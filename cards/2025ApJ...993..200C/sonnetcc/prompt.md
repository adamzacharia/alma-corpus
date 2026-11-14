# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...993..200C\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...993..200C",
 "title": "The Hourglass-shaped Magnetic Fields and Dust Filaments in the HH 211 Protostellar Envelope",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Choi, Youngwoo",
 "n_authors": 7,
 "arxiv_id": "2509.25764",
 "doi": "10.3847/1538-4357/ae0710",
 "alma_projects_linked_by_archive": [
  "2016.1.00604.S",
  "2017.1.01310.S"
 ]
}
```

Paper text:
<paper>
# The Hourglass-shaped Magnetic Fields and Dust Filaments in the HH 211 Protostellar Envelope

## Abstract

Magnetic fields influence the structure and evolution of protostellar systems, thus understanding their role is essential for probing the earliest stages of star formation. We present ALMA Band 3 and 6 polarized continuum observations at $\sim$0.5$^{\prime \prime}$ resolution toward the Class 0 protostellar system HH 211. Three dust filaments ($\sim$4000 au in length) are found in the HH 211 protostellar envelope, two of which are aligned with core-scale ($\sim$10,000 au) magnetic fields detected by previous JCMT observations. This result suggests that the formation of the dust filaments may be influenced by magnetic fields. In the inner envelope ($\sim$1000 au), we detect a clear hourglass-shaped magnetic field morphology near the protostar and toroidal fields along the outflow directions. We also estimate the line-of-sight–averaged temperature and column density distributions in the inner envelope and find that the temperature is higher in the east, while the column density is enhanced in the southern and western regions. The southern dense regions of the inner envelope may trace either outflow cavity walls, due to their alignment with the outflow, or possible infalling channels in the midplane, given the close correspondence between the observed magnetic fields and the predicted infall trajectories.

# Introduction

Stars form through the gravitational collapse of molecular cloud cores (cite: Shu_1987; Larson_2003; McKee_2007). Traditionally, it has been considered that core materials collapse isotropically into the central part of the core, forming a protostar (cite: Shu_1977). However, recent high-resolution observations have revealed numerous asymmetric accretion channels around various young protostellar systems, known as streamers (cite: Pineda_2023). Streamers have been observed around young stellar objects from the youngest Class 0 to older Class II disks, indicating gravitational collapse occurs in asymmetrical ways during the star formation process (cite: Le_Gouellec_2019; Yen_2019; Pineda_2020; Cabedo_2021; Thieme_2022; Murillo_2022; Garufi_2022; Valdivia_Mena_2022; Valdivia_Mena_2023; Leej_2023; Kido_2023; Aso_2023; Flores_2023; Cacciapuoti_2024; Tychoniec_2024; Codella_2024; Riaz_2024; Hales_2024).

Several numerical simulations have shown that streamers are naturally caused by turbulence in the parent cloud cores (cite: Walch_2010; Seifried_2013; Seifried_2015). In the presence of turbulence, the gravitational collapse of cores occurs asymmetrically, as observed in the simulations (cite: Matsumoto_2017; Lam_2019; Hennebelle_2020; Tu_2023; Heigl_2024). Additionally, since star-forming cores are embedded within the filamentary structures of molecular clouds (cite: Andre_2014), streamers could also be generated through interactions with the surrounding medium (cite: Kuffmeier_2017; Bate_2018; Kuffmeier_2023). Collisions between cores or filaments present another possible mechanism for forming asymmetric structures around protostellar systems (cite: Yano_2024).

Another important feature of star-forming cores is that they are threaded with ambient magnetic fields (cite: Crutcher_2012). As core material collapses toward the center, the magnetic fields are dragged inward, forming a classical hourglass shape (cite: Mestel_1966; Mouschovias_1976; Galli_1993; Basu_1994; Myers_2018; Myers_2020). Hourglass magnetic fields are observed around several high-mass (cite: Schleuning_1998; Girart_2009; Tang_2009; Qiu_2014; Li_2015) and low-mass protostellar systems (cite: Girart_2006; Stephens_2013; Maury_2018; Kwon_2019). In addition, the magnetic fields near protostars are twisted by rotational motions, forming toroidal fields along the jet directions (cite: Pudritz_2019). These magnetic fields are expected to play a significant role in the formation of protostellar disks, jets, and outflows (cite: Blandford_1982; Machida_2006; Li_2013).

HH 211 is a Class 0 protostellar system located in the IC 348 star-forming region of the Perseus molecular cloud complex. The distance to HH 211 is about 300 pc (cite: Ortiz_Le_n_2018; Zucker_2018), and its bolometric temperature is 27 K (cite: Tobin_2016). HH 211 was first discovered through the observation of its molecular hydrogen jets (cite: McCaughrean_1994), and subsequent observations revealed a highly collimated jet and outflow with distinct knot structures (cite: Lee_2009; Jhan_2016; Jhan_2021; Ray_2023). Possible toroidal magnetic fields along the jet have also been detected through SiO polarization observations (cite: Lee_2018a). A thick, nearly edge-on Keplerian disk, approximately 20 au in size, is embedded within the protostellar envelope (cite: Lee_2018b; Lee_2023). The total mass of the central protostar and embedded disk is estimated to be $\sim$0.08 $M_{\odot}$ (cite: Lee_2019). Infalling and rotating motions are observed in the HH 211 protostellar envelope (cite: Tanner_2011; Lee_2019), and the mass of the HH 211 core ($\sim$10,000 au scale) is about 2.5 $M_{\odot}$ (cite: Yen_2023; Choi_2024).

In this paper, we study the magnetic fields and physical properties within the HH 211 protostellar envelope. We present ALMA Band 3 ($\sim$97.5 GHz) and Band 6 ($\sim$233 GHz) polarization observations toward the HH 211 protostellar system. Observations and data reductions are described in Section [2](#sec:observations). In Section [3](#sec:results), we present observational results. We discuss physical properties of HH 211 in Section [4](#sec:discussions) and summarize our conclusions in Section [5](#sec:conclusion).

# Observations

## ALMA Band 3

HH 211 was observed by ALMA in Band 3 from December 14 to 26, 2017 (2017.1.01310.S, PI: Woojin Kwon). The minimum and maximum baseline lengths are about 4 $k\lambda$ and 1100 $k\lambda$, respectively. The maximum recoverable scale ($\theta_{\mathrm{MRS}}$) is about 31$^{\prime \prime}$. We used CASA to calibrate the raw data. J0522+3627 and J0510+1800 were used for bandpass and polarization calibrations during individual executions, while J0237+2848 and J0341+3352 were used to calibrate flux and phase, respectively. We also performed phase-only self-calibration using the Stokes $I$ map with solution intervals of 300 s to reduce the noise in the final Stokes $I$, $Q$, and $U$ maps. The resulting peak SNR for Stokes $I$ is 753. We made images with the CASA $tclean$ task using a Briggs weighting with robust parameters of 0.5 and 2.0. With a robust parameter of 0.5, the resulting beam size is $0.514^{\prime \prime} \times 0.337^{\prime \prime}$ (PA =$-28.9^{\circ}$), and the rms noises of final Stokes $I$, $Q$, and $U$ maps are $9.0 \times 10^{-3}$ mJy beam$^{-1}$, $5.8 \times 10^{-3}$ mJy beam$^{-1}$, and $5.8 \times 10^{-3}$ mJy beam$^{-1}$, respectively. With a robust parameter of 2.0, the resulting beam size is $0.754^{\prime \prime} \times 0.536^{\prime \prime}$ (PA =$-31.1^{\circ}$), and the rms noises of final Stokes $I$, $Q$, and $U$ maps are $1.0 \times 10^{-2}$ mJy beam$^{-1}$, $6.0 \times 10^{-3}$ mJy beam$^{-1}$, and $6.0 \times 10^{-3}$ mJy beam$^{-1}$, respectively. Polarized intensity is debiased with $PI = \sqrt{Q^2 + U^2 - \sigma_{QU}^2}$, where $\sigma_{QU}$ is the rms noise of Stokes $Q$ and $U$. The rms noises of the polarized intensity are $8.2 \times 10^{-3}$ mJy beam$^{-1}$ and $7.5 \times 10^{-3}$ mJy beam$^{-1}$ for robust parameters of 0.5 and 2.0, respectively. The Stokes $V$ parameter is not detected, with an rms noise of $5.8 \times 10^{-3}$ mJy beam$^{-1}$ for a robust parameter of 0.5.

## ALMA Band 6

HH 211 was observed by ALMA in Band 6 from November 12 to 14, 2016 (2016.1.00604.S, PI: Woojin Kwon). The minimum and maximum baseline lengths are about 9 $k\lambda$ and 825 $k\lambda$, respectively. The maximum recoverable scale ($\theta_{\mathrm{MRS}}$) is about 14$^{\prime \prime}$. We used CASA to calibrate the raw data. J0238+1636 was used for flux and polarization calibration, while J0237+2848 and J0336+3218 were used to calibrate bandpass and phase, respectively. We also performed phase-only self-calibration using the Stokes $I$ map with solution intervals of 300 s, 100 s, and 30 s to reduce the noise in the final Stokes $I$, $Q$, and $U$ maps. The resulting peak SNR for Stokes $I$ is 1166. We made images with the CASA $tclean$ task using a Briggs weighting with robust parameters of 0.5 and 2.0. With a robust parameter of 0.5, the resulting beam size is $0.587^{\prime \prime} \times 0.355^{\prime \prime}$ (PA = $15.1^{\circ}$), and the rms noises of Stokes $I$, $Q$, and $U$ maps are $4.5 \times 10^{-2}$ mJy beam$^{-1}$, $1.3 \times 10^{-2}$ mJy beam$^{-1}$, and $1.3 \times 10^{-2}$ mJy beam$^{-1}$, respectively. With a robust parameter of 2.0, the resulting beam size is $0.742^{\prime \prime} \times 0.471^{\prime \prime}$ (PA = $9.9^{\circ}$), and the rms noises of final Stokes $I$, $Q$, and $U$ maps are $3.5 \times 10^{-2}$ mJy beam$^{-1}$, $1.3 \times 10^{-2}$ mJy beam$^{-1}$, and $1.3 \times 10^{-2}$ mJy beam$^{-1}$, respectively. Polarized intensity is debiased with $PI = \sqrt{Q^2 + U^2 - \sigma_{QU}^2}$, where $\sigma_{QU}$ is the rms noises of Stokes $Q$ and $U$. The rms noises of the polarized intensity are $1.9 \times 10^{-2}$ mJy beam$^{-1}$ and $1.2 \times 10^{-2}$ mJy beam$^{-1}$ for robust parameter of 0.5 and 2.0, respectively. The Stokes $V$ parameter is not detected, with an rms noise of $1.2 \times 10^{-2}$ mJy beam$^{-1}$ for a robust parameter of 0.5.

## JCMT 850 $\mu$m

The HH 211 core was observed using the JCMT SCUBA-2 camera with the POL-2 polarimeter between July (Project ID: M17AP073, PI: Woojin Kwon) and September (Project ID: M17BP058, PI: Woojin Kwon) 2017, and between October 2019 and February 2020 as part of the BISTRO survey (Project ID: M17BL011) (cite: Ward_Thompson_2017). We used 850 $\mu$m polarization continuum data to infer core-scale ($\sim$10,000 au) magnetic fields around HH 211. Detailed data reduction process is described in (cite: Choi_2024). The beam size of the JCMT observations is 14.6$^{\prime \prime}$, and the rms noises of final Stokes $I$, $Q$, and $U$ maps at 850 $\mu$m are 3.3 mJy beam$^{-1}$, 2.5 mJy beam$^{-1}$, and 2.5 mJy beam$^{-1}$, respectively.

# Results

## Dust Continuum and Core-scale Magnetic Field

Figure [1](#fig:cont_band3) shows dust continuum toward the HH 211 envelope in Band 3 (97.5 GHz) with a robust parameter of 2.0. We detect three dust filaments, each about 4000 au in scale, in the HH 211 envelope. These filaments are located in the southern, western, and northwestern regions of the HH 211 envelope, all directed toward the central embedded protostar. The intensity of the filaments is the strongest in the southern filament and the faintest in the northwestern filament. For comparison, dust continuum emission in Band 6 with a robust parameter of 2.0 is presented in Appendix [6](#sec:app).

The left panel of Figure [2](#fig:jcmt) shows the core-scale ($\sim$10,000 au) magnetic field orientations around HH 211 observed by JCMT with the POL-2 polarimeter. The right panel of Figure [2](#fig:jcmt) shows a zoomed-in view of the core-scale magnetic fields overlaid with ALMA Band 3 continuum. Notably, the southern and northwestern filaments are well aligned with the core-scale magnetic fields. This alignment suggests that the formation of southern and northwestern filaments is likely influenced by the magnetic fields. If these filaments are infalling mass streams, they could be guided by the magnetic fields. In contrast, the western filament is almost perpendicular to the core-scale magnetic fields. Instead, it is directed toward the asymmetrically extended part of the core, as shown in the right panel of Figure [2](#fig:jcmt).

Figure [3](#fig:continuum) shows dust continuum toward the HH 211 envelope in Band 3 (97.5 GHz) and Band 6 (233 GHz) with a robust parameter of 0.5. Since the size of the embedded disk is about 20 au (cite: Lee_2018b; Lee_2023), which is smaller than our beam size, the disk is not resolved in our observations. At both frequencies, there is a narrow filamentary structure in the southern part of the envelope, which is connected to the larger southern dust filament shown in Figure [1](#fig:cont_band3).

In addition, the dust continuum is asymmetrically extended toward the southwest direction near the central protostar. (cite: Lee_2009) first reported this feature with SMA observations, suggesting the possibility of a binary companion at $0.3^{\prime \prime}$ to the southwest of HH 211. However, high-resolution ALMA observations did not show any secondary source at the predicted position (cite: Lee_2018b; Lee_2019). This asymmetrically extended envelope might be due to the asymmetric density distributions, as will be discussed in a Section [4](#sec:discussions).

Another feature of the HH 211 envelope is that it is flattened along the east-west direction on a 2000 au scale. The position angle of the minor axis of the flattened envelope is about 165$^{\circ}$. The position angle of the outflow direction is about 116$^{\circ}$, which is nearly perpendicular to the position angle of the embedded disk (cite: Lee_2018b; Segura-Cox_2018), as indicated in Figure [3](#fig:continuum). The outflow direction is tilted by 50$^{\circ}$ relative to the flattened envelope direction on the 2000 au scale. Since the outflow direction, a proxy of the rotation axis, is not aligned with the the short axis of the flattened structure, this may not be the result of rotational motions. Instead, the core-scale ($\sim$10,000 au) magnetic field at the position of the protostar has a position angle of about 155$^{\circ}$, which is more aligned with the flattening axis within 10$^{\circ}$. This suggests that the flattened envelope may be a pseudodisk, possibly formed by the preferential mass accumulation along the ambient magnetic field lines.

## Magnetic Field Morphology

Figure [4](#fig:B_field) shows the inferred plane-of-sky magnetic field orientations toward the HH 211 envelope from Band 3 and Band 6 polarization observations. The plane-of-sky magnetic field orientations are inferred from $90^{\circ}$ rotation of polarization directions. We selected the Band 3 image with a robust parameter of 2.0 and the Band 6 image with a robust parameter of 0.5, as larger-scale magnetic fields are more effectively detected in Band 3, whereas smaller-scale fields are more clearly revealed in Band 6. For Band 3 observations, we represent half-vectors satisfying $I > 3\sigma_{I}$ and $PI > 1.5\sigma_{PI}$, while for Band 6, the criteria are $I > 3\sigma_{I}$ and $PI > 3\sigma_{PI}$. Magnetic field vectors are sampled at intervals of 0.24$^{\prime\prime}$ and 0.32$^{\prime\prime}$ for robust parameters of 0.5 and 2.0, respectively, which are approximately half the beam size of the corresponding observations. Red and blue contours in the right panels indicate red-shifted and blue-shifted CO (2-1) integrated intensities, respectively (cite: Jhan_2021). For comparison, magnetic field orientations from the Band 3 observations with a robust parameter of 0.5 and Band 6 with a robust parameter of 2.0 are presented in Appendix [6](#sec:app).

The left panel of Figure [4](#fig:B_field) shows the magnetic field orientations within the southern and western filaments. In the southern filament, the magnetic fields are aligned with the filament direction, consistent with the core-scale magnetic fields shown in Figure [2](#fig:jcmt). In the case of the western filament, the filament is oriented in the east-west direction. The magnetic fields within the western filament are almost aligned with the filament but slightly tilted toward the northwest. Since the core-scale magnetic fields at the western filament are oriented toward the northwest, as shown in Figure [2](#fig:jcmt), the magnetic field directions within the western filament are likely inherited from the core-scale magnetic fields. If the southern and western filaments are infalling streams toward the central protostars, the observed magnetic field directions might result from the fields dragged by these streams, aligning the field direction with the infalling direction. The magnetic fields within the northwestern filament are not clearly detected in our Band 3 observations and also not in Band 6.

The right panel of Figure [4](#fig:B_field) shows the magnetic field orientations in the HH 211 inner envelope ($\sim500$ au). The magnetic fields in the southern and western parts of the envelope are connected to the magnetic fields in the southern and western filaments shown in the left panel of Figure [4](#fig:B_field). Near the central protostar, we detect clear U-shaped pinched magnetic fields around the blue-shifted outflow axis, as well as a hint of pinched fields around the red-shifted outflow. The pinched fields associated with the red-shifted outflow are more clearly seen in the Band 6 image with a robust parameter of 2.0, shown in the right panel of Figure [14](#fig:B_field_appendix). This represents so-called hourglass-shaped magnetic fields, indicating that infalling materials are well coupled to the magnetic fields, dragging the fields toward the central region. At the center of the HH 211 envelope, the inferred magnetic fields from both Band 3 and Band 6 observations are oriented in the north-south direction, consistent with previous Band 7 (358 GHz) observations (cite: Lee_2019; Yen_2023).

The magnetic field is perpendicular to the outflow directions in the outflow regions. This field morphology is observed in both the red-shifted and blue-shifted outflows, suggesting the presence of toroidal magnetic fields. Previous SiO polarization observations also detected possible toroidal fields on the blue-shifted side of the jet (cite: Lee_2018a). SiO observations trace the inside of the outflow, where dust grains are destroyed by shocks, while dust emission primarily originates from the envelope material in front of and behind the outflow. Therefore, outflow rotation could generate toroidal fields within the outflow regions and also induce the rotation of the envelope, leading to the formation of toroidal fields in the envelope.

## Polarized Intensity and Polarization Fraction

Figure [5](#fig:pol_I) and [6](#fig:pol_frac) show the polarized intensity ($PI$) and polarization fraction toward the HH 211 envelope in Band 3 with a robust parameter of 2.0 (left panel) and in Band 6 with a robust parameter of 0.5 (right panel). The polarized intensity and polarization fraction from the Band 3 observations with a robust parameter of 0.5 and Band 6 with a robust parameter of 2.0 are presented in Appendix [6](#sec:app). In Band 6, the polarized intensity is high in the southern and western parts of the envelope, where it connects with the larger filaments.

The polarization fraction is calculated with $PI/I$, where $I$ represents the Stokes $I$ parameter and $PI$ represent the polarized intensity. In Band 3, the polarization fraction is high in the northern and southern regions near the central protostar. An X-shaped depolarization pattern appears in the Band 6 observations (see the blue regions in the right panel of Figure [6](#fig:pol_frac)). These depolarization regions might represent the boundaries between toroidal fields and pinched hourglass fields, where the plane-of-sky magnetic field directions change abruptly.

## Spectral Index

We investigate the spectral index between Band 3 and 6 observations to study the physical properties of the HH 211 envelope, which will be discussed in Section [4](#sec:discussions). The spectral index of dust continuum emission between two frequencies can be calculated as follows: $$\begin{equation}
\alpha = \frac{\mathrm{log} \hspace{0.08cm} (I_{\nu_{1}}/I_{\nu_{2}})}{\mathrm{log} \hspace{0.08cm} (\nu_{1}/\nu_{2})},
\label{eq:alpha}
\end{equation}$$ where $\nu_{1}$ and $\nu_{2}$ are 233 and 97.5 GHz, respectively. Before estimating the spectral index using Equation [\[eq:alpha\]](#eq:alpha), we matched the $uv$-coverage of the Band 3 and Band 6 observations by adjusting `uvtaper` and `uvrange` parameters during the CASA `tclean` task. In this process, the minimum $uv$-distance is set to 9 $k\lambda$. Figure [7](#fig:spectral_index) presents the Band 3 and Band 6 dust continuum images after matching their $uv$-coverage, and the corresponding spectral index map. The spectral index map is shown where both Band 3 and Band 6 intensities are larger than 3 times their rms noise levels. The spectral index has a decreasing hole structure in the central region where the spectral index becomes 2.5. The spectral index gradually increases outwardly from the center, then decreases again outwardly. Also, the spectral index shows an asymmetric structure with high values in the east and smaller values in the west.

# Analysis and Discussion

## Temperature and Density Distributions

To better understand the observed spectral index structure around HH 211, we formalize the expression for the spectral index. The dust continuum without background radiation is calculated as follows: $$\begin{equation}
I_{\nu} = \int_{0}^{\tau_{\nu}}{B_{\nu}(T)e^{-\tau^{\prime}_{\nu}} d\tau^{\prime}_{\nu}},
\label{eq:radiation}
\end{equation}$$ where $I_{\nu}$ is the intensity, $\tau_{\nu}$ is the optical depth, and $B_{\nu}(T)$ is the blackbody radiation at temperature $T$. The optical depth $\tau_{\nu}$ is calculated as follows: $$\begin{eqnarray}
\tau_{\nu} &=& \kappa_{\nu}^{\prime} \Sigma_{\mathrm{d}}, \\
&=& \kappa_{\nu}^{\prime} \int{\rho_{\mathrm{d}}} \hspace{0.1cm} ds, \\
&=& \mu m_{\mathrm{H}} \kappa_{\nu} \int{n(\mathrm{H}_2)} \hspace{0.1cm} ds, \\
&=& \mu m_{\mathrm{H}} \kappa_{\nu} N (\mathrm{H}_2), 
\label{eq:opt_dep}
\end{eqnarray}$$ where $\kappa_{\nu}^{\prime}$ is the dust opacity, $\kappa_{\nu}$ is the dust opacity divided by gas-to-dust ratio, $\Sigma_{\mathrm{d}}$ is the dust mass column density, $\rho_{\mathrm{d}}$ is the dust density, $\mu$ is the mean molecular weight, $m_\mathrm{H}$ is the mass of a hydrogen atom, $n(\mathrm{H}_2)$ is the number density of molecular hydrogen and $N(\mathrm{H}_2)$ is the column density of molecular hydrogen. Dust opacity has the form of $\kappa_{\nu} \propto \nu^{\beta}$ in the far-IR and mm wavelengths (cite: Hildebrand_1983; Draine_2006), where $\beta$ is the dust opacity spectral index.

Equation [\[eq:radiation\]](#eq:radiation) is simplified through $$\begin{eqnarray}
I_{\nu} &=& \int_{0}^{\tau_{\nu}}{B_{\nu}(T)e^{-\tau^{\prime}_{\nu}} d\tau^{\prime}_{\nu}}, \\
&=& B_{\nu}(\overline{T}_{\mathrm{los}}) \int_{0}^{\tau_{\nu}}{e^{-\tau^{\prime}_{\nu}} d\tau^{\prime}_{\nu}}, \\
&=& B_{\nu}(\overline{T}_{\mathrm{los}})(1-e^{-\tau_{\nu}}),
\label{eq:rad_modified}
\end{eqnarray}$$ where $\overline{T}_{\mathrm{los}}$ is the line-of-sight averaged temperature, assuming uniform temperature along the line-of-sight. The definition of $\overline{T}_{\mathrm{los}}$ becomes as follows: $$\begin{equation}
B_{\nu}(\overline{T}_{\mathrm{los}}) = \frac{\int_{0}^{\tau_{\nu}}{B_{\nu}(T)e^{-\tau^{\prime}_{\nu}} d\tau^{\prime}_{\nu}}}{\int_{0}^{\tau_{\nu}}{e^{-\tau^{\prime}_{\nu}} d\tau^{\prime}_{\nu}}}.
\label{eq:los_temp}
\end{equation}$$

Figure [8](#fig:los_temp) illustrates a cartoon depicting the observation of a protostellar envelope. Generally, the temperature decreases outward from the protostar, leading to a non-uniform temperature along the line-of-sight. The region closest to the protostar ($A$) is warmer than the background ($B$) and foreground ($C$). Since dust emission from the protostellar envelope is optically thin at millimeter wavelengths, the dust continuum traces both the warm material at position $A$ and the cooler material in the background and foreground. As a result, the line-of-sight averaged temperature is lower than the temperature at location $A$.

By substituting Equation [\[eq:rad_modified\]](#eq:rad_modified) into Equation [\[eq:alpha\]](#eq:alpha), the spectral index of the dust continuum emission can be calculated as the sum of two components (cite: Silsbee_2022): $$\begin{eqnarray}
\alpha &=& \alpha_{\mathrm{pl}}(\overline{T}_{\mathrm{los}}) + \frac{\beta \tau_{\nu_1}}{e^{\tau_{\nu_1}}-1}, \\
&=& \alpha_{\mathrm{pl}}(\overline{T}_{\mathrm{los}}) + \beta^{\prime}(\tau_{\nu_1}),
\label{eq:alpha2}
\end{eqnarray}$$ where $\alpha_{\mathrm{pl}}(\overline{T}_{\mathrm{los}})$ is the spectral index of the Planck function at temperature $T = \overline{T}_{\mathrm{los}}$. Figure [9](#fig:alpha) shows the two components of the spectral index between 97.5 GHz and 233 GHz from Equation [\[eq:alpha2\]](#eq:alpha2). The left panel of Figure [9](#fig:alpha) represents $\alpha_{\mathrm{pl}}(\overline{T}_{\mathrm{los}})$ as a function of the line-of-sight averaged temperature ($\overline{T}_{\mathrm{los}}$), while the right panel indicates $\beta^{\prime}(\tau_{\nu_1})$ as a function of the optical depth ($\tau_{\nu_1}$), assuming a dust opacity spectral index ($\beta$) of 1.5 at the protostellar envelope. Note that the dust opacity spectral index in protostellar envelopes is generally observed to be lower than in the diffuse ISM (cite: Kwon_2009; Galametz_2019; Cacciapuoti_2025). Without contamination from other emissions, such as free-free emission or anomalous microwave emission (AME), the spectral index is determined by three factors: the line-of-sight averaged temperature ($\overline{T}_{\mathrm{los}}$), the optical depth ($\tau_{\nu_1}$), and the dust opacity spectral index ($\beta$). As the line-of-sight averaged temperature increases, the spectral index of the Planck function $\alpha_{\mathrm{pl}}(\overline{T}_{\mathrm{los}})$ also increases, asymptotically approaching 2 at high temperatures. This value corresponds to the Rayleigh–Jeans limit of the Planck function at the observing frequencies. In the optically thin regime, the spectral index associated with dust opacity $\beta^{\prime}(\tau_{\nu_1})$ approaches $\beta$ and decreases as the optical depth increases. In the optically thick limit, the spectral index for dust opacity becomes 0. The dust opacity spectral index ($\beta$) can vary based on dust grain size, with smaller grains resulting in higher $\beta$ values, and larger grains resulting in lower $\beta$ (cite: Draine_2006). In the Rayleigh-Jeans and the optically thin limits, Equation [\[eq:alpha2\]](#eq:alpha2) reduces to $\alpha = 2 + \beta$.

The outwardly decreasing spectral index beyond a radius of about 2$^{\prime \prime}$ seen in Figure [7](#fig:spectral_index) is likely caused by the decreasing temperature, as the optical depth decreases outward. The dust opacity spectral index, $\beta$, is also not expected to decrease outward. This suggests that the temperature of the HH 211 envelope is low enough that the Rayleigh-Jeans approximation does not hold. The inward decrease of the spectral index in the central region is likely due to the emission from the optically thick embedded disk. This disk emission might be smoothed out by the beam pattern, increasing optical depth in the central region.

Since the optical depth depends on the dust opacity and the column density (refer to Equation [\[eq:opt_dep\]](#eq:opt_dep)), the dust continuum emission is governed by three parameters: the line-of-sight averaged temperature, the dust opacity, and the column density (refer to Equation [\[eq:rad_modified\]](#eq:rad_modified)). Therefore, by assuming a dust opacity value, the dust continuum depends on the line-of-sight averaged temperature and the column density. To estimate these parameters for the HH 211 envelope, we take $\mu = 2.86$, $\beta=1.5$, $\kappa_{\nu}=0.01$ at 233 GHz assuming the gas-to-dust ratio of 100 (cite: Ossenkopf_1994). We assume that $\beta$ is constant across the region. Then, we solve Equation [\[eq:rad_modified\]](#eq:rad_modified) using the Band 3 and 6 images in Figure [7](#fig:spectral_index), and calculate the line-of-sight averaged temperature and the column density simultaneously.

Figure [10](#fig:temp_dens) shows the estimated line-of-sight averaged temperature and column density of the HH 211 envelope. Note that the line-of-sight averaged temperature is generally lower than the temperature at the projected radial distance from the protostar (refer to Figure [8](#fig:los_temp)). Estimates in the central region are uncertain due to contamination from the embedded disk emission, which increases the optical depth and affects the assumed $\beta$ value. Consequently, the estimated line-of-sight temperature in the center is also uncertain. The line-of-sight temperature pattern is similar to the spectral index, as the spectral index is sensitive to the temperature. The estimated line-of-sight temperature is high in the east and low in the west, with a decrease outward, reaching $\sim$4 K at the boundary. This unexpectedly low temperature may be due to the fact that the continuum emission is resolved out on large scales, which could behave differently at the two bands, even though we match the minimum $uv$-distance. Another possibility is that it could result from the assumed $\beta$ value. If $\beta$ is as low as 1.2, the estimated line-of-sight temperature at the boundary would increase to about 6 K.

The estimated column density also shows an asymmetric structure. The column density is enhanced in the southwestern part of the envelope, corresponding to the asymmetrically extended emission observed in the dust continuum. The estimated column density also reveals narrow channels in the south and the west, consistent with the dust filament locations observed in the dust continuum. This suggests that the dust filaments observed in the dust continuum are likely regions of high density rather than high temperature. In Appendix [7](#sec:modeling), we demonstrate that our analysis can reliably distinguish between temperature and density structures from the dust continuum. If the dust filaments are infalling toward the protostar, our results indicate that accretion in HH 211 occurs preferentially through the southern and western channels, though this should be confirmed with high-resolution spectral line observations. We emphasize that the inferred line-of-sight temperature and column density patterns remain consistent regardless of the assumptions of dust opacity and $\beta$ values. Although different dust opacity values will affect the resulting line-of-sight temperature and column density values, their overall patterns do not change.

## Outflow Cavity Walls or Infalling Streams?

On a $\sim$1000 au scale, the HH 211 envelope shows an enhanced column density toward the south and west (Figure [10](#fig:temp_dens)). The dust continuum emission in both Band 3 and Band 6 reveals an elongated filamentary structure in the southern region (Figure [3](#fig:continuum)), while the magnetic field orientations (Figure [4](#fig:B_field)) are well aligned with this filament. One interpretation is that the southern filament traces the outflow cavity walls. Similar cavity wall filaments have also been reported in other Class 0 protostellar envelopes (cite: Maury_2018; Kwon_2019; Le_Gouellec_2019). Alternatively, the southern filament might not be physically related to the outflow. Its apparent alignment with the outflow could simply result from a projection effect. Instead, the southern feature may correspond to a dense infalling stream that supplies material to the central protostar.

To investigate possible infall motions along the southern filament, we adopt the CMU (Cassen–Moosman–Ulrich) model (cite: Ulrich_1976; Cassen_1981), which describes ballistic, parabolic trajectories resulting from the gravitational collapse of a rotating system. The model assumes an initial solid-body rotation and a central point mass, and it neglects pressure forces and magnetic fields. Infalling streamer trajectories in protostellar envelopes have been successfully identified using the CMU model in several previous studies (cite: Thieme_2022; Kido_2023; Aso_2023). The model contains six free parameters: the central protostellar mass ($M_*$), the centrifugal radius ($R_c$), the disk inclination ($i$), the position angle of the disk (PA), and the initial polar and azimuthal angles ($\theta_0$, $\phi_0$) of the infalling particles. These parameters determine the shape of the parabolic trajectory and the velocity field along the streamline. For details on calculating the CMU model trajectory, refer to Appendix [8](#sec:cmu).

To infer parabolic infall trajectories around HH 211, we adopt a central mass of $M_* + M_{\text{disk}} = 0.08$ $M_\odot$ (cite: Lee_2018b; Lee_2019), a centrifugal radius of $R_c = 42$ au (cite: Lee_2019), and disk inclination and position angle of $i = 98^\circ$ and PA = $64^\circ$, respectively (cite: Lee_2023). For the definitions of inclination and position angle used in this study, refer to Appendix [8](#sec:cmu). With these four parameters fixed, we search for CMU model trajectories that reproduce the southern filamentary structures traced by the dust continuum emission and aligned magnetic field lines. Figure [11](#fig:infall_traj) shows the inferred CMU model trajectories along the southern filament. The red curve corresponds to the trajectory with initial angles $\theta_{0}=90^\circ$ and $\phi_{0}=90^\circ$, while the orange curves represent models with $80^\circ < \theta_{0} < 90^\circ$ and $90^\circ < \phi_{0} < 95^\circ$. The inferred trajectories align well with the observed magnetic field lines. This can be interpreted as magnetic field lines being dragged inward by infalling motions, as shown in previous simulations (cite: Mignon_2021; Tu_2023). Since the inferred trajectories are located near the equatorial plane ($\theta_0=90^{\circ}$), the filament’s apparent association with the outflow could be a projection effect. Upon careful inspection, we find no other sets of initial angles ($\theta_0$, $\phi_0$) that yield trajectories consistent with both the observed dust filamentary structures and the curvature of the magnetic field, apart from those originating near the midplane region ($80^\circ < \theta_0 < 95^\circ$). We note that one cannot arbitrarily obtain infalling trajectories that reproduce any curved field lines simply by varying the initial angles ($\theta_0$, $\phi_0$), given the fixed physical conditions ($M_*$, $R_c$) and viewing geometry ($i$, PA) of the system. The trajectories shown in Figure [11](#fig:infall_traj) are derived under the well-constrained physical parameters of HH 211, and thus support the interpretation that the magnetic field lines could be dragged inward by infall motions.

## Polarized Filaments in Protostellar Envelopes

The polarized intensity shown in the right panel of Figure [5](#fig:pol_I) also highlights filamentary structures in the south. Similar polarized filamentary structures have been observed in various Class 0 protostellar envelopes, such as Ser-emb-8 (cite: Hull_2017), IRAS 16293 (cite: Sadavoy_2018), B335 (cite: Maury_2018), L1448 IRS2 (cite: Kwon_2019), and Serpens SMM1 (cite: Le_Gouellec_2019). (cite: Le_Gouellec_2023) argued that these polarized filaments are associated with outflow cavity walls, suggesting they are produced by enhanced radiation from the protostar onto the outflow cavity walls, which aligns dust grains within the wall. In HH 211, the polarized filaments also coincide with the outflow cavity walls in the plane of the sky. However, our results further indicate that these filaments are associated with the high-density regions, rather than high-temperature regions. Notably, the magnetic field directions observed within the polarized filaments are almost parallel to the filament orientations and directed toward the central protostars (cite: Hull_2017; Sadavoy_2018; Maury_2018; Kwon_2019; Le_Gouellec_2019; Le_Gouellec_2023). For the southern polarized filament in HH 211, this field morphology is consistent with the infall trajectories in the midplane shown in Figure [11](#fig:infall_traj), suggesting that the magnetic fields on $\sim$1000 au scale may be dragged by infalling motions. (cite: Le_Gouellec_2023; Le_Gouellec_2023_2) reported that polarized filaments are also detected in the equatorial planes of protostellar systems, where ordered magnetic fields can produce highly linear polarization. Taken together, the southern polarized filament in HH 211 could therefore correspond either to outflow cavity walls or to dense infalling streams within the midplane.

## Mass Infalling Rate along the Southern Filament

The southern envelope exhibits high column density, and the magnetic field orientations in this region are consistent with a ballistic infall model. This raises the possibility that, if the southern filament indeed traces dense infalling streams along the midplane, such flows could contribute substantially to the overall mass accretion in the HH 211 system. To quantitatively estimate the mass infall rate along the southern filament, we first define a possible southern stream region where the magnetic field orientations are consistent with the modeled ballistic infall trajectories. Figure [12](#fig:stream) shows the defined stream region. We exclude the central part of the envelope ($I > 50\sigma_I$), where the mass is uncertain due to optically thick disk emission being smoothed out by the beam pattern.

Using the column density map shown in the right panel of Figure [10](#fig:temp_dens), the mass of the defined southern stream region is estimated to be $\sim$0.15 $M_\odot$. Alternatively, the mass can be derived directly from the dust continuum emission under the assumption of optically thin thermal emission, using the following relation (cite: Hildebrand_1983):

$$\begin{equation}
M = \frac{F_\nu D^2}{\kappa_{\nu} B_{\nu}(T)},
\label{eq:mass2}
\end{equation}$$ where $F_{\nu}$ is the total flux density, $D$ is the distance to the source, $\kappa_{\nu}$ is the dust opacity, and $B_{\nu}(T)$ is the Planck function at temperature $T$. The integrated flux density within the defined region in Band 6 is 10 mJy. Assuming a dust opacity of $\kappa_{\nu} = 0.01$ cm$^2$ g$^{-1}$ at 233 GHz with a gas-to-dust mass ratio of 100 (cite: Ossenkopf_1994) and a dust temperature in the range $T = 5$–10 K, the inferred total mass is $0.05$–$0.19$ $M_\odot$. It is important to note that the measured dust continuum flux within the defined region may include contributions from background and foreground envelope material in addition to the infalling stream itself. Therefore, the derived mass should be considered an upper limit for the mass of the stream.

The length and velocity of the stream within the defined region are estimated based on the CMU model trajectory. The total length of the stream is approximately 6160 au, and the velocity increases along the path from 0.136 km s$^{-1}$ to 0.306 km s$^{-1}$. The average inward velocity along the stream is calculated using $\bar{v} = \int{v \hspace{0.05cm} dl}/L$, where $v$ is the local infall velocity, $dl$ is a differential segment along the trajectory, and $L$ is the total length of the stream. Using this definition, the average velocity is found to be $\bar{v} = 0.188$ km s$^{-1}$. The mass infall rate along the stream is calculated using $\dot{M} = M / (L/\bar{v})$, where $M$ is the mass of the stream. Using the inferred mass, length, and velocity, the estimated mass infall rate along the defined stream region is $(0.32$–$1.22) \times 10^{-6}$ $M_{\odot}$ yr$^{-1}$. Note that the estimated mass infall rate should be considered an upper limit, as the stream mass represents an upper limit.

The mass accretion rate onto the the central protostar can be estimated using the following relation:

$$\begin{equation}
\dot{M}_{\text{acc}} = \frac{L_{\text{acc}} R_{*}}{G M_{*}},
\label{eq:accretion}
\end{equation}$$ where $L_{\text{acc}}$ is the accretion luminosity, $R_{*}$ is the stellar radius, $M_{*}$ is the stellar mass, and $G$ is the gravitational constant. The bolometric luminosity of the HH 211 system is estimated to be $L_{\text{bol}}\sim$3.6 $L_{\odot}$ (cite: Froebrich_2005). Assuming an accretion luminosity of $0.5–1$ $L_{\text{bol}}$ and a stellar radius of $1–3$ $R_{\odot}$ (cite: Stahler_1988), the resulting mass accretion rate is calculated to be $(0.72–4.30) \times 10^{-6}$ $M_{\odot}$ yr$^{-1}$. The mass infall rate along the southern stream, estimated as $(0.32–1.22) \times 10^{-6}$ $M_{\odot}$ yr$^{-1}$, can account for a significant fraction of this accretion rate. This suggests that if the southern filament indeed represents an infalling stream, it could play a crucial role in supplying mass to the central protostar in the HH 211 system.

## Dynamical Role of Magnetic Fields in the HH 211 System

On the core scale ($\sim$10,000 au), the mass-to-flux ratio of the HH 211 core is estimated to be 1.2–3.7 (cite: Yen_2023) and 0.45–2.20 (cite: Choi_2024). Since these estimates are based on plane-of-sky magnetic field measurements and do not account for the line-of-sight component, they should be considered upper limits. Accordingly, the HH 211 core region on this scale is either magnetically subcritical or near critical, where magnetic fields dominates or balances gravity. Figure [2](#fig:jcmt) indeed shows that the core-scale ($\sim$10,000 au) magnetic field orientation is well aligned with the $\sim$4000 au long southern and northwestern filaments. This alignment is unlikely to result from material dragging the field, as the filament widths are much smaller than the core-scale magnetic field structures, and the field strength on this scale is substantial. Instead, the strong magnetic field likely guides the formation of filamentary structures along its direction. Thus, magnetic fields likely play a significant role in regulating the dynamics of the system on the core scale.

On the inner envelope scale ($\sim$1000 au), the mass-to-flux ratio of the HH 211 envelope region is estimated to be 9.1–32.3 (cite: Yen_2023), indicating that gravity dominates over magnetic forces. The right panel of Figure [4](#fig:B_field) shows an hourglass-shaped magnetic field morphology and possible toroidal components along the outflow direction, likely shaped by gas motions dragging the field lines. In the southern envelope, the magnetic field orientation closely follows the expected infall trajectory along the disk midplane. These results suggest that magnetic fields at this scale are not dynamically dominant and instead follow the kinematic motions of the gas.

Between the core scale ($\sim$10,000 au) and the inner envelope scale ($\sim$1000 au), magnetic flux must be significantly reduced. This extraction may occur through non-ideal MHD effects such as ambipolar diffusion, in which neutral particles drift relative to the magnetic field lines (cite: Mouschovias_1992). Another possibility is mass accumulation along magnetic field lines, which increases the local mass without a corresponding increase in magnetic flux (cite: Vazquez_2011). The alignment of the $\sim$4000 au southern and northwestern filaments with the core-scale magnetic field, together with the inner envelope’s flattened structure perpendicular to the large-scale field, suggests that preferential mass accumulation along field lines could lead to a high mass-to-flux ratio in the inner envelope. This, in turn, would allow infall and rotational motions to become dominant in governing the dynamics of the system. We note that flow along field lines and ambipolar diffusion are not mutually exclusive. They can work together to increase the mass-to-flux ratio at smaller distances.

# Conclusions

We present ALMA Band 3 and Band 6 polarization observations at $\sim$0.5$^{\prime\prime}$ resolution toward the Class 0 protostellar system HH 211. The Band 3 dust continuum emission reveals three filamentary structures, each approximately 4000 au in length, within the HH 211 envelope. Two of these, the southern and northwestern filaments, are well aligned with the core-scale ($\sim$10,000 au) magnetic fields previously detected with JCMT observations. This alignment suggests that the formation of these filamentary structures may have been influenced by the large-scale magnetic field.

The Band 3 polarization observations show that the magnetic field orientations are generally parallel to the southern and western filamentary structures. The magnetic field is not clearly detected in the northwestern filament. On the inner envelope scale ($\sim$1000 au), the Band 6 polarization observations reveal a clear hourglass-shaped magnetic field morphology around the central protostar, and toroidal magnetic fields along the outflow directions. These features suggest that the magnetic fields in the inner envelope are being dragged and shaped by infalling and rotational motions.

We estimate the line-of-sight–averaged temperature and column density distributions in the inner envelope of HH 211 using Band 3 and Band 6 continuum emission. The resulting maps reveal asymmetric temperature and density structures. The temperature is higher in the eastern part of the envelope, while the column density is enhanced in the southern and western regions. These high-density regions are aligned with the larger-scale dust filament directions, suggesting that the filaments correspond to high-density regions within the envelope.

The southern dense region on a $\sim$1000 au scale exhibits strong polarized intensity and well-aligned magnetic field lines. Since it coincides with the outflow locations, this structure may be outflow cavity walls. Alternatively, this could represent an infalling stream, as the magnetic field orientations are closely aligned with the parabolic trajectories predicted by the ballistic infall model. In this interpretation, we suggest that the magnetic fields in the inner envelope ($\sim$1000 au) may be shaped by infalling motions. If the southern dense region indeed corresponds to an infalling stream, the estimated mass infall rate suggests that it could play a significant role in the overall mass accretion onto the central protostar.

We are grateful to the anonymous referee for helpful comments. This work was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (RS-2024-00342488 and RS-2024-00416859). L.W.L. acknowledges support from NSF 2307844. Z.Y.L is supported in part by NASA 80NSSC20K0533, NSF AST-2307199, and the Virginia Institute of Theoretical Astronomy (VITA). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00604 and ADS/JAO.ALMA#2017.1.01310. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA, JCMT

# Software

CASA (cite: CASA_2022), NumPy (cite: Harris_2020), Matplotlib (cite: Hunter_2007), Astropy (cite: Astropy_2013; Astropy_2018; Astropy_2022), SciPy (cite: Virtanen_2020)

# Additional polarization properties from the observations

We present dust continuum toward the HH 211 envelope in Band 6 (233 GHz) with a robust parameter of 2.0. We also present the magnetic field orientations and polarization properties of the HH 211 envelope based on the Band 3 observations with a robust parameter of 0.5 and the Band 6 observations with a robust parameter of 2.0.

# Modeling the HH 211 envelope

We make models and carry out synthetic observations to understand the observed spectral index structure, the estimated line-of-sight temperature, and the column density distributions discussed in Section [4](#sec:discussions). The goal of our modeling is not to derive the best model parameters for the HH 211 envelope. Rather, it is to assess the reliability of our analysis in Section [4](#sec:discussions).

We construct models with an embedded disk and a flattened protostellar envelope. The radius of the disk in our model is 20 au and the height is 10 au with a position angle of $54^{\circ}$ and an inclination of $81^{\circ}$ (cite: Lee_2018b; Lee_2019). We assume uniform density and temperature of the disk since it is not resolved in our observations. We take $\rho_{\text{disk}}=3.0 \times 10^{-14}$ g cm$^{-3}$ , and $T_{\text{disk}} =100$ K (cite: Yen_2023). The density and temperature distributions of the model envelope are as follows:

$$\begin{equation}
\rho_{\mathrm{env}} = \rho_0 \bigg(\frac{r^{\prime}}{r_0}\bigg)^{p},
\label{eq:dens}
\end{equation}$$

$$\begin{equation}
T_{\mathrm{env}} = T_0 \bigg(\frac{r^{\prime}}{r_0}\bigg)^{q},
\label{eq:temp}
\end{equation}$$

$$\begin{equation}
r^{\prime} = \sqrt{x^2 + y^2 + (z/f)^2}.
\label{eq:radius}
\end{equation}$$

+------------------------------+--------------------------------------------+----------------------------------+
| Parameter                    | Description                                | Value                            |
+:=============================+:===========================================+:=================================+
| **Disk Parameters**                                                                                          |
+------------------------------+--------------------------------------------+----------------------------------+
| $\rho_{\mathrm{disk}}$       | Dust mass density in the disk              | $3.0\times 10^{-14}$ g cm$^{-3}$ |
+------------------------------+--------------------------------------------+----------------------------------+
| $T_{\mathrm{disk}}$          | Temperature in the disk                    | 100 K                            |
+------------------------------+--------------------------------------------+----------------------------------+
| $r_{\mathrm{disk}}$          | Radius of the disk                         | 20 au                            |
+------------------------------+--------------------------------------------+----------------------------------+
| $h_{\mathrm{disk}}$          | Height of the disk                         | 10 au                            |
+------------------------------+--------------------------------------------+----------------------------------+
| **Envelope Parameters**                                                                                      |
+------------------------------+--------------------------------------------+----------------------------------+
| $\rho_{0}$                   | Dust mass density at a radius of 100 au    | $3.0\times 10^{-17}$ g cm$^{-3}$ |
+------------------------------+--------------------------------------------+----------------------------------+
| $T_{0}$                      | Temperature at a radius of 100 au          | 20 K                             |
+------------------------------+--------------------------------------------+----------------------------------+
| $p$                          | Power-law index of the density profile     | -1.5                             |
+------------------------------+--------------------------------------------+----------------------------------+
| $q$                          | Power-law index of the temperature profile | -0.65                            |
+------------------------------+--------------------------------------------+----------------------------------+
| $f$                          | Envelope flattening parameter              | 0.7                              |
+------------------------------+--------------------------------------------+----------------------------------+
| **Filament Parameters**                                                                                      |
+------------------------------+--------------------------------------------+----------------------------------+
| $\Delta \rho_{\mathrm{fil}}$ | Filament mass density                      | $6.0\times 10^{-18}$ g cm$^{-3}$ |
+------------------------------+--------------------------------------------+----------------------------------+
| $\Delta T_{\mathrm{fil}}$    | Temperature enhancement                    | 6 K                              |
+------------------------------+--------------------------------------------+----------------------------------+
| $r_{\mathrm{fil}}$           | Filament width                             | 200 au                           |
+------------------------------+--------------------------------------------+----------------------------------+

: The Model Parameters

Both the density and temperature have power-law profiles in our model. We insert the parameter $f = 0.7$ in the $z$ direction to make a flattened envelope. Following the results of (cite: Yen_2023), we define $r_0 = 100$ au and set $\rho_0$ = $3.0\times 10^{-17}$ g cm$^{-3}$, $p=-1.5$, $T_{0}$ = 20 K, $q=-0.65$. The power-law slope of the temperature $q$ in (cite: Yen_2023) is -0.4, but we set $q$ to be -0.65 to match the observational features. The model parameters are summarized in Table [1](#tab:parameters).

We construct two models with filament structures. The first model (Model 1) features a protostellar envelope with dense filaments. In this model, the density is high along the filaments, but the temperature remains consistent with that of the envelope. In contrast, the second model (Model 2) has high temperature along the filaments, corresponding to enhanced temperatures along the outflow cavity wall. Comparing these models to the observations allows us to determine whether the observed asymmetric dust continuum and spectral index are due to dense filaments or high temperatures. We consider two cylindrical filaments: one to the west and one to the south. The filament regions are defined as follows:

$$\begin{equation}
\mathrm{Filament} \hspace{0.05cm} 1: x>0, \hspace{0.15cm} y^2+z^2<r_{\mathrm{fil}}^2,
\label{eq:fila1}
\end{equation}$$

$$\begin{equation}
\mathrm{Filament} \hspace{0.05cm} 2: z<0, \hspace{0.15cm} x^2+y^2<r_{\mathrm{fil}}^2,
\label{eq:fila2}
\end{equation}$$ where $r_{\mathrm{fil}}$ represents the filament width, measured as a radius. We set $r_{\mathrm{fil}}$ to 200 au. For the density-enhanced model (Model 1), we add an additional density $\Delta \rho_{\mathrm{fil}}$ to the filament regions. The dust mass density of the filament is set to $\Delta \rho_{\mathrm{fil}}$ = $6.0\times 10^{-18}$ g cm$^{-3}$. In the temperature-enhanced model (Model 2), we add an additional temperature $\Delta T_{\mathrm{fil}}$ to the filament regions. The additional temperature of the filament regions is set to $\Delta T_{\mathrm{fil}}$ = 6 K. The top panels of Figures [17](#fig:model1) and [18](#fig:model2) show the model temperature and density distributions in the $x-z$ plane ($y=0$).

We run RADMC-3D to generate synthetic images in Band 3 (97.5 GHz) and Band 6 (233 GHz) frequencies (cite: Dullemond_2012). We use Optool to make dust opacity tables (cite: Dominik_2021). The maximum sizes of dust particles are assumed to be 200 $\mu$m in the disk and 10 $\mu$m in the envelope and the filaments. Dust particles have thin icy mantles with MRN distributions in our models. The position angle of the envelope is assumed to be $10^{\circ}$. After making synthetic images in Band 3 and Band 6 frequencies, we calculate the spectral index, the line-of-sight averaged temperature, and the column density using the same methods described in Sections [3](#sec:results) and [4](#sec:discussions).

The middle and bottom panels of Figure [17](#fig:model1) show the synthetic images, the spectral index, the line-of-sight averaged temperature and the column density from the density-enhanced model (Model 1). The western and southern dust filaments are seen in the synthetic images. However, the filamentary structures are not apparent in the spectral index map, which resembles the observed spectral index map. This is because, in the optically thin limit, the density does not affect the spectral index. The general structure of the synthetic spectral index map is similar to the observed spectral index. It reproduces the low spectral index in the center and the decreasing trend outward. The inward decreasing pattern in the central region is attributed to the optically thick disk emission. The black dotted lines in the bottom panels indicate an optical depth of 0.1 at 233 GHz, where spectral index in dust opacity drops abruptly (see the right panel of Figure [9](#fig:alpha)). The outward decreasing trend is due to the lower temperature. The estimated line-of-sight averaged temperature and the column density clearly identify the high-density filaments in the south and west. As with the observations, the estimated values are uncertain in the central region.

The middle and bottom panels of Figure [18](#fig:model2) show the synthetic images, the spectral index, the line-of-sight averaged temperature and the column density from the temperature-enhanced model (Model 2). The western and southern temperature-boosted regions are seen in the synthetic images. In contrast to the density-enhanced model, the filamentary structures are stronger in the Band 6 image than the Band 3 image since the change in intensity with temperature is more sensitive at higher frequencies. The synthetic spectral index map shows high spectral index along the filaments due to high temperatures in the non-Rayleigh-Jeans realm. The estimated line-of-sight averaged temperature and the column density clearly identify the high-temperature regions, though there is some distortion in the column density in the south and west. Overall, the general observed features are more similar to those predicted by the density-enhanced model than by the temperature-enhanced model. Therefore, we suggest that the HH 211 envelope contains dense filaments in the south and the west.

# Inferring the CMU Model Trajectory

The procedure for inferring the CMU model trajectory is as follows. First, we compute the position ($r, \theta, \phi$) and velocity components ($v_r, v_\theta, v_\phi$) in spherical coordinates using Equations (5)–(10) from (cite: Ulrich_1976). These quantities are then converted into Cartesian coordinates, where the disk midplane lies in the $x-y$ plane and the angular momentum vector is aligned with the $+z$-axis. The initial polar angle, $\theta_0$, ranges from $0^\circ$ to $180^\circ$, with $\theta_0 = 0^\circ$ corresponding to a particle initially located along the angular momentum axis, and $\theta_0 = 90^\circ$ corresponding to a particle starting in the disk midplane. The initial azimuthal angle, $\phi_0$, ranges from $0^\circ$ to $360^\circ$.

To transform from the disk frame to the observer frame, where the new $x-y$ plane corresponds to the plane of the sky and the new $z$-axis points along the line of sight, we apply a sequence of rotations. First, we rotate about the $x$-axis by the disk inclination angle $i$. We define $i = 0^\circ$ as a face-on disk with clockwise rotation, which naturally aligns the disk $x-y$ plane with the plane of the sky and the $+z$-axis with the line of sight. The inclination increases as the $x$-axis rotates from the $y$-axis toward the $z$-axis, with $i = 90^\circ$ corresponding to an edge-on disk in which the eastern side (positive $x$) is redshifted. This definition may differ from conventional definitions. The inclination $i$ ranges from $0^\circ$ to $360^\circ$.

After applying the inclination rotation about the $x$-axis, we rotate the system around the $z$-axis by the position angle (PA) of the disk. The PA ranges from $-90^\circ$ to $90^\circ$, where a disk major axis aligned with the $x$-axis corresponds to PA = $0^\circ$, and a major axis oriented in the northeast–southwest direction corresponds to a positive PA. After these two rotations, the position and velocity vectors are fully transformed into the observer’s frame. The resulting $x$ and $y$ components represent the trajectory in the plane-of-sky, while the $v_z$ component corresponds to the line-of-sight velocity.

natexlab

(ref: Andre_2014) André, P., Di Francesco, J., Ward-Thompson, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 27–51, doi: [`10.2458/azu_uapress_9780816531240-ch002`](http://doi.org/10.2458/azu_uapress_9780816531240-ch002)

(ref: Aso_2023) Aso, Y., Kwon, W., Ohashi, N., et al. 2023, ApJ, 954, 101, doi: [`10.3847/1538-4357/ace624`](http://doi.org/10.3847/1538-4357/ace624)

(ref: Astropy_2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy_2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Basu_1994) Basu, S., & Mouschovias, T. C. 1994, ApJ, 432, 720, doi: [`10.1086/174611`](http://doi.org/10.1086/174611)

(ref: Bate_2018) Bate, M. R. 2018, MNRAS, 475, 5618, doi: [`10.1093/mnras/sty169`](http://doi.org/10.1093/mnras/sty169)

(ref: Blandford_1982) Blandford, R. D., & Payne, D. G. 1982, MNRAS, 199, 883, doi: [`10.1093/mnras/199.4.883`](http://doi.org/10.1093/mnras/199.4.883)

(ref: Cabedo_2021) Cabedo, V., Maury, A., Girart, J. M., & Padovani, M. 2021, A&A, 653, A166, doi: [`10.1051/0004-6361/202140754`](http://doi.org/10.1051/0004-6361/202140754)

(ref: Cacciapuoti_2024) Cacciapuoti, L., Macias, E., Gupta, A., et al. 2024, A&A, 682, A61, doi: [`10.1051/0004-6361/202347486`](http://doi.org/10.1051/0004-6361/202347486)

(ref: Cacciapuoti_2025) Cacciapuoti, L., Testi, L., Maury, A. J., et al. 2025, [`https://arxiv.org/abs/2506.06865`](https://arxiv.org/abs/2506.06865)

