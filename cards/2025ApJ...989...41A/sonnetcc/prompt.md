# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989...41A\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989...41A",
 "title": "Discovery of Jet─Bubble─Disk Interaction: Jet Feedback on a Protoplanetary Disk Via an Expanding Bubble in WSB 52",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Aizawa, Masataka",
 "n_authors": 3,
 "arxiv_id": "2501.10121",
 "doi": "10.3847/1538-4357/add47e",
 "alma_projects_linked_by_archive": [
  "2015.1.00486.S",
  "2015.1.00964.S"
 ]
}
```

Paper text:
<paper>
# Discovery of Jet-Bubble-Disk Interaction:\
Jet Feedback on a Protoplanetary Disk via an Expanding Bubble in WSB 52

## Abstract

While stellar jets and outflows are fueled by accretion from disks, their direct influence on disks remain unexplored. Here we revisit ALMA observations of $^{12}\mathrm{CO}\,(J=2\mbox{--}1)$ line emission for the young stellar object WSB 52. We identify an expanding bubble that interacts with its protoplanetary disk. Given that the disk axis points toward the bubble center and the kinetic energy of the bubble is roughly $10^{41}$ erg, we postulate that stellar jets, aligned with the disk axis, have triggered the bubble. The bubble morphology is consistent with uniform expansion with partial concavity, implying the bubble-disk interaction. Correspondingly, the shape and the velocity field of protoplanetary disk appear to be deformed and exhibit high-velocity components, suggesting strong interactions and mass loss from the disk. The discovery of jet feedback onto the disk via the bubble—which we term the jet-bubble-disk interaction—sheds new light on the dynamical processes governing star and planet formation.

UTF8gbsn

# Introduction

Protoplanetary disks are circumstellar disks composed of gas and dust, serving as the birthplaces of planets (cite: hayashi1985; williams2011). Recent high-resolution observations by the Atacama Large Millimeter/submillimeter Array (ALMA) have revealed the detailed distributions of disk materials, greatly enhancing our understanding of planet formation (cite: brogan2015; andrews2018; oberg2021). The discovery of numerous substructures—such as gaps and rings—demonstrates that ongoing physical processes within the disk, including planetary formation, are actively taking place (cite: bae2022). Moreover, comparisons of Class I and Class II disks, where fewer annular substructures have been identified in the earlier phases, offer insights into how protoplanetary disks evolve (cite: andrews2018; ohashi2023).

The materials of protoplanetary disks are supplied by larger-scale envelopes or cores and, in turn, promote mass accretion onto protostars. A fraction of the inflowing material does not end up on the star but is instead expelled as jets and outflows, carrying away excess mass and angular momentum (cite: Blandford1982; matzner2000; machida2014). Indeed, there is a strong correlation between the mass-loss rates and the protostellar accretion rates (cite: Hartigan1995) (see also Fig. 14 in (cite: Ellerbroek2013)) or (cite: lee2020) for review.) The kinetic energy of ejected materials can be released into surrounding environments, increasing turbulence strengths (cite: Norman1980; li2006; Nakamura2007) and thereby regulating star formation efficiency (cite: Hansen2012; Federrath_2013; offner2017; mathew2021) (see also (cite: frank2014) and (cite: bally2006) for reviews).

Additionally, such mass ejection could promote material circulation within protostellar disks by lifting dusts from inner disks to outer areas, as discussed in the context of chondrule formation in the early Solar System (cite: shu1996; shu2001; haugbolle2019) and dust growth (cite: tsukamoto2021; Cacciapuoti2024). This can be seen as indirect feedback on the disks. However, the more direct and kinematic influence of jets and outflows on protoplanetary disks remains unexplored.

In this study, we present, for the first time, evidence of a potential direct feedback mechanism of jets on a protoplanetary disk. Specifically, we identify an expanding bubble near the star—likely driven by past jet activity—that appears to be interacting with the disk. Although similar bubble morphologies have been observed in systems such as XZ Tau (cite: Krist1997; Krist1999; Kirst2008) and SVS 13 (cite: Hodapp2014) via optical and near-infrared observations, this direct interaction has not been reported previously, perhaps because the bubble’s rapid expansion relative to its systemic motion is uniquely evident in the current system.

The present paper is organized as follows. Section [2](#sec:obs) provides a detailed description for the ALMA observations. Section [3](#sec:results) presents the comprehensive analyses on main three features identified in the system. Section [4](#sec:discuss) presents the discussion, and Section [5](#sec:conclusion) concludes the study.

# Observation and Data Reduction

The target in this paper, WSB 52, is a T Tauri star in Class II phase, located $135.27\pm0.92$ pc away from the Earth (cite: gaia2016; gaia2023), in the Ophiuchus region. The star harbors a dusty disk with a gap structure, as observed by ALMA in DSHARP (The Disk Substructures at High Angular Resolution Project) (cite: andrews2018). Table [1](#fig:channels_maps_all) lists the stellar and disk parameters, as used or reported in (cite: andrews2018) and (cite: huang2018). In (cite: andrews2018), the $^{12}\mathrm{CO}\,(J=2\mbox{--}1)$ data for WSB 52 were described as “cloud (severe), complex outflow" in their Table 5. While we identify the noted cloud contamination, our analysis provides further insight into the system’s nature. Note that, aside from WSB 52, we also examined the other DSHARP targets but did not identify similar events in any of the other systems.

We began our analysis by examining the $^{12}\mathrm{CO}\,(J=2\mbox{--}1)$ cube data, available on the DSHARP data release webpage. However, we found that the velocity coverage of the released image cube was insufficient to fully capture the features of our interest; therefore, we reconstruct the image cube from the raw data, extending the line-of-sight velocity range to $v_{\rm LSR} = -15.70$ km/s to $29.45$ km/s. The measurement set, downloaded from the ALMA archive, is processed using the Common Astronomy Software Applications (CASA) pipeline (version 4.7.2) by the East Asian ALMA Regional Center (EA-ARC), followed by self-calibration with the standard DSHARP analysis script using CASA 6.6.5. For CLEAN imaging, we basically adopt the same parameters as the standard script but slightly adjust the following parameters; ${\tt gain}=0.2$, ${\tt niter}=200000$, ${\tt threshold}=2.5$ mJy, and ${\tt imsize}= 2000$. We apply the primary beam correction to the image.

The reconstructed cube data have a channel spacing of $0.35$ km/s and an image pixel size of $0.01$ arcsec. As noted in (cite: andrews2018), the actual velocity resolution is about two channels, because of Hanning smoothing in the ALMA correlators. The synthesized beam size is $0.141 \times 0.092$ arcsec with a position angle of $-85.5^{\circ}$. As (cite: andrews2018) described this target as “cloud (severe), complex outflow", contamination from extended molecular cloud emission around WSB 52 obscured the circumstellar gas, including disk emission near the systemic velocity ($v_{\text{sys},\star} = 3.9$ km/s, as determined in Sec [3.3](#sec:deformed)) within the range $v_{\rm LSR} = 2.85$ to $4.6$ km/s. Nonetheless, our focus on velocity components with minimal cloud contamination ensures that this issue does not compromise our primary findings.

![](./all_cube_data.pdf)

| Parameter                        | Value   | Reference           |
|:---------------------------------|:--------|:--------------------|
| $M_{\star}$ \[$M_{\rm sun}$\]    | 0.4786  | (cite: andrews2018) |
| Distance \[pc\]                  | 135.27  | (cite: gaia2023)    |
| $x_{\star}^{\dagger}$ \[arcsec\] | $-$0.12 | (cite: huang2018)   |
| $y_{\star}^{\dagger}$ \[arcsec\] | $-$0.43 | (cite: huang2018)   |
| $i$ \[deg\]                      | 54.4    | (cite: huang2018)   |
| PA$^{\dagger\dagger}$ \[deg\]    | 138.4   | (cite: huang2018)   |
|                                  |         |                     |

\
$^{\dagger}$ $(x, y) = (\Delta \text{RA}, \Delta \text{Dec})$ measured from the observational center.\
$^{\dagger\dagger}$ Position angle for the disk major axis measured from the north direction.

|                                                            | **Value** |
|:-----------------------------------------------------------|:----------|
| **Expanding Bubble Model in Sec [3.1](#sec:exp_bubble)**   |           |
| $x_{\rm bubble}$ \[arcsec\]                                | 2.50      |
| $y_{\rm bubble}$ \[arcsec\]                                | 1.90      |
| $r_{\rm bubble}$ \[arcsec\]                                | 5.5       |
| $v_{\rm sys,bubble}$ \[km/s\]                              | $-$0.25   |
| $u_{\rm bubble}$ \[km/s\]                                  | 12.5      |
| **Shock Boundary Model in Sec [3.2](#sec:shock_boundary)** |           |
| $r_{\rm bubble}$ \[arcsec\]                                | 5.5 / 6.5 |
| $a$                                                        | 2.14      |
| $h_{\rm shock}$ \[arcsec\]                                 | 0.18      |
| $\zeta_0$ \[arcsec\]                                       | $-$0.28   |
| **Keplerian Disk Model in Sec [3.3](#sec:deformed)**       |           |
| $v_{\text{sys},\star}$ \[km/s\]                            | 3.9       |
| $h_{\rm disk}$ \[au\]                                      | 5         |
| $p$                                                        | 1         |

: Model Parameters

# Result

Figure [1](#fig:channels_maps_all) presents the selected channel maps with velocity spacing of $1.05$ km/s for the $^{12}$CO emission. After a thorough inspection of the channel maps, three distinct features have been identified as follows: (1) shell-like patterns in $v_{\mathrm{LSR}} = -11.85$ to $0.75$ km/s and $v_{\mathrm{LSR}} =4.95$ to $11.25$ km/s in the figure, sharing the same central position offset from the star, (2) a concave morphology at $v_{\mathrm{LSR}} = 4.95$-$10.20$ km/s in the southwestern part of the shells, and (3) spatially compact emissions in the vicinity of the star at $v_{\mathrm{LSR}} = -6.60$ to $18.60$ km/s. These features can be interpreted as follows: (1) an expanding bubble offset from the stellar position, (2) a shock boundary between the bubble and the star’s vicinity, and (3) a deformed protoplanetary disk.

Figure [2](#fig:summary) shows the proposed models that will be discussed in detail throughout the paper; the bubble is likely driven by jet compression, which sweeps up the circumstellar material and interacts with the disks. Panel (2a) illustrates the current state of the system as inferred from the observations. In the remaining of this section, we analyze the structures identified in the observations.

![](./bubble_fig.pdf)

## The expanding bubble

Figure [1](#fig:channels_maps_all) shows shell-like patterns that vary in size with velocity, ultimately converging to a single point. This morphology appears to be explained by a uniformly expanding bubble. The bubble is not perfectly spherical but shows notable asymmetry, appearing particularly bright near the star. This point is discussed in detailed in Section [4.1](#sec:scenario).

To constrain the physical property of the bubble, we develop a simple model, which is characterized by the central position $(x_{\rm bubble}, y_{\rm bubble})$, bubble radius $r_{\rm bubble}$, radial expansion velocity $u_{\rm bubble}$, and systematic velocity $v_{\rm sys, bubble}$. In the modeling, we adopt a Cartesian coordinate system $(x, y, z)$. We assume $(x, y) = (\Delta \text{RA}, \Delta \text{Dec})$, where $\Delta \text{RA}$ and $\Delta \text{Dec}$ are the offsets in right ascension and declination, respectively, from the phase center of the image. The $z$-axis represents the relative depth to the bubble center; we assume that the bubble center is located at $(x_{\rm bubble}, y_{\rm bubble}, 0)$, and a positive $z$-value represents the side that is farther away from the observer. We here use arcseconds as the unit for the scale of the coordinate system, but we can convert it into physical scales by using the distance $d=135.27$ pc.

In the rest frame of the bubble, the velocity field is defined as: $$\begin{eqnarray}
    \mathbf{u}(\mathbf{r}) &=&  u_{\rm bubble} \left(\frac{\mathbf{r}}{r_{\rm bubble}}\right),  \label{eq:bubble_vel}
\end{eqnarray}$$ where ${\bf r} = (x - x_{\rm bubble}, y- y_{\rm bubble}, z)$ denotes a relative vector from the bubble center to the point on the sphere.

We assume the line-of-sight systematic velocity of the bubble to be $v_{\rm sys, bubble}$. The line-of-sight radial velocity for the expanding bubble obtained by an observer is then given as follows: $$\begin{eqnarray}
    v_{\rm LOS}(z) &=& v_{\rm sys, bubble} + u_{\rm bubble}\left(\frac{z}{r_{\rm bubble}}\right). 
\end{eqnarray}$$ Conversely, for a given constant observed velocity $v_{\rm LOS}$, the cross-section of the sphere is characterized by the depth $z(v_{\rm LOS})$ and the radius $r(v_{\rm LOS})$ as follows: $$\begin{eqnarray}
    z(v_{\rm LOS}) &=& r_{\rm bubble} \left(\frac{v_{\rm LOS} - v_{\rm sys,  bubble}}{u_{\rm bubble}}  \right),  \\
    r(v_{\rm LOS}) &=& r_{\rm bubble} \sqrt{1 - \frac{z^{2}(v_{\rm LOS})}{r_{\rm bubble}^{2}}}.
\end{eqnarray}$$

The model described above provides the location of the bubble rim for each observed line-of-sight velocity. We have opted to employ a visual optimization of the parameters by comparing the observed bubble rims to the model prediction. This approach is motivated by the fact that a numerical optimization is susceptible to the arbitrary choices of the optimization function and criteria when analyzing such a complex phenomenon. Specifically, given the parameters and the array of the observed velocities, we plot the circles with the center $(x_{\rm bubble}, y_{\rm bubble})$ and the radii of $r(v_{\rm LOS})$, and then compare them to the cube data. The obtained solution is in strong agreement with the observed bubble, thereby satisfying the objective of this analysis to characterize the emission features in a coherent manner.

We overlay the continuum emission contour and the disk axis in Figure [1](#fig:channels_maps_all). The image is taken from the DSHARP observation at <https://almascience.eso.org/almadata/lp/DSHARP/>, and a contour level of 1 mJy/beam is used to approximate the outer disk radius. Both the bubble and the concave structure appear symmetric with respect to the disk axis, also as discussed in the next subsection. Consequently, the disk axis seems to point toward the bubble center, not only in the sky plane but also in three-dimensional space. We thus assume that the bubble center to be on the line of the disk axis in determining $(x_{\rm bubble}, y_{\rm bubble})$.

Table [1](#table:model_parameters) presents our optimized parameters. White lines in Figure [1](#fig:channels_maps_all) delineate the bubble rims in our model. Despite its simplicity, the model demonstrates a high degree of agreement with the observational data. The inferred radius of the bubble is approximately 750 au, and the expansion velocity is 12.5 km/s. The center of the bubble is derived as ($x_{\rm bubble}, y_{\rm bubble}$) = ($2.50", 1.90"$), indicating a distance between the bubble center and the star of 580 au if $i = 58.4^{\circ}$. The stellar location is within the bubble, thereby suggesting an interaction between circumstellar materials and the bubble. In addition, $v_\mathrm{{sys, bubble}}$, $-0.25$ km/s, is blue-shifted from the systemic velocity of the star.

We further estimate the bubble mass and kinetic energy using $^{12}$CO(2-1) intensities under the assumption that the emission is not completely optically thick. In the analysis, we mask out the disk gas emission within a 1.5 arcsec radius around the star to isolate the shell. The detail of the calculation is given in Appendix [\[sec:mass_energy_bubble\]](#sec:mass_energy_bubble). Assuming local thermodynamic equilibrium (LTE) with gas temperatures ranging from 25 K to 100 K, we derive a total mass of $M_{\rm shell} = (0.2-1.1) \times10^{-4}$ $M_{\odot}$. Combined with the mass and the expansion velocity with 12.5 km/s, we estimate a kinetic energy of $E_{\rm shell} = (0.3-1.6) \times10^{41}$ erg. As discussed in Section [4](#sec:discuss), this energy scale is consistent with that of the jets.

## The shock boundary between bubble and the stellar vicinity

As in Figure [1](#fig:channels_maps_all), the bubble is not perfectly spherical; it exhibits a concave morphology near the star. Figure [3](#fig:channels) presents a zoomed-in view of this feature across selected velocity channels. We overplot the continuum emission contour at a level of 0.1 mJy/beam in Figure [3](#fig:channels).

Notably, the disk axis points toward the bubble center, and the shock boundary appears to be symmetric along this disk axis as well. These observations prompt two assumptions: (a) the shock boundary is nearly axisymmetric with respect to the disk axis, and (b) the bubble center lies on the disk axis in three-dimensional space, as described in Section [3.1](#sec:exp_bubble). Under the assumption (b), we estimate the star’s line-of-sight depth relative to the bubble center by using the disk inclination and the projected distance on the sky. Specifically, for the stellar position $(x_{\star}, y_{\star}, z_{\star})$, where $x_{\star}, y_{\star}$ are given in Table [\[table:parameters\]](#table:parameters), we determine $z_{\star}$ as follows: $$\begin{equation}
    z_{\star} = \frac{\sqrt{(x_{\star} -x_{\rm bubble})^{2} + (y_{\star} -y_{\rm bubble})^{2}} }{\tan i}, 
\end{equation}$$ where $i$ is the disk inclination.

To interpret the concave morphology, we develop a simple analytical model. We introduce a coordinate system $(\xi, \eta, \zeta)$ as in the left panel of Figure [4](#fig:xi_coord). The $\zeta$-axis is assumed to pass through both the star and the center of the bubble, with the positive direction of the axis pointing from the bubble center toward the star, and the origin is taken to be the stellar position. The $(\xi, \eta)$-plane corresponds to the disk plane, and the $\xi$-axis aligns with the disk major axis in the sky plane. We denote the radial distance from the $\zeta$ axis by $\rho$, as shown in the right panel of Figure [4](#fig:xi_coord), as follows: $$\begin{equation}
\rho = \sqrt{\xi^2 + \eta^2}. 
\end{equation}$$

![image](./anot_fig_update) ![image](./model_0_6.00.pdf) ![image](./vel68_8.10_inline.pdf) ![image](./model_1_8.10.pdf) ![image](./vel74_10.20_inline.pdf) ![image](./model_2_10.20.pdf)

![image](./shock_3d.pdf) ![image](./bubble_geo.pdf)

We model the vertical position of the shock boundary using a simple power-law form with a vertical offset: $$\begin{eqnarray}
\zeta_{\rm surf} (\rho) = h_{\rm shock} \left(\frac{\rho}{1 \; \text{arcsec}} \right)^{a}  + \zeta_{0}, 
\end{eqnarray}$$ where $h_{\rm shock}$ determines the height of the surface, $a$ determines the steepness of the surface, and $\zeta_0$ determines the vertical offset from the stellar position. The model is axisymmetric with respect to the $\zeta$ axis.

In the $(\xi, \eta, \zeta)$ coordinate system, the bubble center is located at $(0, 0, -d)$, where $d$ is the distance between the star and bubble center, $$\begin{equation}
 d = \sqrt{(x_{\star} -x_{\rm bubble})^{2} + (y_{\star} -y_{\rm bubble})^{2}  + z_{\star} ^{2}}. 
\end{equation}$$

We consider two cases for our models; the bubble model and the shock boundary model. To distinguish between the two cases, we introduce the angle $\theta$, which is measured from the $\zeta$-axis within a spherical coordinate system that has its origin at the bubble center $(0,0,-d)$. The angle $\theta$ is depicted in the right panel of Figure [4](#fig:xi_coord):

$$\begin{equation}
\tan \theta = \frac{\rho}{d+\zeta},
\end{equation}$$ or $$\begin{equation}
    \theta = \arctan \left(\frac{\rho}{d+\zeta}\right).
\end{equation}$$

We categorize the points on the surface (indicated by the red point in the panel of Figure [4](#fig:xi_coord)) into two cases based on the angle $\theta$ as follows: $$\begin{cases} 
\text{Shock boundary model} & \text{if } \theta < \theta_{\rm inter} \\
\text{Bubble model} & \text{if } \theta \geq \theta_{\rm inter},  
\end{cases}$$ where $\theta_{\rm inter}$ is the boundary value, as depicted in the right panel of Figure [4](#fig:xi_coord).

The intersection between the bubble and the shock boundary is characterized by $\theta_{\rm inter}$ or $\rho=\rho_{\rm inter}$, which can be determined by solving following equation: $$\begin{equation}
r_{\rm bubble}^{2} = \rho_{\rm inter}^{2} + (\zeta_{\rm surf}(\rho_{\rm inter}) + d)^{2},
\end{equation}$$ where both the left-hand side and the right-hand side represent the square of the distance from the bubble center. The polar angle $\theta_{\rm inter}$ is derived from $\rho_{\rm inter}$ as follows $$\begin{equation}
 \theta_{\rm inter} =  \arctan\left(\frac{\rho_{\rm inter}}{d + \zeta_{\rm surf}(\rho_{\rm inter})}\right). 
\end{equation}$$ Note that the values of $\theta_{\rm inter}$ and $\rho_{\rm inter}$ depend on $r_{\rm bubble}$.

For the bubble model, the spatial distribution and velocity fields are taken to be same as those in the simple expansion model in Sec [3.1](#sec:exp_bubble). In the shock boundary model, we assume that the velocity direction aligns with the radial direction from the bubble center, and the velocity amplitude is constant, $u_{\rm bubble}$. Specifically, the velocity field on the boundary $\mathbf{u}$ in the rest frame of the bubble center is given as follows: $$\begin{equation}
\mathbf{u} = u_{\rm bubble} \left(\frac{\mathbf{ S}}{||\mathbf{ S}||}\right) , 
\end{equation}$$ where $\mathbf{S}$ is the position vector from the bubble center to the point on the boundary. This equation is assumed in a similar manner to Eq ([\[eq:bubble_vel\]](#eq:bubble_vel)).

Assuming the above models, we derive analytical expressions for the predicted shock-boundary contours with fixed $v_{\rm LOS}$, as presented in Appendix [7](#sec:analytical_shock). We optimize the shell models by comparing the predicted contours $(x_{\rm contour}(v_{\rm LOS}, \rho), y_{\rm contour}(v_{\rm LOS}, \rho))$ with the observed shock boundaries. We initially attempted manual optimization as in Section [3.1](#sec:exp_bubble); however, due to the model’s increased complexity, we relied on numerical optimization. To facilitate efficient optimization, we manually approximate the observed shock boundaries by discrete points along each channel. For each velocity, we calculate the sum of the distances from the points to the predicted model contours. The total distance metric is defined as the sum of these minimum distances across all selected channels. We minimize this aggregate distance by adjusting the parameters of the bubble model.

Table [1](#table:model_parameters) presents the derived parameters for the bubble model. To account for the range in bubble width, we adopt two values for $r_{\rm bubble}$, namely $5.5 \ensuremath{''}$ and $6.5\ensuremath{''}$. The optimized models are shown as white dotted and dashed lines in Figure [3](#fig:channels). Our model reasonably replicates the observed shock boundary morphology, supporting our estimation of the stellar position. The three-dimensional distance between the shock’s apex and the stellar position is $\zeta_0 = -0.28\ensuremath{''}$, which corresponds to approximately 38 au. The right panel in Figure [4](#fig:xi_coord) shows a side view of the optimized shock boundary models with $r_{\rm bubble}=5.5 \ensuremath{''}$ and $6.5\ensuremath{''}$, where $(\rho_{\rm inter}, \theta_{\rm inter}) = (2.23\ensuremath{''}, 23.9^{\circ})$ and $(2.92\ensuremath{''}, 26.7^{\circ})$, respectively.

## The deformation of the disk by the expanding bubble

Beyond the shock boundary, the protoplanetary disk of WSB 52 is distinctly resolved, exhibiting clear spatial and kinematic separation from the shock front. Figure [5](#fig:channelszoom) provides channel maps with a zoomed-in view of the stellar disk. The disk appears to be deformed. The alignment of the shock front with the direction of disk deformation suggests that the shock front of the expanding bubble is colliding with and perturbing the protoplanetary disk.

On the other hand, the dusty disk—significantly more compact than the gas disk as shown in Figure [5](#fig:channelszoom)—appears unaffected by the shock. The disk is overall optically thick and exhibits only marginal substructure in the DSHARP sample (cite: huang2018), with possible shallow gap/ring pairs at 13/17 and 21/25 au (cite: jennings2022). Its extent corresponds to a high-density region where deformations are less likely, as observed in the inner regions of the gas disk.

To quantify the deformation, we compare a Keplerian disk model (cite: 2020zndo...4321137T; 2021ApJS..257....2C) with the observed disk. In the implementation, we use our code for the Keplerian mask, which is publicly available at <https://github.com/rorihara/Keplerian_Mask_Generator> and overall faster than an existing code, `keplerian_mask` at <https://github.com/richteague/keplerian_mask> (cite: 2020zndo...4321137T).

We assume an axisymmetric disk. The height of the disk, $h(\rho)$, is specified by the following model: $$\begin{equation}
h(\rho) = h_0 \left( \frac{\rho}{100 \, \text{au}} \right)^p, 
\end{equation}$$ where $h_0$ determines the characteristic height for the model, $p$. Here, we only consider the upper layer of the disk, given that we only see that side in the observed disk.

The velocity field of the disk model $v_{\rm model}$ is assumed to follow the Keplerian motion, and an additional systemic velocity $v_{\text{sys},\star}$ is applied as an offset along the line-of-sight direction. Given each observational velocity $v_{\rm chan}$ and the channel width $\Delta v_{\rm chan}$, we make the masked region with $|v_{\rm model} - v_{\rm chan}| < \Delta v_{\rm chan}$. Here, we ignore the intrinsic line widths for the simplicity.

In the modeling, we adopt the stellar mass and the disk parameters in Table [\[table:parameters\]](#table:parameters). We assume the rotation direction of the disk to be consistent with the channel maps. The outer disk radius is assumed to be $150$ au. Due to significant cloud contamination in the relevant channels, the star’s systemic velocity $v_{\text{sys},\star}$ remains highly uncertain. As the reference value we assume it to be $3.9$ km/s, but it may vary 0.5-1.0 km/s based on the observed maps. The assumed parameters are summarized in Table [1](#table:model_parameters).

The dashed lines in Figure [5](#fig:channelszoom) present a Keplerian disk model, which delineates the iso-velocity surfaces of the disk’s flared upper layer as described. We present results using $h_0 = 5$ au and $p = 1$, demonstrating that the observed curvature of the disk cannot be accounted for by a simple flared disk model. We also test other parameters but consistently observe significant discrepancies, indicating intrinsic deformations likely caused by external forces.

Additionally, we identify high-velocity components near the disk reaching up to approximately $v_{\rm LOS} = 18$ km/s, some of which exceed the star’s escape velocity of $\sim 3$ km/s at 100 au. This suggests ongoing mass loss from the disk. Figure [5](#fig:channelszoom) includes an integrated image highlighting regions with $13$ $\text{km/s}<v_{\rm LOS}$.

![image](./vel51_2.15.pdf) ![image](./vel50_1.80.pdf) ![image](./vel49_1.45.pdf) ![image](./vel61_5.65.pdf) ![image](./vel62_6.00.pdf) ![image](./vel63_6.35.pdf) ![image](./image_zoom_sum.pdf) ![image](./image_zoom_sum_v13.00.pdf)

# Discussion

## The proposed scenario for the observation

As described in Section 3.1, the shell-like patterns can be well explained by the expanding bubble model, which is distinct from sideways motions of bow shocks perpendicular to the jet directions (cite: Tafalla2017) and from outflow phenomena (cite: harada2023). The similar bubbles have been observed in XZ Tau (cite: Krist1997; Krist1999; Kirst2008) and SVS 13 (cite: Hodapp2014). Previous studies (cite: Kirst2008; Hodapp2014; gardner2016) propose that such bubbles result from the compression of cold gas, possibly ejected during prior outflow events, by powerful jet outbursts. The compressed hot gas exerts high pressure, leading to a spherical expansion that sweeps up interstellar material, manifesting as a shell. We postulate that the similar jet-driven mechanisms are responsible for the observed expanding bubble in WSB 52.

However, we note that similar CO bubble events have not been identified in other stellar systems, including XZ Tau and SVS 13. Although ALMA observations have revealed circumstellar dust and gas in these systems (cite: ichikawa2021; rodriguez2022; bianchi2023) and an outflow in XZ Tau (cite: zapata2015), no corresponding CO emission from the bubbles has been detected. We therefore caution that the origin of the bubble in WSB 52 remains uncertain and warrants further investigation. The observed difference may be related to the fact that WSB 52 is a single star, while XZ Tau and SVS 13 are binary systems, but the effect of binarities is unclear. Nonetheless, this paper focuses on the outcome of the bubble’s interaction with the disk rather than its formation mechanism, and its conclusions do not depend on any specific assumption regarding the bubble’s origin.

The key distinction between the bubbles observed in XZ Tau/SVS 13 and the current bubble in WSB 52 lies in their velocity profiles. The radial expansion velocity of the WSB 52 bubble ($12.5$ km/s) exceeds its velocity relative to the star, enabling a returning motion toward the star. In contrast, previously reported bubbles in XZ Tau and SVS 13 primarily exhibit outward discharge without significant returning motion. This returning movement in WSB 52 facilitates interaction between the bubble and the circumstellar material. The observed brightness distribution of the bubble sphere in Figure [1](#fig:channels_maps_all) appears asymmetric: the side close to the star is bright, while the side far from the star remains dark. This asymmetry is consistent with a greater amount of circumstellar material near the star, where strong interactions with the bubble have occurred.

We also explore whether the jets could supply the energy driving the current bubble. The jet mass ejection rates for Class II T Tauri stars have been found to range from $10^{-9}$ to $10^{-7}$ $M_{\odot}/{\rm yr}$ (cite: Ellerbroek2013). Furthermore, several systems have been reported to exhibit episodic ejections on timescales of around 10 years and rates exceeding $10^{-8}$ $M_{\odot}/{\rm yr}$ (cite: takami2023; pyo2024). A jet outburst characterized by a radial velocity of 200 km/s and a mass ejection rate of $10^{-7}$ $M_{\odot}/{\rm yr}$ yields a kinetic energy rate of approximately $0.4 \times 10^{41}$ erg/yr. This energy output is sufficient to drive an expanding bubble with kinetic energy in the range of $0.4-4 \times 10^{41}$ erg within one to ten years. In the current case, the mass accretion rate for WSB 52 was estimated to be $10^{-7.6 \pm 0.5}, M_{\odot}/\mathrm{yr}$ (cite: Natta2006; andrews2018), implying that a jet mass ejection rate can be as high as $10^{-8}-10^{-7}$ $M_{\odot}/\mathrm{yr}$ (cite: Ellerbroek2013). Given the temporal variability of jet activity, it is reasonably that jets were more powerful in the past, thereby driving the bubble formation.

Figure [2](#fig:summary) summarizes the proposed scenario accounting for these features from the formation of the bubble to the current state. We propose that a uniform explosion is sweeping through the circumstellar material, thereby perturbing and shaking or even destructing the disk structure.

## Simple model for disk deformation by bubble expansion

As observed, the disk is deformed along the expansion direction of the bubble. This deformation may be explained by considering the ram pressure exerted by the bubble on the disk, in a manner similar to the interaction between supernova ejecta and a protoplanetary disk (cite: Chevalier2000; Ouellette2007). Assuming a gas flow with density $\rho_{\rm flow}$ and the velocity $v_{\rm flow}$, the ram pressure $\rho_{\rm flow} v_{\rm flow}^2$ acts on the disk, which has a surface density $\Sigma_{\rm disk}$. The corresponding equation of motion is $$\begin{equation}
    \rho_{\rm flow} v_{\rm flow}^2 = \Sigma_{\rm disk} a, 
\end{equation}$$ where $a$ is the acceleration. Assuming that the acceleration is maintained for a duration $\Delta t$, the surface density of the impacting flow is given by $$\begin{equation}
    \Sigma_{\rm flow} = \rho_{\rm flow} v_{\rm flow} \Delta t.
\end{equation}$$ Thus, the vertical velocity $v_{\zeta}$ acquired by the disk is $$\begin{equation}
    v_{\zeta} = a \Delta t = \frac{\Sigma_{\rm flow}}{\Sigma_{\rm disk}} v_{\rm flow},
\end{equation}$$ and the resulting vertical displacement $D_{\zeta}$ is approximated by $$\begin{equation}
    D_{\zeta} = \frac{1}{2} a \Delta t^2 = \frac{\Sigma_{\rm flow}}{2 \Sigma_{\rm disk}}\ v_{\rm flow} \Delta t.
\end{equation}$$

The surface density associated with the bubble is expressed as $$\begin{equation}
    \Sigma_{\rm flow} = \frac{M_{\rm bubble}}{4 \pi r_{\rm bubble}^2},
\end{equation}$$ where $r_{\rm bubble}$ is the bubble radius and $M_{\rm bubble}$ is its mass.

Consequently, the vertical displacement becomes $$\begin{align}
    D_{\zeta} &= 0.01\,\text{au} \left(\frac{M_{\rm bubble}}{10^{-4}\,M_{\odot}}\right) \left(\frac{r_{\rm bubble}}{700\,\text{au}}\right)^{-2} \nonumber\\
    &\quad \times \left(\frac{\Sigma_{\rm disk}}{1\,\text{g/cm}^2}\right)^{-1}
    \left(\frac{v_{\rm flow}}{12.5\,\text{km/s}}\right)
    \left(\frac{\Delta t}{50\,\text{yr}}\right).
\end{align}$$ Figure [6](#fig:disp_density) illustrates the result with $(v_{\rm flow}, r_{\rm bubble}, \Delta t) = (12.5 \,\text{km/s}, 700\,\text{au}, 50\,\text{yr})$, where $v_{\rm flow}=12.5 \text{km/s}$ represents the bubble expansion velocity, $r_{\rm bubble}=700\,\text{au}$ is the current bubble radius, and $\Delta t$ is taken to be 50 yr, approximately equal to the shell’s crossing time over 1 arcsec. Under the assumption $\Sigma_{\rm disk}=1\,\text{g/cm}^2$, the vertical displacement is approximately 0.01 au. This value is likely negligible and inconsistent with the observed significant deformation.

If, however, the bubble-disk interaction began at an earlier phase when the disk and bubble centers were closer, we can expect a larger vertical displacement. In that case, the bubble’s relative velocity with respect to the disk center should be considered, and the bubble radius is not constant. Assuming a relative velocity of $v_{\rm rel}= 7.5$ km/s ($\simeq$ 1.5 au/yr), as estimated from the current separation between the two centers, the effective flow velocity is $v_{\rm flow} = u_{\rm bubble} - v_{\rm rel} = 5$ . Ignoring the time variability of the bubble radius, the vertical displacement can be then estimated as: $$\begin{align}
    D_{\zeta} &= 0.8 \,\text{au} \left(\frac{M_{\rm bubble}}{10^{-4}\,M_{\odot}}\right) \left(\frac{r_{\rm bubble}}{30\,\text{au}}\right)^{-2} \nonumber\\
    &\quad \times \left(\frac{\Sigma_{\rm disk}}{1\,\text{g/cm}^2}\right)^{-1}
    \left(\frac{v_{\rm flow}}{5\,\text{km/s}}\right)
    \left(\frac{\Delta t}{20\,\text{yr}}\right).
\end{align}$$ Here, we adopt fiducial values with $(v_{\rm flow}, r_{\rm bubble}, \Delta t) = (5\,\text{km/s}, 30\,\text{au}, 20\,\text{yr} \,(\simeq 30 \, \text{au}/v_{\rm rel}))$, and the expected displacement is shown in Figure [6](#fig:disp_density). Assuming a lower surface density, a smaller effective radius, or increased bubble mass (or energy), the resulting displacement can become significantly larger. Overall, the feedback on the disk is expected to be weaker in the dense inner regions and stronger in the less-dense outer regions, which is consistent with the observation that the deformation increases with radius, while no significant deformation is observed in the compact dusty disk.

Although the current model provides a preliminary interpretation of the disk deformation, further detailed modeling of the observed vertical displacement can offer valuable constraints on the evolution of the bubble and the surface density profile of the disk.

![](./density_Dz.pdf)

## Implications for star and planet formation

Jets and outflows play a critical role in removing excess angular momentum from accreting materials by expelling mass flux (cite: Blandford1982). Their substantial kinetic energy is injected into surrounding molecular clouds, significantly influencing the interstellar environment. Herbig-Haro objects, luminous nebulae at jet shock fronts, serve as direct evidence of such energy injections (cite: Reipurth2001). This energy input at larger scales increases turbulence and pressure within surrounding environments, and thereby regulating star formation efficiency (cite: Norman1980; Nakamura2007). Our findings extend this impact to the protoplanetary disk scale, demonstrating that jets can interact with circumstellar environments through expanding bubbles. The observed disk deformation indicates that the effects of such jet-driven bubbles are substantial, particularly in the outer disk regions.

Beyond accretion from larger structures like envelopes (cite: ohashi2014; sakai2014; yen2014), several mechanisms transfer energy and materials into protoplanetary disks. Proplyds, or ionized disks, are heated by radiation from nearby massive stars, as seen in the Orion Nebula Cluster (cite: odell1993; bally2000). Supernovae can reshape the structure of protoplanetary disks while injecting short-lived radioactive isotopes, such as $^{26}$Al and $^{60}$Fe, which influence the thermal evolution of forming planetary systems (cite: Chevalier2000; Ouellette2007). Outbursts from central stars, such as FU Ori-type events, can also reshape disk structures by altering the temperature distribution, which shifts snowline positions (cite: Banzatti2015; cieza2016; lee2019). Our study reveals a novel mechanism of energizing a disk through jet-induced bubbles, especially influencing the vertical structure in localized environments.

The deformation of the disk shape provides clear evidence of significant kinetic energy injection into the system. This interaction suggests that part of the disk mass could be lost due to the strong momentum transfer from the bubble. The vertical extent and dynamics of the gas may be enhanced by the explosive event, altering turbulence levels through shock interactions. Shock heating could also energize dust grains, potentially leading to molecular desorption, which could produce observable signatures—for example, through the emergence of specific shock tracers.

# Conclusion

In this study, we report the first case for the jet feedback on the disk via an expanding bubble. Specifically, jets generate bubbles, which interact with disks. The disks again feed the jets. We name this process as “*jet-bubble-disk interaction*”.

The current analysis solely relies on $^{12}\mathrm{CO}\,(J=2\mbox{--}1)$. Therefore, follow-up observations of CO isotopes are highly desirable to gain a better understanding of the mass and temperature distribution. Additionally, follow-up observations for other chemical species are helpful for investigating the chemical compositions of the gas, which may have been altered by the bubble interaction. Furthermore, detailed dynamical modeling of the disk’s deformation caused by bubble wind will be important for understanding the bubble’s effect on the disk.

In our analysis, among the DSHARP targets, only WSB 52 exhibits similar events, suggesting that such explosive interactions may be rare. The estimation of occurrence rates of bubbles is challenging due to the uncertain frequency of jet-interacting cold material. Such cold material may be ejecta from previous outflows or small-scale cloudlets that are inherent in parent molecular clouds (cite: koyama2000; hennebelle2012). To better understand the prevalence and impact of these bubbles, more extensive surveys for similar explosive events are highly recommended. For example, systems with higher mass accretion rates—such as protostars and FU Ori-type stars—could exhibit more energetic phenomena. In addition, theoretical modelings are necessary to better understand the mechanisms underlying jet-induced bubble formation and their long-term effects on protoplanetary disks.

# Acknowledgements

We thank an anonymous referee for constructive comments. This work was supported by JSPS KAKENHI grant number 22H01274. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00486.S, ADS/JAO.ALMA #2015.1.00964.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

# Availability of data and materials

$^{12}\mathrm{CO}\,(J=2\mbox{--}1)$ image cube is provided in <https://doi.org/10.5281/zenodo.15314468>. The raw ALMA data are publicly available via the ALMA archive https://almascience.nrao.edu/aq/. The DSHARP data used in this article are available in the DSHARP Data Release at https://bulk.cv.nrao.edu/almadata/lp/DSHARP.

# Code availability

The original code used for reconstrucing the images is available in the DSHARP Data Release at https://bulk.cv.nrao.edu/almadata/lp/DSHARP. The Keplerian mask code is publicly available at <https://github.com/rorihara/Keplerian_Mask_Generator>.

*Software*: `Astropy` (cite: astropy2013; 2018AJ....156..123A; 2022ApJ...935..167A), `CASA` (cite: mcmullin2007), `CARTA` (cite: comrie2021carta), `Jupyter Notebook` (cite: kluyver2016), `Matplotlib` (cite: hunter2007), `NumPy` (cite: walt2011), `Pandas` (cite: mckinney-proc-scipy-2010), `SciPy` (cite: virtanen2020).

# Estimation of mass and kinematic energy of bubble using $^{12}$CO emission line 

We perform an order-of-magnitude estimation of the bubble’s mass and kinematic energy to assess whether the observed disk can be plausibly energized by the stellar jet. For this estimation, we utilize the intensities of $^{12}$CO emission line, assuming that the line emission is not fully optically thick.

Assuming the local thermal equilibrium (LTE), we can derive the molecular column density from the observed optical depth as follows (cite: mangum2015; orihara2023): $$\begin{eqnarray}
    N_{\rm{}tot}=&\cfrac{3h}{8\pi^3|\mu_{\rm{}lu}|^2}\cfrac{Q_{\rm{}rot}}{g_{\rm{}u}}\exp\Big(\cfrac{E_{\rm{}u}}{kT_{\rm{}ex}}\Big) 
    \Big[\exp\Big(\cfrac{h\nu}{kT_{\rm{}ex}}\Big)-1\Big]^{-1}\int\tau_{\rm{}g}dv,
\end{eqnarray}$$ where $N_{\rm{}tot}$ is the total column density, $h$ is the Planck constant, $E_{\rm{}u}$ is the energy of the upper energy level, $k$ is the Boltzmann constant, $T_{\rm{}ex}$ is the excitation temperature, which is assumed to be equal to the gas temperature in the LTE analysis, $\nu$ is the frequency of the transition, and $\int \tau_{\rm{}g}dv$ is the integrated optical depth.

The square of the transition dipole moment, $|\mu_{\rm{}lu}|^2$, is given by: $$\begin{eqnarray}
    |\mu_{\rm{}lu}|^2=\mu^2 \frac{J_{\rm{}u}^2}{J_{\rm{}u}(2J_{\rm{}u}+1)},
\end{eqnarray}$$ where $\mu$ $(= 0.110 \times 10^{-18}$ esu cm for $^{12}$CO) is the permanent dipole moment, and $J_{\rm{}u}$ is the rotational quantum number of the upper energy level. The degeneracy of the upper energy level, $g_{\rm{}u}$, is given by: $$\begin{eqnarray}
    g_{\rm{}u}=2J_{\rm{}u}+1,
\end{eqnarray}$$ and the energy of the upper energy level, $E_{\rm{}u}$, is given by: $$\begin{eqnarray}
    E_{\rm{}u}=hBJ_{\rm{}u}(J_{\rm{}u}+1),
\end{eqnarray}$$ where $B$ is the rotational constant $(= 57635.96$ MHz for $^{12}$CO). The partition function $Q_{\rm{}tot}$ is given by $$\begin{eqnarray}
  Q_{\rm{}rot} = \sum_{i} g_{i} \exp\left(-\frac{E_{i}}{kT}\right), 
\end{eqnarray}$$ where the value is approximated by summing up to $J_{i}<20$ in this study. The optical depth is derived from the observed intensity $I_\nu = I_{\rm obs}$ and the

Planck function $B_\nu (T_{\rm g})$ using the following relation: $$\begin{equation}
I_\nu = B_\nu (T_{\rm g})  (1 - e^{-\tau_{\rm g}}). 
\end{equation}$$ Specifically, we use $$\begin{equation}
\tau_{\rm g} = - \ln \left(1 - \frac{ I_\nu}{ B_\nu (T_{\rm g}) } \right).
\end{equation}$$ With the derived column density $N_{\rm{tot}}$, the gas column density is then calculated by $$\begin{eqnarray}
    \Sigma_{\rm{}g} =\frac{m_{\rm{H_2}}N_{\rm{tot}}}{X}, \label{eq:sigma_mass}
\end{eqnarray}$$ where $m_{\rm{H_2}}$($=3.32\times10^{-24}~\rm{g}$) is the molecular mass of $\rm{H_2}$, and $X$ is the molecular abundance ratio with $\rm{}H_2$. We assume $X=10^{-4}$ for $^{12}$CO.

The mass is derived by integrating Eq. ([\[eq:sigma_mass\]](#eq:sigma_mass)) over each pixel, using the estimates of $\tau_{\rm g}$ obtained from the real cube data. The integration region is defined between two circles corresponding to the bubble models with radii $r_{\rm bubble} = 4$ and $7.0$ arcsec. To remove the contribution from disk emission, we exclude intensities within 1.5 arcsec from the star. We also remove channels with $v_{\rm LOS}$ between 1.45 and 6 km/s to eliminate cloud contamination. The mass depends on the unknown gas temperature, so we vary the temperature from $25$ K to $95$ K in steps of $10$ K.

During the analysis, we notice that $I_\nu$ and $\tau_{\rm g}$ can take negative values because of random noises, thus possibly biasing the estimation of $\tau_{\rm g}$. To understand the possible uncertainty in the mass, we employ three different integration methods : (1) Integrating by forcing $I$ to be zero if it is negative, (2) Integrating only in regions where $I$ is above the 3-sigma level, and (3) Integrating without applying any specific conditions, accounting for both positive and negative fluxes. To reduce the biases, we also smooth the cube data using a beam size of 0.25 arcsec reducing the number of negative pixels. As a result, we find that the mass range is $0.2 - 1.1 \times 10^{-4} M_{\odot}$.

The kinematic energy is then estimated from the total mass and the velocity as follows: $$\begin{equation}
E_{\rm shell} = \frac{1}{2} m_{\rm g} u_{\rm bubble}^{2}. 
\end{equation}$$ Assuming $u_{\rm bubble} = 12.5$ km/s and the mass range, we find $E_{\rm kin}$ varies between $0.3-1.6 \times10^{41}$ erg. The method (1) gives $E_{\rm kin}=0.8-1.6 \times10^{41}$ erg, and the other two give the lower total energy, $E_{\rm kin}=0.3-1.0 \times10^{41}$ erg. As discussed in the main text, this energy can be explained by the energy injection though the stellar jet.

# Analytical solution for iso-velocity section for shock boundary model

For the analysis in Sec [3.2](#sec:shock_boundary), we derive an analtycial expression for the model’s projection onto the observational $(x,y)$ coordinate system with fixed $v_{\rm LOS}$. We denote the unit vector from the bubble center to the star by $\mathbf{\hat{\zeta}} = (\hat{\zeta}_{x}, \hat{\zeta}_{y}, \hat{\zeta}_{z})^{T}$. To make the coordinate system, we prepare two orthogonal unit vectors as follows: $$\begin{eqnarray}
\mathbf{\hat{\xi}} &\equiv& (\hat{\xi}_{x}, \hat{\xi}_{y}, \hat{\xi}_{z})^{T} = \frac{1} { \sqrt{ \hat{\zeta}_x^{2} +\hat{\zeta}_y^{2}}} (-\hat{\zeta}_{y}, \hat{\zeta}_{x}, 0)^{T}, \\
\mathbf{ \hat{\eta}} &\equiv& (\hat{\eta}_{x}, \hat{\eta}_{y}, \hat{\eta}_{z})^{T} = \mathbf{ \hat{\zeta}} \times \mathbf{\hat{\xi}} = \frac{1} { \sqrt{ \hat{\zeta}_x^{2} +\hat{\zeta}_y^{2}}} (-\hat{\zeta}_{z} \hat{\zeta}_{x}, -\hat{\zeta}_{z} \hat{\zeta}_{y}, \hat{\zeta}_{x}^{2} + \hat{\zeta}_{y}^{2}) ^{T}, 
\end{eqnarray}$$ where $\mathbf{\hat{\xi}}$ and $\mathbf{\hat{\eta}}$ align with $\xi$ and $\eta$ axes, respectively.

The position on the shock boundary $\mathbf{S}$ measured from the bubble center is given by $$\begin{equation}
\mathbf{S} = (d + \zeta_{\rm surf}(\rho))\mathbf{\hat{\zeta}} + (\rho \cos \phi)\mathbf{\hat{\xi}} + (\rho \sin \phi) \mathbf{ \hat{\eta}}, \label{eq:boundary_pos}
\end{equation}$$ where $\phi$ is the azimuthal angle for $(\xi, \eta)$, ranging from $0$ to $2\pi$: $$\begin{align}
    \xi &= \rho \cos \phi,  \\
    \eta &= \rho \sin \phi.  
\end{align}$$ $\rho$ can vary within the range $[0, \rho_{\rm inter}]$.

The line-of-sight velocity $v_{\rm LOS}$ for the boundary model is given by $$\begin{align}
v_{\rm LOS} &= u_{\rm bubble}\frac{\mathbf{S}\cdot \mathbf{\hat{e}}_{z} }{||\mathbf{S}||} + v_{\rm sys, bubble}  \\
&= \frac{u_{\rm bubble}}{\sqrt{(d + \zeta_{\rm surf}(\rho))^{2} + \rho^{2}}}  \left[(d + \zeta_{\rm surf}(\rho))\hat{\zeta}_{z} + \left( \rho \sin \phi  \sqrt{ \hat{\zeta}_x^{2} +\hat{\zeta}_y^{2}}\right) \right] + v_{\rm sys, bubble}, 
\end{align}$$ where $\mathbf{\hat{e}}_{z}$ is the unit vector in the direction of the $z$-axis (the line-of-sight direction). We can solve $\phi$ from $v_{\rm LOS}$ and $\rho$ as follows: $$\begin{equation}
\phi(v_{\rm LOS}, \rho) = \arcsin \left [ \frac{1}{\rho \sqrt{\hat{\zeta}_{\rm x}^{2} + \hat{\zeta}_{\rm y}^{2}}} \left[ \frac{(v_{\rm LOS}- v_{\rm sys, bubble}) \sqrt{(d + \zeta_{\rm surf}(\rho))^{2} + \rho^{2}}}{u_{\rm bubble}} - (d + \zeta_{\rm surf}(\rho)) \hat{\zeta}_{z} \right]\right]. \label{eq:phi_los_rho}
\end{equation}$$

According to Eq ([\[eq:boundary_pos\]](#eq:boundary_pos)), the positions on the boundary $(x_{\rm surface}, y_{\rm surface})$ are given by $$\begin{align}
x_{\rm surface} &= \mathbf{S} \cdot \mathbf{\hat{e}}_{x} 
=  (d + \zeta_{\rm surf}(\rho)) \hat{\zeta}_x + (\rho \cos \phi)\hat{\xi}_x + (\rho \sin \phi) \hat{\eta}_x,  \\
y_{\rm surface} &= \mathbf{S} \cdot \mathbf{\hat{e}}_{y} 
=(d + \zeta_{\rm surf}(\rho)) \hat{\zeta}_y + (\rho \cos \phi)\hat{\xi}_y + (\rho \sin \phi) \hat{\eta}_y.  \label{eq:y_position}
\end{align}$$ Using the above equations and Eqs ([\[eq:phi_los_rho\]](#eq:phi_los_rho)-[\[eq:y_position\]](#eq:y_position)), the iso-velocity contour for the boundary model at the observed velocity $v_{\rm LOS}$ can be obtained as follows: $$\begin{eqnarray}
x_{\rm contour}(v_{\rm LOS}, \rho)  &=& (d + \zeta_{\rm surf}(\rho))\hat{\zeta}_{x} + \frac{\left (- \rho \hat{\zeta}_{y} \cos \phi(v_{\rm LOS}, \rho) - \rho \hat{\zeta}_{z} \hat{\zeta}_{x}  \sin \phi(v_{\rm LOS}, \rho) \right)} { \sqrt{ \hat{\zeta}_x^{2} +\hat{\zeta}_y^{2}}} ,  \\
y_{\rm contour}( v_{\rm LOS}, \rho)  &=& (d + \zeta_{\rm surf}(\rho))\hat{\zeta}_{y}  + \frac{ \left ( \rho  \hat{\zeta}_{x} \cos \phi(v_{\rm LOS}, \rho) - \rho  \hat{\zeta}_{z} \hat{\zeta}_{y} \sin \phi(v_{\rm LOS}, \rho) \right)} { \sqrt{ \hat{\zeta}_x^{2} +\hat{\zeta}_y^{2}}}, 
\end{eqnarray}$$ where $\rho$ can vary within the range $[0, \rho_{\rm inter}]$.

natexlab

(ref: andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2022ApJ...935..167A) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: bae2022) Bae, J., Isella, A., Zhu, Z., et al. 2022, arXiv preprint arXiv:2210.13314

(ref: bally2006) Bally, J. 2016, ARA&A, 54, 491, doi: [`10.1146/annurev-astro-081915-023341`](http://doi.org/10.1146/annurev-astro-081915-023341)

(ref: bally2000) Bally, J., O’Dell, C. R., & McCaughrean, M. J. 2000, AJ, 119, 2919, doi: [`10.1086/301385`](http://doi.org/10.1086/301385)

(ref: Banzatti2015) Banzatti, A., Pinilla, P., Ricci, L., et al. 2015, ApJL, 815, L15, doi: [`10.1088/2041-8205/815/1/L15`](http://doi.org/10.1088/2041-8205/815/1/L15)

(ref: bianchi2023) Bianchi, E., López-Sepulcre, A., Ceccarelli, C., et al. 2023, Faraday Discussions, 245, 164, doi: [`10.1039/D3FD00018D`](http://doi.org/10.1039/D3FD00018D)

(ref: Blandford1982) Blandford, R. D., & Payne, D. G. 1982, MNRAS, 199, 883, doi: [`10.1093/mnras/199.4.883`](http://doi.org/10.1093/mnras/199.4.883)

(ref: brogan2015) Brogan, C., Pérez, L., Hunter, T., et al. 2015, The Astrophysical journal letters, 808, L3

(ref: Cacciapuoti2024) Cacciapuoti, L., Testi, L., Podio, L., et al. 2024, ApJ, 961, 90, doi: [`10.3847/1538-4357/ad0f17`](http://doi.org/10.3847/1538-4357/ad0f17)

(ref: Chevalier2000) Chevalier, R. A. 2000, ApJL, 538, L151, doi: [`10.1086/312814`](http://doi.org/10.1086/312814)

(ref: cieza2016) Cieza, L. A., Casassus, S., Tobin, J., et al. 2016, Nature, 535, 258, doi: [`10.1038/nature18612`](http://doi.org/10.1038/nature18612)

(ref: comrie2021carta) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, Astrophysics Source Code Library, ascl

(ref: 2021ApJS..257....2C) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2, doi: [`10.3847/1538-4365/ac1430`](http://doi.org/10.3847/1538-4365/ac1430)

(ref: rodriguez2022) Diaz-Rodriguez, A. K., Anglada, G., Blázquez-Calero, G., et al. 2022, ApJ, 930, 91, doi: [`10.3847/1538-4357/ac3b50`](http://doi.org/10.3847/1538-4357/ac3b50)

(ref: Ellerbroek2013) Ellerbroek, L. E., Podio, L., Kaper, L., et al. 2013, A&A, 551, A5, doi: [`10.1051/0004-6361/201220635`](http://doi.org/10.1051/0004-6361/201220635)

(ref: Federrath_2013) Federrath, C., & Klessen, R. S. 2013, The Astrophysical Journal, 763, 51, doi: [`10.1088/0004-637X/763/1/51`](http://doi.org/10.1088/0004-637X/763/1/51)

(ref: frank2014) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451–474, doi: [`10.2458/azu_uapress_9780816531240-ch020`](http://doi.org/10.2458/azu_uapress_9780816531240-ch020)

(ref: gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: gaia2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: gardner2016) Gardner, C. L., Jones, J. R., & Hodapp, K. W. 2016, ApJ, 830, 113, doi: [`10.3847/0004-637X/830/2/113`](http://doi.org/10.3847/0004-637X/830/2/113)

(ref: Hansen2012) Hansen, C. E., Klein, R. I., McKee, C. F., & Fisher, R. T. 2012, The Astrophysical Journal, 747, 22, doi: [`10.1088/0004-637X/747/1/22`](http://doi.org/10.1088/0004-637X/747/1/22)

(ref: harada2023) Harada, N., Tokuda, K., Yamasaki, H., et al. 2023, ApJ, 945, 63, doi: [`10.3847/1538-4357/acb930`](http://doi.org/10.3847/1538-4357/acb930)

(ref: Hartigan1995) Hartigan, P., Edwards, S., & Ghandour, L. 1995, ApJ, 452, 736, doi: [`10.1086/176344`](http://doi.org/10.1086/176344)

(ref: haugbolle2019) Haugbølle, T., Weber, P., Wielandt, D. P., et al. 2019, AJ, 158, 55, doi: [`10.3847/1538-3881/ab1591`](http://doi.org/10.3847/1538-3881/ab1591)

(ref: hayashi1985) Hayashi, C., Nakazawa, K., & Nakagawa, Y. 1985, in Protostars and Planets II, ed. D. C. Black & M. S. Matthews, 1100–1153

(ref: hennebelle2012) Hennebelle, P., & Falgarone, E. 2012, A&ARv, 20, 55, doi: [`10.1007/s00159-012-0055-y`](http://doi.org/10.1007/s00159-012-0055-y)

(ref: Hodapp2014) Hodapp, K. W., & Chini, R. 2014, ApJ, 794, 169, doi: [`10.1088/0004-637X/794/2/169`](http://doi.org/10.1088/0004-637X/794/2/169)

(ref: huang2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: ichikawa2021) Ichikawa, T., Kido, M., Takaishi, D., et al. 2021, ApJ, 919, 55, doi: [`10.3847/1538-4357/ac0dc3`](http://doi.org/10.3847/1538-4357/ac0dc3)

(ref: jennings2022) Jennings, J., Booth, R. A., Tazzari, M., Clarke, C. J., & Rosotti, G. P. 2022, MNRAS, 509, 2780, doi: [`10.1093/mnras/stab3185`](http://doi.org/10.1093/mnras/stab3185)

(ref: kluyver2016) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in IOS Press, 87–90, doi: [`10.3233/978-1-61499-649-1-87`](http://doi.org/10.3233/978-1-61499-649-1-87)

(ref: koyama2000) Koyama, H., & Inutsuka, S.-I. 2000, ApJ, 532, 980, doi: [`10.1086/308594`](http://doi.org/10.1086/308594)

(ref: Kirst2008) Krist, J. E., Stapelfeldt, K. R., Hester, J. J., et al. 2008, AJ, 136, 1980, doi: [`10.1088/0004-6256/136/5/1980`](http://doi.org/10.1088/0004-6256/136/5/1980)

(ref: Krist1997) Krist, J. E., Burrows, C. J., Stapelfeldt, K. R., et al. 1997, ApJ, 481, 447, doi: [`10.1086/304056`](http://doi.org/10.1086/304056)

(ref: Krist1999) Krist, J. E., Stapelfeldt, K. R., Burrows, C. J., et al. 1999, ApJL, 515, L35, doi: [`10.1086/311961`](http://doi.org/10.1086/311961)

(ref: lee2020) Lee, C.-F. 2020, A&ARv, 28, 1, doi: [`10.1007/s00159-020-0123-7`](http://doi.org/10.1007/s00159-020-0123-7)

(ref: lee2019) Lee, J.-E., Lee, S., Baek, G., et al. 2019, Nature Astronomy, 3, 314, doi: [`10.1038/s41550-018-0680-0`](http://doi.org/10.1038/s41550-018-0680-0)

(ref: li2006) Li, Z.-Y., & Nakamura, F. 2006, ApJL, 640, L187, doi: [`10.1086/503419`](http://doi.org/10.1086/503419)

(ref: machida2014) Machida, M. N. 2014, ApJL, 796, L17, doi: [`10.1088/2041-8205/796/1/L17`](http://doi.org/10.1088/2041-8205/796/1/L17)

(ref: mangum2015) Mangum, J. G., & Shirley, Y. L. 2015, PASP, 127, 266, doi: [`10.1086/680323`](http://doi.org/10.1086/680323)

(ref: mathew2021) Mathew, S. S., & Federrath, C. 2021, MNRAS, 507, 2448, doi: [`10.1093/mnras/stab2338`](http://doi.org/10.1093/mnras/stab2338)

(ref: matzner2000) Matzner, C. D., & McKee, C. F. 2000, ApJ, 545, 364, doi: [`10.1086/317785`](http://doi.org/10.1086/317785)

(ref: mckinney-proc-scipy-2010) McKinney, W. 2010, in Proceedings of the 9th Python in Science Conference, ed. S. van der Walt & J. Millman, 51 – 56

(ref: mcmullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Nakamura2007) Nakamura, F., & Li, Z.-Y. 2007, ApJ, 662, 395, doi: [`10.1086/517515`](http://doi.org/10.1086/517515)

(ref: Natta2006) Natta, A., Testi, L., & Randich, S. 2006, A&A, 452, 245, doi: [`10.1051/0004-6361:20054706`](http://doi.org/10.1051/0004-6361:20054706)

(ref: Norman1980) Norman, C., & Silk, J. 1980, ApJ, 238, 158, doi: [`10.1086/157969`](http://doi.org/10.1086/157969)

(ref: oberg2021) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, in press. [`https://arxiv.org/abs/2109.06268`](https://arxiv.org/abs/2109.06268)

