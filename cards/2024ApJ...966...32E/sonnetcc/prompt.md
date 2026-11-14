# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...966...32E\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...966...32E",
 "title": "Early Planet Formation in Embedded Disks (eDisk). XIII. Aligned Disks with Nonsettled Dust around the Newly Resolved Class 0 Protobinary R CrA IRAS 32",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Encalada, Frankie J.",
 "n_authors": 22,
 "arxiv_id": "2403.14143",
 "doi": "10.3847/1538-4357/ad3442",
 "alma_projects_linked_by_archive": [
  "2019.1.00261.L"
 ]
}
```

Paper text:
<paper>
# Early Planet Formation in Embedded Disks (eDisk) XIII: Aligned Disks with Non-Settled Dust Around the Newly Resolved Class 0 Protobinary R CrA IRAS 32

## Abstract

Young protostellar binary systems, with expected ages less than $\sim$10$^5$ years, are little modified since birth, providing key clues to binary formation and evolution. We present a first look at the young, Class 0 binary protostellar system R CrA IRAS 32 from the Early Planet Formation in Embedded Disks (eDisk) ALMA large program, which observed the system in the 1.3 mm continuum emission, $^{12}$CO (2-1), $^{13}$CO (2-1), C$^{18}$O (2-1), SO (6$_5$-5$_4$), and nine other molecular lines that trace disk, envelope, shocks, and outflows. With a continuum resolution of $\sim$0.03$^{\prime\prime}$ ($\sim$5 au, at a distance of 150 pc), we characterize the newly discovered binary system with a separation of 207 au, their circumstellar disks, and a circumbinary disk-like structure. The circumstellar disk radii are 26.9$\pm$0.3 and 22.8$\pm$0.3 au for sources A and B, respectively, and their circumstellar disk dust masses are estimated as 22.5$\pm$1.1 and 12.4$\pm$0.6 M$_{\Earth}$. The circumstellar disks and the circumbinary structure have well aligned position angles and inclinations, indicating formation in a smooth, ordered process such as disk fragmentation. In addition, the circumstellar disks have a near/far-side asymmetry in the continuum emission suggesting that the dust has yet to settle into a thin layer near the midplane. Spectral analysis of CO isotopologues reveals outflows that originate from both of the sources and possibly from the circumbinary disk-like structure. Furthermore, we detect Keplerian rotation in the $^{13}$CO isotopologues toward both circumstellar disks and likely Keplerian rotation in the circumbinary structure; the latter suggests that it is probably a circumbinary disk.

# Introduction

The circumstellar disks around young stellar objects are the mass reservoirs from which planets are eventually formed. The structures and properties of the disk, especially in the early stages of protostellar evolution, are critical for understanding star and planet formation. The youngest disks, around the so-called Class 0 sources (cite: andre1993), are accreting mass and angular momentum from the surrounding envelope while also losing angular momentum via low-velocity outflows and high-velocity jets (cite: snell1980; frank2014). Class 0 disks are critical for star and planet evolution as they are the conduit for envelope accretion onto the protostar, and they are the site for dust evolution and the beginning of planetesimals (cite: Testi2014).

Current observations reveal that gaps and rings are ubiquitous in Class II protostellar disks (cite: brogan2015; andrews2018). The substructures in the disks are likely caused by planetary-mass bodies in the gaps, shepherding the dust into sharply defined rings or spiral structures (cite: dong2015; zhang2018; huang2018). The idea that protoplanets are playing a role in the substructure formation has also been supported by localized gas deviations from Keplerian rotation that are consistent with protoplanets in the gaps (cite: Pinte2020).

Although protoplanets creating these substructures appear to be the most likely creation mechanism, other possible explanations for the gaps and rings have been suggested, such as 1) non-ideal magnetohydrodynamics effects, e.g., ambipolar diffusion on $\sim$10 au scales with a magnetically coupled disk-wind (cite: suriano2018), 2) gas density variations at the outer edge of the dead-zone in a magnetorotational instability driven accretion disk (cite: ruge2015), 3) radial variations in dust properties due to volatiles freezing onto dust grains (i.e., snowlines) (cite: zhang2015), or 4) heterogenous infall onto the disk (cite: kuznetsova2022), among others. In any formation process, the gaps and rings (and other substructures such as spirals) will still have local pressure deviations that trap dust grains, which then promote planetesimal formation (cite: vanderMarel2013; perez2016), so the evolution of substructures is still likely a fundamental step in understanding planet formation regardless of their origins.

It is now clear that a large fraction of T Tauri stars have clear and well-developed substructures (cite: Bae2022). Many theoretical studies have suggested that if such structures are produced by already-formed planets, planet formation should have started at an earlier time when there was a large reservoir of material (cite: tsukamoto2017). However, observing Class 0/I objects is more difficult due to the disks still being deeply embedded in an envelope. Nonetheless, recent observations have suggested that substructures can form early in the disk formation process in some cases. (cite: sheehan2020) showed substructure in seven sources of the VLA/ALMA Nascent Disk and Multiplicity Survey of Orion Protostars (cite: tobin2020). Three of the sources were modeled to have a very large envelope-to-disk masses, suggesting very young disks. In addition, the Class I source Oph IRS63 was shown to have multiple narrow (and shallow) annular substructures (cite: dom2020).

To probe the youngest protostellar disk for substructures, measure young disk properties, observe the outflows, probe the disk kinematics, and constrain the protostellar mass, the Atacama Large Millimeter/submillimeter Array (ALMA) Large Program, Early Planet Formation in Embedded Disks (cite: edisk), focuses on the embedded disks in Class 0/I systems. In this program, 17 YSOs in nearby star forming regions were observed, and 2 YSOs were used from the archive, at 1.3 mm (230 GHz) to quantify the kinematics and structures of the embedded disks. The main means of this analysis is through the continuum and CO isotopologues, with a dozen other complementary molecular lines that probe other aspects of the protostellar system.

+:------------:+:----------:+:-------------:+:--------------:+:----------:+:---------:+:----------:+:----------:+:----------:+
| Observation  | Time On    | Array         | Number of      | Baselines  | PWV$^{c}$ | Calibrators                          |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| Date         | Source     | Config.$^{a}$ | Antennas$^{b}$ |            |           | Bandpass   | Phase      | Flux       |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| (yyyy-mm-dd) | (mm:ss.ss) |               |                | \(m\)      | \(mm\)    |            |            |            |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| 2021-05-04   | 13:05      | C4/5          | 42             | 15 - 2500  | 1.72      | J1924-2914 | J1937-3958 | J1839-3453 |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| 2021-05-15   | 13:05      | C6            | 45             | 15 - 2500  | 1.01      | J1924-2914 | J1937-3958 | J1839-3453 |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| 2021-08-18   | 21:31      | C8            | 40             | 92 - 8300  | 0.33      | J1924-2914 | J1839-3453 | J1823-3454 |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| 2021-08-22   | 21:31      | C8            | 49             | 47 - 11600 | 0.30      | J1924-2914 | J1839-3453 | J1823-3454 |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| 2021-10-01   | 21:31      | C8            | 47             | 70 - 11600 | 1.55      | J1924-2914 | J1839-3453 | J1823-3454 |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+
| 2021-10-02   | 21:31      | C8            | 43             | 70 - 11600 | 0.73      | J1924-2914 | J1839-3453 | J1826-3650 |
+--------------+------------+---------------+----------------+------------+-----------+------------+------------+------------+

The youngest multiple systems, of which eDisk was found to contain 4, are important to examine in order to reveal their possible formation mechanisms.(cite: edisk). Although main sequence stars have a multiplicity rate that depends on stellar mass (cite: raghavan2010; sana2011; duchene2013; ward-duong2015; moe2017),

it has been shown that the multiplicity fraction appears to be the largest among the youngest protostars with observed peaks at separations of $\sim$100 au and $\sim$1000 au (cite: tobin2016; encalada2021; tobin2022). These separations provide evidence of both (1) disk fragmentation by gravitational instability and turbulent fragmentation with migration for systems $<$500 au and of (2) turbulent fragmentation for systems $>$1000 au (cite: adams1989; lee2019; padoan2002). The youngest protostars are not only setting the stage for the growth of planetesimals in the young disk, but also for multiplicity.

In this paper, we will present the eDisk observations of the young protobinary system R CrA IRAS 32 (IRAS 18595-3712), hereafter IRAS 32. These are the first observations to resolve the binary. The Corona Australis dark cloud complex is a nearby star-forming region in the southern skies. It is situated toward the galactic center but well away from the galactic plane ($l$=359.84$^\circ$, $b$=-18.12$^\circ$). IRAS 32 was classified as a Class I protostellar system (cite: wilkings1992) toward the Rossano Cloud B in Corona Australis (cite: rossano1978; nutter2005; bresnahan2018). However, a more careful fit to the photometry of the source gives a bolometric temperature of 64 K, which suggests that IRAS 32 is better described as a Class 0 source (cite: edisk). IRAS 32 has been included in both Herschel and Spitzer surveys of the Corona Australis cloud (cite: bresnahan2018; peterson2011) with a known large NE-SW outflow cavity (cite: seale2008). The distance is taken to be 150 pc as a convenient value that is in agreement with recent Gaia parallax estimations (cite: bracco2020; galli2020; zucker2020; dzib2018).

The paper is organized as follows: in section 2 we present the observations and data reduction, section 3 covers the results of the data reduction, section 4 discusses the results, and section 5 contains our conclusions.

# Observations and Data Reduction

IRAS 32 was observed as part of eDisk, ALMA Large Cycle 7 Program, project 2019.1.00261.L (PI N. Ohashi) in Band 6 (230 GHz, 1.3 mm). Here we briefly summarize the observations; see (cite: edisk) for more details. As described in Table [\[tab:obs_data\]](#tab:obs_data), data from single pointings with only the 12 m array were collected between 2021 May 4th and 2021 October 2nd in six execution blocks, which included the eDisk source IRS5N. The blocks individually lasted either 52 or 81 minutes, corresponding to the two short baseline and four long baseline observations. The two short baseline blocks were in the C4/5 and C6 configuration, with the antenna separations ranging between 15 m and 2500 m; the shortest baselines set the maximum recoverable scale for the data to 4.1$^{\prime\prime}$. The four long baseline blocks (all C8) had the antenna array elements at distances between 47 m and 11600 m.

The products were 1.3 mm continuum along with a slew of molecular lines ($^{12}$CO, $^{13}$CO, C$^{18}$O, SO, H$_{2}$CO, c-C$_{3}$H$_{2}$, CH$_{3}$OH, DCN, and SiO), see Table [\[tab:spec_data\]](#tab:spec_data) for more details. Due to the large time difference between the scheduling blocks and dynamic scheduling, different sources were used as calibrators, see Table [\[tab:obs_data\]](#tab:obs_data) and (cite: edisk) for specifics.

As per the ALMA handbook, the absolute flux calibration accuracy is assumed to be $\sim$10%. For the remainder of this paper any uncertainties are only statistical in nature.

All six of the ALMA calibrated data sets were combined to create the final product. They were imaged within CASA, Common Astronomy Software Applications (cite: casa2022), version 6.2.1.7. All execution blocks had their flux rescaled to be in line with the execution block from 2021 August 18th.

We performed continuum self-calibration on the short baseline observations alone, then separately on the combined short and long baseline observations with different thresholds and solution intervals, and then compared the corrected data to verify that the results were similar for the short baselines. For the final combined solutions, initial maps were created to assess the clean thresholds per solution interval. We did four iterations of phase-only self-calibration at solution intervals of `inf-EB`, `inf`, 18.14 sec, and `int`. A solution interval of `inf-EB` encompasses the whole execution block of the observation (when combined with `combine=’scan,spw’` during the `gaincal` step of applying the derived gains to the visibilities), which corrects time invariant phase errors in the data. The solution interval `inf` encompasses each scan (when combined with `combine=’spw’`), which begins to correct time variant phase errors. The solution interval of `int` uses every integration, which corrects time variant phase errors down to the integration time. The time intervals are iteratively applied to the data, building the final solutions. Subsequently, amplitude and phase self-calibration on the continuum was done with an interval of `inf`, since we had high S/N and the dynamic range was still limited after phase-only self-calibration by amplitude errors, further iterations showed no improvements.

We used Briggs weighting with a robust parameter of -0.5 for all the final images since it slightly favors uniform weighting over natural weighting. The deconvolver was `mtmfs`, or Multi-Term Multi-Frequency Synthesis (cite: rau2011). All maps were primary beam corrected.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Transition | Start Freq.$^a$ | End Freq.$^a$ | $\nu_{rest}$ | $\Delta\nu$ | $\Delta$v |
|  |  | (GHz) | (GHz) | (GHz) | (kHz) | (km s$^{-1}$) |
| SiO | 5-4 | 217.032808 | 217.177398 | 217.104980 | 970.407 | 1.35 |
| DCN | 3-2 | 217.224484 | 217.245846 | 217.238600 | 971.004 | 1.35 |
| $c$-C$_3$H$_2$$^b$ | 6$_{0,6}$-5$_{1,5}$ | 217.808970 | 217.830389 | 217.822036 | 973.612 | 1.34 |
| $c$-C$_3$H$_2$$^b$ | 6$_{1,6}$-5$_{0,5}$ | 217.808970 | 217.830389 | 217.822150 | 973.612 | 1.34 |
| $c$-C$_3$H$_2$ | 5$_{1,4}$-4$_{2,3}$ | 217.926863 | 217.948294 | 217.940050 | 974.139 | 1.34 |
| $c$-C$_3$H$_2$ | 5$_{2,4}$-4$_{1,3}$ | 218.147239 | 218.168692 | 218.160440 | 975.125 | 1.34 |
| H$_{2}$CO | 3$_{0,3}$-2$_{0,2}$ | 218.208012 | 218.229471 | 218.222192 | 975.401 | 1.34 |
| CH$_3$OH | 4$_2$-3$_1E$ | 218.425869 | 218.447349 | 218.440063 | 976.374 | 1.34 |
| H$_{2}$CO | 3$_{2,2}$-2$_{2,1}$ | 218.461436 | 218.482920 | 218.475632 | 976.533 | 1.34 |
| H$_{2}$CO | 3$_{2,1}$-2$_{2,0}$ | 218.749578 | 218.764079 | 218.760066 | 121.861 | 0.17 |
| C$^{18}$O | 2-1 | 219.549828 | 219.564382 | 219.560354 | 122.307 | 0.17 |
| SO | 6$_{5}$-5$_{4}$ | 219.938897 | 219.953477 | 219.949433 | 122.523 | 0.17 |
| $^{13}$CO | 2-1 | 220.388118 | 220.402728 | 220.398684 | 122.774 | 0.17 |
| $^{12}$CO | 2-1 | 230.461570 | 230.614899 | 230.538000 | 488.310 | 0.63 |

The spectral windows were continuum subtracted, imaged, and used to produce data cubes. The imaging process followed mostly the same steps as with the continuum. However, the masking was done automatically using `auto-multithresh` (cite: kepley2020) with the default parameters over the ranges of spectral windows containing specific molecular lines instead of over the full window. We also used `briggsbwtaper` weighting, which is the standard Briggs weighting but with an inverse uv taper added per channel, with a robust parameter of 0.5 for all the final molecular line images.

Specific spectral line observational details are in Table [\[tab:spec_data\]](#tab:spec_data). All the eDisk data products will soon be available within the ALMA science archive, see (cite: edisk) for more details.

# Results

## Continuum data

Fig. [1](#fig:900) shows the 1.3 mm (225 GHz) continuum map of IRAS 32. The source is resolved into a binary for the first time, with the A component in the southeast and the B component in the northwest. The binary has a projected separation of 1.38$^{\prime\prime}$ (207 au) and a separation angle of 135.9$^{\circ}$ (East of North), with the A component containing nearly twice as much flux density as the B component. In addition, when using only the short baseline data of the project, we can make a low resolution map (Fig. [1](#fig:900), right) that shows a clear flattened circumbinary dust structure surrounding the two disks. We can derive disk properties directly from the images and from simple Gaussian fits to the two disks and the circumbinary structure.

The peak intensities for the A and B sources are taken from the emission map (Fig. [1](#fig:900), left) as 4.92 mJy beam$^{-1}$ (148 K) and 3.21 mJy beam$^{-1}$ (96 K), respectively, where the RMS noise is 0.02 mJy beam$^{-1}$. We do a two Gaussian fit to Fig. [1](#fig:900), left, for each disk simultaneously to measure the flux density (F$_{\nu}$) and the deconvolved minor/major axes ($a$ and $b$, respectively) and PA of the disks, as listed in Table [\[tab:cont_data\]](#tab:cont_data). The Gaussian fit peak intensity is also given but not used anywhere in the analysis since the fit peak is less robust than the total flux. We do another simultaneous three Gaussian fit to the low resolution map (Fig. [1](#fig:900), right, two for each disk and one for the circumbinary structure) to measure the circumbinary dust parameters, which is also listed in Table [\[tab:cont_data\]](#tab:cont_data). Note that the two disk PAs are aligned within a margin of a few degrees, as well as the PA of the overall circumbinary disk structure (see Table [\[tab:cont_data\]](#tab:cont_data)).

![](900_img_continuums_with_zoom.pdf)

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | RA | Dec | F$_{\nu}$ | Peak I$_{\nu}$ | a | b | PA |  |
|  | (ICRS) | (ICRS) | (mJy) | (mJy bm$^{-1}$) | (mas) | (mas) | ($^{\circ}$) |  |
| IRAS 32 A | 19:02:58.7 | -37:07:37.38 | 79.7$\pm$0.9 | 4.92$\pm$0.02 | 212$\pm$2 | 78$\pm$1 | 135.3$\pm$0.4 |  |
| IRAS 32 B | 19:02:58.6 | -37:07:36.39 | 43.8$\pm$0.4 | 3.21$\pm$0.02 | 180$\pm$2 | 57.9$\pm$0.7 | 131.5$\pm$0.3 |  |
| Circumbinary$^{a}$ | 19:02:58.7 | -37:07:36.88 | 46 | 0.5 | 3831 | 1903 | 140.7 |  |

The beam is 35 $\times$ 23 mas with a PA of 66.6$\ensuremath{^\circ}$. The RMS is 0.026 mJy beam$^{-1}$. $^{a}$ The short baseline only continuum map was also used to simultaneously fit the circumbinary structure with the two compact sources. The main objective of this fit was to quantify the circumbinary structure PA. The other circumbinary structure quantities are also given but the errors should be assumed to be of order $\sim$10%. We give the binary midpoint as the RA and DEC, as this location is used as the center of some maps.

In Table [1](#tab:cont_derived_data), we include the derived quantities of the continuum data presented in Table [\[tab:cont_data\]](#tab:cont_data). The inclination, $i$, is estimated by using $\arccos{\frac{b}{a}}$, where a and b are the major and minor axes of the fitted Gaussian. The radius ($R_{\rm disk}$) is taken as the 2$\sigma$ value (FWHM/$\sqrt{2{\rm ln2}}$) of the Gaussian-fit deconvolved major axis. The dust mass estimate assumes isothermal and optically thin emission and is derived from

$$\begin{equation}
M_{dust} = \frac{d^{2} F_{\nu}}{B_{\nu}(T_{dust}) \kappa_{\nu}}
\label{eq:mdust}
\end{equation}$$

where $d$ is the distance to the source (150 pc), $F_{\rm \nu}$ is the observed flux density, and $B_{\rm \nu}$ is the Planck function. We adopt a dust mass opacity, $\kappa_{\nu}$ = 2.3 cm$^{2}$ g$^{-1}$ at $\nu=225$ GHz (cite: beckwith1990).

We use two temperatures for the mass estimate. First, we adopt a temperature of 20 K. In that case, we calculate the dust masses of the two disks as M$_{\rm dust,A,20K}$ = 53.0$\pm$2.6 M$_{\Earth}$ and M$_{\rm  dust,B,20K}$ = 29.1$\pm$1.4 M$_{\Earth}$. In the second case, we estimate the temperature, $T_{\rm  dust}$, given the bolometric luminosity prescription from (cite: tobin2020)

$$\begin{equation}
T_{dust} = T_{0} \left( \frac{L_{bol}}{1 ~L_{\odot}} \right) ^{0.25},
\label{eq:tdust}
\end{equation}$$

with $T_{0}$ = 43 K. IRAS 32 has L$_{bol}$ = 1.6 L$_{\odot}$ via a spectral energy distribution (SED) fit compiled from the NASA/IPAC Infrared Science Archive (IRSA) database (cite: edisk). It is not possible to accurately estimate the individual protostellar contributions to the total luminosity, but due to their similarities, we assign 50% of the luminosity to each of them, which

gives T$_{dust}$=40.7 K. Putting it all together, our derived dust masses are M$_{dust,A}$ = 22.5$\pm$1.1 M$_{\Earth}$ and M$_{dust,B}$ = 12.4$\pm$0.6 M$_{\Earth}$. As the luminosity prescription gives nearly twice the temperature, it estimates a lower disk mass. It should also be mentioned that the IRAS 32 disks are somewhat smaller in radii than those used to derive the 43 K normalization in (cite: tobin2020) (50 au), so we would expect our disks to actually be even warmer on average to this estimate. In addition, since the disks are likely not optically thin, the estimates here are disk mass lower limits.

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Source | i | M$_{dust,40.7K}$$^{a}$ | M$_{dust,20K}$$^{b}$ | R$_{disk}$ |  |
|  | ($^{\circ}$) | (M$_{\Earth}$) | (M$_{\Earth}$) | (au) |  |
| A | 69 | 23$\pm$1 | 53$\pm$3 | 26.9$\pm$0.3 |  |
| B | 71 | 12.4$\pm$0.6 | 29$\pm$1 | 22.8$\pm$0.3 |  |

: Derived Continuum Information

### Radial profile

While Gaussian-fitting is used to derive basic parameters and quantify the structure of our continuum data, we must ask how accurate this assumption is. In Fig. [2](#fig:905c), we show intensity profiles of the 1.3-mm continuum emission (from Fig. [1](#fig:900) left) from along the major and minor axis of both sources, centered on the Gaussian-fit peaks. The separation between the sources gives a high degree of confidence that there is no overlapping contamination from the other source. The first feature we notice is the non-Gaussian nature of the major axis for both sources on both sides of the center. On the other hand, the same can only be said for both sources in the western side of the minor axis. The second noticeable feature is the shift in peak position from the Gaussian-fit center location. This offset can also be visually confirmed in Fig. [1](#fig:900), left. We will discuss this further in Section [4.1](#cont-asym).

![image](905c_img_lineproj_srcA.pdf) ![image](905c_img_lineproj_srcB.pdf)

## Molecular line data

For a full overview of the spectral data, refer again to Table [\[tab:spec_data\]](#tab:spec_data). Our primary molecular lines, which are used as a proxy for H$_2$, are the CO isotopologues in ALMA Band 6.

The $^{12}$CO, $^{13}$CO, and C$^{18}$O isotope observations capture gas kinematics and are used to quantify the source as well as trace the outflow. As we observe the more rare isotopologues (i.e., from $^{12}$CO to $^{13}$CO to C$^{18}$O), the overall abundances and thus column densities drop. In many cases, this allows us to probe a larger fraction of the total column density of the structures if the lower column densities become optically thin in the rarer isotope. In effect, this means we may be able to see further down into the YSOs, through the envelope and into the disk.

Given that one of the goals of eDisk is to characterize the properties of disks in young systems, the molecular line data were carefully chosen. C$^{18}$O is our main workhorse, as it traces the protostellar envelope and disk. $^{13}$CO also serves the same purpose as C$^{18}$O. $^{12}$CO traces outflows, and for our purposes is compared against disk tracers to avoid outflow contamination to kinematic measurements of the disk and envelope. Although SO is typically detected in the shocked gas from bi-polar outflows, it is sometimes seen at the disk/envelope interface (cite: yen2014; sakai2014; ohashi2014).

Visual inspection of our spectral cube data shows that we have significant emission in $^{12}$CO, $^{13}$CO, C$^{18}$O, and SO to warrant moment map analysis and position-velocity (PV) diagram analysis. All $c$-C$_3$H$_2$, H$_2$CO, and DCN lines show faint $\gtrsim$3$\sigma$ emission, but the S/N is insufficient to trace the kinematics of the detected structures. Their channel and moment 0 maps are shown in the Appendix. And finally, SiO and CH$_3$OH only have upper-limits of 3$\sigma$.

Integrated intensity (moment 0) and intensity-weighted average velocity (moment 1) maps were created using the `bettermoments` Python package (cite: bettermoments). Briefly, it integrates along the spectral dimension for each pixel and returns both a moment map and an error map. It is capable of determining the RMS from the empty channels in the cube and of determining the central velocity emission by fitting a quadratic around the brightest pixel and its 2 closest neighbors. Threshold cuts were implemented to only include signal above 3$\sigma$.

In the following sub-sections, we discuss the general broad features of the main molecular line tracers ($^{12}$CO, $^{13}$CO, C$^{18}$O, and SO) with further analysis in §[4.2](#gaskinematics).

### $^{12}$CO emission

The CO emission toward IRAS 32 mainly traces the outflow and some circumstellar material. Fig. [3](#fig:906c) shows the channel maps, and Fig. [4](#fig:901) shows the moment 1 maps for the combined observations. The systemic velocity adopted was 5.86 km s$^{-1}$, and the velocities are all given with respect to this center velocity. The adopted systemic velocity was based on a visual inspection of the cube and will be used for all molecules hereafter, although the value will be revisited when analysing the PV diagrams in §[4.2](#gaskinematics). The two circles mark the binary sources from Fig. [1](#fig:900) whereas the continuum emission is indicated by lime contours in Fig. [4](#fig:901)B and [4](#fig:901)D. The channel maps show structure that is consistent with two outflows (one from each source), seen especially in the blue emission toward the North. To the North there is also a possible outflow interaction region just to the northeast corner of the box in Fig. [4](#fig:901)A that demonstrates a wide range of velocities (blue and red). To the South, there is a clear structure that appears connected to the source B binary outflow component that is toward the blue side compared to the systemic velocity but then crosses over to the red. Similarly, the A binary source has a redshifted component of its outflow that extends far into the red channels. This may indicate that the two sources have slightly offset outflow ranges that smooths the emission from the individual outflows in Fig. [4](#fig:901)A. Nonetheless, in both the full dataset image Fig. [4](#fig:901)A and [4](#fig:901)B and the short baselines only Fig. [4](#fig:901)C and [4](#fig:901)D, one can still clearly see a velocity gradient along the individual disks and along the circumbinary structure that will be further examined below.

![](906d_img_chanmap__12co_sblb.pdf)

![image](901_img_mom+cont_12co_sblb.pdf) ![image](901_img_mom+cont_12co_sb.pdf)

### $^{13}$CO emission

Our moment map of $^{13}$CO, a molecule useful in tracing protostellar disks and the inner envelope, is shown in Fig. [5](#fig:902). As seen in Fig. [5](#fig:902)A, the large scale emission appears to be tracing the higher density material around the outflow cavities of the combined two outflows from the binary, as well as the disks themselves. There is an asymmetry in the southeast that may indicate asymmetry in the gas structure into which the outflow is impacting or streamer motion. On the small scale, the inner regions of the disks are clearly seen in absorption in Figure [5](#fig:902)B as dashed contours (and later in the PV diagrams). These negatives arise from the line center where the line is optically thick in contrast to the line wings that are optically thin in emission, all of which are common in young sources (cite: vantHoff2023; lin2023). This absorption is likely from an over subtraction of the continuum due to the optically thick line emission (i.e. the compact continuum is not fully detected at line center so it is over subtracted), probably in combination with absorption by resolved-out, cold outer envelope material. In the case of the eDisk source R CrA IRS 7B-a, which has an observed continuum peak brightness temperature of $\sim$195 K, a detailed radiative transfer modeling of the disk (cite: takakuwa2024) shows that the continuum over-subtraction is dominated by the high background dust brightness temperature and high dust optical depth. On the other hand, there are also detected velocity gradients across each disk as well as a larger gradient over the circumbinary disk structure.

![image](902_img_mom+cont_13co_sblb.pdf) ![image](902_img_mom+cont_13co_sb.pdf)

### C$^{18}$O emission

In Fig. [6](#fig:903), we show the C$^{18}$O moment 1 map overlaid with moment 0 and continuum contours. C$^{18}$O was one of the main targeted molecular lines in the eDisk program due to its ability to trace the protostellar disk from which we estimate disk rotation and morphology. These maps are very similar to the $^{13}$CO maps in Fig. [5](#fig:902), although with less signal to noise.

Again the C$^{18}$O is tracing the higher density material of the disks, the circumbinary structure, and around the outflow cavities of the combined two outflows. The blueshifted material to the southeast of the binary, particularly noticeable in Fig. [6](#fig:903)C, is spatially offset to east of the outflow redshifted material seen CO, Fig. [3](#fig:906c). On the disk scale, there is again some continuum over-subtraction.

![image](903_img_mom+cont_c18o_sblb.pdf) ![image](903_img_mom+cont_c18o_sb.pdf)

### SO emission

Similar to the previous three molecular lines, Fig. [7](#fig:904) shows the moment 0 and 1 maps of SO. The SO emission is morphologically and kinematically distinct compared to the CO isotopes in that it mostly traces the circumbinary structure and the circumstellar disks (and the inner envelope) with very little outflow emission. As can be seen in Fig. [7](#fig:904)B, the disks in SO have similar velocities with the exception of a strong blue-shifted component near the center of disk A.

With Fig. [8](#fig:904b), we can compare the $^{12}$CO moment 0 from Figs. [4](#fig:901)A and [4](#fig:901)B with the SO moment 0 from Fig. [7](#fig:904). In general, the SO along the midplane appears to be tracing the circumbinary disk and the circumstellar disks. SO is also tracing some of the jet or outflow material very close to the protostars, particularly seen to the northeast along the outflow direction of source B in Figs. [8](#fig:904b) and [7](#fig:904)B. Note that this emission is also seen in $^{13}$CO in Fig. [5](#fig:902)B, and in both cases it is redshifted. In addition, there are two SO filamentary structures to the northeast and southwest in Fig. [8](#fig:904b) that appear to begin between the protostars and curve away. The southwest SO filament is aligned with a depression in the $^{12}$CO moment 0 contours, which is slightly offset to the west of the $^{13}$CO traced cavity wall seen in Figs. [5](#fig:902)A and B. Although the two filamentary structures are not tracing the same material as the $^{12}$CO directly, they may be still related to the outflow structures (e.g., enhanced cavity walls or interfaces) or perhaps streamers shaped by the outflow.

![](904_img_mom+cont_so_sblb.pdf)

![](904b_img_SO12CO.pdf)

### Other molecules

We have also imaged the other molecular lines seen in Table [\[tab:spec_data\]](#tab:spec_data). We detected $>$3$\sigma$ emission in all cases except SiO, $c$-C$_3$H$_2$ (5$_{2,4}$-4$_{1,3}$), and CH$_{3}$OH, where we instead only report their 1$\sigma$ noise levels (0.63 and 0.52 mJy beam$^{-1}$, respectively). See the details of the images listed in Table [\[tab:spec_results\]](#tab:spec_results). The channel maps of the detected lines not shown in the main text are provided in the Appendix.

+:----------------------+:--------------------:+:---------:+:---------:+:---------------:+:---------------:+:---------------:+:-------------:+
| Molecule              | Maps                 | RMS$^a$               | Moment 0$^b$                      | Moment 1$^c$                    |
+-----------------------+----------------------+-----------------------+-----------------------------------+---------------------------------+
| (GHz)                 |                      | (mJy beam$^{-1}$)     | Velocity Range (km s$^{-1}$)                                        |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| SiO                   | Not detected         | 0.63      | –         | –               | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| DCN                   | Channel & Moment     | 0.64      | –         | -2.46 - +1.56   | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| $c$-C$_3$H$_2$ 217.82 | Channel & Moment     | 0.60      | –         | -2.46 - +1.56   | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| $c$-C$_3$H$_2$ 217.94 | Channel & Moment     | 0.54      | –         | -2.46 - +1.56   | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| $c$-C$_3$H$_2$ 218.16 | Not detected         | 0.55      | –         | –               | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| H$_{2}$CO 218.22      | Channel & Moment     | 0.53      | –         | -3.80 - +2.90   | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| CH$_3$OH              | Not detected         | 0.52      | –         | –               | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| H$_{2}$CO 218.48      | Channel & Moment     | 0.53      | –         | -2.46 - +2.90   | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| H$_{2}$CO 218.76      | Channel & Moment     | 1.59      | –         | -2.50 - +1.51   | –               | –               | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| C$^{18}$O             | Channel & Moment     | 1.68      | 3.1       | -5.01 - +4.50   | -5.35 - +4.67   | -5.85 - +5.34   | -6.18 - +5.51 |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| SO                    | Channel, Moment & PV | 2.06      | –         | -4.35 - +4.34   | –               | -5.18 - +5.17   | –             |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| $^{13}$CO             | Channel, Moment & PV | 2.20      | 4.1       | -5.68 - +5.01   | -5.85 - +5.51   | -6.52 - +5.84   | -6.68 - +6.34 |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+
| $^{12}$CO             | Channel, Moment      | 1.00      | 1.9       | -18.23 - +20.50 | -31.57 - +30.03 | -21.45 - +23.68 | -8.08 - +8.00 |
+-----------------------+----------------------+-----------+-----------+-----------------+-----------------+-----------------+---------------+

# Analysis and Discussion

## Continuum Emission

As is clear in Fig. [1](#fig:900), the two circumstellar disks of the system are well aligned parallel to each other. In addition, the two disks are also well aligned with the (projected) orbital plane of the circumbinary structure, as seen in Figs. [1](#fig:900) (left) and [4](#fig:901)B. This suggests that this particular binary system likely formed in a relatively ordered process, such as disk fragmentation instead of a less ordered formation process, such as turbulent fragmentation followed by orbital migration to match the close spacing.

In addition, as hinted in Fig. [1](#fig:900) and shown with line projections in Fig. [2](#fig:905c), there are asymmetries in the 1.3 mm continuum disk emission. Specifically, these asymmetries are present in both disks and present themselves as more emission in the northeast half of the disk than in the southwest half; indeed, in both cases, the emission peak is shifted to northeast along the minor axis. We can use the outflows to determine the near/far side of the disks. Since the brighter (northeast) side of the disks are superposed on the blueshifted side of the CO outflow (see Fig. [4](#fig:901)), that is the far side of the disks. Thus, this brightness asymmetry along the minor axis is evidence that the dust disk is optically thick and has a significant geometrical thickness with the continuum-emitting dust not well-settled to the disk midplane, similar to other eDisk sources (e.g., IRAS 04302+2247, (cite: lin2023); R CrA IRS7B-a, (cite: takakuwa2024)).

## Gas Kinematics

To analyze the gas kinematics in the binary system, we follow a similar procedure to (cite: edisk) using position-velocity (PV) diagrams. The PV diagrams were created using the CASA task `impv`, and the fits to the data were done using the `pvanalysis` package of the SLAM (Spectral Line Analysis/Modeling) Python library (cite: yusuke_aso_2023).

SLAM uses the gas kinematics to fit the gas rotational profile as a simple power-law with radius described as

$$\begin{equation}
    v = V_b\left(\frac{r}{R_b}\right)^{-p},
\end{equation}$$

where $V_b$ is the mean velocity, $R_b$, is the radius of the mean velocity, and $p$ is the power-law index.

A power-law index of $p\approx0.5$ would be consistent with Keplerian rotation of a disk, whereas $p\approx1$ would be consistent with rotating and infalling material with conserved angular momentum. One can estimate the Keplerian mass enclosed within $R_b$ by

$$\begin{equation}
    M = \frac{V_b^2 R_b}{G \sin^2 i},
\end{equation}$$

where $G$ is the gravitational constant and $i$ is the inclination angle from the continuum fitting. SLAM will fit the velocities along the emission edge and ridge of the contours (see Fig. [9](#fig:907c2)). These two cases should bracket the Keplerian central protostellar mass, assuming a Keplerian profile power-law. For the angle of the PV cuts, we used the Gaussian-fit position angles. The PV line widths used are $\sim$1 beam for all images and any subsequent analysis. Note that IRAS 32, with the combination of two close disks and a large circumbinary disk/envelope, complicates the fitting process. In addition, the fitting process is also more complicated for young sources with evidence of infall from the envelope onto the circumstellar disks in PV diagrams (cite: ohashi1997).

### Circumbinary structure

![](907c2_img_vp__13co_sb_1beam.pdf)

For the circumbinary structure seen in Figs. [4](#fig:901)D and [5](#fig:902)D, the $^{13}$CO emission provides the best compromise between signal to noise and outflow contamination. Fig. [9](#fig:907c2) shows the $^{13}$CO PV diagram for the circumbinary structure using the short baseline observations only. Although one can clearly see evidence of differential rotation, there is also emission in the off-Keplerian quadrants (upper left and bottom right) of the diagram, which suggests infall motions too. In addition, those quadrants also have the peaks from the circumstellar disks, but we only fit the larger velocity variations for the outer region of the circumbinary structure.

Table [2](#tab:slam_params) gives the SLAM output fits for Fig. [9](#fig:907c2). Note that we allowed the central velocity to be a fit parameter in SLAM and did not force the adopted 5.86 km s$^{-1}$ used in our figures. The fit values of p were 0.58 and 0.79 for the ridge and edge fits, respectively. This is suggestive of some combination of Keplerian and infall motions. Although not conclusive, we posit that the circumbinary structure is a circumbinary disk. This may be fed by the filamentary structures seen in SO, Fig. [7](#fig:904). Circumbinary disks surrounding two circumstellar disks are frequently seen in young systems (cite: looney1997; takakuwa2012; hsieh2020; maureira2020; diaz-rodriguez2022). Although the SLAM fits do not provide strong evidence of the Keplerian kinematics nor place very accurate mass limits, the general circumbinary shape and kinematics follow the trends seen in other young sources.

| $^{13}CO$               | Circumbinary    | Source A      | Source B      |
|:------------------------|:----------------|:--------------|:--------------|
| Ridge                   |                 |               |               |
| M$_b$ (M$_{\odot}$)     | 0.53$\pm$0.09   | 0.5$\pm$0.6   | 0.48$\pm$0.03 |
| v$_{sys}$ (km s$^{-1}$) | 5.809$\pm$0.004 | 5.05$\pm$0.01 | 4.87$\pm$0.01 |
| p                       | 0.58$\pm$0.02   | 0.35$\pm$0.01 | 0.4$\pm$0.2   |
| Edge                    |                 |               |               |
| M$_b$ (M$_{\odot}$)     | 1.0$\pm$0.9     | 0.91$\pm$0.01 | 0.32$\pm$0.01 |
| v$_{sys}$ (km s$^{-1}$) | 5.791$\pm$0.005 | 5.48$\pm$0.01 | 5.46$\pm$0.01 |
| p                       | 0.79$\pm$0.02   | 0.36$\pm$0.01 | 0.71$\pm$0.02 |

: SLAM Fit Parameters

### Circumstellar Disks

![](907b_img_vpd_13co_sblb_both.pdf)

There are signs of circumstellar disk rotation present to some extent in all of our disk maps.

As can seen in Fig. [10](#fig:907b), there is absorption in the center of the disks at the low velocities of the line center, but that does not limit our ability to fit Keplerian velocity profiles as the higher velocities in the inner disk are more constraining. Instead, the two larger issues for fitting velocity profiles in the PV diagrams of Fig. [10](#fig:907b) are that the binary systems kinematically interact (i.e., overlapping spatially and spectrally) and, more importantly, that there is contamination from circumbinary, envelope, and outflow velocity components, especially in $^{12}$CO.

On the other hand, the data for $^{13}$CO and C$^{18}$O, which also have absorption in the inner region, are more consistent with each other and trace slightly closer into the disk for both sources. Nonetheless, even in these cases, the effect of the other binary system is demonstrated in the gas kinematics. For both sources, the inner portion of their PV diagram has a lower gas kinematic velocity that makes it more difficult to fit a protostellar mass with the kinematics.

We chose to use the mass fit from the $^{13}$CO emission, e.g., Fig. [5](#fig:902)A and B as the best compromise between signal to noise and contamination from the outflow and other disk. To minimize the effect of the other disk, we only fit the opposite side of the disks, which limits our fitting constraints. The $^{13}$CO PV diagrams of A and B differ in the length of the PV cuts, due to considerations of contamination from the other binary source since the position angle of both sources also coincides with the separation angle of the sources. For those reasons, we fit the IRAS 32 A PV diagram extended to 2 arcseconds around the center, while the IRAS 32 B fit extended out to 1.5 arcseconds around the center. This of course means some overlap in the inner regions, as the binary separation is 1.38 arcseconds. In addition, as we sample the gas to the outside of the disk, the kinematics will be more and more affected by the combined mass of the system, which will also change the rotation curve, making the kinematics more difficult to fit.

Table [2](#tab:slam_params) gives the SLAM output fits for Fig. [10](#fig:907b). The disk A fit values for p were 0.35 and 0.36 for the ridge and edge fits, respectively. However, the mass fits for source A are different (0.5 and 0.9 M$_\odot$, respectively) with very large uncertainty for the ridge fit. The disk B fit values for p were 0.43 and 0.71 for the ridge and edge fits, respectively. This is closer to the expected values for Keplerian motion, but as can be seen in Fig. [10](#fig:907b), the ridge fit is likely not a good representation of the kinematics as it falls much more steeply than the edge fit. The mass for the ridge only fit is 0.48$\pm$0.03 M$_\odot$.

## Inner binary region

In all 4 moment maps (Fig. [4](#fig:901), [5](#fig:902), [6](#fig:903), & [7](#fig:904)), the inner region along the binary separation is at or nearly at the system velocity with few velocity fluctuations. This is interesting because the PV diagrams show that 1) there is substantial infalling material all along the binary, assumed to be from either the large mass reservoir in the envelope or the circumbinary disk, and that 2) the material in the Keplerian disks are close enough that there could be kinematic interactions between them.

Towards the first point, although infall is expected to favor the lower mass protostar in young binary systems around rotating gas reservoirs (cite: bate2000), the similar protostar masses suggest infall all along the binary, including the inner region. Nevertheless, such a presumably chaotic region is not seen in $^{12}$CO, $^{13}$CO, nor C$^{18}$O at our current velocity and spatial resolution. The PV diagrams show an equal amount of material on both sides around the rest velocity in the region between the binaries, which is likely from the circumbinary disk with its own Keplerian rotation. This is not the case with SO in Fig. [7](#fig:904); while there is a small central region at the systematic velocity, there is also a velocity gradient along the binary separation. In the PV diagram, material seems to favor the negative velocities, or the blue side. Although the SO emission profile generally matches the CO isotopologues that trace the circumstellar disk rotation, SO is commonly found to trace multiple features of a protostar, including the disk, warm inner envelope, low-velocity outflow, jets, and binary interaction flows (cite: tychoniec2021; takakuwa2020).

![](900b_img_continuum_robust1.0_sb.pdf)

Finally, using only the short-baseline continuum data with a robust parameter of 1.0, shown in Fig. [11](#fig:900b), we detect continuum emission between the two circumstellar disks. Additionally, the strong SO emission in Fig. [8](#fig:904b) between the binaries, which is also seen in the moment 0 map in Fig. [7](#fig:904)B, also shows the connection of gas between the binaries. This emission could be evidence of gas funneling between the disks, as previously seen in L1551 IRS 5 (cite: takakuwa2017; takakuwa2020) and predicted by numerical simulations (cite: matsumoto2019).

## Outflows

Among the four molecular lines chosen for analysis, $^{12}$CO, to a lesser extent $^{13}$CO, and arguably even C$^{18}$O, capture emission from the outflows (see Fig. [4](#fig:901) & [5](#fig:902)). That is, we see high-velocity emission normal to the disk PA for disk A, disk B, and the circumbinary disk. The driving mechanism for the overall outflows in this system could be all 3 disk components. Indeed, MHD simulations of (cite: machida2009) revealed that circumbinary disks of a protostellar system can drive outflows, although they examined a closer binary separation.

While the $^{12}$CO moment maps show clear evidence of an outflow originating from disk A, the case for disk B is best seen in Fig. [3](#fig:906c) in the blue channels between the velocity ranges of -4.90 and -2.99 km s$^{-1}$, and the red channels between the velocity ranges of +1.45 and +2.72 km s$^{-1}$. However, in Figs. [4](#fig:901)A there is also clear redhifted material in the northern blueshifted lobe and blueshifted material in the southern redshifted lobe.

For the possibility of the circumbinary structure driving an outflow, it is less clear. As seen in Fig. [3](#fig:906c) in the northeast blue channels (velocity ranges of -6.17 to -5.53 km s$^{-1}$) and in the southwest (velocity ranges of +3.36 to +9.71 km s$^{-1}$), there are strong persistent features that are equidistant to the two disks. These may be interaction regions (between the A and B outflows, see below), so visually the existence of three outflows is inconclusive. On the other hand, there is also widespread low-velocity outflow gas emission that is best seen in the blue channels in the north traced by CO and $^{13}$CO, emphasized in Figs. [4](#fig:901)A and [5](#fig:902)A. In either case, further modeling is necessary to address a third outflow.

For the clear individual protostellar outflows, the blue-shifted (negative velocities relative to the system velocity) regions tend to be in the northeast for both the individual sources and the circumbinary disk. Similarly, the red-shifted regions are opposite, in the southwest. They show both low- and high- velocity emission centered on both sources and centered on the inferred circumbinary disk center. The outflow 3$\sigma$ emission extends to the edges of the $^{12}$CO field-of-view, putting the projected length of any one particular side at about 20 arcsec (3000 au). We calculate a deprojected dynamical age of the observed outflow of $\sim$280 years by using the deprojected maximum velocity of the $^{12}$CO outflow (adopting an inclination of 70$^\circ$, the average of the disk inclination fits from Table [1](#tab:cont_derived_data) and $\sim$17 km s$^{-1}$ from visual inspection of the cube).

![](906e_img_12co_mom0_w_arrow.pdf)

As mentioned above, there are bright red and blue $^{12}$CO structures in the southwest highlighted in Fig. [12](#fig:906e). The structures begin somewhat equidistant southwest of the protostars and extend to the southwest; the structures are detected in the higher velocity red and blue components. The blue structure is peaking generally to the north of the red structure (see Fig. [12](#fig:906e)). In addition, on the opposite side, to the northeast of the binary pair, there is a red component in channels with velocities of 2.09 and 2.72 km s$^{-1}$ that is best seen in Figure [3](#fig:906c). There is also a blue component in channels with velocities of -8.07 to -4.06 km s$^{-1}$ but with much more contamination by the blue shifted lobe. The northern interaction region is in general less defined compared to the south.

The mostly likely explanation for these features is two regions where the outflows driven by each of the binary disks A and B are interacting. If we consider the two outflows as cones of entrained material then the two outflows will intercept each other, resulting in flows or possibly shocks that enhance the emission toward the observer and away from the observer (see Figure [13](#fig:920) for a cartoon of one possible configuration). On the south side of the binary, the interaction is more pronounced than on the north side. With highly inclined protostars, it is common for outflows to exhibit both redshifted and blueshifted emission on both sides of the outflow (cite: vantHoff2023), so with an inclination of around 70$^{\circ}$ in IRAS32, the interacting gas easily flows blueshifted and redshifted on both sides. In this case, the blue component and the red component are seen as nearly co-spatial along the line of sight. Note that Fig. [12](#fig:906e) also nicely shows red jet emission from Source A.

Although we do not detect an SiO jet in either outflow component of the binary, this is not uncommon in Class 0 sources as about only 33% of the sources with an internal luminosity between 0.1 and 1 L$_\odot$ have detected SiO emission (cite: padio2021); IRAS 32 has a total luminosity for both sources of 1.6 L$_\odot$, hence each source individually may be too weak to drive a detectable SiO jet.

![](920cartoon3.png)

## SO structure

The SO moment maps, in Figs. [7](#fig:904) and [8](#fig:904b), show structures influenced by the Keplerian motion of the circumbinary disk and the circumstellar disks. The velocities in these features are not as large as the corresponding velocities in $^{13}$CO in Fig. [5](#fig:902)B, (e.g., also compare Fig. [14](#fig:907d) with Fig. [10](#fig:907b)), suggesting that the SO is tracing circumstellar disk Keplerian material with generally larger radii. As also seen in Fig. [7](#fig:904), the filamentary structures (described in §[3.2.4](#SOemission)) exhibit slight velocity gradients toward the binaries. The filament kinematics in Fig. [7](#fig:904) show a blue component in the north and a red component in the south. We interpret these asymmetric structures as perhaps streamers between the envelope and the circumstellar and/or circumbinary disks.

![](907d_img_so_pv.pdf)

With Fig. [14](#fig:907d), we can compare the PV diagram of the SO emission to the $^{13}$CO emission in Fig. [10](#fig:907b). Besides the lack of central velocities in $^{13}$CO, the two PV diagrams are broadly similar, although the SO velocity ranges are smaller for most features, as mentioned above. However, the velocity gradients in the PV diagrams are somewhat different in detail. On the blueshifted and redshifted sides of the disks in Fig. [14](#fig:907d), one can again see hints of the Keplerian rotation (which is much more clear in the $^{13}$CO of Fig. [10](#fig:907b)). One feature that is more noticeable in the SO PV diagram is the bright blue emission between the two disks, just below the blueshifted side of disk B in Fig. [14](#fig:907d). This is the location of the filament structure in SO in the northeast, suggesting a possible interaction from the incoming flow of material at that location.

When comparing the SO and $c$-C$_3$H$_2$ line emission of IRAS 32 with those of the eDisk source L1527 (cite: vantHoff2023), they have similar features. As discussed above, the SO line emission is also extended and traces the disk (cite: vantHoff2023) in both sources. The $c$-C$_3$H$_2$ in both sources is not detected in the outflow cavity but rather in the inner envelope (or circumbinary region). In fact, out of the eDisk survey IRAS 32 most resembles the detection of these two molecules with L1527. It is possible that IRAS 32, like L1527, may be another example of a source that exhibits warm carbon-chain chemistry pathways (cite: sakai2008), wherein carbon-chain molecules are produced via CH$_4$ evaporated from dust grains.

# Conclusion

We observed the emission towards IRAS 32 at a resolution of $\sim$0.03$''$ in the 1.3 mm dust continuum and $\sim$0.1$''$ for numerous molecular lines, including $^{12}$CO ($J=2\rightarrow1$), $^{13}$CO ($J=2\rightarrow1$), C$^{18}$O ($J=2\rightarrow1$), and SO ($J=6_5\rightarrow5_4$), as a part of the ALMA eDisk Large Program. Our conclusions are:

1.  IRAS 32 is a Class 0 newly discovered binary protostellar system with circumstellar disks surrounding both protostars and a circumbinary disk. The circumstellar disks are aligned parallel to each other and to the (projected) orbital plane, indicating that this particular binary system is likely formed in a relatively ordered fashion, such as disk fragmentation (as opposed to turbulent fragmentation followed by orbital migration).

2.  We detected all the molecular lines in Table [\[tab:spec_data\]](#tab:spec_data) except for SiO, CH$_{3}$OH, and the 218.16 transition of $c$-C$_3$H$_2$. Maps of CO, $^{13}$CO, and C$^{18}$O show outflows in the NE-SW direction, normal to the circumbinary disk, and the aligned circumstellar disks. SO emission mainly shows the inner envelope/circumbinary disk and the circumstellar disks structures. The remaining molecular lines were detected in only a few channels and seemed to mostly favor the SW region of the binary system.

3.  IRAS 32 A has a Gaussian-fit estimated disk radius of 180$\pm$2 millarcseconds (26.9$\pm$0.3 au), whereas the IRAS 32 B disk is estimated at 153$\pm$2 millarcseconds (22.8$\pm$0.3 au). The circumbinary disk-like structure size is estimated at 3.25$''$ (488 au).

4.  The (northeast) far-side of the disk is brighter than the (southeast) near-side in dust continuum along the minor axis, which indicates that the dust emission is optically thick and the grains responsible for the continuum emission has yet to settle into a thin layer near the mid-plane.

5.  No clear substructures are detected in the circumstellar disks. The radial profile of the circumstellar disks are non-Gaussian. More careful modeling is required.

6.  The dust mass for protostars A and B are given as either a) 21.9$\pm$1.1 and 12.7$\pm$0.6 M$_{\Earth}$ for an average temperature derived from a radiative transfer calculation using the bolometric luminosity as prescribed by (cite: tobin2020), or b) 52.0$\pm$2.6 and 29.1$\pm$1.4 M$_{\Earth}$ for T=20 K.

7.  The protostar masses, derived from SLAM fits to the PV diagrams of $^{13}$CO ($J=2\rightarrow1$) emission in the circumstellar disks, are estimated to be 0.91$\pm$0.01 M$_\odot$ and 0.32$\pm$0.01 M$_\odot$ for the edge fit and 0.50$\pm$0.55 M$_\odot$ and 0.48$\pm$0.03 M$_\odot$ for the ridge fit, for source A and B, respectively. The errors here are large due to the complicated nature of the binary system. Since the stellar masses are likely somewhere between the edge and ridge fits, we find expected stellar masses of $<$0.92 M$_\odot$ and 0.31-0.51 M$_\odot$, for sources A and B, respectively.

# Acknowledgments

FJE and LWL acknowledge support from NSF AST-2108794. ST is supported by JSPS KAKENHI grant Nos. 21H00048 and 21H04495, and by NAOJ ALMA Scientific Research grant No. 2022-20A. J.J.T. acknowledges support from NASA XRP 80NSSC22K1159. J.K.J. acknowledges support from the Independent Research Fund Denmark (grant No. 0135-00123B). Y.A. acknowledges support by NAOJ ALMA Scientific Research Grant code 2019-13B, Grant-in-Aid for Scientific Research (S) 18H05222, and Grant-in-Aid for Transformative Research Areas (A) 20H05844 and 20H05847. W.K. was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (NRF-2021R1F1A1061794). N.O. acknowledges support from National Science and Technology Council (NSTC) in Taiwan through grants NSTC 109-2112-M-001-051 and 110-2112-M-001-031. Z.-Y.L. is supported in part by NASA NSSC20K0533 and NSF AST-2307199 and AST-1910106. ZYDL acknowledges support from NASA 80NSSCK1095, the Jefferson Scholars Foundation, the NRAO ALMA Student Observing Support (SOS) SOSPA8-003, the Achievements Rewards for College Scientists (ARCS) Foundation Washington Chapter, the Virginia Space Grant Consortium (VSGC), and UVA research computing (RIVANNA). IdG acknowledges support from grant PID2020-114461GB-I00, funded by MCIN/AEI/10.13039/501100011033. H.-W.Y. acknowledges support from National Science and Technology Council (NSTC) in Taiwan through grant NSTC 110-2628-M-001-003-MY3 and from the Academia Sinica Career Development Award (AS-CDA-111-M03).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00261.L. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Moment 0 and Channel Maps

![](908h_img_chanmap__13co_sblb.pdf)

![](908i_img_chanmap__c18o_sblb.pdf)

![](908j_img_chanmap__so_sblb.pdf)

This section includes the moment 0 and channel maps for all the molecular lines with sufficient emission that were not already shown in the main text. This includes the channel maps of $^{13}$CO, C$^{18}$O, and SO in Fig. [15](#fig:908h), [16](#fig:908i), and [17](#fig:908j), respectively. All of the lines are consistent with the analysis presented in the main text.

## DCN

![](908d2_img_mom0__dcn_sblb.pdf)

![](908d_img_chanmap__dcn_sblb.pdf)

The DCN (3-2) emission is shown in Figs. [18](#fig:908d2) and [19](#fig:908d). With an adopted rest velocity at 5.86 km s$^{-1}$, DCN has emission in about 4 channels (-2.46, -1.12, 0.22, and 1.56 km s$^{-1}$), which slightly favors the blue north-east. Morphologically, the blue and red sides look most similar to C$^{18}$O in Fig. [16](#fig:908i), which traces a combination of circumbinary disk and outflow although the blue side of DCN seems to trace out more of the NE outflow cavity than the C$^{18}$O.

## $c$-C$_3$H$_2$

![](908a2_img_mom0__cc3h2-217.82ghz_sblb.pdf)

![](908a_img_chanmap__cc3h2_217.82ghz_sblb.pdf)

The blended line of c-C$_{3}$H$_{2}$ at 217.82 GHz (6$_{0,6}$-5$_{1,5}$) and (6$_{1,6}$-5$_{0,5}$) is shown in Figs. [20](#fig:908a2) and [21](#fig:908a), which also has emission in the same 4 channels as DCN (-2.46, -1.12, 0.22, and 1.56 km s$^{-1}$). The c-C$_{3}$H$_{2}$ is mostly tracing a flattened region surrounding the binaries. This morphology is most similar to the $^{13}$CO and C$^{18}$O lines in Figs. [15](#fig:908h) and [16](#fig:908i), respectively. Although c-C$_{3}$H$_{2}$ is often considered a good tracer of irradiated gas inside outflow cavities, in this case, c-C$_{3}$H$_{2}$ is mostly tracing the circumbinary disk or inner envelope. This can be compared to eDisk source L1527 (cite: vantHoff2023), where the c-C$_{3}$H$_{2}$ emission is also tracing a flattened region of the inner envelope.

The 217.94 GHz transition (5$_{1,4}$-4$_{2,3}$) is shown in Figs. [22](#fig:908b2) and [23](#fig:908b) with a very similar emission, albeit with weaker emission.

![](908b2_img_mom0__cc3h2-217.94ghz_sblb.pdf)

![](908b_img_chanmap__cc3h2_217.94ghz_sblb.pdf)

## H$_2$CO

![](908e2_img_mom0__h2co-218.22ghz_sblb.pdf)

![](908e_img_chanmap__h2co-218.22ghz_sblb.pdf)

Formaldehyde at 218.22 GHz (3$_{0,3}$-2$_{0,2}$) is shown in Figs. [24](#fig:908e2) and [25](#fig:908e). It has emission from -3.80 to 2.90 km s$^{-1}$ in steps of $\Delta$v = 1.34 km s$^{-1}$. The relatively high velocity channels show emission around the SE side (blue) of protostar A and the NW side (red) of protostar B. As we approach the lower velocity channels, the emission begins to look like the $^{13}$CO map in Fig. [15](#fig:908h) with the blue side predominately in the SE region and the NE outflows, and the red side predominately in the SW side of the binary. However, there is a strong emission feature on the E side of protostar B in the red channel. The only other equivalent feature is in $^{12}$CO. It is possible that this is the NE outflow of protostar B. Similarly, on the blue side there is a bright emission feature south of protostar B that is projected from either protostar. It does not seem to match with any other feature seen in the other molecular lines, but with much lower spectral resolution than the CO and SO lines, it can be difficult to compare. The formaldehyde 218.48 GHz transition (3$_{2,2}$-2$_{2,1}$) is shown in Figs. [26](#fig:908f2) and [27](#fig:908f). It is similar except with weaker emission, the outer channels fading into the noise, and the sharp emission features at low velocities are subdued. The formaldehyde 218.76 GHz transition (3$_{2,1}$-2$_{2,0}$) is shown in Figs. [28](#fig:908g2) and [29](#fig:908g). It is again similar to the other H$_2$CO lines with even weaker emission but with higher velocity resolution.

![](908f2_img_mom0__h2co-218.48ghz_sblb.pdf)

![](908f_img_chanmap__h2co-218.48ghz_sblb.pdf)

![](908g2_img_mom0__h2co-218.76ghz_sblb.pdf)

![](908g_img_chanmap__h2co-218.76ghz_sblb.pdf)

natexlab

(ref: adams1989) Adams, F. C., Ruden, S. P., & Shu, F. H. 1989, ApJ, 347, 959, doi: [`10.1086/168187`](http://doi.org/10.1086/168187)

(ref: brogan2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3, doi: [`10.1088/2041-8205/808/1/L3`](http://doi.org/10.1088/2041-8205/808/1/L3)

(ref: andre1993) Andre, P., Ward-Thompson, D., & Barsony, M. 1993, ApJ, 406, 122, doi: [`10.1086/172425`](http://doi.org/10.1086/172425)

(ref: andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41, doi: [`10.3847/2041-8213/aaf741`](http://doi.org/10.3847/2041-8213/aaf741)

(ref: yusuke_aso_2023) Aso, Y., & Sai, J. 2023, jinshisai/SLAM: First Release of SLAM, v1.0.0, Zenodo, doi: [`10.5281/zenodo.7783868`](http://doi.org/10.5281/zenodo.7783868)

(ref: Bae2022) Bae, J., Isella, A., Zhu, Z., et al. 2022, arXiv e-prints, arXiv:2210.13314. [`https://arxiv.org/abs/2210.13314`](https://arxiv.org/abs/2210.13314)

