# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...970...30M\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...970...30M",
 "title": "First Constraints on the Interstellar Medium Conditions of a Low-mass, Highly Obscured z = 4.27 Main-sequence Galaxy",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Mizener, Andrew",
 "n_authors": 7,
 "arxiv_id": "2405.04582",
 "doi": "10.3847/1538-4357/ad4965",
 "alma_projects_linked_by_archive": [
  "2021.1.00272.S"
 ]
}
```

Paper text:
<paper>
# First Constraints on the ISM Conditions of a Low Mass, Highly Obscured z=4.27 Main Sequence Galaxy

## Abstract

We present the molecular gas content and ISM conditions of MACSJ0717_Az9, a strong gravitationally lensed $z=4.273$, $M_{*} \simeq 2\times10^9M_{\odot}$ star-forming galaxy with an unusually high ($\sim 80\%$) obscured star formation fraction. We detect CO(4-3) in two independent lensed images, as well as \[N II\]205$\mu$m, with ALMA. We derive a molecular gas mass of log$_{10}[M_{H_{2}} (M_{\odot})] = 9.77$ making it moderately deficient in molecular gas compared to the lower redshift gas fraction scaling relation. Leveraging photodissociation region (PDR) models, we combine our CO(4-3) measurements with existing measurements of the \[C II\] 158$\mu$m line and total infrared luminosity to model the PDR conditions. We find PDR conditions similar to local star-forming galaxies, with a mean hydrogen density log$_{10}$\[$n_H$ $cm^{-3}$\] = $4.80\pm0.39$ and a mean radiation field strength log$_{10}$\[G$_0$ Habing\] = $2.83\pm0.26$. Based on Band 3 continuum data, we derive an upper limit on the intrinsic dust mass of log$_{10}[M_{\rm dust} (M_{\odot})] < 7.73$, consistent with existing estimates. We use the 3D tilted-ring model fitting code 3D-Barolo to determine the kinematic properties of the CO(4-3) emitting gas. We find that it is rotationally dominated, with a $V/\sigma=4.6 \pm 1.7$, consistent with the kinematics of the \[C II\]. With PDR conditions remarkably similar to normal dusty star-forming galaxies at z \<0.2 and a stable molecular disk, our observations of Az9 suggest that the dust-obscured phase for a low-mass galaxy at z$\sim$4 is relatively long. Thus, Az9 may be representative of a more widespread population that has been missed due to insufficiently deep existing millimeter surveys.

# Introduction

In the late 1990s, the first sub-millimeter surveys with SCUBA (cite: Smail1997; Barger1998) revealed a new population of massive, intensely IR-luminous dusty star-forming galaxies at high redshift. Though massive, dusty, infrared-luminous galaxies have been a popular subject of study in the intervening decades, our understanding of their highly-obscured analogues at lower masses, infrared luminosities, and star formation rates is limited. These systems are widespread: at $z > 2.5$, star-forming galaxies with stellar masses $M < 10^{10} M_\odot$ dominate the galaxy population by number count (cite: Somerville2015; Solimano2021). The subset of these galaxies with total stellar mass around $\sim 10^9 M_{\odot}$ at $z\sim4$ are the likely progenitors of galaxies with stellar mass similar to our Milky Way at $z\sim0$ (cite: Moster2013; vanDokkum2013). However, due to observational challenges, they are not well studied at millimeter wavelengths. Probing the gas content, kinematics, and ISM conditions of these systems is vital to developing an understanding of how “normal" galaxies assemble their mass and build up their dust and metal content in the early universe.

With a stellar mass of $2.14^{+1.04}_{-0.05} \times 10^{9} M_{\odot}$ and a total star formation rate of SFR$_{total} = 30.3$ $M_{\odot}$/yr, MACSJ0717_Az9 (hereafter Az9) lies on the star-forming main sequence at its stellar mass and redshift (cite: Pope2017; Pope2023). Az9 is very dust obscured - its obscured star formation rate (SFR) fraction is $0.83 \pm 0.12$, $\sim4\times$ the expected value at its stellar mass based on UV-selected galaxies (cite: Pope2017; Pope2023). Taken together, the mass-metallicity relation (cite: Tremonti2004; Sanders2021) and observations of the dust-obscured star formation rate at z$<$2.5 (cite: Whitaker2017) suggest that systems like Az9 should not be this heavily obscured. High-redshift objects have had less time to produce the metals that condense into dust (cite: Popping2017), and lower-mass systems tend to be less obscured (cite: Whitaker2017) than their more massive counterparts. This begs the question: is Az9 a typical source for its mass and redshift? And how did it end up with such a high obscuration fraction?

One way to tackle this issue is through the lens of PDR conditions. The dominant mechanism for dust production at high redshift is direct condensation in the ISM (cite: Michalowski2015; Popping2017), the rate of which depends in part on the density and temperature of the medium (cite: Hirashita2000; Asano2013). Stemming from the seminal work of (cite: Tielens1985), a series of theoretical models of photodissociation regions (PDRs) have been produced allowing observers to link observed line ratios to the physical conditions (i.e. density, incident radiation field strength, and surface temperature) of PDRs (cite: Wolfire1990; Kaufman1999; Kaufman2006). Models like these have been used to describe the PDR conditions in a range of galaxies, from nearby normal dusty galaxies (cite: Malhotra2001; Hughes2017) to IR-bright dusty massive galaxies at high redshift (cite: Bothwell2017; Gullberg2015). However, since observationally expensive tracers of the dense gas like \[O I\] or CO are required to constrain these models, the PDR conditions in low-mass systems at high redshift have not yet been extensively studied.

The total molecular gas content of Az9 is also a part of the puzzle, as it is both the fuel for star formation and the environment in which dust grains condense. Observations of massive systems suggest that as we push to higher redshifts, galaxies tend to have larger molecular gas mass to stellar mass fractions (hereafter referred to as $\mu_{gas} =$ log$_{10}[{M_{H_2}} / M_{*}]$) compared to galaxies in the local universe (cite: Tacconi2010) at the same stellar mass. Additionally, systems with higher stellar masses are generally associated with lower $\mu_{gas}$(cite: Tacconi2018). Thus, we may naively expect low-mass high-redshift systems to possess very high $\mu_{gas}$ even relative to more massive systems at the same redshift. However, observations suggest that these systems possess $\mu_{gas}$ smaller than what scaling relations lead us to expect. Molecular gas mass to stellar mass fractions in the range $\mu \sim$ 0.2 to 0.5 are found in the few low-mass ($M_{*} \lessapprox 10^{10} M_{\odot})$ high-redshift $(z \gtrapprox 2.5)$ galaxies that have been observed (cite: Saintonge2013; DZ2017; Solimano2021) compared to expected (via extrapolation) fractions around $\mu_{gas}$ $\sim$ 0.4 to 0.6 (cite: Tacconi2018) with expected scatter $\sim 0.2$ dex.

The mass assembly of galaxies is dominated by two processes: steady cold accretion (cite: Keres2005) and mergers (cite: Hopkins2010). While steady cold accretion tends to produce systems with stable disks (cite: Forster2020; Rizzo2023), mergers and counter-rotating gas inflows may disrupt galactic structure. Generally speaking, star-forming galaxies (SFGs) are less likely to host rotation-dominated disks as we push to lower stellar masses and earlier epochs (cite: Forster2020). This is an unsurprising result; low-mass systems are easier to disrupt, and the harsher conditions of the early universe increases the efficacy of disruptive processes (cite: Pillepich2019). However, a number of dynamically cold disks have still been observed in the high-redshift regime (cite: Rizzo2020; Rizzo2021; Jones2021b; Rizzo2022; Rizzo2023; Roman-Oliveira2023).

Recent work with the James Webb Space Telescope (JWST) has identified a population of relatively low-mass dusty galaxies at $z < 6$, some of which were originally misidentified as $z > 10$ galaxies (cite: Naidu2022; Barrufet2023; Nelson2023). These systems, often referred to as “HST-dark galaxies", likely represent a lower mass and SFR extension of the high redshift LIRG/ULIRG population (cite: Barrufet2023). Such galaxies are likely missing from existing HST and Spitzer-selected samples, as well as single-dish submillimeter studies (cite: Barrufet2023). As a highly obscured galaxy on the star-forming main sequence at moderately high redshift, Az9 presents a unique opportunity to study a potential member of this newly discovered population in great detail.

Intrinsically dim galaxies such as these HST-dark systems can be difficult to study without significant investments of telescope time. However, we can more easily access a subset of these systems (including Az9) by leveraging strong gravitational lensing. Depending on the distribution of matter producing such a field (the “lens"), as well as the geometry between the source, lens, and observer, this phenomenon can increase the apparent angular area subtended by a source (cite: Wambsganss1998; Peacock1999). Because gravitational lensing does not affect surface brightness (cite: Peacock1999), this phenomenon amplifies lensed sources.

In this paper, we aim to characterize the ISM conditions and molecular gas content of Az9. Our paper is organized as follows. In Section 2 we describe our new ALMA CO(4-3) and \[N II\]205$\mu$m observations and introduce existing measurements of Az9 from the literature. Our analysis is found in Section 3, including our PDR modeling methodology, our kinematic modeling process and how we convert our CO measurements into a molecular gas mass. We present our results in Section 4, including total molecular gas mass, dynamical mass, metallicity, and PDR conditions. We finish with our discussion in Section 5. Throughout this paper we assume a flat $\Lambda CDM$ cosmology with $H_0 = 69.6$ km s$^{-1}$ Mpc$^{-1}$ and a Chabrier IMF (cite: Chabrier2003).

# Observations & Data Reduction

![](az9_contours.png)

## Target

The cluster MACSJ0717.5+37.45 was imaged with the Hubble Space Telescope (HST) as part of the Hubble Frontier Fields (HFF) program. Lensing models of this cluster consistently identify a multiply lensed system at z$\sim$4 with three lensed components in the image plane (cite: Limousin2016; Diego2015; Johnson2014; Zitrin2015). Following the naming convention from (cite: Limousin2016) we call these components 5.1, 5.2, and 5.3. It is possible for a lensing configuration like this to have one image containing the full galaxy and a pair of images (with reverse parity) merging together at a line of symmetry. The 5.2 arc studied in this paper is part of a pair of merging images, its counterpart being the 5.1 image. In some cases, each member of a merging pair may not be representative of the lensed galaxy as a whole. However, in our case, we are confident we are recovering flux from a complete image of Az9 (see Section 3.4). By using existing HST, Spitzer, Large Millimeter Telescope (LMT), and Atacama Large Millimeter Array (ALMA) data (cite: Pope2023) obtained a stellar mass, star formation rate, and total IR luminosity for 5.2 (hereafter Az9). The \[C II\] line emission from Az9 has also been measured with ALMA (cite: Pope2023).

## Band 3 Observations

The CO(4-3) line ($\nu_{rest} = 461.04$ GHz) in MACSJ0717 Az9 was observed over the course of 6 nights in December 2021 with the Atacama Large Millimeter Array (ALMA) in Band 3 as a part of proposal 2021.1.00272.S (PI: Pope). The array spent time in the C-6, C-5, and C-4 configurations over the course of these observing sessions, resulting in a nominal configuration of C43-5. The primary beam (HPBW $\simeq 66^{\prime\prime}$) was centered on the 5.2 image of Az9, but also covered 5.1 which is $\sim 17^{\prime\prime}$ away. Total on source observing time was 8.67 hours. Precipitable water vapor (PWV) varied from 3.3mm to 8.3mm over the course of these observations.

The data are calibrated with the standard ALMA pipeline (Version 2021.2.0.128), which utilizes the Common Astronomy Software Applications (CASA) package (cite: CASA). We search for both continuum and line emission in these data using the CASA routine *tclean*. We determined that the JvM correction is not required for this source, as in these data the clean beam is a very good approximation to the shape and volume of the dirty beam on scales containing real emission.

### Continuum

Because the presence of strong continuum emission can potentially effect measured line characteristics, we first use *tclean* in continuum mode (excluding channels expected to contain line emission) to produce a continuum image. After interactive cleaning, we find that the continuum emission is undetected allowing us to place an upper limit on continuum emission from the image RMS of $\sigma = 0.004$ mJy/beam.

Although Az9 is expected to be dust-rich, a non-detection of the continuum emission is still consistent with existing model SEDs (see Section 3.3). With a beam size of $1.165^{\prime\prime} \times 0.629^{\prime\prime}$ with natural weighting and using the same aperture used for the CO, this corresponds to a $1\sigma$ upper limit on the continuum flux of 0.015 mJy at the frequency we measure the continuum, 94.3 GHz (i.e. $600 \mu$m).

### Line

To image the line emission, use a standard Hogbom deconvolver with Briggs weighting and use cell sizes sufficient to place 6 pixels across the restoring beam major axis for each clean attempt. We image the whole FOV, capturing both the 5.1 and 5.2 lensed images. Re-imaging with the 5.1 image at the phase center did not substantially improve its detection, so we consistently use the map with 5.2 at the phase center such that all reported values are derived from the same CLEAN map. We produce cubes using an array of different Briggs weights ranging from 0.0 to 2.0 with an 0.5 step in order to explore how various weighting schemes affect our results. Inspecting each cube leads us to select the Briggs 1.0 cube as our final science image, as this weight produces a relatively fine resolving beam that does not miss significant observed line flux when compared to natural weighting.

This final image cube has a per-channel rms of $0.052$ mJy / beam with a channel velocity width of $53.6$ km/s, the native channel width of the observations. The maximum recoverable scale for ALMA at Band 3 in the C-6 configuration is $4.11^{\prime\prime}$. As the largest scale across which we measured emission is $\sim1.5^{\prime\prime}$, our observations do not resolve out any significant emission. At the location of the 5.1 image, the sensitivity is $\sim 86\%$ of the sensitivity at the 5.2 image due to primary beam falloff.

+:-----------------------------------+:-----------:+:------------:+:-------------------:+:---------------:+:-----------------:+:-------------------:+:--------------------:+:---------------:+:---------------:+
| Component ID                       | RA          | DEC          | z                   | $S_{cont}$      | $\Delta v$ (FWHM) | $S_{line} \Delta v$ | $L^\prime_{CO(4-3)}$ | $L_{CO(4-3)}$   | Magnification   |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+
| ID                                 | J2000       | J2000        |                     | mJy             | (km/s)            | $10^{-1}$ (Jy km/s) | $\mu$                |                 |                 |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+
| *CO(4-3)*                          |                                                                                                              |                                                          |
+------------------------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+
| *($\lambda_{\rm rest} = 650\mu$m)* |                                                                                                              |                                                          |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+
| **5.2**                            | 07:17:30.71 | +37:44:33.33 | $4.2734 \pm 0.0002$ | $<0.046$        | $250 \pm 22$      | $1.80 \pm 0.27$     | $7.5 \pm 1.0$        | $1.21 \pm 0.18$ | $3.54 \pm 0.53$ |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+
| **5.1**                            | 07:17:31.18 | +37:44:48.70 | $4.2735 \pm 0.0003$ | $<0.044$        | $305 \pm 50$      | $1.63 \pm 0.46$     | $6.8 \pm 1.1$        | $1.09 \pm 0.31$ | $3.20 \pm 0.90$ |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+
| *\[N II\]205$\mu$m*                |                                                                                                              |                                                          |
+------------------------------------+--------------------------------------------------------------------------------------------------------------+----------------------------------------------------------+
| *($\lambda_{\rm rest} = 205\mu$m)* |                                                                                                              |                                                          |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+
| **5.2**                            | 07:17:30.74 | +37:44:33.60 | $4.2702 \pm 0.0002$ | $1.03 \pm 0.16$ | $150 \pm 30$      | $2.36 \pm 1.02$     | $7.5 \pm 1.0$        |                 |                 |
+------------------------------------+-------------+--------------+---------------------+-----------------+-------------------+---------------------+----------------------+-----------------+-----------------+

: MACSJ0717 Az9: Observed Quantities

Table notes: Although both images have a similar total line flux, the detection of image 5.1 is less significant because it lies further from the primary beam center, where the RMS level is higher. $S_{\text{cont}}$ upper limits are at the 3$\sigma$ level. Values to the left of the double line have not been corrected for lensing magnification. Luminosity value to the right of the double line have been corrected for lensing magnification. A primary beam correction has been applied to the values shown here.

## Band 7 Observations

Az9 was also observed in Band 7 during a single night (2022 September 14) with ALMA as part of proposal 2021.1.00272.S (PI: Pope) with the intention of measuring the \[N II\]205$\mu$m line ($\nu_{rest} = 1461.13$ GHz). The total time on source was 26 minutes, only 25$\%$ of what was requested, with 0.24mm PWV. The array was in the C43-3 configuration during these observations, resulting in a maximum recoverable scale of 5.5 $^{\prime\prime}$.

As with the CO data, these data are calibrated with the standard ALMA pipeline (Version 2021.2.0.128). Because these observations do not achieve the requested depth, we use natural weighting to maximize our sensitivity for both continuum and line imaging.

### Continuum

After cleaning in multifrequency synthesis mode, continuum flux is extracted within an elliptical aperture and the uncertainty is determined following the procedure used in (cite: Pope2023). The final continuum image has rms of $0.06$ mJy / beam and beam size 0.71$^{\prime\prime}$ $\times$ 0.44$^{\prime\prime}$.

### Line

We find relatively strong continuum emission in this band, so we first perform continuum subtraction using *uvcontsub*. We fit a 1st-order polynomial over the range 277.763 GHz - 277.279 GHz and 277.201 GHz - 275.919 GHz, corresponding to all unmasked channels not containing line emission. After cleaning in cube mode, the final line image has a per-channel rms of $0.66$ mJy / beam and beam size 0.81$^{\prime\prime}$ $\times$ 0.54$^{\prime\prime}$.

# Analysis

## CO(4-3) and \[N II\]205$\mu$m Measurements

We perform our spectral extraction in the image (i.e. unreconstructed) plane. We perform a Gaussian fit to the extracted spectrum of each lensed image within a custom aperture (used to optimally include low-surface-brightness, $\sim 2\sigma$ emission near the edge of the source) using the (cite: astropy1) software package. The CO emission is well modeled by a Gaussian in both lensed images, with a reduced chi-squared of 0.638 for the 5.2 component and 0.522 for the 5.1 component (Figure 2). The \[N II\]205$\mu$m emission in 5.2 is also modeled with a Gaussian with a reduced chi-squared of 1.41. The CO(4-3) detection is significant in both lensed images; $\sim8.1\sigma$ and $\sim4.7\sigma$ in the 5.2 and 5.1 images respectively. Binning the spectrum by a factor of 2 did not have a significant impact on the derived line intensity. The \[N II\]205$\mu$m detection is less significant at $\sim2.4\sigma$; only the 5.2 image is within the FOV. The redshifts of each CO component agree with one another within their mutual uncertainties. The \[N II\]205$\mu$m is offset from the peak in the CO (5.2 image) by $\sim 184 \pm 25$ km/s blueward. However, compared to the CO velocity at the spatial location of the \[N II\]205$\mu$m

emission, the velocity offset between the two is only $\sim60 \pm 25$ km/s. Because the low SNR of the \[N II\]205$\mu$m observations, we refrain from making any physical interpretation of this offset until a higher quality \[N II\]205$\mu$m observation can be obtained.

We provide the observed CO(4-3) and \[N II\]205$\mu$m properties of Az9 in Table 1. In addition to our measurements of line flux, we also provide the CO line luminosity in units of $L_\odot$ and the areal integrated source brightness temperature in units K km/s pc$^2$ (often referred to as L$'_{CO(4-3)}$). For the remainder of our analysis, we use our measurement of the 5.2 image as it is a more reliable detection than 5.1. We also apply a lensing magnification correction when working with intrinsic quantities. For the remainder of this work, we will refer to lensing-corrected quantities as *intrinsic* and uncorrected quantities as *observed*.

## Total Dust Mass

We place an upper limit on the dust mass of Az9 based on our Band 3 continuum ($600 \mu$m rest frame) observations. Although we detect continuum emission in our Band 7 observations (cite: Pope2023), this does not correspond to emission from the Rayleigh-Jeans tail of the rest-frame dust SED and so cannot be used to constrain the total dust content. To produce a dust mass upper limit, we use the prescription given in Section 3.4 of (cite: Solimano2021), setting our dust temperature to $T_{dust} = 25$K and using a standard dust emissivity index of $\beta$=1.8. This $T_{dust} = 25$K is the expected temperature of the cold dust component that dominates the dust mass (cite: Scoville2016; Kaasinen2019), this is not the same as the luminosity-weighted dust temperature, which cannot be used to estimate a dust mass.

Given our continuum observations are centered at a rest wavelength of $600\mu$m, we use a dust mass absorption coefficient of 0.9 cm$^2$ g$^{-1}$ (cite: Draine2001). With these parameters, we derive an intrinsic $3\sigma$ dust mass upper limit of log$_{10}[M_{dust} (M_{\odot})] < 7.73$ after correcting for lensing magnification. This dust mass is consistent with expectations from the MAGPHYS SED: log$_{10}[M_{dust,SED}] = 7.55^{+0.20}_{-0.13}$ (cite: Pope2023). The dust mass estimate from MAGPHYS is less reliable than our new upper limit, as it is constrained by data from near the peak of the dust SED rather than the Rayleigh-Jeans tail (i.e. it traced the warm rather than cold dust component).

We note that there is some debate in the literature as to whether the mass-weighted dust temperature is in fact equivalent to the luminosity-weighted dust temperature in some systems (cite: Harrington2021). If we assume a luminosity-weighted dust temperature based on the SED fits of (cite: Pope2023) ($T_{dust} = 40$K), we derive a dust mass upper limit of log$_{10}[M_{dust} (M_{\odot})] < 7.52$, also consistent with the mass estimate from those SED fits.

## CO Conversion Factors

It is standard to estimate molecular gas masses from higher-J transitions by assuming a ratio of CO(J-(J-1)) to CO(1-0) (cite: Carilli2013) since the CO(1-0) transition in high-redshift sources is often intrinsically faint and may fall into unsuitable atmospheric windows. One of the main sources of systematic uncertainty in our analysis is this conversion from CO(4-3) to CO(1-0), $r_{41}$. Recently, (cite: Castillo2023) found a range of $r_{41} = 0.63 \pm 0.44$ in a sample of 30 massive, high redshift, star-forming galaxies. For the molecular gas mass, our PDR modeling and our kinematic analysis, we use the (cite: Castillo2023) distribution.

CO line measurements are used to infer molecular gas masses via a quantity called $\alpha_{CO}$, which converts a CO(1-0) areal integrated source brightness temperature into a total molecular gas mass. A range of $\alpha_{CO}$ values have been reported in the literature, from $\alpha_{CO}=$ 0.8 $M_{\odot}$ / K km s$^{-1}$ pc$^2$ in submillimeter galaxies (SMGs) and quasars up to $\alpha_{CO}=$ 4.8 $M_{\odot}$ / K km s$^{-1}$ pc$^2$ in color-selected galaxies (CSGs) (cite: Carilli2013). $\alpha_{CO}$ can be significantly higher in some environments - values as high as $\sim 70$ have been inferred in the SMC (cite: Leroy2011). In general, the conversion factor is expected to increase as metallicity decreases because not only are fewer CO molecules able to form in low-metallicity environments, but also because CO is photodissociated to larger depths within low-metallicity clouds (cite: Bolatto2013). The typical approach is to rely on known scaling relations in order to infer the $\alpha_{CO}$ in a given system or to adopt a reasonable $\alpha_{CO}$ from the literature. The assumption of a fixed gas-to-dust ratio is also sometimes used. As CO is generally optically thick, its luminosity depends most strongly on the physical size and velocity dispersion of the emitting cloud (cite: Bolatto2013). This produces a higher $\alpha_{CO}$ in low-metallicity environments, which possess smaller CO emitting regions relative to the $H_2$ cloud size. Dust is also expected to play an important role as dustier environments are better at shielding CO from photodissociation.

We use a flat distribution of $\alpha_{CO}$ with an upper limit motivated by the kinematics of Az9 (as discussed in Section 4.4.1) and a lower limit corresponding to the QSO value from (cite: Carilli2013). Additionally, we provide constraints on metallicity and discuss the implications that these constraints gave on the $\alpha_{CO}$ of Az9 in Section 4.5.

## Source Plane Reconstruction

From the public HFF lens models,[^1] we use the non-cored model produced by (cite: Limousin2016). We find that the relative CO fluxes of the 5.1 and 5.2 images are consistent with each other given the (cite: Limousin2016) model prediction. Uncertainties in the lensing correction are propagated through our gas mass and PDR analysis.

We perform a source-plane reconstruction at our observed spectroscopic CO(4-3) redshift of $z=4.27$ with Lenstool (cite: Kneib1996; Jullo2007; Jullo2009). We apply this reconstruction on a channel-by-channel basis. We also produce an approximate channel-averaged reconstructed beam by placing the image-plane synthesized beam in the spectral and spatial center of the image. As the magnification across any individual image of Az9 is relatively constant, this produces a reasonable approximation to the true source-plane beam. Because the 5.1 image is further from the primary beam center in our data, our source-plane reconstruction of it is of lower quality than 5.2. We thus elect to perform all source-plane analysis (i.e. kinematic analysis) on the 5.2 image. The 5.2 image is 0.75$^{\prime\prime}$ away from the caustic curve in the minor axis direction in the source plane. Given this distance and the Sersic fit described below, at most $\sim10\%$ of the flux from the 5.2 could be lost beyond the caustic, which is well within the uncertainty in line flux.

To help us further understand the nature of Az9 in the source plane, we perform a 2D Sersic profile fit (cite: astropy1). We show our reconstructed source-plane image in Figure 3. We over-plot a contour corresponding to the flux level at the half-light radius obtained via 2D Sersic fitting. The results of the Sersic fit are described in Section 4.1.

## PDR Modeling

In order to model the physical conditions within PDRs, we use the PDR models of (cite: Kaufman1999; Kaufman2006) and (cite: Pound2008; Pound2023). We note that a single PDR, as modeled here, is not a realistic description of the ISM of an entire galaxy. In practice, the ISM of any galaxy is composed of a mix of gas in multiple phases. This exercise provides a simplified picture that is only broadly representative of the PDR conditions in Az9. These models are constructed as infinite plane-parallel slabs of hydrogen illuminated on one side by an incident FUV radiation field. In these models, the gas is primarily heated via photoelectrons ejected from dust grains and PAH molecules. Gas cooling arising from line emission is handled by solving for chemical and energetic equilibrium in the slab under the escape probability formalism. Even though PDR models only formally apply to an individual star-forming region, the results when applied to a whole galaxy provide a luminosity-weighted average of the PDR conditions across the galaxy as a whole, and so should still be reliable if we wish to make broad comparisons between different galaxy populations.

We apply a few correction factors to our observed quantities. Because low-J CO emission is almost certainly optically thick, we multiply the observed CO luminosities by a factor of two to account for emission from shielded cloud regions following the procedure of (cite: Hughes2017; Tadaki2019), among others. \[C II\] and FIR emission are generally optically thin, so we do not apply any optical thickness correction to these luminosities. We note that specific approaches vary throughout the literature; for example, an equivalent correction (not applied in this work) is sometimes performed by keeping the luminosity of optically thick tracers the same and instead dividing the luminosity of optically thin tracers by a factor of 2 (cite: Hashimoto2023).

Furthermore, we only want to use the \[C II\] emission arising from PDRs in this model, excluding the component arising from ionized regions. We use a relation derived by (cite: Croxall2017) (which requires only a measurement of the \[C II\] and \[N II\]205$\mu$m fluxes) to estimate the \[C II\] PDR fraction in Az9, which we use as a correction to the total \[C II\] luminosity in our PDR model. Via their equation in (cite: Croxall2017), we find that the \[C II\] PDR fraction is $f_{neutral} = 0.83$. This is comparable to \[C II\] PDR fractions found in other galaxies across redshifts, which typically range from 0.5-0.85 (cite: Hughes2017). Although there are some differences in approach from study to study, corrections like these are standard practice (cite: Hughes2017; DiazSantos2017; Tadaki2019; Leung2019; Rybak2019; Ono2022; Hashimoto2023) and should be performed if we wish to fairly compare Az9 to other sources studied in the literature. For clarity, we note that our \[N II\]205$\mu$m measurement is not used in the PDR modeling except for this \[C II\] PDR fraction calculation.

We apply a Monte Carlo approach to our PDR modeling, drawing from a normal distribution centered on the measured value of each input quantity with $\sigma$ equal to the measured uncertainty in that quantity. We use two luminosity ratios as inputs to the model: \[C II\] / CO(1-0) and \[C II\] / FIR. In the context of this PDR model, the \[N II\]205$\mu$m is used only to estimate the \[C II\] PDR fraction as described in the previous paragraph. In order to understand the systematic effects caused by our unknown $r_{41}$, we use the (cite: Castillo2023) distribution $r_{41}=0.63 \pm 0.44$ as our CO(4-3) to CO(1-0) conversion factor. One run of our PDR modeling routine is performed with the $r_{41}$ fixed at 0.63; in another, we draw from a normal distribution like we do for the observed quantities. We perform 1000 runs of the model using each of these two approaches in order to fully sample the distribution of our uncertainties. The results of this analysis are described in Section 4.3.

## Kinematic Analysis

We model the molecular gas kinematics of Az9 by applying 3D-Barolo, a 3-D tilted ring model fitting code (cite: Teodoro2015), to our source-plane reconstruction of Az9 following the approach of (cite: Pope2023). Using a forward-modeling approach, 3D-Barolo is able to robustly recover disc galaxy kinematic properties even at very low spatial resolution (cite: Teodoro2015; Teodoro2016; Rizzo2022).

We begin by using 3D-Barolo’s SEARCH module to isolate the regions in each channel containing real emission. We use a primary SNR cut of $4.5\sigma$, a secondary SNR cut of $3.5\sigma$, and we require regions to contain at least 30 pixels and contain significant flux in at least 2 consecutive channels to be included in the final mask. Once real emission has been isolated by SEARCH, we use 3D-Barolo’s primary fitting module 3DFIT. This module simulates spectral cube observations by building a model made up from multiple concentric rings, which it combines to produce a model of a rotating gaseous disk which is compared to observations after convolution with the resolving beam.

To set the number and radius of rings used in our fit, we follow the approach of (cite: Jones2021b) and use a maximum model radius of $0.8\times$(the major axis FWHM of a 2D Gaussian fit to the de-convolved CO emission) and a minimum ring radius of the beam minor axis divided by 2.5. We use a minimum model radius of 0, and a number of rings determined by dividing the maximum model radius by the ring width. We use as initial guesses for the inclination and position angle the results from modeling of the \[C II\] emission (cite: Pope2023).

For $V_{max}$ and $V_{\sigma}$, we use initial guesses of 150 km/s and 30 km/s based on initial inspection of the moment 1 and moment 2 maps. We perform a preliminary run of 3D-Barolo with the ring centers, position angle, and inclination as free parameters to estimate their values. We then perform a second run with these parameters fixed at their means from the previous run, allowing only the rotational velocity and velocity dispersion to vary, in order to determine our final fitted values. We find an inclination of 47°.6 and a position angle of 188°.9 compared to an inclination of 46°.6 and a position angle of 189°.2 in the \[C II\] (cite: Pope2023). The results of our kinematic analysis are described in Section 4.4.

## Molecular Gas Mass Uncertainties

Accurately estimating a molecular gas mass from mid or high-J CO observations is a difficult business and must be done with care. The significant systematic uncertainties in $r_{41}$ and $\alpha_{CO}$ mean that the same CO observation could be interpreted as any gas mass in a relatively wide range, based on which fiducial values one selects for these parameters. As such, we wish to conservatively quantify the total uncertainty on our gas mass estimate including these systematics over the entire range of physically reasonable guesses.

We use a 5000-run Monte Carlo approach to explore how possible combinations of reasonable estimates for $r_{41}$ and $\alpha_{CO}$ impact the inferred molecular gas mass of Az9. We first draw the value of $L'_{CO(4-3)}$ from a normal distribution based on our observed $L'_{CO(4-3)}$, observed error, and lensing correction. Then, for each sample, we draw a value for $r_{41}$ and $\alpha_{CO}$ from distributions described in the next paragraph in order to estimate $M_{\rm H_2}$.

We note that there may be additional systematics that are not propagated through this exercise. For example, it is possible that at high redshift, more extreme excitation conditions cause a lower fraction of the total molecular gas mass to be traced by the CO(1-0) line than in the local universe, making our estimate too low. However, without observations of additional CO lines, we cannot definitively address this issue.

In this exercise, we use the $r_{41} = 0.63 \pm 0.44$ found by (cite: Castillo2023), excluding any negative values. We draw from a uniform $\alpha_{CO}$ distribution $\alpha_{CO} = 0.8 - 6.1$, with the lower limit corresponding to the 0.8 value for SMGs and QSOs (cite: Carilli2013) and the upper limit motivated by our kinematic work in Section 4.4.1. As quantities such as the molecular gas fraction require a measure of stellar mass to be evaluated, we also draw stellar masses from a distribution based on the results and uncertainties of the MAGPHYS fit performed by (cite: Pope2023). The results of this analysis are described in Section 4.2.

# Results

## Source-Plane Properties

After fitting a 2D Sersic profile to our source plane reconstruction of the CO(4-3) emission, we find that it has a best-fit half-light radius of 0.4$^{\prime\prime}$, an ellipticity of 0.52, and a Sersic index of 0.79. The CO is more extended than the \[C II\], which had a half-light radius of 0.26$^{\prime\prime}$.

## Total Molecular Gas Content

We show the intrinsic molecular gas content of Az9 compared to the (cite: Tacconi2018) relations and a sample of galaxies from the literature in Figure 4. We display this in terms of molecular gas mass to stellar mass fraction (defined as $\mu_{gas} = \log_{10}[M_{H_2}/M_{*}]$) in the upper panel, and in terms of the molecular gas depletion time (defined as $t_{dep} = [M_{H_2}/SFR]$) on the lower panel.

Contours are placed around the Monte Carlo results at the 0.3, 0.6, and 0.9 levels via a kernel density estimate. We derive a total molecular gas mass of log$_{10}[M_{H_{2}}(M_{\odot})] = 9.82 \pm 0.09$ using the fiducial $r_{41}$ and median $\alpha_{CO}$. This result implies a gas fraction of $\mu_{M_{H_2}} = 0.49 \pm 0.12$ and a depletion time of $0.22 \pm 0.05$ Gyr. The error we report on these quantities is derived from measurement uncertainties only. If the systematic uncertainties from $\alpha_{CO}$ and $r_{41}$ are included (as shown in Figure 4), we find that the median inferred gas mass is log$_{10}[M_{H_{2}}(M_{\odot})] = 9.77 \pm 0.43$. The small offset between the two mass estimates occurs because the fiducial $r_{41}$ is not the median of the distribution once non-physical negative $r_{41}$ draws are removed. In terms of its overall molecular gas content, Az9 appears to have a molecular gas mass to stellar mass fraction $\sim2.0\sigma$ below, and a depletion time consistent with, the main-sequence expectation at its stellar mass and redshift. However, given the substantial systematic uncertainties involved, we do not consider the offset in molecular gas content significant.

|         Quantity         |       Unit        |          Value (Az9)           |
|:------------------------:|:-----------------:|:------------------------------:|
| log$_{10}[M_{\rm dust}]$ |    $M_{\odot}$    |            $< 7.73$            |
|  log$_{10}[M_{H_{2}}]$   |    $M_{\odot}$    |        $9.77 \pm 0.43$         |
|     $\mu_{\rm gas}$      |        $$         |        $0.49 \pm 0.12$         |
|      $t_{\rm dep}$       |        Gyr        |        $0.22 \pm 0.05$         |
| log$_{10}[n_{H}]$ (PDR)  |     cm$^{-3}$     |        $4.80 \pm 0.39$         |
|  log$_{10}[G_0]$ (PDR)   |      Habing       |        $2.83 \pm 0.26$         |
|          $T_s$           |         K         |         $186 \pm 116$          |
|      $V_{\rm rot}$       |       km/s        |          $148 \pm 33$          |
|       $V_{\sigma}$       |       km/s        |          $32 \pm 10$           |
|        $V/\sigma$        |                   |         $4.6 \pm 1.7$          |
|    $M_{\rm dyn,disk}$    |    $M_{\odot}$    | $(1.39\pm0.31) \times 10^{10}$ |
|           $Z$            |  12 + Log\[O/H\]  |        $7.96 \pm 0.44$         |
|    $r_{1/2}$ (Sersic)    | $^{\prime\prime}$ |             $0.40$             |

: Intrinsic ISM Properties of Az9

Table notes: All quantities have been corrected for lensing magnification.

![](az9_pdr.png)

## Gas Conditions in PDRs

In Figure 5, we show the results of our best-fit PDR model. We plot the position in radiation field / density space of Az9 alongside a sample of galaxies from the literature, including GOALS LIRGs and sub-LIRGS, (cite: DS2017), normal SFGs (cite: Hughes2017), and high-z dusty star forming galaxies (cite: Gullberg2015). We also show AzTEC-1 (cite: Tadaki2019), a galaxy at comparable redshift to Az9 but with a much higher mass and SFR. We note that, with the exception of the SPT sources, the literature points shown on this plot have been subject to identical corrections as those we apply to Az9 (i.e. doubling the CO luminosity and correcting for the \[C II\] PDR fraction). Additionally, the GOALS sources use \[O I\] 63 $\mu m$ as their dense gas tracer rather than CO. We show our results for Az9 (maroon) in the form of 2 sets of density contours: one set (dashed) representing the distribution of results produced assuming a variable $r_{41}$, and one set (solid) representing the results assuming a fixed $r_{41} =0.63$. Under the assumption of a fixed $r_{41} = 0.63$, we find that Az9 has a hydrogen density log\[$n_H$ $cm^{-3}$\] = $4.80 \pm 0.39$ and a radiation field strength log\[G$_0$ Habing\] = $2.83 \pm 0.26$. Using a normally distributed $r_{41} = 0.63 \pm 0.44$, we find log\[$n_H$ $cm^{-3}$\] = $4.70 \pm 0.72$ and log\[G$_0$ Habing\] = $2.73 \pm 0.91$

Regardless of how we handle $r_{41}$, Az9 appears to host PDR conditions consistent with the local normal star-forming galaxies studied in the VALES program (cite: Hughes2017), who derived PDR conditions in their sample using measurements similar to those used in our study. The PDR conditions in Az9 are less similar but still broadly comparable to those found in AzTEC-1, with a somewhat less intense radiation field - sensible, given that AzTEC-1 is a massive ($M_{*} \sim 10^{11} M_{\odot}$) galaxy undergoing an aggressive starburst (cite: Tadaki2018). In fact, it is curious that these two systems, with star formation rate surface densities varying by a factor of $\sim 10$ ($\Sigma_{SFR}$ $\sim$ 2.5 $M_{\odot}$/yr/kpc$^2$ for Az9, (cite: Pope2023) and $\Sigma_{SFR}$ $\sim$ 270 $M_{\odot}$/yr/kpc$^2$ for AzTEC-1, (cite: Sharda2019)) have similar PDR conditions. Although it is in agreement in with the GOALS sources in radiation field terms, Az9 is well offset from them in density space, possibly due to the use of different PDR tracers.

The PDR models also estimate a surface temperature of $T_s = 186 \pm 116$ K in the variable $r_{41}$ case. This is an upper limit to the gas temperature in PDRs as the surface gas most directly exposed to radiation will be the hottest.

## Kinematic Properties

![](az9_momMaps.png)

We show the kinematic maps (moment 0, moment 1 and moment 2 in the data, model, and residuals) produced by 3D-Barolo in Figure 6. With about $\sim 2$ beams resolving Az9 along the axis of rotation (similar to the resolution achieved by (cite: Jones2021b; Pope2023)), Az9 is decently fit by a tilted-ring model and is consistent with a rotating system. 3D-Barolo also provides the best-fit velocity dispersion and circular velocity within each model ring. The distribution of these values as a function of ring outer radius (i.e. the rotation curve of our model of Az9) is presented in Figure 7. The shape of the rotation curve is broadly consistent with the shape of other rotation curves derived for rotating disks observed at low spatial resolution (cite: Teodoro2015). We find a mean circular velocity $V_{rot}$ = $148\pm32$ km/s in the outer 5 rings (where the velocity profile is approximately flat) and mean velocity dispersion $V_{\sigma}$ = $32\pm10$ km/s across the source. The value of $V/\sigma$ for CO-emitting gas in Az9 is $4.6 \pm 1.7$, implying that Az9 is a rotationally dominated system. This result is consistent with the $V/\sigma$ found for the \[C II\] $(5.3 \pm 3.6)$ in the same system (cite: Pope2023). These derived quantities are not sensitive within uncertainty to initial guesses of $V_{rot}$ and $V_{\sigma}$. In some cases, kinematic analyses performed at low spatial resolution can misclassify mergers as disks (cite: Rizzo2022). However, following (cite: Pope2023), the lack of a multiply-peaked velocity profile in our data lends credence to the disk interpretation.

![](az9_radProf.png)

### Dynamical Mass

In order to estimate the dynamical mass of Az9 assuming a disk-like geometry, we use an equation first developed by (cite: Wang2013) and commonly used throughout the literature (cite: Capak2015; Cassata2020): $M_{dyn, disk}[M_{\odot}] = 1.16 \times 10^{5} V_{cir}^2 D$ where $D$ is the disk diameter in kpc and $V_{cir}$ is the circular velocity of the gas disk in km$/$s. Using twice our half-light radius $R_{1/2}=2.74$ kpc as the diameter and our radially-averaged rotational velocity $V_{rot}$=148 $\pm$ 32 km/s, we find a dynamical mass of $M_{dyn,disk} = 1.39 \pm 0.31 \times$ 10$^{10}$ $M_{\odot}$.

Some systematic uncertainties must be considered when interpreting this value. Simulations of massive disk galaxies suggest that gradients in the turbulent pressure at large radii ($\gtrapprox 3$kpc) cause the observed circular velocity to fall off relative to the spherically symmetric zero-pressure expectation $V_{c} = \sqrt{G M_{enc} / r}$ (cite: Wellons2020), which may bias dynamical masses low by up to $\sim40\%$, and is more important at higher masses and redshifts. Beam smearing, which causes the observed velocity gradient to be reduced relative to its intrinsic value, is common in low-resolution observations like those we present here. As it causes rotational velocity to be confused with velocity dispersion, it may reduce the derived $V/\sigma$ and dynamical mass if not handled properly (cite: Bukert2016; Wuyts2016; Molina2019). We do not believe either phenomenon has a significant impact on our results; turbulent pressure support is only a major contributor to disk structure for thick disks or systems with a low $V/\sigma$ (cite: Molina2019), and 3D-Barolo accounts for beam smearing through its convolution step (cite: Teodoro2015) and fully 3-D approach.

### Dynamical Constraints on $\alpha_{CO}$

The highest $\alpha_{CO}$ possible for Az9 given its dynamical mass (assuming it contains *no neutral gas or dark matter*, only stars and molecular gas, and using $r_{41} = 0.63$) is $\alpha_{CO} = 6.1 \pm 1.6$ $M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$. The true value of $\alpha_{CO}$ is likely lower than the value quoted above, as Az9 is certain to contain some amount of dark matter and neutral gas. As such, for the Monte Carlo gas mass analysis described in Section 3.8, we set the upper limit on $\alpha_{CO}$ to $6.1$. Although the neutral gas mass fraction is uncertain (and often neglected in this sort of analysis) a dark matter mass fraction on the order of $\sim 20 \%$ is commonly quoted in the literature (cite: Hodge2012; Cassata2020). Interestingly, our $\alpha_{CO}$ upper limit becomes consistent with the classical $\alpha_{CO} = 3.8$ used by (cite: Tacconi2018) for normal star-forming galaxies once adjusted down by $\sim 20 \%$.

## Metallicity Constraints

Alongside the existing measurement of the \[C II\] line in Az9, our new measurement of the \[N II\]205$\mu$m line allows us to estimate the gas-phase metallicity of this system. (cite: Croxall2017) find that the \[C II\]/\[N II\]205$\mu$m ratio can be used as a rough metallicity tracer and calibrate a fitting function on the (cite: Pilyugin2005) metallicity scale: $$\textrm{12+log$_{10}$[O/H]}_{PT05} = 8.97 - 0.043 \times \textrm{[C II]} / \textrm{[N II}]$$ Using this relation we find $\textrm{12+log$_{10}$[O/H]}_{PT05} = 7.96 \pm 0.44$. The high uncertainty here is driven by the low signal-to-noise of our observation of the \[N II\]205$\mu$m line. This is consistent with the metallicity one would estimate via the mass-metallicity relation at *z*=4.3 . Assuming this metallicity, we estimate the $\alpha_{CO}$ using the recipe developed by (cite: Genzel2015): $$\alpha_{CO}^Z = \alpha_{CO,MW} \times 10^{-1.27(12+\log(O/H)_{PP04}-8.67)}$$ where $\alpha_{CO,MW}$ is the Milky Way CO-to-H$_{2}$ conversion factor including a correction factor for helium, typically taken to be 4.36 $M_{\odot}$ $/$ K km s$^{-1}$ pc$^2$ (cite: Strong1996). We obtain the very high value of $\alpha_{CO} = 34$ $M_{\odot}$ / K km s$^{-1}$ pc$^2$ for Az9 using this method. Using this $\alpha_{CO}$ and the (cite: Castillo2023) value $r_{41}=0.63$ for the 4-to-1 conversion factor, we calculate a molecular gas mass of $M_{H2}$ = $8.2 \pm 1.2$ $\times 10^{10}$ $M_{\odot}$. This is unphysical, as it is much higher than the total dynamical mass of the system regardless of the assumed geometry. Additionally, assuming $\alpha_{CO} = 34$, an extremely high $r_{41} = 3.7$ would be required in order to produce a molecular hydrogen mass equal to the dynamical mass. The result that locally calibrated fitting functions for $\alpha_{CO}$ may not be appropriate in high-redshift galaxies is not new (cite: Narayanan2012; DZ2017) and this Az9 result confirms that more work must be done to understand the conversion factor in high z, low mass galaxies.

# Discussion

Combining our new CO (tracing dense molecular gas) and \[N II\]205$\mu$m (an important cooling line for ionized regions) measurements of Az9 with existing measurements of the \[C II\] (an important cooling line for PDRs) provides us with insight into the nature of multiple gas phases within a low mass dusty galaxy at $z=4.27$. Our observations paint a picture of a system that - despite its high obscured SFR - is surprisingly “normal", with PDR conditions comparable to local normal dusty galaxies and kinematics suggesting a dynamically cold disk. A system with “normal" kinematics and ISM properties like Az9 should be able to sustain them for an extended period, which perhaps suggests that Az9 is representative of a larger low-mass galaxy population heretofore inaccessible without the benefit of gravitational lensing.

![](az9_fgas_taccDist.png)

## PDR Conditions: Evidence of a “Normal" System?

We can gain some additional insight into how Az9 compares to other populations by looking at the molecular gas content of Az9 relative to the (cite: Tacconi2018) relation, log$_{10}$\[$\mu_{H_2}$/$\mu_{H_2,tacc}$\], in the context of other ISM properties. In Figure 7, we show log$_{10}$\[$\mu_{H_2}$/$\mu_{H_2,tacc}$\] as a function of log$_{10}$\[$G_0$/$n_H$\] for Az9 alongside the same sample of galaxies we showed in Figure 4. Az9 has ISM conditions and molecular gas mass to stellar mass fraction in log$_{10}$\[$G_0$/$n_H$\] space that are consistent with VALES (cite: Jones2021b). This suggests that a relatively “normal” $\alpha_{CO}$ is appropriate: if for example we had found that Az9 possessed an extremely strong internal radiation field, radiation would be able to drive photodissociation deeper into a given component cloud and it would make sense to use a higher $\alpha_{CO}$. However, in terms of its PDR conditions, Az9 appears broadly similar to local universe dusty star-forming galaxies - a comparable $\alpha_{CO}$ is probably reasonable.

The PDR conditions of Az9 are not only interesting in the context of $\alpha_{CO}$ - they also represent the first time these properties have been measured for a galaxy with log\[$M_{*} (M_{\odot})$\] $\lesssim 10$ at high redshift. Az9 appears to possess PDR physical conditions quite similar to those observed in a sample of local-universe dusty star forming galaxies, despite those galaxies hosting somewhat higher stellar masses (log$_{10}[M_{*} (M_{\odot})] = 9.79 - 11.2$ compared to log$_{10}[M_{*} (M_{\odot})] = 9.33$ in Az9) and significantly lower specific star formation rates (sSFR(Gyr$^{-1}$) $= 0.05 - 4.03$ compared to sSFR(Gyr$^{-1}$) $= 14.15$ in Az9) (cite: Hughes2017; Villanueva2017).

One explanation for the surprising similarity between Az9 and the VALES local-universe sources is a picture in which the nature of the ISM in individual dusty star-forming clumps is broadly similar in all systems undergoing “normal" star formation. (cite: DiazSantos2017) suggest that the youngest PDRs account for the highest G/n ratios. Young PDRs host younger stars which produce more intense radiation radiation fields, and are likely more compact as they have had less time to expel their dusty envelopes. In this model, the high G/n ratios typical of starbursts are due to the presence of many such PDRs, individually short-lived but constantly replenished as they are triggered by mergers.

In contrast, the more typical PDR conditions of Az9 suggest a more gentle, extended history of dust-obscured star formation rather than a recent or ongoing starburst. This in turn suggests that the normal dust-obscured star forming phase is reasonably long for galaxies like Az9. If so, Az9 could be representative of a more widespread population of low-mass main-sequence systems - with an intrinsic 1.1mm flux of merely $S_{1.1mm} \sim 0.1$ mJy (cite: Pope2017), any similar unlensed systems would be well below the detection threshold of all existing blank-field single-dish surveys (cite: Hodge2013; Geach2017; Stach2019) and all but the deepest (and therefore smallest) interferometric (cite: Franco2018) surveys. We can further test the idea that systems like Az9 are widespread with deep observations from LMT/TolTEC.

## Dust Content

We derive a dust mass upper limit of log$_{10}[M_{\rm dust}] < 7.73$, consistent with the dust mass estimated via SED fitting in (cite: Pope2023) as well as expectations from semi-analytical models (cite: Popping2017). The gas-to-dust ratio (GDR) is consistent with GDRs seen in local universe galaxies of comparable metallicity; we find Az9 has a GDR lower limit of log$_{10}[GDR_{Az9,lower}] \geq 2.04$ compared to the expected (assuming the low-metallicity branch) log$_{10}[GDR_{expected}] = 2.92 \pm 1.28$ (cite: Remy2014).

It is also worthwhile to consider how Az9 is so heavily obscured so early on in the history of the universe. At high redshift, condensation of metals on to existing small grains in the cold neutral medium (CNM) or molecular clouds is likely to be the predominant dust formation channel (cite: Draine2009; Michalowski2015; Popping2017). The interstellar dust population is also dominated by grains formed in molecular clouds in systems like the Milky Way (cite: Zhukovska2008). Using a common expression for the dust accretion timescale in the CNM (cite: Asano2013; Triani2020):

$$\begin{equation}
\label{eq:tau_acc}
\tau_{\rm acc} =  2 \times 10^7 \times \bigg(\frac{n_{\rm mol}}{100
  \,\rm{cm}^{-3}}\bigg)^{-1}\,\bigg(\frac{T_{dust}}{50\,\rm{K}}\bigg)^{-1/2}\,\bigg(\frac{Z}{Z_{\odot}}\bigg)^{-1} \text{[yr]}
\end{equation}$$

and the $H_{2}$ density we found in our PDR model $n_{mol} \sim 10^{4.8}$ cm$^{-3}$, $T_{dust} = 40$K, and our metallicity 12 + log$_{10}$\[O/H\] $\sim$ $8$, we find Az9 has a dust growth timescale $\tau_{acc} \approx 0.2$ Myr. This is quite rapid, but timescales on the order of $10^5$yr is reasonable some situations, such as the depletion of metal ions onto small grains in normal HI clouds (cite: Draine2004; Draine2009). The majority of this growth is expected to occur on the surface of small grains, as these grains provide a significant fraction of the dust total surface area and are likely to be negatively charged (cite: Draine2009). Coagulation of small grains may also be an important process in dense regions of the ISM (cite: Hirashita2023). Although both our PDR results and this dust coagulation timescale are uncertain, we can conclude qualitatively that the presence of dense PDRs in Az9 may allow for the rapid assembly of dust mass in these small dense regions.

With a dynamical timescale of roughly $\sim30$Myr (calculated as $R/V$), this suggests that in its current state, Az9 is able to assemble dust mass in its densest ISM regions more rapidly than that dust can be transported throughout its structure. Thus, we suggest that the high obscuration fraction of Az9 might be due to the presence of clumpy dusty regions strongly associated with dense gas and ongoing star formation. This is an idea that could be tested with future high-resolution ALMA data.

# Summary

In this work, we present new ALMA observation of the CO(4-3) and \[N II\] lines in the z=4.273 low-mass star-forming galaxy MACSJ0717_Az9. The main conclusions of this paper are as follows:

- We find that Az9 is moderately deficient in molecular gas compared to the existing molecular gas mass to stellar mass fraction scaling relation, with a molecular gas mass of log$_{10}[M_{H_{2}} ] = 9.77 \pm 0.43$ and molecular gas mass to stellar mass fraction $\mu_{\rm gas} = 0.49 \pm 0.12$. This is consistent with other low-mass systems observed at high redshift. The strength of this conclusion is limited by the systematic uncertainties on $\alpha_{CO}$ and $r_{41}$, which are poorly unconstrained at high redshift and low stellar mass.

- Based on observations of the CO(4-3) line, we find that Az9 is a rotationally-dominated system, with $V_{rot} = 148 \pm 33$ km/s and $V_{disp} = 32 \pm 10$ km/s. These observations trace a different gas phase than previous work and provide strong evidence that Az9 hosts a stable molecular disk.

- Az9 has PDRdd conditions similar to local normal dusty star-forming galaxies, with a mean hydrogen density log$_{10}$\[$n_H$ $cm^{-3}$\] = $4.80 \pm 0.39$ and a mean radiation field strength log$_{10}$\[G$_0$ Habing\] = $2.83 \pm 0.26$ in these regions. This is the first measurement of PDR conditions in a galaxy with log$_{10}$\[$M_{*} (M_{\odot})$\] $< 10$ at z $>$ 4.

- Assuming an $r_{41}$ of 0.63, we find that the dynamical mass favors an upper limit on $\alpha_{CO}$ of 6.1 assuming a disk-like geometry. This suggests that $\alpha_{CO}$ values based on extrapolating scaling relations from more massive, local galaxies may not be appropriate for galaxies like Az9.

- Based on our new observations of the \[N II\] 205 $\mu$m line, we estimate the metallicity of Az9 to be 12 + log$_{10}$\[O/H\]$_{PTO5}$ = 7.96 $\pm$ 0.44. The high uncertainty on this value is driven by the low signal-to-noise of our \[N II\] 205 $\mu$m data.

- We find that Az9 has a short dust growth timescale. This implies that Az9 is able to assemble dust mass in its ISM more rapidly than that dust can be transported throughout its structure, resulting in a clumpy dust geometry. It implies that any metals injected into its dense ISM are very quickly depleted onto the surface of dust grains.

In most respects, Az9 appears to be a fairly normal low-mass star forming galaxy for its redshift. Az9 is mainly notable for two reasons: (1) it has a high obscured star formation fraction, and (2) it appears to be have molecular gas content somewhat below what might be expected based on extrapolating existing scaling relations. Deeper observations of dust continuum emission in the Rayleigh-Jeans tail and a stronger constraint on the metallicity of Az9 through rest-frame optical lines would be excellent next steps, allowing us to understand how Az9 assembled its metal content in significantly more detail.

Az9 hosts a dynamically cold, stable disk and has ISM conditions comparable to local normal star-forming galaxies, suggesting that it can maintain its current dust-obscured phase for an extended period. If so, this suggests that Az9 may be representative of a more numerous population of low-mass dust-obscured galaxies at $z\sim4$. Future mm/sub-mm surveys with $3\sigma$ depths better than $\sim$0.1 mJy such as the LMT/TolTEC UDS survey (cite: Montana2019) may be able to detect more systems like Az9, though with current instruments gravitational lensing is the only practical way to study these systems in detail.

The authors would like to thank the NAASC data reduction training team, who provided valuable assistance during the data reduction process. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00272.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Facilities

ALMA, HST(WFC3), LMT(AzTEC)

# Software

astropy (cite: astropy1),

natexlab

(ref: Armus2009) Armus, L., Mazzarella, J. M., Evans, A. S., et al. 2009, PASP, 121, 559, doi: [`10.1086/600092`](http://doi.org/10.1086/600092)

(ref: Asano2013) Asano, R. S., Takeuchi, T. T., Hirashita, H., & Inoue, A. K. 2013, Earth, Planets and Space, 65, 213, doi: [`10.5047/eps.2012.04.014`](http://doi.org/10.5047/eps.2012.04.014)

(ref: astropy1) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Barger1998) Barger, A. J., Cowie, L. L., Sanders, D. B., et al. 1998, Nature, 394, 248, doi: [`10.1038/28338`](http://doi.org/10.1038/28338)

(ref: Barrufet2023) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, MNRAS, 522, 449, doi: [`10.1093/mnras/stad947`](http://doi.org/10.1093/mnras/stad947)

(ref: Birkin2021) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926, doi: [`10.1093/mnras/staa3862`](http://doi.org/10.1093/mnras/staa3862)

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: Bothwell2017) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825, doi: [`10.1093/mnras/stw3270`](http://doi.org/10.1093/mnras/stw3270)

(ref: Bukert2016) Burkert, A., Förster Schreiber, N. M., Genzel, R., et al. 2016, ApJ, 826, 214, doi: [`10.3847/0004-637X/826/2/214`](http://doi.org/10.3847/0004-637X/826/2/214)

(ref: Rivera2018) Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56, doi: [`10.3847/1538-4357/aacffa`](http://doi.org/10.3847/1538-4357/aacffa)

(ref: Capak2015) Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455, doi: [`10.1038/nature14500`](http://doi.org/10.1038/nature14500)

(ref: Carilli2013) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: Cassata2020) Cassata, P., Liu, D., Groves, B., et al. 2020, ApJ, 891, 83, doi: [`10.3847/1538-4357/ab7452`](http://doi.org/10.3847/1538-4357/ab7452)

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: Croxall2017) Croxall, K. V., Smith, J. D., Pellegrini, E., et al. 2017, ApJ, 845, 96, doi: [`10.3847/1538-4357/aa8035`](http://doi.org/10.3847/1538-4357/aa8035)

(ref: DZ2017) Dessauges-Zavadsky, M., Zamojski, M., Rujopakarn, W., et al. 2017, A&A, 605, A81, doi: [`10.1051/0004-6361/201628513`](http://doi.org/10.1051/0004-6361/201628513)

(ref: Teodoro2015) Di Teodoro, E. M., & Fraternali, F. 2015, MNRAS, 451, 3021, doi: [`10.1093/mnras/stv1213`](http://doi.org/10.1093/mnras/stv1213)

(ref: Teodoro2016) Di Teodoro, E. M., Fraternali, F., & Miller, S. H. 2016, A&A, 594, A77, doi: [`10.1051/0004-6361/201628315`](http://doi.org/10.1051/0004-6361/201628315)

(ref: DiazSantos2017) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017a, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: DS2017) —. 2017b, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: Diego2015) Diego, J. M., Broadhurst, T., Zitrin, A., et al. 2015, MNRAS, 451, 3920, doi: [`10.1093/mnras/stv1168`](http://doi.org/10.1093/mnras/stv1168)

(ref: Draine2004) Draine, B. T. 2004, in The Cold Universe, 213, doi: [`10.48550/arXiv.astro-ph/0304488`](http://doi.org/10.48550/arXiv.astro-ph/0304488)

(ref: Draine2009) Draine, B. T. 2009, in Astronomical Society of the Pacific Conference Series, Vol. 414, Cosmic Dust - Near and Far, ed. T. Henning, E. Grün, & J. Steinacker, 453, doi: [`10.48550/arXiv.0903.1658`](http://doi.org/10.48550/arXiv.0903.1658)

(ref: Forster2020) Förster Schreiber, N. M., & Wuyts, S. 2020, ARA&A, 58, 661, doi: [`10.1146/annurev-astro-032620-021910`](http://doi.org/10.1146/annurev-astro-032620-021910)

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152, doi: [`10.1051/0004-6361/201832928`](http://doi.org/10.1051/0004-6361/201832928)

(ref: Castillo2023) Frias Castillo, M., Hodge, J., Rybak, M., et al. 2023, ApJ, 945, 128, doi: [`10.3847/1538-4357/acb931`](http://doi.org/10.3847/1538-4357/acb931)

(ref: Geach2017) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789, doi: [`10.1093/mnras/stw2721`](http://doi.org/10.1093/mnras/stw2721)

(ref: Genzel2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20, doi: [`10.1088/0004-637X/800/1/20`](http://doi.org/10.1088/0004-637X/800/1/20)

(ref: Gullberg2015) Gullberg, B., De Breuck, C., Vieira, J. D., et al. 2015, MNRAS, 449, 2883, doi: [`10.1093/mnras/stv372`](http://doi.org/10.1093/mnras/stv372)

(ref: Harrington2021) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: Hashimoto2023) Hashimoto, T., Inoue, A. K., Sugahara, Y., et al. 2023, ApJ, 952, 48, doi: [`10.3847/1538-4357/acdd5c`](http://doi.org/10.3847/1538-4357/acdd5c)

(ref: Hirashita2000) Hirashita, H. 2000, PASJ, 52, 585, doi: [`10.1093/pasj/52.4.585`](http://doi.org/10.1093/pasj/52.4.585)

(ref: Hirashita2023) Hirashita, H., & Chen, C.-C. 2023, MNRAS, 526, 4710, doi: [`10.1093/mnras/stad3077`](http://doi.org/10.1093/mnras/stad3077)

(ref: Hodge2012) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11, doi: [`10.1088/0004-637X/760/1/11`](http://doi.org/10.1088/0004-637X/760/1/11)

(ref: Hodge2013) Hodge, J. A., Karim, A., Smail, I., et al. 2013, ApJ, 768, 91, doi: [`10.1088/0004-637X/768/1/91`](http://doi.org/10.1088/0004-637X/768/1/91)

(ref: Hopkins2010) Hopkins, P. F., Bundy, K., Croton, D., et al. 2010, ApJ, 715, 202, doi: [`10.1088/0004-637X/715/1/202`](http://doi.org/10.1088/0004-637X/715/1/202)

(ref: Hughes2017) Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, A&A, 602, A49, doi: [`10.1051/0004-6361/201629588`](http://doi.org/10.1051/0004-6361/201629588)

(ref: Johansson2012) Johansson, D., Horellou, C., Lopez-Cruz, O., et al. 2012, A&A, 543, A62, doi: [`10.1051/0004-6361/201117918`](http://doi.org/10.1051/0004-6361/201117918)

(ref: Johnson2014) Johnson, T. L., Sharon, K., Bayliss, M. B., et al. 2014, ApJ, 797, 48, doi: [`10.1088/0004-637X/797/1/48`](http://doi.org/10.1088/0004-637X/797/1/48)

(ref: Jones2021b) Jones, G. C., Vergani, D., Romano, M., et al. 2021, MNRAS, 507, 3540, doi: [`10.1093/mnras/stab2226`](http://doi.org/10.1093/mnras/stab2226)

(ref: Jullo2009) Jullo, E., & Kneib, J. P. 2009, MNRAS, 395, 1319, doi: [`10.1111/j.1365-2966.2009.14654.x`](http://doi.org/10.1111/j.1365-2966.2009.14654.x)

(ref: Jullo2007) Jullo, E., Kneib, J. P., Limousin, M., et al. 2007, New Journal of Physics, 9, 447, doi: [`10.1088/1367-2630/9/12/447`](http://doi.org/10.1088/1367-2630/9/12/447)

(ref: Kaasinen2019) Kaasinen, M., Scoville, N., Walter, F., et al. 2019, ApJ, 880, 15, doi: [`10.3847/1538-4357/ab253b`](http://doi.org/10.3847/1538-4357/ab253b)

(ref: Kaufman2006) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ, 644, 283, doi: [`10.1086/503596`](http://doi.org/10.1086/503596)

(ref: Kaufman1999) Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman, M. L. 1999, ApJ, 527, 795, doi: [`10.1086/308102`](http://doi.org/10.1086/308102)

(ref: Keres2005) Kereš, D., Katz, N., Weinberg, D. H., & Davé, R. 2005, MNRAS, 363, 2, doi: [`10.1111/j.1365-2966.2005.09451.x`](http://doi.org/10.1111/j.1365-2966.2005.09451.x)

(ref: Kneib1996) Kneib, J. P., Ellis, R. S., Smail, I., Couch, W. J., & Sharples, R. M. 1996, ApJ, 471, 643, doi: [`10.1086/177995`](http://doi.org/10.1086/177995)

(ref: Leroy2011) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12, doi: [`10.1088/0004-637X/737/1/12`](http://doi.org/10.1088/0004-637X/737/1/12)

(ref: Leung2019) Leung, T. K. D., Riechers, D. A., Baker, A. J., et al. 2019, ApJ, 871, 85, doi: [`10.3847/1538-4357/aaf860`](http://doi.org/10.3847/1538-4357/aaf860)

(ref: Draine2001) Li, A., & Draine, B. T. 2001, ApJ, 554, 778, doi: [`10.1086/323147`](http://doi.org/10.1086/323147)

(ref: Limousin2016) Limousin, M., Richard, J., Jullo, E., et al. 2016, A&A, 588, A99, doi: [`10.1051/0004-6361/201527638`](http://doi.org/10.1051/0004-6361/201527638)

(ref: Magdis2012) Magdis, G. E., Daddi, E., Sargent, M., et al. 2012, ApJL, 758, L9, doi: [`10.1088/2041-8205/758/1/L9`](http://doi.org/10.1088/2041-8205/758/1/L9)

(ref: Malhotra2001) Malhotra, S., Kaufman, M. J., Hollenbach, D., et al. 2001, ApJ, 561, 766, doi: [`10.1086/323046`](http://doi.org/10.1086/323046)

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Michalowski2015) Michałowski, M. J. 2015, A&A, 577, A80, doi: [`10.1051/0004-6361/201525644`](http://doi.org/10.1051/0004-6361/201525644)

(ref: Molina2019) Molina, J., Ibar, E., Villanueva, V., et al. 2019, MNRAS, 482, 1499, doi: [`10.1093/mnras/sty2577`](http://doi.org/10.1093/mnras/sty2577)

(ref: Montana2019) Montaña, A., Chávez Dagostino, M., Aretxaga, I., et al. 2019, Mem. Soc. Astron. Italiana, 90, 632

(ref: Moster2013) Moster, B. P., Naab, T., & White, S. D. M. 2013, MNRAS, 428, 3121, doi: [`10.1093/mnras/sts261`](http://doi.org/10.1093/mnras/sts261)

(ref: Naidu2022) Naidu, R. P., Oesch, P. A., Setton, D. J., et al. 2022, arXiv e-prints, arXiv:2208.02794, doi: [`10.48550/arXiv.2208.02794`](http://doi.org/10.48550/arXiv.2208.02794)

(ref: Narayanan2012) Narayanan, D., Bothwell, M., & Davé, R. 2012, MNRAS, 426, 1178, doi: [`10.1111/j.1365-2966.2012.21893.x`](http://doi.org/10.1111/j.1365-2966.2012.21893.x)

(ref: Nelson2023) Nelson, E. J., Suess, K. A., Bezanson, R., et al. 2023, ApJL, 948, L18, doi: [`10.3847/2041-8213/acc1e1`](http://doi.org/10.3847/2041-8213/acc1e1)

(ref: Ono2022) Ono, Y., Fujimoto, S., Harikane, Y., et al. 2022, ApJ, 941, 74, doi: [`10.3847/1538-4357/ac9ea6`](http://doi.org/10.3847/1538-4357/ac9ea6)

(ref: Peacock1999) Peacock, J. A. 1999, Cosmological Physics

(ref: Pillepich2019) Pillepich, A., Nelson, D., Springel, V., et al. 2019, MNRAS, 490, 3196, doi: [`10.1093/mnras/stz2338`](http://doi.org/10.1093/mnras/stz2338)

(ref: Pilyugin2005) Pilyugin, L. S., & Thuan, T. X. 2005, ApJ, 631, 231, doi: [`10.1086/432408`](http://doi.org/10.1086/432408)

(ref: Pope2017) Pope, A., Montaña, A., Battisti, A., et al. 2017, ApJ, 838, 137, doi: [`10.3847/1538-4357/aa6573`](http://doi.org/10.3847/1538-4357/aa6573)

(ref: Pope2023) Pope, A., McKinney, J., Kamieneski, P., et al. 2023, ApJL, 951, L46, doi: [`10.3847/2041-8213/acdf5a`](http://doi.org/10.3847/2041-8213/acdf5a)

(ref: Popping2017) Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152, doi: [`10.1093/mnras/stx1545`](http://doi.org/10.1093/mnras/stx1545)

(ref: Pound2008) Pound, M. W., & Wolfire, M. G. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 394, Astronomical Data Analysis Software and Systems XVII, ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654

(ref: Pound2023) Pound, M. W., & Wolfire, M. G. 2023, AJ, 165, 25, doi: [`10.3847/1538-3881/ac9b1f`](http://doi.org/10.3847/1538-3881/ac9b1f)

(ref: Remy2014) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31, doi: [`10.1051/0004-6361/201322803`](http://doi.org/10.1051/0004-6361/201322803)

(ref: Reichers2010a) Riechers, D. A., Carilli, C. L., Walter, F., & Momjian, E. 2010, ApJL, 724, L153, doi: [`10.1088/2041-8205/724/2/L153`](http://doi.org/10.1088/2041-8205/724/2/L153)

(ref: Rizzo2022) Rizzo, F., Kohandel, M., Pallottini, A., et al. 2022, A&A, 667, A5, doi: [`10.1051/0004-6361/202243582`](http://doi.org/10.1051/0004-6361/202243582)

(ref: Rizzo2021) Rizzo, F., Vegetti, S., Fraternali, F., Stacey, H. R., & Powell, D. 2021, MNRAS, 507, 3952, doi: [`10.1093/mnras/stab2295`](http://doi.org/10.1093/mnras/stab2295)

(ref: Rizzo2020) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201, doi: [`10.1038/s41586-020-2572-6`](http://doi.org/10.1038/s41586-020-2572-6)

(ref: Rizzo2023) Rizzo, F., Roman-Oliveira, F., Fraternali, F., et al. 2023, arXiv e-prints, arXiv:2303.16227, doi: [`10.48550/arXiv.2303.16227`](http://doi.org/10.48550/arXiv.2303.16227)

(ref: Roman-Oliveira2023) Roman-Oliveira, F., Fraternali, F., & Rizzo, F. 2023, MNRAS, 521, 1045, doi: [`10.1093/mnras/stad530`](http://doi.org/10.1093/mnras/stad530)

(ref: Rybak2019) Rybak, M., Calistro Rivera, G., Hodge, J. A., et al. 2019, ApJ, 876, 112, doi: [`10.3847/1538-4357/ab0e0f`](http://doi.org/10.3847/1538-4357/ab0e0f)

(ref: Saintonge2013) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2, doi: [`10.1088/0004-637X/778/1/2`](http://doi.org/10.1088/0004-637X/778/1/2)

(ref: Sanders2021) Sanders, R. L., Shapley, A. E., Jones, T., et al. 2021, ApJ, 914, 19, doi: [`10.3847/1538-4357/abf4c1`](http://doi.org/10.3847/1538-4357/abf4c1)

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: Sharda2019) Sharda, P., da Cunha, E., Federrath, C., et al. 2019, MNRAS, 487, 4305, doi: [`10.1093/mnras/stz1543`](http://doi.org/10.1093/mnras/stz1543)

(ref: Smail1997) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5, doi: [`10.1086/311017`](http://doi.org/10.1086/311017)

(ref: Solimano2021) Solimano, M., González-López, J., Barrientos, L. F., et al. 2021, A&A, 655, A42, doi: [`10.1051/0004-6361/202141835`](http://doi.org/10.1051/0004-6361/202141835)

(ref: Somerville2015) Somerville, R. S., & Davé, R. 2015, ARA&A, 53, 51, doi: [`10.1146/annurev-astro-082812-140951`](http://doi.org/10.1146/annurev-astro-082812-140951)

(ref: Stach2019) Stach, S. M., Dudzevičiūtė, U., Smail, I., et al. 2019, MNRAS, 487, 4648, doi: [`10.1093/mnras/stz1536`](http://doi.org/10.1093/mnras/stz1536)

(ref: Strong1996) Strong, A. W., & Mattox, J. R. 1996, A&A, 308, L21

(ref: Tacconi2010) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781, doi: [`10.1038/nature08773`](http://doi.org/10.1038/nature08773)

(ref: Tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: Tadaki2018) Tadaki, K., Iono, D., Yun, M. S., et al. 2018, Nature, 560, 613, doi: [`10.1038/s41586-018-0443-1`](http://doi.org/10.1038/s41586-018-0443-1)

(ref: Tadaki2019) Tadaki, K.-i., Iono, D., Hatsukade, B., et al. 2019, ApJ, 876, 1, doi: [`10.3847/1538-4357/ab1415`](http://doi.org/10.3847/1538-4357/ab1415)

(ref: Tielens1985) Tielens, A. G. G. M., & Hollenbach, D. 1985, ApJ, 291, 722, doi: [`10.1086/163111`](http://doi.org/10.1086/163111)

(ref: Tremonti2004) Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al. 2004, ApJ, 613, 898, doi: [`10.1086/423264`](http://doi.org/10.1086/423264)

(ref: Triani2020) Triani, D. P., Sinha, M., Croton, D. J., Pacifici, C., & Dwek, E. 2020, MNRAS, 493, 2490, doi: [`10.1093/mnras/staa446`](http://doi.org/10.1093/mnras/staa446)

(ref: U2012) U, V., Sanders, D. B., Mazzarella, J. M., et al. 2012, ApJS, 203, 9, doi: [`10.1088/0067-0049/203/1/9`](http://doi.org/10.1088/0067-0049/203/1/9)

(ref: vanDokkum2013) van Dokkum, P. G., Leja, J., Nelson, E. J., et al. 2013, ApJL, 771, L35, doi: [`10.1088/2041-8205/771/2/L35`](http://doi.org/10.1088/2041-8205/771/2/L35)

(ref: Villanueva2017) Villanueva, V., Ibar, E., Hughes, T. M., et al. 2017, MNRAS, 470, 3775, doi: [`10.1093/mnras/stx1338`](http://doi.org/10.1093/mnras/stx1338)

(ref: Wambsganss1998) Wambsganss, J. 1998, Living Reviews in Relativity, 1, 12, doi: [`10.12942/lrr-1998-12`](http://doi.org/10.12942/lrr-1998-12)

(ref: Wang2013) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: Wellons2020) Wellons, S., Faucher-Giguère, C.-A., Anglés-Alcázar, D., et al. 2020, MNRAS, 497, 4051, doi: [`10.1093/mnras/staa2229`](http://doi.org/10.1093/mnras/staa2229)

(ref: Whitaker2017) Whitaker, K. E., Pope, A., Cybulski, R., et al. 2017, ApJ, 850, 208, doi: [`10.3847/1538-4357/aa94ce`](http://doi.org/10.3847/1538-4357/aa94ce)

(ref: Wolfire2010) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191, doi: [`10.1088/0004-637X/716/2/1191`](http://doi.org/10.1088/0004-637X/716/2/1191)

(ref: Wolfire1990) Wolfire, M. G., Tielens, A. G. G. M., & Hollenbach, D. 1990, ApJ, 358, 116, doi: [`10.1086/168966`](http://doi.org/10.1086/168966)

(ref: Wuyts2016) Wuyts, S., Förster Schreiber, N. M., Wisnioski, E., et al. 2016, ApJ, 831, 149, doi: [`10.3847/0004-637X/831/2/149`](http://doi.org/10.3847/0004-637X/831/2/149)

(ref: Yamashita2017) Yamashita, T., Komugi, S., Matsuhara, H., et al. 2017, ApJ, 844, 96, doi: [`10.3847/1538-4357/aa7af1`](http://doi.org/10.3847/1538-4357/aa7af1)

(ref: Zhukovska2008) Zhukovska, S., Gail, H. P., & Trieloff, M. 2008, A&A, 479, 453, doi: [`10.1051/0004-6361:20077789`](http://doi.org/10.1051/0004-6361:20077789)

(ref: Zitrin2015) Zitrin, A., Fabris, A., Merten, J., et al. 2015, ApJ, 801, 44, doi: [`10.1088/0004-637X/801/1/44`](http://doi.org/10.1088/0004-637X/801/1/44)

[^1]: https://archive.stsci.edu/prepds/frontier/lensmodels/

</paper>

Write the methods card for this paper.