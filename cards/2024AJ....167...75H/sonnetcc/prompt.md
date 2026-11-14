# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024AJ....167...75H\sonnetcc\reply.txt

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
 "bibcode": "2024AJ....167...75H",
 "title": "Shadowing in the Protoplanetary Disk of ZZ Tau IRS with HST",
 "year": 2024,
 "journal": "The Astronomical Journal",
 "first_author": "Hashimoto, Jun",
 "n_authors": 5,
 "arxiv_id": "2401.02004",
 "doi": "10.3847/1538-3881/ad1b5e",
 "alma_projects_linked_by_archive": [
  "2016.1.01511.S"
 ]
}
```

Paper text:
<paper>
# Shadowing in the protoplanetary disk of ZZ Tau IRS with HST

## Abstract

An inner component misaligned from an outer component in a protoplanetary disk can result in the former casting shadows on the latter. We present a new instance of shadowing on the outer disk around a very low mass star, ZZ Tau IRS. Through the analysis of near-infrared (NIR) archival data at $\lambda=1.6$ $\mu$m acquired with the Wide Field Camera 3 on the Hubble Space Telescope, we identified brightness asymmetries in the top and bottom halves of the highly inclined outer disk, separated by a dark lane. The brighter sides in the top and bottom halves are on the opposite sides, which we attributed to shadows cast by a misaligned inner disk. Radiative transfer modeling of the system with a misaligned angle of 15 deg between the inner and outer disks well reproduced the observations. Additionally, we found an elevated brightness temperature of $^{12}$CO (3-2) at $r\sim30$ au on the brighter side in NIR wavelengths in the top half disk, which can be explained by the shadowing effect too. While the origin of the misaligned inner disk remains unclear, future monitoring observations to search for temporal variations in brightness asymmetries will likely provide useful clues.

# Introduction

Planet formation takes place in protoplanetary disks. During their formation, gas giant planets perturb the host disk and produce substructures through planet-disk interactions (cite: Paardekooper2023PPVII). A variety of substructures, including rings/gaps, spirals, and crescents, have been predicted (cite: Bae2023PPVII), and observed in numerous disks, with rings/gaps being the most prevalent (cite: Andrews2018DSHARP; vandermarel2023). Additionally, some systems exhibit misaligned inner disks relative to outer disks (cite: Benisty2023PPVII). It is noteworthy that the orbits of planets in our Solar System are also misaligned relative to the Sun’s equator (cite: Kuiper1951SolarSystem), which may be related to these misaligned planet-forming disks.

Various mechanisms have been proposed to induce a misaligned inner disk. One such mechanism involves a misaligned stellar magnetic field relative to its disk, which can create a magnetically warped inner disk edge (cite: bouv99). Anisotropic accretion flow of gas from envelopes is also expected to occur in early evolutionary stages such as class 0/I, resulting in subsequent formation of disks with different rotational axes (cite: Bate2018a; sakai2019; sai2020a). Furthermore, a misaligned massive companion embedded in the disk can cause disk misalignment through companion-disk interactions (cite: Zhu2019a).

Misaligned inner disks have been discerned through both direct and indirect methods. Infrared interferometric observations have directly constrained the geometries of a few misaligned inner disks (cite: Labdon2019CHARA; Bohn2022a). Indirectly, shadows in the outer disk, cast by a misaligned inner disk obstructing starlight, have been detected at optical and near-infrared (NIR) wavelengths. While an inner disk with a small misalignment of a few to $\sim$10 degrees can cast a broad shadow in the outer disk (cite: Debes2017TWHya; beni2018; muro2020a; Zurlo2021BHB2007-1; Villenave2023Edge-on), an inner disk misaligned by a few tens of degrees casts two narrow shadow lanes (cite: Krist2002GGTau; Marino2015HD142527; Pinilla2015J1604; Stolker2016a; Benisty2017HD100453; Casassus2018a; Kraus2020GWOri; Ginski2021SUAur). Another observational approach capable of identifying misalignments in disks is gas kinematic observations at radio frequencies: the misaligned inner disk twists the gas velocity field, creating an ‘S’- or ‘Z’-shaped pattern at the boundary of red-shifted and blue-shifted components (cite: Rosenfeld2014Radialflow; Mayama2018; Bi2020GWOri).

When the misaligned inner disk casts a shadow on the outer disk, local disk temperature in the shadow may or may not decrease significantly, depending on the cooling timescale. The temperature drops depend on the surface density of the outer disk, the extent of cooling during the shadow crossing time, and the efficiency of radiative diffusion (cite: Casassus2019Cooling; Arce-Tord2023DoAr44). Analyses of shadowed disks provide an alternative method for estimating the surface density of disks.

In this paper, we report an occurrence of shadowing in the protoplanetary disk surrounding ZZ Tau IRS. ZZ Tau IRS, with a mass of 0.1 to 0.2 $M_\ensuremath{\odot}$ (cite: Andrews2013), is classified as a very low-mass (VLM) star and is situated at an assumed distance of 130.7 pc[^1] (cite: akeson2019) in the Taurus star-forming region. It hosts a dust disk with a mass of about 24–50 $M_\ensuremath{\oplus}$ (cite: Hashimoto2021zztauirs), making it the most massive known disk among VLM stars (cite: ansdell2017a). The outer ring at $r \sim 60$ au is also the largest, and it hosts a crescent with an azimuthal contrast of 1.4 at $\lambda = 0.9$ mm (cite: Hashimoto2021zztauirs). Recent observations have revealed the growth of dust grains in the crescent to millimeter size (cite: Hashimoto2022ZZTauIRS). ZZ Tau IRS is currently the only known VLM star with a ring and crescent configuration (cite: Pinilla2022review). The innermost disk is likely nearly edge-on (cite: white2004; furlan2011) while the outer disk has an inclination of approximately 60 deg (cite: Hashimoto2021zztauirs), suggesting a misalignment with the outer ring at an angle of approximately 30 deg. This fact implies the presence of shadows, which have not been previously reported.

# HST archive data and PSF subtraction

We utilized archival data of ZZ Tau IRS from observations conducted with the Wide Field Camera 3 (WFC3) on the Hubble Space Telescope (HST) as part of HST Proposal 14181 (cite: Pontoppidan2020HST; Habel2021HST) . The observations were executed on August 23, 2017, with an exposure time of 1,596.9 seconds. The broad-band filter F160W, centered on 1536.9 nm with a bandwidth of 268.3 nm, was employed for these observations. The data underwent calibration through the `calwf3` data processing pipeline. The calibration process included basic calibration of the raw data such as subtracting the zeroth read, dark, and bias, correcting for detector nonlinearities, performing flat fielding, and removing cosmic rays. As the `calwf3` pipeline does not correct for geometric distortion, `AstroDrizzle`, part of the `Drizzlepac` package, was utilized for distortion correction. The final product, suffixed with ‘`_drz`,’ was obtained from the Multimission Archive at STScI (MAST). The stellar Full Width at Half Maximum (FWHM), measured in field stars within the field of view (FoV), was found to be 0.23$''$. Finally, the absolute flux, expressed in Jy, was determined using the value of `PHOTFNU` in the FITS header.

![](zztauirs_image_v2.pdf)

Prior to subtracting the Point Spread Function (PSF) of ZZ Tau IRS, the PSF of ZZ Tau, situated 35$\ensuremath{''}$ to the north (refer to the HST image with a wider field-of-view in Figure [8](#figA:field) in Appendix), was subtracted using the Image Reduction and Analysis Facility (cite: Tody1986IRAF). This step was necessary because the diffraction pattern of the telescope spider associated with ZZ Tau contaminated the PSF of ZZ Tau IRS. The PSF used for subtracting ZZ Tau is at the same filter F160W and was meticulously chosen from the WFC3 PSF database[^2] on the MAST Portal. We selected a PSF that exhibited sufficient brightness to induce a bright diffraction pattern at the position of ZZ Tau IRS. Additionally, to avoid subtractions on the disk of ZZ Tau IRS, the PSF used to subtract ZZ Tau was chosen to have no visible stars within 3$\ensuremath{''}$ at the position of ZZ Tau IRS. U Car observed with WFC3/F160W as part of HST Program 13335 (cite: Riess2018HST1; Riess2018HST2) was chosen for PSF subtraction of ZZ Tau by simply scaling the PSF of U Car. For the PSF subtraction of ZZ Tau IRS, we selected a PSF star, Gaia DR3 147869474824734208, in the same image as ZZ Tau IRS, with no visible stars within 3$\ensuremath{''}$. The PSF of ZZ Tau IRS was then subtracted by scaling the PSF star. The PSF-subtracted image is shown in Figure [1](#fig:zztauirs_image). While the spatial resolution is 0.23$''$, we convolved the image with a larger Gaussian kernel of 0.64$''$ in diameter to mitigate residuals from the PSF subtraction process, specifically addressing remnants of the diffraction pattern from the telescope spider. As several stars are contaminated in the PSF stars, there are black spots beyond 3$\ensuremath{''}$ from ZZ Tau IRS in the PSF-subtracted image.

# Results

Extended structures out to approximately $r=2.5\ensuremath{''}$ (300 au) have been identified around ZZ Tau IRS in the scattered light image in Figure [1](#fig:zztauirs_image)(a). The top and bottom half disks are separated by a dark lane annotated in Figure [1](#fig:zztauirs_image)(b), representing the disk midplane of the disk. This result is consistent with the fact that the outer disk at $r\sim60$ au in ALMA observations is known to be inclined by approximately 60 deg (cite: Hashimoto2021zztauirs). The dark lane appears to exhibit a slight diagonal orientation along the south-east/north-west axis due to the absence of a portion of the dark lane. This effect is also evident in our modeling in §[4](#sec:modeling).

![](radprof_v1.pdf)

We assessed the existence of the dark lane by examining the radial profiles. Figure [2](#fig:radprof) displays the radial profiles along PA $=$ 265 deg, which is the direction indicated by the black arrow in Figure [1](#fig:zztauirs_image)(b), for the PSF-subtracted ZZ Tau IRS and the PSF reference star Gaia DR3 147869474824734208. Since the dark lane along the disk minor axis at PA $=$ 225 deg is closer to the mask edge, we opted to plot the radial profiles at PA $=$ 265 deg instead. We distinctly observed a dip at approximately $r=1$ arcsec in the radial profile of ZZ Tau IRS. As the PSF reference star exhibits monotonic decrease, the dip in the radial profile of ZZ Tau IRS is not attributed to artifacts created by the PSF subtraction processes outlined in § [2](#sec:obs). Therefore, we consider that the dark lane is a real feature in the disk.

The top and bottom half disks exhibit brightness asymmetries, however on the opposite sides. The southeast side is brighter in the top half, while the northwest side is brighter in the bottom half. We attribute these brightness asymmetries to shadows cast by the misaligned inner disk on the outer disk. Such a brightness asymmetry caused by shadows has been reported in disk modeling before, for example, by (cite: Facchini2018Warp) (refer to their Figure 9m).

To explore additional observational evidence of the presence of a misaligned inner disk, we revisited ALMA $^{12}$CO (3-2) observations reported by (cite: Hashimoto2021zztauirs). In cases where the inner disk is misaligned with the outer disk, the boundary between red-shifted and blue-shifted components in the inner disk — i.e., the minor axis of the inner disk — is expected to be tilted relative to the outer disk’s minor axis (cite: Rosenfeld2014Radialflow), unless the minor axes of the inner and outer disks are aligned. Figure [3](#fig:co_m1) shows the $^{12}$CO moment 1 map. We found an approximate 15-deg tilt of the minor axis in the inner disk relative to the outer disk’s minor axis. While acknowledging that the 15-deg tile of the inner disk’s minor axis in Figure [3](#fig:co_m1) may be affected by the beam size, we are confident in asserting the presence of a misaligned inner disk around ZZ Tau IRS.

![](zztauirs_CO_m1_v1.pdf)

We did not find a cavity/gap structure in the HST image in Figure [1](#fig:zztauirs_image), while a dust ring structure at $r=58$ au (0.45$''$) was previously reported in (sub)mm wavelengths (cite: Hashimoto2021zztauirs). The central region within approximately $r=80$ au (0.6$''$) in Figure [1](#fig:zztauirs_image) is masked due to large residual noises. A potential cavity/gap in the optical/NIR wavelengths comparable to the mm-ring may be present. In addition, the counterpart of the (sub)mm emission cavity at the NIR wavelength may have a small radius (cite: dong12cavity), making it harder to detect.

Additionally, no narrow shadows are apparent in the outer disk in Figure [1](#fig:zztauirs_image). (cite: white2004) and (cite: furlan2011) have suggested the presence of a nearly edge-on innermost disk, which is expected to cast two narrow shadows on the outer disk (cite: Whitney2013MCRT). The identification of such narrow shadows in the present HST observations may be challenging due to the low angular resolution of 0.23$''$. To more effectively search for the cavity/gap structure and the two narrow shadows, higher spatial and contrast observations are necessary.

# Radiative transfer modeling

As introduced in § [1](#sec:intro), the brightness asymmetry in the outer disk can be attributed to shadows cast by a misaligned inner disk. Given that nearly half of the top and bottom half outer disks are shadowed in Figure [1](#fig:zztauirs_image), the misalignment is likely small (cite: Debes2017TWHya; beni2018; muro2020a). In this section, we assess the aforementioned hypothesis by employing radiative transfer modeling through the Monte Carlo radiative transfer (MCRT) code (`HOCHUNK3D`; (cite: Whitney2013MCRT)).

![](surface_density_v2.pdf)

In our modeling, we excluded the edge-on innermost disk proposed by (cite: white2004; furlan2011) because the HST image in Figure [1](#fig:zztauirs_image) did not distinctly reveal the two expected narrow shadows (§ [3](#sec:results)). We considered two disks: the misaligned inner disk casting shadows and the outer disk shadowed over extended areas.

## Setup and results

The MCRT code follows a two-layer disk model featuring small dust grains (up to micron size) well-mixed with the gas and large dust grains (up to millimeter size) in the disk midplane (cite: DAlessio2006Disk). The disk structure and dust properties are described in (cite: hashimoto+15). In summary, we utilize the standard interstellar-medium dust model for the small dust grains ((cite: Kim1994SmallDust); a composite of silicates and graphites with a size distribution of $n(s) \propto s^{-3.5}$ from $s_{\rm min} = 0.0025$ $\mu$m to $s_{\rm max} = 0.2$ $\mu$m) and dust Model 2 in (cite: Wood2002LargeDust) for the large dust grains (a composite of carbons and silicates with a size distribution of $n(s) \propto s^{-3.5}$ from $s_{\rm min} = 0.01$ $\mu$m to $s_{\rm max} = 1000$ $\mu$m).

![](mcrt_v4.pdf)

![](comparison_v1.pdf)

The radial surface densities for both large and small grains shown in Figure [4](#fig:sigma) were assumed to follow the same power-law profiles: $$\begin{eqnarray*}
\Sigma(r) &=& C \cdot \Sigma_{0} (r/r_{0})^{-1}, \\
C &=& \left \{
\begin{array}{llllllll}
0 &{\rm for}&                 & & r  &\leq& r_{\rm sub}\\
1 &{\rm for}& r_{\rm sub}     &<& r  &\leq& r_{\rm gap\mathchar`-in}\\
0 &{\rm for}& r_{\rm gap\mathchar`-in}  &<& r  &\leq& r_{\rm gap\mathchar`-out}\\
1 &{\rm for}& r_{\rm gap\mathchar`-out} &<& r  &\leq& r_{\rm out},
\end{array}
\right. 
\end{eqnarray*}$$ where $r_{0}$ is a radial scaling factor, and $\Sigma_{0}$ is the surface density at $r_0$ set by the total (gas $+$ dust) disk mass ($M_{\rm disk}$) assuming a gas-to-dust mass ratio of 100. The dust sublimation radius $r_{\rm sub}$ is at approximately 0.04 au and is determined as the radius at which the temperature reaches the sublimation temperature $T_{\rm sub} \sim 1600$ K (cite: Dullemond2001).

We introduce a gap that separates the inner and outer disks. To simplify the model, we assume this gap to be devoid of material. In practice, the residual gas within the gap may form a warp connecting the inner and outer disks, resulting in the observed CO emission pattern (Figure [3](#fig:co_m1)). Regarding the inner disk, given its poorly constrained size, we assume $r_{\rm gap\mathchar`-in}=1$ au. Our experiments have shown that the shadow in the outer disk is not affected by the inner disk size. For the outer disk, we adopt an inner radius of $r_{\rm gap\mathchar`-out}=60$ au based on ALMA dust observations (cite: Hashimoto2021zztauirs). The outer edge of the outer disk is assumed to be at $r_{\rm out}=300$ au, as indicated by Figure [1](#fig:zztauirs_image). Figure [4](#fig:sigma) illustrates the surface densities of large and small dust grains in our model. We set $M_{\rm disk}$ to 0.01 $M_\ensuremath{\odot}$ based on previous ALMA (sub)mm observation (cite: Hashimoto2021zztauirs). The mass fraction of large dust grains in the total dust mass is set to 0.9.

The scale heights ($h$) of both large and small grains were assumed to change radially following $h \propto r^{p}$. We assumed $p=1.15$ as it yielded a favorable fit to the observations. At $r=100$ au, we set $h$ to be 1 au for the large dust grain disk and 7 au for the small dust grain disk.

To illustrate the geometry of misalignment, we introduce a Cartesian coordinate system, as depicted in the inset of Figure [5](#fig:mcrt)(a). Initially, the midplane of both the inner and outer disks are positioned on the xy-plane. Next, the rotational axis of the inner disk, originally pointing in the $z$-direction, is tilted within the $yz$-plane by 5 to 30 deg towards the $-y$-direction. After several iterations, we set the tilt angle to 15 deg to achieve a good agreement with HST observations. Finally, we observe the system at $\theta=0$ deg and $\phi=60$ deg (i.e., the direction of the line of sight), representing a disk inclination of 60 deg (cite: Hashimoto2021zztauirs), as shown in the schematic view in Figure [5](#fig:mcrt)(a).

Figure [5](#fig:mcrt)(b) presents a synthesized scattered light image at $\lambda=1.6$ $\mu$m of our model. The top and bottom half disks show brightness asymmetries on the opposite sides, reproducing the morphology of the disk around ZZ Tau IRS in Figure [1](#fig:zztauirs_image). While the outer disk in our model is set to align perfectly horizontally, the dark lane representing the disk midplane appears to exhibit a slight diagonal orientation along the southeast/northwest axis due to the effect of shadows. This is consistent with the observed image in Figure [1](#fig:zztauirs_image). Figure [6](#fig:comparison) presents a direct comparison between the HST image and the model image convolved with a Gaussian kernel with a diameter of 0.64$''$, demonstrating a good agreement between the two.

![](schematics_v3.pdf)

## Caveat

As mentioned at the beginning of this section, we excluded the edge-on inner disk proposed by (cite: white2004; furlan2011) from our modeling. The Spectral Energy Distribution (SED) of ZZ Tau IRS clearly reveals deficits in flux density at optical/NIR wavelengths (cite: furlan2011), possibly caused by the blocking of stellar light by the edge-on inner disk. In contrast, since the inclination of the misaligned inner disk in our modeling is approximately 60 deg, the central star is not significantly obscured by the misaligned inner disk (cite: Whitney2013MCRT). Although our modeling effectively replicates the observed asymmetric features in the outer disk captured by HST, it does not reproduce the SED. A comprehensive exploration of the parameter space is necessary to assess the feasibility of adjusting the properties of the inner and outer disks in our model (e.g., viewing geometry, scale height, and mass) to reconcile both the HST observations and the SED. Alternatively, it is plausible that an additional disk component, such as an innermost disk inside our shadow-casting disk, is required to adequately reproduce the SED. These considerations extend beyond the scope of this paper.

# Discussion

## Comparison with ALMA (sub)mm results

ZZ Tau IRS was observed with ALMA at $\lambda=870$ $\mu$m (cite: Hashimoto2021zztauirs). We have presented a comparison between the NIR image (Figure [1](#fig:zztauirs_image)) and ALMA images showing the $^{12}$CO brightness temperature and the dust continuum in Figure [9](#figA:alma) in the Appendix. Both ALMA images relate to temperature, exhibit greater brightness on the southeast side. The $^{12}$CO is generally optically thick, effectively tracing the surface of the upper disk. The elevated surface temperature on the southeast side of the top disk in Figure [9](#figA:alma)(a) can be attributed to direct irradiation, a consequence of the shadowing inner disk.

In the case of dust continuum, significant contributions to (sub)millimeter emissions come from large dust grains situated in the disk midplane (cite: Andrews2020ARAA). The disk composed of these large dust grains is geometrically thin, allowing it to be considered vertically isothermal. Despite the presence of shadows, both the southeast and northwest sides receive an equal amount of irradiation, resulting in comparable disk temperature on both sides. This is different from the situation in which narrow lane shadows result in a local temperature drop relative to the rest of the disk (cite: Casassus2019Cooling; Arce-Tord2023DoAr44). Consequently, the observed brightness asymmetry in the dust continuum cannot be attributed to shadows. Indeed our modeling in dust continuum at $\lambda=0.9$ mm in Figure [5](#fig:mcrt)(c) exhibits symmetric brightness distributions. Instead, it may be linked to asymmetric distributions of properties and/or surface density of dust grains.

Figure [7](#fig:schematics) presents schematics of the ZZ Tau IRS system. In addition to featuring the misaligned inner disk and the shadowed outer disk, the diagram depicts the outer disk composed of large dust grains, traced by (sub)millimeter emissions. It also shows the presence of warmer CO gas in proximity to the central star, along with CO gas within the gap that might form a warp connecting the inner and outer disks.

## Origin of misalignment

Several mechanisms have been proposed to elucidate disk misalignments, such as the stellar magnetic field, anisotropic accretion flow, and the influence of an inclined massive companion (refer to § [1](#sec:intro)). The variation in shadows caused by the precession of the inner disk periodically obscuring the central star could serve as a diagnostic tool for identifying the origins. However, the presence of such variability in the outer disk around ZZ Tau IRS has not been explored, as only one epoch of HTS/WFC3 NIR observation has been carried out[^3]. In this subsection, we will explore how to differentiate the origin of misalignment through the brightness variability of the outer disk.

*Stellar magnetic field —* The inner disk undergoes warping due to a misaligned stellar magnetic field, and the timescale of variability may align with the stellar rotational period. However, the rotational period of ZZ Tau IRS has not been reported. Assuming that ZZ Tau IRS shares a similar rotational period with other T-Tauri stars (cite: Bouvier1989StarRot), it could be approximately 1-10 days.

*Anisotropic accretion flow —* The direction of angular momentum in different disks is anticipated to be stable on short timescales, as precession of disks caused by their mutual gravitational interaction is expected to be slow due to the large separation of the inner and outer disks in the current model.

*A massive companion on an orbit misaligned from the disk —* Such a companion has the potential to create a gap and induce misalignment and precession of the inner disk (cite: Zhu2019a). According to equation (28) in (cite: Zhu2019a), the precession timescale for $q=M_{\rm p}/M_*=0.05$ is approximately 10$^2$ orbits of the planet. Even if the 10 $M_{\rm Jup}$ planet’s orbit is as close as 0.05 au to the dust sublimation radius (§ [4](#sec:modeling)), the precession timescale for the inner disk around ZZ Tau IRS is approximately 10$^3$ days.

According to the core (pebble) accretion scenario, very low-mass (VLM) stars, typically defined as having a mass of $\lesssim0.2 M_\ensuremath{\odot}$, including ZZ Tau IRS, are expected to be capable of forming only low-mass planets, typically up to a few Earth masses (cite: Payne2007a; Ormel2017a; Schoonenberg2019; liu2019a; Liu2020a; miguel2020a; burn2021). Meanwhile, a recent study by (cite: Pan2023VLM) suggests that even around VLM stars, giant planets are still likely to form. This process involves the initial formation of multiple low-mass protoplanets, followed by their growth through a combination of pebble accretion and planet-planet collisions within disks.

The origin of misalignment of the inner disk around ZZ Tau IRS remains uncertain. Meanwhile, monitoring observations for brightness asymmetries of the disk could provide valuable insights into its origin, as discussed earlier. Intriguingly, the discovery of long-term variability with a timescale of approximately 10$^3$ days in the future could suggest the presence of a massive planet, although the situation is degenerated, as a brown dwarf at larger separation may lead to the same precession timescale of the inner disk as a planet at smaller separation. Such a finding would pose a challenge to existing core accretion models if the perturber is a massive planet.

# Summary

We analyzed HST archival NIR ($\lambda=1.6$ $\mu$m) observations of ZZ Tau IRS. The scattered light image clearly shows that the disk is separated by a dark lane, typical for disks at relatively high inclinations. Additionally, we identified brightness asymmetries in the top and bottom halves of the disk, and their brighter sides on the opposition sides. We attributed the brightness asymmetries to shadows cast by a misaligned inner disk. Furthermore, we presented a radiative transfer model to explain the HST observations with an inner disk inclined by 15 degrees relative to the outer disk.

We revisited $^{12}$CO brightness temperature and the dust continuum at $\lambda=870$ $\mu$m observed by ALMA. Both images revealed a brighter side in the southeast region of the disk, similar to the pattern observed in the near-infrared scattered light image. The asymmetry of $^{12}$CO brightness temperature can be attributed to shadows, while the asymmetry in the dust continuum may be linked to asymmetry in the spatial distribution of dust surface density and/or dust properties.

We discussed potential origins for the misaligned inner disk, including the stellar magnetic field, anisotropic accretion flow, and an inclined massive companion. While the specific cause remains open, future monitoring observations for variability of brightness asymmetries hold the promise of offering valuable insights.

The authors thank the anonymous referee for a timely and constructive report. The authors thank Yifan Zhou for useful comments on data reduction. This study was supported by JSPS KAKENHI Grant Numbers 21H00059, 22H01274, 23K03463. H.B.L. is supported by the National Science and Technology Council (NSTC) of Taiwan (Grant Nos. 111-2112-M-110-022-MY3). Some/all of the data presented in this article were obtained from the Mikulski Archive for Space Telescopes (MAST) at the Space Telescope Science Institute. The specific observations analyzed can be accessed via . This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01511.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC (Taiwan), ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. IRAF is distributed by the National Optical Astronomy Observatories, which are operated by the Association of Universities for Research in Astronomy, Inc., under cooperative agreement with the National Science Foundation.

# Software

astropy (cite: Astropy2013; Astropy2018; Astropy2022), Numpy (cite: VanDerWalt2011), IRAF (cite: Tody1986IRAF), Matplotlib (cite: Hunter2007Matplotlib)

# Facilities

HST, ALMA

# HST image with wide field-of-view

We provide the HST image with a wide field-of-view in Figure [8](#figA:field) for readers to easily discern the positions of ZZ Tau, ZZ Tau IRS, and the PSF reference star Gaia DR3 147869474824734208 for ZZ Tau IRS, in the PSF subtraction process in § [2](#sec:obs). The PSF reference star U Car for ZZ Tau is in a separate field.

![](field_v1.pdf)

# ALMA results of ZZ Tau IRS

We revisited ALMA images of the $^{12}$CO brightness temperature and the dust continuum at $\lambda=870$ $\mu$m in Figure [9](#figA:alma) (cite: Hashimoto2021zztauirs).

![](alma_v3.pdf)

natexlab

(ref: akeson2019) Akeson, R. L., Jensen, E. L. N., Carpenter, J., et al. 2019, ApJ, 872, 158

(ref: Andrews2020ARAA) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: Andrews2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129

(ref: Andrews2018DSHARP) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: ansdell2017a) Ansdell, M., Williams, J. P., Manara, C. F., et al. 2017, AJ, 153, 240

(ref: Arce-Tord2023DoAr44) Arce-Tord, C., Casassus, S., Dent, W. R. F., et al. 2023, MNRAS, 526, 2077

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: Bae2023PPVII) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423

(ref: Bate2018a) Bate, M. R. 2018, MNRAS, 475, 5618

(ref: Benisty2017HD100453) Benisty, M., Stolker, T., Pohl, A., et al. 2017, A&A, 597, A42

(ref: beni2018) Benisty, M., Juhász, A., Facchini, S., et al. 2018, A&A, 619, A171

(ref: Benisty2023PPVII) Benisty, M., Dominik, C., Follette, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 605

(ref: Bi2020GWOri) Bi, J., van der Marel, N., Dong, R., et al. 2020, ApJL, 895, L18

(ref: Bohn2022a) Bohn, A. J., Benisty, M., Perraut, K., et al. 2022, A&A, 658, A183

(ref: Bouvier1989StarRot) Bouvier, J., & Bertout, C. 1989, A&A, 211, 99

(ref: bouv99) Bouvier, J., Chelli, A., Allain, S., et al. 1999, A&A, 349, 619

(ref: burn2021) Burn, R., Schlecker, M., Mordasini, C., et al. 2021, A&A, 656, A72

(ref: Casassus2019Cooling) Casassus, S., Pérez, S., Osses, A., & Marino, S. 2019, MNRAS, 486, L58

(ref: Casassus2018a) Casassus, S., Avenhaus, H., Pérez, S., et al. 2018, MNRAS, 477, 5104

(ref: DAlessio2006Disk) D’Alessio, P., Calvet, N., Hartmann, L., Franco-Hernández, R., & Servı́n, H. 2006, ApJ, 638, 314

(ref: Debes2017TWHya) Debes, J. H., Poteet, C. A., Jang-Condell, H., et al. 2017, ApJ, 835, 205

(ref: dong12cavity) Dong, R., Rafikov, R., Zhu, Z., et al. 2012, ApJ, 750, 161

(ref: Dullemond2001) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957

(ref: Facchini2018Warp) Facchini, S., Juhász, A., & Lodato, G. 2018, MNRAS, 473, 4459

(ref: furlan2011) Furlan, E., Luhman, K. L., Espaillat, C., et al. 2011, ApJS, 195, 3

(ref: gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1

(ref: gaia2022) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2022, arXiv e-prints, arXiv:2208.00211

(ref: Ginski2021SUAur) Ginski, C., Facchini, S., Huang, J., et al. 2021, ApJL, 908, L25

(ref: Habel2021HST) Habel, N. M., Megeath, S. T., Booker, J. J., et al. 2021, ApJ, 911, 153

(ref: Hashimoto2021zztauirs) Hashimoto, J., Dong, R., & Muto, T. 2021, AJ, 161, 264

(ref: Hashimoto2022ZZTauIRS) Hashimoto, J., Liu, H. B., Dong, R., Liu, B., & Muto, T. 2022, ApJ, 941, 66

(ref: hashimoto+15) Hashimoto, J., Tsukagoshi, T., Brown, J. M., et al. 2015, ApJ, 799, 43

(ref: Hunter2007Matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: Kim1994SmallDust) Kim, S.-H., Martin, P. G., & Hendry, P. D. 1994, ApJ, 422, 164

(ref: Kraus2020GWOri) Kraus, S., Kreplin, A., Young, A. K., et al. 2020, Science, 369, 1233

(ref: Krist2002GGTau) Krist, J. E., Stapelfeldt, K. R., & Watson, A. M. 2002, ApJ, 570, 785

(ref: Kuiper1951SolarSystem) Kuiper, G. P. 1951, Proceedings of the National Academy of Science, 37, 1

(ref: Labdon2019CHARA) Labdon, A., Kraus, S., Davies, C. L., et al. 2019, A&A, 627, A36

(ref: liu2019a) Liu, B., Lambrechts, M., Johansen, A., & Liu, F. 2019, A&A, 632, A7

(ref: Liu2020a) Liu, B., Lambrechts, M., Johansen, A., Pascucci, I., & Henning, T. 2020, A&A, 638, A88

(ref: Marino2015HD142527) Marino, S., Perez, S., & Casassus, S. 2015, ApJL, 798, L44

(ref: Mayama2018) Mayama, S., Akiyama, E., Panić, O., et al. 2018, ApJL, 868, L3

(ref: miguel2020a) Miguel, Y., Cridland, A., Ormel, C. W., Fortney, J. J., & Ida, S. 2020, MNRAS, 491, 1998

(ref: muro2020a) Muro-Arena, G. A., Benisty, M., Ginski, C., et al. 2020, A&A, 635, A121

(ref: Ormel2017a) Ormel, C. W., Liu, B., & Schoonenberg, D. 2017, A&A, 604, A1

(ref: Paardekooper2023PPVII) Paardekooper, S., Dong, R., Duffell, P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 685

(ref: Pan2023VLM) Pan, M., Liu, B., Johansen, A., et al. 2023, arXiv e-prints, arXiv:2311.10317

(ref: Payne2007a) Payne, M. J., & Lodato, G. 2007, MNRAS, 381, 1597

(ref: Pinilla2022review) Pinilla, P. 2022, European Physical Journal Plus, 137, 1206

(ref: Pinilla2015J1604) Pinilla, P., de Boer, J., Benisty, M., et al. 2015, A&A, 584, L4

(ref: Pontoppidan2020HST) Pontoppidan, K. M., Green, J. D., Pauly, T. A., Salyk, C., & DePasquale, J. 2020, ApJ, 896, 169

(ref: Riess2018HST2) Riess, A. G., Casertano, S., Yuan, W., et al. 2018a, ApJ, 861, 126

(ref: Riess2018HST1) —. 2018b, ApJ, 855, 136

(ref: Rosenfeld2014Radialflow) Rosenfeld, K. A., Chiang, E., & Andrews, S. M. 2014, ApJ, 782, 62

(ref: sai2020a) Sai, J., Ohashi, N., Saigo, K., et al. 2020, arXiv e-prints, arXiv:2003.07067

(ref: sakai2019) Sakai, N., Hanawa, T., Zhang, Y., et al. 2019, Nature, 565, 206

(ref: Schoonenberg2019) Schoonenberg, D., Liu, B., Ormel, C. W., & Dorn, C. 2019, A&A, 627, A149

(ref: Stolker2016a) Stolker, T., Dominik, C., Avenhaus, H., et al. 2016, A&A, 595, A113

(ref: Tody1986IRAF) Tody, D. 1986, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 627, Instrumentation in astronomy VI, ed. D. L. Crawford, 733

(ref: vandermarel2023) van der Marel, N. 2023, European Physical Journal Plus, 138, 225

(ref: VanDerWalt2011) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22

(ref: Villenave2023Edge-on) Villenave, M., Stapelfeldt, K. R., Duchene, G., et al. 2023, arXiv e-prints, arXiv:2311.07668

(ref: white2004) White, R. J., & Hillenbrand, L. A. 2004, ApJ, 616, 998

(ref: Whitmore2016HSTcatalog) Whitmore, B. C., Allam, S. S., Budavári, T., et al. 2016, AJ, 151, 134

(ref: Whitney2013MCRT) Whitney, B. A., Robitaille, T. P., Bjorkman, J. E., et al. 2013, ApJS, 207, 30

(ref: Wood2002LargeDust) Wood, K., Wolff, M. J., Bjorkman, J. E., & Whitney, B. 2002, ApJ, 564, 887

(ref: Zhu2019a) Zhu, Z. 2019, MNRAS, 483, 4221

(ref: Zurlo2021BHB2007-1) Zurlo, A., Garufi, A., Pérez, S., et al. 2021, ApJ, 912, 64

[^1]: We do not use the GAIA distance of 105.7 pc because the astrometric solution is poor with a value of the renormalized unit weight error (RUWE) of 2.490 (cite: gaia2016; gaia2022).

[^2]: https://www.stsci.edu/hst/instrumentation/wfc3/data-analysis/psf/psf-search

[^3]: Except HTS/WFC3 NIR observations, ZZ Tau IRS was observed with HST/WFPC2 at visible wavelengths in 1999-Oct-25 (program ID of 8216). The comparison of ZZ Tau IRS disk at different wavelengths will be present in the future work.

</paper>

Write the methods card for this paper.