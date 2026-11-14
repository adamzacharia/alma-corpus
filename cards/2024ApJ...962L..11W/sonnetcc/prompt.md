# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...962L..11W\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...962L..11W",
 "title": "A Massive Protocluster Anchored by a Luminous Quasar at z = 6.63",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Wang, Feige",
 "n_authors": 16,
 "arxiv_id": "2402.01844",
 "doi": "10.3847/2041-8213/ad20ef",
 "alma_projects_linked_by_archive": [
  "2018.1.01188.S",
  "2019.1.01216.S"
 ]
}
```

Paper text:
<paper>
# A Massive Protocluster Anchored by a Luminous Quasar at $z=6.63$

## Abstract

Protoclusters, the progenitors of galaxy clusters, trace large scale structures in the early Universe and are important to our understanding of structure formation and galaxy evolution. To date, only a handful of protoclusters have been identified in the Epoch of Reionization (EoR). As one of the rarest populations in the early Universe, distant quasars that host active supermassive black holes are thought to reside in the most massive dark matter halos at that cosmic epoch, and could thus potentially pinpoint some of the earliest protoclusters. In this letter, we report the discovery of a massive protocluster around a luminous quasar at $z=6.63$. This protocluster is anchored by the quasar, and includes three \[C II\] emitters at $z\sim6.63$, 12 spectroscopically confirmed Ly$\alpha$ emitters (LAEs) at $6.54<z\le6.64$, and a large number of narrow-band imaging selected LAE candidates at the same redshift. This structure has an overall overdensity of $\delta=3.3^{+1.1}_{-0.9}$ within $\sim35\times74$ cMpc$^2$ on the sky and an extreme overdensity of $\delta>30$ in its central region (i.e., $R\lesssim2$ cMpc). We estimate that this protocluster will collapse into a galaxy cluster with a mass of $6.9^{+1.2}_{-1.4}\times10^{15}~M_\odot$ at the current epoch, more massive than the most massive clusters known in the local Universe such as Coma. In the quasar vicinity, we discover a double-peaked LAE which implies that the quasar has a UV lifetime greater than 0.8 Myrs and has already ionized its surrounding intergalactic medium.

# Introduction

How luminous quasars, powered by billion-solar-mass supermassive black holes (SMBHs), formed less than a billion years after the Big Bang has been one of the outstanding open questions in cosmology since the early 2000s. In the current theoretical paradigm, the earliest SMBHs grew in massive galaxies and inhabit massive dark matter halos (cite: Springel05; Costa14; Latif22). This picture is supported by the observed strong clustering of high redshift quasars (cite: Shen07; Arita23) and the discoveries of a significant number of binary quasars at $z>4$ (cite: hennawi06b; McGreer16; Yue21). Following these arguments, one might expect that the most distant quasars, hosting the earliest active SMBHs, could act as signposts for protoclusters, the progenitors of local galaxy clusters and the largest (well beyond 1 cMpc) structures in the early Universe.

Extensive efforts on finding overdensities of galaxies around $z>6$ quasars (cite: Stiavelli05; Willott05; Zheng06; Kim09; Banados13; Morselli14; Champagne23) have been made in the past two decades (cite: Overzier16), however, to date only four $z>6$ quasar fields were spectroscopically confirmed to be associated with galaxy overdensities at Mpc-scales: J0100+2802 at $z=6.3$ with $\sim$20 \[O III\] emitters confirmed with recent JWST observations (cite: Kashino22), J0305–3150 at $z=6.6$ with 10 \[O III\] emitters and a large number of Lyman Break Galaxies (LBGs) confirmed with recent JWST observations (cite: Wang23a) and Hubble Space Telescope (HST) observations (cite: Champagne23), respectively, J1030+0524 at $z=6.3$ with two LAEs and four LBGs at the quasar redshift (cite: Mignoli20) and J1526–2050 at $z=6.6$ with two LAEs and two \[C II\] emitters (cite: Decarli17; Neeleman19b; Meyer22).

![](fig_map.pdf)

In this letter, we report the discovery of a protocluster anchored by a luminous quasar: J0910–0414 at $z=6.63$. The identification of this protocluster is secured by the discovery of a large number of narrow-band imaging selected LAE candidates, twelve spectroscopically confirmed LAEs, and three \[C II\] emitters in addition to the central luminous quasar. In §[2](#sec:obs), we present our observations, data reduction, LAE selection and confirmation, as well as ALMA confirmation of \[C II\] emitters. In §[3](#sec:cluster), we show the characterization of the overdensity of both LAEs and \[C II\] emitters and discuss the constraints on the mass of the protocluster. We also compare the structure anchored by J0910–0414 with other structures traced by distant quasars in this section. In addition, we report the discovery of a double-peaked LAE in the quasar vicinity and its implications in this section. Finally, we summarize our findings and discuss future implications in §[4](#sec:conclusion).

# Observations and data analysis

J0910–0414, a luminous quasar discovered by (cite: Wang19b) with a \[C II\]-based redshift of $z=6.6363\pm0.0003$ (cite: Wang23b). J0910–0414 hosts a SMBH with a virial mass of $(3.59\pm0.61)\times10^9~M_\odot$ (cite: Yang21). The black hole in J0910–0414 is among the most massive SMBHs known at $z>6.5$ and therefore is an ideal candidate for tracing the most biased dark matter halos and galaxy overdensities. In addition, the redshifted Ly$\alpha$ line of galaxies at the quasar redshift is well placed in a narrow band filter, NB926, on Subaru/HSC, which makes J0910–0414 a good target to search for an overdensity of LAEs with narrow-band imaging. This motivated us to investigate whether J0910–0414 traces an overdensity of galaxies with multi-wavelength followup observations.

## Subaru/HSC observation and LAE selection

The Subaru/HSC observations were obtained from 2019 November to 2020 January. We observed this quasar field with $i2$, $z$ and $NB926$ filters and the on-source exposure times are 150 minutes, 240 minutes, and 313 minutes, respectively. The data were processed with `hscPipe 6.7`, a customization of the LSST Science Pipelines (cite: Juric17; Bosch18). The pipeline first processes and calibrates the individual CCDs and then combines them into stacked mosaics for each filter. The photometric and astrometric calibrations were performed based on the Pan-STARRS1 DR1 dataset (cite: Chambers16). The seeing of stacked images were estimated to be $0.79''$, $0.74''$, and $0.56''$ for $i2$, $z$ and $NB926$, respectively. The 5$\sigma$ limiting magnitudes measured within $1.5''$ diameter apertures were measured to be 27.31, 26.27, and 25.71 AB magnitudes for $i2$, $z$ and $NB926$, respectively. The `hscPipe` pipeline performs a range of photometric measurements. In this work, we used the `forced` catalog following previous works (cite: Becker18; Shibuya18). The `forced` catalog contains the intrinsic astrometric parameters of a source that are determined from the band in which it is detected with the highest significance. These parameters are then held fixed for other bands. For the photometric information, it contains CModel magnitude, aperture magnitude and a number of pipeline flags. The CModel magnitude is a weighted combination of exponential and de Vaucouleurs fits to the light profiles of each object. The detailed algorithm of the CModel photometry is presented in (cite: Bosch18). Except where noted below, we adopt CModel magnitudes for the color and total magnitude measurements.

Subaru/HSC covers a circular field-of-view (FoV) with a radius of $45'$ and our designed dither pattern gives a relative uniform depth within $r\lesssim40'$ from the central quasar position. Therefore, the Ly$\alpha$ emitter (LAE) within $40'$ of the quasar position will have a uniform selection. Similar with (cite: Shibuya18), we impose the following selection criteria to select LAEs: $$\begin{equation}
SNR(NB926)\ge5
\end{equation}$$ $$\begin{equation}
z-NB926\ge1.0
\end{equation}$$ $$\begin{equation}
SNR(i)<3
\end{equation}$$ The signal-to-noise ratio (SNR) is measured in a $1.5''$ diameter aperture while the color was measured using the CModel magnitude following previous works (cite: Shibuya18). We also required `[i2,z,NB926]_flag_edge`, `[i2,z,NB926]_flag_bad`, `[i2,z,NB926]_flag_intercenter`,\
`[i2,z,NB926]_flag_saturcenter`, and\
`[i2,z,NB926]_flag_crcenter` to be `False` to reject most of the artifacts and/or low-$z$ contaminants introduced by inaccurate photometry. As a usual step on selecting LAEs, all sources satisfying these criteria were then visually inspected in the stacked images to further reject moving objects, satellite trails, uncorrected hot pixels, and other artifacts. In total, 87 LAE candidates pass our selection. The spatial distribution of these LAEs is shown in Figure [1](#fig:map). For visualization purpose, we estimate the overdensity contours of LAEs using a quartic kernel and a $1'$ grid size which are also shown in Figure [1](#fig:map). Many of these LAEs are distributed within the central $\sim 14\times30$ arcmin$^2$, or $\sim35\times74$ cMpc$^2$ and clustered around the central luminous quasar, indicating that the quasar resides in a significant overdense structure.

![](fig_spec_new.pdf)

## Optical spectroscopy

To confirm the imaging selected LAE candidates and understand the contamination rate of our selection, we performed optical spectroscopic observations for a subset of the LAEs with Magellan/IMACS and Keck/DEIMOS. The Magellan/IMACS observations were carried out on March 2021. We used the IMACS f/2 camera with 300-line red-blazed grism and designed a dedicated multi-slit mask (slit mask ID is 4129 in the Magellan/IMACS mask database) for the observation. With a single mask, we observed 10 LAE candidates, some dropout-selected galaxies, bright alignment stars and flux-calibration stars. All slits on the mask have a $1''$ slit width. The sky was clear with a seeing of $\sim0.8''-1.0''$ on the first night (2021 March 5) and $\sim0.6''-0.7''$ on the second night (2021 March 10). We obtained 11$\times$1200s exposures on the first night and 6$\times$1200s exposures on the second night. Following the standard procedures, we reduced IMACS data with the COSMOS2 pipeline (cite: COSMOS). From these observations, we spectroscopically confirmed six LAEs at $z\sim6.6$ and one low-redshift \[O III\] emitter at $z\sim0.85$. One object falls into a bad slit and the other two galaxies are undetected by the IMACS observations.

To obtain high quality spectra for IMACS confirmed LAEs and confirm more LAEs in the field, we also observed this field with Keck/DEIMOS. We designed three multi-slit masks with $1''$ slit width and used the 830G grating for the DEIMOS observations. We observed one mask on 2022 February 25 and two masks on 2022 February 26. We placed 8 LAE candidates on mask1, 4 LAE candidates on mask2, and 6 LAE candidates on mask3. We also added some dropout-selected galaxies and alignment stars as filler targets on these masks. The sky was clear on both nights and the seeing varied from $0.6''$ to $1.2''$ with a short period of $\sim1.5''$ seeing on the second night. We spent 6-hours of time on-source for mask1 and 3-hours each on the other two masks.

The DEIMOS data were reduced with the PypeIt pipeline (cite: Pypeit_ascl; Pypeit) following the standard steps, including overscan subtraction, flat fielding, wavelength calibration, optimal extraction, flux calibration and telluric correction. Seven of the eight LAEs on mask1 were confirmed to be $z\sim6.6$ LAEs, with three of them previously confirmed with IMACS. The other LAE candidate was undetected because of its faintness (NB926=25.8 magnitude). Masks mask2 and mask3 were observed for only 3-hours and only three (one of them was previously confirmed with IMACS) of the ten LAE candidates were confirmed to be $z\sim6.6$ LAEs. One LAE candidate is too close to the slit edge. The rest of the LAE candidates on mask2 and mask3 are either undetected or show very faint emissions and cannot be either confirmed or ruled out as $z\sim6.6$ LAEs. Future deeper spectroscopic observations are needed to confirm the nature of these LAE candidates.

In total, the IMACS and DEIMOS observations convincingly confirmed 12 bright LAEs at $z\sim6.6$ and only one low-$z$ interloper at $z=0.85$.

We can only measure redshift for $\sim$60% of the LAE candidates but of these 92% are indeed at the intended redshift $z\sim6.6$ suggesting that the narrow-band selection has low interloper contamination. These bright LAEs have Ly$\alpha$ luminosities of $L_{\rm Ly\alpha}\simeq (0.6-3.6) \times10^{43}~{\rm erg~s^{-1}}$. The detailed properties of these spectroscopically confirmed $z\sim6.6$ LAEs are listed in Table [\[tbl:galaxy\]](#tbl:galaxy) and the spectra of these LAEs are shown in Figure [2](#fig:spec).

| ID | Name | Redshift | Mask ID | NB926 | $z$$^{a}$ | $i$ | $L_{\rm Ly\alpha}$ | $L_{\rm [CII]}$ |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|---:|:--:|---:|
|  |  |  |  | mag | mag | mag | $\rm 10^{43} erg~s^{-1}$ | $10^{8}~L_\odot$ |  |  |  |
| LAE-01 | J091051.899$-$041703.94 | 6.541 | mask1,4129 | 24.36$\pm$0.05 | 25.46$\pm$0.10 | $>$27.81 | 3.57$\pm$0.87 | – |  |  |  |
| LAE-02 | J091039.434$-$042258.45 | 6.563 | mask1 | 25.29$\pm$0.08 | $>$27.19 | $>$27.73 | 1.34$\pm$0.09 | – |  |  |  |
| LAE-03 | J091043.771$-$040755.72 | 6.572 | mask2 | 25.28$\pm$0.07 | 26.91$\pm$0.30 | $>$27.81 | 1.21$\pm$0.13 | – |  |  |  |
| LAE-04 | J091042.675$-$042828.98 | 6.589 | mask3 | 25.06$\pm$0.09 | $>$27.17 | $>$27.73 | 0.76$\pm$0.16 | – |  |  |  |
| LAE-05 | J091135.005$-$041744.02 | 6.597 | 4129 | 23.94$\pm$0.05 | 25.70$\pm$0.20 | $>$27.80 | 2.71$\pm$0.36 | – |  |  |  |
| LAE-06 | J091022.398$-$040522.91 | 6.602 | mask2,4129 | 24.54$\pm$0.07 | 26.24$\pm$0.27 | $>$27.64 | 1.20$\pm$0.08 | – |  |  |  |
| LAE-07 | J091101.294$-$041522.55 | 6.625 | mask1,4129 | 24.12$\pm$0.04 | 26.60$\pm$0.26 | $>$27.79 | 2.25$\pm$0.12 | – |  |  |  |
| LAE-08 | J091122.389$-$035809.51 | 6.626 | 4129 | 24.71$\pm$0.10 | 25.74$\pm$0.17 | $>$27.75 | 0.78$\pm$0.12 | – |  |  |  |
| LAE-09 | J091042.883$-$041734.68 | 6.626 | mask1 | 26.00$\pm$0.15 | $>$27.17 | $>$27.82 | 1.24$\pm$0.10 | – |  |  |  |
| LAE-10 | J091046.177$-$041747.74 | 6.634 | mask1 | 26.08$\pm$0.16 | $>$27.24 | $>$27.86 | 0.65$\pm$0.10 | – |  |  |  |
| LAE-11 | J091054.343$-$041452.80 | 6.641 | mask1,4129 | 24.66$\pm$0.06 | 26.98$\pm$0.34 | $>$27.83 | 1.86$\pm$0.30 | – |  |  |  |
| LAE-12$^{b}$ | J091053.671$-$041322.62 | 6.641 | mask1,4129 | 24.97$\pm$0.10 | $>$27.19 | $>$27.82 | 0.42$\pm$0.11 | – |  |  |  |
| SMG-A | J091054.544$-$041355.52 | 6.6266 | – | – | – | – | – | 12.82$\pm$0.43 |  |  |  |
| SMG-B | J091053.598$-$041409.11 | 6.6272 | – | – | – | – | – | 42.43$\pm$0.73 |  |  |  |
| SMG-C | J091054.552$-$041406.99 | 6.6379 | – | – | – | – | – | 1.76$\pm$0.16 |  |  |  |

: Spectroscopically confirmed high-redshift galaxies in the protocluster.

Table notes: $^{a}$ We adopt 3-$\sigma$ magnitude limits for undetected sources. $^{b}$ The Ly$\alpha$ line of LAE-12 was only detected from the DEIMOS data, limited by the depth of the IMACS observation.

## ALMA observation and \[C II\] emitters

To identify obscured galaxies in the quasar field, we also observed the quasar J0910–0414 with Atacama Large Millimeter/submillimeter Array (ALMA) C-3 in band 6 (Project: 2018.1.01188.S, PI: F. Wang). The on-source exposure time was 19 minutes. We identified two \[C II\] emitting galaxies (SMG-A and SMG-B) from the single-pointing ALMA observation, indicating that we are seeing a significant small-scale overdensity of galaxies around this quasar. We then followed up this quasar field with ALMA/C-6 (Project: 2019.1.01216.S, PI: J. Yang) to reach a higher resolution and better sensitivity. The high resolution observations were obtained from 2021 May to 2021 June with a total on-source time of 383 minutes and revealed a third \[C II\] emitting galaxy (SMG-C) interacting with the quasar itself.

The ALMA data were reduced with the standard `CASA` package (cite: CASA). In this letter, we focus on the identification of three \[C II\] emitting galaxies, while the detailed ALMA data reduction and the characterization of the quasar host galaxy will be presented in a separate work (Yang J. et al., in prep). The two bright \[C II\] emitting galaxies (SMG-A and SMG-B) are clearly seen in the moment zero map in panel c of Figure [1](#fig:map) and the third galaxy is merging with the quasar itself and can be seen in the the zoom-in plot in Figure [1](#fig:map). The \[C II\] spectra of galaxy SMG-A and SMG-B were extracted from the deep C-6 data cube with a $1.0''$ diameter aperture centered at (09h10m54.544s, –04d13m55.515s) and (09h10m53.598s, –04d14m09.107s), respectively. To avoid contamination from the flux of the quasar, we extracted the spectra for the SMG-C with a smaller aperture ($0.3''$ diameter aperture ) centered at (09h10m54.552s, –04d14m06.994s). The \[C II\] spectra of all these galaxies are also shown in Figure [2](#fig:spec) and the apertures used for spectral extraction are highlighted with yellow circles in panel **b** and **c** of Figure [1](#fig:map). The \[C II\] luminosities of SMG-A, SMG-B, and SMG-C are in the range of $(1.8-42.5)\times10^8~L_\odot$. It is interesting to note that all three \[C II\] emitters are not detected in Subaru narrow-band imaging and $z$-band imaging, which indicates that these \[C II\] emitters are likely dustier than the narrow-band selected LAEs.

# Results

## Overdensity of galaxies

To measure the significance of the overdensity of LAEs in the protocluster, we measure the density of LAEs in two regions. First, we measure the LAE density in the outskirts of the Subaru HSC field. As shown in Figure [1](#fig:map), the LAEs are clustered within the central $\sim14\times30$ arcmin$^2$ or $\sim35\times74$ cMpc$^2$ region. We choose to only use the region with $r>50$ cMpc (cite: Jiang18) from the central quasar as a comparison field to measure the ‘background’ LAE density. Second, we measure the LAE density within the central $\sim14\times30$ arcmin$^2$ region where the LAEs are clustered.

In Figure [3](#fig:density) we plot the surface density of LAEs as a function of their narrow band brightness. As shown in Figure [3](#fig:density), the ‘background’ LAE densities (red open circles) in our HSC field are very similar to that measured from other $z\sim6.6$ LAE surveys (cite: Ouchi10; Shibuya18; Ono21), except at the very faint end close to the survey depth limit. The surface density of LAEs in the central $\sim14\times30$ arcmin$^2$ region, however, is clearly higher than that estimated from both the outskirts of the HSC field and other studies in all magnitude bins. On average, the density in the central region (24 LAEs within 420 arcmin$^2$) is $4.3^{+1.1}_{-0.9}$ ($\delta=\frac{n}{\bar{n}}-1=3.3^{+1.1}_{-0.9}$) times higher than that derived from the outskirts (50 LAEs within 3740 arcmin$^2$) of the field. In particular, the overdensity of LAEs within the central $\lesssim2$cMpc is $\delta>30$, making J0910–0414 among the most extreme (in terms of both extent and overdensity) overdensities of LAEs known in the early Universe (cite: Jiang18).

![image](fig_surface_density.pdf) ![image](fig_overdensity.pdf)

To characterize the overdensity and the extent of the protocluster in detail, we also measure the cumulative overdensity profile of both LAEs and \[C II\] emitters in this field. We measure the overdensity profile in a set of cylindrical volumes with logarithmically spaced radial bins and a velocity bin of $\Delta v=\pm1000~{\rm km~s^{-1}}$ (cite: Meyer22) and $\Delta v=\pm2250~{\rm km~s^{-1}}$ (the width of NB926 filter) for \[C II\] emitters and LAEs, respectively. The background number of \[C II\] emitters is estimated from the \[C II\] cumulative number density with $L_{\rm [CII]}>10^{8.2}~L_\odot$ (cite: Popping19; Uzgil21) while the background number of LAEs is directly measured from the outskirts ($r>50$ cMpc ) of our HSC observations. The overdensity profiles of \[C II\] emitters and LAEs are shown as orange squares and red dots in Figure [3](#fig:density), respectively. In this figure, we also show the overdensity profiles of three quasar fields with known \[C II\] overdensities measured using both \[C II\] emitters and LAEs by (cite: Meyer22) [^1].

To quantitatively characterize the overdensity profile in this protocluter, we further compare it with the overdensity profiles expected from protoclusters and quasar-galaxy cross-correlation functions in Figure [3](#fig:density). (cite: Shen07) measured a correlation length of $r_0^{\rm QQ}=24.3~h^{-1}~{\rm Mpc}$ for a fixed slope of $\gamma=2.0$ using a sample of $\sim1500$ quasars at $z>3.5$, which indicates that high redshift quasars are among the most highly clustered population in the Universe. (cite: Garcia19) re-fit the measurements in (cite: Shen07) by fixing $\gamma=1.8$ and derive $r_0^{\rm QQ}=22.3~h^{-1}~{\rm Mpc}$. (cite: Ouchi18) measured a correlation length of $r_0^{\rm GG}=2.66~h^{-1}~{\rm Mpc}$ (for a fixed slope of $\gamma=1.8$) for $z\sim6.6$ LAEs. This yields an expected quasar-LAE cross-correlation length of $r_0^{\rm QG}=\sqrt{r_0^{\rm QQ}, r_0^{\rm GG}}=7.7~h^{-1}~{\rm Mpc}$ ($\gamma=1.8$). The cumulative overdensity profile measured from the $r_0^{\rm QG}$ and $\gamma$ for quasar-LAE is plotted as a black dotted line in Figure [3](#fig:density). Since there is no existing measurement of the auto-correlation length for \[C II\] emitters, we show the overdensity profile (magenta dashed line) measured from quasar-CO emitters with $r_0^{\rm QG}=8.37~h^{-1}~{\rm Mpc}$ and $\gamma=1.8$ (cite: Garcia22) as a comparison. Furthermore, we also show the LAE overdensity profile (blue dot-dashed line) in protocluster fields at intermediate redshifts that is measured from a sample of high-$z$ radio galaxies (HzRg) and Ly$\alpha$ blobs (LAB) by (cite: Hennawi15) — we used $\gamma=1.8$ and $r_0^{\rm QG}=20~h^{-1}~{\rm Mpc}$ to be consistent with $\gamma$ of other profiles shown in Figure [3](#fig:density). It is clear that the overdensity in the J0910–0414 field is much higher than that expected from the quasar–galaxy cross-correlation function and the overdensity even exceeds the average protocluster by a factor of seven for $R\lesssim2~{\rm cMpc}$, decreasing to an excess of $\sim3$ on scales of $R\simeq5$ cMpc, and exhibits a steeper profile. This indicates that the protocluster traced by quasar J0910–0414 is among the most overdense structures known in the early Universe.

## The mass of the protocluster

To estimate the total present-day mass of this protocluster, we follow the widely used formula by assuming that this structure will collapse into a cluster at $z=0$ (cite: Chiang13): $M_{z=0}=(1+\delta_m)\bar{\rho}V$, where $\bar{\rho}=3.88\times10^{10}M_\odot~{\rm cMpc^{-3}}$ is the mean matter density of the Universe, $V$ is the volume of the protocluster, and $\delta_m$ is the mass overdensity. We estimate the volume of the protocluster using the yellow box ($\sim14\times30$ arcmin$^2$ or $\sim35\times74$ cMpc$^2$) shown in Figure [1](#fig:map) and a line-of-sight depth of $36.9~ {\rm cMpc}$ which is derived from the redshift difference of the highest-$z$ LAE and lowest-$z$ LAE in the spectroscopic sample. We note that the volume is conservative because the boundary does not cover the whole structure and the line-of-sight depth is a lower limit since the sensitivity of NB926 filter drops dramatically for detecting LAEs at $z\gtrsim6.65$. The observed galaxy overdensity within this region is $3.3^{+1.1}_{-0.9}$ and the bias parameter for $z\sim6.6$ LAEs is measured to be $b=4.54\pm0.63$ (cite: Ouchi18). We thus can determine $\delta_m$ through $1+b\delta_m = C(1+\delta)$, where $C$ is the correction factor for the redshift space distortion. Extrapolating the (cite: Chiang13) formula to $z\sim6.6$ and higher masses, we derive $C=0.84$, $\delta_m=0.57$ and the present-day mass $M_{z=0}=6.9^{+1.2}_{-1.4}\times10^{15}~M_\odot$ for $\delta=3.3^{+1.1}_{-0.9}$ at $z=6.63$, . This would make J0910–0414 the most massive protocluster known at $z>6$ (cite: Jiang18; Hu21) and at $z=0$ it would be three times more massive than the nearby Coma cluster (cite: Merritt87).

## Comparison with other galaxy overdensities traced by $z\sim6$ quasars

J0100+2802, the most luminous quasar known at $z>6$, has been found to be associated with a galaxy overdensity with $\sim20$ \[O III\] emitters in its vicinity (cite: Kashino22). However, these \[O III\] emitters are much fainter than the galaxies identified in J0910–0414 field and we could not compare the two structures directly. Similarly, J0305–3150 resides in a structure with overdensities of both \[O III\] emitters (cite: Wang23a) and LBGs (cite: Champagne23). Nevertheless, the narrow-band imaging observation of J0305–3150 indicates that no bright candidate LAEs presents in the vicinity of J0305–3150, and the surface density of LAEs on large scales appears to be underdense compared to control fields (cite: Ota18), making it a different kind of structure from J0910–0414. J0836+0054, a radio-loud quasar at a slightly lower redshift ($z\sim5.8$), resides in a rich structure with overdensity of bright LAEs (cite: Overzier22). In particular, the three $z\sim5.8$ LAEs confirmed in J0836+0054 field have similar Ly$\alpha$ luminosities (cite: Bosman20) to the LAEs found in J0910–0414 field. In addition, the LAE overdensity in the central $R\lesssim3$ cMpc regions of both fields are comparable (cite: Overzier22). This indicates that the two structures around J0836+0054 and J0910–0414 could be similar despite the lack of dusty galaxy observations in J0836+0054 field. J1030+0524, a well studied quasar at $z=6.3$, has been found residing in a structure with overdensities of both LBGs and LAEs at various scales (cite: Mignoli20). Interestingly, most spectroscopically confirmed galaxies in J1030+0524 field are much fainter than the LAEs found in this work, indicating that the galaxy populations in these two structures could be different. Finally, J1526–2050, a luminous quasar at $z\sim6.6$, has been studied with both ALMA and MUSE observations. These observations indicates that J1526–2050 traces an Mpc-scale structure with both \[C II\] emitters and LAEs in the quasar vicinity, making it a structure potentially similar to the structure around J0910–0414. However, the wide-field imaging and spectroscopic observations in the J1526–2050 field are lacking and the extend of this structure is still unclear. In summary, the structures traced by distant quasars exhibit significant diversity, and the current non-uniform observations make it challenging to directly compare their physical properties and evolutionary phases. Therefore, conducting systematic investigations of the Mpc-scale environment of distant quasars in a more consistent manner would be valuable for understanding the connection between quasars and their Mpc-scale surroundings, as well as the evolutionary phases of these large-scale structures.

## A double peaked LAE in the quasar vicinity

Although the proximity zone size of the central quasar cannot be determined from the optical spectra because of the appearance of strong N V broad absorption line on top of the quasar Ly$\alpha$ line (cite: Yang21). Nevertheless, the typical proximity zone size of quasars with similar luminosity and redshift is $\sim$5 pMpc (cite: Eilers20a). In Figure [4](#fig:escape), we show the zoom-in spectra of the LAE-11, the nearest companion LAE at $\sim0.3$ pMpc from the quasar, and the relative position of the LAE-11 to the quasar. The line-of-sight proper distance and the perpendicular separation along the plane of sky between the quasar and the LAE-11 are $D_\parallel=0.18$ pMpc, and $D_\perp=0.25$ pMpc, respectively. Interestingly, LAE-11, at a slightly higher redshift than the quasar, shows a widely separated double peak $\rm Ly\alpha$ line as shown in Figure [4](#fig:escape). The peak separation of the $\rm Ly\alpha$ line is measured to be $320\pm22~{\rm km~s^{-1}}$ which implies a low ionizing photon escape fraction of $\sim7$% by using the empirical fitting formula of (cite: Izotov18). Since the blue peak of the Ly$\alpha$ line is only visible in a highly ionized environment, the presence of a double-peaked $\rm Ly\alpha$ line in LAE-11 provides a direct evidence that the quasar has ionized the gas in the intergalactic medium (IGM) around LAE-11 (cite: Bosman20). This indicates that the quasar proximity zone size is $>0.3~{\rm pMpc}$. Additionally, we can constrain the quasar UV lifetime using galaxies in the proximity zones of quasars (cite: Bosman20) because the observed radiation field at a certain point in space is sensitive to the quasar radiation emitted at an earlier time with a time delay of $$\begin{equation}
    \Delta t = \frac{(D_\parallel^2+D_\perp^2)^{1/2}-D_\parallel}{c}
\end{equation}$$ , where $c$ is the speed of light (cite: Bosman20). Using Equation (4), we estimate the time delay to be $\Delta t=1.6\times10^6$ yr. Nevertheless, the redshift difference between the LAE-11 and the quasar is small ($\Delta z=0.005$ or $v=185~{\rm km~s^{-1}}$), we cannot distinguish the line-of-sight separation from the peculiar velocity of the galaxy around the quasar. In addition, the Ly$\alpha$ of high-redshift galaxies is usually redshifted (cite: Stark17), which could make the line-of-sight velocity separation between the quasar and LAE-11 more uncertain. Taking these into account, we estimate the lower limit of quasar UV lifetime using $t_q > \frac{D_\perp}{c}=8.1\times10^5$ yr. Future deeper spectroscopic observations of more galaxies around the quasar or at slightly higher redshifts than the quasar will allow us to study the ionizing property and the structure of quasar proximity zone (cite: Schmidt19).

![](figures/fig_doublepeak_Lya.pdf)

# Summary

In this letter, we report the discovery of a protocluster anchored by a luminous quasar J0910–0414 at $z=6.63$ from wide-field Subaru/HSC imaging, Keck/DEIMOS and Magellan/IMACS optical spectroscopic, and deep ALMA observations. The identification of this protocluster is secured by the discovery of a significant overdensity of both \[C II\] emitters and LAEs in the field. The existence of three \[C II\] emitters within just one ALMA pointing indicates that the density of \[C II\] emitters in J0910–0414 field is three orders of magnitude times higher than that expected from blank field. The density of LAEs within the central $\sim14\times30$ arcmin$^2$ (or $\sim35\times74$ cMpc$^2$) region is $4.3^{+1.1}_{-0.9}$ times higher than that found in the outskirts of Subaru/HSC imaging, and the overdensity of LAEs increases to $\delta>30$ within the central two Megaparsecs. We measured the cumulative overdensity profile of galaxies in J0910–0414 field, which is much higher than that expected from the quasar–galaxy cross-correlation function from kpc-scale up to $\sim50$ Mpc-scale. The overdensity of LAEs even exceeds the average overdensity of protoclusters at $z\sim2$ by a factor of $\sim7$ for $R\lesssim2~{\rm cMpc}$ decreasing to an excess of $\sim3$ on scales of $R\simeq5$ cMpc. In addition, we estimated the present-day mass of this protocluster to be $M_{z=0}=6.9^{+1.2}_{-1.4}\times10^{15}~M_\odot$, three times more massive than the nearby Coma cluster, making J0910–0414 the most massive protocluster known at $z\gtrsim6$.

Our deep optical spectroscopy indicated a high purity of narrow-band selected LAE candidates and successfully confirmed 12 LAEs at $6.54<z\le6.64$ with only one low-$z$ interloper at $z=0.85$. Remarkably, we discover a double-peaked LAE in the vicinity of the central quasar. The presence of the blue peak Ly$\alpha$ line in this galaxy implies that the quasar vicinity is highly ionized by the quasar radiation and the quasar UV lifetime is larger than 0.8 Myr.

This work demonstrates that it is efficient to identify galaxy overdensities by targeting quasar fields with both ALMA and narrow-band observations. Future ALMA mosaic observations, wide-field narrow band imaging, and JWST observations of quasars in the EoR will allow us to not only identify galaxy overdensities in the EoR but also study the environmental dependence of galaxy evolution.

We thank Yoshiaki Ono for providing their collected data for Ly$\alpha$ emitter surface densities. We thank Romain Meyer for providing the overdensity profiles of \[C II\] and LAEs in three $z\sim6$ quasar fields and for insightful discussions about their measurements. We thank the referee for carefully reading the manuscript and providing great comments. FW acknowledges support from NSF Grant AST-2308258.

This work was supported by a NASA Keck PI Data Award, administered by the NASA Exoplanet Science Institute. Data presented herein were obtained at the W. M. Keck Observatory from telescope time allocated to the National Aeronautics and Space Administration through the agency’s scientific partnership with the California Institute of Technology and the University of California. The Observatory was made possible by the generous financial support of the W. M. Keck Foundation.

This paper includes data gathered with the 6.5 meter Magellan Telescopes located at Las Campanas Observatory, Chile.

This research is based in part on data collected at the Subaru Telescope, which is operated by the National Astronomical Observatory of Japan. We are honored and grateful for the opportunity of observing the Universe from Maunakea, which has the cultural, historical, and natural significance in Hawaii. The NB926 filter was supported by KAKENHI (26707006) Grant-in-Aid for Scientific Research (A) through the Japan Society for the Promotion of Science (JSPS).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01188.S and ADS/JAO.ALMA#2019.1.01216.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortunate to have the opportunity to conduct observations from this mountain.

# Facilities

ALMA, Keck:II (DEIMOS), Magellan:Baade (IMACS), Subaru (HSC)

# Software

astropy (cite: Astropy), Cosmos2 (cite: IMACS; COSMOS), hscPipe (cite: Bosch18), Matplotlib (cite: Matplotlib), Numpy (cite: Numpy), PypeIt (cite: Pypeit_ascl; Pypeit), Scipy (cite: Scipy),

natexlab

(ref: Arita23) Arita, J., Kashikawa, N., Matsuoka, Y., et al. 2023, ApJ, 954, 210, doi: [`10.3847/1538-4357/ace43a`](http://doi.org/10.3847/1538-4357/ace43a)

(ref: Astropy) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Banados13) Bañados, E., Venemans, B., Walter, F., et al. 2013, ApJ, 773, 178, doi: [`10.1088/0004-637X/773/2/178`](http://doi.org/10.1088/0004-637X/773/2/178)

(ref: Becker18) Becker, G. D., Davies, F. B., Furlanetto, S. R., et al. 2018, ApJ, 863, 92, doi: [`10.3847/1538-4357/aacc73`](http://doi.org/10.3847/1538-4357/aacc73)

(ref: Bosch18) Bosch, J., Armstrong, R., Bickerton, S., et al. 2018, PASJ, 70, S5, doi: [`10.1093/pasj/psx080`](http://doi.org/10.1093/pasj/psx080)

(ref: Bosman20) Bosman, S. E. I., Kakiichi, K., Meyer, R. A., et al. 2020, ApJ, 896, 49, doi: [`10.3847/1538-4357/ab85cd`](http://doi.org/10.3847/1538-4357/ab85cd)

(ref: Chambers16) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv e-prints, arXiv:1612.05560. [`https://arxiv.org/abs/1612.05560`](https://arxiv.org/abs/1612.05560)

