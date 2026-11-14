# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.532L..36R\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024MNRAS.532L..36R",
 "title": "HCN as a probe of the inner disc in a candidate proto-brown dwarf",
 "year": 2024,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Riaz, B.",
 "n_authors": 3,
 "arxiv_id": "2405.11321",
 "doi": "10.1093/mnrasl/slae044",
 "alma_projects_linked_by_archive": [
  "2021.1.00134.S"
 ]
}
```

Paper text:
<paper>
# HCN as a probe of the inner disk in a candidate proto-brown dwarfSupplementary Material

## Abstract

The detection of Keplerian rotation is rare among Class 0 protostellar systems. We have investigated the high-density tracer HCN as a probe of the inner disk in a Class 0 proto-brown dwarf candidate. Our ALMA high angular resolution observations show the peak in the HCN (3-2) line emission arises from a compact component near the proto-brown dwarf with a small bar-like structure and a deconvolved size of $\sim$50 au. Radiative transfer modelling indicates that this HCN feature is tracing the innermost, dense regions in the proto-brown dwarf where a small Keplerian disk is expected to be present. The limited velocity resolution of the observations, however, makes it difficult to confirm the rotational kinematics of this feature. A brightening in the HCN emission towards the core center suggests that HCN can survive in the gas phase in the inner, dense regions of the proto-brown dwarf. In contrast, modelling of the HCO$^{+}$ (3-2) line emission indicates that it originates from the outer pseudo-disk/envelope region and is centrally depleted. HCN line emission can reveal the small-scale structures and can be an efficient observational tool to study the inner disk properties in such faint compact objects where spatially resolving the disk is nearly impossible.

(stars:) brown dwarfs – stars: formation – stars: evolution – astrochemistry – ISM: molecules – stars: individual: Ser-emb 16

# Introduction

Protoplanetary disks are the potential sites of planet formation, which makes them a key physical component to understand the transition from the late star-formation to the early planet-formation stages. The timescale of the formation of rotational disks is predicted to be during the very early star-formation stages when extremely young stars are in their embedded Class 0 phase (e.g., Andrews et al. 2018). Numerical simulations that consider non-ideal magneto-hydrodynamical effects, radiative transfer, turbulence, and initial conditions, such as, the misalignment between the magnetic field and the rotation axis, predict the formation of small disks of a few tens of au in Class 0 protostars (e.g., Machida et al. 2020). Molecular line interferometric observations have revealed rotational kinematics in a few Class 0 protostars, indicating the presence of a Keplerian disk, with radii of a few tens to a few hundred au (e.g., Aso et al. 2017; Hennebelle et al. 2017; Yen et al. 2017; Maret et al. 2020; Bergner et al. 2021; Chapillon et al. 2012). However, such observational evidence of rotational disks in Class 0 protostars has been very rare, mainly due to the fact that the disks are still deeply embedded in an infalling envelope, which makes it difficult to clearly distinguish the rotational kinematics from infalling motions (e.g., Guzmán et al. 2021; 2015; Qi et al. 2008).

Here, we present an investigation of a disk-like structure in a proto-brown dwarf candidate, Ser-emb 16, which is in its early Class 0 evolutionary stage (Riaz et al. 2018; 2024). Numerical simulations on brown dwarf formation predict sizes of $\leq$10 au for the inner Keplerian disk (e.g., Machida et al. 2009; van Zadelhoff et al. 2003), which is difficult to spatially resolve even in high angular resolution ALMA observations. An alternative way is to use high-density molecular line tracers that can probe the innermost densest regions in compact, dense proto-brown dwarfs. The HCN (3-2) transition line is one such tracer. At a critical density of the order of 10$^{7}$ cm$^{-3}$, it can probe the inner dense regions of a proto-brown dwarf where densities are predicted to be $>$10$^{6}$ cm$^{-3}$ (Machida et al. 2009).

Our target of interest is Ser-emb 16 that is located in the Serpens region ($d$=440$\pm$9 pc) (Ortiz-León et al. 2017; Gong et al. 2021). The bolometric luminosity for Ser-emb 16 is 0.06$\pm$0.01 L$_{\odot}$ and the total (dust+gas) mass (central object mass and circumstellar material) is $\sim$28 M$_{Jup}$ (Riaz et al. 2024), which are well below the sub-stellar limits of $<$0.08 M$_{\odot}$ and $<$0.1 L$_{\odot}$ typically considered in brown dwarf evolutionary models. This YSO is therefore a strong proto-brown dwarf candidate. A detailed discussion on the present and final mass of Ser-emb 16 is presented in Riaz et al. (2024). Paper 1 (Riaz et al. 2024) presented the results in the ALMA continuum and HCO$^{+}$ (3-2) line. Here we present the results from ALMA HCN (3-2) line observations of Ser-emb 16. Previous single-dish IRAM 30m molecular line surveys have identified Ser-emb 16 to be chemically rich (Riaz et al. 2019a; 2022abc; 2023), with strong emission in the HCN (3-2) hyperfine lines (Riaz et al. 2018). We have followed-up with ALMA high angular resolution observations to investigate the origin of the HCN line emission in this proto-brown dwarf.

# Observations and Data Analysis

We observed Ser-emb 16 with ALMA in the HCN (3-2) line at 265.8865 GHz in Band 6. The observations were obtained in Cycle 8 (PID: 2021.1.00134.S) in September, 2022. The primary beam of the ALMA 12m dishes covers a field of $\sim$30 arcsec in diameter. Our chosen configuration was a maximum recoverable scale of $\sim$4 arcsec, and an angular resolution of $\sim$0.4 arcsec. The synthesized beam size of the observations is 0.47$^{\prime\prime} \times$0.38$^{\prime\prime}$. The bandwidth was set to 117.18 MHz, which provides a resolution of 244.14 kHz, or a velocity resolution of $\sim$0.3-0.4 km s$^{-1}$ at 265.8 GHz. One baseband was used for continuum observations where the spectral resolution was set to 976 kHz and the total bandwidth was 1875 MHz. We employed the calibrated data delivered by the EU-ARC. Data analysis was performed on the uniform-weighted synthesized images using the CASA software. We have used the CASA tasks *uvmodelfit* and *imfit* to measure the source size, peak position, position angle, and the line fluxes by fitting one or more elliptical Gaussian components on the continuum and HCN (3-2) line images.

![image](HCN-HFS.eps) ![image](HCN-spec-LTE.eps)

# Results

## Anomalous hyperfine structure

Figure [1](#cont)b shows the observed HCN (3-2) spectrum collapsed over all velocity channels and measured over an area of 3x3 arcsecond that covers the full spatial scale of the observed structures (Fig. [2](#mom0)). The HCN (3-2) spectrum shows hyperfine splitting. The hyperfine structure expected under optically thin LTE conditions is plotted in Fig. [1](#cont)a. HCN (3-2) has six hyperfine components. The central bright feature (labelled ‘A’) is a composite of four components that are not spectrally resolved, and the spectrum has the appearance of a strong central component with two satellite components (labelled ‘B’ and ‘C’). Under optically thin LTE conditions, the relative weightings of the HCN (3-2) hyperfine lines are 0.037:0.926:0.037. The satellite hyperfine components ‘B’ and ‘C’ are thus expected to be of equal intensities, with the B/A and C/A line ratios equal to 0.04, assuming that the level populations of the hyperfine states are in LTE and hence proportional to the statistical weights. Ratios between 0.04 and 1 indicate anomalous sources and imply different hyperfine line ratios than expected due to various effects.

For the case of Ser-emb 16, the HCN-B and HCN-C components have an equal intensity of T$_{mb}$ = 0.16 K, and the HCN-A component is $\sim$5 times stronger with T$_{mb}$ = 0.83 K (Fig. [1](#cont)b). This implies B/A and C/A line ratios of $\sim$0.2. We therefore find hyperfine anomalies that are related to non-equal excitation temperature among the hyperfine lines of a given multiplet. Radiative transfer effects of absorption or scattering of the photons emitted from the high-density core in the less dense outer envelope could produce such anomalies. Other factors such as line trapping effects or extra velocity components along the line of sight, could also produce higher or lower relative line intensity ratios of the hyperfine components than the expected values (e.g., Riaz et al. 2018). The anomalies are further discussed in Sect. [4](#model).

## Moment maps

Figures [2](#mom0)abc show the moment 0 (integrated value of the spectrum) maps individually for the B ($\sim$4-6 km/s), A ($\sim$6.2-8.3 km/s), C ($\sim$8.3-10 km/s) hyperfine components in the HCN (3-2) line. The satellite HCN-B and HCN-C components (Fig. [2](#mom0)ac) show a compact object that overlaps with the continuum emission for Ser-emb 16. In comparison, an extended “spiral” like structure originating from the proto-brown dwarf position is seen for the brightest HCN-A component, with some faint clumps within the spiral (Fig. [2](#mom0)b). The brightest emission in all three components is thus seen originating from the proto-brown dwarf position.

The moment 8 (maximum value of the spectrum) map in the HCN-A component (Fig. [3](#mom8)ab) shows that the peak/maximum in the emission originates from a flattened “bar” like structure that lies very close ($\sim$0.1$\ensuremath{''}$ or $\sim$44 au) to the continuum peak position. The size of this peak emission region deconvolved by the beam is $\sim$0.11$\ensuremath{''}$ ($\sim$50 au) with a PA of 58.8$\ensuremath{^\circ}$. This size was determined by performing a 2D Gaussian fit using the *imfit* task in CASA and restricting the fit to a region excluding the filamentary (or spiral) structure. The origin of this bar-like feature is explored in Sect. [4](#model).

The moment 0 map shows the integrated value of the spectrum, whereas the moment 8 map shows the maximum value of the spectrum. In Fig. [3](#mom8)ab, for the case of the bar, we want to highlight the region of origin of the peak or maximum value of the spectrum, due to which moment 8 is preferred over moment 0 map. For the case of the spiral, moment 0 and 8 show the same results. Thus, moment 8 is necessary to highlight the bar but not to separate the bar and spiral. The distinction between the spiral and bar features is made visually. It is an intensity cut in the moment 8 map. To highlight the bar-like feature, we selected a range in intensities close to the peak value of $\sim$0.04 Jy/beam. For the spiral, the full range in intensities is shown. This indicates that we are seeing the highest intensities in the bar, likely because it is tracing the high-density regions in the proto-brown dwarf system.

The bar-like structure does not have similar strengths across all three components, otherwise this feature could be seen in the moment 8 map for the B and C components. These fainter components are barely detected at a $\sim$3-$\sigma$ level compared to A that is detected at a $>$10-$\sigma$ level. Since B and C are weakly detected, the bar is not visible in these components. The spiral structure is expected to have some contribution near the source position from the fainter B and C components. The extended part or the tail of the spiral as seen in the A component is at least a factor of $\sim$2 fainter than the emission seen close to the source position. It would thus be much more difficult to detect this extended tail of the spiral in the B and C components.

![](mom0-HCN-3.eps)

![](mom8-HCN-5.eps)

# Line radiative transfer modelling

We consider the magnetohydrodynamical simulations presented in Machida, Hirano, & Kitta (2020) of magnetized rotating clouds in which the rotation axis is misaligned with the global magnetic field by an angle ranging between 0$\ensuremath{^\circ}$ and 90$\ensuremath{^\circ}$. At large scales of $>$500 au, the pseudo-disk/envelope in this model is spatially stretched or extended due to the rotation of the proto-brown dwarf core in the presence of a strong magnetic field (Fig. [4](#sim)a; Riaz et al. 2024). Close to the central source ($\leq$200 au), the simulations show distinct physical components of an inner Keplerian disk, a inner pseudo-disk/envelope, a high-velocity jet, and a low-velocity outflow, as shown in the generic model figure in Fig. [4](#sim)b. We have modified the simulations of the Machida et al. (2020) model. The modifications are described in Riaz et al. (2024).

![](model-Mach-2.eps)

We conducted line radiative transfer modelling following the method described in detail in Riaz et al. (2019b). The physical structure, i.e. the radial profiles of density, temperature, and velocity from the simulations is used as an input to the 3D non-LTE radiative transfer code MOLLIE (Keto et al. 2004). Synthetic HCN line profiles convolved by the ALMA beam size are compared with the observed spectrum. A reasonable fit to the strength and width of the observed line profile is reached from varying the abundance profile, the line width, the inclination angle of the system, and the angle between the rotation axis and the global magnetic field. For each synthetic spectrum, a reduced-$\chi^{2}$ value is computed to determine the goodness of fit. From the best line model fit (lowest reduced-$\chi^{2}$ value), model moment maps convolved by the beamsize are produced and compared with the observed maps. We find a model with the HCN molecular abundance relative to H$_{2}$ of (1-2)$\times$10$^{-8}$, an initial misalignment angle of 30$\ensuremath{^\circ}$, and an inclination angle of 60$\ensuremath{^\circ}$ provides the best-fit to the observed spectrum (Fig. [5](#fit)a) and best matches the observed spiral and bar-like structures (Fig. [5](#fit)b-e).

![image](HCN-spec-model.eps)\
![image](HCN-model-1.eps)\
![image](HCN-model-2.eps)

![image](Model-90deg-4.eps)\
![image](HCOp-HCN-l12-profiles.eps)

Modelling indicates that the spiral is tracing the pseudo-disk structure formed by the process of gravitational collapse with the rotation of an east-west angular momentum vector, which will cause the pseudo-disk to drag the magnetic field and finally connect it to the proto-brown dwarf (Fig. [5](#fit)bc). Close to the central proto-brown dwarf, the model map shows a flattened, bar-like structure, similar in size to the observed bar (Fig. [5](#fit)de). The origin of this structure can be seen more clearly in the edge-on (90$\ensuremath{^\circ}$) model map (Fig. [6](#fit-2)a). Here, HCN shows a brightening in emission in the inner most dense region within $\sim$100 au. The bar-like shape of this peak emission region suggests that HCN is tracing the high-density emission towards the inner disk (labelled ‘ID’) in the proto-brown dwarf. Note that since the proto-brown dwarf system is viewed at a $\sim$60$\ensuremath{^\circ}$ angle to the line-of-sight, we are seeing one-sided or asymmetric emission from the disk/pseudo-disk/envelope.

We note that MOLLIE will account for the splitting in the HCN hyperfine components and their relative optical depth effects (e.g., Loughnane et al. 2012; Mullins et al. 2014). The line radiative transfer model originally produces B/A and C/A hyperfine intensity ratios in HCN of $\sim$0.05, which is close to the LTE value of 0.04. Varying the radial profile of the abundance when modelling the observed spectrum produces a noticeable change in these hyperfine component ratios. For e.g., reducing the molecular abundance results in reducing the ratios. When modelling the spiral and the bar, the size of the region where the emission originates from was also constrained. When making the model moment maps from the best-fit to the spectrum, we had matched the intensity scale and the range in velocities in the model with the observations. Therefore, based on the modelling results, we can say that the hyperfine line ratios are truly anomalous.

We have shown through modelling that the spiral and bar structures are tracing different physical components in the Ser-emb 16 system, namely, the spiral is likely tracing the extended/twisted pseudo-disk/envelope regions while the bar is likely tracing the inner Keplerian disk. Different physical regions imply different excitation conditions and different physical conditions, such as, the physical sizes, temperatures, densities, optical depths. Optical depth depends on the level population and the kinetic temperature effects. The effects of these are coupled and cannot be clearly distinguished. The anomalies seen in the HCN hyperfine structure can therefore be due to different hyperfine components tracing different physical regions. Such anomalies cannot be pinpointed to one particular effect.

Figure [6](#fit-2)b shows the HCN abundance profile for the best model fit. There is an enhancement in the HCN abundance towards the core center, which suggests that HCN can survive in the gas phase in the inner, dense regions of the proto-brown dwarf. As shown in the Supplementary Material (Appendix C), the HCO$^{+}$ model moment 0 map generated from the best-fit indicates depletion in the central dense regions where a peak in the HCN emission is seen (Fig. C1 in Appendix C). This is also seen in the abundance profile for HCO$^{+}$ best model fit (Fig. [6](#fit-2)b) where the abundance is depleted towards the core center. The HCN and HCO$^{+}$ molecules thus provide a contrasting view of the internal structure in the proto-brown dwarf, such that, HCN can reveal the small-scale structures in regions where HCO$^{+}$ is depleted.

Our results are consistent with previous studies on molecular line observations of low-mass protostars, which have shown that the depletion of molecular species from the gas phase in the dense interiors of the cores is a highly selective process (e.g., Lee et al. 2004). Molecules like CO and HCO$^{+}$ disappear rapidly from the gas phase and suffer a significant drop in abundance towards the core center, while species like HCN and N$_{2}$H$^{+}$ survive much longer at high densities and are present in the gas phase at the core center.

# Kinematics

Figure [7](#mom9) shows the moment 9 (velocity of the maximum value of the spectrum) map in the HCN (3-2) line (all components). With respect to the V$_{lsr}\sim$8.0 km s$^{-1}$ for Ser-emb 16 (Riaz et al. 2024), the emission at the Ser-emb 16 position and the spiral is blue-shifted and does not show any clear velocity gradient with the distance (or radius) over the narrow velocity range of $\sim$7-7.5 km s$^{-1}$. The moment 1 map shows the intensity weighted coordinate, which is traditionally used to get the “velocity fields”, whereas the moment 9 map shows the velocity of the maximum value of the spectrum. Since there is no velocity gradient seen within the spiral or bar structures, the moment 1 map does not show any velocity fields. The blue- vs. red-shifted velocities can be seen in much more clarity in the moment 9 map than moment 1.

The velocity resolution of our ALMA observations is $\sim$0.3-0.4 km s$^{-1}$. Thus, velocity dispersions of $<$0.6-0.8 km s$^{-1}$ cannot be resolved. This makes it difficult to constrain the position angle and build a position-velocity diagram (PVD) that can help probe the infall and/or Keplerian kinematics for the proto-brown dwarf and the spiral. For a central object mass of 18 M$_{Jup}$ measured for Ser-emb 16, we may find evidence for Keplerian rotation if the velocity spread was $\sim$0.3 km s$^{-1}$ or larger. The non-detection of Keplerian rotation in the bar-like structure is thus mainly due to the limited velocity resolution of the observations. Note that we do not see any jet or outflow for Ser-emb 16, which would support the idea that there is no Keplerian disk in this Class 0 proto-BD system. On the other hand, this also suggests that either the disk has not formed yet or it is still deeply embedded in the pseudo-disk or its size is much smaller than the $\sim$176 au resolution of the observations. Future interferometric observations at a higher velocity and angular resolution can provide more insight into the kinematics of a disk structure in this system.

![](HCN-mom9-2.eps)

The moment 9 map also shows a trail of surrounding cloud material towards the north-west of the spiral and extending to the south of it. This trail is associated with a larger scale streamer seen much more brightly in the HCO$^{+}$ (3-2) line emission (Riaz et al. 2024).

# Conclusions

We have explored if the HCN (3-2) line emission could be a useful tracer of the inner Keplerian disk in a proto-brown dwarf system. We find two prominent features in the ALMA HCN (3-2) line observations at $\sim$0.4$\ensuremath{''}$ angular resolution towards the proto-brown dwarf, Ser-emb 16. One is a flattened, compact, bar-like structure of size $\sim$50 au, and the other is a spatially extended spiral-shaped structure of size $\sim$1610 au. Radiative transfer modelling indicates that the bar-like structure is tracing the inner disk, albeit confirming the Keplerian kinematics will require at least $\sim$10 times higher velocity resolution than the present observations. The spiral-shaped structure is tracing the pseudo-disk that has been twisted due to core rotation. Combining both results, HCN is found to be a good tracer of the pseudo-disk and the inner disk embedded in it in a proto-brown dwarf system.

We also present radiative transfer modelling of ALMA HCO$^{+}$ (3-2) line emission observed close to the Ser-emb 16 position. The best model fit indicates that the HCO$^{+}$ is tracing the outer pseudo-disk/envelope regions at $>$200 au. Based on the modelling results, HCN can trace the innermost, densest regions in the proto-brown dwarf where HCO$^{+}$ is depleted from the gas phase.

# Acknowledgements

B.R. acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG) - Projekt number RI-2919/2-3.

# Data Availability

The data underlying this article are available in the ALMA archives through the ALMA online database.

99

(ref: ) Andrews et al. 2018, ApJL, 869:L41

(ref: ) Aso, Yusuke et al., 2017, ApJ, 849, 1

(ref: ) Bergner et al. 2021, ApJSS, 257, 11

(ref: ) Chapillon et al. 2012, A&A, 537, A60

(ref: ) Y. Gong, A. Belloche, F. J. Du et al. 2021, A&A, 646, A170

(ref: ) Guzmán et al. 2021, ApJSS, 257, 6

(ref: ) Guzmán et al. 2015, ApJ, 814, 53

(ref: ) Hennebelle, Patrick; Lesur, Geoffroy Fromang, Sebastien, 2017, A&A, 599, A86

(ref: ) Lee, Chang Won ; Myers, Philip C. ; Plume, Rene, 2004, ApJSS, 153, 523

(ref: ) Loughnane et al. 2012, MNRAS, 420, 1367

(ref: ) Maret, S. et al. 2020, A&A, 635, A15

(ref: ) Machida, Masahiro N.; Inutsuka, Shuichiro; Matsumoto, Tomoaki 2009, ApJ, 699, 157

(ref: ) Masahiro N. Machida, Shingo Hirano & Hideyuki Kitta, 2020, MNRAS, 491, 2180

(ref: ) Mullins et al. 2014, MNRAS, 459, 2882

(ref: ) Qi et al. 2008, ApJ, 681,1396

(ref: ) Ortiz-Leon G. N. et al., 2017, ApJ, 834, 141

(ref: ) Oberg et al. 2011, ApJ, 734, 98

(ref: ) Riaz, B. Thi, W. -F.; Caselli, P., 2018, MNRAS, 481, 4662

(ref: ) Riaz, B. Thi, W. -F.; Caselli, P., 2019a, MNRAS, 483, 1139

(ref: ) Riaz, B. Machida, M. N., Stamatellos, D., 2019b, MNRAS, 486, 4114

(ref: ) Riaz, B., Thi, W. -F. 2022a, MNRAS, 511, 6110

(ref: ) Riaz, B., Thi, W. -F. 2022b, MNRAS, 511, L50

(ref: ) Riaz, B., Thi, W. -F. 2022c, MNRAS, 514, 3604

(ref: ) Riaz, B., Thi, W. -F., Machida, M. N. 2023, MNRAS, 522, 4934

(ref: ) Riaz, B., Stamatellos, D., Machida, M. N., 2024, MNRAS, 529, 3601

(ref: ) van Zadelhoff et al. 2003, A&A, 397, 789

(ref: ) Yen, Hsi-Wei et al. 2017, ApJ, 834, 178

# Sizes, gas masses and densities

We have used the CASA task *imfit* to measure the source size, peak position, position angle, and the line fluxes by fitting one or more elliptical Gaussian components on the continuum and HCN (3-2) line images. The size of Ser-emb 16 measured in the continuum image was used to measure the HCN line fluxes. The integrated and peak HCN (3-2) flux for Ser-emb 16 is 37.88$\pm$5.3 mJy and 31.6$\pm$2.0 mJy beam$^{-1}$. The H$_{2}$ gas mass derived from the HCN column density is 2.8$\pm$0.3 M$_{Jup}$, and the H$_{2}$ gas number density is (1.2$\pm$0.2)$\times$10$^{7}$ cm$^{-3}$.

The size of the spiral, both convolved and deconvolved with the beam, is 3.0$\ensuremath{''} \pm$0.6$\ensuremath{''}$ along the major axis and 2.1$\ensuremath{''} \pm$0.1$\ensuremath{''}$ along the minor axis, with a PA of 128.9$\ensuremath{^\circ}$$\pm$4.6$\ensuremath{^\circ}$. The projected size of the spiral is 1610$\pm$264 au. The integrated and peak HCN (3-2) flux for the spiral is 23.4$\pm$3.2 mJy and 23.1$\pm$2.7 mJy beam$^{-1}$. The H$_{2}$ gas mass derived from the HCN column density is 12.2$\pm$0.5 M$_{Jup}$, and the H$_{2}$ gas number density is (0.2$\pm$0.01)$\times$10$^{7}$ cm$^{-3}$.

# Comparison of HCN and HCO$^{+}$ maps

![](HCN-HCOp-3.eps)

The spectral setup in our ALMA observations included the HCO$^{+}$ (3-2) line. A detailed discussion on the HCO$^{+}$ results are presented in Riaz et al. (2024). Here, we present a comparison of the HCN and the HCO$^{+}$ line maps. Figure [8](#hcop) shows an overlap of the HCN and HCO$^{+}$ moment 0 maps close to the central Ser-emb 16 source \[panel (a)\] and a zoomed-out view of the large-scale ($\sim$2000 au) spiral structure seen in both lines \[panel (b)\]. Close to the proto-brown dwarf position as traced by the continuum emission (red contours), the HCN emission peaks at an offset of $\sim$0.15$\ensuremath{''} \sim$66 au while HCO$^{+}$ peaks at an offset of $\sim$0.4$\ensuremath{''} \sim$176 au. The HCO$^{+}$ peak is thus twice the distance away from the proto-brown dwarf position than the HCN peak. The HCO$^{+}$ is also more spatially extended, with a spatial extent of $\sim$167 au vs $\sim$123 au for HCN emission close to the central proto-brown dwarf source \[Fig. [8](#hcop); panel (a)\].

If we zoom out over a larger spatial scale \[Fig. [8](#hcop); panel (b)\], then the spiral structure is seen in both lines but the spatial scale (both length and width) is larger by a factor of $\sim$1.5 in HCO$^{+}$ than in HCN. HCN is therefore tracing the more compact and high-density material close to the central proto-brown dwarf source. As discussed in Sect. 4 (main paper) and Sect. [10](#hcop-model), line radiative transfer modelling indicates that the HCN peak emission originates from the inner disk, while HCO$^{+}$ emission originates from the outer pseudo-disk/envelope in the proto-brown dwarf. These lines are therefore tracing different physical components, the evidence of which is clearly seen in the position offset and spatial extent in the line maps (Fig. [8](#hcop)ab).

Interestingly, there is no streamer seen in the HCN (3-2) line map, unlike the impressive large-scale streamer seen in the HCO$^{+}$ (3-2) line (Riaz et al. 2024). The HCO$^{+}$ (3-2) line has an order of magnitude lower critical density of the order of 10$^{6}$ cm$^{-3}$ than the HCN (3-2) line. The surrounding cloud material around an extremely young proto-brown dwarf is expected to be of low density, and thus would be detectable in a comparatively low density tracer such as HCO$^{+}$ than HCN.

Figure [8](#hcop)c compares the observed HCN (3-2) and HCO$^{+}$ (3-2) spectra collapsed over all velocity channels. The peak intensity has been normalized to one; the normalization factor is 0.82 for HCN and 2.14 for HCO$^{+}$. The HCO$^{+}$ peak intensity is $\sim$2.6 times higher than HCN. The blue-shifted brighter peak in HCO$^{+}$ shows a similar spectral profile as the HCN-A component. Both of these peaks are dominated by the emission from the bright spiral structure (Riaz et al. 2024). The much fainter red-shifted peak in HCO$^{+}$ does not overlap with the HCN satellite components. As discussed in Riaz et al. (2024), this fainter HCO$^{+}$ peak arises from a large-scale streamer that is not observed in the HCN line map.

Note that since the proto-brown dwarf system is viewed at a $\sim$60$\ensuremath{^\circ}$ angle to the line-of-sight, we are seeing one-sided or asymmetric emission from the disk/pseudo-disk/envelope, which could explain why HCN peaks at a slight offset inward of the continuum position while HCO$^{+}$ peaks slightly outward of it (Fig. [8](#hcop)a).

# HCO$^{+}$ Modelling

A detailed modelling of the large-scale spiral structure seen in the HCO$^{+}$ (3-2) line is presented in Riaz et al. (2024). Here we present results from modelling the HCO$^{+}$ emission close to the central proto-brown dwarf (Fig. [8](#hcop)a). We used the same modified physical model by Machida et al. (2020) as used for the HCN data. The best model fit is shown in Fig. [9](#hcop-fit)a. The model moment 0 map produced from the best line model fit (Fig. [9](#hcop-fit)c) shows a twist around $\sim$0.3$\ensuremath{''}$ or $\sim$130 au, which is likely a line-of-sight effect.

Fig. [9](#hcop-fit)d shows the model image at an edge-on inclination. The peak in the HCO$^{+}$ emission is seen in the outer pseudo-disk/envelope regions at $>$200 au (labelled ‘PD/IE’), and in the boundary layers (labelled ‘BL’) between the high-velocity jet and the inner pseudo-disk/envelope regions. The model also predicts a significant decline in the HCO$^{+}$ intensity towards the central regions (labelled ‘CD’). This suggests that the HCO$^{+}$ molecule is depleted in the inner, dense regions of the proto-brown dwarf.

![image](HCOp-model.eps)\
![image](Model-Env.eps)

[^1]: E-mail: briaz@usm.lmu.de

</paper>

Write the methods card for this paper.