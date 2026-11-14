# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...970..137G\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...970..137G",
 "title": "The Empirical and Radiative Transfer Hybrid (EaRTH) Disk Model: Merging Analyses of Protoplanetary Dust Disk Mineralogy and Structure",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Grimble, William",
 "n_authors": 10,
 "arxiv_id": "2405.11061",
 "doi": "10.3847/1538-4357/ad4d91",
 "alma_projects_linked_by_archive": [
  "2017.1.01167.S"
 ]
}
```

Paper text:
<paper>
# The Empirical and Radiative Transfer Hybrid (EaRTH) Disk Model: Merging Analyses of Protoplanetary Dust Disk Mineralogy and Structure

## Abstract

Our understanding of how exoplanets form and evolve relies on analyses of both the mineralogy of protoplanetary disks and their detailed structures; however, these key complementary aspects of disks are usually studied separately. We present initial results from a hybrid model that combines the empirical characterization of the mineralogy of a disk, as determined from its mid-infrared spectral features, with the MCFOST radiative transfer disk model, a combination we call the EaRTH Disk Model. With the results of the mineralogy detection serving as input to the radiative transfer model, we generate mid-infrared spectral energy distributions (SEDs) that reflect both the mineralogical and structural parameters of the corresponding disk. Initial fits of the SED output by the resulting integrated model to $Spitzer~Space~Telescope$ mid-infrared (IRS) spectra of the protoplanetary disk orbiting the nearby T Tauri star MP Mus demonstrate the potential advantages of this approach by revealing details like the dominance of $\mu m$-sized olivine and $\mu m$-sized forsterite in this dusty disk. The simultaneous insight into disk composition and structure provided by the EaRTH Disk methodology should be directly applicable to the interpretation of mid-infrared spectra of protoplanetary disks that will be produced by the James Webb Space Telescope.

# Introduction

In recent years, exoplanets have been detected at a very high rate; it is widely recognized that these planets form in dusty circumstellar (aka protoplanetary) disks orbiting young stars (cite: 2020ARA&A..58..483A). Analysis of the dust in these disks is thus essential to the study of stellar and planetary evolution. We need to understand the relative amounts of constituents in protoplanetary disks and their temperatures in order to establish the disk compositions and physical structures that represent the initial conditions for planet formation. The same methods can be applied to study the composition of dust in a wide variety of circumstellar environments, including outflows from evolved stars and even disks orbiting massive stars (cite: 2006ApJ...638L..29K; 2010AJ....139.1993K).

Protoplanetary disks are comprised mainly of gas and contain a small amount of dust ($\sim 1\%$ of the disk’s mass), but that dust is the main source of opacity in the disk, and this opacity manifests in distinguishable features in the infrared regime of the stellar spectra, such as a prominent peak at 10 $\ensuremath{\mu}m$ and a lesser but still prominent peak at $\sim$20 $\ensuremath{\mu}m$ (cite: 2011ppcd.book...14C). $Spitzer$ IRS spectroscopy of hundreds of classical T Tauri stars has established that properties of dust within the planet-forming ($\sim$0.5-5 au) regions of their disks span a wide range, in terms of degree of silicate crystallinity and grain size distributions. This mineralogical diversity among disks is poorly understood; disk lifetimes, levels of disk irradiation, internal shock waves, and grain transport within disks have all been considered as contributing factors (cite: 2019ApJ...882...33G; 2016ApJS..226....8K; 2009ApJ...690.1193S). However, features of silicates and other minerals are easily and reliably distinguishable and have shown to sensibly model the shape of a disk’s near- to mid-infrared spectrum (cite: 2011ppcd.book..114H).

One useful empirical model in analyzing signatures of dust emission in IR spectra is the two-temperature empirical model, established by (cite: 2009ApJ...690.1193S; 2009ApJS..182..477S). This approach has been used by many authors (cite: 2016ApJ...830...71F; 2015ApJ...810...62R; 2022ApJ...933...54L). The successful use of crystalline materials in the model exposes the lack of clearly known mechanisms underlying their formation in the disk, though (cite: 2009ApJ...690.1193S) postulate rapid grain transport through the disk. However, the simplifying assumption of two isothermal zones that underlies this modeling approach does not yield realistic descriptions of the disk structures where the various dust components reside. Alternatively, another empirical model, the two-layer temperature distribution, assumes that sections of the disk can be modeled based on the assumption that each section has a unique temperature distribution (cite: 2009ApJ...695.1024J; 2010ApJ...721..431J). This model has likewise been used to model SEDs successfully (cite: 2023Natur.620..516P), but struggles to fit spectra over a full mid-IR wavelength range primarily due to the presumption of only one population of dust in the optically thin atmosphere.

In contrast, radiative transfer algorithms are designed to simulate a protoplanetary disk using input parameters corresponding to a set of (potentially overlapping) disk zones, each characterized by parameters such as scale height at some reference radius, flaring exponent, inner radius, viscosity (cite: 1995Icar..114..237D), and dust mass (cite: 2006A&A...459..797P; 2009A&A...498..967P). However, the “off the shelf" versions of such radiative transfer simulations of disk structure generally only incorporate a few simple mineralogies, and radiative transfer algorithms that have included additional mineralogical parameters to more accurately reproduce mid- to far-infrared spectra have generally incorporated limited sets of mineralogies that are fine-tuned to specific systems (cite: 2012ApJ...759L..10M; 2019A&A...623A.106L; 2020A&A...642A.171R; 2022A&A...666A.139A; 2023A&A...672A..30K).

This article demonstrates a prototype methodology that integrates the empirical mineralogical studies in these disks into the radiative transfer based structural analysis of the disks to create a single Empirical and Radiative Transfer Hybrid Disk Model (hereafter the EaRTH Disk Model). This hybrid modeling approach, like previous self-consistent (mineralogical+structural) disk models (cite: 2012ApJ...759L..10M), has the potential to generate highly accurate spectral energy distribution (SED) model outputs in the infrared regime, which we further improve by tuning the parameters of the disk structure, thus providing new insight into the compositions and structures of individual disks. We develop and test this model by fitting high-quality infrared spectral and radio interferometric data available for the nearby T Tauri star/disk system MP Muscae (MP Mus), to demonstrate the model’s potential.

# Methodology

Given the impact of disk mineralogy on the infrared spectrum of the disk, it is intuitive that mineralogical model fits to data will provide important constraints on radiative transfer disk models, which depend on parameters like mineralogy to constrain the structure of the disk. Therefore, we develop a hybrid model based on the following methodology: we first apply a newly developed “two-zone temperature distribution” (TZTD) model to empirically fit the $Spitzer$ IRS spectrum, so as to establish both dust disk mineralogy and radial temperature structure; we use the resulting TZTD-constrained mineralogy as input to MCFOST and, in parallel, determine the MCFOST disk structural parameters that best match the TZTD radial temperature structure; and finally we fine-tune the MCFOST results to fit the $Spitzer$ IRS spectrum (primarily) and ALMA continuum mapping data (secondarily). This methodology forms the basis of the EaRTH Disk Model.

## Empirical Dust Composition Model: Two-Zone Temperature Distribution

The first stage of the EaRTH Disk modeling methodology utilizes the empirical mineralogical analysis of the disk using what we call a two-zone temperature distribution model, which is based on both a two-layer temperature distribution and a two-temperature component model. The two-layer temperature distribution (TLTD) (cite: 2009ApJ...695.1024J; 2010ApJ...721..431J) is a method for mid-infrared spectral analysis that models the SED assuming that the protoplanetary disk can be partitioned into three sections: a puffed-up inner rim, the disk midplane, and the optically thin atmosphere. The hot inner rim and the optically thick midplane characterize the continuum along with stellar emission, while the silicate features manifest from the small dust grains in the optically thin atmosphere. The model is applied to an observed mid-IR spectrum, usually a preprocessed flux density function recorded by the $Spitzer~Space~Telescope$ Infrared Spectrograph (IRS) over a portion of the wavelength range of 5.2-38 $\ensuremath{\mu}m$ (with the upper or lower bound typically set at 17 $\ensuremath{\mu}m$), using mineralogy functions based on mineral opacities and blackbody functions integrated over corresponding disk temperatures. The results returned include the maximum temperatures $T_{max}$ corresponding to the disk components, assumed to decrease radially exponentially according to exponents $q$ corresponding to each component that are also returned, i.e. $$\begin{equation}
T(R)=T_{max}\left(\frac{R}{R_{inner/rim}}\right)^q,
\end{equation}$$ and constants corresponding to the mass fraction of each component, including the individual fractions of each mineralogical component in the disk atmosphere, which can be very helpful in surmising an approximate mineralogy-influenced disk structure. These parameters are estimated using a genetic algorithm (cite: 1995ApJS..101..309C) to minimize the reduced $\chi^2$ value between the spectrum and the model constructed from the model fluxes of individual components,

$$\begin{equation}
\label{chisq}
{\chi}^{2}={\sum_{k}[{\frac{F_{\nu}({\lambda}_{k})^{irs}-F_{\nu}({\lambda}_{k})^{mod}}{{\Delta}F_{\nu}({\lambda}_{k})^{irs}}}}]^{2},
\end{equation}$$ where $F_{\nu}({\lambda}_{k})_{irs}$ is the flux density of the disk measured by the $Spitzer~Space~Telescope$ at a given wavelength, ${\Delta}F_{\nu}({\lambda}_{k})_{irs}$ is the uncertainty of the flux density at that wavelength, and the modeled flux density is $$\begin{equation}
\label{mod_flux0}
\begin{array}{l}
F_{\nu}({\lambda}_{k})^{mod}=\frac{\pi R_*^2}{d^2}B_{\nu}({\lambda}_{k},T_*)+D1\int_{T_{rim,max}}^{T_{rim,min}}\frac{2\pi}{d^2}B_{\nu}({\lambda}_{k},T)T^{\frac{2-q_{rim}}{q_{rim}}}dT\\
\indent+D2\int_{T_{mid,max}}^{T_{mid,min}}\frac{2\pi}{d^2}B_{\nu}({\lambda}_{k},T)T^{\frac{2-q_{mid}}{q_{mid}}}dT\\
\indent+\Sigma_{i=1}^{N}\Sigma_{i=1}^{M}D_{i,j}\kappa_{i,j}({\lambda}_{k})\int_{T_{atm,max}}^{T_{atm,min}}\frac{2\pi}{d^2}B_{\nu}({\lambda}_{k},T)T^{\frac{2-q_{atm}}{q_{atm}}}dT+\Sigma_{i=1}^{NP}C_iI_i^{PAH}.
\end{array}
\end{equation}$$ The first term represents an approximation of stellar photospheric emission, where $R_*$ is the stellar radius, $d$ is the distance to the star-disk system, and $B_{\nu}({\lambda}_{k}, T)$ is the blackbody intensity at wavelength ${\lambda}_{k}$ for effective stellar temperature $T_*$; the second term represents the puffed-up inner rim, where $D$ is the constant corresponding to the mass fraction of the component in question; the third term represents the disk midplane. These first three terms represent the continuum below the dust features. The fourth term represents the optically thin dusty atmosphere, where $\kappa_{i,j}({\lambda}_{k})$ is the opacity of mineral species $i$ and grain size $j$, $N$ is the total number of species and $M$ is the total number of sizes for a given species; the fifth and final term represents the contribution of polycyclic aromatic hydrocarbons (PAHs), where $I_i^{PAH}$ is the intensity function corresponding to PAH feature $i$, $C_i$ is the constant corresponding to the feature’s contribution to the total flux, and $NP$ is the amount of PAH feature functions.

The TLTD model is particularly effective at fitting observed *Spitzer* spectra over specific sections of the mid-infrared wavelength range, especially regions around the 10 $\mu$m and 20 $\mu$m silicate emission features. However, the model struggles to fit the full *Spitzer* wavelength range, primarily due to the assumption of a single atmospheric dust composition (cite: 2009ApJ...695.1024J; 2010ApJ...721..431J).

The two-temperature (2-T) empirical model (cite: 2009ApJ...690.1193S; 2009ApJS..182..477S) mitigates this limitation, by approximating the mineralogy of a dusty disk under the assumption that the disk can be partitioned into two distinct temperature regimes of equilibrium dust temperature, each with its own distinct dust population. We hereafter frequently refer to these two spatially distinct disk components as the “cool and warm disk atmospheres" since, as we later demonstrate, they can be modeled as spatially distinct physical structures, wherein the warm disk lies interior to the cool disk; these disks are representative estimates of the inner and outer regions of the disk atmosphere, respectively. Within the two-temperature model, the two temperatures are estimated by setting a reasonable range given the materials whose spectral features appear in each disk component via a reduced $\chi^2$ fit between the spectrum and the model constructed from the model fluxes of individual components,

$$\begin{equation}
\label{mod_flux1}
\begin{array}{l}
F_{\nu}({\lambda}_{k})^{mod}=B_{\nu}({\lambda}_k,T_c)[{\Omega}_c+{\sum_i}{a_{c,i}}{\kappa}_i({\lambda}_k)]\\
\indent +B_{\nu}({\lambda}_k,T_w)[{\Omega}_w+{\sum_j}{a_{w,j}}{\kappa}_j({\lambda}_k)].
\end{array}
\end{equation}$$ Here the subscripts $c$ and $w$ denote the cold and warm disk flux densities, respectively, $B_{\nu}({\lambda}_{k}, T)$ is the blackbody intensity at wavelength ${\lambda}_{k}$ for temperature $T$, $\Omega$ is the blackbody solid angle, $a_{c,i}$ is the mass weight of a given disk component ($a_{c,i}$=$m_{c,i}/d^2$), and ${\kappa}_{i}({\lambda}_{k})$ is the opacity corresponding to the same component and wavelength. The $\chi^2$ fit is minimized for each temperature pair to extract the mass weight of each component from the model flux, removing most negative mass weights by setting them to zero until the model minimizing $\chi^2$ has no negative mass weights. Despite the few nonlinear variables, the spectral fits produced by the 2-T model are robust, well representing the atmosphere of a dusty disk via multiple dust populations. However, unlike the TLTD model, the 2-T model does not attempt to represent the realistic structure of a circumstellar, protoplanetary disk.

To take advantage of the best aspects of both models, we have effectively combined them, yielding a hybrid hereafter referred to as the two-zone temperature distribution (TZTD) model. The TZTD model can be parameterized in the form $$\begin{equation}
\label{mod_flux}
\begin{array}{l}
F_{\nu}({\lambda}_{k})^{mod}=\frac{\pi R_*^2}{d^2}B_{\nu}({\lambda}_{k},T_*)\\
\indent+(D1+\Sigma_{i=1}^{N}\Sigma_{j=1}^{M}Dw_{i,j}\kappa_{i,j}({\lambda}_{k}))\int_{T_{warm,min}}^{T_{warm,max}}\frac{2\pi}{d^2}B_{\nu}({\lambda}_{k},T)T^{\frac{2-q_{warm}}{q_{warm}}}dT\\
\indent+(D2+\Sigma_{i=1}^{N}\Sigma_{j=1}^{M}Dc_{i,j}\kappa_{i,j}({\lambda}_{k}))\int_{T_{cool,min}}^{T_{cool,max}}\frac{2\pi}{d^2}B_{\nu}({\lambda}_{k},T)T^{\frac{2-q_{cool}}{q_{cool}}}dT.
\end{array}
\end{equation}$$ where $B_\nu$ is again the Planck function, $D$ represents the constant corresponding to the mass fraction of the components, $\kappa_{i,j}({\lambda}_{k})$ is the opacity of mineral species $i$ and grain size $j$, $N$ is the total number of species, $M$ is the total number of sizes for a given species, and $q$ represents the temperature distribution exponent. In this model, the disk is split into a warm component and cool component with separate dust compositions, as in the 2-T model, but each component is assigned a distinct temperature distribution, in line with the TLTD model. In keeping with the 2-T model, we assume that each component has the same approximate minimum and maximum temperature, i.e., a range of 19 K to 1500 K, respectively, where the upper limit corresponds to a nominal dust sublimation temperature. The adoption of a temperature lower limit allows us to estimate a spectrum that incorporates the bulk of the disk surface without having to fit or estimate the radii corresponding to the outermost detectable emission from the two zones; we leave that estimation to the radiative transfer analysis (§ [2.2](#mcfost)).

In keeping with the TLTD model’s use of a genetic algorithm to fit the nonlinear parameters, we use differential evolution (cite: 1997JGOpt..11..341S), a global optimization genetic algorithm of a stochastic nature, via the `scipy.optimize.differential_evolution` function. We use this function to find the maximum temperatures as well as the radial temperature distribution exponents for both the warm and cool disk components and the dust grain size power law exponent of the whole disk; the allowed ranges for these exponents are $-$1.5 to $-$0.1 and $-$3.9 to $-$3.1, respectively. We permit the temperature search of each component, or zone, to span the full range from 19 K to 1500 K. The component with the higher maximum temperature is taken as the warm disk, and the one with the lower maximum temperature as the cool disk.

For each set of the nonlinear parameters in Equation [\[mod_flux\]](#mod_flux), we perform a linear fit of the component distribution constants to the stellar-subtracted (i.e. the first term of Equation [\[mod_flux\]](#mod_flux)) $Spitzer$ spectrum via the same approach used by the 2-T model. The inherent degeneracies in dust composition as determined via this modeling methodology are discussed and explored in Appendix [\[degeneracy\]](#degeneracy).

## Radiative Transfer Model: MCFOST

We accomplish radiative transfer modelling in EaRTH Disk via the MCFOST code. MCFOST is a 3D continuum and line radiative transfer code that utilizes both Monte Carlo and ray-tracing methods (cite: 2006A&A...459..797P; 2009A&A...498..967P). MCFOST performs these calculations based on a number of different parameters, such as mineralogy (mass fractions, mixtures, and sizes) and disk structure. Both the dust mineralogy (composition) and structural parameters — i.e., inner and outer radii, scale height at a reference radius, and flaring exponent – can be specified for multiple disk components. To specify dust mineralogy, input files specifying complex optical constants $n+i\kappa$ (distinct from opacity $\kappa$) of different minerals and wavelength grids such as that for $Spitzer$ can be provided.

As detailed in (cite: 2006A&A...459..797P; 2009A&A...498..967P), MCFOST uses cylindrical grids, setting individual dust populations in each cell, with the resulting opacities, densities, and temperatures staying constant within the cell for the purposes of considering thermal emission. Opacities and scattering matrices are computed using either Mie theory (cite: 1983uaz..rept.....B) or distribution of hollow spheres (cite: 2003A&A...404...35M). Individual “photon packets" from photospheric and dust thermal emission are tracked as they move through each cell, with the distance of each movement calculated using optical depth. This permits both temperature throughout the disk structure and SEDs to be outputted from the program, as well as images at individual bands.

## EaRTH Disk Modeling Approach

The EaRTH Disk Model utilizes a set of opacities to be used first in the empirical model equation fit, along with the corresponding parameters defining the opacity of a given mineral (optical indices and grain sizes) to be used with MCFOST. This set of opacities, discussed in Appendix [\[opacsec\]](#opacsec), is generated using the infrastructure of MCFOST itself for use with MCFOST after the empirical model returns the presence and amounts of these constituents; this union is what effectively integrates the empirical and radiative transfer models into a single hybrid model, the EaRTH Disk Model.

We first constrain the mineral compositions and mass fractions of the warm and cool disk components using our empirical model fit to the observed mid-IR spectrum. Next, we use the mass fractions of the detected minerals in the cool and warm disk atmosphere components to determine relative percentages corresponding to the dust population and total mass of each disk component. This is a reasonable starting point for the optically thin regions of the disk, but may not well describe the optically thick regions.

We then use DHS, assuming $V_{max}=0.9$, to compute the scattering and absorption opacity functions and matrices, based on mineralogy derived with our empirical model fit. Simulation of DHS is implemented into MCFOST following the algorithm derived by (cite: 2003A&A...404...35M); we use this MCFOST implementation to estimate the opacity of a mineral over a wide range of grain sizes based on the dust grain size power law. Since we have the opacity functions corresponding to individual grain sizes, we can calculate the opacity of each mineral for a given dust size power law exponent.

As minimum dust grain size has a negligible effect on the infrared SED of a disk (cite: 2016A&A...586A.103W), we set small grains, assumed to be sub-$\ensuremath{\mu}m$ size, to range from 0.01-1 $\ensuremath{\mu}m$, and we assume large grains to have a minimum size of 1 $\ensuremath{\mu}m$; we set the maximum grain size for each large amorphous and crystalline mineral to 2 $\ensuremath{\mu}m$ and 5 $\ensuremath{\mu}m$, respectively, based on the opacities used by (cite: 2010ApJ...721..431J). The set of minerals we use are primarily based on those used with the the two-temperature model by (cite: 2016ApJ...830...71F) but also has partial basis on the set used with the TLTD model by (cite: 2010ApJ...721..431J). This opacity analysis is further detailed in Appendix [\[opacsec\]](#opacsec).

With the mineralogy of the disk and temperature distributions affecting the observed mid-IR spectrum constrained by the empirical model fit, we vary seven other parameters, outlined in Table [\[initparams\]](#initparams) and detailed in the following paragraphs, to find a MCFOST-generated disk temperature structure that matches the empirically fitted temperature distributions. The parameter values that minimize the normalized root mean squared error (NRMSE) — i.e., the RMSE divided by the mean — between the generated and observed temperature structures are taken as the initial representative parameters of the disk; we initially fit the temperature structure rather than SEDs to tie the radiative transfer model directly to the nonlinear parameter results from the empirical fit, and because this method is significantly faster, allowing many iterations to tune parameters to values that approach a strong fit between modeled and observed SEDs. We perform this fit using differential evolution, with bounds for each parameter. After establishing the set of parameters that minimizes the NRMSE between the generated temperature structures, we fine-tune the values individually, as well as other parameters as necessary. This fine-tuning focuses on improving the fit to the mid-IR spectrum of the disk via minimization of the reduced $\chi^2$ value between the stellar-subtracted radiative transfer modeled SED and $Spitzer$ IRS spectrum; while MCFOST generates a photospheric curve, the generated curve is close to the empirically calculated photosphere within the mid-IR regime.

The parameters we vary, as well as their allowed ranges, are partially based on studies by (cite: 2016A&A...586A.103W), which indicate that certain parameters such as scale height and flaring exponent have a noticeable effect on the infrared SED of the disk, while other parameters like column density power law index have a negligible effect; we discuss and study this further in the model assessment in Section [3.3](#assess). We set the range of the viscosity parameter $\alpha$ to 10$^{-4}$-10$^{-1}$, which (respectively) constitute reasonable assumptions for the lower and upper limits for protoplanetary disks (cite: 2019MNRAS.486.4829R; 2020A&A...642A.171R; 2023ASPC..534..645P), assuming the treatment of dust settling by (cite: 1995Icar..114..237D). We alter the distribution of mass in the disk according to the proportional relation $$\begin{equation}
\label{dustdens}
\Sigma~\alpha~r^{p_1},
\end{equation}$$ where $p_1$ is the surface density exponent of the disk.

To reduce the number of parameters fitted, we empirically constrain some parameters based on standard disk models (cite: 2001ApJ...547.1077C; 2001ApJ...560..957D). (cite: 2001ApJ...547.1077C) gives the disk flaring exponent as $$\begin{equation}
\label{flaring1}
\beta=\frac{3}{2}+\frac{1}{2}\frac{d\ln T}{d\ln r}.
\end{equation}$$ Since $q=d\ln{T}/d\ln{r}$ by definition (from our empirical fit), we derive $$\begin{equation}
\label{flaring2}
\beta=\frac{q+3}{2}.
\end{equation}$$ However, since other parameters can affect the temperature distribution, we fit the flaring exponent of both disks. Nevertheless, this empirical flaring exponent should not be ignored; while the fitted parameter may not be exactly the same as the empirical parameter, we seek to ensure they are close in value.

The scale height of the disk at the inner rim is given by $$\begin{equation}
\label{scale1}
h=\sqrt{\frac{kT_{rim}R_{rim}^3}{\mu m_p GM_*}},
\end{equation}$$ where $\mu$ is the mean molecular weight of the gas at the stellar surface (cite: 2001ApJ...560..957D). Following (cite: 1997ApJ...490..368C) and (cite: 2001ApJ...560..957D), we may generalize Eq. [\[scale1\]](#scale1) as $$\begin{equation}
\label{scale2}
h(R)=\sqrt{\frac{kT_{max}(R/R_{in})^q R^3}{\mu m_p GM_*}}.
\end{equation}$$ We can use this function to derive a factor between the scale heights of the warm and cool disks, $$\begin{equation}
\label{scalefactor}
\frac{h_{warm}}{h_{cool}}(R)=\sqrt{\frac{T_{max,warm}(R/R_{in,warm})^{q_{warm}}}{T_{max,cool}(R/R_{in,cool})^{q_{cool}}}}.
\end{equation}$$ We fit the cool scale height at a reference radius of $R=100$ au. Using Eq. [\[scalefactor\]](#scalefactor), we can then empirically estimate the warm disk scale height as well as derive an approximate inner radius for the disk — or, equivalently, the inner radius of the warm disk — via Eq. 14 in (cite: 2001ApJ...560..957D), $$\begin{equation}
\label{inner_rad}
R_{in}=\sqrt{\frac{L_*}{4\pi T_{in}^4 \sigma}\left(1+\frac{H_{in}}{R_{in}}\right)}=R_*\left(\frac{T_*}{T_{max,warm}}\right)^2\sqrt{1+\frac{H_{in}}{R_{in}}},
\end{equation}$$ where $H_{in}$ is the full surface height of the disk inner rim, which is some factor $\chi$ of the warm disk scale height at the inner radius (where $\chi$ is greater than or equal to 1); we adopt the MCFOST default of $\chi=6.95$. Eq. [\[inner_rad\]](#inner_rad) implicitly assumes isotropic luminosity and that the inner rim is at the derived maximum temperature of the warm disk.

We fit the outer radius of the warm disk and the inner radius of the cool disk based on the value of $R_{in}$ determined from Eq. [\[inner_rad\]](#inner_rad), thus permitting the warm and cool disk radial zones to overlap or for a gap to be present between them.

We derive and constrain some disk parameters — namely the mass of the disk, the outer radius of the disk, and the approximate surface density exponent of the cool/outer disk — based on available ALMA data. We further discuss these ALMA data, and the values for the parameters so constrained, in Section [3](#res).

| Parameter | Value Range |
|:---|:--:|
| Warm Disk Flaring Exponent | 0.75-1.5 |
| Warm Disk Surface Density Exponent | -1.5 - -0.5 |
| Warm Disk Outer Radius (au) | 1.1$\times$Inner Radius-11$\times$Inner Radius |
| Cool Disk Inner Radius (au) | 1$\times$Inner Radius-11$\times$Inner Radius |
| Cool Disk Scale Height (au) | 5-15 |
| Cool Disk Flaring Exponent | 0.75-1.5 |
| Viscosity Parameter $\alpha$ | $10^{-4}-10^{-1}$ |

Table notes: The scale height in both sections of the disk is measured at a reference radius of R=100 au.

# Results: Application to the Protoplanetary Disk Orbiting MP Mus

To demonstrate the application of the EaRTH Disk Model to mid-IR spectroscopy data, we have fit the preprocessed $Spitzer$ IRS spectrum of the nearby star/disk system MP Mus (cite: 2010ApJ...723L.248K; 2016ApJ...818L..15W), observed by (cite: 2004sptz.prop..148M). We retrieved the spectrum (AORKEY 5198336) from CASSIS[^1] (cite: 2011ApJS..196....8L) on 2020 May 21; the preprocessing of the $Spitzer$ IRS data is summarized in Appendix [\[process\]](#process).

MP Mus is an actively accreting pre-main sequence star (cite: 2007A&A...465L...5A) of spectral type K1 (cite: 2006A&A...460..695T; 2002AJ....124.1670M), effective temperature 4920 K based on this spectral type (cite: 2013ApJS..208....9P), and stellar radius of $1.45R_{\ensuremath{\odot}}$ based on the star’s bolometric luminosity and effective temperature. The MP Mus star/disk system is of great interest for observation because it constitutes a rare example of an actively accreting T Tauri star with a molecule-rich protoplanetary disk within $\sim$100 pc of Earth (cite: 2010ApJ...723L.248K; 2014A&A...561A..42S). As a member of the $\epsilon$ Cha association, MP Mus likely has an age of $\sim$5 Myr (cite: 2021AJ....161...87D). We adopt a distance of 97.89 pc, as obtained from the inverse of the $Gaia$ DR3 parallax (cite: 2016A&A...595A...1G; 2022arXiv220800211G; 2021A&A...649A...2L) of MP Mus.

MP Mus has been observed in the infrared and mm-range wavelengths to estimate disk parameters (cite: 2016ApJ...818L..15W). (cite: 2005AJ....129.1049C) used the observed 1.2 mm continuum flux to estimate a total dust mass of $5\times10^{-5}M_{\ensuremath{\odot}}$. (cite: 2009ApJ...697.1305C) resolved the disk using Hubble Space Telescope (HST)/NICMOS imaging and estimated an outer radius of 195 au (corrected for the $Gaia$ parallax distance) and disk inclination of $32\ensuremath{^\circ}\pm5\ensuremath{^\circ}$; the latter determination is consistent with that of (cite: 2014AJ....148...59S), who used HST/STIS coronagraphy to estimate a disk inclination of $27.3\ensuremath{^\circ}\pm3.3\ensuremath{^\circ}$. Additionally, based on a comparison between the MP Mus SED and the median Taurus SED, (cite: 2009ApJ...697.1305C) detected a flux deficit in the 4-20 $\ensuremath{\mu}m$ range, indicating either clearing in the disk or a shadow on the disk resulting from a puffed-up rim; however, (cite: 2005A&A...431..165S) estimated an inner radius of 0.1 au, in line with the approximate dust sublimation radius, based on models of the mid-infrared SED, implying that the presence of a shadow is more likely than disk clearing.

Another set of parameter values come from a forthcoming Atacama Large Millimeter Array (ALMA)-based analysis of the disk by Aguayo, Caceres, et al. (private communication). These parameters include a total dust mass of $1.57\times10^{-4}M_{\ensuremath{\odot}}$ (or $1.72\times10^{-4}M_{\ensuremath{\odot}}$ with an additional dust ring in the disk from 80-100 au); a scale height of 5.5 au at a reference radius of 100 au (along with a section of dust with a scale height of 4 au at R=100 au that encompasses R=4.6 au to R=100 au); an inner radius of 0.03 au; an outer radius of 240 au; disk inclination $27.3\ensuremath{^\circ}$ on the basis of HST/STIS imaging (cite: 2014AJ....148...59S); and a stellar radius of $1.65R_{\ensuremath{\odot}}$ based on the star’s bolometric luminosity and effective temperature, estimated at 5035 K, which differs from the estimated effective temperature in this study. A recent analysis of these ALMA data by (cite: 2023A&A...673A..77R) derived a dynamic stellar mass of 1.3 $M_{\ensuremath{\odot}}$, age 7-10 Myr based on this mass, dust disk mass $1.44\times10^{-4}M_{\ensuremath{\odot}}$, dust disk outer radius 60 au, gas disk outer radius 130 au (assuming small grain coupling with gas), and disk inclination $32\ensuremath{^\circ}$, which we adopt as the inclination of our model disk along with the dust disk mass and dust disk outer radius; furthermore, this study also indicates likely shadowing on the disk of MP Mus.

These sets of parameters indicate certain discrepancies in our knowledge of the disk, particularly in the wide range of estimated disk masses. The protoplanetary disk surrounding MP Mus therefore represents fertile ground for application of the EaRTH Disk Model, in an attempt to obtain a more robust set of fundamental disk structural parameters and to investigate disk dust composition.

## Disk Mineralogy

Our mineralogy analysis using the TZTD model with the new opacities indicated dust continuum emission, represented here by very large grains and carbon, in the optically thick atmosphere making up essentially all of the total masses of the warm and cool dust disk components (99.95%$\pm$0.01% and 99.98%$\pm$0.01%, respectively). The model returns a dust temperature distribution parameterization of $T_{warm}(r)=(1500~K)(\frac{r}{r_{in}})^{-1.5}$ and $T_{cool}(r)=(240~K)(\frac{r}{r_{in}})^{-0.9}$, and a dust grain size power law of 3.1. A substantial amount of this optically thick dust is likely very large ($>$0.1 mm) silicates otherwise unrepresented in the fit, and thus does not represent the ratio of carbons and silicates. The results for the mineralogy of the disk excluding the continuum emission (representative of the optically thin portion of the atmosphere) are presented in Figure [1](#mpmus_dust_plots) and in Table [\[comp_table\]](#comp_table), where we find the reduced $\chi^2$ value of the fit to be 2.63; the error within the $Spitzer$ IRS spectrum is taken to be the RMS error from the archival data.

| Dust Component                                  |    Percent    |
|:------------------------------------------------|:-------------:|
| Warm Small Amorphous Pyroxene (wSmAmPy)         |   0$\pm$5.3   |
| Warm Large Amorphous Pyroxene (wLgAmPy)         | 34.8$\pm$10.2 |
| Warm Small Amorphous Olivine (wSmAmOl)          |   0$\pm$6.8   |
| Warm Large Amorphous Olivine (wLgAmOl)          | 56.1$\pm$14.1 |
| Warm Small Amorphous Polivene (wSmAmPo)         |   0$\pm$8.3   |
| Warm Large Amorphous Polivene (wLgAmPo)         |   0$\pm$9.7   |
| Warm Small Crystalline Forsterite (wSmCryForst) |  4.0$\pm$5.3  |
| Warm Small Crystalline Enstatite (wSmCryEnst)   |   0$\pm$4.8   |
| Warm Small Crystalline Silica (wSmCrySil)       |   0$\pm$1.5   |
| Warm Large Crystalline Forsterite (wLgCryForst) |  0$\pm$12.3   |
| Warm Large Crystalline Enstatite (wLgCryEnst)   |  4.3$\pm$6.4  |
| Warm Large Crystalline Silica (wLgCrySil)       |  0.8$\pm$3.5  |

Table notes: Includes full names and abbreviations of materials shown in composition plots in Figure [1](#mpmus_dust_plots); see Appendix [\[uncert\]](#uncert) for process of uncertainty derivation

| Dust Component                                  |    Percent    |
|:------------------------------------------------|:-------------:|
| Cool Small Amorphous Pyroxene (cSmAmPy)         | 76.1$\pm$22.6 |
| Cool Large Amorphous Pyroxene (cLgAmPy)         |  0$\pm$11.7   |
| Cool Small Amorphous Olivine (cSmAmOl)          |   0$\pm$8.4   |
| Cool Large Amorphous Olivine (cLgAmOl)          |   0$\pm$8.7   |
| Cool Small Amorphous Polivene (cSmAmPo)         |  0$\pm$12.4   |
| Cool Large Amorphous Polivene (cLgAmPo)         |  0$\pm$12.1   |
| Cool Small Crystalline Forsterite (cSmCryForst) |  6.9$\pm$5.7  |
| Cool Small Crystalline Enstatite (cSmCryEnst)   |  1.2$\pm$7.4  |
| Cool Small Crystalline Silica (cSmCrySil)       |   0$\pm$5.4   |
| Cool Large Crystalline Forsterite (cLgCryForst) | 15.8$\pm$7.8  |
| Cool Large Crystalline Enstatite (cLgCryEnst)   |   0$\pm$8.1   |
| Cool Large Crystalline Silica (cLgCrySil)       |   0$\pm$7.1   |
| Reduced $\chi^2$ Value                          |     2.63      |

Table notes: Includes full names and abbreviations of materials shown in composition plots in Figure [1](#mpmus_dust_plots); see Appendix [\[uncert\]](#uncert) for process of uncertainty derivation

The results indicate that both disks are predominantly composed of amorphous minerals, with large ($\ensuremath{\mu}m$-sized) amorphous grains in the warm disk and small (sub-$\ensuremath{\mu}m$) pyroxene grains in the cool disk, suggesting grain growth focused in the warmer regions of the disk (cite: 2009ApJS..182..477S). The presence of crystalline silicates also indicates substantial grain processing and growth within the MP Mus disk (cite: 2009ApJS..180...84W); $\ensuremath{\mu}m$-sized forsterite has a prominent presence in the cool disk, as indicated by features in the $Spitzer$ IRS spectrum at wavelengths $>20~\ensuremath{\mu}m$, suggesting grain growth is not limited to the warmer regions of the disk. We note that degeneracies may be present between model dust components; see Appendix [\[degeneracy\]](#degeneracy), where we detail a degeneracy analysis on the new set of components and find significant degeneracies between cool amorphous silicates, such as pyroxene and olivine.

## Disk Structure

We implement the detected materials and mass fractions using the new set of opacities into MCFOST accordingly; summing up the mass fraction constants of each disk component and comparing the totals yields an estimate that the cool disk encompasses almost all of the mass of the disk; in this sense, the warm disk can represent the puffed-up inner rim of the disk, while the cool disk represents the rest of the disk, including the midplane and atmosphere of the disk.

We use the EaRTH Disk Model to calculate the disk structural parameters and list the resulting parameters, including the reduced $\chi^2$ value of the MCFOST generated model and the $Spitzer$ IRS spectrum, found to be 10.81, in Table [\[mpmusres\]](#mpmusres). This result was established by fine-tuning the parameters to fit the $Spitzer$ IRS spectrum after the fit to the temperature structure. We demonstrate the result of the corresponding MCFOST model as compared to the observed spectrum in Figure [2](#mpmus_seds), alongside the mineralogy fit generated by the TZTD model, as well as the modeled temperature structure of the disk, which is compared to the empirically fitted temperature distribution parameterization, in Figure [3](#mpmus_temp). In Figure [4](#mpmus_comp), we illustrate the contributions of various emission and scattering components to the best-fit radiative transfer model. We further demonstrate how variations in these parameters alter the model mid-IR SED in Figure [5](#both_disk_effects).

As can be seen from the best-fit SED and the reduced $\chi^2$ value, upon using the mineralogical input from the TZTD model, MCFOST produces a robust fit in the infrared regime; the fit well reproduces the 10-$\ensuremath{\mu}m$ feature, the 15-$\ensuremath{\mu}m$ valley, the $\sim$20-$\ensuremath{\mu}m$ spike, and the overall pattern. However, as the comparison demonstrates, with a reduced $\chi^2$ value of 2.63, the TZTD model fit alone more robustly captures these features, as well as smaller features in the longer-wavelength infrared that the combined model fails to capture, particularly the boundaries of the wavelength range. This slight mismatch demonstrates the inherent tendency of the EaRTH Disk Model to propagate systematic errors in feature wavelengths that are present in the TZTD model fit, given this fit serves as the MCFOST mineralogical input; for example, both the empirical and radiative transfer SEDs have a slight mismatch in the 12-16 $\ensuremath{\mu}m$ range, likely the result of mispointing, which we account for as detailed in Appendix [\[misp\]](#misp).

## Model Assessment

As a result of the model’s tendency to propagate the errors from the TZTD fit, as well as the presence of physical structural constraints in MCFOST (and by extension the EaRTH Disk Model) that are not present in the TZTD model, the TZTD model will always produce a more robust fit than the EaRTH Disk Model; we again stress that degeneracy between dust components must be considered, as is discussed in Appendix [\[degeneracy\]](#degeneracy). However, despite the additional parameters, as demonstrated in Figure [2](#mpmus_seds), the EaRTH Disk Model fit is visually very close to that of the TZTD model fit; the reduced $\chi^2$ value of the EaRTH Disk Model fit is still relatively low, which demonstrates the robustness of the model in fitting the infrared SED to both mineralogical and structural disk parameters.

Additionally, many of the values are similar to those predicted by other studies. For example, the inner radius, 0.08 au, is consistent with the determinations by (cite: 2005A&A...431..165S), Aguayo, Caceres, et al. (in prep.) and (cite: 2023A&A...673A..77R). Also, while the outer radius of 60 au we adopted based on the ALMA study by (cite: 2023A&A...673A..77R) was effective in constraining the structural fit, we later tuned it to 53 au to match up with the edge falloff observed in the ALMA image and radial profile, a value which remained an effective constraint on the fit. These agreements are a promising demonstration of the hybrid model’s capabilities.

A complicating factor to be considered is that mass absorption coefficients are typically used as the opacity functions with mid-infrared empirical mineralogical models (cite: 2009ApJ...695.1024J; 2010ApJ...721..431J; 2009ApJ...690.1193S; 2009ApJS..182..477S); such is the case with the TZTD model as well. These functions do not, and typically cannot, account for scattering opacity, and therefore implicitly assume that thermal emission, from both disk and star (which can be removed in advance and is removed in the EaRTH Disk Model; see Section [2.1](#2tmodel)), is the sole source of flux in the mid-infrared regime. Scattering is accounted for in MCFOST, however, and Figure [4](#mpmus_comp) demonstrates this; the dominant contribution to the mid-IR SED, as expected, is thermal emission from disk dust, and contributions from direct and scattered stellar photospheric radiation are negligible. However, while scattering of thermal radiation from the disk itself accounts for far less flux in the mid-infrared regime than direct thermal emission, the scattered dust emission component is not negligible, due to the presence of large grains in the mineralogical fit. This factor must be considered when using the EaRTH Disk Model for structural analysis, particularly if large grains are prevalent in the disk.

Given the computational cost of our EaRTH Disk Model, we were not able to perform a Bayesian analysis to extract robust estimates of the errors on our parameter determination; (cite: 2020A&A...642A.171R) indicates that full Bayesian analyses are not typically feasible with radiative transfer models due to the computation costs typically associated with them. However, as an indication of the acceptable range of parameter values, Figure [5](#both_disk_effects) demonstrates the effects of each parameter on the mid-IR SED of MP Mus. We use these spectra to extract uncertainty estimates based on the $\Delta\chi^2$ approach outlined in Appendix [\[uncert\]](#uncert); we empirically estimate the uncertainties of the inner radius and warm disk scale height using Equations [\[inner_rad\]](#inner_rad) and [\[scalefactor\]](#scalefactor) respectively along with these uncertainties and those derived from the TZTD model fit. Based on this analysis, we surmise that the selected parameters for the fit are optimal for determining the structure of the disk; except for the surface density exponent of the warm inner disk (panel (g) of Figure [5](#both_disk_effects)), as reflected in the large uncertainty of the parameter, altering the parameters highlighted in Table [\[initparams\]](#initparams) has a profound effect on the mid-infrared SED model.

The viscosity parameter can be degenerate with some parameters, so it is necessary to be careful when using the mid-IR SED to determine the parameter value (cite: 2023NewAR..9601674R). For lower values of the viscosity parameter, grain mixing becomes less turbulent, causing larger grains to settle in the midplane (cite: 1995Icar..114..237D; 2016A&A...586A.103W), which reduces their influence in the optically thin atmosphere, reducing mid-IR flux. Therefore, the assumption of the mixture of such grains in the TZTD model likely causes the proper viscosity parameter for the fit to be larger, i.e. a more turbulent, mixed disk; likewise, an empirical model that divides grains into separate zones by size would potentially require a weaker viscosity parameter, with weak turbulence and more settling to permit separation of grains in the disk by size. Thus, in future models using empirical results in radiative transfer modelling, an empirical model selection on the basis of known turbulence, or lack thereof, in the disk would be appropriate.

With this set of parameters, the disk must have a very small inner cavity, with only a radius of 0.08 au; furthermore, based on the temperature distributions from the TZTD model, the EaRTH Disk Model infers a potential gap within the disk at larger radii from $\sim$0.1 au up to $\sim$0.85 au, thereby creating a cavity with some hot dust, near the star, effectively creating a narrow, puffed up inner rim with most of its mass gathered at the inner radius to the point that its remaining mass is negligible at larger radii. The ALMA image (Figure [6](#mpmus_mm)) and VLT/SPHERE image (Figure [7](#mpmus_sphere)) indicate a lack of an inner cavity down to their resolutions, as noted by (cite: 2023A&A...673A..77R). However, the resolution of the ALMA image is 0.01 arcseconds, which translates to a resolution of $\sim$1 au at the $Gaia$ DR3 measured distance of 97.89 pc, so ALMA would not resolve such a cavity. Furthermore, the center of the disk within $\sim$0.1 arcseconds ($\sim$10 au) of the SPHERE image is occulted by the coronagraph, so such an inner cavity would not be imaged. Therefore, as the observed $Spitzer$ IRS spectrum and model indicate, it is possible that there is a small inner cavity in the disk of MP Mus that these images could not show.

This hypothesis is further supported by the temperature structure of the disk (Figure [3](#mpmus_temp)). The maximum temperature of the dust in the disk is $\sim$1350 K, close to the warm maximum temperature of 1500 K returned by the TZTD model. Variations in the inner radius would either introduce hotter dust or remove dust at reasonable temperatures; this further indicates that a puffy inner rim occupying an inner radius of $\sim$0.1 au corresponding to a small cavity undetected by ALMA and SPHERE is a reasonable possibility, along with a main dust disk distribution starting at a radius of $\sim$0.85 au.

## Model Images

| Parameter | Value |
|:---|:--:|
| Warm Disk Flaring Exponent | 0.850$\pm$0.007 |
| Warm Disk Surface Density Exponent | -0.57$\pm$0.39 |
| Warm Disk Outer Radius (au) | (1.30$\pm$0.11)$\times$Inner Radius |
| Cool Disk Inner Radius (au) | (10.5$\pm$0.4)$\times$Inner Radius |
| Cool Disk Scale Height (au) | 12.5$\pm$0.4 |
| Cool Disk Flaring Exponent | 1.05$\pm$0.09 |
| Viscosity Parameter $\alpha$ | $1\times 10^{-2}\pm 7\times 10^{-3}$ |
| Inner Radius (au) | 0.08$\pm$0.25 |
| Warm Disk Scale Height (au) | 1.30$\pm$1.18 |
| Cool Disk Surface Density Exponent | -0.642 |
| Cool Disk Outer Radius (au) | 53 |
| Total Dust Mass ($M_{\ensuremath{\odot}}$) | $1.44\times 10^{-4}$ |
| Reduced $\chi^2$ value | 10.81 |

Table notes: The scale height in both sections of the disk is measured at a reference radius of R=100 au; the top section of the table indicates the parameters directly fitted by the model, the middle section indicates the parameters indirectly fitted, empirically calculated using the above parameters, and the bottom section indicates the parameters constrained using ALMA archival data.

We use the MCFOST model described in Section [3.2](#struc) (see Figure [2](#mpmus_seds) and Table [\[mpmusres\]](#mpmusres)) to generate simulated images at wavelengths of the $H$ band (i.e. 1.662 $\ensuremath{\mu}m$) and 1.3 mm for comparison with these VLT/SPHERE and ALMA images, respectively. The rendered 1.3 mm image is compared to archival continuum mapping data obtained by the ALMA radio telescope at Band 6 (Program ID 2017.1.01167.S), with frequencies of 229.607-247.819 GHz and a 69 mas $\times$ 50 mas Gaussian beam with position angle $-$11.88$\ensuremath{^\circ}$; the simulated 1.3 mm image is blurred with a Gaussian beam of the same parameters. As can be seen in Figure [6](#mpmus_mm), the simulated disk image and radial profile well reproduce the observed image and radial profile within a radial angular size of 0.6 arcseconds, with a NRMSE of 1.02 mJy beam$^{-1}$ between the observed and simulated radial profile and a NRMSE of 1.90 mJy beam$^{-1}$ between the observed and simulated image. However, the flux radially decreases much more slowly in the ALMA image than the EaRTH Disk-simulated image, despite the outer disk’s surface density exponent being estimated based on that of the ALMA image; this is because the real disk does not precisely radially decrease according to a surface density exponent. This is a limitation caused by some of the simplified assumptions of the EaRTH Disk Model, as well as the fact that the model is primarily focused on fitting the mid-IR SED rather than the image; to better fit the image beyond the model, a third intermediate overlapping zone may be necessary, potentially only consisting of very large dust grains.

In Figure [7](#mpmus_sphere) we show the comparison of the normalized $Q_{\phi}$ model image rendered at the $H$ band to the normalized $Q_{\phi}$ image of MP Mus recorded by the infra-red dual imaging and spectrograph (IRDIS) instrument (cite: 2008SPIE.7014E..3LD) of the Spectro-Polarimetic High contrast imager for Exoplanets REsearch (SPHERE) using the European Southern Observatory’s Very Large Telescope (ESO VLT) (cite: 2019A&A...631A.155B), on 2016 March 16; this image was produced by sending the data through the IRDAP pipeline (cite: 2020A&A...633A..64V). We mask the central $\sim$120 mas of the image to approximate the occultation of the star from the coronagraphic imaging as seen in the original SPHERE image. However, besides the significantly narrower flux density peak in the central disk in the model compared to the SPHERE image, the latter demonstrates that MP Mus has a ring, located about 80 au from the central star, which is visible at the $H$ band, that is undetected by ALMA in the mm-wave regime, as Figure [6](#mpmus_mm) confirms; our model, restricted by the outer radius estimated using ALMA data, also fails to capture this ring. This ring, detected by (cite: 2016ApJ...818L..15W), is either the result of the presence of a radially confined over-density of small grains (peaking near $\sim$80 au) (cite: 2018ApJ...863...44A), or is caused by shadowing of the disk at radii $<$80 au (cite: 2023A&A...673A..77R).

To address these possibilities, we first include a small grain ring in an amended model. This ring is permitted a tapered-edge structure, which has a density distribution of

$$\begin{equation}
\label{dustdens2}
\Sigma~\alpha~r^{-\gamma}\exp(-\left(\frac{r}{R_c}\right)^{2-\gamma_{\exp}}),
\end{equation}$$

where $\gamma$ is similar to the surface density exponent in Equation [\[dustdens\]](#dustdens) but with a negative value, $R_c$ is the critical radius of the disk, and $\gamma_{\exp}$ affects the tapering rate with respect to the critical radius. The radial distribution of the ring is set from R=80 au to R=130 au, with an edge parameter of 4.5 (i.e. a density drop outside of these radii following a Gaussian with $\sigma=$4.5) and $R_c=$100 au; we assign it a scale height of 5.25 au at R=100 au, flaring exponent of 1.25, dust mass of $7\times10^{-5}M_{\ensuremath{\odot}}$, surface density exponent 0.5, and $\gamma_{\exp}$=3.0. Furthermore, the very large amorphous carbon grains are removed, leaving only small dust in the $\ensuremath{\mu}m$ and sub-$\ensuremath{\mu}m$ size range. As before, we render images simulating the appearance of MP Mus with the ring at the $H$ band in Figure [7](#mpmus_sphere) along with the simulated image of MP Mus without the observed outer ring; we also render a mid-IR SED corresponding to this model, where it becomes obvious that the inclusion of this ring makes little difference. However, the radial profile well represents that of the SPHERE image, with NRMSE=0.99 normalized $Q_{\phi}$ units.

Alternatively, as proposed by (cite: 2023A&A...673A..77R), the ring could be the result of shadowing of the intermediate regions of the disk by the inner disk; we hence tested a model to simulate this shadowing, this time without a small grain ring. We accomplish this by cutting off the initially modeled disk at 30 au (with mass $\sim$1.1$\times~10^{-4}~M_{\ensuremath{\odot}}$), then setting a new disk from 30-130 au with $\sim$3.44$\times~10^{-5}~M_{\ensuremath{\odot}}$ of very large grains and $7\times~10^{-5}~M_{\ensuremath{\odot}}$ of small grains, scale height of 12.5 au at R=100 au, flaring exponent of 1.3, and surface density exponent -0.642; the small grains are modeled as a tapered-edge disk with edge parameter 4.5 and $\gamma_{\exp}$=3.0, co-spatial with the non-tapered-edge disk of large grains. We end up with results that capture the general shape and peaks of the radial profile but contain an excess of flux in the disk, with NRMSE=0.99 normalized $Q_{\phi}$ units; while this implies a similar degree of success in simulating the SPHERE image as the addition of the ring, qualitatively, the image of the ring appears closer to reality (comparing panels (c) and (d) of Figure [7](#mpmus_sphere)) while also producing a mid-IR SED that more closely fits the $Spitzer$ IRS spectrum. This is indicative of the inherent degeneracy in the parameters that must be considered when generating representative models of a disk; however, using multiple data sources, such as a comparison of $Spitzer$ and SPHERE data, can expose degenerate models while also indicating which model is closer to reality.

Both of these disk models maintain the estimated inner radius of $\sim$0.08 au. The dust mass in both cases was initialized to the mass estimated by (cite: 2023A&A...673A..77R), with an additional $7~\times~10^{-5}~M_{\ensuremath{\odot}}$ of dust, either in the ring or the general outer area of the disk. The low value of $\gamma$ in both disks is necessary to permit the distribution of mass in the disk such that the infrared flux from the outer part of the disk is as large as it is; otherwise, most of the mass will be contained at smaller radii and reduce flux from the outer portions of the disk. The values of $\gamma_{\exp}$ capture the large-radii falloff from the R=80 au flux peak. In both cases, setting the outer radius at 130 au, the outer radius of the gas/small grain disk measured by (cite: 2023A&A...673A..77R), results in models that match the data.

# Conclusions

We have presented a new modeling framework, the Empirical and Radiative Transfer (EaRTH) Disk Model, which integrates two complementary modeling approaches to elucidate the compositions and density structures of the dust components of circumstellar, protoplanetary disks orbiting young stars. This model operates on the following methodology:\
1) apply a “two-zone temperature distribution” (TZTD) model we developed to empirically fit the $Spitzer$ IRS spectrum, so as to establish both dust disk mineralogy and radial temperature structure\
2) use the resulting TZTD-constrained mineralogy as input to MCFOST and, in parallel, determine the MCFOST disk structural parameters that best match the TZTD radial temperature distribution\
3) fine-tune the MCFOST results to fit the $Spitzer$ IRS spectrum (primarily) and ALMA continuum mapping data (secondarily).

We use the EaRTH Disk Model to analyze archival Spitzer IRS and ALMA mm-wave data for the nearby pre-MS star/disk system MP Mus as a demonstration of the model’s promise to yield integrated mineralogy and structural parameters for protoplanetary disks. The modeling indicates MP Mus has a dense inner disk (scale height to radius ratio ranging from 0.036-0.037), effectively a puffed-up inner rim, which is composed primarily of large amorphous silicates (dominated by amorphous olivine) but includes a significant ($\sim$8$\%$) crystalline silicate (small forsterite and large enstatite) component. The warm inner disk extends from $\sim$0.08 au to $\sim$0.1 au, inside of which is a small, thus far unobserved cavity; this disk then gives way to a gap or otherwise area of negligible dust up to a radius of 0.85 au, followed by an outer disk that is more forsterite-rich, with scale height to radius ratio ranging from 0.1 to 0.12 at the outermost radii of the disk. The total disk dust mass of 1.44$\times10^{-4}~M_{\ensuremath{\odot}}$ and outer disk radius of $\sim$53 au used within our EaRTH Disk modeling are based on previous ALMA estimates and enhance the analysis.

Challenges remain to improve the model; the mineralogical output can be improved to better capture finer features in different mid-infrared SEDs, so different realistic mineralogical distributions can be tested for improved fits and reduced degeneracy. The model is also currently somewhat slow, requiring many radiative transfer models to be generated in sequence and requires further fine-tuning after the fact; if realistic and less complex mineralogy distributions can be produced that improve the mineralogical fit to the mid-IR spectrum, this would speed up the model, potentially removing the need for fine-tuning and/or permitting the use of more parameters in the fit, such as those outlined in Section [3](#res). Furthermore, if other nonlinear variables can be removed and still produce a good fit, the model can be made to run faster; for example, by constraining the minimum temperature of the warm disk to the maximum temperature of the cool disk, while removing the ability to produce a gap or overlap, the model would not need to fit for the outer radius of the warm disk or the inner radius of the cool disk. A similar result could be achieved with a complex distribution with a pre-generated grid of models; however, due to the number of parameters that can be altered, such a grid would be massive and would take a long time to generate, and then would be tied to a single set of minerals. The mass distribution can also be adjusted in a reasonable way to improve the model, such as constraining the warm and cool disk mass percentages to within an approximate radius where dust thermal emission is predominantly in the mid-infrared while maintaining the overall mass of the disk. Furthermore, the linearly fitted constants corresponding to the dust composition in the TZTD model as well as the original TLTD model contain factors corresponding to the fitted disk parameters $T_{max}$ and $q$, as well as $r_{in}$ (cite: 2009ApJ...695.1024J), which were disregarded as part of the constant since they do not affect the non-linear parameters; however, they can affect the linearly fitted dust component constants, which, while not affecting the composition, can affect the relative mass percentages of the warm and cool disk.

The Mid-Infrared Instrument (MIRI) Medium Resolution Spectrometer (MRS) aboard the James Webb Space Telescope (JWST) (cite: 2015PASP..127..646W) will soon produce spectra at sensitivity and spectral resolution far exceeding those of $Spitzer$/IRS. The EaRTH Disk model methodology described here should offer a particularly effective means to analyze JWST/MRS spectroscopy of dusty disks, enabling optimal extraction of the information that is inherent in such data concerning both disk composition and structure.

# Acknowledgements

We thank the anonymous referee for their careful review and helpful comments which helped to greatly improve this article.

This research was supported by NASA Astrophysics Data Analysis Program grant 80NSSC22K0625 and NASA Exoplanets Program grant 80NSSC19K0292 to RIT.

Partial support for this work was provided by Vanderbilt University’s Frist Center for Autism & Innovation.

This research has made use of the NASA/ IPAC Infrared Science Archive, which is operated by the Jet Propulsion Laboratory, California Institute of Technology, under contract with the National Aeronautics and Space Administration.

This work is based in part on observations made with the $Spitzer~Space~Telescope$, obtained from the NASA/ IPAC Infrared Science Archive, both of which are operated by the Jet Propulsion Laboratory, California Institute of Technology under a contract with the National Aeronautics and Space Administration.

This research makes use of data products from the Two Micron All Sky Survey, which is a joint project of the University of Massachusetts and the Infrared Processing and Analysis Center/California Institute of Technology, funded by the National Aeronautics and Space Administration and the National Science Foundation.

This work has made use of data from the European Space Agency (ESA) mission *Gaia* (<https://www.cosmos.esa.int/gaia>), processed by the *Gaia* Data Processing and Analysis Consortium (DPAC, <https://www.cosmos.esa.int/web/gaia/dpac/consortium>). Funding for the DPAC has been provided by national institutions, in particular the institutions participating in the *Gaia* Multilateral Agreement.

This research has made use of the SIMBAD database, operated at CDS, Strasbourg, France.

This research has made use of the VizieR catalogue access tool, CDS, Strasbourg, France (DOI : 10.26093/cds/vizier). The original description of the VizieR service was published in 2000, A$\&$AS 143, 23.

The online documentation for SciPy (cite: 2020SciPy-NMeth) was referenced for the utility of some Python functions, as well as sample code to see how the functions work, particularly `scipy.interpolate.interp1d` for data interpolation. The program made significant use of NumPy (cite: oliphant2006guide) (cite: 2011CSE....13b..22V) and AstroPy (cite: 2013A&A...558A..33A). Graph plotting was done using Matplotlib (cite: Hunter:2007).

This research made use of the Heidelberg - Jena - St.Petersburg - Database of Optical Constants (HJPDOC) for the retrieval of silicate optical constants (cite: 1999A&AS..136..405H; 2003JQSRT..79..765J).

This paper makes use of the following ALMA data: [ADS/JAO.ALMA#2017.1.01167.S](ADS/JAO.ALMA#2017.1.01167.S). ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

Part of the data are retrieved from the JVO portal (<http://jvo.nao.ac.jp/portal>) operated by the NAOJ.

Images of MCFOST (cite: 2022ascl.soft07023P) data were rendered by making use of pymcfost (cite: 2022ascl.soft07024P).

C. Caceres acknowledges support by ANID BASAL project FB210003.

MRS acknowledges support by ANID, – Millennium Science Initiative Program – NCN19_171, and FONDECYT (grant 1221059).

natexlab

(ref: 2020ARA&A..58..483A) Andrews, S. M. 2020, ARA&A, 58, 483, doi: [`10.1146/annurev-astro-031220-010302`](http://doi.org/10.1146/annurev-astro-031220-010302)

(ref: 2022A&A...666A.139A) Arabhavi, A. M., Woitke, P., Cazaux, S. M., et al. 2022, A&A, 666, A139, doi: [`10.1051/0004-6361/202141825`](http://doi.org/10.1051/0004-6361/202141825)

(ref: 2007A&A...465L...5A) Argiroffi, C., Maggio, A., & Peres, G. 2007, A&A, 465, L5, doi: [`10.1051/0004-6361:20067016`](http://doi.org/10.1051/0004-6361:20067016)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018ApJ...863...44A) Avenhaus, H., Quanz, S. P., Garufi, A., et al. 2018, ApJ, 863, 44, doi: [`10.3847/1538-4357/aab846`](http://doi.org/10.3847/1538-4357/aab846)

(ref: 1976ApJ...210..642A) Avni, Y. 1976, ApJ, 210, 642, doi: [`10.1086/154870`](http://doi.org/10.1086/154870)

(ref: 2019A&A...631A.155B) Beuzit, J. L., Vigan, A., Mouillet, D., et al. 2019, A&A, 631, A155, doi: [`10.1051/0004-6361/201935251`](http://doi.org/10.1051/0004-6361/201935251)

(ref: 1983uaz..rept.....B) Bohren, C. F., & Huffman, D. R. 1983, Absorption and scattering of light by small particles, Tech. rep.

(ref: 2011ppcd.book...14C) Calvet, N., & D’Alessio, P. 2011, Protoplanetary Disk Structure and Evolution, ed. P. J. V. Garcia, 14–54

(ref: 2005AJ....129.1049C) Carpenter, J. M., Wolf, S., Schreyer, K., Launhardt, R., & Henning, T. 2005, AJ, 129, 1049, doi: [`10.1086/427131`](http://doi.org/10.1086/427131)

(ref: 2009ApJ...690..496C) Chapman, N. L., Mundy, L. G., Lai, S.-P., & Evans, Neal J., I. 2009, ApJ, 690, 496, doi: [`10.1088/0004-637X/690/1/496`](http://doi.org/10.1088/0004-637X/690/1/496)

(ref: 1995ApJS..101..309C) Charbonneau, P. 1995, ApJS, 101, 309, doi: [`10.1086/192242`](http://doi.org/10.1086/192242)

(ref: 1997ApJ...490..368C) Chiang, E. I., & Goldreich, P. 1997, ApJ, 490, 368, doi: [`10.1086/304869`](http://doi.org/10.1086/304869)

(ref: 2001ApJ...547.1077C) Chiang, E. I., Joung, M. K., Creech-Eakman, M. J., et al. 2001, ApJ, 547, 1077, doi: [`10.1086/318427`](http://doi.org/10.1086/318427)

(ref: 2002A&A...391..267C) Chihara, H., Koike, C., Tsuchiyama, A., Tachibana, S., & Sakamoto, D. 2002, A&A, 391, 267, doi: [`10.1051/0004-6361:20020791`](http://doi.org/10.1051/0004-6361:20020791)

(ref: 2009ApJ...697.1305C) Cortes, S. R., Meyer, M. R., Carpenter, J. M., et al. 2009, ApJ, 697, 1305, doi: [`10.1088/0004-637X/697/2/1305`](http://doi.org/10.1088/0004-637X/697/2/1305)

(ref: 2021AJ....161...87D) Dickson-Vandervelde, D. A., Wilson, E. C., & Kastner, J. H. 2021, AJ, 161, 87, doi: [`10.3847/1538-3881/abd0fd`](http://doi.org/10.3847/1538-3881/abd0fd)

(ref: 2008SPIE.7014E..3LD) Dohlen, K., Langlois, M., Saisse, M., et al. 2008, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7014, Ground-based and Airborne Instrumentation for Astronomy II, ed. I. S. McLean & M. M. Casali, 70143L, doi: [`10.1117/12.789786`](http://doi.org/10.1117/12.789786)

(ref: 1995A&A...300..503D) Dorschner, J., Begemann, B., Henning, T., Jaeger, C., & Mutschke, H. 1995, A&A, 300, 503

(ref: 1995Icar..114..237D) Dubrulle, B., Morfill, G., & Sterzik, M. 1995, Icarus, 114, 237, doi: [`10.1006/icar.1995.1058`](http://doi.org/10.1006/icar.1995.1058)

(ref: 2001ApJ...560..957D) Dullemond, C. P., Dominik, C., & Natta, A. 2001, ApJ, 560, 957, doi: [`10.1086/323057`](http://doi.org/10.1086/323057)

(ref: 2001A&A...378..228F) Fabian, D., Henning, T., Jäger, C., et al. 2001, A&A, 378, 228, doi: [`10.1051/0004-6361:20011196`](http://doi.org/10.1051/0004-6361:20011196)

(ref: 2000A&A...364..282F) Fabian, D., Jäger, C., Henning, T., Dorschner, J., & Mutschke, H. 2000, A&A, 364, 282

(ref: 2016ApJ...830...71F) Fogerty, S., Forrest, W., Watson, D. M., Sargent, B. A., & Koch, I. 2016, ApJ, 830, 71, doi: [`10.3847/0004-637X/830/2/71`](http://doi.org/10.3847/0004-637X/830/2/71)

(ref: 2016A&A...595A...1G) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1, doi: [`10.1051/0004-6361/201629272`](http://doi.org/10.1051/0004-6361/201629272)

(ref: 2022arXiv220800211G) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2022, arXiv e-prints, arXiv:2208.00211, doi: [`10.48550/arXiv.2208.00211`](http://doi.org/10.48550/arXiv.2208.00211)

(ref: 2019ApJ...882...33G) Giacalone, S., Teitler, S., Königl, A., Krijt, S., & Ciesla, F. J. 2019, ApJ, 882, 33, doi: [`10.3847/1538-4357/ab311a`](http://doi.org/10.3847/1538-4357/ab311a)

(ref: 1999A&AS..136..405H) Henning, T., Il’In, V. B., Krivova, N. A., Michel, B., & Voshchinnikov, N. V. 1999, A&AS, 136, 405, doi: [`10.1051/aas:1999222`](http://doi.org/10.1051/aas:1999222)

(ref: 2011ppcd.book..114H) Henning, T., & Meeus, G. 2011, Dust Processing and Mineralogy in Protoplanetary Accretion Disks, ed. P. J. V. Garcia, 114–148

(ref: Hunter:2007) Hunter, J. D. 2007, Computing In Science & Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 1998A&A...339..904J) Jaeger, C., Molster, F. J., Dorschner, J., et al. 1998, A&A, 339, 904

(ref: 1994A&A...292..641J) Jaeger, C., Mutschke, H., Begemann, B., Dorschner, J., & Henning, T. 1994, A&A, 292, 641

(ref: 2003A&A...408..193J) Jäger, C., Dorschner, J., Mutschke, H., Posch, T., & Henning, T. 2003a, A&A, 408, 193, doi: [`10.1051/0004-6361:20030916`](http://doi.org/10.1051/0004-6361:20030916)

(ref: 2003A&A...401...57J) Jäger, C., Fabian, D., Schrempel, F., et al. 2003b, A&A, 401, 57, doi: [`10.1051/0004-6361:20030002`](http://doi.org/10.1051/0004-6361:20030002)

(ref: 2003JQSRT..79..765J) Jäger, C., Il’in, V. B., Henning, T., et al. 2003c, JQSRT, 79-80, 765, doi: [`10.1016/S0022-4073(02)00301-1`](http://doi.org/10.1016/S0022-4073(02)00301-1)

(ref: 2009ApJ...695.1024J) Juhász, A., Henning, T., Bouwman, J., et al. 2009, ApJ, 695, 1024, doi: [`10.1088/0004-637X/695/2/1024`](http://doi.org/10.1088/0004-637X/695/2/1024)

(ref: 2010ApJ...721..431J) Juhász, A., Bouwman, J., Henning, T., et al. 2010, ApJ, 721, 431, doi: [`10.1088/0004-637X/721/1/431`](http://doi.org/10.1088/0004-637X/721/1/431)

(ref: 2023A&A...672A..30K) Kaeufer, T., Woitke, P., Min, M., Kamp, I., & Pinte, C. 2023, A&A, 672, A30, doi: [`10.1051/0004-6361/202245461`](http://doi.org/10.1051/0004-6361/202245461)

(ref: 2010AJ....139.1993K) Kastner, J. H., Buchanan, C., Sahai, R., Forrest, W. J., & Sargent, B. A. 2010a, AJ, 139, 1993, doi: [`10.1088/0004-6256/139/5/1993`](http://doi.org/10.1088/0004-6256/139/5/1993)

(ref: 2006ApJ...638L..29K) Kastner, J. H., Buchanan, C. L., Sargent, B., & Forrest, W. J. 2006, ApJ, 638, L29, doi: [`10.1086/500804`](http://doi.org/10.1086/500804)

(ref: 2010ApJ...723L.248K) Kastner, J. H., Hily-Blant, P., Sacco, G. G., Forveille, T., & Zuckerman, B. 2010b, ApJL, 723, L248, doi: [`10.1088/2041-8205/723/2/L248`](http://doi.org/10.1088/2041-8205/723/2/L248)

(ref: 2016ApJS..226....8K) Kim, K. H., Watson, D. M., Manoj, P., et al. 2016, ApJS, 226, 8, doi: [`10.3847/0067-0049/226/1/8`](http://doi.org/10.3847/0067-0049/226/1/8)

(ref: 2011ApJS..196....8L) Lebouteiller, V., Barry, D. J., Spoon, H. W. W., et al. 2011, The Astrophysical Journal Supplement Series, 196, 8, doi: [`10.1088/0067-0049/196/1/8`](http://doi.org/10.1088/0067-0049/196/1/8)

(ref: 2021A&A...649A...2L) Lindegren, L., Klioner, S. A., Hernández, J., et al. 2021, A&A, 649, A2, doi: [`10.1051/0004-6361/202039709`](http://doi.org/10.1051/0004-6361/202039709)

(ref: 1998ApJ...496..971L) Lisse, C. M., A’Hearn, M. F., Hauser, M. G., et al. 1998, ApJ, 496, 971, doi: [`10.1086/305397`](http://doi.org/10.1086/305397)

(ref: 2019A&A...623A.106L) Liu, Y., Pascucci, I., & Henning, T. 2019, A&A, 623, A106, doi: [`10.1051/0004-6361/201834418`](http://doi.org/10.1051/0004-6361/201834418)

(ref: 2022ApJ...933...54L) Lu, C. X., Chen, C. H., Sargent, B. A., et al. 2022, ApJ, 933, 54, doi: [`10.3847/1538-4357/ac70d1`](http://doi.org/10.3847/1538-4357/ac70d1)

(ref: 2002AJ....124.1670M) Mamajek, E. E., Meyer, M. R., & Liebert, J. 2002, AJ, 124, 1670, doi: [`10.1086/341952`](http://doi.org/10.1086/341952)

(ref: 2009ApJ...693L..81M) McClure, M. 2009, ApJ, 693, L81, doi: [`10.1088/0004-637X/693/2/L81`](http://doi.org/10.1088/0004-637X/693/2/L81)

(ref: 2012ApJ...759L..10M) McClure, M. K., Manoj, P., Calvet, N., et al. 2012, ApJL, 759, L10, doi: [`10.1088/2041-8205/759/1/L10`](http://doi.org/10.1088/2041-8205/759/1/L10)

(ref: 2004sptz.prop..148M) Meyer, M. R., Backman, D., Beckwith, S. V. W., et al. 2004, The Formation and Evolution of Planetary Systems: Placing Our Solar System in Context, Spitzer Proposal

(ref: 2003A&A...404...35M) Min, M., Hovenier, J. W., & de Koter, A. 2003, A&A, 404, 35, doi: [`10.1051/0004-6361:20030456`](http://doi.org/10.1051/0004-6361:20030456)

(ref: oliphant2006guide) Oliphant, T. E. 2006, A guide to NumPy, Vol. 1 (Trelgol Publishing USA)

(ref: 2013ApJS..208....9P) Pecaut, M. J., & Mamajek, E. E. 2013, The Astrophysical Journal Supplement Series, 208, 9, doi: [`10.1088/0067-0049/208/1/9`](http://doi.org/10.1088/0067-0049/208/1/9)

(ref: 2023Natur.620..516P) Perotti, G., Christiaens, V., Henning, T., et al. 2023, Nature, 620, 516, doi: [`10.1038/s41586-023-06317-9`](http://doi.org/10.1038/s41586-023-06317-9)

(ref: 2022ascl.soft07024P) Pinte, C. 2022, pymcfost: Python interface to the MCFOST 3D radiative transfer code, Astrophysics Source Code Library, record ascl:2207.024

(ref: 2009A&A...498..967P) Pinte, C., Harries, T. J., Min, M., et al. 2009, A&A, 498, 967, doi: [`10.1051/0004-6361/200811555`](http://doi.org/10.1051/0004-6361/200811555)

(ref: 2006A&A...459..797P) Pinte, C., Ménard, F., Duchêne, G., & Bastien, P. 2006, A&A, 459, 797, doi: [`10.1051/0004-6361:20053275`](http://doi.org/10.1051/0004-6361:20053275)

(ref: 2023ASPC..534..645P) Pinte, C., Teague, R., Flaherty, K., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 645, doi: [`10.48550/arXiv.2203.09528`](http://doi.org/10.48550/arXiv.2203.09528)

(ref: 2022ascl.soft07023P) Pinte, C., Ménard, F., Duchêne, G., et al. 2022, MCFOST: Radiative transfer code, Astrophysics Source Code Library, record ascl:2207.023. [`http://ascl.net/2207.023`](http://ascl.net/2207.023)

