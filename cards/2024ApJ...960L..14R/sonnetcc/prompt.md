# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...960L..14R\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...960L..14R",
 "title": "A Radio Counterpart to a Jupiter-mass Binary Object in Orion",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Rodríguez, Luis F.",
 "n_authors": 3,
 "arxiv_id": "2401.04905",
 "doi": "10.3847/2041-8213/ad18ac",
 "alma_projects_linked_by_archive": [
  "2013.1.00546.S",
  "2015.1.00262.S",
  "2015.1.00534.S",
  "2015.1.00669.S",
  "2017.1.01353.S",
  "2017.1.01639.S",
  "2018.1.01107.S"
 ]
}
```

Paper text:
<paper>
# A Radio Counterpart to a Jupiter-Mass Binary Object in Orion

## Abstract

Using James Webb Space Telescope near-infrared data of the inner Orion Nebula, (cite: Pearson_McCaughrean_2023) detected 40 Jupiter-Mass Binary Objects (JuMBOS). These systems are not associated with stars and their components have masses of giant Jupiter-like planets and separations in the plane of the sky of order $\sim$100 au. The existence of these wide free-floating planetary mass binaries was unexpected in our current theories of star and planet formation. Here we report the radio continuum (6.1 and 10.0 GHz) Karl G. Jansky Very Large Array detection of a counterpart to JuMBO 24. The radio emission appears to be steady at a level of $\sim$50 $\mu$Jy over timescales of days and years. We set an upper limit of $\simeq15$ km s$^{-1}$ to the velocity of the radio source in the plane of the sky. As in the near-infrared, the radio emission seems to be coming from both components of the binary.

# Introduction

In a new James Webb Space Telescope (JWST) near-infrared survey of the inner Orion Nebula and Trapezium Cluster, (cite: Pearson_McCaughrean_2023) detected 40 Jupiter- Mass Binary Objects (JuMBOS). Additionally, two triple objects were reported. These multiple systems are not associated to stars and their components have masses in the range of 0.6 to 14 Jupiter masses and separations in the plane of the sky between 28 and 384 au (0.07 and 0.99 arcsec at a distance of 388 pc; (cite: Kounkel+2017)). The existence of these wide planetary-mass binaries is surprising since our current knowledge of star and planet formation cannot account for them. A possible theoretical explanation has been offered by (cite: Wang+2023) in terms of an ejection after a close stellar flyby between two solar-like stars. Rogue planets (single planets not gravitationally bound to any star or brown dwarf, also known as free-floating or orphan planets) have been detected in the optical and near-infrared (cite: Lucas_Roche_2000; ZapateroOsorio+2000). This latter class of single sources, however, is compatible with the known physical conditions of forming stellar and planetary systems (cite: Hurley_Shara_2002; Kroupa_Bouvier_2003; Whitworth_Zinnecker_2004; MiretRoig2023). We have searched for radio counterparts to the 42 JuMBOS in Orion using sensitive observations from the archive of the Karl G. Jansky Very Large Array (VLA) of the National Radio Astronomy Observatory. Here we report the radio detection of JuMBO 24 in three epochs distributed across a decade, in 2012, 2018, and 2022. This paper is organized as follows. In Section 2 we present the observations, while in Section 3 we discuss the implications of this detection. Finally, in Section 4 we summarize our conclusions.

# Observations

## VLA Observations

We analyzed the VLA data of the three projects listed in Table [\[tab:obsvla\]](#tab:obsvla). The data were calibrated in the standard manner using the CASA (Common Astronomy Software Applications; (cite: McMullin+2007)) package of NRAO and the pipeline provided for VLA[^1] observations. A robust weighting of 0 (cite: Briggs_1995) was used in the imaging to optimize the compromise between sensitivity and angular resolution. The images were made with a $(u,v)$ range set to $>100~k\lambda$, to suppress structures larger than 2$''$ that limit the signal-to-noise ratio in the Orion field. The project SD0630 consists of five sessions made on 2012 September 30 and October 2, 3, 4, and 5. The projects 17A-069 and 22A-285 were made on single sessions on 2018 May 11 and 2022 July 2, respectively. In Table [\[tab:obsvla\]](#tab:obsvla) we also give the mean epoch of the observations, the configurations used, the central frequency and the bandwidth of the observations, the parameters of the synthesized beam, the radio flux density and position of JuMBO 24, and the 4-$\sigma$ upper limit to the absolute circular polarization. The gain calibrator, J0541$-$0541, was the same for all observations so the astrometry can be directly compared more easily. The absolute flux calibrator was J0137$+$331 (3C 48) for projects SD0630 and 22A-285, and J0521$+$1638 (3C 138) for project 17A-069.

We find that the near-infrared source JuMBO 24 coincides within 0.05 arcsec with a radio continuum source present in all three VLA images. The position of JuMBO 24 given by (cite: Pearson_McCaughrean_2023) is RA(J2000) = $05^h 35^m 19\rlap.^s50616$, DEC(J2000) = $-05^\circ 23' 39\rlap.{''}7303$. The positions of the radio counterpart source for the three epochs are given in Table 1. This radio source first appeared in the list of (cite: Forbrich+2016). JuMBO 24 was originally detected in near-infrared Hubble Space Telescope observations in the F160W (1.4-1.8 $\mu$m) and F110W (0.8-1.4 $\mu$m) filters, with magnitudes of 17.11 and 18.33, respectively (cite: Luhman+2000). (cite: Slesnick+2004) reported a K-band magnitude of 19.51 (their source 728). These authors used near-infrared photometry and spectroscopy as well as evolutionary stellar models (cite: Dantona_Mazzitelli_1994; Baraffe+1998) to determine an infrared spectral type of M5.5$\pm$1.5 and a mass of $\sim 52$ M$_J$, under the assumption of a single star. The JWST data and the interpretation of (cite: Pearson_McCaughrean_2023) indicate that JuMBO 24 is a binary with both components having the same giant-planet mass of $11.5~M_J$ and a separation of 28 au in the plane of the sky. JuMBO 24 stands out in the list of these objects because it has the largest total mass ($23~M_J$) and the closest separation in the plane of the sky (28 au). Also, the primary of JuMBO 24 has the second smallest extinction, $A_V$ = 3.6, behind only JuMBO 27, that has $A_V$ = 2.4.

+:-------:+:--------:+:--------------------:+:-----:+:------------:+:----------------------------------------------:+:---------------:+:-----------------------------------:+:------------------------------------:+:---------------:+
|         | Mean     |                      | $\nu$ | $\Delta \nu$ | Synthesized Beam                               | Observational results for JuMBO 24                                                                             |
+---------+----------+----------------------+-------+--------------+------------------------------------------------+-----------------+-------------------------------------+--------------------------------------+-----------------+
| Project | Epoch    | Configuration        | (GHz) | (GHz)        | ($\theta_{max} \times \theta_{min}$; PA)       | $F_\nu~(\mu$Jy) | RA(J2000)                           | DEC(J2000)                           | $\vert V \vert$ |
+---------+----------+----------------------+-------+--------------+------------------------------------------------+-----------------+-------------------------------------+--------------------------------------+-----------------+
| SD0630  | 2012.762 | A, BnA$\rightarrow$A | 6.1   | 2.0          | $0\rlap.{''}25 \times 0\rlap.{''}21;+2^\circ$  | 45.4$\pm$4.5    | $19\rlap.^s5061 \pm 0\rlap.^s0006$  | $39\rlap.{''}730 \pm 0\rlap.{''}012$ | $\leq 15\%$     |
+---------+----------+----------------------+-------+--------------+------------------------------------------------+-----------------+-------------------------------------+--------------------------------------+-----------------+
| 17A-069 | 2018.359 | A                    | 10.0  | 4.0          | $0\rlap.{''}21 \times 0\rlap.{''}17;-17^\circ$ | 60.0$\pm$13.0   | $19\rlap.^s 5065\pm0\rlap.^s0017$   | $39\rlap.{''}727\pm0\rlap.{''}024$   | $\leq 40\%$     |
+---------+----------+----------------------+-------+--------------+------------------------------------------------+-----------------+-------------------------------------+--------------------------------------+-----------------+
| 22A-285 | 2022.501 | A                    | 6.1   | 4.0          | $0\rlap.{''}27 \times 0\rlap.{''}21;+10^\circ$ | 50.0$\pm$7.2    | $19\rlap.^s 5059\pm 0\rlap.^s 0016$ | $39\rlap.{''}698\pm0\rlap.{''}017$   | $\leq 20\%$     |
+---------+----------+----------------------+-------+--------------+------------------------------------------------+-----------------+-------------------------------------+--------------------------------------+-----------------+

: Parameters of the VLA Observations

Table notes: Columns 4 and 5 are the central frequency and bandwidth of the observations. The position given in columns 8 and 9 show only the seconds of the RA and the arcseconds of the DEC, measured from RA(J2000) = $05^h35^m$ and DEC(J2000) = $-05^\circ23'$, respectively. Column 10 gives the 4-$\sigma$ upper limit to the absolute circular polarization.

## ALMA Observations

We searched for JuMBO counterparts in the Atacama Large Millimeter/Submillimeter Array archive. We analyzed several data sets: 2013.1.00546.S, 2015.1.00534.S, 2015.1.00262.S, 2015.1.00669.S, 2017.1.01353.S, 2017.1.01639.S, and 2018.1.01107.S. However, we do not find any evident millimeter or even submillimeter continuum counterpart for any of the 42 JuMBOs. In particular, the data set 2015.1.00669.S (PI: Hacar, Alvaro) is a large mosaic made in Band 3 that covers a large area (OMC2, OMC1-N, OMC1, OMC1-S). The rms noise for this large mosaic is 150 $\mu$Jy Beam$^{-1}$, so we do not detect any counterpart at a 5-$\sigma$ level of 750 $\mu$Jy Beam$^{-1}$. Future much deeper ALMA observations of the Orion Nebula could reveal thermal emission related with the JuMBOS.

# Discussion

The first centimeter detection of a single planetary mass object, SIMP J01365662+0933473, was achieved by (cite: 2018ApJS..237...25K). The first identification of a centimeter continuum source with a planetary-mass binary object presented here is also of great relevance by the information the radio data can provide. We exemplify these possibilities in what follows. Further work, particularly in relation to the origin of the radio emission is deferred to forthcoming papers.

## The Probability of a Random Association

In this section we estimate how likely it is that the positional agreement of JuMBO 24 with one of the radio sources in the region is fortuitous and not real. In their study of Orion, (cite: Forbrich+2016) detected a total of 556 radio sources in a region of $13\rlap.’6 \times 13\rlap.’6$. Most of the sources, however, are enclosed in a region with radius of $\sim 3’$ (see Figure 5 of (cite: Forbrich+2016)). Of the 556 sources, 358 have flux densities equal or larger than 50 $\mu$Jy, the characteristic value for the radio source proposed to be associated with JuMBO 24. These results give a solid angle density of $3.5 \times 10^{-3}$ radio sources per arcsec$^2$.

The most accurate position for the radio source is that obtained from the multiepoch project SD0630. Convolving the statistical errors of the position of the radio source (Table 1) with the systematic positional error of $0\rlap.{''}01$, as estimated by (cite: Dzib+2017), we obtain a $\pm 1-\sigma$ error box of $0\rlap.{''}027 \times 0\rlap.{''}031$. The *a priori probability of a source randomly falling in this error box is then $2.9 \times 10^{-6}$. However, the coincidence of the radio source with any of the 42 JuMBOs in Orion would have been considered significant, so assuming that these possible coincidences are independent events we have to multiply the probability of a given JuMBO source being spatially associated times 42. We finally get an *a priori probability of one JuMBO randomly coinciding in position with one radio source to be only $1.2 \times 10^{-4}$, supporting a real association.**

## Upper Limits to the Proper Motion

Using the radio positions determined at the three epochs we can search for the proper motions of the source. As noted before, the fact that the same nearby ($\sim 1\rlap.^\circ5$) gain calibrator (J0541$-$0541) was used in all observations implies a sound astrometry. A least-squares fit to the positions given in Table 1, after adding in quadrature a systematic error of $0\rlap.{''}01$, yields the following values:

$$\mu_{\alpha} \cos \delta = +1.8 \pm 2.8 \text{~mas~yr}^{-1} ~~; ~~\mu_\delta  = -3.0 \pm 2.5\text{~mas~yr}^{-1}.$$

This result implies that there are no significant proper motions at a 3-$\sigma$ level of $\sim$8 mas yr$^{-1}$, that corresponds to a transverse velocity of $\sim 15$ km s$^{-1}$ at a distance of 388 pc (cite: Kounkel+2017). These upper limits rule out large velocities in the plane of the sky, although it should be pointed out that significant velocities could be present in the radial direction. Our measurements can be registered to an approximate rest frame for the Orion Cluster by subtracting the average proper motion of the radio stars in the core of Orion (cite: Dzib+2017), $\mu_{\alpha} \cos\delta = +1.07 \pm 0.09\text{~mas~yr}^{-1}; \mu_{\delta}  = -0.84 \pm 0.16\text{~mas~yr}^{-1}$. We obtain:

$$\mu_{\alpha} \cos \delta = +0.7 \pm 2.8\text{~mas~yr}^{-1} ~~ ; ~~ \mu_\delta  = -2.2 \pm 2.5\text{~mas~yr}^{-1}.$$

We conclude that JuMBO 24 is not moving at large velocities compared to the radio stars in Orion. (cite: 2019A&A...624A.120V) have made numerical simulations for the evolution of young and dense stellar clusters. They find that single free-floating planets ejected from their original system after a strong encounter with another star will have velocities typically three times those of the stars in the cluster. (cite: Dzib+2017) find a typical velocity dispersion of $\sim 2-3$ km s$^{-1}$ along a plane-of-the-sky coordinate for the radio-emitting stars in the core of the Orion Nebula Cluster. Assuming that the results of (cite: 2019A&A...624A.120V) can be extended to free-floating binary planets, we expect velocity dispersions of $\sim 6-9$ km s$^{-1}$ for the JuMBOs as well as for the $\sim$500 single planetary-mass objects reported in Orion by (cite: Pearson_McCaughrean_2023). Future highly accurate determinations of the kinematics of the Orion JuMBOs will help understand the origin of these unexpected sources.

## Time Monitoring

The two measurements at 6.1 GHz given in Table 1 are separated by a decade and, within the noise, they are consistent with being equal. Another evidence that weighs in favor of a steady flux is the analysis of the five different epochs observed in project SD0630. In Table 2, we give the epochs and flux densities for each individual observing session, where we can see that all flux densities are consistent within noise with a value of $\simeq 45~ \mu$Jy. While more intensive observations are needed to establish firmly the time behavior of the radio emission from JuMBO 24, all existing data are consistent with a steady flux density over timescales of days to years.

|             |          |               |
|:-----------:|:--------:|:-------------:|
|             | Mean UTC | Flux Density  |
|    Date     | (hours)  |   ($\mu$Jy)   |
| 2012 Sep 30 |   11.3   | 52.9$\pm$6.5  |
| 2012 Oct 02 |   11.2   | 39.7$\pm$5.5  |
| 2012 Oct 03 |   14.8   | 55.0$\pm$11.0 |
| 2012 Oct 04 |   13.4   | 44.9$\pm$7.1  |
| 2012 Oct 05 |   12.3   | 40.5$\pm$6.6  |

: Flux Densities of JuMBO 24 at 6.1 GHz from Project SD0630

## Nature of the Radio Emission

The objects with known radio emission that are more similar to the components of the JuMBOs are the ultracool dwarfs (cite: 2022ApJ...932...21K). The radio emission from the latter objects has two main components: a periodically bursting emission arising in aurorae and a slowly varying, quiescent emission with a low degree of circular polarization arising from a structure similar in morphology to the Jovian radiation belts (cite: 2023Sci...381.1120C; 2023Natur.619..272K). The bursting component is circularly polarized and it is believed to be produced by the electron cyclotron maser instability (cite: 2006ApJ...653..690H), the same coherent emission process that creates the auroral radio emission from the planets of the Solar System (cite: 2017ApJ...846...75P). On the other hand, the quiescent component is usually interpreted as being caused by radio emission from relativistic electrons giving rise to gyrosynchrotron or synchrotron mechanisms, according to how relativistic the electrons are. Now it is known that this quiescent emission is produced in radiation belts (cite: 2023Sci...381.1120C; 2023Natur.619..272K). Given that the radio emission from JuMBO 24 is steady in time, one would expect it to be produced by relativistic electrons spiraling in the magnetic fields of a radiation belt.

The spectral index of the radio emission is an indicator of the nature of the radiation. The observations of SD0630 were made using two bandwidths of 1 GHz each, centered at 4.8 and 7.4 GHz, respectively. We obtain that the flux densities at these two frequencies are 53.8$\pm$6.0 and 43.0$\pm$5.8 $\mu$Jy, respectively. Assuming that the continuum spectrum is described by a power law, $S_{\nu} \propto \nu^{\alpha}$, we derive a spectral index of $\alpha = -0.52\pm0.40$. We can also derive a spectral index assuming that the source has a steady flux density and combining the values given in Table 1. From these data we derive $\alpha = +0.50\pm0.43$. The weighted mean and rms of these two determinations is $\alpha = -0.05\pm0.51$. Given the large uncertainty, it is difficult to discriminate between possible emission mechanisms, but we can rule out an optically-thick blackbody in the Rayleigh-Jeans regime ($\alpha$ = 2) and the negative steep indices characteristic of pulsars ($\alpha \leq$ –2).

We did not detect circular polarization at any epoch. However, the upper limits are not very stringent. The presence of circular polarization is a strong indicator of either electron cyclotron maser instability, cyclotron or gyrosynchrotron radiation but, of course, its absence does not rule out these mechanisms.

As noted above, the ultracool dwarfs are the closest thing to giant planets that have been detected in the radio. The radio luminosities of nine quiescent binary ultracool dwarf systems discussed by (cite: 2022ApJ...932...21K) are in the range of $10^{11.9-14.6}$ erg s$^{-1}$ Hz$^{-1}$. JuMBO 24 has a radio luminosity of $10^{16.0}$ erg s$^{-1}$ Hz$^{-1}$. We then conclude that the radio luminosity of JuMBO 24 is orders of magnitude larger than naively expected.

## Position and Morphology of the Radio and Infrared Sources

In Figure [1](#fig:VLAmap) we show an image of the radio continuum emission obtained from concatenating all the data of project SD0630. We can see that the radio source coincides closely with the near-infrared position given by (cite: Pearson_McCaughrean_2023). A Gaussian ellipsoid fit to the radio image using the task IMFIT of CASA gives a deconvolved angular size of $0\rlap.{''}179 \pm 0\rlap.{''}045 \times 0\rlap.{''}143  \pm 0\rlap.{''}074; 60^\circ \pm 89^\circ$. Although the radio source is only marginally resolved, these angular dimensions and the orientation of the major axis are consistent with the value obtained from Gaussian ellipsoid fits to the JWST images. For instance a fit to the image at 2.77 $\mu$m results in $0\rlap.{''}170 \pm 0\rlap.{''}002 \times 0\rlap.{''}132  \pm 0\rlap.{''}002; 97^\circ \pm 2^\circ$. The shorter wavelength JWST observations show that the cause of the extension along the east-west direction is the binarity of the source, which is comprised of two objects separated by about 100 mas precisely along the east-west direction. This result suggests that, as in the near-infrared, there is significant radio emission from both components of the binary. This result is similar to that obtained for the compact ultra-cool dwarf binary VHS 1256$-$1257AB, where the optical and radio emissions show compatible dimensions and orientation (cite: Rodriguez+2023).

# Conclusions

We report the detection of radio continuum emission at 6 to 10 GHz associated with the recently identified Jupiter-Mass Binary Object JuMBO 24 in the Orion Nebula Cluster. Within the errors, the radio emission appears steady on timescales from days to years and exhibits no circular polarization. No significant proper motion is detected between the three observing epochs, ruling out large velocities ($\geq 15~km~s^{-1}$) in the plane of the sky. The radio emission is marginally resolved in the same direction as the infrared source detected by the JWST, suggesting that the radio emission comes from a combination of the two planetary mass objects. Additional radio observations are necessary to pin down the nature of the radio emission mechanism.

natexlab

(ref: Baraffe+1998) Baraffe, I., Chabrier, G., Allard, F., & Hauschildt, P. H. 1998, A&A, 337, 403, doi: [`10.48550/arXiv.astro-ph/9805009`](http://doi.org/10.48550/arXiv.astro-ph/9805009)

(ref: Briggs_1995) Briggs, D. S. 1995, in American Astronomical Society Meeting Abstracts, Vol. 187, American Astronomical Society Meeting Abstracts, 112.02

(ref: 2023Sci...381.1120C) Climent, J. B., Guirado, J. C., Pérez-Torres, M., Marcaide, J. M., & Peña-Moñino, L. 2023, Science, 381, 1120, doi: [`10.1126/science.adg6635`](http://doi.org/10.1126/science.adg6635)

(ref: Dantona_Mazzitelli_1994) D’Antona, F., & Mazzitelli, I. 1994, ApJS, 90, 467, doi: [`10.1086/191867`](http://doi.org/10.1086/191867)

(ref: Dzib+2017) Dzib, S. A., Loinard, L., Rodrı́guez, L. F., et al. 2017, ApJ, 834, 139, doi: [`10.3847/1538-4357/834/2/139`](http://doi.org/10.3847/1538-4357/834/2/139)

(ref: Forbrich+2016) Forbrich, J., Rivilla, V. M., Menten, K. M., et al. 2016, ApJ, 822, 93, doi: [`10.3847/0004-637X/822/2/93`](http://doi.org/10.3847/0004-637X/822/2/93)

(ref: Greisen_2003) Greisen, E. W. 2003, in Astrophysics and Space Science Library, Vol. 285, Information Handling in Astronomy - Historical Vistas, ed. A. Heck, 109, doi: [`10.1007/0-306-48080-8_7`](http://doi.org/10.1007/0-306-48080-8_7)

(ref: 2006ApJ...653..690H) Hallinan, G., Antonova, A., Doyle, J. G., et al. 2006, ApJ, 653, 690, doi: [`10.1086/508678`](http://doi.org/10.1086/508678)

(ref: Hurley_Shara_2002) Hurley, J. R., & Shara, M. M. 2002, ApJ, 565, 1251, doi: [`10.1086/337921`](http://doi.org/10.1086/337921)

(ref: 2018ApJS..237...25K) Kao, M. M., Hallinan, G., Pineda, J. S., Stevenson, D., & Burgasser, A. 2018, ApJS, 237, 25, doi: [`10.3847/1538-4365/aac2d5`](http://doi.org/10.3847/1538-4365/aac2d5)

(ref: 2023Natur.619..272K) Kao, M. M., Mioduszewski, A. J., Villadsen, J., & Shkolnik, E. L. 2023, Nature, 619, 272, doi: [`10.1038/s41586-023-06138-w`](http://doi.org/10.1038/s41586-023-06138-w)

(ref: 2022ApJ...932...21K) Kao, M. M., & Sebastian Pineda, J. 2022, ApJ, 932, 21, doi: [`10.3847/1538-4357/ac660b`](http://doi.org/10.3847/1538-4357/ac660b)

(ref: Kounkel+2017) Kounkel, M., Hartmann, L., Loinard, L., et al. 2017, ApJ, 834, 142, doi: [`10.3847/1538-4357/834/2/142`](http://doi.org/10.3847/1538-4357/834/2/142)

(ref: Kroupa_Bouvier_2003) Kroupa, P., & Bouvier, J. 2003, MNRAS, 346, 369, doi: [`10.1046/j.1365-2966.2003.07224.x`](http://doi.org/10.1046/j.1365-2966.2003.07224.x)

(ref: Lucas_Roche_2000) Lucas, P. W., & Roche, P. F. 2000, MNRAS, 314, 858, doi: [`10.1046/j.1365-8711.2000.03515.x`](http://doi.org/10.1046/j.1365-8711.2000.03515.x)

(ref: Luhman+2000) Luhman, K. L., Rieke, G. H., Young, E. T., et al. 2000, ApJ, 540, 1016, doi: [`10.1086/309365`](http://doi.org/10.1086/309365)

(ref: McMullin+2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: MiretRoig2023) Miret-Roig, N. 2023, Ap&SS, 368, 17, doi: [`10.1007/s10509-023-04175-5`](http://doi.org/10.1007/s10509-023-04175-5)

(ref: Pearson_McCaughrean_2023) Pearson, S. G., & McCaughrean, M. J. 2023, arXiv e-prints, arXiv:2310.01231, doi: [`10.48550/arXiv.2310.01231`](http://doi.org/10.48550/arXiv.2310.01231)

(ref: 2017ApJ...846...75P) Pineda, J. S., Hallinan, G., & Kao, M. M. 2017, ApJ, 846, 75, doi: [`10.3847/1538-4357/aa8596`](http://doi.org/10.3847/1538-4357/aa8596)

(ref: Rodriguez+2023) Rodriguez, L. F., Dzib, S. A., Zapata, L. A., & Loinard, L. 2023, arXiv e-prints, arXiv:2309.08812, doi: [`10.48550/arXiv.2309.08812`](http://doi.org/10.48550/arXiv.2309.08812)

(ref: Slesnick+2004) Slesnick, C. L., Hillenbrand, L. A., & Carpenter, J. M. 2004, ApJ, 610, 1045, doi: [`10.1086/421898`](http://doi.org/10.1086/421898)

(ref: 2019A&A...624A.120V) van Elteren, A., Portegies Zwart, S., Pelupessy, I., Cai, M. X., & McMillan, S. L. W. 2019, A&A, 624, A120, doi: [`10.1051/0004-6361/201834641`](http://doi.org/10.1051/0004-6361/201834641)

(ref: Wang+2023) Wang, Y., Perna, R., & Zhu, Z. 2023, arXiv e-prints, arXiv:2310.06016, doi: [`10.48550/arXiv.2310.06016`](http://doi.org/10.48550/arXiv.2310.06016)

(ref: Whitworth_Zinnecker_2004) Whitworth, A. P., & Zinnecker, H. 2004, A&A, 427, 299, doi: [`10.1051/0004-6361:20041131`](http://doi.org/10.1051/0004-6361:20041131)

(ref: ZapateroOsorio+2000) Zapatero Osorio, M. R., Béjar, V. J. S., Martı́n, E. L., et al. 2000, Science, 290, 103, doi: [`10.1126/science.290.5489.103`](http://doi.org/10.1126/science.290.5489.103)

We thank the anonymous reviewer for several valuable comments that improved the paper. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. We acknowledge the support from DGAPA, UNAM (projects IN112323, IN112417, IN112820 and IN108324) and CONAHCyT, México (projects 238631, 280775 and 263356).

# Facilities

NASA/ESA/CSA(JWST), NRAO(VLA)

# Software

AIPS (cite: Greisen_2003), CASA (cite: McMullin+2007)

[^1]: https://science.nrao.edu/facilities/vla/data-processing/pipeline

</paper>

Write the methods card for this paper.