(ref: CASA_2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Cassen_1981) Cassen, P., & Moosman, A. 1981, Icarus, 48, 353, doi: [`10.1016/0019-1035(81)90051-8`](http://doi.org/10.1016/0019-1035(81)90051-8)

(ref: Choi_2024) Choi, Y., Kwon, W., Pattle, K., et al. 2024, ApJ, 977, 32, doi: [`10.3847/1538-4357/ad88ed`](http://doi.org/10.3847/1538-4357/ad88ed)

(ref: Codella_2024) Codella, C., Podio, L., De Simone, M., et al. 2024, MNRAS, 528, 7383, doi: [`10.1093/mnras/stae472`](http://doi.org/10.1093/mnras/stae472)

(ref: Crutcher_2012) Crutcher, R. M. 2012, ARA&A, 50, 29, doi: [`10.1146/annurev-astro-081811-125514`](http://doi.org/10.1146/annurev-astro-081811-125514)

(ref: Dominik_2021) Dominik, C., Min, M., & Tazaki, R. 2021, , Astrophysics Source Code Library, record ascl:2104.010 [`http://ascl.net/2104.010`](http://ascl.net/2104.010)

(ref: Draine_2006) Draine, B. T. 2006, ApJ, 636, 1114, doi: [`10.1086/498130`](http://doi.org/10.1086/498130)

(ref: Dullemond_2012) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, , Astrophysics Source Code Library, record ascl:1202.015 [`http://ascl.net/1202.015`](http://ascl.net/1202.015)

(ref: Flores_2023) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98, doi: [`10.3847/1538-4357/acf7c1`](http://doi.org/10.3847/1538-4357/acf7c1)

(ref: Froebrich_2005) Froebrich, D. 2005, ApJS, 156, 169, doi: [`10.1086/426441`](http://doi.org/10.1086/426441)

(ref: Galametz_2019) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5, doi: [`10.1051/0004-6361/201936342`](http://doi.org/10.1051/0004-6361/201936342)

(ref: Galli_1993) Galli, D., & Shu, F. H. 1993, ApJ, 417, 220, doi: [`10.1086/173305`](http://doi.org/10.1086/173305)

(ref: Garufi_2022) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104, doi: [`10.1051/0004-6361/202141264`](http://doi.org/10.1051/0004-6361/202141264)

(ref: Girart_2009) Girart, J. M., Beltrán, M. T., Zhang, Q., Rao, R., & Estalella, R. 2009, Science, 324, 1408, doi: [`10.1126/science.1171807`](http://doi.org/10.1126/science.1171807)

(ref: Girart_2006) Girart, J. M., Rao, R., & Marrone, D. P. 2006, Science, 313, 812, doi: [`10.1126/science.1129093`](http://doi.org/10.1126/science.1129093)

(ref: Hales_2024) Hales, A. S., Gupta, A., Ruı́z-Rodrı́guez, D., et al. 2024, ApJ, 966, 96, doi: [`10.3847/1538-4357/ad31a1`](http://doi.org/10.3847/1538-4357/ad31a1)

(ref: Harris_2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Heigl_2024) Heigl, S., Hoemann, E., & Burkert, A. 2024, A&A, 686, A246, doi: [`10.1051/0004-6361/202449154`](http://doi.org/10.1051/0004-6361/202449154)

(ref: Hennebelle_2020) Hennebelle, P., Commerçon, B., Lee, Y.-N., & Charnoz, S. 2020, A&A, 635, A67, doi: [`10.1051/0004-6361/201936714`](http://doi.org/10.1051/0004-6361/201936714)

(ref: Hildebrand_1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hull_2017) Hull, C. L. H., Mocz, P., Burkhart, B., et al. 2017, ApJL, 842, L9, doi: [`10.3847/2041-8213/aa71b7`](http://doi.org/10.3847/2041-8213/aa71b7)

(ref: Hunter_2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Jhan_2016) Jhan, K.-S., & Lee, C.-F. 2016, ApJ, 816, 32, doi: [`10.3847/0004-637X/816/1/32`](http://doi.org/10.3847/0004-637X/816/1/32)

(ref: Jhan_2021) Jhan, K.-S., & Lee, C.-F. 2021, ApJ, 909, 11, doi: [`10.3847/1538-4357/abd6c5`](http://doi.org/10.3847/1538-4357/abd6c5)

(ref: Kido_2023) Kido, M., Takakuwa, S., Saigo, K., et al. 2023, ApJ, 953, 190, doi: [`10.3847/1538-4357/acdd7a`](http://doi.org/10.3847/1538-4357/acdd7a)

(ref: Kuffmeier_2017) Kuffmeier, M., Haugbølle, T., & Nordlund, Å. 2017, ApJ, 846, 7, doi: [`10.3847/1538-4357/aa7c64`](http://doi.org/10.3847/1538-4357/aa7c64)

(ref: Kuffmeier_2023) Kuffmeier, M., Jensen, S. S., & Haugbølle, T. 2023, European Physical Journal Plus, 138, 272, doi: [`10.1140/epjp/s13360-023-03880-y`](http://doi.org/10.1140/epjp/s13360-023-03880-y)

(ref: Kwon_2009) Kwon, W., Looney, L. W., Mundy, L. G., Chiang, H.-F., & Kemball, A. J. 2009, ApJ, 696, 841, doi: [`10.1088/0004-637X/696/1/841`](http://doi.org/10.1088/0004-637X/696/1/841)

(ref: Kwon_2019) Kwon, W., Stephens, I. W., Tobin, J. J., et al. 2019, ApJ, 879, 25, doi: [`10.3847/1538-4357/ab24c8`](http://doi.org/10.3847/1538-4357/ab24c8)

(ref: Lam_2019) Lam, K. H., Li, Z.-Y., Chen, C.-Y., Tomida, K., & Zhao, B. 2019, MNRAS, 489, 5326, doi: [`10.1093/mnras/stz2436`](http://doi.org/10.1093/mnras/stz2436)

(ref: Larson_2003) Larson, R. B. 2003, Reports on Progress in Physics, 66, 1651, doi: [`10.1088/0034-4885/66/10/R03`](http://doi.org/10.1088/0034-4885/66/10/R03)

(ref: Le_Gouellec_2023) Le Gouellec, V. J. M., Maury, A. J., & Hull, C. L. H. 2023a, A&A, 671, A167, doi: [`10.1051/0004-6361/202244865`](http://doi.org/10.1051/0004-6361/202244865)

(ref: Le_Gouellec_2023_2) Le Gouellec, V. J. M., Maury, A. J., Hull, C. L. H., et al. 2023b, A&A, 675, A133, doi: [`10.1051/0004-6361/202245346`](http://doi.org/10.1051/0004-6361/202245346)

(ref: Le_Gouellec_2019) Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106, doi: [`10.3847/1538-4357/ab43c2`](http://doi.org/10.3847/1538-4357/ab43c2)

(ref: Lee_2009) Lee, C.-F., Hirano, N., Palau, A., et al. 2009, ApJ, 699, 1584, doi: [`10.1088/0004-637X/699/2/1584`](http://doi.org/10.1088/0004-637X/699/2/1584)

(ref: Lee_2018a) Lee, C.-F., Hwang, H.-C., Ching, T.-C., et al. 2018a, Nature Communications, 9, 4636, doi: [`10.1038/s41467-018-07143-8`](http://doi.org/10.1038/s41467-018-07143-8)

(ref: Lee_2023) Lee, C.-F., Jhan, K.-S., & Moraghan, A. 2023, ApJL, 951, L2, doi: [`10.3847/2041-8213/acdbca`](http://doi.org/10.3847/2041-8213/acdbca)

(ref: Lee_2018b) Lee, C.-F., Li, Z.-Y., Hirano, N., et al. 2018b, ApJ, 863, 94, doi: [`10.3847/1538-4357/aad2da`](http://doi.org/10.3847/1538-4357/aad2da)

(ref: Lee_2019) Lee, C.-F., Kwon, W., Jhan, K.-S., et al. 2019, ApJ, 879, 101, doi: [`10.3847/1538-4357/ab2458`](http://doi.org/10.3847/1538-4357/ab2458)

(ref: Leej_2023) Lee, J.-E., Matsumoto, T., Kim, H.-J., et al. 2023, ApJ, 953, 82, doi: [`10.3847/1538-4357/acdd5b`](http://doi.org/10.3847/1538-4357/acdd5b)

(ref: Li_2015) Li, H.-B., Yuen, K. H., Otto, F., et al. 2015, Nature, 520, 518, doi: [`10.1038/nature14291`](http://doi.org/10.1038/nature14291)

(ref: Li_2013) Li, Z.-Y., Krasnopolsky, R., & Shang, H. 2013, ApJ, 774, 82, doi: [`10.1088/0004-637X/774/1/82`](http://doi.org/10.1088/0004-637X/774/1/82)

(ref: Machida_2006) Machida, M. N., Inutsuka, S.-i., & Matsumoto, T. 2006, ApJL, 647, L151, doi: [`10.1086/507179`](http://doi.org/10.1086/507179)

(ref: Matsumoto_2017) Matsumoto, T., Machida, M. N., & Inutsuka, S.-i. 2017, ApJ, 839, 69, doi: [`10.3847/1538-4357/aa6a1c`](http://doi.org/10.3847/1538-4357/aa6a1c)

(ref: Maury_2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760, doi: [`10.1093/mnras/sty574`](http://doi.org/10.1093/mnras/sty574)

(ref: McCaughrean_1994) McCaughrean, M. J., Rayner, J. T., & Zinnecker, H. 1994, ApJL, 436, L189, doi: [`10.1086/187664`](http://doi.org/10.1086/187664)

(ref: McKee_2007) McKee, C. F., & Ostriker, E. C. 2007, ARA&A, 45, 565, doi: [`10.1146/annurev.astro.45.051806.110602`](http://doi.org/10.1146/annurev.astro.45.051806.110602)

(ref: Mestel_1966) Mestel, L. 1966, MNRAS, 133, 265, doi: [`10.1093/mnras/133.2.265`](http://doi.org/10.1093/mnras/133.2.265)

(ref: Mignon_2021) Mignon-Risse, R., González, M., Commerçon, B., & Rosdahl, J. 2021, A&A, 652, A69, doi: [`10.1051/0004-6361/202140617`](http://doi.org/10.1051/0004-6361/202140617)

(ref: Mouschovias_1976) Mouschovias, T. C. 1976, ApJ, 207, 141, doi: [`10.1086/154478`](http://doi.org/10.1086/154478)

(ref: Mouschovias_1992) Mouschovias, T. C., & Morton, S. A. 1992, ApJ, 390, 144, doi: [`10.1086/171267`](http://doi.org/10.1086/171267)

(ref: Murillo_2022) Murillo, N. M., van Dishoeck, E. F., Hacar, A., Harsono, D., & Jørgensen, J. K. 2022, A&A, 658, A53, doi: [`10.1051/0004-6361/202141250`](http://doi.org/10.1051/0004-6361/202141250)

(ref: Myers_2018) Myers, P. C., Basu, S., & Auddy, S. 2018, ApJ, 868, 51, doi: [`10.3847/1538-4357/aae695`](http://doi.org/10.3847/1538-4357/aae695)

(ref: Myers_2020) Myers, P. C., Stephens, I. W., Auddy, S., et al. 2020, ApJ, 896, 163, doi: [`10.3847/1538-4357/ab9110`](http://doi.org/10.3847/1538-4357/ab9110)

(ref: Ortiz_Le_n_2018) Ortiz-León, G. N., Loinard, L., Dzib, S. A., et al. 2018, ApJ, 865, 73, doi: [`10.3847/1538-4357/aada49`](http://doi.org/10.3847/1538-4357/aada49)

(ref: Ossenkopf_1994) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Pineda_2020) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158, doi: [`10.1038/s41550-020-1150-z`](http://doi.org/10.1038/s41550-020-1150-z)

(ref: Pineda_2023) Pineda, J. E., Arzoumanian, D., Andre, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 233, doi: [`10.48550/arXiv.2205.03935`](http://doi.org/10.48550/arXiv.2205.03935)

(ref: Pudritz_2019) Pudritz, R. E., & Ray, T. P. 2019, Frontiers in Astronomy and Space Sciences, 6, 54, doi: [`10.3389/fspas.2019.00054`](http://doi.org/10.3389/fspas.2019.00054)

(ref: Qiu_2014) Qiu, K., Zhang, Q., Menten, K. M., et al. 2014, ApJL, 794, L18, doi: [`10.1088/2041-8205/794/1/L18`](http://doi.org/10.1088/2041-8205/794/1/L18)

(ref: Ray_2023) Ray, T. P., McCaughrean, M. J., Caratti o Garatti, A., et al. 2023, Nature, 622, 48, doi: [`10.1038/s41586-023-06551-1`](http://doi.org/10.1038/s41586-023-06551-1)

(ref: Riaz_2024) Riaz, B., Stamatellos, D., & Machida, M. N. 2024, MNRAS, 529, 3601, doi: [`10.1093/mnras/stae724`](http://doi.org/10.1093/mnras/stae724)

(ref: Sadavoy_2018) Sadavoy, S. I., Myers, P. C., Stephens, I. W., et al. 2018, ApJ, 869, 115, doi: [`10.3847/1538-4357/aaef81`](http://doi.org/10.3847/1538-4357/aaef81)

(ref: Schleuning_1998) Schleuning, D. A. 1998, ApJ, 493, 811, doi: [`10.1086/305139`](http://doi.org/10.1086/305139)

(ref: Segura-Cox_2018) Segura-Cox, D. M., Looney, L. W., Tobin, J. J., et al. 2018, ApJ, 866, 161, doi: [`10.3847/1538-4357/aaddf3`](http://doi.org/10.3847/1538-4357/aaddf3)

(ref: Seifried_2013) Seifried, D., Banerjee, R., Pudritz, R. E., & Klessen, R. S. 2013, MNRAS, 432, 3320, doi: [`10.1093/mnras/stt682`](http://doi.org/10.1093/mnras/stt682)

(ref: Seifried_2015) Seifried, D., Banerjee, R., Pudritz, R. E., & Klessen, R. S. 2015, MNRAS, 446, 2776, doi: [`10.1093/mnras/stu2282`](http://doi.org/10.1093/mnras/stu2282)

(ref: Shu_1977) Shu, F. H. 1977, ApJ, 214, 488, doi: [`10.1086/155274`](http://doi.org/10.1086/155274)

(ref: Shu_1987) Shu, F. H., Adams, F. C., & Lizano, S. 1987, ARA&A, 25, 23, doi: [`10.1146/annurev.aa.25.090187.000323`](http://doi.org/10.1146/annurev.aa.25.090187.000323)

(ref: Silsbee_2022) Silsbee, K., Akimkin, V., Ivlev, A. V., et al. 2022, ApJ, 940, 188, doi: [`10.3847/1538-4357/ac978b`](http://doi.org/10.3847/1538-4357/ac978b)

(ref: Stahler_1988) Stahler, S. W. 1988, ApJ, 332, 804, doi: [`10.1086/166694`](http://doi.org/10.1086/166694)

(ref: Stephens_2013) Stephens, I. W., Looney, L. W., Kwon, W., et al. 2013, ApJL, 769, L15, doi: [`10.1088/2041-8205/769/1/L15`](http://doi.org/10.1088/2041-8205/769/1/L15)

(ref: Tang_2009) Tang, Y.-W., Ho, P. T. P., Koch, P. M., et al. 2009, ApJ, 700, 251, doi: [`10.1088/0004-637X/700/1/251`](http://doi.org/10.1088/0004-637X/700/1/251)

(ref: Tanner_2011) Tanner, J. D., & Arce, H. G. 2011, ApJ, 726, 40, doi: [`10.1088/0004-637X/726/1/40`](http://doi.org/10.1088/0004-637X/726/1/40)

(ref: Thieme_2022) Thieme, T. J., Lai, S.-P., Lin, S.-J., et al. 2022, ApJ, 925, 32, doi: [`10.3847/1538-4357/ac382b`](http://doi.org/10.3847/1538-4357/ac382b)

(ref: Tobin_2016) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73, doi: [`10.3847/0004-637X/818/1/73`](http://doi.org/10.3847/0004-637X/818/1/73)

(ref: Tu_2023) Tu, Y., Li, Z.-Y., Lam, K. H., Tomida, K., & Hsu, C.-Y. 2023, arXiv e-prints, arXiv:2307.16774, doi: [`10.48550/arXiv.2307.16774`](http://doi.org/10.48550/arXiv.2307.16774)

(ref: Tychoniec_2024) Tychoniec, Ł., van Gelder, M. L., van Dishoeck, E. F., et al. 2024, A&A, 687, A36, doi: [`10.1051/0004-6361/202348889`](http://doi.org/10.1051/0004-6361/202348889)

(ref: Ulrich_1976) Ulrich, R. K. 1976, ApJ, 210, 377, doi: [`10.1086/154840`](http://doi.org/10.1086/154840)

(ref: Valdivia_Mena_2022) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2022, A&A, 667, A12, doi: [`10.1051/0004-6361/202243310`](http://doi.org/10.1051/0004-6361/202243310)

(ref: Valdivia_Mena_2023) Valdivia-Mena, M. T., Pineda, J. E., Segura-Cox, D. M., et al. 2023, A&A, 677, A92, doi: [`10.1051/0004-6361/202346357`](http://doi.org/10.1051/0004-6361/202346357)

(ref: Vazquez_2011) Vázquez-Semadeni, E., Banerjee, R., Gómez, G. C., et al. 2011, MNRAS, 414, 2511, doi: [`10.1111/j.1365-2966.2011.18569.x`](http://doi.org/10.1111/j.1365-2966.2011.18569.x)

(ref: Virtanen_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Walch_2010) Walch, S., Naab, T., Whitworth, A., Burkert, A., & Gritschneder, M. 2010, MNRAS, 402, 2253, doi: [`10.1111/j.1365-2966.2009.16058.x`](http://doi.org/10.1111/j.1365-2966.2009.16058.x)

(ref: Ward_Thompson_2017) Ward-Thompson, D., Pattle, K., Bastien, P., et al. 2017, ApJ, 842, 66, doi: [`10.3847/1538-4357/aa70a0`](http://doi.org/10.3847/1538-4357/aa70a0)

(ref: Yano_2024) Yano, Y., Nakamura, F., & Kinoshita, S. W. 2024, ApJ, 964, 119, doi: [`10.3847/1538-4357/ad2a54`](http://doi.org/10.3847/1538-4357/ad2a54)

(ref: Yen_2019) Yen, H.-W., Gu, P.-G., Hirano, N., et al. 2019, ApJ, 880, 69, doi: [`10.3847/1538-4357/ab29f8`](http://doi.org/10.3847/1538-4357/ab29f8)

(ref: Yen_2023) Yen, H.-W., Koch, P. M., Lee, C.-F., et al. 2023, ApJ, 942, 32, doi: [`10.3847/1538-4357/aca47f`](http://doi.org/10.3847/1538-4357/aca47f)

(ref: Zucker_2018) Zucker, C., Schlafly, E. F., Speagle, J. S., et al. 2018, ApJ, 869, 83, doi: [`10.3847/1538-4357/aae97c`](http://doi.org/10.3847/1538-4357/aae97c)

</paper>

Write the methods card for this paper.