(ref: bate2000) Bate, M. R. 2000, MNRAS, 314, 33, doi: [`10.1046/j.1365-8711.2000.03333.x`](http://doi.org/10.1046/j.1365-8711.2000.03333.x)

(ref: beckwith1990) Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten, R. 1990, AJ, 99, 924, doi: [`10.1086/115385`](http://doi.org/10.1086/115385)

(ref: bracco2020) Bracco, A., Bresnahan, D., Palmeirim, P., et al. 2020, A&A, 644, A5, doi: [`10.1051/0004-6361/202039282`](http://doi.org/10.1051/0004-6361/202039282)

(ref: bresnahan2018) Bresnahan, D., Ward-Thompson, D., Kirk, J. M., et al. 2018, A&A, 615, A125, doi: [`10.1051/0004-6361/201730515`](http://doi.org/10.1051/0004-6361/201730515)

(ref: diaz-rodriguez2022) Diaz-Rodriguez, A. K., Anglada, G., Blázquez-Calero, G., et al. 2022, ApJ, 930, 91, doi: [`10.3847/1538-4357/ac3b50`](http://doi.org/10.3847/1538-4357/ac3b50)

(ref: dong2015) Dong, R., Zhu, Z., & Whitney, B. 2015, ApJ, 809, 93, doi: [`10.1088/0004-637X/809/1/93`](http://doi.org/10.1088/0004-637X/809/1/93)

(ref: duchene2013) Duchêne, G., & Kraus, A. 2013, ARA&A, 51, 269, doi: [`10.1146/annurev-astro-081710-102602`](http://doi.org/10.1146/annurev-astro-081710-102602)

(ref: dzib2018) Dzib, S. A., Loinard, L., Ortiz-León, G. N., Rodrı́guez, L. F., & Galli, P. A. B. 2018, ApJ, 867, 151, doi: [`10.3847/1538-4357/aae687`](http://doi.org/10.3847/1538-4357/aae687)

(ref: encalada2021) Encalada, F. J., Looney, L. W., Tobin, J. J., et al. 2021, ApJ, 913, 149, doi: [`10.3847/1538-4357/abf4fd`](http://doi.org/10.3847/1538-4357/abf4fd)

(ref: frank2014) Frank, A., Ray, T. P., Cabrit, S., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 451, doi: [`10.2458/azu_uapress_9780816531240-ch020`](http://doi.org/10.2458/azu_uapress_9780816531240-ch020)

(ref: galli2020) Galli, P. A. B., Bouy, H., Olivares, J., et al. 2020, VizieR Online Data Catalog, J/A+A/634/A98

(ref: hsieh2020) Hsieh, C.-H., Lai, S.-P., Cheong, P.-I., et al. 2020, ApJ, 894, 23, doi: [`10.3847/1538-4357/ab7b69`](http://doi.org/10.3847/1538-4357/ab7b69)

(ref: huang2018) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJL, 869, L42, doi: [`10.3847/2041-8213/aaf740`](http://doi.org/10.3847/2041-8213/aaf740)

(ref: kepley2020) Kepley, A. A., Tsutsumi, T., Brogan, C. L., et al. 2020, Publications of the Astronomical Society of the Pacific, 132, 024505, doi: [`10.1088/1538-3873/ab5e14`](http://doi.org/10.1088/1538-3873/ab5e14)

(ref: kuznetsova2022) Kuznetsova, A., Bae, J., Hartmann, L., & Mac Low, M.-M. 2022, ApJ, 928, 92, doi: [`10.3847/1538-4357/ac54a8`](http://doi.org/10.3847/1538-4357/ac54a8)

(ref: lee2019) Lee, A. T., Offner, S. S. R., Kratter, K. M., Smullen, R. A., & Li, P. S. 2019, ApJ, 887, 232, doi: [`10.3847/1538-4357/ab584b`](http://doi.org/10.3847/1538-4357/ab584b)

(ref: lin2023) Lin, Z.-Y. D., Li, Z.-Y., Tobin, J. J., Ohashi, N., & eDisk Team. 2023, ApJ, submitted

(ref: looney1997) Looney, L. W., Mundy, L. G., & Welch, W. J. 1997, ApJL, 484, L157, doi: [`10.1086/310795`](http://doi.org/10.1086/310795)

(ref: machida2009) Machida, M. N., ichiro Inutsuka, S., & Matsumoto, T. 2009, The Astrophysical Journal, 704, L10, doi: [`10.1088/0004-637X/704/1/L10`](http://doi.org/10.1088/0004-637X/704/1/L10)

(ref: matsumoto2019) Matsumoto, T., Saigo, K., & Takakuwa, S. 2019, ApJ, 871, 36, doi: [`10.3847/1538-4357/aaf6ab`](http://doi.org/10.3847/1538-4357/aaf6ab)

(ref: maureira2020) Maureira, M. J., Pineda, J. E., Segura-Cox, D. M., et al. 2020, ApJ, 897, 59, doi: [`10.3847/1538-4357/ab960b`](http://doi.org/10.3847/1538-4357/ab960b)

(ref: moe2017) Moe, M., & Di Stefano, R. 2017, ApJS, 230, 15, doi: [`10.3847/1538-4365/aa6fb6`](http://doi.org/10.3847/1538-4365/aa6fb6)

(ref: nutter2005) Nutter, D. J., Ward-Thompson, D., & André, P. 2005, MNRAS, 357, 975, doi: [`10.1111/j.1365-2966.2005.08711.x`](http://doi.org/10.1111/j.1365-2966.2005.08711.x)

(ref: ohashi1997) Ohashi, N., Hayashi, M., Ho, P. T. P., & Momose, M. 1997, ApJ, 475, 211, doi: [`10.1086/303533`](http://doi.org/10.1086/303533)

(ref: ohashi2014) Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ, 796, 131, doi: [`10.1088/0004-637X/796/2/131`](http://doi.org/10.1088/0004-637X/796/2/131)

(ref: edisk) Ohashi, N., Tobin, J. J., Jørgensen, J. K., et al. 2023, ApJ, 951, 8, doi: [`10.3847/1538-4357/acd384`](http://doi.org/10.3847/1538-4357/acd384)

(ref: padoan2002) Padoan, P., & Nordlund, Å. 2002, ApJ, 576, 870, doi: [`10.1086/341790`](http://doi.org/10.1086/341790)

(ref: perez2016) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519, doi: [`10.1126/science.aaf8296`](http://doi.org/10.1126/science.aaf8296)

(ref: peterson2011) Peterson, D. E., o Garatti, A. C., Bourke, T. L., et al. 2011, The Astrophysical Journal Supplement Series, 194, 43, doi: [`10.1088/0067-0049/194/2/43`](http://doi.org/10.1088/0067-0049/194/2/43)

(ref: Pinte2020) Pinte, C., Price, D. J., Ménard, F., et al. 2020, ApJL, 890, L9, doi: [`10.3847/2041-8213/ab6dda`](http://doi.org/10.3847/2041-8213/ab6dda)

(ref: padio2021) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45, doi: [`10.1051/0004-6361/202038429`](http://doi.org/10.1051/0004-6361/202038429)

(ref: raghavan2010) Raghavan, D., McAlister, H. A., Henry, T. J., et al. 2010, ApJS, 190, 1, doi: [`10.1088/0067-0049/190/1/1`](http://doi.org/10.1088/0067-0049/190/1/1)

(ref: rau2011) Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71, doi: [`10.1051/0004-6361/201117104`](http://doi.org/10.1051/0004-6361/201117104)

(ref: rossano1978) Rossano, G. S. 1978, AJ, 83, 234, doi: [`10.1086/112198`](http://doi.org/10.1086/112198)

(ref: ruge2015) Ruge, J. P., Wolf, S., Demidova, T., & Grinin, V. 2015, A&A, 579, A110, doi: [`10.1051/0004-6361/201321770`](http://doi.org/10.1051/0004-6361/201321770)

(ref: sakai2008) Sakai, N., Sakai, T., Hirota, T., & Yamamoto, S. 2008, ApJ, 672, 371, doi: [`10.1086/523635`](http://doi.org/10.1086/523635)

(ref: sakai2014) Sakai, N., Oya, Y., Sakai, T., et al. 2014, ApJL, 791, L38, doi: [`10.1088/2041-8205/791/2/L38`](http://doi.org/10.1088/2041-8205/791/2/L38)

(ref: sana2011) Sana, H., & Evans, C. J. 2011, in Active OB Stars: Structure, Evolution, Mass Loss, and Critical Limits, ed. C. Neiner, G. Wade, G. Meynet, & G. Peters, Vol. 272, 474–485, doi: [`10.1017/S1743921311011124`](http://doi.org/10.1017/S1743921311011124)

(ref: seale2008) Seale, J. P., & Looney, L. W. 2008, ApJ, 675, 427, doi: [`10.1086/526766`](http://doi.org/10.1086/526766)

(ref: dom2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228, doi: [`10.1038/s41586-020-2779-6`](http://doi.org/10.1038/s41586-020-2779-6)

(ref: sheehan2020) Sheehan, P. D., Tobin, J. J., Federman, S., Megeath, S. T., & Looney, L. W. 2020, ApJ, 902, 141, doi: [`10.3847/1538-4357/abbad5`](http://doi.org/10.3847/1538-4357/abbad5)

(ref: snell1980) Snell, R. L., Loren, R. B., & Plambeck, R. L. 1980, ApJL, 239, L17, doi: [`10.1086/183283`](http://doi.org/10.1086/183283)

(ref: suriano2018) Suriano, S. S., Li, Z.-Y., Krasnopolsky, R., & Shang, H. 2018, MNRAS, 477, 1239, doi: [`10.1093/mnras/sty717`](http://doi.org/10.1093/mnras/sty717)

(ref: takakuwa2017) Takakuwa, S., Saigo, K., Matsumoto, T., et al. 2017, ApJ, 837, 86, doi: [`10.3847/1538-4357/aa6116`](http://doi.org/10.3847/1538-4357/aa6116)

(ref: takakuwa2012) Takakuwa, S., Saito, M., Lim, J., et al. 2012, ApJ, 754, 52, doi: [`10.1088/0004-637X/754/1/52`](http://doi.org/10.1088/0004-637X/754/1/52)

(ref: takakuwa2020) Takakuwa, S., Saigo, K., Matsumoto, T., et al. 2020, ApJ, 898, 10, doi: [`10.3847/1538-4357/ab9b7c`](http://doi.org/10.3847/1538-4357/ab9b7c)

(ref: takakuwa2024) Takakuwa, S., Saigo, K., Kido, M., et al. 2024, arXiv e-prints, arXiv:2401.08722, doi: [`10.48550/arXiv.2401.08722`](http://doi.org/10.48550/arXiv.2401.08722)

(ref: bettermoments) Teague, R., & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173, doi: [`10.3847/2515-5172/aae265`](http://doi.org/10.3847/2515-5172/aae265)

(ref: casa2022) Team, T. C., Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Testi2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339–361, doi: [`10.2458/azu_uapress_9780816531240-ch015`](http://doi.org/10.2458/azu_uapress_9780816531240-ch015)

(ref: tobin2016) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73, doi: [`10.3847/0004-637X/818/1/73`](http://doi.org/10.3847/0004-637X/818/1/73)

(ref: tobin2020) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130, doi: [`10.3847/1538-4357/ab6f64`](http://doi.org/10.3847/1538-4357/ab6f64)

(ref: tobin2022) Tobin, J. J., Offner, S. S. R., Kratter, K. M., et al. 2022, ApJ, 925, 39, doi: [`10.3847/1538-4357/ac36d2`](http://doi.org/10.3847/1538-4357/ac36d2)

(ref: tsukamoto2017) Tsukamoto, Y., Okuzumi, S., & Kataoka, A. 2017, ApJ, 838, 151, doi: [`10.3847/1538-4357/aa6081`](http://doi.org/10.3847/1538-4357/aa6081)

(ref: tychoniec2021) Tychoniec, Ł., van Dishoeck, E. F., van’t Hoff, M. L. R., et al. 2021, A&A, 655, A65, doi: [`10.1051/0004-6361/202140692`](http://doi.org/10.1051/0004-6361/202140692)

(ref: vanderMarel2013) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340, 1199, doi: [`10.1126/science.1236770`](http://doi.org/10.1126/science.1236770)

(ref: vantHoff2023) van’t Hoff, M. L. R., Tobin, J. J., Li, Z.-Y., et al. 2023, ApJ, 951, 10, doi: [`10.3847/1538-4357/accf87`](http://doi.org/10.3847/1538-4357/accf87)

(ref: ward-duong2015) Ward-Duong, K., Patience, J., De Rosa, R. J., et al. 2015, MNRAS, 449, 2618, doi: [`10.1093/mnras/stv384`](http://doi.org/10.1093/mnras/stv384)

(ref: wilkings1992) Wilking, B. A., Greene, T. P., Lada, C. J., Meyer, M. R., & Young, E. T. 1992, ApJ, 397, 520, doi: [`10.1086/171808`](http://doi.org/10.1086/171808)

(ref: yen2014) Yen, H.-W., Takakuwa, S., Ohashi, N., et al. 2014, ApJ, 793, 1, doi: [`10.1088/0004-637X/793/1/1`](http://doi.org/10.1088/0004-637X/793/1/1)

(ref: zhang2015) Zhang, K., Blake, G. A., & Bergin, E. A. 2015, ApJL, 806, L7, doi: [`10.1088/2041-8205/806/1/L7`](http://doi.org/10.1088/2041-8205/806/1/L7)

(ref: zhang2018) Zhang, S., Zhu, Z., Huang, J., et al. 2018, ApJL, 869, L47, doi: [`10.3847/2041-8213/aaf744`](http://doi.org/10.3847/2041-8213/aaf744)

(ref: zucker2020) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2020, A&A, 633, A51, doi: [`10.1051/0004-6361/201936145`](http://doi.org/10.1051/0004-6361/201936145)

</paper>

Write the methods card for this paper.