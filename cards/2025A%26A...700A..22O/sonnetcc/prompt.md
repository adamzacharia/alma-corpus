# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...700A..22O\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...700A..22O",
 "title": "The changing impact of radio jets as they evolve: The view from the cold gas",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Oosterloo, Tom",
 "n_authors": 6,
 "arxiv_id": "2506.20448",
 "doi": "10.1051/0004-6361/202554536",
 "alma_projects_linked_by_archive": [
  "2022.1.01498.S"
 ]
}
```

Paper text:
<paper>
# The changing impact of radio jets as they evolve:\
The view from the cold gas

We present ALMA CO(1-0) and CO(3-2) observations of a powerful young radio galaxy, PKS 0023$-$26, that is hosted by a far-infrared bright galaxy. The galaxy has a luminous optical active galactic nucleus (AGN) and a very extended distribution of molecular gas. We used these observations (together with available ALMA CO(2-1) data) to trace the impact of the active nucleus across the extent of the radio emission and beyond on scales of a few kiloparsec (kpc). Despite the strength of the optical AGN, the kinematics of the cold molecular gas is strongly affected only in the central kpc, and it is more weakly affected around the northern lobe. We found other signatures of the substantial impact of the radio AGN, however. Most notably, the extreme line ratios of the CO transitions in a region that is aligned with the radio axis indicate conditions that are very different from those observed in the undisturbed gas at large radii. The non-detection of CO(1-0) at the location of the core of the radio source implies extreme conditions at this location. Furthermore, on the scale of a few kpc, the cold molecular gas appears to be wrapped around the northern radio lobe. This suggests that a strong jet-cloud interaction has depleted the northern lobe of molecular gas, perhaps as a result of the hot wind behind the jet-induced shock that shreds the clouds via hydrodynamic instabilities. The higher gas velocity dispersion and molecular excitation that we observed close to this location may then be the result of a milder interaction in which the expanding jet cocoon induces turbulence in the surrounding interstellar medium. These results highlight that the impact of an AGN can manifest itself not only in the kinematics of the gas, but also in molecular line ratios and in the distribution of the gas. The work also highlights that it is important to spatially resolve the gas throughout the radio source to trace different modes of AGN feedback that can coexist. Although the radio plasma and the cold molecular gas are clearly coupled, the kinetic energy that is transferred to the interstellar medium is only a small fraction of the energy available from the AGN.

# Introduction

As a result of the wide range of sizes they cover, radio jets have the potential to impact the surrounding medium on scales from parsec (pc) to hundreds of kiloparsec (kpc), from the circumnuclear- and interstellar medium (ISM) to the intergalactic medium (IGM). On galaxy cluster scales, this has been shown by studies of the cavities in the hot X-ray emitting gas that is created by the radio jets in cool-core clusters (bright cluster galaxies; BCG) and by measuring their lifting power (e.g. (cite: McNamara16; Russell19; Tamhane22)). On the other hand, we also know that radio jets can impact their surrounding medium already at an earlier stage on small scales (pc to kpc) in the circumnuclear regions of galaxies. In particular, young jets can drive fast outflows and increase the turbulence of the surrounding gas. This has been shown by several studies that traced warm ionised gas (e.g. (cite: Holt08; Santoro20)) as well as the cold and warm molecular component (e.g. (cite: Guillard12; Tadhunter14; Murthy22; Ruffa24; Cresci23; Costa24)). As in the case of radiation-driven outflows, however, most of the most massive cold-gas outflows that are driven by radio jets have been found in regions that are limited to the inner kpc, and the connection of the impact of jets on small scales to what is seen on large scales is still unclear.

The predictions from numerical simulations are interesting in this context. According to these simulations of jets that expand in a clumpy medium ((cite: Sutherland07; Mukherjee16; Mukherjee18a; Tanner22; Dutta24)), the initial direct interaction of the jet with the cloud does not only produce gas outflows, but also a cocoon of shocked material that is filled with expanding dense gas around the jet. Crucially, this cocoon also expands in a direction perpendicular to the jet, which ensures that a large volume of the ISM and not just the immediate surroundings of the jet is indirectly affected by the radio plasma. The energy is injected via the continual dissipation from the several interactions of the jets with the surrounding clouds, which drives the expansion of the cocoon and results in a high turbulence of the gas. The impact of this bubble may become dominant when the radio source grows and breaks out from the central regions (cite: Mukherjee16; Mukherjee18a). Although the characteristics of the bubble depend, among other factors, on the jet power (low-power jets interact for a longer time with the surrounding medium), the bubble of shocked gas can ensure that the energy released from the radio plasma is coupled to the ISM in low- and high-power jets. Observations have suggested that an expanding bubble of gas like this exists for a growing number of cases and for various phases of the gas (cite: Villar99; Croston07; Mingo11; Mingo12; Audibert19; Zovaro19; Girdhar24; Murthy25), but the development of the bubble with the evolution of the jet remains to be clarified.

![](Figures/Fig1-S2-1Annotated.eps)

A way to trace this interaction is to complement measurements of the gas kinematics with those of its physical properties. The cold molecular gas (traced by CO) is ideally suited for studying these effects because its distribution and kinematics can be observed at a high spatial resolution (see reviews by (cite: Bolatto13; Carilli13; Ruffa24)). In addition, observations of multiple CO transitions and other molecules can inform us about the physical conditions of the molecular gas. For example, in regions in which the jets/lobes (or an expanding jet cocoon) and the ISM interact, extreme line ratios have been observed. Examples include IC 5063, PKS 1549–79, NGC 3100, the Tea Cup, and B2 0258+35 ((cite: Oosterloo17; Oosterloo19; Ruffa22; Audibert23; Murthy25), respectively), and other cases in (cite: Audibert25).

In the above cases, the effects of the AGN on the gas are observed to extend to scales of a kpc or smaller. The object studied in this paper, PKS 0023$-$26, is particularly suited for extending these investigations to scales of several kpc because it is a young but relatively more evolved radio galaxy with a size of a few kpc in which the radio jet might be in the process of breaking out from the gas-rich central region. We therefore earlier observed PKS 0023$-$26 with ALMA to explore the impact of young radio jets on kpc scales (cite: Morganti21). These ALMA CO(2-1) observations revealed a large amount of molecular gas that was estimated to be between $3.7 \times 10^9$ $M_\odot$ and $3.1 \times 10^{10}$ $M_\odot$, depending on the assumed CO(2-1)/CO(1-0) line ratio and the CO-to-H$_2$ conversion factor (see Fig. [1](#fig:paper1)). The observations suggested an evolutionary scenario in which only the gas in the very inner region might be part of an outflow resulting from the direct interaction of the radio plasma jet and the ISM, while a gentler interaction occurs on larger scales (see Fig. 11 in (cite: Morganti21)). These two different effects suggest that the impact of the jet might evolve as the jet expands. Interestingly, this has also been suggested to occur in other types of AGN (i.e. radio-quiet AGN; e.g. (cite: Girdhar24)).

![](Figures/Fig2-optical3-2annotated.eps)

In order to test this scenario for PKS 0023$-$26 and to understand how it may affect the conditions of the ISM, observations of multiple transitions of CO are needed. Furthermore, the origin of the high mass of cold molecular gas that was found with ALMA (cite: Morganti21) is also unclear, and it is uncertain whether it might be connected with the rich, cluster-like environment. Therefore, we performed new ALMA observations that targeted two other CO transitions in order to trace the line ratios. We also performed new Chandra observations to investigate the environment in more detail. The Chandra observations will be presented in a companion paper (cite: Siemiginowska2025).

+:----------+:---------:+-----:+:----:+:-----:+--:+----:+:---:+:--------------------:+:-----------------:+:-----------:+:-:+:-:+
|           | Frequency | Beam & PA           |   | Beam      | Velocity resolution  | Noise             | Description |   |   |
+-----------+-----------+-------------+-------+---+-----------+----------------------+-------------------+-------------+---+---+
|           | (GHz)     | (arcsec)    | (deg) |   | (kpc)     | ($\,$km$\,$s$^{-1}$) | (mJy beam$^{-1}$) |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| CO(1-0)   |           | 0.39 | 0.26 | 84.8  |   | 1.8 | 1.2 | 33.6                 | 0.08              |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| CO(2-1)   |           | 0.45 | 0.34 | –77.8 |   | 2.1 | 1.6 | 33.6                 | 0.12              |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| CO(3-2)   |           | 0.29 | 0.25 | 78.3  |   | 1.4 | 1.2 | 33.6                 | 0.16              |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| CO(1-0)   |           | 0.19 | 0.13 | 57.2  |   | 0.9 | 0.6 | 3.4                  | 0.60              | absorption  |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| CO(2-1)   |           | 0.15 | 0.11 | –80.9 |   | 0.7 | 0.5 | 1.7                  | 0.40              | absorption  |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| Continuum | 87        | 0.16 | 0.09 | 58.1  |   | 0.8 | 0.4 |                      | 0.06              |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| Continuum | 174       | 0.15 | 0.11 | –82.1 |   | 0.7 | 0.5 |                      | 0.10              |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+
| Continuum | 262       | 0.19 | 0.09 | –63.9 |   | 0.9 | 0.4 |                      | 0.11              |             |   |   |
+-----------+-----------+------+------+-------+---+-----+-----+----------------------+-------------------+-------------+---+---+

Table notes: The maximum recoverable scales of the CO(1-0), CO(2-1)  and the CO(3-2) observations are 4.7$''$ (22 kpc), 3.8$''$ (18 kpc) , and 2.5$''$ (12 kpc), respectively.

The properties of PKS 0023$-$26 have been described in detail by (cite: Morganti21). We summarise the main features below. PKS 0023$-$26 is a relatively young, powerful radio source ($\log P_{\rm 5\, GHz}/{\rm W\, Hz^{-1}} = 27.43$) that is hosted by an early-type galaxy (see (cite: Ramos11) and references therein and Fig. [2](#fig:environment)), with a relatively high far-infrared luminosity for this type of galaxy (cite: Dicken09). An accurate redshift of $z = 0.32188\pm0.00004$ was derived by (cite: Santoro20)[^1] by fitting stellar absorption lines in a VLT/Xshooter spectrum, refining the estimate of (cite: Holt08). The relatively young age of PKS 0023$-$26 was confirmed by the peaked radio spectrum shown in (cite: Tzioumis02) and (cite: Callingham17). Interestingly, the latter found the spectrum to peak at a low frequency (i.e. 145 MHz) by fitting the radio spectral energy distribution. When we consider that the turnover frequency is predicted to shift to lower frequencies as the components of the source expand with time (cite: ODea98), this indicates that the age of PKS 0023$-$26 is about $10^5$ yr.

The radio continuum emission is distributed in two relatively symmetric lobes, as described by (cite: Tzioumis02). The extent of the radio emission is about 3 kpc measured from peak to peak of the lobes, and the full extent is $\sim$4.7 kpc. In addition to this, the high spatial resolution, combined with the high frequency of the ALMA 1.7 mm image of (cite: Morganti21), enabled the detection of the core of PKS 0023$-$26, as shown in Fig. [1](#fig:paper1), reproduced from (cite: Morganti21). PKS 0023$-$26 is also a strong optical AGN, with a bolometric luminosity in the range $L_{\rm bol}\sim 2.5$ – $4 \times 10^{45}$ $\,$erg$\,$s$^{-1}$ (cite: Santoro20) and an \[OIII\]$\lambda$5007 luminosity $L_{\rm [OIII]} = 1.5\times10^{42}$ erg s$^{-1}$ (cite: Dicken09). This qualifies it as a type 2 quasar according to the criteria of (cite: Zakamska06). Strong and broad (${\rm FWHM}>1000$ $\,$km$\,$s$^{-1}$) optical emission lines were detected by (cite: Holt08), (cite: Shih13) and (cite: Santoro20). This large width indicates outflowing ionised gas with a mass outflow rate in the range $0.13<\dot{M}<1.47$ $M_\odot$ yr$^{-1}$. According to (cite: Santoro20), the warm outflows have similar radial extents as the radio source, and they have a high density. The latter is explained as the result of compression of the gas from the jet/ISM interaction. However, photoionisation (and not shocks) likely produces the emission lines (see (cite: Santoro20) for details).

Finally, three bright neighbouring galaxies that we identify in Fig. [2](#fig:environment) are confirmed to have similar redshifts as PKS 0023$-$26 (cite: Tadhunter11). The galaxy number counts presented by (cite: Ramos13) also suggest a rich environment[^2]. However, based on XMM observations, the total X-ray luminosity of PKS 0023$-$26 and its surroundings ($\log L_{\rm 2-10\,keV}/{\rm erg s^{-1}} = 43.27$; (cite: Mingo14)) is lower than expected for a rich cluster of galaxies, and it is more consistent with that of a galaxy group (cite: Eckmiller11). The type of environment in which PKS 0023$-$26 lives (whether cluster or group) is evidently still unclear, and this has motivated our new Chandra X-ray observations. These observations show that PKS 0023–26 is not part of a galaxy cluster or rich group, and it is at most a member of a poor, low-temperature ($kT \lesssim$ 0.5 keV) galaxy group. A detailed analysis is presented in the companion paper.

In this paper, we aim to further investigate the proposed scenario of the interplay between the AGN in PKS 0023$-$26 and the rich medium in which it is embedded based on new ALMA observations. The paper is organised in the following way. The new ALMA CO(1-0) and CO(3-2) observations are presented in Sect. [2](#sec:observations). The results for the molecular gas, obtained by combining CO(1-0) and CO(3-2) with the available CO(2-1) data, are presented in Sect. [3](#sec:molecular). In Sect. [4](#sec:discussion) we combine our findings and describe the energetics and the proposed scenario, also by comparing PKS 0023$-$26 with BCG and other AGN.

# ALMA observations of CO(1-0) and CO(3-2)

The parameters of the ALMA CO(1-0) and CO(3-2) observations that were performed during Cycle 9 are presented in Table [\[tab:obs\]](#tab:obs) and were chosen to match those of the CO(2-1) observations of (cite: Morganti21), the details of which are given in this table as well. This allowed us to study the distribution of the molecular gas on similar spatial scales as the extended radio emission (about 1 arcsec or $\sim$ 5 kpc).

![](Figures/Fig3.eps)

The ALMA CO(1-0) observations were obtained in configuration C43-7 in four observing sessions, two on June 11 and two on June 12, 2023, resulting in a total on-source observing time of 46.32 min. The observations were made in Band 3 and used the correlator in frequency-division mode. One spectral window was centred on the redshifted CO(1-0) emission using a central sky frequency of 87.195 GHz and a total bandwidth of 1.875 GHz (corresponding to 6450 $\,$km$\,$s$^{-1}$). With the 1920 channels we used, the native velocity resolution is 3.4 $\,$km$\,$s$^{-1}$  but the data were binned to a lower spectral resolution when we made the final data cube (see below). The maximum recoverable scale of these observation is 4.7$''$ (22.2 kpc).

The CO(3-2) observations were obtained using ALMA in configuration C43-5 in one observing session on April 22, 2023, with a total on-source time of 83.18 min. The observations were made in Band 6 with the correlator in frequency-division mode. One spectral window was centred on the CO(3-2) emission using a central sky frequency 262.273 GHz and a total bandwidth of 1.875 GHz (corresponding to 2150.0 $\,$km$\,$s$^{-1}$). With the 1920 channels, the native velocity resolution is 1.1 $\,$km$\,$s$^{-1}$, but in the subsequent data reduction, the velocity channels were binned to match the spectral resolution of the CO(1-0) and CO(2-1) cubes (see below). The maximum recoverable scale of these observation is 2.5$''$ (11.8 kpc). The source J2253+1608 was used as bandpass, flux, and atmospheric calibrator for the observations of both transitions. J0011–2612 was used as phase calibrator for the CO(1-0) observations and J0038–2459 for the CO(3-2) observations. In general, the main uncertainty in the derived ALMA fluxes comes from the limited accuracy of the flux calibration, which is estimated to be about 5% (cite: vanKempen14). The data in the ALMA calibrator database show, however, that the flux of J2253+1608 varied rapidly during the period of our observations. To be on the safe side, we therefore assumed that the error on the derived fluxes is 10%.

The calibration was made in CASA (v6.4.1.12; (cite: McMullin07)) using the reduction scripts provided by the ALMA observatory. The visibility products resulting from the ALMA pipeline were found to be of sufficient quality, and no further calibration was made. The calibrated $uv$ data produced by the pipeline were exported to MIRIAD (cite: Sault95) for the further analysis.

For both the CO(1-0) and CO(3-2) line observations, data cubes were made with the same velocity resolution as the existing CO(2-1) data cube (33.6$\,$km$\,$s$^{-1}$) by binning the channels to 16.8 $\,$km$\,$s$^{-1}$ and applying Hanning smoothing. We made them using natural weighting. The binning improves the S/N of the emission in the channel maps while still resolving the individual spectra, the narrowest of which have a velocity dispersion of about 25 $\,$km$\,$s$^{-1}$. Before making these cubes, we removed the absorption seen in the CO(1-0) data against the northern lobe (see below). The continuum was subtracted in the image domain by fitting for every position a straight line through the line-free channels and subtracting this fit from the observed spectrum. The channel images were cleaned down to half the noise level using masks that were made by smoothing the cube to twice the spatial resolution and using the 2$\sigma$ level of this smoothed cube to create the mask for the original cube. After cleaning, the CO(1-0) and CO(3-2) data cubes were de-redshifted using $z = 0.32188$.

As mentioned above, strong absorption was detected against the N lobe in the CO(1-0) data cube, but not in the CO(3-2) cube. This complements the absorption that was earlier also detected in CO(2-1) (cite: Morganti21). To study this absorption, we also made CO(1-0) and CO(2-1) data cubes at the original velocity resolution of the observations (3.4 $\,$km$\,$s$^{-1}$ and 1.7 $\,$km$\,$s$^{-1}$  respectively; see Table [\[tab:obs\]](#tab:obs)). For these cubes, we used uniform weighting, and thus, a higher spatial resolution, in order to minimise the effect of confusion of the absorption spectra with emission. The properties of this absorption are discussed in Appendix [6](#sec:Abs-Appendix). We also used these cubes with the high velocity and spatial resolution to remove the absorption from the cubes with a lower velocity resolution, however. Because the surface brightness of the CO emission is relatively low, the high spatial resolution and the higher noise level of these cubes means that most of the CO emission is below the noise level, while the absorption is detected at high significance (see Fig. [10](#fig:absorption)). In order to obtain a model of the absorption, we therefore only used the deconvolution task clean on these high-resolution cubes at the location where absorption was seen and subtracted these negative clean components from the original $uv$ data sets before we made the low-velocity resolution cubes.

The total intensity (i.e. moment-0) images of CO(1-0) and CO(3-2) are shown in Fig. [3](#fig:molecularGas) (left and right image, respectively), together with the image of the CO(2-1) emission (centre) from (cite: Morganti21) for comparison. Because we wished to use these images to make images of the line ratios, we convolved the CO(1-0) and CO(3-2) cubes to the same spatial resolution as the CO(2-1) cube (0.45$''$ $\times$ 0.34$''$ $\equiv 2.1 \times 1.6$ kpc) and regridded them to the same spatial and velocity grids as the CO(2-1) observations. In these cubes, the peak S/N of the emission is 12 $\sigma$ in the CO(1-0) cube and 18 $\sigma$ in both the CO(2-1) and CO(3-2) cubes.

The moment-0 images were obtained by first running the SoFia-2 source-finding software (cite: Westmeier21) on the CO(2-1) data cube to construct the moment images for this line transition, and we subsequently applied the same mask generated by Sofia-2 on the cubes of the two other transitions to make the moment images for these transitions as well because the typical S/N level of the CO emission is quite different for the three transitions. Therefore, using masks that were derived separately for the three transitions would mean that the spectra of the different transitions are integrated over different velocity ranges, which would lead to S/N-dependent biases in the line ratio. We chose the CO(2-1) cube as the benchmark because the typical S/N of the emission is highest in this data cube.

Continuum images were made from the line-free channels, and the parameters of these images are summarised in Table [\[tab:obs\]](#tab:obs). More details on the continuum are given in Appendix [7](#sec:AppendixCont).

![](Figures/Fig4-profiles.eps)

![](Figures/Fig5.eps)

# Results: The molecular gas

The moment-0 images presented in Fig. [3](#fig:molecularGas) show that the addition of observations of two more CO transitions provides very useful information on what occurs in PKS 0023$-$26. We first discuss the results for the distribution of the gas that is observed in emission (Sect. [3.1](#sec:COdistribution)). We then discuss the kinematics of the gas in Sect. [3.2](#sec:COkinematics), and we study the line ratios in Sect. [3.3](#sec:lineRatios).

![image](Figures/Fig6-vel1-0.eps) ![image](Figures/Fig6-vel2-1.eps) ![image](Figures/Fig6-vel3-2.eps) ![image](Figures/Fig6-vel3-2Zoom.eps)

## Distribution of molecular gas in the three CO transitions

The extent and morphology of the distribution of the CO(3-2) is similar to that of the CO(2-1) (cite: Morganti21), although clear differences can be noted in the relative intensity of these two transitions at different locations. This suggests different conditions of the gas (Fig. [3](#fig:molecularGas)). This is even more extreme in the case of CO(1-0). Overall, the molecular gas is distributed over a region with a diameter of about 3–4 arcsec (14–19 kpc) that surrounds the radio source, but is not centred on it, and is more extended to the W and N. In particular, while the northern lobe appears to be embedded in the molecular gas, the southern lobe is not.

From the main body around the radio source, a tail or tidal feature extends toward a nearby galaxy $\sim$3 arcsec ($\sim$14 kpc) east of PKS 0023$-$26 (A in Fig. [2](#fig:environment)). A tail in the SW direction is also seen, although less clearly, and possibly pointing in the direction of another companion galaxy (B or C2). A small cloud is seen close to another companion (C1), but it is offset from its centre and has an elongated morphology roughly in the direction of PKS 0023$-$26. A more detailed discussion of the environment and origin of the gas will be given in the companion paper (cite: Siemiginowska2025).

The brightest region of CO(3-2) emission is (similar to what is seen in CO(2-1)  but more clearly) seen at the location of the radio core and extends in a direction roughly perpendicular to the jet (Fig. [3](#fig:molecularGas)). The diameter of this structure is $\sim$0.8 arcsec ($\sim$3.7 kpc) from one side of the nucleus to the other. Interestingly, and in contrast to what we observed in CO(2-1) and CO(3-2), this region appears to be depleted of CO(1-0) gas. This is illustrated in Fig. [4](#fig:ProfilesCore), where the profiles of the three transitions taken at the position of the core of PKS 0023$-$26 are shown. At this location, no CO(1-0) emission is found, but the other transitions are clearly detected. This is clearly different in the outer regions, where the CO(2-1) and CO(3-2) are fainter than near the core, but where the CO(1-0) is detected instead. This appears to be similar to the situation in NGC 3100, where a central lack of CO(1-0) is observed (cite: Ruffa22), or in ESO 428–G014, where a lack of CO(2-1) is seen in the central regions while H$_2$ gas is clearly detected (cite: Feruglio20). Feruglio et al. (2020) suggested that X-ray photons in these regions might excite CO to higher excitation levels, which would explain the low levels of the low-$J$ CO emission. Something similar may also occur in NGC 2110 (cite: Fabbiano19). We discuss this further in Sect. [3.3](#sec:lineRatios).

In the region of the radio lobes, the CO appears to be faint in CO(2-1) and CO(3-2). This is clearly visible in the channel maps in Fig. [5](#fig:channels), where the distribution of the CO(3-2) gas (grey scale, black contours) for a range of velocities (from $+58$ to $-128$ $\,$km$\,$s$^{-1}$) is shown. The continuum emission (at 262 GHz) of the radio galaxy is superposed in red contours. The CO emission clearly avoids the locations with the strongest continuum emission. This was already noted by (cite: Morganti21) for the CO(2-1) emission. For this transition, we were unable to completely exclude some effect of the CO absorption seen against the northern lobe (even though (cite: Morganti21) removed this absorption from the CO(2-1) data cube). In contrast to CO(1-0) and CO(2-1), no CO(3-2) absorption is detected against the northern lobe, and this is therefore no problem here.

![](Figures/Fig7-sliceBoth.eps)

## The complex kinematics from small to large scales

The overall velocity field observed for the three transitions is shown in Fig. [6](#fig:velfies) , where a zoom-in of the velocity field of the CO(3-2) is also shown. The CO(1-0) and CO(3-2) show the same smooth velocity gradient that was already observed for the CO(2-1). The kinematics of the gas at the location and around the radio source is particularly interesting, however.

Since no CO(1-0) is detected in the central regions, we used the CO(3-2) to investigate the kinematics of the gas. The zoom-in velocity field of the CO(3-2) clearly shows that while there is an overall SW-NE gradient, the large-scale kinematics does not correspond to that of a regularly rotating disk. As mentioned above, the most extreme kinematics of the gas is observed in the central region. Figure [7](#fig:PositionVelocity) shows the position-velocity plot of the CO(3-2) emission at a position angle $51^{\circ}$ (i.e. perpendicular to the radio axis), which illustrates the large profile width in the central regions, with a full width zero-intensity of FWZI $\sim$600 $\,$km$\,$s$^{-1}$ (FWHM $\sim$300 $\,$km$\,$s$^{-1}$), consistent with the profiles shown in Fig [4](#fig:ProfilesCore). Figure [7](#fig:PositionVelocity) also shows that the kinematics of the gas near the nucleus does not seem to be consistent with a regularly rotating disk, and its kinematics clearly differs from the overall large-scale gradient in velocity. This suggests that the broad profiles are driven by the AGN. Although a broad, central profile was already seen in the CO(2-1) data, the new CO(3-2) observations show a more symmetric profile with a broader blueshifted component than is observed in CO(2-1) (cite: Morganti21). The reason is probably that the CO(3-2) is brighter than the CO(2-1) in this region and has a higher S/N (see Fig. [4](#fig:ProfilesCore) and Sect. [3.3](#sec:lineRatios)). In this direction perpendicular to the radio jet, the broad component appears to be spatially limited to one beam, and it therefore is on a scale of an FWHM $\sim$1 kpc.

As mentioned above, the CO emission appears to avoid the northern lobe. The emission at this location is not only very faint (see Fig. [5](#fig:channels)), but also relatively broad in velocity. This can be seen in the velocity dispersion ($\sigma$) image presented in Fig. [8](#fig:LineRatio), which shows that in the region between the core to the northern lobe, $\sigma$ reaches almost 100 $\,$km$\,$s$^{-1}$, which is well above the typical values for undisturbed molecular gas in normal galaxies ($\sigma \sim 10 - 20$ $\,$km$\,$s$^{-1}$; (cite: Ruffa24)). Just beyond the radio source, the velocity dispersion is still about 50 $\,$km$\,$s$^{-1}$.

As mentioned above, on the largest scales, the CO(1-0) and CO(3-2) show the same smooth velocity gradient as was observed for the CO(2-1) (Fig. [6](#fig:velfies)). In the north-eastern part of this extended gas distribution, a region with a high velocity dispersion is found. As remarked in (cite: Morganti21), this is likely to be due to the superposition of two gas structures, as is evident from double-peaked profiles at these locations. About 1 arcsecond south-west of the radio source, another region has large velocity dispersions. This is likely due to beam smearing, given the large, local velocity gradients at this location.

![image](Figures/Fig8-ratio.eps) ![image](Figures/Fig8-disp.eps)

## Line ratios

The total intensity images in Fig. [3](#fig:molecularGas) clearly show that the relative intensity of the three different transitions strongly changes with position. This is particularly extreme in the central beam, where the CO(1-0) is undetected, while the other two transitions are relatively bright. In the outer regions, the contrast is much lower. To investigate this in more detail, we constructed line-ratio images of the observed CO transitions.

The plot in Fig. [8](#fig:LineRatio) shows the distribution of the brightness temperature ratio $R_{\rm 32}\equiv I_{\rm 3-2}/I_{\rm 2-1}$, and the 87-GHz radio continuum (in grey contours) is superposed for reference. This image clearly shows that $R_{\rm 32}$ peaks in the region between the core and the northern lobe. The values are in the range of 1.0 to 1.2. No high values like this are seen at the location of the southern lobe, where we also observed a lack of gas (see above).

Despite the depth of the observations, the region of the radio source of PKS 0023$-$26and slightly beyond is depleted of CO(1-0). We estimated an upper limit to the CO(1-0) flux by assuming the same line width as for CO(3-2), and this gives a 3$\sigma$ upper limit to the CO(1-0) flux integral of the central region of 39 mJy $\,$km$\,$s$^{-1}$. This means a lower limit of $R_{21} \gtrsim 1.9$, which is quite extreme. At the locations where $R_{32} < 0.6$, CO(1-0) is detected, and values more typical for a normal ISM are seen ($0.4 < R_{21} < 0.6$).

For comparison, the molecular gas in star-forming galaxies shows typical values of $R_{\rm 21}$ around 0.6, with a standard deviation of about 0.2 (cite: Brok21; Yajima21; Leroy22), and $R_{\rm 32}$ ranges between 0.2 and 0.6 (16% – 84% range; (cite: Leroy22)). For early-type galaxies, similar values for $R_{\rm 21}$ are found from spatially resolved observations (e.g. (cite: Topal16; Young22) and Davis priv. comm.). Values like this have also been found in high-$z$ galaxies (e.g. (cite: Kaur25)). On the other hand, a broad distribution of $R_{\rm 32}$ and $R_{\rm 21}$ values is seen in ULIRG/LIRG objects, including ratios higher than one (e.g. (cite: Montoya23)). However, these studies reported integrated values and did not resolve the distribution of the gas, as we did for PKS 0023$-$26. Thus, it is difficult to identify whether the high ratio is connected to particular regions in ULIRG systems, specifically, to regions that might be affected by the AGN (when present). For example, in the case of the LIRG NGC 6240, the region of higher line ratios ($R_{\rm 21} > 1$ ) is associated with outflowing gas, and in general, with higher velocity dispersion components. This region appears to be located between the two AGN (cite: Cicone18). For another ULIRG, however, IRAS 10190+1322, (cite: Gracia07) found a brightness temperature ratio $R_{\rm 21}$ between 0.6 and 0.78, which is at the upper end of what is found in normal spiral galaxies.

Figure [8](#fig:LineRatio) shows that the region with elevated line ratios extends well outside the radio source. A region extending up to $\sim$5 kpc from the radio source shows ratios higher than 0.6. This might indicate that a large region might be directly or indirectly affected by the AGN, and in particular, the radio plasma, in regions that lie well outside the radio source. In these regions, however, we cannot exclude the possibility that other mechanisms that are connected to the on-going galaxy interaction also affect the gas conditions (see Sect. [4.1](#sec:interaction)).

Although there is no exact one-to-one correlation, the distribution of $R_{\rm 32}$ is similar to the structure of the velocity dispersion shown in Fig. [8](#fig:LineRatio). In both cases, the regions with the strongest enhancements appear to be aligned with the radio axis on the NW side of the nucleus. In addition to the central region with high velocity dispersions and high values for $R_{\rm 32}$, both extend to the west, where high values are found. Structures with high line ratios and/or a high velocity dispersion that extends perpendicular to the radio axis are seen in a growing number of objects (e.g. (cite: Audibert23; Murthy25)), but they are smaller in scale than in PKS 0023$-$26.

Finally, the results for the excitation of the gas allowed us to re-estimate the total mass of the molecular gas by narrowing down the parameters used by (cite: Morganti21). The combination of conversion factors that seems to be most appropriate considering the observed line ratio gives an H$_2$ mass of $M_{\rm mol} = 6.2 \times 10^{9}$ $M_\odot$ for a conversion factor $\alpha_{\rm CO}$ typical of ULIRGs, $\alpha_{\rm CO} = 0.89  \ M_\odot/({\rm K\ km\ s^{-1}\ pc^2})$ and $R_{21}=1$. The latter represents a compromise between the value measured at large radii and the value in the central part. When we instead assumed that all the gas had a typical Galactic $\alpha_{\rm CO} = 4.3  \ M_\odot/({\rm K\ km\ s^{-1}\ pc^2})$, this gave an upper limit of the molecular mass of $M_{\rm mol} = 3.1 \times 10^{10}$ $M_\odot$ (see also (cite: Morganti21)).

# Discussion: AGN feedback and evolution of the radio jets

We have traced the distribution and kinematics of the cold molecular gas, and we mapped the diversity of the physical conditions of this gas in PKS 0023$-$26 using different transitions. The observations confirmed that the AGN has a significant impact on the ISM and added evidence of how this impact appears to evolve as the radio jet expands.

## Jet-ISM interactions

The new ALMA observations show several signatures of not only the impact of the AGN, but more specifically, of the on-going interaction between the jet and the ISM. We can even trace and quantify the impact. In the central kpc, we found broad line profiles and disturbed kinematics for the molecular gas. This was already seen in CO(2-1)  but appears even more prominently in the new CO(3-2) observations. The broad range in velocities that is observed (FWZI$\sim$ 600 $\,$km$\,$s$^{-1}$) suggests that the gas is likely associated with an outflow driven by the AGN. This was also observed for the warm ionised gas by (cite: Santoro20). The extreme conditions of the gas in the central regions are further illustrated by the values of the line ratios of the various CO transitions and by the non-detection of CO(1-0) in the central regions. The size of the region in which the outflow of cold molecular gas is observed ($\sim$1 kpc) is similar to that seen in other objects (as summarised in Sect. [1](#sec:introduction)). In some cases that were presented in the literature (e.g. (cite: Dasyra16; Oosterloo17; Ruffa22; Murthy22; Murthy25)), the morphological association between the extended radio continuum and the region in which the outflow occurs, or in some cases, the absence of a powerful optical AGN, suggests that the radio jet probably produces the outflows. In PKS 0023$-$26, the near-nuclear outflow is spatially unresolved in our observations, but the galaxy also hosts an AGN with a high bolometric luminosity. Thus, it is not possible to determine whether the radio jet or a radiation-pressure-driven wind accelerates this compact outflow.

The distribution, kinematics, and line ratios of the molecular gas on larger scales, however, suggest that the jet interacts with the ISM on larger scales, especially at the location of the N lobe and in the regions between this lobe and the nucleus. At the position of the N lobe, there is a lack of molecular gas, while molecular gas appears to be wrapped around the lobe at larger distances (Fig. [5](#fig:channels)). The former is consistent with a strong interaction between the expanding radio jet/lobe and the molecular ISM, which probably causes the gas clouds to be shredded and heated by hydrodynamical instabilities as they interact with the hot wind behind the jet-induced shock (cite: Klein94; Mellema02). If the pre-existing warm/cold gas had fairly low densities (perhaps not unlikely to be the case at the radius of the N lobe), it may not have survived the passage of the jet and cooled back to a molecular phase. This would explain the lack of molecular gas at the sites of the lobes. There is evidence in some local radio galaxies that strong jet-cloud interactions can indeed be so destructive that the warm/cold precursor gas does not cool behind the jet-induced shock. PKS 2152–69 and 3C 277.3 (Coma A) both show strong jet-cloud interactions in which the jets are deflected in the interactions, but the warm gas kinematics of the interacting gas clouds show only mild (PKS 2152–69; (cite: Tadhunter88)) or no (3C 277.3; (cite: Inarrea03)) signs of kinematic disturbance at radio knots that mark the locations in which the jets are deflected. In the case of PKS 0023$-$26, direct evidence for the destruction of gas clouds at the site of the N lobe may be provided by the detection of enhanced soft X-ray emission at this location in our deep Chandra observations, as reported in the companion paper. These observations reveal hot gas that is aligned with the radio source. The X-rays are enhanced at the N radio lobe and at the location of the peak of $R_{32}$, suggesting that the X-ray emission could play a role in the excitation of CO. Evidence that the radio jet can drive shocks in the ISM and produce the X-ray emission was seen in other cases, for example, NGC 4151 (cite: Wang11), Mkn 573 (cite: Paggi12), and 3C 305 (cite: Hardcastle12) (see also (cite: Fabbiano22) for an overview). In PKS 0023$-$26 we detect some molecular gas even in the extended region between the core and the N lobe, however, which is characterised by an enhanced velocity dispersion ($\sigma\sim$ 80 – 100 km s$^{-1}$) and very high CO excitation ($R_{32} > 0.9$) compared with its immediate surroundings (see Fig. [8](#fig:LineRatio)). Thus, even if not all the molecular clouds are destroyed by the interaction, the physical properties of the gas are profoundly affected by it.

At larger distances from the core, the molecular gas tends to wrap itself around the N radio lobe (Fig. [5](#fig:channels)). These regions are still characterised by values of $R_{32}$ that are higher than the values expected for an ISM like this (i.e. $R_{32} > 0.6$). Moreover, the region with these high line ratios extends a few kpc beyond the N radio lobe to the north-west and to the west of the nucleus, in a direction that is more or less perpendicular to the radio axis. This might suggest that a milder interaction occurs there that might be created by the more slowly expanding cocoon around the radio source. This is also suggested by the lack of strong kinematical disturbances at these locations, except for the velocity dispersion (observed to be in the range 40-50$\,$km$\,$s$^{-1}$), which is higher than what is typically found in an undisturbed ISM.

Overall, the values of $R_{\rm 21}$ and $R_{\rm 32}$ measured in and around PKS 0023$-$26 clearly deviate from the ratios found in the undisturbed ISM in normal star-forming galaxies. We observe $R_{21} > 1.9$ and $R_{\rm 32}> 0.9$ in the region of the radio source, while over a more extended area, $R_{\rm 32}$ is still well above 0.6 (Fig. [8](#fig:LineRatio)) and is thus very different from what is expected from an undisturbed ISM in normal galaxies. The coincidence of the most extreme line ratios with the region of the radio emission strongly suggests the impact of the radio jet.

As mentioned above, a high excitation of the molecular gas is a common feature observed in radio AGN when multiple CO transitions are available. The best-studied case is IC 5063 (cite: Dasyra16; Oosterloo17), which is one of the best examples of a jet that affects the surrounding medium, as confirmed by the kinematics of various phases of the gas (atomic, molecular, and ionised, and using the same CO transitions as for PKS 0023$-$26), as well as by numerical simulations (cite: Mukherjee18b). In IC 5063, the cold molecular gas associated with the outflow and the jet-ISM interaction is much brighter in CO(2-1) and CO(3-2) than in CO(1-0) and has values between 0.97 and 1.25 for $R_{\rm 32}$ and between 1.06 and 1.79 for $R_{\rm 21}$. These values are similar to what is seen in PKS 0023$-$26. For the fastest outflowing gas in IC 5063, the high line ratios are explained by the gas being clumpy and having kinetic temperatures in the range 20 – 100 K and densities between $10^5$ and $10^6$ cm$^{-2}$ (cite: Oosterloo17). These conditions may be indicative for PKS 0023$-$26. Similar situations have now been found in a number of objects across a range of radio jet powers, such as PKS 1549$-$79 (cite: Oosterloo19), NGC 3100 (cite: Ruffa22), the Teacup (cite: Audibert23), and B2 0258+35 (cite: Murthy25).

For the regions with high CO ratios that are well outside the visible radio structures, it is more difficult to find an unambiguous explanation for the observed physical conditions of the gas. In two of the objects mentioned above (B2 0258+35 and the TeaCup), high line ratios in the region perpendicular to the direction of the radio jets have been observed and were explained as the signatures of the effect of the latterly expanding cocoon of shocked gas created by the jet-ISM interaction. Although radio jets with similar power as those in PKS 0023$-$26 ($P_{\rm jet} \ge 10^{45}$ erg s$^{-1}$) can directly punch through the circumnuclear ISM more rapidly than low-power jets, simulations showed that in powerful sources, a cocoon of shocked gas is also created that expands in the direction perpendicular to the jet (cite: Mukherjee16). Therefore, we conclude that at least part of the gas with a high line ratio that is observed in the direction orthogonal to the radio axis can be created by such a cocoon. An alternative explanation could be that the X-ray emission that is observed in this region excites the CO gas to higher excitation levels, but this would require high X-ray fluxes and high densities (cite: Lamperti20). The radial size of the affected regions in the two low-power sources B2 0258+35 and the TeaCup is about 0.7 kpc, which is smaller than the $\sim$2 – 5 kpc observed in PKS 0023$-$26. Interestingly, new ALMA observations of powerful AGN (Morganti et al. in prep.) show regions with high line ratios that extend over similar spatial scales (radius of a few kpc) to those observed in PKS 0023$-$26.

On the other hand, PKS 0023$-$26 is embedded in an on-going galaxy interaction or merger, as is evidenced by the unsettled overall nature of the CO on large scales. Therefore, in addition to the impact of the AGN, the CO excitation might be affected by turbulence and dissipation as the accreted gas settles into a more stable configuration. For example, this mechanism might explain the region of enhanced excitation beyond the N lobe in the direction of the radio axis, which is otherwise difficult to reconcile with the effects of jet-cloud interactions (cite: Mukherjee16). In this case, we would expect enhanced CO excitation to be a common feature of the central regions of gas-rich mergers. Therefore, future spatially resolved CO line ratio studies of non-AGN mergers are required to confirm or refute this idea.

## The energetics of the near-nuclear outflow

As mentioned above, in the sub-kpc central region, the broad CO line suggests an outflow. This is also supported by the high line ratios that are indicative of high excitation and/or optically thin conditions. It is difficult to derive the properties of the outflow because it is only detected in CO(2-1) and CO(3-2), not in CO(1-0). The non-detection of CO(1-0) is one of the surprising results because of the extreme conditions this implies. Using the upper limit to the CO(1-0) flux integral for the centre derived in Sect. [3.3](#sec:lineRatios), we derived an upper limit to the mass of the molecular gas in the outflow (in the central kpc) of $M_{\rm out} < 1.9 \times 10^8$ $M_\odot$, assuming $\alpha_{\rm CO} = 0.89$ $M_\odot$(K $\,$km$\,$s$^{-1}$ pc$^2$)$^{-1}$.

The mass outflow rate can be estimated using $\dot{M} \sim M_{\rm out} \times v_{\rm out} /r_{\rm out}$ with $v_{\rm out}$ the outflow velocity and $r_{\rm out}$ the extent of the outflow. We took $v_{\rm out}$ to be in the range between 200 and 300 $\,$km$\,$s$^{-1}$, the former representing an estimate of the bulk of the outflow and the latter the maximum velocity with respect to the systemic velocity at which we observe gas. A conservative estimate for the radial extent $r_{\rm out}$ is about 1 kpc, that is, about one beam. With these assumptions, we derived an upper limit on the mass outflow rate (by taking $v_{\rm out} = 300$ $\,$km$\,$s$^{-1}$) of $\dot{M} \lesssim$ 20 $M_\odot$ yr$^{-1}$. As stated above, we suspect that the true mass of the molecular outflow is not much lower than our upper limit, and hence, that the actual mass outflow rate is only slightly lower than 20 $M_\odot$ yr$^{-1}$. If this is indeed the case, the mass outflow rate for the molecular gas is much higher than the $\dot{M} \sim 1$ $M_\odot$ yr$^{-1}$ measured for the warm ionised gas component ((cite: Santoro20)). Using our estimate of the mass outflow rate of the cold molecular gas, we derived the kinetic power, estimated as $\dot{E}_{\rm kin} = \frac{1}{2}\dot{M}(v^2_{\rm out}+3\sigma^2)$, and find $\dot{E}_{\rm kin} \lesssim 1 \times 10^{42}$ $\,$erg$\,$s$^{-1}$ assuming $\sigma = 85$ $\,$km$\,$s$^{-1}$.

The jet power (a few $\times 10^{46}$ $\,$erg$\,$s$^{-1}$ derived in (cite: Morganti21)) is much higher than this kinetic power, and therefore, there is enough energy on kpc scales in the radio plasma to accelerate, heat, and disperse the gas and to produce the cocoon of shocked gas. As mentioned above, however, although the impact of the radio plasma is clear at large radii, on the small scales at which the outflow is observed, we cannot exclude that it is driven by the impact of radiation from the optical AGN. The high bolometric luminosity ($L_{\rm bol} \sim 2.5 - 4 \times 10^{45}$ $\,$erg$\,$s$^{-1}$, (cite: Santoro20)) implies that radiation pressure might be a possible driver of the outflow. The uncertainties connected to many parameters (e.g. the outflow launching radius, the mass of the galaxy inside that radius, and the dust properties) mean, however, that we cannot precisely quantify the importance of the radiation pressure.

In summary, the results above suggest that while the jet evolves and grows, the impact of the radio plasma changes: In the first phase, the jet/lobe directly interacts with dense clouds in the near-nuclear regions on sub-kpc scales, and it might accelerate them to several 100 km s$^{-1}$. Then, when the jet expands to larger scales, it interacts with lower-density gas clouds that cannot cool quickly enough to avoid shredding and destruction by hydrodynamic instabilities associated with the hot wind behind the jet-induced shock. On larger scales, however, the interaction with the radio source is still visible in the enhanced CO excitation and in the velocity dispersion that results from a milder and less destructive interaction with the more slowly expanding jet cocoon. Thus, part of the energy that is deposited by the interaction can go into affecting the conditions of the gas in two ways: maintaining the turbulence, as indicated by the high-velocity dispersion, and increasing the excitation temperature of the gas.

![](Figures/Fig9.eps)

## Impact and comparison with other AGN

The energetics derived for PKS 0023$-$26 suggest that the kinetic energy that is transferred to the ISM is only a small fraction of the energy that is available in the radio jets. This would suggest that although we see a clear coupling between the radio plasma and the cold molecular gas, most of the energy of the jets escapes from the galaxy, possibly to the CGM. This has been reported for other AGN in the literature, and we illustrate this in Fig. [9](#fig:Energetics) , modified from the figure presented by (cite: Tamhane22). These authors compared the energetics derived from the cold molecular gas observed in BCG located in cool-core clusters with those of galaxies hosting AGN with wind- or radiation-driven outflows (also in cold molecular gas) from (cite: Fluetsch19). Depending on the type of AGN, they used the mechanical power of the jet (for the radio loud AGN) or the bolometric luminosity for the optical AGN for $P_{\rm drive}$ .

In this plot, we add next to PKS 0023$-$26galaxies for which jet-driven cold molecular outflows were observed and their energetics derived. In particular, we included two high radio power AGN (4C 12.50 and PKS 1549–79; (cite: Holden24; Oosterloo19), respectively) and four lower-luminosity radio AGN (IC 5053 (cite: Oosterloo17; Holden23); B2 0258+35 (cite: Murthy22; Murthy25), the TeaCup (cite: Audibert23); and NGC 3100 (cite: Ruffa22)) that all represent young radio galaxies. For these radio AGN, including PKS 0023$-$26, we used the jet kinetic power as $P_{\rm drive}$. The general conclusion does not change when the bolometric luminosity is used for the objects that also host an optical AGN (as is the case of PKS 0023$-$26).

The figure shows that the kinetic energy fluxes of molecular gas in most systems lie near or below a few percent of the AGN or the starburst power, regardless of the driving mechanism of the outflows, as was also reported by (cite: Audibert25). Interestingly, PKS 0023$-$26 appears to be well below the 0.05% line, like some BCG, and lower than other similarly powerful radio galaxies. Considering the more advanced evolutionary stage of PKS 0023$-$26, we suggest that the coupling between the energy and the ISM may have been high for a short initial period when the radio jet interacted strongly with the higher-density gas in the central regions of the galaxy before it escaped into the extended halo of the galaxy. If this is the case, it would agree with predictions from simulations (cite: Mukherjee18a).

From the results described above, we conclude that PKS 0023$-$26 shows the effect of the two different types of feedback: ejective in the central sub-kpc region and possibly at the location of the (northern) radio lobe, and preventative on the scale of a few kpc, in a way similar to what is seen in clusters, where the molecular gas appears to be wrapped around the radio lobes.

It is interesting to note that gas cocoons created by the interaction of the radio plasma with the ISM are seen in a growing number of objects. For example, (cite: Girdhar24) found similar features in radio-quiet type 2 quasars where extended radio emission, albeit much weaker than in radio galaxies, has been observed. This confirms that low-power jets can also affect their surrounding medium in a ways that can go beyond producing fast gas outflows.

# Conclusions

We have used multiple CO transitions (CO(1-0), CO(2-1)  and CO(3-2)) to investigate the kinematics and physical conditions of the cold molecular gas around a powerful, young radio galaxy, PKS 0023$-$26. The results show that the information from the CO line ratios can complement and expand the view of the AGN impact on the cold gas as derived solely from the gas kinematics. Although the results from the three transitions show similarities to first order, clear differences can be noted in their relative intensities at different locations. This suggests different conditions of the gas. This is particularly extreme in the case of CO(1-0), which is undetected in the central regions that are coincident with the radio core. This is the same location as that at which CO(3-2) shows its peak intensity.

The region with the highest $R_{32}$ line ratios was found to be aligned with the radio emission north-west of the nucleus, where relatively high velocity dispersions were also measured. This clearly demonstrates the impact of the radio source on the excitation and kinematics of the molecular gas, and it might result from interaction of the gas with the slowly expanding cocoon that is created by the jet as it finds its way through the ISM. More destructive interactions with the radio source likely occur at the site of the N radio lobe itself, however, which appears to have very little CO emission. At this location, the CO emission is not only very faint (see Fig. [5](#fig:channels)), but also broad in velocity.

PKS 0023$-$26 is one of a growing number of AGN that show regions of extreme CO line ratios that also extend in a direction perpendicular to the radio jet. To first order, this is consistent with the predictions of numerical simulations, where the jet-ISM interaction can produce a cocoon of shocked gas that can extend in the direction orthogonal to the jet. This affects the physical condition of the gas well outside the visible radio source. A region of high CO excitation ($R_{\rm 32} > 0.6$) that extends up to $\sim$2 kpc beyond the N radio lobe in the jet direction is difficult to reconcile with this explanation, however. In this context, it is notable that PKS 0023$-$26 is relatively gas rich for an early-type galaxy and shows clear signs of interactions with neighbouring galaxies. This suggests an alternative explanation for the high line ratios in terms of the turbulence and dissipation induced as the accreted gas settles following a galaxy merger or interaction.

From the kinematics, excitation, and the distribution of the cold molecular gas, we were able to trace different types of interaction between the (radio) AGN and the gas. The fastest gas outflows are confined to the central kpc, and the effects at larger radii are milder. As suggested by (cite: Morganti21), the AGN feedback may appear in different forms during the evolution of the radio jet. Most importantly, we confirmed that the impact of the AGN is not necessarily only seen in the kinematics, but rather in the line ratios, and their spatial distribution are also powerful diagnostics. This introduces additional complexity in our attempt to describe and quantify AGN feedback.

Another important finding is that although the effects of the interaction between the radio plasma and the ISM are clear, the energy that is transferred from the AGN to the gas is only a small fraction of the energy available in the jet. This adds to a growing body of evidence that now expands to high redshift through the results obtained with JWST (e.g. (cite: Cresci23; Roy24; Eugenio25)), and it implies that much of the jet energy is likely to escape the galaxy to affect its environment on larger scales.

# Acknowledgements

We thank Tim Davis for his input on the CO line ratios of early-type galaxies and we thank an anonymous referee for very useful input. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01498.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

(ref: Audibert19) Audibert, A., Combes, F., Garcı́a-Burillo, S., et al. 2019, A&A, 632, A33

(ref: Audibert23) Audibert, A., Ramos Almeida, C., Garcı́a-Burillo, S., et al. 2023, A&A, 671, L12

(ref: Audibert25) Audibert, A., Ramos Almeida, C., Garcı́a-Burillo, S., et al. 2025, arXiv:2505.02759

(ref: Bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207.

(ref: Callingham17) Callingham, J. R., Ekers, R. D., Gaensler, B. M., et al. 2017, ApJ, 836, 174.

(ref: Carilli13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Cicone18) Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018, ApJ, 863, 143

(ref: Costa24) Costa-Souza, J. H., Riffel, R. A., Souza-Oliveira, G. L., et al. 2024, ApJ, 974, 127

(ref: Cresci23) Cresci, G., Tozzi, G., Perna, M., et al. 2023, A&A, 672, A128

(ref: Croston07) Croston, J. H., Kraft, R. P., & Hardcastle, M. J. 2007, ApJ, 660, 191

(ref: Dasyra16) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7

(ref: Dicken09) Dicken, D., Tadhunter, C., Axon, D., et al. 2009, ApJ, 694, 268

(ref: Brok21) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221

(ref: Eugenio25) D’Eugenio, F., Maiolino, R., Mahatma, V. H., et al. 2025, MNRAS, 536, 1, 51

(ref: Dutta24) Dutta, R., Sharma, P., Sarkar, K. C., et al. 2024, ApJ, 973, 2, 148

(ref: Eckmiller11) Eckmiller, H. J., Hudson, D. S., & Reiprich, T. H. 2011, A&A, 535, A105.

(ref: Fabbiano19) Fabbiano, G., Paggi, A., & Elvis, M. 2019, ApJL, 876, 2, L18

(ref: Fabbiano22) Fabbiano, G. & Elvis, M. 2022, Handbook of X-ray and Gamma-ray Astrophysics, 92

(ref: Feruglio20) Feruglio, C., Fabbiano, G., Bischetti, M., et al. 2020, ApJ, 890, 1, 29

(ref: Fluetsch19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: Girdhar24) Girdhar, A., Harrison, C. M., Mainieri, V., et al. 2024, MNRAS, 527, 9322

(ref: Gracia07) Graciá-Carpio, J., Planesas, P., & Colina, L. 2007, A&A, 468, L67

(ref: Guillard12) Guillard, P., Ogle, P. M., Emonts, B. H. C., et al. 2012, ApJ, 747, 95

(ref: Hardcastle12) Hardcastle, M. J., Massaro, F., Harris, D. E., et al. 2012, MNRAS, 424, 3, 1774

(ref: Holden23) Holden, L. R., Tadhunter, C. N., Morganti, R., et al. 2023, MNRAS, 520, 1848

(ref: Holden24) Holden, L. R., Tadhunter, C., Audibert, A., et al. 2024, MNRAS, 530, 446

(ref: Holt08) Holt, J., Tadhunter, C. N., & Morganti, R. 2008, MNRAS, 387, 639

(ref: Kaur25) Kaur, B., Kanekar, N., Neeleman, M., et al. 2025, ApJL, A Massive H I-absorption-selected Galaxy at z $\approx$ 2.356, 982, 1, L26.

(ref: Klein94) Klein, R.I., McKee, C.F., Colella, P. 1994, ApJ, 420, 213

(ref: Lamperti20) Lamperti, I., Saintonge, A., Koss, M., et al. 2020, ApJ, 889, 2, 103

(ref: Leroy22) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127

(ref: McNamara16) McNamara, B. R., Russell, H. R., Nulsen, P. E. J., et al. 2016, ApJ, 830, 79.

(ref: Mellema02) Mellema, G., Kurk, J.D., Röttgering, H.J.A. 2002, A&A, 395, 13

(ref: Mingo11) Mingo, B., Hardcastle, M. J., Croston, J. H., et al. 2011, ApJ, 731, 21.

(ref: Mingo12) Mingo, B., Hardcastle, M. J., Croston, J. H., et al. 2012, ApJ, 758, 95.

(ref: Mingo14) Mingo, B., Hardcastle, M. J., Croston, J. H., et al. 2014, MNRAS, 440, 269

(ref: Miura21) Miura, R. E., Espada, D., Hirota, A., et al. 2021, MNRAS, 504, 6198.

(ref: Montoya23) Montoya Arroyave, I., Cicone, C., Makroleivaditi, E., et al. 2023, A&A, 673, A13

(ref: Morganti15) Morganti, R., Oosterloo, T., Oonk, J. B. R., Frieswijk, W., Tadhunter, C. 2015, A&A, 580, A1

(ref: Morganti21) Morganti, R., Oosterloo, T., Tadhunter, C., et al. 2021, A&A, 656, A55

(ref: Mukherjee16) Mukherjee, D., Bicknell, G. V., Sutherland, R., & Wagner, A. 2016, MNRAS, 461, 967;

(ref: Mukherjee18a) Mukherjee, D., Bicknell, G. V., Wagner, A. Y. et al. 2018a, MNRAS, 479, 5544

(ref: Mukherjee18b) Mukherjee, D., Wagner, A. Y., Bicknell, G. V., et al. 2018b, MNRAS, 476, 80

(ref: Murgia99) Murgia, M., Fanti, C., Fanti, R., et al. 1999, A&A, 345, 769

(ref: Murthy22) Murthy, S., Morganti, R., Wagner, A. Y., et al. 2022, Nature Astronomy, 6, 488

(ref: Murthy25) Murthy, S., Morganti, R., Oosterloo, T., et al. 2025, A&A, 694, A110

(ref: ODea98) O’Dea, C. P. 1998, IAU Colloq. 164: Radio Emission from Galactic and Extragalactic Compact Sources, 291

(ref: Oosterloo17) Oosterloo, T., Raymond Oonk, J. B., Morganti, R., et al. 2017, A&A, 608, A38

(ref: Oosterloo19) Oosterloo, T., Morganti, R., Tadhunter, C., et al. 2019, A&A, 632, A66

(ref: Paggi12) Paggi, A., Wang, J., Fabbiano, G., et al. 2012, ApJ, 756, 39

(ref: Ramos11) Ramos Almeida, C., Tadhunter, C. N., Inskip, K. J., et al. 2011, MNRAS, 410, 1550.

(ref: Ramos13) Ramos Almeida, C., Bessiere, P. S., Tadhunter, C. N., et al. 2013, MNRAS, 436, 997

(ref: Rose24) Rose, T., McNamara, B. R., Combes, F., et al. 2024, MNRAS, 533, 771

(ref: Roy24) Roy, N., Heckman, T., Overzier, R., et al. 2024, ApJ, 970, 69

(ref: Ruffa22) Ruffa, I., Prandoni, I., Davis, T. A., et al. 2022, MNRAS, 510, 4485

(ref: Ruffa24) Ruffa, I. & Davis, T. A. 2024, Galaxies, 12, 36

(ref: Russell19) Russell, H. R., McNamara, B. R., Fabian, A. C., et al. 2019, MNRAS, 490, 3025

(ref: Santoro20) Santoro, F., Tadhunter, C., Baron, D., et al. 2020, A&A, 644, A54.

(ref: Sault95) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, Astronomical Data Analysis Software and Systems IV, 77, 433

(ref: Shih13) Shih, H.-Y., Stockton, A., & Kewley, L. 2013, ApJ, 772, 138

(ref: Siemiginowska2025) Siemiginowska, A., Morganti, R., Fabbiano, G. et al. 2026, ApJ, submitted

(ref: Inarrea03) Solórzano-In̂arrea, C., Tadhunter, C. 2003, MNRAS, 340, 705.

(ref: Sutherland07) Sutherland, R. S. & Bicknell, G. V. 2007, Ap&SS, 311, 293.

(ref: Tadhunter88) Tadhunter, C., Fosbury, R., de Serego Alighieri, S., Bland, J., Danziger, I., Goss, W., Snijders, M. 1988, MNRAS, 235, 403

(ref: Tadhunter11) Tadhunter, C., Holt, J., González Delgado, R., et al. 2011, MNRAS, 412, 960

(ref: Tadhunter14) Tadhunter, C., Morganti, R., Rose, M., et al. 2014, Nature, 511, 440

(ref: Tamhane22) Tamhane, P. D., McNamara, B. R., Russell, H. R., et al. 2022, MNRAS, 516, 861

(ref: Tanner22) Tanner, R. & Weaver, K. A. 2022, AJ, 163, 134

(ref: Topal16) Topal, S., Bureau, M., Davis, T. A., et al. 2016, MNRAS, 463, 4121

(ref: Tzioumis02) Tzioumis, A., King, E., Morganti, R., et al. 2002, A&A, 392, 841

(ref: vanKempen14) van Kempen, T.A., Kneissl, R., Marcelino, N., et al. 2014, ALMA Memo 599

(ref: Villar99) Villar-Martı́n, M., Tadhunter, C., Morganti, R., et al. 1999, MNRAS, 307, 24.

(ref: Wang11) Wang, J., Fabbiano, G., Elvis, M., et al. 2011, ApJ, 736, 62

(ref: Westmeier21) Westmeier, T., Kitaeff, S., Pallot, D., et al. 2021, MNRAS, 506, 3962

(ref: Yajima21) Yajima, Y., Sorai, K., Miyamoto, Y., et al. 2021, PASJ, 73, 257

(ref: Young22) Young, L. M., Meier, D. S., Crocker, A., et al. 2022, ApJ, 933, 90

(ref: Zakamska06) Zakamska, N. L., Strauss, M. A., Krolik, J. H., et al. 2006, AJ, 132, 1496

(ref: Zovaro19) Zovaro, H. R. M., Sharp, R., Nesvadba, N. P. H., et al. 2019, MNRAS, 484, 3, 3393

# Absorption against the N radio lobe

As was the case in the CO(2-1) observations of (cite: Morganti21), absorption is present in the CO(1-0) data at the location of the peak of the continuum emission of the northern lobe. No absorption is detected in the CO(3-2) data, but this is at least in part due to the faint continuum flux (26 mJy beam$^{-1}$) of the peak of the northern lobe in the CO(3-2) data compared to that at the other frequencies (see Appendix [7](#sec:AppendixCont)). We characterise the absorption using the highest resolution cubes described in Sect. [2](#sec:observations) and Table [\[tab:obs\]](#tab:obs). Figure [10](#fig:absorption) shows the two absorption profiles plotted in optical depth $\tau$. The profiles are extracted from the high spatial- and velocity resolution CO(1-0) and CO(2-1) cubes, given the small velocity width of the absorption.

![](Figures/FigA1-profilesBoth.eps)

As in the case of CO(2-1), the CO(1-0) absorption is narrow with a FWHM $\sim$10 $\,$km$\,$s$^{-1}$, roughly centred on the systemic velocity. This is consistent with what was reported by (cite: Morganti21), although those values were derived from a lower velocity resolution cube. The depth of the CO(1-0) absorption is almost 12 mJy beam$^{-1}$ against the continuum peak flux of 123 mJy beam$^{-1}$. As discussed in (cite: Morganti21), the narrow width of the absorption suggests that it is likely produced by a single giant molecular cloud (cite: Miura21) observed against the small, compact component in the N lobe which has been detected in VLBI and that has a size of about 100 pc (cite: Tzioumis02). The results from Gaussian fits to the CO(1-0) and CO(2-1) profiles are given in Table [1](#tab:absFit).

From the detection of absorption in two transition, in principle, one can estimate the excitation temperature $T_{\rm ex}$ using $$\frac{\int \tau_{21} dv}{\int \tau_{10}dv} = 2 \frac{1-e^{-h\nu_{21}/kT_{\rm ex}} }{e^{h\nu_{10}/kT_{\rm ex}} - 1} .$$ Using the observed values for the CO(1-0) and CO(2-1) absorption, we find $T_{\rm ex} = 5 \pm 1$ K. However, as described by (cite: Rose24), the fact that the background continuum may have different sizes at different frequencies, as well as the complex hierarchical structure of the molecular clouds, make the interpretation of optical depths ratios very uncertain. Using $T_{\rm ex}$ = 5 K and a CO abundance relative to H$_2$ of $10^{-4}$, we find that the H$_2$ column density is $N_{{\rm H}_2} = 2.0 \pm 0.5 \cdot 10^{19}\ {\rm cm}^{-2}$. This is in the range of column densities observed by (cite: Rose24) in a number of radio galaxies.

| Parameter                              |      CO(1-0)      |      CO(2-1)      |
|:---------------------------------------|:-----------------:|:-----------------:|
| Peak $\tau$                            | 0.099 $\pm$ 0.007 | 0.083 $\pm$ 0.005 |
| FWHM   ($\,$km$\,$s$^{-1}$)            |   9.4 $\pm$ 0.8   |  10.4 $\pm$ 0.7   |
| $V_{\rm cen}$   ($\,$km$\,$s$^{-1}$)   |   2.6 $\pm$ 0.3   |   2.8 $\pm$ 0.3   |
| $\int \tau\,dv$   ($\,$km$\,$s$^{-1}$) |  0.99 $\pm$ 0.20  |  0.92 $\pm$ 0.15  |

: Parameters of Gaussian fits to the absorption profiles

# Continuum properties

The continuum images made at the three frequency bands (see Table [\[tab:obs\]](#tab:obs)) all show the same structure of a core and two lobes (see Fig. [3](#fig:molecularGas) and (cite: Morganti21)). Table [2](#tab:fluxes) and Fig. [11](#fig:specindex) give the integrated flux for the three components and their spectral indices $\alpha$ (defined through $S\propto \nu^\alpha$) as derived from these fluxes. The spectral indices of the lobes are quite steep and steeper than seen at lower frequencies (cite: Morganti21). This trend, which suggests the presence of a spectral break at relatively high frequencies, is often seen in Compact Steep Spectrum radio galaxies similar to PKS 0023$-$26, as shown in (cite: Murgia99). According to (cite: Murgia99), this confirms the idea that these radio galaxies are genuinely young.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
|  | $S_{\rm 87\ GHz}$ | $S_{\rm 174\ GHz}$ | $S_{\rm 262\ GHz}$ | $\alpha$ |  |  |
|  | (mJy) | (mJy) | (mJy) |  |  |  |
| N lobe | 144 | 62 | 30 | $-1.40 \pm 0.14$ |  |  |
| SE - lobe | 70 | 24 | 9.9 | $-1.75 \pm 0.16$ |  |  |
| Core | 3.7 | 2.7 | 1.8 | $-0.63 \pm 0.15$ |  |  |

:  Continuum flux densities and spectral indices of the three components derived from the ALMA observations.

Table notes: The error in the fluxes is assumed to be 10%.

![](Figures/FigB1-spectraPub.eps)

[^1]: At this redshift, 1 arcsec corresponds to 4.716 kpc for the cosmology adopted in this paper, which assumes a flat Universe and the following parameters: $H_{\circ} = 70$ $\,$km$\,$s$^{-1}$ Mpc$^{-1}$, $\Omega_\Lambda = 0.7$, and $\Omega_{\rm M} = 0.3$.

[^2]: The number count results for the environments of individual objects can be unreliable because they rely on an accurate subtraction of the background galaxy counts, which can be challenging.

</paper>

Write the methods card for this paper.