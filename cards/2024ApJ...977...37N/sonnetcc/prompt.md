# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977...37N\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977...37N",
 "title": "Turbulent Pressure Heats Gas and Suppresses Star Formation in Galactic Bar Molecular Clouds",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Nilipour, Andy",
 "n_authors": 9,
 "arxiv_id": "2410.09258",
 "doi": "10.3847/1538-4357/ad8631",
 "alma_projects_linked_by_archive": [
  "2019.2.00068.S",
  "2021.2.00001.S",
  "2022.1.00591.S"
 ]
}
```

Paper text:
<paper>
# Turbulent Pressure Heats Gas and Suppresses Star Formation in Galactic Bar Molecular Clouds

## Abstract

The Central Molecular Zone (CMZ) of the Milky Way is fed by gas inflows from the Galactic disk along almost radial trajectories aligned with the major axis of the Galactic bar. However, despite being fundamental to all processes in the nucleus of the Galaxy, these inflows have been studied significantly less than the CMZ itself. We present observations of various molecular lines between 215 and 230 GHz for 20 clouds with $\lvert \ell \rvert < 10^\circ$, which are candidates for clouds in the Galactic bar due to their warm temperatures and broad lines relative to typical Galactic disk clouds, using the Atacama Large Millimeter/submillimeter Array (ALMA) Atacama Compact Array (ACA). We measure gas temperatures, shocks, star formation rates, turbulent Mach numbers, and masses for these clouds. Although some clouds may be in the Galactic disk despite their atypical properties, nine clouds are likely associated with regions in the Galactic bar, and in these clouds, turbulent pressure is suppressing star formation. In clouds with no detected star formation, turbulence is the dominant heating mechanism, whereas photoelectric processes heat the star-forming clouds. We find that the ammonia (NH~3~) and formaldehyde (H~2~CO) temperatures probe different gas components, and in general, each transition appears to trace different molecular gas phases within the clouds. We also measure the CO-to-H~2~ X-factor in the bar to be an order of magnitude lower than the typical Galactic value. These observations provide evidence that molecular clouds achieve CMZ-like properties before reaching the CMZ.

# Introduction

The Central Molecular Zone (CMZ) is a region of molecular gas at high density and pressure within the inner $\sim$250 pc of the Milky Way (cite: morris_galactic_1996; henshaw_star_2023). The CMZ is contained within the Galactic bar, which has a semimajor axis length of about 3.5 kpc and a semiminor axis length of around 1 kpc (e.g., (cite: queiroz_milky_2021; lucey_dynamically_2023)), although some have proposed that it may be longer (cite: wegg_structure_2015; bland-hawthorn_galaxy_2016; sormani_stellar_2022). Two important families of closed orbits in a bar potential are x~1~ and x~2~ orbits (e.g., (cite: contopoulos_orbits_1989)). x~1~ orbits are elongated roughly parallel to the major axis of the bar and can form cusps and self-intersecting loops, whereas x~2~ orbits are more circular, closer to the bar center, and elongated roughly parallel to the minor axis of the bar. Shocks mainly form at the self-intersections of material on x~1~ orbits or at the x~1~-x~2~ orbit intersections (cite: athanassoula_existence_1992). The CMZ is suggested to be associated with material on x~2~ orbits (cite: binney_understanding_1991; fux_3d_1999; sormani_gas_2015; busch_living_2022), and the gas transitioning from x~1~ to x~2~ orbits is believed to form bar lanes that feed the CMZ.

While the CMZ has been extensively studied at many wavelengths (e.g., (cite: baganoff_chandra_2003; oka_hot_2005; goto_absorption_2008; jones_spectral_2012; kruijssen_what_2014; yang_fermi-lat_2015; ginsburg_dense_2016; oka_central_2019)), the bar dust lanes and inflows have been relatively neglected. (cite: sormani_mass_2019) calculate the gas inflow rate along the Milky Way bar lanes to be $2.7^{+1.5}_{-1.7} \text{ M}_\odot \text{ yr}^{-1}$ using previous observations of ^12^CO and a simple geometrical model of the inner Galaxy, but simulations show more complex dynamics, such as inflowing gas overshooting the CMZ and subsequently colliding with the bar lane on the opposite side (cite: sormani_geometry_2019), which reduces the CMZ gas accretion rate to $0.8 \pm 0.6 \text{ M}_\odot \text{ yr}^{-1}$ (cite: hatchfield_dynamically_2021). (cite: gramze_evidence_2023) suggest that this is an overestimate based on evidence that the CO-to-H~2~ X-factor in the bar region may be significantly lower than the standard Galactic value.

Observations and simulations have shown that the bar inflows induce strong shocks, large shears, and collisions with gas clouds (cite: fux_3d_1999; li_gas_2016). (cite: marshall_large_2008) find that the gas and dust distributions of the inflows overlap but are offset, which may be due to shock destruction of the dust material. (cite: liszt_molecular_2006) conclude that the presence of localized wide lines, indicating extremely large velocity gradients, in this region results from material crossing standing shocks along the inner edge of the inflows. It has also been suggested that clouds such as Bania 2 (B2; (cite: stark_clump_1986)) and G5, the cloud at $(\ell, b) = (+5.4, -0.4)$ (cite: gramze_evidence_2023), which have broad lines, warm temperatures, and shocked gas, are sites of high-velocity cloud-cloud collisions along the bar lanes (cite: fux_3d_1999; sormani_geometry_2019).

Star formation may be suppressed by the aforementioned extreme processes in the Galactic bar, but also more generally in the bar regions of barred galaxies (cite: athanassoula_existence_1992). However, observations of star formation in the bar region have been largely limited to nearby galaxies, and the effect of these dynamics on star formation efficiency is still poorly understand (cite: diaz-garcia_molecular_2021; maeda_statistical_2023). For example, (cite: meier_molecular_2001) find that star formation in IC 342 may be triggered by shocks at the intersection of x~1~ and x~2~ orbits, where molecular gas driven toward the nucleus by the bar potential collides with gas on the inner orbits. (cite: meier_nuclear_2008) observe a similar presence of dynamically induced star formation at the intersection of the nuclear bar orbits of the galaxy Maffei 2. Meanwhile, (cite: reynaud_kinematics_1998) find that star formation in NGC 1530 is strong at the center of the galaxy and at the ends of the bar but weak along the length of the bar, and they conclude that it is likely inhibited by shocks and shears in the bar lanes. Similarly, observations of four nearby barred galaxies by (cite: james_stellar_2016) show the existence of a central peak and outer ring of strong star formation, but also a region between the two where the star formation is strongly suppressed. And, with a sample of over 1000 galaxies, (cite: vera_effect_2016) show that strong-barred galaxies have lower star formation efficiencies than galaxies with weak or no bars.

In this paper, we have selected 20 clouds that are candidates for being in the Milky Way Galactic bar region outside the CMZ, including several located within B2 and G5. These clouds show bright NH~3~ (3,3) emission in the Mopra H~2~O Southern Galactic Plane Survey (cite: walsh_h2o_2011; purcell_h2o_2012; longmore_h2o_2017), have line widths greater than a few kilometers per second, and exhibit gas temperatures warmer than typical clouds in the Galactic disk ($\gtrsim 10 - 20$ K). We use the Total Power (TP) antennas of the Atacama Large Millimeter/submillimeter Array (ALMA) Atacama Compact Array (ACA) to observe several molecular lines from these 20 clouds in order to probe physical parameters including temperature, shocks, ionization, star formation, and turbulence, and to investigate where these clouds are located. In Section [2](#sec:obs) we describe the observations, ancillary data, and data reduction procedure. In Section [3](#sec:loc) we discuss the locations of the clouds. In Section [4](#sec:results) we calculate and compare the temperature, turbulence, star formation rates (SFRs), shock properties, and masses of the clouds. In Section [5](#sec:discussion) we discuss the relationships between the cloud properties, and we conclude in Section [6](#sec:conclusion).

![](hopsOverlayHQ.pdf)

# Observations and Data Reduction

## Sample Selection

We selected 20 clouds from HOPS that may be in the Milky Way Galactic bar region. The clouds were selected on the basis of bright, large-scale NH~3~ (3,3) emission, which is only observed toward a few objects, and which indicates that the gas temperatures may be warmer than typical clouds in the Galactic disk. In addition, several of the clouds have ammonia line widths much broader than typical clouds in the Galactic disk. The combination of these two properties suggests that the clouds may not be located in the Milky Way disk but rather be part of the central Galactic bar.

The spatial distribution of the 20 selected clouds is shown in Figure [1](#fig:hopsOverlay). We discuss the location of these clouds in the Galaxy in Section [3](#sec:loc).

## ALMA Observations and Data Reduction

The clouds were observed with the ALMA-ACA between 2021 May and 2023 May (project codes: 2019.2.00068.S, 2021.2.00001.S, 2022.1.00591.S; PI: Ott, J.) using both the 7 m array and the TP antennas. We analyze the TP data in this work. The spectral windows used cover lines of several important molecules: the carbon monoxide isotopologues ^12^CO, ^13^CO, and C^18^O; the shock tracers SiO (e.g., (cite: schilke_sio_1997)) and methanol (CH~3~OH; e.g., (cite: meier_spatially_2005)); formaldehyde (H~2~CO), from which the gas temperature can be determined (e.g., (cite: mangum_formaldehyde_1993; ginsburg_dense_2016)); the dense molecular gas tracer HC~3~N (e.g., (cite: meier_cyanoacetylene_2011; mills_dense_2018)); and the radio recombination line H30$\alpha$. The observing parameters of the spectral windows and the specific lines are shown in Table [\[table:obs_params\]](#table:obs_params).

| Spectral Line | Rest Frequency (GHz) | Bandwidth (GHz) | No. of Channels |
|:--:|:--:|:--:|:--:|
| SiO $J=5\to 4$ | 217.1050 | 0.25 | 512 |
| H~2~CO $J=3_{21} \to 2_{20}$ | 218.7601 | 0.25 | 512 |
| H~2~CO $J=3_{03} \to 2_{02}$ | 218.2222 | 0.25 | 512 |
| HC~3~N $J=24 \to 23$ | 218.3247 | 0.25 | 512 |
| CH~3~OH $J = 4_{22} \to 3_{12}$ | 218.4401 |  |  |
| C^18^O $J=2 \to 1$ | 219.5604 | 0.25 | 1024 |
| ^13^CO $J=2 \to 1$ | 220.3987 | 0.25 | 1024 |
| ^12^CO $J=2 \to 1$ | 230.5380 | 0.25 | 2048 |
| H30$\alpha$ | 231.9009 | 2 | 2048 |

| Cloud | $\ell$ \[$^\circ$\] | $b$ \[$^\circ$\] | NH~3~ (1,1) $\Delta$v \[km s$^{-1}$\] | v$_\mathrm{lsr}$ \[km s$^{-1}$\] | v$_\mathrm{int}$ \[km s$^{-1}$\] | $D$ \[kpc\] | $R_\text{Gal}$ \[kpc\] | $D_\text{ref}$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| G008.67 | 8.67 | -0.37 | $3.31 \pm 0.13$ | $35.10 \pm 0.19$ | $24\textup{--}52$ | $3.4 \pm 0.3$ | $4.8 \pm 1.0$ | **1** |
| G008.40 | 8.40 | -0.29 | $2.38 \pm 0.08$ | $36.79 \pm 0.07$ | $31\textup{--}42$ | $4.5 \pm 1.0$ | $3.8 \pm 2.1$ | **2** |
| G006.92 | 6.92 | -0.23 | $2.73 \pm 0.23$ | $19.21 \pm 0.26$ | $5\textup{--}35$ | $3.5 \pm 1.0$ | $4.7 \pm 3.3$ | **2** |
| ***G006.56*** | 6.56 | -0.30 | $24.34 \pm 1.98$ | $7.41 \pm 0.04$ | $-10\textup{--}45$ | $6.9 \pm 1.0$ | $1.6 \pm 0.6$ | **3** |
| ***G005.75*** | 5.75 | 0.23 | $27.43 \pm 1.93$ | $70.11 \pm 0.27$ | $31\textup{--}100$ | $7.0 \pm 1.0$ | $1.4 \pm 0.5$ | **3** |
| ***G005.49*** | 5.49 | -0.08 | $20.35 \pm 2.48$ | $53.57 \pm 0.16$ | $25\textup{--}95$ | $7.0 \pm 1.0$ | $1.3 \pm 0.5$ | **3** |
| ***G005.38*** | 5.38 | -0.12 | $27.36 \pm 2.06$ | $38.16 \pm 0.18$ | $0\textup{--}75$ | $7.1 \pm 1.0$ | $1.3 \pm 0.5$ | **3** |
| G003.43 | 3.43 | -0.35 | $3.54 \pm 0.22$ | $-25.36 \pm 0.26$ | $-50\textup{--}5$ | $2.5 \pm 1.0$ | $5.7 \pm 5.0$ | **3**, **4** |
| ***G003.09*** | 3.09 | 0.16 | $42.17 \pm 0.64$ | $151.06 \pm 0.41$ | $90\textup{--}200$ | $7.5 \pm 1.0$ | $0.8 \pm 0.3$ | **3** |
| ***G003.02*** | 3.02 | -0.07 | $38.43 \pm 0.62$ | $42.17 \pm 1.00$ | $-48\textup{--}145$ | $7.5 \pm 1.0$ | $0.8 \pm 0.3$ | **3** |
| ***G002.96*** | 2.96 | -0.19 | $34.09 \pm 0.63$ | $97.16 \pm 0.59$ | $30\textup{--}130$ | $7.5 \pm 1.0$ | $0.8 \pm 0.3$ | **3** |
| ***G002.51*** | 2.51 | -0.03 | $37.74 \pm 0.96$ | $8.21 \pm 0.53$ | $-35\textup{--}20$ | $7.6 \pm 1.0$ | $0.7 \pm 0.2$ | **3** |
| ***G001.93*** | 1.93 | 0.11 | $30.61 \pm 1.59$ | $23.64 \pm 0.63$ | $2\textup{--}76$ | $7.7 \pm 1.0$ | $0.5 \pm 0.2$ | **3** |
| G358.48 | 358.48 | -0.38 | $2.80 \pm 0.17$ | $-1.67 \pm 0.06$ | $-17\textup{--}30$ | $2.5 \pm 1.0$ | $5.7 \pm 5.0$ | **3** |
| G354.61 | 354.61 | 0.47 | $2.30 \pm 0.20$ | $-20.57 \pm 0.09$ | $-35\textup{--}-9$ | $12.3 \pm 2.2$ | $4.2 \pm 1.8$ | **5** |
| G353.41 | 353.41 | -0.36 | $3.73 \pm 0.15$ | $-15.44 \pm 0.20$ | $-25\textup{--}-4$ | $2.0 \pm 0.7$ | $6.2 \pm 5.0$ | **1** |
| G351.77 | 351.77 | -0.49 | $3.05 \pm 0.23$ | $-3.23 \pm 0.25$ | $-15\textup{--}20$ | $2.0 \pm 0.1$ | $6.2 \pm 5.0$ | **6** |
| G351.58 | 351.58 | -0.34 | $4.22 \pm 0.28$ | $-92.18 \pm 0.28$ | $-105\textup{--}-80$ | $5.2 \pm 1.0$ | $3.1 \pm 1.4$ | **7** |
| G350.18 | 350.18 | 0.02 | $24.32 \pm 1.37$ | $-66.50 \pm 0.13$ | $-90\textup{--}-49$ | $6.2 \pm 0.8$ | $2.3 \pm 0.7$ | **4**, **8** |
| G350.10 | 350.10 | 0.09 | $21.10 \pm 0.94$ | $-69.25 \pm 0.16$ | $-85\textup{--}-45$ | $6.2 \pm 0.8$ | $2.3 \pm 0.7$ | **8** |

| Cloud | SiO | H~2~CO $(3_{21}-2_{20})$ | H~2~CO $(3_{03}-2_{02})$ | HC~3~N | CH~3~OH | H30$\alpha$ | NH~3~ $(2,2)$ | NH~3~ $(6,6)$ |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| G008.67 |  |  |  |  |  |  |  | $\hdots$ |  |  |  |
| G008.40 |  |  |  | $\hdots$ |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G006.92 |  |  |  | $\hdots$ |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G006.56 |  |  |  |  |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G005.75 | $\hdots$ | $\hdots$ |  | $\hdots$ |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G005.49 | $\hdots$ | $\hdots$ |  | $\hdots$ | $\hdots$ | $\hdots$ | $\hdots$ | $\hdots$ |  |  |  |
| G005.38 |  |  |  | $\hdots$ |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G003.43 |  |  |  |  |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G003.09 |  |  |  |  |  | $\hdots$ |  |  |  |  |  |
| G003.02 |  |  |  |  |  | $\hdots$ |  |  |  |  |  |
| G002.96 |  |  |  | $\hdots$ |  | $\hdots$ |  |  |  |  |  |
| G002.51 |  |  |  | $\hdots$ |  | $\hdots$ |  |  |  |  |  |
| G001.93 |  |  |  | $\hdots$ |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G358.48 |  |  |  |  |  | $\hdots$ |  | $\hdots$ |  |  |  |
| G354.61 |  |  |  |  |  |  |  | $\hdots$ |  |  |  |
| G353.41 |  |  |  |  |  |  |  | $\hdots$ |  |  |  |
| G351.77 |  |  |  |  |  |  |  | $\hdots$ |  |  |  |
| G351.58 |  |  |  |  |  |  |  | $\hdots$ |  |  |  |
| G350.18 |  |  |  | $\hdots$ |  |  |  | $\hdots$ |  |  |  |
| G350.10 |  |  |  |  |  |  |  | $\hdots$ |  |  |  |

We used the default ALMA Pipeline Reduction, which utilized the Common Astronomy Software Application (CASA) versions 6.2.1.7-6.4.1.12 (cite: the_casa_team_casa_2022). We visually inspected and selected the velocity and channel ranges without any spectral features for the presence of continuum emission. If found, the continuum was subtracted.

The native full width at half-maximum (FWHM) beam sizes of the observations are between approximately 28$''$ and 30$''$. We smooth the cubes to all have the same beam size of 31$''$. For each cloud, we also regrid the cubes to match the ^13^CO $J=2\to 1$ pixel size of 2.935$''$ and velocity resolution of 0.332 km s$^{-1}$. In this channel width of 0.332 km s$^{-1}$, the 1$\sigma_\text{rms}$ root-mean-square noise (rms) over the line-free channels varies from about 0.22 to 0.28 Jy beam$^{-1}$. We also convert from intensity $I_\nu$ in units of Jy beam$^{-1}$ to a brightness temperature (kelvins), in which case the rms noise ranges from about 5.2 to 7.7 mK.

## ALMA Maps

To make integrated intensity (“moment 0”) maps, we set a cutoff at 4$\sigma_\text{rms}$, then integrate over the velocity range of the cloud in ^13^CO $J=2\to 1$, which is observed for all clouds and is less contaminated with foreground and background emission than the more common isotopologue ^12^CO $J = 2 \to 1$. The velocity range of each cloud is given in Table [\[table:cloudLocations\]](#table:cloudLocations). We also generate intensity-weighted velocity (“moment 1”), intensity-weighted velocity dispersion (“moment 2”), and peak intensity maps for each cube. For these images, we again use a 4$\sigma_\text{rms}$ pixel cutoff, as well as a 5$\sigma$ threshold on the moment 0 map, where $\sigma$ is estimated as $$\begin{equation}
\label{eq:noise}
\sigma \approx \sqrt{N} \sigma_\text{rms} \Delta v.
\end{equation}$$ Here, $N$ is the number of channels integrated over for the moment 0 map, and $\Delta v = 0.332$ km s$^{-1}$ is the channel velocity width. Although $N$ varies across a single map, since we also use a 4$\sigma_\text{rms}$ cutoff when creating integrated intensity maps, we set $N$ to be constant at the number of channels corresponding to the full integration velocity range, which is likely more than the actual number of channels integrated over for most pixels. This effectively corresponds to the error assuming no masking in the integrated intensity map, which represents a maximum possible $N$, and thus a constant “maximum" $\sigma$. We then calculate ratio maps between each of the lines and both ^12^CO $J=2\to 1$ and ^13^CO $J=2\to 1$ using the respective moment 0 maps. For each moment 0 ratio map, $R = \frac{M_0^i}{M_0^j}$, between lines $i$ and $j$, we calculate a corresponding error map, where the error $\delta R$ is $$\begin{equation}
\label{eq:ratioError}
\delta R = R\sqrt{\left(\frac{\sigma_i}{M_0^i} \right)^2 + \left( \frac{\sigma_j}{M_0^j} \right)^2},
\end{equation}$$ where $M_0 = \int I_v dv$ is the integrated intensity of a line, and $\sigma$ is the error of the moment 0 map (Eq. [\[eq:noise\]](#eq:noise)). Although this equation does not hold under all circumstances, we use it as an approximation of the error for the integrated intensity ratios. We note that although $\sigma$ is assumed to be constant across each moment 0 map, as discussed above, the ratio error maps are not constant since they are also functions of the individual moment 0 maps. The same holds for the temperature error maps described in Section [4.1](#subsec:gastemp).

We also create position-velocity (PV) diagrams for each cube using the packages `pvextractor`[^1] and `spectral-cube`[^2] (cite: ginsburg_radio-astro-toolsspectral-cube_2019). We select a path going through the main regions of each cloud, then calculate the PV diagram using the cloud velocity range, with an extra 20 km s$^{-1}$ on each side.

All clouds display clear emission for all three carbon monoxide isotopologues, although some other lines do not have a significant detection. The detected lines for each cloud are shown in Table [\[table:detections\]](#table:detections). We show the integrated intensity maps of all clouds for each line in Figure [2](#fig:integratedIntensities), and the PV diagrams in Figure [3](#fig:pvDiagrams). The full figure sets for these figures are available in the online journal.

![](h2co_303-202_II.pdf)

![](G008.67_pvDiagrams.pdf)

## Ancilllary Data

### HOPS

We use HOPS for measurements of metastable ammonia inversion transitions with $(J, K) = (1,1),\ (2,2),\ (3,3),$ and $(6,6)$, for which the rotational temperature is similar to the gas kinetic temperature (cite: huettemeister_multilevel_1995; ott_temperature_2005). HOPS used the 22 m Mopra radio telescope, which has a main-beam FWHM of 2’ at 12 mm (cite: urquhart_characterisation_2010), and covered a velocity range of -200 to 200 km s$^{-1}$, which may exclude parts of the bar dust lanes that are at even higher velocities. Further observation details about the HOPS ammonia catalog can be found in (cite: purcell_h2o_2012).

The clouds were initially selected to be bright in NH~3~ $(3,3)$ emission, and all clouds are observed in the NH~3~ $(1,1)$ line, although not all clouds have significant NH~3~ $(2,2)$ or $(6,6)$ emission. The ammonia line detections are also shown in Table [\[table:detections\]](#table:detections). For each cloud, we select a region that covers the full extent of the cloud, which in general is larger than the ALMA field of view (FOV) of the cloud. We then make a moment 0 map of each region for all four ammonia lines using the same velocity range as used for the ALMA moment maps.

### Spitzer

We additionally use data from two Spitzer Galactic plane surveys, the Galactic Legacy Infrared Midplane Survey Extraordinaire (GLIMPSE; (cite: churchwell_spitzerglimpse_2009), (cite: glimpse_team_galactic_2020)) and the Multiband Imaging Photometer Galactic Plane Survey (MIPSGAL; (cite: rieke_multiband_2004), (cite: carey_mipsgal_2009), (cite: mipsgal_team_24_2020)). We use the cutout service of the Infrared Science Archive (IRSA) to take 10$'$ wide images containing the central location of each cloud in the 4.5 and 8 $\mu$m bands of the Infrared Array Camera (cite: fazio_infrared_2004) from GLIMPSE. We also take 30$'$ wide images of the same locations in the 24 $\mu$m band of MIPS, then regrid to match the pixel spacing of the GLIMPSE data using the `reproject`[^3] package.

# Cloud Locations

![](lvDiagram.pdf)

As mentioned in Section [2.1](#subsec:sampselec), the clouds in the sample are candidates for being in the Galactic bar region due to their bright and broad NH~3~ (3,3) emission. We also note that we find fewer clouds with similar properties at $\lvert \ell \rvert > 10^\circ$ in the HOPS data. Although the locations are uncertain, we take the clouds with a NH~3~ (1,1) line width greater than 10 km s$^{-1}$ to lie along the Galactic bar. We note that, for all 11 clouds in this selection, the line widths are in fact all above 20 km s$^{-1}$, and for all nine clouds not in this selection, the line widths are all below 5 km s$^{-1}$, indicating two distinct populations rather than a continuum of line widths. The broad-lined clouds are likely to be in the Galactic bar; however, we note below that two of the clouds in this selection may have Galactic longitudes beyond the extent of the bar. This is also further discussed in Section [5.4](#subsec:loc2). We thus consider a total of nine clouds to be in the Galactic bar region, and we assume that they lie along the Galactic bar’s major axis. We use a Galactic Center distance of $8178 \pm 26$ pc (cite: abuter_geometric_2019) and an angle between the Galactic bar and the line of sight of $30^\circ \pm 2^\circ$ (cite: wegg_structure_2015) to calculate the distance and Galactocentric radius of each cloud. We also include a 1 kpc uncertainty along the line of sight to account for finite bar thickness. We adopt previous distance measurements using Galactic kinematics or associations with nearby cloud complexes for the clouds not in the bar, noting that these distances may be highly uncertain.

The longitude-velocity ($\ell$-v) diagram in Figure [4](#fig:lvdiagram) can also provide information about the location of the clouds. We see that many of the clouds are consistent with being outside the bar region in the Galactic disk, which is the generally flat feature at all longitudes between velocities of about -50 and 50 km s$^{-1}$, and the dust lane features are at higher velocities than all of the clouds in the sample. This is expected given that the HOPS data extends only to $\pm 200$ km s$^{-1}$, which cuts out much of the dust lane emission. However, we note that processes such as cloud-cloud collisions in the Galactic bar region can create features in the $\ell$-v diagram that extend over a wide range of velocities (cite: sormani_geometry_2019). For example, (cite: gramze_evidence_2023) find that the G5 region around $\ell = 5.4^\circ$ is likely undergoing a cloud-cloud collision and covers a velocity range from approximately 0 to 200 km s$^{-1}$. We therefore continue to consider the aforementioned nine broad-lined clouds to be in the Galactic bar. We discuss these bar clouds in more detail in Appendix [7](#appendix:barClouds), and we discuss the clouds not in the bar below.

## Clouds Not in the Galactic Bar

*G008.67*, also known as IRAS 18032-2137, is included in the ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS) survey (cite: liu_atoms_2020), which uses kinematic distances calculated from the APEX Telescope Large Area Survey of the Galaxy (ATLASGAL; (cite: urquhart_atlasgal_2018)). G008.67 is reported to have a distance of 5.2 kpc in the ATOMS survey. It is also included in the ALMA-IMF Large Program (cite: motte_alma-imf_2022), which also uses ATLASGAL kinematic distances but includes revisions made possible by other surveys such as the Bar and Spiral Structure Legacy Survey (cite: reid_trigonometric_2014). We adopt the ALMA-IMF kinematic distance of 3.4 $\pm$ 0.3 kpc.

*G003.43*. (cite: longmore_h2o_2017) note that the narrow velocity dispersion of G003.43 is consistent with being outside the Galactic center. Although they adopt a kinematic distance of 21.1 kpc, they find that the probability of the cloud being at the far kinematic distance is low. They conclude that it likely lies on the nearside of the Galactic bar but are unable to calculate a kinematic distance given its proximity to the Galactic Center. The cloud central velocity indicates that it is likely local to the Sun, on the order of 1 kpc, so we adopt a distance of 2.5 kpc but note this is highly uncertain.

*G358.48* does not have a previously reported distance. We assume that its near kinematic distance is more likely than its far kinematic distance, since HOPS has a 3.2 kpc sensitivity limit for typical 400 M$_\odot$ clouds with the NH~3~ (1,1) transition (cite: purcell_h2o_2012), and its central velocity also indicates it as being local to the Sun, so we adopt the same distance of 2.5 kpc as for G003.43.

*G354.61*. Although G354.61 appears to be associated with the clump B1, its central velocity does not match, as can be seen in Figure [4](#fig:lvdiagram). (cite: jones_h_2013) find its kinematic distance to be 12.3 $\pm$ 2.2 kpc.

*G353.41*, also known as IRAS 17271-3439, is reported to have a kinematic distance of 3.1 kpc in the ATOMS survey, but we instead adopt the revised kinematic distance of 2.0 $\pm$ 0.7 kpc from ALMA-IMF.

*G351.77*, also known as IRAS 17233-3606, is reported to have a distance of 1.34 kpc in the ATOMS survey. This is consistent with the ALMA-IMF distance of 2.0 $\pm$ 0.7 kpc. (cite: reyes-reyes_benchmarking_2024) find a consistent distance of 2.0 $\pm$ 0.1 kpc using astrometric data from Gaia Data Release 3 (cite: gaia_collaboration_gaia_2016; gaia_collaboration_gaia_2023) for sources associated with the cloud, which we adopt.

*G351.58*, also known as IRAS 17220-3609, is reported to have a distance of 8.0 kpc in the ATOMS survey, although (cite: green_distances_2011) place it at a distance of 5.2 kpc using kinematic estimates from maser emission. We adopt the latter since it agrees with the kinematic assessment of the cloud as belonging to the near 3 kpc arm, which is evident in Figure [4](#fig:lvdiagram).

*G350.18 and G350.10*. Although the two clouds at the most negative Galactic longitude, G350.18 and G350.10, have line widths above our cutoff of 10 km s$^{-1}$, we find that their Galactic longitudes are likely beyond the extent of the Galactic bar. If they do lie along the major axis of the bar, the bar would have to extend to over 4 kpc in the negative Galactic longitude (see Figure [5](#fig:geometry)). Indeed, it has been suggested that the bar may extend out to 5 kpc, or possibly even longer (cite: wegg_structure_2015; sormani_stellar_2022), so these clouds may lie near or around the tip of the bar, but we cannot conclude with certainty that these clouds belong to the Galactic bar region. We discuss the locations of these clouds further in Section [5.4](#subsec:loc2). We refer to previous kinematic measurements of their distances, of which there are several.

*G350.10*, also known as IRAS 17160-3707, is reported to have a distance of 10.53 kpc in the ATOMS survey, although (cite: nandakumar_star-forming_2016) adopt a distance of 6.2 kpc using the kinematics determined by (cite: quireza_radio_2006). We adopt a value of 6.2 $\pm$ 0.8 kpc, as it matches other kinematic distances to this cloud, which range from 5.7 to 7.3 kpc (cite: caswell_southern_1987; peeters_iso_2002; faundez_simba_2004). Although the cores of G350.10 and G350.18 are separate as seen in the Spitzer data (see Section [4.3](#subsec:sf)), the two appear to be linked in the ammonia and CO maps. (cite: longmore_h2o_2017) also consider the two clouds to be two components of the same young massive cluster progenitor gas cloud candidate. We therefore adopt the same distance to G350.18 as that of G350.10.

For these clouds, we also calculate a Galactocentric radius using their distance estimates and Galactic longitudes and latitudes. The locations of all clouds are summarized in Table [\[table:cloudLocations\]](#table:cloudLocations), as well as the references for the distance estimates. Our reclassification of G350.18 and G350.10 leaves nine clouds as most likely to lie in the Galactic bar region. We show a top-down projection of the distribution in Figure [5](#fig:geometry).

![](geometry.pdf)

![](NH3_temperatures.pdf)

# Results

## Gas Temperature

We calculate gas temperatures for all of the clouds using emission from ammonia and formaldehyde.

### Ammonia Temperature

We first calculate the rotational temperature using ammonia lines for each cloud following the same procedure outlined in (cite: ott_temperature_2005). We find that the NH~3~ $(1, 1)$ hyperfine structure lines are generally narrow, so we assume that the ammonia emission is optically thin, in which case the column density of an ammonia inversion doublet can be calculated as $$\begin{equation}
\label{eq:NH3col}
N(J, K) = \frac{7.77 \times 10^{13}}{\nu} \frac{J(J+1)}{K^2} \int T_\text{B} dv
\end{equation}$$ (cite: henkel_dense_2000), where the column density $N$, rest frequency $\nu$, and integrated main-beam brightness temperature have units of per square centimeter, GHz, and K km s$^{-1}$, respectively. We have only metastable ($J = K$) inversions, and the rotational temperature between two such states can be found from the equation $$\begin{equation}
\frac{N(J', J')}{N(J, J)} = \frac{g_\text{op}(J')}{g_\text{op}(J)} \frac{2J'+1}{2J+1} \text{exp}\left(\frac{-\Delta E}{T_{JJ'}}\right),
\end{equation}$$ where $\Delta E$ is the energy level difference between the NH~3~ $(J', J')$ and NH~3~ $(J, J)$ transitions in K, and $g_\text{op} = 1$ for para-ammonia (i.e., NH~3~ $(1, 1)$ and $(2,2)$) and $g_\text{op} = 2$ for ortho-ammonia (i.e., NH~3~ $(3, 3)$ and $(6,6)$). We note that the abundance ratio of para- and ortho-ammonia also introduces some additional uncertainty that propagates into the column density and ammonia temperatures calculations.

Solving for the rotational temperature gives $$\begin{equation}
\label{eq:NH3temp}
T_{JJ'} = \frac{-\Delta E}{\text{ln}\left(\frac{N(J', J')}{g_\text{op}(J')(2J' + 1)}\right) - \text{ln}\left(\frac{N(J, J)}{g_\text{op}(J)(2J + 1)}\right)}.
\end{equation}$$ For each cloud, we calculate a temperature map of $T_{12}$, $T_{13}$, and $T_{36}$, or the largest possible subset of the three given that some clouds do not have significant NH~3~ $(2,2)$ or $(6,6)$ emission, by applying Eqs. [\[eq:NH3col\]](#eq:NH3col) - [\[eq:NH3temp\]](#eq:NH3temp) to the pairs of ammonia moment 0 maps, as well as a 5$\sigma$ cutoff (Eq. [\[eq:noise\]](#eq:noise)) on both moment 0 maps. We also calculate estimated ammonia temperature error maps using the equation $$\begin{equation}
\label{eq:NH3tempErr}
\delta T_{JJ'} = \frac{T^2}{\Delta E}\sqrt{\left(\frac{\delta N(J', J')}{N(J', J')}\right)^2 + \left(\frac{\delta N(J, J)}{N(J, J)}\right)^2},
\end{equation}$$ where $$\delta N(J, K) = \frac{7.77 \times 10^{13}}{\nu} \frac{J(J+1)}{K^2} \sigma,$$ where $\sigma$ is the error of the integrated intensity map (Eq. [\[eq:noise\]](#eq:noise)). This equation assumes $\delta N \ll N$, or equivalently $\sigma \ll \int T_B dv$. The ammonia $(3,3) - (1,1)$ ($T_{13}$) temperature maps for all clouds are shown in Figure [6](#fig:NH3temp). The corresponding error maps are shown in Figure [20](#fig:NH3tempError) in Appendix [8](#appendix:tempErr).

Although it does not factor into our analysis below, we note that the only four clouds with detections of NH~3~ $(6,6)$ are G003.09, G003.02, G002.96, and G002.51, which are the clouds associated with B2, highlighting the extreme nature of this large cloud complex that is the closest region of bright NH~3~ $(3,3)$ emission to the CMZ (Figure [1](#fig:hopsOverlay)).

To get a single temperature value for each pair of ammonia lines, we take the temperature and error at the brightest pixel in the NH~3~ $(3,3)$ moment 0 map. We show rotation diagrams (or Boltzmann diagrams) of the ammonia lines and the resultant temperature values in Figure [7](#fig:NH3BD).

![](NH3_BDgrid.pdf)

### Formaldehyde Temperature

![](H2CO_temperatures.pdf)

![](tCorrelations.pdf)

Next, we calculate the gas temperature based on the line ratio of H~2~CO $(3_{21}-2_{20})$ to H~2~CO $(3_{03}-2_{02})$. We take the ratio between the integrated intensity maps of the two lines, described in Section [2.3](#subsec:maps), enforcing a 3$\sigma$ cutoff (Eq. [\[eq:noise\]](#eq:noise)) on both moment 0 maps. We then use the formula $$\begin{equation}
\label{eq:formaldehydeTemp}
T_G [K] = 590 R_{\rm{H}_2 \rm{CO}}^2 + 2.88 R_{\rm{H}_2 \rm{CO}} + 23.4,
\end{equation}$$ which is a polynomial fit to the gas temperature and formaldehyde line ratio $R_{\rm{H}_2 \rm{CO}} = \frac{\int I_v (3_{21} - 2_{20}) dv}{\int I_v (3_{03} \to 2_{02}) dv}$ (cite: ginsburg_dense_2016) derived from the radiative transfer code RADEX (cite: van_der_tak_computer_2007). This fit uses an assumed gas density of $n(\text{H}_2) = 10^4 \text{ cm}^{-3}$. Unlike ammonia, formaldehyde is an asymmetric top molecule, so the excitation of different transitions, and in turn the line ratio, depend on the H~2~ density, although the gas temperature has only a weak density dependence for most of the line ratios we observe ($R_{\rm{H}_2 \rm{CO}} \lesssim 0.3$; (cite: ginsburg_dense_2016)). We discuss this further in Section [5.1](#subsec:temperature). We also calculate temperature error maps, $$\begin{equation}
\label{eq:formaldehydeTempErr}
\delta T_G [K] = \frac{dT_G}{dR} \delta R = 1080R \delta R + 2.88\delta R,
\end{equation}$$ where $\delta R$ is the error on the formaldehyde ratio (Eq. [\[eq:ratioError\]](#eq:ratioError)). These errors are likely underestimates for regions where the gas temperature is greater than about 80 K. The resultant formaldehyde temperature maps are shown in Figure [8](#fig:H2COtemp). We also show the error maps in Figure [21](#fig:H2COtempError) in Appendix [8](#appendix:tempErr).

The formaldehyde and ammonia temperature depend differently on physical conditions, so a comparison between the two may reveal some insight into the cloud structure. However, their observations are at different resolutions, so to compensate, we return to the formaldehyde data cubes and regrid them to the same spatial and velocity resolution as the HOPS ammonia cubes. We create a regridded temperature map using the same procedure as above, then take the temperature (Eq. [\[eq:formaldehydeTemp\]](#eq:formaldehydeTemp)) and error (Eq. [\[eq:formaldehydeTempErr\]](#eq:formaldehydeTempErr)) at the pixel with peak NH~3~ $(3,3)$ integrated intensity.

We find that the peak NH~3~ $(3,3)$ pixel often lies far from the peak emission of the formaldehyde lines, and in one case lies outside the ALMA FOV of the corresponding cloud. The average angular offset between the two peaks is 1.26’, and the average physical offset is 2.23 pc, although the uncertainty on the latter may be large due to the individual distance uncertainties. We thus also calculate a potentially more representative formaldehyde temperature value by taking the mean of the temperature map at its original resolution within a 1’ box centered on the pixel with maximum H~2~CO $J=3_{03} \to 2_{02}$ integrated intensity (light blue boxes in Figure [8](#fig:H2COtemp)). We take the error on this temperature to be the mean of the temperature error map within the same box.

We use this same box to calculate representative values for other properties of the ALMA data, such as the line widths (Section [4.2](#subsec:turb)) and ratio maps.

### Ammonia versus Formaldehyde Temperature

A direct, quantitative comparison between the ammonia and formaldehyde temperature measurements is difficult because of the factor of four difference in beam size between the HOPS and ALMA data and the spatial distance between the peak NH~3~ (3,3) and H~2~CO $J = 3_{03} \to 2_{02}$ emission. We still plot the correlations between them in Figure [9](#fig:tCorr), but we find no significant correlation between the ammonia and formaldehyde temperature. However, there is a clear correlation between the ammonia temperatures calculated using the NH~3~ (1,1) and (2,2) emission versus that using the NH~3~ (1,1) and (3,3) emission, as well as between the formaldehyde temperature taken at the pixel with peak NH~3~ (3,3) emission versus that averaged over a 1’ box centered at the peak H~2~CO $J=3_{03} \to 2_{02}$ emission, both of which are expected.

The lack of any correlation between the ammonia and formaldehyde temperatures indicates they may be tracing gas components at different densities and optical depths. As discussed in more detail in Section [5.1](#subsec:temperature), the properties derived from these two molecules, and indeed from many of the molecular lines we observe, are inconsistent with a single gas component.

## Turbulence

We calculate a line width for each ALMA line by fitting a Gaussian to the mean spectrum of the 1’ box centered on the peak pixel in the H~2~CO $J=3_{03} \to 2_{02}$ integrated intensity map. One cloud exhibits two velocity components in its spectrum, so we fit a double Gaussian and take the wider of the two. Figure [10](#fig:H2COtempLW) shows that there is no correlation between the formaldehyde temperatures and line widths of the clouds, which is expected if the line broadening is due to processes such as turbulence rather than thermal broadening.

![](H2CO_tempLW.pdf)

We can calculate the expected degree of thermal broadening for each cloud. Assuming local thermal equilibrium (LTE), the thermal one-dimensional velocities of molecules should follow a Maxwell-Boltzmann distribution. The thermal FWHM is $$\begin{equation}
\label{eq:vThermal}
\Delta v_\text{th} = \left( 8\ln2 \frac{k_B T_k}{\mu m_H} \right)^{1/2},
\end{equation}$$ where $k_B$ is the Boltzmann constant, $T_k$ is the kinetic temperature of the cloud, $\mu = 2.34$ is the mean molecular weight of a molecular cloud (cite: syed_atomic_2020), and $m_H$ is the mass of a hydrogen atom. Taking the calculated formaldehyde temperatures of each cloud to be representative of the kinetic temperature, we can calculate a thermal line width, then calculate a nonthermal line width corresponding to large- and small-scale velocity variations. Both turbulent and bulk ordered motion contribute to the nonthermal line width, so to isolate the turbulence component, we take $$\begin{equation}
\label{eq:vnon-thermal}
\Delta v_\text{turb} = \sqrt{\Delta v^2 - \Delta v_\text{th}^2 - \Delta v_\text{bulk}^2},
\end{equation}$$ where $\Delta v$ is the observed total line width. We can estimate the contribution from ordered motion through the velocity gradients of the clouds, which can be measured by fitting a linear velocity gradient to the intensity-weighted velocity maps (e.g., (cite: federrath_link_2016; balser_discovery_2021; wang_role_2024)). An example of this calculation is shown in Appendix [9](#appendix:vg). Although the velocity gradient may not accurately represent the bulk motion, particularly for clouds with multiple complex velocity components (cite: henshaw_brick_2019), for the clouds in our sample, which are not very kinematically complex, it likely suffices as an approximate measure of the ordered motion contribution to the line width. As can be seen in Figure [10](#fig:H2COtempLW), the turbulent line widths are significantly greater than the thermal line widths, which range from $\sim 0.4$ to 1.6 km s$^{-1}$. The line width contribution from bulk motion is also small, on the same order as the thermal contribution, indicating that the gas is dominated by turbulence. The one exception is G005.49, which has an estimated bulk motion line width contribution nearly equal to the total line width ($\sim 10 \text{ km s}^{-1}$); however, this is a cloud for which there is no detection of H~2~CO $J=3_{21} \to 2_{20},$ and thus no formaldehyde temperature. For this cloud, we can expect that its line width is dominated by some ordered motion.

The turbulent FWHM line widths, which largely dominate the total FWHM line widths, of formaldehyde for the clouds ranges between $\sim 4$ and 25 km s$^{-1}$. The molecular clouds in the Galactic disk studied by (cite: larson_turbulence_1981) have a three-dimensional rms velocity dispersion between $\sim 0.4$ and 9 km s$^{-1}$. The one-dimensional FWHM and three-dimensional rms velocity dispersions are related by $$\begin{equation}
\label{eq:rmsVSfwhm}
\Delta v = \sqrt{\left(8 \ln 2\right)/3} \ v_\text{rms}.
\end{equation}$$ The rms velocity dispersion range of the clouds is $\sim 3-20$ km s$^{-1}$, which lies between the values expected of clouds in the Galactic disk and clouds in the CMZ, the latter of which have FWHM line widths on the order of $10-50$ km s$^{-1}$ (e.g., (cite: tsuboi_central_2015)). This suggests that some of the clouds in the sample may indeed be exposed to some of the extreme conditions of the CMZ.

We can approximate the sound speed of the cloud by assuming an isothermal gas with equation of state $P = \rho k_B T/(\mu \text{m}_\text{H})$, in which case the sound speed is $$\begin{equation}
\label{eq:soundSpeed}
\text{c}_s = \sqrt{k_B T_k/(\mu \text{m}_\text{H})}.
\end{equation}$$ The three-dimensional Mach number, assuming isotropic turbulence, is then $\mathcal{M} = v_\text{rms}/\text{c}_s$, where $v_\text{rms}$ is the turbulent three-dimensional rms velocity dispersion of Eq. [\[eq:rmsVSfwhm\]](#eq:rmsVSfwhm). The calculated Mach numbers range from 7 to 45. These values also lie between those typical of molecular clouds in the Galactic disk ($\lesssim 10$; e.g., (cite: tang_kinetic_2018), (cite: syed_atomic_2020)) and those observed in the CMZ ($\gtrsim 25$; e.g., (cite: kauffmann_galactic_2017), (cite: henshaw_molecular_2016)).

We take the errors in the total line widths to be the errors on the Gaussian fits, then propagate accordingly to get errors on the Mach numbers.

## Star Formation

| Cloud | $\Delta v$ \[km s$^{-1}$\] | $T_e$ \[K\] | $D_{\text{H30}\alpha}$ \[pc\] | $n_e$ \[cm^-3^\] | $\int F_{v} dv$ \[Jy km s$^{-1}$\] | $\text{log}_{10} Q$ \[s$^{-1}$\] |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| G008.67 | $27.21 \pm 1.04$ | $7170.24 \pm 512.06$ | $0.73 \pm 0.09$ | $860.28 \pm 100.02$ | $28.94 \pm 0.07$ | $47.76 \pm 0.09$ |
| G354.61 | $38.99 \pm 2.09$ | $6993.59 \pm 665.36$ | $4.34 \pm 0.79$ | $145.23 \pm 26.39$ | $5.50 \pm 0.05$ | $48.12 \pm 0.17$ |
| G353.41 | $26.62 \pm 0.22$ | $7558.10 \pm 1588.27$ | $0.79 \pm 0.28$ | $798.87 \pm 279.99$ | $147.07 \pm 0.08$ | $48.00 \pm 0.34$ |
| G351.77 | $10.18 \pm 0.81$ | $7560.89 \pm 545.06$ | $0.29 \pm 0.04$ | $2174.67 \pm 308.14$ | $13.31 \pm 0.17$ | $46.98 \pm 0.24$ |
| G351.58 | $25.41 \pm 1.07$ | $6677.77 \pm 566.97$ | $1.25 \pm 0.24$ | $504.76 \pm 97.14$ | $61.63 \pm 0.06$ | $48.42 \pm 0.18$ |
| G350.18 | $26.62 \pm 1.78$ | $6446.82 \pm 422.08$ | $1.98 \pm 0.29$ | $318.40 \pm 45.86$ | $1.95 \pm 0.05$ | $47.06 \pm 0.12$ |
| G350.10 | $28.15 \pm 0.24$ | $6448.32 \pm 422.37$ | $1.62 \pm 0.21$ | $390.11 \pm 51.41$ | $135.03 \pm 0.10$ | $48.90 \pm 0.12$ |

![](h30moment0.pdf)

![](spitzer.pdf)

![](spitzerH2CO.pdf)

We can calculate the ionizing photon production rate, $Q$, from measurements of H30$\alpha$, via $$\begin{equation}
\label{eq:H30a}
\begin{split}
\frac{Q(\text{H}n\alpha)}{\text{s}^{-1}} = & \ 3.99 \times 10^{24} \left(\frac{\alpha_B}{\text{cm}^3 \text{ s}^{-1}}\right)\left(\frac{\epsilon_\nu}{\text{erg s}^{-1}\text{ cm}^{-3}}\right)^{-1} \\ 
& \ \times \left(\frac{\nu}{\text{GHz}}\right)\left(\frac{D}{\text{kpc}}\right)^2 \left(\frac{\int F_v dv}{\text{Jy km\ s}^{-1}}\right)
\end{split}
\end{equation}$$ (cite: scoville_submillimeter_2013; bendo_tests_2017; kim_new_2018), where $\alpha_B$ is the case B effective recombination coefficient, and $\epsilon_\nu$ is the emissivity, both of which are functions of electron density and temperature.

To estimate the electron temperature, we use the Galactic disk electron temperature gradient from (cite: quireza_electron_2006), $$\begin{equation}
\label{eq:eTempGradient}
T_e [\text{K}] = (5780 \pm 350) + (287 \pm 46) R_\text{Gal} [\text{kpc}],
\end{equation}$$ which is an empirical fit to HII regions with electron temperatures derived from radio recombination line and continuum measurements, and Galactocentric distances calculated via radial velocity measurements. We can also confirm that these fall under the upper limit on the electron temperature given by the line width of our H30$\alpha$ observations. The thermal contribution to the line width is Gaussian and has a FWHM of $$\begin{equation}
\label{eq:thermalFWHM}
\Delta v_\text{th} = \left(8 \text{ln} 2 \frac{k_\text{B} T_e}{m_\text{H}} \right)^{1/2}
\end{equation}$$ (cite: rivera-soto_recombination_2020), which is the same form as Eq. [\[eq:vThermal\]](#eq:vThermal) but replacing the kinetic temperature with electron temperature. Pressure broadening is proportional to $\nu^{-4}$, so it is negligible at the H30$\alpha$ frequency (cite: keto_early_2008). Thus, the total H30$\alpha$ line should be Gaussian and have a FWHM of $$\begin{equation}
\label{eq:totalFWHM}
\Delta v = \sqrt{\Delta v_\text{th}^2 + \Delta v_\text{dy}^2},
\end{equation}$$ where $\Delta v_\text{dy}$ is the dynamical contribution from unresolved bulk motions. We find that electron temperature calculated from Eq. [\[eq:eTempGradient\]](#eq:eTempGradient) is indeed below the upper limit set by Eq. [\[eq:thermalFWHM\]](#eq:thermalFWHM) (using the Gaussian line width calculated in Section [4.2](#subsec:turb)) for all the clouds with H30$\alpha$ detections.

Whereas the value of the electron temperature can affect the ionizing photon production rate $Q$ by a factor of up to $\sim$2.5 over a temperature range from 3000 to 15,000 K, the electron density has a relatively small effect on $Q$, with less than a 15% variation in both the recombination coefficient and emissivity over a density range from $10^2$ and $10^5$ cm$^{-3}$ (cite: bendo_tests_2017). We estimate the electron density using the fits of $n_e$ against diameter of Galactic HII regions by (cite: hunt_size-density_2009). To calculate sizes for the clouds, we collapse the H30$\alpha$ PV diagram along the velocity axis to create a one-dimensional cloud profile, then fit a Gaussian. We take the angular diameter of the cloud to be 4 times the standard deviation of the fitted Gaussian, then calculate a physical size using the distance to the cloud. Although this is an inaccurate estimate for elongated clouds, we find that the integrated intensity maps of H30$\alpha$ are roughly circular, shown in Figure [11](#fig:h30moment0) (which also includes the overlain PV diagram path). The resulting cloud sizes all lie within the range of 0.3 and 5 pc, which is covered by the (cite: kim_radio_2001) sample of compact Galactic HII regions; (cite: hunt_size-density_2009) finds a best-fit regression of $$\begin{equation}
\label{eq:neDiameter}
\text{log}\ n_e \ [\text{cm}^{-3}] = 2.8 - \text{log}\ D \ [\text{pc}] \,.
\end{equation}$$

Using these calculated electron densities and temperatures, we interpolate the tables of $\alpha_B$ and $\epsilon_\nu$ values published by (cite: storey_recombination_1995). We calculate errors on these values using a simple Monte Carlo simulation, assuming a normal distribution for $T_e$ and $n_e$. To calculate the integrated flux density of H30$\alpha$ from our moment 0 maps, we use a 1’ box centered on the pixel with peak H30$\alpha$ integrated intensity, then take $$\begin{equation}
\label{eq:fluxDensity}
\int F_v\ dv\ [\text{Jy km\ s}^{-1}] = \frac{2k_B \nu^2}{c^2} \iint T_B\ dv\ d\Omega,
\end{equation}$$ where $\int T_B\ dv$ is the moment 0 map.

The quantities derived from the H30$\alpha$ line, including the ionizing photon production rate $Q$, are shown for all the clouds with H30$\alpha$ detection in Table [\[table:SFparameters\]](#table:SFparameters). The resultant $Q$ values are mostly consistent with that of a main sequence O star, which has a $\text{log}_{10} Q$ value between 47.88 for an O9.5 star and 49.64 for a an O3 star (cite: martins_new_2005).

Using the derived $Q$, $n_e$, and $\alpha_B$ values, we can estimate the radius of a Strömgren sphere, which represents a region ionized by a single O-type star, using the equation $$\begin{equation}
r_S = \left(\frac{3Q}{4\pi \alpha_B n_e^2}\right)^{1/3}.
\end{equation}$$ We find that the radii derived from this calculation agree with the measured radii of the H30$\alpha$ emission within a factor of 4, with an average $r_{\text{H30}\alpha}/r_S$ ratio of 2.2. Although $n_e$, and thus $\alpha_B$ and $Q$, is calculated using the diameter of the cloud in H30$\alpha$, the relationship between them is non-linear, and so, this provides a check of internal consistency within the calculations.

We also calculate upper limits on $Q$ values for the clouds without significant H30$\alpha$ detections. We take the upper limit on the integrated flux density to be $$\begin{equation}
\label{eq:fluxDensityErr}
\int F_v\ dv\ [\text{Jy km\ s}^{-1}] \leq \frac{2k_B \nu^2}{c^2} \sigma \sqrt{N},
\end{equation}$$ where $\sigma$ is the error on the H30$\alpha$ moment 0 map (Eq. [\[eq:noise\]](#eq:noise)), and $N$ is the number of pixels in a 1’ box on the map. We use the electron temperature gradient (Eq. [\[eq:eTempGradient\]](#eq:eTempGradient)) to estimate electron temperatures for each cloud, and choose the mean of the electron densities of clouds with H30$\alpha$ detections to be an estimate of the electron density of clouds with no detection. We interpolate the electron density and temperature to get $\alpha_B$ and $\epsilon_\nu$ values, then calculate a photoionizing photon production rate with Eq. [\[eq:H30a\]](#eq:H30a); we take a 2$\sigma$ upper limit of twice this $Q$ value. The same method is also applied to calculate errors on the $Q$ values for clouds with H30$\alpha$ emission.

We plot Spitzer images for clouds with detections in Figure [12](#fig:spitzer), with H30$\alpha$ contours, and in Figure [13](#fig:spitzerH2CO), with H~2~CO $J=3_{03} \to 2_{02}$ contours. There is generally a correlation between the presence and location of H30$\alpha$ and both 8 and 24 $\mu$m emission, although G003.43 displays 24 $\mu$m emission consistent with the location of formaldehyde emission but does not have an H30$\alpha$ detection. We can also estimate the SFR in the clouds from 24 $\mu$m emission using the relationship from (cite: calzetti_calibration_2007), $$\begin{equation}
\label{eq:24muSFR}
\text{SFR} \ [\text{M}_\odot \text{ yr}^{-1}] = 1.27 \times 10^{-38} (L_{24 \mu\text{m}} \ [\text{ergs s}^{-1}])^{0.8850},
\end{equation}$$ where $L_{24 \mu \text{m}} = \nu L(\nu)$. This relation is derived from extragalactic star-forming regions, so it may not be fully applicable to the clouds in our sample, but it can be used as an approximation. For comparison, we also calculate a star formation rate from the ionizing photon production rate using a conversion from $Q$ to SFR of $7.29 \times 10^{-54} \text{ M}_\odot \text{yr}^{-1}/\text{s}^{-1}$ (cite: murphy_calibrating_2011), which is calculated using `STARBURST99` (cite: leitherer_starburst99_1999) and also applies primarily to the galactic scale. It also assumes solar metallicity and a constant SFR over about 100 Myr.

The 24 $\mu$m MIPSGAL processing pipeline masks artifacts in the data, which are particularly prevalent around bright sources (cite: mizuno_processing_2008). Most of the clouds with H30$\alpha$ emission, which are also bright in the mid-IR, are thus masked, as can be seen in Figures [12](#fig:spitzer) and [13](#fig:spitzerH2CO). To mitigate this effect, we interpolate the missing values, although this is imperfect as the masked pixels are generally around the brightest locations. We thus treat the resultant SFR values as lower limits.

We integrate the 24 $\mu$m emission, which is given in units of MJy sr^-1^, over a 2’ box centered on the location with peak H30$\alpha$ integrated intensity. We choose a larger box size than for calculating the H30$\alpha$ flux density because we expect the emission to be more extended, as the 24 $\mu$m emission comes from dust around the star-forming region whereas H30$\alpha$ emission comes from, or closer to, the ionized region. We convert these fluxes into luminosities using their distances, then calculate the SFR with Eq. [\[eq:24muSFR\]](#eq:24muSFR).

To calculate errors on the SFR of these clouds, as well as upper limits on the clouds with no detection, we use the uncertainty maps provided by MIPSGAL. For the clouds with detections, we add the pixel errors in quadrature over the integration box and multiply by the pixel spacing to get a flux density error; for the other clouds, we take the mean over the uncertainty map and multiply by the square root of the number of pixels in a 2’ box and the pixel spacing. We then propagate the distance error and the errors in the parameters of Eq. [\[eq:24muSFR\]](#eq:24muSFR) appropriately to get an error. We again use a 2$\sigma$ detection as an upper limit. We note that these errors, as well as the errors for the SFR calculated with H30$\alpha$, are likely underestimates, as there is additional uncertainty from the stochastic distribution around the initial mass function (IMF) for small clusters.

To remove scatter due to cloud size, we calculate an SFR density ($\Sigma_\text{SFR}$) by dividing over the physical area of integration in units of squared parsecs. For the 24 $\mu$m data, this area is a 2’ box taken at the cloud distance. For the H30$\alpha$ detections, some of the integrated intensity data is masked by our 4$\sigma_\text{rms}$ cut, as seen in Figure [11](#fig:h30moment0), so the area is slightly less than a 1’ box at the cloud distance. For the H30$\alpha$ upper limits, the area is the full 1’ box at the cloud distance. We note that, since $Q$ is proportional to $D^2$, the $\Sigma_\text{SFR}$ calculated with H30$\alpha$ is not directly dependent on distance, but there is still a weak dependence on distance given Eqs. [\[eq:eTempGradient\]](#eq:eTempGradient) and [\[eq:neDiameter\]](#eq:neDiameter). Additionally, since $L_{24\mu \text{m}}$ is also proportional to $D^2$, and the SFR calculated with 24 $\mu$m emission is proportional to $L_{24\mu \text{m}}^{0.8850}$, the $\Sigma_\text{SFR}$ calculated with 24 $\mu$m emission has a weak inversely proportional dependence on distance.

A comparison between the two $\Sigma_\text{SFR}$ measures is shown in Figure [14](#fig:sfr). The values generally agree for the clouds that are detected in both. We are also able to place stricter upper limits using H30$\alpha$ due to the higher sensitivity of ALMA.

(cite: calzetti_calibration_2007) notes that emission at 8 $\mu$m is correlated with star formation, but it also depends strongly on metallicity and size, so we do not calculate an SFR using the 8 $\mu$m emission from GLIMPSE. We note, however, that 8 $\mu$m emission is present for all clouds that exhibit 24 $\mu$m emission.

## Shocks

Both methanol (CH~3~OH) and SiO are associated with the presence of shocks (cite: meier_spatially_2005; schilke_sio_1997), although they trace different shock velocities. CH~3~OH can be formed on grain mantles then evaporated into the gas phase through weak shocks with $v_s \lesssim 10$ km s$^{-1}$ (cite: bergin_postshock_1998). On the other hand, evaporation of SiO into the gas phase requires more energetic grain processing through grain core or mantle erosion, which can occur in shocks with $v_s \gtrsim 25$ km s$^{-1}$ (cite: garay_silicon_2000).

SiO is detected in all clouds except G005.75 and G005.49, and CH~3~OH is detected in all clouds except G005.49.

### SiO

We can calculate the column density of SiO, with several assumptions. We assume optically thin emission, LTE, a Rayleigh-Jeans approximation, and negligible background. Then, the column density is $$\begin{equation}
\label{eq:sioColDens}
N_\text{tot} = \left( \frac{3k_B}{8\pi^3 \nu S \mu^2}\right) \left( \frac{Q_\text{rot}}{g_J g_K g_I} \right) \text{exp}\left( \frac{E_u}{k_B T_\text{ex}} \right) \int \frac{T_B dv}{f}
\end{equation}$$ (cite: mangum_how_2015), where $Q_\text{rot}$ is the partition function, $g_i$ are the degeneracies, $\mu$ is the dipole moment of the molecule, $S$ is the intrinsic line strength, $E_u$ is the upper energy level, $T_\text{ex}$ is the excitation temperature of the gas, and $f$ is the beam filling factor. For a linear molecule like SiO, we have $g_J = 2J +1$, $g_K = g_I = 1$, $Q_\text{rot} = \sum_{J=0}^\infty (2J+1) \text{exp}(-\frac{E_J}{kT})$, and $S = \frac{J}{2J+1}$. For a diatomic molecule, the rotational energy levels are $E_J \approx hBJ(J+1)$, where $B = \frac{\hbar}{4\pi I}$ is the rotational constant of the molecule. For SiO in particular, the dipole moment is $\mu = 3.0982$ Debye (cite: raymonda_electric_1970) and the rotational constant is $B = 21787.5$ MHz (cite: lowry_manson_millimeter_1977). The column density is proportional to $Q_\text{rot}(T_\text{ex})\text{exp}\left(\frac{1}{T_\text{ex}}\right)$, which has a global minimum at $T_\text{ex} = 31.72$ K. We find that the difference between the column density assuming $T_\text{ex} = 31.72$ K and at the LTE case of $T_\text{ex} = T_\text{k}$ (where we take to be the formaldehyde gas temperature to be the gas kinetic temperature sampled by SiO since the formaldehyde temperature is more likely to sample denser gas than the ammonia temperature) is less than the uncertainty in the integrated intensity of SiO $J = 5 \to 4$, which we take to be within the same 1’ box that the formaldehyde temperature is calculated in. However, at a gas density of $n(\text{H}_2) = 10^{4} \text{ cm}^{-3}$, which we assumed when calculating the formaldehyde temperature, the SiO $J=5\to 4$ line is subthermally excited ($T_\text{ex} \ll T_\text{k}$). With RADEX, we find that the SiO column density derived from the LTE assumption is insufficient to explain the observed line intensity. Indeed, for nearly all of the clouds in the sample, either $n(\text{H}_2)$ or $N(\text{SiO})$ must be 1 to 3 orders of magnitude higher, or the kinetic temperature of the gas phase traced by SiO must be significantly higher than that traced by formaldehyde. As we are unable to further constrain the H~2~ number density or the gas kinetic temperature sampled by SiO, we treat the SiO column densities calculated under the assumption of LTE as lower limits on the true column density. We also assume the beam filling factor is 1, although it may be lower, in which case the calculated column densities will be lower limits; however, if the beam filling factors for the SiO and CO observations are similar, then the SiO abundances N(SiO)/N(H~2~) are independent of the beam filling factor.

We also calculate column densities of ^13^CO and C^18^O $J = 2 \to 1$ to obtain SiO abundances. Since it is likely these lines are optically thin, compared to their isotopologue ^12^CO, we can again use Eq. [\[eq:sioColDens\]](#eq:sioColDens).[^4]. These lines are likely to be closer to LTE than the subthermally excited SiO $J = 5 \to 4$ line.

We use the ^12^C/^13^C and ^16^O/^18^O isotope abundance ratios, respectively, which increase with Galactocentric radius (cite: langer_12c_1990). We use the equations $$\begin{equation}
\label{eq:cAbundance}
^{12}\mathrm{C}/^{13}\mathrm{C} = (7.5 \pm 1.9) R_\text{Gal} + (7.6 \pm 12.9)
\end{equation}$$ and $$\begin{equation}
\label{eq:oAbundance}
^{16}\mathrm{O}/^{18}\mathrm{O} = (58.8 \pm 11.8) R_\text{Gal} + (37.1 \pm 82.6)
\end{equation}$$ from (cite: wilson_abundances_1994). The ^12^CO column densities derived from the two isotopologues agree well. The SiO abundances derived from both, where we have assumed a typical ^12^CO-to-H~2~ abundance ratio of $10^{-4}$ for dense clouds (e.g., (cite: lacy_detection_1994; burgh_direct_2007)), largely agree within error bars.

Shocks can enhance the abundance of SiO to values greater than 10$^{-10}$ compared to ambient values of 10$^{-12}$–10$^{-11}$ (cite: schilke_sio_1997; garay_silicon_2000), and they have been shown to enhance abundances to values as high as 10$^{-6}$ at extreme velocities (cite: martin-pintado_sio_1992). Many of the clouds in our sample exhibit SiO abundances above 10$^{-10}$, with some exceeding 10$^{-9}$, indicating that the gas in these clouds are likely undergoing shocks.

### Methanol

We use the line ratio of CH~3~OH $J = 4_{22} \to 3_{12}$ to ^13^CO $J = 2\to 1$ to assess the weak shocks associated with methanol emission. We take the mean value of the 1’ box centered on the pixel with peak H~2~CO $J = 3_{03} \to 2_{02}$ emission, and we take the error to be the mean of the ratio error map within the same box.

The values derived for all properties above are reported in Table [1](#table:cloudprops).

## Mass

We calculate masses for each cloud using the ^12^CO, ^13^CO, and C^18^O integrated intensity maps. As in Section [4.4](#subsec:shocks), we calculate the column density maps of ^13^CO and C^18^O, assuming they are optically thin, then use ^12^C/^13^C and ^16^O/^18^O isotope abundance ratios (Eqs. [\[eq:oAbundance\]](#eq:oAbundance) and [\[eq:cAbundance\]](#eq:cAbundance)) to convert to column density maps of ^12^CO. From this, we multiply by the typical ^12^CO-to-H~2~ abundance ratio of $10^{-4}$ to estimate the H~2~ column density. For the two clouds without detections of H~2~CO $(3_{21}-2_{20})$, we estimate the kinetic temperature to be the ammonia (3,3) - (1,1) temperature. In contrast, for the ^12^CO, which is unlikely to be optically thin compared to ^13^CO and C^18^O, we multiply the integrated intensity by the CO-to-H~2~ X-factor of $2.3 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ derived by (cite: strong_radial_1988). We also multiply by the factor 0.8, the typical ^12^CO $J=2 \to 1/J=1\to 0$ line ratio (cite: leroy_heracles_2009).

For each cloud, we integrate the three derived H~2~ column density maps, then multiply by the molecular weight per hydrogen molecule, $\mu_{\text{H}_2} = 2.8$, which accounts for cosmic abundance ratios (e.g., (cite: kauffmann_mambo_2008)), to calculate an estimated cloud mass. We define the extent of the cloud to integrate over using a 5$\sigma$ (Eq. [\[eq:noise\]](#eq:noise)) cutoff on the integrated intensity map of H~2~CO $J=3_{03} \to 2_{02}$, because the extent of the cloud is less clear on the CO maps, even for the less abundant isotopologues.

The masses derived from all three CO isotopologues are shown in Table [\[table:masses\]](#table:masses). We also plot several other properties derived against Galactic longitude in Figure [15](#fig:glonProperties).

# Discussion

## Ammonia and Formaldehyde Thermometers

As noted in Section [4.1.3](#subsubsec:ammFormTemp), based on our data and temperature determination methods, there appears to be no correlation between the formaldehyde and ammonia temperatures of the clouds, indicating that the two thermometers may be tracing different gas in the clouds or some of the methods to derive the gas temperatures are not applicable to these clouds. The critical densities of the ammonia lines are lower than those of the formaldehyde lines, and so, the ammonia temperature generally traces more diffuse gas than the formaldehyde thermometer (cite: ginsburg_dense_2016). This may explain why the hot molecular cores seen in the formaldehyde temperature maps are generally not present in the ammonia temperature maps (Figures [6](#fig:NH3temp) and [8](#fig:H2COtemp)), although this may also be in part due to the smaller ALMA beam size of the formaldehyde data compared to the Mopra beam size of the ammonia data.

In Figure [16](#fig:tempProperties), we plot the Mach number, $\Sigma_\text{SFR}$, SiO abundance, and CH~3~OH/^13^CO line ratio against the ammonia and formaldehyde temperature for each cloud. The ammonia temperature is well-correlated with the turbulent Mach number, whereas the formaldehyde temperature is not. Although the Mach numbers are calculated using the formaldehyde temperatures and line widths, the result would be similar if the Mach numbers were calculated using ammonia since the thermal line widths (calculated from Eq. [\[eq:vThermal\]](#eq:vThermal) with the ammonia temperatures) are small compared to the observed ammonia line widths. On the other hand, the opposite is true for correlations with the CH$_3$OH/$^{13}$CO line ratio, which is a weak shock tracer. No strong correlations are apparent for any other properties. Given that the molecules all seem to trace different phases of the gas, each of which likely has different physical properties, strong correlations are not expected.

Another notable feature is that the clouds with the highest ammonia temperatures ($T_{13} > 50$ K) all do not have detected star formation; in other words, all the clouds with detected star formation (with both 24 $\mu$m and H30$\alpha$ emission) are at comparatively lower

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Cloud | T~12~ | T~13~ | T~H$_2$CO~ | $\Delta v_{\text{H}_2\text{CO} 3_{03}-2_{02}}$ | $\mathcal{M}$ | $\text{log}_{10} \Sigma_{\text{SFR, H30}\alpha}$ | $\text{log}_{10} \Sigma_{\text{SFR}, 24\mu\text{m}}$ | N(SiO)/N(H~2~ (^13^CO) | N(SiO)/N(H~2~) (C^18^O) | CH~3~OH/^13^CO |
|  | K | K | K | km s$^{-1}$ |  | M$_\odot$ yr$^{-1}$ pc$^{-2}$ | M$_\odot$ yr$^{-1}$ pc$^{-2}$ |  |  |  |
| G008.67 | $19.59 \pm 1.29$ | $33.98 \pm 1.18$ | $68.87 \pm 1.53$ | $5.17 \pm 0.07$ | $7.47 \pm 0.13$ | $-5.22 \pm 0.09$ | $\geq-5.50$ | $\geq -10.2$ | $\geq -10.7$ | $0.0442 \pm 0.0004$ |
| G008.40 | $23.59 \pm 3.38$ | $34.96 \pm 2.86$ | $40.45 \pm 1.76$ | $4.34 \pm 0.06$ | $8.25 \pm 0.22$ | $\leq -7.80$ | $\leq -6.00$ | $\geq -10.3$ | $\geq -10.6$ | $0.0072 \pm 0.0003$ |
| G006.92 | $20.28 \pm 3.47$ | $33.56 \pm 3.16$ | $35.09 \pm 1.85$ | $4.71 \pm 0.09$ | $9.65 \pm 0.32$ | $\leq -7.43$ | $\leq -5.86$ | $\geq -9.82$ | $\geq -10.1$ | $0.0387 \pm 0.0016$ |
| G006.56 | $42.36 \pm 13.18$ | $85.63 \pm 16.02$ | $69.98 \pm 3.17$ | $12.33 \pm 0.10$ | $18.05 \pm 0.43$ | $\leq -7.47$ | $\leq -6.29$ | $\geq -9.72$ | $\geq -9.53$ | $0.0076 \pm 0.0008$ |
| G005.75 | $37.64 \pm 10.92$ | $74.34 \pm 12.19$ | — | $11.03 \pm 0.24$ | — | $\leq -7.37$ | $\leq -6.68$ | — | — | $0.0073 \pm 0.0025$ |
| G005.49 | — | $122.16 \pm 86.33$ | — | $9.43 \pm 0.16$ | — | $\leq -7.41$ | $\leq -6.58$ | — | — | — |
| G005.38 | $35.05 \pm 6.98$ | $71.68 \pm 8.05$ | $35.51 \pm 1.70$ | $18.26 \pm 0.15$ | $37.65 \pm 0.95$ | $\leq -7.42$ | $\leq -6.55$ | $\geq -9.32$ | $\geq -9.05$ | $0.0328 \pm 0.0015$ |
| G003.43 | $19.69 \pm 1.62$ | $27.37 \pm 1.83$ | $49.25 \pm 2.84$ | $4.66 \pm 0.04$ | $8.00 \pm 0.24$ | $\leq -7.55$ | $\geq-6.09$ | $\geq -9.94$ | $\geq -10.3$ | $0.0703 \pm 0.0016$ |
| G003.09 | $46.89 \pm 2.17$ | $77.88 \pm 1.90$ | $102.67 \pm 1.41$ | $25.71 \pm 0.08$ | $31.19 \pm 0.24$ | $\leq -7.43$ | $\leq -6.66$ | $\geq -9.09$ | $\geq -8.98$ | $0.0812 \pm 0.0003$ |
| G003.02 | $31.48 \pm 1.75$ | $72.09 \pm 2.33$ | $47.54 \pm 1.94$ | $15.38 \pm 0.25$ | $45.81 \pm 1.04$ | $\leq -7.30$ | $\leq -6.56$ | $\geq -8.96$ | $\geq -8.55$ | $0.0159 \pm 0.0041$ |
| G002.96 | $33.89 \pm 4.34$ | $63.03 \pm 4.22$ | $38.18 \pm 4.43$ | $11.97 \pm 0.13$ | $23.83 \pm 1.41$ | $\leq -7.47$ | $\leq -6.56$ | $\geq -9.73$ | $\geq -9.41$ | $0.0084 \pm 0.0015$ |
| G002.51 | $30.56 \pm 1.91$ | $52.16 \pm 1.60$ | $49.35 \pm 2.45$ | $21.39 \pm 0.28$ | $37.51 \pm 1.06$ | $\leq -7.61$ | $\leq -6.46$ | $\geq -9.38$ | $\geq -9.34$ | $0.0280 \pm 0.0006$ |
| G001.93 | $33.15 \pm 6.19$ | $59.59 \pm 5.68$ | $26.76 \pm 1.81$ | $14.99 \pm 0.23$ | $35.17 \pm 1.32$ | $\leq -7.55$ | $\leq -6.64$ | $\geq 9.96$ | $\geq -9.66$ | $0.0134 \pm 0.0009$ |
| G358.48 | $31.08 \pm 6.21$ | $37.13 \pm 4.10$ | $48.85 \pm 2.28$ | $5.49 \pm 0.06$ | $9.53 \pm 0.25$ | $\leq -7.52$ | $\leq -5.91$ | $\geq -10.1$ | $\geq -10.5$ | $0.0251 \pm 0.0006$ |
| G354.61 | $29.67 \pm 5.36$ | $38.40 \pm 3.72$ | $68.56 \pm 2.16$ | $6.46 \pm 0.10$ | $9.47 \pm 0.21$ | $-5.89 \pm 0.17$ | $\geq-5.51$ | $\geq -9.95$ | $\geq -10.3$ | $0.0363 \pm 0.0003$ |
| G353.41 | $18.98 \pm 0.97$ | $31.02 \pm 0.94$ | $69.79 \pm 0.71$ | $7.51 \pm 0.07$ | $10.95 \pm 0.12$ | $-4.66 \pm 0.34$ | $\geq-5.00$ | $\geq -10.1$ | $\geq -10.50$ | $0.0316 \pm 0.0002$ |
| G351.77 | $16.97 \pm 1.89$ | $32.09 \pm 1.78$ | $129.70 \pm 0.69$ | $8.12 \pm 0.08$ | $8.62 \pm 0.09$ | $-5.01 \pm 0.08$ | $\geq-5.51$ | $\geq -9.41$ | $\geq -9.84$ | $0.1030 \pm 0.0002$ |
| G351.58 | $18.39 \pm 2.21$ | $36.10 \pm 1.99$ | $127.70 \pm 1.97$ | $7.54 \pm 0.12$ | $8.04 \pm 0.15$ | $-4.99 \pm 0.18$ | $\geq-5.86$ | $\geq -9.58$ | $\geq -10.23$ | $0.1674 \pm 0.0007$ |
| G350.18 | $20.36 \pm 3.36$ | $32.65 \pm 3.11$ | $34.57 \pm 3.07$ | $6.23 \pm 0.07$ | $12.79 \pm 0.59$ | $-6.09 \pm 0.12$ | $\geq-5.89$ | $\geq -11.0$ | $\geq -11.3$ | $0.0063 \pm 0.0010$ |
| G350.10 | $24.92 \pm 2.76$ | $39.04 \pm 2.24$ | $53.15 \pm 1.32$ | $6.73 \pm 0.06$ | $11.24 \pm 0.18$ | $-4.76 \pm 0.12$ | $\geq-5.15$ | $\geq -9.94$ | $\geq -10.2$ | $0.0323 \pm 0.0003$ |

: Clouds properties derived in Section [4](#sec:results). The clouds we take to be inside the bar, per the discussion in Sections [3](#sec:loc) and [5.4](#subsec:loc2), have their names underlined and in bold.

ammonia temperatures. This is not observed with the formaldehyde temperature.

![](sfr.pdf)

There are several possible reasons for these differences. It may be that formaldehyde is more sensitive to heating from star formation, giving the distinct core structure in the formaldehyde temperature maps, and that ammonia is more sensitive to turbulent heating, resulting in a strong correlation with Mach number. Although neither formaldehyde temperatures nor ammonia temperatures appear to correlate with the SiO abundance, the stronger correlation with the methanol line ratio may indicate that formaldehyde is more sensitive to weak shocks that do not necessarily cause turbulence in the gas. Methanol emission, although associated with shocks, has also been found to be suppressed at sites of star formation due to direct photodissociation or inefficient production from CO on dust grains (e.g., (cite: meier_spatially_2014; saito_merger-induced_2017)), so star formation is unlikely to explain the correlation between formaldehyde and methanol. A simpler explanation may be that formaldehyde and methanol are chemically similar, whereas the nitrogen atom in ammonia may make it chemically different from methanol. Indeed, astrochemical theory and experiments have shown that both formaldehyde and methanol can be, and likely are, produced by successive hydrogenation of CO on ice and dust grains in molecular clouds (e.g., (cite: hiraoka_formation_1994; watanabe_efficient_2002; potapov_formation_2017)).

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Cloud | Mass Estimate (^12^CO) | Mass Estimate (^13^CO) | Mass Estimate (C^18^O) |
|  | M$_\odot \times 10^3$ | M$_\odot \times 10^3$ | M$_\odot \times 10^3$ |
| G008.67 | $5.3 \pm 0.5$ | $4.3 \pm 0.4$ | $9.1 \pm 0.8$ |
| G008.40 | $13.6 \pm 3.0$ | $6.8 \pm 1.5$ | $13.0 \pm 2.9$ |
| G006.92 | $1.8 \pm 0.5$ | $0.7 \pm 0.2$ | $1.3 \pm 0.4$ |
| ***G006.56*** | $116.5 \pm 17.8$ | $11.5 \pm 1.8$ | $7.8 \pm 1.2$ |
| ***G005.75*** | $14.2 \pm 2.1$ | $0.9 \pm 0.1$ | $0.3 \pm 0.0$ |
| ***G005.49*** | $4.5 \pm 0.7$ | $0.4 \pm 0.1$ | $0.020 \pm 0.003$ |
| ***G005.38*** | $34.9 \pm 5.2$ | $1.5 \pm 0.2$ | $0.6 \pm 0.1$ |
| G003.43 | $0.5 \pm 0.2$ | $0.2 \pm 0.1$ | $0.3 \pm 0.1$ |
| ***G003.09*** | $276.7 \pm 39.8$ | $27.1 \pm 3.9$ | $17.8 \pm 2.6$ |
| ***G003.02*** | $311.6 \pm 44.8$ | $15.9 \pm 2.3$ | $6.1 \pm 0.9$ |
| ***G002.96*** | $84.6 \pm 12.1$ | $4.1 \pm 0.6$ | $2.4 \pm 0.3$ |
| ***G002.51*** | $53.7 \pm 7.6$ | $5.0 \pm 0.7$ | $3.3 \pm 0.5$ |
| ***G001.93*** | $48.6 \pm 6.9$ | $2.1 \pm 0.3$ | $0.9 \pm 0.1$ |
| G358.48 | $2.7 \pm 1.1$ | $2.0 \pm 0.8$ | $3.9 \pm 1.5$ |
| G354.61 | $46.2 \pm 8.3$ | $32.3 \pm 5.8$ | $60.0 \pm 10.8$ |
| G353.41 | $3.4 \pm 1.2$ | $3.5 \pm 1.2$ | $7.0 \pm 2.4$ |
| G351.77 | $2.0 \pm 0.1$ | $3.5 \pm 0.2$ | $7.1 \pm 0.5$ |
| G351.58 | $5.2 \pm 1.0$ | $4.0 \pm 0.8$ | $10.4 \pm 2.0$ |
| G350.18 | $7.7 \pm 1.0$ | $1.8 \pm 0.2$ | $2.7 \pm 0.3$ |
| G350.10 | $24.8 \pm 3.2$ | $9.8 \pm 1.3$ | $15.5 \pm 2.0$ |

![](glonProperties.pdf)

![](tempProperties.pdf)

![](sfMach.pdf)

Furthermore, while the ammonia temperature is largely independent of H~2~ density (e.g., (cite: ott_temperature_2005)), formaldehyde is an asymmetric top molecule, and thus, the H~2~ density affects the excitation of the different energy levels. Although the asymmetry in formaldehyde is very small (cite: mangum_formaldehyde_1993), making it useful for measuring molecular cloud kinetic temperatures (e.g., (cite: hogerheijde_millimeter_1995), (cite: ao_thermal_2013), (cite: ginsburg_dense_2016), (cite: tang_kinetic_2018)), most of these studies that survey a large area or multiple clouds typically assume a constant $n(\text{H}_2)$ across the sample. For example, (cite: ginsburg_dense_2016) assumes $n(\text{H}_2) = 10^{4}$ cm^-3^ for most analyses, although they also calculate kinetic temperatures with a constant $n(\text{H}_2) = 10^{3}$ cm^-3^ and $n(\text{H}_2) = 10^{5}$ cm^-3^. Similarly, (cite: tang_kinetic_2018) assumes a constant $n(\text{H}_2) = 10^{5}$ cm^-3^ across their sample of ATLASGAL clumps. However, given the variety of clouds in our sample, particularly in their location and possible environment, assuming a constant H~2~ density is likely an oversimplification. We therefore also explore the H~2~ densities required to explain the observed formaldehyde emission using the ammonia temperature as the kinetic temperature of the gas.

For each cloud, we estimate the column density of H~2~CO using a $N(\text{H}_2\text{CO})$-to-$N(\text{H}_2)$ abundance ratio of $1.2 \times 10^{-9}$ (cite: wootten_molecular_1978; ginsburg_dense_2016), where we use the H~2~ column densities derived from the LTE calculations of ^13^CO and C^18^O in Section [4.4.1](#subsubsec:sio). In Sections [4.5](#subsec:mass), we also calculate the H~2~ density directly using the ^12^CO emission and a CO-to-H~2~ X-factor; however, as discussed in [5.5](#subsec:xfactor), we find that this is likely less accurate, particularly for clouds in the bar.

We use RADEX to calculate the $R_{\rm{H}_2 \rm{CO}}$ line ratio at the cloud’s ammonia temperature (T~13~), H~2~CO $J=3_{03} \to 2_{02}$ line width, the two derived H~2~CO column densities, and a range of H~2~ volume densities ($n = 10^{2.5} - 10^{7}$ cm$^{-3}$). We then interpolate and attempt to calculate the H~2~ volume density given the observed line ratio for both column densities. The line width, line ratio, and column densities are taken to be the average within within the same 1’ box that the formaldehyde temperature is calculated in.

We find that, for all but four of the clouds, there is no H~2~ density for which the expected line ratio from RADEX matches the observed line ratio. The four clouds for which there is an H~2~ density at which the two agree are the four clouds where the formaldehyde and ammonia temperatures from Section [5.1](#subsec:temperature) agree within uncertainties. In the cases where T~H$_2$CO~ $>$ T~13~, the formaldehyde column density must be several orders of magnitude higher for there to be a H~2~ density at which the colder T~13~ can explain the observed line ratio. On the other hand, for the clouds where T~H$_2$CO~ $<$ T~13~, there is no combination of formaldehyde column density and H~2~ density at which the warmer T~13~ can explain the observed line ratio.

Given that the critical densities of the ammonia lines are orders of magnitude lower than those of the formaldehyde lines (cite: shirley_critical_2015; ginsburg_dense_2016), we expect that the two temperatures trace different density components of the gas. This is further complicated by the significant difference in beam size of the two observations. We therefore do not necessarily expect the two to agree, although we do not conclude that one traces the overall properties of the clouds better than the other. More data at a comparable resolution is needed to better understand the relationships between the ammonia and formaldehyde thermometers.

## Star Formation and Turbulence

We note in Section [5.1](#subsec:temperature) that the clouds with higher ammonia temperatures all do not have 24 $\mu$m or H30$\alpha$ detections. At the same time, we see in Figure [16](#fig:tempProperties) that these clouds have the highest Mach numbers ($\mathcal{M} > 15$) in the sample. This indicates that the turbulence in these clouds may be inhibiting star formation to some degree.

We plot the $\Sigma_\text{SFR}$ measured by H30$\alpha$ against the Mach number in Figure [17](#fig:sfMach). Although there is no direct inverse correlation between the two, we find that all the clouds with detected star formation are at relatively low Mach numbers; in other words, the highly turbulent clouds are not star forming.

It is well known that the SFR in the CMZ is significantly lower than expected given the high gas densities and that this discrepancy may be due to turbulent pressure (cite: longmore_variations_2013; kruijssen_what_2014; barnes_star_2017). The relationship between SFR and turbulence is less understood on the scale of individual molecular clouds, as turbulence can both create density fluctuations needed for local collapse (e.g., (cite: mac_low_control_2004)) and also prevent global cloud collapse (e.g., (cite: federrath_link_2016)). Meanwhile, star formation itself can inject energy into the surrounding gas, enhancing turbulence (cite: yun_turbulent_2021); we see that, although the clouds with detected star formation are comparatively less turbulent, their Mach numbers still indicate supersonic motions, likely caused by dynamical activities related to stellar feedback. We conclude from our observations that the turbulent pressure is suppressing star formation in the clouds with high Mach numbers.

## What is Heating the Clouds?

The gas temperatures of most of the clouds in our sample are well above the typical values in the Galactic disk of $\sim 10-20$ K, and some are well above the CMZ average of $\sim$60 K (cite: ginsburg_dense_2016).

There are likely four main heating mechanisms for molecular clouds here: radiative photoelectric heating, X-ray heating, cosmic ray heating, and turbulent heating (e.g., (cite: ao_thermal_2013)).

Although the Galactic center and CMZ regions have an elevated X-ray luminosity (cite: yuasa_suzaku_2008; muno_diffuse_2004) and cosmic ray ionization rate (cite: yusef-zadeh_cosmic-ray_2007; indriolo_herschel_2015), we do not expect this to be the case for the Galactic bar and disk regions in which the clouds in our sample lie. (cite: ginsburg_dense_2016) finds that, although in some regions of the CMZ, heating from cosmic rays may be important, the energetics of the CMZ are largely dominated by turbulent heating. X-ray heating and cosmic ray heating can thus be disfavored as heating mechanisms in these clouds.

In the clouds with no detections of H30$\alpha$ or Spitzer 24 $\mu$m emission, it is highly unlikely that radiation plays a major role in heating since the nondetection of these indicates the lack of high-mass stars. Thus, for these clouds, the most likely heating mechanism is turbulence. We can estimate the temperature due to turbulent heating: $$\begin{equation}
\label{eq:turbTemp}
\begin{split}
T_\text{turb} = & \ 62 \left( \frac{n}{10^{4.5} \text{ cm}^{-3}} \right)^{1/6} \left( \frac{L}{5 \text{ pc}} \right)^{-1/3} \\
& \ \times \left(\frac{ \text{d}v/\text{d}r}{5 \text{ km\ s}^{-1} \text{ pc}^{-1}}\right)^{-1/3} \left( \frac{V_\text{FWHM}}{20 \text{ km\ s}^{-1}} \right) \text{ K},
\end{split}
\end{equation}$$ which is a simplified analytic solution to the turbulence-dominated thermal equilibrium equation, assuming gas densities $n \leq 10^{5} \text{ cm}^{-3}$, where $L$ is the size of the cloud, d$v/$d$r$ is the velocity gradient of the cloud, and $V_\text{FWHM}$ is the observed FWHM line width (cite: ao_thermal_2013).

![](turbTemp.pdf)

Since the structure of the formaldehyde emission is generally more complex than the H30$\alpha$ emission, we fit a circular two-dimensional Gaussian around the peak H~2~CO $(3_{21}-2_{20})$ emission to calculate the cloud angular diameter, rather than fit a 1-dimensional Gaussian to the flattened PV diagram as in Section [4.3](#subsec:sf). We again take the angular diameter to be four times the standard deviation of the Gaussian fit, then calculate the physical size of the cloud using its distance.

We use the cloud velocity gradients measured in Section [4.2](#subsec:turb) and assume a gas density of $10^4 \text{ cm}^{-3}$, the same as used to derive Eq. [\[eq:formaldehydeTemp\]](#eq:formaldehydeTemp), although we note that the estimated turbulent kinetic temperature depends relatively weakly on the gas density, cloud size, and velocity gradient compared to the line width. We calculate the estimated turbulence-driven kinetic temperatures of all our clouds and plot the results against the observed formaldehyde temperatures in Figure [18](#fig:turbTemp), noting the clouds that are detected with Spitzer.

We see that, for the clouds with no detected Spitzer emission, or in other words, with no detected star formation, turbulent heating is generally sufficient to explain the observed temperatures of the clouds, but for the clouds with detected Spitzer emission, it is generally insufficient. We can then expect that turbulence is the dominant heating mechanism in the clouds without star formation, whereas radiation is dominant in the clouds with star formation.

Although turbulence is likely heating the non-star-forming clouds, it is uncertain what exactly is causing the turbulence. High-velocity shocks could be one potential mechanism driving turbulence. Such shocks would be traced by SiO (cite: martin-pintado_sio_1992; schilke_sio_1997; garay_silicon_2000), but we find no correlation between the SiO abundances and the kinetic temperature (see Figure [16](#fig:tempProperties)). Our analysis of the SiO column densities in Section [4.4.1](#subsubsec:sio) suggests that the kinetic temperature of the gas phase traced by SiO is possibly significantly higher than that traced by formaldehyde, and given such a multiphase scenario, a correlation between properties of phases traced by different molecules is not expected. We also note that, due to the likely subthermal emission of the SiO $J = 5\to 4$ line, the SiO abundances calculated in Section [4.4.1](#subsubsec:sio) are lower limits. However, the values do appear to be, on average, higher for clouds in the bar (see Figure [15](#fig:glonProperties)), and in general are elevated above ambient values of $10^{-12}$ to $10^{-11}$ (cite: schilke_sio_1997; garay_silicon_2000). On the other hand, shocks at lower velocity, as traced by methanol, may also be contributing to turbulence and heating. We do see a weak correlation between the methanol line ratio and the formaldehyde temperature, as noted in Section [5.1](#subsec:temperature), although this is complicated by the fact that the clouds with star formation also appear to show elevated methanol line ratios. We can see in the integrated intensity maps in Figure Set [2](#fig:integratedIntensities) that the methanol emission is slightly more extended than the SiO emission for many clouds, indicating that weak shocks may be prevalent on a wider scale, potentially heating the gas, generating turbulence, and mildly elevating the SiO abundance as well. As such, shocks may be a reasonable source for the observed turbulence, particularly for the clouds in the bar, although the exact source is uncertain. The uncertainty is compounded by the assumption of gas in a single phase in our calculations, whereas the clouds are certainly much more complex.

## Where Are the Clouds Located?

In Section [3](#sec:loc), we discussed the locations of the clouds based primarily on their line widths and prior kinematic distance determinations. With the greater context of the various properties we have derived, we provide further evidence that some of the clouds in the sample lie in the Galactic bar region.

We initially considered all clouds with an NH~3~ (1,1) line width greater than 10 km s$^{-1}$ to be on the Galactic bar, since such broad lines are atypical for clouds in the Galactic disk. However, we noted that the two clouds at the most negative Galactic longitude, G350.18 and G350.11, are at Galactocentric radii around 4 kpc, which may be beyond the extent of the Galactic bar, and so preliminarily concluded that they do not lie in the bar region, despite having broad lines. However, given that the bar may extend to 5 kpc or greater (cite: wegg_structure_2015), it is possible that these two clouds are in the region around the tip of the bar, where gas accumulates at the apocenter of x~1~ orbits. With our ALMA observations, we find that these two clouds have relatively narrow formaldehyde line widths, and note that their Mach numbers and ammonia temperatures, both of which are calculated independent of distance, are lower than all of the other clouds we assumed to be in the bar. We thus still consider these two clouds to be part of a separate population from the nine clouds in the bar region.

In fact, we can broadly categorize the clouds in our sample into three groups. The first is highly turbulent clouds with no detected star formation. The Mach numbers of these clouds are all greater than 15, and many match or exceed values expected in the CMZ ($\gtrsim 25$). Although we can not calculate Mach numbers for G005.49 and G005.75 since they are not detected with the H~2~CO $J=3_{21} \to 2_{20}$ line, we include them in this group because they are associated with the same cloud complex G5 as G003.58; have very high ammonia temperatures, as do the other clouds in this group ($T_{13} > 50$ K); and also do not exhibit any star formation. Furthermore, G005.49 is the only cloud for which the bulk motion, as measured by the velocity gradient in Section [4.2](#subsec:turb), appears to dominate the line width, indicating that some gradient-inducing process, such as shear, rotation, or a cloud-cloud collision, is affecting the cloud. In total, there are nine clouds in this group, and these nine are the same as the clouds we considered to be in the Galactic bar in Section [3](#sec:loc). As previously noted, seven of these clouds are associated with either G5 or B2, both of which have been suggested to be high-velocity collisions in the Galactic bar region, possibly between the dust lanes and overshooting gas (cite: fux_3d_1999; sormani_geometry_2019; gramze_evidence_2023). The other two clouds in this group, G006.56 and G001.93, have not previously been studied in detail, but their similar features to the clouds in G5 and B2 indicate that they may also be undergoing collisions, perhaps as they cross the nearside dust lane, or subject to other extreme physical processes in the Galactic bar region. In particular, G001.93 appears to be located spatially near the CMZ, so it may belong to a collision between the dust lane and CMZ itself, which is a second type of extended velocity feature observed in the dynamical simulations of (cite: sormani_geometry_2019), or it may be subject to conditions closer to those in the CMZ. We conclude that, regardless of whether these clouds are undergoing high-velocity collisions, the extreme processes in the Galactic bar region are inhibiting gravitational collapse and suppressing star formation.

The second group contains stars with detected star formation but low turbulence. As noted in Section [5.2](#subsec:sfTurb), the eight clouds with 24 $\mu$m detections, seven of which are also detected with H30$\alpha$, exhibit Mach numbers comparable to typical molecular clouds in the Galactic disk ($\lesssim$ 10), so these are likely normal Galactic disk star-forming regions. G350.18 and G350.11, which may lie around the tip of the Galactic bar, belong to this group. If these two clouds are indeed near the end of the bar, this may indicate that the processes causing the observed turbulence and inhibited star formation in the Galactic bar nearer to the Galactic Center, such as collisions and shears, are less prominent around the edge of the Galactic bar, because these two clouds do not exhibit such turbulence or suppressed star formation. This may agree with previous observations of nearby barred galaxies that show inhibited star formation along the length of the bar but strong star formation at the center and ends of the bar (e.g., (cite: reynaud_kinematics_1998; james_stellar_2016)).

The remaining three clouds, G008.40, G006.92, and G358.48, exhibit neither turbulence nor star formation. These are also likely typical Galactic disk molecular clouds with unusually bright NH~3~ (3,3) emission, and they may become star-forming in the future.

We note here that while the calculation of $\Sigma_\textrm{SFR}$ is weakly dependent on distance, as noted in Section [4.3](#subsec:sf), the detection or non-detection of star formation is enough to distinguish between our three groups. The only other properties calculated in Section [4](#sec:results) that are dependent on distance are the SiO abundance (Section [4.4.1](#subsubsec:sio)) and mass (Section [4.5](#subsec:mass)). However, we do not use these properties when distinguishing between our three groups. We do note that the SiO abundance may be generally elevated for clouds in the bar (see Figure [15](#fig:glonProperties)), consistent with the increased presence of strong shocks in the bar. We also discuss a relationship between the calculated mass and cloud location in Section [5.5](#subsec:xfactor).

We find that all of the clouds likely to be in the bar are located on the nearside of the bar, at positive Galactic longitudes. This may be due to projection effects of the bar. At a bar angle of 30$^\circ$ (cite: wegg_structure_2015), a Galactic longitude of $-10^\circ$ along the bar major axis corresponds to a Galactocentric radius of nearly twice that of a Galactic longitude of $10^\circ$. In other words, the farside of the bar is contained within a much smaller longitude range: assuming a semimajor axis of 3.5 kpc, the bar extends 8.4$^\circ$ in the negative longitude direction but 16$^\circ$ in the positive longitude direction. Furthermore, the distance from the Sun to the farside of the bar is greater than that to the nearside of the bar: a cloud on the bar major axis at -5$^\circ$ would be about 2.5 kpc further than a cloud on the bar major axis at 5$^\circ$. The combination of these two projection effects may make observing clouds on the farside of the bar more difficult than clouds on the nearside of the bar.

## X-Factor in the Bar

![image](massComp.pdf) ![image](massRatio.pdf)

The mass estimates calculated using the equation of LTE (Eq. [\[eq:sioColDens\]](#eq:sioColDens)) and the integrated intensities of ^13^CO and C^18^O agree to within a factor of about 2-3, although there is one outlier for which it seems most of the C^18^O lies outside the extent of the cloud as defined by a 5$\sigma$ cutoff on the H~2~CO $J=3_{03} \to 2_{02}$. On the other hand, the mass calculated using the integrated intensity of ^12^CO and the typical Galactic X-factor of $2.3 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ is quite discrepant from the other two estimates, as seen in Figure [19](#fig:massComp). In particular, for the clouds most likely to be on the bar, the X-factor calculation significantly overestimates the mass compared to the LTE calculations, whereas the difference is smaller for the clouds not on the bar.

(cite: ferriere_spatial_2007) find the X-factor in the Galactic Center region to be lower than the typical Galactic value, on the order of $10^{19}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$. (cite: gramze_evidence_2023) find a similar value of $1.5 \times 10^{19}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ for G5, and conclude that the lower value extends beyond just the Galactic center, although they note that the special conditions of G5 may not be representative of the entire bar lane. Our findings provide further evidence that this reduced X-factor value does indeed extend along the Galactic bar, which is consistent with the dynamically disturbed nature of clouds on the bar. If we take the LTE mass estimate with ^13^CO to be more representative of the true cloud mass, then we can calculate an X-factor for each cloud in the bar, the average of which is $(1.59 \pm 0.5) \times 10^{19}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$, where the uncertainty is taken to simply be the standard deviation over the sample. This value is consistent with that calculated by (cite: gramze_evidence_2023) and indicates that the standard Galactic X-factor is an overestimate by 10-20 times in this region.

(cite: gramze_evidence_2023) suggest that this discrepancy is due to low optical depth, since the typical X-factor of $2.3 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ assumes optical thickness (cite: strong_radial_1988). We estimate the optical depth for each of the clouds using a root finding algorithm on the equation

$$\begin{equation}
\label{eq:opticalDepth}
\frac{I_\nu (^{12}\text{CO})}{I_\nu (^{13}\text{CO})} = \frac{1-e^{-\tau_{12}}}{1-e^{-\tau_{12}/\text{R}_\text{C}}},
\end{equation}$$ where $I_\nu$ is the integrated intensity of the line, $\tau_{12}$ is the optical depth of ^12^CO, and R~C~ is the ^12^C/^13^C isotope abundance ratio (Eq. [\[eq:cAbundance\]](#eq:cAbundance)). We use the average integrated intensity over a 1’ box centered on the pixel with maximum ^12^CO integrated intensity. The resulting optical depth values are shown in Table [\[table:opticalDepths\]](#table:opticalDepths).

| Cloud | $\tau_{12}$ (Eq. [\[eq:cAbundance\]](#eq:cAbundance)) | $\tau_{12}$ ($\text{R}_\text{C} = 40$) | Location |
|:--:|:--:|:--:|:--:|
| G008.67 | $24$ | $22$ | Out |
| G008.40 | $14$ | $16$ | Out |
| G006.92 | $14$ | $13$ | Out |
| G006.56 | $1.0$ | $3.2$ | In |
| G005.75 | $0.087$ | $2.1$ | In |
| G005.49 | $0.085$ | $1.8$ | In |
| G005.38 | $0.47$ | $2.7$ | In |
| G003.43 | $11$ | $9.1$ | Out |
| G003.09 | $0.78$ | $4.3$ | In |
| G003.02 | $0.35$ | $3.5$ | In |
| G002.96 | $0.097$ | $3.1$ | In |
| G002.51 | $1.9$ | $7.2$ | In |
| G001.93 | $0.11$ | $3.7$ | In |
| G358.48 | $20$ | $16$ | Out |
| G354.61 | $16$ | $16$ | Out |
| G353.41 | $32$ | $23$ | Out |
| G351.77 | $25$ | $18$ | Out |
| G351.58 | $12$ | $16$ | Out |
| G350.18 | $8.8$ | $14$ | Out |
| G350.10 | $12$ | $19$ | Out |

We see that the optical depths of the clouds on the bar are significantly lower than those not on the bar, and are mostly within the optically thin regime. Since the optical depth is strongly dependent on R~C~, we also perform the calculation assuming a constant R~C~ = 40 (cite: gramze_evidence_2023) to ensure that this difference is not only due to the large uncertainty of the dependence of R~C~ on the Galactocentric radius (Eq. [\[eq:cAbundance\]](#eq:cAbundance)). These are also shown in Table [\[table:opticalDepths\]](#table:opticalDepths). Although taking R~C~ = 40 increases the optical depths of the clouds in the bar, they are still all lower than those of the clouds outside the bar, and we note that the values using Eq. [\[eq:cAbundance\]](#eq:cAbundance) are likely more reflective of the actual optical depth. We thus conclude that the lower optical depth of the clouds on the bar are the likely cause of the reduced X-factor for these clouds, in agreement with (cite: gramze_evidence_2023). This gives further evidence that the X-factor in the bar region as a whole is lower than the typical Galactic value, and the previously reported values of the mass inflow rate into the CMZ (cite: sormani_mass_2019; hatchfield_dynamically_2021), which use the Galactic X-factor, are overestimates.

We previously noted that the masses estimated from the integrated intensities of ^13^CO and C^18^O agree to within a factor of about 2-3, excluding one outlier. Interestingly, we note that there are nine clouds for which the mass estimate from C^13^O is greater than that from ^18^CO, and these nine clouds are the clouds likely to be on the bar. Over these clouds (excluding the outlier for which $\text{M}_{\text{C}^{13}\text{O}}/\text{M}_{\text{C}^{18}\text{O}} = 19$), the average ratio is $\text{M}_{\text{C}^{13}\text{O}}/\text{M}_{\text{C}^{18}\text{O}} = 2$, whereas for the 11 clouds not on the bar, the average ratio is $\text{M}_{\text{C}^{13}\text{O}}/\text{M}_{\text{C}^{18}\text{O}} = 0.5$. One possible reason for this discrepancy is the uncertainty in location of the clouds, since, although the two mass estimates scale equivalently with distance, they are dependent in different ways on Galactocentric radius, as per the ^12^C/^13^C and ^16^O/^18^O isotope abundance ratios (Eqs. [\[eq:cAbundance\]](#eq:cAbundance) and [\[eq:oAbundance\]](#eq:oAbundance)). It may also be that these abundance ratios themselves do not apply to the clouds, or the Galactic bar region as a whole, in the same way as the typical Galactic X-factor does not apply.

# Conclusion

We observed the molecular lines SiO $J=5\to 4$, H~2~CO $J=3_{21} \to 2_{20}$, H~2~CO $J=3_{03} \to 2_{02}$, HC~3~N $J = 24 \to 23$, CH~3~OH $J = 4_{22} \to 3_{12}$, C^18^O $J = 2\to 1$, ^13^CO $J = 2\to 1$, ^12^CO $J = 2\to 1$, and H30$\alpha$ with the ALMA ACA for 20 clouds with Galactic longitudes $\lvert \ell \rvert < 10^\circ$ that are outside the CMZ. These clouds were selected from the HOPS survey, which covers velocities from -200 to 200 km s$^{-1}$ and Galactic latitudes $\lvert b \rvert < 5^\circ$, for their bright and broad NH~3~ (3,3) emission. These spectral lines and bands probe several important processes (e.g., (cite: schilke_sio_1997; meier_spatially_2005; ott_temperature_2005; calzetti_calibration_2007; ginsburg_dense_2016)), and we measure temperatures, shocks, turbulence, $\Sigma_\text{SFR}$, and masses for all the clouds. We also used observations of the metastable ammonia inversion transitions with $(J, K) = (1,1), (2,2), (3,3)$ and $(6,6)$ from HOPS to measure ammonia temperatures, as well as the 4.5, 8, and 24 $\mu$m bands from Spitzer as tracers of star formation.

We found that although the clouds do not share a velocity with the large-scale dust lanes feeding the CMZ, nine of them have similar properties to clouds that do have those velocities, such as high Mach numbers and ammonia temperatures. It is possible that these clouds are associated with the dust lanes but have been accelerated to velocities closer to zero by collisions. Of these clouds, most are associated with the known clumps G5 and B2, which may be sites of dust lane gas that has overshot the CMZ and is colliding with the dust lane on the opposite side (cite: fux_3d_1999; sormani_geometry_2019; gramze_evidence_2023), although at least two of the clouds that we expect to lie on the Galactic bar have not been previously studied in detail. Furthermore, we showed that turbulence in the clouds along the Galactic bar, possibly from high-velocity collisions, is inhibiting star formation, as all of the clouds with high turbulence are not star forming. Heating solely from turbulent pressure is sufficient to heat these clouds to their observed temperatures, whereas photoelectric heating is dominant in the star-forming clouds.

Simple modeling and calculations with RADEX, which assumes a single gas phase, suggests that all transitions are inconsistent with a single gas temperature and density. Different molecules appear to trace different gas phases in the molecular clouds. Ammonia appears to trace colder gas in the clouds, formaldehyde appears to trace warm gas, and SiO may be tracing shocked and hot gas, with each of these gas phases likely at a different density. A more detailed analysis that accounts for the complex, multiphase nature of the clouds can be carried out with further data, including observations of ammonia at comparable resolution.

We found that the typical (cite: strong_radial_1988) CO-to-H~2~ X-factor of $2.3 \times 10^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ significantly overestimates the mass of clouds in the bar, and that this overestimation is likely due to the lower optical thickness of the ^12^CO in these clouds compared to those outside the bar. We measured the average X-factor for these clouds to be $(1.59 \pm 0.5) \times 10^{19}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$, which is comparable to the value of $1.5 \times 10^{19}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ obtained by (cite: gramze_evidence_2023) from observations of the cloud G5, which they also find to have optically thin, or slightly optically thick, ^12^CO. (cite: gramze_evidence_2023) note that G5 may be not be representative of gas in the bar, but our findings suggest that this reduced X-factor indeed applies to the bar region as a whole, in which case previous measurements of the CMZ gas inflow rate (cite: sormani_mass_2019; hatchfield_dynamically_2021) are overestimates.

Our observations of clouds located in and out of the Galactic bar region highlight the dynamical activity of the Galactic bar outside of just the CMZ. Although some recent statistical surveys of barred galaxies suggest that star formation is environmentally independent and not lower in the bar region (e.g. (cite: muraoka_co_2019; diaz-garcia_molecular_2021; querejeta_stellar_2021)), we have shown that, in the Milky Way, turbulence and other extreme processes along the bar lane inflows, induced by the bar potential, suppress star formation, an observation that has been reported for both individual barred galaxies and statistical studies (e.g., (cite: tubbs_inhibition_1982; reynaud_kinematics_1998; james_stellar_2016; maeda_statistical_2023)). Our findings further provide evidence that molecular clouds acquire CMZ-like properties as they travel along the bar inflows, prior to reaching the CMZ itself. This transitional region of the Milky Way merits further study and observation as a link between the Galactic disk and the CMZ, and a deeper understanding of its dynamics can provide insight into the inner Galaxy as a whole.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.2.00068.S, ADS/JAO.ALMA#2021.2.00001.S,\
ADS/JAO.ALMA#2022.1.00591.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This research has made use of the NASA/IPAC Infrared Science Archive, which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology.

A.N. is a student at the National Radio Astronomy Observatory and was funded as a participant in the National Radio Astronomy Observatory Research Experience for Undergraduates Site, supported by the National Science Foundation under grant No. 1852401.

M.C.S. acknowledges financial support from the European Research Council under the ERC Starting Grant “GalFlow” (grant 101116226).

A.G. acknowledges support from the NSF under grants AAG 2206511 and CAREER 2142300.

R.S.K. acknowledges financial support from the European Research Council via the ERC Synergy Grant “ECOGAL” (project ID 855130), from the German Excellence Strategy via the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”, and from the German Ministry for Economic Affairs and Climate Action in project “MAINN” (funding ID 50OO2206). R.S.K. is grateful for computing resources provided by the Ministry of Science, Research and the Arts (MWK) of the State of Baden-Württemberg through bwHPC and the German Science Foundation (DFG) through grants INST 35/1134-1 FUGG and 35/1597-1 FUGG, and also for data storage at SDS@hd funded through grants INST 35/1314-1 FUGG and INST 35/1503-1 FUGG. R.S.K. also thanks the Harvard-Smithsonian Center for Astrophysics and the Radcliffe Institute for Advanced Studies for their hospitality during his sabbatical, and the 2024/25 Class of Radcliffe Fellows for highly interesting and stimulating discussions.

# Software

Python, IPython (cite: perez_ipython_2007), NumPy (cite: harris_array_2020), Matplotlib (cite: hunter_matplotlib_2007), SciPy (cite: virtanen_scipy_2020), Astropy (cite: the_astropy_collaboration_astropy_2022), `spectral-cube` (cite: ginsburg_radio-astro-toolsspectral-cube_2019), CASA (cite: the_casa_team_casa_2022), CARTA (cite: comrie_carta_2021), RADEX (cite: van_der_tak_computer_2007)

ALMA, IRSA

# Clouds in the Galactic Bar

As noted in Section [3](#sec:loc), for the clouds we assume to be in the Galactic bar, we calculate distances using the geometry of the bar and the Galactic longitudes of the clouds, assuming they lie along the Galactic bar’s major axis.

*G005.75, G005.49, and G005.38* are spatially associated with the cluster G5, which has observational evidence suggesting that it is the site of a cloud-cloud collision between the dust lane on the nearside of the Galaxy and gas that originated from the dust lane on the farside of the Galaxy and overshot the CMZ (cite: gramze_evidence_2023). The line-of-sight velocities of these three clouds are all consistent with that of G5, which (cite: gramze_evidence_2023) found to extend from as low as 0-200 km s$^{-1}$. We adopt geometric distances of 7.0 $\pm$ 1.0, 7.0 $\pm$ 1.0, and 7.1 $\pm$ 1.0 kpc for these three clouds, respectively.

*G003.09, G003.02, and G002.96* are spatially associated with the cluster B2, which has also been suggested to be a similar site of a collision between the dust lane and overshooting material from the other side, or gas accreting onto x~2~ orbits in the bar region (cite: sormani_geometry_2019). *G002.51* may also be associated with the same clump. Although the central velocities of these four clouds are not similar, B2 itself extends over a velocity range greater than 150 km s$^{-1}$ (cite: fux_3d_1999), so these clouds likely belong to B2 given their aforementioned broad lines. We adopt geometric distances of 7.5 $\pm$ 1.0 kpc for G003.09, G003.02, and G002.96, and 7.6 $\pm$ 1.0 kpc for G002.51.

*G006.56 and G001.93* are not associated with known clusters in the bar but still exhibit broad lines, so we consider them as likely to be in the bar. We adopt geometric distances of 6.9 $\pm$ 1.0 kpc and 7.7 $\pm$ 1.0 kpc for these two clouds, respectively.

# Temperature Error Maps

As mentioned in Section [4.1.1](#subsubsec:ammoniaTemp), we include the ammonia temperature error maps for each cloud in Figure [20](#fig:NH3tempError). Likewise, as mentioned in Section [4.1.2](#subsubsec:h2coTemp), we include the formaldehyde temperature error maps for each cloud in Figure [21](#fig:H2COtempError).

![](NH3_temperature_errors.pdf)

![](H2CO_temperature_errors.pdf)

# Velocity Gradient Fitting

To determine the velocity gradients of the clouds, we fit a plane of form

$$\begin{equation}
z = ax + by + c
\end{equation}$$ to the H~2~CO $(3_{03}-2_{02})$ intensity-weighted velocity (“moment 1”) map of each cloud, where $z$ is the velocity, $(x,y)$ are the sky pixel coordinates, and $(a,b,c)$ are fit constants. We take the velocity gradient magnitude to be $\text{d}v/\text{d}r = \sqrt{a^2 + b^2}$, which can be converted to units of kilometers per second per parsec using the distance to the cloud. We multiply this by the beam size in radians to estimate the contribution of bulk motion to the line width.

In Figure [22](#fig:velGrad), we show an example of the gradient fitting procedure for cloud G008.67.

![image](velocityGradientG00867.pdf) ![image](velocityGradientSubtractedG00867.pdf)

natexlab

(ref: abuter_geometric_2019) Abuter, R., Amorim, A., Bauböck, M., et al. 2019, Astronomy & Astrophysics, 625, L10, doi: [`10.1051/0004-6361/201935656`](http://doi.org/10.1051/0004-6361/201935656)

(ref: ao_thermal_2013) Ao, Y., Henkel, C., Menten, K. M., et al. 2013, Astronomy and Astrophysics, 550, A135, doi: [`10.1051/0004-6361/201220096`](http://doi.org/10.1051/0004-6361/201220096)

(ref: athanassoula_existence_1992) Athanassoula, E. 1992, Monthly Notices of the Royal Astronomical Society, 259, 345, doi: [`10.1093/mnras/259.2.345`](http://doi.org/10.1093/mnras/259.2.345)

(ref: baganoff_chandra_2003) Baganoff, F. K., Maeda, Y., Morris, M., et al. 2003, The Astrophysical Journal, 591, 891, doi: [`10.1086/375145`](http://doi.org/10.1086/375145)

(ref: balser_discovery_2021) Balser, D. S., Wenger, T. V., Anderson, L. D., et al. 2021, The Astrophysical Journal, 921, 176, doi: [`10.3847/1538-4357/ac1db3`](http://doi.org/10.3847/1538-4357/ac1db3)

(ref: bania_clump_1986) Bania, T. M., Stark, A. A., & Heiligman, G. M. 1986, The Astrophysical Journal, 307, 350, doi: [`10.1086/164422`](http://doi.org/10.1086/164422)

(ref: barnes_star_2017) Barnes, A. T., Longmore, S. N., Battersby, C., et al. 2017, Monthly Notices of the Royal Astronomical Society, 469, 2263, doi: [`10.1093/mnras/stx941`](http://doi.org/10.1093/mnras/stx941)

(ref: bendo_tests_2017) Bendo, G. J., Miura, R. E., Espada, D., et al. 2017, Monthly Notices of the Royal Astronomical Society, 472, 1239, doi: [`10.1093/mnras/stx1837`](http://doi.org/10.1093/mnras/stx1837)

(ref: bergin_postshock_1998) Bergin, E. A., Melnick, G. J., & Neufeld, D. A. 1998, The Astrophysical Journal, 499, 777, doi: [`10.1086/305656`](http://doi.org/10.1086/305656)

(ref: binney_understanding_1991) Binney, J., Gerhard, O. E., Stark, A. A., Bally, J., & Uchida, K. I. 1991, Monthly Notices of the Royal Astronomical Society, 252, 210, doi: [`10.1093/mnras/252.2.210`](http://doi.org/10.1093/mnras/252.2.210)

(ref: bitran_large_1997) Bitran, M., Alvarez, H., Bronfman, L., May, J., & Thaddeus, P. 1997, Astronomy and Astrophysics Supplement Series, 125, 99, doi: [`10.1051/aas:1997214`](http://doi.org/10.1051/aas:1997214)

(ref: bland-hawthorn_galaxy_2016) Bland-Hawthorn, J., & Gerhard, O. 2016, Annual Review of Astronomy and Astrophysics, 54, 529, doi: [`10.1146/annurev-astro-081915-023441`](http://doi.org/10.1146/annurev-astro-081915-023441)

(ref: burgh_direct_2007) Burgh, E. B., France, K., & McCandliss, S. R. 2007, The Astrophysical Journal, 658, 446, doi: [`10.1086/511259`](http://doi.org/10.1086/511259)

(ref: busch_living_2022) Busch, L. A., Riquelme, D., Güsten, R., et al. 2022, Astronomy & Astrophysics, 668, A183, doi: [`10.1051/0004-6361/202244870`](http://doi.org/10.1051/0004-6361/202244870)

(ref: calzetti_calibration_2007) Calzetti, D., Kennicutt, R. C., Engelbracht, C. W., et al. 2007, The Astrophysical Journal, 666, 870, doi: [`10.1086/520082`](http://doi.org/10.1086/520082)

(ref: carey_mipsgal_2009) Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, Publications of the Astronomical Society of the Pacific, 121, 76, doi: [`10.1086/596581`](http://doi.org/10.1086/596581)

(ref: caswell_southern_1987) Caswell, J. L., & Haynes, R. F. 1987, Astronomy and Astrophysics, 171, 261. <https://ui.adsabs.harvard.edu/abs/1987A&A...171..261C>

(ref: churchwell_spitzerglimpse_2009) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, Publications of the Astronomical Society of the Pacific, 121, 213, doi: [`10.1086/597811`](http://doi.org/10.1086/597811)

(ref: comrie_carta_2021) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA: The Cube Analysis and Rendering Tool for Astronomy, Zenodo, doi: [`10.5281/zenodo.4905459`](http://doi.org/10.5281/zenodo.4905459)

(ref: contopoulos_orbits_1989) Contopoulos, G., & Grosbøl, P. 1989, The Astronomy and Astrophysics Review, 1, 261, doi: [`10.1007/BF00873080`](http://doi.org/10.1007/BF00873080)

(ref: diaz-garcia_molecular_2021) Díaz-García, S., Lisenfeld, U., Pérez, I., et al. 2021, Astronomy and Astrophysics, 654, A135, doi: [`10.1051/0004-6361/202140674`](http://doi.org/10.1051/0004-6361/202140674)

(ref: fazio_infrared_2004) Fazio, G. G., Hora, J. L., Allen, L. E., et al. 2004, The Astrophysical Journal Supplement Series, 154, 10, doi: [`10.1086/422843`](http://doi.org/10.1086/422843)

(ref: faundez_simba_2004) Faúndez, S., Bronfman, L., Garay, G., et al. 2004, Astronomy and Astrophysics, 426, 97, doi: [`10.1051/0004-6361:20035755`](http://doi.org/10.1051/0004-6361:20035755)

(ref: federrath_link_2016) Federrath, C., Rathborne, J. M., Longmore, S. N., et al. 2016, The Astrophysical Journal, 832, 143, doi: [`10.3847/0004-637X/832/2/143`](http://doi.org/10.3847/0004-637X/832/2/143)

(ref: ferriere_spatial_2007) Ferrière, K., Gillard, W., & Jean, P. 2007, Astronomy and Astrophysics, 467, 611, doi: [`10.1051/0004-6361:20066992`](http://doi.org/10.1051/0004-6361:20066992)

(ref: fux_3d_1999) Fux, R. 1999, Astronomy and Astrophysics, 345, 787, doi: [`10.48550/arXiv.astro-ph/9903154`](http://doi.org/10.48550/arXiv.astro-ph/9903154)

(ref: gaia_collaboration_gaia_2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, Astronomy and Astrophysics, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: gaia_collaboration_gaia_2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, Astronomy and Astrophysics, 674, A1, doi: [`10.1051/0004-6361/202243940`](http://doi.org/10.1051/0004-6361/202243940)

(ref: garay_silicon_2000) Garay, G., Mardones, D., & Rodríguez, L. F. 2000, The Astrophysical Journal, 545, 861, doi: [`10.1086/317853`](http://doi.org/10.1086/317853)

(ref: ginsburg_dense_2016) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, Astronomy & Astrophysics, 586, A50, doi: [`10.1051/0004-6361/201526100`](http://doi.org/10.1051/0004-6361/201526100)

(ref: ginsburg_radio-astro-toolsspectral-cube_2019) Ginsburg, A., Koch, E., Robitaille, T., et al. 2019, radio-astro-tools/spectral-cube: Release v0.4.5, Zenodo, doi: [`10.5281/zenodo.3558614`](http://doi.org/10.5281/zenodo.3558614)

(ref: glimpse_team_galactic_2020) GLIMPSE Team. 2020, Galactic Legacy Infrared Midplane Survey Extraordinaire, IPAC, doi: [`10.26131/IRSA405`](http://doi.org/10.26131/IRSA405)

(ref: goto_absorption_2008) Goto, M., Usuda, T., Nagata, T., et al. 2008, The Astrophysical Journal, 688, 306, doi: [`10.1086/591657`](http://doi.org/10.1086/591657)

(ref: gramze_evidence_2023) Gramze, S. R., Ginsburg, A., Meier, D. S., et al. 2023, The Astrophysical Journal, 959, 93, doi: [`10.3847/1538-4357/ad01be`](http://doi.org/10.3847/1538-4357/ad01be)

(ref: green_distances_2011) Green, J. A., & McClure-Griffiths, N. M. 2011, Monthly Notices of the Royal Astronomical Society, 417, 2500, doi: [`10.1111/j.1365-2966.2011.19418.x`](http://doi.org/10.1111/j.1365-2966.2011.19418.x)

(ref: harris_array_2020) Harris, C. R., Millman, K. J., Van Der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: hatchfield_dynamically_2021) Hatchfield, H. P., Sormani, M. C., Tress, R. G., et al. 2021, The Astrophysical Journal, 922, 79, doi: [`10.3847/1538-4357/ac1e89`](http://doi.org/10.3847/1538-4357/ac1e89)

(ref: henkel_dense_2000) Henkel, C., Mauersberger, R., Peck, A. B., Falcke, H., & Hagiwara, Y. 2000, Astronomy and Astrophysics, 361, L45, doi: [`10.48550/arXiv.astro-ph/0010519`](http://doi.org/10.48550/arXiv.astro-ph/0010519)

(ref: henshaw_star_2023) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, 534, 83, doi: [`10.48550/arXiv.2203.11223`](http://doi.org/10.48550/arXiv.2203.11223)

(ref: henshaw_molecular_2016) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, Monthly Notices of the Royal Astronomical Society, 457, 2675, doi: [`10.1093/mnras/stw121`](http://doi.org/10.1093/mnras/stw121)

(ref: henshaw_brick_2019) Henshaw, J. D., Ginsburg, A., Haworth, T. J., et al. 2019, Monthly Notices of the Royal Astronomical Society, 485, 2457, doi: [`10.1093/mnras/stz471`](http://doi.org/10.1093/mnras/stz471)

(ref: hiraoka_formation_1994) Hiraoka, K., Ohashi, N., Kihara, Y., et al. 1994, Chemical Physics Letters, 229, 408, doi: [`10.1016/0009-2614(94)01066-8`](http://doi.org/10.1016/0009-2614(94)01066-8)

(ref: hogerheijde_millimeter_1995) Hogerheijde, M. R., Jansen, D. J., & van Dishoeck, E. F. 1995, Astronomy and Astrophysics, 294, 792. <https://ui.adsabs.harvard.edu/abs/1995A&A...294..792H>

(ref: huettemeister_multilevel_1995) Huettemeister, S., Wilson, T. L., Mauersberger, R., et al. 1995, Astronomy and Astrophysics, 294, 667. <https://ui.adsabs.harvard.edu/abs/1995A&A...294..667H>

(ref: hunt_size-density_2009) Hunt, L. K., & Hirashita, H. 2009, Astronomy and Astrophysics, 507, 1327, doi: [`10.1051/0004-6361/200912020`](http://doi.org/10.1051/0004-6361/200912020)

(ref: hunter_matplotlib_2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: indriolo_herschel_2015) Indriolo, N., Neufeld, D. A., Gerin, M., et al. 2015, The Astrophysical Journal, 800, 40, doi: [`10.1088/0004-637X/800/1/40`](http://doi.org/10.1088/0004-637X/800/1/40)

(ref: james_stellar_2016) James, P. A., & Percival, S. M. 2016, Monthly Notices of the Royal Astronomical Society, 457, 917, doi: [`10.1093/mnras/stv2978`](http://doi.org/10.1093/mnras/stv2978)

(ref: jones_h_2013) Jones, C., Dickey, J. M., Dawson, J. R., et al. 2013, The Astrophysical Journal, 774, 117, doi: [`10.1088/0004-637X/774/2/117`](http://doi.org/10.1088/0004-637X/774/2/117)

(ref: jones_spectral_2012) Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2012, Monthly Notices of the Royal Astronomical Society, 419, 2961, doi: [`10.1111/j.1365-2966.2011.19941.x`](http://doi.org/10.1111/j.1365-2966.2011.19941.x)

(ref: kauffmann_mambo_2008) Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, II, N. J., & Lee, C. W. 2008, Astronomy and Astrophysics, 487, 993, doi: [`10.1051/0004-6361:200809481`](http://doi.org/10.1051/0004-6361:200809481)

(ref: kauffmann_galactic_2017) Kauffmann, J., Pillai, T., Zhang, Q., et al. 2017, Astronomy & Astrophysics, 603, A89, doi: [`10.1051/0004-6361/201628088`](http://doi.org/10.1051/0004-6361/201628088)

(ref: keto_early_2008) Keto, E., Zhang, Q., & Kurtz, S. 2008, The Astrophysical Journal, 672, 423, doi: [`10.1086/522570`](http://doi.org/10.1086/522570)

(ref: kim_radio_2001) Kim, K.-T., & Koo, B.-C. 2001, The Astrophysical Journal, 549, 979, doi: [`10.1086/319447`](http://doi.org/10.1086/319447)

(ref: kim_new_2018) Kim, W. J., Urquhart, J. S., Wyrowski, F., Menten, K. M., & Csengeri, T. 2018, Astronomy and Astrophysics, 616, A107, doi: [`10.1051/0004-6361/201732330`](http://doi.org/10.1051/0004-6361/201732330)

(ref: kruijssen_what_2014) Kruijssen, J. M. D., Longmore, S. N., Elmegreen, B. G., et al. 2014, Monthly Notices of the Royal Astronomical Society, 440, 3370, doi: [`10.1093/mnras/stu494`](http://doi.org/10.1093/mnras/stu494)

(ref: lacy_detection_1994) Lacy, J. H., Knacke, R., Geballe, T. R., & Tokunaga, A. T. 1994, The Astrophysical Journal, 428, L69, doi: [`10.1086/187395`](http://doi.org/10.1086/187395)

(ref: langer_12c_1990) Langer, W. D., & Penzias, A. A. 1990, The Astrophysical Journal, 357, 477, doi: [`10.1086/168935`](http://doi.org/10.1086/168935)

(ref: larson_turbulence_1981) Larson, R. B. 1981, Monthly Notices of the Royal Astronomical Society, 194, 809, doi: [`10.1093/mnras/194.4.809`](http://doi.org/10.1093/mnras/194.4.809)

(ref: leitherer_starburst99_1999) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, The Astrophysical Journal Supplement Series, 123, 3, doi: [`10.1086/313233`](http://doi.org/10.1086/313233)

(ref: leroy_heracles_2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, The Astronomical Journal, 137, 4670, doi: [`10.1088/0004-6256/137/6/4670`](http://doi.org/10.1088/0004-6256/137/6/4670)

(ref: li_gas_2016) Li, Z., Gerhard, O., Shen, J., Portail, M., & Wegg, C. 2016, The Astrophysical Journal, 824, 13, doi: [`10.3847/0004-637X/824/1/13`](http://doi.org/10.3847/0004-637X/824/1/13)

(ref: liszt_molecular_2006) Liszt, H. S. 2006, Astronomy and Astrophysics, 447, 533, doi: [`10.1051/0004-6361:20054070`](http://doi.org/10.1051/0004-6361:20054070)

(ref: liu_atoms_2020) Liu, T., Evans, N. J., Kim, K.-T., et al. 2020, Monthly Notices of the Royal Astronomical Society, 496, 2790, doi: [`10.1093/mnras/staa1577`](http://doi.org/10.1093/mnras/staa1577)

(ref: longmore_variations_2013) Longmore, S. N., Bally, J., Testi, L., et al. 2013, Monthly Notices of the Royal Astronomical Society, 429, 987, doi: [`10.1093/mnras/sts376`](http://doi.org/10.1093/mnras/sts376)

(ref: longmore_h2o_2017) Longmore, S. N., Walsh, A. J., Purcell, C. R., et al. 2017, Monthly Notices of the Royal Astronomical Society, 470, 1462, doi: [`10.1093/mnras/stx1226`](http://doi.org/10.1093/mnras/stx1226)

(ref: lowry_manson_millimeter_1977) Lowry Manson, E., Clark, W. W., De Lucia, F. C., & Gordy, W. 1977, Physical Review A, 15, 223, doi: [`10.1103/PhysRevA.15.223`](http://doi.org/10.1103/PhysRevA.15.223)

(ref: lucey_dynamically_2023) Lucey, M., Pearson, S., Hunt, J. A. S., et al. 2023, Monthly Notices of the Royal Astronomical Society, 520, 4779, doi: [`10.1093/mnras/stad406`](http://doi.org/10.1093/mnras/stad406)

(ref: mac_low_control_2004) Mac Low, M.-M., & Klessen, R. S. 2004, Reviews of Modern Physics, 76, 125, doi: [`10.1103/RevModPhys.76.125`](http://doi.org/10.1103/RevModPhys.76.125)

(ref: maeda_statistical_2023) Maeda, F., Egusa, F., Ohta, K., Fujimoto, Y., & Habe, A. 2023, The Astrophysical Journal, 943, 7, doi: [`10.3847/1538-4357/aca664`](http://doi.org/10.3847/1538-4357/aca664)

(ref: mangum_how_2015) Mangum, J. G., & Shirley, Y. L. 2015, Publications of the Astronomical Society of the Pacific, 127, 266, doi: [`10.1086/680323`](http://doi.org/10.1086/680323)

(ref: mangum_formaldehyde_1993) Mangum, J. G., & Wootten, A. 1993, The Astrophysical Journal Supplement Series, 89, 123, doi: [`10.1086/191841`](http://doi.org/10.1086/191841)

(ref: marshall_large_2008) Marshall, D. J., Fux, R., Robin, A. C., & Reylé, C. 2008, Astronomy and Astrophysics, 477, L21, doi: [`10.1051/0004-6361:20078967`](http://doi.org/10.1051/0004-6361:20078967)

(ref: martin-pintado_sio_1992) Martin-Pintado, J., Bachiller, R., & Fuente, A. 1992, Astronomy and Astrophysics, 254, 315. <https://ui.adsabs.harvard.edu/abs/1992A&A...254..315M>

(ref: martins_new_2005) Martins, F., Schaerer, D., & Hillier, D. J. 2005, Astronomy and Astrophysics, 436, 1049, doi: [`10.1051/0004-6361:20042386`](http://doi.org/10.1051/0004-6361:20042386)

(ref: meier_molecular_2001) Meier, D. S., & Turner, J. L. 2001, The Astrophysical Journal, 551, 687, doi: [`10.1086/320243`](http://doi.org/10.1086/320243)

(ref: meier_spatially_2005) —. 2005, The Astrophysical Journal, 618, 259, doi: [`10.1086/426499`](http://doi.org/10.1086/426499)

(ref: meier_spatially_2014) Meier, D. S., Turner, J. L., & Beck, S. C. 2014, The Astrophysical Journal, 795, 107, doi: [`10.1088/0004-637X/795/2/107`](http://doi.org/10.1088/0004-637X/795/2/107)

(ref: meier_nuclear_2008) Meier, D. S., Turner, J. L., & Hurt, R. L. 2008, The Astrophysical Journal, 675, 281, doi: [`10.1086/524932`](http://doi.org/10.1086/524932)

(ref: meier_cyanoacetylene_2011) Meier, D. S., Turner, J. L., & Schinnerer, E. 2011, The Astronomical Journal, 142, 32, doi: [`10.1088/0004-6256/142/1/32`](http://doi.org/10.1088/0004-6256/142/1/32)

(ref: mills_dense_2018) Mills, E. A. C., Ginsburg, A., Immer, K., et al. 2018, The Astrophysical Journal, 868, 7, doi: [`10.3847/1538-4357/aae581`](http://doi.org/10.3847/1538-4357/aae581)

(ref: mipsgal_team_24_2020) MIPSGAL Team. 2020, A 24 and 70 Micron Survey of the Inner Galactic Disk with MIPS, IPAC, doi: [`10.26131/IRSA435`](http://doi.org/10.26131/IRSA435)

(ref: mizuno_processing_2008) Mizuno, D. R., Carey, S. J., Noriega-Crespo, A., et al. 2008, Publications of the Astronomical Society of the Pacific, 120, 1028, doi: [`10.1086/591809`](http://doi.org/10.1086/591809)

(ref: morris_galactic_1996) Morris, M., & Serabyn, E. 1996, Annual Review of Astronomy and Astrophysics, 34, 645, doi: [`10.1146/annurev.astro.34.1.645`](http://doi.org/10.1146/annurev.astro.34.1.645)

(ref: motte_alma-imf_2022) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, Astronomy & Astrophysics, 662, A8, doi: [`10.1051/0004-6361/202141677`](http://doi.org/10.1051/0004-6361/202141677)

(ref: muno_diffuse_2004) Muno, M. P., Baganoff, F. K., Bautz, M. W., et al. 2004, The Astrophysical Journal, 613, 326, doi: [`10.1086/422865`](http://doi.org/10.1086/422865)

(ref: muraoka_co_2019) Muraoka, K., Sorai, K., Miyamoto, Y., et al. 2019, Publications of the Astronomical Society of Japan, 71, S15, doi: [`10.1093/pasj/psz015`](http://doi.org/10.1093/pasj/psz015)

(ref: murphy_calibrating_2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, The Astrophysical Journal, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: nandakumar_star-forming_2016) Nandakumar, G., Veena, V. S., Vig, S., et al. 2016, The Astronomical Journal, 152, 146, doi: [`10.3847/0004-6256/152/5/146`](http://doi.org/10.3847/0004-6256/152/5/146)

(ref: oka_central_2019) Oka, T., Geballe, T. R., Goto, M., et al. 2019, The Astrophysical Journal, 883, 54, doi: [`10.3847/1538-4357/ab3647`](http://doi.org/10.3847/1538-4357/ab3647)

(ref: oka_hot_2005) Oka, T., Geballe, T. R., Goto, M., Usuda, T., & McCall, B. J. 2005, The Astrophysical Journal, 632, 882, doi: [`10.1086/432679`](http://doi.org/10.1086/432679)

(ref: ott_temperature_2005) Ott, J., Weiss, A., Henkel, C., & Walter, F. 2005, The Astrophysical Journal, 629, 767, doi: [`10.1086/431661`](http://doi.org/10.1086/431661)

(ref: peeters_iso_2002) Peeters, E., Martín-Hernández, N. L., Damour, F., et al. 2002, Astronomy and Astrophysics, 381, 571, doi: [`10.1051/0004-6361:20011516`](http://doi.org/10.1051/0004-6361:20011516)

(ref: perez_ipython_2007) Perez, F., & Granger, B. E. 2007, Computing in Science & Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: potapov_formation_2017) Potapov, A., Jäger, C., Henning, T., Jonusas, M., & Krim, L. 2017, The Astrophysical Journal, 846, 131, doi: [`10.3847/1538-4357/aa85e8`](http://doi.org/10.3847/1538-4357/aa85e8)

(ref: purcell_h2o_2012) Purcell, C. R., Longmore, S. N., Walsh, A. J., et al. 2012, Monthly Notices of the Royal Astronomical Society, 426, 1972, doi: [`10.1111/j.1365-2966.2012.21800.x`](http://doi.org/10.1111/j.1365-2966.2012.21800.x)

(ref: queiroz_milky_2021) Queiroz, A. B. A., Chiappini, C., Perez-Villegas, A., et al. 2021, Astronomy & Astrophysics, 656, A156, doi: [`10.1051/0004-6361/202039030`](http://doi.org/10.1051/0004-6361/202039030)

(ref: querejeta_stellar_2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, Astronomy and Astrophysics, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: quireza_radio_2006) Quireza, C., Rood, R. T., Balser, D. S., & Bania, T. M. 2006a, The Astrophysical Journal Supplement Series, 165, 338, doi: [`10.1086/503901`](http://doi.org/10.1086/503901)

(ref: quireza_electron_2006) Quireza, C., Rood, R. T., Bania, T. M., Balser, D. S., & Maciel, W. J. 2006b, The Astrophysical Journal, 653, 1226, doi: [`10.1086/508803`](http://doi.org/10.1086/508803)

(ref: raymonda_electric_1970) Raymonda, J. W., Muenter, J. S., & Klemperer, W. A. 1970, Journal of Chemical Physics, 52, 3458, doi: [`10.1063/1.1673510`](http://doi.org/10.1063/1.1673510)

(ref: reid_trigonometric_2014) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, The Astrophysical Journal, 783, 130, doi: [`10.1088/0004-637X/783/2/130`](http://doi.org/10.1088/0004-637X/783/2/130)

(ref: reyes-reyes_benchmarking_2024) Reyes-Reyes, S. D., Stutz, A. M., Megeath, S. T., et al. 2024, Monthly Notices of the Royal Astronomical Society, 529, 2220, doi: [`10.1093/mnras/stae631`](http://doi.org/10.1093/mnras/stae631)

(ref: reynaud_kinematics_1998) Reynaud, D., & Downes, D. 1998, Astronomy and Astrophysics, 337, 671. <https://ui.adsabs.harvard.edu/abs/1998A&A...337..671R>

(ref: rieke_multiband_2004) Rieke, G. H., Young, E. T., Engelbracht, C. W., et al. 2004, The Astrophysical Journal Supplement Series, 154, 25, doi: [`10.1086/422717`](http://doi.org/10.1086/422717)

(ref: rivera-soto_recombination_2020) Rivera-Soto, R., Galván-Madrid, R., Ginsburg, A., & Kurtz, S. 2020, The Astrophysical Journal, 899, 94, doi: [`10.3847/1538-4357/aba749`](http://doi.org/10.3847/1538-4357/aba749)

(ref: saito_merger-induced_2017) Saito, T., Iono, D., Espada, D., et al. 2017, The Astrophysical Journal, 834, 6, doi: [`10.3847/1538-4357/834/1/6`](http://doi.org/10.3847/1538-4357/834/1/6)

(ref: schilke_sio_1997) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, Astronomy and Astrophysics, 321, 293. <https://ui.adsabs.harvard.edu/abs/1997A&A...321..293S>

(ref: scoville_submillimeter_2013) Scoville, N., & Murchikova, L. 2013, The Astrophysical Journal, 779, 75, doi: [`10.1088/0004-637X/779/1/75`](http://doi.org/10.1088/0004-637X/779/1/75)

(ref: shirley_critical_2015) Shirley, Y. L. 2015, Publications of the Astronomical Society of the Pacific, 127, 299, doi: [`10.1086/680342`](http://doi.org/10.1086/680342)

(ref: sormani_mass_2019) Sormani, M. C., & Barnes, A. T. 2019, Monthly Notices of the Royal Astronomical Society, 484, 1213, doi: [`10.1093/mnras/stz046`](http://doi.org/10.1093/mnras/stz046)

(ref: sormani_gas_2015) Sormani, M. C., Binney, J., & Magorrian, J. 2015, Monthly Notices of the Royal Astronomical Society, 449, 2421, doi: [`10.1093/mnras/stv441`](http://doi.org/10.1093/mnras/stv441)

(ref: sormani_stellar_2022) Sormani, M. C., Gerhard, O., Portail, M., Vasiliev, E., & Clarke, J. 2022, Monthly Notices of the Royal Astronomical Society, 514, L1, doi: [`10.1093/mnrasl/slac046`](http://doi.org/10.1093/mnrasl/slac046)

(ref: sormani_geometry_2019) Sormani, M. C., Treß, R. G., Glover, S. C. O., et al. 2019, Monthly Notices of the Royal Astronomical Society, 488, 4663, doi: [`10.1093/mnras/stz2054`](http://doi.org/10.1093/mnras/stz2054)

(ref: stark_clump_1986) Stark, A. A., & Bania, T. M. 1986, The Astrophysical Journal, 306, L17, doi: [`10.1086/184695`](http://doi.org/10.1086/184695)

(ref: storey_recombination_1995) Storey, P. J., & Hummer, D. G. 1995, Monthly Notices of the Royal Astronomical Society, 272, 41, doi: [`10.1093/mnras/272.1.41`](http://doi.org/10.1093/mnras/272.1.41)

(ref: strong_radial_1988) Strong, A. W., Bloemen, J. B. G. M., Dame, T. M., et al. 1988, Astronomy and Astrophysics, 207, 1. <https://ui.adsabs.harvard.edu/abs/1988A&A...207....1S>

(ref: syed_atomic_2020) Syed, J., Wang, Y., Beuther, H., et al. 2020, Astronomy & Astrophysics, 642, A68, doi: [`10.1051/0004-6361/202038449`](http://doi.org/10.1051/0004-6361/202038449)

(ref: tang_kinetic_2018) Tang, X. D., Henkel, C., Menten, K. M., et al. 2018, Astronomy & Astrophysics, 609, A16, doi: [`10.1051/0004-6361/201731849`](http://doi.org/10.1051/0004-6361/201731849)

(ref: the_astropy_collaboration_astropy_2022) The Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, The Astrophysical Journal, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: the_casa_team_casa_2022) The CASA Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: tsuboi_central_2015) Tsuboi, M., Miyazaki, A., & Uehara, K. 2015, Publications of the Astronomical Society of Japan, 67, 90, doi: [`10.1093/pasj/psv058`](http://doi.org/10.1093/pasj/psv058)

(ref: tubbs_inhibition_1982) Tubbs, A. D. 1982, \\apj, 255, 458, doi: [`10.1086/159846`](http://doi.org/10.1086/159846)

(ref: urquhart_characterisation_2010) Urquhart, J. S., Hoare, M. G., Purcell, C. R., et al. 2010, Publications of the Astronomical Society of Australia, 27, 321, doi: [`10.1071/AS10002`](http://doi.org/10.1071/AS10002)

(ref: urquhart_atlasgal_2018) Urquhart, J. S., König, C., Giannetti, A., et al. 2018, Monthly Notices of the Royal Astronomical Society, 473, 1059, doi: [`10.1093/mnras/stx2258`](http://doi.org/10.1093/mnras/stx2258)

(ref: van_der_tak_computer_2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & Dishoeck, E. F. v. 2007, Astronomy & Astrophysics, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: vera_effect_2016) Vera, M., Alonso, S., & Coldwell, G. 2016, Astronomy and Astrophysics, 595, A63, doi: [`10.1051/0004-6361/201628750`](http://doi.org/10.1051/0004-6361/201628750)

(ref: virtanen_scipy_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: walsh_h2o_2011) Walsh, A. J., Breen, S. L., Britton, T., et al. 2011, Monthly Notices of the Royal Astronomical Society, 416, 1764, doi: [`10.1111/j.1365-2966.2011.19115.x`](http://doi.org/10.1111/j.1365-2966.2011.19115.x)

(ref: wang_role_2024) Wang, C., Wang, K., Xu, F.-W., et al. 2024, Astronomy and Astrophysics, 681, A51, doi: [`10.1051/0004-6361/202347024`](http://doi.org/10.1051/0004-6361/202347024)

(ref: watanabe_efficient_2002) Watanabe, N., & Kouchi, A. 2002, The Astrophysical Journal, 571, L173, doi: [`10.1086/341412`](http://doi.org/10.1086/341412)

(ref: wegg_structure_2015) Wegg, C., Gerhard, O., & Portail, M. 2015, Monthly Notices of the Royal Astronomical Society, 450, 4050, doi: [`10.1093/mnras/stv745`](http://doi.org/10.1093/mnras/stv745)

(ref: wilson_abundances_1994) Wilson, T. L., & Rood, R. 1994, Annual Review of Astronomy and Astrophysics, 32, 191, doi: [`10.1146/annurev.aa.32.090194.001203`](http://doi.org/10.1146/annurev.aa.32.090194.001203)

(ref: wootten_molecular_1978) Wootten, A., Evans, II, N. J., Snell, R., & vanden Bout, P. 1978, The Astrophysical Journal, 225, L143, doi: [`10.1086/182813`](http://doi.org/10.1086/182813)

(ref: yang_sedigism_2022) Yang, A. Y., Urquhart, J. S., Wyrowski, F., et al. 2022, Astronomy & Astrophysics, 658, A160, doi: [`10.1051/0004-6361/202142039`](http://doi.org/10.1051/0004-6361/202142039)

(ref: yang_fermi-lat_2015) Yang, R.-z., Jones, D. I., & Aharonian, F. 2015, Astronomy and Astrophysics, 580, A90, doi: [`10.1051/0004-6361/201425233`](http://doi.org/10.1051/0004-6361/201425233)

(ref: yuasa_suzaku_2008) Yuasa, T., Tamura, K.-I., Nakazawa, K., et al. 2008, Publications of the Astronomical Society of Japan, 60, S207, doi: [`10.1093/pasj/60.sp1.S207`](http://doi.org/10.1093/pasj/60.sp1.S207)

(ref: yun_turbulent_2021) Yun, H.-S., Lee, J.-E., Evans, N. J., et al. 2021, The Astrophysical Journal, 921, 31, doi: [`10.3847/1538-4357/ac193e`](http://doi.org/10.3847/1538-4357/ac193e)

(ref: yusef-zadeh_cosmic-ray_2007) Yusef-Zadeh, F., Wardle, M., & Roy, S. 2007, The Astrophysical Journal, 665, L123, doi: [`10.1086/521359`](http://doi.org/10.1086/521359)

[^1]: <https://github.com/radio-astro-tools/pvextractor>

[^2]: <https://github.com/radio-astro-tools/spectral-cube>

[^3]: <https://github.com/astropy/reproject>

[^4]: Values for $\mu$ and $B$ for CO taken from <https://spec.jpl.nasa.gov/>

</paper>

Write the methods card for this paper.