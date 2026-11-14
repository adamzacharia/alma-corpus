# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A..86Y\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694A..86Y",
 "title": "ALMA observations of massive clouds in the central molecular zone: slim filaments tracing parsec-scale shocks",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Yang, Kai",
 "n_authors": 25,
 "arxiv_id": "2502.03913",
 "doi": "10.1051/0004-6361/202453191",
 "alma_projects_linked_by_archive": [
  "2016.1.00243.S",
  "2016.1.00875.S"
 ]
}
```

Paper text:
<paper>
# ALMA observations of massive clouds in the central molecular zone: slim filaments tracing parsec-scale shocks

The central molecular zone (CMZ) of our Galaxy exhibits widespread emission from SiO and various complex organic molecules (COMs), yet the exact origin of such emission is uncertain. Here we report the discovery of a unique class of long ($>$0.5 pc) and narrow ($<$0.03 pc) filaments in the emission of SiO 5–4 and eight additional molecular lines, including several COMs, in our ALMA 1.3 mm spectral line observations toward two massive molecular clouds in the CMZ, which we name as slim filaments. However, these filaments are not detected in the 1.3 mm continuum at the 5$\sigma$ level. Their line-of-sight velocities are coherent and inconsistent with being outflows. The column densities and relative abundances of the detected molecules are statistically similar to those in protostellar outflows but different from those in dense cores within the same clouds. Turbulent pressure in these filaments dominates over self gravity and leads to hydrostatic inequilibrium, indicating that they are a different class of objects than the dense gas filaments in dynamical equilibrium ubiquitously found in nearby molecular clouds. We argue that these newly detected slim filaments are associated with parsec-scale shocks, likely arising from dynamic interactions between shock waves and molecular clouds. The dissipation of the slim filaments may replenish SiO and COMs in the interstellar medium and lead to their widespread emission in the CMZ.

# Introduction

The central molecular zone (CMZ), usually referring to the inner 500 pc of the Galaxy, is a gas reservoir of total mass of several times $10^7$ $M_\odot$ and mean density at $10^4$ cm$^{-3}$ (cite: morris1996; ferriere2007; longmore2013a) yet with unexpectedly inefficient star formation (cite: longmore2013a; kruijssen2014; barnes2017; 2023ASPC..534...83H). Prominent parsec-scale shocks have been suggested to be widespread in the CMZ, manifested by the measured molecular line widths of 5–10 km s$^{-1}$, a factor of $\gtrsim$10 broader than those measured toward nearby clouds at the same scale (cite: baobab2013; henshaw2016a), as well as the ubiquitous SiO emission in the cloud scale (cite: martinpintado1997; baobab2013; minh2015). The shocks are suggested to heat the gas, leading to the de-coupling of gas and dust temperatures in the clouds (cite: ao2013; mills2013; ginsburg2016; immer2016; krieger2017; lu2017), and to be related to the unique “hot-core like” chemistry with widespread complex organic molecules (COMs) in the cloud scale (cite: martinpintado2001; requenatorres2006; requenatorres2008; menten2009).

The origin of the parsec-scale shocks in the CMZ is unclear. Similar parsec-scale shocks have been discussed toward massive star forming clouds in the Galactic disk (cite: jimenezserra2010; jimenezserra2014; nguyenluong2013; cosentino2018), which are often attributed to collisions between clouds. Dynamic interactions such as collisions, shear motions, or inflow along the bar may be more frequent for clouds in the CMZ given the high volume densities of clouds (cite: kruijssen2014; kruijssen2019a; li2020; inutsuka2021).

Recent high resolution observations using the Atacama Large Millimeter/submillimeter Array (ALMA) have detected filamentary molecular gas structures in the CMZ clouds. (cite: bally2014) discovered molecular absorption filaments in HCO$^+$ in the massive cloud G0.253+0.016, and proposed that the broad-line absorption filaments (with line widths $>$ 20 km s$^{-1}$) could be foreground magnetic structures and the narrow-line absorption filaments (with line widths $<$ 20 km s$^{-1}$) may trace optically thick gas on the front expanding surface of this cloud. (cite: wallace2022) identified CO filaments running parallel to the Galactic plane in the Sgr E cloud and argued that the gravitational influence of the Galactic bar is responsible for these filaments by stretching molecular gas in this region. (cite: 2022MNRAS.509.4758H) identified an arc-shaped HNCO emission feature in G0.253+0.016, which is believed to result from a bubble swept up by winds or stellar feedback driven by star formation. In addition, a bubble-shaped HNCO emission feature M0.8$-$0.2 was reported by (cite: 2024A&A...691A..70N), which is thought to be the outcome of a high-energy hypernova explosion. However, none of these filaments were thought to be directly related to parsec-scale shocks. Meanwhile, in nearby star-forming regions, interferometric observations have identified shock-related filamentary structures using shock tracers, particularly SiO (cite: 2019ApJ...881L..42C; 2022A&A...667A...6C; desimone2022).

Using emissions from nine spectral lines at 1.3 mm, observed with ALMA toward two massive clouds in the CMZ, we have discovered a population of narrow ($<$0.03 pc) filamentary structures, which are not visible in dust emission, termed “slim filaments”. These slim filaments are likely related to parsec-scale shocks, which could be indicative of active dynamic interactions within the clouds. We adopt a distance of 8.1 kpc to the CMZ (cite: reid2019).

# Observations

|  |  |  |  |  |
|:---|:---|:--:|---:|:--:|
| Molecule | Transition | Rest frequency | $E_{u}/k$ | $n_{\rm crit}^{(a)}$ |
|  |  | (MHz) | \(K\) | (cm$^{-3}$) |
| SiO | 5–4 | 217104.98 | 31.3 | 2.6$\times$10$^{6}$ |
| c-C$_3$H$_2$ | 6$_{1,6}$–5$_{0,5}$ | 217822.15 | 38.6 | 4.5$\times$10$^{7}$ |
| H$_2$CO | 3$_{0,3}$–2$_{0,2}$ | 218222.19 | 21.0 | 3.4$\times$10$^{6}$ |
| HC$_3$N | 24–23 | 218324.72 | 131.0 | 1.7$\times$10$^{7}$ |
| CH$_3$OH | 4$_{2,2}$–3$_{1,2}$ | 218440.06 | 45.5 | 7.8$\times$10$^{7}$ |
| HNCO | 10$_{0,10}$–9$_{0,9}$ | 219798.27 | 58.0 | 7.6$\times$10$^{6}$ |
| H$_2$$^{13}$CO | 3$_{1,2}$–2$_{1,1}$ | 219908.53 | 32.9 | 4.8$\times$10$^{6}$ |
| SO | 6$_{5}$–5$_{4}$ | 219949.44 | 35.0 | 2.3$\times$10$^{6}$ |
| CH$_3$CN | 12$_{1}$–11$_{1}$ | 220743.01 | 76.0 | 4.5$\times$10$^{6}$ |
|  | 12$_{0}$–11$_{0}$ | 220747.26 | 68.9 | 4.1$\times$10$^{6}$ |

: Spectral lines detected in the slim filaments.

\
Notes. $^{\rm (a)}$ The critical density is calculated based on Einstein coefficients $A_{\rm ul}$ and collisional rate coefficients $C_{\rm ul}$ from the Leiden Atomic and Molecular Database (cite: lamda2005): via the approximation $n_{\rm crit}$ = $A_{\rm ul}$/$C_{\rm ul}$ (cite: shirley2015) at a temperature of $\sim$100 K. For the case of H$_2$$^{13}$CO, we give the critical density for the 3$_{1,2}$–2$_{1,1}$ transition of the main isotope.

The ALMA observations and data reduction were detailed in (cite: lu2020) and (cite: lu2021), which have focused on 2000-au scale cores and protostellar outflows in the CMZ, respectively. Here, we summarize the key points. The observations toward four clouds in the CMZ were performed with the C40-3 and C40-5 configurations in 2017 April and July (project code: 2016.1.00243.S) and within frequency ranges of 217–221 GHz and 231–235 GHz. The sample includes the 20 km s$^{-1}$ cloud, the 50 km s$^{-1}$ cloud, cloud e, and Sgr C. The image cubes have been produced with the tclean task in CASA following the procedures outlined in . The synthesized beam size of the images is on average 0$''$28$\times$0$''$19 (equivalent to 2200 AU$\times$1500 AU) but slightly varies between lines. The maximum recoverable angular scale is 10$''$ ($\sim$0.4 pc). The continuum rms measured in the emission-free regions without primary beam corrections is 40 $\mu$Jy beam$^{-1}$, with a central frequency of 226 GHz. The spectral line rms is between 1.6–2.0 mJy beam$^{-1}$ (0.8–1.0 K in brightness temperatures) per 0.976 MHz channel (corresponding to 1.35 km s$^{-1}$ at 217.105 GHz).

![](fig1.pdf)

# Results

## Identification of the slim filaments

identified 43 protostellar outflows from emissions of six potential shock tracers (SiO, SO, HNCO, H$_2$CO, HC$_3$N, and CH$_3$OH, with transitions listed in [1](#tab_lines)). Interestingly, apart from these outflows, filamentary structures not associated with any dust emission are found in three regions in the 20 km s$^{-1}$ cloud and one region in the 50 km s$^{-1}$ cloud. In this letter, we focused on the SiO 5–4 transition that has been suggested to primarily trace shock activities, including not only outflow-associated fast shocks (e.g., (cite: 2007prpl.conf..245A); (cite: 2007ApJ...654..361Q); (cite: 2011A&A...526L...2L); (cite: 2024ApJ...960...48T)), but also slow shocks (with emissions mostly within $\pm$5 km s$^{-1}$ of the cloud $V_{\rm LSR}$, e.g., (cite: 2007A&A...476.1243M); (cite: 2014A&A...570A...1D); (cite: 2016A&A...586A.149C); (cite: 2016A&A...595A.122L); (cite: 2016ApJ...824...99M); (cite: 2024A&A...684A.140Y)).

As shown in panel (a) of [1](#fig:zoomin), a MeerKAT continuum map (cite: heywood2022) illustrates the positions of the two filament-detected clouds relative to Sgr A$^{\star}$. Panels (b) and (c) present the integrated intensity maps of the SiO 5–4 line toward the clouds, obtained from ALMA low-resolution ($\sim$1.9$^{\prime\prime}$) observations (project code: 2016.1.00875.S). Panels (d)–(g) display zoomed-in views of the filamentary structures captured with our ALMA high-resolution observations.

We identified the slim filaments through visual inspection by the following criteria: the filaments should have spatially continuous SiO 5–4 integrated line emission with a signal-to-noise ratio greater than 3, a coherent velocity structure in the position-velocity diagram, and an aspect ratio greater than 10. The skeletons, lengths, widths, and velocity structures of the filaments are detailed in Section [3.2](#subsec:basic_para). In the 50 km s$^{-1}$ cloud, we detected two slim filaments oriented in the west-east direction. In the A region of the 20 km s$^{-1}$ cloud, identified two bipolar outflows. Additionally, a filamentary structure with several branches was identified north of the outflows, and two straight filaments were found to the west of the outflows. In the B and C regions, we found two curved filaments and a north-south oriented filament, respectively. Notably, these filaments are not detected in the dust emission at the 5$\sigma$ level of 0.2 mJy beam$^{-1}$. As shown in panels (b) & (c) of [1](#fig:zoomin), similar filamentary emissions were also found in the low-resolution ALMA SiO images, suggesting that the slim filaments are unlikely to be a result of spatial filtering.

The integrated intensity maps of other potential shock tracers in the 50 km s$^{-1}$ cloud are presented in Figures [2](#fig:m0_d_app), where these filaments are also detected in the emissions of these tracers. The integrated maps of these molecular lines toward slim filaments in the 20 km s$^{-1}$ cloud are shown in [6](#app_sec:fila). In some cases, the filaments are even marginally detected in the emission of CH$_3$CN 12$_{0/1}$–11$_{0/1}$, H$_2$$^{13}$CO 3$_{1,2}$–2$_{1,1}$, and c-C$_3$H$_2$ 6$_{1,6}$–5$_{0,5}$, which are usually detected in star forming dense cores.

![](fig6_filaD_app.pdf)

Considering their slim morphology and unique properties (e.g., high velocity dispersions, see Section [3.2](#subsec:basic_para)), these filaments represent distinctive structures within the CMZ that have not been seen elsewhere in the Galaxy. We note that the identified slim filaments are by no means a complete sample of such objects in the surveyed clouds. A few ambiguous candidates may exist in cloud e and Sgr C. (cite: 2024arXiv241009253C) identified morphologically similar filaments in Sgr C using the JWST-NIRCam H$_{2}$ image, which might trace shocked molecular gas as well. However, in this letter, we intended to report the first detection and characterization of such objects, and therefore only focused on the most robust candidates.

## Characteristics of the slim filaments

### Widths

Based on the SiO 5–4 integrated intensity maps, we use the python-based package `FilFinder`[^1] (cite: 2015MNRAS.452.3435K) to compute the filament skeletons (extraction processes are detailed in [7](#app_sec:filfinder)). To determine the Full Width at Half Maximum (FWHM) of the filaments, we extract intensity profiles perpendicular to the skeletons at intervals of every 5 pixels (about one beam size) and perform Gaussian fits to the mean radial profile. The Gaussian function is expressed as:

$$\begin{equation}
\label{fib_wid}
A(r) = A_{0}~{\rm exp}\left( \frac{-(r- \mu )^{2}}{2 \sigma^{2}_{\rm G}} \right) ,\\
\end{equation}$$

where $A(r)$ represents the profile amplitude at the radial distance $r$, $A_{0}$ is the amplitude, $\mu$ is the mean, and $\sigma_{\rm G}$ is the standard deviation. The best-fit FWHMs of the 50 km s$^{-1}$ cloud and the 20 km s$^{-1}$-A, B, C regions are 0.025, 0.025, 0.026, and 0.028 pc, respectively. The overall best-fit FWHM for all the filaments is 0.026 pc, with the corresponding Gaussian curve shown as the red solid line in [3](#fig:widths). Considering the half-power beam width ($\rm FWHM_{\rm bm}$) of about 0.23$^{\prime\prime}$ ($\sim$ 0.009 pc), the beam-deconvolved FWHM can be estimated by FWHM$_{\rm decon}$ = $\sqrt{\rm FWHM^{2} - \rm FWHM_{\rm bm}^{2}}$ to be about 0.024 pc, approximately 3 times the beam size, which is narrower than the characteristic width of 0.1 pc toward dense gas filaments in nearby clouds (cite: 2011A&A...529L...6A; 2019A&A...621A..42A; 2022A&A...667L...1A). We will demonstrate in Section [4.1](#subsec:equi) that these slim filaments exhibit fundamentally different dynamic states compared to nearby filaments.

![](fig2_fila_width.pdf)

### Velocity dispersions

The velocity dispersion, $\sigma_{v}$, is estimated as:

$$\begin{equation}
\label{velo_disp}
\begin{split}
\sigma_{v} &= \sqrt{\sigma_{\rm nt,SiO}^{2}+c_{s}^{2}} \\
           &= \sqrt{\sigma_{\rm obs}^{2} - \frac{\Delta_{\rm ch}^{2}}{(2\sqrt{\rm 2ln2})^{2}} - \frac{k_{B}T}{\mu_{\rm SiO} m_{p}} + \frac{k_{B}T}{\mu_{p}m_{p}}}
\end{split}
\end{equation}$$

where $\sigma_{\rm nt}$ represents the non-thermal velocity dispersion, $c_{s}$ is the isothermal sound speed, $\Delta_{\rm ch}$ is channel width, $k_{B}$ is the Boltzmann constant, $T$ is gas temperature, $\mu_{\rm SiO}$ is the molecular weight of 44 for SiO, $\mu_{p}$ = 2.37 is the mean molecular weight per free particle (cite: 2008A&A...487..993K), and $m_{p}$ is the proton mass. The observed velocity dispersion, $\sigma_{\rm obs}$, is derived by fitting the averaged spectra (details provided in [8](#appd_sec:widths)) with values of 5.7, 4.5, 4.5, and 3.8 km s$^{-1}$ for the 50 km s$^{-1}$ cloud and the 20 km s$^{-1}$-A, B, C regions, respectively. The typical gas temperature is approximately 70 K adopted from . Finally, the velocity dispersions, $\sigma_{v}$, toward these four regions are found to be 5.6, 4.4, 4.4, and 3.7 km s$^{-1}$ respectively, corresponding to FWHM line widths of 13.2, 10.4, 10.4, and 8.9 km s$^{-1}$.

### Velocity structures

The position-velocity (PV) diagrams for the slim filaments, shown in [4](#fig:pv), are derived along the dashed lines in [1](#fig:zoomin). Most of the slim filaments exhibit emissions around the systematic velocity, and their PV diagrams display consistent velocities along their major axes (with FWHM line widths of $\sim$10 km s$^{-1}$).

The SiO 5–4 transition was used to identify outflows in the CMZ in . However, as shown in [4](#fig:pv), the slim filaments do not show apparent velocity gradients along the major axes that are typically observed in outflows (cite: 2001ApJ...554..132A; 1996ApJ...459..638L). Therefore, it is unlikely that they are outflows.

![](fig3_pv_plot.pdf)

## Relative Abundances of the Molecules and Comparison to Outflows

Assuming local thermodynamic equilibrium (LTE) conditions and optically thin line emission, we estimated the column densities of the nine molecules (listed in [1](#tab_lines)) at the SiO peak positions on the filament branches (shown as green stars in [6](#fig:maser)). The method is detailed in [9](#appd_sec:column). Similar method has been used in for calculating column densities of six molecules toward protostellar outflows in the CMZ. However, without detectable dust emission, we were unable to constrain the total molecular hydrogen column densities in the filaments. Consequently, we could only provide lower limits for molecular abundances and relative abundances between the molecules.

We normalized the abundances of the nine molecules with respect to that of CH$_3$OH and plot the relative abundances in [5](#fig:abund). To understand the relative abundances, we compared our results with outflow studies toward the same star-forming clouds in the CMZ . Additionally, CH$_3$CN and H$_2$$^{13}$CO are rarely found in outflows. The outflow of a high-mass protostar IRAS 20126+4104 (cite: 2017MNRAS.467.2723P) allows us to compare the column densities of these two molecules to that of CH$_3$OH. The mean values of relative abundances in the outflows and dense cores in the CMZ, and IRAS 20126+4104 are also shown.

We performed a two-sample Kolmogorov-Smirnov test to compare the relative abundances in the slim filaments and outflows in the CMZ. In the test, a small *p*-value (typically $<$ 0.05) indicates that the two distributions under consideration are significantly different. The *p*-value is 0.68, indicating no significant evidence that they come from different distributions. We found no significant difference between the relative abundances in the filaments and the IRAS 20126+4104 outflow with a $p$-value of 0.14. However, the *p*-value between the relative abundances in the filaments and dense cores in the CMZ is 0.02, indicating that they are statistically different from each other.

![](fig4_Abundance.pdf)

# Discussion

![](fig5_maser_spots.pdf)

## A new class of filaments

Many studies of filaments in nearby clouds are based on the assumption of hydrostatic equilibrium (cite: 2011A&A...529L...6A; 2016A&A...586A..27K; 2018A&A...610A..77H), which suggest a balance among pressures from turbulence, gravity, thermal motions, magnetic fields, and the external environment. In this study, we estimate these pressures and examine the radial equilibrium of the slim filaments.

The turbulent pressure can be estimated using $P_{\rm turb}$ = $\rho\sigma_{v}^{2}$. We adopt a mean $\sigma_{v}$ value of 4.4 km s$^{-1}$ from Section [3.2.2](#subsec:linewidths). The gas density, $\rho$ = $n m_{\rm H}$, depends on the density, $n$, which we estimate as follows. Given the slim filaments are detected with dust emission under a 5$\sigma$ level, the upper limit of the column density, $N_{\rm H_{2}}$, can be derived from the continuum emission using the following equation:

$$\begin{equation}
\label{equa_col}
N_{\rm H_{2}} = \eta \frac{S_{\nu}}{B_{\nu}(T_{\rm dust})~\Omega~\kappa_{\nu}~\mu_{\rm H_{2}}~m_{p}}
\end{equation}$$

where $\eta$ = 100 is the assumed gas-to-dust mass ratio, $S_{\nu}$ is the continuum flux density, $B_{\nu}(T_{\rm dust})$ is the Plank function at dust temperature $T_{\rm dust}$ = 20 K following (cite: kauffmann2017a) and frequency $\nu$ = 226 GHz, $\Omega$ is the solid angle, $\kappa_{\nu}$ is the dust opacity, and $\mu_{\rm H_{2}}$ = 2.8 is the mean molecular weight of the interstellar medium (cite: 2008A&A...487..993K). We adopt $\kappa_{\nu}$ = 0.817 cm$^{2}$g$^{-1}$, assuming $\kappa_{\nu}$ = 10 $\times$ ($\nu$/1.2 THz)$^{\beta}$ cm$^{2}$g$^{-1}$ with $\beta$ = 1.5 (cite: 1983QJRAS..24..267H). Considering the dust emission at the 5$\sigma$ level of 0.2 mJy beam$^{-1}$, the upper limit for the column density is calculated to be 2.3 $\times$ 10$^{23}$ cm$^{-2}$. Assuming that the thickness along the line of sight is the same as the slim filament width of 0.024 pc (see Section [3.2.1](#subsec:disc_width)), the estimated upper limit of the density $n$ is approximately 3.1 $\times$ 10$^{6}$ cm$^{-3}$. This yields a turbulent pressure $P_{\rm turb}$/$k_{\rm B}$ of approximately 1.7 $\times$ $10^{10}$ K cm$^{-3}$.

The thermal pressure is calculated as $P_{\rm th}$/$k_{\rm B}$ = $\rho T$/$\mu_{p} m_{p}$, resulting in 9.2 $\times$ $10^{7}$ K cm$^{-3}$. The gravitational pressure, given by $P_{\rm gravity}$ $\propto$ $G\rho^{2}L^{2}$/$\pi$, is estimated to be $P_{\rm gravity}$/$k_{\rm B}$ of 1.3 $\times$ 10$^{8}$ K cm$^{-3}$. The magnetic pressure $P_{\rm mag}$/$k_{\rm B}$, which reaches the maximum $P_{\rm mag}$ = $B^{2}$/8$\pi$ when the magnetic field lines are parallel to the filament, is about 6.6 $\times$ $10^{7}$ K cm$^{-3}$ for a magnetic strength of 0.48 mG from (cite: 2024ApJ...962...39L). Additionally, the external pressure, $P_{\rm ex}$/$k_{\rm B}$, is estimated using $\rho_{\rm ex} \sigma_{\rm ex}^{2}$ + $\rho_{\rm ex} T$/$\mu_{p} m_{p}$. We obtain median values from (cite: lu2019a), with an external density of 4.4 $\times$ 10$^{5}$ cm$^{-3}$ and a external velocity dispersion of 1.43 km s$^{-1}$. Therefore, the external pressure is calculated to be approximately 2.6 $\times$ 10$^{8}$ K cm$^{-3}$.

Our results show that the turbulent pressure is two to three orders of magnitude higher than the other estimated pressures, suggesting that

the slim filaments are not in hydrostatic equilibrium. The high turbulent pressure could lead to the expansion and eventual dissipation of these filaments. These findings indicate that the slim filaments differ significantly from the dense gas filaments typically observed in nearby molecular clouds that are usually considered to be in hydrostatic equilibrium (cite: wang2014; lu2018).

With the filament width of 0.024 pc and the typical velocity dispersion of 4.5 km s$^{-1}$, the dissipation timescale of the filaments is estimated to be $\sim$5.2 $\times$ 10$^{3}$ years, which is comparable with the freeze-out timescale of SiO (cite: 1998ApJ...499..777B; 1999A&A...343..585C). Under the assumptions of LTE conditions, optically thin line emission, and an excitation temperature of 70 K, we estimate a SiO mass of 1.3 $M_{\odot}$ in the CMZ based on the SiO 5–4 line emission within a velocity range of $-$50 to 120 km s$^{-1}$ from APEX observations (cite: ginsburg2016). This estimate covers an area of 325 $\times$ 56 pc$^{2}$ in the CMZ, with detailed calculations provided in [9](#appd_sec:column). This corresponds to a SiO depletion rate of $\sim$1.3 $\times$ 10$^{-4}$ $M_{\odot}$ yr$^{-1}$.

For our detected slim filaments, the median SiO mass is 8.1 $\times$ 10$^{-5}$ $M_{\odot}$, meaning that each filament contributes an SiO replenishment rate of $\sim$1.6 $\times$ 10$^{-8}$ $M_{\odot}$ yr$^{-1}$. To maintain a balance between the replenishment and depletion, about 8000 filaments would be required over the CMZ, which amounts to a slim filament surface density of $\sim$0.4 pc$^{-2}$. Toward the observed regions in the 20 km s$^{-1}$ cloud and the 50 km s$^{-1}$ cloud where the total area is $\sim$15 pc$^{-2}$, 10 slim filaments have been identified, leading to a surface density of $\sim$0.7 pc$^{-2}$.

If the slim filaments ubiquitously exist throughout the CMZ at a similar surface density, their dissipation would be sufficient to refuel the widespread SiO emission in the CMZ while this molecule is simultaneously freezing out onto dust grains, achieving a balance between the replenishment and depletion. Meanwhile, several COMs, such as CH$_3$OH, CH$_3$CN, H$_2$CO, and HC$_3$N in the slim filaments would be released into the interstellar medium (ISM), which might explain the widespread emission of COMs in the CMZ. A CMZ-wide census of slim filaments is necessary to confirm this possibility.

## Possible origin of the slim filaments

The slim filaments exhibit unique morphology, velocity structures, relative molecular abundances, and dynamic states, suggesting that they may have a different origin than the dense gas filaments found in nearby clouds. We find several clues suggesting that the slim filaments are related to shock activities:

- The rotational transitions of SiO in the ISM are usually suggested to trace shocks because Si atoms can be released from dust grains through sputtering or vaporization caused by shock activities (cite: schilke1997). The shock activities consist of high-velocity shocks from outflows and low-velocity shocks with unclear origins (cite: 2014A&A...570A...1D; 2016A&A...595A.122L; 2024ApJ...960...48T).

- Class I CH$_3$OH masers are believed to be collisionally pumped (cite: 2014MNRAS.439.2584V), and are found in all the four regions with slim filaments (marked by orange crosses in [6](#fig:maser)). While widespread CH$_3$OH masers are observed in the CMZ and are thought to result from photodesorption driven by cosmic rays (cite: yusefzadeh2013), the masers in these regions are likely generated by shock activities, as their velocities are consistent with the $V_{\rm lsr}$ of the SiO emissions observed in the filaments, hinting a shocked environment.

- Statistically, the relative abundances of the molecules in the slim filaments are similar to those in other shocked regions such as protostellar outflows, while they are different from those in dense cores, suggesting their closer relation to shocks instead of protostellar heating.

Under shock conditions, the non-detection of thermal dust emission at the 5$\sigma$ level can be explained if: (i) the shocks have destroyed most, if not all, of the dust grains, releasing Si into the gas phase; or (ii) the initial dust emission is diffuse, and a shock wave can efficiently sputter Si atoms and form SiO. In the latter case, the dust emission remains undetectable by ALMA due to missing flux, a phenomenon similar to shocks in outflows interacting with surrounding gas.

In [1](#fig:zoomin), we notice that the regions containing slim filaments are located at the edges of the 20 km s$^{-1}$ cloud and the 50 km s$^{-1}$ cloud, where they are exposed to and can more easily interact with the external environment. Additionally, [6](#fig:maser) presents the magnetic orientations with a resolution of 19.6$^{\prime\prime}$ obtained from (cite: 2024ApJ...969..150P). We find that magnetic fields are nearly perpendicular to the main filament skeletons. Studies modeling the influence of a shock wave on a molecular cloud suggest that shock compression can lead to the formation of filaments oriented perpendicular to the magnetic field (cite: 2018PASJ...70S..53I; 2021ApJ...916...83A). Given the likely presence of shocks, we speculate that these filaments result from the interaction of shock waves with magnetized molecular clouds. Future multi-wavelength investigations that better constrain excitation conditions and chemistry will help confirm the nature of these filaments.

# Conclusions

We have identified slim filaments in four regions toward the CMZ through ALMA 1.3 mm molecular lines. These filaments are distinctive for their narrow ($\lesssim$0.03 pc) morphology, with strong SiO 5–4 line emissions as well as non-detections of thermal dust emission at the 5$\sigma$ level. They show consistent velocity structures which are different from outflows. The analysis of various pressures in slim filaments suggests that turbulent pressure dominates, leading to hydrostatic inequilibrium and therefore potential expansion and dissipation. The relative molecular abundances are statistically similar with those in protostellar outflows and the detection of collisionally pumped Class I CH$_3$OH masers hints an association with shocks.

We speculate that these slim filaments represent a distinct class from the dense gas filaments typically observed in nearby molecular clouds, and they may result from interactions between shocks and molecular clouds. Their eventual dissipation within $\sim$10$^4$ years may enrich SiO and several COMs (e.g., CH$_3$OH, CH$_3$CN, H$_2$CO, HC$_3$N) in the ISM, thus leading to the observed widespread emission of SiO and COMs in the CMZ.

# Acknowledgements

We thank Di Li, Dalei Li, and Natalie Butterfield for helpful discussions. This work is supported by the National Key R&D Program of China (No. 2022YFA1603100) and the Strategic Priority Research Program of the Chinese Academy of Sciences (CAS) Grant No. XDB0800300. K.Y. acknowledges support from the Shanghai Post-doctoral Excellence Program (No. 2024379). X.L. acknowledges support from the National Natural Science Foundation of China (NSFC) through grant Nos. 12273090 and 12322305, the Natural Science Foundation of Shanghai (No. 23ZR1482100), and the CAS “Light of West China” Program No. xbzg-zdsys-202212. Y.Z. acknowledges the support from the Yangyang Development Fund. H.B.L. is supported by the National Science and Technology Council (NSTC) of Taiwan (Grant Nos. 111-2112-M-110-022-MY3, 113-2112-M-110-022-MY3). Q.Z. acknowledges the support of National Science Foundation under award No. 2206512. E.A.C. Mills gratefully acknowledges funding from the National Science Foundation under Award Nos. 1813765, 2115428, 2206509, and CAREER 2339670. JMDK gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. S.F. acknowledges support by the National Science Foundation of China (12373023, 12133008). AG acknowledges support from the NSF under grants AAG 2008101, 2206511, and CAREER 2142300. H.-H.Q. is partially supported by the Youth Innovation Promotion Association CAS and the NSFC (grant No. 11903038) and the Strategic Priority Research Program of the Chinese Academy of Sciences (grant No. XDB1070301 and XDB1070302). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00243.S, ADS/JAO.ALMA#2016.1.00875.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis was in part carried out on the open-use data analysis computer system at the Astronomy Data Center (ADC) of NAOJ. This research has made use of NASA’s Astrophysics Data System. This research has made use of CASA (cite: 2022PASP..134k4501C), APLpy (cite: aplpy2012), Astropy (cite: astropy2013), and pvextractor(<http://pvextractor.readthedocs.io>).

87 natexlab

(ref: 2021ApJ...916...83A) Abe, D., Inoue, T., Inutsuka, S.-i., & Matsumoto, T. 2021, ApJ, 916, 83

(ref: 2022A&A...667L...1A) André, P. J., Palmeirim, P., & Arzoumanian, D. 2022, A&A, 667, L1

(ref: ao2013) Ao, Y., Henkel, C., Menten, K. M., et al. 2013, A&A, 550, A135

(ref: 2001ApJ...554..132A) Arce, H. G. & Goodman, A. A. 2001, ApJ, 554, 132

(ref: 2007prpl.conf..245A) Arce, H. G., Shepherd, D., Gueth, F., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 245

(ref: 2011A&A...529L...6A) Arzoumanian, D., André, P., Didelon, P., et al. 2011, A&A, 529, L6

(ref: 2019A&A...621A..42A) Arzoumanian, D., André, P., Könyves, V., et al. 2019, A&A, 621, A42

(ref: astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: bally2014) Bally, J., Rathborne, J. M., Longmore, S. N., et al. 2014, ApJ, 795, 28

(ref: barnes2017) Barnes, A. T., Longmore, S. N., Battersby, C., et al. 2017, MNRAS, 469, 2263

(ref: 1998ApJ...499..777B) Bergin, E. A., Melnick, G. J., & Neufeld, D. A. 1998, ApJ, 499, 777

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: 2022A&A...667A...6C) Chahine, L., López-Sepulcre, A., Podio, L., et al. 2022, A&A, 667, A6

(ref: 1999A&A...343..585C) Codella, C., Bachiller, R., & Reipurth, B. 1999, A&A, 343, 585

(ref: 2019ApJ...881L..42C) Cosentino, G., Jiménez-Serra, I., Caselli, P., et al. 2019, ApJL, 881, L42

(ref: cosentino2018) Cosentino, G., Jiménez-Serra, I., Henshaw, J. D., et al. 2018, MNRAS, 474, 3760

(ref: cotton2016) Cotton, W. D. & Yusef-Zadeh, F. 2016, ApJS, 227, 10

(ref: 2024arXiv241009253C) Crowe, S., Fedriani, R., Tan, J. C., et al. 2024, arXiv e-prints, arXiv:2410.09253

(ref: 2016A&A...586A.149C) Csengeri, T., Leurini, S., Wyrowski, F., et al. 2016, A&A, 586, A149

(ref: desimone2022) De Simone, M., Codella, C., Ceccarelli, C., et al. 2022, MNRAS, 512, 5214

(ref: 2014A&A...570A...1D) Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2014, A&A, 570, A1

(ref: 2016JMoSp.327...95E) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: ferriere2007) Ferrière, K., Gillard, W., & Jean, P. 2007, A&A, 467, 611

(ref: ginsburg2016) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50

(ref: goldsmith1999) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: 2018A&A...610A..77H) Hacar, A., Tafalla, M., Forbrich, J., et al. 2018, A&A, 610, A77

(ref: 2023ASPC..534...83H) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 83

(ref: 2022MNRAS.509.4758H) Henshaw, J. D., Krumholz, M. R., Butterfield, N. O., et al. 2022, MNRAS, 509, 4758

(ref: henshaw2016a) Henshaw, J. D., Longmore, S. N., Kruijssen, J. M. D., et al. 2016, MNRAS, 457, 2675

(ref: heywood2022) Heywood, I., Rammala, I., Camilo, F., et al. 2022, ApJ, 925, 165

(ref: 1983QJRAS..24..267H) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: immer2016) Immer, K., Kauffmann, J., Pillai, T., Ginsburg, A., & Menten, K. M. 2016, A&A, 595, A94

(ref: 2018PASJ...70S..53I) Inoue, T., Hennebelle, P., Fukui, Y., et al. 2018, PASJ, 70, S53

(ref: inutsuka2021) Inutsuka, S. 2021, in Astronomical Society of the Pacific Conference Series, Vol. 528, New Horizons in Galactic Center Astronomy and Beyond, ed. M. Tsuboi & T. Oka, 271

(ref: jimenezserra2014) Jiménez-Serra, I., Caselli, P., Fontani, F., et al. 2014, MNRAS, 439, 1996

(ref: jimenezserra2010) Jiménez-Serra, I., Caselli, P., Tan, J. C., et al. 2010, MNRAS, 406, 187

(ref: 2016A&A...586A..27K) Kainulainen, J., Hacar, A., Alves, J., et al. 2016, A&A, 586, A27

(ref: 2008A&A...487..993K) Kauffmann, J., Bertoldi, F., Bourke, T. L., Evans, N. J., I., & Lee, C. W. 2008, A&A, 487, 993

(ref: kauffmann2017a) Kauffmann, J., Pillai, T., Zhang, Q., et al. 2017, A&A, 603, A89

(ref: 2015MNRAS.452.3435K) Koch, E. W. & Rosolowsky, E. W. 2015, MNRAS, 452, 3435

(ref: krieger2017) Krieger, N., Ott, J., Beuther, H., et al. 2017, ApJ, 850, 77

(ref: kruijssen2019a) Kruijssen, J. M. D., Dale, J. E., Longmore, S. N., et al. 2019, MNRAS, 484, 5734

(ref: kruijssen2014) Kruijssen, J. M. D., Longmore, S. N., Elmegreen, B. G., et al. 2014, MNRAS, 440, 3370

(ref: 1996ApJ...459..638L) Lada, C. J. & Fich, M. 1996, ApJ, 459, 638

(ref: li2020) Li, C., Wang, H.-C., Wu, Y.-W., Ma, Y.-H., & Lin, L.-H. 2020, Research in Astronomy and Astrophysics, 20, 031

(ref: baobab2013) Liu, H. B., Ho, P. T. P., Wright, M. C. H., et al. 2013, ApJ, 770, 44

(ref: longmore2013a) Longmore, S. N., Bally, J., Testi, L., et al. 2013, MNRAS, 429, 987

(ref: 2011A&A...526L...2L) López-Sepulcre, A., Walmsley, C. M., Cesaroni, R., et al. 2011, A&A, 526, L2

(ref: 2016A&A...595A.122L) Louvet, F., Motte, F., Gusdorf, A., et al. 2016, A&A, 595, A122

(ref: lu2020) Lu, X., Cheng, Y., Ginsburg, A., et al. 2020, ApJL, 894, L14

(ref: lu2021) Lu, X., Li, S., Ginsburg, A., et al. 2021, ApJ, 909, 177

(ref: 2024ApJ...962...39L) Lu, X., Liu, J., Pillai, T., et al. 2024, ApJ, 962, 39

(ref: lu2019b) Lu, X., Mills, E. A. C., Ginsburg, A., et al. 2019a, ApJS, 244, 35

(ref: lu2019a) Lu, X., Zhang, Q., Kauffmann, J., et al. 2019b, ApJ, 872, 171

(ref: lu2017) Lu, X., Zhang, Q., Kauffmann, J., et al. 2017, ApJ, 839, 1

(ref: lu2018) Lu, X., Zhang, Q., Liu, H. B., et al. 2018, ApJ, 855, 9

(ref: mangum2015) Mangum, J. G. & Shirley, Y. L. 2015, PASP, 127, 266

(ref: martinpintado1997) Martı́n-Pintado, J., de Vicente, P., Fuente, A., & Planesas, P. 1997, ApJL, 482, L45

(ref: martinpintado2001) Martı́n-Pintado, J., Rizzo, J. R., de Vicente, P., Rodrı́guez-Fernández, N. J., & Fuente, A. 2001, ApJL, 548, L65

(ref: menten2009) Menten, K. M., Wilson, R. W., Leurini, S., & Schilke, P. 2009, ApJ, 692, 47

(ref: mills2013) Mills, E. A. C. & Morris, M. R. 2013, ApJ, 772, 105

(ref: 2016ApJ...824...99M) Minh, Y. C., Liu, H. B., & Galvań-Madrid, R. 2016, ApJ, 824, 99

(ref: minh2015) Minh, Y. C., Liu, H. B., Su, Y.-N., et al. 2015, ApJ, 808, 86

(ref: morris1996) Morris, M. & Serabyn, E. 1996, ARA&A, 34, 645

(ref: 2007A&A...476.1243M) Motte, F., Bontemps, S., Schilke, P., et al. 2007, A&A, 476, 1243

(ref: 2005JMoSt.742..215M) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: 2001A&A...370L..49M) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: nguyenluong2013) Nguyen-Lu’o’ng, Q., Motte, F., Carlhoff, P., et al. 2013, ApJ, 775, 88

(ref: 2024A&A...691A..70N) Nonhebel, M., Barnes, A. T., Immer, K., et al. 2024, A&A, 691, A70

(ref: 2017MNRAS.467.2723P) Palau, A., Walsh, C., Sánchez-Monge, Á., et al. 2017, MNRAS, 467, 2723

(ref: 2024ApJ...969..150P) Paré, D., Butterfield, N. O., Chuss, D. T., et al. 2024, ApJ, 969, 150

(ref: 1998JQSRT..60..883P) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: 2011ApJ...739L..21P) Pihlström, Y. M., Sjouwerman, L. O., & Fish, V. L. 2011, ApJL, 739, L21

(ref: 2007ApJ...654..361Q) Qiu, K., Zhang, Q., Beuther, H., & Yang, J. 2007, ApJ, 654, 361

(ref: reid2019) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131

(ref: requenatorres2008) Requena-Torres, M. A., Martı́n-Pintado, J., Martı́n, S., & Morris, M. R. 2008, ApJ, 672, 352

(ref: requenatorres2006) Requena-Torres, M. A., Martı́n-Pintado, J., Rodrı́guez-Franco, A., et al. 2006, A&A, 455, 971

(ref: aplpy2012) Robitaille, T. & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python

(ref: schilke1997) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A, 321, 293

(ref: lamda2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: shirley2015) Shirley, Y. L. 2015, PASP, 127, 299

(ref: 2024ApJ...960...48T) Towner, A. P. M., Ginsburg, A., Dell’Ova, P., et al. 2024, ApJ, 960, 48

(ref: 2014MNRAS.439.2584V) Voronkov, M. A., Caswell, J. L., Ellingsen, S. P., Green, J. A., & Breen, S. L. 2014, MNRAS, 439, 2584

(ref: wallace2022) Wallace, J., Battersby, C., Mills, E. A. C., et al. 2022, ApJ, 939, 58

(ref: wang2014) Wang, K., Zhang, Q., Testi, L., et al. 2014, MNRAS, 439, 3275

(ref: 2024A&A...684A.140Y) Yang, K., Qiu, K., & Pan, X. 2024, A&A, 684, A140

(ref: yusefzadeh2013) Yusef-Zadeh, F., Cotton, W., Viti, S., Wardle, M., & Royster, M. 2013, ApJL, 764, L19

# Integrated maps of different molecular lines

The integrated maps of SO 6$_{5}$–5$_{4}$, H$_2$CO 3$_{0,3}$–2$_{0,2}$, HNCO 10$_{0,10}$–9$_{0,9}$, HC$_3$N 24–23, CH$_3$OH 4$_{2,2}$–3$_{1,2}$, H$_2$$^{13}$CO 3$_{1,2}$–2$_{1,1}$, c-C$_3$H$_2$ 6$_{1,6}$–5$_{0,5}$, and CH$_3$CN 12$_{0/1}$–11$_{0/1}$ for the slim filaments in the 20 km s$^{-1}$ cloud are presented in Figures [7](#fig:m0_a_app)–[9](#fig:m0_c_app).

![](fig6_filaA_app.pdf)

![](fig6_filaB_app.pdf)

![](fig6_filaC_app.pdf)

# Skeletons identified by FilFinder

The `FilFinder` package reduces the selecting area to identify skeletons that represent the topology of the areas, by using a Medial Axis Transform method. To achieve optimal filament detection, we set the following parameters: (i) global threshold - integrated intensities below 3$\sigma_{\rm area}$ are excluded from the mask; (ii) size threshold - filaments must have a minimum area of 125 pixel$^{2}$ ($\sim$ 5 times the beam size). The resulting skeletons are depicted as red lines in [10](#fig:skele).

![image](fig7_skele_d.pdf) ![image](fig7_skele_a.pdf)\
![image](fig7_skele_b.pdf) ![image](fig7_skele_c.pdf)

# Gaussian fits to the SiO 5–4 spectra in four regions

We perform Gaussian fits to the averaged SiO 5–4 spectra toward the four regions with results shown in [11](#fig:gauss).

![image](fig8_d_gauss.pdf) ![image](fig8_a_gauss.pdf)\
![image](fig8_b_gauss.pdf) ![image](fig8_c_gauss.pdf)

# Calculation of Molecular Column Densities

Assuming local thermodynamic equilibrium (LTE) conditions, optically thin line emission, Rayleigh-Jeans approximation, and negligible background, the column densities of a molecule can be derived following (cite: mangum2015):

$$\begin{equation}
\label{Eq_N}
N_{\rm tot} = \frac{8 \pi k_{\rm B} \nu^{2}}{h c^{3} A_{ul}} \frac{Q(T_{\rm ex})}{g_{u}} {\rm exp} \left(\frac{E_{u}}{k_{\rm B} T_{\rm ex}}\right) \int T_{B}dv, \\
\end{equation}$$

where $k_{\rm B}$ is the Boltzmann constant, $\nu$ is the rest frequency of the transition, $h$ is the Planck constant, $c$ is the light speed, $A_{ul}$ is the spontaneous emission coefficient from the upper state $u$ to the lower state $l$, $Q(T_{\rm ex})$ is the partition function, $T_{\rm ex}$ is the excitation temperature, $g_{u}$ is the degeneracy of the upper state, $E_{u}$ is the energy of the upper level energy, and $\int T_{B}dv$ is the integrated intensity. The spectroscopic parameters are obtained from the CDMS database (cite: 2001A&A...370L..49M; 2005JMoSt.742..215M; 2016JMoSp.327...95E), JPL catalogues (cite: 1998JQSRT..60..883P), and the LAMDA database (cite: lamda2005). The excitation temperature is adopted to be 70 K following . The derived column densities are presented in [\[tab_column\]](#tab_column).

The SiO mass, $M_{\rm SiO}$, can estimated based on the SiO column density (cite: goldsmith1999):

$$\begin{equation}
\label{Eq_mass}
M_{\rm SiO} = N_{\rm tot} \mu_{\rm SiO}m_{p}\Omega d^{2}, \\
\end{equation}$$

where $\mu_{\rm SiO}$ is the mean atomic weight of 44 for SiO, $\Omega$ is the solid angle, and $d$ is the distance of 8.1 kpc.

+----------------+--------+---+--------------------------------+---+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Cloud          | Region |   | Coordinates                    |   | Column densities                                                                                                                                                                                                      |
+:==============:+:======:+:=:+:============:+:===============:+:=:+:=====================:+:=====================:+:=====================:+:=====================:+:=====================:+:=====================:+:=====================:+:=====================:+:=====================:+
| 4-5            |        |   | R.A.         | Decl.           |   | SiO                   | SO                    | CH$_3$OH              | H$_2$CO               | HC$_3$N               | HNCO                  | H$_2$$^{13}$CO        | c-C$_3$H$_2$          | CH$_3$CN              |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | (hh:mm:ss)   | (dd:mm:ss)      |   | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           | (cm$^{-2}$)           |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
| 50 km s$^{-1}$ |        |   | 17:45:52.087 | $-$28:58:55.150 |   | 1.54$\times$10$^{14}$ | 4.57$\times$10$^{14}$ | 1.83$\times$10$^{16}$ | 2.86$\times$10$^{14}$ | 1.86$\times$10$^{14}$ | 2.82$\times$10$^{14}$ | —                     | 4.91$\times$10$^{13}$ | 1.09$\times$10$^{14}$ |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:52.340 | $-$28:58:58.224 |   | 9.50$\times$10$^{13}$ | 1.70$\times$10$^{14}$ | 9.54$\times$10$^{15}$ | 3.60$\times$10$^{14}$ | 6.25$\times$10$^{13}$ | 2.05$\times$10$^{14}$ | —                     | —                     | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
| 20 km s$^{-1}$ | A      |   | 17:45:37.906 | $-$29:03:35.371 |   | 1.37$\times$10$^{14}$ | 6.28$\times$10$^{14}$ | 9.49$\times$10$^{15}$ | 1.27$\times$10$^{15}$ | 1.65$\times$10$^{14}$ | 4.63$\times$10$^{14}$ | 1.27$\times$10$^{14}$ | 9.02$\times$10$^{13}$ | 3.72$\times$10$^{13}$ |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:38.540 | $-$29:03:32.649 |   | 6.47$\times$10$^{13}$ | 1.51$\times$10$^{14}$ | 8.67$\times$10$^{15}$ | 1.04$\times$10$^{14}$ | 8.03$\times$10$^{13}$ | 4.05$\times$10$^{14}$ | 4.77$\times$10$^{13}$ | —                     | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:37.664 | $-$29:03:38.772 |   | 1.09$\times$10$^{14}$ | 3.17$\times$10$^{14}$ | 1.26$\times$10$^{16}$ | 9.20$\times$10$^{14}$ | 1.31$\times$10$^{14}$ | 8.91$\times$10$^{14}$ | 1.27$\times$10$^{14}$ | 5.49$\times$10$^{13}$ | 7.49$\times$10$^{13}$ |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:38.030 | $-$29:03:38.573 |   | 5.48$\times$10$^{13}$ | 1.00$\times$10$^{14}$ | 5.36$\times$10$^{15}$ | 3.78$\times$10$^{14}$ | 6.29$\times$10$^{13}$ | 4.70$\times$10$^{14}$ | —                     | 2.17$\times$10$^{13}$ | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:36.996 | $-$29:03:47.614 |   | 7.16$\times$10$^{13}$ | 2.55$\times$10$^{14}$ | 9.41$\times$10$^{15}$ | 3.62$\times$10$^{14}$ | 2.89$\times$10$^{13}$ | 4.25$\times$10$^{14}$ | 2.56$\times$10$^{13}$ | —                     | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:36.831 | $-$29:03:53.011 |   | 5.69$\times$10$^{13}$ | 7.79$\times$10$^{13}$ | 1.73$\times$10$^{15}$ | 3.05$\times$10$^{14}$ | 1.26$\times$10$^{13}$ | 8.84$\times$10$^{13}$ | 2.74$\times$10$^{13}$ | —                     | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
| 2-15           | B      |   | 17:45:39.293 | $-$29:04:22.061 |   | 6.17$\times$10$^{13}$ | 2.09$\times$10$^{14}$ | 7.15$\times$10$^{15}$ | 4.53$\times$10$^{14}$ | 9.70$\times$10$^{13}$ | 5.16$\times$10$^{14}$ | 1.04$\times$10$^{14}$ | 8.37$\times$10$^{13}$ | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
|                |        |   | 17:45:39.576 | $-$29:04:12.630 |   | 3.02$\times$10$^{13}$ | 7.79$\times$10$^{13}$ | 2.87$\times$10$^{15}$ | 8.74$\times$10$^{13}$ | 1.22$\times$10$^{13}$ | 1.73$\times$10$^{14}$ | —                     | —                     | —                     |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+
| 2-15           | C      |   | 17:45:34.835 | $-$29:04:40.047 |   | 4.27$\times$10$^{13}$ | 2.56$\times$10$^{14}$ | 1.00$\times$10$^{16}$ | 2.98$\times$10$^{14}$ | 9.25$\times$10$^{13}$ | 7.17$\times$10$^{14}$ | 2.87$\times$10$^{13}$ | 1.22$\times$10$^{14}$ | 3.38$\times$10$^{13}$ |
+----------------+--------+---+--------------+-----------------+---+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+-----------------------+

[^1]: <https://github.com/e-koch/FilFinder>

</paper>

Write the methods card for this paper.