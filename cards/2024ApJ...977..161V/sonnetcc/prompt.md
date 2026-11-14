# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977..161V\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977..161V",
 "title": "Kinematic Analysis of z = 4.3 Galaxies in the SPT2349─56 Protocluster Core",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Venkateshwaran, Aparna",
 "n_authors": 13,
 "arxiv_id": "2409.13823",
 "doi": "10.3847/1538-4357/ad7bb4",
 "alma_projects_linked_by_archive": [
  "2018.1.00058.S"
 ]
}
```

Paper text:
<paper>
# Kinematic analysis of $\mathbf{z = 4.3}$ galaxies in the SPT2349$-$56 protocluster core

## Abstract

SPT2349$-$56 is a protocluster discovered in the 2500 deg$^2$ South Pole Telescope (SPT) survey. In this paper, we study the kinematics of the galaxies found in the core of SPT2349$-$56 using high-resolution (1.55 kpc spatial resolution at $z = 4.303$) redshifted \[CII\] 158-$\ensuremath{\mu}m$ data. Using the publicly available code ^`3D`^`BAROLO`, we analyze the seven far-infrared (FIR) brightest galaxies within the protocluster core. Based on conventional definitions for the detection of rotating discs, we classify six sources to be rotating discs in an actively star-forming protocluster environment, with weighted mean $V_{\mathrm{rot}}/\sigma_{\mathrm{disp}} = 4.5 \pm 1.3$. The weighted mean rotation velocity ($V_{\mathrm{rot}}$) and velocity dispersion ($\sigma_{\mathrm{disp}}$) for the sample are $357.1 \pm 114.7$ km s$^{-1}$ and $43.5 \pm 23.5$ km s$^{-1}$, respectively. We also assess the disc stability of the galaxies and find a mean Toomre parameter of $Q_\mathrm{T} = 0.9 \pm 0.3$. The galaxies show a mild positive correlation between disc stability and dynamical support. Using the position-velocity maps, we find that five sources further classify as disturbed discs, and one classifies as a strictly rotating disc. Our sample joins several observations at similar redshift with high $V/\sigma$ values, with the exception that they are morphologically disturbed, kinematically rotating and interacting galaxies in an extreme protocluster environment.

# Introduction

Galaxy formation is thought to be driven either by ‘hot’ or ‘cold’ processes. In the former scenario, in-falling gas is shock-heated to virial temperatures, accreted spherically by the disc, and cooled over long timescales, eventually triggering star-formation that is regulated by feedback from stars or active galactic nuclei (AGN; (cite: Rees_1977; White_1978; Fall_1980; King_2015)). Theoretically, this implies an increase in turbulence within galaxies at earlier times since systems are dominated by violent disc instabilities (in other words, they are dynamically hotter at earlier epochs; (cite: Dekel_2014; Zolotov_2015; Hayward_2017; Krumholz_2018; Pillepich_2019)).

‘Cold’ processes, however, describe efficient (and possibly co-planar) gas accretion via mergers or filamentary structures in the cosmic web (cite: Keres_2005; Dekel_2006; Dekel_2009a; Dekel_2009b; Kretschmer_2022). With infrequent mergers over long time scales, this process allows relatively cold ($V/\sigma \ensuremath{\gtrsim} 4$) discs to be present across all epochs (cite: Lelli_2016; Dekel_2020a). Several observations have demonstrated the existence of rotational discs with $V/\sigma > 3$ at $z>2$ (cite: Hodge_2012; Lelli_2018; Sharda_2019; Rizzo_2020; Lelli_2021; Rizzo_2021; Fratenalli_2021), which most numerical simulations have struggled to reproduce (cite: Grand_2017; Pillepich_2019). More recently, a study using high-resolution zoom-in cosmological simulations reproduced the presence of non-transient, massive ($M_{\star} > 10^{10}$ M$_\ensuremath{\odot}$), super-cold ($V/\sigma > 10$) discs at $z \ge 4$ (cite: Pallottini_2022; Kohandel_2023). Understanding the kinematics of such galaxies across cosmic epochs allows for studying the physical processes involved in their mass accretion.

Studying the kinematics of galaxies at high redshift requires high-resolution data. At $z < 3$, the use of optical recombination and forbidden lines such as H$\alpha$, \[OIII\], and \[NII\] is common (cite: Swinbank_2009; Foerster_Schreiber_2009; Wisnioski_2015; Teodoro_2016; Turner_2017). The rotational transitions of the carbon monoxide (CO) molecule are also useful for studying disc kinematics in the innermost parts of a galaxy. However, at $z \ensuremath{\gtrsim} 3$, these lines are difficult to detect and require long integration times to reach the required sensitivities (cite: Hodge_2012; Ginolfi_2020). Improvements in adaptive optics (AO) techniques (cite: Foerster_Schreiber_2018) and in interferometric facilities (ALMA, ATCA, NOEMA, VLA, etc.) have significantly contributed towards improving the sensitivity and angular resolution required in such studies.

A commonly studied emission line in astronomy is that of singly ionized carbon ($\mathrm{C}^+$, hereafter \[CII\]). Occurring due to a transition between the fine-structure levels $\rightarrow$ , it is one of the dominant cooling lines in the cool interstellar gas (cite: De_looze_2011; Wagg_2012; Herrera_Camus_2015; Lagache_2018). \[CII\] emission traces the atomic and molecular gas across the different phases of the interstellar medium (ISM) due to its ionization potential being lower than that of neutral hydrogen (cite: Carilli_2013). For solar metallicity gas, it is also the brightest emission line from far-IR (FIR) to radio wavelengths. At $z \ensuremath{\gtrsim} 2$, it shifts into the (sub-)millimeter wavelength regime, becoming a popular candidate for studying the ISM at high-redshift (cite: Posses_2023). Due to its brightness, the line is also used in obtaining high-resolution data such as those presented in (cite: Bethermin_2020) and (cite: Walter_2022).

Galaxy cluster progenitors, also known as ‘protoclusters’ are found in the $z>1$ epoch overlapping with the peak in the cosmic star-formation rate (SFR; (cite: Madau_2014; Overzier_2016)). (cite: Miley_2008) state that these protoclusters host massive starburst galaxies and are characterized by their large far-infrared (FIR) luminosities (cite: Casey_2014). The way protoclusters are found differs from their virialized counterparts, as they lack an established intracluster medium and have a much larger angular extent. Protoclusters are usually found via examining the environments of tracer populations such as quasi-stellar objects (QSOs, i.e., radio galaxies and quasars), Ly$\alpha$ emitters, and dusty star-forming galaxies, also known as sub-millimeter galaxies (SMGs; (cite: Weiss_2009; Dannenbauer_2014; Overzier_2016)). In recent years, surveys using the South Pole Telescope (SPT; (cite: Carlstrom_2011)) and the *Herschel Space Observatory* (cite: Herschel_2010) have revealed several rare, strongly lensed and a few un-lensed millimeter selected galaxies (cite: Eales_2010; Vieira_2010; Williamson_2011; Mocanu_2013; Oteo_2018). Among these, SPT2349$-$56 is the brightest un-lensed protocluster core discovered at $z = 4.303$.

Since its discovery, SPT2349$-$56 has been the subject of several follow-up observations. (cite: Miller_2018) presented ALMA (Atacama Large (sub-)Millimeter Array; (cite: Wootten_2009)) Cycle 3 and 4 data targeting the \[CII\] and CO(4-3) transitions, where they identified 14 galaxies at the same redshift within a radius of 65 kpc, known as the ‘core’ region. They report an estimated SFR of around 6000 $\mathrm{M_{\ensuremath{\odot}}\,yr^{-1}}$, making the system the most active protocluster core discovered to date. Further estimates provided in (cite: Hill_2020) show the presence of over 30 galaxies contained within a 500 kpc region, with SFR of over 10,000 $\mathrm{M_{\ensuremath{\odot}}\,yr^{-1}}$. The protocluster is expected to be a Coma-type progenitor, with a cluster mass of $M > 10^{15}\,\mathrm{M_{\ensuremath{\odot}}}$ at $z = 0$ (cite: Chiang_2013; Miller_2018).

(cite: Rotermund_2021) presented *Gemini*-S (optical) and *Spitzer*-IRAC (near-infrared) observations of SPT2349$-$56, identifying nine counterparts to existing galaxies and four additional Lyman-break galaxies (LBGs). The protocluster core has an estimated stellar mass of $10^{12}$ M$_\ensuremath{\odot}$, comparable to a $z = 1$ brightest cluster galaxy (BCG). With minimal detection in the optical wavelengths, the protocluster system appears to be predominantly composed of heavily dust-obscured galaxies. More recently, (cite: Hill_2022) presented deeper optical and infrared observations using the *Hubble Space Telescope* and *Spitzer*-IRAC, showing that the galaxies in the core are broadly aligned with the galaxy main sequence, resembling the distribution of field galaxies at a similar redshift. Non-cosmological hydro-dynamical simulations predict that the core region will collapse into a system resembling a low-redshift, giant elliptical galaxy within 100–300 Myr, depending on the true gas fraction (cite: Rennehan_2020).

The analysis of high-redshift galaxy kinematics is a vital component in examining galaxy evolution. The studies presented thus far have no known associations with their environments, i.e. they are ‘isolated’ or ‘field’ galaxies. This leaves a gap in our understanding of how galaxies behave in a turbulent and interactive environment like that of a protocluster core. In contrast to previous studies, in this paper, we present the kinematics of galaxies within the core region of the protocluster SPT2349$-$56.

In this paper, [2](#sec:observations_and_data_reduction) describes the observations and data reduction process, [3](#sec:methods) describes the kinematic fitting process, and [4](#sec:results) presents the results from the kinematic analysis. [5](#sec:discussion) discusses the results, comparing it to similar studies across redshifts, and explores a new classification method using the position-velocity maps. Lastly, [6](#sec:conc) summarizes our findings. Throughout the analysis, we use a $\Lambda$CDM cosmology with $h = 0.678$, $\Omega_\mathrm{m} = 0.308$, $\Omega_\Lambda = 0.692$, and $1\ensuremath{''} = 6.897$ kpc (cite: Planck_2016).

# Observations and data reduction

We use high-resolution ALMA Cycle 6 (2018.1.00058.S; PI: S. Chapman) Band 7 data, centered on the \[CII\] 158-$\ensuremath{\mu}m$ line. The data were obtained as a 6-point mosaic over several days in November 2018, with a total on-source integration time of 35 to 57 minutes for each observation. The array configurations had baselines between 15 m and 1.4 km. The quasar J2357$-$5311 was used as a phase calibrator, while J2258$-$2758 and J2056$-$4714 were used as band-pass calibrators. We note here that this data set exclusively targets the core region presented in (cite: Hill_2020). See Table 1 in (cite: Hill_2020) for more details about the observations.

The data were reduced using Common Astronomy Software Applications (`CASA`; (cite: McMullin_2007)). They were concatenated and imaged using the `tclean` task, first using the multi-frequency synthesis (MFS) routine to obtain a continuum image using channels without \[CII\] emission. We used the Briggs weighting mode and compared the results from a range of robust values between -2 and 2. We found that a robust value of 0.5 optimally balanced resolution and sensitivity. Applying the same weighting parameters, we construct a spectral cube, and subtract the continuum using the `imcontsub` task.

The line cube was cleaned to a threshold of 0.55 mJy (1.4$\times$ the root-mean-square (RMS) noise in the dirty cube), but we note that choice of this parameter does not have a significant impact on the resulting morphology of the \[CII\] maps. [1](#fig:spt2349_mosaic) shows the signal-to-noise ratio (SNR) map of the integrated \[CII\] (moment-0) intensity distribution obtained using the continuum-subtracted spectral cube, averaged between $-1250$ km s$^{-1}$ and $1350$ km s$^{-1}$.

The noise at each position was estimated using the emission free channels. A SNR cube was computed by dividing each channel map of the cube by this noise map. This approach is justified since the noise is mainly a function of position and almost constant along the frequency axis (as verified at the emission free positions). The SNR moment-0 was computed by summing all consecutive channels with SNR $> 2.5$ for positions with significant emission, while taking the noise reduction due to the decreased velocity resolution into account. For positions without significant emission, we summed the SNR channel maps centered at the mean velocity and using the mean line width of all consecutive pixels with SNR $> 2.5$ as integration borders (160 km s$^{-1}$). The spectral cube has an angular resolution of $\theta_x \times \theta_y = 0.225\ensuremath{''} \times 0.166\ensuremath{''}$ (spatial resolution of 1.55 kpc $\times$ 1.14 kpc at $z = 4.303$, $\theta_x$ and $\theta_y$ are the semi-major and semi-minor axes of the synthesized beam). It has a channel width of 13 km s$^{-1}$, and root mean square (RMS) noise $\sigma_\mathrm{[C\textsc{ii}]} = 0.5$ mJy beam$^{-1}$.

# Methods

When studying galaxy kinematics in distant sources, the finite beam size of the observations is often larger than the spatial region over which a change in velocity takes place, in an effect known as beam-smearing (cite: Davies_2011; Swaters_2009). The commonly-used tilted-ring modelling technique (cite: Rogstad_1974) has been used to extract galaxy kinematics in 2D (cite: Begeman_1989; van_der_Hulst_1992; Krajnovic_2006; Sellwood_2015), and also in 3D (cite: Sicking_1997; Jozsa_2007; 3db_2015). 2D methods require an intermediate step between the model and observations, where a velocity field must be extracted from the spectral cube. Several methods can be used to perform this step, and they can often be inconsistent amongst themselves (cite: 3db_2015). They also perform poorly with low angular resolution data due to beam-smearing. 3D methods have an advantage where they skip this intermediate stage to work directly with the spectral cube, naturally taking into account the effect of the synthesized beam to provide better results in kinematic analyses. In this work, we use ^`3D`^`BAROLO` (3D-Based Analysis of Rotating Object via Line Observations, (cite: 3db_2015)) for its ability to handle low SNR data and low angular resolution data.

## Source detection using 

Using the same naming convention presented in (cite: Hill_2020), we extract $2\ensuremath{''} \times 2\ensuremath{''}$ ($3\ensuremath{''} \times 3\ensuremath{''}$ for source C1) sub-cubes for the sources (green boxes in [1](#fig:spt2349_mosaic)) using the `imsubimage` task in `CASA`. We note that sources C3 and C6 appear off-center due to their proximity to nearby galaxies. These sub-cubes are then processed with the `SEARCH` task in ^`3D`^`BAROLO`. The task detects sources in position-position-velocity space, creating a mask using a combination of smoothing and clipping. Here, we use only the clipping options, identifying the sources at 5$\sigma_{\mathrm{[C\textsc{ii}]}}$ and growing them down to 2.1$\sigma_{\mathrm{[C\textsc{ii}]}}$ around the emission peaks for sources C2–C7, and 2.5$\sigma_{\mathrm{[C\textsc{ii}]}}$ for source C1. The lower threshold includes sufficient signal without introducing excessive noise around the sources, while also being the SNR limit for use with ^`3D`^`BAROLO`. Using these thresholds, sources C1–C11 and C13 are identified in the \[CII\] spectral cube. Sources C12 and C14–C23, identified in (cite: Hill_2020), are not detected here (see discussion in [4](#sec:results)).

## Kinematic fitting using 

The `3DFIT` task requires initial values for an array of geometrical parameters such as the kinematic center ($x_0$, $y_0$), position angle ($\phi$), and inclination angle ($i$), along with kinematic parameters such as the rotation velocity ($V_{\mathrm{rot}}$), velocity dispersion ($\sigma_{\mathrm{disp}}$), and the systemic velocity ($V_{\mathrm{sys}}$) to perform a rotation curve fit in 3D-space. A model observation is built in 3D space as concentric rings based on the initial parameter values, allowing for the gas motion to be characterized in a disc as rotational or turbulent. The model is then convolved with the beam, before performing a $\chi^2$–minimization between the observed line emission and the model. The code continues to re-compute models until a best-fitting model is found. The advantage of such a fitting process is the reduction of the aforementioned beam-smearing effects, where the comparable sizes of the source and the synthesized beam could underestimate the rotation velocity and, at the same time, overestimate the gas velocity dispersion (cite: 3db_2015). We note that the term ‘velocity dispersion’ refers to the galaxy’s intrinsic value, corrected for instrumental effects of spatial and spectral resolution. The term ‘broadening’ will refer to the non-corrected velocity dispersion.

We provide initial guesses for $x_0$, $y_0$, $V_{\mathrm{rot}}$ and $V_{\mathrm{sys}}$ using the results from the `SEARCH` task. The values of $x_0$, $y_0$ obtained as such are the flux-weighted average of the moment-0 map. We find that for some galaxies, $x_0$ and $y_0$ do not overlap with the kinematic center of the galaxy (where the line-of-sight velocity $V_{\mathrm{LOS}} \approx 0$ km s$^{-1}$). For these cases, we use the moment-1 (velocity field) map and the position-velocity ($p-v$) maps to adjust the coordinates before supplying them as initial guesses. $\phi$ is measured counter-clockwise from the north towards the receding side of the galaxy using the moment-1 map. For $i$, we first compute $(b/a)$, where $a$ and $b$ are the semi-major and semi-minor axes of the source, respectively, using the `CASA imageanalysis` tool `fitcomponents`. $i$ is then estimated using $\cos^2 i = ((b/a)^2 - q^2) / (1-q^2)$, where $q = 0.2$ for a mildly thick disc. We note here that for galaxies that appear edge-on (C1, C4, and C5), we use $\cos i = (b/a)$ since the former definition consistently overestimates the inclination angle by $\approx 5\ensuremath{^\circ}$. The estimated $i$ is also verified against a fraction-of-peak contour that encloses 20% of the peak moment-0 intensity, $\mathrm{[C\textsc{ii}]_{peak}}$. Lastly, $\sigma_{\mathrm{disp}}$ is arbitrarily set at values between 30–150 km s$^{-1}$.

Other relevant parameters used in the analysis are the ring separation (`RADSEP`), number of rings (`NRADII`), and normalization type (`NORM`). Generally, `RADSEP` defaults to the major axis of the synthesized beam in order to describe rotation curves with independently estimated points along the rotation curve. In our case, we use `RADSEP` $= \sqrt{\theta_x \theta_y}/2$, achieving a close-to-Nyquist sampling[^1] of the rotation and dispersion curves. `NRADII` provides the number of rings that are spaced at a width of `RADSEP`, where the kinematic parameters are extracted. Lastly, `NORM` allows for choosing between a pixel-to-pixel or an azimuthal normalization of the moment-0 map (see (cite: 3db_2015) for more details). Here we choose azimuthal normalization.

We finally run the `3DFIT` task to simultaneously fit four parameters per ring – $V_{\mathrm{rot}}$, $\sigma_{\mathrm{disp}}$, $\phi$ and $i$ – using a two-stage fitting process. The code allows the user to choose the regularization type for the geometry. Here, we use a Bezier[^2] fitting of geometrical parameters in the first stage, while the code automatically fits the kinematic parameters in the second stage. $x_0$, $y_0$, and $V_{\mathrm{sys}}$ are kept constant throughout after verification using the ($p-v$) diagrams and the moment-1 map. We assume a thin-disc approximation and set the scale height $z_{0}$ to 1/10th of the half-light radius of the individual sources (see (cite: Hill_2020) for values), and discuss the implications in [5](#sec:discussion). We also assume the large-scale radial motion of the gas is obscured in the high rotation velocities, and set the radial velocity $V_{\mathrm{rad}} = 0$. A sample parameter file used in the fitting is presented in Appendix [7](#sec:initial_values_and_parameter_file).

# Results

At the end of the kinematic analysis, we find converging models for sources C1–C7, i.e., the seven FIR brightest sources listed in Table 3 of (cite: Hill_2020). While we were able to detect sources C8–C11 and C13 using the `SEARCH` task, we find that due to their spatial extent approaching the synthesized beam size, too few data points exist to properly model their kinematics. Sources C12, and C14–C23 are not detected in the `SEARCH` task due to reduced sensitivity when compared to (cite: Hill_2020). They report $\sigma_{\mathrm{[C\textsc{ii}]}} = 0.22$ mJy beam$^{-1}$ channel$^{-1}$ with a similar channel width, and a beam size that is 28% larger than that for our sample. However, they use a combination of Cycle 5 and 6 ALMA data to produce a single, deep \[CII\] data cube focusing on sensitivity, whereas we only use Cycle 6 data for its longer baseline, therefore prioritizing spatial resolution. Overall, this drop in sensitivity explains the lack of detection of the sources C12, and C14–C23.

For each source, [2](#fig:spt2349_pvs_azim) and [3](#fig:spt2349_kinmaps) show the position-velocity ($p-v$) slices, the moment maps and the spectra. The $p-v$ slices are across the kinematic major and minor axes, while the moment maps and spectra are obtained from a spectral cube masked using `SEARCH` task parameters. We note that the $p-v$ slices and moment maps are not corrected for beam smearing. In [\[tab:physical_params\]](#tab:physical_params) and [\[tab:kin_params\]](#tab:kin_params), we present the resulting kinematic center, position angle, inclination angle, and systemic velocity with respect to $z = 4.303$ (the flux-weighted kinematic center of the protocluster core).

## Position-velocity slices

*Major-axis slice:* For source C1, we find a rising and flattening of the rotation curve. For the remaining sources, the rotation curve rises, but cannot be measured out to distances where it is expected to flatten ($>3$ kpc). There is, however, a symmetry between the approaching and receding sides in all the sources, showing resemblance to the characteristic ‘S’-shape of a rotation-supported disc (cite: deBlok_2008).\
*Minor-axis slice*: At low angular resolution, a minor-axis $p-v$ slice of a moderately inclined rotating disc will present a broad, ‘blooming’ pattern due to line broadening from instrumental effects (cite: 3db_2015). This behavior is present in all our sources.

CccCCCC Source & R.A., Dec. (morph)$^{a}$ & R.A., Dec. (kin)$^{b}$ & $\phi_{\mathrm{morph}}$$^{c}$ & $\phi_{\mathrm{kin}}$$^{d}$ &$i$$^{e}$ & $z_0$$^{f}$\
& (J2000) & (J2000) & ($^\circ$) & ($^\circ$) & ($^\circ$) & (kpc)\
& 23:49:42.7 $-$56:38:19.4 & 23:49:42.6 $-$56:38:19.4 & 244.3 & 238.9 & 72.4 & 0.2\
& 23:49:43.2 $-$56:38:30.1 & 23:49:43.2 $-$56:38:30.1 & 93.1 & 112.7 & 52.7 & 0.2\
& 23:49:42.8 $-$56:38:23.8 & 23:49:42.8 $-$56:38:23.8 & 95.7 & 85.8 & 51.5 & 0.1\
& 23:49:41.4 $-$56:38:22.4 & 23:49:41.4 $-$56:38:22.4 & 316.0 & 315.2 & 62.9 & 0.1\
& 23:49:42.1 $-$56:38:25.8 & 23:49:42.1 $-$56:38:25.8 & 180.6 & 180.5 & 68.3 & 0.2\
& 23:49:42.8 $-$56:38:25.1 & 23:49:42.8 $-$56:38:25.1 & 314.5 & 318.7 & 48.8 & 0.1\
& 23:49:43.0 $-$56:38:18.1 & 23:49:42.9 $-$56:38:18.0 & 328.5 & 13.2 & 57.4 & 0.2

Table notes: $^{a,b}$ Morphological and kinematic center of the source, respectively. $^{c,d}$ Morphological and derived kinematic position angles, respectively. $^{e}$ Derived inclination angle.

## Moment maps and spectra

For our sample, we find from column 1 in [3](#fig:spt2349_kinmaps) that there is minimal scatter ($<0.22\ensuremath{''}$) between the kinematic center (black cross) and the flux-weighted average of the moment-0 map (blue cross). The red contour is at $0.2\mathrm{[C\textsc{ii}]_{peak}}$, and the black ellipse describes the outermost evaluated ring. There is good agreement between the two for all the sources, except in the case of C2 where the \[CII\] emission appears to be asymmetrically concentrated around the center within a small region. In the case of source C7, we find sub-structures at this spatial scale that are perpendicular to its kinematic major axis.

The position angle for the morphological major axis is derived using the `CASA imageanalysis` tool `fitcomponents`, and is reported in [\[tab:physical_params\]](#tab:physical_params). It is represented by the blue dashed line. We note that the angle obtained from the tool is degenerate by $180\ensuremath{^\circ}$, and we report the adjusted value in [\[tab:physical_params\]](#tab:physical_params). The difference between the morphological and kinematic axes (black dashed line in [3](#fig:spt2349_kinmaps)) is less than $30\ensuremath{^\circ}$ for all the sources except C7.

Column 2 in [3](#fig:spt2349_kinmaps) shows the moment-1 maps, obtained as the intensity-weighted velocity of the spectral line. In each source, we find a smooth velocity gradient, with the kinematic and morphological major axes broadly aligned with each other. The blue and red contours constitute a ‘spider’ diagram for each source and are placed at $\pm n100$ ($n=1,2,3)$ km s$^{-1}$ (cite: Begeman_1989). There are no closed contours along the major axis, suggesting that there is no peak in the rotation curve. The exceptions are C6 and C7, where the map shows a closed loop. Since there is no peak in the velocity profile (see [4](#fig:spt2349_velocity_profiles), column 1), we suggest this is due to a combination of observing a compact disc, low SNR and remnant beam effects. The black cross is the kinematic center of the galaxy.

Column 3 in [3](#fig:spt2349_kinmaps) shows the line broadening map for the sources, i.e., a velocity dispersion map that is not corrected for instrumental broadening. We reiterate here that [3](#fig:spt2349_kinmaps) shows the moment maps obtained directly from the data cubes, without correcting for beam smearing. They are not used in the kinematic extraction and are presented here for completeness only. Appendix [8](#sec:model_residual_maps) shows the observed, modeled, and residual moment maps for sources C1–C7.

Column 4 in [3](#fig:spt2349_kinmaps) shows the spectrum of each source. The dashed vertical line is the systemic velocity of the source. We find double-peaked profiles with varying degrees of assymmetry across the systemic velocity for all the sources.

## Velocity profiles

Columns 1 and 2 in [4](#fig:spt2349_velocity_profiles) show the rotation curve and velocity dispersion profiles respectively, derived using the spectral cubes of the sources. The errors are obtained via a Markov-Chain Monte Carlo (MCMC) sampling of the parameter space around the best-fit value. We note here that the errors are not statistical errors, but a measure of how the well-behaved the parameter space is around the best-fit value (cite: 3db_2015). In sources C3–C6, there is insufficient data to estimate the outermost parts of the rotation curve ($>3.5$ kpc). In [\[tab:kin_params\]](#tab:kin_params), we tabulate the noise-weighted mean rotation velocity and dispersion, calculated by excluding the data points falling within the beam size ($<1.55$ kpc, vertical dashed line in [4](#fig:spt2349_velocity_profiles)) to avoid possible remnant beam-smearing effects. We are then left with at least three independent measurements for each velocity and dispersion profile. Since we have a reasonable estimate of the inclination angles, the computed $V_{\mathrm{rot}}$ values are robust. The estimated $\sigma_{\mathrm{disp}}$ for all the galaxies are greater than the velocity resolution of 13 km s$^{-1}$, and we can therefore expect the values produced by `3DFIT` to be reliable.

# Discussion

CCCCCCCCCC Source & $V_{\mathrm{sys}}$$^{a}$ & $V_{\mathrm{rot}}$$^{b}$ & $\sigma_{\mathrm{disp}}$$^{c}$ & $(V_{\mathrm{rot}}/\sigma_{\mathrm{disp}})$$^{d}$ & $Q_\mathrm{T}$$^{e}$ & $f_{\mathrm{gas}}$$^{f}$\
& (kms$^{-1}$) & (kms$^{-1}$) & (kms$^{-1}$) & & &\
& -21.5 & 472.3 & 95.6 & 4.0 & 1.1 & 0.35\
& -534.5 & 209.3 & 37.6 & 3.3 & 0.6 & 0.20\
& -265.1 & 425.4 & 49.3 & 6.7 & 0.9 & \<0.69\
& -93.5 & 427.6 & 50.6 & 4.1 & 1.3 & 0.54\
& 118.2 & 425.3 & 20.8 & 5.9 & 0.8 & 0.40\
& 466.3 & 184.2 & 35.7 & 3.3 & 0.6 & 0.17\
& 618.7 & 173.3 & 14.9 & 4.2 & 0.2 & 0.31\
& 357.1 (114.7) & 48.4 (23.5) & 4.5 (1.3) & 0.9 (0.3) &

Table notes: $^{a}$ Systemic velocity, relative to $z = 4.303$ $^{b,c,d,e}$ Noise-weighted mean and uncertainty for rotation velocity, velocity dispersion, $V/\sigma$ ratio, and Toomre parameter at $r>1.55$ kpc. $^{f}$ Gas fraction, as presented in (cite: Rotermund_2021).

We have presented the results of a 3D kinematic analysis of the seven FIR brightest galaxies within the SPT2349$-$56 protocluster core. To interpret the results, we first take a look at the assumptions made in the fitting process. First, we note that any further improvement in the derived kinematics in the inner part of the discs can only be achieved with a combination of higher resolution and deeper data.

Next, the two available types of normalization – localized and azimuthal – serve different purposes (cite: 3db_2015). The former constructs non-axisymmetric models, used to identify untypical regions such as small-scale clumps, outflows or holes that could affect the overall velocity profile fit. This is presented via a model moment-0 map that is identical to that of the observations, i.e., the integrated spectrum in each pixel is the same for the model and the observations. In the latter case, an axisymmetric model is constructed such that the model flux is normalized to the azimuthally averaged flux of the data in each ring. This model is used to identify warps or large-scale clumps. We compared the output from both cases and find no large-scale structures in the galaxies, but the azimuthal normalization presented a better fit to the geometry. The data, model, and residual moment maps, residual $p-v$ maps, and fitting results for the four free parameters obtained from the azimuthal fitting are presented in Appendix [8](#sec:model_residual_maps). We also found there is no significant, large-scale radial motion present in the galaxies by setting the radial velocity as a free parameter with an initial value of $V_{\mathrm{rad}} = 0$. We note that any possible radial velocity component much less than the rotation velocity would be lost due to resolution effects and low sensitivities.

The simultaneous modeling of geometry and kinematics often leads to unphysical gaps in the velocity and dispersion profiles. In our case, the `3DFIT` code uses the first minimization stage to fit a Bezier function to both $\phi$ and $i$. The next stage is used purely to fit the velocity curves, holding the geometry constant. We find that this two-stage minimization process is efficient compared to user-supplied fixed angles.

The weakest link in kinematic modeling is the inclination angle. For galaxies that appear face-on, there is no significant visual distinction between $i = 5\ensuremath{^\circ}$ and $i = 20\ensuremath{^\circ}$, but their estimated rotation curves differ drastically since $V_{\mathrm{rot}} \propto V_{\mathrm{obs}}/ \sin i$. For reference, $\sin 20\ensuremath{^\circ}/\sin 5\ensuremath{^\circ} \approx 4$. In such cases, the estimation of the minor-to-major ($b/a$) axis ratio has to be done with great precision. Here, we use a number of techniques as described in [3.2](#subsec:3Dfitting) to initially estimate $b/a$, and all the galaxies clearly present initial values greater than $40\ensuremath{^\circ}$.

Our assumption of a thin disc with $z_0 \approx 0.1$ times the half-light radius also affects the estimation of the inclination angle. The mean of the derived inclination angles for our sample is $\approx$ 60$^\circ$,corresponding to the mean inclination of a random sample of galaxies (cite: Romanowsky_2012). The sample also presents clear rotation curves, suggesting that we are not dealing with face-on discs, where the assumption of a thin disc may wreck our interpretation. While the generated model reproduces the \[CII\] emission well, it is still a simplified assumption, since at high redshift, turbulence within the disc would give rise to a higher velocity dispersion and a thick disc. (cite: Neeleman_2020) present a comparison between assumptions of an infinitely thin disc and a disc where the scale height is 0.15–1 times the scale radius at $z\approx 4.2$. Their results show a decrease in the estimated inclination angles by $\approx 7\ensuremath{^\circ}$. Since we use $z_0 =$ 0.07–0.15 times the scale radius provided in (cite: Hill_2020), there may be a possibility that we are overestimating the inclination angles. However, in the absence of additional information about the disc thickness, we report values obtained using a simplified thin-disc assumption.

## Kinematic analysis

### Rotators vs. Mergers

At the spatial resolution of our study, it remains difficult to distinguish between rotating discs and compact mergers. Several studies in the literature exist where the gas kinematics and morphology in FIR bright high redshift galaxies appear to be fully consistent with a rotating disc, but the authors favor the interpretation of a compact merger (cite: Neri_2014; Litke_2019). Merging of galaxies is a common interpretation for the cause of the extreme SFRs of local and high-redshift FIR bright sources. For the SPT2349-58 protocluster system, a strong interaction between the galaxies (cite: Rennehan_2020) is a likely trigger for the high SFRs in the gas-rich members, but as described in the following sections, we find evidence for rotating disc signatures along with mergers and/or tidal disturbance signatures in six of these galaxies.

For a given system to be dynamically classified as rotation-supported, a series of criteria exist in the literature (cite: Foerster_Schreiber_2018; Wisnioski_2019; Foerster_schreiber_2020; Jones_2021). The system:

1.  Must have a monotonically smooth velocity gradient that defines the kinematic axis.

2.  Is rotation-supported and has $V/\sigma > 3$.

3.  Has spatially coincident morphological and kinematic centers.

4.  Has morphological and kinematic major axes separated by less than $30\ensuremath{^\circ}$.

5.  Has a centrally-peaked velocity dispersion profile, such that the maximum defines the kinematic center.

For our sample, we find that all galaxies satisfy condition 1. In this work, the morphological center of a galaxy is defined as the flux-weighted center of the moment-0 map (column 2 in [\[tab:physical_params\]](#tab:physical_params)). Therefore, for condition 3, if the distance between the kinematic and morphological center (determined using simple geometry) is less than $\theta_x = 0.22\ensuremath{''}$, then we assume that the centers are spatially coincident. The sources in our sample, except C7, satisfy condition 3.

From [4.2](#subsec:moment_maps), we have the difference between the kinematic and morphological axes to be $< 30\ensuremath{^\circ}$ for all the sources except C7. In addition, if we use the definition for kinematic misalignment angle ($\phi_{\mathrm{mis}}$) from (cite: Franx_1991), we find the morphological major axis of the \[CII\] gas distribution co-aligned with the kinematic axis for the sample such that $\phi_{\mathrm{mis}} < 15\ensuremath{^\circ}$. The exceptions are sources C2 and C7, where in the former, the emission appears to be centrally clumpy (see [3](#fig:spt2349_kinmaps), columns 1 and 2), and in the latter, the sub-structures appear perpendicular to the kinematic axis.

Next, from [4](#fig:spt2349_velocity_profiles) we find that for all of our sources, excluding the points at $<0.22\ensuremath{''}$, the velocity dispersion profiles are centrally peaked. The dispersion maps presented in [3](#fig:spt2349_kinmaps) are broadening maps, and the increase in dispersion towards the edges is a result of low SNR and/or the broadening effect itself.

In addition to these criteria, we refer to [4.1](#subsec:position_velocity_slices), where we identified the presence of the distinctive symmetrical $p-v$ slices. Lastly, we refer to column 4 in [3](#fig:spt2349_kinmaps) where we find double-peaked profiles for all the sources, considered a signature of rotating discs (cite: Kohandel_2019). Therefore, based on the conventional dynamical-support criteria, we find no immediate evidence supporting the presence of mergers in the protocluster environment, allowing us to further investigate gas kinematics. The exception is source C7, which appears to be a major merger, and we discard from the analysis in [5.1.3](#subsubsec:SPT2349).

cccCccC Study$^{a}$ & Type of Objects & Tracer & $z$ & $V$ & $\sigma$ & $V/\sigma$\
(cite: Foerster_Schreiber_2009) & Main-Sequence & H$\alpha$ & 2.08 & $V_{\mathrm{rot}}$ & $\sigma_{\mathrm{disp}}$ & $4.6 \pm 0.6$\
(cite: Teodoro_2016) & Main-Sequence & H$\alpha$ & 0.90 & $V_{\mathrm{flat}}$ & $\sigma_{\mathrm{ext}}$ & $5.5 \pm 0.3$\
(cite: Rizzo_2020) & Starburst & \[CII\] & 4.22 & $V_{\mathrm{flat}}$ & $\sigma_{\mathrm{ext}}$ & $14.4 \pm 0.4$\
(cite: Neeleman_2020) & Main-Sequence & \[CII\] & 4.26 & $V_{\mathrm{rot}}$ & $\sigma_{\mathrm{disp}}$ & $3.4_{-0.3}^{+1.1}$\
(cite: Fratenalli_2021) & Starburst & \[CII\] & 4.54 & $V_{\mathrm{flat}}$ & $\sigma_{\mathrm{ext0}}$ & $9.0 \pm 0.7$\
(cite: Rizzo_2021) & Starburst and Main-Sequence & \[CII\] & 4.50 & $V_{\mathrm{flat}}$ & $\sigma_{\mathrm{ext}}$ & $11 \pm 4$\
(cite: Lelli_2021) & Starburst & \[CII\] & 4.75 & $V_{\mathrm{rot}}$ & $\sigma_{\mathrm{disp}}$ & $9.7 \pm 3.7$\
(cite: Jones_2021) & Main-Sequence & \[CII\] & 4.86 & $V_{\mathrm{rot}}$ & $\sigma_{\mathrm{disp}}$ & $3.3 \pm 0.7$\
(cite: Posses_2023) & Main-Sequence & \[CII\] & 6.81 & $V_{\mathrm{flat}}$ & $\sigma_{\mathrm{ext}}$ & $2.9 \pm 0.5$

Table notes: $^{}$ *Note-* The samples are shown in [5](#fig:spt2349_ratio_vs_redshift). $^{a}$ The studies chosen depend on two criteria - (i) It uses 3D kinematic modeling methods, (ii) It uses an ionized tracer.

### Gas kinematics

Gas kinematics can help study the measure of rotational support in a galaxy. In this context, the rotational velocity and velocity dispersion correspond to *ordered* and *random* motions, respectively. There are a few definitions available in the literature to quantify this, such as $\Delta V_{\mathrm{obs}}/2\sigma_{\mathrm{int}}$ and $V_{\mathrm{rot}}/\sigma_{\mathrm{disp}}$ (cite: Foerster_Schreiber_2009; Rizzo_2020). Here, $V_{\mathrm{obs}}$ is the velocity gradient of the tracer, and $\sigma_{\mathrm{int}}$ is the source-integrated velocity dispersion, where both are uncorrected for inclination. $V_{\mathrm{rot}}$ and $\sigma_{\mathrm{disp}}$ are the inclination-corrected rotation velocity and velocity dispersion respectively, where two further definitions can be derived. The first is obtained by setting $V_{\mathrm{rot}} = V_{\mathrm{max}}$, the maximum inclination-corrected rotation velocity and $\sigma_{\mathrm{disp}} = \sigma_{\mathrm{mean}}$, the mean velocity dispersion of the profile. The second definition is used for our sample, where we set $V_{\mathrm{rot}} = V_{\mathrm{flat}}$ and $\sigma_{\mathrm{disp}} = \sigma_{\mathrm{extended}}$, both measured beyond $0.22\ensuremath{''}$ ($\approx 1.55$ kpc, the beam size, marked as a vertical dashed line in [4](#fig:spt2349_velocity_profiles)).

We exclude the innermost points due to possible remnant beam-smearing effects in the central regions. We use the (cite: Burkert_2010) definition, where a galaxy is dynamically hot or pressure-supported if $V/\sigma \le 3$, and dynamically cold or rotation-supported if $V/\sigma > 3$. We find, however, that there are other thresholds used across different works (see (cite: Turner_2017) and references therein).

Simulations and comparative observational studies have found that the velocity dispersion measured from ionized tracers tends to be $\approx$ 15 km s$^{-1}$ higher than those obtained from molecular or neutral tracers, implying a lower $V/\sigma$ when using ionized tracers (cite: Ubler_2019; Kretschmer_2022). Similar to recent high-redshift studies that use ionized gas as a tracer to study gas kinematics, we use the \[CII\] 158-$\ensuremath{\mu}m$ line to study the galaxies within the SPT2349$-$56 protocluster core.

### SPT2349$-$56

For the galaxies in our sample, we observe a rise and flattening of the rotation curves in sources C1–C5, and only flattening in source C6, while the dispersion profiles are all centrally peaked (excluding the beam, $<1.55$ kpc) and decaying (see [4](#fig:spt2349_velocity_profiles), columns 1 and 2 respectively). Column 3 in [4](#fig:spt2349_velocity_profiles) shows the complete $V/\sigma$ ratio profile for the galaxies in our sample, while Column 5 in [\[tab:kin_params\]](#tab:kin_params) shows the corresponding mean $V/\sigma$ ratio. All seven sources show $V/\sigma > 3$, categorizing them as rotation-dominated systems, also satisfying condition 2 in [5.1.1](#subsubsec:rots_vs_merg). The mean of the sample (excluding source C7) is $4.5 \pm 0.2$. Since \[CII\] traces the cold inner molecular disc, our sample, with its high $V/\sigma$ values, is in line with the results presented for the inner molecular disc in (cite: Kretschmer_2022) and (cite: Kohandel_2023). [5](#fig:spt2349_ratio_vs_redshift) summarizes the current understanding of the evolution for the $V/\sigma$ ratio with $z$, for both observational data and theoretical models. We discuss the relevant theoretical models and observational samples in the following sections.

### Numerical and analytical studies

The grey shaded region in [5](#fig:spt2349_ratio_vs_redshift) includes results and analyses from (cite: Dekel_2014; Zolotov_2015; Hayward_2017) and (cite: Pillepich_2019). Through theoretical methods and cosmological simulations, (cite: Dekel_2014) and (cite: Zolotov_2015) show that beyond $z = 3$, galaxies are dominated by violent disc instabilities, with $V/\sigma \le 2$.

(cite: Hayward_2017) presented an analytical model to study the consequences of stellar feedback processes. In this model, the velocity dispersion is not a measured quantity, but a derived one, and is obtained as $\sigma_{\mathrm{disp}} \approx f_{\mathrm{gas}} (V_\mathrm{c}/\sqrt{2})$[^3]. Here, $f_{\mathrm{gas}} = M_{\mathrm{gas}}/(M_{\mathrm{gas}}+M_{\mathrm{star}})$ is the gas fraction, and $V_\mathrm{c} = \sqrt{V_\mathrm{gas}^2 + V_\mathrm{star}^2 + V_\mathrm{DM}^2}$ is the circular velocity. Since we do not have stellar and dark matter velocity contributions on hand, we substitute $V_\mathrm{c} = V_\mathrm{gas}$ and first set $f_{\mathrm{gas}} = 0.7$ (cite: Tadaki_2019; Rennehan_2020). This leaves us with predicted $\sigma_{\mathrm{disp}}$ values that are approximately 2–5 times higher than the derived values. However, if we use the $f_{\mathrm{gas}}$ values presented in (cite: Rotermund_2021) (column 7 in [\[tab:kin_params\]](#tab:kin_params)), we find that the predicted $\sigma_{\mathrm{disp}}$ values are between 0.5–3 times the derived values. This difference in predicted $\sigma_{\mathrm{disp}}$ values using the (cite: Hayward_2017) model possibly rises from the assumption that for high-redshift galaxies, the inferred gas fractions are usually high ($f_{\mathrm{gas}} \approx 0.7$), spread over a range of 0.4–0.9 (cite: Tadaki_2019).

Lastly, (cite: Pillepich_2019) predict the evolution of $V/\sigma$ with respect to redshift ($0 \le z \le 5$) for a gas mass range of $10^9 - 10^{11}$ $M_\ensuremath{\odot}$ from the TNG50 simulation. At $z = 4.303$, we find that the mean SPT2349$-$56 value ($4.5 \pm 0.2$) is greater than the median TNG50 value of $3\pm 1.5$ by one standard deviation. We also note that in [5](#fig:spt2349_ratio_vs_redshift), this evolution is extrapolated beyond $z = 5$.

### Observational samples

[\[tab:comparison_Sample\]](#tab:comparison_Sample) shows the observational samples used in [5](#fig:spt2349_ratio_vs_redshift) as comparisons, including the tracer, the definition of $V_{\mathrm{rot}}$ and $\sigma_{\mathrm{disp}}$, and the $V/\sigma$ values. We choose the samples based on two criteria - (i) The study uses an ionized gas tracer to study kinematics; (ii) The study uses a 3D kinematic modeling method to evaluate the kinematics. The objects in these studies are starbursts or Main-Sequence (MS) galaxies. Beyond $z = 2.5$, several samples deviate from the predicted $V/\sigma$ evolution. Starbursts (colored crosses in [5](#fig:spt2349_ratio_vs_redshift)) appear to have higher $V/\sigma$ compared to the MS samples (colored dots in [5](#fig:spt2349_ratio_vs_redshift)). SPT2349$-$56 consists mainly of MS galaxies (cite: Rotermund_2021; Hill_2022), and its mean and corresponding error (black filled circle in [5](#fig:spt2349_ratio_vs_redshift)) is within the region between starbursts and MS samples at a similar redshift.

The comparison samples at a similar redshift are *field* galaxies, i.e., they are not associated with a protocluster-like environment. In these cases, it is possible to achieve a rotating disc via ‘cold’ processes (see [1](#sec:introduction)). However, if we assume that the SPT2349$-$56 core accretes via a ‘cold stream in a hot medium’ as presented in (cite: Dekel_2009a), we find that the tidal interaction timescale in a protocluster system is much shorter than the cold stream accretion time, rendering the cold streaming process inefficient. This is further discussed in [5.4](#sec:rotating_discs_in_a_protocluster_core).

## Toomre parameter analysis

In the absence of sufficient random motion in a thin, smoothly distributed rotating disc, the disc is expected to suffer violent instabilities (cite: Toomre_1964). The Toomre parameter ($Q_\mathrm{T}$) measures the stability of a disc against gravitational perturbations. $Q_\mathrm{T}$ is defined as

$$\begin{equation}
\label{eq:toomre_q}
        Q_\mathrm{T} = \frac{\sigma_{\mathrm{disp}}\kappa}{\pi G \Sigma_{\mathrm{gas}}}\;,
    
\end{equation}$$

where $Q_\mathrm{T} < 1$ describes an unstable disc. $\kappa = \sqrt{R( \mathrm{d} \Omega^{2}/\mathrm{d} R) + 4\Omega^2}$ is the epicyclic frequency, with $\Omega = V_{\mathrm{rot}}/R$ (which simplifies to $\kappa = \sqrt{2}V_{\mathrm{rot}}/R$). $\Sigma_{\mathrm{gas}}$ is the gas mass surface density, which is obtained in our case as

$$\begin{equation}
 \label{eq:surface_density}
        \Sigma_{\mathrm{gas}} = \frac{L_{\mathrm{CII}}\alpha_{\mathrm{CII}}}{\mathrm{per\,unit\,area}}\quad(\mathrm{M_\ensuremath{\odot}\,kpc}^{-2})\;,
    
\end{equation}$$

where $L_{\mathrm{CII}}$ and $\alpha_{\mathrm{CII}}$ are the \[CII\] line luminosity and the atomic gas mass to \[CII\] line luminosity ratio, respectively. The $\alpha_{\mathrm{CII}}$ parameter takes a range of values between 5 – 30 (Sulzenauer et al. (in prep.), (cite: Zanella_2018; Rizzo_2020; Vizgan_2022)). Here we use values presented in (cite: Rizzo_2020), where $\alpha_{\mathrm{CII}} = 7.3 \pm 1.2$ $M_\ensuremath{\odot}/L_\ensuremath{\odot}$. There is a possibility to use dynamical mass estimates to deduce $\alpha_{\mathrm{[C\textsc{ii}]}}$ for this sample, however, it is beyond the scope of this work.

$L_{\mathrm{CII}}$ is found via replacing the CO line luminosity calculations with the \[CII\] line in Eq. 1 of (cite: Solomon_1997)

$$\begin{equation}
        L_{\mathrm{CII}} = 1.04 \times 10^{-3} S_{\mathrm{CII}}\Delta V \nu_{\mathrm{rest}}(1+z)^{-1} D_\mathrm{L}^2 \quad (\mathrm{L_\ensuremath{\odot}}),
    
\end{equation}$$

where $S_{\mathrm{CII}}\Delta V$ is the velocity integrated flux in Jy km s$^{-1}$, $\nu_{\mathrm{rest}}$ is the \[CII\] line rest frequency in GHz, and $D_\mathrm{L}$ is the luminosity distance in Mpc.

Studies such as (cite: Rizzo_2020) and (cite: Neeleman_2020) obtain mean values of $\approx 0.96$ beyond 1 kpc radii at redshift $\approx 4.2$. For our sample of galaxies, the mean value is $Q_\mathrm{T} = 0.8 \pm 0.1$, with individual values ranging from 0.2–1.1. The largest source of uncertainty is the gas surface density, which could be mitigated using sophisticated means of flux profile extraction in future works. Sources C2 and C7 show sub-structures in the moment-0 maps with low $Q_\mathrm{T}$ values, suggesting an imminent collapse of unstable discs. Source C6, found in the central region of the core, appears to be extremely compact in its moment-0 map with low $Q_\mathrm{T}$ values, suggesting unresolved sub-structuring at our spatial resolution.

cCCCc Source & $P_{\mathrm{major}}$ & $P_{\mathrm{V}}$ & $P_{\mathrm{R}}$ & Classification\
& Discs $\le 0 <$ Mergers & Discs $< 0 <$ Mergers & Mergers $0 \leftrightarrow 1$ Discs & \
C1 (A) & -1.47 & -1.18 & 0.30 & Disturbed disc\
C2 (J) & -1.62 & -0.85 & 0.16 & Disturbed disc\
C3 (B) & -2.64 & -0.52 & 0.41 & Disc\
C4 (D) & -1.32 & -0.62 & 0.35 & Disturbed disc\
C5 (F) & -1.32 & -0.55 & 0.42 & Disturbed disc\
C6 (C) & -2.33 & -0.50 & 0.19 & Disturbed disc\
C7 (K) & -1.63 & -0.40 & 0.35 & Disturbed disc

[6](#fig:spt2349_q_vs_ratio) shows disc stability as a function of the $V /\sigma$ ratio. Sources C1 and C4 show rotation support with a stable disc, while the rest of the sources show rotation support with unstable discs. There is a mild positive correlation between disc stability with respect to dynamical support, with a Pearson-$r$ coefficient of $\approx 0.19$. In order to further explore the nature of these sources using their morphology, we utilize a newly developed tool, `PVsplit` (cite: Rizzo_2022).

## 

In light of low-resolution data and its role in the incorrect kinematic classification of galaxies at high-redshift, (cite: Rizzo_2022) have developed a new tool, `PVsplit`. This method utilizes $p-v$ maps instead of moment maps to quantify the morpho-kinematic nature of galaxies using three empirical parameters, provided that there are at least three independent elements and SNR $\ge 10$ across all the elements. The three parameters are defined as follows:

- $P_{\mathrm{major}}$ : asymmetry of the major-axis slice with respect to the systemic velocity of the source; Discs $\le 0 <$ Mergers

- $P_{\mathrm{V}}$ : distribution of the emission peak along the velocity axis; Discs $< 0 <$ Mergers

- $P_{\mathrm{R}}$ : distribution of the emission peak along the position axis; Discs: closer to 1, Mergers: closer to 0.

Applying Eqns. 6, 7 and 8 in (cite: Rizzo_2022) to our $p-v$ maps, we present the results for our sample in [\[tab:PVsplit\]](#tab:PVsplit) and [7](#fig:spt2349_pvsplit). Targets in our sample do not meet the criteria for SNR, but we nevertheless apply the method since it gives valuable insights in the dynamical classification of the systems. The dividing plane in [7](#fig:spt2349_pvsplit) is obtained using $-0.63P_{\mathrm{major}} - 0.27P_{\mathrm{V}} + 2.78P_{\mathrm{R}} - 2.72 = 0$ (cite: Roman_Oliviera_2023).

Comparing [7](#fig:spt2349_pvsplit) with Figure 17 in (cite: Rizzo_2022), it is immediately apparent that our sample occupies the same space as those of *disturbed* discs and mergers. Based on the definitions of $P_{\mathrm{major}}$ and $P_{\mathrm{V}}$, we find from [\[tab:PVsplit\]](#tab:PVsplit) that all the sources satisfy conditions for being ‘disc-like’. This implies two things - first, the sources are symmetric about the systemic velocity; second, the emission is either slightly spread out along the line-of-sight velocities or concentrated closer to the systemic velocity. Lastly, based on the intensity distribution along the position axis ($P_{\mathrm{R}}$) and the best-dividing plane, we find that only source C3 identifies as a disc in our sample.

A possible explanation for the differences in classifications obtained via dynamical analysis ([5.1.3](#subsubsec:SPT2349)) and `PVSplit` is tidal torques. In a highly-overdense environement like that of a protocluster core, tidal torques can induce a velocity gradient across the galaxy, along with an asymmetric gas accumulation (cite: Gullberg_2019; MartinezGarcia_2023). From column 4 in [3](#fig:spt2349_kinmaps), we know that the sources display double-peaked spectra with varying degrees of asymmetry, arising from the corresponding aymmetric gas distributions. This interpretation also supports the low Toomre-$Q$ values obtained in [5.2](#subsec:toomre_parameter_analysis). We therefore find that at this resolution and sensitivity, our sample adheres to the ‘disturbed discs’ region, despite the high $V/\sigma$ values, i.e., they present with strong kinematic signatures and moderate morphological disturbances.

## Rotating discs in a protocluster core

The number of observations describing the presence of cold rotating disc galaxies at high-redshift (cite: Pillepich_2019; Rizzo_2020; Neeleman_2020; Fratenalli_2021) is already challenging our current theories of galaxy evolution. In our case, we have found six seemingly well-ordered discs packed in an extreme environment containing 23 galaxies with average velocity $v = 360$ km s$^{-1}$ (cite: Hill_2020) within a radius of $\approx 100$ kpc. At $z = 4.303$, the age of the Universe is 1.4 Gyr. From (cite: Murdin_2001), the crossing time for the protocluster core is $$\begin{equation*}
        t_{\mathrm{cr}} = \frac{R}{v} = \frac{100\,\mathrm{kpc}}{360\,\mathrm{km\,s^{-1}}} = 0.28\,\mathrm{Gyr},
    
\end{equation*}$$

while the relaxation time is

$$\begin{equation*}
        t_{\mathrm{r}} = t_{\mathrm{cr}} \frac{N}{8\ln{N}} = 0.27\frac{23}{8\ln{23}} = 0.25\,\mathrm{Gyr}.
    
\end{equation*}$$

In a protocluster system that is around 1 Gyr old (inferred from the stellar population, see (cite: Rotermund_2021)), we have $t_{\mathrm{cr}} \approx t_{\mathrm{r}}$, meaning that the galaxies are losing energy via collisions every 0.27 Gyr; i.e., they very likely had a close interaction within their lifetime, suggesting that their gaseous discs should be disturbed, clearly evident in [7](#fig:spt2349_pvsplit).

Explanations other than that of tidal torques in an overdense environement for ordered motion are that the discs are able to immediately recover after an interaction, or that the discs are simply so massive, that a strong interaction does not affect its stability, or that the classical definitions strongly depend on the SNR of the source.

Numerical simulations of the SPT2349$-$56 protocluster system provide further evidence that the galaxies are undergoing strong interactions at a timescale of $\approx 0.5$ Gyr (cite: Rennehan_2020). However, (cite: Remus_2022) present results from the *Magneticum* simulation, wherein they reproduce the fast-rotating galaxies at the protocluster core, suggesting that the discs need not be completely destroyed even if they experience close interactions. This is also supported by recent observations of interacting galaxies in group environments at high-redshift, where the kinematics traced by \[CII\] observations show well-ordered rotating discs, albeit in less dense environments (cite: Oteo_2016; Roman_Oliviera_2023). Despite this possible evidence of another galaxy group presenting with ordered discs in its environment, we lack evidence to state whether the phenomenon of rotating discs in such environments is an outlier or the norm.

# Conclusion

In this paper, we have presented kiloparsec-scale resolution ALMA observations of the \[CII\] 158-$\ensuremath{\mu}m$ transition of galaxies within the SPT2349$-$56 protocluster system at $z \approx 4.3$. Previous works describe the identification, multi-wavelength studies, and forward simulations of the system (cite: Miller_2018; Hill_2020; Rennehan_2020; Rotermund_2021; Hill_2022), and here we report the kinematics of the constituent galaxies. The results are summarized as follows:

1.  The \[CII\] emission of our sample of the seven submillimeter-bright galaxies is reproduced well using differentially-rotating models with a thin-disc assumption.

2.  The mean inclination-corrected rotation velocity of the sample is $V_{\mathrm{rot}} = 357.1 \pm 114.7$ km s$^{-1}$, and individual values between 170–475 km s$^{-1}$.

3.  The mean intrinsic velocity dispersion of the sample is $48.4 \pm 23.5$ km s$^{-1}$, and individual values between 10–100 km s$^{-1}$.

4.  On the basis of criteria found across literature, we find evidence for six rotating discs and one possible major merger at $z = 4.303$ within a protocluster environment.

5.  The mean Toomre parameter for the sample is $Q_\mathrm{T} = 0.9 \pm 0.3$, where sources C1 and C4 are stable rotating systems, while the remaining sources classify as unstable rotating discs.

6.  Analyzing the $p-v$ maps to further study the morpho-kinematic nature of these sources, we find evidence for disc disturbance in regions $<10$ kpc, supporting the low Toomre-$Q$ values and high $V/\sigma$ values. That is, the sources are observed as disturbed rotating discs characterized by an asymmetric gas distribution.

Overall, we find that the dynamical properties of the galaxies in our sample show considerable similarity to a number of other observations at a similar redshift. The main difference is that of morphology and the environment - while the comparison samples are not associated with turbulent environments, our galaxies exist in a highly active protocluster system that in itself has several unique properties.

# Acknowledgements

The authors would like to thank E. M. Teodoro for the many useful discussions about using ^`3D`^`BAROLO`. M. A. acknowledges support from FONDECYT grant 1211951, ANID+PCI+INSTITUTO MAX PLANCK DE ASTRONOMIA MPG 190030, ANID+PCI+REDES 190194 and ANID BASAL project FB210003. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00058.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA

# Software

Astropy (cite: astropy_2013; astropy_2018), `CASA` (cite: McMullin_2007), ^`3D`^`BAROLO` (cite: 3db_2015)

natexlab

(ref: astropy_2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Begeman_1989) Begeman, K. G. 1989, A&A, 223, 47

(ref: Bethermin_2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2, doi: [`10.1051/0004-6361/202037649`](http://doi.org/10.1051/0004-6361/202037649)

(ref: Burkert_2010) Burkert, A., Genzel, R., Bouché, N., et al. 2010, ApJ, 725, 2324, doi: [`10.1088/0004-637X/725/2/2324`](http://doi.org/10.1088/0004-637X/725/2/2324)

(ref: Carilli_2013) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: Carlstrom_2011) Carlstrom, J. E., Ade, P. A. R., Aird, K. A., et al. 2011, PASP, 123, 568, doi: [`10.1086/659879`](http://doi.org/10.1086/659879)

(ref: Casey_2014) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: Chiang_2013) Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, ApJ, 779, 127, doi: [`10.1088/0004-637X/779/2/127`](http://doi.org/10.1088/0004-637X/779/2/127)

(ref: Dannenbauer_2014) Dannerbauer, H., Kurk, J. D., De Breuck, C., et al. 2014, A&A, 570, A55, doi: [`10.1051/0004-6361/201423771`](http://doi.org/10.1051/0004-6361/201423771)

(ref: Davies_2011) Davies, R., Förster Schreiber, N. M., Cresci, G., et al. 2011, ApJ, 741, 69, doi: [`10.1088/0004-637X/741/2/69`](http://doi.org/10.1088/0004-637X/741/2/69)

(ref: deBlok_2008) de Blok, W. J. G., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2648, doi: [`10.1088/0004-6256/136/6/2648`](http://doi.org/10.1088/0004-6256/136/6/2648)

(ref: De_looze_2011) De Looze, I., Baes, M., Bendo, G. J., Cortese, L., & Fritz, J. 2011, MNRAS, 416, 2712, doi: [`10.1111/j.1365-2966.2011.19223.x`](http://doi.org/10.1111/j.1365-2966.2011.19223.x)

(ref: Dekel_2006) Dekel, A., & Birnboim, Y. 2006, MNRAS, 368, 2, doi: [`10.1111/j.1365-2966.2006.10145.x`](http://doi.org/10.1111/j.1365-2966.2006.10145.x)

(ref: Dekel_2014) Dekel, A., & Burkert, A. 2014, MNRAS, 438, 1870, doi: [`10.1093/mnras/stt2331`](http://doi.org/10.1093/mnras/stt2331)

(ref: Dekel_2020a) Dekel, A., Ginzburg, O., Jiang, F., et al. 2020, MNRAS, 493, 4126, doi: [`10.1093/mnras/staa470`](http://doi.org/10.1093/mnras/staa470)

(ref: Dekel_2009a) Dekel, A., Sari, R., & Ceverino, D. 2009a, ApJ, 703, 785, doi: [`10.1088/0004-637X/703/1/785`](http://doi.org/10.1088/0004-637X/703/1/785)

(ref: Dekel_2009b) Dekel, A., Birnboim, Y., Engel, G., et al. 2009b, Nature, 457, 451, doi: [`10.1038/nature07648`](http://doi.org/10.1038/nature07648)

(ref: 3db_online) Di Teodoro, E. 2015, 3D-BAROLO Documentation. <https://bbarolo.readthedocs.io/en/latest/>

(ref: 3db_2015) Di Teodoro, E. M., & Fraternali, F. 2015, MNRAS, 451, 3021, doi: [`10.1093/mnras/stv1213`](http://doi.org/10.1093/mnras/stv1213)

(ref: Teodoro_2016) Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016, A&A, 594, A77, doi: [`10.1051/0004-6361/201628315`](http://doi.org/10.1051/0004-6361/201628315)

(ref: Eales_2010) Eales, S., Dunne, L., Clements, D., et al. 2010, PASP, 122, 499, doi: [`10.1086/653086`](http://doi.org/10.1086/653086)

(ref: Fall_1980) Fall, S. M., & Efstathiou, G. 1980, MNRAS, 193, 189, doi: [`10.1093/mnras/193.2.189`](http://doi.org/10.1093/mnras/193.2.189)

(ref: Foerster_schreiber_2020) Förster Schreiber, N. M., & Wuyts, S. 2020, ARA&A, 58, 661, doi: [`10.1146/annurev-astro-032620-021910`](http://doi.org/10.1146/annurev-astro-032620-021910)

(ref: Foerster_Schreiber_2009) Förster Schreiber, N. M., Genzel, R., Bouché, N., et al. 2009, ApJ, 706, 1364, doi: [`10.1088/0004-637X/706/2/1364`](http://doi.org/10.1088/0004-637X/706/2/1364)

(ref: Foerster_Schreiber_2018) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21, doi: [`10.3847/1538-4365/aadd49`](http://doi.org/10.3847/1538-4365/aadd49)

(ref: Franx_1991) Franx, M., Illingworth, G., & de Zeeuw, T. 1991, ApJ, 383, 112, doi: [`10.1086/170769`](http://doi.org/10.1086/170769)

(ref: Fratenalli_2021) Fraternali, F., Karim, A., Magnelli, B., et al. 2021, A&A, 647, A194, doi: [`10.1051/0004-6361/202039807`](http://doi.org/10.1051/0004-6361/202039807)

(ref: Ginolfi_2020) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90, doi: [`10.1051/0004-6361/201936872`](http://doi.org/10.1051/0004-6361/201936872)

(ref: Grand_2017) Grand, R. J. J., Gómez, F. A., Marinacci, F., et al. 2017, MNRAS, 467, 179, doi: [`10.1093/mnras/stx071`](http://doi.org/10.1093/mnras/stx071)

(ref: Gullberg_2019) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956, doi: [`10.1093/mnras/stz2835`](http://doi.org/10.1093/mnras/stz2835)

(ref: Hayward_2017) Hayward, C. C., & Hopkins, P. F. 2017, MNRAS, 465, 1682, doi: [`10.1093/mnras/stw2888`](http://doi.org/10.1093/mnras/stw2888)

(ref: Herrera_Camus_2015) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1, doi: [`10.1088/0004-637X/800/1/1`](http://doi.org/10.1088/0004-637X/800/1/1)

(ref: Hill_2020) Hill, R., Chapman, S., Scott, D., et al. 2020, MNRAS, 495, 3124, doi: [`10.1093/mnras/staa1275`](http://doi.org/10.1093/mnras/staa1275)

(ref: Hill_2022) Hill, R., Chapman, S., Phadke, K. A., et al. 2022, MNRAS, 512, 4352, doi: [`10.1093/mnras/stab3539`](http://doi.org/10.1093/mnras/stab3539)

(ref: Hodge_2012) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11, doi: [`10.1088/0004-637X/760/1/11`](http://doi.org/10.1088/0004-637X/760/1/11)

(ref: Jones_2021) Jones, G. C., Vergani, D., Romano, M., et al. 2021, MNRAS, 507, 3540, doi: [`10.1093/mnras/stab2226`](http://doi.org/10.1093/mnras/stab2226)

(ref: Jozsa_2007) Józsa, G. I. G., Kenn, F., Klein, U., & Oosterloo, T. A. 2007, A&A, 468, 731, doi: [`10.1051/0004-6361:20066164`](http://doi.org/10.1051/0004-6361:20066164)

(ref: Keres_2005) Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2, doi: [`10.1111/j.1365-2966.2005.09451.x`](http://doi.org/10.1111/j.1365-2966.2005.09451.x)

(ref: King_2015) King, A., & Pounds, K. 2015, ARA&A, 53, 115, doi: [`10.1146/annurev-astro-082214-122316`](http://doi.org/10.1146/annurev-astro-082214-122316)

(ref: Kohandel_2019) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2019, MNRAS, 487, 3007, doi: [`10.1093/mnras/stz1486`](http://doi.org/10.1093/mnras/stz1486)

(ref: Kohandel_2023) —. 2023, arXiv e-prints, arXiv:2311.05832, doi: [`10.48550/arXiv.2311.05832`](http://doi.org/10.48550/arXiv.2311.05832)

(ref: Krajnovic_2006) Krajnović, D., Cappellari, M., de Zeeuw, P. T., & Copin, Y. 2006, MNRAS, 366, 787, doi: [`10.1111/j.1365-2966.2005.09902.x`](http://doi.org/10.1111/j.1365-2966.2005.09902.x)

(ref: Kretschmer_2022) Kretschmer, M., Dekel, A., & Teyssier, R. 2022, MNRAS, 510, 3266, doi: [`10.1093/mnras/stab3648`](http://doi.org/10.1093/mnras/stab3648)

(ref: Krumholz_2018) Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS, 477, 2716, doi: [`10.1093/mnras/sty852`](http://doi.org/10.1093/mnras/sty852)

(ref: Lagache_2018) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130, doi: [`10.1051/0004-6361/201732019`](http://doi.org/10.1051/0004-6361/201732019)

(ref: Lelli_2018) Lelli, F., De Breuck, C., Falkendal, T., et al. 2018, MNRAS, 479, 5440, doi: [`10.1093/mnras/sty1795`](http://doi.org/10.1093/mnras/sty1795)

(ref: Lelli_2021) Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713, doi: [`10.1126/science.abc1893`](http://doi.org/10.1126/science.abc1893)

(ref: Lelli_2016) Lelli, F., McGaugh, S. S., & Schombert, J. M. 2016, AJ, 152, 157, doi: [`10.3847/0004-6256/152/6/157`](http://doi.org/10.3847/0004-6256/152/6/157)

(ref: Litke_2019) Litke, K. C., Marrone, D. P., Spilker, J. S., et al. 2019, ApJ, 870, 80, doi: [`10.3847/1538-4357/aaf057`](http://doi.org/10.3847/1538-4357/aaf057)

(ref: Madau_2014) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: MartinezGarcia_2023) Martı́nez-Garcı́a, A. M., del Pino, A., & Aparicio, A. 2023, MNRAS, 518, 3083, doi: [`10.1093/mnras/stac3305`](http://doi.org/10.1093/mnras/stac3305)

(ref: McMullin_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miley_2008) Miley, G., & De Breuck, C. 2008, A&ARv, 15, 67, doi: [`10.1007/s00159-007-0008-z`](http://doi.org/10.1007/s00159-007-0008-z)

(ref: Miller_2018) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469, doi: [`10.1038/s41586-018-0025-2`](http://doi.org/10.1038/s41586-018-0025-2)

(ref: Mocanu_2013) Mocanu, L. M., Crawford, T. M., Vieira, J. D., et al. 2013, ApJ, 779, 61, doi: [`10.1088/0004-637X/779/1/61`](http://doi.org/10.1088/0004-637X/779/1/61)

(ref: Murdin_2001) Murdin, P. 2001, Encyclopedia of Astronomy & Astrophysics (CRC Press). <https://books.google.co.in/books?id=R5dBEAAAQBAJ>

(ref: Neeleman_2020) Neeleman, M., Prochaska, J. X., Kanekar, N., & Rafelski, M. 2020, Nature, 581, 269, doi: [`10.1038/s41586-020-2276-y`](http://doi.org/10.1038/s41586-020-2276-y)

(ref: Neri_2014) Neri, R., Downes, D., Cox, P., & Walter, F. 2014, A&A, 562, A35, doi: [`10.1051/0004-6361/201322528`](http://doi.org/10.1051/0004-6361/201322528)

(ref: Oteo_2016) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34, doi: [`10.3847/0004-637X/827/1/34`](http://doi.org/10.3847/0004-637X/827/1/34)

(ref: Oteo_2018) —. 2018, ApJ, 856, 72, doi: [`10.3847/1538-4357/aaa1f1`](http://doi.org/10.3847/1538-4357/aaa1f1)

(ref: Overzier_2016) Overzier, R. A. 2016, A&ARv, 24, 14, doi: [`10.1007/s00159-016-0100-3`](http://doi.org/10.1007/s00159-016-0100-3)

(ref: Pallottini_2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621, doi: [`10.1093/mnras/stac1281`](http://doi.org/10.1093/mnras/stac1281)

(ref: Herschel_2010) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1, doi: [`10.1051/0004-6361/201014759`](http://doi.org/10.1051/0004-6361/201014759)

(ref: Pillepich_2019) Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196, doi: [`10.1093/mnras/stz2338`](http://doi.org/10.1093/mnras/stz2338)

(ref: Planck_2016) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13, doi: [`10.1051/0004-6361/201525830`](http://doi.org/10.1051/0004-6361/201525830)

(ref: Posses_2023) Posses, A. C., Aravena, M., González-López, J., et al. 2023, A&A, 669, A46, doi: [`10.1051/0004-6361/202243399`](http://doi.org/10.1051/0004-6361/202243399)

(ref: Rees_1977) Rees, M. J., & Ostriker, J. P. 1977, MNRAS, 179, 541, doi: [`10.1093/mnras/179.4.541`](http://doi.org/10.1093/mnras/179.4.541)

(ref: Remus_2022) Remus, R.-S., Dolag, K., & Dannerbauer, H. 2022, arXiv e-prints, arXiv:2208.01053. [`https://arxiv.org/abs/2208.01053`](https://arxiv.org/abs/2208.01053)

