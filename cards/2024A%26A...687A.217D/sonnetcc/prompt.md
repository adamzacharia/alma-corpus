# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...687A.217D\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...687A.217D",
 "title": "ALMA-IMF. XII. Point-process mapping of 15 massive protoclusters",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Dell'Ova, P.",
 "n_authors": 32,
 "arxiv_id": "2407.07610",
 "doi": "10.1051/0004-6361/202348984",
 "alma_projects_linked_by_archive": [
  "2013.1.01365.S",
  "2015.1.01273.S",
  "2017.1.01355.L"
 ]
}
```

Paper text:
<paper>
# ALMA-IMF XII: Point-process mapping of 15 massive protoclusters[^1]

A crucial aspect in addressing the challenge of measuring the core mass function (CMF), that is pivotal for comprehending the origin of the initial mass function (IMF), lies in constraining the temperatures of the cores.

We aim to measure the luminosity, mass, column density and dust temperature of star-forming regions imaged by the ALMA-IMF large program. These fields were chosen to encompass early evolutionary stages of massive protoclusters. High angular resolution mapping is required to capture the properties of protostellar and pre-stellar cores within these regions, and to effectively separate them from larger features, such as dusty filaments.

We employed the point process mapping (PPMAP) technique, enabling us to perform spectral energy distribution fitting of far-infrared and submillimeter observations across the 15 ALMA-IMF fields, at an unmatched 2.5$^{\prime \prime}$ angular resolution. By combining the modified blackbody model with near-infrared data, we derived bolometric luminosity maps. We estimated the errors impacting values of each pixel in the temperature, column density, and luminosity maps. Subsequently, we employed the extraction algorithm *getsf* on the luminosity maps in order to detect luminosity peaks and measure their associated masses.

We obtained high-resolution constraints on the luminosity, dust temperature, and mass of protoclusters, that are in agreement with previously reported measurements made at a coarser angular resolution. We find that the luminosity-to-mass ratio correlates with the evolutionary stage of the studied regions, albeit with intra-region variability. We compiled a PPMAP source catalog of 313 luminosity peaks using *getsf* on the derived bolometric luminosity maps. The PPMAP source catalog provides constraints on the mass and luminosity of protostars and cores, although one source may encompass several objects. Finally, we compare the estimated luminosity-to-mass ratio of PPMAP sources with evolutionary tracks and discuss the limitations imposed by the 2.5$^{\prime \prime}$ beam.

# Introduction

![image](images/SED-coverage.pdf)

The Atacama large millimeter array – initial mass function (ALMA-IMF[^2]) large program surveyed massive protoclusters of the Milky Way ($2.5 - 33 \times 10^3 M_\odot$, see paper I by (cite: Motte2022)). With distances spanning from 2 to 5.5 kpc, performing interferometric observations with ALMA was paramount to trace the dust and gas emission at a scale that probes the formation and evolution of pre-stellar cores and protostars in the dense gas of dusty filaments (see paper II by (cite: Ginsburg2022) and paper VII by (cite: Cunningham2023)). Measuring the mass and thus the temperature of these structures is essential to understand the conditions in which stars form, and to constrain the core mass function (hereafter CMF), since the estimated core masses may vary substantially depending on the adopted temperature. In addition to the spectrum of masses, measuring the bolometric luminosity is indispensable to build the luminosity-to-mass ratio, a fundamental quantity that can be related to the evolutionary stage of protostellar objects ((cite: Motte2001); (cite: Elia2010); (cite: Csengeri2016); (cite: Mottram2017)). One of the challenges faced by the ALMA-IMF program is that millimeter observations, on their own, are insufficient to measure the bolometric luminosity. This paper addresses all of these issues and provides high-resolution (2.5$^{\prime \prime}$) column density, temperature, and luminosity maps based on a multiwavelength approach.

Constraining the bolometric luminosity, dust column density, and temperature requires the spectral energy distribution (hereafter SED) of dust grains to be modeled. While it is possible to accurately describe the scattering, absorption, and reemission of starlight through the dusty interstellar medium, phenomenological approximations are more practical in most cases (see (cite: Galliano2018), and references therein). The modified blackbody (MBB) description, a widely used approximation, allows such measurements to be inferred from an analysis of the far-infrared (hereafter FIR, $70 \leq \lambda \leq 500 ~\upmu$m) and millimeter fluxes (see Fig. [\[fig:SED-coverage\]](#fig:SED-coverage), bottom panel). Assuming that the majority of the dust mass is in large grains ($r> 0.02~\upmu$m, (cite: Galliano2018)), and that these grains are in thermal equilibrium (because of their large enthalpy), both the mass $M_\mathrm{dust}$ and temperature $T_\mathrm{dust}$ can be measured through SED fitting based on the following equation: $$\begin{equation}
L_\lambda = M_\mathrm{dust} \kappa_0 \left( \frac{\lambda}{ \lambda_0} \right)^{-\beta} 4\pi B_\lambda (T_\mathrm{dust}),
\end{equation}$$ where $L_\lambda$ ($\mathrm{W~m^{-1}}$) is the monochromatic luminosity, $\kappa_0$ ($\mathrm{kg^{-1}}$) the dust mass absorption coefficient, $\beta$ the opacity index (both tied to the dust grains’ physical and chemical properties), $\lambda$ the wavelength, and $B_\lambda$ the Planck function. It should be noted, however, that the MBB description cannot reproduce the dust emission at shorter wavelengths ($\lambda < 70 ~\upmu$m), since the stochastic heating of very small grains and the contribution of aromatic features ((cite: Duley&Williams1981); (cite: Leger&Puget1984); (cite: Allamandola1985)) result in a departure from the Planck function (see Fig. [\[fig:SED-coverage\]](#fig:SED-coverage), bottom panel). In this paper, we do not attempt to accurately model the mid- and near-infrared domain of the dust SED ($1 \leq \lambda \leq 70 ~\upmu$m), and instead focus on the emission of dust grains in thermal equilibrium. To this end, a thorough sampling of the SED above 70 $\upmu$m is required to constrain both $M_\mathrm{dust}$ and $T_\mathrm{dust}$ through SED fitting, in particular in the 70-250 $\upmu$m range, since the peak of the SED traces the dust temperature and opacity index.

We acknowledge that this method is subject to biases, since line-of-sight variations of the temperature and measurement noise can induce a degeneracy between $T_\mathrm{dust}$ and $\beta$ ((cite: Shetty2009); (cite: Kelly2012); (cite: Galliano2018)). Including observations longward of 250 $\upmu$m can help to alleviate this issue. Several observatories can provide such FIR and millimeter measurements, namely *Herschel*, SOFIA, APEX and ALMA (see Sect. [2](#sect:observations) and Table [\[table:ObservationSummary\]](#table:ObservationSummary)). Relying on a diversity of instruments and bands immediately poses a problem, illustrated in the top panel of Fig. [\[fig:SED-coverage\]](#fig:SED-coverage): while the angular resolution of ALMA observations such as performed for the ALMA-IMF program lies between $0.29\ensuremath{''} \times 0.26$$''$ and $1.52\ensuremath{''} \times 1.30$$''$, the angular resolution of *Herschel*/SPIRE ranges from 17.6$^{\prime \prime}$ (at 250 $\upmu$m) to 35.2$^{\prime \prime}$ (at 500 $\upmu$m). The standard procedure (e.g., (cite: Galametz2012); (cite: Aniano2012); (cite: Giannetti2013); (cite: Kohler2014); (cite: Guzman2015)) for SED fitting involves smoothing the observations to the same angular resolution, that is, to the coarsest resolution (35.2$^{\prime \prime}$, in our case). Applying this smoothing procedure would entirely defeat the purpose of high-angular ALMA observations, undermining the immense usefulness of high resolution long wavelength data. Alternatively, Fourier-space combination of *Herschel* images with ground-based single-dish bolometer data would allow to work at an intermediate resolution, but the improved angular resolution attained with this technique remains coarse with respect to ALMA observations (e.g., $10^{\prime \prime}$, (cite: Lin2016; Lin2017); $18^{\prime \prime}$, (cite: Palmeirim2013); (cite: Konyves2020); (cite: Ladjelate2020)).

To address this issue and retain the high-angular resolution information from ALMA observations, we employ the point process mapping (PPMAP) algorithm developed by (cite: Marsh2015). PPMAP allows us to combine and reproduce multiwavelength observations using the MBB description while preserving the spatial information contained in the higher angular scale maps. Recently, PPMAP was applied to reveal and constrain dust structures in supernova remnants ((cite: Chawner2019); (cite: Chawner2020)), star-forming filaments ((cite: Howard2019); (cite: Howard2021)) and in the Milky Way disk (cite: Bates2023). All these studies were based on *Herschel* observations, and some included SCUBA-2 data (cite: Holland2013). For the first time, (cite: Motte2018b) advanced PPMAP so far as to simultaneously fit observations from a data set that spanned two orders of magnitudes in angular resolution (from $0.37^{\prime \prime} \times 0.53^{\prime \prime}$ to $35.2^{\prime \prime}$). The results they achieved with a $2.5^{\prime \prime}$ resolution in the massive W43-MM1 protocluster compelled us to apply this novel procedure to the analysis of the 15 ALMA-IMF fields. Through PPMAP, we perform SED fitting for a large set of continuum observations, while preserving the high-angular resolution capabilities of ALMA, providing a first step toward constraining the luminosity, column density, and temperature of the population of candidate cores and protostars.

In Sect. [2](#sect:observations), we present the ALMA and complementary continuum observations toward the ALMA-IMF protoclusters. We then proceed to the analysis in Sect. [3](#sect:PPMAP), where we describe the PPMAP algorithm and the methods used to apply it to our specific problem. The derived luminosity, dust temperature and column density maps are presented and compared with previous studies in Sect. [4](#sect:calibration). Lastly, the construction of a PPMAP luminosity peaks catalog, encompassing luminosity and mass measurements, is detailed in Sect. [5](#sect:discussion), in which we discuss our findings.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |
| Survey | Wavelength | Angular resolution | Spatial coverage | Reference(s) |  |  |
|  | ($\upmu$m) | (arcsec) |  |  |  |  |
|  |  |  |  |  |  |  |
| ALMA-IMF |  |  |  |  |  |  |
| 1-1 |  |  |  |  |  |  |
| Band 6$^1$ | 1300 | $0.35 \times 0.27 - 1.09 \times 0.70^2$ | $\sim 1^\prime \times 1^\prime$ | Galván-Madrid et al. (in prep.), |  |  |
| Band 3$^3$ | 3000 | $0.29 \times 0.26 - 1.52 \times 1.30^2$ |  | and (cite: Diaz2023) |  |  |
| APEX |  |  |  |  |  |  |
| 1-1 |  |  |  |  |  |  |
| SABOCA | 350 | 7.8 | $\sim 2^\prime \times 2^\prime$ | (cite: Lin2019) |  |  |
| LABOCA | 870 | 19.2 | \> $1^\circ \times 1^\circ$ | (cite: Schuller2009), (cite: Csengeri2014) |  |  |
| Hi-GAL$+$HOBYS (*Herschel*) |  |  |  |  |  |  |
| 1-1 |  |  |  |  |  |  |
| PACS | 70 | 5.6 | \> $1^\circ \times 1^\circ$ | (cite: Molinari2010), |  |  |
| PACS | 160 | 10.7 |  | (cite: Motte2010) |  |  |
| SPIRE | 250 | 17.6 |  |  |  |  |
| SPIRE | 350 | 23.9 |  |  |  |  |
| SPIRE | 500 | 35.2 |  |  |  |  |
| SOFIA |  |  |  |  |  |  |
| 1-1 |  |  |  |  |  |  |
| HAWC+ | 53 | 4.85 | $\sim 3^\prime \times 3^\prime$ | (cite: Vaillancourt2016), |  |  |
| HAWC+ | 89 | 7.8 |  | (cite: Pillai2023) |  |  |
| HAWC+ | 214 | 18.2 |  |  |  |  |
| MIPSGAL (*Spitzer*) |  |  |  |  |  |  |
| 1-1 |  |  |  |  |  |  |
| MIPS | 24 | 5.6 | \> $1^\circ \times 1^\circ$ | (cite: Carey2009) |  |  |
| GLIMPSE (*Spitzer*) |  |  |  |  |  |  |
| 1-1 |  |  |  |  |  |  |
| IRAC | 3.6 | 1.7 | \> $1^\circ \times 1^\circ$ | (cite: Benjamin2003) |  |  |
| IRAC | 4.5 | 1.7 |  |  |  |  |
| IRAC | 5.8 | 1.9 |  |  |  |  |
| IRAC | 8.0 | 2.0 |  |  |  |  |

|  |
|:---|
| $^1$As reported in Sect. [2.1](#subsect:ALMAobs), Band 6 observations decontaminated from free-free emission were used in our analysis (Galván-Madrid et al., in prep.). |
| $^2$We indicate both the best (first) and coarsest (second) angular resolutions obtained with the ALMA-IMF observations. |
| $^3$ALMA Band 3 observations were not used in the PPMAP analysis, in order to prevent contamination by free-free emission (see Sect. [6.1.3](#sect:free-free)). |

# Observations

In addition to the new observations obtained with the ALMA, the modified blackbody SED fitting analysis requires far-infrared data. To cover the necessary wavelength range between 70 $\upmu$m and 870 $\upmu$m, we have gathered observations from five different instruments. Additional mid- and near-infrared observations are required to derive bolometric luminosities. The details of these observations, along with the corresponding instruments, are provided in Table [\[table:ObservationSummary\]](#table:ObservationSummary) and shown in Fig. [1](#fig:datacompleteness). To complete the sampling of the SED below 70 $\upmu$m and estimate the bolometric luminosity (see Sect. [3.3](#subsect:luminosity)), we have also collected archival observations between 3.6 $\upmu$m and 24 $\upmu$m. In the following subsections, we present these different observations and the corresponding instruments in detail.

![](images/coverage.pdf)

## ALMA-IMF images

We used the continuum images presented in (cite: Diaz2023). These images are the result of combining the 3 mm (Band 3) and 1 mm (Band 6) ALMA-IMF continuum images presented in Paper I (cite: Motte2022) and Paper II (cite: Ginsburg2022) with the pilot of the Mustang-2 Galactic plane survey (MGPS90, (cite: Ginsburg2020)) at 3 mm and the Bolocam Galactic plane survey (BGPS, (cite: Aguirre2011), (cite: Ginsburg2013)). The more evolved ALMA-IMF fields have a significant contribution of free-free emission in the continuum images. To aid our photometry measurements, we also used the estimates of pure dust emission presented in Galván-Madrid et al. (in prep.), which subtract the free-free contribution to the continuum at 1 mm using the H$41\alpha$ recombination line within the ALMA-IMF data set. Section [6.1.3](#sect:free-free) provide further details about this procedure. The absolute flux calibration for the ALMA observations is estimated to have an uncertainty of 10% as reported by (cite: Ginsburg2022).

## ATLASGAL & APEX/SABOCA observations

The ALMA-IMF regions were mapped by the APEX telescope large area survey of the Galaxy (ATLASGAL, (cite: Schuller2009)). APEX/LABOCA observations provide a 870 $\upmu$m data point at an angular resolution similar to *Herschel*/SPIRE observations at 250 $\upmu$m (see Table [\[table:ObservationSummary\]](#table:ObservationSummary)). Furthermore, 12 out of 15 ALMA-IMF regions were mapped by APEX/SABOCA at 350 $\upmu$m (cite: Lin2019). The absolute flux calibration uncertainties on SABOCA and LABOCA observations are estimated to be 20% and 15%, respectively ((cite: Lin2019); (cite: Contreras2013)).

## Hi-GAL survey

The ALMA-IMF regions have also been extensively mapped by the *Herschel* infrared Galactic plane survey (Hi-GAL, (cite: Molinari2010)). Moreover, W43 was also imaged in the high-gain mode of PACS and SPIRE by HOBYS, a key imaging survey with *Herschel* ((cite: Motte2010); (cite: NguyenLuong2013)), to correct the field for saturation. The combination of PACS and SPIRE observations provides data points from 70 $\upmu$m to 500 $\upmu$m. However, it is worth noting that some Hi-GAL maps contain ‘‘NaN” (Not-a-Number) values, that correspond to pixels that are saturated. For instance, in the PSW band (250 $\upmu$m) observations of the G012.80 (W33) region, there are 154 saturated pixels according to Table B.1 in (cite: Molinari2016). To address this issue, we have applied interpolation to replace the values of these saturated pixels. This interpolation process was performed using Gaussian process regression, as implemented in the `astrofix` `Python` package ((cite: Zhang2021)), described in Appendix [6](#appendix:PPMAP). The extent of pixel replacement through interpolation is visualized in Fig. [1](#fig:datacompleteness). When observations reach saturation levels that preclude interpolation, an alternative approach is to substitute them with SABOCA and/or SOFIA observations (Sect. [2.4](#sect:SOFIA)). This solution is generally applicable, except in the case of G333.60, where the *Herschel*/SPIRE image at 250 $\upmu$m is saturated, but there are not SOFIA observations at 214 $\upmu$m (as shown in Fig. [1](#fig:datacompleteness), sixth row). This makes G333 the least constrained region within our study. For *Herschel*/PACS and *Herschel*/SPIRE observations, the absolute flux calibration uncertainties are estimated to be 10% and 7%, respectively, as reported by (cite: Galametz2014).

## SOFIA/HAWC+ observations

G012.80, G351.77, W51-E, and W51-IRS underwent observations at 53, 89, and 214 $\upmu$m, conducted by (cite: Vaillancourt2016) and (cite: Pillai2023), employing the 2.7 m stratospheric observatory for infrared astronomy (SOFIA) telescope (cite: Temi2018). These observations used the High-resolution Airborne Wideband Camera-plus (HAWC+; (cite: Harper2018)). In our analysis of the G012.80, G351.77, W51-E, and W51-IRS dust emission, the SOFIA/HAWC+ data were employed to better sample the mid-infrared portion of the SED and to replace saturated *Herschel*/SPIRE 250 $\upmu$m maps. The absolute flux calibration uncertainties for SOFIA observations are estimated at 15% for 53 $\upmu$m and 89 $\upmu$m, and 20% for 214 $\upmu$m (cite: Chuss2019).

## *Spitzer* surveys

The ALMA-IMF protoclusters were imaged with *Spitzer* instruments. The MIPSGAL survey (cite: Benjamin2003) covered the Galactic plane with the *Spitzer*/MIPS camera, while the GLIMPSE survey (cite: Carey2009) provides *Spitzer*/IRAC observations. The absolute flux calibration uncertainties for *Spitzer* observations are estimated at 4% for MIPS at 24 $\upmu$m (cite: Engelbracht2007), and 2% for IRAC at 3.6, 4.5, 5.8 and 8.0 $\upmu$m (cite: Reach2005).

# PPMAP description and analysis

## Point process mapping

The point process mapping procedure, denoted as PPMAP ((cite: Marsh2015); (cite: Marsh2017)), is an iterative Bayesian SED fitting algorithm that allows to account for the mixing of physical conditions along the line of sight (dust temperature gradients and variations of the opacity index $\beta$). PPMAP is grounded in the point process formalism ((cite: Richardson&Marsh1987); (cite: Richardson&Marsh1992), (cite: Marsh2006)). The point process formalism represents complex astrophysical systems as an arrangement of individual components, referred to as ‘‘points” (e.g., (cite: Marsh2015)). Points do not correspond to individual astrophysical objects in the image, nor to pixels; rather, they serve as elements that facilitate image representation. These elements are defined by a set of physical parameters, corresponding to a specific position within a state space. For our present purposes, the state space includes the position on the celestial sphere ($x$, $y$) and the dust temperature $T_\mathrm{dust}$. Hence, the state space has a dimensionality $N_\mathrm{states} = N_\mathrm{temp} \times N_x \times N_y$, where $N_\mathrm{temp}$, $N_x$ and $N_y$ are the number of temperature and positional cells that the points may occupy. The system can then be characterized by a vector containing the occupation number of each cell within the state space, denoted $\mathbf{\Gamma}$. In essence, the local density of points corresponds to the density of dust at a specific sky position and temperature. Therefore, the dust column density within the $n^\mathrm{th}$ cell is determined by the corresponding occupation number $\Gamma_n$, and the set of occupation numbers $\mathbf{\Gamma}$ can also be viewed as a probability density function. The underlying PPMAP measurement model is expressed by the equation: $$\begin{equation}
\mathbf{d} = \mathbf{A \Gamma} + \mu .
\end{equation}$$ Here, $\mathbf{d}$ is the vector of observational measurement. The $m^\mathrm{th}$ component of $\mathbf{d}$ pertains to the pixel value at the coordinates ($x_m$, $y_m$) within the observed image at the wavelength $\lambda_m$. The term $\mu$ represents the measurement noise, assumed to be a Gaussian random process. Lastly, $\mathbf{A}$ denotes the system response matrix. Within this matrix, the $mn^\mathrm{th}$ element corresponds to the response of the $m^\mathrm{th}$ measurement to a point situated in the $n^\mathrm{th}$ cell of the state space (characterized by spatial position $x_n$, $y_n$, and temperature $T_n$). The PPMAP algorithm aims to solve this equation for $\mathbf{\Gamma}$, given a set of observations $\mathbf{d}$ and an a priori distribution of points. This is achieved by minimizing the mean square error, ensuring that the best estimate is the a posteriori expectation value of $\mathbf{\Gamma}$. The initial distribution (or ‘‘prior”) across all positions and temperatures is a Gaussian random process, expressed as: $$\begin{equation}
\label{eq:prior}
P(\Gamma_n) = \frac{1}{\sigma \sqrt{2 \pi}} \mathrm{exp} \left( \frac{-(\Gamma_n -\eta)^2}{2 \sigma^2} \right),
\end{equation}$$ where $\Gamma_n$ is the occupation number in the $n^\mathrm{th}$ element of the state space, and $\sigma = \sqrt{\eta (1 - 1 / N_\mathrm{states})}$. The quantity $\eta$ is referred to as the ‘‘dilution”, since it controls the number of points relatively to the number of cells in state space. The initial distribution expressed by Eq. ([\[eq:prior\]](#eq:prior)) means that points are equally likely to occupy any $x$, $y$ position, and any given value in the user-defined log$(T)$ temperature distribution.

![](images/PPMAP-process.jpg)

PPMAP operates under the assumption that the radiation emitted by dust across observed wavelengths is optically thin. Consequently, the system response matrix $\textbf{A}$ takes the form of the MBB approximation, expressed as: $$\begin{equation}
\label{eq:PPMAPresponsematrix}
A_{mn} = H_{\lambda_m} K_{\lambda_m}(T_n) B_{\lambda_m}(T_n) \kappa_{\lambda_m}\Delta \Omega_m .
\end{equation}$$ Here, $H_\lambda$ represents the convolution operator associated with the point spread function (PSF) at wavelength $\lambda$, $K_\lambda (T)$ accounts for a possible color correction, pertaining to the finite bandwidth of observations (cf. [6.2.2](#appendix:colorcorrection)), $B_\lambda (T)$ denotes the Planck function, $\kappa _{\lambda}$ corresponds to the dust opacity law, and $\Delta \Omega$ denotes the solid angle corresponding to a specific pixel in the output map. The $H_\lambda$ operator enables PPMAP to function without downgrading the spatial resolution of input maps, provided that the model benefits from accurate beam profiles. The PPMAP dust opacity law, $\kappa_\lambda$, exhibits a wavelength dependence parametrized by the opacity index $\beta$: $$\begin{equation}
\beta = - \frac{d \mathrm{ln} (\kappa_\lambda)}{d \mathrm{ln} (\lambda)} .
\end{equation}$$ Thus, for any given $\lambda$, the dust opacity law $\kappa_\lambda$ can be represented as: $$\begin{equation}
\label{eq:Kappa300}
\kappa_\lambda = \kappa_{300} \left( \frac{\lambda}{300~\upmu \mathrm{m}} \right) ^{-\beta} .
\end{equation}$$ Here, $\beta$ denotes the opacity power-law index, and $\kappa_{300} = 0.1~\mathrm{cm^2 g^{-1}}$ represents the reference opacity, measured at $\lambda_0 = 300$ $\upmu$m, encompassing both dust and gas mass contributions. The selection of the dust absorption coefficient employed by PPMAP ($\kappa_{300} = 0.1~\mathrm{cm^2 g^{-1}}$) is in line with a gas-to-dust mass ratio of 100 (cite: Hildebrand1983). The value of $\kappa_{300}$ is identical for all points, and remains unchanged during the iterative process. Employing Eq. ([\[eq:Kappa300\]](#eq:Kappa300)) with $\beta=1.8$ yields $\kappa_{1.3\mathrm{mm}} = 0.007~\mathrm{cm^2 g^{-1}}$, which is consistent with the value adopted by (cite: Armante2024) following (cite: Ossenkopf&Henning1994) ($\kappa_{1.3\mathrm{mm}} = 0.01 ^{+0.005}_{-0.0033}~\mathrm{cm^2 g^{-1}}$). The reference opacity is in fact not well known, and may vary across the protoclusters. Depending on the size distribution and the composition of the dust, a range $\kappa_{1.3\mathrm{mm}} = 0.002 - 0.03~\mathrm{cm^2 g^{-1}}$ is predicted by (cite: Ysard2019) for the diffuse interstellar medium (cf. ‘‘Mix 1” and ‘‘Mix 2”, power-law size distributions). Aggregated grain models better represent denser media, and in that case the reference opacity is predicted to increase by a factor 3 to 7, depending on the addition of ice mantles into the models (cite: Koehler2015).

![](images/SEDs-2sigma.pdf)

Unlike conventional modified blackbody fitting approaches, PPMAP circumvents the need to homogenize the input observational data to a common resolution. Instead, when provided with a collection of observational data pertaining to dust continuum emission at varying instrumental resolutions, PPMAP produces maps of column density and temperature that are simultaneously optimized with respect to each specific PSFs associated with each dataset. Figure [2](#fig:PPMAP-process) provides a schematic illustration of the stepwise approach employed by PPMAP. In practical terms, PPMAP initializes an array given an a priori distribution of points. Subsequently, it generates a corresponding synthetic map for comparison with actual maps, accounting for synthetic noise. In each pixel of the maps, PPMAP minimizes the reduced-$\chi^2$ metric, calculated from the deviations between components of the measurement model $\textbf{d}$ and the corresponding observations, that are initially resampled to a common pixel size. Employing a truncated hierarchy of integro-differential equations (described in details by (cite: Marsh2015), Sect. 2.3), the distribution of points in the state space is iteratively updated until the model converges to match the observations. Upon completion of the process, the dust column density and temperature are given by the expectation value $E(\Gamma_n \lvert \mathbf{d})$. The H$_2$ column density is derived assuming a reference opacity of $\kappa_{300}=0.1$ cm$^2$ g$^{-1}$, fractional abundance by mass of hydrogen and molecular hydrogen $X_\mathrm{H}=0.7$, $X_\mathrm{H_2}=1$, and fractional abundance by mass of dust $Z_\mathrm{D}=0.01$ (cite: Howard2019; Howard2021). The differential column density cube $N_\mathrm{H_2}(T_\mathrm{dust})$ represents the H$_2$ column density at different dust temperatures, such that: $$\begin{equation}
\label{eq:PPMAP-N}
N_\mathrm{H_2}(i, j) = \sum_{k=1}^{N_\mathrm{temp}} N_\mathrm{H_2}(i, j, T_{\mathrm{dust}, k}) .
\end{equation}$$ Similarly, the density-weighted dust temperature map is defined by the following average quantity, based on the differential column density cube: $$\begin{equation}
\label{eq:PPMAP-T}
T_\mathrm{dust}(i, j) = \frac{1}{N_\mathrm{H_2}(i, j)} \sum_{k=1}^{N_\mathrm{temp}} \left\lbrace T_{\mathrm{dust}, k} N_\mathrm{H_2}(i, j, T_{\mathrm{dust}, k}) \right\rbrace .
\end{equation}$$ Lastly, in accordance with Eq. ([\[eq:PPMAPresponsematrix\]](#eq:PPMAPresponsematrix)), the synthetic intensity produced by PPMAP at wavelength $\lambda$ in any pixel is determined by the following sum: $$\begin{equation}
\label{eq:PPMAPmod}
I_\lambda(i, j) = \sum_{k=1}^{N_\mathrm{temp}} \left\lbrace \left( \frac{N_\mathrm{H_2}(i, j, T_{\mathrm{dust}, k})}{2.1 \times 10^{24}\mathrm{cm^{-2}}} \right) \left( \frac{\lambda}{300\mathrm{\upmu m}} \right)^{-\beta} B_\lambda(T_{\mathrm{dust}, k}) \right\rbrace .
\end{equation}$$ Here, $N_\mathrm{H_2}(T_{\mathrm{d}, k}) / 2.1 \times 10^{24}~\mathrm{cm^{-2}} = \tau_{300}$ represents the optical depth at 300 $\upmu$m. The numerical constant depends on the adopted values of $\kappa_{300}$, $X_\mathrm{H}$, $X_\mathrm{H_2}$ and $Z_\mathrm{D}$.

## PPMAP analysis

We apply the PPMAP procedure to the continuum data set detailed in Sect. [2](#sect:observations). A comprehensive account of the methodology employed for implementing PPMAP to the data is provided in Appendix [6](#appendix:PPMAP). Here, we present an overview of the principles adopted throughout our analysis. To prevent contamination by free-free emission, we exclude the ALMA Band 3 data from our analysis (that is, the ALMA 3 mm continuum map, see also Sect. [6.1.3](#sect:free-free) on the impact of free-free emission on PPMAP products). Consequently, the input images for PPMAP encompass the wavelength range from 70 $\upmu$m (*Herschel*/PACS) to 1.3 mm (ALMA Band 6).

The opacity indices predicted by dust models describing diffuse and dense interstellar media are $\beta = 1.5$ and $\beta = 1.8$ (cite: Koehler2015), respectively. There is in fact a range of plausible values, and $\beta$ may vary across the field of observations, but we adopt a fixed value to minimize effects from the degeneracy between the temperature and opacity index and thus better constrain the temperature ((cite: Shetty2009); (cite: Kelly2012); (cite: Galliano2018)). We therefore fix the opacity index to $\beta = 1.8$, and we employ 8 MBB components with temperature values ranging from 10 K to 50 K, consistent with prior PPMAP applications (e.g., (cite: Marsh2017); (cite: Howard2019); (cite: Whitworth2019); (cite: Chawner2020); (cite: Howard2021)). Adopting a number of temperature components higher than 8 would result in larger uncertainties without improving the temperature sampling significantly. We experimented with larger temperature ranges and found that $10 - 50$ K is sufficient to reproduce the observations. The final temperature estimate can exceed this temperature range following on the a posteriori temperature correction (see Sect. [3.4](#sect:opacity-correction)). The pixel sizes of the Nyquist-sampled PPMAP arrays are 1.25$^{\prime \prime}$, corresponding to an angular resolution of 2.5$^{\prime \prime}$. We execute the PPMAP analysis twice. The initial run (‘‘Run1”) uses the ALMA B6 data decontaminated from free-free emission (as released by Galván-Madrid et al., in prep.), primarily created for deriving column density and dust temperature. The subsequent run (‘‘Run2”) employs the standard ALMA B6 data (as released by (cite: Diaz2023)), that is more optimal for accurately determining the luminosity by taking into account the millimeter excess tied to free-free emission. Column density and temperature estimates are directly obtained through the application of PPMAP, but deriving the bolometric luminosity requires additional steps.

## Bolometric luminosity measurements

+:---------------------------+:-------------:+:--------------------------------:+:---------------------:+:----------------------:+:---------------------------------:+:-------------------------------:+:-----------------------------:+:----------------------------------------:+:-------------------------------------------:+
|                            |               |                                  |                       |                        |                                   |                                 |                               |                                          |                                             |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| Region                     | Distance$^a$  | $\overline{T_\mathrm{dust}}$$^b$ | $N_\mathrm{peak}$$^c$ | ALMA footprint$^d$                                                                           | ATLASGAL footprint$^e$                                                                                                 |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| (lr.75em)5-7 (lr.75em)8-10 | (kpc)         | (K)                              | ($10^{24}$ cm$^{-2}$) | $M$ ($10^2 M_{\odot}$) | $L_\mathrm{bol}$ ($10^3 L_\odot$) | $L / M$ ($L_\odot / M_{\odot}$) | $M^\prime$ ($10^2 M_{\odot}$) | $L_\mathrm{bol}^\prime$ ($10^3 L_\odot$) | $L^\prime/M^\prime$ ($L_\odot / M_{\odot}$) |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
|                            |               |                                  |                       |                        |                                   |                                 |                               |                                          |                                             |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
|                            |               |                                  |                       |                        |                                   |                                 |                               |                                          |                                             |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| W43-MM1                    | $5.5\pm 0.4$  | 27 $\pm$ 5                       | 12 $\pm$ 3            | 170 $\pm$ 60           | 250 $\pm$ 90                      | 15                              | 110 $\pm$ 30                  | 80 $\pm$ 30                              | 7                                           |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| W43-MM2                    | $5.5\pm 0.4$  | 25 $\pm$ 5                       | 9 $\pm$ 3             | 150 $\pm$ 60           | 180 $\pm$ 60                      | 12                              | 50 $\pm$ 20                   | 30 $\pm$ 10                              | 6                                           |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G338.93                    | $3.9 \pm 1.0$ | 25 $\pm$ 5                       | 1.7 $\pm$ 0.5         | 40 $\pm$ 30            | 100 $\pm$ 60                      | 25                              | 40 $\pm$ 20                   | 90 $\pm$ 30                              | 23                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G328.25                    | $2.5 \pm 0.5$ | 25 $\pm$ 5                       | 1.9 $\pm$ 0.5         | 10 $\pm$ 5             | 50 $\pm$ 30                       | 50                              | 8 $\pm$ 3                     | 30 $\pm$ 10                              | 38                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G337.92                    | $2.7 \pm 0.7$ | 22 $\pm$ 4                       | 8 $\pm$ 2             | 30 $\pm$ 20            | 130 $\pm$ 80                      | 43                              | 20 $\pm$ 10                   | 70 $\pm$ 30                              | 35                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G327.29                    | $2.5 \pm 0.5$ | 25 $\pm$ 5                       | 60 $\pm$ 20           | 80 $\pm$ 40            | 110 $\pm$ 60                      | 14                              | 50 $\pm$ 20                   | 50 $\pm$ 20                              | 10                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
|                            |               |                                  |                       |                        |                                   |                                 |                               |                                          |                                             |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G351.77                    | $2.0\pm 0.7$  | 26 $\pm$ 5                       | 19 $\pm$ 5            | 20 $\pm$ 10            | 80 $\pm$ 60                       | 40                              | 13 $\pm$ 5                    | 60 $\pm$ 20                              | 46                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G008.67                    | $3.4 \pm 0.3$ | 21 $\pm$ 4                       | 4 $\pm$ 1             | 30 $\pm$ 10            | 70 $\pm$ 30                       | 23                              | 20 $\pm$ 10                   | 40 $\pm$ 10                              | 20                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| W43-MM3                    | $5.5\pm 0.4$  | 25 $\pm$ 5                       | 3 $\pm$ 1             | 80 $\pm$ 30            | 180 $\pm$ 70                      | 23                              | 20 $\pm$ 10                   | 50 $\pm$ 20                              | 25                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| W51-E                      | $5.4\pm 0.3$  | 23 $\pm$ 4                       | 30 $\pm$ 10           | 240 $\pm$ 70           | 1200 $\pm$ 400                    | 50                              | 170 $\pm$ 50                  | 500 $\pm$ 200                            | 29                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G353.41                    | $2.0\pm 0.7$  | 21 $\pm$ 4                       | 7 $\pm$ 2             | 20 $\pm$ 10            | 60 $\pm$ 50                       | 30                              | 12 $\pm$ 5                    | 30 $\pm$ 10                              | 25                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
|                            |               |                                  |                       |                        |                                   |                                 |                               |                                          |                                             |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G010.62                    | $5.0 \pm 0.5$ | 24 $\pm$ 5                       | 5 $\pm$ 1             | 110 $\pm$ 40           | 500 $\pm$ 200                     | 45                              | 80 $\pm$ 20                   | 300 $\pm$ 100                            | 38                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| W51-IRS2                   | $5.4\pm 0.3$  | 29 $\pm$ 5                       | 50 $\pm$ 20           | 250 $\pm$ 80           | 1300 $\pm$ 500                    | 52                              | 190 $\pm$ 60                  | 300 $\pm$ 100                            | 16                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G012.80                    | $2.4 \pm 0.2$ | 28 $\pm$ 5                       | 3 $\pm$ 1             | 120 $\pm$ 40           | 300 $\pm$ 100                     | 25                              | 20 $\pm$ 10                   | 180 $\pm$ 60                             | 90                                          |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+
| G333.60                    | $4.2 \pm 0.7$ | 27 $\pm$ 5                       | 3 $\pm$ 1             | 130 $\pm$ 60           | 1400 $\pm$ 700                    | 108                             | 50 $\pm$ 20                   | 800 $\pm$ 300                            | 160                                         |
+----------------------------+---------------+----------------------------------+-----------------------+------------------------+-----------------------------------+---------------------------------+-------------------------------+------------------------------------------+---------------------------------------------+

\
 \

$^a$From Table 1 in (cite: Motte2022).\
$^b$Spatially-averaged density-weighted dust temperature, measured in the corrected PPMAP temperature map (cf Sect. [3.4](#sect:opacity-correction)).\
$^c$ Peak H$_2$ column density, measured in the PPMAP column density map.\
$^d$ Mass of gas, derived from the PPMAP column density map; bolometric luminosity, derived from the PPMAP MBB in addition to observations by *Spitzer* and SOFIA (that is, between 3.6 $\upmu$m and 1.3 mm); and luminosity-to-mass ratio, measured in the ALMA footprint (cf. Sect. [3.3](#subsect:luminosity)).\
$^e$ Mass, bolometric luminosity and luminosity-to-mass ratio measured in the ATLASGAL source footprint ((cite: Contreras2013), (cite: Urquhart2014), cf Sect. [3.3](#subsect:luminosity)).\

Using the outcomes of PPMAP Run2 (in order to take into account the free-free contribution to the luminosity), we computed the luminosity for all observed ALMA-IMF fields. The ‘‘PPMAP Luminosity” ($L_\mathrm{MBB}$) is defined as the integral $4\pi d^2 \int I_\nu \mathrm{d}\nu$, where $I_\nu$ is defined by Eq. ([\[eq:PPMAPmod\]](#eq:PPMAPmod)), and $d$ denotes the distance to the observed star-forming region. On the other hand, the bolometric luminosity ($L_\mathrm{bol}$) accounts for the additional near-infrared flux estimated from background-subtracted *Spitzer*/IRAC, *Spitzer*/MIPS, and SOFIA/HAWC+ observations, extracted from the MIPSGAL, GLIMPSE, and SOFIA archives ((cite: Carey2009); (cite: Benjamin2003); (cite: Vaillancourt2016); (cite: Pillai2023); also see Table  [\[table:ObservationSummary\]](#table:ObservationSummary)). We performed a pixel-per-pixel merge between MIPSGAL, GLIMPSE, and HAWC+ observations and the PPMAP output SED using a piecewise cubic Hermite interpolating polynomial from the `scipy` package in `Python`. This results in a composite SED model as follows: $$\begin{equation}
\begin{split}
I_\lambda^\prime(\lambda < 70~\mathrm{\upmu m}) = \mathrm{PCHI}(\lambda) , \\
I_\lambda^\prime(\lambda \geq 70~\mathrm{\upmu m}) = \mathrm{MBB}(\lambda) .
\end{split}
\end{equation}$$ Here,‘‘PCHI” denotes the cubic spline function employed for interpolating near-infrared data points, and ‘‘MBB” represents the best-fit PPMAP model. The bolometric luminosity is then defined as $L_\mathrm{bol} = 4 \pi d^2 \int_{3.6~\upmu \mathrm{m}}^{1.3~\mathrm{mm}} I_\lambda^\prime d\lambda$. The presence of saturation in the *Spitzer*/MIPS band occasionally resulted in lower limits on the infrared flux at 24 $\upmu$m (refer to the first column in Fig. [1](#fig:datacompleteness)). Additionally, our integration approach effectively merges 2.5$^{\prime \prime}$ products with observations acquired at coarser resolutions (*Spitzer*/MIPS at 5.6$^{\prime \prime}$ and SOFIA/HAWC+ at 4.85$^{\prime \prime}$), resulting in a composite angular resolution. These two limitations have a relatively low impact on the outcome, given that the dominant contribution to the luminosity arises from the MBB emission ($L_\mathrm{MBB} / L_\mathrm{bol} \geq 0.77$ across the 15 star-forming regions studied, where $L_\mathrm{MBB}$ and $L_\mathrm{bol}$ are respectively the modified blackbody and bolometric luminosities integrated over the field of observations).

Figure [3](#fig:SEDs) displays a representative sample of illustrative spectral energy distributions (SEDs) extracted from the ATLASGAL sources’ footprints encompassing the protoclusters ((cite: Contreras2013), (cite: Urquhart2014)). All of the observations align within $\pm 2$ standard deviation ($\sigma$) of the PPMAP MBB model, and 86% of the observations maintain agreement within $\pm 1 \sigma$. We note that the ALMA error bars appear larger as a result of the integration area being large with respect to the 1.3 mm sources sizes.

## Temperature correction and final products

![](images/MM1_tempchange.pdf)

As reported in Sect. [3.1](#sect:PPMAPdescription), PPMAP assumes that the observed astrophysical object is optically thin to the thermal radiation emitted by dust across all input wavelengths. This primarily leads to a bias in the estimate of the dust temperature of deeply embedded sources, since the infrared fluxes at $\lambda \leq 250$ $\upmu$m may significantly deviate from the MBB shape (cite: Menshchikov2016). To mitigate this limitation, in our analysis we have systematically applied an a posteriori correction to the PPMAP-derived temperature maps. After running PPMAP on synthetic observations generated with a dust model that incorporates the effect of the optical depth, the PPMAP outcome is compared with the input model dust parameters. We derive a correction table from this comparison, that can then be applied to PPMAP products (the dust model used to build this correction table is described in Appendix [6.3](#appendix:tempcorr)). Figure [4](#fig:MM1-tempchange) illustrates the change in temperature following the correction of the W43-MM1 temperature image. The outcome of the temperature correction is evident in localized areas, where the temperature is increased. For instance, in G012.80 the 99$^\mathrm{th}$ percentile temperature raises to 38.0 K from 33.2 K after the opacity correction. The magnitude of this correction scales with the column density estimated by PPMAP, as shown in Fig. [15](#fig:tcorr), therefore the high-density pixels benefit the most from it. As a result, the correction allows a better representation of embedded protostars and hot cores.

The final products delivered with this study are the maps of the H$_2$ column density ($N_\mathrm{H_2}$, in cm$^{-2}$), bolometric luminosity ($L_\mathrm{bol}$, in $L_\mathrm{sun} / \mathrm{px}$) and dust temperature ($T_\mathrm{dust}$, in Kelvin) (see Fig. [13](#fig:PPMAPflowchart) for reference). The dust temperature maps are declined in two versions:

1.  The direct output of PPMAP, denoted hereafter as $T_\mathrm{dust}^\prime$, represents the best-fit MBB temperature derived under the assumption of optically thin emission.

2.  The a posteriori correction of the temperature yields a new estimate, denoted hereafter as $T_\mathrm{dust}$.

The opacity-corrected temperature $T_\mathrm{dust}$ generally provides a better representation of the dust temperature, except in instances where the foreground is heated. Therefore, the temperature of internally heated, optically thick dust cores are best estimated by the second version of the temperature map, that we hereafter consider the default. Impending studies will attempt to determine the best combination of both maps based on the identification of prestellar cores and candidate protostars in the ALMA-IMF fields (Motte et al., in prep.).

An other caveat tied to PPMAP-derived temperatures is the impact of the $2.5^{\prime \prime}$ angular resolution. Emission of the ALMA-IMF cores with a median size of $\sim 2100$ au (cite: Motte2022) is diluted in a PPMAP beam of physical size 6000 – 14 000 au, depending on the distance of the region. This dilution of the signal may result in underestimating the temperature of protostellar cores and overestimating that of prestellar cores, since cold and warm dust are mixed in the $2.5^{\prime \prime}$ beam, as well as along the stratified line of sight. Therefore, additional processing should be applied to PPMAP temperature maps prior to their use in constraining core temperatures. This endeavor is also being undertaken by Motte et al. (in prep.), to which we refer the reader for a detailed account of the methodology.

# Results, validation, and caveats

Following the procedures described in Sect. [3](#sect:PPMAP) and expanded upon in Appendix [6](#appendix:PPMAP), we have applied PPMAP to multiwavelength observations and obtained luminosity, column density and temperature maps at a 2.5$^{\prime \prime}$ angular resolution. We here present these outputs, evaluate their reliability against an accepted reference and then discuss their uncertainties.

## Results

![image](images/G353-gain-temp.pdf) ![image](images/G353-gain-cdens.pdf)

![image](images/MM1.pdf) ![image](images/G008.pdf) ![image](images/G012.pdf)

Figure [5](#fig:PPMAP-resolution) illustrates the improvement in angular resolution achieved through PPMAP’s application. We used the temperature and column density images of G353.41 as examples to illustrate the importance of gaining angular resolution for the ALMA-IMF studies. In this figure, we contrast the outcomes of the PPMAP approach at a 2.5$^{\prime \prime}$ resolution with the more typical approach, that requires smoothing all input images to the same angular resolution. To make this illustration, we first substituted the *Herschel*/SPIRE image at 350 $\upmu$m with the SABOCA image and excluded the *Herschel*/SPIRE image at 500 $\upmu$m, thus preventing further smoothing to a 35.2$^{\prime \prime}$ resolution. We then smoothed all continuum images to the coarsest angular resolution, which is that of LABOCA observations, 19.2$^{\prime \prime}$. Finally we performed SED fitting using PPMAP.

Complete representations of PPMAP luminosity, column density and temperature maps obtained for all regions are shown in Fig. [17](#fig:PPMAPs-supplementary). The spatial variations of the reduced $\chi^2$ square metric are also shown in Fig. [18](#fig:PPMAPs-chi2) for all regions. We here present an overview of these PPMAP data products for a subset of regions, selected to provide one example for each evolutionary stage (young, intermediate, evolved, as outlined by (cite: Motte2022)). In Fig. [6](#fig:PPMAPs), we present the column density, bolometric luminosity and dust temperature maps obtained for this specific subset. These temperature images correspond to those corrected for the opacity because we consider them to best represent the dust temperature in dense regions. In the following, we simply call them the temperature images (see Sect. [3.4](#sect:opacity-correction) and Appendix [6.3](#appendix:tempcorr) for a description of the temperature correction procedure).

With a 2.5$^{\prime \prime}$ angular resolution, PPMAP captures the morphology of filamentary structures, pinpoint the location of cores, protostars, Hregions, and constrain their surrounding physical conditions. The angular resolution provided by PPMAP offers an insight into the relationships between the continuum cores identified by (cite: Louvet2024) in the ALMA-IMF 1.3 mm continuum images and the column density and dust temperature maps. These cores, with typical sizes of 0.4-0.9$^{\prime \prime}$ (equivalent to $\sim$2000-4000 au), align with filaments and aggregate within central hubs, a trend depicted in Figs. [5](#fig:PPMAP-resolution)–[6](#fig:PPMAPs). Additionally, within the temperature images we observe correlations between massive, hot protostars and warmer spots, while Hregions appear as extended areas of enhanced temperature (as evidenced in the evolved protocluster G012.80, shown in the bottom panel of Fig. [6](#fig:PPMAPs), also see (cite: Armante2024)). This underscores the pivotal role of PPMAP’s resolution-optimization capacity in achieving our goals.

Table [\[table:Results\]](#table:Results) presents the luminosity measurements using two distinct approaches:

1.  The bolometric luminosity ($L_\mathrm{bol}$) measured in the primary beam response of the ALMA 12 m array mosaics (hereafter referred to as the ‘‘ALMA-IMF mosaic footprint”, as outlined in Paper I, (cite: Motte2022), Fig. 1).\

2.  The bolometric luminosity ($L_\mathrm{bol}^\prime$) measured in the ATLASGAL sources’ footprints, as outlined in (cite: Contreras2013) and (cite: Urquhart2014). These sources were extracted from the ATLASGAL survey (cite: Schuller2009) using the source extraction routine SEXtractor. Protoclusters imaged by ALMA-IMF are associated with either one or two ATLASGAL sources (two sources in the case of G008.67), that are always smaller than the ALMA-IMF mosaic footprints. An example of single ATLASGAL source is shown in the bottom panel of Fig. [5](#fig:PPMAP-resolution).

Table [\[table:Results\]](#table:Results) also provides a compilation of average dust temperatures, peak column densities and total masses. The regions are classified according to their evolutionary stages, as defined in (cite: Motte2022), categorized as ‘‘young”, ‘‘intermediate”, and ‘‘evolved”, in descending order in the table. The luminosity-to-mass ratio, $L / M$, exhibits a noticeable trend aligned with this classification: younger regions generally correspond to lower ratios ($L / M = 20$ on average for the young protoclusters listed in Table [\[table:Results\]](#table:Results)), and vice versa ($L / M = 76$ on average for the evolved protoclusters listed in Table [\[table:Results\]](#table:Results)). There is also a trend of increasingly high temperatures across the evolutionary stages, with a 99$^\mathrm{th}$ percentile temperature of 33.7 K, 35.4 K and 38.7 K respectively for the young, intermediate and evolved regions. The average temperatures presented in the table, ranging from 21 K to 29 K, are representative of broader regions rather than locally heated zones (see Sect. [4.1](#subsect:maps)). The $99^\mathrm{th}$ percentile temperature ranges from 28 K to 42 K, depending on the specific region. As such, the temperatures inferred by PPMAP within the vicinity of massive cores are higher than those measured by (cite: Wienen2012; Wienen2018), (cite: Koenig2017) and used in (cite: Motte2022) as the means to estimate core masses ($T_\mathrm{dust} = 20 - 30$ K). The average column density measured in the 2.5$^{\prime \prime}$ maps ranges from $2.5 \times 10^{22}$ to $2.5 \times 10^{23}$ cm$^{-2}$, about one to two decades higher than those measured in the wide Herschel images of nearby star-forming regions ((cite: Arzoumanian2011), (cite: Hill2011)).

## Comparison to results from ATLASGAL

![image](images/PPMAP-Koenig2017-lum.pdf) ![image](images/PPMAP-Koenig2017-mass.pdf)

In order to benchmark our results, Fig. [7](#fig:Koenig2017Benchmark) compares the bolometric luminosity and mass measured in the PPMAP images to those obtained by (cite: Koenig2017). Based on a two-temperatures MBB description, they inferred bolometric luminosities and masses for a selected sample of 110 ATLASGAL sources through SED fitting of their mid-infrared to submillimeter flux densities, between 8 and 870 $\upmu$m, that is, a slightly narrower range than ours (3.6 $\upmu$m - 1.3 mm). We performed aperture photometry on the 2.5$^{\prime \prime}$ PPMAP-derived bolometric luminosity and column density maps using the exact same apertures. The (cite: Koenig2017) apertures were designed to ensure consistent flux extraction over the same area from the mid-infrared to the submillimeter range. Throughout the comparison we introduced a systematic correction to account for variations in the adopted distances for the ALMA-IMF regions[^3]. The comparison is made on a subset of 10 regions observed by both studies: G008.67, G010.62, G012.80, G327.29, G333.60, G337.92, G338.92, G351.77, G353.41, W43-MM1, and W51-E.

On the one hand, our comparison (cf. Fig. [7](#fig:Koenig2017Benchmark)) indicates that our bolometric luminosity estimates are generally consistent with the measurements made by (cite: Koenig2017). The only noticeable discrepancy, exceeding a standard deviation, is observed for G333.60. This discrepancy is likely due to the saturation of *Spitzer*/MIPS observations in our study, a limitation that was circumvented by (cite: Koenig2017) using MSX observations (cite: Egan2003). Incorporating MSX observations into our study was not feasible, as our focus is to achieve the most accurate representation of the finer scales in the images (below $5^{\prime \prime}$). This objective contrasts with the relatively coarse angular resolution of MSX (18$^{\prime \prime}$), and the fact that MSX observations can only be added to the SED model a posteriori, since PPMAP cannot reproduce the emission from out-of-equilibrium dust grains.

On the other hand, our mass estimates exhibit more significant discrepancies with (cite: Koenig2017)’s results (see Fig. [7](#fig:Koenig2017Benchmark)). Because the derived mass depends on the estimated temperature, using the MBB description can yield larger discrepancies in the mass estimates compared to the luminosity estimates. Measuring luminosities involves a robust and straightforward measurement of the area below the data points, whereas the derived mass depends on the estimated temperature. As a consequence, it is anticipated that a more substantial variability may arise in mass, in contrast to luminosity (see Fig. [7](#fig:Koenig2017Benchmark)). Furthermore, (cite: Galliano2018) reported that mass estimates may depend on the spatial resolution, since the temperature structure can be hidden in poorly resolved images, while it is accounted for in higher-resolution observations (e.g., Fig. 14 in (cite: Aniano2012)). This interpretation is consistent with the fact the more distant protoclusters display larger mass discrepancies, while the less distant protoclusters better align with the identity curve, with the only exception of G327.29.

Additionally, our use of 8 dust temperatures for reproducing the observations contrasts with (cite: Koenig2017) use of at most two temperatures. When using more temperature components, a small amount of warm dust can largely contribute to the 70 $\upmu$m emission, thereby recovering an amount of cold dust that would otherwise would be missed, and consequently increasing the total mass (e.g., (cite: Aniano2012)). Moreover, an other effect is the fact that the longest wavelength used by (cite: Koenig2017) is 870 $\upmu$m, whereas we also used 1.3 mm observations. We checked for these two effects and found that reducing the number of temperature components to two does result in higher density-weighted temperatures, while removing the 1.3 mm data generally results in recovering less mass. Taking into account these two effects combined, 14 out of 15 protoclusters masses are consistent with (cite: Koenig2017)’s measurement within $1\sigma$ (with the exception of G338.93, that is consistent within $2 \sigma$). Finally, the use of a slightly different opacity index ($\beta = 1.75$) and larger reference opacity ($\kappa_{300} \simeq 0.125$ cm$^2$g$^{-1}$) by (cite: Koenig2017) marginally accounts for these mass discrepancies.

## Uncertainties

### Description

We estimate here the uncertainties inherent to the PPMAP-derived products and measurements. While the MBB description itself constitutes an approximation, our results are influenced by additional complexities. Table [1](#table:systematic-errors) provides an estimate of the mean values of these uncertainties across the 15 protoclusters studied. The primary sources of errors within the PPMAP process, that impact the determination of luminosity, mass, column density and dust temperatures, are as follows:

1.  Saturated pixels: saturation in the continuum observations used as PPMAP inputs. Most importantly, the saturation of the *Spitzer*/MIPS map at 24 $\upmu$m (see Fig. [1](#fig:datacompleteness)) may impact the bolometric luminosity estimate, like suggested for that of G333.60 in Fig. [7](#fig:Koenig2017Benchmark). In contrast, the saturation of far-infrared and submillimeter images and its effect on PPMAP products are mitigated by the Gaussian process regression we applied (cf. Appendix [6.1.1](#appendix:desaturation)).\

2.  Free-free emission: the MBB description does not account for the free-free emission that contributes to the ALMA 1.3 mm image of evolved and intermediate regions. We used images approximately corrected for contamination by free-free emission, as described in Sect. [6.1.3](#sect:free-free).\

3.  Noise estimates in the FIR to millimeter maps: they determine the uncertainty in estimating the measurement error for the input maps, that in turn determines the relative weights of data points used throughout the PPMAP SED fitting process. All the PPMAP results are thus sensitive to the methods used to determine the noise level of input maps (Sect. [6.2.1](#sect:noise)).\

4.  PPMAP SED fitting: the uncertainties associated with the PPMAP fitting process for determining dust parameters. Includes systematic errors arising from the adopted opacity index ($\beta = 1.8\pm0.2$).\

5.  Correction of the optically thick emission: while this correction is crucial to estimate the dust temperature maps of ALMA-IMF protoclusters, it relies on a model of extinction that introduces uncertainties (cf. Sect. [3.4](#sect:opacity-correction)).\

Finally, we identified four minor sources of error.

1.  Pointing errors inherent to any map sets taken with different observatories, here leading to relative shifts between *Herschel*, APEX, SOFIA, and ALMA data, could bias the SED fitting (cf. Table [1](#table:systematic-errors)).\

2.  Uncertainties on the distance to the Sun of ALMA-IMF protoclusters (see Table [\[table:Results\]](#table:Results)) lead to errors on their luminosity and mass images.\

3.  Errors introduced by the splines interpolation of the near-infrared observations, below 70 $\upmu$m.

4.  Finally, ring-like artifacts around sources are expected to have an impact on the PPMAP-derived measurements (cf. Appendices [6.2.5](#appendix:convergence) and [6.4](#appendix:post-processing) for a description of these artifacts).

### Quantification of errors

We here quantify the mean uncertainty of each sources of error mentioned above. Systematic and random errors are listed and quantified in Table [1](#table:systematic-errors). The methods we employed to estimate the errors are the following:

1.  To estimate the uncertainties caused by the saturation, free-free emission, noise estimates, opacity index, artifacts, and pointing errors, we ran PPMAP with modified input parameters and maps. We then inferred the errors from the discrepancies between the outcomes. For instance, the uncertainty on the column density originating from the saturation of input maps is defined as $\sigma(N_\mathrm{H_2})= \Delta N_\mathrm{H_2}(\mathrm{RUN_a}, \mathrm{RUN_b}) = \lvert N_\mathrm{H_2}(\mathrm{RUN_a}) - N_\mathrm{H_2}(\mathrm{RUN_b}) \lvert$, where $N_\mathrm{H_2}(\mathrm{RUN_a})$ and $N_\mathrm{H_2}(\mathrm{RUN_b})$ are respectively the column density maps obtained with and without including the saturated images (see Fig. [1](#fig:datacompleteness)). The characteristics of the different PPMAP runs performed to derive uncertainties are described below Table [1](#table:systematic-errors).

2.  For the uncertainty inherent to the PPMAP SED fitting process, we used the uncertainty output, ‘‘`sigtdens.fits`” (in which the random errors obtained from the SED fitting are stored), to derive the column density and temperature uncertainties following Eq. ([\[eq:PPMAP-N\]](#eq:PPMAP-N)) and Eq. ([\[eq:PPMAP-T\]](#eq:PPMAP-T)).

|  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |
| uncertainty $u_X$ | label | $\sigma N_\mathrm{H_2} (u_X)$ | $\sigma T_\mathrm{dust} (u_X)$ |  |  |
|  |  |  |  |  |  |
| $u_\mathrm{saturation}$$^a$ | input saturation | 9% | 3% |  |  |
| $u_\mathrm{free-free}$$^b$ | free-free emission | 8% | 1% |  |  |
| $u_\mathrm{PPMAP}$$^c$ | PPMAP SED fitting | 8% | 11% |  |  |
| $u_\mathrm{\texttt{getnoise}}$$^d$ | noise estimates | 14% | 7% |  |  |
| $u_\beta$$^e$ | opacity index | 21% | 9% |  |  |
| $u_\mathrm{artifacts}$$^f$ | ring-like artifacts | 3% | $\pm 1~$K |  |  |
| $u_\mathrm{\Delta\theta = 1^{\prime \prime}}$$^g$ | *Herschel* pointing (1) | 0.4% | 0.2% |  |  |
| $u_\mathrm{\Delta\theta = 2.5^{\prime \prime}}$$^g$ | *Herschel* pointing (2) | 0.5% | 0.8% |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  | Combined uncertainty | 29% | 16% $\pm$ 1 K |  |  |

: Empirically derived errors associated with PPMAP measurements (see Sect. [4.3.2](#subsect:systematic-errors)).

\
 \

The numbers compiled above are the mean values (across the 15 protoclusters) of the mean errors measured in the uncertainty maps.\
$^a$Error stemming from the saturation of input continuum maps, assessed by comparing the outcomes obtained with and without the inclusion of saturated maps in the PPMAP analysis.\
$^b$Systematic error induced by free-free emission. Estimated from the comparison between Run1 and Run2 (cf. Sect. [3.2](#sect:PPMAPanalysis)).\
$^c$PPMAP SED fitting errors, derived from the `sigtdens.fits` file.\
$^d$Error related to the noise estimates used to weight the data points fed to PPMAP. Empirically derived by comparing PPMAP products obtained with three distinct noise estimate methods (cf. Sect. [6.2.1](#sect:noise)).\
$^e$Error caused by the uncertainty on the opacity index, $\beta = 1.8 \pm 0.2$.\
$^f$Error caused by ring-like artifacts (cf. Appendix [6.4](#appendix:post-processing)).\
$^g$Estimate of the error that would be produced by a 1$^{\prime \prime}$ or 2.5$^{\prime \prime}$ relative shift in the *Herschel* maps with respect to the ALMA observations.

We found that the uncertainty caused by potential *Herschel* pointing errors are negligible ($< 1$%). Meanwhile, the primary contributors to uncertainties in constraining the dust temperature include the errors associated with PPMAP’s SED fitting, noise estimates, the choice of the opacity index ($\beta$), and the influence of ring-like artifacts. Uncertainties are in fact variable across the field of observations, thus we provide uncertainty maps corresponding to the relevant data products. Values in Table [1](#table:systematic-errors) are an account of the spatially averaged uncertainties (measuring the mean value across the error maps). The determination of the total uncertainties for column density ($N_\mathrm{H_2}$) and temperature ($T_\mathrm{dust}$) employs the combined standard uncertainty ($u_\mathrm{tot}^2 = \sum_i u_i^2$, that is, a quadratic sum over the uncertainties listed in Table [1](#table:systematic-errors)), where $u$ pertains to the errors enumerated above. The resulting total uncertainties are $u_{N_\mathrm{H_2}} = 0.29 N_\mathrm{H_2}$ and $u_{T_\mathrm{dust}}= 0.16 T_\mathrm{dust} \pm 1$ K. It should be noted that these total uncertainties do not include *i.)* the uncertainty on $\kappa_{300}$, due to the unknown composition and size distribution of dust ((cite: Koehler2015), (cite: Ysard2019), (cite: Schirmer2020)); *ii.)* the bias induced by the PPMAP assumption of optical thinness, that may significantly affect the temperature and mass estimates, in particular toward high column density pixels. These considerations, along with the beam dilution bias mentioned earlier, should be treated as additional uncertainties if their relevance arises in the context of using our PPMAP estimates. Finally, we propagated the quadratic sum of errors for parameters such as $\beta$, $N$, and $T_\mathrm{dust}$ to infer errors for luminosity and mass estimates (as defined by Eq. ([\[eq:PPMAPmod\]](#eq:PPMAPmod))), employing the same combined standard uncertainty approach. Variable errors associated with distances, as outlined in the second column of Table [\[table:Results\]](#table:Results), are also factored into the mass and luminosity uncertainties.

# Discussion

The PPMAP products presented in this paper have the potential for further analyses. Firstly, high-resolution dust temperature maps are an essential prerequisite for deriving core masses and constructing core mass functions (CMFs). Although the PPMAP 2.5$^{\prime \prime}$ beam is roughly five-fold larger than that of ALMA observations, our temperature maps currently offer the most comprehensive coverage and the best resolution available for the ALMA-IMF survey. In fact, ongoing studies by (cite: Louvet2024) and (cite: Armante2024) are employing these PPMAP-derived temperature maps for CMF investigations. Moreover, our column density maps provide a means to characterize the structure of the protoclusters (as illustrated in Fig. [5](#fig:PPMAP-resolution)), and could be used along with different molecular tracers (e.g., N$_2$H$^+$) to derive abundances in different parts of the same protocluster, or between protoclusters, that has a potential use as an evolutionary indicator. Finally, the luminosity-to-mass ratio may also constitute a tracer of the evolutionary stage of these regions, even enabling the discernment of subregions within the ALMA-IMF fields. These tools open up new possibilities for further exploration within the ALMA-IMF survey, a topic we discuss in the following sections, featuring a selection of examples. More comprehensive analyses will be the focus of future studies.

![](images/cdens-PDFs.pdf)

![](images/PPMAP-N2H+.pdf)

## PPMAP-derived column density

### Probability density functions

Figure [8](#fig:cdens-PDFs) presents the mean probability density function (hereafter PDF) of the PPMAP-derived column density across the 15 regions studied. Column density PDFs of molecular cloud are well described by a lognormal distribution in addition to a power-law tail ((cite: Kainulainen2009); (cite: Schneider2015); (cite: Schneider2022), refer to (cite: Pouteau2022) for an analysis of column density PDFs in W43-MM2&MM3). The low-density tail is always limited by the included sky area, therefore the lognormal shape and position may be biased by the relatively small size of ALMA fields (typically $1^\prime \times 1 ^\prime$). Even though they span a wide range in column densities (from $10^{21}$ cm$^{-2}$ to $10^{25}$ cm$^{-2}$), distances to the Sun and evolutionary stages, the cumulative PDF of the 15 regions shown in the left panel of Fig. [8](#fig:cdens-PDFs) can be roughly described by a lognormal distribution, although substructures are seen. As an example of an individual PDF measured over the extent of the ALMA footprint, we show the PDF of the evolved G012.80 protocluster in the right panel of Fig. [8](#fig:cdens-PDFs). In this individual case the best-fit lognormal distribution better matches the measurements, and for higher column densities the departure from the lognormal distribution can be clearly defined. Deviations from the lognormal shape are predicted for gas structures governed by self-gravity ((cite: Schneider2015) and references therein). The flattening of the distribution at higher column densities is described by a power-law, $p \propto (N_\mathrm{H_2}) ^{-s}$. We measure $s=2.1 \pm 0.2$ in G012.80, a value that is consistent with gravitational collapse of an isothermal sphere (cite: Schneider2015). A comprehensive analysis of the column density PDFs is not in the scope of this study, we refer to (cite: Diaz2023) for a systematic, high-resolution study of column density PDFs inferred with PPMAP temperature maps.

### Comparison of the PPMAP column density maps with a N$_2$H$^+$ line

From the comparison with (cite: Koenig2017)’s measurements described in section [4.2](#subsect:validation), we established that the PPMAP products, including the column density and temperature maps, are robust in terms of large of the large scale measurements. These parameters ($N_\mathrm{H_2}$, $T_\mathrm{dust}$) are vital to understanding the chemistry in massive star-forming protoclusters (column density to measure abundances, temperature in relation to potential energy barriers), and to constraining dust simulations. However, the comparison presented in section [4.2](#subsect:validation) pertains to mean values measured within large apertures (on the order of $10^{\prime \prime}$). To assess our results at the precise angular resolution enabled by PPMAP (2.5$^{\prime \prime}$), we made further comparisons with observations of comparable resolution, such as the ALMA-IMF spectral data (cite: Cunningham2023). Through this comparison we aim to check that small features ($\sim 2.5^{\prime \prime}$) found in the ALMA high-resolution data are reproduced to some extent in the PPMAP products.

![](images/PDFs-LM.pdf)

Figure [9](#fig:PPMAP-N2H+) compares our column density maps with the N$_2$H$^{+}$ J=1–0 integrated line emission (Stutz et al. in prep; Alvarez-Gutierrez et al. in prep), a tracer of the dense and cold medium (cite: Pety2017) that has the potential to correlate with dusty filaments. Our analysis across regions in different evolutionary stages (G327.29: young, G353.41: intermediate, G012.80: evolved) reveals a general consistency between the PPMAP-derived column density and the N$_2$H$^{+}$ integrated intensity map. Toward G327.29 and G353.41, both the global filamentary morphology and a fraction of the local emission peaks peaks are coherent between the dust column density and N$_2$H$^{+}$ maps. Particularly remarkable is the image in the right panel of Fig. [9](#fig:PPMAP-N2H+), displaying W33 Main-West filament ((cite: Immer2014); (cite: Armante2024)). Along the filament, faint column density peaks align with local maxima of N$_2$H$^{+}$ emission, while N$_2$H$^{+}$ fades toward the central, higher column density peak. Local protostellar heating could account for the absence of N$_2$H$^{+}$ emission within the central source, where a heightened gas temperature must result in its chemical destruction following the desorption of CO from grain mantles ((cite: Lee2004); (cite: Busquet2011); (cite: Sanhueza2012)). A hot core was detected at this location, ((cite: Armante2024); (cite: Bonfand2024)), and the PPMAP-derived temperature does register a local increase in this specific area, up to 37 K (see Fig. [9](#fig:PPMAP-N2H+)), a measurement that may be consistent with a localized temperature of a hundred Kelvin, if we account for beam dilution (Motte et al., in prep.). Consistent associations between the positions of hot cores and local temperature increases in the dust temperature maps strengthen the case that the PPMAP products are reliable at their native angular scale of 2.5$^{\prime \prime}$, and demonstrate that they offer opportunities for interpretations of the physical and chemical mechanisms at work in the ALMA-IMF fields of observations.

![image](images/LM-hexbin_r.pdf) ![image](images/PPMAP-decomposition.pdf)

## Luminosity and mass of PPMAP luminosity peaks

Here we discuss the (bolometric) luminosity-to-mass ratio measured over the full extent of the protoclusters, before we delve into the luminosity-to-mass ratio of smaller sources mapped at the 2.5$^{\prime \prime}$ angular resolution. The bolometric luminosity is directly measured from the bolometric luminosity maps described in Sect. [3.3](#subsect:luminosity) (hence, including free-free emission), and the total gas mass is derived from the H$_2$ column density maps. Figure [10](#fig:LM-PDFs) shows the pixel-per-pixel PDFs of the luminosity-to-mass ratio partitioned with respect to the evolutionary stage proposed by (cite: Motte2022).

As star-forming protoclusters evolve, the contribution of Hregions to the luminosity is expected to gradually increase, thus the luminosity-to-mass ratio should be enhanced in the more evolved regions. This trend is found, with the respective distributions shifting toward a higher $L/M$ ratio across the ‘‘young”, ‘‘intermediate” and ‘‘evolved” protoclusters, although a significant dispersion is measured: for any pair of regions the mean values of $L / M$ are consistent with each other at a $\pm 1 \sigma$ level, where $\sigma$ is the standard deviation of the distribution. The large dispersion may be primarily attributed to intra-region variability: regions within the ALMA-IMF survey, despite their relatively small sizes of a few parsecs, can encompass subregions with differing characteristics. This may result in a blend of lower and higher $L / M$ ratios across the field of observations, as we observe in Fig. [10](#fig:LM-PDFs). This interpretation is reinforced by the fact that evolved regions display the largest dispersions. Indeed, evolved protoclusters may harbor a combination of young and more evolved subregions, pertaining to inhomogeneous initial conditions. Consequently, the spatially averaged $L / M$ ratio (over the extent of the ALMA footprint) may not systematically serve as a robust indicator of the global evolutionary stage of one protocluster.

In Fig. [11](#fig:PPMAP-decomposition), we illustrate the pixel-per-pixel spatial variations of the luminosity-to-mass ratio, specifically in the evolved G012.80 protocluster. Through a luminosity map clustering approach based on an arbitrary threshold ($\mathrm{log}(L / M) = 1.8$), we discern a broad correlation between areas exhibiting higher $L / M$ ratios and Hregions, that are traced by H41$\alpha$ and Neline emissions (cite: Beilis2022). This illustrates the capability to map luminosity-to-mass ratio variations at a 2.5$^{\prime \prime}$ angular resolution and to constrain the nature and evolutionary stage of resolved structures. In the subsequent subsection, we outline a method for estimating the luminosity-to-mass ratios of resolved luminosity peaks that may be extracted as individual sources.

### Source extraction with *getsf*

Here we aim to compile a systematic catalog encompassing the luminosity and mass estimates of luminosity peaks found in the PPMAP dataset. With a limited angular resolution of 2.5$^{\prime \prime}$, it is conceivable that certain sources may not correspond to single entities, but rather to clusters of luminous sources, that could include a mixture of protostars, pre-stellar cores, and ultra- or hyper-compact Hregions. Impending studies will attempt to perform cross-identifications based on already established core and protostar catalogs (Motte et al., in prep.). To identify sources within the luminosity maps, we employed the *getsf* method described by (cite: Menshchikov2021). We direct interested readers to that publication for a detailed exposition of the procedure. Below, the underlying principles and application criteria pertinent to our dataset are briefly summarized.

The *getsf* method entails a spatial deconstruction of observed images, effectively separating structural constituents and their background. The technique aims to parse distinct spatial scales and segregating sources and filaments from both one another and the background. Characterized by a single parameter, namely an approximate maximum size of sources to be extracted, detection yields initial approximations of source footprints, dimensions, and fluxes. Subsequently, more precise measurements of the source sizes and fluxes are conducted on background-subtracted images and, if warranted, on auxiliary images.

We executed the *getsf* algorithm on the PPMAP luminosity maps generated from Run2, that is, without taking into account the free-free subtraction performed by Galvan-Madrid et al. (in prep.). This choice is rooted in our goal to ensure the best representation of the bolometric luminosities of the PPMAP luminosity peaks, by including the contribution of free-free emission. In addition, PPMAP column density maps resulting from Run1 were simultaneously given to *getsf* as auxiliary data, in order to measure the mass of the sources. Our initial step involved a resampling of the luminosity maps targeted at achieving a three-pixel sampling of the PPMAP beam (as elaborated in Appendix [6.5](#appendix:resampling)), because it improves the detection of luminosity peaks associated with protostars. Furthermore, we fixed the maximum source size to 5$^{\prime \prime}$, a value equivalent to twice the dimensions of the PPMAP beam.

### Results of the *getsf* extraction

The outcomes of the *getsf* extraction process are presented in Table [\[table:compact-sources\]](#table:compact-sources). This table provides details including celestial coordinates, angular and spatial full width at half maximum (FWHM), background-subtracted luminosities and masses, as well as the luminosity-to-mass ratio of the PPMAP luminosity peaks. We estimated the completeness level of the catalog of 313 luminosity peaks to be $\sim 60$ $L_\odot$, with a tendency for a better completeness level in young regions ($\sim 30$ $L_\odot$) than in evolved ones ($\sim 100$ $L_\odot$). In some instances (18% of the peaks), the luminosity peaks have no counterparts in the column density maps, resulting in a mass below our detection threshold. These mass measurements are discarded and signalled by the symbol ‘‘-” (see Table [\[table:compact-sources\]](#table:compact-sources)). We interpret the luminosity peaks with no massive counterpart as diffuse areas heated by evolved protostars or Hregions.

The spatial distribution of the PPMAP luminosity peaks is superimposed on the column density and luminosity maps, in Figs. [6](#fig:PPMAPs) and [17](#fig:PPMAPs-supplementary). Upon visual examination, we observe a general correspondence between the PPMAP luminosity peaks and features such as dusty filaments, Hregions, clusters of cores and protostars extracted from the ALMA images. Correlations are also observed between PPMAP luminosity peaks and individual cores and/or protostars extracted from the ALMA images. A detailed cross-analysis of the PPMAP source catalog and the *getsf* core catalog extracted from ALMA continuum images falls beyond the scope of this paper and will be covered in a subsequent work by Motte et al. (in prep.).

The relation between the bolometric luminosity and mass is a useful metric to constrain the evolutionary stage of star forming objects. The PPMAP source sample spans a considerable range of luminosity-to-mass ratios, across four orders of magnitude (from $L / M \simeq 10^{-1}$ to $L / M \simeq 10^{3}$, in solar units). This range underscores the wide spectrum of physical conditions and object types encompassed within the sample, ranging from (bright) ultra- and hyper-compact Hregions to (faint) cold, massive star-forming cores. Due consideration must be given to the fact that a single PPMAP source may correspond to several blended objects, possibly of different nature, because of the limited angular resolution (2.5$^{\prime \prime}$).

In Fig. [12](#fig:LM), we present the distribution of masses and luminosities for the PPMAP source catalog, and its comparison with evolutionary tracks from (cite: Motte2018a) and (cite: Duarte-Cabral2013). The path of individual objects within the $M$-$L_\mathrm{bol}$ diagram can be predicted by accretion models. From a given initial envelope mass, the mass is expected to decrease at a given rate through material accretion onto the central star, in addition to material ejection by molecular outflows. The luminosity, on the other hand, is a function of stellar mass, hence it grows over time. These mechanisms steer the progression within the $M$-$L_{\mathrm{bol}}$ diagram from the top-left extremity to the end of the evolutionary tracks, allowing to follow the time evolution of cores and protostars. The positions of luminosity peaks shown in Fig. [12](#fig:LM) are generally consistent with the accretion models presented by (cite: Motte2018a) and (cite: Duarte-Cabral2013), although approximately 20% of the sources are above the 50 $M_\odot$ final stellar mass track. We interpret these massive sources as clusters of unresolved cores and/or protostars. Furthermore, we observe that although the distributions of luminosity peaks pertaining to evolved and young protoclusters are overlapping, their centroid diverge within the diagram, aligning with different segments of the evolutionary tracks. Indeed, the median values of the luminosity-to-mass ratio ($L / M$) of luminosity peaks demonstrate a trend across regions when classified based on their evolutionary stages, as outlined by (cite: Motte2022). Specifically, we measure mean $L / M$ values of 253.5, 12.8, and 12.3 $L_\ensuremath{\odot} / M_\ensuremath{\odot}$ for the luminosity peaks of evolved, intermediate, and young regions, respectively (with a respective dispersion around the mean of 100.0, 4.2 and 8.0 $L_\ensuremath{\odot} / M_\ensuremath{\odot}$, estimated by the mean absolute deviation).

![](images/LM.pdf)

## Summary & perspectives

Using the multiwavelength, multiresolution Bayesian algorithm PPMAP, we performed a SED analysis of the dust emission in the 15 ALMA-IMF protoclusters. Near-infrared to millimeter observations from 8 instruments were included in the MBB analysis, spanning angular resolutions from subarcsecond (ALMA) to 35.2$^{\prime \prime}$ (*Herschel*). Our results are the following:

1.  We present new measurements of the bolometric luminosity, column density and dust temperature toward the 15 massive ALMA-IMF protoclusters (Tab. [\[table:Results\]](#table:Results), Fig. [3](#fig:SEDs)). The PPMAP estimates are consistent with previous measurements at a coarser angular resolution ((cite: Koenig2017), Fig. [7](#fig:Koenig2017Benchmark)), and thus constitute a benchmarked mapping of the dust parameters at the best angular resolution currently attainable (2.5$^{\prime \prime}$).

2.  We compared our column density and dust temperature maps with the continuum cores identified by (cite: Louvet2024), the hot cores identified by (cite: Bonfand2024) and the N$_2$H$^+$ J=1–0 line, showing that the 2.5$^{\prime \prime}$ features found in the PPMAP products are consistent with sources and structures mapped at ALMA’s native resolution, 0.3$^{\prime \prime}$-0.9$^{\prime \prime}$ (Fig. [6](#fig:PPMAPs), Fig. [17](#fig:PPMAPs-supplementary), Fig. [9](#fig:PPMAP-N2H+)).

3.  The pixel-per-pixel analysis of the luminosity-to-mass ratio shows that more evolved regions have, on average, a larger luminosity-to-mass ratio, although intra-region variability is observed (Fig. [10](#fig:LM-PDFs)). We show, with an example in the G012.80 protocluster, that subregions pertaining to different evolutionary stages can be separated by setting a luminosity-to-mass ratio threshold (Fig. [11](#fig:PPMAP-decomposition)).

4.  Using *getsf* (cite: Menshchikov2021) on the PPMAP bolometric luminosity maps, we have extracted a catalog of 313 PPMAP sources, with the associated bolometric luminosity and mass measurements (Tab. [\[table:compact-sources\]](#table:compact-sources)). We find that the luminosity-to-mass ratio of PPMAP sources tends to be consistent with the evolutionary stage attributed to the different protoclusters ((cite: Motte2022), Galván-Madrid et al., in prep.). We compared the PPMAP sources with evolutionary tracks from (cite: Duarte-Cabral2013) and (cite: Motte2018a), although the comparison is biased by the fact that one PPMAP source may correspond to several unresolved cores and/or protostars (Fig. [12](#fig:LM)).

Numerous potential directions stem from our current findings. Our analysis resulted in the determination of luminosity-to-mass ratios across ALMA footprints, ATLASGAL sources’ footprints, and PPMAP luminosity peaks extracted via *getsf*. Our catalog of 313 luminosity peaks presents a resource for forthcoming investigations. The cross-identification of PPMAP luminosity peaks with Hregions offers a pathway to estimate their luminosities. The dataset of column density, temperature, and luminosity maps we provide opens doors to investigate relationships among these quantities. Furthermore, the PPMAP-derived column density, in conjunction with PPMAP source and core catalogs, lays the groundwork for examining core formation efficiency and its dependence with the local gas density at a 2.5$^{\prime \prime}$ angular resolution, following the original study by (cite: Louvet2014) in W43-MM1.

Finally, despite potential challenges related to associating single PPMAP source with multiple protostars, our catalog may help constraining the temperatures and luminosity-to-mass ratios of young stellar objects. Assuming that a robust cross-identification can be completed, the catalog enables a direct comparison with accretion models, based on the $M_\mathrm{core}$ versus $L_\mathrm{bol}$ evolutionary diagram (e.g., (cite: Duarte-Cabral2013)). One such study, underway by Motte et al. (in prep.), focuses on cross-identification and further processing of PPMAP-derived temperatures to estimate core and protostar temperatures and luminosities.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01355.L, #2013.1.01365.S, and #2015.1.01273.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This project has received funding from the European Research Council (ERC) via the ERC Synergy Grant ECOGAL (grant 855130), from the French Agence Nationale de la Recherche (ANR) through the project COSMHIC (ANR-20- CE31-0009), and the French Programme National de Physique Stellaire and Physique et Chimie du Milieu Interstellaire (PNPS and PCMI) of CNRS/INSU (with INC/INP/IN2P3). MB is a postdoctoral fellow in the University of Virginia’s VICO collaboration and is funded by grants from the NASA Astrophysics Theory Program (grant number 80NSSC18K0558) and the NSF Astronomy & Astrophysics program (grant number 2206516). AS gratefully acknowledges support by the Fondecyt Regular (project code 1220610), and ANID BASAL project FB210003.

99 natexlab

(ref: Aguirre2011) Aguirre, J. E., Ginsburg, A. G., Dunham, M. K., et al. 2011, ApJS, 192, 4

(ref: Allamandola1985) Allamandola, L. J., Tielens, A. G. G. M., & Barker, J. R. 1985, ApJL, 290, L25

(ref: Aniano2012) Aniano, G., Draine, B. T., Calzetti, D., et al. 2012, ApJ, 756, 138

(ref: Armante2024) Armante, M., Gusdorf, A., Louvet, F., et al. 2024, arXiv e-prints, arXiv:2401.09203

(ref: Arzoumanian2011) Arzoumanian, D., André, P., Didelon, P., et al. 2011, A&A, 529, L6

(ref: Balog2014) Balog, Z., Müller, T., Nielbock, M., et al. 2014, Experimental Astronomy, 37, 129

(ref: Bates2023) Bates, M. L. & Whitworth, A. P. 2023, MNRAS

(ref: Beilis2022) Beilis, D., Beck, S., & Lacy, J. 2022, MNRAS, 509, 2234

(ref: Benjamin2003) Benjamin, R. A., Churchwell, E., Babler, B. L., et al. 2003, PASP, 115, 953

(ref: Bocchio2016) Bocchio, M., Bianchi, S., & Abergel, A. 2016, A&A, 591, A117

(ref: Bonfand2024) Bonfand, M., Csengeri, T., Bontemps, S., et al. 2024, arXiv e-prints, arXiv:2402.15023

(ref: Busquet2011) Busquet, G., Estalella, R., Zhang, Q., et al. 2011, A&A, 525, A141

(ref: Carey2009) Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, PASP, 121, 76

(ref: Chawner2020) Chawner, H., Howard, A. D. P., Gomez, H. L., et al. 2020, MNRAS, 499, 5665

(ref: Chawner2019) Chawner, H., Marsh, K., Matsuura, M., et al. 2019, MNRAS, 483, 70

(ref: Chuss2019) Chuss, D. T., Andersson, B. G., Bally, J., et al. 2019, ApJ, 872, 187

(ref: Contreras2013) Contreras, Y., Schuller, F., Urquhart, J. S., et al. 2013, A&A, 549, A45

(ref: Csengeri2016) Csengeri, T., Leurini, S., Wyrowski, F., et al. 2016, A&A, 586, A149

(ref: Csengeri2014) Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75

(ref: Cunningham2023) Cunningham, N., Ginsburg, A., Galván-Madrid, R., et al. 2023, arXiv e-prints, arXiv:2306.14710

(ref: Deforest2004) DeForest, C. E. 2004, Sol. Phys., 219, 3

(ref: Diaz2023) Dı́az-González, D. J., Galván-Madrid, R., Ginsburg, A., et al. 2023, ApJS, 269, 55

(ref: Duarte-Cabral2013) Duarte-Cabral, A., Bontemps, S., Motte, F., et al. 2013, A&A, 558, A125

(ref: Duley&Williams1981) Duley, W. W. & Williams, D. A. 1981, MNRAS, 196, 269

(ref: Egan2003) Egan, M. P., Price, S. D., Kraemer, K. E., et al. 2003, VizieR Online Data Catalog, V/114

(ref: Elia2010) Elia, D., Schisano, E., Molinari, S., et al. 2010, A&A, 518, L97

(ref: Engelbracht2007) Engelbracht, C. W., Blaylock, M., Su, K. Y. L., et al. 2007, PASP, 119, 994

(ref: Galametz2014) Galametz, M., Albrecht, M., Kennicutt, R., et al. 2014, MNRAS, 439, 2542

(ref: Galametz2012) Galametz, M., Kennicutt, R. C., Albrecht, M., et al. 2012, MNRAS, 425, 763

(ref: Galliano2018) Galliano, F., Galametz, M., & Jones, A. P. 2018, ARA&A, 56, 673

(ref: Giannetti2013) Giannetti, A., Brand, J., Sánchez-Monge, Á., et al. 2013, A&A, 556, A16

(ref: Ginsburg2020) Ginsburg, A., Anderson, L. D., Dicker, S., et al. 2020, ApJS, 248, 24

(ref: Ginsburg2022) Ginsburg, A., Csengeri, T., Galván-Madrid, R., et al. 2022, A&A, 662, A9

(ref: Ginsburg2013) Ginsburg, A., Glenn, J., Rosolowsky, E., et al. 2013, ApJS, 208, 14

(ref: Guzman2015) Guzmán, A. E., Sanhueza, P., Contreras, Y., et al. 2015, ApJ, 815, 130

(ref: Harper2018) Harper, D. A., Runyan, M. C., Dowell, C. D., et al. 2018, Journal of Astronomical Instrumentation, 7, 1840008

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hill2011) Hill, T., Motte, F., Didelon, P., et al. 2011, A&A, 533, A94

(ref: Holland2013) Holland, W. S., Bintley, D., Chapin, E. L., et al. 2013, MNRAS, 430, 2513

(ref: Howard2020) Howard, A. D. P. 2020, PhD thesis, Cardiff University

(ref: Howard2021) Howard, A. D. P., Whitworth, A. P., Griffin, M. J., Marsh, K. A., & Smith, M. W. L. 2021, MNRAS, 504, 6157

(ref: Howard2019) Howard, A. D. P., Whitworth, A. P., Marsh, K. A., et al. 2019, MNRAS, 489, 962

(ref: Immer2014) Immer, K., Galván-Madrid, R., König, C., Liu, H. B., & Menten, K. M. 2014, A&A, 572, A63

(ref: Jones2017) Jones, A. P., Köhler, M., Ysard, N., Bocchio, M., & Verstraete, L. 2017, A&A, 602, A46

(ref: Juvela2015) Juvela, M., Demyk, K., Doi, Y., et al. 2015, A&A, 584, A94

(ref: Kainulainen2009) Kainulainen, J., Beuther, H., Henning, T., & Plume, R. 2009, A&A, 508, L35

(ref: Kelly2012) Kelly, B. C., Shetty, R., Stutz, A. M., et al. 2012, ApJ, 752, 55

(ref: Kohler2014) Köhler, M., Habart, E., Arab, H., et al. 2014, A&A, 569, A109

(ref: Koehler2015) Köhler, M., Ysard, N., & Jones, A. P. 2015, A&A, 579, A15

(ref: Koenig2017) König, C., Urquhart, J. S., Csengeri, T., et al. 2017, A&A, 599, A139

(ref: Konyves2020) Könyves, V., André, P., Arzoumanian, D., et al. 2020, A&A, 635, A34

(ref: Ladjelate2020) Ladjelate, B., André, P., Könyves, V., et al. 2020, A&A, 638, A74

(ref: Lee2004) Lee, J.-E., Bergin, E. A., & Evans, Neal J., I. 2004, ApJ, 617, 360

(ref: Leger&Puget1984) Leger, A. & Puget, J. L. 1984, A&A, 137, L5

(ref: Leys2013) Leys, C., Ley, C., Klein, O., Bernard, P., & Licata, L. 2013, Journal of Experimental Social Psychology, 49, 764–766

(ref: Lin2019) Lin, Y., Csengeri, T., Wyrowski, F., et al. 2019, A&A, 631, A72

(ref: Lin2017) Lin, Y., Liu, H. B., Dale, J. E., et al. 2017, ApJ, 840, 22

(ref: Lin2016) Lin, Y., Liu, H. B., Li, D., et al. 2016, ApJ, 828, 32

(ref: Louvet2014) Louvet, F., Motte, F., Hennebelle, P., et al. 2014, A&A, 570, A15

(ref: Louvet2024) Louvet, F., Sanhueza, P., & Stutz, A. 2024, A&A, submitted

(ref: Marsh2006) Marsh, K. A., Velusamy, T., & Ware, B. 2006, AJ, 132, 1789

(ref: Marsh2015) Marsh, K. A., Whitworth, A. P., & Lomax, O. 2015, MNRAS, 454, 4282

(ref: Marsh2017) Marsh, K. A., Whitworth, A. P., Lomax, O., et al. 2017, MNRAS, 471, 2730

(ref: Menshchikov2016) Men’shchikov, A. 2016, A&A, 593, A71

(ref: Menshchikov2021) Men’shchikov, A. 2021, A&A, 649, A89

(ref: Molinari2016) Molinari, S., Schisano, E., Elia, D., et al. 2016, A&A, 591, A149

(ref: Molinari2010) Molinari, S., Swinyard, B., Bally, J., et al. 2010, PASP, 122, 314

(ref: Motte2001) Motte, F. & André, P. 2001, A&A, 365, 440

(ref: Motte2022) Motte, F., Bontemps, S., Csengeri, T., et al. 2022, A&A, 662, A8

(ref: Motte2018a) Motte, F., Bontemps, S., & Louvet, F. 2018a, ARA&A, 56, 41

(ref: Motte2018b) Motte, F., Nony, T., Louvet, F., et al. 2018b, Nature Astronomy, 2, 478

(ref: Motte2010) Motte, F., Zavagno, A., Bontemps, S., et al. 2010, A&A, 518, L77

(ref: Mottram2017) Mottram, J. C., van Dishoeck, E. F., Kristensen, L. E., et al. 2017, A&A, 600, A99

(ref: NguyenLuong2013) Nguyen-Lu’o’ng, Q., Motte, F., Carlhoff, P., et al. 2013, ApJ, 775, 88

(ref: Ossenkopf&Henning1994) Ossenkopf, V. & Henning, T. 1994, A&A, 291, 943

(ref: Palmeirim2013) Palmeirim, P., André, P., Kirk, J., et al. 2013, A&A, 550, A38

(ref: Pety2017) Pety, J., Guzmán, V. V., Orkisz, J. H., et al. 2017, A&A, 599, A98

(ref: Pillai2023) Pillai, T. & Simplifi Team. 2023, in American Astronomical Society Meeting Abstracts, Vol. 55, American Astronomical Society Meeting Abstracts, 308.03

(ref: Planck2014) Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2014, A&A, 571, A11

(ref: Pouteau2022) Pouteau, Y., Motte, F., Nony, T., et al. 2022, A&A, 664, A26

(ref: Reach2005) Reach, W. T., Megeath, S. T., Cohen, M., et al. 2005, PASP, 117, 978

(ref: Richardson&Marsh1987) Richardson, J. M. & Marsh, K. A. 1987, Acoustical Imaging, 615

(ref: Richardson&Marsh1992) Richardson, J. M. & Marsh, K. A. 1992, Maximum Entropy and Bayesian Methods, 213

(ref: Sanhueza2012) Sanhueza, P., Jackson, J. M., Foster, J. B., et al. 2012, ApJ, 756, 60

(ref: Schirmer2020) Schirmer, T., Abergel, A., Verstraete, L., et al. 2020, A&A, 639, A144

(ref: Schneider2015) Schneider, N., Ossenkopf, V., Csengeri, T., et al. 2015, A&A, 575, A79

(ref: Schneider2022) Schneider, N., Ossenkopf-Okada, V., Clarke, S., et al. 2022, A&A, 666, A165

(ref: Schuller2009) Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415

(ref: Shetty2009) Shetty, R., Kauffmann, J., Schnee, S., Goodman, A. A., & Ercolano, B. 2009, ApJ, 696, 2234

(ref: Temi2018) Temi, P., Hoffman, D., Ennico, K., & Le, J. 2018, Journal of Astronomical Instrumentation, 7, 1840011

(ref: Traficante2011) Traficante, A., Calzoletti, L., Veneziani, M., et al. 2011, MNRAS, 416, 2932

(ref: Urquhart2014) Urquhart, J. S., Csengeri, T., Wyrowski, F., et al. 2014, A&A, 568, A41

(ref: Vaillancourt2016) Vaillancourt, J. 2016, Characterizing the FIR polarization spectrum in Galactic Clouds, SOFIA Proposal, Cycle 5, ID. 05_0038

(ref: Valtchanov2018) Valtchanov, I., Hopwood, R., Bendo, G., et al. 2018, MNRAS, 475, 321

(ref: Whitworth2019) Whitworth, A. P., Marsh, K. A., Cigan, P. J., et al. 2019, MNRAS, 489, 5436

(ref: Wienen2018) Wienen, M., Wyrowski, F., Menten, K. M., et al. 2018, A&A, 609, A125

(ref: Wienen2012) Wienen, M., Wyrowski, F., Schuller, F., et al. 2012, A&A, 544, A146

(ref: Ysard2019) Ysard, N., Koehler, M., Jimenez-Serra, I., Jones, A. P., & Verstraete, L. 2019, A&A, 631, A88

(ref: Zhang2021) Zhang, H. & Brandt, T. D. 2021, AJ, 162, 139

# Technical insights into the PPMAP implementation

![](images/PPMAP_flow.pdf)

In this appendix, we provide a comprehensive overview of the systematic steps employed while using the PPMAP software for the data analysis. The following sections outline the process, starting from the preparation of input continuum maps and point spread functions (PSFs) to the post-correction procedures applied to the PPMAP data products. Fig [13](#fig:PPMAPflowchart) represents a flow chart of these procedures.

## Preprocessing

### Correction of saturated pixels

Several *Herschel*/PACS and *Herschel*/SPIRE maps exhibit saturation in the regions around the brightest sources, particularly within the peak of the spectral energy distribution (around 160-250 $\upmu$m). As a result, some pixels in these regions contain ‘‘NaN” values, rendering the use of PPMAP impossible for these affected maps. To address this issue, we took the following steps:

1.  In severe cases of saturation (11 out of 124 images in our study), where a significant portion of the map was affected ($\geq 25$%) and the data quality was compromised, we chose to entirely remove these maps from the pool of input data.

2.  In cases where the saturation level was lower (less than 25% of the map is saturated), we applied interpolation to estimate the missing values. We used the `astrofix` Python package (cite: Zhang2021), that employs Gaussian process regression for this purpose. In this process, the algorithm used the unsaturated areas of the available input images as a training set to learn and determine the missing values, using an optimized Gaussian interpolation kernel (as shown in Fig. [1](#fig:datacompleteness), 25 out of 124 images underwent interpolation for the present study, with a median of 6 interpolated pixels per image).

Figure [1](#fig:datacompleteness) illustrates the extent of the pixels replaced using interpolation in the affected *Herschel* maps. We acknowledge that interpolating missing pixels, especially in regions of high intensity peaks, can be an uncertain procedure. To quantify the uncertainties associated with this treatment, we performed two iterations of the PPMAP analysis: one with the interpolated maps and the other without any interpolation (excluding the saturated maps from the analysis). By comparing the results between these two iterations, we measured the discrepancies introduced by the interpolation process. These discrepancies were then propagated into the final uncertainty maps released with this study (see Sect. [4.3.2](#subsect:systematic-errors) and Table [1](#table:systematic-errors)).

### Preparation of point spread functions

To combine a set of input images with different angular resolutions, PPMAP requires accurate Point Spread Function (PSF) profiles. The current PPMAP version[^4] is shipped with *Herschel* PSFs projected on $256 \times 256$ frames. We replaced these files with new ones projected on a larger $2048 \times 2048$ frame. This adjustment was necessary to ensure correct sampling of both the higher-resolution (ALMA) and lower-resolution (*Herschel*) PSFs while using a single array size for all PSFs, as required by PPMAP. The PSFs we used for *Herschel*/SPIRE (at 250, 350, and 500 $\upmu$m) were downloaded from the *Herschel* science archive[^5], while those for *Herschel*/PACS (at 70 and 160 $\upmu$m) were obtained from (cite: Bocchio2016). (cite: Traficante2011) reported that the beams in the Hi-GAL images are elongated because of the sampling procedure adopted in the Galactic plane survey, with an ellipticity lower than 15% across all bands. We produced our own synthetic beam profile for SABOCA, LABOCA, and ALMA observations using the `Gaussian2DKernel` function from the `astropy.convolution` package in Python.

![image](images/G012-ff-subff.pdf) ![image](images/G012-ff-subff_lum.pdf)

### Free-free emission in the ALMA 1.3 mm emission map

As introduced in Sect. [2](#sect:observations), to mitigate the contamination by free-free emission, we have excluded the ALMA Band 3 data from the PPMAP inputs. In addition, we employed two versions of ALMA Band 6 observations : the ‘‘native” version, and a free-free subtracted version, following a process detailed by Galván-Madrid et al. (in prep.). The subtraction method relied on the H41$\alpha$ line emission to disentangle the thermal emission of dust grains from the free-free emission. This was achieved by assuming an electron temperature of $7000$ K and variable helium abundances, depending on the specific region under consideration. Throughout the PPMAP analysis, we either used the free-free subtracted maps to obtain the dust temperature and column density maps (refered to as the PPMAP ‘‘Run1”), or the native ALMA Band 6 maps to estimate the luminosity (refered to as the PPMAP ‘‘Run2”). The motivations for these two runs are described in Sect. [3.2](#sect:PPMAPanalysis). In Fig. [14](#fig:free-free), we emphasize the distinctions in the PPMAP-derived column density between the Run1 (without free-free emission) and Run2 (with free-free emission) outcomes. While the overall column density within the ALMA footprint registers a mere 12.5% increment between the two instances, the column density estimate is significantly enhanced toward localized areas (up to a factor 20). This increase is particularly pronounced around the G012.80 Main-Central and Main-North Hregions as outlined by (cite: Armante2024). Conversely, the impact of the free-free removal process on the Main-West filament is minimal (relative difference below 10%), reinforcing its classification as a primarily dusty filament. The disparity between Run1 and Run2 underscores that the free-free subtraction is necessary to precisely estimate the column density in evolved regions.

## PPMAP SED fitting

### Determination of measurement errors

As discussed in Sect. [3.1](#sect:PPMAPdescription), the PPMAP Bayesian fitting procedure necessitates accurate error estimates, in order to attribute a correct weight to the input observations. We explored three distinct methods to determine the noise:

1.  First method (applied to ALMA, LABOCA, SABOCA observations): Assuming a Gaussian distribution for the sky noise, we conducted a Gaussian fit of the data histograms to extract the standard deviation (referred to as $\sigma_1$).

2.  Second method (applied to *Herschel* observations): due to the high signal-to-noise sky background associated with *Herschel* maps, the first method was not applicable. Instead, we employed the built-in PPMAP noise estimate function, `getnoise`, by setting the `sigobs` input parameter to 0 in the `premap` routine (cite: Marsh2015). Using Gaussian kernels of variable scales, this function facilitates the measurement of sky noise through iterative subtraction of a smoothed background (referred to as $\sigma_2$).

3.  Finally, in a third attempt to estimate the noise, we calculated the median absolute deviation (referred to as ‘‘MAD”, and denoted as $\sigma_3$) in empty areas of the observed fields (searching for such empty areas in a 30$^\prime$ radius around the *Herschel* field center coordinates). MAD is a robust statistic that provides an estimate of the image noise, based on the median of the absolute deviations from the median pixel value in the image (cite: Leys2013).

Based on our investigation, when applied to ALMA, LABOCA, and SABOCA observations, all three noise measurement methods exhibited a general agreement, with relative differences within the range of 30-60% when compared to $\sigma_2$ (the noise estimate obtained from the PPMAP built-in subroutine). The specific values of these relative differences depended on the regions being analyzed. We always observed that $\sigma_2 > \sigma_1 > \sigma_3$, indicating that the third method consistently yields lower noise estimates compared to the other two methods. This outcome is particularly beneficial since it effectively increases the weight of the 1.3 mm image, thus allowing a better representation of the low signal-to-noise features in the observed protoclusters (such as faint cores).

Therefore, we incorporated the median absolute deviation measurement, along with the systematic error on the absolute flux calibration of the sky background $F_\mathrm{\lambda}^\mathrm{sky}$, to estimate the total errors for each input map at a given wavelength $\lambda$ (e.g., $\sigma_{70\mathrm{\upmu m}}$, $\sigma_{350\mathrm{\upmu m}}$, $\sigma_{870\mathrm{\upmu m}}$, $\sigma_{1.3\mathrm{mm}}$, etc). The error estimates $\sigma_\lambda$ were computed as follows:

$$\begin{equation}
\label{eq:error-estimate}
\sigma_\lambda = \mathrm{MAD}(F_\lambda) + u_\lambda F_\mathrm{\lambda}^\mathrm{sky} ,
\end{equation}$$ where, MAD$(F_\lambda)$ represents the median absolute deviation measured in the map $F_\lambda$, and $u_\lambda$ denotes the absolute flux calibration error (e.g., 15% for LABOCA, as discussed in Sect. [2](#sect:observations)). The resulting values of $\sigma_\lambda$ were subsequently assigned to the input parameter `sigobs` for the corresponding wavelengths. The relative contribution of the two terms in Eq. ([\[eq:error-estimate\]](#eq:error-estimate)) varies significantly depending on the map. In typical low signal-to-noise pixels (dominated by Gaussian noise in the ALMA observations), the error estimates for *Herschel* maps are primarily dominated by the sky background component, while the MAD component is the largest contributor to the ALMA Band 6 errors.

### *Herschel* color correction

We applied color corrections to the *Herschel*/PACS and SPIRE observations (see (cite: Balog2014); (cite: Valtchanov2018) and references therein). These corrections are taken directly from the PACS and SPIRE user manuals, and consider the observed flux in each band as an integral over the product of the instrumental bandpass and the source’s spectrum, assuming a MBB profile with $\beta = 2$. The correction tables used in our analysis are consistent with the correction factors used in (cite: Motte2018b) for the PPMAP analysis of W43-MM1. These color corrections are provided to PPMAP as input tables and then automatically applied during the analysis. While it is ideally more accurate to include the color corrections, their effect on the PPMAP outcome is minimal ($< 1$% in relative variation of the column density and temperature estimates) and can be considered negligible in our analysis, with respect to other sources of uncertainties.

### PPMAP parameters

|  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |
| Input parameter | Description | Adopted value |  |  |  |
|  |  |  |  |  |  |
| `pixel` | sampling ($^{\prime \prime}$) | 1.25 (a) |  |  |  |
| `ncells` | cell size (px) | 60 (a) |  |  |  |
| `noverlap` | cell overlap (px) | 40, 50 (a) |  |  |  |
| `kappa`300 | ref. opacity (cm$^2$ g$^{-1}$) | 0.1 (b) |  |  |  |
| `eta` | $\eta$ (*a priori* dilution) | 0 (c) |  |  |  |
| `maxiterat` | maximum nb. of iterations | 10 000 |  |  |  |
| `beta` | $\beta$ (dust opacity) | 1.8 |  |  |  |
| `Nt` | nb. of MBB components | 8 |  |  |  |
| `temprange` | $T_\mathrm{dust}$ (K) | 10 – 50 |  |  |  |
| `sigobs` | measurement error | see Sect. [6.2.1](#sect:noise) |  |  |  |
| `highpass` | high-pass filtering | ‘‘yes” (d) |  |  |  |

: PPMAP input parameters.

\
 \

The parameters listed above are entered in the input file `premap.inp`. The reference opacity at 300 $\upmu$m is defined with respect to the total mass (cite: Marsh2015).\
(a) The maps are Nyquist-sampled with pixels of size 1.25$^{\prime \prime}$, hence the synthetic resolution is 2.5$^{\prime \prime}$. `noverlap` $\geq 0.5$ `ncells` is recommended by the PPMAP user manual. With `ncells` $=60$ and `noverlap` $=40$, all ALMA-IMF regions are contained either in a $3 \times 3$ or $5 \times 5$ mosaic. In some cases we increased `noverlap` to 50 in order to enhance the quality of the subfields seaming, thereby using $7 \times 7$ mosaics.\
(b) The reference opacity $\kappa_{300}$ is defined by Eq. ([\[eq:Kappa300\]](#eq:Kappa300)).\
(c) The *a priori* dilution input parameter, ‘‘`eta`”, characterizes the degree to which the procedure is forced to represent the data with the least number of ‘‘points’’ (that is, with the least number of MBB components with distinct dust temperatures $T_\mathrm{dust}$ ). Values in the range 0.01 – 1 are recommended, but setting the input to ‘‘0” causes an internal PPMAP subroutine to adopt a default value, defined as $\eta = N_\mathrm{prior} / N_\mathrm{states}$, where $N_\mathrm{prior}$ is the maximum number of components that the data may constrain, and $N_\mathrm{states} = N_X \times N_Y \times N_T \times N_\beta$ is the number of states that a ‘‘point” can occupy (see Sect. [3.1](#sect:PPMAPdescription)).\
(d) Enables a PPMAP subroutine to subtract mean value from model and ground-based observed images during the SED fitting process.\

The fixed PPMAP parameters adopted in our initial analysis are shown in Table [2](#table:PPMAPfixedparams). Following previous applications of PPMAP (e.g., (cite: Marsh2017); (cite: Howard2019); (cite: Whitworth2019); (cite: Chawner2020); (cite: Howard2021)), we assumed that we can reproduce the observations in the FIR to submm (70 $\upmu$m to 1.3 mm) with 8 MBB components between 10 K and 50 K (using a logarithmic spacing). We have systematically checked that allowing PPMAP to employ lower or higher temperature components does not provide a substantial change in column density $N_\mathrm{H_2}$ and luminosity (within $\pm$5%). Ground-based input images inherently suppress low spatial frequencies. To address this, we enabled the input parameter `highpass` (see note on Table [2](#table:PPMAPfixedparams) footnote (d)), allowing PPMAP to subtract a constant background from the internal model images. This subtraction is applied at wavelengths corresponding to the ground-based data (SABOCA, LABOCA, and ALMA). The goal is to enhance the alignment between the model and the spatial characteristics of these particular observations, ultimately improving the fitting process. We adopted a standard reference opacity $\kappa_{300}=0.1~\mathrm{cm^2g^{-1}}$, defined with respect to the total mass and corresponding to a gas-to-dust ratio of 100 ((cite: Marsh2015); (cite: Hildebrand1983)). Based on previous studies ((cite: Planck2014); (cite: Juvela2015); (cite: Koehler2015) and references therein for more diffuse gas), in a first approach we fixed the dust opacity to $\beta = 1.8$ for all regions. If we were to assume $\beta = 2$, the estimated dust temperatures would likely be lower (see Table [1](#table:systematic-errors)). Finally, to balance between our high-resolution requirements and potential artifact-inducing effects, we adopted a synthetic angular resolution of 2.5$^{\prime \prime}$ for the analysis. In fact, extensive testing of PPMAP indicated that further reducing the angular resolution could lead to stronger ring-like artifacts (see Appendix [6.4](#appendix:post-processing)).

### Temperature and opacity index optimization

Based on our first series of PPMAP runs, performed with a fixed temperature range ($T_\mathrm{dust} = 10-50$ K, using 8 MBB components) and fixed opacity index ($\beta=1.8$), we refined the input temperature range. From the temperature distributions measured in the zero-order PPMAP output, we systematically lowered the amplitude of the temperature range (e.g., from $T_\mathrm{dust} = 10-50$ K to $T_\mathrm{dust} = 21-39$ K in G012.80). This adjustment allowed us to obtain more precise temperature estimates for the sources, by decreasing the $\Delta T$ interval between the temperature components. Additionally, we explored the possibility of making the opacity index, $\beta$, a free parameter in the PPMAP analysis. To achieve this, we conducted iterative runs, modifying the value of $\beta$ in increments of $\Delta \beta = 0.1$, while measuring the corresponding change in chi-square ($\chi^2$). Following this procedure, we found a best-fit value of the opacity index, that could be different from $\beta=1.8$ (between $\beta=1.4$ and $\beta=2.1$, depending on the specific fields of observation). However, we acknowledge that the degeneracy between the temperature and opacity index makes our attempt at simultaneously constraining them uncertain. The variations in $\chi^2$ associated with the modification of $\beta$ were negligible compared to the expected $\chi^2$ variation at a $1 \sigma$ level. More precisely, for any $\beta_i$ and $\beta_j$, we found that $\Delta \chi^2 (\beta_i, \beta_j) \ll [(1 + 1 / (N - p)] \mathrm{min}(\chi^2)$, where $N$ is the number of data points used to fit the modified blackbody and $p$ is the number of parameters. As a result, we decided to fix $\beta = 1.8$ for all regions, and focused on the determination of the temperature. We acknowledge the potential uncertainty in the opacity index, that may differ significantly from the assumed value of $\beta = 1.8$ across the ALMA-IMF protoclusters. To explore the impact of different opacity indices, we assessed variations in the PPMAP-derived temperature. For instance, we observed average changes of $\Delta T_\mathrm{dust} = + 3$ K and $\Delta T_\mathrm{dust} = + 12$ K when adopting $\beta = 1.5$ and $\beta = 1$ (representative of more evolved dust in denser media), respectively.

### Criteria to stop PPMAP iterations

The quality of PPMAP outputs underwent a systematic validation process through an a posteriori chi-square test, where we manually compared the synthetic fluxes obtained from the PPMAP model to the actual observed fluxes. Based on this a posteriori validation of the product’s reliability, we monitored the convergence of the PPMAP iterative process to prevent over-fitting, that can lead to increasingly severe ring-like artifacts in the column density and temperature maps (Sect. [6.4](#appendix:post-processing)). We refer to this particular effect as ‘‘over-fitting”, since the associated change in synthetic flux is minimal with respect to measurement errors. We systematically controlled for and prevented over-fitting through minor tweaks of the PPMAP iteration number, while validating the outcome through the aforementioned chi-square test. These adjustments were necessary to strike a balance and ensure the best representation of the observed data without introducing excessive artifacts. Most importantly, we note that although it does mitigate the growth of the spurious features, this validation process does not prevent their development.

![](images/tcorr.pdf)

## Dust temperature post-correction

PPMAP relies on the assumption that the dust emission is optically thin. However, this assumption is not met in regions with high-density spikes, such as cores in high-mass star-forming regions. To account for the effect of larger optical depths, we used a procedure established in previous work (first applied by (cite: Motte2018b) in the analysis of W43-MM1) to correct the dust temperature maps generated by PPMAP. The temperature correction table used in this procedure was constructed based on a grid of model sources with varying temperatures ($T_\mathrm{dust}^\mathrm{model}$), optical depths, sizes, and measurement errors. The synthetic sources were represented by the simplest model possible: a uniform dust slab with specified temperature and optical depth. Using this simple dust model, we produced synthetic flux density maps between 70 $\upmu$m and 3 mm. Then, we applied PPMAP to the synthetic flux density maps to provide an estimate for the column density $N(\mathrm{H_2})$ and temperature $T_\mathrm{dust}^\mathrm{PPMAP}$. Using different dust model parameters, we sampled the relationship $\Delta T_\mathrm{dust} = f(N(\mathrm{H_2}), T_\mathrm{dust}^\mathrm{PPMAP})$ between the temperature bias $\Delta T_\mathrm{dust} = T_\mathrm{dust}^\mathrm{PPMAP} - T_\mathrm{dust}^\mathrm{model}$, the PPMAP-derived column density $N(\mathrm{H_2})$ and the PPMAP-derived dust temperature $T_\mathrm{dust}^\mathrm{PPMAP}$. This investigation enabled the implementation of an a posteriori correction. The established relationship is depicted in Fig. [15](#fig:tcorr), covering the initial range of explored temperature and column densities. In fact, the original correction table provided by (cite: Motte2018b) is constrained within certain limits, insufficient to accommodate our PPMAP products. To extend the correction beyond these limits, we performed an extrapolation using cubic splines while assessing the quality and reliability of the extrapolated results. Subsequently, we applied the extrapolated correction table to the PPMAP outputs a posteriori to account for the effect of optical depth on the dust temperature estimates. In each pixel of the PPMAP outputs, temperatures are updated using the tabulated value $\Delta T_\mathrm{dust} = f(N(\mathrm{H_2}), T_\mathrm{dust})$. The impact of the correction on the column density is considered negligible, since the added warm dust represents a minor contribution to the total mass. It is essential to note that this correction is based on a simplified model and may not be fully suitable for the diverse environments observed in the ALMA-IMF fields, including Hregions, internally heated protostellar envelopes and prestellar cores (Motte et al., in prep.). Despite its limitations, this correction helps compensate for the assumption of optical thinness of PPMAP and should be considered when aiming to constrain the temperature in regions with potential optical depth effects such as ALMA-IMF protoclusters.

## PPMAP ring-like artifacts and post-processing

Temperature and column density maps generated with PPMAP often exhibit ring-like artifacts, as shown in Fig. [16](#fig:artifacts). These artifacts consistently appear around sources of significant brightness, and their intensity grows with the brightness of the source they are associated with. They generally occur either as complete or partial spurious rings around a source, and in the most extreme case are accompanied by secondary peaks (cf. Fig. [16](#fig:artifacts), first panel). The underlying cause of these ring-like artifacts may be attributed to several inter-twinned factors. Firstly, PSF errors and missing spatial frequencies between the ALMA images and the rest of the observations could produce these artifacts. Secondly, due to the strong dependence of emission on temperature, PPMAP may fail to reproduce steep temperature gradients around bright sources, thus causing ring-like artifacts. Lastly, the violation of PPMAP’s assumption of optically thin emission toward spikes in column density may also contribute to errors (cite: Howard2020). As reported in Appendix [6.2.5](#appendix:convergence), elevating the number of PPMAP iterations beyond a certain threshold amplifies these spurious patterns. This emphasizes the importance of accurately assessing measurement errors and controlling the number of iterations to prevent over-fitting. Most importantly, the presence of ring-like artifacts may introduce a bias in determining the temperatures of cores. To gauge the extent of this effect, we quantified the discrepancy between our actual maps and PPMAP outputs resulting from an increased number of iterations ($N_\mathrm{iter} = 25~000$). This yielded an estimated upper limit of $\pm 1$ Kelvin for potential temperature biases stemming from these artifacts (cf. Table [1](#table:systematic-errors)). This estimate of $\pm 1$ Kelvin effectively corresponds to the maximum value of the temperature variation measured between the crest and anti-crest of the artifacts in the temperature maps.

We implemented a conservative post-processing treatment to improve the quality of the PPMAP column density and luminosity products, specifically to reduce spurious features around high-density peaks. The post-processing method is defined as follows:

1.  We first convolved the original map with a Gaussian kernel of size 1.25$^{\prime \prime}$ (equivalent to 1 pixel).

2.  Next, we flagged pixels $(i, j)$ that met two specific conditions, identifying them as potentially spurious and in need of correction: $$\begin{equation}
        \begin{split}
        &(a)~\frac{\lvert P(i, j) - P'(i, j) \lvert}{P(i, j)} \geq t , \\
        &(b)~\mathrm{B6}(i, j) \leq \sigma_\mathrm{MAD} ,
        \end{split}
        
    \end{equation}$$ where $P$ and $P'$ are respectively the PPMAP output (column density, temperature and luminosity maps) and its convolved counterpart, $\mathrm{B6}$ is the ALMA 1.3 mm map smoothed at the PPMAP’s angular resolution of 2.5$^{\prime \prime}$, $\sigma_\mathrm{MAD}$ is the median absolute deviation measured in $\mathrm{B6}$, and $t = 0.05$ is a suitable threshold.

3.  The flagged pixels were then corrected by replacing their values with the corresponding values from the convolved product ($P'(i, j)$).

The post-processing approach smoothed out artifacts selectively, ensuring that only spurious pixels were modified. Pixels associated with statistically significant signal, as measured in the ALMA B6 continuum map, remained unchanged. The result of post-processing is shown in Fig. [16](#fig:artifacts) for a small sample of hand-selected artifacts.

![](images/artifacts.pdf)

## Resampling

Finally, we resampled the PPMAP column density and luminosity products onto new grids using the (cite: Deforest2004) adaptive, anti-aliased resampling algorithm implemented through the `reproject_adaptive` routine from the `Python` package `reproject`. In this step, the sampling of the beam is increased from 2 pixels per beam to 3 pixels per beam (that is, the pixel size is lowered from 1.25$^{\prime\prime}$ to 0.83$^{\prime\prime}$). The main motivation for this increased sampling was to achieve better source detection by the *getsf* algorithm (see Sect. [5.2](#sect:GETSF)). The adaptive resampling process leads to minimal map variations, typically around 1-2% on average, and potentially a few Kelvin toward warm sources in the temperature maps. To address this limitation, we employed the `reproject_exact` routine on the PPMAP temperature maps. This approach enabled us to conserve temperatures at the positions of point-like sources, such as cores and protostars, albeit at the expense of introducing (negligible) aliasing artifacts.

# Supplementary tables and figures

![image](images/G010.pdf) ![image](images/G327.pdf) ![image](images/G328.pdf)

![image](images/G333.pdf) ![image](images/G337.pdf) ![image](images/G338.pdf)

![image](images/G351.pdf) ![image](images/G353.pdf) ![image](images/MM2.pdf)

![image](images/MM3.pdf) ![image](images/W51E.pdf) ![image](images/W51IRS.pdf)

![](images/chi2-mosaic-cnt.pdf)

|  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Region | ID | R.A. (J2000) | Dec. (J2000) | a | b | PA | FWHM | $L_{\rm bol}$ | $M$ | $L / M$ |  |  |
|  |  | \[deg\] | \[deg\] | \["\] | \["\] | \[$\deg$\] | \[au\] | \[$\times 10^2 L_\odot$\] | \[$M_\odot$\] | \[$L_\odot / M_\odot$\] |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| Region | ID | R.A. (J2000) | Dec. (J2000) | a | b | PA | FWHM | $L_{\rm bol}$ | $M$ | $L / M$ |  |  |
|  |  | \[deg\] | \[deg\] | \["\] | \["\] | \[$\deg$\] | \[au\] | \[$\times 10^2 L_\odot$\] | \[$M_\odot$\] | \[$L_\odot / M_\odot$\] |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G008.67 | 1 | 271.57936 | -21.62552 | 3.6 | 3.4 | 122 | 11800 | $57\pm18$ | $290\pm80$ | 19 |  |  |
|  |  2 |  271.59800 | -21.61969 |  3.6 |  3.3 |  91 |  11700 |  $19\pm6$ |  $93\pm26$ |  $20$ |  |  |
|  |  3 |  271.57747 | -21.62720 |  3.4 |  3.0 |  268 |  10900 |  $7.0\pm3.2$ |  $16\pm6$ |  $43$ |  |  |
|  |  4 |  271.57764 | -21.62601 |  3.8 |  3.5 |  161 |  12400 |  $6.3\pm2.5$ |  $18\pm7$ |  $35$ |  |  |
|  |  5 |  271.57863 | -21.62740 |  3.7 |  3.4 |  191 |  12100 |  $7.4\pm2.9$ |  $17\pm6$ |  $44$ |  |  |
|  |  6 |  271.58083 | -21.62373 |  3.2 |  2.8 |  148 |  10000 |  $2.4\pm1.2$ |  $4.3\pm2.5$ |  $57$ |  |  |
|  |  7 |  271.57859 | -21.62235 |  3.4 |  3.1 |  103 |  11000 |  $1.8\pm0.9$ |  $26\pm9$ |  $7$ |  |  |
|  |  8 |  271.58070 | -21.62593 |  4.3 |  3.8 |  267 |  13800 |  $5.3\pm2.2$ |  $3.9\pm2.7$ |  $135$ |  |  |
|  |  9 |  271.57909 | -21.62431 |  3.9 |  3.6 |  169 |  12600 |  $4.6\pm2.1$ |  $8.6\pm3.8$ |  $54$ |  |  |
|  |  10 |  271.58021 | -21.62159 |  3.5 |  3.3 |  187 |  11600 |  $0.91\pm0.49$ |  $35\pm11$ |  $3$ |  |  |
|  |  11 |  271.57608 | -21.62612 |  5.8 |  5.2 |  214 |  18700 |  $3.4\pm1.6$ |  $4.3\pm2.4$ |  $80$ |  |  |
|  |  12 |  271.60393 | -21.61498 |  3.2 |  3.1 |  120 |  10700 |  $0.05\pm0.036$ |  $-$ |  $-$ |  |  |
|  |  13 |  271.58752 | -21.62746 |  7.8 |  7.2 |  154 |  25600 |  $0.51\pm0.27$ |  $-$ |  $-$ |  |  |
|  |  14 |  271.57511 | -21.62466 |  5.8 |  5.3 |  212 |  18800 |  $1.3\pm0.7$ |  $4.6\pm2.8$ |  $28$ |  |  |
|  |  15 |  271.59912 | -21.61760 |  8.1 |  6.2 |  133 |  24100 |  $2.3\pm1.0$ |  $5.0\pm2.3$ |  $45$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G010.62 |  1 |  272.61945 | -19.93045 |  4.2 |  3.3 |  197 |  18500 |  $510\pm160$ |  $1400\pm400$ |  $38$ |  |  |
|  |  2 |  272.62108 | -19.92943 |  5.3 |  4.5 |  251 |  24400 |  $84\pm30$ |  $230\pm80$ |  $36$ |  |  |
|  |  3 |  272.63033 | -19.92245 |  3.2 |  3.1 |  181 |  15500 |  $3.0\pm1.0$ |  $16\pm5$ |  $19$ |  |  |
|  |  4 |  272.61438 | -19.92906 |  3.8 |  3.1 |  145 |  17100 |  $31\pm14$ |  $40\pm20$ |  $78$ |  |  |
|  |  5 |  272.62184 | -19.92800 |  3.0 |  2.7 |  135 |  14200 |  $21\pm10$ |  $20\pm9$ |  $104$ |  |  |
|  |  6 |  272.61766 | -19.92881 |  5.1 |  4.3 |  231 |  23200 |  $40\pm16$ |  $35\pm16$ |  $114$ |  |  |
|  |  7 |  272.62221 | -19.93008 |  3.8 |  2.9 |  129 |  16200 |  $19\pm10$ |  $50\pm25$ |  $38$ |  |  |
|  |  8 |  272.61881 | -19.92860 |  4.3 |  3.9 |  262 |  20400 |  $27\pm11$ |  $51\pm24$ |  $52$ |  |  |
|  |  9 |  272.61618 | -19.92835 |  3.6 |  3.4 |  264 |  17300 |  $10\pm6$ |  $19\pm9$ |  $53$ |  |  |
|  |  10 |  272.62336 | -19.92738 |  3.4 |  3.0 |  141 |  15900 |  $5.6\pm3.5$ |  $18\pm10$ |  $31$ |  |  |
|  |  11 |  272.61598 | -19.92422 |  3.9 |  3.3 |  91 |  17700 |  $4.4\pm2.5$ |  $19\pm9$ |  $24$ |  |  |
|  |  12 |  272.61466 | -19.92391 |  3.8 |  3.4 |  262 |  17800 |  $3.2\pm1.7$ |  $14\pm6$ |  $23$ |  |  |
|  |  13 |  272.61224 | -19.93089 |  4.2 |  4.1 |  112 |  20500 |  $2.8\pm2.1$ |  $15\pm8$ |  $18$ |  |  |
|  |  14 |  272.61061 | -19.92242 |  6.6 |  6.2 |  130 |  31600 |  $2.2\pm1.1$ |  $-$ |  $-$ |  |  |
|  |  15 |  272.62533 | -19.92456 |  7.3 |  7.2 |  113 |  35900 |  $2.7\pm1.6$ |  $-$ |  $-$ |  |  |
|  |  16 |  272.61686 | -19.93107 |  4.4 |  4.1 |  173 |  21000 |  $5.4\pm3.5$ |  $-$ |  $-$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G012.80 |  1 |  273.54810 | -17.94589 |  2.9 |  2.9 |  177 |  7000 |  $1.5\pm0.5$ |  $58\pm16$ |  $3$ |  |  |
|  |  2 |  273.54911 | -17.92584 |  3.5 |  2.6 |  151 |  7200 |  $11\pm4$ |  $130\pm40$ |  $9$ |  |  |
|  |  3 |  273.55758 | -17.92923 |  3.6 |  3.0 |  198 |  7900 |  $23\pm8$ |  $9.8\pm2.9$ |  $238$ |  |  |
|  |  4 |  273.54443 | -17.93760 |  3.1 |  2.9 |  157 |  7100 |  $2.3\pm0.8$ |  $49\pm15$ |  $5$ |  |  |
|  |  5 |  273.55730 | -17.92260 |  3.1 |  2.9 |  133 |  7200 |  $12\pm5$ |  $9.4\pm2.8$ |  $132$ |  |  |
|  |  6 |  273.55471 | -17.92792 |  3.5 |  3.2 |  158 |  8000 |  $17\pm6$ |  $16\pm5$ |  $107$ |  |  |
|  |  7 |  273.54029 | -17.93335 |  4.4 |  3.4 |  135 |  9300 |  $2.2\pm0.8$ |  $35\pm11$ |  $6$ |  |  |
|  |  8 |  273.55588 | -17.92888 |  5.7 |  5.2 |  178 |  13000 |  $35\pm12$ |  $66\pm20$ |  $53$ |  |  |
|  |  9 |  273.55945 | -17.92030 |  4.3 |  3.6 |  227 |  9400 |  $14\pm5$ |  $14\pm4$ |  $101$ |  |  |
|  |  10 |  273.55649 | -17.92732 |  4.7 |  4.2 |  200 |  10700 |  $24\pm8$ |  $20\pm6$ |  $118$ |  |  |
|  |  11 |  273.54202 | -17.93270 |  3.3 |  2.7 |  142 |  7200 |  $1.9\pm0.7$ |  $14\pm4$ |  $14$ |  |  |
|  |  12 |  273.55608 | -17.92121 |  3.1 |  3.0 |  157 |  7400 |  $4.9\pm2.0$ |  $6.1\pm1.9$ |  $80$ |  |  |
|  |  13 |  273.55904 | -17.92773 |  4.5 |  3.7 |  163 |  9800 |  $13\pm5$ |  $17\pm5$ |  $78$ |  |  |
|  |  14 |  273.54445 | -17.93027 |  2.9 |  2.9 |  214 |  7000 |  $1.7\pm0.8$ |  $38\pm12$ |  $5$ |  |  |
|  |  15 |  273.54846 | -17.94137 |  2.8 |  2.7 |  98 |  6700 |  $0.3\pm0.12$ |  $51\pm17$ |  $1$ |  |  |
|  |  16 |  273.55260 | -17.92854 |  2.6 |  2.4 |  96 |  6000 |  $3.6\pm1.7$ |  $6.1\pm2.5$ |  $59$ |  |  |
|  |  17 |  273.55576 | -17.91500 |  2.9 |  2.7 |  257 |  6700 |  $0.85\pm0.45$ |  $29\pm10$ |  $3$ |  |  |
|  |  18 |  273.55321 | -17.92079 |  3.7 |  3.2 |  150 |  8300 |  $3.9\pm1.7$ |  $25\pm9$ |  $16$ |  |  |
|  |  19 |  273.54587 | -17.92861 |  3.7 |  3.4 |  132 |  8400 |  $3.2\pm1.3$ |  $6.1\pm2.0$ |  $52$ |  |  |
|  |  20 |  273.55819 | -17.92102 |  5.5 |  4.3 |  186 |  11700 |  $16\pm6$ |  $30\pm9$ |  $52$ |  |  |
|  |  21 |  273.55803 | -17.92537 |  3.3 |  2.7 |  151 |  7100 |  $4.3\pm2.0$ |  $2.5\pm0.8$ |  $172$ |  |  |
|  |  22 |  273.55430 | -17.92900 |  3.2 |  2.7 |  267 |  7100 |  $5.4\pm2.4$ |  $2.2\pm0.7$ |  $241$ |  |  |
|  |  23 |  273.54692 | -17.93332 |  2.9 |  2.5 |  98 |  6500 |  $1.0\pm0.5$ |  $4.5\pm1.5$ |  $22$ |  |  |
|  |  24 |  273.55345 | -17.92807 |  3.6 |  3.3 |  97 |  8200 |  $6.2\pm2.6$ |  $13\pm5$ |  $46$ |  |  |
|  |  25 |  273.55539 | -17.93039 |  2.9 |  2.2 |  162 |  6100 |  $2.7\pm1.5$ |  $12\pm4$ |  $22$ |  |  |
|  |  26 |  273.54636 | -17.94211 |  3.1 |  2.8 |  261 |  7200 |  $0.44\pm0.22$ |  $9.4\pm3.3$ |  $5$ |  |  |
|  |  27 |  273.55770 | -17.93085 |  3.6 |  2.1 |  122 |  6600 |  $3.9\pm1.9$ |  $1.9\pm0.6$ |  $199$ |  |  |
|  |  28 |  273.56135 | -17.91893 |  4.6 |  4.0 |  124 |  10300 |  $4.2\pm2.0$ |  $6.2\pm2.4$ |  $67$ |  |  |
|  |  29 |  273.55955 | -17.91854 |  4.7 |  4.3 |  224 |  10800 |  $4.8\pm2.3$ |  $5.2\pm2.1$ |  $91$ |  |  |
|  |  30 |  273.55855 | -17.92298 |  3.4 |  2.7 |  137 |  7300 |  $2.5\pm1.3$ |  $0.37\pm0.28$ |  $686$ |  |  |
|  |  31 |  273.55800 | -17.93279 |  4.4 |  3.5 |  209 |  9500 |  $5.7\pm2.7$ |  $-$ |  $-$ |  |  |
|  |  32 |  273.55746 | -17.92807 |  3.8 |  2.5 |  157 |  7300 |  $6.7\pm2.8$ |  $2.6\pm1.0$ |  $256$ |  |  |
|  |  33 |  273.55154 | -17.91897 |  3.3 |  3.0 |  203 |  7600 |  $1.1\pm0.7$ |  $11\pm5$ |  $10$ |  |  |
|  |  34 |  273.55795 | -17.92680 |  3.2 |  2.4 |  264 |  6700 |  $2.2\pm1.3$ |  $-$ |  $-$ |  |  |
|  |  35 |  273.55965 | -17.92194 |  4.3 |  3.2 |  130 |  8900 |  $4.0\pm1.8$ |  $2.0\pm0.8$ |  $197$ |  |  |
|  |  36 |  273.55892 | -17.92437 |  3.2 |  2.9 |  155 |  7400 |  $2.5\pm1.3$ |  $6.7\pm2.3$ |  $37$ |  |  |
|  |  37 |  273.56901 | -17.92472 |  3.3 |  2.5 |  181 |  6900 |  $0.74\pm0.46$ |  $12\pm4$ |  $6$ |  |  |
|  |  38 |  273.56626 | -17.92312 |  3.9 |  3.0 |  132 |  8200 |  $1.5\pm0.9$ |  $3.1\pm1.1$ |  $48$ |  |  |
|  |  39 |  273.56889 | -17.93894 |  2.6 |  2.4 |  249 |  6000 |  $0.2\pm0.11$ |  $5.4\pm2.3$ |  $4$ |  |  |
|  |  40 |  273.55130 | -17.92198 |  3.4 |  3.0 |  118 |  7700 |  $1.6\pm0.8$ |  $0.9\pm0.78$ |  $174$ |  |  |
|  |  41 |  273.55924 | -17.93100 |  3.2 |  2.3 |  94 |  6400 |  $1.9\pm1.2$ |  $8.9\pm3.3$ |  $22$ |  |  |
|  |  42 |  273.55681 | -17.92399 |  3.7 |  2.4 |  108 |  7100 |  $2.8\pm1.6$ |  $5.8\pm2.1$ |  $48$ |  |  |
|  |  43 |  273.56054 | -17.93069 |  3.4 |  2.5 |  244 |  7000 |  $2.0\pm1.2$ |  $0.6\pm0.305$ |  $340$ |  |  |
|  |  44 |  273.56779 | -17.92055 |  3.1 |  2.9 |  205 |  7200 |  $0.48\pm0.34$ |  $6.9\pm2.3$ |  $7$ |  |  |
|  |  45 |  273.56181 | -17.92985 |  5.9 |  3.2 |  223 |  10400 |  $6.0\pm2.7$ |  $4.0\pm2.0$ |  $151$ |  |  |
|  |  46 |  273.55787 | -17.91982 |  3.4 |  3.1 |  269 |  7700 |  $2.3\pm1.4$ |  $2.8\pm1.6$ |  $83$ |  |  |
|  |  47 |  273.54652 | -17.92761 |  3.6 |  2.6 |  114 |  7400 |  $2.0\pm1.2$ |  $2.1\pm1.1$ |  $98$ |  |  |
|  |  48 |  273.54652 | -17.94346 |  3.2 |  3.0 |  187 |  7500 |  $0.29\pm0.16$ |  $-$ |  $-$ |  |  |
|  |  49 |  273.55308 | -17.92958 |  3.6 |  3.2 |  172 |  8200 |  $2.9\pm1.4$ |  $-$ |  $-$ |  |  |
|  |  50 |  273.54786 | -17.92726 |  4.0 |  3.4 |  250 |  8900 |  $2.0\pm1.0$ |  $-$ |  $-$ |  |  |
|  |  51 |  273.55673 | -17.93027 |  3.3 |  2.0 |  204 |  6300 |  $2.5\pm1.8$ |  $2.3\pm1.1$ |  $106$ |  |  |
|  |  52 |  273.55163 | -17.92923 |  3.9 |  3.8 |  251 |  9200 |  $3.1\pm1.5$ |  $-$ |  $-$ |  |  |
|  |  53 |  273.55422 | -17.91427 |  2.8 |  2.7 |  188 |  6600 |  $0.2\pm0.15$ |  $-$ |  $-$ |  |  |
|  |  54 |  273.56111 | -17.92032 |  3.8 |  3.2 |  178 |  8300 |  $1.7\pm1.1$ |  $36\pm11$ |  $5$ |  |  |
|  |  55 |  273.56095 | -17.93370 |  4.0 |  2.9 |  161 |  8200 |  $1.5\pm0.9$ |  $-$ |  $-$ |  |  |
|  |  56 |  273.55612 | -17.93490 |  3.0 |  2.4 |  117 |  6400 |  $0.78\pm0.63$ |  $9.0\pm3.4$ |  $9$ |  |  |
|  |  57 |  273.55029 | -17.92298 |  3.4 |  2.9 |  96 |  7500 |  $1.0\pm0.7$ |  $0.71\pm0.32$ |  $148$ |  |  |
|  |  58 |  273.55989 | -17.93224 |  4.8 |  2.7 |  188 |  8600 |  $2.2\pm1.1$ |  $6.4\pm1.9$ |  $34$ |  |  |
|  |  59 |  273.55454 | -17.92668 |  4.0 |  2.5 |  170 |  7500 |  $3.5\pm2.0$ |  $-$ |  $-$ |  |  |
|  |  60 |  273.56054 | -17.92422 |  3.3 |  3.1 |  118 |  7700 |  $1.1\pm0.7$ |  $-$ |  $-$ |  |  |
|  |  61 |  273.55941 | -17.93339 |  4.0 |  3.2 |  190 |  8500 |  $1.5\pm1.0$ |  $0.31\pm0.19$ |  $471$ |  |  |
|  |  62 |  273.55527 | -17.94288 |  6.2 |  5.8 |  202 |  14400 |  $0.47\pm0.2$ |  $8.1\pm2.5$ |  $6$ |  |  |
|  |  63 |  273.55308 | -17.92668 |  4.5 |  3.5 |  210 |  9400 |  $1.6\pm1.0$ |  $-$ |  $-$ |  |  |
|  |  64 |  273.56196 | -17.93201 |  4.0 |  3.0 |  134 |  8400 |  $0.84\pm0.48$ |  $0.65\pm0.45$ |  $129$ |  |  |
|  |  65 |  273.57144 | -17.92506 |  2.8 |  2.2 |  176 |  6000 |  $0.13\pm0.11$ |  $-$ |  $-$ |  |  |
|  |  66 |  273.54441 | -17.93925 |  3.6 |  2.1 |  270 |  6600 |  $0.1\pm0.055$ |  $-$ |  $-$ |  |  |
|  |  67 |  273.56135 | -17.92576 |  3.9 |  2.9 |  170 |  8100 |  $0.84\pm0.65$ |  $-$ |  $-$ |  |  |
|  |  68 |  273.54644 | -17.93717 |  3.7 |  3.4 |  216 |  8500 |  $0.19\pm0.14$ |  $-$ |  $-$ |  |  |
|  |  69 |  273.55539 | -17.92310 |  4.9 |  4.5 |  235 |  11300 |  $1.5\pm0.9$ |  $-$ |  $-$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G327.29 |  1 |  238.28229 | -54.61835 |  3.9 |  3.5 |  181 |  9100 |  $53\pm17$ |  $3000\pm800$ |  $2$ |  |  |
|  |  2 |  238.29827 | -54.60690 |  3.6 |  3.1 |  100 |  8400 |  $3.9\pm1.3$ |  $110\pm30$ |  $4$ |  |  |
|  |  3 |  238.29572 | -54.61299 |  4.4 |  3.7 |  246 |  10200 |  $6.2\pm2.2$ |  $26\pm8$ |  $24$ |  |  |
|  |  4 |  238.28569 | -54.61731 |  4.0 |  3.5 |  154 |  9300 |  $14\pm5$ |  $89\pm27$ |  $15$ |  |  |
|  |  5 |  238.29401 | -54.61111 |  3.3 |  2.9 |  117 |  7700 |  $2.1\pm0.8$ |  $19\pm7$ |  $11$ |  |  |
|  |  6 |  238.29707 | -54.60968 |  3.2 |  2.9 |  184 |  7600 |  $1.9\pm0.7$ |  $14\pm5$ |  $13$ |  |  |
|  |  7 |  238.28958 | -54.61673 |  3.7 |  3.3 |  239 |  8700 |  $6.0\pm2.5$ |  $45\pm17$ |  $13$ |  |  |
|  |  8 |  238.29747 | -54.60852 |  4.3 |  3.8 |  152 |  10000 |  $1.6\pm0.6$ |  $35\pm12$ |  $5$ |  |  |
|  |  9 |  238.28689 | -54.61662 |  3.3 |  3.2 |  183 |  8100 |  $4.2\pm2.0$ |  $11\pm4$ |  $37$ |  |  |
|  |  10 |  238.28655 | -54.61874 |  5.1 |  4.7 |  166 |  12200 |  $7.4\pm3.4$ |  $4.1\pm2.05$ |  $181$ |  |  |
|  |  11 |  238.29468 | -54.60898 |  3.9 |  3.2 |  184 |  8900 |  $0.64\pm0.3$ |  $11\pm6$ |  $6$ |  |  |
|  |  12 |  238.28654 | -54.62925 |  7.0 |  6.6 |  129 |  17000 |  $1.2\pm0.4$ |  $3.5\pm1.9$ |  $34$ |  |  |
|  |  13 |  238.28928 | -54.61431 |  3.4 |  3.1 |  120 |  8200 |  $1.2\pm0.6$ |  $-$ |  $-$ |  |  |
|  |  14 |  238.26052 | -54.62333 |  4.3 |  3.6 |  202 |  9800 |  $0.4\pm0.25$ |  $-$ |  $-$ |  |  |
|  |  15 |  238.27936 | -54.61959 |  6.0 |  5.3 |  141 |  14100 |  $3.6\pm1.8$ |  $6.0\pm3.3$ |  $60$ |  |  |
|  |  16 |  238.29328 | -54.61431 |  3.4 |  2.8 |  134 |  7800 |  $0.37\pm0.26$ |  $5.6\pm3.0$ |  $7$ |  |  |
|  |  17 |  238.29648 | -54.61512 |  2.8 |  2.7 |  218 |  6900 |  $0.24\pm0.18$ |  $14\pm6$ |  $2$ |  |  |
|  |  18 |  238.28869 | -54.61882 |  3.4 |  2.2 |  259 |  6800 |  $0.96\pm0.78$ |  $-$ |  $-$ |  |  |
|  |  19 |  238.29048 | -54.61246 |  2.9 |  2.8 |  250 |  7100 |  $0.14\pm0.08$ |  $1.1\pm0.9$ |  $13$ |  |  |
|  |  20 |  238.28449 | -54.62009 |  6.0 |  5.3 |  234 |  14100 |  $4.0\pm2.2$ |  $21\pm9$ |  $19$ |  |  |
|  |  21 |  238.30627 | -54.62853 |  6.7 |  6.2 |  109 |  16100 |  $0.19\pm0.09$ |  $-$ |  $-$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G328.25 |  1 |  239.49932 | -53.96696 |  3.6 |  3.4 |  227 |  8800 |  $36\pm12$ |  $70\pm22$ |  $51$ |  |  |
|  |  2 |  239.49716 | -53.96535 |  7.5 |  6.6 |  226 |  17600 |  $7.8\pm3.6$ |  $20\pm8$ |  $39$ |  |  |
|  |  3 |  239.47619 | -53.96021 |  3.2 |  3.1 |  187 |  7800 |  $0.02\pm0.016$ |  $-$ |  $-$ |  |  |
|  |  4 |  239.50168 | -53.95446 |  4.2 |  3.7 |  181 |  10000 |  $0.19\pm0.11$ |  $0.13\pm0.085$ |  $146$ |  |  |
|  |  5 |  239.47868 | -53.96418 |  3.1 |  3.0 |  182 |  7600 |  $0.02\pm0.016$ |  $-$ |  $-$ |  |  |
|  |  6 |  239.51355 | -53.96584 |  3.7 |  3.5 |  206 |  9000 |  $0.06\pm0.039$ |  $-$ |  $-$ |  |  |
|  |  7 |  239.51466 | -53.96846 |  4.8 |  4.4 |  158 |  11400 |  $0.09\pm0.058$ |  $0.19\pm0.12$ |  $47$ |  |  |
|  |  8 |  239.50817 | -53.97639 |  9.4 |  8.8 |  191 |  22800 |  $0.1\pm0.05$ |  $0.49\pm0.21$ |  $20$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G333.60 |  1 |  245.53714 | -50.09831 |  3.3 |  2.9 |  241 |  13100 |  $62\pm22$ |  $230\pm70$ |  $27$ |  |  |
|  |  2 |  245.53558 | -50.10088 |  3.7 |  3.2 |  174 |  14400 |  $79\pm28$ |  $49\pm14$ |  $159$ |  |  |
|  |  3 |  245.54297 | -50.09978 |  3.2 |  2.7 |  117 |  12500 |  $65\pm23$ |  $120\pm40$ |  $55$ |  |  |
|  |  4 |  245.54669 | -50.09876 |  3.8 |  2.9 |  159 |  13900 |  $86\pm31$ |  $87\pm28$ |  $98$ |  |  |
|  |  5 |  245.51740 | -50.10861 |  3.9 |  3.4 |  177 |  15100 |  $9.1\pm3.5$ |  $66\pm24$ |  $14$ |  |  |
|  |  6 |  245.54015 | -50.10610 |  3.9 |  3.2 |  182 |  14800 |  $36\pm14$ |  $12\pm6$ |  $309$ |  |  |
|  |  7 |  245.52829 | -50.10496 |  3.3 |  2.5 |  123 |  12000 |  $21\pm9$ |  $25\pm9$ |  $83$ |  |  |
|  |  8 |  245.53864 | -50.10255 |  3.0 |  2.7 |  133 |  11900 |  $28\pm14$ |  $50\pm19$ |  $57$ |  |  |
|  |  9 |  245.53702 | -50.09735 |  3.1 |  2.6 |  171 |  12100 |  $24\pm10$ |  $57\pm22$ |  $42$ |  |  |
|  |  10 |  245.53594 | -50.10325 |  4.3 |  2.9 |  146 |  15000 |  $32\pm14$ |  $18\pm8$ |  $181$ |  |  |
|  |  11 |  245.54261 | -50.10602 |  4.1 |  3.9 |  162 |  16700 |  $34\pm13$ |  $22\pm7$ |  $153$ |  |  |
|  |  12 |  245.54219 | -50.10155 |  3.7 |  3.3 |  217 |  14700 |  $39\pm16$ |  $43\pm18$ |  $91$ |  |  |
|  |  13 |  245.53594 | -50.09978 |  2.7 |  2.4 |  184 |  10500 |  $16\pm8$ |  $3.4\pm1.8$ |  $478$ |  |  |
|  |  14 |  245.52246 | -50.10041 |  5.9 |  4.7 |  167 |  22100 |  $28\pm10$ |  $2.8\pm1.1$ |  $972$ |  |  |
|  |  15 |  245.54459 | -50.10278 |  3.4 |  3.3 |  111 |  14100 |  $24\pm11$ |  $-$ |  $-$ |  |  |
|  |  16 |  245.54517 | -50.10121 |  5.2 |  3.6 |  106 |  18200 |  $67\pm26$ |  $2.9\pm2.2$ |  $2287$ |  |  |
|  |  17 |  245.54880 | -50.09577 |  4.0 |  3.0 |  100 |  14500 |  $17\pm8$ |  $5.1\pm2.1$ |  $339$ |  |  |
|  |  18 |  245.54820 | -50.09931 |  4.0 |  3.6 |  158 |  16000 |  $34\pm16$ |  $2.4\pm1.5$ |  $1412$ |  |  |
|  |  19 |  245.53858 | -50.10456 |  3.7 |  2.8 |  161 |  13500 |  $20\pm10$ |  $2.5\pm1.5$ |  $802$ |  |  |
|  |  20 |  245.50925 | -50.10816 |  2.8 |  2.6 |  182 |  11300 |  $0.86\pm0.57$ |  $-$ |  $-$ |  |  |
|  |  21 |  245.54784 | -50.09735 |  4.0 |  3.5 |  137 |  15700 |  $16\pm8$ |  $17\pm7$ |  $96$ |  |  |
|  |  22 |  245.53269 | -50.09897 |  2.8 |  2.6 |  262 |  11400 |  $9.4\pm5.9$ |  $2.9\pm1.5$ |  $319$ |  |  |
|  |  23 |  245.53305 | -50.08606 |  7.0 |  6.5 |  132 |  28100 |  $10\pm4$ |  $-$ |  $-$ |  |  |
|  |  24 |  245.53798 | -50.10610 |  3.9 |  3.0 |  194 |  14200 |  $17\pm9$ |  $7.8\pm4.6$ |  $217$ |  |  |
|  |  25 |  245.51574 | -50.10926 |  3.4 |  3.1 |  246 |  13700 |  $1.9\pm1.0$ |  $3.0\pm1.3$ |  $64$ |  |  |
|  |  26 |  245.54946 | -50.09850 |  3.3 |  2.9 |  239 |  12900 |  $14\pm8$ |  $11\pm7$ |  $129$ |  |  |
|  |  27 |  245.54739 | -50.10354 |  4.9 |  3.8 |  163 |  18000 |  $23\pm10$ |  $27\pm10$ |  $82$ |  |  |
|  |  28 |  245.54189 | -50.09770 |  3.5 |  2.7 |  150 |  12900 |  $18\pm9$ |  $-$ |  $-$ |  |  |
|  |  29 |  245.51844 | -50.10706 |  3.6 |  3.3 |  144 |  14400 |  $2.1\pm1.2$ |  $-$ |  $-$ |  |  |
|  |  30 |  245.53540 | -50.10487 |  4.2 |  2.9 |  97 |  14600 |  $16\pm8$ |  $-$ |  $-$ |  |  |
|  |  31 |  245.54279 | -50.09862 |  3.3 |  2.9 |  200 |  13000 |  $20\pm10$ |  $1.3\pm0.75$ |  $1535$ |  |  |
|  |  32 |  245.52824 | -50.10679 |  3.5 |  3.4 |  144 |  14500 |  $5.0\pm2.8$ |  $-$ |  $-$ |  |  |
|  |  33 |  245.53926 | -50.09797 |  4.8 |  3.2 |  180 |  16400 |  $23\pm11$ |  $-$ |  $-$ |  |  |
|  |  34 |  245.54730 | -50.09596 |  3.5 |  3.1 |  264 |  13900 |  $7.5\pm4.4$ |  $-$ |  $-$ |  |  |
|  |  35 |  245.55613 | -50.10157 |  3.9 |  3.2 |  195 |  14800 |  $1.5\pm1.0$ |  $-$ |  $-$ |  |  |
|  |  36 |  245.54459 | -50.09689 |  3.0 |  2.2 |  254 |  10900 |  $3.8\pm3.4$ |  $-$ |  $-$ |  |  |
|  |  37 |  245.53305 | -50.10163 |  4.7 |  2.9 |  147 |  15600 |  $6.8\pm5.4$ |  $22\pm10$ |  $31$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G337.92 |  1 |  250.29351 | -47.13402 |  3.9 |  3.3 |  157 |  13000 |  $84\pm27$ |  $450\pm120$ |  $19$ |  |  |
|  |  2 |  250.29300 | -47.13530 |  5.6 |  4.6 |  202 |  18200 |  $51\pm17$ |  $84\pm25$ |  $61$ |  |  |
|  |  3 |  250.29538 | -47.13472 |  4.5 |  3.4 |  93 |  14000 |  $30\pm11$ |  $49\pm15$ |  $62$ |  |  |
|  |  4 |  250.29294 | -47.13260 |  4.9 |  4.8 |  174 |  17500 |  $9.1\pm3.5$ |  $2.7\pm1.0$ |  $337$ |  |  |
|  |  5 |  250.29306 | -47.13167 |  3.2 |  2.3 |  186 |  9800 |  $2.4\pm1.4$ |  $5.4\pm2.6$ |  $44$ |  |  |
|  |  6 |  250.29215 | -47.14143 |  2.8 |  2.7 |  197 |  9900 |  $0.45\pm0.31$ |  $10\pm4$ |  $4$ |  |  |
|  |  7 |  250.28382 | -47.13414 |  3.6 |  3.0 |  186 |  11900 |  $1.0\pm0.6$ |  $2.5\pm1.2$ |  $41$ |  |  |
|  |  8 |  250.29317 | -47.13761 |  4.5 |  3.2 |  101 |  13600 |  $1.9\pm1.4$ |  $6.0\pm3.1$ |  $31$ |  |  |
|  |  9 |  250.29147 | -47.13935 |  4.0 |  3.1 |  124 |  12700 |  $0.97\pm0.62$ |  $2.7\pm1.3$ |  $36$ |  |  |
|  |  10 |  250.27940 | -47.13240 |  3.4 |  3.2 |  120 |  11900 |  $0.67\pm0.4$ |  $3.9\pm2.3$ |  $17$ |  |  |
|  |  11 |  250.29090 | -47.13422 |  4.9 |  3.7 |  113 |  15300 |  $5.4\pm2.3$ |  $5.1\pm2.3$ |  $106$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G338.93 |  1 |  250.14187 | -45.70220 |  3.7 |  3.2 |  260 |  13500 |  $67\pm22$ |  $150\pm50$ |  $43$ |  |  |
|  |  2 |  250.14283 | -45.69357 |  3.1 |  2.8 |  125 |  11400 |  $21\pm7$ |  $59\pm18$ |  $35$ |  |  |
|  |  3 |  250.14023 | -45.70278 |  4.2 |  3.5 |  235 |  14900 |  $40\pm13$ |  $44\pm17$ |  $90$ |  |  |
|  |  4 |  250.13985 | -45.69357 |  3.7 |  3.5 |  227 |  14100 |  $16\pm5$ |  $47\pm15$ |  $33$ |  |  |
|  |  5 |  250.13786 | -45.70398 |  3.4 |  3.2 |  147 |  12900 |  $11\pm4$ |  $730\pm200$ |  $1$ |  |  |
|  |  6 |  250.13862 | -45.69431 |  6.3 |  5.5 |  92 |  23100 |  $66\pm22$ |  $14\pm8$ |  $454$ |  |  |
|  |  7 |  250.14090 | -45.69538 |  5.2 |  4.9 |  268 |  19700 |  $8.5\pm3.0$ |  $40\pm13$ |  $21$ |  |  |
|  |  8 |  250.14001 | -45.70109 |  6.0 |  5.2 |  167 |  21800 |  $14\pm5$ |  $64\pm22$ |  $23$ |  |  |
|  |  9 |  250.14978 | -45.69288 |  3.4 |  3.3 |  227 |  13000 |  $0.97\pm0.44$ |  $0.53\pm0.32$ |  $183$ |  |  |
|  |  10 |  250.15127 | -45.69511 |  5.6 |  3.8 |  140 |  17800 |  $0.75\pm0.42$ |  $1.9\pm1.3$ |  $40$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G351.77 |  1 |  261.67792 | -36.15512 |  7.3 |  5.1 |  191 |  12200 |  $53\pm17$ |  $520\pm140$ |  $10$ |  |  |
|  |  2 |  261.68196 | -36.15440 |  4.6 |  4.3 |  269 |  8900 |  $4.1\pm2.0$ |  $8.0\pm3.3$ |  $51$ |  |  |
|  |  3 |  261.67845 | -36.14318 |  3.7 |  3.3 |  103 |  7000 |  $0.07\pm0.042$ |  $-$ |  $-$ |  |  |
|  |  4 |  261.68031 | -36.15440 |  4.7 |  4.1 |  203 |  8800 |  $1.9\pm1.0$ |  $1.8\pm1.1$ |  $107$ |  |  |
|  |  5 |  261.67530 | -36.15868 |  4.4 |  4.0 |  260 |  8400 |  $1.2\pm0.8$ |  $1.5\pm0.8$ |  $76$ |  |  |
|  |  6 |  261.67859 | -36.15370 |  4.2 |  3.8 |  194 |  8000 |  $2.7\pm1.4$ |  $19\pm7$ |  $14$ |  |  |
|  |  7 |  261.68117 | -36.15289 |  5.2 |  4.5 |  90 |  9600 |  $2.2\pm1.3$ |  $2.4\pm1.7$ |  $95$ |  |  |
|  |  8 |  261.66303 | -36.15918 |  3.8 |  3.3 |  179 |  7100 |  $0.04\pm0.032$ |  $-$ |  $-$ |  |  |
|  |  9 |  261.66530 | -36.14080 |  4.0 |  3.8 |  259 |  7800 |  $0.05\pm0.036$ |  $-$ |  $-$ |  |  |
|  |  10 |  261.67544 | -36.15706 |  4.1 |  3.6 |  267 |  7700 |  $0.52\pm0.5$ |  $-$ |  $-$ |  |  |
|  |  11 |  261.67783 | -36.15062 |  4.2 |  3.7 |  269 |  7900 |  $0.43\pm0.245$ |  $0.57\pm0.295$ |  $75$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| G353.41 |  1 |  262.61837 | -34.69645 |  3.3 |  2.9 |  221 |  6200 |  $3.0\pm1.0$ |  $62\pm18$ |  $5$ |  |  |
|  |  2 |  262.61023 | -34.69610 |  5.7 |  3.1 |  190 |  8500 |  $8.1\pm2.9$ |  $48\pm14$ |  $17$ |  |  |
|  |  3 |  262.61640 | -34.69553 |  3.4 |  3.1 |  187 |  6500 |  $2.0\pm0.8$ |  $43\pm13$ |  $5$ |  |  |
|  |  4 |  262.60869 | -34.69601 |  4.7 |  3.0 |  169 |  7600 |  $4.0\pm1.5$ |  $59\pm17$ |  $7$ |  |  |
|  |  5 |  262.60712 | -34.69691 |  3.9 |  3.6 |  115 |  7400 |  $1.6\pm0.7$ |  $31\pm9$ |  $5$ |  |  |
|  |  6 |  262.61411 | -34.69468 |  3.7 |  2.7 |  167 |  6300 |  $1.3\pm0.7$ |  $11\pm4$ |  $12$ |  |  |
|  |  7 |  262.60482 | -34.69341 |  3.7 |  3.3 |  160 |  7000 |  $1.3\pm0.7$ |  $20\pm7$ |  $7$ |  |  |
|  |  8 |  262.61040 | -34.69337 |  3.1 |  2.9 |  201 |  6000 |  $0.79\pm0.48$ |  $4.3\pm1.5$ |  $19$ |  |  |
|  |  9 |  262.60904 | -34.69734 |  4.0 |  2.9 |  193 |  6700 |  $0.99\pm0.61$ |  $13\pm4$ |  $7$ |  |  |
|  |  10 |  262.60792 | -34.69965 |  3.3 |  3.2 |  163 |  6500 |  $0.64\pm0.41$ |  $3.7\pm1.5$ |  $17$ |  |  |
|  |  11 |  262.60562 | -34.69637 |  4.0 |  3.8 |  181 |  7700 |  $0.85\pm0.45$ |  $-$ |  $-$ |  |  |
|  |  12 |  262.60960 | -34.69452 |  5.5 |  5.0 |  188 |  10500 |  $1.6\pm0.8$ |  $3.9\pm1.8$ |  $41$ |  |  |
|  |  13 |  262.61945 | -34.69040 |  3.7 |  3.1 |  177 |  6800 |  $0.22\pm0.12$ |  $2.2\pm1.1$ |  $10$ |  |  |
|  |  14 |  262.61101 | -34.69769 |  5.6 |  5.3 |  182 |  11000 |  $1.5\pm0.7$ |  $2.7\pm1.4$ |  $55$ |  |  |
|  |  15 |  262.61895 | -34.69213 |  8.5 |  8.0 |  157 |  16500 |  $1.0\pm0.4$ |  $-$ |  $-$ |  |  |
|  |  16 |  262.60449 | -34.69522 |  4.7 |  4.5 |  186 |  9200 |  $0.41\pm0.26$ |  $5.6\pm2.3$ |  $7$ |  |  |
|  |  17 |  262.61368 | -34.68878 |  6.5 |  5.6 |  117 |  12000 |  $0.42\pm0.22$ |  $0.42\pm0.31$ |  $100$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| W43-MM1 |  1 |  281.94584 |  -1.90731 |  3.2 |  3.1 |  222 |  17300 |  $120\pm40$ |  $2400\pm700$ |  $5$ |  |  |
|  |  2 |  281.94520 |  -1.90846 |  4.7 |  3.7 |  162 |  23000 |  $60\pm20$ |  $1300\pm400$ |  $5$ |  |  |
|  |  3 |  281.94368 |  -1.90908 |  3.6 |  3.1 |  168 |  18400 |  $20\pm7$ |  $370\pm110$ |  $6$ |  |  |
|  |  4 |  281.94387 |  -1.90650 |  4.6 |  4.0 |  211 |  23500 |  $23\pm9$ |  $250\pm80$ |  $9$ |  |  |
|  |  5 |  281.94295 |  -1.90939 |  3.2 |  3.0 |  226 |  17300 |  $9.6\pm4.0$ |  $94\pm32$ |  $10$ |  |  |
|  |  6 |  281.93666 |  -1.91247 |  3.7 |  2.9 |  139 |  17900 |  $6.4\pm2.5$ |  $50\pm19$ |  $13$ |  |  |
|  |  7 |  281.94700 |  -1.90846 |  4.2 |  3.4 |  189 |  20800 |  $6.6\pm2.8$ |  $140\pm50$ |  $5$ |  |  |
|  |  8 |  281.93851 |  -1.91093 |  3.3 |  3.0 |  134 |  17300 |  $3.4\pm1.4$ |  $54\pm20$ |  $6$ |  |  |
|  |  9 |  281.93366 |  -1.91360 |  3.2 |  3.0 |  236 |  17100 |  $1.3\pm0.5$ |  $36\pm15$ |  $4$ |  |  |
|  |  10 |  281.94653 |  -1.90303 |  3.1 |  2.9 |  153 |  16500 |  $1.8\pm1.0$ |  $25\pm10$ |  $7$ |  |  |
|  |  11 |  281.93573 |  -1.91155 |  4.3 |  4.0 |  176 |  22800 |  $3.4\pm1.4$ |  $19\pm8$ |  $18$ |  |  |
|  |  12 |  281.93164 |  -1.91556 |  3.3 |  3.1 |  159 |  17600 |  $0.65\pm0.26$ |  $28\pm14$ |  $2$ |  |  |
|  |  13 |  281.94746 |  -1.90245 |  3.1 |  2.6 |  184 |  15500 |  $1.0\pm0.6$ |  $65\pm24$ |  $2$ |  |  |
|  |  14 |  281.94576 |  -1.90368 |  3.2 |  2.4 |  112 |  15200 |  $1.6\pm1.0$ |  $9.0\pm4.9$ |  $18$ |  |  |
|  |  15 |  281.95078 |  -1.90098 |  3.0 |  2.7 |  139 |  15700 |  $0.45\pm0.24$ |  $15\pm7$ |  $3$ |  |  |
|  |  16 |  281.93484 |  -1.91170 |  3.4 |  3.0 |  97 |  17500 |  $1.5\pm0.8$ |  $3.7\pm2.2$ |  $40$ |  |  |
|  |  17 |  281.94040 |  -1.90904 |  3.8 |  3.0 |  170 |  18500 |  $1.3\pm0.7$ |  $3.1\pm1.9$ |  $41$ |  |  |
|  |  18 |  281.93936 |  -1.91031 |  2.9 |  2.6 |  260 |  15000 |  $0.98\pm0.58$ |  $14\pm6$ |  $7$ |  |  |
|  |  19 |  281.94522 |  -1.91317 |  3.7 |  3.6 |  179 |  19900 |  $0.5\pm0.36$ |  $18\pm9$ |  $3$ |  |  |
|  |  20 |  281.95070 |  -1.90245 |  2.7 |  2.6 |  109 |  14500 |  $0.14\pm0.07$ |  $1.4\pm0.85$ |  $10$ |  |  |
|  |  21 |  281.94480 |  -1.90499 |  5.0 |  3.7 |  101 |  23700 |  $1.4\pm1.0$ |  $-$ |  $-$ |  |  |
|  |  22 |  281.94677 |  -1.91263 |  5.0 |  4.3 |  164 |  25700 |  $0.88\pm0.52$ |  $-$ |  $-$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| W43-MM2 |  1 |  281.90319 |  -2.01505 |  3.2 |  3.0 |  104 |  17200 |  $82\pm26$ |  $1800\pm500$ |  $4$ |  |  |
|  |  2 |  281.91361 |  -2.00777 |  3.1 |  3.0 |  263 |  16800 |  $13\pm4$ |  $180\pm50$ |  $7$ |  |  |
|  |  3 |  281.90030 |  -2.02095 |  4.0 |  3.3 |  101 |  20000 |  $4.6\pm1.5$ |  $240\pm70$ |  $2$ |  |  |
|  |  4 |  281.90007 |  -2.02234 |  3.0 |  3.0 |  189 |  16400 |  $2.7\pm0.9$ |  $120\pm40$ |  $2$ |  |  |
|  |  5 |  281.90284 |  -2.01332 |  4.4 |  3.6 |  237 |  21800 |  $11\pm4$ |  $67\pm21$ |  $16$ |  |  |
|  |  6 |  281.90446 |  -2.01540 |  3.9 |  3.4 |  98 |  19900 |  $14\pm5$ |  $73\pm26$ |  $19$ |  |  |
|  |  7 |  281.90111 |  -2.01401 |  2.7 |  2.6 |  188 |  14700 |  $2.6\pm1.3$ |  $25\pm9$ |  $10$ |  |  |
|  |  8 |  281.90354 |  -2.01748 |  3.1 |  2.7 |  96 |  15700 |  $3.4\pm1.9$ |  $22\pm9$ |  $15$ |  |  |
|  |  9 |  281.89451 |  -2.01783 |  2.8 |  2.7 |  122 |  15100 |  $0.75\pm0.31$ |  $24\pm10$ |  $3$ |  |  |
|  |  10 |  281.89995 |  -2.01390 |  3.2 |  2.8 |  162 |  16400 |  $1.3\pm0.7$ |  $4.7\pm2.5$ |  $28$ |  |  |
|  |  11 |  281.89694 |  -2.01714 |  2.5 |  2.5 |  171 |  13700 |  $0.37\pm0.16$ |  $2.9\pm1.8$ |  $13$ |  |  |
|  |  12 |  281.89868 |  -2.00915 |  2.8 |  2.6 |  262 |  14900 |  $0.3\pm0.14$ |  $2.2\pm1.7$ |  $14$ |  |  |
|  |  13 |  281.91118 |  -2.01228 |  2.7 |  2.4 |  118 |  14000 |  $0.2\pm0.11$ |  $-$ |  $-$ |  |  |
|  |  14 |  281.89625 |  -2.01922 |  2.5 |  2.5 |  194 |  13700 |  $0.37\pm0.19$ |  $1.9\pm1.7$ |  $19$ |  |  |
|  |  15 |  281.90041 |  -2.02477 |  2.6 |  2.4 |  132 |  13800 |  $0.5\pm0.3$ |  $5.0\pm3.2$ |  $10$ |  |  |
|  |  16 |  281.90064 |  -2.01297 |  3.0 |  2.6 |  163 |  15400 |  $0.49\pm0.32$ |  $-$ |  $-$ |  |  |
|  |  17 |  281.90504 |  -2.01899 |  7.7 |  7.4 |  188 |  41500 |  $-$ |  $2.8\pm2.4$ |  $-$ |  |  |
|  |  18 |  281.90203 |  -2.01956 |  2.8 |  2.4 |  251 |  14400 |  $0.2\pm0.14$ |  $-$ |  $-$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| W43-MM3 |  1 |  281.91364 |  -2.00779 |  3.4 |  3.1 |  161 |  18000 |  $31\pm10$ |  $220\pm60$ |  $14$ |  |  |
|  |  2 |  281.92382 |  -2.00779 |  4.0 |  3.5 |  217 |  20800 |  $61\pm21$ |  $650\pm180$ |  $9$ |  |  |
|  |  3 |  281.92477 |  -2.00606 |  4.8 |  4.4 |  91 |  25500 |  $48\pm16$ |  $87\pm26$ |  $55$ |  |  |
|  |  4 |  281.92068 |  -2.00581 |  3.0 |  3.0 |  174 |  16300 |  $13\pm5$ |  $230\pm70$ |  $6$ |  |  |
|  |  5 |  281.92519 |  -2.00749 |  3.4 |  3.3 |  123 |  18400 |  $19\pm7$ |  $200\pm60$ |  $10$ |  |  |
|  |  6 |  281.92338 |  -2.00675 |  4.2 |  3.8 |  199 |  22000 |  $29\pm10$ |  $70\pm23$ |  $41$ |  |  |
|  |  7 |  281.91454 |  -2.00911 |  4.5 |  4.0 |  244 |  23400 |  $3.9\pm1.3$ |  $16\pm5$ |  $24$ |  |  |
|  |  8 |  281.92380 |  -2.00575 |  4.1 |  3.0 |  182 |  19200 |  $17\pm6$ |  $13\pm4$ |  $125$ |  |  |
|  |  9 |  281.92615 |  -2.00656 |  5.8 |  4.5 |  267 |  28000 |  $22\pm8$ |  $88\pm29$ |  $25$ |  |  |
|  |  10 |  281.91755 |  -2.00957 |  3.2 |  3.0 |  188 |  17100 |  $2.6\pm1.0$ |  $14\pm5$ |  $19$ |  |  |
|  |  11 |  281.92172 |  -2.01119 |  3.3 |  3.2 |  201 |  17600 |  $2.0\pm1.0$ |  $9.6\pm3.4$ |  $20$ |  |  |
|  |  12 |  281.92276 |  -2.00934 |  2.9 |  2.9 |  213 |  16000 |  $2.4\pm1.5$ |  $3.5\pm1.2$ |  $68$ |  |  |
|  |  13 |  281.91882 |  -2.00633 |  3.0 |  2.5 |  112 |  15100 |  $1.2\pm0.7$ |  $-$ |  $-$ |  |  |
|  |  14 |  281.91639 |  -2.00911 |  3.7 |  3.4 |  221 |  19600 |  $1.1\pm0.5$ |  $7.6\pm2.8$ |  $14$ |  |  |
|  |  15 |  281.92751 |  -2.00159 |  3.1 |  3.0 |  181 |  17000 |  $0.72\pm0.41$ |  $7.8\pm3.3$ |  $9$ |  |  |
|  |  16 |  281.92380 |  -2.00008 |  3.8 |  3.7 |  102 |  20600 |  $0.65\pm0.35$ |  $3.7\pm1.4$ |  $18$ |  |  |
|  |  17 |  281.91991 |  -2.01022 |  3.3 |  2.8 |  208 |  16700 |  $1.1\pm0.7$ |  $-$ |  $-$ |  |  |
|  |  18 |  281.92807 |  -2.01115 |  9.1 |  7.0 |  261 |  44000 |  $6.0\pm2.5$ |  $-$ |  $-$ |  |  |
|  |  19 |  281.92685 |  -1.99503 |  2.6 |  2.4 |  92 |  13700 |  $0.14\pm0.1$ |  $-$ |  $-$ |  |  |
|  |  20 |  281.92531 |  -2.00899 |  3.9 |  2.7 |  234 |  17600 |  $2.3\pm1.5$ |  $29\pm10$ |  $8$ |  |  |
|  |  21 |  281.92172 |  -2.00737 |  3.9 |  2.7 |  238 |  17800 |  $1.6\pm1.4$ |  $-$ |  $-$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| W51-E |  1 |  290.93296 |  14.50771 |  3.7 |  3.4 |  180 |  19000 |  $750\pm240$ |  $7700\pm2100$ |  $10$ |  |  |
|  |  2 |  290.93308 |  14.50973 |  3.5 |  3.2 |  217 |  17900 |  $740\pm240$ |  $7900\pm2100$ |  $9$ |  |  |
|  |  3 |  290.92460 |  14.51014 |  4.1 |  3.7 |  239 |  21000 |  $100\pm30$ |  $1300\pm300$ |  $8$ |  |  |
|  |  4 |  290.92997 |  14.51419 |  4.2 |  3.8 |  250 |  21700 |  $39\pm14$ |  $6.2\pm2.5$ |  $624$ |  |  |
|  |  5 |  290.92436 |  14.51500 |  4.8 |  4.5 |  238 |  24900 |  $63\pm22$ |  $45\pm14$ |  $139$ |  |  |
|  |  6 |  290.93241 |  14.50588 |  5.6 |  5.1 |  106 |  28900 |  $78\pm29$ |  $32\pm11$ |  $242$ |  |  |
|  |  7 |  290.92567 |  14.51592 |  7.8 |  7.0 |  231 |  39700 |  $23\pm10$ |  $21\pm7$ |  $110$ |  |  |
|  |  8 |  290.93558 |  14.50764 |  4.8 |  4.0 |  180 |  23800 |  $7.3\pm5.6$ |  $180\pm50$ |  $4$ |  |  |
|  |  |  |  |  |  |  |  |  |  |  |  |  |
| W51-IRS2 |  1 |  290.91682 |  14.51812 |  3.5 |  3.2 |  170 |  18100 |  $230\pm80$ |  $11200\pm3100$ |  $2$ |  |  |
|  |  2 |  290.91558 |  14.51820 |  3.5 |  3.5 |  96 |  18800 |  $180\pm60$ |  $5000\pm1400$ |  $4$ |  |  |
|  |  3 |  290.91076 |  14.51156 |  3.5 |  3.0 |  173 |  17600 |  $36\pm13$ |  $420\pm120$ |  $9$ |  |  |
|  |  4 |  290.90913 |  14.51854 |  3.0 |  2.9 |  224 |  16000 |  $27\pm11$ |  $170\pm50$ |  $16$ |  |  |
|  |  5 |  290.91630 |  14.51935 |  3.9 |  3.7 |  243 |  20600 |  $95\pm34$ |  $120\pm40$ |  $77$ |  |  |
|  |  6 |  290.92445 |  14.51014 |  4.5 |  3.7 |  267 |  22200 |  $95\pm35$ |  $45\pm13$ |  $212$ |  |  |
|  |  7 |  290.90698 |  14.50617 |  4.7 |  3.6 |  119 |  22100 |  $16\pm6$ |  $94\pm29$ |  $17$ |  |  |
|  |  8 |  290.91443 |  14.51766 |  3.6 |  3.4 |  183 |  18700 |  $68\pm26$ |  $130\pm40$ |  $51$ |  |  |
|  |  9 |  290.91869 |  14.51785 |  4.2 |  3.8 |  188 |  21600 |  $60\pm24$ |  $70\pm22$ |  $86$ |  |  |
|  |  10 |  290.90913 |  14.50917 |  3.5 |  3.1 |  112 |  17900 |  $15\pm6$ |  $73\pm23$ |  $21$ |  |  |
|  |  11 |  290.90989 |  14.51025 |  3.9 |  3.4 |  111 |  19500 |  $17\pm7$ |  $61\pm20$ |  $27$ |  |  |
|  |  12 |  290.92365 |  14.51727 |  3.5 |  3.0 |  142 |  17500 |  $34\pm13$ |  $17\pm5$ |  $197$ |  |  |
|  |  13 |  290.91132 |  14.51272 |  3.1 |  2.6 |  93 |  15200 |  $10\pm5$ |  $83\pm27$ |  $12$ |  |  |
|  |  14 |  290.90509 |  14.51838 |  3.4 |  3.0 |  147 |  17300 |  $3.7\pm1.8$ |  $1300\pm400$ |  $0.3$ |  |  |
|  |  15 |  290.92490 |  14.51970 |  3.6 |  3.2 |  230 |  18500 |  $23\pm10$ |  $57\pm21$ |  $40$ |  |  |
|  |  16 |  290.92275 |  14.51438 |  4.1 |  4.0 |  144 |  21900 |  $46\pm20$ |  $140\pm40$ |  $33$ |  |  |
|  |  17 |  290.92606 |  14.51511 |  4.3 |  3.7 |  141 |  21300 |  $48\pm20$ |  $300\pm90$ |  $16$ |  |  |
|  |  18 |  290.92550 |  14.50883 |  5.7 |  5.1 |  218 |  29200 |  $74\pm28$ |  $22\pm8$ |  $335$ |  |  |
|  |  19 |  290.90949 |  14.50767 |  3.3 |  3.0 |  108 |  17100 |  $4.4\pm2.2$ |  $7.8\pm3.2$ |  $57$ |  |  |
|  |  20 |  290.92418 |  14.51496 |  4.1 |  3.9 |  110 |  21400 |  $35\pm15$ |  $25\pm10$ |  $139$ |  |  |
|  |  21 |  290.90817 |  14.52005 |  3.8 |  3.4 |  203 |  19200 |  $4.2\pm2.3$ |  $7.8\pm3.0$ |  $54$ |  |  |
|  |  22 |  290.92120 |  14.51640 |  3.5 |  3.1 |  172 |  18000 |  $12\pm6$ |  $8.6\pm4.0$ |  $134$ |  |  |
|  |  23 |  290.90805 |  14.50825 |  4.1 |  3.2 |  131 |  19700 |  $6.2\pm3.0$ |  $8.4\pm3.8$ |  $74$ |  |  |
|  |  24 |  290.91159 |  14.51852 |  4.2 |  3.6 |  248 |  20900 |  $14\pm7$ |  $5.0\pm2.6$ |  $279$ |  |  |
|  |  25 |  290.92036 |  14.51299 |  4.3 |  3.7 |  244 |  21400 |  $9.0\pm4.7$ |  $-$ |  $-$ |  |  |
|  |  26 |  290.91586 |  14.51326 |  2.9 |  2.8 |  115 |  15500 |  $2.4\pm1.8$ |  $0.6\pm0.36$ |  $398$ |  |  |
|  |  27 |  290.91307 |  14.51820 |  6.1 |  5.1 |  193 |  30100 |  $40\pm18$ |  $-$ |  $-$ |  |  |
|  |  28 |  290.91618 |  14.52051 |  6.8 |  5.5 |  161 |  33000 |  $70\pm31$ |  $170\pm50$ |  $41$ |  |  |
|  |  29 |  290.90722 |  14.51021 |  3.7 |  3.3 |  118 |  18900 |  $1.3\pm0.9$ |  $-$ |  $-$ |  |  |

: continued.

 \
 \

The quantities a, b, PA, FWHM, $L_\mathrm{bol}$, $M$ and $L / M$ are respectively the major and minor sizes at half-maximum, angle of the major axis (east of vertical), physical full width at half-maximum in astronomical units, bolometric luminosity, mass, and (bolometric) luminosity-to-mass ratio. Some sources overlap between W43-MM2 and W43-MM3.

[^1]: The luminosity, temperature and column density maps are only available in electronic form at the CDS via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via <http://cdsweb.u-strasbg.fr>.

[^2]: <https://www.almaimf.com/>

[^3]: (cite: Koenig2017) assumed 4.8, 5, 3.1, 3.6, 3.2, 4.4, 1.0, 3.4, and 4.9 kpc respectively for G008.67, G010.62, G327.29, G333.60, G337.92, G338.92, G351.77, G353.41, and W43-MM1.

[^4]: <https://github.com/ahoward-cf/ppmap>

[^5]: <http://archives.esac.esa.int/hsa/legacy/ADP/PSF/SPIRE/SPIRE-P/>

</paper>

Write the methods card for this paper.