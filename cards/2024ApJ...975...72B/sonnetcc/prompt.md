# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...975...72B\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...975...72B",
 "title": "Measuring the <SUP>34</SUP>S and <SUP>33</SUP>S Isotopic Ratios of Volatile Sulfur during Planet Formation",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Booth, Alice S.",
 "n_authors": 12,
 "arxiv_id": "2409.03885",
 "doi": "10.3847/1538-4357/ad7817",
 "alma_projects_linked_by_archive": [
  "2017.1.00834.S",
  "2021.1.00738.S"
 ]
}
```

Paper text:
<paper>
# Measuring the and isotopic ratios of volatile sulfur during planet formation

## Abstract

Stable isotopic ratios constitute powerful tools for unraveling the thermal and irradiation history of volatiles. In particular, we can use our knowledge of the isotopic fractionation processes active during the various stages of star, disk and planet formation to infer the origins of different volatiles with measured isotopic patterns in our own solar system. Observations of planet-forming disks with the Atacama Large Millimeter/submillimeter Array (ALMA) now readily detect the heavier isotopologues of C, O and N, while the isotopologue abundances and isotopic fractionation mechanisms of sulfur species are less well understood. Using ALMA observations of the SO and isotopologues in the nearby, molecule-rich disk around the young star Oph-IRS 48 we present the first constraints on the combined / and / isotope ratios in a planet-forming disk. Given that these isotopologues likely originate in relatively warm gas ($>$50 K), like most other Oph-IRS 48 volatiles, SO is depleted in heavy sulfur while is enriched compared to solar system values. However, we cannot completely rule out a cooler gas reservoir, which would put the SO sulfur ratios more in line with comets and other solar system bodies. We also constrain the /SO ratio and find the limit to be consistent with solar system values given a temperature of 60 K. Together these observations show that we should not assume solar isotopic values for disk sulfur reservoirs, but additional observations are needed to determine the chemical origin of the abundant SO in this disk, inform on what isotopic fractionation mechanism(s) are at play, and aid in unravelling the history of the sulfur budget during the different stages of planet formation.

# Introduction

The volatile building blocks of planets, moons and comets exist as gas and ice in protoplanetary disks, which in turn have an origin as ices in cold, dark, molecular clouds (cite: 2021PhR...893....1O). On million-year timescales, the material in the disk is subject to a variety of physical and chemical processes that can alter this initially inherited volatile reservoir (cite: 2022arXiv221214529A). The isotopic ratios of volatile elements can be used as tools to unravel the history of this material throughout the different stages of the star, disk and planet formation. The main drivers of isotopic fractionation are low temperature chemical reactions, due to the differences in the zero-point vibrational energies of different isotopologues, and isotope selective photo-dissociation (see (cite: 2023ASPC..534.1075N) for a recent review).

From sub-millimeter observations of planet-forming disks we now have detections of simple molecules containing the heavier isotopes D, , , , and (cite: 2023ARA&A..61..287O). One of the most readily detected isotopes in disks is deuterium and the measured enhancement of D/H in simple molecules (e.g., HCN, , and ) can be explained via in-situ isotope exchange reactions that are active in the cold outer disk (cite: 2015ApJ...802L..23F; 2018ApJ...855..119A; 2021ApJS..257...10C; 2023ApJ...943...35M). The / ratio has also been measured in disks for both HCN and CN, where fractionation can likely be attributed to the isotope-selective photo-dissociation of in the disk atmosphere (cite: 2014A&A...562A..61H; 2017ApJ...836...30G; 2017A&A...603L...6H; 2019A&A...632L..12H; 2018A&A...615A..75V). Although is readily detectable in nearby disks, the optical depth of the line typically prevents a measurement of the oxygen isotope ratio from CO observations alone. Recent work from (cite: 2022ApJ...926..148F) shows that optically thin isotopologue lines can give access to the / ratio in disks, which can be used to test mechanisms for recovering the oxygen isotope fractionation observed in the Solar System (cite: 2012E&PSL.313...56M). In the specific case of the TW Hya disk, the relative abundance of is found to be consistent with the local interstellar medium value, i.e., is not enhanced or depleted in the disk gas (cite: 2022ApJ...926..148F).

Overall, the results for Class II disks so far do not require the inheritance of fractionated material from the cold cloud stage. The least understood of the detected volatile elements in disks is sulfur, where both its primary volatile form on the ice and the expected isotopic ratios due to thermal and photo-processing are unclear. The rarer isotopologues of CS, and , have been detected in a handful of disks, but we lack concrete information on potential in-situ or inherited isotope-fractionation processes that may have occurred (cite: 2020ApJ...893..101L; 2019ApJ...876...72L; 2021ApJS..257...12L; 2021A&A...653L...5P; 2023A&A...678A.146B). However, when considering comets, the remnant icy material from the protoplanetary disk that formed our Solar System, we have significantly more information. The isotopic ratios in sulfur-bearing molecules have been well measured in comet 67P/Churyumov-Gerasimenko (67P/C-G) and there are indicators that isotopic fractionation processes have occurred (cite: 2017MNRAS.469S.230P; 2017MNRAS.469S.787C; 2020MNRAS.498.5855A). In particular, both the / and / ratios have been derived for a collection of simple molecules and these measurements trace a bulk depletion of heavier isotopes relative to Solar System standards that cannot be explained by photo-dissociation (cite: 2017MNRAS.469S.787C). Additionally, the simple S-bearing molecules SO, and OCS are all enhanced in by approximately a factor of two relative to solar (cite: 2020MNRAS.498.5855A) and / is well above the interstellar elemental ratio (cite: 2017RSPTA.37560253A). The cometary dust particles on the other hand have a / ratio consistent with the expected terrestrial value (cite: 2017MNRAS.469S.230P).

The disk with the most observed volatile sulfur, and therefore the source with the most promise for measuring isotopic ratios of sulfur, is the Oph-IRS 48 disk. Oph-IRS 48 is a nearby (135 pc), young Herbig Ae star (cite: 2012ApJ...744..116B; Gaia2018) host to a molecule-rich transition disk with an asymmetric dust trap where, both, SO and have been robustly detected (cite: 2021A&A...651L...6B; Booth2023_irs48). The observable chemistry in this disk appears to be dominated by the sublimation of ices indicated by the presence of and other complex organic molecules in the gas phase (cite: 2021A&A...651L...5V; 2022A&A...659A..29B; Booth2023_irs48). This makes the Oph-IRS 48 disk a powerful observational laboratory to investigate the isotopic make-up of the typically hidden icy reservoir in disks. Here, we provide the first measurements of the combined / and / ratios in a planet-forming disk. We also report a stringent upper-limit on the abundance and use this to estimate the corresponding lower-limit of the / isotopic ratio.

![](IRS48_moment0_v2.png)

# Methods

We use molecular line observations of the Oph-IRS 48 planet-forming disk taken with the Atacama Large Millimeter/sub-millimeter Array (ALMA) from the programs 2017.1.00834.S (PI: Adriana Pohl) and 2021.1.00738.S (PI: Alice S. Booth). The former were first presented in (cite: 2021A&A...651L...5V) and (cite: 2021A&A...651L...6B) and the latter in (cite: Booth2023_irs48). The 2017.1.00834.S data were pipeline calibrated by (cite: 2020ApJ...900...81O) and (cite: 2021A&A...651L...6B) imaged these data with CASA task `tCLEAN` (cite: 2007ASPC..376..127M) at a velocity resolution of 1.7 km s${^{-1}}$ and a Briggs robust weighting of 0.5 resulting in a $\approx$0.45$\ensuremath{''}$ beam. The 2021.1.00738.S data were self-calibrated (both phase and amplitude) and imaged with CASA task `tCLEAN` at a velocity resolution of 0.9 km s${^{-1}}$ with a Briggs robust weighting of 0.5 resulting in a $\approx$0.3$\ensuremath{''}$ beam (cite: 2021A&A...651L...5V). All integrated intensity maps were generated using Keplerian masks (cite: rich_teague_2020_4321137). In the above referenced works, the data calibration, line identification and imaging steps are described in full detail.

The focus of this paper is on the sulfur-bearing molecules covered in the data. (cite: 2021A&A...651L...6B) and (cite: Booth2023_irs48) report the detections of SO, , , and and we use the integrated intensity maps from these works. One transition of with a $\mathrm{A_{ul}}\approx10^{-3.2}$ s$^{-1}$ is covered in the data from (cite: Booth2023_irs48) and we tentatively detect this line in one velocity channel (0.9 km $\mathrm{s^{-1}}$) at a signal-to-noise ratio of 4. Although only detected in one channel, this is the same velocity channel where the main SO isotope lines are the brightest and the local line-width per pixel is only $\approx$2-3 km s$^{-1}$. A robust detection would require 3$\sigma$ emission over $>$3 channels to confirm. We therefore consider this as an upper-limit on the abundance in this disk. The channel maps of the line are shown in Figure [4](#fig:channels). This line was imaged in the same manner as the other lines from (cite: Booth2023_irs48) and is part of the same ALMA data set. Table [\[tab:tab1\]](#tab:tab1) lists the properties of the transitions and images presented in this paper.

Under the typical assumptions of optically thin line emission and local thermodynamic equilibrium (cite: 2018ApJ...859..131L), we estimate the peak column density traced by the SO and isotopologues detected in the Oph-IRS 48 disk. The various line properties and partition functions of each isotopologue are taken from the Cologne Database for Molecular Spectroscopy (cite: 2001A&A...370L..49M; 2005JMoSt.742..215M; 2016JMoSp.327...95E) with data from (cite: 1985JPCRD..14..395L; 1992ApJ...399..325L; 1996JMoSp.180..197K). The errors in the peak column densities are propagated from the errors in the integrated intensity maps (as listed in Table [\[tab:tab1\]](#tab:tab1)) where these errors are a measure of the root mean square noise (rms) of the line-free regions of the images without Keplerian masking. The rms in the is lower than the other lines since this integrated map is only calculated for one channel.

We calculate these column densities at a range of excitation temperatures (30 to 150 K in steps of 10 K) which cover the range of expected excitation conditions in this disk. The lower limit of this range is informed by the brightness temperature of the midplane millimeter dust which is at a minimum of 30 K and the upper limit is from the $\gtrsim$100 K brightness temperature of the optically thick CO isotopologues, which trace the disk surface layers (cite: 2021A&A...651L...5V; 2023A&A...673A...7L) and, the rotational temperatures of , and ((cite: 2021A&A...651L...5V) and Temmink et al. in prep.). In particular, using the line survey data of the Oph-IRS 48 disk presented in (cite: Booth2023_irs48), where $>$10 lines are detected with an upper energy level range of 35 to 200 K, Temmink et al. 2024 (in prep.) find that the rotational temperature for to be very well constrained to $\approx$60 K at the emission peak. As the SO and emission is co-spatial in the observations (as shown in Figure [1](#fig:fig1)) and chemically linked in disk models through their origins in the warm molecular layer, not the disk midplane (cite: 2024MNRAS.528..388K), we expect them to trace the same gas temperature. Additionally, to support this assumption of warm gas, in disk models, SO and freeze out at dust temperatures less than $\approx$40 K and $\approx$60 K, respectively (cite: 2018A&A...617A..28S). We note that this will depend on the assumed binding energies for example, (cite: 2021arXiv211006010P) used quantum chemical calculations to show that SO has a range of binding energies on a water ice cluster (60 molecules), spanning a temperature range of 933 to 3483 K with an average value of 2128 K, which is lower than the values listed in UDfA and KIDA (2800 and 2600 K, respectively). Ideally, we would have an independent measure of the SO rotational temperature but in total, (cite: Booth2023_irs48) detect only three SO lines in the Oph-IRS 48 disk and the high line opacities of the $J=7_8-6_7$ and $J=8_8-7_7$ transitions do not allow for a rotation diagram analysis. In this work, we only use the optically thinnest transition detected ($J=3_3-3_2$) as a measure of the SO column density. For and two lines of each are detected and we take the average column density traced by these lines at each temperature. Therefore, although we expect the SO to trace warm 60 K gas, we cannot make an independent temperature measurement to confirm this, therefore, we explore a range of higher and lower gas temperatures to see how sensitive the inferred isotopic ratios is to this assumption. Due to the different intrinsic properties of the transitions of each isotopologue these ratios will vary with the assumed gas temperature.

To compare our isotope ratios with measurements of isotopic variations in Solar System bodies, we also calculate the deviation of our ratios relative to the Vienna Canyon Diablo Troilite (V-CDT). This is the most common isotopic standard used in comet and meteorite studies. The standard ratios used are 22.64 for /, 126.9 for / and 498.7 for / (cite: 2001GeCoA..65.2433D; 2001RCMS...15..501W). These differ slightly from the local ISM ratios, where in particular, / is 550 (cite: 1994ARA&A..32..191W). The deviations ($\delta$) are reported in units of per mille () and are calculated as followed: $$\delta\ce{^{34}S} = [(\ce{^{34}S}/\ce{^{32}S})_{disk}/(\ce{^{34}S}/\ce{^{32}S})_{standard} -1]~\times~1000$$ where the above is an example for the / ratio.

# Results

In Figure [1](#fig:fig1), we present the integrated intensity maps of sulfur isotopologues in the Oph IRS 48 disk and the 0.9 mm continuum emission. The molecular species all appear co-spatial and are only present in the Southern region of the disk, where the millimeter dust grains are most prominent. From these integrated intensity maps, we take the peak integrated flux and use this to calculate the molecular column density traced by each of the isotopologues. The resulting peak column densities, corresponding isotopic ratios, and deviations from V-CDT at 30, 60 and 100 K are listed in Table [\[tab:tab2\]](#tab:tab2) and across the full temperature range in Figure [2](#fig:fig2). We also compared these peak column densities to the averaged column densities derived from the whole SO and emitting region and find that the resulting isotope ratios, the key result of this paper, are within the quoted 1 $\sigma$ errors.

In Figure [5](#fig:fig4), we show the inferred ratios as a function of the assumed temperature. The isotope ratios derived from all increase with increasing gas temperature and both and are consistent with the V-CDT values at temperatures lower than $\approx$50 K. When adopting our fiducial temperature of 60 K, we find that traced in SO line emission, the Oph-IRS 48 disk is depleted in both and with /=$34\pm4$ and /=$290\pm60$. The / lower limit from SO of $>$500 is consistent with the V-CDT value. The SO $J=3_3-3_2$ transition is optically thin with $\tau \approx 0.1$ and since the rare isotopes of SO are depleted relative to this, optical depth cannot explain the anomalous

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Mol. | Transition | Frequency | E$\mathrm{_{up}}$ | log$_{10}$(A$_{\mathrm{ul}}$) | Beam (Position Angle) | Peak Integrated Intensity | Uncertainty |  |  |
|  |  | \[GHz\] | \[K\] | \[s$^{-1}$\] | \[$''$$\times$$''$ ($^{\circ}$)\] | \[mJy/beam km/s\] | \[mJy/beam km/s\] |  |  |
|  | $J=3_{3}-3_{2}$ | 339.3414590 | 25.5 | -4.8372 | 0.34$\times$0.28 (88) | 56.2 | 4.7 |  |  |
|  | $J=8_{8}-7_{7}$ | 339.8572694 | 77.3 | -3.2944 | 0.34$\times$0.27 (88) | 58.7 | 4.7 |  |  |
|  | $J=9_{8}-8_{7}$ | 337.5801467 | 86.1 | -3.3109 | 0.34$\times$0.28 (-89) | 52.1 | 5.2 |  |  |
| $^{*}$ | $J=7_{8}-6_{7}$ | 337.1986199 | 80.5 | -3.3158 | 0.34$\times$0.28 (-90) | 22.9 | 5.3 |  |  |
| $^{*}$ | $J=9_{8}-8_{7}$ | 343.0882949 | 78.0 | -3.2819 | 0.34$\times$0.27 (-85) | 29.5 | 4.7 |  |  |
|  | $J=8_{9}-7_{8}$ | 355.5735893 | 93.1 | -3.2414 | 0.33$\times$0.26 (-85) | 3.6 | 0.9 |  |  |
|  | $J=6_{4,2}-6_{3,3}$ | 357.9258478 | 58.6 | -3.5845 | 0.33$\times$0.26 (-85) | 50.1 | 5.9 |  |  |
|  | $J=6_{3,3}-5_{2,4}$ | 362.1582327 | 40.7 | -3.4839 | 0.53$\times$0.42 (80) | 46.5 | 5.0 |  |  |

: Molecular line and image properties where molecular transition data are taken from CDMS (cite: 2005JMoSt.742..215M; 2016JMoSp.327...95E).

Table notes: $^{*}$The lines are blends of multiple hyper-fine components. Here, we show the properties of the strongest transition and the flux is the total of the blended lines. The $J=7_{8}-6_{7}$ line includes the F=17/2-15/2, F=15/2-13/2, F=11/2-9/2 and F=11/2-9/2 hyper-fine components and the $J=9_{8}-8_{7}$ line includes the F=21/2-19/2, F=19/2-17/2, F=17/2-15/2 and F=15/2-13/2 hyper-fine components.

isotope ratios we recover when assuming our fiducial temperature of 60 K or a temperature above this. Additionally, the / ratio is approximately constant with temperature and is always 40-50% above the V-CDT value.

The isotope ratios varies less with temperature, since the upper energy levels of the and lines are similar. In contrast to our findings for SO, the column density appears to be enhanced at all temperatures when measured from the and at 60 K the /=5. From a rotation diagram analysis, Temmink et al. in prep. show that emission is optically thin, but, because the observations are spatially and kinematically unresolved, the optical depth is likely underestimated. Therefore, the inferred / ratio from may only be a lower limit.

# Discussion

The currently observed volatile sulfur reservoir in the Oph-IRS 48 disk is primarily in the form of SO. This is different to most Class II disks where generally CS is the most common S-species detected (cite: 2019ApJ...876...72L; 2021ApJS..257...12L). CS is detected in the Oph-IRS 48 disk, but its column density is $\approx$1000$\times$ lower than for SO; therefore, CS makes a negligible contribution to the total S abundance (cite: Booth2023_irs48). In Figure [3](#fig:fig3), we show the contributions from , S, OCS, SO and to the currently total observed volatile sulfur reservoirs in the low-mass embedded Class 0 protostar IRAS 16293-2442 B, the more evolved Class II disk Oph-IRS 48, the comet 67P/C-G and the shocked region L1157-B1 (cite: 2016MNRAS.462S.253C; 2018MNRAS.476.4949D; 2019ApJ...878...64H; 2023A&A...672A.122K; Booth2023_irs48).

The differences in sulfur reservoirs between IRAS 16293-2442 B and 67P/C-G are discussed in detail in (cite: 2018MNRAS.476.4949D), who suggest that UV-irradiation during the star formation process converted to OCS. OCS is not detected in Oph-IRS 48 down to $<$1% of the SO column density and this is unexpected, as discussed in (cite: Booth2023_irs48), due to the other signatures of ice sublimation in this disk. Interestingly, the /OCS ratio we see in Oph-IRS 48 is also significantly higher than that measured for the outbursting source V883 Ori, where ice sublimation is also occurring (cite: 2024AJ....167...66Y). Oph-IRS 48 is a young Herbig Ae star and therefore the volatiles, in the gas and ice phases, will be subjected to UV-irradiation, which could chemically transform the primary S-reservoir in the disk. It is also possible that in the Oph-IRS 48 disk there are shocks liberating a more refractory form of sulfur, e.g., , that when released from the grains goes on to form SO (and ) efficiently in the gas phase (as discussed in (cite: 2024MNRAS.528..388K)). Indeed, the bulk of the S in disks is expected to be in refractory form (cite: 2019ApJ...885..114K). The high SO/ ratio in Oph-IRS 48 is also most closely a match with that in the shocked region L1157-B1, but the CS/SO ratio is orders of magnitude higher in the shocked region when compared to the Oph-IRS 48 disk (cite: 2019ApJ...878...64H). Observations of the shock tracer SiO (and SiS, (cite: 2023ApJ...952L..19L)) and key sulfur species will help unravel the distinctions between the volatile reservoir in the Oph-IRS 48 disk and that in other environments.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Molecule |  | $\mathrm{N_{peak}}$ \[$\mathrm{cm^{-2}}$\] |  |  |
|  | $\mathrm{T_{ex}}$: 30 K | **60 K** | 100 K |  |
|  | 2.7$\pm0.2\times10^{15}$ | 3.6$\pm0.3\times10^{15}$ | 5.1$\pm0.41\times10^{15}$ |  |
|  | 2.0$\pm0.2\times10^{14}$ | 1.0$\pm0.1\times10^{14}$ | 1.0$\pm0.09\times10^{14}$ |  |
|  | 2.2$\pm0.4\times10^{13}$ | 1.2$\pm0.2\times10^{13}$ | 1.3$\pm0.25\times10^{13}$ |  |
|  | 1.5$\pm0.4\times10^{13}$ | 0.7$\pm0.2\times10^{13}$ | 0.7$\pm0.17\times10^{13}$ |  |
|  | 6.9$\pm0.4\times10^{14}$ | 6.7$\pm0.5\times10^{14}$ | 9.6$\pm0.69\times10^{14}$ |  |
|  | 0.9$\pm0.1\times10^{14}$ | 1.3$\pm0.1\times10^{14}$ | 2.1$\pm0.21\times10^{14}$ |  |
| Ratio | $\mathrm{T_{ex}}$: 30 K | textbf60 K | 100 K | V-CDT |
| / | $13\pm1$ | $34\pm4.0$ | $50\pm6.0$ | 22.64 |
| / | $7.5\pm0.9$ | $5.2\pm0.6$ | $4.6\pm0.6$ | 22.64 |
| / | $120\pm25$ | $290\pm60$ | $410\pm90$ | 126.9 |
| / | $>180$ | $>$500 | $>$760 | 498.7 |
| Deviation from V-CDT | $\mathrm{T_{ex}}$: 30 K | textbf60 K | 100 K |  |
| $\delta$ | 690$^{+160}_{-200}$ | -340$^{+90}_{-70}$ | -550$^{+60}_{-50}$ |  |
| $\delta$ | 2016$^{+410}_{-320}$ | 3350$^{+250}_{-170}$ | 3920$^{+740}_{-570}$ |  |
| $\delta$ | 23$^{+250}_{-170}$ | -559$^{+120}_{-80}$ | -690$^{+80}_{-60}$ |  |
| $\delta$ | $<$1820 | $<$5 | $<$-340 |  |

![](IRS48_isotope_ratios_figure.png)

![](IRS48_sulphur_reservior_figure.png)

Given the differences in molecular reservoirs of S we may expect differences in the isotopic ratios on volatile sulfur in the Oph-IRS48 disk. To place our isotopic ratios in context, in Figure [2](#fig:fig2), we show a comparison of the isotope ratios measured in comets to Class II disks for a variety of simple species. The ratios we measure do vary as a function of the assumed gas temperature (as shown in Figures [2](#fig:fig2) and [5](#fig:fig4)). If the gas is cool ($<$50 K), the and ratios for SO are within range 1-2$\sigma$ range of the V-CDT values. This would mean there are no significant isotopic differences between the Oph-IRS 48 disk and the solar system and, that volatile S is not severely fractionated during the planet formation timescale. Similarly, at 30 K we would tentatively recover the enhancement as seen in 67P/C-G but further data are needed to verify this.

The rotational temperature of in this disk has been well constrained to be 60 K (Temmink et al. in prep.) therefore, we discuss the case where the SO gas is also warm, as also supported by astrochemical models (cite: 2018A&A...617A..28S; 2024MNRAS.528..388K). At temperatures of 60 K and above the isotope ratios for sulfur are anomalous when compared to the V-CDT and cometary values. This possible observed depletion of and traced in SO is currently not traced in any cometary volatiles and in particular, not in the measured in 67P/C-G (cite: 2020MNRAS.498.5855A). This depletion is also not traced in the refractory dust of 67P/C-G nor the dust collected in the STARDUST mission (cite: 2012M&PS...47..649H; 2017MNRAS.469S.230P). For the other few disks with robust measurements of / from CS, these values are consistent with the expected isotope ratio of 22 (cite: 2021A&A...653L...5P; Booth2023_hd100546). In the broader context of meteorite samples, our $\delta^{34}$S and $\delta^{33}$S values, calculated at 60 K, lie at the most depleted end of the distribution of isotopic ratios measured in SiC grains from the meteorites Murchison and Indarch (cite: 2017MNRAS.469S.787C). The apparent factor $\approx$4 enhancement of in is an extreme outlier in all cases, but this may be due to beam diluted and optically thick emission. This low ratio in is similar to that measured in SO for Class 0/I sources in Perseus (cite: 2023A&A...678A.124A) where this can be attributed to optically thick emission from the main isotopologue.

Finally, when considering the lower limit of the isotope ratio in SO at $\gtrsim$60 K find a difference to the volatiles in 67P/C-G. The enhanced in SO, and OCS in 67P/C-G and, the high HDS/ (of $\approx10^{-3}$) indicate the possible pre-solar formation of these molecules in the cold dark cloud stage (cite: 2017RSPTA.37560253A). In comparison, for warm gas, in the Oph-IRS 48 disk our upper-limit does not indicate any oxygen isotope fractionation, similar to the findings from (cite: 2022ApJ...926..148F) for / in TW Hya. The nominal ratio of $\approx$500 is also the same as that measured for the 67P/C-G cometary dust particles (cite: 2018MNRAS.477.3836P).

The observations of Oph-IRS 48 show the possibility of isotopically distinct sulfur reservoirs in planet forming disks with an isotopic fractionation distinct to that of 67P/C-G. The depletion of heavier isotopes and lack of enhancement would also suggest that low temperature isotope exchange reactions are not responsible as these would have the opposite effect. If the optically thin nature of holds, the different isotopic signatures in SO and mean that they may not share a common formation path via and ice sublimation (cite: 2018A&A...617A..28S; 2021A&A...651L...6B). If SO and both form from photodissociated , they would be expected to have the same isotopic ratios. The isotope selective photo-dissociation of has been proposed as a mechanism for the enrichment of heavy isotopes in some chondritic meteorites, but if this were the case in Oph-IRS 48, we would expect both the SO and to be enriched in the heavier isotopes, if they indeed formed from (cite: 2013PNAS..11017650C; 2017GeCoA.196..326L; 2021GeCoA.309..135V). If there are shocks in the Oph-IRS 48 disk, the injection of refractory S into the gas phase could pollute the isotopic ratios set by photo-processes. Future observations of Oph-IRS 48 to detect and measure its isotopic ratios will be necessary to determine if SO and/or are daughter molecules forming from . Additionally, observations of multiple optically thin lines of SO and its isotopologues will enable an independent temperature measurement for the SO rather than assuming the same temperature as .

# Conclusion

We have presented the first measurements of the combined and isotope ratios relative to in a planet-forming disk. Additionally, we share the an upper-limit on the column density and the inferred lower-limit on the / ratio. The observed isotopic fractionation of the S reservoir in the Oph-IRS 48 disk is potentially distinct from that measured in comets for both the elements sulfur and oxygen but, this relies heavily on the adopted gas temperature. Assuming a kinetic temperature of 60 K (as measured for ) or above, both and are depleted relative to their Solar System standard values when traced in SO. At cooler temperatures, the isotope ratios are consistent with the cometary values indicating the need for additional data to better and independently constrain the SO gas temperature. Interestingly, at all temperatures the / ratio traced in SO is enhanced. We also identify a tentative enhancement in the heavier isotopologue which requires observations of optically thinner transitions to confirm.

There are also possible limitations in the current data due to dust optical depth that will require longer wavelength observations to assess. It may be that the isotopologues are tracing gas deeper in the disk, below the optically thick dust surface, resulting in an underestimated column density measurement, as seen towards protostars (cite: 2020ApJ...896L...3D). Furthermore, follow-up observations with ALMA to detect (and its isotopologues) will help to complete the observable volatile inventory of S in this disk. Knowing if is depleted or enhanced in the heavier isotopes will aid significantly in understanding the isotopic fractionation mechanisms at play. More generally, future high-sensitivity line surveys of populations of protoplanetary disks will be able to target multiple isotopologues of S and other volatile elements, which can be used to connect the dots between the initial and final stages of planetary system formation.

# Acknowledgements

This paper makes use of the following ALMA data: 2017.1.00834.S, 2021.1.00738.S. We acknowledge assistance from Allegro, the European ALMA Regional Centre node in the Netherlands. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This work has used the following additional software packages that have not been referred to in the main text: Astropy, IPython, Jupyter, Matplotlib and NumPy (cite: Astropy; IPython; Jupyter; Matplotlib; NumPy). Astrochemistry in Leiden is supported by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK). A.S.B. is supported by a Clay Postdoctoral Fellowship from the Smithsonian Astrophysical Observatory. M.N.D. acknowledges the Holcim Foundation Stipend. M.T. acknowledges support from the ERC grant 101019751 MOLDISK. Support for C.J.L. was provided by NASA through the NASA Hubble Fellowship grant No. HST-HF2-51535.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. M.L. is funded by the European Union (ERC, UNVEIL, 101076613). Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council. Neither the European Union nor the granting authority can be held responsible for them. S.N. is grateful for support from RIKEN Special Postdoctoral Researcher Program (Fellowships), Grants-in-Aid for JSPS (Japan Society for the Promotion of Science) Fellows Grant Number JP23KJ0329, and MEXT/JSPS Grants-in-Aid for Scientific Research (KAKENHI) Grant Numbers JP 18H05441, JP20K22376, JP20H05845, JP20H05847, JP23K13155, and JP24K00674. C.W. acknowledges financial support from the University of Leeds, the Science and Technology Facilities Council, and UK Research and Innovation (grant numbers ST/X001016/1 and MR/T040726/1).

natexlab

(ref: 2018ApJ...855..119A) Aikawa, Y., Furuya, K., Hincelin, U., & Herbst, E. 2018, ApJ, 855, 119, doi: [`10.3847/1538-4357/aaad6c`](http://doi.org/10.3847/1538-4357/aaad6c)

(ref: 2022arXiv221214529A) Aikawa, Y., Okuzumi, S., & Pontoppidan, K. 2022, arXiv e-prints, arXiv:2212.14529, doi: [`10.48550/arXiv.2212.14529`](http://doi.org/10.48550/arXiv.2212.14529)

(ref: 2017RSPTA.37560253A) Altwegg, K., Balsiger, H., Berthelier, J. J., et al. 2017, Philosophical Transactions of the Royal Society of London Series A, 375, 20160253, doi: [`10.1098/rsta.2016.0253`](http://doi.org/10.1098/rsta.2016.0253)

(ref: 2020MNRAS.498.5855A) Altwegg, K., Balsiger, H., Combi, M., et al. 2020, MNRAS, 498, 5855, doi: [`10.1093/mnras/staa2701`](http://doi.org/10.1093/mnras/staa2701)

(ref: 2023A&A...678A.124A) Artur de la Villarmois, E., Guzmán, V. V., Yang, Y. L., Zhang, Y., & Sakai, N. 2023, A&A, 678, A124, doi: [`10.1051/0004-6361/202346728`](http://doi.org/10.1051/0004-6361/202346728)

(ref: Astropy) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: 2016A&A...589A..78B) Biver, N., Moreno, R., Bockelée-Morvan, D., et al. 2016, A&A, 589, A78, doi: [`10.1051/0004-6361/201528041`](http://doi.org/10.1051/0004-6361/201528041)

(ref: Booth2023_hd100546) Booth, A., Leemker, M., & et al. 2023a, submitted AJ

(ref: Booth2023_irs48) Booth, A., Temmink, M., & et al. 2024, A&A

(ref: 2023A&A...678A.146B) Booth, A. S., Law, C. J., Temmink, M., Leemker, M., & Macı́as, E. 2023b, A&A, 678, A146, doi: [`10.1051/0004-6361/202346974`](http://doi.org/10.1051/0004-6361/202346974)

(ref: 2021A&A...651L...6B) Booth, A. S., van der Marel, N., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L6, doi: [`10.1051/0004-6361/202141057`](http://doi.org/10.1051/0004-6361/202141057)

(ref: 2012ApJ...744..116B) Brown, J. M., Herczeg, G. J., Pontoppidan, K. M., & van Dishoeck, E. F. 2012, ApJ, 744, 116, doi: [`10.1088/0004-637X/744/2/116`](http://doi.org/10.1088/0004-637X/744/2/116)

(ref: 2022A&A...659A..29B) Brunken, N. G. C., Booth, A. S., Leemker, M., et al. 2022, A&A, 659, A29, doi: [`10.1051/0004-6361/202142981`](http://doi.org/10.1051/0004-6361/202142981)

(ref: 2016MNRAS.462S.253C) Calmonte, U., Altwegg, K., Balsiger, H., et al. 2016, MNRAS, 462, S253, doi: [`10.1093/mnras/stw2601`](http://doi.org/10.1093/mnras/stw2601)

(ref: 2017MNRAS.469S.787C) —. 2017, MNRAS, 469, S787, doi: [`10.1093/mnras/stx2534`](http://doi.org/10.1093/mnras/stx2534)

(ref: 2015PhDT.......418C) Calmonte, U. M. 2015, PhD thesis, University of Bern, Switzerland

(ref: 2021ApJS..257...10C) Cataldi, G., Yamato, Y., Aikawa, Y., et al. 2021, ApJS, 257, 10, doi: [`10.3847/1538-4365/ac143d`](http://doi.org/10.3847/1538-4365/ac143d)

(ref: 2013PNAS..11017650C) Chakraborty, S., Jackson, T. L., Ahmed, M., & Thiemens, M. H. 2013, Proceedings of the National Academy of Science, 110, 17650, doi: [`10.1073/pnas.1213150110`](http://doi.org/10.1073/pnas.1213150110)

(ref: 2004A&A...418.1141C) Crovisier, J., Bockelée-Morvan, D., Colom, P., et al. 2004, A&A, 418, 1141, doi: [`10.1051/0004-6361:20035688`](http://doi.org/10.1051/0004-6361:20035688)

(ref: 2020ApJ...896L...3D) De Simone, M., Ceccarelli, C., Codella, C., et al. 2020, ApJL, 896, L3, doi: [`10.3847/2041-8213/ab8d41`](http://doi.org/10.3847/2041-8213/ab8d41)

(ref: 2001GeCoA..65.2433D) Ding, T., Valkiers, S., Kipphardt, H., et al. 2001, , 65, 2433, doi: [`10.1016/S0016-7037(01)00611-1`](http://doi.org/10.1016/S0016-7037(01)00611-1)

(ref: 2018MNRAS.476.4949D) Drozdovskaya, M. N., van Dishoeck, E. F., Jørgensen, J. K., et al. 2018, MNRAS, 476, 4949, doi: [`10.1093/mnras/sty462`](http://doi.org/10.1093/mnras/sty462)

(ref: 2016JMoSp.327...95E) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: 2015ApJ...802L..23F) Favre, C., Bergin, E. A., Cleeves, L. I., et al. 2015, ApJL, 802, L23, doi: [`10.1088/2041-8205/802/2/L23`](http://doi.org/10.1088/2041-8205/802/2/L23)

(ref: 2022ApJ...926..148F) Furuya, K., Tsukagoshi, T., Qi, C., et al. 2022, ApJ, 926, 148, doi: [`10.3847/1538-4357/ac45ff`](http://doi.org/10.3847/1538-4357/ac45ff)

(ref: Gaia2018) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1, doi: [`10.1051/0004-6361/201833051`](http://doi.org/10.1051/0004-6361/201833051)

(ref: 2017ApJ...836...30G) Guzmán, V. V., Öberg, K. I., Huang, J., Loomis, R., & Qi, C. 2017, ApJ, 836, 30, doi: [`10.3847/1538-4357/836/1/30`](http://doi.org/10.3847/1538-4357/836/1/30)

(ref: NumPy) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: 2014A&A...562A..61H) Heays, A. N., Visser, R., Gredel, R., et al. 2014, A&A, 562, A61, doi: [`10.1051/0004-6361/201322832`](http://doi.org/10.1051/0004-6361/201322832)

(ref: 2012M&PS...47..649H) Heck, P. R., Hoppe, P., & Huth, J. 2012, , 47, 649, doi: [`10.1111/j.1945-5100.2012.01362.x`](http://doi.org/10.1111/j.1945-5100.2012.01362.x)

(ref: 2017A&A...603L...6H) Hily-Blant, P., Magalhaes, V., Kastner, J., et al. 2017, A&A, 603, L6, doi: [`10.1051/0004-6361/201730524`](http://doi.org/10.1051/0004-6361/201730524)

(ref: 2019A&A...632L..12H) Hily-Blant, P., Magalhaes de Souza, V., Kastner, J., & Forveille, T. 2019, A&A, 632, L12, doi: [`10.1051/0004-6361/201936750`](http://doi.org/10.1051/0004-6361/201936750)

(ref: 2019ApJ...878...64H) Holdship, J., Jimenez-Serra, I., Viti, S., et al. 2019, ApJ, 878, 64, doi: [`10.3847/1538-4357/ab1cb5`](http://doi.org/10.3847/1538-4357/ab1cb5)

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 1997Sci...278...90J) Jewitt, D., Matthews, H. E., Owen, T., & Meier, R. 1997, Science, 278, 90, doi: [`10.1126/science.278.5335.90`](http://doi.org/10.1126/science.278.5335.90)

(ref: 2019ApJ...885..114K) Kama, M., Shorttle, O., Jermyn, A. S., et al. 2019, ApJ, 885, 114, doi: [`10.3847/1538-4357/ab45f8`](http://doi.org/10.3847/1538-4357/ab45f8)

(ref: 2024MNRAS.528..388K) Keyte, L., Kama, M., Chuang, K.-J., et al. 2024, MNRAS, 528, 388, doi: [`10.1093/mnras/stae019`](http://doi.org/10.1093/mnras/stae019)

(ref: 1996JMoSp.180..197K) Klaus, T., Saleck, A. H., Belov, S. P., et al. 1996, Journal of Molecular Spectroscopy, 180, 197, doi: [`10.1006/jmsp.1996.0243`](http://doi.org/10.1006/jmsp.1996.0243)

(ref: Jupyter) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, in Positioning and Power in Academic Publishing: Players, Agents and Agendas, ed. F. Loizides & B. Schmidt, IOS Press, 87 – 90

(ref: 2023A&A...672A.122K) Kushwahaa, T., Drozdovskaya, M. N., Tychoniec, Ł., & Tabone, B. 2023, A&A, 672, A122, doi: [`10.1051/0004-6361/202245097`](http://doi.org/10.1051/0004-6361/202245097)

(ref: 2017GeCoA.196..326L) Labidi, J., Farquhar, J., Alexander, C. M. O. D., Eldridge, D. L., & Oduro, H. 2017, , 196, 326, doi: [`10.1016/j.gca.2016.09.036`](http://doi.org/10.1016/j.gca.2016.09.036)

(ref: 2023ApJ...952L..19L) Law, C. J., Booth, A. S., & Öberg, K. I. 2023, ApJL, 952, L19, doi: [`10.3847/2041-8213/acdfd0`](http://doi.org/10.3847/2041-8213/acdfd0)

(ref: 2019ApJ...876...72L) Le Gal, R., Öberg, K. I., Loomis, R. A., Pegues, J., & Bergner, J. B. 2019, ApJ, 876, 72, doi: [`10.3847/1538-4357/ab1416`](http://doi.org/10.3847/1538-4357/ab1416)

(ref: 2021ApJS..257...12L) Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJS, 257, 12, doi: [`10.3847/1538-4365/ac2583`](http://doi.org/10.3847/1538-4365/ac2583)

(ref: 2023A&A...673A...7L) Leemker, M., Booth, A. S., van Dishoeck, E. F., et al. 2023, A&A, 673, A7, doi: [`10.1051/0004-6361/202245662`](http://doi.org/10.1051/0004-6361/202245662)

(ref: 2018ApJ...859..131L) Loomis, R. A., Cleeves, L. I., Öberg, K. I., et al. 2018, ApJ, 859, 131, doi: [`10.3847/1538-4357/aac169`](http://doi.org/10.3847/1538-4357/aac169)

(ref: 2020ApJ...893..101L) Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2020, ApJ, 893, 101, doi: [`10.3847/1538-4357/ab7cc8`](http://doi.org/10.3847/1538-4357/ab7cc8)

(ref: 1985JPCRD..14..395L) Lovas, F. J. 1985, Journal of Physical and Chemical Reference Data, 14, 395, doi: [`10.1063/1.555729`](http://doi.org/10.1063/1.555729)

(ref: 1992ApJ...399..325L) Lovas, F. J., Suenram, R. D., Ogata, T., & Yamamoto, S. 1992, ApJ, 399, 325, doi: [`10.1086/171928`](http://doi.org/10.1086/171928)

(ref: 2012E&PSL.313...56M) Marty, B. 2012, Earth and Planetary Science Letters, 313, 56, doi: [`10.1016/j.epsl.2011.10.040`](http://doi.org/10.1016/j.epsl.2011.10.040)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2023ApJ...943...35M) Muñoz-Romero, C. E., Öberg, K. I., Law, C. J., et al. 2023, ApJ, 943, 35, doi: [`10.3847/1538-4357/aca765`](http://doi.org/10.3847/1538-4357/aca765)

(ref: 2005JMoSt.742..215M) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215, doi: [`10.1016/j.molstruc.2005.01.027`](http://doi.org/10.1016/j.molstruc.2005.01.027)

(ref: 2001A&A...370L..49M) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49, doi: [`10.1051/0004-6361:20010367`](http://doi.org/10.1051/0004-6361:20010367)

(ref: 2023ASPC..534.1075N) Nomura, H., Furuya, K., Cordiner, M. A., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 1075

(ref: 2021PhR...893....1O) Öberg, K. I., & Bergin, E. A. 2021, Phys. Rep., 893, 1, doi: [`10.1016/j.physrep.2020.09.004`](http://doi.org/10.1016/j.physrep.2020.09.004)

(ref: 2023ARA&A..61..287O) Öberg, K. I., Facchini, S., & Anderson, D. E. 2023, ARA&A, 61, 287, doi: [`10.1146/annurev-astro-022823-040820`](http://doi.org/10.1146/annurev-astro-022823-040820)

(ref: 2020ApJ...900...81O) Ohashi, S., Kataoka, A., van der Marel, N., et al. 2020, ApJ, 900, 81, doi: [`10.3847/1538-4357/abaab4`](http://doi.org/10.3847/1538-4357/abaab4)

(ref: 2018MNRAS.477.3836P) Paquette, J. A., Engrand, C., Hilchenbach, M., et al. 2018, MNRAS, 477, 3836, doi: [`10.1093/mnras/sty560`](http://doi.org/10.1093/mnras/sty560)

(ref: 2017MNRAS.469S.230P) Paquette, J. A., Hornung, K., Stenzel, O. J., et al. 2017, MNRAS, 469, S230, doi: [`10.1093/mnras/stx1623`](http://doi.org/10.1093/mnras/stx1623)

(ref: IPython) Pérez, F., & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: 2021arXiv211006010P) Perrero, J., Rimola, A., Corno, M., & Ugliengo, P. 2021, arXiv e-prints, arXiv:2110.06010, doi: [`10.48550/arXiv.2110.06010`](http://doi.org/10.48550/arXiv.2110.06010)

(ref: 2021A&A...653L...5P) Phuong, N. T., Dutrey, A., Chapillon, E., et al. 2021, A&A, 653, L5, doi: [`10.1051/0004-6361/202141881`](http://doi.org/10.1051/0004-6361/202141881)

(ref: 2018A&A...617A..28S) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28, doi: [`10.1051/0004-6361/201832980`](http://doi.org/10.1051/0004-6361/201832980)

(ref: rich_teague_2020_4321137) Teague, R. 2020, richteague/keplerian_mask: Initial Release, 1.0, Zenodo, doi: [`10.5281/zenodo.4321137`](http://doi.org/10.5281/zenodo.4321137)

(ref: 2021GeCoA.309..135V) Vacher, L. G., Ogliore, R. C., Jones, C., Liu, N., & Fike, D. A. 2021, , 309, 135, doi: [`10.1016/j.gca.2021.06.026`](http://doi.org/10.1016/j.gca.2021.06.026)

(ref: 2021A&A...651L...5V) van der Marel, N., Booth, A. S., Leemker, M., van Dishoeck, E. F., & Ohashi, S. 2021, A&A, 651, L5, doi: [`10.1051/0004-6361/202141051`](http://doi.org/10.1051/0004-6361/202141051)

(ref: 2018A&A...615A..75V) Visser, R., Bruderer, S., Cazzoletti, P., et al. 2018, A&A, 615, A75, doi: [`10.1051/0004-6361/201731898`](http://doi.org/10.1051/0004-6361/201731898)

(ref: 2001RCMS...15..501W) Werner, R. A., & Brand, W. A. 2001, Rapid Communications in Mass Spectrometry, 15, 501, doi: [`10.1002/rcm.258`](http://doi.org/10.1002/rcm.258)

(ref: 1994ARA&A..32..191W) Wilson, T. L., & Rood, R. 1994, ARA&A, 32, 191, doi: [`10.1146/annurev.aa.32.090194.001203`](http://doi.org/10.1146/annurev.aa.32.090194.001203)

(ref: 2024AJ....167...66Y) Yamato, Y., Notsu, S., Aikawa, Y., et al. 2024, AJ, 167, 66, doi: [`10.3847/1538-3881/ad11d9`](http://doi.org/10.3847/1538-3881/ad11d9)

#  channel maps

The channel maps generated over the frequency range of the $J=9_9-8_8$ transition are shown in Figure [4](#fig:channels).

![](irs48_s18o_channelmaps.png)

# Isotope ratios as a function of temperature

The isotope ratios of /, /, / and / measured from SO and as a function of the assumed excitation temperature are shown in Figure [5](#fig:fig4).

![](IRS48_peak_ratios.png)

</paper>

Write the methods card for this paper.