# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989...66V\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989...66V",
 "title": "Modeling the Mass Distribution and Gravitational Potential of Nearby Disk Galaxies: Implications for the Interstellar Medium Dynamical Equilibrium",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Vijayakumar, Vivek",
 "n_authors": 8,
 "arxiv_id": "2506.22381",
 "doi": "10.3847/1538-4357/ade800",
 "alma_projects_linked_by_archive": [
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00392.S",
  "2017.1.00886.L",
  "2018.1.01651.S"
 ]
}
```

Paper text:
<paper>
# Modeling the Mass Distribution and Gravitational Potential of Nearby Disk Galaxies:\
Implications for the ISM Dynamical Equilibrium

## Abstract

We characterize stellar, gas, and dark matter mass distributions for 17 nearby massive disk galaxies from the PHANGS sample. This allows us to compute the gravitational potential that vertically confines the interstellar gas and determines its equilibrium scale height and weight. We first combine dynamical mass constraints from existing CO and HI rotation curves together with stellar and gas mass estimates from near-infrared, CO, and HI data. These estimates incorporate current best practices in modeling stellar mass-to-light ratios and CO-to-H$_2$ conversion factor variations. Then, we fit joint stellar–gas–dark matter mass models to the rotation curves, adopting the classic maximal disk assumption to account for remaining zero-point uncertainties on the stellar mass-to-light ratio. After obtaining three-component radial mass profiles, we calculate the vertical equilibrium gas scale height and ISM weight in the combined gravitational potential. We find the gas scale height $H_\mathrm{gas}$ increases from ${\lesssim}100$ pc in the inner disks to ${>}500$ pc at large radii, consistent with observations of our Galaxy and other edge-on galaxies. The gas weight is dominated by stellar gravity at small radii, but the gas and dark matter gravity often become important beyond 3–6 times the stellar disk radial scale length. Both our gas scale height and weight estimates are dependent on the treatment of stellar disk scale height $H_\star$, with $H_\mathrm{gas}$ varying by 30–40% when $H_\star$ varies by a factor of 3. The relationship between our refined ISM weight estimates and local star formation surface density generally agrees with previous observations and predictions from theory and simulations.

# Introduction

A galaxy’s stellar, gas, and dark matter distribution encodes its evolutionary history in cosmological contexts (cite: Kormendy_Kennicutt_2004; Conselice_2014). The gravitational potential of these components controls both stellar and gas dynamical processes (cite: vanderKruit_Freeman_2011), contributes to regulation of the star formation rate averaged over large scales (cite: 2022ApJ...936..137O; Schinnerer_Leroy_2024), and affects the gas outflow rate (cite: Thompson_Heckman_2024). Thus, the gravitational potential plays a prominent role in determining galactic evolution.

Observationally, the galaxy-wide, multi-component mass distribution can be constrained with spatially resolved imaging and kinematics, which provides estimates of baryonic mass (from stars and gas) and the total dynamical mass. This exercise has a long history starting in the early 1970s using both 21 cm and optical observations (cite: vanderKruit_Freeman_2011), leading to the hypothesis that dark matter dominates the gravitational potential in outer regions (cite: Rubin; Bosma_1981; vanAlbada_etal_1985). Since then, our understanding of mass distribution in galaxies has been greatly improved thanks to systematic surveys probing both the stellar and gaseous components, including WHISP (cite: vanderHulst_etal_2001), THINGS (cite: things; Walter2008), and DiskMass surveys (cite: Bershady_etal_2010; diskmass; Martinsson_etal_2013a).

A recurring theme in these studies is the challenge of determining an accurate stellar mass given an uncertain stellar mass-to-light ratio (M/L). This uncertainty stems from the limitations of stellar population synthesis models (cite: Bell_deJong_2001; Kauffmann_etal_2003), and it complicates the decomposition of galaxy rotation curves. Common remedies include assuming a maximum disk (cite: vanAlbada_etal_1985; maximaldisk) or invoking independent dynamical equilibrium considerations based on disk thickness and velocity dispersion (cite: vanderKruit_Freeman_1984; diskmass). With recent developments in stellar population models (cite: Sanchez_2020), it is worth revisiting this topic in the context of galaxy mass modeling.

Another important aspect of disk galaxy mass modeling is the stellar and gas distribution perpendicular to the galaxy plane. Direct constraints on the vertical scale heights of stellar and gas disks have been obtained primarily through photometric observations of edge-on galaxies (cite: vanderKruit_Searle_1981; Kregel2002; Yim_etal_2011; Yim_etal_2014; Salo_etal_2015). These studies suggested that the stellar disk scale height $H_\star$ strongly correlates with the disk’s radial exponential scale length $\ell_\star$, but remains relatively constant with radius within galaxies (cite: vanderKruit_Freeman_1984; Herrmann_etal_2008; diskmass). Intriguingly, the typical scale height to length ratio derived by these extragalactic photometric studies agrees with photometric measurements for the Milky Way (cite: Guerrette_etal_2024), but these measurements disagree with dynamical modeling results for the stellar populations in the solar neighborhood (cite: 2008ApJ...673..864J; Zhang2013; 2022MNRAS.511.3863E). This tension may be due to different measurements preferentially reflecting different disk components (e.g., photometric results may be more sensitive to the thick disk) and will hopefully be resolved by future Galactic and extragalactic studies with refined modeling methods.

The galaxy mass distributions along both the radial and vertical directions have many important implications. Among them, the dynamical equilibrium of the interstellar medium (ISM) along the vertical direction, together with its implied steady-state SFR, have been emphasized recently by both theoretical and observational studies (cite: OML2010; 2015ApJ...815...67K; Sun2020; Sun_etal_2023), especially in the context of the pressure-regulated, feedback-modulated star formation theory (cite: 2022ApJ...936..137O). In this framework, the three-dimensional gas, stellar, and dark matter distribution determines the ISM’s weight in the galaxy’s gravitational potential. This weight is balanced by the combined thermal, turbulent, and magnetic pressure (or stress) in the ISM, which requires a certain level of SFR and stellar feedback to maintain. As such, accurate mass modeling is of critical importance when applying the PRFM theory to observed galaxies, especially for obtaining SFR predictions. In particular, the gas scale height and weight depend on the vertical distribution of stars, and therefore are subject to potential uncertainty in the stellar scale height.

This work aims at modeling the stellar, gas, and dark matter distribution for a sample of nearby, massive, star-forming disk galaxies. These galaxies all have high-quality, multiwavelength coverage, in particular CO line imaging from PHANGS–ALMA (cite: Leroy2021), H I data from THINGS (cite: Walter2008) and PHANGS–VLA (cite: Chiang_etal_2024), and ancillary near-infrared imaging by *Spitzer* and *WISE* (cite: Sun2022). These datasets together provide the necessary information for reconstructing the total radial mass distribution as well as the mass distribution of gaseous components. The same galaxies also have empirical stellar M/L ratio estimates from (cite: Leroy2019), which are anchored to modern SPS-based results (cite: Salim_etal_2016), enabling construction of stellar mass profiles. The dark matter contribution can then be constrained by combining these measurements. Last but not least, having three-dimensional mass models for these galaxies can critically support many active science endeavors, especially those examining the ISM dynamical equilibrium (cite: Sun2020; Eibensteiner_etal_2024) or modeling feedback-driven gas outflows (D. Pathak et al., in preparation).

We structure this paper as follows. §[2](#sec:data) describes several key datasets and high-level data products used in our analysis. §[3](#sec:method) details our method for modeling the galaxy mass distributions, gravitational potential, and the ISM vertical equilibrium weight. §[4](#sec:results) presents the modeling results and discusses their implications in the PRFM framework. §[5](#sec:summary) summarizes all findings and provides an outlook for future work.

# Data

We use existing multiwavelength data for 17 massive star-forming disk galaxies (see [1](#table:galprops)) selected from the PHANGS–ALMA parent sample (cite: Leroy2021). These galaxies satisfy the follow criteria:

- High-quality CO, H I, and near-IR imaging data have been obtained from various sources (see references in §[1](#sec:intro)). These data have been compiled and converted into radial profiles of molecular gas, atomic gas, and stellar mass surface densities by (cite: Sun2022).

- CO and H I rotation curves are also available from either the literature (cite: rotation; DiTeodoro_Peek_2021) or our own kinematic modeling (see §[2.4](#sec:data:rotcurve)).

- For galaxies hosting stellar bars (cite: Querejeta_etal_2021), the semi-major axis of the bar should not exceed $2.2\,\ell_\star$, where $\ell_\star$ is the radial exponential scale length of the galaxy disk. This criterion is to mitigate the substantial imprint of stellar bars on gas kinematics by requiring reasonable radial coverage *outside* their footprint for robust dynamical mass modeling (see further discussion in §[4.1](#sec:result:rcmodel)).

These criteria ensure sufficient data coverage for constraining the distribution of stars, gas, and dark matter across each galaxy. We provide high-level information about the key observational measurements involved in this process in §[2.1](#sec:data:nir)–[2.4](#sec:data:rotcurve) and refer the reader to the original references for full descriptions. Visual presentations of these measurements for all galaxies can be found in [6](#apdx:gallery).

|          |         |                      |         |         |            |
|:--------:|:-------:|:--------------------:|:-------:|:-------:|:----------:|
|  Galaxy  |   $d$   | $\log_{10}\!M_\star$ |   $i$   | $\phi$  |  H I data  |
|          | \[Mpc\] |    \[$M_\odot$\]     | \[deg\] | \[deg\] |            |
| NGC 1087 |  15.9   |         9.9          |  42.9   |  359.1  | PHANGS-VLA |
| NGC 1300 |  19.0   |         10.6         |  31.8   |  278.0  | PHANGS-VLA |
| NGC 1385 |  17.2   |         10.0         |  44.0   |  181.3  | PHANGS-VLA |
| NGC 1512 |  18.8   |         10.7         |  42.5   |  261.9  | PHANGS-VLA |
| NGC 2283 |  13.7   |         9.9          |  43.7   |  355.9  | PHANGS-VLA |
| NGC 2835 |  12.2   |         10.0         |  41.3   |   1.0   | PHANGS-VLA |
| NGC 2903 |  10.0   |         10.6         |  66.8   |  203.7  |   THINGS   |
| NGC 2997 |  14.1   |         10.7         |  33.0   |  108.1  | PHANGS-VLA |
| NGC 3137 |  16.4   |         9.9          |  70.3   |  359.7  | PHANGS-VLA |
| NGC 3507 |  23.6   |         10.4         |  21.7   |  55.8   | PHANGS-VLA |
| NGC 3511 |  13.9   |         10.0         |  75.1   |  256.8  | PHANGS-VLA |
| NGC 3521 |  13.2   |         11.0         |  68.8   |  343.0  |   THINGS   |
| NGC 3621 |   7.1   |         10.1         |  65.8   |  343.8  |   THINGS   |
| NGC 4303 |  17.0   |         10.5         |  23.5   |  312.4  | PHANGS-VLA |
| NGC 4571 |  14.9   |         10.1         |  32.7   |  217.5  | PHANGS-VLA |
| NGC 4781 |  11.3   |         9.6          |  59.0   |  290.0  | PHANGS-VLA |
| NGC 5042 |  16.8   |         9.9          |  49.4   |  190.6  | PHANGS-VLA |

: Galaxy Properties

Table notes: Column descriptions: (2) galaxy distance (cite: Anand_etal_2021); (3) global stellar mass (cite: Leroy2021); (4-5) inclination and position angles (cite: rotation); (6) Source of H I data – THINGS (cite: Walter2008), PHANGS–VLA (cite: Chiang_etal_2024).

## Near-IR Data Tracing Stellar Distribution

Our analysis leverages near-IR imaging data taken by the IRAC instrument on the *Spitzer Space Telescope*, some processed and made public as part of the S$^4$G survey (cite: Sheth2010) and others from (cite: Querejeta_etal_2021). In particular, the measurements we use are based on a processed version of the IRAC 3.6 $\ensuremath{\mu}m$ images with the background subtracted and foreground stars masked (cite: Sheth2010; Querejeta_etal_2021). From there, (cite: Sun2022) created radial profiles of the 3.6 $\ensuremath{\mu}m$ surface brightness for each galaxy (with a fixed radial bin width of 500 pc) and converted them into stellar mass surface densities via $$\begin{equation}
\frac{\Sigma_\star}{M_\odot \textrm{ pc}^{-2}} = 350 \left(\frac{\Upsilon_\mathrm{3.6\mu m}}{0.5\,M_\odot\,L_\mathrm{\odot,3.6\mu m}^{-1}}\right) \left(\frac{I_\mathrm{3.6\mu m}}{\textrm{MJy sr}^{-1}}\right) \cos i~,
\label{eq:Sigma_star}
\end{equation}$$ where $I_\mathrm{3.6\mu m}$ is the 3.6 $\ensuremath{\mu}m$ surface brightness within a given radial bin, $\Upsilon_\mathrm{3.6\mu m}$ is the stellar M/L ratio at 3.6 $\ensuremath{\mu}m$ (see below), and $i$ is the inclination angle of the galactic disk (see [1](#table:galprops)). The derived stellar mass surface density, $\Sigma_\star$, is what we directly use in our analyses.

The treatment of the stellar M/L ratio is long known to be of critical importance for dynamical mass modeling (cite: vanderKruit_Freeman_2011). In this work, we start with the empirically calibrated, spatially varying $\Upsilon_\mathrm{3.6\mu m}$ values derived by (cite: Leroy2019; Leroy2021) for all our targets. These values are anchored against modern SPS models with *GALEX*, SDSS, and *WISE* data (cite: Salim_etal_2016; Salim_etal_2018). In essence, the $\Upsilon_\mathrm{3.6\mu m}$ values are derived for each radial bin based on the ratio of SFR surface density to near-IR surface brightness, which traces the local specific SFR and thus stellar population age. In this way, the varying $\Upsilon_\mathrm{3.6\mu m}$ values account for systematically varying stellar age as a function of galactocentric radius within each galaxy.

While our approach allows for a radially varying M/L ratio, it could still introduce a ${\sim}0.1$ dex (or $25\%$) error on the *global* stellar mass (cite: Leroy2019), which is still substantial for determining the stellar contribution to the total dynamical mass. We thus allow for a multiplicative factor on top of the existing $\Upsilon_\mathrm{3.6\mu m}$ estimates to account for any residual “zero point offset.” This multiplicative factor is a fixed number for each galaxy, and we describe its derivation in §[3.2](#sec:method:scaling). In this way, our M/L ratio treatment attempts to combine the advantage of SPS-based and maximum disk approaches, simultaneously accounting for radial stellar age variations within galaxies and ensuring reasonable decomposition of total dynamical mass into stellar and non-stellar (gas and dark matter) contributions.

## H I Data Tracing Atomic Gas Distribution

We make use of H I 21 cm line observations taken by the Very Large Array (VLA), as part of the THINGS (cite: Walter2008) and PHANGS–VLA surveys (cite: Chiang_etal_2024). From these data, (cite: Sun2022) derived radial profiles of the H I line integrated intensity and subsequently the atomic gas surface density via $$\begin{equation}
\frac{\Sigma_\mathrm{atom}}{M_\odot \textrm{ pc}^{-2}} = 0.020 \left(\frac{I_\mathrm{HI}}{\textrm{K km s}^{-1}}\right) \cos{i}~,
\label{eq:Sigma_atom}
\end{equation}$$ where $I_\mathrm{HI}$ is the average H I line integrated intensity in each radial bin. We use the derived atomic gas surface density ($\Sigma_\mathrm{atom}$, including the helium contribution) in our analyses.

## CO Data Tracing Molecular Gas Distribution

We also make use of $\mathrm{CO}\,(2\text{--}1)$ line data from the Atacama Large Millimeter/sub-millimeter Array (ALMA), obtained as part of the PHANGS-ALMA survey (cite: Leroy2021). These data allowed (cite: Sun2022) to derive radial profiles of the $\mathrm{CO}\,(2\text{--}1)$ line integrated intensity, $I_\mathrm{CO(2-1)}$. We then convert these $I_\mathrm{CO(2-1)}$ values into molecular gas surface densities via $$\begin{equation}
\Sigma_\mathrm{mol} = \alpha_\mathrm{CO(2-1)}\,I_\mathrm{CO(2-1)} \cos{i}~,
\label{eq:Sigma_mol}
\end{equation}$$ where $\alpha_\mathrm{CO(2-1)}$ is a varying CO(2–1)-to-H$_2$ conversion factor, derived following current best practices suggested by (cite: Schinnerer_Leroy_2024). These are based on empirically calibrated scaling relations that attempt to account for CO-dark gas, CO emissivity, and CO excitation variations within and among galaxies. The molecular gas surface density $\Sigma_\mathrm{mol}$ derived from [\[eq:Sigma_mol\]](#eq:Sigma_mol) is the measurement that enters the following analyses.

## CO and H I Kinematic Measurements

We use CO and H I rotation curves derived from the aforementioned ALMA and VLA datasets. The CO rotation curves were measured by (cite: rotation), assuming fixed position and inclination angles across each galaxy disk. These position and inclination angles are quoted in [1](#table:galprops) and were also used in (cite: Sun2022) for radial binning and deriving profiles of $\Sigma_\star$, $\Sigma_\mathrm{atom}$, and $\Sigma_\mathrm{mol}$ (§[2.1](#sec:data:nir)–[2.3](#sec:data:co)). Overall, the CO rotation curves and associated orientation parameters are fairly consistent with literature measurements for a subset of our targets (cite: Frank2016).

The H I rotation curves come from two sources. For galaxies in the THINGS sample, we use the rotation curves derived by (cite: DiTeodoro_Peek_2021) with 3D-Barolo (cite: DiTeodoro_Fraternali_2015). We have verified that these rotation curves are quantitatively consistent with those derived and presented by (cite: things) and (cite: Frank2016) based on the same THINGS data. For the other galaxies, we perform similar kinematic modeling with 3D-Barolo (version 1.7) on the PHANGS–VLA H I data cubes. Our modeling followed a standard two-step approach, with the first step devoted to determining the galaxy geometry (i.e. its center, inclination and position angles, systemic velocity) and the second step aimed to derive the kinematical parameters (the rotation velocity and the intrinsic gas velocity dispersion). The inclination and position angles are allowed to vary as a function of galactocentric radius, which is appropriate for extended H I disks which often warp at large radii. For further technical details on the modeling procedure, we refer to (cite: DiTeodoro+2023).

Beside rotation curves, we also use measurements of CO and H I velocity dispersion for the purpose of modeling the vertical thickness of the gas disks (§[3.4](#sec:method:height)). The CO velocity dispersion is measured at fixed 150 pc scales (cite: Sun2018; Sun2020a) and then averaged over each radial bin in a CO intensity-weighted fashion (cite: Sun2022). A moderate inclination correction is also applied to the CO velocity dispersion following (cite: Sun2022). The H I velocity dispersion per radial bin is provided by 3D-BAROLO as an output parameter.

# Methodology

Based on the observational data described in §[2](#sec:data), we model the mass distributions of stars, gas, and dark matter, and from these we derive their combined gravitational potential, the weight of the ISM in this potential, and the thickness of the ISM disk (assuming vertical dynamical equilibrium), for each of our target galaxies. To achieve these goals, we first model the radial mass profiles of the stars and gas in each galaxy with the azimuthally-averaged surface density profiles from (cite: Sun2022). We then determine the dark matter radial distribution by calculating the stellar and gas gravitational potentials and subtracting their contributions from the rotation curves. To obtain a smooth dark matter potential, we assume the dark matter halos follow a spherically symmetric, Navarro-Frenk-White profile (cite: NFW). After obtaining the radial mass profiles for stars, gas, and dark matter, we compute the equilibrium weight of the gas within the combined gravitational potential as well as the equilibrium vertical scale height of the gas disk. We explore different assumptions regarding the vertical scale height of the stellar disk, and the impacts of this choice on the modeling results.

## Stellar and Gas Disk Potentials

To prepare for gravitational potential calculations for the stellar and gas components, we first create smooth models of their radial mass profiles from the observed, discrete, bin-averaged radial profiles (§[2.1](#sec:data:nir)–[2.3](#sec:data:co)).

The observed stellar and gas mass surface density profiles show obvious fluctuations between adjacent radial bins. This is not unexpected given measurement uncertainties and the true inhomogeneity in the distributions, but it can cause issues in the subsequent calculations of gravitational potential and circular velocity (as they involve numerical integrals and derivatives). To mitigate these issues, we perform a Gaussian process regression to damp out small-scale fluctuations in the surface density profiles (see [2](#fig:starprofiles)). This effective “smoothing” is achieved by adopting a radial basis function kernel with a relatively large length scale to ensure covariance over that scale. We test different length scales on our data and visually inspect the outcomes, finding that the optimal length scales for the stellar and gas profiles are 3 kpc and 1.5 kpc, respectively.

For a subset of galaxies, the radial coverage of their stellar surface density profiles are more limited than their H I rotation curves. This is primarily due to an outer radius threshold imposed by (cite: Sun2022) when creating the surface density profiles. Considering that these galaxies are well described by exponential profiles near the outskirts, we fit exponential models to their outer parts and extrapolate them to match the corresponding H I rotation curve coverage. This allows us to fully utilize the H I kinematic information at large radii, which is especially important for constraining the dark matter halo profiles (also see [3.3](#sec:method:rcfit)).

From the interpolated and smoothed surface density profiles for the stars and gas, we compute their gravitational potentials and corresponding contributions to the galaxy rotation curve. For the stellar disk, we follow (cite: Bovy) to derive the potential near the galaxy midplane as a function of radius, assuming an exponential vertical distribution with a constant vertical scale height $H_\star$, $$\begin{align}
\Phi(R, z{=}0) &= -\frac{2\pi G}{H_\star}\!\int_{0}^{\infty}\!dk \frac{H_\star}{1+kH_\star} \ J_0(kR) \ S_0(k)\\
\text{where } &S_0(k) = \int_{0}^{\infty}\!dR'\ J_0(kR') \ R'  \ \Sigma(R') ~.
\label{eq:thickpotential}
\end{align}$$ We further discuss choices of the stellar disk vertical scale height $H_\star$ and their rationale in [3.4](#sec:method:height).

For the gas disk, we assume a geometrically thin disk and follow (cite: 2008gady.book.....B) to derive the potential, $$\begin{equation}
\Phi(R, z{=}0) = -4G\!\int_{0}^{\infty}\!dR'\frac{R'\Sigma(R')}{R+R'}K\!\left(\frac{2\sqrt{RR'}}{R+R'}\right)~,
\label{eq:thinpotential}
\end{equation}$$ where $K$ represents the complete elliptic integral of the first kind.

We derive the potentials for each component, $\Phi_\star(R)$ and $\Phi_\mathrm{gas}(R)$, by numerically integrating [\[eq:thickpotential\]](#eq:thickpotential) and [\[eq:thinpotential\]](#eq:thinpotential) using the corresponding surface density functions, $\Sigma_\star(R)$ and $\Sigma_\mathrm{gas}(R)$, respectively. From the potentials we can derive the circular velocity contributed by each mass component via $$\begin{align}
    V^2_\star(R) &= R \frac{d\Phi_\star}{dR}~, \label{eq:vcirc_star}\\
    V^2_\mathrm{gas}(R) &= R \frac{d\Phi_\mathrm{gas}}{dR}~. \label{eq:vcirc_gas}
\end{align}$$

## Rescaling of the H I Rotation Curves and the Stellar Potential

When comparing the CO and H I rotation curves (§[2.4](#sec:data:rotcurve)) and the derived $V_\star(R)$ profiles (from [\[eq:vcirc_star\]](#eq:vcirc_star)), we notice two issues. The first issue is that the CO and H I rotation curves do not always agree within the radius range where both are available. This may be caused by the different spatial and velocity resolutions of the CO and H I data and the sometimes inconsistent inclination angles derived from them. To address this, we scale the entire H I rotation curve by a multiplicative factor $f_\mathrm{HI}$: $$\begin{equation}
V_\mathrm{\mathrm{HI},scaled}(R) = f_\mathrm{HI} V_\mathrm{HI}(R)~,
\label{eq:HIscaling}
\end{equation}$$ such that it matches the CO rotation velocity in the outer part of the CO radial coverage to ensure continuity. Here we use the CO-based results as our “anchoring points” for internal consistency, as the surface density and velocity dispersion measurements from (cite: Sun2022) were all derived assuming the CO-based inclination angles. The resulting correction is small for most galaxies, typically $|1-f_\mathrm{HI}|\,{\lesssim}\,10\%$ (see §[4.1](#sec:result:rcmodel)). After that, we merge the CO rotation curve with the scaled H I curve at larger radii to form a combined rotation curve, $V_\mathrm{c}(R)$, to be used in further analyses[^1].

The second (perhaps more important) issue is that the $V_\star(R)$ profile derived directly from [\[eq:vcirc_star\]](#eq:vcirc_star) appears inconsistent with the measured $V_\mathrm{c}(R)$ in many cases. That is, we expect stellar gravity be dominant in the inner parts of massive disk galaxies, so that $V_\star(R)$ should be smaller than but very close to $V_\mathrm{c}(R)$. However, we find $V_\star(R)$ to be much lower than $V_\mathrm{c}(R)$ in some cases (such that stellar contribution become very subdominant) and to exceed $V_\mathrm{c}(R)$ in a few other cases (which is unphysical). This likely reflects uncertainties from various sources, including the stellar M/L ratio (see §[2.1](#sec:data:nir)), galaxy distance (which affects the overall normalization of the stellar contribution), and galaxy inclination angle (which affects the normalization of the rotation curve). To address this issue, we re-scale the stellar contribution to the circular velocity with a multiplicative factor, $f_\star$.

$$\begin{equation}
V_\mathrm{\star,scaled}(R) = f_\star V_\star(R)
\label{eq:stellarscaling}
\end{equation}$$

The value of $f_\star$ is determined for each galaxy from the classic maximum disk assumption (cite: maximaldisk), such that $$\begin{equation}
\sqrt{V^2_\mathrm{\star,scaled} + V^2_\mathrm{gas}} = 0.85 \times V_\mathrm{c}\quad \mathrm{at} \quad R=2.2\ell_\star~.
\label{eq:maximumdisk}
\end{equation}$$ Here $\ell_\star$ is the radial exponential scale length of the stellar disk, which we measure for each galaxy by fitting an exponential function to the $\Sigma_\star$ profile within the disk-dominated radius range, where the range is determined by outlier rejection (see [2](#fig:starprofiles), and [2](#table:scalingpars) for the measured $\ell_\star$ values). [\[eq:maximumdisk\]](#eq:maximumdisk) uses $2.2 \times \ell_\star$ as the “anchoring radius” because it is where $V_\star(R)$ would reach its maximum for a pure exponential disk. The choice to normalize the total baryonic contribution to 0.85 times the dynamical mass implied by the circular velocity is empirically determined in previous studies (cite: maximaldisk).

## Rotation Curve Fitting

After merging the CO and H I rotation curves and scaling $V_\star(R)$ according to the maximum disk assumption, we fit a combined stellar–gas–dark matter model to the rotation curve: $$\begin{equation}
V_\mathrm{c}^2(R) = V_\mathrm{\star,scaled}^2(R) + V_\mathrm{gas}^2(R) + V_\mathrm{DM}^2(R)~.
\label{eq:rcmodel}
\end{equation}$$ In this model, the stellar and gas components do not have free parameters as they are given by gravitational potential calculations (§[3.1](#sec:method:potential)), with the stellar component rescaled according to the maximum disk assumption (§[3.2](#sec:method:scaling)). The dark matter component is parametrized according to the cumulative version of the NFW profile (cite: NFW), $$\begin{align}
V_\mathrm{DM}^2(r)
&= \frac{GM_\mathrm{DM}({<}r)}{r} \nonumber\\
&= \frac{4\pi G\rho_0 R_s^3}{r}\left[\ln\!\left(1+\frac{r}{R_s}\right) - \frac{r/R_s}{1+r/R_s}\right]~.
\label{eq:NFW_vsquared}
\end{align}$$ Here $R_s$ is the dark matter halo scale radius and $\rho_0$ is the normalization factor. With the best-fit $\rho_0$ and $R_s$, the dark matter density profile can be expressed as $$\begin{equation}
\rho_\mathrm{DM}(r) = \frac{\rho_0}{\frac{r}{R_s}\left(1+\frac{r}{R_s}\right)^2}~.
\label{eq:NFW_rho}
\end{equation}$$

In some of our galaxies, we do not have sufficient coverage at larger radii (where the dark matter dominates the potential) to separately constrain $R_s$ and $\rho_0$. To remedy this, we compare the fitting results between a two-parameter model with varying $R_s$ and a one-parameter model with a fixed fiducial $R_s = 9H_\star$ (cite: Somerville2025). We use the Bayesian information criterion (BIC) to determine which model best fits the rotation curve of each galaxy.

## Disk Scale Height

To convert the 2D, in-plane stellar and gas surface density profiles into full 3D mass distributions, we also need the vertical scale heights of the stellar and gas disks. For the gas disk, we compute its scale height $H_\mathrm{gas}$ from the vertical dynamical equilibrium condition, which relates $H_\mathrm{gas}$ to the gas effective velocity dispersion $\sigma_\mathrm{eff}$ and the galaxy gravitational potential. In practice, this requires solving a cubic equation (cite: Hassan_etal_2024): $$\begin{align}
H_\mathrm{gas}^3 &\left(  \frac{2\zeta\Omega_\mathrm{DM}^2  }{\pi G \Sigma_\mathrm{gas}} \right) +
H_\mathrm{gas}^2 \left(1 + \frac{2\Sigma_\star}{\Sigma_\mathrm{gas}} + \frac{2\zeta\Omega_\mathrm{DM}^2  H_\star}{\pi G \Sigma_\mathrm{gas}} \right)\nonumber\\  
&+ H_\mathrm{gas} \left(H_\star - \frac{\sigma_{\rm eff}^2 }{\pi G\Sigma_\mathrm{gas}} \right) - H_\star \frac{\sigma_{\rm eff}^2 }{\pi G\Sigma_\mathrm{gas}}=0.
\label{eq:Hg_cubic}
\end{align}$$ Here, $\zeta \approx 1/3$ is a geometric factor that is insensitive to the exact vertical distribution of the gas density (cite: Ostriker+Shetty); $\Omega_\mathrm{DM}=V_\mathrm{DM}/R$ quantifies the dark matter gravity; $H_\star$ is the vertical scale height[^2] of the stellar disk (see below); and $\sigma_\mathrm{eff}$ represents the effective gas velocity dispersion. [\[eq:Hg_cubic\]](#eq:Hg_cubic) is exact if the gas disk and stellar disk both have exponential profiles along the vertical direction, and is correct within $\sim 25\%$ more generally (cite: Hassan_etal_2024).

For the effective gas velocity dispersion $\sigma_\mathrm{eff}$, we use the mass-weighted average of the molecular and atomic gas velocity dispersion[^3] (see §[2.4](#sec:data:rotcurve)) following (cite: Sun2020). Similar to our treatments for the stellar and gas surface density profiles in [3.1](#sec:method:potential), we perform a Gaussian process regression also on the $\sigma_\mathrm{eff}$ profiles to suppress small-scale fluctuations.

For the stellar disk scale height $H_\star$, we consider five different assumptions both for calculating the stellar disk potential in [3.1](#sec:method:potential) and for deriving the gas scale height here:

1.  The conventional estimate of $H_\star = 0.27\,\ell_\star$, where $\ell_\star$ is the radial scale length of the stellar surface density profile (cite: Kregel2002; Sun2020)

2.  A rescaled version of the above, $H_\star = 0.09\,\ell_\star$, based on the ratio of the Milky Way’s stellar disk scale length (cite: Bovy_Rix_2013) and scale height (cite: Zhang2013).

3.  An assumption that $H_\star=H_\mathrm{gas}$. The purpose of considering this assumption is to test how much the results differ from those in other cases when a specific value of $H_\star$ is adopted. This is particularly relevant to situations where $H_\star$ is uncertain (e.g. in cosmological simulations where the vertical structure of the disk is not resolved). If one assumes a constant $H_\star/H_g$ ratio, [\[eq:Hg_cubic\]](#eq:Hg_cubic) reduces to a quadratic form with a single unknown variable (cite: Hassan_etal_2024), from which $H_\star$ or $H_g$ can be directly solved. Here we assume $H_\star=H_g$, which would be appropriate for early stages of galactic evolution prior to secular thickening of the stellar disk, and is also not too far from observations of the Milky Way solar neighborhood.

4.  A constant value of $H_\star = 800$ pc. This value is motivated by the $H_\star = 0.27\,\ell_\star$ relation mentioned above and the observation that the galaxy scale radii in our sample are clustered around $\sim$3 kpc. This simple assumption is easy to implement and may be appropriate for local massive galaxy disks in dynamical equilibrium.

5.  An alternative constant value, $H_\star = 300$ pc. The motivation is similar to the assumption above, but instead based on the $H_\star = 0.09\,\ell_\star$ scaling.

## Gas Equilibrium Weight

With the aforementioned treatments of the stellar and gas disk vertical scale heights, we now have the full 3D information for the stellar, gas, and dark matter distribution. This allows us to compute the total weight of the gas (per unit area) in the combined galaxy potential, which should be balanced by the average gas pressure near the disk midplane under the assumption of vertical dynamical equilibrium. This total weight is equal to the sum of the weight contributed by the gravity of the gas disk, stellar disk, and dark matter halo, as given by (cite: Hassan_etal_2024), $$\begin{align}
\mathcal{W}_\mathrm{gas} &= \frac{\pi}{2}G\Sigma_\mathrm{gas}^2~,
\label{eq:Wgas}\\
\mathcal{W}_\star &= \pi G\Sigma_\mathrm{gas} \Sigma_\star \frac{H_\mathrm{gas}}{H_\mathrm{gas} + H_\star}~,
\label{eq:Wstar}\\
\mathcal{W}_\mathrm{DM} &= 
\zeta \Sigma_\mathrm{gas} \Omega_\mathrm{DM}^2 H_\mathrm{gas},
\label{eq:Wdm}
\end{align}$$ where $H_\mathrm{gas}$ is the solution of [\[eq:Hg_cubic\]](#eq:Hg_cubic). The total weight of the gas per unit area is the sum of these terms, $$\begin{equation}
\mathcal{W} = \mathcal{W}_\mathrm{gas} + \mathcal{W}_\star + \mathcal{W}_\mathrm{DM}~.
\label{eq:Wtot}
\end{equation}$$

In the limit of $H_\mathrm{gas} \ll H_\star$ and negligible dark matter contribution, we obtain a result very similar to the expression $$\begin{align}
\mathcal{W} &=\frac{\pi G \Sigma_\mathrm{gas}^2}{2} + \Sigma_\mathrm{gas} (2 G \rho_\star)^{1/2}\sigma_\mathrm{eff}
\label{eq:Wtot_lim}
\end{align}$$ that is commonly adopted in the nearby galaxy observational literature (cite: 2004ApJ...612L..29B; 2017ApJ...835..201H; Sun2020; Sun_etal_2023; 2021MNRAS.503.3643B), with the only difference being a factor $\pi$ instead of $2$ in the square root. For galaxy models with similar properties to normal spirals, [\[eq:Wtot_lim\]](#eq:Wtot_lim) has also been validated in numerical hydrodynamic and magnetohydrodynamic simulations (cite: 2011ApJ...743...25K; 2013ApJ...776....1K; 2015ApJ...815...67K; 2022ApJ...936..137O; 2024ApJ...972...67K).

# Results

## Rotation Curve Decomposition

A key part of this work is decomposing the observed galaxy rotation curves into stellar, gas, and dark matter contributions for mass modeling. We highlight the main results and caveats in [3](#fig:vsquared). Specifically, the left panels show the original CO and H I rotation curves derived from kinematic modeling as well as the stellar and gas circular velocity contributions computed without any rescaling (§[3.2](#sec:method:scaling)). The three galaxies shown in [3](#fig:vsquared) reflect the diversity of situations we see across the whole sample – that is, for some galaxies the amplitudes of the rotation curves and the stellar component are consistent with each other as they are; but for the remaining majority, the CO and H I rotation curves show small relative offsets in the overlapping radius range, and the stellar component either exceeds the rotation curves or appears much smaller than expected for these massive disk galaxies. These issues motivate us to rescale the H I rotation curve relative to CO and the stellar contribution relative to the combined rotation curve (as described in §[3.2](#sec:method:scaling)), such that we can achieve reasonable rotation curve decomposition results for mass modeling.

+--------------------+--------------+-----------------+------------------------+---------+---------------------------------------------------------+
| Galaxy             | $\ell_\star$ | $f_\mathrm{HI}$ | $\log_{10}\rho_0$      | $R_s$   | $f_\star$                                               |
+:===================+:============:+:===============:+:======================:+:=======:+:==========================:+:==========================:+
| 6-7                | \[kpc\]      |                 | \[$\rm M_\odot/pc^3$\] | \[kpc\] | $H_\star = 0.27\ell_\star$ | $H_\star = 0.09\ell_\star$ |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 1087           | 1.54         | 1.10            | -2.2                   | 14      | 1.71                       | 1.55                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 1300           | 3.73         | 1.19            | -2.6                   | 34      | 1.94                       | 1.70                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 1385$^\dagger$ | 1.97         | 1.08            | -2.7                   | 18      | 1.10                       | 1.00                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 1512           | 6.18         | 1.12            | -3.1                   | 56      | 1.07                       | 0.99                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 2283           | 2.19         | 1.05            | -2.7                   | 20      | 1.83                       | 1.67                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 2835           | 2.53         | 1.08            | -2.8                   | 23      | 1.97                       | 1.79                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 2903           | 3.38         | 1.01            | -2.6                   | 30      | 1.09                       | 0.98                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 2997           | 4.25         | 1.08            | -2.5                   | 38      | 1.68                       | 1.48                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 3137           | 3.15         | 1.02            | -2.8                   | 28      | 2.46                       | 2.21                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 3507           | 2.17         | 1.19            | -2.3                   | 20      | 0.67                       | 0.60                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 3511           | 2.49         | 1.03            | -2.5                   | 22      | 1.25                       | 1.14                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 3521           | 5.02         | 1.01            | -2.5                   | 23      | 0.80                       | 0.74                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 3621           | 1.95         | 1.02            | -2.3                   | 18      | 0.99                       | 0.90                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 4303           | 2.77         | 1.09            | -2.4                   | 25      | 0.95                       | 0.86                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 4571$^\dagger$ | 2.14         | 0.94            | -2.6                   | 19      | 1.61                       | 1.46                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 4781           | 0.97         | 1.06            | -1.9                   | 8.7     | 1.15                       | 1.05                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+
| NGC 5042           | 2.13         | 1.10            | -2.4                   | 19      | 1.51                       | 1.37                       |
+--------------------+--------------+-----------------+------------------------+---------+----------------------------+----------------------------+

: Derived Parameters

Table notes: Column descriptions: (2) stellar disk radial scale length measured from the $\Sigma_\star$ radial profile; (3) multiplicative factor applied to $V_\mathrm{HI}$ to match $V_\mathrm{CO}$ ([\[eq:HIscaling\]](#eq:HIscaling)); (4) & (5) the dark matter NFW profile normalization factor $\rho_0$ and scale radius $R_s$; (6) & (7) scaling factor applied to $\Sigma_\star$ to satisfy the maximal disk criterion ([\[eq:stellarscaling\]](#eq:stellarscaling)), assuming either $H_\star = 0.27\ell_\star$ or $H_\star = 0.09\ell_\star$. $^{\dagger}$ For these two galaxies the observational data have very limited radial coverage (only out to $\approx3.5\,\ell_\star$). Their dark matter NFW profile fit results should be taken with caution.

We report in [2](#table:scalingpars) the scaling factors applied to the H I rotation curves using [\[eq:HIscaling\]](#eq:HIscaling) ($f_\mathrm{HI}$) and the stellar components using [\[eq:stellarscaling\]](#eq:stellarscaling) ($f_\star$). The $f_\mathrm{HI}$ values for most galaxies are in the range of $0.94{-}1.19$, reflecting the small relative offset (${\lesssim}19\%$) between the CO and H I rotation curves. The fact that most $f_\mathrm{HI}$ values are above 1 indicates that the estimated H I rotation velocity tends to be smaller than CO rotation velocity at the same radius. This is in part due to systematic differences in the inclination angles derived from H I and CO kinematic modeling, such that the estimated inclination is often higher for H I, resulting in a lower circular rotation velocity than CO. Another possibility is that the H I circular velocity is indeed smaller than CO on average as the H I gas disk is often thicker, so most of the H I gas is located farther away from the galaxy mid-plane. This effect has been reported by previous studied when comparing the centroid of H I and CO line profiles in nearby galaxies (cite: Koch_etal_2018), but the amplitude of this effect in literature studies tends to be smaller than the offsets that we find here.

The scaling factor applied to the stellar mass and potential, $f_\star$, tends to be more substantial than $f_\mathrm{HI}$. As mentioned in §[3.2](#sec:method:scaling), this likely reflects a much larger uncertainty on the stellar M/L ratio, although uncertainties on the galaxy distance and inclination angle can also play some role. [4](#fig:scaling) shows the distribution of $f_\star$ across our sample. Assuming $H_\star = 0.27\ell_\star$, 13 out of 17 galaxies have $f_\star$ values between $0.8{-}1.5$ (or $-0.10$ to $0.15$ dex), comparable to the expected level of uncertainty for our stellar M/L ratio treatment (cite: Leroy2019). The remaining four galaxies have $f_\star$ values of $1.6{-}2.1$, i.e., the whole stellar mass profile and potential needs to be scaled up by the square of that factor to satisfy the maximum disk assumption. Adopting $H_\star = 0.09\ell_\star$ yields mildly different $f_\star$ values, but the qualitative behaviors and the fraction of “outlier” galaxies remain similar.

We note that our analyses cannot conclusively confirm or rule out the maximal disk scenario. It is possible that galaxies with large $f_\star$ values actually have sub-maximal disks, though one of them (NGC 1300) is among the most massive galaxies in our sample ($10^{10.6}\,M_\odot$) and is expected to be stellar gravity dominated at least within the inner disk. On the other hand, if we assume a maximal disk and attribute the $f_\star$ scaling entirely to uncertain M/L ratio estimates, then they would imply a modified M/L ratio with a median value and 1$\sigma$ range of $0.47\pm0.14\;M_\odot\,L_\mathrm{\odot,3.6\mu m}^{-1}$ across our sample, which also seem quite plausible. In any case, the maximal disk (or submaximal disk) scenario simply dictates some modified M/L ratio in this work, and we have verified that adopting any reasonable alternative M/L ratio (e.g., between 0.2 and 0.6) would not change our main results on a qualitative level.

After rescaling the H I rotation curve and stellar potential, we perform the joint stellar–gas–dark matter fit on the rotation curve and illustrate the results in the right panels in [3](#fig:vsquared). Note that the fit ignores all measurements in the radius range covered by a stellar bar or a central stellar structure (shaded area), where we expect, and indeed often see, strong non-circular motions affecting the rotation curve measurements and non-axisymmetric structures distorting the stellar potential.

We find the combination of the rescaled stellar component, the gas component, and the NFW dark matter component can fit the joint CO-H I rotation curve very well, especially outside the bar and/or center region. The rescaled stellar component always dominates at small radii, which is partly by construction with the maximum disk assumption, but also does align with our expectation for massive disk galaxies at $z\sim0$. The dark matter component often surpasses the stellar component at the largest radius probed by the H I data, except for very few galaxies where the H I rotation curves are too limited in their radius coverage (i.e., only out to $4{-}5\;\ell_\star$) to reach the dark matter-dominant region. For all galaxies, the gas gravity has a negligible contribution to the circular velocity at all radii, as one would expect given their small contribution to the overall mass budget in these systems.

## Disk Scale Heights

Based on the stellar, gas, and dark matter mass profiles obtained via rotation curve decomposition, we derive the equilibrium gas disk scale height ($H_\mathrm{gas}$) from [\[eq:Hg_cubic\]](#eq:Hg_cubic) at all galactocentric radii and show the results in [5](#fig:scaleheights) and [6](#fig:allgasscaleheights). As discussed in §[3.4](#sec:method:height), the $H_\mathrm{gas}$ calculation is dependent on and sensitive to the assumption for the stellar disk scale height $H_\star$. We thus compare the results under three different assumptions, namely $H_\star=0.27\ell_\star$ (cite: Kregel2002; Sun2020), $H_\star=0.09\ell_\star$ (cite: Zhang2013), and $H_\star=H_\mathrm{gas}$ (to test how accurate an $H_\mathrm{gas}$ could be obtained if $H_\star$ is unknown).

[5](#fig:scaleheights) shows the derived gas scale height $H_\mathrm{gas}$ as a function of galactocentric radius in two galaxies: NGC 4571 and NGC 4781. A general trend is that $H_\mathrm{gas}$ increases strongly with radius, from ${\lesssim}100$ pc in the inner disk to ${>}500$ pc in the outer disk. Considering that $H_\mathrm{gas}$ mostly reflects the scale height of the mass-dominating ISM phase at each radius, this trend is consistent with measurements for the Milky Way and other edge-on galaxies (cite: Yim_etal_2011; Yim_etal_2014; Heyer_Dame_2015; McClure-Griffiths_etal_2023). On top of this overall trend are small-scale fluctuations that can be traced back to residual bin-to-bin variations in stellar surface density and gas velocity dispersion.

The derived $H_\mathrm{gas}$ values directly depend on the assumption for $H_\star$. Adopting a larger fixed $H_\star$ value (i.e., $H_\star=0.27\ell_\star$ rather than $0.09\ell_\star$) would lead to larger $H_\mathrm{gas}$ values at any given radius, as one would expect from the reduced “confining force” by stellar gravity near the disk mid-plane. This also affects the radius at which the gas scale height exceeds the stellar scale height – in this example, for NGC 4781, $H_\mathrm{gas}$ exceeds $H_\star$ at $r\approx4$ kpc when assuming $H_\star=0.27\ell_\star$ (blue dashed line), but it happens at $r\approx2$ kpc when assuming $H_\star=0.09\ell_\star$ (red dashed line). The assumption $H_\star=H_\mathrm{gas}$ leads to a solution consistent with the solution obtained for smaller $H_\star$ at small $R$, and larger $H_\star$ at large $R$.

[6](#fig:allgasscaleheights) summarizes our gas scale height measurements across the entire sample. The left panel shows all the $H_\mathrm{gas}$ radial profiles assuming $H_\star = 0.27\ell_\star$, with the $x$-axis normalized by the stellar disk radial scale length of each galaxy. Aside from the general trend of increasing $H_\mathrm{gas}$ with radius, the $H_\mathrm{gas}$ profiles show some variety as each galaxy has its unique radial profiles of $\Sigma_\star$, $\Sigma_\mathrm{gas}$, and $\sigma_\mathrm{eff}$. Most galaxies have $H_\mathrm{gas}$ in the range of 100–500 pc over several disk scale lengths. For a comparison, in the Milky Way solar neighborhood, the scale heights of the mass-dominating cold and warm neutral media are $160$ pc and $230$ pc, respectively (cite: McClure-Griffiths_etal_2023). With the Sun located at $R=8.3\;\mathrm{kpc}$ (cite: Bovy_Rix_2013) in the Milky Way, the local gas disk scale heights appear normal among nearby star-forming disk galaxies studied in this work. Our results also seem to agree with previous extragalactic studies (cite: Yim_etal_2011; Yim_etal_2014; Bacchini_etal_2019; ManceraPina_etal_2022) in both the gas scale height range and the quantitative trends.

The right panel in [6](#fig:allgasscaleheights) shows the fractional changes in the gas scale heights derived from the alternative stellar scale height assumptions ($H_\star=0.09\ell_\star$ and $H_\star = H_\mathrm{gas}$) relative to $H_\star=0.27\ell_\star$. Overall, assuming $H_\star=0.09\ell_\star$ leads to ${\sim}0.15$ dex (or $30{-}40\%$) smaller gas scale heights than $H_\star=0.27\ell_\star$ in the inner disk ($R \lesssim \ell_\star$), with the discrepancy reducing to ${\lesssim}0.05$ dex (or ${\lesssim}\,10\%$) towards the outer disk ($R \gtrsim 5\ell_\star$). This radial trend is expected because (a) stellar gravity is most important at small radii (also see §[4.3](#sec:result:weight) below), and (b) the gas disk is much thinner than the stellar disk there ([5](#fig:scaleheights)). Under these conditions, the stellar volume density near the disk mid-plane ($\rho_\star$) is most important for setting the gas equilibrium scale height. Since $\rho_\star$ is directly set by $H_\star$ via $\rho_\star = \Sigma_\star/2H_\star$, it is not surprising the $H_\star$ assumption matters the most for setting $H_\mathrm{gas}$ in the inner disk. Then as the gas scale height approaches and even exceeds the stellar scale height towards larger radii, the $H_\star$ assumption matters less, hence the trend seen in the right panel of [6](#fig:allgasscaleheights). The same arguments hold for the $H_\star = H_\mathrm{gas}$ case as well, except that we see much larger discrepancies with $H_\star=0.27\ell_\star$ there, up to $0.5{-}1.0$ dex in the inner disk.

## Gas Equilibrium Weight

Combining the mass profiles and gas equilibrium scale heights derived in §[4.1](#sec:result:rcmodel)–[4.2](#sec:result:height), we compute the weight of the gas (along the vertical direction) in the combined galaxy potential via [\[eq:Wgas\]](#eq:Wgas)–[\[eq:Wtot\]](#eq:Wtot) and showcase the results for one galaxy (NGC 2903) in [7](#fig:weight). The total gas weight and all of its components generally decreases with galactocentric radius, as both the gas surface density drops and the vertical gravitational field decreases towards the outer galaxy. Among all the weight components (as defined by Equations [\[eq:Wgas\]](#eq:Wgas)–[\[eq:Wdm\]](#eq:Wdm)), the component associated with stellar gravity often dominates over a wide radius range across the inner galaxy, and in a few cases over the entire radius range probed by the CO and H I data (out to $4{-}5\;\ell_\star$ in those cases). However, the gas and dark matter components can become more important at large radii: for many galaxies, the gas component becomes dominant beyond $3{-}6\;\ell_\star$; for some, we even see the dark matter component taking over beyond $5{-}8\;\ell_\star$. The latter means that ignoring the dark matter gravity can sometimes be problematic, especially when examining the spatially extended H I gas.

We note that the relative contribution of stellar, gas, and dark matter gravity to the gas weight is a related but distinct issue from their relative contribution to the galaxy rotation curve. The latter mostly depends on the cumulative mass of each component within a given three-dimensional radius, whereas the former is more closely related to the local mass surface density near the galaxy mid-plane within the scale height of the gas disk. Considering the different geometries, radial profiles, and scale heights of each component, we can understand why gas gravity can be much more prominent in the local weight budget (especially at large radius) even though its contribution to the rotation curve is always negligible. Similarly, the dark matter gravity already becomes quite important for the rotation curve at intermediate radius, but its effect on the local gas weight can be less pronounced until further out in the galaxy disk.

Similar to the gas scale height results discussed in §[4.2](#sec:result:height), the gas weight also depends on the assumption for the *stellar* disk scale height. As shown by [7](#fig:weight)(b-c), assuming a smaller stellar scale height often results in a larger total weight, because the stellar mass surface density within the gas disk scale height is larger in that case. [7](#fig:weight)(b) shows that the stellar and dark matter contribution to the weight are affected in opposing ways (due to additional constraints imposed by the rotation curve), though the tighter stellar distribution is primarily responsible for the increased total weight. These effects can in turn alter the relative importance of stellar gravity versus gas and dark matter gravity in the total weight budget, which can sometimes change the physical picture at a qualitative level (i.e., whether the gas component dominates over any radius range at all).

We further compare the total gas weight calculated based on five different stellar scale height assumptions (see [3.4](#sec:method:height)). That is, in addition to $H_\star = 0.27\ell_\star$, $H_\star = 0.09\ell_\star$, and $H_\star = H_\mathrm{gas}$ (shown in [6](#fig:allgasscaleheights) right panel), we also consider $H_\star = 800$ pc and $300$ pc as easily implementable alternatives. For many galaxies including NGC 2903 in our sample, adopting $H_\star = 0.27\ell_\star$ ($0.09\ell_\star$) leads to similar results as $H_\star = 800$ pc ($300$ pc). This is partly because the $\ell_\star$ values are close to $\sim3$ kpc for most galaxies in our sample, and partly due to the somewhat mild sensitivity of gas weight to stellar scale height assumptions. Nonetheless, galaxies with scale radii significantly different from $\sim 3$ kpc see deviations of up to 0.1 dex in the inner disk.

We also test the impact of gas weight calculation with different formulae in [7](#fig:weight)(d), comparing the more accurate and broadly applicable Equations [\[eq:Wgas\]](#eq:Wgas)–[\[eq:Wtot\]](#eq:Wtot) with the commonly adopted approximation of [\[eq:Wtot_lim\]](#eq:Wtot_lim). While in most cases the two options give almost identical results, in a few cases they can deviate on a non-trivial level. This is mostly because the gas scale height can approach or even exceed the stellar scale height towards the outer disk in some galaxies (see [5](#fig:scaleheights)), which would violate the assumption of $H_\mathrm{gas} \ll H_\star$ behind [\[eq:Wtot_lim\]](#eq:Wtot_lim). We thus advocate for the use of Equations [\[eq:Wgas\]](#eq:Wgas)–[\[eq:Wtot\]](#eq:Wtot) in combination with [\[eq:Hg_cubic\]](#eq:Hg_cubic) for gas weight calculations, especially in the H I-dominated outer disks.

## Gas Weight and Star Formation

We additionally reassess the relationship between the gas weight (which in equilibrium balances total pressure, ${\cal W} = P_\mathrm{tot}$) and the local SFR surface density, which is predicted by PRFM theory and simulations to follow a close-to-linear relationship (cite: OML2010; Ostriker+Shetty; 2011ApJ...743...25K; 2013ApJ...776....1K; 2015ApJ...815...67K; 2022ApJ...936..137O). In particular, (cite: 2022ApJ...936..137O) predicts the following power-law relation based on the TIGRESS simulations: $$\begin{equation}
\frac{\Sigma_\text{SFR}}{M_\odot \mathrm{\; pc^{-2} \;Myr^{-1}}} =  10^{-7.32}\left(\frac{\cal W}{k_B\;\mathrm{K \; cm^{-3}}}\right)^{1.17}~.
\label{eq:SFRWeight}
\end{equation}$$ This “Ostriker–Kim” relationship between $\mathcal{W}$ and $\Sigma_\mathrm{SFR}$ has previously been examined for the full PHANGS–ALMA galaxy sample by (cite: Sun2020; Sun_etal_2023), using the approximate expression in [\[eq:Wtot_lim\]](#eq:Wtot_lim) for the weight. While we use existing SFR surface density measurements for the these galaxies by (cite: Sun_etal_2023), our detailed gravitational potential modeling and gas weight calculations provide an opportunity to revisit this topic with more rigor, in particular including the dark matter contribution to the weight and using a formulation that does not assume $H_\mathrm{gas} \ll H_\star$.

The left panel in [8](#fig:sfr) shows $\cal W$ versus $\Sigma_\mathrm{SFR}$ across our sample, in comparison with previous observational measurements by (cite: Sun_etal_2023) and [\[eq:SFRWeight\]](#eq:SFRWeight). Our results agree well with previous observational and numerical studies when assuming $H_\star = 0.27\ell_\star$, i.e., matching the assumption used by (cite: Sun_etal_2023) and other observational works. It is worth noting that applying the scaling factor on the stellar mass ($f_\star$) resulted in a tighter $\mathcal{W}$–$\Sigma_\mathrm{SFR}$ relation in comparison to the same relation calculated with the raw, unscaled measurements (rms scatter decreases from 0.18 to 0.16 dex). This reduction in scatter possibly means that our rescaling of the stellar mass also helps reduce a source of systematic uncertainty (namely the stellar M/L ratio) in the gas weight calculation.

The right panel shows the comparison for the two choices of $H_\star$. Because weight is higher for lower $H_\star$, and this primarily affects the higher-pressure, inner regions of galaxies, the $\Sigma_\mathrm{SFR}$ versus weight relation has a slightly shallower slope for smaller $H_\star$. At high pressure, both choices of $H_\star$ lead to a $\Sigma_\mathrm{SFR}$ versus weight relation that is shallower than that obtained from simulations. This discrepancy may be partly attributable to known observational biases (cite: Sun_etal_2023; Schinnerer_Leroy_2024) that would lead to overestimated gas mass (and therefore pressure) near galaxy centers. However, it is also possible that effects other than feedback significantly contribute to driving pressure, which local-patch simulations such as TIGRESS do not capture. We expect current and future galaxy-scale simulations with detailed ISM physics and feedback recipes to further our understanding of ISM dynamical equilibrium and star formation self-regulation in disk galaxies.

Lastly, we directly compare the predicted SFR surface densities from [\[eq:SFRWeight\]](#eq:SFRWeight) for all of our stellar scale height assumptions in [9](#fig:sfrinferred). The comparisons are all made against the fiducial $H_\star = 0.27\ell_\star$ assumption and are plotted as a function of the normalized galactocentric radius. We can see differences of ${\sim}0.1{-}0.2$ dex between $H_\star = 0.09\ell_\star$ and $H_\star = 0.27\ell_\star$ in the inner disk ($\sim 2\ell_\star$), indicating that the choice of stellar scale height can change the predicted SFR by up to $\sim 60\%$ in the inner disk. With $H_\star = H_\mathrm{gas}$ we see larger differences of ${>}0.2$ dex in the inner disk. These trends mirror those in [6](#fig:allgasscaleheights) right panel due to an anticorrelation between gas scale height and weight. They are also essentially the same trends as shown in [7](#fig:weight)(c), but here recast in SFR surface density units. We also plot inferred SFR surface density for two assumed scale heights of $H_\star = 300$ pc and $H_\star = 800$ pc, which provide results similar to $H_\star = 0.09\ell_\star$ and $H_\star = 0.27\ell_\star$ respectively. This shows that for predicting SFR surface density for galaxies in our sample, their galaxy scale radii are similar enough that assuming these simple values would suffice for most galaxies in the sample, though there remains some galaxy-to-galaxy scatter of up to 0.1 dex.

# Summary

We combine high-quality multiwavelength data for a sample of 17 nearby massive disk galaxies to model their stellar, gas, and dark matter mass distribution as functions of galactocentric radius. We use *Spitzer* IRAC images, VLA H I data, and ALMA CO data ([1](#fig:observations)) to trace the stellar, atomic gas, and molecular gas mass, leveraging recent efforts in understanding and accounting for variations in stellar mass-to-light ratio and CO-to-H$_2$ conversion factor (cite: Salim_etal_2016; Leroy2019; Schinnerer_Leroy_2024). These measurements in combination with H I and CO rotation curves allow us to decompose the total dynamical mass and constrain the dark matter mass profile.

From the multi-component radial mass profile, we further derive the gas disk vertical scale height and the gas equilibrium weight in the combined galaxy potential. These calculations are dependent on the treatment of the stellar disk scale height, and we test several plausible options motivated by various Galactic and extragalactic studies (cite: Kregel2002; Zhang2013; Sun2020). We also assess the validity of a commonly used approximation for the weight calculation over a range of conditions present among our targets. Finally, our refined gas weight measurements enable a reassessment of its relationship with local SFR surface density, in contexts of the PRFM theory (cite: 2022ApJ...936..137O) and previous observational results (cite: Sun2020; Sun_etal_2023).

Our key findings are as follows:

1.  We construct a joint stellar–gas–dark matter mass model for each galaxy that can successfully account for its measured rotation curve ([3](#fig:vsquared)). This is achieved only after combining the CO and H I rotation curves and rescaling the stellar mass component according to the maximal disk assumption (cite: maximaldisk). The scaling factor applied to the stellar component is between $0.8{-}1.5$ for most (13 out of 17) galaxies ([4](#fig:scaling)), consistent with the expected uncertainty of our stellar M/L ratio estimates relative to SPS-based results.

2.  Our multi-component model suggests that the dark matter contribution to the circular velocity often exceeds the stellar contribution at $R\approx3{-}5\,\ell_\star$, except for a few cases where the radial coverage of the data does not reach the dark matter dominated outer disk. The gas contribution to the circular velocity remains subdominant at all radii.

3.  We find that the gas disk vertical scale height is typically $H_\mathrm{gas}\lesssim100$ pc in inner disks and increases towards the outer disk to ${>}500$ pc ([5](#fig:scaleheights)–[6](#fig:allgasscaleheights)), consistent with other Galactic and extragalactic studies. This increasing trend with radius is present regardless of the assumed stellar disk scale height $H_\star$. The stellar disk scale height assumption matters more in the inner disk, with a $3\times$ difference in $H_\star$ translating into a $30{-}40\%$ difference in $H_\mathrm{gas}$. Its impact becomes smaller (${<}10\%$) towards the outer disk, as stellar gravity becomes less important and the gas scale height approaches or even exceeds the stellar scale height.

4.  For the gas equilibrium weight in the combined galaxy potential, the stellar gravity contribution is also dominant in the innermost disk, but the gas self-gravity contribution can often surpass it at $3{-}6\,\ell_\star$; for fewer galaxies, the dark matter gravity contribution becomes dominant beyond $5{-}8\,\ell_\star$ ([7](#fig:weight)). The relative importance of these contributions in the gas weight budget differs from that in the circular velocity decomposition due to the different 3D geometry of these mass components.

5.  The gas weight calculation also mildly depends on the stellar scale height assumption, with smaller stellar scale heights leading to larger gas weights ([7](#fig:weight)). More importantly, the commonly adopted approximation for the weight calculation ([\[eq:Wtot_lim\]](#eq:Wtot_lim)) can fail when the gas and stellar disk scale height become comparable, which does happen in a few galaxies towards the outer disks.

6.  When examining the gas weight versus SFR surface density relation ($\mathcal{W}_\mathrm{tot}$–$\Sigma_\mathrm{SFR}$, [8](#fig:sfr)), our refined gas weight calculation still results in overall agreement with simulation predictions (cite: 2022ApJ...936..137O) and previous observational measurements (cite: Sun2020; Sun_etal_2023). The slope of this relation appears mildly shallower than the simulation prediction for both $H_\star$ assumptions, possibly due to observational biases at the high pressure end and/or physics not captured by subgalactic, local-patch simulations.

This work represents one of several ongoing efforts in modeling the mass distribution of nearby disk galaxies for the purpose of assessing ISM dynamics and self-regulation. We anticipate follow-up studies to improve upon this work in various ways, including joint CO-H I kinematic modeling, dedicated analyses of the influence of stellar bars and central structures on gas kinematics, as well as obtaining independent constraints on stellar disk scale heights based on spectroscopic stellar velocity dispersion measurements.

We thank Neta Bahcall for helpful discussions.

JS acknowledges support by the National Aeronautics and Space Administration (NASA) through the NASA Hubble Fellowship grant HST-HF2-51544 awarded by the Space Telescope Science Institute (STScI), operated by the Association of Universities for Research in Astronomy, Inc., under contract NAS 5-26555. The work of ECO was partly supported by grant No. 510940 from the Simons Foundation. EDT is supported by the European Research Council (ERC) under grant agreement no. 101040751.

This paper makes use of the following ALMA data, which have been processed as part of the PHANGS–ALMA $\mathrm{CO}\,(2\text{--}1)$ survey:\
ADS/JAO.ALMA#2015.1.00925.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2017.1.00392.S,\
ADS/JAO.ALMA#2017.1.00886.L,\
ADS/JAO.ALMA#2018.1.01651.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of NSF operated under cooperative agreement by Associated Universities, Inc (AUI).

This work is based in part on observations made with NSF’s Karl G. Jansky Very Large Array (VLA; project code: 18B-184). VLA is also operated by NRAO.

This work is based in part on observations made with the *Spitzer Space Telescope*, which is operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with NASA.

We acknowledge the usage of the SAO/NASA Astrophysics Data System.

# Facilities

ALMA, Spitzer, VLA

# Software

`NumPy` (cite: NumPy_2020), `SciPy` (cite: SciPy_2020), `Astropy` (cite: Astropy2013; Astropy2018; AstroPy_2022), `Matplotlib` (cite: Matplotlib_2007), `Scikit-learn` (cite: Sklearn_2011), `hankel` (cite: Murray2019), `Pandas` (cite: Pandas_2020), `3D-Barolo` (cite: DiTeodoro_Fraternali_2015), `MegaTable` (cite: MegaTable_4.0).

# Rotation Curve Modeling Results

We show radial profiles of gas and stellar surface densities, gas velocity dispersions, as well as rotation curve modeling results for all 17 galaxies in Figure Set [10](#fig:gallery).

# Gas Weight and Vertical Scale Height Profiles

We report radial profiles of gas weight and vertical scale height for all 17 galaxies in [11](#fig:spam).

natexlab

(ref: Anand_etal_2021) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: AstroPy_2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bacchini_etal_2019) Bacchini, C., Fraternali, F., Iorio, G., & Pezzulli, G. 2019, A&A, 622, A64, doi: [`10.1051/0004-6361/201834382`](http://doi.org/10.1051/0004-6361/201834382)

(ref: 2021MNRAS.503.3643B) Barrera-Ballesteros, J. K., Sánchez, S. F., Heckman, T., et al. 2021, MNRAS, 503, 3643, doi: [`10.1093/mnras/stab755`](http://doi.org/10.1093/mnras/stab755)

(ref: Bell_deJong_2001) Bell, E. F., & de Jong, R. S. 2001, ApJ, 550, 212, doi: [`10.1086/319728`](http://doi.org/10.1086/319728)

(ref: Bershady_etal_2010) Bershady, M. A., Verheijen, M. A. W., Swaters, R. A., et al. 2010, ApJ, 716, 198, doi: [`10.1088/0004-637X/716/1/198`](http://doi.org/10.1088/0004-637X/716/1/198)

(ref: 2008gady.book.....B) Binney, J., & Tremaine, S. 2008, Galactic Dynamics: Second Edition (Princeton University Press)

(ref: 2004ApJ...612L..29B) Blitz, L., & Rosolowsky, E. 2004, ApJL, 612, L29, doi: [`10.1086/424661`](http://doi.org/10.1086/424661)

(ref: Bosma_1981) Bosma, A. 1981, AJ, 86, 1825, doi: [`10.1086/113063`](http://doi.org/10.1086/113063)

(ref: Bovy) Bovy, J. in preparation, Dynamics and Astrophysics of Galaxies (Princeton University Press). <https://galaxiesbook.org/>

(ref: Bovy_Rix_2013) Bovy, J., & Rix, H.-W. 2013, ApJ, 779, 115, doi: [`10.1088/0004-637X/779/2/115`](http://doi.org/10.1088/0004-637X/779/2/115)

(ref: Chiang_etal_2024) Chiang, I.-D., Sandstrom, K. M., Chastenet, J., et al. 2024, ApJ, 964, 18, doi: [`10.3847/1538-4357/ad23ed`](http://doi.org/10.3847/1538-4357/ad23ed)

(ref: Conselice_2014) Conselice, C. J. 2014, ARA&A, 52, 291, doi: [`10.1146/annurev-astro-081913-040037`](http://doi.org/10.1146/annurev-astro-081913-040037)

(ref: things) de Blok, W. J. G., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2648, doi: [`10.1088/0004-6256/136/6/2648`](http://doi.org/10.1088/0004-6256/136/6/2648)

(ref: DiTeodoro_Fraternali_2015) Di Teodoro, E. M., & Fraternali, F. 2015, MNRAS, 451, 3021, doi: [`10.1093/mnras/stv1213`](http://doi.org/10.1093/mnras/stv1213)

(ref: DiTeodoro_Peek_2021) Di Teodoro, E. M., & Peek, J. E. G. 2021, ApJ, 923, 220, doi: [`10.3847/1538-4357/ac2cbd`](http://doi.org/10.3847/1538-4357/ac2cbd)

(ref: DiTeodoro+2023) Di Teodoro, E. M., Posti, L., Fall, S. M., et al. 2023, MNRAS, 518, 6340, doi: [`10.1093/mnras/stac3424`](http://doi.org/10.1093/mnras/stac3424)

(ref: Eibensteiner_etal_2024) Eibensteiner, C., Sun, J., Bigiel, F., et al. 2024, arXiv e-prints, arXiv:2407.01716, doi: [`10.48550/arXiv.2407.01716`](http://doi.org/10.48550/arXiv.2407.01716)

(ref: 2022MNRAS.511.3863E) Everall, A., Belokurov, V., Evans, N. W., Boubert, D., & Grand, R. J. J. 2022, MNRAS, 511, 3863, doi: [`10.1093/mnras/stac305`](http://doi.org/10.1093/mnras/stac305)

(ref: Frank2016) Frank, B. S., de Blok, W. J. G., Walter, F., Leroy, A., & Carignan, C. 2016, AJ, 151, 94, doi: [`10.3847/0004-6256/151/4/94`](http://doi.org/10.3847/0004-6256/151/4/94)

(ref: Guerrette_etal_2024) Guerrette, J. A., Mosenkov, A. V., Spencer, D., & Shakespear, Z. D. 2024, Research in Astronomy and Astrophysics, 24, 035002, doi: [`10.1088/1674-4527/ad1a06`](http://doi.org/10.1088/1674-4527/ad1a06)

(ref: NumPy_2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Hassan_etal_2024) Hassan, S., Ostriker, E. C., Kim, C.-G., et al. 2024, ApJ, 975, 151, doi: [`10.3847/1538-4357/ad73a4`](http://doi.org/10.3847/1538-4357/ad73a4)

(ref: 2017ApJ...835..201H) Herrera-Camus, R., Bolatto, A., Wolfire, M., et al. 2017, ApJ, 835, 201, doi: [`10.3847/1538-4357/835/2/201`](http://doi.org/10.3847/1538-4357/835/2/201)

(ref: Herrmann_etal_2008) Herrmann, K. A., Ciardullo, R., Feldmeier, J. J., & Vinciguerra, M. 2008, ApJ, 683, 630, doi: [`10.1086/589920`](http://doi.org/10.1086/589920)

(ref: Heyer_Dame_2015) Heyer, M., & Dame, T. M. 2015, ARA&A, 53, 583, doi: [`10.1146/annurev-astro-082214-122324`](http://doi.org/10.1146/annurev-astro-082214-122324)

(ref: Matplotlib_2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2008ApJ...673..864J) Jurić, M., Ivezić, Ž., Brooks, A., et al. 2008, ApJ, 673, 864, doi: [`10.1086/523619`](http://doi.org/10.1086/523619)

(ref: Kauffmann_etal_2003) Kauffmann, G., Heckman, T. M., White, S. D. M., et al. 2003, MNRAS, 341, 33, doi: [`10.1046/j.1365-8711.2003.06291.x`](http://doi.org/10.1046/j.1365-8711.2003.06291.x)

(ref: 2011ApJ...743...25K) Kim, C.-G., Kim, W.-T., & Ostriker, E. C. 2011, ApJ, 743, 25, doi: [`10.1088/0004-637X/743/1/25`](http://doi.org/10.1088/0004-637X/743/1/25)

(ref: 2015ApJ...815...67K) Kim, C.-G., & Ostriker, E. C. 2015, ApJ, 815, 67, doi: [`10.1088/0004-637X/815/1/67`](http://doi.org/10.1088/0004-637X/815/1/67)

(ref: 2013ApJ...776....1K) Kim, C.-G., Ostriker, E. C., & Kim, W.-T. 2013, ApJ, 776, 1, doi: [`10.1088/0004-637X/776/1/1`](http://doi.org/10.1088/0004-637X/776/1/1)

(ref: 2024ApJ...972...67K) Kim, C.-G., Ostriker, E. C., Kim, J.-G., et al. 2024, ApJ, 972, 67, doi: [`10.3847/1538-4357/ad59ab`](http://doi.org/10.3847/1538-4357/ad59ab)

(ref: Koch_etal_2018) Koch, E. W., Rosolowsky, E. W., Lockman, F. J., et al. 2018, MNRAS, 479, 2505, doi: [`10.1093/mnras/sty1674`](http://doi.org/10.1093/mnras/sty1674)

(ref: Kormendy_Kennicutt_2004) Kormendy, J., & Kennicutt, Robert C., J. 2004, ARA&A, 42, 603, doi: [`10.1146/annurev.astro.42.053102.134024`](http://doi.org/10.1146/annurev.astro.42.053102.134024)

(ref: Kregel2002) Kregel, M., van der Kruit, P. C., & de Grijs, R. 2002, MNRAS, 334, 646, doi: [`10.1046/j.1365-8711.2002.05556.x`](http://doi.org/10.1046/j.1365-8711.2002.05556.x)

(ref: rotation) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897

(ref: Leroy2019) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24, doi: [`10.3847/1538-4365/ab3925`](http://doi.org/10.3847/1538-4365/ab3925)

(ref: Leroy2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJ, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: ManceraPina_etal_2022) Mancera Piña, P. E., Fraternali, F., Oosterloo, T., et al. 2022, MNRAS, 514, 3329, doi: [`10.1093/mnras/stac1508`](http://doi.org/10.1093/mnras/stac1508)

(ref: diskmass) Martinsson, T. P. K., Verheijen, M. A. W., Westfall, K. B., et al. 2013a, A&A, 557, A131, doi: [`10.1051/0004-6361/201321390`](http://doi.org/10.1051/0004-6361/201321390)

(ref: Martinsson_etal_2013a) —. 2013b, A&A, 557, A130, doi: [`10.1051/0004-6361/201220515`](http://doi.org/10.1051/0004-6361/201220515)

(ref: McClure-Griffiths_etal_2023) McClure-Griffiths, N. M., Stanimirović, S., & Rybarczyk, D. R. 2023, ARA&A, 61, 19, doi: [`10.1146/annurev-astro-052920-104851`](http://doi.org/10.1146/annurev-astro-052920-104851)

(ref: Murray2019) Murray, S. G., & Poulin, F. J. 2019, Journal of Open Source Software, 4, 1397, doi: [`10.21105/joss.01397`](http://doi.org/10.21105/joss.01397)

(ref: NFW) Navarro, J. F., Frenk, C. S., & White, S. D. M. 1996, ApJ, 462, 563, doi: [`10.1086/177173`](http://doi.org/10.1086/177173)

(ref: 2022ApJ...936..137O) Ostriker, E. C., & Kim, C.-G. 2022, ApJ, 936, 137, doi: [`10.3847/1538-4357/ac7de2`](http://doi.org/10.3847/1538-4357/ac7de2)

(ref: OML2010) Ostriker, E. C., McKee, C. F., & Leroy, A. K. 2010, ApJ, 721, 975, doi: [`10.1088/0004-637X/721/2/975`](http://doi.org/10.1088/0004-637X/721/2/975)

(ref: Ostriker+Shetty) Ostriker, E. C., & Shetty, R. 2011, ApJ, 731, 41, doi: [`10.1088/0004-637X/731/1/41`](http://doi.org/10.1088/0004-637X/731/1/41)

(ref: Pandas_2020) pandas development team, T. 2020, pandas-dev/pandas: Pandas, latest, Zenodo, doi: [`10.5281/zenodo.3509134`](http://doi.org/10.5281/zenodo.3509134)

(ref: Sklearn_2011) Pedregosa, F., Varoquaux, G., Gramfort, A., et al. 2011, Journal of Machine Learning Research, 12, 2825

(ref: Querejeta_etal_2021) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: Rubin) Rubin, V. C., Ford, W. K., J., & Thonnard, N. 1980, ApJ, 238, 471, doi: [`10.1086/158003`](http://doi.org/10.1086/158003)

(ref: maximaldisk) Sackett, P. D. 1997, ApJ, 483, 103, doi: [`10.1086/304223`](http://doi.org/10.1086/304223)

(ref: Salim_etal_2018) Salim, S., Boquien, M., & Lee, J. C. 2018, ApJ, 859, 11, doi: [`10.3847/1538-4357/aabf3c`](http://doi.org/10.3847/1538-4357/aabf3c)

(ref: Salim_etal_2016) Salim, S., Lee, J. C., Janowiecki, S., et al. 2016, ApJS, 227, 2, doi: [`10.3847/0067-0049/227/1/2`](http://doi.org/10.3847/0067-0049/227/1/2)

(ref: Salo_etal_2015) Salo, H., Laurikainen, E., Laine, J., et al. 2015, ApJS, 219, 4, doi: [`10.1088/0067-0049/219/1/4`](http://doi.org/10.1088/0067-0049/219/1/4)

(ref: Sanchez_2020) Sánchez, S. F. 2020, ARA&A, 58, 99, doi: [`10.1146/annurev-astro-012120-013326`](http://doi.org/10.1146/annurev-astro-012120-013326)

(ref: Schinnerer_Leroy_2024) Schinnerer, E., & Leroy, A. K. 2024, ARA&A, 62, 369, doi: [`10.1146/annurev-astro-071221-052651`](http://doi.org/10.1146/annurev-astro-071221-052651)

(ref: Sheth2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397, doi: [`10.1086/657638`](http://doi.org/10.1086/657638)

(ref: Somerville2025) Somerville, R. S., Gabrielpillai, A., Hadzhiyska, B., & Genel, S. 2025, arXiv e-prints, arXiv:2502.03679, doi: [`10.48550/arXiv.2502.03679`](http://doi.org/10.48550/arXiv.2502.03679)

(ref: MegaTable_4.0) Sun, J. 2023, PhangsTeam/MegaTable: PHANGS mega-table pipeline release v4.0, v4.0, Zenodo, doi: [`10.5281/zenodo.8049365`](http://doi.org/10.5281/zenodo.8049365)

(ref: Sun2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: Sun2020) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020a, ApJ, 892, 148, doi: [`10.3847/1538-4357/ab781c`](http://doi.org/10.3847/1538-4357/ab781c)

(ref: Sun2020a) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020b, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: Sun2022) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43, doi: [`10.3847/1538-3881/ac74bd`](http://doi.org/10.3847/1538-3881/ac74bd)

(ref: Sun_etal_2023) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL, 945, L19, doi: [`10.3847/2041-8213/acbd9c`](http://doi.org/10.3847/2041-8213/acbd9c)

(ref: Thompson_Heckman_2024) Thompson, T. A., & Heckman, T. M. 2024, ARA&A, 62, 529, doi: [`10.1146/annurev-astro-041224-011924`](http://doi.org/10.1146/annurev-astro-041224-011924)

(ref: vanAlbada_etal_1985) van Albada, T. S., Bahcall, J. N., Begeman, K., & Sancisi, R. 1985, ApJ, 295, 305, doi: [`10.1086/163375`](http://doi.org/10.1086/163375)

(ref: vanderHulst_etal_2001) van der Hulst, J. M., van Albada, T. S., & Sancisi, R. 2001, in Astronomical Society of the Pacific Conference Series, Vol. 240, Gas and Galaxy Evolution, ed. J. E. Hibbard, M. Rupen, & J. H. van Gorkom, 451

(ref: vanderKruit_Freeman_1984) van der Kruit, P. C., & Freeman, K. C. 1984, ApJ, 278, 81, doi: [`10.1086/161769`](http://doi.org/10.1086/161769)

(ref: vanderKruit_Freeman_2011) —. 2011, ARA&A, 49, 301, doi: [`10.1146/annurev-astro-083109-153241`](http://doi.org/10.1146/annurev-astro-083109-153241)

(ref: vanderKruit_Searle_1981) van der Kruit, P. C., & Searle, L. 1981, A&A, 95, 105

(ref: SciPy_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Walter2008) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563, doi: [`10.1088/0004-6256/136/6/2563`](http://doi.org/10.1088/0004-6256/136/6/2563)

(ref: Yim_etal_2011) Yim, K., Wong, T., Howk, J. C., & van der Hulst, J. M. 2011, AJ, 141, 48, doi: [`10.1088/0004-6256/141/2/48`](http://doi.org/10.1088/0004-6256/141/2/48)

(ref: Yim_etal_2014) Yim, K., Wong, T., Xue, R., et al. 2014, AJ, 148, 127, doi: [`10.1088/0004-6256/148/6/127`](http://doi.org/10.1088/0004-6256/148/6/127)

(ref: Zhang2013) Zhang, L., Rix, H.-W., van de Ven, G., et al. 2013, ApJ, 772, 108, doi: [`10.1088/0004-637X/772/2/108`](http://doi.org/10.1088/0004-637X/772/2/108)

[^1]: Since the H I rotation curves have larger radial bin width than the CO curves, we also assign proportionally larger weights to each of the H I data points when using the hybrid rotation curves in further analyses.

[^2]: We adopt the *exponential* disk scale height convention, such that the volume density near the mid-plane is $\rho_\star=\Sigma_\star/(2H_\star)$.

[^3]: This does not take into account the magnetic contribution to $\sigma_\mathrm{eff}$, which could increase its value by $\sim 30\%$ (cite: 2022ApJ...936..137O; 2024ApJ...972...67K).

</paper>

Write the methods card for this paper.