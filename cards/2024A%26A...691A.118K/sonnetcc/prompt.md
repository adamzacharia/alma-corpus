# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...691A.118K\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024A&A...691A.118K",
 "title": "AGN feeding along a one-armed spiral in NGC 4593: A study using ALMA CO(2─1) observations",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Kianfar, K.",
 "n_authors": 12,
 "arxiv_id": "2410.09941",
 "doi": "10.1051/0004-6361/202451185",
 "alma_projects_linked_by_archive": [
  "2017.1.00236.S",
  "2018.1.00576.S"
 ]
}
```

Paper text:
<paper>
# AGN feeding along a one-armed spiral in NGC 4593

We investigate active galactic nuclei (AGN) feeding through the molecular gas (CO(2-1) emission) properties of the local Seyfert 1 galaxy NGC 4593, using Atacama Large Millimeter Array (ALMA) observations and other multi-wavelength data.

Our study aims to understand the interplay between the AGN and the interstellar medium (ISM) in this galaxy, examining the role of the AGN in steering gas dynamics within its host galaxy, evaluating the energy injected into the ISM, and determining whether gas is inflowing or outflowing from the galaxy.

After reducing the ALMA CO(2-1) images, we employed two models, 3D-BAROLO and DISCFIT, to construct a disc model and fit its emission to the ALMA data. Additionally, we used photometric data to build a spectral energy distribution (SED) and apply the CIGALE code to derive key physical properties of the AGN and its host.

Our analysis reveals a complex interplay within NGC 4593, including a clear rotational pattern, the influence of a non-axisymmetric bar potential, and a central molecular zone (CMZ)-like ring. We observe an outflow of CO(2-1) gas along the minor axis, at a distance of $\sim$ 220 pc from the nucleus. The total molecular gas mass is estimated to be $1 - 5 \times 10^8 \, M_{\odot}$, with non-circular motions contributing $10\%$. Our SED analysis indicates an AGN fraction of 0.88 and a star formation rate (SFR) of 0.42 $M_{\odot}\,\text{yr}^{-1}$.

These findings highlight the complex dynamics in the centre of NGC 4593, which are significantly influenced by the presence of the AGN. The overall physical properties of this system suggest that the AGN has a substantial impact on the evolution of NGC 4593.

# Introduction

The role of active galactic nuclei (AGN) in shaping the evolution of galaxies across the Universe is not well understood. AGNs are powered by the accretion of matter into a supermassive black hole (SMBH) in the galaxy’s core, and in many cases, their luminosity outshines that of the host galaxy (cite: kauffmann2000unified; heckman2004present; hopkins2005black).

Observational and theoretical studies in the last decades have highlighted a possible link between the redshift evolution of black hole (BH) accretion and the star formation rate in galaxies, which may result from feeding and feedback processes (cite: silk1998quasars; fabian2012observational). The relative influence of matter accretion (feeding) versus feedback processes, such as energy released in the form of radiation, outflows, and jets, likely interacts with the surrounding medium, preventing the gas from cooling and condensing into stars. AGN feedback can also have positive effects, such as jet-induced star formation (cite: combes2017agn). These processes are observed in various gas phases, including molecular, atomic, and ionised, and their interaction with host galaxies remains a topic of ongoing research (cite: cicone2014massive; hatziminaoglou2010hermes; morganti2017many; fiore2017agn; tombesi2015wind).

Theoretical works suggest that even a tiny fraction of the vast energy produced by AGN can have a significant impact on the growth and evolution of galaxies, highlighting the importance of further research in this area (cite: mcnamara2007heating; gitti2012evidence; gaspari2020linking; schawinski2007observational). Massive molecular outflows are observed in many galaxies and are generally interpreted as the long-sought feedback mechanism. However, the exact properties and timescales of this feedback are still not fully understood (cite: morganti2017many). Several studies suggest that the observed outflows do not suppress star formation in their host galaxies (cite: feruglio2010quasar; harrison2013impact). The relationship between AGN feedback and star formation is indeed complex, suggesting a potential interplay between these two processes (cite: harrison2017impact; girdhar2022quasar).

AGN radiation is often ’hidden’ by large amounts of dust and gas, which prevents the study of the activities in the central part of galaxies where the interaction between AGN and host galaxy takes place (cite: hickox2018obscured). Dust and gas absorb and scatter radiation from the central AGN, thereby attenuating the radiation intensity, and the dust grains mainly absorb the FUV radiation and re-emit it mostly at far-infrared (FIR) wavelengths. This reemission in the IR drastically affects the observable parameters of the AGN (cite: pier1992infrared), and polarising its light provides important knowledge on the AGN structure and shape (cite: antonucci1985spectropolarimetry). Studies demonstrate that radiative feedback from AGNs confirms that radiation pressure on dusty gas is the primary mechanism regulating the obscuration and, consequently, the visibility of AGN activities (cite: hensley2014grain; venanzi2020role; arakawa2022radiation; ishibashi2015agn; ricci2017close; ricci2022bass). The AGN feedback effectively clears out the obscuring dust and gas within the BH, impacting its interaction with the host galaxy. The study by (cite: hopkins2012stellar) suggests that radiation pressure on dust grains is a significant, yet not exclusive, driver of galactic superwinds. In a specific case, (cite: contursi2013spectroscopic) observed in the outflow of M 82 that dust is kinematically decoupled from gas, indicating that dust grains move slower than ionised and molecular gas and may fall back into the galaxy disc.

Carbon monoxide (CO) is a pivotal tracer for cold molecular gas in galaxies, detectable with submillimetre and radio telescopes (cite: bolatto2013co). The several rotational transitions of the CO molecules provide insights into the molecular gas temperature and density (cite: weiss2005multiple; papadopoulos2010co; kamenetzky2018recovering; andreani2018extreme). Several ALMA observations of galaxies have particularly focused on the dynamics of the gas around AGN (cite: veilleux2020cool; esposito2022agn), highlighting the influence of AGN emission on the molecular gas properties. The exact nature of this influence, especially on star-forming gas, can be localised and complex (cite: rosario2019accreting). Multi-transition CO data modelling further refines our understanding of the AGN impact on molecular gas (cite: van2010black; fluetsch2019cold).

High-resolution CO observations are crucial to constrain the spatial and velocity dynamics of molecular gas (cite: sun2018cloud). Through moment maps, we derive the properties of the gas dynamics, with zeroth, first, and second moment maps detailing the CO emission distribution, line-of-sight velocity, and velocity dispersion, respectively (cite: davis2013atlas3d). Different studies examine the relationship between CO molecular gas and obscured AGN, highlighting the intricate interplay with dust. For instance, ALMA observations of dust-obscured quasars at high redshifts unveil molecular gas outflows and feedback mechanisms, suggesting a potential evolutionary sequence between star-forming galaxies, ultra-luminous infrared galaxies, and quasars (cite: spingola2019erratum; brusa2017molecular). However, this correlation may primarily be driven by underlying factors such as stellar mass and SFR. Interestingly, when controlling for star formation, (cite: koss2021bat) find no significant differences in molecular gas properties between AGN-hosting galaxies and inactive galaxies, indicating that AGN feedback might not have a discernible impact on the molecular gas reservoirs.

Molecular outflows are usually identified in high spectral resolution data cubes as high-velocity gas deviating from a regular gas rotation (cite: cicone2014massive). In a comprehensive study, (cite: lutz2020molecular) discuss methods for detecting such outflows, emphasising the intermittent activity of AGN as a potential driver (cite: newman2012sins). Additionally, (cite: stuber2021frequency) find that central molecular outflows are relatively common in nearby spiral galaxies, especially those with higher stellar mass and SFR. These outflows often link to AGN and bars, but they seem to have a limited effect on suppressing star formation due to their low mass-loading factors.

In this paper, we report a study of the galaxy NGC 4593, which belongs to the Twelve-micron WInd STatistics (TWIST) sample, a CO(2–1) molecular gas survey of 41 galaxies drawn from the 12-micron sample (cite: rush1993extended). Other studies (cite: Juan+20; Asnakew) have reported results derived from four galaxies in the same sample.

![image](images/hubble_image_cropped_aug.pdf) ![image](images/NGC4593_HST_ALMA_contour_cropped_aug.pdf) ![image](images/dss.pdf)

NGC 4593 is a face-on spiral galaxy in the southern sky ($\alpha = 12^h\,39^m\,39.4^s, \, \delta = -5^\circ\, 20'\, 39''$) located at $D \approx 39 \pm 4$ Mpc (cite: marinova2007characterizing). This galaxy is a well-defined barred spiral with nuclear, inner, and outer rings, classified morphologically as (R)SB(rs)b (cite: deVaucouleurs1991). It contains a prominent bar that likely drives gas inflow toward the nucleus. NGC 4593 has a nuclear dust ring linked to radial dust lanes in the galaxy’s bar, indicative of gas inflow (cite: wu2021morphological; hunt2008molecular; laine2001ngc). The accretion disc size in NGC 4593 exceeds that of the broad-line region, hinting at a complex central engine structure (cite: cackett2019comparison). NGC 4593 is a well-studied Seyfert 1 galaxy, exhibiting polarised continuum emission, X-ray, UV, and radio variability, as well as time lags between FUV and NUV bands, and between $0.3-0.5 \, \rm keV$ vs. $0.8 - 1.5 \, \rm keV$ and $0.3-0.5 \, \rm keV$ vs. $4.0-10.0\, \rm keV$ energy bands (cite: sriram2009energy; kumari2023contrasting; kammoun2021modelling).

The density profile of NGC 4593’s circumnuclear medium aligns with a power-law distribution, indicating a continuous gas distribution around the central BH (cite: wang2022density). In Table [1](#tab:table1), we summarise the observed properties and measured quantities for NGC 4593, providing an overview of the galaxy’s physical characteristics, which are used in this work.

The main goal of this paper is to study the molecular gas properties in the central part of NGC 4593 using ALMA observations of the CO(2-1) transition. Using these observations (Section [2](#obs)), we model the data to determine the kinematics and morphology of the gas (Section [3](#res)). To acquire a better understanding of the interaction between the molecular gas and the AGN, we further enhance our study by using observations at other wavelengths to create a spectral energy distribution (SED). This approach provides a more holistic perspective of the galaxy, allowing for a better understanding of the influence of AGN activity on its host galaxy. We discuss how our findings contribute to the ongoing debate over the mechanisms driving AGN feeding, feedback, and dust emission, as well as their impact on galaxy evolution, in Section [4](#Discussion).

| Parameter                    | Value                               | Ref.   |
|:-----------------------------|:------------------------------------|:-------|
| Name                         | NGC 4593                            | \(1\)  |
| RA                           | 12:39:39.43                         | \(1\)  |
| Dec                          | $-5$:20:39.3                        | \(1\)  |
| *Hubble* class               | (R)SB(rs)b                          | \(2\)  |
| $z$                          | 0.0083                              | \(1\)  |
| $D_L$                        | 39 Mpc                              | \(1\)  |
| Type                         | S1                                  | \(3\)  |
| $F_{12}$                     | 0.47 Jy                             | \(4\)  |
| $\log(M_*/M_{\odot})$        | 10.6–11.01                          | \(5\)  |
| SFR                          | $0.19$–$1.12$ $M_{\odot}$ yr$^{-1}$ | \(6\)  |
| $\log(L_{\mathrm{IR}})$      | 43.431                              | \(7\)  |
| PA                           | $-59.3^{\circ}$                     | \(8\)  |
| $V_{\mathrm{sys}}$           | 2492 km s$^{-1}$                    | \(2\)  |
| $i$                          | $47.4^{\circ}$                      | \(8\)  |
| $F_{\mathrm{PAH2}}$          | $287.2 \pm 7.4$ mJy                 | \(9\)  |
| $F_{\mathrm{mid\text{-}IR}}$ | $352 \pm 8$ mJy                     | \(10\) |

: Observed properties of NGC 4593

Table notes: List of observed properties includes coordinates, redshift, luminosity distance, star formation rate (SFR), infrared luminosity, position angle (PA), systemic velocity, and inclination.

# Observations

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Band | Emission | Frequency | BMAJ | BMIN | BPA | RMS | $\rm V_{sys}$ | Velocity width | Velocity range | Velocity res. |
|  |  | (GHz) | (arcsec) | (arcsec) | ($^{\circ}$) | (Jy beam$^{-1}$ km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) | (km s$^{-1}$) |
| 6 (mosaic) | CO(2–1) | 228.628 | 0.232 | 0.183 | $-59.3$ | $7 \times 10^{-4}$ | 2491 | 310 | 1990 | 2.4 |

Table notes: Details of Band 6 (mosaic) observations of NGC 4593 (Project ID: 2017.1.00236.S). Listed parameters include the ALMA Band, target emission line, central frequency, and synthesised beam properties (BMAJ, BMIN, and BPA). The RMS column indicates the noise level, $\rm V_{sys}$ is the systemic velocity, and velocity width represents the observed line width. Velocity range denotes the data cube’s velocity coverage relative to $\rm V_{sys}$, and velocity resolution specifies the observation’s resolution.

## ALMA mm/sub-mm interferometry

NGC 4593 was observed by the Atacama Large Millimeter/submillimeter Array (ALMA) on January 4th, 2018 (Cycle 5, PI Matthew A. Malkan, Program ID: 2017.1.00236.S). The spectral setup was optimised for the CO(2-1) transition line in band 6, at a rest frequency of 230.5380 GHz. The synthesised beam size was $0.029^{\prime\prime} \times 0.027^{\prime\prime}$, and the rms sensitivity was $0.36$ mJy/beam over 0.9767 GHz. The observations consist of a total of 1920 channels with a total bandwidth of 1.875 GHz. The observing parameters are detailed in Table [\[tab:table2\]](#tab:table2).

Data were calibrated and imaged using the Common Astronomy Software Applications (**CASA**) package (cite: bean2022casa), pipeline v5.1.1-5, and our own scripts to perform the imaging and post-processing tasks under **CASA** v5.4.0-70. For the image reconstruction, we used the standard **hogbom** deconvolution algorithm with **briggs** weighting and a robustness value of $2.0$. The beam size for our object in the CO(2-1) spectral window is $12.8^{\prime\prime} \, \times \, 6.5^{\prime\prime}$ at a position angle of $PA \,=\, -59.3^{\circ}$, corresponding to $438 \, \times \, 345$ $\rm\,pc^2$ at a distance of $39$ Mpc. The field of view (FOV) has a diameter of 27$^{\prime\prime}$ ($5.1$ kpc) and is covered using a single pointing, with the largest angular scale recoverable being $2.6^{\prime\prime}$ ($\sim \, 490$ pc). The continuum sensitivity of the data is $0.1$ mJy/beam, while the rms noise for the spectral line data, with a channel width of $10$   km/s, is $0.7$ mJy/beam.

After reconstructing the image, we prepared the final CO data cube and maps. We used the same deconvolution algorithm for image reconstruction, processing it initially at the native velocity resolution of 2.4 km/s, as shown in Table  [\[tab:table2\]](#tab:table2). To improve the signal-to-noise ratio, we resampled the data to a coarser velocity resolution of 10 km/s. This resampling helped us optimise the analysis of kinematic features while preserving critical details. We applied a masking process to isolate CO(2-1) emission regions, starting with a threshold mask at $2 \times \text{rms}$ noise level to detect significant emission. We then made manual adjustments to refine the mask and minimise noise. This process follows the methodology used in the analysis of ESO 420-G13 (cite: fernandez2020co). After masking, we subtracted the continuum emission using a zero-degree polynomial fit in the spatial frequency domain and the adjacent channels. Finally, we corrected the data cubes for primary beam attenuation within the 37.84$^{\prime\prime}$ field of view, ensuring accurate calibration for further analysis.

## Ancillary data

To gain a more comprehensive understanding of our object, we expanded our analysis beyond ALMA observations. Specifically, we adopted a multi-wavelength approach to construct a well-sampled SED. For this purpose, we utilise Johnson photometry for the U, B, and V bands (cite: mcalary1983near). Additionally, we incorporated far-ultraviolet (FUV) and near-ultraviolet (NUV) measurements from GALEX (cite: bouquin2018galex). *Spitzer*-IRS high-resolution spectra are crucial for constraining the dusty torus component at its peak wavelengths (cite: tommasin2010spitzer). 2MASS measurements were adopted for the near-infrared continuum in the J and H bands (cite: jarrett20032mass), and additional 2$\mu$m observations were obtained from (cite: skrutskie2006two). The Wide-field Infrared Survey Explorer (WISE) survey contribute key data points in the mid-infrared range (cite: cutri2012explanatory). HST/STIS (UV, NIR, and optical) observations were collected from the HST science archive (archival research programme ID: HST-AR-16143; PI: M. Malkan) (cite: malkan1998hubble) and shown Fig. [1](#fig:hst) (cite: cackett2018accretion) together with the CO(2-1) emission.

In order to provide a comprehensive view of possible AGN feeding and feedback mechanisms within host galaxies, our study incorporates SED fitting alongside our CO observations (cite: ciesla2015constraining). This method enriches our analysis by enabling detailed quantification of dust and gas properties, crucial for interpreting molecular gas dynamics. By linking SED-derived parameters such as dust mass, SFRs, and the AGN’s Eddington ratio with CO kinematics, we can better understand the interplay between AGN activity and star formation. Furthermore, SED fitting allows us to identify the AGN component or fraction and assess its impact on the surrounding environment(cite: atlee2011multi; karouzos2014tale; salome2023star). We have complemented our observations with additional ALMA data, specifically for the continuum emission in Band 3. This observation was carried out under the project code: 2018.1.00576.S. The selected frequency band for this observation is Band 3, which ranges from 89.509 to 105.494 GHz. The angular resolution achieved during this observation is 0.25$^{\prime\prime}$. The Band 3 observation has a continuum sensitivity of 0.0259 mJy/Beam, obtained with an integration time of 5 minutes. The detailed information of the observations with ALMA is listed in Table [\[tab:table2\]](#tab:table2). The photometry data used for the SED fitting, supported by ancillary data are listed in Table [\[table:3\]](#table:3).

# Results

## Molecular gas properties

![image](images/mom0.jpg) ![image](images/mom1.jpg) ![image](images/mom2.jpg) ![image](images/cont.jpg)

| Observed band | Flux | Significance | Systematic Error (%) | Ref. |
|:---|:---|:---|:---|:---|
| *Swift* ($2$–$10$ keV) | $3.16 \times 10^{-11} \, \mathrm{erg\,cm^{-2}\,s^{-1}}$ | No uncertainty reported | 10% | \(1\) |
| *Swift* ($14$–$195$ keV) | $3.4 \times 10^{-10} \, \mathrm{erg\,cm^{-2}\,s^{-1}}$ | 90% confidence | 10% | \(1\) |
| GALEX (FUV) | $3.60 \pm 0.05 \, \mathrm{mJy}$ | $1\sigma$ | 5% | \(2\) |
| GALEX (NUV) | $5.91 \pm 0.03 \, \mathrm{mJy}$ | $1\sigma$ | 5% | \(2\) |
| 2MASS (J) | $415.00 \pm 7.71 \, \mathrm{mJy}$ | $1\sigma$ | 2% | \(3\) |
| 2MASS (H) | $494.00 \pm 10.20 \, \mathrm{mJy}$ | $1\sigma$ | 2% | \(3\) |
| 2MASS (Ks) | $427.00 \pm 12.40 \, \mathrm{mJy}$ | $1\sigma$ | 2% | \(4\) |
| IRAC ($3.6\,\mu\mathrm{m}$) | $125.00 \pm 8.03 \, \mathrm{mJy}$ | $1\sigma$ | 5% | \(5\) |
| IRAC ($4.5\,\mu\mathrm{m}$) | $134.00 \pm 21.00 \, \mathrm{mJy}$ | $1\sigma$ | 5% | \(5\) |
| IRAC ($5.8\,\mu\mathrm{m}$) | $163.00 \pm 23.95 \, \mathrm{mJy}$ | $1\sigma$ | 5% | \(5\) |
| IRAC ($8.0\,\mu\mathrm{m}$) | $229.00 \pm 33.16 \, \mathrm{mJy}$ | $1\sigma$ | 5% | \(6\) |
| IRAS ($12\,\mu\mathrm{m}$) | $299.00 \pm 73.00 \, \mathrm{mJy}$ | Uncertainty, confidence not specified | 10% | \(7\) |
| Spitzer MIPS ($24\,\mu\mathrm{m}$) | $633.00 \pm 89.00 \, \mathrm{mJy}$ | No uncertainty reported | 10% | \(5\) |
| ALMA (Band 6) | $8.13 \pm 0.22 \, \mathrm{mJy}$ | $1\sigma$ | 10% | \(8\) |
| ALMA (Band 3) | $8.42 \pm 0.06 \, \mathrm{mJy}$ | $1\sigma$ | 10% | \(8\) |

Table notes: This table presents the photometry data for NGC 4593 across a range of observed bands, including X-ray, UV, near-infrared, and mid-infrared wavelengths. Flux values are given in units of $\mathrm{mJy}$, except for the *Swift* X-ray data, which are expressed in $\mathrm{erg\,cm^{-2}\,s^{-1}}$. The uncertainties listed in the flux column correspond to the statistical errors of the measurements. The significance column denotes the confidence level associated with the data, while the systematic error indicates the potential percentage uncertainty due to instrumental calibration or observational conditions.

Moment maps were created from the available data cubes and are shown in Fig. [2](#fig:Moments). The moment-0 map delineates the overall spatial molecular gas distribution within the galaxy, indicating intensity values ranging from 0 to 6.0 $\rm Jy/beam \cdot km/s$, with a heightened concentration of gas discernible in the very inner regions of the galaxy. The moment-1 map traces the velocity field of the gas, quantified in units of $\rm km/s$, and highlights the dynamics in NGC 4593, including the rotational dynamics and the kinematic patterns inherent in the galaxy’s structure. In Fig. [2](#fig:Moments), we present a comparison between the dust and molecular gas distributions within the galaxy under study. This figure features the continuum emission, indicating the extent of dust, with ALMA CO(2-1) contours overlaid to highlight the molecular gas distribution.

As shown in Fig. [2](#fig:Moments), the CO gas distribution within NGC 4593 exhibits a striking one-arm structure. This feature is indicative of a logarithmic $m=1$ mode, which refers to a pattern where there is a single dominant spiral arm in the distribution of gas. This phenomenon is not commonly observed in the nuclear regions of barred galaxies (cite: shaw1995nuclear; phookun1993ngc; ann2005formation; thakur2009effect). The $m=1$ mode suggests a significant deviation from axisymmetric equilibrium, potentially driven by tidal interactions or internal instabilities.

![](images/chanmap.jpg)

## 3D-BAROLO model

To delve into the kinematics of NGC 4593’s innermost regions, we employed the 3D-Based Analysis of Rotating Object via Line Observations (3D-BAROLO) software (cite: di20153d). This tool fits a 3D tilted-ring model to emission line data cubes, enabling us to infer the galaxy’s rotation curves and the gas column density, a critical parameter in our analysis. 3D-BAROLO provides two distinct normalisation options for the gas column density: pixel-by-pixel (**LOCAL**) and azimuthally averaged (**AZIM**). The **LOCAL** normalisation allows to consider the non-axisymmetric density models and prevents regions with unusual gas distributions, such as clumpy regions or voids, from skewing the overall fit. This method offers a granular view of the galaxy’s kinematics and is particularly beneficial when examining complex structures or regions with high spatial variability in the gas distribution. On the other hand, the **AZIM** normalisation uses the azimuthally averaged flux in each ring as the normalisation value, providing a more global perspective of the galaxy’s kinematics. This method is particularly effective when the goal is to understand large-scale kinematic patterns in the galaxy, such as rotation curves or velocity dispersion profiles.

![image](images/ngc_4593_maps_azim.pdf) ![image](images/ngc_4593_maps_local.pdf)

We used the CO(2-1) data cube with a spectral resolution of 10 $\rm km/s$ as input data for 3D-BAROLO. The tilted-ring model adopted by 3D-BAROLO operates on two fundamental assumptions: the emitting material is encapsulated within a thin disc, and the angular momentum of the galaxy is responsible for the observed rotational pattern. These assumptions prove to be remarkably effective in scrutinising galaxy kinematics, extending their applicability even to scenarios where the galaxy is not perfectly edge-on or the gas does not adhere to a circular motion trajectory. As inputs to the model, we used *Hubble* and Pan-STARRS images of the galaxy to deduce the initial values for position angle (PA) and inclination (INC). The ALMA moment-0 maps (see Fig. [2](#fig:Moments)) are instrumental in pinpointing the galaxy’s centre and systemic velocity ($\rm V_{SYS}$). Fig. [3](#fig:chan_azim) showcases the channel maps, which feature two distinctive normalisations, **LOCAL** and **AZIM**, conceived through the analytical process of 3D-BAROLO.

Fig. [4](#fig:maps) shows a dissection of the molecular gas dynamics in NGC 4593, the CO(2-1) emission characteristics within the galaxy, as interpreted through two distinct normalisation methods: Azimuthal and Local, respectively portrayed in separate panels. The model enables us to discern a clear velocity field within the residual representations, indicating a spread of up to $\pm \, 50$ $\rm km/s$. This trend is consistent across both the Azimuthal and Local normalisation techniques, substantiating the robustness of the observed patterns. Similarly, the velocity dispersion maps delineate variations up to $50$ $\rm km/s$, shedding light on the complex, yet orderly gas dynamics prevalent within the NGC 4593 galaxy. Furthermore, the velocity field distribution ranges from $-150$ to $150 \, \rm km/s$ for both data and model, while the residuals show a range of -50 to 50 $\rm km/s$. The dispersion (sigma) ranges from $10$ to $35$ $\rm km/s$ for data and model, and $-10$ to $20$ $\rm km/s$ for residuals. The intensity ranges from $0.002$ to $0.016$ $\rm Jy \, km/s$ for data/model and $-0.0025$ to $0.0025$ for residuals.

![](images/ngc_4593_pv_azim.pdf)

The position-velocity ($p-v$) diagrams of the CO(2-1) emission in NGC 4593, extracted from the data and model cubes along the major and minor axes, are shown in Fig. [5](#fig:pv). For the major axis (top panel), the observed rotational velocities (yellow dots) from the best-fit disc model align closely with the data-derived contours, showcasing a consistent rotation curve. The minor axis (bottom panel), on the other hand, offers insights into non-rotational gas motions 1.5$^{\prime\prime}$ away from the centre of the galaxy (redshifted motion to the south of AGN near the centre). The dashed green circle in the bottom panel highlights a region about 2$^{\prime\prime}$ away from the centre, where possible gas inflow or outflow is observed. The disparities between the model and observed data in this plane may hint at vertical motions or inflows (or outflows), potentially driven by mechanisms like feeding or feedback, interactions with neighbouring galaxies, or even AGN-driven winds. In the bottom panel of Fig. [5](#fig:pv), it is clear that the model does not accurately represent the molecular gas distribution between 4$^{\prime\prime}$ and 6$^{\prime\prime}$. This discrepancy could arise from the model primarily emphasising the central region. Alternatively, it might indicate the presence of cold molecular outflows.

## DISCFIT model

To complement and cross-verify our results obtained from the 3D-BAROLO analysis, we utilised an additional analysis tool, DISCFIT. DISCFIT (cite: spekkens2007modeling) is an instrumental modelling tool for dissecting the structural components of galaxies. This tool adeptly deconstructs a galaxy’s luminosity distribution into its fundamental constituents, such as the disc, bulge, and bar structures, when they are present. We applied DISCFIT to NGC 4593 and replicated the galaxy’s observed kinematic features using the velocity moment map as an input, and utilising the same initial conditions as used for 3D-BAROLO. However, as shown in Fig. [6](#fig:discfit) (residuals in the top right and rotation curve comparison in the bottom plot), we observe notable deviations, particularly in the galaxy’s core and along the first eastern spiral arm. These deviations, visible in the residuals and the rotation curve comparison, show that while the models capture the general kinematic structure, they struggle to accurately represent the complex dynamics in these regions. One key observation is that 3D-BAROLO tends to align more closely with observational data when accounting for radial velocity, suggesting a potential overfitting to axisymmetric non-circular motions. In contrast, DISCFIT provides a more consistent fit regardless of radial velocity inclusion. Notably, DISCFIT does not significantly react to data bumps that 3D-BAROLO attempts to follow. A specific example of this behaviour is evident near the galaxy’s centre, around 0.8$^{\prime\prime}$ from the nucleus, which can be observed in the residual image of DISCFIT overlaid with contours.

The discrepancy between models could also be attributed to their dimensional approaches: DISCFIT’s 2D modelling contrasts with 3D-BAROLO’s additional consideration of disc scale-height (Z0 parameter), set to 1$^{\prime\prime}$ in our study. This difference becomes particularly apparent at the edges of the rings in the models. 3D-BAROLO excels in detailing galaxy morphology, aiding in the derivation of physical quantities like surface density and the calculation of molecular and black hole masses. Conversely, DISCFIT better elucidates axisymmetric behaviours. However, the face-on orientation of NGC 4593 complicates the evaluation of model accuracy. Furthermore, the absence of the galaxy’s outer northern arms, approximately 10$^{\prime\prime}$ from the centre, raises questions about possible outer rings or gas stripped and scattered in a conical distribution.

In Fig. [7](#fig:spiral_arm_widths), we compare the spiral arm widths, estimated from the observational data of CO(2-1) molecular gas, with the disc scale height derived from 3D-BAROLO modelling. In the inner disc region (0 to 5.5$^{\prime\prime}$), the spiral arm width ranges from 1.0$^{\prime\prime}$ to 1.3$^{\prime\prime}$, while the disc scale height shows a similar variation, from 1.1$^{\prime\prime}$ to 1.3$^{\prime\prime}$. Beyond 5.5$^{\prime\prime}$, the single-arm region has a width ranging from 1.35$^{\prime\prime}$ to 1.45$^{\prime\prime}$. Although it is not possible to measure the flaring directly without an edge-on galaxy, the proportionality between the width and height suggests that the flaring in NGC 4593 is compatible with that seen in other galaxies (cite: patra2020theoretical).

![image](images/diskfit.png) ![image](images/allplots.pdf)

![](images/spiral_arm_widths.pdf)

# Discussion

## Gas kinematics

In our analysis, delineated in Fig. [8](#fig:parameters), we subjected the ALMA data for NGC 4593 to a detailed 3D-BAROLO analysis. This analytical representation comprises six plots, each detailing a distinctive parameter — $V_{\text{rot}}$ (rotation velocity), $\sigma_{\text{gas}}$ (gas velocity dispersion), $v_{\text{rad}}$ (radial velocity), $\phi$ (azimuthal angle), $i$ (inclination angle), and $\Sigma$ (gas surface density measured in $\rm Jy \, km/s$) — in relation to the radius measured in arcseconds.

The best-fit values of the model to the data, derived from this analysis, indicate an average inclination of 47.4 degrees and a position angle (PA) of 276 degrees. Since the kinematic major axis is roughly E-W, the near side is located to the north, and the far side to the south, as indicated by the molecular gas kinematics (see Fig. [9](#fig:velocityfield)). We conclude that the near side of NGC 4593 is to the north and the far side to the south, further supported by the dust lane morphology visible in HST images (see Fig. [1](#fig:hst)). This conclusion is confirmed by extended MUSE observations of the galaxy’s kinematics (cite: den2020muse), which ensure consistency with the northern side as the near side.

The residual map reveals deviations from the expected rotation (see Figs. [4](#fig:maps),  [6](#fig:discfit)). A redshifted residual does not necessarily imply that a region is receding; it may instead indicate less blueshifted velocity than expected. These residuals could result from unmodelled radial gas motions or other dynamic factors. 3D-BAROLO’s axisymmetric assumption may not fully account for the kinematics of molecular gas in heavily barred systems. For instance, (cite: schnorr2014feeding) demonstrated that non-axisymmetric bar potentials in NGC2110 influenced significant molecular outflows, suggesting that similar effects could be at play in NGC 4593.

![](images/ngc_4593_parameters.pdf)

## Estimation of the molecular gas mass

We computed the CO(2–1) line luminosity $L^{\prime}_{\text{CO}(2-1)}$ using the following equation (cite: solomon2005molecular): $$\begin{equation}
L^{\prime}_{\text{CO}(2-1)} = 3.25 \times 10^{7} \, S_{\text{CO}}\Delta v \, \nu^{-2}_{\text{obs}} \, D^{2}_{L} \, (1+z)^{-3}.
\end{equation}$$ To determine the total flux $S_{\text{CO}}\Delta v$, we used the moment-0 map of the ALMA CO(2-1) observations (Fig. [2](#fig:Moments)), where the restoring beam size is $0.23^{\prime \prime} \times 0.18^{\prime \prime}$ at a position angle of $-59.30$ degrees. Focusing on a region with a $12^{\prime \prime}$ radius, we obtained a flux density of $146.3 \pm 1.1$ $\rm Jy \,\rm km/s$, which serves as our value for $S_{\text{CO}}\Delta v$. Using these values, along with $D = 39$ Mpc, $z = 0.009$, and $\nu_{\text{obs}} = 230$ GHz, we calculated the CO(2–1) line luminosity to be: $$\begin{equation}
L^{\prime}_{\text{CO}(2-1)}  \approx 1.40 \pm 0.10\times 10^{8} \,\, [\text{K km s}^{-1} \text{ pc}^{2}].
\end{equation}$$

We then converted $L^{\prime}_{\text{CO}(2-1)}$ to $L^{\prime}_{\text{CO}(1-0)}$ using a conversion ratio of $\frac{L^{\prime}_{\text{CO}(2-1)}}{L^{\prime}_{\text{CO}(1-0)}} \approx 5.0$, which reflects the typical ratio observed in galaxies with moderate to high levels of star formation, including (ultra) luminous infrared galaxies ((U)LIRGs) (cite: kamenetzky2016relations). This conversion yields: $$\begin{equation}
L^{\prime}_{\text{CO}(1-0)} \approx (0.28 \pm 0.02) \times 10^{8} \,\, [ \text{K km s}^{-1} \text{ pc}^{2}].
\end{equation}$$ Using the conversion factor $\alpha_{\text{CO}}$, which ranges from $0.8 \, M_{\astrosun}$ to $3.2 \, M_{\astrosun}$ (cite: bolatto2013co), we estimated the molecular gas mass $M(H_2)$ to be within the range: $$\begin{equation}
M_{H_2} = \alpha_{\text{CO}} \, L^{\prime}_{\text{CO}(1-0)} \approx (0.22 - 0.90) \times 10^{8} \, M_{\astrosun}.
\end{equation}$$ It is important to note that, in addition to the conversion factor, there are uncertainties in the derived total CO luminosity due to the nature of interferometric observations, which can filter out extended emissions. Consequently, the total molecular gas mass could be larger if CO(2-1) emission is more extended.

## Estimation of SMBH mass

To estimate the mass of the supermassive black hole (SMBH) in NGC 4593, we adopted the methodology outlined in (cite: smith2021wisdom), which relies on the correlation between the SMBH mass and the rotation of its host galaxy using molecular gas kinematics. The relationship is described by the following equation: $$\begin{equation}
\log \left(\frac{M_{\text{BH}}}{M_{\odot}}\right) = (7.5 \pm 0.1) + (8.5 \pm 0.9) \left[\log \left(\frac{W_{50}}{\sin i} \, \text{km s}^{-1}\right) - 2.7\right],
\end{equation}$$ where $M_{\text{BH}}$ represents the central SMBH mass, $W_{50}$ denotes the full width at half-maximum of a double-peaked CO(2-1) emission line profile, and $i$ is the inclination of the CO disc. This relationship exhibits a total scatter of $0.6$ dex, comparable to other SMBH mass correlations, which have an intrinsic scatter of $0.5$ dex.

For our analysis, we derived the line width at half-maximum, $W_{50}$, by employing the method described by (cite: tiley2016tully) for measuring the line width of double-peaked profiles. This approach involves fitting a Gaussian double-peak profile to the emission-line data. As demonstrated in Fig. [9](#fig:velocityfield), we utilised a double-peak Gaussian function to accurately fit the integrated CO(2-1) emission-line spectrum, representing the observed emission profile from the entire field of view (FOV) as obtained from our 3D-BAROLO modelling. The $W_{50}$ value was determined using the formula $W_{50} = 2(w + \sigma \sqrt{2 \ln 2})$, where $w$ is the velocity half-width at half-maximum (HWHM) and $\sigma$ is the velocity width of the Gaussian peaks. From this analysis, we obtained $W_{50} \simeq 314 \pm 10$ $\rm km/s$, and the inclination was derived as $i \simeq 47.70^{\circ} \pm 1.1$, as depicted in Fig. [8](#fig:parameters).

Combining these measurements, we calculated the SMBH mass as $\log \left( \frac{M_{\text{BH}}}{M_{\odot}} \right) = 6.89 \pm 0.04$. This result was compared with the values obtained from the WISDOM project for NGC 4593 (cite: tiley2016tully), yielding $\log \left( \frac{M_{\text{BH}}}{M_{\odot}} \right) = 6.86$, and with (cite: denney2006mass), who derived an SMBH mass of approximately $\log \left( \frac{M_{\text{BH}}}{M_{\odot}} \right) = 6.99$ using reverberation mapping.

![image](images/mom_reg.png) ![image](images/ngc4593_w50.jpg)

## Evidence of non-circular motion and molecular inflow or outflows

Our analysis using 3D-BAROLO on NGC 4593 reveals significant dynamics within the galaxy’s gas structure. The CO gas distribution exhibits a one-arm structure, indicative of an $m = 1$ density wave or perturbation. Such a feature, rare in the nuclear regions of barred galaxies, suggests a dominant regular velocity field, implying limited non-circular motion. However, the presence of this $m = 1$ feature challenges the axisymmetric assumptions inherent in the 3D-BAROLO models. The discrepancy in the fit between the galaxy’s northern and southern sections highlights the limitations of current models in fully capturing the kinematic complexity. This aspect aligns with observations by (cite: barbosa2006gemini) regarding ionised gas kinematics, offering a broader comparative perspective on gas dynamics in barred galaxies.

The observed CO ring (inner) near the centre of the bar shows a complex interplay between bar dynamics and molecular gas distribution. The kinematic position angle (PA) of approximately $-59.3^{\circ}$ in the nuclear disc significantly differs from the morphological PA of $46^{\circ}$, suggesting that the ring has an elliptical structure with elongated stellar and gas orbits. This discrepancy likely indicates non-circular motions within the nuclear region, possibly driven by the influence of the central bar or other asymmetries in the gravitational potential. The inner structure of NGC 4593 is intricately shaped by its AGN, which exerts considerable influence on both the light profile and the dynamics of the central region, as demonstrated by (cite: alexei2008image). The poor fit in the nuclear region may reflect the limitations of the current kinematic model, which assumes axisymmetric conditions that may not fully capture the complexities of the actual orbital dynamics.

Adding to this complexity, the misalignment between its bar and bulge, alongside the presence of a pseudobulge identified through Ks-band surface photometry (cite: kormendy2006pseudobulges), suggests a deviation from the standard evolutionary path driven by secular processes and bar-driven gas inflows (cite: sanders2022mira). Furthermore, the central region is characterised by a nuclear dust ring linked to radial dust lanes, indicating active gas inflow and potential starburst activity, which could significantly impact the pseudobulge’s development. The dynamic evolution of this region is further influenced by a non-axisymmetric bar potential, which alters gas dynamics and morphological structures, marking a critical phase in the galaxy’s evolution.

Residuals from the 3D-BAROLO modelling on velocity dispersion maps (Fig. [4](#fig:maps)) further support our findings by highlighting regions of excess velocity dispersion. These residuals, unaccounted for by the model, suggest additional kinematic components like turbulence or unresolved inflows (or outflows). Fig. [9](#fig:velocityfield) illustrates the CO(2-1) mean velocity map and the residuals between the observed and modelled data using 3D-BAROLO. The dashed red circle (region *a*), located about 2$^{\prime\prime}$ to 3$^{\prime\prime}$ northeast of the galaxy’s centre, highlights an area with non-circular motion likely caused by inflows or outflows of cold molecular gas. This region, visible in the velocity map, contributes approximately 10% of the galaxy’s total flux, with about half of this flux seen in the residuals, indicating that around 5% of the total flux is linked to non-circular motion. The estimated gas mass in this area is between $(0.5 - 2.5) \times 10^7 \, M_{\odot}$.

We must consider that some of these residuals may be associated with extraplanar gas, often extending several kiloparsecs above the disc in spiral galaxies (cite: fraternali2002deep; li2021kinematic). However, given the low inclination of NGC 4593, distinguishing non-circular motions within the plane of the disc from potential outflows in the perpendicular direction is challenging. The residuals observed in our analysis are relatively small and appear consistent with non-circular motions in the plane, rather than significant extraplanar outflows. If these were true outflows, we would expect velocities much larger than the observed rotational velocity (cite: marasco2019halogas). Additionally, extraplanar gas in other galaxies, such as the Milky Way, tends to be mostly atomic, have low densities, and constitute a small fraction of the total mass (typically less than 15%) (cite: soding2024spatially). Furthermore, the global SFR in NGC 4593 does not suggest a strong star-formation-driven outflow, and the galaxy does not reside in a particularly crowded environment that would indicate gas stripping or strong interactions (cite: kormendy2006pseudobulges).

Therefore, while we cannot completely rule out the presence of extraplanar gas, it is unlikely to be a significant factor in the observed kinematics of NGC 4593. The presence of this excess gas flux in the residuals suggests an inflow or outflow of molecular gas. Moreover, the bump in rotation velocity, radial velocity, surface density, and velocity dispersion for the same radius away from the centre, observed in the 3D-BAROLO results (see Fig. [8](#fig:parameters)), provides further evidence of this non-circular motion. The rotation velocity shows a noticeable rise and fall in the region, indicative of local perturbations. The radial velocity profile demonstrates deviations from the symmetric field expected for purely circular motions, suggesting inflow or outflow dynamics. An excess in surface density corresponds with the region, consistent with molecular gas accumulation. Finally, an increase in velocity dispersion in this region highlights the disturbed nature of the molecular gas. These characteristics, combined with the residual analysis, confirm the presence of non-circular motion and molecular inflows or outflows. The observed inflows or outflows and perturbations challenge the axisymmetric assumptions in the 3D-BAROLO models and underline the importance of non-axisymmetric bar potentials in shaping gas dynamics.

## Central molecular zone (CMZ) ring

The CMZ is a dense, gas-rich region typically found in the innermost few hundred parsecs of galaxies, characterised by intense star formation and dynamic activity influenced by the gravitational effects of the galactic bar and potential AGN activity (cite: morris1983temperature; bally1987galactic). Understanding the CMZ is crucial for studying galactic evolution due to its high concentration of molecular gas and its role as a central engine driving various dynamic processes.

Inflows of molecular gas, driven by bar-induced gravitational torques, funnel material into the CMZ, creating high-density molecular rings. These inflows are significant as they can enhance star formation rates (SFRs), fuel AGN activity, and drive turbulence within the CMZ. The interaction between inflowing gas and the central black hole (BH) can lead to episodic accretion events, contributing to AGN feedback mechanisms that regulate the growth and activity of the BH (cite: sormani2019mass; hatchfield2021dynamically; tress2024magnetic).

Our analysis suggests the presence of a CMZ-like ring in the innermost region of NGC 4593 (see Fig. [9](#fig:velocityfield)). The bar of the galaxy, with a length of approximately 35$^{\prime\prime}$ (cite: Mulchaey1997), aligns in such a way that it channels molecular gas into the CMZ-like ring through shocks and streaming motions. These patterns are consistent with bar-driven inflow mechanisms observed in other barred galaxies (cite: Athanassoula1992). The CMZ-like ring, with its high concentration of molecular gas, could play a crucial role in the galaxy’s evolution, potentially influencing SFRs, AGN activity, and the overall dynamical state of the galaxy (cite: armillotta2020life; torii2013detailed).

We estimate that the CMZ-like ring, located in the central region with a radius of about $2^{\prime \prime}$, accounts for approximately $20\%$ of the total molecular gas mass in NGC 4593, translating to a mass range of $\sim 0.2 - 1.0 \times 10^8 \, M_{\odot}$. The surface density of molecular gas in this CMZ-like ring is estimated to be in the range of $\Sigma \sim 0.26 - 0.34 \, \text{Jy}\,\text{km/s}$, which is significantly higher than the average surface density of molecular gas across the entire galaxy, estimated at $\Sigma \sim 0.10 - 0.14 \, \text{Jy}\,\text{km/s}$. This suggests that the surface density in the CMZ-like ring is about 2.5 times higher than the galaxy-wide average.

The velocity structure of the ring reveals strong rotational motion with signs of non-circular streaming inflow, potentially driven by bar-induced mechanisms. By examining the residual velocity field from our model, we observe significant residuals in the central region of the galaxy. The residual velocity profile indicates an inflow or outflow pattern that is perpendicular to the overall velocity map of the galaxy. Furthermore, most of these residuals at the centre are positive, suggesting an inflow of gas towards the nucleus.

## The spectral energy distribution

To characterise galaxies and gain insights into their basic constituents, decomposing their spectral energy distributions (SEDs) into various components is a standard approach. We employed the Code Investigating GALaxy Emission (CIGALE; (cite: boquien2019cigale; yang2020x; yang2022fitting)) to plot and analyse the SED of NGC 4593. The photometry data, including observations and corresponding error bars used as inputs for CIGALE, are reported in Table [\[table:3\]](#table:3). For modelling the star formation history, we used a "delayed" model, characterised by a gradual rise of the star formation rate (SFR) to a maximum, followed by an exponential decline. This model can also accommodate an exponential burst to simulate a recent episode of star formation.

For the Stellar Population Synthesis, we utilised a Single Stellar Population (SSP) as defined in (cite: bruzual2003stellar), incorporating a Chabrier Initial Mass Function, a metallicity of 0.02, and a separation age of 10 Myr. Dust attenuation was modelled using the attenuation modules from (cite: calzetti2000dust) and (cite: leitherer2002ultraviolet), while the dust emission parameters were based on the models by (cite: dale2014two). In addition, CIGALE allows for the inclusion of AGN emission in the SED. We employed a two-phase torus model for the AGN component, as described by (cite: stalevski2016dust), and linked the X-ray and UV/optical emissions of the AGN using the $\alpha_{\rm ox}$–$L_{\nu,2500\mathrm{\AA}}$ relation (cite: just2007x), with a maximum deviation of $|\Delta \alpha_{\rm ox}|_{\rm max} = 0.2$ to account for intrinsic scatter.

Initial conditions for our object were set as a face-on type-1 AGN, following the methodology outlined by (cite: mountrichas2021galaxy) and (cite: ciesla2015constraining), who investigated type-1 and type-2 AGNs using CIGALE. Parameters such as inclination and other model settings were primarily derived from the 3D-BAROLO results presented in Section [3](#res), while other initial conditions were allowed greater flexibility to improve the fit. This approach, while computationally demanding, yielded more precise fitting results.

The resulting SED fit, shown in Fig. [10](#fig:sed), represents the best-fitting model obtained with CIGALE based on our initial conditions and photometric data. For the AGN component, specific parameters in the torus model were chosen, including an outer-to-inner radius ratio ($R_{\rm out}/R_{\rm in}$) of 20, with possible values ranging from 10 to 30. The half-opening angle was selected based on the type-1 AGN perspective, and the inclination angle was derived from the position angle (PA) of the source (see Table [1](#tab:table1) for detailed parameter values). Although the alignment between the galaxy disc and torus may not be perfect, we assumed a standard inclination angle for consistency. Dust density gradients were set to $1.0$ for both polar angle and radial direction, ensuring a comprehensive representation of the dust distribution.

The power-law index $\delta$, modifying the optical slope of the disc, was set to $-0.36$, with an average edge-on optical depth at $9.7 \, \mu$m of $4.37 \pm 0.93$. These parameters indicate a prominent dusty torus structure around the AGN, aligned with the direct line of sight to the bright accretion disc and central engine, thus confirming the type-1 classification of NGC 4593. Based on this model, the AGN fraction (the ratio of AGN luminosity to total FIR luminosity) was determined to be $0.876 \pm 0.052$, underscoring the significant impact of the AGN on the SED and its influence on the galaxy’s overall spectrum. Detailed results derived by CIGALE are provided in Table [2](#table:4).

NGC 4593 is classified as a late-type barred spiral (SB) galaxy hosting a type-1 AGN. Its bolometric luminosity ($\log(L_{\rm bol}) = 44.163$) and the substantial AGN contribution to the overall spectrum indicate a dominant AGN influence. Bright AGNs often exhibit complex interactions between SFRs and AGN luminosity, with various studies suggesting diverse relationships (cite: fanidakis2012evolution; gutcke2015sfr). The AGN disc luminosity ($1.26 \times 10^{36} \, \text{erg/s}$) and intrinsic 2-10 keV luminosity ($L_{\nu, 2\,\text{keV}} = 1.11 \times 10^{18} \, \text{erg/s}$) support the presence of a powerful central black hole ($\log\left( \frac{M_{\rm BH}}{M_{\odot}} \right) = 6.86$).

Despite the strong AGN activity, the galaxy’s SFR remains moderate. Using CIGALE, we derived an SFR of 0.43 $M_{\odot}$ yr$^{-1}$ and a stellar mass of $\log({\rm M}_*/{\rm M}_\odot) = 10.646$, consistent with previous studies. The SFR calculated from the PAH11.25$\mu$m emission (cite: mordini2021calibration) is 0.36 $M_{\odot}$/year, while that from the \[CII\]158$\mu$m line (cite: fernandez2020co) is 0.19 $M_{\odot}$/yr. In contrast, the total FIR luminosity estimate (cite: kennicutt1998global) provides a higher SFR of 1.2 $M_{\odot}$/yr, using the log(FIR) luminosity from (cite: spinoglio1995multiwavelength) of 43.43. The specific star formation rate (sSFR) of $4.4 \times 10^{-11} \, \text{yr}^{-1}$ indicates significant star-forming activity relative to its stellar mass, possibly influenced by AGN feedback mechanisms.

NGC 4593 is positioned near the threshold between high-luminosity AGNs (with $\log_{10}(L_{\rm AGN}) \gtrsim 44$) and lower-luminosity AGNs. High-luminosity AGNs tend to show a strong positive correlation between SFR and $L_{\rm AGN}$, whereas lower-luminosity AGNs may exhibit a mildly negative correlation (cite: rosario2013mean). However, studies such as those by (cite: pitchford2016extreme) and (cite: hatziminaoglou2018multiplicity) indicate that AGN luminosity and SFR are not always strongly correlated, with some FIR-bright AGNs displaying signs of companions or mergers.

Our findings place NGC 4593 within the high-luminosity AGN regime. The AGN fraction relative to the IR luminosity is $0.87$, and its bolometric luminosity exceeds $10^{44}$ erg/s, highlighting the dominance of AGN activity in its SED. While this dominance indicates a significant AGN contribution to the galaxy’s IR emission, it does not imply a straightforward correlation between AGN luminosity and star formation processes. This result suggests that while AGN activity significantly influences the galaxy’s infrared emission, it may not directly drive star formation.

According to (cite: zhuang2023evolutionary), AGNs and their host galaxies evolve along specific trajectories on the black hole mass (M$_{\rm BH}$) versus stellar mass (M$_*$) plane. Galaxies above the M$_{\rm BH}$-M$_*$ relation typically grow horizontally with substantial stellar mass increases, while those on the relation evolve proportionally in both M$_{\rm BH}$ and M$_*$. Our analysis reveals that NGC 4593 aligns with this "horizontal path," suggesting that radiative-mode feedback cannot fully suppress star formation in such AGNs, and kinetic-mode feedback is insufficient to halt long-term star formation. The high AGN fraction and substantial stellar mass growth support the conclusion that radiative-mode feedback does not effectively constrain star formation in NGC 4593.

![](images/NGC4593_best_model.pdf)

## Challenges in kinematic modelling

Our analysis reveals a significant challenge in modelling the dynamics of NGC 4593 due to the clear presence of an m=1 feature, which indicates lopsidedness that the 3D-BAROLO model, which imposes axisymmetry, struggles to account for. This discrepancy suggests potential variations in fits between the northern and southern regions of the galaxy, which the model cannot adequately address. The proximity of the bar’s PA to the kinematic PA complicates the determination of true inclinations, potentially leading to systematic biases, especially in the presence of an outer ring, which is rarely circular. The assumption of circular orbits by 3D-BAROLO, when the orbits may actually be elongated, introduces further inaccuracies in the modelled inclination and fails to capture the lack of a velocity gradient in the modelled PV diagrams. Consequently, the radial velocities predicted by 3D-BAROLO cannot accurately reproduce the observed elongated orbits, as they assume isotropic motion, overlooking the complexities of elliptical orbits that do not conform to simple inflow or outflow patterns.

A critical limitation in our modelling is that the CO(2-1) line does not represent the entire molecular gas content, and relying solely on it could lead to an underestimation of the total molecular gas mass. Furthermore, the interferometric observations used in this study filter out extended emissions, resulting in missing flux, suggesting that the actual molecular gas mass could be higher than our model predicts.

This missing flux is particularly important in regions with significant non-circular motions, such as the areas affected by the bar and spiral arms, where the model’s limitations in capturing the full extent of gas dynamics are most evident. Additionally, the 3D-BAROLO model, with its inherent assumption of axisymmetry, cannot capture the entire molecular gas distribution, leading to the omission of the single arm of the galaxy in our analysis. This limitation underscores the need for a more comprehensive modelling approach to fully understand the gas dynamics in NGC 4593.

| Parameter | Value |
|:---|:---|
| $L_{\mathrm{IR,AGN}} / L_{\mathrm{IR,total}}$ | $0.876 \pm 0.052$ |
| $\log(L_{\mathrm{AGN,torus}}\, [\mathrm{erg\,s^{-1}}])$ | $36.193 \pm 0.049$ |
| $\log(L_{\mathrm{AGN,disc}}\, [\mathrm{erg\,s^{-1}}])$ | $36.096 \pm 0.116$ |
| $\log(L_{\mathrm{AGN,total\,dust}}\, [\mathrm{erg\,s^{-1}}])$ | $36.510 \pm 0.050$ |
| $\log(L_{\mathrm{AGN,6\,\mu m}}\, [\mathrm{erg\,s^{-1}}])$ | $35.784 \pm 0.048$ |
| $\log(L_{\mathrm{AGN,accretion\,power}}\, [\mathrm{erg\,s^{-1}}])$ | $36.492 \pm 0.047$ |
| $\log(L_{\mathrm{AGN,polar\,dust}}\, [\mathrm{erg\,s^{-1}}])$ | $36.224 \pm 0.057$ |
| $\log(L_{\mathrm{AGN}}\, [\mathrm{erg\,s^{-1}}])$ | $36.651 \pm 0.048$ |
| $\log(L_{\mathrm{stellar}}\, [\mathrm{erg\,s^{-1}}])$ | $37.402 \pm 0.035$ |
| $\log(M_*/M_\odot)$ | $10.633 \pm 0.039$ |
| $\log(M_{\mathrm{stellar\,gas}}\, [M_\odot])$ | $10.535 \pm 0.041$ |
| $\log(\mathrm{SFR}_{\mathrm{integrated}}\, [M_\odot\,\mathrm{yr}^{-1}])$ | $10.888 \pm 0.039$ |
| $\log(\mathrm{SFR}_{\mathrm{current}}\, [M_\odot\,\mathrm{yr}^{-1}])$ | $-0.367 \pm 0.045$ |
| $\log(\mathrm{SFR}_{100\,\mathrm{Myr}}\, [M_\odot\,\mathrm{yr}^{-1}])$ | $-0.329 \pm 0.042$ |
| $\log(\mathrm{SFR}_{10\,\mathrm{Myr}}\, [M_\odot\,\mathrm{yr}^{-1}])$ | $-0.364 \pm 0.045$ |

: CIGALE-derived parameters for NGC 4593

Table notes: CIGALE-derived parameters for NGC 4593, including luminosity components of the stellar population, active galactic nucleus (AGN), accretion disc, and dust structures (polar, torus, and total). SFRs reflect the current and past 10 and 100 million-year averages. These values are estimated based on CIGALE fitting results.

# Summary and conclusions

We used CO(2-1) observations from ALMA to study the kinematics and morphology of molecular gas in the Seyfert 1 AGN galaxy NGC 4593, which is a barred spiral galaxy. For this work, we used 3D-BAROLO and DISCFIT to analyse the gas kinematics and morphology. Additionally, we utilised multi-wavelength data to construct the SED of the galaxy using CIGALE. Our analysis revealed that the molecular gas mass in NGC 4593 is in the range $1.0 \sim 5.0 \times 10^8 \, M_{\odot}$, derived from the CO(1-0) line luminosity from the CO(2-1) using an excitation factor typical of active galaxies (cite: kamenetzky2016relations).

The gas distribution exhibits a one-arm structure, indicative of an $m = 1$ density wave or perturbation. Such a feature, rare in the nuclear regions of barred galaxies, suggests a dominant regular velocity field, implying limited non-circular motion. Yet, the evident $m = 1$ feature challenges the axisymmetry assumptions inherent in the 3D-BAROLO models.

The mass of the central SMBH was estimated based on the relationship between the CO line width ($W_{50}$) and SMBH mass. Our analysis yielded a BH mass of $\log \left( \frac{M_{\text{BH}}}{M_{\odot}} \right) = 6.89 \pm 0.04$, which aligns with previous estimates from reverberation mapping.

In the region about 2$^{\prime\prime}$ to 3$^{\prime\prime}$ ($\sim$ 220 pc) northeast of the galaxy centre (see Fig. [9](#fig:velocityfield)), we identified significant non-circular motion likely due to molecular gas outflow. This region contains between $(0.5 - 2.5) \times 10^7 \, M_{\odot}$ of gas, representing roughly 10% of the total galaxy flux. Perturbations in rotation velocity, radial velocity, surface density, and velocity dispersion confirm the presence of significant non-circular motion and molecular outflows. These findings align with observations by (cite: barbosa2006gemini), who noted similar perturbations in ionised gas kinematics.

The inner structure of NGC 4593 appears to be shaped by a CMZ-like ring in the innermost region of the galaxy. This ring, which could account for up to 20% of the total molecular gas mass, exhibits strong rotational motion with signs of non-circular inflow patterns. The bar-driven inflow mechanisms channel molecular gas into this CMZ-like ring, thereby affecting star formation and AGN activity in the central region. This prominent bar structure significantly influences the gas dynamics.

The SED fitting using CIGALE confirmed the presence of a strong AGN component in NGC 4593. The AGN fraction to IR luminosity is $0.87$, underscoring the significant impact of the AGN on the galaxy’s overall spectrum. The inferred star formation rate is not large, which might suggest the suppression of star formation processes because of AGN quenching. NGC 4593 fits well within the high-luminosity AGN regime, with a bolometric luminosity above $10^{44}$ erg/s. The galaxy’s stellar mass growth suggests that radiative-mode feedback is ineffective in fully suppressing star formation. Instead, the AGN activity remains tightly linked with star formation, consistent with the coevolution trajectory outlined by (cite: zhuang2023evolutionary).

NGC 4593 exhibits complex gas dynamics due to the interplay between bar dynamics and AGN activity. The presence of a CMZ-like ring and significant molecular outflows highlight the impact of non-axisymmetric bar potentials on shaping gas dynamics.

# Acknowledgements

This paper makes use of data from ALMA program ADS/JAO.ALMA#2017.1.00236.S and ADS/JAO.ALMA#2018.1.00576.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSTC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. KK acknowledges the support of the European Southern Observatory (ESO) through the SSDF grant, which facilitated a visit to ESO contributing to this work. CR acknowledges support from Fondecyt Regular grant 1230345 and ANID BASAL project FB210003. JAFO acknowledges financial support by the Spanish Ministry of Science and Innovation (MCIN/AEI/10.13039/501100011033), by “ERDF A way of making Europe” and by “European Union NextGenerationEU/PRTR” through the grants PID2021-124918NB-C44 and CNS2023-145339; MCIN and the European Union – NextGenerationEU through the Recovery and Resilience Facility project ICTS-MRR-2021-03-CEFCA. MPS acknowledges support from grants RYC2021-033094-I and CNS2023-145506 funded by MCIN/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. PA warmly thanks the Department of Physics, Section of Astrophysics, Astronomy and Mechanics of the Aristotle University of Thessaloniki (Greece), the Institute of Theoretical Astrophysics, University of Oslo (Norway), and the Fukui University of technology, Fukui (Japan) for their hospitality when part of this work was written.

134 natexlab

(ref: andreani2018extreme) Andreani, P., Retana-Montenegro, E., Zhang, Z.-Y., et al. 2018, A&A, 615, A142

(ref: ann2005formation) Ann, H. & Thakur, P. 2005, ApJ, 620, 197

(ref: antonucci1985spectropolarimetry) Antonucci, R. & Miller, J. 1985, AJ, Part 1 (ISSN 0004-637X), vol. 297, Oct. 15, 1985, p. 621-632., 297, 621

(ref: arakawa2022radiation) Arakawa, N., Fabian, A., Ferland, G., & Ishibashi, W. 2022, MNRAS, 517, 5069

(ref: armillotta2020life) Armillotta, L., Krumholz, M. R., & Di Teodoro, E. M. 2020, MNRAS, 493, 5273

(ref: asmus2014subarcsecond) Asmus, D., Hönig, S., Gandhi, P., Smette, A., & Duschl, W. 2014, MNRAS, 439, 1648

(ref: Athanassoula1992) Athanassoula, E. 1992, MNRAS, 259, 345

(ref: atlee2011multi) Atlee, D. W., Martini, P., Assef, R. J., Kelson, D. D., & Mulchaey, J. S. 2011, ApJ, 729, 22

(ref: bally1987galactic) Bally, J., Stark, A. A., Wilson, R. W., & Henkel, C. 1987, ApJS (ISSN 0067-0049), vol. 65, Sept. 1987, p. 13-82., 65, 13

(ref: barbosa2006gemini) Barbosa, F. K. B., Storchi-Bergmann, T., Fernandes, R. C., Winge, C., & Schmitt, H. 2006, MNRAS, 371, 170

(ref: bean2022casa) Bean, B., Bhatnagar, S., Castro, S., et al. 2022, PASP, 134, 114501

(ref: Asnakew) Bewketu Belete, A., Andreani, P., Fernández-Ontiveros, J. A., et al. 2021, A&A, 654, A24

(ref: bolatto2013co) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: boquien2019cigale) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: bouquin2018galex) Bouquin, A. Y., de Paz, A. G., Muñoz-Mateos, J. C., et al. 2018, ApJS, 234, 18

(ref: brusa2017molecular) Brusa, M. 2017, in Workshop sull’Astronomia Millimetrica in Italia, 24

(ref: bruzual2003stellar) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: cackett2019comparison) Cackett, E. 2019, AAS/High Energy Astrophysics Division, 17, 106

(ref: cackett2018accretion) Cackett, E. M., Chiang, C.-Y., McHardy, I., et al. 2018, ApJ, 857, 53

(ref: calzetti2000dust) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: cicone2014massive) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: ciesla2015constraining) Ciesla, L., Charmandaris, V., Georgakakis, A., et al. 2015, A&A, 576, A10

(ref: combes2017agn) Combes, F. 2017, Front. Astron. Space Sci., 4, 10

(ref: contini1998starbursts) Contini, T., Considere, S., & Davoust, E. 1998, Astron. Astrophys. Suppl. Ser., 130, 285

(ref: contursi2013spectroscopic) Contursi, A., Poglitsch, A., Carpio, J. G., et al. 2013, A&A, 549, A118

(ref: cutri2012explanatory) Cutri, R., Wright, E., Conrow, T., et al. 2012, Explanatory Supplement to the WISE All-Sky Data Release Products, 1

(ref: dale2014two) Dale, D. A., Helou, G., Magdis, G. E., et al. 2014, ApJ, 784, 83

(ref: davis2013atlas3d) Davis, T. A., Alatalo, K., Bureau, M., et al. 2013, MNRAS, 429, 534

(ref: deVaucouleurs1991) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, J., et al. 1991, Third reference catalogue of bright galaxies (Springer)

(ref: de2013third) De Vaucouleurs, G., de Vaucouleurs, A., Harold Jr, G., et al. 2013, Third Reference Catalogue of Bright Galaxies: Volume III, Vol. 3 (Springer Science & Business Media)

(ref: den2020muse) den Brok, M., Carollo, C. M., Erroz-Ferrer, S., et al. 2020, MNRAS, 491, 4089

(ref: denney2006mass) Denney, K. D., Bentz, M. C., Peterson, B. M., et al. 2006, ApJ, 653, 152

(ref: di20153d) Di Teodoro, E. & Fraternali, F. 2015, ASCL, ascl

(ref: esposito2022agn) Esposito, F., Vallini, L., Pozzi, F., et al. 2022, MNRAS, 512, 686

(ref: fabian2012observational) Fabian, A. C. 2012, ARA & A, 50, 455

(ref: fanidakis2012evolution) Fanidakis, N., Baugh, C., Benson, A., et al. 2012, MNRAS, 419, 2797

(ref: fernandez2020co) Fernández-Ontiveros, J., Dasyra, K., Hatziminaoglou, E., et al. 2020, A&A, 633, A127

(ref: Juan+20) Fernández-Ontiveros, J. A., Dasyra, K. M., Hatziminaoglou, E., et al. 2020, A&A, 633, A127

(ref: fernandez2016far) Fernández-Ontiveros, J. A., Spinoglio, L., Pereira-Santaella, M., et al. 2016, ApJS, 226, 19

(ref: feruglio2010quasar) Feruglio, C., Maiolino, R., Piconcelli, E., et al. 2010, A&A, 518, L155

(ref: fiore2017agn) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: fluetsch2019cold) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: fraternali2002deep) Fraternali, F., van Moorsel, G., Sancisi, R., & Oosterloo, T. 2002, AJ, 123, 3124

(ref: alexei2008image) Gadotti, D. A. 2008, MNRAS, 384, 420

(ref: gaspari2020linking) Gaspari, M., Tombesi, F., & Cappi, M. 2020, Nat. Astron., 4, 10

(ref: girdhar2022quasar) Girdhar, A., Harrison, C., Mainieri, V., et al. 2022, MNRAS, 512, 1608

(ref: gitti2012evidence) Gitti, M., Brighenti, F., & McNamara, B. R. 2012, Adv. Astron., 2012

(ref: gutcke2015sfr) Gutcke, T. A., e. a. 2015, MNRAS, 451, 3759

(ref: harrison2013impact) Harrison, C. 2013, IAU Proc., 9, 284

(ref: harrison2017impact) Harrison, C. 2017, Nat. Astron., 1, 0165

(ref: hatchfield2021dynamically) Hatchfield, H. P., Sormani, M. C., Tress, R. G., et al. 2021, ApJ, 922, 79

(ref: hatziminaoglou2018multiplicity) Hatziminaoglou, E., Farrah, D., Humphreys, E., et al. 2018, MNRAS, 480, 4974

(ref: hatziminaoglou2010hermes) Hatziminaoglou, E., Omont, A., Stevens, J., et al. 2010, A&A, 518, L33

(ref: heckman2004present) Heckman, T. M., Kauffmann, G., Brinchmann, J., et al. 2004, ApJ, 613, 109

(ref: hensley2014grain) Hensley, B. S., Ostriker, J. P., & Ciotti, L. 2014, ApJ, 789, 78

(ref: hickox2018obscured) Hickox, R. C. & Alexander, D. M. 2018, ARA&A, 56, 625

(ref: hopkins2005black) Hopkins, P. F., Hernquist, L., Cox, T. J., et al. 2005, ApJ, 630, 705

(ref: hopkins2012stellar) Hopkins, P. F., Quataert, E., & Murray, N. 2012, MNRAS, 421, 3522

(ref: horst2009mid) Horst, H., Duschl, W. J., Gandhi, P., & Smette, A. 2009, A&A, 495, 137

(ref: horst2008mid) Horst, H., Gandhi, P., Smette, A., & Duschl, W. J. 2008, A&A, 479, 389

(ref: horst2006small) Horst, H., Smette, A., Gandhi, P., & Duschl, W. 2006, A&A, 457, L17

(ref: hunt2008molecular) Hunt, L. K., Combes, F., Garcı́a-Burillo, S., et al. 2008, A&A, 482, 133

(ref: ishibashi2015agn) Ishibashi, W. & Fabian, A. C. 2015, MNRAS, 451, 93

(ref: jarrett20032mass) Jarrett, T., Chester, T., Cutri, R., Schneider, S., & Huchra, J. 2003, AJ, 125, 525

(ref: just2007x) Just, D. W., Brandt, W., Shemmer, O., et al. 2007, ApJ, 665, 1004

(ref: kamenetzky2018recovering) Kamenetzky, J., Privon, G., & Narayanan, D. 2018, ApJ, 859, 9

(ref: kamenetzky2016relations) Kamenetzky, J., Rangwala, N., Glenn, J., Maloney, P., & Conley, A. 2016, ApJ, 829, 93

(ref: kammoun2021modelling) Kammoun, E., Papadakis, I., & Dovčiak, M. 2021, MNRAS, 503, 4163

(ref: karouzos2014tale) Karouzos, M., Im, M., Trichas, M., et al. 2014, ApJ, 784, 137

(ref: kauffmann2000unified) Kauffmann, G. & Haehnelt, M. 2000, MNRAS, 311, 576

(ref: kennicutt1998global) Kennicutt Jr, R. C. 1998, ApJ, 498, 541

(ref: kormendy2006pseudobulges) Kormendy, J., Cornell, M. E., Block, D. L., Knapen, J. H., & Allard, E. L. 2006, ApJ, 642, 765

(ref: koss2021bat) Koss, M. J., Strittmatter, B., Lamperti, I., et al. 2021, ApJS, 252, 29

(ref: kumari2023contrasting) Kumari, K., Dewangan, G., Papadakis, I., et al. 2023, MNRAS, 521, 4109

(ref: laine2001ngc) Laine, S. 2001, Ap&SS, 276, 667

(ref: leitherer2002ultraviolet) Leitherer, C., Calzetti, D., & Martins, L. P. 2002, ApJ, 574, 114

(ref: li2021kinematic) Li, A., Marasco, A., Fraternali, F., Trager, S., & Verheijen, M. A. 2021, MNRAS, 504, 3013

(ref: lutz2020molecular) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134

(ref: malkan1998hubble) Malkan, M. A., Gorjian, V., & Tam, R. 1998, ApJS, 117, 25

(ref: marasco2019halogas) Marasco, A., Fraternali, F., Heald, G., et al. 2019, A&A, 631, A50

(ref: marinova2007characterizing) Marinova, I. & Jogee, S. 2007, ApJ, 659, 1176

(ref: mcalary1983near) McAlary, C. W., McLaren, R., McGonegal, R., & Maza, J. 1983, ApJS, 52, 341

(ref: mcnamara2007heating) McNamara, B. & Nulsen, P. 2007, Annu. Rev. Astron. Astrophys., 45, 117

(ref: mordini2021calibration) Mordini, S., Spinoglio, L., & Fernández-Ontiveros, J. A. 2021, A&A, 653, A36

(ref: morganti2017many) Morganti, R. 2017, Front. Astron. Space Sci., 4, 42

(ref: morris1983temperature) Morris, M., Polish, N., Zuckerman, B., & Kaifu, N. 1983, AJ (ISSN 0004-6256), vol. 88, Aug. 1983, p. 1228-1235., 88, 1228

(ref: mountrichas2021galaxy) Mountrichas, G., Buat, V., Georgantopoulos, I., et al. 2021, A&A, 653, A70

(ref: Mulchaey1997) Mulchaey, J. S. & Regan, M. W. 1997, ApJL, 482, L135

(ref: newman2012sins) Newman, S. F., Genzel, R., Förster-Schreiber, N. M., et al. 2012, ApJ, 761, 43

(ref: papadopoulos2010co) Papadopoulos, P. P., Van der Werf, P., Isaak, K., & Xilouris, E. M. 2010, ApJ, 715, 775

(ref: patra2020theoretical) Patra, N. N. 2020, A&A, 638, A66

(ref: phookun1993ngc) Phookun, B., Vogel, S. N., & Mundy, L. G. 1993, Astrophysical Journal v. 418, p. 113, 418, 113

(ref: pier1992infrared) Pier, E. A. & Krolik, J. H. 1992, Astrophysical Journal, Part 1 (ISSN 0004-637X), vol. 401, no. 1, p. 99-109., 401, 99

(ref: pitchford2016extreme) Pitchford, L., Hatziminaoglou, E., Feltre, A., et al. 2016, MNRAS, 462, 4067

(ref: ricci2022bass) Ricci, C., Ananna, T. T., Temple, M. J., et al. 2022, ApJ, 938, 67

(ref: ricci2017bat) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017a, ApJS, 233, 17

(ref: ricci2017close) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017b, Nature, 549, 488

(ref: rosario2013mean) Rosario, D., Santini, P., Lutz, D., et al. 2013, A&A, 560, A72

(ref: rosario2019accreting) Rosario, D. J., Togi, A., Burtscher, L., et al. 2019, ApJ Letters, 875, L8

(ref: rush1993extended) Rush, B., Malkan, M. A., & Spinoglio, L. 1993, ApJS, 89, 1

(ref: salome2023star) Salomé, Q., Krongold, Y., Longinotti, A. L., et al. 2023, MNRAS, 524, 3130

(ref: sanders2022mira) Sanders, J. L., Matsunaga, N., Kawata, D., et al. 2022, MNRAS, 517, 257

(ref: schawinski2007observational) Schawinski, K., Thomas, D., Sarzi, M., et al. 2007, MNRAS, 382, 1415

(ref: schnorr2014feeding) Schnorr-Müller, A., Storchi-Bergmann, T., Nagar, N. M., et al. 2014, MNRAS, 437, 1708

(ref: schombert2019mass) Schombert, J., McGaugh, S., & Lelli, F. 2019, MNRAS, 483, 1496

(ref: shaw1995nuclear) Shaw, M., Axon, D., Probst, R., & Gatley, I. 1995, MNRAS, 274, 369

(ref: silk1998quasars) Silk, J. & Rees, M. J. 1998, arXiv preprint astro-ph/9801013

(ref: skrutskie2006two) Skrutskie, M., Cutri, R., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: smith2021wisdom) Smith, M. D., Bureau, M., Davis, T. A., et al. 2021, MNRAS, 500, 1933

(ref: soding2024spatially) Söding, L., Edenhofer, G., Enßlin, T. A., et al. 2024, arXiv preprint arXiv:2407.02859

(ref: solomon2005molecular) Solomon, P. & Vanden Bout, P. 2005, Annu. Rev. Astron. Astrophys., 43, 677

(ref: sormani2019mass) Sormani, M. C. & Barnes, A. T. 2019, MNRAS, 484, 1213

(ref: spekkens2007modeling) Spekkens, K. & Sellwood, J. 2007, ApJ, 664, 204

(ref: spingola2019erratum) Spingola, C., McKean, J., Auger, M., et al. 2019, MNRAS, 482, 1247

(ref: spinoglio1995multiwavelength) Spinoglio, L., Malkan, M. A., Rush, B., Carrasco, L., & Recillas-Cruz, E. 1995, arXiv preprint astro-ph/9506139

(ref: sriram2009energy) Sriram, K., Agrawal, V., & Rao, A. 2009, ApJ, 700, 1042

(ref: stalevski2016dust) Stalevski, M., Ricci, C., Ueda, Y., et al. 2016, MNRAS, 458, 2288

(ref: stuber2021frequency) Stuber, S. K., Saito, T., Schinnerer, E., et al. 2021, A&A, 653, A172

(ref: sun2018cloud) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172

(ref: thakur2009effect) Thakur, P., Ann, H., & Jiang, G. 2009, ApJ, 693, 586

(ref: tiley2016tully) Tiley, A. L., Bureau, M., Saintonge, A., et al. 2016, MNRAS, 461, 3494

(ref: tombesi2015wind) Tombesi, F., Meléndez, M., Veilleux, S., et al. 2015, Nature, 519, 436

(ref: tommasin2010spitzer) Tommasin, S., Spinoglio, L., Malkan, M. A., & Fazio, G. 2010, ApJ, 709, 1257

(ref: torii2013detailed) Torii, K., Enokiya, R., Fukui, Y., et al. 2013, IAU Proc., 9, 106

(ref: tress2024magnetic) Tress, R., Sormani, M., Girichidis, P., et al. 2024, arXiv preprint arXiv:2403.13048

(ref: van2010black) van der Werf, P. P., Isaak, K., Meijerink, R., et al. 2010, A&A, 518, L42

(ref: veilleux2020cool) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, The A&A Review, 28, 1

(ref: venanzi2020role) Venanzi, M., Hönig, S., & Williamson, D. 2020, ApJ, 900, 174

(ref: wang2022density) Wang, Y., He, Z., Mao, J., et al. 2022, ApJ, 928, 7

(ref: weiss2005multiple) Weiß, A., Downes, D., Walter, F., & Henkel, C. 2005, A&A, 440, L45

(ref: wu2021morphological) Wu, Y.-T., Trejo, A., Espada, D., & Miyamoto, Y. 2021, MNRAS, 504, 3111

(ref: yang2022fitting) Yang, G., Boquien, M., Brandt, W. N., et al. 2022, ApJ, 927, 192

(ref: yang2020x) Yang, G., Boquien, M., Buat, V., et al. 2020, MNRAS, 491, 740

(ref: zhuang2023evolutionary) Zhuang, M.-Y. & Ho, L. C. 2023, ApJ, 945, 154

[^1]:

[^2]: Deceased: It is with profound sadness we note the passing of our esteemed colleague, M. Malheiro, who made significant contributions to this work.

</paper>

Write the methods card for this paper.