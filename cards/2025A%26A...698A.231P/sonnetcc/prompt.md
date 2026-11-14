# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...698A.231P\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...698A.231P",
 "title": "Vertical CO surfaces as a probe for protoplanetary disk mass and carbon depletion",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Paneque-Carreño, T.",
 "n_authors": 5,
 "arxiv_id": "2501.08294",
 "doi": "10.1051/0004-6361/202451862",
 "alma_projects_linked_by_archive": [
  "2015.1.00168.S",
  "2015.1.00192.S",
  "2016.1.00204.S",
  "2016.1.00344.S",
  "2016.1.00484.L",
  "2016.1.00606.S",
  "2017.1.00069.S",
  "2018.1.01055.L"
 ]
}
```

Paper text:
<paper>
# Vertical CO surfaces as a probe for\
protoplanetary disk mass and carbon depletion

As the sample of mid-inclination disks with measured CO emission surfaces grows, a fundamental unanswered question is how these vertical profiles connect to their host properties.

This project aims to relate the vertical extent of protoplanetary disks as traced by $^{12}$CO $2-1$ to key stellar and physical parameters. In order to produce a result that is applicable towards an observational analysis, we benchmark our results with ALMA observations of CO emission from nineteen disks.

We produce a grid of disk models using the physical-chemical code DALI, for a template T Tauri and Herbig star. Our models use an iterative solver to calculate the hydrostatic equilibrium equations and determine a physically-motivated density structure. Key stellar and disk parameters such as stellar luminosity and temperature, total disk mass, carbon abundance and critical radius are varied to determine their effect on the CO emitting surface. Each vertical profile is fitted by an exponentially tapered power-law and characterized by the $z/r$ value that represents the structure inwards of 80% of the tapering radius.

The CO emission surface location is primarily determined by the disk mass ($M_d$) and the level of volatile carbon depletion. T Tauri and Herbig systems show different vertical profiles, with disks around T Tauri stars being more vertically extended. We derive a $z/r$-$M_d$ relationship, which for each stellar type has a degeneracy with the volatile carbon abundance. In order to reconcile total disk mass estimates from the characteristic $z/r$ and the values obtained based on dust continuum analysis, a volatile carbon depletion of 10-100 (with respect to the ISM) is needed for the majority of our sources. Our carbon depletion values are in agreement with previous literature estimates, highlighting the potential of this method to rapidly calculate key disk parameters.

# Introduction

Planets form and grow within protoplanetary disks made of dust and gas which orbit around young stellar objects. Through high spatial and spectral resolutions of the Atacama Large Millimeter/submillimeter Array (ALMA) it has been possible to trace the extent and structure of these disks in dust and gas across all three dimensions; azimuthal, radial and vertical (cite: DSHARP_Huang_radial; Andrews_2020_review; MAPS_Law_radial; MAPS_Law_Surf; Paneque_2023_vert; Temmink_2023_HD142527; booth_2023_hd100546). To date, most studies have focused on the information offered by the radial and azimuthal structure (cite: Bae_2023_ppvii). Radial extent compared to the stellar age is used as an indicator on the governing evolution processes (cite: Rosotti_2019; Tazzari_2021_dustsizes; Long_2022_disksize; Trapman_2023_disksize) and radial substructures characterize a number of chemical and physical scenarios (cite: Andrews_2020_review; MAPS_Oberg; Oberg_2023_chemreview). Azimuthal enhancements can signal towards the presence of planetary companions (cite: Ragusa_2017_horseshoes; Perez_2020_hd100546; Long_2022_lagrangian; booth_2023_hd100546; Rampinelli_2024_PDS70) and some azimuthal asymmetries can be linked to inner warps or other disk processes such as ongoing infall (cite: Perez_2018_DSHARP; Young_2021_warp; Paneque-Carreno_2022_Elias_CN). Vertical structure, however, has been less accessible from an observational point of view and therefore less studied in comparison to the other two dimensions.

Directly probing the vertical structure and molecular layering of disks through observations of edge-on disks has offered valuable insight on the thermal and density conditions (cite: Dutrey_2017_flyingsaucer; RuizRodriguez_2021), as well as dust-settling processes (cite: Villenave_2020; Villenave_2023). In the recent years, novel methodologies (cite: Dartois_2003_DMTau; Pinte_2018_method; Kurtovic_2024_MHO6) have proven that the vertical structure can also be traced from mid-inclination ($\sim$40-60$^{\circ}$) disks, opening an exciting avenue to explore this dimension in larger samples (cite: Rich_2021; MAPS_Law_Surf; Law_2022_12CO; Law_2023_CO_isotop_surf) and multiple molecular tracers (cite: Paneque-Carreno_2022_Elias_CN; Paneque_2023_vert; paneque-carreno_2024_IMLup; Law_2023_CI; Urbina_2024_CI; Hernandez-Vera_2024_H2CO_HD16). From a theoretical point of view, the vertical distribution of the gaseous disk material will follow hydrostatic equilibrium between the stellar gravitational potential and thermal pressure support (cite: Armitage_2015). This implies that a number of properties such as stellar mass and radiation field, but also disk temperature structure and density distribution are expected to affect the vertical extent (cite: Dalessio_1998; Aikawa_2002). While the bulk of the disk material is composed of molecular hydrogen (H$_2$), we are not able to trace the disk structure through its emission, as it is extremely hard to detect throughout the cold outer ($r>$50 au) disk region. Due to this difficulty, less abundant, but bright tracers, such as carbon monoxide (CO) are preferred to characterize the disk structure and conditions (cite: Miotello_ppvii_2023).

This work focuses on the protoplanetary disk properties that affect the vertical structure as traced by bright $^{12}$CO $2-1$ emission. We select this specific transition as it is easily observed by ALMA in protoplanetary disks and the most common tracer of the disk vertical extent (cite: Law_2022_12CO; Law_2023_CO_isotop_surf). CO is the main carrier of gas-phase carbon in the interstellar medium and its chemistry is relatively simple and reliably implemented in various physical-chemical models (cite: Aikawa_2002; Gorti_2008_CO; Bruderer_DALI_2013; Miotello_2014; woitke_2016_prodimo; Yu_2016_CO; Molyarova_2017_CO). For this reason CO is a preferred molecule to study the disk extent (cite: Ansdell_2018; Sanchis_2021; MAPS_Law_radial; Law_2022_12CO; Rich_2021), kinematical processes (cite: Pinte_2023_ppvii; Izquierdo_2023_discminer2; MAPS_Teague), temperature structure (cite: MAPS_Law_Surf; Paneque_2023_vert; Stapper_2023_Herbig_surf) and disk mass (cite: Miotello_2014; miotello_2016; BoothA_2019_13C17O; stapper_2024_gasmass). Vertically, CO gas emission originates from the warm molecular layer defined by the boundary of UV photo-dissociation in the upper regions and low temperatures that cause CO freeze-out ($\sim$20 K) closer to the midplane (cite: Aikawa_2002). At typical temperatures (40–60 K) and CO column densities ($\geq$ 5 $\times$ 10$^{16}$ cm$^{-2}$) of the molecular layer in protoplanetary disks, the CO millimeter emission will be optically thick (cite: van_der_Tak_2007_RADEX). Indeed, previous works have shown that the emitting surface traced by CO, as extracted from line emission channel maps, follows the CO $\tau \sim$1 region of the disk structure (cite: Paneque_2023_vert). Efforts in linking the observationally derived CO surfaces to system or emission properties such as stellar mass, brightness temperature or disk radius have only provided tentative trends (cite: Law_2022_12CO; Law_2023_CO_isotop_surf) and it is not yet well understood how the wide range of CO vertical profiles (cite: Law_2023_CO_isotop_surf; Paneque_2023_vert) relates to the system properties.

A crucial assumption that most studies related to CO emission make is that its abundance with respect to H$_2$, as set by the volatile carbon abundance, follows the canonical interstellar medium (ISM) value of $\sim$10$^{-4}$ (cite: Andrews_2011; Ansdell_2016_Lupus; Flaherty_2015_hd16_weakturb; stapper_2024_gasmass). This is in tension with observational results that show that between 1-2 orders of magnitude of volatile carbon depletion must be present to account for disk masses derived from HD observations (cite: Favre_2013_lowCO; McClure_2016_HD; Schwarz_2016_CO_TWHya; Calahan_2021_HD_TwHya) and derivations of CO depletion, with respect to ISM abundance, from optically thin CO isotopologue emission profiles (cite: Zhang_2019_CO_abundance; MAPS_Zhang). Lower-than-ISM CO abundances may be caused by chemical reprocessing of CO into other molecules (cite: Bergin_2014_CO; Bosman_2018_CO; Diop_2024_CO_ML) or physical processing through which carbon is removed from the disk atmosphere by icy dust grains that grow and settle towards the disk midplane (cite: Krijt_2016; Krijt_2018; Krijt_2020). These processes are in addition to photodissociation and freeze-out, which will also lower the CO abundance throughout the disk and are included in standard thermochemical models (cite: Bruderer_DALI_2013; woitke_2016_prodimo). Overall, it is expected that the CO abundance may change as the disk evolves and therefore it is not inherited from the natal cloud environment (cite: Visser_2009_CO; Bergner_2020_CO; MAPS_Zhang). To the best of our knowledge, there are no previous studies that model or observationally analyze the effect of volatile carbon depletion on the vertical emitting surface of disks.

The remainder of this paper is organized as follows. Section 2 details the setup of thermochemical models used in our analysis, indicating the relevance of accounting for hydrostatic equilibrium for a more realistic approach. Section 3 shows our main results, an overview of the sampled parameter space and the effect of various disk and stellar properties on the location of the $\tau =$ 1 CO emission layer. We present a $z/r-$Disk mass relation for both T Tauri and Herbig disk systems and apply it to a sample of archival protoplanetary disk observations. Our results showcase the necessity of considering carbon depletion in order to obtain disk masses that are in agreement with literature values. Section 4 has a detailed discussion of our results, comparing them to previous studies and literature values of carbon depletion. Finally, Section 5 indicates the main conclusions of this work.

# Modelling

The results shown in this paper are based on an extensive grid of models run with the thermochemical code DALI (cite: Bruderer_DALI_2013). For details on the code, how the chemical network is setup and the calculation of the temperature structure, dust populations and flux values we refer to past works using the same code (cite: Bruderer_2012; Bruderer_DALI_2013; miotello_2016; leemker_2022_LkCa15; stapper_2024_gasmass). Our models are run using the chemical network from (cite: Miotello_2014), that accounts for CO isotope-selective effects, considering selective photodissociation, fractionation reactions, self-shielding, and freeze-out (cite: Miotello_2014; miotello_2016).

## Initial DALI setup

+-------------------------------------------+--------------------------------------------------------+
| Parameter                                 | Value                                                  |
+:==========================================+:=======================================================+
| *Chemistry*                                                                                        |
+-------------------------------------------+--------------------------------------------------------+
| Chemical Age                              | 1 Myr                                                  |
+-------------------------------------------+--------------------------------------------------------+
| Volatile \[C\]/\[H\]                      | 1.35 $\times$ 10$^{-4}$, 10$^{-5}$, 10$^{-6}$          |
+-------------------------------------------+--------------------------------------------------------+
| Volatile \[O\]/\[H\]                      | 2.88 $\times$ 10$^{-4}$, 10$^{-5}$, 10$^{-6}$          |
+-------------------------------------------+--------------------------------------------------------+
| \[PAH\]                                   | 10$^{-4}$ ISM abundance                                |
+-------------------------------------------+--------------------------------------------------------+
| *Physical Structure*                                                                               |
+-------------------------------------------+--------------------------------------------------------+
| gas-to-dust ratio                         | 100                                                    |
+-------------------------------------------+--------------------------------------------------------+
| $f_\mathrm{{large}}$ (small/large grains) | 0.95                                                   |
+-------------------------------------------+--------------------------------------------------------+
| $\chi$ (settling of large grains)         | 0.2                                                    |
+-------------------------------------------+--------------------------------------------------------+
| $\varphi$ (flaring index)                 | 0.1                                                    |
+-------------------------------------------+--------------------------------------------------------+
| $h_{100}$ (scale height aspect ratio)     | 0.1                                                    |
+-------------------------------------------+--------------------------------------------------------+
| $R_c$ (characteristic radii)              | 100 au                                                 |
+-------------------------------------------+--------------------------------------------------------+
| $M_d$ (total disk mass)                   | 10$^{-1}$, 10$^{-2}$, 10$^{-3}$, 10$^{-4}$ M$_{\odot}$ |
+-------------------------------------------+--------------------------------------------------------+
| *Stellar Parameters*                                                                               |
+-------------------------------------------+--------------------------------------------------------+
| $L_x$                                     | 1.0 $\times$ 10$^{30}$ erg s$^{-1}$                    |
+-------------------------------------------+--------------------------------------------------------+
| $T_x$                                     | 7.0 $\times$ 10$^{7}$ K                                |
+-------------------------------------------+--------------------------------------------------------+
|                                                                                                    |
+----------------------------------------------------------------------------------------------------+
| *T Tauri model*                                                                                    |
+-------------------------------------------+--------------------------------------------------------+
| $M_*$                                     | 1.0 M$_{\odot}$                                        |
+-------------------------------------------+--------------------------------------------------------+
| $\dot{M}_{\mathrm{acc}}$                  | 10$^{-8}$ M$_{\odot}$ yr$^{-1}$                        |
+-------------------------------------------+--------------------------------------------------------+
| $L_{\mathrm{bol}}$                        | 1.0 L$_{\odot}$                                        |
+-------------------------------------------+--------------------------------------------------------+
| $T_{\mathrm{eff}}$                        | 4000 K                                                 |
+-------------------------------------------+--------------------------------------------------------+
|                                                                                                    |
+----------------------------------------------------------------------------------------------------+
| *Herbig model*                                                                                     |
+-------------------------------------------+--------------------------------------------------------+
| $M_*$                                     | 2.0 M$_{\odot}$                                        |
+-------------------------------------------+--------------------------------------------------------+
| $L_{\mathrm{bol}}$                        | 17.0 L$_{\odot}$                                       |
+-------------------------------------------+--------------------------------------------------------+
| $T_{\mathrm{eff}}$                        | 9000 K                                                 |
+-------------------------------------------+--------------------------------------------------------+

: Initial parameters in fiducial DALI model

The initial setup of the radial structure for the gas and dust in DALI follows the self-similar solution to a viscously evolving disk (cite: Lynden_Bell_Pringle_1974; Andrews_2011).

$$\begin{equation}
    \Sigma(R) = \Sigma_c \left( \frac{R}{R_c} \right) ^{-\gamma} \mathrm{exp} \left[ - \left(\frac{R}{R_c} \right) ^{2-\gamma} \right]
\end{equation}$$

where $R_c$ is the characteristic radius at which the surface density is $\Sigma_c/e$ and $\gamma$ the surface density exponent. The initial vertical structure of the disk follows a Gaussian distribution, where the gas density ($\rho$) corresponds to,

$$\begin{equation}
    \rho (z) = \rho_c (r) \mathrm{exp} \left[-\frac{z^{2}}{(2 H^2)} \right]
\end{equation}$$

and $H$ is the disk scale height and $\rho_c$ a characteristic gas density. To set the scale heigh aspect ratio ($H/r$), we have modified the usual DALI prescription (cite: leemker_2022_LkCa15) to match the parametrization of (cite: MAPS_Zhang). In our model the scale height aspect ratio as a function of radius follows,

$$\begin{equation}
    H/r = h_\mathrm{100} \left( \frac{R}{ 100 \mathrm{au} } \right) ^{\varphi}
\end{equation}$$

where $h_\mathrm{100}$ is the scale height aspect ratio at 100 au and $\varphi$ the flaring angle. The main results in this study are based on the fiducial models for a T Tauri and Herbig system following the values presented in Table [1](#table_DALI_param). The parameters of the T Tauri system are based on the models of (cite: miotello_2016), while the fiducial Herbig model has the stellar parameters (mass, luminosity and temperature) based on HD 163296 (cite: MAPS_Oberg; Paneque_2023_vert). For the T Tauri model, excess UV radiation due to a mass accretion rate of 10$^{-8}$ M$_{\odot}$ yr$^{-1}$ was taken into account. It was assumed that the gravitational potential energy of the accreted mass is released with 100% efficiency as blackbody emission with $T = 10^{4}$ K (cite: Miotello_2014; miotello_2016). For our parameters, these assumptions result in $L_{\mathrm{FUV}}$/$L_{\mathrm{bol}} = 1.46 \times 10^{-1}$. No accretion is considered in the Herbig system, based on observational evidence (cite: Hartmann_2016) and previous models (cite: stapper_2024_gasmass). Beyond the fiducial models, we study a wider parameter space to determine the effect of key disk properties on the location of the vertical structure as traced by $^{12}$CO. Table [2](#table_DALI_varyparam) indicates the sampled values which includes a range of disk masses, stellar luminosities and temperatures, to cover a broader observational sample. The fraction of small/large dust grains is also an important number that may modify the CO emitting layer as it affects the degree of penetrating energetic radiation responsible for enhancing or inhibiting CO photo-dissociation.

+-------------------------------------------+-----------------------------------------------------------+
| Parameter                                 | Sampled values                                            |
+:==========================================+:==========================================================+
| *T Tauri model*                                                                                       |
+-------------------------------------------+-----------------------------------------------------------+
| $\varphi$ (flaring index)                 | **0.1**, 0.2, 0.5                                         |
+-------------------------------------------+-----------------------------------------------------------+
| $f_\mathrm{{large}}$ (small/large grains) | 0.9, **0.95**, 0.99                                       |
+-------------------------------------------+-----------------------------------------------------------+
| $T_{\mathrm{eff}}$                        | 3500, **4000**, 4500 K                                    |
+-------------------------------------------+-----------------------------------------------------------+
| $L_{\mathrm{bol}}$                        | 0.2, **1.0**, 3 L$_{\odot}$                               |
+-------------------------------------------+-----------------------------------------------------------+
| $\dot{M}_{\mathrm{acc}}$                  | 10$^{-9}$, **10$^{-8}$**, 10$^{-7}$ M$_{\odot}$ yr$^{-1}$ |
+-------------------------------------------+-----------------------------------------------------------+
| $R_c$ (characteristic radii)              | 15, 50, **100** au                                        |
+-------------------------------------------+-----------------------------------------------------------+
|                                                                                                       |
+-------------------------------------------------------------------------------------------------------+
| *Herbig model*                                                                                        |
+-------------------------------------------+-----------------------------------------------------------+
| \[PAH\]                                   | **10$^{-4}$**, 10$^{-2}$ , 10$^{-1}$ ISM abundance        |
+-------------------------------------------+-----------------------------------------------------------+
| $T_{\mathrm{eff}}$                        | 7500, **9000**, 10000 K                                   |
+-------------------------------------------+-----------------------------------------------------------+
| $L_{\mathrm{bol}}$                        | 10, **17**, 30 L$_{\odot}$                                |
+-------------------------------------------+-----------------------------------------------------------+
| $R_c$ (characteristic radii)              | 15, 50, **100** au                                        |
+-------------------------------------------+-----------------------------------------------------------+

: Variation of DALI model parameters. Bold numbers indicate the fiducial model values.

## Hydrostatic equilibrium

![](abundance_ttauri_0.01model.pdf)

The initial setup presented in the previous section is a useful approximation, but is not realistic, as it is known that the disk vertical structure does not follow a gaussian distribution, rather it is set by hydrostatic equilibrium between the stellar gravity and pressure support of the disk (given by the thermal structure). To produce more realistic models, DALI has a hydrostatic equilibrium solver implemented, which self-consistently iterates over consecutive models, starting from the initial parametrization, to compute the disk structure. We use this approach for all of our analysis. To this end, the hydrostatic equilibrium equation that must be solved in the vertical direction, using cylindrical coordinates, is:

$$\begin{equation}
   \frac{1}{\rho}\frac{dP}{dz} = -\frac{d\phi}{dz}
\end{equation}$$

where $\rho$ is the gas density, $P$ the gas pressure and $\phi$ the gravitational potential. Without considering self-gravity, $\phi$ corresponds to the stellar gravitational potential and follows,

$$\begin{equation}
   \phi = -\frac{GM_*}{(r^2 + z^2)^{1/2}}
\end{equation}$$

Self-gravity may become relevant for the most massive disks in our parameter space, producing lower emitting layers than our prescription. However, its effect is prevalent in the outer portions of the disk (cite: Lodato_2023_mass_imlup) which are not relevant for the $z/r$ calculations of this study (method detailed in section 3).

Pressure and density can be connected such that $P/\rho = c_{s}^{2} = kT/(\mu m_p)$. Disks are not isothermal in their vertical direction, therefore, the sound speed ($c_s$) will vary as function of height, depending on the density and thermal conditions. The differential equation for $P$ is

$$\begin{equation}
    \frac{1}{P} \frac{dP}{dz} = -\frac{z\,GM_*}{c_{s}^{2}(r^2 + z^2)^{3/2}}
\end{equation}$$

and can be solved through

$$\begin{equation}
    P(z) = c_{s}(z)^{2} \rho(z) = C \, \mathrm{exp} \left(\, - \int \frac{z\,GM_*}{c_{s}^{2}(r^2 + z^2)^{3/2}}  dz\, \right)
\end{equation}$$

which will obtain the vertical distribution for the gas density ($\rho(z)$). In DALI, the disk temperature structure is first obtained from the initial model, which computes the thermal conditions of the material considering all relevant cooling and heating processes, and is then used to update the gas density distribution accounting for thermal support. The updated density is consecutively used to recalculate the temperature for the next iteration and start over until reasonable convergence of the disk structure is achieved, which in this case is checked by verifying that the variation of the temperature and vertical location of the CO layer is minimal. The integration constant $C$ is adjusted such that $\int \rho(z)\,dz$ is preserved with each iteration. In the isothermal approximation $c_{s}^{2}$ does not have a vertical dependence and we recover the gaussian distribution indicated in equation 2.

Figure [1](#ttauri_model) shows the 2D maps for the gas density, temperature and CO abundance (with respect to H$_2$) of a converged DALI model for a 10$^{-2}$M$_{\odot}$ disk around a 1M$_{\odot}$ and 1L$_{\odot}$ stellar system. The static gaussian distribution corresponds to the initial DALI output, computed from the setup equations outlined in section 2.1. The self-consistent model solution is the result of six iterations solving the hydrostatic equilibrium equations, considering the previously computed thermal structure. The material appears to be more vertically extended in the self-consistent model, which is expected due to the increased pressure support of the heated atmosphere calculated from the vertical temperature gradient. Our study focuses on the $^{12}$CO $2-1$ emission surface, which is directly computed from the models as the location where the integrated column density of material results in an optical depth ($\tau$) of 1 for $^{12}$CO $2-1$. Indeed, the $\tau =$1 layer of DALI models is consistent with the emission surfaces extracted from ALMA gas emission maps of $^{12}$CO $2-1$ (cite: Paneque_2023_vert).

![](comp_hydro_model.pdf)

When accounting for hydrostatic equilibrium, the $\tau = 1$ surface varies both in its vertical and radial extent from the surface extracted from the parametric model. Figure [2](#hydro_models) indicated the variations for the $\tau = 1$ layer in a 10$^{-2}$ M$_{\odot}$ disk around a 1 M$_{\odot}$ and 1 L$_{\odot}$ star (T Tauri model) compared to the same disk mass around a 2 M$_{\odot}$ and 17 L$_{\odot}$ star (Herbig model). As the hydrostatic equilibrium solution depends on the stellar mass, temperature and density distribution, it is expected that the surfaces will be different in each case. Convergence is reached rapidly after a couple of iterations, therefore all presented models in this work will consider the output from the 6th iteration of the self-consistent hydrostatic equilibrium solver. Small perturbations can be identified in the surfaces extracted from the first iterations, but we do not consider them relevant as they are artifacts that appear while the model is reaching convergence.

# Results

As has been shown in multiple studies, CO molecular surfaces can be parametrized through an exponentially tapered power-law (cite: MAPS_Law_Surf; Law_2023_CO_isotop_surf; Paneque_2023_vert). To model each $^{12}$CO $\tau = 1$ surface from the self-consistent DALI outputs after solving the hydrostatic equilibrium equations, we select the following prescription,

$$\begin{equation}
z(r) = z_0\times \left(\frac{r}{100\,\mathrm{au}}\right)^{\phi} \times \exp\left[\left(\frac{-r}{r_{\mathrm{taper}}}\right)^{\psi}\right]
\end{equation}$$

The best fit values for $z_0$, $\phi$, $r_{\mathrm{taper}}$ and $\psi$ are obtained using a Monte Carlo Markov Chain (MCMC) sampler as implemented by emcee (cite: emcee_ref). We initialize the MCMC assuming a uniform distribution of the four parameters within the following intervals: $z_0 \in [0, 100]$, $\phi \in [0, 10]$, $r_{\mathrm{taper}}/\mathrm{au} \in [50, 500]$, $\psi \in [0,10]$. We use 30 walkers, with 500 steps as burn-in and 800 steps to evaluate confidence intervals. Each surface is then identified based on its characteristic $z/r$ value, which corresponds to the best-fit line of constant $z/r$ that traces the height profile within 80% of $r_{\mathrm{taper}}$ (cite: Law_2023_CO_isotop_surf). This assures us that we are characterizing the rising portion of the $^{12}$CO surface, as exemplified in Figure [3](#method_zr) where a schematic of the method is shown. We consider only the rising portion to match the observational prescription found in the literature (cite: Law_2022_12CO; Law_2023_CO_isotop_surf) and to avoid the drop of the emission surface in the outer disk, an effect that happens due to the radially decreasing density profile. In some model outputs this drop appears as a sudden, almost vertical, feature in the outer radii which is likely a resolution artifact that does not impact our results.

![](zr_method_show.pdf)

![](percent_vary_param.pdf)

![](CO_dep_zr_only.pdf)

## Parameters that affect vertical CO surface

Our fiducial models for each stellar type are indicated in Table [1](#table_DALI_param). To determine which parameter variation most strongly affects the measured $z/r$ we compute additional models with a varied stellar luminosities and temperatures as reported in Table [2](#table_DALI_varyparam) covering the range of reported values from the comparison observations. Disk structure values for the flaring angle ($\varphi$), small-to-large dust grain fraction ($f$), PAH abundance, surface density characteristic radius ($R_c$), total disk mass ($M_d$) and volatile carbon abundance (C$_{\mathrm{abu}}$) are also sampled. Only one parameter is varied at a time in each model, starting from the fiducial values. For every case the characteristic $z/r$ is computed as described at the beginning of Section 3. Figure [4](#vary_param_grid) presents the percentual variation from the fiducial model for disk masses of 10$^{-3}$ M$_{\odot}$ and 10$^{-2}$ M$_{\odot}$. The full vertical profiles for each parameter can be found in Figures [9](#vary_param_appendix_M1e-2) and [10](#vary_param_appendix_M1e-3).

+:----------:+:---------------:+:---------------:+:---------:+:----------------------:+:--------------------:+:---------------------------:+:---------------------:+:-----------------:+
| Star       | M$_*$           | L$_*$           | T$_*$     | Previous disk mass estimates \[M$_{\odot}$\]                                                        | References        |
|            +-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+                   |
|            | \[M$_{\odot}$\] | \[L$_{\odot}$\] | \[K\]     | Dust mass $\times$ 100 | CO flux              | HD emission                 | Dynamical             |                   |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| **T Tauri Disks**                                                                                                                                                                    |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| MY Lup     | 1.27            | 0.87            | 5129      | 1.5$\times$10$^{-2}$   | 8.3$\times$10$^{-5}$ | \-                          | \-                    | 4 , 3, 12, 5      |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| AS 209     | 1.2             | 1.41            | 4266      | 7.5$\times$10$^{-2}$   | 4.5$\times$10$^{-3}$ | \-                          | $>$2$\times$10$^{-4}$ | 1, 13, 16, 18     |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| WaOph 6    | 1.12            | 2.9             | 4169      | 1.4$\times$10$^{-2}$   | \-                   | \-                          | \-                    | 4, 3, 14          |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| IM Lup     | 1.1             | 2.57            | 4266      | 3.67$\times$10$^{-1}$  | 2$\times$10$^{-1}$   | \-                          | 1.1$\times$10$^{-1}$  | 1, 13, 16, 18     |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| GM Aur     | 1.1             | 1.2             | 4350      | 7.3$\times$10$^{-2}$   | 2$\times$10$^{-1}$   | (2.5–20.4)$\times$10$^{-2}$ | 1.2$\times$10$^{-1}$  | 1, 13, 16, 18, 20 |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| DoAr 25    | 1.06            | 0.95            | 4266      | 4.2$\times$10$^{-2}$   | \-                   | \-                          | \-                    | 4, 3, 5           |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| LkCa 15    | 0.7             | 1.098           | 4162      | 2.7$\times$10$^{-2}$   | \-                   | $<$6.2$\times$10$^{-2}$     | \-                    | 5, 20             |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| GW Lup     | 0.62            | 0.33            | 3631      | 1.5$\times$10$^{-2}$   | 9.6$\times$10$^{-5}$ | \-                          | \-                    | 4, 3, 12, 5       |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| Sz 91      | 0.55            | 0.26            | 3720      | 2.2$\times$10$^{-3}$   | \-                   | \-                          | \-                    | 4, 10, 5          |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| DM Tau     | 0.50            | 0.24            | 3705      | 1.6$\times$10$^{-2}$   | \-                   | (1.0–4.7)$\times$10$^{-2}$  | \-                    | 4, 9, 5, 20       |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| Elias 2-27 | 0.46            | 0.91            | 3890      | 3.4$\times$10$^{-2}$   | \-                   | \-                          | 8$\times$10$^{-2}$    | 2, 3, 5, 17       |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| **Herbig Disks**                                                                                                                                                 |                   |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| HD 100546  | 2.10            | 23.4            | 9750      | 1.2$\times$10$^{-2}$   | 3.2$\times$10$^{-2}$ | $<$8$\times$10$^{-2}$       | \-                    | 4, 8, 11, 15, 19  |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| HD 97048   | 2.70            | 44.2            | 10500     | 4.7$\times$10$^{-2}$   | 1$\times$10$^{-1}$   | $<$9.4$\times$10$^{-2}$     | \-                    | 4, 8, 11, 15, 19  |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| HD 100453  | 1.66            | 6.31            | 7400      | 5.3$\times$10$^{-3}$   | 3.2$\times$10$^{-2}$ | $<$1$\times$10$^{-2}$       | \-                    | 6, 11, 15, 19     |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| HD 34282   | 1.59            | 13.64           | 8625      | 2.6$\times$10$^{-2}$   | 1.2$\times$10$^{-1}$ | \-                          | \-                    | 7, 11, 15         |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| MWC 480    | 2.1             | 21.9            | 8250      | 1.2$\times$10$^{-1}$   | 1$\times$10$^{-1}$   | \-                          | 1.5$\times$10$^{-1}$  | 1, 13, 15, 16     |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| HD 163296  | 2.0             | 17.0            | 9332      | 8.4$\times$10$^{-2}$   | 1$\times$10$^{-1}$   | $<$6.7$\times$10$^{-2}$     | 1.3$\times$10$^{-1}$  | 1, 13, 15, 16, 19 |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| HD 142666  | 1.73            | 9.1             | 7500      | 7.6$\times$10$^{-3}$   | 3.2$\times$10$^{-2}$ | \-                          | \-                    | 4, 8, 11, 15      |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+
| Ak Sco     | 1.2             | 2.4             | 6250      | 1.8$\times$10$^{-3}$   | 2.3$\times$10$^{-3}$ | \-                          | \-                    | 8, 11, 15         |
+------------+-----------------+-----------------+-----------+------------------------+----------------------+-----------------------------+-----------------------+-------------------+

The largest variation in $z/r$ is caused by varying the total disk mass, which is sampled at 10$^{-4}$ M$_{\odot}$ , 10$^{-3}$ M$_{\odot}$ , 10$^{-2}$ M$_{\odot}$ and 10$^{-1}$ M$_{\odot}$. An order of magnitude change in the disk mass can vary the emission height by more than 50%. Volatile carbon abundance also presents a strong effect in the emission surfaces. Indeed, an order of magnitude decrease in the assumed volatile carbon abundance with respect to the ISM can lower the characteristic $z/r$ by $\sim$30% and two orders of magnitude in carbon depletion produce $z/r$ variations beyond 50%. These two parameters have a degenerate contribution to the vertical surface, as can be seen from Figure [5](#CO_dep_zr_results). Increasing disk mass will push the CO emission layer higher, while for the same disk mass a lower volatile carbon abundance (higher depletion) will push the emitting layer towards the midplane. This result can be intuitively understood by remembering that the studied CO emision layers correspond to the location of the optically thick $\tau = 1$ surface and, therefore, they trace the vertical location at which the vertical column density of CO gas saturates, as seen from outside of the disk structure towards the midplane. A more massive disk will have larger column densities and saturate higher above the midplane. Likewise, for the same disk mass, a lower amount of CO gas due to lower quantities of volatile carbon will diminish the CO column densities and push the emission surface towards the midplane. This effect of carbon abundance in the vertical structure had been previously observed in (cite: Calahan_2021_HD_TwHya) when constraining the disk model of TW Hya.

Across all masses, for the same degree of carbon depletion, the T Tauri systems display a larger $z/r$ than the disks around Herbig stars (see Fig. [5](#CO_dep_zr_results)). This is expected due to the larger stellar mass of the Herbig model, which will translate into a higher gravitational potential (equation 5). The parameter space between our models is covered using a cubic spline which we use to extrapolate our results beyond our mass grid, to nearby values. We refer to this result as the $z/r$-$M_d$ relationship, noting that volatile carbon depletion will shift it and must be accounted for.

All other parameters, including order of magnitude variations in stellar accretion rate and PAH abundance (see Table [2](#table_DALI_varyparam)), cause a variation of less than $\sim$30%. We stress that these results only hold for the $^{12}$CO $2-1$ surface $z/r$, other molecules, particularly those more sensitive to UV fields are likely more significantly affected by some of the sampled parameters.

![](zr_mass_ISM_CO.pdf)

## Model comparison to observations

In order to benchmark our model results and the $z/r$-$M_d$ relationship, we estimate the gas masses and expected $z/r$ in an observational sample of 19 disks, as indicated in Table [\[table_sample_all\]](#table_sample_all). The studied disks all have estimates of their total disk mass from dust continuum observations, additionally, some of them have disk mass estimates from modelling of CO, HD or N$_2$H$^+$ fluxes and dynamical analysis of CO rotation curves.

Most disk mass values from dust continuum emission are extracted by converting the total continuum flux into a dust mass, assuming a dust temperature and grain opacity and then using the canonical assumption of a gas-to-dust ratio of 100 (cite: Hildebrand_1983_dustmass; Ansdell_2016_Lupus; andrews_2013_diskmass; Barenfeld_2016_uppersco; pascucci_2016_diskmass; stapper_2022_dustmass). Excluding the sources from the MAPS program (cite: MAPS_Oberg), the total disk masses estimated from CO millimeter emission for the Herbig sample are calculated in (cite: stapper_2024_gasmass) based on an extensive grid of models, as is the case of MY Lup and GW Lup from the T Tauri sample (cite: Miotello_2017). For the disks in the MAPS program (cite: MAPS_Oberg) the total disk mass calculated from dust continuum accounts for dust scattering processes and has a more accurate fitting of the thermal conditions (cite: sierra_2021_MAPS). On the other hand, the CO disk masses come from detailed thermochemical modelling of (cite: MAPS_Zhang). Estimations and upper limits of disk mass from HD emission are available for some sources and these were also calculated using thermochemical disk models to match the fluxes or non-detection threshold (cite: McClure_2016_HD; Kama_2020_HD). Through the combination of N$_2$H$^{+}$ and C$^{18}$O emission, thermochemical models assuming a degree of disk ionization have computed the total disk mass and expected carbon depletion (cite: Trapman_2022_N2Hp). Dynamical masses have been obtained for some disks, through the detection of super-Keplerian motion in the CO gas rotation curves from the outer radius of the disk rotation profile using isothermal (cite: Veronesi_2021_Elias) and thermally stratified (cite: Martire_2024_stratified_dyn_mass) vertical disk prescriptions.

This sample has been constructed from mid-inclination disks with available $^{12}$CO $2-1$ data cubes from which the surfaces have been extracted and published in previous works (cite: Law_2022_12CO; Law_2023_CO_isotop_surf; Stapper_2023_Herbig_surf; Paneque_2023_vert). In all cases, the vertical structure from the observations is obtained following the methodology presented in (cite: Pinte_2018_method), where the surfaces are constrained based on the emission maxima across the molecular line emission channel maps. However, some have used the automated code DISKSURF (cite: disksurf) and others have employed the manual masking approach of the code ALFAHOR (cite: Paneque_2023_vert). All $^{12}$CO surfaces for the Herbig disk sample are taken from (cite: Stapper_2023_Herbig_surf), where ALFAHOR is used to extract the vertical profile. For the T Tauri disks, part of the sample (AS 209, WaOph 6, IM Lup, GM Aur, Elias 2-27) is presented in (cite: Paneque_2023_vert), also using ALFAHOR. The remainder of the T Tauri disks are published in (cite: Law_2023_CO_isotop_surf) using an initial version of DISKSURF that in some cases underestimated the vertical profiles due to contamination from the back side of the disk (cite: Paneque_2023_vert). In order to do a uniform analysis, the disks previously studied using DISKSURF (MY Lup, DoAr 25, LkCa 15, GW Lup, Sz 91, DM Tau) are re-analysed using ALFAHOR, yielding comparable results but with a lower scatter. The scatter corresponds to the spread in height values recovered from the channel map analysis within each radial bin. A larger scatter, which may be due to low signal-to-noise data, contamination from the back side or optical depth effects for less abundant molecules, will produce a broader vertical profile, as the dispersion will be larger within a given radial bin. All vertical profiles from the observational sample are presented in Figures [11](#ttauri_obs) and [12](#herbig_obs), compared to the vertical profiles from the fiducial DALI models of varying disk mass with ISM-like carbon abundance.

As done for the DALI models, the vertical profiles of the observational sample are processed to obtain their characteristic $z/r$. To accurately account for the spread in the vertical profile, $z/r$ is calculated for the mean value and also for the lower and upper limits of the profiles, which indicate the dispersion within radial bins and will give the uncertainty on the characteristic $z/r$.

![](final_mass_plot.pdf)

Based on the $z/r$ - $M_d$ relationship shown in Figure [5](#CO_dep_zr_results) we estimate the expected $z/r$ for the reported total disk mass derived from dust continuum and available HD upper limits, assuming an ISM-like carbon abundance. These values are compared against the observationally derived $z/r$ values in Figure [6](#obs_comp_zr_COISM). For the majority of the sample, if we assume an ISM-like carbon abundance, our measured $z/r$ is below the expected value based on the dust masses considering a gas-to-dust ratio of 100. The only exceptions are DM Tau, Elias 2-27, HD 97048 and HD 34282. Throughout the sample, the differences are more noticeable in the T Tauri systems, as Herbig systems have better agreement within the uncertainty of our method. We note that taking into consideration carbon depletion would lower the expected $z/r$ of the literature mass measurements (see Fig. [5](#CO_dep_zr_results)), obtaining a better agreement with the observational emission heights.

Overall, these results may indicate that the assumed gas-to-dust ratio in the systems is much lower than 100 (effectively lowering the literature estimates from the dust flux) or that our model assumptions are failing to account for a significant factor affecting the $z/r$ value, such as the presence of carbon depletion. We favor the second scenario as dust-derived masses are expected to be lower limits of the total disk mass due to the assumptions on uncertain dust properties required for their calculation and usually unaccounted for effects such as optical depth and scattering (cite: Miotello_ppvii_2023). Additionally, dynamical estimates of total disk mass have shown typical gas-to-dust ratios $\gtrsim$100 (cite: Lodato_2023_mass_imlup; Martire_2024_stratified_dyn_mass), further indicating that the total disk mass derived from dust measurements should be a lower limit to the actual value.

## Accounting for volatile carbon depletion

The initial abundance of volatile carbon in our models will determine the amount of CO formed in each case. We have shown in the previous sections that this has a significant effect in the extracted vertical CO gas surfaces, with low-carbon models producing shallower emission layers. There is independent observational motivation to assume carbon depletion for our disk sample, as measurements of CO abundance in some of the sources have shown depletion factors of 10-100 from the typically assumed ISM value of $\sim$10$^{-4}$ (cite: Zhang_2019_CO_abundance; MAPS_Zhang).

Figure [7](#final_mass_plot) compares the published masses from various methods (see Table [\[table_sample_all\]](#table_sample_all)) to the derived disk mass from our $z/r$ values, calculated accounting for varying degrees of carbon depletion in the $z/r$ - $M_d$ relationship. For disks that show a large scatter in their literature values we focus on the total disk mass extracted from the dust mass assuming a gas-to-dust ratio of 100 as our main indicator of the expected value, unless a dynamical mass estimate is available in which case we prefer that value.

In some disks it is sufficient to consider a volatile carbon depletion of 10 to match the dust or dynamical masses, however many require carbon depletion of 100 to be in agreement, particularly in the T Tauri systems. We briefly discuss here the case of HD 163296 and MWC 480, which have well constrained CO depletion profiles from optically thin C$^{18}$O and C$^{17}$O emission (cite: MAPS_Zhang). The HD 163296 literature analysis indicates an almost constant CO abundance profile, depleted by a factor 10 with respect to the ISM value beyond $\sim$50 au and MWC 480 follows a similar pattern going towards even lower values of CO depletion beyond $\sim$100 au (cite: MAPS_Zhang). Our analysis indicates that for HD 163296 a global volatile carbon depletion of $\sim$10 is required to match the literature disk mass estimates to those derived from the CO $z/r$. For MWC 480 the preferred carbon depletion from our results ranges between 10-100, also in agreement with the spatially resolved values of (cite: MAPS_Zhang).

For all disks, the inferred total mass we obtain from the characteristic $z/r$, for each carbon depletion value, are presented in Table [\[table_results_mass_CO\]](#table_results_mass_CO) together with the preferred carbon depletion. For the most massive disks, assuming carbon depletion of 100 produces unrealistic disk mass values of $\gtrsim1$M$_{\odot}$ as the extrapolation goes largely beyond our parameter space grid and therefore we do not include these estimations in Table [\[table_results_mass_CO\]](#table_results_mass_CO). The volatile carbon depletion value should be taken with caution, as it is a single order of magnitude approximation based on full-disk model predictions compared to the available dynamical or dust-derived total disk mass. In the optimal scenario it may be a lower limit of the disk integrated volatile carbon depletion with respect to the ISM.

+:----------:+:----------------------:+:-----------------------:+:-----------------------:+:-----------------------:+:----------------:+
| Star       | Characteristic         | Total disk mass \[log$_{\mathrm{10}}$(M$_{\odot}$)\]                        | Preferred        |
|            +------------------------+-------------------------+-------------------------+-------------------------+------------------+
|            | $^{12}$CO $z/r$        | ISM C abundance         | C depletion: 10         | C depletion: 100        | carbon depletion |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| **T Tauri Disks**                                                                                                                    |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| MY Lup     | 0.16$_{-0.05}^{+0.03}$ | -3.52$_{-0.48}^{+0.38}$ | -2.99$_{-0.44}^{+0.37}$ | -2.16$_{-0.44}^{+0.33}$ | 100              |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| AS 209     | 0.21$_{-0.08}^{+0.05}$ | -2.95$_{-0.85}^{+0.53}$ | -2.45$_{-0.81}^{+0.55}$ | -1.67$_{-0.74}^{+0.49}$ | 100              |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| WaOph 6    | 0.30$_{-0.07}^{+0.05}$ | -2.19$_{-0.63}^{+0.34}$ | -1.67$_{-0.64}^{+0.35}$ | -0.97$_{-0.59}^{+0.36}$ | 10               |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| IM Lup     | 0.40$_{-0.05}^{+0.03}$ | -1.55$_{-0.34}^{+0.17}$ | -1.02$_{-0.35}^{+0.18}$ | -0.26$_{-0.39}^{+0.21}$ | 10               |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| GM Aur     | 0.38$_{-0.08}^{+0.05}$ | -1.67$_{-0.56}^{+0.27}$ | -1.13$_{-0.57}^{+0.27}$ | -0.40$_{-0.6}^{+0.32}$  | 10-100           |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| DoAr 25    | 0.24$_{-0.05}^{+0.03}$ | -2.73$_{-0.50}^{+0.32}$ | -2.22$_{-0.49}^{+0.33}$ | -1.48$_{-0.43}^{+0.30}$ | 100              |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| LkCa 15    | 0.25$_{-0.06}^{+0.04}$ | -2.60$_{-0.56}^{+0.34}$ | -2.09$_{-0.56}^{+0.35}$ | -1.36$_{-0.49}^{+0.33}$ | 100              |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| GW Lup     | 0.25$_{-0.11}^{+0.08}$ | -2.60$_{-1.1}^{+0.59}$  | -2.09$_{-1.08}^{+0.6}$  | -1.36$_{-0.96}^{+0.58}$ | 10-100           |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| Sz 91      | 0.12$_{-0.06}^{+0.04}$ | -3.94$_{-0.52}^{+0.47}$ | -3.38$_{-0.46}^{+0.43}$ | -2.54$_{-0.55}^{+0.42}$ | 100              |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| DM Tau     | 0.45$_{-0.09}^{+0.05}$ | -1.27$_{-0.53}^{+0.22}$ | -0.73$_{-0.54}^{+0.23}$ | \-                      | 0                |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| Elias 2-27 | 0.55$_{-0.09}^{+0.05}$ | -0.82$_{-0.49}^{+0.17}$ | -0.27$_{-0.50}^{+0.17}$ | \-                      | 0                |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| **Herbig Disks**                                                                                                                     |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| HD 100546  | 0.19$_{-0.1}^{+0.08}$  | -2.27$_{-1.31}^{+0.74}$ | -1.83$_{-1.09}^{+0.76}$ | -1.14$_{-1.15}^{+0.84}$ | 10               |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| HD 97048   | 0.32$_{-0.07}^{+0.04}$ | -1.14$_{-0.52}^{+0.27}$ | -0.57$_{-0.66}^{+0.41}$ | \-                      | 0                |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| HD 100453  | 0.14$_{-0.09}^{+0.08}$ | -2.83$_{-1.18}^{+0.87}$ | -2.30$_{-1.03}^{+0.76}$ | -1.64$_{-1.06}^{+0.83}$ | 10               |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| HD 34282   | 0.37$_{-0.08}^{+0.04}$ | -0.83$_{-0.49}^{+0.24}$ | -0.14$_{-0.69}^{+0.14}$ | \-                      | 0                |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| MWC 480    | 0.24$_{-0.05}^{+0.04}$ | -1.74$_{-0.53}^{+0.32}$ | -1.31$_{-0.52}^{+0.37}$ | -0.56$_{-0.57}^{+0.41}$ | 10-100           |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| HD 163296  | 0.28$_{-0.04}^{+0.02}$ | -1.42$_{-0.29}^{+0.18}$ | -0.94$_{-0.34}^{+0.23}$ | -0.14$_{-0.39}^{+0.14}$ | 10               |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| HD 142666  | 0.15$_{-0.05}^{+0.05}$ | -2.69$_{-0.65}^{+0.48}$ | -2.19$_{-0.53}^{+0.42}$ | -1.52$_{-0.56}^{+0.45}$ | 10               |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+
| AK Sco     | 0.07$_{-0.05}^{+0.03}$ | -3.82$_{-0.46}^{+0.48}$ | -3.14$_{-0.49}^{+0.43}$ | -2.51$_{-0.48}^{+0.43}$ | 100              |
+------------+------------------------+-------------------------+-------------------------+-------------------------+------------------+

# Discussion

## Low gas-to-dust or high carbon depletion?

It has been previously discussed in the literature that current CO gas models compared to observations do not allow us to distinguish between a low gas-to-dust system (lower gas mass than dust-derived total disk mass) or a high volatile carbon depletion scenario (cite: Miotello_2017; Calahan_2021_HD_TwHya). Our results are in agreement with this entanglement. However we favor the high carbon depletion over low gas-to-dust due to evidence for CO abundance evolution over time in young stars (cite: Bergner_2020_CO; Zhang_2020_CO), measurements of CO depletion in sources from our sample (cite: Zhang_2019_CO_abundance; MAPS_Zhang) and results from dynamical mass estimates that indicate gas-to-dust ratios $\gtrsim$100 (cite: Martire_2024_stratified_dyn_mass) rather than much less than 100.

As discussed in (cite: Miotello_ppvii_2023), various methods can yield orders of magnitude differences in the calculated disk mass. This is particularly apparent for the literature total disk mass values of T Tauri systems MY Lup and GW Lup. For these disks our analysis indicates that a high carbon depletion of $\sim$100 is needed to reach the reported dust-derived mass value, but the reported gas mass, which is several ($\sim$2) orders of magnitude lower in both cases, was extracted without accounting for carbon depletion (cite: Miotello_2017). It is therefore likely that a higher carbon depletion rate would put all values in agreement, an alternative that was suggested by (cite: Miotello_2017) to account for the low gas-to-dust ratios that the measurement would otherwise entail.

We note that for the Herbig sample, the gas mass estimates used in this work were mostly obtained from DALI models of isotopologue CO emission (cite: stapper_2024_gasmass), measuring the fluxes and disk radii in these tracers. These models assumed an ISM volatile carbon abundance, with a parameter space similar to our models. However they obtain mass values higher than the dust-based masses, consistent with a gas-to-dust ratio $\gtrsim$100 (see right panel of Figure [7](#final_mass_plot)). We are confident that carbon depletion must happen at least for MWC 480 and HD 163296, as it has been measured independently through dedicated models and observations (cite: MAPS_Zhang). HD 100546 also has estimates of volatile carbon depletion between 2-10, consistent with our results (cite: Bruderer_2012; Kama_2016_HD100546). The overall discrepancy between our work and analysis using models of CO isotopologue fluxes is the consideration of hydrostatic equilibrium in our models. We show in Figure [13](#lucas_comp_fluxes) that for high disk masses, when the gas emission becomes optically thick, not accounting for hydrostatic equilibrium can underestimate the CO flux, therefore overestimating the calculated disk masses. Due to the optical depth, the use of model fluxes in the high disk mass regime also leads to large uncertainties of up to an order in magnitude in the calculated mass, which also affects the comparison (cite: Miotello_2017; stapper_2024_gasmass). Overall, this highlights the sensitivity of vertical surfaces as a probe for total disk mass and volatile carbon depletion.

While our results are in agreement with most literature works, showing that carbon depletion is present by 1-2 orders of magnitude with respect to ISM levels (see Table [\[table_results_mass_CO\]](#table_results_mass_CO) and previous references), some recent articles have argued that carbon depletion may not be as common in protoplanetary disk systems (cite: Ruaud_2022_CO; Pascucci_2023_CO). The differences between these results and the rest may come from the assumed temperature structure and the effect of considering or not hydrostatic equilibrium (cite: Bosman_2018_CO; Ruaud_2022_CO), which our models account for, similar to those of (cite: Ruaud_2022_CO). Another fundamental difference is the semantics when referring to carbon or CO depletion. In this work, we define carbon depletion as the lack of volatile carbon with respect to ISM levels, which causes a depletion of the CO gas abundance. However, we are agnostic as to what specific mechanism is responsible for depleting the gas phase CO, beyond photodissociation and freeze-out which are included in the DALI standard network (cite: Bruderer_DALI_2013). The models used in (cite: Ruaud_2022_CO) also model photodissociation and freeze-out, but additionally consider the conversion of CO ice to other species, which implies a further reduction in both gas and ice CO abundances from ISM levels, therefore requiring lower levels of depletion.

## Synergy with other methods and comparison to previous studies

Using our $z/r-$$M_d$ relationships can be useful to have an initial idea on the system properties. Contrary to other methods, we are able to utilize a bright and readily detected molecule to have a first-order joint constraint of disk mass and carbon abundance. Indeed, if the calculated $z/r$ is $\geq0.3$ then the total disk mass is $\geq10^{-2}$M$_{\odot}$. For lower $z/r$, the uncertainty on the carbon abundance creates a span of several orders of magnitude in the total disk mass value. However, if gas-to-dust ratio of at least 100 is assumed, which is reasonable from accretion rate values that point towards gas-rich disks (cite: Manara_2016_acc; Manara_2023_ppvii) and dynamical mass estimates (cite: Lodato_2019_H_R; Martire_2024_stratified_dyn_mass), this work has shown that the total mass calculated from the dust continuum flux may be used as an anchor to estimate the lower limit of carbon depletion (see section 3.3).

Combining the information from CO surfaces with dynamical mass estimates, as has been done for a small sample in this work would put strong constraints on the overall carbon depletion during planet formation. Furthermore, the use of rarer CO isotopologues and C-abundance-sensitive tracers such as N$_2$H$^{+}$ has demonstrated to be a good tool to discern between the effects of varying disk mass and volatile carbon depletion (cite: Anderson_2019_N2Hp; Anderson_2022_LupusMass; Trapman_2022_N2Hp). N$_2$H$^{+}$ models have the uncertainty of the disk ionization rate and complication of relying on a fainter molecular line. However, in combination with measurements of the CO vertical profile it could be possible to determine all three parameters, key for understanding protoplanetary disk conditions. We highlight that our results for DM Tau and GM Aur using the CO surface and dust-derived disk masses are in great agreement with the total disk mass and carbon depletion values determined in (cite: Trapman_2022_N2Hp) through N$_2$H$^{+}$ and C$^{18}$O flux analysis and in (cite: McClure_2016_HD) for the HD flux study of DM Tau.

![](zr_COiso_ref.pdf)

Our models may also be used to interpret the observational $z/r - R_{\mathrm{CO}}$ trend, which predicts a relation between the location of the CO emission layer and the CO emission radius of the disk such that more elevated disks also have a larger radial extent (cite: Law_2022_12CO; Law_2023_CO_isotop_surf). Thermochemical models have shown that the radial CO extent is directly related to the total disk mass (cite: Trapman_2024_diskmasssize) and our work finds that $z/r$ also scales with increasing disk mass. Therefore, the observational $z/r - R_{\mathrm{CO}}$ trend reflects on the amount of material contained in the disk. Both vertical and radial extent also depend on carbon abundance, therefore, in a strict interpretation, the observational trend offers information on the total CO gas mass, which can be translated to total disk mass if the carbon abundance is known.

## Caveats and future perspectives

While exciting and very useful for an initial overview of the disk conditions, there are a few caveats to our results. In particular, the studied models have been developed using a full-disk prescription, a standard radial density profile and a single disk-integrated volatile carbon depletion value. However observations show disks with a plethora of substructure (cite: DSHARP_Andrews; Andrews_2020_review; Long_2019_Taurus) and that CO abundance profiles varies radially (cite: Zhang_2019_CO_abundance; MAPS_Zhang). Highly structured or transition disks, which is the case for several disks in our sample, are likely not accurately represented by our models. Future work, beyond the scope of this paper, will test the effect of large cavities and other substructure on the vertical profile and $z/r$-$M_d$ relationship.

We note that emission surfaces obtained at high enough spatial resolution may give direct information on the surface density profile, allowing for a more accurate description of the material distribution without the need to use a characteristic $z/r$ (cite: Paneque_2023_vert). Through this approach, the total disk mass may be more accurately determined and scaled depending on the carbon abundance in a source-by-source analysis, without the uncertainties of general models.

Most importantly, future work must focus on different molecular tracers, such as rarer CO isotopologues and bright optically thin molecules, for example CN and C$_2$H, that have been proposed to be sensitive tracers of the upper disk regions (cite: Cazzoletti_2018_CN; Bergin_2016_c2h; Paneque-Carreno_Elias1; paneque-carreno_2024_IMLup). As a first step towards the analysis of other CO isotopologues and $^{12}$CO transitions, Figure [8](#CO_isotope_test) shows that for ISM-like carbon abundance the vertical layer of $^{13}$CO and C$^{18}$O will be more settled towards the midplane. The challenge in observing less abundant isotopologues is that it is only possible to retrieve optically thick emission surfaces for higher disk masses. An interesting take-away point from Figure [8](#CO_isotope_test) is that within the same isotopologue, different transitions create a negligible variation in the recovered $z/r$, as the emission comes from similar regions. This result is in agreement with previous theoretical studies and models of the vertical distribution of CO in disks (cite: van_zadelhoff_2003). Our results in this work are only applicable to the CO emitting layer. However, it is likely that tracing the vertical structure with other molecular species will give direct insight into varied ongoing disk processes.

# Conclusions

In this work we have presented a $z/r$-$M_d$ relationship, linking the vertical extent of $^{12}$CO $2-1$ to the disk mass and volatile carbon abundance. This was done through the study of thermochemical DALI models, computed accounting for hydrostatic equilibrium. Our models tested the effect of various stellar and disk parameters on the vertical structure and our theoretical predictions were benchmarked on a set of observations. The main findings and conclusions are the following:

1.  We determine that for T Tauri and Herbig systems, the total disk mass and volatile carbon abundance are the main parameters that set the location of the $^{12}$CO $2-1$ emission surface. This surface can be characterized by a constant characteristic $z/r$ tracing the rising portion of the vertical profile.

2.  The $z/r$-$M_d$ relationship for T Tauri systems is different than that of disks around Herbig stars. For the same disk mass and assumed volatile carbon abundance, material around T Tauri stars extends further vertically, as expected due to the difference in the stellar masses and gravitational potential.

3.  Using the total disk masses inferred from continuum dust observations (assuming a gas-to-dust ratio of 100) we are able to calibrate the $z/r$-$M_d$ relationship for each individual system and estimate the order of magnitude of carbon depletion.

4.  Fifteen out of the nineteen studied systems (79%) show indicators of volatile carbon depletion (compared to the ISM abundance). For disks with previous constraints on their carbon abundance, our results yield comparable values. T Tauri disks seem to be more carbon depleted than Herbig systems.

Overall, this study has demonstrated the utility of a bright and readily-detected molecular tracer, $^{12}$CO $2-1$, that may be used to probe two of the most fundamental disk parameters through its vertical extent: total disk mass and carbon abundance. As the sample of disks with high resolution data grows, studies of vertical layering in mid-inclination disks will be used to deepen our understanding not only on the thermal and density conditions, but also on the amount and composition of the materials available for planet formation.

112 natexlab

(ref: Aikawa_2002) Aikawa, Y., van Zadelhoff, G. J., van Dishoeck, E. F., & Herbst, E. 2002, A&A, 386, 622

(ref: Anderson_2019_N2Hp) Anderson, D. E., Blake, G. A., Bergin, E. A., et al. 2019, ApJ, 881, 127

(ref: Anderson_2022_LupusMass) Anderson, D. E., Cleeves, L. I., Blake, G. A., et al. 2022, ApJ, 927, 229

(ref: Andrews_2020_review) Andrews, S. M. 2020, ARA&A, 58, 483

(ref: DSHARP_Andrews) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: andrews_2013_diskmass) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129

(ref: Andrews_2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42

(ref: Ansdell_2018) Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ, 859, 21

(ref: Ansdell_2016_Lupus) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46

(ref: Armitage_2015) Armitage, P. J. 2015, arXiv e-prints, arXiv:1509.06382

(ref: Bae_2023_ppvii) Bae, J., Isella, A., Zhu, Z., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 423

(ref: Barenfeld_2016_uppersco) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, ApJ, 827, 142

(ref: Bergin_2014_CO) Bergin, E. A., Cleeves, L. I., Crockett, N., & Blake, G. A. 2014, Faraday Discussions, 168, 61

(ref: Bergin_2016_c2h) Bergin, E. A., Du, F., Cleeves, L. I., et al. 2016, ApJ, 831, 101

(ref: Bergner_2020_CO) Bergner, J. B., Öberg, K. I., Bergin, E. A., et al. 2020, ApJ, 898, 97

(ref: booth_2023_hd100546) Booth, A. S., Ilee, J. D., Walsh, C., et al. 2023, A&A, 669, A53

(ref: BoothA_2019_13C17O) Booth, A. S., Walsh, C., Ilee, J. D., et al. 2019, ApJL, 882, L31

(ref: Bosman_2018_CO) Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 618, A182

(ref: Brown-Sevilla_2021) Brown-Sevilla, S. B., Keppler, M., Barraza-Alfaro, M., et al. 2021, A&A, 654, A35

(ref: Bruderer_DALI_2013) Bruderer, S. 2013, A&A, 559, A46

(ref: Bruderer_2012) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541, A91

(ref: Calahan_2021_HD_TwHya) Calahan, J. K., Bergin, E., Zhang, K., et al. 2021, ApJ, 908, 8

(ref: Cazzoletti_2018_CN) Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018, A&A, 609, A93

(ref: Dalessio_1998) D’Alessio, P., Cantö, J., Calvet, N., & Lizano, S. 1998, ApJ, 500, 411

(ref: Dartois_2003_DMTau) Dartois, E., Dutrey, A., & Guilloteau, S. 2003, A&A, 399, 773

(ref: Diop_2024_CO_ML) Diop, A., Cleeves, L. I., Anderson, D. E., Pegues, J., & Plunkett, A. 2024, ApJ, 962, 90

(ref: Dutrey_2017_flyingsaucer) Dutrey, A., Guilloteau, S., Piétu, V., et al. 2017, A&A, 607, A130

(ref: Fairlamb_2015) Fairlamb, J. R., Oudmaijer, R. D., Mendigutı́a, I., Ilee, J. D., & van den Ancker, M. E. 2015, MNRAS, 453, 976

(ref: Favre_2013_lowCO) Favre, C., Cleeves, L. I., Bergin, E. A., Qi, C., & Blake, G. A. 2013, ApJL, 776, L38

(ref: Flaherty_2015_hd16_weakturb) Flaherty, K. M., Hughes, A. M., Rosenfeld, K. A., et al. 2015, ApJ, 813, 99

(ref: emcee_ref) Foreman-Mackey, D., Farr, W., Sinha, M., et al. 2019, The Journal of Open Source Software, 4, 1864

(ref: Gorti_2008_CO) Gorti, U. & Hollenbach, D. 2008, ApJ, 683, 287

(ref: Hartmann_2016) Hartmann, L., Herczeg, G., & Calvet, N. 2016, ARA&A, 54, 135

(ref: Hernandez-Vera_2024_H2CO_HD16) Hernández-Vera, C., Guzmán, V. V., Artur de la Villarmois, E., et al. 2024, ApJ, 967, 68

(ref: Hildebrand_1983_dustmass) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: DSHARP_Huang_radial) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42

(ref: Izquierdo_2023_discminer2) Izquierdo, A. F., Testi, L., Facchini, S., et al. 2023, A&A, 674, A113

(ref: Kama_2016_HD100546) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83

(ref: Kama_2020_HD) Kama, M., Trapman, L., Fedele, D., et al. 2020, A&A, 634, A88

(ref: Krijt_2020) Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134

(ref: Krijt_2016) Krijt, S., Ciesla, F. J., & Bergin, E. A. 2016, ApJ, 833, 285

(ref: Krijt_2018) Krijt, S., Schwarz, K. R., Bergin, E. A., & Ciesla, F. J. 2018, ApJ, 864, 78

(ref: Kurtovic_2024_MHO6) Kurtovic, N. T. & Pinilla, P. 2024, A&A, 687, A188

(ref: Law_2023_CI) Law, C. J., Alarcón, F., Cleeves, L. I., Öberg, K. I., & Paneque-Carreño, T. 2023a, ApJL, 959, L27

(ref: Law_2022_12CO) Law, C. J., Crystian, S., Teague, R., et al. 2022, ApJ, 932, 114

(ref: MAPS_Law_radial) Law, C. J., Loomis, R. A., Teague, R., et al. 2021a, ApJS, 257, 3

(ref: MAPS_Law_Surf) Law, C. J., Teague, R., Loomis, R. A., et al. 2021b, ApJS, 257, 4

(ref: Law_2023_CO_isotop_surf) Law, C. J., Teague, R., Öberg, K. I., et al. 2023b, ApJ, 948, 60

(ref: leemker_2022_LkCa15) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2022, A&A, 663, A23

(ref: Lodato_2019_H_R) Lodato, G., Dipierro, G., Ragusa, E., et al. 2019, MNRAS, 486, 453

(ref: Lodato_2023_mass_imlup) Lodato, G., Rampinelli, L., Viscardi, E., et al. 2023, MNRAS, 518, 4481

(ref: Long_2022_disksize) Long, F., Andrews, S. M., Rosotti, G., et al. 2022a, ApJ, 931, 6

(ref: Long_2022_lagrangian) Long, F., Andrews, S. M., Zhang, S., et al. 2022b, ApJL, 937, L1

(ref: Long_2019_Taurus) Long, F., Herczeg, G. J., Harsono, D., et al. 2019, ApJ, 882, 49

(ref: Lynden_Bell_Pringle_1974) Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: Manara_2023_ppvii) Manara, C. F., Ansdell, M., Rosotti, G. P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 539

(ref: Manara_2016_acc) Manara, C. F., Rosotti, G., Testi, L., et al. 2016, A&A, 591, L3

(ref: Martire_2024_stratified_dyn_mass) Martire, P., Longarini, C., Lodato, G., et al. 2024, arXiv e-prints, arXiv:2402.12236

(ref: McClure_2016_HD) McClure, M. K., Bergin, E. A., Cleeves, L. I., et al. 2016, ApJ, 831, 167

(ref: Merin_2004) Merı́n, B., Montesinos, B., Eiroa, C., et al. 2004, A&A, 419, 301

(ref: Miotello_2014) Miotello, A., Bruderer, S., & van Dishoeck, E. F. 2014, A&A, 572, A96

(ref: Miotello_ppvii_2023) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501

(ref: miotello_2016) Miotello, A., van Dishoeck, E. F., Kama, M., & Bruderer, S. 2016, A&A, 594, A85

(ref: Miotello_2017) Miotello, A., van Dishoeck, E. F., Williams, J. P., et al. 2017, A&A, 599, A113

(ref: Molyarova_2017_CO) Molyarova, T., Akimkin, V., Semenov, D., et al. 2017, ApJ, 849, 130

(ref: Oberg_2023_chemreview) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287

(ref: MAPS_Oberg) Öberg, K. I., Guzmán, V. V., Walsh, C., et al. 2021, ApJS, 257, 1

(ref: paneque-carreno_2024_IMLup) Paneque-Carreño, T., Izquierdo, A. F., Teague, R., et al. 2024, A&A, 684, A174

(ref: Paneque-Carreno_2022_Elias_CN) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2022, A&A, 666, A168

(ref: Paneque_2023_vert) Paneque-Carreño, T., Miotello, A., van Dishoeck, E. F., et al. 2023, A&A, 669, A126

(ref: Paneque-Carreno_Elias1) Paneque-Carreño, T., Pérez, L. M., Benisty, M., et al. 2021, ApJ, 914, 88

(ref: Pascucci_2023_CO) Pascucci, I., Skinner, B. N., Deng, D., et al. 2023, ApJ, 953, 183

(ref: pascucci_2016_diskmass) Pascucci, I., Testi, L., Herczeg, G. J., et al. 2016, ApJ, 831, 125

(ref: Pegues_2020) Pegues, J., Öberg, K. I., Bergner, J. B., et al. 2020, ApJ, 890, 142

(ref: Perez_2018_DSHARP) Pérez, L. M., Benisty, M., Andrews, S. M., et al. 2018, ApJL, 869, L50

(ref: Perez_2020_hd100546) Pérez, S., Casassus, S., Hales, A., et al. 2020, ApJL, 889, L24

(ref: Pinte_2018_method) Pinte, C., Ménard, F., Duchêne, G., et al. 2018, A&A, 609, A47

(ref: Pinte_2023_ppvii) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645

(ref: Ragusa_2017_horseshoes) Ragusa, E., Dipierro, G., Lodato, G., Laibe, G., & Price, D. J. 2017, MNRAS, 464, 1449

(ref: Rampinelli_2024_PDS70) Rampinelli, L., Facchini, S., Leemker, M., et al. 2024, A&A, 689, A65

(ref: Rich_2021) Rich, E. A., Teague, R., Monnier, J. D., et al. 2021, ApJ, 913, 138

(ref: Rosotti_2020) Rosotti, G. P., Benisty, M., Juhász, A., et al. 2020, MNRAS, 491, 1335

(ref: Rosotti_2019) Rosotti, G. P., Tazzari, M., Booth, R. A., et al. 2019, MNRAS, 486, 4829

(ref: Ruaud_2022_CO) Ruaud, M., Gorti, U., & Hollenbach, D. J. 2022, ApJ, 925, 49

(ref: RuizRodriguez_2021) Ruı́z-Rodrı́guez, D., Kastner, J., Hily-Blant, P., & Forveille, T. 2021, A&A, 646, A59

(ref: Sanchis_2021) Sanchis, E., Testi, L., Natta, A., et al. 2021, A&A, 649, A19

(ref: Schwarz_2016_CO_TWHya) Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2016, ApJ, 823, 91

(ref: sierra_2021_MAPS) Sierra, A., Pérez, L. M., Zhang, K., et al. 2021, ApJS, 257, 14

(ref: stapper_2024_gasmass) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., et al. 2024, A&A, 682, A149

(ref: stapper_2022_dustmass) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., & Mentel, R. 2022, A&A, 658, A112

(ref: Stapper_2023_Herbig_surf) Stapper, L. M., Hogerheijde, M. R., van Dishoeck, E. F., & Paneque-Carreño, T. 2023, A&A, 669, A158

(ref: Tazzari_2021_dustsizes) Tazzari, M., Clarke, C. J., Testi, L., et al. 2021, MNRAS, 506, 2804

(ref: MAPS_Teague) Teague, R., Bae, J., Aikawa, Y., et al. 2021a, ApJS, 257, 18

(ref: disksurf) Teague, R., Law, C., Huang, J., & Meng, F. 2021b, The Journal of Open Source Software, 6, 3827

(ref: Temmink_2023_HD142527) Temmink, M., Booth, A. S., van der Marel, N., & van Dishoeck, E. F. 2023, A&A, 675, A131

(ref: Trapman_2023_disksize) Trapman, L., Rosotti, G., Zhang, K., & Tabone, B. 2023a, ApJ, 954, 41

(ref: Trapman_2024_diskmasssize) Trapman, L., Rosotti, G., Zhang, K., & Tabone, B. 2023b, ApJ, 954, 41

(ref: Trapman_2022_N2Hp) Trapman, L., Zhang, K., van’t Hoff, M. L. R., Hogerheijde, M. R., & Bergin, E. A. 2022, ApJL, 926, L2

(ref: Tsukagoshi_2019) Tsukagoshi, T., Momose, M., Kitamura, Y., et al. 2019, ApJ, 871, 5

(ref: Urbina_2024_CI) Urbina, F., Miley, J., Kama, M., & Keyte, L. 2024, A&A, 686, A120

(ref: van_der_Tak_2007_RADEX) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: van_zadelhoff_2003) van Zadelhoff, G. J., Aikawa, Y., Hogerheijde, M. R., & van Dishoeck, E. F. 2003, A&A, 397, 789

(ref: Veronesi_2021_Elias) Veronesi, B., Paneque-Carreño, T., Lodato, G., et al. 2021, ApJL, 914, L27

(ref: Villenave_2020) Villenave, M., Ménard, F., Dent, W. R. F., et al. 2020, A&A, 642, A164

(ref: Villenave_2023) Villenave, M., Podio, L., Duchêne, G., et al. 2023, ApJ, 946, 70

(ref: Visser_2009_CO) Visser, R., van Dishoeck, E. F., & Black, J. H. 2009, A&A, 503, 323

(ref: woitke_2016_prodimo) Woitke, P., Min, M., Pinte, C., et al. 2016, A&A, 586, A103

(ref: Young_2021_warp) Young, A. K., Alexander, R., Walsh, C., et al. 2021, MNRAS, 505, 4821

(ref: Yu_2016_CO) Yu, M., Willacy, K., Dodson-Robinson, S. E., Turner, N. J., & Evans, Neal J., I. 2016, ApJ, 822, 53

(ref: Zhang_2019_CO_abundance) Zhang, K., Bergin, E. A., Schwarz, K., Krijt, S., & Ciesla, F. 2019, ApJ, 883, 98

(ref: MAPS_Zhang) Zhang, K., Booth, A. S., Law, C. J., et al. 2021, ApJS, 257, 5

(ref: Zhang_2020_CO) Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJL, 891, L17

# Acknowledgements

This paper makes use of the following ALMA data: #2015.1.00192.S, #2015.1.00168.S, #2016.1.00344.S, #2016.1.00204.S, #2016.1.00484.L, #2016.1.00606.S, #2017.1.00069.S and #2018.1.01055.L ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. Astrochemistry in Leiden is supported by the Netherlands Research School for Astronomy (NOVA), and by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK). GPR acknowledges support from the European Union (ERC Starting Grant DiscEvol, project number 101039651) and from Fondazione Cariplo, grant No. 2022-1217. Views and opinions expressed are, however, those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them.

# Full emission surfaces from models and observational sample

In the main text our results are expressed in $z/r$. For visual comparison, here we show the full vertical profiles extracted for the CO emission surfaces in models and observations. Figures [9](#vary_param_appendix_M1e-2) and [10](#vary_param_appendix_M1e-3) show the emission surfaces tracing the $\tau=1$ layer, as extracted from the DALI model output of the fiducial models and models varying specific parameters (see Table [2](#table_DALI_varyparam) for details).

Figures [11](#ttauri_obs) and [12](#herbig_obs) display the emission surfaces extracted from the CO channel map emission of each disk using ALFAHOR (cite: Paneque_2023_vert; Stapper_2023_Herbig_surf). For comparison, the location of the $\tau=1$ layer from the fiducial models using $R_c = 100$ au of each sampled disk mass are plotted in each panel.

![](models_vary_param_0.01.pdf)

![](models_vary_param_0.001.pdf)

![](ttauri_obs_comparison.pdf)

![](herbig_obs_comparison.pdf)

# CO isotopologue model fluxes using hydrostatic equilibrium solver

When using the hydrostatic equilibrium solver in DALI, the disk density converges to a physical structure given by the equilibrium between the stellar gravitational potential and the thermal structure. The disk integrated fluxes may vary when comparing the hydrostatic equilibrium output to the models with static gaussian distributions. For optically thin emission in low-mass disks, the fluxes will be larger in the static models, which means the disk masses will be underestimated in comparison to those obtained from model fluxes when hydrostatic equilibrium is considered. In the case of high-mass disks the reverse happens, the static gaussian models underestimate the fluxes, therefore overestimate the disk masses.

Figure [13](#lucas_comp_fluxes) shows this effect displaying the total flux difference and percentual variation. This flux variation explains the generally higher masses of (cite: stapper_2024_gasmass) and the lower masses obtained by (cite: Miotello_2017) for MY Lup and GW Lup compared to our mass values assuming an ISM carbon abundance (see Fig. [7](#final_mass_plot)).

![](comp_lucas_herbig.pdf)

</paper>

Write the methods card for this paper.