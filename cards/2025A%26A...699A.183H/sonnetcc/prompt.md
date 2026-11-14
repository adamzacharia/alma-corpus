# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...699A.183H\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...699A.183H",
 "title": "Spatially resolved spectrophotometric SED modeling of NGC 253's central molecular zone: I. Star formation in extragalactic giant molecular clouds",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Humire, Pedro K.",
 "n_authors": 32,
 "arxiv_id": "2501.15082",
 "doi": "10.1051/0004-6361/202553897",
 "alma_projects_linked_by_archive": [
  "2017.1.00161.L",
  "2018.1.00162.S"
 ]
}
```

Paper text:
<paper>
# Spatially-resolved spectro-photometric SED Modeling of NGC 253’s Central Molecular Zone

This study aims to produce and analyze the physical properties of the first spatially-resolved multi-wavelength SED of an extragalactic source that covers six decades in frequency (from near-ultraviolet to centimeter wavelengths) at an angular resolution of 3$^{\prime\prime}$ which corresponds to a linear scale of $\sim$51 pc at the distance of NGC 253. We focus on the central molecular zone (CMZ) of this starburst galaxy, which contains giant molecular clouds (GMCs) responsible for half of the galaxy’s star formation.

We retrieve archival data from near-UV to centimeter wavelengths, covering six decades of spectral range. We compute SEDs to fit the observations using the GalaPy code and confronting results with the CIGALE code for validation. We also employ theSTARLIGHT code to analyze the stellar optical spectra of the GMCs.

Our results reveal significant differences between internal and external GMCs in terms of stellar and dust masses, star formation rates (SFRs), and bolometric luminosities, to provide a few, with internal GMCs doubling maximum values of the external ones in most of the cases. We have obtained tight relations between monochromatic stellar tracers and star-forming conditions obtained from panchromatic emission. We find that the best SFR tracers are radio continuum bands at 33 GHz, radio recombination lines (RRLs), and the total infrared (IR) luminosity range (L$_{\rm IR}$; 8–1000$\mu$m) as well as the IR emission at 60$\mu$m. The emission line diagnostics based on the BPT and WHAN diagrams suggest that the nuclear region of NGC 253 exhibits shock signatures, placing it in the composite zone typically associated with AGN/star-forming region hybrids, while the AGN fraction from panchromatic emission is negligible ($\leq$7.5%).

Our findings demonstrate the significant heterogeneity within the CMZ of NGC 253, with central GMCs exhibiting high densities, elevated SFRs, and greater dust masses compared to their external counterparts. We confirm the effectiveness of certain centimeter photometric bands as a reliable method to estimate the global SFR, in accordance with previous studies but this time on GMC scales.

# Introduction

The panchromatic spectral energy distribution (SED) of an astrophysical system encapsulates the intricate interplay among its various components, including stars in different evolutionary phases and their remnants; molecular, atomic, and ionized gas; dust, and compact objects such as supermassive black holes. It contains the imprints of baryonic processes that drive its formation and evolution across cosmic times. A comparison of SEDs across different wavebands provides crucial constraints into the physical mechanisms governing the system’s radiation, including the relative contributions of stellar, nebular, and dust emission, as well as the processes that regulate its energy balance. Therefore, modeling the SED is one of the most effective tools, if not the most effective, for estimating the specific star formation rate (sSFR), from which the star formation rate (SFR) and the stellar mass ($M_{\rm{\star}}$) can be derived. This method relies on reconstructing the stellar emission through star formation history (SFH) models, which can be either purely theoretical or non-parametric (the latter refers to models that do not assume a specific functional form and rely on templates to infer the SFH; see, e.g., (cite: CidFernandes2005; Cunha08; Conroy2013)). SED fitting allows for a detailed analysis of the light emitted across different wavelengths, providing insights into the age, metallicity, and dust content of the stellar population (cite: Bruzual2003).

While SEDs have been extensively applied to high-redshift galaxies, there are inherent resolution limitations, particularly at far-infrared (FIR) wavelengths. For example, the Herschel SPIRE beam has a resolution of 36$\ensuremath{''}$ at 500 $\mu$m, corresponding to roughly 1 kpc at $z\approx0.0013$, meaning that the observed SEDs often conflate contributions from recent star formation, AGN, and/or stellar outflows, and sub-thermally excited gas, to mention a few. Considering also that a photometric aperture of 2.5 times the beam, assuming a Gaussian profile for the emission source, ensures the capture of extended emission, the problem becomes more critical. Given these constraints, to gain a deeper understanding of the relevant processes affecting galaxies, such as epochs with galaxy-galaxy interactions or times when their star formation began to decline (cite: Hopkins2006; Hopkins_mergers2010), it is imperative to focus on local analogs. In this regard, the extensively studied nearby starburst galaxy NGC 253 serves as an ideal target due to its proximity and intense nuclear star formation, which mirrors conditions seen in distant galaxies (cite: Leroy2015). Focusing on spatially-resolved objects, such as giant molecular clouds (GMCs), allows us to take a significant step forward in producing SED fittings with unprecedented detail, overcoming the aforementioned limitations.

NGC 253 is a nearby starburst galaxy about 3.5 Mpc away with a steep inclination ranging from approximately 70$^\circ$ to 79$^\circ$ (cite: Rekola2005; Pence1980; Iodice2014). Its inner kiloparsec (kpc) region is a hub of vigorous star formation, generating a rate of roughly 1.7 solar masses per year, which constitutes about half of the galaxy’s total star formation activity (cite: Bendo2015; Leroy2015). This active star-forming core encompasses a central molecular zone (CMZ), spanning around 300 parsecs in length and 100 parsec in width projection (cite: Sakamoto2011) and hosting ten giant molecular clouds (GMCs) discerned through molecular and continuum emissions at high resolution (cite: Leroy2015). Notably, studies indicate that an active galactic nucleus (AGN) has minimal impact on the molecular gas within NGC 253’s CMZ (cite: FernandezOntiveros2009; MullerSanchez2010; PerezBeaupuits2018), making it an excellent test-bed to study pure star-forming conditions.

The CMZ of NGC 253, along with its GMCs, has been the focus of the ALMA Comprehensive High-resolution Extragalactic Molecular Inventory (ALCHEMI) program (cite: Martin2021). This project delves into chemical changes caused by shocks or cosmic ray flux density variations, some of them also aiming for a direct comparison with galaxy conditions, the discovery of new molecules, and the characterization of the GMCs that highlights differences between the very central part of the CMZ and its outskirts (cite: Holdship2021; Harada2021; Martin2021; Behrens2022ApJ; Holdship2022ApJ; Humire2022; Harada2022; Butterworth2024; Huang2023; Behrens2024ApJ; Bouvier2024; Tanaka2024ApJ; Harada2024).

Previous studies of the NGC 253 spectral energy distribution (SED) have focused on specific wavelength regimes like optical/IR (cite: FernandezOntiveros2009), mid-IR to (sub-)millimeter (cite: PerezBeaupuits2018), far-UV to far-IR (cite: Beck2022), the Rayleigh-Jeans tail (cite: Martin2021), radio (1 GHz) to sub-mm (350 GHz) (cite: Belfiori2025) and low-frequency radio (MHz to 11 GHz) regimes (cite: Kapinska2017). However, there remains significant potential in extending these investigations across a broader wavelength regime. This extension can provide valuable insights into various physical processes, including levels, the (s)SFR, and the mass-to-dust rates, to provide a few.

In the present article, we aim to create the first extragalactic panchromatic SED (near-ultraviolet to centimeter wavelengths) performed at a linear resolution of 51 pc or 3$''$, at the typical physical size of a giant molecular cloud. For the specific case of this article, given the massive amount of information extracted, we will focus on the stellar processes derived per GMC, such as the SFRs and SFHs.

Along with the acquisition of our new results, we also highlight the importance of testing tracers or proxies that focus on a single wavelength range against the values provided by the full SED to understand the scope of the former in terms of luminosity, ages, object classifications, and calculated SFRs. This way, one can gauge their effectiveness on a larger spectro-photometric wavelength scale.

In the following sections, we will present the collected observations (Sect. [2](#sec.observations)), our SED and spectroscopic modeling (Sect. [3](#sec.SED_and_spec_modeling)), our results with small discussions inside (Sect. [4](#sec.results)), and a general discussion on common limitations of our methods and the placement of our findings in a high-z perspective (Sect. [5](#sec.discussion)), before providing our conclusions in Sect. [6](#sec.conclusions).

# Observations

To ensure consistency in the physical scales analyzed, we extract fluxes using a uniform aperture size with a 3$\ensuremath{''}$ diameter, despite the varying angular resolutions across the sample. The coordinates of all GMCs are listed in Table [1](#tab.positions). A summary of the dataset used in this study is provided in Table [\[Tab.observations\]](#Tab.observations). An over-view of the full information used in this work is presented in Fig. [1](#Fig.summary_plot). Below, we provide a detailed description of the observations conducted with each facility.

## S-PLUS

The Southern Photometric Local Universe Survey (S-PLUS; (cite: MendesdeOliveira2019)) will cover $\sim$9,300 deg$^{2}$ of the southern hemisphere (currently 80% complete), employing 7 narrow-band and 5 broad-band filters, encompassing a wavelength range from 3,533 Å ($u$ filter) to 8,941 Å ($z$ filter). The survey uses a dedicated robotic telescope of 0.8 m called T80-South, at the Cerro Tololo Inter-American Observatory (CTIO) in Chile. The angular resolution is subject to weather conditions, with a typical seeing range of 0.8$''$ to 2.0$''$ and an average of 1.5$''$.

For this work, we have used images in all 12 available filters from the S-PLUS fifth data release (available for internal collaboration), maintaining a consistent angular resolution of 1.5$''$ ($\sim$25.4 pc). For further details on the S-PLUS survey, we refer the reader to (cite: MendesdeOliveira2019) and (cite: Herpich2024).

|  |  |  |  |
|:---|:---|:---|:---|
| Position | $\alpha_{\rm ICRS}$ | $\delta_{\rm ICRS}$ | $v_{\rm LSR}$ |
|  | \[00$^{h}$:47$^{m}$:–$^{s}$\] | \[-25$^{\circ}$:17’:–"\] | \[km s$^{-1}$\] |
|  |  |  |  |
| GMC 1 | 31.93 | 29.00 | 304 |
| GMC 2 | 32.36 | 18.80 | 330 |
| GMC 3 | 32.81 | 21.55 | 286 |
| GMC 4 | 32.97 | 19.97 | 252 |
| GMC 5 | 33.16 | 17.30 | 231 |
| GMC 6 | 33.33 | 15.70 | 180 |
| GMC 7 | 33.65 | 13.10 | 174 |
| GMC 8 | 33.94 | 10.90 | 205 |
| GMC 9 | 34.14 | 12.00 | 201 |
| GMC 10 | 34.24 | 7.84 | 144 |

: Giant Molecular Cloud (GMC) positions.

Table notes: GMC positions taken from (cite: Harada2024) except for GMCs 3, 4, and 10, that were obtained using CPROPS (cite: Rosolowsky2006) on ALCHEMI data at 1.6$''$ angular resolution. The Local Standard of Rest (LSR) velocities were obtained by fitting a local thermodynamic equilibrium model (LTE) to the ALCHEMI spectra and averaging between the A– and E–CH$_{3}$OH symmetry species (see (cite: Humire2022) for further information). The ALCHEMI spectral resolution of $\sim$8–9 km s$^{-1}$ (see Subsect. [2.4](#sec.obs.ALCHEMI)) dominates the velocity uncertainty.

![](Figures/larger_summary_plot_ALCHEMI_in_Angstroms_with_hatched_motives_labelled.pdf)

![](Figures/moments_0_maps_v4_ALCHEMI_newcolor.pdf)

## VLT and HST

This study incorporates the dataset presented in (cite: FernandezOntiveros2009), including Adaptive Optics images from the Very Large Telescope/NaCo (VLT/NaCo) and diffraction-limited images from VLT/VISIR and the Hubble Space Telescope (HST). We refer the reader to (cite: FernandezOntiveros2009) for further details.

The VLT/NaCo observations were conducted on December 2 and 4, 2005, utilizing the IR wavefront sensor (dichroic N90C10) for atmospheric correction. The observation included the following filters and integration times: J (600 s; 3% Strehl ratio[^1]), Ks (500 s; 20% SR), L (4.375 s; 40% SR), and NB$\_$4.05 (8.75 s, centered on Br$\alpha$; 40% SR). The resulting images achieved different Full Width at Half Maximum (FWHM) resolutions: 0.29$''$ (J), 0.24$''$ (Ks), 0.13$''$ (L), and 0.14$''$ (NB$\_$4.05). Images from VLT/VISIR, captured on December 1, 2004, and October 9, 2005, encompassed the N (PAH2$\_$2, $\lambda$11.88$\mu$m, $\delta\lambda$0.37$\mu$m; 2826 s) and Q (Q2, $\lambda$18.72$\mu$m, $\delta\lambda$0.88$\mu$m; 6237 s) bands. The achieved FWHM resolutions were 0.4$''$ (N) and 0.74$''$ (Q). Furthermore, HST images were utilized within the central $\sim$300 pc region of NGC 253, employing the F555W (V band, FWHM = 0.11$''$), F656N (H$\alpha$, 0.22$''$), F675W (R band, 0.20$''$), F814W (I band, 0.13$''$), and F850LP (0.13$''$) filters.

| Source | $\lambda$ \[Å\] | FWHM \[$\ensuremath{''}$\] | $\theta_{\rm{LAS}}$ \[$\ensuremath{''}$\] | GMC 1 | GMC 2 | GMC 3 | GMC 4 | GMC 5 | GMC 6 | GMC 7 | GMC 8 | GMC 9 | GMC 10 |
|:---|---:|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
|  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| S-PLUS/uJAVA | 3,563 | $1.5$ | – | 0.03 | 0.03 | 0.03 | 0.04 | 0.03 | 0.04 | 0.05 | 0.06 | 0.05 | 0.04 |
| S-PLUS/J0378 | 3,770 | $1.5$ | – | 0.04 | 0.04 | 0.04 | 0.04 | 0.05 | 0.04 | 0.08 | 0.09 | 0.08 | 0.06 |
| S-PLUS/J0395 | 3,940 | $1.5$ | – | 0.05 | 0.05 | 0.05 | 0.07 | 0.06 | 0.07 | 0.11 | 0.10 | 0.11 | 0.08 |
| S-PLUS/J0410 | 4,094 | $1.5$ | – | 0.07 | 0.07 | 0.08 | 0.10 | 0.10 | 0.12 | 0.16 | 0.19 | 0.18 | 0.13 |
| S-PLUS/J0430 | 4,292 | $1.5$ | – | 0.09 | 0.09 | 0.10 | 0.13 | 0.12 | 0.14 | 0.20 | 0.24 | 0.20 | 0.18 |
| S-PLUS/gSDSS | 4,751 | $1.5$ | – | 0.13 | 0.15 | 0.24 | 0.31 | 0.26 | 0.30 | 0.40 | 0.44 | 0.38 | 0.31 |
| S-PLUS/J0515 | 5,133 | $1.5$ | – | 0.15 | 0.17 | 0.29 | 0.37 | 0.31 | 0.35 | 0.49 | 0.54 | 0.45 | 0.37 |
| HST/F555W | 5,443 | $0.1$ | – | – | – | – | 0.74 | 0.63 | 0.70 | 0.89 | 0.79 | – | – |
| S-PLUS/rSDSS | 6,258 | $1.5$ | – | 0.35 | 0.42 | 1.07 | 1.56 | 1.22 | 1.24 | 1.43 | 1.37 | 1.10 | 0.87 |
| S-PLUS/J0660 | 6,614 | $1.5$ | – | 0.43 | 0.56 | 1.89 | 3.27 | 2.39 | 2.16 | 2.35 | 1.94 | 1.49 | 1.13 |
| HST/F675W | 6,718 | $0.1$ | – | – | – | – | 2.46 | 1.96 | 1.86 | 2.05 | 1.69 | – | – |
| S-PLUS/iSDSS | 7,690 | $1.5$ | – | 0.65 | 0.84 | 2.56 | 3.94 | 3.08 | 2.90 | 2.80 | 2.53 | 1.91 | 1.53 |
| HST/F814W | 7,996 | $0.1$ | – | – | – | – | 6.28 | 4.81 | 4.15 | 3.78 | 2.98 | – | – |
| S-PLUS/J0861 | 8,611 | $1.5$ | – | 0.88 | 1.24 | 3.94 | 6.46 | 5.20 | 4.71 | 4.08 | 3.40 | 2.55 | 2.01 |
| S-PLUS/zSDSS | 8,831 | $1.5$ | – | 1.07 | 1.52 | 5.11 | 9.07 | 7.08 | 6.07 | 4.97 | 4.06 | 2.93 | 2.35 |
| HST/F850LP | 9,114 | $0.13$ | – | – | – | – | 12.53 | 8.93 | 6.95 | 5.48 | 3.87 | – | – |
| VLT/J | 12,650 | $0.29$ | – | – | – | 22.01 | 45.75 | 31.77 | 20.08 | 9.88 | – | – | – |
| VLT/K | 21,800 | $0.24$ | – | – | – | 31.16 | 93.29 | 71.15 | 39.01 | – | – | – | – |
| Spitzer/IRAC 3.6$\mu$m | 36,000 | $1.66$ | – | 2.71 | 5.72 | 28.40 | 106.38 | 109.02 | 62.01 | 23.41 | 12.60 | 6.27 | 6.30 |
| Spitzer/IRAC 4.5$\mu$m | 45,000 | $1.72$ | – | 2.43 | 4.78 | 28.08 | 150.28 | 150.45 | 69.47 | 21.64 | 10.77 | 5.20 | 5.79 |
| Spitzer/IRAC 5.8$\mu$m | 58,000 | $1.88$ | – | 7.23 | 17.75 | 121.03 | 357.56 | 464.85 | 250.73 | 89.61 | 45.28 | 22.27 | 22.98 |
| Spitzer/IRAC 8.0$\mu$m | 80,000 | $1.98$ | – | 18.98 | 52.71 | 335.32 | 1016.10 | 1095.98 | 644.08 | 243.56 | 120.51 | 60.60 | 61.62 |
| VLT/N | 118,800 | $0.4$ | – | – | – | 287.88 | 3207.94 | 1273.06 | 477.52 | 121.49 | – | – | – |
| VLT/Q | 187,200 | $0.74$ | – | – | – | 1178.25 | 18901.04 | 9984.58 | 3340.52 | 654.91 | 355.37 | – | – |
| ALMA/B7 | 9,252,854 | $1.6$ | 15 | 11.48 | 9.63 | 188.92 | 289.28 | 343.56 | 255.51 | 51.86 | 18.37 | 18.35 | 17.51 |
| ALMA/B6 | 12,337,138 | $1.6$ | 15 | 2.58 | 3.28 | 68.74 | 122.77 | 165.38 | 103.49 | 17.11 | 5.82 | 5.17 | 6.45 |
| ALMA/B5 | 16,031,682 | $1.6$ | 15 | 2.85 | 1.91 | 35.92 | 72.02 | 110.39 | 58.05 | 8.34 | 3.07 | 2.86 | 2.64 |
| ALMA/B4 | 20,818,921 | $1.6$ | 15 | 1.29 | 1.57 | 24.13 | 56.96 | 101.44 | 40.57 | 5.76 | 2.37 | 1.69 | 2.50 |
| ALMA/B3 | 29,979,246 | $1.6$ | 15 | – | – | 18.41 | 50.46 | 102.15 | 33.61 | 3.60 | – | – | 1.27 |
| EVLA Band Ka (DnC) | 91,330,642 | 1.76$\times$1.39 | 44 | – | – | 21.80 | 59.07 | 141.84 | 40.53 | 4.91 | – | – | 1.54 |
| VLA Band K (B) | 127,245,834 | 0.47$\times$0.26 | 7.9 | – | – | – | – | 135.60 | – | – | – | – | – |
| VLA Band Ku (B) | 200,665,639 | 0.67$\times$0.40 | 12 | – | – | 30.67 | 71.92 | 181.58 | 50.21 | – | – | – | – |
| EVLA Band X (A) | 299,773,911 | 0.46$\times$0.19 | 5.3 | – | – | – | 98.03 | 264.56 | 81.33 | – | – | – | – |
| VLA Band C (A) | 616,844,217 | 0.69$\times$0.39 | 8.9 | – | – | 41.34 | 104.45 | 318.02 | 70.16 | 9.08 | – | – | – |
| VLA Band L (A) | 2,012,164,964 | 2.13$\times$1.25 | 36 | 6.57 | 12.38 | 89.09 | 175.32 | 274.92 | 160.83 | 36.35 | 16.68 | 15.20 | 5.69 |

Table notes: The fifth to last columns display the extracted fluxes \[mJy\] for each sampled Giant Molecular Cloud (GMC) within a 3$\ensuremath{''}$ aperture diameter. A dash – indicates the lack of (enough) data filling the aperture. Uncertainties were assumed to be of the order of 10% for all the sample except for ALMA data, where we assume 15%. Additionally, observational parameters, namely, wavelength, FWHM of the beam/psf, and largest angular scales in the case of interferometric observations are indicated in columns 2, 3, and 4, respectively, while the first column specifies the source (facility or survey) and filter, plus the array configuration mode provided parenthetically for the (E)VLA observations. The largest angular scale, $\theta_{\rm{LAS}}$, is pertinent for interferometric observations only, namely: ALMA (cite: Martin2021), EVLA[^2], and VLA[^3].

## Spitzer/IRAC

We retrieved Spitzer/IRAC mosaic images from the Spitzer Heritage Archive[^4]. The mean FWHM of the point spread function (PSF) of the four IRAC bands at 3.6, 4.5, 5.8, and 8.0 $\mathrm{\mu m}$ are 1.66$''$, 1.72$''$, 1.88$''$, and 1.98$''$, respectively (cite: Fazio2004). Thanks to the large field of view (FoV) of Spitzer, which covers the entire emission from NGC 253, we were able to use data from these four IRAC filter images in all our GMCs.

## ALMA

ALMA observations of NGC 253 were conducted during Cycles 5 and 6 as part of the ALCHEMI large program. The observations consisted of an unbiased complete spectral scan across the ALMA bands 3 to 7 (84–373 GHz, $\lambda$=3.6–0.8 mm) across the whole CMZ region (inner 500 pc; (cite: Sakamoto2006)) of the galaxy. The observations were carried out using both 12m and 7m antenna arrays aiming to retrieve extended emission, and the data were imaged to common angular and spectral resolutions of 1.6$''$ and $\sim$8–9 km s$^{-1}$, respectively. The flux density RMS noise ranges from 0.18 to 5.0 mJy beam$^{-1}$ in the 8–9 km s$^{-1}$ channels. In Fig. [2](#Fig.Cont_maps_ALCHEMI) we provide integrated intensity maps of the continuum emission (in mJy) of the CMZ of NGC 253 at ALMA Bands 3, 4, 6, and 7 (100, 144, 243, and 324 GHz, respectively).

The absolute flux density uncertainty was reported to be of order 10 to 15%. We conservatively assume an uncertainty of 15% for our extracted ALCHEMI fluxes. However, the relative flux uncertainty within the individual ALCHEMI observations is $2-3\%$ after the alignment performed on the data enabled by the continuous frequency coverage. A full description of the dataset, calibration, and imaging is provided by (cite: Martin2021).

## EVLA

We obtained Expanded Karl G. Jansky Very Large Array (EVLA) archival data in two different ways. One was by directly searching into the VLA archive. In this way, we obtained the reduced NGC 253’s CMZ image in the X Band at 3 cm (PI: N. Harada), which has been observed in A configuration mode, leading to a largest angular scale (LAS) of 5.3$''$ according to the EVLA documentation[^5]. We applied a cleaning to this data using `tclean` with a standard gridder and a hogbom deconvolver inside the Common Astronomy Software Applications (CASA) package[^6]. Additionally, we used a 1 cm (33 GHz; Ka-Band) continuum image presented in (cite: Kepley2011). These observations were done at DnC hybrid configuration, which leads to a LAS of 44$\ensuremath{''}$[^7]. We used CASA `imsmooth` to convolve the X Band EVLA continuum image to a common circular beam of 1.6$''$, matching that of ALCHEMI. In the same way, for the Ka-Band (26.5–40.0 GHz) image, we choose a slightly larger (1.8$''$) beam due to an original beam of 1.76$''$$\times$1.38$''$. Since the images are in Jy/beam, we converted them into Janskys by dividing their flux by the beam area in pixels \[pix/beam\] available in the CASA Viewer (Statistics/BeamArea) panel. We note that the LAS, $\theta_{\rm{LAS}}$ (see Table [\[Tab.observations\]](#Tab.observations)), is smaller than the aperture size for the Ka-Band observations. However, we did not see significant deviations of these observations with respect to the rest of the dataset. In fact, the model adjusts well to the observations when they are available (GMCs 3–7), and any expected departure or uncertainty in flux is compensated for by the added uncertainties in our SED models, which is up to 30% for the case of GalaPy (cite: Ronconi2024).

## VLA

We retrieve Karl G. Jansky Very Large Array (VLA) continuum maps processed with the AIPS VLA pipeline by Lorant Sjouwerman (NRAO) from the webpage[^8]. Of those, VLA Band L (VLA A conf.) is the only one where all the 10 GMCs studied in this work are detectable. Details about wavelengths, fluxes per GMC, array configurations, and FWHMs, are summarized in Table [\[tab.phot_points\]](#tab.phot_points). We find very good consistency between VLA and EVLA points, delivering similar fluxes within 1 or 2$\sigma$ of the SED fitting. There is a noticeable missing flux in L-band for GMC 5 (see Fig. [3](#fig.SEDs)), which can be associated to the free-free absorption effect (cite: Kellermann1969) observed in compact IR-bright starbursts (cite: Condon91; Clemens10; Dey2022).

Since we are considering flux densities, we decided not to convolve our VLA continuum maps, as we noticed that it can produce artifacts that may show up in GMC positions without clear emission, leading to false positives. Upon examining the summed fluxes within 3$\ensuremath{''}$ diameter apertures before and after convolution with CASA `imsmooth`, we observed differences of less than 10% (i.e., less than the instrumental uncertainties).

## GMC positions

The selection of GMC positions to be analyzed in this study is driven by the ALMA data from the ALCHEMI project. Thus, we use the GMC positions determined by (cite: Harada2024), which incorporate both the continuum and molecular emission peaks, except for GMC 3, GMC 4, and GMC 10. For these three clouds, and given the similarity between the dataset used in (cite: Leroy2015) and the ALCHEMI data, A. K. Leroy (private communication) provided modified GMC coordinates tailored to the ALCHEMI data for the collaboration, which were retained for GMCs 3, 4, and 10. These three GMC positions were derived using CPROPS (cite: Rosolowsky2006) considering intensity peaks of the CS $J = 2{-}1$ and H$^{13}$CN $J = 1{-}0$ transitions.

Our region coordinates are close to those used by (cite: Leroy2015), whose reference coordinates are clarified in (cite: Behrens2022ApJ), their Appendix A. The differences between their coordinates and the ones we used in this study, listed in Table [1](#tab.positions), are up to $\sim$1.3$''$ in right ascension and $\sim$1.4$''$ in declination, corresponding to spatial offsets of up to 23 pc and 24 pc, respectively, at the assumed distance of NGC 253 of 3.5 Mpc. These variations fall within our photometric aperture radius of 25 pc.

The general reason for this selection is to avoid, as much as possible, overlapping between our apertures of 3$\ensuremath{''}$, while at the same time extracting most of the intensity in each aperture. We note that the variation in the GMC positions from different source extraction criteria is relatively marginal ($\sim$0.2$''$) compared to the apertures used in this paper.

Along the course of this work, we will compare our GMC characteristics with those of the GMCs in previous ALCHEMI works with the same numbering, unless it is explicitly mentioned.

# Analysis: SED and spectroscopic modeling

The main results from this study come from two methods used to explore in detail the spectroscopic and photometric information of the CMZ of NGC 253. We have employed GalaPy for the photometry information, from near-UV to centimeter wavelengths. To cross-validate the results obtained from GalaPy, we compared them with those from the broadly used Code Investigating GALaxy Emission (CIGALE). While CIGALE provides a refined treatment from the UV to the sub-mm regimes, it models the radio centimeter luminosities from star formation using the FIR/radio correlation coefficient (q$_{\rm IR}$) scaling relations. In contrast, GalaPy incorporates a full model based on the theoretical Simple Stellar Population (SSP) approach of (cite: Bressan02). It self-consistently incorporates nebular and synchrotron emission within the chosen star formation history (SFH) model. This makes GalaPy a powerful tool for gaining deeper insights into the link between radio emission and stellar populations. Given that our study relies on extensive radio data, we selected GalaPy as the primary tool for SED modeling, particularly for testing the radio-SF correlation.

As we will see in Section [4.1](#sec.SED_fitting), despite differences between the SED modeling codes (e.g., in our Fig. [3](#fig.SEDs)), we confirm the nature of GMCs and much of their main physical properties, for example, the star formation rate and the stellar mass in the studied GMCs is higher toward the inner regions of the CMZ, independently of the code used. Nevertheless, we have found certain differences among the codes’ results, which reflects the range of possibilities one can obtain when depending on the used SFH model, mass-luminosity relation, and IMF, among other assumptions.

Additionally, to complement this study, we applied STARLIGHT for the spectral MUSE data plus photometric (S-PLUS) information in the near-UV to near-IR range. Below, we elaborate on our procedures. In Fig. [3](#fig.SEDs) we provide our best-fit models to the extracted flux densities summarized in Table [\[Tab.observations\]](#Tab.observations). This Figure primarily shows GalaPy results but also presents the CIGALE best-fit models (solid blue lines). CIGALE best-fitting results are further provided in detail (i.e., with all the considered components) in Fig. [15](#apen.fig:cigalefitting).

## GalaPy photometric SED fitting

We perform the SED fitting of our selected GMCs with GalaPy (cite: Ronconi2024), an open-source application programming interface developed in Python/C$++$ across a range from X-ray to radio frequencies. GalaPy assumes a Chabrier initial mass function (cite: Chabrier2003) and a flat $\Lambda$CDM cosmology with approximate parameters: matter density around 0.3, baryonic density around 0.05, and a Hubble constant $H_{0}=$100 $h$ km s$^{-1}$ Mpc$^{-1}$, where $h$ is roughly 0.7 (cite: Planck2020). GalaPy is expected to include tools for optical spectroscopy and an AGN component on top of its SED fitting algorithm, although these modules were not available at the time this work was initiated. In the subsequent subsections, we detail the relevant configurations pertinent to the objectives of this study.

### The In-Situ model

GalaPy allows the user to choose among a range of SFH models, both empirical and non-parametric. For our models, we use the default In-Situ SFH model, which has proven successful in predicting the emission from both late and early type galaxies in the local Universe as well as for young highly star-forming systems up to high redshift (cite: Pantoni2019; Giulietti2023; Ronconi2024; Gentile2024). The physically motivated In-Situ model, developed by (cite: Lapi2018), adopts a star formation rate ($\psi(t)$) of: $$\begin{equation}
    \psi(t) \propto e^{-x}-e^{-s\gamma x},
\end{equation}$$ with $x \equiv \tau/s\tau_{\star}$, where $\tau$ is the galactic age, $\tau_{\star}$ is the characteristic star-formation timescale, $s \approx 3$ is related to the gas condensation, and $\gamma$ is related to the gas dilution, recycling, and stellar feedback (cite: Lapi2020).

In the in situ model, the evolution of the gas and dust masses and of the gas and stellar metallicities can be followed analytically as a function of the galactic age, and self-consistently with respect to the evolution of the SFR. This means that an isolated system is assumed for each molecular cloud (MC), implying an interdependence among parameters. For example, a correspondence between metallicities and ages. This approach guarantees that the derived physical properties that directly result from the evolution of the stellar population (e.g. the components’ masses and metallicities), are consistently propagated to the other models contributing to the overall emission of the object.

### Simple stellar populations

Among the available Simple Stellar Population (SSP) libraries in GalaPy, we have selected the “refined” version of $parsec22.NTL$ (cite: Bressan2012; Yan2019; Ronconi2024) as our preferred choice. This library ensures a dense wavelength grid with a minimum of 128 values per order of magnitude within its 2189-point grid. It incorporates emission from dusty Asymptotic Giant Branch (AGB) stars and accounts for nebular emission and free-free continuum in addition to the stellar continuum and non-thermal synchrotron radiation from core-collapse supernovae.

For the purposes of our study, the $parsec22.NTL$ SSP library was modified to correctly process the photometric points obtained from the narrow bands of the VLT/VISIR instrument (see Sect. [2.2](#sec.obser_VLT)). This adjustment will be available in the next release of GalaPy.

### Dust model

GalaPy implements an age-dependent two component dust model which is constructed in order not to assume an attenuation curve but to derive it instead from structural parameters (e.g. density and extension) which can be obtained by tuning the model to best represent an observed dataset.

The two different components comprise the contribution of (1) a hot molecular cloud phase (normally referred in the literature as a “birth-molecular cloud”; see, e.g., (cite: CharlotFall2000)) of new stellar populations and (2) a diffuse and extended dusty medium which further attenuates the stellar emission. Both components also contribute to the IR emission which is then the combination of two separate modified grey-bodies.

Among the several possible free parameters on which this dust model depends, we chose to fix some known values and ranges, in order to both ensure physically plausible results and speed up the computing process. This consists in setting a range of reliable physical terms, such as the total number of molecular clouds to $N_\text{MC} = 1$, as in this work we are assuming isolated GMCs, and their dusty and molecular radii, which were set to be within a 10–100 pc range, although they will likely be closer to the lower limit considering the 30 pc diameter inferred from their sub-mm emission (cite: Leroy2015). A list of all common parameter ranges and individual values used to model the SEDs in the ten GMCs is provided in Table [2](#tab.gmcs_GalaPy_constant_parameters). There, the redshift was taken from the SIMBAD Astronomical Database (cite: Wenger2000). These ranges are fixed for all GMCs. On the other hand, the parameters that were fine-tuned for specific GMCs along with their corresponding adjusted ranges are presented in Table [\[tab.gmcs_variable_parameters\]](#tab.gmcs_variable_parameters). The parameters listed in this second table vary across different GMCs, with their respective ranges for each GMC. For example, the range of the molecular cloud radius, R$_{\rm{CM}}$ (pc), was fine-tuned and is set between 0.0 and 1.7 for GMCs 2 and 8, while for the other GMCs, this radius remains between 0.0 and 2.0 (in log10 scale).

We use different initial conditions for unknown parameter ranges such as the GMC ages (age), the time of maximum star-formation (sfh.tau_star), the time that stars need to escape from its parental molecular cloud (ism.tau_esc), the maximum SFR (sfh.psi_max), and the average radius of the molecular cloud (ism.R_MC). We mainly modified the R_MC, ism.R_MC, and sfh.psi_max in cases where the results were bimodal, in order to achieve a single result in the parameter space distribution. For example, the R_MC was fixed to not exceed 50 pc in GMCs 2 and 8, motivated by Table 3 in (cite: Leroy2015), where their molecular radii are expected to be around 52 and 44 pc, respectively. Interestingly, these two GMCs are the largest in the sample, according to the mentioned study.

We recommend the reader consult Table B.3 in (cite: Ronconi2024) for a complete description of all GalaPy parameters. This table is also described on the project’s $Read the Docs$ web page[^9]. The information there goes beyond what is covered in the present work, which is limited to the In-Situ model.

| Parameter       | Value/Range          | Brief description                     |
|:----------------|:---------------------|:--------------------------------------|
| redshift        | 0.000864             |                                       |
| sfh.tau_quench  | 1e+20                | Star formation quenching (yrs.)       |
| ism.f_MC        | (\[0.0, 1.0\], lin)  | MCs’ fraction into the ISM            |
| ism.norm_MC     | 100.0                | MCs’ normalization factor             |
| ism.N_MC        | 1.0                  | number of MCs                         |
| ism.dMClow      | 1.3                  | Extinction index $<$100$\mu$          |
| ism.dMCupp      | 1.6                  | Extinction index $\gtrsim$100$\mu$    |
| ism.norm_DD     | 1.0                  | Diffuse dust norm. factor             |
| ism.Rdust       | (\[0.0, 2.0\], log)  | Radius of the diffuse dust (DD, pc)   |
| ism.f_PAH       | (\[0.0, 1.0\], lin)  | DD fraction radiated by PAH           |
| ism.dDDlow      | 0.7                  | DD extinction index $<$100$\mu$       |
| ism.dDDupp      | 2.0                  | DD extinction index $\gtrsim$100$\mu$ |
| syn.alpha_syn   | 0.75                 | Spectral index                        |
| syn.nu_self_syn | 0.2                  | Self-absorption frequency (GHz)       |
| f_cal           | (\[-5.0, 0.0\], log) | Calibration uncertainty               |

: GalaPy common inputs.

Table notes: Parameter values or ranges common to the ten GMCs studied in this work provided as inputs to GalaPy. The terms “log” and “lin” next to the ranges indicate logarithmic (log10) and linear values, respectively. For a detailed explanation, see Sect. [3.1](#sec.GalaPy_model).

| Parameter | GMC(s) with varied parameters | Common parameter ranges | Brief description |
|:---|:---|:---|:---|
| age | GMC2: (\[6.0, 12.0\]) | (\[6.0, 11.0\]) | Age of the MC |
| sfh.tau_star | GMC2: (\[6.0, 12.0\]) | (\[6.0, 11.0\]) | Characteristic timescale |
| ism.R_MC | GMC2: (\[0.0, 1.7\]), GMC8: (\[0.0, 1.7\]) | (\[0.0, 2.0\]) | Average radius of a MC |
| ism.tau_esc | GMC2: (\[6.0, 12.0\]) | (\[6, 11.0\]) | Stars’ escape time from MC |
| sfh.psi_max | GMC3: (\[-2.0, 1.5\]), GMC5: (\[-2.0, 1.5\]) | (\[-3.0, 1.5\]) | Maximum SFR, at sfh.tau_star |

Table notes: Parameter ranges set to GalaPy that vary depending on the modeled GMC. All values are given in log10 scale. For a detailed explanation, see Sect. [3.1](#sec.GalaPy_model).

![](Figures/SEDs_bigger_plus_CIGALE.pdf)

## CIGALE photometric SED fitting

In addition to the main results obtained from GalaPy, for comparison we also provide simultaneous UV-to-radio SED modeling with the CIGALE 2022.1 version (cite: Yang22). This software operates on the principle of energy balance, where energy attenuation in the UV-to-optical range is re-emitted in the infrared in a self-consistent manner. Its modular and parallelized design, along with its user-friendly interface, has made it a popular choice in the literature for estimating the astrophysical characteristics of various targets. Below, we provide a brief overview of the models employed to simulate the galaxy emission.

To construct the SEDs with CIGALE, we utilized the full photometric coverage available for our GMCs. The modeling was based on the widely-used (cite: Bruzual2003) SSPs, adopting the IMF of (cite: Chabrier2003) and assuming a solar-like metallicity. The stellar populations evolved using a delayed SFH, a model in which the star formation rate initially rises, peaks after a delay, and then declines exponentially, with an additional burst component (cite: ciesla2015). This SFH approach is more realistic compared to the simple delayed model and has been demonstrated to minimize biases in the estimation of SFR and stellar mass (cite: Schreiber2018). Additionally, the inclusion of the burst is consistent with the ALMA detections (cite: Hamed2021; hamed2023a). For the SFH parameters, we maintained flexibility in the age and the e-folding time of the main stellar population to avoid introducing artificial biases in the efficiency of the initial burst.

Dust attenuation was modeled following the (cite: Calzetti2000) attenuation law, allowing the color excess of the young stellar population to vary as a free parameter. Dust emission was a critical component of our SED modeling, given the extensive IR coverage, particularly from ALMA. We used the models provided by (cite: Draine2014). To ensure a good fit, we explored the parameter space for PAH fractions and the radiation field, U$_{\rm{min}}$, aiming to minimize $\chi^2$ while keeping the models physically realistic. Considering the rich radio data available for the GMCs, we extended our UV-IR modeling to the radio regime taking into account the power-law nature of the synchrotron spectrum and the ratio of the FIR/radio (q$_{\rm IR}$) correlation in the CIGALE fitting.

CIGALE minimizes $\chi^2$ by measuring the difference between observed data and the model predictions, weighted by the uncertainties in the observations. The goal of minimization is to find the best-fitting model parameters that reduce this difference (cite: Boquien19). Additional details, including the addition of AGN-related parameters, are provided in Appendix [\[apen.CIGALE_results\]](#apen.CIGALE_results).

## Stellar population fitting with STARLIGHT

GalaPy and CIGALE are used in the full SED fits (all wavelengths from UV to Radio), while STARLIGHT will be used for the optical data only to fit stellar population models. STARLIGHT has been successfully applied to fit the stellar component of a diverse range of galaxy types, such as low-luminosity AGN, Seyfert nuclei, and normal galaxies (cite: CidFernandes2005; CidFernandes2013; Krabbe2017).

While traditionally used for optical spectra, we applied the latest version of the code, described by (cite: Werle2019), to fit simultaneously the combined MUSE and S-PLUS data, thus covering the 3,500–10,000 Å range. The combination of these datasets provides a comprehensive view of the galaxy’s stellar populations, spanning a wide range of wavelengths. In particular, the S-PLUS bands densely cover the highly informative region around the 4,000 Å break which falls outside the range of MUSE spectra that start at 4,600Å.

STARLIGHT uses a chi-squared minimization technique to find the best-fit non-parametric combination of stellar populations of different ages and metallicities from a pre-defined library. This analysis allows us to estimate properties, such as mean age, metallicity, and extinction, as well as the velocity dispersion of the stellar component. The base is built from SSP models from the Charlot & Bruzual 2019 library models (cite: paredes2023) using PARSEC (*PA*dova T *R*ieste *S*tellar *E*volution *C*ode) evolutionary tracks (cite: Bressan2012; ChenBressan2015) and a Chabrier IMF. A base of composite stellar population is built from the SSP models assuming constant SFRs in 16 logarithmically spaced age bins with 5 different metallicities. Extinction is modeled with two components: one applied to all populations ($A_{\rm{V}}$) and an extra one applied exclusively to $\leq 10$ Myr old stars ($\delta A_{V}$).

The list of parameters to fit includes the flux (or mass) fractions of the different populations, global and selective extinction, the velocity shift and velocity dispersion.

We have adjusted the weight scheme for the code used to extract residuals for H$\alpha$, \[N II\], \[O III\], and H$\beta$ by augmenting them around those lines. This modification allows a detailed examination on the contribution of stellar absorption features to these emission lines, compared to a general fit to the MUSE+S-PLUS spectra/photometry. These lines will subsequently serve as input for diagnostic diagrams and to estimate the extinction affecting the emission line regions.

# Results

In the following, we supplement our SED analysis with existing results from the literature, including those obtained by the ALCHEMI collaboration. Since the GMC selection was based on ALMA observations, our primary sources of information are the ALCHEMI results (cite: Martin2021). After detailing the characteristics of the ten GMCs by dividing them in two main groups, we will compare our panchromatic results – derived from SED fitting – on star formation rates (SFRs) and histories (SFHs) with those obtained from pure-optical and pure-sub-mm/cm observations, that is, from monochromatic tracers such as the H$\alpha$ and H40$\alpha$ emission lines and different infrared and radio continuum regimes or bands. This approach will help us understand the key limitations to consider when working with mono-wavelength datasets. For a more detailed description of our results in light of previous literature information and for each of the ten GMCs, we refer the reader to our Appendix [8](#apen.individual_GMCs).

## SED fitting

The wealth of archival data described in Sect. [2](#sec.observations) does not always cover the ten GMCs. Only S-PLUS, Spitzer/IRAC, ALCHEMI, VLA L (1.5 GHz), and Ku (15 GHz) Bands fully cover the NGC 253’s CMZ (see Table [\[tab.phot_points\]](#tab.phot_points)). EVLA Band X does not detect emission outside GMCs 3 to 6, similar to the case in VLA K (23.6 GHz) band observation, which also detects emission only in GMCs 3 to 6. Also, the VLA C (4.9 GHz) band does not detect emission in GMCs 1 and 2, and our aperture of 3$''$ is not fully covered by emission in GMCs 8–10, hence we discarded the latter contribution. From the above, we can say that the best-studied GMCs are GMCs 3 to 6, corresponding to the core of NGC 253 and encapsulating most of the star formation activity across the central starburst region (cite: Bendo2015). It is worth saying that, in addition to the possible lack of continuum emission, the not imaged/detected GMCs may fall below the detection limit of our ALMA Band 3 observations and the different centimeter bands mentioned above. The detection limit at 3 $\sigma$ of EVLA Band X, and VLA Bands K and C are 2.4$\times$10$^{-2}$, 5.4$\times$10$^{-3}$, and 6.6$\times$10$^{-4}$ Jy, respectively.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|---:|
| GMC | SFR | $M_{\bigstar}$ | $\tau_{\bigstar}$ | $Z_{\bigstar}$ | $L_{\rm{bol}}$ | Age |  |  |  |  |  |  |  |  |
|  | \[$\times 10^{-4} M_{\odot}$ yr$^{-1}$\] | \[log$_{10}$ ($M_{\odot}$)\] | \[log$_{10}$ (yrs)\] | \[$\times$10$^{-3}$\] | \[log$_{10}$ ($L_{\odot}$)\] | \[log$_{10}$ (yrs)\] |  |  |  |  |  |  |  |  |
| 1 | 50$_{-10}^{+10}$ | 6.535$_{-0.097}^{+0.159}$ | 10.88$_{-0.21}^{+0.08}$ | 0.35$_{-0.08}^{+0.18}$ | 8.065$_{-0.073}^{+0.052}$ | 9.30$_{-0.13}^{+0.15}$ |  |  |  |  |  |  |  |  |
| 2 | 80$_{-10}^{+10}$ | 7.534$_{-0.086}^{+0.106}$ | 9.21$_{-0.14}^{+0.14}$ | 3.88$_{-0.15}^{+0.19}$ | 8.391$_{-0.062}^{+-0.002}$ | 9.66$_{-0.12}^{+0.13}$ |  |  |  |  |  |  |  |  |
| 3 | 870$_{-90}^{+110}$ | 8.573$_{-0.100}^{+0.108}$ | 9.07$_{-0.46}^{+0.28}$ | 7.88$_{-0.94}^{+2.27}$ | 9.354$_{-0.042}^{+0.071}$ | 9.62$_{-0.23}^{+0.15}$ |  |  |  |  |  |  |  |  |
| 4 | 2740$_{-280}^{+390}$ | 8.850$_{-0.136}^{+0.251}$ | 7.48$_{-0.10}^{+0.13}$ | 20.84$_{-1.47}^{+2.31}$ | 10.132$_{-0.114}^{+0.050}$ | 8.54$_{-0.08}^{+0.16}$ |  |  |  |  |  |  |  |  |
| 5 | 6450$_{-590}^{+600}$ | 8.620$_{-0.105}^{+0.124}$ | 7.57$_{-0.11}^{+0.12}$ | 17.59$_{-1.14}^{+1.17}$ | 10.184$_{-0.065}^{+0.016}$ | 8.40$_{-0.03}^{+0.13}$ |  |  |  |  |  |  |  |  |
| 6 | 1870$_{-170}^{+180}$ | 8.605$_{-0.095}^{+0.072}$ | 8.17$_{-0.12}^{+0.10}$ | 12.87$_{-0.63}^{+0.82}$ | 9.602$_{-0.045}^{+0.061}$ | 8.56$_{-0.04}^{+0.06}$ |  |  |  |  |  |  |  |  |
| 7 | 220$_{-20}^{+30}$ | 8.156$_{-0.087}^{+0.096}$ | 8.50$_{-0.18}^{+0.31}$ | 8.12$_{-1.18}^{+0.87}$ | 8.903$_{-0.080}^{+0.041}$ | 9.39$_{-0.14}^{+0.23}$ |  |  |  |  |  |  |  |  |
| 8 | 110$_{-10}^{+10}$ | 7.837$_{-0.127}^{+0.098}$ | 9.24$_{-0.24}^{+0.24}$ | 4.45$_{-0.40}^{+0.71}$ | 8.533$_{-0.048}^{+0.045}$ | 9.76$_{-0.16}^{+0.15}$ |  |  |  |  |  |  |  |  |
| 9 | 90$_{-10}^{+10}$ | 7.752$_{-0.099}^{+0.106}$ | 9.12$_{-0.18}^{+0.24}$ | 4.53$_{-0.53}^{+0.62}$ | 8.605$_{-0.212}^{+0.102}$ | 9.73$_{-0.10}^{+0.12}$ |  |  |  |  |  |  |  |  |
| 10 | 50$_{-10}^{+10}$ | 7.581$_{-0.150}^{+0.095}$ | 9.55$_{-0.25}^{+0.21}$ | 3.31$_{-0.32}^{+0.37}$ | 8.507$_{-0.090}^{+0.075}$ | 9.64$_{-0.12}^{+0.12}$ |  |  |  |  |  |  |  |  |

Table notes: From left to right, the columns correspond to the GMC number, the instantaneous star formation rate (SFR), the stellar mass ($M_{\bigstar}$), the characteristic star formation timescale ($\tau_{\bigstar}$), the stellar metallicity ($Z_{\bigstar}$), the bolometric luminosity ($L_{\rm{bol}}$), and the stellar age; all including 1$\sigma$ uncertainties. A complete list of results is provided in Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy).

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| GMC | SFR$_{\rm{INST}}$ | SFR$_{\rm{100Myr}}$ | SFR$_{\rm{10Myr}}$ | $M_{\bigstar}$ | $\tau_{\rm{burst}}$ | $M_{\bigstar, \text{old}}$ | $M_{\bigstar, \text{young}}$ | Age |  |  |  |  |  |  |  |
|  | \[$\times 10^{-4} \, M_{\odot} \, \text{yr}^{-1}$\] | \[$\times 10^{-4} \, M_{\odot} \, \text{yr}^{-1}$\] | \[$\times 10^{-4} \, M_{\odot} \, \text{yr}^{-1}$\] | \[log$_{10}$($M_{\odot}$)\] | \[log$_{10}$(yrs)\] | \[log$_{10}$($M_{\odot}$)\] | \[log$_{10}$($M_{\odot}$)\] | \[log$_{10}$(yrs)\] |  |  |  |  |  |  |  |
| 1 | 20.76$\pm$3.81 | 23.27$\pm$4.43 | 20.95$\pm$3.82 | 6.70$\pm$0.07 | 8.15$\pm$0.33 | 6.70$\pm$0.04 | 7.87$\pm$0.09 | 9.41$\pm$0.57 |  |  |  |  |  |  |  |
| 2 | 31.02$\pm$4.81 | 26.37$\pm$7.53 | 31.80$\pm$4.82 | 7.17$\pm$0.06 | 8.32$\pm$0.31 | 7.17$\pm$0.04 | 8.10$\pm$0.09 | 9.52$\pm$0.93 |  |  |  |  |  |  |  |
| 3 | 262.01$\pm$73.46 | 292.05$\pm$60.68 | 264.88$\pm$75.60 | 7.82$\pm$0.07 | 8.10$\pm$0.33 | 7.82$\pm$0.04 | 7.74$\pm$0.09 | 9.36$\pm$0.55 |  |  |  |  |  |  |  |
| 4 | 642.50$\pm$71.84 | 446.83$\pm$66.94 | 655.24$\pm$73.26 | 8.50$\pm$0.02 | 8.39$\pm$0.33 | 8.50$\pm$0.01 | 8.16$\pm$0.09 | 9.54$\pm$1.03 |  |  |  |  |  |  |  |
| 5 | 1956.59$\pm$262.37 | 204.02$\pm$24.33 | 2024.70$\pm$239.81 | 8.17$\pm$0.02 | 8.26$\pm$0.33 | 8.17$\pm$0.01 | 7.92$\pm$0.09 | 9.44$\pm$0.83 |  |  |  |  |  |  |  |
| 6 | 476.20$\pm$68.99 | 509.41$\pm$79.90 | 481.12$\pm$70.22 | 7.94$\pm$0.06 | 8.23$\pm$0.33 | 7.94$\pm$0.04 | 7.93$\pm$0.09 | 9.44$\pm$1.04 |  |  |  |  |  |  |  |
| 7 | 191.88$\pm$38.04 | 214.98$\pm$40.54 | 193.54$\pm$37.91 | 7.68$\pm$0.06 | 8.03$\pm$0.33 | 7.68$\pm$0.04 | 7.68$\pm$0.09 | 9.33$\pm$0.52 |  |  |  |  |  |  |  |
| 8 | 47.72$\pm$12.44 | 46.49$\pm$10.59 | 49.32$\pm$12.65 | 7.51$\pm$0.07 | 8.02$\pm$0.33 | 7.51$\pm$0.04 | 7.75$\pm$0.09 | 9.36$\pm$0.64 |  |  |  |  |  |  |  |
| 9 | 35.29$\pm$6.93 | 41.35$\pm$8.98 | 35.72$\pm$6.92 | 7.18$\pm$0.06 | 8.15$\pm$0.31 | 7.18$\pm$0.04 | 7.71$\pm$0.09 | 9.35$\pm$0.64 |  |  |  |  |  |  |  |
| 10 | 32.41$\pm$5.98 | 38.11$\pm$9.19 | 32.98$\pm$6.07 | 7.17$\pm$0.07 | 8.22$\pm$0.33 | 7.17$\pm$0.04 | 7.82$\pm$0.09 | 9.40$\pm$0.58 |  |  |  |  |  |  |  |

Table notes: From left to right, the columns correspond to the GMC number, the instantaneous star formation rate (SFR), the integrated SFR over the last 100 Myr, the SFR over the last 10 Myr, the stellar mass ($M_{\bigstar}$), the age of the last stellar burst ($\tau_{\rm{burst}}$), the old stellar population mass ($M_{\bigstar, \text{old}}$), the young stellar population mass ($M_{\bigstar, \text{young}}$), and the stellar age; all including 1$\sigma$ uncertainties. Additional results are listed in Tables [\[Apen.Tab.Extinction_Factors_CIGALE\]](#Apen.Tab.Extinction_Factors_CIGALE), [\[Apen.Tab.Modified_Parameters_CIGALE\]](#Apen.Tab.Modified_Parameters_CIGALE), and [\[Apen.Tab.CIGALE_AGN\]](#Apen.Tab.CIGALE_AGN).

In general, the GMC’s SED shapes, which can be seen in Fig. [3](#fig.SEDs), are similar to what is found in local and high-redshift starbursts (cite: Swinbank2010). These SEDs exhibit significant absorption in the near-UV and optical wavelength regimes ($\sim 3\times10^{3}$–$10^{4}$ ), caused by an exceptionally large amount of dust. This leads to a substantial difference between the predicted and observed emissions (i.e., stellar emission with and without extinction), illustrated by the red and green lines in Fig. [3](#fig.SEDs). At the mentioned wavelengths, the flux difference can reach up to four orders of magnitude (e.g., from $\sim10^{3}$ mJy down to $\sim10^{-1}$ mJy in GMCs 4–6 at 10$^{4}$ $\AA$). The total extinction ($A_{\rm{v}}$) derived from the stellar component exceeds 5.0 magnitudes in GMCs 3–6, based on analyses from GalaPy, CIGALE, and the Balmer lines (H$\alpha$ and H$\beta$; see Sect. [4.2.2](#subsec.attenuations)).

Tables [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy) and [\[Tab.CIGALE_main_results\]](#Tab.CIGALE_main_results) respectively contain GalaPy and CIGALE results related to star-formation processes, such as the SFR, the stellar mass ($M_{\bigstar}$), the characteristic timescale ($\tau_{\bigstar}$), or the stellar age (Age). In addition, results on the gas and dust characteristics, the attenuation, the radiation field (U$_{\rm min}$), the time for stars to escape from their parental MC (ism.tau_esc), and uncertainties of the model, to mention a few, are given in Tables [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy) and [\[Apen.Tab.Modified_Parameters_CIGALE\]](#Apen.Tab.Modified_Parameters_CIGALE) for GalaPy and CIGALE, respectively.

We summarize below the main characteristics of the molecular clouds studied here by dividing them into two groups: the central GMCs, numbered from 3 to 6, and the external ones, GMCs 1, 2, and 7–10. We find strong differences among them in terms of stellar and dust masses, and star formation rates. Appendix [8](#apen.individual_GMCs) provides detailed information of individual GMCs.

### GMC characteristics

The Central Molecular Zone (CMZ) of NGC 253 can mainly be divided into two primary groups based on the physical and chemical properties found in their giant molecular clouds (GMCs): internal and external GMCs. The internal GMCs, corresponding to GMCs 3, 4, 5, and 6, are located in the very nuclear region of the CMZ, about 120 pc extension (see, e.g., the scale bar in Fig. [11](#Fig.SFR_H40a)), and are characterized by a large occurrence of molecular tracers indicating high densities ($n_{\rm{gas}}>$10$^{7}$ cm$^{-3}$), elevated temperatures ($T_{\rm{kin}}>$100 K), and strong/fast shocks ($v_{\rm{shock}}\gtrsim$15-20 km s$^{-1}$) likely triggered by a tremendous star formation activity (cite: Meier2015; Bouvier2024; Bao2024).

Conversely, the external GMCs encompass GMCs 1, 2, 7, 8, 9, and 10, located near (GMC 7) or fully immersed in the periphery of the internal bar. We note that, unlike some ALCHEMI studies (cite: Huang2023) but in line with others (cite: Harada2024), based on the findings of the current study –namely, the star formation rate (SFR), dust ($M_{\rm{dust}}$), and stellar ($M_{\bigstar}$) mass– GMC 7 is better defined as an external region (see the text below and also Fig. [4](#Fig.Mstar_vs_Mdust)). Due to their locations, these external GMCs may experience the effect of orbital intersections such as inner Lindblad resonances (cite: Iodice2014), bar/spiral arm interactions –also known as $x_{1}/x_{2}$ interactions (cite: Kim2012)–, and cloud-cloud collisions (cite: Ellingsen2017) take place (see, e.g., ellipses in Fig. [2](#Fig.Cont_maps_ALCHEMI)). These GMCs are dominated by a lower-density molecular gas, as compared to the internal GMCs, and exhibit signatures of slow shocks (up to $\sim$15 km s$^{-1}$) rather than intense stellar feedback. This division reflects significant dynamical and chemical variations across the CMZ, previously noted by ALCHEMI studies (cite: Tanaka2024ApJ; Behrens2024ApJ; Harada2024).

![](Figures/log10_Mstar_vs_Mdust_with_fits_v6_with_contours_fancy.pdf)

The study by (cite: Harada2024) utilized ALMA observations to conduct a detailed survey of molecular lines, applying principal component analysis (PCA) to distinguish patterns of chemical excitation and physical conditions across the CMZ. Their results indicate that the internal GMCs (GMCs 3–6) exhibit strong emissions from dense gas tracers such as HCN and HC$_{3}$N, along with radio recombination lines (RRLs), which are associated with active star formation and high-excitation regions (cite: Bendo2015). In contrast, the external GMCs (GMCs 1, 2, and 7 to 9 in the work of (cite: Harada2024), which did not account for GMC 10) are characterized by tracers of slow shocks, such as CH$_3$OH and an increment of HNCO over SiO (cite: Meier2015; Humire2022), reflecting less energetic dynamical processes. The PCA revealed that molecular emission correlates strongly with dynamical features, with high-excitation species dominating the central regions, while shock tracers are more prevalent in the outskirts.

In the current analysis, the differentiation between internal and external GMCs is further supported by variations in star formation rate (SFR), stellar mass, and dust mass. The internal GMCs exhibit SFRs above 0.087 $M_{\odot}$ yr$^{-1}$, as found by GalaPy, which provides an instantaneous SFR listed in the second column of Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy). They also have greater stellar masses (third column; Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy)) and dust masses ($M_{\rm{dust}}$; Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy)) compared to the external GMCs. This is consistent with the high-density, high-excitation environments described by (cite: Harada2024).

For the sake of clarity, we provide a plot showing the dust mass, $M_{\rm{dust}}$ versus stellar mass $M_{\rm{star}}$ in Fig. [4](#Fig.Mstar_vs_Mdust), from GalaPy. In the latter figure, we label the ranges for these quantities for nuclear and external regions or GMCs. The internal or nuclear GMCs (GMCs 3-6) display stellar masses in the 3.7$^{+1.1}_{-0.7}$–7.1$^{+5.5}_{-1.4}\times$10$^{8}~M_{\odot}$ range, and dust masses in the 1.6$^{+0.7}_{-0.3}$–5.8$^{+3.5}_{-3.0}\times$10$^{5}\,M_{\odot}$ range, in strong contrast to the external GMCs, where the stellar and dust masses range between 0.034$^{+0.01.5}_{-0.00.7}$–1.4$^{+0.4}_{-0.3}\times$10$^{8}~M_{\odot}$ and 2.6$^{+1.6}_{-0.9}$–4.8$^{+1.7}_{-1.2}\times$10$^{4}\,M_{\odot}$, respectively.

The above indicates that the dust mass is the clearest distinction between the two primary groups, while the stellar mass, although enhanced in the internal GMCs, is only a factor of two larger in GMC 6 (internal) with respect to GMC 7 (external).

The external GMCs are also characterized by a lower SFR than the inner ones, with values in the 0.005–0.022 $M_{\odot}$ yr$^{-1}$ range. These findings align with the chemical and dynamical distinctions previously observed in multiple ALCHEMI studies (cite: Tanaka2024ApJ; Behrens2024ApJ; Harada2024), reinforcing the conclusion that the physical properties of the CMZ are tightly coupled with its molecular and dynamical characteristics.

## Optical spectral fitting

We fit archival MUSE data (ID:0102.B-0078(A), PI: Laura Zschaechner) in the 4600–9350Å range with S-PLUS photometric data using STARLIGHT (cite: CidFernandes2005) in its latest version which is capable to fit spectra and photometry simultaneously (cite: LopesFernandez2016; Werle2019).

To correct for the mismatch between spectroscopic and photometric fluxes, we scale MUSE spectra to match the iSDSS band flux of S-PLUS. The S-PLUS bands used for the fits are uJAVA, J0395, J0410 and J0430, iSDSS. The filter F0378 was not used to avoid contamination by \[O II\] 3727 emission. Of these, the blue ones are the most important, because they extend the MUSE coverage to the age sensitive 4,000 Å region.

The STARLIGHT fits to the MUSE spectra and the fitted S-PLUS photometric points for the ten GMCs are shown by the blue lines and the cyan points, respectively, in Fig. [5](#Fig.STARLIGHT_fit). Some important stellar absorption features are labeled in the top panels and indicated by vertical dashed green lines for all the GMCs. The outputs of the fitting are summarized in Table [\[Tab.STARLGIGHT_results\]](#Tab.STARLGIGHT_results).

As is commonly known (cite: Conroy2013), low-mass stars dominate both the total mass and the number of stars in a galaxy, but they contribute only a small fraction to the overall light output, or bolometric luminosity, since young stars outshine older stars. This can be seen in the star formation histories per GMC, which are plotted in Fig. [6](#Fig.SFHs). Independent of the molecular cloud, the light fraction is always shifted towards young stars, while the mass fraction is concentrated in old stars. For example, in GMC 5, nearly 100% of the stellar mass was already formed 10 Gyr ago while $\sim$ 50% of the light comes from stars younger than 30 Myr.

Also in Fig. [6](#Fig.SFHs), for GMC 5, we have over-plotted (in magenta) the normalized skewed Gaussian derived from the age-metallicity relation (AMR; see Appendix [9](#sec.AMR)). This same distribution was adapted to be cumulative (cAMR) and plotted (in yellow). GMCs 3 to 6 also show the estimated ages from super star clusters derived by (cite: Butterworth2024) in vertical dashed blue lines.

![](Figures/MUSE_SL.pdf)

![](Figures/SFHs_plus_AMR_wcffn_bigger.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| GMC | adev | Lum$_{\rm{tot}}$ | $\log M_\bigstar$ | $v_0$ | $\sigma_\bigstar$ | $A_{\rm{V}}$ | $\delta A_{\rm{V}}$ | $x(\delta A_{\rm{V}}>0)$ | $\tilde{A_{\rm{V}}}$ | $\langle \log t_{*} \rangle_L$ | $\langle \log t_{*} \rangle_M$ | $\langle \log Z/Z_{\odot} \rangle_L$ | $\langle \log Z/Z_{\odot} \rangle_M$ |  |
|  | \[%\] | \[$L_{\odot}$\] | \[$M_{\odot}$\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] |  |  | \[%\] |  | \[yr\] | \[yr\] |  |  |  |
| 1 | 1.85 | 9.82 | 4.94 | -2.41 | 107.86 | 2.12 | 3.85 | 0.00 | 2.12 | 8.95 | 9.79 | 0.06 | 0.15 |  |
| 2 | 2 | 234.68 | 5.27 | -11.02 | 113.8 | 2.22 | 7.24 | 2.76 | 2.42 | 9.15 | 8.77 | -0.07 | -0.07 |  |
| 3 | 4.3 | 160.71 | 6.28 | 11.63 | 154.93 | 4.44 | 0 | 23.78 | 4.44 | 8.72 | 9.86 | 0.02 | 0.13 |  |
| 4 | 3.56 | 6241.17 | 6.23 | 1.37 | 83.82 | 3.35 | 5.77 | 40.23 | 5.67 | 7.33 | 7.22 | 0.22 | 0.17 |  |
| 5 | 3.46 | 229.04 | 6.35 | -18.47 | 126.71 | 4.66 | 0 | 4.75 | 4.66 | 8.51 | 9.89 | -0.09 | 0.26 |  |
| 6 | 3.03 | 251.04 | 6.05 | -39.4 | 125.21 | 3.59 | 2.04 | 24.95 | 4.1 | 8.66 | 9.88 | -0.11 | -0.25 |  |
| 7 | 2.73 | 310.66 | 5.8 | -62.53 | 133.2 | 1.85 | 3.94 | 28.56 | 2.97 | 8.57 | 9.82 | 0.46 | 0.54 |  |
| 8 | 2.77 | 40.41 | 5.63 | -59.2 | 106.07 | 2.28 | 4.46 | 0.00 | 2.28 | 9.69 | 9.95 | -0.4 | -0.51 |  |
| 9 | 2.65 | 22.74 | 5.35 | -56.9 | 116.32 | 1.84 | 4.22 | 0.00 | 1.84 | 9.57 | 9.78 | -0.12 | -0.18 |  |
| 10 | 2.14 | 74.93 | 5.01 | -69.57 | 124.54 | 1.43 | 3.61 | 18.89 | 2.12 | 8.6 | 9.08 | 0.55 | 0.55 |  |

Table notes: From left to right, the columns represent region number (GMC), mean deviation from the model to the observed data (adev), total luminosity ($\rm{Lum_{tot}}$), stellar mass ($M_\star$), velocity offset ($v_0$), stellar velocity dispersion ($\sigma_\bigstar$), attenuation at V band ($A_{\rm{V}}$), extra extinction applied to young stellar populations ($\delta A_{\rm{V}}$), percentage of stellar populations affected by the extra extinction ($x(\delta A_{\rm{V}}>0)$), the effective extinction ($\tilde {A_{\rm{V}}}$), which is equivalent to $A_{\rm{V}}+\delta A_{\rm{V}} \times x(\delta A_{\rm{V}}>0)$ and corresponds to the total extinction; the mean light-pondered ages ($\langle \log t_\star \rangle_{L}$), mean logarithmic mass-pondered ages ($\langle logt_\star \rangle _M$), mean logarithmic light-pondered metallicity ($\langle \log Z/Z_\odot \rangle _L$), and mean logarithmic mass-pondered metallicity ($\langle \log Z/Z_\odot \rangle _M$). Further information is provided in Sect. [4.2](#sec.MUSE_starlight).

![](Figures/myWHAN_fancy.pdf)

![](Figures/myBPT.pdf)

In most cases (GMCs 1–9), GalaPy yields stellar age estimates that are consistent with those from STARLIGHT, falling between the young and old stellar populations that best reproduce the optical stellar contribution modeled by STARLIGHT. This is more clearly seen in Fig. [22](#fig.stellar_ages_GalaPy_STARLIGHT_CIGALE), where we plot, for all ten GMCs studied in this work, the average old and young stellar population ages from STARLIGHT, and the global stellar ages from GalaPy. Both codes agree in that GMC 4 is the youngest in the sample, with younger stellar populations in GMCs 3 to 7 and older ones located in GMCs 1, 2, and 8 to 10. In addition, in the same plot we added results from CIGALE, whose output delivers youngest ages in general with the youngest stellar burst in GMC 5, very close to the youngest burst in GMC 4 derived by GalaPy.

### Emission line diagnostic diagrams

The fluxes of emission lines from the MUSE spectra were measured in the pure nebular spectra, which were obtained by subtracting the stellar population continuum from the observed spectra. The contribution of the stellar population was determined using the stellar population synthesis code STARLIGHT (cite: CidFernandes2005).

We show our results in Fig. [7](#fig.WHAN_BPT), where we extract the emission lines in our common 3$\ensuremath{''}$ diameter aperture using archival MUSE observations (PI: Laura Zschaechner). Fig. [7](#fig.WHAN_BPT) displays two diagnostic diagrams to analyze the dominant ionization mechanism of the emitting gas in the galaxy:

1.  The \[O III\] $\lambda5007$/H$\beta$ versus \[N II\] $\lambda6584$/H$\alpha$ diagnostic diagram proposed by (cite: Baldwin1981), commonly known as the BPT diagram. This diagram includes the theoretical separation between HII-like and AGN-like objects proposed by (cite: Kewley2001) \[K01\], and the empirical star-forming limit proposed by (cite: Kauffmann2003) \[K03\]. The region between the theoretical and empirical limits is commonly referred to as the “composite region,” although there are claims against this designation (see below).

2.  The WHAN diagram, namely, $\log(\mathrm{EW~H}\alpha)$ versus $\log([\mathrm{N~II}]\lambda6584)$ (cite: CidFernandes2010), which is used to differentiate the nature of the ionization sources, classifying objects as star-forming, strong AGNs, weak AGNs, or retired galaxies. The line at $\log(\mathrm{EW~H}\alpha) = 6\AA\,$ represents the limit between weak and strong AGN emission. We note that in this diagram, the chosen log10(\[N II\]$\lambda6584$/H$\alpha$; x-axis) limit to disentangle between SF and AGN gaseous ionization origin is normally taken from (cite: Stasinska2006) \[S06\] in the literature, although for NGC 253’s CMZ we can rely on K03 as there are no GMCs between S06 and K03 limits.

Although molecular gas and star-forming regions are known to spatially decorrelate at sub-100 pc scales (cite: Kruijssen2014; Chevance2020b), in the CMZ of NGC 253, we do observe gas and dust in regions where star formation is taking place, especially in the inner regions (cite: Bendo2015; Ando2017; RicoVillas2020) (see also the super star clusters in Fig. [2](#Fig.Cont_maps_ALCHEMI)). Nevertheless, our GMCs do not occupy the regions in these diagnostic diagrams that are typically associated with star-forming regions. Instead, they are located in what is often referred to as the “composite” zone, lying between star-forming and AGN-dominated areas. According to some studies, this behavior can occur in starbursts where stellar shocks are strong (cite: Kewley2001a), and we consider this as the most likely scenario for the CMZ of NGC 253, which is also consistent with recent ALCHEMI studies on shocks (cite: Bao2024; Bouvier2024). However, we cannot completely discard a decorrelation between star-forming regions and molecular gas in our line of sight given the large inclination (70$^\circ$–79$^\circ$; e.g., (cite: Pence1980)) of NGC 253.

However, given the lack of evidence for an actual AGN in NGC 253, and the fact that these line-ratios are observed well away from the nucleus, our GMCs are most likely not starburst$+$AGN composites. Instead, we prefer to describe them as “starburst$+$shocks” composites, where the observed line ratios are a mixture of star-formation and shocks from stellar winds and supernovae. Shocks are indeed known to be present in NGC 253 (cite: Meier2015; Holdship2022ApJ; Humire2022; Behrens2022ApJ; Harada2022; Huang2023; Behrens2024ApJ; Bouvier2024; Bao2024), whereas there is extensive literature arguing against the presence of an AGN (cite: FernandezOntiveros2009; Brunthaler2009; MullerSanchez2010).

From the SED perspective, a clear argument against the existence of an AGN is provided in Appendix [7](#apen.CIGALE_AGN), where the AGN fraction, $f_{\rm{AGN}}$ in Table [\[Apen.Tab.CIGALE_AGN\]](#Apen.Tab.CIGALE_AGN), is negligible ($<$7.5%) and also does not peak at the centrally located GMC 5 as one might expect in the presence of an AGN. Although this behavior could potentially suggest the presence of a low-luminosity AGN (LLAGN), it is more plausibly interpreted as an artifact of CIGALE’s attempt to accurately fit the AGN-free SED. Further arguments specifically against the presence of an LLAGN can be found, for instance, in (cite: Mangum2019).

### Attenuation estimations

The attenuation from dust in HII regions can be estimated using the Balmer lines H$\alpha$ and H$\beta$ by contrasting their observed ratios with their expected ratios without attenuation. The intrinsic H$\alpha$/H$\beta$ flux ratio is 2.86 under typical conditions of electron density ($n_{\rm{e}} \sim 100$ cm$^{-3}$) and temperature ($T_{\rm{e}} \sim 10,000$ K), although variations in these conditions can change the ratio by up to 4% (cite: Osterbrock2006). The so called Balmer extinction is given by

$$\begin{equation}
A_{\rm{V}}^{\rm Balmer}  = \frac{2.5}{ \frac{A_{\rm{H}\beta}}{A_{\rm{V}}} - \frac{A_{\rm{H}\alpha}}{A_{\rm{V}}} } \log_{10}\left(\frac{(F_{\rm{H}\alpha}/F_{\rm{H}\beta})_\text{obs}}{2.86}\right),
\label{eq.attenuation.1}
\end{equation}$$

where $A_{\mathrm{H}\beta}/A_{\rm{V}} = 1.14$ and $A_{\mathrm{H}\alpha}/A_{\rm{V}} = 0.82$ for a (cite: Calzetti2000) reddening law. In the following, we will apply this method to the GMCs studied in this work by measuring $(F_{\mathrm{H}\alpha}/F_{\mathrm{H}\beta})_{\text{obs}}$ for each region and estimating their respective attenuations.

For comparison, we also considered the attenuation model proposed by (cite: CharlotFall2000), a widely used approach for estimating dust extinction in stellar populations. This method distinguishes between the contributions of young and old stellar populations, assigning different power-law attenuation slopes to each. The attenuation for young populations, attributed to birth clouds, is represented by $\alpha_{\rm{BCs}}$, while that for older populations, associated with the ISM, is denoted as $\alpha_{\rm{ISM}}$, as described in Eq. [\[eq.CF2000\]](#eq.CF2000). According to this framework, stars are initially formed within interstellar birth clouds (BCs) and migrate to the ISM after approximately $10^7$ years. The transition between these two attenuation regimes occurs at a wavelength of 5,500 $\text{\AA}$. In CIGALE, this model can be adopted using the `dustatt_2powerlaws module`. The functional form of the law is commonly expressed in the literature as:

$$\begin{equation}
\label{eq.CF2000_orientative}
A(\lambda) = 
\begin{cases} 
A_{\lambda}(\text{BC}) + A_{\lambda}(\text{ISM}), & \text{for young stars, age} < 10^7 \, \text{years}, \\
A_{\lambda}(\text{ISM}), & \text{for old stars, age} > 10^7 \, \text{years}.
\end{cases}
\end{equation}$$

where $A_{\lambda}$ is the wavelength-dependent attenuation expressed as $A_{\lambda} = A_{\rm{V}} \left( \frac{\lambda}{\lambda_{\rm{V}}} \right)^\delta$, with $\lambda_{\rm{V}} = 5,500 \, \text{Å}$, and $A_{\rm{V}}$ represents the attenuation in the V band. In practice, this translates to the following expression:

$$\begin{equation}
\label{eq.CF2000}
A(\lambda) = A_\mathrm{V} \left[ \left( \frac{\lambda}{\lambda_0} \right)^{\alpha_{\rm{BCs}}}  (\lambda < 5500 \, \text{\AA}) + \left( \frac{\lambda}{\lambda_0} \right)^{\alpha_{\rm{ISM}}} (\lambda \geq 5500 \, \text{\AA}) \right],
\end{equation}$$

where $A_{\rm{V}}$ is the overall attenuation at 5,500 $\text{\AA}$ that we assume to be unity for simplicity. The exponents $\alpha_{\rm{BCs}}$ and $\alpha_{\rm{ISM}}$ describe the slopes for the birth clouds and the ISM, respectively. In the implementation, the values for $\alpha_{\rm{BCs}}$ range from –0.69 to $-$0.9, while $\alpha_{\rm{ISM}}$ ranges from –0.75 to –0.3. We find these values starting from those commonly used in (cite: CharlotFall2000) and also being influenced by other works that assume a -0.7 (an original assumption from C&F 2000) value for both stellar populations. Then, looking at our GalaPy-derived curves from the SED, we set values that better reproduce the observations.

We compute the attenuation curves over a wide wavelength range, from the near-UV to the near-infrared, using these parameter ranges. The curves are normalized at 5,500 $\text{\AA}$ to allow a consistent comparison. As shown in Fig. [8](#fig.attenuation_curves), the model’s attenuation curves are sensitive to the chosen values of $R_{\rm{V}}$ for the (cite: Calzetti2000) attenuation law, which assumes a single attenuation slope for all stellar populations, and the values of $\alpha_{\rm{BCs}}$ and $\alpha_{\rm{ISM}}$ in the case of the (cite: CharlotFall2000) models. The better agreement of our model-inferred attenuation laws with the (cite: CharlotFall2000) prescription compared to (cite: Calzetti2000) stems from fundamental differences in their treatment of the star-dust geometry, which are particularly critical in the dense, young stellar environments of NGC 253’s giant molecular clouds. While (cite: Calzetti2000) provides a robust empirical description for homogeneous starburst systems by assuming a single attenuation component with a gray slope ($R_{\rm{V}}$ $\sim$ 4.05) and suppressed 2175$\text{\AA}$ UV bump (cite: Conroy2013; Samir2020), it fails to capture the spatially segregated attenuation effects expected in galaxies with distinct birth clouds and diffuse ISM components. Our results align with theoretical studies demonstrating that the two-component (cite: CharlotFall2000) models – which separate the attenuation between optically thick birth clouds and a diffuse ISM with shallower attenuation – better reproduces the observed SEDs of systems with ongoing star formation in dense environments. This is consistent with NGC 253’s molecular clouds, where young stars remain embedded in their natal dusty clouds, creating a non-uniform attenuation geometry that the Calzetti law’s simplified single-screen approximation cannot adequately model. The widespread adoption of the Calzetti law in literature reflects its utility for global galaxy-scale attenuation in starburst-dominated systems, but our findings emphasize that its limitations become pronounced in resolved studies of individual star-forming regions.

![image](Figures/Attenuations_curves.pdf) ![image](Figures/CF2000.pdf)

Table [3](#tab:attenuation_comparison) lists the measured Balmer decrement, the corresponding $A_{\rm{V}}^{\mathrm{Balmer}}$, as well as the $A_{\rm{V}}$ values obtained with CIGALE and STARLIGHT. As expected from the extremely red shape of the optical spectra (see Fig. [5](#Fig.STARLIGHT_fit)), we obtain large values of $A_{\rm{V}}^{\mathrm{Balmer}}$: from 1 to 6 mag. The largest values are found for GMCs 3, 4, 5, and 6, which are closer to the galactic bar and in dense star-forming areas. We note, however, the very substantial uncertainties in $(F_{\mathrm{H}\alpha}/F_{\mathrm{H}\beta})_{\text{obs}}$ (ranging from 10 to nearly 90%). These happen because of the weak $\mathrm{H}\beta$ emission, which is barely visible in most cases in Fig. [5](#Fig.STARLIGHT_fit).

Table [3](#tab:attenuation_comparison) further lists the STARLIGHT results for the extinction. In the case of STARLIGHT the table gives $\tilde{A}_{\rm{V}}$, which we define as the average of the extinctions affecting all populations ($A_{\rm{V}}$) and that affecting only those younger than 10 Myr ($A_{\rm{V}} + \delta A_{\rm{V}}$), weighting them by the fluxes of the respective components as derived from the fits. Again, the extinction values are large (1.8–5.7 mag), as expected from the redness of the optical continuum. The derived values are close to, but in general somewhat smaller than those derived from the Balmer decrement. CIGALE values of $A_{\rm{V}}$ are, in median, 16% lower than those from the Balmer decrement, $A_{\rm{V}}^{\rm Balmer}$. On the other hand, STARLIGHT-based values also differ from those of $A_{\rm{V}}^{\rm Balmer}$ by a median value of 27%.

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| GMC | $(F_{\rm{H}\alpha}/F_{\rm{H}\beta})_\text{obs}$ | $A_{\rm{V}}^\text{Balmer}$ | $A_{\rm{V}}^\text{CIGALE}$ | $\tilde{A_{\rm{V}}}^\textsc{starlight}$ |  |
|  |  | \[mag\] | \[mag\] | \[mag\] |  |
| 1 | $3.81 \pm 0.32$ | $1.08 \pm 0.11$ | $3.57 \pm 0.02$ | $2.12$ |  |
| 2 | $8.32 \pm 1.70$ | $2.89 \pm 0.30$ | $3.58 \pm 0.02$ | $2.42$ |  |
| 3 | $29.79 \pm 16.90$ | $5.06 \pm 0.56$ | $6.04 \pm 0.11$ | $4.44$ |  |
| 4 | $45.69 \pm 37.94$ | $5.87 \pm 0.67$ | $6.06 \pm 0.00$ | $5.67$ |  |
| 5 | $43.43 \pm 37.37$ | $5.81 \pm 0.65$ | $6.24 \pm 0.02$ | $4.66$ |  |
| 6 | $29.14 \pm 16.45$ | $5.04 \pm 0.54$ | $6.08 \pm 0.01$ | $4.10$ |  |
| 7 | $21.21 \pm 10.11$ | $4.38 \pm 0.47$ | $5.07 \pm 0.02$ | $2.97$ |  |
| 8 | $19.18 \pm 10.04$ | $4.18 \pm 0.45$ | $3.53 \pm 0.01$ | $2.28$ |  |
| 9 | $17.01 \pm 7.84$ | $3.96 \pm 0.42$ | $3.54 \pm 0.01$ | $1.84$ |  |
| 10 | $11.13 \pm 5.05$ | $3.36 \pm 0.37$ | $3.54 \pm 0.12$ | $2.11$ |  |

: GMC attenuations.

Table notes: Attenuation estimates for the studied giant molecular clouds (GMCs) derived from the Balmer decrement ($A_{\rm{V}}^\text{Balmer}$), CIGALE ($A_{\rm{V}}^\text{CIGALE}$), and effective $A_{\rm{V}}$ ($\tilde{A_{\rm{V}}}^\textsc{starlight}$) from STARLIGHT. The first two columns correspond to the GMC number and the H$\alpha$ over H$\beta$ observed flux ratio, from left to right, respectively.

The only GMC where $\tilde{A}_V$ exceeds $A_{\rm{V}}^{\rm Balmer}$ is GMC 1. This discrepancy may suggest additional sources of attenuation, potentially linked to warm or dense dust. One possible explanation is the influence of strong shocks, which could sputter dust grains and enhance local dust densities. Supporting evidence for the presence of shocks in GMC 1 comes from its elevated SiO $J=$5–4/HNCO (10$_{0,10}$–9$_{0,9}$) transition ratios observed at about 220 GHz (ALMA Band 6). This region shows the highest ratio values, averaging around 1.3, as noted in the right panel of Fig. 11 in (cite: Humire2022). In contrast, the mean ratio in other regions is 0.5, excluding GMC 10, where this ratio cannot be measured. The above values have been derived using an aperture of 3.0$''$ and the coordinates from this work, listed in Table [1](#tab.positions). These elevated ratios are well-known tracers of strongly shocked gas, indicating a prevalence of strong (traced by SiO) over weak/mild shocks (traced by HNCO). Additionally, GMC 1 hosts methanol masers with the strongest deviations from LTE expectations among the 10 GMCs, as illustrated in the left panel of Fig. 13 in (cite: Humire2022). While these observations strongly point to the presence of shocks, they are not direct indicators of warm or dense dust. However, shocks may indirectly affect the dust environment by altering its spatial distribution or properties. Future studies are needed to assess whether gas and dust are tightly coupled in this region and to determine the extent to which shocks influence the observed attenuation.

![](Figures/Att_vs_Age_mcmc_with_stats_v3_2_Gyr.pdf)

We compared the stellar continuum attenuation in the V-band, $A_{\rm{V}}$, with the corresponding stellar colour excess, E(B-V)s (represented by the `attenuation.E_BVs` parameter), both derived from the CIGALE spectral energy distribution fitting results (Tables [3](#tab:attenuation_comparison) and [\[Apen.Tab.Extinction_Factors_CIGALE\]](#Apen.Tab.Extinction_Factors_CIGALE)). We find that the ratio $A_{\rm{V}}$/E(B-V)s ranges from $\sim$4.0 to 6.3 across our sample. Notably, this ratio systematically differs from the value $R_{\rm V} = 3.1$ that was set as an input parameter in our CIGALE configuration.

This apparent discrepancy arises from the specific implementation within the `dustatt_modified_starburst` module used in our analysis. This module employs distinct attenuation laws for the stellar continuum and the nebular emission lines. The input parameter $R_{\rm V}=3.1$, characteristic of the diffuse interstellar medium in the Milky Way (cite: Cardelli1989), governs the shape of the Cardelli et al. extinction curve applied specifically to the nebular emission lines (as we selected `Ext_law_emission_lines = 1`). However, the attenuation affecting the stellar continuum (from which $A_{\rm{V}}$ and E(B-V)s are primarily determined) is modeled using the empirical starburst attenuation law from (cite: Calzetti2000), which can be further modified by a power-law slope ($\delta$) and a UV bump. The baseline Calzetti law itself possesses an effective ratio $A_{\rm{V}}$/E(B-V) $\approx 4.05$, inherently different from the Milky Way value. The flexibility introduced by the allowed modifications ($\delta$ and the UV bump) within the module accounts for the observed range of $A_{\rm{V}}$/E(B-V)s extending above this baseline value, consistent with the methodology described in (cite: Boquien19). Therefore, the $A_{\rm{V}}$ and E(B-V)s values derived for the stellar component are not expected to follow the relation $A_{\rm{V}} = 3.1 \cdot$E(B-V)s, but rather reflect the properties of the modified Calzetti law applied to the integrated starlight.

GalaPy derived attenuation curves are shown in Fig. [8](#fig.attenuation_curves), where curves indicate the attenuation in the visible band and legends show its value at 5500Å, on a linear scale, to be compared with STARLIGHT outputs (Table [\[Tab.STARLGIGHT_results\]](#Tab.STARLGIGHT_results)). The results from this code are normalize at that wavelength value. $R_{V}$ values following (cite: Calzetti2000) are also included for comparison. These values describe the relationship between the total amount of dust extinction and the amount of reddening it causes in the context of the Milky Way’s dust extinction curve and corresponds to the ratio between the total extinction $A_{V}$ and the color excess E(B-V). Considering the ten GMCs studied, most $R_{\rm{V}}$ values range between 6 and 9, far beyond the Galactic value of 3.1. Surprisingly, the extreme values are found in clouds located at the boundaries of the CMZ, with the highest $R_{\rm{V}}$ values in GMCs 2 and 9. These clouds are closer to the modeled curves (dashed lines in the left panel of Fig. [8](#fig.attenuation_curves)) corresponding to $R_{\rm{V}} \sim 8$–9. In contrast, the lowest $R_{\rm{V}}$ value is found in GMC 1, which is best matched by a modeled curve with $R_{\rm{V}} \sim 4$.

As a final remark, when comparing the different attenuation estimates, it is important to recognize that the gas attenuation (from the Balmer decrement) and stellar attenuation (from GalaPy, CIGALE, and STARLIGHT in our case) have distinct origins. Recent studies suggest that these two types of attenuation should become increasingly similar as the observed region ages (cite: Li2024).

However, we do not see a clear trend for attenuation differences between the ones derived from the Balmer decrement and those obtained from CIGALE, namely $\Delta A_{\rm{V}} = A_{\rm{V}}^{\rm{Balmer}} - A_{\rm{V}}^{\rm{CIGALE}}$, taken from Table [3](#tab:attenuation_comparison), versus derived stellar ages from either GalaPy or CIGALE (last columns of Tables [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy) and [\[Tab.CIGALE_main_results\]](#Tab.CIGALE_main_results), respectively), we do see a trend when comparing attenuation differences between Balmer lines and the gas attenuation derived from the stellar continuum by STARLIGHT, namely $\Delta A_{\rm{V}} = A_{\rm{V}}^{\rm{Balmer}} - A_{\rm{V}}^{\textsc{\rm{starlight}}}$, versus stellar ages derived by CIGALE. For an easy visualization of that finding, in Fig. [9](#fig.attenation_diff_vs_CIGALE_age) we present such a relation.

### Linear regression

The procedure for all linear regressions in this work, including Fig. [9](#fig.attenation_diff_vs_CIGALE_age), followed two main steps. First, we used the `linregress` function from the `scipy` Python library to obtain initial priors. For power-law relationships, we performed the regression in log-space when required (using $\log_{10}$ values as inputs), with results either maintained in logarithmic form ($\log y = m\log x + c$) or converted back to linear space depending on the analysis.

The second step applied Bayesian inference through Markov Chain Monte Carlo (MCMC) sampling using the `emcee` Python package (cite: Foreman-Mackey2013). Unlike `linregress`, MCMC incorporates uncertainties in both axes (x and y), which were rigorously included in our modeling. We ran 1,000 iterations per fit with 50 walkers, discarding the first 100 as burn-in to ensure convergence. The resulting posterior distributions provided robust estimates of the slope and intercept, with their $1\sigma$ uncertainties represented as shaded regions in all plots.

## Star formation rates

### Kennicutt (1998): H$\alpha$–SFR calibration

![](Figures/from_Gaussian_emcee_v6.pdf)

There are many ways to obtain the SFR from monochromatic emission. One of the most commonly used is the relation found by (cite: Kennicutt1998) regarding H$\alpha$, which we will hereafter refer to as the “Kennicutt relation”:\
$$\begin{equation}
\rm{SFR}~ [\mathrm{M_{\odot}~year^{-1}}] = 7.9 \times 10^{-42} L(\mathrm{H\alpha})~[\mathrm{erg~s^{-1}}].
\label{eq.KS_rel}
\end{equation}$$

where $L(\mathrm{H\alpha})$ is corrected for extinction using $A_{\rm{H}\alpha} = 0.82 \times A_{\rm{V}}^{\rm Balmer}$.

Fig. [10](#Fig.SFR_SED_MUSE_Ha) shows a comparison between the SFRs obtained from the above considerations and the one obtained from the SED fitting using GalaPy and CIGALE, while the dashed-black line indicates a one-to-one proportion. To create this plot we considered the attenuation of the H$\alpha$ emission line derived SFR considering the $A_{\rm{V}}^{\rm{Balmer}}$, since it is expected to be the most accurate method: STARLIGHT and SED derived attenuation rely on the continuum level.

We notice that SFRs derived by GalaPy (red symbols in Fig. [10](#Fig.SFR_SED_MUSE_Ha)) tend to be larger than expected by the Kennicutt relation. This result is expected if the instantaneous SFR is greater than the average SFR over 10 Myr, as the SFR derived from H$\alpha$ corresponds to the stellar formation averaged over that period of time (cite: Stroe2015). When considering the 10 Myr and 100 Myr averaged SFRs from CIGALE (blue and gray symbols in Fig. [10](#Fig.SFR_SED_MUSE_Ha), respectively), the Kennicutt relation is followed more closely at 100 Myr than at 10 Myr (see Table [\[Tab.CIGALE_main_results\]](#Tab.CIGALE_main_results)). However, the slope which is closer to 1 is obtained from CIGALE’s SFR$_{\rm{10~Myr}}$, in line with what is expected from deriving the SFR from H$\alpha$ emission.

![](Figures/SFR_from_H_40alpha.pdf)

![](Figures/Ka_Band_vs_H40a_v7_single_column.pdf)

![](Figures/SFR_radio_vs_SED_combined_1line_bigger_mcmc_v2.pdf)

![](Figures/SFR_IR_vs_SED_combined_with_errors_and_GMC_bigger_mcmc_final_trap_int_v2.pdf)

### Radio recombination lines

There are several methods to estimate the SFR of an astronomical source. One of the most accurate techniques, unaffected by dust extinction, relies on radio recombination lines (RRLs). Following the approach of (cite: Bendo2015), who used the H$40\alpha$ line at 99.02 GHz, we derived the SFR for the nuclear GMCs (specifically GMCs 3 to 6). Figure [11](#Fig.SFR_H40a) displays the SFR density in units of M$_{\odot}$ yr$^{-1}$ spaxel$^{-1}$, after selecting the free-free emission only, namely, after applying a correction of 70% to H40$\alpha$’s total emission, as described in (cite: Bendo2015).

To contextualize our results, we compared our SED-based estimates (GalaPy; Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy)) with those derived from the H40$\alpha$ line in (cite: Bendo2015) with observations at a similar resolution. While our aperture is larger than theirs (see their Fig. 1, leftmost panel), the regions are comparable: their West, Central, and East regions correspond to our GMCs 4, 5, and 6, respectively. The SFRs derived from the H40$\alpha$ line in (cite: Bendo2015) (their Table 1) are on average between 6% (total H40$\alpha)$ and 25% (free-free corrected) lower than the ones derived by GalaPy, and this can be due to our larger apertures.

Eliminating the effect of different aperture sizes by taking the total emission in NGC 253’s CMZ, we conciliate the results: (cite: Bendo2015) reported a total SFR of $1.73\pm 0.12~\text{M}_{\odot}\,\text{yr}^{-1}$ for NGC 253’s CMZ within a $20 \times 10$ arcsec region. A separate $9\ensuremath{''}$-radius SED (GalaPy) analysis (including Herschel PACS data) encompassing GMCs 4–6 (Fig. [25](#fig.FIR_SEDs_attempts), bottom inset in the left panel) yields a SFR of $1.620^{+0.201}_{-0.156}~\text{M}_{\odot}\,\text{yr}^{-1}$. Including the contribution from GMCs 3 ($0.087^{+0.011}_{-0.009}~\text{M}_{\odot}\,\text{yr}^{-1}$) and 7 ($0.022^{+0.003}_{-0.002}~\text{M}_{\odot}\,\text{yr}^{-1}$), which also fall within the mentioned region, the total SFR raises to $1.729^{+0.201}_{-0.156}~\text{M}_{\odot}\,\text{yr}^{-1}$, consistent with (cite: Bendo2015)’s (free-free) value within uncertainties.

Since the H40$\alpha$ line is only detectable in the inner regions of the studied CMZ, at SFRs larger than about 0.870 $\text{M}_{\odot}~\text{yr}^{-1}$ (GalaPy) or 0.262 $\text{M}_{\odot}~\text{yr}^{-1}$ (CIGALE), considering GMC 3’s SFR as the lower limit, we wanted to probe its derived SFR at spaxel levels. With that aim, we decided to consider the EVLA Ka-Band, at 32.8 GHz, which is the Band that better correlates with our SED analysis, as we will see in the next Subsection [4.3.3](#subsubsection.SFR_from_radio_cm_and_FIR). To derive the SFR from that band, we applied the best-fit from the linear regression labeled in Fig. [13](#Fig.SFR_GalaPy_vs_radio) upper panels, which for the case of the mentioned Band is: $$\begin{equation}
\label{eq.SFR_from_Ka_band}
   \mathrm{SFR_{SED}} [M_{\odot}~\mathrm{yr}^{-1}] = L_{32.8~\mathrm{GHz}}^{1.06}~[\mathrm{erg s^{-1}~Hz^{-1}}] \cdot 10^{-29.27},
\end{equation}$$ in linear scale. The resulting SFR value is what we used in the y-axis of Fig. [12](#fig.comparing_SED_with_H40a) while, on the x-axis, we plot the same values as shown in Fig. [11](#Fig.SFR_H40a).

Fig. [12](#fig.comparing_SED_with_H40a) shows a variety of fits, the best fit found considering all spaxels is shown as a solid red line while the best-fitting values per GMCs are color-coded. In general, the correlations are very strong, with the largest Pearson correlation coefficient ($\langle R \rangle$) and the closest slope to unity found for GMC 5. Taking the dashed black line, which denotes a 1:1 correspondence (“corr.” in the Fig.), as a reference, we find that the H40$\alpha$ derived SFR tends to be slightly overestimated in GMC 5 and slightly underestimated in the other GMCs. In general, the correlation is strong ($\langle R \rangle =$0.97) and the values tend to be slightly lower than the derived ones from the 33 GHz band, with a general slope of 1.07$\pm$0.01.

We note that GalaPy measures the instantaneous SFR, whereas RRLs trace star formation over the last $\sim$5–10 Myr (cite: Scoville2013; Emig2020). The tight correlation between the Ka-band and H$40\alpha$ SFRs (Figure [12](#fig.comparing_SED_with_H40a)) suggests that both tracers reliably probe recent star formation activity, and that the comprised timescales should be similar.

### Radio cm continuum and FIR

As summarized in (cite: Murphy11), there are several SFR tracers in the wavelength range considered in this work. According to these authors, the 33 GHz continuum emission is a reliable indicator of current star formation, as it primarily arises from thermal free-free emission. Although this frequency can sometimes be affected by rotating dust, this is not the case for NGC 253 at the studied scales, as shown in the SEDs. We indeed find a strong correlation between the emission in the EVLA Ka Band, as originally published in (cite: Kepley2011), and the total SFR computed by GalaPy. Furthermore, accounting for scaling offsets, we also observe generally good correlations—close to a 1:1 correspondence—between cm tracers and the GalaPy results, as seen in Fig. [13](#Fig.SFR_GalaPy_vs_radio). The latter was obtained using the same approach as for the 33 GHz data, namely, by performing a linear regression in logarithmic space with all retrieved (E)VLA continuum images that detect at least four GMCs (see Table [\[Tab.observations\]](#Tab.observations)), aiming to obtain the best-fit assembly valid for the GMCs in the starburst galaxy NGC 253. A caveat should be noted, as different galaxy types (e.g., MW-like, dwarf galaxies, AGN hosts) may present different relationships. In this regard, an immediate prospect for the current work is to evaluate the different relations between SFR tracers.

Accounting for IR points as SFR tracers, as can be seen in Fig. [14](#Fig.SFR_GalaPy_vs_IR), we generally find a comparable dispersion and quality of fit (in terms of mean $R$) to that obtained with radio bands. However, it is important to note that, since these IR data points are directly derived from the GalaPy SED fitting employed to estimate the SFR, they are not entirely independent of the latter. On the other hand, while the flux uncertainties (along the x-axis) associated with the IR data are considerably larger than those of the radio bands, this is compensated by the availability of IR points for all ten GMCs. Notwithstanding this potential interdependence, the general conclusion drawn from the IR tracers is that the best ones correspond to the integrated IR emission between 8 and 1000 $\mu$m, commonly referred to as total IR emission, and the IR emission at 60 $\mu$m.

For the radio bands, unlike optical lines, we do not assume a relation factor a priori, we only convert our mJy measurements to erg s$^{-1}$ Hz$^{-1}$ for an easy comparison between this study and the literature. For the mJy to erg s$^{-1}$ Hz$^{-1}$ conversion we have assumed a distance of 3.5 Mpc to NGC 253 (cite: Rekola2005). For the IR bands, we retained the original units of mJy or mJy $\AA$ to allow for straightforward comparison with other studies.

# Discussion

## Reliability of our SED model along the FIR window

One of the critical, if not the most critical, challenges that astronomers have to face when attempting to fit a panchromatic SED at high angular resolution is the impossibility to acquire far infrared (FIR) observations at resolutions below 6$\ensuremath{''}$. Current facilities in the regime, such as the James Webb (JWST) and Euclid telescopes, cover mainly the near-IR and mid-IR parts of the electromagnetic spectrum, with the largest wavelength window ranging from 0.5 (Euclid) to 28 $\mu$m (JWST). Indeed, only the JWST can keep angular resolutions below $\sim$0.8$\ensuremath{''}$ at 28 $\mu$m. However, the FIR bump primarily occurs at wavelengths larger than those, mainly from about 50 to 300 $\mu$m.

While we made use of our well covered sub-mm regime, with ALCHEMI data, to fine-tune the Rayleigh-Jeans tail, at the emergence of the FIR bump on the radio side. We also used VLT/NACO data at 11 and 18.7 $\mu$m on the MIR side for GMCs 3–7, we know the caveat that this is likely not enough to properly ensure the fit on the IR bump itself, relying on our SED model extrapolations. This is why we further retrieved archival Herschel PACS observations selecting level 2.5 PACS images at 70, 100, and 160 $\mu$m. While these FIR observations are not able to resolve the targeted GMCs, they are sufficient to fit emission from the inner part of the CMZ, covering at most GMCs 3 to 6 in the worst-case scenario (at 11.3$\ensuremath{''}$), and partially covering GMCs 4 to 6 at 6 and 9$\ensuremath{''}$ (see Appendix [11](#apen.testing_at_9_arcsec) for more information on the latter).

In Fig. [25](#fig.FIR_SEDs_attempts) it can be noted that the far infrared peak agrees between the 3$\ensuremath{''}$ aperture SED, devoid of FIR photometric points and the SED at 9$\ensuremath{''}$, whose diffuse dust temperature, $T_{\rm{DD}}$, of 68.8$_{-13.9}^{+7.8}$ K is in agreement to the ones of the covered GMCs (GMCs 4–6), as noted in Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy). Specifically, we get $T_{\rm{DD}}$ estimations of 84.5$_{-12.6}^{+6.8}$, 67.9$_{-3.9}^{+4.0}$, and 63.3$_{-2.8}^{+3.2}$ K for GMCs 4, 5, and 6, respectively. All in all, this arguments in favor of our 3$\ensuremath{''}$ apertures as the FIR bump and the SED shape in general peak at a very similar point. It is worth noting that the SED shape is responsible for specific star formation rate estimates and, thus, for the stellar mass and SFR estimates as well (cite: Conroy2013).

Given the lack of FIR photometric points in the FIR regime at 3$\ensuremath{''}$, our SED models experienced considerable freedom in this specific wavelength range. We found that GalaPy produced SED shapes that were closer, compared to CIGALE’s models, to those observed at 9$\ensuremath{''}$, where Herschel PACS observations are available. Nevertheless, it is worth emphasizing that CIGALE performs well in fitting the SED of GMC 5 at 9$\ensuremath{''}$ (which also includes GMCs 4 and 6), both with and without an AGN component, as discussed in Appendix [7](#apen.CIGALE_AGN).

## Comparison to high-z dusty starbursts

The question of whether local starbursts can serve as analogues of primeval dusty galaxies at high redshifts ($z>4-8$) remains a topic of active debate. A useful parameter in this context is the dust-to-stellar mass ratio, which provides insight into the balance between dust production and destructive processes such as supernova-driven shocks and astration ((cite: nanni20), (cite: donevski20), (cite: kokorev21), (cite: donevski23), (cite: witstok23), (cite: palla24), (cite: sawant25)).

To place the ISM conditions of NGC 253 into perspective against those of distant dusty galaxies, we compare the dust-to-stellar mass ratios ($M_{\rm dust}/M_{\star}$) derived in this work to those inferred from ALMA observations of high-$z$ starbursts ((cite: donevski20), (cite: salak24), (cite: sawant25)). Regardless of the SED fitting code used, all GMCs in NGC 253 exhibit relatively high dust-to-stellar mass ratios, with a median value of $\log(M_{\rm dust}/M_{\star}) = -2.32 \pm 0.29$ (values from CIGALE), or $\log(M_{\rm dust}/M_{\star}) = -2.89 \pm 0.45$, if values from GalaPy are considered. These ratios are close to those observed in young dusty starburst galaxies in the distant Universe. Specifically, the average dust-to-stellar mass ratio is $\log(M_{\rm dust}/M_{\star}) = -2.13 \pm 0.3$ at $z \sim 2-5$ ((cite: donevski20)) and $\log(M_{\rm dust}/M_{\star}) = -2.58 \pm 0.4$ at $z \sim 4-6$ ((cite: sawant25)). A caveat in comparing the dust-to-stellar mass ratio found here with literature is in the method used to derive galaxy properties. Both in (cite: donevski20) and (cite: sawant25), the SED fitting is performed using CIGALE, which results in average lower values with respect to GalaPy, as also reported above.

Moreover, inferred attenuation values in the GMCs of NGC 253 are comparable to those observed in high-$z$ dusty starbursts but also significantly higher than those typically found in JWST-detected galaxies at $z > 6-8$ (e.g., (cite: nanni20), (cite: alvarez24), (cite: markov25)). It is important to note that, despite their comparable "dustiness," GMCs in NGC 253 have $M_{\star}$, SFR and sSFR several orders of magnitude lower than their high-$z$ counterparts. In such low stellar mass regimes, dust production is generally expected to be dominated solely by stellar sources, such as Type II supernovae ((cite: galliano19), (cite: sommovigo20)).

However, recent models suggest that dust production in young starbursts may be significantly diminished due to ISM removal in the presence of strong stellar outflows, similar to those observed in NGC 253. To reconcile the high dust-to-stellar mass ratios, these models propose efficient growth of large dust grains through ISM accretion in rapidly cooling gas within stellar outflows ((cite: hirashita23), (cite: donevski23), (cite: romano24), (cite: palla24)). While a detailed exploration of this intriguing possibility lies beyond the scope of this work, we note that the high dust-to-stellar mass ratios and attenuations observed in the GMCs may signal that NGC 253 is undergoing a shift in the dominant dust production mechanisms, as proposed by recent simulations (see e.g., (cite: narayanan25), also (cite: schneider24) for a review).

# Conclusions and prospects

This study represents a significant step forward in understanding the CMZ of NGC 253, utilizing the first panchromatic SED analysis at a 51-pc resolution towards extragalactic regions. The integration of diverse modeling approaches, from GalaPy to CIGALE and STARLIGHT on the stellar continuum features, enabled a thorough characterization of physical properties such as star formation rates, dust and stellar masses, and attenuation effects across ten GMCs using both parametric and non-parametric models.

The integration of multi-wavelength SED modeling tools, such as GalaPy and CIGALE plus the integration of mono-wavelength tracers in the optical using STARLIGHT and the sub-mm using ALMA observations, provided detailed insights into star formation histories, attenuation, and stellar population properties at different timescales. High extinction values (e.g., A$_V$ exceeding 5 magnitudes in internal GMCs) were robustly derived, aligning well with other methods and showcasing the importance of panchromatic approaches.

We summarize our main findings below.

1.  Dynamical and chemical diversity: The Central Molecular Zone (CMZ) of NGC 253 exhibits significant dynamical and chemical distinctions between internal (nuclear) and external GMCs. Internal GMCs (e.g., GMCs 3–6) are characterized by higher star formation rates (SFR), stellar masses, and dust masses, consistent with active star formation, high-excitation regions, and higher metallicities. External GMCs (e.g., GMCs 1, 2, 7–10) display lower density, slower and weaker shocks, and chemical signatures indicative of less energetic processes as compared to the internal GMCs.

2.  Comparison of internal vs. external GMCs: Internal GMCs exhibit stellar masses in the range of $3.7^{+1.1}_{-0.7}$–$7.1^{+5.5}_{-1.4} \times 10^8 M_\odot$ and dust masses in the range of $1.6^{+0.7}_{-0.3}$–$5.8^{+3.5}_{-3.0} \times 10^5 M_\odot$, both greatly surpassing (doubling) maximum values observed in external GMCs. Specific star formation rates (sSFR) further underscore these differences, exhibiting a trend of enhanced values in the nuclear regions.

3.  Insights from age-metallicity relations: Differences in stellar ages and metallicities highlight the varied evolutionary states of the studied GMCs. Depending on the adopted software, these values can vary by up to two orders of magnitude in age (STARLIGHT; Tab [\[Tab.STARLGIGHT_results\]](#Tab.STARLGIGHT_results)) and one order of magnitude in metallicity (GalaPy; Tab [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy)).

4.  Emission line diagnostics: The BPT and WHAN diagrams indicate shock signatures in the nuclear region of NGC 253, placing it in the composite zone. However, these shocks likely result from stellar winds and supernovae in the starburst environment, not from AGN activity.

5.  Caveats on H$\alpha$’s derived SFR: While H$\alpha$ remains a popular SFR tracer, our analysis reveals its significant limitations in NGC 253’s dust-obscured CMZ, where attenuation causes large discrepancies compared to more robust radio (e.g., the band at 33 GHz) and panchromatic SED tracers, suggesting H$\alpha$ should be supplemented with dust-insensitive indicators in similar environments.

6.  Star formation, panchromatic vs. monochromatic results: We have found a strong 1:1 correlation between cm tracers and SED derived SFR values, being the Ka-band (at 33 GHz) the best among the available dataset. This is in line with previous works based on entire galaxy properties (cite: Murphy11), and is now confirmed at GMC scales. Additionally, we validate the effectiveness of RRLs (H40$\alpha$) as a SF tracer, although limited to the brightest sources (GMCs 3–6).

The current study provides a robust framework for leveraging spatially-resolved multi-wavelength datasets to investigate the interplay between star formation, gas dynamics, and attenuation in starburst galaxies. In addition, this work not only advances our knowledge of starburst environments but also serves as a benchmark for studying high-redshift galaxies, where similar extreme conditions prevail.

In the future, we plan to focus on several key directions to broaden the applicability of these findings. These include utilizing JWST instead of Spitzer observations, achieving aperture diameters as fine as 1$''$ in the mid-IR, enabling more detailed analyses of star-forming regions and/or augmenting the redshift regime for our potential targets. We plan to apply the same approach to other well-known starburst like M 82. Alternatively, we want to improve the robustness of our fit by restricting ourselves to very nearby galaxies where FIR data from Herschel can still resolve GMC-scale structures, that is, if we assume a GMC size of 50 pc, and a Herschel aperture of 9$\ensuremath{''}$, we can utilize Herschel/PACS FIR observations of Milky Way’s and Andromeda’s satellites, yielding approximately 20 objects.

Additionally, this framework has the potential to be extended to diverse systems, including Milky Way like galaxies, LINERs, ULIRGs, and AGN, to explore differences in star formation processes across various galactic environments. Furthermore, focused studies of GMCs in our Galaxy will offer a critical baseline for contrasting extragalactic GMC properties, contributing to a thorough understanding of star formation under varying conditions. As a final remark, we also aim at providing future GalaPy users with a full set of priors well suited for GMC scales in extreme, intensively star-forming and highly obscured environments, which will also be helpful for Galactic analogues such as Sgr B2 mini-starbursting system (cite: Belloche2013; Schwoerer2019) and the distant (high-$z$) universe.

# Acknowledgements

We thank the anonymous referee for their helpful comments, questions, and suggestions on revising the manuscript. P.K.H. gratefully acknowledges the Fundação de Amparo à Pesquisa do Estado de São Paulo (FAPESP) for the support grant 2023/14272-4. P.K.H. acknowledges L. Barcos for discussions on the project’s initial scope, E. Caux for insights into the FIR cross-validation methodology, G. Ortiz-León for support with the EVLA X-band data reduction, and D. Hazarika for guidance on the proper implementation of the MCMC algorithm for the linear regression analysis. We thank A. Kepley for providing us with the 33 GHz (Ka-band) EVLA image. S.D has been supported by the Polish National Science Center project UMO-2023/51/D/ST9/00147 TR is supported by the Italian Research Center on High Performance Computing Big Data and Quantum Computing (ICSC), project funded by European Union - NextGenerationEU - and National Recovery and Resilience Plan (NRRP) - Mission 4 Component 2 within the activities of Spoke 3 (Astrophysics and Cosmos Observations). D.D. acknowledges support from the National Science Center (NCN) grant SONATA (UMO-2020/39/D/ST9/00720). JAFO acknowledges financial support by the Spanish Ministry of Science and Innovation (MCIN/AEI/10.13039/501100011033), by “ERDF A way of making Europe” and by “European Union NextGenerationEU/PRTR” through the grants PID2021-124918NB-C44 and CNS2023-145339; MCIN and the European Union – NextGenerationEU through the Recovery and Resilience Facility project ICTS-MRR-2021-03-CEFCA. M.H. acknowledges the support by the National Science Centre, Poland (UMO-2022/45/N/ST9/01336). V.M.R. and L.C. acknowledge support from the grant PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. V.M.R also acknowledges support from the grant RYC2020-029387-I funded by MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", and from the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC); and from the grant CNS2023-144464 funded by MICIU/AEI/10.13039/501100011033 and by “European Union NextGenerationEU/PRTR”. A.R.L. acknowledges financial support from Consejo Nacional de Investigaciones Científicas y Técnicas (CONICET), Agencia I+D+i (PICT 2019–03299) and Universidad Nacional de La Plata (Argentina). A.C.K thanks Fundação de Amparo à Pesquisa do Estado de São Paulo (FAPESP) for the support grant 2024/05467-9. SP is supported by the international Gemini Observatory, a program of NSF NOIRLab, which is managed by the Association of Universities for Research in Astronomy (AURA) under a cooperative agreement with the U.S. National Science Foundation, on behalf of the Gemini partnership of Argentina, Brazil, Canada, Chile, the Republic of Korea, and the United States of America. R.D. gratefully acknowledges support by the ANID BASAL project FB210003

For the near-UV, optical, and near-IR regimes, this work utilizes data from the S-PLUS collaboration (cite: MendesdeOliveira2019), as well as VLT and HST observations reported by (cite: FernandezOntiveros2009).

Additionally, this study is partially based on archival data obtained with the Spitzer Space Telescope, which was operated by the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA.

For radio observations, this work includes the following ALMA data: : ADS/JAO.ALMA#2017.1.00161.L and ADS/JAO.ALMA#2018.1.00162.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This study also made use of (extended) Karl G. Jansky Very Large Array archival observations provided by the National Radio Astronomy Observatory (NRAO), a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

In constructing the SED fitting at 9$\ensuremath{''}$ resolution, this work incorporates observations from the ESA Herschel Space Observatory (cite: Pilbratt2010), specifically using the PACS instrument (cite: Poglitsch2010).

144 natexlab

(ref: Allard2006) Allard, E. L., Knapen, J. H., Peletier, R. F., & Sarzi, M. 2006, MNRAS, 371, 1087

(ref: Allard2005) Allard, E. L., Peletier, R. F., & Knapen, J. H. 2005, ApJL, 633, L25

(ref: alvarez24) Álvarez-Márquez, J., Crespo Gómez, A., Colina, L., et al. 2023, A&A, 671, A105

(ref: Anantharamaiah1996) Anantharamaiah, K. R. & Goss, W. M. 1996, ApJL, 466, L13

(ref: Ando2017) Ando, R., Nakanishi, K., Kohno, K., et al. 2017, ApJ, 849, 81

(ref: Baes2011) Baes, M., Verstappen, J., De Looze, I., et al. 2011, ApJS, 196, 22

(ref: Baldwin1981) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5

(ref: Bao2024) Bao, M., Harada, N., Kohno, K., et al. 2024, A&A, 687, A43

(ref: Beck2022) Beck, A., Lebouteiller, V., Madden, S. C., et al. 2022, A&A, 665, A85

(ref: Behrens2022ApJ) Behrens, E., Mangum, J. G., Holdship, J., et al. 2022, ApJ, 939, 119

(ref: Behrens2024ApJ) Behrens, E., Mangum, J. G., Viti, S., et al. 2024, ApJ, 977, 38

(ref: Belfiori2025) Belfiori, D., Paladino, R., Hughes, A., et al. 2025, A&A, 697, A24

(ref: Belloche2013) Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013, A&A, 559, A47

(ref: Bendo2015) Bendo, G. J., Beswick, R. J., D’Cruze, M. J., et al. 2015, MNRAS, 450, L80

(ref: Boquien19) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: Bouvier2024) Bouvier, M., Viti, S., Behrens, E., et al. 2024, A&A, 689, A64

(ref: Bressan2012) Bressan, A., Marigo, P., Girardi, L., et al. 2012, MNRAS, 427, 127

(ref: Bressan02) Bressan, A., Silva, L., & Granato, G. L. 2002, A&A, 392, 377

(ref: Brunthaler2009) Brunthaler, A., Castangia, P., Tarchi, A., et al. 2009, A&A, 497, 103

(ref: Bruzual2003) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Bulatek2023) Bulatek, A., Ginsburg, A., Darling, J., Henkel, C., & Menten, K. M. 2023, ApJ, 956, 78

(ref: Butterworth2024) Butterworth, J., Viti, S., Van der Werf, P. P., et al. 2024, A&A, 686, A31

(ref: Calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Cardelli1989) Cardelli, J. A., Clayton, G. C., & Mathis, J. S. 1989, ApJ, 345, 245

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: CharlotFall2000) Charlot, S. & Fall, S. M. 2000, ApJ, 539, 718

(ref: ChenBressan2015) Chen, Y., Bressan, A., Girardi, L., et al. 2015, MNRAS, 452, 1068

(ref: Chevance2020b) Chevance, M., Kruijssen, J. M. D., Hygate, A. P. S., et al. 2020, MNRAS, 493, 2872

(ref: CidFernandes2005) Cid Fernandes, R., Mateus, A., Sodré, L., Stasińska, G., & Gomes, J. M. 2005, MNRAS, 358, 363

(ref: CidFernandes2013) Cid Fernandes, R., Pérez, E., Garcı́a Benito, R., et al. 2013, A&A, 557, A86

(ref: CidFernandes2010) Cid Fernandes, R., Stasińska, G., Schlickmann, M. S., et al. 2010, MNRAS, 403, 1036

(ref: ciesla2015) Ciesla, L., Charmandaris, V., Georgakakis, A., et al. 2015, A&A, 576, A10

(ref: Clemens10) Clemens, M. S., Scaife, A., Vega, O., & Bressan, A. 2010, MNRAS, 405, 887

(ref: Cohen2020) Cohen, D. P., Turner, J. L., & Consiglio, S. M. 2020, MNRAS, 493, 627

(ref: Condon91) Condon, J. J., Huang, Z. P., Yin, Q. F., & Thuan, T. X. 1991, ApJ, 378, 65

(ref: Conroy2013) Conroy, C. 2013a, ARA&A, 51, 393

(ref: Conroy13) Conroy, C. 2013b, ARA&A, 51, 393

(ref: Cunha08) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595

(ref: Dey2024) Dey, S., Goyal, A., Małek, K., & Dı́az-Santos, T. 2024, ApJ, 966, 61

(ref: Dey2022) Dey, S., Goyal, A., Małek, K., et al. 2022, ApJ, 938, 152

(ref: donevski23) Donevski, D., Damjanov, I., Nanni, A., et al. 2023, A&A, 678, A35

(ref: donevski20) Donevski, D., Lapi, A., Małek, K., et al. 2020, A&A, 644, A144

(ref: Draine2014) Draine, B. T., Aniano, G., Krause, O., et al. 2014, ApJ, 780, 172

(ref: Ellingsen2017) Ellingsen, S. P., Chen, X., Breen, S. L., & Qiao, H. H. 2017, MNRAS, 472, 604

(ref: Emig2020) Emig, K. L., Bolatto, A. D., Leroy, A. K., et al. 2020, ApJ, 903, 50

(ref: Fazio2004) Fazio, G. G., Hora, J. L., Allen, L. E., et al. 2004, ApJS, 154, 10

(ref: FernandezOntiveros2009) Fernández-Ontiveros, J. A., Prieto, M. A., & Acosta-Pulido, J. A. 2009, MNRAS, 392, L16

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: galliano19) Galliano, F., Galametz, M., & Jones, A. P. 2018, ARA&A, 56, 673

(ref: Galvin18) Galvin, T. J., Seymour, N., Marvil, J., et al. 2018, MNRAS, 474, 779

(ref: Gentile2024) Gentile, F., Talia, M., Daddi, E., et al. 2024, A&A, 687, A288

(ref: Giulietti2023) Giulietti, M., Lapi, A., Massardi, M., et al. 2023, ApJ, 943, 151

(ref: Gommers2022) Gommers, R., Virtanen, P., Haberland, M., et al. 2025, scipy/scipy: SciPy 1.15.2

(ref: Gorski2019) Gorski, M. D., Ott, J., Rand, R., et al. 2019, MNRAS, 483, 5434

(ref: Hamed2021) Hamed, M., Ciesla, L., Béthermin, M., et al. 2021, A&A, 646, A127

(ref: hamed2023a) Hamed, M., Małek, K., Buat, V., et al. 2023, A&A, 674, A99

(ref: Harada2022) Harada, N., Martı́n, S., Mangum, J. G., et al. 2022, ApJ, 938, 80

(ref: Harada2021) Harada, N., Martı́n, S., Mangum, J. G., et al. 2021, ApJ, 923, 24

(ref: Harada2024) Harada, N., Meier, D. S., Martı́n, S., et al. 2024, ApJS, 271, 38

(ref: HernandezGomez2019) Hernández-Gómez, A., Sahnoun, E., Caux, E., et al. 2019, MNRAS, 483, 2014

(ref: Herpich2024) Herpich, F. R., Almeida-Fernandes, F., Oliveira Schwarz, G. B., et al. 2024, A&A, 689, A249

(ref: hirashita23) Hirashita, H. & Chen, C.-C. 2023, MNRAS, 526, 4710

(ref: Holdship2022ApJ) Holdship, J., Mangum, J. G., Viti, S., et al. 2022, ApJ, 931, 89

(ref: Holdship2021) Holdship, J., Viti, S., Martı́n, S., et al. 2021, A&A, 654, A55

(ref: Hopkins2006) Hopkins, A. M. & Beacom, J. F. 2006, ApJ, 651, 142

(ref: Hopkins_mergers2010) Hopkins, P. F., Bundy, K., Croton, D., et al. 2010, ApJ, 715, 202

(ref: Huang2023) Huang, K. Y., Viti, S., Holdship, J., et al. 2023, A&A, 675, A151

(ref: Humire2022) Humire, P. K., Henkel, C., Hernández-Gómez, A., et al. 2022, A&A, 663, A33

(ref: Humire2024) Humire, P. K., Ortiz-León, G. N., Hernández-Gómez, A., et al. 2024, A&A, 688, L1

(ref: Humire2020b) Humire, P. K., Thiel, V., Henkel, C., et al. 2020, A&A, 642, A222

(ref: Iodice2014) Iodice, E., Arnaboldi, M., Rejkuba, M., et al. 2014, A&A, 567, A86

(ref: Kapinska2017) Kapińska, A. D., Staveley-Smith, L., Crocker, R., et al. 2017, ApJ, 838, 68

(ref: Kauffmann2003) Kauffmann, G., Heckman, T. M., Tremonti, C., et al. 2003, MNRAS, 346, 1055

(ref: Kellermann1969) Kellermann, K. I. & Pauliny-Toth, I. I. K. 1969, ApJL, 155, L71

(ref: Kennicutt1998) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: Kepley2011) Kepley, A. A., Chomiuk, L., Johnson, K. E., et al. 2011, ApJL, 739, L24

(ref: Kewley2001) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J. 2001, ApJ, 556, 121

(ref: Kewley2001a) Kewley, L. J., Heisler, C. A., Dopita, M. A., & Lumsden, S. 2001, The Astrophysical Journal Supplement Series, 132, 37

(ref: Kim2012) Kim, W.-T., Seo, W.-Y., & Kim, Y. 2012, ApJ, 758, 14

(ref: Kobayashi2020) Kobayashi, C., Karakas, A. I., & Lugaro, M. 2020, ApJ, 900, 179

(ref: Kobayashi2011) Kobayashi, C., Karakas, A. I., & Umeda, H. 2011, MNRAS, 414, 3231

(ref: kokorev21) Kokorev, V. I., Magdis, G. E., Davidzon, I., et al. 2021, ApJ, 921, 40

(ref: Krabbe2017) Krabbe, A. C., Rosa, D. A., Pastoriza, M. G., et al. 2017, MNRAS, 467, 27

(ref: Kruijssen2014) Kruijssen, J. M. D. & Longmore, S. N. 2014, MNRAS, 439, 3239

(ref: Lapi2020) Lapi, A., Pantoni, L., Boco, L., & Danese, L. 2020, ApJ, 897, 81

(ref: Lapi2018) Lapi, A., Pantoni, L., Zanisi, L., et al. 2018, ApJ, 857, 22

(ref: Leroy2015) Leroy, A. K., Bolatto, A. D., Ostriker, E. C., et al. 2015, ApJ, 801, 25

(ref: Li2024) Li, N. & Li, C. 2024, ApJ, 975, 234

(ref: LopesFernandez2016) López Fernández, R., Cid Fernandes, R., González Delgado, R. M., et al. 2016, Monthly Notices of the Royal Astronomical Society, 458, 184

(ref: Mangum2019) Mangum, J. G., Ginsburg, A. G., Henkel, C., et al. 2019, ApJ, 871, 170

(ref: markov25) Markov, V., Gallerani, S., Ferrara, A., et al. 2025, Nature Astronomy, 9, 458

(ref: Martin2021) Martı́n, S., Mangum, J. G., Harada, N., et al. 2021, A&A, 656, A46

(ref: paredes2023) Martı́nez-Paredes, M., Bruzual, G., Morisset, C., et al. 2023, MNRAS, 525, 2916

(ref: Meier2015) Meier, D. S., Walter, F., Bolatto, A. D., et al. 2015, ApJ, 801, 63

(ref: MendesdeOliveira2019) Mendes de Oliveira, C., Ribeiro, T., Schoenell, W., et al. 2019, MNRAS, 489, 241

(ref: Mueller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: MullerSanchez2010) Müller-Sánchez, F., González-Martı́n, O., Fernández-Ontiveros, J. A., Acosta-Pulido, J. A., & Prieto, M. A. 2010, ApJ, 716, 1166

(ref: Murphy11) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: nanni20) Nanni, A., Burgarella, D., Theulé, P., Côté, B., & Hirashita, H. 2020, A&A, 641, A168

(ref: narayanan25) Narayanan, D., Stark, D. P., Finkelstein, S. L., et al. 2025, ApJ, 982, 7

(ref: Osterbrock2006) Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of Gaseous Nebulae and Active Galactic Nuclei (Sausalito, CA: University Science Books)

(ref: palla24) Palla, M., De Looze, I., Relaño, M., et al. 2024, MNRAS, 528, 2407

(ref: Pantoni2019) Pantoni, L., Lapi, A., Massardi, M., Goswami, S., & Danese, L. 2019, ApJ, 880, 129

(ref: Pence1980) Pence, W. D. 1980, ApJ, 239, 54

(ref: PerezBeaupuits2018) Pérez-Beaupuits, J. P., Güsten, R., Harris, A., et al. 2018, ApJ, 860, 23

(ref: Pilbratt2010) Pilbratt, G. L., Riedinger, J. R., Passvogel, T., et al. 2010, A&A, 518, L1

(ref: Planck2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6

(ref: Poglitsch2010) Poglitsch, A., Waelkens, C., Geis, N., et al. 2010, A&A, 518, L2

(ref: Rekola2005) Rekola, R., Richer, M. G., McCall, M. L., et al. 2005, MNRAS, 361, 330

(ref: RicoVillas2020) Rico-Villas, F., Martı́n-Pintado, J., González-Alfonso, E., Martı́n, S., & Rivilla, V. M. 2020, MNRAS, 491, 4573

(ref: romano24) Romano, M., Donevski, D., Junais, et al. 2024, A&A, 683, L9

(ref: Ronconi2024) Ronconi, T., Lapi, A., Torsello, M., et al. 2024, A&A, 685, A161

(ref: Rosolowsky2006) Rosolowsky, E. & Leroy, A. 2006, PASP, 118, 590

(ref: Sakamoto2006) Sakamoto, K., Ho, P. T. P., Iono, D., et al. 2006, ApJ, 636, 685

(ref: Sakamoto2011) Sakamoto, K., Mao, R.-Q., Matsushita, S., et al. 2011, ApJ, 735, 19

(ref: salak24) Salak, D., Hashimoto, T., Inoue, A. K., et al. 2024, ApJ, 962, 1

(ref: Samir2020) Salim, S. & Narayanan, D. 2020, ARA&A, 58, 529

(ref: Salpeter1995) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: sawant25) Sawant, P., Nanni, A., Romano, M., et al. 2025, A&A, 694, A82

(ref: schneider24) Schneider, R. & Maiolino, R. 2024, A&ARv, 32, 2

(ref: Schreiber2018) Schreiber, C., Glazebrook, K., Nanayakkara, T., et al. 2018, A&A, 618, A85

(ref: Schwoerer2019) Schwörer, A., Sánchez-Monge, Á., Schilke, P., et al. 2019, A&A, 628, A6

(ref: Scoville2013) Scoville, N. & Murchikova, L. 2013, ApJ, 779, 75

(ref: sommovigo20) Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 497, 956

(ref: Stalevski2012) Stalevski, M., Fritz, J., Baes, M., Nakos, T., & Popović, L. Č. 2012, MNRAS, 420, 2756

(ref: Stalevski2016) Stalevski, M., Ricci, C., Ueda, Y., et al. 2016, MNRAS, 458, 2288

(ref: Stasinska2006) Stasińska, G., Cid Fernandes, R., Mateus, A., Sodré, L., & Asari, N. V. 2006, MNRAS, 371, 972

(ref: Stroe2015) Stroe, A., Oosterloo, T., Röttgering, H. J. A., et al. 2015, MNRAS, 452, 2731

(ref: Swinbank2010) Swinbank, A. M., Smail, I., Longmore, S., et al. 2010, Nature, 464, 733

(ref: Tanaka2024ApJ) Tanaka, K., Mangum, J. G., Viti, S., et al. 2024, ApJ, 961, 18

(ref: Turner_and_Ho1985) Turner, J. L. & Ho, P. T. P. 1985, ApJ, 299, L77

(ref: vanderTak2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: Vastel2015) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. M., & Boiziot, M. 2015, in SF2A-2015: Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313–316

(ref: Walmsley1989) Walmsley, C. 1989, in Interstellar Dust, ed. L. J. Allamandola & A. G. G. M. Tielens, Vol. 135, 263

(ref: Walter2017) Walter, F., Bolatto, A. D., Leroy, A. K., et al. 2017, ApJ, 835, 265

(ref: Wenger2000) Wenger, M., Ochsenbein, F., Egret, D., et al. 2000, A&AS, 143, 9

(ref: Werle2019) Werle, A., Cid Fernandes, R., Vale Asari, N., et al. 2019, MNRAS, 483, 2382

(ref: Wirstrom2010) Wirström, E. S., Bergman, P., Black, J. H., et al. 2010, A&A, 522, A19

(ref: witstok23) Witstok, J., Jones, G. C., Maiolino, R., Smit, R., & Schneider, R. 2023, MNRAS, 523, 3119

(ref: Xiang2022) Xiang, M. & Rix, H.-W. 2022, Nature, 603, 599

(ref: Yan2019) Yan, Y. T., Zhang, J. S., Henkel, C., et al. 2019, ApJ, 877, 154

(ref: Yang22) Yang, G., Boquien, M., Brandt, W. N., et al. 2022, ApJ, 927, 192

(ref: Zeng2020) Zeng, S., Zhang, Q., Jiménez-Serra, I., et al. 2020, MNRAS, 497, 4896

(ref: Zhao2023) Zhao, J. Y., Zhang, J. S., Wang, Y. X., et al. 2023, ApJS, 266, 29

# CIGALE SED modeling with AGN component

To assess potential AGN contributions, we incorporated the SKIRTOR module (cite: Stalevski2012; Stalevski2016). SKIRTOR is based on the 3D radiative transfer code SKIRT (cite: Baes2011). It includes obscuration by dusty torus and obscuration by dust settled along with the polar directions. The 2022.1 version of CIGALE offers significant advancements over its predecessors, particularly through its enhanced radio module, which includes both thermal (free-free emission from nebular gas) and nonthermal (synchrotron emission from star formation and AGN activity) contributions. The updated module also incorporates a new AGN component, enabling us to estimate the radio loudness, $R_{\rm{AGN}}$, defined as the ratio of AGN luminosities measured at 5 GHz and 2500Å. Additionally, it provides the slope of the AGN power-law (PL) radiation, which is assumed to be isotropic (cite: Yang22).\
CIGALE 2022.1 models the radio luminosities from star formation and AGN components using the FIR/radio correlation coefficient (q$_{\rm IR}$) and radio loudness (R$_{\rm AGN}$) parameters in scaling relations. At 1.4 GHz, the radio luminosity from star formation is predominantly nonthermal synchrotron emission, normalized using the q$_{\rm IR}$ parameter. The q$_{\rm IR}$ determines the normalization at this frequency, while a single power-law describes the synchrotron emission from star formation. Variations in the q$_{\rm IR}$ parameter contribute to uncertainties in modeling the radio component with CIGALE. The nonthermal synchrotron emission from the AGN is also described using a single PL form governed by the R$_{\rm AGN}$ parameter. However, the galaxy-averaged radio SEDs of starburst galaxies are rarely represented by single-PL models, showing low-frequency turnover due to free-free absorption (cite: Galvin18; Dey2022; Dey2024). It would be interesting to compare the physical conditions responsible for radio emission on the galaxy-wide scale to GMC scales, and that will be the aim of future studies using spatially-resolved radio SEDs of NGC 253. The list of input parameters to CIGALE analysis without and with AGN component is given in Table [\[tab:sedpar\]](#tab:sedpar). For the CIGALE modeling including the AGN component, we only added the AGN module to the existing input parameters. These CIGALE inputs have yielded a mean reduced $\chi^2$ of 2.2 for the ten GMCs studied in this work. The resulting SEDs are shown in Figs. [15](#apen.fig:cigalefitting) (without an AGN component) and [16](#apen.fig:cigalefitting_AGN) (considering an AGN component). These Figs. also include, in the bottom middle panel each, the SED fitting centered at GMC 5 at 9$\ensuremath{''}$ aperture diameter, which allows to include Herschel PACS observations (see Appendix [11](#apen.testing_at_9_arcsec)). The results on the main physical properties for each GMC are shown in Table [\[Tab.CIGALE_main_results\]](#Tab.CIGALE_main_results), those regarding attenuation effects are also in Table [\[Apen.Tab.Extinction_Factors_CIGALE\]](#Apen.Tab.Extinction_Factors_CIGALE) while additional results can be found in Tables [\[Apen.Tab.Modified_Parameters_CIGALE\]](#Apen.Tab.Modified_Parameters_CIGALE), and [\[Apen.Tab.CIGALE_AGN\]](#Apen.Tab.CIGALE_AGN).

+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| ***Parameters***                                                 |                          | ***Values***                                     |
+:=================================================================+:========================:+:================================================:+
| **delayed star formation history + additional burst** (cite: ciesla2015)                                                                       |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| e-folding time of the main stellar population model \[Myr\]      | $\tau_{\rm{main}}$       | 300-5000 by a bin of 300                         |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| e-folding time of the late starburst population model \[Myr\]    | $\tau_{\rm{burst}}$      | 50-500 by a bin of 50                            |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| mass fraction of the late burst population                       | $f_{\rm{burst}}$         | 0.01, 0.03, 0.05, 0.1, 0.3, 0.6, 0.9             |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Age of the main stellar population in the galaxy \[Myr\]         | age                      | 1000, 2000, 3000, 4500, 5000, 6500, 10000, 12000 |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Age of the late burst \[Myr\]                                    | age$_{\rm{burst}}$       | 10-350 by a bin of 50                            |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| **stellar synthesis population** (cite: Bruzual2003)                                                                                           |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Initial mass function                                            | IMF                      | (cite: Salpeter1995)                             |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Metallicity                                                      | $Z$                      | 0.02                                             |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Separation age                                                   |                          | 1 Myr                                            |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| **dust attenuation laws** (cite: Calzetti2000)                                                                                                 |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Colour excess of young stars                                     | E(B-V)                   | 0.1-2 by a bin of 0.2                            |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Reduction factor$^{(iii)}$                                       | $f_{\rm{att}}$           | 0.3, 0.44, 0.6, 0.7                              |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| **dust emission** (cite: Draine2014)                                                                                                           |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Mass fraction of PAH                                             | $q_{\rm{PAH}}$           | 0.47, 1.77, 2.50, 3.19, 4.58, 5.26, 6.63, 7.32   |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Minimum radiation field                                          | $U_{\rm{min}}$           | 0.4, 0.8, 1.2, 1.6, 2.0, 2.5, 4, 8, 15           |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| power law index of the radiation                                 | $\alpha$                 | 2                                                |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| fraction illuminated from $U_\mathrm{min}$ to $U_\mathrm{max}$   | $\gamma$                 | 0.02, 0.06, 0.1, 0.15, 0.2                       |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| **active nucleus model; Skirtor** (cite: Stalevski2012; Stalevski2016)                                                                         |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| optical depth at 9.7$~\mu$m                                      | $\tau_{9.7}$             | 3.0, 7.0                                         |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| torus density radial parameter                                   | pl                       | 1.0                                              |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| torus density angular parameter                                  | q                        | 1.0                                              |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| angle between the equatorial plan and edge of the torus \[deg\]  | oa                       | 40                                               |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| ratio of outer to inner radius                                   | R                        | 20                                               |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| fraction of total dust mass inside clumps \[%\]                  | Mcl                      | 97                                               |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| inclination (viewing angle) \[deg\]                              | i                        | 30 (type 1), 70 (type 2)                         |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| AGN fraction                                                     |                          | 0.0-0.4 by a bin of 0.05                         |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| extinction law of polar dust                                     |                          | SMC                                              |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| E(B-V) of polar dust                                             |                          | 0.01-0.7 by a bin of 0.5                         |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Temperature of the polar dust                                    | K                        | 100                                              |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Emissivity index of the polar dust                               |                          | 1.6                                              |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| **Radio**                                                                                                                                      |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| SF FIR/radio parameter$^*$                                       | $q_{\rm{IR}}$            | 1.3 - 2.9 by a bin of 0.5                        |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| SF Power-law slope (Flux $\propto$ Frequency$^{\alpha_{synch}}$) | $\alpha_{\rm{SF}}$       | $-$2.0 to $-$0.2 by a bin of 0.5                 |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| Radio-Loudness parameter$^{**}$                                  | $R_{\rm{AGN}}$           | 0.01, 0.05, 0.1, 0.5... 1000, 5000               |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+
| AGN Power-law slope                                              | $\alpha_{\rm{AGN}}$      | $-$2.0 to $-$0.2 by a bin of 0.5                 |
+------------------------------------------------------------------+--------------------------+--------------------------------------------------+

$^*$ computed as $\log_{10}L_{\rm{IR}(8-1000\mu\rm m)}$ -$\log_{10}L_{1.4\,\rm{GHz}}$, where $L_{1.4\,\rm{GHz}}$ is the radio luminosity at 1.4 GHz.\
$^{**}$ defined as a ratio of AGN luminosities measured at 5 GHz and 2500Å.

|  |  |  |
|:--:|:--:|:--:|
| ![image](./Figures/CIGALE/GMC1_best_model.pdf) | ![image](./Figures/CIGALE/GMC2_best_model.pdf) | ![image](./Figures/CIGALE/GMC3_best_model.pdf) |
| ![image](./Figures/CIGALE/GMC4_best_model.pdf) | ![image](./Figures/CIGALE/GMC5_best_model.pdf) | ![image](./Figures/CIGALE/GMC6_best_model.pdf) |
| ![image](./Figures/CIGALE/GMC7_best_model.pdf) | ![image](./Figures/CIGALE/GMC8_best_model.pdf) | ![image](./Figures/CIGALE/GMC9_best_model.pdf) |
| ![image](./Figures/CIGALE/GMC10_best_model.pdf) | ![image](./Figures/CIGALE/NGC253_noagn.pdf) |  |

|  |  |  |
|:--:|:--:|:--:|
| ![image](./Figures/CIGALE/cigale_agn/GMC1_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/GMC2_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/GMC3_best_model.pdf) |
| ![image](./Figures/CIGALE/cigale_agn/GMC4_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/GMC5_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/GMC6_best_model.pdf) |
| ![image](./Figures/CIGALE/cigale_agn/GMC7_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/GMC8_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/GMC9_best_model.pdf) |
| ![image](./Figures/CIGALE/cigale_agn/GMC10_best_model.pdf) | ![image](./Figures/CIGALE/cigale_agn/NGC253_agn.pdf) |  |

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| GMC | V_B90 | B_B90 | E_BV_factor | E_BV_lines | E_BVs |
|  | \[mag\] | \[mag\] | \[mag\] | \[mag\] | \[mag\] |
| 1 | $2.87 \pm 0.04$ | $3.58 \pm 0.05$ | $0.10 \pm 0.00$ | $7.00 \pm 0.09$ | $0.70 \pm 0.01$ |
| 2 | $3.00 \pm 0.17$ | $3.70 \pm 0.21$ | $0.33 \pm 0.33$ | $5.00 \pm 2.80$ | $0.73 \pm 0.05$ |
| 3 | $6.14 \pm 0.04$ | $6.20 \pm 0.02$ | $0.40 \pm 0.00$ | $3.00 \pm 0.00$ | $1.20 \pm 0.00$ |
| 4 | $6.10 \pm 0.01$ | $7.60 \pm 0.01$ | $0.45 \pm 0.09$ | $3.50 \pm 0.90$ | $1.50 \pm 0.00$ |
| 5 | $6.10 \pm 0.01$ | $7.60 \pm 0.01$ | $0.45 \pm 0.09$ | $3.50 \pm 0.90$ | $1.50 \pm 0.00$ |
| 6 | $4.90 \pm 0.01$ | $6.10 \pm 0.01$ | $0.40 \pm 0.00$ | $3.00 \pm 0.00$ | $1.20 \pm 0.00$ |
| 7 | $3.20 \pm 0.01$ | $4.00 \pm 0.01$ | $0.80 \pm 0.01$ | $1.00 \pm 0.05$ | $0.80 \pm 0.01$ |
| 8 | $3.00 \pm 0.17$ | $3.70 \pm 0.21$ | $0.29 \pm 0.31$ | $5.40 \pm 2.70$ | $0.73 \pm 0.04$ |
| 9 | $2.80 \pm 0.11$ | $3.50 \pm 0.14$ | $0.10 \pm 0.02$ | $7.00 \pm 0.34$ | $0.70 \pm 0.03$ |
| 10 | $2.90 \pm 0.03$ | $3.60 \pm 0.04$ | $0.10 \pm 0.05$ | $7.00 \pm 0.41$ | $0.70 \pm 0.01$ |

Table notes: The columns represent the GMC number, $A_{\rm{V}}^{\rm{Balmer}}$ as presented in Table [3](#tab:attenuation_comparison), the slope of the attenuation curve, the scaling factor between E(B-V) for lines and continuum, the color excess for nebular emission lines, and the color excess for the stellar continuum.

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| GMC | $M_{\rm dust}$ | U$_{\rm min}$ | $\gamma$ | $q_{\rm PAH}$ | age$_{\rm burst}$ | $f_{\rm burst}$ | $\tau_{\rm burst}$ | $\tau_{\rm main}$ |  |
|  | \[log$_{10}$ ($M_{\odot}$)\] |  |  |  | \[Myr\] |  | \[Myr\] | \[Myr\] |  |
| 1 | $4.47 \pm 0.09$ | $4.39 \pm 1.51$ | $0.025 \pm 0.033$ | $2.236 \pm 0.590$ | $7.87 \pm 99.45$ | $0.03 \pm 0.02$ | $142.23 \pm 85.13$ | $1170.23 \pm 645.23$ |  |
| 2 | $4.49 \pm 0.09$ | $3.06 \pm 1.84$ | $0.057 \pm 0.067$ | $4.821 \pm 1.218$ | $8.10 \pm 32.48$ | $0.02 \pm 0.01$ | $210.26 \pm 75.10$ | $290.93 \pm 141.61$ |  |
| 3 | $5.89 \pm 0.07$ | $3.25 \pm 0.72$ | $0.011 \pm 0.010$ | $1.118 \pm 0.036$ | $7.74 \pm 98.75$ | $0.03 \pm 0.02$ | $126.62 \pm 81.91$ | $864.58 \pm 527.05$ |  |
| 4 | $6.19 \pm 0.04$ | $0.68 \pm 0.16$ | $0.089 \pm 0.038$ | $0.470 \pm 0.001$ | $8.16 \pm 8.01$ | $0.01 \pm 0.00$ | $246.94 \pm 60.90$ | $203.13 \pm 30.50$ |  |
| 5 | $6.23 \pm 0.09$ | $0.90 \pm 0.39$ | $0.078 \pm 0.025$ | $0.471 \pm 0.026$ | $7.92 \pm 0.01$ | $0.01 \pm 0.02$ | $180.44 \pm 84.63$ | $213.33 \pm 61.83$ |  |
| 6 | $6.08 \pm 0.06$ | $0.58 \pm 0.34$ | $0.189 \pm 0.033$ | $1.036 \pm 0.312$ | $7.93 \pm 101.79$ | $0.03 \pm 0.02$ | $170.89 \pm 86.57$ | $1520.01 \pm 683.09$ |  |
| 7 | $5.13 \pm 0.11$ | $9.03 \pm 1.47$ | $0.192 \pm 0.029$ | $3.116 \pm 0.871$ | $7.68 \pm 93.06$ | $0.03 \pm 0.02$ | $134.24 \pm 83.65$ | $844.18 \pm 544.03$ |  |
| 8 | $4.79 \pm 0.21$ | $2.65 \pm 1.02$ | $0.160 \pm 0.053$ | $3.384 \pm 1.132$ | $7.75 \pm 88.29$ | $0.02 \pm 0.01$ | $176.04 \pm 86.66$ | $258.82 \pm 125.10$ |  |
| 9 | $4.73 \pm 0.23$ | $5.37 \pm 1.72$ | $0.012 \pm 0.014$ | $3.105 \pm 0.838$ | $7.71 \pm 93.91$ | $0.03 \pm 0.02$ | $137.08 \pm 83.70$ | $592.04 \pm 305.75$ |  |
| 10 | $4.83 \pm 0.19$ | $1.87 \pm 0.71$ | $0.051 \pm 0.042$ | $3.412 \pm 0.918$ | $7.82 \pm 103.06$ | $0.02 \pm 0.02$ | $170.82 \pm 86.23$ | $589.30 \pm 352.26$ |  |

Table notes: From left to right columns are: the GMC number, the dust mass ($M_{\rm dust}$), the minimum radiation field (U$_{\rm min}$), the fraction illuminated from U$_{\rm min}$ to the maximum radiation field ($\gamma$), the mass fraction of PAH ($q_{\rm PAH}$), the age of the late burst (age$_{\rm burst}$), the mass fraction of late burst population ($f_{\rm burst}$), the e-folding time of the late starburst population model ($\tau_{\rm burst}$) and that of the main stellar population model ($\tau_{\rm main}$).

|  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| GMC | $f_{\rm{AGN}}$ | accretion power | $L_{\rm disk}$ | polar dust luminosity | $R_{\rm AGN}$ | $\alpha_{\rm AGN}$ | $\alpha_{\rm SF}$ | $q_{\rm IR}$ |  |
|  | \[%\] | \[log$_{10}$ erg s$^{-1}$\] | \[log$_{10}$ erg s$^{-1}$\] | \[log$_{10}$ erg s$^{-1}$\] |  |  |  |  |  |
| 1 | $2.52 \pm 1.37$ | $32.70 \pm 0.24$ | $30.40 \pm 0.24$ | $31.97 \pm 0.24$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.56 \pm 0.11$ | $2.20 \pm 0.03$ |  |
| 2 | $3.86 \pm 2.56$ | $33.01 \pm 0.30$ | $30.70 \pm 0.31$ | $32.28 \pm 0.30$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.59 \pm 0.12$ | $2.20 \pm 0.00$ |  |
| 3 | $2.00 \pm 0.01$ | $34.01 \pm 0.02$ | $31.56 \pm 0.10$ | $33.28 \pm 0.02$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.51 \pm 0.04$ | $2.21 \pm 0.05$ |  |
| 4 | $2.05 \pm 0.46$ | $34.48 \pm 0.10$ | $32.01 \pm 0.10$ | $33.75 \pm 0.10$ | $0.01 \pm 0.01$ | $0.70 \pm 0.00$ | $0.50 \pm 0.00$ | $2.20 \pm 0.00$ |  |
| 5 | $5.34 \pm 1.48$ | $34.87 \pm 0.12$ | $32.40 \pm 0.12$ | $34.13 \pm 0.12$ | $0.01 \pm 0.01$ | $0.70 \pm 0.00$ | $0.50 \pm 0.00$ | $2.20 \pm 0.00$ |  |
| 6 | $4.66 \pm 2.68$ | $34.31 \pm 0.26$ | $31.92 \pm 0.24$ | $33.57 \pm 0.26$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.50 \pm 0.00$ | $2.20 \pm 0.01$ |  |
| 7 | $7.54 \pm 2.85$ | $33.79 \pm 0.18$ | $31.47 \pm 0.25$ | $33.06 \pm 0.18$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.69 \pm 0.11$ | $2.64 \pm 0.08$ |  |
| 8 | $2.56 \pm 1.54$ | $33.18 \pm 0.24$ | $30.85 \pm 0.25$ | $32.45 \pm 0.24$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.73 \pm 0.12$ | $2.22 \pm 0.09$ |  |
| 9 | $2.17 \pm 0.93$ | $32.95 \pm 0.14$ | $30.62 \pm 0.22$ | $32.22 \pm 0.14$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.79 \pm 0.11$ | $2.20 \pm 0.01$ |  |
| 10 | $2.51 \pm 1.42$ | $32.97 \pm 0.26$ | $30.64 \pm 0.25$ | $32.23 \pm 0.26$ | $0.04 \pm 0.04$ | $0.70 \pm 0.00$ | $0.50 \pm 0.00$ | $2.58 \pm 0.01$ |  |

Table notes: From left to right, the columns represents the GMC number, AGN fraction ($f_{\rm{AGN}}$), accretion power, disk luminosity ($L_{\rm disk}$), polar dust luminosity of AGN, radio loudness ($R_{\rm AGN}$), AGN power-law slope ($\alpha_{\rm AGN}$), SF power-law slope ($\alpha_{\rm SF}$), and radio-IR correlation parameter ($q_{\rm IR}$).

# Individual GMC properties

GMC 1: Located at the boundaries of the CMZ, where x$_{1}$/x$_{2}$ interactions are present, GMC 1 traces weak shocks at low-frequency transitions (cite: Humire2022; Harada2022; Huang2023) and strong shocks at high-$J$ frequency transitions. Indeed, the strongest SiO(5–4)/HNCO(10$_{0,10}-9_{0,9}$) ratios are observed at this position (cite: Humire2022). The whole picture may also be that weak and strong shocks are actually mixed over the entire CMZ (cite: Bao2024). The shocked environment results in some of the more prominent Class I methanol masers (MMCIs) in the $J_{-1}\rightarrow(J-$ 1)$_{0}-E$ and $J_{0}\rightarrow(J-$ 1)$_{1}-A$ line series (cite: Ellingsen2017; Gorski2019; Humire2022). Devoid of a strong continuum, but showing the strongest maser over LTE emission (cite: Humire2022), GMC 1 appears to be an extragalactic example of what is seen in the Milky Way object GMC G$+$0.693 (cite: Zeng2020). In line with the latter, this cloud possesses the lowest amount of dust and stellar masses in the sample, according to GalaPy (see Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy)).

Contrary to the others GMCs in our sample, GMC 1 is the only one whose SED fitting could also deliver ages of the order of 10$^{5}$ years. However, since we observe CO emission, a molecule that needs a few million years to be produced (cite: Walmsley1989), a permitted range of 10$^{6-11}$ or 10$^{6-12}$ years was imposed to all GMCs. This restriction yielded SED shapes that are closer to the observed ones compared to those with an age of $\sim$10$^{5}$ years, and significantly improved the results at millimeter and centimeter wavelengths by better reproducing the observed flux densities.

| GMC | $T_{\rm{MC}}$ | $M_{\rm{gas}}$ | ism.R_MC | $Z_{\rm{gas}}$ | sfh.psi_max | ism.f_MC | ism.tau_esc |
|:---|:---|:---|:---|:---|:---|:---|:---|
|  | \[K\] | \[log$_{10}$ ($M_{\odot}$)\] | \[log$_{10}$ (pc)\] | \[$\times 10^{-3}$\] | \[log$_{10}$ ($M_{\odot}$ yr$^{-1}$)\] |  | \[log$_{10}$ (yrs)\] |
| 1 | 50.365$_{-6.532}^{+11.259}$ | 8.573$_{-0.173}^{+0.095}$ | 0.90$_{-0.48}^{+0.60}$ | 0.53$_{-0.12}^{+0.27}$ | -1.69$_{-0.24}^{+0.23}$ | 0.01$_{-0.01}^{+0.01}$ | 7.75$_{-0.43}^{+0.34}$ |
| 2 | 67.295$_{-4.749}^{+6.536}$ | 7.126$_{-0.119}^{+0.129}$ | 1.02$_{-0.13}^{+0.13}$ | 4.11$_{-0.16}^{+0.20}$ | -1.67$_{-0.06}^{+0.07}$ | 0.02$_{-0.01}^{+0.01}$ | 9.19$_{-0.26}^{+0.17}$ |
| 3 | 66.739$_{-6.464}^{+7.394}$ | 8.010$_{-0.439}^{+0.260}$ | 0.79$_{-0.18}^{+0.20}$ | 8.77$_{-0.94}^{+2.50}$ | -0.54$_{-0.17}^{+0.38}$ | 0.04$_{-0.02}^{+0.09}$ | 8.83$_{-1.96}^{+0.29}$ |
| 4 | 61.899$_{-10.657}^{+22.586}$ | 6.925$_{-0.124}^{+0.135}$ | 1.27$_{-0.40}^{+0.41}$ | 25.38$_{-2.09}^{+3.44}$ | 1.15$_{-0.14}^{+0.22}$ | 0.43$_{-0.23}^{+0.13}$ | 7.98$_{-0.45}^{+0.25}$ |
| 5 | 54.833$_{-5.765}^{+6.791}$ | 7.386$_{-0.134}^{+0.133}$ | 1.60$_{-0.35}^{+0.28}$ | 21.14$_{-1.45}^{+1.57}$ | 0.84$_{-0.12}^{+0.12}$ | 0.20$_{-0.10}^{+0.17}$ | 6.98$_{-0.68}^{+0.71}$ |
| 6 | 35.814$_{-5.174}^{+13.118}$ | 7.441$_{-0.121}^{+0.095}$ | 1.53$_{-0.60}^{+0.34}$ | 14.70$_{-1.08}^{+1.09}$ | 0.26$_{-0.12}^{+0.11}$ | 0.35$_{-0.12}^{+0.13}$ | 6.18$_{-0.13}^{+0.40}$ |
| 7 | 40.327$_{-7.569}^{+10.562}$ | 6.833$_{-0.164}^{+0.288}$ | 1.41$_{-0.51}^{+0.37}$ | 8.77$_{-1.32}^{+1.00}$ | -0.54$_{-0.25}^{+0.17}$ | 0.38$_{-0.19}^{+0.16}$ | 7.64$_{-1.39}^{+1.10}$ |
| 8 | 59.476$_{-2.716}^{+3.305}$ | 7.320$_{-0.163}^{+0.147}$ | 1.05$_{-0.11}^{+0.13}$ | 3.04$_{-0.32}^{+0.41}$ | -0.51$_{-0.09}^{+0.10}$ | 0.02$_{-0.01}^{+0.01}$ | 8.12$_{-0.28}^{+0.25}$ |
| 9 | 64.423$_{-8.143}^{+16.924}$ | 7.079$_{-0.175}^{+0.234}$ | 0.54$_{-0.33}^{+0.38}$ | 4.77$_{-0.54}^{+0.65}$ | -1.45$_{-0.18}^{+0.19}$ | 0.04$_{-0.02}^{+0.03}$ | 9.22$_{-0.15}^{+0.12}$ |
| 10 | 41.421$_{-2.957}^{+3.811}$ | 7.250$_{-0.247}^{+0.213}$ | 1.53$_{-0.65}^{+0.31}$ | 3.48$_{-0.31}^{+0.37}$ | -1.92$_{-0.14}^{+0.15}$ | 0.11$_{-0.05}^{+0.09}$ | 9.02$_{-0.56}^{+0.40}$ |

Table notes: From left to right columns are: selected GMC, the molecular cloud (MC) temperature ($T_{\rm{MC}}$) obtained from a gray body fit, the MC radius (ism.R_MC), the gas metallicity ($Z_{\rm{gas}}$), the maximum SFR, which happens at certain time ism.tau_esc, known as the characteristic timescale (last column). The previous to last column corresponds to MC’s fraction into the ISM (ism.f_MC). For main SF related parameters, see Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy).

| GMC | $T_{\rm{DD}}$ | $M_{\rm{dust}}$ | ism.Rdust | ism.f_PAH | noise.f_cal | $\chi^{2}_{red}$ |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
|  | \[K\] | \[log$_{10}$ ($M_{\odot}$)\] | \[log$_{10}$ (pc)\] |  |  |  |  |  |  |
| 1 | 34.643$_{-3.512}^{+2.957}$ | 4.410$_{-0.195}^{+0.210}$ | 1.08$_{-0.09}^{+0.10}$ | 0.17$_{-0.06}^{+0.10}$ | -0.64$_{-0.11}^{+0.11}$ | 2.27 |  |  |  |
| 2 | 33.528$_{-2.875}^{+4.437}$ | 4.435$_{-0.105}^{+0.115}$ | 1.08$_{-0.07}^{+0.07}$ | 0.32$_{-0.07}^{+0.06}$ | -2.25$_{-0.14}^{+0.14}$ | 1.80 |  |  |  |
| 3 | 34.110$_{-3.781}^{+14.707}$ | 5.766$_{-0.315}^{+0.204}$ | 1.64$_{-0.20}^{+0.11}$ | 0.12$_{-0.07}^{+0.04}$ | -0.61$_{-0.06}^{+0.07}$ | 1.47 |  |  |  |
| 4 | 84.532$_{-12.551}^{+6.791}$ | 5.195$_{-0.108}^{+0.153}$ | 1.17$_{-0.08}^{+0.15}$ | 0.04$_{-0.02}^{+0.02}$ | -0.55$_{-0.07}^{+0.07}$ | 1.32 |  |  |  |
| 5 | 67.929$_{-3.896}^{+4.023}$ | 5.566$_{-0.107}^{+0.133}$ | 1.43$_{-0.09}^{+0.08}$ | 0.03$_{-0.01}^{+0.02}$ | -0.62$_{-0.08}^{+0.08}$ | 1.14 |  |  |  |
| 6 | 63.318$_{-2.800}^{+3.233}$ | 5.453$_{-0.102}^{+0.079}$ | 1.35$_{-0.08}^{+0.06}$ | 0.04$_{-0.01}^{+0.01}$ | -0.73$_{-0.08}^{+0.10}$ | 1.35 |  |  |  |
| 7 | 62.911$_{-10.806}^{+4.631}$ | 4.474$_{-0.135}^{+0.145}$ | 1.08$_{-0.10}^{+0.12}$ | 0.06$_{-0.03}^{+0.02}$ | -0.94$_{-0.09}^{+0.10}$ | 1.38 |  |  |  |
| 8 | 41.419$_{-2.629}^{+4.510}$ | 4.492$_{-0.127}^{+0.147}$ | 1.21$_{-0.09}^{+0.08}$ | 0.17$_{-0.05}^{+0.07}$ | -1.38$_{-0.10}^{+0.11}$ | 1.35 |  |  |  |
| 9 | 43.383$_{-4.396}^{+5.060}$ | 4.679$_{-0.124}^{+0.133}$ | 1.17$_{-0.09}^{+0.08}$ | 0.15$_{-0.04}^{+0.07}$ | -1.11$_{-0.08}^{+0.09}$ | 1.29 |  |  |  |
| 10 | 41.532$_{-3.377}^{+5.290}$ | 4.574$_{-0.117}^{+0.128}$ | 1.20$_{-0.08}^{+0.08}$ | 0.19$_{-0.05}^{+0.06}$ | -1.25$_{-0.09}^{+0.10}$ | 1.31 |  |  |  |

Table notes: From left to right, the columns represent the GMC number, the temperature diffuse dust (DD) temperature ($T_{\rm{DD}}$), the dust mass ($M_{\rm{dust}}$), the radius of the DD region (ism.Rdust), the fraction of the total emission from DD contributed by PAH (ism.f_PAH), the calibration error (noise.f_cal) which can introduce up to 30% uncertainties in the photometric points, accounting for observation uncertainties while effectively relaxing the constraints on the parameter space and allowing for a broader range of possible solutions. The last column is the the reduced $\chi^{2}$ computed at the best-fitting values of parameters. For main SF related parameters, see Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy).

GMC 2: This molecular cloud also overlaps with x$_{1}$/x$_{2}$ interactions and presents physical and chemical conditions that are similar to GMC 1, although GMC 2 is more massive in terms of stellar and dust mass (Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy); see also (cite: Humire2022) and (cite: Bouvier2024)), older (Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy)), and shows weaker MMCIs exclusively in the $J_{-1}\rightarrow(J-$ 1)$_{0}-E$ family (cite: Humire2022). With slightly lower values than GMC 1, GMc 2 presents the lowest dusty radius, as calculated by GalaPy, and the lowest stellar mass, according to STARLIGHT, as indicated in Tables [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy) and [\[Tab.STARLGIGHT_results\]](#Tab.STARLGIGHT_results), respectively.

GMC 3 appears to be the source of the stellar outflow best viewed by high-density tracers such as CN, HCN (cite: Walter2017), or an increment in the CO/$^{13}$CO $J=$1–0 ratios owed to a more transparent environment (cite: Bao2024). Although dense molecular gas possess a velocity dispersion of $\sim$40 km s$^{-1}$ in the streamer (cite: Walter2017), the stellar velocity dispersion is the lowest among the sample (see Table [\[Tab.STARLGIGHT_results\]](#Tab.STARLGIGHT_results)) at the GMC position. This corresponds to the depiction of cold/low-dispersion gas actively producing stars at the convergence of the ring and the bar, as observed in M 100 (cite: Allard2005). A more evolved and therefore, more easily observed stellar stream is in line with this position being the oldest among the nuclear regions, as deduced from our SED fitting in Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy). In the same table, and also in Figure[4](#Fig.Mstar_vs_Mdust), it can be seen than GMC 3 presents the largest dust reservoir and extension.

GMC 4 exhibits the highest SiO(2–1)/HNCO(4$_{0,4}-3_{0,3}$) ratio in the sample (cite: Meier2015; Humire2022), indicative of strong shocks. It is also the second youngest molecular cloud in the sample according to GalaPy and the youngest according to STARLIGHT fits, respectively (see Table [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy) and Figs. [6](#Fig.SFHs) and [22](#fig.stellar_ages_GalaPy_STARLIGHT_CIGALE)). From CIGALE and GalaPy, it also possess the second largest SFR. This intense stellar formation, despite the absence of a distinct molecular stellar streamer, may be a consequence of its youthful nature or simply that radio emission is not strong enough to trace it (although the stellar streamers originating from the central GMCs is clearly seen in H$\alpha$; see second to last upper panel of Fig. [1](#Fig.summary_plot)). Additionally, and from GalaPy’s results, GMC 4 has the largest $M_{\rm{dust}}/M_{\rm{gas}}$ ratio in the sample ($\log_{10} \left( \frac{M_{\rm{dust}}}{M_{\rm{gas}}} \right) = -1.730$; see Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy)), which could suggest that material is being rapidly funneled toward the nucleus via the bar. Similarly, GMCs 5 and 6 are also among the youngest in the sample, with the second and third largest dust-to-gas mass ratios ($\log_{10} \left( \frac{M_{\rm{dust}}}{M_{\rm{gas}}} \right) = -1.820$ and -1.988, respectively). A possible explanation is that material is being concentrated in these GMCs due to inner-inner Lindblad resonances caused by the nuclear bar (cite: Anantharamaiah1996; Cohen2020). Indeed, looking at the left panel of Fig. 11 in (cite: Humire2022), and after considering our 3$\ensuremath{''}$ photometric aperture and modified GMC positions, we can clearly see a peak in the SiO(2–1)/HNCO(4$_{0,4}-3_{0,3}$) ratios around GMC 5, this latter showing a gap due to SiO(2–1) self-absorption.

Our mid-IR data from NACO and VISIR at the VLT show the highest fluxes in the sample at this position (see Fig. [3](#fig.SEDs)). GMCs 2 and 4 are the only giant molecular clouds where 10–36% of the stellar mass was produced in the last $\sim$2 million years. In contrast, the bulk of stellar mass in the remaining GMCs was produced approximately 1 to 10 billion years ago (see Fig. [6](#Fig.SFHs)).

GMC 5: Among our sample, GMC 5 has the best signal across the different wavelengths, being the most clearly observed at centimeter wavelengths, with its emission covering almost the entire aperture. It is closest to the strongest radio continuum source, TH2 (cite: Turner_and_Ho1985), which also produces some (self-)absorption features in methanol (cite: Humire2022), in contrast to the outermost GMCs, where methanol absorption is primarily attributed to anti-inversion against the cosmic microwave background (CMB; (cite: Bulatek2023)). The strong continuum emission also leads to self-absorption in other molecules, such as SiO $J$=2–1, as inferred from (cite: Humire2022), although this has not been investigated in detail. According to GalaPy and CIGALE results, GMC 5 exhibits by far the largest instantaneous and time-averaged (over 10 and 100 Myr) SFRs in our sample ($\sim$0.7 and 0.2$M_{\odot}$ yr$^{-1}$, according to GalaPy and CIGALE, respectively; see Tables [\[Tab.star_formation_results_GalaPy\]](#Tab.star_formation_results_GalaPy) and [\[Tab.CIGALE_main_results\]](#Tab.CIGALE_main_results)), creating about three times more stars than GMC 4, which shows the closest characteristics among the ten GMCs studied.

GMC 6: Most species peak at this location, including CO isotopologues (cite: Harada2024). Clear exceptions are the sub-mm continuum emissions at Bands 3-7, RRLs, CN, HCN, and CO ($J=$2–1, and $J=$3–2), whose emission is strongest in GMC 5. It shows the highest column densities in both methanol symmetric types and presents the second highest SiO(2–1)/HNCO(4$_{0,4}-3_{0,3}$) ratios after GMC 4, indicative of a strongly perturbed environment due to the presence of strong shocks (cite: Meier2015; Humire2022; Huang2023).

GMC 7 hosts the strongest methanol emission at 84.53 and 132.89 GHz, which is enhanced by maser emission. It also presents the strongest difference between E- and A-CH$_{3}$OH from a single LTE component analysis, with a E/A ratio of 3.16$^{+0.17}_{-0.18}$, which can only be related to shocks since theoretical values are not expected to surpass 1.0, unless methanol is not formed from CO on cold grain surfaces in NGC 253 (cite: Wirstrom2010). We note that E/A ratios of up to 6.0 have been seen in massive star-forming regions in our galaxy (cite: Zhao2023).

GMC 8: Using a two-component LTE analysis, this GMC shows one of the largest E/A-CH$_{3}$OH ratios in the cold layer (3.14$\pm$0.58). This may be due to low temperatures, where E-CH$_{3}$OH is more populated as their upper level energies ($E_{\rm{up}}$) are in general lower than its A-CH$_{3}$OH counterparts (cite: Humire2022; Humire2024). The above is in line with cold dust emission increments, as can be inferred from enhanced $~$100 GHz continuum emission, in contrast to its spurious signal in GMCs 1 and 2, as accounted for in our Fig. [2](#Fig.Cont_maps_ALCHEMI). A similar conclusion can also be obtained from the distribution of sulfurated molecules seen in ALMA Band 3 (84–116 GHz), whose emission is also enhanced toward the northeast segment of NGC 253’s CMZ (cite: Meier2015).

GMC 9 presents a mild stellar velocity dispersion ($\sigma_{\bigstar}$; see Table [\[Tab.STARLGIGHT_results\]](#Tab.STARLGIGHT_results)) that may account for a relative low formation of stars (cite: Allard2006) and be a result of its position in between the spiral arms and the inner bar, where (x$_{1}$/x$_{2}$) interactions and inner Lindblad resonances take place (see dashed gray ellipses in Fig. [2](#Fig.Cont_maps_ALCHEMI)). A similar origin for the velocity dispersion can be inferred for GMCs 1, 2, and 8–9, in contrast to the larger $\sigma_{\bigstar}$ measured at GMCs 3, 5, 6, and 7, that are possibly due to a vigorous stellar formation instead (cite: Bouvier2024; Bao2024).

GMC 10: We do not see much high-excitation methanol lines in this region, that shows the lowest excitation temperatures and number of methanol lines, in addition to the lowest column density and line-widths (FWHM $\sim$23 km s$^{-1}$) of both methanol symmetric types among the ten GMCs studied in this work. Using high density sulfured molecules, (cite: Bouvier2024) also determined the lowest line-widths (FWHM $\sim$20 km s$^{-1}$) and rest velocities (100–150 km s$^{-1}$) among the GMCs in the sample.

# Sulfur ratios and Age-metallicity relation in GMC 5

While many simple abundant molecules are prone to undergo strong opacity effects, impeding a confident derivation of line ratios, isotopologues of less abundant elements are normally optically thin. Moreover, line ratios can be used to derive metallicities such as \[Fe/H\], defined concerning the Solar metallicity by the following relation: $$\begin{equation}
    [\rm{Fe/H}] = log_{10}([N_{\rm{Fe}/N_{\rm{H}}}])_{\rm{star}} - log_{10}([N_{Fe}/N_{\rm{H}}])_{\rm{Sun}}.
\end{equation}$$

One way to obtain \[Fe/H\] through optically thin molecules is using the relation in Table 3 of (cite: Kobayashi2011), well defined across the -0.5$\leq$\[Fe/H\]$\leq$0.0 range:

$$\begin{equation}
    \frac{\it{N}\rm{(^{32}S})}{\it{N}\rm{(^{34}S)}} = -19.8\times [\rm{Fe/H}]+23.2.
\label{eq.Kabayashi11}
\end{equation}$$

This equation relates the column densities, $N$, of sulfur isotopologues with the metallicities. With the purpose of obtaining the required column density ratio, we employed the $^{13}$CS and $^{13}$C$^{34}$S isotopologues, of which $^{13}$C$^{34}$S is only detectable in GMC 5 from our sub-mm data. Within the ALCHEMI frequency coverage (84.4–373.3 GHz), $^{13}$C$^{34}$S is always close but not fully blended with HC$_{3}$N (see Fig. [19](#Fig.13CS_and_13C34S_LTE_modeling), bottom panels). Its transitions at $J_{u}=$2 to 8, when present, fall $\sim$160 km s$^{-1}$ away (redshifed) from HC$_{3}$N at $J_{u}=$2$x$ to 8$x$, with $x$ being equal to 5 and $J_{u}$ being always the unity above the lower $J$; for example $J_{u}=4$ being equal to the $J=$4–3 transition.

Assuming LTE conditions, we fitted the observed spectra with a single component to account for the very dense regions that CS isotopologues trace. To this end, we employed the Centre d’Analyse Scientifique de Spectres Instrumentaux et Synthétiques (CASSIS), a software developed by CESR/IRAP[^10] (cite: Vastel2015) and designed for the analysis and synthesis of molecular spectra in astrophysical research. It enables spectral modeling, line identification, and data interpretation for astronomical observations, with the capability of performing both local thermodynamic equilibrium (LTE) and non-LTE modeling. When performing non-LTE modeling, CASSIS functions as a wrapper for the RADEX code (cite: vanderTak2007), facilitating its utilization for users. CASSIS is not restricted to the radio regime (cite: HernandezGomez2019) as it has also been used to distinguish between LTE and non-LTE emission, enabling the discovery of new maser transitions (cite: Humire2024). While originally designed to process single spectra, the code can be adapted to handle data cubes (cite: Harada2022)

To produce the synthetic spectrum that better reproduces the CS-related lines, we have utilized the Cologne Database for Molecular Spectroscopy (cite: Mueller2005) for spectroscopic data and restricted to LTE conditions, since these molecules are expected to trace dense gas. Our best-results are shown in Fig. [19](#Fig.13CS_and_13C34S_LTE_modeling).

This way, we obtained different solutions ranging from $^{32}$S/$^{34}$S rates much lower than expected in the Milky Way ($\sim$5) to more reasonable values ($\sim$17). We also find that the line intensities can be reproduced under a large range of excitation temperatures. Due to this degeneracy, we decided to limit the $^{32}$S/$^{34}$S range to values fulfilling the criterion: \[Fe/H\]$\leq$0.5, motivated by the metallicity values obtained from a sample of $\sim$247,000 sub-giant stars in the Milky Way (see (cite: Xiang2022) and Fig. [20](#Fig.MAR)). This way, we expect $^{32}$S/$^{34}$S isotopologue ratios no lower than 13.3, namely, within the range of values measured in most of the galaxy (cite: Humire2020b). Considering that Sgr B2(N) shows properties comparable to a mini-starburst system (cite: Belloche2013; Schwoerer2019), and that the best $^{32}$S/$^{34}$S column density ratio measured there is 16.3$^{+2.1}_{-1.7}$ (cite: Humire2020b), our assumption of $^{32}$S/$^{34}$S$\geq$13.3 is well justified.

Our best-fit LTE modeling parameters from the spectra of $^{13}$CS and $^{13}$C$^{34}$S are presented in Table [4](#tab.best_fit_sulfur_isotopologues). The resulting $^{32}$S/$^{34}$S column density ratio is 14.26$^{7.53}_{-4.72}$, and we set it to be 14.26$^{7.53}_{-0.96}$ considering our lowest threshold. Using Eq. [\[eq.Kabayashi11\]](#eq.Kabayashi11), the resulting \[Fe/H\] metallicity values are 0.45$^{+0.05}_{-0.38}$, namely, between 0.07 and 0.5. Comparing this latter result with the age-metallicity relation presented in Fig. 2a of (cite: Xiang2022), reproduced in the left panel of Fig. [20](#Fig.MAR), we can estimate an age range. To this aim, we utilized a skewed Gaussian distribution model due to the uni-modal and asymmetric distribution of ages within our estimated metallicity range, as can be seen in the right panel of Fig. [20](#Fig.MAR). The fitting process involved optimizing the parameters of the skewed Gaussian function, including amplitude $A$, mean $\mu$, standard deviation $\sigma$, and skewness $\alpha$, using a least-squares approach. The skewed Gaussian distribution function is defined as: $$\begin{equation}
f(x) = \frac{A}{\sigma \sqrt{\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}} \left(1 + \text{erf}\left(\alpha \frac{x - \mu}{\sigma \sqrt{2}}\right)\right),
\end{equation}$$ where the error function, $\text{erf}(z)$, is defined as: $$\begin{equation}
\text{erf}(z) = \frac{2}{\sqrt{\pi}} \int_0^z e^{-t^2} \, dt.
\end{equation}$$ Our analysis revealed a negative skewness parameter $\alpha$, indicating a non-symmetric age distribution with a higher density toward young ($\sim$2.5–7.5 Gyr) sub-giant stars, withing the age-metallicity relation distribution used here (Fig. [20](#Fig.MAR)). The resulting estimated age, namely, the distribution peak and its FWHM, is 7.85$^{+0.18}_{-5.39}$ Gyrs, reflecting a stellar population 31 times older than the one traced by our SED fitting in GMC 5, summarized in Table [\[Tab.SED_outputs_GalaPy\]](#Tab.SED_outputs_GalaPy), whose value is of 10$^{8.40}$ or $\sim$251 Myr.

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
| Species | $N$(Sp) | $T_{\rm ex}$ | FWHM | $V_{\rm LSR}$ | Size |
|  | \[$\times$10$^{14}$cm$^{-2}$\] | \[K\] | \[km s$^{-1}$\] | \[km s$^{-1}$\] | \[$\ensuremath{''}$\] |
|  |  |  |  |  |  |
| $^{13}$CS | 29.67$^{+4.12}_{-9.63}$ | 36.17$^{+46.95}_{-10.14}$ | 83.87$^{+86.64}_{-22.81}$ | 198.89$^{+39.20}_{-12.99}$ | 1.08$^{+1.91}_{-0.25}$ |
| $^{13}$C$^{34}$S | 2.08$^{+0.02}_{-0.53}$ | 60.97$^{+101.06}_{-23.88}$ | 39.83$^{+0.16}_{-14.66}$ | 195.00$^{+1.00}_{-1.00}$ | 2.93$^{+0.07}_{-1.96}$ |
|  |  |  |  |  |  |

: Best fit parameters from our LTE plus non-LTE modeling for CARMA-7.

Table notes: Best-fitting parameters obtained through our LTE modeling of sulfur isotopologues. From left to right columns correspond to: Name of the species, $N$(Sp) stands for column density of species, $T_{\rm{ex}}$ is the excitation temperature, the line-width measured from its FWHM, the local standard of rest velocity, $V_{\rm{LSR}}$, and the best-fit source size in arcseconds. Uncertainties correspond to a 3$\sigma$ level.

Although magnetohydrodynamic models for sulfur may not yet be well constrained for the bulge of galaxies, the most likely explanation for sulfur ratios in the very center of our Milky Way is that its large-scale bar is funneling material from its edges toward the galaxy’s nucleus or bulge (cite: Humire2020b). Following this reasoning, the $^{32}$S/$^{34}$S abundances can still be modeled according to (cite: Kobayashi2011) (C. Kobayashi, priv. comm.), by assuming that the origin of $^{32}$S/$^{34}$S abundances occurs at a certain level in the disk of galaxies.

In a more recent paper, (cite: Kobayashi2020) presented an updated version of their age-metallicity relation (their Fig. 2b), which, as the SFH models used in GalaPy and CIGALE, also considers a single burst in its SFH model. This updated model integrates a bulge outflow component that is more suited for the NGC 253 central molecular zone (CMZ), where stars drive material outside the bar through significant stellar outflows, likely originating from supernovae. Applying the 0.0–0.5 iron metallicity range to the bulge outflow model yields ages starting from one Gyr, while the bulge component alone provides a more restricted range of one to five Gyr, peaking at 3 Gyr (or 10$^{9.48}$ years). Both results are in good agreement with the AMR-derived estimations.

The discrepancy arises because metallicities measured by molecular emitters provide a broader perspective, reflecting the average contributions of all stellar populations that have expelled material to the interstellar medium (ISM). In contrast, values derived from SED fitting are predominantly influenced by recent star formation, which emits most of its radiation in the mid-infrared (MIR; 1.5–50$\mu$m). Consequently, we anticipate deriving an average age estimate from the sub-millimeter regime and a younger age estimate from SED fitting. Additionally, employing molecular tracers at higher vibrational modes ($v=1$ or 2) and angular resolutions allows for tracing the youngest stellar population nicely tracing the last burst in the light-weighted SFHs of Fig. [6](#Fig.SFHs), representing up to 43% of the total stellar light emitted in the optical regime (see dashed blue vertical lines in Fig. [6](#Fig.SFHs)) (cite: RicoVillas2020; Butterworth2024).

However, it might be that the MIR emission we account for in the SED fitting mainly originates from low-mass/old stellar populations. If that is the case, we do not have a clear answer for this discrepancy.

![image](Figures/13CS_specfit_bigger.pdf)

![image](Figures/13C34S_specfit_bigger.pdf)

![](Figures/fitted_skewed_gaussian_bigger_dip400.png)

# Comparison among different methodologies

Given the different SED modeling approaches, that differ in terms of star formation histories and several other assumptions, here we provide a few comparison plots. Depending directly on the SED shape, we will obtain a sSFR (cite: Conroy13). Then, each model assumes a certain mass-to-light ratio to derive the stellar mass and a specific SFH to derive the stellar ages, combining both results, mass and time, to obtain the SFR. Given the variation between GalaPy and CIGALE modeled SED shapes, as seen in Fig. [3](#fig.SEDs), we expect dispersion in their resulting sSFRs, but a relative tendency to be a one-to-one relation. Such a tendency is seen in the bottom right panel of our Fig. [21](#fig:comparison_grid), whose values are listed in Table [5](#tab:sSFR_comparison), meaning that, at this level of comparison, both codes share similarities. From that same Figure it can be noted that GalaPy tends to produce larger SFRs and stellar masses, as also previously noted by (cite: Ronconi2024). The dust mass is mostly consistent between the GalaPy and CIGALE models within 1$\sigma$ uncertainties for the less massive GMCs but systematically shifts toward the lower values of CIGALE compared to the higher values of GalaPy, as evidenced by the 1:1 red line in the bottom left panel of Fig. [21](#fig:comparison_grid). This trend becomes more pronounced in the more nuclear and massive regions, specifically GMCs 4–6 and also GMC 7.

|         |                        |                        |
|:--------|:----------------------:|:----------------------:|
| **GMC** |   **sSFR (GalaPy)**    |   **sSFR (CIGALE)**    |
|         | \[log$_{10}$ $^{-1}$\] | \[log$_{10}$ $^{-1}$\] |
| 1       |    $-8.84 \pm 0.09$    |    $-9.38 \pm 0.07$    |
| 2       |    $-9.63 \pm 0.05$    |    $-9.68 \pm 0.05$    |
| 3       |    $-9.63 \pm 0.05$    |    $-9.40 \pm 0.11$    |
| 4       |    $-9.41 \pm 0.04$    |    $-9.69 \pm 0.02$    |
| 5       |    $-8.81 \pm 0.04$    |    $-8.88 \pm 0.03$    |
| 6       |    $-9.33 \pm 0.04$    |    $-9.26 \pm 0.05$    |
| 7       |    $-9.81 \pm 0.04$    |    $-9.40 \pm 0.07$    |
| 8       |    $-9.80 \pm 0.04$    |    $-9.83 \pm 0.11$    |
| 9       |    $-9.80 \pm 0.05$    |    $-9.63 \pm 0.07$    |
| 10      |    $-9.88 \pm 0.09$    |    $-9.66 \pm 0.07$    |

: Specific star formation rates (sSFRs).

Table notes: Comparison of specific star formation rates (sSFRs) in log$_{10}$ scale derived from GalaPy and CIGALE in our ten selected GMCs.

In Fig. [22](#fig.stellar_ages_GalaPy_STARLIGHT_CIGALE), we compare the stellar population ages, burst ages, SF characteristic timescales, and ages weighted by light and mass, as provided by the different models utilized in this work. Specifically, CIGALE provides the main stellar population age, the late starburst age, the burst age, and the average age of the young and old stellar populations. From STARLIGHT, we include the averaged stellar ages weighted by light and by mass, which primarily correspond to the young and old stellar populations, respectively. Additionally, we present the stellar ages derived by GalaPy, along with the characteristic star-formation timescale, $\tau_{\star}$, obtained from the same code.

![](Figures/4plots_emcee_v3.pdf)

![](Figures/comparison_plot_plus_CIGALE_results_v2_bigger.pdf)

# Testing the FIR bump accuracy

We have performed an SED fitting with both GalaPy and CIGALE considering a 9$''$ aperture diameter to include Herschel PACS data in the far infrared. This approach ensures that the infrared bump more accentuated in GalaPy than in CIGALE models (see Fig. [3](#fig.SEDs) for a clear comparison) at around 100$\mu$m is properly fit without extrapolations. Additionally, it allows us to test whether our extrapolation was consistent with real observations, which cannot be verified at 3$\ensuremath{''}$ due to instrumental limitations. We found a similar dust temperature, which is a result driven by the FIR SED peak, in both cases, at 3 and 9$\ensuremath{''}$, as already pointed out in Sect. [5.1](#Sec.reliability_of_SED_fit_in_the_FIR). Overall, the SED model used in GalaPy for GMC 5 correlates well with the one derived for the larger 9$''$ aperture centered at the same GMC.

In contrast, while CIGALE models underpredict the FIR bump in several GMCs compared to GalaPy, incorporating Herschel photometric points at 70, 100, and 160$\mu$m enables the code to fit all SED points accurately, regardless of whether an AGN component is assumed. The 9$\ensuremath{''}$ SED fitting using CIGALE is shown in the bottom middle panel of Figs. [15](#apen.fig:cigalefitting) and [16](#apen.fig:cigalefitting_AGN) for the cases without and with an AGN component, respectively. Interestingly, the SFRs differ by less than 5% between these models, reaffirming that the presence of an AGN is irrelevant from the SED perspective, as previously discussed in Sect. [4.2.1](#subsec.WHAN_BPT).

Finally, the 3$\ensuremath{''}$ and 9$\ensuremath{''}$ SED models from GalaPy are shown in the right panel of Fig. [25](#fig.FIR_SEDs_attempts). The 3$\ensuremath{''}$ aperture SED corresponds to what was already presented in Fig. [3](#fig.SEDs) for GMC 5.

![image](Figures/nice_fig_v2_bigger.pdf)

![image](Figures/results_SED_combined_plus_Beck.pdf)

[^1]: The Strehl ratio (SR) is a measure of the quality of adaptive optics correction, indicating the ratio of the peak intensity of the observed point spread function to the ideal diffraction-limited one.

[^2]: <https://science.nrao.edu/facilities/vla/docs/manuals/oss2012B/performance/referencemanual-all-pages>

[^3]: <https://science.nrao.edu/facilities/vla/docs/manuals/oss/performance/resolution>

[^4]: <https://irsa.ipac.caltech.edu/data/SPITZER/Enhanced/SEIP/>

[^5]: <https://science.nrao.edu/facilities/vla/docs/manuals/oss2012B/performance>

[^6]: <https://casa.nrao.edu/index.shtml>

[^7]: according to the smaller array extension of the hybrid configuration, configuration C for this case

[^8]: <https://www.vla.nrao.edu/astro/nvas/>

[^9]: <https://galapy.readthedocs.io/en/latest/general/free_parameters.html>

[^10]: <http://cassis.irap.omp.eu/?page=cassis>

</paper>

Write the methods card for this paper.