(ref: Champagne23) Champagne, J. B., Casey, C. M., Finkelstein, S. L., et al. 2023, ApJ, 952, 99, doi: [`10.3847/1538-4357/acda8d`](http://doi.org/10.3847/1538-4357/acda8d)

(ref: Chiang13) Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, ApJ, 779, 127, doi: [`10.1088/0004-637X/779/2/127`](http://doi.org/10.1088/0004-637X/779/2/127)

(ref: Costa14) Costa, T., Sijacki, D., Trenti, M., & Haehnelt, M. G. 2014, MNRAS, 439, 2146, doi: [`10.1093/mnras/stu101`](http://doi.org/10.1093/mnras/stu101)

(ref: Decarli17) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: IMACS) Dressler, A., Bigelow, B., Hare, T., et al. 2011, PASP, 123, 288, doi: [`10.1086/658908`](http://doi.org/10.1086/658908)

(ref: Eilers20a) Eilers, A.-C., Hennawi, J. F., Decarli, R., et al. 2020, ApJ, 900, 37, doi: [`10.3847/1538-4357/aba52e`](http://doi.org/10.3847/1538-4357/aba52e)

(ref: Garcia19) Garcı́a-Vergara, C., Hennawi, J. F., Barrientos, L. F., & Arrigoni Battaia, F. 2019, ApJ, 886, 79, doi: [`10.3847/1538-4357/ab4d52`](http://doi.org/10.3847/1538-4357/ab4d52)

(ref: Garcia22) Garcı́a-Vergara, C., Rybak, M., Hodge, J., et al. 2022, ApJ, 927, 65, doi: [`10.3847/1538-4357/ac469d`](http://doi.org/10.3847/1538-4357/ac469d)

(ref: Numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hennawi15) Hennawi, J. F., Prochaska, J. X., Cantalupo, S., & Arrigoni-Battaia, F. 2015, Science, 348, 779, doi: [`10.1126/science.aaa5397`](http://doi.org/10.1126/science.aaa5397)

(ref: hennawi06b) Hennawi, J. F., Strauss, M. A., Oguri, M., et al. 2006, AJ, 131, 1

(ref: Hu21) Hu, W., Wang, J., Infante, L., et al. 2021, Nature Astronomy, 5, 423, doi: [`10.1038/s41550-021-01322-2`](http://doi.org/10.1038/s41550-021-01322-2)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Izotov18) Izotov, Y. I., Worseck, G., Schaerer, D., et al. 2018, MNRAS, 478, 4851, doi: [`10.1093/mnras/sty1378`](http://doi.org/10.1093/mnras/sty1378)

(ref: Jiang18) Jiang, L., Wu, J., Bian, F., et al. 2018, Nature Astronomy, 2, 962, doi: [`10.1038/s41550-018-0587-9`](http://doi.org/10.1038/s41550-018-0587-9)

(ref: Juric17) Jurić, M., Kantor, J., Lim, K. T., et al. 2017, in Astronomical Society of the Pacific Conference Series, Vol. 512, Astronomical Data Analysis Software and Systems XXV, ed. N. P. F. Lorente, K. Shortridge, & R. Wayth, 279. [`https://arxiv.org/abs/1512.07914`](https://arxiv.org/abs/1512.07914)

(ref: Kashino22) Kashino, D., Lilly, S. J., Matthee, J., et al. 2022, arXiv e-prints, arXiv:2211.08254. [`https://arxiv.org/abs/2211.08254`](https://arxiv.org/abs/2211.08254)

(ref: Kim09) Kim, S., Stiavelli, M., Trenti, M., et al. 2009, ApJ, 695, 809, doi: [`10.1088/0004-637X/695/2/809`](http://doi.org/10.1088/0004-637X/695/2/809)

(ref: Latif22) Latif, M. A., Whalen, D. J., Khochfar, S., Herrington, N. P., & Woods, T. E. 2022, Nature, 607, 48, doi: [`10.1038/s41586-022-04813-y`](http://doi.org/10.1038/s41586-022-04813-y)

(ref: McGreer16) McGreer, I. D., Eftekharzadeh, S., Myers, A. D., & Fan, X. 2016, AJ, 151, 61, doi: [`10.3847/0004-6256/151/3/61`](http://doi.org/10.3847/0004-6256/151/3/61)

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Merritt87) Merritt, D. 1987, ApJ, 313, 121, doi: [`10.1086/164953`](http://doi.org/10.1086/164953)

(ref: Meyer22) Meyer, R. A., Decarli, R., Walter, F., et al. 2022, ApJ, 927, 141, doi: [`10.3847/1538-4357/ac4f67`](http://doi.org/10.3847/1538-4357/ac4f67)

(ref: Mignoli20) Mignoli, M., Gilli, R., Decarli, R., et al. 2020, A&A, 642, L1, doi: [`10.1051/0004-6361/202039045`](http://doi.org/10.1051/0004-6361/202039045)

(ref: Morselli14) Morselli, L., Mignoli, M., Gilli, R., et al. 2014, A&A, 568, A1, doi: [`10.1051/0004-6361/201423853`](http://doi.org/10.1051/0004-6361/201423853)

(ref: Neeleman19b) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: COSMOS) Oemler, A., Clardy, K., Kelson, D., Walth, G., & Villanueva, E. 2017, COSMOS: Carnegie Observatories System for MultiObject Spectroscopy, Astrophysics Source Code Library, record ascl:1705.001. [`http://ascl.net/1705.001`](http://ascl.net/1705.001)

(ref: Ono21) Ono, Y., Itoh, R., Shibuya, T., et al. 2021, ApJ, 911, 78, doi: [`10.3847/1538-4357/abea15`](http://doi.org/10.3847/1538-4357/abea15)

(ref: Ota18) Ota, K., Venemans, B. P., Taniguchi, Y., et al. 2018, ApJ, 856, 109, doi: [`10.3847/1538-4357/aab35b`](http://doi.org/10.3847/1538-4357/aab35b)

(ref: Ouchi10) Ouchi, M., Shimasaku, K., Furusawa, H., et al. 2010, ApJ, 723, 869, doi: [`10.1088/0004-637X/723/1/869`](http://doi.org/10.1088/0004-637X/723/1/869)

(ref: Ouchi18) Ouchi, M., Harikane, Y., Shibuya, T., et al. 2018, PASJ, 70, S13, doi: [`10.1093/pasj/psx074`](http://doi.org/10.1093/pasj/psx074)

(ref: Overzier16) Overzier, R. A. 2016, A&ARv, 24, 14, doi: [`10.1007/s00159-016-0100-3`](http://doi.org/10.1007/s00159-016-0100-3)

(ref: Overzier22) —. 2022, ApJ, 926, 114, doi: [`10.3847/1538-4357/ac448c`](http://doi.org/10.3847/1538-4357/ac448c)

(ref: Popping19) Popping, G., Narayanan, D., Somerville, R. S., Faisst, A. L., & Krumholz, M. R. 2019, MNRAS, 482, 4906, doi: [`10.1093/mnras/sty2969`](http://doi.org/10.1093/mnras/sty2969)

(ref: Pypeit) Prochaska, J., Hennawi, J., Westfall, K., et al. 2020, The Journal of Open Source Software, 5, 2308, doi: [`10.21105/joss.02308`](http://doi.org/10.21105/joss.02308)

(ref: Pypeit_ascl) Prochaska, J. X., Hennawi, J., Cooke, R., et al. 2019, PypeIt: Python spectroscopic data reduction pipeline, Astrophysics Source Code Library, record ascl:1911.004. [`http://ascl.net/1911.004`](http://ascl.net/1911.004)

(ref: Schmidt19) Schmidt, T. M., Hennawi, J. F., Lee, K.-G., et al. 2019, ApJ, 882, 165, doi: [`10.3847/1538-4357/ab2fcb`](http://doi.org/10.3847/1538-4357/ab2fcb)

(ref: Shen07) Shen, Y., Strauss, M. A., Oguri, M., et al. 2007, AJ, 133, 2222, doi: [`10.1086/513517`](http://doi.org/10.1086/513517)

(ref: Shibuya18) Shibuya, T., Ouchi, M., Konno, A., et al. 2018, PASJ, 70, S14, doi: [`10.1093/pasj/psx122`](http://doi.org/10.1093/pasj/psx122)

(ref: Springel05) Springel, V., White, S. D. M., Jenkins, A., et al. 2005, Nature, 435, 629, doi: [`10.1038/nature03597`](http://doi.org/10.1038/nature03597)

(ref: Stark17) Stark, D. P., Ellis, R. S., Charlot, S., et al. 2017, MNRAS, 464, 469, doi: [`10.1093/mnras/stw2233`](http://doi.org/10.1093/mnras/stw2233)

(ref: Stiavelli05) Stiavelli, M., Djorgovski, S. G., Pavlovsky, C., et al. 2005, ApJL, 622, L1, doi: [`10.1086/429406`](http://doi.org/10.1086/429406)

(ref: Uzgil21) Uzgil, B. D., Oesch, P. A., Walter, F., et al. 2021, ApJ, 912, 67, doi: [`10.3847/1538-4357/abe86b`](http://doi.org/10.3847/1538-4357/abe86b)

(ref: Scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Wang23b) Wang, F., Yang, J., Fan, X., et al. 2023a, ApJ submitted.

(ref: Wang19b) —. 2019, ApJ, 884, 30, doi: [`10.3847/1538-4357/ab2be5`](http://doi.org/10.3847/1538-4357/ab2be5)

(ref: Wang23a) Wang, F., Yang, J., Hennawi, J. F., et al. 2023b, ApJL, 951, L4, doi: [`10.3847/2041-8213/accd6f`](http://doi.org/10.3847/2041-8213/accd6f)

(ref: Willott05) Willott, C. J., Percival, W. J., McLure, R. J., et al. 2005, ApJ, 626, 657, doi: [`10.1086/430168`](http://doi.org/10.1086/430168)

(ref: Yang21) Yang, J., Wang, F., Fan, X., et al. 2021, ApJ, 923, 262, doi: [`10.3847/1538-4357/ac2b32`](http://doi.org/10.3847/1538-4357/ac2b32)

(ref: Yue21) Yue, M., Fan, X., Yang, J., & Wang, F. 2021, ApJL, 921, L27, doi: [`10.3847/2041-8213/ac31a9`](http://doi.org/10.3847/2041-8213/ac31a9)

(ref: Zheng06) Zheng, W., Overzier, R. A., Bouwens, R. J., et al. 2006, ApJ, 640, 574, doi: [`10.1086/500167`](http://doi.org/10.1086/500167)

[^1]: The \[C II\] density estimated from the \[C II\] luminosity function (cite: Popping19) is underestimated by a factor of two in Figure 10 of (cite: Meyer22). We corrected this factor in Figure [3](#fig:density).

</paper>

Write the methods card for this paper.