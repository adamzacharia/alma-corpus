# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...701A..31P\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...701A..31P",
 "title": "Spatially resolved Hα emission in B14-65666: Compact starbursts, ionizing efficiency, and gas kinematics in an advanced merger at the Epoch of Reionization",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Prieto-Jiménez, C.",
 "n_authors": 31,
 "arxiv_id": "2507.06793",
 "doi": "10.1051/0004-6361/202555057",
 "alma_projects_linked_by_archive": [
  "2016.1.00954.S",
  "2017.1.00190.S",
  "2019.1.01491.S"
 ]
}
```

Paper text:
<paper>
#  Spatially resolved H$\alpha$ emission in B14-65666: Compact starbursts, ionizing efficiency, and gas kinematics in an advanced merger at the Epoch of Reionization

We present MIRI/JWST medium-resolution spectroscopy (MRS) and imaging (MIRIM) of B14-65666, a source identified as a Lyman-break and interacting galaxy at a redshift of $z$ = 7.15. We detect the H$\alpha$ line emission in this system, revealing a spatially resolved structure of the H$\alpha$-emitting gas, which consists of two distinct galaxies, E and W, at a projected distance of 0.4 arcsec apart (i.e., 2.2 kpc). One of the galaxies (E) is very compact (upper limit for the effective radius of 63 pc) in the rest-frame ultraviolet light, while the other galaxy (W) is more extended (effective radius of 348 pc), showing a clumpy structure reminiscent of a tidal tail. The total H$\alpha$ luminosity implies that the system is forming stars at a rate of 76 ± 8 M$_{\odot}$ yr$^{-1}$ and 30 ± 4 M$_{\odot}$ yr$^{-1}$ for E and W galaxies, respectively. The ionizing photon production efficiency, $\log(\zeta_\mathrm{ion}$), for galaxies E and W, has values of 25.1 ± 0.1 Hz erg$^{-1}$ and 25.5 ± 0.1 Hz erg$^{-1}$, which is within the range measured in galaxies at similar redshifts. The high values derived for the H$\alpha$ equivalent widths (832 ± 100 and 536 ± 78 $\AA$) and the distinct locations of the E and W galaxies in the $\log(\zeta_\mathrm{ion}$) $-$ equivalent width (H$\alpha$) plane indicate that the system is dominated by a young (under 10 Myr) stellar population. The overall spectral-energy distribution suggests that in addition to a young stellar population, the two galaxies may have mature (over 100 Myr) stellar populations and very different dust attenuations, with galaxy E showing a larger attenuation (A$_{V}$ = 1.5 mag) compared to the almost dust-free (A$_{V}$ = 0.1 mag) galaxy W. The derived star formation rate (SFR) and stellar masses identify the two galaxies as going through a starburst phase characterized by a specific SFR (sSFR) of 40 – 50 Gyr$^{-1}$. Galaxy E has an extreme stellar mass surface density (6 $\times$ 10$^4$ M$_{\odot}$ pc$^{-2}$), close to that of the nuclei of low-$z$ galaxies, while galaxy W (10$^3$ M$_{\odot}$ pc$^{-2}$) is consistent with the surface densities measured in galaxies at these redshifts. The kinematics of the ionized gas traced by the H$\alpha$ line show a velocity difference of 175 $\pm$ 28 km s$^{-1}$ between the two components of B14-65666 and a broader profile for galaxy W (312 $\pm\,$44 km s$^{-1}$) relative to galaxy E (243 $\pm$ 41 km s$^{-1}$). The detailed study of B14-65666 shows that the complex stellar and interstellar medium structure in merging galaxy systems was already in place by the Epoch of Reionization. The general properties of B14-65666 agree with those predicted for massive merging systems at redshifts of 7 and above in the FIRSTLIGHT cosmological simulations. The in-depth study of systems such as B14-65666 reveal how galaxy mergers in the early Universe drive intense star formation, shape the interstellar medium, and influence the buildup of stellar mass, just 700 – 800 Myr after the Big Bang.

# Introduction

The *James Webb Space Telescope* (JWST, (cite: Gardner+23)) is transforming our understanding of galaxy formation, particularly during the so-called Epoch of Reionization (EoR). The JWST has photometrically detected potential galaxy candidates up to redshift 25 ((cite: perezgonzalez2025risegalacticempireluminosity)) and spectroscopically confirmed galaxies up to redshift 14.44 ((cite: naidu_2025)). At these redshifts, the rest-frame optical emission lines and continuum are redshifted into the mid-infrared (5 – 25 $\mu$m), which is the spectral range covered by the Mid-Infrared Instrument (MIRI, (cite: Rieke+15; Wright+15; Wright+23)). At redshifts of 7 and above, this instrument allows us to explore the strong optical emission lines, such as H$\alpha$.

Mergers are expected to have a greater impact on galaxy evolution at higher redshifts than at lower redshifts, as the merger rate increases with redshift ((cite: duan_2024_mergers)). The gravitational forces from mergers can cause significant disruptions in galaxy structures and movements, leading to features such as tidal tails and asymmetric stellar envelopes (e.g., (cite: toomre72); (cite: mihos_1996); (cite: Bushouse_2002); (cite: conselice_2003); (cite: Spilker+22)). These disturbances can cause gas to flow from the outer regions into the center of galaxies, triggering the formation of new stars in central areas ((cite: perez-gonzalez_24_jekyll_hyde)). Simulations such as FirstLight ((cite: Ceverino_17)) show that about 10% of galaxies at redshifts of 6 – 10 exhibit clumpy structures, which are primarily formed through mergers. The central clumps are mainly composed of older stellar populations exceeding 50 Myr, while off-center clumps originate from gas debris along tidal tails during major mergers. These mergers have a short life, typically merging into the main galaxy within a few tens of million years ((cite: nazakoto_2024)). Observational studies also support the presence of mergers in the EoR, with recent works identifying clear merger signatures in high-redshift galaxies (e.g., (cite: Alvarez-Marquez+23-SPT); (cite: arribas_24_spt); (cite: harshan_2024); (cite: hu_papovich_2025)).

High-$z$ star-forming galaxies (SFGs) are characterized by optical lines with high (rest-frame) values of the equivalent widths (EW up to 3000 $\AA$) in extreme emission line galaxies ((cite: boyett24)). There is also a trend of EW increasing with redshift, which indicates an evolution in the galaxy-specific star formation rate ((cite: Rinaldi+23); (cite: rinaldi2024emergencestarformationmain)) and young stellar populations (\< 10 Myr). Studies at low redshifts have shown that galaxies in close pairs exhibit an SFR increase compared to isolated galaxies, highlighting the impact of gravitational interactions on gas dynamics and star formation ((cite: barton_2000)). This enhancement is also observed at higher redshifts (6.5 – 8.5), with an excess in SFR of 0.26 ± 0.11 dex found in very close pairs, with no significant increase at larger separations ((cite: duan_2024); (cite: puskas25)).

B14-65666 (also known as the Big Three Dragons galaxy) was discovered based on wide-field imaging data of the UltraVISTA survey of the Cosmological Evolution Survey (COSMOS) field in Y, J, H, and K${_s}$ near-infrared bands ((cite: bowler_2012), (cite: bowler_2014_the)). It was then spectroscopically detected in Ly$\alpha$ ((cite: furusawa_2016_a)). An image captured with the Hubble Space Telescope (HST) showed that the galaxy consists of two clearly separated components in the rest-frame ultraviolet (UV), thus suggesting that the object could be undergoing a merger of two galaxies ((cite: bowler_2017_unveiling)). Observations performed with the Atacama Large Millimeter/submillimeter Array (ALMA) with Band 6 reported the detection of an $\approx$ 160 $\mu$m dust continuum at the position of the components ((cite: bowler_2018_obscured)). It also detected \[O III\] 88 $\mu$m, \[C II\] 158 $\mu$m, and underlying dust continuum emission at $\approx$ 90 $\mu$m in Bands 6 and 8 ((cite: hashimoto_2019_big)). Furthermore, they showed that \[O III\] 88 $\mu$m and \[C II\] 158 $\mu$m can be decomposed into two components that are spatially resolved and kinematically separated. These components are associated with the two UV emission peaks identified in the HST images. Additional observations with ALMA Band 7 did not detect the presence of the far-infrared \[N II\] 122 $\mu$m fine-structure emission line, nor did ALMA Band 3 observations detect other lines such as CO (6-5), CO (7-6), and \[C I\] (2-1) ((cite: sugahara_2021_big); (cite: hashimoto_2023_big)).

Recent JWST Near Infrared Camera (NIRCam) imaging has revealed the complex morphology of the two galaxy components: galaxy E consists of a compact core, surrounded by diffuse, extended, rest-frame optical emission, and galaxy W has an elongated morphology interpreted as tidal tails ((cite: sugahara_2024_rioja)). Follow-up observations with NIRSpec IFU from 2.9 – 5.3 $\mu$m directly map the strength of the rest-frame optical emission lines across the source ((cite: gareth_2024)). The profile of these lines revealed the presence of both narrow and broad line emission, with the latter indicating tidal interaction or outflows. This analysis showed that both galaxies have subsolar metallicities (0.24 Z$_\odot$ and 0.3 Z$_\odot$, E and W, respectively) and a high rate of star formation. The observations do not show evidence for the presence of an active galactic nucleus (AGN) in B14-65666.

B14-65666 is one of the few galaxies identified as undergoing a major merger during the EoR. This system allows the investigation of the physical properties of an early major merger, including its stellar structure, as well as the different phases of the interstellar medium (ISM). Additionally, this system provides a reference for direct comparisons with simulations. In this paper, we present the first spatially resolved spectroscopy of the H$\alpha$ emission in the system B14-65666 at $z$ = 7.15 based on new MIRI/JWST integral field spectroscopy. The paper presents several of the physical properties of B14-65666 based on the combination of the new MIRI data with ancillary NIRCam imaging and ALMA spectroscopy. This paper is organized as follows. In Sect. [2](#Sec:obs_cal), we present the observations and data calibrations. In Sect. [3](#Sect:analysis), we outline our analysis methods of spectroscopy and photometry. In Sect. [4](#Sec:results_dis), we present the results of the analysis. In the subsections, we study the spectral energy distribution of the galaxy ([4.1](#subSect:SED)), the attenuation ([4.2](#subSec:attenuation)), the star formation rate and burstiness ([4.3](#subSec:SFR)), the H$\alpha$ EW and ionizing photon production efficiency ([4.4](#subSec:ew)), the kinematics ([4.5](#subSect:kinematics)), the stellar and dynamical mass ([4.6](#subSect:morph)), the mass-size relation ([4.7](#subSect:mass-size)), the starburst nature ([4.8](#subSect:burstiness)), and finally the origin and evolution of the system according to simulations ([4.9](#subSect:simulations)). We discuss and analyze the spectral and spatial distribution of the H$\alpha$ line and the derived properties of the galaxies, and we study the morphology and SFR of the galaxy and compare it with local galaxies. Our conclusions are presented in Sect. [5](#Sec:conclusion_Summary).

In this paper, we assume a flat $\Lambda$CDM cosmology with $\Omega_\mathrm{m}$ = 0.310, and $H_0$ = 67.7 km s$^{-1}$ Mpc$^{-1}$ (cite: PlanckCollaboration18VI). With these parameters, 1 " is equal to 5.275 kpc at $z$ = 7.15 and the luminosity distance is $D_L$= 72276.9 Mpc. For these cosmological parameters and redshift, the age of the Universe corresponds to 740 Myr. We use vacuum emission-line wavelengths throughout the paper.

# Observations and data calibrations

## MIRI

B14-65666 was observed with MIRI on 30 April, 2023 as a part of the MIRI European Consortium guaranteed time observations (program ID 1284, PI: L. Colina). The observations are composed of MIRI imaging (MIRIM, (cite: Bouchet+15; dicken_2024_miri)) and integral field spectroscopy using the Medium Resolution Spectrograph (MRS; (cite: Wells+15; Argyriou+23)).

### MIRI spectroscopy

The MRS observations were performed with the SHORT band for channels 1 – 4. We only used Channel 1 in this study. This channel covers the wavelengths 4.9 – 5.74 $\mu$m, thus targeting the H$\alpha$ emission line at redshift 7.15 and other fainter emission lines such as \[N II\] 6550,6585 $\AA$ and \[S II\] 6718,6733 $\AA$. The total on-source exposure time of the MRS observations is 22743 seconds. The positive and negative four-point dither patterns for point sources were used. For each dither position, a total of six integrations were obtained using the SLOWR1 readout mode with 19 groups each. When the MRS targeted B14-65666, a parallel field was imaged using the MIRI F770W filter. This imaging data is utilized exclusively for the astrometric calibration of the MRS (see Sect. [2.4](#Sect:astrometry)).

We used version 1.15.1 of the JWST calibration pipeline and context 1276 of the Calibration Reference Data System (CRDS) to process and calibrate the MRS observations of B14-65666. The standard MRS pipeline procedure ((cite: bushouse_pipeline)) was used with additional customized steps to improve the quality of the final MRS-calibrated products and background (see (cite: Alvarez-Marquez+23-SPT) and (cite: Alvarez-Marquez+23-SPT) for details). Additionally, we implemented the algorithm developed by (cite: spilker_2023_spatial) to correct the striping pattern produced by the cosmic-ray showers in the spectral cube. The final Channel 1 cube has a spatial and spectral sampling of 0.13" $\times$ 0.13" $\times$ 0.8 nm ((cite: Law+23)), and the resolving power ($R\,\equiv\,\lambda/\Delta\lambda$) is about 3500 ((cite: Labiano+21); (cite: Jones+23)).

### MIRI imaging

The MIRIM observations of B14-65666 were performed using the F560W filter covering the rest-frame optical continuum at $\approx$ 0.7 $\mu$m and the H$\alpha$ emission line. The MIRIM F560W image has a total on-source integration time of 2675 seconds. The observational setup consists of a four-point dither pattern, with the dither composed of two integrations of 120 groups using the FASTR1 readout mode.

The MIRIM F560W observations are calibrated with version 1.12.0 of the JWST pipeline (cite: bushouse_pipeline) and context 1150 of the CRDS. We followed the general procedure to calibrate the data, but we also included more steps to correct for striping artifacts and background gradients (see (cite: pablo_perezgonzalez_2024_LRD); (cite: goran_ostlin_2024_midis) for details). The final MIRIM F560W mosaic has a pixel size of 0.06 ", after resampling, and a field of view (FoV) of 74" $\times$ 113 ". The point spread function (PSF) full width at half maximum (FWHM) is 0.207 " ((cite: libralato_2024_highprecision)).

## NIRCam

The NIRCam (cite: Rieke_2023) data used in this work were presented in a previous study ((cite: sugahara_2024_rioja)). The observations were taken with filters F115W, F150W, F200W, F277W, F356W, and F444W (JWST GO1 program ID 1840; PIs: J. Álvarez-Márquez and T. Hashimoto). At redshift 7.15, F115W, F150W, and F200W sample the rest-frame UV spectrum, F277W and F356W cover the Balmer break region, and F444W targets the rest-frame continuum around 5000 $\text{\AA}$ and the \[O III\] 4960,5008 $\AA$ emission lines.

NIRCam and MIRIM images present large variations on the spatial resolution, with PSF FWHMs increasing with wavelength from 0.04 " to 0.21 ". To obtain consistent multiwavelength aperture photometry in the different NIRCam and MIRIM images, we performed a PSF homogenization in the NIRCam images to match the spatial resolution of NIRCam images to the coarser MIRIM F560W image. However, we also used the NIRCam images with the native spatial resolution to investigate the structure of B14-65666 in the rest-frame UV (see Sect. [3.4](#subSect:reff)).

The PSF homogenization procedure includes the following steps. We employed the observed effective PSFs (ePSFs) for MIRI ((cite: libralato_2024_highprecision)) and for NIRCam ((cite: nardiello_2022))[^1]. We compared these ePSFs with point-like sources from our observations and conclude that they are consistent with each other. The first step was to rotate the NIRCam ePSF to the position angle (PA) of the MIRI image (PA=108º), ensuring orientation alignment between the two ePSFs. We rotate the MIRI ePSF to match the PA of the MIRI image. Next, we resampled the pixel scale of the MIRI ePSF (0.028 ", (cite: libralato_2024_highprecision)) to match that of the MIRI imager and the NIRCam ePSF (0.008 " for F115W, F150W, and F200W; and 0.016 " for F277W, F356W, and F444W; (cite: nardiello_2022)) to match the pixel scale of the MIRI imager. Using these aligned and resampled ePSFs, we then generated a matching kernel using the python package `PHOTUTILS` to bridge the differences between the NIRCam and MIRI ePSFs. Finally, to apply the kernel using the python function `creatematchingkernel` ((cite: larry_bradley_2022_6825092)), we rescaled it to the NIRCam image pixel size (0.03 " after resampling). Subsequently, we convolved the NIRCam images with the kernel, thus homogenizing the PSF.

## ALMA ancillary data

The ALMA data used in this work were previously presented in other studies. ALMA Band-6 and Band-8 data were taken in Cycles 4 (ID 2016.1.00954.S, PI: A. K. Inoue) and 5 (ID 2017.1.00190.S, PI: A. K. Inoue) to target the \[C II\] 158 $\mu$m and \[O III\] 88 $\mu$m emission lines ((cite: hashimoto_2019_big)). ALMA Band-7 data were taken during Cycle 7 (ID 2019.1.01491.S, PI: A. K. Inoue; (cite: sugahara_2021_big)). In this article, we used the spectra of \[C II\] 158 $\mu$m and \[O III\] 88 $\mu$m and the emission-line and continuum (90, 120, and 160 $\mu$m) fluxes presented in (cite: hashimoto_2019_big) and (cite: sugahara_2021_big).

## MIRI-NIRCam astrometry

We corrected the astrometry in the MIRI F560W image by using the centroid of two point-like sources within the FoV of the available GAIA DR3 (cite: GaiaCollaboration+22) coordinates. The uncertainty in the final positioning is 18 mas. With the corrected MIRIM F560W image, we aligned the simultaneous MIRIM F770W image with two point-like sources in the common FoV of both images. As the MRS data and the MIRIM F770W image were taken simultaneously, we used the astrometric offset found in the MIRIM F770W image to correct the MRS 1SHORT cube, obtaining an uncertainty of less than 60 mas (0.3 kpc). Finally, we aligned the NIRCam images using the astrometrically corrected MIRIM F560W image as we did for the simultaneous MIRIM F770W image. The NIRCam images have an uncertainty smaller than 35 mas; this was obtained with the available star and galaxy that have Gaia astrometry (cite: GaiaCollaboration+22).

# Analysis

![](mirim_mrs_nircam2.png)

## MIRI and NIRCam images and H$\alpha$ line map

Previous HST images showed that B14-65666 is composed of two spatially separated galaxies in the rest-frame UV, a brighter galaxy in the northeast (galaxy E), and a fainter galaxy in the southwest (galaxy W) ((cite: bowler_2017_unveiling)). ALMA data further demonstrated that the \[O III\] 88 $\mu$m and \[C II\] 158 $\mu$m emission lines can be spatially and spectrally decomposed into two components associated with galaxies E and W ((cite: Hashimoto+18)). NIRCam images revealed the complex morphology of the individual galaxy components ((cite: sugahara_2024_rioja)): galaxy E has a compact core surrounded by diffuse extended optical emission, while galaxy W displays elongated clumpy morphology.

The MIRIM and MRS data cover the emission line of H$\alpha$ together with the continuum at 0.7 $\mu$m. MIRI observations show a similar trend to NIRCam images. MRS shows an extended H$\alpha$ emission associated with E and W galaxy components; additionally, each of these galaxy components is spectroscopically resolved as they were already presented in ALMA observations ((cite: hashimoto_2019_big)). We present MIRI and NIRCam images in Fig. [1](#fig:all).

For this study, we defined a total elliptical aperture for the whole system (named galaxies E+W) with a semi-major axis of 0.456 ", semi-minor axis of 0.343 ", and position angle (PA) of 85.83º. In the case of the galaxy E we define an elliptical aperture with semi-major axis of 0.211 " and semi-minor axis of 0.201 ", position angle (PA) of 112.83º. For the galaxy W, we extracted an ellipse with a 0.228 " and 0.177 " semi-major and semi-minor axis, respectively, and a PA of 112.83º. The coordinates of the center are shown in Table [\[tab:results\]](#tab:results). The E and W elliptical apertures are compatible with the main emission of these galaxy components in our MIRIM F560W image. The elliptical aperture of galaxies E+W covers the extended H$\alpha$ emission from the MRS H$\alpha$ line map. The H$\alpha$ line map is generated by integrating the H$\alpha$ line emission, centered at the H$\alpha$ peak of galaxies E+W (5.3510 $\mu$m) in the velocity range -500 \< *v* \[km s$^{-1}$\] \< 300 (see Fig. [1](#fig:all)).

![](spectra_final.png)

| Parameter | Galaxies E+W | Galaxy E | Galaxy W |  |
|:---|:--:|:--:|:--:|:--:|
| RA (ICRS) | 10:01:40.6858s | 10:01:40.6984s | 10:01:40.6707s |  |
| DEC (ICRS) | +1:54:52.553s | +1:54:52.616s | +1:54:52.481s |  |
| Redshift | $7.1513 \pm 0.0007$ | $7.1529 \pm 0.0004$ | $7.1481 \pm 0.0007$ |  |
| FWHM \[km s$^{-1}$\] | $407 \pm 86$ | $243 \pm  41$ | $312 \pm 44$ |  |
| Flux H$\alpha$ \[$\times 10^{-18}$ erg s$^{-1}$ cm$^{-2}$\] | $23.1 \pm 3.1$ | $11.9 \pm 1.3$ | $8.6  \pm 1.2$ |  |
| H$\alpha$ peak \[$\mu$m\] | $5.3510 \pm 0.0004$ | $5.3520 \pm 0.0003$ | $5.3489 \pm 0.0004$ |  |
| Luminosity H$\alpha$ \[$\times 10^{42}$ erg s$^{-1}$\] | $14.4 \pm 2.0$ | $7.4 \pm 0.8$ | $5.3  \pm 0.7$ |  |
| Flux MIRIM F560W \[$\mu$Jy\] | $0.57\pm 0.02$ | $0.21 \pm 0.01$ | $0.22 \pm 0.01$ |  |
| Flux F115W \[$\mu$Jy\] | $0.222\pm  0.032$ | $0.073\pm 0.011$ | $0.114\pm 0.010$ |  |
| Flux F150W \[$\mu$Jy\] | $0.313\pm 0.010$ | $0.096\pm 0.003$ | $0.151\pm 0.003$ |  |
| Flux F200W \[$\mu$Jy\] | $0.288\pm 0.029$ | $0.114\pm 0.001$ | $0.119\pm 0.010$ |  |
| Flux F277W \[$\mu$Jy\] | $0.380\pm 0.100$ | $0.132\pm 0.003$ | $0.145\pm 0.003$ |  |
| Flux F356W \[$\mu$Jy\] | $0.370\pm 0.007$ | $0.125\pm  0.002$ | $0.147\pm 0.002$ |  |
| Flux F444W \[$\mu$Jy\] | $0.761\pm 0.006$ | $0.316\pm 0.002$ | $0.245\pm 0.002$ |  |

Table notes: Photometric results obtained for MIRIM and NIRCam images and spectroscopic results obtained with the MRS.

## H$\alpha$ spectra and line fluxes

We extracted the integrated H$\alpha$ spectra of galaxies E+W, E, and W using the three defined apertures (Fig. [1](#fig:all)). We corrected the two individual spectra for aperture losses, assuming that the two galaxies are unresolved sources for the MRS angular resolution taking into account the MRS PSF ((cite: Argyriou+23)), which has a FWHM of 0.27 " $\times$ 0.35 " at 5.35 $\mu$m. The aperture correction is 1/0.57 for the galaxies E and W. In the case of the galaxies E+W, we also corrected for aperture losses, assuming that the flux is mainly dominated by galaxies E and W, which are unresolved. The aperture correction in this case is 1/0.81. We also corrected the spectrum for the contamination of flux from galaxy E in the W aperture by modeling galaxy E at the center of the aforementioned PSF and measuring how much of its flux would appear in the W aperture. We applied the same procedure for galaxy W to estimate its contribution to the E aperture. These corrections are 1/0.02 and 1/0.03, respectively.

We extracted twelve 1D spectra using the same apertures as the E+W, E, and W galaxies, respectively, at random positions of the MRS FoV clean of emission. We combined these spectra to generate the 1D median of the local background. The median is subtracted from the H$\alpha$ spectra with the aim of removing any systematic residual feature left in the MRS calibration process. The three spectra are presented in Fig. [2](#fig:main_figure).

The H$\alpha$ spectrum is modeled by a single Gaussian function, to fit the emission line, and a second-order polynomial, to fit any residual background gradient. Using a Monte Carlo simulation, we estimated the uncertainties for the derived emission line parameters (such as FWHM, flux, and central wavelength). To determine the noise level in the spectrum, the root mean square (rms) was calculated from the continuum adjacent to the emission line. Using this rms value as the 1$\sigma$ standard deviation, we generated 1000 synthetic spectra by adding random Gaussian noise to the original spectrum. Each synthetic spectrum was then refit to obtain new measurements of the line parameters. The final uncertainty for each parameter is given by the standard deviation of these measurements across all simulations. The Gaussian fit is shown in Fig. [2](#fig:main_figure), and the results are presented in Table [\[tab:results\]](#tab:results).

From the H$\alpha$ line, the E+W galaxies of B14-65666 are at a redshift of 7.1513 $\pm$ 0.0007. Galaxy E is redshifted to 7.1529 $\pm$ 0.0004; however, galaxy W is blueshifted to 7.1481 $\pm$ 0.0007. This implies that galaxy E and W present a velocity offset between the two components of 175 $\pm$ 28 km s$^{-1}$, compatible with that observed from \[O III\] 88 $\mu$m and \[C II\] 158 $\mu$m, 177 $\pm$ 16 km s$^{-1}$ ((cite: hashimoto_2019_big)).

The H$\alpha$ line is spectrally resolved with the MIRI-MRS. It presents an intrinsic FWHM of 407 $\pm$ 86 km s$^{-1}$ for galaxies E+W and 243 $\pm$ 41 km s$^{-1}$ and 312 $\pm$ 44 km s$^{-1}$, respectively, for E and W, after deconvolving with the line spread function of the MRS ((cite: Labiano+21)). Due to the offset in velocities the component of the E+W galaxies presents a higher FWHM than that of galaxies E and W. The observed H$\alpha$ fluxes are for E+W, E, and W: (23.1 $\pm$ 3.1) $\times\,10^{-18}$, (11.9 $\pm$ 1.3) $\times\,10^{-18}$, and (8.6 $\pm$ 1.2) $\times\,10^{-18}$ erg s$^{-1}$ cm$^{-2}$, respectively. All results are presented in Table [\[tab:results\]](#tab:results). The H$\alpha$ flux for galaxies E+W is in agreement within the uncertainties of the sum of the individual galaxy fluxes. This suggests that the H$\alpha$ emission is mainly dominated by the two galaxies excluding any relevant diffuse component.

## MIRIM and NIRCam photometry

MIRIM F560W photometry for galaxies E+W and for galaxies E and W is derived with the same apertures as for the H$\alpha$ spectra (see Fig. [1](#fig:all) and Sect. [3.1](#subsect:MIRI_NIRCAM_IMAGES_MAP)). The local background level for each aperture is estimated in an elliptical annulus centered at the same position as the E+W galaxies’ elliptical aperture and with an inner radius of 0.95 " and outer radius of 1.95 ". Additionally, we used 300 apertures on blank regions of the MIRI image with the same size as the galaxy apertures to estimate the flux uncertainties. We also performed the NIRCam photometry using the same aperture as for MIRIM F560W. To do so, we utilized the NIRCam images (F115W, F150W, F200W, F277W, F356W, F444W) that are homogenized to the MIRI F560W PSF. The final observed MIRIM F560W and NIRCam fluxes are presented in Table [\[tab:results\]](#tab:results). These NIRCam fluxes are lower by a factor of $\approx0.13$ than the ones obtained from previous results ((cite: sugahara_2024_rioja)) because of the PSF homogenization from NIRCam F444W to MIRI F560W (see Sect. [2.2](#subsect:nircam_2)) and the different aperture sizes.

Galaxy E is an unresolved source in the NIRCam F150W image with an estimated physical size of 63 pc (see Sect. [3.4](#subSect:reff) for details). The selected aperture mainly contains emission from galaxy E; thus, we implemented aperture correction in the NIRCam and MIRIM photometry using the MIRIM F560W PSF. This aperture correction has a value of 1/0.67. On the contrary, galaxy W is fully resolved in the NIRCam F150W, and for that reason we did not implement aperture correction to its photometry.

## Stellar structure and effective radius

We study the stellar structure of the two galaxies, E and W, individually. To achieve this, we utilized the F150W image, as it offers the best combination of signal-to-noise ratio (S/N) and spatial resolution. It presents the largest exposure time, 1675 s, arriving at a sensitivity of 7.7 nJy at 5 $\sigma$ depth, which is a factor of 2 – 3 better than any other NIRCam band. Also, the PSF FWHM is 0.067 ", allowing us to resolve structure up to 0.35 kpc at redshift 7.15 ((cite: sugahara_2024_rioja)). The F150W image traces the UV emission, which is dominated by the young and attenuated stellar population. We worked with native-resolution images (before PSF-matching and resampling), and the analysis was done using the GALFIT code ((cite: Peng+02)).

Galaxy E consists of a compact core, which appears unresolved, and a nondominant extended component. To obtain the effective radius of galaxy E, we modeled the F150W data in GALFIT with a Sérsic profile (with n=0.5, which gives a Gaussian profile) to fit the diffuse emission and a point-like component (using our ePSF) to fit the more compact part of the galaxy (Fig. [3](#fig:GALFIT_profiles)). The surface brightness of galaxy E is compatible with a nuclear, point-like source plus a diffuse emission component at radii larger than 0.05 ". However, as the core remains unresolved in the F150W image, we extend our analysis to the F115W image, in which the S/N is lower, but the spatial resolution is higher than in the F150W image. The core of galaxy E also remains unresolved in the F115W image; thus, we obtained an upper limit for the effective radius of 63 pc (0.012 ").

Galaxy W has a clumpy elongated morphology and is resolved in the F150W filter. It is well modeled by four different clumps. Three of them are unresolved point sources, which we modeled in GALFIT with point-like components. The other one is a more diffuse clump, associated with the brightest emission, modeled with point-like and Sérsic-profile (with an index n = 0.5) components (Fig. [3](#fig:GALFIT_profiles)). When considering galaxy W as a single entity and circularizing the profile, the intrinsic effective radius is 348 pc (0.057 ") after deconvolving with the NIRCam F150W PSF.

![](galaxy_galfit.png)

The merger nature of B14-65666 is supported by the morphological analysis using the `statmorph` code ((cite: rodriguez_gomez19)). We analyzed galaxies E and W separately and find that in both cases the shape asymmetry, A$_S$ – a reliable tracer of merging galaxies ((cite: rinaldi_24_LRD)) – is greater than 0.2, reinforcing the idea that each galaxy exhibits significant asymmetry. Specifically, we find A$_S$ of 0.35 and 0.80 for galaxies E and W, respectively. We also tested the multimode-intensity-deviation (MID) statistics, which are useful for detecting multicomponent systems, such as the double-nucleus of a late-stage merger, highly disordered post-merger remnants, galaxies with bright star-forming clumps in rest-UV emission, or an apparently single galaxy with an extended emission component(s) ((cite: freeman_2013_MID)). M (multimode statistics) quantifies how a galaxy’s light is distributed into distinct regions, and D (deviation statistic) measures the offset between the brightest region and the overall centroid. M values approaching 1 are likely to indicate a double nucleus, while values close to zero are interpreted as indicating a single source; D values close to zero indicate symmetric and ordered morphologies such as spheroids and disks. In the case of galaxy E, M $\approx$ 0.0 and D $\approx$ 0.1. This corroborates the interpretation that galaxy E is a single (compact spheroidal) source. In the case of galaxy W, M $\approx$ 0.4 and D $\approx$ 0.3, indicating that galaxy W is composed of at least two clumps, with one of them dominating the emission.

# Results and discussion

We detected and spatially resolved the rest-frame optical continuum and H$\alpha$ emission in the system B14-65666 at $z$ = 7.15 with MIRI imaging and spectroscopy. The new MIRI data are combined with ancillary NIRCam imaging and ALMA spectroscopy to obtain the physical properties of galaxies E and W, and of the entire system: star formation rate, instantaneous SFR, ionizing photon-production efficiency, H$\alpha$ equivalent width, dynamical mass, stellar-mass surface density, and SFR surface density.

![](Final_SED.png)

| Parameter | Galaxies E+W | Galaxy E | Galaxy W |  |
|:---|:--:|:--:|:--:|:--:|
| M$_{\star}$ \[$\times 10^{8}$ M$_{\odot}$$_{total}$ \]$^{(a)}$ | $28 \pm 16$ | $15 \pm9$ | $8 \pm4$ |  |
| M$_{dyn}$ \[$\times 10^{9}$ M$_{\odot}$$_{total}$ \]$^{*}$ | \- | $1.5 \pm0.3$ | $8.5 \pm2.4$ |  |
| Age$_{young}$ \[Myr\]$^{(a)}$ | $7\pm 3$ | $6 \pm3$ | $8\pm3$ |  |
| Age$_{main}$ \[Myr\]$^{(a)}$ | $214\pm150$ | $224\pm150$ | $158\pm155$ |  |
| Metallicity \[Z$_{\odot}$\]$^{(a)}$ | $0.25\pm  0.11$ | $0.24\pm 0.12$ | $0.31\pm 0.15$ |  |
| EW$_{0}$(H$\alpha$) \[$\AA$\]$^{*}$ | \- | $832 \pm 100$ | $536 \pm 78$ |  |
| EW$_{0}$(H$\alpha$) \[$\AA$\]$^{(a)}$ | $800 \pm 159$ | $880 \pm180$ | $833 \pm180$ |  |
| $L_{dust}$ \[$\times 10^{11}$ L$_{\odot}$\]$^{(a)}$ | $4.8\pm0.4$ | $2.6\pm0.5$ | $2.5\pm0.5$ |  |
| $L_{UV}$ \[$\times 10^{21}$ W$Hz^{-1}$\]$^{(a)}$ | $22.6\pm1.1$ | $11.8\pm0.7$ | $9.7\pm0.6$ |  |
| $A_{FUV}$\[mag\]$^{(a)}$ | $1.4\pm0.1$ | $1.5\pm0.2$ | $1.6\pm0.2$ |  |
| $A_{V}$ \[mag\] | \- | $1.5\pm0.4$ | $0.1 ^{+0.5}_{-0.1}$ |  |
| $\log(\zeta_\mathrm{ion}$ \[Hz erg$^{-1}$\])$^{*}$ | \- | $25.1\pm0.1$ | $25.5\pm0.1$ |  |
| SFR \[M$_{\odot}$yr$^{-1}$\]$^{(a)}$ | $127\pm66$ | $84\pm49$ | $50\pm12$ |  |
| SFR$_\mathrm{H_{\alpha},Z=Z_\odot}$ \[M$_{\odot}$ yr$^{-1}$\]$^{*}$ | \- | $76 \pm 8$ | $30 \pm 4$ |  |
| SFR $_\mathrm{H_{\alpha},Z=0.29Z_\odot}$ \[M$_{\odot}$ yr$^{-1}$\]$^{*}$ | \- | $46 \pm 5$ | $18 \pm 3$ |  |
| SFR$_\mathrm{[C\,II]158 {\mu m}}$ \[M$_{\odot}$ yr$^{-1}$\] | 140 $\pm$ 130 | 68 $\pm$ 64 | 53 $\pm$ 50 |  |
| SFR$_\mathrm{H_{\alpha}+TIR}$ \[M$_{\odot}$ yr$^{-1}$\]$^{*}$ | 107 $^{+35}_{-16}$ | 50 $^{+14}_{-9}$ | 54 $^{+27}_{-17}$ |  |
| SFR$_\mathrm{UV}$ \[M$_{\odot}$ yr$^{-1}$\]$^{*}$ | 72 $\pm$ 4 | 41 $\pm$ 3 | 37 $\pm$ 2 |  |
| SFR$_\mathrm{UV+TIR}$ \[M$_{\odot}$ yr$^{-1}$\]$^{*}$ | 147$^{+62}_{-22}$ | 66 $^{+24}_{-15}$ | 88 $^{+43}_{-19}$ |  |

Table notes: ($^{a}$) Obtained with SED fitting from CIGALE. ($^{*}$)The derived parameters are corrected for dust attenuation (see Sect. [4.2](#subSec:attenuation)).

## Spectral energy distribution and star formation history

We performed an SED fitting using `CIGALE` ((cite: noll_2009_analysis); (cite: boquien_2019_cigale)) for galaxies E+W as well as for the two individual components. The SED covers the 1 $\mu$m to 1.3 mm observed wavelength range, combining JWST photometric data (NIRCam and MIRIM) with ALMA continuum imaging ((cite: hashimoto_2019_big); (cite: sugahara_2021_big)), along with our H$\alpha$ and \[O III\] 88 $\mu$m ((cite: hashimoto_2019_big)) line fluxes. The redshift used in the analysis is the one derived spectroscopically from the H$\alpha$ line.

We made different assumptions to represent the star formation history of the system. The best results are determined from `CIGALE` fitting by minimizing the $\chi$$^{2}$ value and ensuring the best agreement with observed photometry and line fluxes. These are obtained when considering two components: an instantaneous burst with ages ranging from 30 to 500 Myr to model the mature stellar population; and a constant burst with ages lower than 10 Myr to model the young stellar population. We used the (cite: BruzualandCharlot+03) stellar population models and the (cite: Chabrier+03) initial mass function (IMF). The nebular continuum and emission lines were modeled using electron densities from 100 to 1000 cm$^{-3}$ and the ionization parameter (logU) ranging from -3.5 to -1.5. The metallicity was treated as a free parameter, ranging from 0.03 Z$_{\odot}$ to 0.7 Z$_{\odot}$, as previous studies showed that it varies in galaxies E and W ((cite: sugahara_2024_rioja); (cite: gareth_2024)). We used the dust attenuation law from (cite: Calzetti+00), and the dust emission was modeled using the (cite: Draine2014) models.

The best-fit models for galaxies E+W and for galaxies E and W separately are shown in Fig. [4](#fig:sed_cigale). These models reveal that B14-65666 is dominated by a young stellar burst characterized with a total SFR of 127 $\pm$ 66 M$_{\odot}\,$yr$^{-1}$ and a mass for the young stellar component of (8 $\pm$ 1) $\times$ 10$^{8}$ M$_{\odot}$. Galaxies E and W have SFRs of 84 $\pm$ 49 and 50 $\pm$ 12 M$_{\odot}\,$yr$^{-1}$, respectively, and show the same young stellar component with a stellar mass of (4 $\pm$ 1) $\times$ 10$^{8}$ M$_{\odot}$. The SED fitting results indicate the presence of a mature stellar population in B14-65666 with a stellar mass of around 0.5 $-$ 2 $\times$ 10$^{9}$ M$_{\odot}$ and average ages about 200 Myr. SED fitting results are presented in Table [\[tab:physical_parameters\]](#tab:physical_parameters). We conclude from the SED fitting that the B14-65666 system consists of two galaxies experiencing starbursts characterized by a similar age (see Sect. [4.9](#subSect:simulations) for a more detailed discussion). Also, despite the compactness of galaxy E (see Sect. [4.7](#subSect:mass-size)), the SED based on the NIRCam and MIRI imaging and covering the rest-frame 0.16 – 0.78 $\mu$m does not correspond to that of the average little red dots at redshifts $\sim$ 6 – 8 ((cite: perez_2024); (cite: kokorev_24); (cite: rinaldi_24_LRD)).

## Nebular and stellar attenuation

Dust attenuation plays a key role in shaping the observed properties of B14-65666, as revealed by MIRI, NIRCam, and ALMA observations. Combining the MRS H$\alpha$ and the NIRSpec H$\beta$ fluxes[^2], the H$\alpha$/H$\beta$ ratio gives observed values of 4.5$\,\pm$ 0.6 and 2.9 $\pm$ 0.4 for galaxies E and W, respectively. We note that these values correspond to the narrow component of the line emission for both galaxies as the broad component present on the H$\beta$ line ((cite: gareth_2024)) is not detected in H$\alpha$ with the present data (see Sect. [4.5](#subSect:kinematics)). Assuming a case B recombination, T$_{e}$ $\approx$ 1.5 $\times$ $10^{4}$ K and n$_{e}$ = $10^{3}$ cm$^{-3}$, the theoretical ratio is 2.8. Using (cite: Cardelli+89), we obtain that the nebular visual extinction ($A_{V}$) is $A_{V}$ = 1.5 $\pm$ 0.4 mag for galaxy E, and it is $A_{V}$ = $0.1 ^{+0.5}_{-0.1}$ mag for galaxy W. Thus the nebular attenuation is higher for galaxy E, in agreement, within the uncertainties, with the values of $A_{V}$ = 1.6 $\pm$ 0.3 mag for galaxy E and $A_{V}$ = 0.7 $^{+0.3}_{-0.2}$ mag for W from (cite: sugahara_2024_rioja) (obtained with SED fitting and applying the conversion factor to nebular attenuation, f = 0.44; (cite: calzetti97)).

We also calculated the dust attenuation in the FUV, $A_{FUV}$, with the IR-to-UV luminosity ratio (IRX = $L_{IR}$/$L_{UV}$), as this is a robust tracer of $A_{FUV}$. Taking the value of $log_{IRX}$ = 0.7 for the total galaxy ((cite: sugahara_2024_rioja)), we adopted expression (5) from (cite: meurer99) assuming the bolometric correction for the total light emitted by dust is 1, and for the total light emitted by stars, UV, is 1.68 ((cite: meurer99)). We obtain a value of $A_{FUV}$ = 1.50, which is compatible with that obtained with our SED fitting for galaxies E+W, $A_{FUV}$ = 1.41 $\pm\,0.09$ mag ((cite: Calzetti+00)).

## Star formation rate and burstiness

We derived the recent (i.e., less than 10 Myr) star formation rate directly from our H$\alpha$ measurements, assuming solar (to facilitate comparison with other star formation tracers at other wavelengths) and subsolar metallicity (0.29 Z$_{\odot}$, (cite: gareth_2024) and see Table [\[tab:physical_parameters\]](#tab:physical_parameters)). We applied the corresponding SFR-to-H$\alpha$ conversion factor for each metallicity, which is approximately 1.7 times lower in the subsolar case ((cite: Reddy+18)). The final SFR values are corrected for attenuation using the H$\alpha$/H$\beta$ ratios (see previous section). We obtain SFRs of $76\,\pm\,8$ ($46\,\pm\,5$) M$_{\odot}$ yr$^{-1}$ and $30\,\pm\,4$ ($18\,\pm\,3$) M$_{\odot}$ yr$^{-1}$ for galaxies E and W and solar (subsolar) metallicities, respectively.

Additional estimates of the SFR can be obtained directly from far-infrared emission lines or using a combination of multiwavelength tracers. The \[C II\] 158 $\mu m$ emission line is a tracer of SFR in low-redshift, star-forming, and composite SF+AGN galaxies ((cite: DeLooze+14)); it is confirmed for high-redshift galaxies ((cite: Schaerer+20); (cite: carninai_ferrara_2020)). Adopting the ancillary \[C II\] 158 $\mu$m luminosities derived from ALMA ((cite: hashimoto_2019_big)), values similar to those derived from our H$\alpha$ measurements are obtained, within the uncertainties (see Table [\[tab:physical_parameters\]](#tab:physical_parameters)). The large uncertainty in the value of the SFR derived from the \[C II\] 158 $\mu$m emission line is due to the nature of this emission, which could include extended or diffuse regions not directly linked to active star formation. Also, to trace less massive stars we used the SFR(UV) for solar metallicities and considering a constant SFH over 100 Myr ((cite: Calzetti+13)).

Other SFR estimates involve the use of hybrid indicators such as the UV+TIR (total infrared) luminosity ((cite: Kennicutt-Evans+12)), or H$\alpha$+TIR ((cite: catalntorrecilla_2015_star); (cite: Calzetti+13)), that capture both obscured and unobscured star formation over longer periods of time (up to 100 Myr). Assuming a simple energy balance ((cite: kennicutt_2009_dustcorrected)), and considering the far-UV luminosity derived from our SED fitting ($L(\text{UV})$ = (1.15 $\pm$ 0.11) $\times\,10^{11}$ $L_\odot$), and the TIR luminosity $L(TIR)$ = (1.05 $\pm$ 0.2) $\times\,10^{12}$ $L_\odot$ ((cite: hashimoto_2019_big)), we obtain an SFR consistent with our extinction-corrected H$\alpha$ estimates. The SFR derived from the H$\alpha$ and TIR luminosities are also in good agreement with those obtained from UV+TIR (see Table [\[tab:physical_parameters\]](#tab:physical_parameters)). The SFRs derived in this analysis (70 – 140 M$_{\odot}$ yr$^{-1}$) are lower than the SED-based SFR reported by (cite: sugahara_2024_rioja), SFR = 225 $^{+71}_{-56}$ M$_{\odot}$ yr$^{-1}$, and the (narrow+broad) H$\beta$-based SFR from (cite: gareth_2024), SFR$_{H\beta}$ = 308 $\pm$ 39 M$_{\odot}$ yr$^{-1}$. This difference is attributed to variations in aperture sizes where the contribution of the extended emission (H$\beta$) is significant, as well as other factors such as different estimates of the internal dust attenuation. Additionally, in the case of the H$\beta$-based SFR, the presence of both narrow and broad components in the H$\beta$ line emission also contributes to the higher SFR value by a factor of 2 ((cite: gareth_2024)).

A useful diagnostic for assessing the recent star formation in high-${\it z}$ galaxies is the ratio of the SFR(H$\alpha$)-to-SFR(UV), which is referred to as the burstiness parameter and probes star formation over the last 10 Myr relatively to the last 100 Myr. If the ratios are above 1, it indicates that the galaxy is in a bursty phase ((cite: Atek+23)). We obtain a value of the ratio SFR(H$\alpha$)-to-SFR(UV) for solar metallicities of 1.8 $\pm$ 0.1 and 0.8 $\pm$ 0.1 for galaxies E and W, respectively (we would expect similar values for subsolar metallicities). When compared to the range of burstiness ratios reported by (cite: Atek+23) (0.7 \< *z* \< 1.5), values above or close to unity are typical in low-mass galaxies (M$_{\star}$\<$10^{9}$ M$_{\odot}$) and below unity in high-mass galaxies (M$_{\star}$\>$10^{9}$ M$_{\odot}$). Thus, our values suggest that galaxy E shows signs of bursty activity, forming stars at nearly twice the average rate of the past 100 Myr; it is in a mild bursty phase, while galaxy W forms stars at a rate closer to that if this past 100 Myr; i.e., experiencing a more continuous burst. This aligns with the results from (cite: navarro-carrera24), whose authors analyzed $\sim4500$ H$\alpha$ emitters across $\textit{z}$ $\sim$ 2 – 6.5 using JADES data, observing a correlation between enhanced SFR(H$\alpha$)/SFR(UV) and EW$_0$(H$\alpha$), reinforcing the scenario where galaxies with above-unity SFR(H$\alpha$)/SFR(UV) experience a bursty phase in the last $\sim 50$ Myr.

![](log_Ion-EW.png)

## Equivalent width of H$\alpha$ and ionizing photon-production efficiency

To derive the rest-frame equivalent width of H$\alpha$ (EW$_0$(H$\alpha$)) for galaxies E+W and galaxies E and W, we make use of the F560W and H$\alpha$ fluxes measured in our MIRIM and the MRS observations, respectively. First, we obtain rest-frame optical continuum emission by subtracting the contribution of the H$\alpha$ line (Sect. [3.2](#subSect:halpha_spectra)) to the F560W flux (Sect. [3.3](#subSect:mirim_nircam_photom)). The EW$_0$(H$\alpha$) is then derived as the ratio of the H$\alpha$ to the continuum flux under the H$\alpha$ line. We obtain rest-frame equivalent widths of 832 $\pm$ 100 Å and 536 $\pm$ 78 Å for galaxies E and W, respectively. The difference in the EW$_0$(H$\alpha$) of the two galaxies is attributed to a different star formation history in the two galaxies with ionizing young stars and more mature, non-ionizing stellar populations contributing in different proportions to the continuum emission. According to our SED analysis, galaxy E, with a larger EW$_0$(H$\alpha$) value, has a slightly younger stellar population (6 Myr) relative to galaxy W (8 Myr).

The ionizing photon production efficiency, $\log(\zeta_\mathrm{ion}$), is the ratio of the ionizing to the non-ionizing UV flux. Assuming recombination, $\log(\zeta_\mathrm{ion}$) is empirically obtained as the ratio of the number of ionizing photons ($N_{LyC}$) derived from the H$\alpha$ line (after extinction correction) and the luminosity at 1500 Å. Assuming zero escape fraction, a dust attenuation as derived in Sect. [4.2](#subSec:attenuation), and a temperature of 1.5 $\times$ 10${^4}$ K ((cite: alvarez-marquez+23c)) the integrated H$\alpha$ luminosity provides a total number of ionizing photons ($N_{LyC}$) equal to $1.1\times10^{55}$ ph s$^{-1}$ and $4.1\times10^{54}$ ph s$^{-1}$ for galaxies E and W, respectively. Different approaches to dust correction can yield significantly different values of $\zeta_\mathrm{ion}$ introducing uncertainty in its determination and affecting the interpretation of its physical implications ((cite: matthee17)). Thus, correcting the UV and H$\alpha$ luminosities, we obtain ionizing photon-production efficiencies $\log(\zeta_\mathrm{ion}$) equal to $25.1\pm0.1$ and $25.5\pm0.1$ Hz erg$^{-1}$ for galaxies E and W, respectively. This difference in the $\zeta_\mathrm{ion}$ between the two galaxies of the system can be interpreted as partly due to the age difference in the young stellar populations in the two galaxies. Models indicate that in addition to the stellar continuum, there is a strong nebular contribution due to the two-photon continuum at 1500$\AA$. This contribution can be close to 50% of the total for very young populations (1 Myr), decreasing with age and becoming almost negligible for 10-Myr-old populations ((cite: katz_2024)). Thus, the impact of this nebular continuum would be to increase the 1500 $\AA$ luminosity and consequently decrease the corresponding $\log(\zeta_\mathrm{ion})$ by factors of 0.15 to 0.04 for ages of 1 to 8 Myr. In addition, residual differential extinction in the two galaxies could also play a role due to uncertainties in the derivation of the extinction in the UV.

We present the previous results in the $\log(\zeta_\mathrm{ion})$ – EW$_0$(H$\alpha$) plane (see Fig. [5](#fig:log_Ion-EW)). Additional samples of galaxies at redshifts 4 to 9 are also presented for comparison. These include Lyman-alpha emitters (LAE) at redshifts 3.8-6 ((cite: Maseda+20); (cite: Ning+23); (cite: Lam+19); (cite: harikane2018)), H$\alpha$ and \[O III\] emitters at redshifts 6.1 to 8 ((cite: sun_2023); (cite: Rinaldi+23)), and the mean of Lyman-break galaxies at redshift 8 ((cite: Stefanon+22)). Individual galaxies with resolved integral-field spectroscopy are also shown (RXCJ0600-2007 at $z$ = 6.07, (cite: gimenez-arteaga_2024) and MACS1149-JD1 at $z$ = 9.1, (cite: alvarez-marquez+23c)). While galaxies E and W forms stars at a rate much higher than the average galaxy at redshift 7, they have $\log(\zeta_\mathrm{ion})$ and EW$_0$(H$\alpha$) in the range of high-${\it z}$ galaxies. These values are consistent with the predicted values for young stellar populations. The Binary Population and Spectral Synthesis (BPASS; (cite: Eldridge+Stanway+20)) model demonstrates that the $\log(\zeta_\mathrm{ion}$) and the EW$_0$(H$\alpha$) of a single-aged, instantaneous-starburst binary population increases as the age of the population decreases (see Fig. [5](#fig:log_Ion-EW)), with values compatible with those observed for young populations with ages from 1 to 20 Myr. The production of ionizing photons also depends on the presence of massive stars and therefore the IMF ((cite: stanway_16)). Values for the logarithm of the photon production efficiency above 25.5 Hz erg$^{-1}$ can only be obtained with massive bursts, $10^{7}$ M$_{\odot}$ due to the stochasticity of the formation of massive stars ((cite: Stanway+Eldridge-23)). The galaxies in the B14-65666 system and the high-*z* galaxies identified with the JWST should have higher young stellar masses.

![](A_B_h_alpha.png)

![](halpha_hbeta_normalized_all.png)

## Kinematics of the ionized ISM

The kinematics of the ionized gas can be measured with the H$\alpha$ emission-line profile in our MRS data. Based on the integrated H$\alpha$ line, we measure a redshift of $z$ = 7.1513 $\pm$ 0.0007 for the B14-65666 system, compatible with the values obtained with the FIR emission lines \[O III\] 88 $\mu$m and \[C II\] 158 $\mu$m ($z$ = 7.1521 $\pm$ 0.0004, (cite: hashimoto_2019_big)) and optical \[O III\] line ($z$ = 7.1517 $\pm$ 0.0001, (cite: gareth_2024)). The two galaxies of the B14-65666 system have a relative velocity of 175 $\pm$ 28 km s$^{-1}$ along our line of sight as derived from the centroid of the H$\alpha$ line emission, showing it is a galaxy merger.

The kinematics of the ionized gas traced by H$\alpha$ appears to show differences between the two galaxies. Specifically, we find that the FWHM for galaxy W is higher than for galaxy E, with values of 312 $\pm$ 44 km s$^{-1}$ and 243 $\pm$ 41 km s$^{-1}$, respectively. These values agree within the uncertainties (from those measured) with the far-infrared emission lines, \[C II\] 158 $\mu$m and \[O III\] 88 $\mu$m. The \[C II\] 158 $\mu$m emission has similar kinematics in both galaxies (FWHM of 288 $\pm$ 41 km s$^{-1}$ for galaxy W and 276 $\pm$ 34 km s$^{-1}$ [^3] for galaxy E). For \[O III\] 88 $\mu$m, galaxy E shows a broader line (322 $\pm$ 41 km s$^{-1}$) than galaxy W (267 $\pm$ 42 km s$^{-1}$). In Fig. [6](#fig:oiii_cii_A_B), we present the comparison of these three lines for galaxies E+W and E and W. The observed differences in the two galaxies indicate the complex structure of the velocity field in the different phases of the ISM. While the H$\alpha$ line traces the overall kinematics of the ionized gas, the \[C II\] 158 $\mu$m line is closely associated with the neutral gas and the \[O III\] 88 $\mu$m with the high excitation gas. Simulations also show that different tracers are sensitive to different kinematic properties ((cite: kohandel)). In addition, the continuum imaging ((cite: sugahara_2024_rioja)) of both galaxies shows a different morphology; galaxy E as a very compact source, while galaxy W shows a more extended structure, in particular in the rest-UV light, reminiscent of tidal tails. Moreover, low-spectral-resolution (R $\approx$ 1000) integral-field spectroscopy with NIRSpec suggests the presence of a narrow and a broad kinematic component in both galaxies and in all optical emission lines tracing the ionized gas ((cite: gareth_2024)). These two components are potentially associated with the motions in the host galaxy (narrow) and the presence of high-velocity gas outflows (broad). The width of the narrow component is only 144 $\pm$ 11 km s$^{-1}$ for galaxy E and 227 $\pm$ 6 km s$^{-1}$ for galaxy W. These are significantly narrower than the values derived from our H$\alpha$ line and far-infrared emission lines, obtained with a better spectral resolution but lower S/N. We tested whether the observed H$\alpha$ line profile could be compatible with the combination of the narrow and broad (653 $\pm$ 10 km s$^{-1}$ for galaxy E and 755 $\pm$ 23 km s$^{-1}$ for galaxy W) line components identified with NIRSpec. Our tests (see Fig. [7](#fig:hbeta)) indicate that the narrow+broad (N+B) component could be slightly compatible with our observed H$\alpha$ line profiles. However, the simulated H$\alpha$ N+B line profile appears to have a flux excess in the spectral range of the line (i.e., residuals mostly below zero) for galaxy E, while the faint broad component in galaxy W is close in velocity to the peak emission in galaxy E. Since the two galaxies are separated by only 0.44 arcsec, this secondary emission in W could be due to a contamination from the brighter emission from E ((cite: gareth_2024)). Further higher spectral resolution data with NIRSpec, and higher S/N MRS spectra, would be required to confirm the presence of such a broad line emission in the two galaxies.

The consistency of the trends between our results and the ancillary data provides robust evidence of the dynamic differences between galaxies E and W. The broader profiles observed in galaxy W for both H$\alpha$ and \[C II\] 158 $\mu$m may indicate enhanced turbulence or kinematic effects, potentially driven by interactions or feedback processes, as well as a possibility of a connection with outflows. On the other hand, the higher FWHM in \[O III\] 88 $\mu$m for galaxy E suggests that highly ionized gas dynamics differ from those of lower ionization states, pointing to localized physical conditions or energetic phenomena. Also, dust attenuation could impact the interpretation, in particular in galaxy E where a large visual extinction is measured. The optical lines are more susceptible to dust extinction, which can affect measurements of line widths and kinematic features, whereas far-infrared lines are less impacted by such effects.

## Stellar and dynamical mass

Although the line profiles of the different emission lines suggest that the gas is not fully (dynamically) relaxed, here we obtain an upper limit of the dynamical mass of each of the galaxies assuming the system is close to relaxation and characterized by the random motions traced by the ionized gas velocity dispersion; i.e., not dominated by rotational motions. Under this working hypothesis, we followed previous works on similar systems such as the low-*z* luminous infrared galaxies (e.g., Eq. (1) in (cite: bellocchi2013)). The dynamical masses we derive are (1.5 $\pm$ 0.3) $\times$ $10^9$ $M_\odot$ and (8.5 $\pm$ 2.4) $\times$ $10^9$ $M_\odot$ for galaxies E and W, respectively, assuming velocity dispersions of 103 $\pm$ 17 km s$^{-1}$ and 132 $\pm$ 19 km s$^{-1}$ (obtained with the FWHM from our H$\alpha$ line), and the effective radii derived from our NIRCam images (see Sect. [3.4](#subSect:reff) for details). The total stellar masses are derived from the multiwavelength SED fitting and correspond to (15 $\pm$ 9) $\times$ $10^{8}$ M$_{\odot}$ and (8 $\pm$ 4) $\times$ 10$^{8}$ M$_{\odot}$ for galaxies E and W. Thus, while there is a good agreement between the stellar and dynamical masses for galaxy E, an order of magnitude difference appears for galaxy W. The difference in galaxy W could be due to the presence of a dominant molecular gas component in this galaxy amounting to close to 90% of the total mass. However, the stellar structure shows the presence of extended emission consisting of star-forming clumps along tidal tails ((cite: sugahara_2024_rioja)). This suggests that this galaxy is far from relaxed, and therefore the estimated dynamical mass is highly uncertain.

![](M_R_B14.png)

## Mass-size relation

The two galaxies of the B14-65666 system occupy a very different location in the stellar mass-size plane (see Fig. [8](#fig:mass-size)). Galaxy W, with an effective radius of 348 pc and a stellar mass of (8 $\pm$ 4) $\times$ 10$^8$ M$_{\odot}$, is consistent with the expected values according to the relations derived for high-redshift galaxies from the JADES program (redshifts 4 to 10; (cite: langeroodi_2023)) and from the CEERS, PRIMER-UDS, and PRIMER-COSMOS surveys (redshifts 3 to 9; (cite: allen2024galaxysizemassbuildup)). Therefore, galaxy W appears as an average galaxy at approximately redshift 7. On the other hand, the second component of the system, galaxy E, appears to be deviating from the standard relations, showing a very small and compact size (upper limit of 63 pc to the effective radius) for a stellar mass of 15 ($\pm$ 9) $\times$ 10$^8$ M$_{\odot}$. This translates into a high-stellar-mass surface density (6 $\times$ $10^{4}$ M$_{\odot}$ pc$^{-2}$ for E, versus 1 $\times\,10^{3}$ M$_{\odot}$ pc$^{-2}$ for W), close to the limit of the highest values ($10^{5.5}$ M$_{\odot}$ pc$^{-2}$) measured in the stellar clusters and nuclei of low-*z* galaxies ((cite: grudic_19)). Galaxies as compact as galaxy E and with similar stellar surface densities are not uncommon at high-$z$ ((cite: alvarez25)). Star-forming clumps and galaxies with an effective radius in the 30 to 200 pc range and a wide mass range (4 $\times$ 10$^7$ to 2 $\times$ 10$^{10}$ M$_{\odot}$) are already known at redshifts above 6 (see Fig. [8](#fig:mass-size); (cite: Claeyssens_2023); (cite: baggen23)). Thus, B14-65666 is identified as a system that consists of a pair of interacting galaxies, with similar stellar masses (within a factor of 2) but with one of the galaxies (E) being extremely compact and already showing stellar-mass surface densities close to those measured in the nuclei of galaxies at low redshifts. The galaxies of the B14-65666 system are much less massive ($\approx$ $\times$ 20 – 30) and far more compact ($\approx$ $\times$ 10 – 60) than the main-sequence and most luminous star-forming galaxies at low redshifts, with effective radii $\approx$ 3.5 kpc ((cite: leroy21)) and $\approx$ 2.2 kpc ((cite: bellocchi_2022)), respectively (see Fig. [8](#fig:mass-size)). Thus, galaxies E and W appear to be building up their stellar mass as they go through the advanced phases of the interaction/merging process.

![](SFR_M_B14.png)

## Starburst nature

The analysis of the SFR derived with the H$\alpha$-versus-stellar-mass plane reveals that both galaxies E and W are well above the main sequence (MS) of galaxies at redshift 7 ((cite: heintz+23)). Galaxies E and W of our system are situated between the region defined by (cite: Caputi+17) for H$\alpha$ emitters, the starburst (SB) region, and the MS (see Fig. [9](#fig:sfr-mass)). Such extremely compact starburst galaxies are expected to have short depletion times (\<100 Myr, see (cite: franco2020)), and therefore galaxy E may quickly quench out of gas exhaustion ­–at least temporarily– which is in line with a bursty/stochastic SFH.

We compared the position in the SFR stellar-mass plot with more galaxies at similar redshifts (Fig. [9](#fig:sfr-mass)). The sSFRs of E and W (51 and 38 Gyr$^{-1}$, respectively) are similar to those of low-mass galaxies, but also to some very massive ones, such as REBELS-25 (sSFR=25 Gyr$^{-1}$), a relaxed, dynamically cold disc galaxy at a similar redshift, $z$ = 7.31 ((cite: rowland24_rebels)). A recent large compilation of NIRSpec prism data and stacked spectra showed that the average galaxy becomes progressively more bursty with increasing redshift, as well as with increasing sSFR ((cite: langeroodi24)). Based on this, B14-65666 seems slightly less bursty (but consistent within error bars) than the average galaxy at similar redshift and sSFR. UV-faint galaxies at redshifts from 6 to 8 from the Cosmic Evolution Early Release Science (CEERS) JWST/NIRCam survey also show a bursty star formation history ((cite: endsley_2023)). Galaxies from the ALMA-ALPINE \[C II\] survey at redshifts 4 to 6 ((cite: fevre_2020); (cite: faisst_2020)) show normal star formation following the MS of galaxies at these redshifts ((cite: Speagle+14)). LIRGs at low redshifts, with typical stellar masses in the $10^{10}-10^{11}$ M${_\odot}$ and SFR 30 M${_\odot}$ yr$^{-1}$ range ((cite: bellocchi_2022)), are placed above the low-$z$ MS plane ((cite: elbaz_2011)) and indicate that at high redshifts LIRGs are less massive but more compact.

## B14-65666: A merger of starburst galaxies in the early Universe

The picture that emerges from our analysis is that B14-65666 is a system of two galaxies in the process of interacting and merging. We identified one of the components (E) as an extremely compact source, characterized by a stellar-mass surface density close to that of the nuclei of low-*z* galaxies. On the other hand, the second component of the system (galaxy W) shows a more elongated structure with four fainter clumps ((cite: sugahara_2024_rioja)), reminiscent of star-forming regions along the tidal tails produced in gas-rich interacting galaxies. A significant velocity offset of 175 km s$^{-1}$ between the two galaxies supports the merger scenario. Furthermore, the estimated stellar masses for each component are on the order of $\sim$ $10^9$ M$_\odot$, which is three-to-four orders of magnitude higher than typical stellar masses of star-forming clumps in galactic disks ($10^5$ – $10^6$ M$_\odot$, (cite: Adamo+24); (cite: mowla24)), reinforcing the interpretation that we are observing two galaxy-scale systems. The stellar-mass ratio between the components is $\sim$ 2:1, which is potentially consistent with a major merger. Additionally, we find differences in metallicity between the two components, with values derived using the SED-fitting of 0.24 Z$_\odot$ for E and 0.31 Z$_\odot$ for W; this is in agreement with line diagnostics from NIRSpec IFS ((cite: gareth_2024)). Collectively, the presence of tidal features, velocity offset, distinct stellar populations and metallicities, and the high stellar masses all provide compelling evidence that B14-65666 is an example of a merging system of two galaxies. In addition, galaxies E and W are experiencing a bursty phase with an SFR well above that of the main-sequence star-forming galaxies of the same mass at those redshifts.

Recent simulations of the formation of galaxies during the EoR ((cite: nazakoto_2024) and references therein) show that systems identified as clumpy –i.e., with two or more high-surface-density star-forming clumps as traced by emission lines– represent 10$\%$ of all simulated sources. Moreover, most of the clumpy systems are produced by mergers, with the young stellar populations forming along the gas-rich tidal tails, and with specific SFR of the order of 50 Gyr$^{-1}$. However, these clumpy systems appear to be temporal and short-lived, merging into a single galaxy in about 50 Myr ((cite: hashimoto23_A2744)). Under this scenario, the compact, and highly dense, galaxy E could already be a protobulge produced by the merger of previous clumps, while galaxy W would be in the process of merging of smaller and less massive clumps before the two main components, E and W, merge together in a single, more massive galaxy at a later time; i.e., at lower redshifts (see Figure 5 in (cite: nazakoto_2024)).

B14-65666 is not a unique system at those redshifts. Recent JWST observations show merging systems of star-forming galaxies such as the interacting system SPT0311-58, which resides in the core of an extremely massive protocluster at $z$ = 6.9 ((cite: arribas_24_spt)); the source A2744-z7p9OD, the most distant protocluster at $z$ = 7.88 ((cite: hashimoto23_A2744)); or the JWST’s Quintet, a merger of at least five galaxies containing over 17 clumps, at $z$ = 6.7 ((cite: hu2025circumgalacticenrichmentmultigalaxymerger)). The detection with the JWST and further studies of new systems such as these will allow us to understand the formation process of massive galaxies in the early Universe.

# Conclusions and summary

We present mid-infrared imaging and spectroscopy of the $z$ = 7.15 Lyman-break galaxy B14-65666 taken with MIRI/JWST. The data provide the first detection of the H$\alpha$ emission line of this source, a system of two merging galaxies at the EoR. The study also combines the new MIRI data with NIRCam data ((cite: sugahara_2024_rioja)) and archival high-angular-resolution ALMA imaging ((cite: Hashimoto+18)) to derive additional physical properties. The main results are summarized below.

The H$\alpha$-emitting gas shows a structure dominated by two spatially resolved sources (E and W) separated by a projected distance of 0.4 arcsec (i.e., 2.2 kpc) and relative velocity of 175 km s$^{-1}$. The rest-frame UV light shows galaxy E as a very compact, unresolved source (upper limit for the effective radius of 63 pc), while galaxy W is more extended (348 pc) with the presence of fainter sources along an elongated structure.

The SFR derived from the H$\alpha$ luminosity is 76 and 30 M$_{\odot}$ yr$^{-1}$ (for solar metallicity as reference), for galaxies E and W, respectively. Other measurements of the SFR using hybrid tracers; H$\alpha$ and the luminosity TIR; and the UV-plus-TIR luminosities give values of 50 and 54 M$_{\odot}$ yr$^{-1}$ and 66 and 88 M$_{\odot}$ yr$^{-1}$ for galaxies E and W, respectively. These values are compatible within the uncertainties with the SFR derived from H$\alpha$. The ratio of H$\alpha$-to-UV-based SFR (burstiness) indicates that while galaxy E is in a mild bursty phase (ratio of 1.8), galaxy W is experiencing a more continuous burst (ratio of 0.8).

The equivalent width of the H$\alpha$ line (832 ± 100 and 536 ± 78 $\AA$ for galaxies E and W, respectively) and the ionizing photon production efficiency ($\log(\zeta_\mathrm{ion})$ = 25.1 ± 0.1 Hz erg$^{-1}$ and $\log(\zeta_\mathrm{ion})$ = 25.5 ± 0.1 Hz erg$^{-1}$) in the two galaxies are within the range of values measured in other samples of galaxies at these redshifts. Their different locations in the production efficiency $-$ equivalent width plane, with galaxy W above and galaxy E below the relation for high-$z$ galaxies is interpreted as being due to slightly different ages in their young stellar populations.

The specific star formation rate (40 – 50 Gyr$^{-1}$) indicates that the two galaxies involved in the B14-65666 system are experiencing an intense starburst phase, well above the typical values for galaxies of similar masses at those redshifts and similar to less massive ($\times$ 10) galaxies.

The stellar-mass surface density of galaxy E is extreme ($>$ 6 $\times$ $10^{4}$ M$_{\odot}$ pc$^{-2}$) and close to the value measured in the nuclei of low-$z$ galaxies, while galaxy W has a surface density ($10^{3}$ M$_{\odot}$ pc$^{-2}$) similar to that of a high-$z$ galaxy.

The H$\alpha$ emission-line profile shows a different gas kinematics, with galaxy W showing larger velocities (i.e., broader line) than galaxy E. The ionized gas kinematics traced by the H$\alpha$ line shows differences with respect to the neutral and highly ionized gas traced by the far-infrared \[C II\] 158 $\mu$m and \[O III\] 88 $\mu$m lines, respectively. This indicates a complex structure in the ISM, likely due to the internal substructure of the young and mature stellar populations and dust distribution in these galaxies on (sub)kiloparsec scales.

In summary, B14-65666 is a system consisting of two galaxies that are experiencing an extreme starburst phase due to the interaction/merging process. One of the galaxies (E) is already very compact and massive, with a stellar density close to that of the mature nucleus/bulge of low$-z$ galaxies, while the other one (W) is consistent with a more extended star formation, distributed in a few fainter clumps along a tidal tail. These results agree with recent cosmological simulations of clumpy merging systems in the early Universe ((cite: nazakoto_2024)). According to these simulations, this clumpy phase identified in B14-65666 is short-lived, with the bursty clumps merging on a short timescale (50 Myr) and forming a massive, single-nucleus galaxy at later times. Detailed studies of systems similar to B14-65666 will help our understanding of the physical conditions and mechanisms involved in the formation process of massive galaxies and their evolution in the early Universe, just a few hundred Myr after the Big Bang and during the EoR.

# Acknowledgements

We thank Michele Perna and Gareth Jones for discussions on B14-65666. CPJ, JAM, LC acknowledge support by grant PIB2021-127718NB-100 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe”. ACG acknowledges support by JWST contract B0215/JWST-GO-02926. AB, JM and GÖ acknowledge support from the Swedish National Space Administration (SNSA). KIC acknowledges funding from the Dutch Research Council (NWO) through the award of the Vici Grant VI.C.212.036 and funding from the Netherlands Research School for Astronomy (NOVA). AAH acknowledges support from from grant PID2021-124665NB-I00 funded by the Spanish Ministry of Science and Innovation and the State Agency of Research MCIN/AEI/10.13039/501100011033 and ERDF A way of making Europe. This work was supported by research grants (VIL16599,VIL54489) from VILLUM FONDEN. JPP and TVT acknowledge financial support from the UK Science and Technology Facilities Council, and the UK Space Agency. The project that gave rise to these results received the support of a fellowship from the “la Caixa” Foundation (ID 100010434). The fellowship code is LCF/BQ/PR24/12050015. PGPG and LC acknowledge support from grant PID2022-139567NB-I00 funded by Spanish Ministerio de Ciencia e Innovación MCIN/AEI/10.13039/501100011033, FEDER *Una manera de hacer Europa*. EI acknowledges funding from the Netherlands Research School for Astronomy (NOVA). IJ acknowledge support from the Carlsberg Foundation (grant no CF20-0534) and the Cosmic Dawn Center is funded by the Danish National Research Foundation under grant No. 140. SG acknowledges financial support from the Villum Young Investigator grant 37440 and 13160 and the Cosmic Dawn Center (DAWN), funded by the Danish National Research Foundation under grant DNRF140. AE and FP acknowledge support through the German Space Agency DLR 50OS1501 and DLR 50OS2001 from 2015 to 2023.

The work presented is the effort of the entire MIRI team and the enthusiasm within the MIRI partnership is a significant factor in its success. MIRI draws on the scientific and technical expertise of the following organisations: Ames Research Center, USA; Airbus Defence and Space, UK; CEA-Irfu, Saclay, France; Centre Spatial de Liége, Belgium; Consejo Superior de Investigaciones Científicas, Spain; Carl Zeiss Optronics, Germany; Chalmers University of Technology, Sweden; Danish Space Research Institute, Denmark; Dublin Institute for Advanced Studies, Ireland; European Space Agency, Netherlands; ETCA, Belgium; ETH Zurich, Switzerland; Goddard Space Flight Center, USA; Institute d’Astrophysique Spatiale, France; Instituto Nacional de Técnica Aeroespacial, Spain; Institute for Astronomy, Edinburgh, UK; Jet Propulsion Laboratory, USA; Laboratoire d’Astrophysique de Marseille (LAM), France; Leiden University, Netherlands; Lockheed Advanced Technology Center (USA); NOVA Opt-IR group at Dwingeloo, Netherlands; Northrop Grumman, USA; Max-Planck Institut für Astronomie (MPIA), Heidelberg, Germany; Laboratoire d’Etudes Spatiales et d’Instrumentation en Astrophysique (LESIA), France; Paul Scherrer Institut, Switzerland; Raytheon Vision Systems, USA; RUAG Aerospace, Switzerland; Rutherford Appleton Laboratory (RAL Space), UK; Space Telescope Science Institute, USA; Toegepast- Natuurwetenschappelijk Onderzoek (TNO-TPD), Netherlands; UK Astronomy Technology Centre, UK; University College London, UK; University of Amsterdam, Netherlands; University of Arizona, USA; University of Cardiff, UK; University of Cologne, Germany; University of Ghent; University of Groningen, Netherlands; University of Leicester, UK; University of Leuven, Belgium; University of Stockholm, Sweden; Utah State University, USA. A portion of this work was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with the National Aeronautics and Space Administration. We would like to thank the following National and International Funding Agencies for their support of the MIRI development: NASA; ESA; Belgian Science Policy Office; Centre Nationale D’Etudes Spatiales (CNES); Danish National Space Centre; Deutsches Zentrum fur Luft-und Raumfahrt (DLR); Enterprise Ireland; Ministerio De Economía y Competitividad; Netherlands Research School for Astronomy (NOVA); Netherlands Organisation for Scientific Research (NWO); Science and Technology Facilities Council; Swiss Space Office; Swedish National Space Board; UK Space Agency.

For the purpose of open access, the authors have applied a Creative Commons Attribution (CC BY) licence to the Author Accepted Manuscript version arising from this submission.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy (AURA), Inc., under NASA contract NAS 5-03127 for *JWST*; and from the [European *JWST* archive (e*JWST*)](https://jwst.esac.esa.int/archive/) operated by the ESDC.

This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

This research made use of Photutils, an Astropy package for detection and photometry of astronomical sources (cite: larry_bradley_2022_6825092).

117 natexlab

(ref: Adamo+24) Adamo, A., Bradley, L. D., Vanzella, E., et al. 2024, Nature, 632, 513

(ref: allen2024galaxysizemassbuildup) Allen, N., Oesch, P. A., Toft, S., et al. 2025, A&A, 698, A30

(ref: alvarez-marquez+23c) Álvarez-Márquez, J., Colina, L., Crespo Gómez, A., et al. 2024, A&A, 686, A85

(ref: alvarez25) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2025, A&A, 695, A250

(ref: Alvarez-Marquez+23-SPT) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671, A105

(ref: Argyriou+23) Argyriou, I., Glasse, A., Law, D. R., et al. 2023, A&A, 675, A111

(ref: arribas_24_spt) Arribas, S., Perna, M., Rodrı́guez Del Pino, B., et al. 2024, A&A, 688, A146

(ref: Atek+23) Atek, H., Labbé, I., Furtak, L. J., et al. 2024, Nature, 626, 975

(ref: baggen23) Baggen, J. F. W., van Dokkum, P., Labbé, I., et al. 2023, ApJL, 955, L12

(ref: barton_2000) Barton, E. J., Geller, M. J., & Kenyon, S. J. 2000, ApJ, 530, 660

(ref: bellocchi2013) Bellocchi, E., Arribas, S., Colina, L., & Miralles-Caballero, D. 2013, A&A, 557, A59

(ref: bellocchi_2022) Bellocchi, E., Pereira-Santaella, M., Colina, L., et al. 2022, A&A, 664, A60

(ref: boquien_2019_cigale) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, Astronomy & Astrophysics, 622, A103

(ref: Bouchet+15) Bouchet, P., Garcı́a-Marı́n, M., Lagage, P. O., et al. 2015, PASP, 127, 612

(ref: bowler_2014_the) Bowler, A., Dunlop, J., McLure, R., et al. 2014, Monthly Notices of the Royal Astronomical Society, 440, 2810

(ref: bowler_2018_obscured) Bowler, R. A. A., Bourne, N., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2018, Monthly Notices of the Royal Astronomical Society, 481, 1631

(ref: bowler_2012) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., et al. 2012, Monthly Notices of the Royal Astronomical Society, 426, 2772

(ref: bowler_2017_unveiling) Bowler, R. A. A., Dunlop, J. S., McLure, R. J., & McLeod, D. J. 2017, MNRAS, 466, 3612

(ref: boyett24) Boyett, K., Bunker, A. J., Curtis-Lake, E., et al. 2024, MNRAS, 535, 1796

(ref: larry_bradley_2022_6825092) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2022, astropy/photutils: 1.5.0

(ref: BruzualandCharlot+03) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: bushouse_pipeline) Bushouse, H., Eisenhamer, J., Dencheva, N., et al. 2024, JWST Calibration Pipeline

(ref: Bushouse_2002) Bushouse, H. A., Borne, K. D., Colina, L., et al. 2002, The Astrophysical Journal Supplement Series, 138, 1

(ref: calzetti97) Calzetti, D. 1997, in American Institute of Physics Conference Series, Vol. 408, The ultraviolet universe at low and High redshift, ed. W. H. Waller (AIP), 403–412

(ref: Calzetti+13) Calzetti, D. 2013, in Secular Evolution of Galaxies, ed. J. Falcón-Barroso & J. H. Knapen, 419

(ref: Calzetti+00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Caputi+17) Caputi, K. I., Deshmukh, S., Ashby, M. L. N., et al. 2017, ApJ, 849, 45

(ref: Cardelli+89) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245

(ref: carninai_ferrara_2020) Carniani, S., Ferrara, A., Maiolino, R., et al. 2020, MNRAS, 499, 5136

(ref: catalntorrecilla_2015_star) Catalán-Torrecilla, C., Gil de Paz, A., Castillo-Morales, A., et al. 2015, A&A, 584, A87

(ref: Ceverino_17) Ceverino, D., Glover, S. C. O., & Klessen, R. S. 2017, MNRAS, 470, 2791

(ref: Chabrier+03) Chabrier, G. 2003, PASP, 115, 763

(ref: Claeyssens_2023) Claeyssens, A., Adamo, A., Richard, J., et al. 2023, MNRAS, 520, 2180

(ref: conselice_2003) Conselice, C. J., Bershady, M. A., Dickinson, M., & Papovich, C. 2003, AJ, 126, 1183

(ref: DeLooze+14) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: dicken_2024_miri) Dicken, D., Marı́n, M. G., Shivaei, I., et al. 2024, A&A, 689, A5

(ref: Draine2014) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172

(ref: duan_2024_mergers) Duan, Q., Conselice, C. J., Li, Q., et al. 2025, MNRAS

(ref: duan_2024) Duan, Q., Li, Q., Conselice, C. J., et al. 2024, arXiv e-prints, arXiv:2411.04944

(ref: elbaz_2011) Elbaz, D., Dickinson, M., Hwang, H. S., et al. 2011, A&A, 533, A119

(ref: Eldridge+Stanway+20) Eldridge, J. J. & Stanway, E. R. 2020, arXiv e-prints, arXiv:2005.11883

(ref: endsley_2023) Endsley, R., Stark, D. P., Whitler, L., et al. 2023, MNRAS, 524, 2312

(ref: faisst_2020) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: franco2020) Franco, M., Elbaz, D., Zhou, L., et al. 2020, A&A, 643, A30

(ref: freeman_2013_MID) Freeman, P. E., Izbicki, R., Lee, A. B., et al. 2013, Monthly Notices of the Royal Astronomical Society, 434, 282

(ref: furusawa_2016_a) Furusawa, H., Kashikawa, N., Kobayashi, M. A. R., et al. 2016, The Astrophysical Journal, 822, 46

(ref: GaiaCollaboration+22) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Gardner+23) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001

(ref: gimenez-arteaga_2024) Giménez-Arteaga, C., Fujimoto, S., Valentino, F., et al. 2024, A&A, 686, A63

(ref: grudic_19) Grudić, M. Y., Hopkins, P. F., Quataert, E., & Murray, N. 2019, MNRAS, 483, 5548

(ref: harikane2018) Harikane, Y., Ouchi, M., Shibuya, T., et al. 2018, ApJ, 859, 84

(ref: harshan_2024) Harshan, A., Tripodi, R., Martis, N. S., et al. 2024, ApJL, 977, L36

(ref: hashimoto23_A2744) Hashimoto, T., Álvarez-Márquez, J., Fudamoto, Y., et al. 2023, ApJL, 955, L2

(ref: hashimoto_2019_big) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, Publications of the Astronomical Society of Japan, 71

(ref: hashimoto_2023_big) Hashimoto, T., Inoue, A. K., Sugahara, Y., et al. 2023, The Astrophysical Journal, 952, 48

(ref: Hashimoto+18) Hashimoto, T., Laporte, N., Mawatari, K., et al. 2018, Nature, 557, 392

(ref: heintz+23) Heintz, K. E., Brammer, G. B., Giménez-Arteaga, C., et al. 2023, Nature Astronomy, 7, 1517

(ref: hu_papovich_2025) Hu, W., Papovich, C., Shen, L., et al. 2025, arXiv e-prints, arXiv:2503.04032

(ref: hu2025circumgalacticenrichmentmultigalaxymerger) Hu, W., Papovich, C., Shen, L., et al. 2025, Circumgalactic Enrichment by a Multi-Galaxy Merger at Redshift 6.7

(ref: gareth_2024) Jones, G. C., Bowler, R., Bunker, A. J., et al. 2024, arXiv e-prints, arXiv:2412.15027

(ref: Jones+23) Jones, O. C., Álvarez-Márquez, J., Sloan, G. C., et al. 2023, MNRAS, 523, 2519

(ref: katz_2024) Katz, H., Cameron, A. J., Saxena, A., et al. 2024, arXiv e-prints, arXiv:2408.03189

(ref: Kennicutt-Evans+12) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: kennicutt_2009_dustcorrected) Kennicutt, R. C., Hao, C.-N., Calzetti, D., et al. 2009, The Astrophysical Journal, 703, 1672

(ref: kohandel) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2024, A&A, 685, A72

(ref: kokorev_24) Kokorev, V., Caputi, K. I., Greene, J. E., et al. 2024, ApJ, 968, 38

(ref: Labiano+21) Labiano, A., Argyriou, I., Álvarez-Márquez, J., et al. 2021, A&A, 656, A57

(ref: Lam+19) Lam, D., Bouwens, R. J., Labbé, I., et al. 2019, A&A, 627, A164

(ref: langeroodi_2023) Langeroodi, D. & Hjorth, J. 2023, arXiv e-prints, arXiv:2307.06336

(ref: langeroodi24) Langeroodi, D. & Hjorth, J. 2024, arXiv e-prints, arXiv:2404.13045

(ref: Law+23) Law, D. D., Morrison, J. E., Argyriou, I., et al. 2023, AJ, 166, 45

(ref: fevre_2020) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: leroy21) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43

(ref: libralato_2024_highprecision) Libralato, M., Argyriou, I., Dicken, D., et al. 2024, Publications of the Astronomical Society of the Pacific, 136, 034502

(ref: Maseda+20) Maseda, M. V., Bacon, R., Lam, D., et al. 2020, MNRAS, 493, 5120

(ref: matthee17) Matthee, J., Sobral, D., Best, P., et al. 2017, MNRAS, 465, 3637

(ref: meurer99) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: mihos_1996) Mihos, J. C. & Hernquist, L. 1996, ApJ, 464, 641

(ref: mowla24) Mowla, L., Iyer, K., Asada, Y., et al. 2024, Nature, 636, 332

(ref: naidu_2025) Naidu, R. P., Oesch, P. A., Brammer, G., et al. 2025, arXiv e-prints, arXiv:2505.11263

(ref: nazakoto_2024) Nakazato, Y., Ceverino, D., & Yoshida, N. 2024, ApJ, 975, 238

(ref: nardiello_2022) Nardiello, D., Bedin, L. R., Burgasser, A., et al. 2022, MNRAS, 517, 484

(ref: navarro-carrera24) Navarro-Carrera, R., Rinaldi, P., Caputi, K. I., et al. 2024, arXiv e-prints, arXiv:2410.23249

(ref: Ning+23) Ning, Y., Cai, Z., Jiang, L., et al. 2023, ApJL, 944, L1

(ref: noll_2009_analysis) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, Astronomy & Astrophysics, 507, 1793

(ref: goran_ostlin_2024_midis) Östlin, G., Pérez-González, P. G., Melinder, J., et al. 2025, A&A, 696, A57

(ref: Peng+02) Peng, C. Y., Ho, L. C., Impey, C. D., & Rix, H.-W. 2002, AJ, 124, 266

(ref: pablo_perezgonzalez_2024_LRD) Pérez-González, P. G., Barro, G., Rieke, G. H., et al. 2024a, ApJ, 968, 4

(ref: perez_2024) Pérez-González, P. G., Barro, G., Rieke, G. H., et al. 2024b, ApJ, 968, 4

(ref: perez-gonzalez_24_jekyll_hyde) Pérez-González, P. G., D‘Eugenio, F., Rodrı́guez del Pino, B., et al. 2024c, arXiv e-prints, arXiv:2405.03744

(ref: perezgonzalez2025risegalacticempireluminosity) Pérez-González, P. G., Östlin, G., Costantin, L., et al. 2025, arXiv e-prints, arXiv:2503.15594

(ref: PlanckCollaboration18VI) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Prieto-Lyon+23) Prieto-Lyon, G., Strait, V., Mason, C. A., et al. 2023, A&A, 672, A186

(ref: puskas25) Puskás, D., Tacchella, S., Simmonds, C., et al. 2025, MNRAS, 540, 2146

(ref: Reddy+18) Reddy, N. A., Shapley, A. E., Sanders, R. L., et al. 2018, ApJ, 869, 92

(ref: Rieke+15) Rieke, G. H., Wright, G. S., Böker, T., et al. 2015, PASP, 127, 584

(ref: Rieke_2023) Rieke, M. J., Kelly, D. M., Misselt, K., et al. 2023, Publications of the Astronomical Society of the Pacific, 135, 028001

(ref: rinaldi_24_LRD) Rinaldi, P., Bonaventura, N., Rieke, G. H., et al. 2024a, arXiv e-prints, arXiv:2411.14383

(ref: Rinaldi+23) Rinaldi, P., Caputi, K. I., Costantin, L., et al. 2023, ApJ, 952, 143

(ref: rinaldi_24_halpha_emitters) Rinaldi, P., Caputi, K. I., Iani, E., et al. 2024b, ApJ, 969, 12

(ref: rinaldi2024emergencestarformationmain) Rinaldi, P., Navarro-Carrera, R., Caputi, K. I., et al. 2025, ApJ, 981, 161

(ref: rodriguez_gomez19) Rodriguez-Gomez, V., Snyder, G. F., Lotz, J. M., et al. 2019, MNRAS, 483, 4140

(ref: rowland24_rebels) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, MNRAS, 535, 2068

(ref: Schaerer+20) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3

(ref: Speagle+14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Spilker+22) Spilker, J. S., Hayward, C. C., Marrone, D. P., et al. 2022, ApJL, 929, L3

(ref: spilker_2023_spatial) Spilker, J. S., Phadke, K. A., Aravena, M., et al. 2023, Nature, 618, 708

(ref: Stanway+Eldridge-23) Stanway, E. R. & Eldridge, J. J. 2023, MNRAS, 522, 4430

(ref: stanway_16) Stanway, E. R., Eldridge, J. J., & Becker, G. D. 2016, MNRAS, 456, 485

(ref: Stefanon+22) Stefanon, M., Bouwens, R. J., Illingworth, G. D., et al. 2022, ApJ, 935, 94

(ref: sugahara_2024_rioja) Sugahara, Y., Álvarez-Márquez, J., Hashimoto, T., et al. 2025, ApJ, 981, 135

(ref: sugahara_2021_big) Sugahara, Y., Inoue, A. K., Hashimoto, T., et al. 2021, The Astrophysical Journal, 923, 5

(ref: sun_2023) Sun, F., Egami, E., Pirzkal, N., et al. 2023, ApJ, 953, 53

(ref: toomre72) Toomre, A. & Toomre, J. 1972, ApJ, 178, 623

(ref: Wells+15) Wells, M., Pel, J. W., Glasse, A., et al. 2015, PASP, 127, 646

(ref: Wright+23) Wright, G. S., Rieke, G. H., Glasse, A., et al. 2023, PASP, 135, 048003

(ref: Wright+15) Wright, G. S., Wright, D., Goodson, G. B., et al. 2015, PASP, 127, 595

[^1]: <https://www.stsci.edu/~jayander/JWST1PASS/LIB/PSFs/STDPSFs/>.

[^2]: We implemented aperture corrections (AC = 1/0.79) using the NIRSpec IFS PSF to match the fluxes presented in (cite: gareth_2024) to the larger aperture of our MRS measurements.

[^3]: The FWHM value for clump E has been recalculated and differs from that reported in (cite: hashimoto_2019_big), as confirmed through a private communication with the authors.

</paper>

Write the methods card for this paper.