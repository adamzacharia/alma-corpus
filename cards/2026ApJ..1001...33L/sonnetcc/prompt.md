# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1001...33L\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1001...33L",
 "title": "ALMA FACTS. III. High-resolution CO(2─1)/CO(1─0) Maps of Twelve Nearby Galaxies",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Lee, Amanda M.",
 "n_authors": 7,
 "arxiv_id": "2507.13498",
 "doi": "10.3847/1538-4357/ae4d39",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00886.L",
  "2018.1.01651.S",
  "2022.1.00360.S"
 ]
}
```

Paper text:
<paper>
# ALMA FACTS III. High-Resolution CO(2-1)/CO(1-0) Maps of Twelve Nearby Galaxies

## Abstract

We present early results from a high-resolution analysis ($\sim$100-200pc) of the CO(2-1)/CO(1-0) line ratio in twelve nearby galaxies. We use new ALMA CO(1-0) observations from the Fundamental CO(1-0) Transition Survey (FACTS), and re-imaged CO(2-1) data from PHANGS. We make empirical classifications based on the optical and molecular gas morphologies, which show clear systematic trends in the variation of $R_{21}$ as a function of galactic structure. The sample includes barred and unbarred, and flocculent galaxies. The barred spiral galaxies follow a general trend when the gas exists significantly: $R_{21}$ is high in the center, low along the bar, increases at the bar ends, and then lowers beyond the bar end or flattens in the outer parts of the disk. The structure dependence suggests the importance of galactic dynamics on molecular gas evolution, and consequently on star formation, in galaxies. $R_{21}$ fluctuates in the spiral arms for both barred and unbarred galaxies. Areas around HII regions in some cases appear to show more high-ratio gas. Together, $R_{21}$ varies systematically as a function of galactic structure, dynamics, and star formation activity.

# Introduction

The two lowest transitions, $J$=1-0 and 2-1, of $^{12}$CO are often used to trace the bulk molecular gas in galaxies. Both emissions likely originate from the same region within the molecular gas even when it is not resolved (cite: Sakamoto:1994; Sakamoto:1997; Oka:1998b). Therefore, their line ratio CO(J=2-1)/CO(J=1-0) ($\equiv R_{21}$) can trace and constrain the physical conditions of the molecular gas (cite: Goldreich:1974; Scoville:1974; vanderTak:2007). CO is excited by collisions with H$_{2}$ molecules, and its emissions travel through regions of high CO opacity. Hence, $R_{21}$ is determined by the kinetic temperature $T_{\rm k}$, H$_{2}$ volume density $n_{\rm H_2}$, and the CO column density $N_{\rm CO}$. It can increase due to gas compression before star formation or due to gas heating after star formation (cite: Koda:2012). The variations of $R_{21}$ across galaxies can thus show the evolution of the bulk molecular gas in the galactic disks.

Studies in the Milky Way (MW) have shown systematic variations in $R_{21}$ within and amongst molecular clouds, and in the Galactic disk (cite: Hasegawa:1997). These studies have classified molecular gas according to $R_{21}$ as low-ratio gas (LRG) with $R_{21} < 0.7$, high-ratio gas (HRG) with $R_{21} > 0.7$, and very-high ratio gas (VHRG) $R_{21} > 1.0$. For example, $R_{21}$ varies between and within star-forming and non-star-forming molecular clouds. (cite: Sakamoto:1994) and more recently (cite: Nishimura:2015) mapped the star-forming Orion molecular clouds, and found that $R_{21}$ ranges from 0.5 to 1.0 between the main ridge and peripheries of Orion A. (cite: Falgarone:1998) studied non-star-forming molecular clouds and found they have roughly uniform $R_{21}$ $\sim$ 0.65. In the Galactic disk, $R_{21}$ radially decreases (cite: Sakamoto:1997), with azimuthal variations, i.e., LRG in the interarms and HRG in the spiral arms. In the Galactic center, the molecular gas exhibits distinctive properties than gas in the disk, and can be excited to high $R_{21}>0.7$, and occasionally, very-high ratios $R_{21}>1.0$ (cite: Oka:1996; Oka:1998b; Sawada:2001). Overall, the ratio varies from 0.96 in the central kiloparsec region of the MW, while the typical disk value is 0.6-0.7 (cite: Sawada:2001). VHRG with $R_{21} > 1.0$ is relatively rare and is typically found in the close vicinity of star formation, e.g. due to interaction with supernovae, or in the galactic center (cite: Oka:1996; Seta:1998).

There have been many efforts to characterize $R_{21}$ in external galaxies. However, previous measurements were often hindered by challenges in calibration, especially since $R_{21}$ intrinsically has a relatively small dynamic range (cite: Garcia-Burillo:1993; Crosthwaite:2002; Lundgren:2004; Crosthwaite:2007; Koda:2012; Yajima:2021; Leroy:2022). The calibration issue often led to high $R_{21}>1$ over large regions of the galaxies, seemingly indicating widespread optically-thin CO gas, which is not very likely. Only HRG $\sim$ 0.9 in galactic centers has been a consistent and physically-plausible result (cite: Braine:1992; Leroy:2009). Spatial variations in $R_{21}$ in external galaxies began to become apparent with improvements in calibration and techniques (cite: Koda:2012). In particular, with the advent of ALMA, studies of $R_{21}$ have become increasingly possible (cite: Koda:2020; Egusa:2022; Maeda:2022; den-Brok:2023). There have also been galaxy-wide studies of $R_{21}$ in normal galaxies, (cite: Saintonge:2017; Keenan:2024; Keenan:2025), as well as in extreme systems such as starburst and (ultra)-luminous infrared galaxies (cite: Papadopoulos:2012; Montoya-Arroyave:2023).

High-resolution studies of $R_{21}$($\sim$ 100 pc) remain relatively scarce and are typically case-studies, or due to limited coverage, focus on particular regions in galaxies (cite: Druard:2014; Egusa:2022; Maeda:2022; den-Brok:2023; Koda:2025). These studies have found $R_{21}$ values similar to those of Galactic studies as well as indications of $R_{21}$ trends with respect to galactic structures. Beyond case-studies, it is clear that a survey of $R_{21}$ in nearby galaxies at high-resolution and with well-calibrated data, is needed to understand the general evolution of molecular gas and their physical conditions. While there are existing surveys of $R_{21}$ variations (cite: Yajima:2021; Leroy:2022; den-Brok:2025), they are at lower sensitivity and resolution, or the compared CO(1-0) and CO(2-1) data were often observed from different telescopes. As a result, overall systematic trends were not clear.

In this paper, we analyze $R_{21}$ in twelve nearby galaxies using new high-resolution CO(1-0) data from the ALMA-FACTS survey and reimaged CO(2-1) data from the PHANGS-ALMA survey (cite: Leroy:2021). We present early results, which already empirically show systematic trends as a function of galactic structure. This is the third paper of the ALMA-FACTS Survey. $R_{21}$ on kpc-scales in the same sample of galaxies using the ALMA Total Power (TP) component has been studied (cite: Komugi:2025). We plan multi-wavelength comparisons for future studies.

# Observations and Data Reduction

The FACTS sample of 12 galaxies (Table [\[tab:sample\]](#tab:sample); Figure [\[fig:spitzer\]](#fig:spitzer)) is the complete set of all the galaxies common to the PHANGS-ALMA (cite: Leroy:2021), Spitzer-SINGS (cite: Kennicutt:2003), and Herschel-KINGFISH surveys (cite: Kennicutt:2011), except one galaxy (NGC 4569) whose redshifted frequency is near the edge of the ALMA coverage and is not optimal for ALMA sensitivity. It spans a wide range of spiral arm/bar strength and SF activity. The design of the survey is discussed in a separate summary paper from the FACTS survey (Koda et al. in prep).

This section discusses the data reduction, mainly on the CO(2-1) data (Section [2.1](#sec:CO21red)). The CO(1-0) data reduction is discussed in a separate paper (Koda et al. in prep.), but is practically the same with one note in Section [2.2](#sec:CO10red). This method has been discussed in depth and used by (cite: Koda:2023) and (cite: Koda:2025).

We used a common channel width of $5\, {\rm km \, s^{-1}}$ in CO(1-0) and CO(2-1). After the imaging discussed below, we smoothed the CO(1-0) and CO(2-1) data to a common beam size of 2.5$\ensuremath{''}$ for the line ratio analysis.

Figure [\[fig:spitzer\]](#fig:spitzer) shows the sample in *Spitzer* 3.6 $\mu$m dust emission from S4G (cite: Sheth:2010; S4G) and SINGS (cite: Kennicutt:2003; SINGS) to demonstrate the field-of-view (FoV) of the observations. The FoVs of the 12m+07m CO(2-1) observations (yellow contours), and consequently the $R_{21}$ maps (section [\[sec:r21\]](#sec:r21)), cover the *inner* disks of the galaxies.

## CO(2-1)

The twelve galaxies in our sample were observed in CO(J=2-1) with the ALMA 12m, 07m, and TP arrays, as a part of the PHANGS survey (cite: Leroy:2021). We obtained the raw archival data from projects 2012.1.00650.S (NGC 0628), 2015.1.00925.S (NGC 1512), 2015.1.00956.S (NGC 3351, 3627, 4254, and 4321), 2017.1.00886.L (NGC 1097, 3521, 3621, 4536, 4579, and 4826), and 2018.1.01651.S (NGC 1512). The procedure used for the TP data reduction is described in (cite: Koda:2020). Here, we explain the data reduction of the 12m and 07m data. The 12m and 07m data were calibrated with the Common Astronomy Software Application (cite: CASA:2022) and imaged with Multichannel Image Reconstruction, Image Analysis, and Display (cite: Sault:1995; Sault:1996).

### Calibration

To calibrate the archival measurement sets (MSs), we ran the distributed pipeline scripts from the observatory, either generated for the PI, or a generic pipeline script. Different versions (v.4.7.2, v.5.1.2, and v.5.4.1) of the CASA pipeline were used across the galaxy sample. We used v.4.7.2 for projects 2012.1.00650.S and 2015.1.00925.S, v.4.7.2 and v.5.4.1 for 2015.1.00956.S, v.5.1.2 and v.5.4.1 for 2017.1.00886.L, and v.5.4.1 for 2018.1.01651.S.

To assess the data after calibration, we checked the calibrated amplitudes and phases of the bandpass and gain calibrators (point sources). We considered the calibration successful if their amplitudes were flat and constant as functions of channel and time, and the phases as functions of channel and time were concentrated about 0 degrees. The consistency between the 12m and 07m calibrated data was checked by looking at the galaxy amplitude plotted against uv distance.

For NGC 3621, the same gain calibrator was used across all of the archival 12m data (execution blocks) and had a weak amplitude of $\sim$60 mJy. This resulted in relatively large phase errors even after the calibration. In this case, we also made plots of the bandpass and gain calibrators in the complex plane and checked that their calibrated data points were localized.

The standard flux calibration in the CASA pipeline was used for most galaxies. However, NGC 0628 was observed relatively early in the ALMA observatory operation, and the pipeline calibration returned too low a flux. Therefore, we measured the fluxes of gain and bandpass calibrators with respect to Uranus or Neptune when they were observed in NGC 0628 measurement sets, and applied the measured fluxes to the rest of measurement sets when neither Uranus nor Neptune was included.

### Imaging

The 12m and 07m array data for each galaxy were imaged together in MIRIAD, instead of CASA, because it takes into account spatial variations in the point spread function (PSF) (cite: Koda:2023). To prepare for imaging in MIRIAD, we used the CASA tasks *split* and *mstransform* to split the narrowband spectral window (SPW) containing the CO(2-1) emission out from each 12m and 07m MS, and then to regrid them to a common velocity grid with channel width 5 km/s. These were converted into MIRIAD format. We used the average system temperature T$_{\rm sys}$ and integration times t$_{\rm int}$ from each MS following (cite: Koda:2023). The invert task in MIRIAD was then performed on these 12m and 07m visibilities to produce the CO(2-1) data cubes. We used robust = +2 (approximately) corresponding to natural weighting), cellsize = 0.25’’, and a velocity coverage and width of $5\,\rm km/s$ matching those of the CO(1-0) data cubes (Koda et al. in prep).

We used the mossdi2 task in MIRIAD for cleaning. To identify regions where we may expect significant CO(2-1) emission, we first created masks for each galaxy by using its corresponding CO(1-0) signal-to-noise (SN) data cube (Koda et al. in prep). The mask includes connected regions with at least one pixel with SN $\geq$ 3.5$\sigma$ and 32 pixels with SN $\geq$ 2.5$\sigma$, and then is expanded to include pixels with SN $\geq$ 1.5$\sigma$. Using these masks, the dirty CO(2-1) cubes were cleaned in two steps: \[1\] within the mask and then \[2\] without a mask but cleaning the residual from \[1\] to recover emission that was potentially missed in the first step. We set a gain parameter of 0.05, options=positive (for cleaning within the mask in \[1\]), and 10$^7$ clean components per channel. The residual emission within the mask after the two-step cleaning were about $\sim$0.1$\sigma$.

The cleaned 12m+07m data cubes were combined with the TP data cubes using the immerge task in MIRIAD. We identified velocity channels that were covered by both 12m+07m and TP data cubes, regridded the TP data spatially to the same grid as the 12m+07m data cube, and then combined the TP data cube to the primary-beam corrected 12m+07m cleaned data cube.

The RMS noise per 5 km/s channel for the 12m+07m+TP data was measured with the dirty 12m+07m cube combined with TP data. The RMS is measured in emission-free channels. They are in Table [1](#tab:cubeparam).

## CO(1-0)

The data reduction for CO(1-0) is discussed in a separate paper (Koda et al., in prep.), but is practically the same as the one discussed above. The only difference is the very first step of imaging, where we did not have a reference cube to make a mask. We went through the full imaging process without any mask and generated a 12m+07m+TP cube in CO(1-0). A mask is then made with this cube for the final imaging which was done in the same way as discussed for CO(2-1).

# Maps

Figure [\[fig:spitzer\]](#fig:spitzer) shows the FoVs of the CO(2-1) data on the Spitzer $3.6\mu m$ images. The corresponding RMS per channel maps for CO(2-1) are shown in Figure [\[fig:senrm\]](#fig:senrm). The CO(2-1) data were imaged out to when the sensitivity drops to $1/3 \sim 33\%$ of the peak sensitivity of each pointing (primary beam). However, we restrict the analysis to the area where the sensitivity drops to 40-50% of the peak sensitivity, which is indicated by the black contours in Figure [\[fig:senrm\]](#fig:senrm) (yellow contours in Figure [\[fig:spitzer\]](#fig:spitzer)). For most of the sample, multiple separate observations in CO(2-1) were taken to cover the entire field. Consequently, there are variations in the CO(2-1) sensitivity across the map for each galaxy, but for eleven out of the twelve galaxies, the sensitivities are roughly uniform within $\sim 20-30 \%$ across the entire field, and drop towards the edge. NGC 4321 is an exception with the northern part of the map having about twice lower sensitivity (i.e., twice higher noise) relative to the southern part. NGC 4321 had only two 12m MSs, one for the northern part and the other covering the southern part. Overall, to avoid the low sensitivity edges in the $R_{21}$ analysis, we only include the region where the sensitivity drops to $1/2 \sim 50\%$ of the peak sensitivity for eleven of the galaxies, and to $\sim 40\%$ of the peak sensitivity for NGC 4321.

Figures [1](#fig:co10co21_set1) and [2](#fig:co10co21_set2) show the integrated intensity maps, $I_{\rm{CO(1-0)}}$ and $I_{\rm{CO(2-1)}}$, in CO(1-0) and CO(2-1) for all the 12 galaxies. The coverage of the CO(1-0) observations are slightly larger than the CO(2-1) observations. Unlike CO(2-1), the CO(1-0) observations cover the entire field in each execution, and thus have more or less uniform sensitivity across the field. Hence, the resulting coverage and variations in sensitivity across the $R_{21}$ maps for each galaxy are mainly determined by the CO(2-1) observations.

To make the integrated intensity maps for each galaxy, we smoothed the CO(1-0) and CO(2-1) cubes to a common angular resolution of 2.5$\ensuremath{''}$. We then regridded the CO(2-1) data spatially to the CO(1-0) data and applied a mask to the data cubes. The mask was based on the (cleaned) CO(1-0) signal-to-noise (SN) cube starting from volumes that have at least 80 pixels with $>$ 5.0$\sigma$. This mask was then expanded spatially by 2.5$\ensuremath{''}$ (=10 pixels in length) to include potential diffuse extended emission (if it exists). The mask was not expanded in velocity. After applying this mask, the cubes were integrated along the velocity axis to produce the integrated intensity maps, and corresponding error maps were generated. The error in each pixel is calculated as RMS$\cdot\Delta v\cdot\sqrt{N}$, where RMS is the RMS noise per channel width $\Delta v$, and $N$ is the number of channels included in the velocity integration.

These are shown in Figures [1](#fig:co10co21_set1) and [2](#fig:co10co21_set2). The colorbar scales for $I_{\rm{CO(2-1)}}$ are adjusted to cover 0.7 times the shown range of $I_{\rm{CO(1-0)}}$ for a fairer comparison using a (fiducial) average line ratio $I_{\rm{CO(2-1)}}/I_{\rm{CO(1-0)}}$ of 0.7. The $I_{\rm CO(1-0)}$ and $I_{\rm{CO(2-1)}}$ maps appear similar for prominent structures, although their ratio maps show variations (see Section [\[sec:results\]](#sec:results)).

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Galaxy | Morphology | Distance | $D_{25}$ | Inclination | PA$_{\rm disk}$ | $R_{\rm bar}$ | PA$_{\rm bar}$ | $\epsilon_{\rm bar}$ | Scale (2.5$\ensuremath{''}$) |
|  |  | \[Mpc\] | ($^{\prime}$) | \[$^{\circ}$\] | \[$^{\circ}$\] | \[$\ensuremath{''}$\] | \[$^{\circ}$\] |  | \[pc\] |
| NGC  0628 | SAc | 9.8 (1) | 10.5 | 19.8 | 20 | – | – | – | 119 |
| NGC  1097 | SBb | 15.4 (2) | 9.3 | 54.8 | 133.9 | 95.1 | 141 | 0.65 | 187 |
| NGC  1512 | SBa | 12.6 (2) | 8.9 | 68.3 | 65.2 | 73.5 | 42 | 0.66 | 153 |
| NGC  3351 | SBb | 9.33 (3) | 7.4 | 54.6 | 10.7 | 53.6 | 112 | 0.46 | 113 |
| NGC  3521 | SA$^*$ | 12.1 (2) | 11 | 60.0 | 162.8 | – | – | – | 147 |
| NGC  3621 | SAd | 6.55 (3) | 12.3 | 67.6 | 161.7 | – | – | – | 79 |
| NGC  3627 | SABb | 9.38 (3) | 9.1 | 67.5 | 168.1 | 59.1 | 160 | 0.76 | 114 |
| NGC  4254 | SAc | 13.9 (4) | 5.4 | 20.1 | 66 | – | – | – | 168 |
| NGC  4321 | SABbc | 14.3 (2) | 7.4 | 24.0 | 158 | 54.6 | 108 | 0.59 | 173 |
| NGC  4536 | SABbc | 14.5 (2) | 7.6 | 73.1 | 120.7 | 39.8 | 77 | 0.50 | 176 |
| NGC  4579 | SABb | 16.4 (4) | 5.9 | 41.9 | 90.2 | 42.2 | 53 | 0.48 | 199 |
| NGC  4826 | SAab | 4.41 (5) | 10 | 64.0 | 114.0 | – | – | – | 53 |

: Sample properties of ALMA-FACTS and adopted parameters for the bar. The corresponding spatial resolution at 2.5$\ensuremath{''}$.

Table notes: Columns (2-6) are from (cite: Komugi:2025).\
(1)  Galaxy.\
(2)  Galaxy morphology taken from RC3 (cite: deVaucouleurs:1991). $^{*}$ For NGC 3521, (cite: deVaucouleurs:1991) lists this as a SABbc galaxy, but is treated as an unbarred SA for reasons explained in (cite: Komugi:2025).\
(3)  Redshift-independent distance. Numbers in parentheses is the reference. In order of preference, measurements taken from Cepheid variables, tip of RGB, Tully-Fischer relation. References : 1. (cite: McQuinn:2017), 2. (cite: Tully:2016), 3. (cite: Freedman:2001), 4. (cite: Tully:2013), 5. (cite: Anand:2021).\
(4)  Isophotal diameter at the major axis, taken from RC3 (cite: deVaucouleurs:1991).\
(5)(6)  Inclination and position angle taken from HyperLEDA (cite: Makarov:2014) when available, or from (cite: Kuno:2007), (cite: Sorai:2019).\
(7-9)  Adopted semi-major axis, position-angle, and ellipticity of the bar from (cite: Herrera-Endoqui:2015) for bar region masks (section [\[sec:r21_structures\]](#sec:r21_structures)).\
(10) Spatial resolution at 2.5$\ensuremath{''}$.

# Results 

From the integrated intensity maps in Section [3](#sec:maps), we calculated the line ratio $R_{21}\equiv{I_{\rm{CO(2-1)}}}/{I_{\rm{CO(1-0)}}}$ maps (Figures [3](#fig:r21rgb_set1)-[8](#fig:r21rgb_set6)). We applied a signal-to-noise (SN) cut of $>$5 in both CO(1-0) and CO(2-1). We summarize the $R_{21}$ values and their distribution for each galaxy individually. The spatial resolutions of our maps at the adopted angular resolution of 2.5$\ensuremath{''}$ range from $\sim$ 50-200 pc amongst the sample (Table [\[tab:sample\]](#tab:sample)), larger than the typical size of a molecular cloud. The $R_{21}$ values presented here thus represent the average $R_{21}$ within individual molecular clouds.

## $R_{21}$ Maps and Distributions 

The $R_{21}$ maps for each galaxy and their distributions (histograms), as well as their optical images for comparison, are shown in Figures [3](#fig:r21rgb_set1)-[8](#fig:r21rgb_set6). We summarize the $R_{21}$ variations in each galaxy separately (see Table [\[tab:percentages\]](#tab:percentages)). We tend to find similar trends in each morphological type and galactic structure (e.g., barred, unbarred, spiral), which leads us to classify them according to their optical and molecular gas morphologies (Section [\[sec:disc\]](#sec:disc)).

We divide the molecular gas using the definitions adopted in (cite: Hasegawa:1997). Low-ratio gas (LRG) have $R_{21} < 0.7$ (blue), high-ratio gas (HRG) are in between $0.7 < R_{21} < 1.0$ (red), and very-high-ratio gas (VHRG) have $R_{21} > 1.0$. The division of molecular gas at $R_{21}=0.7$ (white) is motivated both theoretically via the large-velocity gradient (LVG) approximation (cite: Goldreich:1974; Scoville:1974) and observationally first in MW studies (cite: Sakamoto:1997; Oka:1998a; Hasegawa:1997). Typical molecular gas with physical conditions (${n_{\rm{H_2}}, T_{\rm{k}}}$) = (300 cm$^{-3}$, 10 K) have $R_{21}$ $\sim$ 0.6-0.7 (around the LRG-HRG boundary), with the transition from LRG to HRG requiring 2-3x denser and/or hotter gas (cite: Koda:2012). On the other hand, VHRG with $R_{21} > 1.0$ is difficult to achieve, requiring optically thin conditions yet even denser/hotter gas.

We note that the shift from LRG to HRG (or vice-versa) is continuous in the values of $n_{\rm H2}$, $T_{\rm k}$ (and $N_{\rm CO}$) (cite: Koda:2025) and cannot be characterized by single numbers. Nevertheless, a crude guideline would be helpful to gauge the relative physical conditions of LRG and HRG. According to the calculations by (cite: Koda:2012) which considered a range of $N_{\rm CO}$, HRG requires $\sim$2-3 times higher $n_{\rm H2}$ and $T_{\rm k}$ than LRG.

The blue and green histograms show how the bulk of the molecular gas in each galaxy are distributed by area (number) and mass (weighted by I$_{\rm{CO(1-0)}}$), respectively. They show the overall distribution (lightest shade) and the contribution from the central 1 kpc ($R<0.5$ kpc, darkest shade) in the plane of each galaxy, following the definition for central regions adopted in e.g. (cite: Sakamoto:1999; Sheth:2005). The central 1 kpc has been used as a fiducial value for central regions in the literature. However, the size of the central region depends on the galaxy, and based on the $R_{21}$ maps, the region of HRG in the centers of galaxies can extend beyond $R>0.5$ kpc. We thus also show the contribution from the central 2 kpc ($R>1.0$ kpc, hatched, dark shade) in the histograms.

### NGC 0628

NGC 0628 is an isolated spiral galaxy (SAc) with many star-forming regions (HII) along its spiral arms. It does not have a bar structure. At its distance, the angular resolution 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 119 pc. From Figure [1](#fig:co10co21_set1), the molecular gas distribution in NGC 0628 is relatively dim (e.g. compared to the other unbarred galaxies in the sample) in both transitions of CO and its spiral arms appear loosely wound. The stellar spiral arms extend beyond the CO coverage (e.g., Figure [\[fig:spitzer\]](#fig:spitzer)).

The $R_{21}$ measurements are concentrated around the spiral arms due to the sensitivity limitation, with that in the interarm regions only occasionally determined. The disk is dominated by low-ratio gas (Figure [3](#fig:r21rgb_set1)), encompassing 67% of the significantly detected pixels, while high-ratio gas makes up 26% (blue histogram). This is similar for the CO(1-0) intensity weighted distribution (green histogram), with low-ratio gas and high-ratio gas containing 77% and 19% respectively. Over the whole area, the mean $R_{21}$ is 0.65 while the intensity-weighted mean is 0.60.

(cite: Barnes:2023) conducted a detailed case-study of the Phantom Void (1 kpc bubble) in this galaxy. They suggested the bubble is sustained by stellar feedback. In Figure [3](#fig:r21rgb_set1), the molecular gas around there does not show a particular excess in $R_{21}$.

### NGC 1097

NGC 1097 is a strongly barred, interacting spiral galaxy (SBb). At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 187 pc. It is the second-farthest galaxy in the sample. From Figure [1](#fig:co10co21_set1), the molecular gas distribution shows a prominent central core and offset ridges along the bar. The spiral arms extend from the bar ends beyond our coverage (e.g., Figure [\[fig:spitzer\]](#fig:spitzer)). There are also interarm structures (structures between the offset ridges) that often appear filamentary.

$R_{21}$ is high in the center, becomes lower along the bar, and then increases at the bar ends (Figure [3](#fig:r21rgb_set1)). Low-ratio gas and high-ratio gas make up 70% and 26% of the area (blue histogram), respectively. However, the CO(1-0) intensity contained by low-ratio and high-ratio gas are similar, at 47% and 50% respectively (green histogram). Over the whole area, the mean $R_{21}$ is 0.63 while the intensity-weighted mean is 0.71.

From the dark/hatched and darkest regions in the histograms, the central 1-2 kpc ($R<1$ kpc) contains mostly high-ratio gas. The middle panel shows a 1-kpc scale (white bar) in the lower-right corner. The high-ratio gas region, and the central gas concentration, in this galaxy extends even beyond the traditional definition of the central 1 kpc region (cite: Sakamoto:1999; Sheth:2005). In any case, the whole region is located at the roots of the offset ridges.

### NGC 1512

NGC 1512 is a barred spiral galaxy (SBa) with a companion. At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 153 pc. From Figure [1](#fig:co10co21_set1), the molecular gas distribution in NGC 1512 shows a bright core and two offset ridges. The ridges are significantly detected in their inner parts but not in the outer parts. The CO emission re-appears around the bar ends, which continues to fainter spiral arms.

$R_{21}$ is high in the center and becomes lower along the offset ridges (Figure [4](#fig:r21rgb_set2)). The $R_{21}$ along the spiral arms fluctuate between low-ratio and high-ratio, with some high-ratio gas spatially coincident with HII regions. This galaxy also has a central gas concentration and high ratio region larger than the nominal definition of the central 1 kpc. Indeed, the histogram for the central 2 kpc explains most of the HRG. Low-ratio and high-ratio gas encompass 50% and 42% of the area shown, respectively. However, low-ratio gas contain 31% of the CO(1-0) intensity, while 61% is contained within the high-ratio gas. Over the whole area, the mean $R_{21}$ is 0.72 while the intensity-weighted mean is 0.79. From the histograms, the central 1-2 kpc ($R<1.0$ kpc) contain mostly high-ratio gas.

### NGC 3351

NGC 3351 is a barred spiral galaxy (SBb). The angular resolution of 2.5$\ensuremath{''}$ corresponds to 113 pc. From Figure [1](#fig:co10co21_set1), the molecular gas distribution in NGC 3351 has a bright central core and two offset ridges, also surrounded by spiral arms. The offset ridges are bright in the inner part of the bar, but not in the outer part.

In Figure [4](#fig:r21rgb_set2), $R_{21}$ is high in the center and decreases along the offset ridges, but fluctuates in the surrounding spiral arms between low and high ratios. Low-ratio and high-ratio gas make up 58% and 38% of the area shown (blue histogram). However, the amount of low-ratio gas and high-ratio gas contained by the CO(1-0) intensity are 36% and 62%, respectively (green histogram). Over the whole area, the mean $R_{21}$ is 0.69 while the intensity-weighted mean is 0.77. From the histograms, high-ratio gas is concentrated predominantly in the central kiloparsec ($R<0.5$ kpc) region.

(cite: Teng:2022) studied $^{12}{\rm CO}$, $^{13}{\rm CO}$ and $^{18}{\rm CO}$ line ratios (at 2.1$\ensuremath{''}$ resolution; $\sim$ 100 pc) in the central kiloparsec of NGC 3351. They also found that the central region consists of high-ratio gas $R_{21} \sim 1.0$.

### NGC 3521

NGC 3521 is a spiral galaxy (SA) with star-forming (HII) regions spread across its disk. This is an unbarred galaxy. The resolution of 2.5$\ensuremath{''}$ corresponds to 147 pc. The optical image of NGC 3521 shows a flocculent pattern across the disk, but from Figure [1](#fig:co10co21_set1), the molecular gas distribution shows tightly wound spiral arms. Both transitions of CO are detected across the disk, but there is no central gas concentration as seen in the barred galaxies.

$R_{21}$ fluctuates between low and high values along the spiral arms (Figure [5](#fig:r21rgb_set3)). Low-ratio and high-ratio encompass 52% and 45% of the disk respectively (blue histogram). The CO(1-0) intensity contained by the low-ratio and high-ratio gas are 50% and 49% respectively (green histogram). Over the whole area, the mean $R_{21}$ is 0.69 while the intensity-weighted mean is 0.70. As both transitions of CO are not detected in the center, there is little contribution from the central kiloparsec ($R<0.5$ kpc) in the $R_{21}$ distributions, if any.

### NGC 3621

NGC 3621 is another isolated unbarred spiral galaxy (SAd) with star-forming regions spread across its disk. At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 79 pc. It is the second-closest galaxy in the sample.

From Figure [1](#fig:co10co21_set1), the molecular gas structure appears less organized and flocculent. $R_{21}$ fluctuates between low and high values across the disk (Figure [5](#fig:r21rgb_set3)). The spatial distribution of high-ratio gas seems to coincide closely with HII regions. Low-ratio gas and high-ratio gas cover 35% and 58% of the area shown (blue histogram). The CO(1-0) intensity contained by low-ratio and high-ratio gas are 26% and 67% (green histogram). Hence, the majority of the molecular gas by area and by CO(1-0) intensity have high-ratios. Over the whole area, the mean $R_{21}$ is 0.76 while the intensity-weighted mean is 0.78.

### NGC 3627

NGC 3627 is an interacting barred spiral galaxy (SABb) in the Leo Triplet group. At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 114 pc. From Figure [2](#fig:co10co21_set2), the molecular gas distribution in NGC 3627 shows a prominent center and bar, with coherent spiral arms extending from the bar ends. The central region and bar ends are bright in both CO transitions.

$R_{21}$ is high in the center, lowers along the bar, and then increases again at the bar ends (Figure [6](#fig:r21rgb_set4)). The high ratio regions especially at the bar ends and along the spiral arms are located near the HII regions in the optical image. Low-ratio and high-ratio gas encompass 57% and 38% of the galaxy by area (blue histogram), while they contain a similar amount of the CO(1-0) intensity at 48% and 50% (green histogram), respectively. Over the whole area, the mean $R_{21}$ is 0.70 while the intensity-weighted mean is 0.71. The majority of the gas in the central kiloparsec ($R<0.5$ kpc) is high-ratio gas.

(cite: den-Brok:2023) also studied $R_{21}$ in NGC 3627 (as well as other line ratios including CO(3-2) ALMA observations) at $4\ensuremath{''}$ resolution ($\sim$200 pc), and correlated it with star-formation activity (H$\alpha$). They also found high $R_{21}$ in the center and bar-ends, in comparison to the bar and spiral arms.

### NGC 4254

NGC 4254 is an interacting unbarred spiral galaxy (SAc) in the Virgo cluster. The angular resolution of 2.5$\ensuremath{''}$ is 168 pc. From Figure [2](#fig:co10co21_set2), the molecular gas distribution appears asymmetric (cite: Hidaka:2002). The center is bright and spiral arms are apparent in both transitions of CO, but the structures of the spiral arm and tightness differ between the northern and southern parts. The southern spiral arm extends beyond the coverage in CO (e.g., Figure [\[fig:spitzer\]](#fig:spitzer)).

$R_{21}$ fluctuates between low and high-values along the spiral arms in the disk. Low-ratio and high-ratio gas encompass 46% and 49% of the area (blue histogram). Low-ratio and high-ratio gas include 44% and 54% of the CO(1-0) intensity distribution (green histogram), respectively. Over the whole area, the mean $R_{21}$ is 0.72 while the intensity-weighted mean is 0.71. From the histogram, the central kiloparsec ($R<0.5$ kpc) contains mostly high-ratio gas.

### NGC 4321 

NGC 4321 is a barred spiral galaxy (SABbc) in the Virgo cluster. The 2.5$\ensuremath{''}$ resolution corresponds to 173 pc. From Figure [2](#fig:co10co21_set2), the molecular gas distribution shows a bright center and two spiral arms in both CO transitions. The spiral arms extend beyond the CO coverage (e.g., Figure [\[fig:spitzer\]](#fig:spitzer)).

We note that for NGC 4321, the sensitivity in the CO(2-1) data between the northern and southern parts of the galaxy differs by about a factor of two (Figure [\[fig:senrm\]](#fig:senrm)). However, the analysis of the center, bar, and bar ends are all in the southern part where the sensitivity is better. Thus, we discuss the structural variations of $R_{21}$ in this galaxy as we do in the other galaxies.

$R_{21}$ is high in the center, lowers in the bar region, but fluctuates between low and high-values along the spiral arms (Figure [7](#fig:r21rgb_set5)). The southern spiral arm may be showing a potential transition from low to high-ratio gas along the gas flow across the spiral arm (where it runs horizontally in the image), assuming that the gas passes through the arm in the counter-clockwise direction. Low-ratio gas encompasses 56% of the disk while high-ratio gas makes up 35% by area (blue histogram). Likewise, low-ratio gas contains 49% of the CO(1-0) intensity and high-ratio gas contains 44% (green histogram). Most of the molecular gas distribution in NGC 4321 thus has low-ratios by area and by CO(1-0) intensity. Over the whole area, the mean $R_{21}$ is 0.70 while the intensity-weighted mean is 0.71. The central 1-2 kpc is mostly high ratio gas.

### NGC 4536 

NGC 4536 is a barred spiral galaxy (SABbc). At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 176 pc. From Figure [2](#fig:co10co21_set2), the center is bright in both CO transitions and has two spiral arms which extend beyond the CO coverage (e.g., Figure [\[fig:spitzer\]](#fig:spitzer)). The bar is likely running nearly along the minor axis of the disk (cite: Diaz-Garcia:2016), but because the bar appears substantially shorter due to this projection, its orientation can be debated (cite: Mazzalay:2014).

$R_{21}$ is high in the center but fluctuates between low and high-values along the spiral arms (Figure [7](#fig:r21rgb_set5)). The peak of the $R_{21}$ distribution by number is in low-ratio gas (blue histogram), but the peak shifts to high-ratio gas when weighted by CO(1-0) intensity (green histogram). Low-ratio gas and high-ratio gas encompass 68% and 28% of the area. However, low-ratio gas contains 31% of the CO(1-0) intensity distribution, with high-ratio gas containing 53%. Over the whole area, the mean $R_{21}$ is 0.62 while the intensity-weighted mean is 0.79. From the histograms, there is molecular gas concentrated in the central region, with the central 1-2 kpc containing predominantly high/very-high ratio gas.

### NGC 4579

NGC 4579 is a barred spiral galaxy (SABb). At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 199 pc. It is the farthest galaxy in the sample. From Figure [2](#fig:co10co21_set2), the central region is bright in both CO transitions and is surrounded by spiral arms. There is a concentration of gas in the central region. Its structure is spatially resolved and in the CO(1-0) map, it also looks like the roots of offset ridges. We treat it as a central concentration but since the transition from a central concentration to offset ridges is continuous, the boundary cannot be defined clearly.

$R_{21}$ is high in the center. The central gas concentration and high ratio region is also larger than the nominal definition of the central 1 kpc. Indeed, the histogram for the central 2 kpc explains most of the HRG. $R_{21}$ appears to fluctuate along the spiral structure (Figure [8](#fig:r21rgb_set6)). The distribution of the $R_{21}$ in the histogram weighted by CO(1-0) intensity appears doubly-peaked, signifying the difference in the $R_{21}$ distributions between the central region and spiral arms structure. The peaks of the distributions by number and when weighted by CO(1-0) are both in low-ratio gas. Low-ratio gas and high-ratio gas encompass 88% and 10% of the area, respectively (blue histogram). However low-ratio gas contains 74% of the CO(1-0) intensity while high-ratio gas contains 17%. Over the whole area, the mean $R_{21}$ is 0.54 while the intensity-weighted mean is 0.63. From the histograms, the central 1-2 kpc contains mostly high/very-high ratio gas, while the spiral arms contain low-ratio gas.

### NGC 4826

NGC 4826 is an unbarred spiral galaxy (SAab). At its distance, the angular resolution of 2.5$\ensuremath{''}$ corresponds to a spatial resolution of 53 pc. It is the closest galaxy in the sample. The CO coverage of this galaxy in linear size is around the size of the central regions of the other galaxies in the sample. The molecular gas properties presented thus may be more comparable to the centers of galaxies. From Figure [2](#fig:co10co21_set2), this central region is prominent and bright in both CO transitions.

$R_{21}$ is high in the center but fluctuates between low and high in the surrounding regions. Low-ratio and high-ratio gas comprise similar portions of the galaxy by area, at 47% and 49% respectively. However, low-ratio gas contains 36% of the CO(1-0) intensity, while high-ratio gas contains 56%. Over the whole area, the mean $R_{21}$ is 0.72 while the intensity-weighted mean is 0.76. Given the small linear extent of the molecular gas, this skewed distribution towards high-ratio gas may be consistent with those in the central regions of the other galaxies, especially in the barred galaxies (see Figure [10](#fig:R21_size)). This might indicate that once the gas is concentrated in the central regions, $R_{21}$ becomes high independent of the cause of the concentration.

+:------------:+:------------------------------------------------------------------+:----------------------------------------------------------------+:----:+:-----------:+:----------------:+:-----------------------:+
| \(1\)        | \(2\)                                                             | \(3\)                                                           |      | \(4\)       | \(5\)            | \(6\)                   |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| Galaxy       | FoV                                                               | Beam Size                                                       |      | RMS Noise (1$\sigma$)                                    |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+--------------------------------------------+
| 5-7          | Map Area, P.A.                                                    | b$_{\rm{maj}}$, b$_{\rm{min}}$, P.A.                            |      | Native Res. | Smoothed (2.5$\ensuremath{''}$)            |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
|              | \[$\ensuremath{'} \times \ensuremath{'}$, $\ensuremath{^\circ}$\] | \[$\ensuremath{''}$, $\ensuremath{''}$, $\ensuremath{^\circ}$\] |      | \[mK\]      | \[mK\]           | \[M$_\odot$ pc$^{-2}$\] |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| CO(2-1) Data Cube Parameters                                                                                                                                                                                         |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| 1-7 NGC 0628 | 4.3 $\times$ 2.9, 135                                             | 1.48, 0.88, -61.04                                              |      | 74.9        | 24.9             | 0.8, 1.8                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 1097     | 4.4 $\times$ 2.5, 145                                             | 1.54, 1.17, -85.48                                              |      | 46.2        | 18.5             | 0.6, 1.3                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 1512     | 3.1 $\times$ 2.2, 37                                              | 1.23, 0.99,  85.14                                              |      | 71.9        | 21.8             | 0.7, 1.6                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3351     | 2.6 $\times$ 2.5, 0                                               | 1.44, 1.20, -78.83                                              |      | 92.2        | 36.2             | 1.1, 2.6                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3521     | 4.9 $\times$ 2.1, 160                                             | 1.39, 1.12, -81.01                                              |      | 37.9        | 13.6             | 0.4, 1.0                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3621     | 4.2 $\times$ 2.3, 160                                             | 1.55, 1.13, -79.09                                              |      | 31.8        | 12.2             | 0.4, 0.9                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3627     | 4.2 $\times$ 2.3, 0                                               | 1.16, 1.00,  44.23                                              |      | 92.0        | 28.1             | 0.9, 2.0                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4254     | 3.5 $\times$ 3.0, 0                                               | 1.64, 1.17,  57.54                                              |      | 53.1        | 22.4             | 0.7, 1.6                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4321     | 3.6 $\times$ 3.1, 90                                              | 1.13, 1.00, -30.25                                              |      | 102.5       | 28.5             | 0.9, 2.1                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4536     | 4.2 $\times$ 1.8, 119                                             | 1.55, 1.22, -71.86                                              |      | 25.3        | 10.0             | 0.3, 0.7                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4579     | 3.0 $\times$ 2.2, 52                                              | 1.52, 1.33, -73.31                                              |      | 39.3        | 16.8             | 0.5, 1.2                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4826     | 2.8 $\times$ 1.8, 112                                             | 1.35, 1.18, -23.85                                              |      | 53.6        | 19.1             | 0.6, 1.4                |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| 1-7          |                                                                   |                                                                 |      |             |                  |                         |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| 1-7 NGC 0628 | 4.3 $\times$ 3.3, 135                                             | 2.42, 1.94, -56.77                                              |      | 63.8        | 49.0             | 1.1                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 1097     | 4.8 $\times$ 2.8, 145                                             | 2.11, 1.69, 89.44                                               |      | 75.7        | 47.4             | 1.0                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 1512     | 3.1 $\times$ 2.5, 37                                              | 2.24, 1.70, 88.36                                               |      | 60.6        | 39.9             | 0.9                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3351     | 2.9 $\times$ 2.8, 0                                               | 2.10, 2.02, -72.57                                              |      | 60.0        | 42.0             | 0.9                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3521     | 5.3 $\times$ 2.5, 160                                             | 2.18, 1.95, 88.84                                               |      | 67.1        | 47.5             | 1.0                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3621     | 4.4 $\times$ 2.9, 160                                             | 2.16, 1.64, 84.68                                               |      | 75.5        | 47.0             | 1.0                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 3627     | 4.4 $\times$ 2.9, 0                                               | 2.17, 2.08, -46.96                                              |      | 68.8        | 50.4             | 1.1                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4254     | 4.0 $\times$ 3.7, 0                                               | 2.41, 1.95, -49.85                                              |      | 68.9        | 52.8             | 1.1                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4321     | 4.0 $\times$ 3.6, 90                                              | 2.17, 1.95, -58.89                                              |      | 68.7        | 48.2             | 1.0                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4536     | 4.5 $\times$ 2.2, 119                                             | 2.10, 2.01, 85.63                                               |      | 59.2        | 41.3             | 0.9                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4579     | 3.1 $\times$ 2.6, 52                                              | 2.20, 1.93, -51.86                                              |      | 74.0        | 52.2             | 1.1                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+
| NGC 4826     | 3.1 $\times$ 2.1, 112                                             | 2.45, 2.02, -22.37                                              |      | 55.1        | 44.4             | 1.0                     |
+--------------+-------------------------------------------------------------------+-----------------------------------------------------------------+------+-------------+------------------+-------------------------+

: CO(2-1) and CO(1-0) 12m+07m+TP data cube parameters before and after smoothing to 2.5$\ensuremath{''}$ angular resolution. The listed RMS noises are measured in high-sensitivity regions of emission-free channels.

Table notes: (1) Galaxy (2) Rectangular field-of-view (FoV) enclosing the region out to where the sensitivity drops to 50% of the peak sensitivity (40% for NGC 4321 CO(2-1)). The position angle (PA) is along the major axis of the map, counterclockwise from North. (3) Beam Size. (4) RMS Noise for the 12m+07m+TP data in 5 km/s channel at the native resolution. (5)(6) Same as (4) but at the smoothed 2.5$\ensuremath{''}$ resolution and converted to mass surface density assuming $\alpha_{\rm CO(1-0)}$ = 4.35 and fiducial $R_{21}$=0.7 and $R_{21}$=0.3, respectively. The sensitivity limit becomes more important for lower brightness regions, which tend to have lower ratio.

+:-------:+:-----:+:--------------------------------:+:---------------------------------:+:------:+:---------:+:---------:+:-:+:--------:+:---------:+:---------:+
| \(1\)   | \(2\) | \(3\)                            | \(4\)                             | \(5\)  | \(6\)     | \(7\)     |   | \(8\)    | \(9\)     | \(10\)    |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| Galaxy  | Ridge | $\Sigma^{\rm{center}}_{\rm H_2}$ | $\Sigma^{\rm{outside}}_{\rm H_2}$ | $R_{21}$ by Area               |   | $R_{21}$ by $I_{\rm CO}$         |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| 5-7     |       | \[M$_{\odot}$ pc$^{-2}$\]        | \[M$_{\odot}$ pc$^{-2}$\]         | Mean   | LRG \[%\] | HRG \[%\] |   | Mean     | LRG \[%\] | HRG \[%\] |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC0628 | –     | 40                               | 36                                | 0.65   | 67        | 26        |   | 0.60     | 77        | 19        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC1097 | L     | 647                              | 75                                | 0.63   | 70        | 26        |   | 0.71     | 47        | 50        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC1512 | S     | 61                               | 13                                | 0.72   | 50        | 42        |   | 0.79     | 31        | 61        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC3351 | S     | 319                              | 22                                | 0.69   | 58        | 38        |   | 0.77     | 36        | 62        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC3521 | –     | 24                               | 41                                | 0.69   | 52        | 45        |   | 0.70     | 50        | 49        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC3621 | –     | 21                               | 17                                | 0.76   | 35        | 58        |   | 0.78     | 26        | 67        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC3627 | L     | 394                              | 41                                | 0.70   | 57        | 38        |   | 0.71     | 48        | 50        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC4254 | –     | 266                              | 70                                | 0.72   | 46        | 49        |   | 0.71     | 44        | 54        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC4321 | L     | 490                              | 77                                | 0.70   | 56        | 35        |   | 0.71     | 49        | 44        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC4536 | S     | 403                              | 20                                | 0.62   | 68        | 28        |   | 0.79     | 31        | 53        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC4579 | S     | 240                              | 31                                | 0.54   | 88        | 10        |   | 0.63     | 74        | 17        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+
| NGC4826 | –     | 200                              | 62                                | 0.72   | 47        | 49        |   | 0.76     | 36        | 56        |
+---------+-------+----------------------------------+-----------------------------------+--------+-----------+-----------+---+----------+-----------+-----------+

: Area and intensity-weighted $R_{21}$, and the molecular gas surface density within and outside of the fiducial 1 kpc central region.

Table notes:\
(1) Galaxy.\
(2) Long or short (“L" or “S") offset ridges for barred galaxies, based on the molecular gas morphology (Section [\[sec:morphclass\]](#sec:morphclass), Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)).“-" stands for unbarred galaxies.\
(3) Average molecular gas surface density within the central 1 kpc using $\alpha_{\rm CO}$=4.35 in each galaxy.\
(4) Same as (2) but outside of the central 1 kpc.\
(5-7) Mean $R_{21}$, and percentage of molecular gas in LRG and HRG across the whole area of the galaxy.\
(8-10) Same as (5-7) but weighted by $I_{\rm CO(1-0)}$.

# Discussion 

This work presents high-resolution $R_{21}$ maps of a sample of nearby spiral galaxies, an early result from the ALMA-FACTS survey. While we plan on more quantitative analyses in our subsequent papers, the $R_{21}$ maps already offer the first opportunity to compare the variations of $R_{21}$ amongst galaxies at high-resolution ($\sim$ 100-200 pc). The $R_{21}$ maps appear to show some general trends with respect to galactic morphology. While, in general, discussions on morphology tend to be empirical, we attempt to characterize the general trends in terms of galactic structures. In particular, the galactic centers, bars, and spiral arms appear to play their own distinct roles in the organization of the molecular gas conditions traced by $R_{21}$, in addition to their mass distributions as often discussed in the literature. These empirical characterizations also seem consistent with the results in recent case studies at high-resolution ($\sim$ 100-200 pc) (cite: den-Brok:2021; Egusa:2022; Maeda:2022; den-Brok:2023)

We will first explain an idea for the stellar and gas morphology-based classifications and supporting dynamical models in the literature (section [\[sec:morphclass\]](#sec:morphclass)). We then discuss the behaviors of $R_{21}$ in the galactic centers, bars, bar ends, and spiral arms, as well as radial and azimuthal variations of $R_{21}$ along this empirical classification (section [\[sec:struct\]](#sec:struct)).

## Morphology-Based Classification

For characterizing general trends in $R_{21}$, we rearrange the sample galaxies based on (1) their optical morphologies and (2) molecular gas morphologies (i.e., molecular gas distributions) with emphasis on bar and spiral arm structures. Their optical morphologies are classified as barred (SB and SAB) and unbarred spiral galaxies (SA), which appear to primarily determine the behaviors of $R_{21}$ across the disks. For barred galaxies, there is a suggested picture on the gas evolutionary sequence based on hydrodynamical simulations and observations (cite: Sakamoto:1999; Sheth:2005; Yu:2022), which appears to help understand the behaviors of $R_{21}$ amongst the barred galaxies. We summarize this sequence and discuss our arrangement of the sample galaxies.

### Bar-Driven Gas Transport 

In the bar-driven gas transport model, the stellar bar potential organizes the gas motions to form the offset ridges on the leading side of the bar. The interactions between the gas along the offset ridges (e.g., shocks) and/or with the stellar potential (e.g., torque) cause the gas to lose angular momentum, and the gas falls towards the center from the offset ridges (cite: Wada:1994; Sheth:2002). This picture is supported by observations. (cite: Sakamoto:1999) and (cite: Sheth:2005) studied the central regions of barred spiral galaxies, and found that the central kiloparsec of barred spiral galaxies have higher concentrations of molecular gas than their unbarred counterparts. They, and others in the literature, attributed the concentrations of molecular gas in their central regions to the bar-driven gas transport by stellar bars to the centers (cite: Sakamoto:1999; Sheth:2005; Garcia-Burillo:2009; Sormani:2023). In this process, the amount of gas in the bar should decrease, if no gas is inflowing from outside the bar.

### Classification 

Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph) shows the $R_{21}$ maps from Section [\[sec:results\]](#sec:results) arranged primarily by their optical morphological classifications (SB, SAB, or SA), and secondarily by their gas morphology for the barred galaxies. The secondary part is based on the presence or absence of gas along the offset ridges. Even when the offset ridges are not present, all of the barred galaxies have central condensations of gas, and thus fit within the bar-driven gas transport picture, if the absence of the ridges is due to the gas inflow. Hence, using the optical and gas morphological classifications, we arrange the $R_{21}$ maps (ordered by galaxy number) starting from barred galaxies with shorter offset ridges, i.e., lacking molecular gas between the central region and spiral arms, to barred galaxies with longer offset ridges and having clearer spiral arms extending from the bar ends, and then to the unbarred galaxies.

In the arranged gas morphological sequence of Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph), the barred galaxies NGC 1512, NGC 3351, NGC4579, and NGC 4536 (top row) have shorter offset ridges and/or show an absence of gas between the central regions and their surrounding spiral arm structures. Following these, the barred galaxies NGC 1097, NGC 3627, and NGC 4321 (left middle row) show longer offset ridges and have clearer spiral arms extending out of the bar ends. The rest of the galaxies are unbarred (the bottom row and the rightmost in the middle row). Figure [10](#fig:R21_size) is the same as Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph), but shows the galaxies on the same physical scale. NGC 4826 (unbarred) is placed succeeding the barred galaxies (middle row) since it has a central gas condensation/region with a linear size more comparable to those of the barred galaxies (e.g., Section [\[sec:r21\]](#sec:r21) and Figure [10](#fig:R21_size)).

The barred galaxies have higher average $I_{\rm CO(1-0)}$ surface brightness in their central regions than the unbarred galaxies. If we simply assume the Milky-Way CO-to-H$_{2}$ conversion factor of $\alpha_{\rm CO}$ = 4.35 M$_{\odot}$pc$^{-2}$ $\cdot [\rm K\cdot km \cdot s^{-1}]^{-1}$ (cite: Bolatto:2013), then this translates to higher average molecular gas surface densities in the centers of the barred galaxies (Table [\[tab:percentages\]](#tab:percentages)). This is consistent with (cite: Sakamoto:1999) and (cite: Sheth:2005), which was interpreted as an outcome of bar-driven gas transport towards the center. We note the conversion of surface brightness to molecular mass has the caveat that $\alpha_{\rm CO}$ may vary especially in the galaxy centers (cite: Sandstrom:2013; Teng:2023).

In the following sections, we discuss $R_{21}$ along this sequence to understand the observed trends in $R_{21}$ as a function of structure.

## Structural Dependence of $R_{21}$ 

We discuss the overall trends in $R_{21}$ seen amongst the barred and unbarred galaxies, and then within each galactic structure (center, bar, bar ends, and spiral arms). Figure [9](#fig:radialdist_arrangedbygasmorph) shows the radial distributions in two ways: as scatter plots to show the sampling (i.e., data density; top) and as density plots with the same data normalized by the peak number of points per radial bin to show the radial trend (bottom). They are arranged in the same order as Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph). The binned means (area-weighted) are shown in blue and orange for the barred galaxies with short or long ridges respectively, and teal for unbarred galaxies. The secondary x-axis is in arcseconds, and the blue dotted line indicates the bar length.

Overall, the barred galaxies (top and left middle rows) follow a general trend: $R_{21}$ is high in the center ($R_{21} \sim$ 1.0), low along the bar ($R_{21} \sim 0.6-0.7)$, increases at the bar ends ($R_{21} \gtrsim$ 0.7), and then lowers beyond the bar ends or flattens, with fluctuations in the spiral arms. The higher ratios in the bar ends are remarkable, given that the bar end areas are only in a small azimuthal range but still appear as high $R_{21}$ in these azimuthally-averaged plots. The radial distributions of $R_{21}$ in the unbarred galaxies (right middle and bottom rows) look similar to the outer parts of the barred galaxies (cite: Komugi:2025).

There are also some variations in the azimuthal direction in the sample galaxies. However, due to the sensitivity limitations, most interarm regions of the galaxies are not readily detected (Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)). Variations in the azimuthal direction can be seen as scatters at each radius in the radial distributions. With these trends in mind, we discuss $R_{21}$ as a function of structure in the following sections.

### Central Regions: High $R_{21}$ 

It has been known that barred galaxies often have high gas concentrations in their central regions (cite: Sakamoto:1999; Sheth:2005; Yu:2022). The same central gas concentrations are apparent in the barred galaxies in our observations (Figures [1](#fig:co10co21_set1)-[2](#fig:co10co21_set2)). In addition, the sample of the unbarred spiral galaxies do not show such gas concentrations at the centers besides NGC 4826. This study (section [\[sec:r21\]](#sec:r21)) shows that the central 1-2 kiloparsec regions within barred galaxies also comprise of high/very-high ratio gas, and that the gas physical conditions change within the central gas condensations. $R_{21}$ is elevated significantly and consistently in the centers, which has also been found in earlier studies, e.g. (cite: Braine:1992; Leroy:2009; den-Brok:2021). The elevated line-ratios in their galactic centers are clear in the radial distributions.

The presence of high-ratio gas across these central regions indicates that the molecular gas there has higher $n_{\rm{H2}}$ and $T_{\rm{k}}$ and is thus denser and/or warmer than the typical molecular gas conditions, ($n_{\rm H_2}$, $T_{\rm k}$)=(300 cm$^{-3}$, 10 K), in the disks (cite: Koda:2012).

The high ratios may be the result of dynamical processes and/or on-going star formation in the galaxy centers. As a dynamical process, the high ratios in the central regions of the barred galaxies across the sample could be due to the bar-driven gas transport to the centers, discussed in section [\[sec:gasevol\]](#sec:gasevol). The influence of the bar may compress the gas (increase in gas density) and/or trigger star formation in galactic centers (increase in gas kinetic temperature by stellar feedback) and lead to the high-ratios. The enhancement of star formation in the centers of barred galaxies has been studied e.g., in (cite: Ho:1997).

Amongst the sample galaxies, NGC 1097, NGC 3627, NGC 4579, and NGC 4826 (as well as NGC 3621) are classified as having AGN (cite: Veron-Cetty:2010) and this may also be a cause of the high $R_{21}$ there. However, even the galaxies without AGN often show high $R_{21}$ in the central $\sim 1-2$kpc when they have the central gas concentrations. Thus, AGN may not be the only cause of high $R_{21}$ in central regions.

It may also be worth noting that NGC 4826 is an unbarred spiral galaxy in the optical classification, but has a central concentration of high-ratio gas. Although it is only one case, its presence may indicate that the high ratio is due to the local environment of the central region (e.g., strong shears or tidal forces), rather than the compression due to the infalling gas.

### Along the Bar: Low $R_{21}$ 

Bar regions overall show lower $R_{21}$ ($R_{21} \sim 0.6$). This is evident in the spatial and radial distributions of $R_{21}$ (Figures [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)-[9](#fig:radialdist_arrangedbygasmorph)), even though there is molecular gas concentrated along the offset ridges and bar (Figures [1](#fig:co10co21_set1)-[2](#fig:co10co21_set2)). This seems to be a general trend amongst barred spiral galaxies, including the ones in other studies: NGC 1300, NGC 1365, NGC 2903, NGC 3627, and NGC 5236 (M83) (cite: Maeda:2022; Egusa:2022; den-Brok:2023; Koda:2025). The low $R_{21}$ in the bar region is seen even when the offset ridges do not have much gas (NGC 1512, NGC 3351, and NGC 4579; top row in Figures [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)-[9](#fig:radialdist_arrangedbygasmorph)).

The lower $R_{21}$ suggests that $n_{\rm H_2}$ and $T_{\rm k}$ remain low in the bar (cite: Koda:2012), even when the gas is concentrated along the offset ridges. This may explain why star formation efficiency is often low in the bar regions of galaxies (cite: Downes:1996; Koda:2006; Momose:2010; Maeda:2023). Recently, (cite: Rodriguez:2024) analyzed the 3.3 $\mu$m polycyclic aromatic hydrocarbon (PAH) emission in 19 nearby star-forming galaxies to identify star clusters in their early dust-embedded phases. They also found that, in general, there is an absence of PAH emitters in bars (including our FACTS sample: NGC 1512, NGC 3351, NGC 3627, and NGC 4321).

The generally low $R_{21}$ along the offset ridges may also be important in considering gas dynamics within the bar. It has been suggested that the offset ridges are regions of strong shocks (cite: Athanassoula:1992a; Athanassoula:1992b; Sellwood:1993), which should naturally increase $n_{\rm H_2}$ and $T_{\rm k}$, and hence, $R_{21}$. Instead, the gas concentration along the offset ridges may be caused by the mere crowding of gas orbits with only occasional collisions (cite: Wada:1994; Koda:2006), which could keep $R_{21}$ low in general. In the case of orbit crowding, the gas falls towards the center by the loss of angular momentum due to the gravitational torque of the stellar bar potential, as the gas resides longer on the leading side of the bar (cite: Wada:1994). This gas infall process would take longer than the rapid gas infall by the strong shocks, which could make offset ridges live longer, and appear more frequently in a sample of barred galaxies. In the future, it may be interesting to check the frequency of the offset ridges (from long to short to none), in a larger sample.

### Bar Ends: High $R_{21}$ 

Bar ends are the transition regions from the offset ridges in the bar to spiral arms outside the bar. The gas often builds up around the bar ends (cite: Sheth:2002). Even when the offset ridges fade away at their further ends, the CO emission often starts to re-appear around the bar ends and extends along the spiral arms (e.g., NGC 1512, NGC 3351). Star formation is likewise evident at the bar ends in the optical images e.g. for NGC 1097 and NGC 3627 (Figures [3](#fig:r21rgb_set1) and [6](#fig:r21rgb_set4)). (cite: Rodriguez:2024) show there is a clustering of 3.3 $\mu$m PAH emitters at the bar ends of NGC 3627.

The bar ends also show higher $R_{21}$ spatially and in the radial distributions often $R_{21} \gtrsim 0.7$) (Figures [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)-[9](#fig:radialdist_arrangedbygasmorph)). This is most apparent in the galaxies with longer offset ridges (see also section [\[sec:r21_structures\]](#sec:r21_structures)). The high ratios again suggest that the molecular gas located there has relatively higher $n_{\rm H_2}$ and/or $T_{\rm k}$ (cite: Koda:2012). When there is not much gas in the bar region (as in the short-offset ridge galaxies) it is difficult to assess. NGC 1512 shows an increase towards the bar ends in its radial profile, but this is unclear in NGC 3351 and NGC 4579. NGC 4536 is affected by projection effects (section [\[sec:ngc4536\]](#sec:ngc4536)).

The stellar bar pattern should have a constant pattern speed to maintain its linear structure over time. The bar end is often considered to be around the co-rotation radius where the orbital speed of gas and stars are synchronized with the bar pattern speed (it is at $\sim$80% of the co-rotation radius according to (cite: Athanassoula:1992a; Athanassoula:1992b)). Once the gas gets into the bar end, it will likely reside there for a long time. This explains the gas concentrations around the bar ends. The combination of the high gas concentration and long residential time may trigger local gravitational collapses, which may explain the high $R_{21}$ and star formation (cite: Maeda:2025). This is, of course, a hypothesis and needs to be verified by future observational and theoretical studies.

### Spiral Arms 

Spiral arms are also where the gas builds up. $R_{21}$ fluctuates between low and high values along the molecular gas spiral arms (Figures [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)-[9](#fig:radialdist_arrangedbygasmorph)) (cite: Druard:2014; Koda:2025). It is remarkable that the fluctuations appear similar between the spiral arms in the barred galaxies and those of the unbarred galaxies. High-ratio gas in these regions sometimes appear to be associated with HII regions, and thus, star formation. This has been found in Galactic and extragalactic studies (cite: Sakamoto:1994; Seta:1998; Koda:2012; Koda:2020; Egusa:2022; Koda:2025).

These spatial correlations provide an important benchmark for understanding the interplay between molecular gas evolution and star formation in spiral galaxies. However, their causality needs to be discussed with more detailed comparisons with multi-wavelength data or with future observations. In fact, the galactic potential, such as the spiral arm potential, can control gas dynamics/flows, which can compress the gas, increase $R_{21}$, and trigger star formation. On the other hand, the galactic structures can help in assembling the gas to form stars, and their feedback can increase $R_{21}$.

In the analysis of the nearby barred spiral galaxy M83, which had higher resolution and sensitivity, (cite: Koda:2025) recently found that $R_{21}$ changes systematically from a low ratio in the interarm regions to high ratio in the bar and spiral arms even without star formation. They concluded that the large-scale galactic dynamics plays an important role in the evolution of molecular gas, in addition to the local impacts of stellar feedback. In this sample, NGC 1097, NGC 3627, and NGC 4321 show more coherent molecular spiral arms, with some parts possibly showing a similar transition from low to high $R_{21}$.

### $R_{21}$ by Structure 

$R_{21}$ clearly varies within each galaxy. The dependence on galactic structures (center, bar, bar ends, and spiral arms) is apparent in Section [\[sec:r21\]](#sec:r21). For a more quantitative comparison, we define regions to enclose the structures in each galaxy (Figure [\[fig:R21_arrangedbygasmorph\]](#fig:R21_arrangedbygasmorph)). We created masks for the center, bar, and bar ends. Our adopted region definitions are not meant to be exact boundaries, but are an attempt to capture the rough areas of the structures of interest. We describe the definitions and $R_{21}$ distribution in each region below.

For the central regions, we adopt either 1 or 2 kpc diameter areas around the galactic center (projected in the sky). We adopt the fiducial 1 kpc for all *unbarred* galaxies. For the *barred* galaxies, we showed that the size of the high-ratio region in the center sometimes extends beyond this in section [\[sec:r21\]](#sec:r21). We adopt 2 kpc for all barred galaxies except for NGC3351 and NGC3627.

For the bar and bar ends, we define regions based on the cataloged bar structure (cyan ellipse) in (cite: Herrera-Endoqui:2015), which is based on Spitzer 3.6 $\mu$m from S4G (cite: Sheth:2010; S4G). We use their on-sky PA$_{\rm bar}$, semi-major axis $R_{\rm bar}$, and ellipticity (see Table [\[tab:sample\]](#tab:sample)). The bar region is enclosed by the cyan ellipse but does not include the bar ends (magenta). The bar ends are 2 kpc circles centered on the “tips” of the ellipse.

We adopt the definitions of the spiral arms from (cite: Querejeta:2021). The area outside the center, bar, bar end, and spiral arms is analyzed as interarm regions.

Using these definitions, we compared the $R_{21}$ distributions for adjacent structure pairs (center-bar, bar-bar end, and bar end-spiral arm) and the spiral arm-interarm regions by performing the Kolmogorov-Smirnov (KS) two-sample test using the *ks_2samp* function in *scipy*. The null hypothesis is that the two samples originate from the same parent distribution. We applied this test including only every fifth pixel (Nyquist sampling) (1) within each galaxy and (2) all galaxies combined. We find p-values $<0.05$ (majority lower than $<10^{-6}$) meaning the null hypothesis can be rejected in all the structure pairs compared in all galaxies, except in two cases: bar-bar end in NGC 1512 (p-value $\sim$ 0.4) and bar end-spiral arm in NGC 4536 (p-value $\sim$ 0.3). In NGC 1512 there is not much gas in the bar, and in NGC 4536 the bar-end definition is ambiguous due to its projection (section [\[sec:ngc4536\]](#sec:ngc4536)). (Note: with full-beam sampling, the NGC1097 bar-bar end and NGC4321 bar end-spiral arm comparisons also show p-values $>$ 0.05. However, p-values are still $<0.05$ in most cases, and the overall discussion does not change.)

Figure [11](#fig:R21_structures_hist) shows the corresponding $R_{21}$ distributions. They reflect the general trends discussed in section [\[sec:struct\]](#sec:struct). Central regions of barred galaxies show high $R_{21} > 0.7$. Bars show mostly low $R_{21} < 0.7$. Bar ends for the galaxies with relatively longer offset ridges more often show high $R_{21} > 0.7$. We note that the longer offset ridged galaxies contribute the most in panels (c-d) because more emission is detected there (see section [\[sec:barend\]](#sec:barend)).

The KS test also suggests the arm-interarm distributions are different (p-values $< 10^{-6}$). The histogram for the interarms is slightly but systematically shifted towards lower $R_{21}$ (Figure [11](#fig:R21_structures_hist)). The contrast could be higher if the sensitivity is higher because low brightness/density gas, expected more in the interarms, tends to have lower $R_{21}$. We note that our equal flux-based cut in CO(1-0) and CO(2-1) (SN$>$5) practically corresponds to a higher density threshold for CO(2-1) if $R_{21}$ is low (Table [1](#tab:cubeparam), column (6)).

We note that (cite: Querejeta:2021) also defined the inner structures (the center, bar, and bar ends). Their bar ends are defined as overlap regions of bar and spiral arms, but are not identified when their bar is defined too short to reach the spiral arms. This does not assure a consistent analysis across the galaxy sample, and thus, we adopted the above definitions. The trends of $R_{21}$ discussed above for the centers and bars are the same when we use their definitions.

# Systematic Trends and Comparison to Literature 

In sections [\[sec:results\]](#sec:results) and [\[sec:disc\]](#sec:disc), we showed that $R_{21}$ systematically varies as a function of galactic structure in the twelve nearby spiral galaxies. Such structural variations were not previously clear from single-dish surveys (cite: den-Brok:2021; Yajima:2021; Leroy:2022). (cite: Komugi:2025) conducted the $R_{21}$ analysis using the ALMA-TP component only. They were not able to resolve the galactic structures with their coarser resolution, but found that most of the barred galaxies showed steeper radial gradients, whereas all the unbarred galaxies showed flat or shallower gradients.

This general trend of structure-dependent variations is consistent with the results from high-resolution ALMA case studies. For example, (cite: Egusa:2022) studied NGC 1365 at $\sim$ 200 pc resolution and found high $R_{21}$ $>$ 0.7 in the center while it is low $R_{21}$ $<$ 0.7 in the bar region. (cite: Maeda:2022) studied NGC 1300 at $\sim$100 pc resolution, finding $R_{21}$ to be low along the bar $\sim 0.50$, high $\sim 0.72$ in the bar end, and $\sim 0.60$ in the spiral arm. While these studies covered only small regions within individual galaxies, the results are consistent with the general trend. Furthermore, (cite: den-Brok:2023) studied $R_{21}$ in the disk of NGC 3627 at $\sim$200 pc resolution and found a consistent trend, with high $R_{21}$ $\sim$ 0.90 in the center, low $\sim$ 0.70 along the bar, and then increasing again at the bar ends to $\sim$ 0.86, and high $\sim$ 0.75 in the spiral arms. The same trend was also found in M83 at a higher 46 pc resolution (cite: Koda:2025). The high $R_{21}$ in the centers of the barred galaxies could explain the steeper radial gradients found by (cite: Komugi:2025).

Most of these studies, including FACTS, have insufficient sensitivity to detect interarm emission; but when it is detected, it appears to have low-ratios. The M83 study by (cite: Koda:2025) has higher sensitivity to detect faint interarm gas, which clearly exhibits low-ratios. As the trends amongst bright structures in M83 is similar to that of the FACTS galaxies and other high-resolution case-studies, we conclude that the observed trends in $R_{21}$ are common amongst all nearby (barred) star-forming spiral galaxies.

# Summary

In this study, we analyzed the CO(2-1)/CO(1-0) line ratio in twelve nearby galaxies from the Fundamental CO(1-0) Transition Survey (FACTS) in conjunction with the PHANGS CO(2-1) survey. We focused on empirical trends and showed that $R_{21}$ systematically varies as a function of galactic structures in twelve nearby galaxies. To characterize the observed structural variations, we made empirical classifications of the galaxies based on their optical morphologies (SB, SAB, or SA), and their molecular gas morphologies for the barred galaxies, depending on the presence or absence of molecular offset ridges. The molecular gas morphological sequence may be explained as an evolutionary sequence by the bar-driven gas transport model. We discussed $R_{21}$ in the context of this sequence.

From the radial distributions of $R_{21}$, the barred galaxies follow a general trend: $R_{21}$ is high in the central 1-2 kpc regions $\sim$ 1.0, low along the bar offset ridges $\sim$ 0.6, increases at the bar ends often $\gtrsim$ 0.7, and then declines in the rest of the disk with fluctuations along the spiral arms. The radial distributions of the unbarred galaxies fluctuate in $R_{21}$ and are similar to the outer parts (spiral arms) of the barred galaxies.

High $R_{21}$ in the central 1-2 kpc regions is always associated with the central gas condensations in the barred galaxies. NGC 4826 is the only unbarred spiral galaxy in our sample that shows the central condensation and high $R_{21}$. Low $R_{21}$ along the bar offset ridges suggest that the gas density and/or temperature are lower there (cite: Koda:2012), which may explain the reduced star formation efficiency along bars as suggested by previous studies. Bar ends show high $R_{21}$, indicating increased density and/or temperature. In spiral arms, $R_{21}$ fluctuates, presumably due to the impacts of star-formation activity or galactic dynamics.

The $R_{21}$ variations found in this study are consistent with previous high-resolution ALMA case studies (NGC 1300, NGC 1365, NGC 3627, and M83). In particular, while interarm emission is not well-detected in this study due to the sensitivity limitation, all the other structures show trends in $R_{21}$ similar to that observed in a recent case-study of M83 which had higher sensitivity and resolution (cite: Koda:2025). The common trends in $R_{21}$ amongst the FACTS sample, M83, and a few other barred galaxies suggests that they may be common amongst all nearby (barred) star-forming galaxies.

We have shown that the variations in $R_{21}$ appear to depend on the galactic structures (the central regions, bar offset ridges, bar ends, and spiral arms). The structure dependence may also suggest the importance of galactic dynamics on the molecular gas evolution and star formation. We plan more detailed multi-wavelength comparisons in our future publications from the FACTS survey.

![](updated_250930_ngc0628_1097_1512_3351_3521_3621_co10_co21.png)

![](updated_250930_ngc3627_4254_4321_4536_4579_4826_co10_co21.png)

![](updated_251005_SN5both_rgb_r21_hist_Rlt0.5_1.0kpc_ngc0628_1097.png)

![](updated_251005_SN5both_rgb_r21_hist_Rlt0.5_1.0kpc_ngc1512_3351.png)

![](updated_251005_SN5both_rgb_r21_hist_Rlt0.5_1.0kpc_ngc3521_3621)

![](updated_251005_SN5both_rgb_r21_hist_Rlt0.5_1.0kpc_ngc3627_4254.png)

![](updated_251005_SN5both_rgb_r21_hist_Rlt0.5_1.0kpc_ngc4321_4536.png)

![](updated_251220_SN5both_rgb_r21_hist_Rlt0.5_1.0kpc_ngc4579_4826.png)

![](all_radial_SN5both_251217_stretched.png)

![](251004_SN5both_relativephysicalsize_arrangedbygasmorph2.png)

![](r21_structures_histogram_SN5both_251217.png)

natexlab

(ref: Anand:2021) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: Athanassoula:1992a) Athanassoula, E. 1992a, MNRAS, 259, 328, doi: [`10.1093/mnras/259.2.328`](http://doi.org/10.1093/mnras/259.2.328)

(ref: Athanassoula:1992b) —. 1992b, MNRAS, 259, 345, doi: [`10.1093/mnras/259.2.345`](http://doi.org/10.1093/mnras/259.2.345)

(ref: Barnes:2023) Barnes, A. T., Watkins, E. J., Meidt, S. E., et al. 2023, ApJL, 944, L22, doi: [`10.3847/2041-8213/aca7b9`](http://doi.org/10.3847/2041-8213/aca7b9)

(ref: Bolatto:2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Braine:1992) Braine, J., & Combes, F. 1992, A&A, 264, 433

(ref: CASA:2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Crosthwaite:2007) Crosthwaite, L. P., & Turner, J. L. 2007, AJ, 134, 1827, doi: [`10.1086/521645`](http://doi.org/10.1086/521645)

(ref: Crosthwaite:2002) Crosthwaite, L. P., Turner, J. L., Buchholz, L., Ho, P. T. P., & Martin, R. N. 2002, AJ, 123, 1892, doi: [`10.1086/339479`](http://doi.org/10.1086/339479)

(ref: deVaucouleurs:1991) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, Herold G., J., et al. 1991, Third Reference Catalogue of Bright Galaxies

(ref: den-Brok:2025) den Brok, J., Oakes, E. K., Leroy, A. K., et al. 2025, ApJ, 988, 162, doi: [`10.3847/1538-4357/addf4c`](http://doi.org/10.3847/1538-4357/addf4c)

(ref: den-Brok:2021) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221, doi: [`10.1093/mnras/stab859`](http://doi.org/10.1093/mnras/stab859)

(ref: den-Brok:2023) den Brok, J. S., Leroy, A. K., Usero, A., et al. 2023, MNRAS, 526, 6347, doi: [`10.1093/mnras/stad3091`](http://doi.org/10.1093/mnras/stad3091)

(ref: Diaz-Garcia:2016) Dı́az-Garcı́a, S., Salo, H., Laurikainen, E., & Herrera-Endoqui, M. 2016, A&A, 587, A160, doi: [`10.1051/0004-6361/201526161`](http://doi.org/10.1051/0004-6361/201526161)

(ref: Downes:1996) Downes, D., Reynaud, D., Solomon, P. M., & Radford, S. J. E. 1996, ApJ, 461, 186, doi: [`10.1086/177046`](http://doi.org/10.1086/177046)

(ref: Druard:2014) Druard, C., Braine, J., Schuster, K. F., et al. 2014, A&A, 567, A118, doi: [`10.1051/0004-6361/201423682`](http://doi.org/10.1051/0004-6361/201423682)

(ref: Egusa:2022) Egusa, F., Gao, Y., Morokuma-Matsui, K., Liu, G., & Maeda, F. 2022, ApJ, 935, 64, doi: [`10.3847/1538-4357/ac8050`](http://doi.org/10.3847/1538-4357/ac8050)

(ref: Falgarone:1998) Falgarone, E., Panis, J. F., Heithausen, A., et al. 1998, A&A, 331, 669

(ref: Freedman:2001) Freedman, W. L., Madore, B. F., Gibson, B. K., et al. 2001, ApJ, 553, 47, doi: [`10.1086/320638`](http://doi.org/10.1086/320638)

(ref: Garcia-Burillo:1993) Garcia-Burillo, S., Guelin, M., & Cernicharo, J. 1993, A&A, 274, 123

(ref: Garcia-Burillo:2009) Garcı́a-Burillo, S., Fernández-Garcı́a, S., Combes, F., et al. 2009, A&A, 496, 85, doi: [`10.1051/0004-6361/200810640`](http://doi.org/10.1051/0004-6361/200810640)

(ref: Goldreich:1974) Goldreich, P., & Kwan, J. 1974, ApJ, 189, 441, doi: [`10.1086/152821`](http://doi.org/10.1086/152821)

(ref: Hasegawa:1997) Hasegawa, T. 1997, in IAU Symposium, Vol. 170, IAU Symposium, ed. W. B. Latter, S. J. E. Radford, P. R. Jewell, J. G. Mangum, & J. Bally, 39–46

(ref: Herrera-Endoqui:2015) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86, doi: [`10.1051/0004-6361/201526047`](http://doi.org/10.1051/0004-6361/201526047)

(ref: Hidaka:2002) Hidaka, M., & Sofue, Y. 2002, PASJ, 54, 33, doi: [`10.1093/pasj/54.1.33`](http://doi.org/10.1093/pasj/54.1.33)

(ref: Ho:1997) Ho, L. C., Filippenko, A. V., & Sargent, W. L. W. 1997, ApJ, 487, 591, doi: [`10.1086/304643`](http://doi.org/10.1086/304643)

(ref: Keenan:2025) Keenan, R. P., Marrone, D. P., & Keating, G. K. 2025, ApJ, 979, 228, doi: [`10.3847/1538-4357/ada361`](http://doi.org/10.3847/1538-4357/ada361)

(ref: Keenan:2024) Keenan, R. P., Marrone, D. P., Keating, G. K., et al. 2024, ApJ, 975, 150, doi: [`10.3847/1538-4357/ad7504`](http://doi.org/10.3847/1538-4357/ad7504)

(ref: Kennicutt:2011) Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011, PASP, 123, 1347, doi: [`10.1086/663818`](http://doi.org/10.1086/663818)

(ref: Kennicutt:2003) Kennicutt, Jr., R. C., Armus, L., Bendo, G., et al. 2003, PASP, 115, 928, doi: [`10.1086/376941`](http://doi.org/10.1086/376941)

(ref: Koda:2025) Koda, J., Egusa, F., Hirota, A., et al. 2025, ApJ, 986, 29, doi: [`10.3847/1538-4357/add1dc`](http://doi.org/10.3847/1538-4357/add1dc)

(ref: Koda:2006) Koda, J., & Sofue, Y. 2006, PASJ, 58, 299, doi: [`10.1093/pasj/58.2.299`](http://doi.org/10.1093/pasj/58.2.299)

(ref: Koda:2012) Koda, J., Scoville, N., Hasegawa, T., et al. 2012, ApJ, 761, 41, doi: [`10.1088/0004-637X/761/1/41`](http://doi.org/10.1088/0004-637X/761/1/41)

(ref: Koda:2020) Koda, J., Sawada, T., Sakamoto, K., et al. 2020, ApJL, 890, L10, doi: [`10.3847/2041-8213/ab70b7`](http://doi.org/10.3847/2041-8213/ab70b7)

(ref: Koda:2023) Koda, J., Hirota, A., Egusa, F., et al. 2023, ApJ, 949, 108, doi: [`10.3847/1538-4357/acc65e`](http://doi.org/10.3847/1538-4357/acc65e)

(ref: Komugi:2025) Komugi, S., Sawada, T., Koda, J., et al. 2025, ApJ, 980, 126, doi: [`10.3847/1538-4357/ada6b5`](http://doi.org/10.3847/1538-4357/ada6b5)

(ref: Kuno:2007) Kuno, N., Sato, N., Nakanishi, H., et al. 2007, PASJ, 59, 117, doi: [`10.1093/pasj/59.1.117`](http://doi.org/10.1093/pasj/59.1.117)

(ref: Leroy:2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, AJ, 137, 4670, doi: [`10.1088/0004-6256/137/6/4670`](http://doi.org/10.1088/0004-6256/137/6/4670)

(ref: Leroy:2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: Leroy:2022) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149, doi: [`10.3847/1538-4357/ac3490`](http://doi.org/10.3847/1538-4357/ac3490)

(ref: Lundgren:2004) Lundgren, A. A., Wiklind, T., Olofsson, H., & Rydbeck, G. 2004, A&A, 413, 505, doi: [`10.1051/0004-6361:20031507`](http://doi.org/10.1051/0004-6361:20031507)

(ref: Maeda:2023) Maeda, F., Egusa, F., Ohta, K., Fujimoto, Y., & Habe, A. 2023, ApJ, 943, 7, doi: [`10.3847/1538-4357/aca664`](http://doi.org/10.3847/1538-4357/aca664)

(ref: Maeda:2022) Maeda, F., Egusa, F., Ohta, K., et al. 2022, ApJ, 926, 96, doi: [`10.3847/1538-4357/ac4505`](http://doi.org/10.3847/1538-4357/ac4505)

(ref: Maeda:2025) Maeda, F., Ohta, K., Egusa, F., et al. 2025, ApJ, 981, 156, doi: [`10.3847/1538-4357/adb41e`](http://doi.org/10.3847/1538-4357/adb41e)

(ref: Makarov:2014) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13, doi: [`10.1051/0004-6361/201423496`](http://doi.org/10.1051/0004-6361/201423496)

(ref: Mazzalay:2014) Mazzalay, X., Maciejewski, W., Erwin, P., et al. 2014, MNRAS, 438, 2036, doi: [`10.1093/mnras/stt2319`](http://doi.org/10.1093/mnras/stt2319)

(ref: McQuinn:2017) McQuinn, K. B. W., Skillman, E. D., Dolphin, A. E., Berg, D., & Kennicutt, R. 2017, AJ, 154, 51, doi: [`10.3847/1538-3881/aa7aad`](http://doi.org/10.3847/1538-3881/aa7aad)

(ref: Momose:2010) Momose, R., Okumura, S. K., Koda, J., & Sawada, T. 2010, ApJ, 721, 383, doi: [`10.1088/0004-637X/721/1/383`](http://doi.org/10.1088/0004-637X/721/1/383)

(ref: Montoya-Arroyave:2023) Montoya Arroyave, I., Cicone, C., Makroleivaditi, E., et al. 2023, A&A, 673, A13, doi: [`10.1051/0004-6361/202245046`](http://doi.org/10.1051/0004-6361/202245046)

(ref: Nishimura:2015) Nishimura, A., Tokuda, K., Kimura, K., et al. 2015, ApJS, 216, 18, doi: [`10.1088/0067-0049/216/1/18`](http://doi.org/10.1088/0067-0049/216/1/18)

(ref: Oka:1996) Oka, T., Hasegawa, T., Handa, T., Hayashi, M., & Sakamoto, S. 1996, ApJ, 460, 334, doi: [`10.1086/176973`](http://doi.org/10.1086/176973)

(ref: Oka:1998a) Oka, T., Hasegawa, T., Hayashi, M., Handa, T., & Sakamoto, S. 1998a, ApJ, 493, 730, doi: [`10.1086/305133`](http://doi.org/10.1086/305133)

(ref: Oka:1998b) Oka, T., Hasegawa, T., Sato, F., Tsuboi, M., & Miyazaki, A. 1998b, ApJS, 118, 455, doi: [`10.1086/313138`](http://doi.org/10.1086/313138)

(ref: Papadopoulos:2012) Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M., et al. 2012, MNRAS, 426, 2601, doi: [`10.1111/j.1365-2966.2012.21001.x`](http://doi.org/10.1111/j.1365-2966.2012.21001.x)

(ref: Querejeta:2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: Rodriguez:2024) Rodríguez, M. J., Lee, J. C., Indebetouw, R., et al. 2024, Tracing the earliest stages of star and cluster formation in 19 nearby galaxies with PHANGS-JWST and HST: compact 3.3 $\mu$m PAH emitters and their relation to the optical census of star clusters. [`https://arxiv.org/abs/2412.07862`](https://arxiv.org/abs/2412.07862)

