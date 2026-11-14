# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...990..150A\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...990..150A",
 "title": "PEACHES. IV. Tracing the Formation and Evolution of C<SUB>2</SUB>H in Perseus Low-mass Protostars",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Anderson, Jack G.",
 "n_authors": 5,
 "arxiv_id": "2508.03918",
 "doi": "10.3847/1538-4357/adf199",
 "alma_projects_linked_by_archive": [
  "2016.1.01501.S",
  "2017.1.01462.S",
  "2022.1.00303.S"
 ]
}
```

Paper text:
<paper>
# PEACHES IV: Tracing the Formation & Evolution of C$_2$H in Perseus Low-Mass Protostars

## Abstract

The radical hydrocarbon molecule C$_2$H is widely detected in various stages of star and planet formation, and has emerged as a useful tracer of high-C/O gas within the photochemically active surface layers of mature (Class II) protoplanetary disks. However, the chemistry and evolution of C$_2$H within younger (Class 0/I) protostars remains much more poorly understood. Here, using data observed as part of the PEACHES survey along with new ALMA ACA observations, we investigate the C$_2$H emission towards an unbiased sample of 35 Class 0/I low-mass protostars in Perseus. With this large sample, we identify a clear association between C$_2$H emission and the protostellar outflow cavity walls, and a consistent spatial anti-correlation between C$_2$H and SO emission. Together, these trends confirm that C$_2$H is tracing photochemically active, O-poor gas in these younger sources. We fitted the C$_2$H spectra with a simple LTE model to yield column density maps, and find values ranging from 10$^{14}$ – 10$^{15}$ cm$^{-2}$ in these sources. We also looked for trends in the C$_2$H emission morphology as a function of various protostellar evolutionary metrics, but find no clear patterns: the C$_2$H emission remains spatially extended in most sources, independent of age. This indicates that the transition to the compact C$_2$H emission observed on the surface of Class II disks must happen rapidly, sometime just after the embedded stage.

# Introduction

The process of star formation is kicked off by the gravitational collapse of the densest regions of interstellar molecular clouds. Before they evolve into fully formed star systems, these objects begin the maturation process as protostars. Still embedded in their host molecular cloud, they can be characterized as pre-main sequence stars surrounded by a dense, infalling natal envelope of gas and dust ((cite: lada1987)). In the innermost regions of these objects, material from the envelope accretes onto the newly formed star, setting its final mass and luminosity. On larger scales, this envelope begins to be dissipated by large-scale high-velocity outflows of gas and dust ((cite: arce_sargent2006)). As these sources evolve, their outer envelope is cleared away, yielding only a host star and mature protoplanetary disk. Between the envelope, inner envelope/proto-disk, and outflows, the protostellar environment is host to a wide range of physical conditions, which can be traced observationally using chemical probes (cite: tychoniec2021).\

There is recent evidence that at this point in the formation of the star system, the earliest steps towards planet formation are already taking place ((cite: harsono2018), (cite: manara2018), (cite: tobin2020)). This makes protostars the best sites for understanding the physical processes and chemistry governing the initial formation steps of new planetary systems. Because of this connection between the formation of planets and their host stars, understanding the chemical and physical evolution of protostellar environments plays a critical role in our understanding of how planetary compositions are set inside of and beyond our solar system.\

Observations of mature Class II disks show a distinctive chemical environment compared to earlier evolutionary stages, characterized by the depletion of key volatiles in the gas and active UV-driven photochemistry ((cite: calahan2023)). The presence of highly-reactive hydrocarbon radicals, namely C$_2$H, serves as an indicator to this unique chemical environment. Notably, strong C$_2$H emission has been widely observed towards many well studied disks ((cite: miotello2019), (cite: bergner2019)), indicating a long-lived hydrocarbon chemical equilibrium ((cite: calahan2023)). Two main factors seem to play a role in driving C$_2$H formation. Firstly, chemical models and high-resolution ALMA observations show that C$_2$H can only form efficiently in oxygen-poor, i.e. high C/O, gas ((cite: sakai2010), (cite: bergin2016), (cite: krijt2018), (cite: miotello2019), (cite: krijt2020), (cite: bosman2021), (cite: vanclepper2022)). This is because free gas-phase O will readily lock up gas-phase carbon into the more stable CO. Second, abundant ultraviolet (UV) radiation is required for sustained C$_2$H production ((cite: bergin2016), (cite: heays2017), (cite: bosman2021), (cite: calahan2023)). This is underscored by the early detections of C$_2$H in interstellar photodissociation regions (PDRs), which are exposed to high UV fields ((cite: jansen1995), (cite: nagy2015)). The physical and chemical environments necessary for long-lived C$_2$H production in the surface layers of mature disks have been well studied, but comprehensive studies of the factors driving C$_2$H formation in younger, embedded sources are still needed.\

C$_2$H has been detected and mapped in a number of protostellar sources including L1527 ((cite: sakai2014_a), (cite: sakai2014_b)), L483 ((cite: oya2018)), IRAS 15398-3359 ((cite: oya2014), (cite: okoda2018)), NGC 1333 IRAS 4C ((cite: zhang2018)), and CB68 ((cite: imai2022)). In general, the C$_2$H morphology in these embedded sources is extended. Except for L1527 ((cite: sakai2017)), it appears to trace the low-density cavity regions where the high velocity outflows meet the quiescent envelope in most of the sources ((cite: tychoniec2021)). This is in contrast to the compact C$_2$H morphology seen on the surface of mature disks. Therefore, at some point there must be a transition from the large-scale outflow morphology seen in young protostars, to the compact disk-associated morphology seen in more mature systems. As of yet, there has not been a systematic survey of protostellar C$_2$H chemistry which could reveal this transition stage or place constraints on the timescale over which it occurs.\

With the aim of obtaining an unbiased view of C$_2$H chemistry in a large sample of protostars of varied ages, we make use of data available as part of the Perseus ALMA Chemical Survey (PEACHES, (cite: PEACHES_I)) and the MASS Assembly of Stellar Systems and their Evolution with the SMA (MASSES, (cite: MASSES)) which cover 35 Class 0/I protostars in Perseus. We focus on the C$_2$H, SO, and CO emission in order to trace the chemistry, morphology and evolution of C$_2$H in this sample. Our main goals are to (1) disambiguate what C$_2$H is tracing within the protostellar environment, and whether its formation is driven by then same factors (high C/O, high UV) in embedded sources as is seen in class II disks; and (2) search for evolutionary trends in the C$_2$H emission morphology, from an extended, outflow cavity structure to a more compact disk-like morphology.

# Methods

## Observations

We used ALMA observations of C$_2$H and SO transitions taken with the 12m array as part of the PEACHES project (Project codes 2016.1.01501.S and 2017.1.01462.S, (cite: PEACHES_I)). All data reprocessing and imaging was performed using CASA ((cite: CASA)). The measurement sets were obtained using the ALMA pipeline. Line-free channels were averaged to form continuum measurement sets, on which self-calibration was performed for sources with bright continuum emission to improve signal-to-noise ratio. We performed two to three rounds of manual self-calibration, until minimal gains in SNR were observed. The self-calibration process yielded an average improvement in continuum SNR of 31%, while the major and minor beam axes were changed by an average of 0.2% and 1%, respectively. Line and continuum images were created using the CASA task `tclean`. We produced images for our spatial analysis using Briggs weighting and a robust parameter of 1. Images of 600 by 600 pixels were created, with a pixel size of 0.05". Line images were cleaned to a threshold of twice the rms estimated using line free-channels, using automasking low noise, sidelobe and noise thresholds of 1.5, 3.0 and 3.75, respectively. Moment 0 maps of the lines were then created from the line data cubes by integrating over the velocities of interest. The $N$ = 7–6, $J$ = 6–5 transition of ground state SO and and the $N$ = 3–2, $J$ = $\frac{5}{2}$–$\frac{3}{2}$, $F$ = 3–2 C$_2$H transition were imaged. These transitions were selected for each molecule of interest because of their high signal-to-noise ratio and the overall number of sources in which detections of the transitions were made. See (cite: PEACHES_I) for a list of all detected molecular transitions. Additional images of S-bearing molecules towards the PEACHES sources can be found in (cite: PEACHES_III).\

To obtain better flux measurements for column density calculations (Section [3.2](#sub:3)), we also used complementary observations taken with the ALMA Atacama Compact Array (ACA; project code 2022.1.00303.S) and combined with the 12m data. The ACA observations, taken in August and September of 2023, target the same PEACHES sources and molecular lines as the original 12m survey. Here only the C$_2$H spectral window is used, covering the F = 3–2, 2–1 and 2–2 hyperfine components of the N = 3–2, J = $\frac{5}{2}$–$\frac{3}{2}$ C$_2$H transition at $\sim$262.06 GHz, with a channel width of 61.035 kHz ($\sim$0.07 km/s). As before, data reprocessing and imaging was performed using CASA, and line images were created using `tclean`. The 12m and ACA data were imaged together using the ‘mosaic’ gridding parameter, Briggs weighting and a robust value of 2. During imaging, the ACA visibilities were downweighted by a factor of 0.41 to correct for the time-on-source (ToS) ratio between the 12m and ACA observations: from 1:5.8 (actual 89:512 minutes) to an effective ratio of 1:2.4 as recommended by (cite: alma_handbook). Line images were cleaned to a threshold of twice the rms estimated using line free-channels, using automasking low noise, sidelobe and noise thresholds of 1.5, 2.0 and 4.25, respectively. Moment 0 maps of the lines were then created from the line data cubes by integrating over the velocities of interest.\

The CO images used in our C$_2$H spatial analyses come from SMA observations as part of the MASS Assembly of Stellar Systems and their Evolution with the SMA (MASSES) survey ((cite: MASSES)). The MASSES survey made use of the subcompact, compact and extended configurations of the SMA, covering baseline distances of 9.5-77m, 16-77m and 44-226m, respectively. The 15-1231m baselines of the PEACHES ALMA 12m array data (configuration details provided in (cite: PEACHES_I)), with the addition of the 9-50m baselines provided by the ACA observations, cover similar short-baseline distances. We can therefore directly compare the large-scale emission structures from both the ALMA and SMA observations, and in addition we are able to recover more small-scale detail in the ALMA observations. CO data products were taken directly from the MASSES data release web page through the Harvard data archive ((cite: MASSESData)).\

## C$_2$H Spectral Line Fitting

Maps of C$_2$H column densities and rotational temperatures were produced by fitting synthetic spectra to the ACA + 12m images at positions where the F= 3–2 C$_2$H emission in the moment-0 maps is above a 3$\sigma$ threshold. The image cubes were first regridded by a factor of 4, i.e. squares of 2-by-2 pixels were averaged, to increase the signal to noise and sample on spatial scales comparable to the beam. In the spectral line model, we assume that the line profiles of each hyperfine component are Gaussian, that each hyperfine component can be described with the same rotational temperature, $T_r$, and that the emission is in local thermodynamic equilibrium (LTE). The optical depth at the center of the each hyperfine line $i$ is found via: $$\begin{equation}
    \tau_{i,0} = \frac{N_T}{Q(T_r)}e^{\frac{E_{u,i}}{T_r}}\frac{g_{u,i}A_{u,i}c^3}{8\pi\nu_i^3}\frac{1}{\sigma\sqrt{2\pi}}(e^{\frac{h\nu_i}{kT_r}}-1)
\label{eq:tau_i}
\end{equation}$$ where $N_T$ the total column density, $Q(T)$ the molecular partition function, and $\sigma$ is the Gaussian line width. For each hyperfine line, $E_{u,i}$ is the upper state energy, $g_{u,i}$ is the upper-state degeneracy, $A_{u,i}$ is the Einstein coefficient and $\nu_i$ is the transition frequency. The total optical depth profile can then be described as: $$\begin{equation}
    \tau_\nu=\sum_{i} \tau_{i,0}\;\mathrm{exp}\left( \frac{-(V-V_i-V_{lsr})^2}{2\sigma^2}\right)
\label{eq:tau_nu}
\end{equation}$$ where $V$ is the velocity, $V_i$ is the velocity offset of each hyperfine line, and $V_{lsr}$ is the source velocity. Finally, the intensity can be calculated using: $$\begin{equation}
I_{\nu} = [B_\nu(T_r) - B_\nu(T_{bg})]\times(1-e^{-\tau_\nu})\times\Omega
\label{I_nu} 
\end{equation}$$ where $B_\nu$ is the Planck function, $\Omega$ is the effective angular area of the restoring beam, and $T_{bg}$ the cosmic microwave background (2.73 K).

# Results

## C$_2$H and SO Emission Morphology

Previous observations of C$_2$H in protostars have hinted at a connection between the C$_2$H emission and the outflow ((cite: oya2014), (cite: oya2018), (cite: tychoniec2021)), as well as a possible anti-correlation with SO ((cite: sakai2014_a), (cite: sakai2014_b), (cite: okoda2018), (cite: arturdelavillarmois2019)). Using the unbiased survey of C$_2$H provided by the PEACHES dataset, we aim to explore these connections by comparing the C$_2$H morphology to the outflow tracer CO, as well as SO. In studying these correlations, we are interested in the small-scale emission patterns, and therefore use the 12m-only images for our analysis. Figure [1](#fig:fig1) presents an overview of the PEACHES sources and detected molecules of interest. The two sources where continuum emission is not detected, SVS 3 and L1448 IRS2E, are omitted. Integrated intensity (moment-0) maps were constructed for all the sources where C$_2$H emission was detected, shown contoured in red. Also included in Figure [1](#fig:fig1) are integrated maps of SO, contoured in orange. Integrated intensity maps of CO are shown as a greyscale colormap, which includes both red- and blueshifted emission.

![](Figure1_alt.pdf)

Of the 35 protostars observed, C$_2$H and SO were detected towards 30 and 30, respectively. The sources shown in Figure [1](#fig:fig1) display a wide range of C$_2$H emission morphologies. Some appear relatively extended (scales of $\sim$3-4") but without discernible structure, (see L1448 NW, Per-emb 18, Per-emb 33, Per-emb 36, Per-emb 44, Per-emb 54). However, many sources exhibit coherent C$_2$H emission morphologies that suggest a relationship to the outflow structures traced by CO. Several of these exhibit quite narrow C$_2$H emission (Per-emb 11, 13, SVS 13B), while most others exhibit a X-wing or cone-like emission morphology (Per-emb 1, 2, 5, 10, 14, 17, 20, 22, 25, 26, 27, 29, 35, 53; and to a lesser extent 8 and 12). Interestingly, many of the sources with this cone-like structure are also those where the CO (2-1) moment-0 maps (in greyscale) trace discernible bipolar outflows moving away from the continuum peak. In these cases, we see a clear association between the C$_2$H emission and the base or edges of the outflow traced by CO.\

The SO moment-zero maps (contoured in orange) show a similar range of behavior to that of C$_2$H, with some directionally extended emission and some more compact emission. However, comparison of SO and C$_2$H by visual inspection of the moment-zero contours is not sufficient to understand the degree of spatial overlap between the two molecules, especially given that many sources show large azimuthal asymmetries in their emission patterns. To more definitively compare the C$_2$H and SO emission morphology in the outflowing regions of the protostars, we produce a series of spatial intensity profiles, as shown for an example source in Figure [2](#fig:fig2). The emission of both molecules of interest is sampled along spatial rays (shown in green) which approximately cover the outflow regions around each protostar. The rays are spaced in 10 degree increments originating at the source continuum peak. The emission from each individual ray is then averaged to give a spatial intensity profile, as shown on the right of Figure [2](#fig:fig2).

![](Figure2.pdf)

As shown in Figure [2](#fig:fig2) for the case of Per-emb 5, this procedure clearly illustrates the difference in spatial morphology between the two molecules. The C$_2$H is more spatially extended, with emission extending up to 2$\ensuremath{''}$ away from the continuum peak. The SO, as can be visualized in both the moment-zero map and intensity profile, is compact around the location of the continuum maximum, only showing emission within $\sim$1$\ensuremath{''}$ around the continuum peak. What is not clear from the moment-zero contours, but does become evident from the average intensity profiles, is the drop in C$_2$H emission towards the continuum peak of Per-emb 5, as shown by the dip in the C$_2$H intensity profile around a distance of 0$\ensuremath{''}$. This coincides with the SO emission peak. Moving away from the continuum peak, the C$_2$H emission climbs sharply while the SO emission falls off. This type of behavior is very similar to the profile observed in IRAS 15398-3359 ((cite: okoda2018)). To analyze this further, this type of intensity profile analysis was carried out across all sources in the sample where a bipolar outflow could be discerned from the CO (2-1) emission.

![](Figure4.png)

Figure [3](#fig:fig3) shows the resulting intensity profiles in all sources for which this spatial analysis was possible. To enable comparisons across the sources, the average intensity profiles are now plotted with distance as the vertical axis and the relative emission intensity of each molecule shown with color saturation. The sources have been arranged such that similar SO and C$_2$H morphologies are grouped together. The leftmost sources, Per-emb 5, 29, 26, 25 and 14 all display compact SO around the continuum peak, whereas C$_2$H is absent from the continuum peak but emits at larger distances beyond the SO peak. Per-emb 10, 22, and 17 also show compact and centrally located SO, with C$_2$H emission dipping at the SO position but not disappearing entirely. In the center sources (Per-emb 27, 11, 53 and 1), the SO emission is either spatially extended or off-center from the continuum peak; even so the C$_2$H emission again anti-correlates with the SO emission locations. Per-emb 1 is particularly asymmetric, with strong SO emission within one outflow lobe and strong C$_2$H emission in the other lobe. This can also be visualized in the moment-zero maps of Per-emb 1 presented in Figure [1](#fig:fig1). The sources on the right, Per-emb 16 and 20, exhibit compact SO emission, but the C$_2$H emission does not drop around the the continuum peak and appears more co-spatial with SO. Overall, we find that most sources (12 of 14) show a clear anti-correlation between the location of C$_2$H and SO within the outflow.

## ACA Images and Column Density Maps

Beyond the characterizing the emission morphology, we also aim to obtain quantitative constraints on the C$_2$H column densities towards the sources. To do this, we create column density maps using the spectral line model outlined in section [2.2](#sec:line_fitting). To ensure complete recovery of the C$_2$H flux, we use the combined 12m+ACA images for this analysis. To illustrate our approach, the top panel of Figure [4](#fig:fig5) shows the average spectrum for Per-emb 1 (from all pixels with a $>$3$\sigma$ detection of the F=3-2 hyperfine component), with the fitted model overlaid in orange. Our C~2~H hyperfine transitions span an equal upper state energy, and as a result cannot precisely fit a variable rotational temperature. We proceed with fitting column densities assuming a fixed temperature of 20K, and bound our column density values between 10^13^ and 10^16^ cm^-2^, noting that true constraints on the C$_2$H rotational temperatures, and in turn more precise constraints on the column densities, would require coverage of additional C$_2$H lines. Our choice of rotational temperature is informed by prior studies of molecular outflows in low-mass protostars, from which rotational temperatures of 10–50K are typical ((cite: Parker1991), (cite: Hatchell2007), (cite: Curtis2010), (cite: Dunham2010), (cite: Dunham2014)). We adopted a value on the low end of this range under the assumption that the outflow cavities are cooler than the outflowing gas itself. In any case, varying T$_r$ in our spectral line modeling within the 10–50 K range yields changes in calculated C$_2$H column densities of $<$ 5%.\

The maps resulting from fitting all pixels individually are shown in the top panel on the right. Column density maps for all sources with sufficiently bright C$_2$H emission are shown in the bottom portion of Figure [4](#fig:fig5). For reference, we also show the CO 2-1 emission (grey colormap) and mm continuum (white contour). All column density colormaps in the lower panel have the same color scaling as the example of Per-emb 1. The fitted column density maps show values spanning $\sim 10^{14}$ – $10^{15}$ cm^-2^, with maps resembling that of the flux, as expected when fitting assuming a fixed rotational temperature. See Table [1](#tab:column densities) for the median and range of fitted column densities for all sources. The average-per-source uncertainties on our retrieved column densities range from 10^0.05^ - 10^0.5^ cm^-2^. Most sources show high C~2~H column densities close to the continuum max, decreasing moving away form the central star, while some (Per-emb 26, 44, and 54) show peaking C~2~H column densities more offset from the continuum max. However, definitive conclusions would require maps of fitted column densities with variable rotational temperatures, only possible with further spectral coverage.

![image](Figure5a_fixedtemp.png) ![image](Figure5b_fixedtemp.png)

## C$_2$H Morphology in Conjunction with Protostar Evolution

Using this large sample of protostellar sources with C$_2$H detections, we also attempt to identify possible evolutionary trends in the C$_2$H emission over the course of the protostellar lifetime. In order to do this, we compare the C$_2$H emission with three evolutionary metrics. As embedded protostars evolve, their central dust disk, best traced in the mm continuum, is expected to increase in size (cite: Maury2019). Additionally, their observed luminosities increase and their spectral energy distributions (SEDs) shift towards longer wavelengths ((cite: dunham2014review)). This shift in SED can be described using a blackbody with the same mean frequency, whose temperature increases as the SED shifts towards longer wavelengths. This temperature is defined as the bolometric temperature, and luminosity described as the bolometric luminosity ((cite: myers1993), (cite: Myers1998)). We therefore use the mm continuum deconvolved radius, the bolometric temperature and the bolometric luminosity as our evolutionary proxies. In particular, we are interested to see whether the C$_2$H emission trends from more extended morphologies associated with large-scale outflow cavities to more compact morphologies associated with a (proto-)disk over the duration of the embedded stage.\

For this comparison, we estimated the overall spatial extent of the C$_2$H emission from the width above 3$\sigma$ of the intensity profiles obtained in Section [3.1](#sub:1). These are plotted in Figure [5](#fig:fig4) against the three evolutionary metrics. The bolometric temperature and luminosity values and uncertainties are taken from (cite: tobin2016), while the deconvolved radii are determined via the CASA task `imfit`. The sources clearly vary in spatial extent of the C$_2$H emission, however there is no clear discernable trend with respect to our evolutionary metrics. The C$_2$H emission may be either extended or compact for both less mature and more mature systems.

![](Figure3_alt.pdf)

## Kinematic Comparison of C~2~H with CO

We also make use of the C~2~H fitting procedure outlined in Section [2.2](#sec:line_fitting) to extract basic kinematic information from the observations and compare that to the outflows as traced by CO. From our fitted spectra we calculate the shift in the C$_2$H F=3-2 hyperfine component with respect to the source velocity, and compare that to the intensity-weighted velocities (moment-1) of the CO observations. These maps are shown in Figure [6](#fig:C2H_CO). Most sources show some red- or blue-shifting of the C~2~H emission, though with a fairly small magnitude of $\sim$ 1 km/s, still much larger than the 0.07 km/s velocity resolution of our observations.\

In Per-emb 1, 10, 11, 17 and 26, the C~2~H emission most closely traces bipolar outflow cavities (Section [3.1](#sub:1)). Of these, the C$_2$H in Per-emb 10 appears very close to the rest velocity. Per-emb 11 and 17 show gradients in the C~2~H kinematics that appear correlated with the kinematic structure of CO, with a transition from red-to-blueshifted emission across the two lobes of the outflow. Interestingly, this pattern holds for both of the outflow-like structures near Per-emb 11. In Per-emb 1, 26, and 27, C$_2$H only traces one outflow lobe, but in both cases shows redshifted emission consistent with the CO kinematics. Per-emb 33 also shows similar kinematic trends between C$_2$H and CO, but has less clearly defined outflow structure. Note that in all cases, the magnitude of the C$_2$H red-or blue-shifting is much lower than the CO velocities. Still, these correlations suggest some connection in the velocity structure between the gas of the outflow cavity and that of the outflow itself. In several sources where no bipolar outflow is clearly identifiable, the C$_2$H emission is uniformly blueshifted (Per-emb 22, 35, 36, 53), possibly due to the extinction of emission originating on the far side of the protostar.\

It is important to consider whether radiative transfer effects may be influencing our comparison between the CO and C$_2$H kinematics. We appear to be tracing optically thinner, higher-velocity CO from the inner region of the outflows, rather than optically thick CO which would originate from the outflow’s outer layers at a lower velocity shift. Therefore, we do not expect that optical depth effects are responsible for any differences in red/blueshift between the two species.

![](C2H_CO.png)

# Discussion

## Evolution of C$_2$H chemistry

This large sample of low-mass protostars provides an opportunity to search for evolutionary patterns in the emission morphology of C$_2$H. As protostars begin to clear away their envelope and mature towards Class II systems, the photochemically active regions could be expected to evolve (cite: bergner2020). In particular, at some stage before $\sim$1 Myr, photochemistry must become active on small scales at the disk position based on the C$_2$H morphologies seen in Class II disks ((cite: bergin2016), (cite: bergner2019), (cite: guzman2021)). Figure [5](#fig:fig4) shows, however, that there is no clear correlation between the C$_2$H emission extent in these Class 0/I sources and the evolutionary metrics of bolometric temperature/luminosity or continuum radius. This can also be seen through visual inspection of Figure [1](#fig:fig1), in which the sources are ordered in terms of increasing bolometric temperature (or increasing maturity). While there are some systems with more compact C$_2$H emission confined to the outflow base (Per-emb 2, 5, 10, 16, 20, 27), which could approximately correspond to a proto-disk surface, there is no obvious evolutionary association. One caveat is that we cannot rule out whether there is a compact C$_2$H component on even smaller spatial scales than we can access with the spatial resolution of these observations.\

The fact that the C$_2$H emission morphology does not apparently evolve during the Class 0/I lifetime implies that a rapid change must happen at the Class I/Class II transition. The detection of bright, compact C$_2$H emission even in relatively young $\lesssim$1 Myr Class II disks (cite: miotello2019; bergner2019) means that small-scale photochemistry must ‘turn on’ soon after the embedded protostar phase. This fast photochemical transition is one of several dramatic chemical changes that seems to occur during the transition from Class I to Class II systems, along with the rapid depletion of CO ((cite: zhang2020), (cite: bergner2020)) and H~2~O ((cite: harsono2020)). Studying the volatile chemistry in intermediary sources between the embedded protostellar and mature disk stages will be crucial to disentangling these processes.

## C$_2$H formation chemistry in embedded protostars

Our study of C$_2$H in Perseus protostars provides insight into the underlying C$_2$H chemistry in these embedded environments. In mature systems, C$_2$H is associated with the ingredients of high-C/O gas, and high UV fields (cite: bergin2016). We show here that C$_2$H can be used to trace both of these conditions in the embedded stage as well.

The zeroth-moment maps in Figure [1](#fig:fig1) reveal that many of the Perseus protostars exhibit C$_2$H emission with a motif of x-wing or cone like structure, which widen moving away from the continuum. The coincidence of these directional, cone or wing-like structures with the edges of the CO emission strongly points to a relationship between C$_2$H and the overall outflow structure. With this large and unbiased sample, we can confirm the trend between C$_2$H and outflow cavity walls previously identified in individual protostars: B1-c (cite: tychoniec2021), CB68 (cite: imai2022), and IRAS 15398–3359 (cite: oya2014; okoda2018). The presence of C$_2$H and similar hydrocarbons (e.g. c-C$_3$H$_2$ in SMM3; (cite: tychoniec2021)) at the intersection between the outflow and the envelope can be attributed to the prevalence of UV photons in these low density regions, which are needed to produce hydrocarbon radicals. The fact that several protostars do not clearly show this association or it appears incomplete may be due to unfavorable viewing geometries (e.g. if the outflow is pointing toward or away from the line of sight), more complicated source structures or the chemical effects discussed below. Indeed, in all cases where we could clearly identify a bipolar CO outflow structure, we see C$_2$H emission associated with the base and/or edges of at least one side of the outflow cavity.\

We can also investigate the role of gas-phase oxygen in suppressing C$_2$H production by comparing the C$_2$H and SO emission morphologies. SO is associated with the sputtering of icy material from grains and therefore serves as a signpost of oxygen rich gas ((cite: bachiller1997), (cite: Jimenez-Serra2005)). Figure [3](#fig:fig3) shows a clear spatial anti-correlation between C$_2$H and SO, implying that C$_2$H production cannot be sustained in gas that is oxygen rich. Indeed, of the 14 Perseus sources where C$_2$H is present and the outflow could be clearly identified, 12 sources exhibit strong avoidance between SO and C$_2$H. This behavior in sources where the SO is compact and co-spatial with the continuum (Per-emb 5, 29, 26, 25) could be attributed to differing physical or chemical factors close to the protostar. However, this cannot explain the avoidance of the two species in the sources where the SO emission is offset from the continuum (Per-emb 27, 14, 11, 53, 1). The fact that this trend exists for a range of SO and C$_2$H structures points to the destruction of C$_2$H in regions traced by SO.\

This behavior is consistent with expectations from chemical modeling: in oxygen rich gas, available gas-phase carbon will react with oxygen or O-bearing species, thereby suppressing the formation of hydrocarbons (cite: Bergin1997; Hollenbach2009; Du2015). (cite: bosman2021) has shown this threshold gas phase C/O ratio is dependent of the UV field strength and overall gas density, but for a UV field to gas density ratio ($F_{UV}/n_{gas}$) of 10^-7^ - 10^-5^ G~0~ cm^3^, this hydrocarbon production is quenched as the C/O falls below unity. Interestingly, spatial anti-correlations between small hydrocarbons and SO are also seen in the mature Herbig disks HD 169142 and HD 100546 (cite: booth2023; booth2024). C$_2$H can therefore serve as a reliable tracer to distinguish O-rich vs. O-poor gas within protostellar environments. Indeed, while the SO observed in our sources is likely produced at least in part by weak-shock sputtering of grains ((cite: PEACHES_II)), we expect O-rich gas to be present on even smaller spatial scales due to the thermal sublimation of icy material, for instance the spatially unresolved detections of O-bearing complex organics reported in (cite: PEACHES_I). Higher-resolution observations of organics as well as C$_2$H would provide a more detailed picture of the balance between O- and C-dominated gas on smaller, disk-forming scales in the protostellar environment.\

While the C$_2$H morphologies are quite different between embedded protostars and mature disks, the column densities are relatively consistent. As shown in Figure [4](#fig:fig5), we retrieve column densities ranging from 10^14^ - 10^15^ cm^-2^ with an average C$_2$H column density across all sources of 10^14.3\ $\pm$\ 0.2^ cm^-2^. This is comparable to values estimated in the Class II sources in (cite: guzman2021), and to the column densities predicted by PDR chemical models (cite: nagy2015). The similar column densities across these varied contexts points to a formation chemistry dependent on a narrow range of physical conditions: i.e., if C$_2$H is always formed within a thin gas layer characterized by high UV fluxes, then the resulting column density may be similar even in different astrophysical objects. Note, however, that coverage of additional J-level transitions would improve the precision of our column density retrievals.

# Summary

Using ALMA 12m and SMA data as part of the PEACHES and MASSES projects and new ALMA ACA observations, we analyze the C$_2$H emission morphology towards 35 embedded protostars in Perseus.

- We present zeroth-moment maps of the C$_2$H in the the sources, and show many exhibit a emission morphology which traces the protostar outflow cavity.

- Analysis of the C$_2$H and SO emission morphologies though the use of outflow intensity traces shows strong spatial avoidance between the two molecules, demonstrating the role of gas-phase oxygen in the formation chemistry of C$_2$H.

- The C$_2$H emission morphology appears to not be directly related to protostar age though comparisons of C$_2$H structure with source bolometric temperature and deconvolved continuum radius, however all sources where C$_2$H is detected exhibit large, extended structure, indicating the transition in C$_2$H morphology to what is seen in mature disks must happen rapidly.

- The C$_2$H spectra of combined 12m and ACA images is fit to a spectral line model, and maps of the fitted column density show C$_2$H column densities of  10^14^ - 10^15^ cm^-2^.

Through these observations and analysis, we are able to better understand C$_2$H morphology and the role of oxygen in the formation of C$_2$H over a large survey of protostellar sources. Additionally, we better understand the rapid transition that these low-mass sources must undergo from the embedded stage to the mature disk stage, as the photochemically active regions that C$_2$H trace go from extended and surrounding the outflows to on the surface of the disk once the star is clear of its envelope. To further investigate the difference between the C$_2$H distribution around Class 0/I sources and that in disks around Class II sources, analyzing the correlation between the outflow opening-angle and the distributions of C$_2$H and outflow-tracing molecules may serve as a useful diagnostic. Additionally, in some sources with high C$_2$H abundances, other mechanisms beyond C$_2$H formation in the cavity wall may need to be considered (cite: sakai2013; aikawa2020). Further studies of C$_2$H in sources just at the end of their embedded protostar stage may yield more information about when in planet formation period C$_2$H and other photochemically active molecules may be formed in regions undergoing the very first stages of planet formation.

# Acknowledgments

The PEACHES project is supported by the MEXT/JSPS Grant-in-Aid from the Ministry of Education, Culture, Sports, Science, and Technology of Japan (JP20H05844 and JP20H05845). J.B. and J.A. are grateful for support from UC Berkeley and the UC Berkeley College of Chemistry. This research used the Savio computational cluster resource provided by the Berkeley Research Computing program at the University of California, Berkeley (supported by the UC Berkeley Chancellor, Vice Chancellor for Research, and Chief Information Officer). Y.-L.Y., Y.Z., and N.S. are grateful for support from the RIKEN pioneering project: Evolution of Matter in the Universe. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01501.S, ADS/JAO.ALMA#2017.1.01462.S., and ADS/JAO.ALMA#2022.1.00303.S. ALMA is a partnership of the ESO (representing its member states), the NSF (USA) and NINS (Japan), together with the NRC (Canada) and the NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by the ESO, the AUI/NRAO, and the NAOJ.\
Facility: ALMA

# Appendix: 12m + ACA Images

![](Figure6.png)

In Figure [7](#fig:fig6), we present the moment-0 maps of the C$_2$H emission from both the 12m ALMA PEACHES data as well as the combined 12m + ACA images. The red contours show the 12m only and the blue contours and colormap show the 12m + ACA images. For all sources, the contours are drawn at 35 mJy/beam as well as the colormap minimum. The combined 12m + ACA images, as compared to the imaging the 12m data alone contoured at the same flux of 35 mJy/beam reveals more large scale structure in the C$_2$H surrounding the sources, with the exception of Per-emb 14. As expected, these images still retain the general spatial morphology seen in the 12m images. As the combined 12m + ACA images are less sensitive to small scale structure, we use the 12m only images for the spatial analyses with SO in section [3.1](#sub:1).

# Appendix: Line and Continuum Imaging Tables

|     Source     | Max (mJy/beam) | RMS (mJy/beam) |  Beam (")   |
|:--------------:|:--------------:|:--------------:|:-----------:|
|   Per-emb 53   |     18.30      |      0.09      | 0.59 x 0.42 |
|   Per-emb 16   |      6.00      |      0.13      | 0.69 x 0.59 |
|   Per-emb 8    |     56.86      |      0.14      | 0.57 x 0.39 |
|  Per-emb 11 A  |     127.53     |      0.29      | 0.58 x 0.40 |
|   Per-emb 1    |     53.60      |      0.62      | 0.57 x 0.39 |
|   Per-emb 5    |     169.17     |      0.31      | 0.56 x 0.40 |
|   Per-emb 2    |     115.35     |      0.54      | 0.59 x 0.43 |
|   Per-emb 40   |     13.58      |      0.09      | 0.56 x 0.40 |
|   Per-emb 10   |     18.15      |      0.09      | 0.56 x 0.40 |
|   Per-emb 29   |     95.14      |      0.25      | 0.56 x 0.40 |
| Per-emb-41 N/S |     128.81     |      0.25      | 0.56 x 0.41 |
|    L1448 NW    |     56.25      |      0.71      | 0.59 x 0.36 |
|  Per-emb 33 A  |     155.65     |      0.39      | 0.59 x 0.36 |
|   Per-emb 26   |     145.36     |      0.48      | 0.60 x 0.37 |
|  Per-emb 22 A  |     30.46      |      0.17      | 0.59 x 0.36 |
|   Per-emb 25   |     86.84      |      0.22      | 0.59 x 0.37 |
|   Per-emb 17   |     34.07      |      0.17      | 0.59 x 0.37 |
|   Per-emb 20   |      8.25      |      0.38      | 1.01 x 0.93 |
|  L1455 IRS 2   |      2.04      |      0.15      | 0.58 x 0.37 |
|   Per-emb 44   |     148.83     |      2.13      | 0.63 x 0.40 |
|   Per-emb 12   |     502.33     |      1.06      | 0.63 x 0.40 |
|   Per-emb 13   |     311.00     |      0.51      | 0.63 x 0.40 |
|   Per-emb 27   |     141.23     |      0.34      | 0.63 x 0.40 |
|   Per-emb 54   |      1.62      |      0.09      | 0.63 x 0.40 |
|   Per-emb 21   |     43.37      |      0.16      | 0.63 x 0.40 |
|   Per-emb 14   |     62.19      |      0.14      | 0.63 x 0.40 |
| Per-emb 35 A/B |     21.47      |      0.11      | 0.63 x 0.40 |
|    SVS 13B     |     140.67     |      0.36      | 0.63 x 0.40 |
|   Per-emb 15   |      5.32      |      0.15      | 0.70 x 0.56 |
|   Per-emb 50   |     82.65      |      0.19      | 0.63 x 0.40 |
|   Per-emb 18   |     65.08      |      0.71      | 0.63 x 0.40 |
|   Per-emb 37   |     11.06      |      0.09      | 0.63 x 0.40 |
|   Per-emb 60   |      1.76      |      0.09      | 0.63 x 0.40 |
|  EDJ2009-172   |     12.94      |      0.09      | 0.63 x 0.40 |
|   Per-emb 36   |     112.16     |      0.24      | 0.63 x 0.40 |

: Continuum Parameters

+----------------+------------------------------------------------+------------------------------------------------+
|                | C$_2$H                                         | SO                                             |
+:==============:+:========:+:========:+:==========:+:===========:+:========:+:========:+:==========:+:===========:+
|                | Moment 0            | Channel    |             | Moment 0            | Channel    |             |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Source         | Max      | RMS      | RMS        | Beam        | Max      | RMS      | RMS        | Beam        |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
|                | (mJy/beam\*km/s)    | (mJy/beam) | (")         | (mJy/beam\*km/s)    | (mJy/beam) | (")         |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 53     | 91.45    | 6.42     | 4.87       | 0.56 x 0.37 | 776.73   | 6.44     | 5.38       | 0.57 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 16     | 56.44    | 5.69     | 4.73       | 0.55 x 0.37 | 81.05    | 10.07    | 4.79       | 0.67 x 0.40 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 8      | 86.34    | 7.47     | 4.80       | 0.55 x 0.37 | 142.25   | 8.50     | 4.67       | 0.58 x 0.39 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 11 A   | 59.55    | 6.28     | 4.88       | 0.55 x 0.37 | 245.98   | 10.03    | 5.31       | 0.58 x 0.39 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 1      | 51.10    | 5.86     | 4.66       | 0.55 x 0.38 | 288.86   | 24.42    | 10.25      | 0.58 x 0.39 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 5      | 50.28    | 5.85     | 4.76       | 0.53 x 0.38 | 33.77    | 5.71     | 4.75       | 0.54 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 2      | 52.62    | 7.44     | 4.68       | 0.54 x 0.38 | 179.54   | 6.48     | 4.64       | 0.54 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 40     | 36.88    | 7.61     | 4.84       | 0.54 x 0.38 | 379.63   | 21.95    | 4.65       | 0.54 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 10     | 83.97    | 7.33     | 4.78       | 0.54 x 0.38 | 360.86   | 7.10     | 4.74       | 0.54 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 29     | 45.50    | 7.11     | 4.79       | 0.54 x 0.38 | 435.62   | 13.24    | 5.80       | 0.54 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb-41 N/S | 32.11    | 6.37     | 4.72       | 0.54 x 0.38 | 103.74   | 6.11     | 4.74       | 0.54 x 0.38 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| L1448 NW       | 88.36    | 7.01     | 5.32       | 0.68 x 0.43 | 411.02   | 7.67     | 5.26       | 0.67 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 33 A   | 197.92   | 8.57     | 5.35       | 0.68 x 0.43 | 168.93   | 9.04     | 5.48       | 0.67 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 26     | 66.70    | 5.66     | 5.08       | 0.67 x 0.43 | 339.26   | 23.78    | 6.23       | 0.67 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 22 A   | 150.10   | 7.25     | 5.12       | 0.68 x 0.43 | 601.36   | 12.42    | 5.04       | 0.67 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 25     | 63.27    | 7.85     | 5.13       | 0.70 x 0.45 | 538.26   | 6.54     | 5.02       | 0.67 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 17     | 75.88    | 7.86     | 5.21       | 0.68 x 0.43 | 2656.63  | 59.39    | 6.36       | 0.66 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 20     | 114.13   | 7.29     | 5.20       | 0.68 x 0.43 | 465.58   | 7.67     | 5.09       | 0.66 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| L1455 IRS 2    | 30.84    | 7.10     | 5.18       | 0.67 x 0.43 | 31.28    | 6.84     | 4.99       | 0.66 x 0.43 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 44     | 147.33   | 13.19    | 5.67       | 0.71 x 0.45 | 3794.34  | 15.61    | 5.42       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 12     | 127.98   | 8.34     | 5.65       | 0.71 x 0.45 | 1184.92  | 51.15    | 8.75       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 13     | 113.12   | 12.51    | 5.69       | 0.71 x 0.45 | 473.99   | 24.11    | 5.95       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 27     | 60.35    | 8.66     | 5.78       | 0.71 x 0.45 | 3705.70  | 138.48   | 8.31       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 54     | 78.32    | 9.37     | 5.82       | 0.71 x 0.45 | 224.24   | 8.54     | 5.64       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 21     | 73.45    | 11.57    | 5.68       | 0.71 x 0.45 | 441.03   | 9.14     | 5.50       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 14     | 111.01   | 7.53     | 5.68       | 0.71 x 0.45 | 530.19   | 7.26     | 5.42       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 35 A/B | 168.85   | 7.42     | 5.68       | 0.71 x 0.45 | 1335.69  | 13.84    | 5.43       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| SVS 13B        | 149.13   | 7.72     | 5.53       | 0.71 x 0.45 | 1149.74  | 18.95    | 5.56       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 15     | 35.58    | 7.43     | 5.64       | 0.71 x 0.45 | 51.32    | 10.21    | 5.51       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 50     | 35.92    | 7.71     | 5.68       | 0.71 x 0.45 | 2270.27  | 46.94    | 6.28       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 18     | 159.19   | 7.21     | 5.62       | 0.71 x 0.45 | 1280.34  | 15.02    | 5.41       | 0.72 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 37     | 38.87    | 6.94     | 5.64       | 0.72 x 0.45 | 194.68   | 9.68     | 5.56       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 60     | 33.61    | 9.13     | 5.81       | 0.72 x 0.45 | 51.14    | 9.94     | 5.65       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| EDJ2009-172    | 37.73    | 8.92     | 5.67       | 0.71 x 0.45 | 43.44    | 9.95     | 5.50       | 0.72 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+
| Per-emb 36     | 230.23   | 8.17     | 5.71       | 0.71 x 0.45 | 1031.61  | 23.11    | 5.28       | 0.71 x 0.45 |
+----------------+----------+----------+------------+-------------+----------+----------+------------+-------------+

: Line Parameters

+:-----------:+:-----------:+:-----------:+
|             | Log N$_T$ (cm$^{-2})$     |
+-------------+-------------+-------------+
| Source      | Median      | Range       |
+-------------+-------------+-------------+
| Per-emb 53  | 14.47       | 1.34        |
+-------------+-------------+-------------+
| Per-emb 16  | 14.36       | 1.16        |
+-------------+-------------+-------------+
| Per-emb 8   | 14.59       | 1.51        |
+-------------+-------------+-------------+
| Per-emb 11  | 14.48       | 1.21        |
+-------------+-------------+-------------+
| Per-emb 1   | 14.36       | 1.05        |
+-------------+-------------+-------------+
| Per-emb 5   | 14.28       | 1.49        |
+-------------+-------------+-------------+
| Per-emb 2   | 14.42       | 1.05        |
+-------------+-------------+-------------+
| Per-emb 40  | 14.29       | 1.00        |
+-------------+-------------+-------------+
| Per-emb 10  | 14.42       | 2.03        |
+-------------+-------------+-------------+
| Per-emb 29  | 14.11       | 1.32        |
+-------------+-------------+-------------+
| Per-emb 41  | 14.18       | 0.92        |
+-------------+-------------+-------------+
| L1448 NW    | 14.48       | 2.97        |
+-------------+-------------+-------------+
| Per-emb 33  | 14.59       | 1.52        |
+-------------+-------------+-------------+
| Per-emb 26  | 14.15       | 1.69        |
+-------------+-------------+-------------+
| Per-emb 22  | 14.25       | 1.10        |
+-------------+-------------+-------------+
| Per-emb 25  | 14.21       | 1.13        |
+-------------+-------------+-------------+
| Per-emb 17  | 14.19       | 1.08        |
+-------------+-------------+-------------+
| Per-emb 20  | 14.16       | 1.29        |
+-------------+-------------+-------------+
| L1455 IRS 2 | 14.05       | 1.29        |
+-------------+-------------+-------------+
| Per-emb 44  | 14.19       | 1.11        |
+-------------+-------------+-------------+
| Per-emb 12  | 13.99       | 1.35        |
+-------------+-------------+-------------+
| Per-emb 13  | 14.04       | 1.39        |
+-------------+-------------+-------------+
| Per-emb 27  | 14.14       | 1.23        |
+-------------+-------------+-------------+
| Per-emb 54  | 14.31       | 1.42        |
+-------------+-------------+-------------+
| Per-emb 21  | 14.64       | 1.86        |
+-------------+-------------+-------------+
| Per-emb 14  | 14.08       | 0.84        |
+-------------+-------------+-------------+
| Per-emb 35  | 14.23       | 1.05        |
+-------------+-------------+-------------+
| SVS 13B     | 14.49       | 1.86        |
+-------------+-------------+-------------+
| Per-emb 15  | 13.97       | 1.15        |
+-------------+-------------+-------------+
| Per-emb 50  | 14.01       | 0.91        |
+-------------+-------------+-------------+
| Per-emb 18  | 14.27       | 2.18        |
+-------------+-------------+-------------+
| Per-emb 37  | 14.00       | 0.39        |
+-------------+-------------+-------------+
| Per-emb 36  | 14.32       | 1.07        |
+-------------+-------------+-------------+

: Fitted C$_2$H Column Densities

natexlab

(ref: aikawa2020) Aikawa, Y., Furuya, K., Yamamoto, S., & Sakai, N. 2020, ApJ, 897, 110, doi: [`10.3847/1538-4357/ab994a`](http://doi.org/10.3847/1538-4357/ab994a)

(ref: arce_sargent2006) Arce, H. G., & Sargent, A. I. 2006, ApJ, 646, 1070, doi: [`10.1086/505104`](http://doi.org/10.1086/505104)

(ref: PEACHES_III) Artur de la Villarmois, E., Guzmán, V. V., Yang, Y. L., Zhang, Y., & Sakai, N. 2023, A&A, 678, A124, doi: [`10.1051/0004-6361/202346728`](http://doi.org/10.1051/0004-6361/202346728)

(ref: arturdelavillarmois2019) Artur de la Villarmois, E., Jørgensen, J. K., Kristensen, L. E., et al. 2019, A&A, 626, A71, doi: [`10.1051/0004-6361/201834877`](http://doi.org/10.1051/0004-6361/201834877)

(ref: bachiller1997) Bachiller, R., & Pérez Gutiérrez, M. 1997, ApJL, 487, L93, doi: [`10.1086/310877`](http://doi.org/10.1086/310877)

(ref: bergin2016) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101, doi: [`10.3847/0004-637X/831/1/101`](http://doi.org/10.3847/0004-637X/831/1/101)

(ref: Bergin1997) Bergin, E. A., Goldsmith, P. F., Snell, R. L., & Langer, W. D. 1997, ApJ, 482, 285, doi: [`10.1086/304108`](http://doi.org/10.1086/304108)

(ref: bergner2019) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2019, ApJ, 876, 25, doi: [`10.3847/1538-4357/ab141e`](http://doi.org/10.3847/1538-4357/ab141e)

(ref: bergner2020) —. 2020, ApJ, 898, 97, doi: [`10.3847/1538-4357/ab9e71`](http://doi.org/10.3847/1538-4357/ab9e71)

(ref: booth2023) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macı́as, E. 2023, A&A, 678, A146, doi: [`10.1051/0004-6361/202346974`](http://doi.org/10.1051/0004-6361/202346974)

(ref: booth2024) Booth, A. S., Leemker, M., van Dishoeck, E. F., et al. 2024, AJ, 167, 164, doi: [`10.3847/1538-3881/ad2700`](http://doi.org/10.3847/1538-3881/ad2700)

(ref: bosman2021) Bosman, A. D., Alarcón, F., Zhang, K., & Bergin, E. A. 2021, ApJ, 910, 3, doi: [`10.3847/1538-4357/abe127`](http://doi.org/10.3847/1538-4357/abe127)

(ref: calahan2023) Calahan, J. K., Bergin, E. A., Bosman, A. D., et al. 2023, Nature Astronomy, 7, 49, doi: [`10.1038/s41550-022-01831-8`](http://doi.org/10.1038/s41550-022-01831-8)

(ref: alma_handbook) Cortes, P., Vlahakis, C., Hales, A., et al. 2023, ALMA Cycle 11 Technical Handbook, doi: [`10.5281/zenodo.7822943`](http://doi.org/10.5281/zenodo.7822943)

(ref: Curtis2010) Curtis, E. I., Richer, J. S., Swift, J. J., & Williams, J. P. 2010, MNRAS, 408, 1516, doi: [`10.1111/j.1365-2966.2010.17214.x`](http://doi.org/10.1111/j.1365-2966.2010.17214.x)

(ref: Du2015) Du, F., Bergin, E. A., & Hogerheijde, M. R. 2015, ApJL, 807, L32, doi: [`10.1088/2041-8205/807/2/L32`](http://doi.org/10.1088/2041-8205/807/2/L32)

(ref: Dunham2014) Dunham, M. M., Arce, H. G., Mardones, D., et al. 2014a, ApJ, 783, 29, doi: [`10.1088/0004-637X/783/1/29`](http://doi.org/10.1088/0004-637X/783/1/29)

(ref: Dunham2010) Dunham, M. M., Evans, N. J., Bourke, T. L., et al. 2010, ApJ, 721, 995, doi: [`10.1088/0004-637X/721/2/995`](http://doi.org/10.1088/0004-637X/721/2/995)

(ref: dunham2014review) Dunham, M. M., Stutz, A. M., Allen, L. E., et al. 2014b, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 195–218, doi: [`10.2458/azu_uapress_9780816531240-ch009`](http://doi.org/10.2458/azu_uapress_9780816531240-ch009)

(ref: guzman2021) Guzmán, V. V., Bergner, J. B., Law, C. J., et al. 2021, ApJS, 257, 6, doi: [`10.3847/1538-4365/ac1440`](http://doi.org/10.3847/1538-4365/ac1440)

(ref: harsono2018) Harsono, D., Bjerkeli, P., van der Wiel, M. H., et al. 2018, Nature Astronomy, 2, 646

(ref: harsono2020) Harsono, D., Persson, M. V., Ramos, A., et al. 2020, A&A, 636, A26, doi: [`10.1051/0004-6361/201935994`](http://doi.org/10.1051/0004-6361/201935994)

(ref: Hatchell2007) Hatchell, J., Fuller, G. A., & Richer, J. S. 2007, A&A, 472, 187, doi: [`10.1051/0004-6361:20066467`](http://doi.org/10.1051/0004-6361:20066467)

(ref: heays2017) Heays, A. N., Bosman, A. D., & van Dishoeck, E. F. 2017, A&A, 602, A105, doi: [`10.1051/0004-6361/201628742`](http://doi.org/10.1051/0004-6361/201628742)

(ref: Hollenbach2009) Hollenbach, D., Kaufman, M. J., Bergin, E. A., & Melnick, G. J. 2009, ApJ, 690, 1497, doi: [`10.1088/0004-637X/690/2/1497`](http://doi.org/10.1088/0004-637X/690/2/1497)

(ref: imai2022) Imai, M., Oya, Y., Svoboda, B., et al. 2022, ApJ, 934, 70, doi: [`10.3847/1538-4357/ac77e7`](http://doi.org/10.3847/1538-4357/ac77e7)

(ref: jansen1995) Jansen, D. J., Spaans, M., Hogerheijde, M. R., & van Dishoeck, E. F. 1995, A&A, 303, 541

(ref: Jimenez-Serra2005) Jiménez-Serra, I., Martı́n-Pintado, J., Rodrı́guez-Franco, A., & Martı́n, S. 2005, ApJL, 627, L121, doi: [`10.1086/432467`](http://doi.org/10.1086/432467)

(ref: krijt2020) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134, doi: [`10.3847/1538-4357/aba75d`](http://doi.org/10.3847/1538-4357/aba75d)

(ref: krijt2018) Krijt, S., Schwarz, K. R., Bergin, E. A., & Ciesla, F. J. 2018, ApJ, 864, 78, doi: [`10.3847/1538-4357/aad69b`](http://doi.org/10.3847/1538-4357/aad69b)

(ref: lada1987) Lada, C. J. 1987, in Symposium-International astronomical union, Vol. 115, Cambridge University Press, 1–18

(ref: manara2018) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3, doi: [`10.1051/0004-6361/201834076`](http://doi.org/10.1051/0004-6361/201834076)

(ref: Maury2019) Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76, doi: [`10.1051/0004-6361/201833537`](http://doi.org/10.1051/0004-6361/201833537)

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: miotello2019) Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019, A&A, 631, A69, doi: [`10.1051/0004-6361/201935441`](http://doi.org/10.1051/0004-6361/201935441)

(ref: Myers1998) Myers, P. C., Adams, F. C., Chen, H., & Schaff, E. 1998, ApJ, 492, 703, doi: [`10.1086/305048`](http://doi.org/10.1086/305048)

(ref: myers1993) Myers, P. C., & Ladd, E. F. 1993, ApJL, 413, L47, doi: [`10.1086/186956`](http://doi.org/10.1086/186956)

(ref: nagy2015) Nagy, Z., Ossenkopf, V., Van der Tak, F. F. S., et al. 2015, A&A, 578, A124, doi: [`10.1051/0004-6361/201424220`](http://doi.org/10.1051/0004-6361/201424220)

(ref: okoda2018) Okoda, Y., Oya, Y., Sakai, N., et al. 2018, ApJL, 864, L25, doi: [`10.3847/2041-8213/aad8ba`](http://doi.org/10.3847/2041-8213/aad8ba)

(ref: oya2018) Oya, Y., Sakai, N., Watanabe, Y., et al. 2018, ApJ, 863, 72, doi: [`10.3847/1538-4357/aacf42`](http://doi.org/10.3847/1538-4357/aacf42)

(ref: oya2014) Oya, Y., Sakai, N., Sakai, T., et al. 2014, ApJ, 795, 152, doi: [`10.1088/0004-637X/795/2/152`](http://doi.org/10.1088/0004-637X/795/2/152)

(ref: Parker1991) Parker, N. D., Padman, R., & Scott, P. F. 1991, MNRAS, 252, 442, doi: [`10.1093/mnras/252.3.442`](http://doi.org/10.1093/mnras/252.3.442)

(ref: sakai2010) Sakai, N., Saruwatari, O., Sakai, T., Takano, S., & Yamamoto, S. 2010, A&A, 512, A31, doi: [`10.1051/0004-6361/200913098`](http://doi.org/10.1051/0004-6361/200913098)

(ref: sakai2013) Sakai, N., & Yamamoto, S. 2013, Chemical Reviews, 113, 8981, doi: [`10.1021/cr4001308`](http://doi.org/10.1021/cr4001308)

(ref: sakai2014_a) Sakai, N., Oya, Y., Sakai, T., et al. 2014a, ApJL, 791, L38, doi: [`10.1088/2041-8205/791/2/L38`](http://doi.org/10.1088/2041-8205/791/2/L38)

(ref: sakai2014_b) Sakai, N., Sakai, T., Hirota, T., et al. 2014b, Nature, 507, 78, doi: [`10.1038/nature13000`](http://doi.org/10.1038/nature13000)

(ref: sakai2017) Sakai, N., Oya, Y., Higuchi, A. E., et al. 2017, MNRAS, 467, L76, doi: [`10.1093/mnrasl/slx002`](http://doi.org/10.1093/mnrasl/slx002)

(ref: MASSESData) Stephens, I. 2019, Top Level README - MASSES Full Data Release, V1, Harvard Dataverse, doi: [`10.7910/DVN/N5ISPG`](http://doi.org/10.7910/DVN/N5ISPG)

(ref: MASSES) Stephens, I. W., Bourke, T. L., Dunham, M. M., et al. 2019, ApJS, 245, 21, doi: [`10.3847/1538-4365/ab5181`](http://doi.org/10.3847/1538-4365/ab5181)

(ref: tobin2016) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73, doi: [`10.3847/0004-637X/818/1/73`](http://doi.org/10.3847/0004-637X/818/1/73)

(ref: tobin2020) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, The Astrophysical Journal, 890, 130

(ref: tychoniec2021) Tychoniec, Ł., van Dishoeck, E. F., van’t Hoff, M. L. R., et al. 2021, A&A, 655, A65, doi: [`10.1051/0004-6361/202140692`](http://doi.org/10.1051/0004-6361/202140692)

(ref: vanclepper2022) Van Clepper, E., Bergner, J. B., Bosman, A. D., Bergin, E., & Ciesla, F. J. 2022, ApJ, 927, 206, doi: [`10.3847/1538-4357/ac511b`](http://doi.org/10.3847/1538-4357/ac511b)

(ref: PEACHES_I) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20, doi: [`10.3847/1538-4357/abdfd6`](http://doi.org/10.3847/1538-4357/abdfd6)

(ref: zhang2020) Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJL, 891, L17, doi: [`10.3847/2041-8213/ab7823`](http://doi.org/10.3847/2041-8213/ab7823)

(ref: zhang2018) Zhang, Y., Higuchi, A. E., Sakai, N., et al. 2018, ApJ, 864, 76, doi: [`10.3847/1538-4357/aad7ba`](http://doi.org/10.3847/1538-4357/aad7ba)

(ref: PEACHES_II) Zhang, Z. E., Yang, Y.-l., Zhang, Y., et al. 2023, ApJ, 946, 113, doi: [`10.3847/1538-4357/acbdf7`](http://doi.org/10.3847/1538-4357/acbdf7)

</paper>

Write the methods card for this paper.