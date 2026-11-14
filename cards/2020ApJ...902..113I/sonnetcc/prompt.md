# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020ApJ...902..113I\sonnetcc\reply.txt

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
 "bibcode": "2020ApJ...902..113I",
 "title": "The ALMA Spectroscopic Survey in the Hubble Ultra Deep Field: Constraining the Molecular Content at log(M<SUB>*</SUB>/M<SUB>☉</SUB>) ∼ 9.5 with CO Stacking of MUSE-detected z ∼ 1.5 Galaxies",
 "year": 2020,
 "journal": "The Astrophysical Journal",
 "first_author": "Inami, Hanae",
 "n_authors": 22,
 "arxiv_id": "2009.10843",
 "doi": "10.3847/1538-4357/abba2f",
 "alma_projects_linked_by_archive": [
  "2016.1.00324.L"
 ]
}
```

Paper text:
<paper>
# The ALMA Spectroscopic Survey in the HUDF: Constraining the Molecular Content at $\log{(M_*/M_\odot)} \sim 9.5$ with CO stacking of MUSE detected $z\sim1.5$ Galaxies

## Abstract

We report molecular gas mass estimates obtained from a stacking analysis of CO line emission in the ALMA Spectroscopic Survey (ASPECS) using the spectroscopic redshifts from the optical integral field spectroscopic survey by the Multi Unit Spectroscopic Explorer (MUSE) of the *Hubble* Ultra Deep Field (HUDF). Stacking was performed on subsets of the sample of galaxies classified by their stellar mass and position relative to the main-sequence relation (on, above, below). Among all the CO emission lines, from CO(2-1) to CO(6-5), with redshifts accessible via the ASPECS Band 3 and the MUSE data, CO(2-1) provides the strongest constraints on the molecular gas content. We detect CO(2-1) emission in galaxies down to stellar masses of $\log{(M_*/M_\odot)}=10.0$. Below this stellar mass, we present a new constraint on the molecular gas content of $z\sim1.5$ main-sequence galaxies by stacking based on the MUSE detections. We find that the molecular gas mass of main-sequence galaxies continuously decreases with stellar mass down to $\log{(M_*/M_\odot)}\approx9.0$. Assuming a metallicity-based CO–to–$\rm H_2$ conversion factor, the molecular gas-to-stellar mass ratio from $\log{(M_*/M_\odot)}\sim9.0$ to $\sim10.0$ does not seem to decrease as fast as for $\log{(M_*/M_\odot)}>10.0$, which is in line with simulations and studies at lower redshift. The inferred molecular gas density $\rho{\rm (H_2)}=(0.49\pm0.09)\times10^8\,{\rm
    M_\odot\,Mpc^{-3}}$ of MUSE-selected galaxies at $z\sim1.5$ is comparable with the one derived in the HUDF with a different CO selection. Using the MUSE data we recover most of the CO emission in our deep ALMA observations through stacking, demonstrating the synergy between volumetric surveys obtained at different wavebands.

# Introduction

Stars form inside dense molecular gas clouds. It is thus critical to reveal how much molecular gas exists in galaxies to characterize galaxy formation and evolution (cite: Kenn12; Cari13b; Tacc20; Hodg20). It is well established that the cosmic star formation rate density increased from the early stages of the Universe towards its peak around $z \sim 1-3$, after which it progressively decreased until the current epoch (cite: Mada14). A broad consensus is emerging on the cause of this growth, peak, and decline of the star formation history over cosmic time via measurements of the gas that fuels star formation (cite: Walt14; Deca16a; Scov17b; Deca19; Riec19; Liu19; Magn20; Lenk20; Tacc20). This evolution could be due to either the available supply of molecular gas for forming stars, a mechanism that causes high efficiency in star formation such as galaxy mergers, or a combination of these processes.

Most of the star formation in the Universe occurs in galaxies residing on the so-called “main sequence”, a tight correlation between the star formation rate (SFR) and stellar mass ($M_*$) of star-forming galaxies (cite: Noes07; Salm12; Whit12; Whit14; Schr15; Pope19a; Pope19b). This correlation is observed at redshifts up to at least $z\sim6.5$ (cite: Spea14; Salm15). In other words, most star formation in the Universe is long-lasting and evolves steadily, supporting the idea that it is predominantly regulated by the gas accretion of the available fuel supply and feedback processes, rather than stochastic events like galaxy mergers (cite: Lill13; Deke13; Tacch16). Such stochastic events cause enhanced star formation activity, which elevates SFRs significantly above the main-sequence relation. However, these galaxies, referred to as starbursts are in the minority (cite: Rodi11; Sarg12; Lutz14). To understand these two star formation modes and the efficiency of the star formation process, it is essential to determine the $\rm H_2$ gas supply and deficiency. The most common tracer of the molecular gas, the fuel of star formation, is line emission from carbon monoxide ($^{12}{\rm CO}$) rotational transitions at low excitation (cite: Bola13b; Cari13b).

The connection between molecular gas content, stellar mass, and SFR for $z > 1$ galaxies on and above the main-sequence relation has been investigated in various targeted studies (cite: Magd12b; Sant14; Scov16; Tacc13; Tacc18). However, the targets have so far been limited to massive ($> 10^{10} \, M_\odot$) and highly star-forming ($\gtrsim 50 M_\odot \, {\rm yr^{-1}}$) galaxies. Little is known about the molecular gas reservoirs in galaxies either below the main sequence or at modest stellar masses, mostly because of sensitivity limits.

The ALMA Spectroscopic Survey in the *Hubble* Ultra-Deep Field (cite: Walt16) has been conducted as a spectroscopic survey over the entire frequency range of ALMA Bands 3 and 6 in the *Hubble* Ultra Deep Field (cite: Beck06) to perform an unbiased search for multiple rotational transitions of CO emission (cite: Walt16; Gonz19). Spectral line scans have an advantage in assessing the molecular gas content based on a complete line flux-limited sample without any target preselections. (cite: Gonz19) conducted a blind search of line and continuum sources directly in the ASPECS data cube (Band 3) and evaluated its completeness. Using these reliable CO detections, (cite: Deca19) constructed CO luminosity functions and presented the evolution of the cosmic gas mass density. A census of the molecular gas content of galaxies that have direct CO detections is shown and discussed in (cite: Arav19). These gas measurements were compared with model predictions from cosmological simulations and semi-analytical models in (cite: Popp19). (cite: Uzgi19) performed a power spectrum analysis and probed CO emission at $1 \lesssim z \lesssim 4$ below the sensitivity limit of individual detections and gave a constraint on missing CO emission from individually undetected galaxies.

Here, we maximize the sensitivity of the ASPECS data to detect CO emission by stacking ALMA spectra using the Band 3 data. Our stacking analysis is based on optical spectroscopic redshifts from another large, unbiased, blind spectroscopic survey in the HUDF carried out by the integral field unit (IFU) instrument MUSE (Multi Unit Spectroscopic Explorer) on the Very Large Telescope (cite: Baco17). The combination of the three-dimensional (3D) data obtained by both the ASPECS and MUSE surveys not only made the stacking analysis possible, but also enabled a direct comparison between the molecular gas properties and rest-frame optical/ultraviolet properties (cite: Boog19).

This paper is structured as follows: we first introduce the observations and data taken with the ASPECS and MUSE HUDF surveys and the ancillary data in §[2](#sec:sample). We describe the method of the stacking analysis along with the sample used for stacking in §[3](#sec:method). In §[4](#sec:results), the stacked CO spectra are presented. We then convert the measured CO emission to molecular gas mass and discuss the gas mass content in §[5](#sec:discussion). We summarize and conclude our findings in §[6](#sec:summary). A flat $\Lambda$CDM cosmology with $H_0 = 70 \, {\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_\Lambda = 0.7$, and $\Omega_m = 0.3$ is adopted throughout this paper.

# The ASPECS and MUSE Datasets

The MUSE survey covered the entire area of the HUDF (cite: Baco17), whereas the ASPECS LP observed almost the entire region of the *Hubble* eXtremely Deep Field (cite: Illi13). MUSE is an optical IFU (cite: Baco15) on the Very Large Telescope (VLT) Yepun (UT4) of the European Southern Observatory (ESO) with a wide field-of-view (FoV, $1\ensuremath{'} \times 1\ensuremath{'}$), high sensitivity, wide wavelength coverage ($4650-9300\,{\rm \AA}$), and high spectral resolution ($R\sim3000$). In particular, the large size of its FoV facilitates spectroscopic redshift surveys without requiring any target preselection, achieving a spatially homogeneous spectroscopic completeness. It offers redshift determination at $z=0-6.5$ based on rest-frame ultraviolet and optical emission and absorption lines.

Complementing the MUSE spectroscopic survey, the ASPECS line scan survey in ALMA Band 3 (3mm) can detect multiple CO rotational transition lines from $J=1-0$ to $J=6-5$ in the redshift range of $z=0-7$ (cite: Walt16). The MUSE redshift coverage overlaps well with the redshift coverage of the ASPECS Band 3 line scan survey at $z > 1$ (Figure [1](#fig:MUSE_ASPECS)), except for a small gap at $z=1.74-2.00$.

![](muse_aspecs_z_cov_b3.png)

In this paper, we concentrate on the ASPECS Band 3 data where the full MUSE redshift coverage can be exploited (see §[3.2](#subsec:subsamples)). The significant redshift overlap of these two unbiased spectroscopic surveys in the same field is beneficial for performing stacking analyses on ASPECS CO spectral lines based on the optically determined MUSE redshifts. In this section, we will briefly present the survey designs of the HUDF conducted by ASPECS and MUSE.

## ASPECS observations and data

The detailed survey strategy and data reduction of the ASPECS Pilot and Large Program surveys are presented in (cite: Walt16) and (cite: Gonz19), respectively. The observational setups of the Large Program (LP) survey were the same as the Pilot survey, except its coverage is extended to $\sim 5 \, {\rm arcmin}^2$. In this work, we used the combined data of the ASPECS Pilot and LP surveys taken with ALMA Band 3. ASPECS LP carried out a full frequency scan in Band 3 ($84-115$ GHz) over the XDF, which resides in the HUDF. With a total of 17 pointings centered at (RA, Dec) $=$ (03:32:38.5, -27:47:00), which completely cover the Pilot region, the total area with a primary beam response $>50\%$ in the LP survey is $4.6\,{\rm arcmin}^2$ at $\approx 99.5\,{\rm GHz}$ (the central frequency of Band 3).

The CASA (Common Astronomy Software Applications) software was used to calibrate and image the data. With the C40-3 array configuration, we obtained a synthesized beam size of $1.75\ensuremath{''} \times 1.49\ensuremath{''}$ with a position angle $91.5\deg$ at $\approx 99.5\,{\rm GHz}$ by using natural weighting in CASA when imaging the data. The frequency channel was rebinned to 7.813 MHz ($23.5\,{\rm km\,s^{-1}}$ at 99.5 GHz). The sensitivity for this channel bin size was $\sim 0.2\,{\rm mJy\,beam^{-1}}$ throughout the entire scanned frequency range. The $5\sigma$ CO(2-1) line sensitivity is $> 1.4 \times 10^9 \, {\rm K\,km\,s^{-1}\,pc^2}$ assuming a line width of $200\,{\rm km\,s^{-1}}$. Based on assumptions made in this work (see §[5.1](#subsec:gas_mass)), the corresponding molecular gas ($\rm H_2$) limit is $\ensuremath{\gtrsim} 6.8 \times 10^9 \, M_\odot$. For our main target emission line, CO(2-1), the ALMA Band 3 scan offers redshift coverage of $z=1.0059-1.7387$.

Using the same data cube, (cite: Gonz19) reported CO emission line detections from an unbiased blind search without prior knowledge of source positions and observed CO frequencies. They found 16 high significance CO emitting sources, among which 11 were identified as CO(2-1) emission. We refer the readers to (cite: Gonz19) for comprehensive discussions on the detection methods. (cite: Arav19) assessed the molecular gas properties of these sources, which will be used for comparison in this paper.

## MUSE observations and data

The MUSE-HUDF deep survey was conducted as a two layer survey of different depths (cite: Baco17). The $3\ensuremath{'} \times 3\ensuremath{'}$ deep survey observed the entire HUDF region, whereas the $1\ensuremath{'} \times 1\ensuremath{'}$ ultra deep survey was carried out near the center of the deep survey area. The $\approx 10$ h and $\approx 31$ h exposure times, respectively, reached $3\sigma$ emission line flux limits of $3.1$ and $1.5 \times 10^{-19} \, {\rm erg\,s^{-1}\,cm^{-2}}$ at $\sim 7000\,{\rm \AA}$.

The MUSE spectra were extracted with two methods: prior extractions based on the UVUDF catalog (cite: Rafe15) and a blind search for emission lines in the data cubes. In the former case, the coordinates for the source extraction were from UVUDF [^1], whereas for the latter, the coordinates were determined from the MUSE data. For a more detailed description of the survey and data treatments, see (cite: Baco17). Following (cite: Dunl17), we corrected the known systematic offset of the *Hubble* Space Telescope (*HST*) positions to match the radio astrometric reference frame by applying $+0.279\ensuremath{''}$ in Declination (Dec) and $-0.076\ensuremath{''}$ in Right Ascension (R.A.).

The MUSE spectroscopic redshifts were measured from the spectral features in the extracted spectra. Each redshift has an associated confidence level of 3 (secure redshift, determined by multiple spectral lines), 2 (secure redshift, determined by a single spectral line), or 1 (possible redshift, determined by a single spectral line whose spectral identification remains uncertain). The typical MUSE redshift uncertainty is $\sigma_z = 0.00012(1+z)$ or $\sigma_v \approx 40 \, {\rm km \, s^{-1}}$, which is smaller than the typical line width of CO emission. We refer to (cite: Inam17) for details about the redshift determination and redshift catalogs of the MUSE-HUDF field. In this work, we only use the reliable MUSE redshifts of confidence levels 2 and 3.

The MUSE-HUDF survey obtained 1338 reliable redshifts in total, a factor of eight increase over the previously available spectroscopic redshifts in this field. The simultaneous wavelength coverage of $4650-9300\,{\rm \AA}$ and the spectral resolution of $R\sim3000$ of MUSE allowed detections and unambiguous identifications of major rest-frame ultraviolet and optical emission lines, including H$\alpha$, \[O II\], \[O III\], and Ly$\alpha$. These lines were used to determine redshifts over the range $0 < z <
6.5$. Although more difficult to probe, the redshift range $z \sim 1.5-3$ can be covered by C III\] and absorption features (cite: Inam17).

Among the spectroscopic redshifts assessed in the MUSE HUDF field, 503 sources with a confidence level of 2 or higher lie within the ASPECS survey region (LP primary beam response $> 50\%$). Out of these sources, 107 sources are \[O II\] emitters covering $z=0.25-1.5$ and 363 sources are Ly$\alpha$ emitters covering $z=2.8-6.6$. For the analysis presented in the main part of this paper, we took advantage of the prevalent \[O II\] line detections and their redshift overlap with the CO(2-1) selection function in ALMA Band 3 (Figure [1](#fig:MUSE_ASPECS)) to perform a stacking analysis. In the redshift range where CO(2-1) can be detected, the MUSE spectroscopic redshift sources with absorption features and C III\] emission also contributed to the stacking, although the number was small (Figure [1](#fig:MUSE_ASPECS)). We also attempted to stack spectra to detect higher-$J$ CO lines. The MUSE redshifts used in higher-$J$ CO stacked spectra were mostly measured using the Ly$\alpha$ line, which is known to be offset from the systemic redshift for a few hundred $\rm km\,s^{-1}$ (cite: Shap03). We have applied a correction to this offset (§[4.2](#subsec:results_hiJ)).

## Ancillary data and physical parameters derived from SED fitting

Owing to the same HUDF coverage of the MUSE and ASPECS observations, there are abundant ancillary data available. We assembled optical and near-infrared photometric data from (cite: Skel14). These photometry catalogs and data include ultraviolet to infrared from the *HST*, various ground-based telescopes, and all of the *Spitzer* IRAC channels.

Based on this photometric dataset, we inferred physical parameters such as star formation rate (SFR) and stellar mass ($M_*$) via modeling with the high redshift extension of the Spectral Energy Distribution (SED) fitting code `MAGPHYS` (cite: daCu08; daCu15). In addition to *Spitzer*/MIPS and *Herschel*/PACS, the ALMA 1.2 and 3 mm photometry from the ASPECS data (cite: Gonz19; Gonz20) were also used for the SED fitting for a subset of the sources whose CO or continuum emission was detected. The same procedure was carried out in the other ASPECS work (cite: Arav20; Boog20). The SED fits were computed based on the MUSE spectroscopic redshift. See (cite: Boog19) for the detailed process of the SED fitting.

# Methods

## ALMA spectral extraction and stacking

From the ALMA data, we first extracted a sub-cube centered at the position of each MUSE source with a secure spectroscopic redshift. This sub-cube has a size of $11\ensuremath{''} \times 11\ensuremath{''} \times 3000\,{\rm
  km\,s^{-1}}$. The primary beam correction using the combined Pilot and LP primary beam response was applied after the sub-cube extraction.

The uncertainty of the extracted spectra was calculated based on the region in the data cube where the combined beam response is $> 99\%$ of the peak sensitivity at the phase center. The uncertainty for each spectrum is then scaled by the combined primary beam response of the location of the objects under consideration.

To perform stacking, the channel frequencies of the extracted spectra were converted to the rest-frame, then the spectra were resampled onto a common frequency grid. In the rest-frame, a CO line detected at the lower frequency end of the spectrum (i.e., galaxies at higher redshift) has a coarser spectral sampling due to the $(1+z)$ correction of the redshift. Thus, the common frequency grid was given at the coarsest sampling, corresponding to the CO line detected at the lowest frequency end of Band 3. In the case of CO(2-1), we set the final spectral range and the channel width of the extracted spectra to be $3000\, {\rm km\,s^{-1}}$, centered on the CO(2-1) rest-frame frequency ($230.538\,$GHz), and $27.8 \, {\rm km\,s^{-1}}$ ($21.4 \, {\rm MHz}$), respectively. This resulted in 108 channels in the extracted spectra. The final extracted rest-frame frequency range is $229.395 - 231.682\,$GHz ($\pm 1500 \, {\rm km\,s^{-1}}$). The same procedure is adopted for stacking high-$J$ CO lines.

This conversion was implemented by first shifting the channel frequencies of the spectra to the rest-frame, according to the MUSE redshift. We then applied a Gaussian decimation filter to the rest-frame spectra via the Fourier plane. This filter removes fine scale (high sampling frequency) noise in the spectrum which would otherwise be aliased into spurious noise when sub-sampled to the lower target resolution (cite: Lyons11). A better signal-to-noise ratio (SNR) was thus obtained when we binned all spectra onto the coarser common frequency grid in the later step. In the Fourier plane, the width of the Gaussian filter was set to give an attenuation of 40 dB at the Nyquist folding frequency of half a cycle per channel of the new channel width (0.5 cycles per $27.8 \, {\rm km\,s^{-1}}$). This value is a reasonable compromise between the desirable suppression of aliased noise and the corresponding (minor) reduction in the resolution of the sub-sampled spectra. The Gaussian kernel was scaled to be unity at the origin of the Fourier plane to guarantee flux conservation. In addition, the kernel was given an odd number of elements, placed symmetrically around the origin, to prevent spectral shifts during the convolution. The effect of this filter was equivalent to performing a linear convolution of the spectrum with an area-normalized Gaussian of FWHM $63.2\,{\rm km\,s^{-1}}$.

Next, we interpolated the filtered spectrum onto the frequency grid of the stacked spectra. The mean of the resulting spectra was then calculated to obtain the final stacked spectrum  [^2]. We did not apply any weighting when performing the stack.

We also carried out two different random extractions following the same procedure described above, to produce random stacked spectra for comparisons. One random extraction involved assigning random redshifts to each spectrum before combining them at the location of the known MUSE position. The other involved using the correct MUSE redshifts, but extracting the spectra at random positions within the region where the LP primary beam response is $> 50\%$, instead of at the known source position. The number of randomized extractions is the same as the number of CO emission samples. Neither of these methods should produce stacked spectra with real features. This random spectral extraction highlights which features in the real stacked spectra should be discounted as noise.

In Figure [2](#fig:stack_rms), we show the standard deviation of randomly stacked spectra against the number of the stacks. For this plot, we randomize both redshift and position for the spectral extractions. The standard deviation of stacked spectra roughly decreases with $1/\sqrt{N}$.

![](muse_z_aspecs_rand_CO2-1_rms_vs_N.pdf)

## Sample selection

We took advantage of the significant redshift overlap between the ASPECS and MUSE surveys to carry out a stacking analysis on CO line emission: we focused on the ASPECS Band 3 data where the full MUSE redshift coverage can be exploited. In particular, over the range $1.0059 \leq z \leq 1.7387$, the ASPECS survey has the highest sensitivity for detecting CO(2-1) among all of the observable CO emission features (cite: Boog19). In addition, this redshift range is where MUSE is efficient at detecting spectral features (up to $z\sim1.5$ for \[O II\]) as shown in Figure [1](#fig:MUSE_ASPECS).

We first selected a subset of the MUSE sources for stacking CO(2-1) emission in the ASPECS Band 3 data cube. The criteria were the following: (1) $1.0059 \leq {\rm MUSE \ spec-}z \leq 1.7387$, (2) MUSE spec$-z$ confidence levels $\geq 2$, and (3) location within ALMA Band 3 LP primary beam response $\geq 50\%$. For high-$J$ CO emission, we used the same selection criteria, except for the redshift range. The ranges were $z=2.0088-3.1080$ for CO(3-2), $z=3.0115-4.4771$ for CO(4-3) $z=4.0142-5.8460$ for CO(5-4) $z=5.0166-7.2146$ for CO(6-5).

The resulting number of MUSE sources for stacking CO(2-1) was 111 in total [^3]. For 104 sources, the MUSE spectroscopic redshift identifications were based on \[O II\], five sources used absorption features, one source used C III\], and one quasar had strong Mg II emission.

Among these 111 sources, 10 sources [^4] were identified with CO(2-1) emission by the ASPECS blind search: MUSE IDs 8 (ASPECS-LP-3mm.06), 16 (3mm.11), 924 (3mm.14), 925 (3mm.16), 996 (3mm.02), 1001 (3mm.05), 1011 (3mm.10), 1117 (3mm.04), 6415 (3mm.08), and 6870 (3mm.15) (cite: Boog19; Arav19).

We performed the stacking in each group of the sample galaxies classified by the stellar mass and specific SFR ($SSFR=SFR/M_*$) derived from the MAGPHYS SED fits (see §[2.3](#subsec:sed)). The $SFR-M_*$ relation of our sample is shown in Figure [3](#fig:SFR-M). The SSFR classification was based on the main-sequence (MS) relation from Eq.11 of (cite: Boog18), using the mean redshift of the CO(2-1) line detectable in Band 3 (cite: Walt16). Galaxies lying within, above, and below the intrinsic scatter (0.44 dex [^5]) of this relation are referred to as the “MS”, “above” the MS, and “below” the MS, respectively, throughout this paper. We here use the main-sequence relation from (cite: Boog18) because their $SFR-M_*$ correlation is assessed with the objects whose spectral features and redshifts were measured based on the MUSE data. Compared with earlier studies such as (cite: Whit14) and (cite: Schr15) whose samples are mostly massive galaxies, (cite: Boog18) better constrained the low-mass end of the relation. The numbers of galaxies in each group for stacking are presented in Table [\[tbl:bins\]](#tbl:bins).

The main-sequence relation of (cite: Boog18) was also adopted for classifying galaxies which expected to have CO $J>2$ lines. Similar to CO(2-1), we used the mean redshifts of $z=2.61$, $3.80$, $4.99$, and $6.18$ for CO(3-2), CO(4-3), CO(5-4), and CO(6-5) lines, respectively (cite: Walt16).

![](muse_z_aspecs_CO2-1_ssfr.pdf)

## CO line flux and upper limit measurements

For each stacked spectrum, we performed a best fit on the 2D image (moment-0) with a 2D Gaussian function to estimate the line flux or upper limit. The x- and y-positions are allowed to vary in the vicinity of the MUSE positions within a radius of $1/3$ of the ALMA beam size. The widths were fixed to the beam size. We considered a CO emission line to have been detected when the amplitude of the fitted Gaussian function was higher than $3\sigma$ of the local fluctuations in the 2D image. The line flux was estimated by integrating the fitted Gaussian function. When the CO line was not detected, the standard deviation in the central area of the image was used to evaluate the $3\sigma$ upper limit, assuming a point source.

Uncertainties in MUSE redshifts can cause some flux losses when we stack spectra. We assumed an emission line with a width of $300\,{\rm km\,s^{-1}}$ (full width at half maximum, FWHM) and performed a bootstrap simulation to assess the flux loss resulting from $\sigma_z = 0.00012(1+z)$ (§[2.2](#subsec:muse)). The total flux was measured within $\Delta v = 528\,{\rm km\,s^{-1}}$ (corresponding to 19 slices in frequency; see §[4.1.1](#subsubsec:co21_all) for this choice of $\Delta v$) centered at the rest-frequency of CO(2-1). This velocity range was the same as the one we used to create coadded 2D images for flux measurements (see §[4](#sec:results)). With 10000 realizations, we found that 92% of them resulted in less than 3% flux loss. We do not scale up our measured fluxes in this work to take account of this flux loss, because its impact on our line flux measurements is not significant.

# CO emission from stacked spectra

We performed CO emission line stacking from CO(2-1) to CO(6-5). In this section, we will present the resulting stacked spectra.

## CO(2-1)

### Stacking the entire sample

We first performed stacking without binning in stellar mass or SSFR to obtain a constraint on the average properties of all galaxies. The entire sample (111 spectra) and a subset of the sample (101 spectra) that excluded 10 objects whose CO emission were detected by the blind search (§[3.2](#subsec:subsamples)) were used to search for signals in the stacks (below the noise threshold of individual galaxies).

For these two sets of samples, we inspected 2D images (moment-0) that were coadded between $230.335 \leq \nu_{\rm rest}/{\rm GHz} \leq 230.741$ ($\Delta v = 528\,{\rm km\,s^{-1}}$) centered at the CO(2-1) rest frequency ($230.538\,{\rm GHz}$) in the corresponding 1D spectrum. This width is consistent with $2\sigma$ of the mean line width of the ASPECS blind CO detections (cite: Arav19) to recover 95% of the emission.

The total line fluxes were obtained by fitting a 2D Gaussian function in the 2D images. This measure helps to avoid problems such as a possible slight positional offset between the optical and CO emission. All of the Gaussian parameters, the peak position, and amplitude were set to be free parameters, whereas the widths were fixed to the mean beam size. We obtained total line fluxes (upper limit) of $0.031 \pm 0.007 \, {\rm Jy\,km\,s^{-1}}$ ($<0.012\, {\rm Jy\,km\,s^{-1}}$) for the stacked spectra including (excluding) the sources with direct CO(2-1) detections.

### Stacking in stellar mass and SSFR bins

We carried out the stacking on both the entire sample and the sample that excluded the direct CO detections. To investigate the dependence of the molecular gas content on fundamental properties of galaxies, we divided the sample into ranges of stellar mass and SSFR to perform the stacking. As shown in Figure [3](#fig:SFR-M), we set the bins to have steps of $\log{(M_*/M_\odot)} = 1.0$ over the range $8.0 < \log{(M_*/M_\odot)} \leq 12.0$ (4 bins) with stellar mass, and galaxies “above” the MS, on the “MS”, and “below” the MS based on the main-sequence relation at $z = 1.43$ discussed in §[3.2](#subsec:subsamples). In the redshift range where CO(2-1) can be detected with the ASPECS Band 3 survey ($z=1.0-1.7$), the main-sequence relation does not evolve significantly.

The stacked 2D and 1D spectra are shown in Figure [4](#fig:M8-12_2D1Dstack) and the CO line flux measurements are summarized in Table [\[tbl:lineflux\]](#tbl:lineflux). When the directly detected CO(2-1) emission is included, there are solid detections ($>3\sigma$) at $\log{(M_*/M_\odot)} > 10.0$, regardless of their SSFRs (except in the $10.0 < \log{(M_*/M_\odot)} \leq 11.0$ bin where there is only a single source). On the other hand, at $\log{(M_*/M_\odot)} \leq 10.0$, we only obtain a signal in the bin above the MS with $9.0 < \log{(M_*/M_\odot)} \leq 10.0$. When we exclude the known CO(2-1) emission from the stacks, a significant detection is seen in the MS bin with $10.0 < \log{(M_*/M_\odot)} \leq 11.0$ (seven sources)  [^6].

Although the bins of the MS galaxies in the ranges of $8.0 < \log{(M_*/M_\odot)} \leq 9.0$ and $9.0 < \log{(M_*/M_\odot)} \leq 10.0$ contain the largest numbers of galaxies, we do not detect a CO(2-1) line. To attempt to detect stacked CO emission for galaxies in these low mass bins, we adopt a $\Delta \log{(M_*/M_\odot)}=0.5$ stellar mass bin size in case some hidden emission from a small number of sources has been diluted by averaging too many sources without any emission. This smaller bin size results in 14, 24, 23, and 9 MS sources from $8.0 < \log{(M_*/M_\odot)} \leq 8.5$ to $9.5 < \log{(M_*/M_\odot)} \leq 10.0$ in steps of $\log{(M_*/M_\odot)} = 0.5$. No detection is identified even with these finer bins. The estimated $3\sigma$ upper limits with the 2D data are $0.028$, $0.024$, and $0.017$, $0.030 \, {\rm Jy\,km\,s^{-1}}$, from lower to higher stellar mass bins, respectively.

Among the bins with stacked detections, although the censoring fraction is unity for the bin of below the MS with stellar mass $10.0 < \log{(M_*/M_\odot)} \leq 11$, all of the remaining bins are $\leq 0.75$. In particular, the fraction is $\leq 0.6$ for the MS galaxies.

\[width=,trim=0 0 0 35,clip\] muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO.png

\[width=,trim=0 0 0 95,clip\] muse_z_aspecs_1d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO.png

\[width=,trim=0 0 0 35,clip\] muse_z_aspecs_2d_CO2-1_pb0.5_confid2_NoKnownCO_WithPotentialCO.png

\[width=,trim=0 0 0 95,clip\] muse_z_aspecs_1d_CO2-1_pb0.5_confid2_NoKnownCO_WithPotentialCO.png

### The CO(2-1) lines detected in individual galaxies

We inspect individual spectra of galaxies in the MS bin of $10 < \log{(M_*/M_\odot)} \leq 11$, where the stacked spectrum has the highest SNR (the spectra are depicted in Appendix [7](#app:indiv)). Excluding the emission already found by the blind search, it is possible to identify the CO(2-1) line with lower SNR in MUSE IDs 879, 985, and 1308. We note that MUSE IDs 879 and 985 have already been reported by (cite: Boog19) as the MUSE prior-based sample (see their Table 2 and Figure 4). A further potential stacked CO(2-1) detection is seen in the range of $10.0 < \log{(M_*/M_\odot)} \leq 11.0$ for the mean of two galaxies lying below the MS. A detected CO(2-1) line is dominated by MUSE ID 928.

## Higher-$J$ CO stacked spectra

Along with the CO(2-1) stacking analysis, we attempt to detect higher excitation CO emission, up to $J=6-5$, with the same stacking method. The census of the stacked sources is shown in Table [\[tbl:hi_j\]](#tbl:hi_j).

For CO(3-2), among our sample selection (§[3.2](#subsec:subsamples)), MUSE IDs 35 and 1124 [^7] are the only sources that were already known from the blind search (ASPECS-LP-3mm.01 and 3mm.12). The former is a galaxy above the MS and the latter is on the MS with $\log{(M_*/M_\odot)} = 10.39$ and 10.64, respectively. In addition, we consider MUSE ID 35’s pair galaxy MUSE ID 24 ($\log{(M_*/M_\odot)} = 9.45$) to have a CO(3-2) detection in our analysis. This is because the CO spatial extent, which peaks at the location of ID 35, covers ID 24 and it is difficult to distinguish the flux contributions from these two sources. When the stacking was performed in the same way as for CO(2-1), these two sources dominated the detections in their bins (Appendix [8](#app:hi_j)). If we discard them, no significant emission remains. This result agrees with the finding of (cite: Uzgi19) who also did not find additional CO(3-2) emission with a masked auto-power spectrum using all MUSE positions with LP primary beam response $\geq 20\%$. There is also no stack detection for $J_{\rm up} \ge 4$ CO emission in our sample with the blind search [^8], nor the stacking.

We note that the MUSE spectroscopic redshifts of galaxies at $z \gtrsim 3$, which allow detections of $J_{\rm up} > 4$ CO emission, were mostly determined using the Ly$\alpha$ line. Its redshift was measured using the peak emission, which can have a few hundred $\rm km\,s^{-1}$ offset from the systemic redshift (cite: Shap03). When the redshifts of the stacked sources were measured with Ly$\alpha$, we tried to recover their systemic redshifts based on an empirical correlation between the Ly$\alpha$ emission peak and the Ly$\alpha$ line width (cite: Verh18). The intrinsic scatter of the relation is $\pm 73\,{\rm km\,s^{-1}}$ measured with 13 sources that have both Ly$\alpha$ and C III\] detections. We do not find any detection for $J_{\rm up} > 4$ CO emission either. This is likely either due to dilution of the stacked signal, owing to uncertainties in the velocity offset, or to Ly$\alpha$ emitters on average having smaller SFRs and molecular gas content.

We also visually investigate individual CO spectra with the MUSE redshifts as priors to search for possible CO emission which is washed out by stacking. Two potential CO(5-4) emission lines were identified as shown in Figure [10](#fig:CO5-4) in Appendix [9](#app:CO5-4). If confirmed, they may be one of the first cases of high-$J$ CO detection at $z > 4.5$ for Ly$\alpha$ emitters. Deeper observations are needed to confirm these detections.

# Discussion

In this section, we will concentrate on discussing the molecular gas content at $z\sim1.5$, as we have obtained the most reliable measurements at this redshift with our analysis.

## CO Luminosities and Molecular ($\rm H_2$) Gas Masses

We employed the following equation to obtain the CO luminosities from the measured CO(2-1) emission (cite: Solo97; Solo05):

$$\begin{equation}
\frac{L^{\rm \prime}_{\rm COJ-[J-1]}}{{\rm K\,km\,s^{-1}\,pc^2}} = 
3.25 \times 10^7 \, 
\frac{F_{\rm line}}{\rm Jy\,km\,s^{-1}} \,
\frac{D_L^2}{(1+z)^3 \nu_{\rm obs}^2}
\end{equation}$$

where $F_{\rm line}$ is the integrated line flux density, $D_L$ is the luminosity distance in Mpc, and $\nu_{\rm obs}$ is the observed frequency in GHz. For the redshift ($z$), we used the mean redshift of the galaxies in each stacking bin.

We then adopted the following equation and the same conditions as (cite: Deca16b) to infer molecular gas masses ($M_\odot$) from the line luminosities (${\rm K\,km\,s^{-1}\,pc^2}$):

$$\begin{equation}
  M_{\rm gas} = 
  \frac{\alpha_{\rm CO}}{r_{J1}}\, L^{\rm \prime}_{\rm COJ-[J-1]}
\end{equation}$$

where $J$ is the upper level of the CO excitation and $\alpha_{\rm CO}$ is the CO luminosity to gas mass conversion factor. We assume $r_{21}=0.76 \pm 0.09$ following (cite: Dadd15). Based on galaxies detected with the ASPECS survey, (cite: Boog20) estimated $r_{21}=0.75 \pm 0.11$, which is comparable to the value from (cite: Dadd15). Here we adopt the value from the former to be consistent with the molecular mass measurements published in (cite: Arav19), which are used for comparison in this paper. For $\alpha_{\rm CO}$, we used $3.6 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ for galaxies in the stellar mass bins of $\log{(M_*/M_\odot)} > 10$ which is one of the best estimates for high-redshift main-sequence star-forming galaxies (cite: Dadd10b). Among the ASPECS directly detected CO sources with metallicity estimates available from the MUSE spectra, all have roughly solar metallicity (cite: Boog19), which further justifies our choice of $\alpha_{\rm CO}$ (cite: Arav19). For the galaxies with $\log{(M_*/M_\odot)} \le 10.0$, because they are likely to have lower metallicity, $\alpha_{\rm CO}$ could be higher (cite: Bola13b). In this work, we assume that the metallicities of galaxies with $\log{(M_*/M_\odot)} \sim 9.5$ and $\sim 8.5$ are $\sim 2/3Z_\odot$ and $\sim 1/2Z_\odot$ (cite: Sava05; Erb06; Mann09; Zahi11; Sarg14; Sand20). Thus, $\alpha_{\rm CO}$ would increase by a factor of $\sim 2$ and $\sim 3$, respectively, compared to galaxies with $\log{(M_*/M_\odot)} > 10.0$ (cite: Genz12; Schr12). We adopt $\alpha_{\rm CO} = 7.2$ and $10.8 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ for galaxies with $\log{(M_*/M_\odot)} \sim 9.5$ and $\log{(M_*/M_\odot)} \sim 8.5$, respectively. In these lower stellar mass bins, the $M_{\rm gas}$ estimates with a constant $\alpha_{\rm CO} = 3.6 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ are also shown as dotted symbols in figures for reference. The calculated line luminosities and molecular gas masses from CO(2-1) are summarized in Table [\[tbl:linelum\]](#tbl:linelum).

In the following subsections, we discuss the gas content of galaxies at $z\sim1.5$, together with their stellar masses and SFRs derived from the SED fitting (§[2.3](#subsec:sed)). The CO(2-1) emission used here stems from the measurements based on the 2D Gaussian fits in the images presented in §[4.1.2](#subsec:M*-SSFR) and Figure [4](#fig:M8-12_2D1Dstack). Because we are interested in global properties of the molecular gas, we use the measurements that include the direct CO(2-1) detections from the blind search.

## Molecular gas and stellar mass scaling relation of MS galaxies

Previous observational and theoretical studies of molecular gas in high redshift galaxies have established a set of scaling relations that relate the molecular gas content to galaxy properties such as stellar masses, SFRs, source sizes (cite: Tacc13; Tacc18; Freu19; Arav19; Genz15; Magd12b; Sant14; Scov16; Some12; Dave17; Popp19). These relations have been key to understanding how the galaxy growth process has taken place through cosmic time. We first compare average molecular gas properties to the stellar mass of distant galaxies.

In conjunction with the MUSE deep survey in the same field, the stacking analysis facilitates the exploration of the gas scaling relations below stellar masses of $\log{(M_*/M_\odot)} = 10$, a regime that is rather uncharted in CO emission for individual detections at $z > 1$ (see also Appendix [10](#app:Spea14)). We focus on discussing the main-sequence galaxies, which have the largest numbers of stacked spectra in our CO(2-1) sample.

![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Mgas_vs_Mstar_MS_B18-MSonly}.pdf) ![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Fgas_vs_Mstar_MS_B18-MSonly}.pdf)

In Figure [5](#fig:Mgas) (left), we plot the molecular gas mass from the stacking analysis against stellar mass of the main-sequence galaxies, along with individual ASPECS CO detections (cite: Gonz19; Arav19). The majority of directly detected galaxies have $\log{(M_*/M_\odot)} > 10$. At $\log{(M_*/M_\odot)} \leq 10$, there is only one direct detection. Although stacking also leads to no detection, the stacks of 38 and 32 spectra provide tight constraints on the average gas mass in the range of $8 < \log{(M_*/M_\odot)} \leq 10$ at $z \sim 1.5$. Taking upper limits into account, an increase of gas mass is found with increasing stellar mass from at least $\log{(M_*/M_\odot)} \sim 9.0$ to $12.0$.

For comparison, we also show the contours of the molecular gas measurements from the PHIBSS2 survey (cite: Tacc13; Tacc18; Freu19). For further comparison with the literature, we show the distributions of the PHIBSS2 galaxies at lower redshifts in Appendix [10](#app:Spea14). The gas masses of the PHIBSS2 sources were derived via a metallicity-based prescription for this parameter (cite: Genz12), resulting in $\alpha_{\rm CO} \sim 4-7 \, M_\odot \, ({\rm
  K\,km\,s^{-1}\,pc^2})^{-1}$ at $z\sim1.5$.

We also compare our measurements with cosmological galaxy formation model calculations of molecular gas mass presented in (cite: Popp19). In the same diagram we show three different model predictions: the IllustrisTNG hydrodynamical simulations with the “3.5arcsec” and “Grav” apertures and the Santa Cruz semi-analytic model (SC SAM). The former corresponds to all the $\rm H_2$ within a radius of $3.5\ensuremath{''}$ of the source center (similar to ASPECS) and the latter corresponds to all the $\rm H_2$ gravitationally bound to the galaxy. The $\rm H_2$ properties of galaxies were derived based on the molecular hydrogen fraction recipe of (cite: Gned11) [^9].

We use the gas mass model predictions at $z=1.43$ (cite: Popp19), which is the mean redshift of the CO(2-1) line detectable in Band 3. At the higher stellar mass end, all of the three models predicted lower gas mass than the observed gas mass. At $\log{(M_*/M_\odot)} \sim 10.5$, about half of the sources with ASPECS direct detections lie within the $2\sigma$ scatter of the predictions. At $\log{(M_*/M_\odot)} \lesssim 10.0$, where the predicted gas mass is below the ASPECS detection limit, the only CO constraint is from stacking. The upper limit at $\log{(M_*/M_\odot)} \sim 9.5$ derived from the stacking is consistent with the models. This result also implies that at least a factor of 10 increase in the sample size is needed to confirm or rule out the model predictions.

## Molecular gas-to-stellar mass ratio of MS galaxies as a function of stellar mass

We depict this plot with a different presentation in Figure [5](#fig:Mgas) (right) to show a more common presentation of molecular gas mass normalized by the stellar mass (molecular gas-to-stellar mass ratio, $\mu_{\rm gas} \equiv M_{\rm gas}/M_*$) as a function of stellar mass. In the literature, a decrease of the gas-to-stellar mass ratio with increasing stellar mass at $\log{(M_*/M_\odot)} > 10.5$ has been reported at $z \sim 1.5$ (cite: Tacc13). However, no observational CO constraints exist at lower stellar masses below $10^{10}\,M_\odot$. Our stacking analysis facilitates exploration of this lower stellar mass regime.

For galaxies with $\log{(M_*/M_\odot)} \sim 10.5$ and $11.5$, we estimate $\mu_{\rm gas} =$ $0.49 \pm 0.08$ and $0.24 \pm 0.02$, respectively. Similarly to Figure [5](#fig:Mgas) (left), these values are in agreement with the measurements of the PHIBSS2 galaxies lying on the MS relation of (cite: Boog18) (cite: Spea14). In the lower stellar mass bin, $\log{(M_*/M_\odot)} \sim 9.5$, we constrain $\mu_{\rm gas}$ to have a $3\sigma$ upper limit of $<1.25$ with $\alpha_{\rm CO}=7.2 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ (or $< 0.63$ if $\alpha_{\rm CO} = 3.6 \, M_\odot \, ({\rm
  K\,km\,s^{-1}\,pc^2})^{-1}$).

Beyond $\log{(M_*/M_\odot)} \sim 10.5$, a *decrease* of the gas-to-stellar mass ratio is discerned with increasing stellar mass in our stack results, as well as in previous work reporting both CO-based and dust-based gas estimates (cite: Magd12b; Tacc13; Tacc18; Genz15; Scov17b; Arav19; Liu19). As an example, we show in Figure [5](#fig:Mgas) the result from PHIBSS2 with a steady decrease of $\mu_{\rm gas}$ with an increase of stellar mass (black line).

This decline of $\mu_{\rm gas}$ does not seem to be as steep at $\log{(M_*/M_\odot)} < 10.0$. If a constant $\alpha_{\rm CO}$ is also adopted for these lower mass bins, the gas-to-stellar mass ratio is consistent with being constant from $\log{(M_*/M_\odot)} \sim 9.5$ to $10.5$, then turning down around $\log{(M_*/M_\odot)} \sim 10.5$. We note that the models from (cite: Popp19), despite a discrepancy with the observed results at the high mass side, show a similar constant gas-to-stellar mass ratio up to $\log{(M_*/M_\odot)} \sim 10.5$. This is consistent with our finding if we assume a constant conversion factor.

Given the limitations of our data, and the unknown dependence of the $\alpha_{\rm CO}$ conversion factor, we cannot determine at which stellar mass a possible downturn of the gas-to-stellar mass ratio occurs. We, however, note that such a “plateau” in the low stellar mass regime has also been identified for local galaxies with direct detections of CO emission: here $\mu_{\rm gas}$ stays constant from at least $\log{(M_*/M_\odot)} \sim 9.0$ and starts decreasing around $\log{(M_*/M_\odot)} \sim 10.5$ (cite: Sain17; Both14). A similar result is found in (cite: Tacc18) who compared local star-forming galaxies, where CO measurements for low mass galaxies are available (cite: Sain17), to distant galaxies after removing assumed redshift effects on their gas mass content (see also Appendix [10](#app:Spea14)).

The declining $\mu_{\rm gas}$ at the high stellar mass end can be attributed to stellar feedback (cite: Tacc13; Genz15; Dave11). In contrast, the flatter $\mu_{\rm gas}$ at $\log{(M_*/M_\odot)} \lesssim 10.5$ may imply that the effects of feedback are weaker. The drop in gas-to-stellar mass ratio seems to appear around $\log{(M_*/M_\odot)} \sim 10.5$, which is relevant to the characteristic stellar mass of star-forming galaxies (cite: Dunc14) where mass-quenching is becoming dominant (cite: Peng10).

Furthermore, the gas-to-stellar mass ratio below $\sim 1$ at $3\sigma$ of low stellar mass galaxies suggests that we may have retrieved most of the CO emission at $z \sim 1.5$. As shown in (cite: Deca19), CO luminosity functions derived from the ASPECS data are assumed to have a fixed faint-end slope, which is consistent with the faint-end slope of the stellar mass function of star-forming galaxies. Thus, the value of $\mu_{\rm gas} \lesssim 1$ indicates that the assumed faint-end slope of the CO luminosity function is at least consistent or could be flatter than that of the stellar mass function. If this is the case, most of the CO emission at $z \sim 1.5$ has been recovered (cite: Uzgi19).

The estimated molecular gas density $\rho{\rm (H_2)}$ at $z\sim1.5$, based on our CO(2-1) stacking measurements, is $(0.49 \pm 0.09) \times 10^8 \,{\rm M_\odot\,Mpc^{-3}}$. This value is lower than, but formally consistent with, the value derived in (cite: Deca19) with a different CO selection. The CO emission used in (cite: Deca19) included sources that did not enter the present analysis because the lack of a counterpart with high-quality MUSE redshift. Our total CO flux estimate from stacking is also in line with the result from the CO auto-power spectrum analysis using the MUSE positions (cite: Uzgi19).

## Dependence of the molecular gas content on SSFR

In the previous section we only considered main-sequence galaxies; in the remaining discussion, we will include galaxies above and below the main-sequence relation of (cite: Boog18) to discuss the dependence of molecular gas content on SSFR. Below, we keep the same assumed $\alpha_{\rm CO}$ conversion factors as above: 3.6, 7.2, and $10.8 \, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ for galaxies with $\log{(M_*/M_\odot)} > 10$, $\sim 9.5$, and $8.5$, respectively (§[5.1](#subsec:gas_mass)). We include the constraints using a constant $\alpha_{\rm CO}=3.6$ throughout the stellar mass bins in the figures for reference.

### Gas-to-stellar mass ratios

As shown earlier, the gas-to-stellar mass ratio ($\mu_{\rm gas}$) provides information on the supply and depletion of gas reservoirs in galaxies. We compare $\mu_{\rm gas}$ against SSFRs in the left panel of Figure [6](#fig:fgas-SSFR). We find that $\mu_{\rm gas}$ increases with increasing SSFRs, which is also seen in earlier studies of high-redshift galaxies, including the dust-based measurements of the molecular gas mass (cite: Tacc13; Tacc18; Genz15; Magd12b; Scov16; Liu19). With the stacking analysis, we show that this trend holds even for galaxies below the main-sequence at $z \sim 1.5$.

![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Fgas_vs_SSFR_ALL_B18}.pdf) ![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Fgas_vs_z_ALL_B18}.pdf)

In the right panel of Figure [6](#fig:fgas-SSFR), we show $\mu_{\rm gas}$ of stacked sources color-coded by different SSFRs to compare with their evolution (cite: Geac11; Magd12b). Because our data points are derived from the CO(2-1) line, all of them lie between $z=1.0-1.5$. A wide spread is related to the variations of $\mu_{\rm gas}$ across the main-sequence relation seen in the left panel (cite: Tacc18). The lower $\mu_{\rm gas}$ of low SSFR sources is also found by (cite: Spil18) who investigated galaxies lying below the MS with $\log{(M_{\rm gas}/M_\odot)} \sim 11$ at $z \sim 0.7$. The depletion times of our sample below the MS are on average comparable with Spilker et al.’s sample. Following the same assumption as (cite: Spil18), if these galaxies continuously consume the existing gas with the observed SFR, then the $\mu_{\rm gas}$ of the galaxies with $\log{(M_{\rm gas}/M_\odot)} \sim 10.5$ (11.5) would reduce to $1/10$ at $z \approx 0.5$ (0.2) and $1/100$ at $z \approx 0.1$ (0.0). Hence, by $z=0$ their $\mu_{\rm gas}$ would be comparable to those of passive galaxies at the current epoch.

### Gas depletion time

The gas depletion time, $t_{\rm depl} = M_{\rm gas}/SFR$, is another way of examining the gas content in galaxies. It estimates the time taken for the gas to be fully consumed at the current SFR without accounting for additional fueling. We show the gas depletion time as a function of SSFR in Figure [7](#fig:Tdepl-SSFR). Our results from the stacking analysis are in good agreement with previous studies. Both the stacked and directly detected sources show decreasing $t_{\rm depl}$ with increasing SSFR, except that the $9.0 < \log{(M_*/M_\odot)} \le 10.0$ bin above the MS shows an elevated $t_{\rm depl}$ value. The data points from these two sets of measurements occupy the same range in the diagram, following the constant gas-to-stellar mass ratio ($M_{\rm gas}/M_*$) from around 0.1 to 1.0. The decreasing gas depletion timescale with SSFR demonstrates that galaxies with more extreme star formation consume their gas at a higher rate. This may be the major cause of the scatter as shown in Figure [6](#fig:fgas-SSFR).

![]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Tdepl_vs_SSFR_ALL_B18}.pdf)

# Summary and Conclusions

Based on the accurate redshifts from the MUSE IFU survey in the Hubble Ultra Deep Field, we perform a CO emission stacking analysis with the ASPECS Band 3 data. When we split the sample into stellar mass and SSFR bins (on, below, and above the main-sequence relation), we detect CO(2-1) emission ($z\sim1.43$) down to $\log{(M_*/M_\odot)} = 10.0$, even after removing previously reported CO detections. We do not recover any higher-$J$ CO emission at higher redshift ($z \gtrsim 3$) with stacking when excluding the sources with direct CO detections.

The $3\sigma$ upper limits on CO(2-1) emission at $\log{(M_*/M_\odot)} < 10.0$ in the redshift range $1.0 < z < 1.7$ provide meaningful upper limits on molecular gas mass estimates of main-sequence star-forming galaxies in this stellar mass range, which has been poorly explored at $z \sim 1.5$. Under the assumption of a metallicity-based $\alpha_{\rm CO}$ conversion factor, we observe an increase in gas mass with increasing stellar mass from $\log{(M_*/M_\odot)} \sim 9.0$ to $11.0$. The upper limits at the low mass end are consistent with the model predictions, but to confirm or rule out these predictions, at least a factor of 10 increase in the sample size is needed. The gas-to-stellar mass ratio ($\mu_{\rm gas} \equiv M_{\rm gas}/M_*$) from $\log{(M_*/M_\odot)} \sim 9.0$ to $10.5$ declines at a slower rate compared with the known decrease of $\mu_{\rm gas}$ at higher stellar masses. If a fixed $\alpha_{\rm CO}=3.6 \, M_\odot \, ({\rm
      K\,km\,s^{-1}\,pc^2})^{-1}$ conversion factor is assumed across the stellar mass range explored here, $\mu_{\rm gas}$ is consistent with being constant from at least $\log{(M_*/M_\odot)} \sim 9.0$ to $10.5$, in agreement with predictions by models and observations at lower redshifts.

Furthermore, the gas-to-stellar mass ratios of $\sim 0.5$ and $\lesssim 1$ at the stellar masses of $\log{(M_*/M_\odot)} \sim 10.5$ and $\log{(M_*/M_\odot)} \sim 9.5$, respectively, imply that the faint end slope of the CO luminosity function is at least consistent or could be flatter than the stellar mass function. We have successfully recovered the majority of the CO emission at $z \sim 1.5$ with the stacking analysis. The molecular gas density $\rho{\rm (H_2)}=(0.49 \pm 0.09) \times 10^8 \,{\rm
  M_\odot\,Mpc^{-3}}$ from this stacking analysis is comparable with the one inferred from a CO-driven selection (cite: Deca19).

When we compare the gas-to-stellar mass ratio ($\mu_{\rm gas}$) against SSFR, we confirmed the known correlations to also hold for galaxies with low SSFRs at $z \sim 1.2$. The scatter in the $\mu_{\rm gas}-$SSFR correlation seems to be related to the decrease of $\mu_{\rm gas}$ at $\log{(M_*/M_\odot)} \gtrsim 10.5$ for star-forming galaxies. We also show that the gas-to-stellar mass ratios of massive galaxies ($\log{(M_*/M_\odot)} \sim 11$) below the MS at $z\sim1.2$ are comparable to those at $z \sim 0.7$ (cite: Spil18; Tacc18).

Our stacking analysis of the combined volumetric surveys of ALMA and MUSE has let us explore regimes that were uncharted before and that will remain challenging for investigations that rely on direct CO detections.

# Acknowledgments

The authors would like to thank the referee whose constructive comments helped improving the manuscript. The authors thank Ian Smail for useful suggestions to improve this study. This work was supported by JSPS KAKENHI Grant Number JP19K23462 (HI). Este trabajo cont ó con el apoyo de CONICYT + PCI + INSTITUTO MAX PLANCK DE ASTRONOMIA MPG190030. FW acknowledges support by ERC Advanced Grant 740246 (Cosmic Gas). T.D-S. acknowledges support from the CASSACA and CONICYT fund CAS-CONICYT Call 2018. D.R. acknowledges support from the National Science Foundation under grant numbers AST-1614213 and AST-1910107 and from the Alexander von Humboldt Foundation through a Humboldt Research Fellowship for Experienced Researchers. MK acknowledges support from the International Max Planck Research School for Astronomy and Cosmic Physics at Heidelberg University (IMPRS-HD). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

# Facilities

ALMA, VLT:Yepun

# Software

astropy (cite: AsPy13; AsPy18), CASA (cite: McMu07)

ccccc & 4c$\log{(M_*/M_\odot)}$\
& $8.0-9.0$ & $9.0-10.0$ & $10.0-11.0$ & $11.0-12.0$\
Above the MS & 11 (11) & 4 (3) & 1 (1) & 0 (0)\
On the MS & 38 (38) & 32 (32) & 12 (7) & 3 (0)\
Below the MS & 0 (0) & 5 (5) & 2 (2) & 3 (2)

Table notes: The numbers in parentheses are after excluding the galaxies which have the CO(2-1) line identified by the blind search (see §[3.2](#subsec:subsamples)).

rcccc & 4c$\log{(M_*/M_\odot)}$\
& $8.0-9.0$ & $9.0-10.0$ & $10.0-11.0$ & $11.0-12.0$\
Above the MS & $<0.032$($<0.032$) & $0.110 \pm 0.027$($<0.041$) & $<0.081$($<0.081$) & –(–)\
On the MS & $<0.022$($<0.022$) & $<0.019$($<0.019$) & $0.130 \pm 0.021$($0.095 \pm 0.024$) & $0.453 \pm 0.042$(–)\
Below the MS & –(–) & $<0.051$($<0.051$) & $0.119 \pm 0.039$($0.119 \pm 0.039$) & $0.152 \pm 0.027$($<0.054$)

Table notes: The units are in ${\rm Jy\,km\,s^{-1}}$. Values in parentheses are after excluding the galaxies which have the CO(2-1) line identified by the blind search (see §[3.2](#subsec:subsamples)).

rcccccc & 5c$\log{(M_*/M_\odot)}$\
& CO & $7.0-8.0$ & $8.0-9.0$ & $9.0-10.0$ & $10.0-11.0$ & $11.0-12.0$\
& 3-2 & 1 (1) & 5 (5) & 5 (4) & 1 (-) & -\
& 4-3 & 4 (4) & 4 (4) & 5 (5) & 1 (1) & -\
& 5-4 & - & - & - & - & -\
& 6-5 & - & - & - & - & -\
& 3-2 & 4 (4) & 21 (21) & 9 (9) & 4 (3) & -\
& 4-3 & 63 (63) & 79 (79) & 29 (29) & 4 (4) & -\
& 5-4 & 40 (40) & 46 (46) & 26 (26) & 11 (11) & 2 (2)\
& 6-5 & 2 ( 2) & 16 (16) & 14 (14) & 7 (7) & 3 (3)\
& 3-2 & - & - & - & - & -\
& 4-3 & - & - & 2 (2) & - & -\
& 5-4 & 1 (1) & - & 1 (1) & 1 (1) & -\
& 6-5 & 2 (2) & - & - & - & -

Table notes: The numbers in parentheses are after excluding the galaxies which have the CO line identified by the blind search (see §[3.2](#subsec:subsamples)).

rccccc & & 4c$\log{(M_*/M_\odot)}$\
& & $8.0-9.0$ & $9.0-10.0$ & $10.0-11.0$ & $11.0-12.0$\
& (1) & $<0.62$($<0.62$) & $2.47 \pm 0.61$($<1.02$) & $<1.59$($<1.59$) & –(–)\
& (2) & $<8.78$($<8.78$) & $23.42 \pm 5.89$($<9.70$) & $<7.53$($<7.53$) & –(–)\
& (1) & $<0.43$($<0.43$) & $<0.38$($<0.38$) & $2.51 \pm 0.40$($1.85 \pm 0.47$) & $10.57 \pm 0.97$(–)\
& (2) & $<6.11$($<6.11$) & $<3.62$($<3.62$) & $11.87 \pm 1.95$($8.74 \pm 2.26$) & $50.07 \pm 5.00$(–)\
& (1) & –(–) & $<1.03$($<1.03$) & $2.12 \pm 0.69$($2.12 \pm 0.69$) & $3.10 \pm 0.55$($<1.04$)\
& (2) & –(–) & $<9.71$($<9.71$) & $10.03 \pm 3.31$($10.03 \pm 3.31$) & $14.67 \pm 2.68$($<4.95$)

Table notes: The units are in ${\rm 10^9 \, K\,km\,s^{-1}\,pc^2}$ and $10^9 \, M_\odot$ for (1) CO(2-1) line luminosities (the first row in each MS bin) and (2) molecular masses ($M_{\rm gas}$; the second row), respectively. The CO–to–$\rm H_2$ conversion factors are assumed to be $\alpha_{\rm CO}=3.6$, 7.2, and 10.8 $\, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ for galaxies in the bins of $\log{(M_*/M_\odot)} > 10$, $9 < \log{(M_*/M_\odot)} \le 10$, and $8 < \log{(M_*/M_\odot)} \le 9$, respectively (see §[5.1](#subsec:gas_mass)). The values in parentheses are after excluding the galaxies which have the CO(2-1) line identified by the blind search (see §[3.2](#subsec:subsamples)).

rccccc & & 4c$\log{(M_*/M_\odot)}$\
& & $8.0-9.0$ & $9.0-10.0$ & $10.0-11.0$ & $11.0-12.0$\
& (1) & $<22.01$($<22.01$) & $9.94 \pm 2.50$($<4.52$) & $<0.51$($<0.51$) & –(–)\
& (2) & $<5.95$($<5.95$) & $1.82 \pm 0.46$($<1.84$) & $<0.05$($<0.05$) & –(–)\
& (1) & $<14.12$($<14.12$) & $<1.25$($<1.25$) & $0.49 \pm 0.08$($0.46 \pm 0.12$) & $0.24 \pm 0.02$(–)\
& (2) & $<11.27$($<11.27$) & $<1.46$($<1.46$) & $0.69 \pm 0.11$($0.67 \pm 0.17$) & $1.13 \pm 0.11$(–)\
& (1) & –(–) & $<2.82$($<2.82$) & $0.18 \pm 0.06$($0.18 \pm 0.06$) & $0.08 \pm 0.01$($<0.02$)\
& (2) & –(–) & $<31.44$($<31.44$) & $1.75 \pm 0.58$($1.75 \pm 0.58$) & $3.13 \pm 0.57$($<3.56$)

Table notes: The first and second rows in each MS bin are (1) molecular-to-stellar mass ratios ($M_{\rm gas}/M_*$) and (2) depletion times ($M_{\rm gas}/SFR$ in $\rm Gyr$), respectively. The CO–to–$\rm H_2$ conversion factors are assumed to be $\alpha_{\rm CO}=3.6$, 7.2, and 10.8 $\, M_\odot \, ({\rm K\,km\,s^{-1}\,pc^2})^{-1}$ for galaxies in the bins of $\log{(M_*/M_\odot)} > 10$, $9 < \log{(M_*/M_\odot)} \le 10$, and $8 < \log{(M_*/M_\odot)} \le 9$, respectively (see §[5.1](#subsec:gas_mass)). The values in parentheses are after excluding the galaxies which have the CO(2-1) line identified by the blind search (see §[3.2](#subsec:subsamples)).

# The individual spectra in the stacking

The individual spectra for the stacking of the galaxies on and below the MS with $10.0 < \log{(M*/M_\odot)} \leq 11.0$ are displayed in Figure [8](#fig:indiv_spec) (§[4.1.3](#subsec:indiv)).

![image]({NoKnownCO_WithPotentialCO_Mass10.0-11.0_Main-Sequence}.png) ![image]({NoKnownCO_WithPotentialCO_Mass10.0-11.0_Quiescent}.png)

# The stacked images, spectra, and measured upper limits for high-$J$ CO lines

The stacked images and spectra for CO(3-2), CO(4-3), CO(5-4), and CO(6-5) are shown in Figure [9](#fig:hi_j). The measured line flux upper limits are summarized in Table [\[tbl:hi_j_flux\]](#tbl:hi_j_flux).

![image]({muse_z_aspecs_2d_CO3-2_pb0.5_confid2_WithKnownCO_WithPotentialCO}.png) ![image]({muse_z_aspecs_2d_CO4-3_pb0.5_confid2_WithKnownCO_WithPotentialCO}.png) ![image]({muse_z_aspecs_2d_CO5-4_pb0.5_confid2_WithKnownCO_WithPotentialCO}.png) ![image]({muse_z_aspecs_2d_CO6-5_pb0.5_confid2_WithKnownCO_WithPotentialCO}.png)

# Tentative detections of CO(5-4)

In Figure [10](#fig:CO5-4), we present the two cases of potential CO(5-4) detections. As discussed in § [4.2](#subsec:results_hiJ), further observations are required to verify these tentative detections.

![]({CO5-4_possible_detection}.png)

# Comparisons with earlier studies

Here we demonstrate our results in the context of earlier studies including molecular gas measurements for galaxies at lower redshifts. We adopt the main-sequence relation of (cite: Spea14), which was also used in the analysis of PHIBSS2 (cite: Tacc18), to be consistent with the literature. Note that in the main text of this paper, the main-sequence relation of (cite: Boog18) is utilized throughout, because this is calibrated based on the MUSE-detected sources whose average stellar masses and SFRs are lower than the sample used in (cite: Spea14). Therefore, the data points and the boundaries of the main-sequence relation shown in this Appendix are slightly shifted compared to the ones shown in the main text. As presented in the rightmost panels of Figures [11](#fig:gas_T18_MS) and [12](#fig:gas_T18_All), the results are consistent even when the MS relation of (cite: Spea14) is adopted.

In this study, we put constraints on the molecular gas content through CO emission at $\log{(M_*/M_\odot)} \sim 9.5$, which has only been explored at lower redshift, as illustrated in the two left panels of Figure [11](#fig:gas_T18_MS). The majority of the PHIBSS2 sample at $z\sim0$ are from xCOLD GASS (cite: Sain11a; Sain11b; Sain16; Sain17). We find that at $z\sim1.5$, the molecular gas mass of the MS galaxies is increasing with increasing stellar mass, at least from $\log{(M_*/M_\odot)} \sim 9.5$ (top right). At lower redshift, this trend is seen starting from $\log{(M_*/M_\odot)} \sim 9.0$, but at smaller gas masses (cite: Sain17). In the bottom panels, a constant gas-to-stellar mass ratio between $\log{(M_*/M_\odot)} \sim 9.5$ and $\sim 10.5$ is shown at both $z\sim0$ and $z\sim1.5$ for galaxies lying on the MS. Then the gas-to-stellar mass ratio declines towards higher stellar masses.

In Figure [12](#fig:gas_T18_All), we show the same plots as in Figures [6](#fig:fgas-SSFR) and [7](#fig:Tdepl-SSFR) in the main text, but now the main-sequence relation of (cite: Spea14) is adopted. We also include the best-fit lines from (cite: Tacc18).

![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Mgas_vs_Mstar_z2_MS_T18-MSonly}.pdf) ![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Fgas_vs_Mstar_z2_MS_T18-MSonly}.pdf)

![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Fgas_vs_SSFR_z_ALL_T18}.pdf)\
![image]({muse_z_aspecs_2d_CO2-1_pb0.5_confid2_WithKnownCO_WithPotentialCO__Tdepl_vs_SSFR_z_ALL_T18}.pdf)

rcccccc & 5c$\log{(M_*/M_\odot)}$\
& CO & $7.0-8.0$ & $8.0-9.0$ & $9.0-10.0$ & $10.0-11.0$ & $11.0-12.0$\
& 3-2 & $<0.076$& $<0.026$& $<0.029$& –& –\
& 4-3 & $<0.035$& $<0.041$& $<0.035$& $<0.066$& –\
& 5-4 & –& –& –& –& –\
& 6-5 & –& –& –& –& –\
& 3-2 & $<0.039$& $<0.014$& $<0.025$& $<0.024$& –\
& 4-3 & $<0.008$& $<0.010$& $<0.017$& $<0.034$& –\
& 5-4 & $<0.013$& $<0.011$& $<0.014$& $<0.026$& $<0.037$\
& 6-5 & $<0.061$& $<0.018$& $<0.021$& $<0.027$& $<0.061$\
& 3-2 & –& –& –& –& –\
& 4-3 & –& –& $<0.065$& –& –\
& 5-4 & $<0.057$& –& $<0.044$& $<0.153$& –\
& 6-5 & $<0.052$& –& –& –& –

Table notes: The units are in ${\rm Jy\,km\,s^{-1}}$.

natexlab

(ref: Arav19) Aravena, M., Decarli, R., Gónzalez-López, J., et al. 2019, ApJ, 882, 136, doi: [`10.3847/1538-4357/ab30df`](http://doi.org/10.3847/1538-4357/ab30df)

(ref: Arav20) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, arXiv e-prints, arXiv:2006.04284. [`https:
//arxiv.org/abs/2006.04284`](https://arxiv.org/abs/2006.04284)

