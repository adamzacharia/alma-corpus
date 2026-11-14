# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A..84N\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...687A..84N",
 "title": "Core to ultracompact HII region evolution in the W49A massive protocluster",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Nony, T.",
 "n_authors": 13,
 "arxiv_id": "2404.02250",
 "doi": "10.1051/0004-6361/202449279",
 "alma_projects_linked_by_archive": [
  "2016.1.00620.S"
 ]
}
```

Paper text:
<paper>
# Core to ultracompact HII region evolution in the W49A massive protocluster

We aim to identify and characterize cores in the high-mass proto-cluster W49, determine their evolutionary stages and measure the associated lifetimes.

We built a catalog of 129 cores extracted from an ALMA 1.3 mm continuum image at 0.26$\ensuremath{''}$ (2900 au) angular resolution. The association between cores and Hyper/Ultra Compact HII (H/UC HII) regions was established from the analysis of VLA 3.3 cm continuum and H30$\alpha$ line observations. We also looked for emission of hot molecular cores (HMCs) using the methyl formate doublet at 218.29 GHz.

We identified 40 cores associated with an H/UC HII region and 19 HMCs over the ALMA mosaic. The 52 cores with an H/UC HII region and/or a HMC are assumed to be high-mass protostellar cores,

while the rest of the core population likely consists in prestellar cores and low-mass protostellar cores. We found a good agreement between the two tracers of ionized gas, with 23 common detections and only four cores detected at 3.3 cm and not in H30$\alpha$. The spectral indexes from 3.3 cm to 1.3 mm range from 1, for the youngest cores with partially optically thick free-free emission, to about -0.1, that is optically thin free-free emission obtained for cores likely more evolved.

Using as a reference the H/UC HII regions, we found the statistical lifetimes of the HMC and massive protostellar phases in W49N to be about $6\times10^4$ yr and $1.4\times10^5$ yr, respectively. We also showed that HMC can co-exist with H/UC HII regions during a short fraction of the core lifetime, about 2$\times10^4$ yr. This indicates a rapid dispersal of the inner molecule envelope once the HC HII is formed.

# Introduction

The evolutionary sequence and timescales of the formation of high-mass stars are still poorly constrained (cite: 2018Motte), partly because of observational difficulties related to low-number statistics and large distances within the Milky Way. W49A is among the few molecular clouds that enable us to study, in a single region and with robust statistics, various evolutionary stages of high-mass star formation. Young, massive protostars first drive strong molecular outflows and heat the inner part of their envelope. Complex organic molecules (COMs) are released from the grains in the heated region (cite: 2009ARA&A..47..427H), which is called hot molecular core (HMC) and is thus characterized by multiple lines from COMs - the so called "line forest". Contrarily to their low-mass analogs, high-mass protostars are still embedded in their nascent envelope when they evolve to the main sequence. The extreme ultraviolet (EUV) radiation from high-mass stars (\>8 $\ensuremath{M_{\odot}}$) is sufficient to ionize hydrogen and create an HII region (cite: 2002ARA&A..40...27C). As the luminosity of the star keeps increasing, the HII region expands and breaks through the core, and eventually impacts the whole molecular cloud. Hypercompact (HC) HII regions are usually interpreted as the youngest stage of ionization by a massive star (cite: 2007ApJ...666..976K; 2016ApJ...818...52T), confined to within cores to sizes $\sim 10^{-2}$ pc, or even less, and having electron densities $n_e > 10^6$ cm$^{-3}$ (cite: Kurtz05). Ultracompact (UC) HII regions are, by definition, expected to be larger and less dense by at least one order of magnitude. However, deep centimeter surveys of protocluster regions (cite: 2016A&A...595A..27G) have shown that the most common type of hypercompact sized HII regions have lower densities, in the range $10^4$ to $<10^6$ cm$^{-3}$ (cite: 2020ApJ...899...94R). Since a reliable distinction between these two types of objects requires modeling of the cm to (sub)mm spectral energy distribution (cite: 2008ApJ...672..423K; 2009ApJ...706.1036G; 2022ApJ...936...68Z), we refer to all our detections of small HII emission as H/UC HII regions.

W49A, located at a distance of 11.1 kpc from the Sun (cite: 2013ApJ...775...79Z), is one of the most luminous protoclusters in the Galaxy ($L \sim 2.6\times10^{7}\ensuremath{L_{\odot}}$, (cite: 1991A&A...251..231S; 2016ApJ...828...32L)). The W49A giant molecular cloud (GMC) has been mapped from $\sim 100$ pc to sub-pc scales in the (sub)millimeter continuum and in molecular lines, down to angular resolutions of a few arcseconds (cite: 2009PASJ...61...39M; 2010A&A...520A..84P; 2013ApJ...779..121G; 2020MNRAS.497.1972). The W49A GMC can be divided in three subcomponents labeled W49 north (W49N), W49 south (W49S), and W49 south-west (W49SW). From CO observations, (cite: 2013ApJ...779..121G) evaluated the gas mass of the W49A GMC within a radius of 60 pc to be $10^6\,\ensuremath{M_{\odot}}$, with the main star-forming hub W49N concentrating $M_{\rm gas} \sim 2\times10^5\,\ensuremath{M_{\odot}}$ within a radius of 6 pc. A cluster of massive stars with a total mass of about $10^4\,\ensuremath{M_{\odot}}$ has been identified in the near infrared by (cite: 2005A&A...430..481H), at about 3 pc east of the center of W49N. The study of (cite: 2015ApJ...813...25S) with *Spitzer* also revealed 232 Class 0/I Young Stellar Objects in the entire W49A GMC. About 50 HC and UC HII regions have been detected in W49A (cite: 1987Sci...238.1550W; 1997ApJ...482..307D; 2020AJ....160..234D). The embedded and infrared-visible stellar populations drive already significant feedback across the GMC (cite: 2019A&A...622A..48R). Prominent water maser features extending to hundreds of kilometers per second from the cloud velocity have been reported within W49N (cite: 1992ApJ...393..149G; 2004ApJS..155..577M).

Also, five 6.7 GHz methanol masers were reported the catalog of (cite: 2015MNRAS.450.4109B). Finally, (cite: 2001ApJ...550L..81W) reported the detection of 6 HMCs in W49N using CH$_{3}$CN observations at subarcsecond resolution, and (cite: 2022Miyawaki) studied the HMC W49N MCN-a (UCHII region J1 in (cite: 1997ApJ...482..307D)).

The star forming core population and star formation sequence in W49A have however not been explored in detail so far. In this work, we present a subarcsecond resolution study of W49A aimed at identifying and characterizing its core populations, as well as the evolutionary sequence from young star forming cores to UCHII regions. The ALMA and VLA observations we used are presented in [2](#s:obs). The analysis of the continuum maps and molecular lines presented in [3](#s:analy) is used in [4](#s:charac) to characterize the dust cores and establish a temporal classification based on their association with hot molecular cores and UC HII regions. A discussion is proposed in [5](#s:discu) and [6](#s:conclu) summarizes our main conclusion.

# Observations

## ALMA data

Observations of W49A at 1.3 mm (Band 6) were carried out with ALMA in Cycle 5 (project 2016.1.00620.S, PIs: Ginsburg, Galván-Madrid) between 2017 and 2018. The data consist in a mosaic of 28 fields with a primary beam of 25.6$\ensuremath{''}$, for a total mapping extent of about $2.5\ensuremath{'} \times 1.6\ensuremath{'}$ ($8.2 \times 5.3$ pc). The maximum recoverable scale of the 12-m array configuration used in this work is about 11$\ensuremath{''}$.

Continuum data were processed with `CASA` version 5.4 (cite: 2022CASA) using the imaging and self-calibration pipeline developed by the ALMA-IMF consortium (described in detail in (cite: Ginsburg22)). The continuum map has been produced using a selection of line-free channels (equivalent to the `cleanest` maps in (cite: Ginsburg22)) from the four spectral windows (hereafter Spws) of the dataset, summing up to a bandwidth of 1.23 GHz. We performed three iterations of cleaning and phase self-calibration and one iteration of amplitude self-calibration, using model masks of increasing size and decreasing cleaning thresholds We used the Multi-term (Multi Scale) Multi-Frequency Synthesis deconvolver of `tclean` with two Taylor terms, a robust parameter of 0, and scales up to nine times larger than the synthesized beam.

The final beam of the 1.3 mm continuum image has a FWHM size of $0.29\ensuremath{''} \times 0.24\ensuremath{''}$ ($\approx 2900$ au at 11.1 kpc). The rms noise measured in regions far away from the brightest emission, where the map is not limited by dynamic range, is of 0.38 mJy beam$^{-1}$ (see [\[tab:data\]](#tab:data)).

For the line data, the four spectral windows were processed with `IMAGER`[^1], implemented within the `GILDAS` software[^2]. Cleaning was performed using Clark deconvolution and 0.1 robust weighting. The cubes across the four bands have a spatial resolution of approximately 0.24$\ensuremath{''}$ (2750 au), a channel width of 0.65 km s$^{-1}$, and an rms noise of 1.6 mJy beam$^{-1}$ (0.6 K) per channel. The detailed parameters for each spectral window are given in [\[tab:data\]](#tab:data). We have used the method presented in (cite: 2019Molet) and (cite: 2022Brouillet) to separate the continuum and spectral line emission in each pixel of the image plane. The Spw 2 band covers the H30$\alpha$ line at 231.9 GHz. We also used the Spw 0 and Spw 3 bands to analyze CH$_3$OCHO lines.

## VLA data

We used the VLA A-array continuum image at 3.3 cm (X Band) presented in (cite: 2020AJ....160..234D). This image was created with the purpose of only studying W49N. Its field of view is outlined in Fig. [1](#fig:contB6). We smoothed this image from its original angular resolution (0.16$\ensuremath{''}$) to the resolution of the B6 ALMA continuum image (0.26$\ensuremath{''}$), then corrected it for its primary-beam response and regridded it to the ALMA image frame.

Juárez-Gama et al. (in prep.) used this image to provide a dendrogram catalog of H/UC HII regions and their physical properties in W49N. Their catalog of 79 H/UC HIIs is consistent with, and more complete, than previous visual identifications of H/UC HIIs in this protocluster (cite: 2005ApJ...624L.101D; 2020AJ....160..234D). We used the cm continuum catalog of Juárez-Gama et al. to complement the identification of dust cores and HMCs reported in this paper, as well as the HII emission traced by H$30\alpha$ also presented in this paper.

+:-----------------:+:------:+:---------------:+:---------:+:---------------------:+:--------------------------------------------:+:---------------:+:-------------------:+:-:+
| Image             | Instr. | $\nu_{\rm obs}$ | Bandwidth | pixel                 | Resolution                                                     | $1\sigma$ rms       |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
|                   |        | \[GHz\]         | \[MHz\]   | \[$\ensuremath{''}$\] | \[$\ensuremath{''} \times \ensuremath{''}$\] | \[km s$^{-1}$\] | \[mJy beam$^{-1}$\] |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
| X band cont.      | VLA    | 9.107           | 688       | 0.06                  | $0.29 \times 0.24$                           | \-              | 0.22                |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
| Band 6 cont.      | ALMA   | 227.950         | 1230      | 0.06                  | $0.29 \times 0.24$                           | \-              | 0.38                |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
| Spw 0             | ALMA   | 217.900         | 1875      | 0.07                  | $0.28 \times 0.23$                           | 0.67            | 1.47                |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
| Spw 1             | ALMA   | 219.860         | 1875      | 0.07                  | $0.28 \times 0.25$                           | 0.67            | 1.67                |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
| Spw 2/H30$\alpha$ | ALMA   | 231.870         | 1875      | 0.07                  | $0.27 \times 0.20$                           | 0.63            | 1.57                |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+
| Spw 3             | ALMA   | 233.740         | 1875      | 0.07                  | $0.27 \times 0.20$                           | 0.63            | 1.57                |   |
+-------------------+--------+-----------------+-----------+-----------------------+----------------------------------------------+-----------------+---------------------+---+

Central frequency of the continuum images or of the spectral windows. The central frequency of the ALMA continuum image is computed as the intensity-weighted average frequency, with a spectral index of 3 (see Eq. 1 in (cite: Ginsburg22)).

Bandwidth used to create the continuum images or bandwidth of the cubes.

Beam FWHM and channel width. The data cubes have been produced using the default Hanning smoothing function without channel averaging (N=1), resulting in a spectral resolution of two channels.

1 mJy beam$^{-1}$ corresponds to 0.34 K at 230 GHz and to 222 K at 9 GHz for the continuum maps.

# Analysis of the continuum maps and molecular lines

![](W49-B6map_article_v2.pdf)

![image](W49-B6map_article-zoom_ctr.pdf) ![image](W49-RLmap_article-zoom_ctr.pdf)

\

\

## Core catalog

We used the `getsf` algorithm (cite: 2021Mensh) to extract sources from the 1.3 mm continuum images. `getsf` decomposes the image into various spatial scales and separates compact sources from their background and filamentary structures. It is therefore well suited to find cores in complex environments such as high-mass star-forming regions. `getsf` has been extensively used in ALMA studies of protocluster regions (cite: 2022Pouteau; 2023Nony). We found 129 cores passing the post-selection filters for robust detection and measurements recommended by (cite: 2021Mensh): signal-to-noise for the background-subtracted peak larger than two, source size smaller than four times the FWHM beamsize, and ellipticity smaller than two. Table [2](#tab:cores-par) lists the retrieved parameters of the identified cores: position, major and minor axis FWHM, and position angle.

We also used `getsf` to measure the peak intensity and integrated flux of the cores in the ALMA B6 ($S^{\rm peak}_{\rm B6}$, $S^{\rm int}_{\rm B6}$) and VLA X-band ($S^{\rm peak}_{\rm BX}$, $S^{\rm int}_{\rm BX}$) maps. Cores are marked in the B6 continuum map in [1](#fig:contB6) and in zoom-in [\[fig:zomm-center,fig:zomm-swout\]](#fig:zomm-center,fig:zomm-swout).

Complementary, we measured directly in the continuum maps the maximum intensity of cores in both B6 and X band, $F^{\rm max}$[^3], and computed the integrated flux from the sum of the pixel intensities ($I$) within the core FWHM: $F^{\rm int}=c\,\Sigma I\,A_{\rm pix}/A_{\rm beam}$; with $A_{\rm pix}$ the pixel area and $A_{\rm beam}=\pi\,\theta_{min}\theta_{maj}/(4\mathrm{ln(2)})$ the beam area. We set the constant c=1/ln(2) to account for the core extension beyond its FWHM. We used this second set of parameters for the calculations presented in [4.2](#su:ff_B6), in which we compare a continuum map dominated by thermal dust emission (ALMA B6 at 230 GHz) with one dominated by free-free emission (VLA X-band at 9 GHz).

## Recombination line and free-free emission

We identified cores associated with H/UC HII regions using two tracers of ionized gas, the H30$\alpha$ recombination line and the free-free emission measured using the X-band map.

### Detection of the H30$\alpha$ line

We identified cores associated with H30$\alpha$ emission using two complementary methods. Our first method is as follows: for all the cores we inspected the spectrum at the frequency of the H30$\alpha$ line and performed Gaussian fitting to measure the line systemic velocity, the FWHM line width $\Delta V$, and the peak brightness temperature $T_\mathrm{B}$. We then separated cores with brightness temperature $T_\mathrm{B} > 2$ K (38 cores) from cores with $T_\mathrm{B}$ between 0.8 and 2 K (14 cores). There are $^{33}$SO$_2$ (12$_{3,9}$ – 12$_{2,10}$) lines very close in frequency (231.9004 GHz, 231.9015 GHz) to the H30$\alpha$ line at 231.9009 GHz, as well as CH$_3$C$^{15}$N and CH$_3$OCHO lines within 3 MHz. Therefore, disentangling the H30$\alpha$ emission can be challenging. Since the H30$\alpha$ line is expected to be much broader (cite: 2007prpl.conf..181H), we further applied a threshold for the linewidth of $\Delta V>20~\ensuremath{\rm km\,s^{-1}}$ to filter out cores dominated by contamination from molecular lines. This gave us 29 remaining cores with strong H30$\alpha$ detection ($T_\mathrm{B} > 2$ K) and 9 with a weak detection.

Our second method relies on moment 0 maps of the H30$\alpha$ line, which we constructed by integrating in velocity from $-50~\ensuremath{\rm km\,s^{-1}}$ to $+50~\ensuremath{\rm km\,s^{-1}}$ (the line systemic velocity ranges from about 0 to 20 $\ensuremath{\rm km\,s^{-1}}$ LSR). We considered a positive detection when the core’s FWHM ellipse includes a group of pixels above a given threshold. Considering the large dynamic range of the line emission in the map, we noticed that the noise strongly decreases from the center to the edges of the mosaic. In consequence, we defined two reference thresholds, 5$\sigma_{\rm ctr}=0.4$ Jy beam$^{-1}$$\ensuremath{\rm km\,s^{-1}}$ in the center, 5$\sigma_{\rm sw}=0.1$ Jy beam$^{-1}$$\ensuremath{\rm km\,s^{-1}}$ in the South West (SW) region, and we constructed a clipped moment 0 map where pixels below $5\sigma$ are set to zeros.

All the 29 cores with a strong H30$\alpha$ line detection are also detected in the moment 0 maps and qualify as robust H30$\alpha$ detections. On the other hand, the nine cores with weak H30$\alpha$ line detection using the first method have a few isolated pixels above their respective threshold at most, and are considered as tentative H30$\alpha$ detections.

Cores with a robust or tentative H30$\alpha$ detection are overlaid on the moment 0 maps in the bottom panels of [\[fig:zomm-center,fig:zomm-swout\]](#fig:zomm-center,fig:zomm-swout).

### Detection of free-free centimeter emission

We defined the criterion for a robust detection and measurement in X band as $S^{\rm peak}_{\rm BX} > 3\sigma_{\rm BX}$ and $F^{\rm max}_{\rm BX} > 3\sigma_{\rm BX}$, where $\sigma_{\rm BX}=0.22$ mJy beam$^{-1}$ is the noise in the X band maps convolved to the B6 angular resolution, measured using the median absolute deviation. This criterion combines the background subtracted peak intensity $S^{\rm peak}$ determined by *getsf* and the maximum intensity measured in the original continuum map (see [3.1](#su:catalog)).

Out of the 109 cores lying in the field of view of the X band map, 27 have a robust detection at 3.3 cm. Table [2](#tab:cores-par) lists the integrated core fluxes in X band ($F^{\rm int}_{\rm BX}$) and Band 6 ($F^{\rm int}_{\rm B6}$).

## Identification of hot molecular cores

We used methyl formate (CH$_3$OCHO) as a signature of hot molecular core emission, following the method described in (cite: 2022Brouillet) where it was found that the use of methyl formate to identify the main HMCs in the W43-MM1 region provides similar results compared to the use of a broad frequency band with various other lines of complex organic molecules (see their Fig. 5). This study showed that this molecule offers a good compromise between widespread detectability and reliability in tracing HMC. Methyl formate has also been used to identity HMC candidates in the recent survey of (cite: 2024Bonfand). We have based the identification on the CH$_3$OCHO (17$_{3,14}$ – 16$_{3,13}$) doublet at 218.281 and 218.298 GHz, with an upper-level energy $E_{\rm u}$ of 99.7 K. We have further verified our detections with a synthetic spectrum fitting the numerous methyl formate lines in Spw 3. We found 19 dust cores with HMC emission within the entire ALMA mosaic, that is 17 within the field of view of the X band map and 2 in the south-western region. They are indicated with an asterisk in [2](#tab:cores-par).

# Characterization of dust cores

From the measurements presented in [3](#s:analy), we identify cores associated with H/UC HII regions in [4.1](#su:HII) and measure their properties in [4.2](#su:ff_B6). The inclusion of HMCs enables us to refine the evolutionary status of cores in [4.3](#su:evol).

## Classification of cores with H/UC HII regions

### With VLA measurements

For 109 cores within the field of view of the X band image, we have information on both the X band and the H30$\alpha$ detection. The 27 cores with a robust detection in X band are likely associated with an H/UC HII region. 20 are also detected in H30$\alpha$ and three have a tentative H30$\alpha$ detection (#74, #87, #116). The remaining four cores without detection in H30$\alpha$ (#8, #18, #104, #117) only have a weak X band detection, with $S^{\rm peak}_{\rm BX}$ and $F^{\rm max}_{\rm BX}$ between 3 and 10$\sigma_{\rm BX}$, which suggests that our sensitivity to detect ionized gas is higher in the X band map than with the recombination line. Two other cores have a tentative H30$\alpha$ detection and no detection in X band: after visual inspection core #94 is considered as an H/UC HII region candidate and core #82 is rejected.

Our identification of dust cores associated with H/UC HII regions largely overlaps with the independent dendrogram catalog of H/UC HII regions of Juárez-Gama et al. (in prep.) (see [2.2](#su:VLAdat)). 21 H/UC HII dendrogram structures out of 79 within the X band map are associated with a core with H/UC HII region, as previously defined. In detail, 20 HII dendrogram structures are associated with 26 cores with a robust detection in X band[^4]

Only one HII dendrogram structure is associated with a dust core (#27) not detected in X band. Conversely, only one dust core with a detection in X band is not associated with a dendrogram structure. This core (#18) is among the weakest X band detections ($S^{\rm peak}_{\rm BX} = 4\sigma_{\rm BX}$ and $F^{\rm max}_{\rm BX} = 3.4\sigma_{\rm BX}$) and is not found in H30$\alpha$. Fifity seven structures in the dendrogram catalog built from the X band map do not have any counterpart in the Band 6 core catalog and qualify as H/UC HII regions without association to dust cores. A summary of the relation between the 28 dust cores associated with H/UC HII regions (27 when excluding the H/UC HII region candidate) and the dendrogram-identified H/UC HII regions is shown in [4](#fig:statbox).

### Without VLA measurements

For the 20 dust cores outside the field of view of the X band image, the recombination line is the only tool to search for emission from H/UC HII regions. Nine cores associated with a robust H30$\alpha$ detection (four in the southwestern region, five in the eastern outskirts, see [4](#fig:statbox)) are likely associated with an H/UC HII region. After visual inspection, three additional cores with a tentative H30$\alpha$ detection located in the SW region (#50, #131, #147) are considered as H/UC HII region candidates, and another core located in the eastern outskirts (#115) is rejected.

## Free-free emission in ALMA Band 6

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| n | $F^{\rm int}_\mathrm{ff,cm}$  | $F^{\rm int}_\mathrm{ff,RL}$  | $P_\mathrm{ff}$ | $\alpha$ | EM |
|  | \[mJy.b$^{-1}$\] | \[mJy.b$^{-1}$\] | \[%\] |  | \[pc cm$^{-6}$\] |
| 1 | 26.3 | 809.1 | \>78 | \>0.96 | \>2.9e8 |
| 2 | 27.6 | 422.5 | \>58 | \>0.74 | \>2.9e8 |
| 3 | 40.3 | 224.2 | \>61 | \>0.43 | \>2.9e8 |
| 4 | \- | 90.4 | 96 | \- | \- |
| 5 | \- | 71.5 | 54 | \- | \- |
| 7 | 29.2 | 115.3 | \>61 | \>0.32 | \>2.9e8 |
| 8 | 1.1 | \- | \- | \- | 1.1e7 |
| 9 | \- | 55.8 | 65 | \- | \- |
| 10 | 8.8 | 179.6 | 54 | 0.83 | 1.8e8 |
| 11 | 15.8 | 24.6 | 44 | 0.04 | 1.4e8 |
| 12 | \- | 65.3 | 56 | \- | \- |
| 13 | 9.2 | 94.8 | 64 | 0.62 | 1.1e8 |
| 14 | 97.1 | 137.1 | \>67 | \>0.00 | \>2.9e8 |
| 15 | 43.2 | 39.5 | 67 | -0.13 | 1.9e8 |
| 16 | 49.6 | 176.5 | 63 | 0.29 | 2.9e8 |
| 17 | 12.7 | 80.5 | 64 | 0.47 | 1.7e8 |
| 18 | 0.7 | \- | \- | \- | 4.5e6 |
| 23 | 9.1 | 11.0 | 62 | -0.04 | 8.3e7 |
| 29 | 12.4 | 17.6 | 75 | 0.01 | 9.5e7 |
| 39 | \- | 17.9 | 59 | \- | \- |
| 40 | 39.4 | 40.5 | 51 | -0.09 | 1.5e8 |
| 44 | 1.0 | 8.1 | 37 | 0.53 | 8.7e6 |
| 46 | 24.9 | 35.3 | 61 | 0.00 | 3.1e8 |
| 47 | 14.6 | 23.7 | 54 | 0.05 | 1.6e8 |
| 50 | \- | 9.1 | 25 | \- | \- |
| 59 | \- | 11.2 | 49 | \- | \- |
| 69 | 12.4 | 13.6 | 64 | -0.07 | 4.2e7 |
| 72 | 22.4 | 19.1 | 45 | -0.15 | 1.1e8 |
| 73 | 21.6 | 25.0 | 55 | -0.06 | 1.7e8 |
| 74 | 2.6 | 2.9 | 33 | -0.07 | 1.4e7 |
| 78 | \- | 8.1 | 37 | \- | \- |
| 87 | 10.0 | 13.7 | 42 | -0.01 | 1.3e7 |
| 94 | \- | 13.8 | 54 | \- | \- |
| 104 | 0.5 | \- | \- | \- | 9.1e6 |
| 107 | \- | 7.1 | 48 | \- | \- |
| 112 | \- | 16.7 | 65 | \- | \- |
| 116 | 2.4 | 3.6 | 73 | 0.02 | 9.9e6 |
| 117 | 1.7 | \- | \- | \- | 1.3e7 |
| 131 | \- | 1.3 | 40 | \- | \- |
| 147 | \- | 4.4 | 22 | \- | \- |

: Derived parameters of dust cores associated with H/UC HII regions: core identifier, integrated free-free flux at 1.3 mm estimated from the 3.3 cm map and from the H30$\alpha$ line, percentage of free-free emission in Band 6, spectral index of free-free emission, and emission measure.

Out of the 129 dust cores detected with ALMA over the entire mosaic, we found 36 cores associated with H/UC HII regions (27 with VLA measurements, 32 with H30$\alpha$ measurements, see [4.1](#su:HII)) and 4 cores tentatively associated with H/UC HII regions (#50, #94, #131, #147), which have only tentative H30$\alpha$ detections.

A first evaluation of their free-free emission at 1.3 mm is obtained from the integrated fluxes, $F^{\rm int}_{\rm BX}$ measured in the X band map over FWHM of the cores (see [3.1](#su:catalog)): $$\begin{equation}
F^{\rm int}_\mathrm{ff,cm} = F^{\rm int}_\mathrm{BX}\,\left(\frac{\nu_\mathrm{B6}}{\nu_\mathrm{BX}} \right) ^{\alpha},  
\end{equation}$$

where $\nu_\mathrm{B6}=227.95$ GHz and $\nu_\mathrm{BX}=9.11$ GHz are the reference frequency of the ALMA B6 and VLA X band images, respectively (see [\[tab:data\]](#tab:data)). We took a spectral index $\alpha=-0.1$, assuming that the free-free emission is optically thin all the way from 3 cm to 1 mm. The fluxes calculated in this way are thus lower limits to the free-free emission in the ALMA image.

We also constructed a pixel by pixel free-free map $I_\mathrm{ff,RL}$ using the moment 0 of the H30$\alpha$ recombination line (cite: Wilson09; 2019ApJ...871..185L): $$\begin{equation}
    \centering
    I_\mathrm{ff,RL} = 1.432 \times 10^{-4} \bigl( \nu_0^{-1.1} T_\mathrm{e}^{1.15} \bigr ) \bigl( 1+N_\mathrm{He}/N_\mathrm{H} \bigr ) \int I_{{\rm H}30} dv, 
\label{eq:ff_map}
\end{equation}$$ where the electron temperature is $T_\mathrm{e} = 7000$ K (e.g. (cite: 2023MNRAS.520.3245Z)), the helium to hydrogen number ratio is $N_\mathrm{He}/N_\mathrm{H} = 0.08$, and $\nu_0$ is the central frequency of the H$30\alpha$ line. We then obtained a second evaluation of the free-free emission in B6 by measuring on the $I_\mathrm{ff,RL}$ map the integrated fluxes of the cores, $F^{\rm int}_\mathrm{ff,RL}$, using the method presented in [3.1](#su:catalog).

From the previous measurements, we derived various parameters for the cores associated with H/UC HII regions. We defined their percentage of free-free emission in B6 as $P_\mathrm{ff}=\,F_\mathrm{ff,RL}/F_\mathrm{B6}$. $P_\mathrm{ff}$ ranges from 22 to 96%. The dust flux in B6 is expressed as $F_\mathrm{B6, dust} = F_\mathrm{B6} - F_\mathrm{ff}$, with $F_\mathrm{ff}=F_\mathrm{ff,RL}$ when the H30$\alpha$ is detected, and $F_\mathrm{ff}=F_\mathrm{ff,cm}$ otherwise. By construction, $F_\mathrm{ff,RL}$ can be expressed as a function of $F_\mathrm{B6, dust}$ and $P_\mathrm{ff}$: $F_\mathrm{ff,RL} = F_\mathrm{B6, dust}\,P_\mathrm{ff}/(1-P_\mathrm{ff})$. We also computed the spectral index of free-free emission from $\nu_\mathrm{BX}$ to $\nu_\mathrm{B6}$: $$\begin{equation}
\alpha_\mathrm{ff} = \frac{\mathrm{log}(F_\mathrm{ff,RL}/F_\mathrm{BX})}{\mathrm{log}(\nu_\mathrm{B6}/\nu_\mathrm{BX})}
\end{equation}$$

Finally, we computed the emission measure, EM, of H/UC HII emission within dust cores:

$$\begin{equation}
 \label{eq:EM}
\mathrm{EM}~[\mathrm{pc\,cm}^{-6}] = \int n_e^2 dl = 12\,\tau_\mathrm{ff} \Bigl[ \frac{\nu_\mathrm{BX}}{\mathrm{GHz}} \Bigr ]^{2.1}
\Bigl [ \frac{T_\mathrm{e}}{\mathrm{K}} \Bigl ]^{1.35},
\end{equation}$$

with $n_\mathrm{e}$ the electron density and $\tau_\mathrm{ff}$ the free-free continuum optical depth, expressed as $$\begin{equation}
 \label{eq:tauff}
\tau_\mathrm{ff} = - \ln \biggl [ \biggl ( 1 - \frac{T_\mathrm{B}}{T_\mathrm{e}} \biggr ) \biggr ],
\end{equation}$$

The brightness temperature $T_\mathrm{B}$ is calculated from the maximum intensity in X band within the cores FWHM, $F^{\rm max}_{\rm BX}$, and we used a constant electron temperature $T_\mathrm{e} = 7000$ K. Two cores with $T_\mathrm{B} > 7000$ K (#3 and #16) and 4 cores with $6700 < T_\mathrm{B} < 7000$ K (#1, #2, #7 and #14) are likely to have higher electron temperature, considering the condition $T_\mathrm{e} > T_\mathrm{B}$ set by [\[eq:tauff\]](#eq:tauff). We computed for these six cores a lower limit of the emission measure using an opacity $\tau_\mathrm{ff}=1.5$ in line with the rest of the core sample. The emission measures of cores with H/UC HII regions range from 4.5$\,\times\,10^6$ to 3.1$\,\times\,10^8$ pc cm$^{-6}$, which are in the range of values found for ultra-compact HII regions (cite: 2002ARA&A..40...27C; 2007prpl.conf..181H). Table [1](#tab:HII-par) lists $F_\mathrm{ff,cm}$, $F_\mathrm{ff,RL}$, $P_\mathrm{ff}$, $\alpha_\mathrm{ff}$, and EM for the 40 cores with robust and candidate H/UC HII emission.

## Core classification

In what follows, we combine the statistics obtained from the detection rates of H/UC HII regions (see [4.1](#su:HII)) with the hot molecular core (HMC) detections (see [3.3](#su:hotcore)) to build a classification of the dust cores into four types: $a/$ cores without either HMC or H/UC HII region, $b/$ cores associated with a HMC but without H/UC HII emission, $c/$ cores associated with both a HMC and H/UC HII emission, and $d/$ cores associated with a H/UC HII region but without HMC emission. Within the full ALMA B6 mosaic, the number counts of each type are $a/$: 77 (81), $b/$: 12, $c/$: 7, and $d/$: 33 (29). Numbers in parenthesis correspond to the situation where all the cores with H/UC HII regions candidates are accounted in first type. Within the smaller field of view of the VLA X band map, the statistics are 69 (70), 12, 5 and 23 (22). [4](#fig:statbox) shows a diagram summarizing the detection statistics. In addition, 57 (58) H/UC HII regions without cores have been detected by Juárez-Gama et al. (in prep.).

![](W49-statbox_v3.png)

![](W49-timesequence_v3.png)

# Discussion

## Evolution of Star Forming Cores in W49A

From the empirical classification presented in [4.3](#su:evol), in this section we propose an evolutionary sequence for the dust cores in W49A, based on the presence or absence of the analyzed indicators of high-mass star formation. [5](#fig:timeseq) summarizes the proposed evolutionary scheme.

Cores in stage $a/$ do not have evidence of a HMC or H/UC HII region, they are likely prestellar or low-mass protostellar cores. Among cores in stage $a/$, which we label "young cores", only a fraction are the precursors of high-mass stars. It is indeed expected that some of them will produce low-mass objects.

From stage $b/$ onward, all cores are expected to harbor a high-mass ($\gtrsim 8~\ensuremath{M_{\odot}}$) protostar. As it grows in mass, the protostellar object will first reach the luminosity necessary to heat its envelope to a temperature where complex organic molecules are released from dust grains. This defines the onset of the hot molecular core stage ($b/$, "young HMC" in [5](#fig:timeseq)). Later on, when the extreme ultraviolet (EUV) radiation of the star is sufficient to ionize atomic hydrogen, an HII region is born. During the short phase in which the HMC and the H/UC HII region coexist (stage $c/$, "evolved HMC"), we expect that the remaining dust and molecules form a cocoon around the HII region, which is mostly free of dust (cite: 2008ASPC..387..232L). The radiation then becomes strong enough to fully destroy molecules, and only some dust remains surrounding the H/UC HII region (stage $d/$, "intermediate UCHII"). Finally, the UCHII fully clears its way out of the now extinct core, which is not detected anymore in dust emission (stage $e/$, "evolved UCHII"). We expect that high-mass protostars keep accreting from their envelopes from stages $b/$ to $d/$, which therefore represent the phases of high-mass protostellar evolution. Under this definition, 40 (39) cores out of 109 in W49N are high-mass protostellar cores. For W49SW and what we label as outskirts, 12 (9) cores out of 20 contain high-mass protostars (see [4](#fig:statbox)).

Regarding their spatial distribution, the large majority of the cores detected at 1.3 mm (109 out of 129) lie within the central star forming region W49N. Only a few cores are located at distances beyond a parsec from the central hub (see [1](#fig:contB6)). In W49N, HMCs and the well known HII regions (cite: 1997ApJ...482..307D; 2018ApJ...863L...9D) co-exist with a population of young cores (see zoom-in [2](#fig:zomm-center)). This indicates that the central protocluster is still actively forming stars in spite of the significant stellar feedback, as suggested by (cite: 2013ApJ...779..121G) from the measurement of a $\sim 2\times10^5~\ensuremath{M_{\odot}}$ molecular gas reservoir in W49N. A similar scenario has been proposed for the also very active W51-E and W51-IRS2 protoclusters (cite: 2016A&A...595A..27G).

Using uncertainties from the binomial distribution, we measured the 75% confidence interval for the percentage of cores containing high-mass protostars (stages $b/$ to $d/$) to be \[30-42\]% in W49N and \[30-75\]% in W49SW and the W49 outskirts. Therefore, the relative abundance of high-mass protostars does not appear to be statistically different between the center of W49A and its periphery. We reach the same conclusion when only HMCs or cores with H/UC HII regions are considered. This suggests that the different sub-protoclusters analyzed in this paper have a similar "age", in the sense that their core and protostellar populations look statistically similar. The small number of objects in W49SW and the W49 outskirts forbids us to make a stronger statement, but this further suggests that star formation across the W49A cloud started simultaneously, possibly by cloud-cloud collision as suggested by (cite: 2022PASJ...74..128M).

## Ionization evolution within dust cores

![image](histo-Fxt_dust.png) ![image](RLff-thermB6_err.png)

![](Pff-specind_err.png)

The physical parameters derived in [4.2](#su:ff_B6) allow us to evaluate the evolution of the protostar and envelope masses. The left panel of [6](#fig:compar-plots1) shows that cores with a HMC and/or H/UC HII region have statistically higher dust flux than the others. The median dust flux of the two distributions are $2.2 \times 10^{-2}$ Jy and $6.9 \times 10^{-3}$ Jy, respectively. We have verified with a KS test that the distributions are statistically distinct ($p$-value of $4 \times 10^{-7}$). Since the dust flux is related to the molecular gas mass of the core, this difference suggests that the more evolved cores could also be more massive.

Complementary, the right panel of [6](#fig:compar-plots1) shows a strong correlation between the dust flux at 1.3 mm and the amount of free-free emission. Both the Pearson and Spearman correlation coefficients are higher than 0.8, with $p$-values $\simeq 10^{-10}$. Since the amount of free-free emission is related to the mass of the central star through the number of ionizing photons (cite: 1994ApJS...91..659K), this correlation could indicate that the mass of the central (proto)star grows simultaneously with the mass of its gas envelope. This hypothesis is in line with models of continuous accretion across multiple scales (cite: 2009MNRAS.400.1775S; 2019MNRAS.490.3061V), as well as with recent observations suggesting that cores grow in mass as they evolve from quiescent (candidate prestellar) to active protostellar stages (cite: 2023Nony).

However, the dust flux is also dependent on the dust temperature, which might be higher in the more evolved cores than in the younger ones. This could partially explain the difference between the distributions in the left panel of [6](#fig:compar-plots1). For an envelope internally heated by an embedded protostar, the dust temperature depends on its luminosity (cite: 1976ApJ...206..718S), hence on the protostellar mass. Therefore, the correlation found in the right panel of [6](#fig:compar-plots1) between the dust and free-free fluxes could alternatively be explained by the dependence on the stellar mass of both quantities. Detailed measurements of core temperatures, which are beyond the scope of this work, are thus needed to draw firmer conclusions.

In [7](#fig:compar-plots2) we compare the percentage of free-free emission in the 1.3 mm flux ($P_\mathrm{ff}$) to the free-free spectral index ($\alpha_\mathrm{ff}$) between 3.3 cm and 1.3 mm, for the sample of dust cores with an estimation of their free-free content from both a centimeter continuum and H$30\alpha$ detection (see [4.2](#su:ff_B6)). A first group of dust cores with optically thin free-free emission ($\alpha_\mathrm{ff} \simeq-0.1$ to 0) has $P_\mathrm{ff}$ spanning a large range of values, from 30 to 80%. In contrast, a second group of cores with partially optically thick free-free emission ($\alpha_\mathrm{ff} \sim$ 0.3 to 1) tends to show a more restricted $P_\mathrm{ff} \simeq 55-65\%$, with a couple of exceptions. To first order, HII regions are expected to smoothly evolve as they ionize and break out of their parental core (cite: 2007ApJ...666..976K; 2016ApJ...818...52T). During this process, they are expected to transition from denser objects with partially optically thick emission, to being less dense and optically thin (cite: 2008ApJ...672..423K; 2009ApJ...706.1036G). HMCs represent an early stage within this sequence (see [5.1](#su:sf)), therefore the fact that the three HMCs within the sample of dust cores with HII emission have partially optically thick free-free emission is consistent with this scenario. Under this simple interpretation, however, the points in [7](#fig:compar-plots2) should follow an anti-correlation, or at least the – more evolved – optically thin HII regions should have on average a larger $P_\mathrm{ff}$ than the – younger – optically thicker ones. This is not observed. Previous work on hydrodynamical simulations with ionization feedback and synthetic observations has shown that the stochastic interactions of the neutral gas and ionizing photons can cause variations in the appearance of the youngest HII regions (cite: 2010ApJ...711.1017P), including their spectral indices (cite: 2010ApJ...719..831P). This means that, even if H/UC HIIs eventually break free from their cores on timescales of $\sim 10^5$ yr, their early evolution is not necessarily monotonic. We propose that this could be the cause of the observed spread of values in [7](#fig:compar-plots2).

## Lifetimes

We now proceed to evaluate the core lifetimes using the evolutionary sequence presented in [5.1](#su:sf) and shown in [5](#fig:timeseq). For this purpose, we consider the population of 109 cores in W49N, for which the more complete search of H/UC HII regions has been made. Summing up 28 cores with H/UC HII regions and 57 H/UC HII regions not associated to a dust core, 85 objects fall in the H/UC HII regions category. Under the hypothesis of constant star-formation and assuming that HMCs are precursors of H/UC HII regions, the relative number of HMCs to H/UC HII regions (17/85) provides an estimation of their statistical lifetime. Using the typical lifetime for H/UC HII regions of $3\times10^5$ yr, calculated from Galaxy-wide surveys (cite: 2002ARA&A..40...27C; 2011ApJ...730L..33M), we estimate the lifetime of the HMC phase to be $\tau_\mathrm{HMC} \simeq (17/85) \cdot (3 \times 10^5) = 6\times10^4$ yr. The ratio of 17 HMCs to 85 H/UC HII we find in W49, and thus the inferred lifetime, are smaller than previous estimations in the same region (6/12, (cite: 2001ApJ...550L..81W)) and in Sgr B2 (5/8, (cite: 2017A&A...604A..60B)). It is similar to that found in another high-mass star-forming region (1/9, (cite: 2005ApJ...624..827F)).

The period during which HMCs and H/UC HII regions coexist in W49A (5 cores out of 17) appears to be very short, $\simeq 2\times10^4$ yr (cite: 2021MNRAS.505.2801L). Therefore, our results point toward a rapid dispersal of the warm, inner molecular envelope once the HII region appears.

We also use the relative number of high-mass protostellar cores to H/UC HII regions (40/85, see [5.1](#su:sf)) to estimate the lifetime of the massive protostellar phase, $\tau_\mathrm{proto} \simeq 40/85\,\times\,3\,10^5 \simeq 1.4\times10^5$ yr. Our estimation is about two times lower than the value reported in the review of (cite: 2018Motte), $\tau_\mathrm{proto} \sim 3\times10^5$ yr. It is also within the range of durations reported by (cite: 2011ApJ...730L..33M), $7\times10^4$ yr to $4\times10^5$ yr for massive YSOs with luminosities from $10^4$ to $10^5\ensuremath{L_{\odot}}$. Our estimation of the lifetime of the massive protostellar phase may be a lower limit if we are missing detections of HMCs or H/UC HII regions. For example, it has been reported that a large dust optical depth could hinder the detection of molecular lines in emission (cite: 2020ApJ...896L...3D). Conversely, our estimation of the number of high-mass protostars may be an upper limit if some of the HMCs are associated with intermediate mass protostars which will not evolve to high-mass stars, or if our 3000 au-cores subfragment into several intermediate and low-mass stars.

# Conclusions

We presented an analysis of the star-formation activity in W49 based on the first millimeter continuum survey in this region. Our main results and conclusions are as follows:

1.  We built a 1.3 mm continuum image at $0.29\ensuremath{''} \times 0.24\ensuremath{''}$ resolution from ALMA B6 observations and constructed a catalog of 129 cores, extracted using the *getsf* algorithm.

2.  We looked for cores associated with H/UC HII regions by analyzing the VLA X band map (3.3 cm, (cite: 2020AJ....160..234D)), dominated by free-free emission, and the H30$\alpha$ recombination line at 231.9 GHz, covered by our ALMA observations. We found a good agreement between these two tracers of ionized gas, with 23 common detections and only four cores with HII regions detected only in the X band map, out of 109 cores within the VLA field of view.

3.  We identified a total of 36 cores associated with H/UC HII regions over the entire ALMA mosaic, as well as four other cores tentatively associated with H/UC HII regions. We measured their integrated free-free flux and derived their dust flux at 1.3 mm.

4.  The spectral indexes from 3.3 cm to 1.3 mm range from 1, for the youngest cores with partially optically thick free-free emission, to about -0.1, that is optically thin free-free emission obtained for cores allegedly more evolved. The emission measures, which range from 4.5$\times10^6$ to 3.1$\times10^8$ pc cm$^{-6}$, are typical of H/UC HII regions.

5.  We also found, using the methyl formate doublet at 218.281 and 218.298 GHz within the spectral coverage of our ALMA B6 data, that 19 cores are associated with hot molecular core (HMC) emission. 17 HMCs are located within the central subregion, W49N, which is about three time the number of HMCs previously reported by (cite: 2001ApJ...550L..81W). This places W49 among the protoclusters with the best statistics for HMCs studies, along with W43 and W51(cite: 2022Brouillet; 2024Bonfand).

6.  We combined these two tracers of high-mass star formation (HMC and HII region emission) to propose a classification of the cores according to their evolutionary stage. Within W49N, covered by the VLA map, 69 cores without HMC or H/UC HII region are labeled as "young cores", meaning that they are either prestellar or lower-mass protostellar cores. The 5 cores with H/UC HII regions which are also associated with HMCs are assumed to be less evolved than the 23 cores with H/UC HII regions only. Finally we also considered a fifth category of H/UC HII regions not associated to dust cores.

7.  The statistical lifetimes of the hot molecular core and massive protostellar phases in W49 are estimated to be $6\times10^4$ yr and $1.4\times10^5$ yr, respectively, based on a duration of the H/UC HII phase of $3\times10^5$ yr. The identification of massive protostellar cores is based on the association between a dust core and a HMC and/or an H/UC HII region. These estimations could be upper limits taking into the possible subfragmentation of HMCs into less massive protostars.

8.  We found that HMCs and H/UC HII regions coexist in W49A during a short period of $\simeq 2\times10^4$ yr. This indicates a rapid dispersal of the inner molecule envelope once the HC HII is formed.

# Acknowledgements

We thank the referee R. Miyawaki for his helpful comments improving the manuscript. RGM and TN acknowledge support from UNAM-PAPIIT project IN108822 and from CONACyT Ciencia de Frontera project ID 86372. TN also acknowledges support from the postdoctoral fellowship program of the UNAM. Part of this work was performed using the high-performance computers at IRyA, Mexico, funded by CONACyT and UNAM. The work from the IT staff at this institute is acknowledged. AG acknowledges support from the NSF via grants AST 2008101 and CAREER 2142300. H.B.L. is supported by the National Science and Technology Council (NSTC) of Taiwan (Grant Nos. 111-2112-M-110-022-MY3). C R-Z acknowledges support from program UNAM-PAPIIT IG101723. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00620.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work is based on an analysis carried out with the GILDAS, IMAGER and CASSIS softwares, as well as the CDMS and JPL spectroscopic databases. CASSIS has been developed by IRAP-UPS/CNRS (http://cassis.irap.omp.eu).

56 natexlab

(ref: 2020MNRAS.497.1972) Barnes, A. T., Kauffmann, J., Bigiel, F., et al. 2020, MNRAS, 497, 1972

(ref: 2017A&A...604A..60B) Bonfand, M., Belloche, A., Menten, K. M., Garrod, R. T., & Müller, H. S. P. 2017, A&A, 604, A60

(ref: 2024Bonfand) Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, arXiv e-prints, arXiv:2402.15023

(ref: 2015MNRAS.450.4109B) Breen, S. L., Fuller, G. A., Caswell, J. L., et al. 2015, MNRAS, 450, 4109

(ref: 2022Brouillet) Brouillet, N., Despois, D., Molet, J., et al. 2022, A&A, 665, A140

(ref: 2022CASA) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: 2002ARA&A..40...27C) Churchwell, E. 2002, ARA&A, 40, 27

(ref: 2018ApJ...863L...9D) De Pree, C. G., Galván-Madrid, R., Goss, W. M., et al. 2018, ApJL, 863, L9

(ref: 1997ApJ...482..307D) De Pree, C. G., Mehringer, D. M., & Goss, W. M. 1997, ApJ, 482, 307

(ref: 2005ApJ...624L.101D) De Pree, C. G., Wilner, D. J., Deblasio, J., Mercer, A. J., & Davis, L. E. 2005, ApJL, 624, L101

(ref: 2020AJ....160..234D) De Pree, C. G., Wilner, D. J., Kristensen, L. E., et al. 2020, AJ, 160, 234

(ref: 2020ApJ...896L...3D) De Simone, M., Ceccarelli, C., Codella, C., et al. 2020, ApJL, 896, L3

(ref: 2005ApJ...624..827F) Furuya, R. S., Cesaroni, R., Takahashi, S., et al. 2005, ApJ, 624, 827

(ref: 2009ApJ...706.1036G) Galván-Madrid, R., Keto, E., Zhang, Q., et al. 2009, ApJ, 706, 1036

(ref: 2013ApJ...779..121G) Galván-Madrid, R., Liu, H. B., Zhang, Z. Y., et al. 2013, ApJ, 779, 121

(ref: Ginsburg22) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022, A&A, 662, A9

(ref: 2016A&A...595A..27G) Ginsburg, A., Goss, W. M., Goddi, C., et al. 2016, A&A, 595, A27

(ref: 1992ApJ...393..149G) Gwinn, C. R., Moran, J. M., & Reid, M. J. 1992, ApJ, 393, 149

(ref: 2009ARA&A..47..427H) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: 2007prpl.conf..181H) Hoare, M. G., Kurtz, S. E., Lizano, S., Keto, E., & Hofner, P. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 181

(ref: 2005A&A...430..481H) Homeier, N. L. & Alves, J. 2005, A&A, 430, 481

(ref: 2007ApJ...666..976K) Keto, E. 2007, ApJ, 666, 976

(ref: 2008ApJ...672..423K) Keto, E., Zhang, Q., & Kurtz, S. 2008, ApJ, 672, 423

(ref: Kurtz05) Kurtz, S. 2005, in Massive Star Birth: A Crossroads of Astrophysics, ed. R. Cesaroni, M. Felli, E. Churchwell, & M. Walmsley, Vol. 227, 111–119

(ref: 1994ApJS...91..659K) Kurtz, S., Churchwell, E., & Wood, D. O. S. 1994, ApJS, 91, 659

(ref: 2016ApJ...828...32L) Lin, Y., Liu, H. B., Li, D., et al. 2016, ApJ, 828, 32

(ref: 2019ApJ...871..185L) Liu, H. B., Chen, H.-R. V., Román-Zúñiga, C. G., et al. 2019, ApJ, 871, 185

(ref: 2021MNRAS.505.2801L) Liu, H.-L., Liu, T., Evans, Neal J., I., et al. 2021, MNRAS, 505, 2801

(ref: 2008ASPC..387..232L) Lizano, S. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 387, Massive Star Formation: Observations Confront Theory, ed. H. Beuther, H. Linz, & T. Henning, 232

(ref: 2004ApJS..155..577M) McGrath, E. J., Goss, W. M., & De Pree, C. G. 2004, ApJS, 155, 577

(ref: 2021Mensh) Men’shchikov, A. 2021, A&A, 649, A89

(ref: 2009PASJ...61...39M) Miyawaki, R., Hayashi, M., & Hasegawa, T. 2009, PASJ, 61, 39

(ref: 2022PASJ...74..128M) Miyawaki, R., Hayashi, M., & Hasegawa, T. 2022a, PASJ, 74, 128

(ref: 2022Miyawaki) Miyawaki, R., Hayashi, M., & Hasegawa, T. 2022b, PASJ, 74, 705

(ref: 2019Molet) Molet, J., Brouillet, N., Nony, T., et al. 2019, A&A, 626, A132

(ref: 2018Motte) Motte, F., Bontemps, S., & Louvet, F. 2018, ARA&A, 56, 41

(ref: 2011ApJ...730L..33M) Mottram, J. C., Hoare, M. G., Davies, B., et al. 2011, ApJL, 730, L33

(ref: 2023Nony) Nony, T., Galván-Madrid, R., Motte, F., et al. 2023, A&A, 674, A75

(ref: 2010A&A...520A..84P) Peng, T. C., Wyrowski, F., van der Tak, F. F. S., Menten, K. M., & Walmsley, C. M. 2010, A&A, 520, A84

(ref: 2010ApJ...711.1017P) Peters, T., Banerjee, R., Klessen, R. S., et al. 2010a, ApJ, 711, 1017

(ref: 2010ApJ...719..831P) Peters, T., Mac Low, M.-M., Banerjee, R., Klessen, R. S., & Dullemond, C. P. 2010b, ApJ, 719, 831

(ref: 2022Pouteau) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26

(ref: 2020ApJ...899...94R) Rivera-Soto, R., Galván-Madrid, R., Ginsburg, A., & Kurtz, S. 2020, ApJ, 899, 94

(ref: 2019A&A...622A..48R) Rugel, M. R., Rahner, D., Beuther, H., et al. 2019, A&A, 622, A48

(ref: 2015ApJ...813...25S) Saral, G., Hora, J. L., Willis, S. E., et al. 2015, ApJ, 813, 25

(ref: 1976ApJ...206..718S) Scoville, N. Z. & Kwan, J. 1976, ApJ, 206, 718

(ref: 1991A&A...251..231S) Sievers, A. W., Mezger, P. G., Bordeon, M. A., et al. 1991, A&A, 251, 231

(ref: 2009MNRAS.400.1775S) Smith, R. J., Longmore, S., & Bonnell, I. 2009, MNRAS, 400, 1775

(ref: 2016ApJ...818...52T) Tanaka, K. E. I., Tan, J. C., & Zhang, Y. 2016, ApJ, 818, 52

(ref: 2019MNRAS.490.3061V) Vázquez-Semadeni, E., Palau, A., Ballesteros-Paredes, J., Gómez, G. C., & Zamora-Avilés, M. 2019, MNRAS, 490, 3061

(ref: 1987Sci...238.1550W) Welch, W. J., Dreher, J. W., Jackson, J. M., Terebey, S., & Vogel, S. N. 1987, Science, 238, 1550

(ref: 2001ApJ...550L..81W) Wilner, D. J., De Pree, C. G., Welch, W. J., & Goss, W. M. 2001, ApJL, 550, L81

(ref: Wilson09) Wilson, T. L., Rohlfs, K., & Hüttemeister, S. 2009, Tools of Radio Astronomy

(ref: 2013ApJ...775...79Z) Zhang, B., Reid, M. J., Menten, K. M., et al. 2013, ApJ, 775, 79

(ref: 2023MNRAS.520.3245Z) Zhang, C., Zhu, F.-Y., Liu, T., et al. 2023, MNRAS, 520, 3245

(ref: 2022ApJ...936...68Z) Zhang, Y., Tanaka, K. E. I., Tan, J. C., et al. 2022, ApJ, 936, 68

# Core catalog

[2](#tab:cores-par) lists the physical properties, detection (or non detection) of H/UC HII regions and hot molecular cores for the 129 cores detected at 1.3 mm in W49. The labels of H/UC HII regions previously identified at the core positions are also given.

\(1\) Core number in the getsf catalog. (2) Right Ascension and Declination coordinates. (3) Subregion: (W49-)N, (W49-)SW or (W49)-out(skirts). (4) FWHM major and minor axis. (5) Position Angle (West to North) of the ellipse. (6,7) Integrated fluxes in B6 and BX. (8) Detection of the H/UC HII region in X band 3.3 cm (BX) and/or in H30$\alpha$ (RL). (9) Identification of the associated H/UC HII region in the catalogs of (cite: 1997ApJ...482..307D; 2020AJ....160..234D). (10) Cores associated to hot molecular core emission are marked with \*.

+:------:+:------------------------:+:------:+:--------------------------------------------:+:------:+:----------------------:+:----------------------:+:------:+:--------:+:------:+:-:+
| n      | R.A. Dec.                | Region | Size                                         | $PA$   | $F^{\rm int}_{\rm B6}$ | $F^{\rm int}_{\rm BX}$ | HII    | Cross ID | HMC    |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
|        | \[ICRS\]                 |        | \[$\ensuremath{''} \times \ensuremath{''}$\] |        | \[mJy.beam$^{-1}$\]    | \[mJy.beam$^{-1}$\]    |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| \(1\)  | \(2\)                    | \(3\)  | \(4\)                                        | \(5\)  | \(6\)                  | \(7\)                  | \(8\)  | \(9\)    | \(10\) |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| **Table A** – continued from previous page                                                                                                                                        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| n      | R.A. Dec.                | Region | Size                                         | $PA$   | $F^{\rm int}_{\rm B6}$ | $F^{\rm int}_{\rm BX}$ | HII    | Cross ID | HMC    |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
|        | \[ICRS\]                 |        | \[$\ensuremath{''} \times \ensuremath{''}$\] |        | \[mJy.beam$^{-1}$\]    | \[mJy.beam$^{-1}$\]    |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| \(1\)  | \(2\)                    | \(3\)  | \(4\)                                        | \(5\)  | \(6\)                  | \(7\)                  | \(8\)  | \(9\)    | \(10\) |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
|        | 19:10:13.419  9:06:13.00 | N      | 0.33$\,\times\,$0.27                         | 10     | 1031.9                 | 36.6                   | BX+RL  | G2a      |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 2      | 19:10:13.149  9:06:12.72 | N      | 0.37$\,\times\,$0.33                         | 117    | 728.4                  | 38.5                   | BX+RL  | B2       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 3      | 19:10:12.889  9:06:11.73 | N      | 0.39$\,\times\,$0.29                         | 169    | 365.0                  | 56.0                   | BX+RL  | A2       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 4      | 19:10:10.938  9:05:17.53 | SW     | 0.31$\,\times\,$0.27                         | 166    | 94.6                   |                        | RL     | \-       | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 5      | 19:10:16.356  9:06:07.04 | out    | 0.49$\,\times\,$0.35                         | 115    | 133.2                  |                        | RL     | O        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 6      | 19:10:13.614  9:06:49.12 | N      | 0.45$\,\times\,$0.30                         | 118    | 75.0                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 7      | 19:10:13.144  9:06:18.76 | N      | 0.35$\,\times\,$0.29                         | 142    | 188.5                  | 40.6                   | BX+RL  | C        | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 8      | 19:10:14.130  9:06:25.00 | N      | 0.44$\,\times\,$0.30                         | 155    | 200.2                  | 1.5                    | BX     | J1       | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 9      | 19:10:11.050  9:05:20.11 | SW     | 0.44$\,\times\,$0.40                         | 17     | 85.9                   |                        | RL     | R        | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 10     | 19:10:13.455  9:06:12.79 | N      | 0.33$\,\times\,$0.27                         | 20     | 332.0                  | 12.3                   | BX+RL  | G2c      |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 11     | 19:10:15.369  9:06:14.95 | N      | 0.40$\,\times\,$0.33                         | 174    | 56.2                   | 22.0                   | BX+RL  | N        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 12     | 19:10:16.372  9:06:06.81 | out    | 0.47$\,\times\,$0.31                         | 123    | 116.1                  |                        | RL     | O        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 13     | 19:10:13.116  9:06:12.36 | N      | 0.30$\,\times\,$0.26                         | 11     | 149.0                  | 12.7                   | BX+RL  | B1       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 14     | 19:10:13.202  9:06:11.13 | N      | 0.68$\,\times\,$0.57                         | 69     | 203.9                  | 135.2                  | BX+RL  | D        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 15     | 19:10:13.340  9:06:21.37 | N      | 0.56$\,\times\,$0.47                         | 97     | 59.1                   | 60.1                   | BX+RL  | F        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 16     | 19:10:13.373  9:06:12.58 | N      | 0.46$\,\times\,$0.39                         | 146    | 279.9                  | 69.0                   | BX+RL  | G1       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 17     | 19:10:12.884  9:06:12.16 | N      | 0.39$\,\times\,$0.34                         | 30     | 125.9                  | 17.7                   | BX+RL  | A1       | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 18     | 19:10:13.312  9:06:19.87 | N      | 0.44$\,\times\,$0.32                         | 172    | 93.3                   | 1.0                    | BX     | \-       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 19     | 19:10:14.645  9:06:25.97 | N      | 0.41$\,\times\,$0.40                         | 143    | 20.3                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 20     | 19:10:13.279  9:06:12.79 | N      | 0.39$\,\times\,$0.29                         | 0      | 82.6                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 22     | 19:10:14.628  9:06:45.96 | N      | 0.38$\,\times\,$0.33                         | 6      | 10.5                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 23     | 19:10:13.060  9:06:16.07 | N      | 0.35$\,\times\,$0.33                         | 178    | 17.7                   | 12.7                   | BX+RL  | C1       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 24     | 19:10:14.284  9:06:22.22 | N      | 0.44$\,\times\,$0.40                         | 69     | 20.7                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 25     | 19:10:15.358  9:06:15.36 | N      | 0.36$\,\times\,$0.33                         | 167    | 21.3                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 26     | 19:10:12.665  9:06:07.57 | N      | 0.48$\,\times\,$0.44                         | 71     | 25.0                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 27     | 19:10:13.272  9:06:16.38 | N      | 0.52$\,\times\,$0.37                         | 47     | 53.7                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 28     | 19:10:13.149  9:06:13.84 | N      | 0.45$\,\times\,$0.38                         | 72     | 112.0                  | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 29     | 19:10:13.259  9:06:12.19 | N      | 0.37$\,\times\,$0.31                         | 35     | 23.3                   | 17.3                   | BX+RL  | E3       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 30     | 19:10:14.137  9:06:26.60 | N      | 0.45$\,\times\,$0.38                         | 110    | 27.9                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 31     | 19:10:14.312  9:06:22.21 | N      | 0.37$\,\times\,$0.27                         | 23     | 11.7                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 32     | 19:10:13.170  9:06:13.36 | N      | 0.36$\,\times\,$0.33                         | 64     | 70.4                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 34     | 19:10:13.259  9:06:18.88 | N      | 0.38$\,\times\,$0.29                         | 164    | 32.2                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 35     | 19:10:13.441  9:06:07.11 | N      | 0.28$\,\times\,$0.25                         | 27     | 4.5                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 36     | 19:10:12.097  9:06:14.64 | N      | 0.41$\,\times\,$0.26                         | 74     | 9.0                    | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 37     | 19:10:14.182  9:06:20.58 | N      | 0.32$\,\times\,$0.28                         | 103    | 2.9                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 39     | 19:10:11.671  9:05:26.86 | SW     | 0.55$\,\times\,$0.45                         | 153    | 30.6                   |                        | RL     | S        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 40     | 19:10:13.392  9:06:11.82 | N      | 0.56$\,\times\,$0.48                         | 10     | 79.0                   | 54.8                   | BX+RL  | G1S      |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 42     | 19:10:14.664  9:06:25.53 | N      | 0.45$\,\times\,$0.36                         | 107    | 12.0                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 43     | 19:10:13.348  9:06:16.05 | N      | 0.39$\,\times\,$0.33                         | 155    | 25.9                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 44     | 19:10:12.703  9:06:11.29 | N      | 0.31$\,\times\,$0.26                         | 24     | 22.2                   | 1.5                    | BX+RL  | \-       | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 45     | 19:10:13.211  9:06:14.30 | N      | 0.31$\,\times\,$0.27                         | 26     | 24.8                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 46     | 19:10:13.498  9:06:11.77 | N      | 0.36$\,\times\,$0.32                         | 179    | 58.1                   | 34.7                   | BX+RL  | G3b      |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 47     | 19:10:13.498  9:06:12.42 | N      | 0.37$\,\times\,$0.26                         | 8      | 43.7                   | 20.3                   | BX+RL  | G3a      |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 48     | 19:10:13.721  9:06:44.58 | N      | 0.37$\,\times\,$0.33                         | 53     | 3.6                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 49     | 19:10:12.671  9:06:18.28 | N      | 0.39$\,\times\,$0.29                         | 172    | 7.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 50     | 19:10:10.686  9:05:16.78 | SW     | 0.95$\,\times\,$0.70                         | 134    | 36.7                   |                        | RL     | R3       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 51     | 19:10:12.644  9:06:18.93 | N      | 0.39$\,\times\,$0.30                         | 37     | 4.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 52     | 19:10:16.504  9:06:04.24 | out    | 0.63$\,\times\,$0.53                         | 23     | 11.4                   |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 53     | 19:10:13.364  9:06:18.01 | N      | 0.44$\,\times\,$0.41                         | 88     | 10.3                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 54     | 19:10:13.323  9:06:16.32 | N      | 0.33$\,\times\,$0.30                         | 27     | 16.8                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 55     | 19:10:13.230  9:06:54.16 | N      | 0.72$\,\times\,$0.58                         | 130    | 4.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 56     | 19:10:13.188  9:06:12.85 | N      | 0.45$\,\times\,$0.36                         | 0      | 81.5                   | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 57     | 19:10:13.114  9:06:13.77 | N      | 0.42$\,\times\,$0.37                         | 120    | 62.3                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 58     | 19:10:16.666  9:05:49.88 | out    | 0.44$\,\times\,$0.32                         | 53     | 7.2                    |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 59     | 19:10:16.402  9:06:07.36 | out    | 0.47$\,\times\,$0.36                         | 143    | 22.8                   |                        | RL     | \-       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 60     | 19:10:15.754  9:06:05.78 | N      | 0.49$\,\times\,$0.40                         | 169    | 4.7                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 61     | 19:10:15.256  9:06:10.99 | N      | 0.32$\,\times\,$0.29                         | 92     | 2.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 62     | 19:10:12.843  9:06:11.44 | N      | 0.61$\,\times\,$0.42                         | 149    | 76.7                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 63     | 19:10:14.605  9:06:26.38 | N      | 0.45$\,\times\,$0.32                         | 4      | 7.2                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 65     | 19:10:14.159  9:06:21.56 | N      | 0.60$\,\times\,$0.54                         | 110    | 14.2                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 66     | 19:10:13.385  9:06:19.37 | N      | 0.40$\,\times\,$0.36                         | 37     | 19.7                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 67     | 19:10:13.656  9:06:21.49 | N      | 0.57$\,\times\,$0.43                         | 46     | 10.0                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 68     | 19:10:12.800  9:06:27.54 | N      | 0.54$\,\times\,$0.34                         | 85     | 6.9                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 69     | 19:10:14.186  9:06:15.32 | N      | 0.66$\,\times\,$0.41                         | 42     | 21.3                   | 17.2                   | BX+RL  | J        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 70     | 19:10:12.746  9:06:10.33 | N      | 0.36$\,\times\,$0.32                         | 53     | 24.0                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 71     | 19:10:13.434  9:06:22.78 | N      | 0.46$\,\times\,$0.36                         | 155    | 7.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 72     | 19:10:13.178  9:06:18.28 | N      | 0.50$\,\times\,$0.40                         | 143    | 42.5                   | 31.2                   | BX+RL  | C        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 73     | 19:10:13.601  9:06:11.02 | N      | 0.43$\,\times\,$0.30                         | 0      | 45.6                   | 30.1                   | BX+RL  | G3d      |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 74     | 19:10:14.563  9:06:20.47 | N      | 0.50$\,\times\,$0.40                         | 50     | 8.7                    | 3.6                    | BX+RL  | L        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 75     | 19:10:14.126  9:06:24.28 | N      | 0.33$\,\times\,$0.21                         | 20     | 17.8                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 76     | 19:10:13.323  9:06:25.53 | N      | 0.47$\,\times\,$0.31                         | 124    | 6.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 77     | 19:10:13.898  9:06:36.91 | N      | 0.29$\,\times\,$0.24                         | 47     | 1.5                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 78     | 19:10:16.344  9:06:07.75 | out    | 0.53$\,\times\,$0.49                         | 111    | 21.8                   |                        | RL     | \-       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 79     | 19:10:13.018  9:06:17.05 | N      | 0.60$\,\times\,$0.55                         | 90     | 16.2                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 80     | 19:10:10.801  9:05:19.45 | SW     | 1.03$\,\times\,$0.77                         | 137    | 25.9                   |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 81     | 19:10:14.610  9:06:02.65 | N      | 0.47$\,\times\,$0.37                         | 41     | 6.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 82     | 19:10:14.178  9:06:26.65 | N      | 0.34$\,\times\,$0.29                         | 55     | 9.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 83     | 19:10:13.135  9:06:13.45 | N      | 0.43$\,\times\,$0.38                         | 75     | 83.7                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 84     | 19:10:12.329  9:06:18.58 | N      | 0.28$\,\times\,$0.25                         | 176    | 2.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 85     | 19:10:12.720  9:06:28.69 | N      | 0.30$\,\times\,$0.28                         | 18     | 2.8                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 86     | 19:10:13.234  9:06:12.68 | N      | 0.44$\,\times\,$0.40                         | 177    | 49.8                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 87     | 19:10:14.184  9:06:14.37 | N      | 1.05$\,\times\,$0.94                         | 178    | 32.2                   | 13.9                   | BX+RL  | J        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 88     | 19:10:12.613  9:06:22.60 | N      | 0.43$\,\times\,$0.31                         | 168    | 3.5                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 89     | 19:10:13.231  9:06:08.87 | N      | 0.53$\,\times\,$0.38                         | 152    | 9.6                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 90     | 19:10:15.433  9:06:16.78 | N      | 0.43$\,\times\,$0.32                         | 11     | 3.3                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 91     | 19:10:11.174  9:05:53.85 | N      | 0.45$\,\times\,$0.34                         | 12     | 3.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 92     | 19:10:12.685  9:06:32.36 | N      | 0.97$\,\times\,$0.90                         | 127    | 7.3                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 93     | 19:10:15.317  9:06:14.80 | N      | 0.54$\,\times\,$0.34                         | 5      | 13.4                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 94     | 19:10:14.509  9:06:22.47 | N      | 1.06$\,\times\,$0.82                         | 67     | 25.7                   | \-                     | RL     | L        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 95     | 19:10:11.487  9:05:32.14 | N      | 0.31$\,\times\,$0.27                         | 24     | 2.4                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 96     | 19:10:13.571  9:06:21.34 | N      | 0.47$\,\times\,$0.35                         | 173    | 9.9                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 97     | 19:10:13.307  9:06:17.02 | N      | 0.37$\,\times\,$0.29                         | 162    | 15.2                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 98     | 19:10:14.796  9:06:44.25 | N      | 0.68$\,\times\,$0.47                         | 81     | 5.8                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 99     | 19:10:15.807  9:06:05.59 | N      | 0.29$\,\times\,$0.27                         | 157    | 1.4                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 100    | 19:10:11.490  9:06:24.34 | N      | 0.35$\,\times\,$0.29                         | 11     | 1.5                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 101    | 19:10:13.459  9:06:20.14 | N      | 0.49$\,\times\,$0.32                         | 144    | 15.4                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 102    | 19:10:12.779  9:06:11.13 | N      | 0.34$\,\times\,$0.29                         | 24     | 19.5                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 103    | 19:10:14.825  9:06:36.88 | N      | 0.69$\,\times\,$0.50                         | 140    | 5.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 104    | 19:10:14.037  9:06:23.56 | N      | 0.41$\,\times\,$0.35                         | 122    | 15.5                   | 0.7                    | BX     | \-       | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 105    | 19:10:13.630  9:06:20.30 | N      | 1.03$\,\times\,$0.86                         | 146    | 33.5                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 106    | 19:10:12.720  9:06:28.38 | N      | 0.41$\,\times\,$0.39                         | 52     | 4.5                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 107    | 19:10:16.297  9:06:06.66 | out    | 0.55$\,\times\,$0.40                         | 157    | 14.8                   |                        | RL     | \-       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 108    | 19:10:13.719  9:06:25.03 | N      | 0.40$\,\times\,$0.34                         | 111    | 5.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 109    | 19:10:14.237  9:06:28.51 | N      | 0.48$\,\times\,$0.37                         | 162    | 11.0                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 110    | 19:10:15.409  9:06:11.87 | N      | 0.65$\,\times\,$0.36                         | 2      | 5.8                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 111    | 19:10:11.629  9:06:16.03 | N      | 0.35$\,\times\,$0.26                         | 172    | 3.4                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 112    | 19:10:11.731  9:05:27.37 | SW     | 0.67$\,\times\,$0.43                         | 10     | 25.7                   |                        | RL     | S        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 113    | 19:10:10.277  9:05:14.07 | SW     | 0.30$\,\times\,$0.23                         | 160    | 4.5                    |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 114    | 19:10:12.838  9:06:29.46 | N      | 0.34$\,\times\,$0.27                         | 180    | 3.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 115    | 19:10:16.826  9:05:49.99 | out    | 0.83$\,\times\,$0.66                         | 4      | 11.1                   |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 116    | 19:10:14.747  9:06:25.65 | N      | 0.50$\,\times\,$0.34                         | 150    | 4.9                    | 3.4                    | BX+RL  | M        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 117    | 19:10:13.683  9:06:10.06 | N      | 0.36$\,\times\,$0.34                         | 119    | 6.4                    | 2.4                    | BX     | \-       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 119    | 19:10:10.956  9:05:18.60 | SW     | 0.34$\,\times\,$0.25                         | 90     | 2.5                    |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 120    | 19:10:14.284  9:06:32.28 | N      | 0.55$\,\times\,$0.53                         | 52     | 11.3                   | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 121    | 19:10:14.253  9:06:29.98 | N      | 0.42$\,\times\,$0.35                         | 115    | 4.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 122    | 19:10:12.416  9:06:06.76 | N      | 0.75$\,\times\,$0.64                         | 72     | 8.4                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 123    | 19:10:10.758  9:05:21.46 | SW     | 0.30$\,\times\,$0.23                         | 34     | 1.7                    |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 124    | 19:10:13.735  9:06:49.42 | N      | 0.44$\,\times\,$0.40                         | 147    | 4.4                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 125    | 19:10:14.685  9:06:45.97 | N      | 0.33$\,\times\,$0.24                         | 12     | 2.4                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 126    | 19:10:13.779  9:06:16.81 | N      | 0.38$\,\times\,$0.26                         | 15     | 3.5                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 128    | 19:10:16.708  9:05:49.17 | out    | 0.34$\,\times\,$0.27                         | 73     | 3.4                    |                        |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 130    | 19:10:13.780  9:06:22.11 | N      | 0.37$\,\times\,$0.29                         | 173    | 4.1                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 131    | 19:10:10.541  9:05:14.08 | SW     | 0.30$\,\times\,$0.25                         | 124    | 3.2                    |                        | RL     | Q        |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 133    | 19:10:14.122  9:06:26.01 | N      | 0.39$\,\times\,$0.35                         | 65     | 9.9                    | \-                     |        |          | \*     |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 138    | 19:10:14.525  9:06:28.78 | N      | 0.40$\,\times\,$0.30                         | 173    | 1.7                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 140    | 19:10:14.262  9:06:26.22 | N      | 0.36$\,\times\,$0.26                         | 117    | 3.0                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 141    | 19:10:13.980  9:06:24.90 | N      | 0.34$\,\times\,$0.27                         | 103    | 2.9                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 142    | 19:10:14.980  9:06:03.82 | N      | 0.30$\,\times\,$0.23                         | 142    | 1.7                    | \-                     |        |          |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+
| 147    | 19:10:10.893  9:05:16.78 | SW     | 0.95$\,\times\,$0.68                         | 152    | 20.0                   |                        | RL     | \-       |        |   |
+--------+--------------------------+--------+----------------------------------------------+--------+------------------------+------------------------+--------+----------+--------+---+

: Main characteristics of cores detected on the 1.3 mm continuum image.

[^1]: https://imager.oasu.u-bordeaux.fr

[^2]: http://www.iram.fr/IRAMFR/GILDAS

[^3]: Contrarily to the peak intensity in X band $S^{\rm peak}_{\rm BX}$, which is measured at the center of the ellipse defined in the B6 map, $F^{\rm max}_{\rm BX}$ is measured on the brightest pixel within the ellipse.

[^4]: 5 dendrogram HII structures are associated with more than one dust core.

</paper>

Write the methods card for this paper.