(ref: odell1993) O’Dell, C. R., Wen, Z., & Hu, X. 1993, ApJ, 410, 696, doi: [`10.1086/172786`](http://doi.org/10.1086/172786)

(ref: offner2017) Offner, S. S. R., & Chaban, J. 2017, ApJ, 847, 104, doi: [`10.3847/1538-4357/aa8996`](http://doi.org/10.3847/1538-4357/aa8996)

(ref: ohashi2014) Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ, 796, 131, doi: [`10.1088/0004-637X/796/2/131`](http://doi.org/10.1088/0004-637X/796/2/131)

(ref: ohashi2023) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8, doi: [`10.3847/1538-4357/acd384`](http://doi.org/10.3847/1538-4357/acd384)

(ref: orihara2023) Orihara, R., Momose, M., Muto, T., et al. 2023, PASJ, 75, 424, doi: [`10.1093/pasj/psad009`](http://doi.org/10.1093/pasj/psad009)

(ref: Ouellette2007) Ouellette, N., Desch, S. J., & Hester, J. J. 2007, ApJ, 662, 1268, doi: [`10.1086/518102`](http://doi.org/10.1086/518102)

(ref: pyo2024) Pyo, T.-S., Hayashi, M., Takami, M., & Beck, T. L. 2024, ApJ, 963, 159, doi: [`10.3847/1538-4357/ad1f59`](http://doi.org/10.3847/1538-4357/ad1f59)

(ref: Reipurth2001) Reipurth, B., & Bally, J. 2001, ARA&A, 39, 403, doi: [`10.1146/annurev.astro.39.1.403`](http://doi.org/10.1146/annurev.astro.39.1.403)

(ref: sakai2014) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78, doi: [`10.1038/nature13000`](http://doi.org/10.1038/nature13000)

(ref: shu2001) Shu, F. H., Shang, H., Gounelle, M., Glassgold, A. E., & Lee, T. 2001, The Astrophysical Journal, 548, 1029

(ref: shu1996) Shu, F. H., Shang, H., & Lee, T. 1996, Science, 271, 1545

(ref: Tafalla2017) Tafalla, M., Su, Y. N., Shang, H., et al. 2017, A&A, 597, A119, doi: [`10.1051/0004-6361/201629493`](http://doi.org/10.1051/0004-6361/201629493)

(ref: takami2023) Takami, M., Günther, H. M., Schneider, P. C., et al. 2023, ApJS, 264, 1, doi: [`10.3847/1538-4365/ac9afc`](http://doi.org/10.3847/1538-4365/ac9afc)

(ref: 2020zndo...4321137T) Teague, R. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: tsukamoto2021) Tsukamoto, Y., Machida, M. N., & ichiro Inutsuka, S. 2021, The Astrophysical Journal Letters, 920, L35, doi: [`10.3847/2041-8213/ac2b2f`](http://doi.org/10.3847/2041-8213/ac2b2f)

(ref: walt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: williams2011) Williams, J. P., & Cieza, L. A. 2011, ARA&A, 49, 67, doi: [`10.1146/annurev-astro-081710-102548`](http://doi.org/10.1146/annurev-astro-081710-102548)

(ref: yen2014) Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014, ApJ, 793, 1, doi: [`10.1088/0004-637X/793/1/1`](http://doi.org/10.1088/0004-637X/793/1/1)

(ref: zapata2015) Zapata, L. A., Galván-Madrid, R., Carrasco-González, C., et al. 2015, ApJL, 811, L4, doi: [`10.1088/2041-8205/811/1/L4`](http://doi.org/10.1088/2041-8205/811/1/L4)

</paper>

Write the methods card for this paper.