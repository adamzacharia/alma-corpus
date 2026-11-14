# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...977L...9Z\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...977L...9Z",
 "title": "ALMA Detection of [O III] 88 μm at z = 12.33: Exploring the Nature and Evolution of GHZ2 as a Massive Compact Stellar System",
 "year": 2024,
 "journal": "The Astrophysical Journal Letters",
 "first_author": "Zavala, Jorge A.",
 "n_authors": 24,
 "arxiv_id": "2411.03593",
 "doi": "10.3847/2041-8213/ad8f38",
 "alma_projects_linked_by_archive": [
  "2021.A.00020.S",
  "2023.A.00017.S"
 ]
}
```

Paper text:
<paper>
# ALMA detection of \[OIII\] 88 $\mu\rm m$ at $z=12.33$:\
Exploring the Nature and Evolution of GHZ2 as a Massive Compact Stellar System

## Abstract

We present ALMA observations on the high-redshift galaxy GHZ2 and report a successful detection of the rest-frame 88 $\mu\rm m$ atomic transition from doubly-ionized Oxygen at $z=12.3327\pm0.0005$. Based on these observations, combined with additional constraints on the \[OIII\] 52 $\mu\rm m$ line luminosity and previous JWST data, we argue that GHZ2 is likely powered by compact and young star formation, and show that it follows well-established relationships found for giant HII regions and metal-poor star-forming dwarf galaxies that are known to host bright super star clusters. Additionally, these observations provide new constraints on the Oxygen electron density ($100\lesssim n_e\,{\rm[cm^{-3}]}\lesssim4,000$) and dynamical mass ($M_{\rm dyn}\approx3-8\times10^8\rm\,M_\odot$). The existence of these massive starburst systems 13.3 Gyr ago might explain the origin of today’s globular clusters, a long-standing question in astronomy. To test this, we present observational probes to investigate whether sources like GHZ2 are linked to the formation of today’s globular clusters or other more massive compact stellar systems.

# Introduction

The discovery of bright galaxies at very high redshifts ($z\gtrsim10$) by the James Webb Space Telescope (JWST) is challenging our understanding of galaxy formation and evolution. Their high luminosities ($M_{UV}<-20$) and inferred volume density are in tension with the predictions from widely-adopted (pre-JWST) theoretical studies (e.g. (cite: Adams2024; Castellano2023; Finkelstein2023; Harikane2024b)). This could be the result of very young stellar populations and/or bursty star formation, enhanced star formation efficiencies in the early Universe, contribution from active black holes, or strong evolution in the dust properties, among others, including a non-universal initial mass function or modifications to the standard cosmology itself (e.g. (cite: Boylan-Kolchin2023; Feldmann2024; Ferrara2023; Liu2022; Sun2023; Yung2024)).

These galaxies provide thus crucial insights into the earliest phases of galaxy formation within the first few hundred million years after the Big Bang, as well as into the galaxy-dark matter connection and black hole-galaxy co-evolution. To date, more than ten galaxies have been spectroscopically confirmed at $z>10$ (see recent compilation by (cite: Roberts-Borsani2024)), reaching up to $z\sim14$ (cite: Carniani2024), but their nature and primary source of excitation remain unclear, especially for the brightest and most compact systems. *Are they primarily powered by intense star formation or do they host active galactic nuclei (AGN) that contribute significantly to their luminosity?*

To address this question, spectroscopic observations to probe the physics of their multiphase interstellar media are essential. At high redshifts, the JWST NIRSpec instrument has became one of the workhorses for characterizing these systems thanks to its high sensitivity and wavelength coverage (e.g. (cite: ArrabalHaro2023; Bunker2023; Curtis-Lake2023; Fujimoto2023; Sanders2023; Wang2023)), but at $z\gtrsim9-10$, it provides access mainly to rest-frame UV lines. Recently, the Mid-Infrared Instrument (MIRI) has also been used to study some of the highest redshift galaxies since it probes the well studied (and typically bright) rest-frame optical emission lines up to $z\gtrsim 14-15$, offering valuable complementary data to the NIRSpec observations (e.g. (cite: Alvarez-Marquez2024; Hsiao2024; Zavala2024)). Furthermore, the Atacama Large Millimeter/submillimeter Array (ALMA) is uniquely equipped to characterize high-redshift galaxies through the detection of far-infrared emission lines, which can also serve as powerful diagnostics for the physical conditions of distant galaxies (e.g. (cite: Inoue2014; Inoue2016; Bakx2020; Carniani2017; Hashimoto2019)), specifically when using multi-wavelength line diagnostics (e.g. (cite: Katz2019; Nakazato2023)).

Nevertheless, some recent ALMA follow-ups on ultra-high-redshift galaxy candidates have resulted in non-detections ((cite: Bakx2023; Kaasinen2023; Yoon2023)), preventing us from fully characterizing the nature of these systems and calling into question the ALMA’s capabilities to study the $z\gtrsim10$ universe. Most of these observations, however, suffered from targets with highly uncertain redshifts (most of them limited to photometric redshifts), which require line-searches through multi-setup spectral scans, limiting the sensitivity of the observations and preventing the derivation of tight constraints on their physical properties.

In this study, we present deep ALMA observations targeting a spectroscopically confirmed galaxy within the Universe’s first 400 Myrs, GHZ2/GLASSz12 at $z=12.3$ (hereafter GHZ2; (cite: Castellano2024; Zavala2024); see also (cite: Naidu2022; Castellano2022; Calabro2024)), and report a successful detection of the \[OIII\] 88$\mu\rm m$ far-infrared emission line. This breakthrough allows us to place new constraints on the physical properties of this unique galaxy, which stands out as one of the brightest known objects at this epoch ($M_{UV}\approx-20.5$). Moreover, this study provides critical insights into the nature and evolution of the luminous high-redshift galaxies recently discovered by JWST and the mechanisms powering their extraordinary brightness, while demonstrating the feasibility of studying these early systems with ALMA.

The enormous potential of the ALMA-JWST synergy is further demonstrated by (cite: Carniani2024b) and (cite: Schouws2024), who reported subsequent ALMA observations on a higher redshift galaxy, JADES-z14-0, with a successful detection of the \[OIII\] 88$\mu\rm m$ transition at $z=14.18$.

This paper is structured as follows. Section [2](#secc:observations) presents the details of the ALMA observations and data reduction, as well as the identification of the \[OIII\] 88$\ensuremath{\mu}m$ line. The main results of the paper and the comparison of the properties of GHZ2 and those from local and low-redshift star-forming systems are presented in Section [3](#secc:results). In Section [4](#secc:discussion) we discuss circumstantial evidence relating GHZ2, and other bright high-redshift galaxies, to globular clusters and other compact stellar systems. Finally, a summary of this work is presented in Section [5](#secc:summary). A companion paper (Mitsuhashi et al. in prep.) will present the dust constraints inferred from the ALMA continuum observations (which remains undetected at $>3\sigma$).\
Throughout this paper, we assume a flat $\Lambda$CDM cosmology with $\Omega_\mathrm{m} = 0.29$, $\Omega_\mathrm{\Lambda} = 0.71$ and $\rm H_0=69.6\,\rm km\,s^{-1}\,Mpc^{-1}$.

# ALMA observations, data reduction, and data analysis

## Observations and data reduction

![](spectrum.png)

The source GHZ2 was previously targeted by ALMA using a Band 6 spectral scan strategy to search for the \[OIII\] 88$\,\mu\rm m$ line ($\nu_{\rm rest} = 3393.0062\,\rm GHz$) across the frequency range 234-263 GHz, corresponding to $z\approx11.9-13.55$. Nevertheless, no robust detection was identified at the JWST position of the target ((cite: Bakx2023); see also (cite: Popping2023)). After the spectroscopic redshift confirmation by JWST/NIRSpec and JWST/MIRI (cite: Castellano2024; Zavala2024), deeper ALMA observations were obtained in April 2024 around the refined expected frequency of the line at 254.45 GHz as part of the DDT project 2023.A.00017.S (PI: J. Zavala). The new observations consist of $\sim4.9\,\rm h$ on-source ($\sim8.7\,\rm h$ including calibrations and overheads), which adds to $\sim7\,\rm h$ on-source in total when combining the cycle 9 and cycle 10 data-sets. Unfortunately, the new data do not cover the previous tentative line reported by (cite: Bakx2023) at $\nu=258.67\,\rm GHz$.

Additionally, Band 8 observations covering the redshifted \[OIII\] 52$\,\mu\rm m$ line ($\nu_{\rm rest} = 5785.8796\,\rm GHz$) were also carried out as part of project 2023.A.00017.S. The spectral setup covers the frequency ranges $418.6-422.4\rm\, GHz$ and $430.8-434.5\rm\, GHz$, with an on-source time of $2.5\,\rm h$ (4.8 h including calibrations and overheads). These observations are by design shallower than the Band 6 data since were only aimed to provide a limit on the \[OIII\] 52$\,\mu\rm m$ in the case of an extreme electron density (see Section [3.3](#secc:electron_density)). Matching the Band 6 sensitivity would have required a much larger time investment that is beyond the scope of a DDT proposal.

Data reduction was performed as described in (cite: Bakx2023), using CASA and following the standard ALMA pipeline workflow. Then, as part of our imaging process, we created data cubes from the $uv$-visibilties using a Natural weighting to maximize the signal-to-noise ratio (at the cost of angular resolution). For the Band 6 observations, during this process, we tested several choices for the pixel size (namely $0.05\ensuremath{''}$, $0.075\ensuremath{''}$, and $0.10\ensuremath{''}$) and channel width (35, 50, 75, and 100 km s$^{-1}$), as well as the effect of slightly changing the phase center within a beam-size and slightly shifting the velocity of the first channel. The typical sensitivity (r.m.s.) of these cubes is equivalent to $1\sigma=75\,\mu$Jy beam$^{-1}$ in 35 km s$^{-1}$ channels, and have a typical beam size of $0.36\ensuremath{''}\times0.28\ensuremath{''}$. As described below, all of these datacubes are used to robustly estimate the uncertainties on the line parameters.

In the case of the Band 8 observations, the achieved $1\sigma$ r.m.s. is around 500 $\mu$Jy beam$^{-1}$ in 35 km s$^{-1}$ channels, with a beam size of $0.36\ensuremath{''}\times0.32\ensuremath{''}$.

## The \[OIII\]88$\ensuremath{\mu}m$ transition at $z = 12.3$: line properties

We use the collection of datacubes described above to search for the \[OIII\] 88$\ensuremath{\mu}m$ emission line using an iterative process as follows. First, we extract the spectrum from each datacube exactly at the JWST position of GHZ2. Second, we identify the brightest channel within the expected frequency range of the redshifted \[OIII\]88$\ensuremath{\mu}m$ line base on the JWST/MIRI and JWST/NIRSpec spectroscopic redshifts, and perform a Gaussian fit with $A,\sigma, \nu_{\rm cent}$ as free parameters (with a flat zero continuum). Then, to improve the SNR of each extracted spectrum, we create a moment-0 map by collapsing the datacube within the full-width half-maximum (FWHM) of the best-fit Gaussian function and re-extract the spectrum but now at the position of the peak pixel in this moment-0 map. Finally, we perform a new Gaussian fit around the expected frequency and save the best-fit parameters. Reassuringly, all the extracted spectra (those extracted at the JWST position and at the peak ALMA pixel) identify the same feature as an emission line with a significance of $\approx4.5-5.2\sigma$, confirming the tentative detection reported in (cite: Zavala2024).

Figure [1](#fig:ALMA_spectrum) shows one of the extracted spectrum and associated moment-0 map (right and left panels, respectively) along with the adopted best-fit Gaussian function (red solid line). The best-fit Gaussian functions from other spectra are also shown to illustrate the typical variance in the data (gray lines). The fiducial line properties and associated uncertainties are assumed to be the median values of all the different best-fit functions and their standard deviation. This approach allows us to properly take into account the impact of the imaging parameters in the shape of the line and to robustly estimate the uncertainties in the best-fit values. These best-fit properties are summarized in Table [\[table:line_properties\]](#table:line_properties).

+:----------------------------------------------:+:-----------------------:+
| GHZ2                                                                     |
+--------------------------------------------------------------------------+
| ${\rm RA}=00$:13:59.76; $\rm Dec=-30$:19:29.16                           |
+------------------------------------------------+-------------------------+
| $z_{\rm [OIII]88\mu m}$                        | $12.3327\pm 0.0035$     |
+------------------------------------------------+-------------------------+
| $z_{\rm NIRSpec}$$^{a}$                        | $12.342\pm 0.009$       |
+------------------------------------------------+-------------------------+
| $z_{\rm MIRI}$$^{b}$                           | $12.33\pm 0.04$         |
+------------------------------------------------+-------------------------+
| $\nu_{\rm cent}$ \[$\rm GHz$\]                 | $254.487\pm 0.019$      |
+------------------------------------------------+-------------------------+
| FWHM \[$\rm km\,s^{-1}$\]                      | $186 \pm58$             |
+------------------------------------------------+-------------------------+
| $S_{\rm total}$ \[$\rm mJy\,km\,s^{-1}$\]      | $36\pm10$               |
+------------------------------------------------+-------------------------+
| $L_{\rm [OIII]}$ \[$\rm L_\odot$\]$\times10^8$ | $1.7\pm0.4$             |
+------------------------------------------------+-------------------------+

: \[OIII\] 88$\,\mu\rm m$ line properties (uncorrected for gravitational amplification).

Table notes: $^{a}$ (cite: Castellano2024) $^{b}$ (cite: Zavala2024)

## An upper limit on the \[OIII\] 52$\mu$m line luminosity

Armed with a more precise spectroscopic redshift from the \[OIII\] 88$\ensuremath{\mu}m$ detection, we search for the 52$\mu$m line around the expected frequency of 433.96 GHz, but no obvious line was detected (see Figure [6](#fig:52um_spectrum) in the Appendix). We estimate an upper limit on the \[OIII\] 52$\ensuremath{\mu}m$ line luminosity using the measured local noise r.m.s., adopting the \[OIII\]88$\ensuremath{\mu}m$ line-width of $186\pm58\,\rm km\,s^{-1}$ (see Table [\[table:line_properties\]](#table:line_properties)) and assuming no spatially-extended emission beyond the beam-size. This results in a $3\sigma$ upper limit of $L_{\rm [OIII]52\mu m}<9.6\times10^8\,L_\odot$, implying a $3\sigma$ upper limit on the 52-to-88$\mu\rm m$ line ratio of $L_{\rm [OIII]52\mu m}/L_{\rm [OIII]88\mu m}<5.6$.

# Results

## Detection of \[OIII\] 88$\,\mu\rm m$: Expectations and implications

Using observations of local and low-redshift galaxies with the *Herschel Space Observatory*, (cite: DeLooze2014) found a set of correlations between the \[OIII\] 88$\ensuremath{\mu}m$ line luminosity and galaxies’ SFR for different galaxy populations. Evolved, massive star-forming galaxies (referred as *starbursts* in the aforementioned work) and composite/AGN systems are clearly offset from metal-poor star-forming dwarf galaxies. These correlations seems to be valid at $z\sim5-9$, as can be seen in Figure [2](#fig:sfr_vs_O3), where we plot all the high-redshift \[OIII\] 88$\ensuremath{\mu}m$ detections to date. Lyman break galaxies (LBGs) and Lyman-$\alpha$ emitters (LAEs) follow the same local relation found for metal-poor dwarf galaxies, while QSO and submillimeter-selected galaxies are in better agreement with the local relation for composite/AGN (although with large scatter and with some objects being consistent with both relationships).

![](SFR_vs_O3.png)

In this context, we show, in Figure [2](#fig:sfr_vs_O3), the \[OIII\] 88$\ensuremath{\mu}m$ line luminosity and SFR measured for our target and compare it with the reported relationships and with previous detections from high-redshift galaxies. We adopt the line luminosity reported above corrected by magnification ($\mu=1.3$; (cite: Bergamini2023)), and the range of SFR values reported by (cite: Zavala2024) based on the spectro-photometric SED fittings and the H$\alpha$ line ($2-12\,\rm M_\odot\,yr^{-1}$, after correcting for magnification).

As can been seen in the figure, GHZ2 lies on a locus comparable to some $z\sim8$ LBGs/LAEs and in very good agreement with the local relationship for metal-poor dwarf galaxies. These galaxies are dominated by star formation and, thus, by analogy, we suggest that it might also be the case for our $z=12$ target. Actually, the measured line luminosity is also in broad agreement with the predictions from the serra zoom-in simulations for galaxies with similar properties as GHZ2, in terms of SFRs and redshifts ((cite: Kohandel2023)), which further support the star formation scenario for GHZ2. To further test this interpretation, below we compare other properties of GHZ2 with those measured directly for well-known systems dominated by star formation, such as HII regions and HII galaxies[^1] (while the potential contribution of an AGN in discussed in Section [4](#secc:discussion)).

![](Lsigma.png)

Over the past decades, it has been shown that giant HII regions exhibit a correlation between the luminosity of the Balmer emission lines (typically $H\beta$) and the line velocity dispersion ((cite: Terlevich1981)). Although the physical origin of this relation is still a matter of debate, it is typically thought to be driven by the total mass of the (gravitationally-bounded) star-forming region, dominated by young super star clusters. The relation has been calibrated using samples of several dozens of local and extragalactic giant HII regions (e.g. (cite: Chavez2014)) and shown to be also valid for HII-galaxies up to $z\sim3$ (e.g. (cite: Gonzalez-Moran2021)). (cite: Melnick2017) presented a new calibration using the $\rm [OIII]5007\AA$ line-width and the $H\beta$ line luminosity that shows a similar scatter than the original $L_{\rm H\beta}-\sigma_{\rm H\beta}$ relationship. Here we use this correlation given that the Balmer lines are not spectrally resolved for our target, and test whether GHZ2 follows a similar trend, as expected if the source is dominated by young bursts of star formation and assuming the relationship does not evolve significantly with redshift (note that the $z\sim6-7$ HII-galaxies recently reported by (cite: Chavez2024) follow the same relationship, as can be seen in Figure [3](#fig:Lsigma)).

We adopt the lensing-corrected H$\beta$ luminosity of $\log\, L_{\rm H\beta} = 42.16^{+0.09}_{-0.13}\rm\,erg\,s^{-1}$ from (cite: Zavala2024) (inferred from the H$\alpha$ line assuming zero dust attenuation), and the \[OIII\] 88$\ensuremath{\mu}m$ line-width provided by the ALMA observations as a proxy for the \[OIII\]5007$\AA$ velocity dispersion (given that both transitions are produced by the same ion and the \[OIII\]5007$\AA$ line is unresolved in the MIRI low-resolution spectrum). As can be seen in Figure [3](#fig:Lsigma), GHZ2 follows the same relationship found for giant HII regions, suggesting that this very high-redshift galaxy is also powered by (extreme) star formation. Actually, some of the \[OIII\] 88$\mu$m-detected dwarf galaxies described above are also known to harbor bright HII regions powered by super star clusters ((cite: Madden2013)). This might imply that the high ionization conditions in GHZ2 are likely driven by extreme HII regions associated with young bursts of star formation. The same can be said for the $z=10.2$ MACS0647-JD galaxy recently observed with NIRSpec and MIRI ((cite: Hsiao2024; Hsiao2024b)). This object also follows the relationship derived for HII-dominated systems, which supports the conclusions by (cite: Hsiao2024b) who argued against an AGN-dominated galaxy.

On the other hand, while similar relationships between the Balmer line luminosities and lines’ velocity dispersion have been reported for AGN (e.g. (cite: Ho2003)), typical AGN hosting super massive black holes show emission lines significantly broader than the HII regions and HII galaxies (with \[OIII\] line-widths of $>300\,\rm km\,s^{-1}$; e.g. (cite: Kakkad2020)). And while less massive AGN with narrower line-widths have recently been found by JWST up to $z\sim7$ or beyond, they have brighter line luminosities compared to star-forming dominated systems (see Figure [3](#fig:Lsigma)). All of this supports our conclusion that GHZ2 is most likely dominated by a burst of star formation.

Given that the population of young, low-metallicity massive clusters powering giant HII regions have been proposed to be the progenitors of globular clusters (e.g. (cite: Ho1997; PortegiesZwart2010; Terlevich2018)), it is possible that the current starburst episode of GHZ2 might result in the formation of proto-globular clusters or other compact stellar systems. Indeed, its abundance, with an enhanced nitrogen abundance, has already been noticed to be consistent with the expected progenitor population for globular clusters ((cite: Castellano2024)), as well as its high SFR and stellar mass surface densities ((cite: Ono2023; Calabro2024)). This might point towards an evolutionary connection between the bright, compact high-redshift galaxies discovered by JWST (including GHZ2) and the enigmatic population of old globular clusters (see also (cite: Charbonnel2023; Isobe2023; Castellano2024; Marques-Chaves2024; Topping2024)). This is discussed in detail below, in Section [4](#secc:discussion).

## Dynamical mass

Assuming a spherical geometry (a reasonable assumption for this very compact source), we estimate the dynamical mass using the virial equation (e.g. (cite: Pettini2001; Wolf2010)): $$\begin{equation}
     M_{\rm dyn}=\frac{5\sigma^2 R}{G}, \label{eq:Mdyn}
\end{equation}$$ where $\sigma$ is the velocity dispersion and $R$ is the virial radius. The velocity dispersion is determined from the \[OIII\] 88$\ensuremath{\mu}m$ transition ($\sigma=79\pm25\rm\,km\,s^{-1}$) and the virial radius is adopted to be the half-light radius measured from the JWST/NIRcam images, with reported values of $r_{1/2}=39\pm11\,$pc ((cite: Ono2023)) and $105\pm9\,$pc ((cite: Yang2022)). Using Equation [\[eq:Mdyn\]](#eq:Mdyn) and the aforementioned assumptions we constrain the dynamical mass to be $3\times10^8\rm-8\times10^8\rm\,M_\odot$.

This is remarkably similar to the stellar masses inferred from the spectro-photometric SED fitting analysis presented in (cite: Zavala2024), with best-fit stellar masses of $2\times10^8\rm-8\times10^8\rm\,M_\odot$ (assuming a magnification of $\mu=1.3$: (cite: Bergamini2023)). This implies a dynamical-to-stellar mass ratio of close to unity for GHZ2, similar to the measured values for globular clusters (e.g. (cite: Forbes2014)), providing more evidence for a relation between these objects as discussed below.

Finally, to assess the impact of our assumptions on the inferred dynamical mass, we alternatively use the approach described by (cite: Ubler2023). Here, we assume Sersic indices of $n=1$ and $1.5$, with axis ratios in the range of $q=\{0.3:0.7\}$. Overall, the dynamical masses inferred from these models fall within the range of the values described above but allow for up to a 50% increase. However, given the compactness and symmetry of the source ((cite: Treu2023b)), we adopt the mass constraints from the virial equation described above as our fiducial value.

## Constraining the electron density

The \[OIII\]52$\ensuremath{\mu}m$-over-\[OIII\]88$\ensuremath{\mu}m$ line luminosity ratio provides strong constraints on the electron density almost independently from metallicity, ionization field effects, or electron temperature (e.g. (cite: Jones2020; Killi2023; Nakazato2023)). Here, given the non-detection of the \[OIII\] 52$\mu$m transition (see Section [2.3](#secc:upperlimit52um)), we determine a $3\sigma$ upper limit on the ionized Oxygen electron density of $\log(n_e\,[\rm cm^{-3}])<3.62$ (see Figure [4](#fig:n_e)). While this value seems high compared to the typical values found in star-forming galaxies at low redshifts ($\sim100\,\rm cm^{-3}$; e.g. (cite: Kaasinen2017)), this upper limit is totally consistent with the measured electron densities of high-redshift ($z\gtrsim5$) star-forming galaxies and with the apparent redshift evolution of $n_e$ (e.g. (cite: Isobe2023; Jones2024)), particularly when combined with the lower limit of $n_e\gtrsim100\,\rm cm^{-3}$ reported in (cite: Zavala2024). On the other hand, the electron density of GHZ2 contrasts with that of GNz11, the brightest confirmed galaxy at $z>10$. In the case of GNz11, the \[NIV\] doublet and NIII\] multiplet indicate extremely large electron densities ($>10^5\rm cm^{-3}$) in better agreement with the broad line regions in AGN ((cite: Maiolino2024)). We stress, however, that transitions with different ionization potentials might trace different regions of the ISM with different electron densities (e.g. (cite: ji2024))

![](ne.png)

# Discussion

## A system dominated by star formation

The nature of the intriguing population of bright, high-redshift galaxies discovered by JWST remains unclear. *What processes drive their high luminosity so early in the Universe’s history?* Understanding whether these galaxies are dominated by stellar processes or AGN activity is crucial for developing a comprehensive picture of galaxy formation in the early Universe.

In the case of GHZ2, this question has been approached from different perspectives, starting with its JWST/NIRCam morphology. (cite: Ono2023) found that while the source is very compact, it is spatially resolved with a half-light radius of a few tens of parsecs (see also (cite: Yang2022)). This provides evidence against an AGN-dominated system, although it does not totally rule out some fractional contribution to its continuum luminosity. Similarly, (cite: Zavala2024), who presented the detection of $H\alpha$ and \[OIII\]5007$\AA$ in the JWST/MIRI spectrum and a spectro-photometric SED analysis of this source, attributed its high luminosity to the presence of a very young, massive and metal-poor stellar population; but, again, the possibility of having some contribution from AGN remained open. This latter scenario was revitalized given the detection of relatively high-ionization UV transitions and line rations, and lines with high equivalent widths, in the JWST/NIRSpec spectrum presented by (cite: Castellano2024), indicating ionizing photons with energies in excess of $\sim 50-60$ eV. Nevertheless, the absence of higher ionization lines typically seen in AGN (like HeII or \[NeIV\]2424$\AA$) and the strong upper limit on the \[Ne IV\]/N IV\] ratio put some doubts on this scenario and led the authors to suggest that GHZ2 is most likely dominated by (extreme) star formation. Finally, (cite: Calabro2024) presented a comprehensive analysis of the (rest-frame) UV and optical line ratios finding very high ionization conditions but indistinguishable between those produced by AGN and low metallicity, compact star-forming regions.

It is thus clear that GHZ2 shows extreme properties with high ionization conditions, but a pure AGN model would fail to reproduce all the characteristics described above (such as the lack of some specific atomic transitions and extended emission). Additionally, in Section [3.1](#secc:scaling_relations) we have shown that this source follows the SFR-\[OIII\] 88$\ensuremath{\mu}m$ relationship found for metal-poor star-forming galaxies and the L-$\sigma$ relation found for giant HII regions and HII-galaxies, which would be hard to explain within the AGN framework. The fact that the H$\alpha$-based SFR is in good agreement (within a factor of $\sim2$) with the star-forming SED modelling (see (cite: Zavala2024)) might also imply that the contribution from AGN (if any) should be low. The same could be said of the fact that the stellar mass (from the SED analysis) and the dynamical mass (from the \[OIII\] 88$\ensuremath{\mu}m$ detection) are consistent with a factor of $\sim 2$. Such results would be entirely coincidental in the case of an AGN-dominated system. Finally, the electron density upper limit of $n_e<4.2\times10^3\,\rm cm^{-3}$, although high, has been shown to be within the realm of star-forming galaxies (see §[3.3](#secc:electron_density)), and significantly below the typical values of the broad line region in AGN. Hence, we conclude that GHZ2 is most likely dominated by star formation activity driven by metal-poor and young stellar populations.

Furthermore, given its high H$\alpha$ and H$\beta$ luminosities – consistent only with the most luminous starbursts and HII galaxies (e.g. (cite: Ho1997b; FernandezArenas2018)) – and its remarkable compactness and concentration ((cite: Ono2023; Treu2023b)), it would be expected that this extreme star formation activity is taking place in the form of super star clusters, commonly found in starburst systems ((cite: Ho1997b)). The high specific SFR of GHZ2 of $\rm sSFR\approx10-30\,Gyr^{-1}$ might actually be an evidence of a starburst-like star formation mode propitious to the formation of these massive clusters. This is also supported by the high *burstiness* found for the serra simulated galaxies that match other properties of GHZ2 ((cite: Pallottini2022)).

However, it is important to remark that, although the star-forming scenario seems the most plausible to explain the nature of this object, available models fail to reproduce the extremely high equivalent widths of the UV lines, some of them only compatible with AGN or composite emission models, as discussed in detail by (cite: Castellano2024) and (cite: Calabro2024).

![](sigma_vs_Mstar_both.png)

## The progenitor of a compact stellar object

*Will GHZ2 evolve into a globular cluster?*

The fact that GHZ2 might be powered by massive star clusters does not necessarily make it a globular cluster progenitor. However, here we provide additional arguments that might support this scenario and that might, additionally, explains some of the long-standing problems associated with globular clusters.

First, its low metallicity and enhanced nitrogen abundance ((cite: Castellano2024)) resembles the well-known chemical anomalies observed in globular clusters (e.g. (cite: Cannon1998)) – though not exclusive to them. These abundance patterns are thought to be the product of massive stars in very dense environments (e.g. (cite: Smith2006)) and, interestingly, in GHZ2, the presence of very massive stars has been inferred from its high ionization conditions ((cite: Calabro2024; Castellano2024; Zavala2024)). Moreover, its compact morphology implies a high mass density (with $\Sigma_\star\sim10^4\,\rm M_\odot\,pc^{-2}$ and $n_e\approx 100-4,000\,\rm cm^{-3}$), similar to those found in globular clusters (see Figure [5](#fig:mstar-sigma)). In addition, spectro-phometric SED fitting analysis on GHZ2 indicates a bursty star formation history for this object ((cite: Zavala2024); see also (cite: Harikane2024b)). These short bursts with duration in the range of a few or a few tens of Myr, in combination with its very rapid metal enrichment[^2], would naturally explain the low spread in stellar ages and the multiple stellar populations observed in globular clusters (see reviews by (cite: Gratton2012), (cite: Forbes2018)). Lastly, its unique spectral features with UV lines with high EWs and clear emission of the OIII 3123Å  fluorescence line[^3] ((cite: Castellano2024)) might be explained by the *stellar exotica* in globular clusters (e.g. X-ray binaries; (cite: PortegiesZwart2010)) and their high helium abundance ((cite: Norris2004; DAntona2005)).

There is one thing, however, that appears to be at odds with expected proto-globular cluster properties: the high total mass of GHZ2. With a stellar mass of $\approx10^8-10^9\,\rm M_\odot$ (see Section [3.2](#secc:mdyn)), GHZ2 exceeds by more than one order of magnitude the masses of even the most massive known globular clusters (see Figure [5](#fig:mstar-sigma)). These two values might be reconciled by assuming significant mass losses due to stellar and dynamical evolution (e.g. (cite: Webb2015)), but even assuming extreme values, GHZ2 would only be barely consistent with the most massive population of globular clusters. Alternatively, this tension might be solved by the models presented in (cite: DErcole2008), in which most of the first-generation stars are lost due to the expansion and stripping of the cluster’s outer layers caused by the heating from SN ejecta, followed by a highly concentrated second generation of stars. Indeed, several models require this first generation to be at least $\sim10$ times more massive than current globular cluster survivors in order to explain the different chemical composition of the multiple stellar populations (e.g. (cite: Renzini2015)).

Another possibility is that GHZ2 hosts an ensemble of super star clusters. This scenario is supported not only by its large mass, but also by its size. Its effective radius of $\sim40\,\rm pc$ exceeds by a factor from a few to tens the sizes of the few high-redshift proto-globular clusters that have been individually resolved thanks to strong gravitational lensing effects (e.g. (cite: Adamo2024; Vanzella2023)). These two discrepancies (the size and total mass), could be solved by assuming that GHZ2 is actually a superposition of several individual clusters (e.g. (cite: Mowla2024)). Supporting evidence for this scenario is found in the simulations presented in (cite: Kohandel2023), in which the \[OIII\] 88$\mu$m emission of $z>10$ galaxies is resolved into several individual HII regions. And, although it is possible that these HII regions might be normal OB associations with a high probability of dissolution, as discussed above and in Section [4.1](#secc:SSC), GHZ2 shows properties rather similar to those of massive, super star clusters.

The final scenario discussed considers the possibility that GHZ2 is an ultra-compact dwarf (UCD) galaxy or a proto-compact elliptical given the similarities between their stellar mass, size, and velocity dispersion (see Figure [5](#fig:mstar-sigma)). The formation processes of these objects remains unclear, but they are known to bridge the gap between stellar clusters and galaxies (e.g. (cite: Norris2014; Terlevich2018); see also Figure [5](#fig:mstar-sigma)), and it has been shown that some of these objects could represent the massive end of the globular cluster luminosity function (e.g. (cite: Mieske2012)) or the result of merging of several star clusters (e.g. (cite: UrrutiaZapata2019)). While it is also true that some UCD show elevated dynamical-to-stellar mass ratio that can be attributed to the presence of massive black holes (e.g. (cite: Seth2014)), GHZ2 shows a dynamical-to-stellar mass ratio around one (see Section [3.2](#secc:mdyn)), in better agreement with globular clusters and compact ellipticals ((cite: Forbes2014)).

We thus conclude that GHZ2 might be powered by young and compact star-forming regions that could evolve into globular clusters or to become the central core of a more massive galaxy. This is, however, only suggestive and not conclusive. Further observations and simulations should be conducted to further test this interpretation.

# Summary

Through the detection of \[OIII\] 88$\ensuremath{\mu}m$ at $z=12.33$, we have demonstrated the feasibility of studying the early ($z>10$) universe with ALMA and its unique synergy with JWST to characterize the most distant galaxies known to date. By combining these observations with previous multi-wavelength photometry and spectroscopy, we investigated the nature of GHZ2 – one of the brightest known galaxies at $z>10$ universe, just 350 million years after the Big Bang. We concluded that this object is likely powered by young bursts of star formation similar to those found in giant HII regions (metal-poor, massive, and compact star clusters). Finally, we presented compelling evidence suggesting that GHZ2 might be a progenitor of globular clusters or represent the early phases of a compact dwarf or elliptical galaxy. While this characterization is very suggestive, further observations with both high spectral and high angular resolution are needed to test this hypothesis and to fully understand some of the unique properties of this object.

We thank Stefano Carniani, Mahsa Kohandel, and Andrea Ferrara for stimulating discussions; Angela Adamo, Hiddo Algera, Ricardo Chávez, and Anthony Taylor for sharing their datasets; and Takuya Hashimoto and Yurina Nakazato for sharing information about their research projects. We also thank the anonymous reviewer and the scientific editor for their valuable feedback on the manuscript. JAZ acknowledge funding from JSPS KAKENHI grant number KG23K13150. MC and PS acknowledge INAF Mini Grant 2022 “Reionization and Fundamental Cosmology with High-Redshift Galaxies, INAF Mini Grant 2022 “The evolution of passive galaxies through cosmic time”, and PRIN 2022 MUR project 2022CB3PJ3 - First Light And Galaxy aSsembly (FLAGS) funded by the European Union - Next Generation EU. LCH was supported by the National Science Foundation of China (11991052, 12233001), the National Key R&D Program of China (2022YFF0503401), and the China Manned Space Project (CMS-CSST-2021-A04, CMS-CSST-2021-A06). PGP-G acknowledges support from grant PID2022-139567NB-I00 funded by Spanish Ministerio de Ciencia, Innovación y Universidades MICIU/AEI/10.13039/501100011033, and the European Union FEDER program *Una manera de hacer Europa*. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.A.00020.S and JAO.ALMA#2023.A.00017.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST,ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Facilities

ALMA (Band 6 and Band 8; (cite: Ediss2004; Sekimoto2008)), *JWST* ((cite: Gardner2006; Gardner2023))

# Software

CASA (cite: CASATeam2022),

# Band 8 spectrum around the \[OIII\] $52\,\mu \mathrm{\lowercase{m}}$ transition

Figure [6](#fig:52um_spectrum) shows the extracted spectrum at the position of GHZ2 (right panel) along with a collapsed data-cube within the expected FWHM of the line (from approx. 433.8 to 434.1 GHz; left panel). The line is undetected at the current depth of the observations, but provide useful constraints on the electron density as discussed in Section [3.3](#secc:electron_density).

![](52um_spectrum.png)

natexlab

(ref: Adamo2024) Adamo, A., Bradley, L. D., Vanzella, E., et al. 2024, Nature, 632, 513, doi: [`10.1038/s41586-024-07703-7`](http://doi.org/10.1038/s41586-024-07703-7)

(ref: Adams2024) Adams, N. J., Conselice, C. J., Austin, D., et al. 2024, ApJ, 965, 169, doi: [`10.3847/1538-4357/ad2a7b`](http://doi.org/10.3847/1538-4357/ad2a7b)

(ref: Algera2024) Algera, H. S. B., Inami, H., Sommovigo, L., et al. 2024, MNRAS, 527, 6867, doi: [`10.1093/mnras/stad3111`](http://doi.org/10.1093/mnras/stad3111)

(ref: Alvarez-Marquez2024) Álvarez-Márquez, J., Colina, L., Crespo Gómez, A., et al. 2024, A&A, 686, A85, doi: [`10.1051/0004-6361/202347946`](http://doi.org/10.1051/0004-6361/202347946)

(ref: ArrabalHaro2023) Arrabal Haro, P., Dickinson, M., Finkelstein, S. L., et al. 2023, Nature, 622, 707, doi: [`10.1038/s41586-023-06521-7`](http://doi.org/10.1038/s41586-023-06521-7)

(ref: Bakx2020) Bakx, T. J. L. C., Tamura, Y., Hashimoto, T., et al. 2020, MNRAS, 493, 4294, doi: [`10.1093/mnras/staa509`](http://doi.org/10.1093/mnras/staa509)

(ref: Bakx2023) Bakx, T. J. L. C., Zavala, J. A., Mitsuhashi, I., et al. 2023, MNRAS, 519, 5076, doi: [`10.1093/mnras/stac3723`](http://doi.org/10.1093/mnras/stac3723)

(ref: Bakx2024) Bakx, T. J. L. C., Algera, H. S. B., Venemans, B., et al. 2024, MNRAS, 532, 2270, doi: [`10.1093/mnras/stae1613`](http://doi.org/10.1093/mnras/stae1613)

(ref: Bergamini2023) Bergamini, P., Acebron, A., Grillo, C., et al. 2023, ApJ, 952, 84, doi: [`10.3847/1538-4357/acd643`](http://doi.org/10.3847/1538-4357/acd643)

(ref: Boylan-Kolchin2023) Boylan-Kolchin, M. 2023, Nature Astronomy, 7, 731, doi: [`10.1038/s41550-023-01937-7`](http://doi.org/10.1038/s41550-023-01937-7)

(ref: Bunker2023) Bunker, A. J., Saxena, A., Cameron, A. J., et al. 2023, A&A, 677, A88, doi: [`10.1051/0004-6361/202346159`](http://doi.org/10.1051/0004-6361/202346159)

(ref: Calabro2024) Calabro, A., Castellano, M., Zavala, J. A., et al. 2024, arXiv e-prints, arXiv:2403.12683, doi: [`10.48550/arXiv.2403.12683`](http://doi.org/10.48550/arXiv.2403.12683)

(ref: Cannon1998) Cannon, R. D., Croke, B. F. W., Bell, R. A., Hesser, J. E., & Stathakis, R. A. 1998, MNRAS, 298, 601, doi: [`10.1046/j.1365-8711.1998.01671.x`](http://doi.org/10.1046/j.1365-8711.1998.01671.x)

(ref: Carniani2017) Carniani, S., Maiolino, R., Pallottini, A., et al. 2017, A&A, 605, A42, doi: [`10.1051/0004-6361/201630366`](http://doi.org/10.1051/0004-6361/201630366)

(ref: Carniani2024) Carniani, S., Hainline, K., D’Eugenio, F., et al. 2024a, arXiv e-prints, arXiv:2405.18485, doi: [`10.48550/arXiv.2405.18485`](http://doi.org/10.48550/arXiv.2405.18485)

(ref: Carniani2024b) Carniani, S., D’Eugenio, F., Ji, X., et al. 2024b, arXiv e-prints, arXiv:2409.20533, doi: [`10.48550/arXiv.2409.20533`](http://doi.org/10.48550/arXiv.2409.20533)

(ref: CASATeam2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Castellano2022) Castellano, M., Fontana, A., Treu, T., et al. 2022, ApJL, 938, L15, doi: [`10.3847/2041-8213/ac94d0`](http://doi.org/10.3847/2041-8213/ac94d0)

(ref: Castellano2023) —. 2023, ApJL, 948, L14, doi: [`10.3847/2041-8213/accea5`](http://doi.org/10.3847/2041-8213/accea5)

(ref: Castellano2024) Castellano, M., Napolitano, L., Fontana, A., et al. 2024, arXiv e-prints, arXiv:2403.10238, doi: [`10.48550/arXiv.2403.10238`](http://doi.org/10.48550/arXiv.2403.10238)

(ref: Charbonnel2023) Charbonnel, C., Schaerer, D., Prantzos, N., et al. 2023, A&A, 673, L7, doi: [`10.1051/0004-6361/202346410`](http://doi.org/10.1051/0004-6361/202346410)

(ref: Chavez2014) Chávez, R., Terlevich, R., Terlevich, E., et al. 2014, MNRAS, 442, 3565, doi: [`10.1093/mnras/stu987`](http://doi.org/10.1093/mnras/stu987)

(ref: Chavez2024) —. 2024, arXiv e-prints, arXiv:2404.16261, doi: [`10.48550/arXiv.2404.16261`](http://doi.org/10.48550/arXiv.2404.16261)

(ref: Curtis-Lake2023) Curtis-Lake, E., Carniani, S., Cameron, A., et al. 2023, Nature Astronomy, 7, 622, doi: [`10.1038/s41550-023-01918-w`](http://doi.org/10.1038/s41550-023-01918-w)

(ref: DAntona2005) D’Antona, F., Bellazzini, M., Caloi, V., et al. 2005, ApJ, 631, 868, doi: [`10.1086/431968`](http://doi.org/10.1086/431968)

(ref: DeLooze2014) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62, doi: [`10.1051/0004-6361/201322489`](http://doi.org/10.1051/0004-6361/201322489)

(ref: DErcole2008) D’Ercole, A., Vesperini, E., D’Antona, F., McMillan, S. L. W., & Recchi, S. 2008, MNRAS, 391, 825, doi: [`10.1111/j.1365-2966.2008.13915.x`](http://doi.org/10.1111/j.1365-2966.2008.13915.x)

(ref: Ediss2004) Ediss, G. A., Carter, M., Cheng, J., et al. 2004, in Fifteenth International Symposium on Space Terahertz Technology, ed. G. Narayanan, 181–188

(ref: Feldmann2024) Feldmann, R., Boylan-Kolchin, M., Bullock, J. S., et al. 2024, arXiv e-prints, arXiv:2407.02674, doi: [`10.48550/arXiv.2407.02674`](http://doi.org/10.48550/arXiv.2407.02674)

(ref: FernandezArenas2018) Fernández Arenas, D., Terlevich, E., Terlevich, R., et al. 2018, MNRAS, 474, 1250, doi: [`10.1093/mnras/stx2710`](http://doi.org/10.1093/mnras/stx2710)

(ref: Fernandez-Ontiveros2016) Fernández-Ontiveros, J. A., Spinoglio, L., Pereira-Santaella, M., et al. 2016, ApJS, 226, 19, doi: [`10.3847/0067-0049/226/2/19`](http://doi.org/10.3847/0067-0049/226/2/19)

(ref: Ferrara2023) Ferrara, A., Pallottini, A., & Dayal, P. 2023, MNRAS, 522, 3986, doi: [`10.1093/mnras/stad1095`](http://doi.org/10.1093/mnras/stad1095)

(ref: Finkelstein2023) Finkelstein, S. L., Bagley, M. B., Ferguson, H. C., et al. 2023, ApJL, 946, L13, doi: [`10.3847/2041-8213/acade4`](http://doi.org/10.3847/2041-8213/acade4)

(ref: Forbes2014) Forbes, D. A., Norris, M. A., Strader, J., et al. 2014, MNRAS, 444, 2993, doi: [`10.1093/mnras/stu1631`](http://doi.org/10.1093/mnras/stu1631)

(ref: Forbes2018) Forbes, D. A., Bastian, N., Gieles, M., et al. 2018, Proceedings of the Royal Society of London Series A, 474, 20170616, doi: [`10.1098/rspa.2017.0616`](http://doi.org/10.1098/rspa.2017.0616)

(ref: Fujimoto2023) Fujimoto, S., Arrabal Haro, P., Dickinson, M., et al. 2023, ApJL, 949, L25, doi: [`10.3847/2041-8213/acd2d9`](http://doi.org/10.3847/2041-8213/acd2d9)

(ref: Gardner2006) Gardner, J. P., Mather, J. C., Clampin, M., et al. 2006, Space Sci. Rev., 123, 485, doi: [`10.1007/s11214-006-8315-7`](http://doi.org/10.1007/s11214-006-8315-7)

(ref: Gardner2023) Gardner, J. P., Mather, J. C., Abbott, R., et al. 2023, PASP, 135, 068001, doi: [`10.1088/1538-3873/acd1b5`](http://doi.org/10.1088/1538-3873/acd1b5)

(ref: Gonzalez-Moran2021) González-Morán, A. L., Chávez, R., Terlevich, E., et al. 2021, MNRAS, 505, 1441, doi: [`10.1093/mnras/stab1385`](http://doi.org/10.1093/mnras/stab1385)

(ref: Gratton2012) Gratton, R. G., Carretta, E., & Bragaglia, A. 2012, A&ARv, 20, 50, doi: [`10.1007/s00159-012-0050-3`](http://doi.org/10.1007/s00159-012-0050-3)

(ref: Harikane2024b) Harikane, Y., Inoue, A. K., Ellis, R. S., et al. 2024, arXiv e-prints, arXiv:2406.18352, doi: [`10.48550/arXiv.2406.18352`](http://doi.org/10.48550/arXiv.2406.18352)

(ref: Hashimoto2019) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019, PASJ, 71, 71, doi: [`10.1093/pasj/psz049`](http://doi.org/10.1093/pasj/psz049)

(ref: Ho1997) Ho, L. C. 1997, in Revista Mexicana de Astronomia y Astrofisica Conference Series, Vol. 6, Revista Mexicana de Astronomia y Astrofisica Conference Series, ed. J. Franco, R. Terlevich, & A. Serrano, 5, doi: [`10.48550/arXiv.astro-ph/9606016`](http://doi.org/10.48550/arXiv.astro-ph/9606016)

(ref: Ho1997b) Ho, L. C., Filippenko, A. V., & Sargent, W. L. W. 1997, ApJ, 487, 579, doi: [`10.1086/304642`](http://doi.org/10.1086/304642)

(ref: Ho2003) —. 2003, ApJ, 583, 159, doi: [`10.1086/345354`](http://doi.org/10.1086/345354)

(ref: Hsiao2024) Hsiao, T. Y.-Y., Álvarez-Márquez, J., Coe, D., et al. 2024a, arXiv e-prints, arXiv:2404.16200, doi: [`10.48550/arXiv.2404.16200`](http://doi.org/10.48550/arXiv.2404.16200)

(ref: Hsiao2024b) Hsiao, T. Y.-Y., Abdurro’uf, Coe, D., et al. 2024b, ApJ, 973, 8, doi: [`10.3847/1538-4357/ad5da8`](http://doi.org/10.3847/1538-4357/ad5da8)

(ref: Inoue2014) Inoue, A. K., Shimizu, I., Tamura, Y., et al. 2014, ApJL, 780, L18, doi: [`10.1088/2041-8205/780/2/L18`](http://doi.org/10.1088/2041-8205/780/2/L18)

(ref: Inoue2016) Inoue, A. K., Tamura, Y., Matsuo, H., et al. 2016, Science, 352, 1559, doi: [`10.1126/science.aaf0714`](http://doi.org/10.1126/science.aaf0714)

(ref: Isobe2023) Isobe, Y., Ouchi, M., Tominaga, N., et al. 2023, ApJ, 959, 100, doi: [`10.3847/1538-4357/ad09be`](http://doi.org/10.3847/1538-4357/ad09be)

(ref: ji2024) Ji, X., Übler, H., Maiolino, R., et al. 2024, GA-NIFS: An extremely nitrogen-loud and chemically stratified galaxy at $z\sim 5.55$. [`https://arxiv.org/abs/2404.04148`](https://arxiv.org/abs/2404.04148)

