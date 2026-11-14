# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694L..15H\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694L..15H",
 "title": "Discovery of ionized circumstellar gas emission around the long-period Cepheid ℓ Carinae with ALMA",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Hocdé, V.",
 "n_authors": 6,
 "arxiv_id": "2501.19011",
 "doi": "10.1051/0004-6361/202453221",
 "alma_projects_linked_by_archive": [
  "2023.1.00196.S",
  "2024.1.00315.S"
 ]
}
```

Paper text:
<paper>
# Discovery of ionized circumstellar gas emission around the long-period Cepheid $\ell$ Carinae with ALMA

# Introduction

The Cepheid $\ell$ Carinae ($\ell$ Car, HD 84810, HIP 47854) has the largest angular diameter among southern hemisphere Cepheids (in average 2.9$\,$mas), making it an ideal candidate for investigating its photosphere and circumstellar environment. Additionally, with a pulsation period of $P = 35.55\,$days, $\ell$ Car is the closest analog to the long-period, extragalactic Cepheids observed by the James Webb Space Telescope (JWST). Therefore, understanding the evolution and the physics of this star is important to infer the properties of the Period-Luminosity (PL) relation of long-period Cepheids, which directly impact the accuracy of the distance scale. This is especially important now, as JWST is observing Cepheids in distant galaxies to refine the precision and reliability of these measurements (cite: Freedman2024IAU; Riess2024).

One of the intriguing phenomena associated with Cepheids is the possible presence of infrared (IR) circumstellar emission, which may serve as a tracer of their mass-loss rates (cite: Deasy1988) and may impact the accuracy of the PL relation (cite: Neilson2009; Neilson2010). However, circumstellar emissions originate from various environments, including gas and dust contributions from the local interstellar medium, extended circumstellar material produced by the star’s own mass loss, or an extended atmospheric layer near the stellar surface. Distinguishing between these components requires observations across different wavelengths and angular resolutions. For instance, *Spitzer* IRAC imaging has revealed low surface brightness emission around $\ell$ Car at 5.8 and 8.0$\,\mu$m, extending out to a radius of approximately 35$''$ (1.7 $\times 10^4$ AU; (cite: Barmby2011)). Closer to the star, a comparative study in the IR with *Spitzer*, VLT/VISIR, and VLTI/MIDI detected emission within a radius of 1$''$, attributed to warm circumstellar dust of a few 100 K at a distance of about 500 AU (cite: Kervella2009). This region might be associated to the circumstellar emission resolved at only a few stellar radii by near-IR interferometry in the $K$-band through VLTI/VINCI observations around $\ell$ Car (cite: kervella06a). Later, similar compact envelopes were resolved with CHARA/FLUOR (cite: merand06; merand07) around other Cepheids, as well as in the mid-IR, with MIDI and VLTI/MATISSE (cite: gallenne13b; Hocde2021). However, evidence from *Spitzer* low-resolution spectra and VLTI/MATISSE observations (cite: Hocde2020a; Hocde2025a) argue in favor of gaseous envelopes for most of the Cepheids, including $\ell$ Car. Therefore, these circumstellar emission could be related to an extended gas layer above the photosphere. Various authors reported a deep and static absorption feature in the H$\alpha$ line of $\ell$ Car (cite: Rodgers1968; nardetto08b; Hocde2020b), and a strong Mg II absorption line in the ultraviolet (UV) (cite: love1994), attributed to a gaseous envelope centered on the stellar restframe with an extension up to about 1000 AU. Chromosphere activity is also suspected for several Cepheids, in particular for $\ell$ Car, from Ca II K emission (cite: kraft57), several UV emission lines (cite: schmidt1982I), and the calcium IR triplet (cite: Hocde2020b). The presence of hot plasma is also revealed by periodic UV emission lines and X-ray emission (cite: engle14; engle2017; Andrievsky2023). On the modeling side, (cite: Hocde2020a) have shown that the IR excesses of Cepheids, including $\ell$ Car, can be explained by a thin envelope of ionized gas emitting free-free emission (cite: Hocde2021).

#### 

However, there is still no direct observational evidence of free-free emission toward Cepheids. Radio and millimeter-wave observations are useful to constrain ionized gas emission above the photospheric continuum as well as the spectral index. Prior to the recent results for $\delta$ Cep (cite: Matthews2023), only upper limits on continuum emission were obtained for the twelve Cepheids observed with radio telescopes (cite: welch1988; Altenhoff1994).. In particular, radio observations with the Very Large Array at 5$\,$GHz were performed by (cite: welch1988) who provided upper limits for the mass-loss rates of the order of $10^{-9}$ to $10^{-7}$ M$_\odot$/yr assuming ionized wind emission. Observations of radio spectral lines were attempted, too. (cite: Matthews2012; Matthews2016) observed the H I 21 cm transition with the VLA for different Cepheids. Recently, the first radio detection of continuum emission associated with a Cepheid ($\delta$ Cep) was reported based on VLA observations at 10-15 GHz (cite: Matthews2020; Matthews2023). These authors discuss different potential mechanisms responsible for the radio emission, including free-free emission from either a chromosphere, an optically thick ionized shell, or an ionized wind. However, obtaining the spectral index is essential to differentiate these scenarios.

In this letter, we explore the first millimeter-wave observation of the bright Cepheid $\ell$ Car with the Atacama Large Millimeter/submillimeter Array (cite: ALMA2009) in order to investigate the presence and the characteristics of the ionized gas emission. The advantages of observing at higher frequencies are twofold. First, using higher frequencies increases the spatial resolution, which helps mitigate confusion from background sources and potential companions, facilitating the study of regions at sub-arcsecond scales. Second, higher frequencies allow the observation of free-free emission from the stellar wind originating from the inner regions of the circumstellar gas, as the opacity decreases with increasing frequency. Finally, ALMA also allows us to investigate hydrogen recombination lines (cite: Peters2012). We present the ALMA observations and reduction in Sect. [2](#sect:observation) and the subsequent results in Sect. [3](#sect:analysis), in particular concerning the continuum, the spectral index and the RRL. We conclude in Sect. [4](#sect:conclusion).

# Observations of $\ell$ Car

We observed $\ell$ Car with the ALMA main array on 16 December 2023, 5 May, 1 July, 13 July, and 2 October 2024. Observations were conducted in two spectral setups in Band 6. Both setups used the continuum (frequency division mode, FDM) configuration of the correlator with a coarse spectral resolution of 7.8 MHz which is the result of averaging 16 channels before the data were stored. The first setup, *Setup 1*, effectively covers simultaneously the spectral ranges 211.6–215.3 and 227.6–231.4 GHz at a channel binning of about 10.7 km s$^{-1}$. The second spectral setup, Setup 2, covers higher frequencies, 255.1–258.9 and 270.9–274.6 GHz, at a channel binning of about 8.8 km s$^{-1}$. The spectral setup was designed not only to provide us with a good estimate of the continuum spectral index, but also to cover a few key spectral lines; for instance, the CO 2–1 and H29$\alpha$ lines at 230.5 and 256.4 GHz, respectively. The CO molecules can form in the Cepheid atmospheres which are metallic enough and have temperature of about 5000 K (cite: scowcroft2016). The project was executed at ALMA without a specific requirement on the array configuration, and, as a consequence, our target was observed 3 times in *Setup 1* (although two of these were very close in time), and 3 times in Setup 2 with different baseline lengths. Details of these observations can be found in Table [1](#tab:table-obs1). The visibilities were calibrated by the observatory using the default pipeline in CASA (cite: CASA). Self-calibration in phases was attempted but did not improve the image quality owing to insufficient signal-to-noise ratio in individual tracks. All imaging was done in CASA 6.6. using `tclean` procedures. Most of the analysis presented in this paper was done on images produced with natural weighting of visibilities, which optimizes the sensitivity of maps at the cost of spatial resolution.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
|  | Beam | $S_{\nu}$ | $S_{\nu}$ max | RMS | $\alpha$ | $S_{\nu}$ (BB) |
|  | ($''$) | (mJy) | (mJy/beam) | ($\mu$Jy/beam) |  | (mJy) |
| *Setup 1* | 0.70$\times$0.59 | 3.306 | 3.19 | 10.4 | $+1.45\pm0.16$ | 1.23 |
| *Setup 2* | 0.37$\times$0.30 | 3.992 | 3.37 | 9.60 | $+1.31\pm 0.09$ | 1.77 |
| *Setup 1+2* | 0.46$\times$0.39 | 3.689 | 3.35 | 7.06 | $+1.26\pm 0.06$ | 1.50 |

Table notes: All values for maps obtained at natural weighting. Flux density was calculated by a Gaussian fit to continuum images. Max represents the value of maximum pixel (central beam). Stellar photospheric component is not resolved and total fluxes are given. The uncertainty in $\alpha$ represents 1$\sigma$ confidence and does not include the uncertainty in absolute flux. $S_{\nu}$ (BB) is the flux density of the photosphere assuming black-body emission with T$_\mathrm{eff}$ and $\theta_\mathrm{UD}$ from Table [1](#tab:table-obs1) and derived using Eq. [\[eq:Sv\]](#eq:Sv). $S_{\nu}$ (BB) for *Setup 2* is the mean of the three epochs, *Setup 1+2* is the mean of the two setups.

# Results and discussion

Our ALMA observations result in a single unresolved point source at the position of $\ell$ Car with a beam size of about 0.6$''$ and 0.5$''$, respectively, for *Setup 1* and 2 (see Fig. [4](#fig:setup1_2)). This confirms the absence of any companion of $\ell$ Car brighter than about 35 $\mu$Jy (5$\sigma$) in Band 6 and within 15$''$ from the star. At uniform weighting of the visibilities which give effective resolution of 85 mas, the map shows a single point source. This is in line with earlier interferometric and radial velocity observations which excluded the possibility of a companion (cite: anderson16lcar), and is consistent with the analysis of *Gaia* proper motions (cite: Kervella2019). Flux densities for each Setup and for all continuum data combined are presented in Table [\[tab:measurements\]](#tab:measurements), with the flux density of $3.689\pm0.024$ mJy representing the midpoint of the covered frequencies. We inspected possible variability of the radio emission, in particular between the observations of the second setup which are taken at different phases of the pulsation cycle. We do not find variability between these three epochs above our measurement uncertainties (see Appendix [8](#appendix-fluxes)).

In order to compare the measured flux density with the stellar continuum, we derived the predicted flux assuming the emission follows the Rayleigh-Jeans regime of a black-body. Indeed, we can estimate the flux of $\ell$ Car at a given frequency knowing its effective temperature and angular diameter. Hereafter we assume that the millimeter continuum is formed at a similar photospheric radius as the optical and the IR. However we note that the millimeter continuum is formed slightly higher in the photosphere, because the atmosphere becomes optically thick at increasing height, as it is the case of the Sun (cite: Wedemeyer2016). In some extreme cases, the presence of gas in the high atmosphere can also form a radio-photosphere of much larger radius such as the ones observed in the case of AGB stars (cite: reid1997). The flux density $S_\nu$ in the Rayleigh-Jeans tail for a black-body subtended by a solid angle $\Omega$ follows the convenient form: $$\begin{equation}
\label{eq:Sv}
    S_\nu =\frac{2kT_\mathrm{eff}\nu^2}{c^2}\Omega\approx5.67.10^{-10}\left(\frac{T_\mathrm{eff}}{1\mathrm{K}}\right)\left( \frac{\nu}{1\mathrm{GHz}}\right)^2 \left(\frac{\theta}{1\mathrm{mas}}\right)^2 \mathrm{mJy}
\end{equation}$$ which is mostly sensitive to the variation of the limb-darkening (LD) angular diameter $\theta$ as compared to the effective temperature $T_\mathrm{eff}$.

Fortunately, the uniform disk (UD) angular diameter of $\ell$ Car is known precisely along the pulsation cycle owing to interferometric observations in the $H$-band with PIONIER/VLTI (cite: anderson16lcar) and in the $K$-band with VINCI/VLTI (cite: kervella04a) presented in Fig. [8](#fig:angular_diameter). In the following, we will neglect the LD effect by adopting the UD angular diameter. On the contrary the effective temperature of $\ell$ Car is not well characterized along the pulsation cycle. We found only one measurement given by (cite: Luck2018), with $T_\mathrm{eff}=5253\pm38\,$K measured at pulsation phase $\phi=0.05$. In the following we adopt this measurement for the closest epoch of observations. For the effectve temperature at $\phi=0.65$ and 0.26, we adopt interpolated values derived using the parallax-of-pulsation code `SPIPS` (cite: Merand2015), see Table [1](#tab:table-obs1).

For *Setup 1* at $\phi=0.06$ the measured angular size is $\theta=2.91\pm0.04\,$mas (cite: anderson16lcar) and the temperature measured by (cite: Luck2018) is adopted. Thus, we obtain an expected flux density for *Setup 1* of $S_\nu$$=1.23\pm0.12\,$mJy assuming a conservative 10% uncertainty because of the black-body assumption. Given the flux density of $S_\nu=3.31\,$mJy measured by ALMA, we obtain a significant excess, 2.7 times brighter than the stellar photospheric continuum. For *Setup 2*, we obtained observations at three different pulsation phases (see Table [1](#tab:table-obs1)). For the three epochs of $\ell$ Car, we derived an average predicted flux density of $S_\nu=1.77\pm0.18\,$mJy using Eq. [\[eq:Sv\]](#eq:Sv). Therefore, the measured flux density is about 2.2 times higher than the stellar continuum. Assuming a maximum $\theta_\mathrm{UD}$ of 3.2 mas for $\ell$ Car (at $\phi\approx0.4$, see Fig. [8](#fig:angular_diameter)), the upper limit for the flux density expected is $S_\nu\approx1.9\,$mJy. We present these measurements in Fig. [1](#fig:SED) together with photometry obtained in the visible and the IR (see Table [2](#tab:flux_density)) and an ATLAS9 atmosphere model (cite: castelli2003) derived from the effective temperature and the angular diameter corresponding to the pulsation phase of *Setup 2*. From this figure it is clear that the radio emission deviates significantly from Rayleigh-Jeans continuum of the star. We use the measured spectral index to constrain the mechanism giving rise to the millimeter emission.

![](Figures/l_Car_SED.pdf)

## Spectral index

For the first time we are able to derive the spectral index of the radio emission of a Cepheid, which is essential for understanding the origin of this emission (see Table [\[tab:measurements\]](#tab:measurements)). We derived an average spectral index of $+1.26\pm$0.06 (1$\sigma$). We calculated the spectral index using CASA’s tclean algorithm `mt-mfs`[^1] by applying a second-order ($N$=2) Taylor series. In the resulting maps, the spectral index $\alpha$ shows some variations within the region with strong continuum emission, and thus we take the average value from pixels lying roughly within a contour of 20% peak flux as the representative $\alpha$; as the associated uncertainty, we take the corresponding average 1$\sigma$ error calculated in tclean (see Appendix [7](#app:spectral_index) for an alternative method). When combining data from two different setups, the results depend quite strongly on the cross-calibration between the basebands. Our flux and bandpass calibration were performed using quasars, for which the observatory claims flux accuracy of about 10% (cite: Francis). For *Setups* 1 and 2 combined, this uncertainty translates to a systematic error in $\alpha$ of about 0.4. We therefore hereafter adopt $\alpha$=+1.26$\pm$0.44 (3$\sigma$).

In the hypothesis that excess flux is caused by free-free emission, the spectral index $\alpha$ ($S_\nu \propto \nu^\alpha$) constrains the physical characteristics of the emission region. For free-free emission from a spherical, symmetrically distributed ionized gas component with constant electron density, the spectral index shifts from $\alpha=-0.1$ in the optically thin regime (observed at frequencies above a critical threshold $\nu>\nu_c$) to $\alpha=+2$ in the optically thick regime at lower frequencies (cite: WrightBarlow1975; panagia1975; Olnon1975). This is, for example, the model proposed by (cite: Hocde2020a) to explain the IR excess of Cepheids constrained by low-resolution spectra from *Spitzer* which shows optically thick emission in the mid-IR (see the model for $\ell$ Car in Fig. [1](#fig:SED)). The spectral index at low frequency depends mostly on the density distribution of the ionized gas environment. Hence, the spectral index tends to $+0.6$ at low frequencies for emission in expanding envelopes corresponding to a spherically symmetric ionized wind with a density distribution given as $n_e\propto r^{-2}$. The spectral index calculated in CASA is twice larger than the nominal value of ionized wind emission. This spectral index is also comparable to chromospheric emission of the red supergiant (RSG) Antares in the millimeter regime (cite: OGorman2020) and also Betelgeuse in the centimeter (cite: OGorman2015). In these chromospheric regions of RSGs, the gas is partially optical thick, with a steep gradient in the ionized gas density. Specifically, the spectral index found in the case of $\ell$ Car might be explained if the electron density scales as $n_e \propto r^{-3.0}$ (cite: panagia1975). However, this spectral index is below the one derived in the model developed for $\ell$ Car and constrained by IR data (cite: Hocde2021) (see Fig. [1](#fig:SED)). This shows the importance of taking into account the density distribution when modeling the ionized gas emission. It is also not excluded that lower frequencies could probe the wind-dominated emission regime with $\nu^{+0.6}$, while observations at $\sim$200$\,$GHz are most sensitive to the inner regions of the gas envelope. Therefore, future observations at both higher and lower frequencies will help to probe the structure of the ionized gas environment of $\ell$ Car.

## Radio Recombination Line H29$\alpha$

Emission lines from Rydberg transition of hydrogen are produced from radiative recombination at high principal quantum numbers. They are an excellent tracers of ionized gas (cite: BookRRL2002). For example, emission from H30$\alpha$ was recently detected close to the surface of Betelgeuse at about 230$\,$GHz (cite: Dent2024). These authors proposed that periodic shocks might be the origin of the emission in the atmosphere.

Within our *Setup 2* observations we found a spectral feature which we identify as H29$\alpha$, that is a radio recombination line of Rydberg-like transition from principal quantum number $n$=29 of hydrogen. The emission coincides spatially with the continuum emission of $\ell$ Car. At the reference frequency of 256.302035 GHz, the emission is seen from –54 to 29 km s$^{-1}$ (Local Standard of Rest, LSR). Due to a coarse spectral sampling (8.8 km s$^{-1}$) and a modest signal-to-noise ratio (SNR), this range probably overestimates the spread of the emission. The velocity-integrated emission has a peak at 71.5 mJy/beam km s$^{-1}$ on maps (see Fig. [5](#fig:imageh29)) with rms noise of 6.63 mJy/beam km s$^{-1}$. In the general case, the RRL profile results from the convolution of a Gaussian component accounting for thermal and microturbulent broadening, and a Lorentzian component due to electron pressure broadening, as outlined by (cite: Brocklehurst1972). Hereafter we assume only a Gaussian profile for simplicity, as the low SNR prevents more detailed modeling. A Gaussian fit to the feature yields a full width at half power (FWHM) of 55.3$\pm$7.5 km s$^{-1}$ and a line center at –6.2$\pm$3.2 km s$^{-1}$ (1$\sigma$, LSR). For comparison, (cite: Dent2024) measured a FWHM of $\approx$42 km s$^{-1}$ for H30$\alpha$ from the chromosphere of Betelgeuse. The central velocity is equivalent to 7.2 km s$^{-1}$ in the Solar System barycenter frame, and thus is within the 3$\sigma$ errors consistent with the catalog systemic velocity of $\ell$ Car of 3.4 km s$^{-1}$ in the same rest frame (cite: Anderson2024). There is no doubt that the H$\alpha$ emission originates from $\ell$ Car. The current data do not allow us to conclusively determine the symmetry of the H29$\alpha$ line, which can be useful to probe local thermodynamical equilibrium conditions (cite: Peters2012). Data at a better SNR and spectral resolution are necessary to verify it.

The flux of $\ell$ Car’s H29$\alpha$ emission integrated over the spectral profile is 72.2 mJy km s$^{-1}$ or on average 0.9 mJy per channel in the $\sim$80 km s$^{-1}$ range occupied by the H$\alpha$ emission. This line flux is approximately equivalent to 35% of the continuum flux level at the same frequencies (3.5 mJy). The continuum flux is a combination of the photospheric component, estimated at this frequency to be 1.5 mJy from Eq ([\[eq:Sv\]](#eq:Sv)), and the atmospheric or circumstellar component, which we calculate simply as the total measured continuum flux minus the photospheric component, 3.5–1.5=2.0 mJy (cf. Table [\[tab:measurements\]](#tab:measurements)). The photospheric contribution was calculated as the blackbody radiation of a star with an effective temperature of 4850 K, and an angular diameter of 2.9 mas, representing the average properties of $\ell$ Car. Our calculation therefore leads to a flux ratio of line to non-photospheric continuum of about 0.45. This can be used to calculate the electron temperature of the plasma following the transfer equation for RRLs. With equation 2.124 in (cite: BookRRL2002), line width of 63 MHz, and an oscillator strength of 5.8174132 (cite: Goldwire1968), we find that an electron temperature of 23 500 K best explains the observed ratio, but the uncertainty in this value is very large, roughly 10 000 K (propagated from error in the flux of the emission line), due to a very low SNR and uncertain intrinsic line width. Also, the formula assumes optically thin emission for both components. Considering these limitations, we cannot exclude that the electron temperature is considerably higher than 23 500 K. On the other hand, assuming optically thick gas we can estimate a lower limit for the mean brightness temperature using Eq. [\[eq:Sv\]](#eq:Sv). We find a lower limit of 14 000 K and 11,000 K for *Setup 1* and *2* respectively, assuming the star angular diameter, which rapidly drop off as $\theta^{-2}$ for a larger source.

# Conclusions

In this letter, we presented ALMA observations of continuum and H29$\alpha$ emission for the long-period Cepheid $\ell$ Car. The presence of a ionized circumstellar gas is inferred from the following observational results

1.  We measured continuum emission of about 3.5 mJy at 200 GHz (1mm), which is about 2.5 times brighter than the stellar photospheric continuum at these frequencies.

2.  We derived a mean spectral index ($S_\nu\propto \nu^\alpha)$ of $\alpha=+1.26\pm$0.44 indicating partially optically thick ionized gas emission, similar to chromospheric emission from RSGs.

3.  We detected for the first time a RRL of H29$\alpha$ centered on the $\ell$ Car restframe and smaller than about 0.2$''$ ($\approx$100 au, $\approx$140 $R_\star$), which is direct evidence for the presence of ionized gas physically connected to the Cepheid. We derived a temperature of the gas of the order of few $10^4\,$K.

4.  We do not find significant evidence of variability among our different epoch of observations.

Hence, these observations reveal the emission of ionized gas connected to the star which is distinct from the photospheric emission. The spectral index derived is higher than expected from free-free emission of partially ionized wind, which prevents us from estimating a mass-loss rate. However, we cannot exclude that such emission can be detected at lower frequency. Our results suggest that the free-free emission originates from the hot gas of the star chromosphere, in line with previous emission lines from the literature for this star (cite: kraft57; schmidt1982I; love1994). However, the millimeter emission is not explained by the current model of the shell of ionized gas from (cite: Hocde2020a; Hocde2021), which suggests that this model could be improved by inclusion of density gradient and temperature. Interestingly, we find no significant evidence of variability of the emission in contrast to the results of (cite: Matthews2023) for $\delta$ Cep, which suggests that the free-free emission of $\ell$ Car is not directly linked to the pulsation. The temperature of the gas estimated, of the order of $10^4\,$K, is also not compatible with X-ray emission. The fact that the measurements of the spectral index and RRL of H29$\alpha$ are similar to what is found in RSGs of much lower effective temperature and with very active atmospheres also suggests that convection plays an active role to heat up the gas, as previously noted by (cite: sasselov94a; sasselov94c). Finally, given that $\ell$ Car is a nearby analog to the long-period Cepheids observed by the JWST, it is likely that other extragalactic Cepheids possess similar ionized gas emissions, too. As (cite: Neilson2009; Neilson2010) suggested that dust emission could impact the slope and the zero-point of the PL relation in different bands, the question remains whether ionized gas emission could affect the PL relation in the optical and the near-IR. Further observations are essential to reconstruct a complete radio SED, enabling us to better determine the temperature profile and physical properties of the ionized gas and for a larger sample of Cepheids.

# Acknowledgements

We gratefully thank the referee for valuable comments and suggestions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.1.00196.S and ADS/JAO.ALMA#2024.1.00315.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The research leading to these results has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreements No 695099 and No 951549). This work received the funding from the Polish-French Marie Skłodowska-Curie and Pierre Curie Science Prize awarded by the Foundation for Polish Science and the Polish Ministry of Science and Higher Education grant agreement 2024/WK/02. The authors acknowledge the support of the French Agence Nationale de la Recherche (ANR) under grant ANR-23-CE31-0009-01 (Unlock-pfactor). This research made use of the SIMBAD and VIZIER (Available at [http://cdsweb.u- strasbg.fr/](http://cdsweb.u- strasbg.fr/)) databases at CDS, Strasbourg (France) and the electronic bibliography maintained by the NASA/ADS system. This research also made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy2018). This research has benefited from the help of SUV, the VLTI user support service of the Jean-Marie Mariotti Center (<http://www.jmmc.fr/suv.htm>). This research has also made use of the Jean-Marie Mariotti Center `Aspro` service (Available at <http://www.jmmc.fr/aspro>).

62 natexlab

(ref: Altenhoff1994) Altenhoff, W. J., Thum, C., & Wendker, H. J. 1994, A&A, 281, 161

(ref: anderson16lcar) Anderson, R. I., Mérand, A., Kervella, P., et al. 2016, MNRAS, 455, 4231

(ref: Anderson2024) Anderson, R. I., Viviani, G., Shetye, S. S., et al. 2024, A&A, 686, A177

(ref: Andrievsky2023) Andrievsky, S. M., Kovtyukh, V. V., & Korotin, S. A. 2023, A&A, 671, A27

(ref: astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Barmby2011) Barmby, P., Marengo, M., Evans, N. R., et al. 2011, AJ, 141, 42

(ref: love1994) Bohm-Vitense, E. & Love, S. G. 1994, ApJ, 420, 401

(ref: Brocklehurst1972) Brocklehurst, M. & Seaton, M. J. 1972, MNRAS, 157, 179

(ref: CASA) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: castelli2003) Castelli, F. & Kurucz, R. L. 2003, in IAU Symposium, Vol. 210, Modelling of Stellar Atmospheres, ed. N. Piskunov, W. W. Weiss, & D. F. Gray, A20

(ref: Csorney2022) Csörnyei, G., Szabados, L., Molnár, L., et al. 2022, MNRAS, 511, 2125

(ref: Deasy1988) Deasy, H. P. 1988, MNRAS, 231, 673

(ref: Dent2024) Dent, W. R. F., Harper, G. M., Richards, A. M. S., Kervella, P., & Matthews, L. D. 2024, ApJL, 966, L13

(ref: engle2017) Engle, S. G., Guinan, E. F., Harper, G. M., et al. 2017, ApJ, 838, 67

(ref: engle14) Engle, S. G., Guinan, E. F., Harper, G. M., Neilson, H. R., & Remage Evans, N. 2014, ApJ, 794, 80

(ref: Fouqué2007) Fouqué, P., Arriagada, P., Storm, J., et al. 2007, A&A, 476, 73

(ref: Francis) Francis, L., Johnstone, D., Herczeg, G., Hunter, T. R., & Harsono, D. 2020, AJ, 160, 270

(ref: Freedman2024IAU) Freedman, W. L. & Madore, B. F. 2024, in IAU Symposium, Vol. 376, IAU Symposium, ed. R. de Grijs, P. A. Whitelock, & M. Catelan, 1–14

(ref: gaia2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: gallenne13b) Gallenne, A., Mérand, A., Kervella, P., et al. 2013, A&A, 558, A140

(ref: Goldwire1968) Goldwire, Henry C., J. 1968, ApJS, 17, 445

(ref: BookRRL2002) Gordon, M. A. & Sorochenko, R. L. 2002, Radio Recombination Lines. Their Physics and Astronomical Applications, Vol. 282

(ref: Herschel2024) Herschel Team, Schulz, B., Marton, G., et al. 2024, VizieR Online Data Catalog: Herschel/SPIRE point source catalog (HSPSC) (Herschel team+, 2017), VizieR On-line Data Catalog: VIII/112. Originally published in: Herschel catalogs (2017)

(ref: Hocde2025a) Hocdé, V., Matter, A., Nardetto, N., et al. 2024, arXiv e-prints, arXiv:2501.00373

(ref: Hocde2020b) Hocdé, V., Nardetto, N., Borgniet, S., et al. 2020a, A&A, 641, A74

(ref: Hocde2020a) Hocdé, V., Nardetto, N., Lagadec, E., et al. 2020b, A&A, 633, A47

(ref: Hocde2021) Hocdé, V., Nardetto, N., Matter, A., et al. 2021, A&A, 651, A92

(ref: Kervella2019) Kervella, P., Gallenne, A., Evans, N. R., et al. 2019, A&A, 623, A116

(ref: Kervella2009) Kervella, P., Mérand, A., & Gallenne, A. 2009, A&A, 498, 425

(ref: kervella06a) Kervella, P., Mérand, A., Perrin, G., & Coudé du Foresto, V. 2006, A&A, 448, 623

(ref: kervella04a) Kervella, P., Nardetto, N., Bersier, D., Mourard, D., & Coudé du Foresto, V. 2004, A&A, 416, 941

(ref: kraft57) Kraft, R. P. 1957, ApJ, 125, 336

(ref: Luck2018) Luck, R. E. 2018, AJ, 156, 171

(ref: Marton2024) Marton, G., Gezer, I., Madarász, M., et al. 2024, A&A, 688, A203

(ref: Matthews2020) Matthews, L. D., Evans, N. R., & Rupen, M. P. 2020, in American Astronomical Society Meeting Abstracts, Vol. 235, American Astronomical Society Meeting Abstracts #235, 106.03

(ref: Matthews2023) Matthews, L. D., Evans, N. R., & Rupen, M. P. 2023, AJ, 165, 92

(ref: Matthews2016) Matthews, L. D., Marengo, M., & Evans, N. R. 2016, AJ, 152, 200

(ref: Matthews2012) Matthews, L. D., Marengo, M., Evans, N. R., & Bono, G. 2012, ApJ, 744, 53

(ref: merand07) Mérand, A., Aufdenberg, J. P., Kervella, P., et al. 2007, ApJ, 664, 1093

(ref: Merand2015) Mérand, A., Kervella, P., Breitfelder, J., et al. 2015, A&A, 584, A80

(ref: merand06) Mérand, A., Kervella, P., Coudé du Foresto, V., et al. 2006, A&A, 453, 155

(ref: nardetto08b) Nardetto, N., Groh, J. H., Kraus, S., Millour, F., & Gillet, D. 2008, A&A, 489, 1263

(ref: Neilson2009) Neilson, H. R., Ngeow, C.-C., Kanbur, S. M., & Lester, J. B. 2009, ApJ, 692, 81

(ref: Neilson2010) Neilson, H. R., Ngeow, C.-C., Kanbur, S. M., & Lester, J. B. 2010, ApJ, 716, 1136

(ref: Neugebauer2019) Neugebauer, G., Habing, H. J., van Duinen, R., et al. 2019, IRAS Point Source Catalog v2.1 (PSC), NASA IPAC DataSet, IRSA4

(ref: OGorman2015) O’Gorman, E., Harper, G. M., Brown, A., et al. 2015, A&A, 580, A101

(ref: OGorman2020) O’Gorman, E., Harper, G. M., Ohnaka, K., et al. 2020, A&A, 638, A65

(ref: Olnon1975) Olnon, F. M. 1975, A&A, 39, 217

(ref: panagia1975) Panagia, N. & Felli, M. 1975, A&A, 39, 1

(ref: Peters2012) Peters, T., Longmore, S. N., & Dullemond, C. P. 2012, MNRAS, 425, 2352

(ref: reid1997) Reid, M. J. & Menten, K. M. 1997, ApJ, 476, 327

(ref: Riess2024) Riess, A. G., Anand, G. S., Yuan, W., et al. 2024, ApJL, 962, L17

(ref: Rodgers1968) Rodgers, A. W. & Bell, R. A. 1968, MNRAS, 138, 23

(ref: sasselov94c) Sasselov, D. D. & Lester, J. B. 1994a, ApJ, 423, 795

(ref: sasselov94a) Sasselov, D. D. & Lester, J. B. 1994b, ApJ, 423, 777

(ref: schmidt1982I) Schmidt, E. G. & Parsons, S. B. 1982, ApJS, 48, 185

(ref: scowcroft2016) Scowcroft, V., Seibert, M., Freedman, W. L., et al. 2016, MNRAS, 459, 1170

(ref: Smith2004) Smith, B. J., Price, S. D., & Baker, R. I. 2004, ApJS, 154, 673

(ref: Wedemeyer2016) Wedemeyer, S., Bastian, T., Brajša, R., et al. 2016, Space Sci. Rev., 200, 1

(ref: welch1988) Welch, D. L. & Duric, N. 1988, AJ, 95, 1794

(ref: ALMA2009) Wootten, A. & Thompson, A. R. 2009, IEEE Proceedings, 97, 1463

(ref: WrightBarlow1975) Wright, A. E. & Barlow, M. J. 1975, MNRAS, 170, 41

# Observational material

The observations hereafter are introduced in Sect. [2](#sect:observation). Figs. [4](#fig:setup1_2) and [7](#fig:H29plots) present the ALMA continuum observations and the radio recombination line H29$\alpha$ respectively.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:---|:--:|:--:|:--:|
|  | Date | Date | $t_{\rm on}$ | PWV | Baselines | $N_{\rm ant}$ | $\phi$ | T$_\mathrm{eff}$ | $\theta_\mathrm{UD}$ |
|  | obs. UTC | (MJD) | (min) | \(mm\) | \(m\) |  |  | \(K\) | (mas) |
| *Setup 1* | 2024-05-05 01:04:51 | 60435.04 | 38 | 1.19 | 15 – 99 | 42 | 0.02 | 5253$\pm$38 | $2.91\pm0.04$ |
| (221.61 GHz) | 2023-12-16 09:05:51 | 60294.38 | 38 | 3.26 | 15 – 2516 | 47 | 0.06 | 5253$\pm$38 | $2.91\pm0.04$ |
|  | 2023-12-16 08:08:02 | 60294.34 | 38 | 2.98 | 15 – 2516 | 47 | 0.06 | 5253$\pm$38 | $2.91\pm0.04$ |
| *Setup 2* | 2024-07-13 21:46:16 | 60504.91 | 44 | 0.34 | 15 – 2516 | 43 | 0.98 | 5253$\pm$38 | $2.91\pm0.04$ |
| (264.86 GHz) | 2024-07-01 20:23:21 | 60492.85 | 44 | 0.31 | 37 – 2516 | 43 | 0.65 | 4586$\pm$100 | $2.99\pm0.04$ |
|  | 2024-10-02 13:50:51 | 60585.56 | 41 | 0.94 | 15 – 499 | 42 | 0.26 | 4785$\pm100$ | $3.18\pm0.04$ |

: Journal of ALMA observations together with $\ell$ Car temperature and angular diameter.

Table notes: Journal of observations presented in Sect. [2](#sect:observation) for *Setup 1* and 2. $t_{\rm on}$ is time on source. PWV is the average precipitable water vapour during the observations. Baseline lengths represent datasets before pipeline flagging. $N_{\rm ant}$ is the number of unflagged antennas. For each epoch, we derive the pulsation phase using recent pulsation period and reference epoch at maximum light as measured by *Gaia*, $P_0=35.558\,$day and $T_0=56807.202$ (cite: gaia2023) and with a rate of period change from (cite: Csorney2022). For each pulsation phase $\phi$, the UD angular diameter $\theta_\mathrm{UD}$ are retrieved from the literature, while the effective temperature $T_\mathrm{eff}$ are retrieved from the literature and interpolated (see Sect. [3](#sect:analysis)).

![](Figures/IMAGE_L_CAR_SETUP1.pdf)

![](Figures/IMAGE_L_CAR_SETUP2.pdf)

![](Figures/IMAGE_L_CAR_H29alpha.pdf)

![](Figures/HISTO29line.pdf)

# Photometry and angular diameter measurements

![](Figures/Angular_diameter_lcar.pdf)

|           |                        |                     |            |
|:----------|:----------------------:|:-------------------:|:----------:|
| Inst.     | $\lambda_\mathbf{eff}$ |    Flux density     | References |
| *System*  |        ($\mu$m)        |        (Jy)         |            |
| *Johnson* |          0.44          |   72.6 $\pm$ 2.0    |    F07     |
| *Johnson* |          0.55          |    181 $\pm$ 5.1    |    F07     |
| *Cousins* |          0.75          |    274 $\pm$ 7.7    |    F07     |
| *2MASS*   |          1.22          |    382 $\pm$ 18     |    F07     |
| *2MASS*   |          1.65          |    342 $\pm$ 16     |    F07     |
| *2MASS*   |          2.16          |    269 $\pm$ 13     |    F07     |
| COBE      |          3.50          |    127 $\pm$ 17     |    S04     |
| IRAC      |          3.55          |     117 $\pm$ 4     |    K09     |
| IRAC      |          4.49          |     68 $\pm$ 2      |    K09     |
| COBE      |          4.90          |     60 $\pm$ 10     |    S04     |
| IRAC      |          5.73          |   46.3 $\pm$ 1.4    |    K09     |
| IRAC      |          7.87          |   29.1 $\pm$ 0.9    |    K09     |
| VISIR     |          8.60          |   24.6 $\pm$ 0.9    |    K09     |
| VISIR     |         11.22          |   18.1 $\pm$ 0.7    |    K09     |
| COBE      |         11.25          |   14.6 $\pm$ 0.5    |    S04     |
| IRAS      |         11.79          |   13.9 $\pm$ 0.3    |    I19     |
| IRAS      |         23.34          |   4.31 $\pm$ 0.26   |    I19     |
| MIPS      |         23.68          |   3.73 $\pm$ 0.15   |    K09     |
| IRAS      |         59.32          | 0.896 $\pm$ 0.0801  |    I19     |
| MIPS      |         71.42          |   0.45 $\pm$ 0.02   |    K09     |
| PACS      |          160           |  0.106 $\pm$ 0.013  |    M24     |
| SPIRE     |          250           | 0.0488 $\pm$ 0.0021 |    H24     |
| SPIRE     |          363           | 0.0288 $\pm$ 0.0023 |    H24     |

: Flux density in Janskys (Jy) at different wavelengths with associated uncertainties. The SED is displayed in Fig. [1](#fig:SED) complemented with ALMA observations. I19: (cite: Neugebauer2019), S04: (cite: Smith2004), F07: (cite: Fouqué2007), K09: (cite: Kervella2009), M24: (cite: Marton2024), H24: (cite: Herschel2024).

# Spectral index fit

As an alternative method of deriving $\alpha$ presented in Sect. [3.1](#sect:spectral_index), we generated a full spectrum of the map area within the 20% contour and fitted a line to the logarithmic version of the spectrum ($\log \lambda$ vs $\log F_{\nu}$), as shown in Fig. [9](#fig:spfit). This resulted in $\alpha$=+1.78$\pm$0.03 (1$\sigma$), a value higher than that obtained in CASA in Sect. [3.1](#sect:spectral_index). However, since the simple linear fit is more prone to calibration errors between the different frequency setups of the correlator (cite: Francis), we favor the result obtained in CASA.

![](Figures/mkImageSpFit.pdf)

# Fluxes in individual epochs

Flux densities were measured for each individual observation on restored images and using a Gaussian fit. They are presented in Table [3](#tab:table-obs2) along with the associated 1$\sigma$ errors derived from the statistical noise in the data and to the goodness of the fit [^2]. The fluxes measured for the last epoch in *Setup 2*, on 2 Oct 2024, are over 30% higher than in both earlier epochs. Although this discrepancy exceeds the 5$\sigma$ statistical uncertainties and 10% calibration errors from ALMA documentation, all measurements are consistent within the more realistic statistical errors from practical applications, as shown by (cite: Francis).

|     |                     |       |                 |                    |
|:---:|:-------------------:|:-----:|:---------------:|:------------------:|
|     |        Date         | Flux  | 1$\sigma$ error |     Beam size      |
|     |      obs. UTC       | (mJy) |      (mJy)      |       ($''$)       |
|     | 2023-12-16 09:05:51 | 3.506 |      0.038      | 0.307$\times$0.270 |
|     | 2023-12-16 08:08:02 | 3.562 |      0.044      | 0.317$\times$0.301 |
|     | 2024-05-05 01:04:51 | 3.213 |      0.066      | 1.136$\times$0.954 |
|     | 2024-07-13 21:46:16 | 3.265 |      0.021      | 0.213$\times$0.181 |
|     | 2024-07-01 20:23:21 | 3.821 |      0.040      | 0.228$\times$0.194 |
|     | 2024-10-02 13:50:51 | 4.653 |      0.032      | 0.869$\times$0.773 |

: Flux measurements for individual observations.

Table notes: Flux is integrated flux density measured by a Gaussian fit to an image. 1$\sigma$ error is the statistical uncertainty of the fit taken from the CASA’s `imfit` procedure, where the noise rms was specified based on image noise statistics. The uncertainties do not include statistical (calibration) uncertainties.

[^1]: <https://casadocs.readthedocs.io/en/v6.3.0/notebooks/synthesis_imaging.html>

[^2]: <https://casadocs.readthedocs.io/en/latest/api/tt/casatasks.analysis.imfit.html>

</paper>

Write the methods card for this paper.