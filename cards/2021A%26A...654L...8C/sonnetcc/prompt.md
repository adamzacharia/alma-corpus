# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...654L...8C\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...654L...8C",
 "title": "SUPER. VI. A giant molecular halo around a z∼2 quasar",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Cicone, C.",
 "n_authors": 19,
 "arxiv_id": "2109.02269",
 "doi": "10.1051/0004-6361/202141611",
 "alma_projects_linked_by_archive": [
  "2016.1.00798.S",
  "2018.1.00992.S",
  "2019.2.00118.S"
 ]
}
```

Paper text:
<paper>
# SUPER. VI. A giant molecular halo around a $z\sim2$ quasar

# Introduction

The past few years of observational and theoretical advances in the field of galaxy formation and evolution have drawn significant attention to the role of gaseous halos surrounding galaxies, referred to as ‘circumgalactic medium’ (CGM, usually defined to extend up to the virial radius). The CGM is continuously enriched by galactic outflows, cosmological inflows, and mergers, and it is depleted by the same processes. The CGM gas undergoes several physical and chemical transformations, resulting in a constantly evolving multi-phase medium. Originally expected to be in a rarefied, highly ionised diffuse phase at $T\sim10^6~K$ (the ‘Galactic corona’), the CGM has been studied mostly in absorption (cite: Tumlinson+17; Chen17_chap9). However, there is now overwhelming evidence that the CGM of both normal and active galaxies, at any redshift, also embeds much colder and denser gas clouds, which allow it to be detected in emission using several tracers: Ly$\alpha$ (cite: ArrigoniBattaia+19; Cai+19; Bacon+21), CIV and HeII (cite: Travascio+20; Guo+20), \[OII\] (cite: Rupke+19), MgII (cite: Burchett+21), and H$\alpha$ (cite: Fossati+19). Nevertheless, the total mass of (multi-phase) gas stored on CGM scales remains unconstrained.

In addition to (tidal or ram-pressure) gas stripping from satellites (e.g. (cite: Nelson+20)), galactic outflows and fountains are the primary mechanisms enriching the CGM with metals and cool gas (cite: Suresh+19). Observations have shown that outflows can carry large amounts (a few $\sim 10^{10}~M_{\odot}$) of cold and dense molecular (H$_2$) gas travelling at speeds $v>1000$ km s$^{-1}$, out to $r\sim10$ kpc (see review by (cite: Veilleux+20)). Although there is not yet evidence for a significant H$_2$ gas mass in the CGM, (cite: Cicone+19) have pointed out that these observations will only become feasible with a new, large (e.g. 50-m) single dish (sub)mm telescope because of the limited sensitivity of current facilities to diffuse large-scale structures of cold gas. These limitations are partially mitigated at high-$z$, thanks to the larger angular diameter distance, and indeed there have been a few promising detections at $z>2$. The \[C ii\] $158\mu m$ line, probing both Hi and H$_2$ gas, was imaged out to $r\sim30$ kpc around a luminous $z=6.4$ quasar hosting a massive outflow (cite: Cicone+15) and out to $r\sim10$ kpc in a number of individual main sequence galaxies at $4<z<6$ (cite: Fujimoto+20). Diffuse CO and \[Ci\] components have been revealed on scales of $\sim70$ kpc around the Spiderweb galaxy (cite: Emonts+16) and $\sim40$ kpc around a massive star forming galaxy at $z=3.5$ (cite: Ginolfi+17).

The target of this study, cid_346, is an X-ray selected $z\sim2$ type 1 active galactic nucleus (AGN), which is part of the SINFONI survey for Unveiling the Physics and Effect of Radiative feedback (SUPER[^2], (cite: Circosta+18)). The AGN ($L_{Bol, AGN}=10^{46.66}~erg~s^{-1}$) and its host galaxy (SFR$=360$ M$_{\odot}~yr^{-1}$, $M_*=10^{11}~M_{\odot}$, see target properties in Table [1](#table:properties)) are likely undergoing an explosive feedback phase since energetic outflows have been detected from parsec ($v_{\rm CIV}^{wind}\sim2230$ km s$^{-1}$, (cite: Vietri+20)[^3]) to kiloparsec scales ($v_{\rm [OIII]}^{out}=1700$ km s$^{-1}$, (cite: Kakkad+20)). Using snapshot $1~\ensuremath{''}$-resolution Atacama Large Millimeter/submillimeter Array (ALMA) observations, (cite: Circosta+21) resolved the CO(3-2) stemming from the interstellar medium (ISM), and found no evidence for depletion of H$_2$ gas with respect to inactive galaxies at matched $z$, $M_{*}$, and broadly covering the same star formation rate (SFR) range. In this Letter we present new Atacama Compact Array (ACA) CO(3-2) observations of cid_346 tracing significant additional CO emission beyond the ISM, which led to the first image of a molecular halo out to $r\sim200$ kpc.

# Observations

The technical parameters, including line sensitivities, of the data used in this work are reported in Table [2](#table:obs). In the following, we briefly outline the data reduction and analysis steps.

The ACA CO(3-2) line observations are dated 6-8 March 2020 (Project code 2019.2.00118.S, PI: Mainieri). Data reduction and analysis were performed using the Common Astronomy Software Applications package (CASA, (cite: McMullin+07)). We obtained the calibrated measurement set by running the standard pipeline through the *scriptForPI* in CASA v.5.6. The continuum is not detected by ACA (see Appendix [5.1](#sec:continuum)), hence we did not perform a continuum subtraction. The data were imaged at their native spectral resolution of $\Delta v_{\rm channel} =5.45$ km s$^{-1}$. Deconvolution and cleaning were executed using the task `tclean` with interactive guidance for mask selection. We applied Briggs weighting and set the robust parameter equal to 0.5. All spectra were extracted from the primary-beam corrected cubes.

The ALMA CO(3-2) data are the same as in (cite: Circosta+21). We reduced them using the CASA pipeline (v.5.1) and subtracted the continuum in the *uv* plane using `uvcontsub` with a linear polynomial fit, estimating the continuum from the $\nu_{obs}<107.2$ GHz and $\nu_{obs}>107.6$ GHz channels, corresponding to $|v|>560$ km s$^{-1}$. We note that this dataset spans $\nu_{obs}\in(107.07, 109.5)$ GHz, corresponding to $v\in(-5900, 920)$ km s$^{-1}$, hence it does not provide good coverage of the redshifted side of the CO line. The maximum spectral resolution is 22 km s$^{-1}$. We imaged the ALMA *uv* visibilities with Briggs weighting and robust=0.5. We also produced a second, lower resolution cube by applying an *uv* tapering of $4\ensuremath{''}$ to enhance any extended components (ALMA-t in Table [2](#table:obs)).

The APEX $^{12}$\[CI\]$^3$P$_{2}$-$^3$P$_{1}$ (hereafter, \[CI\](2-1)) line observations were carried out in 2017 (five UT dates in April-June 2017, project ID: 098.A-0774, PI: Cicone) and 2018 (4 UT dates in May 2018, project ID: 0101.B-0758, PI: Cicone) with the PI230 heterodyne receiver in dual polarisation. Jupiter and IRC+10216 were the main focus and pointing calibrators. We placed the tuning frequency ($\rm \nu_{obs}=251.372$ GHz) at IF=10 GHz in the upper side band (USB), and analysed the data exploiting the full IF 4-12 GHz bandwidth. The instrumental resolution is 0.061 MHz ($\Delta v_{res}$= 0.073 km s$^{-1}$). We reduced the data using the Continuum and Line Analysis Single-dish Software (CLASS), which is part of the GILDAS package[^4]. We checked all scans and dropped those showing baseline ripples or instrumental features. The final spectrum (Figure [6](#fig:APEX_CI_spec)) does not show any clear \[CI\] detection, down to a 1$\sigma$ rms line sensitivity of $T_{A}^{\prime}=0.175$ mK in $\Delta v=50$ km s$^{-1}$. To convert the antenna temperature units into flux density, we adopted a factor of $40\pm7$ Jy K$^{-1}$, which is the average value estimated for PI230 during our observing runs[^5].

|                                            |                            |
|:-------------------------------------------|:--------------------------:|
| RA, Dec (ICRS)                             | 09:59:43.412, 02:07:07:402 |
| Redshift                                   |  $z_{\rm CO}=2.2197^{\S}$  |
| Physical scale \[kpc arcsec$^{-1}$\]       |        8.459 $^{*}$        |
| Nuclear activity                           |           quasar           |
| $\log M_{*}~[M_{\odot}]$                   |   $11.0\pm0.2$$^{\dag}$    |
| SFR \[$M_{\odot}~yr^{-1}$\]                |    $360\pm 50$$^{\dag}$    |
| $\log L_{\rm Bol, AGN}~[\rm erg~s^{-1}]$   | $46.66\pm 0.02$$^{\ddag}$  |
| $\log M_{BH}$ $[M_{\odot}]$                |   $9.1\pm 0.3$$^{\ddag}$   |
| $\lambda_{Edd} = L_{\rm Bol, AGN}/L_{Edd}$ |      $0.2$$^{\ddag}$       |

: Source properties: cid_346

*Notes:* $^{\S}$ Line peak of the ALMA CO(3-2) spectrum probing $r\lesssim8$ kpc (see also (cite: Circosta+21)). $^{*}$ We adopted a standard $\Lambda$ cold dark matter cosmology with $H_0$ = 67.4 km s$^{-1}$Mpc$^{-1}$, $\Omega_{\rm M}$ = 0.315, and $\Omega_{\Lambda}$ = 0.685 (cite: Planck2018_parameters). $^{\dag}$ (cite: Circosta+18); $^{\ddag}$ (cite: Vietri+20).

+----------------------------------------------------------------------------------------------------------------------------------------------+
| $^{12}$CO(J=3-2) line ($\nu_{\rm rest}=345.796$ GHz, $\nu_{obs} = 107.4$ GHz)                                                                |
+:==================+:=====================:+:=====================:+:=================:+:=================:+:================================:+
| Tel.              | Res.                  | MRS/FoV               | Time              | PWV               | 1$\sigma$ ($\Delta v_{channel})$ |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+
|                   | \[$\ensuremath{''}$\] | \[$\ensuremath{''}$\] | \[h\]             | \[mm\]            | \[mJy/beam\]                     |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+
| \(1\)             | \(2\)                 | \(3\)                 | \(4\)             | \(5\)             | \(6\)                            |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+
| ACA               | $9.3$                 | 73/99                 | 5.2               | 5.2               | 4.0 (6 km s$^{-1}$)              |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+
| ALMA              | $1.0$                 | 9.9/57                | 0.2               | 1.8               | 0.7 (22 km s$^{-1}$)             |
+-------------------+-----------------------+                       |                   |                   +----------------------------------+
| ALMA-t            | $3.4$                 |                       |                   |                   | 1.4 (22 km s$^{-1}$)             |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+
| $^{12}$\[CI\]$^3$P$_{2}$-$^3$P$_{1}$ line ($\nu_{\rm rest}=809.342$ GHz, $\nu_{obs}=251.372$ GHz)                                            |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+
| APEX              | 27                    | 27/27                 | 16.9              | 1.5               | 7.0 (50 km s$^{-1}$)             |
+-------------------+-----------------------+-----------------------+-------------------+-------------------+----------------------------------+

: Description of the sub-millimetre and millimetre data used in this work

*Columns:* (1) telescope; (2) spatial resolution; (3) maximum recoverable scale (MRS) and field of View (FoV); (4) on source time; (4) precipitable water vapour (PWV); and (6) average line sensitivity per spectral channel ($1\sigma$ rms).

![](aca_co32_m400p1000_map.pdf)

![](plot_spec_aca_co32_m400p1000cont_PB.pdf)

# Results

Figure [1](#fig:co32_aca_maps) shows the ACA CO(3-2) map obtained by integrating the line emission across its full spectral extent of $-400<v[\rm km~s^{-1}]<1000$. The source was resolved at the ACA resolution of $9.3\ensuremath{''}\simeq80$ kpc, spreading across tens of arcsec in projected size. It shows a central peak, slightly ($\sim3\ensuremath{''}$) offset from the AGN position in the south-east direction, and additional secondary peaks north, north-east, and south-east of the nucleus. To our knowledge, this is the most extended molecular CGM reservoir that has ever been mapped.

The ACA CO(3-2) spectrum is shown in Figure [2](#fig:co32_spectra). A Gaussian fit returns a total flux of $8.7\pm2.6$ Jy km s$^{-1}$, which is a factor of $14\pm5$ higher than estimated by (cite: Circosta+21) for the ISM component. The additional CO(3-2) emission detected by ACA spans a much broader range in line-of-sight velocities than the inner ISM. Although our spectral analysis is limited by the low signal-to-noise (S/N) of the data, by comparing ACA and ALMA spectra extracted from different apertures (see Figure [2](#fig:co32_spectra) and additional spectra in Fig. [7](#fig:co32_spectra_appendix)), we infer that: (i) the CO(3-2) emission within $r_{\rm ap}\lesssim 5\ensuremath{''}$ is dominated by a narrow (FWHM$\sim200$ km s$^{-1}$) line centred at $\nu_{\rm obs}=107.4$ GHz (corresponding to the $z_{\rm CO}$ listed in Table [1](#table:properties)). Its peak flux density is maximised in the spectrum extracted from $r_{\rm ap}=2.5\ensuremath{''}$ ($S^{\rm peak}_{\nu}\sim4$ mJy), and it remains constant when using bigger extraction areas. (ii) Larger apertures collect significant additional flux due to a second line centred at $v\sim450$ km s$^{-1}$, a feature that is marginally detected by ALMA even in smaller apertures, but it only becomes dominant at $r_{\rm ap}>5\ensuremath{''}$. This component is responsible for the red shift of the main CO(3-2) peak in the low resolution ACA spectra. (iii) For $r_{\rm ap}>15\ensuremath{''}$, which are only reliably probed by ACA, we observed – at a spectral resolution of $\Delta v_{channel}=160$ km s$^{-1}$ – a very broad line profile extending from $v\sim-400$ km s$^{-1}$ to $v\sim1000$ km s$^{-1}$with respect to a central frequency of $\nu_{\rm obs}=107.4$ GHz, with an additional fainter component at $v\sim1500$ km s$^{-1}$(see Fig. [7](#fig:co32_spectra_appendix), bottom panel).

![](co32_flux_apertures.pdf)

![](aca_co32_m400p1000_merge_uvc8_real_cgausspoint_fit.pdf)

The curve of growth in Figure [3](#fig:co32_flux_apertures) shows a steady increase in CO(3-2) flux up to $r_{\rm ap}\simeq 25\ensuremath{''}$, and it plateaus for larger apertures. From this, we infer that the CO halo extends up to $r\sim200$ kpc. This size estimate is consistent with the analysis of the *uv* visibilities presented in Fig. [4](#fig:co32_aca_uvplots), where the data are modelled using a circular Gaussian function with $\rm FWHM=300\pm80$ kpc, in addition to a point source (the unresolved ISM) which contributes very little to the total flux.

# Discussion and conclusions

|  |  |  |  |
|:---|:--:|:--:|:---|
| Region | $\int S_{CO(3-2)}dv$ | $\rm L^{\prime}_{CO(3-2)}$ | Notes |
|  | \[Jy km s$^{-1}$\] | \[10$^{10}$ K km s$^{-1}$ pc$^2$\] |  |
| $r\lesssim8$ kpc | $0.63\pm0.09$ | $1.74\pm0.24$ | fiducial ISM (cite: Circosta+21) |
| $r\lesssim200$ kpc | $8.7\pm2.6$ | $24\pm7$ | fiducial CGM (Figure [2](#fig:co32_spectra)) |
| FWHM=$300\pm80$ kpc | $16\pm11$ | $40\pm30$ | *uv* fit (Figure [4](#fig:co32_aca_uvplots)) |

*Notes:* Errors include a 5% calibration uncertainty.

Table [\[table:results\]](#table:results) summarises the CO(3-2) measurements available for cid_346 and its halo: our fiducial ISM value is the one measured by (cite: Circosta+21) at $r\lesssim8$ kpc, while the fiducial CGM CO(3-2) flux (which includes the ISM contribution) is the one obtained through the Gaussian fit shown in Fig. [2](#fig:co32_spectra). In the same table, we also report the zeroth-baseline flux extrapolated through the *uv* visibility fit in Fig. [4](#fig:co32_aca_uvplots), which is consistent, within its (large) error, with the CGM flux measured from the spectrum.

Any estimate of molecular gas mass based on a single CO transition is highly uncertain. The uncertainty is even higher in the absence of any (theoretical or observational) constraint on the physical conditions of the gas, which is the case for this newly discovered molecular CGM reservoir around cid_346. An extremely strict lower boundary on $M_{mol}^{CGM}$, obtained by simply counting the CO molecules in the $J=3$ level in an optically thin regime, is $M_{mol}^{CGM}\gg 2\times 10^9$ M$_{\odot}$ (see Sect [5.4](#sec:mmol_limits)). A more reasonable (but still quite strict) lower limit is $M_{mol}^{CGM}> 10^{10}$ M$_{\odot}$, inferred assuming local thermodynamic equilibrium (LTE). There is however room for up to $1.7\times 10^{12}$ M$_{\odot}$ of molecular gas in the CGM of cid_346 (upper limit assuming optically thick CO with $\alpha_{\rm CO}=3.6$ $\rm M_{\odot}~(K~km~s^{-1}~pc^2)^{-1}$ and $L^{\prime}_{CO(3-2)}/L^{\prime}_{CO(1-0)}=0.5$, see Sect [5.4](#sec:mmol_limits)). As a comparison, it has been estimated that the CGM of the Milky Way contains a few 10$^9~M_{\odot}$ of gas within 75 kpc (cite: Zheng+19), although a constraint on the molecular phase, as well as on the warm-hot medium, is still missing.

The origin of such a massive molecular CGM reservoir around cid_346 is unclear. Current data (see Sect. [5.5](#sec:field_overdensity)) disfavour an over-density of galaxies, contrary to previous (albeit much less extended) detections of molecular halos, all in high-z protoclusters (cite: Ginolfi+17; Emonts+16). Therefore, in the absence of better quality data, we set aside the hypothesis that this cold CGM reservoir coincides with a dense environment and thus that it may be the result of gravitational interactions and ram-pressure stripping from satellites.

The moment maps (see Section [5.6](#sec:moment_maps)) show complex kinematics, which may be a signature of the direct imprint by AGN-driven outflows, but also of accreting streams. Interestingly, cid_346 is one of the few Type 1 SUPER targets for which high velocity \[OIII\] $\lambda5007\AA{}$ emission, which is a signature of ionised outflows, has been detected as far as $\sim3$ kpc south-east of the AGN, using SINFONI-AO data (cite: Kakkad+20). This is also the same direction of the offset of the global ACA CO(3-2) peak with respect to the AGN position (Fig. [1](#fig:co32_aca_maps)), although we should not over-interpret this result, since the map in Fig. [1](#fig:co32_aca_maps) results from an integration of the CO(3-2) emission over a very broad velocity range, and by restricting the velocity range the peak would shift (see e.g. Fig. [9](#fig:co32_aca_moment_maps), left panel). The large line width of the CO emission stemming from the CGM (Fig. [2](#fig:co32_spectra)) is suggestive of outflows, but it may also simply reflect gas assembly within the dark matter halo.

Understanding the presence and survival of molecular gas out to $r\sim200$ kpc is a real puzzle. On the one hand, the fact that the CGM of massive high-z galaxies is shaped by outflows, and, specifically, AGN-driven outflows, is a prediction of models (cite: Nelson+19; Suresh+19). On the other hand, whether such outflows can have a direct impact on – or even be responsible for – a molecular CGM reservoir has yet to be proven from a theoretical perspective. It has been shown that clumps of cold gas can survive the entrainment by a hot medium if they are large enough (e.g. (cite: Armillotta+17; Gronke+Oh18)). This process has, however, never been probed on CGM scales in a cosmological box. In current simulations, even though AGN-driven outflows can have a higher cool ($T\sim10^4~K$) mass content and thus contribute to seed cold gas on large scales, the outer CGM is still predominantly hot (cite: Nelson+20). This could be a numerical resolution bias (cite: Hummels+19) since no current cosmological simulation can track the survival or formation of molecular gas on scales of 100s of kiloparsecs. Observational evidence that outflows may be linked to extended cold gas CGM reservoirs has been building up, especially in powerful AGN (cite: Cicone+15; Travascio+20; Izumi+21), and cid_346 is the most extraordinary of such cases. However, an in-depth study of such extended cold CGM structures, especially at $z\sim0$, will only be possible with a facility such as the Atacama Large Aperture Submillimeter Telescope (AtLAST, e.g. (cite: Klaassen+20; Cicone+19)).

# Acknowledgements

We thank the anonymous referee for the very valuable feedback. CC thanks Padelis P. Papadopoulos for helping us derive sensible limits on the molecular gas masses, and Rolf Güsten for early access to the PI230 instrument. We warmly thank the APEX and ALMA staff for their technical support and their excellent service to the community, especially during the current pandemic. This paper makes use of the following ACA and ALMA data: ADS\JAO.ALMA#2019.2.00118.S, ADS\JAO.ALMA#2016.1.00798.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This publication is based on data acquired with the Atacama Pathfinder Experiment (APEX). APEX is a collaboration between the Max-Planck-Institut fur Radioastronomie, the European Southern Observatory, and the Onsala Space Observatory. Based on observations collected at the European Organisation for Astronomical Research in the Southern Hemisphere under ESO programmes 098.A-0774(A) and 0101.B-0758(A). GV acknowledges financial support from Premiale 2015 MITiC (PI: B. Garilli). This project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 951815.

37 natexlab

(ref: Armillotta+17) Armillotta, L., Fraternali, F., Werk, J. K., Prochaska, J. X., & Marinacci, F. 2017, MNRAS, 470, 114

(ref: ArrigoniBattaia+19) Arrigoni Battaia, F., Hennawi, J. F., Prochaska, J. X., et al. 2019, MNRAS, 482, 3162

(ref: Bacon+21) Bacon, R., Mary, D., Garel, T., et al. 2021, A&A, 647, A107

(ref: Burchett+21) Burchett, J. N., Rubin, K. H. R., Prochaska, J. X., et al. 2021, ApJ, 909, 151

(ref: Cai+19) Cai, Z., Cantalupo, S., Prochaska, J. X., et al. 2019, ApJS, 245, 23

(ref: Chen17_chap9) Chen, H.-W. 2017, Outskirts of Distant Galaxies in Absorption, ed. J. H. Knapen, J. C. Lee, & A. Gil de Paz, Vol. 434, 291

(ref: Cicone+19) Cicone, C., De Breuck, C., Chen, C.-C., et al. 2019, BAAS, 51, 82

(ref: Cicone+15) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14

(ref: Circosta+21) Circosta, C., Mainieri, V., Lamperti, I., et al. 2021, A&A, 646, A96

(ref: Circosta+18) Circosta, C., Mainieri, V., Padovani, P., et al. 2018, A&A, 620, A82

(ref: Emonts+16) Emonts, B. H. C., Lehnert, M. D., Villar-Martı́n, M., et al. 2016, Science, 354, 1128

(ref: Fossati+19) Fossati, M., Fumagalli, M., Gavazzi, G., et al. 2019, MNRAS, 484, 2212

(ref: Fujimoto+20) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: Ginolfi+17) Ginolfi, M., Maiolino, R., Nagao, T., et al. 2017, MNRAS, 468, 3468

(ref: Gronke+Oh18) Gronke, M. & Oh, S. P. 2018, MNRAS, 480, L111

(ref: Guo+20) Guo, Y., Maiolino, R., Jiang, L., et al. 2020, ApJ, 898, 26

(ref: Hummels+19) Hummels, C. B., Smith, B. D., Hopkins, P. F., et al. 2019, ApJ, 882, 156

(ref: Izumi+21) Izumi, T., Matsuoka, Y., Fujimoto, S., et al. 2021, ApJ, 914, 36

(ref: Kakkad+20) Kakkad, D., Mainieri, V., Vietri, G., et al. 2020, A&A, 642, A147

(ref: Klaassen+20) Klaassen, P. D., Mroczkowski, T. K., Cicone, C., et al. 2020, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 11445, 114452F

(ref: Laigle+16) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: Lamperti+21) Lamperti, I., Harrison, C. M., Mainieri, V., et al. 2021, arXiv e-prints, arXiv:2109.02674

(ref: McMullin+07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mehta+18) Mehta, V., Scarlata, C., Capak, P., et al. 2018, ApJS, 235, 36

(ref: Nelson+19) Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234

(ref: Nelson+20) Nelson, D., Sharma, P., Pillepich, A., et al. 2020, MNRAS, 498, 2391

(ref: Papadopoulos+12b) Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak, K. G., & Gao, Y. 2012, ApJ, 751, 10

(ref: Planck2018_parameters) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Rupke+19) Rupke, D. S. N., Coil, A., Geach, J. E., et al. 2019, Nature, 574, 643

(ref: Suresh+19) Suresh, J., Nelson, D., Genel, S., Rubin, K. H. R., & Hernquist, L. 2019, MNRAS, 483, 4040

(ref: Travascio+20) Travascio, A., Zappacosta, L., Cantalupo, S., et al. 2020, A&A, 635, A157

(ref: Tumlinson+17) Tumlinson, J., Peeples, M. S., & Werk, J. K. 2017, ARA&A, 55, 389

(ref: Valentino+18) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: Valentino+20) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24

(ref: Veilleux+20) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2

(ref: Vietri+20) Vietri, G., Mainieri, V., Kakkad, D., et al. 2020, A&A, 644, A175

(ref: Zheng+19) Zheng, Y., Peek, J. E. G., Putman, M. E., & Werk, J. K. 2019, ApJ, 871, 35

# Supplementary material

## ACA non-detection of the continuum

The 3mm continuum flux density measured in cid_346 by (cite: Circosta+21) using ALMA is $0.15\pm0.04$ mJy. Such continuum emission is not detected by ACA. We verified this by using a line-free spectral window (spw17) adjacent to the one containing the CO(3-2) line, but at a lower spectral resolution of $\Delta v_{\rm channel}=22$ km s$^{-1}$, which covers observed frequencies between 106.75 and 104.80 GHz. In Figure [5](#fig:ACA_cont) we present a collapsed map of the full spw17 range, centred at $\nu_{obs}=105.796$ GHz, which does not show any significant detection. Using this map, we can place an ACA $3\sigma$ upper limit on the continuum level of $\rm S_{106~GHz}<0.5~mJy~beam^{-1}$, which is consistent with the detection by (cite: Circosta+21).

![](all_spw17_cid346_cont_map.pdf)

## The APEX \[CI\](2-1) data

![](2018_2017_APEX_CI10_combine.pdf)

Figure [6](#fig:APEX_CI_spec) shows the final APEX PI230 spectrum, obtained by combining all the good quality scans selected from the 2017 and 2018 observing runs, for a total of 16.9 hours of single-polarisation data. The tuning frequency is the redshifted frequency of the \[CI\](2-1) line ($\rm \nu_{obs}=251.372$ GHz, set to $v=0$ km s$^{-1}$). The CO(7-6) line would be expected at $\rm \nu_{obs}=250.5363$ GHz, thus $\Delta v\sim 1000$ km s$^{-1}$ redward of the \[CI\](2-1) line. Neither of the two lines is detected in the APEX data, down to a sensitivity of $7.0\pm1.2$ mJy per $\Delta v=50$ km s$^{-1}$ channel.

By assuming that the \[CI\](2-1) and CO(3-2) lines share the same line profile, we can assume ${\rm FWHM}\sim1000$ km s$^{-1}$ (see Fig. [2](#fig:co32_spectra)) to place a 3$\sigma$ upper limit on the \[CI\](2-1) flux: $$\begin{equation}
        \rm \int S_{\nu}^{[CI]}dv < 3 \sigma_{rms}\sqrt{\Delta v_{channel}\cdot {\rm FWHM}_{\rm [CI]}} \sim  4.7~Jy~km~s^{-1},
\end{equation}$$ which corresponds to $L^{\prime}_{\rm [CI](2-1)}<2.4\times10^{10}$ K km s$^{-1}$ pc$^2$.

## CO(3-2) line spectral fits

![](plot_spec_alma_oplot.pdf)

![](plot_spec_alma_oplot_2.pdf)

![](plot_spec_aca_co32_PB_oplot_2.pdf)

In this section we describe, in more detail, the Gaussian fitting procedure used to measure the CO(3-2) fluxes for the curve of growth reported in Fig. [3](#fig:co32_flux_apertures). A few representative spectra used to compute Fig. [3](#fig:co32_flux_apertures) are reported in Fig. [7](#fig:co32_spectra_appendix). The CO(3-2) spectral line profile significantly varies with the aperture used for spectra extraction, and of course it also depends on the S/N of the data and spectral binning applied. The spectra used in this analysis can be divided into three categories, shown in different panels of Fig. [7](#fig:co32_spectra_appendix).

For small apertures probed by the ALMA data ($r_{aperture}=0.6\ensuremath{''}-5\ensuremath{''}$), the CO(3-2) spectrum exhibits a single component, which can be modelled using a Gaussian function. The top panel of Fig. [7](#fig:co32_spectra_appendix) shows a few examples and reports, in the top-right inset, the best fit to the $r_{aperture}=1''$ spectrum.

The ALMA spectra extracted using $r_{aperture}=7.5\ensuremath{''}$ and $10\ensuremath{''}$ show a clear additional redshifted component at $v\sim 450-480$ km s$^{-1}$, brighter than the one at $v=0$ km s$^{-1}$, which is very close to the edge of the ALMA spectral window. These spectra are shown in the middle panel of Fig. [7](#fig:co32_spectra_appendix).

The ALMA spectra extracted from even larger apertures, with $r_{aperture}>10\ensuremath{''}$, are not reliable, even when using the tapered dataset (ALMA-t in Table [1](#table:properties)). Indeed, at these scales, the snapshot $1\ensuremath{''}$-resolution ALMA data fail to recover the additional extended flux and the increasingly larger contribution from the redshifted component (due to their limited bandwidth on the red side of the line), and the resulting flux measurement is affected by severe aperture dilution effects. These technical issues are instructively shown by the two ALMA data points at $r_{aperture}>10\ensuremath{''}$ in Fig. [3](#fig:co32_flux_apertures). These fluxes were obtained by fitting the spectra extracted from the ALMA-t cube, using elliptical apertures with semi-major axes of $a=15\ensuremath{''}$, $b=10\ensuremath{''}$ for the data point plotted at $r_{aperture}=12.5\ensuremath{''}$, and $a=20\ensuremath{''}$, $b=15\ensuremath{''}$, for the data point plotted at $r_{aperture}=17.5\ensuremath{''}$. The resulting flux values fall below the $r_{aperture}=10\ensuremath{''}$ value, hence demonstrating the inadequacy of this dataset for probing extended structures.

Apertures with $r>10\ensuremath{''}$ are only reliably probed by the ACA data. The ACA spectra were rebinned to $\Delta v_{channel}=160$ km s$^{-1}$ in order to maximise the S/N. All spectra were fitted using a single broad Gaussian component, as shown in the bottom panel of Fig. [7](#fig:co32_spectra_appendix) (see also Fig. [2](#fig:co32_spectra)). The central velocity of the best-fit Gaussian function varies within the range $v\sim200-300$ km s$^{-1}$ for different apertures, hence robustly displaying a red shift compared to the CO(3-2) emission arising from the inner ISM of cid_346. This is also clearly shown by the comparison between ALMA and ACA spectra in Fig. [2](#fig:co32_spectra). Although the low S/N of the ACA spectra does not allow us to analyse them at higher spectral resolution, it is likely that the observed global redshift of the CO(3-2) line results from the spectral blending (when using such a large bin size of $\Delta v_{channel}=160$ km s$^{-1}$) of the two peaks that are already visible in the ALMA spectra extracted from $r_{aperture}=7.5\ensuremath{''}$ and $10\ensuremath{''}$ (middle panel of Fig. [7](#fig:co32_spectra_appendix)). The best-fit FWHM value is $\sim1000$ km s$^{-1}$ for all ACA spectral fits. None of these single-Gaussian fits include the additional component centred at $v\sim1500$ km s$^{-1}$, which is detected at too low of an S/N to be fit separately, but it is consistently present in all the ACA spectra, as shown in the bottom panel of Fig. [7](#fig:co32_spectra_appendix). We note that we cannot verify whether this component is also present on the smaller ISM scales probed by ALMA because our ALMA data lack the corresponding frequency coverage.

## Lower and upper limits on $M_{mol}^{CGM}$

In the following, we use our fiducial estimate of the CGM CO(3-2) luminosity, $L^{\prime}_{\rm CO(3-2)}=(24\pm7)\times10^{10}$ K km s$^{-1}$ pc$^2$ (Table [\[table:results\]](#table:results)), to place strict lower and upper limits on the CGM molecular gas mass. We treat all of the CO(3-2) emission equally, although the physical conditions in the ISM (inner kiloparsecs) can be different from those on larger scales. In the absence of additional constraints, any assumption would be speculative.

### Lower limit on $M_{mol}^{CGM}$

A lower boundary for $M_{mol}^{CGM}$ can be estimated using the optically thin limit. Even in this case, there are several possible routes (see, e.g. (cite: Papadopoulos+12b)), which are more or less conservative depending on the underlying assumptions. The most minimalist one is to estimate the column density of the molecular gas in the $J=3$ level, $N_3$, and from this infer the molecular gas mass assuming only the $J=3$ level contribution, that is $$\begin{equation}
\label{eq:N3_contri}
 M_{mol}^{CGM} \gg N_3~R_{\rm CO}~\mu~m_{H_2} \sim 2 \times 10^9 ~M_{\odot},
\end{equation}$$ where $R_{CO}$ is the $\rm [H_2/CO]$ abundance ratio and $\mu=1.36$ accounts for the mass in Helium. We have assumed a typical CO abundance $\rm [CO/H_2]=10^{-4}$ since lower values, for example due to lower metallicities and/or CO-dark H$_2$ gas, would only increase the mass. We stress that Eq. [\[eq:N3_contri\]](#eq:N3_contri) represents an extremely strict lower limit (hence the $\gg$ symbol) that is physically unattainable because it does not account for the (significant) contribution to the total column density $N_{tot}$ due to the CO molecules in the $J=0,1,2$ levels (or in the $J\geq4$ levels).

To account for the contribution from the other CO energy levels, we can assume local thermodynamic equilibrium (LTE) and so describe the system as a Boltzmann distribution with a single temperature, $T_{kin}$. Under this condition, the total column density $N_{tot}$ can be derived using $$\begin{equation}
        \frac{N_{3}}{N_{tot}} =\frac{g_3}{Z_{\rm LTE}}e^{-E_{3}/ (k_B T_{kin})},
\end{equation}$$ where $g_3 = 7$, $Z_{LTE}$ is the LTE partition function given by $Z_{\rm LTE}\simeq 2k_B T_{kin}/E_1$, and the $J=1$ and $J=3$ state energies are $E_1/k_B = 5.53$ K and $E_3/k_B = 33.19$ K. Hence, a more reasonable lower limit for the CGM molecular gas mass is as follows: $$\begin{equation}
\label{eq:N3_LTE}
        M_{mol}^{CGM} > N_{tot} R_{\rm CO}~\mu~m_{H_2} \sim  10^{10}~M_{\odot}.
\end{equation}$$ Here we have assumed $T_{kin}=50$ K, which corresponds to the lower boundary of the cold neutral medium temperature range.

### Upper limit on $M_{mol}^{CGM}$

We may estimate an upper limit on $M_{mol}^{CGM}$ by assuming optically thick CO emission throughout the entire CGM reservoir. Several recent literature studies promote the use of a CO-to-$H_2$ conversion factor of $\alpha_{\rm CO(1-0)}=3.6$ M$_{\odot}~(K~km~s^{-1}~pc^2)^{-1}$ (including the Helium correction) for the molecular ISM of $z\sim2$ galaxies (see references in (cite: Circosta+21)). Concerning the CO excitation, the literature reports a broad range of $r_{31}=L^{\prime}_{CO(3-2)}/L^{\prime}_{CO(1-0)}$ measurements, $r_{31}\sim0.5-1$, at both low and high redshifts. If we assume $r_{31}\sim0.5$, combined with the $\alpha_{\rm CO(1-0)}$ quoted above, we obtain a total molecular gas mass of $1.7\times10^{12}~M_{\odot}$, which may be considered an upper limit given the premise of optically thick CO emission and the low $r_{31}$ ratio.

Alternatively, it is possible to convert the APEX \[CI\](2-1) non-detection into an upper limit on $M_{mol}^{CGM}$, by assuming a Carbon excitation temperature $T_{ex}$ and a Carbon abundance $X_{CI}=[C]/[H_2]$. The most updated high-z compilations of \[CI\](2-1) and \[CI\](1-0) line measurements by (cite: Valentino+18) and (cite: Valentino+20) provide average values of $L^{\prime}_{\rm [CI](2-1)}/L^{\prime}_{\rm [CI](1-0)}= 0.47$ (corresponding to $T_{ex}=26$ K) and $X_{\rm CI}= 1.6\times 10^{-5}$ for the ISM of main sequence galaxies at $z>1$. If we adopt these values we obtain $M_{mol}< 9 \times 10^{11}~M_{\odot}$, which is slightly more stringent than the $\alpha_{\rm CO(1-0)}$-based upper $M_{mol}$ boundary. However, we note that the APEX single-pointing FoV of $27\ensuremath{''}$ (Table [2](#table:obs)) is smaller than the full extent of the CO halo detected by ACA, and an aperture of $r_{ap}=15\ensuremath{''}$ contains half of our fiducial CGM CO(3-2) flux ($4.2\pm1.9$ Jy km s$^{-1}$, see Fig [3](#fig:co32_flux_apertures)), hence the two upper limits are consistent.

Finally, we note that some caution must be taken when comparing these mass estimates with the previous molecular CGM detections by (cite: Ginolfi+17) and (cite: Emonts+16). Indeed, these studies used very high $\alpha_{\rm CO(1-0)}$ values of $\alpha_{\rm CO(1-0)}=10$ and $\alpha_{\rm CO(1-0)}=4$ M$_{\odot}~(K~km~s^{-1}~pc^2)^{-1}$, respectively.

## Continuum sources in the field

![](ACA_ALMA_RGB_400_1000.pdf)

|  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|
| Instrument | Band | $\lambda_{cen}$ | FWHM | PSF | 5$\sigma$-depth |
|  |  | \[$\mu$m\] | \[$\mu$m\] | \[$''$\] | \[mag\] |
| Subaru/HSC$^{\dag}$ | g-band (Blue) | 0.4816 | 0.1386 | 0.63 | 26.84 |
| Subaru/HSC$^{\dag}$ | z-band (Green) | 0.8912 | 0.0773 | 0.45 | 24.79 |
| Spitzer$^{\ddag}$ | IRAC ch2 (Red) | 4.5049 | 1.0097 | 1.4 | 25.13 |

*Notes:* $^{\dag}$ (cite: Laigle+16); $^{\ddag}$ (cite: Mehta+18).

Figure [8](#fig:RGB) displays the ACA CO(3-2) contours overlaid on the optical and infrared image of the field, obtained by combining photometric data from the *Subaru* and *Spitzer* telescopes. The central wavelength ($\lambda_{cen}$) and FWHM of the photometric filters, as well as the point spread function (PSF) and sensitivity of the images are listed in Table [\[table:RGB\]](#table:RGB). Figure [8](#fig:RGB) shows that the ACA CO peaks do not coincide with any known optical or infrared source. The galaxies with a photometric or spectroscopic redshift measurement that lie close to the CO contours have redshifts that are not consistent with the range inferred from the CO data of $z\sim 2.215-2.230$. In addition, sensitive ALMA Band 7 continuum observations [^6] do not show any dust continuum emitters besides cid_346 within a FoV of $16\ensuremath{''}$.

Furthermore, there is no clear indication that cid_346 is in a galaxy pair or in a merging state. The target appears as a point source both in the COSMOS HST-Advanced Camera for Surveys data (rest-frame UV, PSF=$0.12''$) and in the UltraVista near-infrared data (seeing-limited, FWHM $\simeq0.78''$) (cite: Laigle+16). Even at longer wavelengths, cid_346 does not show close companions. Its rest frame 260-$\mu$m continuum emission ($870\mu$m observed frame) was imaged at $\sim2$ kpc resolution with a very high S/N ($\sim29$, (cite: Lamperti+21)) and resolved into a Gaussian distribution with half-light radius $R_e=1.81$ kpc and a possible additional central point source (a compact starburst or the AGN) contributing $\sim13$% to the flux.

## CO(3-2) moment maps

![image](aca_co32_mom0.pdf) ![image](aca_co32_mom1.pdf) ![image](aca_co32_mom2.pdf)

Figure [9](#fig:co32_aca_moment_maps) shows the ACA CO(3-2) moment maps. These were produced with the task `immoments` in CASA by selecting the velocity range $v\in[-300, 300]$ km s$^{-1}$and masking pixels below a flux threshold of 0.04 Jy beam$^{-1}$ km s$^{-1}$. Since it was produced by applying a flux and a velocity threshold, the moment 0 map (left panel of Fig. [9](#fig:co32_aca_moment_maps)) is biased against faint and high-velocity emission, and it is shown only for completeness. We refer to Fig [1](#fig:co32_aca_maps) for an unbiased, total CO(3-2) flux map.

The velocity map (middle panel of Fig. [9](#fig:co32_aca_moment_maps)) does not display a regular velocity gradient. However, about $15\ensuremath{''}$ north-east of the AGN position, it is possible to identify an extended region of predominantly redshifted emission with $150\lesssim v[\rm km~s^{-1}]<200$, and an average velocity dispersion of $\sigma_v\sim 120$ km s$^{-1}$. Almost symmetrically, $\sim15\ensuremath{''}$ south-west of the AGN, the CO(3-2) is mostly blueshifted, with $-250<v[\rm km~s^{-1}]\lesssim-200$ and an overall low velocity dispersion of $\sigma_v< 50$ km s$^{-1}$. In the central portion of the field, just south-west of the redshifted area, the moment 2 map shows a stripe of high-$\sigma_v$ CO emission extending towards the east, with $\sigma_v\gtrsim 200$ km s$^{-1}$. Other clear distinctive features of the moment maps are two spots of redshifted CO emission about $20\ensuremath{''}$ west of the AGN, offset in declination by $\Delta\delta\sim +10\ensuremath{''}$ and $\Delta\delta\sim -10\ensuremath{''}$, respectively, and two regions of high $\sigma_v\gtrsim200$ km s$^{-1}$ between them.

Interestingly, the velocity dispersion peaks are not centred on cid_346. This may favour accreting streams over the AGN-outflow interpretation for explaining the kinematics of the molecular CGM, since in the outflow scenario one would expect the $\sigma_v$ peak to coincide with the AGN position. However, we caution against an over-intepretation of Fig. [9](#fig:co32_aca_moment_maps) since the very large beam of ACA would dilute any kinematic signature of kiloparsec-scale outflows. In fact, the ACA resolution of 80 kpc is much larger than any ISM structure (disk, ring, or outflow) ever observed in molecular tracers. At this resolution, even the two largest detections of molecular CGM reservoirs prior to this work, that is the Spiderweb protocluster (70 kpc, (cite: Emonts+16)) and Candels-5001 (40 kpc, (cite: Ginolfi+17)), would be unresolved. Therefore, the kinematic features resolved by ACA around cid_346, shown in Figure [9](#fig:co32_aca_moment_maps), cannot be compared to anything known. Due to the poor resolution and low S/N of the data, none of these features can be studied in detail.

[^1]: claudia.cicone@astro.uio.no

[^2]: http://www.super-survey.org

[^3]: Measured from the broad, blue-shifted CIV emission component. The spectrum also exhibits a CIV broad absorption line (BAL).

[^4]: `http://www.iram.fr/IRAMFR/GILDAS`

[^5]: `http://www.apex-telescope.org/telescope/efficiency/`

[^6]: Project number 2018.1.00992.S, PI: C. Harrison

</paper>

Write the methods card for this paper.