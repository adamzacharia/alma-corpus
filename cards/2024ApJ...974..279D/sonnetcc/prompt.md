# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...974..279D\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...974..279D",
 "title": "A Millimeter Rebrightening in GRB 210702A",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "de Wet, Simon",
 "n_authors": 12,
 "arxiv_id": "2408.14641",
 "doi": "10.3847/1538-4357/ad77bb",
 "alma_projects_linked_by_archive": [
  "2019.1.01032.T",
  "2019.1.01484.T"
 ]
}
```

Paper text:
<paper>
# A millimeter rebrightening in GRB 210702A

## Abstract

We present X-ray to radio frequency observations of the bright long gamma-ray burst GRB 210702A. Our ALMA 97.5 GHz observations show a significant rebrightening by a factor of $\approx2$ beginning at 8.2 days post-burst and rising to peak brightness at 18.1 days before declining again. This is the first such rebrightening seen in a millimeter afterglow light curve. A standard forward shock model in a stellar wind circumburst medium can explain most of our X-ray, optical and millimeter observations prior to the rebrightening, but significantly over-predicts the self-absorbed radio emission, and cannot explain the millimeter rebrightening. We investigate possible explanations for the millimeter rebrightening and find that energy injection or a reverse shock from a late-time shell collision are plausible causes. Similar to other bursts, our radio data may require alternative scenarios such as a thermal electron population or a structured jet to explain the data. Our observations demonstrate that millimeter light curves can exhibit some of the rich features more commonly seen in optical and X-ray afterglow light curves, motivating further millimeter wavelength studies of GRB afterglows.

# Introduction

The highly relativistic jets in long gamma-ray bursts (GRBs) are thought to be ejected by a black hole or a magnetar central engine that is formed following the catastrophic destruction of a massive Wolf-Rayet star due to their association with Type Ic supernovae (cite: Woosley2006). In the fireball model for GRBs, the GRB itself is produced via emission from internal dissipation processes within the expanding jet, while the longer-lived broadband afterglow emission is produced within an external forward shock created by the expanding jet as it sweeps up the surrounding medium (cite: Meszaros1997; Sari1998; Piran1999; Piran2004; Kumar2015).

The forward shock model for GRB afterglows has been successful in explaining large swathes of observational data. In this basic picture, electrons are accelerated within the decelerating forward shock, which results in a power-law in energies that gives rise to a multi-segment broken power-law synchrotron emission spectrum characterised by a number of break frequencies whose evolution is dictated by the dynamics of the blast wave (cite: Meszaros1997; Sari1998). Optical and X-ray observations have shown widespread compatibility with the synchrotron forward shock model (cite: Wang2015), though extensions from the simplest case have been required to account for less common features such as achromatic steepenings, flares and plateaus (cite: Rhoads1999; Sari1999; Zhang2006).

Compared to X-ray and optical observations, radio follow-up of GRBs has been more sparse, despite the key role that radio observations can play in elucidating the physics of GRB jets (cite: Frail1997; Waxman1998; Berger2003; Chandra2012; Granot2014). Radio observations uniquely sample the peak of the synchrotron spectrum and the synchrotron self-absorption break, allowing for the GRB jet energy, external density, and microphysical parameters to be determined via broadband modelling (cite: BarniolDuran2014; Laskar2015; Aksulu2022; Duncan2023). At later times once the blast wave has transitioned to a non-relativistic, spherical state, radio observations may be used to perform calorimetry and thereby constrain the jet energetics (cite: Frail2000; Berger2004; Frail2005; Vanderhorst2008). Very Long Baseline Interferometry observations have been used to constrain the source size and proper motion, for instance in GBR 030329 (cite: Taylor2005; Pihlstrom2007; Mesler2012). Perhaps the most valuable contribution from studies at radio frequencies has been the detection of a second emission component due to reverse shock emission from a shock wave travelling back into the jet (cite: Kulkarni1999; Frail2000a; Laskar2013; Perley2014; Vanderhorst2014), which has resulted in constraints on the jet’s magnetization and initial bulk Lorentz factor (cite: Sari1999b; Kobayashi2003; Zhang2005; Laskar2018a; Laskar2018b).

Observationally, radio light curves often rise at early times and peak at a few days post-burst before declining (cite: Chandra2012), which is in contrast to X-ray and optical light curves which are generally decaying at all times. Lower frequency radio light curves may even peak on longer timescales of months to years (cite: Vanderhorst2008). These peaks are commonly interpreted as the passage of the synchrotron peak frequency through the observing band, with lower frequencies peaking later than higher frequencies. However, sample studies have found that a large number of radio afterglows are challenging to interpret within standard forward shock models and may require non-standard scenarios such as a long-lived reverse shock, altered electron population, or a structured outflow to explain the data (cite: Panaitescu2004; Kangas2020; Levine2023; Laskar2023). Radio light curves show a diversity of behaviour, with some showing smooth light curves and others showing flares (cite: Kulkarni1999; Soderberg2007; Schroeder2023). At early times, diffractive and refractive interstellar scintillation can severely affect centimeter-band observations, hampering physical interpretation (cite: Laskar2018b; Alexander2019). In contrast, millimeter observations are usually not subject to scintillation and therefore any observed light curve feature must be intrinsic to the source. Despite its value, millimeter follow-up efforts have been more limited compared to the centimeter bands, particularly in the pre-ALMA era when existing observatories had limited sensitivity (cite: Postigo2012).

Here we present X-ray, optical, millimeter and radio observations of the long GRB 210702A spanning 8 orders of magnitude in frequency (1 keV to 700 MHz) and almost 5 orders of magnitude in time (0.001 to 86 days). Our ALMA 97.5 GHz ($\approx3$ mm) light curve shows an unpredecedented rebrightening beginning at 8.2 days and increasing by a factor of $\approx2$ in brightness to reach a peak at 18.1 days before declining again. We find that a standard forward shock model can explain most of our multi-wavelength data prior to the millimeter rebrightening, but cannot explain the low frequency radio data and early X-ray light curve. We investigate a number of common explanations for rebrightenings in GRB afterglows and find that energy injection or a reverse shock from a late-time shell collision are plausible explanations, although we are unable to conclusively favour one scenario.

We report all uncertainties at the $1\sigma$ level unless stated otherwise, and all magnitudes are in the AB system. We adopt a $\Lambda$CDM cosmology with $\Omega_m=0.315$ and $H_0=67.4$ km s$^{-1}$ Mpc$^{-1}$ (cite: Planck2020).

# Observations

## Prompt emission

The *Swift* Burst Alert Telescope (cite: BAT) was triggered by GRB 210702A at 19:07:13 UT on 2021 July 2 (cite: 30351). Refined BAT analysis indicated that the $\gamma$-ray mask-weighted light curve showed a single-peaked fast rise exponential decay-like structure with a measured duration of $T_{90}=138.2\pm47.6$ s. GRB 210702A was also detected by the CALET, AGILE, and Konus-Wind $\gamma$-ray detectors (cite: 30362; 30363; 30366). The Konus Wind fluence in the 20 keV – 20 MeV range was $(2.5\pm0.2)\times10^{-4}$ erg cm$^{-2}$. The burst redshift of $z=1.160$ (cite: 30357) corresponds to a luminosity distance of $D_L=2.53\times10^{28}$ cm, from which we calculate a burst isotropic $\gamma$-ray energy of $E_{\gamma,\mathrm{iso}}=(9.3\pm0.7)\times10^{53}$ erg. We take the BAT trigger time as $T_0$ and reference all other times with respect to this time.

## X-ray

The X-Ray Telescope aboard *Swift* (cite: XRT) began observing the field of the GRB 95.5 s after the BAT trigger and identified a bright new X-ray source consistent with the BAT position (cite: 30351). The first 310 s of data were taken in windowed timing (WT) mode while BAT was also capturing data, after which *Swift* had to slew away. Observations began again in photon counting (PC) mode at 3561 s post-trigger. We downloaded the X-ray count-rate light curve and time-averaged WT and PC spectra from the online *Swift*/XRT GRB Catalogue[^1]. We fitted the WT and PC mode spectra in Xspec version 12.13.0 with a photoelectrically absorbed power-law model (`tbabs*ztbabs*pow`) taking into account Galactic and host galaxy absorption. The Galactic column density was fixed at $N_\mathrm{H,Gal}=1.19\times10^{21}$ cm$^{-2}$ (cite: Willingale2013) and the burst redshift at $z=1.160$. For the PC mode spectrum we derived a host galaxy column density of $N_\mathrm{H,host}=(2.3\pm0.6)\times10^{21}$ cm$^{-2}$ with a C-stat of 522 for 561 degrees of freedom. We obtained photon indices of $\Gamma=1.54\pm0.01$ and $\Gamma=1.95\pm0.03$ for the WT and PC mode spectra, respectively. The resulting spectral indices[^2] are therefore $\beta_\mathrm{X,WT}=-0.54\pm0.01$ and $\beta_\mathrm{X,PC}=-0.95\pm0.03$. Using the photon indices from our fits along with respective unabsorbed counts-to-flux conversion factors of $4.86\times10^{-11}$ erg cm$^{-2}$ count$^{-1}$ and $4.54\times10^{-11}$ erg cm$^{-2}$ count$^{-1}$ from our fits, we converted the 0.3–10 keV count-rate light curve into a 1 keV flux density light curve.

## UV/Optical

The *Swift* Ultra-Violet Optical Telescope (cite: UVOT) started observing the BAT error region 104 s after the BAT trigger in the *white* filter. A bright optical source consistent with the XRT position was identified at coordinates $\alpha=11^\mathrm{h}14^\mathrm{m}18.70^\mathrm{s}$, $\delta = -36^\circ 44^{\prime}50.0^{\prime\prime}$ (J2000) with an uncertainty of $0.42^{\prime\prime}$ (cite: 30356). The first 147 s *white* filter exposure was saturated, along with a 44 s $u$-band exposure that began at 316 s post-trigger. UVOT recommenced observations just under one hour post-trigger, detecting the afterglow with a brightness of $b=15.15\pm0.03$ mag. Observations continued intermittently in all filters until 8.08 days post-trigger. We obtained the UVOT data from the *Swift* Archive Download Portal[^3] hosted on the UK *Swift* Science Data Centre website, and extracted magnitudes using the `uvotproduct` tool from the HEASoft[^4] *Swift* FTOOLS software package, version 6.31.1. We employed a $5^{\prime\prime}$ aperture for the source region and a $10^{\prime\prime}$ aperture for the background region. For the saturated $u$-band exposure we adopt the AB magnitude measurement of $u=12.34\pm0.18$ mag calculated by (cite: Zhou2023) using their method for measuring photometries of moderately saturated UVOT sources. We do not include the $white$ filter exposures since the $white$ filter is too broad for our purposes.

The MeerLICHT optical telescope (cite: Bloemen2016) was automatically triggered by the *Swift* detection of GRB 210702A and began observing the BAT errorbox at 19:22:54 UT, just under 16 minutes after the BAT trigger time. Observations consisted of 60 s exposures in six optical filters following the filter sequence $quqgqrqiqz$, where the $q$ band is a wide filter spanning 440–720 nm and the $ugriz$ bands are standard SDSS filters. The optical afterglow was detected with a brightness of $q=12.84\pm0.02$ mag in our first exposure (cite: 30354). A total of 15 exposures were obtained over 25 minutes of observing before strong winds forced the telescope to close. We used the MeerLICHT pipeline (Vreeswijk et al., in prep.) to reduce the data, implementing standard CCD reduction tasks including astrometry and PSF photometry. The afterglow was well detected in all images.

We additionally make use of optical photometry made public through Gamma-Ray Coordinates Network (GCN) Circulars: the X-Shooter acquisition camera on the Very Large Telescope (VLT) detected the afterglow in a 20 s exposure at 0.18 days post-trigger with a brightness of $r^{\prime}=16.91\pm0.01$ mag (cite: 30357), and the Chilescope RC-1000 telescope detected the afterglow at 0.19 days with a brightness of $r^{\prime}=17.01\pm0.05$ mag (cite: 30365).

## Radio

### ALMA

We obtained nine epochs of observations with the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 3 (97.5 GHz) and three epochs of observations in Band 7 (343.5 GHz), through programs 2019.1.01484.T (PI Laskar) and 2019.1.01032.T (PI Perley). The Band 3 and Band 7 observations both employed two 4 GHz base-bands centred on 91.5 and 103.5 GHz, and 337.5 and 349.5 GHz, respectively. We downloaded the pipeline-generated images from the ALMA archive and measured the source flux using the Common Astronomy Software Application (cite: McMullin2007) `imfit` task.

### ATCA

We observed GRB 210702A at seven epochs with the Australia Telescope Compact Array (ATCA) beginning at 3.50 days post-trigger. The first epoch consisted of observations in the 16.7, 21.2, 33 and 35 GHz bands, while all subsequent epochs consisted of observations at these same frequencies along with the 5.5 and 9 GHz bands. We used PKS 1934$-$638 as the flux and bandpass calibrator and PKS 1144$-$379 as the complex gain calibrator. At 33 and 35 GHz the flux calibrator was significantly fainter than the gain calibrator, so in these two bands we used the gain calibrator as our bandpass calibrator (after first deriving its intrinsic spectral index using PKS 1934$-$638) in order to derive an accurate bandpass solution.

We used the `MIRIAD` software package[^5] (cite: Miriad) for calibration and the CASA `tclean` task for imaging the calibrated target visibilities. We combined the 33 and 35 GHz measurement sets prior to imaging in order to obtain a single 34 GHz flux measurement. At 5.5 GHz we combined the target visibilities from all epochs and imaged the resulting data set in order to create a sky model for the other sources in the field. We then performed imaging on the UV-subtracted target visibilities in order to measure the source flux. During epochs four through six the Array was in a configuration in which antenna CA06 was located far away compared to the other antennas. We excluded antenna CA06 while imaging the fifth epoch data as it produced images with a lower noise level. The epoch three and seven high frequency (16.7–35 GHz) gain calibrator phases varied wildly as a result of poor weather. We therefore exclude these data from subsequent analysis.

We measured the flux of the afterglow using two methods: using the CASA `imfit` task on the target images; and UV-fitting the calibrated measurement sets with a point source model with the CASA `uvmodelfit` task. The fluxes measured with both methods were generally found to agree within errors. We employ the UV fitting fluxes henceforth.

Additionally, (cite: Anderson2023) obtained early ($t<1$ day) radio observations of GRB 210702A with ATCA and found rapid variability in the radio light curves which they attribute to interstellar scintillation. Since short time-scale variability is not the focus of this paper, we take the average of the $3\sigma$ fluxes per observing band from their Table A1 which results in a single flux measurement in each of the 5.5, 9, 16.7 and 21.2 GHz bands at $\approx0.53$ days.

### MeerKAT

We observed the radio afterglow with the MeerKAT radio telescope in the L band (1.28 GHz) at five epochs through observing program SCI-20210212-TL-01 (PI Laskar). We used J0408$-$6545 as the flux and bandpass calibrator for the first and last epochs and J1939$-$6342 as the flux and bandpass calibrator for the intervening epochs, while J1154$-$3505 was used as the complex gain calibrator for all epochs. The total integration time on source was 0.65 hr per epoch. We flagged, calibrated and imaged the data using the `oxkat` pipeline[^6] (cite: Heywood2020), and measured the flux of the afterglow with the `imfit` task in CASA.

### GMRT

We obtained five epochs of observations with the Giant Metrewave Radio Telescope (GMRT) through program 40_084 (PI Laskar) beginning at 8.6 days post-trigger. Observations were carried out in Band 4 (700 MHz) with a 400 MHz bandwidth, employing 3C286 as the flux and bandpass calibrator, and J1154$-$350 as the complex gain calibrator. We flagged and calibrated the data using standard reduction techniques in CASA, and thereafter used the Inter-University Institute for Data Intensive Astronomy (IDIA) `processMeerKAT` software pipeline[^7] (Collier, Sekhar, Frank, Taylor, et al., in prep.) to perform imaging and two rounds of phase self-calibration followed by one round of amplitude and phase self-calibration. No radio source was visible at the GRB position in the images from the first four epochs, so we report upper limits as three times the RMS noise at the afterglow position, calculated using the CASA task `imstat`. We detected the afterglow in our fifth and final epoch image and measured the flux density using `imfit`.

We report all X-ray, optical and radio flux measurements in Table [3](#tab:flux).

# Multi-wavelength modelling

We interpret our observations within the synchrotron forward shock model of GRB afterglows. In this model, a collimated relativistic blast wave sweeps up the surrounding circumburst medium forming a shock front in which electrons are accelerated into a power-law distribution in energies characterised by a spectral index $p$. The electron distribution gives rise to a multi-segment broken power-law emission spectrum consisting of spectral breaks at three frequencies: $\nu_m$ is the frequency of the spectral break corresponding to electrons with the minimum energy in the distribution; $\nu_c$ is that of the break above which electrons are undergoing cooling; and $\nu_a$ is the frequency of the break below which synchrotron radiation is self-absorbed. The evolution of the spectral breaks is dictated by the dynamics of the blast wave, for which we assume the (cite: BM1976) solution for a relativistic explosion. The synchrotron forward shock model is described in detail in (cite: Sari1998) and (cite: Granot2002). We follow the convention with $F_{\nu}\propto t^{\alpha}\nu^{\beta}$ henceforth.

## The millimeter rebrightening

The most striking feature of our multi-wavelength data set is the ALMA 97.5 GHz light curve, as shown in Figure [1](#fig:ALMA_LC). After five epochs of clear fading behaviour the light curve begins to rebrighten at 8.2 days post-trigger, rising to a peak at 18.1 days before declining again. This rebrightening by a factor of $\approx2$ in flux is, to our knowledge, the first such rebrightening seen in a millimeter afterglow light curve. Although the light curve behaviour is unusual, the 3 millimeter luminosity of GRB 210702A is typical when compared to other long GRB millimeter light curves (Figure [2](#fig:3mm_comparison)).

To characterise this light curve further, we fit a model comprising the sum of a power-law (PL) and a smoothly broken power-law (BPL), where the BPL follows the functional form $$\begin{equation}
\label{eq:BPL}
    F(t)=F_0 \left[\left(\frac{t}{t_b}\right)^{-\alpha_1\omega}+\left(\frac{t}{t_b}\right)^{-\alpha_2\omega}\right]^{-1/\omega},
\end{equation}$$ with $F_0$ as a normalising flux, $\alpha_1$ and $\alpha_2$ as the pre- and post-break temporal indices, $t_b$ as the break time, and $\omega$ as a smoothness parameter which sets the sharpness of the break. Larger values of $\omega$ ($>1$) correspond to a sharper break in the light curve. The results of our light curve fit in Table [1](#tab:LC_fit) show that the power-law component decays with $\alpha_\mathrm{97.5~GHz}=-1.03\pm0.02$. For the broken power-law component we find that a smoother break with $\omega=1$ results in a better fit than sharper breaks. The rising and decaying indices for this component are $\alpha_1=3.04\pm0.78$ and $\alpha_2=-3.41\pm1.60$ with a break time of $t_b=19.5\pm4.3$ days. On the other hand, direct fits to the rising and decaying segments (Figure [1](#fig:ALMA_LC)) result in $\alpha_\mathrm{97.5GHz,rise}=0.95$ and $\alpha_\mathrm{97.5GHz,decay}=-1.67\pm0.17$, respectively, while the 343.5 GHz light curve decays with $\alpha=-1.31$. We return to this in our investigation of the millimeter rebrightening in Section [5](#sec:mm_rebrightening).

![](ALMA_LC.pdf)

| Parameter        |     Value      |
|:-----------------|:--------------:|
| PL $\alpha$      | $-1.03\pm0.02$ |
| BPL $\alpha_1$   | $3.04\pm0.78$  |
| BPL $\alpha_2$   | $-3.41\pm1.60$ |
| BPL $t_b$ (days) | $19.50\pm4.33$ |

: ALMA 97.5 GHz light curve fit parameters

![](3mm_comparison.pdf)

## X-ray and UV/optical temporal evolution

The X-ray and UV/optical band data show declining light curves throughout our observations. Fitting the MeerLICHT and *Swift* UV/optical data separately with power-laws in time, we find that the optical temporal decay rate during the MeerLICHT observations is $\alpha=-1.23\pm0.02$ while the decay rate during the *Swift* UV/optical observations is $\alpha=-1.37\pm0.02$ (see Figure [3](#fig:UV_opt_LCs)), indicating a steepening in the optical decay rate between the two sets of observations. The residuals from the power-law fit to the MeerLICHT observations show evidence for the steepening occurring at $\approx0.016$ days.

We measure the $u$- to $v$-band spectral index during each set of observations by interpolating our light curve fits in Figure [3](#fig:UV_opt_LCs) to a common time, and find that the MeerLICHT in-band spectral index of $\beta_\mathrm{MeerLICHT}=-1.42\pm0.15$ is consistent with the UVOT in-band spectral index of $\beta_\mathrm{UVOT}=-1.46\pm0.11$. To characterise the optical temporal evolution further, we create a composite $b$-band light curve by transforming the UVOT $u$, $b$ and $v$ bands along with the MeerLICHT $u$, $g$ and $q$ bands to a common observing frequency equivalent to the UVOT $b$-band using a spectral index of $\beta=-1.44$, the average spectral index from our spectral fits to the MeerLICHT and UVOT data. Since the optical light curve steepens between the MeerLICHT and UVOT observations, we fit the light curve with a smoothly broken power-law following Equation [\[eq:BPL\]](#eq:BPL). The best-fit light curve (see Figure [4](#fig:LC_fits)) has pre- and post-break temporal indices of $\alpha_1=-1.05\pm0.16$ and $\alpha_2=-1.42\pm0.01$, respectively, favouring a sharper break ($\omega\approx29$) with a break time of $t_b=0.017\pm0.002$ days which is consistent with the evidence for a break seen in our residuals from the power-law fit to the MeerLICHT data. The steepening of the light curve to $\alpha=-1.42\pm0.01$ is unlikely to be due to a jet break since post-jet break decay is predicted to decay as $t^{-p}$ with $p$ between 2 and 3 (cite: Sari1999). If lateral spreading of the jet is not significant, the predicted steepening is $\Delta\alpha=-0.75$ in an interstellar medium-like (ISM) circumburst medium or $\Delta\alpha=-0.5$ in a stellar-wind medium (cite: Granot2002). Both of these cases are still steeper than the measured $\Delta\alpha=-0.37\pm0.16$, though the wind case does agree within the errors. If the temporal steepening is due to the passage of the cooling break we would expect a change of $\Delta\alpha=-0.25$ which is shallower than the measured $\Delta\alpha=-0.37\pm0.16$, but also consistent within the errors. We return to this in Section [3.3](#subsec:wind).

The X-ray light curve consists of two segments separated by a period during which *Swift* had to slew away. Fitting each segment with a simple power-law (see Figure [4](#fig:LC_fits)), we find that the early WT-mode decay rate of $\alpha_\mathrm{WT}=-1.00\pm0.02$ is consistent with the early optical evolution, while the later PC-mode decay rate of $\alpha_\mathrm{PC}=-1.44\pm0.01$ is in very close agreement with the post-break optical decay rate of $\alpha_2=-1.42\pm0.01$. Although the pre- and post-break X-ray and optical decay rates are very similar and may suggest achromatic X-ray to optical evolution, we note that the X-ray to optical $b$-band spectral index was $\beta_\mathrm{O-X}=-0.91$ at 0.004 days and $\beta_\mathrm{O-X}=-0.77$ at 0.1 days, therefore ruling out achromatic evolution between the two bands. We return to this in Section [3.3](#subsec:wind) below.

![](LC_fits.pdf)

## Stellar wind medium

We now investigate whether a standard forward shock model can explain the observed spectral and temporal characteristics of our X-ray, UV/optical and early millimeter data. From 0.2–10 days our X-ray and UV/optical light curves decline as power-laws with similar indices of $\alpha~\approx-1.43$, suggestive of a ‘normal’ afterglow decay and that both bands may lie within the same spectral regime. During slow-cooling ($\nu_m<\nu_c$) there are two spectral regimes to consider for our declining X-ray and optical light curves: either $\nu_m<\nu_c<\nu_\mathrm{O}<\nu_\mathrm{X}$ or $\nu_m<\nu_\mathrm{O}<\nu_\mathrm{X}<\nu_c$.

In the regime with $\nu_m<\nu_c<\nu_\mathrm{O}<\nu_\mathrm{X}$ we expect a spectral index of $\beta=-p/2$ and a temporal decay rate of $\alpha=(2-3p)/4$, regardless of the circumburst medium. Using the average of the observed optical and X-ray temporal indices of $\alpha=-1.43\pm0.01$ results in $p=2.57\pm0.01$ and a spectral index of $\beta=-1.28\pm0.01$. Correcting our optical SED derived from the *Swift*/UVOT light curve for a Galactic extinction of $A_V=0.3271$ mag along the line of sight (cite: SF2011), the $b$- to $r$-band spectral index of $\beta_\mathrm{O}=-0.63\pm0.08$ is clearly in disagreement with the predicted spectral index of $\beta=-1.28\pm0.01$, ruling out this scenario.

In the regime with $\nu_m<\nu_\mathrm{O}<\nu_\mathrm{X}<\nu_c$ we expect a spectral index of $\beta=(1-p)/2$ and temporal indices of $\alpha_\mathrm{ISM}=3(1-p)/4$ for an ISM-like circumburst medium or $\alpha_\mathrm{wind}=(1-3p)/4$ for a stellar wind medium. For the ISM case we derive $p=2.91\pm0.01$ and a spectral index of $\beta=-0.96\pm0.01$ from our temporal index of $\alpha=-1.43\pm0.01$. This was the scenario favoured by (cite: Anderson2023). Although this spectrum agrees with the PC-mode X-ray spectral index of $\beta_\mathrm{X}=-0.95\pm0.03$ (Section [2.2](#sec:XRT)), it is steeper than the optical index of $\beta_\mathrm{O}=-0.63\pm0.08$ and the optical-to-X-ray index of $\beta_\mathrm{O-X}=-0.77$ calculated at 0.1 days. For the stellar wind case we derive $p=2.24\pm0.01$ from our observed light curve evolution and an expected spectral index of $\beta=-0.62\pm0.01$, which is in close agreement with the optical spectral index of $\beta_\mathrm{O}=-0.63\pm0.08$ and therefore our preferred scenario. With $p=2.24\pm0.01$ the predicted spectral index above the cooling break is $\beta=-1.12\pm0.01$, which is slightly steeper than our X-ray spectral index of $\beta_\mathrm{X}=-0.95\pm0.03$. In a stellar wind medium, the frequency of the cooling break, $\nu_c$, rises as $t^{1/2}$. A smooth cooling break (cite: Uhm2014) with $\nu_c$ close to the X-ray band is a possible explanation for the similar temporal indices of the X-ray and optical bands, but steeper X-ray spectrum compared to the optical.

Further support for a stellar wind medium is found when considering the early millimeter data. At the time of the first ALMA 97.5 GHz detection at 1.17 days, we measure a 97.5 GHz to optical $r$-band spectral index of $\beta_\mathrm{97.5GHz-O}=-0.47$, which is shallower than the optical in-band spectral index $\beta_\mathrm{O}=-0.63\pm0.08$ and optical-to-X-ray index of $\beta_\mathrm{O-X}=-0.77$. Moreover, extrapolating our 97.5 GHz light curve fit to the time of the first 343.5 GHz detection at 1.06 days yields a 97.5 GHz to 343.5 GHz spectral index of $\beta_\mathrm{97.5-343.5GHz}=-0.31$, indicating that the spectrum is flattening off towards lower frequencies and that $\nu_m$ lies below the millimeter bands. In an ISM medium the peak flux of the synchrotron spectrum remains constant with time, whereas in a stellar wind medium the peak flux declines as $t^{-1/2}$. Assuming that $\nu_m$ is within the 97.5 GHz band at the time of our first detection at 1.17 days, the corresponding peak flux is $F_{\nu_m}\approx2$ mJy. Our $u$-band detection at 0.004 days has a flux density of $F_u\approx42$ mJy, which is more than an order of magnitude larger than our constraint on the peak flux from our millimeter data at 1.17 days and therefore clearly rules out an ISM medium.

The peak frequency for both an ISM and wind medium evolves as $t^{-3/2}$. If we assume a stellar wind medium in which $\nu_m$ is close to the 97.5 GHz band with a flux of $F_{\nu_m}\approx2$ mJy at 1.17 days, we expect the peak flux to be $F_{\nu_m}\approx34$ mJy at 0.004 days and $\nu_m$ to be at a frequency $\nu_m\approx4.9\times10^{14}$ Hz, which corresponds to the optical $r$-band. Since the $u$ band must be above $\nu_m$ due to the declining optical light curve and negative spectral slope observed in the MeerLICHT data, $\nu_m$ in the $r$-band at 0.004 days is consistent with our observations. The expected peak flux of $F_{\nu_m}\approx34$ mJy is only a factor 1.2 smaller than our $u$-band detection of $F_u\approx42$ mJy at this time, and so we still regard a stellar wind medium as being consistent with our observations.

The UV/optical and millimeter light curves initially have temporal decay rates with $\alpha\approx-1$ compared to the later decay rate of $\alpha\approx-1.43$ observed in the optical and X-rays. This shallower decay might be due to the proximity of $\nu_m$ to the observing band, causing the light curve to decay less steeply initially before transitioning to the expected decay rate. The shallow decay with $\alpha=-1.00\pm0.02$ observed in the X-rays prior to 0.01 days, however, cannot be explained via this interpretation since $\nu_m$ should be far below the X-ray band at this time. An explanation for the shallower X-ray decline could be continuous energy injection into the GRB blast wave which results in an observed plateau or shallow decay, an effect which has been observed extensively in X-ray light curves (cite: Zhang2006; Nousek2006).

## Radio evolution

We have shown in the previous section that the optical, X-ray data after 0.01 days, and millimeter data prior to the millimeter wavelength rebrightening can be explained with a standard forward shock model in a stellar wind medium with $p\approx2.2$. We now consider the implications of our lower frequency radio data.

Figure [5](#fig:Radio_LC) shows our radio light curves separated by observing band and instrument. We have extracted SEDs at seven epochs indicated by the vertical grey regions, which are shown in Figure [6](#fig:Radio_SEDs). The ALMA 97.5 GHz rebrightening begins at 8.2 days and rises to a peak at 18.1 days. Prior to the start of the rebrightening at 8.2 days we assume that the rebrightening does not have a significant effect on the light curves nor SEDs. The early ATCA observations obtained by (cite: Anderson2023) allow us to construct an SED at the time of our first ALMA observations by interpolating the light curves using their power-law behvaiour. The Epoch 1 SED shows a clearly rising spectrum from 5.5 GHz to 97.5 GHz measurement with a spectral index of $\beta_\mathrm{5.5-97.5GHz}=0.93\pm0.06$. Such a rising spectrum is suggestive of optically thick synchrotron emission, which we use to place a tentative constraint on the self-absorption break of $\nu_a\approx97.5$ GHz at 1.17 days. From our arguments in Section [3.3](#subsec:wind), this places $\nu_a$ very close to $\nu_m$ at this time. In Section [4](#subsec:modelling) below we will demonstrate that no standard forward shock model can accommodate such a high self absorption frequency.

Although $\beta_\mathrm{5.5-97.5GHz}=0.93\pm0.06$ is not as steep as the theoretically-predicted slope of $\nu^2$ for synchrotron self-absorbed emission, a smooth self-absorption break may account for the shallower measured slope. The rising ATCA light curves at $t<8$ days (see Figure [5](#fig:Radio_LC)) with $\alpha\approx1$ are also suggestive of optically thick emission, since the predicted temporal evolution below $\nu_a$ is $t^1$ in a stellar wind medium. By the time of our Epoch 2 SED at 3.5 days we see a flat spectrum from 16.7 to 97.5 GHz. This allows us to place a constraint on the self-absorption break of $\nu_a<16.7$ GHz, and that $\nu_a$ must have evolved faster than $t^{-1.6}$ between these two epochs. Such a fast evolution of the self-absorption break is inconsistent with any known evolution. The declining spectrum from 97.5 to 343.5 GHz appears to be consistent with $\nu_m$ having passed through the millimeter bands as demonstrated in Section [3.3](#subsec:wind) above. The Epoch 3 SED at 6.6 days provides a second clear case of a self-absorbed spectrum with a spectral index $\beta=1.03\pm0.16$ measured from 5.5 to 16.7 GHz, and a self-absorption break at $\nu_a\approx16.7$ GHz. The fact that the self-absorption break evolved as $t^{-1.6}$ between Epochs 1 and 2 and not at all between Epoch 2 and 3 demonstrates that the optically-thick radio data cannot be reconciled within any standard forward shock model.

Throughout the millimeter rebrightening, our radio light curves do not show obviously achromatic behaviour. The low frequency 1.4, 5.5 and 9 GHz bands rise and even peak when the 97.5 GHz light curve is rising and peaks, whereas the higher frequency bands at 16.7 and 21.2 GHz do not show simultaneous rises. The 34 GHz band appears to rise slowly at the start of the 97.5 GHz rebrightening but peaks later at $\approx30.6$ days. We note that the omission of higher frequency data from our third epoch of ATCA data at 10.4 days (Section [2.4.2](#subsec:ATCA)) leads to a loss of possibly valuable temporal information. Following the 97.5 GHz peak, all of the radio light curves besides the 34 and 1.28 GHz light curves decline. Since the MeerKAT band is in the optically thick regime throughout our observations (see Figure [6](#fig:Radio_SEDs)), the rising L band light curve appears consistent with rising self-absorbed synchrotron emission (cite: Granot2002).

Before, during, and after the rebrightening, our radio SEDs show complex behaviour. Epoch 4 coincides in time with the 97.5 GHz peak and the fluxes measured in that epoch show tentative evidence for an additional spectral component peaking at 97.5 GHz as seen in the rising spectrum from 16.7 to 97.5 GHz. The Epoch 5 and 6 SEDs show similar peaks at 34 GHz and 21.2 GHz, respectively. However, our radio SEDs are characterised by a number of sharp jumps which may not be intrinsic to the source since we do not expect synchrotron radiation from a relativistic blast wave – even with additional spectral components – to result in such sharp jumps in the spectrum. It may be the case that the small scale features in our light curves and SEDs are a result of unaccounted-for systematic uncertainties from the calibration of our ATCA data or due to interstellar scintillation (Section [6.2](#subsec:discuss_FS_models)). We discuss our radio data taken during and after the rebrightening further in Section [5](#sec:mm_rebrightening).

![](Radio_LC.pdf)

![](Radio_SEDs.pdf)

# Afterglow modelling with ScaleFit

Constraints on the three spectral break frequencies ($\nu_a$, $\nu_m$, $\nu_c$) and the peak flux of the synchrotron spectrum can be used to derive intrinsic blast wave parameters of the forward shock and may also be used to test whether a standard forward shock model is compatible with our data. In Section [3.3](#subsec:wind) we constrained the peak flux to $F_{\nu_m}\approx2$ mJy at 1.17 days, the time of our first 97.5 GHz observation. We also have $\nu_m$ close to the 97.5 GHz band at this time, so $\nu_m\approx90$ GHz. We expect the cooling break to cross the X-ray band during our PC-mode observations, so $\nu_c\approx2.4\times10^{17}$ Hz at 0.5 days. Our Epoch 1 radio SED places a constraint on the self-absorption frequency of $\nu_a\approx97.5$ GHz at 1.17 days. Solving the system of four equations describing the locations of the spectral breaks and their flux densities in a wind medium (see Table 2 in (cite: Granot2002)) results in an unphysical value for the fraction of shock internal energy partitioned to electrons of $\epsilon_e>1$, which is driven primarily by our constraint on the self-absorption break. We therefore do not expect a standard wind-medium forward shock model to be able to account for the observed optically thick radio emission prior to the 97.5 GHz rebrightening at 8.2 days. We note that similar incompatibilities with standard forward shock models resulting from radio observations have been observed in other GRB afterglows (cite: Marongiu2022; deWet2023a; Laskar2023; Schroeder2023). We discuss this further in Section [6.2](#subsec:discuss_FS_models).

We perform theoretical modelling using the `ScaleFit` software package (cite: Ryan2015; Aksulu2020; Aksulu2022), which is based on the `BoxFit` set of high-resolution hydrodynamic simulations of GRB explosions (cite: VanEerten2012). `ScaleFit` generates afterglow spectra and light curves of forward shock emission in both ISM or stellar wind environments during the deceleration phase after reverse shock crossing, and can take into account the jet break effect as well as the non-relativistic transition. Non-standard effects such as reverse shock emission, energy injection, plateaus, or flares, however, are not included. `ScaleFit` accepts 10 free parameters: the isotropic-equivalent energy of the blast wave $E_\mathrm{K,iso}$, circumburst density $n_0$[^8], opening angle of the jet $\theta_j$, electron energy distribution spectral index $p$, fraction of accelerated electrons within the shock $\xi_N$, fractions of shock internal energy distributed to electrons and magnetic fields $\epsilon_e$ and $\epsilon_B$, burst redshift $z$, luminosity distance $d_L$, and observer angle relative to the jet axis $\theta_\mathrm{obs}$.

We fix the burst redshift to $z=1.160$ and the luminosity distance to the value computed using our adopted cosmology, $d_L=2.52\times10^{28}$ cm. We assume that the observer is looking directly down the axis of the jet ($\theta_\mathrm{obs}=0$) and that the fraction of shock-accelerated electrons is unity despite the fact that $\xi_N$ is degenerate with respect to the parameters $\{E_\mathrm{K,iso},n_0,\epsilon_e,\epsilon_B\}$, as shown by (cite: Eichler2005). To account for Galactic dust extinction we correct our UV/optical data using the (cite: Fitzpatrick1999) Milky Way extinction law with $R_V=3.1$ and $A_V=0.3271$ mag. Furthermore, we adopt the Small Magellanic Cloud (SMC) extinction curve from (cite: Pei1992) to account for possible host galaxy extinction, which is a free parameter in our modelling.

We conduct a Markov Chain Monte Carlo (MCMC) exploration of our `ScaleFit` parameter space using the `emcee` Python package (cite: Foreman2013) following the implementation described in detail in (cite: deWet2023b). The Lyman limit of 912 Å at the host redshift lies squarely within the $uvw2$ ultraviolet band so these flux measurements are likely to be severely affected by photoelectric absorption. We therefore exclude these data from our modelling, along with the radio observations following the start of the 97.5 GHz rebrightening at 8.2 days. We also exclude the early-time X-ray data ($t<0.01$ days), the first epoch of ATCA data ($t\approx0.5$ days), and the lower frequency ($<16.7$ GHz) radio data at 6.6 days since we do not expect our model to be able to account for these data following the arguments in Sections [3.3](#subsec:wind) and [3.4](#subsec:radio). We assume a spherical jet ($\theta=\pi/2$) since our observations show no clear evidence for a jet break.

The results of our modelling are presented in Table [2](#tab:MCMC) and Figure [7](#fig:MCMC), while the light curves corresponding to the highest-likelihood model are shown in Figure [8](#fig:model_LCs). This model has $p=2.27$ which is close to the value of $p=2.24$ derived from our late-time optical and X-ray light curves in Section [3.3](#subsec:wind). The spectrum is in fast cooling with $\nu_c<\nu_m$ until $\nu_m$ crosses $\nu_c$ at 0.0011 days at a frequency of $\nu\approx10^{16}$ Hz which is between the optical and X-ray bands. The cooling break $\nu_c$ begins crossing the X-ray band midway through our PC-mode observations which explains the steeper observed X-ray spectral index of $\beta_\mathrm{X}=-0.95\pm0.03$ compared to the optical index of $\beta_\mathrm{O}=-0.63\pm0.08$, while the similar temporal decay observed in both bands is a result of the smooth cooling break. By $\approx0.01$ days $\nu_m$ has passed through all of the optical bands, consistent with the observed steepening of the optical light curve from $\alpha_\mathrm{O}=-1.05$ to $\alpha_\mathrm{O}=-1.44$ at 0.017 days as seen in Figure [4](#fig:LC_fits). At the time of our first ALMA observations we have $\nu_m\approx330$ GHz which is close to the 343.5 GHz ALMA band. The shallow decay observed in the early optical and millimeter light curves is a result of the proximity of $\nu_m$ to the observing band, consistent with our arguments in Section [3.3](#subsec:wind). As we expected, the optically thick spectra observed in the Epoch 1 and 3 radio SEDs are incompatible with our highest-likelihood model, as shown in Figure [9](#fig:model_SEDs). At 6.6 days the self-absorption frequency is at $\nu_a\approx110$ MHz, an order of magnitude below the observed break at 16.7 GHz. We return to this in Section [6.2](#subsec:discuss_FS_models).

No jet break is seen in our data prior to the start of the millimeter rebrightening at 8.2 days, so we can place a lower limit on the opening angle using the inverted form of Equation 5 from (cite: Chevalier2000): $$\begin{equation}
    \theta_j = 0.17\left(\frac{1+z}{2}\right)^{-1/4}E_\mathrm{52}^{-1/4}A_\star^{1/4}t_j^{1/4},
\end{equation}$$ where $\theta_j$ is in radians, $E_\mathrm{52}$ is the isotropic-equivalent kinetic energy in units of $10^{52}$ erg, and $t_j$ is the jet break time in days. We calculate a lower limit of $\theta_j\gtrsim1.1$ deg, which is consistent with the sample range of $\theta_j=2.5\pm1.5$ degrees found by (cite: Wang2015). The corresponding lower limit on the beaming correction is $f_b=(1-\cos\theta_j)\gtrsim1.8\times10^{-4}$, resulting in a beaming-corrected $\gamma$-ray energy of $E_\gamma\gtrsim1.7\times10^{50}$ erg and a kinetic energy of $E_\mathrm{K}\gtrsim5.2\times10^{50}$ erg. We calculate the radiative efficiency using $\eta_\gamma=E_{\gamma,\mathrm{iso}}/(E_{\gamma,\mathrm{iso}}+E_\mathrm{K,iso})$ and find $\eta_\gamma = 24.6$%.

| Parameter | Highest-likelihood model | MCMC results |
|:---|:--:|:--:|
| $p$ | 2.27 | $2.28^{+0.01}_{-0.01}$ |
| $E_\mathrm{K,iso}$ ($10^{53}$ erg) | 29.0 | $30.7^{+4.5}_{-3.1}$ |
| $A_\star$ | $6.3\times10^{-3}$ | $4.7^{+1.6}_{-2.1}\times10^{-3}$ |
| $\epsilon_e$ | $9.7\times10^{-3}$ | $8.7^{+1.3}_{-2.1}\times10^{-3}$ |
| $\epsilon_B$ | $1.5\times10^{-1}$ | $2.4^{+3.7}_{-1.0}\times10^{-1}$ |
| $A_{V,\mathrm{host}}$ (mag) | 0.009 | $0.011^{+0.010}_{-0.007}$ |
| $t_j$ (days) | $\gtrsim8.2$ | \- |
| $\theta_j$ (deg) | $\gtrsim1.1$ | \- |
| $E_\mathrm{K}$ ($10^{50}$ erg) | $\gtrsim5.2$ | \- |
| $E_\gamma$ ($10^{50}$ erg) | $\gtrsim1.7$ | \- |

: Forward shock parameters

![](WIND_fancy_corner.pdf)

![](model_fit.pdf)

![](SEDs.pdf)

# Explanations for the millimeter rebrightening

We consider a number of mechanisms that may give rise to a rebrightening at radio frequencies, including supernova emission, a counter jet, a density enhancement of the surrounding medium, interstellar scintillation, a two-component jet, energy injection, and reverse shock emission.

## Supernova emission

(cite: BarniolDuran2015) investigated the possibility of detecting radio emission from the highly-energetic Type Ic supernovae that are expected to accompany most long GRBs, and found that the emission from the shocked external medium swept up by the supernova blast wave should peak a few tens of years after the explosion, much later than our observed peak at 18.1 days. Furthermore, the luminosities of supernovae observed at millimeter wavelengths are generally 2–4 orders of magnitude fainter than those of GRB afterglows (cite: Eftekhari2022). We therefore rule out supernova emission as a possible cause for the rebrightening in GRB 210702A.

## Counter jet

Once the GRB blast wave transitions into the non-relativistic regime, a bump in radio light curves may be expected from the receding counter jet, with simulations showing that the emission should peak more than $\sim1000$ days after the GRB (cite: Zhang2009). The decelerating jet will experience a jet break prior to the non-relativistic transition. The lack of a jet break observed in our data therefore rules out a counter jet as a viable explanation.

## Density enhancement

Long GRBs offer a natural mechanism for producing a variable circumburst density since their progenitors are massive stars which produce stellar winds and undergo significant mass loss preceding their death. Several studies, however, have shown that even large density variations are unlikely to produce significant changes in the afterglow emission (cite: Nakar2007; Vaneerten2009; Gat2013; Geng2014).

## Interstellar scintillation

Interstellar scintillation (ISS) due to inhomogeneities in the Galactic free electron density have been observed at radio wavelengths in a number of GRB afterglows (cite: Goodman1997; chandra2008; Vanderhorst2014; Greiner2018; Alexander2019). (cite: Anderson2023) explored ISS as an explanation for the early, rapid variability in the radio light curves of GRB 210702A and found a transition frequency of $\nu_0=7.66$ GHz for the GRB line of sight. Our millimeter observations are more than an order of magnitude higher in frequency than this transition frequency and at a much later time so that the effects of ISS should be negligible. Our calculation of the modulation index of $m\lesssim2.5\%$ throughout our 97.5 GHz observations confirms that ISS is not relevant, though it may be relevant at lower frequencies (see Section [6.2](#subsec:discuss_FS_models)). We rule out ISS as a viable explanation for the millimeter rebrightening.

## Two-component jet

A two-component jet has been invoked to explain the afterglows of several GRBs where a standard forward shock model does not suffice (cite: Berger2003; Racusin2008; Vanderhorst2014; Sato2023). A faster, more narrowly-collimated inner jet gives rise to the early optical and X-ray emission while a slower, wider jet gives rise to later emission. If the rebrightening is due to forward shock emission from a wider jet, we would require a jet break from the inner jet near the start of the rebrightening around 8.1 days, otherwise a very steep rise of $\alpha\approx3$ (from our light curve fit in Section [3.2](#subsec:temporal)) would be required which is not possible from standard forward shock emission. No jet break is seen in our X-ray light curve, so this model appears to be disfavoured.

## Energy injection

There are two physical forms of energy injection that may give rise to a rebrightening in afterglow light curves. The first involves a long-lasting central engine which injects a Poynting flux into the blast wave, such as a spinning-down millisecond magnetar (cite: Dai1998; Zhang2001a). The luminosity of the central engine is usually given as a power-law in time beginning at a time $t_0$ and defined by the power-law index $q$: $L(t)=L_0(t/t_0)^{-q}$. The blast wave energy will only increase substantially when $q<1$, with the total energy increasing as $E_\mathrm{tot}\propto t^{1-q}$. The second form of energy injection invokes an impulsive central engine injection of a stratified ejecta with a power-law distribution in the bulk Lorentz factor: $M(>\gamma)\propto  \gamma^{-s}$ (cite: Rees1998; Sari2000). It is impossible to physically distinguish the two scenarios from afterglow observations since both forms can be made equivalent through a relationship between the $q$ and $s$ parameters (cite: Zhang2006). During the period of energy injection the light curves within each spectral regime will be altered according to the value of $q$ or $s$. Thereafter, the afterglow will evolve as a blast wave with the new, increased kinetic energy.

We test the energy injection scenario by making use of the closure relations for energy injection within the $q$-formalism from (cite: Zhang2006). At the start of the rebrightening the 97.5 GHz band is within the spectral regime with $\nu_m<\nu_\mathrm{97.5GHz}<\nu_c$. The appropriate closure relation in a wind medium is $\alpha=\frac{(2-2p)-(p+1)q}{4}$. Using our light curve rising index of $\alpha_\mathrm{97.5GHz,rise}=0.95$ and a value of $p=2.28\pm0.01$ derived from our theoretical modelling, we calculate a value of $q=-1.88$. The blast wave energy increases as $E_\mathrm{K,iso,1}=E_\mathrm{K,iso,0}\left(t_1/t_0\right)^{1-q}$ over the period of energy injection. We take $t_0$ and $t_1$ as the times corresponding to the start and peak of the rebrightening at 8.2 and 18.1 days, respectively. We find that the blast wave energy increases by a factor of $\approx10$ over the course of the rebrightening.

Taking our forward shock model from Section [4](#subsec:modelling) as the starting point, we introduce a period of energy injection in which the kinetic energy of the blast wave increases as $t^{1-q}$ between 8.2 and 18.1 days. We keep all other forward shock parameters the same. We exclude the lower frequency radio bands since there is no standard forward shock model prior to the rebrightening that can accommodate these data. The resulting model results in an achromatic rebrightening across all bands. The model can adequately capture the 97.5 GHz rebrightening, but does not fully capture the behaviour in the higher frequency bands (Figure [10](#fig:E_injection)). As discussed in Section [3.4](#subsec:radio), however, possible unaccounted-for systematic uncertainties from the calibration of our ATCA data prevents us from completely excluding this scenario.

![](E_injection_RS.pdf)

## Reverse shock

We now consider whether the 97.5 GHz rebrightening is caused by emission from a reverse shock (RS). There are two physical mechanisms that can produce RS emission: the first is a standard RS related to the forward shock (FS) that is produced by a shock wave moving back through the jet ejecta; the second is a RS produced by the late-time collision of a shell ejected by the GRB central engine. For both cases, the RS will emit synchrotron radiation characterised by its own set of spectral break frequencies and peak flux: $\nu_{a,\mathrm{r}}$, $\nu_{m,\mathrm{r}}$, $\nu_{c,\mathrm{r}}$, and $F_{\nu_{m,\mathrm{r}}}$. For a standard RS, the RS and FS parameters are related at the deceleration (or shock crossing) time $t_\mathrm{dec}$, and can therefore be used to derive the ejecta Lorentz factor and magnetization. After the deceleration time, the flux above $\nu_{c,\mathrm{r}}$ is negligible since electrons are no longer accelerated within the ejecta. The evolution of the RS spectral breaks depends on whether the shock is relativistic or Newtonian in the frame of the unshocked ejecta. In the Newtonian case the spectral evolution depends on an additional parameter $g$ which dictates the profile of the shocked ejecta with $\gamma\propto r^{-g}$, and where we expect $1/2\lesssim  g\lesssim3/2$ from theoretical arguments (cite: Meszaros1999; Kobayashi2000).

If the 97.5 GHz rebrightening is caused by a standard RS related to the FS, our first optical detection at 0.004 days allows us set an upper limit on the deceleration time of $t_\mathrm{dec}<0.004$ days since we were able to model all of the optical emission with a FS (Section [4](#subsec:modelling)) which must have decelerated prior to this time. After shock crossing, it is only possible to obtain a rising and falling light curve through the passage of a spectral break, which must be $\nu_{a,\mathrm{r}}$ for a RS in a wind medium (cite: Zou2005). Regardless of the ordering of the spectral breaks, we find that the RS emission in this case would outshine the detected optical emission at 0.004 days by several orders of magnitude, ruling out a standard RS scenario.

Next we consider RS emission from the violent collision of two ejecta shells (cite: Zhang2002; Lyutikov2017; Lamberts2018). Such a scenario has been used to model GRBs 140304A and 210672A (cite: Laskar2018a; Schroeder2023). A requirement for a violent collision is that the second shell is moving much faster than the initial shell (which is responsible for the observed FS emission) at the collision time ($t_\mathrm{col}$), so that $\Gamma_2\gg\Gamma_1$. Furthermore, we rely on the assumptions that the energy of the initial shell does not increase enough to cause an increase in the FS emission and that FS emission from the second shell is negligible compared to the RS emission (cite: Zhang2002). The RS emission from the second shell begins forming when the two shells collide at $t_\mathrm{col}$, and peaks once the RS has crossed the ejecta and fully decelerated at the deceleration time $t_\mathrm{dec}$. We choose to associate the collision time with the beginning of the rise in the 97.5 GHz light curve at 8.2 days, and the deceleration time with the peak in the light curve at 18.1 days. For a standard ordering of spectral breaks ($\nu_{a,\mathrm{r}}<\nu_{m,\mathrm{r}}<\nu_{c,\mathrm{r}}$), we find that a relativistic RS in which $\nu_{m,\mathrm{r}}$ crosses the 97.5 GHz band shortly after shock crossing can provide an adequate fit to our higher frequency radio data (Figure [10](#fig:E_injection)). At the shock crossing time, this model has $\nu_{m,\mathrm{r}}\approx 300$ GHz, $\nu_{a,\mathrm{r}}\lesssim16.7$ GHz, $\nu_{c,\mathrm{r}}\gtrsim10^{14}$ Hz, and $F_{\nu_{m,\mathrm{r}}}\approx1$ mJy. We note, however, that this is not a unique model since two of the break frequencies ($\nu_{a,\mathrm{r}}$, and $\nu_{c,\mathrm{r}}$) are not well-constrained. Futhermore, Newtonian RS models with both standard and non-standard orderings of spectral breaks can also accommodate the data.

# Discussion

## Radio rebrightenings

Similar radio rebrightenings to the one observed in GRB 210702A have been observed in XRF 050416A and GRB 210726A (cite: Soderberg2007; Schroeder2023). Radio observations of XRF 050416A at 1.43, 4.86 and 8.46 GHz showed an unusual flare peaking at $t\sim40$ days which was followed by rapid fading ($t^{-2}$), with the radio spectrum remaining optically thin throughout the observations. (cite: Soderberg2007) regarded a large circumburst density jump or late-time energy injection from a slow-moving shell as the most plausible explanation for the rebrightening. In the energy injection scenario, the decay following the peak should be the same as the asymptotic temporal decay prior to the injection. The fact that the post-peak decay rate of $\alpha\gtrsim-2$ was steeper than the predicted decay led (cite: Soderberg2007) to suggest that a jet break may have occurred on a similar timescale to the energy injection, a trend found by (cite: Laskar2015) in their study of energy injection in GRB afterglows. This scenario is in fact consistent with the post-peak decay rate in GRB 210702A of $\alpha_\mathrm{mm,decay}=-1.67\pm0.17$ being steeper than the predicted decay of $\alpha\approx-1.4$.

More recently, (cite: Schroeder2023) studied the short GRB 210726A and found a radio flare at 6 GHz with a rapid rise between $\approx10-19$ days followed by a rapid decline at 3, 6 and 10 GHz. Energy injection and a reverse shock from a shell collision were regarded as plausible explanations to explain the late-time radio flare. Similar to the energy injection scenario for XRF 050416A, a jet break at the time of the peak of the flare was invoked to explain the steep post-peak temporal index of $\alpha=-2.1\pm0.4$. For the reverse shock shell collision scenario, an X-ray rebrightening at 4.6 days was attributed to the ejection of the shell while the peak of the radio flare was attributed to the deceleration time of the reverse shock.

The most noteworthy difference between these previous studies and ours is that the observed rebrightening in these bursts occurred at centimeter wavelengths whereas the rebrightening in GRB 210702A occurred in the millimeter regime, where scintillation is virtually guaranteed not to play a role (Section [5.4](#subsec:ISS)). Had millimeter data been obtained for these other bursts, it is possible that they may also have shown a rebrightening at millimeter wavelengths. Our observations demonstrate that millimeter light curves can exhibit some of the more complex features commonly seen at higher frequency optical and X-ray bands, and that these features may actually be more widespread than previous observations suggest, given that only a small number of bursts have millimeter follow-up light curves.

## Failure of forward shock model

Prior to the millimeter rebrightening, a standard forward shock model within a stellar wind medium was sufficient to account for the optical, early millimeter and late-time X-ray data in GRB 210702A. The early ($t<0.01$ day) X-ray data was not accounted for by our model, so we attributed the shallower early X-ray decline with $\alpha=-1.00\pm0.02$ to a period of energy injection. The greatest challenge to our model, however, was posed by the lower frequency ($\nu\leq21.2$ GHz) radio data. This includes multiple apparent spectral peaks in the SEDs and a flux suppression relative to the FS model that generally grows and persists for longer with decreasing observing frequency. For the former, one possible mechanism could be ISS, which was shown to be important in ATCA observations during the first day (cite: Anderson2023). We now investigate this further. Using the ISS transition frequency ($\nu_0=7.66$ GHz) and scattering measure ($\mathrm{SM} = 1.06\times10^{-3}$ kpc m$^{-20/3}$) from (cite: Anderson2023) derived using RISS19 (cite: Goodman1997; Hancock2019), we employ the prescription of (cite: Goodman2006) to calculate modulation indices (which represents fractional flux variability), and find that these range from $m\approx20\%$–$100\%$ at $\lesssim18$ days for frequencies between 1 and 22 GHz. While the predicted value of the modulation index decreases rapidly with both time and frequency, we nevertheless find $m\gtrsim50\%$ in the ATCA 5.5 GHz and 9 GHz bands for the full duration of the observations, indicating that at least some of the observed variations at these frequencies may be attributable to ISS. On the other hand, values of $m\lesssim10\%$ at 34 GHz and $m\lesssim2.5\%$ at 97.5 GHz confirm that the millimeter bands are unaffected by ISS and that the observed rebrightening is intrinsic to the source.

For the latter (reduced observed flux relative to the model), we note that the flux suppression in the MeerKAT L band relative to the FS model spans a factor of 3–10 at 8.7–32 days, whereas we expect $m\lesssim40\%$ at 1.3 GHz during this period. As we discussed in Section [3.4](#subsec:radio), this could be alleviated by requiring $1.28~{\rm GHz}\ll\nu_a\approx97.5~{\rm GHz}$ at 1.17 days. However, no standard model can accommodate such a high self-absorption frequency (Section [4](#subsec:modelling)). An additional means of suppressing the radio emission is to invoke a population of thermal, non-accelerated electrons within the shocked region which may lead to an increase in the self-absorption frequency by a factor of $\approx10-100$ (cite: Ressler2017; Warren2018). Such an argument was made for GRB 210731A and GRB 210726A (cite: deWet2023a; Schroeder2023). Nevertheless, the expected rapid evolution of $\nu_a$ in such a case would remain a challenge, and we defer further discussion of this model to future work.

Past sample studies of radio afterglows have shown that standard forward shock models are often incompatible with observations, which contrasts with observations at optical and X-ray afterglows that show general agreement with the forward shock models. (cite: Kangas2020) studied 21 GRBs with multi-wavelength data showing clear evidence for a jet break in their X-ray light curves and found that only half of the bursts had radio afterglows consistent with standard models. Most of the radio light curves were consistent with a single power-law, even after a jet break observed at higher frequencies. (cite: Levine2023) used standard afterglow closure relations to test whether radio observations of 84 GRBs were consistent with predicted temporal and spectral behaviour and, similar to (cite: Kangas2020), found that only roughly half of the sample agreed with expectations. More recently, difficulties in modelling radio data have been encountered in the all time brightest GRB 221009A (cite: Bright2023; Laskar2023; Oconnor2023). (cite: Laskar2023) found that the data could only partially be explained by a forward shock model, with additional emission components needed to explain the radio and millimeter emission, or nonstandard assumptions regarding the basic analytic models of relativistic synchrotron emission such as evolving microphysics parameters or an atypical electron energy distribution. (cite: Gill2023) instead modelled the broadband afterglow with a shallow angular structured jet in which all of the radio emission arises from a reverse shock rather than forward shock emission component. A two-component jet was proposed by other authors (cite: Sato2023; Zhang2023). In summary, radio observations of GRB afterglows are highlighting the need for additional theoretical and modelling efforts in order to explain the data. We leave it to future work to test these alternative scenarios for GRB 210702A.

# Conclusions

We have presented the results of our extensive multi-wavelength follow-up campaign of GRB 210702A, a bright long-duration GRB at $z=1.160$. Our 97.5 GHz ALMA light curve shows a rebrightening beginning at 8.2 days and peaking at 18.1 days, the first such rebrightening seen in a GRB millimeter light curve. Our X-ray, optical and millimeter data taken prior to the rebrightening can be explained by a standard forward shock model in a stellar wind medium with an electron energy spectral index of $p\approx2.27$. The shallow decay with $\alpha\approx-1$ seen in the optical light curve prior to 0.017 days and in the 97.5 GHz light curve prior to the rebrightening we attribute to the proximity of $\nu_m$ to the observing band. The shallow decay with $\alpha\approx-1$ in the X-rays, however, we attribute to a period of energy injection. Our radio light curves from 700 MHz to 34 GHz do not appear to evolve achromatically along with the millimeter rebrightening, though we cannot exclude this for the higher-frequency ATCA data due to inherent uncertainties arising from radio data calibration. Our radio SEDs show clear evidence for synchrotron self-absorbed emission, though we are unable to reconcile our constraints on the self-absorption break with any standard forward shock model. Our radio observations show similar incompatibilities found in modelling other GRBs, such as GRB 221009A (cite: Bright2023; Laskar2023; Oconnor2023), and may require alternative scenarios such as a structured jet or thermal electron population.

We considered a number of scenarios to explain the millimeter rebrightening in GRB 210702A and found that a period of energy injection into the forward shock or a reverse shock from a late-time shell collision are the most plausible mechanisms, yet both scenarios are unable to capture the behaviour seen in the other radio bands. Our observations demonstrate that millimeter light curves can display some of the more complex features seen in X-ray and optical light curves, such as rebrightenings or flares. Further millimeter observations will be required to determine the frequency of such features.

The MeerLICHT consortium is a partnership between Radboud University, the University of Cape Town, the South African Astronomical Observatory (SAAO), the University of Oxford, the University of Manchester and the University of Amsterdam, in association with and, partly supported by, the South African Radio Astronomy Observatory (SARAO), the European Research Council and The Netherlands Research School for Astronomy (NOVA). We acknowledge the use of the Inter-University Institute for Data Intensive Astronomy (IDIA) data intensive research cloud for data processing. IDIA is a South African university partnership involving the University of Cape Town, the University of Pretoria and the University of the Western Cape. SdW and PJG are supported by NRF SARChI Grant 111692. RBD acknowledges support from the National Science Foundation under grant 2107932. TE is supported by NASA through the NASA Hubble Fellowship grant HST-HF2-51504.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. SB is supported by a Dutch Research Council (NWO) Veni Fellowship (VI.Veni.212.058). The research leading to these results has received funding from the European Union’s Horizon 2020 Programme under the AHEAD2020 project (grant agreement number 871158). This work made use of data supplied by the UK Swift Science Data Centre at the University of Leicester. The Australia Telescope Compact Array is part of the Australia Telescope National Facility[^9] which is funded by the Australian Government for operation as a National Facility managed by CSIRO. We acknowledge the Gomeroi people as the Traditional Owners of the Observatory site. We thank the staff of the GMRT that made these observations possible. The MeerKAT telescope is operated by the South African Radio Astronomy Observatory, which is a facility of the National Research Foundation, an agency of the Department of Science and Innovation. GMRT is run by the National Centre for Radio Astrophysics of the Tata Institute of Fundamental Research.

natexlab

(ref: Aksulu2020) Aksulu, M. D., Wijers, R. A. M. J., van Eerten, H. J., & van der Horst, A. J. 2020, MNRAS, 497, 4672, doi: [`10.1093/mnras/staa2297`](http://doi.org/10.1093/mnras/staa2297)

(ref: Aksulu2022) —. 2022, MNRAS, 511, 2848, doi: [`10.1093/mnras/stac246`](http://doi.org/10.1093/mnras/stac246)

(ref: Alexander2019) Alexander, K. D., Laskar, T., Berger, E., et al. 2019, ApJ, 870, 67, doi: [`10.3847/1538-4357/aaf19d`](http://doi.org/10.3847/1538-4357/aaf19d)

(ref: Anderson2023) Anderson, G. E., Russell, T. D., Fausey, H. M., et al. 2023, MNRAS, 523, 4992, doi: [`10.1093/mnras/stad1635`](http://doi.org/10.1093/mnras/stad1635)

(ref: BarniolDuran2014) Barniol Duran, R. 2014, MNRAS, 442, 3147, doi: [`10.1093/mnras/stu1070`](http://doi.org/10.1093/mnras/stu1070)

(ref: BarniolDuran2015) Barniol Duran, R., & Giannios, D. 2015, MNRAS, 454, 1711, doi: [`10.1093/mnras/stv2004`](http://doi.org/10.1093/mnras/stv2004)

(ref: BAT) Barthelmy, S. D., Barbier, L. M., Cummings, J. R., et al. 2005, Space Sci. Rev., 120, 143, doi: [`10.1007/s11214-005-5096-3`](http://doi.org/10.1007/s11214-005-5096-3)

(ref: 30365) Belkin, S., Pozanenko, A., Pankov, N., Krugov, M., & GRB IKI FuN Collaboration. 2021, GRB Coordinates Network, 30365, 1

(ref: Berger2004) Berger, E., Kulkarni, S. R., & Frail, D. A. 2004, ApJ, 612, 966, doi: [`10.1086/422809`](http://doi.org/10.1086/422809)

(ref: Berger2003) Berger, E., Kulkarni, S. R., Pooley, G., et al. 2003, Nature, 426, 154, doi: [`10.1038/nature01998`](http://doi.org/10.1038/nature01998)

(ref: BM1976) Blandford, R. D., & McKee, C. F. 1976, Physics of Fluids, 19, 1130, doi: [`10.1063/1.861619`](http://doi.org/10.1063/1.861619)

(ref: Bloemen2016) Bloemen, S., Groot, P., Woudt, P., et al. 2016, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9906, Ground-based and Airborne Telescopes VI, ed. H. J. Hall, R. Gilmozzi, & H. K. Marshall, 990664

(ref: Bright2023) Bright, J. S., Rhodes, L., Farah, W., et al. 2023, Nature Astronomy, 7, 986, doi: [`10.1038/s41550-023-01997-9`](http://doi.org/10.1038/s41550-023-01997-9)

(ref: XRT) Burrows, D. N., Hill, J. E., Nousek, J. A., et al. 2005, Space Sci. Rev., 120, 165, doi: [`10.1007/s11214-005-5097-2`](http://doi.org/10.1007/s11214-005-5097-2)

(ref: Chandra2012) Chandra, P., & Frail, D. A. 2012, ApJ, 746, 156, doi: [`10.1088/0004-637X/746/2/156`](http://doi.org/10.1088/0004-637X/746/2/156)

(ref: chandra2008) Chandra, P., Cenko, S. B., Frail, D. A., et al. 2008, ApJ, 683, 924, doi: [`10.1086/589807`](http://doi.org/10.1086/589807)

(ref: Chevalier2000) Chevalier, R. A., & Li, Z.-Y. 2000, ApJ, 536, 195, doi: [`10.1086/308914`](http://doi.org/10.1086/308914)

(ref: Dai1998) Dai, Z. G., & Lu, T. 1998, , 81, 4301, doi: [`10.1103/PhysRevLett.81.4301`](http://doi.org/10.1103/PhysRevLett.81.4301)

(ref: Postigo2012) de Ugarte Postigo, A., Lundgren, A., Martı́n, S., et al. 2012, A&A, 538, A44, doi: [`10.1051/0004-6361/201117848`](http://doi.org/10.1051/0004-6361/201117848)

(ref: deWet2023a) de Wet, S., Laskar, T., Groot, P. J., et al. 2023a, A&A, 671, A116, doi: [`10.1051/0004-6361/202244917`](http://doi.org/10.1051/0004-6361/202244917)

(ref: deWet2023b) de Wet, S., Izzo, L., Groot, P. J., et al. 2023b, A&A, 677, A32, doi: [`10.1051/0004-6361/202347017`](http://doi.org/10.1051/0004-6361/202347017)

(ref: Duncan2023) Duncan, R. A., van der Horst, A. J., & Beniamini, P. 2023, MNRAS, 518, 1522, doi: [`10.1093/mnras/stac3172`](http://doi.org/10.1093/mnras/stac3172)

(ref: Eftekhari2022) Eftekhari, T., Berger, E., Metzger, B. D., et al. 2022, ApJ, 935, 16, doi: [`10.3847/1538-4357/ac7ce8`](http://doi.org/10.3847/1538-4357/ac7ce8)

(ref: Eichler2005) Eichler, D., & Waxman, E. 2005, ApJ, 627, 861, doi: [`10.1086/430596`](http://doi.org/10.1086/430596)

(ref: Fitzpatrick1999) Fitzpatrick, E. L. 1999, PASP, 111, 63, doi: [`10.1086/316293`](http://doi.org/10.1086/316293)

(ref: Foreman2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Frail1997) Frail, D. A., Kulkarni, S. R., Nicastro, L., Feroci, M., & Taylor, G. B. 1997, Nature, 389, 261, doi: [`10.1038/38451`](http://doi.org/10.1038/38451)

(ref: Frail2005) Frail, D. A., Soderberg, A. M., Kulkarni, S. R., et al. 2005, ApJ, 619, 994, doi: [`10.1086/426680`](http://doi.org/10.1086/426680)

(ref: Frail2000) Frail, D. A., Waxman, E., & Kulkarni, S. R. 2000a, ApJ, 537, 191, doi: [`10.1086/309024`](http://doi.org/10.1086/309024)

(ref: Frail2000a) Frail, D. A., Berger, E., Galama, T., et al. 2000b, ApJL, 538, L129, doi: [`10.1086/312807`](http://doi.org/10.1086/312807)

(ref: 30366) Frederiks, D., Golenetskii, S., Lysenko, A., et al. 2021, GRB Coordinates Network, 30366, 1

(ref: Gat2013) Gat, I., van Eerten, H., & MacFadyen, A. 2013, ApJ, 773, 2, doi: [`10.1088/0004-637X/773/1/2`](http://doi.org/10.1088/0004-637X/773/1/2)

(ref: Geng2014) Geng, J. J., Wu, X. F., Li, L., Huang, Y. F., & Dai, Z. G. 2014, ApJ, 792, 31, doi: [`10.1088/0004-637X/792/1/31`](http://doi.org/10.1088/0004-637X/792/1/31)

(ref: Gill2023) Gill, R., & Granot, J. 2023, MNRAS, 524, L78, doi: [`10.1093/mnrasl/slad075`](http://doi.org/10.1093/mnrasl/slad075)

(ref: Goodman1997) Goodman, J. 1997, New A, 2, 449, doi: [`10.1016/S1384-1076(97)00031-6`](http://doi.org/10.1016/S1384-1076(97)00031-6)

(ref: Goodman2006) Goodman, J., & Narayan, R. 2006, ApJ, 636, 510, doi: [`10.1086/497903`](http://doi.org/10.1086/497903)

(ref: Granot2002) Granot, J., & Sari, R. 2002, ApJ, 568, 820, doi: [`10.1086/338966`](http://doi.org/10.1086/338966)

(ref: Granot2014) Granot, J., & van der Horst, A. J. 2014, PASA, 31, e008, doi: [`10.1017/pasa.2013.44`](http://doi.org/10.1017/pasa.2013.44)

(ref: Greiner2018) Greiner, J., Bolmer, J., Wieringa, M., et al. 2018, A&A, 614, A29, doi: [`10.1051/0004-6361/201731755`](http://doi.org/10.1051/0004-6361/201731755)

(ref: 30354) Groot, P. J., de Wet, S., Vreeswijk, P. M., Levan, A. J., & Meerlicht Consortium. 2021, GRB Coordinates Network, 30354, 1

(ref: Hancock2019) Hancock, P. J., Charlton, E. G., Macquart, J.-P., & Hurley-Walker, N. 2019, arXiv e-prints, arXiv:1907.08395, doi: [`10.48550/arXiv.1907.08395`](http://doi.org/10.48550/arXiv.1907.08395)

(ref: Heywood2020) Heywood, I. 2020, oxkat: Semi-automated imaging of MeerKAT observations, Astrophysics Source Code Library, record ascl:2009.003. [`http://ascl.net/2009.003`](http://ascl.net/2009.003)

