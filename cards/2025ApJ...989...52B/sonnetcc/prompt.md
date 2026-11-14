# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989...52B\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989...52B",
 "title": "Properties of H<SUB>2</SUB>O Masers and Their Associated Sources in Sagittarius B2",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Budaiev, Nazar",
 "n_authors": 8,
 "arxiv_id": "2506.09115",
 "doi": "10.3847/1538-4357/adea3b",
 "alma_projects_linked_by_archive": [
  "2016.1.00550.S",
  "2017.1.00114.S"
 ]
}
```

Paper text:
<paper>
# Properties of masers and their associated sources in Sagittarius B2

## Abstract

We present high-resolution Karl G. Jansky Very Large Array observations of the 22 GHz maser line in the extended Sagittarius B2 cloud. We detect 499 masers across the observed velocities between -39 and 172 km s$^{-1}$. To investigate the nature of the masers, we analyze their spatial distribution and cross-match with catalogs of  regions and protostellar cores. 62% of masers are associated with protostellar cores and 32% with regions. The nature of the remaining 6% of sources was not established, but is likely associated with protostellar cores. Based on the spatial extent of the groups of masers, we classify them as either outflow-associated or young stellar object (YSO)-associated. We identify 144 unique sites of maser emission: 23 are associated with regions and 94 with protostellar cores, of which 33 are associated with protostellar outflows and 18 with YSOs.

The outflow-associated maser emission is confined to within $<2000$ au of the central continuum source, despite shocked emission extending over tens of thousands of au. The YSO-associated masers show a lack of detections at $5 < V_{rel} < 30km~s\ensuremath{^{-1}}$, which we suggest may be due to maser self-absorption. We show how masers trace the large-scale material flow in Sgr B2 N (North) also seen in and mm continuum emission. Finally, we find that protostellar cores with associated masers tend to have brighter 3 mm continuum emission on average, although there is no strong correlation between maser brightness and continuum flux.

show\]nbudaiev@ufl.edu

# Introduction

The Central Molecular Zone (CMZ) hosts some of the most extreme star-forming conditions in the Galaxy, with elevated gas temperatures, high turbulence, and strong magnetic fields (cite: Henshaw2022). Within the CMZ, Sagittarius B2 (Sgr B2) is the most massive and active star-forming complex. Located approximately 100 pc from the Galactic center (cite: Reid2009), Sgr B2 contains a network of star-forming protoclusters: North (N), Main (M), South (S), and Deep South (DS), with N and M being the most active centers of massive star formation. Sgr B2 is known for its high star-formation rate (cite: Ginsburg2018). It contains over 50 regions (cite: Meng2022), close to a thousand protostellar cores (cite: Ginsburg2018; Budaiev2024), and over a dozen hot cores (cite: Bonfand2019; Jeff2024). The combination of extreme environmental conditions and clustered star formation makes Sgr B2 a compelling analog for star formation at during the peak epoch of cosmic star formation (cite: Madau2014).

Water maser emission at 22.2350798has long served as a tracer of massive star formation. These masers typically arise from shocks within protostellar outflows, disk winds, or ionization fronts (cite: deJong1973; elitzur1992; liljestrom2000; Goddi2005; Moscadelli2019), and have been used extensively to trace kinematics and proper motions in embedded regions (cite: Goddi2006; Asanok2023; Zhang2024). However, the inability to resolve the immediate environments of individual massive protostars limited the physical interpretation of maser observations. With the advent of Atacama Large Millimeter/submillimeter Array (ALMA) and James Webb Space Telescope (JWST), it is now possible to resolve forming stars and their surroundings within massive molecular clouds (cite: Budaiev2024; Zhang2025; Xu2025; Crowe2025). The high-resolution multi-wavelength observations enable us to revisit existing maser data in the context of resolved feedback, infall, and dynamical interactions within the forming star clusters.

We report high-resolution Karl G. Jansky Very Large Array (VLA) observations of masers in the Sgr B2 cloud. In Section [2](#sec:data), we present the VLA observations and describe the pipeline rerun and imaging procedures, including self-calibration. We then describe the source extraction methods in Section [3](#sec:methods). In Section [4](#sec:analysis), we compare our catalog with the previous observations of masers in the region and cross-match the detections with the existing catalogs of protostellar cores and regions. Finally, in Section [5](#sec:discussion) we investigate the spatial distribution and clustering of masers to determine their nature and analyze the propeties of the associated sources. The summary of the work is provided in Section [6](#sec:conclusions).

# Observations and Data Reduction

## Observation description

The observations of the 22.2350798maser line towards Sgr B2 are a part of VLA project 18A-229 (PI: A. Ginsburg). The data were collected in two observing sessions on March 28th and 29th, 2018 using A configuration. The three fields covered a 10.6 $\times$ 6field of view extending from Sgr B2 N to DS (Fig. [1](#fig:overview_flux)). The observations were centered on 22.2330969to account for the velocity of the cloud ($V_{\mathrm{LSR}}=60km~s\ensuremath{^{-1}}$), with a total bandwidth of 16 MHz and a channel width of 0.07km s$^{-1}$. The beam size is $0.\ensuremath{''}16\times0.\ensuremath{''}06$ (cite: GRAVITY2022). The total on-source time is just under 42 minutes for each of the three fields. The observations used 1331+305=3C286 as the flux calibrator, J1733-1304 as the bandpass calibrator, and J1744-3116 [^1] as the phase calibrator. We note that the labels for fields “MS" (Main-South) and “SDS" (South-Deep South) are swapped in the observation logs, but only for K-band observations. The “MN" (Main-North) field is labeled correctly. In this paper, we refer to fields based on what was observed, but the reduction code primarily uses the observational log’s labels.

## Pipeline rerun

Due to the extreme brightness of the observed masers (up to 200) the standard pipeline would flag most of the signal as radio frequency interference. We reran the VLA pipeline (version 6.4.1.12) with manually specified continuum (signal-free) channels and Hanning smoothing turned off.

## Antenna flagging, channel flagging, scan flagging

Upon inspection of amplitude vs. frequency plots, we identified problematic antennas ea18 and ea05, which we subsequently flagged in both measurement sets. Upon further evaluation of the data, we discovered that the fourth scan for each field in the measurement set observed on March 28th produces images with much higher noise and more spatially spread out flux, which could not be addressed with self-calibration. Thus, we excluded the fourth scan for both measurement sets.

## Spatial offset between two measurement sets

Upon inspection of the preliminary images from the two measurement sets, we discovered a spatial offset in emission. The maser locations were spatially offset by $\sim$0.$''$1 in all fields between the two measurement sets, primarily in the North-South direction. There are several possible explanations for this offset, but the true source could not be established. The two measurement sets were observed only one day apart; thus, the offset cannot be attributed to proper motion.

In addition, the quality of the phase solutions was not uniform over different scans, with the earlier scans having worse solutions. This was particularly the case for the measurement set observed on Match 28th. As the result, the peak of the emission is not aligned between scans, which could have contributed to the offset.

Finally, some of the offset can be attributed to VLA’s absolute pointing accuracy. The best-case pointing accuracy for the observing configuration is $\sim$10 mas. However, the observing conditions, especially the low elevation of Sgr B2, can significantly impact the final pointing accuracy.

We imaged both measurement sets with a manual input model such that the data converge to the same location and aligned the image with high-resolution ALMA continuum from (cite: Budaiev2024). The details of this process are explained in Sections [2.5](#sec:self-calibration), [2.6](#sec:cube_imaging), and [2.7](#sec:wcs_shift).

![](overview_masers_flux.png)

## Maser self-calibration

We self-calibrated the data on the channel with the brightest maser emission in each field. Considering the spatial offset between the measurement sets and the scans described in the previous section, we use a manually generated input model for the first round of self-calibration. The model consists of a single pixel located in the average position of the brightest maser between two measurement sets. As a result, all scans and measurement sets converge to a single location, so the measurement sets can be imaged together.

![image](MN_before.png) ![image](MN_after.png)

We applied the self-calibration solution tables to the continuum spectral windows to produce a 22 GHz continuum map of Sgr B2 (see Appendix [9](#app:continuum_image) and Figure [18](#fig:continuum_22GHz)). The continuum image is later used to astrometrically align these observations to ALMA observations of the same region (see Section [2.7](#sec:wcs_shift)). Figure [2](#fig:MN_calibration) demonstrates the improvement gained with self-calibration: better phase solutions result in more concentrated emission. The fully reduced continuum files are available on Zenodo via doi:[10.5281/zenodo.15747715](https://doi.org/10.5281/zenodo.15747715).

## Cube imaging

Computational constraints were the driving factor in the selection of most of the imaging parameters. We downselect the cube for imaging: we exclude the first and last 32 channels. We inspect these channels separately to ensure that there are no masers present. We also restrict the imaged area to 6 $\times$ 6for each field. At the edges of the square field of view, the primary-beam response ranges between 0.33 for the inscribed circle radius and 0.08 for the circumscribed circle radius. With these restrictions the size of one cube for each field was $\sim$700 GB.

We use CASA’s (cite: McMullin2007) *automultithresh* automatic masking algorithm to generate cleaning masks. Due to the volume of data, it is impractical to perform interactive cleaning. However, *automultithresh* was developed on ALMA data and does not perform as well with the data in hand. For example, after the first $\sim$10 individual masks were created in a channel, the algorithm would begin masking artifacts and the number of masks would rise rapidly. Masking and consequently cleaning artifacts results in inaccurate flux measurements. Thus, we adjusted *automultithresh* parameters until there were no more than 10 masks per channel. While some of the fainter sources in a channel may not get masked, the brightest ones, responsible for the most artifacts, do get masked.

These masks are used for the remainder of the cleaning process. We then clean each cube to several threshold levels (2, 0.5, 0.1) and inspect the results for divergence or overcleaning when each cleaning threshold is reached.

The final imaged velocity range is from -39.14km s$^{-1}$ and 172.06km s$^{-1}$, with a spectral resolution of 0.07km s$^{-1}$. The per-channel median-absolute-deviation-based (MAD) standard deviation for each channel, which is used as a noise estimate, is shown in Figure [3](#fig:noise).

![](cube_noise.png)

The imaging process took approximately one month of computational time for each of the three cubes using the University of Florida Research Computing machine HiPerGator.

## WCS shift

After successfully self-calibrating on a bright maser to an arbitrary location, we perform spatial alignment. We applied the resulting self-calibration tables on the continuum spectral windows of the observations to obtain a well-behaved 1.3 cm continuum image. Then, we use the phase cross-correlation algorithm from the `scikit-image` python package (cite: scikit-image). We then cross-correlate the 3 mm ALMA continuum image (cite: Budaiev2024) with the 1.3 cm continuum image. The two data sets have similar resolutions. The ALMA observations happened 8 months prior to the VLA observations, thus any expected deviations due to proper motions are negligible. ALMA’s absolute astrometry for long-baseline observations is $\sim$10% of the beam size, 70 au in our case, and is better than that of the VLA.

The northernmost field observed by VLA has a similar field-of-view to that of the ALMA 3 mm observations. We select five regions of bright, extended emission to perform cross-correlation (Sgr B2 M, two extended regions near Sgr B2 N, and two extended regions near Sgr B2 M). We then take the average of the results and propagate the errors; the final cross-correlation error is 0.19 pixels (3.6 mas).

We bootstrap our WCS solutions from the northernmost field to the remaining two fields by spatially fitting the locations of masers. We identify the four brightest masers within the spatial overlap between all fields. For each maser, we select the channel with the brightest emission and fit a 2D Gaussian to each maser. We then calculate the shift in pixels. Between the four masers, the calculated coordinate shift variation was no larger than 3% of the offset distance. We take the average offset from the four measurements and apply it to the remaining two fields by editing the ‘CRVAL’ in the FITS headers of the maser cubes. The propagated error is 0.2 pixels (4 mas).

The best-case absolute positional accuracy of our observations is $\sim$0.3 pixels (6 mas, 50 au). However, we caution the reader that the reported uncertainty is not necessarily representative of true uncertainty (e.g. cross-correlation does not account for the changes in physical properties of the observed objects in the 22 and 100 GHz images).

# Methods

## Source extraction

We utilized `astrodendro` (cite: Rosolowsky2008), a dendrogram-based python package to extract sources. Due to the large number of extremely bright ($>$ 100 ) masers, the per-channel noise varies significantly throughout the cube. Since `astrodendro` is not designed to work with varying noise, we implemented an approach to split the cube into smaller cube chunks with similar noise.

First, we calculated the standard deviation based on the MAD for each channel, which should be representative of the noise even in channels with several bright masers. Then, we defined noise bins that will determine how the cube will be split: the first noise bin was defined as the lowest noise in the cube and twice that value. The next noise bin starts at the previous value and ends at twice that, and so on. This ensures that the assumed noise for the source extraction algorithm will be different by no more than a factor of two from the actual noise. Then, all consecutive channels that fall into the same noise bin are grouped into chunks. After the channel chunks are determined, we expand each chunk range by one on each side such that all chunks now overlap by two channels. This is done to simplify the source extraction pipeline later on, as the dendrogram will pick up any source that has rising spectrum within a chunk but peaks outside outside of the relevant channel chunk.

Finally, we run `astrodendro` on each of the channel chunks on the non-primary-beam-corrected images. After preliminary testing, we determined that the three imaged fields require slightly different parameters to achieve the best balance between the number of true positives and false positives. We fix the *num_pix* at 45 (the number of pixels per beam), varied the *min_value* parameter, and set the *min_delta* to 0.7 the *min_value* parameter). We start at *min_value* equal to four times the highest noise in each chunk (equivalent to eight times the lowest noise) and gradually increased the threshold until the number of false positives was less than number of true positives with a by-eye inspection. The final *min_value* parameters for each field were: 16 for MN, 14 for MS, and 10 for SDS.

Next, we combine the dendrogram-generated catalogs from each of the chunks. Since the neighboring channel chunks overlap by two channels, we remove all detections in the edge channels for each of the chunks. This ensures that the rising emission profile of the line that peaks in the following chunk is not cataloged as a source in the preceding chunk. This removed all false positives detections caused by any source that lies outside, but close to, the channel chunk. We construct the final catalog by combining the merged catalogs from each of the fields. If a source is present in multiple fields, we prioritize the distance to the center of the imaged field as the selection criteria.

## Completeness estimation

To estimate the noise, we used the MAD standard deviation for each channel from Figure [3](#fig:noise). The typical noise in a signal-free channel is 11. The presence of bright emission results in a higher per-channel noise, primarily between 50 and 90 km s$^{-1}$. The brightest masers are abundant in Sgr B2 N and M, thus the field covering Sgr B2 S and DS stands out with the lower noise.

The sensitivity of our data varies radially (due to radio beam sensitivity drop-off), varies with frequency (due to some channels containing bright emission that cannot be fully cleaned), and varies spatially (due to local artifacts within a single channel). The varying sensitivity complicates the completeness estimation. We estimated the completeness based on the noise statistics of the extracted sources. This is important because if the majority of the sources were extracted near channel 1450, where the noise is $\sim$100, then the completeness value is much higher than if the majority of detections came from channels with $\sigma = 11\mjyb$.

We show the distribution of channel noises from which the sources were extracted and the sources’ brightnesses in Figure [4](#fig:completeness). 93% of sources were extracted from channels with noise below 0.046. Thus, we choose 0.046 as our representative noise for the completeness calculation. As described in Section [3.1](#sec:source_extraction), the signal-to-noise threshold was different for each field: 16 for MN, 14 for MS, and 10 for SDS. We choose $14\sigma$ as a representative completeness for our sample. Thus, we estimate our catalog completeness to be 0.66. While several assumptions were made to obtain this catalog completeness, it should be representative for the majority of the sample.

![](completeness_estimation.png)

We report the isotropic maser luminosities for each detection assuming d=8.277 (cite: GRAVITY2022). The histogram of the luminosities is shown in Figure [5](#fig:luminosities).

![](luminosity_histogram_jy_kpc.png)

## Spatial fitting, spectral fitting with pyspeckit

We fit the dendrogram-detected sources spatially and spectrally to increase the precision of our measurements. We use the location and flux of the brightest pixel in each source as input parameters for fitting. First, we fit sources spatially with a 2D Gaussian fitting in the channel with brightest emission. We visually inspect each detection and reject any spurious detections caused by beam sidelobes or imaging artifacts. Only 8 sources out of the 499 had unsatisfactory fits and are marked as such in the catalog (see Table [1](#tab:catalog)). The median fit uncertainty is 0.1 pixels (2 mas) in Right Ascension and 0.2 pixels (4 mas) in Declination. The relative positional uncertainty in the catalog is $<$5 mas ($<$50 au at Sgr B2’s distance).

In addition, we inspect the spectra of each source. In rare occasions, *automultithresh* masking would result in unphysical changes in brightness in the channel preceding the mask. Consequently, `astrodendro` would identify these as sources. We reject these detections at this step.

With the selected *min_delta* parameter, `astrodendro` was successful at spatial de-blending for the majority of clustered sources. While some sources were merged and thus identified as a single detection, the conclusions drawn in this work are unaffected.

We then fit the sources spectrally using `pyspeckit` package (cite: pyspeckit). We center on each detection with a range of 140 channels. To make the automated fitting process more robust, we add additional guesses to the spectra: we search the $30\times30\times140$ subcube around the cataloged detection for other detections, and us their extracted parameters as initial guesses. We us 0.1km s$^{-1}$ as the FWHM guess, similar to the channel width. Again, we inspect each fit and refit the unsuccessful fits manually using the GUI interface available in `pyspeckit`. The full width at half maximum for each source is $<$0.1km s$^{-1}$ (1.5 channels), indicating that all sources are unresolved spectrally.

The final catalog contains 499 maser detections in the Sgr B2 molecular cloud shown in Figures [1](#fig:overview_flux) and [6](#fig:overview_velocities). The sample from the catalog is shown in Table [1](#tab:catalog). The full catalog is available in machine-readable format.

![](overview_masers_velocity.png)

# Analysis

![](velocity_vs_dec.png)

## Comparison with McGrath 2004 catalog

The previous observations of masers in the extended regions of Sgr B2 were described in (cite: McGrath2004). Their velocity coverage is between -40 and 120km s$^{-1}$, with a spectral resolution of 0.66km s$^{-1}$, compared to ours of between -39 and 172km s$^{-1}$ at 0.07km s$^{-1}$. (cite: McGrath2004) report the typical rms noise in a line-free channel as 1, compared to 0.011 in our data. Accounting for their slightly larger beam, our absolute sensitivity is 12 times better than their rms noise. Spatially, our observations extend further in the negative declination, covering the younger part of Sgr B2 (DS). With better sensitivity, higher spatial resolution, and larger spectral coverage, we detect $\sim$2.5 times more masers in the overlapping part of the fields of view.

Their observations were conducted in June 1998, resulting in a $\sim$20 year baseline between the observations. masers are known to vary on much shorter timescales (cite: Zhang2024). As expected, we find significant changes in source brightnesses. Due to the high source density and the large time baseline between two observations, it is impractical to perform variability analysis.

The distribution of fluxes above the common completeness limit is similar between the two catalogs. This similarity could be coincidental with two observations having similar flux distributions by chance. Alternatively, and more likely, it may suggest that the overall flux distribution remains relatively stable over time, with only a few bright outliers, caught near the peak of their variability cycles, dominating the detectable maser emission. Thus, the population-level statistics shown in this work are likely to remain consistent over time. Follow up VLA observations of the region will show whether the underlying flux distribution persists across multiple epochs.

We cross-match our catalog with the catalog from (cite: McGrath2004) and show the locations of masers without spatial matches within 0.$''$5 ($\sim$4000 au). The details of the cross-matching process are described in Section [4.2](#sec:proper-motion). The cross-match search radius is several times larger than the resolution of either observation to highlight locations not previously associated with masers. Figure [8](#fig:overview_new_detections) shows the spatial distribution of the new and absent maser detections.

![](overview_masers_new_detections_with_reid.png)

## Maser relative proper motion

Upon comparing the spatial distributions of our catalog and that of (cite: McGrath2004), we found a consistent shift present in all sources in the North-South direction. The systemic shift indicates a poor astrometric accuracy of one (or both) of the observations.

We quantify the positional offset by cross-matching detections between the two catalogs. To ensure robust matches, we select sources that are isolated and have $<5km~s\ensuremath{^{-1}}$ velocity difference between the two catalogs. Since a large fraction of masers are detected in groups, only nine sources meet the above criteria.

For these matched sources, the average positional separation between our catalog and that of (cite: McGrath2004) is 0.$''$03 (250 au) in RA and -0.$''$12 (1000 au) in Dec. Over the 20-year baseline between observations, this offset implies a proper motion of the cloud of $\sim270km~s\ensuremath{^{-1}}$, significantly larger than values suggested by previous observations and models (cite: Kruijssen2015; Sormani2020; Takeshi2022). (cite: McGrath2004) report an absolute astrometric accuracy of $\sim$0.$''$01 based on alignment of the centroids of continuum emission from regions with those of (cite: Gaume1995). However, we were unable to access either continuum dataset to compare with ours.

Our VLA observations are astrometrically aligned to those of ALMA, which typically offer superior absolute positional accuracy. Given the lack of independent verification for the (cite: McGrath2004) absolute positions and the alignment of our data with ALMA, we conclude that the positions reported by (cite: McGrath2004) are likely offset from the true source locations. While readers should be aware of the potential absolute astrometric uncertainties in both datasets, the conclusions in this work are based on comparisons with the ALMA continuum to which the current VLA observations were aligned, and thus are not affected by the absolute astrometric calibration.

We shift the (cite: McGrath2004) catalog by the calculated systemic offset. The relative, source-to-source proper motions for the nine cross-matched sources are shown in Figure [9](#fig:proper_motion). Both (cite: McGrath2004) and our catalogs have relative source positional accuracy of 0.$''$005. However, (cite: McGrath2004) did not report their source extraction methods, so the validity of their uncertainty could not be verified. Thus, we choose 10 mas as a representative uncertainty for the error bars.

Two masers have proper motions over 100km s$^{-1}$, much higher than the typical 1D velocity dispersion of $\sim$12km s$^{-1}$. Such high proper motions are more consistent with the velocities we expect from outflows, oriented along the plane-of-sky. Indeed, for all but one source, the line-of-sight velocities are within 10km s$^{-1}$ of the $V_{\mathrm{LSR}}$ of the cloud, which is consistent with the plane-of-sky outflows.

We note that such relative proper motions are proof-of-concept rather than robust measurements. masers are known to vary on much shorter timescales than the two-epoch baseline of 20 years. These results should be interpreted as part of a larger discussion on measuring cloud proper motion (see Section [5.4](#sec:PM_Reid)).

![](PM_after_shift.png)

## Maser associations

We cross-match the maser detections with foreground stars, protostellar cores, and regions.

We use VLA- (cite: DePree1998; DePree2015; Meng2022) and ALMA-based (cite: Ginsburg2018; Budaiev2024) catalogs of regions augmented with JWST MIRI data (N. Budaiev 2025, in prep). We associate a maser with an region if it is either within the physical boundaries of an region, or, for unresolved sources, is within one beam of the detection. 162 masers (32%) are associated with regions, with none associated with regions larger than 0.025 pc (5000 au).

masers are known to trace currently-forming, very massive stars and evolved massive stars. We identify evolved stars by cross-matching isolated masers with masers from the large ALMA survey ACES (S. Longmore in prep). As we have already identified region-associated masers, we exclude any masers within 0.3 pc of known regions. Using a search radius of 0.1 pc, a single match is identified. We confirm the classification with JWST data (N. Budaiev 2025, in prep.) which also have a detection in all observed filters between 1.5 and 25 $\mu m$.

The source also has faint 3 mm emission, also typical for an evolved massive star. Thus, we classify this maser as associated with an evolved massive star.

We then cross-match the masers with mm continuum data to find protostellar core associations. Having already classified massive evolved stars and regions, we have minimized the risk of contamination. We utilize the $\sim$1000 au resolution catalog from (cite: Budaiev2024) and a $\sim$5000 au resolution catalog that covers the extended cloud (cite: Ginsburg2018). If no match is found (or no data are available) within a 0.$''$3 ($\sim$2500 au) search radius of the higher-resolution data, we search within 0.$''$5 ($\sim$4500 au). In total, we find 259 sources associated with protostellar cores via cross-matching. 55 remaining masers have no matches between $\mu$m and cm wavelengths and are marked as “no match" (see Table [1](#tab:catalog)).

# Discussion

## Nature of water masers

To our knowledge, this is the first work that investigates the properties of masers and their associated star-forming objects within one site of massive star formation with statistically significant samples for different populations. Thus, the differences in the properties of different populations of masers can be attributed directly to their nature rather than the varying environment in the different star-forming regions.

![](source_nature_on_contunuum.png)

### Classifying masers around protostellar cores

In Section [4.3](#sec:associations), we associated masers with foreground stars, regions, and protostellar cores. We now further classify the masers associated with protostellar cores and those that did not have any matches in the existing continuum catalogs into two groups: masers collisionally pumped by the YSO’s outflow and masers attributed to different physical processes other than outflows (e.g. due to disk-winds, polar winds, radiative effects). In this work, we refer to them as “outflow-associated" and “YSO-associated," respectively. The main differentiating criteria between the two population is the spatial extent of the maser groups. The outflows can extend to thousands of aus and, correspondingly, so can the collisionally-pumped masers. Meanwhile, other physical processes are confined to few hundreds of au. Observations with VLBI or the ngVLA will allow us to distinguish between the different origins of YSO-associated masers through high spatial resolution or kinematic information. Since the “no match" masers likely do have dust continuum associations that are below the sensitivity limit, we combine them with the protostellar core-associated masers for a total sample of 336 sources.

We the use DBSCAN algorithm to cluster the maser features. We then classify the clusters based on their properties. If the maximum separation between members of each cluster is below 100 au, we classify all sources within this group as “YSO-associated". Otherwise, they are classified as “outflow-associated" (see Figure [11](#fig:zoom_in_DS4)).

We set the minimum separation required for two groups to be considered distinct to be d$_{\mathrm{min}}$= 500 au. Additionally, we visually inspect each cluster to identify if any group of masers that follow a larger outflow pattern were separated due to the selection parameters, but find no such cases.

We examine the spatial distribution of masers relative to SiO (5-4) outflows in Sgr B2 S and DS. Figure [11](#fig:zoom_in_DS4) shows one such object.

We find that the sources with structured outflows have associated masers distributed over hundreds of au, consistent with their outflow-correlated classifications.

We do not consider the location of the emission relative to the continuum source to perform classifications. A maser located close, but not on top of the flux contour, could be either from the outflow of a given continuum source or from the fainter, not-detected YSO.

Similarly, we do not consider the velocity relative to the cloud or neighboring masers. While the outflow-associated masers can reach $\sim$ 100km s$^{-1}$, YSO-associated masers can reach similar speeds due to the YSO’s rotation or wind speed.

Assuming that masing occurs within the rotating, edge-on disk, we can expect orbital velocities as high as 150km s$^{-1}$ for a 10M$_\odot$ star at 1 au or 50km s$^{-1}$ at 10 au.

We note that these selection criteria do not distinguish between the populations perfectly. For instance, a perfectly face-on outflow will be categorized as “YSO-associated". A “chain" of YSOs in a filament, below the sensitivity limit, each having a maser will be classified as an outflow. An outflow producing a few closely-spaced masers in one location would be classified as “YSO-associated". Finally, if masing occurs in both the outflow and in the YSO, we classify all detections as “outflow-associated". However, despite these possible misclassifications, the findings should be generally representative of the two populations. The remaining sources are marked as “ambiguous".

We determine the number of sites of maser emission based on source clustering and cross-matching.

We define a “site" as a group of masers distinctly associated with one object via DBSCAN-determined clusters for YSO-associated and outflow-associated masers and via cross-matching results for the ambiguous and region-associated masers. We identify 18 sites of YSO-associated masers with 53 individual detections, 33 sites of outflow-associated masers with 214 detections, 23 sites of region-associated masers with 162 detections, and 69 “ambiguous" sites. We note that 43 of the “ambiguous" sites have a match in protostellar core catalogs. Here, “ambiguous" only refers to whether we are able to establish the physical processes responsible for the maser emission. The remaining 26 sites with one detection in each are unclassified, but are likely associated with protostellar cores below the previous surveys’ sensitivity limits.

Finally, one maser site is associated with an evolved star. Bringing the total number of independent sites of maser emission to 144. The zoom-ins for each site of maser emission, similar to those shown in Figure [11](#fig:zoom_in_DS4), are available on Zenodo[^2] via doi: [10.5281/zenodo.15747715](https://doi.org/10.5281/zenodo.15747715)

.

![](DS_zoom_in_DS4.png)

![](DS_zoom_in_2.png)

### Properties of different populations of masers

We show the flux distributions of the different populations of masers for individual detections in Figure [12](#fig:flux_histogram) and for sites of maser emission in Figure [13](#fig:flux_histogram_clusters). The flux distribution of masers associated with regions peaks at $\sim$3 Jy, a factor of four above our completeness limit. The majority of the masers associated with regions are located in Sgr B2 M, with most of the remaining ones being in Sgr B2 N, as shown in Figure [10](#fig:overview_spatial). High spatial density and the presence of extremely bright masers worsens our completeness limit within the clusters.

We perform the Kolmogorov-Smirnov (KS) test on the flux distributions of the outflow-associated and YSO-associated masers. The resulting p-value of 0.0022 indicates the underlying distributions are a likely different between the two populations of masers. To our knowledge, this is the largest sample of masers classified by origin. Future, deeper observations with the new generations of radio interferometers would be needed to verify the difference in flux distributions and explore it in other environments.

![](peak_flux_kde_with_ambiguous.png)

![](peak_flux_histogram_with_ambiguous.png)

![](peak_flux_histogram_clusters.png)

We do not find any correlation between the separation between the maser, the associated source, and the brightness of the maser, which matches the conclusions of a more sensitive survey by (cite: Moscadelli2020). This highlights that the absence of masers at far distances from YSOs, even with extended outflows visible in SiO, is not due to the decreasing brightness of the masers further in the outflow.

We compare the observed line-of-sight velocity of the masers to their flux. We do not find any correlation across the different populations of masers. This matches previous high-resolution surveys of masers (cite: Moscadelli2019). A histogram of maser velocities broken down by population is shown in Figure [14](#fig:velocity_histogram). The YSO-associated masers appear to have blue-shifted velocities, whereas the outflow masers average to the mean cloud velocity. It is unclear what is causing the velocities of the YSO-associated masers to be negative on average. Below, we discuss several possibilities.

We analyze the spatial distribution of each population of masers (see Figure [10](#fig:overview_spatial)). If the majority of the YSO-associated masers are constrained to a small area of the sky, it might indicate that these sources are associated with another star-forming region along the line of sight. However, these maser detections are distributed throughout the cloud, and thus are most likely part of Sgr B2 complex.

The selection criteria was based on the spatial extent of the groups of the sources. In case our interpretation of the nature of the maser emission is erroneous, we still observe that tightly-clustered groups of masers have on-average negative velocities relative to the cloud.

The distribution of the velocities of YSO-associated masers seem to lack sources at 65km s$^{-1}$ $<$ V $<$ 90km s$^{-1}$. We explore whether the lack of detections are data-driven. As shown in Figure [3](#fig:noise), the noise is the highest between $\sim50<\mathrm{V}<90km~s\ensuremath{^{-1}}$ with a slight increase at around 70km s$^{-1}$.

We filter the YSO-associated masers to match the average noise in the $\sim50<\mathrm{V}<90km~s\ensuremath{^{-1}}$ range, $\sigma\approx0.7$. The same overabundance of the slightly blue-shifted sources is present. While it is possible that some faint sources are obscured with the higher noise, it is not enough to explain the observed trend completely.

We propose self-absorption of maser emission as a possible explanation for the lack of detection at $65-90km~s\ensuremath{^{-1}}$. maser modeling by (cite: Gray2022) shows that having T$_{dust} = 100-300$ K at gas kinetic temperatures typical for masing can result in absorption. If the maser emission comes from the central region of the YSO and is surrounded by infalling hot dust, the red-shifted emission will end up self-absorbed. Assuming a simple free-fall model for a $M = 20 M\ensuremath{_\odot}$ star at 100 au, a representative source from (cite: Budaiev2024), the expected velocity is $\sim$20km s$^{-1}$, consistent with the gap in the data. The dust temperatures observed around hot cores in the extended Sgr B2 cloud can be as high as 500 K (cite: Bonfand2019; Jeff2024; Moller2025). The absorption attenuates the source just enough to make it undetectable in our observations. The HII region-associated and outflow-associated masers will not be affected by self-absorption due to the lack of foreground high-temperature dust.

The observational parameters of this study are not ideal to determine whether the lack of $65-90km~s\ensuremath{^{-1}}$ masers is due to self-absorption of emission.

Measuring the separations between the YSOs and masers on au scales with VLBI and identifying their locations relative to the infalling gas can test the proposed self-absorption mechanism.

![](velocity_histogram_with_ambiguous.png)

## Properties of the associated continuum sources

Using the maser associations from Section [4.3](#sec:associations), we compare the flux distributions of 3 mm continuum cores with and without matched masers. Figure [15](#fig:cont_hist) shows that the continuum sources are brighter if they have associated maser emission. Of the 371 protostellar cores in Sgr B2 N and M, 31 have a corresponding maser, likely limited by our sensitivity. Following the conclusions of Section 3.2 from (cite: Moscadelli2020), there exist at least twice as many masers in Sgr B2 below our sensitivity limit.

![](cont_flux_matched.png)

We do not find a strong correlation between the 3 mm continuum flux and the maser luminosity as shown in Figure [16](#fig:cont_vs_masers). It has been shown that lower-mass YSOs have a correlation between their bolometric luminosity and total maser luminosity (cite: Bae2011; Urquhart2011), and we can expect the bolometric luminosity to be proportional to the mm continuum. We attribute the lack of correlation in our observations to the spread in the ages of the star-forming clusters – from Sgr B2 M being the oldest with the most regions, and Sgr B2 DS being the youngest.

![](cont_vs_sum_maser_fluxes.png)

### Comparison to other maser observations

We summarize the recent studies of masers in Table [\[tab:maser_studies\]](#tab:maser_studies) to provide the context to this work. Due to the high star formation rate and relative proximity, Sgr B2 is uniquely positioned to investigate maser populations. The 144 sites of maser emission is close to an order of magnitude more than in any other cloud. The observed properties of the different populations of masers, can be used for further interpretation of maser surveys in the CMZ (e.g. D. Ward in prep.)

The maser emission in Sgr B2 would not be detected at the distance one of the most nearby star-forming galaxies: NGC 253. (cite: Gorski2019) report 13 sites of maser emission in NGC 253. Excluding the nuclear kilomaser W1, they observe a range of peak fluxes from 3 to 14.4 after smoothing their spectral resolution to 0.5km s$^{-1}$. After spatially blending all maser emission in Sgr B2, matching the spectral resolution, and placing at a distance of 3.5 Mpc, the observed peak flux would be $\sim$2.1 , which is just below the sensitivity of the currently available observations of NGC 253.

C C B B E B A Name & Type of observations & Telescope & Resolution & Sensitivity & $N$(maser) & $N$(site)\
Sgr B2 (This work) & Star-forming cloud & VLA & 0.1$''$; 0.07km s$^{-1}$ & 0.06(4.1kpc$^{2}$) & 499 & 144\
W49 $^{(a)}$ & Star-forming cloud & KaVA (KVN + VERA) & 0.0012$''$; 0.42 km s$^{-1}$ & $\sim$15(1800kpc$^{2}$) & $\sim$300 & 2-3$^\dag$\
W51A $^{(b)}$& Star-forming cloud & VLA & 1.5$''$; 0.11km s$^{-1}$ & 0.01(0.3kpc$^{2}$) & 999 & $>$20$^\dag$\
Sgr B2 $^{(c)}$ & Star-forming cloud & VERA & 0.0015$''$; 0.21- 0.42km s$^{-1}$ & $\sim$1(68kpc$^{2}$) & 128 & $>$20$^\dag$\
regions $^{(d)}$ & Survey of masers in regions & KVN & 130$''$; 0.21km s$^{-1}$ & 1.5& 74 & 74\
POETS survey $^{(e)}$ & Survey of masers in regions$^*$ & VLBA & $\sim$0.001$''$; 0.42 km s$^{-1}$ & $\sim$0.1& 994 & 36\
HOPS survey $^{(f)}$ & Survey of maser sites in the Galactic plane & ATCA & 0.4–12$''$; 0.42 km s$^{-1}$ & $\sim$0.05–0.& 2790 & 631\
SWAG survey $^{(g)}$ & Survey of masers in the CMZ & ATCA & 30$''$; 0.4km s$^{-1}$ & $\sim$0.02(1.4kpc$^{2}$) & 1227 & 593\
CMZ clouds $^{(h)}$ & Survey of masers in the CMZ clouds & VLA & 2.5$''$; 0.2km s$^{-1}$ & 0.15(10.3kpc$^{2}$) & 56 & $\sim$30\

## Large-scale SiO outflow from Sgr B2 N

Due to their high masses (cite: Sanchez-Monge2017; Schworer2019), Sgr B2 N and M are likely to evolve young massive clusters, similar to the Arches and Quintuplet. The formation and evolution of these massive clusters is still not well understood. The absence of the distributed region population in Sgr B2 N provides a more transparent view of the mass flows in the cluster.

(cite: Schworer2019) reported high accretion rate (0.08–0.16 M$_\odot$ $^{-1}$) via eight filaments in Sgr B2 N. At the same time, (cite: Higuchi2015) see a large-scale outflow in this source. Based on SiO and SO$_2$ emission, they report an outflow rate of $\sim0.4 M\ensuremath{_\odot} \yr^{-1}$ on $\sim$0.1 pc scales.

We show the structure of the outflow in Sgr B2 N on the scale of thousands of aus in Figure [17](#fig:n_outflow), as seen in SiO (ALMA PID: 2016.1.00550.S). The outflow boundaries are neighboring and likely interacting with the filaments that are feeding the proto-cluster. The blue lobe is located between filaments F01-F02 and F03-F04 and the red lobe is located between filaments F07 and F08 defined in (cite: Schworer2019). This orientation aligns with the velocities of the filaments. Such an inflow of material could be responsible for the collimation of the outflow. The  masers, which trace shocked gas, are aligned with the edges of the outflow as seen in SiO emission. This alignment suggests that we are observing the actual physical boundaries of the outflow, unaffected by limitations such as resolution, sensitivity, projection, or optical depth effects. A similar configuration is observed in the massive protostellar outflow W51-North, where  masers are excited at the leading edges of compact SiO outflow lobes (cite: Goddi2020), supporting the interpretation that masers trace shock fronts at the outflow interface. The “outflow" could therefore be a combination of ionization, radiation, and smaller-scale, isotropic outflows within the cluster that are then shaped to appear as a bipolar outflow (cite: Peters2012).

However, the high-resolution data suggest an alternative possibility. The outflow is typically attributed to Sgr B2 N K2 source (e.g. (cite: Higuchi2015), (cite: Schmiedeke2016)). The $\sim$500 au resolution mm continuum catalog shows that Sgr B2 N K2 source splits into three regions (cite: Budaiev2024). Visually, there is only a single source that lies along the outflow axis and thus could be responsible for the outflow: source 17 (see Figure [17](#fig:n_outflow)). While identifying the exact nature of this outflow is beyond the scope of this work,

it is possible that this massive outflow is produced by one, or at most two, accreting objects.

The previously reported properties of the outflow are consistent with those at the early stages of massive star formation (cite: Zapata2010).

![](SgrB2_N_SiO_outflow.png)

## Maser-based proper motions measurements

Currently, the most cited measurements of the proper motion of Sgr B2 come from (cite: Reid2009). The authors used VLBI observations of two masers, both in the hearts of Sgr B2 N and M, and reported an average motion in Galactic longitude of -4.05 mas yr$^{-1}$ ($\sim$160km s$^{-1}$). They acknowledged that the measurement does not account for the internal motion of the masers and thus assign a probable uncertainty of 1 mas y$^{-1}$ ($\sim$40km s$^{-1}$). However, as shown in this work, this uncertainty is significantly underestimated (see Figure [8](#fig:overview_new_detections)). As discussed in Section [5.1](#sec:nature), depending on the pumping mechanism the masers can have relative velocities of over 100km s$^{-1}$. We detect masers with relative velocities of up to 100km s$^{-1}$ and are possibly observationally limited. As seen in Figure [7](#fig:velocity_vs_dec), there are detected sources up to the edges of the observed frequencies. Furthermore, sources in the vicinity of a massive cluster are subject to high gravitational potentials and strong feedback, which can further impact the proper motion measurements. For example, when measuring the velocity dispersion in Sgr B2 via radio recombination lines, (cite: Ginsburg2018CFE) reports a group of regions with $v_{rel} = \sim$28km s$^{-1}$.

(cite: Sakai2023) measured proper motions of 55 masers in Sgr B2 M. They report internal proper motions up to 3.5 mas $^{-1}$ ($\sim$140 km s$^{-1}$), further highlighting the high uncertainty of using a small sample of masers to measure proper motions.

In conclusion, one must take great care when estimating the proper motion of a massive molecular cloud like Sgr B2 using masers with multiple pumping mechanisms. As has been mentioned in the sections above, even with a large sample, it is possible to introduce a large bias in the measurement. For example, if there exists a cloud with a density gradient, which results in regions facing less pressure on one side, such regions will have more masers in the denser side of the expanding shell. If all of the regions are still expanding, measuring their proper motions using masers will introduce a large velocity bias in the direction of increasing density.

Thus, if masers are used to measure the proper motions of the cloud, an analysis of the nature of the masers, and thus the possible biases, should be undertaken. Follow up VLA observations are likely to face issues similar to those described in this work: complicated phase calibration, confusion due to source density and maser variability, and non-standard imaging procedures. Thus, very long baseline observation are more suitable for the studies of maser proper motions. Describing the proper motions within the cloud is one of the key elements to understanding the formation history of the cloud and can provide insights into the 3D kinematics of the CMZ. Alternatively, the dusty cores themselves can be used to measure the proper motions in the CMZ. High-resolution ALMA observations in the Galactic Center began almost ten years ago, allowing for tens of km s$^{-1}$ velocity resolution.

# Conclusions

We presented a catalog of 499 masers in Sgr B2, the most star-forming cloud in the CMZ. We classified the nature of the masers by cross-matching with catalogs of regions, protostellar cores, and massive stars. At this time, Sgr B2 is the only location where we can study population-level properties of masers produced by different star-forming objects within the same environment. We identified 144 unique sites of maser emission, almost an order of magnitude more than in any other cloud. Of those, 23 are associated with regions, 33 with protostellar outflows, and 18 with YSOs.

- The maser produced by YSO outflows extend only up to thousand au scales, compared to the SiO emission which extends up to tens of thousands au.

- 3 mm continuum emission from YSOs is generally brighter if maser emission is present. However, there is no strong correlation between the brightness of masers and the associated mm continuum.

- The YSO-associated and outflow-associated masers seem to have different observable properties: the YSO-associated masers are slightly dimmer; in addition, there is an unexplained tendency for YSO-associated masers to have negative relative velocities on average.

- masers trace the colliding material flows in the center of Sgr B2 N. Combined with high-resolution SiO observations, the large-scale outflow appears to originate from a single star-forming object.

- If masers are used to measure the proper motion of a massive cloud, the nature of the water masers should be established to reduce the uncertainty.

# Acknowledgements

We thank Sheila Sagear and Cara Battersby for helpful discussions about this work. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00550.S, ADS/JAO.ALMA#2017.1.00114. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. A.G. and N.B. acknowledge support from the NSF under AST 2206511. A.G. acknowledges support from NSF under CAREER 2142300 and AST 2206511. C.G. acknowledges financial support by the European Union NextGenerationEU RRF M4C2 1.1 project n. 2022YAPMJH and FAPESP (Fundação de Amparo á Pesquisa do Estado de São Paulo) under grant 2021/01183-8. The authors acknowledge University of Florida Research Computing for providing computational resources and support that have contributed to the research results reported in this publication. URL: http://www.rc.ufl.edu.

N.B. led the analysis, writing, and interpretation. A.G. acquired the observations, oversaw the project progress, and contributed to the interpretation. C.G., A.S-M., and A.S. were instrumental in acquiring the observations and contributed to the interpretation. D.J. contributed to the interpretation. P.S. and C.D.P. were instrumental in acquiring the observations.

# Facilities

VLA, ALMA

# Software

`astropy` (cite: astropy:2013; astropy:2018), `pyspeckit` (cite: pyspeckit), `astrodendro` (cite: Rosolowsky2008), CASA version version 6.6.0.2 (cite: McMullin2007), `scikit-image` (cite: scikit-image).

# Catalog of masers in Sgr B2

We present an excerpt from the catalog of masers in Sgr B2 in Table [1](#tab:catalog). The full catalog is available in machine-readable format.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 0 | 266.832 | -28.384 | 0.0012 | 0.0025 | 0.55676 | -29.35 | 0.076 | TRUE | B24 | 178 | core | YSO | 1 |
| 1 | 266.832 | -28.384 | 0.0003 | 0.0007 | 5.2794 | -25.77 | 0.046 | TRUE | B24 | 178 | core | YSO | 1 |
| 2 | 266.833 | -28.372 | 0.0004 | 0.0008 | 1.85667 | -23.19 | 0.025 | TRUE | No match | No match | No match | Outflow | 19 |
| 3 | 266.834 | -28.384 | 0.0023 | 0.005 | 0.35604 | -17.31 | 0.036 | TRUE | B24 | 19 | HII | HII | 56 |
| 4 | 266.834 | -28.384 | 0.0014 | 0.0029 | 0.44133 | -14.71 | 0.033 | TRUE | B24 | 19 | HII | HII | 56 |
| 5 | 266.834 | -28.384 | 0.0015 | 0.0031 | 0.51742 | -13.32 | 0.041 | TRUE | B24 | 19 | HII | HII | 56 |
| 6 | 266.832 | -28.384 | 0.0004 | 0.0008 | 2.23226 | -10.52 | 0.051 | TRUE | B24 | 178 | core | YSO | 1 |
| 7 | 266.832 | -28.384 | 0.0003 | 0.0006 | 9.76375 | -6.4 | 0.042 | TRUE | B24 | 178 | core | YSO | 1 |
| 8 | 266.832 | -28.386 | 0.0033 | 0.0063 | 0.29287 | -5.37 | 0.028 | TRUE | B24 | 168 | core | Outflow | 20 |
| 9 | 266.83 | -28.385 | 0.0021 | 0.0044 | 0.62262 | -4.62 | 0.023 | TRUE | B24 | 215 | core | YSO | 2 |
| 10 | 266.832 | -28.384 | 0.0002 | 0.0005 | 7.5093 | -4.65 | 0.036 | TRUE | B24 | 178 | core | YSO | 1 |
| 11 | 266.834 | -28.372 | 0.0005 | 0.001 | 1.71108 | 7.0 | 0.021 | TRUE | No match | No match | No match | Outflow | 21 |
| 12 | 266.844 | -28.375 | 0.0022 | 0.0043 | 0.29912 | 9.61 | 0.033 | TRUE | No match | No match | star | Star | 75 |
| 13 | 266.834 | -28.372 | 0.0012 | 0.0024 | 0.4292 | 10.86 | 0.036 | TRUE | No match | No match | No match | Outflow | 21 |
| 14 | 266.829 | -28.385 | 0.0018 | 0.004 | 0.23549 | 13.16 | 0.035 | TRUE | B24 | 227 | core | Outflow | 22 |
| 15 | 266.833 | -28.372 | 0.0004 | 0.0009 | 8.60395 | 15.64 | 0.015 | TRUE | B24 | 4 | core | Outflow | 23 |
| 16 | 266.833 | -28.372 | 0.0012 | 0.0028 | 1.34287 | 16.37 | 0.024 | TRUE | B24 | 4 | core | Outflow | 23 |
| 17 | 266.828 | -28.384 | 0.0016 | 0.0035 | 0.4187 | 16.92 | 0.032 | TRUE | B24 | 229 | core | Ambiguous | 76 |
| 18 | 266.833 | -28.372 | 0.002 | 0.0037 | 0.45586 | 18.17 | 0.034 | TRUE | B24 | 4 | core | Outflow | 23 |
| 19 | 266.832 | -28.386 | 0.0004 | 0.0009 | 2.60437 | 19.01 | 0.029 | TRUE | B24 | 167 | core | YSO | 3 |
| 20 | 266.833 | -28.372 | 0.0015 | 0.0036 | 0.82865 | 19.56 | 0.022 | TRUE | B24 | 4 | core | Outflow | 23 |
| 21 | 266.833 | -28.372 | 0.0012 | 0.0025 | 0.41599 | 20.78 | 0.023 | TRUE | No match | No match | No match | Outflow | 19 |
| 22 | 266.833 | -28.372 | 0.0017 | 0.0035 | 1.38237 | 21.93 | 0.053 | TRUE | B24 | 4 | core | Outflow | 23 |
| 23 | 266.834 | -28.372 | 0.0005 | 0.001 | 3.08462 | 22.04 | 0.015 | TRUE | No match | No match | No match | Ambiguous | 77 |
| 24 | 266.834 | -28.384 | 0.0029 | 0.0051 | 0.59177 | 22.15 | 0.061 | TRUE | B24 | 21 | HII | HII | 57 |
| 25 | 266.832 | -28.386 | 0.0002 | 0.0005 | 8.82692 | 22.34 | 0.037 | TRUE | B24 | 167 | core | YSO | 3 |
| 26 | 266.832 | -28.386 | 0.0062 | 0.0138 | 0.46005 | 23.04 | 0.028 | TRUE | B24 | 168 | core | Ambiguous | 78 |
| 27 | 266.829 | -28.384 | 0.0019 | 0.004 | 0.46551 | 24.27 | 0.025 | TRUE | No match | No match | No match | YSO | 4 |
| 28 | 266.833 | -28.372 | 0.0004 | 0.0009 | 1.75948 | 24.38 | 0.022 | TRUE | B24 | 4 | core | Outflow | 23 |
| 29 | 266.832 | -28.386 | 0.0017 | 0.0037 | 0.64469 | 25.3 | 0.024 | TRUE | B24 | 167 | core | YSO | 3 |
| 30 | 266.833 | -28.371 | 0.0016 | 0.0033 | 0.77047 | 25.53 | 0.028 | TRUE | B24 | 159 | core | YSO | 5 |
| 31 | 266.829 | -28.384 | 0.0008 | 0.0016 | 1.67536 | 29.01 | 0.02 | TRUE | No match | No match | No match | YSO | 4 |
| 32 | 266.833 | -28.372 | 0.0003 | 0.0006 | 20.25269 | 28.94 | 0.047 | TRUE | B24 | 4 | core | Outflow | 23 |
| 33 | 266.834 | -28.385 | 0.0038 | 0.0075 | 0.78611 | 29.23 | 0.024 | TRUE | B24 | 16 | HII | HII | 53 |
| 34 | 266.834 | -28.384 | 0.0032 | 0.007 | 0.24507 | 29.72 | 0.044 | TRUE | B24 | 27 | HII | HII | 62 |

: First 35 entries of the maser catalog in Sgr B2.

# Source extraction with *Duchamp*

We tested source extraction software `DUCHAMP` (cite: duchamp). While this software is more appropriate when working with large 3D cubes, we find that it does not behave well with clustered groups of sources. We were unable to de-blend most of the detections in Sgr B2 N and M.

# VLA 22continuum

![](continuum.png)

We include the 22continuum map used to align the VLA observations to ALMA data. The map is shown in Figure [18](#fig:continuum_22GHz). The reduced fits files for each pointing is available on Zenodo via doi: [10.5281/zenodo.15747715](https://doi.org/10.5281/zenodo.15747715).

natexlab

(ref: Asanok2023) Asanok, K., Gray, M. D., Hirota, T., et al. 2023, ApJ, 943, 79, doi: [`10.3847/1538-4357/aca6f1`](http://doi.org/10.3847/1538-4357/aca6f1)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Bae2011) Bae, J.-H., Kim, K.-T., Youn, S.-Y., et al. 2011, ApJS, 196, 21, doi: [`10.1088/0067-0049/196/2/21`](http://doi.org/10.1088/0067-0049/196/2/21)

(ref: Bonfand2019) Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27, doi: [`10.1051/0004-6361/201935523`](http://doi.org/10.1051/0004-6361/201935523)

(ref: Budaiev2024) Budaiev, N., Ginsburg, A., Jeff, D., et al. 2024, ApJ, 961, 4, doi: [`10.3847/1538-4357/ad0383`](http://doi.org/10.3847/1538-4357/ad0383)

(ref: Crowe2025) Crowe, S., Fedriani, R., Tan, J. C., et al. 2025, ApJ, 983, 19, doi: [`10.3847/1538-4357/ad8889`](http://doi.org/10.3847/1538-4357/ad8889)

(ref: deJong1973) de Jong, T. 1973, A&A, 26, 297

(ref: DePree1998) De Pree, C. G., Goss, W. M., & Gaume, R. A. 1998, ApJ, 500, 847, doi: [`10.1086/305782`](http://doi.org/10.1086/305782)

(ref: DePree2015) De Pree, C. G., Peters, T., Mac Low, M. M., et al. 2015, ApJ, 815, 123, doi: [`10.1088/0004-637X/815/2/123`](http://doi.org/10.1088/0004-637X/815/2/123)

(ref: elitzur1992) Elitzur, M., Hollenbach, D. J., & McKee, C. F. 1992, ApJ, 394, 221, doi: [`10.1086/171574`](http://doi.org/10.1086/171574)

(ref: Gaume1995) Gaume, R. A., Claussen, M. J., de Pree, C. G., Goss, W. M., & Mehringer, D. M. 1995, ApJ, 449, 663, doi: [`10.1086/176087`](http://doi.org/10.1086/176087)

(ref: Ginsburg2018CFE) Ginsburg, A., & Kruijssen, J. M. D. 2018, ApJL, 864, L17, doi: [`10.3847/2041-8213/aada89`](http://doi.org/10.3847/2041-8213/aada89)

(ref: pyspeckit) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022, AJ, 163, 291, doi: [`10.3847/1538-3881/ac695a`](http://doi.org/10.3847/1538-3881/ac695a)

(ref: Ginsburg2018) Ginsburg, A., Bally, J., Barnes, A., et al. 2018, ApJ, 853, 171, doi: [`10.3847/1538-4357/aaa6d4`](http://doi.org/10.3847/1538-4357/aaa6d4)

(ref: Goddi2020) Goddi, C., Ginsburg, A., Maud, L. T., Zhang, Q., & Zapata, L. A. 2020, ApJ, 905, 25, doi: [`10.3847/1538-4357/abc88e`](http://doi.org/10.3847/1538-4357/abc88e)

(ref: Goddi2005) Goddi, C., Moscadelli, L., Alef, W., et al. 2005, A&A, 432, 161, doi: [`10.1051/0004-6361:20042074`](http://doi.org/10.1051/0004-6361:20042074)

(ref: Goddi2006) Goddi, C., Moscadelli, L., Torrelles, J. M., Uscanga, L., & Cesaroni, R. 2006, A&A, 447, L9, doi: [`10.1051/0004-6361:200500230`](http://doi.org/10.1051/0004-6361:200500230)

(ref: Gorski2019) Gorski, M. D., Ott, J., Rand, R., et al. 2019, MNRAS, 483, 5434, doi: [`10.1093/mnras/sty3077`](http://doi.org/10.1093/mnras/sty3077)

(ref: GRAVITY2022) GRAVITY Collaboration, Abuter, R., Aimar, N., et al. 2022, A&A, 657, A82, doi: [`10.1051/0004-6361/202142459`](http://doi.org/10.1051/0004-6361/202142459)

(ref: Gray2022) Gray, M. D., Etoka, S., Richards, A. M. S., & Pimpanuwat, B. 2022, MNRAS, 513, 1354, doi: [`10.1093/mnras/stac854`](http://doi.org/10.1093/mnras/stac854)

(ref: Henshaw2022) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2022, arXiv e-prints, arXiv:2203.11223, doi: [`10.48550/arXiv.2203.11223`](http://doi.org/10.48550/arXiv.2203.11223)

(ref: Higuchi2015) Higuchi, A. E., Hasegawa, T., Saigo, K., Sanhueza, P., & Chibueze, J. O. 2015, ApJ, 815, 106, doi: [`10.1088/0004-637X/815/2/106`](http://doi.org/10.1088/0004-637X/815/2/106)

(ref: Jeff2024) Jeff, D., Ginsburg, A., Bulatek, A., et al. 2024, ApJ, 962, 48, doi: [`10.3847/1538-4357/ad1507`](http://doi.org/10.3847/1538-4357/ad1507)

(ref: Kim2019) Kim, W.-J., Kim, K.-T., & Kim, K.-T. 2019, ApJS, 244, 2, doi: [`10.3847/1538-4365/ab2fc9`](http://doi.org/10.3847/1538-4365/ab2fc9)

(ref: Kruijssen2015) Kruijssen, J. M. D., Dale, J. E., & Longmore, S. N. 2015, MNRAS, 447, 1059, doi: [`10.1093/mnras/stu2526`](http://doi.org/10.1093/mnras/stu2526)

(ref: Lanyi2010) Lanyi, G. E., Boboltz, D. A., Charlot, P., et al. 2010, AJ, 139, 1695, doi: [`10.1088/0004-6256/139/5/1695`](http://doi.org/10.1088/0004-6256/139/5/1695)

(ref: liljestrom2000) Liljeström, T., & Gwinn, C. R. 2000, ApJ, 534, 781, doi: [`10.1086/308781`](http://doi.org/10.1086/308781)

(ref: lu2019) Lu, X., Zhang, Q., Kauffmann, J., et al. 2019, ApJ, 872, 171, doi: [`10.3847/1538-4357/ab017d`](http://doi.org/10.3847/1538-4357/ab017d)

(ref: Madau2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: McGrath2004) McGrath, E. J., Goss, W. M., & De Pree, C. G. 2004, ApJS, 155, 577, doi: [`10.1086/424486`](http://doi.org/10.1086/424486)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Meng2022) Meng, F., Sánchez-Monge, Á., Schilke, P., et al. 2022, A&A, 666, A31, doi: [`10.1051/0004-6361/202243674`](http://doi.org/10.1051/0004-6361/202243674)

(ref: Moller2025) Möller, T., Schilke, P., Sánchez-Monge, Á., & Schmiedeke, A. 2025, A&A, 693, A160, doi: [`10.1051/0004-6361/202451274`](http://doi.org/10.1051/0004-6361/202451274)

(ref: Moscadelli2019) Moscadelli, L., Sanna, A., Goddi, C., et al. 2019, A&A, 631, A74, doi: [`10.1051/0004-6361/201936436`](http://doi.org/10.1051/0004-6361/201936436)

(ref: Moscadelli2020) Moscadelli, L., Sanna, A., Goddi, C., et al. 2020, A&A, 635, A118, doi: [`10.1051/0004-6361/202037472`](http://doi.org/10.1051/0004-6361/202037472)

(ref: Takeshi2022) Oka, T., & Geballe, T. R. 2022, ApJ, 927, 97, doi: [`10.3847/1538-4357/ac3912`](http://doi.org/10.3847/1538-4357/ac3912)

(ref: Peters2012) Peters, T., Klaassen, P. D., Mac Low, M.-M., Klessen, R. S., & Banerjee, R. 2012, ApJ, 760, 91, doi: [`10.1088/0004-637X/760/1/91`](http://doi.org/10.1088/0004-637X/760/1/91)

(ref: Reid2009) Reid, M. J., Menten, K. M., Zheng, X. W., Brunthaler, A., & Xu, Y. 2009, ApJ, 705, 1548, doi: [`10.1088/0004-637X/705/2/1548`](http://doi.org/10.1088/0004-637X/705/2/1548)

(ref: Rosolowsky2008) Rosolowsky, E. W., Pineda, J. E., Kauffmann, J., & Goodman, A. A. 2008, ApJ, 679, 1338, doi: [`10.1086/587685`](http://doi.org/10.1086/587685)

(ref: Sakai2023) Sakai, D., Oyama, T., Nagayama, T., Honma, M., & Kobayashi, H. 2023, PASJ, 75, 937, doi: [`10.1093/pasj/psad052`](http://doi.org/10.1093/pasj/psad052)

(ref: Sanchez-Monge2017) Sánchez-Monge, Á., Schilke, P., Schmiedeke, A., et al. 2017, A&A, 604, A6, doi: [`10.1051/0004-6361/201730426`](http://doi.org/10.1051/0004-6361/201730426)

(ref: Schmiedeke2016) Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143, doi: [`10.1051/0004-6361/201527311`](http://doi.org/10.1051/0004-6361/201527311)

(ref: Schworer2019) Schwörer, A., Sánchez-Monge, Á., Schilke, P., et al. 2019, A&A, 628, A6, doi: [`10.1051/0004-6361/201935200`](http://doi.org/10.1051/0004-6361/201935200)

(ref: Sormani2020) Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497, 5024, doi: [`10.1093/mnras/staa1999`](http://doi.org/10.1093/mnras/staa1999)

(ref: Urquhart2011) Urquhart, J. S., Morgan, L. K., Figura, C. C., et al. 2011, MNRAS, 418, 1689, doi: [`10.1111/j.1365-2966.2011.19594.x`](http://doi.org/10.1111/j.1365-2966.2011.19594.x)

(ref: scikit-image) van der Walt, S., Schönberger, J. L., Nunez-Iglesias, J., et al. 2014, PeerJ, 2, e453, doi: [`10.7717/peerj.453`](http://doi.org/10.7717/peerj.453)

(ref: walsh2014) Walsh, A. J., Purcell, C. R., Longmore, S. N., et al. 2014, MNRAS, 442, 2240, doi: [`10.1093/mnras/stu989`](http://doi.org/10.1093/mnras/stu989)

(ref: duchamp) Whiting, M. T. 2012, MNRAS, 421, 3242, doi: [`10.1111/j.1365-2966.2012.20548.x`](http://doi.org/10.1111/j.1365-2966.2012.20548.x)

(ref: Xu2025) Xu, F., Lu, X., Wang, K., et al. 2025, arXiv e-prints, arXiv:2503.23700, doi: [`10.48550/arXiv.2503.23700`](http://doi.org/10.48550/arXiv.2503.23700)

(ref: Zapata2010) Zapata, L. A., Tang, Y.-W., & Leurini, S. 2010, ApJ, 725, 1091, doi: [`10.1088/0004-637X/725/1/1091`](http://doi.org/10.1088/0004-637X/725/1/1091)

(ref: Zhang2025) Zhang, S., Lu, X., Ginsburg, A., et al. 2025, ApJL, 982, L10, doi: [`10.3847/2041-8213/adb30b`](http://doi.org/10.3847/2041-8213/adb30b)

(ref: Zhang2024) Zhang, Y.-K., Chen, X., Wang, Y.-X., et al. 2024, AJ, 168, 10, doi: [`10.3847/1538-3881/ad428d`](http://doi.org/10.3847/1538-3881/ad428d)

[^1]: As reported in (cite: Budaiev2024), VLA phase calibrator J1744-3116, which is used for many observations of Sgr B2, has wrong coordinates recorded in the VLA catalogs when compared to other catalogs, such as (cite: Lanyi2010).

[^2]: The files are also available on GitHub: [https: //github.com/nbudaiev/SgrB2_VLA_water_masers/tree/ master/zenodo_zoomins](https://github.com/nbudaiev/SgrB2_VLA_water_masers/tree/master/zenodo_zoomins)

</paper>

Write the methods card for this paper.