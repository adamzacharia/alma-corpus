# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...695A..23S\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...695A..23S",
 "title": "Molecular gas and dust properties in z &gt; 7 quasar hosts",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Salvestrini, Francesco",
 "n_authors": 15,
 "arxiv_id": "2412.02688",
 "doi": "10.1051/0004-6361/202453226",
 "alma_projects_linked_by_archive": [
  "2018.1.01188.S",
  "2019.1.00074.S",
  "2019.1.01025.S",
  "2019.A.00017.S",
  "2021.1.00934.S",
  "2021.1.01262.S"
 ]
}
```

Paper text:
<paper>
# Molecular gas and dust properties in $z>7$ quasar hosts

# Introduction

The significant role of quasars in reionizing the Universe at $z>6$ has been known for many years (cite: GunnPeterson65). However, our understanding has advanced considerably over the past couple of decades, paralleling the growth in the number of known quasars, which now includes approximately 300 identified at the epoch of reionization (cite: Fan23). This has been achieved thanks to the combination of near-infrared photometric surveys and spectroscopic follow-up observations, which have proven to be reliable tools for discovering the quasar population at high redshifts ($z>5$; e.g., (cite: Banados16; Shen19)).

Luminous quasars at the EoR are also crucial probes for testing the coevolution between supermassive black holes (SMBHs) and their host galaxies. In this regard, modern interferometric facilities have been essential for confirming the redshift of the objects and constraining the star formation activity and properties of the cold phase of the interstellar medium (ISM) of their host galaxies (e.g., (cite: Riechers06; Riechers07; Riechers09; WangR07; WangR10)). Far-infrared (FIR)/submillimeter observations have revealed the presence of highly star-forming host galaxies, with star formation rates (SFRs) of up to 1000-3000 M$_{\odot}$ yr$^{\rm -1}$, and copious amount of dust (M$_{\rm dust}>10^8$ M$_{\odot}$; (cite: Maiolino05; WangR13; Feruglio18; Pensabene22; Venemans17a; Venemans20)). These massive quasar hosts are crucial for benchmarking gas and dust content and star formation efficiencies (SFEs) during the mid-point and terminal stages of the EoR, but observations are still limited to a few tens of quasar hosts at these epochs. Furthermore, the scaling relation between gas and dust is not clear yet, and the methods that are currently adopted to derive molecular gas masses can be improved with more data. Given its brightness, the 158$\mu$m emission line of the singly ionized carbon atom (\[C ii\] hereafter) is the most used tracer of the ISM at $z>4$.

|  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:--:|:--:|:--:|:--:|
| Name | Ra,Dec | $z_{\rm \mbox{[C\,{\sc ii}]}~}$ | Freq. | Beam | R.m.s. | S$_\nu$ | Size |
|  | h:m:s, d:m:s (J2000.0) |  | \[GHz\] | \[arcsec$^2$\] | \[$\mu$Jy/beam\] | \[$\mu$Jy\] | \[arcsec$^2$\] |
| J0313-1806 | 03:13:43.84, $-$18:06:36.40 | 7.6423 | USB 92.568 | $13.1\times 3.7$ | 48.5 | $<100.5^{(a)}$ |  |
|  |  |  | LSB 78.756 | $16.4\times 4.3$ | 46.3 | – |  |
|  |  |  | B6 219.911 | $0.62\times 0.44$ | 19 | $0.50\pm0.05$ | $0.71\times 0.55$ |
| J1243+0100 | 12:43:53.93, +01:00:38.50 | 7.0749 | USB 100.310 | $5.8\times2.3$ | 16.1 | $119\pm16$ |  |
|  |  |  | LSB 86.756 | $6.3\times2.8$ | 13.0 | $49.8\pm12.5$ |  |
|  |  |  | B6 235.364 | $0.62\times 0.50$ | 19 | $2.07\pm0.09$ | $0.78\times 0.72$ |
| J0038-1527 | 00:38:36.10, $-$15:27:23.60 | 7.034 | USB 100.821 | $6.2\times3.8$ | 22.3 | $<44.4^{(a)}$ |  |
|  |  |  | LSB 87.256 | $7.3\times 4.4$ | 19.8 | – |  |
|  |  |  | B6 236.562 | $0.62\times 0.55$ | 37 | $1.8\pm0.7$ | $1.9\times 1.2$ |
| J2356+0017 | 23:56:46.33, +00:17:47.30 | 7.01 | USB 101.373 | $4.6\times3.5$ | 15.8 | $54\pm15$ |  |
|  |  |  | LSB 87.756 | $5.4\times4.1$ | 13.4 | $<40.2$ |  |
| J0252-0503 | 02:52:16.64, $-$05:03:31.80 | 7.0006 | USB 101.491 | $5.6\times4.2$ | 19.0 | $123.4\pm17.8$ |  |
|  |  |  | LSB 87.756 | $6.6\times4.9$ | 15.6 | $76.9\pm14.9$ |  |
|  |  |  | B6 237.852 | $0.56\times0.40$ | 35 | $1.04\pm0.10$ | $0.72\times 0.55$ |

**Notes.** NOEMA fluxes are derived from a fit of the visibilities with a point source model. ALMA band 6 (B6) fluxes are the integrated emission of best-fit 2D Gaussian function model of the cleaned continuum map. Upper limits are at the 3$\sigma$ significance level. R.m.s. is estimated using a channel width of 20 MHz. $^{(a)}$ upper limits are computed for the merged USB+LSB continuum data.

While the \[C ii\] emission is undoubtedly useful for dynamical studies (e.g., (cite: WangR13; Decarli17; Venemans19; Venemans20; Neeleman21; WangF24)), it may not effectively trace the dense and cold components of the molecular gas, nor the star-forming regions (e.g., (cite: Pineda13; HerreraCamus18; Neeleman19; Bischetti24; Izumi24)). On the other hand, the rotational excited transitions of carbon monoxide (CO) are much more reliable probes of the dense cold $H_2$ and are pivotal when investigating the star formation process (cite: Kaasinen24). Despite being fainter than \[C ii\], CO lines have been successfully detected in massive quasar hosts at $z\sim6$ (e.g., (cite: WangR13; Decarli22)); however, they remain poorly sampled at the highest redshifts ($z>7$) of quasars, with only one confirmed individual detection (cite: Feruglio23) and a possible detection suggested by the stacking of multiple lines (cite: Venemans17a; Novak19) at $z\sim7.1-7.5$.

In this work we present new observations targeting CO(6-5) and (7-6) emission lines and the underlying continuum in five quasars at $z > 7$, obtained with the Northern Extended Millimeter Array (NOEMA), thus providing a complete census of the molecular gas in the population of $z>7$ quasars known to date (cite: Fan23). We also investigated the star formation activity and dust properties for the five quasars by modeling the FIR spectral energy distribution (SED) using NOEMA and archival observations of the Atacama Large Millimeter/submillimeter Array (ALMA). Based on these measurements, we studied the growth of host galaxies and the implications for their coevolution with SMBHs in the reionization era.

This paper is organized as follows. Section [2](#sec:obs) describes the observations and data reduction. Section [3](#sec:results) describes the procedures adopted to model the FIR SED and, in turn, measure the dust and cold molecular gas content, including a new calibration using the \[CII\] luminosity. In Sect. [4](#sec:discussion) we discuss the results and their implication for the coevolution of the host galaxy of quasars at the EoR, and compare them with objects at lower redshifts and the results from semi-analytic models (SAMs). We summarize the paper in Sect. [5](#sec:concl).

Throughout the paper, we adopt a standard flat ${\rm \Lambda}$ cold dark matter cosmology with the matter density parameter ${\rm \Omega_{M}} = 0.30$, the dark energy density parameter ${\rm \Omega_{\Lambda}}= 0.70$, and the Hubble constant H$_{\rm 0} = 70$ km s$^{\rm -1}$.

# Sample and observations

We focused on the quasars with $z\geq7$, which are eight in total according to (cite: Fan23), aiming to obtain a complete census of the molecular gas content in these objects. The five quasars for which we acquired new NOEMA observations under project S23CX are listed in Table [\[tab:observations\]](#tab:observations), while the entire list of $z>7$ quasars with their names and identifications are reported in Table [\[tab:properties\]](#tab:properties).

Regarding project S23CS, receivers were tuned to detect the CO(6–5) and CO(7–6) and the underlying continuum in the lower and upper side band (LSB and USB), respectively. We calibrated the visibilities using the CLIC pipeline of the GILDAS software[^1]. Imaging was performed with MAPPING in GILDAS, using a natural weighting scheme for visibilities, with a detection threshold equal to the noise of the pre-imaging visibilities. The observation targeting quasar J0313 was executed in bad weather conditions, so it did not reach the requested sensitivity to detect either continuum emission or CO lines in both LSB and USB. Given the low declination of J0038 (coordinates are listed in Table [\[tab:observations\]](#tab:observations)), the observation of this target was limited by shadowing, which reduced the total observing time on-source, hence the final sensitivity. In these two cases, we merged LSB and USB to increase the signal-to-noise ratio, and we used the merged cube to extract an upper limit on the continuum emission. Continuum-subtracted cubes were binned to spectral resolutions of 20 MHz, corresponding to $\sim60$ km s$^{-1}$, to optimize the sensitivity.

To extend the sampling of the FIR emission of the quasar host galaxies, we collected archival ALMA observations for four of the five quasars[^2], which cover sky frequencies $\sim220-240$ GHz, where the \[C ii\] emission line falls. ALMA-calibrated visibilities of observations covering \[C ii\] and the underlying continuum were retrieved from the science archive (see the acknowledgements for the list of ALMA project IDs). The imaging was performed through the Common Astronomy Software Applications (CASA; (cite: McMullin07)), version 6.5.5-21. We ran `tclean` procedures using natural weighting, a 3$\sigma$ cleaning threshold, and a channel width of 20 MHz. Continuum-subtracted cubes and continuum maps were created using the *imfit* procedure in CASA, fitting a constant function to all line-free channels.

The synthesized beams, root-mean-square (rms) noise levels, and representative frequencies of the continuum maps are reported in Table [\[tab:observations\]](#tab:observations). Continuum maps of ALMA and NOEMA observations are shown in Fig. [8](#fig:cont_maps).

![](figures/plots/Redshift_evolution_2_panels.png)

![](figures/plots/SFR_CII_Zanella.png)

# Results

## Dust properties and star formation rates

The continuum maps of the five targets are presented in Fig.[8](#fig:cont_maps). We measured continuum flux densities of NOEMA maps with a fit of the visibilities with a point source model. The associated error accounts for both the statistical uncertainty of the fit and the calibration error ($\lesssim10\%$[^3]). For J0252, J1243, and J2356, we also measured the continuum flux by integrating the 2D Gaussian function that fits the cleaned continuum emission map. The two approaches provide flux estimates that are consistent within the uncertainties. In the case of the NOEMA observations, the observing setup did not allow us to spatially resolve the target extension, all best-fit functions are consistent with a point-like source having a size comparable with the beam (see Table [\[tab:observations\]](#tab:observations)). Flux upper limits are estimated at a 3$\sigma$ significance level using the rms noise and assuming a size equal to the beam size.

As visible in Fig.[8](#fig:cont_maps), ALMA observations of J0038, J0313, J0252, and J1243 spatially resolve the extent of the continuum emission. This allowed us to measure the size of the continuum emitting region in quasar host galaxies by modeling the continuum maps with a 2D Gaussian function. In Table [\[tab:observations\]](#tab:observations), we report the integrated flux and host-galaxy size, which is assumed to be equal to the full width half maximum (FWHM) of the best-fit 2D Gaussian function.

Using EOS-Dustfit[^4], we fitted the cold dust SED of the target galaxies. In EOS-Dustfit, following the prescription by (cite: DraineLi07), the cold dust continuum emission is modeled with a modified blackbody (MBB) function, assuming an optically thin regime. The MBB model can have up to three free parameters, namely dust temperature ($T_d$), dust mass ($M_d$), and the emissivity index ($\beta$). However, for the five sources of our sample, the limited amount of data prevents us from modeling the FIR SED with three free parameters. In particular, the peak of the SED is not sampled by current data, making it challenging to constrain the dust temperature. Consequently, we adopted a fixed temperature, $T_d=55$ K, for all five quasars based on the mean dust temperature in a sample of 10 $z>6$ quasars (cite: Tripodi24b). This assumption is further supported by recent literature results on $z>6$ quasars (e.g., (cite: Decarli22), (cite: Sommovigo22a), (cite: Shao22), (cite: Witstok23), and (cite: Tripodi23b)) and lower-z quasars with measured $T_{d}$ (e.g., (cite: Bischetti21)), as it would be expected in the case of compact, and dense star-forming regions (dust sizes of few kiloparsecs; e.g., (cite: Venemans17a), (cite: Decarli18), (cite: Decarli22), and (cite: Tripodi24b)). Their intense star formation still stands even after accounting for the active galactic nucleus (AGN) contribution to the dust heating, which can be substantial, especially in the nuclear region ((cite: Duras17), (cite: DiMascia21), (cite: Walter22), and (cite: Tsukui23)).

Combining NOEMA and ALMA detections in the observed-frame $\sim$80-230 GHz range, we estimated the dust emissivity parameter, $\beta,$ for two objects in our sample (J0252 and J1243). For the others, we fixed $\beta=1.6$, the local value ((cite: Beelen06) and (cite: Witstok23)) and similar to that measured in J0252 and J1243. Since NOEMA observations do not allow us to resolve the source size, we assumed that the size does not vary significantly with frequency in the observed range $\sim80$ GHz to $\sim 230$ GHz. Quasar J2356 only has an unresolved observation at 3 mm (Fig. [8](#fig:cont_maps)). Then, we assumed a size of $0.75\times0.64$ arcsec$^{\rm 2}$, based on the median value of the FWHM dimensions measured for the four quasars of our sample with ALMA observations.

EOS-Dustfit explores the parameter space for each SED using a Markov chain Monte Carlo algorithm implemented in the *emcee* package (cite: emcee1). A uniform distribution for priors is assumed for fitting parameters in the range: $5<\log(M_{d}/M_{\odot})<9$ for all the quasars, and $0.5<\beta<3.0$ for both J0252 and J1243. We ran 40 chains, with 3000 trials and a burn-in phase of 150 steps for each dataset; we added in quadrature a 10% calibration uncertainty to the continuum flux errors. The upper limits of the continuum emission were included in the fit as a 1$\sigma$ detection with a 2$\sigma$ error. There is not yet a standard approach for dealing with upper limits in the fitting procedure, one could either treat them as detections with large errors (as we do; see also, e.g., (cite: Witstok22) and (cite: Ronconi24)) or change the fitting code properly to ensure that above the upper limit level, the likelihood is zero. We adopt the first method given that it is commonly employed in many fitting routines (e.g., GalaPy and MERCURIUS) and gives us reasonable results. We adopted the 50th percentile of the posterior distribution as the best-fit value, while the errors are calculated considering the 16th and 84th percentiles (corner plots of the posterior distribution of free parameters are shown in Fig. [6](#fig:corner_plots)). In the case of the modeling of FIR SED assuming a fixed $\beta$, the uncertainties on $\rm M_{d}$ are relatively small (see below) when compared to the fit where $\beta$ is left free to vary. This is because of the marginalization over the distribution of $\beta$. To determine with accuracy to which extent the uncertainty on $\rm M_{d}$ and $\rm L_{FIR}$ may be underestimated due to marginalization on $\beta$, we performed additional fits for J0252 and J1243, this time setting $\beta=1.6$. We then obtained uncertainties on $\rm M_{d}$ and $\rm L_{FIR}$ lower by $\sim0.05$ dex. A similar conclusion can be reached for the assumption of $T_d$, leaving it free to vary over a limited range of temperature ($T_d=40-70$ K). In Sect. [3](#sec:results) we take care of this systematic by including an additional contribution to the error on $\rm M_{d}$ and $\rm L_{FIR}$. The results from the SED fitting are reported in Tab. [\[tab:properties\]](#tab:properties), while the best-fit models are shown in Fig. [5](#fig:fir_sed). We measured the FIR luminosity ($L_{FIR}$) by integrating the 40-1000 $\mu$m emission of the best-fit model produced by EOS-Dustfit in the five quasars. SFR is computed with the relation by (cite: Kennicutt98), $SFR/(M_{\odot}\,yr^{-1}) = 10^{-10}\,L_{FIR}/L_{\odot}$, assuming a Chabrier initial mass function (IMF; (cite: Chabrier03)). The same prescription is commonly assumed in high-z quasars (e.g., (cite: Duras17), (cite: Bischetti21), and (cite: Bertola24)), and is roughly consistent with the SFR derived assuming a (cite: Kroupa01) IMF (within $7\%$). A Chabrier IMF was also adopted for J1007 by (cite: Feruglio23) and J1342 by (cite: Novak19), while (cite: Venemans17a) assumed a Kroupa IMF for J1120.\
In two cases we modeled the dust emissivity index, for J1243 the best-fit value derived is fully consistent with the typical value observed in high-redshift quasars ( (cite: Beelen06), (cite: Venemans17a), (cite: Venemans20), and (cite: Tripodi24b)). For J0252, we derived $\beta=0.93^{+0.20}_{-0.21}$, which is significantly lower (4$\sigma$) than $\beta$ values measured in high-z quasars. A potential reason for the flat FIR SED in J0252 could be the presence of contaminant sources within the beam of the NOEMA observation (see Fig. [8](#fig:cont_maps)). Indeed, the ALMA continuum map of J0252 (see Fig. [8](#fig:cont_maps)) shows a marginally resolved source surrounded by elongated emission features, each detected with $>2\sigma$ significance level. These emission features may either hide the presence of close companion galaxies or interloper sources. However, the relatively low $\beta$ value obtained from the fit does not significantly affect the $\rm M_{d}$ estimate. Assuming $\beta=1.6$ for J0252, we obtained a $\rm M_{d}$ fully consistent with the one presented in Table [\[tab:properties\]](#tab:properties).\
We tested the consistency of our assumptions (namely, $T_d$, $\beta$) on the results of the SED fitting. Using a higher (lower) dust temperature such as $T_d=70$ K (40 K) would have led to an average decrease (increase) in $\rm M_{d}$ by a factor of $\sim1.5$ ($\sim0.18$ dex), while the value of $\rm L_{FIR}$ would have been higher (lower) by a factor of $\sim2$ ($\sim0.3$ dex). Regarding $\beta$, assuming a steeper emissivity index ($\beta=2$) for the targets with $\beta$ fixed (namely, J0038, J0313, and J2356) would have resulted in a larger $\rm M_{d}$ (lower $\rm L_{FIR}$) by a factor of $\sim2$. The results of the modeling assuming different $\beta$ and $T_d$ values are shown in Fig. [7](#fig:fir_sed_multi_par). Conversely, choosing a flatter $\beta$ ($\beta=1.2$) results in a mean increase (decrease) in the value of $\rm M_{d}$ ($\rm L_{FIR}$) by a factor of $\leq1.2$. Eventually, we tested the impact of assuming a different source size: increasing the source area up to a factor of 10 provided results consistent within the uncertainties with those listed in Table [\[tab:properties\]](#tab:properties); if the source area was overestimated by a factor of 10 or more, this would have led to $\rm M_{d}$ and $\rm L_{FIR}$ being lower by a factor of $\geq2$.

The five quasars in our sample show $\rm M_{d}$ in the range $0.6-4\times10^{8}$ M$_{\odot}$ (see Fig. [1](#fig:mass_redshift) and Table [\[tab:properties\]](#tab:properties)), consistent with the dust content derived in the population of luminous quasars at the EoR (e.g., (cite: Izumi21; Witstok23; Tripodi24b)) and at different cosmic epochs (e.g., (cite: Duras17), (cite: Bischetti21), and (cite: Bertola24)), and star-forming galaxies at lower redshifts (e.g., (cite: Mancini15), (cite: Lesniewska19), (cite: Pozzi21), (cite: Hygate23), (cite: Algera24)). As shown in Fig.[1](#fig:mass_redshift), comparing quasars at $z>7$ and sources at later epochs, there is no clear evolution of $\rm M_{d}$ as a function of the redshift. The quasars in our sample have already built large dust masses in a relatively short time (the Hubble time at $z\sim7$ is $\sim800$ Myr), suggesting that in high-z quasar hosts the physical processes that drive the formation of dust grains are very efficient and overtake those processes destroying dust particles (e.g., (cite: Popping17)). We continue the discussion on the dust formation processes in Sect. [4.1](#sec:gdr).

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | ID | logM$_{BH}$ | logL$_{\rm bol}$ | $\beta$ | logM$_{\rm dust}$ | log(L$_{FIR}$) | SFR | logM$_{\rm H2}$ | Ref. |  |
|  |  | M$_{\odot}$ | L$_{\odot}$ |  | M$_{\odot}$ | L$_{\odot}$ | M$_{\odot}$ yr$^{\rm -1}$ | M$_{\odot}$ |  |  |
| J0313-1806 | J0313 | 9.2 | 13.6 | 1.6 | $7.8^{+0.1}_{-0.1}$ | $12.20^{+0.05}_{-0.05}$ | $160^{+20}_{-20}$ |  | 1 |  |
| J1243+0100 | J1243 | 8.2 | 12.6 | $1.97^{+0.19}_{-0.21}$ | $8.0^{+0.2}_{-0.1}$ | $12.68^{+0.10}_{-0.09}$ | $475^{+170}_{-160}$ | $<9.96$ | 1 |  |
| J0038-1527 | J0038 | 9.3 | 13.7 | 1.6 | $8.1^{+0.1}_{-0.1}$ | $12.43^{+0.07}_{-0.07}$ | $270^{+75}_{-70}$ | $<10.16$ | 1 |  |
| J2356+0017 | J2356 |  |  | 1.6 | $8.0^{+0.1}_{-0.1}$ | $12.56^{+0.11}_{-0.11}$ | $370^{+120}_{-110}$ | $<10.05$ | 1 |  |
| J0252-0503 | J0252 | 9.3 | 13.5 | $0.93^{+0.20}_{-0.21}$ | $8.6^{+0.2}_{-0.1}$ | $12.68^{+0.03}_{-0.03}$ | $476^{+36}_{-37}$ | $<10.14$ | 1 |  |
| J1120+0641 | J1120 | 9.4 | 13.8 |  | $7.93\pm0.03$ | $12.2^{+0.03}_{0.03}$ | $220^{+15}_{-15}$ | $<10.1$ | 2 |  |
| J1007+2115 | J1007 | 9.2 | 13.7 |  | $8.32\pm12$ | 12.2 | 165 | $10.26\pm0.04$ | 3,4 |  |
| J1342+0928 | J1342 | 8.9 | 13.6 |  | $7.54\pm0.02$ | 12 | 150 | $<9.5$ | 5 |  |

**Notes.** Quasars at $z>7$ known to date (cite: Fan23). From left to right, columns include source name, ID adopted throughout the paper, logarithm of the black hole mass, logarithm of bolometric luminosity, dust emissivity index, logarithm of the dust mass, and 40-1000 $\mu$ infrared luminosity, SFR and logarithm of the molecular gas mass. We refer to Table 1 in (cite: Fan23) for the references for $M_{BH}$ and $L_{bol}$ for all $z>7$ quasars. References for $M_{H2}$, \[CII\], and IR measurements are (1) This work; (2) (cite: Venemans17a); (3) (cite: Feruglio23); (4) (cite: Yang20); (5) (cite: Novak19)

## Molecular gas mass

For four out of five quasars observed with NOEMA we derived 3$\sigma$ upper limits on the cold $H_2$ mass using the rms at the expected frequency of CO(6–5) and (7–6) emission lines. We assumed a line width of FWHM = 300 km/s, as expected for $z>6$ quasars (e.g., (cite: Decarli22) and (cite: Feruglio23)), and a galaxy size equal to the beam of the observations. We adopted the CO spectral line energy distribution (SLED) correction from (cite: Kaasinen24), that is, $r_{6,1}=0.92$ for CO(6-5) and $r_{7,1}=0.65$. Assuming a luminosity to mass conversion factor $\alpha_{co}=0.8$ M$_{\odot}$ (K km s$^{\rm -1}$ pc$^{\rm 2}$)$^{\rm -1}$ (see (cite: Bolatto13) and (cite: CarilliWalter13)), we derive an upper limit $M(H_2)$ in the range $\sim 0.9-1.5\times 10^{10}$ M$_{\odot}$ (see Table [\[tab:properties\]](#tab:properties)). The same $\alpha_{co}$ and CO SLED correction factor are adopted for the upper limits and estimate of the $H_2$ masses of J1007, J1120, J1342, for which we collected CO luminosity from the literature and included in Table [\[tab:properties\]](#tab:properties). Of the known quasars at $z \gtrsim 7$, five have only upper limits on their $H_2$ masses as traced by CO emission lines, with J1007 being the sole source with a statistically significant detection ($>6\sigma$) of molecular gas mass (cite: Feruglio23). The molecular gas mass and the upper limits for the $z>7$ quasars (see Table [\[tab:properties\]](#tab:properties) and Fig. [1](#fig:mass_redshift)) are consistent with the mean value measured in the population of $5<z<7$ quasars ($\log(M_{H2}/M_{\odot})\sim10\pm0.3$; e.g., (cite: Venemans17b; Decarli22; Kaasinen24)).

To test the consistency of our $\rm M_{H2}$ upper limits, we compared the CO-derived measurement with that obtained from the \[CII\]158$\mu$m (\[CII\], hereafter) luminosity. $\rm L_{[CII]}$ is a viable way to derive molecular gas masses for $z\gtrsim4$ non-AGN galaxies given its brightness and scaling relation between $\rm L_{[CII]}$ and $\rm M_{H2}$ calibrated on lower redshift samples. \[CII\] is expected to trace multiple gas phases (e.g., (cite: Maio22), (cite: Maio23), and (cite: Casavecchia24b)), but the corresponding emission is mostly due to the star formation activity in the host. As shown in the left panel of Fig. [2](#fig:cii_zanella), $\rm L_{[CII]}$ is tightly correlated (Pearson correlation coefficient $\sim0.71$) with the SFR in quasar host galaxies at $z>6$. The data points shown in Fig. [2](#fig:cii_zanella) include all quasar at $z>7$ and a collection of objects at $z\gtrsim6$ from the literature with both CO and \[CII\] measurements (see Table [\[tab:comp_sample_z6\]](#tab:comp_sample_z6) for the full list of objects and references). For this reason, several proposed relations use the $\rm L_{[CII]}$ to trace the molecular gas content based on the Kennicutt-Schmidt relation (cite: Kennicutt98). As an example, the relation by (cite: Zanella18) calibrated on MS and starburst galaxies at redshift up to $z\sim6$, with the bulk of the sample at $z\sim2$. Alternatively, the relation by (cite: Madden20) allows us to measure the total $\rm M_{H2}$, including the potential contribution due to CO-dark clouds, and is calibrated on local dwarf galaxies. As shown in the right panel of Fig. [2](#fig:cii_zanella), both relations overestimate significantly the $\rm M_{H2}$ measurement and upper limit derived from $\rm L^{\prime}_{CO}$ in quasars at $z>5$. Indeed, several works in the literature studying the ISM properties of $z>6$ quasars (e.g., (cite: Neeleman21), (cite: Decarli22), (cite: Kaasinen24), and (cite: Tripodi24b)) observed a large discrepancy between $\rm M_{H2}$ derived with the prescription by (cite: Zanella18) and (cite: Madden20) and CO-derived ones, with \[CII\]-based $\rm M_{H2}$ that overestimates CO-based $\rm M_{H2}$ from a factor of a few to one order of magnitude (e.g., (cite: Kaasinen24)). The discrepancies in the determination of $\rm M_{H2}$ from $\rm L_{[CII]}$ are likely due to the different physical properties of the ISM between the sample collected by (cite: Zanella18) and (cite: Madden20) and the host galaxies of high-z quasars. Indeed, when considering galaxies at high redshifts ($z\gtrsim4$) with an intense star formation activity (cite: Rizzo20; Rizzo21), the measured $\rm M_{H2}$-to-$\rm L_{[CII]}$ ratio is considerably lower ($\sim4-8$M$_{\odot}$$/$L$_{\odot}$) than the value $\sim30$ M$_{\odot}$$/$L$_{\odot}$ measured by (cite: Zanella18). This is also supported by the results of post-processed FIR emission lines from the SIMBA cosmological hydrodynamical simulations (cite: Vizgan22), suggesting that the $\rm M_{H2}$-to-$\rm L_{[CII]}$ ratio should be lowered by up to a factor of $\sim2$ for synthetic star-forming galaxies at $z\simeq6$.

Given that, we combined $L_{[CII]}$ and $\rm M_{H2}$ measurements and upper limits for the $z>7$ quasars presented in Table [\[tab:properties\]](#tab:properties) with measurements for 21 $z\gtrsim6$ quasars from the literature (see Table [\[tab:comp_sample_z6\]](#tab:comp_sample_z6)) to provide a new calibration for the $\rm M_{H2}$-$\rm L_{[CII]}$ relation. We fitted data points of the resulting quasar sample of 25 objects with a linear regression based on a Bayesian approach, using the Python package *linmix* (cite: linmix). This package allows us to consider errors on both variables, $L_{[CII]}$ and $\rm M_{H2}$, and upper limits on $\rm M_{H2}$. The best-fit relation is $$\begin{equation}
    \log(M_{H2}/M_{\odot}) = (0.75^{+0.31}_{-0.31} \log(L_{[CII]}) + (2.87^{+0.07}_{-0.07})
    \label{eq:mhcii}
\end{equation}$$ and is shown in Fig. [2](#fig:cii_zanella). The same relation corresponds roughly to a $\rm M_{H2}$-to-$\rm L_{[CII]}$ ratio of $\sim3.9^{+1.7}_{-2.3}$ in the $\rm L_{[CII]}$ regime $10^{9-10}$ L$_{\odot}$, almost one order of magnitude lower than that predicted by (cite: Zanella18). We note that even if we considered a Milky Way like CO-H$_{\rm 2}$ conversion factor ($\alpha_{CO}=4.3$ $\rm M_{\odot}\ pc^{-2}\ (K\ km\ s^{-1})^{-1}$) to derive $\rm M_{H2}$ for high-z quasars, the corresponding $\rm M_{H2}$ would be lower by a factor of 1.5-2 than those derived assuming the calibration of (cite: Zanella18). This relation provides $\rm M_{H2}$ estimates for luminous quasars ($L_{bol}>10^{46}$ erg/s) at $z>5$ that are way more accurate than those provided by scaling relation calibrated from star-forming or dwarf galaxies at lower redshifts.

While applying this relation to high-redshift quasars, it is crucial to consider the following factors: (i) large-scale ionized winds driven by the accreting SMBH could significantly boost the observed $\rm L_{[CII]}$ (e.g., (cite: Bischetti24)); (ii) tidally stripped gas due to merging companions close to the quasar (e.g., (cite: Tripodi24a; Decarli24)) could enhance $\rm L_{[CII]}$ measurements, especially in observations with limited angular resolution. Both (i) and (ii) cases could significantly overestimate the molecular gas masses in the quasar’s host galaxy.

![](figures/plots/GDR_singlepanel_v3.png)

# Discussion

## Dust enrichment at high redshifts

The origin of large dust reservoirs in the early Universe is widely debated (see (cite: SchneiderMaiolino24) for a comprehensive review on this topic), since there is no consensus on the dominant formation mechanisms. However, among the different channels for forming dust in the first few hundred million years of the Universe, asymptotic giant branch (AGB) stars and supernova (SN) ejecta are expected to contribute significantly even at $z>7$ (e.g., (cite: Sommovigo22a)). Even considering the maximally efficient yield from SN ejecta, this process can produce dust masses up to a few times $10^7$ M$_{\odot}$ at the redshift of our targets (cite: Mancini15; Valiante11). Nonetheless, we must also consider that a significant fraction of the dust created by SN ejecta (from 20% up to the total amount, depending on model assumptions; e.g., (cite: Micelotta18) and (cite: Kirchschlager19)) could be destroyed by the reverse shocks that may follow the initial explosion (cite: SchneiderMaiolino24). Regarding AGB stars, their contribution to dust production depends mostly on the gas metallicity and the IMF (e.g., (cite: Ventura18; DellAgli19b)), nevertheless it can reach up to 40% of the total dust at $z\gtrsim6$ (e.g., (cite: SchneiderMaiolino24)).

Moreover, two more processes are expected to significantly contribute to dust production in a pre-enriched ISM: aggregation and evolution of grains within the ISM, and quasar-driven winds. The aggregation of dust particles within the ISM usually requires timescales on the order of 1 Gyr and is observed to contribute up to 20-50% of the total dust production in the local Universe (cite: Saintonge18; Galliano21). However, the extremely dense and turbulent ISM in the host galaxy of quasars ( (cite: Gallerani10), (cite: Valiante11), (cite: Valiante14), (cite: Mancini15), (cite: Decarli23)) could favor the formation of massive dust particles in a fraction of that time, making it the dominant channel in massive systems (e.g., (cite: Mancini15)). Indeed, local studies suggest that the aggregation of dust grains in the ISM primarily depends on gas density and temperature (e.g., (cite: Draine03), (cite: Draine09), and (cite: Galliano21)). Given the luminosity of the quasar at the EoR included in this study, we cannot exclude that a non-negligible amount of dust grains that are produced and continue to grow within the outflowing clouds that are ejected due to the SMBH feedback (cite: Elvis02).

![](figures/plots/SFE_tdep.png)

Even if the role of this production channel is still debated (e.g., (cite: Pipino11)), recent results from hydrodynamical simulations (cite: Sarangi19) suggest that this mechanism can be quite efficient (up to few M$_{\odot}$ yr$^{-1}$ for a $M_{BH}=10^8$ M$_{\odot}$) in luminous quasars such as our targets. This means this channel can contribute to at least a few percent of the total dust budget, considering an AGN cycle of a million years. Although this makes dust production in quasar winds less significant than the other mechanisms just described, it could still play a crucial role in dust enrichment in nuclear regions. To conclude, building dust masses that exceed $10^8$ M$_{\odot}$ in the host galaxies of luminous quasars at redshift $z>7$ requires a combination of the physical processes described above.

As discussed above, the amount of dust traces the metal enrichment of the ISM. For this reason, the gas-to-dust ratio (GDR=$\rm M_{H2}$/$\rm M_{d}$) is a crucial parameter to understand the rapid evolution and growth of galaxies at EoR. Here, we adopted the $\rm M_{H2}$ measurement and upper limits listed in Table [\[tab:properties\]](#tab:properties) to derive the GDR for 7 out of 8 quasars at $z>7$, among which J1007 is the only object with a GDR estimate. We similarly derived GDRs for the quasars listed in Table [\[tab:comp_sample_z6\]](#tab:comp_sample_z6) and quasars with similar luminosity at Cosmic Noon from (cite: Bischetti21). Since the high-z quasar population with dust mass estimates are biased toward luminous objects at FIR wavelength, we also considered a sample of local Seyfert galaxies ($L_{FIR}\sim10^{10-12}$ L$_{\odot}$) to check for any potential selection bias. In Fig. [3](#fig:gdr), the resulting GDRs are shown as a function of $\rm M_{d}$. Globally, the population of quasars at the EoR shows GDRs that are consistent (GDR$_{\rm mean}=80\pm40$) with the local value GDR=100 (cite: DraineLi07), similar to that measured in local star-forming galaxies (e.g., (cite: Casasola20)). This local value is also commonly adopted at high redshifts to derive the molecular gas mass given the dust mass (e.g., (cite: Neeleman21)). Quasars at $z>7$ show upper limits on GDR that are consistent or just below the local value. J0252 shows the tighter constraint of GDR among $z>7$ targets, but it is still consistent with GDR values observed in similarly luminous quasars. We recall that assuming a higher (lower) $\rm T_{d}$ value would result in a higher (lower) GDR up to a factor of $\sim2$ with $\rm T_{d}$=65 K (45 K). Looking at Fig. [3](#fig:gdr), GDR decreases at increasing $\rm M_{d}$, with a similar trend in quasars at different epochs and Seyfert galaxies. Indeed, by fitting the GDR versus $\rm M_{d}$ with linmix, we find a negative slope ($=-0.41\pm0.16$) when considering only quasars at the EoR. Consistent results can be obtained by including either lower-redshift quasars (cite: Bischetti21) or local Seyfert galaxies ((cite: Salvestrini22); in the former case, there is a shift in the normalization). The decreasing trend is likely driven by the level of metal enrichment of the ISM, which is higher at higher dust reservoirs. This confirms that dust-rich systems are already enriched in metals, which are key ingredients of dust particles (cite: RemyRuyer14). However, we recall that our $\rm M_{H2}$ estimates are derived with a constant $\alpha_{CO}$ factor, while an assumption of a $\alpha_{CO}$ dependence on metallicity (e.g., (cite: Amorin16)) would have balanced out the GDR anticorrelation with $\rm M_{d}$. We conclude that quasars at the EoR exhibit GDR values (both detection and upper limits) consistent with those measured in quasars at lower redshifts and in local objects. This confirms that assuming a local GDR value (cite: DraineLi07) is a reasonable choice for quasar host galaxies up to $z \sim 7.5$.

## Gas depletion and star formation efficiency

In the top-left panel of Fig. [4](#fig:SFE), we show the depletion time ($t_{dep}=M_{H2}/SFR$) as a function of redshift. As a comparison, we include a collection of quasars spanning a wide range of redshift, namely: quasars at $6\lesssim z<7$ (see Table [\[tab:comp_sample_z6\]](#tab:comp_sample_z6)), luminous objects at Cosmic Noon from (cite: Bischetti18), (cite: Bischetti21), (cite: Decarli22), (cite: Bertola24), and Salvestrini et al., in prep, and in the nearby Universe (cite: Bischetti19a; Shangguan20). We also extend the comparison to AGN at intermediate luminosities ($L_{bol}\sim10^{44-45}$ erg/s), with samples of local AGN and Seyfert galaxies from (cite: Koss21) and (cite: Salvestrini22) and highly accreting AGN hosts from (cite: Salome23). Eventually, we added star-forming and luminous infrared galaxies with CO detections from (cite: Tacconi18), which cover a wide range of redshift, from the nearby Universe up to redshift $z \sim 4$. As is clearly visible, the quasars at the EoR show relatively low $t_{dep}$ values ($\lesssim0.1$ Gyr), with few objects reaching depletion times of a few tens of megayears. If we limit the analysis to the EoR, there is no evidence of the evolution of $t_{dep}$ in quasar host galaxies.

To further investigate this scenario, we contrasted our findings against theoretical predictions from the GAlaxy Evolution and Assembly (GAEA) model. In particular, the latest rendition of the model (cite: DeLucia24) combines the explicit partitioning of the cold gas into its molecular and neutral phases (the molecular gas ratio depends on the mid-plane pressure (cite: BlitzRosolowsky06), more details in (cite: Xie17)), with improved modeling of AGN activity (both in terms of cold gas accretion onto SMBHs and AGN-driven feedback (cite: Fontanot20)). The GAEA SAM has recently been coupled (Fontanot et al., in prep.) to the P-Millennium simulation (cite: Baugh19), which spans a volume of 800$^3$ Mpc$^3$, with a mass resolution of $m_p = 1.06 \times 10^8$ M$_{\odot}$, and assuming cosmological parameters consistent with the first year results from the *Planck* satellite (cite: Planck_cosmpar), to predict the evolution of galaxy properties from z$\sim$20 to the local Universe (Cantarella et al., in prep.). We extracted all predicted AGN galaxies from the simulated box with a $L_{\rm bol} > 3\times10^{46}$ erg s$^{-1}$ at $z>6$, resulting in a sample of 42 individual sources. For each of these sources, we studied their mean molecular gas content and SFR by considering the evolution of these quantities over a timescale compatible with the Eddington time ($\sim$4 $\times$ 10$^7$ yrs), before the peak of the predicted AGN activity. The synthetic objects show a distribution of $t_{dep}$ that covers a larger range of values, with the bulk of the population of 42 GAEA quasars that have depletion times of a few hundred million years. This can be due to the prescription used in the GAEA SAM that instantaneously triggers the quasar phase when a sufficient amount of gas is concentrated in a certain radius in the host galaxy. This favors the emergence of bright quasars, as well as the case of less massive objects, with respect to our current picture of bright quasars. Indeed, GAEA quasars show $M_{BH}$ that is roughly two orders of magnitude smaller ($\log(M_{BH}/M_{\odot}\sim7.40\pm0.23$) than that observed in the quasar at redshift $z>6$ ($\log(M_{BH}/M_{\odot}\sim9.33\pm0.24$). This is likely due to the flat prescription adopted for black hole seeding, which does not consider the hypothesis that massive ($M_{BH}>10^6$ M$_{\odot}$) can form via the direct collapse of giant gas clouds in the early Universe (for an alternative approach, see (cite: Trinca22)). Furthermore, the different distribution between synthetic and observed quasars can be partially due to an observational bias because we only detect the brightest sources at the EoR. Indeed, considering the quasars at Cosmic Noon that span a larger regime $\rm L_{bol}$ and $\rm L_{FIR}$ (see the upper-right and lower-left panels of Fig. [4](#fig:SFE)), quasars from the SUPER (SINFONI Survey for Unveiling the Physics and Effect of Radiative feedback) and KASHz (KMOS AGN Survey at High redshift) samples from (cite: Bertola24) show depletion times that are consistent with the bulk of GAEA objects. Eventually, AGN and star-forming galaxies at lower redshifts show a wider range of $t_{dep}$ value, but the bulk of the distributions peak close to $t_{dep}\sim1$ Gyr.

An interpretation of this result requires that the feedback from the SMBH in high-redshift and luminous quasars can remove or heat the cold gas reservoir from their host (cite: Brusa18; Fiore17; Fluetsch19). However, several studies of SMBH-driven winds in quasars at different redshifts have shown that they are not powerful enough to impact the star formation ( (cite: Bischetti19b), (cite: Tripodi23b), and (cite: Novak19)), at least in the cold phase of the gas. Simulations suggest that the quenching effect of the accreting SMBH is not instantaneously effective and, hence, that accretion onto the SMBH and massive star formation coexist ( (cite: Costa20), (cite: Costa22), and (cite: Valentini21)).

A different interpretation proposes that the relatively low depletion times are likely due to the highly efficient star formation of the quasar host that is favored by the concentration of cold gas in a relatively compact size. To examine this scenario, we then derived the gas SFE, defined as $\rm SFE_{gas}=1/t_{dep}=SFR/M(H_2)$, which is represented as a function of $L_{IR}$ in the upper-right panel of Fig. [4](#fig:SFE). The trend between SFE and $\rm L_{FIR}$ shown in the upper-right panel of Fig. [4](#fig:SFE) suggests that the galaxies that are brighter at FIR wavelengths (hence have higher SFR), are more efficient at forming stars compared to galaxies at lower $\rm L_{FIR}$. This is true, irrespective of the presence of an AGN at their center. Nonetheless, quasar hosts exceed up to one order of magnitude the SFE measured in star-forming and luminous galaxies ((cite: Tacconi18); dash-doted and dotted lines in the upper panel of Fig. [4](#fig:SFE)) at high luminosities ($L_{FIR}>10^{12}$ L$_{\odot}$). In particular, quasars at the EoR show the highest efficiencies among the objects considered in our analysis, except for the hyper-luminous quasars at Cosmic Noon from the WISE/SDSS-selected hyper-luminous quasar (WISSH) sample ((cite: Bischetti21) and Salvestrini et al. in prep.). Regarding $z>7$ massive quasar hosts, we find lower SFE limits of $\rm >10^{-8}$ yr$^{-1}$, slightly higher than the SFE measured in J1007: $\rm SFE=9.7\pm2.5\times 10^{-9}$ yr$^{-1}$.

As discussed in Sect. [3.2](#sec:mh), a highly star-forming host galaxy is a common characteristic among bright ($L_{bol}>10^{12.5}$ L$_{\odot}$) quasars at high redshifts (e.g., (cite: Venemans17c), (cite: Decarli22), (cite: Izumi21), and (cite: Tripodi24b)). However, this effect could result from a combination of observational bias and the evolution of the MS ((cite: RenziniPeng15)) at high redshifts. Regarding the first point, we still lack a complete sampling, especially at (sub)millimeter wavelengths, of galaxy populations at intermediate luminosities ($L_{FIR}<10^{12}$ L$_{\odot}$). Concerning the second point, the SFR is expected to increase for MS galaxies with redshift as a result of the higher cosmological accretion rate at early times ($0<z<6$; (cite: Tacconi20), (cite: Walter20), and (cite: Popesso23)). This is confirmed by observational studies (e.g., (cite: Tacconi20) and (cite: Sommovigo22a)) that found that the depletion time decreases with redshift, with values of $\sim0.01$ Gyr at $z\sim7$, consistent with those observed in quasars at the EoR (see the upper-left panel of Fig.[4](#fig:SFE)). These two points should be taken into account when interpreting the lower-right panel of Fig. [4](#fig:SFE). In each histogram, AGN and quasar sources are divided by redshift, while the luminous and star-forming galaxies from (cite: Tacconi18) are shown for comparison in the lower panel. Quasars at the EoR represent only the population of the brightest sources at this epoch, and we are likely missing the rich population of intermediate luminosity AGN recently discovered with *James Webb* Space Telescope (JWST; e.g., (cite: Harikane23), (cite: Maiolino24a), and (cite: Maiolino24b)). In this regard, the results from the GAEA simulations predict a broader SFE distribution, with a peak at lower SFEs with respect to observations of quasars at similar redshifts.

Thanks to JWST, it is now possible to detect the stellar light from the quasar host (cite: Ding23), and to model the corresponding emission to derive stellar masses (e.g., (cite: Ding23) and (cite: Yue24)). We took the estimate and upper limit of the stellar mass from (cite: Yue24) for four quasars at the EoR (J1120 and three other quasars), which are listed in Table [\[tab:comp_sample_z6\]](#tab:comp_sample_z6). We then calculated the specific SFR (sSFR$=SFR/M_{\star}$) and molecular gas fraction ($f_{gas}=M_{H2}/M_{\star}$. The lower limit and estimate of the sSFR ($>10^{-8}$ yr$^{-1}$) are way above the expected value for MS galaxies at the EoR. Their molecular gas fraction ($f_{gas}\sim0.05-0.5$) is lower than what observed in local quasars and AGN ( (cite: Shangguan20) and (cite: Salvestrini22)), but consistent with that derived from dynamical measurements in luminous quasars at Cosmic Noon (cite: Bischetti21). This confirms that these objects are experiencing an intense starburst phase that is coeval with the bright phase of the quasars, justifying the shift between the median value of the SFE distribution between AGN and non-AGN host galaxies in the histograms of Fig. [4](#fig:SFE).

In the lower-left panel of Fig. [4](#fig:SFE), we show the SFE as a function of the bolometric luminosity of the accreting SMBH. The solid black line connects the median value of the SFE of quasars and AGN divided into four bins of $\rm L_{bol}$. The increasing trend between the SFE and $\rm L_{bol}$[^5] shown in the lower-left panel of Fig. [4](#fig:SFE) suggests that the processes that convey a significant amount of gas toward the nuclear region (e.g., disk instabilities) are more efficient than the effect of the feedback (e.g., outflows) produced by the accreting SMBH, which is expected to be proportional to the quasar luminosity (cite: Fiore17; Fluetsch19). We then conclude that among the known population of bright quasars at the EoR there is no clear evidence of an efficient quenching of the host-galaxy star formation due to quasar feedback. On the contrary, at such early epochs, a bright quasar phase is likely coeval with an intense buildup phase in the host galaxy. The coexistence between SMBH growth and intense star formation in the host is visible at all redshifts, when considering luminous quasars, suggesting that quasar activity benefits from the gas concentration in the nuclear region of the galaxy. An alternative scenario can be that the quasar activity triggers the star formation in the host, by compressing the gas in the surrounding medium (cite: Cresci18).

# Conclusions

In this work we present new NOEMA observations targeting CO emission lines for five $z > 7$ quasars, completing the survey of molecular gas properties for all eight known quasars at this epoch. These observations represent the highest-redshift investigation of cold dust and gas to date in a sample of quasar host galaxies at the EoR. By modeling the FIR emission with a MBB using EOS-Dustfit, we derived dust properties and SFR estimates for our sample. Although no statistically significant CO emission lines were detected in the five targets, we derived upper limits on the molecular gas mass. We compared the molecular gas and dust properties of all known $z > 7$ quasars with a compilation of quasar hosts and star-forming galaxies at different redshifts. Our results are:

- Among the eight known quasars at $z>7$, only one object (J1007; (cite: Feruglio23)) has a statistically significant molecular gas mass estimate. We find no massive gas reservoirs ($M_{H2} <$ a few times $10^{10}$ M$_{\odot}$) at $z>7$.

- Combining the new observations presented in this work with measurements from the literature, we provide a new calibration to derive $\rm M_{H2}$ from $\rm L_{[CII]}$ for $z\gtrsim6$ quasars.

- Quasar host galaxies at $z>7$ had already accumulated large dust reservoirs ($M_{d}\sim10^8$ M$_{\odot}$) in a relatively short time (a few hundred megayears) after the Big Bang. This suggests that the physical processes responsible for dust enrichment are very efficient and may include contributions from evolved stellar populations, SN, and reprocessing within the ISM. The GDR estimate and upper limits for $z > 7$ quasars presented here align with the mean GDR for luminous quasars and AGN at later epochs, which is consistent with the local value (GDR=100; (cite: DraineLi07)).

- Quasars at the EoR are hosted in galaxies undergoing intense starburst phases, with SFEs up to an order of magnitude higher than those expected for non-AGN host galaxies. This suggests that the emergence of a luminous quasar phase is coeval with the rapid buildup of the host galaxy.

- Semi-analytic models of quasar host galaxies from GAEA at the EoR also support the idea that the quasar phase is triggered during periods of efficient star formation.

# Acknowledgements

FS and CF thank J.M. Winters for his help in data reduction and calibration. FS thanks V. D’Odorico for the useful discussion and suggestions. The project leading to this publication has received support from ORP, that is funded by the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 \[ORP\]. This work is based on observations carried out under project number S23CX with the IRAM NOEMA Interferometer. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain). LZ, EP, AT, and FS acknowledge financial support from the Bando Ricerca Fondamentale INAF 2022 Large Grant “Toward an holistic view of the Titans: multi-band observations of $z>6$ QSOs powered by greedy supermassive black holes”. CF, and FS acknowledge financial support from PRIN MUR 2022 2022TKPB2P - BIG-z and Ricerca Fondamentale INAF 2023 Data Analysis grant “ARCHIE ARchive Cosmic HI & ISM Evolution”. M.B. acknowledges support from INAF under project 1.05.12.04.01 - 431 MINI-GRANTS di RSN1 "Mini-feedback" and support from UniTs under project DF-microgrants23 "Hyper-Gal". This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01188.S, #2019.A.00017.S, #2019.1.00074.S, #2019.1.01025.S, #2021.1.00934.S, #2021.1.01262.S. ALMA is a partnership of ESO (representing its member states), NFS (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

*Software:* Astropy (cite: astropy1; astropy2; astropy3); CASA (cite: casa); emcee (cite: emcee1; emcee2); GILDAS <https://www.iram.fr/IRAMFR/GILDAS/>; linmix (cite: linmix); Matplotlib (cite: matplotlib); NumPy (cite: numpy); Seaborn (cite: seaborn); Scipy (cite: scipy).

143 natexlab

(ref: Algera24) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 6867

(ref: Amorin16) Amorı́n, R., Muñoz-Tuñón, C., Aguerri, J. A. L., & Planesas, P. 2016, A&A, 588, A23

(ref: astropy3) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: astropy2) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: astropy1) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Banados16) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11

(ref: Baugh19) Baugh, C. M., Gonzalez-Perez, V., Lagos, C. D. P., et al. 2019, MNRAS, 483, 4922

(ref: Beelen06) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694

(ref: Bertola24) Bertola, E., Circosta, C., Ginolfi, M., et al. 2024, A&A, 691, A178

(ref: Bischetti24) Bischetti, M., Choi, H., Fiore, F., et al. 2024, ApJ, 970, 9

(ref: Bischetti21) Bischetti, M., Feruglio, C., Piconcelli, E., et al. 2021, A&A, 645, A33

(ref: Bischetti19b) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019a, A&A, 630, A59

(ref: Bischetti18) Bischetti, M., Piconcelli, E., Feruglio, C., et al. 2018, A&A, 617, A82

(ref: Bischetti19a) Bischetti, M., Piconcelli, E., Feruglio, C., et al. 2019b, A&A, 628, A118

(ref: BlitzRosolowsky06) Blitz, L. & Rosolowsky, E. 2006, ApJ, 650, 933

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Brusa18) Brusa, M., Cresci, G., Daddi, E., et al. 2018, A&A, 612, A29

(ref: CarilliWalter13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Carniani19) Carniani, S., Gallerani, S., Vallini, L., et al. 2019, MNRAS, 489, 3939

(ref: casa) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Casasola20) Casasola, V., Bianchi, S., De Vis, P., et al. 2020, A&A, 633, A100

(ref: Casavecchia24b) Casavecchia, B., Maio, U., Péroux, C., & Ciardi, B. 2025, A&A, 693, A119

(ref: Chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: Costa22) Costa, T., Arrigoni Battaia, F., Farina, E. P., et al. 2022, MNRAS, 517, 1767

(ref: Costa20) Costa, T., Pakmor, R., & Springel, V. 2020, MNRAS, 497, 5229

(ref: Cresci18) Cresci, G. & Maiolino, R. 2018, Nature Astronomy, 2, 179

(ref: DeLooze14) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62

(ref: DeLucia24) De Lucia, G., Fontanot, F., Xie, L., & Hirschmann, M. 2024, A&A, 687, A68

(ref: Decarli24) Decarli, R., Loiacono, F., Farina, E. P., et al. 2024, A&A, 689, A219

(ref: Decarli23) Decarli, R., Pensabene, A., Diaz-Santos, T., et al. 2023, A&A, 673, A157

(ref: Decarli22) Decarli, R., Pensabene, A., Venemans, B., et al. 2022, A&A, 662, A60

(ref: Decarli17) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457

(ref: Decarli18) Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97

(ref: DellAgli19b) Dell’Agli, F., Valiante, R., Kamath, D., Ventura, P., & Garcı́a-Hernández, D. A. 2019, MNRAS, 486, 4738

(ref: DiMascia21) Di Mascia, F., Gallerani, S., Behrens, C., et al. 2021, MNRAS, 503, 2349

(ref: DietrichHamann04) Dietrich, M. & Hamann, F. 2004, ApJ, 611, 761

(ref: Ding23) Ding, X., Onoue, M., Silverman, J. D., et al. 2023, Nature, 621, 51

(ref: Draine03) Draine, B. T. 2003, ARA&A, 41, 241

(ref: Draine09) Draine, B. T. 2009, in Astronomical Society of the Pacific Conference Series, Vol. 414, Cosmic Dust - Near and Far, ed. T. Henning, E. Grün, & J. Steinacker, 453

(ref: DraineLi07) Draine, B. T. & Li, A. 2007, ApJ, 657, 810

(ref: Duras17) Duras, F., Bongiorno, A., Piconcelli, E., et al. 2017, A&A, 604, A67

(ref: Elvis02) Elvis, M., Marengo, M., & Karovska, M. 2002, ApJL, 567, L107

(ref: Fan23) Fan, X., Bañados, E., & Simcoe, R. A. 2023, ARA&A, 61, 373

(ref: Feruglio18) Feruglio, C., Fiore, F., Carniani, S., et al. 2018, A&A, 619, A39

(ref: Feruglio23) Feruglio, C., Maio, U., Tripodi, R., et al. 2023, ApJL, 954, L10

(ref: Fiore17) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: Fluetsch19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: Fontanot20) Fontanot, F., De Lucia, G., Hirschmann, M., et al. 2020, MNRAS, 496, 3943

(ref: emcee2) Foreman-Mackey, D., Farr, W., Sinha, M., et al. 2019, The Journal of Open Source Software, 4, 1864

(ref: emcee1) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: Gallerani10) Gallerani, S., Maiolino, R., Juarez, Y., et al. 2010, A&A, 523, A85

(ref: Galliano21) Galliano, F., Nersesian, A., Bianchi, S., et al. 2021, A&A, 649, A18

(ref: GunnPeterson65) Gunn, J. E. & Peterson, B. A. 1965, ApJ, 142, 1633

(ref: Harikane23) Harikane, Y., Zhang, Y., Nakajima, K., et al. 2023, ApJ, 959, 39

(ref: numpy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: HerreraCamus18) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 95

(ref: matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: Hygate23) Hygate, A. P. S., Hodge, J. A., da Cunha, E., et al. 2023, MNRAS, 524, 1775

(ref: Izumi21) Izumi, T., Matsuoka, Y., Fujimoto, S., et al. 2021, ApJ, 914, 36

(ref: Izumi24) Izumi, T., Matsuoka, Y., Onoue, M., et al. 2024, ApJ, 972, 116

(ref: Kaasinen24) Kaasinen, M., Venemans, B., Harrington, K. C., et al. 2024, A&A, 684, A33

(ref: Kashikawa15) Kashikawa, N., Ishizaki, Y., Willott, C. J., et al. 2015, ApJ, 798, 28

(ref: linmix) Kelly, B. C. 2007, ApJ, 665, 1489

(ref: Kennicutt98) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: Kirchschlager19) Kirchschlager, F., Schmidt, F. D., Barlow, M. J., et al. 2019, MNRAS, 489, 4465

(ref: Koss21) Koss, M. J., Strittmatter, B., Lamperti, I., et al. 2021, ApJS, 252, 29

(ref: Kroupa01) Kroupa, P. 2001, MNRAS, 322, 231

(ref: Lesniewska19) Leśniewska, A. & Michałowski, M. J. 2019, A&A, 624, L13

(ref: Madden20) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: Maio22) Maio, U., Péroux, C., & Ciardi, B. 2022, A&A, 657, A47

(ref: Maio23) Maio, U. & Viel, M. 2023, A&A, 672, A71

(ref: Maiolino05) Maiolino, R., Cox, P., Caselli, P., et al. 2005, A&A, 440, L51

(ref: Maiolino24b) Maiolino, R., Risaliti, G., Signorini, M., et al. 2024a, MNRAS, arXiv:2405.00504

(ref: Maiolino24a) Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2024b, A&A, 691, A145

(ref: Mancini15) Mancini, M., Schneider, R., Graziani, L., et al. 2015, MNRAS, 451, L70

(ref: Mazzucchelli17) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017, ApJ, 849, 91

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Micelotta18) Micelotta, E. R., Matsuura, M., & Sarangi, A. 2018, Space Sci. Rev., 214, 53

(ref: Neeleman19) Neeleman, M., Bañados, E., Walter, F., et al. 2019, The Astrophysical Journal, 882, 10

(ref: Neeleman21) Neeleman, M., Novak, M., Venemans, B. P., et al. 2021, ApJ, 911, 141

(ref: Novak19) Novak, M., Bañados, E., Decarli, R., et al. 2019, ApJ, 881, 63

(ref: Pensabene22) Pensabene, A., van der Werf, P., Decarli, R., et al. 2022, A&A, 667, A9

(ref: Pineda13) Pineda, J. L., Langer, W. D., Velusamy, T., & Goldsmith, P. F. 2013, A&A, 554, A103

(ref: Pipino11) Pipino, A., Fan, X. L., Matteucci, F., et al. 2011, A&A, 525, A61

(ref: Planck_cosmpar) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2014, A&A, 571, A16

(ref: Popesso23) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526

(ref: Popping17) Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152

(ref: Pozzi21) Pozzi, F., Calura, F., Fudamoto, Y., et al. 2021, A&A, 653, A84

(ref: RemyRuyer14) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31

(ref: RenziniPeng15) Renzini, A. & Peng, Y.-j. 2015, ApJL, 801, L29

(ref: Riechers09) Riechers, D. A., Walter, F., Bertoldi, F., et al. 2009, ApJ, 703, 1338

(ref: Riechers07) Riechers, D. A., Walter, F., Carilli, C. L., & Bertoldi, F. 2007, ApJL, 671, L13

(ref: Riechers06) Riechers, D. A., Walter, F., Carilli, C. L., et al. 2006, ApJ, 650, 604

(ref: Rizzo21) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952

(ref: Rizzo20) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: Romano22) Romano, M., Morselli, L., Cassata, P., et al. 2022, A&A, 660, A14

(ref: Ronconi24) Ronconi, T., Lapi, A., Torsello, M., et al. 2024, A&A, 685, A161

(ref: Saintonge18) Saintonge, A., Wilson, C. D., Xiao, T., et al. 2018, MNRAS, 481, 3497

(ref: Salome23) Salomé, Q., Krongold, Y., Longinotti, A. L., et al. 2023, MNRAS, 524, 3130

(ref: Salvestrini22) Salvestrini, F., Gruppioni, C., Hatziminaoglou, E., et al. 2022, A&A, 663, A28

(ref: Salvestrini20) Salvestrini, F., Gruppioni, C., Pozzi, F., et al. 2020, A&A, 641, A151

(ref: Sarangi19) Sarangi, A., Dwek, E., & Kazanas, D. 2019, ApJ, 885, 126

(ref: SchneiderMaiolino24) Schneider, R. & Maiolino, R. 2024, A&ARv, 32, 2

(ref: Shangguan20) Shangguan, J., Ho, L. C., Bauer, F. E., Wang, R., & Treister, E. 2020, ApJ, 899, 112

(ref: Shao22) Shao, Y., Wang, R., Weiss, A., et al. 2022, A&A, 668, A121

(ref: Shen11) Shen, Y., Richards, G. T., Strauss, M. A., et al. 2011, ApJS, 194, 45

(ref: Shen19) Shen, Y., Wu, J., Jiang, L., et al. 2019, ApJ, 873, 35

(ref: Sommovigo22a) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2022, MNRAS, 513, 3122

(ref: Stefan15) Stefan, I. I., Carilli, C. L., Wagg, J., et al. 2015, MNRAS, 451, 1713

(ref: Tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tacconi20) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: Trinca22) Trinca, A., Schneider, R., Valiante, R., et al. 2022, MNRAS, 511, 616

(ref: Tripodi24b) Tripodi, R., Feruglio, C., Fiore, F., et al. 2024a, A&A, 689, A220

(ref: Tripodi23b) Tripodi, R., Feruglio, C., Kemper, F., et al. 2023, ApJL, 946, L45

(ref: Tripodi24a) Tripodi, R., Scholtz, J., Maiolino, R., et al. 2024b, A&A, 682, A54

(ref: Tsukui23) Tsukui, T., Wisnioski, E., Krumholz, M. R., & Battisti, A. 2023, MNRAS, 523, 4654

(ref: Valentini21) Valentini, M., Gallerani, S., & Ferrara, A. 2021, MNRAS, 507, 1

(ref: Valiante11) Valiante, R., Schneider, R., Salvadori, S., & Bianchi, S. 2011, MNRAS, 416, 1916

(ref: Valiante14) Valiante, R., Schneider, R., Salvadori, S., & Gallerani, S. 2014, MNRAS, 444, 2442

(ref: Venemans19) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJL, 874, L30

(ref: Venemans17c) Venemans, B. P., Walter, F., Decarli, R., et al. 2017a, ApJL, 851, L8

(ref: Venemans17a) Venemans, B. P., Walter, F., Decarli, R., et al. 2017b, ApJ, 837, 146

(ref: Venemans17b) Venemans, B. P., Walter, F., Decarli, R., et al. 2017c, ApJ, 845, 154

(ref: Venemans20) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130

(ref: Ventura18) Ventura, P., Karakas, A., Dell’Agli, F., Garcı́a-Hernández, D. A., & Guzman-Ramirez, L. 2018, MNRAS, 475, 2282

(ref: scipy) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Vizgan22) Vizgan, D., Greve, T. R., Olsen, K. P., et al. 2022, ApJ, 929, 92

(ref: Walter20) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111

(ref: Walter22) Walter, F., Neeleman, M., Decarli, R., et al. 2022, ApJ, 927, 21

(ref: WangF21) Wang, F., Yang, J., Fan, X., et al. 2021, ApJL, 907, L1

(ref: WangF24) Wang, F., Yang, J., Fan, X., et al. 2024, ApJ, 968, 9

(ref: WangR07) Wang, R., Carilli, C. L., Beelen, A., et al. 2007, AJ, 134, 617

(ref: WangR10) Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714, 699

(ref: WangR11b) Wang, R., Wagg, J., Carilli, C. L., et al. 2011, AJ, 142, 101

(ref: WangR13) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44

(ref: seaborn) Waskom, M. L. 2021, Journal of Open Source Software, 6, 3021

(ref: Witstok23) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS, 523, 3119

(ref: Witstok22) Witstok, J., Smit, R., Maiolino, R., et al. 2022, MNRAS, 515, 1751

(ref: Xie17) Xie, L., De Lucia, G., Hirschmann, M., Fontanot, F., & Zoldan, A. 2017, MNRAS, 469, 968

(ref: Yang21) Yang, J., Wang, F., Fan, X., et al. 2021, ApJ, 923, 262

(ref: Yang20) Yang, J., Wang, F., Fan, X., et al. 2020, ApJL, 897, L14

(ref: Yue24) Yue, M., Eilers, A.-C., Simcoe, R. A., et al. 2024, ApJ, 966, 176

(ref: Zanella18) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976

# Far-infrared SED models

In Fig. [5](#fig:fir_sed) we present the best-fit models of the FIR SED of the five quasars at $z>7$ in our sample. The corresponding corner plots of the free parameters obtained with the Bayesian analysis of the MBB with the EOS-Dustfit code are shown in Fig. [6](#fig:corner_plots). Details of the analysis are reported in Sect. [3.1](#sec:dustsed).

In Fig. [7](#fig:fir_sed_multi_par) we show the results of the modeling of the continuum emission when assuming different values for $\beta$ and $T_d$ for each of the five quasars. The baseline model (i.e., the one shown in Fig. [5](#fig:fir_sed)) is represented with a solid black line in each panel, while observed fluxes and upper limits are black diamonds and triangles, respectively. The impact of the assumption of a different dust temperature is shown as the best-fit model obtained with a $T_d=70$ (40) K, which is displayed with a red (orange) curve. In the case of J1243 and J0252, $\beta$ was left free to vary, while it is fixed to 1.6 for the remaining targets.

For J0313, J0038, and J2356, we also evaluate the impact of the assumption of $\beta=2$ and $\beta=1.2$ with a blue and solid green line, respectively. For J1243 and J0252, the solid blue line represents the case of $\beta=1.6$ fixed. When we varied $\beta$, we left $T_d=55$ K fixed. Relative residuals are shown in the lower box of each panel, color-coded accordingly to the best-fit lines of the upper box.

![](figures/fir_seds/figureA1.png)

![](figures/corner_plots/figure_corner.png)

![](figures/fir_seds/figure_A3.png)

# Continuum maps

In Fig. [8](#fig:cont_maps) we present the continuum maps produced from the interferometric data collected and analyzed as described in Sect. [2](#sec:obs). Flux densities were extracted from the continuum maps as described in Sect. [2](#sec:obs).

|  |  |  |
|:--:|:--:|:--:|
| ![image](figures/continuum_maps/J0313-1806_continuum-s23cx001-co7665-USB_box.png) | ![image](figures/continuum_maps/J0313-1806_continuum-s23cx001-co7665-LSB_box.png) | ![image](figures/continuum_maps/J0313-1806_J0313-1806_cont_3s_box.png) |
| ![image](figures/continuum_maps/J1243+0100_continuum-s23cx002-co7665-USB_box.png) | ![image](figures/continuum_maps/J1243+0100_continuum-s23cx002-co7665-LSB_box.png) | ![image](figures/continuum_maps/J1243+0100_J1243+0100_cont_3s_comb_box.png) |
| ![image](figures/continuum_maps/J0038-1527_continuum-s23cx003-co7665-USB_box.png) | ![image](figures/continuum_maps/J0038-1527_continuum-s23cx003-co7665-LSB_box.png) | ![image](figures/continuum_maps/J0038-1527_J0038-1527_cont_3s_box.png) |
| ![image](figures/continuum_maps/J2356+0017_continuum-s23cx004-co7665-USB_box.png) | ![image](figures/continuum_maps/J2356+0017_continuum-s23cx004-co7665-LSB_box.png) |  |
| ![image](figures/continuum_maps/J0252-0503_continuum-s23cx005-co7665-USB_box.png) | ![image](figures/continuum_maps/J0252-0503_continuum-s23cx005-co7665-LSB_box.png) | ![image](figures/continuum_maps/J0252-0503_J0252-0503_cont_3s_comb_box.png) |

# Comparison sample of high-z quasars

In Table [\[tab:comp_sample_z6\]](#tab:comp_sample_z6) we report the information collected from the literature for 21 quasars at redshift $z\gtrsim6$ and a quasar at $z\sim5$. Quasars have been selected to have observations of CO emission lines, and properties derived from the FIR SED fitting. In addition, 19 out of the 21 quasars at $z\gtrsim6$ have $\rm L_{[CII]}$ measurement. We report $L^{\prime}_{CO(1--0)}$ derived from $L^{\prime}_{CO(J+1--J)}$ available in the literature (see column $J_{up}$), assuming for all objects the same fixed CO SLED that we used in Sect. [3](#sec:results). In particular, we assumed $r_{J+1,J}=L^{\prime}_{CO(J+1--J)}/L^{\prime}_{CO(1--0)}$ as follows: $r_{7,6}=0.65$, $r_{6,5}=0.9$, $r_{2,1}=1$. The host-galaxy SFR is then derived from $\rm L_{FIR}$ by adopting a Chabrier IMF. Moreover, we report only the measurement uncertainties for the sources for which these quantities were reported in the literature (see references). During calculations and fitting procedures described in Sect. [3](#sec:results), for each measurement without uncertainty, we assigned an error that is equal to the median of the relative uncertainties available.

| Source | RA, Dec | $z$ | $\log(L_{bol})$ | $\log(M_{BH})$ | $(L_{[CII]})$ | $\log(L_{TIR})$ | $(L^{\prime}_{CO(1-0)})$ | $\log(M_{dust})$ | Ref |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
|  | J2000 |  | \[erg/s\] | \[M$_{\odot}$\] | $10^9$ L$_{\odot}$ | \[L$_{\odot}$\] | $10^{10}$ K km/s pc$^2$ | \[M$_{\odot}$\] |  |
| SDSSJ0100+2802 | 01:00:13.02 +28:02:25.80 | 6.3258 | 48.187 $\pm$ 0.001 | 10.29 $\pm$ 0.01 | 3.56 $\pm$ 0.49 | 12.42 $\pm$ 0.09 | 3.54 $\pm$ 0.46 | 7.36 $\pm$ 0.13 | \[1,8,13\] |
| J010953.13–304726.30 | 01:09:53.13 -30:47:26.32 | 6.7909 | 46.71 $\pm$ 0.05 | 9.12 $\pm$ 0.16 | 2.4 $\pm$ 0.2 | 12.08 $\pm$ 0.09 | 11.54 $\pm$ 2 | 8.48 $\pm$ 0.4 | \[2,9,15\] |
| VDESJ0224-4711 | 02:24:26.54 -47:11:29.40 | 6.522 | 47.53 $\pm$ 0.03 | 9.11 $\pm$ 0.06 | 5.43 $\pm$ 0.15 | 13.52 $\pm$ 0.2 | 1.48 $\pm$ 0.22 | 7.97 $\pm$ 0.11 | \[3,10\] |
| PSOJ036.5+03 | 02:26:01.87 +03:02:59.24 | 6.541 | 47.3 $\pm$ 0.09 | 9.48 $\pm$ 0.12 | 5.8 $\pm$ 0.7 | 12.71 $\pm$ 0.11 | 1.65 $\pm$ 0.18 | 7.79 $\pm$ 0.15 | \[2,8,16\] |
| J0305-3150 | 03:05:16.92 -31:50:55.90 | 6.6145 | 46.88 $\pm$ 0.13 | 8.95 $\pm$ 0.14 | 3.9 $\pm$ 0.2 | 12.83 $\pm$ 0.013 | 3.08 $\pm$ 0.46 | 8.95 $\pm$ 0.25 | \[2,9,16\] |
| SDSS J0338+0021 | 03:38:29.31 +00:21:56.30 | 5.0278 | 47.25 | 9.4 $\pm$ 0.12 | 5.69 $\pm$ 0.83 | 13.08 | 1.12 $\pm$ 0.17 | 8.33 $\pm$ 0.03 | \[4,11\] |
| J0840+5624 | 08:40:35.09 +56:24:19.90 | 5.8441 | 46.713 $\pm$ 0.002 | 9.55 $\pm$ 0.19 |  |  | 1.81 $\pm$ 0.64$^a$ |  | \[5,12\] |
| J0927+2001 | 09:27:21.82 +20:01:23.70 | 5.7716 | 46.99 $\pm$ 0.003 | 9.69 $\pm$ 0.12 |  |  | 4.75 $\pm$ 1.15$^b$ |  | \[5,12\] |
| PSO J159.2257–02.5438 | 10:36:54.19 -02:32:37.94 | 6.3822 | 47.26 $\pm$ 0.008 | 9.68 $\pm$ 0.05 | 1.19 $\pm$ 0.07 | 12.2 | 1.05 $\pm$ 2 | 7.89 $\pm$ 0.04 | \[1,11\] |
| VIK J1048–0109 | 10:48:19.09 -01:09:40.29 | 6.6766 | 47.023 $\pm$ 0.012 | 9.53 $\pm$ 0.11 | 2.77 $\pm$ 0.08 | 12.89 | 1.72 $\pm$ 0.17 | 8.7 $\pm$ 0.11 | \[1,11\] |
| DELS J1104+2134 | 11:04:21.58 +21:34:28.85 | 6.7672 | 47.18 $\pm$ 0.03 | 9.23 $\pm$ 0.04 | 1.82 $\pm$ 0.28 | 12.7 | 1.18 $\pm$ 0.23 | 8.53 $\pm$ 0.18 | \[6,11\] |
| SDSSJ1148+5251 | 11:48:16.10 +52:51:50.00 | 6.4189 | 47.538 $\pm$ 0.002 | 9.94 $\pm$ 0.02 | 4.2 $\pm$ 0.35 | 13 $\pm$ 0.06 | 3.2 $\pm$ 0.3$^b$ | 8.51 $\pm$ 0.1 | \[5,10,17\] |
| PSOJ183+05 | 12:12:26.98 +05:05:33.49 | 6.4386 | 47.351 $\pm$ 0.006 | 9.67 $\pm$ 0.06 | 25.3 $\pm$ 0.4 | 13.08 $\pm$ 0.15 | 3.51 $\pm$ 0.39 | 8.65 $\pm$ 0.08 | \[1,13,10\] |
| ULASJ1319+0950 | 13:19:11.29 +09:50:51.40 | 6.1336 | 47.247 $\pm$ 0.001 | 9.46 $\pm$ 0.03 | 4.4 $\pm$ 0.9 | 12.99 $\pm$ 0.008 | 1.8 $\pm$ 0.23 | 8.8 $\pm$ 0.16 | \[1,8,10\] |
| PSO231-20 | 15:26:37.84 -20:50:00.66 | 6.5864 | 47.28 $\pm$ 0.09 | 9.48 $\pm$ 0.19 | 2.87 $\pm$ 0.15 | 13.28 $\pm$ 0.09 | 2.15 $\pm$ 0.2 | 8.72 $\pm$ 0.04 | \[2,14,10\] |
| PJ308-21 | 20:32:10.00 -21:14:02.40 | 6.2354 | 47.34 $\pm$ 0.004 | 9.41 $\pm$ 0.07 | 1.73 $\pm$ 0.14 | 12.42 $\pm$ 0.18 | \<0.29 | 7.7 $\pm$ 0.2 | \[1,14,11\] |
| J2054-0005 | 20:54:06.49 -00:05:14.80 | 6.0397 | 47.092 $\pm$ 0.013 | 9.34 $\pm$ 0.05 | 3.3 $\pm$ 0.5 | 12.73 $\pm$ 0.007 | 0.86 $\pm$ 0.31 | 8.03 $\pm$ 0.09 | \[1,8,11\] |
| VIMOS2911001793 | 22:19:17.22 +01:02:48.90 | 6.1503 | 47 $\pm$ 0.07 | 9.49 $\pm$ 0.05 | 2.59 $\pm$ 0.13 | 12.24 $\pm$ 0.03 | 1.42 $\pm$ 0.22 | 7.92 $\pm$ 0.04 | \[7,8,11\] |
| PSO J338.2298+29.5089 | 22:32:55.15 +29:30:32.23 | 6.6668 | 47.61 $\pm$ 0.16 | 9.43 $\pm$ 0.15 | 2 $\pm$ 0.1 | 12.31 $\pm$ 0.11 | 0.94 $\pm$ 0.23 | 7.96 $\pm$ 0.05 | \[2,8,11\] |
| SDSSJ2310+1855 | 23:10:38.89 +18:55:19.70 | 6.0028 | 47.5 $\pm$ 0.001 | 9.86 $\pm$ 0.06 | 8.7 $\pm$ 1.4 | 13.2 $\pm$ 0.004 | 0 $\pm$ 0 | 8.64 $\pm$ 0.06 | \[5,8,18\] |
| J2348-3054 | 23:48:33.35 -30:54:10.28 | 6.9018 | 46.63 $\pm$ 0.17 | 9.3 $\pm$ 0.15 | 1.9 $\pm$ 0.3 | 12.63 $\pm$ 0.03 | 12.46 $\pm$ 2.62 | 8.04 $\pm$ 0.12 | \[2,9,16\] |
| PSOJ359-06 | 23:56:32.45 -06:22:59.26 | 6.1726 | 47.409 $\pm$ 0.005 | 9.58 $\pm$ 0.09 | 2.42 $\pm$ 0.15 | 12.32 | 0.89 $\pm$ 0.25$^b$ | 7.97 $\pm$ 0.04 | \[1,11\] |

[^1]: [www.iram.fr/IRAMFR/GILDAS](www.iram.fr/IRAMFR/GILDAS)

[^2]: Project IDs of the dataset analyzed are listed in the Acknowledgements. J2356 observation with project ID 2023.1.00443.S is still in a proprietary period at the moment of this analysis

[^3]: IRAM NOEMA Data Reduction CookBook, <https://iram-institute.org/science-portal/noema/documentation/>

[^4]: EOS-Dustfit is a publicly available tool for fitting the cold dust SED of galaxies (<https://github.com/roberta96/EOS-Dustfit>), which has been used in this work and in (cite: Tripodi24b). Details about the modeling can be found on the GitHub page and in (cite: Tripodi24b).

[^5]: The Pearson correlation coefficient for the SFE-$\rm L_{bol}$  relation is 0.53 and 0.46 considering all quasars at $z>1$ or the all AGN and quasars shown in the plot, respectively.

</paper>

Write the methods card for this paper.