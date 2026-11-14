# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A..35R\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...687A..35R",
 "title": "Dynamical modelling and the origin of gas turbulence in z ∼ 4.5 galaxies",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Roman-Oliveira, F.",
 "n_authors": 3,
 "arxiv_id": "2403.00904",
 "doi": "10.1051/0004-6361/202348828",
 "alma_projects_linked_by_archive": [
  "2015.1.00330.S",
  "2017.1.00127.S",
  "2017.1.00394.S",
  "2017.1.01052.S",
  "2018.1.00001.S"
 ]
}
```

Paper text:
<paper>
# Dynamical modelling and origin of gas turbulence in *z* $\sim$ 4.5 galaxies

In recent years, a growing number of regularly rotating galaxy discs have been found at z $\geq$ 4. Such systems provide us with the unique opportunity to study the properties of dark matter halos at these early epochs, the turbulence within the interstellar medium and the evolution of scaling relations.

Here, we investigate the dynamics of four gas discs in galaxies at *z* $\sim$ 4.5 observed with ALMA in the \[CII\] 158 $\mu$m fine-structure line. We aim to derive the structural properties of the gas, stars and dark matter halos of the galaxies and to study the mechanisms driving the turbulence in high-*z* discs.

We decompose the rotation curves into baryonic and dark matter components within the extent of the \[CII\] discs, i.e. 3 to 5 kpc. Furthermore, we use the gas velocity dispersion profiles as a diagnostic tool for the mechanisms driving the turbulence in the discs.

We obtain total stellar, gas and dark matter masses in the ranges of $\log{(M/M_{\odot})} = 10.3 - 11.0$, $9.8 - 11.3$, and $11.2 - 13.3$, respectively. We find dynamical evidence in all four galaxies for the presence of compact stellar components, conceivably stellar bulges. The turbulence present in the galaxies appears to be primarily driven by stellar feedback, negating the necessity for large-scale gravitational instabilities. Finally, we investigate the position of our galaxies in the context of local scaling relations, in particular the stellar-to-halo mass and Tully-Fisher analogue relations.

# Introduction

The advent of the Atacama Large Milimiter/submilimiter Array (ALMA) observatory has made possible to study the resolved kinematic properties of the gas in high-*z* galaxies through the \[CII\] 158 $\mu$m line-emission, which is the brightest fine-structure line in the rest-frame far-infrared (cite: lagache18; casey14; carilli&walter13).

Building upon the growing unprecedented data, many studies have reported the presence of disc galaxies at $z > 4$ with unexpectedly high levels of rotation support, with high ratios of rotation-to-random motion (V/$\sigma \sim 10$) similar to those of local galaxies (cite: romanoliveira23; neeleman23; rizzo21; fraternali21; lelli21; tsukui21; rizzo20; neeleman20).

These high V/$\sigma$ values indicate that early galaxy discs are kinematically colder than what it is typically predicted by cosmological simulations (cite: romanoliveira23).

The presence of such high-*z* discs has been further supported by the discovery of both large fractions of disky morphologies in the rest-frame optical emission at $z > 4$ (cite: ferreira22a; ferreira22b; robertson23; kartaltepe23), and barred spiral galaxies up to $z = 3$ (cite: leconte23; costantin23). The presence of bars at $z = 3$ indicates that dynamically settled disks are already present at a lookback time $\gtrsim$ 11 Gyr.

However, since galaxies are known to form hierarchically through the accretion of gas and mergers inside cold dark matter halos, there was a general expectation of a chaotic period in the early stages of matter build-up characterised by high levels of turbulence (cite: hopkins14; schaye15; vogelsberger20).

The recent discoveries suggests instead a scenario in which disc galaxies can form earlier than previously expected and poses challenges to current models of galaxy formation as, in several simulations, disc galaxies at *z* \> 2 tend to be short-lived outliers (cite: kretschmer22).

Therefore, to better understand how galaxies can form persistent discs quickly and early in cosmic time, we need to gather more information on their dark matter halo content and the turbulence in their interstellar medium (ISM).

Fortunately, the regularity of these early gaseous discs provides the unique opportunity to obtain the gas rotation velocity that is linked to the total gravitational potential of the galaxy and consequently allows us to infer the dark matter halo properties (cite: cfn19) and the gas velocity dispersion that is linked to the local turbulence in the ISM and can be driven by different physical mechanisms (cite: ejdetjarn22; yu21; bacchini20).

With an accurate measurement of the gas rotation velocities, we can derive the relative contribution of the different baryonic components, stars and gas, and of the dark matter (cite: lelli16b; mcgaugh04; vanalbada85; rubin80).

There have been a few attempts at performing such dynamical modelling of galaxies at $z \sim 4$, which suggest that those galaxies already host stellar bulges, or at least a massive compact stellar component (cite: lelli21; rizzo20; tsukui21).

Furthermore, the mass decomposition of rotation curves allows us to estimate the total stellar mass of the galaxies even without any observations of the stellar continuum, which are not available for most $z > 4$ galaxies.

With the complete information on the baryonic content of high-*z* galaxies, we can study how they populate different scaling relations such as the stellar-to-halo mass relation (SHMR), which quantifies the efficiency of dark matter halo to transform baryonic matter into stars (cite: moster10; behroozi13).

Moreover, we are able to study the evolution of one the tightest scaling relation in the study of galaxy evolution, the baryonic Tully-Fisher relation (BTFR) (cite: tullyfisher77; mcgaugh00).

This is an empirical relation that correlates the baryonic mass and circular speed of galaxies over several orders of magnitude in mass (cite: lelli16; iorio17) and has been used as benchmark for galaxy formation models and cosmological simulations (cite: governato07; posti19).

At $z=1$ and $z=2$, much work has been done on the stellar Tully-Fisher relation (cite: mcgaugh15). However, no clear consensus has been reached regarding its evolution (cite: tiley16; diteodoro16; uebler17; harrison17). Recently, (cite: fraternali21) investigated the location of two $z=4.5$ galaxies in the Early-Type-Galaxies (ETG) analogue version of the Tully-Fisher relation, which relates the rotational speed of inner CO discs of local ETGs with their stellar mass (cite: davis16). They found that the two galaxies at $z=4.5$ lie nearly in the same relation as local ETGs if one assumes that all their available gas is turned into stars.

The second key observable that we can extract through kinematic modelling is the gas velocity dispersion. Once all observational biases (instrumental spectral resolution and beam smearing) have been removed, we can considered the velocity dispersion as produced by thermal broadening and turbulence.

However, for \[CII\] observations at high-$z$ the thermal broadening can be considered negligible and even in HI observations of local galaxies, it is likely only important in the outer discs (cite: tamburro09).

Therefore, with an accurate measurement of the gas velocity dispersion we can attempt to study the origin of turbulence.

Turbulence plays a significant role in shaping the ISM of galaxies and influencing their evolution: it can arise from various factors such as mergers, gravitational instabilities, gas accretion, and feedback processes (cite: renaud14; tacchella16; kohandel20; orr20; nelson19).

While it is not yet clear what mechanisms are responsible for the turbulence of the ISM of high-*z*, stellar feedback and gravitational instabilities are usually considered the main drivers (cite: bournaud07; genzel11; krumholz16).

Despite the importance of understanding the dynamical state of high-*z* galaxies, there remains a paucity of detailed observations that allow for studies of their dark matter content and the drivers of turbulence.

Although there have been many studies showing the presence of velocity gradients in high-*z* galaxies (cite: shao22; jones21; smit18; hodge12), it is not clear how many of them are actually regularly rotating discs or perhaps poorly resolved disturbed systems, as the observations have varying levels of data quality. (cite: rizzo22) showed that both high angular resolution and high signal-to-noise ratio (SNR) are necessary to determine the dynamical state of galaxies (at least 6 resolution elements across the major axis). To date, the number of galaxies with such data quality at $z > 4$ is limited to a handful of cases.

In this paper, we focus on a sample of four disc galaxies at *z* $\sim$ 4.5 with accurate \[CII\] kinematic measurements from (cite: romanoliveira23). By modelling the mass contributions to the rotation curves, after correction for pressure support, we investigate the mass distribution of the dark matter, as well as the relative contributions of stars and gas to the total mass budget.

Additionally, we investigate the origin of the gas turbulence demonstrating that it can come from stellar feedback alone.

The paper is structured as follows: in Section [2](#sec:data_methods), we describe the data and methodology used in our analysis; in Section [3](#sec:results), we present our main results regarding the dynamical modelling of the rotation curves and the possible origins of the turbulence; in Section [4](#sec:discussion), we discuss the structure of the stellar mass component and where the galaxies fall into scaling relations within the context of the literature; in Section [5](#sec:conclusions), we summarise our main findings and implications. Throughout the paper, we adopt a $\Lambda$CDM cosmology from the 2018 Planck results (cite: planck20) and a Chabrier initial mass function (cite: chabrier03).

# Data and methods

In this Section, we describe the data used and the methodologies we employ in the analysis throughout the paper. We are analysing four galaxies at *z* $\sim$ 4.5 with rotating gas discs to study the disc dynamics and turbulence.

The galaxies in this sample were selected due to the quality of the data available in the ALMA archive, in terms of SNR, angular and spectral resolution. This makes the sample heterogeneous in terms of physical properties: one of the galaxies is a quasar host (BRI1335-0417), two are in a group (SGP38326-1 and SGP38326-2) and the remaining galaxy was originally discovered as a damped Lyman alpha system (cite: wagg14; oteo16; neeleman19).

To perform the analysis presented in the following Sections, in addition to the kinematic profiles from (cite: romanoliveira23), we need estimates of the star formation rates and spatially resolved mass distributions of gas and stars.

## Molecular gas mass

The galaxies of our sample have previous estimates of the molecular gas masses (cite: wagg14; jones16; neeleman20; oteo16). However, these were obtained from CO luminosities in different rotational transitions and assuming different $\alpha_{\mathrm{CO}}$ values (cite: romanoliveira23). Ideally, the total molecular gas mass is best estimated from the CO (J=1-0), although at *z* $\gtrsim 0.4$ this line is redshifted to frequency ranges not covered by current facilities.

In Table [1](#tab:colum), we report the CO luminosities for the lowest CO transitions available in the literature for the galaxies in our sample. We note that the measurement for SGP38326 is for the whole system and it is estimated that SGP38326-1 is 2.5 times more massive than SGP38326-2 (cite: oteo16).

As described in Section [2.6](#sec:dynmod), we determine the total gas mass of the system independently from the gas emission through the mass decomposition of the rotation curves.

Hence, we use initial estimates of the gas mass in the Monte Carlo algorithm we use for the mass decomposition by scaling the values in Table [1](#tab:colum) using a normalisation factor that accounts for conversions between CO luminosities and gas masses (details in Section [2.6](#sec:dynmod)).

+:-------------+:--------------+:--------------------------------------------+
|              | CO transition | Luminosity                                  |
+--------------+               +---------------------------------------------+
|              |               | 10$^{10}$ (K km s$^{-1}$ pc$^2$)            |
+--------------+---------------+---------------------------------------------+
| BRI1335-0417 | J=2-1         | 10.9 $\pm$ 0.8 $^{a}$, 7.3 $\pm$ 0.6 $^{b}$ |
+--------------+---------------+---------------------------------------------+
| J081740      | J=2-1         | 2.4 $\pm$ 0.7 $^{c}$                        |
+--------------+---------------+---------------------------------------------+
| SGP38326     | J=4-3         | 15.4 $\pm$ 1.6 $^{d, e}$                    |
+--------------+---------------+---------------------------------------------+
|              |               |                                             |
+--------------+---------------+---------------------------------------------+

: CO luminosities of our sample.

**Notes.** References: $^{a}$ (cite: jones16); $^{b}$ (cite: wagg14); $^{c}$ (cite: neeleman20); $^{d}$ (cite: oteo16); $^{e}$ (cite: fudamoto17).

## Star Formation Rates

The global star formation rate (SFR) of the galaxies J081740, SGP38326-1 and SGP38326-2 were derived from the total IR luminosity ($166 M_{\odot}$ yr$^{-1}$, $1830 M_{\odot}$ yr$^{-1}$, $882 M_{\odot}$ yr$^{-1}$, respectively), as reported by (cite: neeleman20) and (cite: oteo16).

For BRI1335-0417, there have been studies deriving the SFR from fitting the spectral energy distribution (SED) and from the CO(J=7-6) luminosity, both resulting in a total SFR of $\sim$ 5000 $M_{\odot}$ yr$^{-1}$ (cite: lu18; wagg14). However, more recently, (cite: tsukui23) rederived the SFR by taking into account the spatially resolved nuclear emission and thus excluding the contribution of the AGN to the dust heating, yielding a more accurate SFR of $1700^{+500}_{-400} M_{\odot}$ yr$^{-1}$.

## Dust and gas surface profiles

To perform the mass decomposition of the rotation curves, we need to consider the surface density profiles of the baryonic components in the galaxies.

Since there are no spatially-resolved data covering the rest-frame optical and near infrared emission, the stellar surface density profiles of the galaxies in our sample are unknown.

Therefore, for the stars we make the assumption that it should have an effective radius in between that of the dust and the gas, this will be discussed in further detail in Section [2.6](#sec:dynmod). For the gas, we assume that the \[CII\]-158 $\mu$m emission traces the total gas distribution of the galaxies and therefore the gas surface density is proportional to the \[CII\] surface brightness.

Considering that the galaxies in our sample have resolved ALMA data that comprise the dust continuum and the \[CII\]-158 $\mu$m line-emission, we can make use of the total map of the dust and the \[CII\] emission to derive surface brightness properties.

First, we separate the line-emission from the continuum and produce a dust-continuum only image and a \[CII\] line-emission only datacube, with the `mfs` and `cube` spectral definition modes in `CASA`, respectively (cite: mcmullin07).

With the datacube, we obtain the \[CII\] total emission map by integrating the line emission along the velocity axis of the datacube.

For more details on the ALMA data reduction and imaging refer to (cite: romanoliveira23).

We derive the surface brightness of the galaxies by fitting the \[CII\] and dust continuum maps with a two-dimensional Sérsic profile (cite: sersic68), given by

$$\begin{equation}
    I(x,y) = I(R) = I_e \exp{\left\{ -b_n \left[ \left ( \frac{R}{R_{\mathrm{eff}}} \right) ^{(1/n)} -1 \right] \right\}},
\end{equation}$$

where $I_e$ is the surface brightness at the effective radius $R_{\mathrm{eff}}$, $n$ is the Sérsic index and $b_n$ is a constant defined as such that the profile contains half the total luminosity at $R_{\mathrm{eff}}$ and can be solved for numerically (cite: graham05). We use the function `Sersic2D` as implemented in `Astropy` (cite: astropycollab13; astropycollab18; astropycollab22), which takes into account the geometric parameters defining the 2D distributions, the ellipticity $\epsilon$, the position angle (PA) and the centre.

To account for the spatial resolution of the data, we convolve the model to the same resolution as the data. We then minimise the residuals to find the best-fit model using `DYNESTY`, a python package for estimating Bayesian posteriors and evidences using the Dynamic Nested Sampling algorithm (cite: speagle20; koposov22; skilling04; skilling06).

In the fitting, we minimise the residuals using a chi-square likelihood, $(|\mathcal{D} - \mathcal{M}|)^2 / \sigma_{\mathrm{eff}}^2$. We note that, we weight the residuals by an effective uncertainty related to asymmetry in the galaxy (cite: marasco19). This is because, given that our model is axi-symmetric, this provides a more realistic estimate of the parameter errors than only accounting for the background noise in the data. In this case, based on the methodology employed by (cite: marasco19), we rotate the moment 0 map of the emission by 180$^\circ$ and subtract it from the original data. We then calculate the standard deviation of this residual map and use it as the $\sigma$ in the chi-square minimisation.

For both the gas and the dust we leave all the following parameters free: effective radius ($R_{\mathrm{eff}}$), surface brightness at the effective radius ($I_e$), galactic centre ($x_0$, $y_0$), ellipticity ($\epsilon$) and PA.

We use `DYNESTY` to compute the Bayesian posterior distribution of these parameters considering uniform priors.

As for the Sérsic index, we perform a preliminary fit letting $n$ vary within 0.2 and 10.0. However, we notice that for the gas and dust emission of the galaxy J081740 and for the gas distribution of the SGP38326 system, the free *n* fit does not converge, this is likely due to the data not having enough information to constrain the parameters. Moreover, for the free Sérsic index fit of the dust emission of SGP38326-1 and SGP38326-2, we find an $n$ of 1.4 and 1.5, respectively. For the gas and dust emission of BRI1335-0417, we find $n = 1.5$ and $2.6$, respectively.

We conclude that the gas and dust emission of the galaxies are reasonably described with a Sérsic index around 1, as for the majority of our tests that have converged we find an $n<2$.

Given that a Sérsic index of 1 significantly simplifies our rotation curve decomposition (see Section [2.6](#sec:dynmod)) we prefer to fix it to 1 in our fits for all galaxies, with the only exception of the dust emission of BRI for which we leave $n$ free.

We report our best-fit parameters in Section [3.1](#sec:res_sb); the maps are well reproduced with minimal residuals.

Finally, we assume the discs to be razor-thin such that the inclination is related to the ellipticity by $\cos^2{(i)} = 1 - \epsilon$.

After deriving the \[CII\] surface brightness profiles as an exponential profile, we use the best-fit effective radius to obtain the gas disc scale-length as $R_{\rm gas} = R_{\rm eff, [CII]}/1.678$.

## Gas kinematics

The gas kinematic properties of these galaxies were derived using the \[CII\] 158 $\mu$m emission line, observed with ALMA. These observations have an average SNR of 3 - 5 per pixel and velocity channel, and spatial resolutions in the range of 0.13" - 0.24", which correspond to 6 - 10 independent radial elements across the major axis of the galaxies.

The kinematic modelling was performed with $^{\text{3D}}$`BAROLO` (cite: diteodoro15), which fits the full emission line datacube considering an axisymmetric rotating disc model. For more details we refer to (cite: romanoliveira23). Here we use the kinematic profiles obtained in our previous paper, namely the rotation curves to perform the dynamical modelling and the velocity dispersion profiles to study the turbulence in the discs.

## Circular speed of the gas

For galaxy discs having a rotation support that largely dominate over the pressure support ($V/\sigma \gg 1$), the rotation velocity is essentially equal to the circular speed of a test particle that is moving in perfect circular obits under the influence of the galaxy gravitational potential, $$\begin{equation}
    V_{\mathrm{c}}^2 = R \: \left( \frac{\partial \Phi}{\partial R} \right) \approx V_{\mathrm{rot}}^{2},
\end{equation}$$ where $\Phi$ is the gravitational potential, $V_{\mathrm{c}}$ is the circular speed and $V_{\mathrm{rot}}$ is the gas rotation velocity. For galaxies with $V_{\mathrm{rot}}$ more similar to $\sigma$, the pressure support should be considered.

Assuming that the velocity ellipsoid is isotropic and the disc thickness is constant with radius (cite: binney08; iorio17), we can apply the asymmetric drift correction, $V_{\mathrm{A}}$, as follows

$$\begin{equation}
\label{eq:adc}
    V_{\mathrm{c}}^2 = R \: \left( \frac{\partial \Phi}{\partial R} \right) = V_{\mathrm{rot}}^{2} + V_{\mathrm{A}}^{2} = V_{\mathrm{rot}}^{2} - R \sigma^2 \frac{\partial \ln (\sigma^2 \Sigma_{\rm gas})}{\partial R}.
\end{equation}$$

Therefore, to obtain $V_{\mathrm{A}}$, it is necessary to obtain the gas surface density $\Sigma_{\mathrm{gas}}$, the velocity dispersion $\sigma$ for each radial orbit $R$.

We apply this correction to the four galaxies, as described in Appendix [6](#ap:adc), but we observe that it is only significant for BRI1335-0417 given its low V/$\sigma$ compared to the other galaxies.

## Mass Decomposition

After obtaining the circular speed of the galaxies as a function of radius, we decompose it considering the contribution of stars, gas and DM as follows

$$\begin{equation}
\label{eq:vc}
    V_{\mathrm{c}}(R) = \sqrt{-R \left(\frac{\partial \Phi_{\mathrm{star}}}{\partial R} + \frac{\partial \Phi_{\mathrm{gas}}}{\partial R} + \frac{\partial \Phi_{\mathrm{DM}}}{\partial R} \right) } = \sqrt{ V^2_{\mathrm{star}} + V^2_{\mathrm{gas}} + V^2_{\mathrm{DM}} },
\end{equation}$$

where $\Phi_{\rm i}$ is the gravitational potential contributed by the $i$-matter component (with $i$ star, gas and DM) and $V_{\mathrm{star}}$, $V_{\mathrm{gas}}$, $V_{\mathrm{DM}}$ are the contribution to the circular speed from the stars, gas and dark matter, respectively.

We note that we need to make a few major assumptions regarding the baryonic components. For the stars, we do not have any resolved information on the near-infrared stellar continuum of the galaxies and therefore no prior estimate of the stellar masses. For the gas, we do not have precise estimates of the total gas mass due to uncertainties in the CO line ratios and $\alpha_{\rm CO}$ conversion factor.

Below we describe how we model each of the three, while a summary of our assumptions is shown in Table [2](#tab:priormm).

1.  Stellar component: we assume that the projected light distribution follows a Sérsic profile.

    We use a density–potential relation for a deprojected spherical Sérsic profile from (cite: terzic05) to describe the circular speed contributed by the stellar component as

    $$\begin{equation}
        V_{\mathrm{star}}(R, M_{*}, R_{\mathrm{eff},*}, n) = \sqrt{\frac{G M_{*}}{R} \frac{\gamma(n(3-p)),b(R/R_{\mathrm{eff},*})^{1/n}}{\Gamma(n(3-p))}},
    \end{equation}$$

    where $M_{*}$ is the total stellar mass, $R_{\mathrm{eff},*}$ is the stellar effective radius and $n$ is the Sérsic index. Moreover, the parameters $p$ and $b$ are a function of $n$, and $\gamma$ and $\Gamma$ are the incomplete and complete gamma functions, respectively.

    We let the log of the stellar mass vary uniformly between 9 and 12. The Sérsic index is free to vary uniformly between 0.2 and 10. Lastly, the effective radius is free to vary uniformly between the effective radius of the dust and that of the \[CII\] emission. This is a reasonable assumption as different studies showed that the stellar continuum emission tends to be more extended than the dust continuum emission at high-*z* (cite: gillman23; colina23; tadaki20b; kaasinen20).

    We note that some simulations suggest that the stellar continuum of high-*z* galaxies may be up to four times less extended than the dust emission (cite: popping22; cochrane19). As a sanity check, we ran some tests with a larger prior in the stellar radius, covering a range between 0.2 times the effective radius of the dust and twice that of the \[CII\] emission. We find that it does not impact the estimates of the other parameters significantly nor does it lead the effective radius parameter to converge to a preferred value.

    We highlight that our sample have not (yet) been observed with the James Webb Space Telescope (JWST) and that the reddest band available of the Hubble Space Telescope (HST) only covers the rest-frame far-UV emission of these galaxies. Given that these galaxies are also very dusty, we have no significant prior knowledge on the stellar component of our sample.

2.  Gas component: we assume this component to be a razor-thin disc following an exponential disc profile so that the circular speed contributed by the gas is

    $$\begin{equation}
        V_{\mathrm{gas}}(R, M_{\mathrm{gas}}, R_{\mathrm{gas}}) = \sqrt{\frac{ 2 G M_{\mathrm{gas}} y^2}{R_{\mathrm{gas}}} (I_{0}(y)K_{0}(y) - I_{1}(y)K_{1}(y) ) },
    \end{equation}$$

    where $R_{\rm gas}$ is the scale length of the disc, $M_{\rm gas}$ is the total gas mass, $I_{0}, I_{1}, K_{0}, K_{1}$ are the modified Bessel functions and y = $R/(2 R_{\mathrm{gas}})$ (cite: binney08). We assume that the gas disc has the same distribution of the \[CII\] emission and therefore the same disc scale length $R_{\mathrm{gas}}$. For the mass, we assume that the total gas mass is given by the CO luminosities reported in Table [1](#tab:colum) times a gas mass normalisation ($M_{\mathrm{gas}}$ = $L_{\mathrm{CO}}$ $\times$ gas_norm).

    This normalisation encompasses the conversion factor between the CO luminosity and the molecular gas mass ($\alpha_{\mathrm{CO}}$), as well as the line ratio between the CO(J=1-0) and the CO transition observed (r$_l$). We use a uniform prior ranging from 0 to 10, where the former represents the complete lack of gas in the galaxy and 10 is a sufficiently high number to cover the range of expected $\alpha_{\mathrm{CO}}$ (cite: dunne22; gong20; papadopoulos18; bolatto13; narayanan11) and r$_l$ (cite: boogaard20; yang17; kamenetzky16; dacunha13). We highlight the fact that both of these numbers are highly uncertain even in the local Universe, therefore we choose a conservative uniform prior that can flexibly cover many values of r$_l$ and $\alpha_{\mathrm{CO}}$. The $\alpha_{\mathrm{CO}}$ factor is usually taken to be either 0.8 for starburst galaxies or 4.0 for normal star-forming galaxies, however these values are highly sensitive to metallicity, gas surface density other ISM conditions (cite: dunne22; gong20; papadopoulos18; bolatto13; narayanan11). Similarly, the CO line ratios are uncertain, especially at high-*z*, as the CO spectral-line energy distributions (SLEDs) vary within a wide range of values and can greatly differ among different galaxies (cite: boogaard20; yang17; kamenetzky16; dacunha13).

3.  Dark matter halo component: we assume this component to be a spherical NFW halo profile (cite: navarro97), whose circular speed is given by

    $$\begin{equation}
    \begin{split}
    V_{\mathrm{DM}}(R, R_{200}, M_{200}, c_{200}) = & \\
    = \sqrt{\frac{G M_{200}}{R_{200}} \frac{\ln{(1+ c_{200} x)} - c_{200} x / (1 + c_{200} x)}{x[\ln{(1+c_{200})}- c_{200} / (1+c_{200})]}},
    \end{split}
    \end{equation}$$

    where $c_{200}$ is the concentration of the NFW dark matter halo, $M_{200}$ and $R_{200}$ are the dark matter halo virial mass and radius, respectively, and $x = R/ R_{200}$.

    We assume a concentration ($c_{200}$) fixed at 3.4, which is the typical value of concentration for a wide range of CDM halo masses at *z* $\sim$ 4.5 (cite: dutton14; correa15; child18). The virial CDM halo mass ($M_{200}$) is incorporated in the fit through the baryon fraction ($f_{\mathrm{bar}}$), which is the baryonic (star + gas) mass divided by the virial mass of the dark matter halo. We let $f_{\mathrm{bar}}$ vary between the cosmological baryon fraction of 0.187 (cite: planck20) and a baryon fraction of 10$^{-6}$, as an extreme limit of a highly DM dominated galaxy.

    If we take the literature estimates for the gas mass of the galaxies in our sample as the total baryonic mass ($\sim 10^{10} M_{\odot}$), then the limits in $f_{\rm bar}$ would result in a CDM halo mass in the range of $\sim 5 \times 10^{10} - 10^{16} M_{\odot}$. We let the baryon fraction, $f_{\mathrm{bar}}$, vary uniformly in a log space.

To obtain the best-fit model of the mass decomposition, we use Equation [\[eq:vc\]](#eq:vc) to reproduce the observed circular speed of the galaxy using `DYNESTY`.

We compute Bayesian posterior distribution of the following free parameters: stellar mass ($M_*$), stellar effective radius ($R_{\mathrm{eff,*}}$), stellar Sérsic index ($n$), gas mass normalisation (gas_norm), baryon fraction ($f_{\mathrm{bar}}$).

These priors and assumptions were used to obtain the fiducial models discussed in Section [3.2](#sec:res_dy). We have also tested several different models considering different assumptions and priors, which are not used for the fiducial models although we discuss the implications of these different tests in Section [3.2](#sec:res_dy).

|  |  |  |  |
|:--:|:---|:---|:---|
| Component | Parameter | Prior Type | Value Range |
|  | $\log{(M_*/M_{\odot})}$ | Uniform log | 9 – 12 |
|  | $R_{\mathrm{eff},*}$ (kpc) | Uniform | $R_{\mathrm{eff}, \mathrm{dust}}$ – $R_{\mathrm{eff}, \mathrm{[CII]}}$ |
|  | $n$ | Uniform | 0.2 – 10 |
|  | gas_norm | Uniform | 0 – 10 |
|  | $R_{\mathrm{gas}}$ (kpc) | Fixed | $R_{\mathrm{[CII]}}$ |
|  | $\log{(f_{\mathrm{bar}})}$ | Uniform log | -6 – -0.73 |
|  | $c_{200}$ | Fixed | 3.4 |
|  |  |  |  |

: Priors used in the rotation curve decomposition.

Notes. The stellar component is assumed to be spherical, with a corresponding projected light distribution described by a Sérsic profile, defined by a stellar mass ($M_*$), an effective radius ($R_{\mathrm{eff},*}$) and a Sérsic index ($n$). The gas is described by an exponential disc defined by a disc scale length ($R_{\mathrm{gas}}$) fixed to the scale length of the \[CII\] emission and a gas mass ($M_{\mathrm{gas}}$) that is defined as as the CO luminosity times a gas normalisation (gas_norm). The CDM halo follows an NFW profile with a concentration fixed at 3.4. The CDM halo virial mass is calculated from the baryon fraction which varies between the cosmological baryon fraction and a baryon-dominated halo (see main text for further explanation).

## Supernova explosion driven turbulence

To study whether the stellar feedback can be considered as a valid candidate for explaining the measured turbulence, we use a simple model in which we assume that the turbulence of the gas is fed by the energy injected in the ISM by supernova explosions (cite: bacchini20). Here, we neglect the contribution from supernova type Ia (SNIa) as high-*z* galaxies tend to be dominated by supernova type II due to their high star formation rate and young ages (cite: rodney14). Therefore, the energy input from supernovae is given by

$\dot{E}_{\mathrm{SN}} = {\eta}  \: E_{\mathrm{SNII}}  \:  \xi$,

where $\eta$ is the SNII efficiency defined as the percentage of the total supernova energy that is injected in the ISM as kinetic energy; $E_{\mathrm{SNII}}$ is the total energy per SNII explosion and it is equal to $10^{51}$ erg; and $\xi$ is the expected number rate of SNII given the SFR of each galaxy.

We note that hydrodynamical simulations of supernova remnant evolution tend to find values of $\eta$ around $\sim~0.1$ or less (cite: fierlinger16; ohlin19). Assuming a Chabrier IMF, the rate of SNII is given by $\xi = 0.01 \: M_{\odot}^{-1} \: \times \mathrm{SFR}$ (cite: mo10). The turbulence due to the supernova energy input is dissipated with a timescale $\tau = h / \sigma$, where h is the disc scale height (cite: maclow99). Therefore, the total supernova energy input can be rewritten as

$$\begin{equation}
\label{eq:snii}
     E_{\mathrm{SN}} = {\eta}  \: E_{\mathrm{SNII}}  \:  \xi \: h \: \sigma^{-1}.
\end{equation}$$

If one assumes $\eta$ to be 1, then Equation [\[eq:snii\]](#eq:snii) represents the maximum injectable energy from SNII into the ISM. Then, we can compare this to the observed turbulent energy in the ISM given the measured gas velocity dispersion in a gas disc, given by

$$\begin{equation}
\label{eq:turb}
E_{\mathrm{turb}} = 3/2 \: M_{\mathrm{gas}} \: \sigma^2,    
\end{equation}$$

where $M_{\mathrm{gas}}$ is the total molecular gas mass of the disc and $\sigma$ is the line-of-sight observed velocity dispersion of the gas that we assume to be isotropic.

# Results

In this Section, we present the main findings of our analysis, namely the surface brightness of the dust and \[CII\] 158 $\mu$m emission, the mass decomposition, the stellar masses and star formation rates of the galaxies.

## Surface Brightness

Using the method described in Section [2](#sec:data_methods), we found the best-fit parameters defining the surface brightness profiles for the \[CII\] and dust emission. In Figure [1](#fig:sb_gas), we show the comparison between \[CII\] data and model in 2D and 1D for the 4 galaxies of our sample. The 1D surface brightness is obtained after averaging the emission along rings with a separation of one third of the beam of the observations; these profiles are not deprojected.

Figure [2](#fig:sb_dust) shows the surface brightness of the dust emission for J081740, while equivalent visualisation for the rest of sample is shown in Figure [10](#fig:a_dustsb).

We note that for the SGP38326 group we had to fit the emission of the two main galaxies simultaneously in order to avoid biases due to the diffuse emission of each galaxy influencing the fit of the other. In this case, we also masked the emission of the small companion (SGP38326-3).

In Appendix [7](#ap:corner_sb), we show the corner plots of the best-fits shown in Figure [1](#fig:sb_gas) and [2](#fig:sb_dust).

We summarise the properties of the best-fit models of the surface brightness in Table [\[tab:surfbrightness\]](#tab:surfbrightness). We note that, as discussed in Section [2.3](#sec:met_sb), for both the dust and gas we fit a 2D Sérsic profile with $n$ fixed to 1 (equivalent to an exponential disc), given that the free Sérsic index model does not significantly improves the fits. The only exception is for the dust emission of BRI1335-0417, which we keep free as it is significantly better described by a Sérsic index of $n = 2.6 \pm 0.1$.

We note that for some of the galaxies, the surface brightness in the outer regions tends to be slightly overestimated by the model. This is due to the fact that the emission of the data in the outer parts is less axisymmetric than the model and that the residuals are minimised in a way that gives more importance to the bright central regions of the galaxies. Given that we only use the effective radii of these fits in the following analysis, we conclude that our best-fit models are sufficiently good representations of the shape and extent of the dust and gas emission.

![](figures/surf_bright_gas_fixedn.pdf)

![](figures/surf_bright_dust_fixedn_j0817.pdf)

|  |  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|:--:|
|  |  | $I_{\mathrm{e, gas}}$ | $I_{\mathrm{e, dust}}$ | $R_{\mathrm{eff}}$ | $\epsilon$ | PA |
|  |  | (mJy/beam km/s) | (mJy/beam) | (kpc) |  | (deg) |
|  | gas | 44.9 $^{+0.7}_{-0.6}$ | \- | 3.06 $^{+0.03}_{-0.04}$ | 0.20 $^{+0.01}_{-0.02}$ | 6 $^{+2}_{-3}$ |
|  | dust | \- | 0.97 $\pm 0.07$ | 1.69 $^{+0.08}_{-0.06}$ | 0.22 $\pm$ 0.02 | -2 $^{+3}_{-2}$ |
|  | gas | 9.9 $^{+0.5}_{-0.4}$ | \- | 3.2 $^{+0.2}_{-0.1}$ | 0.42 $\pm 0.03$ | 125 $\pm$ 3 |
|  | dust | \- | 0.17 $\pm 0.01$ | 1.79 $^{+0.09}_{-0.10}$ | 0.56 $\pm 0.04$ | 109 $^{+3}_{-2}$ |
|  | gas | 6.8 $\pm 0.2$ | \- | 3.2 $\pm 0.1$ | 0.24 $\pm$ 0.02 | 83 $\pm$ 3 |
|  | dust | \- | 0.75 $\pm 0.01$ | 1.29 $\pm 0.01$ | 0.04 $\pm$ 0.01 | -49 $\pm$ 8 |
|  | gas | 6.3 $\pm 0.3$ | \- | 2.4 $\pm 0.1$ | 0.50 $\pm 0.03$ | 85 $\pm 2$ |
|  | dust | \- | 0.57 $\pm 0.01$ | 1.08 $\pm 0.02$ | 0.25 $\pm$ 0.02 | 112 $\pm$ 3 |
|  |  |  |  |  |  |  |

**Notes.** Best-fit parameters of the 2D Sérsic fits of the gas and dust distributions: surface brightness at the effective radius ($I_{\mathrm{e}}$); effective radius ($R_{\mathrm{eff}}$); ellipticity ($\epsilon$); and position angle (PA). All maps were fitted with a Sérsic index ($n$) fixed to 1, except for the dust emission of BRI1335-0417 where $n$ was left free and led to $n = 2.6 \pm 0.1$.

## Mass decomposition of the rotation curves

Here, we present the fiducial dynamical models of the galaxies in our sample. Following the methods described in Section [2.6](#sec:dynmod) we decompose the rotation curves of the galaxies into three mass components: stars, gas and a CDM halo. The procedure employed for the dynamical modelling of the galaxies J081740, SGP38326-1 and SGP38326-2 is the same: a single spherical Sérsic profile for the stars with free $n$, an exponential profile considering a razor-thin disc for the gas following the \[CII\] surface brightness and a spherical NFW CDM halo with the priors described in Table [2](#tab:priormm). However, for the galaxy BRI1335-0417, a different approach was taken, wherein the baryon fraction was fixed to the cosmological baryon fraction. This is due to the fact that the literature estimates for the gas mass of BRI1335-0417 are too high for its rotation curve. Therefore, as our fiducial model we assume a scenario that maximises the gas mass while still containing a marginally realistic CDM halo which provides an upper limit on the estimate of the total baryonic mass. We discuss this further in Appendix [8](#ap:dynmod).

In Figure [3](#fig:dy_rotcur), we show the rotation curves derived from the \[CII\] kinematics. These rotation curves are corrected for pressure support following Equation [\[eq:adc\]](#eq:adc), so that we are plotting the circular speeds (further description of this is provided in Appendix [6](#ap:adc)). Similarly to local galaxies, the shapes of the rotation curves of $z \sim 4$ galaxies are diverse: BRI1335-0417 has a bump in the inner region that resembles the dynamical signature of a bulge; the rotation curves of J081470 and SGP38326-1 seem to flatten at large radii; and the rotation curve of SGP38326-2 has a shallow gradient. In Figure [3](#fig:dy_rotcur), we overlap the contributions to the circular speeds by the stellar component, the gas disc and the CDM halo, as well as the total circular speed of our model (in black) that matches the observed rotation curve (in blue). In Table [\[tab:dy_fid\]](#tab:dy_fid), we display the best-fit parameters that define the different components shown in Figure [3](#fig:dy_rotcur). Additionally, in Appendix [8](#ap:dynmod) we show the posterior distribution of the best-fit parameters and discuss some extra tests to probe the limitations of our data.

![](figures/rotcurv.pdf)

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Object | $\log{(M_*/M_{\odot})}$ | $R_{\mathrm{eff, *}}$ (kpc) | $n$ | gas_norm | $\log{(f_{\rm bar})}$ | $\log{(M_{\rm gas}/M_{\odot})}$ | $\log{(M_{200}/M_{\odot})}$ |
| BRI1335-0417 | 10.4 $^{+0.1}_{-0.1}$ | 2.3 $^{+0.5}_{-0.4}$ | 6.9 $^{+2.1}_{-2.1}$ | 0.06 $^{+0.06}_{-0.04}$ | *-0.728* | 9.8 $^{+0.3}_{-0.5}$ | *11.2* |
| J081740 | 10.6 $^{+0.2}_{-0.2}$ | 2.4 $^{+0.5}_{-0.5}$ | 6.7 $^{+2.3}_{-2.4}$ | 1.4 $^{+1.2}_{-0.9}$ | -1.5 $^{+0.5}_{-0.7}$ | 10.5 $^{+0.3}_{-0.5}$ | 12.3 $^{+0.7}_{-0.5}$ |
| SGP38326-1 | 11.0 $^{+0.2}_{-0.2}$ | 2.2 $^{+0.7}_{-0.6}$ | 6.3 $^{+2.5}_{-2.4}$ | 1.9 $^{+0.6}_{-0.9}$ | -1.7 $^{+0.7}_{-0.9}$ | 11.3 $^{+0.1}_{-0.3}$ | 13.2 $^{+0.9}_{-0.7}$ |
| SGP38326-2 | 10.3 $^{+0.4}_{-0.6}$ | 1.7 $^{+0.4}_{-0.4}$ | 5.3 $^{+3.1}_{-2.9}$ | 2.5 $^{+1.1}_{-1.4}$ | -2.2 $^{+1.0}_{-1.3}$ | 11.1 $^{+0.2}_{-0.3}$ | 13.3 $^{+1.3}_{-1.0}$ |
|  |  |  |  |  |  |  |  |

**Notes.** Best-fit parameters of our dynamical model: stellar mass ($M_{*}$); stellar effective radius ($R_{\mathrm{eff,*}}$); stellar Sérsic index ($n$); normalisation of the gas mass (gas_norm); baryon fraction ($f_{\mathrm{bar}}$). We also show the total gas mass ($M_{\mathrm{gas}}$) derived as gas$\_$norm $\times$ L$_{\rm CO}$ (see Table [1](#tab:colum)) and the CDM halo mass ($M_{200}$) derived as $M_{\rm bar} (1 - f_{\rm bar}) / f_{\rm bar}$. For BRI1335-0417, we report the values of $f_{\rm bar}$ and $M_{200}$ in italic as they are kept fixed in our fiducial model.

|              |                    |                          |                |
|:-------------|:------------------:|:------------------------:|:--------------:|
| Object       | $f_{\mathrm{gas}}$ | $R_{\rm eff, bar}$ (kpc) | $f_{\rm disc}$ |
| BRI1335-0417 |  0.16 $\pm$ 0.12   |           2.9            |      0.69      |
| J081740      |  0.52 $\pm$ 0.24   |           2.8            |      0.63      |
| SGP38326-1   |  0.68 $\pm$ 0.17   |           2.8            |      0.78      |
| SGP38326-2   |  0.87 $\pm$ 0.22   |           2.0            |      0.72      |
|              |                    |                          |                |

: Other properties derived from the results of the mass decomposition.

**Notes.** Parameters derived from the results of the mass decomposition: the gas fraction ($f_{\mathrm{gas}}$); the effective baryonic radius as the radius that comprises half of the baryonic mass ($R_{\rm eff, bar}$); and the disc fraction, as the fraction of baryons to dark matter inside $R_{\rm eff, bar}$ ($f_{\rm disc}$).

We find that our rotation curve decomposition can constrain the stellar mass for the four galaxies reasonably well, placing our sample in a considerably massive regime, with stellar masses in between $\log(M_{*}/M_{\odot}) = 10.3 - 11.0$.

The accuracy of these estimates is due to the fact that the stellar component dominates the central region of the rotation curve, as a consequence, the inner shape of the rotation curve can only be reproduced by a massive stellar component. We find that this is only possible with stellar profiles with a high Sérsic index, indicating that a massive compact stellar distribution, such as a bulge, is present in all of the four galaxies. We note that the effective radius of such a component cannot be constrained with precision with the current data, although, we use physically motivated priors that provide plausible limits. Moreover, in spite of all the assumptions involved, we obtain effective radii for the stellar component compatible with values recently found with JWST observations of $z > 2$ galaxies (cite: ormerod24; tadaki23).

The gas mass is constrained for J081740, SGP38326-1 and SGP38326-2, while for BRI1335-0417 we find an upper limit that is driven by the imposition of the cosmological baryon fraction. In general, the values of the gas masses have larger uncertainties than those for the stellar masses. This is because at small radii the stellar component is dominant, while at larger radii the main contribution to the rotation curve comes from both the gas and the CDM halo. Given the low concentration of DM at *z* $\sim$ 4 and that we are still only probing the relatively inner regions of these galaxies, the contribution of the CDM halo is hard to discern from the contribution of the gas.

For example, considering a concentration of 3.4, an NFW halo with a virial mass of $10^{12} M_{\odot}$ produces a circular speed of about only 90 km s$^{-1}$ lower than a halo with a virial mass of $10^{13} M_{\odot}$ at 3 kpc from the galactic centre.

Combining this with the large uncertainties regarding the conversion between the CO luminosity and the gas mass then it becomes difficult to disentangle and constrain both the gas mass and the CDM halo mass with the current data.

However, we can clearly see a pattern regarding the DM content of these galaxies in which they all prefer baryon dominated models as seen by the posterior distributions that has a maximum close to the lower edge of the prior (see Figure [14](#fig:a_dy)).

Finally, we find that the gas mass of the galaxies range between $\log{(M_{\rm gas}/M_{\odot})} = 9.8 - 11.3$ and we find CDM halos masses ranging between $\log{(M_{200}/M_{\odot})}  = 11.2 - 13.3$ with baryon fractions of 0.006 up to the cosmological baryon fraction of 0.187.

In Table [3](#tab:dy_more), we report other relevant properties that can be derived by the direct results of the mass decomposition: we show the gas fractions, defined as $f_{\mathrm{gas}} = M_{\mathrm{gas}}/M_{\mathrm{bar}}$; the baryonic effective radius, defined as the radius that comprises half of the baryonic mass ($R_{\rm eff, bar}$); and the disc fraction, defined as the fraction of baryons to dark matter inside the baryonic effective radius ($f_{\rm disc}$). Recently, (cite: blandhawthorn23) showed that these parameters can be used to predict the capability of a galaxy to form a stable bar. The four galaxies in our sample are above the thresholds set in (cite: blandhawthorn23), indicating that all of these discs have high enough baryon concentrations that could enable the quick formation of a stable bar.

To further support this prediction, (cite: tsukui24) performed a thorough analysis of the \[CII\] and dust emissions in BRI1335-0417 suggesting the presence of a strong bar.

Moreover, in general, our sample shows a diverse range of gas fractions, compatible to those found at $z > 1$ (cite: tacconi20; dessauges20; aravena16; decarli16).

## Star Formation Rates and Stellar Masses

In Figure [4](#fig:ms), we show the position of our galaxies in the SFR vs stellar mass plane, compared to the main-sequence relation at $z =  4.5$ from (cite: speagle14). For our galaxies, we use the stellar masses derived from the mass decomposition of the rotation curves. The SFRs are derived from IR luminosities and converted to a Chabrier IMF as described in Section [2.2](#met:sfr). We also show two thresholds for starburst galaxies: 4 times above the main-sequence (cite: rodighiero11) and the starburst bi-modality (cite: rinaldi22), which is an empirical division between main-sequence and starburst galaxies at high-*z* in the specific SFRs first proposed by (cite: caputi17).

We conclude that our sample is diverse in terms of SFR: J081740 is a main-sequence galaxy, BRI1335-0417 and SGP38326-2 are both starburst and SGP38326-1 is borderline into the starburst region.

![](figures/ms.pdf)

## Origin of Turbulence

As was pointed out in the introduction to this paper, the velocity dispersion measured in cold gas components, in particular CO and \[CII\], is mostly contributed by turbulence as thermal broadening can be considered negligible. An accurate estimation of the velocity dispersion allows us to investigate the potential drivers of turbulence within the ISM.

In high-*z* galaxies, gravitational instabilities and star formation feedback are believed to be the primary drivers of gas turbulence (cite: bournaud07; genzel11; krumholz16). These galaxies have higher gas fractions and densities compared to those in the local Universe (cite: tacconi10; tacconi13; decarli16; scoville17). This abundance of gas not only promotes elevated star formation rates but can also cause more significant disruptions to the equilibrium of the gas disc (cite: tacconi13).

Here, we investigate which of these two possible scenarios are more likely: gas turbulence driven by gravitational instabilities in the disc and turbulence driven by stellar feedback.

### Gravitational Instabilities

To test the hypothesis that the gas turbulence in our sample is driven by gravitational instabilities, we compare the observed gas velocity dispersions to those expected by the analytical model from (cite: krumholz18). This model considers an axisymmetric disc of gas and stars in a dark matter halo, where the gas and stars have isotropic velocity dispersions and the disc is in both vertical hydrostatic and energy equilibrium. The model accounts for the energy contributed by star formation feedback and gravitational potential energy from inward gas flow. One main assumption of this model is that the gas in the disc self-regulates the inflow rate to maintain marginal stability.

We start by comparing our data to two models from (cite: krumholz18): the scenario with only gravitational instabilities as the driver of turbulence and the scenario with only stellar feedback shown in Figure [5](#fig:krumholz). Although in reality both scenarios could be present simultaneously, we choose to analyse these two cases individually to understand which one gets closer to reproduce the data. In both scenarios we use the fiducial parameters for high-*z* galaxies as reported in (cite: krumholz18) with different circular speeds that cover the range of velocities observed in our sample.

On the left panel, we explore the $\sigma$-SFR relation for the gravity driven scenario assuming that the stellar feedback does not contribute to the turbulence. On the right panel, we explore the scenario of stellar feedback driven turbulence, in which there is no mass transport in the disc and the star formation efficiency is free to vary according to physical properties of the galaxy.

Both assume that the Toomre Q parameter, which related to the local stability of the disc (cite: toomre64), is always equal to a marginally stable system.

![](figures/gravity.pdf)

Figure [5](#fig:krumholz) suggests that, for the typical range of SFR of *z*$\sim 4.5$ galaxies, the analytical model including gravitational instabilities overestimates the level of turbulence in the gas discs. Instead, the stellar feedback only model is significantly better at reproducing the data trends, predicting velocity dispersions more similar to those observed. Moreover, despite the low-number statistics, we do not find any clear gradient in the rotation velocities of the observed dataset that follows the ones expected from either models, indicating that the turbulence might not be related to the total halo mass.

### Stellar Feedback

Following up on the evidence that the stellar feedback only models perform better than the gravity only models from (cite: krumholz18), we now compare our data with the simple model described in Section [2.7](#met:snii). Here we estimate the maximum possible energy that can be injected by SNII into the ISM of the galaxies given their current SFRs and compare to the turbulent energy present in the discs estimated from the observed velocity dispersions.

![](figures/turbulence.pdf)

We show this comparison in Figure [6](#fig:expsigma), where the x-axis shows the maximum injectable energy expected from SNII calculated with Equation [\[eq:snii\]](#eq:snii) and assuming a supernova kinetic efficiency of 1. In the y-axis, we show the observed turbulent energy as calculated with Equation [\[eq:turb\]](#eq:turb) using the estimated total gas mass of each galaxy (see Table [\[tab:dy_fid\]](#tab:dy_fid)) and the observed velocity dispersion averaged across the radial extent of the disc as reported in (cite: romanoliveira23). Since we do not have reliable information about the thickness of gas discs, we analyse two different assumptions: one with a relatively thin disc ($h = 0.3$ kpc, thin ellipse) and a thick disc ($h = 1.0$ kpc, thick ellipse). Figure [6](#fig:expsigma) also has identity lines that represent the SNII efficiency $\eta$ that is usually expected to be of the order of 10%.

We find that the three of the galaxies are consistent with $\eta \approx 0.1$ while BRI1335-0417 is more consistent with a lower efficiency of $\eta \approx 0.001 - 0.01$. These are realistic values and indicate that the level of turbulence in the galaxies can be easily explained by the current SFR present in their discs, without the need of other drivers of turbulence.

We note here that we do not have a strong constrain in the gas mass of BRI1335-0417, since we had to keep the baryon fraction fixed to the cosmological fraction, effectively forcing the dark matter halo mass to its minimum realistic value.

# Discussion

In this Section, we discuss the main outcomes of the dynamical modelling of our sample, the origin of turbulence in the galaxies and a comparison of our sample with known scaling relations.

## Compact and massive stellar component

One of the main outcomes of the dynamical models described in Section [3.2](#sec:res_dy) is that the stellar component is described by a compact Sérsic profile with $n \gtrsim 5$. This indicates that a large portion of the stellar mass has to be concentrated in a compact region (\< 2 kpc) in the centre of the galaxies. This could be a compact stellar disc or, more likely, a stellar bulge. This is in line with other recent works that report dynamical signatures of bulges in $z > 4$ galaxies (cite: rizzo21; lelli21; tripodi23).

In particular, (cite: rizzo21) reported steep rises in the rotation curve similar to those found in local galaxies with significant bulge components. In (cite: lelli21) and (cite: tripodi23), there is a significant increase in the rotation velocity in the innermost resolution element that can only be reproduced in the dynamical modelling by a massive bulge component.

These are similar to the rotation curve of BRI1335-0417 shown in Figure [3](#fig:dy_rotcur) which shows an increased velocity at the innermost radius compared to the outskirts.

For BRI1335-0417 in particular, we also observe a high concentration of dust in the centre as the best-fit surface brightness profile suggests a Sérsic index of $\sim 4$. This could be related to the presence of a concentrated star formation region and perhaps a bulge still in formation.

It is also a possibility that the concentrated dust emission could be related to the fact that BRI1335-0417 is a QSO host, however we attempt to fit the surface brightness of the dust emission with a Sérsic + PSF components and we find no evidence that it provides a better fit.

As for the other galaxies in our sample, even though they do not show such a pronounced inner rise in the rotation curves, all of them require a stellar component with a Sérsic index higher than 4 to be able to reproduce the high inner circular speeds.

One may wonder whether the high rotation velocities that we observe in the inner regions could be explained by another component different from the stellar one.

However, a CDM halo cannot explain velocities of such a magnitude considering that there is essentially no leverage in the concentration parameter at $z \sim 4$ (cite: child18; correa15; dutton14).

Moreover, a central supermassive black hole of $10^9 M_{\odot}$ can only give velocities of $\sim 200$ km s$^{-1}$ in the inner $\sim 100$ pc, while we observe these velocities typically within the inner 2 kpc from the centre (see inner points of our rotation curves in Figure [3](#fig:dy_rotcur)).

The only alternative possibility would be an accumulation of gas in a phase that is completely missed by the \[CII\] emission. This seems quite unlikely especially considering that \[CII\] is expected to trace all major phases of the cold ISM. Thus we conclude that the presence of very compact stellar components in our galaxies is very likely.

The above conclusion opens questions as to the which of the pathways of bulge formation can be so efficient in forming bulges so early. There are several processes that may form bulges, e.g. mergers or gravitational instabilities in the stellar discs (cite: kormendy04; kormendy13; ishibashi14).

Another possibility is that bulges can be formed in discs with high fraction of baryonic mass with respect to the dark matter halo within the baryonic effective radius ($f_{\rm disc}$ in Table [3](#tab:dy_more)). In a recent work by (cite: blandhawthorn23), they predict that such high baryonic systems are very efficient at forming persistent bars, but also that in the presence of high gas fractions a bulge can be formed almost instantaneously in the centre of the galaxies.

Independently on the specific mechanism, our findings suggest that the process of bulge formation has to happen rapidly and in the early phases of formation of massive galaxies (cite: ferreira22a; jacobs23; kartaltepe23). In fact, the bulges in galaxies at *z* $\sim 4.5$ may indicate that these galaxies are the progenitors of massive quenched galaxies that host mature bulges at $z = 2 - 4$ (cite: valentino23; ito23; lustig21; tacchella15). Moreover, the discs we observe could also be possible progenitors of red discs recently observed with JWST at $z \sim 2 - 3$ (cite: huang23; fudamoto22; wu23; nelson23).

## Scaling relations

In this Section, we investigate how our sample of high-*z* discs are situated in Tully-Fisher-like relations and in the stellar-to-halo mass relation (SHMR).

### Tully-Fisher relations

![](figures/tullyfisher.pdf)

In Figure [7](#fig:btfr), we show the distribution of our sample with respect to the local BTFR (left panel) and the ETG analogue of the Tully Fisher relation (right panel). The latter, as mentioned in the Introduction, is derived using the rotation velocities of the inner CO discs in local ETGs. We discuss both these panels separately below.

On the left panel of Figure [7](#fig:btfr), we compare our sample to the BTFR for local disc galaxies where we show the disc galaxies from the Spitzer Photometry and Accurate Rotation Curves survey (cite: lelli16b) and the BTFR best-fit relation from (cite: lelli16). Here we show the baryonic masses of these galaxies and the circular speed estimated in the flat part of their rotation curves as obtained from kinematic models of the discs observed in HI.

For our galaxies, we plot the total baryonic mass derived from the mass decomposition of the rotation curves and the external circular speeds defined as the average of the circular speed from the outer two resolution independent elements.

We note that, like we do in the previous plots, we display BRI1335-0417 with an open symbol as we only have upper limits in the baryonic mass and therefore its placement in the BTFR is more uncertain.

We find that, for the galaxies with a more reliable baryonic mass, there is a shift from the relation towards higher velocities for a fixed mass. This trend goes in the same direction as the cosmic evolution predicted by simulations and theoretical models (cite: posti19; torrey14).

However, we highlight that this is a small sample and that these galaxies are unlikely to be the progenitors of local disc galaxies. Therefore, it is difficult to draw firm conclusions and further comparison with theoretical models is needed.

On the right panel of Figure [7](#fig:btfr), we compare our sample to local ETGs, both elliptical and lenticular galaxies, from the MASSIVE survey (cite: ma14). This subset of galaxies have small molecular gas discs extending out to 1-2 kpc that are buried within the stellar component of the host galaxy (cite: davis13a; davis11). We show the rotation derived from the velocity width of these small discs traced by the CO(J=1-0) emission, revised by (cite: davis16) and (cite: fraternali21) for better estimates of their inclinations. The total stellar masses of the local galaxies are derived from a $K-band$ luminosity assuming an ${\rm M/L} = 0.5 M_{\odot}/L_{\odot, K}$. We highlight that, unlike the disc Tully-Fisher shown in the left panel, we show the stellar mass instead of the baryonic mass here.

Moreover, we include a sample of ETGs from the ATLAS$^{\mathrm{3D}}$ survey (cite: cappellari11). This comprises lenticular, disky elliptical and boxy elliptical galaxies with available stellar kinematics, therefore also tracing mostly the inner parts of the galaxies (cite: lelli17).

We also plot the best-fit relation from (cite: davis16), which has a shallower slope than the relation for discs shown on the left panel. We see that when we look at these inner rotations, which trace the baryon dominated inner potential of the galaxies, they deviate from the Tully-Fisher relation for disc galaxies from (cite: lelli16) as, in particular at high masses, they move towards a region of fast rotation with respect to their luminous mass content, as also noted by (cite: davis16).

For our galaxies, we position them according to both their stellar mass (coloured stars in the panel) and their baryonic mass (stars + gas, squares) with the same external circular speed as shown in the left panel.

We see that our $z \sim 4.5$ galaxies tend to be shifted from the local ETG relation when comparing their stellar masses, but this shift disappears once we assume that their gas content will be fully converted into stars by $z=0$, similar to what was observed in (cite: fraternali21).

This suggests that, these $z \sim 4.5$ galaxies are largely formed in the inner regions as they have gravitational potentials similar to local ETGs and do not need to accrete more gas in order to be consistent with the local relation.

Given that it is rare to find spiral galaxies rotating at or above $\sim 300$ km s$^{-1}$ (cite: diteodoro23; ogle19; posti18), we can expect that as the gas is converted into stars, the galaxies should undergo morphological changes and become more pressure supported (cite: hilz13; naab09a; naab09b). Overall these findings give dynamical support to the scenario in which these massive $z \sim 4.5$ galaxies are likely progenitors of local ETGs (cite: fraternali21; rizzo20; toft14; barro14).

### The Stellar-to-Halo Mass Relation

The SHMR is crucial in understanding the relationship between baryonic matter and the dark matter halos of galaxies as it traces the efficiency of the conversion of baryons into stars as a function of the halo mass, providing a proxy of the efficiency of galaxy formation over cosmic time (cite: moster10; behroozi13).

Unlike the BTFR, the SHMR has been extended up to *z* $\sim 6$ with the use of abundance-matching techniques. However, to date, the SMHR has been estimated only up to $z \sim 1$ with direct dynamical estimates of CDM halo masses of individual galaxies (cite: bouche22).

Recent studies suggest that the SHMR may be dependent on the morphology of galaxies, where the relation breaks at the massive end with massive discs containing higher stellar mass fractions than elliptical galaxies (cite: correa20; marasco20; rodriguez-gomez22).

Moreover, this was supported by (cite: posti19) and (cite: diteodoro23) that showed empirically that local massive disc galaxies deviate from the relation obtained from abundance-matching techniques.

It was suggested that these massive discs must have evolved at near isolation, without going through disruptive events such as AGN feedback or major mergers.

In Figure [8](#fig:shmr), we present the SHMR in the form of the stellar-to-halo mass fraction ($M_*/M_h$) as a function of the halo mass ($M_h$). We compare this to the expected relation from abundance-matching techniques at 4.5 \< *z* \< 5.5 from (cite: shuntov22). We see that the curve is reasonably compatible with the data, with the exception of BRI1335-0417, which has only a lower limits on the CDM halo mass.

We note that, at least for this sample of *z* $\sim$ 4.5 massive disc galaxies, we do not find any significant deviation towards higher stellar fractions at the massive end.

![](figures/shmr.pdf)

# Conclusions

In this paper, we provided mass decomposition of the rotation curves of four galaxies at *z* $\sim 4.5$ using resolved kinematics traced by the \[CII\] 158 $\mu \mathrm{m}$ emission-line observed with ALMA to determine the main properties of the various matter components in galaxies in the Early Universe. We also investigated the possible origin of turbulence in the cold gas component of these galaxies to gain insights into the main contributions to the observed velocity dispersions.

Our main results are the following:

- From the rotation curve decomposition, we constrain the stellar masses (ranging between $\log(M_{\rm *}/M_{\odot}) = 10.3 - 11.0$ and gas masses (ranging between $\log(M_{\rm gas}/M_{\odot}) = 9.8 - 11.3$). We estimate the dark matter halo mass of the galaxies (ranging between $\log(M_{200}/M_{\odot}) = 11.2 - 13.3$), albeit with larger uncertainties. We found that our galaxies are strongly baryon dominated in the regions probed (inner 3 to 5 kpc) and that they have a variety of gas-to-baryon fractions, from 0.16 to 0.87.

- We investigated the origin of the turbulence in the gas discs by comparing the observed \[CII\] velocity dispersion to analytical models of turbulence driven by either gravitational instabilities or stellar feedback. We find that the observed gas turbulence in the discs can be fully reproduced by the stellar feedback alone, without the need for large-scale gravitational instabilities or other mechanisms. We established that the observed gas turbulence can be easily maintained by supernova explosions with efficiencies of only 10% or less.

- Our rotation curve decompositions indicate that there must be a massive compact stellar component dominating in the inner 2 kpc of the galaxies in our sample, compatible with what would be expected from a stellar bulge. This dynamical evidence, already suggested by other similar studies of galaxies at $z = 4 - 5$, can be validated by upcoming JWST/NIRCam observations of the stellar continuum of these galaxies.

- With the properties derived from the rotation curve decomposition, we place the galaxies in our sample into two scaling relations: the stellar-to-halo mass relation, where our data is in broad agreement with the relation obtained from abundance-matching techniques; and two versions of the Tully-Fisher relation. Compared to the local baryonic Tully-Fisher relations our galaxies show a shift towards higher rotation velocities as expected from theory. Instead in ETG- analogue of the Tully-Fisher relation our galaxies overlap with local ETGs once their gas mass is added to the stellar mass suggesting that, at least in the inner regions, they have gathered the majority of their baryonic mass already at *z* $\sim$ 4.5.

Finally, we reiterate that spatially-resolved kinematics of galaxies is a powerful tool for studying the physical mechanisms involved in galaxy formation and evolution. It is crucial to obtain constrains on the internal structure and morphology of galaxies, providing insights into the complex interactions between DM, gas, stars, and feedback processes in the ISM.

We emphasise that the detailed analysis carried out in this paper, in particular the mass decomposition of the rotation curves, requires at least 6 independent resolution elements along the major axis in any single galaxy.

ALMA is currently the only instrument that can provide high enough SNR and angular resolution to achieve these requirements. Such observations are time expensive, but critical, and in the future we should push for even higher data quality to be able to investigate the shape of the dark matter halos. We can achieve this with with JWST data, that will give us spatially resolved information for the stellar component, combined with higher sensitivity ALMA data to probe the outer regions of the rotation curve that are more dark matter dominated.

# Data Availability

The data underlying this article are public and available in the ALMA Science Archive, at <https://almascience.nrao.edu/asax/>. The processed data (i.e. the rotation curves corrected for ADC and the 0th-moment maps for the dust continuum and \[CII\] emission) along with the scripts to produce the Figures in this paper are made available at Zenodo (DOI: 10.5281/zenodo.10707348).

# Acknowledgements

We thank Vasily Kokorev and Takafumi Tsukui for the discussion on the SFR of BRI1335-0417, Marko Shuntov for the SHMR and Joss Bland-Hawthorn for the discussion on the disc fraction and the formation of bars. FRO and FF acknowledge support from The Dutch Research Council (NWO) through the Klein-1 Grant code OCEN2.KLEIN.088. FR acknowledges support from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska-Curie grant agreement No. 847523 ‘INTERACTIONS’ and the Cosmic Dawn Center that is funded by the Danish National Research Foundation under grant No. 140. The project leading to this publication has received support from ORP, that is funded by the European Union’s Horizon 2020 research and innovation programme under grant agreement No 101004719 \[ORP\]. We acknowledge extensive assistance from Allegro, the European ALMA Regional Center node in the Netherlands. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00330.S, ADS/JAO.ALMA#2017.1.00127.S, #2017.1.00394.S, #2017.1.01052.S, #2018.1.00001.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. This publication makes use of data products from the Wide-field Infrared Survey Explorer, which is a joint project of the University of California, Los Angeles, and the Jet Propulsion Laboratory/California Institute of Technology, funded by the National Aeronautics and Space Administration.

154 natexlab

(ref: aravena16) Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016, MNRAS, 457, 4406

(ref: astropycollab22) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: astropycollab18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: astropycollab13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: bacchini20) Bacchini, C., Fraternali, F., Iorio, G., et al. 2020, A&A, 641, A70

(ref: barro14) Barro, G., Faber, S. M., Pérez-González, P. G., et al. 2014, ApJ, 791, 52

(ref: behroozi13) Behroozi, P. S., Wechsler, R. H., & Conroy, C. 2013, ApJL, 762, L31

(ref: binney08) Binney, J. & Tremaine, S. 2008, Galactic Dynamics: Second Edition

(ref: blandhawthorn23) Bland-Hawthorn, J., Tepper-Garcia, T., Agertz, O., & Freeman, K. 2023, ApJ, 947, 80

(ref: bolatto13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: boogaard20) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: bouche22) Bouché, N. F., Bera, S., Krajnović, D., et al. 2022, A&A, 658, A76

(ref: bournaud07) Bournaud, F., Elmegreen, B. G., & Elmegreen, D. M. 2007, ApJ, 670, 237

(ref: cappellari11) Cappellari, M., Emsellem, E., Krajnović, D., et al. 2011, MNRAS, 413, 813

(ref: caputi17) Caputi, K. I., Deshmukh, S., Ashby, M. L. N., et al. 2017, ApJ, 849, 45

(ref: carilli&walter13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: casey14) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763

(ref: child18) Child, H. L., Habib, S., Heitmann, K., et al. 2018, ApJ, 859, 55

(ref: cfn19) Cimatti, A., Fraternali, F., & Nipoti, C. 2019, Introduction to Galaxy Formation and Evolution: From Primordial Gas to Present-Day Galaxies

(ref: cochrane19) Cochrane, R. K., Hayward, C. C., Anglés-Alcázar, D., et al. 2019, MNRAS, 488, 1779

(ref: colina23) Colina, L., Crespo Gómez, A., Álvarez-Márquez, J., et al. 2023, A&A, 673, L6

(ref: correa20) Correa, C. A. & Schaye, J. 2020, MNRAS, 499, 3578

(ref: correa15) Correa, C. A., Wyithe, J. S. B., Schaye, J., & Duffy, A. R. 2015, MNRAS, 452, 1217

(ref: costantin23) Costantin, L., Pérez-González, P. G., Guo, Y., et al. 2023, Nature, 623, 499

(ref: dacunha13) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: davis13a) Davis, T. A., Alatalo, K., Bureau, M., et al. 2013, MNRAS, 429, 534

(ref: davis11) Davis, T. A., Bureau, M., Young, L. M., et al. 2011, MNRAS, 414, 968

(ref: davis16) Davis, T. A., Greene, J., Ma, C.-P., et al. 2016, MNRAS, 455, 214

(ref: decarli16) Decarli, R., Walter, F., Aravena, M., et al. 2016, ApJ, 833, 69

(ref: dessauges20) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5

(ref: diteodoro15) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021

(ref: diteodoro16) Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016, A&A, 594, A77

(ref: diteodoro23) Di Teodoro, E. M., Posti, L., Fall, S. M., et al. 2023, MNRAS, 518, 6340

(ref: dunne22) Dunne, L., Maddox, S. J., Papadopoulos, P. P., Ivison, R. J., & Gomez, H. L. 2022, MNRAS, 517, 962

(ref: dutton14) Dutton, A. A. & Macciò, A. V. 2014, MNRAS, 441, 3359

(ref: ejdetjarn22) Ejdetjärn, T., Agertz, O., Östlin, G., Renaud, F., & Romeo, A. B. 2022, MNRAS, 514, 480

(ref: faisst20) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: ferreira22a) Ferreira, L., Adams, N., Conselice, C. J., et al. 2022, ApJL, 938, L2

(ref: ferreira22b) Ferreira, L., Conselice, C. J., Sazonova, E., et al. 2023, ApJ, 955, 94

(ref: fierlinger16) Fierlinger, K. M., Burkert, A., Ntormousi, E., et al. 2016, MNRAS, 456, 710

(ref: fraternali21) Fraternali, F., Karim, A., Magnelli, B., et al. 2021, A&A, 647, A194

(ref: fudamoto22) Fudamoto, Y., Inoue, A. K., & Sugahara, Y. 2022, ApJL, 938, L24

(ref: fudamoto17) Fudamoto, Y., Ivison, R. J., Oteo, I., et al. 2017, MNRAS, 472, 2028

(ref: genzel11) Genzel, R., Newman, S., Jones, T., et al. 2011, ApJ, 733, 101

(ref: gillman23) Gillman, S., Gullberg, B., Brammer, G., et al. 2023, A&A, 676, A26

(ref: gong20) Gong, M., Ostriker, E. C., Kim, C.-G., & Kim, J.-G. 2020, ApJ, 903, 142

(ref: governato07) Governato, F., Willman, B., Mayer, L., et al. 2007, MNRAS, 374, 1479

(ref: graham05) Graham, A. W. & Driver, S. P. 2005, PASA, 22, 118

(ref: harrison17) Harrison, C. M., Johnson, H. L., Swinbank, A. M., et al. 2017, MNRAS, 467, 1965

(ref: hilz13) Hilz, M., Naab, T., & Ostriker, J. P. 2013, MNRAS, 429, 2924

(ref: hodge12) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11

(ref: hopkins14) Hopkins, P. F., Kereš, D., Oñorbe, J., et al. 2014, MNRAS, 445, 581

(ref: huang23) Huang, S., Kawabe, R., Kohno, K., et al. 2023, ApJL, 958, L26

(ref: iorio17) Iorio, G., Fraternali, F., Nipoti, C., et al. 2017, MNRAS, 466, 4159

(ref: ishibashi14) Ishibashi, W. & Fabian, A. C. 2014, MNRAS, 441, 1474

(ref: ito23) Ito, K., Valentino, F., Brammer, G., et al. 2023, arXiv e-prints, arXiv:2307.06994

(ref: jacobs23) Jacobs, C., Glazebrook, K., Calabrò, A., et al. 2023, ApJL, 948, L13

(ref: jones16) Jones, G. C., Carilli, C. L., Momjian, E., et al. 2016, ApJ, 830, 63

(ref: jones21) Jones, G. C., Vergani, D., Romano, M., et al. 2021, MNRAS, 507, 3540

(ref: kaasinen20) Kaasinen, M., Walter, F., Novak, M., et al. 2020, ApJ, 899, 37

(ref: kamenetzky16) Kamenetzky, J., Rangwala, N., Glenn, J., Maloney, P. R., & Conley, A. 2016, ApJ, 829, 93

(ref: kartaltepe23) Kartaltepe, J. S., Rose, C., Vanderhoof, B. N., et al. 2023, ApJL, 946, L15

(ref: kohandel20) Kohandel, M., Pallottini, A., Ferrara, A., et al. 2020, MNRAS, 499, 1250

(ref: koposov22) Koposov, S., Speagle, J., Barbary, K., et al. 2022, joshspeagle/dynesty: v1.2.3, Zenodo

(ref: kormendy13) Kormendy, J. & Ho, L. C. 2013, ARA&A, 51, 511

(ref: kormendy04) Kormendy, J. & Kennicutt, Robert C., J. 2004, ARA&A, 42, 603

(ref: kretschmer22) Kretschmer, M., Dekel, A., & Teyssier, R. 2022, MNRAS, 510, 3266

(ref: krumholz16) Krumholz, M. R. & Burkhart, B. 2016, MNRAS, 458, 1671

(ref: krumholz18) Krumholz, M. R., Burkhart, B., Forbes, J. C., & Crocker, R. M. 2018, MNRAS, 477, 2716

(ref: lagache18) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130

(ref: leconte23) Le Conte, Z. A., Gadotti, D. A., Ferreira, L., et al. 2023, arXiv e-prints, arXiv:2309.10038

(ref: lelli21) Lelli, F., Di Teodoro, E. M., Fraternali, F., et al. 2021, Science, 371, 713

(ref: lelli16b) Lelli, F., McGaugh, S. S., & Schombert, J. M. 2016a, AJ, 152, 157

(ref: lelli16) Lelli, F., McGaugh, S. S., & Schombert, J. M. 2016b, ApJL, 816, L14

(ref: lelli17) Lelli, F., McGaugh, S. S., Schombert, J. M., & Pawlowski, M. S. 2017, ApJ, 836, 152

(ref: lu18) Lu, N., Cao, T., Dı́az-Santos, T., et al. 2018, ApJ, 864, 38

(ref: lustig21) Lustig, P., Strazzullo, V., D’Eugenio, C., et al. 2021, MNRAS, 501, 2659

(ref: ma14) Ma, C.-P., Greene, J. E., McConnell, N., et al. 2014, ApJ, 795, 158

(ref: maclow99) Mac Low, M.-M. 1999, ApJ, 524, 169

(ref: marasco19) Marasco, A., Fraternali, F., Heald, G., et al. 2019, A&A, 631, A50

(ref: marasco20) Marasco, A., Posti, L., Oman, K., et al. 2020, A&A, 640, A70

(ref: mcgaugh04) McGaugh, S. S. 2004, ApJ, 609, 652

(ref: mcgaugh15) McGaugh, S. S. & Schombert, J. M. 2015, ApJ, 802, 18

(ref: mcgaugh00) McGaugh, S. S., Schombert, J. M., Bothun, G. D., & de Blok, W. J. G. 2000, ApJL, 533, L99

(ref: mcmullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mo10) Mo, H., van den Bosch, F. C., & White, S. 2010, Galaxy Formation and Evolution

(ref: moster10) Moster, B. P., Somerville, R. S., Maulbetsch, C., et al. 2010, ApJ, 710, 903

(ref: naab09b) Naab, T., Johansson, P. H., & Ostriker, J. P. 2009, ApJL, 699, L178

(ref: naab09a) Naab, T. & Ostriker, J. P. 2009, ApJ, 690, 1452

(ref: narayanan11) Narayanan, D., Krumholz, M., Ostriker, E. C., & Hernquist, L. 2011, MNRAS, 418, 664

(ref: navarro97) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1997, ApJ, 490, 493

(ref: neeleman19) Neeleman, M., Kanekar, N., Prochaska, J. X., Rafelski, M. A., & Carilli, C. L. 2019, ApJL, 870, L19

(ref: neeleman20) Neeleman, M., Prochaska, J. X., Kanekar, N., & Rafelski, M. 2020, Nature, 581, 269

(ref: neeleman23) Neeleman, M., Walter, F., Decarli, R., et al. 2023, ApJ, 958, 132

(ref: nelson19) Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234

(ref: nelson23) Nelson, E. J., Suess, K. A., Bezanson, R., et al. 2023, ApJL, 948, L18

(ref: ogle19) Ogle, P. M., Lanz, L., Appleton, P. N., Helou, G., & Mazzarella, J. 2019, ApJS, 243, 14

(ref: ohlin19) Ohlin, L., Renaud, F., & Agertz, O. 2019, MNRAS, 485, 3887

(ref: ormerod24) Ormerod, K., Conselice, C. J., Adams, N. J., et al. 2024, MNRAS, 527, 6110

(ref: orr20) Orr, M. E., Hayward, C. C., Medling, A. M., et al. 2020, MNRAS, 496, 1620

(ref: oteo16) Oteo, I., Ivison, R. J., Dunne, L., et al. 2016, ApJ, 827, 34

(ref: papadopoulos18) Papadopoulos, P. P., Bisbas, T. G., & Zhang, Z.-Y. 2018, MNRAS, 478, 1716

(ref: planck20) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A1

(ref: popping22) Popping, G., Pillepich, A., Calistro Rivera, G., et al. 2022, MNRAS, 510, 3321

(ref: posti18) Posti, L., Fraternali, F., Di Teodoro, E. M., & Pezzulli, G. 2018, A&A, 612, L6

(ref: posti19) Posti, L., Marasco, A., Fraternali, F., & Famaey, B. 2019, A&A, 629, A59

(ref: renaud14) Renaud, F., Bournaud, F., Kraljic, K., & Duc, P. A. 2014, MNRAS, 442, L33

(ref: rinaldi22) Rinaldi, P., Caputi, K. I., van Mierlo, S. E., et al. 2022, ApJ, 930, 128

(ref: rizzo22) Rizzo, F., Kohandel, M., Pallottini, A., et al. 2022, A&A, 667, A5

(ref: rizzo21) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952

(ref: rizzo20) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: robertson23) Robertson, B. E., Tacchella, S., Johnson, B. D., et al. 2023, ApJL, 942, L42

(ref: rodighiero11) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40

(ref: rodney14) Rodney, S. A., Riess, A. G., Strolger, L.-G., et al. 2014, AJ, 148, 13

(ref: rodriguez-gomez22) Rodriguez-Gomez, V., Genel, S., Fall, S. M., et al. 2022, MNRAS, 512, 5978

(ref: romanoliveira23) Roman-Oliveira, F., Fraternali, F., & Rizzo, F. 2023, MNRAS, 521, 1045

(ref: rubin80) Rubin, V. C., Ford, W. K., J., & Thonnard, N. 1980, ApJ, 238, 471

(ref: schaye15) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521

(ref: scoville17) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150

(ref: sersic68) Sersic, J. L. 1968, Atlas de Galaxias Australes

(ref: shao22) Shao, Y., Wang, R., Weiss, A., et al. 2022, A&A, 668, A121

(ref: shuntov22) Shuntov, M., McCracken, H. J., Gavazzi, R., et al. 2022, A&A, 664, A61

(ref: skilling04) Skilling, J. 2004, in American Institute of Physics Conference Series, Vol. 735, Bayesian Inference and Maximum Entropy Methods in Science and Engineering: 24th International Workshop on Bayesian Inference and Maximum Entropy Methods in Science and Engineering, ed. R. Fischer, R. Preuss, & U. V. Toussaint, 395–405

(ref: skilling06) Skilling, J. 2006, Bayesian Analysis, 1, 833

(ref: smit18) Smit, R., Bouwens, R. J., Carniani, S., et al. 2018, Nature, 553, 178

(ref: speagle20) Speagle, J. S. 2020, MNRAS, 493, 3132

(ref: speagle14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: tacchella15) Tacchella, S., Carollo, C. M., Renzini, A., et al. 2015, Science, 348, 314

(ref: tacchella16) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 457, 2790

(ref: tacconi10) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781

(ref: tacconi20) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: tadaki20b) Tadaki, K.-i., Belli, S., Burkert, A., et al. 2020, ApJ, 901, 74

(ref: tadaki23) Tadaki, K.-i., Kodama, T., Koyama, Y., et al. 2023, ApJL, 957, L15

(ref: tamburro09) Tamburro, D., Rix, H. W., Leroy, A. K., et al. 2009, AJ, 137, 4424

(ref: terzic05) Terzić, B. & Graham, A. W. 2005, MNRAS, 362, 197

(ref: tiley16) Tiley, A. L., Stott, J. P., Swinbank, A. M., et al. 2016, MNRAS, 460, 103

(ref: toft14) Toft, S., Smolčić, V., Magnelli, B., et al. 2014, ApJ, 782, 68

(ref: toomre64) Toomre, A. 1964, ApJ, 139, 1217

(ref: torrey14) Torrey, P., Vogelsberger, M., Genel, S., et al. 2014, MNRAS, 438, 1985

(ref: tripodi23) Tripodi, R., Lelli, F., Feruglio, C., et al. 2023, A&A, 671, A44

(ref: tsukui21) Tsukui, T. & Iguchi, S. 2021, Science, 372, 1201

(ref: tsukui24) Tsukui, T., Wisnioski, E., Bland-Hawthorn, J., et al. 2024, MNRAS, 527, 8941

(ref: tsukui23) Tsukui, T., Wisnioski, E., Krumholz, M. R., & Battisti, A. 2023, MNRAS, 523, 4654

(ref: tullyfisher77) Tully, R. B. & Fisher, J. R. 1977, A&A, 54, 661

(ref: uebler17) Übler, H., Förster Schreiber, N. M., Genzel, R., et al. 2017, ApJ, 842, 121

(ref: valentino23) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, ApJ, 947, 20

(ref: vanalbada85) van Albada, T. S., Bahcall, J. N., Begeman, K., & Sancisi, R. 1985, ApJ, 295, 305

(ref: vogelsberger20) Vogelsberger, M., Marinacci, F., Torrey, P., & Puchwein, E. 2020, Nature Reviews Physics, 2, 42

(ref: wagg14) Wagg, J., Carilli, C. L., Aravena, M., et al. 2014, ApJ, 783, 71

(ref: wu23) Wu, Y., Cai, Z., Sun, F., et al. 2023, ApJL, 942, L1

(ref: yang17) Yang, C., Omont, A., Beelen, A., et al. 2017, A&A, 608, A144

(ref: yu21) Yu, X., Bian, F., Krumholz, M. R., et al. 2021, MNRAS, 505, 5075

# Asymmetric Drift Correction

As discussed in Section [2.6](#sec:dynmod), to obtain the circular speed from the rotation velocity it is first necessary to correct the rotation curve for the gas pressure support by applying the asymmetric drift correction. Although $^{3D}$`BAROLO` can apply this correction during the kinematic fitting, it does so without convolving the \[CII\] surface brightness with the beam. To properly account for the spatial resolution, we assume that the gas is distributed as an exponential disc and use the best-fit disc scale length reported in Table [\[tab:surfbrightness\]](#tab:surfbrightness). Therefore, we can rewrite the asymmetric drift correction from Equation [\[eq:adc\]](#eq:adc) as

$$\begin{equation}
V_{\mathrm{A}}^2 = - R \sigma^2 \frac{\partial}{\partial R} \left[\ln{(\sigma^2  \exp{(-R/R_{\mathrm{gas}}}})) \right],
\end{equation}$$

and consequently,

$$\begin{equation}
V_{\mathrm{A}}^2 = - 2 R \sigma^2 \frac{\partial \ln \sigma}{\partial R}  + \frac{R \sigma^2}{R_{\mathrm{gas}}}.
\end{equation}$$

To apply this correction to the rotation velocity, we numerically calculate the slope of $\ln{\sigma}$ at each radial element. In Figure [9](#fig:adc) we show the result of the asymmetric drift correction for BRI1335-0417, which, in spite of the difference in methodology, agrees with the circular speed derived with $^{3D}$`BAROLO`.

![](figures/adc_bri.pdf)

# Surface Brightness Models Best-Fit Posteriors

Here we show the posterior distributions of the best-fit surface brightness models for the gas and dust emission obtained as described in Section [2.3](#sec:met_sb). We fit the surface brightness at the effective radius ($I_{\mathrm{e}}$), the effective radius ($R_{\mathrm{eff}}$), the centre (x0, y0), ellipticity ($\epsilon$) and position angle (PA). For the dust emission of BRI1335-0417 we let the Sérsic index ($n$) free to vary as it is significantly different from 1.

![](figures/surf_bright_dust_fixedn.pdf)

![](figures/dynesty_surfbrightness/bri_gas_sb_corner.png)

![](figures/dynesty_surfbrightness/bri_dust_freen_sb_corner.png)

![](figures/dynesty_surfbrightness/j_gas_sb_corner.png)

![](figures/dynesty_surfbrightness/j_dust_sb_corner.png)

![](figures/dynesty_surfbrightness/sgp_system_gas_corner.png)

![](figures/dynesty_surfbrightness/sgp_system_dust_mfs_corner.png)

# Dynamical Models

## Dynamical Models Best-fit Posteriors

Here we show the posterior distributions of the best-fit dynamical models obtained as described in Section [2.6](#sec:dynmod). Our model contains five free parameters: stellar mass ($M_*$), stellar effective radius ($R_{\mathrm{eff,*}}$), stellar Sérsic index ($n$), gas mass normalisation (gas_norm) and baryon fraction ($f_{\mathrm{bar}}$), which allows us to derive the virial mass of the CDM halo. We note that for BRI1335-0417, we fix the baryon fraction to the cosmological baryon fraction, therefore we only have four free parameters. The best-fit parameters reproduce the observed rotation curves as shown in Figure [3](#fig:dy_rotcur).

![](figures/dynesty_dynamics/bri_fiducial_corner.png)

![](figures/dynesty_dynamics/j_fiducial_corner.png)

![](figures/dynesty_dynamics/sgp1_fiducial_corner.png)

![](figures/dynesty_dynamics/sgp2_fiducial_corner.png)

## Further tests

We have also performed a few more tests with different assumptions. Specifically, we test oversampling the rotation curves, both by modelling the kinematics with `3DBarolo` with more rings and by interpolation the rotation curves, and we find that neither retrieve significantly different results. This implies that, to retrieve better constrains on the parameters considered, the main limiting factor in the model is the information in the shape of the rotation curves that can only be achieved with higher resolution data and/or with more extended rotation curves (i.e. higher SNR).

Moreover, we considered models with the DM mass completely free and found that the baryon fraction becomes higher than the cosmological fraction, implying that the rotation curves of these galaxies can be reproduced without a CDM halo component, albeit likely overestimating the gas mass in order to reproduce the outer rotation.

As mentioned in the main text, while the inner part of the rotation curve is sensitive to the stellar component, in the outer parts gas and DM tend to be degenerate.

Moreover, for BRI1335-0417, as explained in Section [3.2](#sec:res_dy), we fixed the baryon fraction to the cosmological baryon fraction when modelling the rotation curve. The main drawback from undertaking the same assumptions used for the dynamical models of the other galaxies is that BRI1335-0417 has significantly lower circular speed with respect with its expected baryonic mass.

Considering the disc inclination of 42$^{\circ}$ as derived in (cite: romanoliveira23), the rotation velocity of BRI1335-0417 goes from 180 km s$^{-1}$ at 0.5 kpc to 124 km s$^{-1}$ at 4.6 kpc. After performing the asymmetric drift correction, the circular speeds become 191 km s$^{-1}$ in the centre and 153 km s$^{-1}$ in the outskirts. If we use these circular speeds to roughly estimate the total mass at each radius then we find that the innermost ring encloses a mass of $4.2 \times 10^9 M_\odot$ and the outermost ring encloses a mass of $2.5 \times 10^{10} M_\odot$.

If we take the CO luminosity observed for BRI1335-0417, presented in Table [1](#tab:colum), and consider a conservative case with the lowest CO luminosity reported in (cite: wagg14), an $\alpha_{\mathrm{CO}} = 0.8$ and a line ratio (J=2-1/J=1-0) of r$_{\mathrm{l}} = 0.5$ (cite: boogaard20; yang17; kamenetzky16; dacunha13), BRI1335-0417 should have a gas mass of $2.92 \pm 0.24 \times 10^{10} M_\odot$.

Just a simple comparison between the expected gas mass and the outer circular speed would imply that there is no room for neither the stellar component nor the CDM halo. Moreover, such a massive gas component could explain the outer rotation, however given the shape of the gas exponential disc it could never reproduce the inner circular speeds.

Therefore, for our fiducial model we considered the extreme case with the highest baryon fraction possible to derive the gas, stars and dark matter masses.

To explore whether we could potentially solve the discrepancy between the dynamical masses and the CO and stellar masses, in this Section we attempt at fitting the rotation curves with the disc inclination free and/or the NFW CDM halo concentration free. To include the inclination as a free parameter in our dynamical model we relate the circular speed $V_c$ to the disc inclination by

$$\begin{equation}
 V_c = \frac{V_{\mathrm{los}}}{\sin{(i)}},
\end{equation}$$

where, $V_{\mathrm{los}}$ is the line-of-sight rotation velocity and $i$ is the disc inclination. Therefore, if we were to consider a more face-on inclination of $i = 30^{\circ}$, the rotation of at the innermost radius would increase to 256 km s$^{-1}$ and the total mass enclosed within this radius would increase to $7.6 \times 10^{9} M_\odot$.

We perform a dynamical model keeping the inclination free to vary uniformly in the range of $20^{\circ} < i < 60^{\circ}$ while also keeping the baryon fraction and the gas normalisation free to vary in the same range as used for the other galaxies.

We find in this case that, despite potentially being able to increase the enclosed mass in the rotation curve to be modelled by decreasing the disc inclination, our dynamical model actually prefers higher inclinations ($i = 50^{\circ}$). Therefore, the resulting model is somewhat similar to the fiducial model presented in the body of this paper, with a stellar mass of $1.7 \times 10^{10} M_{\odot}$, 47% lower than the one obtained with our fiducial model.

The best-fit baryon fraction is $f_{\mathrm{bar}} = 0.12$ and gas normalisation of gas_norm = 0.04, however, both of these values concentrate at the upper and lower edge of the prior range, respectively.

This likely happens due to the flatness of the rotation curve of BRI1335-0417, since the innermost velocity is almost as high as the outskirt velocities any increase in the inner velocity translates to an even higher increase in the stellar mass. Ultimately, the main constrain is that the baryon fraction cannot exceed the cosmological baryon fraction.

Alternatively, we also test a dynamical model with a free DM concentration. In this case we keep the inclination fixed to 42 degrees, we use all the same priors for the remaining parameters and we let $c_{200}$ vary uniformly between 1 and 10. In this case, we find a stellar mass of $2.4 \times 10^{10} M_\odot$, a concentration $c_{200}$ of 2.6 while the problems with the gas normalisation and baryon fraction remain.

</paper>

Write the methods card for this paper.