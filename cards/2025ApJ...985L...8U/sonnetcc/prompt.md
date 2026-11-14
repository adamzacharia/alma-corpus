# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985L...8U\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985L...8U",
 "title": "ADF22-WEB: Detection of a Molecular Gas Reservoir in a Massive Quiescent Galaxy Located in a z ≍ 3 Protocluster Core",
 "year": 2025,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Umehata, Hideki",
 "n_authors": 3,
 "arxiv_id": "2502.06538",
 "doi": "10.3847/2041-8213/add1d4",
 "alma_projects_linked_by_archive": [
  "2013.1.00162.S",
  "2017.1.01332.S",
  "2023.1.01206.S"
 ]
}
```

Paper text:
<paper>
# ADF22-WEB: Detection of a molecular gas reservoir in a massive quiescent galaxy located in a $z\approx3$ proto-cluster core

## Abstract

We present a study of the molecular gas reservoirs and dust contents in three quiescent galaxies (QGs) located in the core of the $z=3.09$ SSA22 proto-cluster. Using the Atacama Large Millimeter/submillimeter Array (ALMA), we detect CO(3–2) emission in one galaxy, ADF22-QG1, marking the first direct detection of molecular gas in a quiescent galaxy from the early universe.

The detected galaxy, ADF22-QG1, has a molecular gas mass of log$M_{\rm H_2}$/M$_\odot = 10.26 \pm 0.07$ assuming a CO-to-H$2$ conversion factor $\alpha_{\rm CO} = 4.4$ (log$M_{\rm H_2}$/M$_\odot = 9.52 \pm 0.07$ for $\alpha_{\rm CO} = 0.8$), corresponding to a gas mass fraction of $f_{\rm gas} \approx 14\%$ (2.5%). The gas-to-dust ratio $\delta _{\rm gdr}\gtrsim170$ ($\delta_{\rm gdr}\gtrsim30$) for $\alpha_{\rm CO} = 4.4$ ($\alpha_{\rm CO} =0.8$) is also derived for the first time for a QG at the epoch.

For the other two galaxies, ADF22-QG2 and ADF22-QG3, non detections of CO(3–2) emission provide upper limits, $f_{\rm gas} \approx 17\%$ (3.1%) and $f_{\rm gas} \approx 13\%$ (2.4%), respectively.

The inferred gas-consumption history of ADF22-QG1, based on its star-formation history, suggests that (i) dusty star-forming galaxies (DSFGs) at $z = 4$–$6$ are plausible progenitors, and (ii) the cessation of gas accretion from cosmic web filaments plays an important role in their evolution to quenched systems. Furthermore, the presence of a detectable molecular gas reservoir in ADF22-QG1 indicates that additional mechanisms, such as morphological quenching, may be required to fully explain its quiescent nature.

# Introduction

To illustrate the formation and evolution of massive galaxies in the early universe is a key goal in modern astronomy. Over the past decade, spectroscopic confirmations of massive quiescent galaxies (QGs) at $z=3-5$ with $\log(M_*/M_\odot) \approx 10-11$ have been reported ((cite: 2012ApJ...759L..44G); (cite: 2017Natur.544...71G); (cite: 2018A&A...611A..22S); (cite: 2018A&A...618A..85S); (cite: 2020ApJ...890L...1F); (cite: 2020ApJ...889...93V); (cite: 2021ApJ...919....6K); (cite: 2022ApJ...935...89K); (cite: 2023Natur.619..716C); (cite: 2024ApJ...974..145S); (cite: 2024MNRAS.534..325C); (cite: 2024NatAs.tmp..284D); (cite: 2024MNRAS.534.3552S); (cite: 2024NatAs...8.1443D)). These findings reveal that mass assembly and quenching processes occur at significantly earlier times in cosmic history. Analyses of photometry and spectra suggest a history of active star formation followed by a quenching event (e.g., (cite: 2021ApJ...919....6K)). While dusty star-forming galaxies (DSFGs; for a review, see (cite: 2014PhR...541...45C)) with various levels of dust continuum detections are proposed as potential progenitors (e.g., (cite: 2020ApJ...889...93V)), the precise evolutionary pathways and quenching mechanisms remain unclear.

One critical missing piece of this puzzle is the molecular gas reservoir in QGs. While detections of CO lines have been reported for some QGs at $z\sim1$ ((cite: 2018ApJ...860..103S); (cite: 2021ApJ...908...54W); (cite: 2022ApJ...925..153B)), reliable detections of molecular gas tracers at higher redshifts remain elusive (e.g., (cite: 2023A&A...678L...9D); (cite: 2024arXiv240519401S)). Some studies have attempted to constrain molecular gas masses based on the (non-)detection of dust continuum (e.g., (cite: 2021Natur.597..485W)), but these efforts are hindered by uncertainties in the conversion factors between dust mass and molecular gas mass ((cite: 2019MNRAS.490.1425L); (cite: 2021ApJ...922L..30W)).

In this Letter, we present observations of three QGs at $z\sim3$ and the first detection of a molecular gas reservoir associated with a QG. The targets are located in ADF22 (“ALMA Deep Field in SSA22”, (cite: 2015ApJ...815L...8U); (cite: 2017ApJ...835...98U); (cite: 2018PASJ...70...65U)), the core region of the SSA22 protocluster at $z=3.09$ ((cite: 1998ApJ...492..428S); (cite: 2004AJ....128.2073H); (cite: 2005ApJ...634L.125M)). This region contains a dense galaxy group at $z\approx3.09$, referred to as the AzTEC14 group, originally identified as an AzTEC/ASTE source ((cite: 2009Natur.459...61T); (cite: 2014MNRAS.440.3462U)), located along Mpc-scale cosmic web gas filaments traced by Ly $\alpha$ in emission ((cite: 2019Sci...366...97U)). The AzTEC14 group hosts a variety of galaxies, including an LBG ((cite: 1998ApJ...492..428S)), DSFGs ((cite: 2015ApJ...815L...8U); (cite: 2017ApJ...835...98U)), and three QGs, ADF22-QG1, ADF22-QG2, and ADF22-QG3 ((cite: 2021ApJ...919....6K); (cite: 2022ApJ...935...89K)). One DSFG (ADF22.A4) and one QG (ADF22-QG2) have X-ray AGNs ((cite: 2009ApJ...691..687L); (cite: 2009MNRAS.400..299L)).

We adopt a standard concordance cosmology with $H_0=70$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.30$, and $\Omega_\Lambda=0.70$.

# Observation and Reduction

We observed the CO(3–2) line ($\nu_{\rm rest} = 345.796\,\mathrm{GHz}$) using ALMA toward the AzTEC14 group. The observations were conducted as part of ALMA project 2023.1.01206.S (PI: Umehata). The phase center was set to ($\alpha$, $\delta$) = (22h17m37.0s, 0d18m20.7s), corresponding to the position of a bright DSFG, ADF22.A4. The observations were performed over 21 runs during ALMA Cycle 10 (between January and September 2024) using the Band-3 receiver. A range of array configurations (C-1 to C-5) was employed. The total on-source integration time was 17 hours.

The correlator was configured with two spectral windows of 1.875 GHz bandwidth (dual polarization) per sideband, separated by 8 GHz. Each spectral window was centered at 85.03, 86.86, 97.03, and 98.86 GHz, respectively. Data reduction was performed using version 6.5.4 of the CASA software package ((cite: 2007ASPC..376..127M); (cite: 2022PASP..134k4501C)). Imaging was carried out using the CLEAN algorithm via the `tclean` task with natural weighting, down to $2\sigma$ with auto-masking. The resulting synthesized beam size was $3.00^{\prime\prime} \times 2.46^{\prime\prime}$ (PA = 87 deg). The typical rms noise level at the phase center was 33 $\mu$Jy beam$^{-1}$ per 100 km s$^{-1}$ channel at around 85 GHz.

The AzTEC14 group was also covered by a deep 1.1 mm mosaic ((cite: 2021ApJ...919....6K); S.Huang et al. in preparation) and observed with JWST/NIRCam (F115W, F200W, F356W, and F444W) as a part of the “ADF22-WEB” ((cite: 2024arXiv241022155U); (cite: 2025arXiv250201868U)). Fig. [1](#fig:alma_map) shows the NIRCam color image and 1.1 mm contours, exhibit the distributions of group member galaxies.

# Results

The CO (3–2) emission line associated with the three QGs was searched for using the deep Band-3 cube, resulting in a detection in the most massive galaxy, ADF22-QG1. Fig [1](#fig:alma_map) shows the CO(3–2) moment-0 map, where the flux was integrated across $\Delta v=600$ km s$^{-1}$ to fully cover the emission in ADF22-QG1. Figure [2](#fig:alma_spectra) presents the extracted spectra for the three QGs.

For ADF22-QG1, the CO(3–2) emission is detected at a significance level of 5.6$\sigma$, spatially overlapping with the stellar emission (Fig. [1](#fig:alma_map)). A single Gaussian fit to the spectrum yields $z_{\rm CO}=3.0889\pm0.0007$, which is broadly consistent with the previously reported redshift based on Balmer absorption lines ($z_{\rm abs}=3.0922_{-0.0004}^{+0.0008}$; (cite: 2021ApJ...919....6K)). The velocity dispersion is measured as $\sigma_{\rm gas}=180\pm50$ km s$^{-1}$, which is smaller than the stellar velocity dispersion $\sigma_*\approx320$ km s$^{-1}$ ((cite: 2021ApJ...919....6K)). Combined with the detection of disk components in stellar emission (Kubo et al., in preparation), this may suggest that the molecular gas distribution and kinematics are not identical as those of the stellar bulge components, which may be more centrally concentrated.

For the remaining two QGs, ADF22-QG2 and ADF22-QG3, the CO(3–2) emission was not significantly detected, although very marginal signals ($\sim2\sigma$) are identified at the expected peak frequency based on the \[O iii\] $\lambda 5007$ detections.

The total line intensity of ADF22-QG1 was measured as peak flux density in the moment-0 map, which was used to estimate the molecular gas masses $M_{\rm H_2}$. In the calculation we assumed the brightness temperature ratio $r_{31}=0.5$ ((cite: 2013MNRAS.429.3047B)) to evaluate the ground state CO luminosity and the two types of CO–H$_2$ conversion factor $\alpha_{\rm CO}$ to convert the measured CO luminosity to $M_{\rm H_2}$, $\alpha_{\rm CO}=4.4$ (for a Milkey-Way like galaxies) and $\alpha_{\rm CO}=0.8$ (for a ULIRG-like galaxies).

The derived molecular gas mass and fraction of ADF22-QG1 are $\log M_{\rm mol}/M_\odot=10.26\pm0.07$ and $\log M_{\rm mol}/M_\odot=9.52\pm0.07$ for $\alpha_{\rm CO}=4.4$ and 0.8, respectively (Table [1](#tab:measurement)).

To estimate upper limits for ADF22-QG2 and QG3, we created a pseudo narrow-band image for each with $\Delta v=500$ km s$^{-1}$[^1] and measured $3\sigma$ upper limits. Bright emission associated with DSFGs does not significantly contaminate the upper limit due to a velocity offset, as indicated in Figure [2](#fig:alma_spectra).

The measured upper limits are summarized in Table [1](#tab:measurement).

We updated the fits of ADF22 QGs with the SED models with parametric SFHs by using FAST$++$ ((cite: 2021ApJ...919....6K); (cite: 2022ApJ...935...89K)), incorporating new JWST photometry (Table [1](#tab:measurement), M. Kubo et al. in preparation for more details).

None of the three ADF22-QGs were significantly detected in the 1.1 mm dust continuum (Fig [1](#fig:alma_map)). The non detections place a $3\sigma$ point-source limit of $S_{\rm 1.1mm} <75$ $\mu$Jy ((cite: 2021ApJ...919....6K); S. Huang et al., in preparation), which provides a lough upper limit on $SFR_{\rm IR}\sim15$ M$_*$ yr$^{-1}$ ((cite: 2021ApJ...919....6K)). We also estimate upper limits on the dust mass $M_{\rm d}$, assuming the dust mass absorption coefficient $\kappa_{850}=0.05$ m$^{2}$ kg$^{-1}$ ((cite: 2003ARA&A..41..241D)), $\beta=2.0$ , and dust temperature of $T_{\rm d}=20$ K ((cite: 2021A&A...647A..33M)). The derived values are summarized in Table [1](#tab:measurement).

The dynamical mass of ADF22-QG1 is estimated as $M_{\rm dyn}=K_n K_q \sigma_*^2 r_e / G$ where $K_n$ and $K_q$ are scaling factor as a function of Sérsic index $n$ and axis ratio $q$, and $\sigma_*$ is the stellar velocity dispersion and $r_e$ is the effective radius ((cite: 2022ApJ...936....9V)). The measurements of the galaxy ((cite: 2021ApJ...919....6K); M. Kubo et al. in preparation) provides $M_{\rm dyn}\approx(2\pm0.5)\times 10^{11}$ M$_\odot$. The sum of $M_*$, $M_{\rm H_2}$, and the dark matter mass $M_{\rm DM}$ (assumed to be 10–20% of $M_{\rm dyn}$; e.g., (cite: 2017Natur.543..397G)) does not exceed $M_{\rm dyn}$ within the uncertainties for either case with $\alpha_{\rm CO}=4.4$ or 0.8.

# Discussion

Fig. [3](#fig:gas_dust) presents the physical parameters derived for ADF22 QGs in comparison with other star-forming galaxies and QGs. The three ADF22 QGs are classified as quenched galaxies regardless of the SFR tracers used (Fig. [3](#fig:gas_dust)a; see also (cite: 2021ApJ...919....6K); (cite: 2022ApJ...935...89K)).

Fig. [3](#fig:gas_dust)b indicates that ADF22-QG1 exhibits a significantly lower SFR as inferred from the CO(3–2) line luminosity ($L^{\prime}_{\rm CO(3-2)}$) than expected for a typical star-forming galaxy (e.g., (cite: 2013ApJ...768...74T)), suggesting suppressed star formation despite the presence of molecular gas.

Fig. [3](#fig:gas_dust) also constrains the gas-to-dust ratio, $\delta_{\rm gdr}=M_{\rm H_2}/M_{\rm d}$. As shown in Fig. [3](#fig:gas_dust)c, we derive $\delta_{\rm gdr} \gtrsim 170$ ($\delta_{\rm gdr} \gtrsim 30$) for $\alpha_{\rm CO}=4.4$ ($\alpha_{\rm CO}=0.8$) in ADF22-QG1. Models predict that QGs at high redshift may have significantly higher values ($\delta_{\rm gdr} \gtrsim 500$–$1000$) compared to star-forming galaxies ($\delta_{\rm gdr} \sim 50$–$100$) ((cite: 2021ApJ...922L..30W); see also (cite: 2019MNRAS.490.1425L)). This discrepancy could arise from the rapid destruction of dust in quiescent galaxies (e.g., via thermal sputtering and shocks from supernovae), which occurs more quickly than the depletion of molecular gas ((cite: 2021ApJ...922L..30W)).

The current constraint, which has been obtained for a QG at high redshift for the first time, may not be sufficient, and a more sensitive dust continuum survey will be crucial for critically testing this prediction.

Fig [4](#fig:fgas) summarizes the gas mass fraction ($f_{\rm gas}=M_{\rm H_2}/M_*$) of QGs at $z\gtrsim1$ from the literature ((cite: 2018ApJ...860..103S); (cite: 2021ApJ...908...54W); (cite: 2021ApJ...909L..11B); (cite: 2022ApJ...940...39W); (cite: 2024arXiv240519401S)).

The measurements for GS-10578 at $z=3.064$ ((cite: 2024arXiv240519401S)) were rescaled with $\alpha_{\rm CO}=4.4$ (and $\alpha_{\rm CO}=0.8$), $r_{31}=0.5$, and $\Delta v = 500$ km s$^{-1}$ for consistency with the ADF22-QGs and other $z\sim1$ QGs.

As shown, the CO detection from ADF22-QG1 at $z=3.09$ provides a unique and invaluable opportunity to investigate the formation processes of these massive, passive populations in the early universe at $z\gtrsim3$.

In Fig [4](#fig:fgas), we present two toy models of the evolution of $f_{\rm gas}$ in a closed box system (i.e., no net inflow or outflow), assuming no additional external gas supply exceeding the amount of outflow (e.g., from the cosmic web). The first model assumes a constant depletion timescale ((cite: 2021ApJ...908...54W)). The dashed red curves in Fig [4](#fig:fgas) show the model tracks with constant $t_{\rm dep}=0.5$ and 0.25 Gyr. The second model, shown with solid and dot-dashed lines, is derived from the star-formation history obtained in a non-parametric manner by (cite: 2021ApJ...919....6K) [^2], simply assuming that molecular gas mass was converted to stellar mass at a rate identical with star-formation rate ((cite: 2024arXiv240519401S)).

In Fig [4](#fig:fgas), we also show the scaling relation of $f_{\rm gas}$ derived by (cite: 2020ARA&A..58..157T) for star-forming galaxies with log$M_*$/M$_\odot=11$ at $z=1-3$. Additionally, we present the observed values of $f_{\rm gas}$ for DSFGs at $z\sim4-6$ ((cite: 2020ApJ...895...81R); (cite: 2021ApJ...907...62R); (cite: 2020A&A...640L...8U); (cite: 2021MNRAS.501.3926B); (cite: 2024ApJ...961..226L); (cite: 2024ApJ...961...69S)), with gas masses rescaled using $\alpha_{\rm CO}=1$.

As shown, both types of model tracks predict progenitors with $f_{\rm gas}$ broadly consistent with the observed DSFGs and the extrapolated scaling relations. This result suggests that (some of) DSFGs at $z=4-6$ are progenitors of massive QGs at $z\sim3$, in line with recent works based on different evidence, such as star-formation histories and cosmic volume densities (e.g., (cite: 2020ApJ...889...93V); (cite: 2020A&A...640L...8U); (cite: 2021ApJ...919....6K)). This trend is not sensitive to adopted $\alpha_{\rm CO}$ (Fig [4](#fig:fgas)).

For the other three QGs which only have upper limits on molecular gas contents , ADF22-QG2/QG3 and GS-10578 ((cite: 2024arXiv240519401S)), such a scenario could also be applicable.

It is worth noticing that the AzTEC14 group is located within the cosmic web filaments and includes both DSFGs and QGs (Fig. [1](#fig:alma_map), (cite: 2019Sci...366...97U)). This might be weird: if abundant gas accretion were still occurring and fueling DSFGs in this group, it would challenge the passive nature of QGs, as the accreted gas could potentially reignite star formation in QGs. The observed situation can be explained if the cessation of cold gas accretion from the cosmic web filaments could occur at some point, possibly due to heating associated with virial shocks and/or starburst/AGN activity, and DSFGs are also on a track to a quiescent system (of various stages), consuming their existing gas reservoirs.

This scenario further aligns with the following observational clues: First, the fact that ADF22-QG1, QG2, and QG3 are closely located to each other and belong to a same galaxy group suggests a common mechanism driving their evolution. Second, Ly $\alpha$ emission from the filaments is relatively faint in this region ((cite: 2019Sci...366...97U)) in contrast with the high density of member galaxies (suggestive of plentiful amount of ionizing photons). This indicates limited availability of cool gas in the filaments for effective Ly $\alpha$ emission. Third, the large velocity dispersion within the group suggests the presence of a (nearly) collapsed massive halo with $M_{\rm vir}\sim10^{13.4-14}$ M$_\odot$ ((cite: 2016MNRAS.455.3333K)), which hosts at least two X-ray AGNs ((cite: 2009MNRAS.400..299L); (cite: 2009ApJ...691..687L)) as possible heating sources. This massive halo may be sufficiently heated to suppress cold accretion.

Thus the gas starvation scenario likely plays a role in quenching, as highlighted by previous molecular gas studies of QGs ((cite: 2021ApJ...908...54W); (cite: 2024arXiv240519401S)). However, the detection of a molecular gas reservoir in ADF22-QG1, despite its quiescent nature (Fig. [3](#fig:gas_dust)b), suggests that star formation can be suppressed even in the presence of a significant amount of molecular gas. This suppression could be attributed to dynamical support preventing H$_2$ collapse. The stellar morphology of ADF22-QG1 is characterized by a combination of spheroidal and disk components (Sérsic index $n=2.88\pm0.30$ at F444W, M.Kubo et al. in preparation), which makes morphological quenching ((cite: 2009ApJ...707..250M)) a plausible mechanism for maintaining its quiescent state.

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | Coordinate | $z_{\rm spec}$ | line | log$M_*$ | $S_{\rm CO}dV$ | $M_{\rm H_2}^{\alpha4.4}$ | $M_{\rm H_2}^{\alpha0.8}$ | log$M_{\rm d}$ |
|  | ICRS |  |  | (M$_\odot$) | Jy m s$^{-1}$ | (M$_\odot$) | (M$_\odot$) |  |
| ADF22-QG1 | 22:17:37.25, +00:18:16.0 | 3.0922$_{-0.004}^{+0.008}$ | Bal. abs. | 11.11 | 45 $\pm$ 8 | 10.26 $\pm$ 0.07 | 9.52 $\pm$ 0.07 | $<8.02$ |
| ADF22-QG2 | 22:17:37.29, +00:18:23.4 | 3.0851 $\pm$ 0.0001 | \[O iii\], H$\beta$, \[O ii\] | 10.74 | $<23$ | $<9.97$ | $<9.23$ | $<8.02$ |
| ADF22-QG3 | 22:17:37.12, +00:18:17.8 | 3.0744 $\pm$ 0.0003 | \[O iii\] | 10.85 | $<23$ | $<9.97$ | $<9.23$ | $<8.02$ |

: Measured properties of ADF22-QGs

Table notes: Spectroscopic redshifts ($z_{\rm spec}$) are adopted from literatures ((cite: 2015ApJ...799...38K); (cite: 2021ApJ...919....6K); (cite: 2022ApJ...935...89K)). Stellar masses ($M_*$) are calculated using FAST$++$ (e.g., (cite: 2021ApJ...919....6K)), updating with JWST NIRCam photometry.

We thank Ian Smail for useful discussions.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST. These observations are associated with program #3547.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00162.S, #2017.1.01332.S,#2023.1.01206.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

HU acknowledges support from JSPS KAKENHI Grant Numbers 20H01953, 22KK0231, 23K20240.

This work was supported by NAOJ ALMA Scientific Research Grant Numbers 2024-26A.

natexlab

(ref: 2021ApJ...909L..11B) Belli, S., Contursi, A., Genzel, R., et al. 2021, ApJL, 909, L11, doi: [`10.3847/2041-8213/abe6a6`](http://doi.org/10.3847/2041-8213/abe6a6)

(ref: 2022ApJ...925..153B) Bezanson, R., Spilker, J. S., Suess, K. A., et al. 2022, ApJ, 925, 153, doi: [`10.3847/1538-4357/ac3dfa`](http://doi.org/10.3847/1538-4357/ac3dfa)

(ref: 2021MNRAS.501.3926B) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926, doi: [`10.1093/mnras/staa3862`](http://doi.org/10.1093/mnras/staa3862)

(ref: 2013MNRAS.429.3047B) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047, doi: [`10.1093/mnras/sts562`](http://doi.org/10.1093/mnras/sts562)

(ref: 2023Natur.619..716C) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023, Nature, 619, 716, doi: [`10.1038/s41586-023-06158-6`](http://doi.org/10.1038/s41586-023-06158-6)

(ref: 2024MNRAS.534..325C) Carnall, A. C., Cullen, F., McLure, R. J., et al. 2024, MNRAS, 534, 325, doi: [`10.1093/mnras/stae2092`](http://doi.org/10.1093/mnras/stae2092)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2014PhR...541...45C) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45, doi: [`10.1016/j.physrep.2014.02.009`](http://doi.org/10.1016/j.physrep.2014.02.009)

(ref: 2024NatAs.tmp..284D) de Graaff, A., Setton, D. J., Brammer, G., et al. 2024, Nature Astronomy, doi: [`10.1038/s41550-024-02424-3`](http://doi.org/10.1038/s41550-024-02424-3)

(ref: 2023A&A...678L...9D) D’Eugenio, C., Daddi, E., Liu, D., & Gobat, R. 2023, A&A, 678, L9, doi: [`10.1051/0004-6361/202347233`](http://doi.org/10.1051/0004-6361/202347233)

(ref: 2024NatAs...8.1443D) D’Eugenio, F., Pérez-González, P. G., Maiolino, R., et al. 2024, Nature Astronomy, 8, 1443, doi: [`10.1038/s41550-024-02345-1`](http://doi.org/10.1038/s41550-024-02345-1)

(ref: 2003ARA&A..41..241D) Draine, B. T. 2003, ARA&A, 41, 241, doi: [`10.1146/annurev.astro.41.011802.094840`](http://doi.org/10.1146/annurev.astro.41.011802.094840)

(ref: 2020ApJ...890L...1F) Forrest, B., Annunziatella, M., Wilson, G., et al. 2020, ApJL, 890, L1, doi: [`10.3847/2041-8213/ab5b9f`](http://doi.org/10.3847/2041-8213/ab5b9f)

(ref: 2017Natur.543..397G) Genzel, R., Förster Schreiber, N. M., Übler, H., et al. 2017, Nature, 543, 397, doi: [`10.1038/nature21685`](http://doi.org/10.1038/nature21685)

(ref: 2017Natur.544...71G) Glazebrook, K., Schreiber, C., Labbé, I., et al. 2017, Nature, 544, 71, doi: [`10.1038/nature21680`](http://doi.org/10.1038/nature21680)

(ref: 2012ApJ...759L..44G) Gobat, R., Strazzullo, V., Daddi, E., et al. 2012, ApJL, 759, L44, doi: [`10.1088/2041-8205/759/2/L44`](http://doi.org/10.1088/2041-8205/759/2/L44)

(ref: 2004AJ....128.2073H) Hayashino, T., Matsuda, Y., Tamura, H., et al. 2004, AJ, 128, 2073, doi: [`10.1086/424935`](http://doi.org/10.1086/424935)

(ref: 2015ApJ...799...38K) Kubo, M., Yamada, T., Ichikawa, T., et al. 2015, ApJ, 799, 38, doi: [`10.1088/0004-637X/799/1/38`](http://doi.org/10.1088/0004-637X/799/1/38)

(ref: 2016MNRAS.455.3333K) —. 2016, MNRAS, 455, 3333, doi: [`10.1093/mnras/stv2392`](http://doi.org/10.1093/mnras/stv2392)

(ref: 2021ApJ...919....6K) Kubo, M., Umehata, H., Matsuda, Y., et al. 2021, ApJ, 919, 6, doi: [`10.3847/1538-4357/ac0cf8`](http://doi.org/10.3847/1538-4357/ac0cf8)

(ref: 2022ApJ...935...89K) —. 2022, ApJ, 935, 89, doi: [`10.3847/1538-4357/ac7f2d`](http://doi.org/10.3847/1538-4357/ac7f2d)

(ref: 2009ApJ...691..687L) Lehmer, B. D., Alexander, D. M., Geach, J. E., et al. 2009a, ApJ, 691, 687, doi: [`10.1088/0004-637X/691/1/687`](http://doi.org/10.1088/0004-637X/691/1/687)

(ref: 2009MNRAS.400..299L) Lehmer, B. D., Alexander, D. M., Chapman, S. C., et al. 2009b, MNRAS, 400, 299, doi: [`10.1111/j.1365-2966.2009.15449.x`](http://doi.org/10.1111/j.1365-2966.2009.15449.x)

(ref: 2019MNRAS.490.1425L) Li, Q., Narayanan, D., & Davé, R. 2019, MNRAS, 490, 1425, doi: [`10.1093/mnras/stz2684`](http://doi.org/10.1093/mnras/stz2684)

(ref: 2024ApJ...961..226L) Liao, C.-L., Chen, C.-C., Wang, W.-H., et al. 2024, ApJ, 961, 226, doi: [`10.3847/1538-4357/ad148c`](http://doi.org/10.3847/1538-4357/ad148c)

(ref: 2021A&A...647A..33M) Magdis, G. E., Gobat, R., Valentino, F., et al. 2021, A&A, 647, A33, doi: [`10.1051/0004-6361/202039280`](http://doi.org/10.1051/0004-6361/202039280)

(ref: 2009ApJ...707..250M) Martig, M., Bournaud, F., Teyssier, R., & Dekel, A. 2009, ApJ, 707, 250, doi: [`10.1088/0004-637X/707/1/250`](http://doi.org/10.1088/0004-637X/707/1/250)

(ref: 2005ApJ...634L.125M) Matsuda, Y., Yamada, T., Hayashino, T., et al. 2005, ApJL, 634, L125, doi: [`10.1086/499071`](http://doi.org/10.1086/499071)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2023A&A...670A.138P) Popping, G., Shivaei, I., Sanders, R. L., et al. 2023, A&A, 670, A138, doi: [`10.1051/0004-6361/202243817`](http://doi.org/10.1051/0004-6361/202243817)

(ref: 2020ApJ...895...81R) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ, 895, 81, doi: [`10.3847/1538-4357/ab8c48`](http://doi.org/10.3847/1538-4357/ab8c48)

(ref: 2021ApJ...907...62R) Riechers, D. A., Nayyeri, H., Burgarella, D., et al. 2021, ApJ, 907, 62, doi: [`10.3847/1538-4357/abcf2e`](http://doi.org/10.3847/1538-4357/abcf2e)

(ref: 2024MNRAS.534.3552S) Sato, R. A., Inoue, A. K., Harikane, Y., et al. 2024, MNRAS, 534, 3552, doi: [`10.1093/mnras/stae2300`](http://doi.org/10.1093/mnras/stae2300)

(ref: 2024arXiv240519401S) Scholtz, J., D’Eugenio, F., Maiolino, R., et al. 2024, arXiv e-prints, arXiv:2405.19401, doi: [`10.48550/arXiv.2405.19401`](http://doi.org/10.48550/arXiv.2405.19401)

(ref: 2018A&A...611A..22S) Schreiber, C., Labbé, I., Glazebrook, K., et al. 2018a, A&A, 611, A22, doi: [`10.1051/0004-6361/201731917`](http://doi.org/10.1051/0004-6361/201731917)

(ref: 2018A&A...618A..85S) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018b, A&A, 618, A85, doi: [`10.1051/0004-6361/201833070`](http://doi.org/10.1051/0004-6361/201833070)

(ref: 2024ApJ...974..145S) Setton, D. J., Khullar, G., Miller, T. B., et al. 2024, ApJ, 974, 145, doi: [`10.3847/1538-4357/ad6a18`](http://doi.org/10.3847/1538-4357/ad6a18)

(ref: 2014ApJS..214...15S) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: 2018ApJ...860..103S) Spilker, J., Bezanson, R., Barišić, I., et al. 2018, ApJ, 860, 103, doi: [`10.3847/1538-4357/aac438`](http://doi.org/10.3847/1538-4357/aac438)

(ref: 1998ApJ...492..428S) Steidel, C. C., Adelberger, K. L., Dickinson, M., et al. 1998, ApJ, 492, 428, doi: [`10.1086/305073`](http://doi.org/10.1086/305073)

(ref: 2024ApJ...961...69S) Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69, doi: [`10.3847/1538-4357/ad07e3`](http://doi.org/10.3847/1538-4357/ad07e3)

(ref: 2020ARA&A..58..157T) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157, doi: [`10.1146/annurev-astro-082812-141034`](http://doi.org/10.1146/annurev-astro-082812-141034)

(ref: 2013ApJ...768...74T) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: 2009Natur.459...61T) Tamura, Y., Kohno, K., Nakanishi, K., et al. 2009, Nature, 459, 61, doi: [`10.1038/nature07947`](http://doi.org/10.1038/nature07947)

(ref: 2025arXiv250201868U) Umehata, H., Kubo, M., Smail, I., et al. 2025, arXiv e-prints, arXiv:2502.01868. [`https://arxiv.org/abs/2502.01868`](https://arxiv.org/abs/2502.01868)

