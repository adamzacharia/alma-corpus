# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A..70N\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...691A..70N",
 "title": "Disruption of a massive molecular cloud by a supernova in the Galactic Centre: Initial results from the ACES project",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Nonhebel, M.",
 "n_authors": 36,
 "arxiv_id": "2409.12185",
 "doi": "10.1051/0004-6361/202451190",
 "alma_projects_linked_by_archive": [
  "2021.1.00172.L"
 ]
}
```

Paper text:
<paper>
# Disruption of a massive molecular cloud by a supernova in the Galactic Centre

# Introduction

![](figures/hnco_rgb_v3.pdf)

The Central Molecular Zone (CMZ) is defined as the region within a galactocentric radius of approximately 300 pc (see (cite: Henshaw2023)). This unique region of the Milky Way hosts the nearest supermassive black hole (e.g. (cite: GRAVITYCollaboration2018; GRAVITYCollaboration2019)), some of the most massive young star clusters (Arches and Quintuplet; e.g. (cite: Clark2018)), the largest number of supernovae (SNe) per unit volume (e.g. (cite: Ponti2015)), and the largest concentration of dense molecular gas in the Galaxy (see Fig. [1](#fig_CMZ_HNCO_peak), upper-right panel), making the CMZ an environment unparalleled in the Milky Way. The interstellar medium (ISM) conditions at the centre of the Galaxy starkly contrast those of the solar neighbourhood. Turbulent motions, magnetic field strengths, gas densities, pressures, and temperatures are orders of magnitude greater than those measured locally (see the recent reviews by e.g. (cite: Morris1996; Bryant2021; Henshaw2023) and references therein). Many of these properties resemble conditions found at earlier epochs in the Universe (cite: Kruijssen2013). In terms of large-scale dynamical effects, the CMZ is also extreme. Inflowing gas rapidly travels along the bar and interacts with pre-existing gas within the CMZ (cite: Sormani2019; Hatchfield2021), with strong cloud–cloud collisions thought to shape the unique structures of various molecular clouds in the region (cite: Gramze2023). Furthermore, the CMZ experiences strong gravitational shear due to differential rotation, with powerful tidal forces capable of stretching and tearing apart molecular clouds (cite: Kruijssen2019a). Taken together, the extreme environment in terms of its constituents, properties, and dynamics renders the CMZ ripe for structures not observed elsewhere in the Milky Way.

One prominent feature in the CMZ that has garnered significant interest is the M0.8$-$0.2 ring: a ring-like gaseous structure situated in the south-eastern extension of the Sgr B2 molecular cloud complex (see Fig. [1](#fig_CMZ_HNCO_peak), upper-right panel). It was initially detected in continuum observations with SCUBA ((cite: Holland1999)) at 450 and 850 $\mu$m, at resolutions of 8 and 15$''$, respectively (PPR G0.80$-$0.18 in (cite: Pierce-Price2000)). (cite: Pierce-Price2000) suggested it was a wind-blown region or a supernova remnant (SNR). The ring-like structure is also distinctly evident in molecular line emission (Shell 5 in (cite: Tsuboi2015), GCM0.83$-$0.18 in (cite: Mills2017)). Using H$^{13}$CO$^+$ (1–0) and SiO (2–1) line observations at $\sim40\ensuremath{''}$ acquired with the 45 m Nobeyama telescope, (cite: Tsuboi2015) identified the structure as a shell with a diameter of $\sim15$ pc, along with several other shells in the region. They interpret the broad velocity-width of the structure in $l-v$ space as evidence of its expansion, and attribute this expansion to successive SN explosions. Polarimetry studies of the M0.8$-$0.2 ring using the SOFIA telescope indicate that the magnetic field is curved and follows the contours of the emission towards the region (cite: Butterfield2023; Butterfield2024). Additionally, the equipartition magnetic field strength from MeerKAT observations has been estimated to be approximately 0.05 mG (cite: Yusef-Zadeh2022). (cite: Butterfield2024) similarly argue that this ring-like structure is expanding, compressing the ambient gas and thereby strengthening the magnetic field.

Numerous studies have highlighted the prevalence of interesting chemistry in the region. The Mopra 3 mm and 7 mm CMZ surveys (cite: Jones2012; Jones2013) reveal that the M0.8$-$0.2 ring is prominently seen in HNCO, HC$_{3}$N, CH$_{3}$CN, CH$_{3}$OH, and SiO emission, as well as to a lesser extent in CS and N$_{2}$H$^{+}$; however, it is not present in HCN or HNC observations. The lines in which it is observed are generally considered dense core or hot core tracers, with HNCO and SiO also known to trace shocks. HNCO notably stood out in the fourth component of the principal component analysis (PCA) within the M0.8$-$0.2 ring and in Sgr B2-North (see (cite: Jones2012)) but nowhere else across the PCA4 map, hinting at some similarity in physical conditions between these two regions. SiO was anti-correlated with HNCO in PCA4, possibly indicating slow shocks. The multi-transition HNCO study by (cite: Martin2008) found a high abundance of HNCO in the region ($\log(X_\mathrm{HNCO}) \approx -8$), again suggesting the presence of shocked gas. Together, these findings point towards a relatively gentle expansion of the ring-like structure.

In this study we made use of new data from the ALMA CMZ Exploration Survey (ACES), which provides an order of magnitude higher spatial and spectral resolution view of the dense and shocked gas across the whole CMZ. In Sect. [2](#sec_obs) we provide an overview of the observations. In Sect. [3](#sec_structure) we introduce the structure of the M0.8$-$0.2 ring with the new ALMA observations (Sects. [3.1](#subsec_morphology) and [3.2](#subsec_kinematics)) and assess its kinematic properties, providing estimates of the mass and energy (Sect. [3.3](#subsec_mass)). We also compare to previous multi-wavelength observations (Sect. [3.4](#subsec_multiwave)). In Sect. [4](#sec_cause) we discuss possible causes of the structure, including young (Sect. [4.1](#subsec_youngfeedback)) and late-stage (Sect. [4.2](#subsec_supernova)) stellar feedback, before considering alternate scenarios such as cloud–cloud collisions and large-scale dynamics (Sect. [4.3](#subsec_alternatives)). Finally, the main results of this paper are summarised in Sect. [5](#sec_conclusions). In the appendices, we provide additional observational information (Appendix [6](#appendixsec_obs)), investigate the radial profiles of molecular line emission across the region (Appendix [7](#appendixsec_radprof)), and present channel maps for a number of lines (Appendix [8](#appendixsec_chans)).

| Property | Value |
|:---|:--:|
| Longitude, $l$ \[deg\] | 0.804 |
| Latitude, $b$ \[deg\] | -0.184 |
| Radius |  |
| …$r_\mathrm{in}$/$r_\mathrm{out}$ \[arcsec\] | 79/154 |
| …$r_\mathrm{in}$/$r_\mathrm{out}$ \[pc\] | 3.1/6.1 |
| …$r_\mathrm{in,d}$ = $r_\mathrm{in}$/cos($i$) \[pc\] | 4.4 |
| …$r_\mathrm{out,d}$ = $r_\mathrm{out}$/cos($i$) \[pc\] | 8.7 |
| Systemic velocity, $v\textsubscript{sys}$ \[km/s\] | 37.5 |
| Expansion speed \[km/s\] |  |
| …$v\textsubscript{exp}$ | 15.1 |
| …$v\textsubscript{exp,d}$ = $v\textsubscript{exp}$/sin($i$) \[km/s\] | 21.3 |
| Age, $t\textsubscript{age}=r_\mathrm{out}/v\textsubscript{exp}$ \[Myr\] | 0.4 |
| Mass \[$\textup{M}_{\odot}$\] |  |
| $^{1}$ …$M$ | 7.6 $\times$ $10^5$ |
| $^{2}$ …$M\textsubscript{d}$ | 1.1 $\times$ $10^6$ |
| $^{3}$ …$M\textsubscript{f}$ | 3.8 $\times$ $10^5$ |
| $^{4}$ …$M\textsubscript{d,f}$ | 5.4 $\times$ $10^5$ |
| Kinetic energy \[erg\] |  |
| …$E = \frac{1}{2} M v\textsubscript{exp}^2$ | $1.7$ $\times$ $10^{51}$ |
| …$E\textsubscript{d} = \frac{1}{2} M\textsubscript{d} v\textsubscript{exp, d}^2$ | $4.8$ $\times$ $10^{51}$ |
| …$E\textsubscript{f} = \frac{1}{2} M\textsubscript{f} v\textsubscript{exp}^2$ | $8.5$ $\times$ $10^{50}$ |
| …$E\textsubscript{d,f} = \frac{1}{2} M\textsubscript{d,f} v\textsubscript{exp, d}^2$ | $2.4$ $\times$ $10^{51}$ |
| Momentum \[$\textup{M}_{\odot}$ km s$^{-1}$\] |  |
| …$p = M v\textsubscript{exp}$ | 1.1 $\times$ $10^7$ |
| …$p\textsubscript{d} = M\textsubscript{d} v\textsubscript{exp, d}$ | 2.3 $\times$ $10^7$ |
| …$p\textsubscript{f} = M\textsubscript{f} v\textsubscript{exp}$ | 5.7 $\times$ $10^7$ |
| …$p\textsubscript{d,f} = M\textsubscript{d,f} v\textsubscript{exp, d}$ | 1.1 $\times$ $10^7$ |
| Magnetic Field, $B_\mathrm{POS}$ \[mG\] | 0.22 $-$ 0.57 |

: Properties of the M0.8$-$0.2 ring.

Table notes: We list properties of the M0.8$-$0.2 ring, obtained in Sects. [3.1](#subsec_morphology), [3.2](#subsec_kinematics), and [3.3](#subsec_mass), as well as the plane-of-sky magnetic field strength measured by (cite: Butterfield2024). A number of different estimates for the radius, expansion velocity, mass, energy and momentum are provided, assuming different possible three-dimensional geometries (see Sect. [3.3](#subsec_mass)). All ‘deprojected’ values, denoted by subscript $d$, use an inclination angle of $i=45\ensuremath{^\circ}$ (where $\sin(45\ensuremath{^\circ})=\cos(45\ensuremath{^\circ})=0.7$) to adjust for an inclined geometry. All mass values are calculated assuming a constant density of $10^{4.2}$ cm$^{-3}$, determined from radiative transfer modelling.

# Observations

The observations primarily used in this work were taken from the Atacama Large Millimeter/submillimeter Array (ALMA) cycle 8 large programme ‘ALMA Central Molecular Zone Exploration Survey’ (ACES, 2021.1.00172.L; Longmore et al. in prep), and represent an initial internal release version of the dataset. The calibration and imaging were conducted with the ALMA pipeline (CASA versions 6.2.1-7 and 6.4.1.12; pipeline versions 2021.2.0.128 and 2022.2.0.64; see (cite: Hunter2023)), with only minor modifications to account for the size mitigation of the data in the ALMA pipeline and fixing divergent cleans.

To include all spatial scales in the final mosaic, we feathered the (primary beam corrected) 7 m Atacama Compact Array (ACA) and total power cubes in CASA (cite: Casa2022), before feathering these cubes to the (primary beam corrected) 12 m array cube. ACES data were imaged onto multiple mosaics, each with a size of $\sim$ 150 pointings, which are then stitched/combined together. In this case, we made use of the four feathered mosaics covering the area of the M0.8$-$0.2 ring, which are combined to a single cube, using appropriate weighting across the mosaic fields to mitigate for the increased noise at the map edges caused by the primary beam response. The complete dataset will be made available to the public with the full description of the data reduction in a later publication (ACES collaboration, in prep.). In the case of the 3 mm continuum, the 12 m array image is feathered to the Green Bank Telescope (GBT) image from MUSTANG Galactic Plane Survey (MGPS90; (cite: Ginsburg2020)), yielding a circular beam size with a full width at half maximum (FWHM) of 2.52$\ensuremath{''}$ and an RMS of $\sim$0.9 mJy beam$^{-1}$.

The ACES dataset comprises six spectral windows in Band 3 (see Table [\[tab:spectral-line-info\]](#tab:spectral-line-info) for extracted lines). There are two narrow windows with high spectral resolution ($\sim$ 0.2 km s$^{-1}$channels) around the HNCO(4–3) transition lines, two intermediate spectral resolution ($\sim$ 1.7 km s$^{-1}$) windows covering H$^{13}$CN(1–0), H$^{13}$CO${+}$(1–0), SiO(2–1), and HN$^{13}$C(1–0), and two broad low spectral resolution ($\sim$ 3 km s$^{-1}$) windows for continuum observations as well as CS(2–1), SO($3_{2}$–$2_{1}$), and HC$_{3}$N(11–10). The working resolution of the HNCO cube is 0.5 km s$^{-1}$, which provides a balance between resolution and sensitivity (we note that in this work, we are studying the large-scale structure of the region, so the full 0.2 km s$^{-1}$  resolution is not required). The data cubes of the other spectral lines were re-gridded to a spectral resolution of 3 km s$^{-1}$, for consistency with the lowest spectral resolution window.

Table [\[tab:spectral-line-info\]](#tab:spectral-line-info) lists the rest frequencies of the studied transitions, as well as the beam sizes and RMS values of their corresponding cubes. The average spatial resolution of the cubes corresponds to a spatial scale of 0.1 pc.

To gain a multi-wavelength view of the M0.8$-$0.2 ring, we used X-ray observations from *Chandra* (cite: Wang2021), 2MASS K-band observations (cite: Skrutskie2006), *Spitzer* 8 $\mu$m (GLIMPSE; (cite: Churchwell2009), also see (cite: Ramirez2008; Anand2021a; Arendt2008b)) and 24 $\mu$m (MIPSGAL; (cite: Carey2009)) observations, *Herschel* 70 to 500 $\mu$m observations (cite: Molinari2010),[^1] Mopra 3 mm observations (cite: Jones2012), and MeerKAT 20 cm observations (cite: Heywood2022).

# Structure of the M0.8$-$0.2 ring

![image](figures/radial-profile.pdf)

![](figures/all_lines.pdf)

## Morphology

We present high angular resolution HNCO (4–3) line emission observations of the M0.8$-$0.2 ring (see Fig. [1](#fig_CMZ_HNCO_peak), upper-left panel). Previous observations of this spectral line with the Mopra telescope (cite: Jones2012) are shown in the lower-left panel of Fig.  [1](#fig_CMZ_HNCO_peak). The more than one order of magnitude increase in linear resolution ($\sim$ 200 finer in area) offered by the ACES observations compared to the Mopra data reveals the complex nature of the structure, with a filamentary, ‘whirlpool-esque’ morphology traced by the peak HNCO emission.

Visually, the majority of the emission from the molecular cloud falls within a ring surrounding a central depression. We used the *Herschel* 250 $\mu$m image ((cite: Molinari2010); see the contours in the top right of Fig. [1](#fig_CMZ_HNCO_peak) and the middle right of Fig.  [6](#fig_multiwavelength)) to define the centre and size of the ring-like structure, rather than the ACES continuum image, due to its higher signal-to-noise detection of the large-scale structure and lack of contamination (i.e. the ACES 3 mm continuum image contains a non-negligible contribution from both free-free and synchrotron emission). We manually determined the centre of the M0.8$-$0.2 ring to be $l=0.^{\circ}804$ and $b=-0.^{\circ}184$, which is consistent with previous definitions (see e.g. (cite: Butterfield2024)). To constrain the inner and outer radii, we used the mean flux radial profile (in steps of one pixel, or 6 $''$) of the *Herschel* 250 $\mu$m emission from the centre of the ring-like structure outwards (see Fig. [2](#fig_herschel_radial)). There is a well-defined peak corresponding to the observed ring of emission, and we defined inner and outer radii where the mean is 50$\%$ of this peak value. This yields $r_\mathrm{in}= 79\ensuremath{''}$ and $r_\mathrm{out}=154\ensuremath{''}$ (Fig. [2](#fig_herschel_radial)), which at the distance of the CMZ (8.2 kpc; (cite: GRAVITYCollaboration2021)) correspond to 3.2 pc and 6.2 pc, respectively. In the absence of prior knowledge regarding the three-dimensional structure of the molecular cloud, we also present ‘deprojected’ values assuming an ellipsoid-like geometry that has one axis elongated in the line-of-sight. We assumed an inclination angle of $i=45^{\circ}$ ($\frac{1}{\mathrm{cos}(i)} \approx 1.4$), resulting in the major axis of the ellipsoid having $r_\mathrm{in,d}=4.4$ pc and $r_\mathrm{out,d}=8.7$ pc.

In Appendix [7](#appendixsec_radprof) we produce mean flux radial profiles of the molecular line emission from the ACES dataset studied in this work (Fig. [9](#fig_all_radial)). We find that the HNCO, HC$_3$N and SO emission profiles are broadly consistent with the continuum definition of the region, but the other lines differ to varying degrees. Figure [3](#fig_alllines) shows the peak intensity for a number of additional lines from the ACES survey in this region. Indeed, the SO emission appears to be most similar to that of HNCO and is concentrated towards the continuum ring, whereas the emission of HC$_{3}$N, CS, SiO, and H$^{13}$CN peaks at larger radii from the centre, possibly tracing denser gas at the edge of the structure (see the critical densities in Table [\[tab:spectral-line-info\]](#tab:spectral-line-info)). It is also interesting to note that the HNCO, HC$_3$N, and SO lines that better trace the ring-like structure are also those with the highest upper energy levels (\>10 K; see Table [\[tab:spectral-line-info\]](#tab:spectral-line-info)).

## Kinematics and expansion

A clear velocity gradient is observed across the M0.8$-$0.2 ring in the intensity-weighted centroid velocity (moment 1) image of the HNCO transition (Fig. [4](#fig_HNCO_spec_moms); upper panel). As highlighted, the blueshifted (lower) velocities towards the north-west (upper-right) end of this structure indicate that here the gas is moving towards us relative to the systemic velocity, whereas the redshifted (higher) velocities towards the south-east (bottom-left) end show the gas to be receding relative to the systemic velocity. The average HNCO spectrum across this region includes a strong broad velocity component, with a FWHM of $\sim$ 30 km s$^{-1}$, around the systemic velocity of 38 km s$^{-1}$ (Fig. [4](#fig_HNCO_spec_moms); lower panel) as well as two additional velocity components at $\sim$ $-$25 km s$^{-1}$ and $\sim$ 100 km s$^{-1}$. To understand whether these additional components are related to the ring-like structure, we located this region in the HNCO position–velocity (PV) plots of (cite: Henshaw2016a). Figure [1](#fig_CMZ_HNCO_peak) (lower-right panel) shows the PV plot of (cite: Henshaw2016a) for the same area of the CMZ as the upper-right panel in the same figure. The M0.8$-$0.2 ring is highlighted with three colours for the three velocity components. The three components are clearly distinct, with the higher velocity component being associated with the material that bridges to the 1.3 degree cloud complex at larger longitudes, and an extension of the turning-point of the orbital model from (cite: Kruijssen2015). Additionally, the HNCO emission from the velocity components at $-$25 and 100 km s$^{-1}$ from the ACES observations do not show any morphological similarity with the HNCO emission of the main component (see the channel maps in Fig. [10](#fig_HNCO_chans)). We thus concluded that these two components represent line-of-sight material unassociated with the M0.8-0.2 ring and hence omitted them from our analysis.

We fitted a single Gaussian profile to the 38 km s$^{-1}$ component present in the HNCO emission (Fig. [4](#fig_HNCO_spec_moms); upper panel) using the PySpecKit package (cite: Ginsburg2011; Ginsburg2022). We determined a centroid velocity ($v\textsubscript{cent}$) of 37.5$\pm$1.7 km s$^{-1}$and a line-width ($v\textsubscript{FWHM}$) of 30.1$\pm$4.0 km s$^{-1}$ (after subtraction of the contribution of the channel width). One interpretation of this velocity profile is that it is the result of the large-scale expansion of the structure (see § [4.3](#subsec_alternatives) for alternative scenarios). Here we interpreted the blueshifted and redshifted material to represent the foreground and background parts of a three-dimensional shell of material, respectively, which along the line-of-sight is observed as a ring of emission. We estimated the expansion velocity to be $v\textsubscript{exp} = (v\textsubscript{FWHM})/2 =$ 15.1 km s$^{-1}$. [^2] We acknowledge that this estimate is a lower limit due to projection effects and calculated an adjusted expansion velocity for an ellipsoidal structure. Again, we conservatively assumed an inclination angle of $i = 45^\circ$, which gives $v\textsubscript{exp, d} \sim 21.3$ km s$^{-1}$.

These estimates of the expansion velocity differ from that reported by (cite: Tsuboi2015). This is due to two factors: 1) (cite: Tsuboi2015) used lower angular resolution ($\sim$ $40$$''$) longitude-velocity ($l-v$) diagrams to analyse the region, rather than fully resolving the position–position–velocity (PPV) structure as in the ACES observations; 2) the observations from the Nobeyama Radio Observatory used by these authors focus on SiO and H$^{13}$CO$^+$, as opposed to HNCO where the M0.8$-$0.2 ring can be seen more clearly (Fig. [6](#fig_multiwavelength)). This resulted in the authors also including the additional higher velocity component (at $\sim$ 100 km s$^{-1}$; see Figs. [4](#fig_HNCO_spec_moms) and [10](#fig_HNCO_chans)), leading to an overestimation of the velocity width of the region and, as such, its expansion speed.

Working on the assumption that the velocity gradient represents expansion, we estimated the age of the M0.8$-$0.2 ring ($t_\mathrm{age} = r_\mathrm{out} / v_\mathrm{exp}$). Assuming the velocity has remained constant throughout the expansion, we calculated $t_\mathrm{age} \sim 0.4$ Myr (note that $t_\mathrm{age} = r_\mathrm{out} / v_\mathrm{exp} = r_\mathrm{out,d} / v_\mathrm{exp,d}$).

![](figures/hnco_spec_mom1.pdf)

## Mass, energy, and momentum

There are multiple mass estimates for the M0.8$-$0.2 ring. For instance, (cite: Mills2017) determined a mass of $2.6 \times 10^5$ M$_\odot$ (see their Fig. 3), employing an iterative cirrus fore/background subtraction technique to *Herschel* data (similar to e.g. (cite: Guzman2015)) to produce a column density of dense gas (Battersby et al. in prep).[^3] (cite: Tsuboi2015) estimated a mass of $2.7 \times 10^3$ M$_\odot$ from radiative transfer modelling of CS (1–0) emission (although the exact geometry assumed to convert the derived density to mass in this calculation is not clear). Given the significant discrepancy between these previous mass estimates, we performed a revised calculation based on the new HNCO (4–3) emission from ACES using the one-dimensional non-local thermodynamic equilibrium radiative transfer code Radex (see Fig. [5](#fig_HNCO_radex); (cite: vanderTak2007)).

We made use of the SpectralRadex python package implementation of Radex (cite: Holdship2021) to explore a grid of models by varying the following parameters: The kinetic temperature ($T_\mathrm{kin}$) ranged from 30 to 150 K with a step size of 10 K. The number density of molecular hydrogen ($n_\mathrm{H_2}$) spanned $10^2$ to $10^8$ cm$^{-3}$ with a step size of 0.05 dex. The line-width values considered were 5, 10, and 20 km s$^{-1}$.[^4] The abundance of HNCO ($X_\mathrm{HNCO}$) was varied from $10^{-10}$ to $10^{-6}$ with a step size of 0.05 dex. We assumed a fixed molecular hydrogen column density ($N_\mathrm{H_2}$) of $8.5 \times 10^{22}$ cm$^{-2}$ (i.e. to convert the HNCO abundance to column density), which represents an average measured value from *Herschel* column density observations across the M0.8-0.2 ring. We note here the consistency of our assumed ranges with the values derived over a single IRAM 30 m pointing on the ring-like structure of $N_\mathrm{H_2}$ $\approx$ $7 \times 10^{22}$ cm$^{-2}$ and $\log(X_\mathrm{HNCO}) \approx -8$, estimated using a multi-transition analysis ((cite: Martin2008); note that here we can only make use of a single transition of HNCO covered by the ACES survey).

The results from the grid of models, as illustrated in Fig. [5](#fig_HNCO_radex), depict the frequency with which the models produce brightness temperatures within the observed range of 1 to 5 K for the M0.8$-$0.2 ring (see the upper-left panel of Fig. [3](#fig_alllines)). Figure [5](#fig_HNCO_radex) indicates that the inferred abundance of HNCO remains approximately constant (within the 90 per cent likelihood contour) at $\log(X_\mathrm{HNCO}) \approx -8.5$ above a number density of around $10^4$ cm$^{-3}$. Below this density (close to the critical density of emission for HNCO, 2.1 $\times$ $10^4$ cm$^{-3}$; see Table [\[tab:spectral-line-info\]](#tab:spectral-line-info)), the abundance must increase to reproduce the observed brightness of HNCO emission.

In Fig. [5](#fig_HNCO_radex) we also show the predicted depth ($L = N_{\mathrm{H2}}/n_{\mathrm{H2}}$) calculated from the observed column density and the model number density. Bounds on the depth are imposed, assuming that the structure should not be much deeper than its projected size ($\sim 10$ pc) and should not be smaller than the angular resolution of our observations ($\sim 0.1$ pc). The analysis yields a peak likelihood of $n_{\mathrm{H2}} \approx 10^{4.2}$ cm$^{-3}$,[^5] with a spread in plausible densities ranging from $10^{3.5}$ to $10^{5.5}$ cm$^{-3}$. A simple check of this value can be done by comparing our HNCO-derived density with what we get if we divide the mean H$_2$ column density by twice the shell width (assuming we have observed both the front and back sides). For a width of 1 pc and $N_{\mathrm{H2}} = 8.5 \times 10^{22}$ cm$^{-2}$, this gives a density $n_{\mathrm{H2}} \approx 10^{4.1}$ cm$^{-3}$, which is consistent with our value.

We estimated the mass of the M0.8$-$0.2 ring given various possible three-dimensional geometries. Taking a constant density of $10^{4.2}$ cm$^{-3}$, and assuming a complete spherical shell geometry with inner and outer radii of 3.1 pc and 6.1 pc (i.e. with a volume of $v_\mathrm{out}-v_\mathrm{in}= 4/3 \pi (r_\mathrm{out}^3 - r_\mathrm{in}^3))$, we calculated a total mass of $M$ = 7.5 $\times$ 10$^{5}$ M$_\odot$. Assuming a complete ellipsoidal shell geometry again inclined at $45^\circ$, with one axis elongated in the line-of-sight and the other two as observed (i.e. with a volume of $v_\mathrm{out}-v_\mathrm{in}= 4/3 \pi (r_\mathrm{out}^2 r_\mathrm{out,d} - r_\mathrm{in}^2 r_\mathrm{in,d}))$, we calculated a mass of $M\textsubscript{d}$ = 1.1 $\times$ 10$^{6}$ M$_\odot$. Assuming instead a clumpy or partial shell with a filling factor of a half (i.e. $f=0.5$) decreases both of these mass estimates by a factor of 2. Our best estimate of the mass is given by adjusting both the inclination and filling factor, yielding $M\textsubscript{d,f}$ = 5.4 $\times$ 10$^{5}$ M$_\odot$. These estimates are in agreement with the mass determined from the *Herschel*-derived H$_2$ column density map (cite: Mills2017), but a factor of 200 higher than the value of (cite: Tsuboi2015).

Using our most realistic mass estimate of a partial, inclined ellipsoidal shell ($M\textsubscript{d,f}$) and taking the inclination-corrected expansion speed ($v\textsubscript{exp,d}$) of the M0.8$-$0.2 ring, we calculated its kinetic energy ($E\textsubscript{d,f} = 0.5 M\textsubscript{d,f} v\textsubscript{exp,d}^2$) and momentum ($p\textsubscript{d,f} = M\textsubscript{d,f} v\textsubscript{exp,d}$). We find $E\textsubscript{d,f} = 2.4$ $\times$ $10^{51}$ erg and $p\textsubscript{d,f} = 1.1$ $\times$ $10^7$ $\textup{M}_{\odot}$ km s$^{-1}$(see Table [1](#tab:bubble_sum) for a summary of all mass, energy and momentum estimates).

![](figures/hnco_radex_grid_labels.pdf)

## Multi-wavelength view

An extensive multi-wavelength analysis of the region has been performed by (cite: Butterfield2024), and here we provide a brief overview of their findings (see Fig. [6](#fig_multiwavelength)). There are two X-ray point sources located, in projection, at the centre of the M0.8$-$0.2 ring and one on the southern edge, but no widespread X-ray emission has been detected. Two infrared point sources, present in 8 and 24 $\mu$m *Spitzer* observations, similarly appear to be located within the ring-like structure (cite: Butterfield2024). Following up on this, we checked the infrared data from the VISTA Variables in the Via Lactea (VVV) survey (cite: Minniti2010) and found no overdensity of stars at these locations, or elsewhere within the M0.8$-$0.2 ring, though this does not discount young stars being present in the region (as in Sgr B1 and C, (cite: Nogueras-Lara2022; Nogueras-Lara2024)). Additionally, if there is a cluster present, extinction may be too high to identify it (cite: Henshaw2022). Indeed, the infrared observations at 8 and 24 $\mu$m reveal an infrared dark (i.e. extinction) feature along the eastern to southern arc of the ring-like structure that coincides with the strongest dust continuum emission at 250 $\mu$m and 3 mm. This arc also shows strong radio emission in the MeerKAT observations at 20 cm (cite: Heywood2019; Heywood2022). The infrared and MeerKAT observations reveal a point source on the eastern inner edge of the ring, which is believed to be a compact H ii region (discussed further in Sect. [4.1](#subsec_youngfeedback)). The M0.8$-$0.2 ring is also well traced by dust polarisation vectors from the FIREPLACE polarimetry survey ((cite: Butterfield2023; Pare2024)), indicating a clear connection between the magnetic field and the ring-like structure, as explored in detail in (cite: Butterfield2024).

![](figures/multiwave_all_max_labels_updated_v4.pdf)

# Cause of the M0.8$-$0.2 ring

We next explored possible explanations for the morphology and velocity profile of the M0.8$-$0.2 ring, taking into consideration the energy and momentum estimates (Sect. [3.3](#subsec_mass)), along with a range of multi-wavelength ancillary observations (Sect. [3.4](#subsec_multiwave)). Stellar feedback, both from young stars and SNe, as well as alternative explanations, such as cloud–cloud collisions and large-scale dynamics, were considered.

## Feedback from young high-mass star(s)

Young high-mass stars are known to inject a large amount of energy and momentum into their surroundings (e.g. (cite: Krumholz2014; Rosen2020)), which can lead to the expansion of bubbles of material (e.g. (cite: Barnes2022; Henshaw2022)). In this context, of interest is a 3 mm point source located at $l=0.^{\circ}8244$, $b=-0.^{\circ}1903$ (marked with a cyan circle in Fig. [6](#fig_multiwavelength)). (cite: Butterfield2024) show that this source is present in observations ranging from the near-infrared to cm wavelengths. Observations from MeerKAT at $\sim$20 cm (cite: Heywood2022; Yusef-Zadeh2022) show that the spectral index of the source is approximately +0.7 (see Fig. [6](#fig_multiwavelength)), suggesting the origin of the source is free-free emission from ionised gas, most likely from a compact H ii region. The fact that this source is also seen in the infrared is also suggestive that this emission is free-free in nature, as opposed to a synchrotron source. In addition, we find a point source in H40$\alpha$ emission towards this location (see Figs. [6](#fig_multiwavelength) and [7](#fig_H40a_spectrum)), which confirms the identification of this source as a compact H ii region. However, we find that the ACES H40$\alpha$ spectrum peaks at $\sim$100 km s$^{-1}$, which differs significantly from the molecular gas associated with the M0.8$-$0.2 ring at this position ($\sim$50 km s$^{-1}$). Rather, the velocity of the H40$\alpha$ emission is consistent with the higher velocity component seen at around 100 km s$^{-1}$ in the average spectrum of HNCO (see Fig. [1](#fig_CMZ_HNCO_peak)), which is morphologically different and does not seem to be associated with the ring-like structure (see Fig. [10](#fig_HNCO_chans)).

We further ruled out this source as the progenitor of the M0.8$-$0.2 ring based on mass. To calculate its mass, we first calculated the Lyman continuum ionising flux using the following, as set out by (cite: Schmiedeke2016):

$$\begin{equation}
N\textsubscript{LyC} = 4.771 \times 10^{42} \left[\dfrac{S_{v}}{\textrm{Jy}}\right] \left[\dfrac{{v}}{\textrm{GHz}}\right]^{0.1}  \left[\dfrac{T\textsubscript{e}}{\textrm{K}}\right]^{-0.45} \left[\dfrac{d}{\textrm{pc}}\right]^2 \text{s}^{-1}, 
\end{equation}$$ where $S_v$ is the integrated flux density of the source, measured in the 12 m-only continuum map to be 36 mJy, with a central frequency, $v$, of 98.6 GHz, $T_\textsubscript{e}$ is the electron temperature, assumed to be 5000 K (typical for Galactic Centre H ii regions; e.g. (cite: Mehringer1992)), and $d$ is the distance to the Galactic Centre of 8.2 kpc (cite: GRAVITYCollaboration2021). Inputting these values, we obtained an ionising Lyman continuum flux of $\log_{10}$(N~LyC~/s$^{-1}$) $\approx$ 47.6. This value is consistent with a late O- or early B-type zero-age main-sequence star (spectral type O9V/B0V; (cite: Panagia1973; Smith2002)) with a mass of $\sim$ 20 $\textup{M}_{\odot}$ ((cite: Nieva2014)). Despite being massive, this single star is not able to drive the expansion of such a massive (10$^{5-6}$ M$_\odot$) bubble over such a short timescale ($\sim$0.4 Myr). For example, such a star produces $\approx$ $10^{4}$ L$_{\odot}$ $\times$ 0.4 Myr $\approx$ 5$\times$10$^{50}$  erg of energy over the lifetime of the M0.8$-$0.2 ring: an insufficient amount given the energy estimate of the structure (see Sect. [3.3](#subsec_mass)). Assuming a conservative coupling efficiency of 10$\%$ and an escape fraction of 50$\%$ (i.e. equal to the filling factor of the ring-like structure), $\sim$ 500 similar O9/B0 stars are needed to power the expansion of the structure (i.e. to achieve $E\textsubscript{d,f}$). If this were the case, and a significant fraction of the ionising radiation was escaping from the region, we would expect to see some influence on the ionisation state of the gas surrounding the M0.8$-$0.2 ring. Such a feature may not be visible in the infrared due to high extinction, but would be observed clearly as free-free emission in the radio (e.g. as in the case of Sgr B1; (cite: Barnes2020b)).

![](figures/hnco_ha_max_spec_lables.pdf)

![](figures/PPV-HNCO.pdf)

## Feedback from supernova(e)

Alternatively, the M0.8$-$0.2 ring may be the result of SN feedback (cite: Pierce-Price2000; Tsuboi2015). Indeed, there is an arc of extended, diffuse (20 cm) radio emission that traces the south-east (lower left) of the ring-like structure (see Fig. [6](#fig_multiwavelength)). In contrast to the radio point source (Sect. [4.1](#subsec_youngfeedback)), the associated spectral indices of this extended radio continuum emission are negative, ranging from -0.4 to -1.7 moving south along the emission (Fig. [6](#fig_multiwavelength)). Such values point towards the emission being synchrotron emission, as is commonly observed towards SNRs (see (cite: Anderson2017; Heywood2022)).[^6] Making use of *Chandra* observations, we find no extended X-ray emission associated with the M0.8$-$0.2 ring (Fig. [6](#fig_multiwavelength)). The lack of X-ray emission, frequently observed towards young SNRs as a result of shock-heated plasma ((cite: Vink2017)), and low radio brightness of the source are in line with an evolved SNR. The large amount of swept-up mass, typical of SNRs in the later ‘radiative’ or ‘snowplough’ phase ((cite: Vink2012)), and the observed orientation of the magnetic field, explored by (cite: Butterfield2024), are also consistent with an older SNR. Typically, young SNRs have radial magnetic fields, whereas more evolved remnants display magnetic fields tangential to the shock front (cite: Dubner2015), as observed here (see Fig. [6](#fig_multiwavelength)). Given the non-linear expansion of an SNR over time, with an initial rapid expansion followed by a slow increase in radius as it enters the later stages of its evolution, our initial estimate of the age of the structure ($t = r/v = 0.4$ Myr) will be a factor of a few too large.

We next compared the kinetic energy of the M0.8$-$0.2 ring to that of a typical SNR. A single SN event is thought to inject $\sim$ $10^{51}$ erg of baryonic energy into the ISM ((cite: Bethe1990; Thornton1998; Kim2015a)). A significant amount of this energy is converted into radiative energy over time, with typical coupling efficiencies (i.e. the percentage of kinetic energy retained by the surrounding medium and not radiated away) varying from a few to a few tens of per cent (e.g. (cite: Thornton1998; Tamburro2009; Sharma2014; Kim2015a; Martizzi2015; Gentry2017)). The total energy available to drive large-scale motions of the ISM from a single SN is therefore $\sim10^{49}-10^{50}$ erg. Making comparison to our most realistic estimate for the kinetic energy of the M0.8$-$0.2 ring ($\sim$ 2.4 $\times$$10^{51}$ erg; see Sect. [3](#sec_structure)), a coupling efficiency of $>100\%$ is required for a single SN to be the driving force behind the expansion of the structure. If late-stage stellar feedback is indeed behind the ring-like structure, there are two solutions to this unphysical coupling efficiency: multiple SNe acting in concert, or a single abnormally luminous event (i.e. a hypernova).

Multiple, clustered SNe could provide an explanation as to the very high kinetic energy and momentum of the M0.8$-$0.2 ring. To derive an approximate minimum number of SNe required to power the expansion of the structure, we assumed a generous coupling efficiency of 30$\%$ and an injected energy of $10^{51}$ erg. Assuming the impact of multiple SNe is additive, and using the estimated kinetic energy of the M0.8$-$0.2 ring of $\sim$ 2.4 $\times$$10^{51}$ erg, we find eight SNe are required. We note that the effect of subsequent SN explosions is not well understood, and clustering of SNe, both temporally and spatially, may have a large impact on the energy and momentum injected per SN (see (cite: Krumholz2019a) for a full discussion). Despite this, we can conclude that many concentrated SNe would have to have occurred within a relatively small (around 10 pc) region. However, the strong gravitational shear within the Galactic Centre will disperse a stellar cluster as it evolves on a relatively short timescale, thus making numerous spatially coincident SNe unlikely unless a cluster is tightly bound. Infrared and radio observations of the region reveal no such massive stellar cluster, nor distribution of diffuse stars, from which multiple SN progenitors may have originated, and thus we deem this explanation implausible.

An alternative explanation is that the M0.8$-$0.2 ring is the remnant of a hypernova explosion. A hypernova is defined as an event where the initial injected energy is greater than the canonical $10^{51}$ erg for a SN (cite: Paczynski1988). Hypernovae have been proposed to explain the similarly energetic young remnant NGC 5471B in M101 and the synchrotron superbubble in IC10 (cite: Wang1999; Chen2002; Lozinskaya2007), as well as the Cygnus superbubble (cite: Kimura2013; Bluem2020). It is important to note, however, the discrepancy in scale when making such comparisons, with NGC 5471B, the IC10 superbubble, and the Cygnus superbubble having significantly larger diameters of approximately 70, 250, and 450 pc, respectively (cite: Chen2002; Lozinskaya2007; Kimura2013). This discrepancy may arise due to the high gas densities and pressures in the CMZ, serving to constrain the size of the M0.8$-$0.2 ring and resulting in the highly energetic remnant remaining compact. Given the lack of an observed massive stellar cluster in the immediate vicinity, the progenitor may have been a runaway star of very high mass from a nearby cluster. The striations visible in the channel maps, with filaments extending from the top and bottom of the ring-like structure towards the Galactic west, suggest that the explosion’s source might have been a runaway star originating near Sgr B1. The cavity’s axis, as seen in the MeerKAT image, aligns with motion towards the Galactic east. Additionally, the increased brightness of non-thermal emission and dust towards the Galactic east supports the idea that the star’s winds and ionising radiation created a tunnel extending from Sgr B1 in the direction of the Galactic east before the explosion.

We also checked for consistency with the typical relationship held by SNRs between radio surface brightness and size ($\Sigma-r$; see e.g. (cite: Case1998)). For a mean radio brightness over the region of $\sim\,0.1$ mJy/beam, measured from the MeerKAT observations at 1.28 GHz with a beam size of 4$''$, the surface brightness at 1 GHz for a spectral index of around $-1$ is $\Sigma_\mathrm{1 GHz}\approx 3\times10^{-21}$ W Hz$^{-1}$ m$^{-2}$ sr$^{-1}$. Using the $\Sigma_\mathrm{1 GHz} \propto r^{-2.64}$ relation from (cite: Case1998), a radius of $r \sim 20$ pc is predicted for such a surface brightness. This is inconsistent with our calculation of the radius of the M0.8$-$0.2 ring of $\sim6$ pc, assuming the region is within the Galactic Centre (i.e. at $\sim$ 8 kpc). The deviation from the typical $\Sigma-r$ relation may again originate due to the unique nature of the CMZ and the environment the SN explosion occurred in. SNRs found within dense molecular clouds (so-called ‘dark’ or ‘buried’ SNRs; see (cite: Sofue2020; Sofue2021; Sofue2024)) have been proposed to obey a different $\Sigma-r$ relation from the typical SNRs located in the inter-cloud ISM. This effect may then be compounded by the order of magnitude higher densities and pressures within the Galactic Centre, resulting in a remnant of unusually compact nature.

## Possible alternatives to stellar feedback?

As stellar feedback does not provide a definitive answer for the cause of the M0.8$-$0.2 ring, we next considered possible alternative explanations.

### Cloud–cloud collisions

An alternative scenario responsible for the formation of the M0.8$-$0.2 ring could involve cloud–cloud collisions. The CMZ harbours a high density of massive molecular clouds, and given the highly dynamic nature of the region, numerous interactions are anticipated. Observable signatures of these collisions, often subject to debate, have been identified in several well-known molecular clouds within the CMZ (e.g. (cite: Higuchi2014; Johnston2014; Tsuboi2015b; Armijos-Abendano2020)). Common arguments involve the presence of shocked gas tracers such as HNCO, SiO, and SO, which indeed all exhibit widespread distribution across the region. Additional indicators of cloud–cloud collisions include kinematic features, such as the widely discussed broad bridge features (cite: Haworth2015). However, inspecting various PV cuts across the region (Fig. [8](#fig_pv-cuts)) revealed no clear examples of distinct bridge features. It is important to note though that the absence of such features in our study does not necessarily negate their presence, and a comprehensive kinematic analysis of the region is planned for future work.

That said, the hole-like structure is intriguing in this context. A possible scenario could be that during the collision of the two clouds, more compact cloud punched a hole through the centre of the other, resulting in the ring-like structure that we now observe. A similar scenario has been presented to explain the kinematic structure observed in Sgr B2 (e.g. (cite: Hasegawa1994; Sato2000)).

The location of the region is particularly favourable for a collisional scenario. Firstly, it is close to the point where we expect gas to be flowing along the bar and into the Galactic Centre around this longitude (at around the 1.3 degree cloud; see (cite: Henshaw2023)). Interactions between this inflowing gas and pre-existing gas within the CMZ are commonly seen in simulations (see e.g. (cite: Tress2020a; Sormani2020; Hatchfield2021)), potentially resulting in high density and highly shocked molecular clouds, akin to our observations. It is also close to the apocentre of the CMZ orbit, which could lead to a build-up of material - similar to a traffic jam - and thus to cloud–cloud collisions on the orbit, or with clouds in the inflow from the bar. The velocity gradient across the M0.8$-$0.2 ring would be in agreement with this scenario; having the highly redshifted velocities on the left side where gas is infalling towards the CMZ along dust-lanes that are oriented away from us (see the geometry presented in (cite: Henshaw2023)). That said, it is noteworthy that the systemic velocity of the ring is notably lower (at $\sim$ 35 km s$^{-1}$) than expected for regions in this location to be interacting with the inflowing gas stream (at $\sim$ 100 km s$^{-1}$). The exact location of the inflowing material also remains a subject of significant debate in the literature.

### Shear and large-scale processes

Gravitational shear may also play a role in the formation of the observed structure. Shear forces due to the rapid rotation around the Galactic Centre are expected to be very strong within the CMZ and play a key role in its evolution (e.g. (cite: Longmore2013b)). The projected galactocentric distance of the centre of the M0.8$-$0.2 ring is $\sim$ 120 pc (not accounting for the three-dimensional location). At this galactocentric radius ($r_\mathrm{gal}$), there is a steep increase in the rotation curve of the galaxy from 100 to 200 km s$^{-1}$ (e.g. (cite: Launhardt2002)), and the dimensionless rate of shear depends sensitively on its derivative as $1 - \beta = 1 - \mathrm{d ln} (v_\phi) / \mathrm{d ln} (r)$ (e.g. (cite: Krumholz2015)). Strong shear forces could then be acting to stretch and enlarge the structure. The combination of shear and feedback may be a potential solution to the energy problem presented in Sect. [4.2](#subsec_supernova). We could foresee a scenario whereby a SN initially seeds the expansion of the molecular cloud, which is then (azimuthally) enlarged by shear as it evolves. This would also explain the origin of the non-thermal emission towards the region, and could provide a reason for our assumed line-of-sight elongation of the structure. However, this then raises the question as to whether the calculated age of the M0.8$-$0.2 ring is sufficient for the shear forces to have a significant effect. Moreover, it is also worth mentioning that the velocity gradient that we observe is in the opposite direction to that of, for example, the Brick, and also in the opposite direction of that of cloud-scale simulations that include the shear (e.g. (cite: Kruijssen2019a)).

An alternative point worth mentioning is that the shear and large-scale cyclical effects within the CMZ could also impart angular momentum on a molecular cloud (e.g. (cite: Federrath2016)). The observed kinematics could then be interpreted as rotation, producing the smooth velocity gradient across the region of $\Delta v \approx 3$ km s$^{-1}$ pc$^{-1}$. Indeed, the region is reminiscent of a large-scale vortex or eddy-like structure (Fig. [1](#fig_CMZ_HNCO_peak)). The cause of such a structure, and reason as to why this is seen within the plane of the sky (as opposed to in the plane of the disk), is not clear, but the location of this region towards the outer edge of the CMZ, and close to the inflowing material along the dust lanes may not be coincidental. Indeed, there may be some connection here to material that is inflowing but overshooting the Galactic Centre (cite: Hatchfield2021), where the viscous interaction of the rapid inflowing gas grazing the CMZ produces strongly rotating clouds. However, since the exact location of these contact points remains unclear, this scenario is still open to interpretation.

### Line-of-sight coincidence

Lastly, the most simplistic argument may be that the structures that we identify as the M0.8$-$0.2 ring are in fact a chance alignment of associated velocity components along the line-of-sight. The three-dimensional spatial structure of the Galactic Centre, and how that relates to the structure of molecular lines in velocity space (i.e. position-position-position vs position-position-velocity), is indeed a subject of much current debate (e.g. (cite: Henshaw2023; Hu2023)). That said, the structure does appear to be coherent spatially and in velocity across a number of molecular lines (see the channel maps for HNCO, HC$_{3}$N, SO, and SiO in Figs. [10](#fig_HNCO_chans) - [13](#fig_SiO_chans)). Moreover, (cite: Butterfield2024) identified this structure as coherent in polarisation using the SOFIA/HAWC+ data from the FIREPLACE survey (cite: Butterfield2023; Pare2024), with the polarisation vectors clearly tracing the ACES HNCO emission, as displayed in Fig. [6](#fig_multiwavelength). Therefore, it seems highly unlikely that this large-scale ring-like structure is misidentified.

# Conclusions

We have studied a complex, massive molecular structure in the CMZ using data from the ALMA large programme ACES. We find that the M0.8$-$0.2 ring has a very striking appearance in the new high-spatial dynamic range observations of the HNCO(4$-$3) line, which serves as a tracer of shocked, dense gas. The structure appears to be coherent in its kinematics across a size-scale of $\sim$ 10 pc, and radiative transfer modelling of the HNCO emission produces a mass estimate of around $10^6$ M$_\odot$. For context, this is equivalent to some of the most massive and densest star-forming molecular clouds within the Galactic Centre. Previous lower-resolution observations identified this cloud as an expanding ring-like structure (e.g. (cite: Pierce-Price2000; Tsuboi2015)) originating due to stellar feedback. We investigated this, and reached the following conclusions.

1.  We argue against the possibility of the M0.8$-$0.2 ring being the result of early-stage stellar feedback. A compact radio point source is observed in the ACES H40$\alpha$ line; however, the source has an inconsistent velocity with the ring-like structure and is deemed to be unassociated. While there remains the possibility that there is a population of highly extincted and/or diffuse stars driving the expansion that we are currently unable to detect, this seems unlikely given the lack of evidence in radio observations.

2.  Supernova feedback could be a viable cause, and would provide an explanation for the non-thermal radio emission observed towards the region. If the M0.8$-$0.2 ring is indeed an SNR, it is certainly atypical, being highly energetic and yet unusually compact for an SNR of its radio brightness. The high kinetic energy of the structure could be explained by multiple, clustered SN explosions; however, no massive stellar cluster from which numerous SN progenitors could have originated is observed, and shear makes several explosions within a concentrated volume unlikely. A particularly energetic hypernova could also provide enough energy to power the structure, and if such an explosion occurred within a very dense molecular cloud, this could explain the morphology and kinematics of the region.

3.  For completeness, we have discussed a number of alternative scenarios for the formation of the observed structure, such as cloud–cloud collisions, shear, and large-scale processes. None of these scenarios provide a clean explanation for the structure, but we suggest promising avenues for future studies of this intriguing region.

# Acknowledgements

We are grateful to the anonymous referee for their constructive and detailed suggestions, which helped significantly improve the quality of this paper.

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2021.1.00172.L ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This project made use of the Astropy, APLpy, PySpecKit, SpectralRadex python packages (cite: astropy:2013; astropy:2018; astropy:2022; Robitaille2012; Ginsburg2011; Ginsburg2022; Holdship2021).

L.C., I.J-S., and V.M.R. acknowledge funding from grants No. PID2019-105552RB-C41 and PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. V.M.R. also acknowledges support from the grant number RYC2020-029387-I funded by MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", and from the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC). A.S.-M. acknowledges support from the RyC2021-032892-I grant funded by MCIN/AEI/10.13039/501100011033 and by the European Union ‘Next GenerationEU’/PRTR, as well as the program Unidad de Excelencia María de Maeztu CEX2020-001058-M, and support from the PID2020-117710GB-I00 (MCI-AEI-FEDER, UE). AG and MGSM acknowledge support from the NSF under grants AAG 2008101, 2206511, and CAREER 2142300. FHL acknowledges support from the ESO Studentship Programme. JDH gratefully acknowledges financial support from the Royal Society (University Research Fellowship; URF/R1/221620). MCS acknowledges financial support from the European Research Council under the ERC Starting Grant “GalFlow” (grant 101116226). JEP was supported by the Max-Planck Society.

CB gratefully acknowledges funding from National Science Foundation under Award Nos. 2108938, 2206510, and CAREER 2145689, as well as from the National Aeronautics and Space Administration through the Astrophysics Data Analysis Program under Award “3-D MC: Mapping Circumnuclear Molecular Clouds from X-ray to Radio,” Grant No. 80NSSC22K1125.

MN and FWX acknowledge funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 (ORP).

J.M.D.K. gratefully acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme via the ERC Starting Grant MUSTANG (grant agreement number 714907). COOL Research DAO is a Decentralised Autonomous Organisation supporting research in astrophysics aimed at uncovering our cosmic origins. E.A.C.M. gratefully acknowledges funding from the National Science Foundation under Award No. 2206509. J.W. gratefully acknowledges funding from National Science Foundation under Award Nos. 2108938 and 2206510.

104 natexlab

(ref: Anand2021a) Anand, G. S., Rizzi, L., Tully, R. B., et al. 2021, AJ, 162, 80

(ref: Anderson2017) Anderson, L. D., Wang, Y., Bihr, S., et al. 2017, A&A, 605, A58

(ref: Arendt2008b) Arendt, R. G., Gezari, D. Y., Stolovy, S. R., et al. 2008, ApJ, 685, 958

(ref: Armijos-Abendano2020) Armijos-Abendaño, J., Banda-Barragán, W. E., Martı́n-Pintado, J., et al. 2020, MNRAS, 499, 4918

(ref: astropy:2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: astropy:2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Barnes2022) Barnes, A. T., Chandar, R., Kreckel, K., et al. 2022, A&A, 662, L6

(ref: Barnes2020a) Barnes, A. T., Kauffmann, J., Bigiel, F., et al. 2020a, MNRAS, 497, 1972

(ref: Barnes2019) Barnes, A. T., Longmore, S. N., Avison, A., et al. 2019, MNRAS, 486, 283

(ref: Barnes2020b) Barnes, A. T., Longmore, S. N., Dale, J. E., et al. 2020b, MNRAS, 498, 4906

(ref: Bethe1990) Bethe, H. A. 1990, Reviews of Modern Physics, 62, 801

(ref: Bluem2020) Bluem, J., Kaaret, P., Fuelberth, W., et al. 2020, ApJ, 905, 91

(ref: Bryant2021) Bryant, A. & Krabbe, A. 2021, New A Rev., 93, 101630

(ref: Butterfield2023) Butterfield, N. O., Chuss, D. T., Guerra, J. A., et al. 2024a, ApJ, 963, 130

(ref: Butterfield2024) Butterfield, N. O., Guerra, J. A., Chuss, D. T., et al. 2024b, ApJ, 968, 63

(ref: Carey2009) Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, PASP, 121, 76

(ref: Casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Case1998) Case, G. L. & Bhattacharya, D. 1998, ApJ, 504, 761

(ref: Chen2002) Chen, C. H. R., Chu, Y.-H., Gruendl, R., Lai, S.-P., & Wang, Q. D. 2002, AJ, 123, 2462

(ref: Churchwell2009) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213

(ref: Clark2018) Clark, J. S., Lohr, M. E., Najarro, F., Dong, H., & Martins, F. 2018, A&A, 617, A65

(ref: Dubner2015) Dubner, G. & Giacani, E. 2015, A&ARv, 23, 3

(ref: Federrath2016) Federrath, C., Rathborne, J. M., Longmore, S. N., et al. 2016, ApJ, 832, 143

(ref: Gentry2017) Gentry, E. S., Krumholz, M. R., Dekel, A., & Madau, P. 2017, MNRAS, 465, 2471

(ref: Ginsburg2020) Ginsburg, A., Anderson, L. D., Dicker, S., et al. 2020, ApJS, 248, 24

(ref: Ginsburg2011) Ginsburg, A. & Mirocha, J. 2011, PySpecKit: Python Spectroscopic Toolkit, Astrophysics Source Code Library, record ascl:1109.001

(ref: Ginsburg2022) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022, AJ, 163, 291

(ref: Gramze2023) Gramze, S. R., Ginsburg, A., Meier, D. S., et al. 2023, ApJ, 959, 93

(ref: GRAVITYCollaboration2018) GRAVITY Collaboration, Abuter, R., Amorim, A., et al. 2018, A&A, 615, L15

(ref: GRAVITYCollaboration2019) GRAVITY Collaboration, Abuter, R., Amorim, A., et al. 2019, A&A, 625, L10

(ref: GRAVITYCollaboration2021) GRAVITY Collaboration, Abuter, R., Amorim, A., et al. 2021, A&A, 647, A59

(ref: Guzman2015) Guzmán, A. E., Sanhueza, P., Contreras, Y., et al. 2015, ApJ, 815, 130

(ref: Hasegawa1994) Hasegawa, T., Sato, F., Whiteoak, J. B., & Miyawaki, R. 1994, ApJL, 429, L77

(ref: Hatchfield2021) Hatchfield, H. P., Sormani, M. C., Tress, R. G., et al. 2021, ApJ, 922, 79

(ref: Haworth2015) Haworth, T. J., Tasker, E. J., Fukui, Y., et al. 2015, MNRAS, 450, 10

(ref: Henshaw2023) Henshaw, J. D., Barnes, A. T., Battersby, C., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 83

(ref: Henshaw2022) Henshaw, J. D., Krumholz, M. R., Butterfield, N. O., et al. 2022, MNRAS, 509, 4758

(ref: Henshaw2016a) Henshaw, J. D., Longmore, S. N., & Kruijssen, J. M. D. 2016, MNRAS, 463, L122

(ref: Heywood2019) Heywood, I., Camilo, F., Cotton, W. D., et al. 2019, Nature, 573, 235

(ref: Heywood2022) Heywood, I., Rammala, I., Camilo, F., et al. 2022, ApJ, 925, 165

(ref: Higuchi2014) Higuchi, A. E., Chibueze, J. O., Habe, A., Takahira, K., & Takano, S. 2014, AJ, 147, 141

(ref: Holdship2021) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55

(ref: Holland1999) Holland, W. S., Robson, E. I., Gear, W. K., et al. 1999, MNRAS, 303, 659

(ref: Hu2023) Hu, Y., Lazarian, A., Alina, D., Pogosyan, D., & Ho, K. W. 2023, MNRAS, 524, 2994

(ref: Hunter2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, PASP, 135, 074501

(ref: Johnston2014) Johnston, K. G., Beuther, H., Linz, H., et al. 2014, A&A, 568, A56

(ref: Jones2012) Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2012, MNRAS, 419, 2961

(ref: Jones2013) Jones, P. A., Burton, M. G., Cunningham, M. R., Tothill, N. F. H., & Walsh, A. J. 2013, MNRAS, 433, 221

(ref: Kim2015a) Kim, C.-G. & Ostriker, E. C. 2015, ApJ, 802, 99

(ref: Kimura2013) Kimura, M., Tsunemi, H., Tomida, H., et al. 2013, PASJ, 65, 14

(ref: Kruijssen2015) Kruijssen, J. M. D., Dale, J. E., & Longmore, S. N. 2015, MNRAS, 447, 1059

(ref: Kruijssen2019a) Kruijssen, J. M. D., Dale, J. E., Longmore, S. N., et al. 2019, MNRAS, 484, 5734

(ref: Kruijssen2013) Kruijssen, J. M. D. & Longmore, S. N. 2013, MNRAS, 435, 2598

(ref: Krumholz2014) Krumholz, M. R., Bate, M. R., Arce, H. G., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 243–266

(ref: Krumholz2019a) Krumholz, M. R. & Federrath, C. 2019, Frontiers in Astronomy and Space Sciences, 6, 7

(ref: Krumholz2015) Krumholz, M. R. & Kruijssen, J. M. D. 2015, MNRAS, 453, 739

(ref: Launhardt2002) Launhardt, R., Zylka, R., & Mezger, P. G. 2002, A&A, 384, 112

(ref: Law2008) Law, C. J., Yusef-Zadeh, F., Cotton, W. D., & Maddalena, R. J. 2008, ApJS, 177, 255

(ref: Longmore2013b) Longmore, S. N., Kruijssen, J. M. D., Bally, J., et al. 2013, MNRAS, 433, L15

(ref: Lozinskaya2007) Lozinskaya, T. A. & Moiseev, A. V. 2007, MNRAS, 381, L26

(ref: Martin2008) Martı́n, S., Requena-Torres, M. A., Martı́n-Pintado, J., & Mauersberger, R. 2008, ApJ, 678, 245

(ref: Martizzi2015) Martizzi, D., Faucher-Giguère, C.-A., & Quataert, E. 2015, MNRAS, 450, 504

(ref: Mehringer1992) Mehringer, D. M., Yusef-Zadeh, F., Palmer, P., & Goss, W. M. 1992, ApJ, 401, 168

(ref: Meng2019) Meng, F., Sánchez-Monge, Á., Schilke, P., et al. 2019, A&A, 630, A73

(ref: Mills2017) Mills, E. A. C. & Battersby, C. 2017, ApJ, 835, 76

(ref: Minniti2010) Minniti, D., Lucas, P. W., Emerson, J. P., et al. 2010, New A, 15, 433

(ref: Molinari2010) Molinari, S., Swinyard, B., Bally, J., et al. 2010, PASP, 122, 314

(ref: Morris1996) Morris, M. & Serabyn, E. 1996, ARA&A, 34, 645

(ref: Nieva2014) Nieva, M.-F. & Przybilla, N. 2014, A&A, 566, A7

(ref: Nogueras-Lara2024) Nogueras-Lara, F. 2024, A&A, 681, L21

(ref: Nogueras-Lara2022) Nogueras-Lara, F., Schödel, R., & Neumayer, N. 2022, Nature Astronomy, 6, 1178

(ref: Paczynski1988) Paczyński, B. 1998, ApJL, 494, L45

(ref: Padovani2019) Padovani, M., Marcowith, A., Sánchez-Monge, Á., Meng, F., & Schilke, P. 2019, A&A, 630, A72

(ref: Panagia1973) Panagia, N. 1973, AJ, 78, 929

(ref: Pare2024) Paré, D., Butterfield, N. O., Chuss, D. T., et al. 2024, ApJ, 969, 150

(ref: Pierce-Price2000) Pierce-Price, D., Richer, J. S., Greaves, J. S., et al. 2000, ApJL, 545, L121

(ref: Ponti2015) Ponti, G., De Marco, B., Morris, M. R., et al. 2015, MNRAS, 454, 1525

(ref: Ramirez2008) Ramı́rez, S. V., Arendt, R. G., Sellgren, K., et al. 2008, ApJS, 175, 147

(ref: Remijan2007) Remijan, A. J., Markwick-Kemper, A., & ALMA Working Group on Spectral Line Frequencies. 2007, in American Astronomical Society Meeting Abstracts, Vol. 211, American Astronomical Society Meeting Abstracts, 132.11

(ref: Robitaille2012) Robitaille, T. & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, Astrophysics Source Code Library, record ascl:1208.017

(ref: Rosen2020) Rosen, A. L., Offner, S. S. R., Sadavoy, S. I., et al. 2020, Space Sci. Rev., 216, 62

(ref: Sato2000) Sato, F., Hasegawa, T., Whiteoak, J. B., & Miyawaki, R. 2000, ApJ, 535, 857

(ref: Schmiedeke2016) Schmiedeke, A., Schilke, P., Möller, T., et al. 2016, A&A, 588, A143

(ref: Sharma2014) Sharma, P., Roy, A., Nath, B. B., & Shchekinov, Y. 2014, MNRAS, 443, 3463

(ref: Shirley2015) Shirley, Y. L. 2015, PASP, 127, 299

(ref: Skrutskie2006) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: Smith2002) Smith, L. J., Norris, R. P. F., & Crowther, P. A. 2002, MNRAS, 337, 1309

(ref: Sofue2020) Sofue, Y. 2020, PASJ, 72, L11

(ref: Sofue2021) Sofue, Y. 2021, Galaxies, 9, 13

(ref: Sofue2024) Sofue, Y. 2024, arXiv e-prints, arXiv:2404.11892

(ref: Sormani2019) Sormani, M. C. & Barnes, A. T. 2019, MNRAS, 484, 1213

(ref: Sormani2020) Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497, 5024

(ref: Tamburro2009) Tamburro, D., Rix, H. W., Leroy, A. K., et al. 2009, AJ, 137, 4424

(ref: Thornton1998) Thornton, K., Gaudlitz, M., Janka, H. T., & Steinmetz, M. 1998, ApJ, 500, 95

(ref: Tress2020a) Tress, R. G., Sormani, M. C., Glover, S. C. O., et al. 2020, MNRAS, 499, 4455

(ref: Tsuboi2015b) Tsuboi, M., Miyazaki, A., & Uehara, K. 2015a, PASJ, 67, 109

(ref: Tsuboi2015) Tsuboi, M., Miyazaki, A., & Uehara, K. 2015b, PASJ, 67, 90

(ref: vanderTak2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: Vink2012) Vink, J. 2012, A&ARv, 20, 49

(ref: Vink2017) Vink, J. 2017, in Handbook of Supernovae, ed. A. W. Alsabti & P. Murdin, 2063

(ref: Wang1999) Wang, Q. D. 1999, ApJL, 517, L27

(ref: Wang2021) Wang, Q. D. 2021, MNRAS, 504, 1609

(ref: Yusef-Zadeh2022) Yusef-Zadeh, F., Arendt, R. G., Wardle, M., et al. 2022, ApJL, 925, L18

# Observational information

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | Rest Frequency ($\nu_\mathrm{rest}$) | Upper Energy Level (E$_\mathrm{up}$) | Critical Density (n$_\mathrm{crit}$) | Beam | RMS |
|  |  | \[GHz\] | \[K\] | \[$10^4$ cm$^{-3}$\] | \[arcsec\] | \[K\] |
| SO | $2_{2}$–$1_{1}$ | 86.0940 | 19.3 | ... | 2.21 | 0.08 |
| H$^{13}$CN | 1–0 | 86.3399 | 4.1 | 25 | 2.72 | 0.09 |
| H$^{13}$CO$^{+}$ | 1–0 | 86.7543 | 4.2 | 4.1 | 2.69 | 0.09 |
| SiO | 2–1 | 86.8470 | 6.3 | 10 | 2.69 | 0.09 |
| HN$^{13}$C | 1–0 | 87.0909 | 4.2 | ... | 2.69 | 0.08 |
| HNCO | 4–3 | 87.9252 | 10.5 | 2.1 | 2.81 | 0.24\* |
| CS | 2–1 | 97.9810 | 7.1 | 10 | 2.21 | 0.09 |
| HC$_{3}$N | 11–10 | 100.0763 | 28.8 | 16 | 2.17 | 0.07 |

Table notes: This table lists the rest frequencies, upper energy levels (taken from Splatalogue; (cite: Remijan2007)), and critical densities (taken from Table 2 of (cite: Barnes2020a), or Table 1 of (cite: Shirley2015); both assume a kinetic temperature of 20 K) of the spectral line transitions, as well as the circularised beam sizes and the RMS values of the corresponding cubes. The table is sorted by increasing frequency. Note the HNCO cube used throughout this study has a velocity resolution of 0.5 km s$^{-1}$, whereas the remaining cubes have a resolution of 3 km s$^{-1}$. Consequently, the noise level in the HNCO cube is higher than that observed in the remaining cubes.

Rest frequencies, upper energy levels, and critical densities of the studied transitions, as well as the beam sizes and RMS values of their corresponding cubes, are listed in Table [\[tab:spectral-line-info\]](#tab:spectral-line-info).

# Radial profiles

Figure [9](#fig_all_radial) shows the mean flux radial profiles of the spectral lines listed within Table [\[tab:spectral-line-info\]](#tab:spectral-line-info) across the M0.8$-$0.2 ring. The annuli are chosen to be 5$\ensuremath{''}$ thick and are centred on the central position of the ring-like structure. Most lines show one or two peaks within the continuum-defined extent of the ring (shown by the two dotted vertical lines in Fig. [9](#fig_all_radial)) and another peak at $\sim$174$\ensuremath{''}$ (dashed line in Fig. [9](#fig_all_radial)).

![](figures/radial-profile-alllines.pdf)

# Channel maps

In this section we present channel maps of the HNCO (4$-$3), HC$_{3}$N(11$-$10), SO(2$_{2}-$1$_{1}$), and SiO(2$-$1) emission across the M0.8$-$0.2 ring (Figs. [10](#fig_HNCO_chans), [11](#fig_HC3N_chans), [12](#fig_SO_chans), and [13](#fig_SiO_chans), respectively). Here, we observe that the ring-like structure is coherent across velocities from 10 km s$^{-1}$ to around 70 km s$^{-1}$ in the HNCO (4–3), HC$_{3}$N(11–10), and SO($2_{2}$–$1_{1}$) transitions. The SiO(2–1) emission, on the other hand, appears to trace only the outer edge of the structure at similar velocities.

Above and below the 10 km s$^{-1}$ to 70 km s$^{-1}$ velocity range, we identify additional velocity components; however, the structure of these components is significantly different from that of the M0.8$-$0.2 ring (Sect. [3.1](#subsec_morphology)). These additional components can also be seen in spectra presented in Figs. [4](#fig_HNCO_spec_moms) and [7](#fig_H40a_spectrum). We believe that they are unassociated with the ring-like structure and are instead related to other known velocity features in the Galactic Centre. For example, the redshifted (higher) velocity component is consistent with the stream of gas entering the Galactic Centre from the bar (e.g. (cite: Henshaw2023)). In addition, the redshifted velocity component seen at around 100 km s$^{-1}$ is consistent with the emission from the point source (H ii region) identified in the H40$\alpha$ emission, which is then also connected to this inflowing gas stream.

The channel maps reveal sharp, concentric rings of emission and here we ask how the rings retain their observed sharp structures for 0.1 Myr or more, especially in the highly turbulent interior of the CMZ. Magnetic fields may play a role, but unless the magnetic tension and pressures are larger than the turbulent pressure, the rings should be destroyed in a time comparable to the ring thickness divided by the turbulent velocity. The individual filaments that make up the rings are observed to have widths comparable to the resolution. For widths of a few arcseconds, or $\sim 20,000$ AU $= 0.1$ pc (at the distance of the Galactic Centre), 1 km s$^{-1}$ of turbulence would allow these features to persist for 100,000 years. However, at higher values of, for example, 10 km s$^{-1}$, they could only persist for 10,000 years. We see that the filaments have velocity dispersions on the scale of the beam size between these two values (see the channel maps in Fig. [10](#fig_HNCO_chans)), highlighting that they may be transient features of the region, or pointing to the M0.8-0.2 ring being younger than proposed.

![image](figures/hnco43_chans.pdf)

![image](figures/hc3n1110_chans.pdf)

![image](figures/so3221_chans.pdf)

![image](figures/sio21_chans.pdf)

[^1]: We also examined re-reduced HiGal datasets using the method of (cite: Guzman2015), which involves a background subtraction technique that more effectively separates Galactic cirrus and other emission from the molecular clouds themselves. We find the differences were not significant and thus retain the HiGal processed results.

[^2]: The full width at tenth maximum (FWTM) could also be employed in this calculation to encompass the more extreme velocities, which would increase the value by a factor of (FWTM/FWHM) $\sim$ 1.8.

[^3]: Assuming a gas-to-dust ratio of 100, yet this could be somewhat lower in the Galactic Centre due to its super-solar metallicity (see the discussion in (cite: Barnes2019)). Moreover, we note that this estimate does not take into account the fore- and background line-of-sight contamination from objects within the Galactic Centre.

[^4]: Note that these do not necessarily correspond to the observed line-width, but rather to one of the dimensions of the radiative transfer box that we expect to be significantly smaller than our mean measured values across the region. These values are more similar to those measured on a per-beam basis across the region (a future work will investigate the full velocity component structure of the region).

[^5]: At this maximum likelihood density of $n_{\mathrm{H2}} \approx 10^{4.2}$, and with a $\log(X_\mathrm{HNCO}) \approx -8.5$, the excitation temperatures of HNCO range from around 10 to 40 K, and the optical depth ranges from around 0.1 to 0.5.

[^6]: Though we note the possible contribution of non-thermal emission mechanisms towards H ii regions, as studied in the Sgr B2 region in the CMZ (e.g. (cite: Meng2019; Padovani2019)).

</paper>

Write the methods card for this paper.