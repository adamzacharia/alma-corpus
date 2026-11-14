# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...690L..16J\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...690L..16J",
 "title": "A photo-z cautionary tale: Redshift confirmation of COSBO-7 at z = 2.625",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Jin, Shuowen",
 "n_authors": 24,
 "arxiv_id": "2407.07585",
 "doi": "10.1051/0004-6361/202451445",
 "alma_projects_linked_by_archive": [
  "2016.1.00463.S",
  "2021.1.00705.S",
  "2022.1.00863.S",
  "2023.A.00021.S"
 ]
}
```

Paper text:
<paper>
# A photo-$z$ cautionary tale: Redshift confirmation of COSBO-7 at $z=2.625$

Photometric redshifts are widely used in studies of dusty star-forming galaxies (DSFGs), but catastrophic photo-$z$ failure can undermine all redshift-dependent results. Here we report the spectroscopic redshift confirmation of COSBO-7, a strongly lensed DSFG in the COSMOS-PRIMER field. Recently, a photometric redshift solution of $z\gtrsim7.0$ was reported for COSBO-7 based on ten bands of *James Webb* Space Telescope (JWST) NIRCam and MIRI imaging data. This $z$ value was favored by four independent spectral energy distribution (SED) fitting codes, and the result provided an appealing candidate for the most distant massive DSFG known to date. This photo-$z$ solution was also supported by a single line detection in Atacama Large Millimeter Array (ALMA) Band 3 consistent with CO(7-6) at $z=7.46$. However, our new ALMA observations robustly detect two lines in Band 6 identified as CO(7-6) and \[CI\](2-1) at $z_{\rm spec}=2.625$, and thus the Band 3 line as CO(3-2). These three robust line detections decidedly place COSBO-7 at $z=2.625$, refuting the photo-$z$ solution. We derive physical parameters by fitting near-infrared(NIR)-to-millimeter(mm) photometry and lens modeling, revealing that COSBO-7 is a main sequence galaxy. We examine possible reasons for this photo-$z$ failure and attribute it to (1) the likely underestimation of photometric uncertainties at 0.9 $\mu$m and 1.15  $\mu$m; and (2) the lack of photometry at wavelengths beyond 20 $\mu$m. Notably, we recover a bona fide $z_{\rm phot}\sim 2.3$ by including the existing MIPS $24\,\mu$m photometry, demonstrating the critical importance of mid-infrared (MIR) data in bolstering photo-$z$ measurements. This work highlights a common challenge in modeling the SEDs of DSFGs, and provides a cautionary tale regarding the reliability of photometric redshifts as well as pseudo-spectroscopic redshifts based on single line detection.

# Introduction

Redshift is one of the most important parameters of a galaxy, and determining the redshift of a galaxy is the first and most critical step in revealing its nature. To date, the most distant galaxies have been confirmed at $z\sim14$ (cite: Carniani2024z14) by spectroscopy from the *James Webb* Space Telescope (JWST). For dusty star-forming galaxies (DSFGs), given the severe dust attenuation and extreme faintness in optical and near-infrared (NIR) wavelengths (e.g., (cite: Wang2019Natur; Smail2021Kdrop)), detecting molecular and neutral line features in millimeter (mm) and submillimeter(submm) wavelengths is a more efficient way of confirming their redshifts. Thanks to the advanced mm and submm interferometers, such as Atacama Large Millimeter Array (ALMA) and Northern Extended Millimeter Array (NOEMA), distant DSFGs have been spectroscopically confirmed at $z>5$ and out to the epoch of reionization (cite: Walter2012; Vieira2010; Vieira2013; Riechers2013Nature; Riechers2017; Strandet2017; Zavala2017; Marrone2017Nature; Endsley2022z68; Fudamoto2021Nature; Hygate2023z7; Rowland2024z7), proving these facilities to be a powerful “redshift machine” (cite: Vieira2013; Neri2020noema; ChenCC2022alma; Cox2023zGal).

However, performing spectroscopy on DSFGs remains observationally expensive, which limits the size and completeness of current spec-$z$ samples. Alternatively, photometric redshifts, which are estimated by modeling spectral energy distributions (SEDs) with optical and NIR photometry (e.g., (cite: Arnouts1999LePhare; Ilbert2006LePhare; da_Cunha2008magphys; Brammer2008EAZY; Kriek2009FAST; Carnall2018Bagpipes; Boquien2019CIGALE)), are widely used and dominate in literature studies of DSFGs (e.g., (cite: Boone2011; Wardlow2011; Simpson2014; Miettinen2015; Wang2019Natur; Gomez-Guijarro2019; Dudzeviciute2020SMG; Smail2021Kdrop)). In comparison to dust-free galaxies, constraining the redshifts of DSFGs is particularly challenging because of severe dust attenuation. Nowadays, the situation has been dramatically improved with the data from JWST. With its unprecedented sensitivity and long-wavelength coverage, photometric redshifts have been estimated out to $z>10-16$ for dust-free galaxies (e.g., (cite: Naidu2022photoz; Finkelstein2022z12; Harikane2023z10; Atek2023z16; Casey2024z10; Chakraborty2024z11)) and $z\sim8$ for DSFGs (e.g., (cite: Barrufet2023dark; Akins2023z8candi)). Nevertheless, photometric redshifts can still fail catastrophically —that is, they can be catastrophically erroneous— for dust-free galaxies, even with multiband JWST photometry. For example, the galaxy CEERS-93316 was reported with a photometric redshift of $z\sim16.4$ based on a SED fitting with seven bands of JWST NIRCam photometry (cite: Donnan2023z16), but was eventually confirmed to be a $z=4.9$ dusty galaxy based on JWST NIRSpec spectroscopy (cite: Arrabal_Haro2023Natur), demonstrating that dusty starbursts can masquerade as ultrahigh-redshift galaxies (cite: Zavala2023photoz; Naidu2022photoz). As the misidentification of photo-$z$ can undermine all results that are dependent on redshift, it is vital to examine whether such photo-$z$ failure can also happen for DSFGs preselected from mm and submm surveys.

![](fig1.pdf)

Recently, a $z>7$ DSFG candidate, COSBO-7, was reported by (cite: Ling2024cosbo7) based on exquisite imaging data from JWST. (cite: Ling2024cosbo7) performed extensive imaging fitting and SED analysis using the JWST NIRCam and MIRI data, and found that COSBO-7 is not detected in NIRCam/F090W but is well detected in nine bands from NIRCam/F115W to MIRI/F1800W. Using the photometry measured on the lens-subtracted images, these authors calculated photometric redshifts of $z_{\rm phot}=6.9-7.7$, finding that four SED algorithms, namely `LePhare` (cite: Ilbert2006LePhare), `EAZY` (cite: Brammer2008EAZY), `Bagpipes` (cite: Carnall2018Bagpipes), and `CIGALE` (cite: Boquien2019CIGALE) agree on a best-fit solution of $z\sim7.0$. This makes COSBO-7 an appealing candidate for the most distant DSFG to date. Furthermore, (cite: Ling2024cosbo7) reported a line detection at 95.4 GHz in ALMA archival data that would be consistent with CO(7-6) emission at $z=7.46$, that is, at a redshift very close to the $z_{\rm phot}$ solution. Nevertheless, robust spectroscopic confirmation with multiple lines was still missing.

In this Letter, we report unambiguous spectroscopic redshift confirmation of COSBO-7 and discuss the implications of erroneous photometric redshift estimates and the lessons learned from this cautionary tale. We adopt a flat $\Lambda$CDM cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$ and $\Omega_M=0.27$, and a Chabrier initial mass function (cite: Chabrier2003).

# Selection and data

## Selection

COSBO-7 (Right Ascension (RA)=10:00:23.97, Declination (Dec.)=+02:17:50.0) was originally discovered in a flux-limited IRAM/MAMBO-2 1.2mm imaging survey by (cite: Bertoldi2007). It is one of the brightest submm sources in the COSMOS field, and is also detected in the AzTEC and SCUBA-2 surveys ($S_{\rm 1mm}\sim2$ mJy, $S_{\rm 850\mu m}\sim10$ mJy; (cite: Aretxaga2011; Geach2017scuba2; Simpson2019SCUBA2)). COSBO-7 is not detected in deep HST images of the COSMOS-CANDELS field, indicating an extremely dust-obscured nature. A secure counterpart of COSBO-7 was first identified in radio wavelengths at VLA 1.4 GHz and 3 GHz (cite: Schinnerer2010; Smolcic2017). COSBO-7 was identified as a lensing system by (cite: Jin2018cosmos), wherein a high-z submillimeter galaxy is lensed by a foreground elliptical galaxy at $z_{\rm spec}=0.36$. COSBO-7 was observed with ALMA Band 7 in the project 2016.1.00463.S (PI: Y. Matsuda) and was cataloged by (cite: Simpson2020alma). Recently, COSBO-7 was observed with JWST/NIRCam and MIRI as part of the PRIMER survey (cite: Dunlop2021PRIMER). The MIRI image clearly reveals a lensing arc in the MIRI 7.7$\mu$m band while a counter-image is found on the ALMA 870$\,\mu$m map (cite: Pearson2024cosbo7), confirming the strong lensing nature of the system. (cite: Ling2024cosbo7) performed an extensive photometric analysis of COSBO-7 by exploiting the JWST imaging data from NIRCam F090W to MIRI F1800W band after subtracting the foreground lens. These authors found that COSBO-7 remains undetected in F090W, but is well detected in nine bands from F115W to F1800W. With the JWST photometry, (cite: Ling2024cosbo7) performed SED fitting using four SED codes that all converged to a photo-$z$ solution of $z\gtrsim7.0$.

## ALMA

The first spectroscopic follow-up of COSBO-7 was carried out with ALMA Band 3 line scans in Cycle 9 (ID:2022.1.00863.S; PI: J. Hodge) as part of a redshift scan program investigating ten radio-selected, optically dark DSFGs. A strong line was detected at 95.4 GHz (Fig. [1](#fig-spec), bottom-left); however the single line detection was insufficient to confirm the redshift of the source. Driven by the photometric redshift $z\gtrsim7.0$ by (cite: Ling2024cosbo7), it was reasonable to postulate that the 95.4 GHz line originates from CO(7-6) emission at $z=7.458$. Further, the $z=7.458$ solution was also supported by a multitude of indirect evidence: (1) a tentative line at 95.7 GHz, consistent with \[CI\](2-1) emission at $z=7.458$ ; (2) F410M excess, indicative of \[OIII\]+H$\beta$ emission at $z\sim7.4$; (3) MIPS 24$\mu m$ excess that is consistent with a 3.3$\mu$m polycyclic aromatic hydrocarbon (PAH) feature at $z=7.458$; and (4) a well-fitted panchromatic SED from NIR to radio wavelengths. However, without a robust detection of a second line, the redshift of the source remained ambiguous. Consequently, we proposed 0.5 hr of ALMA Band 6 observations through DDT time, aiming to detect \[CII\]158$\mu$m and decidedly determine the redshift of COSBO-7.

The DDT program (ID: 2023.A.00021.S; PI: S. Jin) was approved and the observation was executed on March 21 2024 in C-1 configuration. The frequency tuning covers 222.18–225.94 GHz for lines and 235.60–239.48 GHz for continuum. The on-source integration is 15 mins, and self-calibration was performed. This gives a rms sensitivity of 0.107 mJy/beam per 500 km s$^{-1}$, and a beam size of $1.43''\times1.14''$ with natural weighting.

The raw data of the ALMA programs mentioned above were reduced and calibrated using the standard ALMA CASA pipeline (cite: McMullin2007CASA). Following our established pipeline from (cite: Jin2019alma; Jin2022), we converted the calibrated measurement sets to `uvfits` format for further analysis in $uv$ space with the GILDAS software. The 1D spectrum was extracted using the GILDAS `uvfit` routine on the $uv$ tables at all frequencies, where we adopted a point-source model on the fixed position of the ALMA continuum peak. The continuum and line maps are cleaned using the GILDAS HOGBOM clean routine. Given that COSBO-7 is resolved in the ALMA data, we measured the continuum and integrated line fluxes on the clean images using an aperture of $r\sim2.5''$, which maximizes the integrated S/Ns.

We also measured the photometry in ALMA Band 4 (ID: 2021.1.00705.S; PI: O. Cooper), and adopted 870$\mu$m photometry in the A3COSMOS catalog (cite: Liu2019A3COSMOS) measured from Band7 data (ID: 2016.1.00463.S, PI: Y. Matsuda). We list the line fluxes in Table [1](#tab:physpars) and continuum fluxes in Table [2](#tab:photo).

## JWST

COSBO-7 was observed with JWST NIRCam and MIRI in ten bands: F090W, F115W, F150W, F200W, F277W, F356W, F410M, and F444W in NIR, and F770W and F1800W in mid-infrared (MIR). (cite: Ling2024cosbo7) modeled the foreground lens using `Galfit` and measured the photometry on the lens-subtracted residual images. The lens is well modeled, and so the counter image of the arc is recovered in the residual map. The photometry was carefully measured on the PSF-matched and aperture-matched residual images, and therefore we directly adopt the photometry from (cite: Ling2024cosbo7). As (cite: Ling2024cosbo7) measured $2\sigma$ upper limits of F090W using two different apertures, we adopted the flux limit measured within the larger aperture, but use the $3\sigma$ limit in this work for reasons discussed in Sect. [4.1](#discuss1). For visualization and lensing modeling, we used the PRIMER mosaics produced by M. Franco and S. Harish from the COSMOS-Web team (cite: Casey2023cosmosweb).

## Ancillary data

The FIR and radio photometry of COSBO-7 were already measured in the COSMOS Super-deblended catalog (cite: Jin2018cosmos). However, the Herschel photometry is noisy because too many priors were fitted within the Herschel beams; that is, it exhibits a high level of crowding. The ALMA data show that COSBO-7 is the only submm-emitting source within the ALMA Band 7 ($r<8''$) and Band 3 primary beam ($r<30''$), indicating negligible blending and no contributions from neighboring sources. Hence, we reran our “super-deblending” pipeline with improved priors on Herschel maps as done by (cite: Sillassen2024NICE), assuming that COSBO-7 is the only source contributing to the Herschel fluxes. As listed in Table [2](#tab:photo), the newly measured Herschel photometry shows solid detection in the PACS 160$\mu$m and the SPIRE bands (Fig. [2](#fig:sed)).

# Results

## Redshift confirmation

As shown in the bottom-middle panel of Fig. [1](#fig-spec), the DDT program did not detect any line at the expected frequency of 224.7 GHz of \[CII\] at $z=7.458$. Instead, and quite surprisingly, two lines are solidly detected at 222.52 GHz and 223.27 GHz with S/N$=11$ and 23, respectively (Fig. [1](#fig-spec)). The two lines perfectly match the CO(7-6) and \[CI\](2-1) transitions at $z=2.625$. Moreover, the 95.4 GHz line is also fitted at the exact frequency of $z=2.625$ CO(3-2). Further, the line widths of the \[CI\] and CO lines are also consistent with a full width at zero intensity FWZI$=$850 km s$^{-1}$ (Fig. [1](#fig-spec), bottom-right). Therefore, the three solid line detections unambiguously confirm the redshift of COSBO-7 to $z_{\rm spec}=2.625$ instead of $z_{\rm phot}\gtrsim7.0$.

![](COSBO7_FIR_SED.pdf)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | COSBO-7 |  |  |  |  |  |  |
| RA | 10:00:23.97 |  |  |  |  |  |  |
| Dec | +02:17:50.0 |  |  |  |  |  |  |
| $z$ | $2.6250\pm0.0007$ |  |  |  |  |  |  |
| $\mu$ | $3.6^{+2.0}_{-0.9}$ |  |  |  |  |  |  |
| $I_{\rm CO(3-2)}$ \[Jy km s$^{-1}$\] | $1.93\pm0.11$ |  |  |  |  |  |  |
| $I_{\rm CO(7-6)}$ \[Jy km s$^{-1}$\] | $0.88\pm0.08$ |  |  |  |  |  |  |
| $I_{\rm [CI](2-1)}$ \[Jy km s$^{-1}$\] | $1.80\pm0.08$ |  |  |  |  |  |  |
| $A_V$ \[mag\] | $1.95\pm0.01$ |  |  |  |  |  |  |
| $M_\ast$ \[$10^{11}{\rm M_\odot}$\] | $2.50\pm0.23$ |  |  |  |  |  |  |
| ${\rm SFR}_{\rm IR}$ \[${\rm M_\odot\,yr^{-1}}$\] | $521_{-45}^{+122}$ |  |  |  |  |  |  |
| $M_{\rm gas,[CI]}$ \[${\rm 10^{11} M_\odot}$\] | $5.04\pm1.70$ |  |  |  |  |  |  |
| ${\rm SFE}$ \[${\rm Gyr^{-1}}$\] | $1.03\pm0.35$ |  |  |  |  |  |  |
| $T_{\rm dust,thick}$ \[K\] | $36.5^{+0.6}_{-0.6}$ |  |  |  |  |  |  |
| $M_{\rm dust,thick}$ \[$10^{9}{\rm M_\odot}$\] | $2.9^{+0.3}_{-0.3}$ |  |  |  |  |  |  |
| $T_{\rm dust,thin}$ \[K\] | $25.9^{+1.0}_{-0.9}$ |  |  |  |  |  |  |
| $M_{\rm dust,thin}$ \[$10^{9}{\rm M_\odot}$\] | $5.3^{+0.9}_{-0.7}$ |  |  |  |  |  |  |

: Physical properties of COSBO-7

\
Notes: These parameters are not corrected for magnification $\mu$.

## Physical properties and lensing model

With the confirmed $z_{\rm spec}=2.625$, we derive some physical parameters of COSBO-7 by SED fitting with multiwavelength photometry. As shown in Fig. [2](#fig:sed), the SED is well fitted from NIR to radio wavelengths using `Stardust` (cite: Kokorev2021stardust). Specifically, the MIPS 24$\mu$m excess is well fitted by strong PAH features at a rest-frame of $6-8\mu$m, while the MIR AGN contribution to the total IR luminosity is negligible ($<2\%$). We report the best-fit parameters in Fig. [2](#fig:sed) and Table [1](#tab:physpars). We note that the 3mm continuum is not fitted well by `Stardust`, which suggests a steep $\beta$ slope or optically thick dust in FIR (cite: Jin2022). We thus performed FIR SED fitting with modified blackbody models using the `Mercurius` code (cite: Witstok2022-mercurius), accounting for both cases of optically thin and thick dust in FIR (cite: Jin2022). As shown in Fig. [4](#fig-thick), the optically thick model performs slightly better than the thin ones, yielding a dust temperature of $T_{\rm dust}=36.5\pm0.6$ K and a dust mass of $M_{\rm dust}=(2.9\pm0.3)\times10^{9}~M_\odot$. The dust temperature is consistent with the $T_{\rm dust}-z$ relation of main sequence galaxies by (cite: Schreiber2018Tdust).

To constrain the magnification $\mu$, we performed lens modeling of the F777W image by adopting the methodology from (cite: Vegetti2009lensing) and (cite: Rizzo2018lensing). As shown in Fig. [5](#fig-lens), the lensing arc is well modeled with a magnification factor of $\mu=3.6^{+2.0}_{-0.9}$. This magnification is consistent with the findings of (cite: Pearson2024cosbo7), which are based on F777W data, but is slightly higher than the value estimated by (cite: Ling2024cosbo7) from the F444W image.

We derive the molecular gas mass using \[CI\](2-1) and CO(3-2) as gas tracers: (1) Adopting a $R_{\rm [CI]}=L'_{\rm [CI](2-1)}/L'_{\rm [CI](1-0)}=0.3\pm0.1$ (cite: Jiao2019CI) and assuming the excitation $T_{\rm exc}=T_{\rm dust, thick}$, we obtain a gas mass of $M_{\rm gas,CI}=(5.04\pm1.70)\times10^{11}~M_\odot$ using the scaling relation from (cite: Valentino2018CI). (2) Assuming a CO line ratio of $r_{\rm 31}=0.84\pm0.26$ from (cite: Riechers2020COLF), we obtain a CO(1-0) luminosity of $L'_{\rm CO(1-0)}=(7.7\pm2.4)\times10^{11}$ K km s$^{-1}$ pc$^2$, which gives a gas mass of $M_{\rm gas,\alpha_{CO}=3.6}=(2.8\pm0.9)\times10^{12}~M_\odot$, or ${ M_{\rm gas,\alpha_{CO}=0.4}=(3.1\pm1.0)\times10^{11}~M_\odot}$. The CO-derived gas masses agree with $M_{\rm gas,CI}$ within the uncertainty of $\alpha_{\rm CO}$. We adopted a conservative ${\rm SFR= 521_{-42}^{+122}~M_\odot~yr^{-1}}$ comprising the outputs and uncertainties from both `Stardust` and `Mercurius`. As both $r_{31}$ and $\alpha_{\rm CO}$ are uncertain, we simply adopted $M_{\rm gas,CI}$ and derived a median gas depletion time of $\tau\sim1$ Gyr with a lower limit of ${\tau>326}$ Myr. This indicates that COSBO-7 is a gas-rich galaxy with a star formation efficiency (SFE) typical of main sequence galaxies (cite: Sargent2014; Magdis2012SED; Magdis2017). Accounting for the lensing magnification, the stellar mass and SFR of COSBO-7 are consistent with the main sequence at $z\sim2.6$ (cite: Schreiber2017z4MS). This again suggests that COSBO-7 is a typical dusty star-forming galaxy at $z\sim2.6$ (e.g., (cite: daCunha2015)).

![](fig3.png)

# Discussion

## Possible causes of the catastrophic photo-$z$ failure

The robust $z_{\rm spec}=2.625$ for COSBO-7 derived in this study indicates that the photo-$z\gtrsim7.0$ is a catastrophic failure and highlights that caution should be exercised in studies of DSFGs that rely on photometric redshifts. Here we attempt to uncover the reasons behind the photo-$z$ failure and provide suggestions as to how to see through similar “cosmic conspiracies”.

Interestingly, we find that the redshift probability distribution function PDF($z$) by (cite: Ling2024cosbo7) indeed shows an insignificant peak at $z\sim2.6$ from `EAZY` and `CIGALE` results. As already tested by (cite: Ling2024cosbo7), the PDF($z$) at $z\sim2.6$ became dominant if adopting the limit of $z<6$ with `EAZY`, `CIGALE,` and `Bagpipes`. On the other hand, (cite: Ling2024cosbo7) performed SED fitting with two different F090W upper limits, one of which is the average $2\sigma$ depth of the image measured in a $r=0.2''$ aperture, while the other is a $2\sigma$ limit measured within the aperture used for the arc. These authors found that, in either case, the best PDF($z$) solution remains peaked at $z\sim7.0$, and that adjusting the F090W upper limit with a large aperture does not appear to improve the photo-$z$ outputs. We also tested with `EAZY` by adopting the F090W $3\sigma$ upper limit, and found the best-fit output remains $z\sim7-8$, consistent with (cite: Ling2024cosbo7). As shown in the left panel of Fig. [3](#fig:NIR-sed), we tested fitting NIR-to-MIR SEDs at both $z=2.625$ and $z=7.458$, finding that the SED can be fitted at both redshifts, with a subtle difference in the $\chi^2$ values between the two solutions. This indicates that the NIR-to-MIR photometry is fully degenerated between $z\sim2.6$ and $z\sim7.5$.

Further, we test `Bagpipes` fitting without the F090W upper limit. Interestingly, we find that the PDF($z$) peaks at $z\sim2.3$ without a secondary solution at $z>7$, as in the left panel of Fig. [3](#fig:NIR-sed). This photo-$z$ is close to the $z_{\rm spec}=2.625$, and consistent within a typical uncertainty of $\Delta z/(1+z)<10\%$. This well-recovered photo-$z$ suggests that the F090W flux limit by (cite: Ling2024cosbo7) might be underestimated. We note that the F090W limit in Fig. [3](#fig:NIR-sed) is a $3\sigma$ upper limit, which is well above the best-fit models of either $z=2.625$ or $z=7.458$, while (cite: Ling2024cosbo7) adopted a stricter $2\sigma$ upper limit. This stringent upper limit likely forced the templates to interpret the data at $\lambda <1\,\mu$m as a Lyman break at $z\sim7$, while excluding solutions at lower redshifts.

Given that the 24$\mu$m flux density is about ten times higher than the F1800W one, we suspect that such an excess, boosted by PAH emission, might be useful to improve the photo-$z$ quality. Therefore, we tested fitting the SED by including the MIPS 24$\mu$m photometry $S_{\rm 24\mu m}=188.4\pm45.9~\mu$Jy measured by (cite: Jin2018cosmos), which was not used by (cite: Ling2024cosbo7). Strikingly, this again yields a $z_{\rm phot}=2.3$ (Fig. [3](#fig:NIR-sed), right), and the $\chi^2$ is two times smaller than that of the fitting at fixed $z=2.625$ without 24$\mu$m. This is evident in the left panel of Fig. [3](#fig:NIR-sed): it is difficult to fit the 24$\mu$m data point with the narrow rest-frame 3.3$\mu$m PAH at $z>7$, while a better fit is achieved with the broad PAH features at rest-frame 6–8$\mu$m. Therefore, the inclusion of $24\mu$m photometry can directly exclude the deceiving $z>7$ solution without fine-tuning the fluxes and flux uncertainties from (cite: Ling2024cosbo7), and is a straightforward remedy for avoiding the erroneous photo-$z$ of COSBO-7 and could prevent similar situations other objects. This demonstrates that long-wavelength MIR photometry can significantly improve the photo-$z$ of DSFGs.

It remains puzzling that the best-fit photo-$z\sim2.3$ does not agree well with $z_{\rm spec}=2.625$. In the right panel of Fig. [3](#fig:NIR-sed), we show the SED fitting at both redshifts. Interestingly, a significant discrepancy is found for F115W, where the F115W measurement from (cite: Ling2024cosbo7) is clearly above the SED of $z_{\rm spec}=2.625$. As no strong line is expected in the F115W filter, this discrepancy suggests that the F115W flux is overestimated or that the flux uncertainty is underestimated. Given that this F115W photometry was better fitted by $z>7$ models (cite: Ling2024cosbo7), the F115W measurement is likely problematic, and could also be a reason for the photo-$z$ failure.

## Caution on photo-$z$

As COSBO-7 is a strongly lensed galaxy with multiwavelength JWST photometry spanning NIR to MIR, it is alarming that the photo-$z$ failed dramatically, undermining the physical parameters relying on it. Given that COSBO-7 is a typical DSFG at $z\sim2.6$, such photo-$z$ failure could occur in other galaxies. As depicted by the PDF($z$) of COSBO-7 from (cite: Ling2024cosbo7), there are no visible peaks at $z<5$ from `LePhare` and $z<4$ from `Bagpipes`; however, the statistically disfavored peak around $z\sim2.6$ from `EAZY` and `CIGALE` is now proven to be closer to the real solution. This highlights that caution should be exercised when interpreting the output of photo-$z$ codes, and low-$z$ solutions that appear statistically insignificant in the PDF($z$) cannot be ruled out.

As demonstrated in Sect. [4.1](#discuss1), it is also remarkable that a subtle adjustment of the F090W upper limit can tremendously impact the robustness of the photo-$z$. Finally, it is also clear that a combination of photo-$z$ with a single line detection in the mm might not be sufficient for a robust determination of the redshift of DSFGs, especially if the emission line is consistent with multiple solutions. Indeed, this combination entails the danger of providing a deceiving preference for the most exotic but wrong solution. We note that (cite: Ling2024cosbo7) did highlight uncertainties regarding the $z>7$ solution and pointed out that low-z solutions cannot be totally ruled out, although their work only shows that high-z solutions are favored.

It is unclear as to whether COSBO-7 is a rare case or similar catastrophic photo-$z$ failures are common among DSFGs. A large sample is required to determine whether these failures are prevalent or even systematic. If such failures were found to be systematic, literature studies relying purely on photo-$z$ and pseudo-spectroscopic redshifts from single line detection would need to be revised.

# Conclusions

Using ALMA observations, we confirmed that the $z>7$ DSFG candidate COSBO-7 is, in reality, at $z=2.625$. Our conclusions are as follows:

1\. We detect three lines with a high level of certainty and identify them as CO(3-2), CO(7-6), and \[CI\](2-1) at $z=2.625$, thereby robustly confirming the redshift of COSBO-7. This is in tension with the photometric redshift of $z\gtrsim7.0$ reported by (cite: Ling2024cosbo7).

2\. With the confirmed redshift, we derive physical parameters for COSBO-7 and find it to be a main sequence galaxy with possible optically thick dust.

3\. We examined possible explanations for the catastrophic photo-$z$ failure, and attribute it to (1) the likely underestimation of the F090W upper limit and the F115W flux uncertainty; and (2) the lack of photometry at wavelengths beyond 20$\mu$m sampling the PAH features at $z\sim2.6$.

4\. Notably, we recover an almost accurate $z_{\rm phot}\sim2.3$ by including the MIPS 24$\mu$m photometry without applying further changes with respect to the literature photometry. This provides a straightforward remedy for the erroneous photo-$z$, and demonstrates the importance of long-wavelength MIR data in supporting photo-$z$ measurements.

This work highlights a common challenge in modeling the SEDs of DSFGs, and provides a cautionary tale regarding the reliability of photometric redshifts and redshifts that rely on single line detections. Long-wavelength MIR photometry can significantly improve the photo-$z$ quality, and so we encourage the use of MIPS or MIRI 24$\mu$m in SED fitting. However, even with this additional sampling, the photo-$z$ accuracy is still dependent on the sufficient dominance of certain spectral features. As such, detecting multiple lines remains the only way to unambiguously identify the redshifts of DSFGs, and the future Wideband Sensitivity Upgrade of ALMA will turn it into an even more powerful "redshift machine".

# Acknowledgements

We thank Haojing Yan, Emanuele Daddi, Jorge Zavala and Ian Smail for helpful discussions in the preparation of this manuscript. We thank Frank Bertoldi for constructive and insightful review of this manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2023.A.00021, 2022.1.00863, 2021.1.00705.S, and 2016.1.00463.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. SJ acknowledges financial support from the European Union’s Horizon Europe research and innovation program under the Marie Skłodowska-Curie grant No. 101060888. JH acknowledges support from the ERC Consolidator Grant 101088676 (VOYAJ). GEM and SJ acknowledge the Villum Fonden research grants 37440 and 13160. The Cosmic Dawn Center (DAWN) is funded by the Danish National Research Foundation under grant DNRF140. APV acknowledges support from the Carlsberg Foundation (grant no CF20-0534).

74 natexlab

(ref: Akins2023z8candi) Akins, H. B., Casey, C. M., Allen, N., et al. 2023, ApJ, 956, 61

(ref: Aretxaga2011) Aretxaga, I., Wilson, G. W., Aguilar, E., et al. 2011, MNRAS, 415, 3831

(ref: Arnouts1999LePhare) Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999, MNRAS, 310, 540

(ref: Arrabal_Haro2023Natur) Arrabal Haro, P., Dickinson, M., Finkelstein, S. L., et al. 2023, Nature, 622, 707

(ref: Atek2023z16) Atek, H., Shuntov, M., Furtak, L. J., et al. 2023, MNRAS, 519, 1201

(ref: Barrufet2023dark) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, MNRAS, 522, 449

(ref: Bertoldi2007) Bertoldi, F., Carilli, C., Aravena, M., et al. 2007, ApJS, 172, 132

(ref: Boone2011) Boone, F., Schaerer, D., Pelló, R., et al. 2011, A&A, 534, A124

(ref: Boquien2019CIGALE) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: Brammer2008EAZY) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, ApJ, 686, 1503

(ref: Carnall2018Bagpipes) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, MNRAS, 480, 4379

(ref: Carniani2024z14) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024, Nature, 633, 318

(ref: Casey2024z10) Casey, C. M., Akins, H. B., Shuntov, M., et al. 2024, ApJ, 965, 98

(ref: Casey2023cosmosweb) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, ApJ, 954, 31

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chakraborty2024z11) Chakraborty, P., Sarkar, A., Wolk, S., et al. 2024, arXiv e-prints, arXiv:2406.05306

(ref: ChenCC2022alma) Chen, C.-C., Liao, C.-L., Smail, I., et al. 2022, ApJ, 929, 159

(ref: Cox2023zGal) Cox, P., Neri, R., Berta, S., et al. 2023, A&A, 678, A26

(ref: da_Cunha2008magphys) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595

(ref: daCunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110

(ref: Delvecchio2021) Delvecchio, I., Daddi, E., Sargent, M. T., et al. 2021, A&A, 647, A123

(ref: Donnan2023z16) Donnan, C. T., McLeod, D. J., Dunlop, J. S., et al. 2023, MNRAS, 518, 6011

(ref: Dudzeviciute2020SMG) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828

(ref: Dunlop2021PRIMER) Dunlop, J. S., Abraham, R. G., Ashby, M. L. N., et al. 2021, PRIMER: Public Release IMaging for Extragalactic Research, JWST Proposal. Cycle 1, ID. #1837

(ref: Endsley2022z68) Endsley, R., Stark, D. P., Fan, X., et al. 2022, MNRAS, 512, 4248

(ref: Finkelstein2022z12) Finkelstein, S. L., Bagley, M. B., Arrabal Haro, P., et al. 2022, ApJL, 940, L55

(ref: Fudamoto2021Nature) Fudamoto, Y., Oesch, P. A., Schouws, S., et al. 2021, Nature, 597, 489

(ref: Geach2017scuba2) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789

(ref: Gomez-Guijarro2019) Gómez-Guijarro, C., Riechers, D. A., Pavesi, R., et al. 2019, ApJ, 872, 117

(ref: Harikane2023z10) Harikane, Y., Ouchi, M., Oguri, M., et al. 2023, ApJS, 265, 5

(ref: Hygate2023z7) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775

(ref: Ilbert2006LePhare) Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841

(ref: Jiao2019CI) Jiao, Q., Zhao, Y., Lu, N., et al. 2019, ApJ, 880, 133

(ref: Jin2018cosmos) Jin, S., Daddi, E., Liu, D., et al. 2018, ApJ, 864, 56

(ref: Jin2019alma) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144

(ref: Jin2022) Jin, S., Daddi, E., Magdis, G. E., et al. 2022, A&A, 665, A3

(ref: Kokorev2021stardust) Kokorev, V. I., Magdis, G. E., Davidzon, I., et al. 2021, ApJ, 921, 40

(ref: Kriek2009FAST) Kriek, M., van Dokkum, P. G., Labbé, I., et al. 2009, ApJ, 700, 221

(ref: Ling2024cosbo7) Ling, C., Sun, B., Cheng, C., et al. 2024, ApJL, 969, L28

(ref: Liu2019A3COSMOS) Liu, D., Lang, P., Magnelli, B., et al. 2019, ApJS, 244, 40

(ref: Magdis2012SED) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Magdis2017) Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, A&A, 603, A93

(ref: Marrone2017Nature) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51

(ref: McMullin2007CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Miettinen2015) Miettinen, O., Smolčić, V., Novak, M., et al. 2015, A&A, 577, A29

(ref: Naidu2022photoz) Naidu, R. P., Oesch, P. A., Setton, D. J., et al. 2022, arXiv e-prints, arXiv:2208.02794

(ref: Neri2020noema) Neri, R., Cox, P., Omont, A., et al. 2020, A&A, 635, A7

(ref: Pearson2024cosbo7) Pearson, J., Serjeant, S., Wang, W.-H., et al. 2024, MNRAS, 527, 12044

(ref: Riechers2020COLF) Riechers, D. A., Boogaard, L. A., Decarli, R., et al. 2020, ApJL, 896, L21

(ref: Riechers2013Nature) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: Riechers2017) Riechers, D. A., Leung, T. K. D., Ivison, R. J., et al. 2017, ApJ, 850, 1

(ref: Rizzo2018lensing) Rizzo, F., Vegetti, S., Fraternali, F., & Di Teodoro, E. 2018, MNRAS, 481, 5606

(ref: Rowland2024z7) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, arXiv e-prints, arXiv:2405.06025

(ref: Sargent2014) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19

(ref: Schinnerer2010) Schinnerer, E., Sargent, M. T., Bondi, M., et al. 2010, ApJS, 188, 384

(ref: Schreiber2018Tdust) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: Schreiber2017z4MS) Schreiber, C., Pannella, M., Leiton, R., et al. 2017, A&A, 599, A134

(ref: Sillassen2024NICE) Sillassen, N. B., Jin, S., Magdis, G. E., et al. 2024, A&A, 690, A55

(ref: Simpson2020alma) Simpson, J. M., Smail, I., Dudzevičiūtė, U., et al. 2020, MNRAS, 495, 3409

(ref: Simpson2019SCUBA2) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43

(ref: Simpson2014) Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, ApJ, 788, 125

(ref: Smail2021Kdrop) Smail, I., Dudzevičiūtė, U., Stach, S. M., et al. 2021, MNRAS, 502, 3426

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, A&A, 602, A1

(ref: Strandet2017) Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJL, 842, L15

(ref: Valentino2018CI) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: Vegetti2009lensing) Vegetti, S. & Koopmans, L. V. E. 2009, MNRAS, 392, 945

(ref: Vieira2010) Vieira, J. D., Crawford, T. M., Switzer, E. R., et al. 2010, ApJ, 719, 763

(ref: Vieira2013) Vieira, J. D., Marrone, D. P., Chapman, S. C., et al. 2013, Nature, 495, 344

(ref: Walter2012) Walter, F., Decarli, R., Carilli, C., et al. 2012, Nature, 486, 233

(ref: Wang2019Natur) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, Nature, 572, 211

(ref: Wardlow2011) Wardlow, J. L., Smail, I., Coppin, K. E. K., et al. 2011, MNRAS, 415, 1479

(ref: Witstok2022-mercurius) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: Zavala2023photoz) Zavala, J. A., Buat, V., Casey, C. M., et al. 2023, ApJL, 943, L9

(ref: Zavala2017) Zavala, J. A., Montaña, A., Hughes, D. H., et al. 2018, Nature Astronomy, 2, 56

# Supporting material

|    Facility    |    Band    |           Flux/mJy           |
|:--------------:|:----------:|:----------------------------:|
|  Spitzer/MIPS  | 24 $\mu$m  |       $0.188\pm0.046$        |
| Herschel/PACS  | 100 $\mu$m |        $0.01\pm1.57$         |
| Herschel/PACS  | 160 $\mu$m |        $9.72\pm2.52$         |
| Herschel/SPIRE | 250 $\mu$m |        $18.81\pm1.79$        |
| Herschel/SPIRE | 350 $\mu$m |        $28.60\pm2.89$        |
| Herschel/SPIRE | 500 $\mu$m |        $24.66\pm2.06$        |
|    SCUBA-2     | 850 $\mu$m |        $9.71\pm0.67$         |
|    ALMA$^*$    | 870 $\mu$m |        $10.45\pm0.60$        |
|     AzTEC      |   1.1 mm   |        $5.55\pm1.29$         |
|     MAMBO      |   1.2 mm   |        $4.84\pm0.69$         |
|      ALMA      | 237.5 GHz  |        $3.65\pm0.47$         |
|      ALMA      | 224.8 GHz  |        $3.41\pm0.41$         |
|      ALMA      |  145 GHz   |        $0.62\pm0.07$         |
|      ALMA      |  100 GHz   |       $0.071\pm0.016$        |
|      VLA       |   3 GHz    | $(28.6\pm2.8)\times10^{-3}$  |
|      VLA       |  1.4 GHz   | $(91.4\pm10.2)\times10^{-3}$ |

: MIR to radio photometry

\
Notes: $^*$ From A3COSMOS catalog (cite: Liu2019A3COSMOS).

![image](Thick_reduced_res_v2.pdf) ![image](Thin_reduced_res_v2.pdf)

![](fig-lensing.pdf)

</paper>

Write the methods card for this paper.