(ref: 2014MNRAS.440.3462U) Umehata, H., Tamura, Y., Kohno, K., et al. 2014, MNRAS, 440, 3462, doi: [`10.1093/mnras/stu447`](http://doi.org/10.1093/mnras/stu447)

(ref: 2015ApJ...815L...8U) —. 2015, ApJL, 815, L8, doi: [`10.1088/2041-8205/815/1/L8`](http://doi.org/10.1088/2041-8205/815/1/L8)

(ref: 2017ApJ...835...98U) —. 2017, ApJ, 835, 98, doi: [`10.3847/1538-4357/835/1/98`](http://doi.org/10.3847/1538-4357/835/1/98)

(ref: 2018PASJ...70...65U) Umehata, H., Hatsukade, B., Smail, I., et al. 2018, PASJ, 70, 65, doi: [`10.1093/pasj/psy065`](http://doi.org/10.1093/pasj/psy065)

(ref: 2019Sci...366...97U) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97, doi: [`10.1126/science.aaw5949`](http://doi.org/10.1126/science.aaw5949)

(ref: 2020A&A...640L...8U) Umehata, H., Smail, I., Swinbank, A. M., et al. 2020, A&A, 640, L8, doi: [`10.1051/0004-6361/202038146`](http://doi.org/10.1051/0004-6361/202038146)

(ref: 2024arXiv241022155U) Umehata, H., Steidel, C. C., Smail, I., et al. 2024, arXiv e-prints, arXiv:2410.22155, doi: [`10.48550/arXiv.2410.22155`](http://doi.org/10.48550/arXiv.2410.22155)

(ref: 2020ApJ...889...93V) Valentino, F., Tanaka, M., Davidzon, I., et al. 2020, ApJ, 889, 93, doi: [`10.3847/1538-4357/ab64dc`](http://doi.org/10.3847/1538-4357/ab64dc)

(ref: 2022ApJ...936....9V) van der Wel, A., van Houdt, J., Bezanson, R., et al. 2022, ApJ, 936, 9, doi: [`10.3847/1538-4357/ac83c5`](http://doi.org/10.3847/1538-4357/ac83c5)

(ref: 2021Natur.597..485W) Whitaker, K. E., Williams, C. C., Mowla, L., et al. 2021a, Nature, 597, 485, doi: [`10.1038/s41586-021-03806-7`](http://doi.org/10.1038/s41586-021-03806-7)

(ref: 2021ApJ...922L..30W) Whitaker, K. E., Narayanan, D., Williams, C. C., et al. 2021b, ApJL, 922, L30, doi: [`10.3847/2041-8213/ac399f`](http://doi.org/10.3847/2041-8213/ac399f)

(ref: 2021ApJ...908...54W) Williams, C. C., Spilker, J. S., Whitaker, K. E., et al. 2021, ApJ, 908, 54, doi: [`10.3847/1538-4357/abcbf6`](http://doi.org/10.3847/1538-4357/abcbf6)

(ref: 2022ApJ...940...39W) Woodrum, C., Williams, C. C., Rieke, M., et al. 2022, ApJ, 940, 39, doi: [`10.3847/1538-4357/ac9af7`](http://doi.org/10.3847/1538-4357/ac9af7)

[^1]: Although ADF22-QG2 exhibits two emission line peaks as reported in (cite: 2015ApJ...799...38K), we adopt $z_{\rm [OIII]}=3.0851$, which is the most dominant peak.

[^2]: We scaled the star-formation rate to match the stellar mass estimate with that of FAST++.

</paper>

Write the methods card for this paper.