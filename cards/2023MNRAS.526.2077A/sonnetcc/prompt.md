# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023MNRAS.526.2077A\sonnetcc\reply.txt

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
 "bibcode": "2023MNRAS.526.2077A",
 "title": "Radio-continuum decrements associated to shadowing from the central warp in transition disc DoAr 44",
 "year": 2023,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Arce-Tord, Carla",
 "n_authors": 11,
 "arxiv_id": "2309.10735",
 "doi": "10.1093/mnras/stad2885",
 "alma_projects_linked_by_archive": [
  "2018.1.00028.S",
  "2019.1.00532.S"
 ]
}
```

Paper text:
<paper>
# Radio-continuum decrements associated to shadowing from the central warp in transition disc DoAr 44

## Abstract

Warps have often been used to explain disc properties, but well characterised examples are important due to their role in disc evolution. Scattered light images of discs with central gaps have revealed sharp warps, such that the outer rings are shadowed by tilted inner discs. The near-IR intensity drops along the ring around TTauri star DoAr 44 have been interpreted in terms of a central warp. We report new ALMA observations of DoAr 44 in the continuum at 230 GHz and 350 GHz (at $\sim$10 au), along with a new epoch of SPHERE/IRDIS differential polarised imaging taken during excellent weather conditions. The ALMA observations resolve the ring and confirm the decrements proposed from deconvolution of coarse 336 GHz data. The scattered light image constrains the dips, which correspond to a misaligned inner disc with a relative inclination $\xi$ = 21.4 $^{+6.7}_{-8.3}$ deg. The SPHERE intensity profile shows a morphological change compared to a previous epoch that may be interpreted as a variable orientation of the inner disc, from $\xi$ $\sim$ 30 deg to $\xi$ $\sim$ 20 deg. The intensity dips probably correspond to temperature decrements, as their mm-spectral index, $\alpha^{230 \textrm{GHz}}_{350 \textrm{GHz}} \sim$ 2.0 $\pm$ 0.1, is indicative of optically thick emission. The azimuth of the two temperature decrements are leading clockwise relative to the IR-dips, by $\eta$ = 14.95 deg and $\eta$ = 7.92 deg. For a retrograde disc, such shifts are expected from a thermal lag and imply gas surface densities of $\Sigma_g$ = 117 $\pm$ 10 g/cm$^2$ and $\Sigma_g$ = 48 $\pm$ 10 g/cm$^2$. A lopsided disc, with contrast ratio $f_r$=2.4 $\pm$ 0.5, is also consistent with the large continuum crescent.

planetary systems: protoplanetary discs – planet-disc interactions

# Introduction

Transition discs (cite: Espaillat2010) are useful sources for the study of circumstellar disc warps. This is due to their characteristic inner dust cavity, which may have been cleared by the orbit of young planets (cite: dong15). Resolved observations in scattered light have revealed azimuthal dips along the outer rings. For instance, infrared (IR) and optical scattered light observations in HD 142527 (cite: fukagawa+2006; casassus12; avenhaus14) revealed dips in the outer disc thought to be shadows due to a central warp (cite: marino15). The shadows in this disc, seen in polarised-differential imaging (PDI), are explained by a tilted inner disc, 70$^\circ$ relative to the outer disc.

Analysis of gas kinematics traced by ALMA observations of HD 142527 in CO(6$-$5) showed that the intra-cavity gas is close to free-fall through the central warp (cite: casassus15). This warped structure is most likely caused by the inclined orbit of the low mass companion HD 142527B (cite: biller12; price18), which translates into shadows deep enough to cool the dust in the outer ring and cause the local decrements in the ALMA continuum (cite: casassus15b).

Observations with the Spectro Polarimetric High-contrast Exoplanet REsearch (cite: beuzit19) instrument at the Very Large Telescope (VLT) have confirmed and revealed more detailed information on the azimuthal dips in TDs. For instance, another example of a warp related to a tilted inner disc is HD 100453. (cite: benisty17) observed polarised scattered light using VLT/SPHERE at optical and Near-IR wavelengths, and found azimuthal dips interpreted as narrow shadows by (cite: min+17). However, scattered light observations of shadowed outer rings often do not have radio counterparts. This is the case for HD 100453 (cite: vanderplas+2019), and also for warped disc HD 143006 (cite: perezL+2018), both of which show shadows in SPHERE polarised intensity with no radio counterparts in ALMA Band 6. The absence of radio decrements under the shadows may be due to disc thermal radiation, which if optically thin [^2], can smooth out the temperature decrement (cite: casassus_2019_cooling). Thus, for a fixed dust population, such temperature decrements would be more conspicuous in massive discs.

![](figures/band6_SBLB_briggs1.pdf)

![](figures/band7_SBLB_briggs1.pdf)

![](figures/sphere_data.pdf)

An example of smoothed radio decrements due to radiative diffusion can be observed in DoAr 44. DoAr 44 (also known as WSB 72, HBC 268 or ROXs 44) is a T-Tauri young stellar object (YSO) located in the L1689 region of the Ophiuchus dark cloud (cite: padgett08; andrews11) at a distance of 145.9 $\pm$ 1.0 pc (cite: gaia18). It is catalogued as a pre-transition disc (PTD) as represented by its spectral energy distribution (SED) in (cite: cieza21), with a SED slope $\alpha_{\mathrm{IR}}>$ = $-$ 0.61. Here, PTDs are defined as Class II sources ($-$0.3 $>\alpha_{\mathrm{IR}}>-$1.6) with an IR bright inner disc and a mid-IR SED decrement that indicates the existence of a gap. Also, DoAr 44 is included in the multiplicity survey by (cite: zurlo20), but no companion was detected.

Previous works on DoAr 44, using SMA (Submillimeter Array) 340 GHz continuum observations at an angular resolution of 0.3 ″(cite: andrews09; andrews11) and ALMA 335 GHz continuum with spectral observations (cite: vandermarel16) have detected a moderate $\sim$ 30 au cavity in the disc. (cite: casassus18) proposed a warped geometry inside the cavity by studying azimuthal decrements using ALMA 336 GHz continuum observations, complemented with SPHERE/IRDIS (Infrared Dual-band Imager and Spectrograph) differential polarised imaging (DPI) and radiative transfer (RT) parametric models. A comparison with RT predictions suggests that the inner disc is tilted by $\xi$ $\sim$ 30 deg relative to the plane of the outer disc. However, the IRDIS data are affected by the coronograph, which borders the edge of the cavity. Paper I used aggressive deconvolution in order to improve the resolution of the ALMA data available at the time for their analysis, which suggested the presence of a radio dip associated to the northern shadow.

Here, we report new short and long-baseline (SB+LB) ALMA observations and a 3-year time difference follow-up SPHERE/IRDIS VLT observations of DoAr 44. We aim to analyse the variability of the shadows generated by the warped inner disc over the outer disc, using multi-epoch ALMA Band 6 and Band 7 data and comparing follow-up SPHERE polarised intensity observations to the previous published epoch.

Section [2](#sec:obs) of this paper describes the ALMA and SPHERE observations, along with the data reduction. In Sec. [3](#sec:analysis) we describe the characteristics of the azimuthal intensity decrements, of the orientation of the inner disc and of the spectral index map between the radio bands, and Sec. [4](#sec:conc) concludes.

![](figures/sphere_2016.pdf)

![](figures/profiles_comparison_restored.pdf)

# Observations and Data Reduction

## ALMA observations

The Ophiuchus DIsc Survey Employing ALMA (cite: cieza19) LB survey was carried out during ALMA Cycle 6 in Band 6 (230 GHz), reaching resolutions of $\sim$ 3-5 au (PID = 2018.1.00028.S). The aim of this survey is to study the dust and gas components of a flux-limited population of discs, in a wide range of evolutionary stages, located in the Ophiuchus star-forming region at a distance of $\sim\,200$ pc (cite: evans09; williams19). These Band 6 continuum observations of DoAr 44 (bandwidth of 7.5 GHz) were acquired in two epochs during July of 2019, and the data were calibrated using the ALMA Calibration Pipeline in CASA (cite: cieza21). The continuum Band 7 observations of DoAr 44 (PID = 2019.1.00532.S) were carried during May of 2021, in Cycle 7, with an on-source integration time of 43 minutes and a bandwidth of 4.688 GHz.

Self-calibration of the continuum data-sets was performed with the `SNOW` package (cite: casassus_22_selfcal), which uses the `uvmem` package (cite: casassus_22_selfcal; casassus21; casassus18) to replace the `tclean` model in the CASA selfcal iterations (cite: casa). The resulting peak signal to noise ratios (PSNR) in the restored images are $\sim$ 60 for Band 6 and PSNR $\sim$ 100 for Band 7, for Briggs weights with robustness parameter of 1.0. For comparison, the standard `tclean` selfcal resulted in PSNR $\sim$ 49 in Band 6 and PSNR $\sim$ 90 in Band 7. Finally, the Band 6 data-set was aligned to the Band 7 data-set using the `VisAlign` package (cite: casassus_22_selfcal), but without scaling in flux.

Figure [1](#fig:b-fig) shows the reconstructed image for ALMA Band 6, with an rms noise of $\sigma_{230\,\mathrm{GHz}}\,\sim\,$0.019 mJy beam$^{-1}$ and a synthesized `tclean` beam of 72.4 mas $\times$ 62.7 mas. Figure [2](#fig:c-fig) shows the reconstructed image for ALMA Band 7, with an rms noise of $\sigma_{350\,\mathrm{GHz}}\,\sim$0.025 mJy beam$^{-1}$ and a synthesized `tclean` beam of 70.2 mas $\times$ 53.8 mas.

For the position of the star, we used *Gaia* coordinates (cite: gaia18) of RA 16:31:33.4638 ($\pm$ 0.0534 mas), DEC $-$24:27:37.1582 ($\pm$ 0.0404 mas), which were extrapolated to RA 16:31:33.454 , DEC $-$24:27:37.682  by using a proper motion of ($-$6.101 $\pm$ 0.128, $-$24.212 $\pm$ 0.098) mas yr$^{-1}$. The center of the cavity (as calculated with `MPolarMaps` in Sec. [3.1](#sec:profiles)), is shifted, with respect to the *Gaia* coordinates by $\Delta$RA $=$ 1 mas, $\Delta$DEC $=$ 6 mas in Band 6, and by $\Delta$RA $=$ 6 mas, $\Delta$DEC $=$ 7 mas in Band 7, as presented in Table [1](#tab:pa_inc). Given this, we can safely discard that this shift is due to a *Gaia* pointing error ($\sim$0.15 mas at 3$\sigma$). On the other hand, the accuracy of the ALMA data astrometry is regularly taken as $\sim$1/10 of the synthetic beam (cite: alma_book), which translates into $\sim$7 mas for both Band 6 and Band 7. This implies an ALMA pointing error of 21 mas at 3$\sigma$, so the shifted cavity coordinates for both bands are within the errors.

## SPHERE observations

We also used data from follow-up observations with SPHERE, the planet finder of the VLT. In this work, we use the 2019 data (preceded by 2016 096.C-0523(A) data, PI Avenhaus) from IRDIS (cite: dohlen08), a differential imaging NIR camera (working in a range from 900 nm to 2.3 $\upmu$m), in the DPI mode, (cite: deboer2020). The DoAr 44 data were acquired with the IRDIS instrument on September 22 of 2019, and consisted of 60 frames in total. The observation was done in coronagraphic polarimetry mode. The 56 science frames (14 polarimetric cycles) were flanked with ‘flux’ and ‘centering’ frames. The flux frames are taken with the star displaced from the coronagraph and allow to estimate the flux of the star. Then, with the ‘N_ALC_YJH_S’ coronagraph (with a radius of 92.5 mas and an inner working angle, IWA, of $\sim$0.15 arcsec) in place, the acquired star center frames allow a precise determination of the position of the star behind the coronagraph. There were no unexpected artifacts in the science frames and all the polarimetric cycles were successfully completed with a closed adaptive optics loop, thus, no data were discarded to produce the final images. As a result, these scattered light observations were conducted with a better seeing in comparison to the observations presented in (cite: avenhaus_2018_sphere) and in paper I. The seeing varied from 0.41$"$ at the beginning of the observations, had a peak at around 0.8$"$ and went down to $\sim$ 0.6$"$ at the end of the run. We also acquired data of DoAr 44 using the Zurich Imaging Polarimeter (ZIMPOL), however, these observations were designed without considering a coronograph, resulting in lower quality images that were not considered for this work.

The SPHERE data reduction was performed with the publicly available pipeline irdap (cite: VanHolstein2020A&A...633A..64V) version 1.3.3. irdap extracts the images of the left and right optical channels and performs the centering using the star center frames. For each measurement taken at half wave plate (HWP) angles (0, 45, 22.5, and 67.5) the left beam is subtracted from the right beam producing the Q+, Q-, U+ and U- (double difference) images. The single sum of these left and right images (double sum) is used to produce the total intensity images. The double difference images are used to obtain the Stokes Q, U and I images. Subsequently, irdap corrects the Stokes images for instrumental polarisation using a detailed model of the instrument’s optical path. Here we performed the analysis using the $H$-band polarised intensity image, $Q_{\phi}(H)$, as shown in Fig. [3](#fig:a-fig).

![](figures/all_restored.pdf)

![](figures/profiles_restored_final.pdf)

A crucial step in the reduction is the subtraction of the halo of polarised signal associated with the unresolved signal within the central PSF, the so-called "unresolved" polarisation. To remove this component we selected an annular region devoid of disc signal centered on the star with a radius of 40 to 90 pixels. The degree of linear polarisation measured from the unresolved central source in DoAr 44 is 1.6$\pm$0.4%, the polarisation angle (AoLP) of the central source is AoLP$_{\mathrm{central}}$ = 19.97$\pm$7.25 deg, and the uncertainty is the standard deviation of the unresolved polarisation signal during the polarimetric cycles. This uncertainty is caused by variations in the atmospheric conditions and is higher than the statistical uncertainty and the accuracy of the Mueller matrix model used to correct the instrumental polarisation.

An interesting feature to point out is that the locations of the intensity decrements change after the unresolved polarisation subtraction. This effect was seen for different locations of the signal-devoided annular region. The polarised light halo that is associated to the unresolved signal most likely has an asymmetric pattern due to unresolved tilted inner disc around the star. This pattern contributes to a variability in the contrast of the intensity distribution (cite: keppler20), so, when subtracted, the location of the decrements are slightly affected. This is expected as a result of correcting for the shadowing produced by the inner interstellar (IS) polarisation.

In Figure [5](#fig:2a-sphere) we compare our SPHERE/IRDIS $Q_{\phi}(H)$ observations with the SPHERE/IRDIS 2016 $Q_{\phi}(H)$ observations described by (cite: avenhaus_2018_sphere) (project 0.96.C-0523(A)) and presented in paper I. Note that we subtracted the unresolved polarisation from both data-sets using irdap and considering the parameters described above. As confirmed by the profiles in Figure [6](#fig:2b-sphere), the location of the north-western dip varies slightly between both data-sets, however, they show different locations for the south-eastern decrement. There are also variations in the peak intensities between epochs. This discrepancies will be further addressed in Section [3.3](#sec:warpgeo).

# Analysis

## Azimuthal profiles

We trace the location of the decrements in the ring around DoAr 44 with the `MPolarMaps` package, described in (cite: casassus21). This allows us to extract the ring intensity profile $I^{\circ}$($\theta$) as a function of azimuth $\theta$ along a circle that best approximates the disc ring, by minimizing the dispersion in the radial profile of the continuum and under the assumption of axial symmetry. As a result, we get the best fits values for the position angle (PA), the inclination ($i$) and the stellar offsets.

As shown in Table [1](#tab:pa_inc), the 230 GHz ALMA data gives an inclination $i$ = 21.7 $\pm$ 0.3 deg and a PA = 59.9 $\pm$ 0.8 deg, and the offsets from the nominal stellar position are $\Delta$RA = 1 mas and $\Delta$DEC = 6 mas. Similarly, the optimization for the 350 GHz ALMA data gives an $i$ = 21.9 $\pm$ 0.2 deg and a PA = 61,6 $\pm$ 0.5 deg, with offsets from the nominal stellar position as $\Delta$RA = 6 mas and $\Delta$DEC = 7 mas. Since the $Q_{\phi}(H)$ continuum does not show a continuous disc geometry due to its pronounced decrements, we fitted a continuous ellipse to the emission and used the result to run the `MPolarMaps` optimization. This gives an $i$ = 24.4 deg and a PA = 49.7 deg for the $Q_{\phi}(H)$ data, with offsets from the nominal stellar position as $\Delta$RA = 2 mas and $\Delta$DEC = 2 mas. Note that the measurement of $I^{\circ}$($\theta$) depends on the choice of origin, but, as explained in Section [2.1](#sec:almadata), the offset between the stellar position and the center of the cavity is within the ALMA and *Gaia* pointing errors. Given this, we can safely center the cavity to *Gaia* coordinates, as presented in Figure [8](#fig:3a-fig).

|                     |    230 GHz     |    350 GHz     | $Q_{\phi}(H)$ fit |
|:--------------------|:--------------:|:--------------:|:-----------------:|
| Position Angle (PA) | 59.2 $\pm$ 0.8 | 61.6 $\pm$ 0.5 |   49.7$\pm$ 1.9   |
| Inclination ($i$)   | 21.7 $\pm$ 0.3 | 21.9 $\pm$ 0.2 |   24.4$\pm$ 0.8   |
| RA offset (mas)     |  1 $\pm$ 0.1   |  6 $\pm$ 0.1   |    2$\pm$ 0.1     |
| DEC offset (mas)    |  6 $\pm$ 0.1   |  7 $\pm$ 0.1   |    2$\pm$ 0.1     |

: Position angle and ring inclination values for DoAr44 from the polar optimization.

$Q_{\phi}(H)$ observations do not show a continuous disc, which is required for a correct polar optimization, thus, we performed a Gaussian fit along the emission peak in order to calculate the disc PA and inclination.

East of North.

+-------------------------------------------------+----------------------------------------------+----------------------------------------------+
|                                                 | Decrement 1 (south)                          | Decrement 2 (north)                          |
+:===============================================:+:============:+:============:+:==============:+:============:+:============:+:==============:+
| 2-7                                             | 230 GHz      | 350 GHz      | $Q_{\phi}(H)$  | 230 GHz      | 350 GHz      | $Q_{\phi}(H)$  |
+-------------------------------------------------+--------------+--------------+----------------+--------------+--------------+----------------+
| I$_{\mathrm{D}}$/I$_{\mathrm{Peak}}^\mathrm{a}$ | 98$\pm$1$\%$ | 81$\pm$1$\%$ | 11$\pm$0.1$\%$ | 83$\pm$1$\%$ | 89$\pm$1$\%$ | 13$\pm$0.1$\%$ |
+-------------------------------------------------+--------------+--------------+----------------+--------------+--------------+----------------+
| $\theta_{\mathrm{sky}}$\[$\circ$\]$^\mathrm{b}$ | 152.9        | 152.9        | 160.9          | 316.3        | 316.9        | 331.8          |
+-------------------------------------------------+--------------+--------------+----------------+--------------+--------------+----------------+
| r$_{\mathrm{star}}$\[arcsec\]$^\mathrm{c}$      | 0.29         | 0.28         | 0.12           | 0.32         | 0.31         | 0.12           |
+-------------------------------------------------+--------------+--------------+----------------+--------------+--------------+----------------+

$^\mathrm{a}$ Minimum intensity over peak along the ring.

$^\mathrm{b}$ Position Angle (location) of the decrement on the plane of the sky East of North. The errors for these values are calculated as 1/10 of the resolutions, which are in the order of 10$^{-6}$.

$^\mathrm{c}$ Stellocentric separation of the decrements on the sky.

The `MPolarMaps` also records the intensity profiles as a function of azimuth for the radial maxima along the ring, which lets us estimate the location of the intensity decrements. In Figure [9](#fig:3b-fig) we show the ring intensity profiles for all data-sets and the positions of the radio/IR intensity decrements along the projected circles. These positions, indicated by thin lines, correspond to the minima in $I^{\circ}$($\theta$). Table [\[tab:summary\]](#tab:summary) shows the results for the optimization: the PA of the decrement (East of North) as viewed on the sky ($\theta_{\mathrm{sky}}$) and the stellocentric distance to the decrements on the sky (r$_{\mathrm{star}}$).

Table [\[tab:summary\]](#tab:summary) shows that the PAs for both decrements at 230 GHz, 350 GHz and $Q_{\phi}(H)$ are closely coincident. Also, it is interesting to note that the mm-continuum, towards the north-east in Figure [8](#fig:3a-fig), is nearly coincident with the maximum in the $Q_{\phi}(H)$ emission, as also seen in Figure [9](#fig:3b-fig). We find similar results in paper I, where they tested parametric models in order to analyse the characteristics of the disc. Their results suggested that a tilted inner disc provided the simplest explanation for the presence of the decrements in DoAr 44. An inner disc has been detected with ALMA in $^{12}$CO emission by (cite: antilen+23).

| Observed parameters in $Q_{\phi}(H)$     |                              |
|:-----------------------------------------|:----------------------------:|
| PA                                       |          161.7 deg           |
| Angular separation ($\omega$)            |          170.9 deg           |
| Stellar offset ($b$)                     |             0.14             |
| Calculated parameters for the inner disc |                              |
| Inclination ($i_1$)                      |  26.4 $^{+5.6}_{-3.5}$ deg   |
| PA ($\phi_1$)                            | 110.7 $^{+12.7}_{-13.9}$ deg |
| Scale Height ($h$)                       |  0.014 $^{+0.006}_{-0.004}$  |
| Relative Inclination ($\xi$)             |  21.4 $^{+6.7}_{-8.3}$ deg   |

: Observed and calculated values for the orientation of the inner disc in DoAr44 using the idealized geometrical argument.

## Radio/IR intensity decrements

The $Q_{\phi}(H)$ image (Fig. [3](#fig:a-fig)) shows a ring divided into bipolar arcs separated by deep intensity decrements, while the 230 GHz and 350 GHz continuum images (Figs. [1](#fig:b-fig) and [2](#fig:c-fig)) show a smoother and approximately face-on projected circle. However, it is interesting to note the contrast between the mm-continuum and the IR in Fig. [9](#fig:3b-fig), which shows that the decrements are much more prominent in the IR data. Also, the radio decrements of the disc appear to be shifted ahead of the IR decrements in the direction West of North (clockwise). The angular separations between the radio and IR dips on the plane of the disc ($\eta_{\mathrm{shift}}$) are $\eta_{\mathrm{shift}}$ = 14.95 deg for the northern decrements, and $\eta_{\mathrm{shift}}$ = 7.92 deg for the southern decrements. As the dust and gas enter the shadows, we would expect to see the dust temperature decrements shifted with respect to the IR scattered light shadows (cite: casassus_2019_cooling). Provided a clockwise direction of rotation, the observed offset between the radio and IR shadows could be attributed to a thermal lag, and it is interesting to point out that this clockwise offset, where the radio decrements lead, is observed in different epochs (in paper I and in this work). However, a more detailed analysis with simultaneous multi-frequency imaging could provide a better grip on such thermal lag. We also note that the radio decrements in the south of the disc cannot be defined with high precision compared to the northern decrements: the disc appears to be less massive and narrower in the location of the southern decrements (as also proposed by (cite: casassus_2019_cooling)), hence with a lower optical depth to radiation diffusion, which smooths the temperature decrements. This will be further analysed in Sections [3.3](#sec:warpgeo) and [3.5](#sec:discmass).

## Warped inner disc

Shadows in a transition disc can be interpreted as caused by a misaligned inner disc with respect to the outer disc (cite: marino15; benisty17). The scattered light $Q_{\phi}(H)$ image of DoAr 44 clearly reveals the location of two shadows on the outer ring (Figs. [3](#fig:a-fig) and [10](#fig:decrements)) Also, Figure [7](#fig:sphere_comparison) shows a difference between the (cite: avenhaus_2018_sphere) $Q_{\phi}(H)$ observations and our $Q_{\phi}(H)$ observations. Note that the unresolved polarised emission was subtracted from both data-sets using the same parameters in irdap (Sec. [2.2](#sec:spheredata)), but the observing conditions in each epoch could have an effect on the applied correction. However, the unmatched locations of the dips between the two infrared profiles would point toward a morphological change in the location of the dips between epochs, which appears to be more significant for the southern dip. Changes in the location and morphology of intensity dips have been previously identified in other discs, for instance, in J1604, using multi-epoch scattered light observations (cite: pinilla+18). In the case of DoAr 44, the variability in the morphology and the location of the dips is most likely related to an illumination effect due to a shift in the orientation of the tilted inner disc. We analyse this interpretation by using two approaches: an idealized geometrical model for the location of the shadows and a qualitative analysis with radiative transfer (RT) predictions.

![](figures/specind_07error_colorscale.pdf)

![](figures/error_07error.pdf)

### Idealized geometrical model

(cite: min+17) propose an algorithm that considers the location of the observed shadows as the intersection of the inner disc midplane with a perfectly circular outer disc. This scheme relates the inner disc orientation (this is, inclination ($i_{1}$) and PA ($\phi_{1}$) on the sky), to the scale height ($h$) of the outer disc, the PA of the observed shadows (PA) and their subtended angle relative to the star ($\omega$), and the stellar offset ($b$, the intercept of the inner disc PA with the North). In practice, however, some uncertainties arise: the fact that the observed $Q_{\phi}(H)$ cavity is not perfectly circular makes it difficult to determine its center with precision. Also, the exact locations of the center of the shadows, this is, the decrement minimum, might not necessarily be in the midplane of the inner disc. Taking these caveats into consideration, we calculated the inner disc orientation by considering the observed values presented in Table [2](#tab:warpgeo). These give us an inner disc orientation of $i_{1}$ = 26.4 $^{+5.6}_{-3.5}$ deg, $\phi_{1}$  =110.7 $^{+12.7}_{-13.9}$ deg and $h$ =0.014 $^{+0.006}_{-0.
004}$, with uncertainties corresponding to the 1$\sigma$ confidence intervals. We find that the PA value for $Q_{\phi}(H)$ (Table [\[tab:summary\]](#tab:summary)) is significantly different than that of the inner disc. These results provide support to the interpretation of the shadows being caused by a misalignment between the inner and outer discs. (cite: bouvier+20) derived similar results for the orientation of DoAr 44’s inner disc: they fitted the continuum visibilities of 2019 VLT/GRAVITY observations and calculated an inclination of $i_{1}$ = 34 $\pm$ 2 deg and a PA of $\phi_{1}$  =140 $\pm$ 3 deg. Since polarisation vectors are azimuthally oriented in discs, the AoLP can be either parallel or perpendicular to the direction of the disc PA (cite: stolker+17). It is interesting to note that the polarisation angle of the central source, AoLP$_{\mathrm{central}}$ =19.97$\pm$ 7.25 deg, is perpendicular to the inner disc PA, $\phi_{1}$  =110.7 $^{+12.7}_{-13.9}$ deg. Also, in Fig. [10](#fig:decrements) we see that the radio intensity decrements lead in the direction west of north, both in the northern and southern regions. Considering the geometrical approach shown in (cite: min+17), if the azimuthal shift was only related to projection effects due to the emission heights, we would see the northern and southern decrements shifted opposite relative to rotation.

The orientation values we calculated from the idealized geometrical method for DoAr 44’s warped inner disc correspond to a relative orientation of $\xi$ = 21.4 $^{+6.7}_{-8.3}$ deg with respect to the outer disc. We can compare this orientation of the inner disc with the results of (cite: bohn+22), who fit parametric models to the 2019 VLT/GRAVITY visibilities in order to derive the geometry of the inner disc, while the geometry of the outer disc was derived from fitting ALMA velocity maps. They estimated two misalignment angles between the inner and outer discs, considering that, in the GRAVITY data, it is not possible to distinguish which side of the inner disc is closer to the observer: $\xi_{1}$ = 27 $\pm$ 9 deg, which is consistent with our result, and $\xi_{2}$ = 39 $\pm$ 9 deg. It is interesting to note that their PA and $i$ values, both for the outer and inner disc, are also in agreement with our PA and $i$ results.

### Radiative transfer predictions

Our relative orientation of $\xi$ = 21.4 $^{+6.7}_{-8.3}$ deg can be compared with the RT predictions for inner disc tilts presented in paper I. If we examine Figure 4 in paper I, we find that our 2019 $Q_{\phi}(H)$ observations are better reproduced by a misalignment of $\xi$ $\sim$ 20 deg, which is in excellent agreement with $\xi$ = 21.4 $^{+6.7}_{-8.3}$. On the other hand, a relative inclination of $\xi$ $\sim$ 30 deg better accounts for $Q_{\phi}(H)$ images from the 2016 data. Also, the azimuthal profiles for both epochs (Figure [6](#fig:2b-sphere)) are consistent with the RT predicted profiles in paper I (Fig. 7), for the aforementioned $\xi$ values. It is interesting to note that the difference in the relative inclinations between epochs also translates into variations in the location of the shadows and in the relative brightness of the arcs between the shadows. The RT predictions for $\xi$ = 20 deg result in broader decrements compared to the predictions for $\xi$ = 30 deg. These effects are also observed comparing the azimuthal profiles for both $Q_{\phi}(H)$ epochs in Fig. [6](#fig:2b-sphere), which implies a morphological variation, particularly, in the locations of the southern decrement and the western arc.

## Spectral index map

If due to shadowing, we would expect a drop in the dust temperature and optical depth in the location of the intensity decrements. In order to analyse this, we compute the spectral index map between 230 GHz and 350 GHz, as

$$\begin{align}
\alpha\,=\,\frac{\log(I_{230\,\mathrm{GHz}}/I_{350\,\mathrm{GHz}})}{\log(230\,\mathrm{GHz}/350\,\mathrm{GHz})},
\label{eq:specind}
\end{align}$$

and the error map as

$$\begin{align}
\sigma_{\alpha}\,=\,\frac{\sqrt{(\sigma_{230\,\mathrm{GHz}}/I_{230\,\mathrm{GHz}})^2 + (\sigma_{350\,\mathrm{GHz}}/I_{350\,\mathrm{GHz}})^2}}{\log(230\,\mathrm{GHz}/350\,\mathrm{GHz})}.
\label{eq:specinderror}
\end{align}$$

We smoothed the 230 GHz image to obtain the same synthesized (elongated) beam as that of a Briggs 2.0 weighting scheme for 350 GHz (84.9 mas $\times$ 69.9 mas), using the previously aligned images (Sec. [2.1](#sec:almadata)). It is interesting to note that the smoothed 230 GHz emission does not show dips as clear as the 350 GHz emission (Fig. [2](#fig:c-fig)). This could be due to the fact that the 350 GHz emission is more optically thick than the 230 GHz emission, thus, being sensitive to temperature only.

The $\alpha$ map was computed for intensities with errors $\sigma_{\alpha}$ \< 0.7, which translates into intensities greater than 0.27 mJy in Band 6 (14 $\sigma$) and 0.67 mJy in Band 7 (26 $\sigma$). Note that a calibration uncertainty of 2.5 $\%$ for Band 6 and 5 $\%$ for Band 7 (cite: alma_book) translates into a $\pm$ 0.13 uncertainty in the absolute value of $\alpha$ (using error propagation, such that $\sigma_{\alpha}$ = 0.056 / ln(350 GHz / 230 GHz), but the values in the error map in Fig. [12](#fig:4b-fig) do not consider this systematic errors since these are uniform across the map and we are mostly interested in relative changes.

![](figures/radial_specind_intensity_acotado.pdf)

In Fig. [13](#fig:specind), we find spectral index values $\alpha$ $\sim$ 2. The inner cavity (0.13 arcsec $<$ $r$ $<$ 0.25 arcsec, within the black intensity profiles in Fig. [13](#fig:specind)) shows $\alpha$ values much higher than $\sim$ 2, as also seen in Fig. [14](#fig:radial_specind). This suggests an optically thin emission due to the presence of very small grains, most likely as a consequence of grain destruction by stellar radiation. The $\alpha$ $\sim$ 2 values along the rest of the disc could either correspond to an optically thick emission, or suggest a shallow dust opacity index due to larger grains (cite: testi14). Furthermore, this is similar to the structure of HD 142527 in (cite: casassus15b) who reported a drop in the intensity of the outer disc using ATCA and ALMA observations from 34 GHz to 700 GHz. We do not find distinct azimuthal spectral variations in the location of the decrements, where $\alpha$ $\sim$ 2 suggests optically thick emission (Fig. [13](#fig:specind)), however, the dips in the infrared profile (Fig. [10](#fig:decrements)) point towards temperature decrements due to shadowing. We also calculated $\alpha$ $>$ $-$2 to be the lower limit for the star’s spectral index at 1$\sigma$ intensities for Bands 6 and 7.

It is particularly interesting that the spectral index values at 0.13 arcsec \< $r$ \< 0.25 arcsec are $\alpha$ $\sim$ 3.3, as seen in Fig. [14](#fig:radial_specind). This radial range corresponds to the inner cavity in Bands 6 and 7, where a faint dust pedestal can be observed at the edge of the inner cavity (Figs. [1](#fig:b-fig) and [2](#fig:c-fig)). The spectral index values in the inner cavity are typical for the interstellar medium (ISM), therefore, considering a dust opacity index $\beta$ = 1.7 (cite: draine2006), this can be interpreted as optically thin emission and a population of small dust grains (cite: sierra20) filling the cavity. This is consistent with the absence of intensity decrements in the inner cavity, which are smoothed out by optically thin thermal radiation from the dust pedestal. Also, it is intriguing that this high spectral index values are not seen towards $r$ = 0.5 arcsec (Fig. [14](#fig:radial_specind)), where we observe an extended dust halo outside of the radial dust trap in both Bands 6 and 7 (Figs. [1](#fig:b-fig) and [2](#fig:c-fig)). The $\alpha$ $\sim$2-2.5 along the dust halo implies the presence of larger dust grains compared to the inner cavity. However, further multi-wavelength data and modelling is required to resolve these ambiguities in DoAr 44.

## Disc gas mass estimates

The gas mass in discs is an important condition for the formation of planets, and in the case of shadowed transition discs, the cooling of the gas as it crosses the shadows can result on constraints on its mass. In this sense, (cite: casassus_2019_cooling) presented a 1D model that relates the outer disc surface density ($\Sigma_g$) to the depth of the temperature profiles ($T(\phi)$) due to radiation stemming from the central star and the inner disc. The model considers a shadow moving relative to the gas at a retrograde Keplerian speed, a fixed disc structure described by its radius ($R$) and thickness ($H$), and a standard dust population, with a maximum grain size ($a_{\mathrm{max}}$), the gas-to-dust mass ratio ($f_{\mathrm{gd}}$) and the grain filling factor ($f$). Hence, the free parameters governing the gas temperature are the observed angular shifts between the radio and IR decrements, $\eta_{\mathrm{shift}}$, and the gas surface density, $\Sigma_g$. Note that here we define $\eta_{\mathrm{shift}}$ on the plane of the disc, as opposed to paper I that defined $\eta_{\mathrm{shift}}$ on the plane of the sky.

In the case of DoAr 44, the observed angular shifts between the radio and IR decrements, described in Section [3.2](#sec:decrements), can be explained by a thermal lag between the shadowed dust and gas, provided that the outer disc has a retrograde direction of rotation. We computed the $T(\phi)$ profiles considering a maximum grain size of $a_{\mathrm{max}}$ = 1 cm, which is consistent with the optically thick $\alpha \sim$ 2 values we found for the outer disc (Figs. [13](#fig:specind) and [14](#fig:radial_specind)). We also use the established gas-to-dust mass gas ratio for the diffuse ISM, $f_{\mathrm{gd}}$ = 100, and a filling factor for compact grains $f$ = 1. These parameters are presented in Table [3](#tab:mass_parameters).

Figure [15](#fig:disc_mass) shows the resulting $T(\phi)$ profiles for different values of $\eta_{\mathrm{shift}}$ and $\Sigma_g$. The angular shift between the northern decrements is $\eta_{\mathrm{shift}}$ = 14.95 deg, which corresponds to an interpolated surface density of $\Sigma_g$ = 117 $\pm$ 10 g/cm$^2$, and the southern decrements have an angular shift of $\eta_{\mathrm{shift}}$ = 7.92 deg, which corresponds to an interpolated surface density of $\Sigma_g$ = 48 $\pm$ 10 g/cm$^2$. A lower value of $\Sigma_g$ means that the location of the southern dip is optically thinner to thermal radiation, which is consistent with the southern decrement being smoother and broader (as seen in Figure [9](#fig:3b-fig)), as a result of thermal diffusion for the considered disc rotation. The contrast ratio between the estimated intensity decrements along the outer ring gas surface density is $f_r$ = 2.4 $\pm$ 0.5, a value that is consistent with the presence of a large crescent of continuum sub-mm emission in the disc (cite: zhu_bauteau_16), as in, e.g., LkH$\alpha$330 (cite: isella13), HD 135344B (cite: vandermarel15) and MWC 758 (cite: casassus19_mwc758). Also, it is interesting to note that, in the context of a lopsided vortex, the southern decrement may correspond to significantly lower optical depths in the ALMA continuum. Yet the spectral index in the location of both decrements remains $\alpha \sim$2 (Fig. [13](#fig:specind)). If the southern decrement is optically thin, perhaps dust trapping in DoAr 44 is efficient only for the denser large grains, while a population of fluffy large grains would account for spectral index of the continuum halo and the southern decrement.

| Parameter | Value |
|:---|:--:|
| Angular shift between radio and IR dips ($\eta_{\mathrm{shift}}$) | north: 14.95 deg |
|  | south: 7.92 deg |
| Maximum grain size ($a_{\mathrm{max}}$) | 1 cm |
| Gas-to-dust mass ratio ($f_{\mathrm{gd}}$) | 100 |
| Filling factor ($f$) | 1 |

: Parameters for the disc mass calculation.

![](figures/fig_summary_DoAr44_C7.pdf)

# Conclusions

We report ALMA 350 GHz observations of DoAr 44 with a linear resolution of $\sim$10 au, as well as new differential polarised SPHERE/IRDIS observations. The new $Q_{\phi}(H)$ observations correspond to a 3-year time difference follow-up. These new data, along with a re-analysis of the ALMA 230 GHz continuum, allow us to reach the following conclusions:

- We found intensity dips in the resolved ALMA imaging of the radio continuum, confirming the predictions from paper I. The locations of the northern radio decrements in both 230 GHz and 350 GHz are fairly aligned, with position angles of 316.3 deg and 316.9 deg, east of north, respectively. The southern radio decrements, which seem broader, are both aligned at a position angle of 152.9 deg east of north.

- Provided a retrograde disc (rotating clockwise), the temperature decrements are leading in the direction of rotation relative to the $Q_{\phi}(H)$ decrements, by $\eta$ = 14.95 deg in the location of the northern dips and $\eta$ = 7.92 deg in the location of the southern dips.

- Geometrical models of $Q_{\phi}(H)$ provide support for a misaligned inner disc, with a relative inclination of $\xi$ = 21.4 $^{+6.7}_{-8.3}$ deg. The position angle joining both $Q_{\phi}(H)$ decrements results in a shift along the direction west of north, compared to previous observations presented in paper I. This is reflected in the morphological change in the location of the southern decrement, which also implies a variation in the orientation of the inner disc between the two $Q_{\phi}(H)$ epochs.

- The intensity dips may correspond to temperature decrements, since the spectral index map between 230 GHz and 350 GHz shows values $\alpha \sim$ 2 in the location of the shadows, which is consistent with optically thick emission.

- Disc gas mass estimates using the angular shifts between the radio and IR decrements, and for a standard dust population, give surface density values of $\Sigma_g$ = 117 $\pm$ 10 g/cm$^2$ for the northern decrement, and $\Sigma_g$ = 48 $\pm$ 10 g/cm$^2$ for the southern decrement. A lower value of $\Sigma_g$ is consistent with a broader and smoother temperature decrement in the south.

- The spectral index values $\alpha \sim$ 3.3 in the inner cavity, where we observe a faint mm-wavelength dust pedestal at the edge, are typical for the ISM and suggest optically thin emission due to the presence of smaller grains compared to the outer regions of the disc where $\alpha \sim$ 2.

- The outer continuum halo shows spectral index values of $\alpha \sim$ 2, which suggests the presence of fluffy large grains.

- The observed mm-wavelength outer dust halo shows spectral index values around $\alpha \sim$ 2, which can be interpreted as optically thick emission or as a shallow dust opacity index. Multi-wavelength data of DoAr 44 is required to further constrain the spectral index variations in the disc.

# Acknowledgments

We thank Prof. Dr. Hans Martin Schmid for constructive comments on the SPHERE observations. We thank the anonymous referee for helpful comments. The authors acknowledge financial support from ANID – Millennium Science Initiative Program – Center Code NCN2021_080. C.A-T acknowledges support from the Millennium Nucleus on Young Exoplanets and their Moons (YEMS). S.C. acknowledges support from Agencia Nacional de Investigación y Desarrollo de Chile (ANID) given by FONDECYT Regular grant 1211496, and ANID project Data Observatory Foundation DO210001. S.P. acknowledges support from FONDECYT Regular grant 1191934. P.W. acknowledges support from FONDECYT grant 3220399. L.C. acknowledges financial support from FONDECYT grant $\#$1211656. A.Z. acknowledges support from the FONDECYT Iniciación en investigación project number 11190837. SM is supported by a Royal Society University Research Fellowship (URF-R1-221669). This work used the Strelka cluster (FONDEQUIP project EQM140101) hosted at DAS/U. de Chile. This paper makes use of the following ALMA data: ADS/JAO.ALMA $\#$2018.1.00028.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Data Availability

The reduced ALMA and SPHERE data presented in this article are available upon reasonable request to the corresponding author. The original or else non-standard software packages underlying the analysis are available at the following URLs: MPolarMaps (<https://github.com/simoncasassus/MPolarMaps>, (cite: casassus21)), uvmem (<https://github.com/miguelcarcamov/gpuvmem>, (cite: carcamo18)), VisAlign (<https://github.com/simoncasassus/VisAlign>) and SNOW (<https://github.com/miguelcarcamov/snow>).

49 natexlab

(ref: andrews11) Andrews S. M., Wilner D. J., Espaillat C., Hughes A. M., Dullemond C. P., McClure M. K., Qi C., Brown J. M., 2011, The Astrophysical Journal, 732, 42

(ref: andrews09) Andrews S. M., Wilner D. J., Hughes A. M., Qi C., Dullemond C. P., 2009, ApJ, 700, 1502

(ref: antilen+23) Antilen J., Casassus S., Cieza L. A., González-Ruilova C., 2023, MNRAS, 522, 2611

(ref: avenhaus_2018_sphere) Avenhaus H. et al., 2018, The Astrophysical Journal, 863, 44

(ref: avenhaus14) Avenhaus H., Quanz S. P., Schmid H. M., Meyer M. R., Garufi A., Wolf S., Dominik C., 2014, ApJ, 781, 87

(ref: benisty17) Benisty M. et al., 2017, A&A, 597, A42

(ref: beuzit19) Beuzit J. L. et al., 2019, A&A, 631, A155

(ref: biller12) Biller B. et al., 2012, ApJL, 753, L38

(ref: bohn+22) Bohn A. J. et al., 2022, A&A, 658, A183

(ref: bouvier+20) Bouvier J. et al., 2020, A&A, 636, A108

(ref: carcamo18) Cárcamo M., Román P. E., Casassus S., Moral V., Rannou F. R., 2018, Astronomy and Computing, 22, 16

(ref: casassus18) Casassus S. et al., 2018, MNRAS, 477, 5104

(ref: casassus_22_selfcal) Casassus S., Cárcamo M., 2022, MNRAS, 513, 5790

(ref: casassus21) Casassus S. et al., 2021, MNRAS, 507, 3789

(ref: casassus19_mwc758) Casassus S. et al., 2019a, MNRAS, 483, 3278

(ref: casassus15) Casassus S. et al., 2015a, ApJ, 811, 92

(ref: casassus_2019_cooling) Casassus S., Pérez S., Osses A., Marino S., 2019b, MNRAS, 486, L58

(ref: casassus12) Casassus S., Perez M. S., Jordán A., Ménard F., Cuadra J., Schreiber M. R., Hales A. S., Ercolano B., 2012, ApJL, 754, L31

(ref: casassus15b) Casassus S. et al., 2015b, ApJ, 812, 126

(ref: cieza21) Cieza L. A. et al., 2021, MNRAS, 501, 2934

(ref: cieza19) Cieza L. A. et al., 2019, MNRAS, 482, 698

(ref: deboer2020) de Boer J. et al., 2020, A&A, 633, A63

(ref: dohlen08) Dohlen K. et al., 2008, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7014, Ground-based and Airborne Instrumentation for Astronomy II, p. 70143L

(ref: dong15) Dong R., Zhu Z., Whitney B., 2015, ApJ, 809, 93

(ref: draine2006) Draine B. T., 2006, ApJ, 636, 1114

(ref: Espaillat2010) Espaillat C. et al., 2010, The Astrophysical Journal, 717, 29

(ref: evans09) Evans, Neal J. I. et al., 2009, ApJS, 181, 321

(ref: fukagawa+2006) Fukagawa M., Tamura M., Itoh Y., Kudo T., Imaeda Y., Oasa Y., Hayashi S. S., Hayashi M., 2006, ApJL, 636, L153

(ref: gaia18) Gaia Collaboration et al., 2018, A&A, 616, A1

(ref: isella13) Isella A., Pérez L. M., Carpenter J. M., Ricci L., Andrews S., Rosenfeld K., 2013, ApJ, 775, 30

(ref: keppler20) Keppler M. et al., 2020, A&A, 639, A62

(ref: marino15) Marino S., Perez S., Casassus S., 2015, ApJL, 798, L44

(ref: casa) McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, Shaw R. A., Hill F., Bell D. J., eds., p. 127

(ref: min+17) Min M., Stolker T., Dominik C., Benisty M., 2017, A&A, 604, L10

(ref: padgett08) Padgett D. L. et al., 2008, ApJ, 672, 1013

(ref: perezL+2018) Pérez L. M. et al., 2018, ApJL, 869, L50

(ref: pinilla+18) Pinilla P. et al., 2018, ApJ, 868, 85

(ref: price18) Price D. J. et al., 2018, MNRAS, 477, 1270

(ref: alma_book) Remjian A. et al., 2019, ALMA Technical Handbook,ALMA Doc. 7.3, ver. 1.1. 2019

(ref: sierra20) Sierra A., Lizano S., 2020, ApJ, 892, 136

(ref: stolker+17) Stolker, T., Min, M., Stam, D. M., Mollière, P., Dominik, C., Waters, L. B. F. M., 2017, A&A, 607, A42

(ref: testi14) Testi L. et al., 2014, in Protostars and Planets VI, Beuther H., Klessen R. S., Dullemond C. P., Henning T., eds., p. 339

(ref: vandermarel16) van der Marel N., van Dishoeck E. F., Bruderer S., Andrews S. M., Pontoppidan K. M., Herczeg G. J., van Kempen T., Miotello A., 2016, A&A, 585, A58

(ref: vandermarel15) van der Marel N., van Dishoeck E. F., Bruderer S., Pérez L., Isella A., 2015, A&A, 579, A106

(ref: vanderplas+2019) van der Plas G. et al., 2019, A&A, 624, A33

(ref: VanHolstein2020A&A...633A..64V) van Holstein R. G. et al., 2020, A&A, 633, A64

(ref: williams19) Williams J. P., Cieza L., Hales A., Ansdell M., Ruiz-Rodriguez D., Casassus S., Perez S., Zurlo A., 2019, ApJL, 875, L9

(ref: zhu_bauteau_16) Zhu Z., Baruteau C., 2016, MNRAS, 458, 3918

(ref: zurlo20) Zurlo A. et al., 2020, MNRAS, 496, 5089

[^1]: E-mail: carla.atastro@gmail.com

[^2]: In the Planck or Rosseland sense.

</paper>

Write the methods card for this paper.