(ref: Rennehan_2020) Rennehan, D., Babul, A., Hayward, C. C., et al. 2020, MNRAS, 493, 4607, doi: [`10.1093/mnras/staa541`](http://doi.org/10.1093/mnras/staa541)

(ref: Rizzo_2022) Rizzo, F., Kohandel, M., Pallottini, A., et al. 2022, A&A, 667, A5, doi: [`10.1051/0004-6361/202243582`](http://doi.org/10.1051/0004-6361/202243582)

(ref: Rizzo_2021) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952, doi: [`10.1093/mnras/stab2295`](http://doi.org/10.1093/mnras/stab2295)

(ref: Rizzo_2020) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201, doi: [`10.1038/s41586-020-2572-6`](http://doi.org/10.1038/s41586-020-2572-6)

(ref: Rogstad_1974) Rogstad, D. H., Lockhart, I. A., & Wright, M. C. H. 1974, ApJ, 193, 309, doi: [`10.1086/153164`](http://doi.org/10.1086/153164)

(ref: Roman_Oliviera_2023) Roman-Oliveira, F., Fraternali, F., & Rizzo, F. 2023, MNRAS, 521, 1045, doi: [`10.1093/mnras/stad530`](http://doi.org/10.1093/mnras/stad530)

(ref: Romanowsky_2012) Romanowsky, A. J., & Fall, S. M. 2012, ApJS, 203, 17, doi: [`10.1088/0067-0049/203/2/17`](http://doi.org/10.1088/0067-0049/203/2/17)

(ref: Rotermund_2021) Rotermund, K. M., Chapman, S. C., Phadke, K. A., et al. 2021, MNRAS, 502, 1797, doi: [`10.1093/mnras/stab103`](http://doi.org/10.1093/mnras/stab103)

(ref: Sellwood_2015) Sellwood, J. A., & Spekkens, K. 2015, arXiv e-prints, arXiv:1509.07120. [`https://arxiv.org/abs/1509.07120`](https://arxiv.org/abs/1509.07120)

(ref: Sharda_2019) Sharda, P., da Cunha, E., Federrath, C., et al. 2019, MNRAS, 487, 4305, doi: [`10.1093/mnras/stz1543`](http://doi.org/10.1093/mnras/stz1543)

(ref: Sicking_1997) Sicking, F. 1997, PhD thesis, University of Groningen

(ref: Solomon_1997) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144, doi: [`10.1086/303765`](http://doi.org/10.1086/303765)

(ref: Swaters_2009) Swaters, R. A., Sancisi, R., van Albada, T. S., & van der Hulst, J. M. 2009, A&A, 493, 871, doi: [`10.1051/0004-6361:200810516`](http://doi.org/10.1051/0004-6361:200810516)

(ref: Swinbank_2009) Swinbank, A. M., Webb, T. M., Richard, J., et al. 2009, MNRAS, 400, 1121, doi: [`10.1111/j.1365-2966.2009.15617.x`](http://doi.org/10.1111/j.1365-2966.2009.15617.x)

(ref: Tadaki_2019) Tadaki, K.-i., Kodama, T., Hayashi, M., et al. 2019, PASJ, 71, 40, doi: [`10.1093/pasj/psz005`](http://doi.org/10.1093/pasj/psz005)

(ref: Toomre_1964) Toomre, A. 1964, ApJ, 139, 1217, doi: [`10.1086/147861`](http://doi.org/10.1086/147861)

(ref: Turner_2017) Turner, O. J., Cirasuolo, M., Harrison, C. M., et al. 2017, MNRAS, 471, 1280, doi: [`10.1093/mnras/stx1366`](http://doi.org/10.1093/mnras/stx1366)

(ref: Ubler_2019) Übler, H., Genzel, R., Wisnioski, E., et al. 2019, ApJ, 880, 48, doi: [`10.3847/1538-4357/ab27cc`](http://doi.org/10.3847/1538-4357/ab27cc)

(ref: van_der_Hulst_1992) van der Hulst, J. M., Terlouw, J. P., Begeman, K. G., Zwitser, W., & Roelfsema, P. R. 1992, in Astronomical Society of the Pacific Conference Series, Vol. 25, Astronomical Data Analysis Software and Systems I, ed. D. M. Worrall, C. Biemesderfer, & J. Barnes, 131

(ref: Vieira_2010) Vieira, J. D., Crawford, T. M., Switzer, E. R., et al. 2010, ApJ, 719, 763, doi: [`10.1088/0004-637X/719/1/763`](http://doi.org/10.1088/0004-637X/719/1/763)

(ref: Vizgan_2022) Vizgan, D., Greve, T. R., Olsen, K. P., et al. 2022, ApJ, 929, 92, doi: [`10.3847/1538-4357/ac5cba`](http://doi.org/10.3847/1538-4357/ac5cba)

(ref: Wagg_2012) Wagg, J., Wiklind, T., Carilli, C. L., et al. 2012, ApJL, 752, L30, doi: [`10.1088/2041-8205/752/2/L30`](http://doi.org/10.1088/2041-8205/752/2/L30)

(ref: Walter_2022) Walter, F., Neeleman, M., Decarli, R., et al. 2022, ApJ, 927, 21, doi: [`10.3847/1538-4357/ac49e8`](http://doi.org/10.3847/1538-4357/ac49e8)

(ref: Weiss_2009) Weiß, A., Kovács, A., Coppin, K., et al. 2009, ApJ, 707, 1201, doi: [`10.1088/0004-637X/707/2/1201`](http://doi.org/10.1088/0004-637X/707/2/1201)

(ref: White_1978) White, S. D. M., & Rees, M. J. 1978, MNRAS, 183, 341, doi: [`10.1093/mnras/183.3.341`](http://doi.org/10.1093/mnras/183.3.341)

(ref: Williamson_2011) Williamson, R., Benson, B. A., High, F. W., et al. 2011, ApJ, 738, 139, doi: [`10.1088/0004-637X/738/2/139`](http://doi.org/10.1088/0004-637X/738/2/139)

(ref: Wisnioski_2015) Wisnioski, E., Förster Schreiber, N. M., Wuyts, S., et al. 2015, ApJ, 799, 209, doi: [`10.1088/0004-637X/799/2/209`](http://doi.org/10.1088/0004-637X/799/2/209)

(ref: Wisnioski_2019) Wisnioski, E., Förster Schreiber, N. M., Fossati, M., et al. 2019, ApJ, 886, 124, doi: [`10.3847/1538-4357/ab4db8`](http://doi.org/10.3847/1538-4357/ab4db8)

(ref: Wootten_2009) Wootten, A., & Thompson, A. R. 2009, IEEE Proceedings, 97, 1463, doi: [`10.1109/JPROC.2009.2020572`](http://doi.org/10.1109/JPROC.2009.2020572)

(ref: Zanella_2018) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976, doi: [`10.1093/mnras/sty2394`](http://doi.org/10.1093/mnras/sty2394)

(ref: Zolotov_2015) Zolotov, A., Dekel, A., Mandelker, N., et al. 2015, MNRAS, 450, 2327, doi: [`10.1093/mnras/stv740`](http://doi.org/10.1093/mnras/stv740)

# Initial values and parameter file for kinematic fitting

CCCCCC Source & NRADII & VROT & VDISP & PA & INC\
& 10 & 612 & 147 & 237 & 67\
& 8 & 212 & 65 & 110 & 49\
& 6 & 408 & 227 & 89 & 47\
& 7 & 448 & 100 & 318 & 58\
& 8 & 540 & 150 & 179 & 64\
& 6 & 218 & 96 & 316 & 46\
& 9 & 175 & 81 & 12 & 53

Table [\[tab:initial_guesses\]](#tab:initial_guesses) presents the number of rings used per source, along with the initial guess for $V{_\mathrm{rot}}$, $\sigma{_\mathrm{disp}}$, $\phi$ and $i$ determined using the methods described in [3.2](#subsec:3Dfitting). Tables [\[tab:keywords_search\]](#tab:keywords_search) and [\[tab:keywords_3dfit\]](#tab:keywords_3dfit) show the sample parameter files used in the `SEARCH` and `3DFIT` tasks. Keywords with blank keywords are those that change with respect to the source and take values provided in Table [\[tab:physical_params\]](#tab:physical_params) and [\[tab:initial_guesses\]](#tab:initial_guesses). Further information about the keyword units can be found in (cite: 3db_online).

|           Keyword | Value      |
|------------------:|:-----------|
|            SEARCH | true       |
|   FLAGROBUSTSTATS | false      |
|         ITERNOISE | true       |
|        SEARCHTYPE | spatial    |
|            SNRCUT | 0          |
|         THRESHOLD | 0.00250050 |
|        FLAGGROWTH | true       |
|         GROWTHCUT | 0          |
|   GROWTHTHRESHOLD | 0.00100020 |
|            MINPIX | 1          |
|       MINCHANNELS | 5          |
|      FLAGADJACENT | true       |
|     THRESHSPATIAL | 1          |
|    THRESHVELOCITY | 1          |
| REJECTBEFOREMERGE | true       |
|   TWOSTAGEMERGING | true       |

: Keywords and values for the `SEARCH` task.

|    Keyword | Value             |
|-----------:|:------------------|
|      3DFIT | true              |
|     NRADII |                   |
|     RADSEP | 0.0968            |
|       XPOS |                   |
|       YPOS |                   |
|       VSYS |                   |
|       VROT |                   |
|       VRAD | 0                 |
|      VDISP |                   |
|        INC |                   |
|         PA |                   |
|         Z0 | 0.029             |
|       FREE | vrot vdisp pa inc |
|       MASK | search            |
|       NORM | azim              |
|   TWOSTAGE | true              |
|    REGTYPE | bezier            |
|    REVERSE | false             |
|     LINEAR | 0.42466           |
|       SIDE | B                 |
| FLAGERRORS | true              |
|     ADRIFT | false             |
|   DELTAINC | 5                 |
|    DELTAPA | 5                 |
|      FTYPE | 1                 |
|        TOL | 0.0001            |
|      WFUNC | 2                 |
|      LTYPE | 3                 |
|      CDENS | 10                |
|   BIWEIGHT | 3                 |
|   STARTRAD | 0                 |
|   PLOTMASK | false             |
|   NOISERMS | 0                 |
| NORMALCUBE | false             |
|     BADOUT | false             |

: Keywords and values for the `3DFIT` task.

# Kinematic modeling results

Here we show the results from the kinematic modeling using the 3DFIT task. Each source is shown in a $2\ensuremath{''} \times 2\ensuremath{''}$ ($3\ensuremath{''} \times3\ensuremath{''}$ for C1) cut-out where

- row 1 shows the data, model, and residual moment-0 map. The black cross marks the kinematic center, and the black ellipse denotes the maximum radius of analysis. The elliptical $0.225\ensuremath{''} \times 0.166\ensuremath{''}$ beam is shown in the bottom-left corner. The red contour is at $0.2\% \mathrm{[C\textsc{ii}]_{peak}}$.

- row 2 shows the data, model, and residual moment-1 map. Here, the moment-1 map is the line-of-sight rotation velocity map corrected for the systemic velocity with respect to $z = 4.303$. The white circles mark the kinematic major axis of the galaxy ($\phi$).

- row 3 shows the data, model, and residual moment 2 map, not corrected for beam smearing.

- row 4, columns 1 and 2 are the residual major-axis and minor-axis position-velocity maps, extracted along $\phi$ and $\phi-90\ensuremath{^\circ}$ respectively. The blue contours are at $3\sigma_{\mathrm{[C\textsc{ii}],\,RMS}}$, and the grey contours are at $-3\sigma_{\mathrm{[C\textsc{ii}],\,RMS}}$.

- row 4, column 3 shows the inclination angle fitting. The first stage is shown in gray, while the second stage is in red.

- row 5 shows the position angle, rotation velocity and velocity dispersion fitting in columns 1, 2 and 3 respectively. The first stage is shown in gray, and the second stage is shown in red.

In all images, North is up and East is to the left.

[^1]: Nyquist sampling is when the synthesized beam is sampled $\approx2.4$ times.

[^2]: [Encyclopedia of Mathematics](https://encyclopediaofmath.org/wiki/Bézier_curve)

[^3]: equation 20 in their paper, setting $Q_{\mathrm{turb}} = 1$

</paper>

Write the methods card for this paper.