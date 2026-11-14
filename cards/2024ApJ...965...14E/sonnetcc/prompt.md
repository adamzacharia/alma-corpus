# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...965...14E\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...965...14E",
 "title": "An Automated Chemical Exploration of NGC 6334I at 340 au Resolution",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "El-Abd, Samer J.",
 "n_authors": 6,
 "arxiv_id": "2402.13913",
 "doi": "10.3847/1538-4357/ad283f",
 "alma_projects_linked_by_archive": [
  "2015.A.00022.T"
 ]
}
```

Paper text:
<paper>
# An Automated Chemical Exploration of NGC 6334I at 340 au Resolution

## Abstract

Much of the information gleaned from observations of star-forming regions comes from the analysis of their molecular emission spectra, particularly in the radio regime. The time-consuming nature of fitting synthetic spectra to observations interactively for such line-rich sources, however, often results in such analysis being limited to data extracted from a single-dish observation or a handful of pixels from an interferometric observation. Yet, star-forming regions display a wide variety of physical conditions that are difficult, if not impossible, to accurately characterize with such a limited number of spectra. We have developed an automated fitting routine that visits every pixel in the field of view of an ALMA data cube and determines the best-fit physical parameters, including excitation temperature and column densities, for a given list of molecules. In this proof-of-concept work, we provide an overview of the fitting routine and apply it to $0.26\ensuremath{''}$, 1.1 km s$^{-1}$ resolution ALMA observations of two sites of massive star-formation in NGC 6334I. Parameters were found for 21 distinct molecules by generating synthetic spectra across 7.48 GHz of spectral bandwidth between 280 and 351 GHz. Spatial images of the derived parameters for each of the $>8000$ pixels are presented with special attention paid to the isomers and their relative variations. We highlight the greater scientific utility of the column density and velocity images of individual molecules compared to traditional moment maps of single transitions.

# Introduction

The energetic events associated with star formation and the clustered nature of massive protostars result in a complicated picture with respect to the kinematics and excitation mechanisms of the surrounding gas (cite: Hunter:2021:L17; Rivilla:2013:A48). As the nascent protostars continue to evolve they heat up this gas, enabling a plethora of chemical reactions that cannot efficiently occur elsewhere in the interstellar medium (cite: Jorgensen:2020:727). The molecules that are formed in these unique environments are useful tools for understanding the physical conditions in which they are found. The characteristics of their rotational line emission can be used to measure the temperature and velocity of the gas (assuming local thermodynamic equilibrium), and the relative abundances of molecules constrain their formation pathways (cite: Herbst:2009:427).

The molecular emission that arises from star forming environments is a valuable tool for constraining the physical conditions of protostellar regions, *but only in the case that this emission can be properly identified*. The reality is that spectroscopic observations in the millimeter regime are often a dense conglomeration of lines due to the high spectral line density of many molecules. This makes it a challenging task to isolate the emission from a single molecule; attaining an accurate picture of the chemical inventory for such regions requires simultaneously fitting a large number of molecules to the data to accurately model as much of the observed spectral bandwidth as possible. We are fortunate to have a number of tools such as `molsim` (cite: Lee:2023:), `XCLASS` (cite: Moller:2017:A7), `MADCUBA` (cite: Martin:2019:A159), `CASSIS` (cite: Vastel:2015:313), `WEEDS` (cite: Maret:2011:A47) and `pyspeckit` (cite: Ginsburg:2011:ascl:1109.001) which make it a relatively trivial process to overlay a simulated rotational spectrum of a molecule over our observations for a wide range of physical parameters. Given a wide enough bandwidth of observations, we can then be confident of a molecule’s detection and characteristics if we can match the observed emission with reasonable parameters for a large number of emission lines. Individually fitting molecules to observations with a large bandwidth is a time-consuming process, however, especially if one wants to characterize the behavior of a large number of molecules. For this reason, the spectral analysis of star-forming regions is often limited to a small number of positions, if not a single one - thus leaving a wealth of information on the proverbial table. This approach is particularly problematic when applied to massive star-forming regions, as they are often physically and kinematically complex (cite: Brogan2007; Cunningham2023). Because the physical conditions vary significantly over the field of view of the observation, it is impossible to extrapolate information across the region from measurements taken over a handful of pixels with any confidence.

To address this problem, we have developed an automated least-squares fitting routine that will fit the combined spectra of a given list of molecules to every pixel in an ALMA image cube. This technique allows for a broader exploration of the physical conditions and molecular abundances surrounding massive star-forming regions and other protostellar environments by both accelerating the production of the measurements of interstellar molecular abundances and increasing the number of positions for which these measurements can be made. We have chosen ALMA data toward NGC 6334I spanning a total bandwidth of 7.48 GHz in the frequency range from 280 to 351 GHz for our initial proof of concept study. This massive Galactic protocluster hosts two extremely rich hot core line sources, each with distinct physical conditions and kinematics (see § [2.1](#source) for additional details), providing ample fodder to test our fitting technique on a challenging use case. The goal of this work should be stated clearly: we are not claiming that the final fit parameters for each pixel are necessarily as accurate as those that would be derived were one to manually fit each of the molecules by hand in one of the pixels. That said, we do believe that the derived parameters are reasonably accurate for the vast majority of the pixels in our field of view. These fits - taking into account their uncertainties - provide a unique point of view with regards to the spatial morphology of complex interstellar molecules that is not biased by an *a priori* choice in the extraction location of the spectra. Massive star-forming regions are physically and kinematically complicated; the ability to take a holistic view of such regions will be a crucial step forward for understanding their ongoing physical processes.

In this paper, the data on which the fitting routine was tested are described in § [2](#data), while the fitting technique itself is described in § [3](#routine). Images of the excitation temperature, linewidths, and velocity measured for each of $>$8000 pixels across two distinct regions in NGC 6334I are presented in § [4](#results), along with images of the physical column densities of the isomers. § [5](#discussion) expands on some of the methods of analysis this technique enables, as well as how the velocity and column density images compare with their moment map counterparts.

# ALMA Data Characteristics

## Test Case: NGC 6334I

![](test_cont.png)

NGC 6334I contains two prodigious hot core spectral line sources, MM1 and MM2 (cite: Beuther:2007:989; Zernickel:2012:A87; Bogelund:2018:A88). At a distance of 1.3 kpc (cite: Reid2014; Chibueze2014), these two sources are separated by only $\sim$4000 au (see Figure [1](#cont_fig), making any chemical differentiation between the two of them particularly diagnostic as it is reasonable to assume they likely formed from similar primordial material. MM1 (the brighter of the two sources) hosts at least two young protostars, MM1B and MM1D. Complicated bulk motions are evident in the source, with at least two outflows: one on a larger scale oriented NE-SW (cite: Qiu2011) and another more compact, dynamically young outflow in the N-S direction (cite: Brogan:2018:87). It is currently unclear which source within MM1 is driving these outflows. MM2 (129 K continuum peak at 350 GHz) is a source with significantly lower brightness temperature than MM1 (222 K continuum peak), but MM2 is still rich with molecular line emission and exhibits much narrower linewidths (see Figures [6](#3panel_mm1_univ) and [7](#3panel_mm2_univ)).

NGC 6334I-MM1 has recently undergone an accretion outburst in 2015 (cite: Macleod2018; Hunter:2017:L29). Accretion onto young stellar objects is an avenue by which stars are believed to gain a significant portion of their final mass (cite: Fischer:2019:183; Fischer:2022:). While this mechanism has long been associated with low-mass star formation, recent observational and theoretical evidence indicates this mechanism occurs in massive star formation as well (cite: Garatti:2017:276; Hunter:2021:L17; Meyer:2021:4448). Such accretion may occur rapidly in discrete episodes as opposed to a steady process that takes place over a longer stretch of time. These episodes are also responsible for energetic outflows driven through the surrounding cloud, raising the level of continuum emission as well as driving maser emission. In NGC 6334I-MM1, the continuum emission quadrupled in intensity and coincided with a rapid increase in the maser emission observed from the source. Both effects are still visible six years after the event (cite: Hunter:2017:L29; Hunter:2021:L17). It is highly likely that these energetic events serve as the impetus for a variety of unique chemical reactions across the region in question. Attaining a better understanding of this unique, complex environment is not feasible through the analysis of a small handful of positions. A new approach is required to be able to understand the entire breadth of the physical conditions and their associated molecular products.

## Observations

The ALMA data toward NGC 6334I used for this study were observed during Cycle 3 in 2016, under project code 2015.A.00022.T. These are the same data used in (cite: El-Abd:2019:129) but have since been reprocessed with the ALMA Cycle 8 pipeline (cite: Hunter2023) to account for an ALMA renormalization issue that can affect the flux scaling of strong spectral lines[^1]; these corrections were found to be of order 10% for the most affected transition, CS (J=6-5), and much lower to undetectable for the majority of transitions arising from complex organic molecules.

The observations consisted of two tunings, each with four spectral windows, with a bandwidth of 1.87 GHz per pair of windows. The first set of spectral windows were centered at 280.1, 282.0, 292.1, and 294.0 GHz. The second set of spectral windows were centered at 337.1, 339.0, 349.1, and 351.0 GHz. Both tunings were taken with a factor of 2 online channel averaging producing a channel width of 976.6 kHz; the spectral cubes were made with a channel width of 1.1 km s$^{-1}$, comparable to the effective spectral resolution. The observations were centered at $\alpha$(J2000) = 17$^h$:20$^m$:53$^s$.36, $\delta$(J2000) = -35$^\circ$:47$^\prime$:00$^{\prime\prime}$.0 and the images were created with CASA (cite: CASA2022) using `robust` image weighting values of 0.2 and 0.5 for the lower and higher frequency tunings, respectively. The resulting angular resolution of the images was a bit less than $0.26\ensuremath{''}$ (the beam was oversampled by a factor of 5 relative to the minor axis of the synthesized beam). The data were self-calibrated using the bright continuum emission, and the solutions were also applied to the continuum-subtracted line data; the continuum subtraction was performed as described in (cite: Brogan:2018:87). The full width at half-power (FWHP) of the primary beam is $\sim 20''$ and the images were corrected for the primary beam response. The cubes were smoothed to a uniform circular angular resolution of $0.26\ensuremath{''}$ before analysis with an rms noise per channel of 1.8 mJy beam$^{-1}$ for the lower tuning and 3.0 mJy beam$^{-1}$ for the upper tuning.[^2] Further data processing details are given in (cite: McGuire:2017:L46), (cite: Hunter:2017:L29), and (cite: Brogan:2018:87).

# The Fitting Routine

## Technique

`molsim` is a publicly-available Python package tailored for the analysis of high spectral resolution spectroscopic observations of astronomical sources. The use of this package, or others like it, enables astronomers to match the rotational spectra of molecules measured in the lab to observations made of the ISM and in turn derive physical parameters from those observations. This package has already been used to great effect across a number of different studies ranging from single-dish observations of a dark molecular cloud (cite: McGuire:2020:L10) to interferometric surveys of massive star-forming regions (cite: Schuessler:2022:102; Remijan:2022:A85). In tests comparing similar Python packages, (cite: Ginsburg:2022:291) found that the simulations produced by `molsim` were in good agreement with those produced by `XCLASS` and `pyspeckit`.

In addition to telescope- and source-specific parameters, for each molecule we derive values for excitation temperature ($T_{ex}$), linewidth ($\Delta V$), velocity ($v_{LSR}$), and column density ($N_T$) by forward-modeling the spectra of each species and performing a least-squares fit of the combined spectra across the entire frequency range of the observations. For our treatment of NGC 6334I, we made the assumption that all of the molecules in the model share a single excitation temperature, linewidth, and velocity for each pixel while we allow the column density to vary on a molecule-by-molecule basis. We discuss the robustness of each of these assumptions in detail later. In the case of $T_{ex}$ specifically, this assumption is required in order to properly account for optical depth corrections when lines of different species overlap with one another. As many of the spectral lines in our observations are at least modestly optically thick, a full radiative transfer analysis would be needed in order to simulate contributions from molecules at more than one excitation temperature, which is not possible in the current version of `molsim`.

While our initial goals were to use a least-squares minimizer - specifically, the bounded limited-memory BFGS algorithm (cite: Zhu:1997:550) - to find all of the relevant parameters for simulating the molecules, the nature of the spectra we were attempting to fit meant we were left with less than satisfactory results in pixels that had a particularly bright continuum or showed substantial absorption signals. For our specific test data on NGC 6334I near 300 GHz, which exhibits both very high dust continuum and high line opacity for abundant molecules, as well as a fairly extreme level of line blending, we found that it would be better to make independent measurements of the excitation temperature and linewidth for each pixel and rely on the minimizer to fit the velocity and column densities.

![](masking_example.png)

The excitation temperature is measured by assuming the brightest lines in our spectral range are optically thick (see Figure [2](#masking_example)). From this, it follows that we can directly solve for the excitation temperature adopting the formalism of (cite: Turner:1991:617):

$$\begin{equation}
    \Delta T_B = [J_\nu(T_{ul}) - J_\nu(T_{bg}) ] [1 - \text{exp}(-\tau)]
    \label{Turner1}
\end{equation}$$ where the source is assumed to fill the beam, $\Delta T_B$ is the intensity of a single transition, $T_{ul}$ is the excitation temperature, $T_{bg}$ is the background temperature (measured from the continuum image of each spectral window), $\tau$ is the opacity, and $$\begin{equation}
    J_\nu(T) = (h\nu/k)[\text{exp}(h\nu/kT)-1]^{-1}.
    \label{Turner2}
\end{equation}$$

Assuming $\tau>>1$ and rearranging the equations to solve for $T_{ul}$ per pixel, hereafter referred to as $T_{ex}$, we have

$$\begin{equation}
    T_{ex} = \frac{h\nu/k}{\text{ln}\bigl(\frac{h\nu}{k(J_\nu(T_{bg})+\Delta T_B)}  + 1\bigr)}.
    \label{Turner3}
\end{equation}$$ The adopted value for $\Delta T_B$ is found by computing the mean intensity, $I$, of all $N$ channels within $5\%$ of the peak intensity (from any line) for each pair of spectral windows (there are two spectral windows per sideband, two sidebands per tuning, and two different tunings) using the following equations:

$$\begin{equation}
\begin{aligned}
    \Delta T_B & = \overline{\Delta T}_{Bspw}\\
    \Delta T_{B spw} & = \frac{\sum_{j=1}^{N} I_j}{N}
\end{aligned}
\end{equation}$$

In the case of deviations from our assumption of a well-mixed, homogeneous gas parcel, the temperature derived from the optically thick lines may not perfectly represent those of the optically thin lines for a given species. We expect any such deviations to be small, and indeed find that the excitation temperatures derived from our optically thick lines result in fits to the optically thin lines well within expected uncertainties. The linewidth for each pixel is found by first running a spectral peak-finding algorithm across the entire frequency range of our observations, excluding any peaks below $10\sigma$ (see Section [2.2](#obs) for a description of the noise measurement). A Gaussian is fit to each of these spectral peaks and the resulting FWHM values are binned in a histogram. Another Gaussian is fit to the histogram itself, with the central value of this final Gaussian adopted as the canonical linewidth for the pixel in question. Although the linewidth of any particular transition may be heavily affected by spectral line confusion, the ensemble is largely insensitive to this effect given the large number of fitted transitions - see Figure [3](#dv_hist). Visual inspection of the fits and examination of residuals in numerous spectra show that the values extracted from this procedure indeed robustly describe the vast majority of spectral lines.

![](dv_hist.png)

Once the excitation temperature and linewidth have been measured, the fitting itself begins with a single pixel on the image with every molecule initialized to the same column density. Once the velocity and column densities have been measured, the same process is carried out for the pixel directly to the north, with the velocity and column densities from the previous pixel used as the starting parameters. This process is continued until the entire column has been fit (see Figure [4](#pixels_mm1)). Scripts are then launched in parallel that each use one of the pixels in this first column as a starting point and then moves across the rest of the corresponding row in the image. Using scripts in this fashion allows us to maintain the workflow of using the parameters from previous pixels as the starting point for the next fit while greatly decreasing the necessary computation time.

The minimization process is dramatically accelerated by the use of boundary conditions on the allowed values explored by the minimizer for each parameter. The flexibility on the bounds were carefully selected while balancing two factors: capturing the spread in physical parameters across NGC 6334I and a desire to make things more computationally efficient. In this case, we are aided by the assumption that the physical parameters should not vary dramatically (orders of magnitude) between pixels. Thus, we are able to set boundary conditions such that neighboring pixels should not differ significantly from one another.

For the results presented in this work, the velocity was allowed to vary by $\pm$ 1.0 km s$^{-1}$ from pixel-to-pixel, while the column density for each molecule was allowed to vary by $\pm$ 0.4 dex - these bounds were centered on the fitted value from the previous pixel in the fit. While this methodology for setting the bounds works for the vast majority of pixels in our images, a poor fit in one pixel has the potential to adversely affect the fit in the subsequent pixel - see Section [3.5](#areasofconcern) for a discussion of where this might have impacted our results.

## Molecules Included in the Model

The results presented in this work are the product of a best-fit synthetic emission model containing rotational spectra from 21 different molecules. Regarding which species to simulate, the molecules included in the models of (cite: El-Abd:2019:129) served as the starting point, with molecules added and removed as we explored the capability of the automated fitting method (see Table [\[mol_table\]](#mol_table) for the complete list). Several of the molecules initially included with the model had a relatively small number of transitions in the frequency range of our observations. Due to the small number of data points that the minimizer was working with - and more importantly, the overall number of available *unblended* transitions - the fit parameters for these molecules were poorly constrained relative to the other molecules.

Due to the poor fits in some regions for these molecules, we conducted another run of the fitting routine that was identical in every way except for the exclusion of these molecules. This run produced best-fit parameters for the remaining molecules that were well-matched to the previous results, indicating that the inclusion of a handful of poorly-constrained molecules does not negatively impact the fitting of the other molecules in our model. However we continued to exclude these molecules from future runs of the fitting routine as their inclusion drastically increased the required computation time. This increase was likely due to their minimal contributions to the final emission model over a wide range of parameters, meaning that a larger parameter space was being explored for each of these molecules. As these molecules did still have emission in a significant number of pixels in our field of view, channels that contained any of their emission were excluded from the fit.

While the 21 molecules that we included in the fitting routine cover a significant amount of the spectral emission, there are still a number of lines that can be attributed to molecules that are not included, or are otherwise unidentified. This result is within expectations - the goal of this initial pass was to fit the bulk of the emission in as efficient a manner as possible with molecules of interest.

## Exclusion of Channels

We quickly found that we could not simply start the code and leave it with nothing but the minimization function to guide it. NGC 6334I is a kinematically complicated source with a number of outflows and a bright continuum (cite: Brogan:2018:87); these properties cause effects in the spectra that make their simulations much more challenging. The key was figuring out how to identify the channels in our observations that exhibited significant absorption from molecular transitions with $E_{up} \ll T_{bg}$ or other such effects that we are currently incapable of modeling appropriately and excluding them from the fit.

The primary solution was to use an upper state energy exclusion threshold that is applied to problematic molecules included in the model - methyl cyanide and formamide in our case. These molecules are extremely abundant and have many intense lines in the frequency range of our observations. Many of these transitions have low upper state energies - such transitions are easy to excite and are prone to displaying absorption effects due to an intervening colder layer of molecules along our line of sight. There is also the matter of the absorption of these low-lying transitions against the bright continuum - this effect is more pronounced as the continuum level increases. These phenomena allow us to use the background temperature as a measure of which lines we can safely include in our simulations to fit. The exclusion threshold is dependent on the mean background temperature at that pixel (measured for each of four spectral windows), and excludes any channels of the observation from being fit if they are contaminated with emission from transitions with an upper state energy below the threshold (see Figure [2](#masking_example) for a demonstration). While the implementation of this threshold alleviated the opacity issue, there are still instances where the results of the fitting routine appear to be unphysical - see Figures [27](#b3) and [32](#b8) in Appendix B. The depression around MM1D is a likely consequence of the complex kinematics in that particular region, with visible evidence for multiple velocity components for some molecules. This effect appears to be more pronounced for molecules with higher column densities.

Methanol is an especially problematic molecule to fit in NGC 6334I. In the frequency range used for the study, the vibrational ground state of methanol ($v_t$=0) is dominated by relatively low $E_{up}$ transitions that are optically thick; this is true to a large degree even for the $v_t$=1 transitions. Thus, methanol required a separate solution - splitting the catalog into separate vibrational states such that we only attempted to fit the $v_t = 2$ transitions, as fitting the $v_t = 0,1$ transitions was an impossible task for most of the pixels in this source due to their significant opacity and consequent absorption effects. All of the $v_t = 0,1$ transitions were used to exclude channels from the observations as above regardless of their upper state energy. As with methyl cyanide and formamide, there appear to be regions that are difficult to get a handle on the methanol parameters, with MM1D again highlighted (Figure [25](#fig:b1)). For each of these molecules, and even less abundant molecules like methyl formate, the 13C isotopologues are certainly a more reliable representation of their spatial morphologies.

Additionally, a handful of molecules such as and were present in our observations but had few to no unblended transitions that were also unaffected by significant absorption effects. The simulated emission from all of the transitions of these molecules was used to exclude additional channels from the observations (see Section [3.2](#molecules) for the criteria for including a molecule in the model and Table [\[mol_table\]](#mol_table) for a complete list of molecules). All of these methods of treating the emission from various molecules not only improved the fits for the affected molecules like methyl cyanide and formamide, but also improved the fits for many of the other molecules included in the model.

![](pixels_mm1.png)

## Uncertainties

The uncertainties in the values produced by the fitting are estimated through the propagation of uncertainties in the fundamental measurements with the exception of the linewidth, $\Delta V$. Spatial maps of the uncertainties for each parameter can be found in the Appendix.

### Excitation Temperature

The two relevant quantities in Eq. [\[Turner3\]](#Turner3) for measuring the uncertainty in the excitation temperature are $\Delta T_B$ and $T_{bg}$. The rms noise for both of these quantities were measured and this uncertainty was propagated through the equation for excitation temperature for each spectral window; the values for each spectral window were added in quadrature. An additional factor of 10% of the final fitted value was added in quadrature with the final rms noise value to account for the absolute flux calibration uncertainty (cite: CortesPaulo:2023:).

### Linewidth

The uncertainty in the linewidths is taken directly from the uncertainty automatically calculated by the `lmfit` package used for the Gaussian fit to the histogram in Figure [3](#dv_hist).

### $V_{LSR}$

The uncertainty in the central value of a Gaussian can be approximated with the following equation (cite: Campbell:2018:)

$$\begin{equation}
    \sigma_c = \frac{\sqrt{FWHM \Delta\nu}}{SNR}
\end{equation}$$

where $\Delta\nu$ is the channel width of the observation. From this, the uncertainty in our fitted velocity is the root mean square of $\sigma_c$ scaled by the number of transitions used to constrain the velocity.

$$\begin{equation}
    \sigma_{V_{LSR}} = \frac{\sqrt{\sum_{j=1}^N\frac{\sigma_{cj}^2}{N}}}{\sqrt{N}}
\end{equation}$$

It should be stated that the uncertainty for the velocity given in this work is *not the uncertainty in the velocity for any single molecule in our model.* Rather, it is the uncertainty of the single best-fit velocity for the *ensemble* of included molecules.

### Column Density

The column density can be related to the intensity of a single optically thin transition with the following equation (cite: Hollis:2004:L45)

$$\begin{equation}
    N_T = \frac{1}{2}\frac{3k}{8\pi^3}\sqrt{\frac{\pi}{\text{ln2}}}\frac{Q\text{exp}(E_u/T_{ex})\Delta T_B \Delta V}{B \nu S\mu^2 \eta_B \bigl(1 - \frac{\text{exp}(h\nu / kT_{ex})-1}{\text{exp}(h\nu / kT_{bg})-1}\bigr)}
\end{equation}$$

where the relevant quantities for propagating the uncertainty are $\Delta T_B$, $\Delta V$, $T_{ex}$, and $T_{bg}$ for a single transition. However, our calculation of the column density is dependent on *all* of the transitions included in the molecule’s catalog. Due to the nature of performing a least-squares minimization the stronger transitions will be weighted more heavily in this calculation. The uncertainty in our final value for the column density can then be found by taking an intensity-weighted mean of the column density uncertainty calculated for individual optically thin transitions of a molecule

$$\begin{equation}
    \sigma_{N_T} = \sqrt{ \left(\sum_{j=1}^{N} \frac{\sigma_j I_j^2}{\sum_{k=1}^{N} I_k^2} \right)^2 + \sigma_{flux}^2 } 
\end{equation}$$

where $N$ is the number of transitions, $\sigma_j$ is the propagated uncertainty of the column density for a single transition, $I_j$ is the intensity of the transition, and $\sigma_{flux}$ represents 10% of the column density value to account for the absolute flux calibration uncertainty (cite: CortesPaulo:2023:). Note that $\sigma_j$ does not take into account the absolute flux calibration uncertainty as this quantity is correlated across transitions and incorporating it before the final step would result in an underestimate of the uncertainty. As the intensity of optically thick transitions does not change with small changes to the column density, such transitions do not contribute to the uncertainty calculation and are thus excluded from the calculation.

## Identifying Areas of Concern

While a visual inspection indicates that the simulated spectra generated by the automated fitting routine appear to match the observations within the uncertainties for the vast majority of the pixels in our field of view, there are a number of pixels for which the derived parameters were a relatively poor representation of the observations. The principle area of concern was a block of pixels toward MM1C, which displayed a large number of absorbed channels. While the derived parameters for many of the molecules were reasonable, the visible absorption negatively affected enough of the molecules that we decided to mask the region in its entirety for the column density maps. We have highlighted the pixels here as both a cautionary example and as a demonstration that the routine is capable of extricating itself from an unrealistic parameter space after fitting a problematic region.

Since the rows are each fit independently in our pseudo-parallel fitting routine, we had to be careful about introducing artificial structure. This was apparent in early versions of the routine where two rows would diverge wildly in velocity and/or column density for the same molecule. There appeared to be two separate causes for such an effect:

1.  High opacity: When moving over areas of high opacity, the fitting routine could not match any of the strongly absorbed lines for molecules like methanol or methyl cyanide.

2.  Low initial signal: Starting the fitting routine in a region of the image with low signal would cause the column density for weak molecules to go to unrealistic values, which could propagate through the rest of the image due to the bounds being dependent on the fit from the previous pixel.

These two separate causes were evident in MM1 and MM2, respectively. The opacity issue in MM1 and efforts to mitigate it have already been discussed with the upper state energy threshold in Section [3.3](#channel_exclusion), though this did not solve the issue for every pixel as shown with the additional mask we put in place around MM1C. In MM2, we found that simply starting the routine in an image column with higher signal and then branching out in either direction alleviated the issue. This fix necessitated a change in how the fitting routine hopped between pixels (see Figure [5](#pixels_mm2)).

![](pixels_mm2.png)

# Results

## The Shared Parameters - $T_{ex}$, $\Delta V$, and $V_{LSR}$

![](3panel_mm1_univ.png)

![](3panel_mm2_univ.png)

Figure [6](#3panel_mm1_univ) shows the final values for the excitation temperatures, linewidths, and velocities across MM1 while Figure [7](#3panel_mm2_univ) shows the same for MM2. For both of these sources, the presented linewidth images have been deconvolved from the channel width. In MM1, the excitation temperature tracks rather well with the continuum emission with little to no variation otherwise. The linewidth image, on the other hand, shows a significant amount of internal structure with broadening clearly visible in a column to the north and south. This broadening is consistent with our understanding of the kinematics of MM1 as the existence of a N-S outflow has previously been traced by maser emission and thermal lines of CS and HDO (cite: Brogan:2018:87; McGuire2018). The line broadening is a likely consequence of the walls of the outflow impacting the more quiescent gas. This technique gives us a concrete visual demonstration on how such large scale effects have a measurable impact on the spectral emission.

In MM2, neither the excitation temperature nor the linewidth images correlate particularly well with the continuum emission. The excitation temperature increases rapidly to the west of the continuum peak, whereas the linewidths display a clear enhancement to the northwest.

## Column Densities

The column density is uniquely derived for each of the 21 molecules that are included in the fitting routine’s emission model. In this discussion, we will primarily be focusing on images for the three isomers: methyl formate, glycolaldehyde, and acetic acid, with images for the other molecules available in the Appendix. The methyl formate image will, however, be that of the $^{13}$C isotopologue (CH$_3$O$^{13}$CHO) due to the fact that it is optically thin over our entire field of view as opposed to the standard isotopologue. Each of the images in the following sections (Figures [8](#3panel_mm1) and [9](#3panel_mm2)) has had two masks applied. Using the final fit parameters for each molecule, any pixel with less than 3 transitions with intensities greater than 5x the rms noise was masked. This mask manifests largely in the outermost pixels of MM1 and also results in a significant portion of the MM2 field of view being masked for certain molecules. The previously-mentioned block of pixels around MM1C (§ [3.5](#areasofconcern)) was masked for all molecules.

### MM1 Results

![](3panel_mm1_isomers.png)

The spatial morphology of 13-methyl formate follows the continuum emission in a fairly straightforward manner - peaks and troughs in the continuum emission are generally mirrored by increases and decreases in the 13-methyl formate column density, respectively.

The glycolaldehyde column density does not follow the continuum quite as closely as 13-methyl formate with several locations across MM1 presenting column densities close to the maximum; the strongest peak lies to the west of MM1B, which is offset from the peak of 13-methyl formate.

Acetic acid exhibits the sharpest increases and fall-offs in column density in our field of view for MM1, with a peak column density exceeding the other two molecules (its peak column density approaches that of 12-methyl formate) while also having a significant amount of masking visible due to the lack of detectable transitions in the north and south. While acetic acid also peaks to the west of MM1B, there is little apparent structure in the column density map besides also following the continuum emission fairly closely.

### MM2 Results

![](3panel_mm2_isomers.png)

As shown in Figure [9](#3panel_mm2), 13-methyl formate is the easiest isomer to detect in MM2, with relatively few pixels meeting the criteria for masking. The principal structure in the column density is a narrow band that closely follows the continuum emission. A slight decrease in the column density is also visible to the northwest of the continuum peak, around MM2B.

In MM2, glycolaldehyde is largely seen towards the innermost regions, with much of the image masked due to the lack of readily detectable transitions. The previous work of (cite: El-Abd:2019:129) had established the difficulty in detecting glycolaldehyde toward this source; this is reinforced by the significant masking in the field of view due to the small number of visible transitions. The presented column densities for glycolaldehyde in MM2 should be treated as upper limits.

The acetic acid distribution in MM2 is compact around the continuum emission, with much of the field of view again being masked due to the low intensity of the strongest transitions. In pixels that haven’t been masked, however, the acetic acid morphology closely resembles that of 13-methyl formate with the same narrow band cutting through the continuum contours.

## Column Density Ratios

A unique benefit of this method of spectral analysis is the ability to produce images that directly display the column density ratios between molecules, shown in Figure [10](#ratio_map) for the three isomers.

![](2panel_mm1_ratios.png)

There is a coherent structure to the map of the glycolaldehyde column density ratio with 13-methyl formate. The stand-out feature is the relative depletion of glycolaldehyde towards the continuum peak; it is conceivable, however, that the glycolaldehyde column density is getting underestimated in the region due to the optical depth of the spectra. The ratio with acetic acid, on the other hand, is remarkably constant over the field of view.

# Discussion

## Previous Findings

Analysis of the isomers has previously been carried out in NGC 6334I by (cite: El-Abd:2019:129) where the relative abundances of the three molecules were compared across select locations toward both MM1 and MM2 along with measurements for other star-forming regions that were found in the literature. While methyl formate and acetic acid were found to track linearly across all of the star-forming regions in the sample, methyl formate and glycolaldehyde instead displayed a bimodal trend with their abundances. Interestingly, the abundances of these molecules in MM1 and MM2 followed separate trends, an indication of some factor(s) preferentially affecting the production of glycolaldehyde despite the regions’ proximity. As these distributions were identified with a relatively small number of data points, we could now test whether the observed trends hold up with a much larger sample size across MM1 and MM2.

## Collating the Column Density Results

The key finding in (cite: El-Abd:2019:129) was in how ratios of molecular column densities appeared to display distinct trends across multiple sources. This pointed to some physical or chemical factor affecting the production of the selected molecules in a way that had not previously been considered. In that work, the ratio of methyl formate to glycolaldehyde was shown to have two distinct linear trends among a number of star-forming regions. Crucially, NGC 6334I-MM1 and -MM2 lay in separate trends, despite their close proximity. As previously discussed however, these trends were derived from a small number of spectra extracted from each source. The values for other star-forming regions were limited to a single point each. Reproducing such a plot with the plethora of new data points we have produced in this work would serve as an excellent indicator of whether the bimodal trend previously observed was due to the small sample size, or whether it was a true distinction in the data. It should be noted that we are instead using the $^{13}$C isotopologue of methyl formate for this work, as the standard isotopologue was too optically thick for many of the positions in our field of view.

![image](ch3o13cho_ch3cooh_masked.png) ![image](ch3o13cho_hcoch2oh_masked.png)

As can be seen in Figure [11](#scatter_fig), the addition of this new data has broadened the previously-observed trends of the isomers; it also appears that this data now encompasses several distinct regimes in which the production of these molecules may differ from one another within the same source. Despite this, the conclusions of (cite: El-Abd:2019:129) would appear to be upheld; the acetic acid points in MM2 comprise a single trend when combined with data from MM1, while there still appears to be two wholly separate trends in the production of glycolaldehyde relative to 13-methyl formate between the two sources.

![image](ch3o13cho_ch3cooh_tex_masked.png) ![image](ch3o13cho_hcoch2oh_tex_masked.png)

Besides the large-scale linear trends in Figure [11](#scatter_fig) there is some finer structure that is particularly visible when the data is colored by the excitation temperature (Figure [12](#tex_scatter)). (cite: Wilkins:2022:4) took this approach when comparing the $^{13}$CH$_3$OH and CH$_3$OD column densities in Orion-KL. In the case of acetic acid, the column densities and excitation temperatures match up extremely well in the low excitation temperature regime (below $\sim150$ K). There is a distinct trend that is populated by the higher excitation temperature data in MM1, but there is no comparable MM2 data to compare.

The glycolaldehyde plot in Figure [12](#tex_scatter) on the other hand, tells a much more complicated story. Taking each source separately, the glycolaldehyde column density generally increases with the excitation temperature in MM2. In MM1, the same thing happens at lower excitation temperatures (albeit at a faster rate) but the highest excitation temperature data carves out its own trend in the middle of the column density data. Interestingly, it is this high excitation temperature trend that matches the slope of the MM2 data. Overall, however, the column density and excitation temperature data are poorly correlated in the glycolaldehyde data, possibly indicating that there are other factors that play a more prominent role in the interstellar formation of glycolaldehyde.

## Comparison with Traditional Moment Maps

![](2panel_mm1_ch3o13cho_mom0_comparison.png)

The standard methods for analyzing the spatial distribution and kinematics of interstellar molecules over a large field of view make use of a variety of moment maps. Moment 0 maps analyze the integrated intensity of a single transition of a molecule across a given region and are often used as a proxy for the spatial distribution of the molecule. It is impossible, however, to disentangle the excitation conditions of a single transition from the physical abundance of its associated molecule using such an analysis. In regions that span a range of temperatures, this raises the question of whether we are observing a variation in the abundance of the molecule or whether we are highlighting regions where the physical conditions more readily excite a particular transition. Moment 1 maps use the intensity-weighted velocity of a transition to generate a velocity-field and are useful for studying the kinematics of a molecule. A velocity or linewidth gradient across the field of view, however, significantly hampers the applicability of these techniques. Spectral contamination from other molecules may easily be introduced, or the emission that one is attempting to integrate may shift out of the selected channel range, though efforts have been made to mitigate these issues such as the VINE maps introduced by (cite: Calcutt:2018:A90). In quiescent regions, these concerns can be alleviated by carefully selecting a transition and channel range to isolate only the emission of interest; however, in star-forming regions with complex kinematics and molecular inventories that vary from pixel to pixel, such a task is monumentally more difficult.

![](2panel_mm1_ch3o13cho_mom1_comparison.png)

In contrast with moment map analyses, the images that are presented as part of this work – for both the physical column densities and the velocity – are derived using the entire set of transitions for each included molecule in our observed bandwidth. Thus, we have removed any ambiguity that comes from the excitation of a single transition - provided there are enough transitions for said molecule in the scope of our observations to appropriately model the column density - as well as alleviated any concerns about the velocity shifting out of a relevant range. The comparison of the two methods in this work was conducted with 13-methyl formate. There are a number of 13-methyl formate transitions in our frequency range; unfortunately, while the transition used to create these moment maps appeared to be unblended for a number of positions, it also appears to be noticeably optically thick in several positions in MM1. It remains, however, the best of the available options in our data, and serves to illustrate the potential pitfalls when attempting to apply the moment map methodology to such a complex dataset. Even the $^{13}$C isotopologue of an abundant molecule is capable of apparent opacity issues, along with the difficult task of identifying a transition that is perpetually unblended across thousands of pixels in a region with an evolving molecular inventory and varying physical parameters.

### Comparison in MM1

There are several differences in the morphologies of the integrated intensity maps and column density images of methyl formate (Figure [13](#mm1_mom0)) that are immediately apparent. Many of the regions that were highlighted in Figure [1](#cont_fig) coincide with dips in the integrated intensity map; this is most likely a consequence of this particular transition having a high optical depth at these positions. The column density image, as previously discussed, instead varies smoothly across our field of view in a manner that loosely follows the continuum emission. This highlights the challenges of using moment maps as proxies for molecular distributions, as there are clear morphological differences from a true map of the column density.

In contrast, the moment 1 map from this transition and the velocity image from the routine are qualitatively much more similar (Figure [14](#mm1_mom1)). There still exist discrepancies between the two, however, with the greatest divergence occurring around MM1F on the order of several kilometers per second. Delving into the spectra in some of these pixels, it was clear that the kinematics had not been adequately captured by the channels selected for the moment map (see Appendix C for a visual demonstration). This reinforces the difficulty in finding a single range of channels that adequately treats an entire star-forming region for the purposes of generating a velocity field from a moment map. Simply increasing the number of channels to capture the emission in one position would introduce unwanted emission in other positions. In both presented moment maps there are myriad effects which may negatively impact our ability to gain accurate information and are alleviated by the images produced by the fitting routine. The opacity of an individual transition is mitigated by leveraging all of the available transitions for a particular molecule; spectral contamination of an individual transition from molecular variation in different positions also ceases to be an issue. In addition, the velocity image is not skewed by improperly accounting for the velocity structure in a source - an impossible task for a source as complicated as NGC 6334I.

### Comparison in MM2

![](2panel_mm2_mom0_comparison.png)

![](2panel_mm2_mom1_comparison.png)

The morphologies of the integrated intensity maps and column density images are in much better agreement in MM2 than MM1 (Figure [15](#mm2_mom0)). The molecule is fairly well matched to the continuum emission in both cases, and there are no regions where the two plots significantly differ, likely due to the generally lower opacity of MM2. The moment 1 map is in fairly good agreement with the velocity image outside of the displayed contours (Figure [16](#mm2_mom1)), but diverges fairly significantly (again on the order of a few kilometers per second) towards the warmer region. See Appendix C for a discussion on how such a discrepancy may arise.

+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| Molecule                   | Catalogs                | Vib. States $^{1,2}$        | No. of Transitions $^3$ | $E_{U}$ Range \[K\]     | $E_{U}$ Threshold       | Database $^4$           |
+:==========================:+:=======================:+:===========================:+:=======================:+:=======================:+:=======================:+:=======================:+
|                            | 1                       | $\mathbf{v_t = 2}$          | 49                      | 573 - 2524              | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^{13}$CH$_3$OH            | 1                       | $\mathbf{v_t = 0-1}$        | 57                      | 17 - 891                | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 2                       | $\mathbf{v = 0, v_8 = 1}$   | 112                     | 120 - 2969              | $3*T_{BG}$              | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| CH$_3$ $^{13}$CN           | 1                       | $v = 0$                     | 29                      | 120 - 1721              | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 76                      | 101 - 1569              | None                    | JPL                     |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 29                      | 102 - 2323              | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $\mathbf{v_t = 0-2}$        | 626                     | 26 - 2939               | None                    | JPL                     |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 2                       | $v = 0, v_{12} = 1$         | 145                     | 58 - 2472               | $3*T_{BG}$              | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| t-HCOOH                    | 1                       | $v = 0$                     | 98                      | 24 - 2048               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $\mathbf{v = 0}$            | 267                     | 32 - 1302               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 1143                    | 49 - 2688               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 348                     | 25 - 2886               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $\mathbf{v_t = 0-2}$        | 1486                    | 46 - 2241               | None                    | JPL                     |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $\mathbf{v_t = 0-1}$        | 993                     | 38 - 1749               | None                    | JPL                     |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v_t = 0-3$                 | 2142                    | 27 - 4916               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 2                       | $\mathbf{v_t = 0, v_t = 1}$ | 2790                    | 36 - 2398               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| CH$_3$O$^{13}$CHO          | 1                       | $\mathbf{v_t = 0-1}$        | 1435                    | 25 - 1485               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 951                     | 60 - 1696               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 1104                    | 59 - 1912               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 1                       | $v = 0$                     | 421                     | 67 - 1105               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
|                            | 2                       | $\mathbf{v = 0, v_2 = 1}$   | 90                      | 29 - 5355               | None                    | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^{\ddag}$                 | 1                       | $\mathbf{v_t = 0-1}$        | 216                     | 17 - 2640               | N/A                     | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| CH$_3$ $^{18}$OH$^{\ddag}$ | 1                       | $\mathbf{v_t = 0-2}$        | 160                     | 29 - 2620               | N/A                     | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^{\ddag}$                 | 1                       | $v = 0$                     | 14                      | 143 - 1536              | N/A                     | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^{\ddag}$                 | 2                       | $v = 0, v = 1$              | 7                       | 26 - 1718               | N/A                     | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^{\ddag}$                 | 1                       | $\mathbf{v = 0}$            | 2                       | 217 - 307               | N/A                     | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^{\ddag}$                 | 2                       | $v = 0, v_2 = 1$            | 6                       | 161 - 924               | N/A                     | CDMS                    |
+----------------------------+-------------------------+-----------------------------+-------------------------+-------------------------+-------------------------+-------------------------+
| $^1$Vibrational states in separate catalogs are denoted by commas.                                                                                                                         |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^2$Bolded text indicates entries where vibrational contributions to the partition function are included.                                                                                  |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Column density estimates for the non-bolded entries are potentially slightly underestimated in the case                                                                                    |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| an updated partition function is calculated. All entries use the most up-to-date partition functions as of publication.                                                                    |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^3$This number refers to all of the transitions in the catalog in our frequency range, not all detected transitions.                                                                      |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^4$The catalogs were obtained from both the CDMS (cite: Muller:2005:215) and JPL (cite: Pickett:1998:883) spectroscopic databases.                                                        |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{\ddag}$Channels containing emission from these molecules are excluded from the fit.                                                                                                     |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

# Conclusions

Star-forming regions are physically complicated environments; if we are to better understand the effects that evolving protostars have on their environments, and how those environments in turn affect the formation of the protostars, we must first be able to understand the wide range of physical conditions present in these sources. While this problem is of a scale that would be intractable to solve by treating individual pixels, we have demonstrated the feasibility of an automated approach to the measurement of the physical conditions and molecular column densities in NGC 6334I-MM1 and -MM2. The observed trends with respect to the bifurcation of the relative column densities of the isomers were in agreement with the work of (cite: El-Abd:2019:129). Comparisons were conducted with the results of the fitting routine and the closest moment map analogues. In comparing the moment 1 map and velocity image the fitting routine more accurately represented the velocity of the emission. Comparing the moment 0 maps and column density images demonstrated shortcomings in attempting to use the moment 0 map as a proxy for the column density.

# Appendix A

The spectra from NGC 6334I-MM1 and -MM2 are remarkably varied in both the level of spectral crowding and the overall intensity of the molecular emission. We have selected a number of positions from which to extract spectra to demonstrate this fact in Figures [19](#mm1spectra)–[21](#mm2spectra), with emission from the isomers highlighted.

![](mm1_finder.png)

![](mm2_finder.png)

![image](mm1_24_67_window.png) ![image](mm1_34_63_window.png) ![image](mm1_42_55_window.png) ![image](mm1_27_53_window.png)

![image](mm1_34_38_window.png) ![image](mm1_26_29_window.png) ![image](mm1_18_24_window.png) ![image](mm1_26_13_window.png)

![image](mm2_35_41_window.png) ![image](mm2_17_35_window.png) ![image](mm2_24_24_window.png) ![image](mm2_34_17_window.png)

# Appendix B

Images for each of the parameters derived using the fitting routine along with the associated uncertainties are presented in Figures [22](#fig:b00)–[69](#fig:b42) for all of the molecules in the emission model. Note that while each column density image spans 1.2 orders of magnitude, the range is unique for each molecule. The column density uncertainty images cover a uniform range for all molecules and are expressed as a percentage of the value for each pixel. The uncertainty images for the other parameters are expressed in physical units. The same masks described in Section [4.2](#column_densities) have been applied to these images.

![](2panel_mm1_temp_unc.png)

![](2panel_mm1_dV_unc.png)

![](2panel_mm1_velocity_unc.png)

![](2panel_mm1_ch3oh_unc.png)

![](2panel_mm1_13ch3oh_unc.png)

![](2panel_mm1_ch3cn_unc.png)

![](2panel_mm1_ch313cn_unc.png)

![](2panel_mm1_nh2cn_unc.png)

![](2panel_mm1_h2cco_unc.png)

![](2panel_mm1_ch3cho_unc.png)

![](2panel_mm1_nh2cho_unc.png)

![](2panel_mm1_t_hcooh_unc.png)

![](2panel_mm1_ch3och3_unc.png)

![](2panel_mm1_c2h5oh_unc.png)

![](2panel_mm1_c2h5cn_unc.png)

![](2panel_mm1_ch3coch3_unc.png)

![](2panel_mm1_ch3ocho_unc.png)

![](2panel_mm1_hcoch2oh_unc.png)

![](2panel_mm1_ch3cooh_unc.png)

![](2panel_mm1_ch3o13cho_unc.png)

![](2panel_mm1_a_ch2ohch2oh_unc.png)

![](2panel_mm1_g_ch2ohch2oh_unc.png)

![](2panel_mm1_ch3och2oh_unc.png)

![](2panel_mm1_so2_unc.png)

![](2panel_mm2_temp_unc.png)

![](2panel_mm2_dV_unc.png)

![](2panel_mm2_velocity_unc.png)

![](2panel_mm2_ch3oh_unc.png)

![](2panel_mm2_13ch3oh_unc.png)

![](2panel_mm2_ch3cn_unc.png)

![](2panel_mm2_ch313cn_unc.png)

![](2panel_mm2_nh2cn_unc.png)

![](2panel_mm2_h2cco_unc.png)

![](2panel_mm2_ch3cho_unc.png)

![](2panel_mm2_nh2cho_unc.png)

![](2panel_mm2_t_hcooh_unc.png)

![](2panel_mm2_ch3och3_unc.png)

![](2panel_mm2_c2h5oh_unc.png)

![](2panel_mm2_c2h5cn_unc.png)

![](2panel_mm2_ch3coch3_unc.png)

![](2panel_mm2_ch3ocho_unc.png)

![](2panel_mm2_hcoch2oh_unc.png)

![](2panel_mm2_ch3cooh_unc.png)

![](2panel_mm2_ch3o13cho_unc.png)

![](2panel_mm2_a_ch2ohch2oh_unc.png)

![](2panel_mm2_g_ch2ohch2oh_unc.png)

![](2panel_mm2_ch3och2oh_unc.png)

![](2panel_mm2_so2_unc.png)

# Appendix C

We present two spectra extracted from the northernmost “filament" in the linewidth map of Figure [6](#3panel_mm1_univ) to showcase the measurable difference in the lineshapes in Figure [70](#dv_image). We also present a pair of spectra demonstrating how the variation in spectral crowding across the source can impact the measured velocity using the moment map technique.

![](dv_image.png)

![](vlsr_image.png)

# Acknowledgments

This paper makes use of the following ALMA data: #2015.A.00022.T. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research made use of NASA’s Astrophysics Data System Bibliographic Services, Astropy, a community-developed core Python package for Astronomy (cite: AstropyCollaboration:2022:167), and APLpy, an open-source plotting package for Python (cite: aplpy2012). Support for this work was provided by the NSF through the Grote Reber Fellowship Program administered by Associated Universities, Inc./National Radio Astronomy Observatory. We would like to thank the referee for their comments regarding this work.

# Software

APLpy (cite: aplpy2012), Astropy (cite: AstropyCollaboration:2022:167), CASA (cite: CASA2022), Jupyter (cite: Kluyver:2016:87), lmfit (cite: Newville:2014:), molsim (cite: Lee:2023:), scipy (cite: Gommers:2023:)

natexlab

(ref: AstropyCollaboration:2022:167) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, The Astrophysical Journal, 935, 167.

(ref: Beuther:2007:989) Beuther, H., Walsh, A. J., Thorwirth, S., et al. 2007, Astronomy & Astrophysics, 466, 989.

(ref: Brogan2007) Brogan, C. L., Chandler, C. J., Hunter, T. R., Shirley, Y. L., & Sarma, A. P. 2007, ApJL, 660, L133

(ref: Brogan2016) Brogan, C. L., Hunter, T. R., Cyganowski, C. J., et al. 2016, ApJ, 832, 187

(ref: Brogan:2018:87) Brogan, C. L., Hunter, T. R., Cyganowski, C. J., et al. 2018, The Astrophysical Journal, 866, 87.

(ref: Bogelund:2018:A88) Bøgelund, E. G., McGuire, B. A., Ligterink, N. F. W., et al. 2018, Astronomy & Astrophysics, 615, A88.

(ref: Calcutt:2018:A90) Calcutt, H., Jørgensen, J. K., Müller, H. S. P., et al. 2018, Astronomy & Astrophysics, 616, A90.

(ref: Campbell:2018:) Campbell, S. 2018, Comparison of the generalized centroid with Gaussian and quadratic peak localization methods, arXiv, arXiv:1807.08355.

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Chibueze2014) Chibueze, J. O., Omodaka, T., Handa, T., et al. 2014, ApJ, 784, 114

(ref: CortesPaulo:2023:) Cortes, P., Vlahakis, C., Hales, A., et al. 2023, doi:10.5281/ZENODO.4511521, publisher: Zenodo Version Number: Cycle 10; Doc. 10.3; version 1.1.

(ref: Cunningham2023) Cunningham, N., Ginsburg, A., Galván-Madrid, R., et al. 2023, arXiv e-prints, arXiv:2306.14710

(ref: El-Abd:2019:129) El-Abd, S. J., Brogan, C. L., Hunter, T. R., et al. 2019, The Astrophysical Journal, 883, 129.

(ref: Fischer:2022:) Fischer, W. J., Hillenbrand, L. A., Herczeg, G. J., et al. 2022, Accretion Variability as a Guide to Stellar Mass Assembly, arXiv, arXiv:2203.11257 \[astro-ph\].

(ref: Fischer:2019:183) Fischer, W. J., Safron, E., & Megeath, S. T. 2019, The Astrophysical Journal, 872, 183.

(ref: Garatti:2017:276) Garatti, A. C. o., Stecklum, B., Lopez, R. G., et al. 2017, Nature Physics, 13, 276.

(ref: Ginsburg:2011:ascl:1109.001) Ginsburg, A., & Mirocha, J. 2011, Astrophysics Source Code Library, ascl:1109.001, aDS Bibcode: 2011ascl.soft09001G.

(ref: Ginsburg:2022:291) Ginsburg, A., Sokolov, V., de Val-Borro, M., et al. 2022, The Astronomical Journal, 163, 291.

(ref: Gommers:2023:) Gommers, R., Virtanen, P., Burovski, E., et al. 2023, scipy/scipy: SciPy 1.11.1, Zenodo, doi:10.5281/ZENODO.8092679.

(ref: Herbst:2009:427) Herbst, E., & Van Dishoeck, E. F. 2009, Annual Review of Astronomy and Astrophysics, 47, 427.

(ref: Hollis:2004:L45) Hollis, J. M., Jewell, P. R., Lovas, F. J., & Remijan, A. 2004, The Astrophysical Journal, 613, L45.

(ref: Hunter:2017:L29) Hunter, T. R., Brogan, C. L., MacLeod, G., et al. 2017, The Astrophysical Journal, 837, L29.

(ref: Hunter:2021:L17) Hunter, T. R., Brogan, C. L., De Buizer, J. M., et al. 2021, The Astrophysical Journal Letters, 912, L17.

(ref: Hunter2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, arXiv e-prints, arXiv:2306.07420

(ref: Jorgensen:2020:727) Jorgensen, J. K., Belloche, A., & Garrod, R. T. 2020, Annual Review of Astronomy and Astrophysics, 58, 727.

(ref: Kluyver:2016:87) Kluyver, T., Ragan-Kelley, B., Pérez, F., et al. 2016, Jupyter Notebooks—a publishing format for reproducible computational workflows, pages: 87-90 Publication Title: IOS Press ADS Bibcode: 2016ppap.book...87K, doi:10.3233/978-1-61499-649-1-87.

(ref: Lee:2023:) Lee, K. L. K., Loomis, R. A., Xue, C., El-Abd, S., & McGuire, B. A. 2023, molsim, Zenodo, doi:10.5281/ZENODO.8118192.

(ref: Macleod2018) MacLeod, G. C., Smits, D. P., Goedhart, S., et al. 2018, MNRAS, 478, 1077

(ref: Maret:2011:A47) Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, Astronomy and Astrophysics, 526, A47.

(ref: Martin:2019:A159) Martín, S., Martín-Pintado, J., Blanco-Sánchez, C., et al. 2019, Astronomy & Astrophysics, 631, A159.

(ref: McGuire:2017:L46) McGuire, B. A., Shingledecker, C. N., Willis, E. R., et al. 2017, The Astrophysical Journal, 851, L46.

(ref: McGuire2018) McGuire, B. A., Brogan, C. L., Hunter, T. R., et al. 2018, ApJL, 863, L35

(ref: McGuire:2020:L10) McGuire, B. A., Burkhardt, A. M., Loomis, R. A., et al. 2020, The Astrophysical Journal, 900, L10.

(ref: Meyer:2021:4448) Meyer, D. M. A., Vorobyov, E. I., Elbakyan, V. G., et al. 2021, Monthly Notices of the Royal Astronomical Society, 500, 4448.

(ref: Moller:2017:A7) Möller, T., Endres, C., & Schilke, P. 2017, Astronomy & Astrophysics, 598, A7.

(ref: Muller:2005:215) Müller, H. S., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215.

(ref: Newville:2014:) Newville, M., Stensitzki, T., Allen, D. B., & Ingargiola, A. 2014, LMFIT: Non-Linear Least-Square Minimization and Curve-Fitting for Python, Zenodo, doi:10.5281/ZENODO.11813.

(ref: Pickett:1998:883) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883.

(ref: Qiu2011) Qiu, K., Wyrowski, F., Menten, K. M., et al. 2011, ApJL, 743, L25

(ref: Reid2014) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, ApJ, 783, 130

(ref: Remijan:2022:A85) Remijan, A., Xue, C., Margulès, L., et al. 2022, Astronomy & Astrophysics, 658, A85.

(ref: Rivilla:2013:A48) Rivilla, V. M., Martin-Pintado, J., Jimenez-Serra, I., & Rodriguez-Franco, A. 2013, Astronomy & Astrophysics, 554, A48.

(ref: aplpy2012) Robitaille, T., & Bressert, E. 2012, APLpy: Astronomical Plotting Library in Python, , , ascl:1208.017

(ref: Schuessler:2022:102) Schuessler, C., Remijan, A., Xue, C., et al. 2022, The Astrophysical Journal, 941, 102.

(ref: Turner:1991:617) Turner, B. E. 1991, The Astrophysical Journal Supplement Series, 76, 617.

(ref: Vastel:2015:313) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. M., & Boiziot, M. 2015, CASSIS: a tool to visualize and analyse instrumental and synthetic spectra., conference Name: SF2A-2015: Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics Pages: 313-316.

(ref: Wilkins:2022:4) Wilkins, O. H., Carroll, P. B., & Blake, G. A. 2022, The Astrophysical Journal, 924, 4.

(ref: Zernickel:2012:A87) Zernickel, A., Schilke, P., Schmiedeke, A., et al. 2012, Astronomy & Astrophysics, 546, A87.

(ref: Zhu:1997:550) Zhu, C., Byrd, R. H., Lu, P., & Nocedal, J. 1997, ACM Transactions on Mathematical Software, 23, 550.

[^1]: see https://help.almascience.org/kb/articles/what-errors-could-originate-from-the-correlator-spectral-normalization-and-tsys-calibration

[^2]: The rms noise measurements were made in line-free channels of the data cube at several positions between the 0.8 and 0.6 primary beam response annulus; a further distance from the phase center than either MM1 or MM2. These are conservative estimates because the noise is not uniform in the maps corrected for the primary beam response; the noise level increases with distance from the phase center.

</paper>

Write the methods card for this paper.