# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...695L..18M\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...695L..18M",
 "title": "ALMA 360 parsec, high-frequency observations reveal warm dust in the center of a z = 6.9 quasar",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Meyer, Romain A.",
 "n_authors": 6,
 "arxiv_id": "2502.14539",
 "doi": "10.1051/0004-6361/202453279",
 "alma_projects_linked_by_archive": [
  "2018.1.00012.S",
  "2021.1.01350.S"
 ]
}
```

Paper text:
<paper>
# ALMA 360 pc high-frequency observations reveal warm dust in the center of a $z=6.9$ quasar

# Introduction

The advent of ground-based sub-mm interferometry (ALMA/NOEMA) has opened a new window on the interstellar medium (ISM) of distant galaxies (cite: Carilli2013). Over the past two decades, fine structure lines and continuum emission in the rest-frame far-infrared (FIR) have been detected in increasing numbers of extragalactic sources. However, the interpretation of the FIR continuum emission relies on numerous assumptions about the underlying properties of cold ISM dust. The dust continuum modified blackbody emission peaks at rest-frame $\nu_{rest}\sim 3000-6000\ \rm{GHz}$, depending on the dust temperature. At high-redshift ($z\gtrsim 5$) high-frequency observations are thus required to accurately constrain the peak of the spectral energy distribution (SED) and infer the dust temperature, but have proved difficult to obtain. Even recent studies approach, but rarely go beyond, the peak of the dust SED at $z\gtrsim 6$ (cite: Novak2019; Shao2022; Witstok2023; Algera2024; Tripodi2024). FIR luminosities, star-formation rates (SFR), and sometimes gas mass estimates (when no suitable lines are present) are derived from the integrated dust SED, and are thus similarly uncertain. Even more challenging to obtain are resolved dust temperature measurements (and thus resolved SFR, gas and dust mass profiles), which require both high-resolution and at multiple frequencies, including at high frequencies. Resolved dust temperature measurements are however crucial to investigate the assumptions made about dust properties when analysing unresolved data, and offer a new route to probe the interstellar medium (ISM) of distant galaxies.

Of particular interest is the interaction between the active galactic nucleus (AGN) and the surrounding ISM. Numerous studies have searched for evidence of AGN feedback in the host galaxies of luminous $z>6$ quasars powered by supermassive black hole with masses ($M_{BH}>10^8-10^9 \ M_\odot$) and accretion rates close to the Eddington accretion rate, and thus expected to be the best places to look for AGN feedback in the first billion years. The majority of studies have focused on \[C II\] outflows, with mixed results (cite: Maiolino2012; Cicone2015; Bischetti2019; Novak2020; Izumi2021; Tripodi2022; Shao2022; Meyer2022; Tripodi2024). However, other forms of feedback signatures predicted by theoretical models, such as highly-excited gas tracers (cite: Carniani2019) or warm ($\gtrsim 100\ \rm{K}$) dust, have been comparatively less explored. In a recent study, (cite: DiMascia2021) show that radiation from the AGN is expected to heat the ISM in its vicinity. Although the mass of warm dust heated in this way is negligible, it can significantly affect the integrated dust SED at longer wavelengths. Disentangling the effect of the AGN on the dust is not only an important new tracer of AGN feedback, but is also crucial to measure accurately the star-formation heated dust continuum emission of their host galaxies to characterise them (cite: Scoville1976; Casey2012; Tsukui2023; FernandezAranda2025). So far however, such measurements have been impossible at $z>5$ due to the difficulty in obtaining the necessary high-resolution and high-frequency observations. Currently, resolved (i.e., sub-kpc) observations of high-redshift ($z>5$) sources are still rare and limited to a single continuum frequency around the \[C ii\] line (cite: Venemans2019; Walter2022; Meyer2023; Meyer2025; Neeleman2023; Rowland2024).

J2348–3054 is a luminous broad absorption line (BAL) quasar at $z=6.9$ discovered in VIKING imaging data (cite: Venemans2013). It hosts a black hole with a mass of $0.6-2.0\times10^{9}\ M_\odot$ (cite: DeRosa2014; MAzzucchelli2017; Farina2022). The host galaxy was first detected in unresolved \[C II\] and ALMA Band 3 continuum (cite: Venemans2015; Venemans2016; Venemans2020), and more recently was observed at $190\ \rm{pc}$ resolution in \[C II\] and continuum by (cite: Walter2022). The galaxy is infrared- and \[C II\]-luminous ($L_{\rm{TIR},8-1000\mu\rm{m}}=3.2\times10^{13}\ L_\odot,\ L_{[C II]}=1.9\times10^9\ L_\odot$), massive (dynamical mass $M_{\rm dyn}=10^{10.3\pm0.3}\ M_\odot$), with a very compact host galaxy (the central $r=530\ \rm{pc}$ containing $\sim 90\%$ of the continuum flux) and shows kinematics compatible with a rotating disk. Based on the surface brightness observed in the central resolution element, (cite: Walter2022) suggested that the continuum dust emission is optically-thick, with a dust temperature $T_d>130\ \rm{K}$ associated with an Eddington-limited starburst ($\Sigma_{SFR}> 10^4 M_\odot\ \rm{yr}^{-1} \ \rm{kpc}^{-2}$) in the central hundred parsec.

In this Letter, we present resolved ALMA Band 9 continuum observations (rest-frame 4623 GHz) probing the peak of the dust SED of J2348-3054. Combined with the previous Band 6 190 pc resolution data (cite: Walter2022), these observations enable us to derive the resolved dust temperature profile and dust opacity for the first time at this redshift. We confirm the presence of an increase in the dust temperature in the central hundred parsec and discuss the role of the quasar in heating the dust in the central region. This Letter showcases how ALMA is able to resolve the ISM properties of the first galaxies in the Universe. Throughout this Letter we use a concordance cosmology with $\Omega_\Lambda = 0.7, \Omega_M = 0.3, H_0 = 70\ \rm{km\ s}^{-1}$.

# The resolved dust properties of a $z=6.9$ quasar

![](J2348_fig1_band6_9.pdf)

We observed the $z=6.9$ quasar J2348–3054 in configuration C43-6 in ALMA Band 9 at a frequency of $670\ \rm{GHz}$ (Program ID #2021.1.01350.S, PI: Meyer). The final on-source time is $48\ \rm{min}$. J1924-2914 was used a bandpass calibrator, and J2349-3133 as phase calibrator. The data was reduced directly by the ALMA ARC Node. Baselines exceeding a phase RMS of $>100$ deg were manually flagged to minimize decoherence. Importantly, the maximum recoverable scale ($0.9\ensuremath{''}$) is similar to that of the $250\ \rm{GHz}$ continuum observations (cite: Walter2022). We imaged the Band 9 continuum using `CASA` version 6.2.1-7 (cite: THECASATEAM2022) with multiscale cleaning down to $2\sigma$ and a robust Briggs weighting of $r=0.5$ using the entire bandwidth ($15\ \rm{GHz}$) with a pixel scale of $0.005\ensuremath{''}$. Visual inspection of the datacube did not reveal significant absorption or emission in the spectrum. The final $670\ \rm{GHz}$ continuum map has a synthesized beam of $0.076\ensuremath{''}\times0.06\ensuremath{''}$, corresponding to a FWHM of $\sim 360\ \rm{pc}$ and an effective radius of $r=216\ \rm{pc}$, corresponding to a circular area with equivalent area to the beam (for comparison, the beam of the Band 6 data has an effective radius $r=110\ \rm{pc}$). The rms of the continuum map is 215 $\mu\rm{Jy\ beam}^{-1}$. Finally, we convolve the $250\ \rm{GHz}$ continuum map from (cite: Walter2022) down to the $670\ \rm{GHz}$ continuum beam using the `SpectralCube` package[^1], resulting in an rms of $6.2\ \mu\rm{Jy\ beam}^{-1}$ at $250\ \rm{GHz}$.

We find a peak continuum flux density of $3.2\pm0.2 \ \rm{mJy}$ at a position of RA=23:48:33.346, Dec=-30:54:10.307 (ICRS). We then integrate the $670\ \rm{GHz}$ continuum flux over an aperture of $r=0.2\ensuremath{''}$ centered on this peak pixel, and find $S_{\nu=670\ \rm{GHz}}= 9.1\pm1.1\ \rm{mJy}$ (where we have applied residual-scaling (cite: Jorsater1995; Walter1999) as implemented in the `interferopy` Python package). The aperture radius of $r=0.15\ensuremath{''}$ is chosen with a curve-of-growth analysis, where we find that the flux is consistent within uncertainties for all $r>0.15\ensuremath{''}$ apertures.

We show the resolved $670\ \rm{GHz}$ continuum observations alongside the original and convolved Band 6 continuum data in Fig. [1](#fig:fig1). The contours of the $250\ \rm{GHz}$ continuum are more tightly spaced than that of the $670\ \rm{GHz}$ continuum, suggesting a radial evolution of $S_{\nu=250\ \rm{GHz}}/S_{\nu=670\ \rm{GHz}}$ and thus the dust emission properties. To quantify this, we fit the SED in each pixel using the Band 6 and Band 9 resolved data (we further show in Appendix [6](#app:dirtybeam) that our results are not affected by the imprint of the two different dirty beams in the residuals). As (cite: Walter2022) showed, the dust emission is likely optically-thick in the inner center of the quasar host galaxy. We therefore fit the dust SED using the dust emission equation in the optically-thick regime and apply Cosmic Microwave Background contrast and heating corrections as per (cite: DaCunha2015) $$\begin{equation}
S_\nu\,=\,\Omega_A\,[B_\nu(T_d)-B_\nu(T_{\rm CMB})]\,[1-\exp(-\tau_\nu)]\,(1+z)^{-3},
\label{eq:snu}
\end{equation}$$ where $S_\nu$ is the frequency–dependent dust continuum flux density, $\Omega_A$ is the solid angle corresponding to the chosen aperture or beam size, $B_\nu(T_d)$ and $B_\nu$($T_{\rm CMB}$) are the black body emission ($B_\nu(T)=2\,h\,\nu^3\,c^{-2} [\exp(h\,\nu/(k_{\rm b} T)) -1]^{-1}$) from the dust and cosmic microwave background (CMB), with $h$ the Planck constant, $c$ the speed of light, $k_B$ the Boltzmann constant, and $\tau_\nu$ is the optical depth (as a function of frequency $\nu$) of the dust. In this work, we adopt the prescription of (cite: Draine2003) $\tau_\nu=\kappa_0 (\nu / \nu_{\rm ref})^\beta\,M_{\rm dust}\,A^{-1}$, where $\kappa_0=13.9$ cm$^2$ g$^{-1}$ is the absorption coefficient per unit dust mass, $\beta$ is the emissivity index, $\nu_{\rm ref}=2141$ GHz is the reference frequency for the dust emissivity $M_{\rm dust}$ is the dust mass and $A=\pi r^2$ is the area of the emitting region. With the dust opacity specified in this way, we can fit the resolved dust SED for the dust temperature, mass and $\beta$ slope. In this work, we assume $\beta=1.8$ which corresponds roughly to the median value found in statistical samples of galaxies and quasars observed in multi-band FIR observations at $z>5$ (cite: Witstok2023; Tripodi2024). Consequently, the only two free parameters of our fit are the dust temperature and mass (see Appendix [7](#app:thin_thick_differences) for a discussion of the non-degenerate nature of our temperature constraints).

![](J2348_temperature_tau_map_dustbeta1p8.pdf)

We show the resolved dust temperature and optical depth in Fig. [2](#fig:fig2_maps). We only fit pixels where the $670\ \rm{GHz}$ and $250\ \rm{GHz}$ continuum is detected at SNR$>3$, which essentially reduces to the $670\ \rm{GHz}$ SNR$>3$ criterion given the deeper sensitivity of the $250\ \rm{GHz}$ observations. The dust temperature peaks in the central beam to a beam-averaged temperature $88\pm2\ \rm{K}$, with an optical depth of $\tau_d= 1.8$ at $\nu_{rest}=1900\ \rm{GHz}$. Accordingly, the central ($r<216\ \rm{pc}$) total infrared luminosity ($8-1000\ \mu\rm{m}$) is $L_{\rm{TIR}} =  4.8\pm0.5 \times 10^{12}\ L_\odot$. Assuming that dust is heated by star-formation we would derive a central SFR of $717\pm75 \ M_\odot\ \rm{yr}^{-1}$ using the (cite: Kennicutt2012) relation. The corresponding star-formation rate densities (SFRD) $\Sigma_{SFR}=4.9\times10^{3}\ M_\odot \ \rm{yr}^{-1}\ \rm{kpc}^{-2}$. These values could be lower if the central pixel is contaminated by AGN torus hot dust emission and/or the cold dust is in part heated by the AGN, two possibilities we will discuss in Section [3](#sec:integrated_sed) and [4](#sec:feedback), respectively.

We note that the lower resolution of our observations (cite: Walter2022) results in lower dust temperatures, SFR, dust masses and opacities in the central resolution element as the radial density decreases rapidly away from the center of the galaxy. We can still treat the observed continuum in the central beam $360\ \rm{pc}$ resolution as an upper limit to the flux at $190\ \rm{pc}$ resolution (cite: Walter2022). Following the same method as above, we find an upper limit on the a central ($r<110\ \rm{pc}$) dust temperature $T_d < 149\pm5\ \rm{K}$, a total infrared luminosity ($8-1000\ \mu\rm{m}$), $L_{\rm{TIR}}< (10.5\pm0.6) \times 10^{12}\ L_\odot$, a central SFR of $< 1567\ M_\odot\ \rm{yr}^{-1}$ and SFRD $\Sigma_{SFR}< 4.1\times10^{4}\ M_\odot \ \rm{yr}^{-1}\ \rm{kpc}^{-2}$, in agreement with (cite: Walter2022).

# Constraining cold/warm ISM dust and the AGN hot dust torus emission

![](total_dust_sed.pdf)

An important consequence of our results concerns the standard interpretation of the FIR SED with a single, cold dust SED greybody model. As shown in Figure [3](#fig:total_sed), the ALMA Band 9 continuum data excludes the optically-thin model fitted by (cite: Walter2022) with a single temperature of $85\ \rm{K}$. The summed $SNR>3$ Band 6 and Band 9 pixels (see previous section) accounts for $\sim 80\%$ of the total flux, as cold ($T_d\lesssim 60\ \rm{K}$) dust emission is likely missing from the outskirts of the galaxy. Incidentally, the observed SED implies that the Herschel/PACS fluxes at $\nu_{\rm{obs}}\gtrsim 1000\ \rm{GHz}$ contain a non-negligible contribution from the AGN hot dust torus emission.

We thus proceed to fit simultaneously the resolved continuum at $250$ and $670$ GHz and the integrated FIR emission using all literature data at $100-2000$ GHz. In order to do this, we divide the resolved continuum data in four annuli starting with the central resolution element ($r<216$) up to $r=0.15\ensuremath{''}$. We then fit the dust continuum in each annuli (assuming optically-thick emission), and additionally include the contribution from hot dust torus emission in the central beam. To model the AGN torus we use `SKIRTOR` AGN models (cite: Stalevski2012; Stalevski2016) with a nearly face-on geometry ($i=10$°), motivated by the fact that J2348–3054 is a luminous type 1 quasar and the face-on disk \[C II\] kinematics (cite: Walter2022). We define the total log-likelihood as the sum of the individual log-likelihoods in each annuli and that of the integrated SED (see further Appendix [8](#app:dust_fit)).

We show the resulting best fits and uncertainties in Fig. [3](#fig:total_sed), and refer the reader to Appendix [8](#app:dust_fit) for details of the dust properties in each annuli and the parameters posterior distribution [^2]. We find that the central temperature decreases to $T_d(r<216\ \rm{pc})=72^{+2}_{-1}$ K when including an AGN hot torus contribution, although the strength of the torus emission and the central dust temperature are highly anti-correlated. Further high-resolution observations in Band 10 could break this degeneracy, where the AGN torus emission should dominate the central beam with a flux of $f_\nu(875\ \rm{GHz})=2.7\ \rm{mJy}$. Nonetheless, we still find lower dust temperatures at larger radii $T_d\sim60-66\rm{K}$ (see Appendix [8](#app:dust_fit)), indicating that the dust temperature gradient discussed in the previous section is robust.

Finally, we find that the summed FIR luminosity of the four annuli is $L_{FIR} = (8.78\pm0.10)\times 10^{12}L_\odot$, corresponding to SFR$=1307\pm15\ M_\odot\ \rm{yr}^{-1}$. This is $3.6\times$ lower than the previously-reported value of (cite: Walter2022) based on a single, optically-thin emission model, highlighting the importance of high-resolution observations to unveil optically-thick dust emission and potential AGN contamination.

![](fig5_comparison_diMascia.pdf)

# Is AGN radiation heating the dust in the center of J2348–3054?

Our results show that the dust temperature in J2348-3054 is $\sim 60\ \rm{K}$ in the outskirts ($\sim 0.3-0.5\ \rm{kpc}$) and rises up to $70-90\ \rm{K}$ in the central $r<360\ \rm{pc}$ (Fig. [2](#fig:fig2_maps)), and even up to $149\pm5\ \rm{K}$ in the central $r<110\ \rm{pc}$. An interesting question is whether the luminous BAL quasar or an associated intense starburst is primarily responsible for heating the dust. We compare our observations to three different simulations from (cite: DiMascia2021): 1) no AGN feedback, 2) spherical AGN feedback, and 3) conical AGN feedback (Fig. [4](#fig:simulation_comparison)). In particular, we compare the dust temperature profile, dust mass and luminosity fraction as a function of temperature for the most luminous source in their simulations ($M_{1450} = -21.4, -21.3, -25.4$ in their *noAGN*, *AGNsphere*, *AGNcone* runs). We find that the simulations without AGN feedback do not reproduce the warm dust temperature profile observed in the center of J2348–3054, and our observations are in general agreement with the *AGNsphere* model.

We have shown previously that the FIR SED of J2348–3054 indicates the presence of an AGN hot dust torus component at $\nu_{\rm{obs}}\gtrsim 1000\ \rm{GHz}$ (Fig. [3](#fig:total_sed)), whilst the resolved continuum observations at 250 and 670 GHz provides evidence for warm dust in the core of the galaxy. Although we cannot formally exclude that the central FIR luminosity and dust temperature in J2348-3054 is due to a starburst, these results and the better agreement of our resolved temperature observations with a model including AGN feedback (Fig. [4](#fig:simulation_comparison)) suggest that the high dust temperature is most likely due to AGN radiation heating the dust.

An important consequence of AGN radiation heating the dust is that the previous estimates of both the central and total SFR are too high. As a first-order estimate of this overestimation, we can consider excluding the contribution from the central $r<216\ \rm{pc}$ region, which accounts for $35\%$ of the continuum emission at $670\ \rm{GHz}$. Since the high temperature is likely AGN-related and not due to star-formation, the central FIR luminosity should not be converted to SFR. We note that our analysis in Section [3](#sec:integrated_sed) has revised the FIR luminosity by a factor $3.6$ compared to a single optically-thin greybody estimation (cite: Walter2022), implying a total $\sim 5\times$ overestimation of the total SFR when excluding the central resolution element. We note that this is a very rough estimate: in reality, the AGN can heat dust beyond the central beam, and conversely, the central beam is not completely devoid of star-formation. A more quantitative (but model-dependent) estimate of the overestimation of the SFR can be established with simulations, with (cite: DiMascia2023) suggesting that the SFR in J2348–3054 might be overestimated by a factor $\sim 10$, significantly above our back-of-the-envelope calculation. If confirmed in this and other high-redshift quasars, this would alter our view of $z>6$ quasar host galaxies as extreme starbursts, and bring their SFR in line with those observed in non-active galaxies such as REBELS and ALPINE (cite: Bouwens2020; Schouws2022; Bethermin2020; Schaerer2020).

A number of caveats apply to our analysis. Firstly, the luminosity of the most-luminous source in the *AGNsphere* model is much lower than that observed for J2348–3054. However, for the *AGNcone* simulation, the temperature profiles are relatively similar between the most luminous source (as luminous as J2348–3054 this time), and the average profile of all objects in the box. Secondly, whilst the simulations match best the observations when AGN feedback is switched on, other models and simulations might reproduce the observed temperature profiles. Finally, J2348–3054 is amongst the most compact and FIR-luminous high-redshift quasars observed with ALMA so far, which could either support the AGN heating scenario detailed here, or simply be an outlier in terms of SRFD.

# Summary and future prospects

We have reported the first high-frequency ($>600\ \rm{GHz}$) and high-resolution ($360\ \rm{pc}$) observations of a $z\sim 7$ quasar host galaxy, resolving the dust temperature and optical depth across its host galaxy. These observations sample the peak of the dust SED and spatially resolve it at 360 parsec resolution, leading to the following important results:

- We report the presence of a warm ($88\pm2\ \ \rm{K}$), optically-thick ($\tau_{\nu,\rm{rest}=1900\ \rm{GHz}}\sim 2$) dust component at the center ($r<216\ \rm{pc}$) of J2348–3054. Including a contribution from the AGN hot dust torus, we find a slightly reduced dust temperature $T_d= 72_{-1}^{+2}\ \ \rm{K}$, although further ALMA Band 10 high-resolution observations are necessary to conclude on the exact AGN torus contribution.

- The approximation of the unresolved dust emission as optically-thin is inadequate, leading to overestimated measurements of the FIR luminosity. Consequently, we show that the SFR of J2348–3054 is likely overestimated by a factor $\sim 3.6$. This could rise to a factor $\sim 5$ ($\sim0.7$ dex) if the contribution of the central $216\ \rm{pc}$ parsec is removed as the dust in this region is likely heated by AGN radiation.

- Comparison to simulations by (cite: DiMascia2021) show that the dust is likely heated by AGN radiation, with a strong preference for their spherical feedback prescription.

ALMA high-frequency, resolved observations of high-redshift sources have been missing until now. However, these results, obtained in only 48 minutes, show the potential of such observations to reveal and resolve the ISM properties of the most distant IR-luminous sources. With an abundance of lower-frequency high-resolution observations in the archive, it appears that a minimal investment in ALMA Band 8 to 10 observations would yield considerable progress in the study of galaxies and quasars in the first billion years of the Universe.

# Acknowledgements

We thank the anonymous referee for an insightful report that improved this Letter. RAM acknowledges support from the Swiss National Science Foundation (SNSF) through project grant 200020_207349. FW acknowledges support from the ERC Advanced Grant 740246 (Cosmic_Gas). This paper makes use of the following ALMA data: ASA/JAO.ALMA#2018.1.00012.S, ASA/JAO.ALMA#2021.1.01350.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work made use of the following Python packages: *numpy* (cite: Numpy2020), *matplotlib* (cite: Hunter2007), *scipy* (cite: Virtanen2020), *Astropy* (cite: TheAstropyCollaboration2018; TheAstropyCollaboration2022), *interferopy* (cite: interferopy).

52 natexlab

(ref: Algera2024) Algera, H. S. B., Inami, H., De Looze, I., et al. 2024, MNRAS, 533, 3098

(ref: Bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: Bischetti2019) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, Astronomy & Astrophysics, 630, A59

(ref: interferopy) Boogaard, L., Meyer, R. A., & Novak, M. 2021, Interferopy: analysing datacubes from radio-to-submm observations

(ref: Bouwens2020) Bouwens, R., Gonzalez-Lopez, J., Aravena, M., et al. 2020, Themiya Nanayakkara, 10, 19

(ref: Carilli2013) Carilli, C. & Walter, F. 2013, Annual Review of Astronomy and Astrophysics, 51, 105

(ref: Carniani2019) Carniani, S., Gallerani, S., Vallini, L., et al. 2019, MNRAS, 489, 3939

(ref: Casey2012) Casey, C. M. 2012, Monthly Notices of the Royal Astronomical Society, 425, 3094

(ref: Cicone2015) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, Astronomy and Astrophysics, 574, 14

(ref: DaCunha2015) Da Cunha, E., Walter, F., Smail, I. R., et al. 2015, Astrophysical Journal, 806, 110

(ref: DeRosa2014) De Rosa, G., Venemans, B. P., Decarli, R., et al. 2014, Astrophysical Journal, 790, 145

(ref: DiMascia2023) Di Mascia, F., Carniani, S., Gallerani, S., et al. 2023, MNRAS, 518, 3667

(ref: DiMascia2021) Di Mascia, F., Gallerani, S., Behrens, C., et al. 2021, Monthly Notices of the Royal Astronomical Society, 503, 2349

(ref: Draine2003) Draine, B. T. 2003, ApJ, 598, 1017

(ref: Farina2022) Farina, E. P., Schindler, J.-T., Walter, F., et al. 2022, ApJ, 941, 106

(ref: FernandezAranda2025) Fernández Aranda, R., Dı́az Santos, T., Hatziminaoglou, E., et al. 2025, arXiv e-prints, arXiv:2502.10503

(ref: Numpy2020) Harris, C. R., Jarrod Millman, K., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: Izumi2021) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2021, The Astrophysical Journal, 908, 235

(ref: Jorsater1995) Jorsater, S. & van Moorsel, G. A. 1995, The Astronomical Journal, 110, 2037

(ref: Kennicutt2012) Kennicutt, R. C. & Evans, N. J. 2012, Annual Review of Astronomy and Astrophysics, 50, 531

(ref: Maiolino2012) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, Monthly Notices of the Royal Astronomical Society: Letters, 425, L66

(ref: MAzzucchelli2017) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017, The Astrophysical Journal, 849, 91

(ref: Meyer2022) Meyer, R. A., Decarli, R., Walter, F., et al. 2022, The Astrophysical Journal, 927, 141

(ref: Meyer2023) Meyer, R. A., Neeleman, M., Walter, F., & Venemans, B. 2023, ApJ, 956, 127

(ref: Meyer2025) Meyer, R. A., Venemans, B., Neeleman, M., Decarli, R., & Walter, F. 2025, The Astrophysical Journal, 980, 20

(ref: Neeleman2023) Neeleman, M., Walter, F., Decarli, R., et al. 2023, ApJ, 958, 132

(ref: Novak2019) Novak, M., Bañados, E., Decarli, R., et al. 2019, The Astrophysical Journal, 881, 63

(ref: Novak2020) Novak, M., Venemans, B. P., Walter, F., et al. 2020, The Astrophysical Journal, 904, 131

(ref: Rowland2024) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, MNRAS, 535, 2068

(ref: Schaerer2020) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: Schouws2022) Schouws, S., Bouwens, R., Smit, R., et al. 2023, ApJ, 954, 103

(ref: Scoville1976) Scoville, N. Z. & Kwan, J. 1976, ApJ, 206, 718

(ref: Shao2022) Shao, Yali, Wang, Ran, Weiss, Axel, et al. 2022, A&A, 668, A121

(ref: Stalevski2012) Stalevski, M., Fritz, J., Baes, M., Nakos, T., & Popović, L. Č. 2012, MNRAS, 420, 2756

(ref: Stalevski2016) Stalevski, M., Ricci, C., Ueda, Y., et al. 2016, MNRAS, 458, 2288

(ref: TheAstropyCollaboration2022) The Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: TheAstropyCollaboration2018) The Astropy Collaboration, A., Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, The Astronomical Journal, Volume 156, Issue 3, article id. 123, 19 pp. (2018)., 156 \[\]

(ref: THECASATEAM2022) THE CASA TEAM, Bean, B., Bhatnagar, S., et al. 2022 \[\]

(ref: Tripodi2022) Tripodi, R., Feruglio, C., Fiore, F., et al. 2022, Astronomy & Astrophysics, 665, A107

(ref: Tripodi2024) Tripodi, R., Scholtz, J., Maiolino, R., et al. 2024, A&A, 682, A54

(ref: Tsukui2023) Tsukui, T., Wisnioski, E., Krumholz, M. R., & Battisti, A. 2023, MNRAS, 523, 4654

(ref: Venemans2019) Venemans, B., Neeleman, M., Walter, F., et al. 2019, The Astrophysical Journal, 874, L30

(ref: Venemans2013) Venemans, B. P., Findlay, J. R., Sutherland, W. J., et al. 2013, Astrophysical Journal, 779

(ref: Venemans2017) Venemans, B. P., Walter, F., Decarli, R., et al. 2017, The Astrophysical Journal, 851, L8

(ref: Venemans2020) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, The Astrophysical Journal, 904, 130

(ref: Venemans2015) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2015, The Astrophysical Journal, 816, 37

(ref: Venemans2016) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, The Astrophysical Journal, 816, 37

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Walter1999) Walter, F. & Brinks, E. 1999, The Astronomical Journal, 118, 273

(ref: Walter2022) Walter, F., Neeleman, M., Decarli, R., et al. 2022, The Astrophysical Journal, 927, 21

(ref: Witstok2023) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS, 523, 3119

# Impact of the dirty beam and residuals

![image](J2348_fig1_band6_9_clean_model_only.pdf) ![image](J2348_temperature_tau_map_cleanmodel_dustbeta1p8.pdf)

In this Appendix, we consider the impact of the dirty beam pattern on the dust temperature map inferred from the $250\ \rm{GHz}$ and $670\ \rm{GHz}$. Indeed, the final “cleaned" image produced by *tclean* is the sum of the model emission convolved with the clean beam and the residuals below $2\sigma$, which still contain the dirty beam pattern. This leads to ill-defined units, a well-known problem which we address using residual-scaling for the integrated fluxes (cite: Jorsater1995; Walter1999; Novak2019). Here, we aim to check that the dirty beam imprinted in the residuals does not drive the temperature fluctuations reported in this paper.

To do, we subtract the residual maps from the cleaned image to obtain the model emission convolved with the clean beam at $250\ \rm{GHz}$ and $670\ \rm{GHz}$. Such maps are thus free of any dirty beam imprints from the residual. We then rescale the flux in these maps to match the aperture-integrated residual-scaled fluxes reported in (cite: Walter2022) and this work. We then proceed to fit each individual as done in the main body of this work. We show the model-only continuum emission and the inferred dust temperature and opacity maps in Figure [5](#fig:maps_modelonly). We find that the dust temperature and opacity maps are consistent with what is observed when including the residuals, confirming that the gradients are real and not driven by the different dirty beams of the $250\ \rm{GHz}$ and $670\ \rm{GHz}$ continuum observations.

# Impact of the optically-thick/thin assumption on the observed SED and inference of the dust properties

In this Appendix, we briefly highlight the different behaviour of optically-thin and -thick dust emission models with dust temperature and mass. This is of particular importance to the inference made when fitting the observed SED, especially with high frequency observations.

In the case of optically-thin emission, adjusting the dust temperature and dust mass parameters can arbitrarily change the peak of the emission and the overall amplitude of the signal to match the data. In turn this requires a good sampling of the dust SED at various frequencies to constrain the dust properties. In the optically-thick case however, the emission is increasingly suppressed at high frequencies. The first consequence is that the dust SED peaks at lower frequencies than in the optically-thin case (see Fig. [6](#fig:illustration_opt_thick), left), and the apparent slope is flatter. Additionally, the amplitude of the SED at high frequencies plateaus when the optical depth (or equivalently the dust mass in a fixed area) increases further. Thus the high-frequency observations better constrain the dust temperature in the optically-thick case, even with a smaller number of constraints on FIR SED (see Fig. [6](#fig:illustration_opt_thick)). This is what enables us to determine relatively accurate resolved dust temperatures with only two high-resolution images in Band 6 and 9.

![image](illustration_optically_thick_thin.pdf) ![image](illustration_optically_thick.pdf)

# Averaged Dust properties in radial annuli

In this appendix, we detail the fitting procedure for the resolved and integrated FIR SED in J2348-3054, and present the resulting dust properties as a function of radius. The simultaneous fit to the resolved and integrated continuum observations is done as follows. We first assume that the AGN hot dust torus emission is unresolved at 360 pc resolution, and solely located at the peak of the Band 9 continuum observation. We then extract the fluxes in the central beam, and $3$ annuli spanning up to $0.15\ensuremath{''}$. For each annuli, we assume that the emission can be reproduced by an optically-thick dust emission model, and for the central resolution element we combine the dust emission with the hot dust torus emission. The total unresolved FIR SED is modeled with the sum of the four individual models detailed above. The total log-likelihood we aim to maximize is then simply the sum of the log-likelihoods for the model of each annuli compared to the resolved data, to which we add the likelihood of the global SED. As we assume errors are gaussian and i.i.d, the log likelihood is simply the sum of the $\chi^2$ for each annuli and the integrated SED. We fit the data at hand for each 1920 SKIRTOR models (cite: Stalevski2012; Stalevski2016) with nearly face-on inclination $i=10\textdegree$ (given that J2348-3054 is a luminous quasar but not a blazar), and select the model with the highest likelihood.

We show the parameter posterior distribution in Fig. [7](#fig:posterior), with most parameters being well constrained. The dust mass and temperature (and the hot dust torus contribution in the case of the central beam) are correlated for each annuli and the central beam, although correlation for parameters across radii are not significant. We then summarise the inferred dust temperatures, masses and FIR luminosities for each annuli in Table [\[tab:annuli_sed\]](#tab:annuli_sed). For completeness we also present the same parameters inferred for independent fits to the each annuli where only the Band 6 and Band 9 data is considered, without the constraints from the total unresolved SED and without an AGN contribution.

![](corner_plot_dust_fit_annuli_simultaneous.pdf)

cccccccccc & &\
$r_{\rm{min}}$ & $r_{\rm{max}}$ & $S_\nu(250\  \rm{GHz})$ & $S_\nu(670\ \rm{GHz})$ & $M_d$ & $T_d$ & $L_{\rm{TIR}}$& $M_d$ & $T_d$ & $L_{\rm{TIR}}$\
$[\rm{pc}]$ & $[\rm{pc}]$ & \[mJy\] & \[mJy\] & \[$10^8 M_\odot$\] & \[K\] & \[$10^{12}\ L_\odot$\] & \[$10^8 M_\odot$\] & \[K\] & \[$10^{12}\ L_\odot$\]\
& 216 & $1.086\pm0.006$ & $3.24\pm0.25$ & $1.17\pm 0.11$ & $88.2\pm2.3$ & $4.81^{-0.48}_{+0.47}$ & $5.9^{+1.4}_{-3.2}$ &$72.5^{+2.6}_{-0.4}$ & $2.23_{-0.02}^{+0.34}$\
216 & 253 & $0.596\pm0.010$ & $2.41\pm0.42$ & $0.48\pm0.10$ & $63.3\pm5.7$ & $1.69^{-0.51}_{+0.67}$ & $0.72_{-0.10}^{+0.10}$ & $64.3^{+3.3}_{-4.4}$ & $2.73_{-0.61}^{+0.60}$\
253 & 380 & $0.504\pm0.014$ & $1.80\pm0.58$ & $0.17\pm0.11$ & $61.0\pm17.9$ & $0.98^{-0.87}_{+0.52}$ & $0.34_{-0.11}^{+0.11}$ & $60.7^{+13.5}_{-7.2}$ & $1.94_{-0.64}^{+2.23}$\
380 & 506 & $0.147\pm0.018$ & $1.03\pm0.74$& $0.06\pm0.13$ & $62.6\pm60.2$ & $0.52\pm0.52$ & $0.09_{-0.08}^{+0.18}$ & $66^{+82}_{-20}$ & $1.87_{-1.57}^{+15.75}$\
& & & $1.88\pm0.2$$^{a}$ & – & $7.5\pm1.2$$^{a}$ & $5.7^{+3.3}_{-2.1}$ & – & $8.78\pm0.10$

Table notes: The dust slope $\beta$ is fixed to $\beta=1.8$. See further Appendix [8](#app:dust_fit) for details on the simultaneous fitting of the resolved and integrated FIR SED. $^{a}$ Independent fits to the Band 6+9 resolved data, without the total SED constraint. Note that the sum of the luminosity and mass of the independent fits to each annuli are likely biased, as the sum of their best-fit SED is not constrained - and does not reproduced well - the total FIR SED observations. These results are only given here for completeness. $^{b}$ Joint fit to the unresolved and resolved data detailed further in appendix [8](#app:dust_fit). The best-fit annuli SEDs and their sum (including the AGN torus contribution) are shown in Fig. [3](#fig:total_sed).

[^1]: <https://spectral-cube.readthedocs.io/en/latest/>

[^2]: For future reference the best-fit SKIRTOR AGN model is the *t3_p1.5_q1.5_oa80_R10_Mcl0.97_i0_sed.dat* model. We refer to (cite: Stalevski2016) for the naming convention and physical parameters of the model.

</paper>

Write the methods card for this paper.