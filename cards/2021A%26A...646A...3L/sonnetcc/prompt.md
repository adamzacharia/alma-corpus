# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...646A...3L\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...646A...3L",
 "title": "Chemically tracing the water snowline in protoplanetary disks with HCO<SUP>+</SUP>",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Leemker, M.",
 "n_authors": 7,
 "arxiv_id": "2011.12319",
 "doi": "10.1051/0004-6361/202039387",
 "alma_projects_linked_by_archive": [
  "2017.1.01066.T",
  "2018.1.01131.S"
 ]
}
```

Paper text:
<paper>
# Chemically tracing the water snowline in protoplanetary disks with HCO$^+$

Following earlier observed correlations between water and H$^{13}$CO$^+$ emission in a protostellar envelope, the aim of this research is to investigate the validity of HCO$^+$ and the optically thin isotopologue, H$^{13}$CO$^+$, as tracers of the water snowline in protoplanetary disks and the required sensitivity and resolution to observationally confirm this. A typical Herbig Ae disk structure is assumed and its temperature structure is modelled with the thermochemical code `DALI`. Two small chemical networks are then used and compared to predict the HCO$^+$ abundance in the disk; one without water and one including water. Subsequently, the corresponding emission profiles are modelled for the $J=2-1$ transition of H$^{13}$CO$^+$ and HCO$^+$, which provides the best balance between brightness and optical depth effects of the continuum emission, and is less affected by blending with complex molecules. Models are then compared with archival ALMA data. The HCO$^+$ abundance jumps by two orders of magnitude over a radial range of 2 AU outside the water snowline, which in our model is located at 4.5 AU. We find that the emission of H$^{13}$CO$^+$ and HCO$^+$ is ring-shaped due to three effects: destruction of HCO$^+$ by gas-phase water, continuum optical depth, and molecular excitation effects. Comparing the radial emission profiles for $J=2-1$ convolved with a $0.05\ensuremath{''}$ beam reveals that the presence of gas-phase water causes an additional drop of only $\sim$13% and 24% in the center of the disk, for H$^{13}$CO$^+$ and HCO$^+$, respectively. For the much more luminous outbursting source V883 Ori, our models predict that the effects of dust and molecular excitation are not limiting HCO$^+$ as a snowline tracer if the snowline is located at radii larger than $\sim$40 AU. Our analysis of recent archival ALMA band 6 observations of the $J=3-2$ transition of HCO$^+$ is consistent with the water snowline located around 100 AU, further out than was previously estimated from an intensity break in the continuum emission. The HCO$^+$ abundance drops steeply around the water snowline, when water desorbs in the inner disk, but continuum optical depth and molecular excitation effects conceal the drop in HCO$^+$ emission due to the water snowline. Therefore locating the water snowline with HCO$^+$ observations in disks around Herbig Ae stars is very difficult, but it is possible for disks around outbursting stars such as V883 Ori, where the snowline has moved outwards.

# Introduction

High resolution observations of protoplanetary disks show that many of them have rings, gaps, and other substructures (e.g., (cite: Andrews2010; vanderMarel2015; Fedele2017; Huang2018DSHARPII; Long2018); and (cite: Andrews2020) for a review). Different explanations have been proposed for these substructures such as planets (e.g. (cite: Bryden1999; Zhu2014; Dong2018)) and snowlines (e.g. (cite: Banzatti2015; Zhang2015; Okuzumi2016)). A snowline is the midplane radius in a protoplanetary disk where 50% of one of the major volatiles is in the gas phase and 50% is frozen out onto the dust grains. These snowlines are related to planet formation, because dust properties change around the H$_2$O and CO or CO$_2$ snowlines (cite: Pinilla2017). Even though water ice mantles may not always aid dust coagulation by collisions (cite: Kimura2020), the sublimation, condensation, and diffusion of gas-phase water enhances the surface density around the water snowline aiding planet formation and potentially triggering the streaming instability (e.g. (cite: Stevenson1988; Drazkowska2017; Schoonenberg2017)).

Snowlines do not only affect the formation of planets but they also affect their chemical composition. The sequential freeze-out of the major volatile species changes the bulk chemical composition, often measured as the C/O ratio, of the planet-forming material with the ice becoming more oxygen-rich than the gas (cite: Oberg2011; Eistrup2016; Eistrup2018). The water snowline is of particular importance as water is crucial for the origin of life.

Knowledge of the water snowline location is thus essential for the understanding of planet formation and composition. Yet observing water snowlines is challenging because their expected location is only a few AU from the host star for T Tauri disks (cite: Harsono2015) and $\sim$10 AU for disks around more luminous Herbig Ae stars. Therefore, observations with very high spatial resolution are necessary. On top of that, observing water snowlines directly from the ground by observing gas-phase water in protoplanetary disks is challenging because of the absorption of water in the Earth’s atmosphere. The only detections of water in protoplanetary disks probe the inner most hot parts ($\lesssim$5 AU; e.g. (cite: Carr2008; Salyk2008; Mandell2012)) or the cold outer parts with space-based telescopes, analysing multiple water lines (cite: Hogerheijde2011; Zhang2013; Blevins2016; Salinas2016; Du2017) or have used both ground based and space based telescopes (cite: Banzatti2017; Salyk2019). Targeting less abundant isotopologues of water, e.g. H$_2^{18}$O, reduces the atmospheric absorption, but detecting these molecules at a significant signal-to-noise ratio greatly increases the required observing time. Space-based telescopes circumvent this problem, but so far, lacked the spatial resolution to resolve the water snowline.

Chemical tracers provide an alternative way of locating snowlines. Some molecules show ring-shaped emission even if the density of the disk is smooth. One example of such a molecule is CN, which is enhanced if a strong UV field is present (e.g. (cite: vanZadelhoff2003; Teague2016; Cazzoletti2018)) and other examples are molecules that trace snowlines. Chemical imaging has been used to locate the CO snowline in the disks around TW Hya and HD 163296 using N$_2$H$^+$ and DCO$^+$ (cite: Mathews2013; Qi2013; Qi2015; Qi2019). Both tracers show ring-shaped emission but detailed chemical modelling is needed to infer the location of the CO snowline from these observations (cite: Aikawa2015; vantHoff2017; Carney2018).

Water can be traced chemically using the HCO$^+$ ion, which is destroyed by gas-phase water (cite: Phillips1992; Bergin1998): $$\begin{align}
\mathrm{HCO^+} + \mathrm{H_2O} \to \mathrm{CO} + \mathrm{H_3O^+}. \label{eq:HCOpH2O}
\end{align}$$ Based on this reaction, HCO$^+$ is expected to be abundant when water is frozen out onto the grains and HCO$^+$ is depleted when water is in the gas phase. This anti-correlation between water and HCO$^+$ has been verified observationally by the optically thin isotopologue H$^{13}$CO$^+$ and an isotopologue of water, H$_2^{18}$O, in a protostellar envelope (cite: vantHoff2018water). Due to the high luminosity of young stellar objects at this early stage, the snowline is located further away from the star than in protoplanetary disks (cite: Visser2012; Jorgensen2013; Vorobyov2013; Visser2015; Cieza2016; Hsieh2019). Similarly, the higher luminosity of Herbig Ae stars compared to T Tauri stars increases the temperature in the protoplanetary disks around them, which locates the water snowline further out in disks around the former type. Therefore, we focus on protoplanetary disks around Herbig Ae stars in this work.

The aim of this paper is to investigate HCO$^+$ as a tracer of the water snowline in protoplanetary disks. Compared to protostellar envelopes the 2D temperature and density structure of disks complicates matters. First, the location of the water snowline in protoplanetary disks around Herbig Ae stars is expected around 10 AU, in contrast to $\gtrsim$100 AU in protostellar envelopes. Second, the higher column density in disks increases the optical depth of the continuum and line emission. This complicates locating the water snowline as emission from HCO$^+$ can be absorbed by dust particles, mimicking the effect of depletion due to gas-phase water on the HCO$^+$ emission. Finally, the HCO$^+$ emission can also be ring-shaped when the $J$-level population of the low levels, that can be observed with ALMA, decreases towards the center of the star due to the increase in temperature and density in the inner disk. This also mimics the effect of gas-phase water on the HCO$^+$ emission.

The validity of HCO$^+$ as a tracer of the water snowline in protoplanetary disks is investigated by modelling the physical and chemical structure of a disk around a typical Herbig Ae star with a luminosity of 36 L$_{\odot}$ as described in Section [2](#sec:models). The predicted abundance structure of HCO$^+$ is presented in Section [3.1](#sec:resultschem), and the corresponding emission profiles of HCO$^+$ and H$^{13}$CO$^+$ are described in Section [3.2](#sec:results_rad_cut) and [3.3](#sec:results_line_profile). Archival ALMA observations of H$^{13}$CO$^+$ in the outbursting source V883 Ori are discussed in Section [4](#sec:obs). Finally we conclude in Section [5](#sec:concl) that it is difficult to use HCO$^+$ as a tracer of the water snowline in disks around Herbig Ae stars, but that it is possible for outbursting sources such as V883 Ori.

# Protoplanetary disk model

The HCO$^+$ and H$^{13}$CO$^+$ radial emission profiles are modelled in several steps. First, a density structure for a typical disk around a Herbig Ae star is assumed. Second, the gas temperature is calculated using the thermochemical code `DALI` (cite: Bruderer2009; Bruderer2012; Bruderer2013). The gas density and gas temperature are then used as input for two chemical models, one without water and one with water, that predict the HCO$^+$ abundance in the disk. These abundance profiles together with the density and temperature structure of the disk are used to model the HCO$^+$ and H$^{13}$CO$^+$ emission profiles with `DALI`.

## Disk structure

| Model parameter              | Value                       |
|:-----------------------------|:----------------------------|
|                              |                             |
| *Physical structure*         |                             |
| $R_{\mathrm{subl}}$          | 0.05 AU                     |
| $R_{\mathrm{c}}$             | 50 AU                       |
| $\Sigma_{\mathrm{c}}$        | 5.8 g$\ \mathrm{cm^{-2}}$   |
| $M_{\mathrm{disk}}$          | $0.01 \ \mathrm{M_{\odot}}$ |
| $\gamma$                     | 1                           |
| $h_{\mathrm{c}}$             | 0.1                         |
| $\psi$                       | 0.25                        |
|                              |                             |
| *Dust properties*            |                             |
| $\chi$                       | 0.2                         |
| $f_{\mathrm{ls}}$            | 0.85                        |
| $\Delta_{\mathrm{gas/dust}}$ | 100                         |
|                              |                             |
| *Stellar spectrum*$^{(1)}$   |                             |
| Type                         | Herbig                      |
| $L_{\star}$                  | 36 $\mathrm{L_{\odot}}$     |
| $L_{\mathrm{X}}$             | 8(28) erg s$^{-1}$          |
| $T_{\mathrm{eff}}$           | $1(4)$ K                    |
| $T_{\mathrm{X}}$             | 7(7) K                      |
| $\zeta_{\mathrm{c.r.}}$      | 5(-17) $\mathrm{s^{-1}}$    |
|                              |                             |
| *Stellar properties*         |                             |
| $M_{\star}$                  | $2.3 \ \mathrm{M_{\odot}}$  |
|                              |                             |
| *Observational geometry*     |                             |
| $i$                          | 38$\degree$                 |
| $d$                          | 100 pc                      |

: `DALI` model parameters for the disk around a typical Herbig Ae star.

**Notes.** $a(b)$ represents $a\times 10^b$. $^{(1)}$ Spectrum of HD 100546 (cite: Kama2016), which is well approximated by a 10$^4$ K black body spectrum.

The density structure of the disk is modelled with the thermochemical code `DALI` following the approach of (cite: Andrews2011). This approach is based on the self-similar solution for a viscously evolving disk, where the gas surface density of the disk outside the dust sublimation radius follows a power law with an exponential taper (cite: LyndenBell1974; Hartmann1998): $$\begin{align}
\Sigma_{\mathrm{gas}} (R) = \Sigma_{\mathrm{c}} \left (\frac{R}{R_{\mathrm{c}}} \right )^{-\gamma} \exp \left [-\left (\frac{R}{R_{\mathrm{c}}}\right )^{2-\gamma} \right ],
\end{align}$$ with $\Sigma_{\mathrm{c}}$ the gas surface density at the characteristic radius $R_{\mathrm{c}}$ and $\gamma$ the power law index. A sublimation radius of $R_{\mathrm{subl}} = 0.05$ AU is assumed. Inside this radius, the surface density is set to 7$\times$10$^2$ cm$^{-3}$. An overview of all parameters used for the density and temperature structure can be found in Table [1](#tab:paramsdali).

![](dngas_)

![](dTgas_)

![](dTdust_)

The gas follows a Gaussian distribution in the vertical direction, where the temperature is calculated explicitly at each location in the disk. The scale height of the gas is set by the flaring index $\psi$ and the characteristic scaleheight $h_{\mathrm{c}}$ at $R_{\mathrm{c}}$, $$\begin{align}
h = h_{\mathrm{c}} \left ( \frac{R}{R_{\mathrm{c}}} \right )^{\psi}.
\end{align}$$ The resulting gas density of our model is shown in the top panel of Fig. [1](#fig:DALImodel).

The dust surface density is modelled with `DALI` by scaling the gas surface density with the disk-averaged gas-to-dust mass ratio, $\Delta_{\mathrm{gas/dust}}$, which is set to the ISM value of 100. The vertical structure of the dust is modelled using two populations of dust grains following the approach of (cite: DAlessio2006). Small grains with sizes between 5 nm and 1 $\mu$m are well mixed with the gas and therefore follow the same vertical structure of the gas. Large grains with sizes from 5 nm to 1 mm are settled to the disk midplane. This is modelled by reducing the scale height of the large grains with a factor $\chi < 1$. The fraction of the dust mass in large grains is controlled by $f_{\mathrm{ls}}$ and the size distribution of both grain populations is assumed to be proportional to $a^{-3.5}$ with $a$ the size of the grains (MRN distribution, (cite: Mathis1977)).

The gas temperature needs to be computed separately as the abundances of the molecules that act as coolants of the gas in the disk affect the gas temperature, which in turn affects the chemistry. Therefore, `DALI` solves for the gas temperature by iterating over the chemistry and heating by the photoelectric effect and the cooling by molecules in the gas. The dust temperature is computed using Monte Carlo continuum radiative transfer. The gas and dust temperature calculated by `DALI` are shown in the middle and bottom panel of Fig. [1](#fig:DALImodel). The gas temperature exceeds the dust temperature in the surface layers only, whereas the gas and dust temperatures are equal in deeper layers of the disk.

## Chemical models

= \[rectangle, draw, fill=blue!20, text width=4.2em, text centered, rounded corners, minimum height=2em\] = \[rectangle, draw, ultra thick, fill=blue!20, text width=4.2em, text centered, rounded corners, minimum height=2em\]

|  | reaction | $\alpha$ | $\beta$ | $\gamma$ | $k (100~\mathrm{K})$ | $k (150~\mathrm{K})$ | units | ref. | NW | W |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| $\zeta_{\mathrm{c.r.}}$ | $\mathrm{H_2 + c.r. \to H_2^+ + e^-}$ | $1(-17)$ | $0$ | $0$ | $1(-17)$ | $1(-17)$ | $\mathrm{s^{-1}}$ |  | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{2}}$ | $\mathrm{H_2^+ + H_2 \to H_3^+ + H}$ | $2.1(-9)$ | $0$ | $0$ | $2.1(-9)$ | $2.1(-9)$ | $\mathrm{cm^3\ s^{-1}}$ | \(a\) | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{3}}$ | $\mathrm{H_3^+ + e^- \to H_2 + H}$ | $2.3(-8)$ | $-0.5$ | $0$ | $4.1(-8)$ | $3.4(-8)$ | $\mathrm{cm^3\ s^{-1}}$ | \(b\) | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{4}}$ | $\mathrm{CO + H_3^+ \to HCO^+ + H_2}$ | $1.4(-9)$ | $-0.1$ | $-3.4$ | $1.6(-9)$ | $1.5(-9)$ | $\mathrm{cm^3\ s^{-1}}$ | \(c\) | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{e^-}}$ | $\mathrm{HCO^+ + e^- \to CO + H}$ | $2.4(-7)$ | $-0.7$ | $0$ | $5.1(-7)$ | $3.9(-7)$ | $\mathrm{cm^3\ s^{-1}}$ | \(d\) | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{H_2O}}$ | $\mathrm{HCO^+ + H_2O \to CO + H_3O^+}$ | $2.5(-9)$ | $-0.5$ | $0$ | $4.3(-9)$ | $3.5(-9)$ | $\mathrm{cm^3\ s^{-1}}$ | \(e\) |  | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{7}}$ | $\mathrm{H_3O^+ + e^- \to H_2O + H}$ | $7.1(-8)$ | $-0.5$ | $0$ | $1.2(-7)$ | $1.0(-7)$ | $\mathrm{cm^3\ s^{-1}}$ | \(f\) |  | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{8}}$ | $\mathrm{H_2O + H_3^+ \to H_3O^+ + H_2}$ | $5.9(-9)$ | $-0.5$ | $0$ | $1.0(-8)$ | $8.3(-9)$ | $\mathrm{cm^3\ s^{-1}}$ | (g, h) |  | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{f}}$ | $\mathrm{H_2O  \to H_2O\ (ice)}$ | $\dfrac{1.2(-5)n(\mathrm{H_2})}{10(12) \mathrm{cm^{-3}}}$ | $0.5$ | $0$ | $\dfrac{6.7(-6)n(\mathrm{H_2})}{10(12) \mathrm{cm^{-3}}}$ | $\dfrac{8.3(-6)n(\mathrm{H_2})}{10(12) \mathrm{cm^{-3}}}$ | $\mathrm{s^{-1}}$ | \(i\) |  | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |
| $k_{\mathrm{d}}$ | $\mathrm{H_2O\ (ice) \to H_2O }$ | $2.8(12)$ | $0$ | $5.8(3)$ | $2.4(-13)$ | $5.4(-5)$ | $\mathrm{s^{-1}}$ | \(i\) |  | (0,.35) – (.25,0) – (1,.7) – (.25,.15) – cycle; |

**Notes.** $a(b)$ represents $a\times 10^b$. NW is the chemical network without water, whereas W includes water. All reactions are given in the form $k~=~\alpha~(T_{\mathrm{gas}}/300\mathrm{K})^{\beta}\exp(-\gamma/T_{\mathrm{gas}})$, where the values of $\alpha$, $\beta$, and $\gamma$ for $k_{\mathrm{2}}$, $k_{\mathrm{3}}$, $k_{\mathrm{4}}$, $k_{\mathrm{e^-}}$, $k_{\mathrm{H_2O}}$, $k_{\mathrm{7}}$ and $k_{\mathrm{8}}$ are taken from the rate12 UMIST database (cite: McElroy2013) and $k_{\mathrm{d}}$ uses $T_{\mathrm{dust}}$ instead of $T_{\mathrm{gas}}$. References: (a) (cite: Theard1974), (b) (cite: McCall2004), (c) (cite: Klippenstein2010), (d) (cite: Mitchell1990), (e) (cite: Adams1978), (f) (cite: Novotny2010), (g) (cite: Kim1974), (h) (cite: Anicich1975) and (i) Appendix [6](#sec:fdwater) and references therein.

The HCO$^+$ abundance with respect to the total number of hydrogen atoms in the disk is modelled with a small chemical network, which is solved time-dependently up to 1 Myr with the python function `odeint`[^1]. This allows us to more easily study the effect of different parameters than with a computationally more expensive full chemical model. The HCO$^+$ abundance in protoplanetary disks is mainly controlled by three reactions. The main formation route of HCO$^+$ involves gas-phase CO: $$\begin{align}
\mathrm{CO} + \mathrm{H_3^+} \to \mathrm{HCO^+} + \mathrm{H_2}. \label{eq:HCOpform}
\end{align}$$ Here, H$_3^+$ is produced by cosmic ray ionization of molecular hydrogen at a rate of $\zeta_{\mathrm{c.r.}}$. On the other hand, HCO$^+$ is destroyed by gas-phase water (Eq. [\[eq:HCOpH2O\]](#eq:HCOpH2O)) and by dissociative recombination with an electron: $$\begin{align}
\mathrm{HCO^+} + \mathrm{e^-} \to \mathrm{CO} + \mathrm{H}. \label{eq:HCOpem}
\end{align}$$ Therefore, a jump in the HCO$^+$ abundance around the water snowline is expected if electrons are not the dominant destruction mechanism of HCO$^+$.

To investigate the relationship between HCO$^+$ and H$_2$O, two small chemical networks are used. The first network, network *no water* (NW), is shown in the dashed box in Fig. [2](#fig:networkC). This network includes three reactions to model the ionization in the disk (reactions $\zeta_{\mathrm{c.r.}}$, $k_{\mathrm{2}}$ and $k_{\mathrm{3}}$ in Table [\[tab:reactions\]](#tab:reactions)), and two reactions to model the HCO$^+$ abundance in the absence of gas-phase water (reactions $k_{\mathrm{4}}$ and $k_{\mathrm{e^-}}$ (Eq. [\[eq:HCOpform\]](#eq:HCOpform) and [\[eq:HCOpem\]](#eq:HCOpem)) in Table [\[tab:reactions\]](#tab:reactions)). As reaction $k_{\mathrm{H_2O}}$ (Eq. [\[eq:HCOpH2O\]](#eq:HCOpH2O)) is not included in this network, HCO$^+$ is not expected to trace the water snowline in network NW. Therefore, this network serves as a baseline to quantify the effect of the gas-phase water on the HCO$^+$ abundance. The second network, network *water* (W), is shown in the solid box in Fig. [2](#fig:networkC) and contains all reactions present in Table [\[tab:reactions\]](#tab:reactions). Network W includes those in network NW together with reactions to model the effect of water on the HCO$^+$ abundance. The most important reaction for our study is indicated in red in Fig. [2](#fig:networkC) and is the destruction of HCO$^+$ by gas-phase water (reaction $k_{\mathrm{H_2O}}$ or Eq. [\[eq:HCOpH2O\]](#eq:HCOpH2O)). The other reactions present in network W include the freeze-out and desorption of water (reactions $k_{\mathrm{f}}$ and $k_{\mathrm{d}}$) and the formation and destruction of gas-phase water from and to H$_3$O$^+$ (reactions $k_{\mathrm{7}}$ and $k_{\mathrm{8}}$). Therefore, HCO$^+$ is expected to trace the water snowline in network W. The equations for the freeze-out and desorption rates of water can be found in Appendix [6](#sec:fdwater).

Initially, the abundance of all gas- and ice-phase species are set to 0 except for the abundance of gas-phase CO, which is set to $10^{-4}$ both in network NW and W, and the abundance of gas-phase water in network W, which is set to $3.8\times 10^{-7}$, appropriate for a dark cold cloud (cite: McElroy2013), see also Table [2](#tab:params_chem_net). The rate coefficient for the freeze-out of water depends on multiple parameters, including the number density and size of the grains. Therefore, we assume in chemical network NW and W a typical grain number density of 10$^{-12}\times n(\mathrm{H_2})$ and a grain size of 0.1 $\mu$m, which set the surface area available for chemistry on grains. Assuming a single grains size for the chemistry is an approximation, but the effect of grain growth in disks, which decreases this area, is cancelled by the dust settling in disks, which increases this area as there is more dust available for chemistry in the midplane (cite: Eistrup2016). Finally, the H$^{13}$CO$^+$ abundance is taken to be a factor 70 smaller than the abundance of HCO$^+$, corresponding to the typical $^{12}$C/$^{13}$C isotope ratio (cite: Milam2005).

## Radiative transfer

Predictions for multiple transitions of HCO$^+$ and H$^{13}$CO$^+$ were made using the ray tracer in `DALI`, where the outputs of the chemical networks discussed in Section [2.2](#sec:chemmod) were used to set the abundance and both line and continuum optical depth are included. The line radiative transfer does not assume LTE. Instead, the excitation is calculated explicitly, where we used the collisional rate coefficients in the LAMDA database (cite: Botschwina1993; Flower1999; Schoier2005).

Furthermore, the disk is assumed to be located at a distance of 100 pc and the inclination is taken to be 38$\degree$. Changing the inclination does not significantly change our results. The radial emission profiles are taken to be along the semi-major axis of the disk. The focus in the paper is on the $J=2-1$ transition at 178.375 GHz and 173.507 GHz for HCO$^+$ and H$^{13}$CO$^+$ respectively, because this transition provides the best balance between the brightness of the line and the effects of the continuum optical depth. Moreover, the higher transitions could be blended with emission from complex organic molecules. Predictions for the weaker $J=1-0$ transition, as well as the brighter $J=3-2$ and $J=4-3$ transitions, that are more affected by the optical depth of the continuum emission and emission from complex organic molecules, can be found in Appendix [8](#app:Radialcutsotherlines). To mimic high resolution ALMA observations, the emission is convolved with a $0.05\ensuremath{''}$ beam, unless denoted otherwise.

# Modelling results

## Chemistry

![](cnHCOpA_xH2O_3p8e-07_xCO_1p0e-04_zeta_1p0e-17_at_1p0_Myr_Tgas_neq_Tdust_)

![](cnHCOpD_xH2O_3p8e-07_xCO_1p0e-04_zeta_1p0e-17_at_1p0_Myr_Tgas_neq_Tdust_.png)

The predicted abundances of HCO$^+$ by chemical networks NW and W are presented in Fig. [3](#fig:HCOpnetworkAD). The water snow surface in network W is computed as the surface where 50% of the total water abundance is in the gas-phase and 50% is frozen-out onto the grains and is indicated by the black line. In this model, the water snowline, the midplane location where water freezes-out, is located at 4.5 AU. Comparing the two chemical networks outside the water snow surface shows a great similarity in the predicted HCO$^+$ abundances. This is due to the fact that water is frozen out outside the water snow surface in network W, hence there is very little gas-phase water available for the destruction of HCO$^+$. In network W, the HCO$^+$ abundance drops inside the snowline, and is in general at least two orders of magnitude lower than in network NW. Up to 2 AU outside the water snowline HCO$^+$ is still efficiently destroyed by the small amount of water that is present in the gas-phase. Similar effects were found for N$_2$H$^+$ and CO (cite: Aikawa2015; vantHoff2017). As HCO$^+$ is efficiently destroyed by gas-phase water, it thus is a good chemical tracer of the water snowline.

The morphology of the HCO$^+$ distribution predicted by chemical network W is similar to the morphology predicted by full chemical networks (cite: Walsh2012; Walsh2013; Agundez2018). Chemical network W agrees with the full chemical networks quantitatively inside the water snowline where all studies predict a low HCO$^+$ abundance of $\lesssim10^{-14}$. Moreover, the full networks and network W all show a jump of at least one order of magnitude in the HCO$^+$ abundance over a radial range of 5 AU outside the water snowline. In addition, these models predict a layer starting at $z/r \sim 0.1$ where the HCO$^+$ abundance reaches a high abundance of $10^{-6}-10^{-7}$ ((cite: Walsh2012; Walsh2013) and (cite: Agundez2018)). Yet, this layer is not expected to contribute much to the column density and emission of HCO$^+$, because the densities are low in this layer. The midplane abundances at 10 AU are $\sim10^{-12}$ in the full networks and $10^{-11}$ in network W, though the gradient in the HCO$^+$ abundance is very steep between the water snowline at 4.5 AU and a radius of 10 AU in network W complicating comparison. An HCO$^+$ abundance of $10^{-12}$ is reached at 7 AU. The HCO$^+$ abundance at 100 AU lies within the range of HCO$^+$ abundances predicted by the full chemical models. Our small network is thus suited to study HCO$^+$ as a tracer of the water snowline.

### Water vs. electrons

HCO$^+$ only acts as a tracer of the water snowline if the destruction of HCO$^+$ by electrons is not dominant over the destruction by gas-phase water. The dissociative recombination of HCO$^+$ with an electron is included in both chemical networks. The rates of the reactions in Eq. [\[eq:HCOpH2O\]](#eq:HCOpH2O) and Eq. [\[eq:HCOpem\]](#eq:HCOpem), $R_{\mathrm{H_2O}}$ and $R_{\mathrm{e^-}}$, respectively, are given by: $$\begin{align}
&R_{\mathrm{H_2O}} = k_{\mathrm{H_2O}} n(\mathrm{HCO^+}) n(\mathrm{H_2O})\ \text{and} \\
&R_{\mathrm{e^-}} = k_{\mathrm{e^-}} n(\mathrm{HCO^+})n(\mathrm{e^-}).
\end{align}$$ Using Table [\[tab:reactions\]](#tab:reactions), the ratio of these reaction rates is given by: $$\begin{align}
\frac{R_{\mathrm{e^-}}}{R_{\mathrm{H_2O}}} = 96 \left ( \frac{T_{\mathrm{gas}}}{300 \mathrm{K}} \right ) ^{-0.19} \frac{n(\mathrm{e^-})}{n(\mathrm{H_2O})}.
\end{align}$$ Therefore, gas-phase water is the dominant destruction mechanism of HCO$^+$ if the number density of gas-phase water is about two orders of magnitude larger than the number density of electrons.

Fig. [4](#fig:xelectrons) shows this ratio for chemical network W. The region where electrons are the dominant destruction mechanism ($R_{\mathrm{e^-}} > R_{\mathrm{H_2O}}$) is indicated in red and the region where water is dominant ($R_{\mathrm{e^-}} < R_{\mathrm{H_2O}}$) is indicated in blue. The first region exists mostly outside the water snow surface as water is frozen out. The latter region exists mostly inside and above the water snow surface, because there is plenty of water to destroy HCO$^+$ in these regions. Therefore HCO$^+$ is a good chemical tracer of the water snowline even though electrons are its dominant destruction mechanism in most of the disk.

![](e_vs_H2OD_xH2O_3p8e-07_xCO_1p0e-04_zeta_1p0e-17_at_1p0_Myr_Tgas_neq_Tdust_.png)

### Effect of the CO, H$_2$O abundance, and cosmic ray ionization rate on the HCO$^+$ abundance

In this section we investigate the choice of initial conditions for chemical network W listed in Table [2](#tab:params_chem_net). The HCO$^+$ abundance outside the water snow surface in chemical network W can be approximated analytically (for details see Appendix [7.1](#sec:appxHCOp)): $$\begin{align}
x(\mathrm{HCO^+}) = \sqrt{\frac{\zeta_{\mathrm{c.r.}}}{k_{\mathrm{e^-}}n(\mathrm{H_2})}}. \label{eq:xHCOp}
\end{align}$$ Based on this equation, it is expected that the abundance of HCO$^+$ scales as the square root of the cosmic ray ionization rate in the disk region outside the water snowline. This analytical prediction is consistent with the predictions made by the numerical solution to chemical network W (top left panel in Fig. [12](#fig:icchemnet)), where the HCO$^+$ column density decreases by one order of magnitude if the cosmic ray ionization rate decreases by two orders of magnitude.

Furthermore, the HCO$^+$ abundance is expected to be independent of the initial CO and H$_2$O abundance outside the water snow surface based on the analytical approximation. This is in line with the predictions by the numerical solution to chemical network W (see HCO$^+$ column density in Fig. [12](#fig:icchemnet)). The only major difference between the analytical approximation and the numerical solution occurs inside the water snowline. If the initial abundance of gas-phase water increases up to $\sim5\times 10^{-5}$ as expected for water ice in cold clouds, the column density of HCO$^+$ inside the water snowline decreases. This is because the higher abundance of gas-phase water destroys more HCO$^+$. There is no significant effect on the HCO$^+$ column density outside the water snowline as all water is frozen out in that region of the disk. In summary, HCO$^+$ shows a steep jump in its column density around the water snowline for all initial conditions discussed in this section. Therefore, the results in the following sections do not depend critically on the choice of initial conditions. Further details on the initial conditions can be found in Appendix [7.2](#sec:appinit).

## HCO$^+$ and H$^{13}$CO$^+$ emission

![](Col_dens_and_rad_cuts_2_log_dust_opac1e10less_with_contsub)

Observations do not trace the local abundances, only the emission which is closely related to the column densities if the emission is optically thin. The column densities of HCO$^+$ and the predicted radial emission profiles of HCO$^+$ and H$^{13}$CO$^+$ in network NW and W are shown in Fig. [5](#fig:radialmodelandobs). Similar to the abundance plots of HCO$^+$, the total HCO$^+$ column density jumps by a factor $\sim230$ over a radial range of 3 AU outside the water snowline in network W (solid blue line, top panel). Therefore, the HCO$^+$ column density shows a clear dependence on the presence of gas-phase water and the high HCO$^+$ abundance in the surface layers of the disk does not contribute much to the column density.

On the other hand, the shapes of the radial emission profiles of the HCO$^+$ $J=2-1$ transition are very similar for networks NW and W and the profiles peak at the same radius outside the water snowline (solid lines, middle panel). This is different from the HCO$^+$ column densities where only network W predicts the HCO$^+$ column density to peak outside the water snowline. The drop in the column density around the water snowline translates into a relative maximum difference of only 24% between the radial emission profiles of the $J=2-1$ transition of HCO$^+$. This maximum relative difference is defined as the maximum difference between the flux predicted by network NW and W compared to the maximum flux predicted by network W and is typically located at the water snowline.

HCO$^+$ is more abundant than H$^{13}$CO$^+$, hence H$^{13}$CO$^+$ emission is expected to be optically thin, whereas the HCO$^+$ emission is optically thick. To test if this affects the ability to trace the water snowline, we predict emission from the less abundant isotopologue H$^{13}$CO$^+$. The radial emission profiles of H$^{13}$CO$^+$ for both chemical networks are shown in the bottom panel of Fig. [5](#fig:radialmodelandobs). Qualitatively the profiles are similar to the predicted emission for HCO$^+$. Though the expected flux is about 39 times lower for H$^{13}$CO$^+$ than for HCO$^+$. This difference in flux is less than a factor 70, which indicates that the HCO$^+$ emission is indeed at least partially optically thick. The relative maximum difference between chemical network NW and W is 13% for H$^{13}$CO$^+$, which is almost half of the corresponding number for HCO$^+$. So the effect of the water snowline is also seen in the emission of the optically thin H$^{13}$CO$^+$, but even less prominently. The relative difference for H$^{13}$CO$^+$ is smaller than for HCO$^+$ because H$^{13}$CO$^+$ emits from a lower layer in the disk due to its lower optical depth. Therefore more dust is present above the layer where H$^{13}$CO$^+$ emits, hence the effect of dust is larger for H$^{13}$CO$^+$ than for HCO$^+$.

These models show very similar radial emission profiles predicted for network NW and W and only a small difference in flux. Both networks predict ring shaped emission, regardless of the presence of the water snowline. This decrease in line flux towards the center of the disk can have different origins. The first one is a decrease in the abundance of the observed molecule, discussed in the previous section, which is the effect we aim to observe. However, the optical depth of the continuum emission and molecular excitation effects can change the emission as well, potentially obscuring the effect we would like to trace.

### Continuum optical depth

The continuum affects the line intensity when the optical depth of the continuum emission is larger than the optical depth of the line or when both are optically thick (cite: Isella2016). To investigate the effect of the continuum emission, the $J=2-1$ transition of HCO$^+$ and H$^{13}$CO$^+$ was ray traced in a disk model where the dust opacities (dust mass absorption coefficients $\kappa_{\nu}$) are divided by a factor of $10^{10}$, to cancel the effect of dust on the HCO$^+$ emission compared to the typical Herbig Ae disk model. The results are shown as the dotted lines in Fig. [5](#fig:radialmodelandobs). Comparing these radial emission profiles with the fiducial model shows that the effect of dust is small for network W in the inner $\sim$5 AU (solid versus dotted blue lines) even though the dust in the typical Herbig Ae disk model is optically thick out to $\sim$14 AU (see the orange line in Fig. [6](#fig:taudust1surf)). The reason for this is that the HCO$^+$ abundance is low in the inner disk for network W. Therefore, little emission is expected, hence there is also little emission that can be affected by the dust.

However, the dust can mimic the effect of gas-phase water, which greatly complicates matters. That the effect of the dust is significant, can be seen when the radial emission profiles predicted by network NW in the fiducial disk model and in the model with very low dust opacities (solid versus dotted red lines) are compared. This shows that the dust optical depth is largely responsible for the drop in emission in the center in network NW and for the fact that the radial emission profiles for network NW and W look very similar in the fiducial disk model. Therefore, to locate the water snowline using HCO$^+$, a disk with a high gas-to-dust mass ratio would be most suitable. However, recent work by (cite: Kama2020) has shown that disks with high gas-to-dust mass ratios around Herbig Ae stars are rare. Another option is to target HCO$^+$ in even warmer sources than Herbig Ae stars. Fig. [6](#fig:taudust1surf) shows that in more luminous sources, such as outbursting Herbig sources, the snowline is expected to shift to radii where the dust is optically thin at the wavelengths of the $J=1-0$ to $J=4-3$ transitions of HCO$^+$. Note however that the $\tau_{\mathrm{dust}} = 1$ surfaces not only depend on the frequency but also on the mass of the disk. Nonetheless, typical disk masses are not expected to be more than an order of magnitude higher as that would make them gravitationally unstable (cite: Booth2019; Booth2020; Kama2020).

![](tau_dust_1_and_snowline_locs_loglog)

### Molecular excitation

Decreasing the dust opacities by a factor of $10^{10}$ cannot fully explain the unexpected ring-shaped emission found by network NW. A second effect that contributes to the decrease in flux in the center is the temperature dependence of the $J$-level populations of HCO$^+$. The column densities and midplane populations of several $J$-levels of HCO$^+$ in chemical network NW are shown in Fig. [7](#fig:pops). The column density of the $J=2$ level of HCO$^+$ in chemical network NW peaks at a radius of $\sim$30 AU, while the total HCO$^+$ column density, $N_{\mathrm{tot}}$, peaks on-source (red line in top panel of Fig. [5](#fig:radialmodelandobs)).

The radius where the column density of the $J=2$ level peaks roughly coincides with the radius where the emission of the $J=2-1$ transition of HCO$^+$ associated with network NW with low dust opacities starts to drop. Therefore, both the optical depth of the continuum emission as well as the temperature dependence of the $J$-level population contribute to the drop in emission seen in the center.

![](Midplane_populations_dali)

### Chemistry

Finally there could also be a chemical effect in network NW as the midplane abundance of HCO$^+$ decreases towards the center of the disk. Yet, the total column density of HCO$^+$ keeps increasing up to a radius of 0.07 AU, which is too small to explain the decrease in flux out to $\sim$50 AU seen in the radial emission profile associated with network NW in the fiducial model or to $\sim$10-25 AU in the model with the low dust opacities. Still the drop in the emission associated with network W is for a small part due to a decrease in the total HCO$^+$ column density.

### What causes HCO$^+$ rings?

In summary, all three effects contribute to the decrease in flux in the inner regions of the disk. Observing different transitions of HCO$^+$ and H$^{13}$CO$^+$ will give a different balance of these effects. Fig. [7](#fig:pops) shows that higher $J$-levels are more populated in the inner disk because the inner disk is too warm and dense to highly populate the $J=2$ level of HCO$^+$. However, the emitting frequency of HCO$^+$ increases as higher transitions are observed, so also the continuum optical depth increases.

Therefore it is difficult, yet crucial, to disentangle the effects of the water snowline and of the population of HCO$^+$ and the optical depth of the continuum emission. The effect of the continuum optical depth can be quantified by observing another molecule that emits from the same region as HCO$^+$ or H$^{13}$CO$^+$ but does not decrease in column density towards the star such as a CO isotopologue. The excitation and column density of HCO$^+$ need to be inferred from detailed modelling. In conclusion, the results in this section show that even though the HCO$^+$ abundance changes by at least two orders of magnitude around the water snow surface, it is observationally complicated to verify this.

## Line profiles

![](Line_profile_2)

The discussion above has shown that locating the water snowline using the HCO$^+$ radial emission profile is difficult. The velocity resolved line profile provides an alternative method as the removal of HCO$^+$ in the inner disk is expected to remove flux at the highest Keplerian velocities. Accordingly, the line profile predicted by chemical network W is expected to be narrower than the line profile predicted by network NW.

The line profiles predicted by the two chemical networks for the $J=2-1$ transition of HCO$^+$ and H$^{13}$CO$^+$ are shown in left column of Fig. [8](#fig:lineprofile). To show the difference between the models we subtracted the spectrum associated with network W from the spectrum associated with network NW. The result is shown in the right column of Fig. [8](#fig:lineprofile). This column shows that even though the line profiles look almost identical in the left column, there is an additional bump in the difference between them in the line wings (indicated with the black arrows). However, this difference is only 1.75 mJy for HCO$^+$ and 28 $\mu$Jy for H$^{13}$CO$^+$ i.e. 0.6% and 0.3% of emission, which cannot be detected with a reasonable signal-to-noise ratio. Moreover, detailed comparison with the line profile associated with a molecule that does not show a decrease in the column density in the inner disk would be needed as only the flux associated with network W would be observed and not the flux associated with network NW. Hence, it is very difficult to use the line profiles to locate the water snowline in disks around Herbig Ae stars.

# Comparison with observations

The best targets to observe the water snowline using HCO$^+$ are warm disks, because these disks have a water snowline at a large enough radius for ALMA to resolve. In addition, disks without deep gaps in the gas and dust surface density around the expected location of the snowline are preferred, as these gaps complicate the interpretation of the HCO$^+$ emission.

One of the most promising targets to locate the water snowline in a disk is the young outbursting star V883 Ori, with a current luminosity of $\sim$218 L$_{\odot}$ (cite: Furlan2016). During the outburst, the luminosity is greatly increased, which heats the disk, shifting the water snowline outwards compared to regular T Tauri and even Herbig Ae disks. This not only allows for observations with a larger beam, it also mitigates the effects of the dust as the optical depth of the continuum emission decreases with radius. Previous observations of V883 Ori have inferred the location of the water snowline at 42 AU based on a change in the dust emission (cite: Cieza2016). An extended hot inner region is consistent with the detection of many complex organic molecules (cite: Lee2019). However, an abrupt change in the continuum optical depth or the spectral index are not necessarily due to a snowline, as shown for the cases of CO$_2$, CO and N$_2$ (cite: Huang2018DSHARPII; Long2018; vanTerwisga2018). Methanol observations suggest that the water snowline may be located at a much larger radius of $\sim$100 AU if the methanol observations are optically thin and most of its emission originates from inside the water snowline (cite: vantHoff2018methanol). Observations of HCO$^+$ have the potential to resolve this discrepancy.

## H$^{13}$CO$^+$ observations

A promising dataset to locate the water snowline in V883 Ori is the band 7 observation by (cite: Lee2019) (project code: 2017.1.01066.T, PI: Jeong-Eun Lee), which contains the H$^{13}$CO$^+$ $J=4-3$ line. To date, these observations are the only H$^{13}$CO$^+$ observations in a protoplanetary disk, to our knowledge, at sufficient spatial and spectral resolution with sufficient sensitivity to potentially resolve the water snowline. The synthesized beam of these observations is $0.2\ensuremath{''}$ (40 AU radius, 80 AU diameter at a distance of $\sim$400 pc; (cite: Kounkel2017)), and the spectral resolution is 0.25 km s$^{-1}$. The continuum is created using all line-free channels, which are carefully selected to exclude any line emission. The line data are continuum subtracted using these continuum solutions. Using the CASA 5.1.1 *tclean* task with a Briggs weighting of 0.5, line images are made with a mask of about 2" in diameter centered on the peak of the continuum.

![](Spectrum_3_Gaussians_fit_by_python_masked_new_stacking)

Following the approach of (cite: Lee2019), the line observations are velocity-stacked using a stellar mass, $M_{\star}$ = 1.3 M$_{\odot}$, an inclination of 38$\degree$, and a position angle of 32$\degree$ (cite: Cieza2016). This technique reduces line blending because it makes use of the Keplerian velocity of the disk to calculate the Doppler shift of the emission in each pixel (cite: Yen2016; Yen2018). This Doppler shift is then used to shift the spectrum of each pixel to the velocity of the star, before adding the spectra of all pixels. The noise level of $\sim$15 mJy per spectral bin is determined using an empty region in the stacked image.

The observed spectrum of the inner $0.6\ensuremath{''}$ after line stacking is shown as the black line in the top panel of Fig. [9](#fig:V883Orispec). The rest frequency of the H$^{13}$CO$^+$ $J=4-3$ transition lies between the rest frequencies of the 18$_{7, 12}$ - 17$_{7, 11}$, E transition of acetaldehyde (CH$_3$CHO) ($v=0$) at 346.9955 GHz and the two superimposed 18$_{7, 11}$ - 17$_{7, 10}$, E and 18$_{7, 12}$ - 17$_{7, 11}$, E transitions of CH$_3$CHO ($v_{\mathrm{T}}=2$) at 346.99991 GHz and 346.99994 GHz, respectively (Jet Propulsion Laboratory (JPL) molecular database; (cite: Pickett1998)). In between these acetaldehyde transitions, a clear excess in emission is visible due to the $J=4-3$ transition of H$^{13}$CO$^+$. To quantify this excess emission, two Gaussian profiles are fitted with `curve_fit`[^2] to model the acetaldehyde emission. To reduce the number of free parameters in the fit, the line frequencies are fixed to their respective rest frequencies listed above and the widths of the lines are fixed to 2 km s$^{-1}$ following (cite: Lee2019). In addition, emission within 1 km s$^{-1}$ from the rest frequency of the $J=4-3$ transition of H$^{13}$CO$^+$ is excluded from the fit. The result is shown as the red line in the top panel of Fig. [9](#fig:V883Orispec). Subtracting this fit to the acetaldehyde emission from the observed spectrum clearly reveals emission of the $J=4-3$ transition of H$^{13}$CO$^+$. Therefore we conclude that H$^{13}$CO$^+$ is detected at $>$5$\sigma$ but is blended with lines that are expected to peak on-source, preventing a clean image.

The line blending of H$^{13}$CO$^+$ $J=4-3$ with acetaldehyde prevents us from using the only available dataset covering a transition of H$^{13}$CO$^+$ at sufficient spatial and spectral resolution and sensitivity to resolve the water snowline. The $J=3-2$ transition of H$^{13}$CO$^+$ is likely blended with CH$_3$OCHO as both of them are bright in the Class 0 source B1-c (cite: vanGelder2020). However, the H$^{13}$CO$^+$ $J=2-1$ transition in the same Class 0 B1-c source is free from line blending (van ’t Hoff et al. in prep.) and would therefore be the best line to target in sources with bright emission from complex organics.

## HCO$^+$ observations

Another promising dataset for HCO$^+$ is a recent band 6 dataset (project code 2018.1.01131.S, PI: D. Ruı́z-Rodrı́guez; Ruı́z-Rodrı́guez et al. in prep.). The $J=3-2$ transition of HCO$^+$ is detected with a high signal-to-noise ratio. The spatial resolution of $\sim0.5\ensuremath{''}$ is insufficient to resolve the water snowline if it is located within a radius of $\sim90$ AU (180 AU diameter).

An image of the HCO$^+$ emission will be presented in Ruı́z-Rodrı́guez et al. (in prep.). Here, a normalized, deprojected azimuthal average of the observed emission from the product data of the $J=3-2$ transition of HCO$^+$ is presented in the top panel of Fig. [10](#fig:compareHCO+32_models_obs). This azimuthal average shows that the HCO$^+$ emission is ring shaped. Comparing the band 6 HCO$^+$ emission with the band 7 emission from complex organic molecules presented in (cite: vantHoff2018methanol) and (cite: Lee2019) , reveals that the emission from complex organic molecules such as methanol, 13-methanol, acetaldehyde and H$_2$C$^{18}$O peak inside the HCO$^+$ ring and in some cases is even centrally peaked. This is a strong indication that the lack of HCO$^+$ emission in the center is not only due to the optical depth of the continuum and that HCO$^+$ is indeed tracing the water snowline in V883 Ori. Such an anti-correlation between HCO$^+$ and methanol has also been seen in protostellar envelopes (cite: Jorgensen2013).

![](Normalized_flux_three_Ls_obs_HCO+_methanol)

![](Normalized_flux_three_Ls)

## Model HCO$^+$ images: locating the snowline

![](Cartoons_HCO+_J=3-2_thicker_snowline.png)

To quantify the location of the water snowline, we model the HCO$^+$ and H$^{13}$CO$^+$ emission in a representative model for V883 Ori. This model reproduces the previously observed flux of the $J=2-1$ transition of C$^{18}$O (cite: vantHoff2018methanol), the HCO$^+$ and H$^{13}$CO$^+$ total flux discussed in the previous Sections, and mm continuum fluxes within a factor of $\sim$2. The `DALI` model parameters are presented in Table [3](#tab:paramsdaliV883). The main changes compared to the model for the typical Herbig Ae disk include the mass and radius of the disk and the mass and luminosity of the star. The characteristic disk radius is set to 75 AU to match the radial extent of emission from the $J=2-1$ transition of C$^{18}$O presented by (cite: vantHoff2018methanol). The disk mass is estimated using the 9.1 mm continuum observations of the VANDAM survey (cite: Tobin2020) and the relation between the continuum flux and the disk mass (cite: Hildebrand1983): $$\begin{align}
M = \frac{D^2 F_{\nu}}{\kappa_{\nu}B_{\nu}(T_{\mathrm{dust}})},
\end{align}$$ with $D$ the distance to V883 Ori, $F_{\nu}$ the observed continuum flux, $\kappa_{\nu}$ the opacity and $B_{\nu}(T_{\mathrm{dust}})$ the Planck function for a dust temperature $T_{\mathrm{dust}}$. As V883 Ori is an outbursting source, a dust temperature of 50 K is assumed. Following (cite: Tychoniec2020), a dust opacity of 0.28 cm$^2$g$^{-1}$ at a wavelength of 9.1 mm is used (cite: Woitke2016). This gives an estimated disk mass of 0.25 M$_{\odot}$.

The snowline has been estimated at 42 AU from dust (cite: Cieza2016), but can be as far out as 100 AU based on CH$_3$OH (cite: vantHoff2018methanol). Moreover, the outburst likely began before 1888 (cite: Pickering1890). Approximately 25 years ago the luminosity was measured to be $\sim$200 L$_{\odot}$ higher than the current luminosity (cite: Strom1993; Sandell2001; Furlan2016) and it could have been much higher in the past. With a freeze-out time scale of 100-1000 yrs, the snowline may thus not be at the location expected from the current luminosity (cite: Jorgensen2013; Visser2015; Hsieh2019). We therefore use three luminosities of $2\times 10^3$, $6\times 10^3$ and $1.4\times 10^4$ L$_{\odot}$ in our models, which put the snowline at 47, 76, and 119 AU, respectively.

The integrated intensity maps of the $J=3-2$ transition of HCO$^+$ for these models are shown in Fig. [11](#fig:V883Ori_mom0). The corresponding figures for the weaker HCO$^+$ and H$^{13}$CO$^+$ $J=2-1$ transitions are presented in Fig. [14](#fig:V883Ori_mom0HCO+21) and Fig. [15](#fig:V883Ori_mom0HiCO+21). These lines are not expected to be contaminated by emission from complex organic molecules. The results in this section are convolved with a small $0.1\ensuremath{''}$ beam to make predictions for future high resolution observations.

The top row of Fig. [11](#fig:V883Ori_mom0) shows the expected emission for network NW for the three different luminosities. The total HCO$^+$ emission does not depend strongly on the luminosity because the population of the $J=3$ level decreases with luminosity but the increase in the temperature of the emitting region cancels this effect as the HCO$^+$ emission is marginally optically thick. Similar to the models for a disk around a typical Herbig Ae star, the moment 0 maps of network NW show ring shaped emission despite the fact that there is no snowline present in these models. The lack of emission in the center is dominated by absorption by dust. On top of that, the column density of the $J=3$ level of HCO$^+$ decreases in the inner parts of the disk. These two points are difficult to disentangle because the continuum optical depth is frequency and hence $J$-level dependent. However, most importantly, the location of the HCO$^+$ ring does not change as a function of luminosity in network NW.

This is different in the bottom row of Fig. [11](#fig:V883Ori_mom0) where emission associated with network W is shown. The water snowline is indicated with a white ellipse and shifts outwards as the luminosity of the star increases. This is also reflected in the HCO$^+$ emission as the ring of HCO$^+$ shifts outwards together with the water snowline. Therefore, the location of the HCO$^+$ ring can be used to locate the water snowline provided that another molecule is observed to prove that the decrease in the HCO$^+$ flux in the center is not solely due to molecular excitation effects and absorption by dust. The excitation effect needs to be inferred from disk modelling. The effect of the optical depth of the continuum emission can be estimated by observing another molecule, that emits from the same disk region as HCO$^+$ and whose column density does not drop in the inner disk. The most obvious molecule for this purpose is C$^{18}$O. However, the HCO$^+$ $J=3-2$ emission comes from a layer closer to the midplane than the C$^{18}$O $J=2-1$ and $J=3-2$ emission. Therefore, the effect of the dust on the HCO$^+$ emission cannot be fully traced by the $J=2-1$ or $J=3-2$ transition of C$^{18}$O. More rare isotopologues such as C$^{17}$O or $^{13}$C$^{18}$O are more suited for this purpose, as well as other molecules such as complex organics as discussed in Section [4.2](#sec:band6).

The model predictions for the observed flux of the $J=3-2$ transition of HCO$^+$ in V883 Ori are compared with the observed flux in the bottom panel of Fig. [10](#fig:compareHCO+32_models_obs). The model results are convolved to the same spatial resolution as the observations before calculating the deprojected azimuthal average. Even though the beam is too large to resolve the snowline if it is located inside $\sim90$ AU, this figure clearly shows that the observed HCO$^+$ flux drops off steeper in the inner parts than that predicted by the model with a snowline at 47 AU. In addition, the HCO$^+$ ring shifts outwards with increasing snowline location. The observed peak location and gap depth in the center best match with a snowline between 76 and 119 AU.

A central cavity (approx. 1 beam in diameter at $0.35\ensuremath{''} \times 0.27\ensuremath{''}$ resolution corresponding to $\sim$60 AU resolution in radius) was also observed for CO $J=2-1$ and was attributed to the continuum optical depth by (cite: RuizRodriguez2017). However, it is unlikely that the cavity observed in HCO$^+$ is solely due to the continuum as the emission from complex organic molecules peaks inside the HCO$^+$ ring ($0.23\ensuremath{''} \times 0.17\ensuremath{''}$; (cite: Lee2019)). Similarly, the high resolution methanol emission ($0.13\ensuremath{''}\times 0.14\ensuremath{''}$; (cite: vantHoff2018methanol)) and the continuum emission ($0.03\ensuremath{''}$; (cite: Cieza2016)) peak well inside the HCO$^+$ cavity (Fig. [10](#fig:compareHCO+32_models_obs)). Furthermore, the continuum becomes optically thin well within 100 AU in all three of our models (Figs. [10](#fig:compareHCO+32_models_obs) and [11](#fig:V883Ori_mom0)), so the difference between the models is due to different snowline locations. Therefore, our analysis is consistent with a water snowline at $\sim$75-120 AU in V883 Ori and thus suggest that the sudden change in continuum opacity at 42 AU is uncorrelated with the water snowline.

One effect that needs to be taken into account in outbursting sources like V883 Ori is viscous heating. This effect heats the disk midplane, hence the water snowline could be at a larger radius than expected based on radiative heating alone. The $J=3-2$ transition of HCO$^+$ is marginally optically thick in our models. Targeting a low $J$ transition of HCO$^+$ or targeting the optically thin H$^{13}$CO$^+$, will allow to directly trace the midplane. Another effect that could occur due to viscous heating is self-absorption of HCO$^+$ as the surface layers of the disk could have a lower temperature than the viscously heated midplane. This could be resolved by observing multiple transitions of HCO$^+$ as higher $J$ lines are more optically thick and hence trace a layer higher in the disk.

Taken together, our analysis of the observations suggests that HCO$^+$ is tracing the water snowline in V883 Ori and that the snowline is located outside the radius where the change in the continuum opacity is observed. Therefore, V883 Ori is the first example that shows that a change in the dust continuum opacity is not necessarily related to the water snowline, similar to what has been shown for the cases of CO, CO$_2$ and N$_2$ snowlines (cite: Huang2018DSHARPII; Long2018; vanTerwisga2018).

# Conclusions

Chemical imaging with HCO$^+$ is in principle a promising method to image the water snowline as it has been used succesfully in a protostellar envelope (cite: vantHoff2018water). This work examines its application in older protoplanetary disks. The HCO$^+$ abundance is modelled using two chemical networks. The first one, network NW, does not include reactions with water, in contrast to the second one, network W. Predictions for the radial emission profiles of HCO$^+$ and H$^{13}$CO$^+$ are made to examine the validity of HCO$^+$ as a tracer of the water snowline. Moreover, archival observations of V883 Ori are examined and used to put constraints on the water snowline location in V883 Ori and make predictions for future high resolution observations of HCO$^+$ in the disk around this outbursting star.

Based on our models the following conclusions can be drawn:

- The HCO$^+$ abundance jumps two orders of magnitude around the water snowline.

- In addition to the water snowline, the optical depth of the continuum emission and molecular excitation effects for the low $J$-levels contribute significantly to the decrease in the H$^{13}$CO$^+$ and HCO$^+$ flux in the inner parts of the disk and result in ring shaped emission. Therefore the effect of the continuum optical depth needs to be checked observationally and the effects of the molecular excitation and HCO$^+$ abundance need to be modelled in detail. Outbursting sources are the best targets, as the snowline is shifted to larger radii, where the dust optical depth is lower.

- HCO$^+$ and H$^{13}$CO$^+$ are equally good as a tracers of the water snowline but the main isotopologue HCO$^+$ is more readily observable.

- For both HCO$^+$ and H$^{13}$CO$^+$, the $J=2-1$ transition is preferred because it provides the best balance between brightness and effects of the continuum optical depth. Moreover, it is not expected to be blended with emission from complex organic molecules, unlike the $J=3-2$ and $J=4-3$ transitions of H$^{13}$CO$^+$.

- Our analysis of the observations of the HCO$^+$ $J=3-2$ transition and complex organic molecules suggest that HCO$^+$ is tracing the water snowline in V883 Ori. Based on our models, the snowline is located around 100 AU and is not correlated with the opacity change in the continuum emission observed at 42 AU.

Our results thus show that HCO$^+$ and H$^{13}$CO$^+$ can be used to trace the water snowline in warm protoplanetary disks such as those found around luminous stars. Determining the snowline location in these sources is important to understand the process of planet formation and composition.

# Acknowledgements

We thank the referee and the editor for the constructive comments, and Catherine Walsh and Jeong-Eun Lee for useful discussions. Astrochemistry in Leiden is supported by the Netherlands Research School for Astronomy (NOVA). M.L.R.H acknowledges support from a Huygens fellowship from Leiden University, and from the Michigan Society of Fellows. L.T. is supported by NWO grant 614.001.352. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01066.T. and ADS/JAO.ALMA#2018.1.01131.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

106 natexlab

(ref: Adams1978) Adams, N. G., Smith, D., & Grief, D. 1978, International Journal of Mass Spectrometry and Ion Processes, 26, 405

(ref: Agundez2018) Agúndez, M., Roueff, E., Le Petit, F., & Le Bourlot, J. 2018, A&A, 616, A19

(ref: Aikawa2015) Aikawa, Y., Furuya, K., Nomura, H., & Qi, C. 2015, ApJ, 807, 120

(ref: Andrews2020) Andrews, S. M. 2020, arXiv e-prints, arXiv:2001.05007

(ref: Andrews2011) Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42

(ref: Andrews2010) Andrews, S. M., Wilner, D. J., Hughes, A. M., Qi, C., & Dullemond, C. P. 2010, ApJ, 723, 1241

(ref: Anicich1975) Anicich, V. G., Futrell, J. H., Huntress, Wesley T., J., & Kim, J. K. 1975, International Journal of Mass Spectrometry and Ion Processes, 18, 63

(ref: Banzatti2015) Banzatti, A., Pinilla, P., Ricci, L., et al. 2015, ApJL, 815, L15

(ref: Banzatti2017) Banzatti, A., Pontoppidan, K. M., Salyk, C., et al. 2017, ApJ, 834, 152

(ref: Bergin2010) Bergin, E. A., Hogerheijde, M. R., Brinch, C., et al. 2010, A&A, 521, L33

(ref: Bergin1998) Bergin, E. A., Melnick, G. J., & Neufeld, D. A. 1998, ApJ, 499, 777

(ref: Blevins2016) Blevins, S. M., Pontoppidan, K. M., Banzatti, A., et al. 2016, ApJ, 818, 22

(ref: Booth2020) Booth, A. S. & Ilee, J. D. 2020, MNRAS, 493, L108

(ref: Booth2019) Booth, A. S., Walsh, C., Ilee, J. D., et al. 2019, ApJL, 882, L31

(ref: Bosman2018) Bosman, A. D., Tielens, A. G. G. M., & van Dishoeck, E. F. 2018, A&A, 611, A80

(ref: Botschwina1993) Botschwina, P., Horn, M., Flügge, J., & Seeger, S. 1993, J. Chem. Soc., Faraday Trans., 89, 2219

(ref: Bruderer2013) Bruderer, S. 2013, A&A, 559, A46

(ref: Bruderer2009) Bruderer, S., Doty, S. D., & Benz, A. O. 2009, ApJS, 183, 179

(ref: Bruderer2012) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541, A91

(ref: Bryden1999) Bryden, G., Chen, X., Lin, D. N. C., Nelson, R. P., & Papaloizou, J. C. B. 1999, ApJ, 514, 344

(ref: Carney2018) Carney, M. T., Fedele, D., Hogerheijde, M. R., et al. 2018, A&A, 614, A106

(ref: Carr2008) Carr, J. S. & Najita, J. R. 2008, Science, 319, 1504

(ref: Caselli1998) Caselli, P., Walmsley, C. M., Terzieva, R., & Herbst, E. 1998, ApJ, 499, 234

(ref: Cazzoletti2018) Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018, A&A, 609, A93

(ref: Cieza2016) Cieza, L. A., Casassus, S., Tobin, J., et al. 2016, Nature, 535, 258

(ref: DAlessio2006) D’Alessio, P., Calvet, N., Hartmann, L., Franco-Hernández, R., & Servı́n, H. 2006, ApJ, 638, 314

(ref: Dong2018) Dong, R., Liu, S.-y., Eisner, J., et al. 2018, ApJ, 860, 124

(ref: Drazkowska2017) Drążkowska, J. & Alibert, Y. 2017, A&A, 608, A92

(ref: Du2017) Du, F., Bergin, E. A., Hogerheijde, M., et al. 2017, ApJ, 842, 98

(ref: Eistrup2016) Eistrup, C., Walsh, C., & van Dishoeck, E. F. 2016, A&A, 595, A83

(ref: Eistrup2018) Eistrup, C., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 613, A14

(ref: Fedele2017) Fedele, D., Carney, M., Hogerheijde, M. R., et al. 2017, A&A, 600, A72

(ref: Flower1999) Flower, D. R. 1999, MNRAS, 305, 651

(ref: Fraser2001) Fraser, H. J., Collings, M. P., McCoustra, M. R. S., & Williams, D. A. 2001, MNRAS, 327, 1165

(ref: Furlan2016) Furlan, E., Fischer, W. J., Ali, B., et al. 2016, ApJS, 224, 5

(ref: Harsono2015) Harsono, D., Bruderer, S., & van Dishoeck, E. F. 2015, A&A, 582, A41

(ref: Harsono2020) Harsono, D., Persson, M. V., Ramos, A., et al. 2020, A&A, 636, A26

(ref: Hartmann1998) Hartmann, L., Calvet, N., Gullbring, E., & D’Alessio, P. 1998, ApJ, 495, 385

(ref: Hasegawa1992) Hasegawa, T. I., Herbst, E., & Leung, C. M. 1992, ApJS, 82, 167

(ref: Hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: Hogerheijde2011) Hogerheijde, M. R., Bergin, E. A., Brinch, C., et al. 2011, Science, 334, 338

(ref: Hsieh2019) Hsieh, T.-H., Murillo, N. M., Belloche, A., et al. 2019, ApJ, 884, 149

(ref: Huang2018DSHARPII) Huang, J., Andrews, S. M., Dullemond, C. P., et al. 2018, ApJ, 869, L42

(ref: Isella2016) Isella, A., Guidi, G., Testi, L., et al. 2016, Phys. Rev. Lett., 117, 251101

(ref: Jorgensen2013) Jørgensen, J. K., Visser, R., Sakai, N., et al. 2013, ApJ, 779, L22

(ref: Kama2016) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83

(ref: Kama2020) Kama, M., Trapman, L., Fedele, D., et al. 2020, A&A, 634, A88

(ref: Kim1974) Kim, J. K., Theard, L. P., & Huntress, W. T., J. 1974, International Journal of Mass Spectrometry and Ion Processes, 15, 223

(ref: Kimura2020) Kimura, H., Wada, K., Kobayashi, H., et al. 2020, Monthly Notices of the Royal Astronomical Society, staa2467

(ref: Klippenstein2010) Klippenstein, S. J., Georgievskii, Y., & McCall, B. J. 2010, Journal of Physical Chemistry A, 114, 278

(ref: Kounkel2017) Kounkel, M., Hartmann, L., Loinard, L., et al. 2017, ApJ, 834, 142

(ref: Lee2019) Lee, J.-E., Lee, S., Baek, G., et al. 2019, Nature Astronomy, 3, 314

(ref: Lepp1987) Lepp, S., Dalgarno, A., & Sternberg, A. 1987, ApJ, 321, 383

(ref: Long2018) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: LyndenBell1974) Lynden-Bell, D. & Pringle, J. E. 1974, MNRAS, 168, 603

(ref: Mandell2012) Mandell, A. M., Bast, J., van Dishoeck, E. F., et al. 2012, ApJ, 747, 92

(ref: Mathews2013) Mathews, G. S., Klaassen, P. D., Juhász, A., et al. 2013, A&A, 557, A132

(ref: Mathis1977) Mathis, J. S., Rumpl, W., & Nordsieck, K. H. 1977, ApJ, 217, 425

(ref: McCall2004) McCall, B. J., Huneycutt, A. J., Saykally, R. J., et al. 2004, , 70, 052716

(ref: McElroy2013) McElroy, D., Walsh, C., Markwick, A. J., et al. 2013, A&A, 550, A36

(ref: Milam2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: Mitchell1990) Mitchell, J. B. A. 1990, Phys. Rep., 186, 215

(ref: Notsu2019) Notsu, S., Akiyama, E., Booth, A., et al. 2019, ApJ, 875, 96

(ref: Novotny2010) Novotný, O., Buhr, H., Stützel, J., et al. 2010, Journal of Physical Chemistry A, 114, 4870

(ref: Oberg2011) Öberg, K. I., Murray-Clay, R., & Bergin, E. A. 2011, ApJ, 743, L16

(ref: Okuzumi2016) Okuzumi, S., Momose, M., Sirono, S.-i., Kobayashi, H., & Tanaka, H. 2016, ApJ, 821, 82

(ref: Phillips1992) Phillips, T. G., van Dishoeck, E. F., & Keene, J. 1992, ApJ, 399, 533

(ref: Pickering1890) Pickering, E. C. 1890, Annals of Harvard College Observatory, 18, 1

(ref: Pickett1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: Pinilla2017) Pinilla, P., Pohl, A., Stammler, S. M., & Birnstiel, T. 2017, ApJ, 845, 68

(ref: Qi2015) Qi, C., Öberg, K. I., Andrews, S. M., et al. 2015, ApJ, 813, 128

(ref: Qi2019) Qi, C., Öberg, K. I., Espaillat, C. C., et al. 2019, ApJ, 882, 160

(ref: Qi2013) Qi, C., Öberg, K. I., Wilner, D. J., et al. 2013, Science, 341, 630

(ref: RuizRodriguez2017) Ruı́z-Rodrı́guez, D., Cieza, L. A., Williams, J. P., et al. 2017, MNRAS, 468, 3266

(ref: Salinas2016) Salinas, V. N., Hogerheijde, M. R., Bergin, E. A., et al. 2016, A&A, 591, A122

(ref: Salyk2019) Salyk, C., Lacy, J., Richter, M., et al. 2019, ApJ, 874, 24

(ref: Salyk2008) Salyk, C., Pontoppidan, K. M., Blake, G. A., et al. 2008, ApJL, 676, L49

(ref: Sandell2001) Sandell, G. & Weintraub, D. A. 2001, ApJS, 134, 115

(ref: Schoier2005) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: Schoonenberg2017) Schoonenberg, D. & Ormel, C. W. 2017, A&A, 602, A21

(ref: Stevenson1988) Stevenson, D. J. & Lunine, J. I. 1988, Icarus, 75, 146

(ref: Strom1993) Strom, K. M. & Strom, S. E. 1993, ApJ, 412, L63

(ref: Teague2016) Teague, R., Guilloteau, S., Semenov, D., et al. 2016, A&A, 592, A49

(ref: Teague2015) Teague, R., Semenov, D., Guilloteau, S., et al. 2015, A&A, 574, A137

(ref: Theard1974) Theard, L. P. & Huntress, W. T. 1974, , 60, 2840

(ref: Tobin2020) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130

(ref: Tychoniec2020) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19

(ref: vanderMarel2015) van der Marel, N., van Dishoeck, E. F., Bruderer, S., Pérez, L., & Isella, A. 2015, A&A, 579, A106

(ref: vanGelder2020) van Gelder, M. L., Tabone, B., Tychoniec, Ł., et al. 2020, A&A, 639, A87

(ref: vantHoff2018water) van ’t Hoff, M. L. R., Persson, M. V., Harsono, D., et al. 2018a, A&A, 613, A29

(ref: vantHoff2018methanol) van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018b, ApJ, 864, L23

(ref: vantHoff2017) van ’t Hoff, M. L. R., Walsh, C., Kama, M., Facchini, S., & van Dishoeck, E. F. 2017, A&A, 599, A101

(ref: vanTerwisga2018) van Terwisga, S. E., van Dishoeck, E. F., Ansdell, M., et al. 2018, A&A, 616, A88

(ref: vanZadelhoff2003) van Zadelhoff, G. J., Aikawa, Y., Hogerheijde, M. R., & van Dishoeck, E. F. 2003, A&A, 397, 789

(ref: Visser2012) Visser, R. & Bergin, E. A. 2012, ApJL, 754, L18

(ref: Visser2015) Visser, R., Bergin, E. A., & Jørgensen, J. K. 2015, A&A, 577, A102

(ref: Vorobyov2013) Vorobyov, E. I., Baraffe, I., Harries, T., & Chabrier, G. 2013, A&A, 557, A35

(ref: Walsh2013) Walsh, C., Millar, T. J., & Nomura, H. 2013, ApJL, 766, L23

(ref: Walsh2012) Walsh, C., Nomura, H., Millar, T. J., & Aikawa, Y. 2012, ApJ, 747, 114

(ref: Williams1998) Williams, J. P., Bergin, E. A., Caselli, P., Myers, P. C., & Plume, R. 1998, ApJ, 503, 689

(ref: Woitke2016) Woitke, P., Min, M., Pinte, C., et al. 2016, A&A, 586, A103

(ref: Yen2016) Yen, H.-W., Koch, P. M., Liu, H. B., et al. 2016, ApJ, 832, 204

(ref: Yen2018) Yen, H.-W., Koch, P. M., Manara, C. F., Miotello, A., & Testi, L. 2018, A&A, 616, A100

(ref: Zhang2015) Zhang, K., Blake, G. A., & Bergin, E. A. 2015, ApJL, 806, L7

(ref: Zhang2013) Zhang, K., Pontoppidan, K. M., Salyk, C., & Blake, G. A. 2013, ApJ, 766, 82

(ref: Zhu2014) Zhu, Z., Stone, J. M., Rafikov, R. R., & Bai, X.-n. 2014, ApJ, 785, 122

# Freeze-out and desorption coefficients

The reaction coefficients of the freeze-out and desorption of water depend on the local conditions in the disk. The rate coefficient of the freeze-out of water, $k_{\mathrm{f}}$ can be expressed as: $$\begin{align}
k_{\mathrm{f}} &= \langle v \rangle \pi a_{\mathrm{grain}}^2 n(\mathrm{grain}) S \\
& = \sqrt{\frac{k_{\mathrm{B}}T_{\mathrm{gas}}}{m}} \pi a_{\mathrm{grain}}^2 n(\mathrm{grain}) S,
\end{align}$$ where $\langle v \rangle = \sqrt{k_{\mathrm{B}}T_{\mathrm{gas}}/m}$ is the thermal velocity of gas-phase water molecules with mass $m$ in a gas at temperature $T_{\mathrm{gas}}$, and $k_{\mathrm{B}}$ is the Boltzmann constant. The `DALI` models use a distribution of grain sizes, but for the chemistry, only the surface area of the grains matters. Therefore a grain size of $a_{\mathrm{grain}} = 0.1~\mu$m and a number density, $n(\mathrm{grain}) = 10^{-12}\times n(\mathrm{H_2})$ with respect to molecule hydrogen is used. Finally a sticking coefficient, $S$, of 1 is assumed.

The reverse process, the desorption of water ice, is described by the desorption rate coefficient: $$\begin{align}
k_{\mathrm{d}} &= \nu_0 e^{-E_{\mathrm{b}}/k_{\mathrm{B}}T_{\mathrm{dust}}} \\
&= \sqrt{\frac{2n_{\mathrm{s}}E_{\mathrm{b}}}{\pi^2 m}} e^{-E_{\mathrm{b}}/k_{\mathrm{B}}T_{\mathrm{dust}}},
\end{align}$$ with $\nu_0 = \sqrt{2n_{\mathrm{s}}E_{\mathrm{b}}/\pi^2 m}$ the characteristic vibrational frequency of water ice on a grain. Here $n_{\mathrm{s}} = 1.5\times10^{15}$ cm$^{-2}$ is the number density of surface sites where water can bind (cite: Hasegawa1992). The binding energy, $E_{\mathrm{b}}$, assumed in this work is 5775 K, corresponding to an amorphous water ice substrate (cite: Fraser2001).

# Chemical network

## Analytical approximation for network NW

Chemical network NW can be used to derive an analytical expression for the HCO$^+$ abundance because of its simplicity. The time evolution of the HCO$^+$ number density is given by the sum of the formation and destruction rates: $$\begin{align}
    \frac{d n(\mathrm{HCO^+})}{d t} = k_{\mathrm{4}} n(\mathrm{CO})n(\mathrm{H_3^+}) - k_{\mathrm{e^-}}n(\mathrm{HCO^+})n(\mathrm{e^-}),
\end{align}$$ with $k_{\mathrm{4}}$ and $k_{\mathrm{e^-}}$ the reaction rates as listed in Table [\[tab:reactions\]](#tab:reactions). This can be rewritten to $$\begin{align}
    n(\mathrm{HCO^+}) = \sqrt{\frac{k_{\mathrm{4}}}{k_{\mathrm{e^-}}} n(\mathrm{CO})n(\mathrm{H_3^+})} \label{eq:HCOp_ana1}
\end{align}$$ under the assumption of steady state. Furthermore, it is assumed that metallic ions can be neglected as electron donors and that HCO$^+$ is the main electron donor. HCO$^+$ has been found to be the dominant molecular ion protoplanetary disks (cite: Teague2015) and the main charge carrier in starless cores (e.g. (cite: Caselli1998; Williams1998)).

Following the approach of (cite: Lepp1987), the number density of H$_3^+$, which is mainly governed by the ionization, can be found in a similar way. The three reactions that regulate the ionization in the disk: ionization by cosmic rays (reaction $\zeta_{\mathrm{c.r.}}$), the ion-molecule reaction to form H$_3^+$ (reaction $k_{\mathrm{2}}$) and dissociative recombination of H$_3^+$ (reaction $k_{\mathrm{3}}$), see also Table. [\[tab:reactions\]](#tab:reactions). The first two reactions can be approximated as: $$\begin{align}
    \mathrm{H_{2}} + \mathrm{c.r.} \to \mathrm{H_3^+},
\end{align}$$ as the formation of H$_3^+$ is limited by the cosmic ray ionization rate. Assuming CO is the main destroyer of H$_3^+$ and thus neglecting the dissociative recombination of H$_3^+$, the time evolution and steady state abundance of H$_3^+$ can be expressed as: $$\begin{align}
    \frac{d n(\mathrm{H_3^+})}{d t} &= \zeta_{\mathrm{c.r.}} n(\mathrm{H_2}) - k_{\mathrm{4}}n(\mathrm{CO})n(\mathrm{H_3^+})\ \ \ \text{(time-dependent), and} \\
    n(\mathrm{H_3^+}) &= \frac{\zeta_{\mathrm{c.r.}}n(\mathrm{H_2})}{k_{\mathrm{4}}n(\mathrm{CO})}\ \ \ \mathrm{(steady\ state).} \label{eq:H3pana}
\end{align}$$

Combining Eq. [\[eq:HCOp_ana1\]](#eq:HCOp_ana1) and Eq. [\[eq:H3pana\]](#eq:H3pana) gives the analytical approximation of the HCO$^+$ abundance in the disk: $$\begin{align}
x(\mathrm{HCO^+}) = \sqrt{\frac{\zeta_{\mathrm{c.r.}}}{k_{\mathrm{e^-}}n(\mathrm{H_2})}}.
\end{align}$$ The comparison of chemical network NW and W in Section [3.1](#sec:resultschem) and Fig. [3](#fig:HCOpnetworkAD) shows that the HCO$^+$ abundance in network NW is very similar to the HCO$^+$ abundance outside the water snow surface in network W. Therefore, the derived expression for the HCO$^+$ abundance can also be used in this disk region in chemical network W.

## Initial conditions

The effects of the initial conditions on the abundance predicted by chemical network W were discussed in Section [3.1.2](#sec:initial_cond_abu) and expected to be of little importance for HCO$^+$’s ability to trace the water snowline. Here, the effects on the corresponding radial emission profiles of the $J=2-1$ transition of HCO$^+$ and H$^{13}$CO$^+$ are discussed and shown in Fig. [12](#fig:icchemnet).

Previously, it was derived that the column density of HCO$^+$ scales with the square root of the cosmic ray ionization rate (see Eq. [\[eq:xHCOp\]](#eq:xHCOp)). Similarly, the H$^{13}$CO$^+$ emission scales with the square root of the cosmic ray ionization rate because it is optically thin, see Fig. [12](#fig:icchemnet). On the other hand, the HCO$^+$ emission does not scale with the cosmic ray ionization rate as it is optically thick. As the column density of HCO$^+$ decreases, the HCO$^+$ emission becomes less optically thick and approaches the scaling for the column density.

In Section [3.1.2](#sec:initial_cond_abu), it was found that the HCO$^+$ abundance or column density does not depend strongly on the initial abundance of CO or H$_2$O. This is is also seen in the radial emission profiles both for HCO$^+$ and H$^{13}$CO$^+$, because the drop in the HCO$^+$ emission in the center is dominated by the effect of the optical depth of the continuum emission and molecular excitation. A small dependence of the HCO$^+$ emission on the initial abundance of gas-phase water is seen, but the abundance of gas-phase water seems to be low in the outer regions of protoplanetary disks (cite: Bergin2010; Du2017; Notsu2019; Harsono2020). Moreover, the abundance of gas-phase water in the inner disk can be as high as $10^{-2}$ (cite: Bosman2018).

| Model parameter          | Initial value NW | Initial value W | Ref.  |
|:-------------------------|:-----------------|:----------------|:------|
| $\zeta_{\mathrm{c.r.}}$  | $1(-17$)         | $1(-17)$        |       |
| $T_{\mathrm{gas}}$       | `DALI` model     | `DALI` model    |       |
| $T_{\mathrm{dust}}$      | `DALI` model     | `DALI` model    |       |
| $n(\mathrm{H_2})$        | `DALI` model     | `DALI` model    |       |
| $x(\mathrm{H_2^+)}$      | $0$              | $0$             |       |
| $x(\mathrm{H_3^+})$      | $0$              | $0$             |       |
| $x(\mathrm{H})$          | $0$              | $0$             |       |
| $x(\mathrm{e^-})$        | $0$              | $0$             |       |
| $x(\mathrm{CO})$         | $1(-4)$          | $1(-4)$         |       |
| $x(\mathrm{HCO^+})$      | $0$              | $0$             |       |
| $x(\mathrm{H_3O^+})$     | $0$              | $0$             |       |
| $x(\mathrm{H_2O})$       | $0$              | $3.8(-7)$       | \(a\) |
| $x(\mathrm{H_2O (ice)})$ | $0$              | $0$             |       |

: Initial conditions for chemical network NW (no water) and W (water).

**Notes.** $a(b)$ represents $a\times 10^b$. Abundances are defined with respect to molecular hydrogen. References: (a) (cite: McElroy2013).

![](Different_initial_conditions)

# HCO$^+$ and H$^{13}$CO$^+$ $J=1-0$, $J=3-2$ and $J=4-3$ transitions

Radial emission profiles for the $J=1-0$, $J=3-2$ and $J=4-3$ transitions of HCO$^+$ and H$^{13}$CO$^+$ are presented in Fig. [13](#fig:herbigdiffradcuts).

![](Different_lines_dust_opac1e10less)

# V883 Ori

An overview of the model parameters used for the representative `DALI` model for V883 Ori is given in Table [3](#tab:paramsdaliV883). Predictions for the corresponding emission of the $J=2-1$ transition of HCO$^+$ and H$^{13}$CO$^+$ are shown in Fig. [14](#fig:V883Ori_mom0HCO+21) and Fig. [15](#fig:V883Ori_mom0HiCO+21).

| Model parameter | Value | Ref. |
|:---|:---|:---|
|  |  |  |
| *Physical structure* |  |  |
| $R_{\mathrm{subl}}$ | 1 AU |  |
| $R_{\mathrm{c}}$ | 75 AU |  |
| $\Sigma_{\mathrm{c}}$ | 35 g$\ \mathrm{cm^{-2}}$ |  |
| $M_{\mathrm{disk}}$ | $0.25 \ \mathrm{M_{\odot}}$ |  |
| $\gamma$ | 1 |  |
| $h_{\mathrm{c}}$ | 0.1 |  |
| $\psi$ | 0.25 |  |
|  |  |  |
| *Dust properties* |  |  |
| $\chi$ | 0.2 |  |
| $f_{\mathrm{ls}}$ | 0.9 |  |
| $\Delta_{\mathrm{gas/dust}}$ | 100 |  |
|  |  |  |
| *Stellar spectrum*$^{(1)}$ |  |  |
| Type | Outbursting |  |
| $L_{\star + \mathrm{acc}}$ | 2.0(3), 6.0(3), 1.4(4) $\mathrm{L_{\odot}}$ |  |
| $L_{\mathrm{X}}$ | 1.4(30) erg s$^{-1}$ |  |
| $T_{\mathrm{eff}}$ | $1(4)$ K |  |
| $T_{\mathrm{acc}}$ | $1(4)$ K |  |
| $T_{\mathrm{X}}$ | 7(7) K |  |
| $\zeta_{\mathrm{c.r.}}$ | 5(-17) $\mathrm{s^{-1}}$ |  |
|  |  |  |
| *Stellar properties*$^{(2)}$ |  |  |
| $\dot{M}$ | $5(-5) \ \mathrm{M_{\odot}}$ yr$^{-1}$ |  |
| $M_{\star}$ | $1.3 \ \mathrm{M_{\odot}}$ | \(a\) |
| $R_{\star}$ | $5.1 \ \mathrm{R_{\odot}}$ |  |
|  |  |  |
| *Observational geometry* |  |  |
| $i$ | 38$\degree$ | \(a\) |
| P.A. | 32$\degree$ | \(a\) |
| $d$ | 400 pc | \(b\) |

: `DALI` model parameters for the representative model for V883 Ori.

**Notes.** $a(b)$ represents $a\times 10^b$. $^{(1)}$The stellar spectrum is obtained by the sum of the accretion luminosity $L_{\mathrm{acc}}$ and an artificially high stellar luminosity $L_{\star}$ to shift the snowline to 47, 76 and 119 AU. $^{(2)}R_{\star}$ is chosen to obtain an accretion luminosity of $4\times 10^2$ L$_{\odot}$, consistent with (cite: Cieza2016). References: (a) (cite: Cieza2016), (b) (cite: Kounkel2017).

![](Cartoons_HCO+_J=2-1_thick_snowline_v2-1.png)

![](Cartoons_H13CO+_J=2-1_thick_snowline_v2-1.png)

[^1]: The `odeint` function is part of the Scipy package in python and uses the LSODA routine from the ODEPACK library in FORTRAN.

[^2]: The `curve_fit` function is part of the Scipy package in python.

</paper>

Write the methods card for this paper.