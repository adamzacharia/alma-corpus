# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025MNRAS.544.4014Z\sonnetcc\reply.txt

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
 "bibcode": "2025MNRAS.544.4014Z",
 "title": "Connecting star formation in the Milky Way and nearby galaxies ─ I. Comparability of molecular cloud physical properties",
 "year": 2025,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Zhou, J. W.",
 "n_authors": 2,
 "arxiv_id": "2510.26976",
 "doi": "10.1093/mnras/staf1911",
 "alma_projects_linked_by_archive": [
  "2017.1.00886.L"
 ]
}
```

Paper text:
<paper>
# Connecting Star Formation in the Milky Way and Nearby Galaxies. I. Comparability of Molecular Cloud Physical Properties

## Abstract

We used CO (2–1) and CO (1–0) data cubes to identify molecular clouds and study their kinematics and dynamics in three nearby galaxies and the inner Milky Way. When observed at similar spatial and velocity resolutions, molecular clouds in the same mass range across these galaxies show broadly comparable physical properties and similar star formation rates (SFRs). However, this comparability depends on smoothing Milky Way clouds to match the resolution of the extragalactic observations. The beam effect can artificially inflate cloud sizes, leading to inaccurate estimates of radius, density, and virial parameters. By comparing high-resolution and smoothed Milky Way data, we established criteria to exclude beam-affected clouds in the extragalactic sample. After applying this filter, cloud properties remain consistent across galaxies, though some clouds in NGC 5236 show elevated velocity dispersions, likely due to environmental effects. In the inner Milky Way, molecular clouds fall into two groups: those with clumps and those without. Clump-associated clouds are more massive, denser, have higher velocity dispersions, lower virial parameters, and stronger 8$\mu$m emission, suggesting more intense feedback. Strong correlations are found between cloud mass and total clump mass, clump number, and the mass of the most massive clump. These results suggest that a cloud’s physical conditions regulate its internal clump properties and, in turn, its star-forming potential.

– ISM: clouds – galaxies: clusters – galaxies: star formation

# Introduction

Galaxies function as stellar nurseries in the universe, forming stars through the gravitational collapse of the densest parts of molecular clouds within the interstellar medium (ISM). These molecular clouds are widespread throughout galaxies and mark the regions where star formation is actively taking place. Within each cloud, multiple dense clumps are typically present—these clumps are the immediate sites of star formation and serve as the progenitors of embedded star clusters (cite: Kennicutt2012-50; Miville2017-834; Rosolowsky2021-502; Urquhart2022-510; Yan2017-607; Schinnerer2024-62; Zhou2024PASP-1; Zhou2024PASP-2). As presented in (cite: Motte2018-56; Vazquez2019-490; Kumar2020-642; Henshaw2020-4; Dib2020-642; Zhou2022-514; Zhou2023-676; Zhou2024-686-146; Zhou2024PASA; Zhou2024-534; Zhou2025-537b; Zhou2025arXiv250616664Z),

from galactic scales down to dense cores, the molecular gas exhibits a multi-scale, hierarchical structure characterized by hub-filament networks. Dense cores act as hubs within clumps, clumps serve as hubs within molecular clouds, and molecular clouds themselves can function as hubs within galaxies. These hubs, as local centers of gravity, can continuously accrete diffuse surrounding gas, leading to sustained mass growth.

A thorough understanding of the properties of giant molecular clouds (GMCs) is key to deciphering the connection between gas dynamics and star formation in galaxies. Thanks to high-resolution, multi-wavelength observations, it is now possible to resolve star formation down to the scale of individual molecular clouds in nearby galaxies. In particular, high-resolution CO imaging from ALMA (Atacama Large Millimeter/submillimeter Array), along with other submillimeter observations, enables systematic investigations of the molecular cloud population beyond the Milky Way (cite: Leroy2021-257; Leroy2021-255; Lee2022-258; Emsellem2022-659; Lee2023-944; Grishunin2024-682; Schinnerer2024-62).

Since molecular clouds in the Milky Way can be resolved down to their internal structures, they provide a crucial reference for understanding the internal composition and star formation processes of molecular clouds in external galaxies. Star formation occurs primarily within clumps, the dense substructures of molecular clouds. Star formation observed on molecular cloud scales or larger is essentially an integrated outcome of the activity occurring within these clumps.

To truly understand the underlying physics of star formation at those larger scales, it is essential to characterize the star-forming states of individual clumps. This requires turning to the Milky Way as a reference, leveraging surveys such as ATLASGAL and Hi-GAL (cite: Schuller2009-504; Urquhart2022-510; Molinari2010; Elia2021-504), which are capable of resolving individual clumps, along with numerous ALMA follow-up studies that zoom in on single clumps in detail (cite: Sanhueza2019-886; Liu2020; Motte2022-662; Molinari2025-696).

If we aim to use molecular clouds in the Milky Way as a benchmark, we must first establish their comparability to those in nearby galaxies. In this work, we first identify and characterize molecular clouds in the Milky Way, then conduct a detailed comparison with clouds in nearby galaxies. We emphasize the importance of matching angular resolution—i.e., smoothing the data to a common resolution—when comparing cloud properties across different observational datasets. Finally, by taking advantage of the high-resolution insights available for Galactic molecular clouds, we explore how such internal structural information can help interpret the large-scale phenomena observed in $\sim$100 pc molecular clouds in nearby galaxies through ALMA observations, and relate them to the underlying small-scale physics.

# Data

## CO (2-1) cubes and mid-infrared images of nearby galaxies

![](fig/sample.pdf)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | $i$ (deg) | D (Mpc) | beam size (") | linear (pc) | pixel (") | beam area (pix) | leaves |
| NGC 5236 | 24 | 4.89 | 2.14 | 50.7 | 0.5 | 21 | 1722 |
| NGC 628 | 8.9 | 9.84 | 1.12 | 53.5 | 0.2 | 36 | 773 |
| NGC 2835 | 41.3 | 12.22 | 0.84 | 50 | 0.2 | 20 | 130 |
| MW-North |  |  | 72 |  | 24 |  | 597 |
| MW-South |  |  | 72 |  | 24 |  | 707 |
|  |  |  |  |  |  |  |  |

As shown in Table.[\[near\]](#near), we selected three nearby galaxies (NGC 5236, NGC 628 and NGC 2835) with a linear resolution $\sim$50 pc from the PHANGS-ALMA survey (cite: Leroy2021-257; Leroy2021-255), which show different morphologies in Fig.[1](#sample). We used the combined 12m+7m+TP CO (2$-$1) data cubes to investigate gas kinematics and dynamics, which have a spectral resolution of 2.5 km s$^{-1}$. In the Milky Way, the typical molecular cloud size is $\sim$30 pc (cite: Miville2017-834). For molecular clouds smaller than 50 pc in the three nearby galaxies, observational results are inevitably affected by the beam effect.

Among the three galaxies, only NGC 2835 and NGC 628 have available James Webb Space Telescope (JWST) images from the PHANGS-JWST survey (cite: Lee2023-944). We only use the 21 $\mu$m images in this work.

## CO (1-0) cubes and mid-infrared images of the inner Milky Way

Table.1 of (cite: Schuller2021-500) summarizes the CO surveys in the Milky Way. Since we will study the gas environment around the ATLASGAL clumps ($|l| < 60^\circ$ and $|b| < 1.5^\circ$) (cite: Urquhart2018-473), we focus on CO surveys that cover a wide range of Galactic latitudes.

In this work, we use the $^{12}$CO/$^{13}$CO (1-0) cubes from the ThrUMMS (Three-mm Ultimate Mopra Milky Way Survey) and FUGIN (FOREST Unbiased Galactic plane Imaging survey with the Nobeyama 45 m telescope) surveys. The observations and data reduction of the two surveys have been described in detail in (cite: Barnes2015-812; Barnes2025arXiv; Umemoto2017-69).

The ThrUMMS survey, with an angular resolution of $72\ensuremath{''}$ and a spectral resolution of 0.34 km s$^{-1}$, covers the Galactic plane between $300^\circ \le l \le 360^\circ$ and $-1^\circ \le b \le 1^\circ$. For the FUGIN survey, which has an angular resolution of $20\ensuremath{''}$ and a spectral resolution of 1.3 km s$^{-1}$, we focus on observations within the inner Milky Way, covering the Galactic plane between $10^\circ \le l \le 50^\circ$ and $-1^\circ \le b \le 1^\circ$. To compare with the selected nearby galaxies, we unify these two datasets to an angular resolution of 72$\ensuremath{''}$ with a pixel size of 24$\ensuremath{''}$ and a spectral resolution of 2.5 km s$^{-1}$ with a velocity channel of 1.25 km s$^{-1}$.

We also use the mid-infrared images from the *Spitzer* archive, i.e. 8 and 24 $\mu$m images from the GLIMPSE (cite: Benjamin2003-115) and MIPSGAL (cite: Carey2009-121) surveys, respectively.

# Methodology

## Cloud identification

### Nearby galaxies

The cloud identification for NGC 5236 and NGC 628 has been done in (cite: Zhou2024PASA; Zhou2024-534). We conducted a direct identification of hierarchical (sub-)structures based on the 2D intensity maps. As described in (cite: Rosolowsky2008-679), the dendrogram algorithm decomposes density or intensity data into hierarchical structures called leaves, branches, and trunks. In the *astrodendro* package [^2], there are three major input parameters for the dendrogram algorithm: *min_value* for the minimum value to be considered in the dataset, *min_delta* for a leaf that can be considered as an independent entity, and *min_npix* for the minimum area of a structure.

Given that all retained structures in the strictly masked Moment 0 map[^3] are considered reliable, we only require that the smallest identified structure exceeds one beam area (see Table.[\[near\]](#near)). No additional constraints are imposed within the algorithm to reduce the dependence of the identification results on parameter choices. The number of identified molecular clouds (leaves) in each galaxy is shown in Table.[\[near\]](#near).

### The inner Milky Way

![](fig/lv.pdf)

To enable comparison with molecular clouds in nearby galaxies with the resolution of $\sim$50 pc, it is important to identify cloud structures on large spatial scales. Molecular clouds often appear as complexes or as couplings of multi-scale hub-filament structures (cite: Zhou2025arXiv250616664Z), containing numerous substructures within. Our goal is to identify molecular clouds that are as spatially and kinematically continuous and extended as possible.

Since the observations for the molecular gas are confined to within $\pm$1$^{\rm o}$ in Galactic latitude ($b$), we can directly identify molecular clouds from the Galactic longitude–velocity ($lv$) map, as shown in Fig.[2](#lv). For face-on nearby galaxies, we identify molecular clouds directly on the galactic disk, where the clouds are spatially separated. In the Milky Way, however, molecular clouds overlap along the line of sight. By identifying molecular clouds in the $lv$ map, we can use the velocity dimension to separate them. Considering the hierarchical structure of molecular gas, we identify structures at different scales and finally remove duplicate structures.

Before exporting the $lv$ map, we already applied a 3\*rms mask to the $lbv$ cube. As described above, we do not consider the value settings of *min_value* and *min_npix* in the dendrogram algorithm.

Fig.[2](#lv) shows the structures identified with different *min_npix* values. Here, both the velocity and spatial axes are expressed in pixel units, so that they can be properly matched.

Finally, we take *min_npix* = 500, 250, 100, 50, 25, 10, and 5 pixels, in order to cover continuous structures across different scales in the $lv$ map. Since we used a set of different *min_npix* values, each *min_npix* produces a set of structures. For two adjacent *min_npix* values, which are numerically close, they tend to identify a large number of the same structures (i.e., duplicate structures). To exclude duplicate structures, for two structures with similar central coordinates (with areas $A_{\rm 1}$ and $A_{\rm 2}$, where $A_{\rm 1}$ \> $A_{\rm 2}$), if ($A_{\rm 1}$ - $A_{\rm 2}$)/$A_{\rm 2}$ \< 0.3, the structure with area $A_{\rm 2}$ is removed. Because our goal is to eliminate duplicate identifications rather than nested structures, we adopt a value of 0.3. Finally, we identify 707 and 597 molecular clouds from the ThrUMMS and FUGIN surveys, respectively.

We derived the $lv$ map from the $lbv$ cube. Clouds were identified using this $lv$ map, which provides the Galactic longitude, velocity, and their ranges ($l_0$, $v_0$, $dl$, and $dv$) for each cloud, while the Galactic latitude and its range ($b_0$ and $db$) remain unknown. Observations already limit the Galactic latitude to $\pm 1^\circ$. Using $(l_0, 0^\circ, v_0)$ as the center and $(dl, 2^\circ, dv)$ as the extraction range, we extract the molecular gas from the $lbv$ cube. $b_0$ is then determined from the region of strongest emission within this map. Then we take $db = dl$ and use $(l_0, b_0, v_0)$ as the center and $(dl, dl, dv)$ as the extraction range to extract the molecular gas from the $lbv$ cube again to further fix the value $db$.

(cite: Urquhart2022-510) and (cite: Duarte2021-500) have provided detailed descriptions of strategies for determining the distances to molecular clouds and clumps in the inner Milky Way. In order to determine the distances of the identified molecular clouds and investigate the correlations between the physical properties of clouds and those of their internal clumps, we first match the ATLASGAL clumps (cite: Urquhart2022-510) to the identified clouds based on their spatial and velocity ranges, and then assign the median distance of all associated clumps as the distance of the molecular cloud. A typical velocity difference between the median velocity of all associated clumps and the cloud velocity is $\sim$1.2 km/s.

For molecular clouds without matched clumps, we cross-match them with the existing molecular cloud catalogs derived from the SEDIGISM (Structure, Excitation, and Dynamics of the Inner Galactic InterStellar Medium) survey (cite: Duarte2021-500) to determine their distances.

Here, we require the spatial positions of the molecular clouds in the two catalogs to be as close as possible (i.e., we adopt the pair with the smallest separation in both spatial distance and velocity). We also require that the velocity difference of the pair is less than 10 km/s and that the spatial distance of the pair is smaller than the cloud size. As a result, a typical velocity difference between the closest cloud pair (one from our cloud catalog and the other from (cite: Duarte2021-500)) is $\sim$1.0 km/s. Finally, for the ThrUMMS survey, 570 and 137 molecular clouds have and do not have distance estimates, respectively. For the FUGIN survey, the numbers of molecular clouds with and without distance estimates are 370 and 227, respectively. Since the SEDIGISM survey is restricted to $|b| < 0.5^\circ$, therefore, a significant fraction of molecular clouds in the ThrUMMS and FUGIN surveys are not covered by the SEDIGISM survey. In the following analysis, we focus only on molecular clouds with distance estimates.

## Physical parameters

For molecular clouds identified in the Milky Way, the intensity-weighted velocity dispersion is calculated by the second moment method, $$\begin{equation}
v_0 = \frac{\sum T(v) * v}{\sum T(v)}, \quad
\sigma = \sqrt{ \frac{ \sum T(v) * (v - v_0)^2 }{ \sum T(v) } }.
\label{mt}
\end{equation}$$

For molecular clouds in nearby galaxies, we perform Gaussian fitting on the CO line profile to determine the velocity range of the emission. This step is necessary for the velocity dispersion calculation by the second moment. All calculations are based on the PPV cubes masked at the 3\*rms level.

The average column density of a cloud is, $$\begin{equation}
  N  =  I_{\rm CO}^{\rm tot} * X_{\rm CO}/n_{\rm pix},
\label{N-o}
\end{equation}$$ where $I_{\rm CO}^{\rm tot}$ is the total velocity-integrated intensity of the cloud. $n_{\rm pix}$ is the total number of non-empty pixels. The $X_{\rm CO}$ is taken to be $2 \times 10^{20}~\mathrm{cm}^{-2}~(\mathrm{K~km~s}^{-1})^{-1}$ (cite: Bolatto2013-51). The total area of the cloud is, $$\begin{equation}
  A = n_{\rm pix} * l_{\rm pix}^2,
\end{equation}$$ where $l_{\rm pix}$ is the length of a pixel. The total mass of the cloud is, $$\begin{equation}
  M_{\rm cloud} = N * \mu_{\rm H_{2}} * m_{\rm H} * A,
\end{equation}$$ where $\mu_{\rm H_{2}} = 2.8$ is the molecular weight per hydrogen molecule, $m_{\rm H}$ is the hydrogen atom mass. The minimum and maximum radii of the cloud are, $$\begin{equation}
  r_{\rm min} = \sqrt{A/\pi} 
\end{equation}$$ and $$\begin{equation}
  r_{\rm max} = \sqrt{n_{\rm x}*n_{\rm y}}*l_{\rm pix} ,
  \label{rmax}
\end{equation}$$ where $n_{\rm x}$ and $n_{\rm y}$ are the length and width of the box enclosing the cloud. The average column density of the cloud after smoothing is, $$\begin{equation}
  N_{\rm a} = M/(\pi*r_{\rm s}^2)/(\mu_{\rm H_{2}} * m_{\rm H}),
\label{N-a}
\end{equation}$$ where $r_{\rm s}$ is the radius of the cloud after smoothing. The virial parameter of the cloud after smoothing is, $$\begin{equation}
  \alpha_{\rm vir} = 5*\sigma^2*r_{\rm s}/(G*M).
\end{equation}$$

## Radius after smoothing

![](fig/case.pdf)

In order to compare with molecular clouds in nearby galaxies, we need to smooth the high-resolution molecular clouds in the Milky Way to match the resolution of extragalactic observations. This step significantly affects the estimation of the cloud radius. This also leads to notable changes in the estimates of other physical quantities, as shown in Sec.[3.2](#parameters). In Table.[\[near\]](#near), the linear resolution of NGC 628 is 53.5 pc. By taking into account the distances of the identified clouds in the Milky Way, we adjust the smoothing factor such that all clouds are brought to a common spatial resolution of 53.5 pc. Since we are to compare with individual molecular clouds identified in nearby galaxies, for the smoothed map, we only consider the map with one main emission structure, as shown in Fig.[3](#case).

When we smooth the high-resolution image to the lower-resolution one, the radii of structures in the original high-resolution image increase due to blurring on one hand, and on the other hand, spatially dispersed structures may merge into a larger structure. Therefore, the radius of a structure after smoothing depends not only on its original size, but also on its spatial distribution in the original image. Here, we define the filling factor ($f$) as the ratio of pixels with emission to the total number of pixels in the image. The radii of the smoothed molecular clouds can generally be divided into four categories: (1) For the clouds with $r_{\rm max}$ \< 26.75 pc (half the beam size), the smoothed structure is fully contained within a single beam, so its size is effectively the beam size after smoothing, i.e. $r_{\rm s}$ = 26.75 pc; (2) For the clouds with 26.75 \< $r_{\rm max}$ \< 53.5 pc, after smoothing, the emission typically fills the entire image, and thus $r_{\rm s}$ = $r_{\rm max}$ (Fig.[3](#case)(a) and (b)); (3) For the clouds with $r_{\rm max}$ \> 53.5 pc and $f$ \> 0.5, the emission also typically fills the entire image after smoothing, leading to $r_{\rm s}$ = $r_{\rm max}$ (Fig.[3](#case)(c)); (4) For the clouds with $r_{\rm max}$ \> 53.5 pc and $f$ \< 0.5, their radii typically range between 26.75 pc and $r_{\rm max}$, so we adopt a radius of ($r_{\rm max}$ + 26.75 pc) / 2 (Fig.[3](#case)(d)).

## Star formation rates

We further calculate the star formation rates (SFRs) of molecular clouds in the Milky Way and nearby galaxies. For nearby galaxies, JWST observations can resolve individual molecular clouds. In (cite: Zhou2024-534), for the clouds in NGC 628, we calculated the SFR surface density of a cloud using the JWST 21 $\mu$m image following the prescriptions described in (cite: Leroy2021-257),

$$\begin{equation}
    \frac{\Sigma_{\rm SFR}}{\rm M_{\odot}~yr^{-1}~kpc^{-2}} = 3.8\times10^{-3} \left(\frac{I_{\rm 21 \mu m}}{\rm MJy~sr^{-1}}\right),
\end{equation}$$ $$\begin{equation}
    \mathrm{SFR} = \Sigma_{\rm SFR}*l_{\rm pix}^2
    \label{21um}
\end{equation}$$

where $I_{\rm 21 \mu m}$ is the total 21 $\mu$m flux contained within the cloud.

For the clouds in the Milky Way, we also use equation.[\[21um\]](#21um) to calculate the SFR surface density,

but we replace the JWST 21 $\mu$m image by the *Spitzer* 24 $\mu$m image. Unlike in face-on nearby galaxies, 24 $\mu$m emission in the Milky Way suffers from severe overlap due to projection effects. On galaxy-wide and cloud scales, the SFR is correlated with the total amount of dense molecular gas (cite: Gao2004-606; Lada2010-724; Shimajiri2017-604). For each molecular cloud, we know its spatial extent. By calculating the total velocity-integrated CO intensity within this region ($I_{\rm CO,tot}$) and the portion of that intensity confined to the velocity range of the cloud ($I_{\rm CO,cloud}$), we obtain a scaling factor, i.e. $f_{24 \mu m}= I_{\rm CO,cloud}/I_{\rm CO,tot}$. We then multiply the total 24 $\mu$m flux within the region by this factor to determine the 24 $\mu$m flux associated with the cloud. As shown in Fig.[5](#sfr-m), this method proves to be effective.

# Results and discussion

## Comparability of physical properties

![](fig/relation.pdf)

![](fig/sfr.pdf)

As shown in Fig.[4](#para), we compare molecular clouds in the southern and northern inner Milky Way, those in three nearby galaxies, and molecular clouds in the inner Milky Way and nearby galaxies. As long as the observational resolution across these galaxies is consistent, the physical properties of their molecular clouds are overall comparable. In Fig.[5](#sfr-m), the SFRs of molecular clouds in the inner Milky Way and nearby galaxies are also comparable, consistent with the similarity in their physical properties. Moreover, molecular cloud mass shows significant correlations with other physical parameters.

In the upper right boundary of Fig.[4](#para)(a), the average column density increases linearly with mass, which implies a constant radius. These molecular clouds belong to the category with $r_{\rm max} < 26.75$ pc, as defined in Sec.[3.3](#smooth). In Fig.[4](#para)(g), this linear increasing boundary aligns well with observations in nearby galaxies. This further highlights the importance of using a consistent resolution when comparing observations of the Milky Way with those of nearby galaxies.

## Original and smoothed molecular clouds

![](fig/true.pdf)

![](fig/origin.pdf)

![](fig/rn.pdf)

The comparability of molecular clouds in the inner Milky Way and nearby galaxies, as presented above, is based on smoothing the Milky Way molecular clouds to an artificial scale. This highlights the need for caution when interpreting extragalactic observations, as the physical parameters of molecular clouds with sizes (diameters) comparable to or smaller than the beam size may be derived from artificial radius estimates. Consequently, these parameters may not accurately represent the true physical conditions of the clouds. Below, we discuss the impact of resolution on the results by comparing the original high-resolution molecular clouds in the Milky Way with their smoothed counterparts.

Smoothing does not affect mass and SFR estimates, as the total flux remains unchanged, but it does influence radius estimates, which in turn affect the estimation of density and other physical quantities. The estimate of a molecular cloud’s true radius ($r_{\rm t}$) also depends on its filling factor ($f$). Structures with a low filling factor ($f$ \< 0.5) are usually more spatially concentrated in the image. This level of concentration was not important when the image was smoothed, as the structures were blurred. However, it becomes important now that we are estimating the true radius of molecular clouds at high resolution. The filling factor alone does not uniquely reflect the degree of concentration in the pixel distribution, as shown in Fig.[6](#true). Therefore, we introduce an additional image parameter: the ratio of pixels in the largest connected region to the total number of non-zero pixels ($c$). A higher $c$ value indicates a more concentrated pixel distribution. The radius of the molecular cloud is ultimately determined according to the following rules: (1) when the filling factor is high ($f \geq$ 2/3, Fig.[6](#true)(a)), $r_{\rm t} \sim r_{\rm max} \sim r_{\rm min}$; (2) for intermediate filling factors (1/3 \< $f$ \< 2/3, Fig.[6](#true)(b)), $r_{\rm t} \sim$ ($r_{\rm max}$+$r_{\rm min}$)/2; (3) For low filling factor ($f \leq$ 1/3), if $c$ \> 0.5 (Fig.[6](#true)(c)), $r_{\rm t} \sim r_{\rm min}$. Note that 22 clouds ($\sim$2% of the total) with $c$ \< 0.5 are excluded because their radii are difficult to estimate (Fig.[6](#true)(d)).

For the same cloud sample shown in Fig.[4](#para), we now recalculate their physical parameters using $r_{\rm t}$ instead of $r_{\rm s}$. In Fig.[7](#origin)(a), the column density derived using $r_{\rm t}$ by equation.[\[N-a\]](#N-a) is comparable to the original column density derived from equation.[\[N-o\]](#N-o). The strong correlation between column density and mass shown in Fig.[4](#para) is merely an artifact of image smoothing (the beam effect). As shown in Fig.[7](#origin)(a), there is no strong dependence between column density and mass.

The beam effect can artificially enlarge the apparent size of molecular clouds, leading to inaccurate estimates of their radii. As a result, the derived densities of these clouds are also misleading. In Fig.[7](#origin)(a), the straight green boundary line means the clouds on this line have a constant radius, i.e. $r_{\rm s}$ = 26.75 pc. The densities of all molecular clouds located in the upper-left region of this line are distorted due to the beam effect. Fig.[7](#origin)(b) shows the true and distorted column densities. Apart from molecular clouds on the boundary line, molecular clouds with column densities below the dashed black line ($N_{\rm 0} \sim 10^{20.9}$ cm$^{-2}$) are also significantly affected by the beam effect. This fact is more clearly shown in Fig.[8](#rn). For molecular clouds in three nearby galaxies, all of them are located in the lower right of the black solid line, but a subset lies below the black dashed line. These clouds correspond to those that significantly deviate from the mass-radius relation in Fig.[7](#origin)(e). As shown in Fig.[7](#origin)(f), after removing the molecular clouds affected by the beam effect, their mass-radius relation becomes comparable to that of molecular clouds in the inner Milky Way. Here, we only consider the clouds of nearby galaxies located between the dashed and solid black lines in Fig.[7](#origin)(c).

After this filter, in Fig.[7](#origin)(d), the velocity dispersions of molecular clouds in the inner Milky Way and nearby galaxies remain comparable. However, a small fraction of molecular clouds in NGC 5236 exhibit higher velocity dispersions, as also shown in Fig.[4](#para). This may reflect the influence of the galactic environment. As illustrated in Fig.[1](#sample), NGC 5236 features a bar structure and strong spiral arms.

## Molecular clouds and their internal clumps

![](fig/mtot.pdf)

![](fig/CMF.pdf)

Star formation occurs primarily within clumps, the dense substructures of molecular clouds. In this work, the median values of the actual surface density and radius of the molecular clouds are 113 M$_\odot$/pc$^{2}$ and 25 pc, respectively, consistent with the statistical results of the molecular cloud catalog of (cite: Miville2017-834). For the ATLASGAL clumps in the catalog of (cite: Urquhart2022-510), these two values are 906 M$_\odot$/pc$^{2}$ and 0.32 pc, respectively.

In (cite: Urquhart2022-510), the ATLASGAL clumps were grouped into complexes via friends-of-friends clustering, based on their spatial and velocity coherence. For all clump complexes, the median distance uncertainty is $\approx$0.5 kpc. Using the cloud distance determined in Sec. [3.1.2](#inner) as a reference, clumps within a deviation of $r_{\rm t}$ (lower limit) or 0.5 kpc (upper limit) from it are considered to be physically associated with the molecular cloud. For the upper limit case, in Fig.[9](#mtot)(a), there is a clear positive correlation between the mass of a molecular cloud ($M_{\mathrm{cloud}}$) and the total mass of clumps ($M_{\mathrm{clump,tot}}$) within it. Although the number of resolvable clumps is affected by the distance of the cloud, Fig.[9](#mtot)(b) shows that the total clump mass and the total number of clumps within the cloud ($n_{\mathrm{clump,tot}}$) are also positively correlated. If we restrict the cloud sample to those within 2–4 kpc to avoid possible distance bias, as done in (cite: Urquhart2022-510), a much clearer positive correlation can be observed in Fig.[9](#mtot)(b1). For the lower limit case, these correlations persist, as shown in Fig.[12](#mtot1).

We also attempted another method to match clumps with molecular clouds. Specifically, we extracted the averaged $^{13}$CO (1-0) spectrum based on each clump’s central coordinates and radius. If the velocity corresponding to the peak of the spectral line falls within the velocity range of a molecular cloud, the clump is considered to be associated with that cloud. We then assign the median distance of all associated clumps as the distance of the molecular cloud. Subsequently, all physical parameters of the clumps are corrected using this median distance. Comparing Fig.[13](#mtot2) and Fig.[9](#mtot), this method strengthens the correlation between clumps and molecular clouds. The strongest correlations between $M_{\mathrm{cloud}}$, $M_{\mathrm{clump,tot}}$ and SFR for molecular clouds in the inner Milky Way derived in this work are $$\begin{equation}
\mathrm{log}_{\rm 10} (M_{\mathrm{clump,tot}}) = 0.75 \times \mathrm{log}_{\rm 10} (M_{\mathrm{cloud}}) - 0.56 ,
\label{Mcto}
\end{equation}$$ $$\begin{equation}
\mathrm{log}_{\rm 10} (\mathrm{SFR}) = 0.98 \times \mathrm{log}_{\rm 10} (M_{\mathrm{cloud}}) - 9.12 .
\label{sfe-cloud}
\end{equation}$$

Differences in the star-forming ability of molecular clouds are reflected in the variation of their internal clump content. The correlation between a molecular cloud’s physical properties and its star formation activity is also manifested through the presence and characteristics of its internal clumps. Fig.[9](#mtot)(a) shows a significant correlation between the mass of molecular clouds and the total mass of their internal clumps. Similarly, Fig.[9](#mtot)(c) presents a clear correlation between the mass of a molecular cloud and that of its most massive internal clump ($M_{\mathrm{clump,max}}$). In addition, Fig.[4](#para) and Fig.[7](#origin) reveal strong correlations between cloud mass and other physical parameters, such as density, velocity dispersion, and virial parameter. These results suggest that the physical conditions of a molecular cloud may constrain the properties of its internal clumps, thereby influencing the cloud’s star-forming capability. The specific physical mechanisms and how they give rise to the correlations shown in Fig.[9](#mtot) require further investigation.

(cite: Zetterlund2019-881) matched Hi-GAL dust-identified 3674 clumps to 473 clouds traced by $^{12}$CO (3-2) emission, they also found that more massive clouds produce more clumps and more massive clumps. Moreover, they derived a mean clump mass fraction (CMF) of $\sim$0.2. The CMF is defined as the ratio of the total mass of clumps contained within a cloud to the total mass of the cloud (i.e. $M_{\mathrm{clump,tot}}$/$M_{\mathrm{cloud}}$), which is also called the dense gas fraction (DGF) (cite: Urquhart2021-500; Eden2021-500). (cite: Eden2012-422) and (cite: Battisti2014-780) matched BGPS clumps to molecular clouds traced by $^{13}$CO (1–0) emission and found that the CMF ranges from approximately 8% to 13%. Similarly, (cite: Urquhart2021-500) matched ATLASGAL clumps to molecular clouds traced by $^{13}$CO (2–1) emission and reported a CMF range of about 5%–16%. However, for our sample, the median CMF is only $\sim$1.4%. The catalogs of (cite: Eden2012-422; Battisti2014-780; Urquhart2021-500) are available online. Fig.[10](#CMF)(b) shows that the CMF is dependent on the molecular cloud mass. Firstly, different emission lines yield different estimates of molecular cloud masses, and the method used to identify molecular clouds can also affect the mass estimation. The molecular cloud masses identified in this work are significantly larger. To be precise, what is identified in this work are molecular cloud complexes. Previous studies, of course, were able to resolve the substructures within these complexes, which are then referred to as molecular clouds. Moreover, (cite: Urquhart2021-500) used the ATLASGAL clump catalog of (cite: Urquhart2018-473), which gives the full mass of the clump. However, the clump mass in the catalog of (cite: Urquhart2022-510) used in this work is determined by integrating the flux density at 870 $\mu$m within the Full Width at Half Maximum (FWHM) contour, i.e., above 50% of the peak of the ATLASGAL dust continuum emission. The systematically lower clump masses also result in a smaller CMF. Overall, to compare CMFs from various works, the masses of molecular clouds and clumps must be measured consistently.

## Molecular clouds in the inner Milky Way and NGC 628

![](fig/assoc.pdf)

In (cite: Zhou2024-534), we conducted a detailed study of the molecular clouds in NGC 628, where the clouds were classified into three distinct categories (i.e. leaf-HFs-A, leaf-HFs-B and leaf-HFs-C), each exhibiting significantly different physical properties. leaf-HFs-A present the best hub-filament morphology, which also have the highest density contrast, the largest mass and the lowest virial ratio. The numbers of the associated 21 $\mu$m and H$_{\alpha}$ structures and the peak intensities of 7.7 $\mu$m, 21 $\mu$m and H$_{\alpha}$ emissions decrease from leaf-HFs-A to leaf-HFs-C. These evidence indicate that leaf-HFs-A have more active star formation than leaf-HFs-C. Since clumps are the real star-forming sites within molecular clouds, leaf-HFs-A, which have greater mass, contain more clumps and therefore exhibit stronger star formation activity.

As described in Sec.[3.1.2](#inner), a considerable fraction of molecular clouds do not have associated clumps. Thus, we can roughly divide molecular clouds in the inner Milky Way into two groups based on whether they are associated with clumps ("with" and "without"). The group associated with clumps is clearly more active in star formation. In Fig.[11](#assoc), molecular clouds in this group exhibit greater mass, higher density, larger velocity dispersion, and smaller virial parameters. These differences are also clearly reflected in the comparison between leaf-HFs-A and leaf-HFs-C molecular clouds in NGC 628. As presented in (cite: Mazumdar2021-650; Zhou2024-682-128), the 8 $\mu$m emission can be a good indicator of feedback strength. We calculated the average 8 $\mu$m surface brightness ($F_{\rm 8 \mu m,a}$) over each cloud to measure the strength of feedback in each cloud. In Fig.[11](#assoc)(f), molecular clouds associated with clumps exhibit stronger 8 $\mu$m emission, which suggests more intense stellar feedback. Hence, their elevated velocity dispersion may be a consequence of star formation feedback.

# Conclusion

We used the CO (2–1) and CO (1–0) data cubes to identify molecular clouds and investigate their gas kinematics and dynamics in three nearby galaxies and the inner Milky Way, respectively. We compare the physical properties of molecular clouds across these environments and find that, when observed at consistent resolution, their properties are broadly comparable. The star formation rates (SFRs) of molecular clouds in both the inner Milky Way and nearby galaxies also follow similar trends.

However, this comparability relies on smoothing Milky Way molecular clouds to an artificial scale. The beam effect can artificially enlarge the apparent size of molecular clouds, leading to inaccurate estimates of their radii, and consequently, misleading values for derived quantities such as density and virial parameter. By comparing the original high-resolution Milky Way clouds with their smoothed counterparts, we established criteria to exclude clouds significantly affected by the beam effect in the extragalactic sample.

After applying this filter, we re-examined the physical properties of molecular clouds in the inner Milky Way and the three nearby galaxies, and found that the properties remain broadly consistent. Nonetheless, a small fraction of molecular clouds in NGC 5236 exhibit higher velocity dispersions, which may reflect the influence of the galactic environment.

In the inner Milky Way, molecular clouds can be classified into two groups: those associated with clumps and those without. Clump-associated clouds tend to be more massive, denser, have higher velocity dispersions, and lower virial parameters. These clouds also show stronger 8 $\mu$m emission, suggesting more intense stellar feedback, which may contribute to their elevated velocity dispersions.

There is a strong positive correlation between a cloud’s mass and the total mass of clumps it contains. Likewise, the number of clumps scales with both the cloud’s mass and total clump mass. Additionally, a clear relationship exists between a cloud’s mass and that of its most massive clump. These findings indicate that a cloud’s physical conditions influence the properties of its internal clumps, thereby shaping its overall star-forming potential.

# Acknowledgements

Thanks to the referee for the detailed comments that helped clarify this work. It is a pleasure to thank the PHANGS team, the data cubes and other data products shared by the team make this work can be carried out easily.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope.

This publication makes use of data from FUGIN, FOREST Unbiased Galactic plane Imaging survey with the Nobeyama 45-m telescope, a legacy project in the Nobeyama 45-m radio telescope.

# Data availability

For nearby galaxies, all the data used in this work are available on the PHANGS team website [^4]. For the inner Milky Way, the datasets are available on the team websites of the ThrUMMS [^5] and the FUGIN [^6] surveys. The molecular cloud catalog produced in this work is available at the CDS.

natexlab

(ref: Barnes2025arXiv) Barnes, P. J., Barnes, D. G. H., Hernandez, A. K., Lopez, S., & Muller, E. 2025, arXiv e-prints, arXiv:2503.04887, doi: [`10.48550/arXiv.2503.04887`](http://doi.org/10.48550/arXiv.2503.04887)

(ref: Barnes2015-812) Barnes, P. J., Muller, E., Indermuehle, B., et al. 2015, ApJ, 812, 6, doi: [`10.1088/0004-637X/812/1/6`](http://doi.org/10.1088/0004-637X/812/1/6)

(ref: Battisti2014-780) Battisti, A. J., & Heyer, M. H. 2014, ApJ, 780, 173, doi: [`10.1088/0004-637X/780/2/173`](http://doi.org/10.1088/0004-637X/780/2/173)

(ref: Benjamin2003-115) Benjamin, R. A., Churchwell, E., Babler, B. L., et al. 2003, PASP, 115, 953, doi: [`10.1086/376696`](http://doi.org/10.1086/376696)

(ref: Bolatto2013-51) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Carey2009-121) Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, PASP, 121, 76, doi: [`10.1086/596581`](http://doi.org/10.1086/596581)

(ref: Dib2020-642) Dib, S., Bontemps, S., Schneider, N., et al. 2020, A&A, 642, A177, doi: [`10.1051/0004-6361/202038849`](http://doi.org/10.1051/0004-6361/202038849)

(ref: Duarte2021-500) Duarte-Cabral, A., Colombo, D., Urquhart, J. S., et al. 2021, The SEDIGISM survey: molecular clouds in the inner Galaxy, OUP, doi: [`10.1093/mnras/staa2480`](http://doi.org/10.1093/mnras/staa2480)

(ref: Eden2012-422) Eden, D. J., Moore, T. J. T., Plume, R., & Morgan, L. K. 2012, MNRAS, 422, 3178, doi: [`10.1111/j.1365-2966.2012.20840.x`](http://doi.org/10.1111/j.1365-2966.2012.20840.x)

(ref: Eden2021-500) Eden, D. J., Moore, T. J. T., Plume, R., et al. 2021, MNRAS, 500, 191, doi: [`10.1093/mnras/staa3188`](http://doi.org/10.1093/mnras/staa3188)

(ref: Elia2021-504) Elia, D., Merello, M., Molinari, S., et al. 2021, MNRAS, 504, 2742, doi: [`10.1093/mnras/stab1038`](http://doi.org/10.1093/mnras/stab1038)

(ref: Emsellem2022-659) Emsellem, E., Schinnerer, E., Santoro, F., et al. 2022, A&A, 659, A191, doi: [`10.1051/0004-6361/202141727`](http://doi.org/10.1051/0004-6361/202141727)

(ref: Gao2004-606) Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271, doi: [`10.1086/382999`](http://doi.org/10.1086/382999)

(ref: Grishunin2024-682) Grishunin, K., Weiss, A., Colombo, D., et al. 2024, A&A, 682, A137, doi: [`10.1051/0004-6361/202347364`](http://doi.org/10.1051/0004-6361/202347364)

(ref: Henshaw2020-4) Henshaw, J. D., Kruijssen, J. M. D., Longmore, S. N., et al. 2020, Nature Astronomy, 4, 1064, doi: [`10.1038/s41550-020-1126-z`](http://doi.org/10.1038/s41550-020-1126-z)

(ref: Kennicutt2012-50) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Kumar2020-642) Kumar, M. S. N., Palmeirim, P., Arzoumanian, D., & Inutsuka, S. I. 2020, A&A, 642, A87, doi: [`10.1051/0004-6361/202038232`](http://doi.org/10.1051/0004-6361/202038232)

(ref: Lada2010-724) Lada, C. J., Lombardi, M., & Alves, J. F. 2010, ApJ, 724, 687, doi: [`10.1088/0004-637X/724/1/687`](http://doi.org/10.1088/0004-637X/724/1/687)

(ref: Lee2022-258) Lee, J. C., Whitmore, B. C., Thilker, D. A., et al. 2022, ApJS, 258, 10, doi: [`10.3847/1538-4365/ac1fe5`](http://doi.org/10.3847/1538-4365/ac1fe5)

(ref: Lee2023-944) Lee, J. C., Sandstrom, K. M., Leroy, A. K., et al. 2023, ApJL, 944, L17, doi: [`10.3847/2041-8213/acaaae`](http://doi.org/10.3847/2041-8213/acaaae)

(ref: Leroy2021-257) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021a, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: Leroy2021-255) Leroy, A. K., Hughes, A., Liu, D., et al. 2021b, ApJS, 255, 19, doi: [`10.3847/1538-4365/abec80`](http://doi.org/10.3847/1538-4365/abec80)

(ref: Liu2020) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020, MNRAS, 496, 2790, doi: [`10.1093/mnras/staa1577`](http://doi.org/10.1093/mnras/staa1577)

(ref: Mazumdar2021-650) Mazumdar, P., Wyrowski, F., Colombo, D., et al. 2021, A&A, 650, A164, doi: [`10.1051/0004-6361/202040205`](http://doi.org/10.1051/0004-6361/202040205)

(ref: Miville2017-834) Miville-Deschênes, M.-A., Murray, N., & Lee, E. J. 2017, ApJ, 834, 57, doi: [`10.3847/1538-4357/834/1/57`](http://doi.org/10.3847/1538-4357/834/1/57)

(ref: Molinari2010) Molinari, S., Swinyard, B., Bally, J., et al. 2010, A&A, 518, L100, doi: [`10.1051/0004-6361/201014659`](http://doi.org/10.1051/0004-6361/201014659)

(ref: Molinari2025-696) Molinari, S., Schilke, P., Battersby, C., et al. 2025, A&A, 696, A149, doi: [`10.1051/0004-6361/202452702`](http://doi.org/10.1051/0004-6361/202452702)

(ref: Motte2018-56) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41, doi: [`10.1146/annurev-astro-091916-055235`](http://doi.org/10.1146/annurev-astro-091916-055235)

(ref: Motte2022-662) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8, doi: [`10.1051/0004-6361/202141677`](http://doi.org/10.1051/0004-6361/202141677)

(ref: Rosolowsky2021-502) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: Rosolowsky2008-679) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Sanhueza2019-886) Sanhueza, P., Contreras, Y., Wu, B., et al. 2019, ApJ, 886, 102, doi: [`10.3847/1538-4357/ab45e9`](http://doi.org/10.3847/1538-4357/ab45e9)

(ref: Schinnerer2024-62) Schinnerer, E., & Leroy, A. K. 2024, ARA&A, 62, 369, doi: [`10.1146/annurev-astro-071221-052651`](http://doi.org/10.1146/annurev-astro-071221-052651)

(ref: Schuller2009-504) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415, doi: [`10.1051/0004-6361/200811568`](http://doi.org/10.1051/0004-6361/200811568)

(ref: Schuller2021-500) Schuller, F., Urquhart, J. S., Csengeri, T., et al. 2021, MNRAS, 500, 3064, doi: [`10.1093/mnras/staa2369`](http://doi.org/10.1093/mnras/staa2369)

(ref: Shimajiri2017-604) Shimajiri, Y., André, P., Braine, J., et al. 2017, A&A, 604, A74, doi: [`10.1051/0004-6361/201730633`](http://doi.org/10.1051/0004-6361/201730633)

(ref: Umemoto2017-69) Umemoto, T., Minamidani, T., Kuno, N., et al. 2017, PASJ, 69, 78, doi: [`10.1093/pasj/psx061`](http://doi.org/10.1093/pasj/psx061)

(ref: Urquhart2018-473) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, MNRAS, 473, 1059, doi: [`10.1093/mnras/stx2258`](http://doi.org/10.1093/mnras/stx2258)

(ref: Urquhart2021-500) Urquhart, J. S., Figura, C., Cross, J. R., et al. 2021, MNRAS, 500, 3050, doi: [`10.1093/mnras/staa2512`](http://doi.org/10.1093/mnras/staa2512)

(ref: Urquhart2022-510) Urquhart, J. S., Wells, M. R. A., Pillai, T., et al. 2022, MNRAS, 510, 3389, doi: [`10.1093/mnras/stab3511`](http://doi.org/10.1093/mnras/stab3511)

(ref: Vazquez2019-490) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061, doi: [`10.1093/mnras/stz2736`](http://doi.org/10.1093/mnras/stz2736)

(ref: Yan2017-607) Yan, Z., Jerabkova, T., & Kroupa, P. 2017, A&A, 607, A126, doi: [`10.1051/0004-6361/201730987`](http://doi.org/10.1051/0004-6361/201730987)

(ref: Zetterlund2019-881) Zetterlund, E., Glenn, J., & Rosolowsky, E. 2019, ApJ, 881, 90, doi: [`10.3847/1538-4357/ab2e03`](http://doi.org/10.3847/1538-4357/ab2e03)

(ref: Zhou2024PASA) Zhou, J.-W., & Davis, T. 2024, PASA, 41, e076, doi: [`10.1017/pasa.2024.47`](http://doi.org/10.1017/pasa.2024.47)

(ref: Zhou2024-534) Zhou, J. W., Dib, S., & Davis, T. A. 2024a, MNRAS, 534, 683, doi: [`10.1093/mnras/stae2101`](http://doi.org/10.1093/mnras/stae2101)

(ref: Zhou2024-686-146) Zhou, J. W., Dib, S., Juvela, M., et al. 2024b, A&A, 686, A146, doi: [`10.1051/0004-6361/202449514`](http://doi.org/10.1051/0004-6361/202449514)

(ref: Zhou2024PASP-2) Zhou, J. W., Dib, S., & Kroupa, P. 2024c, PASP, 136, 094302, doi: [`10.1088/1538-3873/ad77f4`](http://doi.org/10.1088/1538-3873/ad77f4)

(ref: Zhou2024PASP-1) Zhou, J. W., Kroupa, P., & Dib, S. 2024d, PASP, 136, 094301, doi: [`10.1088/1538-3873/ad6f44`](http://doi.org/10.1088/1538-3873/ad6f44)

(ref: Zhou2025-537b) Zhou, J. W., & Li, G.-X. 2025, MNRAS, 537, 2630, doi: [`10.1093/mnras/staf199`](http://doi.org/10.1093/mnras/staf199)

(ref: Zhou2025arXiv250616664Z) Zhou, J. W., Urquhart, J. S., Wyrowski, F., et al. 2025, arXiv e-prints, arXiv:2506.16664, doi: [`10.48550/arXiv.2506.16664`](http://doi.org/10.48550/arXiv.2506.16664)

(ref: Zhou2024-682-128) Zhou, J. W., Wyrowski, F., Neupane, S., et al. 2024e, A&A, 682, A128, doi: [`10.1051/0004-6361/202347377`](http://doi.org/10.1051/0004-6361/202347377)

(ref: Zhou2022-514) Zhou, J.-W., Liu, T., Evans, N. J., et al. 2022, MNRAS, 514, 6038, doi: [`10.1093/mnras/stac1735`](http://doi.org/10.1093/mnras/stac1735)

(ref: Zhou2023-676) Zhou, J. W., Wyrowski, F., Neupane, S., et al. 2023, A&A, 676, A69, doi: [`10.1051/0004-6361/202346500`](http://doi.org/10.1051/0004-6361/202346500)

# Supplementary maps

![](fig/mtot1.pdf)

![](fig/mtot2.pdf)

[^1]: E-mail: jwzhou@mpifr-bonn.mpg.de

[^2]: <https://dendrograms.readthedocs.io/en/stable/index.html>

[^3]: Details of the masking strategy and completeness statistics are provided in the PHANGS pipeline paper (cite: Leroy2021-255).

[^4]: <https://sites.google.com/view/phangs/home>

[^5]: <https://gemelli.spacescience.org/~pbarnes/research/thrumms/rbank/>

[^6]: <https://nro-fugin.github.io/release/>

</paper>

Write the methods card for this paper.