(ref: Kangas2020) Kangas, T., Fruchter, A. S., Cenko, S. B., et al. 2020, ApJ, 894, 43, doi: [`10.3847/1538-4357/ab8799`](http://doi.org/10.3847/1538-4357/ab8799)

(ref: Kobayashi2000) Kobayashi, S., & Sari, R. 2000, ApJ, 542, 819, doi: [`10.1086/317021`](http://doi.org/10.1086/317021)

(ref: Kobayashi2003) Kobayashi, S., & Zhang, B. 2003, ApJ, 597, 455, doi: [`10.1086/378283`](http://doi.org/10.1086/378283)

(ref: 30356) Kuin, N. P. M., Lien, A. Y., & Swift/UVOT Team. 2021, GRB Coordinates Network, 30356, 1

(ref: Kulkarni1999) Kulkarni, S. R., Frail, D. A., Sari, R., et al. 1999, ApJL, 522, L97, doi: [`10.1086/312227`](http://doi.org/10.1086/312227)

(ref: Kumar2015) Kumar, P., & Zhang, B. 2015, Phys. Rep., 561, 1, doi: [`10.1016/j.physrep.2014.09.008`](http://doi.org/10.1016/j.physrep.2014.09.008)

(ref: Lamberts2018) Lamberts, A., & Daigne, F. 2018, MNRAS, 474, 2813, doi: [`10.1093/mnras/stx2951`](http://doi.org/10.1093/mnras/stx2951)

(ref: Laskar2015) Laskar, T., Berger, E., Margutti, R., et al. 2015, ApJ, 814, 1, doi: [`10.1088/0004-637X/814/1/1`](http://doi.org/10.1088/0004-637X/814/1/1)

(ref: Laskar2013) Laskar, T., Berger, E., Zauderer, B. A., et al. 2013, ApJ, 776, 119, doi: [`10.1088/0004-637X/776/2/119`](http://doi.org/10.1088/0004-637X/776/2/119)

(ref: Laskar2018a) Laskar, T., Berger, E., Margutti, R., et al. 2018a, ApJ, 859, 134, doi: [`10.3847/1538-4357/aabfd8`](http://doi.org/10.3847/1538-4357/aabfd8)

(ref: Laskar2018b) Laskar, T., Alexander, K. D., Berger, E., et al. 2018b, ApJ, 862, 94, doi: [`10.3847/1538-4357/aacbcc`](http://doi.org/10.3847/1538-4357/aacbcc)

(ref: Laskar2023) Laskar, T., Alexander, K. D., Margutti, R., et al. 2023, ApJL, 946, L23, doi: [`10.3847/2041-8213/acbfad`](http://doi.org/10.3847/2041-8213/acbfad)

(ref: Levine2023) Levine, D., Dainotti, M., Fraija, N., et al. 2023, MNRAS, 519, 4670, doi: [`10.1093/mnras/stac3730`](http://doi.org/10.1093/mnras/stac3730)

(ref: 30351) Lien, A. Y., Barthelmy, S. D., Kennea, J. A., et al. 2021, GRB Coordinates Network, 30351, 1

(ref: Lyutikov2017) Lyutikov, M. 2017, Physics of Fluids, 29, 047101, doi: [`10.1063/1.4977445`](http://doi.org/10.1063/1.4977445)

(ref: Marongiu2022) Marongiu, M., Guidorzi, C., Stratta, G., et al. 2022, A&A, 658, A11, doi: [`10.1051/0004-6361/202140403`](http://doi.org/10.1051/0004-6361/202140403)

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mesler2012) Mesler, R. A., Pihlström, Y. M., Taylor, G. B., & Granot, J. 2012, ApJ, 759, 4, doi: [`10.1088/0004-637X/759/1/4`](http://doi.org/10.1088/0004-637X/759/1/4)

(ref: Meszaros1997) Mészáros, P., & Rees, M. J. 1997, ApJ, 476, 232, doi: [`10.1086/303625`](http://doi.org/10.1086/303625)

(ref: Meszaros1999) —. 1999, MNRAS, 306, L39, doi: [`10.1046/j.1365-8711.1999.02800.x`](http://doi.org/10.1046/j.1365-8711.1999.02800.x)

(ref: Nakar2007) Nakar, E., & Granot, J. 2007, MNRAS, 380, 1744, doi: [`10.1111/j.1365-2966.2007.12245.x`](http://doi.org/10.1111/j.1365-2966.2007.12245.x)

(ref: Nousek2006) Nousek, J. A., Kouveliotou, C., Grupe, D., et al. 2006, ApJ, 642, 389, doi: [`10.1086/500724`](http://doi.org/10.1086/500724)

(ref: Oconnor2023) O’Connor, B., Troja, E., Ryan, G., et al. 2023, Science Advances, 9, eadi1405, doi: [`10.1126/sciadv.adi1405`](http://doi.org/10.1126/sciadv.adi1405)

(ref: Panaitescu2004) Panaitescu, A., & Kumar, P. 2004, MNRAS, 350, 213, doi: [`10.1111/j.1365-2966.2004.07635.x`](http://doi.org/10.1111/j.1365-2966.2004.07635.x)

(ref: Pei1992) Pei, Y. C. 1992, ApJ, 395, 130, doi: [`10.1086/171637`](http://doi.org/10.1086/171637)

(ref: Perley2014) Perley, D. A., Cenko, S. B., Corsi, A., et al. 2014, ApJ, 781, 37, doi: [`10.1088/0004-637X/781/1/37`](http://doi.org/10.1088/0004-637X/781/1/37)

(ref: Pihlstrom2007) Pihlström, Y. M., Taylor, G. B., Granot, J., & Doeleman, S. 2007, ApJ, 664, 411, doi: [`10.1086/518955`](http://doi.org/10.1086/518955)

(ref: Piran1999) Piran, T. 1999, Phys. Rep., 314, 575, doi: [`10.1016/S0370-1573(98)00127-6`](http://doi.org/10.1016/S0370-1573(98)00127-6)

(ref: Piran2004) —. 2004, Reviews of Modern Physics, 76, 1143, doi: [`10.1103/RevModPhys.76.1143`](http://doi.org/10.1103/RevModPhys.76.1143)

(ref: Planck2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6, doi: [`10.1051/0004-6361/201833910`](http://doi.org/10.1051/0004-6361/201833910)

(ref: Racusin2008) Racusin, J. L., Karpov, S. V., Sokolowski, M., et al. 2008, Nature, 455, 183, doi: [`10.1038/nature07270`](http://doi.org/10.1038/nature07270)

(ref: Rees1998) Rees, M. J., & Mészáros, P. 1998, ApJL, 496, L1, doi: [`10.1086/311244`](http://doi.org/10.1086/311244)

(ref: Ressler2017) Ressler, S. M., & Laskar, T. 2017, ApJ, 845, 150, doi: [`10.3847/1538-4357/aa8268`](http://doi.org/10.3847/1538-4357/aa8268)

(ref: Rhoads1999) Rhoads, J. E. 1999, ApJ, 525, 737, doi: [`10.1086/307907`](http://doi.org/10.1086/307907)

(ref: UVOT) Roming, P. W. A., Kennedy, T. E., Mason, K. O., et al. 2005, Space Sci. Rev., 120, 95, doi: [`10.1007/s11214-005-5095-4`](http://doi.org/10.1007/s11214-005-5095-4)

(ref: Ryan2015) Ryan, G., van Eerten, H., MacFadyen, A., & Zhang, B.-B. 2015, ApJ, 799, 3, doi: [`10.1088/0004-637X/799/1/3`](http://doi.org/10.1088/0004-637X/799/1/3)

(ref: Sari2000) Sari, R., & Mészáros, P. 2000, ApJL, 535, L33, doi: [`10.1086/312689`](http://doi.org/10.1086/312689)

(ref: Sari1999b) Sari, R., & Piran, T. 1999, ApJ, 520, 641, doi: [`10.1086/307508`](http://doi.org/10.1086/307508)

(ref: Sari1999) Sari, R., Piran, T., & Halpern, J. P. 1999, ApJL, 519, L17, doi: [`10.1086/312109`](http://doi.org/10.1086/312109)

(ref: Sari1998) Sari, R., Piran, T., & Narayan, R. 1998, ApJL, 497, L17, doi: [`10.1086/311269`](http://doi.org/10.1086/311269)

(ref: Sato2023) Sato, Y., Murase, K., Ohira, Y., & Yamazaki, R. 2023, MNRAS, 522, L56, doi: [`10.1093/mnrasl/slad038`](http://doi.org/10.1093/mnrasl/slad038)

(ref: Miriad) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433

(ref: SF2011) Schlafly, E. F., & Finkbeiner, D. P. 2011, ApJ, 737, 103, doi: [`10.1088/0004-637X/737/2/103`](http://doi.org/10.1088/0004-637X/737/2/103)

(ref: Schroeder2023) Schroeder, G., Rhodes, L., Laskar, T., et al. 2023, arXiv e-prints, arXiv:2308.10936, doi: [`10.48550/arXiv.2308.10936`](http://doi.org/10.48550/arXiv.2308.10936)

(ref: Soderberg2007) Soderberg, A. M., Nakar, E., Cenko, S. B., et al. 2007, ApJ, 661, 982, doi: [`10.1086/515562`](http://doi.org/10.1086/515562)

(ref: Taylor2005) Taylor, G. B., Momjian, E., Pihlström, Y., Ghosh, T., & Salter, C. 2005, ApJ, 622, 986, doi: [`10.1086/428346`](http://doi.org/10.1086/428346)

(ref: Uhm2014) Uhm, Z. L., & Zhang, B. 2014, ApJ, 780, 82, doi: [`10.1088/0004-637X/780/1/82`](http://doi.org/10.1088/0004-637X/780/1/82)

(ref: 30363) Ursi, A., Pittori, C., Verrecchia, F., et al. 2021, GRB Coordinates Network, 30363, 1

(ref: Vanderhorst2008) van der Horst, A. J., Kamble, A., Resmi, L., et al. 2008, A&A, 480, 35, doi: [`10.1051/0004-6361:20078051`](http://doi.org/10.1051/0004-6361:20078051)

(ref: Vanderhorst2014) van der Horst, A. J., Paragi, Z., de Bruyn, A. G., et al. 2014, MNRAS, 444, 3151, doi: [`10.1093/mnras/stu1664`](http://doi.org/10.1093/mnras/stu1664)

(ref: VanEerten2012) van Eerten, H., van der Horst, A., & MacFadyen, A. 2012, ApJ, 749, 44, doi: [`10.1088/0004-637X/749/1/44`](http://doi.org/10.1088/0004-637X/749/1/44)

(ref: Vaneerten2009) van Eerten, H. J., Meliani, Z., Wijers, R. A. M. J., & Keppens, R. 2009, MNRAS, 398, L63, doi: [`10.1111/j.1745-3933.2009.00711.x`](http://doi.org/10.1111/j.1745-3933.2009.00711.x)

(ref: Wang2015) Wang, X.-G., Zhang, B., Liang, E.-W., et al. 2015, ApJS, 219, 9, doi: [`10.1088/0067-0049/219/1/9`](http://doi.org/10.1088/0067-0049/219/1/9)

(ref: Warren2018) Warren, D. C., Barkov, M. V., Ito, H., Nagataki, S., & Laskar, T. 2018, MNRAS, 480, 4060, doi: [`10.1093/mnras/sty2138`](http://doi.org/10.1093/mnras/sty2138)

(ref: Waxman1998) Waxman, E., Kulkarni, S. R., & Frail, D. A. 1998, ApJ, 497, 288, doi: [`10.1086/305467`](http://doi.org/10.1086/305467)

(ref: Willingale2013) Willingale, R., Starling, R. L. C., Beardmore, A. P., Tanvir, N. R., & O’Brien, P. T. 2013, MNRAS, 431, 394, doi: [`10.1093/mnras/stt175`](http://doi.org/10.1093/mnras/stt175)

(ref: Woosley2006) Woosley, S. E., & Bloom, J. S. 2006, ARA&A, 44, 507, doi: [`10.1146/annurev.astro.43.072103.150558`](http://doi.org/10.1146/annurev.astro.43.072103.150558)

(ref: 30357) Xu, D., Izzo, L., de Ugarte Postigo, A., et al. 2021, GRB Coordinates Network, 30357, 1

(ref: 30362) Yamaoka, K., Yoshida, A., Sakamoto, T., et al. 2021, GRB Coordinates Network, 30362, 1

(ref: Zhang2006) Zhang, B., Fan, Y. Z., Dyks, J., et al. 2006, ApJ, 642, 354, doi: [`10.1086/500723`](http://doi.org/10.1086/500723)

(ref: Zhang2005) Zhang, B., & Kobayashi, S. 2005, ApJ, 628, 315, doi: [`10.1086/429787`](http://doi.org/10.1086/429787)

(ref: Zhang2001a) Zhang, B., & Mészáros, P. 2001, ApJL, 552, L35, doi: [`10.1086/320255`](http://doi.org/10.1086/320255)

(ref: Zhang2002) —. 2002, ApJ, 566, 712, doi: [`10.1086/338247`](http://doi.org/10.1086/338247)

(ref: Zhang2023) Zhang, B., Wang, X.-Y., & Zheng, J.-H. 2023, arXiv e-prints, arXiv:2311.14180, doi: [`10.48550/arXiv.2311.14180`](http://doi.org/10.48550/arXiv.2311.14180)

(ref: Zhang2009) Zhang, W., & MacFadyen, A. 2009, ApJ, 698, 1261, doi: [`10.1088/0004-637X/698/2/1261`](http://doi.org/10.1088/0004-637X/698/2/1261)

(ref: Zhou2023) Zhou, H., Jin, Z.-P., Covino, S., Fan, Y.-Z., & Wei, D.-M. 2023, ApJS, 268, 65, doi: [`10.3847/1538-4365/acf20a`](http://doi.org/10.3847/1538-4365/acf20a)

(ref: Zou2005) Zou, Y. C., Wu, X. F., & Dai, Z. G. 2005, MNRAS, 363, 93, doi: [`10.1111/j.1365-2966.2005.09411.x`](http://doi.org/10.1111/j.1365-2966.2005.09411.x)

# Table of flux measurements

+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| $\Delta t$ (days) | Telescope    | Band/Filter | Frequency (Hz) | Flux (mJy) | Uncertainty (mJy) | Detection? ($1=$ yes) |   |
+:=================:+:============:+:===========:+:==============:+:==========:+:=================:+:=====================:+:=:+
| 0.00099           | *Swift*/XRT  | 1 keV       | 2.42e+17       | 1.026390   | 0.129683          | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.00099           | *Swift*/XRT  | 1 keV       | 2.42e+17       | 1.316908   | 0.163709          | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.00100           | *Swift*/XRT  | 1 keV       | 2.42e+17       | 0.928455   | 0.114673          | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.00101           | *Swift*/XRT  | 1 keV       | 2.42e+17       | 1.179080   | 0.160764          | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.00101           | *Swift*/XRT  | 1 keV       | 2.42e+17       | 0.798587   | 0.209709          | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| …                 | …                          | …              | …                              | …                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
|                   | *Swift*/UVOT | $u$         | 8.652e+14      | 42.075     | 6.975             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.01126           | MeerLICHT    | $q$         | 5.169e+14      | 27.137     | 0.455             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.01247           | MeerLICHT    | $u$         | 7.889e+14      | 13.316     | 0.502             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.01371           | MeerLICHT    | $q$         | 5.169e+14      | 21.605     | 0.416             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| …                 | …                          | …              | …                              | …                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
|                   | ATCA         | 5.5 GHz     | 5.50e+09       | 0.074      | 0.024             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.530             | ATCA         | 9 GHz       | 9.00e+09       | 0.277      | 0.044             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.550             | ATCA         | 21.2 GHz    | 2.12e+10       | 0.393      | 0.071             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 0.550             | ATCA         | 16.7 GHz    | 1.67e+10       | 0.368      | 0.071             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| 1.061             | ALMA         | 343.5 GHz   | 3.44e+11       | 1.637      | 0.053             | 1                     |   |
+-------------------+--------------+-------------+----------------+------------+-------------------+-----------------------+---+
| …                 | …                          | …              | …                              | …                     |   |
+-------------------+----------------------------+----------------+--------------------------------+-----------------------+---+

: GRB 210702A flux measurements

Table notes: Table [3](#tab:flux) is published in its entirety in the machine-readable format. A portion is shown here for guidance regarding its form and content.

[^1]: <https://www.swift.ac.uk/xrt_live_cat/01058804/>

[^2]: Using $\beta_\mathrm{X}\equiv1-\Gamma$.

[^3]: <https://www.swift.ac.uk/swift_portal/>

[^4]: <https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/>

[^5]: <https://www.atnf.csiro.au/computing/software/miriad/>

[^6]: <https://github.com/IanHeywood/oxkat>

[^7]: <https://idia-pipelines.github.io/docs/processMeerKAT>

[^8]: In a wind medium the $A_\star$ parameter is commonly used as a measure of the density, as defined in (cite: Chevalier2000). The $n_0$ parameter is related to the $A_\star$ parameter via $n_0=A_\star\times29.89$ cm$^{-3}$, where $n_0$ is the number density at a reference distance of $10^{17}$ cm.

[^9]: <https://ror.org/05qajvd42>

</paper>

Write the methods card for this paper.