(ref: 1992nrfa.book.....P) Press, W. H., Teukolsky, S. A., Vetterling, W. T., & Flannery, B. P. 1992, Numerical recipes in FORTRAN. The art of scientific computing

(ref: 2015ApJ...810...62R) Rapson, V. A., Sargent, B., Germano Sacco, G., et al. 2015, ApJ, 810, 62, doi: [`10.1088/0004-637X/810/1/62`](http://doi.org/10.1088/0004-637X/810/1/62)

(ref: 2020A&A...642A.171R) Ribas, Á., Espaillat, C. C., Macı́as, E., & Sarro, L. M. 2020, A&A, 642, A171, doi: [`10.1051/0004-6361/202038352`](http://doi.org/10.1051/0004-6361/202038352)

(ref: 2023A&A...673A..77R) Ribas, Á., Macı́as, E., Weber, P., et al. 2023, A&A, 673, A77, doi: [`10.1051/0004-6361/202245637`](http://doi.org/10.1051/0004-6361/202245637)

(ref: 2023NewAR..9601674R) Rosotti, G. P. 2023, New A Rev., 96, 101674, doi: [`10.1016/j.newar.2023.101674`](http://doi.org/10.1016/j.newar.2023.101674)

(ref: 2019MNRAS.486.4829R) Rosotti, G. P., Tazzari, M., Booth, R. A., et al. 2019, MNRAS, 486, 4829, doi: [`10.1093/mnras/stz1190`](http://doi.org/10.1093/mnras/stz1190)

(ref: 2014A&A...561A..42S) Sacco, G. G., Kastner, J. H., Forveille, T., et al. 2014, A&A, 561, A42, doi: [`10.1051/0004-6361/201322273`](http://doi.org/10.1051/0004-6361/201322273)

(ref: 2006ApJ...645..395S) Sargent, B., Forrest, W. J., D’Alessio, P., et al. 2006, ApJ, 645, 395, doi: [`10.1086/504283`](http://doi.org/10.1086/504283)

(ref: 2009ApJ...690.1193S) Sargent, B. A., Forrest, W. J., Tayrien, C., et al. 2009a, ApJ, 690, 1193, doi: [`10.1088/0004-637X/690/2/1193`](http://doi.org/10.1088/0004-637X/690/2/1193)

(ref: 2009ApJS..182..477S) —. 2009b, The Astrophysical Journal Supplement Series, 182, 477, doi: [`10.1088/0067-0049/182/2/477`](http://doi.org/10.1088/0067-0049/182/2/477)

(ref: 2014AJ....148...59S) Schneider, G., Grady, C. A., Hines, D. C., et al. 2014, AJ, 148, 59, doi: [`10.1088/0004-6256/148/4/59`](http://doi.org/10.1088/0004-6256/148/4/59)

(ref: 2005A&A...431..165S) Schütz, O., Meeus, G., & Sterzik, M. F. 2005, A&A, 431, 165, doi: [`10.1051/0004-6361:20041489`](http://doi.org/10.1051/0004-6361:20041489)

(ref: 2006AJ....131.1163S) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163, doi: [`10.1086/498708`](http://doi.org/10.1086/498708)

(ref: 2006A&A...451..357S) Sogawa, H., Koike, C., Chihara, H., et al. 2006, A&A, 451, 357, doi: [`10.1051/0004-6361:20041538`](http://doi.org/10.1051/0004-6361:20041538)

(ref: 1997JGOpt..11..341S) Storn, R., & Price, K. 1997, Journal of Global Optimization, 11, 341, doi: [`10.1023/A:1008202821328`](http://doi.org/10.1023/A:1008202821328)

(ref: 2006A&A...460..695T) Torres, C. A. O., Quast, G. R., da Silva, L., et al. 2006, A&A, 460, 695, doi: [`10.1051/0004-6361:20065602`](http://doi.org/10.1051/0004-6361:20065602)

(ref: 2005A&A...437..189V) van Boekel, R., Min, M., Waters, L. B. F. M., et al. 2005, A&A, 437, 189, doi: [`10.1051/0004-6361:20042339`](http://doi.org/10.1051/0004-6361:20042339)

(ref: 2011CSE....13b..22V) van der Walt, S., Colbert, S. C., & Varoquaux, G. 2011, Computing in Science and Engineering, 13, 22, doi: [`10.1109/MCSE.2011.37`](http://doi.org/10.1109/MCSE.2011.37)

(ref: 2020A&A...633A..64V) van Holstein, R. G., Girard, J. H., de Boer, J., et al. 2020, A&A, 633, A64, doi: [`10.1051/0004-6361/201834996`](http://doi.org/10.1051/0004-6361/201834996)

(ref: 2020SciPy-NMeth) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`https://doi.org/10.1038/s41592-019-0686-2`](http://doi.org/https://doi.org/10.1038/s41592-019-0686-2)

(ref: 2009ASPC..414...77W) Watson, D. 2009, in Astronomical Society of the Pacific Conference Series, Vol. 414, Cosmic Dust - Near and Far, ed. T. Henning, E. Grün, & J. Steinacker, 77, doi: [`10.48550/arXiv.0902.2744`](http://doi.org/10.48550/arXiv.0902.2744)

(ref: 2009ApJS..180...84W) Watson, D. M., Leisenring, J. M., Furlan, E., et al. 2009, The Astrophysical Journal Supplement Series, 180, 84, doi: [`10.1088/0067-0049/180/1/84`](http://doi.org/10.1088/0067-0049/180/1/84)

(ref: 2001ApJ...548..296W) Weingartner, J. C., & Draine, B. T. 2001, ApJ, 548, 296, doi: [`10.1086/318651`](http://doi.org/10.1086/318651)

(ref: 2015PASP..127..646W) Wells, M., Pel, J. W., Glasse, A., et al. 2015, PASP, 127, 646, doi: [`10.1086/682281`](http://doi.org/10.1086/682281)

(ref: 2016A&A...586A.103W) Woitke, P., Min, M., Pinte, C., et al. 2016, A&A, 586, A103, doi: [`10.1051/0004-6361/201526538`](http://doi.org/10.1051/0004-6361/201526538)

(ref: 2016ApJ...818L..15W) Wolff, S. G., Perrin, M., Millar-Blanchaer, M. A., et al. 2016, ApJL, 818, L15, doi: [`10.3847/2041-8205/818/1/L15`](http://doi.org/10.3847/2041-8205/818/1/L15)

(ref: 2013A&A...553A..81Z) Zeidler, S., Posch, T., & Mutschke, H. 2013, A&A, 553, A81, doi: [`10.1051/0004-6361/201220459`](http://doi.org/10.1051/0004-6361/201220459)

[^1]: The Combined Atlas of Sources with Spitzer IRS Spectra (CASSIS) is a product of the IRS instrument team, supported by NASA and JPL. CASSIS is supported by the "Programme National de Physique Stellaire" (PNPS) of CNRS/INSU co-funded by CEA and CNES and through the "Programme National Physique et Chimie du Milieu Interstellaire" (PCMI) of CNRS/INSU with INC/INP co-funded by CEA and CNES.

</paper>

Write the methods card for this paper.