# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...968..101E\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024ApJ...968..101E",
 "title": "Magnetic Fields Observed along the East─West Outflow of IRAS 16293-2422",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Encalada, Frankie J.",
 "n_authors": 9,
 "arxiv_id": "2405.08118",
 "doi": "10.3847/1538-4357/ad4968",
 "alma_projects_linked_by_archive": [
  "2015.1.01112.S"
 ]
}
```

Paper text:
<paper>
# Magnetic Fields Observed along the E-W Outflow of IRAS 16293-2422

## Abstract

Magnetic fields likely play an important role in the formation of young protostars. Multiscale and multiwavelength dust polarization observations can reveal the inferred magnetic field from scales of the cloud to core to protostar. We present continuum polarization observations of the young protostellar triple system IRAS 16293-2422 at 89 $\mu$m using HAWC+ on SOFIA. The inferred magnetic field is very uniform with an average field angle of 89$^\circ\pm$23$^\circ$ (E of N), which is different from the $\sim$170$^\circ$ field morphology seen at 850 $\mu$m at larger scales ($\ensuremath{\gtrsim}$ 2000 au) with JCMT POL-2 and at 1.3 mm on smaller scales ($\ensuremath{\lesssim}$300 au) with ALMA. The HAWC+ magnetic field direction is aligned with the known E-W outflow. This alignment difference suggests that the shorter wavelength HAWC+ data is tracing the magnetic field associated with warmer dust likely from the outflow cavity, whereas the longer wavelength data are tracing the bulk magnetic field from cooler dust. Also, we show in this source the dust emission peak is strongly affected by the observing wavelength. The dust continuum peaks closer to source B (northern source) at shorter wavelengths and progressively moves toward the southern A source with increasing wavelength (from 22 $\mu$m to 850 $\mu$m).

# Introduction

Magnetic fields are thought to be a critical component of the star formation process on all scales, from the assembly of molecular cloud structure to protostellar accretion (cite: pattle2023; tsukamoto2023). Nevertheless, the details of how magnetic fields affect star formation are not well observationally constrained. The magnetic field is difficult to directly observe in most regions. The most common approach is to use dust polarization emission to infer the plane of the sky magnetic field orientation. This is possible due to radiative alignment torques that tend to align the short axis of elongated dust grains with the magnetic field (cite: lazarian2007). As a result, thermal emission of dust grains will be polarized in a direction that is perpendicular to the field. Many studies therefore rotate the polarization angles by 90$^\circ$ to present the inferred plane-of-sky magnetic field morphology. Although this technique works very well in most star forming regions and spatial scales, when resolving the circumstellar disk other polarization mechanisms, such as scattering, dominate (cite: kataoka2015; yang2016; cox2018; harris2018; sadavoy2019). This makes it very difficult to measure the magnetic field morphology on small scales using dust polarization observations.

On the other hand, there have been a few surveys of the magnetic field in the inner envelope of protostars comparing the average B-field axis with the outflow axis (cite: Hull2014; Galametz2018; Zhang2014). Most recently, (cite: Huang2024) surveyed 61 protostars in Orion (with 56 detections) from the Class 0/I identified disk sources in the VANDAM survey (cite: tobin2022). They found that $\sim$40% of the protostars exhibit B-fields that are perpendicular to the source outflows on scales of 400-1000 au, with the remainder of the sources being consistent with random alignment.

The magnetic field may also play roles in the formation and/or evolution of binaries and multiple systems. Main sequence stars exhibit a multiplicity rate that increases with stellar mass: the mean frequency of stellar companions per primary rises from 0.5 for solar-type main sequence stars to 2.1 for O-type main sequence primaries (cite: moe2017). In addition, the multiplicity fraction is largest in the youngest populations of protostars (cite: tobin2016; encalada2021; tobin2022), likely decreasing as the systems age. To better understand binary formation, we must observe the youngest protobinary systems during binary formation. For young binary systems with separations $<$500 au, we expect the formation pathways are likely a combination of disk fragmentation by gravitational instability and turbulent fragmentation with migration, whereas in systems with separations $>$1000 au the binary formation mechanism is likely dominated by turbulent fragmentation (cite: adams1989; lee2019; padoan2002; moe2018).

IRAS 16293-2422 is a well studied Class 0 protostellar triple system located in the $\rho$-Ophiuchi star forming region inside the dark cloud L1689N (cite: lynd1962) at a distance of 141 pc (cite: dzib2018). The IRAS 16293 system consists of two close binaries in the southeast (separated by 54 au), sources A1 and A2, (cite: al1989; maureira2020) and a single protostar in the northwest, source B, (separated by 725 au) (cite: al1989; looney2000). Sources A and B are embedded in a large (6-8 $\times$ 10$^3$ au) envelope (cite: schoier2002; crimier2010) with a bridge of material connecting them (cite: looney2000; pineda2012). Although there had been speculation that source B was a more evolved T Tauri star (cite: Stark2004), observations of an inverse P-Cygni infall profile toward source B (cite: pineda2012) indicate that the differences in the sources are more due to viewing angle, as source B is likely face-on (cite: Rodriguez2005) whereas the binary sources A1 and A2 are more edge-on (cite: pineda2012).

With three protostars and their geometry, the system has both complicated envelope and outflow structures. The envelope has complex chemistry (cite: jorgensen2016), and due to the multiplicity and the connecting bridge, the envelope presents difficulties in modeling the source details (cite: jacobsen2018). The system has large and impressive outflows that even at their discovery were known to be multi-lobed and very complicated, likely due to a multiple system (cite: fukui1986; al1987; walker1988; mizuno1990). The multiple outflows, some of which are observed only on large scales while others are observed only on small scales, are well summarized in (cite: vanderwiel2019) and many references within.

On the largest scales, there are two observed outflows: east (blue)-west (red) (cite: fukui1986; al1987; walker1988; mizuno1990; Stark2004) and northeast (red)-southwest (blue) (cite: walker1988; mizuno1990; Stark2004). However at smaller scales, the northeast-southwest outflow is not detected, implying that the launching engine was quenched (cite: vanderwiel2019). On the other hand, the east-west outflow, which is driven by source A, is clearly detected on smaller scales with interferometers (cite: Girart2014; Yeh2008; vanderwiel2019). An additional outflow detected only on the small scale is aligned northwest (blue)-southeast (red) originating slightly north of source A with a blue bowshock in the location of source B (cite: Girart2014; kristensen2013). Although there are some observational hints of an outflow from source B (cite: Yeh2008), there are no observations that show clear evidence of outflow emission from source B.

In this paper, we present far-infrared observations (89 $\mu$m) on the scale of $\sim$1000 au toward IRAS 16293-2422. The observations used the High-Resolution Airborne Wide-band Camera (cite: vaillancourt2007; harper2018) onboard the Stratospheric Observatory For Infrared Astronomy (SOFIA). We use the 89 $\mu$m dust continuum observations to infer the magnetic field in the envelope of IRAS 16293-2422, hereafter called IRAS 16293. The inferred magnetic field morphology is compared to 850 $\mu$m observation from the POL-2 polarimeter on the James Clerk Maxwell Telescope (JCMT) and to 1.3 mm observations from the Atacama Large Millimeter/submillimeter Array (ALMA). In addition, we compare the peak flux location variation with wavelength using archival observations from WISE, Herschel, and SCUBA 2 on the JCMT.

The paper is organized as follows: in Section 2 we present the observations and data reduction, Section 3 covers the results of the observations, Section 4 discusses the results, and Section 5 contains our conclusions.

# Observations and Data Reduction

We observed IRAS 16293 on 2019 July 23rd, between 12:21:13 and 12:25:41 UTC, using HAWC+ at Band C (89 $\mu$m). The observations were part of the Cycle 7 program PID 07_0147 (PI: Novak). The bandwidth was 16.9 $\mu$m, the angular resolution (full width at half maximum; FWHM) was 7.8$^{\prime\prime}$, and the field of view for the total intensity and polarimetry was 4.2$^{\prime}$ $\times$ 2.7$^{\prime}$ and 2.1$^{\prime}$ $\times$ 2.7$^{\prime}$, respectively.

The HAWC+ instrument is a far-infrared detector with 5 broadband filters for continuum, a rotating half-wave plate that modulates the incoming polarization, and a grid that orthogonally separates the polarization. Multiple cycles of standard nodding and chopping were used to build an image within a few minutes (cite: hildebrand2000). The instrument typically nods at 0.1 Hz and chops at 10 Hz. The four dithered positional observations are used to construct a single imaging block, or dither set. Due to a lack of bright visual guide stars in the region, there was a small offset in some of the imaging blocks. To correct this, we shifted the fit map Gaussian peak center to align with the archival map from Herschel’s Photodetector Array Camera & Spectrometer (PACS) at 100 $\mu$m. No individual observation was offset by more than half a beam.

The raw images are then processed through the HAWC+ data reduction pipeline, which produces science ready continuum and polarization products. The details of the process are summarized in (cite: harper2018). Briefly, the pipeline flat-fields the demodulated and usable chopped data, calculates the Stokes I, Q, and U parameters from the combined nodded fluxes, and then corrects the pointing and instrumental polarization. Calibrations are applied to the flux via standard atmospheric opacity models using Neptune planetary observations. Finally, the Stokes maps are combined via standard re-gridding and Gaussian smoothing (cite: houde2007). We smoothed the final maps to increase the signal to noise in the lower surface brightness regions away from the central source, creating a final beam size of 11.7$^{\prime\prime}$.

We compared our Stokes I, Q, and U maps across the different dither sets using a $\chi^{2}$ analysis. A $\chi^{2}$ is calculated for each pixel, which is then compare with the pipeline error result for that pixel. If the $\chi^{2}$ is larger, then we inflate the pipeline error (cite: Chapman2013; Novak2011). Following (cite: Erin2022), we perform the inflation by fitting a parameterized $\chi^{2}$ with Stokes I intensity, allowing us to inflate each pixel based on its continuum brightness. This was done to handle the uncertainties more carefully in the the brightest regions, where intensity-dependent errors dominate.

Finally, the percent polarization ($p$) and its error ($\sigma_{p}$) are calculated for each pixel following the HAWC+ handbook (cite: hawcplus_handbook) by

$$\begin{equation}
p =  100 \sqrt{\left(\frac{Q}{I}\right)^2 + \left(\frac{U}{I}\right)^2}
\end{equation}$$

and

$$\begin{equation}
\sigma_{p} = \frac{100}{I} \sqrt{
\begin{aligned}
\frac{1}{(Q^2 + U^2)}
(Q\sigma_{Q}^2 + U\sigma_{U}^2 + 2QU\sigma_{QU})+ \\
\left[\left(\frac{Q}{I}\right)^2 + \left(\frac{U}{I}\right)^2\right]\sigma_{I}^2
- 2 \frac{Q}{I}\sigma_{QI}
- 2 \frac{U}{I}\sigma_{UI}
\end{aligned}}
\end{equation}$$ where $\sigma_{Q}$ and $\sigma_{U}$ are the uncertainties in Stokes Q and U and where $\sigma_{QU}$, $\sigma_{QI}$, and $\sigma_{UI}$ are the covariance uncertainty terms. The polarization fraction is debiased ($p^\prime$), following the HAWC+ handbook (cite: hawcplus_handbook) by $p^\prime = \sqrt{p^2 - \sigma_{p}^2}$. From all of these, the debiased polarization intensity ($P^\prime = I \times p^\prime/100$) and its errors are calculated. Although the uncertainties are calculated per pixel, the median Stokes I RMS is $\sigma_I$ = 2.2 mJy/arsec$^2$ and the median polarization intensity RMS $\sigma_p$ = 0.22 mJy/arsec$^2$.

For the final maps, we selected the debiased polarization vectors that met the criteria of $P^\prime$/$\sigma_{p}$ $>$ 3, the debiased polarization percentage was $<$ 50%, and the Stokes I flux values were at least $\times$10 the Stokes I RMS noise level. While this was done at every pixel in the image, we present only enough vectors to be considered Nyquist sampled, for a total of 45 polarization vectors.

We estimate the overall flux calibration uncertainty of the observations at 20%, but for the remainder of the paper, any flux uncertainty listed will only consider statistical uncertainty.

## Archival Data

To compare our polarization observations with other wavelengths, we used JCMT POL-2 850 $\mu$m wavelength polarization observations at 14$\ensuremath{''}$ resolution from (cite: pattle2021), and ALMA Band 6 (1.3 mm wavelength) polarization observations from (cite: Sadavoy2018), smoothed to 1$\ensuremath{''}$ resolution.

In addition, we also used Herschel 70, 100, and 160 $\mu$m PACS data[^1] and 250, 350, and 500 $\mu$m SPIRE data[^2] (Spectral and Photometric Imaging Receiver).

We included the 24 $\mu$m Spitzer MIPS data[^3] (Multiband Imaging Photometer). All of these data were obtained from the Herschel Science Archive[^4]. Lastly, the 22 $\mu$m WISE data[^5] (Wide-field Infrared Survey Explorer) from the NASA/IPAC Infrared Science Archive[^6] were also included.

# Results

![](fig1_.pdf)

Figure [1](#fig:90) shows the HAWC+ Band C (89 $\mu$m) dust continuum observations of IRAS 16293 with the inferred magnetic field polarization direction (i.e. polarization rotated by 90 degrees) plotted over the 89 $\mu$m continuum map as line segments, hereafter called vectors.

We fit the protostellar envelope continuum emission using a Gaussian. The protostellar envelope is resolved with a deconvolved fit size of 10.3$^{\prime\prime}$ $\pm$ 0.4$^{\prime\prime}$ by 8.7$^{\prime\prime}$ $\pm$ 0.4$^{\prime\prime}$ with a position angle (PA) of 108$^{\circ}$ $\pm$ 11$^{\circ}$. The integrated fit flux is 1236 $\pm$ 25 Jy, and the peak flux is 1.25 $\pm$ 0.02 Jy/arcsec$^{2}$.

The continuum Gaussian fit of the HAWC+ 89 $\mu$m observation is different than Gaussian fits to the Herschel archival data. The PACS 100 $\mu$m source fits are somewhat smaller (7.7$^{\prime\prime}$ $\pm$ 0.4$^{\prime\prime}$ by 4.8$^{\prime\prime}$ $\pm$ 0.4$^{\prime\prime}$ and a PA of 141$^{\circ}$ $\pm$5$^{\circ}$), whereas the PACS 70 $\mu$m source fits are a little larger (11.9$^{\prime\prime}$ $\pm$ 0.3$^{\prime\prime}$ by 10.1$^{\prime\prime}$ $\pm$ 0.3$^{\prime\prime}$ and a PA of 113$^{\circ}$ $\pm$ 7$^{\circ}$). The variation indicated in the Gaussian fits of the HAWC+ and 70 and 100 PACS $\mu$m images likely arises from differences in the source morphologies (e.g., outflows, envelopes, and the bridge connecting source A and B) so close to the overall emission peak near 100 $\mu$m. On the other hand, the PA from the HAWC+ Band C fit is within 10$^{\circ}$ of the 850 $\mu$m dust emission (cite: pattle2021), although the 850 $\mu$m core extension is measured on much larger scales.

![](fig2_.pdf)

We can compare the inferred magnetic field from other observations with varying wavelength and spatial scales. Figure [2](#fig:91) shows the inferred magnetic field from our 89 $\mu$m data from Figure [1](#fig:90) (black vectors) with the 850 $\mu$m data from POL-2 (orange vectors), which have 14$\ensuremath{''}$ resolution and 12$\ensuremath{''}$ pixels (cite: pattle2021), both wavelengths presented as normalized vectors. The vectors align on the western side of the source (and one vector in the southeast), but otherwise there is generally not much agreement on the inferred magnetic field direction.

On the other hand, misalignment is also seen when comparing the core scale (POL-2) with the cloud scale (Planck). As pointed out by (cite: pattle2021), there is a misalignment of the large scale Planck field with the POL-2 850 $\mu$m magnetic field near the IRAS 16293 protostars, which is also seen in Figure [2](#fig:91) as a field shift near the protostars compared to the outer region. In Figure [1](#fig:90), the inferred HAWC+ magnetic field is generally aligned EW. This is offset by $\sim$65$^{\circ}$ from the overall $\sim$arcminute large-scale field inferred from Planck observations of the Ophiuchus L1689 molecular cloud core, which is 24$^{\circ}$ E of N (cite: pattle2021).

At higher spatial scale, Figure [3](#fig:93) compares the 89 $\mu$m HAWC+ data and 850 $\mu$m POL-2 data with high resolution polarization observations at 1.3 mm with ALMA from (cite: Sadavoy2018), which are consistent with 880$\mu$m polarization observations from (cite: Rao2009). The ALMA data have been smoothed to 1$\ensuremath{''}$ resolution to better compare with our observations.

Note that the region mapped in Figure [3](#fig:93) is only slightly larger than the POL-2 and HAWC+ beam sizes, so it is difficult to do more than compare broadly. However, in general, the vectors from the three observations are not well-aligned. The HAWC+ and ALMA observations have some agreement to the northwest, and the ALMA and POL-2 observations have some agreement in the bridge region between source A and B. On the other hand, HAWC+ and ALMA observations are anti-aligned in the South, while ALMA and POL-2 observations are anti-aligned in the middle-eastern side.

![](fig3_.pdf)

# Discussion

![](fig4_.pdf)

## Continuum Wavelength Dependence

When comparing the HAWC+ dust continuum emission Gaussian fits with the Gaussian fits from Herschel, as well as the peak in the POL-2 observations, we noted that the peak of the emission varied with wavelength– with the far infrared wavelengths peaking between the protostellar source locations. As expected, the flux peak dust continuum of the IRAS 16293-2422 system is strongly dependent on observing wavelength, as can be seen in the SED from (cite: schoier2002) with a maximum around 100 $\mu$m, but it also seems that the spatial location of the peak is very strongly dependent on observing wavelength. By using the archival observations, we can compare this trend more broadly.

We fit the different wavelength emission (e.g., WISE, Herschel, and SCUBA2 listed in Section [2](#sec:observations)) to Gaussians. Figure [4](#fig:92) shows the Gaussian fit peak to wavelengths from 22 $\mu$m to 850 $\mu$m. There is a clear gradient from northwest to southeast from short wavelengths to long wavelengths. In other words, we detect a gradient in the cloud dust temperatures with wavelength. This is likely due to differences in the morphology or detailed properties of the source, possibly arising from the structure of the envelope or disks in the binary system.

Another explanation of the shift with wavelength could be a difference in evolutionary stage of the binary sources. As stated in §1, source B has been argued to be more evolved than source A (cite: Stark2004). As we probe shorter and shorter wavelengths, we are most sensitive to the hot dust in the less obscured source. However, the evolutionary stages of the protostars are still uncertain with most recent work suggesting that the sources are likely at about the same evolutionary stage or that source B is slightly less evolved (cite: vanderwiel2019), but the evolutionary ages are still a point of contention.

One of the complications is that the two protostars have different inclinations with respect to the line of sight. Source A, which is the tight binary, is closer to edge-on (cite: maureira2020) while source B is close to face-on (cite: zamponi2021). The source A protostars are most likely Class 0 based on evidence of them driving active outflows (cite: Yeh2008), but the evolution of source B is harder to verify due to its face-on inclination and lack of outflow activity (cite: Yeh2008). The difference in inclination could explain the observed peak shift seen at the shorter wavelengths, since the shorter wavelengths are most sensitive to the hotter dust seen in the more face-on disk, which is less obscured. In addition, source A is also surrounded by a $\sim$100 au circumbinary disk with a PA of $\sim$50$^\circ$ (cite: maureira2020), which could increase the obscuration for the binary. We suggest that such continuum peak positional shifts with wavelength may be present in other binary sources, requiring careful consideration of variation in peak position at the shorter wavelengths.

![](fig5_.pdf)

## Magnetic Fields

At the large scales in dense, elongated structures or filaments of molecular clouds, the magnetic field’s alignment depends on column density: below a critical column density, the magnetic field is preferentially oriented parallel to the elongation of density structures, and above, the magnetic field is preferentially perpendicular (cite: planckXXXV2016). However, the details of the alignment may vary across star formation regions (cite: Stephens2022). Using HAWC+ observations in L1688, it has been shown that the transition occurs at a molecular hydrogen column density of $\sim$10$^{21.7}$ cm$^{-2}$ (cite: lee2021). Magneto-hydrodynamic simulations have suggested that the transition may coincide with the kinetic energy of the gravitationally induced flows surpassing the magnetic energy (cite: chen2016).

One of the goals of our observations was to compare the inferred magnetic field in the far infrared dust continuum to other resolutions and scales that impact the star formation process. The large scale Planck inferred magnetic field in the L1689-N region is 24$^{\circ}$ E of N (cite: pattle2021), i.e. nearly perpendicular to the large L1689/L1712 filament identified in (cite: Ladjelate2020). These large-scale Planck fields are generally consistent with the 850 $\mu$m JCMT POL-2 inferred magnetic fields shown in Figure [2](#fig:91), although in detail the POL-2 fields are less aligned with the overall Planck field at the cloud core (cite: pattle2021). This is not surprising as the overall Planck field seems to exhibit a small shift at the the core that suggests unresolved morphology.

When one traces the magnetic field from the L1689-N core scale down to the protostellar envelope scale with the three observations in Figure [3](#fig:93), we see regions where the inferred magnetic fields are aligned but other regions where the inferred magnetic fields are misaligned. The HAWC+ and ALMA observations are aligned in the northwest, while the ALMA and POL-2 observations are well aligned in the bridge region between source A and B. On the other hand, HAWC+ and ALMA observations are misaligned in the South, while ALMA and POL-2 observations are misaligned on the eastern side. However, as pointed out by (cite: pattle2021), the average field angles are consistent between ALMA and POL-2: 166$^\circ\pm$31$^\circ$ for POL-2 at the cloud core and 176$^\circ\pm$54$^\circ$ and 130$^\circ\pm$14$^\circ$ averaged around the protostars only and the bridge between them only in the unsmoothed ALMA data in (cite: Sadavoy2018), respectively. Whereas the HAWC+ observations have a very different measured polarization angle: 89$^\circ\pm$23$^\circ$, which is more in line with the E-W outflow.

Indeed, one of the most striking features of the HAWC+ map is the uniform field that is nearly completely EW in direction, which is very different morphologically to the Planck, JCMT, and ALMA inferred magnetic field angles. Although one could argue for large field morphological connections or trends between the mapped fields in Figure [3](#fig:93), there is still not overall coherence across wavelengths. The key to understanding these different wavelength observations is that the observations are probing different optical depth and dust temperatures (as seen clearly in Figure [3](#fig:93)), making it difficult to piece together the overall 3D magnetic field morphology without a better understanding of the system details.

The IRAS 16293-2422 triple system has a complicated morphology with the protostars, disks, a bridge feature, and multiple outflows observed on different spatial scales (cite: vanderwiel2019). To date, the outflows have only been associated with source A, which is likely due to the face-on inclination of source B or possibly a difference in evolutionary stage. As discussed in §1, source A has two outflows on the 1000s of au scale: one east-west (cite: Yeh2008) and one northwest-southeast (cite: kristensen2013). Arguably, the east-west outflow dominates the system on the cloud core scale (cite: mizuno1990; Stark2004), which is also well detected in higher resolution interferometric observations (cite: Yeh2008). Figure [5](#fig:94) shows our inferred magnetic fields with the blue- and red-shifted outflows as identified from CO (3-2) observations of (cite: Yeh2008). Our magnetic field vectors are well aligned with this outflow direction, with the exception of our vectors extending more in the south. Nonetheless, based on this comparison, we posit that the HAWC+ observations are tracing the warm dust from the E-W outflow cavity or cavity walls of IRAS 16293-2422 (cite: Stark2004). This is in contrast to the average magnetic field from the POL-2 and ALMA observations, which are approximately perpendicular to the E-W outflow. On the other hand, this is consistent with the (cite: Huang2024) survey, where $\sim$40% of the sources have average magnetic fields perpendicular to the source outflow.

There are many morphological examples of the outflows of protostars seeming to modify or shape the magnetic field of the core as traced by single dish observations: Orion A filament (cite: Pattle2017), NGC 2071IR in Orion B (cite: Lyo2021), and CB 54 (cite: Pattle2022) or to modify or shape the inner protostellar envelope as traced by interferometric observations: Serpens SMM1 (cite: Hull2017), B335 (cite: Maury2018), Emb 8(N) (cite: LeGouellec2019), and BHR 71 IRS2 (cite: Hull2020).

Additionally, the short wavelength observational inferred magnetic field can exhibit different morphologies compared to the longer wavelengths. In Orion, for example, the HAWC+ shorter wavelengths (53 and 89 $\mu$m compared to 154 and 214 $\mu$m) is more aligned with the bipolar outflow structure in the Becklin–Neugebauer/Kleinman–Low region, as traced by molecular tracers (cite: chuss2019). The longer wavelengths are argued to be tracing the cooler dust that is outside of the explosion influenced region.

In this case for IRAS 16293-2422, the 89 $\mu$m continuum emission is tracing the warmer dust surrounding the outflow. The magnetic field morphology in this region is dominated by the outflow and not the magnetic field in the cloud core or the bridge, which is seen to dominate at longer wavelengths. This is somewhat consistent with the continuum peak of IRAS 16293-2442 at $\sim$100 $\mu$m being near the center of the system so that the polarization is dominated by the large opening angle cavity seen in Figure [5](#fig:94).

## Possibility of Polarization by Dichroic Extinction

As the inferred magnetic direction in Figure [1](#fig:90) is different than what is observed at 850 $\mu$m with POL-2, we should also examine other polarization mechanisms that may account for the observations. The most likely other polarization mechanism would be dichroic extinction, used in the optical or infrared to infer magnetic fields from polarization observations of stars extincted by aligned dust grains (cite: scarrott1989). Although dichroic extinction depends on dust properties, optical depth, and temperature gradients (cite: hildebrand2000), we can consider the effect in the typical case for young stellar objects when unpolarized, or weakly polarized, emission is extincted by cooler foreground dust that has its grains aligned by magnetic fields or other means. In that case, the dust grain’s long axis will have more efficient extinction than the short axis, so the light is now polarized along the dust’s short axis, which would result in a 90$^\circ$ flip in the polarization, compared to the inferred magnetic field from emission of aligned dust grains. The effect has been seen in far infrared dust polarization observations, particularly in the Sagittarius B2 molecular cloud (cite: novak1997; dowell1997). The process will be most effective in optically thick sources with a temperature gradient.

Although, we can not rule out dichroic extinction as the dominate mechanism for polarization in IRAS 16293-2422 (cite: Zielinski2021), there are a few reasons to disfavor that explanation. First, we do not see a strong signature of the 90$^\circ$ flip toward the outside of the source, as is seen, for example, in observations of NGC 1333 IRAS4 (cite: ko2020) and OMC-3/MMS 6 (cite: baobab2021). In fact, with the exception of two vectors, Figure [1](#fig:90) shows a very uniform inferred magnetic field. Of course such a flip is not necessary, but if we flip all of our vectors by 90$^\circ$, then the vectors on the west in Figure [2](#fig:91) that currently agree with the POL-2 and ALMA vectors would disagree. Second, although a flip of 90$^\circ$ for the inferred magnetic field would mean an average field of 179$^\circ\pm$23$^\circ$, which is closer to the bulk average magnetic fields of 166$^\circ\pm$31$^\circ$ for POL-2 and 176$^\circ\pm$54$^\circ$ for ALMA data, in detail the vectors in the inner region of the source, see Figure [3](#fig:93) for example, would not better match with a HAWC+ flip of 90$^\circ$. Third, the polarization fraction is lower toward the center of our observations in Figure [1](#fig:90). Such polarization depression with increasing density are commonly detected in magnetic field aligned dust grain polarization observations (cite: chuss2019) and are not seen in regions where the polarization is due to dichroic extinction (cite: novak1997; dowell1997; ko2020). Finally, east-west magnetic fields have also been detected along a few stellar sight lines in the L1689 cloud at optical wavelengths (cite: Vrba1976), suggesting that there are east-west fields in some parts of the region. Overall, based on these four reasons, the IRAS 16293-2422 polarization observations presented here are most likely due to magnetic field alignment of dust grains.

# Conclusions

We present the 89 $\mu$m continuum polarization emission toward the protostellar system IRAS 16293-2422 using the HAWC+ polarimeter onboard SOFIA. Our main conclusions are:

1.  We detect a uniform magnetic field in the inner region of IRAS 16293-2422 that is aligned east-west. The average field angle in the HAWC+ observations is 89$^\circ\pm$23$^\circ$, which is consistent with one of the known large scale outflows. This is different from the average field angles at longer wavelengths: Planck large-scale average field angle of 24$^\circ$, JCMT POL-2 average field angle of 166$^\circ\pm$31$^\circ$, and the ALMA average field angle near the protostars of 176$^\circ\pm$54$^\circ$.

2.  We posit that the magnetic field probed by the 89 $\mu$m continuum emission is dominated by the outflow magnetic field, while the 850 $\mu$m dust emission is dominated more by the core magnetic field.

3.  The continuum peak of the source varies significantly with wavelength, moving from near Source B at the midIR to near Source A in the FIR. This is either a consequence of evolutionary state of the two sources or more likely due to the difference in inclination. The shorter wavelengths are more sensitive to the warmer dust which is seen in Source B.

These observations suggest that magnetic fields in young protostars are likely more complicated than simple pictures suggest with multiple field morphologies dominating at various scales and in different structures. Any observational constraints should include multiwavelength observations that sample multiple scales and all the structures of star formation.

# Acknowledgments

Based on observations made with the NASA/DLR Stratospheric Observatory for Infrared Astronomy (SOFIA). SOFIA is jointly operated by the Universities Space Research Association, Inc. (USRA), under NASA contract NNA17BF53C, and the Deutsches SOFIA Institut (DSI) under DLR contract 50 OK 0901 to the University of Stuttgart. L.W.L. acknowledges support from NSF AST-1910364 and NSF AST-2307844. R.E.H acknowledges support from NSF AST-1910364. G.N. is grateful for NASA support for this work, via award Nos. SOF 06-0116 and SOF 07-0147 issued by USRA to Northwestern University. E.G.C. acknowledges support from the National Science Foundation through the NSF MPS Ascend Fellowship Grant number 2213275. K.P. is a Royal Society University Research Fellow, supported by grant no. URF\R1\211322. We thank Naomi Hirano for providing us with the calibrated SMA CO observations in Figure [5](#fig:94). We thank John Tobin for discussions on binarity and Zhi-Yun Li for discussions on magnetic field alignment with column density.

natexlab

(ref: adams1989) Adams, F. C., Ruden, S. P., & Shu, F. H. 1989, ApJ, 347, 959, doi: [`10.1086/168187`](http://doi.org/10.1086/168187)

(ref: Chapman2013) Chapman, N. L., Davidson, J. A., Goldsmith, P. F., et al. 2013, ApJ, 770, 151, doi: [`10.1088/0004-637X/770/2/151`](http://doi.org/10.1088/0004-637X/770/2/151)

(ref: chen2016) Chen, C.-Y., King, P. K., & Li, Z.-Y. 2016, ApJ, 829, 84, doi: [`10.3847/0004-637X/829/2/84`](http://doi.org/10.3847/0004-637X/829/2/84)

(ref: chuss2019) Chuss, D. T., Andersson, B. G., Bally, J., et al. 2019, ApJ, 872, 187, doi: [`10.3847/1538-4357/aafd37`](http://doi.org/10.3847/1538-4357/aafd37)

(ref: hawcplus_handbook) Clarke, M., Berthoud, M., Kovács, A., Santos, F., & Novak, G. 2020, Guest Observer Handbook for HAWC+ Data Products, Rev. F. <https://www.sofia.usra.edu/sites/default/files/Instruments/HAWC_PLUS/Documents/hawc_data_handbook.pdf>

(ref: cox2018) Cox, E. G., Harris, R. J., Looney, L. W., et al. 2018, ApJ, 855, 92, doi: [`10.3847/1538-4357/aaacd2`](http://doi.org/10.3847/1538-4357/aaacd2)

(ref: Erin2022) Cox, E. G., Novak, G., Sadavoy, S. I., et al. 2022, ApJ, 932, 34, doi: [`10.3847/1538-4357/ac722a`](http://doi.org/10.3847/1538-4357/ac722a)

(ref: crimier2010) Crimier, N., Ceccarelli, C., Maret, S., et al. 2010, A&A, 519, A65, doi: [`10.1051/0004-6361/200913112`](http://doi.org/10.1051/0004-6361/200913112)

(ref: dowell1997) Dowell, C. D. 1997, ApJ, 487, 237, doi: [`10.1086/304577`](http://doi.org/10.1086/304577)

(ref: dzib2018) Dzib, S. A., Ortiz-León, G. N., Hernández-Gómez, A., et al. 2018, A&A, 614, A20, doi: [`10.1051/0004-6361/201732093`](http://doi.org/10.1051/0004-6361/201732093)

(ref: encalada2021) Encalada, F. J., Looney, L. W., Tobin, J. J., et al. 2021, ApJ, 913, 149, doi: [`10.3847/1538-4357/abf4fd`](http://doi.org/10.3847/1538-4357/abf4fd)

(ref: fukui1986) Fukui, Y., Sugitani, K., Takaba, H., et al. 1986, ApJL, 311, L85, doi: [`10.1086/184803`](http://doi.org/10.1086/184803)

(ref: Galametz2018) Galametz, M., Maury, A., Girart, J. M., et al. 2018, A&A, 616, A139, doi: [`10.1051/0004-6361/201833004`](http://doi.org/10.1051/0004-6361/201833004)

(ref: Girart2014) Girart, J. M., Estalella, R., Palau, A., Torrelles, J. M., & Rao, R. 2014, ApJL, 780, L11, doi: [`10.1088/2041-8205/780/1/L11`](http://doi.org/10.1088/2041-8205/780/1/L11)

(ref: harper2018) Harper, D. A., Runyan, M. C., Dowell, C. D., et al. 2018, Journal of Astronomical Instrumentation, 07, 1840008, doi: [`10.1142/s2251171718400081`](http://doi.org/10.1142/s2251171718400081)

(ref: harris2018) Harris, R. J., Cox, E. G., Looney, L. W., et al. 2018, ApJ, 861, 91, doi: [`10.3847/1538-4357/aac6ec`](http://doi.org/10.3847/1538-4357/aac6ec)

(ref: hildebrand2000) Hildebrand, R. H., Davidson, J. A., Dotson, J. L., et al. 2000, PASP, 112, 1215, doi: [`10.1086/316613`](http://doi.org/10.1086/316613)

(ref: houde2007) Houde, M., & Vaillancourt, J. E. 2007, PASP, 119, 871, doi: [`10.1086/521109`](http://doi.org/10.1086/521109)

(ref: Huang2024) Huang, B., Girart, J. M., Stephens, I. W., et al. 2024, ApJL, 963, L31, doi: [`10.3847/2041-8213/ad27d4`](http://doi.org/10.3847/2041-8213/ad27d4)

(ref: Hull2020) Hull, C. L. H., Le Gouellec, V. J. M., Girart, J. M., Tobin, J. J., & Bourke, T. L. 2020, ApJ, 892, 152, doi: [`10.3847/1538-4357/ab5809`](http://doi.org/10.3847/1538-4357/ab5809)

(ref: Hull2014) Hull, C. L. H., Plambeck, R. L., Kwon, W., et al. 2014, ApJS, 213, 13, doi: [`10.1088/0067-0049/213/1/13`](http://doi.org/10.1088/0067-0049/213/1/13)

(ref: Hull2017) Hull, C. L. H., Girart, J. M., Tychoniec, Ł., et al. 2017, ApJ, 847, 92, doi: [`10.3847/1538-4357/aa7fe9`](http://doi.org/10.3847/1538-4357/aa7fe9)

(ref: jacobsen2018) Jacobsen, S. K., Jørgensen, J. K., van der Wiel, M. H. D., et al. 2018, A&A, 612, A72, doi: [`10.1051/0004-6361/201731668`](http://doi.org/10.1051/0004-6361/201731668)

(ref: jorgensen2016) Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595, A117, doi: [`10.1051/0004-6361/201628648`](http://doi.org/10.1051/0004-6361/201628648)

(ref: kataoka2015) Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78, doi: [`10.1088/0004-637X/809/1/78`](http://doi.org/10.1088/0004-637X/809/1/78)

(ref: helen2018) Kirk, H., Hatchell, J., Johnstone, D., et al. 2018, ApJS, 238, 8, doi: [`10.3847/1538-4365/aada7f`](http://doi.org/10.3847/1538-4365/aada7f)

(ref: ko2020) Ko, C.-L., Liu, H. B., Lai, S.-P., et al. 2020, ApJ, 889, 172, doi: [`10.3847/1538-4357/ab5e79`](http://doi.org/10.3847/1538-4357/ab5e79)

(ref: kristensen2013) Kristensen, L. E., Klaassen, P. D., Mottram, J. C., Schmalzl, M., & Hogerheijde, M. R. 2013, A&A, 549, L6, doi: [`10.1051/0004-6361/201220668`](http://doi.org/10.1051/0004-6361/201220668)

(ref: Ladjelate2020) Ladjelate, B., André, P., Könyves, V., et al. 2020, A&A, 638, A74, doi: [`10.1051/0004-6361/201936442`](http://doi.org/10.1051/0004-6361/201936442)

(ref: lazarian2007) Lazarian, A. 2007, JQSRT, 106, 225, doi: [`10.1016/j.jqsrt.2007.01.038`](http://doi.org/10.1016/j.jqsrt.2007.01.038)

(ref: LeGouellec2019) Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106, doi: [`10.3847/1538-4357/ab43c2`](http://doi.org/10.3847/1538-4357/ab43c2)

(ref: lee2019) Lee, A. T., Offner, S. S. R., Kratter, K. M., Smullen, R. A., & Li, P. S. 2019, ApJ, 887, 232, doi: [`10.3847/1538-4357/ab584b`](http://doi.org/10.3847/1538-4357/ab584b)

(ref: lee2021) Lee, D., Berthoud, M., Chen, C.-Y., et al. 2021, ApJ, 918, 39, doi: [`10.3847/1538-4357/ac0cf2`](http://doi.org/10.3847/1538-4357/ac0cf2)

(ref: baobab2021) Liu, H. B. 2021, ApJ, 914, 25, doi: [`10.3847/1538-4357/abf8b6`](http://doi.org/10.3847/1538-4357/abf8b6)

(ref: looney2000) Looney, L. W., Mundy, L. G., & Welch, W. J. 2000, ApJ, 529, 477, doi: [`10.1086/308239`](http://doi.org/10.1086/308239)

(ref: lynd1962) Lynds, B. T. 1962, ApJS, 7, 1, doi: [`10.1086/190072`](http://doi.org/10.1086/190072)

(ref: Lyo2021) Lyo, A. R., Kim, J., Sadavoy, S., et al. 2021, ApJ, 918, 85, doi: [`10.3847/1538-4357/ac0ce9`](http://doi.org/10.3847/1538-4357/ac0ce9)

(ref: maureira2020) Maureira, M. J., Pineda, J. E., Segura-Cox, D. M., et al. 2020, ApJ, 897, 59, doi: [`10.3847/1538-4357/ab960b`](http://doi.org/10.3847/1538-4357/ab960b)

(ref: Maury2018) Maury, A. J., Girart, J. M., Zhang, Q., et al. 2018, MNRAS, 477, 2760, doi: [`10.1093/mnras/sty574`](http://doi.org/10.1093/mnras/sty574)

(ref: mips_handbook) MIPS Instrument And MIPS Instrument Support Teams. 2011, 100, doi: [`10.26131/IRSA488`](http://doi.org/10.26131/IRSA488)

(ref: mizuno1990) Mizuno, A., Fukui, Y., Iwata, T., Nozawa, S., & Takano, T. 1990, ApJ, 356, 184, doi: [`10.1086/168829`](http://doi.org/10.1086/168829)

(ref: moe2017) Moe, M., & Di Stefano, R. 2017, ApJS, 230, 15, doi: [`10.3847/1538-4365/aa6fb6`](http://doi.org/10.3847/1538-4365/aa6fb6)

(ref: moe2018) Moe, M., & Kratter, K. M. 2018, ApJ, 854, 44, doi: [`10.3847/1538-4357/aaa6d2`](http://doi.org/10.3847/1538-4357/aaa6d2)

(ref: Novak2011) Novak, G. 2011, in Astronomical Society of the Pacific Conference Series, Vol. 449, Astronomical Polarimetry 2008: Science from Small to Large Telescopes, ed. P. Bastien, N. Manset, D. P. Clemens, & N. St-Louis, 50

(ref: novak1997) Novak, G., Dotson, J. L., Dowell, C. D., et al. 1997, ApJ, 487, 320, doi: [`10.1086/304576`](http://doi.org/10.1086/304576)

(ref: padoan2002) Padoan, P., & Nordlund, Å. 2002, ApJ, 576, 870, doi: [`10.1086/341790`](http://doi.org/10.1086/341790)

(ref: pattle2023) Pattle, K., Fissel, L., Tahani, M., Liu, T., & Ntormousi, E. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 193, doi: [`10.48550/arXiv.2203.11179`](http://doi.org/10.48550/arXiv.2203.11179)

(ref: Pattle2015) Pattle, K., Ward-Thompson, D., Kirk, J. M., et al. 2015, MNRAS, 450, 1094, doi: [`10.1093/mnras/stv376`](http://doi.org/10.1093/mnras/stv376)

(ref: Pattle2017) Pattle, K., Ward-Thompson, D., Berry, D., et al. 2017, ApJ, 846, 122, doi: [`10.3847/1538-4357/aa80e5`](http://doi.org/10.3847/1538-4357/aa80e5)

(ref: pattle2021) Pattle, K., Lai, S.-P., Di Francesco, J., et al. 2021, ApJ, 907, 88, doi: [`10.3847/1538-4357/abcc6c`](http://doi.org/10.3847/1538-4357/abcc6c)

(ref: Pattle2022) Pattle, K., Lai, S.-P., Sadavoy, S., et al. 2022, MNRAS, 515, 1026, doi: [`10.1093/mnras/stac1356`](http://doi.org/10.1093/mnras/stac1356)

(ref: pineda2012) Pineda, J. E., Maury, A. J., Fuller, G. A., et al. 2012, A&A, 544, L7, doi: [`10.1051/0004-6361/201219589`](http://doi.org/10.1051/0004-6361/201219589)

(ref: planckXXXV2016) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 586, A138, doi: [`10.1051/0004-6361/201525896`](http://doi.org/10.1051/0004-6361/201525896)

(ref: Rao2009) Rao, R., Girart, J. M., Marrone, D. P., Lai, S.-P., & Schnee, S. 2009, ApJ, 707, 921, doi: [`10.1088/0004-637X/707/2/921`](http://doi.org/10.1088/0004-637X/707/2/921)

(ref: Rodriguez2005) Rodrı́guez, L. F., Loinard, L., D’Alessio, P., Wilner, D. J., & Ho, P. T. P. 2005, ApJL, 621, L133, doi: [`10.1086/429223`](http://doi.org/10.1086/429223)

(ref: Sadavoy2018) Sadavoy, S. I., Myers, P. C., Stephens, I. W., et al. 2018, ApJ, 869, 115, doi: [`10.3847/1538-4357/aaef81`](http://doi.org/10.3847/1538-4357/aaef81)

(ref: sadavoy2019) Sadavoy, S. I., Stephens, I. W., Myers, P. C., et al. 2019, ApJS, 245, 2, doi: [`10.3847/1538-4365/ab4257`](http://doi.org/10.3847/1538-4365/ab4257)

(ref: sanchez_portal2014) Sánchez-Portal, M., , Marston, A., et al. 2014, Experimental Astronomy, 37, 453, doi: [`10.1007/s10686-014-9396-z`](http://doi.org/10.1007/s10686-014-9396-z)

(ref: scarrott1989) Scarrott, S. M., & Warren-Smith, R. F. 1989, MNRAS, 237, 995, doi: [`10.1093/mnras/237.4.995`](http://doi.org/10.1093/mnras/237.4.995)

(ref: schoier2002) Schöier, F. L., Jørgensen, J. K., van Dishoeck, E. F., & Blake, G. A. 2002, A&A, 390, 1001, doi: [`10.1051/0004-6361:20020756`](http://doi.org/10.1051/0004-6361:20020756)

(ref: Stark2004) Stark, R., Sandell, G., Beck, S. C., et al. 2004, ApJ, 608, 341, doi: [`10.1086/392492`](http://doi.org/10.1086/392492)

(ref: Stephens2022) Stephens, I. W., Myers, P. C., Zucker, C., et al. 2022, ApJL, 926, L6, doi: [`10.3847/2041-8213/ac4d8f`](http://doi.org/10.3847/2041-8213/ac4d8f)

(ref: tobin2016) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73, doi: [`10.3847/0004-637X/818/1/73`](http://doi.org/10.3847/0004-637X/818/1/73)

(ref: tobin2022) Tobin, J. J., Offner, S. S. R., Kratter, K. M., et al. 2022, ApJ, 925, 39, doi: [`10.3847/1538-4357/ac36d2`](http://doi.org/10.3847/1538-4357/ac36d2)

(ref: tsukamoto2023) Tsukamoto, Y., Maury, A., Commercon, B., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 317

(ref: vaillancourt2007) Vaillancourt, J. E., Chuss, D. T., Crutcher, R. M., et al. 2007, in Infrared Spaceborne Remote Sensing and Instrumentation XV, ed. M. Strojnik-Scholl (SPIE), doi: [`10.1117/12.730922`](http://doi.org/10.1117/12.730922)

(ref: vanderwiel2019) van der Wiel, M. H. D., Jacobsen, S. K., Jørgensen, J. K., et al. 2019, A&A, 626, A93, doi: [`10.1051/0004-6361/201833695`](http://doi.org/10.1051/0004-6361/201833695)

(ref: Vrba1976) Vrba, F. J., Strom, S. E., & Strom, K. M. 1976, AJ, 81, 958, doi: [`10.1086/111976`](http://doi.org/10.1086/111976)

(ref: walker1988) Walker, C. K., Lada, C. J., Young, E. T., & Margulis, M. 1988, ApJ, 332, 335, doi: [`10.1086/166659`](http://doi.org/10.1086/166659)

(ref: al1989) Wootten, A. 1989, ApJ, 337, 858, doi: [`10.1086/167156`](http://doi.org/10.1086/167156)

(ref: al1987) Wootten, A., & Loren, R. B. 1987, ApJ, 317, 220, doi: [`10.1086/165270`](http://doi.org/10.1086/165270)

(ref: wright2010) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, The Astronomical Journal, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: yang2016) Yang, H., Li, Z.-Y., Looney, L., & Stephens, I. 2016, MNRAS, 456, 2794, doi: [`10.1093/mnras/stv2633`](http://doi.org/10.1093/mnras/stv2633)

(ref: Yeh2008) Yeh, S. C. C., Hirano, N., Bourke, T. L., et al. 2008, ApJ, 675, 454, doi: [`10.1086/524648`](http://doi.org/10.1086/524648)

(ref: zamponi2021) Zamponi, J., Maureira, M. J., Zhao, B., et al. 2021, MNRAS, 508, 2583, doi: [`10.1093/mnras/stab2657`](http://doi.org/10.1093/mnras/stab2657)

(ref: Zhang2014) Zhang, Q., Qiu, K., Girart, J. M., et al. 2014, ApJ, 792, 116, doi: [`10.1088/0004-637X/792/2/116`](http://doi.org/10.1088/0004-637X/792/2/116)

(ref: Zielinski2021) Zielinski, N., Wolf, S., & Brunngräber, R. 2021, A&A, 645, A125, doi: [`10.1051/0004-6361/202039126`](http://doi.org/10.1051/0004-6361/202039126)

[^1]: PACS observing labels 1342205093, 1342205094, 1342227150, 1342227151

[^2]: SPIRE observing labels 1342205093, 1342205094

[^3]: MIPS observing label 4321536

[^4]: http://archive.esac.esa.int/hsa/whsa/

[^5]: WISE observing coadd id: 2477m243_ac51

[^6]: https://irsa.ipac.caltech.edu0/applications/wise/

</paper>

Write the methods card for this paper.