(ref: AsPy13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Baco15) Bacon, R., Brinchmann, J., Richard, J., et al. 2015, A&A, 575, A75, doi: [`10.1051/0004-6361/201425419`](http://doi.org/10.1051/0004-6361/201425419)

(ref: Baco17) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1, doi: [`10.1051/0004-6361/201730833`](http://doi.org/10.1051/0004-6361/201730833)

(ref: Beck06) Beckwith, S. V. W., Stiavelli, M., Koekemoer, A. M., et al. 2006, AJ, 132, 1729, doi: [`10.1086/507302`](http://doi.org/10.1086/507302)

(ref: Bola13b) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Boog18) Boogaard, L. A., Brinchmann, J., Bouché, N., et al. 2018, A&A, 619, A27, doi: [`10.1051/0004-6361/201833136`](http://doi.org/10.1051/0004-6361/201833136)

(ref: Boog19) Boogaard, L. A., Decarli, R., González-López, J., et al. 2019, ApJ, 882, 140, doi: [`10.3847/1538-4357/ab3102`](http://doi.org/10.3847/1538-4357/ab3102)

(ref: Boog20) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020 submitted, ApJ

(ref: Both14) Bothwell, M. S., Wagg, J., Cicone, C., et al. 2014, MNRAS, 445, 2599, doi: [`10.1093/mnras/stu1936`](http://doi.org/10.1093/mnras/stu1936)

(ref: Cari13b) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: daCu08) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595, doi: [`10.1111/j.1365-2966.2008.13535.x`](http://doi.org/10.1111/j.1365-2966.2008.13535.x)

(ref: daCu15) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: Dadd10b) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118, doi: [`10.1088/2041-8205/714/1/L118`](http://doi.org/10.1088/2041-8205/714/1/L118)

(ref: Dadd15) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46, doi: [`10.1051/0004-6361/201425043`](http://doi.org/10.1051/0004-6361/201425043)

(ref: Dave11) Davé, R., Finlator, K., & Oppenheimer, B. D. 2011, MNRAS, 416, 1354, doi: [`10.1111/j.1365-2966.2011.19132.x`](http://doi.org/10.1111/j.1365-2966.2011.19132.x)

(ref: Dave17) Davé, R., Rafieferantsoa, M. H., Thompson, R. J., & Hopkins, P. F. 2017, MNRAS, 467, 115, doi: [`10.1093/mnras/stx108`](http://doi.org/10.1093/mnras/stx108)

(ref: Deca16a) Decarli, R., Walter, F., Aravena, M., et al. 2016a, ApJ, 833, 69, doi: [`10.3847/1538-4357/833/1/69`](http://doi.org/10.3847/1538-4357/833/1/69)

(ref: Deca16b) —. 2016b, ApJ, 833, 70, doi: [`10.3847/1538-4357/833/1/70`](http://doi.org/10.3847/1538-4357/833/1/70)

(ref: Deca19) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138, doi: [`10.3847/1538-4357/ab30fe`](http://doi.org/10.3847/1538-4357/ab30fe)

(ref: Deke13) Dekel, A., & Krumholz, M. R. 2013, MNRAS, 432, 455, doi: [`10.1093/mnras/stt480`](http://doi.org/10.1093/mnras/stt480)

(ref: Dunc14) Duncan, K., Conselice, C. J., Mortlock, A., et al. 2014, MNRAS, 444, 2960, doi: [`10.1093/mnras/stu1622`](http://doi.org/10.1093/mnras/stu1622)

(ref: Dunl17) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861, doi: [`10.1093/mnras/stw3088`](http://doi.org/10.1093/mnras/stw3088)

(ref: Erb06) Erb, D. K., Shapley, A. E., Pettini, M., et al. 2006, ApJ, 644, 813, doi: [`10.1086/503623`](http://doi.org/10.1086/503623)

(ref: Freu19) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105, doi: [`10.1051/0004-6361/201732223`](http://doi.org/10.1051/0004-6361/201732223)

(ref: Geac11) Geach, J. E., Smail, I., Moran, S. M., et al. 2011, ApJL, 730, L19, doi: [`10.1088/2041-8205/730/2/L19`](http://doi.org/10.1088/2041-8205/730/2/L19)

(ref: Genz12) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69, doi: [`10.1088/0004-637X/746/1/69`](http://doi.org/10.1088/0004-637X/746/1/69)

(ref: Genz15) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20, doi: [`10.1088/0004-637X/800/1/20`](http://doi.org/10.1088/0004-637X/800/1/20)

(ref: Gned11) Gnedin, N. Y., & Kravtsov, A. V. 2011, ApJ, 728, 88, doi: [`10.1088/0004-637X/728/2/88`](http://doi.org/10.1088/0004-637X/728/2/88)

(ref: Gonz19) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139, doi: [`10.3847/1538-4357/ab3105`](http://doi.org/10.3847/1538-4357/ab3105)

(ref: Gonz20) González-López, J., Novak, M., Decarli, R., et al. 2020, arXiv e-prints, arXiv:2002.07199. [`https:
//arxiv.org/abs/2002.07199`](https://arxiv.org/abs/2002.07199)

(ref: Hodg20) Hodge, J. A., & da Cunha, E. 2020, arXiv e-prints, arXiv:2004.00934. [`https:
//arxiv.org/abs/2004.00934`](https://arxiv.org/abs/2004.00934)

(ref: Illi13) Illingworth, G. D., Magee, D., Oesch, P. A., et al. 2013, ApJS, 209, 6, doi: [`10.1088/0067-0049/209/1/6`](http://doi.org/10.1088/0067-0049/209/1/6)

(ref: Inam17) Inami, H., Bacon, R., Brinchmann, J., et al. 2017, A&A, 608, A2, doi: [`10.1051/0004-6361/201731195`](http://doi.org/10.1051/0004-6361/201731195)

(ref: Kenn12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Lenk20) Lenkić, L., Bolatto, A. D., Förster Schreiber, N. M., et al. 2020, AJ, 159, 190, doi: [`10.3847/1538-3881/ab7458`](http://doi.org/10.3847/1538-3881/ab7458)

(ref: Lill13) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119, doi: [`10.1088/0004-637X/772/2/119`](http://doi.org/10.1088/0004-637X/772/2/119)

(ref: Liu19) Liu, D., Schinnerer, E., Groves, B., et al. 2019, arXiv e-prints, arXiv:1910.12883. [`https:
//arxiv.org/abs/1910.12883`](https://arxiv.org/abs/1910.12883)

(ref: Lutz14) Lutz, D. 2014, ARA&A, 52, 373, doi: [`10.1146/annurev-astro-081913-035953`](http://doi.org/10.1146/annurev-astro-081913-035953)

(ref: Lyons11) Lyons, R. G. 2010, Understanding Digital Signal Processing, 3rd edn. (Prentice Hall)

(ref: Mada14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Magd12b) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6, doi: [`10.1088/0004-637X/760/1/6`](http://doi.org/10.1088/0004-637X/760/1/6)

(ref: Magn20) Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66, doi: [`10.3847/1538-4357/ab7897`](http://doi.org/10.3847/1538-4357/ab7897)

(ref: Mann09) Mannucci, F., Cresci, G., Maiolino, R., et al. 2009, MNRAS, 398, 1915, doi: [`10.1111/j.1365-2966.2009.15185.x`](http://doi.org/10.1111/j.1365-2966.2009.15185.x)

(ref: McMu07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Noes07) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43, doi: [`10.1086/517926`](http://doi.org/10.1086/517926)

(ref: Peng10) Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010, ApJ, 721, 193, doi: [`10.1088/0004-637X/721/1/193`](http://doi.org/10.1088/0004-637X/721/1/193)

(ref: Pope19a) Popesso, P., Concas, A., Morselli, L., et al. 2019a, MNRAS, 483, 3213, doi: [`10.1093/mnras/sty3210`](http://doi.org/10.1093/mnras/sty3210)

(ref: Pope19b) Popesso, P., Morselli, L., Concas, A., et al. 2019b, MNRAS, 490, 5285, doi: [`10.1093/mnras/stz2635`](http://doi.org/10.1093/mnras/stz2635)

(ref: Popp19) Popping, G., Pillepich, A., Somerville, R. S., et al. 2019, ApJ, 882, 137, doi: [`10.3847/1538-4357/ab30f2`](http://doi.org/10.3847/1538-4357/ab30f2)

(ref: Rafe15) Rafelski, M., Teplitz, H. I., Gardner, J. P., et al. 2015, AJ, 150, 31, doi: [`10.1088/0004-6256/150/1/31`](http://doi.org/10.1088/0004-6256/150/1/31)

(ref: Riec19) Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7, doi: [`10.3847/1538-4357/aafc27`](http://doi.org/10.3847/1538-4357/aafc27)

(ref: Rodi11) Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJL, 739, L40, doi: [`10.1088/2041-8205/739/2/L40`](http://doi.org/10.1088/2041-8205/739/2/L40)

(ref: Sain11a) Saintonge, A., Kauffmann, G., Kramer, C., et al. 2011a, MNRAS, 415, 32, doi: [`10.1111/j.1365-2966.2011.18677.x`](http://doi.org/10.1111/j.1365-2966.2011.18677.x)

(ref: Sain11b) Saintonge, A., Kauffmann, G., Wang, J., et al. 2011b, MNRAS, 415, 61, doi: [`10.1111/j.1365-2966.2011.18823.x`](http://doi.org/10.1111/j.1365-2966.2011.18823.x)

(ref: Sain16) Saintonge, A., Catinella, B., Cortese, L., et al. 2016, MNRAS, 462, 1749, doi: [`10.1093/mnras/stw1715`](http://doi.org/10.1093/mnras/stw1715)

(ref: Sain17) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: Salm12) Salmi, F., Daddi, E., Elbaz, D., et al. 2012, ApJL, 754, L14, doi: [`10.1088/2041-8205/754/1/L14`](http://doi.org/10.1088/2041-8205/754/1/L14)

(ref: Salm15) Salmon, B., Papovich, C., Finkelstein, S. L., et al. 2015, ApJ, 799, 183, doi: [`10.1088/0004-637X/799/2/183`](http://doi.org/10.1088/0004-637X/799/2/183)

(ref: Sand20) Sanders, R. L., Shapley, A. E., Reddy, N. A., et al. 2020, MNRAS, 491, 1427, doi: [`10.1093/mnras/stz3032`](http://doi.org/10.1093/mnras/stz3032)

(ref: Sant14) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30, doi: [`10.1051/0004-6361/201322835`](http://doi.org/10.1051/0004-6361/201322835)

(ref: Sarg12) Sargent, M. T., Béthermin, M., Daddi, E., & Elbaz, D. 2012, ApJL, 747, L31, doi: [`10.1088/2041-8205/747/2/L31`](http://doi.org/10.1088/2041-8205/747/2/L31)

(ref: Sarg14) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19, doi: [`10.1088/0004-637X/793/1/19`](http://doi.org/10.1088/0004-637X/793/1/19)

(ref: Sava05) Savaglio, S., Glazebrook, K., Le Borgne, D., et al. 2005, ApJ, 635, 260, doi: [`10.1086/497331`](http://doi.org/10.1086/497331)

(ref: Schr15) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74, doi: [`10.1051/0004-6361/201425017`](http://doi.org/10.1051/0004-6361/201425017)

(ref: Schr12) Schruba, A., Leroy, A. K., Walter, F., et al. 2012, AJ, 143, 138, doi: [`10.1088/0004-6256/143/6/138`](http://doi.org/10.1088/0004-6256/143/6/138)

(ref: Scov16) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: Scov17b) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150, doi: [`10.3847/1538-4357/aa61a0`](http://doi.org/10.3847/1538-4357/aa61a0)

(ref: Shap03) Shapley, A. E., Steidel, C. C., Pettini, M., & Adelberger, K. L. 2003, ApJ, 588, 65, doi: [`10.1086/373922`](http://doi.org/10.1086/373922)

(ref: Skel14) Skelton, R. E., Whitaker, K. E., Momcheva, I. G., et al. 2014, ApJS, 214, 24, doi: [`10.1088/0067-0049/214/2/24`](http://doi.org/10.1088/0067-0049/214/2/24)

(ref: Solo97) Solomon, P. M., Downes, D., Radford, S. J. E., & Barrett, J. W. 1997, ApJ, 478, 144, doi: [`10.1086/303765`](http://doi.org/10.1086/303765)

(ref: Solo05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: Some12) Somerville, R. S., Gilmore, R. C., Primack, J. R., & Domı́nguez, A. 2012, MNRAS, 423, 1992, doi: [`10.1111/j.1365-2966.2012.20490.x`](http://doi.org/10.1111/j.1365-2966.2012.20490.x)

(ref: Spea14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: Spil18) Spilker, J., Bezanson, R., Barišić, I., et al. 2018, ApJ, 860, 103, doi: [`10.3847/1538-4357/aac438`](http://doi.org/10.3847/1538-4357/aac438)

(ref: Tacch16) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 457, 2790, doi: [`10.1093/mnras/stw131`](http://doi.org/10.1093/mnras/stw131)

(ref: Tacc20) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, arXiv e-prints, arXiv:2003.06245. [`https:
//arxiv.org/abs/2003.06245`](https://arxiv.org/abs/2003.06245)

(ref: Tacc13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: Tacc18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: AsPy18) The Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, ArXiv e-prints. [`https:
//arxiv.org/abs/1801.02634`](https://arxiv.org/abs/1801.02634)

(ref: Uzgi19) Uzgil, B., Carilli, C., Lidz, A., et al. 2019, arXiv e-prints, arXiv:1911.00028. [`https:
//arxiv.org/abs/1911.00028`](https://arxiv.org/abs/1911.00028)

(ref: Verh18) Verhamme, A., Garel, T., Ventou, E., et al. 2018, MNRAS, 478, L60, doi: [`10.1093/mnrasl/sly058`](http://doi.org/10.1093/mnrasl/sly058)

(ref: Walt14) Walter, F., Decarli, R., Sargent, M., et al. 2014, ApJ, 782, 79, doi: [`10.1088/0004-637X/782/2/79`](http://doi.org/10.1088/0004-637X/782/2/79)

(ref: Walt16) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67, doi: [`10.3847/1538-4357/833/1/67`](http://doi.org/10.3847/1538-4357/833/1/67)

(ref: Whit12) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: Whit14) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104, doi: [`10.1088/0004-637X/795/2/104`](http://doi.org/10.1088/0004-637X/795/2/104)

(ref: Zahi11) Zahid, H. J., Kewley, L. J., & Bresolin, F. 2011, ApJ, 730, 137, doi: [`10.1088/0004-637X/730/2/137`](http://doi.org/10.1088/0004-637X/730/2/137)

[^1]: In cases where MUSE could not spatially resolve the *HST*-detected sources, these sources were “merged” into a single MUSE object. Its new coordinates are the *HST* F775W flux-weighted center of all the merged objects.

[^2]: The median stacking also produced similar results, but here we adopt the mean stacking for simpler noise estimates and for a better treatment when there are only two samples to stack.

[^3]: There are three galaxies (MUSE IDs 6314, 6450, and 6530) which meet the selection criteria, but their stellar masses and SFRs cannot be constrained because they have no optical counterpart on which to perform an SED fit. These galaxies are found by MUSE (no *HST* counterpart in the UVUDF catalog due to blending). These objects are not included in our sample of 111.

[^4]: Four of them detected by the CO blind search, ASPECS-LP-3mm.02, 04, 05, and 08, have a MUSE redshift confidence level of 1, but they are included in this work.

[^5]: This intrinsic scatter is found by assuming a Gaussian function in a model of the star formation sequence. As noted in (cite: Boog18), this value is higher than the average value reported in previous work.

[^6]: Note that a detection in the bin below the MS with $10.0 < \log{(M_*/M_\odot)} \leq 11.0$ has already been observed when the known CO(2-1) emission were included, because none of the galaxies in this bin include the directly detected CO(2-1) emission (none of the galaxies have been excluded to make any changes).

[^7]: This source has a new additional MUSE redshift $z=2.5739$ whose foreground galaxy is identified at $z=1.098$ (cite: Boog19).

[^8]: There is one CO(4-3) detection in the blind search, but this source does not have a MUSE redshift (cite: Arav19; Boog19).

[^9]: These models are the same as the ones shown in Figure 2 in (cite: Popp19), but without the ASPECS observational selection effects (i.e. we show here the entire population of galaxies predicted by the models).

</paper>

Write the methods card for this paper.