# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...987..142J\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...987..142J",
 "title": "A JWST/MIRI View of the Interstellar Medium in M83. I. Resolved Molecular Hydrogen Properties, Star Formation, and Feedback",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Jones, Logan H.",
 "n_authors": 14,
 "arxiv_id": "2410.09020",
 "doi": "10.3847/1538-4357/adce71",
 "alma_projects_linked_by_archive": [
  "2013.1.01161.S",
  "2022.1.00951.S"
 ]
}
```

Paper text:
<paper>
# A *JWST*/MIRI View of the ISM in M83: . Resolved Molecular Hydrogen Properties, Star Formation, and Feedback

## Abstract

We present a spatially-resolved ($\sim$3 pc pix$^{-1}$) analysis of the distribution, kinematics, and excitation of warm H$_2$ gas in the nuclear starburst region of M83. Our *JWST*/MIRI IFU spectroscopy reveals a clumpy reservoir of warm H$_2$ ($>$200 K) with a mass of $\sim 2.3 \times 10^5$ $M_{\odot}$ in the area covered by all four MRS channels. We additionally use the \[Ne ii\] 12.8 $\mu$m and \[Ne iii\] 15.5 $\mu$m lines as tracers of the star formation rate, ionizing radiation hardness, and kinematics of the ionized ISM, finding tantalizing connections to the H$_2$ properties and to the ages of the underlying stellar populations. Finally, qualitative comparisons to the trove of public, high-spatial-resolution multiwavelength data available on M83 shows that our MRS spectroscopy potentially traces all stages of the process of creating massive star clusters, from the embedded proto-cluster phase through the dispersion of ISM from stellar feedback.

# Introduction

Since ongoing or imminent star formation primarily takes place in molecular clouds, scaling relations have been in use for decades (cite: Kennicutt98; Bigiel08; Bethermin23) to tie the star formation rate (SFR) to the mass of cold H$_2$ gas in galaxies on both integrated and resolved scales. Once massive stars form and evolve, that same H$_2$ gas is heated through a combination of far-ultraviolet (FUV) pumping and shocks from winds or supernovae, leading to strong emission from transitions in the mid-infrared (cite: Appleton06; Donnan23). In other words, precise measurements of the mass and excitation state of H$_2$ in galaxies – especially at small scales relevant to cloud evolution and star formation – are directly linked to both past and future generations of galaxy growth. However, because H$_2$ molecules lack a permanent dipole moment, only much weaker quadrupole (ro-vibrational) transitions are permitted, with allowed upper energy states starting at $E / k$ = 510 K.

Central bursts of star formation (SF) in massive galaxies are excellent laboratories for understanding the interwoven connections between H$_2$ gas, SF, and feedback episodes and their impact on the evolution of galaxies. The *Spitzer* era of space-based infrared astronomy revealed a rich suite of spectroscopic features to diagnose the physical state of the interstellar medium (ISM) in SF galaxies – for example, emission from polycyclic aromatic hydrocarbon (PAH) grains (cite: Maragkoudakis18), or line emission from shocked and/or photoionized atomic and molecular gas (cite: Inami13). With an order of magnitude improvement in sensitivity and in spatial and spectral resolution, the advent of the Medium Resolution Spectrometer (MRS) on *JWST*/MIRI has further broadened the diagnostic space for understanding SF and feedback at previously unattainable scales (cite: Young23; Bik24; Rigo24).

As the nearest face-on spiral galaxy with a nuclear starburst ($D$ = 4.6 Mpc, (cite: Saha06)), M83 has been studied extensively across the electromagnetic spectrum, including the X-ray (cite: Hunt21; Wang21), UV (cite: Thilker05; James14; Hernandez21), optical and near-IR (cite: Mast06; Knapen10; Winkler23), and millimeter to radio (cite: Russell20; Koda23) regimes. Additionally, the nucleus and part of the disk of M83 was recently observed with wide- and medium-band filters from *JWST*/NIRCam and *JWST*/MIRI as part of the FEAST program (GO 1783, PI A. Adamo; Adamo et al., in prep.), which provide unprecedented views of the bulk stellar populations, sites of embedded SF, and diffuse emission from PAHs. Finally, M83 contains numerous young, massive star clusters (YMCs) with archival FUV spectroscopy from *HST*/COS. The COS spectra provide direct constraints on the intensity and hardness of the ambient ionizing radiation field and of the amount of mechanical feedback from stellar winds (via, e.g. CIV $\lambda\lambda$ 1549,1551 Å), each of which acts to regulate the excitation of nearby molecular clouds.

In (cite: Hernandez23) (hereafter H23), we reported top-level results from *JWST* GO program 02219 (PI S. Hernandez), in which we investigated the spatially-integrated spectral properties of our four MRS pointings covering the central $\sim$200$\times$200 pc$^2$ of M83’s nuclear region, including the optical nucleus. These spectra provided insights into the ISM conditions of M83’s center at the scale of $\sim$100 pc, as well as how they vary from region to region. In this work, we return to the same dataset to inspect the properties of the warm H$_2$ gas at the level of individual spaxels (0.13$''$ or $\sim$3 pc). The high spatial resolution and sensitivity of these data allows us to search for quantitative and qualitative changes in the gas properties of the molecular and ionized gas with respect to the location of the optical nucleus and (un)obscured YMCs.

We structure this paper as follows. In Section [2](#sec:obs), we describe the observations and data reduction steps. In Section [3](#sec:methods), we outline the spectral fitting tools and procedures we use to fit our IFU data on a spaxel-by-spaxel basis, followed by a summary in Section [4](#sec:analysis) of our methods for determining H$_2$ excitation, SFR, and other physical properties. We put our findings for the warm H$_2$ content into a broader multiwavelength context in Section [5](#sec:disc), including a qualitative discussion of the different stages of stellar feedback and ISM clearing that M83 displays in its nuclear region.

# Observations

We use the MIRI/MRS observations from program GO 02219 (PI: Hernandez), which were obtained between 2022 July 5 – 9. The raw MIRI/MRS files were retrieved from the Mikulski Archive for Space Telescopes (MAST); all JWST data used in this paper can be found in MAST:10.17909/a61h-f081. Additional details on the observation strategy are given in H23, though we summarize the most important points below.

The primary MRS observations consist of four pointings in a 2 $\times$ 2 mosaic, with a 4-point dither pattern applied to each pointing to achieve optimal sampling throughout the MRS field-of-view (FOV) and to mitigate detector artifacts. This results in contiguous spatial coverage across the mosaic in MRS channels 3 and 4 but not channels 1 and 2. The specific pointings (labelled as Regions 1, 2, 3, and 4 in the left panel of Figure [1](#fig:convolution) and in select figures thereafter) were strategically chosen to provide full spatial coverage of the YMCs in all four MRS channels, with the FOV per pointing increasing from 3.2$''$ $\times$ 3.7$''$ in Channel 1 (4.9 – 7.65 $\mu$m) to 6.6$''$ $\times$ 7.7$''$ in Channel 4 (17.7 – 27.9 $\mu$m). The observations were obtained over three visits, with one visit each dedicated to observing with the SHORT (A), MEDIUM (B), and LONG (C) gratings. The total integration time per pointing+grating was 2264 s.

![](figures/convolution.pdf)

Due to the extended nature of M83’s nuclear region, we required a dedicated sky observation to accurately measure and correct for the thermal background. We thus also obtained a background pointing with MRS along a sightline well off the disk of M83, with integration times equal to those of the primary pointings. All MRS observations were reduced with the standard *JWST* pipeline (version 1.10.2), with the spatial pixels gridded to a common scale of 0.13$''$ pix$^{-1}$ and the output type set to `multi` in the Spec3 pipeline to automate the spectral stitching between bands/channels. We also applied residual fringe corrections available in the *JWST* pipeline to both the three- dimensional and one-dimensional observations, though as we discuss below, significant fringing is present at the longest wavelengths even with these corrections.

In the course of reducing and analyzing these data, we also noted significant discontinuities in the continua of some individual spaxel spectra. These discontinuities are most prominent in the Channel 4 data and occur approximately at the wavelengths where the spectral coverage begins or ends for the 4A, 4B, and 4C bands, which we attribute to issues with flux calibration across bands within the MRS pipeline. These artificial breaks in the continuum flux are often severe enough to affect the quality of our fits to the warm dust continuum at $\lambda_0 \gtrsim 20$ $\mu$m (see Section [3](#sec:methods)), which in turn complicated our emission line extraction and fitting. We opted to truncate the wavelength axis of our combined data cube at 20.68 $\mu$m (the blue limit of band 4B) to mitigate the impact of the discontinuities on our full spectral fitting. For this work, we also restrict ourselves only to the parts of our IFU data cube covered by MRS channel 1 (the smallest FOV of the four channels) to ensure contiguous spectral coverage down to $\sim$5 $\mu$m.

Finally, we spatially smoothed our data cube to a common resolution of 0.788$''$ FWHM ($\sim$18 pc at $D = 4.6 Mpc$), which is the PSF FWHM of MRS at our long-wavelength cutoff of 20.68 $\mu$m (see Equation 1 of (cite: Law23)). For each wavelength slice in the IFU cube, we determine the quadrature difference between the PSF FWHM at 20.68 $\mu$m and the nominal PSF FWHM at that wavelength (again according to Equation 1 of (cite: Law23)), and then convolve the slice with a 2D Gaussian with the corresponding width, $\sigma = \sqrt{\sigma_{20.68}^{2} - \sigma_{\lambda}^{2}}$. We show an example of this process in Figure [1](#fig:convolution).

# Methods

## PAHs, Dust Continuum, and Attenuation

![image](figures/spaxspec_94_42_fitfigure_wlabel.png) ![image](figures/spaxspec_64_95_fitfigure_wlabel.png)

![](figures/wrmtau_wspax.pdf)

We use the Continuum and Feature Extraction software (`CAFE`; (cite: cafe); Diaz-Santos et al., in prep.)[^1] to model PAH features, dust continuum emission, and extinction in our spaxel spectra. We began by assuming a systemic redshift of $z$ = 0.001733 (cite: MeyerHipass) to shift our MRS cube into the approximate rest frame for fitting with `CAFE`. We used a modified version of the MIRI-optimized starburst parameter file in `CAFE`, which models the mid-IR continuum as the sum of reprocessed dust continua and “starburst" continua. The stellar model consists of a mixture of 2, 10, and 100 Myr-old single stellar population (SSP) templates from Starburst99 (cite: starburst99). However, we note that only $\sim$half of spaxels (mostly concentrated near the optical nucleus and generally dust-free areas in Regions 3 and 4) ultimately include a non-zero stellar component in their best-fit `CAFE` model, with the 10 Myr component dominant.

Our primary dust model includes emission and absorption from cool (40 – 100 K) and warm (100 – 400 K) dust and assumes a screen geometry. However, we found that the two-component dust model produced physically implausible fits (i.e., optical depths $\gtrsim$10 at 14 $\mu$m) for some highly-obscured areas in Region 2 whose continuum spectra were dominated by emission from cool dust. For these $\sim$70 spaxels, we instead fitted the spectra with a single dust component with temperatures between 40 – 100 K. Finally, we assume a Galactic interstellar radiation field as the illuminating source for all model dust components.

Individual PAH features (drawn from a feature library included in `CAFE`) were fitted with Drude profiles. We allow the centroid of the Drude profiles to vary by up to 500 km s$^{-1}$, which is sufficient to account for (1) uncertainties in the MIRI/MRS wavelength calibration (cite: Rigby23) and (2) velocity shifts due to the kinematics of the PAH-bearing ISM in M83. We also allow the width of each component to vary by up to $\pm$20% of their default value in `CAFE`. We did not fit emission lines simultaneously with PAHs and mid-IR continua for the sake of computational efficiency, as this would have nearly tripled the number of fittable model parameters for a single spaxel, and instead perform our own line fitting after subtracting the best-fit dust+PAH model as described in the next section. Finally, we assumed the (cite: Ossenkopf92) extinction curve, which includes strong silicate absorption features at 9.7 and 18 $\mu$m.

We show representative spaxel spectra and `CAFE` fits in Figure [2](#fig:cafefits), which illustrate the diversity of dust properties in our data. The left panel shows a spectrum toward the mildly-obscured optical nucleus (($\alpha$, $\delta$) = (13:17:0.887, -29:51:55.921) as measured from our MRS data), while the right panel shows a spectrum toward a UV-bright star cluster with partially-cleared foreground ISM. `CAFE` produces acceptable model fits across the wavelength range we consider in this work (with residuals of $\pm$5% in line-free regions), with the exception of the highly structured PAH complexes at 6 – 6.6 and 11 – 13 $\mu$m, where the fitting algorithm sometimes fails to identify weak features hidden in the broad wings of more dominant PAH features. Finally, we note that the fractional attenuation (dotted grey curve) experienced by PAH features and emission lines can be significant, even in the mid-IR. For the nuclear spaxel spectrum, for example, roughly 10% of the light at 15 $\mu$m is attenuated; this increases to 30% at 10 $\mu$m, driven by the deep silicate absorption feature at 9.7 $\mu$m.

In Figure [3](#fig:cafetau), we show the spatial distribution of the optical depth due to warm dust at 14 $\mu$m, $\tau_{warm}$, as inferred by `CAFE` across the FOV of our MRS cube. Although the median optical depth across our FOV is fairly low ($\tau_{warm} \sim$ 0.64), we note regions where the dust is optically thick ($\tau_{warm} \gtrsim$ 1), particularly in Regions 1 and 2. Because the amount of attenuation experienced by PAHs and emission lines in `CAFE` is tied to the optical depth of warm dust, this means that all line fluxes in these regions will be boosted by up to $\sim$40%.

## Emission Line Maps

After obtaining reliable PAH+continuum models and attenuation estimates across the FOV of our combined cube using the fitting procedure outlined above, we turn to the fitting of emission lines. We perform a local continuum fitting and subtraction in the vicinity of the lines analyzed in this work. We then use `specutils` to fit a single Gaussian to each of the H$_2$ transitions listed in Table [1](#tab:emlist). We also perform single and double Gaussian fits to the \[Ne ii\] 12.81 $\mu$m and \[Ne iii\] 15.56 $\mu$m lines (see Section [4.3](#subsec:analysis:sfr), which we use as an SFR diagnostic and approximate tracer of the hardness of the ambient UV field). All fits were allowed to vary independently (i.e., the kinematics of the H$_2$ lines are not tied). We integrate over the best-fit Gaussian profile to obtain total line or line component fluxes in units of erg s$^{-1}$ cm$^{-2}$.

We note that a small but significant number of spaxels (particularly those near the edge of the Ch1 FOV) have no data in certain narrow wavelength intervals, most of which lie below 8 $\mu$m; we attribute this to a combination of the dither pattern and the spectral stitching routines in the MRS pipeline, which results in edge spaxels having sporadic wavelength coverage when combining our data into a single cube. Unfortunately, these missing wavelength intervals frequently overlap with the expected positions of the S(5) – S(8) transitions of H$_2$, which limits the number of transitions that go into our H$_2$ excitation modeling near the edge of the Ch1 FOV.

We estimate the significance of a line detection by estimating the noise in a nearby, line-free region of the continuum-subtracted spectra, in a manner similar to that used in (cite: DelPino23). Specifically, we measure the RMS flux density in 0.03 $\mu$m-wide windows in the pseudo-continuum around each line, then multiply this value by 2$\times$ the FWHM of the line as an estimate of the amount of “signal" that would be present in the absence of any line emission. Unless otherwise specified, we adopt a threshold of S/N $>3$ for all lines and line components, in line with other emission-line studies (cite: Mingozzi22).

Finally, we correct all line fluxes and uncertainty estimates using the wavelength-dependent attenuation fraction inferred by `CAFE` for each spaxel, shown as a dotted-grey line in Figure [2](#fig:cafefits). In other words, at the rest-frame wavelength of each line, we extract the value $A$ of the grey curve (cite: Ossenkopf92) and multiply the observed flux and flux uncertainty by (1/$A$) to recover the intrinsic, de-reddened line flux without artificially inflating its S/N.

|                       |      |             |           |
|:---------------------:|:----:|:-----------:|:---------:|
|      Transition       | Name | $\lambda_0$ | $E_u / k$ |
|      ($\nu = 0$)      |      |  ($\mu$m)   |   \(K\)   |
| $J = 9 \rightarrow$ 7 | S(7) |   5.5115    |   7197    |
| $J = 8 \rightarrow$ 6 | S(6) |   6.1088    |   4830    |
| $J = 7 \rightarrow$ 5 | S(5) |   6.9095    |   4586    |
| $J = 6 \rightarrow$ 4 | S(4) |   8.0250    |   3475    |
| $J = 5 \rightarrow$ 3 | S(3) |   9.6649    |   2504    |
| $J = 4 \rightarrow$ 2 | S(2) |   12.2786   |   1682    |
| $J = 3 \rightarrow$ 1 | S(1) |   17.0348   |   1015    |

:  List of H$_2$ Rotational Transitions

# Analysis

We show maps of the attenuation-corrected flux, gas velocity, and line FWHM for the S(1), S(3), S(5), and S(7) rotational H$_2$ lines in Figure [4](#fig:h2vis). Velocity maps are shown with respect to the systemic redshift, $z$ = 0.001733, corresponding to a recession velocity of 519 km s$^{-1}$ (cite: MeyerHipass). Line FWHMs have been corrected for instrumental broadening, using Equation 1 of (cite: OJones23) to determine the spectral resolution at the wavelength of each line except for S(1). Their Equation 1 underestimates the observed resolving power of MRS at $\sim$15 – 17 $\mu$m (see their Figure 5 and the *JWST* user documentation[^2]), leading us to adopt $R$ = 3300 for the S(1) transition and other lines in this wavelength interval.

The flux and kinematic maps of these transitions show generally similar structures, with prominent H$_2$ line emission from the optical nucleus (cross symbol in Figure [4](#fig:h2vis) and thereafter), highly-extincted knots in Region 2, and other clumps centered around a string of UV-bright YMCs in Region 4. However, we note that higher-excitation lines are stronger (relative to S(1)) in the optical nucleus and weak or undetected in much of Regions 3 and 4. The lines are generally resolved (corrected FWHMs $\gtrsim$30 km s$^{-1}$) across much of our FOV, with some filamentary or clumpy structures reaching up to FWHM $\sim$140 km s$^{-1}$. We note that the portions of Region 3 which are undetected in higher-excitation lines are coincident with one such patch of highly dispersed gas, as observed in the lower-excitation lines. We also identify a kinematically distinct point source in Region 2, the position of which is marked with a circle in the first and final rows of Figure [4](#fig:h2vis). We further discuss the possible nature of this object in Section [5.3](#subsec:disc:baby), though we note that it is *only* detected robustly in the flux and kinematics of S(1) and weakly in S(2). No such structure is seen at this position in \[Ne ii\], \[Ne iii\], or other H$_2$ lines.

## H$_2$ Excitation Modeling

![](figures/oddJ_H2maps.pdf)

To obtain an estimate of the warm H$_2$ mass per spaxel, we use the H$_2$ excitation model of (cite: Togi16) (hereafter TS16). In brief, the model assumes that the rotational temperatures of H$_2$ gas follow a power-law distribution $dN = mT^{-n}dT$ for column density $N$, temperture $T$, and a constant $m$. Given the analytical expressions in TS16 for $m$ and other relevant quantities (e.g., column density of H$_2$ molecules in the upper energy level $j$ $N_j$), the model parameters that must be constrained by the data are the slope $n$ and the upper and lower bounds of the temperature distribution $T_u$ and $T_l$. TS16 find that the model fit quality and inferred H$_2$ mass become insensitive to the choice of $T_u$ at temperatures above 2000 K and thus assume a fixed $T_u$ = 2000 K, which we also adopt in this work. $n$ and $T_l$ can then be constrained directly from the data by minimizing the difference between the *observed* values of $N_j$ (which are tied to the line fluxes) and the *predicted* values of $N_j$ for some $n$ and $T_l$. Both the observed and predicted columns are normalized to the S(1) line for the fitting procedure.

For this work we created a Python adaptation of the TS16 model, which we release for community use[^3]. Our Python version yields best-fit values of $n$, $T_l$, and H$_2$ masses $M (T > T_l)$ that are identical to the original implementation in IDL to within $< 1\%$, which we confirm through tests using the TS16 sample. Parameter uncertainties on $n$ and $T_l$ are slightly higher in our Python implementation, which we attribute to the choice of minimization algorithm (the Levenberg-Marquardt algorithm in IDL vs. the Trust Region Reflective algorithm in `scipy`’s `curve_fit` function).

We show the map of best-fit slopes $n$ in Figure [5](#fig:h2slopes). For the remainder of our resolved H$_2$ analysis, we consider only those pixels with four or more H$_2$ line detections and with relative error $\delta n / n < 25\%$ to mitigate the impact of poor power-law fits on our total H$_2$ mass estimates. This mostly affects pixels along the FOV edges and the corners of Region 3, which is generally very faint or undetected in H$_2$ transitions beyond S(3), as seen in Figure [4](#fig:h2vis). The median slope and 1$\sigma$ range across our FOV, $n = 5.75 \pm 0.64$,

reaches the upper end of the 3.79 $< n <$ 6.39 range reported in TS16 for their sample of SINGS galaxies and is somewhat steeper than (but consistent with) their sample mean of $n = 4.84 \pm 0.61$. This indicates, on average, relatively little H$_2$ in highly excited states across our four regions in M83, though with significant variation. We note quite shallow slopes (i.e., relatively high H$_2$ excitation) are clustered near the optical nucleus and the clumps or strings of UV-bright star clusters in Regions 2 and 4, while the steepest slopes are concentrated in Region 3. We also find that the best-fit values of $T_l$ across our FOV vary from $\sim$130 – 343 K (median 247 K), with the lowest values of $T_l$ coincident with CO-bright knots in Region 2 (see the discussion in Section [5](#sec:disc)) and the highest found near the optical nucleus.

![image](figures/h2_slope_dered.pdf) ![image](figures/h2_TL.pdf)

## Warm H$_2$ Mass Estimates

With the power-law H$_2$ temperature distribution thus constrained, we can then use Equations 9 and 14 in TS16 to derive total H$_2$ column densities and masses per spaxel. However, while the slope of the temperature distribution in each spaxel is reasonably well-constrained by the data, there remain several justifiable choices for the lower temperature bound $T_{l}^{'}$ for the column integral. Since the bulk of the cold, imminently star-forming H$_2$ cannot be probed through rotational emission, it is natural to wonder if extrapolation of the power-law model to lower temperatures will produce physically sensible results. A proper choice for $T_{l}^{'}$ is particularly critical for our data given the steep slopes we measure in some areas, as extrapolating to lower and lower values of $T_{l}^{'}$ may cause the total inferred H$_2$ mass to balloon beyond what is inferred through CO and other tracers.

![image](figures/h2_mass_200_dered.pdf) ![image](figures/h2_mass_80_dered.pdf)

Using the best-fit power-law slopes per spaxel, we therefore construct three different maps of the H$_2$ mass distribution, each with a different definition of $T_{l}^{'}$:

1.  $T_{l}^{'}$ is set equal to the best-fit $T_l$ for each spaxel. This approach provides an estimate of the *warm* H$_2$ that is the most directly constrained by the data.

2.  $T_{l}^{'}$ is fixed at 200 K across the FOV, which imposes a modest extrapolation of the temperature distribution for most spaxels but provides a more uniform estimate of the warm H$_2$ than (1).

3.  $T_{l}^{'}$ is fixed at 80 K across the FOV, which is a typical temperature below which the H$_2$ reservoir can change in mass without measurable changes to the rotational line fluxes in the *Spitzer*/IRS spectroscopy analyzed in TS16.

Unless otherwise specified, we propagate only the uncertainty on $n$ (and not $T_l$) to the gas mass estimates. Adopting the first two definitions of $T_{l}^{'}$, the warm H$_2$ mass across our FOV ranges between (1) $1.50^{+0.09}_{-0.09} \times 10^5 M_{\odot}$ for a variable $T_{l}^{'}$ and (2) $2.26^{+0.17}_{-0.19} \times 10^5 M_{\odot}$ for $T_{l}^{'}$ = 200 K. Adopting the third definition with $T_{l}^{'}$ = 80 K, which taps into the cooler gas, yields (3) $7.93^{+3.52}_{-2.59} \times 10^6 M_{\odot}$. In Figure [6](#fig:h2_warmmass), we show the mass per 0.13$''$ spaxel inferred using definitions (2) and (3) – in other words, maps of the warm and cool+warm H$_2$ gas over our FOV.

We note that this work is one of the first uses of the TS16 model on the $\lesssim$5 pc scale, compared to the $\sim$kpc-scale regions probed by *Spitzer*/IRS in the sample analyzed in TS16. Even in the era of *JWST*, other recent works that follow TS16 to model H$_2$ masses and excitation from MRS spectroscopy only probe down to scales $\sim$100 pc (cite: Lai22; Armus23; Zhang23; Costa24). To assess the importance of physical scale on the derived mass estimates, we applied `CAFE` and our custom line-fitting procedure to the integrated-light spectrum (created through the coaddition of every spaxel in our common FOV, which approximates the total spectrum of the central 200$\times$200 pc$^2$ of M83).

![](figures/Neon2.pdf)

The observed and attenuation-corrected fluxes of the S(1) – S(7) transitions in the integrated spectrum are consistent within 5 - 10% of the sum of the corresponding line fluxes from the spaxel-by-spaxel fits, with the greatest discrepancies occurring for the de-attenuated S(1) and S(3) fluxes. We attribute this to the modest attenuation ($\tau_{warm}$ = 0.49) inferred by `CAFE` in our integrated spectrum, which is slightly lower than the median value of $\tau_{warm}$ = 0.60 for our resolved analysis as shown in Figure [3](#fig:cafetau).

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Analysis | $T_{l}^{'}$ | $M_{H2}(T >$ $T_{l}^{'}$) | $F_{CO}$ |
|  | \(K\) | ($M_{\odot}$) | (%) |
| Resolved | Model $T_l$ | $1.50^{+0.09}_{-0.09} \times 10^5$ | $0.89^{+0.03}_{-0.07}$ |
|  | 200 | $2.26^{+0.17}_{-0.19} \times 10^5$ | $1.32^{+0.10}_{-0.11}$ |
|  | 80 | $7.93^{+3.52}_{-2.59} \times 10^6$ | $46.2^{+20.5}_{-15.1}$ |
|  | 50 | $8.17^{+8.67}_{-4.04} \times 10^7$ | $476^{+506}_{-235}$ |
| Integrated | Model $T_l$ | $1.54^{+0.06}_{-0.07} \times 10^5$ | $0.90^{+0.04}_{-0.04}$ |
|  | 200 | $1.84^{+0.09}_{-0.09} \times 10^5$ | $1.07^{+0.05}_{-0.05}$ |
|  | 80 | $4.47^{+0.98}_{-0.84} \times 10^6$ | $26.1^{+5.72}_{-4.91}$ |
|  | 50 | $3.05^{+1.14}_{-0.86} \times 10^7$ | $178^{+66.7}_{-49.9}$ |

:  Model H$_2$ Masses for M83’s Nuclear Region

Additionally, while the best-fit value of $T_l$ (215.2 $\pm$ 26.2 K) is roughly consistent with the median $T_l$ value from the spaxel-level analysis, the power-law slope $n$ = 5.10 $\pm$ 0.26 is slightly lower (i.e., shallower) than the median slope in our resolved analysis, though still consistent within the uncertainties. Again adopting each of our three definitions of $T_{l}^{'}$, the H$_2$ mass we infer from the integrated spectrum are (1) $1.54^{+0.06}_{-0.07} \times 10^5 M_{\odot}$ for $T_{l}^{'}$ = 215.2 K; (2) $1.84^{+0.09}_{-0.09} \times 10^5 M_{\odot}$ for $T_{l}^{'}$ = 200 K; and (3) $4.47^{+0.98}_{-0.84} \times 10^6 M_{\odot}$ for $T_{l}^{'}$ = 80 K.

When adopting definition (1), the warm H$_2$ mass estimates in our integrated and resolve-then-sum analyses are in excellent agreement with one another, as expected. However, in the temperature regimes considered under definitions (2) and (3), the H$_2$ masses estimated from our integrated spectrum are at best only marginally consistent within uncertainties with those from our resolved analysis. The systematically lower masses in the integrated case can be attributed to the slight differences in typical power-law slope, which can greatly affect the inferred amount of cool/cold gas as we extend to lower and lower values of $T_{l}^{'}$. Together with the different degrees of attenuation inferred for integrated and spaxel-level data, this hints at a scenario where the inferred H$_2$ mass and excitation depends on the physical scale probed, at least within the framework of the TS16 model. We summarize the various estimates of $M_{H2}$($T >$ $T_{l}^{'}$) and their uncertainties in Table [2](#tab:masslist).

## Star Formation Rates

As described in Section [3.2](#subsec:methods:emlines), we performed single and double Gaussian fits to the \[Ne ii\] 12.81 $\mu$m and \[Ne iii\] 15.56 $\mu$m lines. To determine whether to use the single or two-component fits for a given line in each spectrum, we compare the reduced-$\chi^2$ of the two fits in a statistical $F$-test, following (cite: Westmoquette07). In essence, we adopt the two-component fit if the reduced-$\chi^2$ is lowered by a factor of at least 3.289 compared to the one-component fit, corresponding to a significance level $\alpha = 0.10$; otherwise, we default to the one-component fit. Only after application of the $F$-test do we then apply our detection threshold of S/N $>$ 3, since our definition of noise depends on the fitted FWHM of the line or line component.

![image](figures/ne3_ne2_map.pdf)\
![image](figures/sfr_z19.pdf)

The bright \[Ne ii\] line is better modeled with a two-component fit across nearly all of our FOV (see Figure [7](#fig:neon_maps)), indicating a ubiquitous ISM component that is kinematically distinct from gas near Hii regions. The secondary component contributes $\sim$23% of the total \[Ne ii\] line flux on average in our FOV. The need for a second component in \[Ne iii\] is less uniformly evident, with our $F$-test favoring a single Gaussian fit across large swathes of all four regions.

However, we note that for \[Ne iii\] spectra which do not “pass" the $F$-test, the FWHM of the single-Gaussian fits are slightly but systematically larger (by 20 – 60 km s$^{-1}$) than the FWHM of the primary component in the corresponding double-Gaussian fit. This suggests that there may be a broad component that is strong enough to affect the wings of the \[Ne iii\] line profile, but is unable to be detected by the $F$-test at a reasonable statistical significance. We show the results of both our single-Gaussian and double-Gaussian fitting to \[Ne iii\] in Appendix [7](#sec:appendix) (Figure [12](#fig:appendix:neon3)).

We additionally show the flux ratio of the primary/narrow components of \[Ne iii\] to \[Ne ii\] in the upper panel of Figure [8](#fig:neonSFR). We find that the neon emission is predominantly from the singly-ionized state across our FOV with the exception of two compact regions in Region 1, where \[Ne iii\] and \[Ne ii\] are of roughly equal strength. One of these areas corresponds to the location of the optical nucleus, while the other has an unclear origin. Though shocks may be partly responsible for the elevated \[Ne iii\] abundance, the nearest catalogued supernova remnant (cite: Winkler23) is 1.4$''$ (33 pc projected) away.

Finally, we use our $F$-test and S/N-filtered line luminosity maps to derive SFRs per spaxel using the relation presented in (cite: Zhuang19). Their relation is similar to that given in (cite: Ho07) but with an explicit dependence on metallicity, which affects the neon abundance and the shape of the incident ionizing spectrum. (cite: Zhuang19) also provide prescriptions for determining the fraction of neon in the first and second ionization states, $f_+$ and $f_{+2}$, directly from the \[Ne iii\]/\[Ne ii\] line ratio. We use the extinction-corrected line luminosities and an assumed gas-phase metallicity of $Z = 2\times Z_{\odot}$ (cite: Hernandez21) to derive SFRs using the (cite: Zhuang19) relation. Converting the spaxel size (0.13$''$) to kpc at the distance of M83 (cite: Saha06), we create a map of the SFR surface density $\Sigma_{SFR}$ in $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$, shown in the lower panel of Figure [8](#fig:neonSFR). The SFR densities in Region 2 are fairly high, reaching $\Sigma_{SFR}$ $\sim$75 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ near a grouping of very young (see Section [5.4](#subsec:disc:stararc)) UV-bright star clusters, and rapidly decrease as the eye moves clockwise through Regions 4, 3, and 1, with SFR densities as low as $\sim$1 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$.

We note the (cite: Zhuang19) prescriptions were calibrated using Starburst99 SSP models (cite: starburst99) only up to ages of 2.5 Myr, while the stellar populations in our field span ages up to $\gtrsim$10 Myr. The star cluster ages ($\lesssim$3 Myr) we estimate from archival *HST*/COS spectroscopy in Regions 2 and 4 (see Section [5.4](#subsec:disc:stararc)) are roughly consistent with this calibration. Slightly older stellar populations are mainly seen in Region 3 (e.g., 8.6 Myr in the photometric analysis from (cite: Knapen10)). This area is where we see the faintest \[Ne ii\] and \[Ne iii\] emission, consistent with a low instantaneous SFR despite being outside the age calibration of the (cite: Zhuang19) relations.

# Discussion

## Molecular Gas Contents of M83’s Nuclear Region

Historically, attempts to quantify the amount and distribution of molecular gas in M83 (cite: Hirota18; Koda23) and SF galaxies more generally (cite: Bolatto13; Pavesi18; Leroy21) have relied on observations of CO (and other, less abundant tracers – e.g., OH; (cite: Xu16)) which, unlike H$_2$, have a nonzero dipole moment and hence are strong rotational emitters. CO-based molecular gas measurements usually require an assumed value for the factor $\alpha_{\mathrm{CO}}$ to convert between the intensity of CO emission and H$_2$ mass surface density, although the value of $\alpha_{\mathrm{CO}}$ can vary significantly with time, environment, and metallicity, even within individual galaxies (cite: Sandstrom13; Hu22; Chiang24; Lee24).

Our use of the TS16 model, in principle, allows us to extract estimates of the total molecular gas mass across our FOV in addition to only the warm ($T > 200$ K) H$_2$. TS16 distinguishes between the lower temperature bound for the power-law model $T_l$ and the sensitivity temperature $T_s$, or the temperature below which an increase in the H$_2$ mass results in no measurable change to the line fluxes or excitation, which they determine following (cite: Avni76) by evaluating their model over a grid of $n$ and $T_l$ values and examining the change in $\chi^2$ relative to its minimum value, $\Delta\chi^2$. For the *Spitzer*/IRS spectra they considered in that work, only a handful of galaxies (primarily LINER and Seyfert hosts) showed evidence for a well-defined minimum in $\Delta\chi^2$, such that extrapolating the power-law model for those galaxies to temperatures less than $\sim$120 K results in a poorer fit. They interpret this as evidence for a warm gas excess in these sources, such that the majority of H$_2$ is directly detected via the mid-IR rotational transitions. Most galaxies in their sample have no well-defined minimum in $\Delta\chi^2$ space, meaning that any $T_l < T_s$ remains consistent with the observed line ratios; their sample average is $T_s$ = 81 K.

For completeness, we performed the same $\Delta\chi^2$ evaluation exercise as in TS16 for select spaxel-level spectra and for the FOV-integrated spectrum to obtain estimates of the sensitivity temperature for our observations. We find in all cases that there is a well-defined minimum in $\Delta\chi^2$, such that extrapolating below the best-fit lower temperature inferred by the model ($T_l \sim$220 – 270) degrades the fit. However, we stress that unlike in TS16, our data and analysis does not include the low-excitation S(0) line. Without this line to constrain the colder H$_2$, the power-law temperature model has little incentive to “prefer" low temperatures at a fixed slope $n$. We therefore cannot directly constrain a sensitivity temperature comparable to that in TS16 for the observations presented here. However, as discussed in Sec. [4.2](#subsec:analysis:h2mass), we nonetheless estimated the cool+warm H$_2$ mass down to 80 K, $7.93^{+3.52}_{-2.59} \times 10^6 M_{\odot}$, to serve as a lower limit to the total amount of molecular gas in M83’s nuclear region.

TS16 also discusses the utility of a calibration temperature, which we label here as $T_{cal}$, defined such that at $T_l$ = $T_{cal}$ the H$_2$ mass inferred by their model equals the cold/total molecular gas mass derived from CO emission, $M_{H2}$($T >$ $T_{cal}$) = $M_{H2}$(CO). In that work they assume a Galactic $\alpha_{\mathrm{CO}}$ = 3.2 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$, which we also adopted in H23 and the present work. TS16 report an average $T_{cal}$ = $49 \pm 9$ K for their *Spitzer*/IRS sample, such that H$_2$ warmer than $\sim$50 K can account for the entirety of the molecular gas mass inferred from CO in their galaxies.

We performed a first-pass analysis of this type in H23, in which we applied the TS16 model to the integrated spectra of our four regions. In that work, we measured a warm H$_2$ mass of $8.76 \pm 0.33 \times10^4 M_{\odot}$ summed across the four regional spectra, tracing H$_2$ from 2000 K down to 252 – 301 K. We also measured $M_{H2}(T > 50$ K) = $6.79 \pm 0.54 \times 10^7 M_{\odot}$, which we took as an estimate of the total H$_2$ mass in our field.

Recalling the three definitions of $T_{l}^{'}$ we outlined in Section [4.2](#subsec:analysis:h2mass), the warm H$_2$ mass estimate from H23 is most consistent with definition (1), which uses the best-fit value of $T_l$ as the lower bound on the mass integral. Using that limit, in the present work we measured a warm H$_2$ mass of $1.50^{+0.09}_{-0.09} \times 10^5 M_{\odot}$ summed across our FOV. Although the nominal warm gas mass we measure in this work is higher by a factor of $\sim$2, we note that H23 did not apply attenuation corrections to their line fluxes. Since the H$_2$ mass estimate is proportional to the S(1) line flux in the TS16 framework, the difference between the two values is almost entirely accounted for by our use of attenuation corrections in the present work.

If we instead extrapolate the best-fit TS16 models for each pixel to $T_{cal}$ = 50 K, we obtain $M_{H2}(T > 50$ K) = $8.17^{+8.67}_{-4.04} \times 10^7 M_{\odot}$. Although the nominal “total" mass is again slightly higher than that reported in H23, it remains consistent within the (considerable) uncertainties, especially once attenuation corrections are taken into account. The bulk of the uncertainty on our new estimate of the total molecular gas mass is attributable to uncertainties on the per-pixel power-law slopes.

## Potential CO-dark Molecular Gas

The observational dependence on CO introduces the problem of “CO-dark" molecular gas (cite: Wolfire10), or reservoirs of H$_2$that are not traced by cospatial CO emission. As FUV photons and cosmic rays (cite: Bisbas17) permeate into a molecular cloud, the CO molecules dissociate and leave behind an envelope of ionized and neutral carbon in addition to the colder, denser cloud core. H$_2$, meanwhile, can self-shield from photodissociation (cite: Gnedin14) by FUV photons, which leaves a potentially significant reservoir of gas that is coinhabited (partially or fully) by H$_2$, C, and C$^+$ but not CO (cite: Glover12; Madden20; Hu21).

In H23, we used the TS16 framework to estimate the H$_2$ gas mass $M_{H2}$($T >$ 50 K) in the integrated spectra of our four regions, which we took as a measure of the total molecular gas mass. Using the CO(1-0) observations of (cite: Hirota18) and a Galactic CO-to-H$_2$ conversion factor ($\alpha_{\mathrm{CO}}$ = 3.2 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$), we compared this “total" molecular gas mass per region to that inferred from CO using traditional methods and found $M_{H2}$($T >$ 50 K) $>$ $M_{H2}$(CO) in all four pointings. We estimated that, depending on which region/environment we consider, between $\sim$27% and 92% of the molecular gas mass is not accounted for through CO(1-0) emission – in other words, CO-dark gas mass fractions upwards of $\sim$30%, even in the super-solar metallicity core of M83.

While a direct comparison of pixel-level gas masses between our MRS observations and CO data from ALMA is beyond the scope of this work, the resolved power-law models presented above allow us to more accurately examine the CO-dark gas contents of M83’s nuclear region when considering the entirety of our FOV. As summarized in Table [2](#tab:masslist), at temperatures $>$80 K, the TS16 model can only recover $\sim$46% of the CO-based molecular gas mass in our field. However, given the moderately steep power-law slopes we measure in some areas (Figure [5](#fig:h2slopes)), extrapolating to lower temperatures will rapidly inflate the predicted molecular gas mass. At $T_{l}^{'}$ = 50 K, the total $M_{H2}$ mass is a factor of $\sim$4.7 higher than that inferred from CO observations, implying that $\sim$79% of the molecular gas content of M83’s nuclear region is not traced by CO.

On the other hand, if we assume that the CO-based gas mass estimates are correct, we may tweak the chosen value of $T_{l}^{'}$ to find an appropriate $T_{cal}$ for our observations, such that $M_{H2}$($T >$ $T_{cal}$) = $M_{H2}$(CO). We iterated over values of $T_{l}^{'}$ to find a range of temperatures that satisfy $M_{H2}$($T >$ $T_{l}^{'}$) = $M_{H2}$(CO), again only considering the sum of our FOV. For our resolved analysis, a range of temperatures $T_{cal}$ (60 – 70 K) yield an H$_2$ mass estimate that is consistent with $M_{H2}$(CO) = 1.715$\times 10^7 M_{\odot}$ within the uncertainties. For the integrated-light spectrum, we find that $T_{cal}$ = 57 K provides the best match to $M_{H2}$(CO). These are generally consistent with the range of $T_{cal}$ values given in Table 4 of TS16 for their sample of SINGS galaxies.

While temperatures $\gtrsim$50 K are significantly higher than the $\sim$10 – 30 K range typically assumed for the dense, imminently star-forming parts of molecular clouds, the prediction of significant CO-dark gas reservoirs even in high-metallicity galaxies has been borne out repeatedly in simulations. For example, in the simulations by (cite: Hu21), their models with time-dependent H$_2$ chemistry suggest a shallow radial abundance profile for the H$_2$ gas such that a significant fraction of the H$_2$ mass is found in low-density regions, far from the CO-bearing core. When showing the density distribution in their simulations weighted by CO mass, (cite: Hu21) find that the bulk of the CO is found at densities comparable to or greater than the densities at which C is readily converted to CO. When weighting by H$_2$ mass, however, the majority of H$_2$ is found at densities significantly lower than the H/H$_2$ conversion density. This suggests that a significant fraction of the H$_2$ mass is found not in the CO-bearing cloud cores, but in the atomic-dominated regime. While this effect is most extreme at low metallicities (and hence intrinsically low CO abundances), even at $Z = 1 - 3 \times Z_{\odot}$, between 20 and 35% of the H$_2$ mass can be found in gas with abundances $log_{10}$(2$x_{H_2}$) $<$ -0.5 in the (cite: HU21) simulations. When translated to a mass fraction of CO-dark gas at (super-)solar metallicities, they report that even high-sensitivity CO(1-0) observations (down to column density limits of $\sim$6 $\times 10^{14}$ cm $^{-2}$), $\sim$55 – 60% ($\sim$58 – 70%) of the H$_2$ gas mass is CO-dark in their time-dependent (steady state) models.

Even in the context of (cite: Hu21) and other theoretical works which predict the existence of CO-dark gas in galaxies (cite: Wolfire10; Smith14), CO-dark mass fractions of $\sim$80% in the $\gtrsim2\times Z_{\odot}$ environments of M83’s nucleus are surprising and reinforce the need for small-scale spectroscopic observations of the ISM in starbursting galaxies at all metallicities. It is worth noting that our estimate of $M_{H2}$(CO) in our FOV already has a CO-to-H$_2$ conversion factor baked in, which (in principle) should account for the fact that CO does not perfectly trace the low-density H$_2$. The fact that our H$_2$ mass measurements at cool temperatures $\gtrsim70$ K (let alone the colder, denser ISM) are comparable to $M_{H2}$(CO) suggests that a higher-than-Galactic value of $\alpha_{\mathrm{CO}}$ may be necessary even in solar or supersolar environments. A possible exception to this is the nucleus proper, which has the highest best-fit values of $T_l$ ($>$300 K) in the TS16 framework (Figure [5](#fig:h2slopes)). This suggests that the bulk of the H$_2$ in the central $r \sim 15$ pc of the galaxy is in a warm excess phase and is detected directly from rotational emission.

The notion that high values of $\alpha_{\mathrm{CO}}$ are needed for the nuclear region of M83 runs contrary to several literature results which suggest galaxy centers, starbursting galaxies, and galaxies with high metallicity are expected to have $\alpha_{\mathrm{CO}}$ factors lower than the Galactic value (e.g., $\alpha_{\mathrm{CO}} \lesssim 1.0~M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$, vs. Galactic values $\alpha_{\mathrm{CO}} \approx 3 - 4~M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$); see (cite: Bolatto13) and references therein. For example, recent work by (cite: Lee24) shows that, within M83’s disk, $\alpha_{\mathrm{CO}}$ decreases steadily with radius from $\sim 5 - 7 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$) at $R = 6$ kpc to $\sim 2 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$) at $R = 2$ kpc. ALMA observations of barred galaxy centers at $\sim$100 pc scales (cite: Teng22; Teng23) find generally low values of $\alpha_{\mathrm{CO}}$ ($\lesssim 0.5 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$) that decrease with galactocentric radius, driven primarily by a correlation with the optical depth of CO emission.

In the context of these results, a low assumed value of $\alpha_{\mathrm{CO}}$ may be more appropriate for M83’s nuclear region than the value we adopted in this work (3.2 $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$). However, a low $\alpha_{\mathrm{CO}}$ would result in even lower estimates of $M_{H2}$(CO) in our field, exacerbating the discrepancy with the H$_2$ masses from the TS16 model which include the coldest ($\lesssim$60 K) gas. Comprehensive modeling of the H$_2$ rotational lines, CO lines, dust emission, and other putative tracers of CO-dark gas (cite: Bisbas17; Papado22; Ramambason24) will help to better understand the relationship between diffuse H$_2$ and traditional molecular gas tracers in heavily star-forming environments.

![image](figures/baby_zoom.pdf)\

## A Massive, Obscured Point Source

We now briefly discuss a point source which we identify through the flux and kinematic maps of the S(1) line shown in the top row of Figure [4](#fig:h2vis). Specifically, we identify a compact ($\lesssim$5 pc) source at ($\alpha$, $\delta$) = (13:37:00.555, -29:51:53.900) which (1) is slightly redshifted (by $\sim$10 km s$^{-1}$) relative to its surroundings and (2) is fairly broad and spectrally resolved, with a FWHM of $>$150 km s$^{-1}$ at its core. Additionally, this kinematic structure appears at high significance *only* in the S(1) line, with neither Ne lines nor other H$_2$ rotational lines indicating the presence of a point source at the same position.

We also note a moderately reddened (possibly partially-embedded) star cluster at ($\alpha$, $\delta$) = (13:37:00.5205, -29:51:53.702), as measured from *JWST*/NIRCam imaging from the FEAST program (see the next section). The coordinates of the cluster (marked with a diamond in Figures [5](#fig:h2slopes) and [10](#fig:nucmulti)) and of the kinematic hot spot differ by $\sim$0.43$''$ or 9.6 pc. We show multi-wavelength zoom-ins on this area in Figure [9](#fig:babycluster_zoom), including the FWHM map of the H$_2$ S(1) line; CO(2-1) emission (ALMA pID 2013.1.01161.S, PI Sakamoto), and F187N and F335M imaging from JWST-FEAST (Adamo et al. in prep.). The F187N image in Fig. [9](#fig:babycluster_zoom)(c) clearly shows that the partially-embedded cluster has blown away most of its natal material. The ionized shell is a quite striking feature that is ‘pinched’ in the NW and SE direction, presumably due to higher density material, and more freely expanding to the NE. The ‘pinch’ point to the SW corresponds to the edge of a CO cloud (Fig. [9](#fig:babycluster_zoom)(b)) and the location of the H$_2$ point source.

Recent studies of the spiral galaxy NGC 1365 from the PHANGS collaboration (cite: Whitmore23) showed that YMCs with ages $\sim 1.3 \pm 0.7$ Myr are fully obscured in the optical and can remain completely or partly obscured for up to $\sim 3.7 \pm 1.1$ Myr. This is consistent with clearing timescales of 3 – 5 Myr based on *HST* data only, as determined for M83 (cite: Hollyhead15; Deshmukh24) and other galaxies (cite: Messa21; McQuaid24). The stellar population modelling we discuss in Section [5.4](#subsec:disc:stararc) suggests very young ages (2 $\pm$ 1 Myr) even for the UV-brightest and largely unobscured clusters in our Region 2. The young stellar ages in this area, along with the spatial coincidence of the H$_2$ source with CO-emitting gas, leads us to speculate that the kinematically-distinct H$_2$ point source may be a forming or fully-embedded star cluster.

## Gaseous Confirmation of a Stellar Age Gradient?

Nearby starbursts, such as the nuclear region in M83, make optimal laboratories for unraveling the mechanisms operating in extreme environments and across different phases of star formation as their proximity affords exquisite spatial resolution. This is clearly highlighted in the true-color *HST* optical image displayed in Figure [11](#fig:interestingplaces)(e). This figure shows the various complexities in this starburst system, with some regions almost completely obscured towards the north (in Region 2), partially cleared ISM channels in the west-southwest area (Region 4), and fully cleared regions towards the southeast (Region 3).

The *JWST* and *HST* color image in panel (a) of Figure [10](#fig:nucmulti) shows the spatial distribution of the stellar populations, specifically contrasting the old stars (500–1000 Myr; shown in yellow) with young stars ($<$ 25 Myr; shown in blue). The younger, bluer population in Figure [10](#fig:nucmulti)(a) depict a clear “active ringlet," as labeled by (cite: Harris01), who find an apparent age gradient through a photometric study investigating the properties of the massive clusters in this circumnuclear region. Using *HST* broadband and narrowband filters, (cite: Harris01) report that stellar clusters with ages $<$ 5 Myr are preferentially located along the northwestern area (Region 2 in this work). The presence of this age gradient along the starburst’s arc, running from northern to southeastern regions, has since then been studied and debated (cite: Diaz06; Knapen10; Wofford11).

![image](figures/stars_uv_feast.pdf) ![image](figures/iongas_feast.pdf) ![image](figures/pah_feast.pdf)\
![image](figures/co.pdf) ![image](figures/true_rgb.pdf) ![image](figures/h2_mass_nucmulti.pdf)

To further investigate the possible age gradient, we have analyzed archival *HST*/COS observations targeting YMCs in Regions 2 and 4. In the final two panels of Figure [11](#fig:interestingplaces), we show with white-dotted circles the locations of the four COS pointings, which encompass multiple star clusters in a single 2$''$.5 aperture. We characterize the dominant stellar population in each COS pointing using the `SESAMME` software (cite: Jones2023). Being a Python-based full spectrum fitting code, `SESAMME` uses Markov Chain Monte Carlo methods to obtain estimates of the cluster age, metallicity, E(B-V) values, and when the distance to the clusters is known, the user can also constrain the cluster mass. A caveat to the analysis of the COS observations with this software is that `SESAMME` assumes individual stellar populations for each input spectrum. In the context of our test, this means that our analysis then assumes a single dominant stellar population when inferring the stellar properties of the FUV integrated-light spectra. We find that the most massive stellar population encompassed in our COS pointings resides in Region 2, with a mass estimate of 1.13 ($\pm$ 0.02) $\times$ 10$^{6}$ M$_\odot$ and an age of 2 $\pm$ 1 Myr. For the remaining targets in Region 4 we infer an age of 3 $\pm$ 1 Myr for the two easternmost clusters, and 2 $\pm$ 1 Myr for the pointing west of Region 4. Generally, this agrees with the originally proposed trend in the active ringlet, where some of the youngest stellar clusters are found in Region 2. We note that the science programs collecting the *HST*/COS archival data (*HST* program IDs: 11579, 14681 and 15193) analyzed here primarily targeted the brightest FUV objects in the nuclear region of M83. Not surprisingly, we estimate very young ages for these clusters.

In the context of the “active ringlet", the spaxel-level analysis we present here provides additional support for this age gradient.

For example, the bulk of star-formation activity in our FOV (with $\Sigma_{SFR} > 50$ $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$) is found in a clump coincident with (or just eastward of) the massive grouping of very young, unobscured star clusters in Region 2 (Figure [8](#fig:neonSFR)), plus a plume of high SFR extending northward. Conversely, the lowest SFRs are generally found in Region 3, where the \[Ne ii\] emission is significantly broadened and blueshifted.

Each of these structures – the low-SFR patch and the high-SFR clump and plume – also appear in other figures shown in this work. The low-SFR patch, for example, is coincident with a region of faint CO(2-1) and H$_2$ emission and fairly steep power-law slopes in the TS16 model, suggesting little molecular gas mass and low H$_2$ excitation. This patch also shows low optical extinction and is coincident with slightly evolved stellar populations (8.6 Myr in region A of (cite: Knapen10)). While we do not attempt to distinguish (and indeed cannot in the present analysis) a specific mechanism that drove the creation of this dust-less patch (e.g., photoionization vs. shocks), the combination of low-density ISM, ionizing outflows, and apparent lack of $<$5 Myr-old stellar populations in this area strongly suggests a link to previous bursts and cessations of star formation.

The high-SFR clump and plume, meanwhile, roughly corresponds to a region with both high H$_2$ excitation (Figure [5](#fig:h2slopes)) and modest warm H$_2$ mass (Figure [10](#fig:nucmulti)(f)). Interestingly, the CO(2-1) emission is also fairly weak in parts of the clump, where we see bright, ringed structures in Pa$\alpha$, F335M, and F770W imaging from the JWST-FEAST program (Figures [9](#fig:babycluster_zoom)(c,d), [10](#fig:nucmulti)(c)), which suggests that recently-formed stars may be destroying CO and exciting H$_2$ in this area. Conversely, the strongest CO(2-1) emission and highest warm H$_2$ surface densities are more coincident with a knot of high obscuration which extends to the northeast of Region 2, including the kinematic source seen in H$_2$ S(1). This knot is dark even in *JWST*/NIRCam imaging (Figure [10](#fig:nucmulti)(a,b,e)), suggesting extremely high column densities.

## Spatially-varying ISM Properties in M83

To further illustrate our confirmation of the active star-forming ringlet, we extracted spectra within $r = 2$ pixel (0.26$''$) apertures centered on five locations of interest which illustrate the breadth of environments in our FOV. These include (1) a knot in Region 2 with a continuum dominated by cool dust;

\(2\) a modestly reddened, likely partially-embedded star cluster in Region 2; (3) the optical nucleus of M83; (4) the center of the \[Ne ii\] outflow in Region 3; and (5) an Hii region near the string of YMCs in Region 4. We show spectra for these five locations without any attenuation corrections in Figure [11](#fig:interestingplaces),

with the inset image showing the locations and labels of the extraction apertures overlaid on our map of $\tau_{warm}$. The spectra have been normalized to the flux in a line-free region of the spectrum around $\sim$7.15 $\mu$m for easy comparison of the relative continuum shapes and feature strengths. Although we defer a detailed analysis of PAHs and the ionized gas in the core of M83 to future works (Jones et al. in prep.), we briefly highlight spectral features which support our interpretation of the dust and molecular gas in these five environments.

The broad dust properties, for example, clearly vary strongly at the scale of $\sim$100 pc, as can be seen by the variety of mid-IR slopes in the left panel of Figure [11](#fig:interestingplaces). Spectra (1) and (2), which are respectively drawn from a highly- and modestly- attenuated part of our FOV, show deep absorption troughs at 9.7 $\mu$m due to silicates, as well as a substantial amount of flux at the red end of our spectra. This suggests the presence of cooler dust and ISM, which is corroborated by the bright CO(2-1) emission (Figure [10](#fig:nucmulti)(d)) and by the low best-fit temperatures inferred by the TS16 model (bottom panel of Figure [5](#fig:h2slopes)) in the same location. The relative strengths of the neighboring \[Piii\] 17.88 $\mu$m (ionizing potential IP = 19.7 eV, tracing moderate ionization zones) and \[Feii\] 17.94 $\mu$m lines (IP = 7.9 eV, tracing low-ionization zones and/or the shock destruction of iron-rich dust grains; see (cite: Savage96)) also vary with location, with strong \[Piii\] and weak \[Feii\] in environments which are cooler, dustier, and host less-evolved stellar populations (lower-right panel of Figure [11](#fig:interestingplaces)).

In contrast, the \[Piii\]/\[Feii\] line ratio approaches unity and then inverts as the eye travels clockwise through our FOV, with comparable line strengths in the more typical Hii region and dominant \[Feii\] in the high-excitation nucleus and outflow region. Additionally, spectrum (4) is nearly flat across the broad wavelength range covered by our MRS spectroscopy with minimal absorption at 9.7 $\mu$m, suggesting little to no dust in Region 3 (cite: cafe). Indeed, an examination of archival optical imaging (Figure [10](#fig:nucmulti)(e)) shows a virtually dustless window through the ISM of M83 coincident with the patch of blueshifted and highly-dispersed \[Ne ii\] gas we identify in this work. Finally, the optical nucleus and outflow spectra (3 and 4; yellow and blue curves in Figure [11](#fig:interestingplaces)) also show weak but mildly broadened \[Ne v\] emission at 14.3 $\mu$m, which is absent in the other spectra; spectrum 3 additionally shows emission from the very high ionization \[Ne vi\] 7.65 $\mu$m line. We explore the physical drivers of the \[Ne v\] and \[Ne vi\] emission (e.g., fast radiative shocks, X-ray binaries, etc.) in a forthcoming work (Hernandez et al., in prep.).

In H23, we discussed the distribution of iron (as traced by the \[Feii\] 25.99 $\mu$m line) and its correspondence to soft X-ray emission, which is thought to be driven by both SNRs and strong winds from young, massive stars (cite: Long14). We found that the \[Feii\] emission was generally similar in structure to that of soft X-rays, but had little overall correspondence to the locations of known SNRs. This led us to consider the framework described in the review by (cite: Zhang18), in which hot starburst-driven galactic winds collide with the cooler, surrounding ISM to induce shocks. These shocks would then produce both soft X-rays and diffuse \[Feii\] emission (stemming from the destruction of dust grains that release depleted iron back into the ISM).

As in H23, we emphasize that unambiguous confirmation of this scenario in M83’s nuclear region will require self-consistent modeling of the photo- vs. shock ionization, which will be presented in an upcoming work (Jones et al. in prep.). However, the combination of features discussed above for the high-excitation outflow spectrum – the absence of $<$5 Myr old YMCs, the absence of dust seen in both optical imaging and our MRS spectroscopy, a low \[Piii\]/\[Feii\] line ratio, broadened and blueshifted \[Ne ii\] emission, and the presence of \[Nev\] (IP = 97.12 eV) – paint a picture in which previous episodes of massive star formation induce shocks and feedback onto the surrounding ISM.

![](figures/interesting_places.pdf)

# Conclusions

We used MRS spectroscopy from *JWST*/MIRI to examine the warm molecular gas content and star-formation activity in the nuclear region of M83 on the scale of $\sim$3 pc per spaxel. Our resolved analyses illustrates the importance of high-sensitivity spectroscopic observations with *JWST* to accurately characterize the multi-phase ISM, the formation of massive star clusters, and the effects of feedback at the smallest scales. We summarize our findings as follows:

1.  Our continuum and PAH modeling with `CAFE` shows a remarkable variation in the temperatures and optical depths of dust across our $\sim200\times200$ pc$^2$ field of view. In regions with high dust columns, continuum and line fluxes can be attenuated by non-negligible amounts (up to 30%) even at the long wavelengths accessible to MRS (Section [3.1](#subsec:methods:att)).

2.  Pure rotational transitions of H$_2$ show a range of intensities and excitation conditions within M83’s nuclear region, with the most excited emission coincident with the optical nucleus and with groupings of young, massive star clusters. Maps of the H$_2$ emission and line widths reveal complex filamentary and clumpy structures (Section [4](#sec:analysis)).

3.  We identify a point-like source in the flux and kinematic maps of the H$_2$ S(1) line, which we propose is a forming or fully-embedded star cluster given its location with respect to the CO (2-1) emission and apparent size ($\lesssim$5 pc) (Section [5.3](#subsec:disc:baby)).

4.  Using the power-law temperature distribution model of (cite: Togi16), we derive H$_2$ masses down to various temperature limits. The warmest H$_2$ gas ($>$200 K), totaling 2.26 $\times 10^5 M_{\odot}$, accounts for $\sim$1% of the total molecular gas mass in our FOV as inferred from CO observations (cite: Hirota18), while integrating the TS16 power-law models to temperatures $T_{cal} \sim$57 – 70 K provide a reasonable match to the CO-based mass estimates. Integrating to still-lower temperatures drastically increases the mass of H$_2$ to over 400% of the CO-based mass estimates, suggesting either the presence of a significant reservoir of gas that is not traced by CO or the need for further constraints on $\alpha_{\mathrm{CO}}$ even in the super-solar metallicity environment of M83’s center. Alternative estimates of the molecular gas mass (cite: Papado22; Ramambason24) will be critical for confirming either scenario (Sections [4.2](#subsec:analysis:h2mass) and [5.2](#subsec:disc:codark)).

5.  By performing the same analysis on our spaxel-level data and on the integrated-light spectrum of the nuclear region, we find hints that, within the (cite: Togi16) framework, the inferred H$_2$ mass may depend weakly on the physical scale probed ($<$5 vs. 200 pc) due to blending of high and low-excitation regions (Section [4.2](#subsec:analysis:h2mass)).

6.  The \[Ne ii\] 12.81 $\mu$m line shows evidence for a secondary, high-FWHM kinematic component that is ubiquitous across our FOV, with a patch of our Region 3 showing evidence for ionized outflows. Converting the \[Ne ii\] and \[Ne iii\] luminosities to SFR with diagnostic of (cite: Zhuang19) reveal modest SFR surface densities in Regions 1, 3, and 4, but fairly high ones in Region 2, reaching up to 75 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ in $3\times3$ pc$^2$ pixels (Section [4.3](#subsec:analysis:sfr)).

7.  We model the integrated far-UV light from four *HST*/COS pointings centered on groupings of YMCs, finding that the youngest and most massive clusters coincide with regions of high SFR and high H$_2$ excitation, and are adjacent to extremely dusty, CO-bright clouds. When placed in the context of the high-resolution, multi-wavelength ancillary data available for M83’s nuclear region, this supports the notion of a star-forming ringlet with a mild age gradient as first proposed by (cite: Harris01) (Section [5.4](#subsec:disc:stararc)).

# Acknowledgments

*Software:* This work makes use of

`CAFE` (cite: cafe), `SciPy` (cite: Scipy20), `numpy` (cite: Numpy11), and Astropy (cite: Astropy13; Astropy18; Astropy22) in our analyses, as well as `Matplotlib` (cite: Matplotlib07) and `cmasher` (cite: cmasher) for data visualization and `Jupyter` (cite: JupyterNotebook16) for general workflow. S. H. 

acknowledges support from the European Space Agency (ESA). L. R. gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant No. CH2137/1-1).

natexlab

(ref: Appleton06) Appleton, P. N., Xu, K. C., Reach, W., et al. 2006, ApJL, 639, L51, doi: [`10.1086/502646`](http://doi.org/10.1086/502646)

(ref: Armus23) Armus, L., Lai, T., U, V., et al. 2023, ApJL, 942, L37, doi: [`10.3847/2041-8213/acac66`](http://doi.org/10.3847/2041-8213/acac66)

(ref: Astropy13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy22) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Avni76) Avni, Y. 1976, ApJ, 210, 642, doi: [`10.1086/154870`](http://doi.org/10.1086/154870)

(ref: Bethermin23) Béthermin, M., Accard, C., Guillaume, C., et al. 2023, A&A, 680, L8, doi: [`10.1051/0004-6361/202348115`](http://doi.org/10.1051/0004-6361/202348115)

(ref: Bigiel08) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846, doi: [`10.1088/0004-6256/136/6/2846`](http://doi.org/10.1088/0004-6256/136/6/2846)

(ref: Bik24) Bik, A., Álvarez-Márquez, J., Colina, L., et al. 2024, A&A, 686, A3, doi: [`10.1051/0004-6361/202348845`](http://doi.org/10.1051/0004-6361/202348845)

(ref: Bisbas17) Bisbas, T. G., van Dishoeck, E. F., Papadopoulos, P. P., et al. 2017, ApJ, 839, 90, doi: [`10.3847/1538-4357/aa696d`](http://doi.org/10.3847/1538-4357/aa696d)

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Chiang24) Chiang, I.-D., Sandstrom, K. M., Chastenet, J., et al. 2024, ApJ, 964, 18, doi: [`10.3847/1538-4357/ad23ed`](http://doi.org/10.3847/1538-4357/ad23ed)

(ref: Costa24) Costa-Souza, J. H., Riffel, R. A., Souza-Oliveira, G. L., et al. 2024, arXiv e-prints, arXiv:2408.06100, doi: [`10.48550/arXiv.2408.06100`](http://doi.org/10.48550/arXiv.2408.06100)

(ref: Deshmukh24) Deshmukh, S., Linden, S. T., Calzetti, D., et al. 2024, arXiv e-prints, arXiv:2409.08994, doi: [`10.48550/arXiv.2409.08994`](http://doi.org/10.48550/arXiv.2409.08994)

(ref: Diaz06) Dı́az, R. J., Dottori, H., Aguero, M. P., et al. 2006, ApJ, 652, 1122, doi: [`10.1086/507886`](http://doi.org/10.1086/507886)

(ref: Donnan23) Donnan, F. R., Garcı́a-Bernete, I., Rigopoulou, D., et al. 2023, MNRAS, 519, 3691, doi: [`10.1093/mnras/stac3729`](http://doi.org/10.1093/mnras/stac3729)

(ref: Glover12) Glover, S. C. O., & Clark, P. C. 2012, MNRAS, 426, 377, doi: [`10.1111/j.1365-2966.2012.21737.x`](http://doi.org/10.1111/j.1365-2966.2012.21737.x)

(ref: Gnedin14) Gnedin, N. Y., & Draine, B. T. 2014, ApJ, 795, 37, doi: [`10.1088/0004-637X/795/1/37`](http://doi.org/10.1088/0004-637X/795/1/37)

(ref: Harris01) Harris, J., Calzetti, D., Gallagher, John S., I., Conselice, C. J., & Smith, D. A. 2001, AJ, 122, 3046, doi: [`10.1086/324230`](http://doi.org/10.1086/324230)

(ref: Hernandez21) Hernandez, S., Aloisi, A., James, B. L., et al. 2021, ApJ, 908, 226, doi: [`10.3847/1538-4357/abd6c4`](http://doi.org/10.3847/1538-4357/abd6c4)

(ref: Hernandez23) Hernandez, S., Jones, L., Smith, L. J., et al. 2023, ApJ, 948, 124, doi: [`10.3847/1538-4357/acc837`](http://doi.org/10.3847/1538-4357/acc837)

(ref: Hirota18) Hirota, A., Egusa, F., Baba, J., et al. 2018, PASJ, 70, 73, doi: [`10.1093/pasj/psy071`](http://doi.org/10.1093/pasj/psy071)

(ref: Ho07) Ho, L. C., & Keto, E. 2007, ApJ, 658, 314, doi: [`10.1086/511260`](http://doi.org/10.1086/511260)

(ref: Hollyhead15) Hollyhead, K., Bastian, N., Adamo, A., et al. 2015, MNRAS, 449, 1106, doi: [`10.1093/mnras/stv331`](http://doi.org/10.1093/mnras/stv331)

(ref: Hu22) Hu, C.-Y., Schruba, A., Sternberg, A., & van Dishoeck, E. F. 2022, ApJ, 931, 28, doi: [`10.3847/1538-4357/ac65fd`](http://doi.org/10.3847/1538-4357/ac65fd)

(ref: Hu21) Hu, C.-Y., Sternberg, A., & van Dishoeck, E. F. 2021, ApJ, 920, 44, doi: [`10.3847/1538-4357/ac0dbd`](http://doi.org/10.3847/1538-4357/ac0dbd)

(ref: Hunt21) Hunt, Q., Gallo, E., Chandar, R., et al. 2021, ApJ, 912, 31, doi: [`10.3847/1538-4357/abe531`](http://doi.org/10.3847/1538-4357/abe531)

(ref: Matplotlib07) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Inami13) Inami, H., Armus, L., Charmandaris, V., et al. 2013, ApJ, 777, 156, doi: [`10.1088/0004-637X/777/2/156`](http://doi.org/10.1088/0004-637X/777/2/156)

(ref: James14) James, B. L., Aloisi, A., Heckman, T., Sohn, S. T., & Wolfe, M. A. 2014, ApJ, 795, 109, doi: [`10.1088/0004-637X/795/2/109`](http://doi.org/10.1088/0004-637X/795/2/109)

(ref: Jones2023) Jones, L. H., Hernandez, S., Smith, L. J., et al. 2023a, ApJ, 959, 20, doi: [`10.3847/1538-4357/acfe0f`](http://doi.org/10.3847/1538-4357/acfe0f)

(ref: OJones23) Jones, O. C., Álvarez-Márquez, J., Sloan, G. C., et al. 2023b, MNRAS, 523, 2519, doi: [`10.1093/mnras/stad1609`](http://doi.org/10.1093/mnras/stad1609)

(ref: Kennicutt98) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: JupyterNotebook16) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in IOS Press, 87–90, doi: [`10.3233/978-1-61499-649-1-87`](http://doi.org/10.3233/978-1-61499-649-1-87)

(ref: Knapen10) Knapen, J. H., Sharp, R. G., Ryder, S. D., et al. 2010, MNRAS, 408, 797, doi: [`10.1111/j.1365-2966.2010.17180.x`](http://doi.org/10.1111/j.1365-2966.2010.17180.x)

(ref: Koda23) Koda, J., Hirota, A., Egusa, F., et al. 2023, ApJ, 949, 108, doi: [`10.3847/1538-4357/acc65e`](http://doi.org/10.3847/1538-4357/acc65e)

(ref: Lai22) Lai, T. S. Y., Armus, L., U, V., et al. 2022, ApJL, 941, L36, doi: [`10.3847/2041-8213/ac9ebf`](http://doi.org/10.3847/2041-8213/ac9ebf)

(ref: Law23) Law, D. R., E. Morrison, J., Argyriou, I., et al. 2023, AJ, 166, 45, doi: [`10.3847/1538-3881/acdddc`](http://doi.org/10.3847/1538-3881/acdddc)

(ref: Lee24) Lee, A. M., Koda, J., Hirota, A., Egusa, F., & Heyer, M. 2024, ApJ, 968, 97, doi: [`10.3847/1538-4357/ad40a0`](http://doi.org/10.3847/1538-4357/ad40a0)

(ref: starburst99) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3, doi: [`10.1086/313233`](http://doi.org/10.1086/313233)

(ref: Leroy21) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: Long14) Long, K. S., Kuntz, K. D., Blair, W. P., et al. 2014, ApJS, 212, 21, doi: [`10.1088/0067-0049/212/2/21`](http://doi.org/10.1088/0067-0049/212/2/21)

(ref: Madden20) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141, doi: [`10.1051/0004-6361/202038860`](http://doi.org/10.1051/0004-6361/202038860)

(ref: Maragkoudakis18) Maragkoudakis, A., Ivkovich, N., Peeters, E., et al. 2018, MNRAS, 481, 5370, doi: [`10.1093/mnras/sty2658`](http://doi.org/10.1093/mnras/sty2658)

(ref: cafe) Marshall, J. A., Herter, T. L., Armus, L., et al. 2007, ApJ, 670, 129, doi: [`10.1086/521588`](http://doi.org/10.1086/521588)

(ref: Mast06) Mast, D., Dı́az, R. J., & Agüero, M. P. 2006, AJ, 131, 1394, doi: [`10.1086/499941`](http://doi.org/10.1086/499941)

(ref: McQuaid24) McQuaid, T., Calzetti, D., Linden, S. T., et al. 2024, ApJ, 967, 102, doi: [`10.3847/1538-4357/ad3e64`](http://doi.org/10.3847/1538-4357/ad3e64)

(ref: Messa21) Messa, M., Calzetti, D., Adamo, A., et al. 2021, ApJ, 909, 121, doi: [`10.3847/1538-4357/abe0b5`](http://doi.org/10.3847/1538-4357/abe0b5)

(ref: MeyerHipass) Meyer, M. J., Zwaan, M. A., Webster, R. L., et al. 2004, MNRAS, 350, 1195, doi: [`10.1111/j.1365-2966.2004.07710.x`](http://doi.org/10.1111/j.1365-2966.2004.07710.x)

(ref: Mingozzi22) Mingozzi, M., James, B. L., Arellano-Córdova, K. Z., et al. 2022, ApJ, 939, 110, doi: [`10.3847/1538-4357/ac952c`](http://doi.org/10.3847/1538-4357/ac952c)

(ref: Ossenkopf92) Ossenkopf, V., Henning, T., & Mathis, J. S. 1992, A&A, 261, 567

(ref: Papado22) Papadopoulos, P., Dunne, L., & Maddox, S. 2022, MNRAS, 510, 725, doi: [`10.1093/mnras/stab3194`](http://doi.org/10.1093/mnras/stab3194)

(ref: Pavesi18) Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49, doi: [`10.3847/1538-4357/aacb79`](http://doi.org/10.3847/1538-4357/aacb79)

(ref: Ramambason24) Ramambason, L., Lebouteiller, V., Madden, S. C., et al. 2024, A&A, 681, A14, doi: [`10.1051/0004-6361/202347280`](http://doi.org/10.1051/0004-6361/202347280)

(ref: Rigby23) Rigby, J., Perrin, M., McElwain, M., et al. 2023, PASP, 135, 048001, doi: [`10.1088/1538-3873/acb293`](http://doi.org/10.1088/1538-3873/acb293)

(ref: Rigo24) Rigopoulou, D., Donnan, F. R., Garcı́a-Bernete, I., et al. 2024, MNRAS, 532, 1598, doi: [`10.1093/mnras/stae1535`](http://doi.org/10.1093/mnras/stae1535)

(ref: DelPino23) Rodrı́guez Del Pino, B., Perna, M., Arribas, S., et al. 2023, arXiv e-prints, arXiv:2309.14431, doi: [`10.48550/arXiv.2309.14431`](http://doi.org/10.48550/arXiv.2309.14431)

(ref: Russell20) Russell, T. D., White, R. L., Long, K. S., et al. 2020, MNRAS, 495, 479, doi: [`10.1093/mnras/staa1177`](http://doi.org/10.1093/mnras/staa1177)

(ref: Saha06) Saha, A., Thim, F., Tammann, G. A., Reindl, B., & Sandage, A. 2006, ApJS, 165, 108, doi: [`10.1086/503800`](http://doi.org/10.1086/503800)

(ref: Sandstrom13) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: Savage96) Savage, B. D., & Sembach, K. R. 1996, ApJ, 470, 893, doi: [`10.1086/177919`](http://doi.org/10.1086/177919)

(ref: Smith14) Smith, R. J., Glover, S. C. O., Clark, P. C., Klessen, R. S., & Springel, V. 2014, MNRAS, 441, 1628, doi: [`10.1093/mnras/stu616`](http://doi.org/10.1093/mnras/stu616)

(ref: Teng22) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2022, ApJ, 925, 72, doi: [`10.3847/1538-4357/ac382f`](http://doi.org/10.3847/1538-4357/ac382f)

(ref: Teng23) —. 2023, ApJ, 950, 119, doi: [`10.3847/1538-4357/accb86`](http://doi.org/10.3847/1538-4357/accb86)

(ref: Thilker05) Thilker, D. A., Bianchi, L., Boissier, S., et al. 2005, ApJL, 619, L79, doi: [`10.1086/425251`](http://doi.org/10.1086/425251)

(ref: Togi16) Togi, A., & Smith, J. D. T. 2016, ApJ, 830, 18, doi: [`10.3847/0004-637X/830/1/18`](http://doi.org/10.3847/0004-637X/830/1/18)

(ref: cmasher) van der Velden, E. 2020, The Journal of Open Source Software, 5, 2004, doi: [`10.21105/joss.02004`](http://doi.org/10.21105/joss.02004)

(ref: Numpy11) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: Scipy20) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Wang21) Wang, Q. D., Zeng, Y., Bogdán, Á., & Ji, L. 2021, MNRAS, 508, 6155, doi: [`10.1093/mnras/stab2997`](http://doi.org/10.1093/mnras/stab2997)

(ref: Westmoquette07) Westmoquette, M. S., Exter, K. M., Smith, L. J., & Gallagher, J. S. 2007, MNRAS, 381, 894, doi: [`10.1111/j.1365-2966.2007.12346.x`](http://doi.org/10.1111/j.1365-2966.2007.12346.x)

(ref: Whitmore23) Whitmore, B. C., Chandar, R., Rodrı́guez, M. J., et al. 2023, ApJL, 944, L14, doi: [`10.3847/2041-8213/acae94`](http://doi.org/10.3847/2041-8213/acae94)

(ref: Winkler23) Winkler, P. F., Long, K. S., Blair, W. P., & Points, S. D. 2023, ApJ, 943, 15, doi: [`10.3847/1538-4357/aca7f9`](http://doi.org/10.3847/1538-4357/aca7f9)

(ref: Wofford11) Wofford, A., Leitherer, C., & Chandar, R. 2011, ApJ, 727, 100, doi: [`10.1088/0004-637X/727/2/100`](http://doi.org/10.1088/0004-637X/727/2/100)

(ref: Wolfire10) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191, doi: [`10.1088/0004-637X/716/2/1191`](http://doi.org/10.1088/0004-637X/716/2/1191)

(ref: Xu16) Xu, D., Li, D., Yue, N., & Goldsmith, P. F. 2016, ApJ, 819, 22, doi: [`10.3847/0004-637X/819/1/22`](http://doi.org/10.3847/0004-637X/819/1/22)

(ref: Young23) Young, J., Pope, A., Sajina, A., et al. 2023, ApJL, 958, L5, doi: [`10.3847/2041-8213/ad07e1`](http://doi.org/10.3847/2041-8213/ad07e1)

(ref: Zhang18) Zhang, D. 2018, Galaxies, 6, 114, doi: [`10.3390/galaxies6040114`](http://doi.org/10.3390/galaxies6040114)

(ref: Zhang23) Zhang, L., & Ho, L. C. 2023, ApJL, 953, L9, doi: [`10.3847/2041-8213/acea73`](http://doi.org/10.3847/2041-8213/acea73)

(ref: Zhuang19) Zhuang, M.-Y., Ho, L. C., & Shangguan, J. 2019, ApJ, 873, 103, doi: [`10.3847/1538-4357/ab0650`](http://doi.org/10.3847/1538-4357/ab0650)

# Single and double Gaussian fits to \[Ne iii\]

In Figure [12](#fig:appendix:neon3), we show the flux, velocity shift, and FWHM of the \[Ne iii\] 15.5 $\mu$m line using both a single and a double Gaussian component. Details on the line fitting and on the application of the statistical $F$-test for the two-component fits are given in Sections [3.2](#subsec:methods:emlines) and [4.3](#subsec:analysis:sfr), respectively.

![image](figures/Neon3_single.pdf)\
![image](figures/Neon3.pdf)

[^1]: https://github.com/GOALS-survey/CAFE

[^2]: https://jwst-docs.stsci.edu/jwst-mid-infrared-instrument/miri-observing-modes/miri-medium-resolution-spectroscopy

[^3]: Link TBD

</paper>

Write the methods card for this paper.