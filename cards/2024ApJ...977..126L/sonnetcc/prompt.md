# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977..126L\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977..126L",
 "title": "Multiple Components of the Outflow in the Protostellar System HH 212: Outer Outflow Shell, Rotating Wind, Shocked Wind, and Jet",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "López-Vázquez, J. A.",
 "n_authors": 11,
 "arxiv_id": "2411.01728",
 "doi": "10.3847/1538-4357/ad8eb4",
 "alma_projects_linked_by_archive": [
  "2011.0.00647.S",
  "2012.1.00122.S",
  "2015.1.00024.S",
  "2015.1.00041.S",
  "2016.1.01475.S"
 ]
}
```

Paper text:
<paper>
# Multiple Components of the Outflow in the Protostellar System HH 212:\
Outer Outflow Shell, Rotating Wind, Shocked Wind, and Jet

## Abstract

We present the Atacama Large Millimeter/submillimeter Array Band 7 observations of the CO ($J=3-2$) line emission of the protostellar system HH 212 at $\sim$24 au spatial resolution and compare them to those of the SiO ($J=8-7$) and SO ($J=8-7$) line emission reported in the literature. We find that the CO line traces four distinct regions: (1) an outer outflow shell, (2) a rotating wind region between the SiO and CO shells, (3) the shocked and wide-angle inner X-wind inside a SiO shell, and (4) the jet. The origin of the CO outer outflow shell could be associated with the entrained material of the envelope, or an extended disk wind. The rotating wind, which is shocked, is launched from a radius of $9-15\,\mathrm{au}$, slightly exterior to that of the previously detected SO shell, which marks the boundary where the wide-angle X-wind is interacting with and shocking the disk wind. Additionally, the SO is found to be mixed with the CO emission within the thick and extended rotating wind region. The large scale CO shocked wind coexists with the SO emission near the upper portion of the inner shocked region converged on top of the inner SiO knots. The CO jet is traced by a chain of knots with roughly equal interval, exhibiting quasi-periodicity, as reported in other jets in the literature.

[^1]

# Introduction

The earliest phases of the star formation process (Class 0/I, with ages of $\leq10^4$ yr and $\sim10^5$ yr, respectively, (cite: Andre2000)) are dominated by high accretion of material from the envelope to the protostar-disk system ((cite: Hartmann1996)). As a result of the conservation of angular momentum due to the accretion, the protostar-disk system ejects material from the inner region of the disk in the form of jets and bipolar outflows. Although the jets and outflows are predominantly observed in young protostellar systems (Class 0/I), e.g., the Herschel Orion Protostar Survey (HOPS; (cite: Furlan2016); (cite: Hsieh2023)), ALMA Survey of Orion Planck Galactic Cold Clumps (ALMASOP; (cite: Dutta2020); (cite: Dutta2024)), the Perseus ALMA Chemistry Survey (PEACHES; (cite: Yang2021)), and CALYPSO ((cite: Podio2021)), several jets and outflows associated with more evolved systems (Class II, with an age of $\sim10^6$ yr, (cite: Andre2000)) have also been observed, such as IRAS 16316-1540, T Tau, and GK /GI Tau ((cite: Arce2006)), DO Tauri ((cite: FernandezLopez2020)), and HH 30 ((cite: Pety2006)).

Both jets and outflows may be responsible for removing excess angular momentum from the protostar-disk system ((cite: Ray2007)). This angular momentum is carried away by the vertical magnetic field lines anchored to the disk by the magneto-centrifugal mechanism ((cite: Blandford1982)). The magnetic field lines can be anchored in two regions: close to the central star, where the stellar magnetosphere truncates the disk, known as X-winds ((cite: Shu1994); (cite: Shang1998)), and a wider range of radii, known as disk-winds ((cite: Pudritz1983; Pudritz1986)).

While the jets are associated with material ejected directly from the disk, outflows are described as swept-up material, tracing the interaction between an inner jet or fast stellar winds with the infalling envelope or parent cloud (e.g., (cite: Shu1991); (cite: Matzner1999); (cite: Li2013); (cite: JALV2019); (cite: Shang2023a)). The entrainment of the material can be explained in two different ways, by the jet-driven bow shocks (e.g., (cite: Masson1993); (cite: Raga1993); (cite: Lee2001); (cite: Ostriker2001); (cite: Rabenanahary2022); (cite: RiveraOrtiz2023)) or a wide-angle wind ((cite: Li1996); (cite: Ostriker1997); (cite: Lee2000); (cite: Liang2020)). In the first scenario, the jet propagates into the surrounding cloud and forms bow shocks which push and accelerate the ambient gas, producing outflow shells surrounding the jet (e.g., (cite: Raga1993)). In the second scenario, a radial wind pushes against into the ambient material, forming a radially expanding outflow shell (e.g., (cite: Lee2000)). These two entrainment processes could act simultaneously, as the jet bow shocks and the wide-angle wind may coexist (e.g., (cite: Lee2015; Lee2021; Lee2022)). A unified model of the outflow is presented in (cite: Shang2006; Shang2020), where the outflows are formed by the interaction of a fast wide-angle wind launched from the innermost region (consistent with the X-wind scenario) with the ambient medium. A unified model of the outflows, where jet-driven and wide-angle scenarios are integrated, is presented in (cite: Shang2006; Shang2020). They found that the outflows are formed by the interaction of a wind launched from the innermost region (consistent with the X-wind scenario) with the ambient medium.

Recent radio interferometric and high resolution infrared observations reveal three important characteristics of the outflows. First, outflows exhibit internal structures such as nested/multiple shells connecting to the knots and bow shocks driving them (e.g., (cite: Lee2015); (cite: Schutzer2022)), and associated with episodic ejections (e.g., (cite: Louvet2018); (cite: Zhang2019); (cite: FernandezLopez2020); (cite: Podio2021); (cite: dValon2022); (cite: Harada2023); (cite: Flores2023); (cite: JALV2024)), and bubbles (e.g., (cite: Vazzano2021)). Second, outflows present velocity gradients across the outflow axis, which are interpreted as rotation, e.g., CB 26 ((cite: Launhardt2009; Launhardt2023); (cite: JALV2023)), Ori-S6 ((cite: Zapata2010)), DG Tau B ((cite: Zapata2015); (cite: dValon2020; dValon2022)), TMC1A ((cite: Bjerkeli2016a)), Orion Source I ((cite: Hirota2017); (cite: JALV2020)), HH 212 ((cite: Lee2018; Lee2021)), HH 30 ((cite: Louvet2018); (cite: JALV2024)), NGC 1333 IRAS 4C ((cite: Zhang2018)), and HD 163296 ((cite: Booth2021)). Finally, the jet-outflow system exhibits an onion-like kinematic and chemical structure, with different layers showing decreasing velocity and associated with the emission of various tracers, such as SO and SO$_2$ in the case of HH 212 ((cite: Tabone2017); (cite: Lee2021)), and CO, H$_2$, and \[FeII\] in the cases of DG Tau B ((cite: dValon2020; dValon2022); (cite: Delabrosse2024)) and HH 46/47 ((cite: Nisini2024)).

The protostellar system HH 212 is located in the L1630 cloud of Orion B at a distance of $\sim423\pm21$ pc ((cite: Zucker2019)). The central source has an age of $\sim40000$ yr ((cite: Lee2014)) and a mass of $0.25\pm0.05\mathrm{M_\odot}$ ((cite: Codella2014); (cite: Lee2014)). HH 212 is a very well-studied system with a flattened envelope ((cite: Lee2014; Lee2017ApJ)) accreting material to a protostar-disk system. The system exhibits a dusty edge-on accretion disk ((cite: Lee2017Sc)) with an inclination angle with respect to the line of sight $i\sim86^{\circ}$ ((cite: Claussen1998)) and with an atmosphere rich in complex molecules such as CH$_2$DOH, CH$_3$OH, CH$_3$SH, NH$_2$CHO, D$_2$CO, HNCO, H$_2$CO, H$_2$CO$^{13}$, and CH$_3$CHO ((cite: Lee2017ApJ; Lee2022mol)). It presents a very prominent SiO rotating jet launched from the innermost disk, $\approx 0.05\, \mathrm{au}$ ((cite: Podio2015); (cite: Lee2017Nat); (cite: Codella2023)). In recent studies, (cite: Tabone2017) and (cite: Lee2018; Lee2021), through the emission of the different transitions of SO and SO$_2$ lines found that the outflow presents signatures of the rotation and an onion-like structure consistent with a radially extended magnetohydrodynamic (MHD) disk wind launched up to 40 au. Additionally, (cite: Lee2021) detected that SO emission exhibits an inner shell at a radius of $\sim$ 4 au, which they proposed could trace the interaction of the extended wide-angle MHD disk wind with large bow shocks driven by the time-variable jet ((cite: Tabone2018)). Finally, (cite: Lee2022) found that the HH 212 protostellar system has an SiO shell, whose base is associated with the SO inner shell, they showed that the SiO shell shape and kinematics is formed by the radial component of the wide-angle X-wind expanding into the outer disk wind by the cumulative effect of several large jet bow shocks impacting an outer disk wind ((cite: Tabone2018)).

+---------------+-------------+-------------------------------+----------------+
|               |             | Synthesized Beam              |                |
+:=============:+:===========:+:==================:+:========:+:==============:+
| 3-4           |             |                    |          |                |
+---------------+-------------+--------------------+----------+----------------+
| CO ($J=3-2$)  | 345.7959899 | 0.059$\times$0.057 | 51.36    | 2015.1.00024.S |
+---------------+-------------+--------------------+----------+----------------+
|               |             |                    |          | 2015.1.00041.S |
+---------------+-------------+--------------------+----------+----------------+
|               |             |                    |          | 2016.1.01475.S |
+---------------+-------------+--------------------+----------+----------------+
| SiO ($J=8-7$) | 347.330631  | 0.055$\times$0.050 | 54.53    | 2015.1.00024.S |
+---------------+-------------+--------------------+----------+----------------+
|               |             |                    |          | 2016.1.01475.S |
+---------------+-------------+--------------------+----------+----------------+
| SO ($J=8-7$)  | 346.528481  | 0.057$\times$0.055 | 50.42    | 2015.1.00024.S |
+---------------+-------------+--------------------+----------+----------------+
|               |             |                    |          | 2016.1.01475.S |
+---------------+-------------+--------------------+----------+----------------+
| Continuum     | 358         | 0.020$\times$0.017 | -63.18   | 2015.1.00024.S |
+---------------+-------------+--------------------+----------+----------------+

In previous works, (cite: Lee2015) and (cite: Podio2015) reported the emission of the CO molecular line of the HH 212 source at large scales with low angular resolution ($\gtrsim$0$^{\prime\prime}.5$). They observed that the outflow exhibits a nested shell structure and found internal working surfaces associated with the bow shock emission. In this paper, we present high-angular resolution observations of the CO molecular line emission. We focus on a region close to the central source ($z\lesssim\pm1500\,\mathrm{au}$) and we will compare the CO molecular line emission with the previously reported emission of the SiO and SO molecular lines. The paper is organized as follows: in Section [2](#sec:observations) the observations are detailed. We show the results in Section [3](#sec:results). These results are discussed in Section [4](#sec:discussion). Finally, our conclusions are presented in Section [5](#sec:conclusions).

# Observations

In this work, we used three ALMA data sets of the HH 212 protostellar system from the following projects: 2015.1.00024.S (PI: Chin-Fei Lee), 2015.1.00041.S (PI: John Tobin), and 2016.1.01475.S (PI: Claudio Codella). The data were calibrated using the Common Astronomy Software Application (CASA) package ((cite: CASAteam)) versions 4.5.0, 4.7.2, and 4.7.0 for the projects 2015.1.00024.S, 2015.1.00041.S, and 2016.1.01475.S, respectively. During the imaging process, for all data sets, a Briggs weighting robust parameter of 0.5 was applied to balance sensitivity and angular resolution.

Band 7 high angular resolution of the HH 212 protostellar system was carried out with ALMA using 32-45 12 m antennas with two executions in 2015, one on November 5 and the other on December 3, during the Early Science Cycle 3 phase (2015.1.00024.S), 34-42 12 m antennas on 2016 September 6 and 2017 July 19 during the Cycle 4 phase (2015.1.00041.S), and 44 12 m antennas between October 6 and November 26, 2016 during the Cycle 4 phase (2016.1.01475.S). The maximum baselines are 16196 m, 3697 m, and 3000 m for the Cycles 3 and 4, respectively. The details of the observations have been reported in (cite: Lee2017ApJ) for Cycle 3, (cite: vanthoff2018) and (cite: Tobin2019) for Cycle 4 (2015.1.00041.S), and (cite: Bianchi2017) and (cite: Tabone2017) for Cycle 4 (2016.1.01475.S).

The continuum image rms noise is 0.15 mJy/Beam and the line images have an rms noise level of 2.11 mJy/Beam, 0.96 mJy/Beam, and 0.92 mJy/Beam for the CO, SiO, and SO, respectively. Details of the synthesized beam and rest frequencies are provided in Table [\[tab:obshighres\]](#tab:obshighres).

![](f1.pdf)

# Results

To provide readers with a more comprehensive view of the HH 212 system, we used the low angular resolution dataset ($\sim$0$^{\prime\prime}$.37) from the following projects: 2011.0.00647.S (PI: Claudio Codella), 2012.1.00122.S (PI: Chin-Fei Lee), and 2016.1.01475.S (PI: Claudio Codella). These datasets help contextualize the different scales for our analysis. Additionally, the continuum maps are used as a reference to locate the central object. This paper is focused on presenting and discussing the emission of the CO molecular line; however, the SiO and SO molecular lines are also presented here for our comparison. Also, for clarity in the figures, all the maps are rotated by $22^\circ.5$ clockwise so that the jet axis aligns with the $y-$axis.

The systemic velocity in HH 212 is $V_\mathrm{sys}=1.7\pm0.1\,\mathrm{km\,s^{-1}}$ ((cite: Lee2014)). To facilitate the interpretation of the results, we define an offset velocity $V_\mathrm{off}= V_\mathrm{lsr}-V_\mathrm{sys}$.

![](f2.pdf)

## Comparison between Molecules

Figure [1](#fig:molecules_resolution) shows the ALMA moment zero or integrated intensity maps of the emission of the CO (red), SiO (green), and SO low-velocity (LV) (blue) molecular lines overlaid on the white contours of the 358 GHz continuum map of the disk (adopted from (cite: Lee2017Sc)) in the protostellar system HH 212. The CO and SiO maps were integrated over a velocity range of $\pm11\,\mathrm{km\,s^{-1}}$, while the SO (LV) was integrated over a range of $\pm 3\,\mathrm{km\,s^{-1}}$; all velocities are relative to the systemic velocity $V_\mathrm{sys}$. For the SO emission, we use the low-velocity emission that traces the outflow, as shown in (cite: Lee2021). Another reason that we do not consider the high-velocity emission of the SO is because this line falls outside of the spectral set-up of the dataset ((cite: Tabone2017)).

Figure [1](#fig:molecules_resolution)a displays the map obtained with the low angular resolution data of the outflow presented by (cite: Lee2015), within $\pm4800\,\mathrm{au}$ of the central star. The high angular resolution data are presented in Figure [1](#fig:molecules_resolution)b, where the emission is plotted within $\pm1600\,\mathrm{au}$ of the central star. In both figures, the CO emission reveals an outflow shell previously reported by (cite: Lee2015). Additionally, both CO and SO trace the molecular outflow near to the accretion disk ($z\lesssim |200|\,\mathrm{au}$). The jet and a shell around the jet are traced by the SiO emission (see (cite: Lee2017Nat; Lee2022)). The high angular resolution data suggest that CO is likely tracing the shocked wind within the SiO shell. Notably, while CO, SiO, and SO emissions coexist in the central region, the external region is predominantly dominated by CO emission.

![](f3.pdf)

![](f4.pdf)

The comparison between CO molecular line emission and the SiO jet, as well as the SO (LV) molecular outflow within $\pm 500\,\mathrm{au}$ is presented in Figures [1](#fig:molecules_resolution)c and d, respectively. Figure [1](#fig:molecules_resolution)c illustrates the comparison between CO outflow and the SiO jet. At low heights ($z\lesssim |200|\,\mathrm{au}$), the jet is dominated by knots, while CO traces the outflow around the jet. On the other hand, the comparison between the CO and SO (LV) molecular outflows are presented in Figure [1](#fig:molecules_resolution)d. We observe that the wind previously detected in SO and identified as a wide-angle disk wind ((cite: Tabone2017); (cite: Lee2021)) coexists with the CO. It is important to note that in a region around the central star ($z\lesssim |600|\,\mathrm{au}$), the HH 212 protostellar outflow exhibits an onion-like structure.

In Figure [1](#fig:molecules_resolution), the outermost region relative to the jet axis is dominated by the emission of the CO outer shell, which connects with the knots and bow shocks driven by them observed along the jet axis at large scales, as previously reported by (cite: Lee2015). At heights of $z\geq |400|\,\mathrm{au}$, we detect an internal cavity between the CO outer shell and the SiO shell. For heights $z\leq |400| \,\mathrm{au}$, outside the SiO shell, the emission is dominated by the SO and CO wind. Finally, inside the SiO shell, we observe the CO wind and the SiO jet.

## CO Structure: an Outer Outflow Shell, Internal Cavity, Rotating Wind, Shocked Wind, and Jet

![](f5.pdf)

The CO maps integrated over different velocity ranges are shown in Figure [2](#fig:moment0). Figures [2](#fig:moment0)a and [2](#fig:moment0)b display the blueshifted and redshifted CO emission, respectively, integrated over velocities ranging from -9.3 to 1.7 $\mathrm{km\,s^{-1}}$ and from 1.7 to 12.7 $\mathrm{km\,s^{-1}}$, relative to the systemic velocity $V_\mathrm{sys}$. The northern component of the outflow is traced by the blueshifted emission, while the southern component dominates the redshifted emission. However, within $z\lesssim |400|\,\mathrm{au}$, the outflow emits in both velocity regimes. Figure [2](#fig:moment0)c displays the total CO intensity map integrated over all velocity ranges, $\pm11\,\mathrm{km\,s^{-1}}$ away from the systemic velocity $V_\mathrm{sys}$. The innermost contours in Figure [2](#fig:moment0) trace possible CO knots associated with the jet. Additionally, Figure [2](#fig:moment0)c shows an outer outflow shell (red dashed lines), an internal cavity, and emission features around $z\lesssim |900|\,\mathrm{au}$ including the rotating wind (red arrows) and CO shocked wind inside the SiO shell (see Figure [1](#fig:molecules_resolution)). We infer that the CO shell is produced by the interaction of ejected material from the protostar-disk system with the envelope. While the region between the CO and SiO shells may trace the material directly ejected from the disk, so-called disk wind and previously reported by the SO and SO$_2$ emission by (cite: Tabone2017) and (cite: Lee2018; Lee2021), or it could trace the shocked wind resulting from the interaction of the wind launched directly from the innermost disk with the ambient medium, known as shocked wind ((cite: Shang2023a)). For the reader’s convenience, and considering that this region has been extensively studied in previous works and the gas presents signatures of the rotation (e.g., (cite: Tabone2017; Lee2018; Lee2021)) and shocks, we will henceforth refer to this region as the so-called “rotating wind”, regardless of its origin. Finally, the CO emission inside the SiO shell may trace the shocked wind resulting from the interaction between the wide-angle component of the X-wind with the surroundings (envelope or rotating wind) or it could trace the material ejected sideways from the knots and bow shocks along the jet axis (e.g., (cite: Tabone2018; Rabenanahary2022; RiveraOrtiz2023)). For simplicity, and since the CO emission traces the interaction of different components of the protostellar system, we will refer to this region as the “shocked wind”.

![](f6.pdf)

To provide a more detailed view of the chain of CO knots associated with the jet, Figure [3](#fig:zoom_knots) presents a zoomed-in view of the CO total intensity map around the jet axis, overlaid with the SiO map (green contours). Only the emissions exceeding 10$\sigma$ for CO and 9$\sigma$ for SiO are plotted to better illustrate their distinct distributions. Red points mark the positions of the CO knots in the northern (KN1–KN4) and southern (KS1–KS6) components. The positions of the knots were determined from the emission peaks with detections exceeding $>10\sigma$, as identified from the Gaussian fits. In contrast to the chain of SiO knots ((cite: Lee2017Nat)), the CO knots are detected further away from the central star ($z\gtrsim |100|\,\mathrm{au}$).

![](f7.pdf)

![](f8.pdf)

Figure [4](#fig:knots_position) shows the width of the CO knots as a function of the projected distance from the central source. To determine the width of the knots, we used the method developed in (cite: Lee2017Nat). We extracted spatial profiles from the CO intensity map (Figure [3](#fig:zoom_knots)) and fitted these profiles with a Gaussian profile. The plot reveals a slight increase in the width of the knots with the projected distance, as indicated by the dashed red lines in both panels. The positions and widths of the SiO knots in the northern (N1-N3) and southern (S1-S3) components were taken from (cite: Lee2017Nat), with the exception of knot N4. The position and width of knot N4 were measured using the same method applied to the CO knots.

Figures [3](#fig:zoom_knots) and [4](#fig:knots_position) show that the CO knots are associated with four different episodic ejections: KN1–KN3 (together with KS1–KS2), KN3 (with KS3), KN4 (with KS4–KS5), and KS6. The average distance between these ejections is $140\pm14\,\mathrm{au}$, with a timescale of $5.2\pm0.6$ yr, assuming a jet velocity of $\sim135\,\mathrm{km\,s^{-1}}$ ((cite: Zinneckar1998; Lee2017Nat)). Within these episodic ejections, we observe that the knots (KN1–KN2–KN3, KS1–KS2, and KS4–KS5) are separated by an average distance of $49\pm13\,\mathrm{au}$, with a timescale of $1.8\pm0.4$ yr. This suggests that the jet exhibits quasi-periodicity. This quasi-periodicity may be associated with variations in the ejection velocity of the jet ((cite: Moraghan2016)) or with magnetic pseudopulses, which tends to be periodic and can create perturbations in density and velocity, resulting in the appearance of knots ((cite: Shang2002; Shang2020)).

## Kinematic Properties of the Protostellar System: Rotating Outflow Shells and Interaction between Wide-Angle Winds and the Ambient Envelope

Figure [5](#fig:moment1) displays the first moment, or intensity-weighted velocity map of the CO emission line, overlaid by the black contours of the CO total intensity map. In Figure [5](#fig:moment1)a, the emission is shown up to $\pm 1600\,\mathrm{au}$, with blueshifted velocities observed on the east-side and redshifted velocities on the west-side. Figure [5](#fig:moment1)b focuses on the central region, with red and blue contours indicating the redshifted and blueshifted low-velocity emission from the SO molecular line, respectively, and the black contours show the 358 GHz continuum map of the disk (adopted from (cite: Lee2017Sc)). It is noteworthy that the outflow exhibits a velocity gradient across the outflow axis, which is associated with the rotation of gas at $\sim1.5\,\mathrm{km\,s^{-1}}$. This rotation velocity is consistent with previous reports of the emission from SO and SO$_2$ by (cite: Tabone2017) and (cite: Lee2018; Lee2021) and it has the same direction as the rotation of the disk, envelope, and SiO jet (e.g., (cite: Codella2014; Lee2014; Lee2017Nat)). Furthermore, further away from the central source, the outflow is predominantly blueshifted in the north and redshifted in the south, resembling the velocity sense of the bow shocks at larger distances, thus indicating that they are driven by them ((cite: Lee2015)), and showing strong dominance and influence from the surrounding envelope and the complex interactions weighted by uneven density inhomogeneity on both the blue side but not on the red side. Additionally, in Figure [5](#fig:moment1)b, the red SO emission clearly extends outside of the CO, which may indicate an extended and deeper connection to the outer envelope or it could simply be due to CO absorption by the cloud at $V\sim1.7\,\mathrm{km\,s^{-1}}$, at seen in Figure [8](#fig:pv_diskwinds).

The position-velocity (PV) diagram along the jet axis presented in Figure [6](#fig:pv_jetaxis) traces the emission of the CO (gray scale), SiO (green contours), and SO (blue contours) molecular lines. In Figure [6](#fig:pv_jetaxis)a, we find that further away from the central source, the SiO emission traces a shell in the PV ((cite: Lee2022)), while the CO and SO emission is dominated by the shocked wind. Close to the central source (dashed rectangle in Figure [6](#fig:pv_jetaxis)a, $z\leq|400|\,\mathrm{au}$), the SiO emission (Figure [6](#fig:pv_jetaxis)b) traces the jet, while the SO emission (Figure [6](#fig:pv_jetaxis)c) in the northern region exhibits a classic parabola shape (magenta lines) previously reported by (cite: Lee2018), in the southern region, we do not detect this shape as the SO falls outside of the spectral set-up ((cite: Tabone2017)). This parabola is associated with an expanding shell swept up by successive bowshocks ((cite: Lee2021)) or by wide-angle X-wind ((cite: Lee2022)).

Considering that the CO molecular line emission of the HH 212 protostellar system traces various components, such as an outer outflow shell, the rotating wind, the shocked wind, and a chain of the knots associated with the jet, we will separate the observed region by height into two different regions, further away and close to the central source, $z>|200|\,\mathrm{au}$ and $z\leq |200|\,\mathrm{au}$, respectively. The lack of CO emission around $V_\mathrm{off}=0$ is because the outflow emission at this velocity is absorbed by the parent cloud. Similarly, the lack of CO emission around $V_\mathrm{off}\sim7\,\mathrm{km\,s^{-1}}$ is because the outflow emission at this velocity is absorbed by another cloud in front of HH 212 (cite: Lee2000).

### Kinematic Properties Further at Larger than 200 au

As observed in Figure [6](#fig:pv_jetaxis), the source presents a structure of multiple shells with different velocities, also known as an onion-like velocity structure. To confirm this, PV diagrams perpendicular to the jet axis are displayed in Figure [7](#fig:pv_xwinds). The PV diagrams were made from $z=\pm300\,\mathrm{au}$ to $z=\pm400\,\mathrm{au}$ every 50 au. The CO emission is shown in grayscale and the SiO and SO emissions are plotted in green and blue contours, respectively. In all panels, we observe that the CO traces two different regions, a low-velocity extended shell (red ellipses) associated with the outer outflow shell presented in Figures [1](#fig:molecules_resolution) and [2](#fig:moment0), and a high-velocity component around the jet axis, which may indicate the presence of a shocked wind. The SiO molecular line emission forms a shell between the emission of the CO high-velocity component and the low-velocity extended shell, while the SO emission may be tracing the region between the SiO shell and the CO high-velocity component.

![image](f9a.pdf)![image](f9b.pdf) ![image](f9c.pdf)![image](f9d.pdf)

### Kinematic Properties Close to Central Source

PV diagrams perpendicular to the jet axis at different heights close to the central source ($z\leq |200|\,\mathrm{au}$) are shown in Figure [8](#fig:pv_diskwinds). The diagrams were made from $z=\pm 50\,\mathrm{au}$ to $z=\pm200\,\mathrm{au}$ every 30 au. The CO emission is traced in grayscale, while the emission of the SiO and SO is plotted in green and blue contours, respectively. At heights between $|50|\,\mathrm{au}\leq z\leq |110|\,\mathrm{au}$, the CO and SO emissions are spatially consistent and exhibit the same velocity, while the SiO emission is dominated by the jet and traces a narrow region with a high velocity dispersion. In contrast, at heights $z>|110|\,\mathrm{au}$, the CO and SO coexist spatially; however, the SO traces gas of low velocity and the CO traces gas over a wider range of the velocities with respect to SO, lower than those of the SiO. The SiO shows regions close to the jet axis, but with less velocity dispersion than in the regions closer to the disk.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  | PA | $R$ | $V_\mathrm{exp}$ | $V_\mathrm{rot}$ | $V_{z}$ |
|  |  |  |  |  |  | $(^{\circ})$ |  |  |  |  |
| Low-velocity | 200 | 0.996 | 0.618 | 4.670 | 0.307 | 1.151 | 135.710 | 4.478 | 1.363 | 8.854 |
| (Red ellipses) | 170 | -0.524 | 0.554 | 4.621 | 0.296 | 1.168 | 131.305 | 4.415 | 1.400 | 8.091 |
|  | 140 | -4.328 | 0.560 | 4.543 | 0.292 | 1.240 | 130.207 | 4.317 | 1.450 | 8.023 |
|  | 110 | -7.308 | 0.549 | 3.962 | 0.279 | 1.593 | 126.806 | 3.696 | 1.451 | 7.865 |
|  | 80 | -1.056 | 0.548 | 3.361 | 0.248 | 2.224 | 118.629 | 2.985 | 1.557 | 7.860 |
|  | 50 | 3.164 | 0.547 | 3.154 | 0.218 | 2.509 | 109.260 | 2.675 | 1.681 | 7.838 |
|  | -50 | -11.280 | 0.554 | 3.147 | 0.228 | 2.538 | 112.881 | 2.693 | 1.636 | 7.940 |
|  | -80 | -15.308 | 0.581 | 3.458 | 0.248 | 2.149 | 118.396 | 3.074 | 1.595 | 8.340 |
|  | -110 | -25.300 | 0.574 | 3.902 | 0.275 | 1.672 | 125.868 | 3.615 | 1.489 | 8.227 |
|  | -140 | -29.352 | 0.590 | 4.441 | 0.291 | 1.277 | 129.860 | 4.215 | 1.428 | 8.464 |
|  | -170 | -19.540 | 0.603 | 4.727 | 0.301 | 1.144 | 133.220 | 4.522 | 1.413 | 8.640 |
|  | -200 | -17.204 | 0.614 | 4.812 | 0.315 | 1.131 | 139.315 | 4.619 | 1.385 | 8.806 |
| High-velocity | 110 | -4.684 | 0.788 | 7.056 | 0.193 | 0.085 | 81.641 | 7.063 | 0.383 | 11.293 |
| (Brown ellipses) | 80 | -2.996 | 0.921 | 6.173 | 0.158 | 0.158 | 67.226 | 6.153 | 0.664 | 13.206 |
|  | 50 | -4.444 | 0.764 | 5.544 | 0.135 | 0.177 | 57.561 | 5.514 | 0.698 | 10.952 |
|  | -50 | -19.272 | 0.803 | 5.828 | 0.143 | 0.173 | 61.124 | 5.799 | 0.710 | 11.516 |
|  | -80 | -9.948 | 0.945 | 6.022 | 0.169 | 0.154 | 71.682 | 6.010 | 0.575 | 13.549 |
|  | -110 | -9.588 | 0.820 | 6.474 | 0.174 | 0.112 | 73.745 | 6.473 | 0.471 | 11.761 |

The extended vertically distributed emission around $V_\mathrm{off}=0$ in Figure [8](#fig:pv_diskwinds) may be attributed to emission from the parent cloud or associated with ambient material of the outskirts of the outflow (e.g., (cite: Shang2023a); (cite: Ai2024)). The velocity gradient along the line of sight detected in the velocity map of Figure [5](#fig:moment1) is also observed in these PV diagrams, indicating substantial dominant ambient contribution to the blue side by preexisting cloud inhomogeneity. Note that the CO emission exhibits a possible shell structure consistent with radially expanding shells ((cite: Arce2011); (cite: Zapata2014)), similar to the SO emission observed in Figure [6](#fig:pv_jetaxis). This could be indicative of the elliptical structure expected in the perpendicular PV diagrams of an outflow with a low inclination angle with respect to the plane of the sky ((cite: Lee2000)).

To determine the kinematic and physical properties of the outflow, we performed cuts in each PV diagram at intervals of $0^{\prime\prime}.06$ (synthesized beam size). From these cuts, we extracted spatial profiles and identified the 2$\sigma$ limit, correlating these with positions in the PV diagram. Each position defines a point in the PV diagram. We then fitted ellipses to the points associated with the 2$\sigma$ limit following the CO and SO data in all PV diagrams for red ellipses (which exclude the high-velocity components) and for $z\leq|110|\,\mathrm{au}$ for the dashed brown ellipses (which concentrate on the higher-velocity portion of the data closer to the disk) of Figure [8](#fig:pv_diskwinds). We do not fit ellipses to the higher-velocity emission at heights $z>|110|\,\mathrm{au}$ because the emission is dominated by the low-velocity components, making it complex to distinguish the boundary between the two. After the fitting, we obtained the parameters of the ellipse, position angle (PA), major ($a$) and minor ($b$) axes, and the coordinates of the center ($r_\mathrm{cent}$, $V_\mathrm{cent}$). Using the outflow model presented by (cite: Louvet2018), we estimated the physical properties of the outflow, such as cylindrical radius ($R$), radial expansion velocity ($V_\mathrm{exp}$), rotation velocity ($V_\mathrm{rot}$), and subsequently, we estimate the specific angular momentum ($j_\mathrm{obs}$). The parameters obtained from our fits and the values of the $R$, $V_\mathrm{exp}$, $V_\mathrm{rot}$, and the axial velocity $V_z$ are shown in Table [\[tab:parameters\]](#tab:parameters). The expansion, rotation, and axial velocities are corrected for the inclination angle with respect to the line of sight $i\sim86^{\circ}$ ((cite: Claussen1998)).

The fitted ellipses are used to determine the physical properties depicted in Figure [9](#fig:dwparameters). The red and brown sets of ellipses produce two parallel sets of data lines, displaying consistent differences and similarities. The top left panel displays the assumed cylindrical radius as a function of the height for a conical shell. These radii increase with height, indicating the expansion of the shell. The top right panel of Figure [9](#fig:dwparameters) illustrates the expansion velocity, which also increases with height, as observed in PV diagrams depicted in Figure [8](#fig:pv_diskwinds). The rotation velocity is depicted in the bottom left panel and decreases with height, consistent with findings from prior research by (cite: Lee2018). The bottom right panel shows the specific angular momentum $j_\mathrm{obs}=R\times V_\mathrm{rot}$. The specific angular momentum from the red ellipses maintain constant at around 190 $\mathrm{au}\,\mathrm{km\,s^{-1}}$, while for the brown ellipses is around 50 $\mathrm{au}\,\mathrm{km\,s^{-1}}$. Error bars for these properties are estimated by propagating the statistical uncertainties derived from the ellipse fitting incorporated into the outflow model of (cite: Louvet2018). Stronger than most of these $z$-dependence, are the consistent differences between the red and brown sets of ellipses. These show smaller $R$, $V_\mathrm{rot}$, and $j_\mathrm{obs}$ for the brown set. The smaller $V_\mathrm{exp}$ for the red set of ellipses is consistent with their choice of avoiding high-velocity data in the PV.

Both sets of ellipses are subject to possible overestimates of rotation velocity $V_\mathrm{rot}$, and therefore the specific angular momentum $j_\mathrm{obs}$, because the ellipses method is only valid for a narrow emitting ring, given that, for radially extended disk winds, we observe the summed contribution of the a broad range of the rings. The poloidal and the vertical velocities present high uncertainties associated with a very high inclination angle of the jet axis to the line of sight.

Several PV diagrams shown in Figures [7](#fig:pv_xwinds) and [8](#fig:pv_diskwinds) may be contaminated by the emission from CO and SiO knots; however, this emission does not affect the estimation of the physical parameters of the outflow because the knots trace the emissions of higher intensity ($>10\sigma$) and higher velocity ($V_\mathrm{off}>|5|\,\mathrm{km\,s^{-1}}$) around the jet axis. Our estimations were based on the emission at $2\sigma$.

![](f10.pdf)

# Discussion

## Onion-like Spatial and Kinematic Structures

Figure [10](#fig:cartoon)a summarizes the different components of the HH 212 protostellar system. Given that the outflow has a very low inclination angle with respect to the plane of the sky, the high angular resolution observations reveal a well-defined onion-like spatial structure. From outermost to axial regions, one can observe the infalling envelope ((cite: Lee2014; Lee2017ApJ)), the cavity wall ((cite: Codella2014); (cite: Tabone2017)), the outer outflow shell, the slow wind that is rotating, the SiO shell, the axially extended shocked wind region, and the jet.

The CO outer shell depicted in Figure [10](#fig:cartoon)a is associated with the molecular outflow observed through CO molecular line emission ((cite: Lee2015)). This shell, traced by CO, could result from swept-up material by the outflowing gas from the star or the disk (e.g., (cite: Snell1980); (cite: Shu1991); (cite: JALV2019)), or from the interaction between the wind launched very close to the central star or the jet with the ambient material, (e.g., (cite: Li1996); (cite: Canto2006); (cite: Shang2023a)). Further discussion on the possible origins of these layers of gas will be provided later.

From the outer to inner regions, the system is characterized by the three dominant components: (1) the rotating wind region, traced by the emission of the CO and SO molecular lines, confined by an outer shell, and (2) the SiO shell, and (3) the CO shocked wind and the wide-angle component of the X-wind inside of the SiO shell.

The SiO shell on the parallel PV diagram, located between the wide-angle MHD wind and shocked wind, was identified by (cite: Lee2022). The SiO shell on the PV diagram marks the separation between the large-scale elongated shocked region where CO and SO coexist, and the base SiO jet emission displaying large velocity widths arising in the wide-angle X-wind (cite: Lee2022). It was proposed that the SiO shell could arise by the cumulative effect of several large jet bow shocks impacting an outer disk wind ((cite: Lee2021)), or by a radial component of the wide-angle X-wind expanding into the extended disk wind. The presence of the extended SiO nebulous emission-filled structure is, in fact, consistent with the existence of the large shocked wind region surrounded and confined by the poloidal magnetic field in the compressed ambient region as shown in (cite: Shang2020; Shang2023b). The large-scale axially extended SiO-filled shocked wind region is downstream of the reverse shock cavity, interfacing the newly launched wide-angle X-wind and the lateral disk wind region dominated by CO and SO.

Another explanation of the origin of the CO shocked wind inside of the SiO shell is material ejected sideways from the CO and SiO knots. (cite: Tabone2018) explored the interaction between a pulsating jet and a surrounding disk wind. In their simulations, the perturbations of the disk wind, caused by bow shocks are confined inside a cone, while the gas outside of this cone remains unperturbed disk wind material.

Figures [1](#fig:molecules_resolution)b and [5](#fig:moment1)b show that the CO molecular line traces the same spatial region as the SO. In Figure [6](#fig:pv_jetaxis)c, CO traces the material within the expanding shell on the PV diagram. Therefore, it can be inferred that CO in a region close to the central source, $z\leq |200|\,\mathrm{au}$, could also be associated with the emission of the disk winds. The possible shocked CO emission is primarily characterized by the lower-$J$ CO transitions (3-2) in Band 7. The extended and elongated axial region, confined by the SiO shell, contain CO bullets and emission SO. This extended shocked wind region likely accumulates the shocked wind material accumulated from the previously shocked wide-angle portion of the X-wind ((cite: Lee2022)) interacting with the surrounding ambient environment, then advected downstream. Outside the SiO shell, and exterior to the base SO shell (lower cavity), CO, SO and SO$_2$ emission coexist in an horizontally extended region bounded from outside by the outer CO shell. Connecting the two upper and horizontal shocked regions are CO bridges crossing the SiO and SO shell-like structures.

The inner region is dominated by the emission of the episodic jet. (cite: Lee2017Nat) identified a chain of SiO rotating knots associated with the jet. These knots are situated close to the accretion disk, $z\leq |80|\,\mathrm{au}$. In contrast, we detect a chain of knots traced by CO emission, as shown in Figures [3](#fig:zoom_knots) and [4](#fig:knots_position). However, the CO knots are located at a greater distance compared to the SiO knots, $|100|\,\mathrm{au}\leq z\leq |700|\,\mathrm{au}$. The width of the CO knots, similar to that of the SiO knots, increases with distance from the central source. This may be due to a decrease in pressure along the jet axis, causing the knots to rapidly expand ((cite: Smith1997); (cite: Suttner1997)), or traced by larger blobs of compressed or shocked material advected or entrained from the outer interacting region ((cite: Wang2019)).

The spatial onion-like structure is also observed in the PV diagrams. Along the jet axis (Figure [6](#fig:pv_jetaxis)), the PV diagram reveals that the SiO emission, both spatially and in velocity range, encompasses the emission of CO and SO.

Figure [10](#fig:cartoon)b illustrates the structure observed in PV diagrams of Figure [7](#fig:pv_xwinds), wherein CO traces a slow outer shell, while the SiO delineates a faster internal shell. Inside the SiO shell, the emission is dominated by CO emission, which traces a shocked wind. Additionally, close to the central star, the PV diagrams (Figures [7](#fig:pv_xwinds) and [10](#fig:cartoon)c) show the emission of rotating winds traced by SO ((cite: Lee2021)) and CO, where SO is a shock tracer. In this region, a velocity gradient along the line of sight is observed, likely associated with rotation of the gas. Furthermore, the SiO emission predominantly comes from the jet, exhibiting a compact structure with higher velocities respect to the emission of the SO and CO.

The origin of the onion-like structure may be linked to the temperatures and critical densities of the molecular lines involved. For instance, the SiO jet has a temperature of 150 K and a critical density of $1.7\times10^6\,\mathrm{cm}^{-3}$ ((cite: Dutta2024)). Its emission is associated with dense gas, such as the knots in the jet and the shell formed by collisions between the wide-angle component of the X-wind with the disk wind.

The CO line observed in the shell and in the rotating wind might have a temperature of 50 K and a critical density of $1.2\times10^{4}\,\mathrm{cm}^{-3}$ ((cite: Dutta2024)), while CO associated with the shocked wind and with the jet has a temperature of 150 K and a critical density of $1.1\times10^4\,\mathrm{cm}^{-3}$. The distinction between these CO regions lies in the fact that the emission from the shell could be associated with entrained material by an outflowing gas, whereas the emission from the jet and the shocked wind could be heated by internal shocks between the launched gas and the jet. This explains why the shocked wind exhibits emission of the CO (3-2) (this work) and CO (6-5) ((cite: Codella2023)).

Finally, SO traces shocked gas by interactions, having a temperature ranging from 50 to 100 K and a critical density of $2\times10^{6}\,\mathrm{cm}^{-3}$ ((cite: Podio2015)). As such, SO may trace the interaction between the inner wide-angle portion of the X-wind, with a disk wind. We discuss in the following sections.

## Origin of the CO Emission and the Molecular Outflow

As mentioned above, CO molecular line emission is observed in various regions of the protostellar system HH 212, including the outer outflow shell, the rotating wind, the shocked wind, and the jet/X-wind. CO emission is typically associated with the molecular outflow, so we will discuss the origin of both together. Notice that, the CO emission associated with the CO shocked wind and the jet was already discussed in §[4.1](#subsec:origin_onion).

The origin of the various shells can be explained in several ways. (cite: Lee2006) found that the morphological relationship between the H$_2$ jet and the CO outflow and the kinematic behavior of the CO outflow along the jet axis, supports the jet-driven bow shock model. Additionally, (cite: Lee2015) showed that the CO shell is associated with knots and bow shocks driven by them, suggesting that sideways material ejections from knots within the outflow cavity form bow shocks and internal shells.

Furthermore, (cite: Rabenanahary2022) described that this multiple shell structure observed in this molecular outflow can be explained as a result of the interaction between a narrow jet with a stratified core. The main difference between this interaction and that of the jet with uniform core is that the outflows open much wider. Additionally, after several hundred years, the initial shell splits into a slow parabolic outer shell and an inner, faster shell tracing the jet-ambient interface; eventually these shells stop expanding at the base, and reach a maximum width and opening angle in excellent agreement with observations.

Another possible explanation for the origin of the outflow shell is that it results from entrained material from the envelope by the outflowing gas from the protostar-disk system. (cite: JALV2019) modeled a molecular outflow as a dynamical shell produced by the collision between an anisotropic stellar wind and a rotating cloud envelope in gravitational collapse ((cite: Ulrich1976)). In their model, the shell is fed by both the envelope and stellar wind, such that the mass and rotation velocity coming from the envelope, while the radial expansion results from the pushing effect of the outflowing gas.

However, the observed rotation velocity ($\sim 0.4$–$2\,\mathrm{km\,s^{-1}}$) is between two and ten times larger than the expected rotation velocity ($\sim0.1-0.2\,\mathrm{km\,s^{-1}}$) of the rotating envelope according to (cite: Ulrich1976), as previously reported in Orion Source I (cite: JALV2020). Therefore, it is plausible to consider that this faster rotation or asymmetry may arise from either an MHD disk wind (see (cite: Tabone2017; Tabone2020; Lee2021)) a possibility further discussed in §[4.2.1](#subsubsec:diskwind), or an envelope rotating faster than the Ulrich rate (cite: Mendoza2009) that mixes with shocked X-wind material through magnetized interaction in the region between the outer shell and the reverse shock, a possibility further discussed in §[4.2.2](#subsubsec:unifed). In all of these cases, the CO gas originates from the envelope.

In the region close to the central source, $z\leq |200|\,\mathrm{au}$, between the outer CO shell and the SiO shell, we observe that the CO and SO lines trace the rotating wind. This wind was discovered through SO and SO$_2$ emission by (cite: Tabone2017). Subsequently, (cite: Tabone2020) modeled the emission of this wind and assessed it to be consistent with MHD disk wind solutions, which are used for extracting the excess of the angular momentum from the accretion disk. On the other hand, (cite: Lee2018) found SO expanding shell. Through high angular resolution observations, (cite: Lee2021) confirmed the existence of this shell, which represents the inner limit where the SO shocked wind may exist. This shell has a inner boundary of $4-8\,\mathrm{au}$, while the disk wind is expected to launch from a range of $4-40\,\mathrm{au}$.

Two parameters to describe the MHD disk winds are the launching radius $R_\mathrm{launch}$ and the magnetic lever arm parameter $\lambda$. The $\lambda$ parameter describes the magnetic torque exerted by the disk wind (e.g., (cite: Pudritz2007); (cite: Alexander2014); (cite: Pascucci2022)).

### Free Ballistic Disk Wind Scenarios

![](f11.pdf)

(cite: Anderson2003) found a general relation between the velocity components of the wind at large distances and the rotation rate of the launching surface under following assumptions: (1) the wind is free, meaning that the wind is not interacting with other components of the protostellar system; (2) dynamically cold, such that the entropy effect is negligible; (3) the system is axisymmetric; (4) the system is in steady state and (5) the observation point is sufficiently distant from the launching point.

In the case of HH 212 protostellar system, the presence of the CO and SiO knots, the SiO shell, and the CO shell indicate that the disk wind is in constant interaction with the different components of the system and with itself. Thus, the wind is not free. Nevertheless, (cite: Tabone2018) described that the disk wind outside of the cone is unperturbed; therefore, it is possible to construct a free-wind model that fits the known observations. We connect the CO molecular line emission with the tracing of a MHD wind.

The following equation (cite: Anderson2003) allows to find the launching point of a free magnetocentrifugal MHD wind under the conditions of application mentioned above: $$\begin{equation}
    \label{eq:anderson}
    V_\mathrm{outflow}^2R_\mathrm{launch}^{3/2}+\frac{3}{2}\eta^2 R_\mathrm{launch}-2 R V_\mathrm{rot}\eta \approx 0,
\end{equation}$$ where $V_\mathrm{outflow}=\sqrt{V_\mathrm{p}^2+V_\mathrm{rot}^2}$, $V_\mathrm{p}=\sqrt{V_z^2+V_\mathrm{exp}^2}$ is the poloidal velocity determined by the radial expansion velocity $V_\mathrm{exp}$ and the axial velocity along the jet axis $V_z$, $R$ is the cylindrical radius, and $\eta=(GM_*)^{1/2}$, where the mass of the protostar is $M_*=0.25\pm0.05$ $\mathrm{M_\odot}$ ((cite: Codella2014; Lee2014)). The result of solving this equation is presented in Figure [11](#fig:shell_launch), where we observe that the launching radii for the red ellipses are $\sim9 - 15\,\mathrm{au}$ and for the brown ellipses they are $\sim1-2\,\mathrm{au}$. The red-ellipse values are consistent with those reported by (cite: Tabone2020) and (cite: Lee2021) detail comparison with synthetic PVs for MHD disk wind models, where they estimated launching radii between $4$–$40\,\mathrm{au}$, while the brown ellipse values are connected to larger expansion velocities.

As mentioned above, another parameter in the MHD disk winds is the magnetic lever arm parameter $\lambda\sim(r_\mathrm{A}/r_0)^2$, where $r_\mathrm{A}$ is the cylindrical radius at the Alfvén surface and $r_0$ is the launching point of the streamline that follows the wind. In previous works ((cite: Tabone2017; Tabone2020; Lee2021)), magnetic lever arm parameter of the SO disk wind was found to be $3.5$–$5.5$. We estimate the parameter $\lambda$ value of our CO observations in the asymptotic regime ($R/r_0\to \infty$) where the specific angular momentum extracted by the magnetic torque has been converted in matter rotation ((cite: Blandford1982)). The asymptotic values of the poloidal velocity and the specific angular momentum at different heights $z$ are ((cite: Blandford1982)): $$\begin{equation}
    \label{eq:vpol}
    V_\mathrm{p}=\sqrt{2\lambda-3}\sqrt{G\mathrm{M_*}/r_0},
\end{equation}$$ $$\begin{equation}
    \label{eq:vrot}
    R\times v_\mathrm{rot}=\lambda \sqrt{G \mathrm{M_*} r_0}.
\end{equation}$$ Figure [12](#fig:shell_lambda) shows the relation between the specific angular momentum $j=R\times v_\mathrm{rot}$ and the poloidal velocity $V_\mathrm{p}$ for the various solutions of the launching point $r_0$ and magnetic lever arm parameter $\lambda$. Based on our CO observations, we find that for the red ellipses the launching points are $r_0\approx9-15$ and the magnetic lever arm parameter is $\lambda\sim3-4.5$. These values are consistent with those previously reported for SO observations. However, for the brown ellipses, that do avoid the strong envelope inhomogeneities of the PV diagrams, the picture changes, giving a launching point $r_0\sim1\,\mathrm{au}$, substantially smaller, and $\lambda\sim2-2.5$.

![](f12.pdf)

Regarding the red ellipses, given that the launching point and the magnetic lever arm parameter estimated for the CO molecular line are within the range of previously reported values, we conclude that the CO in the region between the CO shell and SiO shell can be parameterized by means of a MHD disk wind launched from the region $\sim15$–$40\,\mathrm{au}$. The lower limit of $\sim9$–$15\,\mathrm{au}$ likely marks the boundary where the MHD disk wind interacts with the X-wind, as traced by the emission of the SO ((cite: Lee2021)), while 40 au is the disk radius ((cite: Lee2017ApJ)). The discrepancy in the lower limit of 4 au for the wind launching point reported by (cite: Lee2021) arises because our velocities and radii measurements were made at the emission limit (2$\sigma$), whereas (cite: Lee2021) determined the physical properties at the peak of the SO emission. We choose to measure the physical quantities at 2$\sigma$ to avoid contamination from the CO shocked wind inside the SiO shell (Figures [1](#fig:molecules_resolution), [2](#fig:moment0), and [6](#fig:pv_jetaxis)) and SO shell (see Figure [6](#fig:pv_jetaxis)). The multiple shell structure observed in the molecular outflow of HH 212 could be produced by a pulsing jet or wind propagating into a uniform ambient medium (see (cite: Lee2001)).

The outflow associated with HH 212 exhibits characteristics of both jet and wide-angle wind features. Therefore, we suggest that both effects coexist and play decisive roles in the formation and evolution of molecular outflows. At this juncture, the unified jet-wind models such as in (cite: Shang2006) are a direction promising to explain the dual characteristics.

### The Unified Model

In recent numerical simulations, (cite: Shang2020; Shang2023a) propose a unified model where molecular outflows arise from the magnetic interaction between the ambient medium and the X-wind launched from the disk. In this model, the outflow is formed by a magnetized primary wide-angle X-wind that bears a collimated high-density jet along the outflow axis. The interaction between the wide-angle wind and the ambient envelope creates a bubble structure with nested layers of structures, with an extended shocked region of mixing of wind and ambient materials between the forward and reverse shocks, and the free X-wind, exists inside the reverse shock cavity. Due to the magnetic interplay between the X-wind and the envelope, multi cavities looking like multiple large ejections can appear as a result, which resembles the multiple nested components observed in this study.

The structure proposed in the unified model is observed in the protostellar system HH 212. From the outermost to innermost structures relative to jet axis, the cavity wall traced by C$^{34}$S ((cite: Codella2014); (cite: Tabone2017)) represents the shocked ambient medium, corresponding to the material between the forward shock and the contact discontinuity. The CO shell and the SiO shell denote the high-density shocked wind outlining the boundaries of the multicavities. Meanwhile, the wide-angle MHD disk wind and shocked wind of the CO represent the low-density shocked wind. Finally, the CO emission observed between the SiO knots (Figure [1](#fig:molecules_resolution)c) is associated with the large pseudopulses, caused by oscillations in magnetic forces (cite: Shang2020).

It has already been proven that the rotating jet derives from an X-wind model ((cite: Lee2017Nat)). The most straightforward interpretation of the facts of this outflow is more naturally unified with this known fact, in the form of the unified model. The unified model explains the features of the outflow as the result of the magnetic interaction between the wind launched from the protostellar-disk system and the ambient medium. The observed rotation in the rotating region of HH 212 can be attributed within the unified model to the inhomogeneity of outflow lobe in the $\phi$-direction, or to the incorporation of angular momentum of the infalling and collapsing ambient cloud matter entrained through the Kelvin–Helmholtz instability. Future very high-angular resolution observations of molecular outflows with different inclination angles with respect to the line of sight and new analyses that consider rotation in the envelope will be crucial for elucidating the detailed structures produced by the magnetized bubble driven by the unified model, with the hope of discriminating from the free disk wind scenarios.

# Conclusions

We provide a comprehensive analysis of the ALMA observations of the CO line emission in the protostellar system HH 212. We also compare the results with the previous results of the SiO and SO line emission to have a more complete picture of the outflow.

The CO molecular line emission delineates four distinct regions: an outer outflow shell, the shocked rotating wind between the CO and SiO shells, the shocked wind within the SiO shell, and the jet/X-wind.

The CO outer outflow shell is the one previously reported by (cite: Lee2015). This shell is the result of the interaction between the rotating wind with the ambient medium and shows a dominance and influence from the surrounding envelope.

We find that the low velocity components of CO rotating wind can be tracing an expanding shell launched from a disk radius of $\sim 9-15\,\mathrm{au}$. This launching point is larger than that of the previously detected SO shell, suggesting that the CO shell likely marks the boundary where the wide-angle component of the X-wind interacts with the MHD disk wind. This CO wind has a magnetic lever arm parameter of $\lambda \sim 3-4.5$.

Under assumption that the high velocity components of the rotating wind is tracing a MHD disk wind, this emission could be parameterized with launching radii $\sim 1-2\,\mathrm{au}$ with a magnetic lever arm parameter of $\lambda \sim 2-2.5$. However, this emission is likely associated with a shocked wind, as a result of the interaction between the jet or wide-angle X-wind with the surrounding, the envelope, disk atmosphere, or a disk wind. Also, this emission could result from material ejected sideways by the internal bow shocks driven by the CO or SiO knots.

Additionally, the CO jet exhibits discernible knots distributed at roughly equal intervals from the central source, $|100|\,\mathrm{au}<z<|700|\,\mathrm{au}$. Furthermore, the width of the knots increases with the distance away from the central source.

Finally, the shocked CO wind coexists with SO inside the large elongated shell on top of the stream of knots far downstream, converging from the outer shell midway of the SiO. This CO wind could be associated with the wide-angle component of the X-wind shocked in the compressed wind region or entrained from the compressed ambient medium.

We thank an anonymous referee for very useful suggestions that improved the presentation of this paper. We are grateful to Susana Lizano, Jorge Cantó, Manuel Fernández-López for the discussion and helpful comments about the outflow models. We are grateful with Benoit Tabone for his contribution in the ALMA proposal #2016.1.01475.S. J.A.L.V. and C.F.L. acknowledge grants from the National Science and Technology Council of Taiwan (NSTC 112–2112–M–001–039–MY3) and the Academia Sinica (Investigator Award AS–IA–108–M01). H.S. acknowledges support from the National Science and Technology Council in Taiwan (NSTC 113-2112-M-001-008). LP and CC acknowledge financial support under the National Recovery and Resilience Plan (NRRP), Mission 4, Component 2, Investment 1.1, Call for tender No. 104 published on 2.2.2022 by the Italian Ministry of University and Research (MUR), funded by the European Union–Next Generation EU-Project Title 2022JC2Y93 Chemical Origins: linking the fossil composition of the Solar System with the chemistry of protoplanetary disks – CUP J53D23001600006 – Grant Assignment Decree No. 962 adopted on 30.06.2023 by the Italian Ministry of Ministry of University and Research (MUR). LP and CC also acknowledge the PRIN-MUR 2020 BEYOND-2p (Astrochemistry beyond the second period elements, Prot. 2020AFB3FX), the project ASI-Astrobiologia 2023 MIGLIORA (Modeling Chemical Complexity, F83C23000800005), the INAF-GO 2023 fundings PROTO-SKA (Exploiting ALMA data to study planet forming disks: preparing the advent of SKA, C13C23000770005), and the INAF Mini-Grant 2022 “Chemical Origins” (PI: L. Podio). A. M. acknowledges the grant from the National Science and Technology Council (NSTC) of Taiwan 112-2112-M-001-031- and 113-2112-M-001-009-. This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00024.S, ADS/JAO.ALMA #2015.1.00041.S, and ADS/JAO.ALMA #2016.1.01475.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

natexlab

(ref: Ai2024) Ai, T.-H., Liu, C.-F., Shang, H., Johnstone, D., & Krasnopolsky, R. 2024, arXiv e-prints, arXiv:2402.02529, doi: [`10.48550/arXiv.2402.02529`](http://doi.org/10.48550/arXiv.2402.02529)

(ref: Alexander2014) Alexander, R., Pascucci, I., Andrews, S., Armitage, P., & Cieza, L. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 475–496, doi: [`10.2458/azu_uapress_9780816531240-ch021`](http://doi.org/10.2458/azu_uapress_9780816531240-ch021)

(ref: Anderson2003) Anderson, J. M., Li, Z.-Y., Krasnopolsky, R., & Blandford, R. D. 2003, ApJL, 590, L107, doi: [`10.1086/376824`](http://doi.org/10.1086/376824)

(ref: Andre2000) Andre, P., Ward-Thompson, D., & Barsony, M. 2000, in Protostars and Planets IV, ed. V. Mannings, A. P. Boss, & S. S. Russell, 59, doi: [`10.48550/arXiv.astro-ph/9903284`](http://doi.org/10.48550/arXiv.astro-ph/9903284)

(ref: Arce2011) Arce, H. G., Borkin, M. A., Goodman, A. A., Pineda, J. E., & Beaumont, C. N. 2011, ApJ, 742, 105, doi: [`10.1088/0004-637X/742/2/105`](http://doi.org/10.1088/0004-637X/742/2/105)

(ref: Arce2006) Arce, H. G., & Sargent, A. I. 2006, ApJ, 646, 1070, doi: [`10.1086/505104`](http://doi.org/10.1086/505104)

(ref: Bianchi2017) Bianchi, E., Codella, C., Ceccarelli, C., et al. 2017, A&A, 606, L7, doi: [`10.1051/0004-6361/201731404`](http://doi.org/10.1051/0004-6361/201731404)

(ref: Bjerkeli2016a) Bjerkeli, P., van der Wiel, M. H. D., Harsono, D., Ramsey, J. P., & Jørgensen, J. K. 2016, Nature, 540, 406, doi: [`10.1038/nature20600`](http://doi.org/10.1038/nature20600)

(ref: Blandford1982) Blandford, R. D., & Payne, D. G. 1982, MNRAS, 199, 883, doi: [`10.1093/mnras/199.4.883`](http://doi.org/10.1093/mnras/199.4.883)

(ref: Booth2021) Booth, A. S., Tabone, B., Ilee, J. D., et al. 2021, ApJS, 257, 16, doi: [`10.3847/1538-4365/ac1ad4`](http://doi.org/10.3847/1538-4365/ac1ad4)

(ref: Canto2006) Cantó, J., Raga, A. C., & Adame, L. 2006, MNRAS, 369, 860, doi: [`10.1111/j.1365-2966.2006.10344.x`](http://doi.org/10.1111/j.1365-2966.2006.10344.x)

(ref: CASAteam) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Claussen1998) Claussen, M. J., Marvel, K. B., Wootten, A., & Wilking, B. A. 1998, ApJL, 507, L79, doi: [`10.1086/311669`](http://doi.org/10.1086/311669)

(ref: Codella2023) Codella, C., Gueth, F., & Cabrit, S. 2023, Research Notes of the AAS, 7, 204, doi: [`10.3847/2515-5172/acfd9f`](http://doi.org/10.3847/2515-5172/acfd9f)

(ref: Codella2014) Codella, C., Cabrit, S., Gueth, F., et al. 2014, A&A, 568, L5, doi: [`10.1051/0004-6361/201424103`](http://doi.org/10.1051/0004-6361/201424103)

(ref: Schutzer2022) de A. Schutzer, A., Rivera-Ortiz, P. R., Lefloch, B., et al. 2022, A&A, 662, A104, doi: [`10.1051/0004-6361/202142931`](http://doi.org/10.1051/0004-6361/202142931)

(ref: dValon2020) de Valon, A., Dougados, C., Cabrit, S., et al. 2020, A&A, 634, L12, doi: [`10.1051/0004-6361/201936950`](http://doi.org/10.1051/0004-6361/201936950)

(ref: dValon2022) —. 2022, A&A, 668, A78, doi: [`10.1051/0004-6361/202141316`](http://doi.org/10.1051/0004-6361/202141316)

(ref: Delabrosse2024) Delabrosse, V., Dougados, C., Cabrit, S., et al. 2024, arXiv e-prints, arXiv:2403.19400, doi: [`10.48550/arXiv.2403.19400`](http://doi.org/10.48550/arXiv.2403.19400)

(ref: Dutta2020) Dutta, S., Lee, C.-F., Liu, T., et al. 2020, ApJS, 251, 20, doi: [`10.3847/1538-4365/abba26`](http://doi.org/10.3847/1538-4365/abba26)

(ref: Dutta2024) Dutta, S., Lee, C.-F., Johnstone, D., et al. 2024, AJ, 167, 72, doi: [`10.3847/1538-3881/ad152b`](http://doi.org/10.3847/1538-3881/ad152b)

(ref: FernandezLopez2020) Fernández-López, M., Zapata, L. A., Rodrı́guez, L. F., et al. 2020, AJ, 159, 171, doi: [`10.3847/1538-3881/ab7a10`](http://doi.org/10.3847/1538-3881/ab7a10)

(ref: Ferreira2006) Ferreira, J., Dougados, C., & Cabrit, S. 2006, A&A, 453, 785, doi: [`10.1051/0004-6361:20054231`](http://doi.org/10.1051/0004-6361:20054231)

(ref: Flores2023) Flores, C., Ohashi, N., Tobin, J. J., et al. 2023, ApJ, 958, 98, doi: [`10.3847/1538-4357/acf7c1`](http://doi.org/10.3847/1538-4357/acf7c1)

(ref: Furlan2016) Furlan, E., Fischer, W. J., Ali, B., et al. 2016, ApJS, 224, 5, doi: [`10.3847/0067-0049/224/1/5`](http://doi.org/10.3847/0067-0049/224/1/5)

(ref: Harada2023) Harada, N., Tokuda, K., Yamasaki, H., et al. 2023, ApJ, 945, 63, doi: [`10.3847/1538-4357/acb930`](http://doi.org/10.3847/1538-4357/acb930)

(ref: Hartmann1996) Hartmann, L., & Kenyon, S. J. 1996, ARA&A, 34, 207, doi: [`10.1146/annurev.astro.34.1.207`](http://doi.org/10.1146/annurev.astro.34.1.207)

(ref: Hirota2017) Hirota, T., Machida, M. N., Matsushita, Y., et al. 2017, Nature Astronomy, 1, 0146, doi: [`10.1038/s41550-017-0146`](http://doi.org/10.1038/s41550-017-0146)

(ref: Hsieh2023) Hsieh, C.-H., Arce, H. G., Li, Z.-Y., et al. 2023, ApJ, 947, 25, doi: [`10.3847/1538-4357/acba13`](http://doi.org/10.3847/1538-4357/acba13)

(ref: Launhardt2009) Launhardt, R., Pavlyuchenkov, Y., Gueth, F., et al. 2009, A&A, 494, 147, doi: [`10.1051/0004-6361:200810835`](http://doi.org/10.1051/0004-6361:200810835)

(ref: Launhardt2023) Launhardt, R., Pavlyuchenkov, Y. N., Akimkin, V. V., et al. 2023, A&A, 678, A135, doi: [`10.1051/0004-6361/202347483`](http://doi.org/10.1051/0004-6361/202347483)

(ref: Lee2022mol) Lee, C.-F., Codella, C., Ceccarelli, C., & López-Sepulcre, A. 2022a, ApJ, 937, 10, doi: [`10.3847/1538-4357/ac8c28`](http://doi.org/10.3847/1538-4357/ac8c28)

(ref: Lee2014) Lee, C.-F., Hirano, N., Zhang, Q., et al. 2014, ApJ, 786, 114, doi: [`10.1088/0004-637X/786/2/114`](http://doi.org/10.1088/0004-637X/786/2/114)

(ref: Lee2015) —. 2015, ApJ, 805, 186, doi: [`10.1088/0004-637X/805/2/186`](http://doi.org/10.1088/0004-637X/805/2/186)

(ref: Lee2006) Lee, C.-F., Ho, P. T. P., Beuther, H., et al. 2006, ApJ, 639, 292, doi: [`10.1086/499297`](http://doi.org/10.1086/499297)

(ref: Lee2017Nat) Lee, C.-F., Ho, P. T. P., Li, Z.-Y., et al. 2017a, Nature Astronomy, 1, 0152, doi: [`10.1038/s41550-017-0152`](http://doi.org/10.1038/s41550-017-0152)

(ref: Lee2017ApJ) Lee, C.-F., Li, Z.-Y., Ho, P. T. P., et al. 2017b, ApJ, 843, 27, doi: [`10.3847/1538-4357/aa7757`](http://doi.org/10.3847/1538-4357/aa7757)

(ref: Lee2017Sc) —. 2017c, Science Advances, 3, e1602935, doi: [`10.1126/sciadv.1602935`](http://doi.org/10.1126/sciadv.1602935)

(ref: Lee2022) Lee, C.-F., Li, Z.-Y., Shang, H., & Hirano, N. 2022b, ApJL, 927, L27, doi: [`10.3847/2041-8213/ac59c0`](http://doi.org/10.3847/2041-8213/ac59c0)

(ref: Lee2000) Lee, C.-F., Mundy, L. G., Reipurth, B., Ostriker, E. C., & Stone, J. M. 2000, ApJ, 542, 925, doi: [`10.1086/317056`](http://doi.org/10.1086/317056)

(ref: Lee2001) Lee, C.-F., Stone, J. M., Ostriker, E. C., & Mundy, L. G. 2001, ApJ, 557, 429, doi: [`10.1086/321648`](http://doi.org/10.1086/321648)

(ref: Lee2021) Lee, C.-F., Tabone, B., Cabrit, S., et al. 2021, ApJL, 907, L41, doi: [`10.3847/2041-8213/abda38`](http://doi.org/10.3847/2041-8213/abda38)

(ref: Lee2018) Lee, C.-F., Li, Z.-Y., Codella, C., et al. 2018, ApJ, 856, 14, doi: [`10.3847/1538-4357/aaae6d`](http://doi.org/10.3847/1538-4357/aaae6d)

(ref: Li2013) Li, G.-X., Qiu, K., Wyrowski, F., & Menten, K. 2013, A&A, 559, A23, doi: [`10.1051/0004-6361/201220581`](http://doi.org/10.1051/0004-6361/201220581)

(ref: Li1996) Li, Z.-Y., & Shu, F. H. 1996, ApJ, 468, 261, doi: [`10.1086/177688`](http://doi.org/10.1086/177688)

(ref: Liang2020) Liang, L., Johnstone, D., Cabrit, S., & Kristensen, L. E. 2020, ApJ, 900, 15, doi: [`10.3847/1538-4357/aba830`](http://doi.org/10.3847/1538-4357/aba830)

(ref: JALV2019) López-Vázquez, J. A., Cantó, J., & Lizano, S. 2019, ApJ, 879, 42, doi: [`10.3847/1538-4357/ab2242`](http://doi.org/10.3847/1538-4357/ab2242)

(ref: JALV2024) López-Vázquez, J. A., Lee, C.-F., Fernández-López, M., et al. 2024, ApJ, 962, 28, doi: [`10.3847/1538-4357/ad132a`](http://doi.org/10.3847/1538-4357/ad132a)

(ref: JALV2023) López-Vázquez, J. A., Zapata, L. A., & Lee, C.-F. 2023, ApJ, 944, 63, doi: [`10.3847/1538-4357/acb439`](http://doi.org/10.3847/1538-4357/acb439)

(ref: JALV2020) López-Vázquez, J. A., Zapata, L. A., Lizano, S., & Cantó, J. 2020, ApJ, 904, 158, doi: [`10.3847/1538-4357/abbe24`](http://doi.org/10.3847/1538-4357/abbe24)

(ref: Louvet2018) Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120, doi: [`10.1051/0004-6361/201731733`](http://doi.org/10.1051/0004-6361/201731733)

(ref: Masson1993) Masson, C. R., & Chernin, L. M. 1993, ApJ, 414, 230, doi: [`10.1086/173071`](http://doi.org/10.1086/173071)

(ref: Matzner1999) Matzner, C. D., & McKee, C. F. 1999, ApJL, 526, L109, doi: [`10.1086/312376`](http://doi.org/10.1086/312376)

(ref: Mendoza2009) Mendoza, S., Tejeda, E., & Nagel, E. 2009, MNRAS, 393, 579, doi: [`10.1111/j.1365-2966.2008.14210.x`](http://doi.org/10.1111/j.1365-2966.2008.14210.x)

(ref: Moraghan2016) Moraghan, A., Lee, C.-F., Huang, P.-S., & Vaidya, B. 2016, MNRAS, 460, 1829, doi: [`10.1093/mnras/stw1089`](http://doi.org/10.1093/mnras/stw1089)

(ref: Nisini2024) Nisini, B., Navarro, M. G., Giannini, T., et al. 2024, ApJ, 967, 168, doi: [`10.3847/1538-4357/ad3d5a`](http://doi.org/10.3847/1538-4357/ad3d5a)

(ref: Ostriker1997) Ostriker, E. C. 1997, ApJ, 486, 291, doi: [`10.1086/304513`](http://doi.org/10.1086/304513)

(ref: Ostriker2001) Ostriker, E. C., Lee, C.-F., Stone, J. M., & Mundy, L. G. 2001, ApJ, 557, 443, doi: [`10.1086/321649`](http://doi.org/10.1086/321649)

(ref: Pascucci2022) Pascucci, I., Cabrit, S., Edwards, S., et al. 2022, arXiv e-prints, arXiv:2203.10068, doi: [`10.48550/arXiv.2203.10068`](http://doi.org/10.48550/arXiv.2203.10068)

(ref: Pety2006) Pety, J., Gueth, F., Guilloteau, S., & Dutrey, A. 2006, A&A, 458, 841, doi: [`10.1051/0004-6361:20065814`](http://doi.org/10.1051/0004-6361:20065814)

(ref: Podio2015) Podio, L., Codella, C., Gueth, F., et al. 2015, A&A, 581, A85, doi: [`10.1051/0004-6361/201525778`](http://doi.org/10.1051/0004-6361/201525778)

(ref: Podio2021) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45, doi: [`10.1051/0004-6361/202038429`](http://doi.org/10.1051/0004-6361/202038429)

(ref: Pudritz1983) Pudritz, R. E., & Norman, C. A. 1983, ApJ, 274, 677, doi: [`10.1086/161481`](http://doi.org/10.1086/161481)

(ref: Pudritz1986) —. 1986, ApJ, 301, 571, doi: [`10.1086/163924`](http://doi.org/10.1086/163924)

(ref: Pudritz2007) Pudritz, R. E., Ouyed, R., Fendt, C., & Brandenburg, A. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 277

(ref: Rabenanahary2022) Rabenanahary, M., Cabrit, S., Meliani, Z., & Pineau des Forêts, G. 2022, A&A, 664, A118, doi: [`10.1051/0004-6361/202243139`](http://doi.org/10.1051/0004-6361/202243139)

(ref: Raga1993) Raga, A., & Cabrit, S. 1993, A&A, 278, 267

(ref: Ray2007) Ray, T., Dougados, C., Bacciotti, F., Eislöffel, J., & Chrysostomou, A. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 231, doi: [`10.48550/arXiv.astro-ph/0605597`](http://doi.org/10.48550/arXiv.astro-ph/0605597)

(ref: Remijan2007) Remijan, A. J., Markwick-Kemper, A., & ALMA Working Group on Spectral Line Frequencies. 2007, in American Astronomical Society Meeting Abstracts, Vol. 211, American Astronomical Society Meeting Abstracts, 132.11

(ref: RiveraOrtiz2023) Rivera-Ortiz, P. R., de A. Schutzer, A., Lefloch, B., & Gusdorf, A. 2023, A&A, 672, A116, doi: [`10.1051/0004-6361/202245085`](http://doi.org/10.1051/0004-6361/202245085)

(ref: Shang2006) Shang, H., Allen, A., Li, Z.-Y., et al. 2006, ApJ, 649, 845, doi: [`10.1086/506513`](http://doi.org/10.1086/506513)

(ref: Shang2002) Shang, H., Glassgold, A. E., Shu, F. H., & Lizano, S. 2002, ApJ, 564, 853, doi: [`10.1086/324197`](http://doi.org/10.1086/324197)

(ref: Shang2023b) Shang, H., Krasnopolsky, R., & Liu, C.-F. 2023a, ApJL, 945, L1, doi: [`10.3847/2041-8213/acaeae`](http://doi.org/10.3847/2041-8213/acaeae)

(ref: Shang2020) Shang, H., Krasnopolsky, R., Liu, C.-F., & Wang, L.-Y. 2020, ApJ, 905, 116, doi: [`10.3847/1538-4357/abbdb0`](http://doi.org/10.3847/1538-4357/abbdb0)

(ref: Shang2023a) Shang, H., Liu, C.-F., Krasnopolsky, R., & Wang, L.-Y. 2023b, ApJ, 944, 230, doi: [`10.3847/1538-4357/aca763`](http://doi.org/10.3847/1538-4357/aca763)

(ref: Shang1998) Shang, H., Shu, F. H., & Glassgold, A. E. 1998, ApJL, 493, L91, doi: [`10.1086/311135`](http://doi.org/10.1086/311135)

(ref: Shu1994) Shu, F., Najita, J., Ostriker, E., et al. 1994, ApJ, 429, 781, doi: [`10.1086/174363`](http://doi.org/10.1086/174363)

(ref: Shu1991) Shu, F. H., Ruden, S. P., Lada, C. J., & Lizano, S. 1991, ApJL, 370, L31, doi: [`10.1086/185970`](http://doi.org/10.1086/185970)

(ref: Smith1997) Smith, M. D., Suttner, G., & Zinnecker, H. 1997, A&A, 320, 325

(ref: Snell1980) Snell, R. L., Loren, R. B., & Plambeck, R. L. 1980, ApJL, 239, L17, doi: [`10.1086/183283`](http://doi.org/10.1086/183283)

(ref: Suttner1997) Suttner, G., Smith, M. D., Yorke, H. W., & Zinnecker, H. 1997, A&A, 318, 595

(ref: Tabone2018) Tabone, B., Raga, A., Cabrit, S., & Pineau des Forêts, G. 2018, A&A, 614, A119, doi: [`10.1051/0004-6361/201732031`](http://doi.org/10.1051/0004-6361/201732031)

(ref: Tabone2017) Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6, doi: [`10.1051/0004-6361/201731691`](http://doi.org/10.1051/0004-6361/201731691)

(ref: Tabone2020) Tabone, B., Cabrit, S., Pineau des Forêts, G., et al. 2020, A&A, 640, A82, doi: [`10.1051/0004-6361/201834377`](http://doi.org/10.1051/0004-6361/201834377)

(ref: Tobin2019) Tobin, J. J., Bourke, T. L., Mader, S., et al. 2019, ApJ, 870, 81, doi: [`10.3847/1538-4357/aaef87`](http://doi.org/10.3847/1538-4357/aaef87)

(ref: Ulrich1976) Ulrich, R. K. 1976, ApJ, 210, 377, doi: [`10.1086/154840`](http://doi.org/10.1086/154840)

(ref: vanthoff2018) van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018, ApJL, 864, L23, doi: [`10.3847/2041-8213/aadb8a`](http://doi.org/10.3847/2041-8213/aadb8a)

(ref: Vazzano2021) Vazzano, M. M., Fernández-López, M., Plunkett, A., et al. 2021, A&A, 648, A41, doi: [`10.1051/0004-6361/202039228`](http://doi.org/10.1051/0004-6361/202039228)

(ref: Wang2019) Wang, L.-Y., Shang, H., & Chiang, T.-Y. 2019, ApJ, 874, 31, doi: [`10.3847/1538-4357/ab07b5`](http://doi.org/10.3847/1538-4357/ab07b5)

(ref: Yang2021) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20, doi: [`10.3847/1538-4357/abdfd6`](http://doi.org/10.3847/1538-4357/abdfd6)

(ref: Zapata2014) Zapata, L. A., Arce, H. G., Brassfield, E., et al. 2014, MNRAS, 441, 3696, doi: [`10.1093/mnras/stu810`](http://doi.org/10.1093/mnras/stu810)

(ref: Zapata2015) Zapata, L. A., Lizano, S., Rodrı́guez, L. F., et al. 2015, ApJ, 798, 131, doi: [`10.1088/0004-637X/798/2/131`](http://doi.org/10.1088/0004-637X/798/2/131)

(ref: Zapata2010) Zapata, L. A., Schmid-Burgk, J., Muders, D., et al. 2010, A&A, 510, A2, doi: [`10.1051/0004-6361/200810245`](http://doi.org/10.1051/0004-6361/200810245)

(ref: Zhang2018) Zhang, Y., Higuchi, A. E., Sakai, N., et al. 2018, ApJ, 864, 76, doi: [`10.3847/1538-4357/aad7ba`](http://doi.org/10.3847/1538-4357/aad7ba)

(ref: Zhang2019) Zhang, Y., Arce, H. G., Mardones, D., et al. 2019, ApJ, 883, 1, doi: [`10.3847/1538-4357/ab3850`](http://doi.org/10.3847/1538-4357/ab3850)

(ref: Zinneckar1998) Zinnecker, H., McCaughrean, M. J., & Rayner, J. T. 1998, Nature, 394, 862, doi: [`10.1038/29716`](http://doi.org/10.1038/29716)

(ref: Zucker2019) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2019, ApJ, 879, 125, doi: [`10.3847/1538-4357/ab2388`](http://doi.org/10.3847/1538-4357/ab2388)

[^1]: Corresponding author: J. A. López-Vázquez

</paper>

Write the methods card for this paper.