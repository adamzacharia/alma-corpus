# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023PASJ...75..120F\sonnetcc\reply.txt

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
 "bibcode": "2023PASJ...75..120F",
 "title": "Twisted magnetic field in star formation processes of L1521 F revealed by submillimeter dual-band polarimetry using the James Clerk Maxwell Telescope",
 "year": 2023,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Fukaya, Sakiko",
 "n_authors": 6,
 "arxiv_id": "2211.08988",
 "doi": "10.1093/pasj/psac094",
 "alma_projects_linked_by_archive": [
  "2018.1.00343.S"
 ]
}
```

Paper text:
<paper>
# Twisted magnetic field in star formation processes of L1521 F revealed by submillimeter dual band polarimetry using James Clerk Maxwell Telescope

## Abstract

Understanding the initial conditions of star formation requires both observational studies and theoretical works taking into account the magnetic field, which plays an important role in star formation processes. Herein, we study the young nearby dense cloud core L1521 F ($n$(H$_2$) $\sim 10^{4-6}$ cm$^{-3}$) in the Taurus Molecular Cloud. This dense core hosts a 0.2 $M_\odot$ protostar, categorized as a Very Low Luminosity Objects with complex velocity structures, particularly in the vicinity of the protostar. To trace the magnetic field within the dense core, we conducted high sensitivity submillimeter polarimetry of the dust continuum at $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$ using the POL-2 polarimeter situated in front of the SCUBA-2 submillimeter bolometer camera on James Clerk Maxwell Tetescope. This was compared with millimeter polarimetry taken at $\lambda$= 3.3 mm with ALMA. The magnetic field was detected at $\lambda$= 850 $\ensuremath{\mu}m$ in the peripheral region, which is threaded in a north-south direction, while the central region traced at $\lambda$= 450 $\ensuremath{\mu}m$ shows a magnetic field with an east-west direction, i.e., orthogonal to that of the peripheral region. Magnetic field strengths are estimated to be $\sim$70 $\mu$G and 200 $\mu$G in the peripheral- and central-regions, respectively, using the Davis-Chandrasekhar-Fermi method. The resulting mass-to-flux ratio of 3 times larger than that of magnetically critical state for both regions indicates that L1521 F is magnetically supercritical, i.e., gravitational forces dominate over magnetic turbulence forces. Combining observational data with MHD simulations, detailed parameters of the morphological properties of this puzzling object are derived for the first time.

Physics and Astronomy Department, Graduate School of Science and Engineering, Kagoshima University, Kagoshima 890-0065, Japan

Amanogawa Galaxy Astronomy Research Center(AGARC), Graduate School of Science and Engineering, Kagoshima University, Kagoshima 890-0065, Japan

Institute of Liberal Arts and Sciences, Tokushima University, Tokushima 770-8502, Japan

National Astronomical Observatory of Japan, Tokyo 181-8588, Japan

Department of Earth and Planetary Sciences, Faculty of Sciences, Kyushu University, Fukuoka 819-0395, Japan

# Introduction

   Stars are formed in the high-density cores within the interstellar molecular clouds, which consist of cold ($T= 10$ K) molecular gas and dust originating from winds and explosions of evolved low- and high-mass stars. The magnetic field as well as thermal and turbulence pressures interact to oppose gravitational collapse of the core. Accordingly, studying magnetic fields is crucial to understand detailed processes of star formation.

We here study the dense core of L1521 F (also called MC 27) in the Taurus Molecular Cloud, which is one of the nearest sites of low mass star formation at a distance of 140 pc ((cite: Elias97)).

The density of the central 1000 AU region of L1521 F is estimated to be $\sim$ $10^6$ cm$^{-3}$ ((cite: Onishietal99)). The dense core hosts L1521 F-IRS, a protostar categorized as Very Low Luminosity Object ((cite: diFrancesco07)) whose luminosity is 0.05 $\LO$ according to Spitzer measurements at 3.5, 4.5, and 8.0 $\ensuremath{\mu}m$ (e.g., (cite: Bourkeetal06)).

The Spitzer space telescope has detected a bipolar nebula that traces a bipolar outflow cavity stretched over 4000 AU within the core, almost on the plane of the sky.

CCS ($J_N =3_2 - 2_1$) and N$_2$H$^+$ ($J =1 - 0$) molecular emissions taken using the Berkeley-Illinois-Maryland Association Array indicate eight and four substructural clumps within the core, respectively. CCS emissions ($n_{\rm crit~CCS} \sim 10^{4}$ cm$^{-3}$) trace peripheral region of the core, whereas N$_2$H$^+$ emissions ($n_{\rm crit~N_2H^+} \sim 10^{5}$ cm$^{-3}$) trace its central dense region. Velocity maps of these two molecular emissions indicate that there is a notable gap in velocity structures between the peripheral and central regions of the dense core ((cite: Shinnagaetal04)). The Caltech 10.4 m Leighton telescope of the Caltech Submillimeter Observatory detects high $J$ transitions of $^{12}$CO ($J= 6 - 5$ and $J= 7 - 6$) toward the center of the dense core. CO $J= 6 - 5$ traces Warm ($\sim 30 - 70$ K), Extended (radius of $\sim$ 2400 AU), Dense ($\sim$ a few 10$^5$ cm$^{-3}$) Gas (called WEDG), in the Warm-in-Cold Core Stage (WICCS; (cite: Shinnagaetal09)), which would inaugurate a missing link in evolution between a cold quiescent starless core phase and a young protostar in class 0 stage.

High-resolution observations acquired using Atacama Large Millimeter/submillimeter Array (hereafter ALMA) at $\lambda$= 870 $\ensuremath{\mu}m$ reveal high-density condensations named MMS-1, 2, and 3 at the center of the core ((cite: Tokudaetal16)). MMS-1 corresponds to a 0.2 $M_\odot$ protostar with a 10 AU-scale disk and this is the only protostar in the system ((cite: Tokudaetal17)). The other two millimeter sources, MMS-2 and MMS-3, are minor condensations compared to MMS-1, considering their masses ranging 10$^{-3}$ to 10$^{-2} M_\odot$ (Tokuda et al. 2016).

$^{12}$CO($J= 3-2$) shows very complex and warm (\< 60 K) filamentary structures around the protostar, likely generated by turbulence ((cite: Tokudaetal18)).

The global magnetic field surrounding L1521F core is in a north$-$south direction as measured by Planck $\nu$= 353 GHz ($\lambda$= 850 $\mu$m) observations ((cite: Planckcollaboration15)). Both Optical R-band polarimetry and 850 $\ensuremath{\mu}m$ dust continuum polarimetry show north$-$northeast- to south$-$southwest magnetic field direction in the outskirt of the dense core ((cite: Soametal15), 2019).

This paper reports the magnetic field morphology within the core measured at $\lambda$= 850 $\ensuremath{\mu}m$ and $\lambda$= 450 $\ensuremath{\mu}m$ for the first time toward this object, together with $\lambda$= 3.3 mm polarimetry results using ALMA. The SED of the core is also presented to infer parameters of the protostar and the core itself based on the method presented by Robitaille (2017). Comparing these observational results with MHD theoretical simulations described by Machida et al. (2020), we discuss the gravitational infall scenario of the core based on the course of star formation.

# Observation and data reduction

## Polarimetry with Submillimeter Common Users Bolometer Array-2 (SCUBA-2) / Polarimeter-2 (POL-2) at James Clerk Maxwell Telescope (JCMT)

    Submillimeter polarimetry data toward L1521 F were taken at $\lambda$= 850 $\ensuremath{\mu}m$ and $\lambda$= 450 $\ensuremath{\mu}m$ with Submillimeter Common Users Bolometer Array 2 (SCUBA-2) and polarimeter (POL-2) ((cite: Hollandetal13)) mounted on the 15-m James Clerk Maxwell Telescope (JCMT). Dual band polarimetry enables magnetic field morphology to be traced in the peripheral cold region of the core at $\lambda$= 850 $\ensuremath{\mu}m$ as well as that in its central warm region at $\lambda$= 450 $\ensuremath{\mu}m$. Daisy scans, which are suitable for observing compact sources, were utilized to take the data. Spatial resolutions at $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$ were 14.1$\ensuremath{''}$ (corresponds to 1900 AU at 140 pc) and 8$\ensuremath{''}$ ($\sim$ 1080 AU), respectively ((cite: Dempseyetal12)).

Instrumental polarization was calibrated by using the model released on August 3, 2019. The instrumental polarization model includes a new de-biased method in order to treat the positive noise in $PI$ (polarized intensity) using a modified asymptotic estimator (Plaszczynski et al. 2014; Montier et al. 2015), which has not been applied in the past for the instrumental polarization corrections of the instrument. The method enables us to improve significantly in the resulting S/N in $PI$ of the polarization data sets.

Stokes parameters $I$, $Q$, and $U$ were used to derive the polarization fraction ($P$) and polarization angle ($ANG$), which can be described as follows:

$$\begin{equation}
P=\frac{\sqrt{Q^2+U^2}}{I} \label{eq1},
\end{equation}$$

$$\begin{equation}

ANG =\frac{1}{2} \arctan(\frac{U}{Q}) \label{eq2}.
\end{equation}$$     Polarization data were acquired on October 19, November 11, 17, 18, and 21, 2017. Total integration time is 9h 39m. Flux Conversion Factor values were 516 Jy pW$^{-1}$ beam$^{-1}$ and 531 Jy pW$^{-1}$ beam$^{-1}$ at $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$, respectively. Data were selected only when the weather conditions were satisfactory for submillimeter polarimetry (0.03 \<$\tau_{~225~ \rm{GHz}}$ \<0.07). Starlink software ((cite: Currieetal14)) was used for data reduction.

## ALMA polarimetry

   ALMA Cycle 6 Band 3 ($\lambda$= 3.3 mm) data were utilized to investigate dust continuum polarization taken with 12-m array in January 2019 (Project code: 2018.00343.1.S). Data were reduced using the Common Astronomy Software Application (CASA) package ((cite: McMullinetal07)). The synthesized beam of the data is 2.$\ensuremath{''}$958 $\times$ 2.$\ensuremath{''}$276.

## Data selection for Spectral Energy Distribution (SED) analysis

   Astropy `sedfitter` ((cite: Robitailleetal07), 2017) package was used to assess the Spectral Energy Distribution (hereafter SED) of the L1521 F core.

For this purpose, the JCMT data described above were used along with Herschel/PACS data taken at $\lambda$= 70 $\ensuremath{\mu}m$ ((cite: Bulgeretal14)), 100 $\ensuremath{\mu}m$, and 160 $\ensuremath{\mu}m$ ((cite: Sadavoyetal18)), Herschel/SPIRE data of bands at $\lambda$= 250 $\ensuremath{\mu}m$, 350 $\ensuremath{\mu}m$, and 500 $\ensuremath{\mu}m$ ((cite: Andreetal10)), IRAM 30 m MANBO-2 data taken at $\lambda$= 1.2 mm ((cite: Tokudaetal16)), and ALMA data at $\lambda$= 3.3 mm. Fluxes at each band were measured using aperture photometry using `apphot` of the IRAF package in order to subtract background emissions. To derive the respective fluxes at each band, a single aperture of 6$^{\prime\prime}$ was applied. Note that the beam sizes of the data at each band vary, as shown in Table 1. The aperture size of 6$''$ is required for this analysis in order to set the resultant flux contribution coming from the protostar itself, not from the reflection nebula that will appear in multiple infrared bands. The flux densities of each band are summarized in Table [\[tab:flux\]](#tab:flux).

Bands longer than $\lambda$= 70 $\mu$m, with the exception of the $\lambda$= 3.3 mm band, were used to determine the overall properties of the dense core. Flux densities measured at $\lambda$= 3.3 mm were not used because this is the only data taken with an interferometer and it suffers significantly from a missing flux issue.

# Results

## Submillimeter dust continuum polarimetry

| ID | Band | RA \[h m s\] | Dec \[$^\circ$ ’ $^{\prime\prime}$ \] | $I$ \[mJy beam$^{-1}$\] | $P$ \[$\%$\] | $ANG$ \[$^\circ$\] |
|:---|:---|:---|:---|:---|:---|:---|
| ID |  | RA \[h m s\] | Dec \[$^\circ$ ’ $^{\prime\prime}$ \] | $I$ \[mJy beam$^{-1}$\] | $P$ \[$\%$\] | $ANG$ \[$^\circ$\] |
|  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |
|  | 850$\mu$m | 04:28:38.605 | +26:51:03.30 | 33.07 $\pm$ 0.93 | 14.0 $\pm$ 2.0 | -76.3 $\pm$ 4.7 |
| 2 | 850$\mu$m | 04:28:38.605 | +26:51:15.00 | 59.74 $\pm$ 1.65 | 5.3 $\pm$ 1.3 | -86.3 $\pm$ 6.7 |
| 3 | 850$\mu$m | 04:28:39.501 | +26:51:15.00 | 107.09 $\pm$ 1.8 | 3.2 $\pm$ 0.8 | -60.7 $\pm$ 7.2 |
| 4 | 850$\mu$m | 04:28:38.754 | +26:52:15.00 | 62.59 $\pm$ 1.48 | 5.2 $\pm$ 1.3 | -33.5 $\pm$ 8.5 |
| 5 | 850$\mu$m | 04:28:40.548 | +26:51:51.00 | 60.08$\pm$ 2.05 | 4.8 $\pm$ 1.4 | -44.4 $\pm$ 9.0 |
| 6 | 850$\mu$m | 04:28:39.651 | +26:52:03.00 | 16.78 $\pm$ 1.46 | 17.2 $\pm$ 5.0 | -81.1 $\pm$ 12.8 |
| 7 | 450$\mu$m | 04:28:39.501 | +26:51:39.00 | 373.59 $\pm$ 13.01 | 7.0 $\pm$ 1.8 | 14.7 $\pm$ 10.2 |
| 8 | 450$\mu$m | 04:28:39.501 | +26:51:51.00 | 132.45 $\pm$ 8.66 | 23.3 $\pm$ 5.6 | 8.1 $\pm$ 8.0 |

: Polarization data measured with JCMT SCUBA-2/POL-2 at $\lambda$=  850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$

   The top and bottom panels of Figure [1](#fig:stImap) show overlays of magnetic field segments (hereafter B segments) onto the 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$ continuum images, respectively. Black lines represent the magnetic field directions derived from polarization vectors rotated by 90$^\circ$. These B segments were selected according to the following criteria; signal-to-noise ratio ($S/N$) in polarized intensity ($PI$/$DPI$) \> 3 and $S/N$ in intensity ($I$/$DI$) \> 10. Note that the B segments are plotted in 12$^{\prime\prime}$ pixels in order to ensure that every data point is independent; this differs from the continuum images.

The peak intensity of the $\lambda$= 850 $\mu$m image (Figure [1](#fig:stImap) top panel) is 232 mJy beam$^{-1}$ with rms noise levels of 1.5 mJy beam$^{-1}$. At $\lambda$= 850 $\mu$m, the magnetic fields of the peripheral region of the core are traced and they are in an overall north$-$south direction, which smoothly connects to the global magnetic field direction observed with Planck at $\lambda$= 850 $\mu$m.

The $\lambda$= 450 $\mu$m image (Figure [1](#fig:stImap) bottom panel) traces the inner warm region of the core. The corresponding peak intensity of the $\lambda$= 450 $\mu$m image is 565 mJy beam$^{-1}$ with rms noise levels of 9.9 mJy beam$^{-1}$. In the $\lambda$= 450 $\mu$m dust continuum component, the overall direction of the magnetic field is in the east$-$west direction, i.e., almost orthogonal to both the global magnetic field and the magnetic field directions in the peripheral region (traced at $\lambda$= 850 $\ensuremath{\mu}m$) of the dense core. Detected polarization segments at both wavelengths are summarized in Table [1](#tab:segments). Note that the position of the protostar, L1521 F-IRS is at $(\alpha, \delta)_{\rm J2000.0} =$ (, $+$) based on ALMA $\lambda$= 0.87 mm dust continuum observations ((cite: Tokudaetal16)); this offsets from the peak flux positions at $\lambda$= 850 $\mu$m and 450 $\mu$m.

![](L1521F_48_220819.pdf)

## Millimeter dust continuum polarimetry

   Figure [2](#fig:alma) shows the $\lambda$= 3.3 mm dust continuum image of L1521 F as acquired with ALMA.

A single continuum component is detected, with a structure elongated in the southeast direction with respect to the peak component that encases the protostar. Significant polarization was not detected in this dataset. The reason for which no significant polarization detected could either arise from a lack of sensitivity of the observation or from complex magnetic field structures in the region traced by the $\lambda$= 3.3 mm continuum.

![](alma_stokesI_220323.pdf)

# Discussion

## Mass estimated from dust continuum

    To estimate dense core masses traced at $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$, the following equation was used:

$$\begin{equation}
 M_{\rm dust}=\frac{F_\nu d^2}{{\kappa_\nu} B_{\nu}(T_{\rm dust})},
  
\end{equation}$$ where $F_\nu$ is flux density, $d$ is distance (140 pc), $\kappa_\nu$ is dust opacity, and $B{_\nu}$($T_{\rm dust}$) is brightness (Planck function) at dust temperature $T_{\rm dust}$. The flux densities of $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$ are measured as 2.00 $\pm$ 0.13 Jy, and 9.01 $\pm$ 1.51 Jy, and the corresponding dust opacities obtained by the thin ice mantle model at these wavelengths adopted as 1.89 cm$^2$ g$^{-1}$ and 6.14 cm$^2$ g$^{-1}$, respectively ((cite: Ossenkopf94)). Assuming typical values of $T_{\rm dust}$ = 10 K and a gas-to-dust ratio of 100, the estimated core masses at $\lambda$= 850 $\mu$m and 450 $\mu$m are 1.36 $\pm$ 0.09 $M_{\odot}$ and 1.48 $\pm$ 0.25 $M_{\odot}$, respectively.

## SED analysis

   Robitaille’s model ((cite: Robitaille17)) was employed to determine the SED of the dense core in order to better assess physical properties based on unresolved observations. As a result, `s-ubhmi`, i.e., an SED model with a YSO was found to have the best match for L1521 F among the large number of available models computed for 10 viewing angles at 50 apertures in a variety of evolutionary stages of star formation, as shown in Figure 3. The selected model considers following components: emissions from a central star, an Ulrich-like envelope ((cite: Ulrich76)), and a bipolar outflow cavity. The inner hole radius produced by the outflow is set as a free parameter and the dense core has an ambient medium with interstellar dust.

Table [\[tab:sed\]](#tab:sed) summarizes the physical parameters of the most closely matching model using this method. For example, the estimated inclination of the bipolar outflow cavity of 88.5$^\circ$ (nearly edge-on) matches with the observation (see also Fig. [6](#fig:image)).

![](L1521F_s-ubhmi_220323.pdf)

## Morphology of the magnetic field within the dense core

    Soam et al. (2019) reported a magnetic field structure using dust continuum polarimetry traced at $\lambda$= 850 $\ensuremath{\mu}m$ with the same instrument. Herein, by employing an updated and improved instrumental polarization model, a better signal-to-noise (S/N) ratio with higher sensitivity was achieved in order to detect polarization, i.e., the magnetic field, which was otherwise difficult to be detected (see section 2.1).

Figure [4](#fig:ccs_n2hp) shows B segments detected at $\lambda=$ 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$ overlayed onto velocity maps of CCS and N$_2$H$^+$ molecular emission reported by Shinnaga et al. (2004). Small cross marks in each panel show the positions of substructural clumps, while the thick cross on each panel represents the position of the protostar. B segments detected at $\lambda$= 850 $\mu$m and 450 $\ensuremath{\mu}m$ are within the clumps detected in N$_2$H$^+$.

CCS molecular emissions trace the early evolutionary phase which is shown to coincide in the peripheral region of the dense core. On the other hand, N$_2$H$^+$ molecular emissions trace the high-density, late evolutionary stage residing in the central region of the dense core. As such, one can confirm that the CCS peripheral region shows a velocity gradient from east to west, while the N$_2$H$^+$ central region shows a velocity gradient from northwest to southeast. This provides a clear evidence that there is a significant gap in the velocity structure within the dense core, which has been recognized as one of the major outstanding research questions of such objects. Note that magnetic field directions change drastically within and outside the central N$_2$H$^+$ clump, where a significant gap in velocity gradient is detected.

![](ccs_n2hp_bfield_220321.pdf)

## Magnetic field strength and mass-to-flux ratio

   Magnetic field strengths in L1521 F were estimated using the Davis$-$Chandrasekhar$-$Fermi method ((cite: Davis51); (cite: Chandrasekhar53)) measured at $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$. Magnetic field strength on the plane of the sky is given as

$$\begin{eqnarray}
 B_{\rm pos}= Q \sqrt{4 \pi \rho} \cdot \left( \frac{\delta V}{\delta \phi [{\rm rad}]} \right) \approx 9.3  \sqrt{n({\rm H_2})} \cdot  \left( \frac{\Delta V}{\delta\phi [^\circ]}  \right) ~\mu {\rm G}, 
 
\end{eqnarray}$$ where $Q$ is a numerical factor introduced in the simulation by (cite: Ostrikeretal01), $\rho$ is the gas density in g cm$^{-3}$, $\delta V$ is the velocity dispersion in cm s$^{-1}$, $\delta \phi$ is the dispersion in polarization position angles, $n$(H$_2$) is the number density of molecular hydrogen in cm$^{-3}$, and $\Delta V=\sqrt{8\ln2}\delta V$, which corresponds to the FWHM line width in km s$^{-1}$. Based on the results by Ostriker et al. (2001), we used $Q$ value of 0.5.

According to the equation above, gas densities are estimated as (1.14 $\pm$ 0.08) $\times$ 10$^{-18}$ g cm$^{-3}$ and (4.5 $\pm$ 0.8) $\times$ 10$^{-18}$ g cm$^{-3}$, respectively,

based on the $\lambda$= 850 $\ensuremath{\mu}m$ and 450 $\ensuremath{\mu}m$ dust continuum data. For velocity dispersion, N${_2}$H$^+$ ($J = 1 - 0$) clump data of the dense core (Shinnaga et al. (2004)) were used, since the detected magnetic field segments are within the region where N${_2}$H$^+$ emissions were detected. The velocity dispersion is derived to be (0.12 $\pm$ 0.01) $\times$ $10^{5}$ cm s$^{-1}$, and the dispersion in the polarization angle is estimated by adopting the procedure described in Franco et al. (2010). It is found to be $20 \pm 1$ $^\circ$ and $11 \pm 9$ $^\circ$ measured at $\lambda$= 850 $\mu$m and 450 $\mu$m, respectively. Estimated magnetic field strengths in the $\lambda$= 850 $\mu$m continuum and 450 $\mu$m continuum regions were 70 $\pm$ 10 $\mu$G and 200 $\pm$ 70 $\mu$G, respectively. Please note that the field strength derived at $\lambda$= 450 $\mu$m is based on the limited number of detected segments.

Mass-to-flux ratios, $\mu_{\rm c}$, are derived by using the estimated magnetic field strengths, $B_{\rm pos}$: $$\begin{eqnarray}
 \mu_{\rm c}=\frac{(M/\Phi)_{\rm obs}}{(M/\Phi)_{\rm crit}} = 0.76\cdot\left( \frac{{N(\rm{H_2})}}{{10^{-22} {\rm cm}^{-2}}} \right) \cdot \left(\frac{{B_{\rm pos}}}{{{100 \mu {\rm G}}}} \right)^{-1}
\end{eqnarray}$$

where $N$($\rm{H_2}$) is column density, $B_{\rm pos}$ is estimated magnetic field strength, and (${M/\Phi}$)$_{\rm crit}$=1/(2 $\pi$G$^{1/2}$) represents the value for magnetically critical cloud (Nakano and Nakamura 1978). Column densities derived from the observations are (2.82 $\pm$ 0.17) $\times 10^{22}$ cm$^{-2}$ for $\lambda$= 850 $\ensuremath{\mu}m$ and (7.29 $\pm$ 1.3) $\times 10^{22}$ cm$^{-2}$ for $\lambda$= 450 $\ensuremath{\mu}m$. Estimated $\mu_{\rm c}$ values are 3.1 $\pm$ 0.2 at $\lambda$= 850$\mu$m and 2.8 $\pm$ 0.4 at $\lambda$= 450 $\ensuremath{\mu}m$, respectively. These results suggest that L1521 F is in a magnetically supercritical state, i.e., gravitational forces prevail over magnetic forces.

Regarding the aspect that the system has multiple millimeter condensations, the mass of the protostar, MMS-1 (0.2 M$_\odot$), is dominant comparing with MMS-2 and MMS-3 (Tokuda et al. 2016, 2017). As a consequence, the magnetic flux of MMS-1 must dominate among the three condensations, considering the conservation of the mass-to-flux ratio. We expect that the influence of the less massive clumps MMS-2 and MMS-3 on the magnetic configuration is very limited.

Considering their masses and distances from the central protostar, MMS-1, both MMS-2 and MMS-3 cannot significantly contribute to the twist of magnetic field lines.

## Gravitational infall scenario of L1521 F based on comparison with resistive MHD simulations

   The magnetic field structure obtained by JCMT with multi-wavelength polarimetry is compared with MHD simulations described by Machida et al. (2020). This comparison enables the tracing of the gravitational infall history of the puzzling dense core. Machida et al. (2020) used three-dimensional resistive magnetohydrodynamics simulations to address the propagation of protostellar jets and the formation of circumstellar disks as well as gravitational contraction. Machida et al. (2020) studied the contraction of a molecular core which has uniform magnetic ﬁeld $B_0=57 \mu$G, rigid-body rotation speed $\Omega_0$= 1.4 $\times 10^{-13} {\rm rad s^{-1}}$, and density distribution corresponding to a Bonnor-Ebert sphere (the central density $\rho_c$=2.4$\times 10^{-18} \rm{g cm^{-3}}$ and the isothermal temperature $T= 10 \rm{K}$). They compared 9 models with different initial angles $\theta_0$ between the rotation and magnetic ﬁeld vectors.

Configurations of the system as well as magnetic field patterns are investigated for large sets of simulation results, evolution traced from the prestellar cloud phase until $\sim$560 years after the formation of a protostar. This timing corresponds to $\sim 6.3\times 10^{4}$ years since the gravitational infall initiated within the dense core. The mass of the protostar at this point is 0.04 M$_\odot$.

In order to explain the north$-$south magnetic field structure detected at $\lambda$= 850 $\ensuremath{\mu}m$ and the nearly orthogonal east$-$west magnetic field structure detected at $\lambda$= 450 $\ensuremath{\mu}m$, we found that a model with an initial misalignment angle $\theta_0 =85^{\circ}$

best explains the measured data. This is the model recognized as T85 in Machida et al. (2020). Calculating relative Stokes parameter by integrating density and magnetic field, we obtain the expected polarization pattern from the 3D MHD simulation (Tomisaka 2011; Kataoka, Machida, and Tomisaka 2012). For an observer’s viewing angle, one looks at the object with a polar angle from the $z$-axis of $\theta$ = 80$^{\circ}$ and the azimuth angle from $x$-axis of $\phi$ = 30$^{\circ}$ (see Figure [5](#fig:mhd)). For this case, the central magnetic field is twisted by rotation of the prestellar dense cloud core and directed orthogonally to the global magnetic field, i.e., towards the center of the core.

Using this model, one can interpret that the central clump observed in N$_2$H$^+$ and the dust component detected at $\lambda$= 450 $\ensuremath{\mu}m$ correspond to a pseudo-disk structure as previously shown in simulations. L1521 F-IRS is probably formed by processes of gravitational collapse with the rotation of an east$-$west angular momentum vector, which will cause the pseudo-disk to drag the magnetic ﬁeld and ﬁnally connect it to the protostar.

![](L1521F_MHD_85_80_30_220427.pdf)

# Conclusion

   Figure [6](#fig:image) shows a summary cartoon of L1521 F based on the observations described in this paper. A detailed magnetic field structure of L1521 F is detected using JCMT, SCUBA-2 and POL-2. The magnetic field in a peripheral cold region of the dense core threads a north$-$south direction as observed at $\lambda$= 850 $\ensuremath{\mu}m$, while an orthogonal east$-$west magnetic field is observed at $\lambda$= 450 $\ensuremath{\mu}m$ tracing the central warm region of the core. ALMA Band 3 observation did not detect a magnetic field structure at the scale of 1500 AU.

Estimated magnetic field strengths thus are 70 $\mu$G and 200 $\mu$G in the peripheral region traced at $\lambda$= 850 $\ensuremath{\mu}m$ and in the central warm region traced at $\lambda$= 450 $\ensuremath{\mu}m$, respectively. The resulting mass-to-flux ratio is found to be approximately 3 times greater than that of magnetically critical value for both regions, indicating that gravitational forces predominate over magnetic turbulence forces in the dense core.

Comparing observational results with MHD simulations, a gravitational infall scenario is proposed. This indicates that the rotation axis of L1521 F-IRS is misaligned with respect to initial global magnetic field axis by 85$^{\circ}$, which is almost perpendicular. One can thus interpret that the central magnetic field has been twisted by the rotation of the prestellar cloud and directed orthogonal to the global magnetic field. The central clump traced with N$_2$H$^+$ emissions and using the $\lambda$= 450 $\ensuremath{\mu}m$ dust continuum most likely corresponds to a pseudo-disk as shown in the simulation.

![](L1521F_cartoon_220323.pdf)

   The authors thank Drs. Tokuda and Saigo for the fruitful discussion. The James Clerk Maxwell Telescope is operated by the East Asian Observatory on behalf of The National Astronomical Observatory of Japan; Academia Sinica Institute of Astronomy and Astrophysics; the Korea Astronomy and Space Science Institute; the National Astronomical Research Institute of Thailand; Center for Astronomical Mega-Science (as well as the National Key R&D Program of China with No. 2017YFA0402700). Additional funding support is provided by the Science and Technology Facilities Council of the United Kingdom and participating universities and organizations in the United Kingdom and Canada.Additional funds for the construction of SCUBA-2 were provided by the Canada Foundation for Innovation. This research also used the facilities of the Canadian Astronomy Data Centre operated by the National Research Council of Canada with the support of the Canadian Space Agency. This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2018.1.00343.S. ALMA is a partnership of ESO, NSF (USA) and NINS, together with NRC, MOST and ASIAA, and KASI, in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. This work is supported in part by a Grant-in-Aid for Scientific Research of Japan (17K05388; 19H01938; 19K03919) and MEXT program supporting female and young researchers in research projects at Kagoshima University. This research made use of Astropy (Astropy Collaboration 2013, 2018). Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan.

(ref: Andreetal10) André, P., et al.  2010, A&A, 518, L102

(ref: astropycollaboration13) Astropy Collaboration  2013, A&A, 558, 33

(ref: astropycollaboration18) Astropy Collaboration  2018, AJ, 156, 123

(ref: Bulgeretal14) Bulger, J., Patience, J., Ward-Duong, K., Pinte, C., Bouy, H. Ménard, F., & Monin, J. -L  2014, A&A, 570A, 29B

(ref: Bourkeetal06) Bourke, T. L., Myers, P. C., & Evans, N. J., II  2006, ApJL, 649, L37

(ref: Currieetal14) Currie, M. J., Berry, D. S., Jenness, T., Gibb, A. G., Bell, G. S., & Draper, P. W.  2014, ASPC, 485, 391C

(ref: Chandrasekhar53) Chandrasekhar, S., & Fermi, E.  1953, ApJ, 118, 113

(ref: Davis51) Davis, L.  1951, Phys. Rev. 81, 890

(ref: Dempseyetal12) Dempsey, J. T., Friberg, P., Jenness, T., et al.  2013, MNRAS, 430, 2534

(ref: diFrancesco07) di Francesco, J., Evans, N. J., II, Caselli, P. , Myers, P. C., Shirley, Y., Aikawa, Y., & Tafalla, M.  2007, Protostars and Planets V proceedings, 17

(ref: Elias97) Elias, J. H.  1978, ApJ, 224, 857

(ref: Francoetal10) Franco, G. A. P., Alves, F. O., & Girart, J. M.  2010, ApJ, 723, 146

(ref: Hollandetal13) Holland W. S. et al.  2013, MNRAS, 430, 2513

(ref: kataoka12) Kataoka, A., Machida,M.N., & Tomiaska, K.  2012, ApJ, 761, 40

(ref: Nakano78) Nakano, T. & Nakamura, T. 1978, PASJ, 30, 671

(ref: Machidaetal20) Machida, Masahiro N. and Hirano, Shingo and Kitta, Hideyuki.  2020, MNRAS, 491, 2180

(ref: McMullinetal07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K.  2007, Astronomical Data Analysis Software and Systems XVI (ASP Conf. Ser. 376), ed. R. A. Shaw, F. Hill, & D. J. Bell (San Francisco, CA: ASP), 127

(ref: Montier2015) Montier, L., Plaszczynski, S., Levrier, F., Tristram, M., Alina, D., Ristorcelli, I., Bernard, J. -P., & Guillet, V. 2015, A&A, 574, A136

(ref: Onishietal99) Onishi, T., Mizuno, A., & Fukui, Y.  1999, PASJ, 51, 257

(ref: Ossenkopf94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943

(ref: Ostrikeretal01) Ostriker, E. C., Stone, J. M., & Gammie, C. F.  2001, ApJ, 546, 980

(ref: Plaszczynski14) Plaszczynski, S., Montier, L., Levrier, F., & Tristram, M.  2014, MNRAS, 439, 4048

(ref: Planckcollaboration15) Planck Collaboration  2020, A&A, 641, A12

(ref: Robitailleetal07) Robitaille, T. P., Whitney, B. A., Indebetouw, R., & Wood, K.  2006, ApJS, 169, 328

(ref: Robitaille17) Robitaille., T. P.  2017, A&A, 600, 11

(ref: Sadavoyetal18) Sadavoy S. I. et al.  2018, ApJ, 852, 102S

(ref: Shinnagaetal04) Shinnaga, H., Ohashi, N., Lee, S. W., & Moriarty-Schieven, G. H.  2004, ApJ, 601, 962

(ref: Shinnagaetal09) Shinnaga, H., Phillips, T. G., Furuya, R. S., & Kitamura, Y.  2009, ApJL, 706, L226

(ref: Soametal15) Soam, A., Maheswar, G., & Lee, C. W.  2015, ApJ, 883, 9

(ref: Soametal19) Soam, A., et al.  2019, ApJ, 883, 95

(ref: Tomisaka2011) Tomisaka, K.  2011, PASJ, 63, 147

(ref: Tokudaetal16) Tokuda, K., Onishi, T., & Saigo, K.  2016, ApJ, 826, 26

(ref: Tokudaetal17) Tokuda, K., Onishi, T., & Saigo, K.  2017, ApJ, 849, 101

(ref: Tokudaetal18) Tokuda, K., Onishi, T., & Saigo, K.  2018, ApJ, 862, 8

(ref: Ulrich76) Ulrich, R. K.  1976, ApJ, 210, 377

</paper>

Write the methods card for this paper.