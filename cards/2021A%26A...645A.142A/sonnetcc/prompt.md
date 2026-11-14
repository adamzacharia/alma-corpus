# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...645A.142A\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...645A.142A",
 "title": "Continuity of accretion from clumps to Class 0 high-mass protostars in SDC335",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Avison, A.",
 "n_authors": 9,
 "arxiv_id": "2012.08948",
 "doi": "10.1051/0004-6361/201936043",
 "alma_projects_linked_by_archive": [
  "2011.0.00474.S",
  "2012.1.00781.S"
 ]
}
```

Paper text:
<paper>
# Continuity of accretion from clumps to Class 0 high-mass protostars in SDC335[^2]

The infrared dark cloud (IRDC) SDC335.579-0.292 (hereafter, SDC335) is a massive ($\sim$5000M$_{\odot}$) star-forming cloud which has been found to be globally collapsing towards one of the most massive star forming cores in the Galaxy, which is located at its centre. SDC335 is known to host three high-mass protostellar objects at early stages of their evolution and archival ALMA Cycle 0 data (at $\sim$5$^{\prime\prime}$ resolution) indicate the presence of at least one molecular outflow in the region detected in HNC. Observations of molecular outflows from massive protostellar objects allow us to estimate the accretion rates of the protostars as well as to assess the disruptive impact that stars have on their natal clouds during their formation.

The aim of this work is to identify and analyse the properties of the protostellar-driven molecular outflows within SDC335 and use these outflows to help refine the properties of the young massive protostars in this cloud.

We imaged the molecular outflows in SDC335 using new data from the Australia Telescope Compact Array (ATCA) of SiO and Class I CH$_3$OH maser emission (at a resolution of $\sim$3$^{\prime\prime}$) alongside observations of four CO transitions made with the Atacama Pathfinder EXperiment (APEX) and archival Atacama Large Millimeter/submillimeter Array (ALMA) CO, $^{13}$CO ($\sim$1$^{\prime\prime}$), and HNC data. We introduced a generalised argument to constrain outflow inclination angles based on observed outflow properties. We then used the properties of each outflow to infer the accretion rates on the protostellar sources driving them. These accretion properties allowed us to deduce the evolutionary characteristics of the sources. Shock-tracing SiO emission and CH$_3$OH Class I maser emission allowed us to locate regions of interaction between the outflows and material infalling to the central region via the filamentary arms of SDC335.

We identify three molecular outflows in SDC335 – one associated with each of the known compact HII regions in the IRDC. These outflows have velocity ranges of $\sim10$ kms$^{-1}$ and temperatures of $\sim60$ K. The two most massive sources (separated by $\sim$9000AU) have outflows with axes which are, in projection, perpendicular. A well-collimated jet-like structure with a velocity gradient of $\sim$155kms$^{-1}$pc$^{-1}$ is detected in the lobes of one of the outflows. The outflow properties show that the SDC335 protostars are in the early stages (Class 0) of their evolution, with the potential to form stars in excess of 50M$_{\odot}$. The measured total accretion rate, inferred from the outflows, onto the protostars is $1.4(\pm 0.1) \times 10^{-3}$M$_{\odot}$ yr$^{-1}$, which is comparable to the total mass infall rate toward the cloud centre on parsec scales of 2.5$(\pm1.0) \times 10^{-3}$M$_{\odot}$ yr$^{-1}$, suggesting a near-continuous flow of material from cloud to core scales.

Finally, we identify multiple regions where the outflows interact with the infalling material in the cloud’s six filamentary arms, creating shocked regions and pumping Class I methanol maser emission. These regions provide useful case studies for future investigations of the disruptive effect of young massive stars on their natal clouds.

# Introduction

Molecular outflows are a commonly observed feature of the star-formation process detected toward protostars that will ultimately form stars covering a wide range of main sequence masses up to spectral type B ($M_*\sim10$M$_{\odot}$) and beyond. The driving force responsible for such bipolar molecular outflows is thought to be the accretion of matter onto the central protostellar object from a disk coupled with the requirement for angular momentum to be conserved in the process (cite: Konigl00; Pudritz07; Tan14; RosenOffner20). The effects of limited resolution and obscuration impede the testing of theories of the exact physical mechanism driving these outflows observationally, be it X-wind or disk-wind driven (cite: PudritzBanerjee05; Pudritz07; Frank14), and the extent to which magnetic fields play a role. The breadth of the scales of molecular outflows, compared to the region from which they are driven, make them an invaluable tool when testing star formation theories. For example, they can be used to indirectly probe the accretion rates of material onto forming protostars (cite: BontempsOutflow96; Ana13).

In addition to providing information on the protostars that drive them, outflows also have an impact on their natal clouds by entraining matter as they inject energy and momentum into the surrounding interstellar medium (ISM)(cite: Offner17). This feedback may drive turbulence and ultimately help to disrupt the cloud. These effects have implications for the number and masses of stars (i.e. the initial mass function) which can form within a single molecular cloud (cite: Ana12; Plunkett13; Krumholz14; ZhangY15; Drabek-Maunder16). As a result, the observation of molecular outflows toward candidate high-mass protostars provides valuable information on the poorly constrained formation processes of such objects and their effects on the environments in which they form.

The Infrared Dark Cloud (IRDC) SDC335.579-0.292 (cite: Peretto09) (hereafter, SDC335) is an increasingly well-studied star-forming region (cite: Garay02; Peretto13; Avison15) harbouring one of the most massive millimetre cores observed in the Milky Way. Seen in absorption against the mid-infrared background, SDC335 covers approximately 2.4pc at its widest extent and displays six filamentary arms, which converge at the bright infrared source at its centre.

Using the Atacama Large Millimeter/submillimeter Array (ALMA) Cycle 0 data, (cite: Peretto13) demonstrated that the whole SDC335 cloud is in the process of global collapse and that gas (traced by N$_2$H$^+$) is flowing along the filamentary arms towards this central region. ALMA continuum data at 3mm also highlighted two mm-cores, MM1 and MM2, with $M_{core}\sim$500 and 50M$_{\odot}$, respectively (cite: Peretto13). These data also included HNC observations indicating the presence of a molecular outflow from the MM1 core, however, that outflow has not been studied prior to this work.

(cite: Avison15), (hereafter, Paper I) used radio continuum data from the Australia Telescope Compact Array (ATCA) (from 6 to 25 GHz) to reveal that the MM1 core houses two Hyper Compact HII (HCHII) regions, whilst MM2 contains a single source, which also exhibits characteristics of an HCHII region. Each HCHII source was coincident with a Class II methanol (CH$_3$OH) maser, the pair of tracers clearly demonstrating SDC335 is in the process of forming three massive stars (each with $M_* > 9.0$M$_{\odot}$, based on their calculated Lyman $\alpha$ flux). Using this constraint on the upper end of the mass range in SDC335, the authors estimate a final stellar population in SDC335 of $\sim$1400 ($M_* > 0.08$M$_{\odot}$, assuming a (cite: Kroupa02) IMF), suggesting that SDC335 could be a precursor to a massive cluster such as the Trapezium Cluster.

In this paper, we report on the molecular outflows observed in SDC335, which are likely to have been launched by the massive protostars therein. We present the observed molecular species and observations used to study the molecular outflows in SDC335 in Section 2. Section 3 describes the detected outflow properties and how they were measured. In Section 4, we discuss the measured properties and how this relates to the evolutionary status of the SDC335 high-mass protostellar objects. In Section 5, we discuss evidence for outflow-filament interactions. We present our conclusions and summarise our findings in Section 6.

# Observations and ancillary data

+:----------------------------------------+:-----------+:------------------------------------------------:+:---------------------:+:----------------------:+:--------------------------:+:------------+:------------------------+:------------+
| Molecule                                | Obs. Freq. | Beam                                             | MRS$^{\star}$         | Chan. Width            | Sensitivity$^{\star\star}$ | Calibrators                                         |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                         | \[GHz\]    | \[$^{\prime\prime}$ $\times$ $^{\prime\prime}$\] | \[$^{\prime\prime}$\] | \[MHz\]/\[kms$^{-1}$\] | \[mJy/bm\] / \[K\]         | Amplitude   | $\phi$                  | Bandpass    |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                                                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Telescope: ATCA                                                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                                                                                                                                                                                             |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| SiO (1$\rightarrow$0)                   | 43.42385   | 3.1 $\times$ 1.3                                 | 23.3                  | 0.125 / 0.86           | 4.3                        | PKS1934-638 | PKS1646-50$^{\ddagger}$ | PKS1253-055 |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| CH$_3$OH (7$\rightarrow$6)              | 44.06941   | 2.0 $\times$ 1.1                                 | 23.0                  | 0.0313 / 0.21          | 9.3                        | PKS1934-638 | PKS1646-50              | PKS1253-055 |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                                                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Telescope: ALMA                                                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                                                                                                                                                                                             |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| HNC (1$\rightarrow$0)                   | 90.66357   | 5.5 $\times$ 3.9                                 | 22.4                  | 0.0665 / 0.22          | 14.0                       | Neptune,    | J1604-446               | J1517-2422  |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                         |            |                                                  |                       |                        |                            | Mercury     |                         |             |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| $^{13}$CO (3$\rightarrow$2)$^{\dagger}$ | 330.58797  | 0.82 $\times$ 0.58                               | 10.5                  | 0.243 /0.22            | 23.5                       | Mars,       | J1650-5044$^{\ddagger}$ | J1337-1257, |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                         |            |                                                  |                       |                        |                            | Titan,      |                         | J1427-4206, |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                         |            |                                                  |                       |                        |                            | J1613-586   |                         | J1650-5044  |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                         |            |                                                  |                       |                        |                            |             |                         | J1924-2914  |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| CO (3$\rightarrow$2)$^{\dagger}$        | 345.79599  | 0.72 $\times$ 0.54                               | 11.8                  | 0.254 /0.22            | 22.0                       | Titan       | J1650-5044,             | J1427-4026, |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                         |            |                                                  |                       |                        |                            | J1613-586   | J1517-2422              |             |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
|                                                                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Telescope: APEX                                                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|                                                                                                                                                                                                                                             |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| CO (3$\rightarrow$2)                    | 345.7960   | 19.16                                            | \-                    | 0.114 / 0.10           | 1.10                       | \-          | \-                      | \-          |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| CO (4$\rightarrow$3)                    | 461.0408   | 14.37                                            | \-                    | 0.290 / 0.15           | 1.70                       | \-          | \-                      | \-          |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| CO (6$\rightarrow$5)                    | 691.4731   | 9.58                                             | \-                    | 1.464 / 0.64           | 1.20                       | \-          | \-                      | \-          |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+
| CO (7$\rightarrow$6)                    | 806.6518   | 8.21                                             | \-                    | 2.929 / 1.09           | 2.20                       | \-          | \-                      | \-          |
+-----------------------------------------+------------+--------------------------------------------------+-----------------------+------------------------+----------------------------+-------------+-------------------------+-------------+

**Notes:** $^{(\dagger)}$ALMA + ACA combined data.\
$^{(\star)}$ Maximum Recoverable Scale of emission, $MRS\sim0.6\frac{\lambda}{b_{min}}$, where ${b_{min}}$ is the shortest baseline in an array.\
$^{(\ddagger)}$ PKS1646-50 and J1650-5044 are the same source under different naming conventions.\
$^{(\star\star)}$ Unit mJy/bm for ATCA and ALMA, and K for APEX. Measured in a velocity width matching the channel width.

Molecular line emission is key to understanding the morphologies and, more importantly, the kinematics and dynamic interactions of protostellar outflows. We present the results of SiO and Class I methanol (CH$_3$OH) maser observations made with ATCA toward SDC335 in combination with APEX[^3] and archival ALMA data, observing lines of CO, $^{13}$CO (ALMA only), and HNC (ALMA only), which allow us to study the outflows and their disruptive effects. Silicon monoxide, SiO, is depleted in the gas phase of the ISM (cite: Walmsley99), but it can be liberated from the grain mantels by shock fronts arising in molecular outflows (cite: Schilke97), making it a useful tool for studying outflows (cite: Cabral14) particularly at outflow-cloud interaction points.

Similarly, the Class-I CH$_3$OH maser (at 44 GHz) is regularly used as a tracer of outflows, (cite: Cyganowski09; Cyganowski11) as it is a collisionally excited maser species. Class-I CH$_3$OH masers are frequently seen as spatially offset from the local protostellar source, unlike the radiatively pumped Class-II CH$_3$OH maser species, lending support to the idea that the Class-I species is being excited in regions of interaction between outflowing material and the surrounding molecular material (cite: Plambeck90; Kurtz04; Vornokov10). These lines and the observations characteristics are listed in Table [\[Obs_props:tab\]](#Obs_props:tab).

Finally, CO, being ubiquitous in the ISM, provides sufficient molecular abundance to trace the high velocity gas entrained by the outflows. Thus, it is a good tracer of the large scale molecular outflow morphology, something that is not possible when observing shock-tracing species.

## ATCA data

The ATCA data were taken in a single 12.5 hour observing block on 3 September 2015 under the project code C3023. These observations comprised two 2 GHz continuum bands within which four 64 MHz zoom bands were placed using the CABB correlator (cite: CABBpaper). The primary target molecular lines used from these data are SiO (1-0) and the Class-I CH$_3$OH maser transition.

These observations were taken with ATCA in the ‘750B’ antenna configuration. During the data reduction, all baselines to the antenna at 6.0km from the array centre were flagged out, meaning that these data have maximum and minimum baselines of 765.3 and 61.2m, respectively. Data reduction was carried out in the software package `MIRIAD` using standard ATNF calibration and imaging strategies[^4]. We note that poor atmospheric conditions at the start of observing meant that approximately four hours of data were entirely flagged from the start of the run, limiting the total observing time on source to $\sim$ 4.7 hours and setting the theoretical sensitivity to $\sim$5.64mJy/beam per 31.25kHz channel.

## ALMA Band 7 data

We use data taken from the ALMA archive, which forms part of the Cycle 1 observing program 2012.0.00781.S. For this work, we used the 12- and 7-m array observations at 330.64GHz and 345.874GHz, which cover the $^{13}$CO(3-2) and CO(3-2) transitions, respectively.

These observations comprise a 39 pointing Nyquist sampled rectangular mosaic of the central region of SDC335, which is sufficient to cover the three HCHII regions observed in , with the 12-m array. This mosaic has a spatial extent of 65$^{\prime\prime}$$\times$68$^{\prime\prime}$  centred at RA = 16h30m58.550s, Dec = $-$48$^{\circ}$43$^{\prime}$54.00$^{\prime\prime}$. The 7-m data had a complementary 14 point mosaic pattern covering 74.6$^{\prime\prime}$$\times$69$^{\prime\prime}$ centred at the same position, such that the whole 12-m mosaic region was covered (and fractionally exceeded). The data were downloaded from the archive, reprocessed, and the 12- and 7-m data were combined as per ALMA recommendations[^5] in the data reduction package CASA (cite: CASAREF), with a continuum subtraction applied.

For the $^{13}$CO data, the array was configured with minimum and maximum baselines of 10.7 and 1284.1m, respectively [^6]. During the CO observations the minimum and maximum baselines were 9.1 and 437.8m, respectively. The synthesised beam sizes of these data are given in Table [\[Obs_props:tab\]](#Obs_props:tab).

## ALMA Band 3 data

ALMA Cycle 0 project 2011.0.00474.S was an 11 pointing mosaic observation at 90 GHz, covering the whole IRDC cloud seen in extinction against the mid-infrared background at 8$\mu$m from *Spitzer* (see Figure [1](#PressyFig:fig) and Figure 1 of (cite: Peretto13)). The continuum and N$_2$H$^+$ from these data were originally published in (cite: Peretto13), though the line of interest in this current work, HNC, was not. The data were taken with 16 12-m antennas with no 7-m data taken (as this was not available with ALMA at the time). The array had maximum and minimum baselines of 18.3 and 197.7m.

## APEX CO data

Single dish observations were made with the APEX telescope covering CO transitions (3-2), (4-3), (6-5) and (7-6). The observations of CO J=4-3 (at 461.04077 GHz) and J=3-2 (at 345.79599 GHz) were taken with the FLASH+ dual-channel receiver (cite: 2014ITTST...4..588K) on 3-4 June 2013. At the J=3-2 transition the average system temperature was $300$ K giving a typical root mean square (RMS) of 1.1 K in 0.1 km/s channels. For the J=4-3 transition, the average system temperature was 1276 K, giving an average noise of 1.7 K in channels of a velocity width of 0.15 km/s. The data was sampled on a 3$^{\prime\prime}$ grid and then regridded during the data reduction to a resolution of 19.2$^{\prime\prime}$ and 14.4$^{\prime\prime}$ full width half maximum for the J=3-2 and J=4-3 observations, respectively. The emission at the (3-2) and (4-3) transitions shown in Figure [2](#OUTFLOW_GRID:fig)-D.

The CO transitions of J=6-5 (at 691.473076 GHz) and J=7-6 (at 806.651806 GHz) were observed simultaneously with the seven-pixel CHAMP+(cite: 2006SPIE.6275E..0NK; 2008SPIE.7020E..10G) dual channel receiver on 30 May 2013. The (7-6) transition data were convolved to a grid with a 9.6$^{\prime\prime}$ resolution during reduction to match the resolution of the (6-5) transition as shown in Figure [2](#OUTFLOW_GRID:fig)-E. The RMS noise level across the maps was 1.2 K in 0.64 km/s channels and 2.2 K in 1.1 km/s channels for the lower and higher frequency transitions, respectively.

![](SubmissionFigsPDFs/Final_Pressy_2019.pdf)

# Outflow identification

To identify potential outflows within our data, a continuum subtracted data cube was created for each molecular line. These cubes have a velocity range from $-$100 to 0 kms$^{-1}$  which is sufficient to cover the whole kinematic range of the observed species given the $V_{lsr}$ of the target. The MM1 core has a $V_{lsr}$ of $-$46.6kms$^{-1}$ and for MM2 $V_{lsr}$ = $-$46.5kms$^{-1}$ (cite: Peretto13). The $V_{lsr}$ of the compact radio cores observed by are consistent with those of the mm-cores based on their associated Class II (6.7-GHz) methanol masers, MM1*a* $V_{\rm{CH_3OH}}$=$-$48.0 to $-$45.0kms$^{-1}$, MM1*b* $V_{\rm{CH_3OH}}$=$-$56.0 to $-$50.0kms$^{-1}$ and MM2 $V_{\rm{CH_3OH}}$=$-$51.0 to $-$43.0kms$^{-1}$(cite: MMB330to345), and the observed modulus offsets between molecular gas and peak maser emission of $\sim$ 3 to 4 kms$^{-1}$ (cite: Szymczak07; Pandian09; GreenMcClure11). As such, we adopted a $V_{lsr}$ of $-$46.6kms$^{-1}$ for MM1*a* and MM1*b* and $-$46.5kms$^{-1}$ for MM2 in line with the mm-core values.

Using these cubes, the velocity ranges of each identified outflow for each molecular species were found by visual inspection and are listed in Table [1](#OutflowCalc:tab), (defined as the absolute offset from $V_{lsr}$ to the last channel with a 3$\sigma$ detection). Emission close to the $V_{lsr}$ of the system is complex, particularly in the ALMA CO maps. As such, we implemented velocity range limits for our interpretation of the structures in SDC335. For all species, except CO, we excluded emission $\pm5$kms$^{-1}$from the $V_{lsr}$. For calculations of outflow properties with CO we use a larger velocity offset from the $V_{lsr}$ as described in Section [3.2.4](#DerivProps:sec). The velocity ranges used for each outflow by species are given in Table [1](#OutflowCalc:tab). We then generated integrated intensity maps over these velocity ranges from which we measured the observed spatial extent and opening angles of each outflow wing.

Within the multiple datasets presented in this paper, there are three distinct molecular outflows observed within SDC335. We label these A, B, and C and we describe their respective morphologies, along with the identification of their likely progenitor protostars in Section [3.1](#OutDescript:sec). Figure [1](#PressyFig:fig) shows components of each outflow superimposed on a *Spitzer* IRAC three colour image of the SDC335 IRDC to highlight their spatial extent within the larger scale cloud. Figure [2](#OUTFLOW_GRID:fig) presents the morphology of each outflow as observed in CO, $^{13}$CO  HNC (from ALMA), SiO (from ATCA), and CO from APEX. In Figures [3](#OUTA_SPEC_blue:fig) to [6](#OUTC_SPEC:fig), we present the spectra of each detected line from each outflow within the interferometric data. We also present spectra over the same velocity range as the outflows (-100 to 0 kms$^{-1}$) at the peak position of each of the three HCHII at the CO, $^{13}$CO, HNC, and SiO tunings in Appendix [7](#HCHII_SPEC:app) as Figures [20](#MM1a_SPEC:fig) to [22](#MM2_SPEC:fig).

![](SubmissionFigsPDFs/OutFlowGrid3b2_2020FINAL.pdf)

![](SubmissionFigsPDFs/OUTA_SPEC_blue.pdf)

![](SubmissionFigsPDFs/OUTA_SPEC_red.pdf)

![](SubmissionFigsPDFs/OUTB_SPEC.pdf)

![](SubmissionFigsPDFs/OUTC_SPEC.pdf)

## Outflow descriptions

### A: North-south molecular outflow

The most apparent of the three outflows, namely, outflow A, runs approximately from north to south through the MM1[^7] core. The outflow is detected in all tracers, SiO, HNC, CO (both ALMA and APEX), and $^{13}$CO  (see Figure [2](#OUTFLOW_GRID:fig)). However, the red northern component of this outflow is not detected in the $^{13}$CO data. This is consistent with the trend seen throughout all the presented data, which shows that red-shifted emission is found to be weaker within each outflow. We attribute this to the geometry of the system, which is caused by the obscuring effect of self-absorption by the intervening material.

It is not immediately clear to determine which of the two HCHII regions within MM1 is the progenitor of outflow A. As noted in , the area of maximal overlap between the two wings of the HNC outflow (Figure [2](#OUTFLOW_GRID:fig), panel C) is coincident with the position of the MM1*a* compact radio source. At a higher resolution, the morphology of the red-shifted emission seems to show a slight curvature toward MM1*b* within the central core region, as seen in CO (3-2) and SiO (Figures [2](#OUTFLOW_GRID:fig)-A and [2](#OUTFLOW_GRID:fig)-B), but this could be due to interactions between the two outflows A and B (§[3.1.3](#DescB:sec)) originating from this region. Since the blue-shifted emission is elongated linearly with the major axis of emission aligned toward the MM1*a* core, we treat MM1*a* as the progenitor of this outflow. We measure an average length-to-width ratio for this outflow, at the 10% of peak integrated intensity contour in Figure [2](#OUTFLOW_GRID:fig)-A, using both the red and blue lobes of 3.5.

### Jet-like properties in outflow A

An inspection of the ALMA CO and $^{13}$CO data shows that the blue lobe of outflow A is highly collimated and exhibits a high velocity gradient. The length-to-width ratio of the ALMA CO and $^{13}$CO contour at the 10% of peak integrated intensity contours in Figure [2](#OUTFLOW_GRID:fig)-A$_{zoom}$ are 2.8 and 3.4, respectively, matching the fiducial lower bounds of collimation of a jet structure ($\sim$ 3 e.g. (cite: Arceetal06)) and comparable to other observed molecular jet sources, such as HH211 (cite: Gueth99) and Outflow C in IRAS 05358$+$3543 (cite: Beuther02). Figure [7](#PVJet:fig) gives a position velocity (PV) diagram along the outflow axis as observed in CO outward from the driving source and covering a physical scale of $\sim 0.09$pc. We see that there is a clear linear velocity gradient within (highlighted by the white dashed line) from both CO emission (colour scale) and $^{13}$CO (displayed as a 5 and 10$\sigma$ contours). From the CO data, we calculate a velocity gradient of 155 kms$^{-1}$ pc$^{-1}$. This value is comparable to molecular outflow velocities seen in other high mass sources, such as K3-50A (cite: Klaassen13).

![](SubmissionFigsPDFs/PVJet.pdf)

### B: East-west molecular outflow

Outflow B runs approximately east to west through the MM1 core and is seen primarily in the CO (both ALMA and APEX), with the red lobe seen in both HNC and SiO. The APEX CO data (at all four frequencies) is dominated by an EW component (Figure [2](#OUTFLOW_GRID:fig), D and E). The known extended green object (EGO) in SDC335 (cite: Cyganowski08) is orientated in this same east-west (EW) direction (green filled contour in Figure [2](#OUTFLOW_GRID:fig)-C). The 4.5$\mu$m emission responsible for EGO features is thought to be created predominantly by shocked H$_2$ in outflowing material (cite: Cyganowski11). Outflow B displays an average length-to-width ratio as measured in the ALMA CO data of 3.0.

From the ALMA CO(3-2) data (Fig. [2](#OUTFLOW_GRID:fig)-A), the morphology of this outflow would suggest that MM1*b* is the likely progenitor. Interestingly it is approximately perpendicular, as projected on the sky, to the A outflow. This suggests, if MM1*a* and MM1*b* represent individual protostars, that their respective axes of rotation are likely to have very different orientations. Reasons for this misalignment in SDC335 are not clear from these data, but a possible scenario is considered in Section [5.3](#RosenSims:sec).

### C: NW (SE) molecular outflow

Outflow C is located to the north-west (NW) of the MM2 core. Detected in interferometric data in CO, HNC, and SiO, the molecular emission appears to be coming from a single outflow lobe, with its counterpart undetected, likely due to it having a similar velocity to the systemic velocity of SDC335 and, therefore, remaining in the excluded velocity range. This is supported by the presence of red-shifted emission in the APEX CO data that suggests the presence of a counterpart. This outflow hosts the brightest shock-tracing SiO emission of the three and the strongest Class-I CH$_3$OH maser detected here. Due to the lack of a counterpart red lobe, we do not attempt to measure an average length-to-width ratio for this outflow.

### Considering other possible outflows

The detection of the three outflows described above does not preclude the existence of additional outflows within SDC335. Using the ALMA band 7 CO data (the dataset with both the highest sensitivity and spatial resolution), we see that close to the $V_{lsr}$ of the system, the potential for additional structures still remains. However, the current data in this region suffers from two issues arising from interferometric artefacts: firstly, the bright CO emission and, therefore, the associated interferometric side-lobe artefacts are complex at these velocities; and secondly, owing to a lack of zero-spacing or single dish data, the ALMA image suffers from negative ‘bowling’ that comes from resolved-out extended emission in the source[^8], thereby further complicating the assessment of features at these velocities. These issues, combined with a lack of evidence for other outflows in our data at other frequencies, lead us to disregard some tentative structures which may appear to be additional outflows.

+:-------:+:---------:+:----:+:-----------------:+
| Outflow | Molecular | Lobe | $V_{range}$       |
+---------+-----------+------+-------------------+
|         | species   |      | \[kms$^{-1}$\]    |
+---------+-----------+------+-------------------+
| A       | CO        | Blue | $-$59.6 - $-$82.4 |
|         |           +------+-------------------+
|         |           | Red  | $-$11.6 - $-$33.6 |
|         +-----------+------+-------------------+
|         | $^{13}$CO | Blue | $-$51.6 - $-$67.9 |
|         +-----------+------+-------------------+
|         | SiO       | Blue | $-$51.6 - $-$74.0 |
|         |           +------+-------------------+
|         |           | Red  | $-$23.9 - $-$41.6 |
|         +-----------+------+-------------------+
|         | HNC       | Blue | $-$51.6 - $-$70.3 |
|         |           +------+-------------------+
|         |           | Red  | $-$24.1 - $-$41.6 |
+---------+-----------+------+-------------------+
| B       | CO        | Blue | $-$59.6 - $-$74.0 |
|         |           +------+-------------------+
|         |           | Red  | $-$10.0 - $-$33.6 |
+---------+-----------+------+-------------------+
| C       | CO        | Blue | $-$56.6 - $-$65.6 |
|         +-----------+------+-------------------+
|         | SiO       | Blue | $-$51.5 - $-$60.2 |
|         +-----------+------+-------------------+
|         | HNC       | Blue | $-$51.5 - $-$57.5 |
+---------+-----------+------+-------------------+

: Velocity ranges used in calculating outflow properties and integrated intensity maps by observed species from ALMA and ATCA observed transitions.

## Outflow properties

c c c l c \| c c \| c c c \| c & & & & & & &\
Outflow & V$_{lsr}$$^{\dagger}$ &Inclination$^{\dagger\dagger}$ & Molecular & Wing & $l$ & $\mid$V$_{max}$$\mid$ & $l$ & $\mid$V$_{max}$$\mid$ & t$_{dyn}$ & Associated\
& \[kms$^{-1}$\] & Angle \[$^{\circ}$\] & Species & & \[pc\] & \[kms$^{-1}$\] & \[pc\] & \[kms$^{-1}$\] & \[10$^3$ years\] & Masers$^{\ast}$\
& & & CO (3-2)& Red & 0.30 & 35.0 & 0.34 & 87.6 & 3.8 &\
& & &$^{13}$CO (3-2) & Red & - & - & - & - &\
& & &SiO (1-0) & Red & 0.29 & 22.7 & 0.32 & 56.7 & 5.5 &\
& & &HNC (1-0) & Red & 0.30 & 22.5 & 0.33 & 56.3 & 5.8 &\
& & &CO( 3-2)& Blue & 0.16 & 35.8 & 0.18 & 89.5 & 1.9 &\
& & &$^{13}$CO (3-2) & Blue & 0.12 & 21.3 & 0.14 & 53.2 & 2.6 &\
& & &SiO (1-0)& Blue & 0.17 & 27.4 & 0.19 & 68.5 & 2.7&\
& & &HNC (1-0)& Blue & 0.16 & 23.7 & 0.18 & 59.5 & 3.0 &\
& & & CO& Red & 0.30 & 36.6 & 0.33 & 110.9 & 2.9 &\
& & &CO & Blue & 0.25 & 27.4 & 0.25 & 83.1& 3.2 &\
& & & CO (3-2)& Blue & 0.19 & 19.1 & 0.22 & 35.4 & 6.1 &\
& & &SiO (1-0) & Blue & 0.15 & 13.7 & 0.18 & 25.3 & 7.1 &\
& & &HNC (1-0) & Blue & 0.16 & 11.0 & 0.19 & 20.4 & 9.2 &\

**Notes:**\
$^{(\dagger)}$ $V_{lsr}$ is local standard of rest velocity of the outflow driving source, see text for details.\
$^{(\dagger\dagger)}$ For outflows A and B, we present values of $l$, $|V_{max}$\| and t$_{dyn}$ calculated using the average value of the correction factor function of the inclination angle range in column 3, the values of the correction factors are given in Table [\[CorrectionFactors:tab\]](#CorrectionFactors:tab). For outflow C, we use the single value of 57.3$^{\circ}$. See text for definitions and inclination correction factors.\
$^{(\ast)}$ Associated Class I methanol masers as numbered in Table [\[Maser:tab\]](#Maser:tab) and Figure [14](#MaserCO:fig).\

### Inclination angles

To estimate the properties of the detected outflows, we must consider their inclination to the plane of the sky, measured as the angle $i,$ with $i=0$$^{\circ}$ indicating that the axis of the outflow is oriented along the observer’s line of sight and $i=90$$^{\circ}$ indicating that it is perpendicular to the light of sight. To assess this, we used the ALMA CO integrated intensity maps (shown in Figure [2](#OUTFLOW_GRID:fig)-A) as this dataset has the highest spatial resolution and signal-to-noise ratio. In the first instance, we assume each outflow has a symmetric biconical geometry, following (cite: CabritBertout86), and we define the opening angle, $\theta_{max}$, as the angle between the cone’s axis of symmetry and the outer emission contour at 3$\sigma$ (see Figure [10](#outflowIncExplain:fig)).

![](SubmissionFigsPDFs/iGTtheta_size)

 

![](SubmissionFigsPDFs/iGT90mintheta)

Next, we compare the measured $\theta_{max}$, the observed positions and morphology of the red and blue outflow lobes on the plane of the sky to the model outflows described by (cite: CabritBertout86). The work of (cite: CabritBertout86) includes four model ‘cases’ of differing inclination angle, $i$, and the opening angle (see their Table 1) to describe the morphology of the red and blue lobes an observer would expect to see on the sky for each given case. In brief[^9] the four cases are as follows:

Case 1 describes an outflow with both a red-shifted and a blue-shifted lobe on the line of sight, namely, with blue in front of a red lobe. The inclination angle conditions for this case are $i < \theta_{max}$ and $i \leq 90^{\circ} - \theta_{max}$. Observationally, this yields an outflowing red-blue lobe pair, which overlap spatially on the line of sight.

Case 2 describes a case with two observed outflow lobes, again one red-shifted and one blue-shifted, but with the inclination angle conditions of this case as $i \geq \theta_{max}$ and $i \leq 90^{\circ} -\theta_{max}$ (labelled A and B in Figure [10](#outflowIncExplain:fig)). Observationally there will be no point in the plane of the sky where the red and blue lobes spatially (or kinematically) overlap.

Case 3 has outflow lobes which are do not overlap spatially (as per case 2) but with the emission from each lobe in the pair spanning the source, $V_{lsr}$, resulting in mixed red-and-blue-shifted emission from each lobe. The (cite: CabritBertout86) model here requires inclination angles of values of $i \geq \theta_{max}$ and $i > 90^{\circ} -\theta_{max}$.

Case 4 requires very large opening angle ($\theta_{max}$) and inclination angles which obey these conditions, $i < \theta_{max}$ and $i > 90^{\circ} -\theta_{max}$. This results in lobes that overlap spatially (as per Case 1) and also span the $V_{lsr}$ and, as such, exhibit both red-shifted and blue-shifted emission (as per Case 3).

We note that for the purposes of the current study, only cases 2 and 3 are relevant here. Outflow A has two spatially and kinematically non-overlapping lobes in the plane of the sky. This is indicative of a (cite: CabritBertout86) case 2 source. We find that the opening angle, $\theta_{max}$, of the blue-shifted part of outflow A is $\sim 14^{\circ}$, putting loose limits on $i$ of between 14 and 76$^{\circ}$. Similarly, outflow B has two non-spatially or kinematically overlapping lobes, again indicating a (cite: CabritBertout86) case 2 source. We measure $\theta_{max}$ as between $\sim$9.4 and 12.6$^{\circ}$, and use the average value of 11$^{\circ}$ in calculations giving $i$ between 11 and 79$^{\circ}$.

Determining the inclination of outflow C is complicated by the fact that only one lobe is reliably detected to the north-west of MM2. We could assume that C is a (cite: CabritBertout86) case 3 source ( $i\geq \theta_{max}$ and i $> 90^{\circ}$) given that the observed velocity range of the one observed lobe spans the $V_{lsr}$ of MM2. This would give an inclination angle of $>77^{\circ}$ given our measured $\theta_{max}$ of 13.4$^{\circ}$. However, as the red lobe is not reliably detected in this source, we cannot confirm that the red lobe would similarly demonstrate an emission spanning the $V_{lsr}$ and, therefore, we use, instead, the commonly adopted statistical average value of $i =57.3^{\circ}$. This average inclination angle, $\langle \theta \rangle$ is calculated as: $$\begin{equation}
\langle \theta \rangle \int_{0}^{\pi} \rm{d}\Omega =  \int_{\theta = 0}^{\pi/2} \int_{0}^{\pi}\theta \sin \theta \rm{d}\Omega\rm{d}\theta = 1\rm{rad} \simeq 57.3^{\circ} \label{AvAngle:eqn}.
\end{equation}$$.

### Further consideration of the outflow inclination angles for outflows A and B.

Based solely on the (cite: CabritBertout86) models the potential inclination angles for outflows A and B cover ranges of 62$^{\circ}$ and 68$^{\circ}$, respectively. Such broad ranges introduce significantly different correction factors when deriving outflow properties. These correction factors range between 1.0 and 5.2 to correct the measured length, velocity, and momentum, with between 1.0 and 27.5 for energy and 0.2 and 27.0 for momentum flux (see Section [3.2.4](#DerivProps:sec) for a description of these derived properties and their respective correction factors). To further limit the possible range of inclination angles, we now outline an additional consideration, beyond the (cite: CabritBertout86) models, based on the observed length-to-width ratios ($LWR_O$) and the observed distance from the driving source to the maximum width ($x_O$) of the observed outflows. We present in Appendix [8](#incAngle:app) the full geometric derivation of this morphology and our associated results.

Outflows A and B have observed length-to-width ratios of 3.5 and 3.0, respectively (average of both red and blue lobes for each). Given also these outflows’ observed opening angles, and assuming the biconical outflow morphology of (cite: CabritBertout86), we find that it is not possible to recover such observed length-to-width ratios with no external influence on the outflow. With their respective opening angles and a bicone morphology, the maximum recoverable $LWR_O$ for each outflow reaches an asymptote at angles of 76 and 79$^{\circ}$  and with values of $LWR_O$ of 2.1 and 2.6 for A and B, respectively. This is due to the fact that under the biconical outflow morphology the observed length, $L_O$, is also the point along the outflow of maximum observed width.

In observations and modelling of molecular outflows, the idealised biconical morphology is seldom, if ever, seen (see e.g. (cite: Frank14)). This is due to the influence of the environment on the outflow. In particular, modelling the effects of the collapsing clumps, precession, turbulence, and magnetic fields (cite: Rosen20) show that the outflow morphologies are narrower along the outflow axis than the bicone morphology would suggest. Given these effects and the fact that we cannot reproduce the observed *LWR* for outflows A and B using the biconical morphology, we instead propose an alternate morphology to limit the inclination angle ranges of these outflows.

Our proposed ‘pencil-like’ morphology allows the widest point can be at some arbitrary point, $x$, along the length (as is observed for outflows A and B). Using this second morphology (as detailed in Appendix [8](#incAngle:app) and Figure [23](#NewOutflow:fig)) we find inclination angle ranges of between 53 and 76$^{\circ}$ for outflow A and 59 and 79$^{\circ}$ for outflow B which can provide the observed $LWR_O$.

An alternate scenario by which the observed $LWR_O$ for outflows A and B could be achieved would consist of observing these outflows at low inclination angles where the observed emission primarily arises from the outflow cavity rather than the outflow edge (i.e. Figure [8](#iGTtheta:fig), as opposed to Figure [9](#iGT90mintheta:fig) or similar for our alternate morphology). In such a case, the observed length-to-width ratios would require shaping of the outflow cavity away from symmetry about the outflow direction by the surrounding medium, compressing and elongating the cross-section of the cavity in a single dimension. In the case of SDC335, to observe two outflows from driving sources separated by $<$9000 AU which display similar levels of compression of their outflow cavities but at orthogonal directions seems implausible.

We therefore consider it more likely that the outflows are inclined closer to the plane of the sky than along the line of sight. As such, we consider the lower bounds from the (cite: CabritBertout86) models as extreme values and base our analysis instead on values ranging from those allowed by the geometric arguments presented in Appendix [8](#incAngle:app) of 53 to 76$^{\circ}$ for outflow A and 59 to 79$^{\circ}$ for outflow B.

Table [\[CorrectionFactors:tab\]](#CorrectionFactors:tab) provides the correction factors used for each outflow to correct the derived values to create the inclination angle corrected values given in Tables [\[outflowprop:tab\]](#outflowprop:tab) and [\[CO_outflowprop:tab\]](#CO_outflowprop:tab). For outflow C we use the correction factor at 57.3$^{\circ}$ and for outflows A and B we used average value of the correction function over the angle range given in column 3 of Table [\[outflowprop:tab\]](#outflowprop:tab). For completeness, we also include in Table [\[CorrectionFactors:tab\]](#CorrectionFactors:tab) the correction factors which would apply if the inclination angle ranges were based solely on the (cite: CabritBertout86) cases (given in italics) and in, Appendix B, a brief discussion of the implications of using these correction factors.

The proper assignment of inclination angles to observed outflows is a difficult task and has significant implications on derived properties. With current leading observatories, for example, ALMA, providing a wealth of observed molecular outflows, it is timely for investigation to be set into a robust method of assigning these angles. We look forward to the possibility that the use of an alternate morphology in this work will raise further discussions of this matter.

+:----------------------:+:--------------------------:+:----------------------------------------------------:+:----------------------------------------------------:+:------------------------:+
| Derived                | Correction                 | Average in range 53-76$^{\circ}$ *(14-76$^{\circ}$)* | Average in range 59-79$^{\circ}$ *(11-79$^{\circ}$)* | Value at 57.3$^{\circ}$  |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+
| property               | factor                     | (Outflow A)                                          | (Outflow B)                                          | (Outflow C)              |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+
| Length, $l$            | $\frac{1}{\sin i}$         | 1.12 *(1.71)*                                        | 1.08 *(1.81)*                                        | 1.19                     |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+
| Velocity, $|V_{max}|$, | $\frac{1}{\cos i}$         | 2.50 *(1.71)*                                        | 3.03 *(1.81)*                                        | 1.85                     |
+------------------------+                            |                                                      |                                                      |                          |
| Momentum, $P$          |                            |                                                      |                                                      |                          |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+
| Energy, $E$            | $\frac{1}{\cos ^2 i}$      | 6.69 *(3.47)*                                        | 9.97 *(4.17)*                                        | 3.43                     |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+
|                        |                            |                                                      |                                                      |                          |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+
| Momentum Flux, $F$     | $\frac{\sin i}{\cos ^2 i}$ | 6.16 *(2.86)*                                        | 9.45 *(3.56)*                                        | 2.88                     |
+------------------------+----------------------------+------------------------------------------------------+------------------------------------------------------+--------------------------+

### Temperature estimation

The four observed transitions of CO within the APEX data allow us to estimate the kinematic temperature of the outflowing gas in SDC335. To achieve this, we first regridded the data from each observation to the poorest spatial and velocity resolution, those being APEX CO (3-2) spatially and APEX CO (7-6) in velocity. We then created integrated intensity maps at 5 kms$^{-1}$ intervals from each cube. For each observed outflow we measured the integrated intensity (in K kms$^{-1}$) at two positions along the outflow, creating a spectral line energy distribution (SLED) at each position. We then followed the approach of (cite: Liu18) by generating a large grid over temperature, number and column density with the radiative transfer code RADEX (cite: VandertakRADEX) and searching for the best-fit modelled intensities compared to our observed SLED intensities to give a temperature at a given position. The best fit being a $\chi^2\sim1$ following the $\chi^2$ approach of (cite: vanderTak2000). We then take all models with $\chi^2=1\pm0.05$ and use the average properties of these models. Figure [11](#SLED:fig) gives an example of the APEX CO intensities and best fit model at a given position and velocity along outflow A. Using this technique we find $T_{kin}$ values of 62/53K, 54/61K and 55K for the blue and red components of outflows A, B and C respectively, (see Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab)).

![](SubmissionFigsPDFs/SLED.pdf)

### Derived properties

Using the inclination angles discussed in Section [3.2.2](#angConsider:sec), we were able to calculate inclination corrected physical properties for each outflow. For each observed species, we provide in Table [\[outflowprop:tab\]](#outflowprop:tab) both the measured and inclination angle corrected outflow lobe length, $l$ and $|V_{max}|$. We use the inclination-corrected values to calculate a dynamical time, $t_{dyn}$, for each outflow lobe. We define these properties and their inclination angle correction factors following (cite: Cunningham16), as follows:

The lobe length, $l$, is the maximum distance from the progenitor peak to the $3\sigma$ emission contour over the wings velocity range. The corrected length is calculated as $l_{corr}=l_{measured}/\sin(i)$ for inclination angle $i$. The absolute velocity difference, $|V_{max}|$, is defined as the difference between the outflow progenitor’s $V_{lsr}$ and the final velocity channel in the image cube to show $3\sigma$ emission from the outflow, with a correction for $i$ is calculated as $|V_{max_{corr}}|=|V_{max_{meas}}|/\cos(i)$. Finally, $t_{dyn}$, the dynamical age of the outflow is calculated as $t_{dyn}=l_{corr}/|V_{max_{corr}}|$.

For the ALMA CO observations, we also provide in Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab) the mass, momentum, and energy of each outflow lobe, following the methods of (cite: Ana12). As part of this analysis, we note that, as may be expected for a high mass star forming molecular cloud, emission close to the systemic velocity of the cloud becomes increasingly complex, with features of self absorption and missing large scale flux in the interferometric data, which can lead to uncertainties in values derived from emission observed within these velocity ranges. In order to avoid basing our findings on velocity ranges within the data effected by self-absorption or imaging artefacts, we exclude data close to the systemic velocity in the following way.

For the MM1 core, we take the spectrum of CO (3-2) data from APEX over the whole SDC335 velocity range. We fit a Gaussian to this spectrum, centred at the $V_{lsr}$ and exclude emission from channels $\pm2.5\times$ the variance, $\sigma$, of this Gaussian fit. The fitted $\sigma$ was found to be 5.2kms$^{-1}$. The factor of 2.5 was chosen to ensure that all self-absorption and missing flux features in the interferometric data were excluded for the MM1 core outflows (A and B) as can be seen in Figures [3](#OUTA_SPEC_blue:fig), [4](#OUTA_SPEC_red:fig), and [5](#OUTB_SPEC:fig). Excluding these velocity channels means our derived properties are lower limits for outflows A and B.

We repeat the same process for the MM2 core, taking the APEX CO (3-2) spectrum and fitting a Gaussian. Here, $\sigma$ is found to be 6.7kms$^{-1}$. The velocity range of the observed outflow lobe C from source MM2 is very close to the $V_{lsr}$ of MM2 that to exclude emission from $\pm2.5\sigma$ velocity channels would remove too much emission to provide a realistic determination of the values. Instead we use $\pm1.5\sigma$ sufficient to avoid self absorption artefacts in the CO data and retain sufficient data to get a meaningful result. The velocity ranges used for calculating outflow properties and generating the integrated intensity images of each outflow lobe shown in Figure [2](#OUTFLOW_GRID:fig) are given in Table [1](#OutflowCalc:tab).

Although we have other molecular species in the current data we do not carry out the following calculations with the data for these reasons. In particular, SiO is a shock-tracing species and therefore cannot reliably trace the bulk outflow properties since it will be enhanced in regions of shocks and less abundant elsewhere; HNC is currently a poorly studied outflow tracer therefore it is not clear whether or not (like CO) it traces the bulk outflow properties and further studies of this species in multiple targets would be required to assess its nature in outflows, which is beyond the scope of this paper.

For our calculations with the CO ALMA data, we define mass within the outflow, $M_{out}$ in units of M$_{\odot}$, as:

$$\begin{equation}
\begin{split}
M_{out}=\left(\frac{10^3}{M_{\odot}}\right)\left(\frac{8Q\pi k \nu^2}{A_{ul}hg_uc^3} \right)\exp\left(\frac{E_{ul}}{T}+\frac{h\nu}{kT}\right)\\\times\left(\frac{\mu/N_{A}}{M_{\odot}}\right)D^2  \sum \limits_{x,y,v}  \tau_{corr} T_{mb} \rm{d}V
\end{split}
\label{Mout:eqn}
,
\end{equation}$$

where $\mu$ is the mean molecular mass, $N_{A}$ the Avagadro’s constant, $Q$ the partition function, and $A_{ul}$ the Einstein coefficient. $E_{ul}$ and $g_{u}$ are the energy of the transition in K and the statistical weight of the upper energy level (2J+1), respectively, and D is this distance to SDC335 (3.25kpc). The value given by $\sum \limits_{x,y,v}{T_{mb} \rm{d}}V$ is equivalent to the integrated intensity and is calculated from the data cubes within a polygon region around each lobe. The sum is made per pixel, $x, y$, per velocity channel, $v$, over the outflows respective velocity range for all pixels with an intensity greater than or equal to three times the RMS per channel. Within this sum the data units are converted from the native units Jy/beam to Kelvin. The factor $\tau_{corr}$ gives the optical depth correction factor of the form $\tau_{corr}=\frac{\tau}{1-e^{-\tau}}$ and d$V$ gives the channel velocity width in kms$^{-1}$.

We calculate the mass both with a lower bound temperature $T$ of 20K and a literature value for $\tau_{corr}$ of 3.5 (cite: CabritBertout92) as well as the temperature values recovered from our best fit radiative transfer models from §[3.2.3](#Radex:sec) (Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab)) with a $\tau_{corr}$ factor of 8.2 based upon our estimated $^{12}$CO optical depth. To estimate an optical depth for $^{12}$CO in the outflows, we use the $^{13}$CO to $^{12}$CO line ratio observed in the blue wing of outflow A. Following the procedure of (cite: Myers83), we compare the $^{13}$CO/$^{12}$CO line ratios observed at multiple points (at peak emission) along the outflow to the ratio of optical depths given by $\frac{1-e^{-\tau_{^{13}CO}}}{1-e^{-\tau_{^{12}CO}}}$ and use the assumption that $\tau_{^{12}CO}$ is equal to $f\times \tau_{^{13}CO}$. Here, $f$ is the isotopic abundance ratio, in the range $f=50-100$ typical of star-forming regions (cite: Pineda10; Szucs14). Given this range of $f$ we can derive numerically a range of optical depths for $^{13}$CO and thus attain a corresponding range of $\tau_{^{12}CO}$ values. We find a range of $\tau_{^{12}CO}$ = 2.4 and 23.5 and use the median value of 8.2. These are comparable to typical values seen in CO outflows e.g. (cite: CabritBertout92) of 1 to 8.9 with a median of 3.5.

Momentum and energy then follow as:

$$\begin{equation}
P_{CO}=\sum \limits_{x,y,v} M_{x,y,v} \Delta V
\end{equation}$$

and

$$\begin{equation}
E_{CO}=\frac{1}{2}\sum \limits_{x,y,v} M_{x,y,v} \Delta V^2
,
\end{equation}$$

where $\Delta V$ is the absolute velocity difference between the source $V_{lsr}$ and the given channel in the sum. $M_{x,y,v}$ is the outflow mass value for only a single voxel ($x,y,v$), which follows from Equation [\[Mout:eqn\]](#Mout:eqn). Finally, we calculate the momentum flux $F_{CO}$ within annular regions projected out from the central source which is defined (following (cite: BontempsOutflow96), their equation 1 and (cite: Ana13)), as:

$$\begin{equation}
F_{CO}=\sum \limits_{x,y,v} \left( \frac{\Omega \tau_{corr} T_{mb} \rm{d}V \Delta V^2}{{\rm{d}}r}\right)
\label{FCO:eqn}
,
\end{equation}$$

where d$r$ is the width of the annular ring in the sum and $\Omega$ is the same constant as the value preceding the integral in Equation [\[Mout:eqn\]](#Mout:eqn).

To take into account the assumed inclination angles, the values of $P_{CO}$, $E_{CO}$, and $F_{CO}$ are corrected by the factors $1/\cos(i)$, $1/\cos ^2(i)$ and $\sin(i)/\cos ^2(i)$, respectively, with their specific values for each outflow and outflow property given in Table [\[CorrectionFactors:tab\]](#CorrectionFactors:tab). The error in inclination angle is the most significant contribution to the errors on these values. The derived outflow property values are given in Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab).

Our derived values are comparable to those from both observed and theoretical studies of low- to high-mass protostellar objects (cite: Zhang05; Yildiz12; Cunningham16; vanKempen16; Cyganowski17; Staff18), with the SDC335 outflows A and B typically having amongst the highest values compared to published sources. The values for outflow C are somewhat lower and likely affected by the limited velocity range we were able to use for this feature. These results confirm SDC335 protostellar sources are indeed high-mass protostars. When compared to (cite: Maud15), the SDC335 sources appear to have a similar range of momentum fluxes and energies, but significantly lower mass and momentum. This difference is likely due to comparing single dish (cite: Maud15) and interferometric (this work) data with the potential for multiple spatially unresolved outflows in the single dish data boosting values within the (cite: Maud15) sample.

# Infall, accretion, and the evolutionary status of SDC335

## Cloud infall and protostellar accretion rates

Outflow momentum flux (Equation [\[FCO:eqn\]](#FCO:eqn)) is a proxy for the protostellar mass accretion rate, $\dot M_{acc}$, since the driving force of outflows is thought to result from the conservation of angular momentum within an accreting system (cite: Konigl00; Pudritz07; Tan14). A theoretical relation between $F_{CO}$ and $\dot M_{acc}$ equates the two values scaled by a material entrainment efficiency, $f_{ent},$ and the protostellar mass ejection rate and wind speed, $\dot M_{w}, v_w$ (cite: Ana13). Following this form of the $F_{CO}$ to $\dot M_{acc}$ relation and assuming the same material entrainment efficiency and wind properties as these authors have done ($f_{ent} = 0.5$, $\dot M_{w}/\dot M_{acc} = 0.15$ and $v_w = 40$kms$^{-1}$), we derive the mass accretion rates given in Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab).

For outflows A and B, the $\dot M_{acc}$ derived from our $F_{CO}$ values are in the range of 8.7 - 64.8 $\times 10^{-5}$M$_{\odot}$ yr$^{-1}$ , at a fixed temperature of $T=20$K, and 11.5 - 85.4 $\times 10^{-5}$M$_{\odot}$ yr$^{-1}$, for our derived temperatures ($T=53 - 62$K). For outflow C, values are lower at $\dot M_{acc}$ is 0.2 $\times 10^{-5}$M$_{\odot}$ yr$^{-1}$ for $T=20$K and 0.3 $\times 10^{-5}$M$_{\odot}$ yr$^{-1}$ at the derived temperature of $T=55$K.

The values for outflows A and B are at the higher end of inferred accretion rates from low-mass protostars, $\dot M_{acc} \sim 10^{-5}$M$_{\odot}$ yr$^{-1}$, (cite: McKeeTan03; HosokawaOmukai09; HosokawaYorkeOmukai10) and are more typical of those inferred for high-mass protostars, $10^{-4} - 10^{-3}$M$_{\odot}$ yr$^{-1}$ (cite: Zhang05; Fuller05; Beuther13; Ana13; Rosen16; Goddi18; Rosen19), from both observational and theoretical works reported within the literature. The value for $\dot M_{acc}$ of outflow C is very low and likely a consequence of the limited velocity range over which we are able to measure this outflow’s properties. Indeed, as noted in Section [3.1](#OutDescript:sec), the driving sources for all three of the observed outflows are known to be high-mass protostars owing to their association with 6.7GHz methanol masers, so the derived $\dot M_{acc}$ for outflow C can act as a lower limit.

We now consider the total derived mass accretion, $\dot M_{tot. acc}$, within SDC335. This value is calculated as the sum of all the derived $\dot M_{acc}$ values presented in Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab), giving a $\dot M_{tot. acc}$ of 1.4 ($\pm$ 0.1) $\times 10^{-3}$M$_{\odot}$ yr$^{-1}$. With this value, an interesting comparison can be made with the derived mass infall rate, $\dot M_{inf}$, for the whole SDC335 cloud. (cite: Peretto13) calculated a value of $\dot M_{inf} \simeq 2.5 (\pm 1.0) \times 10^{-3}$M$_{\odot}$ yr$^{-1}$. These two values are comparable within the quoted errors, which would imply a near 100% efficiency of infalling material on cloud scales ($\sim$few pc) being funnelled onto the accretion disk scale ($<<0.1$pc) and driving the outflows. We note, however, that this does not imply a 100% accretion of the inflowing material into the protostar. A near continuous flow of material from large (cloud/filament) to smaller (clump/core) scales would be significant as it suggests that each core is acting as a sink within the cloud drawing material from all scales and, as such, would have implications for high-mass star forming models. The protostellar accretion rate is a characteristic of the whole forming cluster under competitive accretion models (cite: Bonnell01; Bonnell04; Bonnell07) but under core accretion models (cite: McKeeTan02; McKeeTan03; Tan14), this is set by the properties of bound cores. It would appear that this result favours the former set of models.

Another interesting implication of these inferred accretion rates is that the three known protostellar sources in SDC335 would appear to be drawing the majority of the material onto themselves, suggesting that there is a limited amount of material available to start forming any additional protostars within the system. In ALMA observations of the IRDC G28.34 P1, (cite: Zhang15) found a lack of low-mass protostars compared to the expected number from a typical IMF. These authors concluded, after discounting migration of low-mass stars into the centre of the cluster, that the most likely scenario for this under-abundance was because the low-mass stars are yet to form. If this is true then SDC335 may hold an explanation, in that early onset high-mass star formation dominates the inflowing material budget depriving lower mass proto or pre-stellar cores from gaining mass and starting formation.

As the inclination angles of the observed outflow are the dominant factor in the error budget of these calculations, an additional study of the protostars in SDC335 is required to better constrain the outflow properties. For example, testing for the presence of rotation axes, indicative of accretion disks, within the sources would help further this investigation.

## Evolutionary Status of SDC335

The works of (cite: Ana13), (cite: Maud15) and (cite: vanKempen16), for instance, have shown there is a linear (in log-space) relation between the molecular outflow momentum flux (and therefore $\dot M_{acc}$) and source luminosity in protostellar sources from low to high-masses. Recent numerical works by (cite: Rosen20) show this same trend.

![](SubmissionFigsPDFs/Fout_Lbol_2020_angArgs.pdf)

Figure [12](#Fout_Lbol:fig) plots the calculated outflow momentum flux as a function of source bolometric luminosity, $L_{bol}$, for the protostars in SDC335 and other sources, both low and high-mass, from the literature. The sources from the literature are low-mass Class 0 and 1 sources using values from (cite: BontempsOutflow96) (both classes), observed and literature Class I sources from (cite: vanderMarel13). High-mass sources in the plot are Class 0 analogues from (cite: Ana13) and high-mass protostellar sources from (cite: Maud15).

The $L_{bol}$ values for SDC335 are those derived in , and we divide the total luminosity of MM1 (1.82$\times 10^4$ $L_{\odot}$) between MM1*a* and MM1*b* in a 2.5:1 ratio (based on their respective optically thin radio emission flux ratios, see Table 5) yielding values of 1.3$\times 10^4$ and 0.51$\times 10^4$ $L_{\odot}$ for MM1*a* and MM1*b* respectively. To compensate for this source of uncertainty each SDC335 point on Figure [12](#Fout_Lbol:fig) is presented with a $\pm$50% error bar on the $L_{bol}$ value. For outflows A and B the dominant source of error is the range of possible inclination angles, as such for these sources the errorbar represents the maximum and minimum values for $F_{CO}$ using the respective maximum and minimum possible inclination angles. For outflow C the $F_{CO}$ error includes the measured error on $F_{CO}$, prior to inclination angle correction due to noise within the data, plus a $\pm$5 degree error on the inclination angle used (57.3$^{\circ}$for the average angle for randomly orientated outflows).

We can see from Figure [12](#Fout_Lbol:fig) that all outflows in SDC335 fit the general trend of outflow momentum flux as a function of luminosity over the wide mass range represented. The plotted points are the sum of the red plus blue lobes for each source in SDC335, using the temperatures from our RADEX fitting and derived optical depth values in the calculation of the $F_{CO}$ values. The outflows A and B in SDC335 reside in the same parameter space as the high-mass protostars from (cite: Maud15) with outflows A amongst the higher $F_{CO}$ range for its calculated $L_{bol}$. We note that the sources from (cite: Maud15) are studied with a single dish instrument, thus lacking the resolution of our current work, leading to the question posed by those authors regarding whether or not their observed outflows are driven by a single or multiple objects. SDC335 outflow C has a significantly lower $F_{CO}$ value away from the proposed observed trend seen within the literature. This suggests either it has a less powerful, potentially more evolved outflow or this effect could simply be an artefact caused by the limited velocity range we are able to integrate over for this outflow coupled with a poorly defined inclination angle.

Assuming each of the identified outflows in SDC335 represents a single protostellar object, we can consider whether these sources represent an analogue of the protostellar source evolution classifications used at lower mass (cite: Lada99). To this end, we generate best linear fit lines for the $F_{CO}$ as a function of $L_{bol}$ for Class 0 and I sources using values from the literature plotted in Figure [12](#Fout_Lbol:fig). The best fit lines are plotted as the red dotted line for Class 0 and blue dashed-dot line for Class I, extended to higher luminosity values for comparison with SDC335 with associated 1-$\sigma$ error margins from the fit plotted as shaded regions of matching colour.

The derived best fits are, $$\begin{equation}
\log_{10}(F_{CO}[\rm{Class 0}])=-4.3(\pm0.15) + 0.60(\pm0.08)\log_{10}\left(\frac{L_{bol}}{L_{\odot}}\right)
\end{equation}$$ and $$\begin{equation}
\log_{10}(F_{CO}[\rm{Class I}])=-5.3(\pm0.12) + 0.63(\pm0.16)\log_{10}\left(\frac{L_{bol}}{L_{\odot}}\right)
\end{equation}$$

for Class 0 and 1 sources, respectively. We note that the best-fit line for Class 0 objects matches very closely to the results reported by (cite: CabritBertout92) for a sample of Class 0 sources (IRAS 16293, IRAS 3282, L1448, L1455M, RNO 43 and VLA1623) and a single high-mass object (G35.2 N).

The fitted lines show a decrease in outflow momentum flux between the Class 0 and I stages, as would be expected during the evolution of a protostellar source along the plotted evolutionary tracks (cite: Ana13) assuming a decreasing and intermittent accretion rate. From Figure [12](#Fout_Lbol:fig) we see that both MM1*a* and MM1*b* lie very close to the Class 0 best fit line and within the 1-$\sigma$ error bound of that line of best fit (red shaded region). This suggests that these sources are very high-mass Class 0 analogue. We use the qualifier ‘very’ to indicate ’more extreme than’ based on a comparison to the position of the other high-mass Class 0 protostars in Figure [12](#Fout_Lbol:fig) from (cite: Ana13) (empty star markers in the Figure).

Supporting the ‘young, very high-mass’ status of the SDC335 sources MM1*a* and MM1*b*,  we can see from the evolutionary tracks in Figure [12](#Fout_Lbol:fig) that these sources sit well above the 50M$_{\odot}$ track, but at an early stage before $\sim$50% of the envelope mass has been accreted (denoted by the first arrow head). This is also corroborated by the short dynamical times of these outflows ($\rm{few}\times 10^3$yr) in Table [\[outflowprop:tab\]](#outflowprop:tab).

found, based on their current radio continuum properties, that the three high-mass protostellar objects in SDC335 are all currently displaying characteristics of zero age main sequence (ZAMS) stars of spectral type B1.5 (or B1.5-B1 for MM1*a*), which equates to stellar masses of $\sim$ 9.0M$_{\odot}$ (cite: Mottram11). These relatively low ‘current’ stellar masses agree with the position of the observed outflow properties for A and B in terms of their position along the evolutionary tracks.

+:-------:+:----:+:-----:+:---------------:+:-------------------------:+:--------------:+:-------------------------------------------:+:---------------------------------:+
| Outflow | Lobe | T     | $M_{out}$       | $P_{CO}$                  | $E_{CO}$       | $F_{CO}$                                    | $\dot M_{acc}$                    |
+---------+------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         |      | \[K\] | \[M$_{\odot}$\] | \[M$_{\odot}$kms$^{-1}$\] | \[$10^{38}$J\] | \[10$^{-5}$M$_{\odot}$kms$^{-1}$yr$^{-1}$\] | \[10$^{-5}$M$_{\odot}$yr$^{-1}$\] |
+---------+------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
| A       | Blue | 20    | 0.19            | 8.72                      | 4.51           | 274.1                                       | 11.0                              |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Red  | 20    | 0.89            | 48.0                      | 29.2           | 1619.1                                      | 64\. 8                            |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Blue | 62.0  | 0.75            | 12.7                      | 6.5            | 368.6                                       | 14.7                              |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Red  | 53.3  | 1.27            | 68.2                      | 41.4           | 2133.8                                      | 85.4                              |
+---------+------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
| B       | Blue | 20    | 0.08            | 4.6                       | 2.98           | 218.6                                       | 8.7                               |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Red  | 20    | 0.21            | 13.2                      | 9.6            | 461.0                                       | 18.4                              |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Blue | 54.6  | 0.22            | 12.1                      | 7.5            | 288.0                                       | 11.5                              |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Red  | 60.9  | 0.32            | 20.0                      | 14.4           | 617.9                                       | 24.7                              |
+---------+------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
| C       | Blue | 20    | 0.002           | 0.07                      | 0.02           | 6.1                                         | 0.2                               |
|         +------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+
|         | Blue | 54.5  | 0.014           | 0.31                      | 0.07           | 8.0                                         | 0.3                               |
+---------+------+-------+-----------------+---------------------------+----------------+---------------------------------------------+-----------------------------------+

### Low bolometric luminosities in the MM1 core

An open issue from previous work on SDC335, presented in , was the discrepancy between the observed bolometric luminosity $L_{bol}$, as derived from the millimetre core spectral energy distributions, and the luminosity of a ZAMS star of the spectral type necessary to produce the Lyman $\alpha$ photon flux inferred from the radio continuum, $L_{\rm ZAMS}$. The value of $L_{bol}$ was found to be approximately a factor 20 less than $L_{\rm ZAMS}$.

To briefly review the finding (for more details, see their Section 4.1); the authors calculated a Lyman $\alpha$ photon flux based upon the HCHII continuum flux density for each of the three HCHII sources. From this, a ZAMS spectral type was associated with each core (B1.5 for MM2 and MM1*b* and B1 $-$ B1.5 for MM1*a*) using values from (cite: Mottram11) and (cite: Davies11).

The ZAMS is reached when hydrogen burning has commenced, however, given the outflow indicators (masers, EGO etc) present in SDC335, it was assumed in that each HCHII region represented a protostar which was still actively accreting. This assumption is borne out by the detection of the three outflows in the current work. An actively accreting protostar will have a total luminosity (assuming ZAMS properties), $L_{tot,ZAMS}$, which is the sum of its intrinsic luminosity, $L_*$, and that from accretion, $L_{acc}$. Here $L_{acc}$ is of the form $L_{acc} = \frac{GM_*\dot M_*}{R_*}$, and the value of $M_*$, $R_*$ and $L_*$ were based on the ZAMS properties and $\dot M_*$ (the mass accretion rate) was assumed to be equal to the global infall rate of SDC335 derived by (cite: Peretto13) of $2.5\times10^{-3}$M$_{\odot}$ yr$^{-1}$.

From this calculation, the authors noted that the ZAMS $L_*$ and $L_{bol}$ agree to within a factor of $\sim2$ however this did not allow for ongoing accretion. Including $L_{acc}$ gives $L_{tot,ZAMS}$ a value that is a factor 20 higher than $L_{bol}$ (see the values in Tables 2 and 6 of ).

presented two scenarios which could account for the observed low bolometric luminosity from all three protostars in SDC335. In light of the data presented in this current work we can review these scenarios. The first scenario was that the assumed accretion rate $2.5\times10^{-3}$M$_{\odot}$ yr$^{-1}$ from (cite: Peretto13)) was too high and that the protostars were undergoing accretion at a lower rate (either overall or as a function of periodic accretion). In this current work, we derive a mass accretion rate onto each protostellar object from their outflow momentum flux (column 8 in Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab)) and find that indeed the values are lower than the (cite: Peretto13) infall rate. This allows us to revise the values of $L_{tot,ZAMS}$ from Table 6 of and address the second scenario discussed by those authors. In doing so, using both the minimum and maximum $\dot M_{acc}$ for each outflow from Table [\[CO_outflowprop:tab\]](#CO_outflowprop:tab) to give a possible range of $\dot M_{acc}$ (and using the derived temperatures from §[3.2.3](#Radex:sec)), we provide revised values for Table 6 in in our current Table [\[RevisedZams:tab\]](#RevisedZams:tab).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | $L_{*}$ | $L_{bol}^{\dagger}$ | $L_{acc}$ (min) | $L_{acc}$ (max) | $L_{tot,ZAMS}$ (min) | $L_{tot,ZAMS}$ (max) | $L_{tot,ZAMS}/L_{bol}$ factor |
| Source | \[L$_{\odot}$\] | \[L$_{\odot}$\] | \[L$_{\odot}$\] | \[L$_{\odot}$\] | \[L$_{\odot}$\] |  |  |
| MM1*a*  | 5.5$\times 10^{3}$ | 1.3$\times 10^{4}$ | 1.3$\times 10^{4}$ | 7.6$\times 10^{4}$ | 1.9$\times 10^{4}$ | 8.1$\times 10^{4}$ | 1.4 - 6.2 |
| MM1*b*  | 4.1$\times 10^{3}$ | 5.1 $\times 10^{3}$ | 9.9$\times 10^{4}$ | 2.1$\times 10^{4}$ | 1.4$\times 10^{4}$ | 2.6$\times 10^{4}$ | 2.8 - 5.0 |
| MM2 | 4.4$\times 10^{3}$ | 9.9$\times 10^{3}$ | 1.7$\times 10^{2}$ | $-$ | 4.5$\times 10^{3}$ | $-$ | 0.5 |

For MM2, the $L_{tot,ZAMS}$ is now a factor $\sim$2 lower than the $L_{bol}$ which is consistent within the uncertainties on these values. A spectral type B1.5 ZAMS star has a mass of $\sim$ 9M$_{\odot}$ (cite: Mottram11), which for MM2 would also agree with the accreting protostars position on the evolutionary tracks in Figure [12](#Fout_Lbol:fig) and its status as a potentially more evolved protostar than the cores in MM1.

In the case of the two ionising sources in MM1, the derived mass accretion rates cover a large range of values, 14.7 to 85.4$\times10^{-5}$ M$_{\odot}$ yr$^{-1}$ and 11.5 to 24.7$\times10^{-5}$ M$_{\odot}$ yr$^{-1}$ for MM1*a* and MM1*b*, respectively. With these values the bolometric luminosity for MM1*a* is consistent with $L_{tot,ZAMS}$ at the lowest $\dot M_{acc}$ values but the discrepancy persists over the majority of the possible range (any value above 30.0 $\times10^{-5}$ M$_{\odot}$ yr$^{-1}$ leads to a factor 2.5 discrepancy between the two luminosities). And for MM1*b* the discrepancy between $L_{bol}$ and $L_{tot,ZAMS}$ is at a factor of about three over the entire range – meaning that the observed $L_{bol} < L_{tot,ZAMS}$ from also persists for this source.

The second scenario to account for the luminosity discrepancy discussed in is based upon the models of massive protostellar evolution at high accretion rates ($\sim 10^{-3}$M$_{\odot}$ yr$^{-1}$) of (cite: HosokawaOmukai09) and (cite: HosokawaYorkeOmukai10). In this model massive protostars go through a phase of swelling to radii of $\sim100$ R$_{\odot}$ when their mass is between 6 and 10M$_{\odot}$, followed by a short contraction phase as their mass grows to between 10 and 30M$_{\odot}$. During the period of swollen radii the effective temperature of the protostar is lower than that of an equivalent mass ZAMS star, as such there are insufficient UV photons to generate a HII region. However, during the short contraction phase as the radius decreases the effective temperature increases and a HII region can form, whilst the radius remains somewhat swollen ($\sim$10 R$_{\odot}$) giving a lower luminosity than a ZAMS star at the same mass. In , the authors suggest that each SDC335 protostar was in the contraction phase, accounting for both the observed HII regions and the low bolometric luminosities, though given the relatively brief duration of the contraction phase having multiple sources at this stage simultaneously would be unlikely.

The new derived mass accretion rates for MM1*a* and MM1*b* have values that are in the range of those considered by the (cite: HosokawaOmukai09) models (although for the swollen radii at accretion rates of $\sim 10^{-4}$M$_{\odot}$ yr$^{-1}$, the swelling is to $\sim$40R$_{\odot}$ rather than 100R$_{\odot}$) and thus these sources are in either the swollen radii phase or the contraction phase – this would still seem a viable scenario that would lead to the lower observed luminosities. Given the relative lengths of each of these phases, it would be more likely that they are still in the swollen radii phase. If this is the case, the origin of the ionised emission in each core would then require an alternate explanation, which we address in Section [4.2.2](#radiojets:sec).

### An alternate interpretation of the ionised radio continuum emission in SDC335

As discussed briefly in , the spectral indices for MM1*b* and MM2 fall within the range of values for both photo-ionised HII regions and collimated ionised jets (cite: Reynolds86). Given the detection in this work of outflows from both these sources, it is important to review origin of radio continuum emission from the SDC335 protostars.

Radio continuum emission has been detected toward a number of low luminosity sources driving molecular outflows, for example in (cite: Anglada95). In this work, the author shows that the low luminosity for their sample of objects precludes the origin of the observed radio continuum emission coming from photoionisation by Lyman alpha photons. Using the models of shock ionised gas from (cite: Curieletal87; Curiel89), the author then shows that for their sample, shock ionisation is capable of creating the observed radio continuum based on the outflow momentum flux of their targets.

Based upon the best-fit model and data in (cite: Anglada95) (their Equation 1 and Figure 5) we find that using their 8, 23, and 25 GHz flux densities , MM1*a* and MM1*b* are shown to reside between the line of minimum requirement (dashed line in (cite: Anglada95) Figure 5) and the line of best fit (solid line in (cite: Anglada95) Figure 5) for shock ionisation as the mechanism for the observed radio continuum emission in their sample. This suggests that for these sources this may indeed be the origin of the detected radio emission. However, MM2 is a factor of between $\sim$17 and 37 below the lower bound of the emission expected from shocks (cite: Anglada95). This may be an evolutionary factor or one arising from the orientation of the MM2 outflow to the line of sight, which limits the range of velocities we are able to integrate over leading to an underestimate of the outflow momentum flux value for this source (§[4.1](#infall:sec)).

The direct implication of interpreting the origin of the ionised matter as from outflow shocks as opposed to photoionisation is the evolutionary status of the protostellar sources themselves. If the emission is not due to photoionisation, this suggests that the protostars are at an earlier pre-ionising stage in their evolution.

It is important to state that although this alternate interpretation may account for the presence of ionised hydrogen and indicate a resolution of the discrepancies between observed bolometric luminosity and a corresponding ZAMS luminosity, the protostars within SDC335 remain high-mass protostellar sources, which will go on to form stars of mass $>8$M$_{\odot}$. We base this on both their observed luminosities (of the order 10$^4$ L$_{\odot}$ ) and the co-location of each of the radio emission peaks with 6.7GHz methanol maser emission. Higher spatial resolution ($\leq$ 2.0 $^{\prime\prime}$) observations of SDC335 at radio frequencies would be required to fully assess this interpretation. The impact on the current work – should the radio free-free emission prove to be outflow shocks – is limited to the discussion in Section [4.2.1](#tooLow:sec). All other results would remain unchanged.

# Interaction between outflows and filaments 

Previous studies of the motion of material at large scales in SDC335 have found that the cloud is both globally collapsing toward its centre and that material is being transported inward to this region along the filamentary arms of the cloud (cite: Peretto13). In our current work, however, we report the detection of material outflowing from the protostellar cores at the cloud centre. In this section, we look at the evidence of the interaction of the filamentary infalling and outflowing material. Finding regions of interaction within SDC335 would make the IRDC a valuable source for studying the potential disruptive effects on material transport from feedback of young massive stars have. In the following, we highlight the observed features within SDC335 that mark potential filament-outflow interactions. As part of this discussion, we identify each outflow lobe by the letter corresponding to the outflow and a sub-script colour to indicate the particular red or blue lobe.

## Class I methanol masers

Collisionally excited Class I methanol masers are commonly associated with molecular outflows in regions of massive star formation (cite: Kurtz04; Cyganowski09). SDC335 was known to harbour four Class I maser sources , all of which are clearly spatially offset from the compact HII regions in the MM1 and MM2 cores. With our new, more sensitive data, an additional four individual maser sources were detected. The spectrum of each maser is presented in Figure [13](#MaserSpec:fig). Figure [14](#MaserCO:fig) presents the maser locations within SDC335, with the masers colour-coded by velocity.

All the maser spots peak at velocities within $\sim$6.0kms$^{-1}$ of the systemic velocity of the SDC335 mm-cores. The position and peak emission properties of each spot are given in Table [\[Maser:tab\]](#Maser:tab). The masers are numbered from south to north. Whilst we do not focus on the properties of each maser spot individually within this work, we include in the following discussion the maser spots that provide useful indications as shock tracing when interpreted as potentially part of the outflow-filament interactions within SDC335.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Maser | RA | Dec | S$_{peak}$ | V$_{peak}$ | V$_{range}$ |
| No. | \[h : m : s\] | \[ $^{\circ}$ : $^{\prime}$ : $^{\prime\prime}$\] | \[Jy\] | \[kms$^{-1}$\] | \[kms$^{-1}$\] |
| 1 | 16:30:58.31 | -48:44:05.2 | 0.79 | -47.3 | -60.4, -47.0$\rightarrow$ |
| 2 | 16:30:58.56 | -48:43:55.4 | 1.01 | -47.7 | -52.3, -47.0$\rightarrow$ |
| 3 | 16:31:00.36 | -48:43:54.1 | 1.05 | -47.9 | -49.6, -47.0$\rightarrow$ |
| 4 | 16:31:00.56 | -48:43:51.6 | 0.462 | -43.2 | $\leftarrow$-43.8, -39.0 |
| 5 | 16:30:59.76 | -48:43:50.9 | 0.294 | -43.4 | $\leftarrow$-43.8, -42.3 |
| 6 | 16:30:57.90 | -48:43:46.2 | 0.119 | -40.4 | -41.5, -39.2 |
| 7 | 16:30:56.45 | -48:43:33.8 | 48.8 | -45.3 | -52.4, -39.0 |
| 8 | 16:30:58.56 | -48:43:32.4 | 0.0742 | -40.0 | -43.0, -36.8 |

![](SubmissionFigsPDFs/MaserSpecRevised.pdf)

![](SubmissionFigsPDFs/MasersCO.pdf)

## Interaction regions

### A$_{Blue}$ and the F3 and F4 filaments

The A$_{Blue}$ outflow is well collimated near the driving source (MM1*a*) when observed at high resolution (ALMA CO and $^{13}$CO), as seen in the narrow structure of the contour plots in Figure [2](#OUTFLOW_GRID:fig)-A$_{zoom}$ and the CO velocity channel maps shown in Figure [15](#BlueJetVcutCO:fig). The shock-tracing SiO emission detected in this outflow lobe is however predominately at the end (furthest from the driving source) of this lobe Figure [2](#OUTFLOW_GRID:fig)-B.

This region of SiO emission and the observed lobe end in the CO and $^{13}$CO ALMA observation coincide spatially and kinematically with the ends of the F3 and F4 filaments of the IRDC (marked as the orange dash line in Figures [1](#PressyFig:fig) and [2](#OUTFLOW_GRID:fig), c.f. (cite: Peretto13)). The F3 and F4 filaments are carrying material into the SDC335 central region at velocities of $\sim-$45.8 and $-46.5$kms$^{-1}$  respectively (cite: Peretto13). Given the $V_{lsr}$ of the MM1*a* core, these infalling velocities are moving in the opposite direction to the outflowing material ($V_{Ablue} \sim$ $-$50.5 to $-$82.4kms$^{-1}$), see Figure [15](#BlueJetVcutCO:fig) and [1](#OutflowCalc:tab)). Supporting this interpretation is the position and velocity range covered by the Class-I CH$_3$OH maser source 1 (see Table [\[Maser:tab\]](#Maser:tab)). We show the presence of the maser spot at a given velocity in Figure [15](#BlueJetVcutCO:fig) as a solid purple circle.

Given the collisionally excited pumping mechanism responsible for Class-I masers and the hypothesis that such collisional excitement occurs at the interfaces of outflows and the surrounding molecular gas as seen in, for example, (cite: Plambeck90; Kurtz04; Vornokov10), the alignment of the maser activities both spatially and kinematically with the outflow lobe end suggest that we are indeed seeing the point of interaction between the A$_{Blue}$ outflow and the infalling material from the F3 and F4 filaments. The large velocity range the CH$_3$OH emission covers requires a strong shock front to pump such maser emission.

![](SubmissionFigsPDFs/blueJetVcut_2020FINAL.pdf)

### C and the F2 filament

The one detected lobe of outflow C (C$_{blue}$) exhibits both the brightest Class I methanol maser (maser 7, Table [\[Maser:tab\]](#Maser:tab)) and the brightest SiO emission detected in the region (see Figure [6](#OUTC_SPEC:fig)). At a peak flux density of 48.78 Jy, maser 7 is over 40 times the intensity of any of the other detected maser sources (see e.g. Figure [13](#MaserSpec:fig)). Given that both SiO emission and Class I CH$_3$OH maser are shock tracing species we note that the end (away from the driving source MM2) of this outflow lobe (Figure [2](#OUTFLOW_GRID:fig)) appears close to the fiducial end of the F2 filament (orange dashed line, c.f. (cite: Peretto13)). This suggests that we are observing a shocked region caused by the meeting of the outflow and the inflowing matter from the F2 filament. The velocities of C$_{blue}$ and the infall along F2 are in opposite directions, with the F2 filament $V_{F2}=\sim-$46.0kms$^{-1}$ (cite: Peretto13), so redder than the $V_{lsr}$ of MM2 and $V_{C_{blue}}$=$-$59.1 to -43.6kms$^{-1}$, thereby extending both red and blue-ward of this $V_{lsr}$. Although the maser position and the end of the orange dashed line representing F2 in Figures [2](#OUTFLOW_GRID:fig)-A,B,C do not match exactly, we emphasise that the dashed line is a fiducial marker and the true morphology and kinematics at the end of the inflow are not known at spatial resolutions better than $\sim$5$^{\prime\prime}$(cite: Peretto13). Further higher resolution observations of the region would be required to confirm this as a true shock-interaction region.

### Curvature of A$_{red}$ and the F1 filament

The A$_{red}$ lobe is observed in our CO (ALMA), SiO, and HNC data to exhibit curvature at its northernmost end. Inspecting the position of the nearby filamentary arm, F1, in Figure [2](#OUTFLOW_GRID:fig) it appears that the curvature coincides with where A$_{red}$ would meet the infalling material from the filament. Emission from the A$_{red}$ here is at velocities of $\sim -$30 to $-$20 kms$^{-1}$ (CO, SiO) whereas the inflowing material of the F1 filament is at $\sim-$47.25kms$^{-1}$ (cite: Peretto13). The start of curvature of the F1 filament also coincides with a clump of SiO emission and CO (beyond the velocity range used to generate the contours in Figure [2](#OUTFLOW_GRID:fig)-A) offset from the outflow (see Figure [2](#OUTFLOW_GRID:fig)-B) at velocities $-36.9$ to $-41.2$kms$^{-1}$. This is spatially and kinematically coincident with maser 8 (see Table [\[Maser:tab\]](#Maser:tab)), suggesting an interaction point between the inflow and outflow is likely associated with a shock front leading to the SiO. Maser 8 peaks at $-$40kms$^{-1}$ with a velocity range $\pm\sim3.0$kms$^{-1}$ as such covers velocities which are between those measured for the inflowing and outflowing material. Figure [16](#maser8_COSiO:fig) gives the spectra of CO and SiO at the position of maser 8.

![](SubmissionFigsPDFs/MAS8_SPEC.pdf)

### B$_{red}$ shocked emission

The B$_{red}$ lobe is observed in SiO, HNC and CO (both APEX and ALMA). The leading edge of this outflow is coincident with the positions of masers 3 and 4 and peak SiO emission (see Figures [2](#OUTFLOW_GRID:fig)-A and [2](#OUTFLOW_GRID:fig)-B) of the outflow, indicating a region of shocked gas. We note that this lobe does not directly appear to be interacting with a filamentary inflow, but from Figure [1](#PressyFig:fig) the outflow appears toward the edge of the 8$\mu$m dark region of the cloud suggesting some interaction at the cloud boundary. In Figures [17](#maser3_COSiO:fig) and [18](#maser4_COSiO:fig) we give the spectra of CO (ALMA), HNC and SiO at the position of masers 3 and 4.

![](SubmissionFigsPDFs/MAS3_SPEC.pdf)

![](SubmissionFigsPDFs/MAS4_SPEC.pdf)

## A and B outflows misalignment, a potential scenario

As evident in Figure [2](#OUTFLOW_GRID:fig) and noted in Section [3.1.3](#DescB:sec), outflows A and B have outflow axes that are approximately perpendicular to one another. Naively, one would assume that the angular momentum axes for a pair of protostars of similar mass separated by a relatively small distance ($\sim$9000AU) would be aligned. This appears not to be the case for SDC335.

Within the literature, there are other examples showing similar misalignments. For example, protostars A and B within IRAS16293 (separated by 600 AU) were found to have rotation axes misaligned (cite: Pineda16293) with A observed edge on and B either having little to no observable rotation or a rotation axis in the plane of the sky. This gives A and B effectively a $\sim$ 90$^{\circ}$ offset in their angular momentum axes. Similarly, there are several systems found in Perseus (with pairs separated by 1000 to 10,000 AU) which show outflow axes that are misaligned between low mass protostars with the distribution of axes appearing to prefer random or anti-aligned orientations (cite: Lee16).

We consider a possible cause for this misalignment in SDC335. This scenario posits that the outflow progenitors MM1*a* and MM1*b*, after fragmenting from the MM1 mm-core, have grown in mass by accreting matter from different material flows arriving at each core from different directions, thus changing their respective angular momentum vectors as the system evolves. The high, non-uniform accretion rates inherent to massive star formation ($\dot M_{\rm acc} \sim 10^{-3} \; \rm M_{\rm \odot} \, yr^{-1}$) will push the star around and cause the angular momentum vector to precess. Such behaviour has been seen in three-dimensional (3D) radiation-magnetohydrodynamic (RHD) simulations of the collapse of a turbulent massive pre-stellar core into a massive star (cite: Rosen16; Rosen20). The movement of the star and its angular momentum vector will cause the outflows to be launched over a larger area as the star grows in mass. This effect will broaden the entrained outflows since the protostellar outflows are likely launched along the star’s or surrounding accretion disk’s angular momentum vector (e.g. (cite: Shu00; Pudritz07)).

Figure [19](#Rosen:fig) (cite: Rosen20) shows two snapshots from a 3D RHD simulation that models the collapse of a turbulent massive (150 $M_{\rm \odot}$) pre-stellar core into a massive stellar system and includes radiative feedback and collimated outflows that are launched along the stars’ angular momentum vectors (cite: Cunningham11). These snapshots show the column density of the molecular material that is entrained by the protostellar outflows from the stars that have formed. To obtain the distribution of entrained material, we compute the mass-weighted integrated gas density only along cells that have $\rho_{\rm OF}/\rho \geq 0.1,$ where $\rho_{\rm OF}$ is the outflow gas density injected by stars, and $\rho$ is the total gas density.

In the first snapshot, where the time elapsed is 0.4 $t_{\rm ff}$ where $t_{\rm ff}=42.7$ kyr is the core’s free-fall timescale, the star has a mass of 9.12 $M_{\rm \odot}$ and what looks like multiple molecular outflows. However, this outflow morphology is due to the non-uniform accretion flow that knocks the star around, causing the star to move away from its birth site and precess; thereby causing the outflow launching direction to change with time. At later times, $t=0.6 t_{ff}$, when multiple low-mass protostars have formed and are clustered near the massive protostar (pink filled-in circles), the smaller and weaker multiple outflows from the low mass protostars overlap. The resulting overlapping entrained outflows from these clustered low-mass companions to the right of the primary star are inclined by $\sim 45^{\circ}$ to the entrained outflow from the primary star, as indicated by the arrow in Figure [19](#Rosen:fig). We note that this significant offset between outflow axes and separation between the massive and low-mass stars is similar to what is seen in SDC335. The fact this is occurring within less than one cloud free-fall time for the simulated cloud lends further credence to SDC335 being at an early period of star formation. (For SDC335 $t_{ff}\sim$ 3.5 $\times 10^5$ yrs.)

Measuring the level of turbulence of material within the central region of SDC335 and the accretion flows onto individual cores would require higher resolution observations of the dense gas (combined with single-dish data to avoid ‘missing spacing’ problems), which are not currently available.

![](SubmissionFigsPDFs/Turb_massEntrainedAll_10_Arrowb.pdf)

# Discussion and conclusions

Using new ATCA SiO and CH$_3$OH observations coupled with archival CO, $^{13}$CO, and HNC data from ALMA and four transitions of CO from the APEX telescope, we identify and analyse three molecular outflows within the young high-mass star forming infrared dark cloud SDC335. These data have yielded the following outcomes:

- The three outflows, A, B, and C, are identified, each associated with one of the three known HCHII regions in SDC335 (MM1*a*, MM1*b*, and MM2, respectively). The red-blue outflow lobes from A extend in the north-south direction, B extends east-west and C, of which only the blue lobe is detected, extends to the north-west. They have a full width velocity ranges of up to 10kms$^{-1}$ and temperatures of $\sim$60 K. The two most massive sources in the cloud, MM1*a* and MM1*b*, are separated by $\sim9000$AU but have driving outflows of projected outflow axes that are approximately perpendicular to one another. The blue lobe of outflow A displays a structure and velocity that is characteristic of a jet.

- The analysis of the measured outflow momentum flux, $F_{CO}$, as a function of source bolometric luminosity, $L_{bol}$, and in comparison to theoretical evolutionary tracks (cite: Ana13) confirms that the progenitor protostars are massive young stellar objects with two sources residing above the tracks for 50M$_{\odot}$ stars. Using samples of $F_{CO}$ and $L_{bol}$ measurements from the literature for low to intermediate mass stars at evolutionary classes 0 and I, we derived best-fit $F_{CO}$-$L_{bol}$ relations for these two classes. Extrapolating these relations upward in $L_{bol}$, we find the outflow momentum flux properties of the SDC335 outflows A and B agree best, with their progenitors being high-mass Class 0 analogues and indicating that SDC335 is at a very early stage of the star-formation process.

- Inferring the mass accretion rates from the source outflow properties, we find that the total mass accretion is 1.4$(\pm0.1) \times 10^{-3}$M$_{\odot}$ yr$^{-1}$ on the protostellar scale. This value is consistent with the calculated mass infall rate on cloud and filamentary scales 2.5$(\pm1.0) \times 10^{-3}$M$_{\odot}$ yr$^{-1}$ found by (cite: Peretto13). This result suggests that at this early stage of evolution nearly all the material accreted onto the clump is funnelled through the cores onto these three massive young sources, limiting the scope for the formation of additional, low mass sources in the region. If significant numbers of lower mass stars are to form in SDC335, these would then have to form at a later stage in the evolution of the region.

- These new data combined with existing knowledge of the bulk inflow and global and filamentary collapse properties of the SDC335 cloud provide compelling evidence of the interaction between the molecular outflows and the material infalling along the filamentary arms. Given the very young (Class 0 analogue) status of the protostars driving the outflows, this makes SDC335 a valuable test bed for study of the disruptive feedback effects of massive protostars on their natal clouds.

The observed properties described in this work make the infrared dark cloud SDC335 a key target for the more detailed study of how massive protostars form and effect their natal environments through accretion and protostellar outflows. Such features warrant further study at high spectral and spatial resolutions and sensitivities.

# Acknowledgements

The Australia Telescope Compact Array is part of the Australia Telescope which is funded by the Commonwealth of Australia for operation as a National Facility managed by CSIRO. The authors would like to thank all ATNF staff past and present who helped during the ATCA observation used in this paper, particularly those who provided A.A. with curry. The authors would also like to thank the anonymous referee for their input into the paper after initial submission which has helped to improve the work.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00474.S and #2012.0.00781.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This publication is based on data acquired with the Atacama Pathfinder EXperiment (APEX). APEX is a collaboration between the Max-Planck-Institut fuer Radioastronomie, the European Southern Observatory, and the Onsala Space Observatory. A.A. is funded by the STFC at the UK ARC Node. G.A.F acknowledges financial support from the State Agency for Research of the Spanish MCIU through the AYA2017-84390-C2-1-R grant (co-funded by FEDER) and through the “Center of Excellence Severo Ochoa” award for the Instituto de Astrofísica de Andalucia (SEV-2017-0709). N.P. wishes to acknowledge support under STFC consolidated grants ST/N000706/1 and ST/S00033X/1. A.D.C acknowledges the support from the UK STFC consolidated grant ST/N000706/1. A.L.R acknowledges support from NASA through Einstein Postdoctoral Fellowship grant number PF7- 180166 awarded by the Chandra X-ray Center, which is operated by the Smithsonian Astrophysical Observatory for NASA under contract NAS8-03060. This research made use of APLpy, an open-source plotting package for Python hosted at http://aplpy.github.com. This research made use of Astropy,[^10] a community-developed core Python package for Astronomy (cite: astropy:2013; astropy:2018).

# Spectra of the outflow driving sources

To compliment the outflow spectra in Figures [3](#OUTA_SPEC_blue:fig) to [6](#OUTC_SPEC:fig), we present in Figures [20](#MM1a_SPEC:fig) to [21](#MM1b_SPEC:fig) spectra over the same velocity range at the peak position of the three HCHII regions in SDC335. These are the likely driving sources of the outflows, as described in the main text.

![](SubmissionFigsPDFs/MM1a_SPEC.pdf)

![](SubmissionFigsPDFs/MM1b_SPEC.pdf)

![](SubmissionFigsPDFs/MM2_SPEC.pdf)

# Inclination angle considerations based on observed length-to-width ratio

Here, we address the arguments used to limit the range of possible inclination angles derived from the (cite: CabritBertout86) models by introducing a general outflow model beyond the simple bicone.

![](SubmissionFigsPDFs/NonBiconeOutflow.pdf)

Following Figure [23](#NewOutflow:fig), we define the length, $L$, of an outflow as from the driving source to the end of the outflows influence on the surrounding medium in the direction of the outflowing material. Complementary to this, the outflow width, $W$, is the maximum extent of the outflows influence orthogonal to the outflow direction. The angle between the axis of symmetry of the outflow (along $L$) and the widest point, called the opening angle, we denote here as $\theta$. The distance along $L$ to the point of maximum width we name $x$. The length of $x$ depends on the morphology of the outflow. In the case of the (cite: CabritBertout86) bicone model $L = x$. The true length-to-width, $LWR$, of the outflow is then defined as $LWR = L/W = \frac{L}{2x\tan{\theta}}$.

Also presented in Figure [23](#NewOutflow:fig) are the observed properties of the outflow. The observed length $L_O$ of the outflow at an inclination angle, $i$, with respect to the observer is the sum of the contribution of the outflow wall or edge, $E_O$, and emission from the outflow cavity/dome end, $C_O$. So, $L_O = E_O + C_O$.

In turn $E_O$ comprises the sum of the outflow wall from it origin to length $x$, $E_{xO}$ and from the wall from $x$ to the end of the outflow at $L$, $E_{L-xO}$. These two contributions have the forms:

$$\begin{equation}
E_{xO} = E_x \sin(i-\theta) = \frac{W}{2\sin(\theta)} \sin(i-\theta)
,
\end{equation}$$

$$\begin{equation}
E_{L - xO} = (L-x) \sin i
,
\end{equation}$$

leading to

$$\begin{equation}
E_{O} = \frac{W}{2\sin(\theta)} \sin(i-\theta) + (L-x) \sin i 
\end{equation}$$

and the contribution of the cavity along the line of sight is given by, $$\begin{equation}
 C_O = W\cos i 
,
\end{equation}$$

such that in its full form the observed length is given by $$\begin{equation}
L_O =   \frac{W}{2\sin(\theta)} \sin(i-\theta) + (L-x) \sin i +W \cos i \rm{~}.
\label{obsLen:eqn}
\end{equation}$$

We note that inclination projection effects on $W$ are minimal, for example, given a source at distance of 3kpc the observed width only differs from the true $W$ due to its inclination at the 0.02% level for $L$ = 0.5pc (larger than any measured or corrected length in our observed outflows) when inclined along the line of sight. Indeed, an outflow of $L$ = 30pc inclined along the line of sight will only have a project effect difference on $W$ at the 1% level. As such, we neglect this consideration. This gives the observed length-to-width as $LWR_O = \frac{L_O}{W}$. There is a final observable counterpart to the true physical value which is the observed length from the driving source to the widest point, $x_O$ which is given by $x \sin i$.

## Bicone case, $L = x$

In the case that the outflow has a biconical morphology, as is the case assumed to derive our initial inclination angle ranges, then $L=x$ and the second term in Equation [\[obsLen:eqn\]](#obsLen:eqn) becomes zero. This leads the observed length-to-width to become:

$$\begin{equation}
LWR_O =   \frac{1}{2\sin(\theta)} \sin(i-\theta) + \cos i 
\label{LWRbiconen:eqn}
,
\end{equation}$$

from which using the measured $LWR_O$ and $\theta$ it is possible to constrain the value of inclination angle, $i$. For outflow A with a $\theta$ = 11$^{\circ}$ and $LWR_O$ = 3.5, Equation [\[LWRbiconen:eqn\]](#LWRbiconen:eqn) asymptotes at 79$^{\circ}$ with a $LWR_O$ = 2.6. Similarly for outflow B with a $\theta$ = 14$^{\circ}$ and $LWR_O$ = 3.0 asymptotes at 76$^{\circ}$ with a $LWR_O$ = 2.1. In both cases, these asymptotes are clearly at 90$^{\circ}$ - $\theta$. Based on this, it becomes clear that whilst the biconical morphology does not apply particularly well to outflows A and B, the observed length-to-width ratios are providing evidence that (in the absence of external influence on the morphology) these outflows tend toward higher inclination angles.

## General case, $L \neq x$

For the general case, where $L \neq x$, the inspection of the inclination angle now depends on an additional piece of information, the observed distance from the outflow origin to the point that the outflow is widest, $x_O$. With this the observed $LWR_O$ becomes,

$$\begin{equation}
LWR_O =   \frac{1}{2\sin(\theta)} \sin(i-\theta) + \frac{(L-\frac{\sin i}{x_0}) \sin i}{W} + \cos i \rm{~}.
\label{LWRgen:eqn}
\end{equation}$$

Given our observed $L_O$, $W$, $\theta$ and $x_O,$ we can solve numerically the range of $i$ and $x$ values that will return a $LWR$ matching our observed values. We do this for a model outflow of $L = 1$ with $x$ and $W$ as fractions of this. For this work, we consider values of $i$ and $x$ which return both an $x_O$ and $LWR_O$ within $\pm 10\%$ of our observed values.

Under these conditions we find that we can limit the range of $i$ values to between 53 and 76$^{\circ}$ for outflow A and 59 and 89$^{\circ}$ for outflow B. The latter values can again be limited at the higher end by kinematics, as above 79$^{\circ}$ we would observe both red- and blue-shifted emission at either side of the driving source for outflow B, giving us a final limit for B of between 59 and 79$^{\circ}$. These are significantly smaller ranges than using the (cite: CabritBertout86) models and again tend to higher inclination angles.

## Implications of using the bicone model

In Section [3.2.2](#angConsider:sec), the morphology described in Section [8.2](#generalCase:sec) is used in place of the typical biconical outflow morphology to narrow the ranges of potential inclination angles for outflows A and B observed in SDC335. Table [\[CorrectionFactors:tab\]](#CorrectionFactors:tab) provides the factors required to correct the observed values for the effects of inclination. These correction factors are given for both the angle ranges generated using our preferred morphology and the bicone case.

Owing to the difference in angles covered the correction factors differ between the two morphologies by factors of 0.65 and 2.15 for outflow A and 0.6 and 2.65 for outflow B, respectively. One item that is of significance with regard to the findings of this paper is the correction factor applied to the momentum flux, $F$. Using the bicone morphology, the momentum flux values are 2.15$\times$ and 2.65$\times$ smaller for outflows A and B, respectively. Following this reduction through our analysis yields the following changes:

- The $F_{CO}$ values for MM1*a* and MM1*b* become 1161.8$\times 10^{-5}$M$_{\odot}$ kms$^{-1}$ yr$^{-1}$ and 341.3$\times 10^{-5}$M$_{\odot}$ kms$^{-1}$ yr$^{-1}$, respectively (for the sum of the red and blue lobes), leading to each source being lower on the y-axis of Figure [12](#Fout_Lbol:fig). MM1*a* remains consistent with the Class 0 line of best fit whereas MM1*b* moves to the upper end of the 1$-\sigma$ error margin for the Class I line of best fit, suggesting it is potentially more evolved than MM1*a*  though remains consistent with the Class 0 line within errors. Both sources remain consistent with the 50M$_{\odot}$ evolutionary track plotted in [12](#Fout_Lbol:fig).

- The $\dot M_{acc}$ derived from our $F_{CO}$ values are now in the range 6.8 - 39.6 $\times 10^{-5}$M$_{\odot}$ yr$^{-1}$ , at $T=20$K, $\tau = 3.5$, and 4.3 - 9.3 $\times 10^{-5}$M$_{\odot}$ yr$^{-1}$, for $T=53-62$K with $\tau = 8.2$ for outflows A and B. From these, the total derived mass accretion, $\dot M_{tot. acc}$, within SDC335 (as defined in §[4.1](#infall:sec)) becomes $6.04 (\pm 0.04) \times 10^{-4}$M$_{\odot}$ yr$^{-1}$. This means the comparison to the total infall rate is somewhat weaker, at 24% of the (cite: Peretto13) values, rather than 55% and comparable within the errors.

- The change in $\dot M_{acc}$ leads to a lessening of the discrepancy discussed in §[4.2.1](#tooLow:sec) between the bolometric luminosity ,$L_{bol}$, and $L_{tot,ZAMS}$. For MM1*b* with $L_{tot,ZAMS},$ becomes a factor 1.5-2.4 times lower than $L_{bol}$, meaning these values are consistent (as is the case with source MM2). For MM1*a* range of $\dot M_{acc}$ values, an allowance remains for a discrepancy of greater than 2.5$\times$ between the two luminosities at the higher end ($>30\times10^{-5}$M$_{\odot}$ yr$^{-1}$) of the derived range.

87 natexlab

(ref: Anglada95) Anglada, G. 1995, in Revista Mexicana de Astronomia y Astrofisica Conference Series, ed. S. Lizano & J. M. Torrelles, Vol. 1, 67

(ref: Arceetal06) Arcé, H., Shepherd, D., Gueth, F., et al. 2006, in Protostars and Planets V, ed. K. K. Bo Reipurth, David Jewitt (University of Arizona Press)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Avison15) Avison, A., Peretto, N., Fuller, G. A., et al. 2015, A&A, 577, A30

(ref: Beuther13) Beuther, H., Linz, H., & Henning, T. 2013, A&A, 558, A81

(ref: Beuther02) Beuther, H., Schilke, P., Gueth, F., et al. 2002, A&A, 387, 931

(ref: Bonnell01) Bonnell, I. A., Bate, M. R., Clarke, C. J., & Pringle, J. E. 2001, MNRAS, 323, 785

(ref: Bonnell07) Bonnell, I. A., Larson, R. B., & Zinnecker, H. 2007, Protostars and Planets V, 149

(ref: Bonnell04) Bonnell, I. A., Vine, S. G., & Bate, M. R. 2004, MNRAS, 349, 735

(ref: BontempsOutflow96) Bontemps, S., Andre, P., Terebey, S., & Cabrit, S. 1996, A&A, 311, 858

(ref: Braun85) Braun, R. & Walterbos, R. A. M. 1985, A&A, 143, 307

(ref: CabritBertout86) Cabrit, S. & Bertout, C. 1986, ApJ, 307, 313

(ref: CabritBertout92) Cabrit, S. & Bertout, C. 1992, A&A, 261, 274

(ref: MMB330to345) Caswell, J. L., Fuller, G. A., Green, J. A., et al. 2011, MNRAS, 417, 1964

(ref: Cunningham11) Cunningham, A. J., Klein, R. I., Krumholz, M. R., & McKee, C. F. 2011, ApJ, 740, 107

(ref: Cunningham16) Cunningham, N., Lumsden, S. L., Cyganowski, C. J., Maud, L. T., & Purcell, C. 2016, MNRAS, 458, 1742

(ref: Curieletal87) Curiel, S., Canto, J., & Rodriguez, L. F. 1987, , 14, 595

(ref: Curiel89) Curiel, S., Rodrı́guez, L. F., Cantó, J., et al. 1989, Astrophysical Letters and Communications, 27, 299

(ref: Cyganowski09) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., & Churchwell, E. 2009, ApJ, 702, 1615

(ref: Cyganowski11) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., Churchwell, E., & Zhang, Q. 2011, ApJ, 729, 124

(ref: Cyganowski17) Cyganowski, C. J., Brogan, C. L., Hunter, T. R., et al. 2017, MNRAS, 468, 3694

(ref: Cyganowski08) Cyganowski, C. J., Whitney, B. A., Holden, E., et al. 2008, AJ, 136, 2391

(ref: Davies11) Davies, B., Hoare, M. G., Lumsden, S. L., et al. 2011, MNRAS, 416, 972

(ref: Drabek-Maunder16) Drabek-Maunder, E., Hatchell, J., Buckle, J. V., Di Francesco, J., & Richer, J. 2016, MNRAS, 457, L84

(ref: Cabral14) Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2014, A&A, 570, A1

(ref: Ana13) Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2013, A&A, 558, A125

(ref: Ana12) Duarte-Cabral, A., Chrysostomou, A., Peretto, N., et al. 2012, A&A, 543

(ref: Frank14) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, Protostars and Planets VI, 451

(ref: Fuller05) Fuller, G. A., Williams, S. J., & Sridharan, T. K. 2005, A&A, 442, 949

(ref: Garay02) Garay, G., Brooks, K. J., Mardones, D., Norris, R. P., & Burton, M. G. 2002, ApJ, 579, 678

(ref: Goddi18) Goddi, C., Ginsburg, A., Maud, L., Zhang, Q., & Zapata, L. 2018, ArXiv e-prints, arXiv:1805.05364

(ref: GreenMcClure11) Green, J. A. & McClure-Griffiths, N. M. 2011, MNRAS, 417, 2500

(ref: Gueth99) Gueth, F. & Guilloteau, S. 1999, Astronomy and Astrophysics, 343, 571

(ref: 2008SPIE.7020E..10G) Güsten, R., Baryshev, A., Bell, A., et al. 2008, in Proc. SPIE, Vol. 7020, Millimeter and Submillimeter Detectors and Instrumentation for Astronomy IV, 702010

(ref: Gusten06) Güsten, R., Nyman, L. Å., Schilke, P., et al. 2006, A&A, 454, L13

(ref: HosokawaOmukai09) Hosokawa, T. & Omukai, K. 2009, ApJ, 691, 823

(ref: HosokawaYorkeOmukai10) Hosokawa, T., Yorke, H. W., & Omukai, K. 2010, ApJ, 721, 478

(ref: 2006SPIE.6275E..0NK) Kasemann, C., Güsten, R., Heyminck, S., et al. 2006, in Proc. SPIE, Vol. 6275, Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, 62750N

(ref: Klaassen13) Klaassen, P. D., Galván-Madrid, R., Peters, T., Longmore, S. N., & Maercker, M. 2013, Astronomy and Astrophysics, 556, A107

(ref: 2014ITTST...4..588K) Klein, T., Ciechanowicz, M., Leinz, C., et al. 2014, IEEE Transactions on Terahertz Science and Technology, 4, 588

(ref: Konigl00) Konigl, A. & Pudritz, R. E. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 759

(ref: Kroupa02) Kroupa, P. 2002, Science, 295, 82

(ref: Krumholz14) Krumholz, M. R., Bate, M. R., Arce, H. G., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 243

(ref: Kurtz04) Kurtz, S., Hofner, P., & Álvarez, C. V. 2004, ApJS, 155, 149

(ref: Lada99) Lada, C. J. 1999, in The Origin of Stars and Planetary Systems, ed. C. Lada & N. Kylafis (Springer), 143–192

(ref: Lee16) Lee, K. I., Dunham, M. M., Myers, P. C., et al. 2016, ApJ, 820, L2

(ref: Liu18) Liu, J., Qiu, K., Wyrowski, F., et al. 2018, ApJ, 860, 106

(ref: Maud15) Maud, L. T., Moore, T. J. T., Lumsden, S. L., et al. 2015, MNRAS, 453, 645

(ref: McKeeTan02) McKee, C. F. & Tan, J. C. 2002, Nature, 416, 59

(ref: McKeeTan03) McKee, C. F. & Tan, J. C. 2003, ApJ, 585, 850

(ref: CASAREF) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mottram11) Mottram, J. C., Hoare, M. G., Davies, B., et al. 2011, ApJL, 730, L33

(ref: Myers83) Myers, P. C., Linke, R. A., & Benson, P. J. 1983, ApJ, 264, 517

(ref: Offner17) Offner, S. S. R. & Chaban, J. 2017, ApJ, 847, 104

(ref: Pandian09) Pandian, J. D., Menten, K. M., & Goldsmith, P. F. 2009, ApJ, 706, 1609

(ref: Peretto09) Peretto, N. & Fuller, G. A. 2009, A&A, 505, 405

(ref: Peretto13) Peretto, N., Fuller, G. A., Duarte-Cabral, A., et al. 2013, A&A, 555, A112

(ref: Pineda16293) Pineda, J. E., Maury, A. J., Fuller, G. A., et al. 2012, A&A, 544, L7

(ref: Pineda10) Pineda, J. L., Goldsmith, P. F., Chapman, N., et al. 2010, ApJ, 721, 686

(ref: Plambeck90) Plambeck, R. L. & Menten, K. M. 1990, ApJ, 364, 555

(ref: Plunkett13) Plunkett, A. L., Arce, H. G., Corder, S. A., et al. 2013, ApJ, 774, 22

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123

(ref: PudritzBanerjee05) Pudritz, R. E. & Banerjee, R. 2005, in Massive Star Birth: A Crossroads of Astrophysics, ed. E. Churchwell, M. Felli, & C. Walmsley, Vol. 227, IAU Symposium

(ref: Pudritz07) Pudritz, R. E., Ouyed, R., Fendt, C., & Brandenburg, A. 2007, Protostars and Planets V, 277

(ref: Reynolds86) Reynolds, S. P. 1986, ApJ, 304, 713

(ref: Rosen20) Rosen, A. L. & Krumholz, M. R. 2020, AJ, 160, 78

(ref: Rosen16) Rosen, A. L., Krumholz, M. R., McKee, C. F., & Klein, R. I. 2016, MNRAS, 463, 2553

(ref: Rosen19) Rosen, A. L., Li, P. S., Zhang, Q., & Burkhart, B. 2019, ApJ, 887, 108

(ref: RosenOffner20) Rosen, A. L., Offner, S. S. R., Sadavoy, S. I., et al. 2020, Space Sci. Rev., 216, 62

(ref: Schilke97) Schilke, P., Walmsley, C. M., Pineau des Forets, G., & Flower, D. R. 1997, A&A, 321, 293

(ref: Shu00) Shu, F. H., Najita, J. R., Shang, H., & Li, Z. Y. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 789–814

(ref: Staff18) Staff, J. E., Tanaka, K. E. I., & Tan, J. C. 2018, ArXiv e-prints, arXiv:1811.00954

(ref: Szucs14) Szűcs, L., Glover, S. C. O., & Klessen, R. S. 2014, MNRAS, 445, 4055

(ref: Szymczak07) Szymczak, M., Bartkiewicz, A., & Richards, A. M. S. 2007, A&A, 468, 617

(ref: Tan14) Tan, J. C., Beltrán, M. T., Caselli, P., et al. 2014, Protostars and Planets VI, 149

(ref: SynthesisImaging) Taylor, G. B., Carilli, C. L., & Perley, R. A., eds. 1999, Astronomical Society of the Pacific Conference Series, Vol. 180, Synthesis Imaging in Radio Astronomy II

(ref: vanderMarel13) van der Marel, N., Kristensen, L. E., Visser, R., et al. 2013, A&A, 556, A76

(ref: VandertakRADEX) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vanderTak2000) van der Tak, F. F. S., van Dishoeck, E. F., Evans, Neal J., I., & Blake, G. A. 2000, ApJ, 537, 283

(ref: vanKempen16) van Kempen, T. A., Hogerheijde, M. R., van Dishoeck, E. F., et al. 2016, A&A, 587, A17

(ref: Vornokov10) Voronkov, M. A., Caswell, J. L., Britton, T. R., et al. 2010, MNRAS, 408, 133

(ref: Walmsley99) Walmsley, C. M., Pineau des Forêts, G., & Flower, D. R. 1999, A&A, 342, 542

(ref: CABBpaper) Wilson, W. E., Ferris, R. H., Axtens, P., et al. 2011, MNRAS, 416, 832

(ref: Yildiz12) Yıldız, U. A., Kristensen, L. E., van Dishoeck, E. F., et al. 2012, A&A, 542, A86

(ref: Zhang05) Zhang, Q., Hunter, T. R., Brand, J., et al. 2005, ApJ, 625, 864

(ref: Zhang15) Zhang, Q., Wang, K., Lu, X., & Jiménez-Serra, I. 2015, ApJ, 804, 141

(ref: ZhangY15) Zhang, Y. & Tan, J. C. 2015, ApJ, 802, L15

[^1]:

[^2]: "The reduced interferometric data cubes and integrated intensity images in FITS format and the outflow spectra in ASCII format are only available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/

[^3]: Atacama Pathfinder EXperiment, (cite: Gusten06).

[^4]: See the MIRIAD user guide for more information, http://www.atnf.csiro.au/computing/software/miriad/userguide/ .

[^5]: See e.g. https://casaguides.nrao.edu/index.php/M100_Band3 for a CASA data combination tutorial.

[^6]: We note that in these $^{13}$CO data, only  6% of baselines are in excess of 600m (the RMS length of all baselines being 325.65m) giving rise to a larger final synthesised beam in the combined image than would be expected from calculating the resolution using the maximum baseline.

[^7]: A note on nomenclature: within this paper, we use MM1 to indicate the millimetre emission core from (cite: Peretto13), while MM1*a* and MM1*b* to refer to the smaller radio emission/HCHII regions from , which are both encompassed within the MM1 mm-core.

[^8]: see e.g. (cite: Braun85) and Chapter 8 (cite: SynthesisImaging) for an explanation of bowling as different to interferometric side-lobes.

[^9]: For more details, please refer to the original text in (cite: CabritBertout86).

[^10]: http://www.astropy.org

</paper>

Write the methods card for this paper.