(ref: Jones2024) Jones, G. C., Bunker, A. J., Telikova, K., et al. 2024, arXiv e-prints, arXiv:2405.12955, doi: [`10.48550/arXiv.2405.12955`](http://doi.org/10.48550/arXiv.2405.12955)

(ref: Jones2020) Jones, T., Sanders, R., Roberts-Borsani, G., et al. 2020, ApJ, 903, 150, doi: [`10.3847/1538-4357/abb943`](http://doi.org/10.3847/1538-4357/abb943)

(ref: Kaasinen2017) Kaasinen, M., Bian, F., Groves, B., Kewley, L. J., & Gupta, A. 2017, MNRAS, 465, 3220, doi: [`10.1093/mnras/stw2827`](http://doi.org/10.1093/mnras/stw2827)

(ref: Kaasinen2023) Kaasinen, M., van Marrewijk, J., Popping, G., et al. 2023, A&A, 671, A29, doi: [`10.1051/0004-6361/202245093`](http://doi.org/10.1051/0004-6361/202245093)

(ref: Kakkad2020) Kakkad, D., Mainieri, V., Vietri, G., et al. 2020, A&A, 642, A147, doi: [`10.1051/0004-6361/202038551`](http://doi.org/10.1051/0004-6361/202038551)

(ref: Katz2019) Katz, H., Galligan, T. P., Kimm, T., et al. 2019, MNRAS, 487, 5902, doi: [`10.1093/mnras/stz1672`](http://doi.org/10.1093/mnras/stz1672)

(ref: Killi2023) Killi, M., Watson, D., Fujimoto, S., et al. 2023, MNRAS, 521, 2526, doi: [`10.1093/mnras/stad687`](http://doi.org/10.1093/mnras/stad687)

(ref: Kohandel2023) Kohandel, M., Ferrara, A., Pallottini, A., et al. 2023, MNRAS, 520, L16, doi: [`10.1093/mnrasl/slac166`](http://doi.org/10.1093/mnrasl/slac166)

(ref: Liu2022) Liu, B., & Bromm, V. 2022, ApJL, 937, L30, doi: [`10.3847/2041-8213/ac927f`](http://doi.org/10.3847/2041-8213/ac927f)

(ref: Luridiana2015) Luridiana, V., Morisset, C., & Shaw, R. A. 2015, A&A, 573, A42, doi: [`10.1051/0004-6361/201323152`](http://doi.org/10.1051/0004-6361/201323152)

(ref: Madden2013) Madden, S. C., Rémy-Ruyer, A., Galametz, M., et al. 2013, PASP, 125, 600, doi: [`10.1086/671138`](http://doi.org/10.1086/671138)

(ref: Maiolino2024) Maiolino, R., Scholtz, J., Witstok, J., et al. 2024, Nature, 627, 59, doi: [`10.1038/s41586-024-07052-5`](http://doi.org/10.1038/s41586-024-07052-5)

(ref: Marques-Chaves2024) Marques-Chaves, R., Schaerer, D., Kuruvanthodi, A., et al. 2024, A&A, 681, A30, doi: [`10.1051/0004-6361/202347411`](http://doi.org/10.1051/0004-6361/202347411)

(ref: Melnick2017) Melnick, J., Telles, E., Bordalo, V., et al. 2017, A&A, 599, A76, doi: [`10.1051/0004-6361/201629728`](http://doi.org/10.1051/0004-6361/201629728)

(ref: Mieske2012) Mieske, S., Hilker, M., & Misgeld, I. 2012, A&A, 537, A3, doi: [`10.1051/0004-6361/201117634`](http://doi.org/10.1051/0004-6361/201117634)

(ref: Mowla2024) Mowla, L., Iyer, K., Asada, Y., et al. 2024, arXiv e-prints, arXiv:2402.08696, doi: [`10.48550/arXiv.2402.08696`](http://doi.org/10.48550/arXiv.2402.08696)

(ref: Naidu2022) Naidu, R. P., Oesch, P. A., van Dokkum, P., et al. 2022, ApJL, 940, L14, doi: [`10.3847/2041-8213/ac9b22`](http://doi.org/10.3847/2041-8213/ac9b22)

(ref: Nakazato2023) Nakazato, Y., Yoshida, N., & Ceverino, D. 2023, ApJ, 953, 140, doi: [`10.3847/1538-4357/ace25a`](http://doi.org/10.3847/1538-4357/ace25a)

(ref: Norris2004) Norris, J. E. 2004, ApJL, 612, L25, doi: [`10.1086/423986`](http://doi.org/10.1086/423986)

(ref: Norris2014) Norris, M. A., Kannappan, S. J., Forbes, D. A., et al. 2014, MNRAS, 443, 1151, doi: [`10.1093/mnras/stu1186`](http://doi.org/10.1093/mnras/stu1186)

(ref: Ono2023) Ono, Y., Harikane, Y., Ouchi, M., et al. 2023, ApJ, 951, 72, doi: [`10.3847/1538-4357/acd44a`](http://doi.org/10.3847/1538-4357/acd44a)

(ref: Pallottini2022) Pallottini, A., Ferrara, A., Gallerani, S., et al. 2022, MNRAS, 513, 5621, doi: [`10.1093/mnras/stac1281`](http://doi.org/10.1093/mnras/stac1281)

(ref: Pettini2001) Pettini, M., Shapley, A. E., Steidel, C. C., et al. 2001, ApJ, 554, 981, doi: [`10.1086/321403`](http://doi.org/10.1086/321403)

(ref: Popping2023) Popping, G. 2023, A&A, 669, L8, doi: [`10.1051/0004-6361/202244831`](http://doi.org/10.1051/0004-6361/202244831)

(ref: PortegiesZwart2010) Portegies Zwart, S. F., McMillan, S. L. W., & Gieles, M. 2010, ARA&A, 48, 431, doi: [`10.1146/annurev-astro-081309-130834`](http://doi.org/10.1146/annurev-astro-081309-130834)

(ref: Renzini2015) Renzini, A., D’Antona, F., Cassisi, S., et al. 2015, MNRAS, 454, 4197, doi: [`10.1093/mnras/stv2268`](http://doi.org/10.1093/mnras/stv2268)

(ref: Roberts-Borsani2024) Roberts-Borsani, G., Treu, T., Shapley, A., et al. 2024, arXiv e-prints, arXiv:2403.07103, doi: [`10.48550/arXiv.2403.07103`](http://doi.org/10.48550/arXiv.2403.07103)

(ref: Sanders2023) Sanders, R. L., Shapley, A. E., Topping, M. W., Reddy, N. A., & Brammer, G. B. 2023, ApJ, 955, 54, doi: [`10.3847/1538-4357/acedad`](http://doi.org/10.3847/1538-4357/acedad)

(ref: Schouws2024) Schouws, S., Bouwens, R. J., Ormerod, K., et al. 2024, arXiv e-prints, arXiv:2409.20549, doi: [`10.48550/arXiv.2409.20549`](http://doi.org/10.48550/arXiv.2409.20549)

(ref: Sekimoto2008) Sekimoto, Y., Iizuko, Y., Satou, N., et al. 2008, in Ninteenth International Symposium on Space Terahertz Technology, ed. W. Wild, 253–257

(ref: Seth2014) Seth, A. C., van den Bosch, R., Mieske, S., et al. 2014, Nature, 513, 398, doi: [`10.1038/nature13762`](http://doi.org/10.1038/nature13762)

(ref: Smith2006) Smith, G. H. 2006, PASP, 118, 1225, doi: [`10.1086/507654`](http://doi.org/10.1086/507654)

(ref: Sun2023) Sun, G., Faucher-Giguère, C.-A., Hayward, C. C., et al. 2023, ApJL, 955, L35, doi: [`10.3847/2041-8213/acf85a`](http://doi.org/10.3847/2041-8213/acf85a)

(ref: Taylor2024) Taylor, A. J., Finkelstein, S. L., Kocevski, D. D., et al. 2024, arXiv e-prints, arXiv:2409.06772, doi: [`10.48550/arXiv.2409.06772`](http://doi.org/10.48550/arXiv.2409.06772)

(ref: Terlevich2018) Terlevich, E., Fernández-Arenas, D., Terlevich, R., et al. 2018, MNRAS, 481, 268, doi: [`10.1093/mnras/sty2325`](http://doi.org/10.1093/mnras/sty2325)

(ref: Terlevich1981) Terlevich, R., & Melnick, J. 1981, MNRAS, 195, 839, doi: [`10.1093/mnras/195.4.839`](http://doi.org/10.1093/mnras/195.4.839)

(ref: Topping2024) Topping, M. W., Stark, D. P., Senchyna, P., et al. 2024, MNRAS, 529, 3301, doi: [`10.1093/mnras/stae682`](http://doi.org/10.1093/mnras/stae682)

(ref: Treu2023b) Treu, T., Calabrò, A., Castellano, M., et al. 2023, ApJL, 942, L28, doi: [`10.3847/2041-8213/ac9283`](http://doi.org/10.3847/2041-8213/ac9283)

(ref: Ubler2023) Übler, H., Maiolino, R., Curtis-Lake, E., et al. 2023, A&A, 677, A145, doi: [`10.1051/0004-6361/202346137`](http://doi.org/10.1051/0004-6361/202346137)

(ref: UrrutiaZapata2019) Urrutia Zapata, F., Fellhauer, M., Alarcón Jara, A. G., Matus Carrillo, D. R., & Aravena, C. A. 2019, MNRAS, 489, 2746, doi: [`10.1093/mnras/stz307`](http://doi.org/10.1093/mnras/stz307)

(ref: Vanzella2023) Vanzella, E., Claeyssens, A., Welch, B., et al. 2023, ApJ, 945, 53, doi: [`10.3847/1538-4357/acb59a`](http://doi.org/10.3847/1538-4357/acb59a)

(ref: Wang2023) Wang, B., Fujimoto, S., Labbé, I., et al. 2023, ApJL, 957, L34, doi: [`10.3847/2041-8213/acfe07`](http://doi.org/10.3847/2041-8213/acfe07)

(ref: Webb2015) Webb, J. J., & Leigh, N. W. C. 2015, MNRAS, 453, 3278, doi: [`10.1093/mnras/stv1780`](http://doi.org/10.1093/mnras/stv1780)

(ref: Wolf2010) Wolf, J., Martinez, G. D., Bullock, J. S., et al. 2010, MNRAS, 406, 1220, doi: [`10.1111/j.1365-2966.2010.16753.x`](http://doi.org/10.1111/j.1365-2966.2010.16753.x)

(ref: Yang2022) Yang, L., Morishita, T., Leethochawalit, N., et al. 2022, ApJL, 938, L17, doi: [`10.3847/2041-8213/ac8803`](http://doi.org/10.3847/2041-8213/ac8803)

(ref: Yoon2023) Yoon, I., Carilli, C. L., Fujimoto, S., et al. 2023, ApJ, 950, 61, doi: [`10.3847/1538-4357/acc94d`](http://doi.org/10.3847/1538-4357/acc94d)

(ref: Yung2024) Yung, L. Y. A., Somerville, R. S., Finkelstein, S. L., Wilkins, S. M., & Gardner, J. P. 2024, MNRAS, 527, 5929, doi: [`10.1093/mnras/stad3484`](http://doi.org/10.1093/mnras/stad3484)

(ref: Zavala2024) Zavala, J. A., Castellano, M., Akins, H. B., et al. 2024, arXiv e-prints, arXiv:2403.10491, doi: [`10.48550/arXiv.2403.10491`](http://doi.org/10.48550/arXiv.2403.10491)

[^1]: HII galaxies are compact low-mass systems ($M_\star<10^9\,M_\odot$) whose luminosities are almost completely dominated by a massive recent burst of star formation; see (cite: FernandezArenas2018); (cite: Gonzalez-Moran2021); and reference therein.

[^2]: Note that, despite its young age, GHZ2 shows already a metallicity of $Z\approx5-10\%\,Z_\odot$; (cite: Calabro2024; Castellano2024; Zavala2024).

[^3]: This transition is pumped by photons emitted from singly ionized helium atoms; i.e. He II Ly$\alpha$ photons at $\lambda_{\rm rest}=303.78\,\AA$.

</paper>

Write the methods card for this paper.