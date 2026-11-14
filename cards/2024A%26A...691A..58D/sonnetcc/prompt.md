# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A..58D\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...691A..58D",
 "title": "Multiple-scale gas infall through gravity torques on Milky Way twins",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "da Silva, Patrícia",
 "n_authors": 2,
 "arxiv_id": "2410.01721",
 "doi": "10.1051/0004-6361/202450500",
 "alma_projects_linked_by_archive": [
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00886.L",
  "2018.1.00517.S",
  "2018.1.01651.S",
  "2019.1.00876.S",
  "2019.1.01718.S",
  "2019.1.01730.S",
  "2019.1.01742.S"
 ]
}
```

Paper text:
<paper>
# Multiple-scale gas infall through gravity torques on Milky Way twins

# Introduction

![](galaxies_new.png)

Supermassive black holes (SMBHs) are ubiquitous at the centres of galaxies, and they play an important role in their evolution. A possible correlation exists between the mass of the black hole and the bulge mass, suggesting a co-evolution of the two (cite: Kormendy2013). One of the main phenomena invoked for this co-evolution is the feedback of active galaxy nucleus (AGN) episodes on the star formation rate in galaxies. AGN winds are able to produce molecular outflows from galactic nuclei, depleting the gaseous medium and moderating or quenching star formation in disks (cite: Fiore2017). The efficiency of AGN winds is related to the Eddington ratio, and it is only significant when this ratio exceeds 0.01 (cite: Heckman2014). Below this, the AGN feedback is more efficient in the radio mode through radio jets (cite: Garcia-Burillo2014; Dasyra2015).

Driving gas towards the galaxy centre to fuel both the central black hole and central star formation is an important ingredient in the co-evolution as well. The mechanisms for these inflows widely depend on the scale: at kiloparsec (kpc) scales in galaxy disks, viscous torques are negligible (cite: Lin1987), and only gravity torques due to non-axisymmetric potentials are possible (cite: Buta1996). Stellar bars are the most efficient and long-lived features in this domain, and they are able to remove the angular momentum of the gas in a few rotations (cite: Garcia-Burillo2005). By computing gravity torques from the observed images of the old stellar component, together with the observed gas maps in nearby galaxies, (cite: Garcia-Burillo2012) concluded that the gas is driven inwards towards the SMBH in only 30% of cases, while it is either stalled in a nuclear ring at the inner Lindblad resonance (ILR) of the bar or driven outwards, from corotation to the outer Lindblad resonance (OLR). The gas infall requires multi-scale mechanisms to reach the very centre, as was already described by (cite: Shlosman1989; Shlosman90; Berentzen2007). For example, recent high-resolution ALMA observations have revealed that embedded nuclear bars efficiently feed the nucleus at a scale of 10 pc (cite: combes14; audibert19). Simulations of nuclear bars that feed the nucleus were made by (cite: Englmaier2004), and (cite: Laine2002) observed that more Seyfert galaxies are present in barred galaxies, proving the importance of this feature in the feeding of the nucleus.

We focus on spiral galaxies of the same type as the Milky Way (MW), that is, with an Sbc morphology, with different bar strengths (SABbc and SBbc) and non-barred counterparts. The study of morphological twins of the MW will allow us to understand the history of its secular evolution. Although our MW is the best-known galaxy because Earth lies in it, it is necessary to study its nearby twins for a grasp on the evolution it may have had and to understand its formation through gas infall, fostered by the bar. Time is very important because the environment can change drastically. For instance, the bar strength is likely not to be a long-lived characteristic (1 to 2 Gyr if there is gas in the disk) because it varies according to gas flows (cite: Bournaud2002) or even according to many other mechanisms during cosmological evolution (cite: Bi2022). Regarding the AGN activity, we know that the Eddington ratio of the MW nucleus is very low $\sim$ 10$^{-9}$, but it could have been quite high in the past (cite: Sarkar2023). When we take into account that AGN episodes are short-lived in galaxies, with a duty cycle of about 40 Myr (cite: Shankar2009), the influence must be acknowledged as variable, if it exists.

We study the molecular gas torques in order to understand the feeding processes in the MW analogues, and also compared with the non-barred galaxies to quantify the effect of the bar strength. By using data from Atacama Large Millimeter/Submillimeter Array (ALMA), Hubble Space Telescope (HST) images in the F814W filter, and the Legacy survey images in the Z and R bands, we were able to map the torque of the gas and to understand better how the molecular gas is driven towards the nuclear region of these galaxies.

Section [2](#sample) presents the sample and the selection criteria, and Section [3](#methodology) describes the method we used to compute gravity torques in the galaxies. We analyse the data in Sec. [4](#data), and the results are discussed in Sec. [5](#disc). Sec. [6](#conclusion) gathers out conclusions.

+----------+----------------------------------------------------------+-------------+------------------------------------------------------------------------------------+---+
|          | HST                                                      | Legacy DR9  | ALMA                                                                               |   |
+:========:+:=====================:+:===============:+:==============:+:===========:+:======================================:+:===================:+:===================:+:=:+
| Galaxy   | Proposal ID           | |             | | |            | | Proposal ID | Proposal ID                            | |                 | | |                 | |   |
|          |                       | |:-----------:| | |:----------:| |             |                                        | |:---------------:| | |:---------------:| |   |
|          |                       | | Observation | | | Exposition | |             |                                        | | Beam Major Axis | | |      Rest       | |   |
|          |                       | |    Date     | | |  Time (s)  | |             |                                        | |    (arcsec)     | | | Frequency (MHz) | |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 1300 | 15133 (PI: P. Erwin)  | 10/27/2017      | 500            | 2012B-0001  | |                                  |   | |           |       | |         |         |   |
|          |                       |                 |                |             | |:--------------------------------:|   | |:---------:|       | |:-------:|         |   |
|          |                       |                 |                |             | |  2015.1.00925.S (PI: G. Blanc)   |   | | 7.45, 8.6 |       | | 230.538 |         |   |
|          |                       |                 |                |             | |  2018.1.01651.S (PI: A. Leroy)   |   | |   1.99    |       | | 230.538 |         |   |
|          |                       |                 |                |             | | 2019.1.01718.S (PI: S. Longmore) |   | |   0.65    |       | | 345.796 |         |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 1792 | 15654 (PI: J. Lee)    | 05/25/2019      | 830            | 2012B-0001  | 2017.1.00886.L (PI: E. Schinnerer)     | 1.92                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 2903 | 9788 (PI: Ho, L.)     | 03/01/2004      | 120            | 2014B-0404  | |                                    | | |            |      | |         |         |   |
|          |                       |                 |                |             | |:----------------------------------:| | |:----------:|      | |:-------:|         |   |
|          |                       |                 |                |             | | 2017.1.00886.L (PI: E. Schinnerer) | | |    1.99    |      | | 230.538 |         |   |
|          |                       |                 |                |             | |   2018.1.00517.S (PI: K. Onishi)   | | |    0.63    |      | | 230.538 |         |   |
|          |                       |                 |                |             | |  2019.1.01730.S (PI: J. Puschnig)  | | | 4.64, 3.69 |      | | 345.800 |         |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 3059 | 9042 (PI: Smartt, S.) | 08/13/2001      | 160            | –           | 2017.1.00886.L (PI: E. Schinnerer)     | 1.99                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 4303 | 15654 (PI: J. Lee)    | 03/29/2020      | 803            | 2014B-0404  | 2015.1.00956.S (PI: A. Leroy)          | 1.99                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 4321 | 15654 (PI: J. Lee)    | 03/15/2020      | 836            | 2014B-0404  | 2015.1.00956.S (PI: A. Leroy)          | 1.99                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 4536 | 15654 (PI: J. Lee)    | 03/22/2020      | 803            | 2014B-0404  | 2017.1.00886.L (PI: E. Schinnerer)     | 1.99                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 4689 | 15133 (PI: P. Erwin)  | 12/22/2017      | 500            | 2014B-0404  | 2017.1.00886.L (PI: E. Schinnerer)     | 1.99                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 5248 | 15133 (PI: P. Erwin)  | 01/04/2018      | 500            | 2014B-0404  | |                                    | | |      |            | |         |         |   |
|          |                       |                 |                |             | |:----------------------------------:| | |:----:|            | |:-------:|         |   |
|          |                       |                 |                |             | | 2017.1.00886.L (PI: E. Schinnerer) | | | 1.99 |            | | 230.538 |         |   |
|          |                       |                 |                |             | | 2019.1.00876.S (PI: E. Schinnerer) | | | 0.29 |            | | 230.538 |         |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+
| NGC 5921 | 15323 (PI: J. Walsh)  | 09/13/2017      | 738            | –           | 2019.1.01742.S (PI: D. Rosario)        | 0.49                | 230.538             |   |
+----------+-----------------------+-----------------+----------------+-------------+----------------------------------------+---------------------+---------------------+---+

+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| Galaxy   | |               | | Distance (Mpc) | Nuclear Activity | PA ($^{\circ}$) | Bar PA ($^{\circ}$) | Inclination ($^{\circ}$) | |                          | | |                           | |
|          | |:-------------:| |                |                  |                 |                     |                          | |:------------------------:| | |:-------------------------:| |
|          | | Morphological | |                |                  |                 |                     |                          | | Total apparent corrected | | |    Total Stellar Mass     | |
|          | |     Type      | |                |                  |                 |                     |                          | |    B-magnitude (mag)     | | | log($M_{*}/M_{\bigodot}$) | |
+:========:+:=================:+:==============:+:================:+:===============:+:===================:+:========================:+:============================:+:=============================:+
| NGC 1300 | SB(rs)bc          | 14.5           | LINER (AGN)      | 278$^{a}$       | 104$^{{1}}$         | 31.8$^{a}$               | 10.61                        | 10.30$^{{7}}$                 |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 1792 | SA(rs)bc          | 11.3           | HII Region       | 316             | –                   | 63.1                     | 10.18                        | 10.57$^{{8}}$                 |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 2903 | SAB(rs)bc         | 8.57           | HII Region       | 202             | 24$^{{2}}$          | 67.1                     | 8.83                         | 10.31$^{{9}}$                 |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 3059 | SB(rs)bc          | 14.8           | HII Region       | 330             | 39$^{{3}}$          | 21.3                     | 10.63                        | 10.40$^{{8}}$                 |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 4303 | SAB(rs)bc         | 12.2           | Seyfert 2/LINER  | 310             | 2$^{{4}}$           | 18.1                     | 10.02                        | 10.48$^{{7}}$                 |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 4321 | SAB(s)bc          | 15.8           | LINER (AGN)      | 156$^{a}$       | 108$^{{4}}$         | 24                       | 9.83                         | 10.71$^{{10}}$                |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 4536 | SAB(rs)bc         | 14.7           | LINER (AGN)      | 306$^{a}$       | 136$^{{5}}$         | 66$^{a}$                 | 10.27                        | 10.19$^{{10}}$                |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 4689 | SA(rs)bc          | 15.7           | HII Region       | 163             | —                   | 42.5                     | 11.23                        | 10.58$^{{8}}$                 |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 5248 | SAB(rs)bc         | 11.8           | Seyfert/LINER    | 120             | 127$^{{4}}$         | 56.4                     | 10.39                        | 10.30$^{{11}}$                |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+
| NGC 5921 | SB(r)bc           | 17.3           | HII Region       | 137             | 18$^{{6}}$          | 49.5                     | 11.2                         | 10.41$^{{12}}$                |
+----------+-------------------+----------------+------------------+-----------------+---------------------+--------------------------+------------------------------+-------------------------------+

# Sample

![](NGC1300_m0_m1_novo.png)

In order to estimate the gravitational potential in the disk, we needed red images of the galaxies to avoid dust extinction and to avoid biasing by the light of a small number of OB stars with low mass-to-light ratios (M/L). The red images were available with several resolutions and fields of view (FOVs): We used HST images in the F814W filter and Legacy survey DR9 images in the R (for NGC 4303 and NGC 4536 because their Z-band images are saturated at the nucleus) and Z bands. To compute the torques on the molecular gas, we used ALMA data mainly from the Phangs survey (cite: PHANGS) and from the ALMA archive. The data details are displayed in Table [\[obsinfo\]](#obsinfo).

We searched for the data of SABbc, SBbc, and SAbc galaxies with inclinations lower than 65$^{\circ}$ because the computations cannot be performed for edge-on galaxies. We also only selected nearby galaxies (D$<$ 18 Mpc) to have enough spatial resolution, and galaxies with a magnitude in the B-band lower than 12 for a complete sample. Based on the classification in the NASA/IPAC Extragalactic Database (NED[^1]), these criteria led to 43 galaxies. The availability of the data limited the sample to ten galaxies, with the exceptions of the two galaxies that were already studied (NGC 1566 (cite: combes14) and NGC 613 (cite: audibert19)). Another two galaxies have ALMA data, but the FOV was too small for this work : NGC 1255 and NGC 4030, and there were problems with the data of a final two galaxies: NGC 3521 and NGC 5530. When these galaxies were removed, we obtained ten galaxies. Their properties are shown in Table [\[tabelagal\]](#tabelagal). The inclinations of NGC 2903 and NGC 4536 are higher than 65$^{\circ}$. However, given the uncertainties on this parameter, which is about 5$^{\circ}$ at least, we chose to include these galaxies in the sample.

![](ngc1792_m0_m1.png)

![](NGC2903_m0_m1_new.png)

# Method

The goal of this work is to quantify the rate of gas inflow due to gravity torques exerted by a bar (or spirals) on the molecular gas. This work was done at different scales, according to the spatial resolutions and FOVs of the observations.

The gravitational potential is mainly due to stars, and because the old population is more representative of the mass, red or near-infrared images are the best tracers, while the dark matter can be neglected in the central parts of MW-like galaxies (cite: Persic1996). The red images at high resolution are usually from the filter F814W from HST for the central region and from the Legacy survey (at bands Z or R) at large scales to benefit from a wider FOV, but the spatial resolution is lower.

The images were rotated and deprojected according to the PAs and inclination angles given in Table [\[tabelagal\]](#tabelagal). The bulge component was separated for the deprojection, because it was assumed to be spherical; in general, the bulge does not significantly contribute to the mass, because of the late morphological types of the targets. After rotation and deprojection, the images were Fourier transformed to compute the gravitational potential and forces. The M/L was assumed to be constant throughout the disk and bulge. Its precise value was considered not to be important because we computed normalised torques, corresponding to the relative loss of angular momentum per rotation. To take the third dimension of the disk into account, we assumed a stellar exponential disk thickness of $\sim$1/12th of the radial scale length of the galaxies (cite: Garcia-Burillo2005; audibert19). After computing the potential and forces in each pixel, we computed the torques with an emission map of the molecular gas at the same resolution. All maps were resampled to the same number of pixels and pixel sizes.

The amount of data available for both infrared images and molecular gas varies for a given galaxy. NGC 1300 has a considerable volume of data. In this case, we opted to use four ALMA data sets: two data sets were from the program 2015.1.00925.S and were combined in order to form a larger FOV (represented by the yellow square in Fig. [1](#galaxiesimage) of NGC 1300). These data were used in the analysis with a Legacy image with a corresponding FOV. We used Phangs ALMA data associated with HST and Legacy images (green and red squares) and also the ALMA data from the program 2019.1.01718.S, which has a better spatial resolution, associated with the same HST image (cyan square). For NGC 1792, we used Phangs data together with HST (green square in Fig. [1](#galaxiesimage) of NGC 1792) and Legacy images (red square). NGC 2903 also had four data sets: two data sets from the program 2019.1.01730.S, which had the same goal as NGC 1300. They were combined to form a larger FOV and were used together with a Legacy image that was matched to have the same size (yellow square). This galaxy also had data from Phangs that were used together with Legacy and HST data (red and green squares, respectively). We also used high spatial resolution ALMA data (program 2018.1.00517.S) together with HST data represented by the cyan square in Fig. [1](#galaxiesimage) of NGC 2903. For NGC 3059, NGC 4303, NGC 4321, NGC 4536, and NGC 4689, only Phangs ALMA data were used, together with HST and Legacy data (with the exception of NGC 3059, which lacks Legacy images). For NGC 5248, the Phangs data were used together with HST and Legacy images as well; however, ALMA data were also used from the program 2019.1.00876.S (with higher spatial resolution) together with the HST images. Finally, for NGC 5921, we used ALMA data from 2019.1.01742.S program with a high spatial resolution, together with the HST image of this galaxy. This galaxy has Legacy images; because the ALMA data have a small FOV, it would provide the same results as were obtained with HST images with a lower spatial resolution, however. For better results, we used HST data. The summary of all information is shown in Table [\[obsinfo\]](#obsinfo) and Fig. [1](#galaxiesimage).

To prepare the data for the computation of gravitational torques from the infrared images, we first removed the MW bright stars in the FOV. We then rotated the images using the PA of the galaxy (Table [\[tabelagal\]](#tabelagal)) so that its major axis was horizontal. This implied the definition of a common centre. Using the infrared image, we established a centre based on the emission peak of the nuclear source. We also centred the ALMA data cube according either to the emission peak or to the centre of the ring, and we used the velocity field. The two components (infrared images and ALMA data cube) were then re-centred so that they had the same centre. The images were then deprojected by stretching the vertical axis. For the ALMA data, the same rotation and deprojection were applied to the data cube converted into velocities relative to the centre. These processes were performed with scripts in Python and Gildas environments.

# Data analysis

## Gas morphology and kinematics

Fig. [2](#NGC1300_m0_m1)(a) and (b) show the nuclear structure of NGC 1300. The morphology is that of a ring with a radius of about 300 pc (already detected in previous works; see Appendix [7](#revisiongalaxies)) , which is decomposed into two concentric rings in the ALMA mean image. There is clear evidence of a structure that connects the nuclear source to the ring. The nuclear low-resolution image reveals that this ring is connected to the spiral structure. This is better visible in the images with a larger FOV (Fig. [2](#NGC1300_m0_m1)c and d). The ring and spiral obey the same regular rotation. The two spiral arms emerge outside the ring. They first correspond to the leading dust lanes in the bar, and then continue to wind out outside the bar.

Fig. [3](#NGC1792_m0_m1)(a) and (b) show NGC 1792 data in two different FOVs. They show the nuclear region, which is considerably flocculent. The nuclear source appears to be divided into two regions (as seen in the ALMA data). Because of the spatial resolution, however, we cannot conclude this with certainty. This galaxy has a short nuclear bar that might be related to this structure (see Appendix [7](#revisiongalaxies)). The gas clearly rotates in both FOVs. The spiral arms from the galaxy appear to be connected to the nuclear source seen in the nuclear ALMA image. This galaxy is classified as non-barred, but these maps are quite similar to those of the barred counterparts.

The structure of the nuclear region of NGC 2903 (Fig. [4](#NGC2903_m0_m1)) is very flocculent and hard to interpret. However, a nuclear ring can be distinguished in the gas map. According to the literature, this ring has radius of about 600 pc (see Appendix [7](#revisiongalaxies) for more information). This structure is also connected to the spiral arms of the galaxy and follows the orientation of the galaxy bar (clearly visible in panel d). The gas obeys a clear rotation, and, as in NGC 1300, the ring also follows the same rotation pattern as the remaining galaxy disk.

![](NGC3059_m0_m1_newPA_newt.png)

The data from NGC 3059 (Fig. [5](#NGC3059_m0_m1)) do not present much detail because of the spatial resolution; the bar is very thin and strong in this almost face-on galaxy. The nuclear source is connected to the spiral arms in the same direction as the bar. The rotation is also clear in this case. This galaxy was reported to have a weak bar (see Appendix [7](#revisiongalaxies)), but we found that this galaxy has the strongest bar in the sample.

![](ngc4303_m0_m1_newPA_newt.png)

NGC 4303 (Fig. [6](#NGC4303_m0_m1)) presents a nuclear ring at the bar ILR in the centre that is connected to the spiral arms, leading dust lanes along the bar. These in turn are connected to the spiral arms outside the bar. The ring radius is about 310 pc. The spiral arms are very clear and rotate regularly. The spatial resolution did not allow us to see the nuclear bar that was reported in the literature (see Appendix [7](#revisiongalaxies) for more details).

![](NGC4321_m0_m1.png)

The gas morphology of NGC 4321 (Fig. [7](#NGC4321_m0_m1)) is very similar to that of NGC 4303. The spiral arms follow the morphology typical of a barred galaxy. The nuclear ring radius is $\sim$ 500 pc. As in 4303, the spatial resolution was not high enough for us to detect the nuclear bar that was observed in previous studies (see Appendix [7](#revisiongalaxies)).

![](NGC4536_m0_m1_new.png)

NGC 4536 has a very obscured nucleus, with a conspicuous dust lane on the near side, in the north-east. The bar orientation of this galaxy is confused with its major axis because of the high inclination. However, in Fig. [8](#NGC4536_m0_m1), molecular gas images show a clear nuclear bar with a PA $\sim$ 136$^{\circ}$ and a diameter of about 2.1 kpc that was also detected in previous studies (see Appendix [7](#revisiongalaxies)). One gas spiral arm is also connected to the bar in the south-west. The opposite arm in the north-east is better visible in the stellar component.

![](NGC4689_m0_m1.png)

NGC 4689 is another non-barred galaxy. In this case, the difference between this non-barred galaxy and the barred galaxies is clear: The nucleus, which is very flocculent, lacks any clear structure (Fig. [9](#NGC4689_m0_m1)). Some studies reported evidence of a weak bar, but we detected no clear structure in this galaxy (see Appendix [7](#revisiongalaxies)). The radio data show no clear nuclear source either. Moreover, the spiral structure in the molecular gas images is not as clear as in the infrared images.

![](NGC5248_m0_m1_new.png)

NGC 5248 has a very clear spiral structure and a nuclear ring at the centre, with a radius of about 88 pc (Fig. [10](#NGC5248_m0_m1)). It also has an inner pseudo-ring that encircles the bar. This is expected to delineate the ultra-harmonic resonance near the corotation at a radius $\sim$ 500 pc. Then the spiral arms connect to this pseudo-ring outside the bar. We did not detect the possible nuclear bar (see Appendix [7](#revisiongalaxies)). This might be due to the low spatial resolution.

![](NGC5921_m0_m1.png)

Several structures are embedded in galaxy NGC 5921 (Fig. [11](#NGC5921_m0_m1)). The morphology at large scales suggests that an inner ring encircles the bar with a radius $\sim$ 5 kpc. Two spiral arms are connected to this ring/bar (see Fig. [1](#galaxiesimage)). At smaller scales, a nuclear ring with a radius of about 230 pc is visible. Nuclear spiral arms are also connected to this nuclear source.

In summary, all barred galaxies of the sample present a very complex nuclear region. Six galaxies present clear evidence of nuclear rings (N1300, N2903, N4303, N4321, N5248, and N5921). Two objects have a nuclear bar (N4536 and N5921). NGC 4689 alone did not show clear structures in its nucleus. This might be related to the lack of a bar. Although it was classified as a non-barred galaxy, NGC 1792 has a clear structure in its nucleus.

![](qplot_N4303b.png)

+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| Galaxy       | Radius (kpc) | |                 | | Radius (kpc) | Qmax (m=2)  | Radius (kpc) | Qmax (Total) |
|              |              | |:---------------:| |              |             |              |              |
|              |              | |      dL/L       | |              |             |              |              |
|              |              | | in one rotation | |              |             |              |              |
+:============:+:============:+:===================:+:============:+:===========:+:============:+:============:+
| NGC 1300 (a) | |      |     | |        |          | 0.5          | 0.11 B      | 0.234        | 0.061 R      |
|              | |:----:|     | |:------:|          |              |             |              |              |
|              | | 0.33 |     | | 0.025  |          |              |             |              |              |
|              | | 0.53 |     | | -0.063 |          |              |             |              |              |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 1300 (b) | |       |    | |        |          | 0.68         | 0.013 B     | |       |    | |         |  |
|              | |:-----:|    | |:------:|          |              |             | |:-----:|    | |:-------:|  |
|              | | 0.083 |    | | 0.084  |          |              |             | | 0.21  |    | | 0.034 R |  |
|              | |  0.4  |    | | -0.237 |          |              |             | | 0.747 |    | | 0.031 B |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 1300 (c) | —            | —                   | 2.66         | 0.143 B     | 3.04         | 0.359 B      |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 1300 (d) | —            | —                   | 3.55         | 0.222 B     | 3.55         | 0.567 B      |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 1792 (a) | |       |    | |        |          | |       |    | |         | | |       |    | |         |  |
|              | |:-----:|    | |:------:|          | |:-----:|    | |:-------:| | |:-----:|    | |:-------:|  |
|              | | 0.09  |    | | -0.145 |          | | 0.276 |    | | 0.265 S | | | 0.276 |    | | 0.255 S |  |
|              | | 0.208 |    | | 0.148  |          | | 0.473 |    | | 0.208 S | | | 0.473 |    | | 0.21 S  |  |
|              |              |                     |              |             | | 0.83  |    | | 0.10 S  |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 1792 (b) | |      |     | |        |          | |      |     | |         | | |      |     | |        |   |
|              | |:----:|     | |:------:|          | |:----:|     | |:-------:| | |:----:|     | |:------:|   |
|              | | 0.2  |     | | -0.225 |          | | 0.37 |     | | 0.026 S | | | 1.07 |     | | 0.25 S |   |
|              | | 1.07 |     | | 0.261  |          | | 1.56 |     | | 0.042 S | | | 1.96 |     | | 0.24 S |   |
|              |              |                     |              |             | | 2.84 |     | | 0.20 S |   |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 2903 (a) | |       |    | |        |          | |      |     | |         | | |       |    | |         |  |
|              | |:-----:|    | |:------:|          | |:----:|     | |:-------:| | |:-----:|    | |:-------:|  |
|              | | 0.387 |    | | 0.444  |          | | 0.13 |     | | 0.135 R | | | 0.324 |    | | 0.177 R |  |
|              | | 0.596 |    | | -0.022 |          | | 0.53 |     | | 0.024 S | | | 0.634 |    | | 0.141 S |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 2903 (b) | |       |    | |        |          | 0.12         | 0.116 S     | |       |    | |         |  |
|              | |:-----:|    | |:------:|          |              |             | |:-----:|    | |:-------:|  |
|              | | 0.025 |    | | -0.892 |          |              |             | | 0.093 |    | | 0.470 S |  |
|              | | 0.314 |    | | 0.578  |          |              |             | | 0.263 |    | | 0.167 S |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 2903 (c) | |       |    | |        |          | |       |    | |         | | |      |     | |         |  |
|              | |:-----:|    | |:------:|          | |:-----:|    | |:-------:| | |:----:|     | |:-------:|  |
|              | | 0.359 |    | | 0.336  |          | | 0.424 |    | | 0.051 R | | | 0.53 |     | | 0.091 R |  |
|              | | 1.62  |    | | -0.077 |          | | 1.71  |    | | 0.009 S | | | 1.55 |     | | 0.059 S |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 2903 (d) | |      |     | |      |            | |      |     | |         | | |      |     | |         |  |
|              | |:----:|     | |:----:|            | |:----:|     | |:-------:| | |:----:|     | |:-------:|  |
|              | | 1.32 |     | | 0.86 |            | | 0.42 |     | | 1.11 S  | | | 0.42 |     | | 0.505 S |  |
|              | | 2.44 |     | | -1.  |            | | 2.32 |     | | 0.057 B | | | 2.32 |     | | 0.257 B |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 3059     | |       |    | |       |           | 0.26         | 0.33 B      | |      |     | |         |  |
|              | |:-----:|    | |:-----:|           |              |             | |:----:|     | |:-------:|  |
|              | | 0.435 |    | | 0.592 |           |              |             | | 0.24 |     | | 0.928 B |  |
|              | | 0.932 |    | |  -1.  |           |              |             | | 0.74 |     | | 0.53 B  |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4303 (a) | |       |    | |        |          | |      |     | |         | | |      |     | |         |  |
|              | |:-----:|    | |:------:|          | |:----:|     | |:-------:| | |:----:|     | |:-------:|  |
|              | | 0.037 |    | | 0.134  |          | | 0.09 |     | | 0.033 R | | | 0.15 |     | | 0.091 R |  |
|              | | 0.96  |    | | -0.835 |          | | 1.72 |     | |  0.1 B  | | | 1.69 |     | | 0.217 B |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4303 (b) | |      |     | |      |            | 1.92         | 0.18 B      | 1.93         | 0.46 B       |
|              | |:----:|     | |:----:|            |              |             |              |              |
|              | | 0.26 |     | | 0.77 |            |              |             |              |              |
|              | | 0.67 |     | | -1.  |            |              |             |              |              |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4321 (a) | |      |     | |        |          | |       |    | |         | | |      |     | |         |  |
|              | |:----:|     | |:------:|          | |:-----:|    | |:-------:| | |:----:|     | |:-------:|  |
|              | | 0.57 |     | | 0.168  |          | | 0.303 |    | | 0.086 R | | | 0.31 |     | | 0.267 R |  |
|              | | 1.19 |     | | -0.273 |          | | 0.605 |    | | 0.084 B | | | 0.67 |     | | 0.18 B  |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4321 (b) | |      |     | |       |           | |      |     | |         | | |      |     | |         |  |
|              | |:----:|     | |:-----:|           | |:----:|     | |:-------:| | |:----:|     | |:-------:|  |
|              | | 0.61 |     | | 0.24  |           | | 0.65 |     | | 0.103 B | | | 0.68 |     | | 0.194 B |  |
|              | | 1.12 |     | | -0.35 |           | | 3.46 |     | | 0.054 B | | | 4.05 |     | | 0.08 B  |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4536 (a) | |      |     | |        |          | 0.252        | 0.201 B     | 1.07         | 0.118 B      |
|              | |:----:|     | |:------:|          |              |             |              |              |
|              | | 0.23 |     | |  0.03  |          |              |             |              |              |
|              | | 1.29 |     | | -0.874 |          |              |             |              |              |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4536 (b) | |      |     | |       |           | 2.49         | 0.145 B     | 2.56         | 0.325 B      |
|              | |:----:|     | |:-----:|           |              |             |              |              |
|              | | 1.21 |     | |  -1.  |           |              |             |              |              |
|              | | 2.61 |     | | 0.459 |           |              |             |              |              |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4689 (a) | |      |     | |        |          | 0.204        | 0.049 R     | 0.63         | 0.150 S      |
|              | |:----:|     | |:------:|          |              |             |              |              |
|              | | 0.08 |     | |  0.47  |          |              |             |              |              |
|              | | 0.25 |     | | -0.148 |          |              |             |              |              |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 4689 (b) | |      |     | |        |          | |       |    | |         | | |       |    | |         |  |
|              | |:----:|     | |:------:|          | |:-----:|    | |:-------:| | |:-----:|    | |:-------:|  |
|              | | 0.1  |     | |  0.5   |          | | 0.298 |    | | 0.039 R | | | 0.556 |    | | 0.135 R |  |
|              | | 1.04 |     | | -0.112 |          | | 1.33  |    | | 0.02 S  | | | 1.75  |    | | 0.66 S  |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 5248 (a) | |       |    | |        |          | 0.124        | 0.071 R     | |       |    | |         |  |
|              | |:-----:|    | |:------:|          |              |             | |:-----:|    | |:-------:|  |
|              | | 0.369 |    | | -0.264 |          |              |             | | 0.17  |    | | 0.325 R |  |
|              | | 0.62  |    | |  0.04  |          |              |             | | 0.465 |    | | 0.204 B |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 5248 (b) | |       |    | |       |           | 0.11         | 0.077 R     | |       |    | |         |  |
|              | |:-----:|    | |:-----:|           |              |             | |:-----:|    | |:-------:|  |
|              | | 0.03  |    | |  -1.  |           |              |             | | 0.164 |    | | 0.325 B |  |
|              | | 0.193 |    | | 0.791 |           |              |             | | 0.41  |    | | 0.208 B |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 5248 (c) | |      |     | |        |          | 0.113        | 0.071 R     | |       |    | |         |  |
|              | |:----:|     | |:------:|          |              |             | |:-----:|    | |:-------:|  |
|              | | 1.87 |     | | -0.681 |          |              |             | | 0.155 |    | | 0.325 R |  |
|              | | 3.08 |     | | 0.322  |          |              |             | | 0.423 |    | | 0.204 B |  |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+
| NGC 5921     | |       |    | |        |          | 0.13         | 0.090 B     | 0.13         | 0.18 B       |
|              | |:-----:|    | |:------:|          |              |             |              |              |
|              | | 0.212 |    | |  0.39  |          |              |             |              |              |
|              | | 0.511 |    | | -0.701 |          |              |             |              |              |
+--------------+--------------+---------------------+--------------+-------------+--------------+--------------+

\
*Notes.* The letters B, S and R are indication for Bars, Spirals and Rings. The corresponding set of observations for each galaxy is indicated following the same pattern as in Fig. [2](#NGC1300_m0_m1) to [11](#NGC5921_m0_m1).

![](torques_NGC1300_newpai_new_newgastor_vrot.png)

![](TORQUES_NGC1792.png)

![](TORQUES_NGC2903_new2.png)

![](torq_NGC3059_newPA_newt.png)

![](torq_N4303_newPA_newt.png)

![](TORQUES_NGC4321_newpa_newt.png)

![](torq_N4536_newpai_new.png)

![](TORQUES_NGC4689.png)

![](torques_NGC5248_new.png)

![](torq_NGC5248_LEGACY.png)

![](torq_NGC5921.png)

## Gas torque analysis

The computation of the gravity potential from the deprojected red images yields the estimate of the bar and spiral strength as a function of radius. The nature of the pattern (bar or spiral) is indicated by the phase and its variation with radius of the different Fourier components into which the potential $\Phi(R,\theta)$ is decomposed, $$\Phi(R,\theta) = \Phi_0(R) + \sum_m \Phi_m(R) \cos (m \theta - \phi_m(R)).$$ The strength of the $m$-Fourier component, $Q_m(R)$, is defined as $Q_m(R)=m \Phi_m / R | F_0(R) |$, that is, by the ratio between tangential and radial forces (cite: Combes1981). The strength of the total non-axisymmetric perturbation $Q_T(R)$ is defined similarly, with the maximum amplitude of the tangential force $F_T^{max}(R)$. Their radial distributions and the radial phase variations are displayed for a typical galaxy in Fig. [12](#fig:qplot). We determine in Table [\[tab:qplot\]](#tab:qplot) the radii and maximum amplitudes of $Q_T(R)$ over the disk for all galaxies.

For each galaxy, the forces per unit mass ($F_x$ and $F_y$) at each pixel were obtained by deriving the potential. The torques per unit mass $t(x,y)$ were then computed by $$t(x,y) = x~F_y -y~F_x.$$ The sign of the torque was determined relative to the sense of rotation in the plane of the galaxy. The net effect on the gas at each radius is then the product of the torque by the gas density $\Sigma$. This quantity, $t(x,y)\times
  \Sigma(x,y)$, is shown in the left panels of Figs. [13](#torquemaps_N1300) – [23](#torquemaps_N5921).

The torque weighted by the gas density $\Sigma(x,y)$ was then averaged over azimuth, $$t(R) = \frac{\int_\theta \Sigma(x,y)\times(x~F_y -y~F_x)}{\int_\theta \Sigma(x,y)}.$$ The quantity $t(R)$ represents the time derivative of the specific angular momentum $L=\Omega R^2$ of the gas averaged azimuthally (cite: Garcia-Burillo2005). The efficiency of the gas flow was then estimated through normalising $t(R)$ at each radius by the angular momentum $L$, divided by the rotation period $T= 2\pi/\Omega$, as shown in the right panels of Figs. [13](#torquemaps_N1300) – [23](#torquemaps_N5921). With this normalisation, the computations are independent of the constant M/L ratios used.

These figures show some general features. Negative torques, implying gas infall between corotation and ILR, as expected, are indeed observed in several barred galaxies when the FOV is sufficient and includes enough of the bar region. This is the case for NGC 1300 in Figs. [13](#torquemaps_N1300) (c) and (d), and also NGC 4303, NGC 4321, NGC 4536, NGC 5248, and NGC 5921. When only the nuclear ring is included in the FOV, the situation is more complex, and the torques do not show a single coherent behaviour, as for NGC 1300 in Figs. [13](#torquemaps_N1300) (a) and (b). The torques are not significant in non-barred flocculent galaxies, as for NGC 1792 in Fig. [14](#torquemaps_N1792) and NGC 4689 in Fig. [20](#torquemaps_N4689).

NGC 2903 is a special case (Fig. [15](#torquemaps_N2903)). Although barred, with a coherent spiral structure, the torque values are more chaotic. This is due to several factors. The main factor is the patchiness of the CO emission, which prevents a spatial continuity in the torque computation. We note that the torques we computed from the two different fields of view are sometimes different. The reason is the different gas maps that were obtained with different configurations of the ALMA interferometer, with different spatial resolutions. Another reason is that the red image of NGC 2903 is quite dusty, with conspicuous dust lanes. This leads to an irregular potential estimation that differs from the real potential.

NGC 3059 has a very thin bar, almost on the minor axis. It is therefore even longer when deprojected, although the inclination is quite low. The torque is positive from 0.3 to 0.6 kpc, and then negative from 0.6 to 1 kpc (Fig [16](#torquemaps_N3059)). This would mean that gas is driven to a ring at a radius of 0.6 kpc. However, in this case, the gas orbits are expected to be very elongated, and positive and negative torques might partially cancel out over the orbits. The torques are negative at radii lower than 0.3 kpc, which explains the gas concentration inside a radius of 3 arcsec, that is, 220 pc.

The quantification of the torques for each galaxy and each FOV is displayed in Table [\[tab:qplot\]](#tab:qplot). The relative loss and gain of angular momentum per rotation is higher than one in absolute value only for NGC 1300, and it is not indicated in this table. It does not satisfy the main hypothesis underlying the azimuthal average of the torque, that the gas has time to remain in its radial range during one rotation. In this case, we plot only the torque map, normalized with physical quantities, computed with the rotation curve of the galaxy. The latter was derived from the potential itself, assuming a constant mass-to-light ratio, and normalised to the CO, HI, and optical observations (see Fig. [24](#fig:Vrot-1300)). In this figure, the rotation curve from the potential model is compared to the observed curves from (cite: Lang20), (cite: england89), and (cite: Lindblad97).

![](vrot_plusmodel_n1300.png)

# Discussion

We studied ten MW analogues, and only two galaxies of this sample are considered non-barred. This sample is homogeneous when we consider that galactic bars may be in a 1-2 Gyr transient phase (cite: Bournaud2002) and when, as previous studies argued (see Appendix [7](#revisiongalaxies)), the AGN activity is weak in these nuclei (which is also an intermittent characteristic, with a duty cycle of 40 Myr). The comparison of gas flow processes within this matched sample can help us to further understand the evolution of these types of galaxies, including our own. Although this sample is small because available data are limited, it is representative because it was selected based on objective criteria. The results are consistent for this sample.

It is important to discuss the limitations of this work. One limitation is the spatial resolution of the data. One of the most frequently encountered questions in astronomy concerns the feeding and feedback processes in galactic nuclei. In order to study this matter comprehensively, high spatial resolution data are fundamental, because these processes occur in a very small region (10 – 100 pc). The spatial resolution of the data we analysed here is insufficient to compute the gas dynamics at these scales in detail. As a consequence, we disregarded results below 1 arcsec (corresponding to 66 pc at an average distance of 13.7 Mpc) in general. The torque maps and values in this central region are uncertain, not only because of the spatial resolution, but sometimes also due to phenomena associated with possible AGN, which may generate ambiguous results that can only be differentiated with data with a higher spatial resolution. These are rare. Not many galaxies are observed with the necessary instrumental configuration for an analysis like this. The spatial resolution we used is considered moderate, and can only provide a general idea of what occurs in these galaxies at scales of 100 pc – 1 kpc.

The assumption that dark matter has no effect is a good approach because these galaxies are massive enough (see the stellar masses in Table [\[tabelagal\]](#tabelagal)). In massive disk-dominated galaxies like this, dark matter is not dominant in the central region and shows a cored distribution (cite: deBlok2008). In addition, we studied features in the nuclear regions of the objects, where baryons dominate the gravitational potential.

The torque maps were computed in each pixel, weighted by the gas density. To derive the global impact on the gas inflow/outflow, we averaged on the azimuth at each radius, although the orbits of the gas, when deprojected, are not circular. We then quantified the relative angular momentum variation in one circular rotation. Although gas orbits might be elliptical in these galaxies, this average gives the correct order of magnitude over many gas streamlines at a given radius. We did not considered this average when the relative loss of angular momentum was higher than one in absolute value (e.g. NGC 1300).

In the case of NGC 1300, we have two data sets (c and d), which are related to the large FOVs that provided noisier results, but also large variations in angular momentum. As a consequence, we could not take the self-normalised torque curves into account and had to use the velocity rotation curve (Fig. [24](#fig:Vrot-1300)) in order to normalise the results. Some parts of the CO maps of these data sets show no emission, and the S/N in other parts is too low, which causes the torque curves to be noisy. The same was observed in other galaxies, but with fewer fluctuations.

Another limitation of this work is the determination of the PA and the galaxy inclination. This relies on the assumption that the outer optical isophotes are circular. These determinations can be biased in barred galaxies, where the PA of the bar can easily be misinterpreted to be aligned with the galaxy major axis, causing systematic errors. The inclination angle has the same problem because these galaxies are not axisymmetric disks. The results strongly depend on these values because the deprojection is important for the computation of the torques.

We did not detect any dynamical influence of AGN feedback in these galaxies. One of the reasons, as mentioned, is the low spatial resolution and low AGN activity. We did not detect radio jets either. An optical data analysis (with a higher spatial resolution within the 500 pc scale) would be interesting in this case, in order to compare the ionized and molecular gas behaviour, and also to determine whether the AGN affects the surrounding ionized gas.

We provided the characteristics of gas flows in MW twins at 100 pc- 1 kpc scales. We consider this study as preliminary results that are to be pursued in the future with data that have a better spatial resolution, and perhaps with multiwavelength data. With these data, it will be possible to connect what we observe at these scales with the smaller scales and to quantify the AGN fueling mechanisms and/or the feedback on the gas flow in these galaxies. In ringed galaxies, the infall of gas is expected to be contained within the ring, but the gas can also be driven towards the nucleus through nuclear spirals/bars.

# Conclusions

We have quantified the gravity torques and their impact on the gas flows in a sample of eight MW analogues with two non-barred counterparts. The sample is homogeneous in mass, morphological type, and fundamental physical characteristics. The bar and spiral strengths varied, as did the AGN types, because they are considered variable during the lifetimes of typical spiral galaxies. This allowed us to compare the effect of non-axisymmetric features on the gas inflows and outflows. By using HST and Legacy images of the stellar emission and ALMA data of the molecular gas emission, we were able to compute the molecular gas torques in this sample at scales of hundreds of parsecs to kiloparsecs.

The galaxy sample presented a diversification of structures, such as rings (NGC 1300, NGC 2903, NGC 4303, NCG 4321, NGC 5248, and NGC 5921) and spiral arms connected to them. The sample also contains flocculent galaxies (the best example is NGC 4689, without any recognisable structure).

Our multi-scale study showed that torques are not significant in the inner resonant rings, even when they are not circular. They are not significant for flocculent galaxies either. For barred galaxies, torques are negative between the corotation and the inner Lindblad resonance, as expected. The torques computed on the H$\alpha$ emitting gas are compatible with those on the molecular gas, but they are noisier and more patchy.

The relative loss of angular momentum can be quite high and may reach nearly 100% in one rotation for extreme cases. When the bar is very strong and thin, the gas orbits are very elongated, which prevents the formation of a ring. The gas is then effectively driven to the nucleus.

We studied intermediate scales between 100 pc and 1 kpc scales. The gas inflow revealed by the torques produces starbursts in the centre of barred galaxies. Future studies at higher spatial resolution are needed to follow-up the AGN feeding into the nucleus.

# Acknowledgements

PS acknowledges Fundação de Amparo à Pesquisa do Estado de São Paulo (FAPESP) post-doctoral fellowships 2020/13239-5 and 2022/14382-1. The Legacy Surveys consist of three individual and complementary projects: the Dark Energy Camera Legacy Survey (DECaLS; Proposal ID #2014B-0404; PIs: David Schlegel and Arjun Dey), the Beijing-Arizona Sky Survey (BASS; NOAO Prop. ID #2015A-0801; PIs: Zhou Xu and Xiaohui Fan), and the Mayall z-band Legacy Survey (MzLS; Prop. ID \# 2016A-0453; PI: Arjun Dey). DECaLS, BASS and MzLS together include data obtained, respectively, at the Blanco telescope, Cerro Tololo Inter-American Observatory, NSF’s NOIRLab; the Bok telescope, Steward Observatory, University of Arizona; and the Mayall telescope, Kitt Peak National Observatory, NOIRLab. Pipeline processing and analyses of the data were supported by NOIRLab and the Lawrence Berkeley National Laboratory (LBNL). The Legacy Surveys project is honored to be permitted to conduct astronomical research on Iolkam Du’ag (Kitt Peak), a mountain with particular significance to the Tohono O’odham Nation. The Digitized Sky Surveys were produced at the Space Telescope Science Institute under U.S. Government grant NAG W-2166. The images of these surveys are based on photographic data obtained using the Oschin Schmidt Telescope on Palomar Mountain and the UK Schmidt Telescope. The plates were processed into the present compressed digital form with the permission of these institutions. This research is based on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with program(s) 15133, 15654, 9788, 9042, 15323. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00925.S, ADS/JAO.ALMA#2015.1.00956.S, ADS/JAO.ALMA#2017.1.00886.L, ADS/JAO.ALMA#2018.1.00517.S, ADS/JAO.ALMA#2018.1.01651.S, ADS/JAO.ALMA#2019.1.01718.S, ADS/JAO.ALMA#2019.1.01730.S, ADS/JAO.ALMA#2019.1.00876.S, and ADS/JAO.ALMA#2019.1.01742.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work was supported by the Programme National Cosmology et Galaxies (PNCG) of CNRS/INSU with INP and IN2P3, co-funded by CEA and CNES.

147 natexlab

(ref: alonsoherrero01) Alonso-Herrero, A., Ryder, S. D., & Knapen, J. H. 2001, MNRAS, 322, 757

(ref: Argyle90) Argyle, R. W. & Eldridge, P. 1990, MNRAS, 243, 504

(ref: arsenault89) Arsenault, R. 1989, A&A, 217, 66

(ref: arsenault88) Arsenault, R., Boulesteix, J., Georgelin, Y., & Roy, J. R. 1988, A&A, 200, 29

(ref: atkinson05) Atkinson, J. W., Collett, J. L., Marconi, A., et al. 2005, MNRAS, 359, 504

(ref: audibert19) Audibert, A., Combes, F., Garcı́a-Burillo, S., et al. 2019, A&A, 632, A33

(ref: beck02) Beck, R., Shoutenkov, V., Ehle, M., et al. 2002, A&A, 391, 83

(ref: Berentzen2007) Berentzen, I., Shlosman, I., Martinez-Valpuesta, I., & Heller, C. H. 2007, ApJ, 666, 189

(ref: Berrier13) Berrier, J. C., Davis, B. L., Kennefick, D., et al. 2013, ApJ, 769, 132

(ref: Bi2022) Bi, D., Shlosman, I., & Romano-Dı́az, E. 2022, ApJ, 934, 52

(ref: bonatto89) Bonatto, C., Bica, E., & Alloin, D. 1989, A&A, 226, 23

(ref: bottema90) Bottema, R. 1990, A&A, 233, 372

(ref: Bournaud2002) Bournaud, F. & Combes, F. 2002, A&A, 392, 83

(ref: burtscher21) Burtscher, L., Davies, R. I., Shimizu, T. T., et al. 2021, A&A, 654, A132

(ref: Buta1996) Buta, R. & Combes, F. 1996, , 17, 95

(ref: buta93) Buta, R. & Crocker, D. A. 1993, AJ, 105, 1344

(ref: Canzian93) Canzian, B. 1993, ApJ, 414, 487

(ref: castillo-morales07) Castillo-Morales, A., Jiménez-Vicente, J., Mediavilla, E., & Battaner, E. 2007, MNRAS, 380, 489

(ref: casuso90) Casuso, E., Beckman, J. E., & Cepa, J. 1990, Ap&SS, 170, 275

(ref: Chiang24) Chiang, I.-D., Sandstrom, K. M., Chastenet, J., et al. 2024, ApJ, 964, 18

(ref: colina99) Colina, L. & Arribas, S. 1999, ApJ, 514, 637

(ref: Colina97b) Colina, L., Garcı́a Vargas, M. L., Mas-Hesse, J. M., Alberdi, A., & Krabbe, A. 1997, ApJL, 484, L41

(ref: colina02) Colina, L., Gonzalez Delgado, R., Mas-Hesse, J. M., & Leitherer, C. 2002, ApJ, 579, 545

(ref: Colina2000) Colina, L. & Wada, K. 2000, ApJ, 529, 845

(ref: combes14) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2014, A&A, 565, A97

(ref: Combes1981) Combes, F. & Sanders, R. H. 1981, A&A, 96, 164

(ref: comeron10) Comerón, S., Knapen, J. H., Beckman, J. E., et al. 2010, MNRAS, 402, 2462

(ref: comeron14) Comerón, S., Salo, H., Laurikainen, E., et al. 2014, A&A, 562, A121

(ref: constantin15) Constantin, A., Shields, J. C., Ho, L. C., et al. 2015, ApJ, 814, 149

(ref: dahlem92) Dahlem, M. 1992, A&A, 264, 483

(ref: dahlem94) Dahlem, M., Bomans, D. J., & Will, J.-M. 1994, ApJ, 432, 590

(ref: das03) Das, M., Teuben, P. J., Vogel, S. N., et al. 2003, ApJ, 582, 190

(ref: Dasyra2015) Dasyra, K. M., Bostrom, A. C., Combes, F., & Vlahakis, N. 2015, ApJ, 815, 34

(ref: davies97) Davies, R. I., Sugai, H., & Ward, M. J. 1997, MNRAS, 291, 314

(ref: davis19) Davis, B. L., Graham, A. W., & Combes, F. 2019, ApJ, 877, 64

(ref: deBlok2008) de Blok, W. J. G., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2648

(ref: RC3) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, Herold G., J., et al. 1991, Third Reference Catalogue of Bright Galaxies

(ref: diaz-garcia21) Dı́az-Garcı́a, S., Lisenfeld, U., Pérez, I., et al. 2021, A&A, 654, A135

(ref: dutil99) Dutil, Y. & Roy, J.-R. 1999, ApJ, 516, 62

(ref: elmegreen92) Elmegreen, B. G., Elmegreen, D. M., & Montenegro, L. 1992, ApJS, 79, 37

(ref: elmegreen97) Elmegreen, D. M., Chromey, F. R., Santos, M., & Marshall, D. 1997, AJ, 114, 1850

(ref: elmegreen96) Elmegreen, D. M., Elmegreen, B. G., Chromey, F. R., & Hasselbacher, D. A. 1996, ApJ, 469, 131

(ref: england89) England, M. N. 1989, ApJ, 344, 669

(ref: Englmaier2004) Englmaier, P. & Shlosman, I. 2004, ApJL, 617, L115

(ref: erwin04) Erwin, P. 2004, A&A, 415, 941

(ref: Eskridge02) Eskridge, P. B., Frogel, J. A., Pogge, R. W., et al. 2002, ApJS, 143, 73

(ref: fathi09) Fathi, K., Beckman, J. E., Piñol-Ferrer, N., et al. 2009, ApJ, 704, 1657

(ref: Fiore2017) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: font14) Font, J., Beckman, J. E., Zaragoza-Cardiel, J., et al. 2014, MNRAS, 444, L85

(ref: fujimoto20) Fujimoto, Y., Maeda, F., Habe, A., & Ohta, K. 2020, MNRAS, 494, 2131

(ref: gadotti20) Gadotti, D. A., Bittner, A., Falcón-Barroso, J., et al. 2020, A&A, 643, A14

(ref: gadotti19) Gadotti, D. A., Sánchez-Blázquez, P., Falcón-Barroso, J., et al. 2019, MNRAS, 482, 506

(ref: Garcia-Burillo2012) Garcı́a-Burillo, S. & Combes, F. 2012, in Journal of Physics Conference Series, Vol. 372, Journal of Physics Conference Series, 012050

(ref: Garcia-Burillo2005) Garcı́a-Burillo, S., Combes, F., Schinnerer, E., Boone, F., & Hunt, L. K. 2005, A&A, 441, 1011

(ref: Garcia-Burillo2014) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: garciaburillo98) Garcia-Burillo, S., Sempere, M. J., Combes, F., & Neri, R. 1998, A&A, 333, 864

(ref: Garrison74) Garrison, R. F. & Walborn, N. R. 1974, , 68, 117

(ref: gonzales09) González-Martı́n, O., Masegosa, J., Márquez, I., Guainazzi, M., & Jiménez-Bailón, E. 2009, A&A, 506, 1107

(ref: Goulding09) Goulding, A. D. & Alexander, D. M. 2009, Monthly Notices of the Royal Astronomical Society, 398, 1165

(ref: goulding10) Goulding, A. D., Alexander, D. M., Lehmer, B. D., & Mullaney, J. R. 2010, MNRAS, 406, 597

(ref: graham19) Graham, A. W., Soria, R., & Davis, B. L. 2019, MNRAS, 484, 814

(ref: haan09) Haan, S., Schinnerer, E., Emsellem, E., et al. 2009, ApJ, 692, 1623

(ref: Heckman2014) Heckman, T. M. & Best, P. N. 2014, ARA&A, 52, 589

(ref: hernandez05) Hernandez, O., Carignan, C., Amram, P., Chemin, L., & Daigle, O. 2005, MNRAS, 360, 1201

(ref: ho97) Ho, L. C., Filippenko, A. V., & Sargent, W. L. W. 1997, ApJS, 112, 315

(ref: hoyer) Hoyer, N., Arcodia, R., Bonoli, S., et al. 2024, A&A, 682, A36

(ref: hughes05) Hughes, M. A., Axon, D., Atkinson, J., et al. 2005, AJ, 130, 73

(ref: jackson91) Jackson, J. M., Eckart, A., Cameron, M., et al. 1991, ApJ, 375, 105

(ref: Jackson89) Jackson, J. M., Snell, R. L., Ho, P. T. P., & Barrett, A. H. 1989, ApJ, 337, 680

(ref: jang14) Jang, I., Gliozzi, M., Hughes, C., & Titarchuk, L. 2014, MNRAS, 443, 72

(ref: jimenez03) Jiménez-Bailón, E., Santos-Lleó, M., Mas-Hesse, J. M., et al. 2003, ApJ, 593, 127

(ref: jimenezesvicente07) Jiménez-Vicente, J., Castillo-Morales, A., Mediavilla, E., & Battaner, E. 2007, MNRAS, 382, L16

(ref: jogee05) Jogee, S., Scoville, N., & Kenney, J. D. P. 2005, ApJ, 630, 837

(ref: jogee02) Jogee, S., Shlosman, I., Laine, S., et al. 2002, ApJ, 575, 156

(ref: jungwiert97) Jungwiert, B., Combes, F., & Axon, D. J. 1997, A&AS, 125, 479

(ref: keel83) Keel, W. C. 1983, ApJS, 52, 229

(ref: knapen95b) Knapen, J. H., Beckman, J. E., Heller, C. H., Shlosman, I., & de Jong, R. S. 1995a, ApJ, 454, 623

(ref: knapen95a) Knapen, J. H., Beckman, J. E., Shlosman, I., et al. 1995b, ApJL, 443, L73

(ref: Knapen02) Knapen, J. H., Pérez-Ramı́rez, D., & Laine, S. 2002, MNRAS, 337, 808

(ref: knapen2000) Knapen, J. H., Shlosman, I., Heller, C. H., et al. 2000, ApJ, 528, 219

(ref: Kormendy2013) Kormendy, J. & Ho, L. C. 2013, ARA&A, 51, 511

(ref: Laine2002) Laine, S., Shlosman, I., Knapen, J. H., & Peletier, R. F. 2002, ApJ, 567, 97

(ref: Lang20) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: leitherer02) Leitherer, C., Li, I. H., Calzetti, D., & Heckman, T. M. 2002, ApJS, 140, 303

(ref: leon08) Leon, S., Jeyakumar, S., Pérez-Ramı́rez, D., et al. 2008, A&A, 491, 703

(ref: PHANGS) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43

(ref: Lin1987) Lin, D. N. C. & Pringle, J. E. 1987, MNRAS, 225, 607

(ref: lindblad96) Lindblad, P. A. B. & Kristen, H. 1996, A&A, 313, 733

(ref: Lindblad97) Lindblad, P. A. B., Kristen, H., Joersaeter, S., & Hoegbom, J. 1997, A&A, 317, 36

(ref: maeda20) Maeda, F., Ohta, K., Fujimoto, Y., & Habe, A. 2020, MNRAS, 493, 5045

(ref: maeda18) Maeda, F., Ohta, K., Fujimoto, Y., Habe, A., & Baba, J. 2018, PASJ, 70, 37

(ref: hyperleda) Makarov, D., Prugniel, P., Terekhova, N., Courtois, H., & Vauglin, I. 2014, A&A, 570, A13

(ref: maoz01) Maoz, D., Barth, A. J., Ho, L. C., Sternberg, A., & Filippenko, A. V. 2001, AJ, 121, 3048

(ref: martin97) Martin, P. & Friedli, D. 1997, A&A, 326, 449

(ref: martinez-garcia12) Martı́nez-Garcı́a, E. E. 2012, ApJ, 744, 92

(ref: martini03) Martini, P., Regan, M. W., Mulchaey, J. S., & Pogge, R. W. 2003, ApJS, 146, 353

(ref: matsuoka12) Matsuoka, Y., Yuan, F.-T., Takeuchi, Y., & Yanagisawa, K. 2012, PASJ, 64, 44

(ref: mazzalay14) Mazzalay, X., Maciejewski, W., Erwin, P., et al. 2014, MNRAS, 438, 2036

(ref: mazzalay13) Mazzalay, X., Saglia, R. P., Erwin, P., et al. 2013, MNRAS, 428, 2389

(ref: mazzuca08) Mazzuca, L. M., Knapen, J. H., Veilleux, S., & Regan, M. W. 2008, ApJS, 174, 337

(ref: mazzuca11) Mazzuca, L. M., Swaters, R. A., Knapen, J. H., & Veilleux, S. 2011, ApJ, 739, 104

(ref: mcalpine11) McAlpine, W., Satyapal, S., Gliozzi, M., et al. 2011, ApJ, 728, 25

(ref: menezes22) Menezes, R. B., Steiner, J. E., Ricci, T. V., & da Silva, P. 2022, MNRAS, 513, 5935

(ref: murugeshan20) Murugeshan, C., Kilborn, V., Jarrett, T., et al. 2020, MNRAS, 496, 2516

(ref: neumann23) Neumann, L., Gallagher, M. J., Bigiel, F., et al. 2023, MNRAS, 521, 3348

(ref: Pereira-santaella10) Pereira-Santaella, M., Diamond-Stanic, A. M., Alonso-Herrero, A., & Rieke, G. H. 2010, ApJ, 725, 2270

(ref: perez-ramirez10) Pérez-Ramı́rez, D., Caballero-Garcı́a, M. D., Ebrero, J., & Leon, S. 2010, A&A, 522, A53

(ref: perezramirez2000) Pérez-Ramı́rez, D., Knapen, J. H., Peletier, R. F., et al. 2000, MNRAS, 317, 234

(ref: Persic1996) Persic, M., Salucci, P., & Stel, F. 1996, MNRAS, 281, 27

(ref: pierce86) Pierce, M. J. 1986, AJ, 92, 285

(ref: planesas97) Planesas, P., Colina, L., & Perez-Olea, D. 1997, A&A, 325, 81

(ref: popping10) Popping, G., Pérez, I., & Zurita, A. 2010, A&A, 521, A8

(ref: regan99) Regan, M. W., Sheth, K., & Vogel, S. N. 1999, ApJ, 526, 97

(ref: riffel16) Riffel, R. A., Colina, L., Storchi-Bergmann, T., et al. 2016, MNRAS, 461, 4192

(ref: rosadobelza20) Rosado-Belza, D., Falcón-Barroso, J., Knapen, J. H., et al. 2020, A&A, 644, A116

(ref: saikia94) Saikia, D. J., Pedlar, A., Unger, S. W., & Axon, D. J. 1994, MNRAS, 270, 46

(ref: sakamoto95) Sakamoto, K., Okumura, S., Minezaki, T., Kobayashi, Y., & Wada, K. 1995, AJ, 110, 2075

(ref: sakamoto99) Sakamoto, K., Okumura, S. K., Ishizuki, S., & Scoville, N. Z. 1999, ApJS, 124, 403

(ref: sanchezgill11) Sánchez-Gil, M. C., Jones, D. H., Pérez, E., et al. 2011, MNRAS, 415, 753

(ref: Sarkar2023) Sarkar, K. C., Mondal, S., Sharma, P., & Piran, T. 2023, ApJ, 951, 36

(ref: satyapal08) Satyapal, S., Vega, D., Dudik, R. P., Abel, N. P., & Heckman, T. 2008, ApJ, 677, 926

(ref: Schinnerer02) Schinnerer, E., Maciejewski, W., Scoville, N., & Moustakas, L. A. 2002, ApJ, 575, 826

(ref: sersic73) Sérsic, J. L. 1973, PASP, 85, 103

(ref: Shankar2009) Shankar, F., Weinberg, D. H., & Miralda-Escudé, J. 2009, ApJ, 690, 20

(ref: shaw95) Shaw, M., Axon, D., Probst, R., & Gatley, I. 1995, MNRAS, 274, 369

(ref: she17) She, R., Ho, L. C., & Feng, H. 2017, ApJ, 842, 131

(ref: Sheth02) Sheth, K., Vogel, S. N., Regan, M. W., et al. 2002, AJ, 124, 2581

(ref: Shlosman90) Shlosman, I., Begelman, M. C., & Frank, J. 1990, Nature, 345, 679

(ref: Shlosman1989) Shlosman, I., Frank, J., & Begelman, M. C. 1989, Nature, 338, 45

(ref: Simons88) Simons, D. A., Depoy, D. L., Becklin, E. E., et al. 1988, ApJ, 335, 126

(ref: sodre99) Sodré, L., J. & Stasińska, G. 1999, A&A, 345, 391

(ref: sofue03b) Sofue, Y., Koda, J., Nakanishi, H., & Onodera, S. 2003a, PASJ, 55, 59

(ref: sofue03) Sofue, Y., Koda, J., Nakanishi, H., et al. 2003b, PASJ, 55, 17

(ref: song21) Song, Y., Linden, S. T., Evans, A. S., et al. 2021, ApJ, 916, 73

(ref: stuber21) Stuber, S. K., Saito, T., Schinnerer, E., et al. 2021, A&A, 653, A172

(ref: stuber23) Stuber, S. K., Schinnerer, E., Williams, T. G., et al. 2023, A&A, 676, A113

(ref: sun20) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020, ApJL, 901, L8

(ref: Turnrose76) Turnrose, B. E. 1976, ApJ, 210, 33

(ref: Tzanavaris07) Tzanavaris, P. & Georgantopoulos, I. 2007, A&A, 468, 129

(ref: vandenbosch16) van den Bosch, R. C. E. 2016, ApJ, 831, 134

(ref: veron-cetty86) Veron-Cetty, M. P. & Veron, P. 1986, A&AS, 66, 335

(ref: wada98) Wada, K., Sakamoto, K., & Minezaki, T. 1998, ApJ, 494, 236

(ref: weinzirl09) Weinzirl, T., Jogee, S., Khochfar, S., Burkert, A., & Kormendy, J. 2009, ApJ, 696, 411

(ref: wynn-williams85) Wynn-Williams, C. G. & Becklin, E. E. 1985, ApJ, 290, 108

(ref: yuan98) Yuan, C. & Kuo, C.-L. 1998, ApJ, 497, 689

(ref: yukita12) Yukita, M., Swartz, D. A., Tennant, A. F., Soria, R., & Irwin, J. A. 2012, ApJ, 758, 105

(ref: zabel22) Zabel, N., Brown, T., Wilson, C. D., et al. 2022, ApJ, 933, 10

# Comments about individual galaxies:

*NGC 1300:* is a very well known MW morphological twin with a prominent strong bar and two arms rich in star forming knots (cite: Eskridge02; Knapen02).

Spiral arms starting at the end of the bar, extend out to the outer Lindblad resonance (cite: england89), responsible for the outer pseudo-ring (major axis: 5’.71– (cite: buta93), age: $10^9$ yrs –(cite: elmegreen96)). The inner Lindblad resonance is the site of a circumnuclear ring. Star formation is concentrated at the ends of the bar (cite: elmegreen92), and, in the central part, there is not much star formation, no molecular gas concentration, and no clear HII regions (cite: Knapen02; maeda18), possibly due to the fast collision of gas clouds (cite: maeda18; maeda20; fujimoto20). There are many classifications for this galaxy nucleus. According to some works there is no AGN (e. g. (cite: martini03; stuber21)); while others see evidence of AGN activity (outflow: (cite: saikia94), low luminosity AGN: (cite: jang14; constantin15; gadotti19; menezes22)). In any case, there is evidence of gas infall into the inner galaxy (radius $<$ 25" (cite: lindblad96)), which harbours an SMBH with $log(M_{BH}/M_{\odot})= 7.82^{+0.29}_{−0.29}$ (cite: atkinson05). No evidence of molecular gas outflow was detected according to (cite: stuber21). The inner ring is more continuous in the northern part, with distinct regions of star formation and there is no evidence of a nuclear bar ((cite: erwin04), (cite: perezramirez2000), and references therein). This ring appears complete in the NIR (cite: Knapen02) and its semi-major axis is 400 pc (cite: comeron10), with age of $4.6 \pm 0.8$ Gyrs (cite: rosadobelza20). The stellar velocity maps from MUSE show rotation with the blueshift towards east and redshift towards west (cite: gadotti20).

*NGC 1792:* is classified as a non-barred SA(rs)bc galaxy (cite: RC3; Eskridge02; sun20; neumann23; stuber23), with flocculent (cite: Eskridge02) chaotic (cite: Garrison74) spiral arms rich in star-forming regions (cite: dahlem94; Eskridge02). The galaxy is currently interacting with NGC 1808 (cite: dahlem92). Its nuclear region, even though showing \[NeV\] emission (that is commonly found in AGNs –(cite: Goulding09; goulding10), is classified as non-active in many studies (cite: veron-cetty86; stuber21; menezes22; neumann23). (cite: Pereira-santaella10) say that the \[NeV\] emission detection in this galaxy might be due to supernova remnants, planetary nebulae, Wolf-Rayet stars or that its HII region classification might be due to strong obscuration of the nuclear region or to a very low luminosity AGN. The mass of the SMBH in its centre was estimated as $log(M_{BH}/M_{\odot})= 6.83^{+0.12}_{−0.53}$ (cite: goulding10). Observations at the H-band indicate the presence of a short nuclear bar (cite: jungwiert97). There is no evidence of molecular gas outflows (cite: stuber21).

*NGC 2903:* is a very well-studied SAB(rs)bc (cite: RC3) galaxy with a strong (in the NIR –(cite: regan99; Sheth02; hernandez05), in short wavelengths it is similar to a patchy spiral disk –(cite: popping10)) and young bar ((cite: dutil99), with age between 200 and 600 Myr – (cite: leon08)) immersed in a flocculent disk (cite: Canzian93), somehow in a very complex structure. Bright HII regions delineate the bar and the multi-arm structure of the galaxy (cite: Knapen02). This galaxy is a typical example of "hot-spot" galaxy (cite: sersic73; Turnrose76; bonatto89), rich in individual young stellar clusters (cite: alonsoherrero01), and starburst galaxy (cite: Turnrose76; wynn-williams85; Simons88; Jackson89; planesas97; perez-ramirez10). The hot-spots near the nucleus seem part of the circumnuclear starburst ring (cite: planesas97; sakamoto99; perezramirez2000; alonsoherrero01; mazzuca11), which has a radius of about 600 pc (cite: leitherer02). The galaxy hosts a SMBH with a mass of $log(M_{BH}/M_{\odot})= 7.06^{+0.28}_{−7.06}$ (cite: vandenbosch16), and is commonly classified as non-active (cite: casuso90; ho97; sodre99; Pereira-santaella10; neumann23), which is supported by no evidence of molecular gas outflows (cite: stuber21), no significant \[NeV\] emission (cite: Goulding09), and low luminosity in X-rays (0.5−8.0 keV –(cite: yukita12)). However, NGC 2903 has NIR emission-line ratios compatible with an AGN (cite: matsuoka12) and new measurements of its X-ray luminosity indicate the presence of a variable AGN (cite: hoyer). The nuclear starburst might be due to the bar that drives the molecular gas into the centre (cite: jackson91; hernandez05; leon08).

*NGC 3059:* is not a very well-studied galaxy. It is classified as SB(rs)bc; however some studies classify it as SBcd (e. g. (cite: Eskridge02)), weakly barred (cite: stuber23) or with a small bar (cite: beck02). There is no evidence of an inner ring in the literature (cite: stuber23), and no AGN (cite: stuber21; Goulding09; neumann23).

*NGC 4303:* is a grand design SAB(rs)bc (cite: RC3) double barred galaxy ((cite: Colina97b; colina99; Colina2000), nuclear bar diameter: 0.2 kpc, primary bar diameter: 2.64 kpc– (cite: erwin04)). It has a young (2.5 -25 Myrs) circumnuclear ring (200−250 pc– (cite: riffel16)), connected to the bar (which is possibly responsible for the feeding of the nuclear region and the ring– (cite: Colina97b)), by two spiral arms, and to an inner bar (cite: Colina97b; Colina2000; perezramirez2000). (cite: Schinnerer02) studied the molecular emission of the central kiloparsec of NGC 4303 and found that inflowing motions of the primary bar of the galaxy are responsible for the complex structure of the centre of this galaxy, and that this circumnuclear ring might be in an early stage of formation. The nuclear activity of this galaxy was classified as Seyfert 2 or LINER or in-between (e. g. (cite: colina99; Argyle90)), or HII region (cite: ho97). According to (cite: colina02), there is a young ($\sim$ 4 Myr) super star cluster coexisting with the low luminosity AGN in the nucleus (within 3.1 pc), and (cite: Tzanavaris07; jimenez03) could not distinguish its nuclear emission from a hidden AGN, a central stellar cluster, or a ultra-luminous X-ray source. NGC 4303 harbours an SMBH with a mass of $log (M_{BH}/M_{\odot})= 6.58^{+0.07}_{-0.26}$ (cite: davis19). An \[OIII\] outflow was detected north-east of the nucleus by (cite: colina99) and no molecular gas outflow was detected (cite: stuber21).

*NGC 4321:* is a very well studied MW morphological twin (SABbc– (cite: RC3)). Due to its inclination, distance, and contrasted features, it was subject to many detailed studies. For instance, this galaxy has a clumpy circumnuclear ring, whose peak radius is 458 pc (cite: song21). Such starburst ring is being maintained by the gravitational influence of the bar (cite: arsenault88; knapen95b; perezramirez2000) and its age is about 50 Myrs (the majority of stars are younger than 6 Myr – (cite: sanchezgill11)). (cite: knapen95b) state that there are two Inner Lindblad Resonances in the nuclear region: one at 500 pc and the other at 1.3 kpc from the nucleus. According to these authors, most of star formation happens at the inner resonance (also see (cite: sakamoto95; yuan98; knapen2000)). The ring is connected by two arms leading the bar to the nucleus ((cite: knapen95a; knapen95b; Knapen02) and the younger stellar populations are located near the connecting points between the ring and the larger bar (cite: mazzuca08). There is also a double bar structure (cite: pierce86; shaw95), the nuclear bar being clearly detected in the NIR and the primary bar being weaker (cite: font14) or moderate (cite: knapen95b). Although (cite: knapen95b) do not found strong evidence for the second bar, they say both structures are part of the same bar, aligned with comparable strength; (cite: garciaburillo98) dynamical models favor that this nuclear bar is decoupled from the major bar and it is rotating faster. There are two dust arms connecting the nuclear bar to the outer bar (cite: knapen95b; sakamoto95), and (cite: wada98) say that this nuclear structure is short lived (10$^7$ yrs) and recurrent. NGC 4321 nucleus was classified as HII region ((cite: keel83), supported by (cite: gonzales09) that have not found any AGN activity); however, some studies classify it as a transition object (cite: ho97) and the emission of \[NeV\] detected by (cite: satyapal08) sustains the hypothesis of a low luminosity AGN. The SMBH in NGC 4321 centre has a mass of $log (M_{BH}/M_{\odot})= 6.67^{+0.17}_{-6.67}$ 6.67+0.17 −6.67 (cite: vandenbosch16). The high nuclear CO concentration is a result of the gas being driven by gravitational torques from the bar; however the fact that there is no strong AGN activity at the centre of this galaxy shows that this inflow is still at intermediate scale, and is not yet prolonged into the center to trigger nuclear activity (cite: sakamoto95). Such remark is actually proven by the detailed torque analysis made by (cite: Garcia-Burillo2005): there are positive torques along the spiral arms at the trailing edges of the nuclear bar and negative torques along the leading quadrants and outer disk (r $>$ 900). They also noticed that the average torque inside 200 pc is positive, implying that there is no significant inflow of molecular gas in the nucleus. (cite: castillo-morales07) detected a nuclear blueshifted region that might be related to an outflow of gas. Such outflow was also reported by (cite: jimenezesvicente07) and the authors say that such wind was generated by a nuclear starburst.

*NGC 4536:* is a SAB(rs)bc (cite: RC3) galaxy with two conspicuous spiral arms (cite: mazzalay14). This galaxy was previously classified as starburst (cite: ho97); however (cite: hughes05) classified it as a weak AGN, based on optical emission-line ratios. There is \[NeV\] emission, detected 10" north-east from the optical nucleus (cite: satyapal08), and XMM-Newton data presents a power law emission typical of low luminosity AGNs (cite: mcalpine11), that supports the presence of a low luminosity AGN in this nucleus. A circumnuclear ring with radius of about 270 pc with age of 6.5 Myr was detected with near-infrared data, with no gradients along the ring (cite: mazzalay13; mazzalay14). There is no evidence of molecular gas outflow (cite: stuber21) and, in the inner 500 pc, the gas kinematics is predominantly circular with streams of inflowing gas along bar into the centre (cite: jogee05). The nucleus is connected to the circumnuclear ring and there is evidence of a nuclear bar (cite: mazzalay14). The star formation is predominant in the ring and it has ceased in the nucleus (cite: davies97; jogee05). If there is a low luminosity AGN in this galaxy, there is no influence of its emission in the circumnuclear ring (cite: mazzalay13). The SMBH mass was estimated to be $log(M_{BH}/M_{\odot})= 7.577^{+0.052}_{−0.054}$ (cite: Berrier13).

*NGC 4689:* is a Milky-Way analogue classified non-barred SA(rs)bc (cite: RC3). The galaxy has flocculent spiral arms (cite: jungwiert97); however, (cite: arsenault89) says that it has a weak bar. Its nucleus is classified as starburst (cite: ho97), confirmed by the non- detection of X-ray emission, with a SMBH mass of $log(M_{BH}/M_{\odot})= 4.2 \pm 0.8$ (cite: graham19). No molecular outflow was detected (cite: stuber21). Molecular gas shows patchy morphology without clear structure (bar or spiral), with a regular velocity field (cite: sofue03; sofue03b). Two pseudo rings were found, one located at the bar Inner Lindblad Resonance, 0’ $\times$0’, and other located at the Outer Lindblad Resonance, with 1’ $\times$1’ (cite: comeron14).

*NGC5248:* is an SAB(rs)bc (cite: RC3) galaxy with strong spiral arms (cite: elmegreen92). Within our field of view, there is evidence of two rings, one inner ring of 650pc diameter around the bar and a double nuclear ring (cite: buta93; comeron10). The bar fuels the nuclear ring with diameter of 150 pc (cite: comeron10) with two molecular trailing spirals, which connect to other two arms (cite: jogee02) (cite: buta93; maoz01; comeron10). The nuclear rings have stellar population ages between 1 and 10 Myr (cite: elmegreen97). Its nucleus was classified as starburst (cite: ho97) and Seyfert/LINER (cite: gadotti19) from the optical emission-line ratios, and harbours a SMBH with mass of $log(M_{BH}/M_{\odot})= 6.73^{-0.22}_{−0.20}$ (cite: she17). There is no evidence of molecular gas outflows (cite: stuber21). (cite: haan09) studied the torques of the CO molecular gas and found that NGC 5248 shows a mixed pattern of gravitational torques that corresponds to the bar and spiral arms, comparable to our results.

*NGC 5921:* is a SB(r)bc (cite: RC3) galaxy with a compact nucleus and a prominent bar that ends in an outer ring (cite: Eskridge02; fathi09). Its nucleus is classified as composite (cite: ho97), LINER and Seyfert-like (cite: veron-cetty86; arsenault89), and non-active (cite: burtscher21). This galaxy has an inner ring-like structure (cite: hernandez05; martinez-garcia12). Its SMBH estimated mass is $log(M_{BH}/M_{\odot})=7.07^{-0.42}_{−7.07}$ (cite: vandenbosch16).

# H$\alpha$ gas torques with MUSE data

![](torque_MUSE_new.png)

For the sample of 10 galaxies of this work, only four galaxies (NGC 1300, NGC 4303, NGC 4321 and NGC 5248) had Multi Unit Spectroscopic Explorer (MUSE) data cubes available. The H$\alpha$ emission line can trace the star forming regions and interstellar medium in the less dense regions, giving a more complete image of the structures of the galaxy. In contrast, the molecular gas emission is more compact, giving a overall idea of the structures punctually. In order to see the distribution of torques in general in the galaxies and compare them with the obtained molecular gas torques, we made images of H$\alpha$ emission line from MUSE data cubes, due to the good spatial resolution, and FOV, to compute the torques on this gas. The data were taken from the ESO public archive. The information about the observations of each galaxy is shown in table [1](#obsinfo_MUSE).

The H$\alpha$ emission-line images were taken from the data cubes by summing the spectral interval of the emission line and by subtracting the nearby continuum equivalent to the same interval. After that, the torques were computed associated to the red images based on the size of the FOV. In the case of NGC 1300, we used HST (cyan square in Fig. [1](#galaxiesimage) or Fig. [2](#NGC1300_m0_m1)b), in the case of NGC 4303, the Legacy image was used (red square in Fig. [1](#galaxiesimage) or Fig. [6](#NGC4303_m0_m1)b), for NGC 4321, we also used the Legacy image (red square in Fig. [1](#galaxiesimage) or Fig. [7](#NGC4321_m0_m1)b), and for NCG 5248 we used the HST image (cyan square in Fig. [1](#galaxiesimage) or Fig. [10](#NGC5248_m0_m1)b). The FOV of the MUSE data was cut to be the same size of the associated FOVs. We then computed the torques analogously to what was done with the ALMA data.

|  Galaxy  |  Program ID   |     P. I.      | Observation Date | Exposition time (s) |
|:--------:|:-------------:|:--------------:|:----------------:|:-------------------:|
| NGC 1300 | 097.B-0640(A) |  Gadotti, D.   | October 2nd 2016 |        2880         |
| NGC 4303 |  1100.B-0651  | Schinnerer, E. |  May 10th 2019   |        2580         |
| NGC 4321 |  1100.B-0651  | Schinnerer, E. | April 28th 2019  |        2580         |
| NGC 5248 | 097.B-0640(A) |  Gadotti, D.   |  April 4th 2016  |        3840         |

: - Observational information of MUSE data from NGC 1300, NGC 4303, NGC 4321, and NGC 5248.

[^1]: The NASA/IPAC Extragalactic Database (NED) is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology.

</paper>

Write the methods card for this paper.