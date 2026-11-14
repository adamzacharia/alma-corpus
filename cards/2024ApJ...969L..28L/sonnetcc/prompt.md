# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...969L..28L\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...969L..28L",
 "title": "A Strongly Lensed Dusty Starburst of an Intrinsic Disk Morphology at a Photometric Redshift of z <SUB>ph</SUB> &gt; 7",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Ling, Chenxiaoji",
 "n_authors": 6,
 "arxiv_id": "2402.16649",
 "doi": "10.3847/2041-8213/ad59a3",
 "alma_projects_linked_by_archive": [
  "2016.1.00463.S",
  "2021.1.00705.S",
  "2022.1.00863.S"
 ]
}
```

Paper text:
<paper>
# A Strongly Lensed Dusty Starburst of an Intrinsic Disk Morphology at Photometric Redshift of $z_{\rm ph}>7$

## Abstract

We present COSBO-7, a strong millimeter (mm) source known for more than sixteen years but was just revealed its near-to-mid-IR counterpart by the James Webb Space Telescope (JWST). The precise pin-pointing by the Atacama Large Millimeter Array (ALMA) on the exquisite NIRCam and MIRI images show that it is a background source gravitationally lensed by a single foreground galaxy, and the analysis of its spectral energy distribution by different tools is in favor of photometric redshift at $z_{\rm ph}>7$. Strikingly, our lens modeling based on the JWST data shows that it has a regular, disk morphology in the source plane. The dusty region giving rise to the far-IR-to-mm emission seems to be confined to a limited region to one side of the disk and has a high dust temperature of $>90$ K. The galaxy is experiencing starburst both within and outside of this dusty region. After taking the lensing magnification of $\mu\approx 2.5$–3.6 into account, the intrinsic star formation rate is several hundred $M_\odot$ yr$^{-1}$ both within the dusty region and across the more extended stellar disk, and the latter already has $>10^{10}M_\odot$ of stars in place. If it is indeed at $z>7$, COSBO-7 presents an extraordinary case that is against the common wisdom about galaxy formation in the early universe; simply put, its existence poses a critical question to be answered: how could a massive disk galaxy come into being so early in the universe and sustain its regular morphology in the middle of an enormous starburst?

# Introduction

Systematic investigation of dust-embedded star formation in external galaxies started from the mid-to-far-IR survey carried out by the InfraRed Astronomy Satellite four decades ago (cite: deJong1984; Sofier1984; Lonsdale1984). The climax of these early studies was the discovery of Ultra-luminous Infrared Galaxies in the local universe (cite: Houck1984; Houck1985; Aaronson1984), which have enormous IR luminosity of $L_{\rm IR}\geq 10^{12} L_\odot$ (integrated over the rest-frame 8–1000 $\mu$m) but are faint in optical. In the late 1990s to early 2000s, a series of new instruments opened up the submillimeter (submm) and millimeter (mm) window from the ground and detected a new population of galaxies that were collectively called “submillimeter galaxies” (SMGs; see (cite: Blain2002) for an early review). Through the pin-pointing of their positions by radio interferometry and the subsequent spectroscopy of their optical counterparts (cite: Barger2000; Chapman2003), a consensus has been reached that SMGs are galaxies mostly at $z\approx 2$–3 with ULIRG-like IR luminosity, and their continuum submm/mm emissions, which must be due to heated dust, are attributed to extreme star formation, often with star formation rates (SFRs) $>100$ $M_\odot$ yr$^{-1}$.

The past decade has witnessed great advancements in the study of high-redshift (high-$z$) dusty galaxies. Numerous far-IR galaxies (FIRGs), which are akin to SMGs, have been cataloged by the wide-field far-IR surveys of the Herschel Space Observatory. The unprecedented sensitivity of the Atacama Large Millimeter Array (ALMA) has allowed the precise localization of SMGs and FIRGs in significant numbers to enable statistical studies at various wavelengths. A more general term, “dusty star forming galaxies” (cite: Casey2014), has become widely in use to refer to galaxies beyond the local universe that are detected in the far-IR-to-mm wavelengths, with the implicit understanding that their continuum emission in this regime is due to dust heated by star formation. While still subject to some debate, it is recognized that DSFGs, once a population of galaxies discovered in a special wavelength range, are not necessarily special as compared to the general population of star-forming galaxies in terms of their global properties; for example, a large fraction of DSFGs seem to follow the tight SFR versus stellar mass relation (the so-called “main sequence”) of star-forming galaxies (cite: Michalowski2012; daCunha2015). In this new context, any galaxies with continuum dust emission signifying their dust-embedded star formation can be categorized as DSFGs, including some high-$z$ Lyman-break galaxies (LBGs) (cite: Capak2015; Bethermin2020). Somewhat surprisingly, continuum dust emissions have been detected in a few quasars and LBGs deep in the epoch of reionization (EoR), the earliest of which are at $z>7$ (cite: Venemans2012; Watson2015; Hashimoto2019a; Bakx2020; Sommovigo2022). This implies that at least some galaxies at even earlier epochs must already be forming a substantial amount of dust. Dusty starbursts, the most extreme ones among DSFGs, have also been seen in the EoR (cite: Riechers2013; Strandet2017). This raises an interesting question: are there starbursts in the EoR that are *not* enshrouded by dust? While there is no obvious reason that they should not exist, no such objects have been found in surveys for LBGs despite that they would be very easy to detect because of their extreme brightness in the rest-frame UV.

The advent of James Webb Space Telescope (JWST) is bringing the study of high-$z$ DSFGs to a new level. In merely over a year, the synergy of JWST and ALMA has brought us a lot of details on the connection between dust-obscured and unobscured (“exposed”) stellar populations in DSFGs (cite: Cheng2022; Chen2022; Cheng2023; Huang2023; Tadaki2023; Liu2023; Barger2023; Kamieneski2023; Fujimoto2023; Hashimoto2023; Boogaard2023; Yoon2023; Rujopakarn2023; AM2023; Sun2024; Killi2024), including a subset among the so-called “HST-dark” galaxies that are faint or even invisible at $\lambda\lesssim 1.6$ $\mu$m (cite: Zavala2023; Kokorev2023; Smail2023). Here we report on a peculiar dusty starburst that could possibly change the existing view of DSFG formation in the EoR. This object is known as a bright SMG for more than sixteen years, however the ALMA pinpointing of its location on the existing Hubble Space Telescope (HST) images would only associate it with a bright spiral galaxy at $z=0.359$. Its true counterpart in the near-to-mid-IR wavelengths was only recently revealed in the JWST NIRCam and MIRI data. Using the MIRI data alone, (cite: Pearson2024) point out that this source is strongly lensed by the foreground galaxy at $z=0.359$. While many strongly lensed DSFGs have been seen among bright SMGs, we find this one special. Based on our comprehensive analysis of both the NIRCam and the MIRI data, its photometric redshift is likely at $z_{\rm ph}> 7$ and its reconstructed image in the source plane has a disk morphology. A dusty starburst hosted by a disk galaxy at such a high redshift, if confirmed, will not only be a record-breaker but also pose a severe challenge to our current theories of galaxy formation in the early universe.

This paper presents the results from our study of this object, organized as follows. The relevant multi-wavelength data are described in Section 2, and the photometry is given in Section 3. The analysis of the spectral energy distributions (SEDs) by four different tools is given in Section 4. The lens model and image reconstruction are detailed in Section 5. We discuss our results in Section 6 and conclude with a summary in Section 7. All magnitudes are in the AB system. We adopt the following cosmological parameters throughout: $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_M=0.3$ and $\Omega_\Lambda=0.7$.

# Data and Source Characterization

## The SMG and its precise location

Our source was first discovered as a bright mm object in the COSBO survey (cite: Bertoldi2007), which was a 1.2 mm imaging survey in the COSMOS field done by the Max-Planck Millimeter Bolometer Array (MAMBO-2) at the 30-m IRAM telescope. For simplicity, hereafter we refer to it as “COSBO-7” according to its ID in the COSBO catalog. This source was later confirmed at different mm and sub-mm wavelengths, and these measurements are summarized in Table [\[tab:literature\]](#tab:literature).

The sub-arcsec position of this source has been located by the ALMA Band 7 (870 $\mu$m) observations made on May 15, 2018 (beam size $\sim$0.75$''$; program ID 2016.1.00463.S, PI: Y. Matsuda), which was reported in (cite: Simpson2020) as “AS2COSMOS0005.1” at R.A. = 10:00:23.97, Decl. = 02:17:50.1 (J2000.0). We adopt the position in the publicly available catalog (version 20220606) from the A$^3$COSMOS project (cite: Liu2019): R.A. = 10:00:23.98, Decl. = 02:17:49.99 (J2000.0). Both are consistent with the indirect pinpointing of the VLA 3 GHz observations at a similar spatial resolution (cite: Smolcic2017), which gives R.A. = 10:00:23.95, Decl. = 02:17:50.03 (J2000.0).

| Reference | Survey/Instrument | Band | R.A. | Decl. | Flux density |
|:---|:---|:---|:---|:---|:---|
| (cite: Bertoldi2007) | COSBO/MAMBO-2 | 1.2 mm | 10:00:24 | 02:17:48 | 5.0 $\pm$ 0.9 mJy |
| (cite: Aretxaga2011) | AzTEC | 1.1 mm | 10:00:24.2 | 02:17:48.7 | 3.1 $\pm$ 1.2 mJy |
| (cite: Casey2013) | SCUBA-2 | 450 $\mu$m | 10:00:23.8 | 02:17:51 | 12.7 $\pm$ 5.42 mJy |
| (cite: Casey2013) | SCUBA-2 | 850 $\mu$m | 10:00:23.8 | 02:17:51 | 8.42 $\pm$ 0.92 mJy |
| (cite: Geach2017) | S2CLS | 850 $\mu$m | 10:00:24.00 | 02:17:50.6 | 9.25 $\pm$ 1.14 mJy |
| (cite: Simpson2019) | S2COSMOS | 850 $\mu$m | 10:00:23.93 | 02:17:51.6 | 10.3 $\pm$ 0.8 mJy |
| (cite: Smolcic2017) | VLA-COSMOS | 3 GHz | 10:00:23.95 | 02:17:50.03 | 28.6 $\pm$ 2.8 $\mu$Jy |
| (cite: Schinnerer2010) | VLA-COSMOS | 1.4 GHz | 10:00:23.99 | 02:17:49.96 | 187 $\pm$ 12 $\mu$Jy |
| (cite: Liu2019)$^\dagger$ | A$^3$COSMOS | 870 $\mu$m | 10:00:23.98 | 02:17:49.99 | 10.446 $\pm$ 0.601 mJy |

: Observations of COSBO-7 in the literature

Table notes: $^{}$ Notes. $^\dagger$ See also (cite: Simpson2020).

## ALMA mm/sub-mm data and Herschel far-IR data

In addition to the aforementioned ALMA Band 7 data, this source also has Band 4 (2.07 mm) data taken on September 19, 2022 (program ID 2021.1.00705.S, PI: O. Cooper) that are now public. For the purpose of this work, we reduced all the public ALMA data in a uniform way. We utilized the default pipeline ScriptForPi.py and performed tclean using the Common Astronomy Software Applications (cite: 2022PASP..134k4501C) to obtain the continuum image in each band. The cleaning was done to 3 $\sigma$ with the default natural weighting parameters of WEIGHTING = “BRIGGS” and ROBUST = 2.0. The final maps reach the root mean square (rms) of 0.180 and 0.075 mJy beam$^{-1}$ in Band 7 and 4, respectively, and have the beams of (bmaj, bmin, PA) = (0.78$''$, 0.72$''$, $-$85.9$^{\rm o}$) and (1.56$''$, 1.33$''$, $-$63.0$^{\rm o}$) in these two bands, respectively, where bmaj, bmin and PA are the major axis, minor axis and positional angle, respectively.

The COSMOS field was observed by the Herschel Multi-tiered Extragalactic Survey (cite: Oliver2012) using the SPIRE imager in 250, 350 and 500 $\mu$m, which had beam sizes of $\sim$18$''$, 25$''$ and 36$''$, respectively. We make use of the maps included in its fourth data release, which have the pixel scales of 6.0$''$, 8.3$''$ and 12.0$''$ in these three bands, respectively.

## JWST near-to-mid IR Data

![](fig_pinpoint.png)

The JWST NIRCam and MIRI imaging data of this source are from the Public Release IMaging for Extragalactic Research (PRIMER) program in Cycle 1 (cite: Dunlop2021). The NIRCam observations were done in eight bands: F090W, F115W, F150W, F200W in the short-wavelength (SW) channel and F277W, F356W, F410M, and F444W in the long-wavelength (LW) channel, respectively, and the MIRI observations were done in F770W and F1800W.

We reduced these data on our own. We started from the Stage 1 “uncal.fits” products retrieved from the Mikulski Archive for Space Telescopes (MAST), which are single exposures after the “Level 1b” processing by the default JWST calibration procedures. Our further process used the JWST pipeline version 1.10.2 in the context of `jwst_1089.pmap` for the NIRCam data and version 1.12.5 in the context of `jwst_1183.pmap` for the MIRI data. We first ran the Stage 1 of the calibration pipeline, `calwebb_detector1`, which applies the detector-level corrections to the “uncal.fits” images. The outputs were then processed through Stage 2, `calwebb_image2`, which mainly applies the flat-field correction and the flux calibration. We adopted most of the default parameters but with a few changes: (1) for the NIRCam images, we expanded the large “jump” events, also known as the “snowball”, by 1.5 times the radius of the event to the neighboring pixels for better masking; (2) for the MIRI images, we enabled the detection and masking of “showers”; (3) we removed the “1/f” readout noise patterns in the NIRCam SW images by using an external recipe “image1overf” [^1]; (4) we removed the vertical and/or horizontal stripe-like noise patters in the MIRI images following the recipe by (cite: Yang2023); (5) we used the external tool “JHAT” [^2] to align each single exposure to the astrometric grid defined by the HST images from the CANDELS program (cite: Grogin2011; Koekemoer2011); and (6) we estimated and subtracted a smooth, 2-dimensional background from all single exposures before stacking. For the MIRI images, we also masked the entire coronagraph regions. After all these processes, the individual exposures in each band were then stacked into one mosaic with a pixel scale of 0.06$''$. The images are in the unit of MJy sr$^{-1}$, which translates to a magnitude zero-point of 26.581.

## COSBO-7: a strongly lensed system due to a single foreground galaxy

Figure [1](#fig:the_arc) shows the ALMA 870 $\mu$m image of COSBO-7 and its color-composite images in the NIRCam SW and LW. Based on the ALMA position (“+” symbol), it is obvious that COSBO-7 corresponds to the red arc in the NIRCam LW bands, which must be an image produced by the strong gravitational lensing due to a single disk galaxy in the foreground. This foreground galaxy has the spectroscopic redshift of $z=0.359$ (cite: Hasinger2018).

There are two notable points regarding this lensing system. First, the arc is extremely red: while being very bright in the NIRCam LW, it is barely visible in the SW. Second, the bright 870 $\mu$m source (corresponding to the arc) has a much fainter companion source that is 1.16$''$ away, which is likely its counter image. While we cannot rule out the possibility that this fainter companion could be due to the foreground lens, interpreting it as the counter image is consistent with our analysis presented in the remainder of this paper.

# Photometry of COSBO-7

## Photometry in the JWST NIRCam and MIRI images

To obtain an accurate photometry of COSBO-7’s counterparts in the JWST images, it is necessary to subtract the extended foreground lens. For this purpose, we utilized the Galfit software (cite: Peng2002; Peng2010) to model this foreground galaxy.

![](fig_jwstgalfit.png)

Running Galfit needs the point spread function (PSF) of the image to be analyzed. For the NIRCam images, we constructed the empirical PSFs following the methodology of (cite: LY2022). For a given band, we selected isolated stars and made cutouts of $201\times 201$ pixels centered on them. The sources around the stars were masked, and the cutout images were subsampled to a finer grid by 10 times. The centers of these cutouts were also aligned in this process. The fluxes of the stars were normalized to unity, and the normalized images were stacked using median. Finally, the stacked star image was rebinned by a factor of 10 in both dimensions to restore the original resolution and was adopted as the PSF image. For the MIRI F770W and F1800W images, we directly used the WebbPSF to obtain their PSFs.

The Galfit modeling of the foreground lens was done on 10$''$ $\times$ 10$''$ cutouts. In the MIRI F1800W band, this galaxy was successfully fitted by using a single Sérsic profile (cite: Sersic1963; Sersic1968). In the MIRI F770W band, we had to use two Sérsic profiles simultaneously in order to obtain a good fit. In the NIRCam bands, however, fitting two Sérsic profiles would still leave a strong residual that shows a barred spiral structure with a ring. In the end, we had to evoke a four-component model: a Sérsic profile for the disk component, a logarithmic-hyperbolic tangent spiral (log-tanh) profile for the barred spiral structure, a truncated Sérsic profile for the ring structure, and a point source at the galaxy’s center for its compact bulge. This four-component model was successful in fitting the foreground galaxy in the eight NIRCam image. Figure [2](#fig:galfit) shows the original images, the Galfit models and the residual images in all the JWST bands.

In addition to the cleaned arc, the counter image of the arc is now also recovered in the residual images. The arc is invisible in F090W, starts to appear in F115W, gets increasingly bright through the successively redder NIRCam bands, and stays prominent in the two NIRCam bands up to 18 $\mu$m. Its counter image has a similar behavior, except that it is invisible in all NIRCam SW bands, presumably due to its much fainter nature.

The photometry was done on these residual images. For the NIRCam images, we carried out PSF-matching to the angular resolution of the F444W image (PSF full-width-at-half-maximum 0.16$''$) by convolving them with the convolution kernels created using the software pypher from the PSF images. Matched-aperture photometry was then done by using SExtractor in the dual-image mode, where the F444W image was set as the detection image. We took the isophotal magnitudes (“MAG_ISO”) to measure the colors and corrected the normalization of the SED to total magnitudes based on the difference between “MAG_AUTO” and “MAG_ISO” measured in the F444W band. Photometry in the MIRI bands was also done using SExtractor, however no PSF-matching was done on these images because they have much coarser resolutions as compared to the NIRCam images. Instead, we took the MAG_AUTO results in these two bands as the total magnitude measurements and appended them to the SED. In all cases, the errors were measured on the root-mean-square (rms) maps. The rms map of a given band was calculated using the “WHT” extension of the pipeline product in this band following $rms=s/\sqrt{WHT}$, where $s$ is the scaling factor that takes into account the artificial suppression of noise in the science image due to pixel resampling. To derive this factor, we used the `astroRMS` software tool [^3], which is based on the algorithm that calculates the auto-correlation of the science image pixels (M. Dickinson, priv. comm.).

As the removal of the foreground lens the subtraction of a smooth, noiseless model from GALFIT, this process does not increase the rms at the source location. The final JWST photometric results are listed in Table [1](#tab:jwstphot). The arc is invisible in F090W, and no flux was extracted in this band. In other words, it is a potential F090W dropout. Following the practices in dropout search, a 2 $\sigma$ limit was placed in this band. To investigate the impact of this limit in the follow-up analysis, we adopted two possible choices. One was the average 2 $\sigma$ depth of the image over the entire field as measured within an $r=$ 0.2$''$ aperture, which is 28.43 mag [^4]. Given its knotty morphology in F115W, if it were emitting in the bluer F090W band, the emission would likely be confined within a small knot that could be encompassed by such an aperture. Another choice was the 2 $\sigma$ limit measured within the same MAG_ISO aperture as used in other bands, which is 26.98 mag and likely very conservative.

We did not attempt to obtain accurate photometry of the counter image because it is much fainter and is severely affected by the noise due to the image subtraction. Nevertheless, a crude photometry shows that the flux ratio between the arc and its counter image is $\sim$11.7 in F444W.

Following similar procedures, we also obtained the photometry for the foreground galaxy using its model images created by Galfit. The results are also reported in Table [1](#tab:jwstphot).

|  Band  |  $\rm mag_{arc}$  |  $\rm mag_{lens}$  |
|:------:|:-----------------:|:------------------:|
| F090W  | $\le 28.43/26.98$ | 19.927 $\pm$ 0.003 |
| F115W  | 25.28 $\pm$ 0.10  | 19.451 $\pm$ 0.002 |
| F150W  | 24.75 $\pm$ 0.05  | 19.076 $\pm$ 0.001 |
| F200W  | 23.78 $\pm$ 0.02  | 18.835 $\pm$ 0.001 |
| F277W  | 23.11 $\pm$ 0.01  | 18.922 $\pm$ 0.001 |
| F356W  | 22.38 $\pm$ 0.01  | 19.438 $\pm$ 0.001 |
| F410M  | 22.08 $\pm$ 0.01  | 19.572 $\pm$ 0.001 |
| F444W  | 21.90 $\pm$ 0.01  | 19.61 $\pm$ 0.001  |
| F770W  | 21.59 $\pm$ 0.01  | 20.916 $\pm$ 0.003 |
| F1800W | 21.43 $\pm$ 0.04  | 21.372 $\pm$ 0.015 |

: JWST Photometry of the Arc and the Lens

Table notes: $^{}$ Notes. The magnitudes quoted for the arc are the measured values without the lensing magnification correction. Two upper limits in F090W are quoted, one being the averaged 2 $\sigma$ depth of the image measured within an $r=$ 0.2$''$ circular aperture and the other being the 2 $\sigma$ limit measured within the MAG_ISO aperture defined in F444W.

## Photometry in the ALMA images

![](fig_almaphot.png)

To maximize the signal-to-noise ratio of the extraction, the photometry in the ALMA images was done using CASA with polygon apertures as shown in Figure [3](#fig:almaphot). Basically, this was to sum up the pixels within the polygons. In Band 7, we separated the main image and its counter image (see Section 2.4) as indicated in the figure, and got $8.87\pm 0.89$ and $1.68\pm 0.17$ mJy, respectively. In Band 4, however, the counter image is completely blended with the main image and not separable; therefore we used a large polygon for photometry, which gave $0.62\pm 0.07$ mJy [^5]. The flux error was estimated to include the rms of the pixel values within the aperture and the uncertainty of the flux calibration (cite: 2014Msngr.155...19F), which were added in quadrature. As it turned out, the latter dominates the error.

|      Source      |     R.A.     |    Decl.     | Flux density (mJy) |
|:----------------:|:------------:|:------------:|:------------------:|
| ALMA 870 $\mu$m  | 10:00:23.971 | 02:17:50.097 |  8.87 $\pm$ 0.89   |
|                  | 10:00:24.032 | 02:17:49.373 |  1.68 $\pm$ 0.17   |
|   ALMA 2.07 mm   | 10:00:23.962 | 02:17:49.598 |  0.62 $\pm$ 0.07   |
| SPIRE 250 $\mu$m |     ...      |     ...      |  15.58 $\pm$ 5.36  |
| SPIRE 350 $\mu$m |     ...      |     ...      |  26.03 $\pm$ 9.68  |
| SPIRE 500 $\mu$m |     ...      |     ...      |  19.24 $\pm$ 5.05  |

: ALMA and Herschel Photometry

Table notes: $^{}$ Notes. The main image and its counter image are separable in ALMA 870 $\mu$m, and the corresponding results are given in the first and the second row, respectively. Their positions are those of the peaks. The position in the Herschel SPIRE images is fixed to the one measured in the VLA 3 GHz (see Table [\[tab:literature\]](#tab:literature)), which is consistent with the ALMA position of the main image.

## Photometry in the Herschel SPIRE maps

Due to their coarse spatial resolutions, the SPIRE images of COSBO-7 are severely blended with its neighbors, which can be seen in Figure [4](#fig:spiregalfit). In the 250 $\mu$m image, COSBO-7 is blended with at least two neighbors (H1 and H2) that can also be identified with the VLA sources. H2 is indistinguishable in 350 $\mu$m and seems disappeared from 500 $\mu$m, however H1 could persist in all three bands. To de-blend, we fit the SPIRE PSFs [^6] to the maps using Galfit at the VLA positions of COSBO-7, H1 and H2 simultaneously. As it turned out, de-blending all three sources were successful in 250 and 350 $\mu$m, with H2 of negligible flux in the latter band as expected. However, Galfit crashed if fitting all three simultaneously in 500 $\mu$m and would only run without fitting H2. Therefore, we discarded H2 when de-blending in this band. To convert from Jy beam$^{-1}$ (the unit of the SPIRE maps) to mJy, we used the beam solid angles of 469.35, 831.27 and 1804.31 arcsec$^2$ for 250, 350 and 500 $\mu$m, respectively, which are the values adopted by the Herschel SPIRE data reduction pipeline to produce these maps. To summarize, COSBO-7 has flux density of $16.58\pm5.36$, $26.03\pm9.68$ and $19.24\pm5.05$ mJy in 250, 350 and 500 $\mu$m, respectively. The quoted errors include the confusion noises of 3.32, 6.51 and 4.91 mJy (based on the HerMES final data release) in these three bands, respectively.

![](fig_spirephot.png)

# SED Fitting

![](fig_almaoverlay.png)

## Distribution of dust-embedded region

Figure [5](#fig:nircam_alma) compares the NIRCam and the ALMA images by superposing the ALMA 870 $\mu$m and 2.07 mm contours on the NIRCam residual image (i.e., after the removal of the foreground lens).

The comparison of the NIRCam and the ALMA images indicates that the dust-embedded star-forming region giving rise to the far-IR-to-mm emission does not cover the entire stellar population of the galaxy. This is shown in Figure [5](#fig:nircam_alma), where the ALMA 870 $\mu$m and 2.07 mm contours are superposed on the NIRCam color-composite image obtained after the removal of the foreground lens. Clearly, the arc has a more extended stellar light distribution than the dust emission: the 870 $\mu$m emission on the arc is concentrated on its southwestern part [^7], and so is the 2.07 mm emission.

There is another piece of evidence supporting a confined dust-embedded star-forming region in this galaxy, which comes from the flux ratio of the arc and its counter image. As mentioned in Section 3, this ratio is $11.7:1$ in the NIRCam F444W and is $5.3:1$ in the ALMA Band 7. Had the dusty region is well mixed with the underlying stellar population throughout the galaxy, the two ratios would be the same. Such a large discrepancy can be explained if the dusty region is confined to a limited area within the galaxy, which does not share the same magnification as the whole galaxy.

For this reason, we carry out SED fitting separately for the stellar population as detected in near-to-mid-IR and the dust-embedded starburst region as detected in far-IR-to-mm.

| Software | $z_{\rm ph}$ | $z_{\rm best}$ | $\chi^2$ | log$\rm\frac{\mu M_*}{M_\odot}$ | log($\rm \frac{\mu SFR}{M_\odot~yr^{-1}}$) | Age(Gyr) | $A_{\rm V}$ | E(B-V) | $Z_*$ | $\tau$(Gyr) |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| LePhare | $7.1^{+0.8}_{-0.0}$ | 7.1 | 11.3 | $11.16^{+0.08}_{-0.41}$ | $4.85^{+0.77}_{-0.56}$ | 0.1 | ... | 0.7 | 0.02 | 0.01 |
| EAZY | $7.26^{+0.35}_{-0.11}$ | 7.23 | 13.8 | $11.54 ^{+0.03}_{-0.03}$ | $2.68^{+0.07}_{-0.06}$ | ... | $0.69^{+0.8}_{-0.09}$ | ... | ... | ... |
| X-CIGALE | $7.54^{+0.25}_{-0.25}$ | 7.3 | 19.3 | $11.14^{+0.21}_{-0.43}$ | $3.53^{+0.24}_{-0.61}$ | 0.71 | ... | 0.5 | 0.02 | 0.14 |
| Bagpipes | $7.67^{+0.03}_{-0.03}$ | 7.67 | 20.0 | $10.56^{+0.08}_{-0.05}$ | $2.56^{+0.06}_{-0.05}$ | 0.01 | $1.93^{+0.04}_{-0.05}$ | ... | 0.07 | 4.96 |
| LePhare | $7.0^{+0.8}_{-0.2}$ | 7.0 | 11.3 | $11.51^{+0.11}_{-0.41}$ | $4.54^{+1.04}_{-0.28}$ | 0.07 | ... | 0.7 | 0.02 | 0.01 |
| EAZY | $6.97^{+0.21}_{-0.29}$ | 7.02 | 12.0 | $11.55^{+0.08}_{-0.13}$ | $2.63^{+0.24}_{-2.18}$ | ... | $0.77^{+0.23}_{-0.10}$ | ... | ... | ... |
| X-CIGALE | $7.03^{+1.1}_{-1.1}$ | 7.2 | 19.1 | $11.08^{+0.22}_{-0.48}$ | $3.46^{+0.25}_{-0.73}$ | 0.83 | ... | 0.5 | 0.02 | 0.15 |
| Bagpipes | $6.89^{+0.08}_{-0.14}$ | 6.89 | 27.6 | $11.13^{+0.25}_{-0.25}$ | $2.98^{+0.09}_{-0.18}$ | 0.16 | $1.90^{+0.07}_{-0.13}$ | ... | 0.05 | 5.25 |

: Physical properties of COSBO-7 from SED fitting

Table notes: $^{}$ Notes. The top four rows are for the SED using the F090W limit of 28.43 mag, while the bottom four rows are for that using the F090W limit of 26.98 mag. For LePhare, EAZY (EAZY+FAST) and X-CIGALE, the $z_{\rm ph}$ and $z_{\rm best}$ values are the mean photometric redshift weighted by $P(z)$ and that of the best-fit template, respectively. For Bagpipes, $z_{\rm ph}$ is the 50th percentile value with errors indicating the 16th and 84th percentiles, and $z_{\rm best}$ is the average of the 16th to 84th percentile. $\chi^2$ is the total (not reduced) value corresponding to $z_{\rm best}$. The estimates of stellar mass ($M_*$) and SFR are affected by the magnification factor $\mu$, and the quoted values ($\mu M_*$ and $\mu$SFR) are not de-magnified. The age derived by Bagpipes is the mass-weighted age. The dust extinction values are either given in terms of $A_{\rm V}$ or $E(B-V)$, depending on the software tool in use; for the Calzetti’s extinction law, $A_{\rm V}\approx 4.04\times E(B-V)$. $Z_*$ is metallicity, which is fixed to the solar metallicity in the LePhare run but is a free parameter in the X-CIGALE and Bagpipes runs. $\tau$ is the characteristic time scale of the exponentially declining SFH.

## Fitting of the SED based on JWST photometry

(cite: Pearson2024) fit to the combined SED that is the mixture of the emissions from both the arc and the foreground lens and obtained $z_{\rm ph}=3.4\pm0.4$ for the arc. Their SED incorporates the data from the Sloan Digital Sky Survey to MAMBO; in terms of the JWST data, however, they only used the two-band MIRI imaging data. Obviously, there is a vast room for improvement in both the data utilization and the fitting method. We performed a full analysis of the SED of the arc, using the JWST photometry summarized in Table [1](#tab:jwstphot). Considering that the removal of the foreground galaxy is not perfect, we added (in quadrature) 10% of the fluxes to the errors.

It is well known that SED fitting results depend on the fitting software as well as the models that it employs, and therefore we utilized four different tools, namely, LePhare (cite: Arnouts1999; Ilbert2006), the python version of EAZY (cite: Brammer2008), Bagpipes (cite: Carnall2018), and CIGALE (cite: Burgarella2005; Noll2009; Boquien2019). The redshift was allowed to vary from 0 to 10, and no prior was applied.

The fitting by LePhare used the population synthesis models of (cite: Bruzual2003) with solar metallicity and the initial mass function (IMF) of (cite: Chabrier2003). The templates were constructed assuming exponentially declining star formation histories (SFHs) in the form of SFR $\propto e^{-t/\tau}$, where $\tau$ ranged from 0 to 13 Gyr (0 for simple stellar population and 13 Gyr to approximate constant star formation). LePhare allows the use of magnitude limits, which we enabled so that any solutions violating the F090W limit were rejected.

In the EAZY run, we used the “tweak_fsps_QSF_12_v3” templates, which are a modified version of the original Flexible Stellar Population Synthesis models (cite: Conroy2010) tailored for galaxies at high redshifts (cite: Finkelstein2022; Larson2023). These templates use the Kroupa IMF (cite: Kroupa2001). For CIGALE, we used the 2022.1 version (cite: YangCIGALE2022) of the program and the BC03 model with the Chabrier IMF. The adopted SFHs were the delayed-$\tau$ model, with other settings similar to the SFHs used in the LePhare run. The age of the stellar population was limited to $>10$ Myr, and the AGN contribution was set to 0. The metallicity was allowed to vary between $0 \le Z_{*}/Z_{\odot} \le 2.5$. The range of the ionization parameter was set to $-3\le {\rm log}(U)\le -2$. For the Bagpipes run, we also used the delayed-$\tau$ model and other settings similar to the CIGALE run, with the exception that the ionization parameter was fixed to ${\rm log}(U)=-3$.

We note that its underlying stellar population synthesis models are those of BC03 with the Kroupa IMF. For LePhare, CIGALE and Bagpipes, we adopted the Calzetti’s dust extinction law (cite: Calzetti1994; Calzetti2001) with $E(B-V)$ ranging from 0 to 1.0 mag. The templates used in the EAZY run have also adopted the same extinction law but the amount is hardwired within.

EAZY, CIGALE and Bagpipes do not directly use magnitude limits; following a common practice, we set the flux density and its error in F090W to the magnitude limit quoted in Table [1](#tab:jwstphot).

The results from these four different tools are given in Table [\[tab:sedfit\]](#tab:sedfit) separately for the two choices of the F090W upper limit. Interestingly, they suggest that a high redshift of COSBO-7 is very likely, which ranges from $\sim$6.9 to 7.7. This is demonstrated in Figure [6](#fig:sedjwst) using the results corresponding to the “$z_{\rm best}$” column in Table [\[tab:sedfit\]](#tab:sedfit). Of course, we cannot rule out the low-redshift possibility due to the nature of SED fitting. In Appendix [8](#forcelowz), we present the fitting results when forcing the redshift to $z\leq 6$. These solutions, however, all have significantly worse $\chi^2$, with $\Delta \chi^2 \approx 16$–65 and 6–9 when adopting 28.43 and 26.98 mag as the F090W upper limit, respectively.

Therefore, it is fair to say that our results are more in favor of a high-redshift interpretation at $z > 7$. During the revision of this paper, a new set of ALMA Band 3 spectroscopic data became publicly available. We detected a single line in these data, which could be the CO (7-6) line at $z=7.455$ (see Appendix [9](#almab3)). Such a redshift, if confirmed, will put COSBO-7 among the earliest DSFGs in the universe known to date.

Another interesting point is that the derived stellar mass is consistent among the four sets (within $\sim$1 dex) but the SFR varies by 1–2 dex. The discrepant SFR derivations are largely due to the different templates in use. Firstly, the inclusion of nebular continuum emission matters. The LePhare run is the only one whose templates do not include nebular continuum emission (albeit with *ad hoc* line emission), and therefore the UV light must be accounted for by using only stars, which tends to result in a high SFR estimate. Secondly, and probably more importantly, the adopted SFH plays a significant role. This is because explaining the strong UV emission of our object must involve a large number of high-mass stars of very young ages, and the adopted SFHs can result in large differences when confined to a short time interval due to the young age of the universe at the derived redshift. The SFH of the BC03 templates used in the LePhare run has an exponentially declining SFR (the classic “$\tau$” model). The small $\tau$ (10 Myr) and young age (70–100 Myr) of the best-fit template means that the inferred stellar population is very close to an instantaneous burst at its beginning, and therefore it must have a very high SFR. Indeed, the LePhare run gave the highest SFR estimate. The X-CIGALE run, which had the same underlying BC03 model as the LePhare run, gave 0.9–1.3 dex lower SFR (the second highest). This can be attributed to its delayed-$\tau$ SFH, which stretches the star formation process to a longer time scale (i.e., not so close to an instantaneous burst), leading to a smaller SFR. Similar arguments can be made to explain the SFR derived by the Bagpipes run.

The EAZY-py run gave a comparable SFR estimate as the Bagpipes run, and this is mostly because the adopted SFH spreads the formation of stars to a few discrete events.

For the sake of completeness, we also fit the SED of the lens. The results are given in Appendix [10](#sedlens).

![](fig_sedjwst.png)

## Fitting of the far-IR-to-mm SED

We used a modified black body (MBB) model to fit the far-IR-to-mm SED constructed from the Herschel and ALMA photometry in Table [\[tab:almaherschel\]](#tab:almaherschel) and the COSBO MAMBO-2 measurement at 1.2 mm in Table [\[tab:literature\]](#tab:literature). Other measurements in Table [\[tab:literature\]](#tab:literature) are not included in the SED for various reasons: the AzTEC 1.1 mm result is of low S/N, the SCUBA-2 450 $\mu$m result is likely contaminated by an unrelated close neighbor (as judged from the Herschel SPIRE images) and cannot be de-blended, and the SCUBA-2 850 $\mu$m results are superseded by the ALMA 870 $\mu$m measurement. In this regime, the ALMA 870 $\mu$m image is the only one of a high enough resolution that separates the two lensed images of COSBO-7, and we combined the two so that the result in this band could be used together with those at other wavelengths. The combined flux density is $S_{870}=10.55\pm1.06$ mJy.

Following (cite: MY2015) and (cite: Yan2016), we used the single-temperature MBB model in this form: $$\begin{equation}
\label{eq:mbb}
\begin{split} 
     S_{\lambda}(\lambda) & \equiv N \cdot I_{\rm mbb}(\lambda)\\
                & = N\frac{1-\mathrm{e}^
         {-(\frac{\lambda_0}{\lambda})^{\beta}}}{1-\mathrm{e}^{-1}}
     \frac{(\frac{2hc^2}{\lambda^5})}{\mathrm{e}^{hc/(\lambda kT_{\rm mbb})}-1} \,,
\end{split}
\end{equation}$$ where $T_{\rm mbb}$ is the characteristic temperature of the MBB, $N$ is the scaling factor that is related to the luminosity, $\beta$ is the emissivity, and $\lambda_0$ is the reference wavelength where the opacity is unity. We set $\lambda_0=100$ $\mu$m. As $\beta$ affects $T_{\rm mbb}$, the fit was done using three different choices of $\beta=1.5$, 2.0 and 2.5. We fixed the redshift to $z=7.455$ (see Appendix A).

The results are shown in Figure [10](#fig:mbbfit). Regardless of the choice of $\beta$, the fit gives a high dust temperature of $T_{\rm mbb}>90$ K. This is significantly higher than the dust temperature of $\sim$40–60 K often seen in the SMGs at $z\approx 2$–4.

The reported $L^{\prime}_{\rm FIR}$ values in Figure [10](#fig:mbbfit) are the far-IR luminosity integrated from 60 to 1000 $\mu$m in the rest-frame. Note that the fit was done by combining the two lensed images. Assuming that the split of $L^{\prime}_{\rm FIR}$ between the two follows the flux density ratio of 5.3 in ALMA 870 $\mu$m (see Table [\[tab:almaherschel\]](#tab:almaherschel)), the main image (corresponding to the arc seen in the JWST images) has $\mu_d L_{\rm FIR}=6.7\times 10^{12} L_\odot$ for $\beta=1.5$ and $8.4\times 10^{12} L_\odot$ for $\beta=2.0$ and 2.5. To obtain the intrinsic $L_{\rm FIR}$, these values should be divided by the lensing amplification factor $\mu_d$ of the dusty region (see Section 5).

From $L_{\rm FIR}$, one can infer the SFR of the dust-embedded population. Using the standard $L_{\rm IR}$ to SFR conversion of (cite: Kennicutt1998), i.e., ${\rm SFR_{IR}} = 1.0\times 10^{-10} L_{\rm IR}/L_\odot$ for a Chabrier IMF, and ignoring the difference between $L_{\rm FIR}$ and $L_{\rm IR}$, the $\mu_d L_{\rm FIR}$ values quoted above correspond to $\mu_d {\rm SFR_{IR}} = 670$ and 840 $M_\odot$ yr$^{-1}$, respectively.

Lastly, the dust mass $M_d$ can also be derived from the MBB fit, for which we followed the recipe of the cmcirsed code by (cite: Casey2012). Again, the reported $M^{\prime}_d$ values in Figure [10](#fig:mbbfit) are for the two images combined and are not corrected for the lensing magnification. Using the same split of $5.3:1$ as above for the two images, we obtain the dust mass based on the main image $\mu_d M_d = 1.1$, 1.6, and $2.3\times 10^8 M_\odot$ for $\beta=1.5$, 2.0 and 2.5, respectively.

![](fig_mbb.png)

# Lens modeling

To obtain the intrinsic luminosity and morphology of COSBO-7, we re-constructed its image in the source plane by modeling the residual F444W image where the foreground lens is subtracted. We utilized the Pipeline for Images of Cosmological Strong lensing (cite: Li2016PICS) and the Affine Invariant Markov chain Monte Carlo Ensemble sampler (cite: DFM2013EMCEE). The mass model of the lens was a Singular Isothermal Ellipsoid (cite: Kormann1994), which is analytically tractable and has also been shown to be applicable in similar strong lensing cases

(cite: Koopmans2006; Gavazzi2007; Dye2008). The convergence map is given by $$\begin{equation}
    \kappa(x, y)= \frac{\theta_{\rm E}}{2}\frac{1}{\sqrt{x^2/q+y^2 q}} \;,
\end{equation}$$ where $q$ is the axis ratio of the lens and $\theta_{\rm E}$ is the Einstein radius. The environmental lensing effects are modeled with external shear $(\gamma^{ext}_1, \gamma^{ext}_2)$. The light distribution of the source is an elliptical Sérsic profile (cite: Sersic1968) following $$\begin{equation}
I(R) =  I_{\rm eff}~{\rm exp} \left\lbrace -b_{n} \left[ \left( \frac{R}{R_{\rm eff}}\right)^{1/n} - 1 \right ] \right\rbrace \, ,
\end{equation}$$ where $R = \sqrt[]{x^2 /q+y^2 q }$, $R_{\rm eff}$ is the effective radius in arc-second, $I_{\rm eff}$ is the intensity at the effective radius, and $n$ is the index of the Sérsic profile. Assuming that the center of mass aligns with the center of light and that the scaling factor $I_{\rm eff}$ can be reduced by normalizing both the observation and source model, the strong lensing system can be fully described by using $\{\theta_{\rm E}, e^l_1, e^l_2, \gamma^{ext}_1, \gamma^{ext}_2\}$ plus $\{y^{s}_{1}, y^{s}_{2}, R^s_{\rm eff}, e^s_1, e^s_2, n^s\}$, where $\{e^l_1, e^l_2\}$ and $\{e^s_1, e^s_2\}$ are the complex ellipticity of the lens and the source, respectively, and $\{y^{s}_{1}, y^{s}_{2}\}$ is the angular position of the source in the source plane. The relation between $\{q, \phi\}$ and $\{e_1, e_2\}$ is given by $$\begin{eqnarray}
    q & = & (1 - e)/(1 + e) \\
    \phi & = & 1/2\,{\rm arctan}(e_2/e_1)\, ,
\end{eqnarray}$$ where $e = \sqrt{e_1^2 + e_2^2}$.

To fit the data, we designed the likelihood below: $$\begin{equation}
    \mathcal{L} = \sum \frac{(img^{mdl}_{i}-img^{obs}_{i})^2}{wht_{i}}msk_{i}\, ,
\end{equation}$$ where $img^{obs}$ and $img^{mdl}$ are the observed image and that generated by the model, respectively, $wht$ is the weight map reflecting the relative noise properties of $img^{obs}$, $msk$ is the mask file that retains only valid pixels for the modeling, and $i$ is the index of pixels. We first found the best-fit results using the `optimize.minimize` function in SCIPY (cite: scipy2020)[^8] and then used EMCEE[^9] to explore the posterior distributions of the parameters of $\{\theta_{\rm E}, e^l_1, e^l_2, \gamma^{ext}_1, \gamma^{ext}_2, y^{s}_{1}, y^{s}_{2}, R^s_{\rm eff}, e^s_1, e^s_2, n^s, F_{scale}\}$. The above modeling procedure was implemented on angular scales without assuming redshifts of the lens and the source. Table [\[tab:bestfits\]](#tab:bestfits) lists the medians and 1 $\sigma$ confidential intervals of the posteriors.

| $\theta_{\rm E}\,(^{\prime\prime})$ | $e^{l}_1$ | $e^{l}_2$ | $\gamma^{ext}_1$ | $\gamma^{ext}_2$ | $y^{s}_1\,(^{\prime\prime})$ | $y^{s}_2\,(^{\prime\prime})$ | $r^{s}_{eff}\,(^{\prime\prime})$ | $e^{s}_1$ | $e^{s}_2$ | $n^s$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $0.59^{+0.06}_{-0.08}$ | $0.17^{+0.05}_{-0.07}$ | $0.14^{+0.06}_{-0.06}$ | $-0.13^{+0.06}_{-0.08}$ | $-0.02^{+0.10}_{-0.08}$ | $0.44^{+0.06}_{-0.04}$ | $0.25^{+0.03}_{-0.06}$ | $0.16^{+0.01}_{-0.01}$ | $0.56^{+0.11}_{-0.11}$ | $-0.45^{+0.12}_{-0.12}$ | $0.24^{+0.08}_{-0.06}$ |

: The medians and 1-$\sigma$ uncertainties of the posteriors of the lens model

Table notes: $^{}$ Notes. As the modeling procedure is in angular scale, the units of $\theta_{\rm E}$, $y^s_1$, $y^s_2$, and $r^s_{eff}$ are arcsec. The estimate of each parameter is the median of the corresponding posterior, and the 1 $\sigma$ uncertainties are estimated by using the confidential interval of $[16\%,\,84\%]$.

According to the parameters given in Table [\[tab:bestfits\]](#tab:bestfits), we generate the model-predicted images of the source and the lensed arc, which are shown in Figure [8](#fig:lensmodel). Interestingly, the best-fitted Sérsic model of the source has $n^s=0.24$ and an axis ratio of $\sim$0.16, suggesting that it is a nearly edge-on disk galaxy. The disk extends to at least 1.6$''$ along the major axis, which corresponds to $\sim$8.1 kpc at $z_s=7.455$. Its small effective radius (0.16$''$, or 0.81 kpc) is to say that its star light distribution is rather concentrated to the central region.

From the reconstructed model, we can also get the flux of the object in the source plane ($F_{src}$) and that of the arc in the image plane ($F_{arc}$), which can be easily calculated by summing the pixels. In this way, we obtain the lensing magnification of the entire galaxy $\mu= F_{arc}/F_{src} = 2.54$. However, the magnification of the dusty region, $\mu_d$, is different from this value because it is confined within a limited region but not spread over the entire galaxy (see Section 4.1). To estimate $\mu_d$, we take a different approach. As the reconstruction also resulted in a magnification map, we trace the position of the peak of the ALMA 870 $\mu$m emission (see Table [\[tab:almaherschel\]](#tab:almaherschel)) to this map and take the average value of a $3\times 3$ pixel region around this position as $\mu_d$, which is $\mu_d=3.62\pm0.49$.

Figure [8](#fig:lensmodel) shows that our lens model also produces a faint counter image at the position largely coinciding the observed one. The flux ratio between the arc and its counter-image is $\sim$12.1 in our model, which is consistent with the measured ratio of $\sim$11.7 (see Section 4.1).

We also note that there are three distinct clumps on the arc. After deconvolving the observed F444W image by its PSF, we reconstruct the light distribution of the source by tracing light rays back to the source plane, and the three clumps are identified in the reconstructed source. The corresponding positions of the clumps in the observed arc are marked by a black square, cross and triangle, respectively. The peak of the ALMA emission lies in between the cross and the triangle.

To estimate the halo mass of the lens, we make use of the Einstein radius $\theta_{\rm E}$, which is related to the redshift of the lens $z_l$, the redshift of the source $z_s$ and the velocity dispersion $\sigma_v$ of the lens galaxy as $$\begin{equation}
\theta_{\rm E} = 4\pi\left(\frac{\sigma_v}{c}\right)^2 \frac{D_{ls}(z_l,z_s)}{D_{s}(z_s)} \ ,
\label{eq:ThetaE}
\end{equation}$$ where $c$ is the speed of light, $D_{ls}$ and $D_{s}$ are the angular diameter distance from the source plane to the lens plane and from the source plane to the observer, respectively. Using $z_l = 0.359$, $z_s = 7.455$ and $\theta_{\rm E} =$ 0.59$''$, we get the velocity dispersion $\sigma_v \approx 156$ km s$^{-1}$. Therefore, the viral mass of the lens is $\sim$$2.6\times10^{12} M_{\odot}$.

As shown in Appendix [10](#sedlens), the stellar mass of the lens is $\sim$$3.8\times10^{10} M_\odot$. The ratio of the two is $\sim$68, which is reasonable for a dark-matter-dominated galaxy.

![](fig_lens_modeling_results.pdf)

# Discussion

Considering its $z_{\rm ph}\gtrsim 7$ (and possibly at $z=7.455$; see Appendix [9](#almab3)), the most striking feature of COSBO-7 is its disk morphology in the source plane. To maintain such an extended thin disk, the galaxy must be fast rotating. Currently, the earliest fast-rotating galaxy confirmed by spectroscopy is “Twister-5” at $z=5.3$ (cite: Nelson2023). If confirmed at $z\gtrsim 7$, COSBO-7 will set a new redshift record for disk galaxies and further challenge the existing models where such galaxies always form late.

After de-magnifying by $\mu_d=3.62$, the SFR of COSBO-7 in the dusty region is ${\rm SFR_{IR}} =$ 185–232 $M_\odot$ yr$^{-1}$, which makes it a starburst regardless of the choice of $\beta$ in the MBB fit. As shown in Figure [10](#fig:mbbfit), it has a very high dust temperature of $\sim$92–126 K (differences due to different $\beta$), which is even higher than the hot-dust DSFGs ($\sim$52$\pm$10 K) at $z\approx 1$–2 selected by mid-IR (cite: Casey2009). On the other hand, given that the temperature of the cosmic microwave background is $\sim$23.1 K at $z=7.5$, such a higher dust temperature at this redshift probably is not very surprising.

As shown in (cite: Yan2016), the $L_{\rm FIR}$-T relation of DSFGs is a manifest of the “modified” Stefan-Boltzmann law, based on which the effective size of the dust emission region (approximated by a sphere) can be obtained. From its dust temperature and intrinsic $L_{\rm FIR}$ (6.7–8.4$\times 10^{12}L_\odot$), the size of the dusty starburst region should be only $\sim$0.15–0.25 kpc in radius based on Figure 2 of (cite: Yan2016). This is consistent with its being confined to a limited region within the host galaxy as argued in Section 4.1. The moderate extinction derived from the exposed stellar population (as detected in the JWST images) is also consistent with a dusty region of a limited size.

Another notable feature of COSBO-7 is that its exposed stellar population is unusually bright for an object at $z\gtrsim 7$. Taking $\mu=2.54$ into account, its de-magnified brightness is 24.8 to 22.9 mag in the NIRCam bands from F200W to F444W (rest-frame $\sim$2300–5060Å), and it could be easily detected without the lensing magnification. Such a brightness in rest-frame UV-to-optical, contributed by the entire disk, can only be due to active, ongoing star formation all over the disk. Its inferred intrinsic (de-magnified) SFR ranges from 143 $M_\odot$ yr$^{-1}$ to $2.8\times 10^4$ $M_\odot$ yr$^{-1}$.

Even the lowest SFR estimate qualifies it as a starburst, and it is possible that it could even be higher than that in the dusty starburst region. To answer the question posed in Section 1, the exposed stellar population of COSBO-7 itself could be a starburst-LBG in the epoch of EoR.

This exposed stellar population is peculiar also because of its huge stellar mass as derived. After de-magnifying by $\mu=2.54$, the stellar mass values reported in Table [\[tab:sedfit\]](#tab:sedfit) correspond $M_*=1.4\times 10^{10}$ to $14.0\times 10^{10}M_\odot$. Even the lowest estimate is $>10^{10}M_\odot$, which is very high for galaxies at $z>7$: as the age of the universe is only $\sim$700 Myr at $z\approx 7.5$, how could it have enough time to turn gas into such a huge amount of stars? Nonetheless, the age estimates are all very small (70–190 Myr), which at least offer a self-consistent picture that the starbursting disk formed all its stars extremely quickly.

Finally, we comment on the dust mass in the dusty starburst region. After de-magnifying by $\mu_d=3.62$, we get $M_d=3.1$, 4.5 and $6.3\times 10^7 M_\odot$ for $\beta=1.5$, 2.0 and 2.5, respectively, which are very large for $z\approx 7.5$. In order to explain such a huge amount of dust mass, supernovae must be invoked as the contributors (cite: Mancini2015). Given the high SFR as discussed above, it is possible to have a high rate of supernova since its formation to generate the necessary amount of dust.

# Summary

Using the recent JWST NIRcam and MIRI data, we have studied the true near-to-mid-IR counterpart of COSBO-7, an SMG known for more than sixteen years but not correctly identified in the existing HST images. It is in fact a background, very red galaxy strongly lensed by a foreground galaxy at $z=0.36$ and is only significantly detected at $\lambda>2$ $\mu$m. Fitting its SED constructed from the NIRCam and MIRI photometry, our analysis gives solutions in favor of $z_{\rm ph}>7$. Due to the statistical nature of the photometric redshift technique, the low-redshift possibility cannot be ruled out; however, the high-redshift possibility at $z>7$ is more likely and cannot be dismissed. The single-line detection in the ALMA Band 3 data would further put it to $z=7.455$ if the line is due to the CO (7-6) transition. Surprisingly, our redshift-independent lens modeling shows that it is a thin edge-on disk subtending at least 1.6$''$ in the source plane, which corresponds to $\sim$8.1 kpc at $z=7.5$. The galaxy as a whole is magnified by a factor of $\mu=2.54$, and the de-magnified brightness in NIRCam would still make it one of the brightest F090W-dropouts (candidates at $z\approx 7$) known to date (22.9 mag in F444W). The inferred intrinsic SFR from the four SED fitting tools ranges from of 143 $M_\odot$ yr$^{-1}$ to $2.8\times 10^4$ $M_\odot$ yr$^{-1}$, which means that the entire stellar disk is experiencing starburst.

The dusty star forming region of COSBO-7 is best revealed by the sub-arcsec ALMA 870 $\mu$m data, which show that the dust emission is on one side of the galaxy and does not cover the whole stellar disk. The far-IR-to-mm SED constructed using the Herschel, ALMA and MOMBO-2 data can be well fitted by a single-temperature MBB model, with a high dust temperature of $\sim$92–126 K. We argue that this dusty region is confined within a limited region ($\sim$0.15–0.25 kpc in radius) in the galaxy. It is magnified by a larger factor of $\mu_d=3.62$, and the intrinsic SFR inferred from its de-magnified far-IR luminosity is 185–232 $M_\odot$ yr$^{-1}$. In other words, the dusty region alone is also experiencing starburst.

If it is confirmed at $z>7$ by spectroscopy, all the above will make COSBO-7 the most exotic galaxy in the EoR. Its stellar mass is $\sim$$10^{10-11}M_\odot$, and it must have formed nearly all its stars in $\sim$70–190 Myr through starburst over the entire galaxy. How it could keep its think disk intact is puzzling, especially when considering that it must have gone through multiple episodes of intense supernova explosion to generate the large amount of dust ($>10^7M_\odot$) necessary to explain the far-IR-to-mm emission. To say the least, COSBO-7 will exacerbate the challenging situation that the current picture of early galaxy formation has been facing since the first batch of JWST data were delivered to the community. Further investigations of this object, especially the kinematics study that can be enabled by the JWST IFU capabilities, will be critical.

All the JWST data used in this paper can be found in MAST: .

# Acknowledgements

We thank the referee for the thoughtful comments, which improve the quality of this paper. CL acknowledges the support from the Special Research Assistant program of the Chinese Academy of Sciences (CAS). HY and BS acknowledge the support from the NSF grant AST-2307447. NL acknowledge the support from the science research grants from the China Manned Space Project (No. CMS-CSST-2021-A01), the CAS Project for Young Scientists in Basic Research (No. YSBR-062), and the Ministry of Science and Technology of China (No. 2020SKA0110100). ZM is supported by the NSF grants No. 1636621, 2034318, and 2307448. CC is supported by the National Natural Science Foundation of China, No. 11933003, 12173045. This work is sponsored (in part) by the CAS, through a grant to the CAS South America Center for Astronomy (CASSACA). We acknowledge the science research grants from the China Manned Space Project with No. CMS- CSST-2021-A05.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00705.S, ADS/JAO.ALMA#2016.1.00463.S, and ADS/JAO.ALMA#2022.1.00863.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. The ALMA data reduction services of this work are supported by the China-Chile Astronomical Data Center (CCADC), which is affiliated with the Chinese Academy of Sciences South America Center for Astronomy (CASSACA).

natexlab

(ref: Aaronson1984) Aaronson, M., & Olszewski, E. W. 1984, Nature, 309, 414, doi: [`10.1038/309414a0`](http://doi.org/10.1038/309414a0)

(ref: AM2023) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671, A105, doi: [`10.1051/0004-6361/202245400`](http://doi.org/10.1051/0004-6361/202245400)

(ref: Aretxaga2011) Aretxaga, I., Wilson, G. W., Aguilar, E., et al. 2011, MNRAS, 415, 3831, doi: [`10.1111/j.1365-2966.2011.18989.x`](http://doi.org/10.1111/j.1365-2966.2011.18989.x)

(ref: Arnouts1999) Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999, MNRAS, 310, 540, doi: [`10.1046/j.1365-8711.1999.02978.x`](http://doi.org/10.1046/j.1365-8711.1999.02978.x)

(ref: Bakx2020) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294, doi: [`10.1093/mnras/staa509`](http://doi.org/10.1093/mnras/staa509)

(ref: Barger2023) Barger, A. J., & Cowie, L. L. 2023, ApJ, 956, 95, doi: [`10.3847/1538-4357/acedae`](http://doi.org/10.3847/1538-4357/acedae)

(ref: Barger2000) Barger, A. J., Cowie, L. L., & Richards, E. A. 2000, AJ, 119, 2092, doi: [`10.1086/301341`](http://doi.org/10.1086/301341)

(ref: Bertoldi2007) Bertoldi, F., Carilli, C., Aravena, M., et al. 2007, ApJS, 172, 132, doi: [`10.1086/520511`](http://doi.org/10.1086/520511)

(ref: Bethermin2020) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2, doi: [`10.1051/0004-6361/202037649`](http://doi.org/10.1051/0004-6361/202037649)

(ref: Blain2002) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002, Phys. Rep., 369, 111, doi: [`10.1016/S0370-1573(02)00134-5`](http://doi.org/10.1016/S0370-1573(02)00134-5)

(ref: Boogaard2023) Boogaard, L. A., Gillman, S., Melinder, J., et al. 2023, arXiv e-prints, arXiv:2308.16895, doi: [`10.48550/arXiv.2308.16895`](http://doi.org/10.48550/arXiv.2308.16895)

(ref: Boquien2019) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103, doi: [`10.1051/0004-6361/201834156`](http://doi.org/10.1051/0004-6361/201834156)

(ref: Brammer2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503, doi: [`10.1086/591786`](http://doi.org/10.1086/591786)

(ref: Bruzual2003) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: Burgarella2005) Burgarella, D., Buat, V., & Iglesias-Páramo, J. 2005, MNRAS, 360, 1413, doi: [`10.1111/j.1365-2966.2005.09131.x`](http://doi.org/10.1111/j.1365-2966.2005.09131.x)

(ref: Calzetti2001) Calzetti, D. 2001, PASP, 113, 1449, doi: [`10.1086/324269`](http://doi.org/10.1086/324269)

(ref: Calzetti1994) Calzetti, D., Kinney, A. L., & Storchi-Bergmann, T. 1994, ApJ, 429, 582, doi: [`10.1086/174346`](http://doi.org/10.1086/174346)

(ref: Capak2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455, doi: [`10.1038/nature14500`](http://doi.org/10.1038/nature14500)

(ref: Carnall2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379, doi: [`10.1093/mnras/sty2169`](http://doi.org/10.1093/mnras/sty2169)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Casey2012) Casey, C. M. 2012, MNRAS, 425, 3094, doi: [`10.1111/j.1365-2966.2012.21455.x`](http://doi.org/10.1111/j.1365-2966.2012.21455.x)

(ref: Casey2014) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: Casey2009) Casey, C. M., Chapman, S. C., Beswick, R. J., et al. 2009, MNRAS, 399, 121, doi: [`10.1111/j.1365-2966.2009.15291.x`](http://doi.org/10.1111/j.1365-2966.2009.15291.x)

(ref: Casey2013) Casey, C. M., Chen, C.-C., Cowie, L. L., et al. 2013, MNRAS, 436, 1919, doi: [`10.1093/mnras/stt1673`](http://doi.org/10.1093/mnras/stt1673)

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Chapman2003) Chapman, S. C., Blain, A. W., Ivison, R. J., & Smail, I. R. 2003, Nature, 422, 695, doi: [`10.1038/nature01540`](http://doi.org/10.1038/nature01540)

(ref: Chen2022) Chen, C.-C., Gao, Z.-K., Hsu, Q.-N., et al. 2022, ApJL, 939, L7, doi: [`10.3847/2041-8213/ac98c6`](http://doi.org/10.3847/2041-8213/ac98c6)

(ref: Cheng2022) Cheng, C., Yan, H., Huang, J.-S., et al. 2022, ApJL, 936, L19, doi: [`10.3847/2041-8213/ac8d08`](http://doi.org/10.3847/2041-8213/ac8d08)

(ref: Cheng2023) Cheng, C., Huang, J.-S., Smail, I., et al. 2023, ApJL, 942, L19, doi: [`10.3847/2041-8213/aca9d0`](http://doi.org/10.3847/2041-8213/aca9d0)

(ref: Conroy2010) Conroy, C., & Gunn, J. E. 2010, ApJ, 712, 833, doi: [`10.1088/0004-637X/712/2/833`](http://doi.org/10.1088/0004-637X/712/2/833)

(ref: daCunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: deJong1984) de Jong, T., Clegg, P. E., Soifer, B. T., et al. 1984, ApJL, 278, L67, doi: [`10.1086/184225`](http://doi.org/10.1086/184225)

(ref: Dunlop2021) Dunlop, J. S., Abraham, R. G., Ashby, M. L. N., et al. 2021, PRIMER: Public Release IMaging for Extragalactic Research, JWST Proposal. Cycle 1, ID. #1837

(ref: Dye2008) Dye, S., Evans, N. W., Belokurov, V., Warren, S. J., & Hewett, P. 2008, MNRAS, 388, 384, doi: [`10.1111/j.1365-2966.2008.13401.x`](http://doi.org/10.1111/j.1365-2966.2008.13401.x)

(ref: Finkelstein2022) Finkelstein, S. L., Bagley, M., Song, M., et al. 2022, ApJ, 928, 52, doi: [`10.3847/1538-4357/ac3aed`](http://doi.org/10.3847/1538-4357/ac3aed)

(ref: 2014Msngr.155...19F) Fomalont, E., van Kempen, T., Kneissl, R., et al. 2014, The Messenger, 155, 19

(ref: DFM2013EMCEE) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: Fujimoto2023) Fujimoto, S., Finkelstein, S. L., Burgarella, D., et al. 2023, ApJ, 955, 130, doi: [`10.3847/1538-4357/aceb67`](http://doi.org/10.3847/1538-4357/aceb67)

(ref: Gavazzi2007) Gavazzi, R., Treu, T., Rhodes, J. D., et al. 2007, ApJ, 667, 176, doi: [`10.1086/519237`](http://doi.org/10.1086/519237)

(ref: Geach2017) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789, doi: [`10.1093/mnras/stw2721`](http://doi.org/10.1093/mnras/stw2721)

(ref: Grogin2011) Grogin, N. A., Kocevski, D. D., Faber, S. M., et al. 2011, ApJS, 197, 35, doi: [`10.1088/0067-0049/197/2/35`](http://doi.org/10.1088/0067-0049/197/2/35)

(ref: Hashimoto2019a) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71, doi: [`10.1093/pasj/psz049`](http://doi.org/10.1093/pasj/psz049)

(ref: Hashimoto2023) Hashimoto, T., Álvarez-Márquez, J., Fudamoto, Y., et al. 2023, ApJL, 955, L2, doi: [`10.3847/2041-8213/acf57c`](http://doi.org/10.3847/2041-8213/acf57c)

(ref: Hasinger2018) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77, doi: [`10.3847/1538-4357/aabacf`](http://doi.org/10.3847/1538-4357/aabacf)

(ref: Houck1985) Houck, J. R., Schneider, D. P., Danielson, G. E., et al. 1985, ApJL, 290, L5, doi: [`10.1086/184431`](http://doi.org/10.1086/184431)

(ref: Houck1984) Houck, J. R., Soifer, B. T., Neugebauer, G., et al. 1984, ApJL, 278, L63, doi: [`10.1086/184224`](http://doi.org/10.1086/184224)

(ref: Huang2023) Huang, S., Kawabe, R., Kohno, K., et al. 2023, ApJL, 958, L26, doi: [`10.3847/2041-8213/acff63`](http://doi.org/10.3847/2041-8213/acff63)

(ref: Ilbert2006) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841, doi: [`10.1051/0004-6361:20065138`](http://doi.org/10.1051/0004-6361:20065138)

(ref: Kamieneski2023) Kamieneski, P. S., Frye, B. L., Pascale, M., et al. 2023, ApJ, 955, 91, doi: [`10.3847/1538-4357/aceb4a`](http://doi.org/10.3847/1538-4357/aceb4a)

(ref: Kennicutt1998) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: Killi2024) Killi, M., Ginolfi, M., Popping, G., et al. 2024, arXiv e-prints, arXiv:2402.07982, doi: [`10.48550/arXiv.2402.07982`](http://doi.org/10.48550/arXiv.2402.07982)

(ref: Koekemoer2011) Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36, doi: [`10.1088/0067-0049/197/2/36`](http://doi.org/10.1088/0067-0049/197/2/36)

(ref: Kokorev2023) Kokorev, V., Jin, S., Magdis, G. E., et al. 2023, ApJL, 945, L25, doi: [`10.3847/2041-8213/acbd9d`](http://doi.org/10.3847/2041-8213/acbd9d)

(ref: Koopmans2006) Koopmans, L. V. E., Treu, T., Bolton, A. S., Burles, S., & Moustakas, L. A. 2006, ApJ, 649, 599, doi: [`10.1086/505696`](http://doi.org/10.1086/505696)

(ref: Kormann1994) Kormann, R., Schneider, P., & Bartelmann, M. 1994, A&A, 284, 285

(ref: 2018ascl.soft03008K) Kriek, M., van Dokkum, P. G., Labbé, I., et al. 2018, FAST: Fitting and Assessment of Synthetic Templates, Astrophysics Source Code Library, record ascl:1803.008

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24, doi: [`10.3847/0067-0049/224/2/24`](http://doi.org/10.3847/0067-0049/224/2/24)

(ref: Larson2023) Larson, R. L., Hutchison, T. A., Bagley, M., et al. 2023, ApJ, 958, 141, doi: [`10.3847/1538-4357/acfed4`](http://doi.org/10.3847/1538-4357/acfed4)

(ref: Li2016PICS) Li, N., Gladders, M. D., Rangel, E. M., et al. 2016, ApJ, 828, 54, doi: [`10.3847/0004-637X/828/1/54`](http://doi.org/10.3847/0004-637X/828/1/54)

(ref: LY2022) Ling, C., & Yan, H. 2022, ApJ, 929, 40, doi: [`10.3847/1538-4357/ac57c1`](http://doi.org/10.3847/1538-4357/ac57c1)

(ref: Liu2019) Liu, D., Lang, P., Magnelli, B., et al. 2019, ApJS, 244, 40, doi: [`10.3847/1538-4365/ab42da`](http://doi.org/10.3847/1538-4365/ab42da)

(ref: Liu2023) Liu, Z., Silverman, J. D., Daddi, E., et al. 2023, arXiv e-prints, arXiv:2311.14809, doi: [`10.48550/arXiv.2311.14809`](http://doi.org/10.48550/arXiv.2311.14809)

(ref: Lonsdale1984) Lonsdale, C. J., Persson, S. E., & Matthews, K. 1984, ApJ, 287, 95, doi: [`10.1086/162666`](http://doi.org/10.1086/162666)

(ref: Lu2017) Lu, N., Zhao, Y., Dı́az-Santos, T., et al. 2017, ApJS, 230, 1, doi: [`10.3847/1538-4365/aa6476`](http://doi.org/10.3847/1538-4365/aa6476)

(ref: Lu2018) Lu, N., Cao, T., Dı́az-Santos, T., et al. 2018, ApJ, 864, 38, doi: [`10.3847/1538-4357/aad3c9`](http://doi.org/10.3847/1538-4357/aad3c9)

(ref: MY2015) Ma, Z., & Yan, H. 2015, ApJ, 811, 58, doi: [`10.1088/0004-637X/811/1/58`](http://doi.org/10.1088/0004-637X/811/1/58)

(ref: Mancini2015) Mancini, M., Schneider, R., Graziani, L., et al. 2015, MNRAS, 451, L70, doi: [`10.1093/mnrasl/slv070`](http://doi.org/10.1093/mnrasl/slv070)

(ref: Michalowski2012) Michałowski, M. J., Dunlop, J. S., Cirasuolo, M., et al. 2012, A&A, 541, A85, doi: [`10.1051/0004-6361/201016308`](http://doi.org/10.1051/0004-6361/201016308)

(ref: Nayyeri2017) Nayyeri, H., Hemmati, S., Mobasher, B., et al. 2017, ApJS, 228, 7, doi: [`10.3847/1538-4365/228/1/7`](http://doi.org/10.3847/1538-4365/228/1/7)

(ref: Nelson2023) Nelson, E. J., Brammer, G., Gimenez-Arteaga, C., et al. 2023, arXiv e-prints, arXiv:2310.06887, doi: [`10.48550/arXiv.2310.06887`](http://doi.org/10.48550/arXiv.2310.06887)

(ref: Noll2009) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793, doi: [`10.1051/0004-6361/200912497`](http://doi.org/10.1051/0004-6361/200912497)

(ref: Oliver2012) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, MNRAS, 424, 1614, doi: [`10.1111/j.1365-2966.2012.20912.x`](http://doi.org/10.1111/j.1365-2966.2012.20912.x)

(ref: Pearson2024) Pearson, J., Serjeant, S., Wang, W.-H., et al. 2024, MNRAS, 527, 12044, doi: [`10.1093/mnras/stad3916`](http://doi.org/10.1093/mnras/stad3916)

(ref: Peng2002) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266, doi: [`10.1086/340952`](http://doi.org/10.1086/340952)

(ref: Peng2010) —. 2010, AJ, 139, 2097, doi: [`10.1088/0004-6256/139/6/2097`](http://doi.org/10.1088/0004-6256/139/6/2097)

(ref: Riechers2013) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329, doi: [`10.1038/nature12050`](http://doi.org/10.1038/nature12050)

(ref: Rujopakarn2023) Rujopakarn, W., Williams, C. C., Daddi, E., et al. 2023, ApJL, 948, L8, doi: [`10.3847/2041-8213/accc82`](http://doi.org/10.3847/2041-8213/accc82)

(ref: Schinnerer2010) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, ApJS, 188, 384, doi: [`10.1088/0067-0049/188/2/384`](http://doi.org/10.1088/0067-0049/188/2/384)

(ref: Sersic1963) Sérsic, J. L. 1963, Boletin de la Asociacion Argentina de Astronomia La Plata Argentina, 6, 41

(ref: Sersic1968) Sersic, J. L. 1968, Atlas de Galaxias Australes (Universidad Nacional de Cordoba)

(ref: Simpson2019) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43, doi: [`10.3847/1538-4357/ab23ff`](http://doi.org/10.3847/1538-4357/ab23ff)

(ref: Simpson2020) Simpson, J. M., Smail, I., Dudzevičiūtė, U., et al. 2020, MNRAS, 495, 3409, doi: [`10.1093/mnras/staa1345`](http://doi.org/10.1093/mnras/staa1345)

(ref: Smail2023) Smail, I., Dudzevičiūtė, U., Gurwell, M., et al. 2023, ApJ, 958, 36, doi: [`10.3847/1538-4357/acf931`](http://doi.org/10.3847/1538-4357/acf931)

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1, doi: [`10.1051/0004-6361/201628704`](http://doi.org/10.1051/0004-6361/201628704)

(ref: Sofier1984) Soifer, B. T., Rowan-Robinson, M., Houck, J. R., et al. 1984, ApJL, 278, L71, doi: [`10.1086/184226`](http://doi.org/10.1086/184226)

(ref: Sommovigo2022) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122, doi: [`10.1093/mnras/stac302`](http://doi.org/10.1093/mnras/stac302)

(ref: Strandet2017) Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJL, 842, L15, doi: [`10.3847/2041-8213/aa74b0`](http://doi.org/10.3847/2041-8213/aa74b0)

(ref: Sun2024) Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69, doi: [`10.3847/1538-4357/ad07e3`](http://doi.org/10.3847/1538-4357/ad07e3)

(ref: Tadaki2023) Tadaki, K.-i., Kodama, T., Koyama, Y., et al. 2023, ApJL, 957, L15, doi: [`10.3847/2041-8213/ad03f2`](http://doi.org/10.3847/2041-8213/ad03f2)

(ref: Venemans2012) Venemans, B. P., McMahon, R. G., Walter, F., et al. 2012, ApJL, 751, L25, doi: [`10.1088/2041-8205/751/2/L25`](http://doi.org/10.1088/2041-8205/751/2/L25)

(ref: scipy2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Watson2015) Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327, doi: [`10.1038/nature14164`](http://doi.org/10.1038/nature14164)

(ref: Yan2016) Yan, H., & Ma, Z. 2016, ApJL, 820, L16, doi: [`10.3847/2041-8205/820/1/L16`](http://doi.org/10.3847/2041-8205/820/1/L16)

(ref: YangCIGALE2022) Yang, G., Boquien, M., Brandt, W. N., et al. 2022, ApJ, 927, 192, doi: [`10.3847/1538-4357/ac4971`](http://doi.org/10.3847/1538-4357/ac4971)

(ref: Yang2023) Yang, G., Papovich, C., Bagley, M. B., et al. 2023, ApJL, 956, L12, doi: [`10.3847/2041-8213/acfaa0`](http://doi.org/10.3847/2041-8213/acfaa0)

(ref: Yoon2023) Yoon, I., Carilli, C. L., Fujimoto, S., et al. 2023, ApJ, 950, 61, doi: [`10.3847/1538-4357/acc94d`](http://doi.org/10.3847/1538-4357/acc94d)

(ref: Zavala2023) Zavala, J. A., Buat, V., Casey, C. M., et al. 2023, ApJL, 943, L9, doi: [`10.3847/2041-8213/acacfe`](http://doi.org/10.3847/2041-8213/acacfe)

# Alternative $z_{\rm ph}$ estimate by limiting $z\leq 6$

As mentioned in Section 4.2, our SED analysis gives $z_{\rm ph}$ solutions that are in favor of $z_{\rm ph}>7$ but cannot rule out the low-$z$ possibilities due to the statistical nature of photometric redshift. To explore such low-$z$ possibilities, we repeated the process described in Section 4.2 but with the difference of setting an upper limit of $z\leq 6$. The results are summarized in Figure [9](#fig:sedjwst_z6).

Regardless of the F090W upper limit choice, LePhare gives solutions close to the upper end of the allowed redshift range, while the other three result in solutions at $z_{\rm ph} \approx 2$–4. However, all these solutions have However, all these solutions have much worsemuch worse $\chi^2$ than those presented in Section 4.2: in case of using the F090 limit of 28.43 mag, the difference of the $\chi^2$ values range from $\Delta\chi^2 \approx 15$–65; in case of using the limit of 26.98 mag, $\Delta\chi^2 \approx 6$–9. Therefore, the high-$z$ solutions in Section 4.2 are indeed preferred.

![](fig_sedjwst_z6.png)

For the sake of completeness, we also performed the MBB fit of the far-IR-to-mm SED as in Section 4.3 but at the fixed redshift of $z=4$. Due to the degeneracy of dust temperature and redshift, the high temperature obtained in Section 4.3 is lowered in this case because of the adopted lower redshift.

![](fig_z4_mbb.png)

![](fig_band3_spec.png)

# ALMA Band 3 Line Detection

COSBO-7 was observed in ALMA Band 3 in January to March 2023 over the range of 84–107 GHz in three separate sectional scans (PID 2022.1.00863.S, PI: J. Hodge), and the data of interest were released while this manuscript was under revision. We reduced these data using the default pipeline ScriptForPi.py to obtain the visibility file and performed tclean using CASA. A line was clearly seen. The continuum was determined from the channels free of line emissions and removed in the *uv* space by uvcontsub. We adopted the natural weighting parameters for the further process. We set the pixel scale to 0.25$''$ and the channel width to 7.812 MHz, which is the same as the original resolution of the observations. The final data cube has the beam of (bmaj, bmin, PA) = (1.60$''$, 1.43$''$, $-$60.35$^{\rm o}$) and an rms of 0.317 mJy beam$^{-1}$.

We extracted the spectrum using the CASA task viewer. The extraction was done at the Band 4 image position (see Table [\[tab:almaherschel\]](#tab:almaherschel)) with a circular aperture of 4$''$ in diameter. The result is shown in Figure [11](#fig:band3line). The line is centered at 95.4 GHz, with a clear double-peak feature. If the line is attributed to the CO (7-6) transition at the rest-frame 806.65 GHz, the corresponding redshift is $z=7.455$, which is consistent with the $z_{\rm ph}$ derivation in Section 4.2. However, such a single line is not sufficient to unambiguously determine the redshift because it could also be due to other lines such as CO (6-5) (corresponding to $z=6.248$), CO (5-4) (corresponding to $z=5.04$), CO (4-3) (corresponding to $z=3.833$), etc. Detecting other lines will be necessary to nail down its redshift.

We also note that the double-peak feature indicates a relative velocity of $\sim$270 km s$^{-1}$ if the line is the CO (7-6) transition. As we argued in Section 4.1, the dusty starburst region is likely confined within a small region, and therefore this velocity should not be interpreted as the rotation velocity of the disk. In other words, it is more likely due to two merging components moving along the sightline.

Lastly, we comment on the non-detection of the \[C I\] line (rest-frame 809.34 GHz), which is often seen accompanying the CO (7-6) line. The ratio of these two lines (\[C I\]/CO(7-6), in logarithmic scale), however, depends on temperature, and the \[C I\] line could vanish at high temperatures. Using the ratio of the flux densities at 60 and 100 $\mu$m (C(60/100)) as the proxy to temperature, it was shown in (cite: Lu2017; Lu2018) that \[C I\]/CO(7-6) decreases with C(60/100). By coincidence, at $z=7.455$ the rest-frame 60 and 100 $\mu$m correspond to approximately Herschel SPIRE 500 $\mu$m and ALMA 870 $\mu$m, respectively. From Table [\[tab:almaherschel\]](#tab:almaherschel), the ratio of the two is $\sim$1.8. Based on the relation given in (cite: Lu2018), the \[C I\] line should be $\sim$11.5$\times$ weaker than the CO (7-6) line, and the sensitivity of the current data is not sufficient for its detection.

# SED fitting of the foreground lens

The catalog of (cite: Laigle2016) includes the stellar mass estimate of the foreground galaxy at $z=0.359$, which is ${\rm log}(M_*/M_{\odot})=10.66^{+0.03}_{-0.04}$. As this quantity provides some constraints on the validity of this galaxy being a viable lens, we have derived it again by fitting its optical-to-near-IR SED after incorporating the NIRCam photometry reported in Table [1](#tab:jwstphot) and fixing its redshift at $z=0.36$. The HST photometry is taken from (cite: Nayyeri2017), and the magnitudes are $21.167\pm 0.008$ and $20.157\pm 0.004$ in the ACS F606W and F814W and $19.407\pm 0.003$ and $19.095\pm 0.002$ mag in the WFC3-IR F125W and F160W, respectively. The results are summarized in Figure [12](#fig:sedlens). These stellar mass estimates are consistent with the result from (cite: Laigle2016). We take the average of our results, which is $3.8\times10^{10}M_\odot$.

![](fig_sedlens.png)

[^1]: <https://github.com/chriswillott/jwst>

[^2]: <https://github.com/arminrest/jhat>

[^3]: Courtesy of M. Mechtley; see <https://github.com/mmechtley/astroRMS>

[^4]: The local 2 $\sigma$ depth within a $r=$ 0.2$''$ aperture at the source location is 28.72 mag, which is deeper because this region is in a overlapped area between two tiles.

[^5]: The peak flux density in the Band 4 image is 0.45 mJy, which is significantly lower than that measured in the polygon. This supports that the Band 4 image is resolved.

[^6]: The SPIRES PSFs of 1$''$ pixel scale were retrieved from <http://archives.esac.esa.int/hsa/legacy/ADP/PSF/SPIRE/SPIRE-P/>. They were then subsampled/rebinned to 5.00$''$, 8.33$''$, and 10.00$''$ to be used by GALFIT, which match the pixel scales of the HerMES 250, 350 and 500 $\mu$m maps, respectively.

[^7]: The systematic difference between the ALMA positions and the CANDELS HST F160W positions in the COSMOS field that our astrometry is tied to is only $\sim$0.06$''$–0.07$''$ (cite: LY2022) and cannot account for the offset seen here. In addition, the offset cannot be due to the random error of the ALMA position, because the high signal-to-noise ratio of the ALMA emission means that the centroid is accurate to $\sim$0.06$''$ (cite: LY2022).

[^8]: <https://scipy.org/>

[^9]: <https://emcee.readthedocs.io/>

</paper>

Write the methods card for this paper.