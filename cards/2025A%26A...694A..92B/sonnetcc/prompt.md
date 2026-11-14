# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A..92B\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694A..92B",
 "title": "Protostellar Outflows at the EarliesT Stages (POETS) VI. Evidence of disk-wind in G11.92-0.61 MM1",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Bayandina, O. S.",
 "n_authors": 6,
 "arxiv_id": "2501.17482",
 "doi": "10.1051/0004-6361/202452843",
 "alma_projects_linked_by_archive": [
  "2019.1.01639.S"
 ]
}
```

Paper text:
<paper>
# Protostellar Outflows at the EarliesT Stages (POETS)\
VI. Evidence of disk-wind in G11.92-0.61 MM1

Magnetohydrodynamic disk-winds are thought to play a key role in the formation of massive stars by providing the fine-tuning between accretion and ejection, where excess angular momentum is redirected away from the disk, allowing further mass growth of a young protostar. However, only a limited number of disk-wind sources have been detected to date. To better constrain the exact mechanism of this phenomenon, expanding the sample is critical.

We performed a detailed analysis of the disk-wind candidate G11.92-0.61 MM1 by estimating the physical parameters of the massive protostellar system and constraining the wind-launching mechanism.

Atacama Large Millimeter/submillimeter Array (ALMA) Band 6 observations of G11.92-0.61 MM1 were conducted in September 2021 with ALMA’s longest baselines, which provided a synthesised beam of $\sim$30 mas. We obtained high-resolution images of the CH$_3$CN ($\varv_8=1$ and $\varv=0$), CH$_3$OH, SO$_2$, and SO molecular lines, as well as the 1.3 mm continuum.

Our high-resolution molecular data allowed us to refine the parameters of the disk-outflow system in MM1. The rotating disk is resolved into two regions with distinct kinematics: the inner region ($<$300 au) is traced by high-velocity emission of high-excitation CH$_3$CN lines and shows a Keplerian rotation; the outer region ($>$300 au), traced by mid-velocity CH$_3$CN emission, rotates in a sub-Keplerian regime. The central source is estimated to be $\sim$20 $M_{\odot}$, which is about half the mass estimated in previous lower-resolution studies. A strong collimated outflow is traced by SO and SO$_2$ emission up to $\sim$3400 au around MM1a. The SO and SO$_2$ emissions show a rotation-dominated velocity pattern, a constant specific angular momentum, and a Keplerian profile that suggests a magneto-centrifugal disk-wind origin with launching radii of $\sim$50-100 au.

G11.92-0.61 MM1 appears to be one of the clearest cases of molecular line-traced disk-winds detected around massive protostars.

# Introduction

Star formation occurs through the interplay of accretion and ejection – seemingly antagonistic forces that are in fact two sides of the same coin. A surprising amount of value is hidden in the thin and often overlooked edge of the coin, the region of interaction between accretion and ejection.

As accretion feeds a protostar, ejection removes angular momentum from the accreting matter, allowing the process to continue. Although the fundamental concept is clear, formulating the actual mechanism of gas-launching requires a great deal of theoretical and observational work. Theoretical works have come a long way from assuming the impact of hydrodynamics and radiation only (for example, (cite: Canto1980)), by, for example, including the role of magnetic fields via ideal magnetohydrodynamics (MHD; for example, (cite: Blandford1982)) and adding further physics, such as non-ideal MHD effects (for example, (cite: Suriano2019)).

Observational studies first examined large-scale low-velocity outflows (for example, (cite: Bally1983)) before turning to jets (compact, collimated shocked gas ejected at high speeds and powering large-scale outflows; for example, (cite: McCaughrean1994; Frank2014)). Modern observing facilities are now finally able to achieve the resolutions needed to study the launching region of jets. Jets are modelled to be launched by rotation and gravitational energy along the magnetic field lines, but the precise acceleration mechanism is still debated. The ‘X-wind’ theory assumes that jets are launched from the inner edge of an accretion disk, a small region within $<$1 au of the star that is dominated solely by the stellar magnetic field (cite: Shu1995). In contrast, the ‘disk-wind’ theory assumes that jets are launched at radii larger by two to three orders of magnitude, where the poloidal component of the disk’s magnetic field dominates (cite: Pudritz2007).

Which theory is correct, X-wind or disk-wind, is still an open question. Although the disk-wind theory has gained more support lately, the evidence in its favour was mostly obtained for low-mass protostars (cite: Pascucci2023). The main obstacle to studying the disk-wind emission in massive protostars is the difficulty in achieving a spatial resolution sufficient to access the region of disk-jet interaction, as well as in identifying suitable tracers. The high resolution required to resolve the jet’s launching regions and obtain evidence for the existence of a disk-wind has been achieved with very long baseline interferometry observations of masers: SiO masers in Orion-BN/KL (cite: Matthews2010) and H$_2$O masers in IRAS 21078+5211 (cite: Moscadelli2022).

Such a high resolution has been achieved with the Atacama Large Millimeter/submillimeter Array (ALMA) for Orion Source I, which is located at a close distance of 418 pc (cite: Kim2008), where (cite: Hirota2017) found compelling evidence for a disk-wind through the detection of a rotating bipolar outflow traced by SiO emission. In this case, neither stellar winds nor X-winds were found to be consistent with the estimated launching radius ($>$10 au) and velocity (10 km/s). For a few more maser sources, the possibility of the presence of disk-winds was only hypothesised (for example, (cite: Moscadelli2011; Sanna2012)).

With the aim of shedding light on the nature and properties of protostellar winds and jets, we started the large project POETS (cite: Moscadelli2016; Sanna2018; Moscadelli2019). Initially, the project was based on a high-resolution survey of radio continuum and water masers, which were observed with the goal of tracing free-free emission from ionised gas in the inner outflow cavities and fast shocked layers of outflowing gas. In recent years, we have selected a number of targets from the POETS sample for follow-up observations with multiple molecular lines in order to provide a view of the diverse phenomenology and to obtain information on outflow tracers. Here, we report the results for one of the POETS targets, G11.92-0.61.

The star-forming region G11.92-0.61 is a promising target for studying the ejection process in massive protostars. Located in the Galactic plane, at a distance of $3.37^{+0.39}_{-0.32}$ kpc (cite: Sato2014), G11.92-0.61 is associated with an infrared dark cloud that is actively forming both low- and high-mass stars (cite: Cyganowski2017). The region has been extensively studied in a variety of wavelengths, which revealed a complex and dynamic environment.

At first, G11.92-0.61 attracted attention when it was identified as an extended green object (EGO; (cite: Cyganowski2008)) and as such was considered to be a massive protostellar outflow candidate. The 4.5 $\mu$m image of G11.92-0.61 showed a bipolar morphology consisting of a north-east (NE) and a south-west (SW) region (cite: Cyganowski2008; Cyganowski2011). Initial (sub-)millimetre observations of the region detected only three massive compact millimetre-continuum cores (cite: Cyganowski2011), while follow-up ALMA observations revealed 16 more low-mass millimetre-continuum cores (cite: Cyganowski2017). The detected millimetre-continuum cores of low and high masses (cite: Cyganowski2017), as well as the 6.7 GHz methanol (cite: Cyganowski2009) and 22 GHz water masers (for example, (cite: Moscadelli2016)), appeared to be predominantly associated with the NE region (cite: Cyganowski2011), with only a cluster of 44 GHz methanol masers found in the SW region (cite: Cyganowski2009; Cyganowski2011; Cyganowski2017). Out of the EGO sample studied in (cite: Cyganowski2008), G11.92-0.61 is the only one that might contain multiple massive protostars, as suggested by the association with two distinct sites of 6.7 GHz methanol maser emission.

The brightest and most massive millimetre core of the region, MM1, is considered an example of a forming proto-O star with an active outflow and ongoing accretion. The central source of MM1 seems to be very young, showing weak ($\sim$1 mJy) centimetre-continuum emission but rich spectral line and maser emission (cite: Cyganowski2011b; Ilee2016; Moscadelli2016). The Submillimeter Array (SMA) and ALMA studies of hot-core molecules in MM1, presented in (cite: Ilee2016) and (cite: Ilee2018), respectively, revealed the presence of a massive Keplerian accretion disk with an enclosed mass of the central object estimated to be $\sim$40 M$_\odot$ (cite: Ilee2018). However, the detected luminosity of only $\sim$10$^4$ L$_{\rm sun}$ (cite: Cyganowski2011; Moscadelli2016) appeared to be too low for such a massive object; (cite: Ilee2018) proposed that such a discrepancy might be explained if the luminosity comes from accretion or if multiple stars are present at the disk centre. The detection of a weak 1.3 mm continuum source to the south-east of MM1, which was denominated MM1b, was interpreted as a sign of one of the first observed examples of disk fragmentation around a high-mass protostar (cite: Ilee2018). However, the case calls for further investigation as MM1b is separated from MM1 by $\sim$2000 au and in fact seems to be located outside the disk.

MM1 drives a massive, collimated bipolar molecular outflow that is detected in numerous tracers (cite: Cyganowski2011). The outflow has a position angle (PA) of $\sim$52$^{\circ}$, with the red lobe propagating to the NE and the blue lobe propagating to the SW (cite: Cyganowski2011; Ilee2016). One of the sites of 6.7 GHz methanol maser emission detected in the region is associated with MM1 (cite: Cyganowski2009). However, the methanol maser does not coincide with the continuum peak, and is located to the south, downstream of the outflow. The intense 22 GHz water masers (cite: Hofner1996; Breen2011; Sato2014) associated with MM1 show a bipolar structure and velocity pattern similar to the large-scale outflow (cite: Moscadelli2016; Moscadelli2019), but the kinematic structure traced by the water emission remains unclear. (cite: Moscadelli2019) have suggested that the 22 GHz water maser may be explained either as tracing a disk-wind or as being due to central source multiplicity.

In this article we present the results of our higher-angular-resolution ALMA observations of the high-mass core G11.92-0.61 MM1. We aim to provide a detailed view of the physical and chemical properties of G11.92-0.61 MM1 and clarify the structure of the source.

# Observations and data reduction

The ALMA observations of G11.92-0.61 MM1 were conducted on September 29, 2021 (project 2019.1.01639.S) for a total observing time of 1.5 hours. The array configuration was C43-9/10 with 45 antennas. The observations provided a synthesised beam with a size of 28 mas $\times$ 25 mas, and PA=-66$^{\circ}$ (corresponding to a linear resolution of $\sim$100 au at the distance of 3.37 kpc to the source).

Two sources, J1924-2914 and J1830-1606, were observed as flux, delay, and bandpass calibrators. The quasar J1825-1718 was used as phase calibrator.

The spectral setup consisted of five spectral windows centred at 220.63, 222.15, 221.44, 219.91, and 219.44 GHz in Band 6. Each spectral window was sampled with 960 channels each of $\sim$0.6 MHz wide, providing a spectral resolution of $\sim$0.7 km s$^{-1}$.

Spectral line identification was performed in the Cube Analysis and Rendering Tool for Astronomy (CARTA[^1]; (cite: Comrie2020)) and MAdrid Data CUBe Analysis (MADCUBA; (cite: Martin2019)) packages. The molecular line data modelling and estimation of the physical parameters were carried out using the SLIM tool of MADCUBA.

Imaging and data cubes analysis were performed with the Common Astronomy Software Applications (CASA[^2]; (cite: CASA2022)) package. The spectral line and continuum images were created using the CASA task *tclean* with natural weighting. From the obtained line cubes, we computed Moment 0 and 1 maps using the CASA task *immoments*. The velocity range was chosen to include the target line only, and the threshold was set at a 5$\sigma$ rms level. Additionally, we produced position–velocity (PV) diagrams for the line data using the GILDAS[^3] software. Finally, we also created ‘peak maps’ with the goal of determining the emission peak position in individual velocity channels. Given that emission in some channels of the line cubes was too diffuse or weak to be properly fitted, we ‘tapered’ the visibilities to create lower resolution cubes with the synthesised beam of $\sim$0.15$''$ (which was found to be the optimal balance between retaining high resolution and obtaining distinct peaks). Then we fitted the emission peaks in each channel with the task *imfit*, which yielded position uncertainties from $\sim$0.8 mas ($\sim$3 au) for bright and compact emission and up to $\sim$8 mas ($\sim$30 au) for weak, extended emission.

# Results

## 1.3 mm continuum

The 1.3 mm continuum yields detection of two emission peaks corresponding to the sources MM1a and MM1b. The 1.3 mm continuum image is presented in Fig. [1](#fig:cont) and the parameters of the detected continuum sources are listed in Table [\[tab:cont\]](#tab:cont). The flux density of MM1b is $\sim$1 mJy, corresponding to $\sim$5$\sigma$ level, and thus the detection is marginal. The 1.3 mm continuum emission of MM1a is found to come from an NW-SE elongated region of $\sim$0.16$''$ ($\sim$500 au) with PA $\sim$130$^{\circ}$ and integrated flux density of $\sim$58 mJy (Table [\[tab:cont\]](#tab:cont)). Interestingly, Fig. [1](#fig:cont) shows some weaker emission towards the south and west from the peak, apparently surrounding the axis of the blue lobe of the outflow observed by (cite: Ilee2016).

![image](Continuum.pdf)\

Considering the measured flux density at 1.3 mm and assuming that the dust is optically thin and in thermal equilibrium with the gas at average temperature of $\sim$300 K (for CH$_3$CN and CH$_3$OH; see Sect. [3.2](#ResLines) and Table [\[tab:l-param\]](#tab:l-param)), we can use the standard approach of (cite: Hildebrand1983). More precisely, by applying Eqs. (1) and (2) from (cite: Schuller2009) to estimate the total gas mass and column density of H$_2$, we derive $M$ $\sim$2.5 $M_{\odot}$ and $N_{\rm H_2}$ = $\sim$1$\times$10$^{23}$ cm$^{-2}$. These numbers are close to the ones obtained in the lower-resolution 1.3 mm continuum observations of (cite: Ilee2018). However, we note that our estimates may be lower limits because part of the continuum emission could have been resolved out; additionally, the column density estimate is probably a lower limit because the continuum source is not resolved in the NE-SW direction.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | RA(J2000) | Dec(J2000) | Size | PA | Int. flux | Peak flux |  |
|  | ($^h$ $^m$ $^s$) | ($^\circ$ $\ensuremath{'}$ $\ensuremath{''}$) | ($\ensuremath{''}$$\times$$\ensuremath{''}$) | ($^\circ$) | (mJy) | (mJy/beam) |  |
| MM1a | 18:13:58.1106$\pm$0.0001 | -18:54:20.199$\pm$0.001 | 0.16$\times$0.05 | 132 | 57.8$\pm$1.4 | 10.3$\pm$0.2 |  |
| MM1b$^{(a)}$ | 18:13:58.1274$\pm$0.0002 | -18:54:20.726$\pm$0.002 | \- | \- | 1.0$\pm$0.2 | 1.0$\pm$0.1 |  |

Table notes: $^{(a)}$Tentative detection at 5$\sigma$ level (the rms of the continuum image is $\sim$0.1 mJy beam$^{-1}$).

## Molecular lines

Abundant molecular line emission is detected towards G11.92-0.61 MM1a. In order to illustrate the molecular emission detected at different physical scales, we present integrated intensity (moment 0) and velocity field (moment 1) maps for selected molecular lines (see Fig. [2](#fig:M0M1)).

All detected molecular lines are found to be associated with the source MM1a, no emission is detected at the position of the MM1b continuum peak. The most compact emissions of the high-excitation energy CH$_3$CN $\varv_8=1$ and $\varv=0$ from $K$=4 to 8 molecular lines are found to originate from a $\sim$0.2$''$ (or $\sim$700 au) region around MM1a, showing a similar size, elongation, and PA as the 1.3 mm continuum emission (Figs. [2](#fig:M0M1)a and [2](#fig:M0M1)c). Apart from the compact region around MM1a, the lower-excitation energy lines of CH$_3$OH and CH$_3$CN $\varv=0$ $K$=1 to 3 also follow a larger region with an extent of $\sim$0.6$''$ ($\sim$2000 au) in the direction perpendicular to the continuum source and the compact molecular line emission (Figs. [2](#fig:M0M1)e and g). Finally, the SO$_2$ and SO emissions is elongated up to $\sim$1$\ensuremath{''}$ ($\sim$3000 au) along the outflow axis (Figs. [2](#fig:M0M1)i and [2](#fig:M0M1)k).

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Lines used$^{(b)}$ | N$^{(c)}$ | T$_{ex}$$^{(c)}$ | log(N/N(H$_2$))$^{(d)}$ | log(N$_{\rm H_2})$ |
|  | $\times$10$^{15}$ cm$^{-2}$ | K | log cm$^{-2}$ | log cm$^{-2}$ |
| CH$_3$CN $\varv_8=1$ $J$ = 12-11 $K$ = -5 to 8 | 5$\pm$0.2 | 333$\pm$21 | -8.7$\pm$1.1 | 24.4$\pm$1.1 |
| CH$_3$CN $\varv=0$ $J$ = 12-11 $K$ = 4 to 9 | 4$\pm$0.1 | 327$\pm$19 | -8.7$\pm$1.1 | 24.3$\pm$1.1 |
| CH$_3$OH $\varv_t=0$ 8$_{0,8}$-7$_{1,6}$ E | 500$\pm$80 | 285$\pm$15 | -7.3$\pm$1.0 | 26.4$\pm$1.0 |
| CH$_3$CN $\varv=0$ $J$ = 12-11 $K$ = 0 to 3 | 6$\pm$0.3 | 248$\pm$10 | -8.7$\pm$1.1 | 24.5$\pm$1.1 |

Table notes: $^{a}$For a position $\sim$0.05$''$ to the SW of MM1a, see Sect. [3.2](#ResLines). $^{(b)}$Throughout the paper we use the nomenclature of the JPL catalogue. $^{(c)}$Determined using the *SLIM* task of the MADCUBA package by simultaneously fitting multiple transitions of CH$_3$CN $\varv_8=1$ (the whole spectrum), CH$_3$CN $\varv=0$ (low and high-K transition fitted separately), and CH$_3$OH (including the weaker transitions 25$_{3,22}$-24$_{4,20}$ and 23$_{5,19}$-22$_{6,17}$) under the assumption of local thermodynamic equilibrium; the fitting process directly adjusts T$_{ex}$ and N to reproduce the observed line intensities and their ratios, without assuming a prior relation between T$_{ex}$ and the column density.

$^{(d)}$The abundances are calculated from the average column densities reported in (cite: Gieser2021).

To estimate the physical parameters traced by different molecular lines, we selected an area of the size of the synthesised beam ($\sim$30 mas) shifted by $\sim$0.05$''$ to the SW of the continuum peak, as the fit towards the continuum peak turned out to be complicated by the presence of multiple kinematic components at this position. Then for each data cube we extracted spectra integrated over the selected area with the Spectral Profile plotting tool of the CASA image viewer. The spectra were fitted using the SLIM tool of MADCUBA. We fitted all 14 lines of CH$_3$CN $\varv_8=1$ simultaneously, while low ($K$ = 0 to 3) and high-$K$ ($K$ = 4 to 9) CH$_3$CN $\varv=0$ transition were fitted separately to take into account the variation of excitation temperatures with $K$ since they trace different environments (Fig. [2](#fig:M0M1)c vs [2](#fig:M0M1)g). The CH$_3$OH $\varv_t=0$ 8$_{0,8}$-7$_{1,6}$ E transition was fit together with two weaker CH$_3$OH $\varv_t=0$ lines, 25$_{3,22}$-24$_{4,20}$ and 23$_{5,19}$-22$_{6,17}$ (however, as these two lines are weak, we do not use them in imaging). We note that we could fit only those molecular species for which there was more than one line in the spectrum, a condition necessary to derive excitation temperature and column density estimates (only single lines were detected for SO and SO$_2$). Physical parameters for the fitted molecular species are presented in Table [\[tab:l-param\]](#tab:l-param). To estimate the physical conditions of the gas, we employed the SLIM task of the MADCUBA package and not the rotational diagram method, since the latter assumes optically thin emission and a single excitation temperature. In contrast, SLIM performs a non-linear fit to the observed spectra, accounting for line opacity, beam dilution, and line blending effects, thereby offering a more reliable characterisation of the molecular excitation conditions.

Comparison of the parameters obtained for different molecular lines (Table [\[tab:l-param\]](#tab:l-param)) shows that compact CH$_3$CN $\varv_8=1$ and $\varv=0$ $K$ = 4 to 9 emissions trace a slightly hotter gas (T$_{ex}$$\approx$330 K) located deeper in the core. While, as expected for gas located at greater separation from the central source, CH$_3$OH and CH$_3$CN $\varv=0$ $K$ = 0 to 3 transitions indicate slightly lower temperatures (T$_{ex}$$\approx$250 K). The column density estimates derived for the CH$_3$CN and CH$_3$OH molecules are consistent, within the uncertainties, with the mean column densities reported in the CORE survey of high-mass star-forming regions by (cite: Gieser2021). Thus, the physical and chemical conditions in our target region align well with those observed in a broader sample of high-mass star-forming environments. To estimate the H$_2$ column densities, we compared our estimated column densities of CH$_3$CN and CH$_3$OH listed in Table [\[tab:l-param\]](#tab:l-param) with the abundances of these molecules calculated based on the typical column densities presented in Fig. 8 of (cite: Gieser2021). The obtained values of $\sim$10$^{24}$ cm$^{-2}$ from CH$_3$CN and $\sim$10$^{26}$ cm$^{-2}$ from CH$_3$OH are higher than that based on the flux density of the 1.3 mm continuum. This finding might be explained by considering the different regions traced by molecular gas with respect to the dust continuum. Concentration of dust closer to the central source with gas being driven to larger radii is a predicted feature of accretion disks in both low-mass (for example, (cite: Perez2012; Vorobyov2018)) and high-mass (for example, (cite: Seifried2011)) protostars, and was first noted for the disk in G11.92-0.61 MM1 by (cite: Ilee2016). Additionally, the larger H$_2$ column density calculated for CH$_3$OH likely reflects the fact that the CH$_3$OH gas occupies a larger region (and thus a larger ‘column’ of gas) than CH$_3$CN.

All velocity field maps (Figs. [2](#fig:M0M1)b, [2](#fig:M0M1)d, [2](#fig:M0M1)f, [2](#fig:M0M1)h, [2](#fig:M0M1)j, and [2](#fig:M0M1)l) show a clear velocity gradient within the dust continuum region around MM1a consistent with rotation around the source and supporting the presence of a disk as previously proposed by (cite: Ilee2016; Ilee2018). In addition to the disk, all the lines also trace gas in the outflow direction (indicated by red and blue arrows in Fig. [2](#fig:M0M1)), albeit to different extents. ‘Strings’ of emission coming from MM1a to the east, west, and south, seemingly outlining an outflow cavity, are clearly seen in the SO$_2$ $\varv=0$ map (Fig. [2](#fig:M0M1)k), and can also be distinguished in all other lines.

Remarkably, the velocity field maps (Figs. [2](#fig:M0M1)b, [2](#fig:M0M1)d, [2](#fig:M0M1)f, [2](#fig:M0M1)h, [2](#fig:M0M1)j, and [2](#fig:M0M1)l) at all the probed scales also suggest the presence of rotation around the direction approximately perpendicular to the major axis of the continuum source (in other words, around the outflow axis; red and blue arrows in Fig. [2](#fig:M0M1)), with redshifted velocities to the south-east and blueshifted velocities to the north-west. The presence of a clear transversal V$_{\rm LSR}$ gradient at all positions suggests the existence of a large-scale rotation along the outflow. One more surprising feature of the velocity field maps is the presence of a velocity spike in the SO Moment 1 map (see the dotted black circle in Fig. [2](#fig:M0M1)l). In contrast to all other imaged molecular lines, in the SO moment 1 map, a region with the reddest and bluest velocities is found not at the position of MM1a but at a separation of $\sim$0.3$''$ ($\sim$1000 au) to the NE of it.

|  |  |  |
|:--:|:--:|:--:|
| ![image](M0-CH3CNv8-2+Cont.pdf) | ![image](M0-CH3CN7+Cont.pdf) | ![image](M0-CH3OH+Cont.pdf) |
| ![image](M1-CH3CNv8-2+Cont.pdf) | ![image](M1-CH3CN7+Cont.pdf) | ![image](M1-CH3OH+Cont.pdf) |
| ![image](M0-CH3CNv0-3+Cont.pdf) | ![image](M0-SO2+Cont.pdf) | ![image](M0-SO+Cont.pdf) |
| ![image](M1-CH3CNv0-3+Cont.pdf) | ![image](M1-SO2+Cont.pdf) | ![image](M1-SO+Cont.pdf) |

## Position-velocity diagrams

We analysed the velocity profile along the disk plane (along the major axis of the continuum emission with PA $\simeq$ 130$^{\circ}$) using the PV diagrams presented in Fig. [3](#fig:pv). Three lines were selected to be representative of the three identified emission scales: CH$_3$CN $\varv=0$ $K$=7 for the compact scale, CH$_3$OH for the intermediate, and SO for the large-scale emission.

While all three selected tracers show similar symmetrical double-peaked profiles, they probe different extents and kinematics of the disk. The CH$_3$CN profile has the steepest velocity gradient and seems to deviate from the Keplerian profile at larger radii from the central star. The CH$_3$OH and SO emissions trace larger radii than the CH$_3$CN line, and their profiles appear to be Keplerian-like over the whole radial extent.

|  |  |  |
|:--:|:--:|:--:|
| ![image](PV_CH3CNv0-12_7-11_7_disk_new.pdf) | ![image](PV_CH3OH-8_0-7_1_220078_disk_new.pdf) | ![image](PV_SO_219949_disk_new.pdf) |
| \(a\) | \(b\) | \(c\) |

## Keplerian disk approximation

To further analyse the distribution and kinematics of the compact molecular emission in the vicinity of MM1a (in other words, the emission associated with the rotating disk), we fitted with a 2D Gaussian the emission peaks in each channel of the data cubes of six spectral lines: CH$_3$CN $\varv_8=1$ $J$ = 12$-$11 $K$ = -2 and 2; CH$_3$CN $\varv=0$ $J$ = 12$-$11 $K$ = 4, 7, and 8; and CH$_3$OH $\varv_t=0$ 8$_{0,8}$-7$_{1,6}$ E. This method was previously used in, for example, (cite: Moscadelli2019). The fitted transitions were selected based on their (1) compactness (the emission should have a defined peak), (2) isolation in the spectrum (heavily blended lines were excluded from the analysis), (3) intensity (peak flux density above 5$\sigma$). This approach allows us to locate the molecular emission with a high positional accuracy. The resulting combined peak map is presented in Fig. [4](#fig:spot) (note that in order to avoid overcrowding of the map, we excluded CH$_3$CN $\varv_8=1$ $J$ = 12$-$11 $K$ = 2 and CH$_3$CN $\varv=0$ $J$ = 12$-$11 $K$ = 8 as they closely follow the distribution of CH$_3$CN $\varv_8=1$ $K$ = -2 and CH$_3$CN $\varv=0$ $K$ = 7, respectively).

![](G11_Spot_map.pdf)

Independently of the tracer, all emission peaks follow the same pattern with blueshifted velocities to the north-west and redshifted velocities to the south-east (Fig. [4](#fig:spot)). The peaks with extreme (bluest and reddest) velocities (V$_{\rm LSR}$=$\sim$25-30 and 39-47 km s$^{-1}$, respectively) are spread along a line parallel and close to the major axis of the continuum source underlining a clear velocity gradient.

Assuming that the obtained peak map represents a rotating disk, we can determine the mass of the central object and the geometry of the disk. To do so, we fitted the peak distribution (Fig. [4](#fig:spot)) with two models: (1) a linear Keplerian model that takes into account only high velocity blue- and redshifted peaks (V$_{\rm LSR}$=$\sim$25-30 and 39-47 km s$^{-1}$) that draw a linear structure at the position of MM1, (2) a planar Keplerian model (cite: Sanchez2013) that fits all peaks and provides, in particular, an estimate of the inclination angle of the disk.

The linear Keplerian fit is illustrated in Fig. [5](#fig:Kep-lin), which shows the V$_{\rm LSR}$ of the emission peaks from Fig. [4](#fig:spot) versus the corresponding offsets projected along the disk major axis (along PA=130$^{\circ}$). The offset position of the central source along the X-axis ($X_0$), the systemic velocity (V$_{\rm star}$), and central source mass (M) were the free parameters of the linear Keplerian fit, whose result is reported in Table [1](#tab:disk). The linear Keplerian fit provides a position of the central source slightly offset by 0.03$''$ from the position of the continuum peak that we used as the reference and V$_{\rm star}$=34.5 km s$^{-1}$. The fitted mass of the central source is $\sim$15 $M_{\odot}$ without consideration of the disk inclination angle.

|                                               |     |
|:---------------------------------------------:|:---:|
| ![image](linear_Kepler_modi_All-lines_K4.pdf) |     |

The free parameters of the planar Keplerian fit were: the position of the central source on the plane of the sky ($X_0$, $Y_0$), the central velocity (V$_{\rm star}$), the PA of the disk projection on the plane of the sky (PA), the inclination ($\theta$) of the disk rotation axis with respect to the plane of the sky, and the central source mass (M). Interestingly, if we use only the emission peaks that make up the inner ellipse around MM1a (all lines excluding the more extended emission of CH$_3$CN $\varv=0$ $J$ = 12-11 $K$ = 4 and CH$_3$OH), we obtain an inconsistent fit with the linear distribution of high-velocity spots offset from the disk’s major axis and a large disk inclination of $\sim$56$^{\circ}$. Inclusion of the more extended CH$_3$CN $\varv=0$ $K$ = 4 and CH$_3$OH data, yield the fit in Fig. [6](#fig:Kep) where the modelled velocity field (sectors of different colour) corresponds well to the data. The best-fit parameters are given in Table $\ref{tab:disk}$. We have ascertained that the inconsistent planar Keplerian fit obtained by employing only the CH$_3$CN data (excluding $\varv=0$ $K$ = 4) is due to the mid-velocity spots (V$_{\rm LSR}$ = 30-39 km s$^{-1}$) spreading out of the disk mid-plane (see Fig. [4](#fig:spot)). Their kinematics is inconsistent with Keplerian rotation around the same central mass as traced by the linear distribution of the corresponding high-velocity (V$_{\rm LSR}$ $<$30 km s$^{-1}$ and $>$39 km s$^{-1}$) spots. From the Keplerian planar fit, we obtained the best-fit mass of the central source of $\sim$20 $M_{\odot}$, which is in good agreement with the result of the linear Keplerian fit corrected for a best-fit disk inclination of $\sim$30$^{\circ}$. Thus, the two approaches provide similar results, confirming the presence of a slightly inclined, rotating disk around MM1a.

![](kep_fit_model_All-lines_K4.pdf)

+:-------------------:+:-------------------:+:--------------:+:----------------:+:------------:+:-------------:+
| X$_0$               | Y$_0$               | V$_{\rm star}$ | $\theta$$^{(a)}$ | PA           | M             |
+---------------------+---------------------+----------------+------------------+--------------+---------------+
| ($\ensuremath{''}$) | ($\ensuremath{''}$) | (km s$^{-1}$)  | ($^{\circ}$)     | ($^{\circ}$) | ($M_{\odot}$) |
+---------------------+---------------------+----------------+------------------+--------------+---------------+
| Linear Keplerian fit                                                                                         |
+---------------------+---------------------+----------------+------------------+--------------+---------------+
| 0.03$^{(b)}$        | \-                  | 34.5           | \-               | \-$^{(c)}$   | 15$^{(d)}$    |
+---------------------+---------------------+----------------+------------------+--------------+---------------+
| Planar Keplerian fit                                                                                         |
+---------------------+---------------------+----------------+------------------+--------------+---------------+
| 0.01                | -0.03               | 34.5           | 32               | 130          | 20            |
+---------------------+---------------------+----------------+------------------+--------------+---------------+

: Fitted parameters of the disk.

Table notes: $^{(a)}$Inclination, i.e. the angle between the disk axis and the plane of the sky. $^{(b)}$Offset along the PV cut. $^{(c)}$Was set to 130$^{\circ}$ in accordance with the PA of the continuum source. $^{(d)}$Not corrected for the disk inclination.

\

# Discussion

## Disk and central mass

Previous observations of G11.92-0.61 MM1a had revealed the presence of a massive protostar surrounded by an accretion disk; however, the exact parameters of this system remained a subject of debate. Our new high-resolution, multi-line ALMA data provided the insights needed to resolve these uncertainties and offer a more precise estimate of the characteristics of the central object and its disk.

The work of (cite: Ilee2016) suggested the presence of an infalling Keplerian disk with a radius of 1200 au and an inclination of $\sim$55-38$^{\circ}$[^4]. rotating around an enclosed mass of $\sim$30-60 $M_{\odot}$ based on multi-line data obtained with the SMA and *Karl G. Jansky* Very Large Array (VLA). Later ALMA observations of CH$_3$CN emission at a higher angular resolution indicated slightly different parameters of $\sim$40 $M_{\odot}$ for the central mass, and a disk inclination of $\sim$20$^{\circ}$ (cite: Ilee2018). However, these discrepancies appear to be mostly dependent on the choice of tracers rather than on the resolution of the observations. Similar to our analysis, (cite: Ilee2016) also noticed that the Keplerian approximation depends on whether methanol is included or not in the input dataset. In (cite: Ilee2016), inclusion of the CH$_3$OH data provided a central mass of $\sim$35 $M_{\odot}$ and a disk inclination of $\sim$38$^{\circ}$, while exclusion of the CH$_3$OH yielded $\sim$60 $M_{\odot}$ and $\sim$55$^{\circ}$. The Keplerian fit of our data provided a central mass of $\sim$20 $M_{\odot}$ and disk inclination $\sim$32$^{\circ}$ with CH$_3$OH and $\sim$35 $M_{\odot}$ and disk inclination $\sim$55$^{\circ}$ without it (see Sect. [3.4](#Kep)). Overall, these estimates suggest two scenarios: (1) a more massive protostar with a more inclined disk, or (2) a less massive protostar with a less inclined disk.

While (cite: Ilee2016) could not discriminate between the two possibilities and confined the mass in the range $\sim$35-60 $M_{\odot}$, we argue that inclusion of the CH$_3$OH data provides a more accurate approximation of the disk geometry, and in particular the disk inclination as CH$_3$OH traces large radii of the disk (Fig. [4](#fig:spot)). The high-excitation energy CH$_3$CN emissions ($\varv_8=1$ and $\varv=0$ $K$=7 to 8) at mid-velocities (30-39 km s$^{-1}$) deviate from Keplerian rotation at disk radii of $>$0.1$''$ ($>$300 au) according to our Keplerian fits as discussed in Sect. 3.4. Figures [4](#fig:spot) and [6](#fig:Kep) show that the mid-velocity emissions of high-excitation CH$_3$CN and the CH$_3$OH lines draw two ‘rings’ around the central protostar, and that of CH$_3$CN is significantly smaller (de-projected diameter of $\sim$400-500 au) than that of CH$_3$OH (1200-1500 au). According to Fig. [5](#fig:Kep-lin), the mid-velocity (30-39 km s$^{-1}$) spots of CH$_3$CN, (tracing the smaller ring in Fig. [6](#fig:Kep)) have line-of-sight velocities closer to V$_{\rm star}$ than expected from the Keplerian profile at the corresponding radius; the high-excitation CH$_3$CN emission is thus tracing sub-Keplerian rotation at these positions. Deviations from Keplerian rotation within the disk (at the radii of $>$300 au in our case) can be due, for example, to magnetic fields (for example, (cite: Seifried2011)), while the radius at which Keplerian rotation dominates may vary depending on the magnetic field strength and age of the system (for example, (cite: Seifried2011; Kuiper2011)).

For instance, for the protostar G23.01-00.41 with a mass comparable to MM1a, ALMA observations of (cite: Sanna2019) showed that sub-Keplerian rotation dominates the accretion disk at radii between 500 and 2000 au with strong infall signatures, whereas centrifugal equilibrium might be reached in the innermost regions only. Notably, because of the higher angular resolution with respect to (cite: Sanna2019), here we are also able to probe the rotation curve where gas approaches centrifugal equilibrium near the protostar. We can also glean interesting insights by comparing G11.92-0.61 MM1a to an object at an earlier stage of evolution. The molecular line study by (cite: Miyawaki2022) of the hot molecular core W49N MCN-a provided a compelling example of the transition from a massive, gravitationally unstable envelope to a Keplerian-like disk. Similar to our findings for G11.92-0.61 MM1a, (cite: Miyawaki2022) demonstrate that the choice of molecular tracers significantly impacts the interpretation of rotation curves and the inferred disk parameters. In both sources, distinct radial regions with differing velocity gradients were identified using different molecular lines. However, in contrast to G11.92-0.61 MM1a, W49N MCN-a remains dominated by a massive, gravitationally unstable envelope. This distinction likely reflects the differing evolutionary stages of the two systems.

Summarising the results obtained for the G11.92-0.61 MM1a system, we confirm the presence of a dust disk traced by the 1.3 mm continuum emission and having a diameter $\sim$0.16$''$ ($\sim$500 au) and PA $\sim$130$^{\circ}$ (Fig. [1](#fig:cont)). Molecular emission of high-excitation CH$_3$CN $\varv_8=1$ and $\varv=0$ $K$=7 to 8, trace two distinct regions of the disk: (1) high-velocity emissions trace the inner $<$300 au radii of the disk, which are dominated by Keplerian rotation; and (2) mid-velocity emission at larger disk radii from $>$300 au traces rotation in a sub-Keplerian regime. Overall, the disk is found to be close to edge-on with inclination of $\sim$30$^{\circ}$. The mass of the central object is determined to be $\sim$20 $M_{\odot}$, which agrees with the luminosity of the source of $\sim$10$^4$ L$_{\rm sun}$ (cite: Cyganowski2011; Moscadelli2016; Ilee2018) better than the higher mass estimates obtained in previous studies.

## Kinematic profiles of the molecular outflow

|  |  |
|:--:|:--:|
| ![image](G11_Offset-NE-SOvsSO2-au-NEW.pdf) | ![image](G11_Offset-SW-SOvsSO2-au_New.pdf) |
| ![image](G11_Rmed-NE-SOvsSO2-New.pdf) | ![image](G11_Rmed-SW-SOvsSO2-New.pdf) |
| ![image](G11_MedianVel-NE-SOvsSO2-New.pdf) | ![image](G11_MedianVel-SW-SOvsSO2-New.pdf) |
| ![image](G11_VelRot-NE-SOvsSO2-New.pdf) | ![image](G11_VelRot-SW-SOvsSO2-New.pdf) |
| ![image](G11_AngMom-NE-SOvsSO2-New.pdf) | ![image](G11_AngMom-SW-SOvsSO2-New.pdf) |

Another insight into the structure of the source is provided by the low-flux-density 1.3 mm continuum emission, which shows excess emission to the SW of the continuum peak (Fig. [1](#fig:cont)), with two distinct spurs to the eastern and western sides. Notably these spurs of emission pointing to the SW from the continuum peak in our image are roughly symmetrical to the NE excess in the lower resolution image by (cite: Ilee2018) at the same wavelength. Now comparing the 1.3 mm continuum images from this work and from (cite: Ilee2018) to the molecular line data in Figs. [2](#fig:M0M1)i and [2](#fig:M0M1)k, we see that the SW 1.3 mm emission correlates well with the strings of SO$_2$ and SO emission propagating to the NE and SW from the central source and tracing outflow motions. Thus, we can infer that the 1.3 mm continuum emission traces not only the disk but also the base of the outflow cavities. And more precisely it traces the dust in the disk and inner flow cavities, as the analysis of the spectral energy distribution from (cite: Ilee2016) demonstrated that the 1.3 mm continuum emission is dominated by thermal dust emission.

All available observations of G11.92-0.61 MM1a indicate the presence of an X-shaped structure parallel to the large-scale outflow and perpendicular to the disk. Besides dust continuum, the structure is clearly seen in our SO$_2$ image (Figs. [2](#fig:M0M1)i-j). It identified in all other detected lines (Fig. [2](#fig:M0M1)), as well as in the molecular line data from (cite: Ilee2016). The X-structure could be associated with accretion of material rather than with ejection, that is to say, it could be streamers driving material from the envelope towards the disk, similar to, for example, the case discussed in (cite: Goddi2020) for the high-mass star-forming complex W51. However, we discard this possibility as the detected structure is clearly aligned with the large-scale outflow and is clearly seen in outflow tracers (SO$_2$ and SO lines). Additionally, the velocity field maps in Fig. [2](#fig:M0M1) hint at an increase in the velocity along the outflow with increased separation from the central protostar, while in the case of streamers, we would expect higher-velocities as the matter approaches the disk. Thus, we tend to interpret this structure as outflowing gas along the outflow cavity. Moreover, the clear velocity gradient seen in all molecular tracers suggests the presence of rotation of the outflowing gas around the outflow axis.

Assuming that both SO$_2$ and SO emissions trace the walls of the rotating outflow cavities for each of the two outflow lobes, we can try to quantify the outflow properties by examining the kinematic profiles of the molecular emission at different separations from the central source, following the methods that have proven to be effective for low-mass protostars (for example, (cite: Zhang2018)). Using the SO$_2$ and SO data, we prepared sets of the PV diagrams for several cuts perpendicular to the outflow axis (z-axis) along the NE and SW lobes (see Figs. [10](#fig:pvsone)-[13](#fig:pvso2sw)). Following our model, we presume that in each PV diagram, the peaks of emission in the ‘red’ (redshifted velocities and positive offsets) and ‘blue’ (blueshifted velocities and negative offsets) part of a diagram correspond to opposite cavity walls of a particular outflow lobe. For these two peaks, we measure the offsets from the central source position (R$_{\rm red}$ and R$_{\rm blue}$) and corresponding local standard of rest velocity (V$_{\rm red}$ and V$_{\rm blue}$). Usage of the lower-resolution data (0.15$''$ synthesised beam) allowed us to better determine the peaks of the PV diagrams. In accordance with the chosen spatial resolution, the step for the cuts was set to 0.15$''$ ($\sim$500 au). For each cut, the radius of the outflow was calculated as R$_{\rm out}$ = (R$_{\rm red}$ $-$ R$_{\rm blue}$)/2 (Fig. [7](#fig:outf-param)a,b), while R$_{\rm med}$ = (R$_{\rm red}$ + R$_{\rm blue}$)/2 is an estimate of the distance between the cavity walls and the outflow axis (Fig. [7](#fig:outf-param)c,d). The median velocity was estimated as the average of the velocities V$_{\rm med}$ = (V$_{\rm red}$ + V$_{\rm blue}$)/2 (Fig. [7](#fig:outf-param)e,f) and the rotation velocity was computed as V$_{\rm rot}$ = (V$_{\rm red}$ $-$ V$_{\rm blue}$)/2 (Fig. [7](#fig:outf-param)g,h). We also calculated the specific angular momentum j as R$_{\rm out}$V$_{\rm rot}$ (Fig. [7](#fig:outf-param)i,j). Our errors on the offset and velocity were determined by the spatial (0.15$''$ or 500 au) and spectral (0.35 km s$^{-1}$) resolution, respectively.

Figure [7](#fig:outf-param) shows the parameters of the outflow that we obtained for the NE (left panels) and SW (right panels) lobes using SO (black circle markers) and SO$_2$ (red square markers) data. The NE lobe turned out to be 1.5 times wider than the SW lobe, with the maximum R$_{\rm out}$ for the NE lobe being $\sim$1400 au, while the emission from the SW lobe has a maximum R$_{\rm out}$ of $\sim$930 au (Fig. [7](#fig:outf-param)a,b). A linear fit to the R$_{\rm out}$ data provides us with an estimate of the outflow launching radius (R$_0$), which is $\sim$260 au for the NE lobe, and $\sim$340 au for the SW lobe. The relatively small values of R$_{\rm med}$ with respect to R$_{\rm out}$ indicate that the cavity wall is approximately centred on the outflow axis (Fig. [7](#fig:outf-param)c,d). SO and SO$_2$ data for both lobes revealed the same median value of the velocity V$_{\rm med}$ = 34.4$\pm$0.5 km s$^{-1}$ (grey line in Fig. [7](#fig:outf-param)e and [7](#fig:outf-param)f), which agrees well with the V$_{\rm star}$ estimated from the Keplerian fits (see Table [1](#tab:disk)). Such a good agreement also suggests that the inclination of the outflow is small. The rotation velocity (V$_{\rm rot}$) shows a decreasing trend with separation from the central source for both the NE and SW lobes (see the dashed line in Fig. [7](#fig:outf-param)g,h). We note that we excluded from the fits the values of V$_{\rm rot}$ (1) obtained for the cut at $\sim$500 au along the NE lobe as the difference between SO and SO$_2$ data points is significant ($\sim$4 km s$^{-1}$) and it seems to indicate that this region closest to the central source is too turbulent or shielded by the dust, and (2) obtained for the cut at $\sim$2500 au along the SW lobe as it seems to reflect a different kinematics in the tail of the outflow. For the NE lobe, V$_{\rm rot}$ changes from $\sim$5 km s$^{-1}$ at z =$\sim$1000 au to $\sim$3.4 km s$^{-1}$ at z = $\sim$2500 au; thus, the difference is 1.6 km s$^{-1}$ over 1500 au. In the SW lobe, V$_{\rm rot}$ ranges from 3.3 km s$^{-1}$ at z = $\sim$500 au to 2 km s$^{-1}$ at z = $\sim$2000 au, with a variation of 1.3 km s$^{-1}$ over 1500 au, which is very similar to the numbers obtained for the NE lobe. Considering the increasing R$_{\rm out}$ of the outflow (Figs. [7](#fig:outf-param)a and [7](#fig:outf-param)b) and decreasing V$_{\rm rot}$ for the cuts that produced reliable estimates, we obtain a distribution of the specific angular momentum (see Figs. [7](#fig:outf-param)i and [7](#fig:outf-param)j) that hints at conservation of this quantity along the flow. In particular, in the NE lobe, the mean of the specific angular momentum is $\sim$4500$\pm$690 au km s$^{-1}$. For the SW lobe, the mean specific angular momentum is $\sim$1600$\pm$200 au km s$^{-1}$.

The observed conservation of specific angular momentum indicates the presence of differential rotation along the outflow. Such a behaviour is consistent with the expected dynamics of a MHD disk-wind, where streams of gas, emerge from the disk and co-rotate with their launching points along the poloidal magnetic field lines. Since SO and SO$_2$ emissions are known to trace denser regions of the outflow, we assume that we detect the rotation of the denser, inner portions of the outflow linked to the disk-wind, rather than the broader, more diffuse outflow cavity.

## Disk-wind evidence

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| ![image](PV_CH3CNv0-12_3-11_3_VS_new.pdf) | ![image](PV_CH3OH-8_0-7_1_220078_VS_new.pdf) | ![image](PV_SO2v0-11-10_221965_VS_new.pdf) | ![image](PV_SO_219949_VS_new.pdf) |
| \(a\) | \(b\) | \(c\) | \(d\) |

There is another particular feature of the SO image that leads us to believe in the presence of a disk-wind in the source. The velocity field imaged with the SO molecular line data shows a velocity spike at a $\sim$0.3$''$ ($\sim$1000 au) separation to the NE of the central source (see the dashed black circle in Fig. [2](#fig:M0M1)l). To analyse the behaviour of the gas in this region, we present PV diagrams for a slice centred on the position of the velocity spike with PA = 130$^{\circ}$ for the tracers of extended emission (CH$_3$CN $\varv=0$ $K$=3, CH$_3$OH, SO$_2$, and SO; see Fig. [8](#fig:pvspur)). At the position of the velocity spike, mildly extended emission of CH$_3$CN $\varv=0$ as well as CH$_3$OH (for example, Figs. [8](#fig:pvspur)a and [8](#fig:pvspur)b) can be interpreted as tracing a ring structure with only the highest-velocity emission showing a hint of Keplerian rotation. In contrast, the SO$_2$ and SO profiles are consistent with Keplerian patterns (Figs. [8](#fig:pvspur)c and [8](#fig:pvspur)d) indicating Keplerian rotation of the matter at such a large distance from the central source as $\sim$1000 au. We note that the distribution of the SO emission (see the moment 0 map in Fig. [2](#fig:M0M1)k) suggests that the vicinity of the central source is opaque in this line while the velocity spike position is more optically thin and allows us to directly see this feature.

Fitting of the PV diagram for the SO emission at the velocity spike position using the KeplerFit script from (cite: Bosco2019) returned a central source mass of 15 $M_{\odot}$; this is consistent with what obtained from the disk analysis (see Table [1](#tab:disk)), suggesting a common origin. The characteristics of the SO$_2$ and SO emission can be explained assuming they trace a disk-wind in the source. Considering a disk in Keplerian rotation, we expect the streams of the disk-wind with the highest velocities to be launched from the smallest radii; thus, the velocity spike seen in the SO Moment 1 map traces the gas coming from the innermost disk regions.

As mentioned in the introduction, one of the distinguishing parameters between the X-wind and disk-wind models is the position of the launching point within the disk: $<$0.1 au for X-wind (cite: Shu1995) and tens of au for disk-wind (cite: Pudritz2007). Thus, if we want to test which of the two theories better fits our data, we need to determine the launching radius (R$_0$). For this purpose, we adopted the approach presented in (cite: Lee2017), where the jet launching radius is constrained by the specific angular momentum of the jet (j), jet expansion velocity, and mass of the central object (M). We use our estimate of the mean specific angular momentum of $\sim$4500 au km s$^{-1}$ for the NE lobe and of $\sim$1600 au km s$^{-1}$ for the SW lobe, as well as the mass of the protostar 15 $M_{\odot}$ (without correcting for the inclination as we did not consider it in the calculations of the angular momentum). The only parameter that we have not evaluated directly with our data is the outflow velocity. We can assume a reasonable value of $\sim$30 km s$^{-1}$ based on the 22 GHz water maser proper motions estimated in (cite: Moscadelli2019). Using these estimates, we get R$_0$ $\sim$50 au for the SW lobe and $\sim$100 au for the NE lobe. Since the water masers typically occur in the regions where outflowing gas collides with the ambient material and thus slows down, we can expect that the real velocity of the outflow is even higher. To take into account this possibility, we recalculated R$_0$ using the same parameters but an outflow velocity of $\sim$100 km s$^{-1}$. We get $\sim$10 au for the SW lobe and $\sim$20 au for the NE lobe. These estimates are not consistent with the X-wind model, which requires much smaller radii, of a fraction of a au.

|                        |     |
|:----------------------:|:---:|
| ![image](G11_plot.pdf) |     |

A quantity of interest in disk-wind models is the magnetic lever arm $\lambda$=R$^2_A$/R$^2_0$. Here R$_A$ is the Alfvén radius (the radius where magnetic energy density and the kinetic energy density of the outflowing material are comparable) and R$_0$ is the radius at which the field line is anchored to the disk that we previously estimated. To evaluate the magnetic lever arm for our case, we used Eq. (10) from (cite: Ferreira2006) and the estimated values of the specific angular momentum, outflow propagation velocity, and protostar mass. For a velocity of the outflow of $\sim$30 km s$^{-1}$, we obtain $\lambda$ of $\sim$2.4 and $\sim$4, and R$_A$ of $\sim$80 and $\sim$200 for the SW and NE lobe, respectively. Such $\lambda$ are in good agreement with the typical values (between 2-10) expected for disk-winds in massive protostars.

Finally, the image in Fig. [9](#fig:masers), combining the SO, SO$_2$, and 1.3 mm continuum emission obtained in this work, as well as the 22 GHz water masers from (cite: Moscadelli2019), shows that all the outflow tracers originate from a common large rotating structure but at different scales. Figure [9](#fig:masers) confirms that the proper motions of the 22 GHz water masers correlate well with the velocity field of the molecular data, suggesting that each of the maser groups co-propagates with the outflow material. As we mentioned above, in the case of massive protostars, high-resolution and high-sensitivity observations of masers are required to resolve the launching region of a disk-wind and confirm its nature. In G11.92-0.61 MM1a, the 22 GHz water masers trace the launching base of the outflow but, unfortunately, not the streamlines of a disk-wind. In conclusion, G11.92-0.61 MM1a seems to be a unique example of a massive protostar in which bright molecular outflow emission (1) reveals clear signs of rotation over $\sim$3400 au from the central source, and (2) shows strong indications for the presence of a disk-wind launched from small radii ($\sim$50-100 au) of the disk. Our study demonstrates that high-resolution molecular line data can suffice to reveal disk-winds in massive protostars.

# Conclusions

We have carried out an ALMA Band 6 observation of the massive protostar G11.92-0.61 MM1. The main results can be summarised as follows:

1.  We confirm the existence of a disk around the source MM1a. The estimate of the disk diameter depends on the tracer, ranging from 500 au in the millimetre continuum to 700 au in the CH$_3$CN and CH$_3$OH lines.

2.  The molecular line data reveal the presence of two distinct velocity fields within the disk: (1) Keplerian rotation at radii of $<$300 au, traced by high-velocity CH$_3$CN emission, and (2) sub-Keplerian rotation at larger disk radii, $>$300 au, traced by mid-velocity CH$_3$CN emission.

3.  Keplerian fitting of the molecular data associated with the disk gives a central source mass of 20 $M_{\odot}$, which is about two times lower than the previous estimates for MM1a and is consistent with the source luminosity of $\sim$10$^4$ L$_{\rm sun}$.

4.  The source MM1b appears to be a distinct source rather than a disk fragment as no molecular emission associated with MM1b and no connection between MM1a and MM1b are detected.

5.  A strong collimated SO$_2$ and SO outflow from MM1a is probed up to $\sim$3400 au from MM1a.

6.  The observed velocity pattern of the SO$_2$ and SO emission indicates that the outflow is rotating about its axis. A decrease in the rotation velocity of $\sim$1.5 km s$^{-1}$ over $\sim$1500 au is found in both lobes of the outflow. Along the lobes, the specific angular momentum is approximately constant: $\sim$4720 au km s$^{-1}$ for the NE lobe and $\sim$1420 au km s$^{-1}$ for the SW lobe.

7.  The Keplerian rotation profile obtained for the molecular outflow tracers suggests magneto-centrifugal launching of the wind. Considering the estimated specific angular momentum and mass of the central object, we derive a launching radius of the outflow of $\sim$50-100 au, which is consistent with the disk-wind model, while the X-wind model requires much smaller launching radii.

8.  Comparison of the newly acquired molecular data and 22 GHz water maser proper motions indicates that the water masers trace the disk-wind interaction region.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2019.1.01639.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. O.B. acknowledges financial support from the Italian Ministry of University and Research - Project Proposal CIR01$\_$00010.

46 natexlab

(ref: Bally1983) Bally, J. & Lada, C. J. 1983, ApJ, 265, 824

(ref: Blandford1982) Blandford, R. D. & Payne, D. G. 1982, MNRAS, 199, 883

(ref: Bosco2019) Bosco, F., Beuther, H., Ahmadi, A., et al. 2019, A&A, 629, A10

(ref: Breen2011) Breen, S. L. & Ellingsen, S. P. 2011, MNRAS, 416, 178

(ref: Canto1980) Canto, J. 1980, A&A, 86, 327

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Comrie2020) Comrie, A., Pińska, A., Simmonds, R., & Taylor, A. R. 2020, Astronomy and Computing, 32, 100389

(ref: Cyganowski2009) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., & Churchwell, E. 2009, ApJ, 702, 1615

(ref: Cyganowski2011b) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., & Churchwell, E. 2011a, ApJ, 743, 56

(ref: Cyganowski2011) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., Churchwell, E., & Zhang, Q. 2011b, ApJ, 729, 124

(ref: Cyganowski2017) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2017, MNRAS, 468, 3694

(ref: Cyganowski2008) Cyganowski, C. J., Whitney, B. A., Holden, E., et al. 2008, AJ, 136, 2391

(ref: Ferreira2006) Ferreira, J., Dougados, C., & Cabrit, S. 2006, A&A, 453, 785

(ref: Frank2014) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451–474

(ref: Gieser2021) Gieser, C., Beuther, H., Semenov, D., et al. 2021, A&A, 648, A66

(ref: Goddi2020) Goddi, C., Ginsburg, A., Maud, L. T., Zhang, Q., & Zapata, L. A. 2020, ApJ, 905, 25

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hirota2017) Hirota, T., Machida, M. N., Matsushita, Y., et al. 2017, Nature Astronomy, 1, 0146

(ref: Hofner1996) Hofner, P. & Churchwell, E. 1996, A&AS, 120, 283

(ref: Ilee2018) Ilee, J. D., Cyganowski, C. J., Brogan, C. L., et al. 2018, ApJL, 869, L24

(ref: Ilee2016) Ilee, J. D., Cyganowski, C. J., Nazari, P., et al. 2016, MNRAS, 462, 4386

(ref: Kim2008) Kim, M. K., Hirota, T., Honma, M., et al. 2008, PASJ, 60, 991

(ref: Kuiper2011) Kuiper, R., Klahr, H., Beuther, H., & Henning, T. 2011, ApJ, 732, 20

(ref: Lee2017) Lee, C.-F., Ho, P. T. P., Li, Z.-Y., et al. 2017, Nature Astronomy, 1, 0152

(ref: Martin2019) Martı́n, S., Martı́n-Pintado, J., Blanco-Sánchez, C., et al. 2019, A&A, 631, A159

(ref: Matthews2010) Matthews, L. D., Greenhill, L. J., Goddi, C., et al. 2010, ApJ, 708, 80

(ref: McCaughrean1994) McCaughrean, M. J., Rayner, J. T., & Zinnecker, H. 1994, ApJL, 436, L189

(ref: Miyawaki2022) Miyawaki, R., Hayashi, M., & Hasegawa, T. 2022, PASJ, 74, 705

(ref: Moscadelli2011) Moscadelli, L., Cesaroni, R., Rioja, M. J., Dodson, R., & Reid, M. J. 2011, A&A, 526, A66

(ref: Moscadelli2016) Moscadelli, L., Sánchez-Monge, Á., Goddi, C., et al. 2016, A&A, 585, A71

(ref: Moscadelli2022) Moscadelli, L., Sanna, A., Beuther, H., Oliva, A., & Kuiper, R. 2022, Nature Astronomy, 6, 1068

(ref: Moscadelli2019) Moscadelli, L., Sanna, A., Goddi, C., et al. 2019, A&A, 631, A74

(ref: Pascucci2023) Pascucci, I., Cabrit, S., Edwards, S., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 567

(ref: Perez2012) Pérez, L. M., Carpenter, J. M., Chandler, C. J., et al. 2012, ApJL, 760, L17

(ref: Pudritz2007) Pudritz, R. E., Ouyed, R., Fendt, C., & Brandenburg, A. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 277

(ref: Sanchez2013) Sánchez-Monge, Á., Cesaroni, R., Beltrán, M. T., et al. 2013, A&A, 552, L10

(ref: Sanna2019) Sanna, A., Kölligan, A., Moscadelli, L., et al. 2019, A&A, 623, A77

(ref: Sanna2018) Sanna, A., Moscadelli, L., Goddi, C., Krishnan, V., & Massi, F. 2018, A&A, 619, A107

(ref: Sanna2012) Sanna, A., Reid, M. J., Carrasco-González, C., et al. 2012, ApJ, 745, 191

(ref: Sato2014) Sato, M., Wu, Y. W., Immer, K., et al. 2014, ApJ, 793, 72

(ref: Schuller2009) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415

(ref: Seifried2011) Seifried, D., Banerjee, R., Klessen, R. S., Duffin, D., & Pudritz, R. E. 2011, MNRAS, 417, 1054

(ref: Shu1995) Shu, F. H., Najita, J., Ostriker, E. C., & Shang, H. 1995, ApJL, 455, L155

(ref: Suriano2019) Suriano, S. S., Li, Z.-Y., Krasnopolsky, R., Suzuki, T. K., & Shang, H. 2019, MNRAS, 484, 107

(ref: Vorobyov2018) Vorobyov, E. I., Akimkin, V., Stoyanovskaya, O., Pavlyuchenkov, Y., & Liu, H. B. 2018, A&A, 614, A98

(ref: Zhang2018) Zhang, Y., Higuchi, A. E., Sakai, N., et al. 2018, ApJ, 864, 76

# Position–velocity diagrams perpendicular to the outflow axis

|  |  |  |
|:--:|:--:|:--:|
| ![image](PV-SO-NE-015.pdf) | ![image](PV-SO-NE-03.pdf) | ![image](PV-SO-NE-045.pdf) |
| ![image](PV-SO-NE-06.pdf) | ![image](PV-SO-NE-075.pdf) |  |

|  |  |  |
|:--:|:--:|:--:|
| ![image](PV-SO2-NE-015.pdf) | ![image](PV-SO2-NE-03.pdf) | ![image](PV-SO2-NE-045.pdf) |
| ![image](PV-SO2-NE-06.pdf) | ![image](PV-SO2-NE-075.pdf) |  |

|  |  |  |
|:--:|:--:|:--:|
| ![image](PV-SO-SW-015.pdf) | ![image](PV-SO-SW-03.pdf) | ![image](PV-SO-SW-045.pdf) |
| ![image](PV-SO-SW-06.pdf) | ![image](PV-SO-SW-075.pdf) |  |

|  |  |  |
|:--:|:--:|:--:|
| ![image](PV-SO2-SW-015.pdf) | ![image](PV-SO2-SW-03.pdf) | ![image](PV-SO2-SW-045.pdf) |
| ![image](PV-SO2-SW-06.pdf) | ![image](PV-SO2-SW-075.pdf) |  |

[^1]: <https://cartavis.org>

[^2]: <http://casa.nrao.edu>

[^3]: <https://www.iram.fr/IRAMFR/GILDAS>

[^4]: Note that (cite: Ilee2016; Ilee2018) and this work use different definitions of inclination angle: in (cite: Ilee2016; Ilee2018), 0$^{\circ}$ corresponds to a face on disk while, in this work, 90$^{\circ}$ corresponds to a face-on disk. Thus, we recalculated the inclinations obtained in (cite: Ilee2016; Ilee2018) to express them according to our definition

</paper>

Write the methods card for this paper.