(ref: S4G) S4G Team. 2020, Spitzer Survey of Stellar Structure in Galaxies, IPAC, doi: [`10.26131/IRSA425`](http://doi.org/10.26131/IRSA425)

(ref: Saintonge:2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: Sakamoto:1999) Sakamoto, K., Okumura, S. K., Ishizuki, S., & Scoville, N. Z. 1999, ApJ, 525, 691, doi: [`10.1086/307910`](http://doi.org/10.1086/307910)

(ref: Sakamoto:1997) Sakamoto, S., Hasegawa, T., Handa, T., Hayashi, M., & Oka, T. 1997, ApJ, 486, 276, doi: [`10.1086/304479`](http://doi.org/10.1086/304479)

(ref: Sakamoto:1994) Sakamoto, S., Hayashi, M., Hasegawa, T., Handa, T., & Oka, T. 1994, ApJ, 425, 641, doi: [`10.1086/174011`](http://doi.org/10.1086/174011)

(ref: Sandstrom:2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: Sault:1996) Sault, R. J., Staveley-Smith, L., & Brouw, W. N. 1996, A&AS, 120, 375

(ref: Sault:1995) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433, doi: [`10.48550/arXiv.astro-ph/0612759`](http://doi.org/10.48550/arXiv.astro-ph/0612759)

(ref: Sawada:2001) Sawada, T., Hasegawa, T., Handa, T., et al. 2001, ApJS, 136, 189, doi: [`10.1086/321793`](http://doi.org/10.1086/321793)

(ref: Scoville:1974) Scoville, N. Z., & Solomon, P. M. 1974, ApJL, 187, L67, doi: [`10.1086/181398`](http://doi.org/10.1086/181398)

(ref: Sellwood:1993) Sellwood, J. A., & Wilkinson, A. 1993, Reports on Progress in Physics, 56, 173, doi: [`10.1088/0034-4885/56/2/001`](http://doi.org/10.1088/0034-4885/56/2/001)

(ref: Seta:1998) Seta, M., Hasegawa, T., Dame, T. M., et al. 1998, ApJ, 505, 286, doi: [`10.1086/306141`](http://doi.org/10.1086/306141)

(ref: Sheth:2002) Sheth, K., Vogel, S. N., Regan, M. W., et al. 2002, AJ, 124, 2581, doi: [`10.1086/343835`](http://doi.org/10.1086/343835)

(ref: Sheth:2005) Sheth, K., Vogel, S. N., Regan, M. W., Thornley, M. D., & Teuben, P. J. 2005, ApJ, 632, 217, doi: [`10.1086/432409`](http://doi.org/10.1086/432409)

(ref: Sheth:2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397, doi: [`10.1086/657638`](http://doi.org/10.1086/657638)

(ref: SINGS) SINGS Team. 2020, Spitzer Infrared Nearby Galaxy Survey, IPAC, doi: [`10.26131/IRSA424`](http://doi.org/10.26131/IRSA424)

(ref: Sorai:2019) Sorai, K., Kuno, N., Muraoka, K., et al. 2019, PASJ, 71, S14, doi: [`10.1093/pasj/psz115`](http://doi.org/10.1093/pasj/psz115)

(ref: Sormani:2023) Sormani, M. C., Barnes, A. T., Sun, J., et al. 2023, MNRAS, 523, 2918, doi: [`10.1093/mnras/stad1554`](http://doi.org/10.1093/mnras/stad1554)

(ref: Teng:2022) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2022, ApJ, 925, 72, doi: [`10.3847/1538-4357/ac382f`](http://doi.org/10.3847/1538-4357/ac382f)

(ref: Teng:2023) —. 2023, ApJ, 950, 119, doi: [`10.3847/1538-4357/accb86`](http://doi.org/10.3847/1538-4357/accb86)

(ref: Tully:2016) Tully, R. B., Courtois, H. M., & Sorce, J. G. 2016, AJ, 152, 50, doi: [`10.3847/0004-6256/152/2/50`](http://doi.org/10.3847/0004-6256/152/2/50)

(ref: Tully:2013) Tully, R. B., Courtois, H. M., Dolphin, A. E., et al. 2013, AJ, 146, 86, doi: [`10.1088/0004-6256/146/4/86`](http://doi.org/10.1088/0004-6256/146/4/86)

(ref: vanderTak:2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: Veron-Cetty:2010) Véron-Cetty, M. P., & Véron, P. 2010, A&A, 518, A10, doi: [`10.1051/0004-6361/201014188`](http://doi.org/10.1051/0004-6361/201014188)

(ref: Wada:1994) Wada, K. 1994, PASJ, 46, 165

(ref: Yajima:2021) Yajima, Y., Sorai, K., Miyamoto, Y., et al. 2021, PASJ, 73, 257, doi: [`10.1093/pasj/psaa119`](http://doi.org/10.1093/pasj/psaa119)

(ref: Yu:2022) Yu, S.-Y., Kalinova, V., Colombo, D., et al. 2022, A&A, 666, A175, doi: [`10.1051/0004-6361/202244306`](http://doi.org/10.1051/0004-6361/202244306)

This work makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00650.S, 2015.1.00925.S, 2015.1.00956.S, 2017.1.00886.L, and 2018.1.01651.S, 2022.1.00360.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc..

This research has made use of the NASA/IPAC Infrared Science Archive, which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration.

JK acknowledges support from NSF through grants AST-2006600 and AST-2406608. F.M. is supported by JSPS KAKENHI grant Nos. JP23K13142 and JP23K20035. S.K. is supported by JSPS KAKENHI grant No. JP25K07371.

</paper>

Write the methods card for this paper.