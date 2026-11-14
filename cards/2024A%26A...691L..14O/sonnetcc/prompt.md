# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691L..14O\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...691L..14O",
 "title": "Contemporaneous high-angular-resolution imaging of the AGB star W Hya in vibrationally excited H<SUB>2</SUB>O lines and visible polarized light with ALMA and VLT/SPHERE-ZIMPOL",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Ohnaka, K.",
 "n_authors": 4,
 "arxiv_id": "2411.09759",
 "doi": "10.1051/0004-6361/202451977",
 "alma_projects_linked_by_archive": [
  "2018.1.01239.S"
 ]
}
```

Paper text:
<paper>
# Contemporaneous high-angular-resolution imaging of the AGB star W Hya in vibrationally excited H$_2$O lines and visible polarized light with ALMA and VLT/SPHERE-ZIMPOL

We present contemporaneous high-angular-resolution millimeter imaging and visible polarimetric imaging of the nearby asymptotic giant branch (AGB) star W Hya to better understand the dynamics and dust formation within a few stellar radii.

The star W Hya was observed in two vibrationally excited H$_2$O lines at 268 and 251 GHz with Atacama Large Millimeter/submillimeter Array (ALMA) at a spatial resolution of 16$\times$20 mas and at 748 and 820 nm at a resolution of 26$\times$27 mas with the Very Large Telescope (VLT)/Spectro-Polarimetric High-contrast Exoplanet REsearch (SPHERE)-Zurich Imaging Polarimeter (ZIMPOL).

ALMA’s high spatial resolution allowed us to image strong emission of the vibrationally excited H$_2$O line at 268 GHz ($\varv_2$ = 2, $J_{K_a,K_c}$ = $6_{5,2}$–$7_{4,3}$) over the stellar surface instead of absorption against the continuum, which is expected for thermal excitation. Strong, spotty emission was also detected along and just outside the stellar disk limb at an angular distance of $\sim$40 mas ($\sim$1.9 $R_{\star}$), extending to $\sim$60 mas ($\sim$2.9 $R_{\star}$).

Another H$_2$O line ($\varv_2$ = 2, $J_{K_a,K_c}$ = $9_{2,8}$–$8_{3,5}$) at 251 GHz with a similar upper-level energy was tentatively identified, which shows absorption over the stellar surface. This suggests that the emission over the surface seen in the 268 GHz H$_2$O line is suprathermal or even maser emission. The estimated gas temperature and H$_2$O density are consistent with the radiatively pumped masers.

The 268 GHz H$_2$O line reveals global infall at up to $\sim$15 km s$^{-1}$ within 2–3 $R_{\star}$, but outflows at up to $\sim$8 km s$^{-1}$ are also present.

The polarized intensity maps obtained in the visible reveal clumpy dust clouds forming within $\sim$40 mas ($\sim$1.9 $R_{\star}$) with a particularly prominent cloud in the SW quadrant and a weaker cloud in the east. The 268 GHz H$_2$O emission overlaps very well with the visible polarized intensity maps, which suggests that both the nonthermal and likely maser H$_2$O emission and the dust originate from dense, cool pockets in the inhomogeneous atmosphere within $\sim$2–3 $R_{\star}$.

# Introduction

Mass loss on the asymptotic giant branch (AGB) plays an important role not only in stellar evolution but also in the chemical evolution of galaxies. The initial–final mass relation of low- and intermediate-mass stars shows that stars can lose up to $\sim$80% of their initial mass before they evolve to white dwarfs (Cummings et al. (cite: cummings18)). Despite such importance, the mass-loss mechanism in AGB stars is not yet fully understood. According to the pulsation-enhanced dust-driven outflow scenario, large-amplitude stellar pulsation levitates the material, which leads to density enhancement at the cool, upper atmosphere, where dust can form, and the radiation pressure on the dust grains can drive the mass loss (Höfner & Olofsson (cite: hoefner18)). The recent 3D models of AGB stars show that convection can also levitate the material, which leads to clumpy stellar winds (Freytag & Höfner (cite: freytag23)).

To clarify the long-standing problem of the AGB mass loss, it is indispensable to probe the region within $\sim$10 $R_{\star}$, where dust forms and the wind accelerates.

The oxygen-rich AGB star W Hya has been studied with various observational techniques from the visible to the infrared to the radio (e.g., Zhao-Geisler et al. (cite: zhao-geisler11); Khouri et al. (cite: khouri15) and references therein) because of its proximity ($98^{+30}_{-18}$ pc, Vlemmings et al. (cite: vlemmings03)). The light curve shows clear periodicity (Woodruff et al. (cite: woodruff08)) with a period of 389 days (Uttenthaler et al. (cite: uttenthaler11)). Woodruff et al. ((cite: woodruff09)) show that the minimum near-infrared uniform-disk (UD) diameter of W Hya at phase 0.58 (near minimum light) is $\sim$36 mas at 1.2–1.3 $\mu$m. This is considered to correspond to the star’s angular diameter as seen in the deepest photospheric layers. We converted the UD diameter to the fully darkened disk diameter by multiplying it by the factor 1.15 derived by Zhao-Geisler et al. ((cite: zhao-geisler11)). This resulted in a stellar angular diameter of 41.4 mas (i.e., 20.7 mas as the star’s angular radius $R_{\star}$).

Taking advantage of visible polarimetric imaging with the Spectro-Polarimetric High-contrast Exoplanet REsearch (SPHERE)-Zurich Imaging Polarimeter (ZIMPOL) instrument (Beuzit et al. (cite: beuzit08); Schmid et al. (cite: schmid18)) at the Very Large Telescope (VLT), Ohnaka et al. ((cite: ohnaka16)) spatially resolved the clumpy dust clouds forming around W Hya at an angular distance of $\sim$50 mas ($\sim$2.4 $R_{\star}$), which is similar to the angular distance derived by Norris et al. ((cite: norris12)) based on polarimetric aperture-masking experiments. The modeling of Norris et al. ((cite: norris12)) and Ohnaka et al. ((cite: ohnaka16)) suggests a predominance of large (0.3–0.5 $\mu$m), transparent grains of Al$_2$O$_3$, Mg$_2$SiO$_4$, or MgSiO$_3$ in the clumpy clouds, lending support to the scenario of scattering-driven mass loss (Höfner (cite: hoefner08)).

Furthermore, the second-epoch

ZIMPOL observations by Ohnaka et al. ((cite: ohnaka17)) revealed the morphological change in the dust clouds as well as a change in the grain size from 0.4–0.5 $\mu$m to $\sim$0.1 $\mu$m. Similar clumpy dust cloud formation has been imaged in other nearby AGB stars, R Dor, IK Tau, and $o$ Cet (Khouri et al. (cite: khouri16), (cite: khouri18); Adam & Ohnaka (cite: adam19)).

Using the Atacama Large Millimeter/submillimeter Array (ALMA), Takigawa et al. ((cite: takigawa17)) imaged W Hya in the gas-phase AlO line at 344 GHz at an epoch between two ZIMPOL observations of Ohnaka et al. ((cite: ohnaka16), (cite: ohnaka17)). Takigawa et al. ((cite: takigawa17)) found that the distribution of AlO is in excellent agreement with the clumpy dust clouds seen in the polarized intensity maps. In this Letter, we present contemporaneous high-angular-resolution imaging of W Hya in two vibrationally excited H$_2$O lines with ALMA and visible polarimetric imaging with VLT/SPHERE-ZIMPOL.

# Observations and data reduction

We observed W Hya with ALMA on 2019 June 8 (UTC) using the C43-10 configuration (Program ID: 2018.1.01239.S, P.I.: K. Ohnaka), when the variability phase of W Hya was 0.53 at minimum light. The shortest and longest baselines were 83.1 m and 16.2 km, respectively. The largest recoverable scale is 190 mas.

We observed in nine spectral windows between 250.7 and 268.2 GHz. Two vibrationally excited H$_2$O lines reported in this Letter are located in the spectral windows centered at 250.727199 and 268.168335 GHz with bandwidths of 468.75 and 937.50 MHz observed at velocity resolutions of 1.17 and 1.09 km s$^{-1}$, respectively.

The ALMA data were reduced with the Common Astronomy Software Applications (CASA version 5.6.1-8; The CASA Team (cite: casa22)), following standard calibration procedures with the ALMA pipeline. We also self-calibrated the data with the continuum of W Hya. The image reconstruction was carried out with the task tclean with a robust parameter of 0.5. In total, we identified nearly 60 molecular lines, which include H$_2$O, $^{29}$SiO, $^{30}$SiO, Si$^{17}$O, OH, SO$_{2}$, $^{34}$SO$_{2}$, SO$^{18}$O, AlO, AlOH, TiO, $^{49}$TiO, $^{50}$TiO, TiO$_{2}$, SO, and HCN. The complete results will be presented in a forthcoming paper (Ohnaka et al., in prep). The images of the H$_2$O lines at 251 and 268 GHz were obtained with a restoring beam of 21$\times$18 mas and 20$\times$17 mas, respectively. The root mean square (RMS) noise is estimated to be 0.56 mJy/beam in both spectral windows.

We also used archival polarimetric imaging data of W Hya taken at 748 and 820 nm on 2019 May 30 (UTC), just nine days before our ALMA observations, using VLT/SPHERE-ZIMPOL as part of the program 0103.D-0168 (P.I.: T. Khouri). The spatial resolution estimated from the 2D Gaussian fit to the point spread function (PSF) reference star is 26$\times$27 mas. The observations and data reduction are described in Appendix [8](#appendix_zimpol).

# Vibrationally excited H$_2$O line at 268 GHz ($\varv_2 = 2$, $6_{5,2}$ – $7_{4,3}$) 

Figure [4](#cont_image) shows the continuum image obtained in the 268.2 GHz spectral window. Fitting the continuum image with a uniform elliptical disk results in a major and minor axis of $59.1 \pm 0.3$ mas and $57.7 \pm 0.2$ mas ($\sim$1.4 times larger than our adopted stellar angular diameter, which was also obtained near minimum light), with the position angle of the major axis being 16 $\pm$ 23$^\circ$. The uniform elliptical disk fitting also results in an intensity of $36.87 \pm 0.10$ mJy/beam. This corresponds to a brightness temperature ($T_{\rm b}$) of $2210 \pm 6$ K. We do not find a hot spot as found in the 338 GHz continuum by Vlemmings et al. ((cite: vlemmings17)).

Figure [1](#channelmap_h2o_268) shows the continuum-subtracted channel maps of the vibrationally excited H$_2$O line ($\varv_2$ = 2, 6$_{5,2}$–7$_{4,3}$, $E_u$ = 6039.00 K) at 268.149117 GHz. We adopted a systemic velocity ($V_{\rm sys}$) of 40.4 km s$^{-1}$ in the local standard of rest (LSR) derived by Khouri et al. ((cite: khouri14)).

The relative velocity with respect to the systemic velocity ($V_{\rm rel}$ = $\mbox{$V_{\rm LSR}$} - \mbox{$V_{\rm sys}$}$) is also given in each panel. The continuum-subtracted channel maps reveal that absorption is seen over the stellar disk at $V_{\rm rel}$ = $-6$ to $0$ km s$^{-1}$, which is expected because of the absorption due to the cooler gas in front of the stellar disk. However, the continuum-subtracted images from $V_{\rm rel}$ $\approx \! -3.0$ to $\sim$7.5 km s$^{-1}$ show noticeable emission over the stellar disk, indicating excess emission on top of the continuum. In addition, prominent, spotty emission is seen along and just outside the limb of the stellar disk at an angular distance of $\sim$40 mas ($\sim$1.9 $R_{\star}$), extending to $\sim$60 mas ($\sim$2.9 $R_{\star}$). The strongest emission is seen in the east-southeast at a radius of $\sim$50 mas (1.9 $R_{\star}$) at $V_{\rm rel}$ = $-1.5$ km s$^{-1}$ with an intensity of $\sim$80 mJy/beam ($T_{\rm b}$ = 4130 K). This is approximately twice as strong as the continuum intensity (already subtracted in the images shown in the figure) over the stellar disk, despite the high energy level of the line.

We extracted spatially resolved spectra of the H$_2$O line at four positions over the stellar disk and on four salient emission spots away from the limb of the stellar disk, as labeled in Fig. [5](#whya_h2o_268_combined)a. The spectra obtained over the stellar disk (Figs. [5](#whya_h2o_268_combined)b–e) show that the emission peak is redshifted by 3–5 km s$^{-1}$. However, the emission is broad, with the red wing extending to $\mbox{$V_{\rm rel}$} \approx 15$ km s$^{-1}$ (position 2) and the blue wing extending down to $-$8 km s$^{-1}$ (position 3). This suggests that the bulk of the material in front of the star within $\sim$60 mas is infalling with strong turbulent motion and/or that the H$_2$O emission originates from layers with different velocities (both infall and outflow) due to pulsation or convection with the major contribution coming from the layers infalling at 3–5 km s$^{-1}$. Wong et al. ((cite: wong16)) also found the presence of both infall and outflow in $o$ Cet observed with ALMA near minimum light. We discuss the dynamics seen in our ALMA data in Sect. [7](#sect_concl).

The spectra extracted off the limb of the stellar disk (Figs. [5](#whya_h2o_268_combined)f–i) show that the emission from positions 7 and 8 is as broad as that obtained at positions 3 and 4. Although the emission at positions 5 and 6 is much narrower, the spectrum at position 5 shows broad emission ranging from $V_{\rm rel}$ = $-$8 to 8 km s$^{-1}$, and the red wing at position 6 is broader than the blue wing.

# Vibrationally excited H$_2$O line at 251 GHz ($\varv_2 = 2$, $9_{2,8}$ – $8_{3,5}$)

We also identified – albeit tentatively – another vibrationally excited H$_2$O line ($\varv_2$ = 2, $9_{2,8}$–$8_{3,5}$, $E_u$ = 6141.05 K) at a rest frequency of 250.756830 GHz (Furtenbacher et al. (cite: furtenbacher20b)). The uncertainty in the rest frequency of this H$_2$O line will be discussed in greater detail in a forthcoming paper.

Figure [2](#channelmap_h2o_250) shows the channel maps obtained for this H$_2$O line (images at $\mbox{$V_{\rm rel}$} \! >$3.0 km s$^{-1}$ are not shown, because they are affected by the blend due to the adjacent Si$^{17}$O line at 250.744695 GHz). While this H$_2$O line at 251 GHz and that at 268 GHz (Sect. [3](#sect_res_h2o_268)) are both in the $\varv_2=2$ state with similar upper-level energies (6141 and 6039 K, respectively), the 251 GHz H$_2$O line predominantly shows absorption over the stellar disk, which is in marked contrast to the prominent emission seen in the 268 GHz line across many velocity channels. The spatially resolved spectra of the 251 GHz H$_2$O line show blueshifted absorption over the stellar disk (Fig. [5](#whya_h2o_268_combined), left column, blue lines), with the deepest absorption blueshifted by 3–4 km s$^{-1}$ at positions 1 and 2 (Figs. [5](#whya_h2o_268_combined)b and c).

In the red supergiant (RSG) VY CMa, Tenenbaum et al. ((cite: tenenbaum10)) reported an unidentified line at rest frequencies from $\sim$250.712 to 250.765 GHz, which is likely a blend of the lines of $^{30}$SiO ($\varv$ = 2, $J$ = 6 – 5, 250.727751 GHz), Si$^{17}$O ($\varv=0$, $J$ = 6 – 5, 250.744695 GHz), and H$_2$O ($\varv_2$ = 2, $9_{2,8}$–$8_{3,5}$). Richards et al. ((cite: richards24)) detected the 251 GHz H$_2$O line toward VY CMa and concluded that the line is quasi-thermal. Our observation of the (tentatively) identified 251 GHz H$_2$O line seen in absorption over the stellar surface suggests that this is also the case for W Hya.

# Nonthermal origin of the 268 GHz H$_2$O line

Both the 251 and 268 GHz $\varv_2$ = 2 H$_2$O lines have similar upper-level energies of $\sim$6040–6140 K. Nevertheless, the former line is only seen in absorption. Therefore, the excess emission in the 268 GHz line is unlikely caused by hot gas in front of the star, and the net emission over the stellar disk in the continuum-subtracted images of the 268 GHz H$_2$O line indicates suprathermal ($T_{\rm ex} > T_{\rm kin}$) or even maser emission ($T_{\rm ex} < 0$), where $T_{\rm ex}$ and $T_{\rm kin}$ denote the excitation temperature and kinetic temperature, respectively.

Until recently there were few detections of this vibrationally excited ($\varv_2$ = 2) H$_2$O line in AGB stars and RSGs reported in the literature. Tenenbaum et al. ((cite: tenenbaum10)) detected a remarkably strong maser in this line toward the RSG VY CMa. Weak emission in this line was also reported in the AGB stars IK Tau (Velilla Prieto et al. (cite: velilla_prieto17)) and R Dor (De Beck & Olofsson (cite: debeck18)), and the RSG NML Cyg (Singh et al. (cite: singh22)). Recently, Baudry et al. ((cite: baudry23)) reported the widespread presence of this H$_2$O line in 15 out of 17 AGB stars and RSGs observed with ALMA, many of which show signs of maser action.

Figure [\[maser_model\]](#maser_model) shows the negative optical depth (maser depth) of the 268 GHz H$_2$O line as a function of the gas temperature (kinetic temperature $T_{\rm kin}$) and the ortho-H$_2$O number density at three dust temperatures (M. Gray, priv. comm.) based on the models of Gray et al. ((cite: gray16)) and similar to Fig. 17 of Baudry et al. ((cite: baudry23)). We note a change of the maser pumping regime with increasing dust temperature. With the presence of cool dust ($T_{\rm d} \ensuremath{\lesssim} 600$ K), the 268 GHz H$_2$O maser is predominantly collisionally pumped, and it requires both a rather high gas temperature of $\ensuremath{\gtrsim}$1500 K and an H$_2$O density of $\ensuremath{\gtrsim} 10^6$ cm$^{-3}$. With hot dust ($T_{\rm d} \ensuremath{\gtrsim} 900$ K), maser action can occur at a lower gas temperature ($\ensuremath{\lesssim}\,$900 K) and H$_2$O density. The pulsation+dust-driven models of Bladh et al. ((cite: bladh19)) show that the density and gas temperature at 2–3 $R_{\star}$ are $10^{-14}$–$10^{-15}$ g cm$^{-3}$ and 700–1500 K, respectively. These mass densities correspond to H$_2$ number densities of $1.5 \times 10^{8}$–$1.5 \times 10^{9}$ cm$^{-3}$, which translates into H$_2$O densities of $8 \times 10^{4}$–$8 \times 10^{5}$ cm$^{-3}$ with an ortho-H$_2$O abundance of $6 \times 10^{-4}$ (Khouri et al. (cite: khouri14b)). This is consistent with the radiative pumping regime if the dust temperature is $\ensuremath{\gtrsim}\,$900 K, which is indeed the case as presented below.

Therefore, the excess emission of the 268 GHz H$_2$O line over the stellar disk can be due to maser amplification. We note that Vlemmings et al. ((cite: vlemmings21)) detected emission of the CO $\varv=1$ $J$ = 3 – 2 line over the surface of W Hya, which they interpreted as masers.

# Comparison between the 268 GHz H$_2$O $\varv_2 = 2$ emission and dust distribution

If the 268 GHz H$_2$O emission is due to maser action in the radiative pumping regime, it traces cool, dense regions, which also provide conditions favorable for dust to form. To examine whether there is a correlation between the H$_2$O emission and dust formation, we compared the 268 GHz H$_2$O emission image with the visible polarimetric imaging data obtained with VLT/SPHERE-ZIMPOL.

We registered the SPHERE images to the ALMA image as follows. Instead of taking the offset intensity peak position, we fitted the SPHERE images with a uniform elliptical disk (Fig. [3](#zimpol_h2o_masers)c, color map). The central position of the fitted elliptical disk was registered to the center of the ALMA continuum image, which was also determined by the uniform elliptical disk fitting described in Sect. [3](#sect_res_h2o_268).

Figure [3](#zimpol_h2o_masers)a (color map) shows the polarized intensity map obtained at 820 nm at a spatial resolution comparable to our ALMA images. The polarized intensity represents the radiation scattered off dust grains, and in an optically thin case, a polarized intensity map reflects the spatial distribution of the dust grains. Figure [3](#zimpol_h2o_masers)a reveals clumpy dust clouds forming at a radius of $\sim$40 mas ($\sim$1.9 $R_{\star}$). The map of the degree of polarization (Fig. [3](#zimpol_h2o_masers)b, color map) shows clumpy dust structures extending up to $\sim$150 mas. Three regions with enhanced polarization of 10–12% are seen in the north-northwest (NNW), east, and south. In both panels, the integrated intensity of the 268 GHz H$_2$O line near the systemic velocity is shown with the contours.

Comparison between the polarized intensity map and the 268 GHz H$_2$O emission reveals noticeable correlation. The strong H$_2$O emission in the south overlaps very well with the large dust cloud showing high polarized intensity. The H$_2$O emission spots in the east and NNW also coincide with the dust clouds. The overall shape of the H$_2$O emission with the NNW extension can also be recognized in the polarized intensity map.

The previous analyses of the clumpy dust clouds forming close to the star in W Hya show a dust temperature of $\sim$1500 K (Ohnaka et al. (cite: ohnaka16), (cite: ohnaka17)). This fulfills the high dust temperature condition necessary for the radiatively pumped 268 GHz H$_2$O maser. Therefore, the agreement between the H$_2$O emission and the polarization maps is consistent with the scenario that the H$_2$O emission is of a maser origin.

The total intensity map obtained with ZIMPOL is presented in Fig. [3](#zimpol_h2o_masers)c. The aforementioned uniform elliptical disk fit results in major and minor axes of 60.6$\pm$0.3 mas and 54.3$\pm$0.3 mas, respectively, and a position angle of the major axis of 24$\pm$4$^\circ$. This size in the visible is comparable to the millimeter continuum size. The intensity peak is offset to the northwest (NW) by $\sim$7 mas ($\sim$0.3 $R_{\star}$) from the stellar disk center.

The overlaid 268 GHz continuum image (contours) also shows a slight offset of the intensity peak of $\sim$7 mas to the NW, although the intensity contrast is much weaker. It is possible that the asymmetry in the ZIMPOL and ALMA data originates from the same inhomogeneity in the atmosphere. For completeness, a comparison of the H$_2$O emission with the ZIMPOL data obtained at 748 nm is presented in Appendix [12](#appendix_zimpol748), which is very similar to Fig. [3](#zimpol_h2o_masers).

# Discussion and conclusion

We detected unexpectedly strong nonthermal emission of the 268 GHz H$_2$O line covering nearly the entire surface of the AGB star W Hya, in marked contrast to the thermal absorption seen in the (tentatively identified) 251 GHz H$_2$O line.

The H$_2$O gas in front of the star shows infall at up to 15 km s$^{-1}$ and outflow at up to $\sim$8 km s$^{-1}$ within $\sim$2–3 $R_{\star}$, with the major contribution to the emission originating from the material infalling at 3–5 km s$^{-1}$.

If the H$_2$O line emission traces dense, cool pockets as indicated by the maser models, and the grains and gas are kinematically coupled, the observed spatial correlation between dust and H$_2$O indicates that the dust clouds are predominantly infalling but with some contribution from outflowing material.

The dynamics within 2–3 $R_{\star}$ predicted by the 1D dynamical models (Höfner et al. (cite: hoefner16), (cite: hoefner22)) is dominated by the expanding and infalling layers generated by stellar pulsation with velocities of up to $15$ km s$^{-1}$ (infall) and $\sim$10 km s$^{-1}$ (outflow). The latest 3D models (Freytag & Höfner (cite: freytag23)) show that dust forms and grows in large clumps, some of which are accelerated to $\sim$25 km s$^{-1}$. However, they also show that there are dust grains that do not grow to the size sufficient for outward acceleration and that fall back to the star at up to $\sim$25 km s$^{-1}$. The infall and outflow velocities observed in the 268 GHz H$_2$O line are in broad agreement with these theoretical models. Furthermore, Liljegren et al. ((cite: liljegren17), Fig. 5) show that dust grains start to form in infalling material, and they are not immediately accelerated outward. This is qualitatively consistent with our findings (assuming the kinematical coupling of dust and gas).

Radiative transfer modeling of the ZIMPOL data will allow us to constrain the grain size, which in turn will help us estimate the radiation pressure on the grains. Also, the grains that started to form in the infalling material are expected to be small, which can be tested by the grain size derived from the modeling.

This work is based on observations made with the Atacama Large Millimeter/submillimeter Array (Program ID: 2018.1.01239.S) and observations collected at the European Southern Observatory under ESO programme 0103.D-0168(B). K.O. acknowledges the support of the Agencia Nacional de Investigación Científica y Desarrollo (ANID) through the FONDECYT Regular grant 1240301. K.T.W. acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (Grant agreement no. 883867, project EXWINGS). We thank M. D. Gray for kindly providing us with the results of his maser models.

This research made use of the SIMBAD database, operated at the CDS, Strasbourg, France.

(ref: adam19) Adam, C, & Ohnaka, K. 2019, A&A, 628, A132

(ref: bladh19) Bladh, S., Liljegren, S., Höfner, S., Aringer, B., & Marigo, P. 2019, A&A, 626, A100

(ref: baudry23) Baudry, A., Wong, K. T., Etoka, S., et al. 2023, A&A, 674, A125

(ref: beuzit08) Beuzit, J.-L., Feldt, M., Dohlen, K., et al. 2008, SPIE Proc. 7014, 18

(ref: cummings18) Cummmings, J. D., Kalirai, J. S., Tremblay, P.-E., Ramirez-Ruiz, E., & Choi, J. 2018, ApJ, 866, 21

(ref: debeck18) De Beck, E., & Olofsson, H. 2018, A&A, 615, A8

(ref: freytag23) Freytag, B., & Höfner, S. 2023, A&A, 669, A155

(ref: furtenbacher20b) Furtenbacher, T., Tóbiás, R., Tennyson, J., et al. 2020, Journal of Physical and Chemical Reference Data, 49, 043103

(ref: gray16) Gray, M. D., Baudry, A., Richards, A. M. S., et al. 2016, MNRAS, 456, 374

(ref: hoefner08) Höfner, S. 2008, A&A, 491, L1

(ref: hoefner18) Höfner, S., & Olofsson, H. 2018, A&ARv, 26, 1

(ref: hoefner16) Höfner, S., Bladh, S., Aringer, B., & Ahuja, R. 2016, A&A, 594, A108

(ref: hoefner22) Höfner, S., Bladh, S., Aringer, B., & Eriksson, K. 2022, A&A, 657, A109

(ref: khouri14) Khouri, T., de Koter, A., Decin, L., et al. 2014, A&A, 561, A5

(ref: khouri14b) Khouri, T., de Koter, A., Decin, L., et al. 2014, A&A, 570, A67

(ref: khouri15) Khouri, T., Waters, L. B. F. M., de Koter, A., et al. 2015, A&A, 577, A114

(ref: khouri16) Khouri, T., Maercker, M., Waters, L. B. F. M., et al. 2016, A&A, 591, A70

(ref: khouri18) Khouri, T., Vlemmings, W. H. T., Olofsson, H., et al. 2018, A&A, 620, A75

(ref: liljegren17) Liljegren, S., Höfner, S., Eriksson, K., & Nowotny, W. 2017, A&A, 606, A6

(ref: lopez22) Lopez, B., Lagarde, S., Petrov, R. G., et al. 2022, A&A, 659, A192

(ref: maercker08) Maercker, M., Schöier, F. L., Olofsson, H., Bergman, P., & Ramstedt, S. 2008, A&A, 479, 779

(ref: norris12) Norris, B., Tuthill, P. G., Ireland, M. J., et al. 2012, Nature, 484, 220

(ref: ohnaka16) Ohnaka, K., Weigelt, G., & Hofmann, K.-H. 2016, A&A, 589, A91

(ref: ohnaka17) Ohnaka, K., Weigelt, G., & Hofmann, K.-H. 2017, A&A, 597, A20

(ref: richards24) Richards, A. M. S., Asaki, Y., Baudry, A., et al. 2024, Cosmic Masers: Proper Motion Toward the Next-Generation Large Projects, Proc. IAU Symposium, 380, 389

(ref: schmid18) Schmid, H. M., Bazzon, A., Roelfsema, R., et al. 2018, A&A, 619, A9

(ref: singh22) Singh, A. P., Edwards, J. L., & Ziurys, L. M. 2022, AJ, 164, 230

(ref: takigawa17) Takigawa, A., Kamizuka, T., Tachibana, S., & Yamamura, I. 2017, Sci. Adv., 3, eaao2149

(ref: tenenbaum10) Tenenbaum, E. D., Dodd, J. L., Milam, S. N., Woolf, N. J., & Ziurys, L. M. 2010, ApJL, 720, L102

(ref: casa22) The CASA Team, et al. 2022, PASP, 134, 114501

(ref: uttenthaler11) Uttenthaler, S., Van Stiphout, K., Voet, K., et al. 2011, A&A, 531, A88

(ref: velilla_prieto17) Velilla Prieto, L., Sánchez Contreras, C., Cernicharo, J., et al. 2017, A&A, 597, A25

(ref: vlemmings03) Vlemmings, W. H. T., van Langevelde, H. J., Diamond, P. J., Habing, H. J., & Schilizzi, R. T. 2003, A&A, 407, 213

(ref: vlemmings17) Vlemmings, W., Khouri, T., O’Gorman, E., et al. 2017, Nat. Ast., 1, 848

(ref: vlemmings21) Vlemmings, W., Khouri, T., & Tafoya, D. 2021, A&A, 654, A18

(ref: wong16) Wong, K. T., Kamiński, T., Menten, K. M., & Wyrowski, F., 2016, A&A, 590, A127

(ref: woodruff08) Woodruff, H. C., Tuthill, P. G., Monnier, J. D., et al. 2008, ApJ, 673, 418

(ref: woodruff09) Woodruff, H. C., Ireland, M. J., Tuthill, P. G., et al. 2009, ApJ, 691, 1328

(ref: zhao-geisler11) Zhao-Geisler, R., Quirrenbach, A., Köhler, R., Lopez, B., & Leinert, C. 2011, A&A, 530, A120

# SPHERE-ZIMPOL observations of W Hya

The archival SPHERE-ZIMPOL data used in our present work were taken on 2019 May 30 (UTC) with the filters Cnt820 (central wavelength $\lambda_c$ = 817.3 nm and full width at half maximum (FWHM) $\Delta \lambda$ = 19.8 nm) and Cnt748 ($\lambda_c$ = 747.4 nm and $\Delta \lambda$ = 20.6 nm). The star HD118877 was observed as a reference for the PSF. A summary of the ZIMPOL observations is given in Table. [1](#obslog_zimpol).

We reduced the SPHERE-ZIMPOL data using the pipeline version 0.40.0 in the same manner as described in our previous studies (Ohnaka et al. (cite: ohnaka16), (cite: ohnaka17); Adam & Ohnaka (cite: adam19)) and obtained the maps of total (i.e., polarized + unpolarized) intensity, polarized intensity, and the degree of linear polarization.

The Strehl ratios of the data of W Hya at the observed wavelengths were estimated from the $H$-band Strehl ratio recorded in the auxiliary files (GEN-SPARTA data) of the SPHERE observations by applying the Maréchal approximation (Adam & Ohnaka (cite: adam19)). The Strehl ratios of the data of the PSF reference HD118877 were directly measured from the observed total intensity maps. The derived Strehl ratios of the observations of W Hya and HD118877 are $\sim$0.5 and $\sim$0.3, respectively, in the visible. The 2D Gaussian fit to the total intensity maps of the PSF reference HD118877 resulted in PSF FWHMs of 26 $\times$ 27 mas.

= 3pt

+:----------+:-------------:+:-------+:-------+:------+:-------+:----------+
| Object    | $t_{\rm obs}$ | Filter | Seeing | AM    | Strehl | Strehl    |
+-----------+---------------+--------+--------+-------+--------+-----------+
|           | (UTC)         | (cam1) | ($''$) |       | ($H$)  | (Cnt820)  |
+-----------+---------------+--------+--------+-------+--------+-----------+
|           |               | (cam2) |        |       |        | (Cnt748)  |
+-----------+---------------+--------+--------+-------+--------+-----------+
| 2019 May 30 (UTC)                                                        |
+-----------+---------------+--------+--------+-------+--------+-----------+
| W Hya     | 01:05:13      | Cnt820 | 0.72   | 1.0   | 0.85   | 0.51      |
+-----------+---------------+--------+--------+-------+--------+-----------+
|           |               | Cnt748 |        |       |        | 0.48      |
+-----------+---------------+--------+--------+-------+--------+-----------+
| HD118877  | 01:47:41      | Cnt820 | 0.74   | 1.0   | 0.68   | 0.32      |
+-----------+---------------+--------+--------+-------+--------+-----------+
|           |               | Cnt748 |        |       |        | 0.26      |
+-----------+---------------+--------+--------+-------+--------+-----------+
|           |               |        |        |       |        |           |
+-----------+---------------+--------+--------+-------+--------+-----------+

:  SPHERE-ZIMPOL observations of W Hya and the PSF reference star HD118877.

Table notes: AM: Airmass. The Strehl ratios in the visible were computed from the $H$-band Strehl ratios for W Hya, while they were measured from the observed ZIMPOL images for HD118877.

# Millimeter continuum image of W Hya

Figure [4](#cont_image) shows the image of W Hya obtained in the 268 GHz continuum with a restoring beam of 18 $\times$ 16 mas. The angular diameter of $\sim$60 mas obtained by fitting with a uniform elliptical disk is $\sim$1.4 times larger than the stellar angular diameter of 40.7 mas. The intensity peak is slightly offset by $\sim$7 mas ($\sim$0.34 $R_{\star}$) to the NW from the disk center. However, the asymmetry in the intensity is 1% at most, as plotted with the contours in Fig. [4](#cont_image).

# Spatially resolved spectra of the $\varv_2=2$ H$_2$O lines 

Figure [5](#whya_h2o_268_combined) shows the spatially resolved spectra of the H$_2$O lines $\varv_2=2$, 6$_{5,2}$–7$_{4,3}$ and $\varv_2=2$, 9$_{2,8}$–8$_{3,5}$ extracted from the continuum-subtracted data.

# 268 GHz H$_2$O maser conditions

Figure [\[maser_model\]](#maser_model) shows the negative optical depth of the 268 GHz H$_2$O line ($\varv_2$ = 2, 6$_{5,2}$–7$_{4,3}$) as a function of the gas temperature (kinetic temperature) and the ortho-H$_2$O number density at three different dust temperatures based on the model of Gray et al. ((cite: gray16)).

l183mm

# Comparison of the ALMA image of the 268 GHz H$_2$O $\varv_2=2$ line with the ZIMPOL data obtained at 748 nm

Figure [\[zimpol748_h2o_masers\]](#zimpol748_h2o_masers) shows a comparison of the ALMA image of the 268 GHz H$_2$O line ($\varv_2$ = 2, $J_{K_a,K_c}$ = $6_{5,2}$–$7_{4,3}$) with the ZIMPOL data obtained at 748 nm. The results are very similar to those shown in Fig. [3](#zimpol_h2o_masers). The degree of polarization at 748 nm is slightly lower than that measured at 820 nm.

l183mm

</paper>

Write the methods card for this paper.