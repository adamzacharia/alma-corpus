# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...995L...7L\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2025ApJ...995L...7L",
 "title": "The Rotation Dip in the Envelope─Disk Transition of HH 111: Evidence for Magnetic Braking",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Lin, Jyun-Heng",
 "n_authors": 6,
 "arxiv_id": "2511.15309",
 "doi": "10.3847/2041-8213/ae2272",
 "alma_projects_linked_by_archive": [
  "2012.1.00013.S",
  "2016.1.00389.S"
 ]
}
```

Paper text:
<paper>
# The Rotation Dip in the Envelope-Disk Transition of HH 111: Evidence for Magnetic Braking

## Abstract

Magnetic braking can drive angular momentum loss in star formation and influence disk evolution. A previous study of HH 111 VLA1 suggested a decrease in rotation velocity in a region between the infalling envelope and rotating disk. Using ALMA C$^{18}$O ($J = 2-1$) data, we analyzed the gas motion within 6000 au and found clear deviations from the simplest expectations of free-fall towards the central star with conserved angular momentum in the transition region between the envelope and disk (from $\sim$5200 to 160 au). The region can be further divided into three zones: (1) outer region with a significant decrease in infall velocity, dropping to approximately 60% of the free-fall velocity and 70% of conservation of angular momentum and energy; (2) middle region with a sharp drop in angular momentum and thus rotation velocity and an increase in infall velocity; and (3) inner region with rotation velocity increasing inward to connect to that of the Keplerian disk and infall velocity decreasing to zero. Comparison with non-ideal MHD simulations suggests that the reduced infall velocity in the outer region can be due to magnetic tension by the pinched magnetic field lines, the sharp drop of angular momentum in the middle region can be due to magnetic braking as the field lines pile up, and the rapid increase in rotation velocity in the inner region might result from weaker magnetic braking due to ambipolar diffusion of the field lines. The resulting dip in the rotation profile supports magnetic braking.

# Introduction

Molecular clouds are magnetized (cite: Troland_2008ApJ...680..457T; Planck_2015A&A...576A.104P), and recent polarimetric observations from the James Clerk Maxwell Telescope (JCMT) BISTRO survey (cite: Ward-Thompson_2017ApJ...842...66W; Pattle_2019ApJ...880...27P) have revealed the presence of organized magnetic fields in dense cores. These observational results indicate the need to include magnetic fields in realistic models, as they can significantly impact the dynamics of core collapse and star formation. In particular, magnetic fields can efficiently extract angular momentum from collapsing gas through magnetic braking (cite: Allen(b)\_2003ApJ...599..363A; Mellon_2008ApJ...681.1356M), thereby regulating the formation and extent of Keplerian disks (cite: Wurster_2018MNRAS.480.4434W).

Numerical and theoretical studies (cite: Krasnopolsky_2011ApJ...733...54K; Li_2011ApJ; Wurster_2018FrASS...5...39W; Zhao_2020SSRv..216...43Z; Lee_YN_2021A&A...648A.101L) suggest that magnetic braking becomes especially efficient in the envelope-disk transition region (hereafter the transition region), where the infalling envelope gradually transforms into a rotationally supported disk. In these models, magnetic braking is found to be most effective when the mass-to-flux ratio is relatively low, typically with dimensionless values $\lambda \lesssim 5$ (cite: Mellon_2008ApJ...681.1356M; Li_2011ApJ). In this region, magnetic field lines are pinched and twisted into toroidal components, generating magnetic torques that extract angular momentum and slow rotation. As a result, both the rotation and infall velocity profiles are modulated. According to simulations, a distinct dip is predicted in the rotation curve between the envelope and the Keplerian disk. The transition is also where the gas kinematics starts to deviate significantly from the simplest expectations of free-fall with conserved angular momentum, due to angular momentum loss through magnetic braking.

Despite extensive theoretical work, direct observational constraints on magnetic braking and the transition region remain limited. During the past decade, numerous studies have investigated the kinematics of early protostellar systems. Observations with the Submillimeter Array (cite: Lee_2010ApJ) and the Atacama Large Millimeter/Submillimeter Array (cite: Murillo_2013ApJ...764L..15M; Aso_2015ASPC..499..285A; Aso_2017ApJ...849...56A) have revealed a transition from $v_\phi\sim r^{-1}$ (corresponding to the outer envelope) directly to $v_\phi\sim r^{-0.5}$ (corresponding to the Keplerian disk).

(cite: Lee_2010ApJ) first introduced the possibility of a transition region in HH 111 VLA 1, which was later confirmed by ALMA observations in (cite: Lee_2016ApJ) (hereafter Paper I). reported that the specific angular momentum decreases by a factor of $\sim$3 in the region between $\sim$2000 and 160 au, reaching a minimum at a radius of about 800 au. However, detailed kinematics has not been well quantified. In this study, we follow up the work of by resolving the velocity profile in the transition region to strengthen the observational evidence for magnetic braking. We construct a kinematic model to characterize angular momentum loss and the associated changes in rotation and infall velocities, and compare our results with theoretical predictions.

The HH 111 system, located in the L1617 cloud of Orion at a distance of $\sim$400 pc (cite: Zucker_2019ApJ...879..125Z), consists of two sources: VLA 1 and VLA 2. Our target, VLA 1, is a young Class I protostar with a flattened envelope. The total mass of the protostar and disk is estimated to be $\sim$1.8$M_\odot$, consisting of $\sim$1.22$M_\odot$ for the protostar and $\sim$0.58$M_\odot$ for the disk (cite: Lee_2024ApJ...971L..23L). The envelope mass is estimated to be $\sim$0.6$M_\odot$ from $\sim$160 au (0$\overset{\prime\prime}{.}$4) to 8000 au (20$^{\prime\prime}$), and the systemic velocity in the LSR frame is 8.85 km s$^{-1}$, both reported in . Based on the inside-out collapse model (cite: Shu_1977ApJ...214..488S), the infall radius is estimated to be $\sim$30000 au. This estimate adopts a sound speed of $\sim$0.27 km s$^{-1}$, corresponding to a temperature of 20 K that is typical of observed Class I protostellar envelopes (cite: Jorgensen_2002A&A...389..908J; Launhardt_2013A&A...551A..98L), and an age of $5 \times 10^5$ yr (cite: Lee_2020NatAs...4..142L). These values suggest that the initial collapsing core has extended well beyond the currently observed envelope. The disk is nearly edge-on, with an inclination angle of 15$^\circ$–18$^\circ$ relative to the line of sight (cite: Lee_2020NatAs...4..142L), which is almost perpendicular to the inner jet axis (cite: Reipurth_1992ApJ), and the position angle (P.A.) is $\sim$6$\overset{\circ}{.}$7.

Our observations are presented in Section [2](#sec:observation). The results, discussion, and conclusion are presented in Section [3](#sec:result), [4](#sec:Disscussion) and [5](#sec:conclusion), respectively.

# Observations

The HH 111 system was observed using ALMA Band 6 with the 12m array, 7m array, and total power dishes. Most data were obtained during Cycle 1 (Project ID: 2012.1.00013.S) from 2013 to 2015, with additional 12m data from Cycle 4 (Project ID: 2016.1.00389.S) in 2016. We used the C$^{18}$O ($J = 2$–$1$) line from the 230 GHz receiver to trace the envelope and disk structures (see Table 1 for details).

To simultaneously present both extended and compact structures, the 12m and 7m data were combined using the tclean task in the Common Astronomy Software Applications (CASA) package (cite: CASA_2022PASP..134k4501C). For Cycle 1, the calibrators included J0750+1231 and J0607–0834 as bandpass calibrators, J0532+0732 and J0607–0834 as gain calibrators, and Callisto and Ganymede as flux calibrators. For Cycle 4, J0750+1231 and J5010+1800 were used as bandpass calibrators, J0552+0313 as the gain calibrator, and J0750+1231 and J0423–0120 as flux calibrators. Robust weighting parameters of 0.5 and -2 for the visibilities yielded synthesized beam sizes of 0$\overset{\prime\prime}{.}$73 × 0$\overset{\prime\prime}{.}$61, and 0$\overset{\prime\prime}{.}$16 × 0$\overset{\prime\prime}{.}$13, respectively. To recover the missing flux, the feather task (cite: Plunkett_2023PASP..135c4501P) was used to incorporate total power measurements into the final map. The resulting C$^{18}$O channel maps have rms noise levels of approximately 4.47 mJy beam$^{-1}$ (robust parameter = 0.5) and 2.62 mJy beam$^{-1}$ (robust parameter = -2), with a velocity resolution of 0.15 km s$^{-1}$.

| Project ID | Array | Execution Block | Observation date | Total integral time | Configuration | Baseline range |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 2012.1.00013.S | 12m | 3 | Apr 13-28, 2014 | 140 min | C32-4 | 20-558.2 m |  |
|  | 7m | 20 | Dec 14, 2013-Dec 14, 2014 | 445 min | 7-m | 7-48.9 m |  |
|  | TP | 8 | Aug 26 - Sep 4, 2015 | 266 min | TP | None |  |
| 2016.1.00389.S | 12m | 4 | Oct 6 - Oct 8, 2016 | 159 min | C40-6 | 17-3247 m |  |

: Observation information

# Results

The HH 111 protostellar system consists of an extended infalling envelope, a Keplerian disk, and a transition region. The envelope, which extends to $\sim$20$^{\prime\prime}$ ($\sim$8000 au), has a mass of $\sim$0.6$M_\odot$ , about one third of the combined mass of the central protostar and disk (cite: Lee_2024ApJ...971L..23L). In the outer envelope, the gas is nearly quasi-static, as discussed earlier in Section [1](#sec:intro). Within the Keplerian disk ($<$160 au or $0\overset{\prime\prime}{.}4$), the gas motion exhibits Keplerian rotation. Between the infalling envelope and the rotationally supported disk, a transition region is expected to form under the influence of a non-negligible magnetic field in the core, as the material gradually loses angular momentum and settles into Keplerian rotation. This angular momentum loss is caused by magnetic field lines transporting angular momentum away from the gas in this region, as shown in previous simulations (cite: Li_2011ApJ; Zhao_2016MNRAS.460.2050Z).

![](mom_cartoon.pdf)

## A Flattened Structure of the Envelope

Left panel of Figure [1](#fig:moment) shows the total intensity map (moment 0) on the flux-weighted velocity map (moment 1) of HH 111, derived from C$^{18}$O ($J = 2$–$1$) emission integrated from 7 to 12 km s$^{-1}$. The intensity map (contours) reveals a flattened envelope with a size of $\sim$30$^{\prime\prime}$, while the velocity map (color) displays a clear velocity gradient: blueshifted emission in the northern region and redshifted emission in the southern region. The schematic diagram in the middle of Figure [1](#fig:moment) follows , illustrating an edge-on system composed of an envelope ($\gtrsim$2000 au), a transition region ($\sim$2000 to 160 au), and a Keplerian disk ($\lesssim$160 au), with the northern side blueshifted, the southern side redshifted, and a P.A. of $\sim$6$\overset{\circ}{.}$7, along which both the velocity gradient and the density structure are aligned.

## Rotation and Infall Motion

Figure [2](#fig:pv_obs) presents the position-velocity (PV) diagram of the C$^{18}$O ($J = 2-1$) line, obtained by making a cut along the major axis of the disk (P.A. = 6$\overset{\circ}{.}$7). The cut extends 15$^{\prime\prime}$ ($\sim$6000 au) from the protostar to the north and south into the envelope (as indicated by the magenta line in Figure [1](#fig:moment)). Two PV diagrams are shown using two different robust weightings of visibilities: robust parameter of 0.5 (top) and robust parameter of -2 (bottom) for low (0$\overset{\prime\prime}{.}$73 × 0$\overset{\prime\prime}{.}$61) and high (0$\overset{\prime\prime}{.}$16 × 0$\overset{\prime\prime}{.}$13) angular resolutions, respectively.

In the low-resolution PV diagram, the line of sight velocity of the extended envelope increases gradually from $\sim$15$^{\prime\prime}$ ($\sim$6000 au) to 5$^{\prime\prime}$ ($\sim$2000 au) along both the northern and southern extensions. A sharp velocity drop is then seen from $\sim$3$^{\prime\prime}$ (1200 au) to 1$^{\prime\prime}$ (400 au), as pointed out in . In contrast, the high-resolution PV diagram reveals a sharp increase in velocity from approximately 0.5 to 4 km s$^{-1}$ inside $\sim$0$\overset{\prime\prime}{.}$5, corresponding to the Keplerian disk.

Additionally, we detected negative flux in the PV diagram, as indicated by white dashed contours in Figure [2](#fig:pv_obs). In the south, a negative feature near 0.5 km s$^{-1}$ extends from $\sim$6$^{\prime\prime}$ to 15$^{\prime\prime}$ in the high-resolution data; a similar feature is found in the north between $\sim$0.6 to 0.7 km s$^{-1}$, up to $\sim$15$^{\prime\prime}$ north of the center. These features suggest the presence of absorption, which could be caused by gas falling inward. Moreover, absorption at this velocity is consistent with the infall velocity derived later in the model (see Section [4](#sec:Disscussion)), further supporting the interpretation.

We also observed two linear PV structures, highlighted by pink ellipses in Figure [2](#fig:pv_obs). One extends from the center of the system out to $\sim-2^{\prime\prime}$, at $\sim$1 to 2 km s$^{-1}$, consistent with ; a faint northern counterpart is also seen within a similar velocity range, extending from the center to $\sim$2$^{\prime\prime}$.

![](pv_coner.pdf)

## A Flattened Infalling Rotating Envelope Model

To interpret the C$^{18}$O ($J = 2-1$), we constructed a flattened, infalling, and rotating envelope model based on (cite: Lee_2010ApJ) and extended it to include the transition region and Keplerian disk. The model combines structural profiles (half-thickness, density, temperature) with kinematic prescriptions (rotation and infall velocities):

The half-thickness of the flattened envelope, $H$, is expressed in cylindrical coordinates ($R$, $\theta$, $z$) as: $$\begin{equation}
H(R) = \text{max}\left( H_0, R\text{ tan}\theta_0\right),
\end{equation}$$ where $H_0$ is the minimum of half-thickness and $\theta_0$ is the flaring angle measuring from the mid-plane (See the right panel of Figure [1](#fig:moment) for a schematic illustration of the model structure). The number density of molecular hydrogen in the envelope is given by $$\begin{equation}
n(R,z)=n_0 \left(\frac{\sqrt{R^2+z^2}}{R_0}\right)^p,
\end{equation}$$ where $R_0$ is 2000 au (5$^{\prime\prime}$), $n_0$ is mid-plane number density at $R_0$, and $p$ is a power-law index. The C$^{18}$O abundance relative to molecular hydrogen is fixed at 1.7 $\times$ 10$^{-7}$. The temperature is **similarly** described by: $$\begin{equation}
T(R,z)=T_0 \left(\frac{\sqrt{R^2+z^2}}{R_0}\right)^q,
\end{equation}$$ where $T_0$ is the temperature at $R_0$ and *q* is the power-law index. We adopt single power-law forms across the envelope, transition region, and disk. Although simplified, this approach enables a focused analysis on velocity structure. The resulting discrepancy between the model emission intensity and the observed emission intensity will be discussed later.

In the envelope, we assume a ballistic motion under the conservation of angular momentum and energy (cite: Sakai_2014Natur.507...78S). In this model, the total energy of the infalling gas is assumed to be zero, under the assumption that collapse begins from large distances where both the gravitational potential and initial velocities are negligible. Although the envelope has finite thickness, the radial and rotation velocities are assumed to be the same as their mid-plane values at each radius: $$\begin{equation}
\label{eq.4}
v_{\phi}(R) = v_{\phi,\ell}(R) \equiv \frac{\ell_0}{R},
\end{equation}$$

$$\begin{equation}
\label{eq.5}
v_{r}(R) = v_{r,\ell,e}(R) \equiv \sqrt{\frac{2G(M_*+M_d)}{R}-v_{\phi,\ell}^2},
\end{equation}$$ where $\ell_0$ is the initial specific angular momentum at large distance before the infall, $G$ is the gravitational constant and $M_*+M_d=1.8M_\odot$ is the total mass of the protostar and disk in VLA 1. The mass of the envelope is $\sim$0.6$M_\odot$, which contributes less than 15% to the infall velocity and is therefore neglected.

In the transition region, deviations from conservation are expected due to magnetic effects (cite: Li_2011ApJ; Zhao_2020MNRAS.492.3375Z; Lee_YN_2021A&A...648A.101L). Since no analytic solution exists for the transition region, we adopted a power-law form as the angular momentum distribution for the first try:

$$\begin{equation}
\label{eq.6}
    \ell(R) = \ell_0\left(\frac{R}{R_e}\right)^{b},
\end{equation}$$ where $R_e$ is 2000 au and $b$ is the power-law index. This assumption provides a baseline for comparing the model with the observational data in more detail. Similar to Eq. [\[eq.4\]](#eq.4) and [\[eq.5\]](#eq.5), the rotation velocity can be derived from a power-law distribution of angular momentum, and the corresponding infall velocity can be obtained as follows: $$\begin{equation}
\label{eq.7}
v_{\phi}(R) =  \frac{\ell(R)}{R},
\end{equation}$$

$$\begin{equation}
\label{eq.8}
v_{r}(R) = \sqrt{\frac{2G(M_*+M_d)}{R}-v_{\phi}^2}.
\end{equation}$$

The envelope is assumed to transition to a Keplerian disk at the disk radius $R_d$ of $\sim$160 au (cite: Lee_2020NatAs...4..142L). In the Keplerian disk, the infall velocity vanishes and the rotation velocity becomes Keplerian: $$\begin{equation}
\label{eq.9}
v_{\phi,\text{Kep}}(R) = \sqrt{\frac{G(M_*+M_d)}{R}},
\end{equation}$$ where $v_{\phi,\text{Kep}}$ is the Keplerian motion.

The model spans from 10 au (0$\overset{\prime\prime}{.}$025) to 8000 au (20$^{\prime\prime}$), covering the entire system. Radiative transfer was performed using RADMC-3D (cite: Dullemond_2012ascl.soft02015D) under LTE to produce model channel maps and then the PV diagram of C$^{18}$O. The inclination angle of the flattened envelope to the plane of sky is $\sim$18$^\circ$, a mean value derived from the disk (cite: Lee_2020NatAs...4..142L) and jet (cite: Reipurth_1992ApJ). The position angle of the disk is $\sim$6$\overset{\circ}{.}$7 (). The power-law index *b* is determined using the envelope angular momentum $\ell_0 \sim 1333$ au km s$^{-1}$ (cite: Lee_2010ApJ) and the value at the disk radius $R_d$, which is derived from Keplerian rotation as $\sim$530 au km s$^{-1}$. These values yield *b* $\sim$ 0.38. The best-fit physical parameters are: $H_0 \sim$ 0$\overset{\prime\prime}{.}$4 (160 au), $\theta_0 \sim 18^\circ$, $n_0 \sim 1.3 \times 10^6$ cm$^{-3}$, $p \sim -0.13\pm0.01$, $T_0 \sim 20\pm1$ K and $q \sim -0.5\pm0.1$. These parameters are obtained by adjusting those previously obtained from fitting the spectrum, moment map, and PV diagrams of C$^{18}$O at lower resolution (cite: Lee_2010ApJ).

Figure [3](#fig:pv_obs_model)(a) presents the radial profiles of angular momentum and velocity. As discussed earlier, the velocity structure shown in the Figure is divided into three regions from the outside inward: the envelope, the transition region, and the Keplerian disk. In the envelope, we assume conservation of angular momentum and energy, and the rotation and infall velocities are derived using Eq. [\[eq.4\]](#eq.4) and [\[eq.5\]](#eq.5). In the transition region, the angular momentum is described by a power-law distribution (Eq. [\[eq.6\]](#eq.6)), and the corresponding rotation and infall velocities are computed using Eq. [\[eq.7\]](#eq.7) and [\[eq.8\]](#eq.8). In the inner Keplerian disk, the rotation follows Keplerian motion (Eq. [\[eq.9\]](#eq.9)), while the infall velocity approaches zero.

Figure [3](#fig:pv_obs_model)(b) displays the model PV diagram as contour levels overlaid on the observed PV diagram, which was generated with a robust weighting of 0.5. The residual map in Figure [3](#fig:pv_obs_model)(c), obtained by subtracting the model from the observed PV diagram, emphasizes the discrepancies between the two and illustrates the regions where the model deviates from the observations. While the outer envelope (outside $\sim$9$^{\prime\prime}$) and the disk (within $\sim$0$\overset{\prime\prime}{.}$5) are well reproduced, the intermediate region ($\sim$9$^{\prime\prime}$ to 1$^{\prime\prime}$) shows a sharp velocity drop of $\sim$70% below the power-law prediction (Figure [3](#fig:pv_obs_model)(c)). This discrepancy motivates the additional modeling of a rotation velocity dip, as discussed in the next subsection.

![](figure2.pdf)

).

## A Dip in Rotation Velocity

To address this sharp velocity decrease observed in the transition region, we introduced a modification to the model. A rotation dip is expected from theoretical and numerical studies (cite: Krasnopolsky_2011ApJ...733...54K; Li_2011ApJ; Zhao_2020MNRAS.492.3375Z; Lee_YN_2021A&A...648A.101L) because the pile-up of magnetic field lines in the transition region can lead to such a dip in rotation velocity due to non-ideal MHD effects. For example, the dotted line in the left panel of Figure 14 in (cite: Li_2011ApJ) illustrates this profile under the assumption of axisymmetry. Therefore, we adopted the angular-momentum–conserving profile as the baseline and introduced a log-Gaussian term to model the dip:

$$\begin{equation}
  v_{\phi}(R) = v_{\phi,\ell}(R) \,\bigg[ 1 - A_{\phi} \exp\!\left(-\frac{(\ln(R/R_{\phi,dip}))^2}{2\sigma_{\phi}^2}\right) \bigg],
\end{equation}$$ where $A_\phi$ is the depth of the dip (ranging from 0 to 1), $R_{\phi,dip}$ is the characteristic radius of the dip center, and $\sigma$ is the dimensionless width. It sets the radial extent of the dip relative to $R_{\phi,dip}$, with the half-maximum points given by $R/R_{\phi,dip} = \exp(\pm \sqrt{2\ln 2}\,\sigma)$. The width is different inside and outside the dip position and can be defined as: $$\begin{equation}
  \sigma_{\phi} =
  \begin{cases}
      \sigma_{\rm in}, & R \leq R_{\phi,dip}\\[6pt]
      \sigma_{\rm out}, & R > R_{\phi,dip}
  \end{cases},
\end{equation}$$ The best-fit parameters are: $A_\phi$ $\sim$ 0.8, $R_{\phi,dip}$ $\sim$ 1$\overset{\prime\prime}{.}$5 (600 au), $\sigma_{\rm in}$ $\sim$ 1.6, and $\sigma_{\rm out}\sim$0.4. The logarithmic form better captures the scale-dependent nature of the dip than a linear Gaussian.

For the infall velocity, we refine it to have a simple gradual decline as our focus in this second attempt is to better reproduce the rotation velocity profile: $$\begin{equation}
    \label{eq.12}
    v_r(R)= v_{r,\ell,e}(R_{c}) \exp\!\left(-\frac{(\ln(R/R_{c}))^2}{2\sigma_{c}^2}\right),
\end{equation}$$ where $R_c$ marks the starting point of the decline, and $\sigma_c$ is the width of the log-Gaussian profile. Here, $R_c\sim5^{\prime\prime}$(2000 au), $\sigma_c\sim1$. As shown in Figure [3](#fig:pv_obs_model)(d), the infall velocity decreases smoothly from $\sim5^{\prime\prime}$ and approaches to zero near $R_d$.

This refinement significantly improved the agreement between the model and the observed velocity profiles, particularly in reproducing the dip between $\sim$4$^{\prime\prime}$ to 1$^{\prime\prime}$, which is indicated by a yellow arrow in Figure [3](#fig:pv_obs_model)(e) and (f). However, discrepancies remain in the outer region ($\sim$13$^{\prime\prime}$ to 5$^{\prime\prime}$), where the observed PV diagram shows a $\sim$ 30% drop (0.9 km s$^{-1}$ to 0.6 km s$^{-1}$) that is not well captured by the present velocity profiles.

## A Dip in Infall Velocity

The discrepancies in the outer region ($\sim$13$^{\prime\prime}$ to 5$^{\prime\prime}$) might be caused by the infall velocity because the rotation velocity is small there. Several numerical simulations (cite: Allen(a)\_2003ApJ...599..351A; Li_2011ApJ; Zhao_2020MNRAS.492.3375Z) have predicted a decline in infall velocity due to magnetic tension (see also the dotted line in the left panel of Figure 14 in (cite: Li_2011ApJ)). Motivated by this, we introduced a similar log-Gaussian dip in the infall profile, applied only at radii greater than 3$^{\prime\prime}$:

$$\begin{equation}
    v_r(R)=v_{r,\ell,e}(R)\,\bigg[ 1 - A_{r} \exp\!\left(-\frac{(\ln(R/R_{r,dip}))^2}{2\sigma_{r}^2}\right) \bigg] ,
\end{equation}$$ where $A_r$, $R_{r,dip}$, $\sigma_r$ represent the depth of the dip, the characteristic radius of the dip, the width of the log-Gaussian profile, respectively.

Additionally, we shift the position of the peak infall velocity from $\sim$ 5$^{\prime\prime}$ to 3$\overset{\prime\prime}{.}$5 and change the profile to log-Gaussian as Eq. [\[eq.12\]](#eq.12), in order to have a better match to the observations. Among various forms tested, a log-Gaussian again provided a simple yet effective match, applied only at radii smaller than 3$\overset{\prime\prime}{.}$5.

The best-fit parameters for infall velocity are: $A_r \sim$ 0.35, $R_{r,dip}\sim7\overset{\prime\prime}{.}5$ (3000 au), $\sigma_r\sim0.3$, $R_c\sim3\overset{\prime\prime}{.}5$ (1400 au), and $\sigma_c\sim0.85$. To further improve the fit, we also slightly refined the rotation velocity profile with $R_{\phi,dip}$ $\sim$ 1$\overset{\prime\prime}{.}$5 (600 au), $A_\phi$ $\sim$ 0.9, $\sigma_{\rm in}$ $\sim$ 1.3, and $\sigma_{\rm out}\sim$ 0.5.

Figure [3](#fig:pv_obs_model)(g)–(i) show the updated model and residuals. The yellow arrows in panels (h) and (i) highlight the improved agreement in the outer envelope. As the infall velocity starts decreasing around 13$\ensuremath{''}$, we define this as the onset of the transition region, marked by the black dashed line in Figure [3](#fig:pv_obs_model)(g)

## The Best-fit Model

As shown in Figure [3](#fig:pv_obs_model)(i), the residuals are reduced to below approximately 10% of the original values in most regions. However, within 1$^{\prime\prime}$, they remain relatively large, with some areas retaining up to 50%, likely due to the reported asymmetry in the innermost envelope (cite: Lee_2024ApJ...971L..23L) as well as the influence of the linear PV structures. Despite these localized discrepancies, the fitting (Figure [3](#fig:pv_obs_model)(h) and (i)) matches observation well, with velocity uncertainties estimated to be less than 20%.

Notice that some residuals should also result from the simplified power-law assumptions for density and temperature. However, the fitting results indicate that these assumptions do not affect the inferred velocity structure. We therefore adopt this as our best-fit model.

![](theoritical_plot.pdf)

# Discussion

## Comparison to theoretical Model

Figure [4](#fig:comparison) compares the rotation and infall velocity profiles of the best-fit model with free-fall, Keplerian rotation, sound speed, as well as the rotation velocity (Eq.[\[eq.4\]](#eq.4)) and infall velocity (Eq.[\[eq.5\]](#eq.5)) from the ballistic model. In the best-fit model, outside $\sim$13$^{\prime\prime}$ infall velocity follows the conserved-energy profile (green dashed line), remaining close to the free-fall velocity (green dotted line). However, inside this radius, it deviates sharply, dropping to $\sim$60% of the free-fall value and $\sim$70% of the conserved value near 7$^{\prime\prime}$. Between 7$^{\prime\prime}$ and 3$\overset{\prime\prime}{.}$5, it slightly recovers to $\sim$70% of the free-fall value and remains close to the conserved value before steadily declining to zero at the Keplerian disk.

The rotation velocity agrees with angular momentum conservation for the region outside 5$^{\prime\prime}$. Around 4$^{\prime\prime}$, it begins to decrease significantly, reaching a minimum of 0.1 km s$^{-1}$ at 1$\overset{\prime\prime}{.}$5 with approximately 5% of the initial conserved value. Inside this point, the rotation increases again and smoothly connects to the Keplerian profile at about 0$\overset{\prime\prime}{.}$4.

Based on these profiles, we identify three distinct kinematic zones in the transition region:

### Region I: Magnetic Cushion

In Region I ($\sim$13$^{\prime\prime}$ to 5$^{\prime\prime}$, gray slashed shading), the infall velocity exhibits a clear dip, possibly due to magnetic tension, but its overall trend is still largely constrained by energy and angular momentum conservation. During the collapse, the magnetic field is initially dominated by the poloidal field. As the gas falls along the equatorial plane, the field lines are gradually dragged inward and become increasingly pinched, amplifying the outward magnetic tension that acts against infall (cite: Allen(a)\_2003ApJ...599..351A).

(cite: Li_2011ApJ) adopted a moderate magnetic field strength corresponding to a dimensionless mass-to-flux ratio $\lambda\approx2.9$ and predicted a similar effect in simulations, where magnetic fields were found to be trapped in the post-shock region of an ambipolar diffusion-induced C-shock (see, e.g., the left panel of their Fig. 5), which reduced the infall velocity by at least 10% compared to free-fall. In our case, the reduction is about $\sim$40%, possibly resulting from a stronger initial magnetic field corresponding to a smaller dimensionless mass-to-flux ratio or differing physical conditions. The trend, however, remains qualitatively consistent.

Moreover, the symmetric absorption features observed in both the northern and southern extensions of the envelope provide further support for this interpretation. Their velocities are consistent with the infall profile in Region I, suggesting that the large-scale envelope is indeed undergoing infall, possibly moderated by magnetic pressure near the outer transition boundary.

### Region II: Magnetic Braking

In Region II ($\sim$5$^{\prime\prime}$ to 1$\overset{\prime\prime}{.}$5, wheat shading), as the gas continues to collapse, the increasing rotation velocity twists the magnetic field lines azimuthally. This generates a magnetic torque in the opposite direction to the rotation, slowing down the rotation and reducing the angular momentum, through the so-called magnetic braking (cite: Allen(b)\_2003ApJ...599..363A).

Inside $\sim$4$^{\prime\prime}$, the rotation velocity decreases significantly, resulting in a dip in rotation velocity profile at $\sim$1$\overset{\prime\prime}{.}$5 (600 au), roughly consistent with that found in . A similar trend is predicted by (cite: Li_2011ApJ), which explained that in this region, ambipolar diffusion (AD) prevents the magnetic field lines from being dragged inward further (see Section [4.1.3](#sec:ambipolar) for details), causing them to accumulate in the post-AD-shock region. The accumulation of magnetic field lines increases the local field-line density and magnetic tension, which not only strengthens magnetic braking and suppresses rotation, but also reduces the radial infall velocity.

While the efficiency of angular momentum removal via magnetic braking depends on uncertain physical parameters such as magnetic field strength, ionization rate, and dust grain properties (cite: Wurster_2018FrASS...5...39W), the observed $\sim$95% reduction in rotation velocity and the accompanying decrease in infall velocity compared to the ballistic model provide empirical constraints on the conditions under which magnetic braking operates effectively.

### Region III: Ambipolar Diffusion

In Region III ($\sim$1$\overset{\prime\prime}{.}$5 to 0$\overset{\prime\prime}{.}$4, purple shading), the increase in rotation velocity can be attributed to the effects of ambipolar diffusion, which reduces the efficiency of magnetic braking, preventing significant further loss of angular momentum. As the collapse proceeds inward, density increases, leading to a lower ionization fraction and a transition to a region dominated by ambipolar diffusion. In this regime, the coupling between neutral gas and the magnetic field weakens, restricting the inward transport of magnetic flux (cite: Zhao_2016MNRAS.460.2050Z). Consequently, the magnetic braking effect becomes less efficient, allowing more angular momentum to be retained.

In this region, the decrease in radial infall velocity is also observed in some simulations (cite: Zhao_2020MNRAS.492.3375Z). As the rotation velocity increases inward, the enhanced centrifugal support counteracts gravity, reducing the infall speed. In addition, magnetic flux is largely removed, rendering the magnetic field dynamically subdominant. The increasing gas density and accumulation near the disk edge lead to further slowdown of infall motion, partly due to momentum conservation. The pressure gradient force also becomes non-negligible in this high-density environment, particularly when the infall motion becomes transonic or subsonic. These effects suggest a deviation from the assumptions of the ballistic model, and Eq. [\[eq.5\]](#eq.5) may no longer be applicable.

The rotation velocity becomes higher than the infall velocity at $\sim$1$^{\prime\prime}$ and thus the envelope starts the final phase of transitioning to the disk and forms the disk at 0$\overset{\prime\prime}{.}$4 (160 au).

In agreement with , the final angular momentum decreases to about one-third of its initial value from $\sim$5$^{\prime\prime}$ to 0$\overset{\prime\prime}{.}$4.

## Magnetic Field Line Measurement

(cite: Yen_2021ApJ...907...33Y) observed polarization in the envelope of this system using the JCMT and found that the mean orientation of the magnetic field at a resolution of $\sim$$14^{\prime\prime}$ is roughly aligned with the rotation axis, with a misalignment of approximately 30$^\circ$.

The alignment between the magnetic field orientation and the rotation axis significantly influences the efficiency of magnetic braking. Simulations by (cite: Joos_2012A&A...543A.128J) and (cite: Tsukamoto_2015ApJ...810L..26T) demonstrated that when the magnetic field is aligned or only moderately misaligned ($\sim$30$^\circ$–40$^\circ$), magnetic braking can effectively remove angular momentum from the system.

In our case, the specific angular momentum is reduced to roughly one-third of its initial conserved value and is thus consistent with these theoretical expectations. Observationally, (cite: Galametz_2020A&A...644A..47G) found a correlation between the misalignment of magnetic fields with outflow axes and the angular momentum content in low-mass protostars. Their results show that aligned systems tend to exhibit lower angular momentum in the inner envelope, further supporting the idea that magnetic braking is more efficient in aligned configurations.

# Conclusion

Using high-resolution ALMA observations, we investigated C$^{18}$O kinematics in the envelope-disk transition region of HH 111. The observed absorption features in the southern and northern regions are consistent with infalling gas, as their velocities are redshifted by $\sim$0.6-0.7 km s$^{-1}$ along the line of sight, which matches the average best-fit infall velocity of $\sim$0.7 km s$^{-1}$ in Region I.

Our best-fit model shows that the infall velocity decreases starting at $\sim$13$^{\prime\prime}$ (5200 au), likely due to magnetic tension by pinched field lines. The rotation velocity increases in the outer envelope, consistent with the angular momentum conservation, but begins to deviate from the conserved value within $\sim$5$^{\prime\prime}$ (2000 au), reaching a minimum at $\sim$1$\overset{\prime\prime}{.}$5 (600 au), as a result of a significant angular momentum loss caused by magnetic braking. Inside 1$\overset{\prime\prime}{.}$5 (600 au), the rotation velocity rapidly increases, likely due to weaker magnetic braking because of ambipolar diffusion of magnetic field lines, eventually reaching Keplerian rotation at 0$\overset{\prime\prime}{.}$4 (160 au).

Overall, the specific angular momentum decreases to one third of the initial value in the transition region, consistent with previous findings. This study provides a clearer understanding of the velocity profiles in the transition region and highlights the role of magnetic braking in the transport of angular momentum.

Further constraints on magnetic field strength, orientation, and ionization fraction in this region are essential to quantify the relative contributions of magnetic braking and other non-ideal MHD effects.

# Acknowledgements

We sincerely thank the editor and reviewer for their kind and constructive feedback. This paper makes use of the following ALMA data: ADS/JAO. ALMA# 2012.1.00013.S and 2016.1.00389.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. J.-H. L., C.-F. L., and J. A. L.-V. acknowledge support from the National Science and Technology Council (NSTC) of Taiwan through grants 112-2112-M-001-039-MY3, 113-2124-M-001-008, and 114-2124-M-001-015; the Academia Sinica Investigator Award (AS-IA-108-M01); and the Taiwan Astronomical Research Alliance (TARA, formerly TAOvA), supported by NSTC grant 113-2740-M-008-005. TARA is committed to advancing astronomy in Taiwan and paving the way for the establishment of a national observatory. J.-H. L. also acknowledges support from the New Generation Talent Cultivation Scholarship provided by the Department of Physics, National Taiwan Normal University. Z.-Y. L. is supported in part by NASA grant 80NSSC20K0533, NSF grant AST-2307199, and the Virginia Institute of Theoretical Astronomy (VITA). J.-H. L. further thanks Mr. Ayumu Shoshi for valuable discussions and assistance with CASA data processing.

# Facilities

ALMA

# Software

Astropy (cite: Astropy_5725236), CASA (cite: CASA_2022PASP..134k4501C), Matplotlib (cite: Matplotlib_2007CSE.....9...90H), CARTA (cite: Comrie_2021ascl.soft03031C), Scipy (cite: Scipy_2020NatAs...4.1158P) RADMC-3D(cite: Dullemond_2012ascl.soft02015D)

natexlab

(ref: Allen(b)\_2003ApJ...599..363A) Allen, A., Li, Z.-Y., & Shu, F. H. 2003a, ApJ, 599, 363, doi: [`10.1086/379243`](http://doi.org/10.1086/379243)

(ref: Allen(a)\_2003ApJ...599..351A) Allen, A., Shu, F. H., & Li, Z.-Y. 2003b, ApJ, 599, 351, doi: [`10.1086/379242`](http://doi.org/10.1086/379242)

(ref: Aso_2015ASPC..499..285A) Aso, Y., Ohashi, N., Saigo, K., et al. 2015, in Astronomical Society of the Pacific Conference Series, Vol. 499, Revolution in Astronomy with ALMA: The Third Year, ed. D. Iono, K. Tatematsu, A. Wootten, & L. Testi, 285

(ref: Aso_2017ApJ...849...56A) Aso, Y., Ohashi, N., Aikawa, Y., et al. 2017, ApJ, 849, 56, doi: [`10.3847/1538-4357/aa8264`](http://doi.org/10.3847/1538-4357/aa8264)

(ref: CASA_2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Comrie_2021ascl.soft03031C) Comrie, A., Wang, K.-S., Hsu, S.-C., et al. 2021, CARTA: Cube Analysis and Rendering Tool for Astronomy, Astrophysics Source Code Library, record ascl:2103.031

(ref: Dullemond_2012ascl.soft02015D) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool, Astrophysics Source Code Library, record ascl:1202.015

(ref: Galametz_2020A&A...644A..47G) Galametz, M., Maury, A., Girart, J. M., et al. 2020, A&A, 644, A47, doi: [`10.1051/0004-6361/202038854`](http://doi.org/10.1051/0004-6361/202038854)

(ref: Matplotlib_2007CSE.....9...90H) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: Joos_2012A&A...543A.128J) Joos, M., Hennebelle, P., & Ciardi, A. 2012, A&A, 543, A128, doi: [`10.1051/0004-6361/201118730`](http://doi.org/10.1051/0004-6361/201118730)

(ref: Jorgensen_2002A&A...389..908J) Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2002, A&A, 389, 908, doi: [`10.1051/0004-6361:20020681`](http://doi.org/10.1051/0004-6361:20020681)

(ref: Krasnopolsky_2011ApJ...733...54K) Krasnopolsky, R., Li, Z.-Y., & Shang, H. 2011, ApJ, 733, 54, doi: [`10.1088/0004-637X/733/1/54`](http://doi.org/10.1088/0004-637X/733/1/54)

(ref: Launhardt_2013A&A...551A..98L) Launhardt, R., Stutz, A. M., Schmiedeke, A., et al. 2013, A&A, 551, A98, doi: [`10.1051/0004-6361/201220477`](http://doi.org/10.1051/0004-6361/201220477)

(ref: Lee_2010ApJ) Lee, C.-F. 2010, ApJ, 725, 712, doi: [`10.1088/0004-637X/725/1/712`](http://doi.org/10.1088/0004-637X/725/1/712)

(ref: Lee_2016ApJ) Lee, C.-F., Hwang, H.-C., & Li, Z.-Y. 2016, ApJ, 826, 213, doi: [`10.3847/0004-637X/826/2/213`](http://doi.org/10.3847/0004-637X/826/2/213)

(ref: Lee_2024ApJ...971L..23L) Lee, C.-F., Li, Z.-Y., Ching, T.-C., et al. 2024, ApJL, 971, L23, doi: [`10.3847/2041-8213/ad68e1`](http://doi.org/10.3847/2041-8213/ad68e1)

(ref: Lee_2020NatAs...4..142L) Lee, C.-F., Li, Z.-Y., & Turner, N. J. 2020, Nature Astronomy, 4, 142, doi: [`10.1038/s41550-019-0905-x`](http://doi.org/10.1038/s41550-019-0905-x)

(ref: Lee_YN_2021A&A...648A.101L) Lee, Y.-N., Charnoz, S., & Hennebelle, P. 2021, A&A, 648, A101, doi: [`10.1051/0004-6361/202038105`](http://doi.org/10.1051/0004-6361/202038105)

(ref: Li_2011ApJ) Li, Z.-Y., Krasnopolsky, R., & Shang, H. 2011, ApJ, 738, 180, doi: [`10.1088/0004-637X/738/2/180`](http://doi.org/10.1088/0004-637X/738/2/180)

(ref: Mellon_2008ApJ...681.1356M) Mellon, R. R., & Li, Z.-Y. 2008, ApJ, 681, 1356, doi: [`10.1086/587542`](http://doi.org/10.1086/587542)

(ref: Murillo_2013ApJ...764L..15M) Murillo, N. M., & Lai, S.-P. 2013, ApJL, 764, L15, doi: [`10.1088/2041-8205/764/1/L15`](http://doi.org/10.1088/2041-8205/764/1/L15)

(ref: Pattle_2019ApJ...880...27P) Pattle, K., Lai, S.-P., Hasegawa, T., et al. 2019, ApJ, 880, 27, doi: [`10.3847/1538-4357/ab286f`](http://doi.org/10.3847/1538-4357/ab286f)

(ref: Scipy_2020NatAs...4.1158P) Pineda, J. E., Segura-Cox, D., Caselli, P., et al. 2020, Nature Astronomy, 4, 1158, doi: [`10.1038/s41550-020-1150-z`](http://doi.org/10.1038/s41550-020-1150-z)

(ref: Planck_2015A&A...576A.104P) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2015, A&A, 576, A104, doi: [`10.1051/0004-6361/201424082`](http://doi.org/10.1051/0004-6361/201424082)

(ref: Plunkett_2023PASP..135c4501P) Plunkett, A., Hacar, A., Moser-Fischer, L., et al. 2023, PASP, 135, 034501, doi: [`10.1088/1538-3873/acb9bd`](http://doi.org/10.1088/1538-3873/acb9bd)

(ref: Reipurth_1992ApJ) Reipurth, B., Raga, A. C., & Heathcote, S. 1992, ApJ, 392, 145, doi: [`10.1086/171413`](http://doi.org/10.1086/171413)

(ref: Sakai_2014Natur.507...78S) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78, doi: [`10.1038/nature13000`](http://doi.org/10.1038/nature13000)

(ref: Shu_1977ApJ...214..488S) Shu, F. H. 1977, ApJ, 214, 488, doi: [`10.1086/155274`](http://doi.org/10.1086/155274)

(ref: Troland_2008ApJ...680..457T) Troland, T. H., & Crutcher, R. M. 2008, ApJ, 680, 457, doi: [`10.1086/587546`](http://doi.org/10.1086/587546)

(ref: Tsukamoto_2015ApJ...810L..26T) Tsukamoto, Y., Iwasaki, K., Okuzumi, S., Machida, M. N., & Inutsuka, S. 2015, ApJL, 810, L26, doi: [`10.1088/2041-8205/810/2/L26`](http://doi.org/10.1088/2041-8205/810/2/L26)

(ref: Astropy_5725236) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science & Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: Ward-Thompson_2017ApJ...842...66W) Ward-Thompson, D., Pattle, K., Bastien, P., et al. 2017, ApJ, 842, 66, doi: [`10.3847/1538-4357/aa70a0`](http://doi.org/10.3847/1538-4357/aa70a0)

(ref: Wurster_2018MNRAS.480.4434W) Wurster, J., Bate, M. R., & Price, D. J. 2018, MNRAS, 480, 4434, doi: [`10.1093/mnras/sty2212`](http://doi.org/10.1093/mnras/sty2212)

(ref: Wurster_2018FrASS...5...39W) Wurster, J., & Li, Z.-Y. 2018, Frontiers in Astronomy and Space Sciences, 5, 39, doi: [`10.3389/fspas.2018.00039`](http://doi.org/10.3389/fspas.2018.00039)

(ref: Yen_2021ApJ...907...33Y) Yen, H.-W., Koch, P. M., Hull, C. L. H., et al. 2021, ApJ, 907, 33, doi: [`10.3847/1538-4357/abca99`](http://doi.org/10.3847/1538-4357/abca99)

(ref: Zhao_2020MNRAS.492.3375Z) Zhao, B., Caselli, P., Li, Z.-Y., et al. 2020a, MNRAS, 492, 3375, doi: [`10.1093/mnras/staa041`](http://doi.org/10.1093/mnras/staa041)

(ref: Zhao_2016MNRAS.460.2050Z) —. 2016, MNRAS, 460, 2050, doi: [`10.1093/mnras/stw1124`](http://doi.org/10.1093/mnras/stw1124)

(ref: Zhao_2020SSRv..216...43Z) Zhao, B., Tomida, K., Hennebelle, P., et al. 2020b, Space Sci. Rev., 216, 43, doi: [`10.1007/s11214-020-00664-z`](http://doi.org/10.1007/s11214-020-00664-z)

(ref: Zucker_2019ApJ...879..125Z) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2019, ApJ, 879, 125, doi: [`10.3847/1538-4357/ab2388`](http://doi.org/10.3847/1538-4357/ab2388)

</paper>

Write the methods card for this paper.