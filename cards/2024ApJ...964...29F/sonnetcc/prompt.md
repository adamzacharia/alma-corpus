# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...964...29F\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...964...29F",
 "title": "The Relationships between Active Galactic Nucleus Power and Molecular Gas Mass within 500 pc of the Center of Elliptical Galaxies",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Fujita, Yutaka",
 "n_authors": 5,
 "arxiv_id": "2310.03794",
 "doi": "10.3847/1538-4357/ad28c0",
 "alma_projects_linked_by_archive": [
  "2011.0.00735.S",
  "2013.1.00073.S",
  "2013.1.00828.S",
  "2015.1.00598.S",
  "2015.1.00623.S",
  "2015.1.00627.S",
  "2015.1.00644.S",
  "2015.1.00860.S",
  "2015.1.00971.S",
  "2015.1.01198.S",
  "2015.1.01572.S",
  "2016.1.00683.S",
  "2016.1.01135.S",
  "2016.1.01214.S",
  "2017.1.00301.S",
  "2017.1.00830.S",
  "2019.1.00036.S",
  "2019.1.01845.S"
 ]
}
```

Paper text:
<paper>
# The relationships between AGN power and molecular gas mass within 500 pc of the center of elliptical galaxies

## Abstract

The physical quantity that directly controls the feedback of active galactic nuclei (AGNs) in elliptical galaxies remains to be determined. The discovery of molecular gas around the AGNs suggests that the gas is fueling the AGNs. Therefore, we analyze Atacama Large Millimeter/submillimeter Array (ALMA) data for the CO line (J=1–0, 2–1, 3–2) emission and estimate the mass of molecular gas within 500 pc of the center of 12 non-central elliptical galaxies (NCEGs) and 10 of the brightest cluster galaxies (BCGs). We find that the mass ($M_{\rm mol} \sim 10^5$–$10^9\rm\: M_\ensuremath{\odot}$) is correlated with the jet power of their AGNs, which is represented by $P_{\rm cav}\approx 4.1\times 10^{42}(M_{\rm mol}/10^7\: M_\ensuremath{\odot})^{1.3}\rm\: erg\: s^{-1}$, although NCEGs alone do not show the correlation. We also find that $M_{\rm mol}$ is correlated with the AGN continuum luminosities at $\sim 1.4$ GHz ($L_{\rm 1.4}$) and $\sim 100$–300 GHz ($L_{\rm con}$). Since $P_{\rm cav}$ reflects galactic-scale, long-term AGN activity, while the continuum luminosities reflect local ($\lesssim 500$ pc), short-term AGN activity, our results suggest that AGN activity depends on the amount of gas, regardless of its time scale. On the other hand, we cannot find a clear correlation between the mass of the black holes in the AGNs ($M_{\rm BH}$) and $P_{\rm cav}$.

This suggests that $M_{\rm mol}$, rather than $M_{\rm BH}$, is the main factor controlling AGN activity. We confirm that the origin of the continuum emission from the AGNs at $\sim 1.4$–300 GHz is mostly synchrotron radiation.

# Introduction

Supermassive black holes are ubiquitous at the centers of galaxies (cite: 2013ARA&A..51..511K), and they produce an enormous amount of energy as active galactic nuclei (AGNs). The AGNs in massive elliptical galaxies are in "radio feedback" mode and often show jet activity (cite: 2014ARA&A..52..589H). Since elliptical galaxies are filled with hot gas (cite: 1989ARA&A..27...87F), it may be natural to assume that the hot gas is fed into the black holes in the form of the Bondi accretion (cite: 1952MNRAS.112..195B). (cite: 2006MNRAS.372...21A) showed that there is a strong correlation between the AGN jet power ($P_{\rm cav}$), which can be inferred from the the size of the X-ray cavities in the host galaxies, and the Bondi accretion rate. However, later studies have disproved such a strong correlation. (cite: 2013MNRAS.432..530R).

The discovery of a large amount of molecular gas ($\gtrsim 10^8\rm\: M_\ensuremath{\odot}$) in elliptical galaxies at the center of nearby clusters (cite: 2001MNRAS.328..762E; 2003A&A...412..657S; 2014ApJ...792...94D; 2014ApJ...785...44M; 2016ApJ...832..148V; 2016MNRAS.458.3134R; 2017ApJ...848..101V; 2017MNRAS.472.4024R; 2019A&A...631A..22O; 2019MNRAS.490.3025R; 2020ApJ...894...72S; 2020MNRAS.496..364R; 2021MNRAS.503.5179N) suggests that this cold gas is feeding the AGNs. However, the cold gas is often widely distributed on a scale of $\gtrsim 10$ kpc, and it is unlikely that all of the gas contributes to AGN activity because some of it is consumed in star formation (cite: 2022ApJ...924...24F). As direct evidence for AGN feeding, many absorption lines have been observed in some AGNs, indicating the presence of dense gas in the vicinity of the AGNs (cite: 2014ApJ...792...94D; 2016Natur.534..218T; 2019MNRAS.485..229R; 2023MNRAS.518..878R). However, it is difficult to estimate the mass of the circumnuclear gas from the absorption. Thus, it is important to focus on the emission from the cold gas in the vicinity (say $\lesssim 500$ pc) of the AGNs, which can directly influence the gas accretion onto them.

We note that (cite: 2019MNRAS.490.3025R) compared the mass of the circumnuclear molecular gas obtained with the Atacama Large Millimeter/submillimeter Array (ALMA) with the AGN jet power $P_{\rm cav}$ and showed that there is a correlation (their Figure 7, see also our Figure [4](#fig:Mmol)(a)). However, they measured the mass in a single ALMA-synthesized beam centered on the AGNs. Since the physical scale of a given beam is larger for more distant objects (see Section [2](#sec:sample) and Figure [1](#fig:rus19a)), the mass in that beam is likely to be larger, while distant AGNs are observationally biased to be brighter and more powerful. This could lead to an artifact relationship.

For this reason, we examined the relationship between AGN power and molecular gas mass within a fixed physical radius ($M_{\rm mol}$), i.e. within 500 pc of the black holes, for 9 brightest cluster galaxies (BCGs) at the center of clusters (cite: 2023arXiv230316927F). The 9 BCGs are part of the samples of (cite: 2019A&A...631A..22O) and (cite: 2019MNRAS.490.3025R). Since the physical scale of the region is fixed, the above bias should be less likely to occur.

We note that this scale (500 pc) is comparable to the circumnuclear disk around the black hole (cite: 2019ApJ...883..193N; 2022ApJ...924...24F). In Paper I we found that $M_{\rm mol}$ is correlated with the AGN jet power ($P_{\rm cav}$). Since the timescale of cavity formation is $\sim 10^7$ yr (cite: 2004ApJ...607..800B; 2006MNRAS.372...21A; 2006ApJ...652...216R), $P_{\rm cav}$ is the power averaged over this timescale. On the other hand, we found that the continuum luminosities of AGNs at 1.4 GHz ($L_{1.4}$) and $\sim 100$–300 GHz ($L_{\rm con}$) are not correlated with $M_{\rm mol}$ (Paper I). The continuum emission is observed as a point source. Considering that the typical beam size is $\lesssim 500$ pc and the corresponding light travel time is $\lesssim 1600$ yr, the emissions reflect the recent activity of the AGNs. Thus, the lack of correlation between the continuum luminosities and $M_{\rm mol}$ may indicate that AGN activity varies on a short time scale. Indeed, intermittent jet activity and jet-cloud interactions have been observed for NGC 1275, the BCG of the Perseus cluster. This object shows radio luminosity variations on a timescale of decades (cite: 2010PASJ...62L..11N; 2017MNRAS.465L..94F; 2017ApJ...849...52N; 2021ApJ...920L..24K).

In this study, we extend the sample of galaxies studied in Paper I to lower masses by including 12 nearby non-central elliptical galaxies (NCEGs) that are not at the center of massive clusters [^1]. We investigate whether the $P_{\rm cav}$–$M_{\rm mol}$ scaling relation is continuous from less massive NCEGs to giant elliptical galaxies (BCGs). If the relation is well established, it could be used in theoretical models of galaxy formation. For the $L_{1.4}$–$M_{\rm mol}$ and $L_{con}$–$M_{\rm mol}$ relations, we test for the existence of a correlation for the larger sample. We also investigate whether the mass of the black holes is a key factor in controlling AGN activity.

The paper is structured as follows: Section [3](#sec:reduc) describes the reduction of the ALMA data. Section [4](#sec:result) presents the results of the data analysis and the correlation between the mass of molecular gas around black holes and AGN activity. Section [5](#sec:discuss) explores the implications of these correlations. We also investigate whether the black hole mass affects AGN activity, and discuss the source of the nonthermal emissions. Section [6](#sec:conc) is devoted to summarizing our findings.

We assume $H_0=70\rm\: km\: s^{-1}\: Mpc^{-1}$, $\Omega_m=0.3$, and $\Omega_\Lambda=0.7$ in this study. All errors are $1\:\sigma$ unless otherwise noted.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | $z$ | CO line | ALMA ID project | Obs. time | Date | Beam | PA | $v$ binning | rms |
|  |  |  |  | (min) |  | ($''$) | (deg) | ($\rm km\: s^{-1}$) | ($\rm mJy\: bm^{-1}$) |
| NGC 4636 | 0.00313 | J=2-1 | 2015.1.00860.S | 59 | 2016-05-02 | 0.68 $\times$ 0.62 | -51 | 20 | 0.3 |
| NGC 4472 | 0.00327 | J=3-2 | 2017.1.00830.S | 17 | 2017-12-26 | 1.2 $\times$ 1.2 | 1 | 30 | 2 |
| NGC 4374 | 0.00339 | J=2-1 | 2013.1.00828.S | 51 | 2015-08-16 | 1.2 $\times$ 1.1 | -85 | 20 | 2 |
| NGC 5846 | 0.00571 | J=2-1 | 2015.1.00860.S | 40 | 2016-05-13 | 0.77 $\times$ 0.68 | -85 | 20 | 0.3 |
| NGC 1316 | 0.00601 | J=1-0 | 2019.1.01845.S | 71 | 2019-11-12 | 2.70 $\times$ 1.9 | -84 | 20 | 0.5 |
| NGC 5813 | 0.00653 | J=2-1 | 2015.1.00971.S | 67 | 2016-06-30 | 0.85 $\times$ 0.46 | -66 | 20 | 0.2 |
| NGC 4261 | 0.00726 | J=2-1 | 2017.1.00301.S | 31 | 2018-01-19 | 0.41 $\times$ 0.33 | 40 | 20 | 0.4 |
| NGC 7626 | 0.01136 | J=2-1 | 2019.1.00036.S | 9 | 2019-12-15 | 1.5 $\times$ 1.3 | 52 | 20 | 0.6 |
| IC 4296 | 0.01247 | J=2-1 | 2015.1.01572.S | 51 | 2016-06-04 | 0.61 $\times$ 0.57 | -80 | 20 | 0.4 |
| NGC 1600 | 0.01561 | J=3-2 | 2016.1.01135.S | 22 | 2016-12-27 | 0.77 $\times$ 0.48 | -73 | 20 | 0.7 |
| NGC 507 | 0.01646 | J=2-1 | 2016.1.00683.S | 42 | 2017-08-03 | 0.21 $\times$ 0.15 | 7 | 20 | 0.3 |
| NGC 315 | 0.01648 | J=2-1 | 2017.1.00301.S | 112 | 2018-10-19 | 0.34 $\times$ 0.19 | 9 | 20 | 0.3 |
| M 87 | 0.00428 | J=2-1 | 2013.1.00073.S | 45 | 2015-06-15 | 2.5 $\times$ 2.3 | -51 | 20 | 2 |

: Target and observation details

# Sample Selection

We examine CO line emission from cold molecular gas in elliptical galaxies using archival ALMA observations to investigate the correlation between cold gas mass and AGN power. Our sample galaxies are taken from the NCEGs studied by (cite: 2010ApJ...720.1066C) and (cite: 2011ApJ...735...11O). For 12 of them we found ALMA data that may contain CO line emissions (cite: 2017ApJ...845..170B; 2018ApJ...858...17T; 2018ApJ...860....9M; 2018MNRAS.475.3004S; 2019MNRAS.484.4239R; 2019PASJ...71...85M; 2021ApJ...908...19B; 2022A&A...664L..11S; 2022ApJ...928..150T). We also add M 87, which is a BCG not examined in Paper I. The observational details of the final sample of 13 galaxies are given in Table [1](#tab:obs). For the NCEGs, their jet powers $P_{\rm cav}$ were obtained by (cite: 2010ApJ...720.1066C). They defined the energy of each to be $4pV$, which is the enthalpy of a cavity filled with relativistic gas. The jet $P_{\rm cav}$ was obtained by dividing the energy by the age of the cavity (the buoyant rise time). If there are multiple cavities in a galaxy, their $P_{\rm cav}$ have been summed. Since we have simply selected the targets that have been observed with ALMA and for which $P_{\rm cav}$ has been estimated, they are not a complete sample.

The redshift range of our sample is 0.00313 (NGC 4636; Table [1](#tab:obs)) to 0.1028 (PKS 0745-191; Paper I) and we focus on the central 500 pc (1 kpc in diameter). In contrast, (cite: 2019MNRAS.490.3025R) studied galaxies with a much wider range of redshifts ($z=0.0093$–0.596), and the beam sizes in which they estimated the circumnuclear gas mass varied among the galaxies (Figure [1](#fig:rus19a)). The fixed radius (500 pc) and the narrower redshift range (Figure [1](#fig:rus19a)) should make our sample less biased.

# Data Reduction

The sample galaxies were observed with ALMA at frequencies corresponding to the CO(J=1-0), CO(J=2-1), or CO(J=3-2)[^2] rotational transition lines, mostly CO(J=2-1), with additional spectral windows that were used to image the millimeter/submillimeter (mm/submm; $\sim 100$–300 GHz) continuum emission. The observations were single pointing, centered on the AGNs, except for NGC 1316, which was covered with mosaics. The data were calibrated using the appropriate version of the Common Astronomy Software Application (CASA) software (cite: 2007ASPC..376..127M) and the ALMA Pipeline used for quality assurance.

We subtracted the continuum emission using line-free channels with the CASA task `uvcontsub` (fitorder=1) to study the line emissions. We reconstructed the line cubes and the underlying continuum maps using the CASA task `tclean` with a threshold of $3\:\sigma$. We used Briggs weighting with a robust parameter of 2 (natural weighting), following previous studies (cite: 2019A&A...631A..22O; 2019MNRAS.490.3025R). The synthesized beam size and rms in each final data cube are shown in Table [1](#tab:obs).

# Results

Using the CASA task `immoments`, we generate images of the integrated intensity for the AGN neighborhoods in the 13 galaxies that cover each CO line. From 6 of them (IC 4296, NGC 315, NGC 1316, NGC 4261, NGC 4374, and NGC 4636) we detected CO emission around their centers. Their images are shown in Figure [2](#fig:image). The following analysis focuses on these 6 galaxies. For the other 7 sources (6 NCEGs + M 87) we could not detect any cold gas, and only the upper limit of the mass is discussed.

Following Paper I, we focus on the central 500 pc region because it is well resolved with ALMA and the gas in this region is likely to be fed into the black hole (cite: 2008ApJ...681...73K; 2022ApJ...924...24F). For all 6 galaxies in Figure [2](#fig:image), the emission is concentrated on a scale smaller than $500$ pc. This is in contrast to the more massive BCGs studied in Paper I, where the CO emission generally extends beyond the central 500 pc region. In the case of NGC 1316 and NGC 4636, the peak of the CO is offset from the location of the AGN (Figure [2](#fig:image)), implying that the gas accretion is neither spherically nor axially symmetric. This happens when the accretion is chaotic (cite: 2015A&A...579A..62G).

We extract spectra from the emission regions for the 6 line-detected galaxies (Figure [3](#fig:spec)) to check the profiles of the CO lines. Unlike in Paper I, we did not fit the spectra of the 6 galaxies with one or two Gaussian components, because not all of them are represented by Gaussians. For example, the spectrum of NGC 315 clearly shows the rotation of the gas and is not well fitted by Gaussians (Figure [3](#fig:spec)). Instead, we derived the line flux densities from the brightness of the integrated intensity images (Figure [2](#fig:image)). The images include channels where line emission is detected. For IC 4296 we ignore the channels corresponding to the prominent absorption (Figure [3](#fig:spec)). We have confirmed that the two methods (Gaussian fit and intensity image) give consistent results when the spectrum can be well fitted by Gaussians. For the 7 galaxies in which we could not detect cold gas, we estimate the $3\:\sigma$ upper limit of the line intensity by assuming that a possible line is within $\pm 500\:\rm km\: s^{-1}$ of the galaxy’s velocity.

In addition, unlike Paper I, we do not discuss the mass accretion rate due to turbulent viscosity ($\dot{M}$), where the turbulent velocity is derived from the width of the Gaussian components. While $\dot{M}$ is determined by the molecular gas mass ($M_{\rm mol}$) and the turbulent velocity, as shown in Paper I, the dependence of the turbulent velocity is not significant. This is because while $M_{\rm mol}$ varies by several orders of magnitude among galaxies, the turbulent velocity varies by only a factor of a few. As a result, $\dot{M}$ is approximately proportional to $M_{\rm mol}$. Moreover, the estimate of $\dot{M}$ has a large uncertainty, such as the gas morphology. Therefore, we focus on $M_{\rm mol}$ rather than $\dot{M}$ in this study.

## Molecular gas mass

For galaxies in which CO emission is detected, we estimate the masses of the molecular gas from the CO intensities $S_{\rm CO}\Delta v$ given in Table [2](#tab:obs2). The table contains the objects studied in Paper I. We take the following relation from (cite: 2013ARA&A..51..207B):

$$\begin{eqnarray}
 M_{\rm mol} &=& \frac{1.05\times 10^4}{F_{\rm ul}}\left(\frac{X_{\rm CO}}{2\times 10^{20}
\frac{\rm cm^{-2}}{\rm K\: km\: s^{-1}}}\right)
\left(\frac{1}{1+z}\right)\nonumber\\
& &\left(\frac{S_{\rm CO}\Delta v}{\rm Jy\: km\: s^{-1}}\right)
\left(\frac{D_{\rm L}}{\rm Mpc}\right)^2\: M_\odot\:,
\end{eqnarray}$$

where $X_{\rm CO}$ is the conversion factor from CO to H$_2$ and $D_{\rm L}$ is the luminosity distance. The empirical factor $F_{\rm ul}$ specifies the CO excitation used to estimate the CO(1-0) flux from higher J measurements, since we are comparing different transition lines. Specifically, $F_{21}$ gives a CO(2-1)/CO(1-0) line ratio on the flux density (Jy) scale of 3.2, and $F_{32}$ gives a CO(3-2)/CO(1-0) ratio of 7.2 (cite: 2019MNRAS.485..229R; 2019MNRAS.490.3025R). Since the conversion factor $X_{\rm CO}$ is not well understood for elliptical galaxies, we adopt a default value of $X_{\rm CO}=2\times 10^{20}\rm\: cm^{-2}(K\: km\: s^{-1})^{-1}$ measured in the Milky Way, following previous studies ((cite: 2019A&A...631A..22O; 2019MNRAS.490.3025R) and see their discussion). For galaxies in which no CO emission is detected, we estimate the upper bounds of the mass from the $3\:\sigma$ upper bounds of $S_{\rm CO}\Delta v$. The resulting mass $M_{\rm mol}$ is shown in Table [2](#tab:obs2).

## Circumnuclear gas and jet power

Figure [4](#fig:Mmol)(a) shows the relationship between the mass of molecular gas within 500 pc of the center ($M_{\rm mol}$) and the AGN jet power required to produce all the observed X-ray cavities in the galaxy ($P_{\rm cav}$). Red filled squares represent NCEGs, while black filled circles represent BCGs. While the data of $P_{\rm cav}$ for the NCEGs are taken from (cite: 2010ApJ...720.1066C), those for the BCGs are taken from (cite: 2006ApJ...652...216R) and (cite: 2018ApJ...853..177P). The jet powers for the BCGs were measured in the same manner as for the NCEGs.

The NCEGs analyzed in this paper have lower values of $M_{\rm mol}$ ($\lesssim 10^7\: M_\ensuremath{\odot}$; Table [2](#tab:obs2)) compared to the BCGs analyzed in Paper I ($M_{\rm mol}\gtrsim 10^7\: M_\ensuremath{\odot}$). The Kendall rank correlation coefficient on the logarithmic scales is $\tau=0.472$ with a $p$-value of $1.9\times 10^{-3}$, which is below the standard threshold of 0.01. Here, the $p$ value indicates the probability that the quantities are statistically independent. The coefficient and the regression line (cite: NADAbook) are calculated for all galaxies including 7 galaxies for which only the upper limit of $M_{\rm col}$ was obtained using the R/CRAN package NADA[^3]. The regression line can be represented by a power law model as follows:

$$\begin{equation}
\label{eq:A1}
 \log\left(\frac{P_{\rm cav}}{10^{42}\rm erg\: s^{-1}}\right) = A_1\log\left(\frac{M_{\rm mol}}{M_\odot}\right) + B_1\:,
\end{equation}$$

where $A_1$ and $B_1$ are parameters, and we get $A_1 = 1.3$ and $B_1 = -8.6$. Thus, the relation can be written as $P_{\rm cav}\approx 4.1\times 10^{42}(M_{\rm mol}/10^7\: M_\ensuremath{\odot})^{1.3}\rm\: erg\: s^{-1}$. The scatter in the relationship between $M_{\rm mol}$ and $P_{\rm cav}$ may be due to physical factors (see Section [5.1](#sec:corr)). Note that the correlation is mainly influenced by the BCGs. This is because no correlation can be found for the 12 NCEGs alone.

We also checked the molecular gas mass within the radius of 250 pc. Considering the given beam sizes, we include all NCEGs and 5 BCGs (NGC 5044, Abell 262, Abell 3581, Abell 2052, and M 87). Hydra A is not included due to strong absorption around the center (Paper I). For the molecular gas mass within 250 pc (Figure [4](#fig:Mmol)(a)), we examined the $P_{\rm cav}$–$M_{\rm mol}$ relation and found that the correlation coefficient is $\tau = 0.25$ and the $p$-value is $0.16$. The lack of correlation is partly due to the small number of BCGs that contribute much to the $P_{\rm cav}$–$M_{\rm mol}$ relationship.

## Circumnuclear gas and continuum emission

While $P_{\rm cav}$ depends on AGN activity on a timescale of $\sim 10^7$ yr, the radio continuum emission is associated with recent ($\lesssim 10^3$ yr) AGN activity (Section [1](#sec:intro)). Thus, the presence or absence of the correlation between $M_{\rm mol}$ and the continuum luminosity reflects the time variability of the gas supply and/or AGN activity on the shorter timescale.

Figure [4](#fig:Mmol)(b) shows the relation between $M_{\rm mol}$ and $L_{\rm con}$, which is the continuum luminosity in the mm/submm band. The luminosity is calculated from the continuum flux in the line-free ALMA channels. Fluxes observed at different frequencies are converted to those at the rest-frame CO(1-0) line frequency ($\nu_{10}=115.3$ GHz), assuming that the continuum emission is represented by a power law of $S_\nu \propto (\nu/\nu_{10})^\gamma$, where $\nu$ is the frequency. A typical spectral index of $\gamma=-0.75$ is assumed, following Paper I. In fact, the contribution of dust emission is not significant (see Section [5.3](#sec:origin)) and the results do not depend much on $\gamma$. For an object observed at the frequency $\nu_{\rm con}$ and located at the redshift $z$, we estimate the radio continuum luminosity at the frequency $\nu_{10}$ to be

$$\begin{equation}
 L_{\rm con} = \frac{4\pi D_{\rm L}^2 \nu_{\rm con} F_{\rm con}}{[(1+z)\eta]^{1+\gamma}}\:,
\end{equation}$$

where $F_{\rm con}$ is the observed flux (mJy), and $\eta$ is the line frequency ratios ($\eta=1$ for CO(1-0), $\eta\approx 2$ for CO(2-1), and $\eta\approx 3$ for CO(3-2)), which is needed to convert the flux between different line frequencies. The redshift dependence of $(1+z)^{-(1+\gamma)}$ comes from the $K$-correction (cite: 2022ApJ...924..133R). The values of $\nu_{\rm con}$, $F_{\rm con}$, and $L_{\rm con}$ are listed in Table [2](#tab:obs2).

The relationship between $L_{\rm con}$ and $M_{\rm mol}$ is shown in Figure [4](#fig:Mmol)(b). There is a correlation between $M_{\rm mol}$ and $L_{\rm col}$ with a correlation coefficient of $\tau = 0.515$ and a $p$-value of $6.8\times 10^{-4}$. The regression line can be represented by a power law model of the form:

$$\begin{equation}
\label{eq:A2}
 \log\left(\frac{L_{\rm con}}{10^{42}\rm erg\: s^{-1}}\right) = A_2\log\left(\frac{M_{\rm mol}}{M_\odot}\right) + B_2\:,
\end{equation}$$

where $A_2$ and $B_2$ are fit parameters and we obtain $A_2=1.4$ and $B_2=-11.5$.

We also calculate the continuum luminosity at 1.4 GHz ($L_{\rm 1.4}$) from the observed flux at 1.4 GHz taken from the literature:

$$\begin{equation}
 L_{\rm 1.4} = \frac{4\pi D_{\rm L}^2 \nu_{\rm 1.4} F_{\rm 1.4}}
{(1+z)^{1+\gamma}}\:,
\end{equation}$$

where $\nu_{1.4}$ is $1.4$ GHz and $F_{1.4}$ is the observed flux at 1.4 GHz (Table [2](#tab:obs2)), and $\gamma=-0.75$. The derived luminosities $L_{1.4}$ are shown in Table [2](#tab:obs2) and compared to $M_{\rm mol}$ in Figure [4](#fig:Mmol)(c). The correlation coefficient is $\tau = 0.437$ and the $p$-value is $4.0\times 10^{-3}$, indicating the existence of a correlation between $M_{\rm mol}$ and $L_{\rm 1.4}$, which can be represented by a power law model of the form:

$$\begin{equation}
\label{eq:A3}
 \log\left(\frac{L_{\rm 1.4}}{10^{42}\rm erg\: s^{-1}}\right) = A_3\log\left(\frac{M_{\rm mol}}{M_\odot}\right) + B_3\:,
\end{equation}$$

where $A_3$ and $B_3$ are fit parameters and we obtain $A_3=2.0$ and $B_3=-16.3$.

The presence of the correlations (equations ([\[eq:A2\]](#eq:A2)) and ([\[eq:A3\]](#eq:A3))) indicates that the short-term variability in gas supply and/or AGN activity is not strong enough to break the correlations. In Paper I we concluded that there were no correlations between $M_{\rm mol}$ and $L_{\rm col}$ and between $M_{\rm mol}$ and $L_{\rm 1.4}$[^4]. The results of the current paper suggest that the lack of correlations is simply due to the small number of sample galaxies and the narrow range of $M_{\rm mol}$.

# Discussion

## Correlations and Scatter

The results shown in Section [4](#sec:result) indicate that the mass of the circumnuclear molecular gas ($M_{\rm mol}$) is correlated not only with the jet power ($P_{\rm cav}$), but also with the continuum luminosities ($L_{\rm con}$ and $L_{\rm 1.4}$).

The power $P_{\rm cav}$ depends on the averaged AGN activity on a timescale of $\sim 10^7$ yr, while the luminosities $L_{\rm con}$ and $L_{\rm 1.4}$ are associated with recent ($\lesssim 10^3$ yr) AGN activity (Section [1](#sec:intro))[^5]. The correlations shown in Figure [4](#fig:Mmol) exhibit a scatter of about $\pm 0.5$ dex. This may indicate that the actual accretion of the cold gas is intermittent due to turbulence in the gas (cite: 2010MNRAS.408..961P; 2017MNRAS.466..677G) or precipitation (cite: 2015Natur.519..203V).

We note that the actual mass accretion rate ($\dot{M}$) or the AGN power depends not only on the mass of the circumnuclear gas ($M_{\rm mol}$), but also on other factors such as the dynamical stability of the gas around the black hole (cite: 2008ApJ...681...73K; 2022ApJ...924...24F). The cycle of variation for each factor is likely to be different. For example, in the model of (cite: 2022ApJ...924...24F), the circumnuclear gas lifetime is $\gtrsim 10^8$ yr, while the timescale of dynamical stability is $\lesssim 10^7$ yr. Smaller timescales can also affect AGN activity. For example, if the circumnuclear gas is very clumpy on a scale much smaller than the resolution of ALMA, $\dot{M}$ could fluctuate on a timescale of $< 10^7$ yr. Indeed, recent observations by (cite: 2023A&A...673A..52U) have shown that while the overall properties of the cool gas do not appear to change on timescales of $\gtrsim 10^7$ yr, AGN activity has shorter variability timescales. If this difference changes $\dot{M}/M_{\rm mol}$ by a factor of $3~(\sim 10^{0.5})$, the scatter of the correlations in Figure [4](#fig:Mmol) could be explained. Moreover, the difference in the conversion factor $X_{\rm CO}$ among galaxies could be another cause of the scatter.

The difference in black hole spin among our sample galaxies may also contribute to the scatter in the relations in Figure [4](#fig:Mmol). (cite: 2007ApJ...658..815S) showed that elliptical galaxies are systematically more radio-loud than spiral galaxies, probably because of a larger black hole spin. The angular momentum brought by the accreted cold gas can spin up the black holes. In fact, some of our sample galaxies appear to have a disk (NGC 315 and NGC 4261 in Figures [2](#fig:image) and [3](#fig:spec)), showing that the gas has angular momentum. Other galaxies may also have unresolved small disks. It will be interesting to study the relationship between disk properties and AGN power in the future.

The relationship between the amount of molecular gas around the black hole and the activity of the AGN[^6] is also known in disk galaxies (cite: 2016ApJ...827...81I). Therefore, the mechanism that fuels the AGN in elliptical galaxies may be similar to that in disk galaxies.

The NCEGs alone do not form a correlation in Figure [4](#fig:Mmol)(a) (Section [4.2](#sec:Mmol-Pcav)). Thus, it is not clear whether the $P_{\rm cav}$–$M_{\rm mol}$ relationship extends from the BCGs to the NCEGs. We need more samples to infer the correlation among the NCEGs. Although the number of the NCEG is small, the wide distribution of NCEGs in Figure [4](#fig:Mmol)(a) suggests that the potential scatter of the possible correlation is large.

## Black hole mass

Since the region we focused on (500 pc) is much smaller than the effective radii of the galaxies ($\gtrsim 10$ kpc; (cite: 2016JAsGe...5..277S)), it is unlikely that the overall properties of the galaxies directly affect $M_{\rm mol}$ and AGN activity. Instead, local properties such as the mass of the central black hole, $M_{\rm BH}$, may play some role in AGN activity. In fact, Figure [4](#fig:Mmol)(a) shows that BCGs (black marks) tend to have larger $P_{\rm cav}$, and one might think that this is a result of their larger black hole masses. Here we check this possibility.

In Figure [5](#fig:MBH-Pcav) we plot the jet power against the black hole masses $M_{\rm BH}$, which are taken from the literature and adjusted to our cosmological parameters. The masses are listed in Table [2](#tab:obs2). For all 22 galaxies, the correlation coefficient is $\tau = 0.234$, and the $p$-value is 0.13, indicating a lack of correlation. This is because some galaxies have significant uncertainties in $M_{\rm BH}$ and $P_{\rm cav}$ (Figure [5](#fig:MBH-Pcav)). Thus, there is no conclusive evidence that the mass of a black hole is a primary factor in the activity of an AGN, at least within our sample of galaxies. Of course, we do not deny a possible correlation between $M_{\rm BH}$ and $P_{\rm cav}$ for more precise data that would be obtained in the future. Since the mass of the black hole reflects the mass and velocity dispersion of the host galaxy (cite: 1998AJ....115.2285M; 2000ApJ...539L...9F), the fact that our sample galaxies have similar $M_{\rm BH}$ ($\sim 10^9\: M_\ensuremath{\odot}$) suggests that the host galaxies also have similar properties.

For AGNs not restricted to those in elliptical galaxies, a correlation between jet power and black hole mass has been reported (cite: 2006ApJ...637..669L). However, the correlation has a large scatter ($\pm 1$ dex), while $M_{\rm BH}$ spans three orders of magnitude. In addition, (cite: 2015AJ....150....8C) pointed out that the correlation between jet power and black hole mass is unclear for AGNs with low gas accretion rates (small Eddington ratios), while the correlation between jet power and accretion rate is prominent for these AGNs. This may be consistent with our results because the accretion rates to AGNs in nearby elliptical galaxies are generally small (cite: 2006ApJ...652...216R).

## The origin of the mm/submm continuum emission

We found the correlation between $M_{\rm mol}$ and continuum emission in section [4.3](#sec:cont). The origin of the continuum emission reflects what kind of matter is present around the AGNs. In Figure [6](#fig:SED) we show the ratio of $F_{\rm con}/F_{\rm 1.4}$. With the exception of NGC 5044, the ratio is less than one, indicating that most of the continuum emission is synchrotron emission from relativistic electrons. In addition, we show a possible continuum spectrum (solid line), which is assumed to be represented by a combination of power-law (synchrotron) and modified blackbody (dust) components:

$$\begin{equation}
 S(\nu) = N_{\rm AGN}\nu^{\gamma} + N_{\rm BB}(1-e^{-(\nu/\nu_0)^b})B_\nu(\nu,T)\:,
\end{equation}$$

where $\gamma=-0.75$, $\nu_0=1.5$ THz, $b=1.5$, and $B_\nu(\nu,T)$ is a blackbody distribution (cite: 2019A&A...621A..27F). The dust temperature is assumed to be $T=10$ K ((cite: 2019ApJ...879..103F); see Paper I). The values for $N_{\rm AGN}$ and $N_{\rm BB}$ are adjusted to match the observations of NGC 5044. Figure [6](#fig:SED) shows that, except for NGC 5044, the effect of the dust component is minimal at frequencies around 100–300 GHz, in agreement with local AGN observations (cite: 2022ApJ...938...87K). A t-test shows that the ratios of $F_{\rm con}/F_{\rm 1.4}$ for the NCEGs are statistically indistinguishable from those for the BCGs. In Paper I we discussed that galaxies with smaller $L_{\rm 1.4}$ may have a larger contribution from dust emission at $\sim 100$–300 GHz, because $L_{\rm con}/L_{\rm 1.4}\propto L_{\rm 1.4}^{-0.57}$. However, for the extended sample in this paper, the relationship is $L_{\rm con}/L_{\rm 1.4}\propto L_{\rm 1.4}^{-0.01}$, and the trend disappears.

# Conclusion

Cold molecular gas has been observed in elliptical galaxies, and it is likely that this gas fuels their AGNs. To confirm this speculation, we measured the masses of the gas around the AGNs and discussed their relation to AGN activity. In this study, we extend the sample of galaxies studied in Paper I to lower masses.

Using ALMA data, we studied the CO line emission within 500 pc of the center of 12 NCEGs plus one BCG, and detected the emission in 6 of them. We estimated the mass of the molecular gas $M_{\rm mol}$ from the emission and combined the results with those of 9 BCGs studied in Paper I. We found that $M_{\rm mol}$ is correlated with the jet power of the central AGN ($P_{\rm cav}$), which is given by $P_{\rm cav}\approx 4.1\times 10^{42}(M_{\rm mol}/10^7\: M_\ensuremath{\odot})^{1.3}\rm\: erg\: s^{-1}$, although NCEGs alone do not show the correlation. This suggests that AGNs are powered by molecular gas. Moreover, $M_{\rm mol}$ is also correlated with the continuum luminosity of AGNs at $\sim 1.4$ GHz and $\sim 100$–300 GHz. Since $P_{\rm cav}$ reflects long-term AGN activity, while the luminosity of the continuum indicates short-term AGN activity, our findings suggest that the amount of gas is a critical factor that affects AGN activity, regardless of the temporal scale.

On the other hand, we cannot find a clear relationship between the mass of black holes in AGNs ($M_{\rm BH}$) and $P_{\rm cav}$. This may be due to the large uncertainties in the data, but it suggests that $M_{\rm mol}$, rather than $M_{\rm BH}$, is the primary factor influencing AGN activity. We confirm that synchrotron radiation is mostly responsible for the continuum emission from AGNs at $\sim 1.4$–300 GHz.

In galaxy formation studies, different models of gas accretion onto black holes have been adopted. For example, the Bondi accretion model is used in the Illustris simulations (cite: 2015MNRAS.452..575S). Some semi-analytical models of galaxy formation use an empirical model of cold gas accretion (cite: 2014ApJ...794...69E). The simple correlation we found between $M_{\rm mol}$ and $P_{\rm cav}$ could be used instead of these models.

We thank the reviewer and the statistician of AAS Journals for their useful comments. We also thank the EA ALMA Regional Center (EA-ARC) for their support. This work was supported by NAOJ ALMA Scientific Research Grant Code 2022-21A, and JSPS KAKENHI Grant Number JP22H01268, JP22H00158, JP22K03624 (Y.F.), JP20K14531, JP21H04496 (T.I.), JP19K03918 (N.Kawakatu), JP21H01137, JP18K03709 (H.N.), JP22K03686 (N.Kawanaka). This paper makes use of the following ALMA data: ADS/JAO.2011.0.00735.S, ADS/JAO.2012.1.00837.S, ADS/JAO.2013.1.00073.S, ADS/JAO.2013.1.00828.S, ADS/JAO2015.1.00598.S, ADS/JAO.2015.1.00623.S, ADS/JAO.2015.1.00627.S, ADS/JAO.2015.1.00644.S, ADS/JAO.2015.1.00860.S, ADS/JAO.2015.1.00971.S, ADS/JAO.2015.1.01198.S, ADS/JAO.2016.1.01214.S, ADS/JAO.2015.1.01572.S, ADS/JAO.2016.1.00683.S, ADS/JAO.2016.1.01135.S, ADS/JAO.2017.1.00301.S, ADS/JAO.2017.1.00830.S, ADS/JAO.2019.1.00036.S, ADS/JAO.2019.1.01845.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Target | $S_{\rm CO}\Delta v$ | $M_{\rm mol}$ | $P_{\rm cav}$$^*$ | $\nu_{\rm con}$ | $F_{\rm con}$ | $L_{\rm con}$ | $F_{\rm 1.4}$$^\dagger$ | $L_{\rm 1.4}$ | $M_{\rm BH}$$^\ddagger$ |
|  | ($\rm mJy bm^{-1} km s^{-1}$) | ($10^7\: M_\odot$) | $(10^{42}\rm\: erg^{-1})$ | (GHz) | (mJy) | $(10^{42}\rm\: erg^{-1})$ | (mJy) | $(10^{42}\rm\: erg^{-1})$ | ($10^8\: M_\odot$) |
| NGC 4636 | $140\pm 31$ | $0.0087\pm 0.0018$ | $2.76_{-0.91}^{+0.56}$$^a$ | 221.8 | $0.483\pm 0.032$ | $(2.0\pm 0.1)\times 10^{-5}$ | $77.8\pm 2.8$$^d$ | $(2.4\pm 0.1)\times 10^{-5}$ | $3.7_{-1.5}^{+2.4}$$^h$ |
| NGC 4472 | $<12700$ | $<0.82$ | $0.53_{-0.32}^{+0.16}$$^a$ | 351.2 | $0.228\pm 0.039$ | $(1.4\pm 0.2)\times 10^{-5}$ | $220\pm 8$$^d$ | $(7.3\pm 0.3)\times 10^{-5}$ | $20_{-1}^{+2}$$^i$ |
| NGC 4374 | $3620\pm 590$ | $0.25\pm 0.15$ | $5.03_{-2.53}^{+2.17}$$^a$ | 236.9 | $127.9\pm 5.2$ | $(6.5\pm 0.3)\times 10^{-3}$ | $6100\pm 150$$^e$ | $(2.2\pm 0.1)\times 10^{-3}$ | $7.2_{-0.7}^{+0.8}$$^j$ |
| NGC 5846 | $<1930$ | $<0.38$ | $0.88_{-0.59}^{+0.30}$$^a$ | 221.3 | $10.46\pm 0.31$ | $(1.4\pm 0.0)\times 10^{-3}$ | $21\pm 1$$^d$ | $(2.1\pm 0.1)\times 10^{-5}$ | $11_{-1}^{+1}$$^k$ |
| NGC 1316 | $673\pm 230$ | $0.47\pm 0.16$ | $1.11_{-0.40}^{+0.26}$$^a$ | 106.9 | $9.06\pm 0.15$ | $(7.8\pm 0.1)\times 10^{-4}$ | $25\pm 10$$^d$ | $(2.9\pm 0.1)\times 10^{-4}$ | $2.1_{-1.1}^{+1.0}$$^k$ |
| NGC 5813 | $<1230$ | $<0.32$ | $3.97_{-2.36}^{+1.02}$$^a$ | 236 | $2.26\pm 0.11$ | $(4.3\pm 0.2)\times 10^{-4}$ | $14.8\pm 1.0$$^d$ | $(2.0\pm 0.1)\times 10^{-5}$ | $6.0_{-0.6}^{+0.6}$$^k$ |
| NGC 4261 | $8140\pm 290$ | $2.6\pm 0.1$ | $0.91_{-0.79}^{+0.37}$$^a$ | 235.6 | $459\pm 48$ | $0.11\pm 0.01$ | $10400\pm 200$$^e$ | $(1.7\pm 0.0)\times 10^{-2}$ | $17_{-3}^{+4}$$^l$ |
| NGC 7626 | $<842$ | $<2.7$ | $0.39_{-0.18}^{+0.09}$$^a$ | 234.1 | $18.96\pm 0.58$ | $(1.1\times 0.0)\times 10^{-2}$ | $265\pm 8$$^d$ | $(1.1\pm 0.0)\times 10^{-3}$ | $4.8_{-2.6}^{+5.5}$$^h$ |
| IC 4296 | $630\pm 195$ | $0.93\pm 0.18$ | $3.87_{-3.03}^{+1.44}$$^a$ | 233.8 | $214\pm 12$ | $0.15\pm 0.01$ | $2420\pm 50$$^e$ | $(1.2\pm 0.0)\times 10^{-2}$ | $14_{-2}^{+2}$$^m$ |
| NGC 1600 | $<1560$ | $<1.0$ | $1.87_{-0.82}^{+0.82}$$^a$ | 340.5 | $< 0.270$ | $<3.8\times 10^{-4}$ | $61.6\pm 2.6$$^d$ | $(4.7\pm 0.2)\times 10^{-4}$ | $170_{-20}^{+20}$$^n$ |
| NGC 507 | $<2010$ | $<3.3$ | $19.9_{-6.8}^{+4.4}$$^a$ | 234.9 | $0.945\pm 0.07$ | $(1.1\pm 0.1)\times 10^{-3}$ | $99.5\pm 1.5$$^f$ | $(8.5\pm 0.1)\times 10^{-4}$ | $1.8_{-0.0}^{+0.0}$$^o$ |
| NGC 315 | $18000\pm 445$ | $30\pm 1$ | $6.58_{-4.96}^{+2.48}$$^a$ | 233.6 | $270\pm 13$ | $0.32\pm 0.02$ | $772\pm 25$$^d$ | $(6.6\pm 0.2)\times 10^{-3}$ | $21_{-1}^{+3}$$^l$ |
| M 87 | $<5290$ | $<0.59$ | $6.0_{-0.9}^{+4.2}$$^b$$^e$ | 222.8 | $1807\pm 78$ | $0.14\pm 0.01$ | $147000\pm 5000$$^e$ | $(8.4\pm 0.3)\times 10^{-2}$ | $71_{-8}^{+8}$$^p$ |
| NGC 5044 | $517\pm 71$ | $2.0 \pm 0.2$ | $4.2_{-2.0}^{+1.2}$$^c$ | 235 .2 | $49.5 \pm 3.7$ | $(1.9\pm 0.1)\times 10^{-2}$ | $34.7\pm 1.1$$^d$ | $(9.3\pm 0.3)\times 10^{-5}$ | $6.0_{-3.0}^{+12.0}$$^q$ |
| Centaurus | $208 \pm 37$ | $1.1 \pm 0.2$ | $7.4_{-1.8}^{+5.8}$$^b$ | 107 .1 | $51.6 \pm 2.6$ | $(1.2\pm 0.1)^{-2}$ | $3980\pm 110$$^g$ | $(1.2\pm 0.0)\times 10^{-2}$ | $31_{-1}^{+1}$$^r$ |
| Abell 262 | $1420\pm 100$ | $24 \pm 2$ | $9.7_{-2.6}^{+7.5}$$^c$ | 235 .6 | $3.336 \pm 0.069$ | $(3.9\pm 0.1)\times 10^{-3}$ | $65.7\pm 2.3$$^d$ | $(5.4\pm 0.2)\times 10^{-4}$ | $21_{-1}^{+1}$$^r$ |
| Abell 3581 | $111\pm 25$ | $2.9 \pm 0.7$ | $3.1$$^c$ | 231 .8 | $107.5 \pm 3.7$ | $0.23\pm 0.01$ | $646\pm 23$$^d$ | $(9.7\pm 0.3)\times 10^{-3}$ | $15_{-3}^{+3}$$^r$ |
| Abell 2052 | $43 \pm 11$ | $5.4 \pm 1.5$ | $150_{-70}^{+200}$$^c$ | 229 .5 | $34.3 \pm 3.1$ | $0.18\pm 0.02$ | $5500\pm 210$$^d$ | $(2.1\pm 0.1)\times 10^{-1}$ | $14_{-8}^{+30}$$^q$ |
| 2A0335+096 | $262 \pm 63$ | $6.1 \pm 1.5$ | $24_{-6}^{+23}$$^b$ | 110 .5 | $6.01 \pm 0.34$ | $(2.0\pm 0.1)\times 10^{-2}$ | $36.7\pm 1.8$$^d$ | $(1.6\pm 0.1)\times 10^{-3}$ | $12_{-7}^{+27}$$^q$ |
| Hydra A | $460\pm 26$ | $42 \pm 2$ | $430_{-50}^{+200}$$^c$ | 227 .6 | $65.23 \pm 0.19$ | $0.87\pm 0.0$ | $40800\pm 1300$$^d$ | $4.0\pm 0.1$ | $31_{-1}^{+1}$$^r$ |
| Abell 1795 | $654\pm 93$ | $15 \pm 2$ | $160_{-50}^{+230}$$^b$ | 225 .8 | $3.29 \pm 0.041$ | $(6.0\pm 0.1)\times 10^{-2}$ | $925\pm 28$$^d$ | $(1.2\pm 0.0)\times 10^{-1}$ | $60_{-4}^{+4}$$^r$ |
| PKS 0745-191 | $353 \pm 49$ | $39 \pm 5$ | $1700_{-300}^{+1400}$$^c$ | 314 .6 | $5.03 \pm 0.35$ | $0.32\pm 0.02$ | $2370\pm 80$$^d$ | $(8.6\pm 0.3)\times 10^{-1}$ | $22_{-11}^{+46}$$^q$ |

: Target and observation details

Table notes: Galaxies from NGC 4636 to NGC 315 are NCEGs and those from M 87 to PKS 0745-191 are BCGs.

($p$) (cite: 2019ApJ...875L...1E), ($q$) (cite: 2017MNRAS.464.4360M), ($r$) (cite: 2018MNRAS.474.1342M).

natexlab

(ref: 2006MNRAS.372...21A) Allen, S. W., Dunn, R. J. H., Fabian, A. C., Taylor, G. B., & Reynolds, C. S. 2006, MNRAS, 372, 21, doi: [`10.1111/j.1365-2966.2006.10778.x`](http://doi.org/10.1111/j.1365-2966.2006.10778.x)

(ref: 2014MNRAS.440..696A) Allison, J. R., Sadler, E. M., & Meekin, A. M. 2014, MNRAS, 440, 696, doi: [`10.1093/mnras/stu289`](http://doi.org/10.1093/mnras/stu289)

(ref: 2004ApJ...607..800B) Bı̂rzan, L., Rafferty, D. A., McNamara, B. R., Wise, M. W., & Nulsen, P. E. J. 2004, ApJ, 607, 800, doi: [`10.1086/383519`](http://doi.org/10.1086/383519)

(ref: 2017ApJ...845..170B) Boizelle, B. D., Barth, A. J., Darling, J., et al. 2017, ApJ, 845, 170, doi: [`10.3847/1538-4357/aa8266`](http://doi.org/10.3847/1538-4357/aa8266)

(ref: 2021ApJ...908...19B) Boizelle, B. D., Walsh, J. L., Barth, A. J., et al. 2021, ApJ, 908, 19, doi: [`10.3847/1538-4357/abd24d`](http://doi.org/10.3847/1538-4357/abd24d)

(ref: 2013ARA&A..51..207B) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: 1952MNRAS.112..195B) Bondi, H. 1952, MNRAS, 112, 195, doi: [`10.1093/mnras/112.2.195`](http://doi.org/10.1093/mnras/112.2.195)

(ref: 2010ApJ...720.1066C) Cavagnolo, K. W., McNamara, B. R., Nulsen, P. E. J., et al. 2010, ApJ, 720, 1066, doi: [`10.1088/0004-637X/720/2/1066`](http://doi.org/10.1088/0004-637X/720/2/1066)

(ref: 2015AJ....150....8C) Chen, Y.-Y., Zhang, X., Xiong, D., & Yu, X. 2015, AJ, 150, 8, doi: [`10.1088/0004-6256/150/1/8`](http://doi.org/10.1088/0004-6256/150/1/8)

(ref: 1998AJ....115.1693C) Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693, doi: [`10.1086/300337`](http://doi.org/10.1086/300337)

(ref: 2009ApJ...690..537D) Dalla Bontà, E., Ferrarese, L., Corsini, E. M., et al. 2009, ApJ, 690, 537, doi: [`10.1088/0004-637X/690/1/537`](http://doi.org/10.1088/0004-637X/690/1/537)

(ref: 2014ApJ...792...94D) David, L. P., Lim, J., Forman, W., et al. 2014, ApJ, 792, 94, doi: [`10.1088/0004-637X/792/2/94`](http://doi.org/10.1088/0004-637X/792/2/94)

(ref: 2001MNRAS.328..762E) Edge, A. C. 2001, MNRAS, 328, 762, doi: [`10.1046/j.1365-8711.2001.04802.x`](http://doi.org/10.1046/j.1365-8711.2001.04802.x)

(ref: 2023arXiv231117848E) Elford, J. S., Davis, T. A., Ruffa, I., et al. 2023, arXiv e-prints, arXiv:2311.17848, doi: [`10.48550/arXiv.2311.17848`](http://doi.org/10.48550/arXiv.2311.17848)

(ref: 2014ApJ...794...69E) Enoki, M., Ishiyama, T., Kobayashi, M. A. R., & Nagashima, M. 2014, ApJ, 794, 69, doi: [`10.1088/0004-637X/794/1/69`](http://doi.org/10.1088/0004-637X/794/1/69)

(ref: 2019ApJ...875L...1E) Event Horizon Telescope Collaboration, e. a. 2019, ApJL, 875, L1, doi: [`10.3847/2041-8213/ab0ec7`](http://doi.org/10.3847/2041-8213/ab0ec7)

(ref: 1989ARA&A..27...87F) Fabbiano, G. 1989, ARA&A, 27, 87, doi: [`10.1146/annurev.aa.27.090189.000511`](http://doi.org/10.1146/annurev.aa.27.090189.000511)

(ref: 2019A&A...621A..27F) Falkendal, T., De Breuck, C., Lehnert, M. D., et al. 2019, A&A, 621, A27, doi: [`10.1051/0004-6361/201732485`](http://doi.org/10.1051/0004-6361/201732485)

(ref: 2000ApJ...539L...9F) Ferrarese, L., & Merritt, D. 2000, ApJL, 539, L9, doi: [`10.1086/312838`](http://doi.org/10.1086/312838)

(ref: 2019ApJ...879..103F) Fogarty, K., Postman, M., Li, Y., et al. 2019, ApJ, 879, 103, doi: [`10.3847/1538-4357/ab22a4`](http://doi.org/10.3847/1538-4357/ab22a4)

(ref: 2023arXiv230316927F) Fujita, Y., Izumi, T., Kawakatu, N., et al. 2023, arXiv e-prints, arXiv:2303.16927, doi: [`10.48550/arXiv.2303.16927`](http://doi.org/10.48550/arXiv.2303.16927)

(ref: 2022ApJ...924...24F) Fujita, Y., Kawakatu, N., & Nagai, H. 2022, ApJ, 924, 24, doi: [`10.3847/1538-4357/ac31a6`](http://doi.org/10.3847/1538-4357/ac31a6)

(ref: 2017MNRAS.465L..94F) Fujita, Y., & Nagai, H. 2017, MNRAS, 465, L94, doi: [`10.1093/mnrasl/slw217`](http://doi.org/10.1093/mnrasl/slw217)

(ref: 2015A&A...579A..62G) Gaspari, M., Brighenti, F., & Temi, P. 2015, A&A, 579, A62, doi: [`10.1051/0004-6361/201526151`](http://doi.org/10.1051/0004-6361/201526151)

(ref: 2017MNRAS.466..677G) Gaspari, M., Temi, P., & Brighenti, F. 2017, MNRAS, 466, 677, doi: [`10.1093/mnras/stw3108`](http://doi.org/10.1093/mnras/stw3108)

(ref: 2013ApJ...764..151G) Graham, A. W., & Scott, N. 2013, ApJ, 764, 151, doi: [`10.1088/0004-637X/764/2/151`](http://doi.org/10.1088/0004-637X/764/2/151)

(ref: 2014ARA&A..52..589H) Heckman, T. M., & Best, P. N. 2014, ARA&A, 52, 589, doi: [`10.1146/annurev-astro-081913-035722`](http://doi.org/10.1146/annurev-astro-081913-035722)

(ref: NADAbook) Helsel, D. R. 2004, Nondetects and Data Analysis : Statistics for Censored Environmental Data (Wiley-Interscience)

(ref: 2016ApJ...827...81I) Izumi, T., Kawakatu, N., & Kohno, K. 2016, ApJ, 827, 81, doi: [`10.3847/0004-637X/827/1/81`](http://doi.org/10.3847/0004-637X/827/1/81)

(ref: 2008ApJ...681...73K) Kawakatu, N., & Wada, K. 2008, ApJ, 681, 73, doi: [`10.1086/588574`](http://doi.org/10.1086/588574)

(ref: 2022ApJ...938...87K) Kawamuro, T., Ricci, C., Imanishi, M., et al. 2022, ApJ, 938, 87, doi: [`10.3847/1538-4357/ac8794`](http://doi.org/10.3847/1538-4357/ac8794)

(ref: 2021ApJ...920L..24K) Kino, M., Niinuma, K., Kawakatu, N., et al. 2021, ApJL, 920, L24, doi: [`10.3847/2041-8213/ac24fa`](http://doi.org/10.3847/2041-8213/ac24fa)

(ref: 2013ARA&A..51..511K) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: 1981AandAS...45..367K) Kuehr, H., Witzel, A., Pauliny-Toth, I. I. K., & Nauber, U. 1981, A&AS, 45, 367

(ref: 2006ApJ...637..669L) Liu, Y., Jiang, D. R., & Gu, M. F. 2006, ApJ, 637, 669, doi: [`10.1086/498639`](http://doi.org/10.1086/498639)

(ref: 1998AJ....115.2285M) Magorrian, J., Tremaine, S., Richstone, D., et al. 1998, AJ, 115, 2285, doi: [`10.1086/300353`](http://doi.org/10.1086/300353)

(ref: 2017MNRAS.464.4360M) Main, R. A., McNamara, B. R., Nulsen, P. E. J., Russell, H. R., & Vantyghem, A. N. 2017, MNRAS, 464, 4360, doi: [`10.1093/mnras/stw2644`](http://doi.org/10.1093/mnras/stw2644)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2014ApJ...785...44M) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2014, ApJ, 785, 44, doi: [`10.1088/0004-637X/785/1/44`](http://doi.org/10.1088/0004-637X/785/1/44)

(ref: 2018ApJ...860....9M) Meyer, E. T., Petropoulou, M., Georganopoulos, M., et al. 2018, ApJ, 860, 9, doi: [`10.3847/1538-4357/aabf39`](http://doi.org/10.3847/1538-4357/aabf39)

(ref: 2018MNRAS.474.1342M) Mezcua, M., Hlavacek-Larrondo, J., Lucey, J. R., et al. 2018, MNRAS, 474, 1342, doi: [`10.1093/mnras/stx2812`](http://doi.org/10.1093/mnras/stx2812)

(ref: 2019PASJ...71...85M) Morokuma-Matsui, K., Serra, P., Maccagni, F. M., et al. 2019, PASJ, 71, 85, doi: [`10.1093/pasj/psz067`](http://doi.org/10.1093/pasj/psz067)

(ref: 2011AandA...526A.148M) Murgia, M., Parma, P., Mack, K. H., et al. 2011, A&A, 526, A148, doi: [`10.1051/0004-6361/201015302`](http://doi.org/10.1051/0004-6361/201015302)

(ref: 2017ApJ...849...52N) Nagai, H., Fujita, Y., Nakamura, M., et al. 2017, ApJ, 849, 52, doi: [`10.3847/1538-4357/aa8e43`](http://doi.org/10.3847/1538-4357/aa8e43)

(ref: 2010PASJ...62L..11N) Nagai, H., Suzuki, K., Asada, K., et al. 2010, PASJ, 62, L11, doi: [`10.1093/pasj/62.2.L11`](http://doi.org/10.1093/pasj/62.2.L11)

(ref: 2019ApJ...883..193N) Nagai, H., Onishi, K., Kawakatu, N., et al. 2019, ApJ, 883, 193, doi: [`10.3847/1538-4357/ab3e6e`](http://doi.org/10.3847/1538-4357/ab3e6e)

(ref: 2021MNRAS.503.5179N) North, E. V., Davis, T. A., Bureau, M., et al. 2021, MNRAS, 503, 5179, doi: [`10.1093/mnras/stab793`](http://doi.org/10.1093/mnras/stab793)

(ref: 2019A&A...631A..22O) Olivares, V., Salome, P., Combes, F., et al. 2019, A&A, 631, A22, doi: [`10.1051/0004-6361/201935350`](http://doi.org/10.1051/0004-6361/201935350)

(ref: 2011ApJ...735...11O) O’Sullivan, E., Giacintucci, S., David, L. P., et al. 2011, ApJ, 735, 11, doi: [`10.1088/0004-637X/735/1/11`](http://doi.org/10.1088/0004-637X/735/1/11)

(ref: 2019ApJ...875..141P) Phipps, F., Bogdán, Á., Lovisari, L., et al. 2019, ApJ, 875, 141, doi: [`10.3847/1538-4357/ab107c`](http://doi.org/10.3847/1538-4357/ab107c)

(ref: 2010MNRAS.408..961P) Pizzolato, F., & Soker, N. 2010, MNRAS, 408, 961, doi: [`10.1111/j.1365-2966.2010.17156.x`](http://doi.org/10.1111/j.1365-2966.2010.17156.x)

(ref: 2018ApJ...853..177P) Pulido, F. A., McNamara, B. R., Edge, A. C., et al. 2018, ApJ, 853, 177, doi: [`10.3847/1538-4357/aaa54b`](http://doi.org/10.3847/1538-4357/aaa54b)

(ref: 2006ApJ...652...216R) Rafferty, D. A., McNamara, B. R., Nulsen, P. E. J., & Wise, M. W. 2006, ApJ, 652, 216, doi: [`10.1086/507672`](http://doi.org/10.1086/507672)

(ref: 2019MNRAS.485..229R) Rose, T., Edge, A. C., Combes, F., et al. 2019, MNRAS, 485, 229, doi: [`10.1093/mnras/stz406`](http://doi.org/10.1093/mnras/stz406)

(ref: 2020MNRAS.496..364R) —. 2020, MNRAS, 496, 364, doi: [`10.1093/mnras/staa1474`](http://doi.org/10.1093/mnras/staa1474)

(ref: 2023MNRAS.518..878R) Rose, T., McNamara, B. R., Combes, F., et al. 2023, MNRAS, 518, 878, doi: [`10.1093/mnras/stac3194`](http://doi.org/10.1093/mnras/stac3194)

(ref: 2019MNRAS.484.4239R) Ruffa, I., Prandoni, I., Laing, R. A., et al. 2019, MNRAS, 484, 4239, doi: [`10.1093/mnras/stz255`](http://doi.org/10.1093/mnras/stz255)

(ref: 2022ApJ...924..133R) Runburg, J., Farrah, D., Sajina, A., et al. 2022, ApJ, 924, 133, doi: [`10.3847/1538-4357/ac37b8`](http://doi.org/10.3847/1538-4357/ac37b8)

(ref: 2013AJ....146...45R) Rusli, S. P., Thomas, J., Saglia, R. P., et al. 2013, AJ, 146, 45, doi: [`10.1088/0004-6256/146/3/45`](http://doi.org/10.1088/0004-6256/146/3/45)

(ref: 2013MNRAS.432..530R) Russell, H. R., McNamara, B. R., Edge, A. C., et al. 2013, MNRAS, 432, 530, doi: [`10.1093/mnras/stt490`](http://doi.org/10.1093/mnras/stt490)

(ref: 2016MNRAS.458.3134R) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2016, MNRAS, 458, 3134, doi: [`10.1093/mnras/stw409`](http://doi.org/10.1093/mnras/stw409)

(ref: 2017MNRAS.472.4024R) —. 2017, MNRAS, 472, 4024, doi: [`10.1093/mnras/stx2255`](http://doi.org/10.1093/mnras/stx2255)

(ref: 2019MNRAS.490.3025R) —. 2019, MNRAS, 490, 3025, doi: [`10.1093/mnras/stz2719`](http://doi.org/10.1093/mnras/stz2719)

(ref: 2003A&A...412..657S) Salomé, P., & Combes, F. 2003, A&A, 412, 657, doi: [`10.1051/0004-6361:20031438`](http://doi.org/10.1051/0004-6361:20031438)

(ref: 2016JAsGe...5..277S) Samir, R. M., Reda, F. M., Shaker, A. A., Osman, A. M. I., & Amin, M. Y. 2016, NRIAG Journal of Astronomy and Geophysics, 5, 277, doi: [`10.1016/j.nrjag.2016.06.004`](http://doi.org/10.1016/j.nrjag.2016.06.004)

(ref: 2022A&A...664L..11S) Sawada-Satoh, S., Kameno, S., & Trippe, S. 2022, A&A, 664, L11, doi: [`10.1051/0004-6361/202244047`](http://doi.org/10.1051/0004-6361/202244047)

(ref: 2020ApJ...894...72S) Schellenberger, G., David, L. P., Vrtilek, J., et al. 2020, ApJ, 894, 72, doi: [`10.3847/1538-4357/ab879c`](http://doi.org/10.3847/1538-4357/ab879c)

(ref: 2015MNRAS.452..575S) Sijacki, D., Vogelsberger, M., Genel, S., et al. 2015, MNRAS, 452, 575, doi: [`10.1093/mnras/stv1340`](http://doi.org/10.1093/mnras/stv1340)

(ref: 2007ApJ...658..815S) Sikora, M., Stawarz, Ł., & Lasota, J.-P. 2007, ApJ, 658, 815, doi: [`10.1086/511972`](http://doi.org/10.1086/511972)

(ref: 2018MNRAS.475.3004S) Simionescu, A., Tremblay, G., Werner, N., et al. 2018, MNRAS, 475, 3004, doi: [`10.1093/mnras/sty047`](http://doi.org/10.1093/mnras/sty047)

(ref: 2018ApJ...858...17T) Temi, P., Amblard, A., Gitti, M., et al. 2018, ApJ, 858, 17, doi: [`10.3847/1538-4357/aab9b0`](http://doi.org/10.3847/1538-4357/aab9b0)

(ref: 2022ApJ...928..150T) Temi, P., Gaspari, M., Brighenti, F., et al. 2022, ApJ, 928, 150, doi: [`10.3847/1538-4357/ac5036`](http://doi.org/10.3847/1538-4357/ac5036)

(ref: 2016Natur.532..340T) Thomas, J., Ma, C.-P., McConnell, N. J., et al. 2016, Nature, 532, 340, doi: [`10.1038/nature17197`](http://doi.org/10.1038/nature17197)

(ref: 2016Natur.534..218T) Tremblay, G. R., Oonk, J. B. R., Combes, F., et al. 2016, Nature, 534, 218, doi: [`10.1038/nature17969`](http://doi.org/10.1038/nature17969)

(ref: 2023A&A...673A..52U) Ubertosi, F., Gitti, M., Brighenti, F., et al. 2023, A&A, 673, A52, doi: [`10.1051/0004-6361/202345894`](http://doi.org/10.1051/0004-6361/202345894)

(ref: 2016ApJ...831..134V) van den Bosch, R. C. E. 2016, ApJ, 831, 134, doi: [`10.3847/0004-637X/831/2/134`](http://doi.org/10.3847/0004-637X/831/2/134)

(ref: 2016ApJ...832..148V) Vantyghem, A. N., McNamara, B. R., Russell, H. R., et al. 2016, ApJ, 832, 148, doi: [`10.3847/0004-637X/832/2/148`](http://doi.org/10.3847/0004-637X/832/2/148)

(ref: 2017ApJ...848..101V) Vantyghem, A. N., McNamara, B. R., Edge, A. C., et al. 2017, ApJ, 848, 101, doi: [`10.3847/1538-4357/aa8fd0`](http://doi.org/10.3847/1538-4357/aa8fd0)

(ref: 2015Natur.519..203V) Voit, G. M., Donahue, M., Bryan, G. L., & McDonald, M. 2015, Nature, 519, 203, doi: [`10.1038/nature14167`](http://doi.org/10.1038/nature14167)

(ref: 2010ApJ...721..762W) Walsh, J. L., Barth, A. J., & Sarzi, M. 2010, ApJ, 721, 762, doi: [`10.1088/0004-637X/721/1/762`](http://doi.org/10.1088/0004-637X/721/1/762)

[^1]: There is no strict distinction between NCEGs and BCGs. Here we refer to massive elliptical galaxies at the center of known clusters as BCGs, and others as NCEGs.

[^2]: We will refer to them as CO(1-0), CO(2-1), and CO(3-2).

[^3]: https://cran.r-project.org/web/packages/NADA/index.html

[^4]: While the Pearson correlation coefficient was used in Paper I, the Kendall rank correlation coefficient also rejects correlations.

[^5]: This does not necessarily mean that the luminosities are changing on a timescale of $\lesssim 10^3$ yr.

[^6]: Recently, (cite: 2023arXiv231117848E) indicated that the circumnuclear molecular gas mass does not correlate with AGN activity. As they pointed out, the difference from our results could be explained by the difference in the samples. While our sample is limited to elliptical galaxies, their sample includes a wide range of galaxies and AGN activity.

</paper>

Write the methods card for this paper.