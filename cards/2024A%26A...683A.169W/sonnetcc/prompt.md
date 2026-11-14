# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...683A.169W\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...683A.169W",
 "title": "JWST discovers an AGN ionization cone but only weak radiatively driven feedback in a powerful z ≈ 3.5 radio-loud AGN",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Wang, Wuji",
 "n_authors": 10,
 "arxiv_id": "2401.02479",
 "doi": "10.1051/0004-6361/202348531",
 "alma_projects_linked_by_archive": [
  "2021.1.00576.S"
 ]
}
```

Paper text:
<paper>
# *JWST* discovers an AGN ionization cone but only weak radiative-driven feedback in a powerful $z$$\approx$3.5 radio-loud AGN

# Introduction

Active galactic nucleus (AGN) feedback can be categorized into either quasar-mode, where the output from the supermassive black hole (SMBH) is coupled radiatively to the gas, or radio-mode, where the feedback is due to the kinetic energy of the jet (cite: Fabian_2012; Harrison_2017). The quasar-mode is known to be prevalent (cite: Harrison_2014). The radio-mode also plays an important role in AGN–gas interactions, leading to quenching. This is especially true in massive galaxies in the early Universe, as shown by both numerical simulations and observations (cite: Heckman_2014; Mukherjee_2018; Kondapally_2023). Indeed, despite the relatively short lifetime of a powerful jet ($\sim 10^{7}$ yr), observations indicate that it can still significantly impact the host galaxy (cite: Nesvadba_2006a; Miley_2008). Relativistic jets trigger shocks and drive outflows through an expanding over-pressured bubble (cite: Begelman_1989). While hydrodynamic simulations demonstrated that jets have the ability to interact with the interstellar medium (ISM) out to several kiloparsecs (cite: Dugan_2017; Mukherjee_2021), observations paint a more complicated picture. Specially, jet–ISM interactions are found to be different between AGN with intermediate radio power (cite: Mullaney_2013) and those with higher power (cite: Mukherjee_2016). Moreover, it is difficult to study the feedback mechanisms of the most powerful jetted AGN due to observational limitations and the simultaneous presence of energetic, quasar-mode feedback.

High-redshift radio galaxies (HzRGs) are the best targets to test AGN feedback in massive host galaxies (cite: DeBreuck_2010) because the gas, dust and stellar populations in their host galaxies can be observed without contamination from the bright, point-like quasar light. In contrast to low-$z$, where radio-mode AGN are believed to have low black hole accretion rates with inefficient radiative luminosity, HzRGs are observed to have both vigorous radio-mode and quasar-mode energy output (cite: vernet_2001; Nesvadba_2007a; Nesvadba_2017a; Nesvadba_2017b). There are numerous studies focused on the outflows on several to 10s of kpc scale for both low- and high-redshift radio galaxies, which find evidence of them being jet-driven (cite: Tadhunter_2001; Tadhunter_2007; Nesvadba_2006a; Nesvadba_2007a). A closer look (scales of tens of pc) at the feedback in the vicinity of radio AGN is possible at low-$z$ (cite: Tadhunter_2003). However, spotting the warm, ionized quasar outflow around Cosmic Noon (cite: MandD_2014) down to sub-kpc scales is challenging. Therefore, it is still unclear how energetic jet-mode and quasar-mode feedback couple with the ISM, how efficient these mechanisms are in driving outflows and on which scales the different feedback mechanisms dominate. All these are critical issues to be addressed before we can achieve a deeper understanding of quenching of star formation in these massive host galaxies (cite: Falkendal_2019).

We can now finally move a step forward thanks to the Near Infrared Spectrograph (cite: Jakobsen_2022) onboard *JWST*, which provides an order of magnitude improvement in sensitivity. At least for HzRGs, there is evidence that the morphology and/or kinematics of the ionized ISM and even CGM (circumgalactic medium) gas are impacted by jets (cite: Nesvadba_2008; Nesvadba_2017b; Falkendal_2021; wang2023), which may indicate their role in feedback. However, the situation may be different when using deeper observations (cite: Wylezalek_2017). For example, how does the ISM of HzRGs look in the vicinity of and inside the host galaxies (e.g., $\sim 10$ to 20 kpc)? NIRSpec integral field unit (IFU) observations of powerful quasars at Cosmic Noon have already revealed the detailed ionization mechanisms and quantified the outflow rates on galactic scales (cite: Wylezalek_2022q3d; Vayner_2023Q3D; Vayner_2023Q3D_2). NIRSpec will revolutionize our view of the inner ISM of HzRGs where the detailed physics are still unclear. A resolution-matched comparison can finally be done for high- and low-$z$ radio AGN. NIRSpec IFU will also enable observational tests of simulated jet feedback (cite: Mukherjee_2016) in the early Universe.

In this work, we present the first *JWST* view of the ionized ISM of a $z\sim3.5$ radio-loud AGN. In Section [2](#sec:data_process), we describe the observations and data processing. We then show in Section [3](#sec:results) the morphology of the warm ionized gas and identification of the observed optical emission lines from the extracted spectra. Finally, we discuss the impact of the jet on the ISM using line-ratio diagnostics and summarize in Section [4](#sec:summary). Throughout this paper, we assume a flat $\Lambda$ cosmology with $H_{0} = 70\, \rm{km\,s^{-1}\,Mpc^{-1}}$ and $\Omega_{m}=0.3$. Following this cosmology, $\rm{1\,arcsec=7.25\, kpc}$ at the redshift of 4C+19.71. Throughout this work, we use $z=3.5892\pm0.0004$ as determined from atomic carbon, $[C i]$(1-0) ($\nu_{\rm rest}=492.16\,\rm GHz$), as the systemic redshift (cite: Falkendal_2021; kolwa2023). Due to the relatively large synthesized beam (cite: Falkendal_2021) of the ALMA \[C i\](1-0) observation, it is uncertain whether the molecular gas is located in the host galaxy (Appendix [8](#app:sys_z)). Though *JWST* observes in a vacuum, we label the emission lines with their air wavelengths in $\mathrm{\mathring{A}}$ following the convention, for example \[O iii\]5007.

![](Figures/Figure1_combine_black.pdf)

![](Figures/Spectrum_1D_full_view_combine.pdf)

# 4C+19.71, observation and data processing

() is the first target observed as part of the *JWST* Cycle 1 General Observers program (ID 1970, PI: Wuji Wang) “Zooming into the monster’s mouth: tracing feedback from their hosts to circumgalactic medium in $z=3.5$ radio-loud AGN". The program includes four HzRGs with a diversity of star formation rates and radio jet morphologies (cite: vanOjik_1996; Carilli_1997; Nesvadba_2007a; Falkendal_2019). We selected them to have similar redshifts ($z\simeq3.5$) to maximize the number of emission lines in a single observational setting.

4C+19.71 has a FR II-type radio jet with a double-sided lobe extending over $\gtrsim 60$ kpc (cite: Fanaroff_1974; Carilli_1997). Besides the radio data, there are multi-wavelength studies available for 4C+19.71 (cite: Pentericci_1999; Maxfield_2002; Seymour_2007; DeBreuck_2010). The HzRG is surrounded by an X-ray halo and \[O iii\]$5007$ nebula with similar extension. Both are elongated in the same direction as the jet (cite: Armus_1998; Smail_2012; Nesvadba_2017a). A more extended, $\sim 100$ kpc Ly$\alpha$ nebula is also detected around the radio AGN. It also shows an elongated morphology along the jet axis, even beyond the radio lobes (cite: Falkendal_2021; wang2023).

The stellar mass of the host galaxy of 4C+19.71 is constrained to be $\lesssim 10^{11.1}\,\mathrm{M_{\ensuremath{\odot}}}$. It forms stars at the rate of $\sim84\,\mathrm{M_{\ensuremath{\odot}}\,yr^{-1}}$ (cite: Falkendal_2019). Finally, there is significant molecular gas in the host (cite: kolwa2023).

The observation of 4C+19.71 was conducted on UT 2022 October 30 with NIRSpec in IFU mode (cite: Boeker_2022; Jakobsen_2022). We selected G235H/F170LP as the disperser/filter setup*,* which covers $1.70-3.15\,\mathrm{\mu m}$ in the observed frame or $\sim3700-7620\,\mathrm{\AA}$ in the rest frame. The combination of filter and grating offers the spectral resolution of $85-150\,\mathrm{km\,s^{-1}}$. This ensures major optical emission lines seen in type-2 AGN (\[O ii\]$3726,\,3729$ to H$\alpha$, including \[S ii\]$6716,6731$) can be observed at once (cite: Zakamska_2003). We adopted a 9-point dither pattern and the improved reference sampling and subtraction (IRS$^2$) read-out pattern. The total on-source exposure time was 3.7 h. We designed the leakage exposure, 0.4 h, to identify light leaking through the failed open shutters on the microshutter array (MSA) at the first dither position.

We downloaded the raw data from the Mikulski Archive for Space Telescopes (MAST). The data were processed with the *JWST* Science Calibration pipeline[^1] (v1.9.4) with the Calibration Reference Data System (CRDS) context file jwst_1041.pmap. Our procedure is similar to (cite: Vayner_2023Q3D), executing the standard first and second stages of the pipeline with one modification. Specifically, we used the “emsm" method instead of “drizzle" during the data cube construction step to reduce the low-frequency ripples due to undersampling. The third and final stage of the processing is to combine cubes from different exposures into the final cube. We instead used the script from (cite: Vayner_2023Q3D), who applied the Python package `reproject` because the third stage of the pipeline falsely rejects the bright emission peak while keeping some noise spikes. During this step, sigma clipping ($2\sigma$) was also included to reject outliers. The data cube was resampled to have a pixel scale of 0.05$''$. We processed the raw NIRSpec IFU data of the standard star TYC 4433-1800-1 (PID 1128) for flux calibration. Finally, we performed an additional background subtraction to the flux-calibrated science data cube to alleviate negative background continuum seen in source-free regions. The size of the point spread function (PSF) of the NIRSpec IFU depends on wavelength and spatial position. We mark the full width at half maximum (FWHM) of the PSF constructed in (cite: Vayner_2023Q3D_2) in Fig. [1](#fig:IFU+spec)a.

Several works based on NIRSpec IFU observations report a World Coordinate System (WCS) offset in the final data cube (cite: Wylezalek_2022q3d; Perna_2023). We aligned the continuum emission position of the west foreground galaxy in our NIRSpec cube to the Hubble Space Telescope (*HST*) WFPC2 image and used this new WCS in the following analysis (cite: Pentericci_1999). The astrometry of the *HST* image was corrected by cross-matching with *Gaia* DR3 targets (cite: gaiaDR3_2023). Our final WCS solution resulted in a shift of $\Delta$RA$=0.43\ensuremath{''}$ and $\Delta$Dec$=-0.22\ensuremath{''}$ compared to the pipeline output WCS. We discuss the astrometry correction in Appendix [5](#app:astrometry).

We also present the ALMA Band 8 observation of 4C+19.71. This observation was carried out under program ID 2021.1.00576.S (PI: Wuji Wang) on UT 2022 June 17. In this work, we use only the archived image at $\nu_{\rm obs}=$400.3 GHz to show the position of the cold dust emission. A detailed analysis of the ALMA observations is beyond the scope of this paper and will be presented in a forthcoming paper.

![](Figures/CygA_compare.pdf)

# Results

In this paper, we inspect both the 2D morphology and 1D spectrum of the warm ionized gas. Given the signal-to-noise ratio (S/N) of the optical emission lines covered in our setting, we choose the \[O III\]5007 ($[O iii]$ hereafter if not specified) as the proxy for the morphology. It is extensively used in the studies of AGN narrow line regions (cite: Husemann_2013b; Harrison_2014; Wylezalek_2016b). This is the first time that the distribution of ionized gas around a $z>3.5$ radio loud AGN is seen with $\lesssim1\,$kpc resolution.

## Morphology of the extended ionized nebula

(cite: Armus_1998) observed the \[O iii\] emission of 4C+19.71 with Keck narrow-band imaging. They reported the central \[O iii\] (i.e., a similar region as observed in the field of view of the NIRSpec IFU) has an elongated morphology along the north-south direction with two distinctive parts. We show the first zoom-in view of the \[O iii\] nebula of 4C+19.71 in Fig. [1](#fig:IFU+spec). We produce three pseudo-narrow-band images and show their composite in Fig. [1](#fig:IFU+spec)a. The individual images are shown in Fig. [1](#fig:IFU+spec)(b1), (b2) and (b3) for the blue wing (\[$-700,-500$\] $\mathrm{km\,s^{-1}}$), systemic redshift (\[$-100,100$\] $\mathrm{km\,s^{-1}}$) and red wing (\[$500,700$\] $\mathrm{km\,s^{-1}}$), respectively. On each of the images, there are two distinct peaks located south and north which roughly align with the jet axis (cite: Carilli_1997). Based on \[O iii\] gas kinematics probed by VLT/SINFONI near the jet hot spot positions (cite: Nesvadba_2017b), we assume the southern jet is the approaching one. There is no doubt that 4C+19.71 has a hidden quasar (cite: Seymour_2007; DeBreuck_2010; Falkendal_2019). Assuming the ionization cone of the quasar is aligned with the jet axis (cite: Drouart_2012), it is likely that we are observing, in both the south and north regions, the foreground and background parts of the cone.

To assist in studying the morphology, we show example \[O iii\]$4959,5007$ spectra extracted at four different locations (Fig. [1](#fig:IFU+spec)(c1) to (c4)). We note that the analysis of the extended emission-line region kinematics is not the focus of this paper. The per-spatial-pixel (spaxel) spectra are fitted using `q3dfit` (cite: Rupke_2023q3dfit), which is a Python tool for analyzing *JWST* IFU data based on the software `IFSFIT` (cite: Rupke_2014; Rupke_2021)[^2]. It is clear that at least three different kinematic components are present on galactic scales ($\lesssim$10$\,$kpc). This is especially obvious for the gas in the south, with three distinct peaks present (e.g., Fig. [1](#fig:IFU+spec) (c2)). We stress that we refer to the component closest to $0\,\mathrm{km\,s^{-1}}$ as “systemic” and the others as “blue” or “red” depending on their relative velocity shift with respect to the systemic component. At this point, it remains unclear whether they are the blueshifted or redshifted outflowing gas clouds.

The most striking morphological features are the spatially extended emission blobs and filamentary structures around the systemic velocity (Fig. [1](#fig:IFU+spec)(b1)). For example, both components detected in the east filament (Fig. [1](#fig:IFU+spec)(c1)) and the gas of the northern spot (Fig. [1](#fig:IFU+spec)(c3)) all have $|\Delta v| <300\,\mathrm{km\,s^{-1}}$. Neither the previous narrow-band imaging nor ground-based IFU could resolve these components spatially and spectrally (cite: Armus_1998; Nesvadba_2017b). With the relatively small field of view (FoV) of the NIRSpec IFU, the jet hot spots are not captured which are presumed to be the regions with the most energetic jet-gas interactions. Given the fact that these extended filamentary features sit at the systemic redshift, we arrive at the conclusion that they are not associated with the outflow but may be high density gas clumps. Their morphologies may have been disrupted by the jet-induced bubble (cite: Mukherjee_2016; Dugan_2017). Indeed, at least in the example spectra extracted at the east filament, we observe a broad component indicative of disruption by the jet (FWHM$= 1052\,\mathrm{km\,s^{-1}}$).

![](Figures/q3dfit_line_ratio_int_paper.png)

![](Figures/q3dfit_line_ratio_diagnostic_int_4panel_paper.png)

## Continuum emission

We overlay in Fig. [1](#fig:IFU+spec)b the continuum emission detected in our ALMA Band 8 observation, which likely indicates the location of the cold dust emission heated by the newly formed stellar population (cite: Herrera-Camus_2021). In Fig. [1](#fig:IFU+spec)d we show that the AGN position (NIRSpec continuum, Sect. [4.1](#subsec:low_z_comp)) agrees with the ALMA dust location within their uncertainties. The $1\sigma$ uncertainty, $\sim0.02\ensuremath{''}$, of the ALMA dust position is estimated using $\mathrm{pos_{acc}=beam_{FWHP}/(S/N)/0.9}$ with $\rm beam_{FWHP}\simeq0.2\ensuremath{''}$ and S/N$\simeq10$ (see Appendix [5](#app:astrometry) for the $1\sigma$ uncertainty, $\sim0.06\ensuremath{''}$, of the NIRSpec continuum) [^3].

A previous *HST* image (WFPC2/F702W) indicates other two objects in the NIRSpec IFU FoV (cite: Pentericci_1999). They are also seen in our NIRSpec observations (Fig. [1](#fig:IFU+spec)a). We label them G1 and G2 for the galaxy in the west and east, respectively. G1 is used as the WCS alignment reference in Section [2](#sec:data_process). They are identified as foreground galaxies with $z\simeq1.786$ for G1 and $z\simeq1.643$ for G2. Their spectra and emission line identifications are shown in Appendix [6](#app:fore_galaxy).

## Emission line identification

|                                     | central comp. | red comp.  | blue comp.  |
|:------------------------------------|:-------------:|:----------:|:-----------:|
| $\Delta v\, [\mathrm{km\,s^{-1}}$\] |  238$\pm10$   | 572$\pm30$ | -148$\pm20$ |
| FWHM$\, [\mathrm{km\,s^{-1}}$\]     |  445$\pm10$   | 412$\pm30$ | 1669$\pm20$ |

: Fitted kinematic results from the 1D spectrum at nucleus.

Table notes: The velocity shift is with respect to the systemic redshift from (cite: kolwa2023), $z=3.5892$.

We present the identification of the emission lines in Fig. [2](#fig:spec_full). This is the first time that optical nebular emission lines from \[O ii\]$3726,3729$ to \[S ii\]$6716,6731$ are observed for $z\simeq3.5$ HzRGs with the spectral resolution of $85$ to $150\,\mathrm{km\,s^{-1}}$. This makes it possible to investigate the ionization mechanisms and metallicities (cite: BPT_1981; Veilleux_1987; Kauffmann_2003; Groves_2004; Groves_2006; Kewley_2001; Kewley_2006; Kewley_2013; Wylezalek_2017).

We extracted a spectrum from a $0.2\ensuremath{''}\times0.2\ensuremath{''}$ or $1.4\times1.4\,\mathrm{kpc}^{2}$ ($4\times4$ pix$^{2}$) square aperture near the position of the continuum emission peak. The aperture and size were chosen to also include the \[O iii\] emission peak which maximizes the S/N for emission line identification. The aperture was aligned with the extension of the brightest \[O iii\] emission blob. We show this aperture in the black box in Fig. [1](#fig:IFU+spec)d. The spectrum is presented in Fig. [2](#fig:spec_full). We summed over five wavelength pixels around the systemic zero (velocity range of $\sim270$ to $\sim150\,\mathrm{km\,s^{-1}}$) to calculate the line $S/N$ for identification. We identify $\sim24$ emission lines (doublets) with S/N$>3$. The ones with S/N$\gtrsim10$ are marked by red lines. We implemented a visual check by examining the spatial distribution of lines with $3<$S/N$<10$. The spatially resolved ones are marked by black dashed lines.

We fitted the spectrum with `q3dfit`. We used three kinematic components. The line center and width of the same component are connected for different lines. We present these kinematic results in Table [1](#tab:1Demission_kine). We refer to them as central, red and blue components based on their velocity shifts. In Appendix [7](#app:linelist), we report fitted line fluxes from the 1D spectrum.

# Discussion and Summary

## Comparison to Cygnus A

Cygnus A (3C405) is the most powerful radio AGN in the local Universe with comparably high radio power as 4C+19.71 (cite: Carilli_1996). This makes it the perfect target to compare with the properties of the warm ionized ISM gas using the common optical tracers (cite: Fosbury_1999; Vernet_2001_thesis). Using the spectropolarimeter on the Keck telescope, (cite: Ogle_1997) observed the nebular emission lines of Cygnus A. We overlay our 1D spectrum (Fig. [2](#fig:spec_full)) with the spectrum of Cygnus A extracted at its nucleus in Fig. [3](#fig:spec_comp). The extraction aperture of Cygnus A is $\sim1"\times1.1"$ which corresponds to $1.1\times1.2\,\mathrm{kpc}^{2}$ and is similar to the aperture used for 4C+19.71 ($1.4\times1.4\,\mathrm{kpc}^{2}$). This is the first time that a rest-frame optical spectrum of a $z\gtrsim 1$ radio AGN can be studied in comparable detail as a local example.

To first order, the continuum shape of 4C+19.71 is consistent with Cygnus A. We note that the Cygnus A spectrum is corrected for Galactic reddening and had its host galaxy continuum subtracted (cite: Ogle_1997). Though there might be contamination of continuum (i.e., due to the leak of from the MSA) for our NIRSpec data, we conclude that the emission from evolved stellar population in the host of 4C+19.71 is faint, i.e., the spectrum is dominated by the (possibly scattered) light of the hidden AGN. This indicates that the stellar population has a sub-dominant contribution in the regions near the AGN.

The relative emission line fluxes are comparable for 4C+19.71 and Cygnus A at least from \[O ii\]$3726,3729$ to \[O iii\]. We conclude that, to first order, AGN photoionization mechanisms dominate the inner parts of these two galaxies. The similarity of the Balmer lines, H$\beta$, H$\gamma$ and H$\delta$ suggests the ISM gas conditions are similar (cite: Osterbrock_2006). The dissimilarity of the flux at redder wavelength (e.g., \[$O i$\], \[$N ii$\] and \[$S ii$\]) may suggest differences in gas enrichment.

(cite: vanBemmel_2003) proposed that the quasar wind-driven outflowing dust clouds scatter the optical line emitting photons in Cygnus A. We know there are at least three kinematic components present in the nucleus of 4C+19.71 (Sect. [3.1](#subsec:O3morphology)). We defer to a future publication the detailed study of the gas kinematics to unveil the spatially resolved gas motions and constrain the ISM distribution.

## Line ratio diagnostics and ionization mechanisms

To study the extended irregular ISM structures around the hidden powerful radio AGN (Sect. [3.1](#subsec:O3morphology)), we construct line ratio maps and compare them to emission line diagnostics (cite: Groves_2004; Kewley_2006; Groves_2006). We use `q3dfit` to fit the cube to systematically separate the blended emission lines and account for doublets. The fitted region was selected based on the \[O iii\] narrow-band image with a S/N cut of $>5$ (white contour in Fig. [4](#fig:q3dfit_line_ratio_map)). We limit the spatial study in this paper to the six brightest emission lines: \[O ii\]$3726,3729$, H$\beta$, \[O iii\]$4959,5007$, \[O i\]$6300$, \[N ii\]$6548,6583$, H$\alpha$ and \[S ii\]$6716,6731$. These lines are fitted simultaneously with the same velocity shift and line width for the corresponding components (cite: Zakamska_2016b). Following (cite: Vayner_2023Q3D), we ran the fit with 3, 2 and 1 as the maximum number allowed Gaussian components. We performed a visual inspection to determine the best fit for each spaxel. In the following discussions, we sum the the fluxes of the doublet \[O ii\]$3726,3729$ and \[S ii\]$6716,6731$, respectively. We use the fluxes of the individual \[O iii\]$5007$ and \[N ii\]$6583$ lines, respectively. Hereinafter, we omit the wavelength when referring to the line name. The line ratio maps and diagnostics based on the fit are shown in Fig. [4](#fig:q3dfit_line_ratio_map) and [5](#fig:q3dfit_line_ratio), respectively. As mentioned before, a kinematical study of the ionized ISM is beyond the scope of this paper; we only derive the line ratios of the integrated line fluxes of all velocity components.

The Balmer line ratios are sensitive to dust attenuation (cite: Veilleux_1987; Osterbrock_2006). We present the color excess, $E(B-V)$, maps based on the fitted H$\alpha$/H$\beta$ flux ratios in Fig. [4](#fig:q3dfit_line_ratio_map)a. The map is constructed using an intrinsic flux ratio of 3.1 assuming Case B recombination in AGN ionization and a (cite: Calzetti_2000) extinction law following (cite: Vayner_2023Q3D). We find that there is a dusty region with high $E(B-V)$$\sim1$ around the AGN position, coincident with our ALMA dust continuum (pink contours in Fig. [4](#fig:q3dfit_line_ratio_map)a), confirming the importance of dust causing extinction near the AGN. This spatial coincidence also validates our manual astrometry correction based on foreground galaxy (Appendix [5](#app:astrometry)). (cite: Fosbury_1999; Vernet_2001_thesis) proposed that a dust ring is present around the nucleus of Cygnus A. Given the spectral similarity of 4C+19.71 to Cygnus A (Fig. [3](#fig:spec_comp)), it is possible that we also detect a dust lane around the center of 4C+19.71. The line ratios shown in Fig. [4](#fig:q3dfit_line_ratio_map)bc are corrected for the dust attenuation based on this $E(B-V)$ map.

In Fig. [4](#fig:q3dfit_line_ratio_map)b and c, we show respectively the ratio maps of $\mathrm{[O i]/H\alpha}$ and $\mathrm{[S ii]/H\alpha}$ based on the integrated line fluxes of all components. The following line ratios are in logarithmic scale, unless otherwise specified. We group the spaxels in the FoV into five regions (white dashed lines in Fig. [4](#fig:q3dfit_line_ratio_map)bc), following the apparent geometry of the AGN ionization cone, with the nucleus added as an individual region. The southern part of the ISM is distinctive as having lower $\mathrm{[O i]/H\alpha}$ and $\mathrm{[S ii]/H\alpha}$ values. In the extended filamentary part of the nebula toward the north, there is a large scatter with the presence of both higher and lower $\mathrm{[O i]/H\alpha}$ and $\mathrm{[S ii]/H\alpha}$ values. In general, the east and west regions have higher $\mathrm{[O i]/H\alpha}$ and $\mathrm{[S ii]/H\alpha}$. To simplify, we combine the East and West regions and refer to it as EW.

We inspect our results in line ratio diagnostic diagrams and present in Fig. [5](#fig:q3dfit_line_ratio). In addition to $\mathrm{[O i]/H\alpha}$ (Fig. [5](#fig:q3dfit_line_ratio)b) and $\mathrm{[S ii]/H\alpha}$ (Fig. [5](#fig:q3dfit_line_ratio)c), we present the $\mathrm{[N ii]/H\alpha-[O iii]/H\beta}$ (Fig. [5](#fig:q3dfit_line_ratio)a) and $\mathrm{[O ii]/[O iii]-[O iii]/H\beta}$ diagnostics (Fig. [5](#fig:q3dfit_line_ratio)d). The east$+$west (EW) region (red diamonds) occupies different locations on the diagnostic diagrams than the other regions, with higher $\mathrm{[O i]/H\alpha}$, $\mathrm{[S ii]/H\alpha}$ and $\mathrm{[O ii]/[O iii]}$ values. The EW region is also distinctive with a lower $\mathrm{[O iii]/H\beta}$ compared to the other regions. Although the southern spaxels (blue hexagons) are clustered toward lower $\mathrm{[N ii]/H\alpha}$, $\mathrm{[O i]/H\alpha}$, $\mathrm{[S ii]/H\alpha}$ and $\mathrm{[O ii]/[O iii]}$ values, we find they fall in the line ratio space spanned by the northern regions (green squares) in all diagrams. Despite having a relatively large dispersion, the median line ratios of the northern region is consistent with the spaxels from the nucleus region (black triangles). We report the median line ratios of each region in Table [2](#tab:Line_diag_median).

We overlay the (cite: Groves_2004_model) dusty radiation-pressure dominated model grids on the diagnostic diagrams. We chose the $2Z_{\odot}$ models (black) as indicated by the $[N ii]/\mathrm{H\alpha}$ ratios (cite: Groves_2006; Nesvadba_2017b). The models are constructed with various combinations of the power-law index, $\alpha$, of the ionizing source (i.e., $F_{\nu}\propto\nu^{\alpha}$) and ionization parameter, $U=S_{\star}/(n_{\rm H}c)$, where $c$ is the speed of light, $n_{\rm H}$ is the hydrogen number density and $S_{\star}$ is the flux of ionizing photons entering the cloud. The goal is not to perform a quantitative comparison, but rather to test which parameter(s) could be responsible for the line ratio differences. Although other interpretations are possible, a higher $U$ parameter could explain the lower $[O i]/\mathrm{H\alpha}$ and a higher $\mathrm{[O iii]/H\beta}$ (cite: villar_martin1999). Our comparison indicates a scenario where the north, south and nucleus regions have higher $U$ parameters than the EW region. This is expected given that the jet axis is along the north-south direction which is also the direction of the AGN ionization cone (cite: Drouart_2012). Hence, the ionizing photons of the AGN can reach the ISM with less extinction along the North-South direction. In this configuration, the East and West regions are outside of the ionization cone where the photons will encounter more obstacles before ionizing the gas (cite: Fosbury_1999; vernet_2001). This indicates larger particle density $n_{\rm H}$ and less ionizing photon flux (smaller $S_{\star}$) in the EW which leads to lower observed $U$ parameters.

The south region has lower $\mathrm{[N ii]/H\alpha}$, $\mathrm{[O i]/H\alpha}$, $\mathrm{[S ii]/H\alpha}$ and $\mathrm{[O ii]/[O iii]}$. The $U$ parameter appears at similar levels in the south as in the nucleus. Comparing with the model grids, this could indicate that the ratio difference is due to lower $\alpha$ (steeper power-law ionizing spectrum). If this is the case, then there may be additional extinction between the ionizing photons and the southern clouds. The attenuation map (Fig. [4](#fig:q3dfit_line_ratio_map)a) indeed shows a higher value toward the south. If this is due to the geometry of the dust torus, it may be inconsistent with the indicated orientation from (cite: Nesvadba_2017b). We also overlay the similar radiation model with $0.5Z_{\odot}$ in cyan in Fig. [5](#fig:q3dfit_line_ratio)c and find that there is an alternative possibility that the southern region is more metal poor than the nuclear region. Additionally, the complex kinematics in the southern region (Fig. [1](#fig:IFU+spec) (c3)), suggesting a more complex scenario in the south (e.g., a late-stage merger, see Sect. [4.5](#subsec:southISM)). The detailed analysis of this southern region requires more lines which is beyond the scope of this paper (cite: Groves_2004_model; Holden_2023a).

To further test the ionization mechanisms, we also overlay the empirical classification from (cite: Kewley_2006) in Fig. [5](#fig:q3dfit_line_ratio)a, b and c. Although these are calibrated using low-$z$ data (cite: Kewley_2019), the results provide evidence of the AGN radiation dominating ionization of the ISM within $\lesssim30\,$kpc of the hidden quasar. Some spaxels in the north and east regions are located in the low ionization or H ii region. This suggests a different ionization mechanism or mix of different mechanisms at these spatial locations. Indeed, we find a part of them are roughly consistent with the “shock+precursor” models (cite: Allen_2008). The shock models can cover a large fraction of the parameter space of the line ratio diagnostics. The identification of shock ionization requires combination of flux ratios with kinematics, electron temperature and H$\alpha$ fluxes (cite: Alatalo_2016; Baron_2017; Alarie_2019). Our discussion is not meant to be decisive but to be inclusive with the possibility of shock. We choose the models with pre-shock number density, $n=100\,\mathrm{cm^{-3}}$ (cite: DeBreuck_2000). For the shock velocities, we use higher values ($v_{\rm shock}\geq200\,\mathrm{km\,s^{-1}}$) following (cite: DeBreuck_2000) studying the emission lines of HzRGs. We note that shock+precursor model with pre-shock density $n=1000\,\mathrm{cm^{-3}}$ are also physical for AGN (cite: Liu_weizhe_2020) which occupies a subset of the line ratio space spanned by $n=100\,\mathrm{cm^{-3}}$ model using the same set of $v_{\rm shock}$ and magnetic parameters. The driver of the shock is unclear. The EW region is roughly in the direction perpendicular to the ionization cone (jet axis) which suggests a less collimated shock driver or the ionization cone is not perpendicular to the dusty obscuring disk (cite: Dugan_2017; Tanner_2022; Vayner_2023Q3D). As for the more extended parts ($\gtrsim10\,$kpc) in the North, the passage of the powerful radio jet could also have left remaining shock effects.

Our results show that the inner part of the ionized ISM in the $z\sim3.5$ radio-loud AGN is dominated by photons from the hidden AGN with potential evidence for shock ionization. Its structure agrees with the classical ionization cone. Although the analysis is based on knowledge gained at low-$z$ and there are more unsolved complexities, *JWST* will be the key to address this (cite: Nakajima_2022; Sanders_2023).

|                           | Nuc.  |   N   |   S   |  EW   |
|:--------------------------|:-----:|:-----:|:-----:|:-----:|
| $\mathrm{[O iii]/H\beta}$ | 1.00  | 0.92  | 0.88  | 0.72  |
| $\mathrm{[N ii]/H\alpha}$ | -0.24 | -0.23 | -0.47 | -0.27 |
| $\mathrm{[O i]/H\alpha}$  | -0.65 | -0.68 | -1.00 | -0.58 |
| $\mathrm{[S ii]/H\alpha}$ | -0.45 | -0.54 | -0.63 | -0.38 |
| $\mathrm{[O ii]/[O iii]}$ | -0.44 | -0.40 | -0.65 | -0.31 |

: Median line ratio values for different regions in Fig. [5](#fig:q3dfit_line_ratio).

## Inefficient quasar-driven outflow at nucleus

Our NIRSpec IFU observations enable studying outflows on scales $\lesssim20\,$kpc. VLT/SINFONI observations captured more extended outflowing gas (cite: Collet_2016; Nesvadba_2017b; Nesvadba_2017a).

In Sect. [3.1](#subsec:O3morphology), we show that the “high-velocity" clouds are only detected within the $\sim5\,$kpc from the AGN and their morphology is aligned with the jet axis (Fig. [1](#fig:IFU+spec)). This is inconsistent with the results from observations of quasars at Cosmic Noon where fast ($|\Delta v|\sim500\,\mathrm{km\,s^{-1}}$) outflows are seen at $\gtrsim10\,$kpc and are less directionally confined (cite: Vayner_2023Q3D_2). However, (cite: Cresci_2023; Veilleux_2023) also showed one contradicting case. Hence, this discussion is yet settled and required more observations. Through our discussions in Sect. [4.1](#subsec:low_z_comp) and [4.2](#subsec:linera_diag), these may be the outflows inside the ionization cone. The double-sided radio lobes have a projected extent of $\sim60\,$kpc, which is beyond the *JWST* FoV. Hence, this potential outflow maybe radiatively-driven.

The systematic per-spaxel kinematic study is beyond the scope of this work. Additionally, as shown in Sect. [4.2](#subsec:linera_diag) (also in Sect. [4.5](#subsec:southISM)), there may be more complex scenarios happening in the southern cone. Hence, we use the results from the integrated 1D spectrum (Fig. [1](#fig:IFU+spec)d and [2](#fig:spec_full) and Table [1](#tab:1Demission_kine) and [4](#tab:emissionline)) at the nucleus region as a proxy to estimate the kinetic energy of the potential outflow near the AGN. For this calculation, we focus on the red and blue components (Table [1](#tab:1Demission_kine) and [4](#tab:emissionline)) and assume them to be the redshifted and blueshifted outflow clouds seen on the back and front side of the northern part of the ionization cone, respectively. Then, we assume their relatively velocity shifts with respect to the central component (Appendix [8](#app:sys_z)) as their outflow velocities ($\Delta v_{\rm red}=334\,\mathrm{km\,s^{-1}}$ and $\Delta v_{\rm blue}=-386\,\mathrm{km\,s^{-1}}$). We follow (cite: Vayner_2023Q3D_2) and use the following equation to calculate the ionized outflow gas mass (cite: Osterbrock_2006): $$\begin{equation}
\label{eq:m_ion}
    M_{\text {ion}}=1.4\left(\frac{m_p L_{\rm H \alpha}}{j_{H_\alpha} n_e}\right),
\end{equation}$$ where $L_{\rm H\alpha}$ and $n_{e}$ are the H$\alpha$ luminosity and electron density, respectively. We assume an electron temperature $T_{e}\simeq15\,000\,$K (cite: Nesvadba_2017b; Vayner_2023Q3D_2). We use the fiducial value $n_{e}=500\,\mathrm{cm^{-3}}$ from (cite: Nesvadba_2017b). Given that the emissivity, $j_{H_\alpha}$, is not sensitive to $n_{e}$, we use the value of $2\times 10^{-25} \mathrm{erg\, cm^3\,s^{-1}}$ for $T_{e}\simeq15\,000\,$K (cite: Vayner_2023Q3D_2). Based on equation [\[eq:m_ion\]](#eq:m_ion), we find $M_{\rm ion} = 10^5$ and $10^6$ M$_\odot$  for the red and blue components, respectively.

We then estimate the outflow rate using the following equation (cite: Vayner_2023Q3D_2): $$\begin{equation}
    \dot{M}_{\rm ion}=\frac{M_{\rm ion} v_{\rm ion}}{\Delta R}.
\end{equation}$$ For the distance $\Delta R$, we use half of the physical size of the extraction aperture, $0.7\,$kpc. For the velocity, we use the $v_{\rm ion} = |\Delta v|+\sigma_{v}$ (cite: Rupke_2013; Vayner_2023Q3D_2). We report the summation of the red and blue components as the estimated total outflow rate. This gives a total $\dot{M}_{\rm ion}$ of $2\,\mathrm{M_{\odot}\,yr^{-1}}$. The outflow momentum flux $\dot{P}_{\rm ion}$ and outflow kinetic luminosity $L_{\rm ion}^{\text{kinetic}}$ are calculated from $$\begin{equation}
    \dot{P}_{\rm ion}^{\text {outflow }}=\dot{M}_{\rm ion}\times v_{\rm ion}
\end{equation}$$ $$\begin{equation}
L_{\rm ion}^{\text{kinetic}}=\frac{1}{2} \dot{M}_{\rm ion}\times v_{\rm ion}^2.
\end{equation}$$ We calculate values for $\dot{P}_{\rm ion}^{\text {outflow }}$ and $L_{\rm ion}^{\text{kinetic}}$ of $1.5\times10^{34}\,\mathrm{dyne}$ and $8.0\times10^{41}\,\mathrm{erg\,s^{-1}}$, respectively. These are much smaller ($\sim2\,$dex) than the values derived on larger scales by SINFONI (cite: Nesvadba_2017a; Nesvadba_2017b). If we use the infrared AGN luminosity, $L_{\rm AGN}^{\rm IR}=10^{10.91}\,L_{\odot}$, and assume a conversion factor, $\kappa_{\rm AGN}^{\rm bol}=6$, the bolometric luminosity of 4C+19.71 is estimated to be $L_{\rm bol}\sim2.5\times10^{47}\,\mathrm{erg\,s^{-1}}$ (cite: Drouart_2014; Falkendal_2019). Then the coupling efficiency of this potential radiatively-driven outflow, $L_{\rm ion}^{\text{kinetic}}/L_{\rm bol}$, is $\sim 10^{-5}$. Using NIRSpec IFU, (cite: Perna_2023) and (cite: Vayner_2023Q3D_2) reported higher coupling efficiency for $z\sim3$ quasars ($0.02$ and $10^{-3}$, respectively). (cite: Veilleux_2023) found a relatively low coupling efficiency using the same instrument, $1.8\times10^{-4}$, for a $z\sim1.6$ type-1 quasar which is still 1 dex higher than 4C+19.71. (cite: Harrison_2018) summarised the coupling efficiency for a large number of AGN (e.g., their Fig. 2). Compared to their statistics, the value from this work is located at the lower end. Our estimation based on the *JWST* observation is a $\sim2$ to $3\,$dex lower than the coupling efficiency of the jet kinetic energy probed on larger scales for a sample of $\sim50$ HzRGs (cite: Nesvadba_2008; Nesvadba_2007a; Nesvadba_2017a; Nesvadba_2017b).

Our NIRSpec IFU data is only sensitive to the central clumps, $\lesssim20\,$kpc, but not to extended diffuse emission. If we assume there are fast outflows ($\sim500\,\mathrm{km\,s^{-1}}$) and use the distance from the centre quasar to the edge of our FoV ($\sim20\,$kpc), the crossing time of this outflow would be $\sim40\,$Myr. This is shorter than the jet age, $\sim60\,$Myr, of 4C+19.71 (cite: Nesvadba_2017b). Hence, it is plausible that we do not capture the fast and (presumably) energetic outflowing gas on large scales (e.g., size of the radio lobes). Nevertheless, if the radiative coupling efficiency is $10^{-5}$ at the nucleus where the radiation is the strongest, it will be less efficient farther outside. Simulations (cite: Costa_2018a) find that the efficiency for the radiation-driven outflows can be $\sim0.1\%$ in luminous quasars ($L_{\rm bol}\gtrsim10^{47}\,\mathrm{erg\,s^{-1}}$) within galactic scales ($\lesssim10\,$kpc). The efficiency drops after $\sim10\,$Myr which may resemble the case of our observation. Though the ISM and CGM gas of 4C+19.71 seem more quiescent than in other HzRGs (cite: Nesvadba_2017b; wang2023), a gas kinetic energy luminosity of $10^{45}\,\mathrm{erg\,s^{-1}}$ was found for this source by including the ISM at the jet lobes. Comparing to the results from (cite: Nesvadba_2017a; Nesvadba_2017b), we conclude that, at least for this HzRG, the mechanical feedback from the radio jet takes the leading role for driving the outflow, and it is happening in the radio lobes beyond the galactic scale (e.g., $\sim$30 kpc from the AGN).

One of the main uncertainties is the estimation of $M_{\text {ion}}$, which is inversely proportional to $n_{e}$. We find that $M_{\text {ion}}$ (and thus $L_{\rm ion}^{\rm kinetic}$) could be $\sim2\,$dex lower if we use the $n_{e}$ estimated based on our observation (Appendix [7](#app:linelist)). Therefore, the radiative coupling could be even more inefficient. Another uncertainty is the outflow speed. We take the unknown orientation of the ionization cone into account by using $v_{\rm ion} = |\Delta v|+\sigma_{v}$. Even if the estimated speed is one of the three components in 3D space (i.e., the intrinsic $v_{\rm ion}$ is higher by another factor of three), the radiative coupling efficiency will increase by a factor of nine, $\sim10^{-4}$, which is still $\sim1\,$dex lower than the kinetic efficiency from (cite: Nesvadba_2017b).

## AGN illuminates the filamentary ISM after jet passage

In Sect. [3.1](#subsec:O3morphology), we found that ionized ISM emission with $\lesssim30\,$kpc of the AGN is dominated by gas close to the systemic redshift (Fig. [1](#fig:IFU+spec)c). Due to the limitation of the FoV, we only captured the northern extended region. In general, the gas morphology is elongated along the north-south direction, aligned with the jet axis. When we focus on the smaller scale structures ($\sim 5$ kpc), these gaseous clouds are filamentary and patchy and do not follow the collimated jet but have larger angle separations ($\sim 30\deg$). As discussed in Sect. [4.2](#subsec:linera_diag), we are observing the ionization cone-like structures along the jet. This provides enough ionizing photons to illuminate the extended gaseous nebula beyond the galactic scale. The fact that we do not observe the extended ISM in directions outside of the ionization cone, for example in the west where we have the spatial coverage (Fig. [1](#fig:IFU+spec)), may be due to the shortage of ionizing photons. Hence, it may be that the patchy filaments in the North are the “intrinsic” structures, which are not seen in other directions as they are not emitting or simply outside the NIRSpec FoV.

The HzRGs we observed may have entered their flux-limited parent radio surveys because their radio lobes are brightened when they encounter a higher density environment which provides a larger “working surface” for the jet (cite: Eales_1992; wang2023). Combining the discussion in Sect. [4.3](#subsec:ouflow) and (cite: Nesvadba_2017b), the situation of 4C+19.71 may be that the jet was launched $\sim60\,$Myr ago, and in its younger years could have pushed some gas outside of the host galaxy. Once the radio lobes have escaped the host galaxy, the radio jet is very collimated and is no longer interacting with the ISM; the observed systemic gas in Fig. [1](#fig:IFU+spec) is thus no longer kinematically affected by the radio jets, but the gas is still photo-ionized by the AGN photons within the ionization cone along the jet axis.

(cite: Fu_2009) found similar quiescent nebulae whose morphology do not fully agree with their radio maps in low-$z$ quasars on comparable physical scales. They proposed that the expanding bubbles following the jet disturb the ISM. 4C+19.71 has one of the most powerful radio jets, $P_{\rm jet}\sim10^{47}\,\mathrm{erg\,s^{-1}}$ (cite: Nesvadba_2017b; Cavagnolo_2010). The situation may be different than the low-$z$ low radio power quasars. Nevertheless, we find evidence of shock ionization on the extended northern nebula of which the jet could be the driver (Sect. [4.2](#subsec:linera_diag)). Further analysis (e.g., $T_{e}$ mapping) will be helpful to determine the mechanisms.

## Complex southern ISM

In Sect. [4.3](#subsec:ouflow), our discussion of the outflow is based on the northern region near the quasar as the nature of the southern “high-velocity" region is more complicated. In Fig. [1](#fig:IFU+spec)(c2), we clearly find that there are three velocity components with the “high-velocity" ones (blue and red) dominating the flux. The morphology of the blue and red parts are not spatially overlapping (Fig. [1](#fig:IFU+spec)a, (b1) and (b3)). Such kinematics resemble that of a rotating disk. If we simply take the velocity shifts of the blue and red components from the one spaxel spectrum (Fig. [1](#fig:IFU+spec)(c2)), $\Delta v_{\rm blue}=-585\,\mathrm{km\,s^{-1}}$ and $\Delta v_{\rm red}=535\,\mathrm{km\,s^{-1}}$. This is very high for a rotating disk; using the half size of $\sim4\,$kpc, this would imply a dynamical mass of $\sim2\times 10^{11}\,\mathrm{M_{\odot}}$. We do not detect any continuum emitting source at this position, though we note that the partially overlapping foreground G2 may obscure some of the emission (Fig. [1](#fig:IFU+spec)a). Extracting from a $r=0.1\ensuremath{''}$ aperture, the observed flux density upper limit is $\sim10^{-20}\,\mathrm{erg\,s^{-1}\,cm^{-2}\,\mathring{A}^{-1}}$ at $2.5\,\mu$m (i.e., rest frame $V$ band). This then gives an upper limit to the absolute $V$ band magnitude of $\sim -17$ which could be a galaxy with $M_{\star}\sim 10^{8}$ to $10^{9}\,\mathrm{M_{\odot}}$ (cite: Weaver_2022). This corresponds to a $M_{\star}/M_{\rm dyn.}\sim10^{-3}$ which is very small for a galaxy at $z\sim3.5$. The southern region shows lower $\mathrm{[O i]/H\alpha}$ and $\mathrm{[S ii]/H\alpha}$ than the rest of the nebula. It also has the potential to have sub-solar metallicity (Sect. [4.2](#subsec:linera_diag)). Though our estimates have large uncertainties, we cannot exclude the possibility of it being a late stage merger. A more detailed kinematic study is required to unveil the nature of this region with complex kinematics.

## Summary and future

In this work, we present the first NIRSpec IFU view of the ionized ISM in the vicinity of the $z\simeq3.59$ radio-loud AGN 4C+19.71. With unprecedented resolution and sensitivity, we study the gas morphology, ionization states and preliminary kinematics within $10\,$kpc of the AGN. This makes it possible to study the role of the jet and radiative feedback near Cosmic Noon and to compare to low-$z$ AGN and theoretical models. We find that the radiation from the hidden quasar dominates the ionization of the ISM of 4C+19.71 which resembles the scenario of other powerful quasars at Cosmic Noon. The radiatively-driven outflow is only found within $5\,$kpc of the AGN and is inefficiently ($\sim 10^{-5}$) coupled to the central $L_{\rm bol}\sim10^{47}\,\mathrm{erg\,s^{-1}}$ quasar even at the nucleus. Combining with ground-based studies, we conclude that the jet kinetic energy takes a leading role in the feedback of this HzRG at $z\sim3.5$. Line ratio diagnostics infer the existence of a ionization cone along the jet axis. The AGN ionizing photons illuminate the filamentary extended ISM along the cone. The observed morphology may be the “intrinsic” shape of the dense gas around this relatively massive galaxy. These conclusions are based on the first source from our sample. The picture of the feedback from the most powerful radio sources will be clearer with our full sample which will allow kinematics studies of the ionized ISM of radio-loud AGN with very different jet morphologies.

# Acknowledgements

This work uses the NASA’s Astrophysics Data System and a number of open source software other than the aforementioned ones such as Jupyter notebook (cite: kluyver2016jupyter); `matplotlib` (cite: Hunter_2007); `SciPy` (cite: virtanen2020scipy); `NumPy` (cite: harris2020numpy); `Astropy` (cite: Astropy_2018); `LMFIT` (cite: newville2016).

We thank Daizhong Liu and Markus Hundertmark for the useful discussion of the WCS alignment. This work is based in part on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program JWST-GO-01970. Support for program JWST-GO-01970 was provided by NASA through a grant from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127. NLZ and AV are supported in part by NASA through STScI grants JWST-ERS-01335 and JWST-GO-01970. The work of DS was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00576.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

99 natexlab

(ref: Alarie_2019) Alarie, A. & Morisset, C. 2019, , 55, 377

(ref: Alatalo_2016) Alatalo, K., Cales, S. L., Rich, J. A., et al. 2016, ApJS, 224, 38

(ref: Allen_2008) Allen, M. G., Groves, B. A., Dopita, M. A., Sutherland, R. S., & Kewley, L. J. 2008, ApJS, 178, 20

(ref: Armus_1998) Armus, L., Soifer, B. T., Murphy, T. W., J., et al. 1998, ApJ, 495, 276

(ref: Astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: BPT_1981) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5

(ref: Baron_2017) Baron, D., Netzer, H., Poznanski, D., Prochaska, J. X., & Förster Schreiber, N. M. 2017, MNRAS, 470, 1687

(ref: Begelman_1989) Begelman, M. C. & Cioffi, D. F. 1989, ApJL, 345, L21

(ref: Boeker_2022) Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82

(ref: Calzetti_2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Carilli_1996) Carilli, C. L. & Barthel, P. D. 1996, A&ARv, 7, 1

(ref: Carilli_1997) Carilli, C. L., Röttgering, H. J. A., van Ojik, R., Miley, G. K., & van Breugel, W. J. M. 1997, ApJS, 109, 1

(ref: Cavagnolo_2010) Cavagnolo, K. W., McNamara, B. R., Nulsen, P. E. J., et al. 2010, ApJ, 720, 1066

(ref: Collet_2016) Collet, C., Nesvadba, N. P. H., De Breuck, C., et al. 2016, A&A, 586, A152

(ref: Costa_2018a) Costa, T., Rosdahl, J., Sijacki, D., & Haehnelt, M. G. 2018, MNRAS, 479, 2079

(ref: Cresci_2023) Cresci, G., Tozzi, G., Perna, M., et al. 2023, A&A, 672, A128

(ref: DeBreuck_2000) De Breuck, C., Röttgering, H., Miley, G., van Breugel, W., & Best, P. 2000, A&A, 362, 519

(ref: DeBreuck_2010) De Breuck, C., Seymour, N., Stern, D., et al. 2010, ApJ, 725, 36

(ref: Drouart_2012) Drouart, G., De Breuck, C., Vernet, J., et al. 2012, A&A, 548, A45

(ref: Drouart_2014) Drouart, G., De Breuck, C., Vernet, J., et al. 2014, A&A, 566, A53

(ref: Dugan_2017) Dugan, Z., Gaibler, V., & Silk, J. 2017, ApJ, 844, 37

(ref: Eales_1992) Eales, S. A. 1992, ApJ, 397, 49

(ref: Fabian_2012) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: Falkendal_2019) Falkendal, T., De Breuck, C., Lehnert, M. D., et al. 2019, A&A, 621, A27

(ref: Falkendal_2021) Falkendal, T., Lehnert, M. D., Vernet, J., De Breuck, C., & Wang, W. 2021, A&A, 645, A120

(ref: Fanaroff_1974) Fanaroff, B. L. & Riley, J. M. 1974, MNRAS, 167, 31P

(ref: Fosbury_1999) Fosbury, R. A. E., Vernet, J., Villar-Martı́n, M., et al. 1999, in The Most Distant Radio Galaxies, ed. H. J. A. Röttgering, P. N. Best, & M. D. Lehnert, 311

(ref: Fu_2009) Fu, H. & Stockton, A. 2009, ApJ, 690, 953

(ref: gaiaDR3_2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Groves_2004_model) Groves, B. A., Dopita, M. A., & Sutherland, R. S. 2004a, ApJS, 153, 9

(ref: Groves_2004) Groves, B. A., Dopita, M. A., & Sutherland, R. S. 2004b, ApJS, 153, 75

(ref: Groves_2006) Groves, B. A., Heckman, T. M., & Kauffmann, G. 2006, MNRAS, 371, 1559

(ref: harris2020numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Harrison_2017) Harrison, C. M. 2017, Nature Astronomy, 1, 0165

(ref: Harrison_2014) Harrison, C. M., Alexander, D. M., Mullaney, J. R., & Swinbank, A. M. 2014, MNRAS, 441, 3306

(ref: Harrison_2018) Harrison, C. M., Costa, T., Tadhunter, C. N., et al. 2018, Nature Astronomy, 2, 198

(ref: Heckman_2014) Heckman, T. M. & Best, P. N. 2014, ARA&A, 52, 589

(ref: Herrera-Camus_2021) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31

(ref: Holden_2023a) Holden, L. R., Tadhunter, C. N., Morganti, R., & Oosterloo, T. 2023, MNRAS, 520, 1848

(ref: Hunter_2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: Husemann_2013b) Husemann, B., Wisotzki, L., Sánchez, S. F., & Jahnke, K. 2013, A&A, 549, A43

(ref: Jakobsen_2022) Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80

(ref: Kauffmann_2003) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055

(ref: Kewley_2001) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J. 2001, ApJ, 556, 121

(ref: Kewley_2006) Kewley, L. J., Groves, B., Kauffmann, G., & Heckman, T. 2006, MNRAS, 372, 961

(ref: Kewley_2013) Kewley, L. J., Maier, C., Yabe, K., et al. 2013, ApJL, 774, L10

(ref: Kewley_2019) Kewley, L. J., Nicholls, D. C., & Sutherland, R. S. 2019, ARA&A, 57, 511

(ref: kluyver2016jupyter) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in Positioning and Power in Academic Publishing: Players, Agents and Agendas, ed. F. Loizides & B. Schmidt, IOS Press, 87 – 90

(ref: kolwa2023) Kolwa, S., De Breuck, C., Vernet, J., et al. 2023, MNRAS, 525, 5831

(ref: Kondapally_2023) Kondapally, R., Best, P. N., Raouf, M., et al. 2023, arXiv e-prints, arXiv:2306.11795

(ref: Liu_weizhe_2020) Liu, W., Veilleux, S., Canalizo, G., et al. 2020, ApJ, 905, 166

(ref: MandD_2014) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Maxfield_2002) Maxfield, L., Spinrad, H., Stern, D., Dey, A., & Dickinson, M. 2002, AJ, 123, 2321

(ref: Miley_2008) Miley, G. & De Breuck, C. 2008, A&ARv, 15, 67

(ref: Mukherjee_2016) Mukherjee, D., Bicknell, G. V., Sutherland, R., & Wagner, A. 2016, MNRAS, 461, 967

(ref: Mukherjee_2021) Mukherjee, D., Bicknell, G. V., & Wagner, A. Y. 2021, Astronomische Nachrichten, 342, 1140

(ref: Mukherjee_2018) Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018, MNRAS, 479, 5544

(ref: Mullaney_2013) Mullaney, J. R., Alexander, D. M., Fine, S., et al. 2013, MNRAS, 433, 622

(ref: Nakajima_2022) Nakajima, K. & Maiolino, R. 2022, MNRAS, 513, 5134

(ref: Nesvadba_2017b) Nesvadba, N. P. H., De Breuck, C., Lehnert, M. D., Best, P. N., & Collet, C. 2017a, A&A, 599, A123

(ref: Nesvadba_2017a) Nesvadba, N. P. H., Drouart, G., De Breuck, C., et al. 2017b, A&A, 600, A121

(ref: Nesvadba_2007a) Nesvadba, N. P. H., Lehnert, M. D., De Breuck, C., Gilbert, A., & van Breugel, W. 2007, A&A, 475, 145

(ref: Nesvadba_2008) Nesvadba, N. P. H., Lehnert, M. D., De Breuck, C., Gilbert, A. M., & van Breugel, W. 2008, A&A, 491, 407

(ref: Nesvadba_2006a) Nesvadba, N. P. H., Lehnert, M. D., Eisenhauer, F., et al. 2006, ApJ, 650, 693

(ref: newville2016) Newville, M., Stensitzki, T., Allen, D. B., et al. 2016, Lmfit: Non-Linear Least-Square Minimization and Curve-Fitting for Python

(ref: Ogle_1997) Ogle, P. M., Cohen, M. H., Miller, J. S., et al. 1997, ApJL, 482, L37

(ref: Osterbrock_2006) Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei

(ref: Pentericci_1999) Pentericci, L., Röttgering, H. J. A., Miley, G. K., et al. 1999, A&A, 341, 329

(ref: Perna_2023) Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89

(ref: Rupke_2023q3dfit) Rupke, D., Wylezalek, D., Zakamska, N., et al. 2023, q3dfit: PSF decomposition and spectral analysis for JWST-IFU spectroscopy, Astrophysics Source Code Library, record ascl:2310.004

(ref: Rupke_2014) Rupke, D. S. N. 2014, IFSFIT: Spectral Fitting for Integral Field Spectrographs

(ref: Rupke_2021) Rupke, D. S. N., Schweitzer, M., Viola, V., et al. 2021, QUESTFIT: Fitter for mid-infrared galaxy spectra

(ref: Rupke_2013) Rupke, D. S. N. & Veilleux, S. 2013, ApJL, 775, L15

(ref: Sanders_2016) Sanders, R. L., Shapley, A. E., Kriek, M., et al. 2016, ApJ, 816, 23

(ref: Sanders_2023) Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy, N. A., & Brammer, G. B. 2023, arXiv e-prints, arXiv:2303.08149

(ref: Seymour_2007) Seymour, N., Stern, D., De Breuck, C., et al. 2007, ApJS, 171, 353

(ref: Smail_2012) Smail, I., Blundell, K. M., Lehmer, B. D., & Alexander, D. M. 2012, ApJ, 760, 132

(ref: Tadhunter_2007) Tadhunter, C., Dicken, D., Holt, J., et al. 2007, ApJL, 661, L13

(ref: Tadhunter_2003) Tadhunter, C., Marconi, A., Axon, D., et al. 2003, MNRAS, 342, 861

(ref: Tadhunter_2001) Tadhunter, C., Wills, K., Morganti, R., Oosterloo, T., & Dickson, R. 2001, MNRAS, 327, 227

(ref: Tanner_2022) Tanner, R. & Weaver, K. A. 2022, AJ, 163, 134

(ref: vanBemmel_2003) van Bemmel, I. M., Vernet, J., Fosbury, R. A. E., & Lamers, H. J. G. L. M. 2003, MNRAS, 345, L13

(ref: vanOjik_1996) van Ojik, R., Roettgering, H. J. A., Carilli, C. L., et al. 1996, A&A, 313, 25

(ref: Vayner_2023Q3D) Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2023a, ApJ, 955, 92

(ref: Vayner_2023Q3D_2) Vayner, A., Zakamska, N. L., Ishikawa, Y., et al. 2023b, arXiv e-prints, arXiv:2307.13751

(ref: Veilleux_2023) Veilleux, S., Liu, W., Vayner, A., et al. 2023, ApJ, 953, 56

(ref: Veilleux_1987) Veilleux, S. & Osterbrock, D. E. 1987, ApJS, 63, 295

(ref: Vernet_2001_thesis) Vernet, J. 2001, PhD thesis, Universite de Paris Diderot (Paris VII), France

(ref: vernet_2001) Vernet, J., Fosbury, R. A. E., Villar-Martı́n, M., et al. 2001, A&A, 366, 7

(ref: villar_martin1999) Villar-Martı́n, M., Tadhunter, C., Morganti, R., Axon, D., & Koekemoer, A. 1999, MNRAS, 307, 24

(ref: virtanen2020scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: wang2023) Wang, W., Wylezalek, D., Vernet, J., et al. 2023, arXiv e-prints, arXiv:2309.15144

(ref: Weaver_2022) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, ApJS, 258, 11

(ref: Whitmore_2016) Whitmore, B. C., Allam, S. S., Budavári, T., et al. 2016, AJ, 151, 134

(ref: Wylezalek_2017) Wylezalek, D., Schnorr Müller, A., Zakamska, N. L., et al. 2017, MNRAS, 467, 2612

(ref: Wylezalek_2022q3d) Wylezalek, D., Vayner, A., Rupke, D. S. N., et al. 2022, ApJL, 940, L7

(ref: Wylezalek_2016b) Wylezalek, D., Zakamska, N. L., Liu, G., & Obied, G. 2016, MNRAS, 457, 745

(ref: Zakamska_2016b) Zakamska, N. L., Hamann, F., Pâris, I., et al. 2016, MNRAS, 459, 3144

(ref: Zakamska_2003) Zakamska, N. L., Strauss, M. A., Krolik, J. H., et al. 2003, AJ, 126, 2125

# Astrometric correction

![](Figures/WCS_correction.png)

The *JWST* Fine Guidance Sensor (FGS) is responsible for guiding the pointing, and there is no known issue in the guiding process. However, there is a known systematic WCS offset of the NIRSpec IFU[^4]. This is due to poorly registered IFU detector coordinates on the *JWST* focal panel with respect to the reference V2 and V3 axes. This corresponds to 0.173 $''$ and 0.178 $''$ in the V2 and V3 direction[^5], respectively (Help Desk, private communication through). This offset projection to sky (RA, Dec) coordinates could then be calculated using `pysiaf` by assuming the targeted RA and Dec of the IFU pointing is correct. The projection matrix for converting V2, V3 coordinates to the sky plane can be set by `pysiaf.utils.rotations.attitude_matrix` using the old (V2, V3) reference coordinates, target RA and Dec, and angle between the north and V3. This angle is measured from north to east with a value of $83.0652845\deg$ for our observation. It is calculated using the angle between the IFU with respect to the North (from the header) and the fixed angle between the IFU and V3. There is an additional $\sim3\ensuremath{''}$ systematic rotational angle error between the IFU plane and V3 axis. Since this will only result in a secondary ($\sim0.007\ensuremath{''}$) offset, we neglect it here. The final systemic offsets of the pointing, from updated position to the original position, are $\Delta$RA$=0.21\ensuremath{''}$ and $\Delta$Dec$=-0.15\ensuremath{''}$. We refer to this correction as “Correction1". This error has been reported as partially corrected using the up-to-date context file. We test the new pipeline assigned WCS using jwst_1093.pmap and find it matches closely with our “Correction1". We report an offset of $|\Delta$RA$|=0.09\ensuremath{''}$ and $|\Delta$Dec$|=0.07\ensuremath{''}$ using the fitted 2D Gaussian centroids of G1 at $\sim2.7\rm \mu m$. Hence, we consider this systematic WCS error has been fixed. However, other source of uncertainty is still presented and still required manual alignment.

In addition, there is a further offset due to the zero-point shift of the NIRSpec detector and the FGS which adds another term to the aforementioned values in the V2V3 plane. The shifts are -0.016$''$ and 0.111$''$ in V2 and V3 coordinates, respectively (Help Desk, private communication). However, a caution is noted that the direction of this shift is not well-understood. We assumed this direction and followed the aforementioned procedure using `pysiaf`. This resulted in the $\Delta$RA$=0.09\ensuremath{''}$ and $\Delta$Dec$=-0.14\ensuremath{''}$. We refer to this correction as “Correction2$++$". Since the direction is uncertain, we produced further corrections “Correction2$+-$", “Correction2$-+$" and “Correction2$--$". The “$+$" and “$-$" signs indicate which direction we adopted for the offset with respect to the original direction suggested by, the Help Desk.

For the manual correction of the astrometry, we matched G1 positions (Section [3](#sec:results)) measured from the $\sim 2.7\rm \mu m$ continuum image collapsed from our NIRSpec IFU cube and the *HST*/WFPC2 (cite: Whitmore_2016) image. This was done by matching the centroids of the fitted 2D Gaussian profile. We caution that although we updated the astrometry of the *HST* image using *Gaia* DR3 (cite: gaiaDR3_2023), the uncertainty of the WCS position is $\sim0.06\ensuremath{''}$. This is estimated based on the standard deviation of the offsets of the cross matched *Gaia* targets in the *HST* FoV. This uncertainty ($\sim1.2\ensuremath{''}$ given the unknown direction) is marked by the size of the plus marker in Fig. [1](#fig:IFU+spec)d. We further note that the *HST* image was observed in 1997. The proper monition of the stars were taken into account during the correction by adopting the reported epoch$=$J2000 coordinates in the *Gaia* DR3 catalog. Another source of uncertainty could be the intrinsic continuum emission offset from different bands. The *HST*/WFPC2 image was taken with the F702W filter, which corresponds to $2520\,\mathrm{\AA}$ in the rest frame of G1. The NIRSpec IFU data covers $\sim 0.57-1.15\mathrm{\mu m}$ for G1. We examined the continuum centroid offset of G1 by extracting narrow-band images at the blue and red ends of the data cube. A $\sim0.09\ensuremath{''}$ shift is seen.

We present the offsets of these corrections with respect to the manual shift (aligned with *HST*) used in the analysis in Table [3](#tab:WCS_offset). Fig. [6](#fig:wcs_corr) presents the visual inspection of the WCS correction by comparing the results from different methods. We mark the *HST* positions of the three continuum emission objects with green circles. The radius of each circle is $0.12\ensuremath{''}$ which can be used as the spatial uncertainty of the *HST* object. We see that Correction2$+-$ and Correction2$-+$ have $\sim0.1\ensuremath{''}$ offsets from the manual shift (or *HST* WCS). Given that there is a $\sim0.1\ensuremath{''}$ uncertainty in the *HST*-NIRSpec alignment, we decide that the IFU WCS offset can be solved by correcting the systematic error. Since the direction of the error is not well-understood, we use the manual match in this paper.

| Method          | $\Delta \alpha_{\rm manual}$ | $\Delta \delta_{\rm manual}$ |
|:----------------|:----------------------------:|:----------------------------:|
| Correction1     |    0.22$\ensuremath{''}$     |    -0.06$\ensuremath{''}$    |
| Correction2$++$ |    -0.34$\ensuremath{''}$    |    0.07$\ensuremath{''}$     |
| Correction2$+-$ |    -0.10$\ensuremath{''}$    |    0.09$\ensuremath{''}$     |
| Correction2$-+$ |    -0.10$\ensuremath{''}$    |    0.06$\ensuremath{''}$     |
| Correction2$--$ |    -0.34$\ensuremath{''}$    |    0.07$\ensuremath{''}$     |

: Offset between different astrometry and manual shift.

# Foreground galaxies

We reported in Sect. [3](#sec:results) that two foreground galaxies have been identified with continuum and emission lines: G1 to the west of the radio galaxy and G2 to the east. There we present the spectra of G1 and G2. Their positions are marked with blue dots in Fig.[1](#fig:IFU+spec) which are the centers of their extraction apertures. For both galaxies, we used square apertures with the size of $0.25\ensuremath{''}\times0.25\ensuremath{''}$ ($\sim5\times5$ pix$^{2}$) and summed each spectrum from the spaxels inside the aperture. For partially covered spaxels, we multiply the area by the fractional overlap with the extraction aperture. The aperture for G1 was centered at its continuum peak position. As for G2 which is only partially captured in our FoV, we placed the aperture to be as close as possible to its continuum emission peak while minimising the impact from the detector edge. In Fig. [7](#fig:spec_G1) and [8](#fig:spec_G2), we show the spectra extracted for G1 and G2, respectively. The redshifts of G1 and G2 are determined based on their H$\alpha$ lines and have values of $z_{\rm G1} \simeq 1.786$ and $z_{\rm G2} \simeq 1.643$. For each foreground galaxy, at least two more emission lines are identified based on their redshifts. We use thick black vertical lines to mark the spatially and spectrally detected emission lines. The expected positions of emission lines near H$\alpha$ based on the derived redshift of the targets are marked in grey lines if not clearly detected. We note that the \[S ii\]$6716,6731$ doublet of G2 overlaps with the \[Ne iii\]3869 line of 4C+19.71 in wavelength (orange line in top panel of Fig. [8](#fig:spec_G2)). The spatial check confirms that there are distinct emission peaks separated by $\sim0.4\ensuremath{''}$.

![](Figures/Spectra_G1.png)

![](Figures/Spectra_G2.png)

# Emission line list

+:----------------------------------+:----------------:+:----------------:+:----------------:+
| Line                              | central comp.    | red comp.        | blue comp.       |
+-----------------------------------+------------------+------------------+------------------+
|                                   | $f\, [10^{-18}\,\mathrm{erg\,s^{-1}\,cm^{-2}}$\]       |
+-----------------------------------+------------------+------------------+------------------+
| $[O ii]3726,3729$                 | 5.8$\pm$0.4      | 2.1$\pm$0.4      | 8.9$\pm$1.6      |
+-----------------------------------+------------------+------------------+------------------+
| $[Ne iii]3869$                    | 3.3$\pm$0.2      | 0.8$\pm$0.2      | 1.3$\pm$0.9      |
+-----------------------------------+------------------+------------------+------------------+
| $He i3888+\mathrm{H8}^{*}$        | $<0.5$                                                 |
+-----------------------------------+------------------+------------------+------------------+
| $[Ne iii]3967+\mathrm{H\epsilon}$ | 1.5$\pm$0.4      | 0.4$\pm$0.3      | 0.4$\pm$1.4      |
+-----------------------------------+------------------+------------------+------------------+
| H$\delta$                         | 0.7$\pm$0.3      | 0.2$\pm$0.2      | 0.6$\pm$0.9      |
+-----------------------------------+------------------+------------------+------------------+
| H$\gamma$                         | 1.6$\pm$0.2      | 0.4$\pm$0.2      | 0.4$\pm$0.7      |
+-----------------------------------+------------------+------------------+------------------+
| $He i4472^{*}$                    | $<0.4$                                                 |
+-----------------------------------+------------------+------------------+------------------+
| $He ii4686$                       | 1.4$\pm$0.1      | $<0.2^{\dag}$    | 1.1$\pm$0.8      |
+-----------------------------------+------------------+------------------+------------------+
| H$\beta$                          | 3.9$\pm$0.2      | 0.6$\pm$0.2      | 2.9$\pm$0.7      |
+-----------------------------------+------------------+------------------+------------------+
| $[O iii]4959$                     | 17.5$\pm$0.5     | 1.8$\pm$0.4      | 8.7$\pm$1.5      |
+-----------------------------------+------------------+------------------+------------------+
| $[O iii]5007$                     | 53.1$\pm$1.0     | 5.6$\pm$1.0      | 26.3$\pm$1.6     |
+-----------------------------------+------------------+------------------+------------------+
| $He i5876^{*}$                    | $<0.6$                                                 |
+-----------------------------------+--------------------------------------------------------+
| $[Fe vii]6087^{*}$                | $<0.7$                                                 |
+-----------------------------------+------------------+------------------+------------------+
| $[O i]6300$                       | 2.4$\pm$0.2      | 0.3$\pm$0.2      | 3.1$\pm$0.8      |
+-----------------------------------+------------------+------------------+------------------+
| $[S iii]6312$                     | 0.4$\pm$0.2      | 0.2$\pm$0.2      | 0.9$\pm$0.9      |
+-----------------------------------+------------------+------------------+------------------+
| $[O i]6364$                       | 0.8$\pm$0.3      | 0.1$\pm$0.3      | 1.0$\pm$1.1      |
+-----------------------------------+------------------+------------------+------------------+
| $[N ii]6548$                      | 2.0$\pm$0.3      | 0.7$\pm$0.3      | 4.0$\pm$1.1      |
+-----------------------------------+------------------+------------------+------------------+
| H$\alpha$                         | 15.8$\pm$0.4     | 1.2$\pm$0.3      | 14.7$\pm$1.1     |
+-----------------------------------+------------------+------------------+------------------+
| $[N ii]6583$                      | 6.0$\pm$0.4      | 2.0$\pm$0.3      | 12.0$\pm$1.1     |
+-----------------------------------+------------------+------------------+------------------+
| $[S ii]6716$                      | 1.6$\pm$0.2      | 0.3$\pm$0.2      | 2.1$\pm$0.6      |
+-----------------------------------+------------------+------------------+------------------+
| $[S ii]6731$                      | 1.8$\pm$0.2      | 0.6$\pm$0.2      | 4.8$\pm$1.1      |
+-----------------------------------+------------------+------------------+------------------+

: Fitted emission line fluxes. The reported uncertainty is the direct $1\sigma$ output of `q3dfit`.

Table notes: $^{*}$ We report $3\sigma$ upper limits for lines with low S/N (Sect. [3.3](#subsec:line_emission)). $^{\dag}$ Though the $He ii4686$ has $S/N>10$, the fit reported the flux of its comp. red to be $0$. Hence, we report the upper limit here.

We fit the 1D spectrum presented in Section [3.3](#subsec:line_emission) (Fig. [2](#fig:spec_full)) using `q3dfit`. The continuum is modeled by a third order polynomial and the emission lines (S/N$>10$) are fitted with Gaussian profiles. We set the maximum number of the Gaussian components to be three for the fit. The centroid (width) of each corresponding Gaussian component is set to be the same (cite: Vayner_2023Q3D). The fitted line fluxes are shown in Table [4](#tab:emissionline). For the doublet $[O ii]3726,3729$, we set the flux ratio to be $1:1$ and report the summation since they are spectrally unresolved. For the low S/N lines (Section [3.3](#subsec:line_emission)), we report $3\sigma$ upper limits.

# Systemic redshift based on ionized gas

The systemic redshift (velocity zero) used in this work is based on the \[C i\](1-0) (cite: kolwa2023). Given its relatively faint flux and large observed beam size, it is unclear whether this traces the “authentic” redshift of the host galaxy. The ideal tracer would be the stellar absorption lines (e.g., Ca ii HK). However, the continuum emission near the nucleus is AGN dominated (Sect. [4.1](#subsec:low_z_comp)) for our target. Nevertheless, we report the \[O iii\] flux-weighted redshift based on the fitted “low-velocity” components from the entire FoV (Sect. [4.2](#subsec:linera_diag)). We define the “low-velocity” components as the ones with $|\Delta v|<300\,\mathrm{km\,s^{-1}}$ (cite: Fu_2009). The redshift is $z_{[O III]}=3.5908\pm0.0017$ which corresponds to $108\pm114\,\mathrm{km\,s^{-1}}$ with respect to the \[C i\](1-0) redshift. The $z_{[O III]}$ and $z_{[C i]}$ are consistent within the relatively large uncertainty.

In our calculation in Sect. [4.3](#subsec:ouflow), we assume the central component is the systemic component. Its $\Delta v_{\rm central}=238\pm10\,\mathrm{km\,s^{-1}}$ agrees with the systemic velocity estimated here from the entire FoV.

# Estimation of electron density

We use the fiducial value of $n_{e}$ in the calculation in Sect. [4.3](#subsec:ouflow) (cite: Nesvadba_2017b). The $n_{e}$ for the red and blue components can also be estimated based on the fitted \[S ii\]6716 and \[S ii\]6731 lines ratios (0.50 and 0.44 for red and blue components respectively; Table [4](#tab:emissionline)). This result in a $n_{e}\,\sim8\times10^{3}\mathrm{cm^{-3}}$ and $\sim8\times10^{4}\mathrm{cm^{-3}}$ for the red and blue components, respectively (cite: Sanders_2016). These are much larger than the fiducial value, $n_{e}=500\,\mathrm{cm^{-3}}$, from (cite: Nesvadba_2017b). However, the fitted line ratios for these two kinematic components are in the range where they are not sensitive to $n_{e}$. If we nevertheless use $n_{e}$ based on our estimation, the radiative coupling efficiency becomes $\sim10^{-7}$, and continues to support the conclusion is valid that the radiative-driven outflow is inefficient in 4C+19.71.

We report that the $n_{e}$ of the central component is $\sim800\,\mathrm{cm^{-3}}$ based on its \[S ii\]6716 and \[S ii\]6731 ratio (cite: Sanders_2016) which is the same order of magnitude as the value reported by (cite: Nesvadba_2017b). Further analysis is required to understand the electron temperature and density at the center.

[^1]: <https://github.com/spacetelescope/jwst>

[^2]: <https://q3dfit.readthedocs.io/en/latest/>

[^3]: <https://statics.teams.cdn.office.net/evergreen-assets/safelinks/1/atp-safelinks.html>

[^4]: <https://jwst-docs.stsci.edu/jwst-observatory-characteristics/jwst-pointing-performance>

[^5]: <https://jwst-docs.stsci.edu/jwst-observatory-characteristics/jwst-field-of-view>

</paper>

Write the methods card for this paper.