# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.496.5089Z\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.496.5089Z",
 "title": "The Ophiuchus DIsc Survey Employing ALMA (ODISEA) - II. The effect of stellar multiplicity on disc properties",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Zurlo, Alice",
 "n_authors": 12,
 "arxiv_id": "2006.16259",
 "doi": "10.1093/mnras/staa1886",
 "alma_projects_linked_by_archive": [
  "2016.1.00545.S"
 ]
}
```

Paper text:
<paper>
# The Ophiuchus DIsc Survey Employing ALMA (ODISEA). II. The effect of stellar multiplicity on disc properties[^2]

## Abstract

We present Adaptive Optics (AO) near infrared (NIR) observations using VLT/NACO and Keck/NIRC2 of ODISEA targets. ODISEA is an ALMA survey of the entire population of circumstellar discs in the Ophiuchus molecular cloud. From the whole sample of ODISEA we select all the discs that are not already observed in the NIR with AO and that are observable with NACO or NIRC2. The NIR-ODISEA survey consists of 147 stars observed in NIR AO imaging for the first time, as well as revisiting almost all the binary systems of Ophiuchus present in the literature (20 out of 21). In total, we detect 20 new binary systems and one triple system. For each of them we calculate the projected separation and position angle of the companion, as well as their NIR and millimeter flux ratios. From the NIR contrast we derived the masses of the secondaries, finding that 9 of them are in the sub-stellar regime (30-50 M$_{\mathrm{Jup}}$). Discs in multiple systems reach a maximum total dust mass of $\sim$ 50 M$_{\oplus}$, while discs in single stars can reach a dust mass of 200 M$_{\oplus}$. Discs with masses above 10 M$_{\oplus}$ are found only around binaries with projected separations larger than $\sim$ 110 au. The maximum disc size is also larger around single star than binaries. However, since most discs in Ophiuchus are very small and low-mass, the effect of visual binaries is relatively weak in the general disc population.

Instrumentation: Adaptive optics, ALMA interferometry, Stars: visual binaries, binaries, Planets formation, Protoplanetary discs, Planetary systems

# Introduction

The very high incidence of extrasolar planets (cite: 2013Sci...340..572H; 2015ApJ...809....8B) suggests that most of the circumstellar discs we see in star-forming regions should form planetary systems. The occurrence of exoplanets is particularly high for low-mass planets around M-dwarfs, where the statistics are robust. (cite: 2016MNRAS.457.2877G) estimate that M-type main-sequence stars host an average of 2.2 $\pm$ 0.3 planets with radii of 1-4 R$_{\oplus}$. The incidence of extrasolar planets at larger distances from their hosts is more poorly constrained, but microlensing studies also indicate that most stars in the Milky Way might harbor ice or gas giants at 5-10 au separations (cite: 2012Natur.481..167C).

In this context, studying full populations of protoplanetary discs can help linking disc properties to the properties of the planets detected so far. ALMA’s unprecedented sensitivity provides the opportunity to study nearly complete and unbiased samples of discs at sub-arcsecond resolution in the (sub)mm regime (cite: 2016ApJ...828...46A; 2016ApJ...831..125P; 2018MNRAS.478.3674R). Circumstellar discs may become optically thin at these wavelengths and therefore, resolved disc images inform on the spatial distribution of mass.

We have recently conducted a survey of the entire population of circumstellar discs ($\sim$290) identified by *Spitzer* in the Ophiuchus molecular cloud to study both their gas and dust components: the Ophiuchus Disk Survey Employing ALMA (cite: 2019MNRAS.482..698C). At a distance of 140$\pm$10 pc (cite: 2017ApJ...834..141O; 2019A&A...626A..80C), Ophiuchus is the closest of the major star-forming regions in the solar neighborhood, and ODISEA is the largest ALMA survey of its kind thus far.

One of the main objectives of ODISEA is to study the dependence of disc properties on stellar multiplicity. While most stars form in multiple systems (cite: 2013ARA&A..51..269D), the effects that (sub)stellar companions have on planet formation are not well understood. Observational studies show that discs are less frequent (cite: 2009ApJ...696L..84C; 2012ApJ...745...19K) and less massive (cite: 2005ApJ...619L.175A; 2017ApJ...851...83C) in close binary systems (separations $<100$ au) and that much wider binaries have little effects on discs.

From extra-solar planet studies, it is also clear that planets can form around very tight ($<1$ au) stellar binary systems (cite: 2011Sci...333.1602D) as well as around individual stars in wide projected separation ($>100$ au) binaries (cite: 2014A&A...569A.120L).

Medium-separation binaries (e.g., $\sim$10-50 au), like those resolvable with the near-IR (NIR) Adaptive Optics (AO) observations presented here, might result in compact discs which might not have enough mass to form giant planets and/or might not survive long enough to form rocky planets (cite: 2009ApJ...696L..84C). However, these hypotheses still need to be observationally verified.

Here we present observations and analysis of the NIR-AO follow-up of 164 objects of the ODISEA survey conducted with the NACO instrument at the VLT and the NIRC2 instrument at Keck. We supplement these observations with multiplicity information from the literature and public archives. The sample selection of this NIR survey is presented in Sec. [2](#s:sample). The observations and data reduction of the NIR and mm data are described in Sec. [3](#s:obs). Our results are presented and discussed in Sec. [4](#s:res). We close the article with a summary of our conclusions in Sec. [5](#s:con).

# The ODISEA Sample and literature data

The population of circumstellar discs in the Ophiuchus molecular cloud is composed of 289 objects. The ODISEA ALMA survey has been divided into two samples, A and B. Sample A includes 147 objects of Class I, Flat spectrum, and bright (K $\le$ 10 mag) Class II sources. Sample B includes a total of 142 sources composed of the fainter Class II objects, and all Class III objects. Many of these targets were previously observed in the near infrared, providing the information of the multiplicity.

(cite: 2009ApJ...696L..84C) collected multiplicity information for 349 stars in nearby star-forming regions, including 73 objects that are part of the ODISEA sample. In (cite: 2013ApJ...762..100C) all 34 objects presented are in common with the sample presented here. In (cite: 2015ApJ...813...83C) 50 of 114 stars presented are in common with this sample. (cite: 2017ApJ...851...83C) presented a 870 $\mu$m survey of 49 objects in $\rho$ Ophiuchus, all of them but one are in common with our sample. (cite: 2018AJ....155..109S) recently presented orbital motion of 8 binaries in common with our survey. As some of the objects are in common in between these works, we found a total number of 109 (of which 21 are binaries) stars in common with our survey.

The ESO and Keck archives were searched for the presence of unpublished NIR public data useful for determining multiplicity. We found three objects in this sample observed with the NACO and SOFI instruments on the VLT and seven observed with the NIRC and NIRC2 instruments on Keck.

Excluding the objects presented in the literature, or available in the archives, we were left with 178 objects. For these objects we planned VLT/NACO and Keck/NIRC2 observations.

The NIR wave front sensor (WFS) on NACO has a K-band magnitude limit where sources need to be brighter than K=12. 70 stars in our sample met this requirement and were observed with NACO. All the other stars were included in the NIRC2 sample. For most of them we required the use of the laser guide star (LGS) using the target itself as natural guide star (NGS) for the laser tip-tilt correction, or a close-by bright star. The stars observable with NIRC2 were 77 in total. Unfortunately, the 29 remaining objects are too faint and do no have any close NGS for the tip-tilt correction. Therefore, they are not observable in NIR with the current AO-imaging instruments from the ground. These objects were excluded from the sample in the statistical analysis, the complete list of them is available in Table [1](#t:non_o).

# Observations and data reduction

NIR observations exploiting VLT/NACO and Keck/NIRC2 were performed to study multiplicity in Ophiuchus. These two instruments were chosen for their efficiency in taking short exposures with small overheads. The observing strategy was the same for both instruments: very short L$^{\prime}$ filter integrations with jittering. For each star we took two or three integrations where the star fell in different quadrants of the detector. This is because the sky background, which is bright at these wavelengths, is recorded quasi-simultaneously.

## VLT/NACO

The observations with NACO were carried out from April 8 to April 11, 2017 (4 half nights), program 099.C-0465 (PI: Zurlo). The atmospheric conditions were in general favorable, especially during the last night, with stable seeing between 0.5$''$ to 0.7$''$, 5 ms coherence time and constant wind. Additional data were taken during the nights 22 to 24 August 2019 of program 0103.C-0466 (PI: Zurlo) as backup targets. The conditions of those nights were also optimal.

We adopted the technique of "star-hopping" which permits switching from one target to another, if they are close enough, by applying an offset to the telescope (hence saving on acquisition overheads). In practice, the AO loop is opened before the “hop” to the second star, and closed again with the same settings as the first star after the hop. To be able to apply this technique, the stars have to be separated by $<$ 900$''$ and have a similar magnitude (1-2 mag of difference). We divided our sample of 70 stars into 10 groups of 7 stars each, with ranges of magnitudes with a difference of maximum 1 mag and close coordinates on the sky.

Given the faintness of our targets, we chose the AO configuration N90C10 which provides NAOS with 90% of the stars light and the detector with the remaining 10%. In this way the AO was stable during the exposure. We chose the L$^{\prime}$ filter given the red colors of the stars of the sample. In this configuration the exposure time is very short, 0.16-0.17 s, to avoid saturation of the background. For each star we took two exposures (of 200 NDIT[^3] each), where the star fell in two different quadrants of the detector to permit a quasi-simultaneous subtraction of the background. The pixel scale of the NACO detector is 0.02712 arcsec/pixel. In total we observed 88 stars.

The data were reduced with the python Vortex Image Processing (`VIP`) package (cite: 2017AJ....154....7G). The raw data, two exposures per star, were background subtracted one from the other, flat-fielded, then recentered to have the target in the center of the detector. A bad-pixel removal has been applied. Finally, in order to reduce the effects of atmospheric turbulences on the images, a high-pass spatial filter has been used. Each final image is the mean of the two recentered frames.

To calibrate the astrometric position of the central star we adopted the coordinates given by the ALMA centroid of the primary star, which are more precise than the coordinates given in the header. The primary was assumed to be the disc with highest flux. The scale and true north calibration has been applied as listed in the NACO user manual.

The reduced NACO images of the stars with companions are shown in Figures [1](#f:mos), [2](#f:mos2), [3](#f:mos3), and [4](#f:mos4). The median value of the NACO contrast curves is shown in Fig. [5](#f:contr), in general companions with a flux 50 times fainter than the primary are detected. Ten new binaries have been found. The properties of the systems are listed in Table [\[t:bin\]](#t:bin). Note that ISO-Oph204 (ODISEA ID: C4_134) seems to be a triple system, but it is very likely that the companion appears double because of a shift of the detector during the acquisition. Since the ghost is present in both the images taken, we can speculate that the primary is in fact a very close binary (it also appears elongated in the image) and the AO is tilting in between the two tight stars, causing the small shift of the detector. With the data available we cannot conclude on the nature of this system. This system was already identified as a wide binary by (cite: 2009ApJ...696L..84C).

## Keck/NIRC2

Observations with Keck/NIRC2 were carried out during the nights from the 8 to the 10 June 2017 (3 half nights), program GN-2017A-Q-29 (PI: Williams). The atmospheric conditions at Mauna Kea were exquisite: seeing from 0.3$''$ to 0.4$''$. During the first night we observed all the targets bright enough to be used as NGS for the AO. During the two other nights we observed very faint stars using the LGS, we implied the target itself for tip-tilt correction when possible, otherwise a close-by bright star. In total 51 stars have been observed. Some of the targets foreseen were not visible in the detector.

The same method exploited for NACO has been followed: for each star we took a short L$^{\prime}$ exposure, jittering the star to place it in three different detector quadrants at each time. The pixel scale of the NIRC2 detector is 0.009942 arcsec/pixel and the true North correction is listed in the Keck header. As for NACO, the astrometric position of the central star are the coordinates given by the ALMA centroid of the primary star.

The NIRC2 data have been reduced the same way as NACO data as described in Sec. [3.1](#s:obsnaco). The reduced NIRC2 images of the stars with companions are shown in Figures [1](#f:mos), [2](#f:mos2), [3](#f:mos3), and [4](#f:mos4). The median value of the NIRC2 contrast curves is shown in Fig. [5](#f:contr), which is deeper than NACO, allowing the detection of companions 100 times fainter than the primary. Nine new binaries have been found, and we followed-up the already known binary system around V\*V2131Oph (C4_123). The properties of the systems are listed in Table [\[t:bin\]](#t:bin).

## Archive data

We found 13 objects of our sample in the ESO and Keck archives. Two objects have been observed with NACO: GY5, during the night 2005-05-28 (program 075.C-0042) and CRBR-L, during the night 2009-04-25 (program 60.A-9800). Both of them have been imaged with the jittering technique. The first target has been detected in K$_s$ filter, while the second one in L$^{\prime}$. Both appear as single stars in the detector. The images have been reduced with the same technique described in Sec. [3.1](#s:obsnaco).

The object BKLTJ162538-242238, also known as Oph-2, which was presented as a binary system in (cite: 2005A&A...437..611R), has public NACO data in the archive under program 079.C-0307(A). We reduced and analyzed the data, with the jittering technique and K$_s$ filter, the final image is shown in Fig. [6](#f:onlyalma) (left panel).

Another object, GY264, has been observed during the night 2012-04-16, with SOFI. The images, taken with the jittering method, have been median combined after recentering. No calibrations (dark, flat-field) have been found for the dataset. Nevertheless, the star is clearly visible at the center of the detector, and it appears isolated. Other stars appear in the FoV, with projected separations greater than 1.4 arcmin.

In the Keck archive, data of 7 objects of our ALMA survey are available from the instruments NIRC and NIRC2. All the available data have been taken in K$_s$ filter. For three stars sparse aperture masking (SAM) data are available. Four stars appear to be single stars. In conclusion, all the stars with archival data are single stars.

## ALMA 1.3 mm data

For the ALMA data reduction and presentation we refer the reader to paper I (cite: 2019MNRAS.482..698C) for Sample A, which consists of 147 targets observed under the Cycle-4 ALMA programme 2016.1.00545.S, with the antennas configuration C40-5. For this sample the typical rms is of $\sim 0.15$ mJy/beam with a synthesized beam of 0.28$''$$\times$0.19$''$. In this first observation block 120 sources are detected and 27 are non-detections. For Sample B we refer the reader to (cite: 2019ApJ...875L...9W), these 142 other objects were observed with a different antennas configuration (C40-3 array), under the same program. Among the 289 objects (cite: 2019ApJ...875L...9W) identified 23 spurious objects that are not part of Ophiuchus. For sample B, the sensitivity is $\sim 0.2$ mJy/beam, the beam size is $\sim$ 0.98$''$$\times$0.74$''$. The number of detections and non-detections in this sample are 66 and 76, respectively. Note that the difference between the two ODISEA ALMA samples is the K-band magnitude, which is intrinsically correlated with the mass of the stars. The sample with lower resolution is composed of stars with magnitudes fainter than K-band = 10 and contain the lower mass stars, which explains the much lower mm detection rate given the dependance of disc masses on stellar mass (cite: 2013ApJ...771..129A; 2016ApJ...831..125P).

Multiple systems were identified and presented in (cite: 2019MNRAS.482..698C): one triple system and 11 binaries were detected in the millimeter. The ALMA images are shown as contours in their NIR counterparts in Fig. [1](#f:mos), [2](#f:mos2), [3](#f:mos3), and [4](#f:mos4). The multiple system detected with ALMA for which we do not have NIR AO-imaging is shown in Fig. [6](#f:onlyalma) (right panel).

![image](Odisea019_final.pdf) ![image](Odisea027_final.pdf) ![image](Odisea045_final.pdf)\
![image](Odisea035_final.pdf) ![image](Odisea057_final.pdf) ![image](Odisea059_final.pdf)\
![image](Odisea060_final.pdf) ![image](Odisea087_final.pdf) ![image](Odisea105_final.pdf)\
![image](Odisea107_final.pdf) ![image](Odisea109_final.pdf) ![image](Odisea110_final.pdf)

![image](Odisea129_final.pdf) ![image](Odisea148_final.pdf) ![image](Odisea187_final.pdf)\
![image](Odisea189_final.pdf) ![image](Odisea223_final.pdf) ![image](Odisea234_final.pdf)\
![image](Odisea247_final.pdf) ![image](Odisea250_final.pdf) ![image](Odisea263_final.pdf)\
![image](Odisea035_final.pdf) ![image](Odisea039_final.pdf) ![image](Odisea041_final.pdf)

![image](Odisea042_final.pdf) ![image](Odisea051_final.pdf) ![image](Odisea082_final.pdf)\
![image](Odisea133_final.pdf) ![image](Odisea162_final.pdf) ![image](Odisea173_final.pdf)\
![image](Odisea190_final.pdf) ![image](Odisea201_final.pdf) ![image](Odisea202_final.pdf)\
![image](Odisea204_final.pdf) ![image](Odisea222_final.pdf) ![image](Odisea230_final.pdf)

![](Odisea233_final.pdf)

![](contrast.pdf)

![image](C4_022_final.pdf) ![image](f23_cont.pdf)

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | ODISEA ID | RA | DEC | Sep | PA | NIR | mm | Category[^4] | Instrument |
|  |  |  |  | (au) | (deg) | flux ratio | flux ratio |  |  |
| 2MASSJ16224539-2431237 | C4_008B | 245.689 | -24.523 | 80 | -41 | 0.17 | \<0.01 | ND | NACO |
| 2MASSJ16230923-2417047 | C4_012B | 245.788 | -24.285 | 226 | 30 | 0.04 | \<0.01 | ND | NIRC2 |
| IRAS16220-2452 | C4_016B | 246.259 | -24.992 | 209 | -98 | 0.1 | 0.29 | Res | NACO |
| 2MASSJ16253253-2326264 | C4_020B | 246.386 | -23.441 | 128 | -141 | 0.17 | \<0.01 | ND | NACO |
| YLW19 | C4_021B | 246.403 | -24.262 | 46 | 59 | 0.11 | \<0.01 | ND | NACO |
| $\blacktriangledown$ BKLTJ162538-242238[^5] | C4_022B | 246.409 | -24.377 | 236 | 172 | 0.08 | 0.04 | Res | NACO |
| 2MASSJ16253943-2326419 | C4_023B | 246.414 | -23.445 | 39 | -67 | 0.97 | \<0.01 | ND | NIRC2 |
| IRAS16226-2420 | C4_024B | 246.415 | -24.443 | 151 | 118 | 0.15 | \<0.01 | ND | NACO |
| WDSJ16264-2421C | C4_037B | 246.598 | -24.350 | 185 | -12 | 0.09 | 0.79 | Res | NIRC2 |
| GY9293 | C4_048B | 246.672 | -24.672 | 9 | \- | 0.99 | \<0.01 | ND | NACO |
| REP40A | C4_050B | 246.678 | -24.342 | 198 | 70 | 0.09 | 0.12 | Res | NACO |
| YLW37 | C4_052B | 246.693 | -24.200 | 57 | 116 | 0.11 | \<0.01 | ND | NACO |
| $\blacktriangledown$ WL2 | C4_053B | 246.702 | -24.478 | 590 | -18 | 0.23 | 0.51 | Res | NACO |
| VSSG31 | C4_065B | 246.767 | -24.475 | 127 | -37 | 0.77 | \<0.01 | ND | NACO |
| YLW10B | C4_078B | 246.814 | -24.445 | 33 | -136 | 0.77 | \<0.01 | Res | NACO |
| YLW45 | C4_105B | 246.916 | -24.721 | 230 | 10 | 0.76 | 0.29 | Res | NACO |
| EM\*SR9 | C4_106B | 246.918 | -24.368 | 89 | -4 | 0.3 | 0.07 | Res | NACO |
| EM\*SR13 | C4_117B | 247.189 | -24.472 | 17 | 79 | 0.16 | 0.14 | Res | NACO |
| GaiaDR26046081782488969600 | C4_120B | 247.434 | -24.689 | 116 | 77 | 0.86 | \<0.01 | ND | NACO |
| V\*V2131Oph | C4_123B | 247.816 | -24.567 | 36 | 162 | 0.25 | \<0.01 | UR | NIRC2 |
| DoAr43 | C4_125B | 247.879 | -24.411 | 339 | 37 | 0.06 | 0.02 | Res | NIRC2 |
| ISO-Oph204 | C4_134B | 247.967 | -24.938 | 498 | -118 | 0.15 | 0.11 | Res | NACO |
| 2MASSJ16233609-2402209 | C5_021B | 245.900 | -24.039 | 251 | -143 | 0.59 | \<0.01 | ND | NACO |
| 2MASSJ16241346-2418219 | C5_025B | 246.056 | -24.306 | 22 | 77 | 0.8 | \<0.01 | ND | NACO |
| $\blacktriangledown$ 2MASSJ16243520-2426196 | C5_027B | 246.147 | -24.439 | 12 | 69 | 0.33 | \<0.01 | ND | NIRC2 |
| $\blacktriangledown$ 2MASSJ16245231-2501269 | C5_028B | 246.218 | -25.024 | 92 | -180 | 0.71 | \<0.01 | ND | NIRC2 |
| $\blacktriangledown$ GaiaDR26049129800516436480 | C5_033B | 246.357 | -24.619 | 48 | -38 | 0.79 | \<0.01 | ND | NIRC2 |
| $\blacktriangledown$ 2MASSJ16262096-2408468 | C5_047B | 246.587 | -24.146 | 734 | -3 | 0.26 | \<0.01 | ND | NACO |
| BBRCG21 | C5_066B | 246.776 | -24.477 | 9 | \- | 0.86 | \<0.01 | ND | NACO |
| $\blacktriangledown$ GY92 259 | C5_072B | 246.852 | -24.493 | 1169 | -92 | 0.85 | \<0.01 | ND | NACO |
| BBRCG60 | C5_076B | 246.886 | -24.556 | 199 | -25 | 0.6 | \<0.01 | ND | NACO |
| 2MASSJ16274164-2435411 | C5_084B | 246.924 | -24.595 | 558 | 149 | 0.3 | \<0.01 | ND | NACO |
| $\blacktriangledown$ GY92 367 | C5_090B | 246.955 | -24.414 | 130 | -66 | 0.39 | \<0.01 | ND | NIRC2 |
| GY92 371 | C5_091B | 246.957 | -24.423 | 54 | -158 | 0.7 | \<0.01 | ND | NACO |
| GY92 397 | C5_092B | 246.980 | -24.478 | 6 | -122 | 0.62 | \<0.01 | UR | NACO |
| EM\*SR20 | C5_106B | 247.136 | -24.379 | 566 | -84 | 0.23 | \<0.01 | ND | NACO |
| $\blacktriangledown$ 2MASS J16290321-2427488 | C5_111B | 247.263 | -24.464 | 39 | -60 | 0.48 | \<0.01 | UR | NIRC2 |
| 2MASS J16290321-2427488 | C5_111C | 247.263 | -24.464 | 495 | 82 | 0.59 | \<0.01 | ND | NIRC2 |
| 2MASSJ16293509-2436104 | C5_114B | 247.396 | -24.603 | 15 | 130 | 0.62 | \<0.01 | ND | NACO |

| Name | ODISEA ID | RA | DEC | Sep (au) | PA (deg) | mm flux ratio |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| 2MASSJ16290321-2427488 | C4_082B | 246.823 | -24.482 | 393 | -50 | 0.15 |

# Results and discussion

In this NIR survey we detected 38 multiple systems: 20 new binaries, 1 triple system, and 17 already-known binaries (cite: 2009ApJ...696L..84C; 2013ApJ...762..100C; 2015ApJ...813...83C; 2017ApJ...851...83C; 2018AJ....155..109S). Two literature binaries were not re-detected by NIR-ODISEA because of lower spatial resolution: 2MASS J162603.0-242336 (C4_028) (cite: 2019ApJ...884...13C) and 2MASS J162654.4-242621 (C5_058) (cite: 2009ApJ...696L..84C). Then, an already known multiple system was not re-observed, the triple hierarchical system EM\*SR24 (C4_062). Also, the object BKLTJ162538-242238 (C4_022), already identified to be a binary by (cite: 2005A&A...437..611R; 2009ApJ...696L..84C) was not re-observed as NACO archive data are available (see Fig. [6](#f:onlyalma), left panel). There is only one multiple system detected in the millimeter which does not have NIR AO-imaging: 2MASSJ16290321-2427488 (C4_082) (see Fig. [6](#f:onlyalma), right panel). This latter appears as a triple system and it is too faint to be observed with NACO or NIRC2.

For each binary system we calculated the position of the companion and its flux ratio with respect to the primary. The projected separation of the companion in au was calculated for each target assuming the distances for each system listed in (cite: 2019ApJ...875L...9W). In Table [\[t:bin\]](#t:bin) we list all these values. Note that the coordinates in RA and Dec correspond to the ALMA coordinates of the primary disc. The properties of the triple system without NIR data, as measured in the ALMA image, are presented in Table [\[t:bin_alma\]](#t:bin_alma).

We found that some companions are sub-stellar, in the brown dwarf regime. To calculate the mass we used the 2MASS K band photometry, available for all the primaries, then we derived the L$^{\prime}$ magnitude using the color for the different spectral types as in (cite: 2015A&A...574A..78S). The spectral type information of each ODISEA target is presented in Ruíz-Rodríguez et al. (in prep). Extinction in K band has also been taken into account. Individual extinction values are listed in (cite: 2020AJ....159..282E) for 20 of the multiple systems. To convert the absolute magnitude into mass we used the AMES-COND evolutionary models by (cite: 2001ApJ...556..357A). The range of masses are 30-50 M$_{\mathrm{Jup}}$. One object, GY92 367 b (C5_090b), is in the planetary regime (14 M$_{\mathrm{Jup}}$), and the primary’s mass derived from the evolutionary models is only 30 M$_{\mathrm{Jup}}$. However, we note that the IR spectrum of the primary does not show the features expected in a brown dwarf (Ruíz-Rodríguez et al. in prep), suggesting that the binary system might be background contamination, a rare but possible occurrence in the ODISEA sample (cite: 2019ApJ...875L...9W).

The NIR images (colour stretch) and their corresponding ALMA 1.3 mm maps (white contours) are overlaid in Figs. [1](#f:mos), [2](#f:mos2), [3](#f:mos3), and [4](#f:mos4). Eight systems are resolved in both the NIR and the millimeter, while five systems are unresolved in the ALMA images. In 11 systems, the companions are undetected in the millimeter at ODISEA sensitivities.

To compare the disc dust masses of single objects to the ones in multiple systems we divided the sample into five categories: single objects, multiple discs where all components are detected and resolved by ALMA, multiple systems unresolved by ALMA, binaries where one or both the components are not detected in the mm, and binaries without IR excess. This last group contains binaries taken from (cite: 2009ApJ...696L..84C) that do not present IR excesses from *Spitzer*. Although these objects are not included in ODISEA, they are taken into account in the following statistical analysis. In the case where each component is resolved, the total mass of the system is the sum of the mass of each component. The five categories of the sample are presented in Table [\[t:cat\]](#t:cat).

| Category | N. of objects | Description |
|:---|:--:|:---|
| Single objects | 252 | Single objects with no IR excess (60) and single objects in NIR-ODISEA (193) |
| Resolved multiple discs (Res) | 11 | Multiple systems where all the components are resolved in the mm |
| Unresolved multiple discs (UR) | 3 | Binary systems where the components are unresolved in the mm |
| ND of component(s) (ND) | 25 | Only the primary is detected in ALMA, or none of the components is detected |
| No IR excess binaries | 26 | Multiple systems excluded from the ALMA sample as they do not present IR excess |

To compute the mass in M$_{\oplus}$ we multiplied the millimeter flux in mJy (cite: 2019ApJ...875L...9W) by 0.58 (cite: 1990AJ.....99..924B; 2005ApJ...631.1134A; 2019MNRAS.482..698C). This conversion from observed mm flux to dust mass assumes a distance of 140 pc, a dust temperature of 20K and suffers from all the uncertainties and caveats discussed in detailed in the references listed above. The histogram of the dust mass of the systems of Ophiuchus is shown in Figure [7](#f:histo). The cumulative probability function for all the categories together is displayed in Fig. [8](#f:cum). For non-detections, we used the Kaplan-Meier (KM) product estimator. The python package lifelines (cite: 2019JOSS....4.1317D) was used to estimate the cumulative distribution functions for each category as shown in Figs. [9](#f:cum_single), [10](#f:cum_a), [11](#f:cum_unre).

Fig. [9](#f:cum_single) shows the cumulative distribution of disc dust masses for single and binary stars, per system (left panel) and per star (right panel). In the latter case, the total disc dust mass are divided by two. The most massive discs (up to masses of $\sim$200 M$_{\oplus}$) are found around single stars. Multiple systems reach lower maximum dust masses, with a maximum total mass of $\sim$50 M$_{\oplus}$.

Note that the distributions of dust masses for single stars and multiple systems are indistinguishable from each other except above M$_{dust}$ $>$ 50 M$_{\oplus}$. The fact that $\lesssim$4$\%$ of singles stars have discs with dust masses $>$ 50 M$_{\oplus}$ suggests that the medium separation binaries (r $>$10 au) only affect a small fraction of the disc population. Fig. [10](#f:cum_a) shows that, in general, discs around the primary star are more massive than the ones around the companion, as found for Taurus (cite: 1996AJ....111.2431J; 2012ApJ...751..115H; 2019ApJ...872..158A). This is consistent with the results on the dependance of disc masses on stellar mass in nearby star-forming regions, according to which the dust mass in discs is roughly proportional to M$_{\star}^{1.5}$ (cite: 2013ApJ...771..129A; 2016ApJ...831..125P). A dedicated publication, Ruíz-Rodríguez et al. (in prep.), will include a spectroscopic study of all the objects of the ODISEA sample, with the spectral type derivation and mass. An in-depth discussion on the dependence of the mass will be presented in that publication.

Fig. [11](#f:cum_unre) shows that tight binaries which are unresolved in the millimeter have total masses M$_{dust}$ $<$ 5 M$_{\oplus}$, while systems where only the primary is detected are in general not very massive. The fact that tight binaries have less massive discs is expected as they should have smaller truncation radii and shorter viscous dissipation timescales (cite: 1977MNRAS.181..441P). Similarly, we speculate that wider binaries where only the primary is detected in the mm are sligthly older or more evolved systems where the discs around the secondaries have already dissipated. In Fig. [12](#f:cum_semi) the cumulative distribution of the semi-major axis of the discs is shown. As expected, discs in multiple systems reach smaller maximum sizes. However, as seen with the dust masses, the difference between single stars and binaries is only seen in the tail of the distributions. Notice that the “ladder shape” is an effect of the ALMA resolution of the two samples. Also, note that a few sources have disc sizes smaller than the ALMA beam. That is because, for detections with very high signal to noise ratios, the ALMA beam can be deconvolved from the image, which allows us to measure the sizes of sources that are smaller than the beam. However, we emphasize that the deconvolved disc sizes must be interpreted with caution.

Figures [13](#f:mass_sep) and  [14](#f:a_sep) show the correlation between the dust mass and the size of the disc as a function of the projected separation between the primary and the companion. Massive, big discs are only found around wide ($>$ 100 au) binary systems. Systems with less massive and unresolved discs are part of close binaries with projected separations between components below 150 au.

(cite: 2012ApJ...751..115H) showed that massive discs (brighter than $>100$ mJy at mm wavelengths) in binaries are only found in Taurus where the stars are very tightly packed and the disc is circumbinary, or around the individual components of wide separation ($>300$ au) binaries. In particular, they identified massive circumbinary discs around 4 systems: GG Tau Aab, MHO 2 AB, UZ Tau Eab and DQ Tau AB. With a separation of  35 au, a system like GG Tau Aab, which has one of the most massive discs in all of Taurus (cite: 2020A&A...639A..62K), would be easily identifiable in the ODISEA sample. Therefore, an analogue system is unlikely to exist in Ophiuchus. However, we note that the other 3 systems with circumbinary discs mentioned above have stellar separations $< 0.1-7$ au and would remain undetectable in our survey. Multi-epoch high-resolution spectroscopy or optical interferometry would be needed to identify very tight binaries and circumbinary discs. Unfortunately, few such observations are available for ODISEA targets, preventing meaningful comparison to the objects in Taurus.

(cite: 2017ApJ...851...83C) studied the effect of multiplicity on a subsample of ODISEA discs. In particular, they restricted the *Spitzer* sample from the “cores to disks” survey (cite: 2009ApJS..181..321E) to the 64 targets with 70 $\mu$m detections in order to increase the expected detection rate at mm wavelengths. This selection criteria, which increased the efficiency of their survey, necessarily introduces a bias towards the largest and most massive discs, where the effect of visual binaries is the strongest. (cite: 2017ApJ...851...83C) conclude that discs in binaries are significantly smaller than those around single stars. While our results are very consistent with those conclusions at extremes of the mass and size distributions, we note that most discs in Ophiuchus are small and low-mass and the effect of visual binaries is likely to be much weaker in the general disc population.

(cite: 2016AJ....152....8K) show that planets can form and survive even in very tight (projected separations of 2-3 au) binary systems. However, the occurrence rate measured by *Kepler* in tight binary systems is 34% that of the wider binaries or single stars. Wider binaries have very similar occurrence rates to single stars, suggesting that when a companion is separated enough it does not affect the disc of the primary. Following (cite: 2016AJ....152....8K), a fifth of all solar-type stars in our Galaxy are most likely not hosting planets due to the presence of a close binary companion. These results on the occurrence of *Kepler* planets could be reconciled with ours, noting that the planets detected by *Kepler* are all within 1 au from their hosts and that our NIR-AO observations are only sensitive to companions with projected separations larger than $\sim$10 au and have been restricted to stars with NIR excess.

The total number of multiple systems of ODISEA is 43, so the occurrence rate is 18% (43/236). Notice that this rate is biased by the fact that, in ODISEA, only Ophiuchus members with discs are included. The objects from (cite: 2009ApJ...696L..84C) that are part of Ophiuchus but are not included in the ODISEA sample because they do not display infrared excess are 86 in total, among which 26 are binaries. Therefore, this indicates that the ocurrence rate of visual binaries in the diskless stars in Ophiuchus is 30$\%$, higher than in the ODISEA sample. A similar result is found for Lupus, where the occurrence rate of multiple systems with discs is 12% (cite: 2021MNRAS.501.2305Z).

The majority of young stars are part of multiple systems, with a frequency twice as high as among solar type main sequence stars (cite: 2013ARA&A..51..269D). In Taurus, for example, the frequency of multiple systems is $\sim$70% (cite: 2011ApJ...731....8K). However, the multiplicity census in Ophiuchus is very incomplete for separations smaller than 10 au and for diskless stars. It is important to mention that (cite: 2019A&A...626A..80C) identified $\sim$200 new members of Ophiuchus using GAIA data, for these objects the study of the multiplicity has not been done so far and a significant fraction of them could be multiple systems.

While some important conclusions can already be derived from the currently available data, additional multiplicity surveys, extending to smaller separations and discless stars, are necessary to obtain a complete picture of the role that companions may have on the planet formation potential of protoplanetary discs. In particular, muti-epoch radial velocity observations will be necessary to identify the companions that are likely to disrupt planet formation at small separations.

![](histo)

![](cum)

![](cum_single)

![](cum_single_median)

![](cum_a)

![](cum_unre)

![](cum_semi)

![](mass_sep)

![](a_maj_sep)

# Summary and conclusion

As part of the ODISEA survey, we have obtained NIR AO imaging at 0.08$''$ resolution for a sample of 164 stars in the Ophiuchus molecular clouds. Combining our results with the ODISEA ALMA 1.3 mm data, archival NIR AO data and multiplicity information from the literature, we present the following results and conclusions:

1.  We detect 20 new binary systems and one new triple system.

2.  Nine companions are in the sub-stellar regime (30-50 M$_{\mathrm{Jup}}$).

3.  The (sub)stellar multiplicity of the ODISEA sample for companions with projected separations in $\sim$ 9 to 1200 au range and flux ratios in the 0.01 to 1 range is 18%. Since all the ODISEA targets have IR excesses, multiple systems might be underrepresented with respect to the general population of young stars in Ophiuchus.

4.  Discs around single stars and stars in multiple systems have similar dust mass cumulative distributions up to 50 M$_{\oplus}$. Disc masses higher than 50 M$_{\oplus}$ and up to 200 M$_{\oplus}$ are only found around single stars.

5.  Primary stars tend to have more massive discs than secondaries.

6.  Discs around single stars can be more extended, with semi-major axes up to 150 au. Discs in multiple systems have a smaller maximum size.

7.  Stellar companions with modest projected separations (10-100 au) are likely to affect the formation of massive planets at large radii (\> 5-50 au) but still allow the formation of terrestrial planets at small projected separation, like those detected by *Kepler*.

8.  Our results are consistent with previous claims that discs in visual binaries are significantly smaller and lower mass than their counterparts around single stars. However, we note that those conclusions only apply to the extremes of the mass and size distributions. Since most discs in Ophiuchus are small and low-mass, the effect of visual binaries seems to be much weaker in the general disc population.

# Acknowledgements

We wish to thank the anonymous referee for their constructive report. A.Z. acknowledges support from the FONDECYT *Iniciación en investigación* project number 11190837. L.C. acknowledges support from FONDECYT Regular number 1171246. S.P. acknowledges support from FONDECYT grant number 1191934 and the Joint Committee of ESO and the Government of Chile. This work has been carried out within the framework of the NCCR PlanetS supported by the Swiss National Science Foundation. G.G. acknowledges the financial support of the SNSF. This paper makes use of the following ALMA data: ADS/JAO.ALMA number 2016.1.00545.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.\

# Data availability

The data underlying this article are available in the article and in its online supplementary material.

# ODISEA objects not observable

| ODISEA ID     |     RA      |     DEC      |
|:--------------|:-----------:|:------------:|
| ODISEA_C4_003 | 16:21:45.13 | -23:42:31.63 |
| ODISEA_C4_042 | 16:26:25.46 | -24:23:01.31 |
| ODISEA_C4_056 | 16:26:51.95 | -24:30:39.45 |
| ODISEA_C4_057 | 16:26:53.47 | -24:32:36.12 |
| ODISEA_C4_058 | 16:26:54.29 | -24:24:37.89 |
| ODISEA_C4_059 | 16:26:54.76 | -24:27:02.14 |
| ODISEA_C4_061 | 16:26:58.27 | -24:37:40.75 |
| ODISEA_C4_063 | 16:27:02.99 | -24:26:14.61 |
| ODISEA_C4_067 | 16:27:05.24 | -24:36:29.59 |
| ODISEA_C4_080 | 16:27:15.87 | -24:25:13.93 |
| ODISEA_C4_081 | 16:27:16.39 | -24:31:14.46 |
| ODISEA_C4_091 | 16:27:26.27 | -24:42:46.09 |
| ODISEA_C4_097 | 16:27:32.12 | -24:29:43.46 |
| ODISEA_C4_111 | 16:27:48.23 | -24:42:25.43 |
| ODISEA_C4_119 | 16:28:57.85 | -24:40:54.88 |
| ODISEA_C4_135 | 16:31:52.45 | -24:55:36.18 |
| ODISEA_C4_144 | 16:39:52.91 | -24:19:31.36 |
| ODISEA_C5_043 | 16:26:18.57 | -24:29:51.32 |
| ODISEA_C5_051 | 16:26:23.81 | -24:18:28.96 |
| ODISEA_C5_056 | 16:26:37.79 | -24:39:03.07 |
| ODISEA_C5_057 | 16:26:40.83 | -24:30:50.83 |
| ODISEA_C5_059 | 16:26:56.35 | -24:41:20.31 |
| ODISEA_C5_060 | 16:26:57.32 | -24:35:38.65 |
| ODISEA_C5_063 | 16:26:58.65 | -24:24:55.37 |
| ODISEA_C5_073 | 16:27:26.21 | -24:19:22.97 |
| ODISEA_C5_077 | 16:27:32.71 | -24:45:00.28 |
| ODISEA_C5_094 | 16:27:58.89 | -24:35:14.57 |
| ODISEA_C5_096 | 16:28:04.53 | -24:34:48.44 |
| ODISEA_C5_126 | 16:31:34.08 | -24:00:59.66 |

: List of the ODISEA objects not observable in the NIR with NACO or NIRC2, then excluded in the statistical analysis.

[^1]: E-mail: alice.zurlo@mail.udp.cl

[^2]: Based on ESO observations (programs number 099.C-0465, 0103.C-0466, 089.D-0199, 075.C-0042, 60.A-9800,079.C-0307), Keck observations (program number GN-2017A-Q-29), ALMA observations (program number 2016.1.00545.S).

[^3]: Number of frames per dithering position

[^4]: See Table [\[t:cat\]](#t:cat) and Sec. [4](#s:res) for more details.

[^5]: For this target K$_s$ filter archive data were used.

</paper>

Write the methods card for this paper.