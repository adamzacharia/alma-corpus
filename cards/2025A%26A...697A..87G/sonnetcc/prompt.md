# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...697A..87G\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...697A..87G",
 "title": "The H<SUB>2</SUB> angular momentum ─ mass relation of local disc galaxies",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Geesink, Nikki N.",
 "n_authors": 4,
 "arxiv_id": "2503.07715",
 "doi": "10.1051/0004-6361/202453290",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00886.L",
  "2018.1.01651.S"
 ]
}
```

Paper text:
<paper>
# The $\mathrm{H_2}$ angular momentum - mass relation of local disc galaxies

We present an analysis of the molecular specific angular momentum–mass ($j_{\rm H_2}-M_{\rm H_2}$) relation using a sample of 51 nearby disc galaxies from the PHANGS-ALMA survey with deep high-resolution molecular gas rotation curves and surface density profiles. For the very first time, using a statistical sample, we report the discovery of a well-defined $j_{\rm H_2}-M_{\rm H_2}$ relation. We quantify the scaling law by fitting a power law with a Bayesian framework, finding $j_{\rm H_2}\propto M_{\rm H_2}^{0.53}$. This slope closely resembles the well-known stellar $j_{\ast}$–$M_{\ast}$ (Fall) relation, highlighting the dynamical connection between molecular gas and stars. We show that the $j_{\rm H_2}-M_{\rm H_2}$ relation cannot be fully explained by analytic models of disc stability, but instead is well recovered with more complex physics as implemented in the SHARK semi-analytical model. These findings demonstrate the power of our novel $j_{\rm H_2}-M_{\rm H_2}$ relation in testing galaxy evolution theories and in setting new constraints for models and simulations that reproduce a realistic interstellar medium. Additionally, our findings provide a critical benchmark for upcoming high-redshift studies of molecular gas kinematics, offering a local baseline to study the evolution of cold gas dynamics across cosmic time.

# Introduction

Specific angular momentum ($j=J/M$) and mass ($M$) are two of the most fundamental properties describing any physical system, including galaxies (e.g. (cite: white_angular_1984; fall_formation_1980; romanowsky_angular_2012; cimatti_introduction_2019)). Angular momentum in galaxies is thought to be acquired by gravitational tidal torques before virialisation, according to the tidal torque theory (cite: peebles_origin_1969; white_angular_1984). This theory predicts a scaling relation for the specific angular momentum of the dark matter haloes of the form $j_{\rm DM} \propto M_{\rm DM}^{2/3}$ (cite: fall_galaxy_1983; shaya_angular_1984; heavens_tidal_1988). Baryonic matter is expected to be subjected to the same tidal torques as the dark matter haloes since during the linear stage of structure formation the dark matter and primordial gas are still well mixed.

Observationally, (cite: fall_galaxy_1983) first showed that both early- and late-type galaxies follow a scaling law in the stellar angular momentum ($j_\ast$) versus stellar mass ($M_\ast$) plane, called the Fall relation. Even though the normalisation for spiral galaxies is higher than that for early types, both classes follow a relationship of the form $j_{\rm \ast} \propto M^{\alpha}_{\ast}$, with $\mathrm{\alpha \approx 0.6}$. Later studies with more and better data confirmed the results of (cite: fall_galaxy_1983), generally finding a power law with a slope of around 0.5-0.6 (cite: romanowsky_angular_2012; fall_angular_2018; posti_angular_2018; mancera_pina_baryonic_2021), consistent (within the uncertainties) with the expectations from tidal torque theory for the dark matter haloes.

In addition to the stellar component, the angular momentum of the cold gas is also vital for galaxy evolution, but has been studied significantly less. In recent years, the neutral atomic hydrogen (H i) $j_{\rm HI}-M_{\rm HI}$ relation has started to be studied using resolved interferometric observations of late-type massive and dwarf galaxies (cite: cortese_sami_2016; chowdhury_angular_2017; kurapati_angular_2018; mancera_pina_baryonic_2021; mancera_pina_tight_2021). This $j_{\rm HI}-M_{\rm HI}$ relation is found to be significantly steeper than the Fall relation, $j_{\rm HI}\propto M_{\rm HI}$ (cite: kurapati_angular_2018; kurapati_h_2021; mancera_pina_baryonic_2021). In contrast, the picture for the molecular gas (H$_2$) is largely incomplete due to the scarcity of deep and high-resolution CO data. In fact, H$_2$ is often neglected when building the baryonic $j-M$ relation, $j_{\rm bar}\propto M_{\rm bar}^{0.6}$ (e.g. (cite: elson_relation_2017; kurapati_angular_2018; murugeshan_influence_2020; mancera_pina_baryonic_2021)). (cite: obreschkow_fundamental_2014) estimated $j_{\rm H_2}$ for a small sample of 16 nearby galaxies from the THINGS survey (cite: walter_things_2008). However, they did not quantify the shape of the $j_{\rm H_2}-M_{\rm H_2}$ relation, and their measurements show large scatter, which casts doubts on the existence of a relation.

Considering that angular momentum regulates galaxy sizes, morphologies, and gas content (cite: fall_galaxy_1983; mo_formation_1998; romanowsky_angular_2012; pezzulli_accretion_2016; mancera_pina_tight_2021; hardwick_xgass_2022; elson_existence_2024) and that molecular gas is the primary fuel for star formation (cite: kennicutt_star_1998; bigiel_star_2008), lacking a quantification of the $j_{\rm H_2}-M_{\rm H_2}$ relation is a significant gap in our attempts to understand the physical properties of the interstellar medium (ISM) in galaxies through their evolutionary pathways (cite: lilly_gas_2013; lagos_angular_2017; catinella_xgass_2018; tacconi_evolution_2020; saintonge_cold_2022). Moreover, since processes such as gas accretion, feedback, mergers, and dynamical friction can dramatically alter a galaxy’s angular momentum distribution (cite: teklu_connecting_2015; stevens_connecting_2018; sweet_stellar_2020), quantifying the molecular $j-M$ relation can also offer important constraints for testing and refining models and simulations of galaxy evolution.

In addition, characterising the $j_{\rm H_2}-M_{\rm H_2}$ relation at $z=0$ is a crucial benchmark for high-redshift observations. To date, only $j_\ast$ has been studied up to $z \approx 1-2$ (see (cite: marasco_angular_2019; sweet_angular_2019; bouche_muse_2021; espejo_salcedo_multiresolution_2022; mercier_stellar_2023)); there is no consensus on its evolution. The molecular phase is vital in order to study the gas counterpart since H i can only be detected in emission up to $z \lesssim 0.2$ (cite: gogate_budhies_2020; ponomareva_mightee-h_2021). For example, thanks to ALMA, it is now becoming common to trace the molecular gas kinematics and distribution at $z\gtrsim3$ (e.g. (cite: rizzo_dynamically_2020; rizzo_alma-alpaka_2023; rowland_rebels-25_2024)). To benchmark the angular momentum content in those young galaxies and their evolution through time, determining the local $j_{\rm H_2}-M_{\rm H_2}$ is imperative. In this paper, we exploit recent deep high-resolution molecular gas observations of 51 local disc galaxies from the PHANGS–ALMA survey to characterise the $j_{\rm H_2}-M_{\rm H_2}$ relation for the first time.

This paper is organised as follows. Section [2](#sec:galsample) describes our galaxy sample, and Sect. [3](#sec: fitting) outlines the methods for determining the specific angular momentum. Our results are presented in Sect. [4](#sec:jmrela) and Sect. [5](#sectestmodel). Finally, we summarise our conclusions in Sect. [6](#secconclusion). Throughout the text, we adopt a $\Lambda$CDM cosmology with H$_0 = 70~{\rm km~s}^{-1}~{\rm Mpc}^{-1}$, $\Omega_{\rm m} = 0.3$, and $\Omega_{\Lambda} = 0.7$.

# Galaxy sample

Our sample was drawn from the PHANGS-ALMA survey (cite: leroy_dataphangs-alma_2021; leroy_surveyphangs-alma_2021), mapping CO $J = 2 \rightarrow 1$ emission, hereafter CO($2-1$), in 90 nearby ($d \lesssim 20\, \rm Mpc$) star-forming galaxies at $\sim 1^{\prime\prime}$ resolution. As detailed below, in selecting our sample, we included galaxies with available CO rotation curves and surface density profiles derived by the PHANGS-ALMA collaboration.

## Rotation curves

We used the rotation curves derived by (cite: lang_phangs_2020) for the PHANGS-ALMA sample, obtained using the commonly employed tilted-ring model of the observed velocity field (cite: rogstad_aperture-synthesis_1974; bosma_distribution_1978; begeman_hi_1987). (cite: lang_phangs_2020) provided high-resolution (150 pc) rotation curves for 67 galaxies with ordered rotation.

To improve the radial coverage of the kinematics of our galaxy sample, we supplemented the CO rotation curves with literature H i rotation curves when available. H i extends well beyond the optical and CO emission of galaxies, making it an effective tracer for galaxy dynamics at the outer radii; we note that H i and CO are expected to corotate, and this has been corroborated with observations in nearby galaxies (cite: bacchini_volumetric_2020; laudage_neutral_2024). Specifically, we supplemented the CO rotation curves of NGC 2903, NGC 3351, NGC 3521, and NGC 3627, NGC 1365, NGC 3621, NGC 4535, and NGC 4536, with H i rotation velocities (also from tilted-ring models) from (cite: di_teodoro_radial_2021) and (cite: ponomareva_detailed_2016). In addition, we included H i rotation curves for three galaxies without available CO rotation curves, bringing the total sample to 70 galaxies. We obtained the H i rotation curves for NGC 253 from (cite: mancera_pina_impact_2022), NGC 300 from (cite: mancera_pina_baryonic_2021), and NGC 7793 from (cite: bacchini_volumetric_2019). Where needed, we corrected the rotation curve data to match the distance and inclination reported in (cite: lang_phangs_2020) to ensure homogeneity.

## Gas surface densities

We used the molecular gas surface density profiles provided by (cite: sun_molecular_2022) for 66 of our 70 galaxies. The molecular gas surface density profiles ($\Sigma_{\rm H_2}$) were derived from the integrated CO(2-1) line intensity $I_{\rm CO}^{(2-1)}$ via $$\begin{align}
    \frac{\Sigma_{\text{H}_2}}{M_{\odot} \, \text{pc}^{-2}} &= \frac{\alpha_{\text{CO}}^{(1-0)}}{M_{\odot} \, \text{pc}^{-2}} \frac{1}{R_{21}} \frac{I_{\text{CO}}^{(2-1)}}{\text{K km/s}},  
\label{eq:surfdens}
\end{align}$$ where $R_{21} = 0.65$ is the adopted CO(2-1) to CO(1-0) line ratio (cite: den_brok_new_2021; leroy_low-j_2022), and ${\alpha_{\text{CO}}^{(1-0)}}$ is the CO-to-$\rm H_2$ conversion factor, for the CO(1-0) line.

The quantity $\alpha_{\rm CO}^{(1-0)}$ remains challenging to constrain precisely due to its sensitivity to local conditions such as gas density, temperature, and metallicity, which vary significantly across galactic environments (cite: schinnerer_molecular_2024). The database of (cite: sun_molecular_2022) provides four alternative prescriptions for the PHANGS-ALMA sample, considering various factors that impact ${\alpha_{\text{CO}}^{(1-0)}}$.

1.  The fiducial conversion factor used by (cite: sun_molecular_2022), which follows a metallicity-dependent calibration first introduced by (cite: sun_dynamical_2020): $$\begin{align}
    \alpha_{\text{CO, S20}} &= 4.35 \, Z'^{-1.6} \, M_{\odot} \, (\text{K km s}^{-1} \, \text{pc}^2)^{-1}.
    \label{eq:alpha_co_sun}    
    \end{align}$$

2.  The commonly used Galactic average value (see (cite: bolatto_co–h2_2013; sandstrom_co–h_2013)): $$\begin{align}
        \alpha_{\text{CO, MW}}= 4.35 \, M_{\odot}\, \mathrm{(K\,km\,s^{-1}\, pc^{2})}^{-1}~.
    \end{align}$$

3.  A calibration that takes into account both metallicity and line intensity from the numerical work by (cite: narayanan_general_2012): $$\begin{align}
        \frac{\alpha_{\text{CO, N12}}}{M_{\odot} \, \text{pc}^{-2} \, (\text{K km s}^{-1})^{-1}} &= 8.5 \, Z'^{-0.65} \, \min\left[1, \, 1.5 \times \left( \frac{\left\langle I_{\text{CO}(2-1)} \right\rangle}{\text{K km s}^{-1}} \right)^{-0.32} \right]~.
    \label{eq:alpha_co_N12}
    \end{align}$$ Here the dependence on the line intensity follows from the effect of varying gas temperature and velocity dispersion in galaxies.

4.  Following (cite: bolatto_co–h2_2013), a calibration considering a dependence on the molecular cloud surface density and total baryonic surface density: $$\begin{align}
        \frac{\alpha_{\text{CO, B13}}}{M_{\odot} \, \text{pc}^{-2} \, (\text{K km s}^{-1})^{-1}} &= 2.9 \exp \left( \frac{40 \, M_{\odot} \, \text{pc}^{-2}}{Z' \left\langle \Sigma_{\text{mol, pix}} \right\rangle} \right) \left( \frac{\Sigma_{\text{total}}}{100 \, M_{\odot} \, \text{pc}^{-2}} \right)^{-\gamma} \\
        \text{with} \quad \gamma &= 
        \begin{cases} 
          0.5, & \text{if } \Sigma_{\text{total}} > 100 \, M_{\odot} \, \text{pc}^{-2} \\
          0, & \text{otherwise}
        \end{cases}.
    \end{align}$$ Here $\Sigma_{\text{mol, pix}}$ gives the molecular cloud surface density and $\Sigma_{\text{total}}$ the total surface density (see (cite: sun_molecular_2022)).

The difference in $\alpha_{\text{CO}}$ between the different calibrations often differs by more than the typical uncertainties quoted in the above references. To incorporate these different prescriptions to obtain $\alpha_{\text{CO}}$, we adopted the following approach. For each galaxy, at each radius, we combine the available $\alpha_{\text{CO, MW}}$, $\alpha_{\text{CO, S20}}$, $\alpha_{\text{CO, B13}}$, and $\alpha_{\text{CO, N12}}$ to construct a master conversion factor. The master conversion factor is derived by averaging the four prescriptions, and we adopt the standard deviation as uncertainty. The master $\alpha_{\text{CO}}$ is then used in Eq. [\[eq:surfdens\]](#eq:surfdens) to derive our final $\Sigma_{\rm H_2}(R)$ profile, with uncertainties determined through standard error propagation. Combining the calibrations into a master $\alpha_{\text{CO}}$ is a conservative approach that manages to capture realistic uncertainties better; this is demonstrated in the right panel of Fig. [1](#Figprofilefits), where the resulting surface density profiles for the various $\alpha_{\rm CO}^{(1-0)}$ calibrations are shown for IC 5273.\

![](Paeprfig1_test.pdf)

From our 66 galaxies we also excluded NGC 1512, NGC 2566, NGC 2775, NGC 4569, and NGC 4826 since their surface density profiles are too irregular to allow a robust quantification of their angular momentum. Similarly, the rotation curve of NGC 5068 is too compact and shows no signs of flattening, making it unsuitable for our purposes. Considering this, we ended up with a final sample of 60 galaxies, spanning the mass ranges $10^9 \lesssim M_{\ast}/M_{\odot} \lesssim 10^{11}$, $10^8 \lesssim M_{\rm H_2}/M_{\odot} \lesssim 10^{10}$, and $10^{-2} \lesssim M_{\rm H_2}/M_{\ast} \lesssim 10^{-0.75}$. In Table [1](#tablejvals) we present the final sample with their Hubble types, stellar masses, and distances adopted from (cite: leroy_surveyphangs-alma_2021).

# Computing j

In this section we describe how we computed the specific angular momentum for our galaxy sample by exploiting their rotation curves and surface density profiles. For a disc, the specific angular momentum within a radius $R$ is described by $$\begin{equation}
     j(< R) = \frac{J(<R)}{M(<R)} = \frac{2\pi \int_{0}^{R} R'^2 \Sigma(R') V(R') \, dR'}{2\pi \int_{0}^{R} R' \Sigma(R') \, dR'}\,
    \label{eq:specific j},
 
\end{equation}$$ where $V(R)$ is the rotation curve and $\Sigma(R)$ the surface density profile. For a typical disc galaxy, most of the angular momentum can be measured by tracing the kinematics and mass surface density out to $R\geq 2 R_{\rm e}$ (cite: romanowsky_angular_2012; posti_angular_2018; mancera_pina_baryonic_2021), where $\Sigma(R)$ becomes small and $V(R)$ has flattened. Measuring $j$ from insufficiently extended data can lead to its underestimation (see Sect. [3.3](#secconv)). Exploiting the empirical facts that rotation curves are flat at large radii (cite: bosma_distribution_1978; begeman_hi_1987; de_blok_high-resolution_2008; kuzio_de_naray_mass_2008) and gas surface densities decay exponentially (cite: bigiel_star_2008; wang_new_2016), we extrapolate the observed data to capture all $j$. For this, we fit $\Sigma(R)$ and $V(R)$ with functional forms.

## Rotation curve fitting

We considered two models to extrapolate $V(R)$: an arctan function (cite: courteau_optical_1997) and a more flexible multi-parameter function (cite: rix_internal_1997). The functions are given, respectively, by $$\begin{align}
    V_{\text{rot}}(R) &= V_0 \frac{2}{\pi} \arctan(R / r_{\rm t}),
    \label{eq: arctan}
\end{align}$$ $$\begin{align}
V_{\mathrm{rot}}(R) = V_{t} \frac{\left( 1 + \frac{r_{\rm t}}{R} \right)^{\beta}}{\left[ 1 + \left( \frac{r_{\rm t}}{R} \right)^{\xi} \right]^{1/\xi}}.
\label{eq:multi}
\end{align}$$ Here $V_0$ is the asymptotic velocity reached at an infinite radius, and $r_{\rm t}$ is the turnover radius between the rising and the outer flat part of the rotation curve. The $V_{\rm t}$ parameter Eq. [\[eq:multi\]](#eq:multi) is a scale velocity regulating the amplitude of the rotation curve. The two additional parameters, $\xi$ and $\beta$, regulate the rise and flattening of the rotation curve.

For simplicity, we first fitted the rotation curves with the arctan function, finding satisfactory fits for most cases. For five galaxies (NGC 300, NGC 1365, NGC 2903, NGC 3521, and NGC 3627) with complex kinematics the multi-parameter function works better. In practice, we retrieved posterior distributions for the best-fitting parameters using a Markov chain Monte Carlo (MCMC) routine with the Python package `emcee` (cite: foreman-mackey_emcee_2013), assuming flat priors on the fitting parameters. Our models successfully reproduced the observed kinematics, as illustrated in Fig. [1](#Figprofilefits) for one representative galaxy.

## Surface density profile fitting

To fit $\Sigma_{\text{H}_2}(R)$, we considered a polyexponential function, which has been shown to effectively capture the complex behaviour of the gas surface densities in nearby galaxies (cite: bacchini_volumetric_2019; mancera_pina_impact_2022). The polyexponential profile is given by $$\begin{align}
    \Sigma_{\text{H}_2}(R) &= \Sigma_{0} e^{-R/R_{\Sigma}} \left(1 + c_1 R + c_2 R^2 + c_3R^3\right),
\end{align}$$ where $\Sigma_{0}$ is the central surface density; $R_{\Sigma}$ is the scale radius; and $c_1$, $c_2$, and $c_3$ are polynomial coefficients. For some profiles (especially those with sharp peaks or strong declines), one polyexponential profile is not flexible enough to reproduce all the observed surface density features. In those cases, we fit instead a combination (sum) of two polyexponential profiles. Similar to our approach with the rotation curves, we used `emcee` to determine the best-fitting parameters. An example of the fit to a representative $\Sigma_{\text{H}_2}(R)$ profile is shown in Fig. [1](#Figprofilefits).

## Specific angular momentum

We adopted a Monte Carlo approach to compute the specific angular momentum and its uncertainties. Specifically, we generated a distribution of $j_{\rm H_2}$ values by calculating $j_{\rm H_2}$ for 100000 random MCMC realisations of both the rotation curves and surface density profiles fitting parameters. For each realisation, we integrated the angular momentum profiles (i.e. Eq. [\[eq:specific j\]](#eq:specific j)) up to 50 kpc.

Our integration limit exploits the extrapolated profiles described in the previous section and is a choice to ensure that we obtained a converged estimation of $j_{\rm H_2}$. We note that the exact value of the upper limit has no impact on our results since $\Sigma_{\rm H_2}(R) \approx 0$ well before our integration limit. Nevertheless, galaxies for which $j_{\rm H_2}(<R)$ is not sufficiently converged at the limits of the data, typically galaxies without flattening of the rotation curve, will have a larger dependence on the functional forms used in the extrapolation. We define a convergence factor $\mathcal{R}$ to quantify the degree of dependence of our results on our extrapolation, which allows us to avoid over-reliance on the extrapolated data. $\mathcal{R}$ is defined as the ratio of $j_{\rm H_2}(<R)$ evaluated at the extent of the rotation curve data to the extrapolated $j_{\rm H_2}(<R)$ (see e.g. (cite: mancera_pina_baryonic_2021)). We establish a threshold such that galaxies with $\mathcal{R}<0.7$ are excluded from the derivation of the molecular $j - M$ relation (see below). In Appendix [9](#sec: appconvergence), we examine the impact of the minimum required convergence factor on our results, but we emphasise already that our results below are robust against sensible variations of $\mathcal{R_{\rm min}}$. Applying the convergence cutoff results in a final sample of 51 galaxies with converged $j_{\rm H_2}$ profiles. Table [1](#tablejvals) ([2](#tablenonconvjvals)) lists the $j_{\rm H_2}$ and $M_{\rm H_2}$ for our converged (non-converged) galaxies.[^3] These values and their uncertainties (which also account for distance uncertainties as reported in Table [1](#tablejvals)) correspond to the medians and $1\sigma$ uncertainties obtained with our Monte Carlo realisations, as described above.

# The molecular $j-M$ relation

## Shape and dependences

In Fig. [2](#Fig_rela) we show the distribution of our converged sample in the $j_{\rm H_2}-M_{\rm H_2}$ plane. Our analysis reveals a clear relation, with a particularly tight scaling law for $M_{\rm H_2} \gtrsim 10^9\, M_{\odot}$, and with increasing scatter below this mass. We fit the observed distribution with a power law of the form $$\begin{align}
    \log\left( \frac{j_{\rm H_2}}{\text{kpc km s}^{-1}} \right) &= \alpha [\log(M_{\rm H_2} / M_{\odot}) - 9] + \beta~, 
    \label{eq: powerlawfit}
\end{align}$$ where $\alpha$ denotes the slope of the relation and $\beta$ the intercept. We include the orthogonal intrinsic scatter ($\sigma_{\perp}$) following (cite: bacchini_volumetric_2019) and (cite: mancera_pina_baryonic_2021). We find the best-fitting parameters to be $\alpha = 0.53 \pm 0.04$, $\beta = 2.62 \pm 0.02$, with an orthogonal intrinsic scatter $\sigma_{\perp}=0.11 \pm 0.02$. In Fig. [2](#Fig_rela) we also show the best-fitting relation and its intrinsic scatter.[^4] The slope of the molecular relation aligns closely with that of the $j_\ast$-$M_\ast$ relation ($\alpha\approx0.5-0.6$, e.g. (cite: romanowsky_angular_2012; fall_angular_2018; posti_angular_2018; mancera_pina_baryonic_2021), whereas it is less steep than the $j_{\rm HI}-M_{\rm HI}$ relation ($\alpha\approx0.8-1$, (cite: kurapati_h_2021; mancera_pina_baryonic_2021)).\

![](Paper_fig_2_vnew.pdf)

With our best-fitting relation, we examined the $j_{\rm H_2}$ residuals ($\Delta_{j_{\rm H_2}-M_{\rm H_2}} = j_{\rm H_2}-j_{\rm H_{2},fit}$) as a function of various parameters to identify any underlying secondary dependences. The parameters considered include Hubble type, effective radius ($R_{\rm e}$), star formation rate (SFR), stellar mass ($M_{\ast}$), and molecular gas fraction $M_{\rm H_2} / M_\ast$. We obtained the values for Hubble type, $R_{\rm e}$, SFR, and $M_{\ast}$ from (cite: leroy_surveyphangs-alma_2021). First, we note that we find no significant correlation between $j_{\rm H_2}$ and star formation rate (SFR) at fixed $M_{\rm H_2}$. We surmise that this could be due to the narrow range of SFRs in our sample (by selection, the PHANGS-ALMA galaxies lie on the star-forming main sequence) or that the variations in the star formation efficiency of H$_2$ are independent of $j_{\rm H_2}$.

Among all the other parameters, the only significant trend ($p-$value=0.003) observed in our residual analysis is a moderate anti-correlation between $\Delta_{j_{\rm H_2}-M_{\rm H_2}}$ and $M_{\rm H_2}/M_\ast$. This relationship indicates that galaxies with higher $M_{\rm H_2}/M_\ast$ tend to have lower $j_{\rm H_2}$ at a given $M_{\rm H_2}$. Similarly, higher $M_{\rm H_I}/M_\ast$ are associated with lower H i specific angular momentum, while the opposite happens in the $j_\ast-M_\ast$ relation, with galaxies with high $j_\ast$ having a high $M_{\rm H_I}/M_\ast$ at fixed $M_\ast$ (see (cite: mancera_pina_tight_2021)). We find no clear dependence with Hubble type or $R_{\rm e}$ in our $j_{\rm H_2}-M_{\rm H_2}$ relation. While the main focus of this work is on the $H_2$ relation, we also performed preliminary explorations of the $j_{\rm H_2}-M_{\star}$ and its dependences, which we discuss in Appendix [10](#appstellar).

## Comparison with previous works

In Fig. [2](#Fig_rela) we compare our results to the study of (cite: obreschkow_fundamental_2014), who analysed 16 nearby spiral galaxies from the THINGS survey (cite: walter_things_2008). In their case the molecular gas surface densities were obtained from CO(2–1) maps at 11$''$ resolution from the HERACLES survey (cite: leroy_heracles_2009), when available, or from CO(1–0) maps at 7$''$ resolution from the BIMA survey (cite: helfer_bima_2003) otherwise. The data used by (cite: obreschkow_fundamental_2014) was of lower resolution than those exploited in this work; in addition they used a higher line ratio of $I_{\rm CO(2 \to 1)} = 0.8 \, I_{\rm CO(1 \to 0)}$ and they adopted the $\alpha_{\text{CO}}$ of the Milky Way. For the kinematics, the approaches were also somewhat different since (cite: obreschkow_fundamental_2014) derived H i rotation velocities based on a pixel-by-pixel fitting technique (see their Appendix B for details) and assumed co-rotation between H i and $\mathrm{H_2}$. As shown in Fig. [2](#Fig_rela), unlike our results, the sample from (cite: obreschkow_fundamental_2014) exhibits greater scatter, biased towards higher $J_{\rm H_2}$ values, and does not show a clear trend. We find that the overlapping galaxies in our samples differ in the $j_{\rm H_2}-M_{\rm H_2}$ plane; these differences are likely attributable to the different $\alpha_{\text{CO}}$ and line ratios adopted. For these galaxies (NGC 628, NGC 3351, NGC 3521, NGC 3627, and NGC 7793), the mean (median) difference in $j_{\rm H_2}$ is 0.04 (0.13) dex, with a maximum discrepancy of approximately 0.25 dex. Whereas the difference in $j_{\rm H_2}$ is not systematic towards one direction, for all of the overlapping galaxies (except NGC 7793) (cite: obreschkow_fundamental_2014) finds lower $M_{\rm H_2}$ values compared to our values. The mean (median) difference, without taking NGC 7793 into account, is 0.32 (0.28) dex, with a maximum difference of about 0.7 dex. For NGC  7793, (cite: obreschkow_fundamental_2014) find a higher value of $M_{\rm H_2}$; however, this is the only galaxy in their sample for which they infer $M_{\rm H_2}$ from the SFR (see their Sect. 2.2) instead of from the CO maps of (cite: leroy_star_2008).\
Overall, our results show the close similarity between the $j_{\rm H_2}-M_{\rm H_2}$ and $j_{\ast}-M_{\ast}$ relations and highlight the significance of molecular angular momentum as an important regulator of the interstellar medium. Future work with samples that span a larger range of physical properties, such as the upcoming KILOGAS ALMA survey, will shed light on possible dependences and further refine our understanding of the $j_{\rm H_2}$–$M_{\rm H_2}$ relation. Despite this, our current relation can already be used to test theoretical models, and in the next section we provide some first examples.

# Testing theoretical models

Angular momentum measurements (to date only $j_\ast$ and $j_{\rm HI}$) have been used to test and constrain analytic models based on disc stability (e.g. (cite: obreschkow_angular_2016; romeo_massive_2020; romeo_specific_2023)) as well as more elaborated semi-analytical models and hydrodynamical simulations (e.g. (cite: obreja_nihao_2016; stevens_building_2016; lagos_angular_2017; el-badry_gas_2018; zoldan_structural_2018; lagos_quenching_2024)). Our novel work allows us to exploit the molecular $j$-$M$ relation for the first time. In this section we compare our results against the expectations of an analytic stability model and a complex semi-analytic model.

First, we compare our findings to the scaling relation driven by disc instability introduced by (cite: romeo_massive_2020) as $\frac{j_i \hat{\sigma}i}{G M_i} \approx 1$, where $\hat{\sigma}$ is the radial velocity dispersion, properly averaged and rescaled, and $i$ denotes a given mass component. This relation appears to be in good agreement with observations of the H i phase ((cite: mancera_pina_baryonic_2021), but see also (cite: mancera_pina_tight_2021)). For H$_2$, we can rewrite the expression by (cite: romeo_massive_2020) as $$\begin{align}
    j_{\rm H_2} \propto \frac{M_{\rm H_2}}{\hat{\sigma}_{\rm H_2}}~,
\end{align}$$ where $\hat{\sigma}_{\rm H_2} = 0.4\bar{\sigma}_{\rm H_2}$, and $\bar{\sigma}_{\rm H_2}$ is the radial average of the $\mathrm{H_2}$ velocity dispersion (see Eq. 4 and Sect. 2.3 of (cite: romeo_massive_2020)). To match this stability relation to our observed $j_{\rm H_2}$–$M_{\rm H_2}$ relation with a slope $\alpha\approx0.5$, we need the scaling $\sigma \propto M_{\rm H_2}^{0.5}$ (but see also (cite: romeo_lenticulars_2020) for potential second-order dependences ). Instead, for our data, the dependence is much weaker, $\sigma \propto M_{\rm H_2}^{\gamma}$, with $\gamma\approx0.05-0.2$, as shown by the kinematic measurements by (cite: sun_molecular_2022; rizzo_alma-alpaka_2024).

We infer that models purely based on disc stability, although powerful tools with the virtue of being simple enough to be falsifiable and intuitive, appear to only partially capture the $j_{\rm H_2}-M_{\rm H_2}$ relation. We surmise that there could be different reasons for this shortcoming. On the one hand, numerous other factors beyond stability conditions can influence the distribution of angular momentum in galaxies, such as gas accretion, star formation, feedback, mergers, and dynamical friction (e.g. (cite: pezzulli_angular_2017; lagos_angular_2017; stevens_connecting_2018; cimatti_introduction_2019)). In addition, it could be that the limitations in the model arise from its attempt to globalise the Toomre parameter (a local condition at a given radius) into one single average value (see (cite: romeo_massive_2020) for details). Finally, we also note that the (cite: romeo_massive_2020) relation was calibrated with the data from (cite: obreschkow_fundamental_2014), which shows a scattered $j_{\rm H_2}-M_{\rm H_2}$ plane that does not fully conform with our new results.

For the semi-analytic models, we performed a first exploration using SHARK (cite: lagos_quenching_2024). SHARK (v2.0) incorporates a range of physical processes, including halo growth and mergers, gas accretion, chemical enrichment, and stellar and AGN feedback. In addition, SHARK features a direct and independent modelling of $j_\ast$, $j_{\rm HI}$, and $j_{\rm H_2}$. SHARK has demonstrated great consistency with the observed scaling relations, such as those between SFR, $M_\ast$, gas content, specific SFR, and black hole mass, making it a valuable model to compare our findings to.

![](Papersharkfig_masstight.pdf)

To compare our $j_{\rm H_2}-M_{\rm H_2}$ relation with SHARK, we selected only SHARK galaxies with $M_\ast$ within $\pm 3 \sigma$ of our own $M_\ast$ range and $B/T<0.3$, ensuring a focus on disc galaxies in a comparable mass regime. Figure [3](#Fig_shark) presents our comparison, which shows a remarkable agreement between the SHARK predictions and our data within our observed masses and $B/T$ ranges. Overall, the agreement in Fig. [3](#Fig_shark) suggests that the physical processes incorporated in SHARK (see (cite: lagos_shark_2018; lagos_quenching_2024) for details) manage to capture the underlying mechanisms shaping the $j_{\rm H_2}-M_{\rm H_2}$ relation at $z=0$.

We note that at the low- and high-mass regimes SHARK predicts a flattening of the relation.[^5] It will be interesting to test this prediction with larger galaxy samples, even though this will be complicated for the low-mass end, given the low metallicity of low-mass galaxies. Additional future promising research avenues include a dedicated study of different hydrodynamical simulations (which will allow us to test whether the physics implementation of SHARK is unique for reproducing the data) as well as the study of the $j_{\rm H_2}-M_{\rm H_2}$ relation at higher redshifts, for which we now provide a local baseline.

# Conclusions

Exploiting observations from the state-of-the-art PHANGS-ALMA survey, we characterised for the first time the scaling relation between the specific angular momentum of molecular gas ($j_{\rm H_2}$) and molecular gas mass ($M_{\rm H_2}$) for disc galaxies in the local universe. Our analysis reveals a clear power-law correlation in the $j_{\rm H_2}-M_{\rm H_2}$ plane (Fig. [2](#Fig_rela)), which we fit with a power law. The best-fitting relation has a slope of $\alpha = 0.53 \pm 0.04$ and an intercept of $\beta = 2.62 \pm 0.02$, aligning closely in slope with the well-studied stellar $j$-$M$ relation and contrasting with the steeper slope observed for neutral atomic gas (H i).

We compared our findings with the predictions from an analytical model based purely on disc stability, and find that it does not recover the $j_{\rm H_2}-M_{\rm H_2}$ completely. On the other hand, compared with predictions from the SHARK semi-analytical model, we find a better agreement (Fig. [3](#Fig_shark)), which supports the model’s portrayal of molecular gas dynamics in galaxy evolution.

Overall, our work provides a valuable tool for upcoming studies of gas dynamics at earlier cosmic times and places new constraints to be reproduced by galaxy formation models and simulations.

# Acknowledgements

We want to thank Gabriele Pezzulli, Luca Cortese, Alessandro Romeo, Michael Fall, Francesca Rizzo, and Danail Obreschkow for valuable discussions, and Paul van der Werf for reading an earlier version of this work. We also thank the anonymous referee for a constructive report that helped improve the paper. PEMP acknowledges the support from the Dutch Research Council (NWO) through the Veni grant VI.Veni.222.364. We thank the PHANGS collaboration for making their data available. This paper makes use of the following ALMA data: `ADS/JAO.ALMA#2012.1.00650.S`, `ADS/JAO.ALMA#2015.1.00925.S`, `ADS/JAO.ALMA#2015.1.00956.S`, `ADS/JAO.ALMA#2017.1.00886.L`, `ADS/JAO.ALMA#2018.1.01651.S`. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. We have used SIMBAD, NED, and ADS services extensively, as well as the Python packages NumPy (cite: oliphant_python_2007), Matplotlib (cite: hunter_matplotlib_2007), SciPy (cite: virtanen_scipy_2020), and Astropy (cite: astropy_collaboration_astropy_2018), for which we are thankful.

98 natexlab

(ref: accurso_deriving_2017) Accurso, G., Saintonge, A., Catinella, B., et al. 2017, MNRAS, 470, 4750

(ref: astropy_collaboration_astropy_2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, The Astronomical Journal, 156, 123

(ref: bacchini_volumetric_2019) Bacchini, C., Fraternali, F., Iorio, G., & Pezzulli, G. 2019, A&A, 622, A64

(ref: bacchini_volumetric_2020) Bacchini, C., Fraternali, F., Pezzulli, G., & Marasco, A. 2020, A&A, 644, A125

(ref: begeman_hi_1987) Begeman, K. G. 1987, PhD thesis

(ref: bekki_transformation_2011) Bekki, K. & Couch, W. J. 2011, MNRAS, 415, 1783

(ref: bellstedt_sluggs_2017) Bellstedt, S., Forbes, D. A., Foster, C., et al. 2017, MNRAS, 467, 4540

(ref: bigiel_star_2008) Bigiel, F., Leroy, A., Walter, F., et al. 2008, The Astronomical Journal, 136, 2846

(ref: bolatto_co–h2_2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: bosma_distribution_1978) Bosma, A. 1978, PhD thesis

(ref: bouche_muse_2021) Bouché, N. F., Genel, S., Pellissier, A., et al. 2021, A&A, 654, A49

(ref: catinella_xgass_2018) Catinella, B., Saintonge, A., Janowiecki, S., et al. 2018, MNRAS, 476, 875

(ref: chowdhury_angular_2017) Chowdhury, A. & Chengalur, J. N. 2017, MNRAS, 467, 3856

(ref: cimatti_introduction_2019) Cimatti, A., Fraternali, F., & Nipoti, C. 2019, Introduction to galaxy formation and evolution: from primordial gas to present-day galaxies (Cambridge ; New York, NY: Cambridge University Press)

(ref: cortese_sami_2016) Cortese, L., Fogarty, L. M. R., Bekki, K., et al. 2016, MNRAS, 463, 170, publisher: OUP ADS Bibcode: 2016MNRAS.463..170C

(ref: courteau_optical_1997) Courteau, S. 1997, The Astronomical Journal, 114, 2402

(ref: de_blok_high-resolution_2008) de Blok, W. J. G., Walter, F., Brinks, E., et al. 2008, The Astronomical Journal, 136, 2648

(ref: deeley_sami_2020) Deeley, S., Drinkwater, M. J., Sweet, S. M., et al. 2020, MNRAS, 498, 2372

(ref: den_brok_new_2021) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221

(ref: di_teodoro_radial_2021) Di Teodoro, E. M. & Peek, J. E. G. 2021, ApJ, 923, 220

(ref: el-badry_gas_2018) El-Badry, K., Quataert, E., Wetzel, A., et al. 2018, MNRAS, 473, 1930

(ref: elson_existence_2024) Elson, E. 2024, MNRAS, 527, 931

(ref: elson_relation_2017) Elson, E. C. 2017, MNRAS, 472, 4551

(ref: espejo_salcedo_multiresolution_2022) Espejo Salcedo, J. M., Glazebrook, K., Fisher, D. B., et al. 2022, MNRAS, 509, 2318

(ref: falcon-barroso_angular_2015) Falcón-Barroso, J., Lyubenova, M., & van de Ven, G. 2015, in IAU Symposium, Vol. 311, Galaxy Masses as Constraints of Formation Models, ed. M. Cappellari & S. Courteau, 78–81

(ref: fall_galaxy_1983) Fall, S. M. 1983, in IAU Symposium, Vol. 100, Internal Kinematics and Dynamics of Galaxies, ed. E. Athanassoula, 391–398

(ref: fall_formation_1980) Fall, S. M. & Efstathiou, G. 1980, MNRAS, 193, 189

(ref: fall_angular_2018) Fall, S. M. & Romanowsky, A. J. 2018, ApJ, 868, 133

(ref: foreman-mackey_emcee_2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications of the Astronomical Society of the Pacific, 125, 306

(ref: gogate_budhies_2020) Gogate, A. R., Verheijen, M. A. W., Deshev, B. Z., et al. 2020, MNRAS, 496, 3531

(ref: hardwick_xgass_2022) Hardwick, J. A., Cortese, L., Obreschkow, D., & Catinella, B. 2022, MNRAS, 516, 4043

(ref: heavens_tidal_1988) Heavens, A. & Peacock, J. 1988, MNRAS, 232, 339

(ref: helfer_bima_2003) Helfer, T. T., Thornley, M. D., Regan, M. W., et al. 2003, ApJ Supplement Series, 145, 259

(ref: hunter_matplotlib_2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: kennicutt_star_1998) Kennicutt, Jr., R. C. 1998, ARA&A, 36, 189

(ref: kurapati_angular_2018) Kurapati, S., Chengalur, J. N., Pustilnik, S., & Kamphuis, P. 2018, MNRAS, 479, 228

(ref: kurapati_h_2021) Kurapati, S., Chengalur, J. N., & Verheijen, M. A. W. 2021, MNRAS, 507, 565, publisher: OUP ADS Bibcode: 2021MNRAS.507..565K

(ref: kuzio_de_naray_mass_2008) Kuzio de Naray, R., McGaugh, S. S., & de Blok, W. J. G. 2008, ApJ, 676, 920

(ref: lagos_quenching_2024) Lagos, C. d. P., Bravo, M., Tobar, R., et al. 2024, MNRAS, 531, 3551

(ref: lagos_angular_2017) Lagos, C. D. P., Theuns, T., Stevens, A. R. H., et al. 2017, MNRAS, 464, 3850

(ref: lagos_shark_2018) Lagos, C. d. P., Tobar, R. J., Robotham, A. S. G., et al. 2018, MNRAS, 481, 3573, publisher: OUP ADS Bibcode: 2018MNRAS.481.3573L

(ref: lang_phangs_2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: laudage_neutral_2024) Laudage, S., Eibensteiner, C., Bigiel, F., et al. 2024, A&A, 690, A169

(ref: laurikainen_photometric_2010) Laurikainen, E., Salo, H., Buta, R., Knapen, J. H., & Comerón, S. 2010, MNRAS, 405, 1089, publisher: OUP ADS Bibcode: 2010MNRAS.405.1089L

(ref: leroy_dataphangs-alma_2021) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, ApJ Supplement Series, 255, 19

(ref: leroy_low-j_2022) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: leroy_surveyphangs-alma_2021) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJ Supplement Series, 257, 43

(ref: leroy_heracles_2009) Leroy, A. K., Walter, F., Bigiel, F., et al. 2009, The Astronomical Journal, 137, 4670

(ref: leroy_star_2008) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, The Astronomical Journal, 136, 2782

(ref: lilly_gas_2013) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119

(ref: mancera_pina_impact_2022) Mancera Piña, P. E., Fraternali, F., Oosterloo, T., et al. 2022, MNRAS, 514, 3329

(ref: mancera_pina_baryonic_2021) Mancera Piña, P. E., Posti, L., Fraternali, F., Adams, E. A. K., & Oosterloo, T. 2021a, A&A, 647, A76

(ref: mancera_pina_tight_2021) Mancera Piña, P. E., Posti, L., Pezzulli, G., et al. 2021b, A&A, 651, L15

(ref: marasco_angular_2019) Marasco, A., Fraternali, F., Posti, L., et al. 2019, A&A, 621, L6

(ref: mercier_stellar_2023) Mercier, W., Epinat, B., Contini, T., et al. 2023, A&A, 677, A143

(ref: mo_formation_1998) Mo, H. J., Mao, S., & White, S. D. M. 1998, MNRAS, 295, 319

(ref: murugeshan_influence_2020) Murugeshan, C., Kilborn, V., Jarrett, T., et al. 2020, MNRAS, 496, 2516

(ref: narayanan_general_2012) Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, MNRAS, 421, 3127

(ref: obreja_nihao_2016) Obreja, A., Stinson, G. S., Dutton, A. A., et al. 2016, MNRAS, 459, 467

(ref: obreschkow_fundamental_2014) Obreschkow, D. & Glazebrook, K. 2014, ApJ, 784, 26

(ref: obreschkow_angular_2016) Obreschkow, D., Glazebrook, K., Kilborn, V., & Lutz, K. 2016, ApJ, 824, L26

(ref: oliphant_python_2007) Oliphant, T. E. 2007, Computing in Science & Engineering, 9, 10

(ref: peebles_origin_1969) Peebles, P. J. E. 1969, ApJ, 155, 393

(ref: pezzulli_accretion_2016) Pezzulli, G. & Fraternali, F. 2016, MNRAS, 455, 2308

(ref: pezzulli_angular_2017) Pezzulli, G., Fraternali, F., & Binney, J. 2017, MNRAS, 467, 311

(ref: ponomareva_mightee-h_2021) Ponomareva, A. A., Mulaudzi, W., Maddox, N., et al. 2021, MNRAS, 508, 1195

(ref: ponomareva_detailed_2016) Ponomareva, A. A., Verheijen, M. A. W., & Bosma, A. 2016, MNRAS, 463, 4052

(ref: posti_angular_2018) Posti, L., Fraternali, F., Di Teodoro, E. M., & Pezzulli, G. 2018, A&A, 612, L6

(ref: querejeta_formation_2015) Querejeta, M., Eliche-Moral, M. C., Tapia, T., et al. 2015, A&A, 579, L2

(ref: rix_internal_1997) Rix, H.-W., Guhathakurta, P., Colless, M., & Ing, K. 1997, MNRAS, 285, 779

(ref: rizzo_alma-alpaka_2024) Rizzo, F., Bacchini, C., Kohandel, M., et al. 2024, A&A, 689, A273

(ref: rizzo_s0_2018) Rizzo, F., Fraternali, F., & Iorio, G. 2018, MNRAS, 476, 2137

(ref: rizzo_alma-alpaka_2023) Rizzo, F., Roman-Oliveira, F., Fraternali, F., et al. 2023, A&A, 679, A129

(ref: rizzo_dynamically_2020) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: rogstad_aperture-synthesis_1974) Rogstad, D. H., Lockhart, I. A., & Wright, M. C. H. 1974, ApJ, 193, 309

(ref: romanowsky_angular_2012) Romanowsky, A. J. & Fall, S. M. 2012, ApJ Supplement Series, 203, 17

(ref: romeo_massive_2020) Romeo, A. B. 2020, MNRAS, 491, 4843

(ref: romeo_lenticulars_2020) Romeo, A. B., Agertz, O., & Renaud, F. 2020, MNRAS, 499, 5656

(ref: romeo_specific_2023) Romeo, A. B., Agertz, O., & Renaud, F. 2023, MNRAS, 518, 1002

(ref: rowland_rebels-25_2024) Rowland, L. E., Hodge, J., Bouwens, R., et al. 2024, MNRAS

(ref: saintonge_cold_2022) Saintonge, A. & Catinella, B. 2022, ARA&A, 60, 319

(ref: sandstrom_co–h_2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: schinnerer_molecular_2024) Schinnerer, E. & Leroy, A. K. 2024, ARA&A, 62, 369

(ref: shaya_angular_1984) Shaya, E. J. & Tully, R. B. 1984, ApJ, 281, 56

(ref: stevens_building_2016) Stevens, A. R. H., Croton, D. J., & Mutch, S. J. 2016, MNRAS, 461, 859

(ref: stevens_connecting_2018) Stevens, A. R. H., Lagos, C. d. P., Obreschkow, D., & Sinha, M. 2018, MNRAS, 481, 5543

(ref: sun_dynamical_2020) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020, ApJ, 892, 148

(ref: sun_molecular_2022) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43

(ref: sweet_angular_2019) Sweet, S. M., Fisher, D. B., Savorgnan, G., et al. 2019, MNRAS, 485, 5700

(ref: sweet_stellar_2020) Sweet, S. M., Glazebrook, K., Obreschkow, D., et al. 2020, MNRAS, 494, 5421

(ref: tacconi_evolution_2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: teklu_connecting_2015) Teklu, A. F., Remus, R.-S., Dolag, K., et al. 2015, ApJ, 812, 29

(ref: van_den_bergh_lenticular_2009) van den Bergh, S. 2009, ApJ, 702, 1502

(ref: virtanen_scipy_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: walter_things_2008) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, The Astronomical Journal, 136, 2563

(ref: wang_new_2016) Wang, J., Koribalski, B. S., Serra, P., et al. 2016, MNRAS, 460, 2143

(ref: white_angular_1984) White, S. D. M. 1984, ApJ, 286, 38

(ref: zoldan_structural_2018) Zoldan, A., De Lucia, G., Xie, L., Fontanot, F., & Hirschmann, M. 2018, MNRAS, 481, 1376

# Molecular angular momentum catalogue

In Table [1](#tablejvals) we show galaxy properties and our calculated values for $j_{\rm H_2}$, $M_{\rm H_2}$, and $\mathcal{R}$ for our sample of 51 converged galaxies. Additionally, we provide the results for our non-converged sample in Table [2](#tablenonconvjvals), but we note that these results are less reliable. In both tables, Hubble types, distances, and stellar masses are from (cite: leroy_surveyphangs-alma_2021).

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| GAL ID | Hubble type | Distance | $\log(M_{\ast})$ | $\log(j_{\mathrm{H_2}})$ | $\log(M_{\mathrm{H_2}})$ | $\mathcal{R}$ |
|  |  | (Mpc) | ($M_\odot$) | (kpc km s$^{-1}$) | ($M_\odot$) |  |
|  |  |  |  |  |  |  |
| GAL ID | Hubble type | Distance | $\log(M_{\ast})$ | $\log(j_{\mathrm{H_2}})$ | $\log(M_{\mathrm{H_2}})$ | $\mathcal{R}$ |
|  |  | (Mpc) | ($M_\odot$) | (kpc km s$^{-1}$) | ($M_\odot$) |  |
| IC 1954 | Sb | $12.80 \pm 2.17$ | 9.67 | $2.29^{+0.07}_{-0.07}$ | $8.65^{+0.15}_{-0.13}$ | 0.98 |
| IC 5273 | SBc | $14.18 \pm 2.14$ | 9.73 | $2.48^{+0.10}_{-0.39}$ | $8.57^{+0.14}_{-0.36}$ | 0.88 |
| NGC 253 | SABc | $3.70 \pm 0.12$ | 10.64 | $2.77^{+0.06}_{-0.36}$ | $9.53^{+0.10}_{-0.29}$ | 1.00 |
| NGC 300 | Scd | $2.09 \pm 0.09$ | 9.27 | $2.05^{+0.05}_{-0.04}$ | $7.67^{+0.06}_{-0.05}$ | 1.00 |
| NGC 628 | Sc | $9.84 \pm 0.63$ | 10.34 | $2.84^{+0.07}_{-0.05}$ | $9.41^{+0.08}_{-0.07}$ | 0.79 |
| NGC 1087 | Sc | $15.85 \pm 2.22$ | 9.94 | $2.51^{+0.06}_{-0.06}$ | $8.99^{+0.12}_{-0.11}$ | 0.92 |
| NGC 1097 | Sbb | $13.58 \pm 2.05$ | 10.76 | $3.04^{+0.06}_{-0.13}$ | $9.62^{+0.11}_{-0.10}$ | 0.85 |
| NGC 1300 | Sbc | $18.99 \pm 2.86$ | 10.62 | $3.09^{+0.08}_{-0.07}$ | $9.23^{+0.14}_{-0.11}$ | 0.74 |
| NGC 1317 | SABa | $19.11 \pm 0.85$ | 10.62 | $2.12^{+0.06}_{-0.06}$ | $8.78^{+0.08}_{-0.07}$ | 0.98 |
| NGC 1365 | Sb | $19.57 \pm 0.78$ | 11.00 | $3.17^{+0.04}_{-0.23}$ | $10.14^{+0.05}_{-0.18}$ | 1.00 |
| NGC 1385 | Sc | $17.22 \pm 2.60$ | 9.98 | $2.47^{+0.06}_{-0.06}$ | $9.11^{+0.13}_{-0.11}$ | 1.00 |
| NGC 1511 | Sab | $15.28 \pm 2.26$ | 9.92 | $2.60^{+0.06}_{-0.06}$ | $9.07^{+0.13}_{-0.12}$ | 0.77 |
| NGC 1546 | S0-a | $17.69 \pm 2.02$ | 10.37 | $2.49^{+0.05}_{-0.05}$ | $9.23^{+0.10}_{-0.09}$ | 0.95 |
| NGC 1559 | SBc | $19.44 \pm 0.45$ | 10.37 | $2.84^{+0.01}_{-0.01}$ | $9.54^{+0.02}_{-0.02}$ | 0.72 |
| NGC 1566 | SABb | $17.69 \pm 2.02$ | 10.79 | $3.00^{+0.05}_{-0.04}$ | $9.69^{+0.10}_{-0.08}$ | 0.93 |
| NGC 1792 | Sbc | $16.20 \pm 2.44$ | 10.62 | $2.83^{+0.06}_{-0.06}$ | $9.76^{+0.14}_{-0.12}$ | 0.89 |
| NGC 2090 | Sbc | $11.75 \pm 0.84$ | 10.04 | $2.42^{+0.03}_{-0.03}$ | $8.47^{+0.09}_{-0.08}$ | 0.97 |
| NGC 2283 | Sc | $13.68 \pm 2.06$ | 9.89 | $2.44^{+0.07}_{-0.07}$ | $8.55^{+0.14}_{-0.12}$ | 0.71 |
| NGC 2835 | Sc | $12.22 \pm 0.93$ | 10.0 | $2.42^{+0.06}_{-0.06}$ | $8.42^{0.12}_{-0.11}$ | 0.79 |
| NGC 2903 | Sbc | $10.00 \pm 1.99$ | 10.64 | $3.04^{+0.08}_{-0.08}$ | $9.53^{+0.17}_{-0.15}$ | 1.00 |
| NGC 2997 | SABc | $14.06 \pm 2.80$ | 10.73 | $3.16^{+0.09}_{-0.10}$ | $9.80^{+0.19}_{-0.17}$ | 0.72 |
| NGC 3059 | SBbc | $20.23 \pm 4.04$ | 10.38 | $2.65^{+0.08}_{-0.08}$ | $9.36^{+0.18}_{-0.15}$ | 0.81 |
| NGC 3137 | SABc | $16.37 \pm 2.34$ | 9.88 | $2.48^{+0.07}_{-0.06}$ | $8.45^{+0.13}_{-0.11}$ | 0.88 |
| NGC 3351 | Sb | $9.96 \pm 0.33$ | 10.37 | $2.88^{+0.04}_{-0.04}$ | $9.03^{+0.06}_{-0.04}$ | 1.00 |
| NGC 3507 | Sbb | $23.55 \pm 3.99$ | 10.40 | $2.93^{+0.08}_{-0.06}$ | $9.17^{+0.15}_{-0.13}$ | 0.73 |
| NGC 3511 | SABc | $13.94 \pm 2.10$ | 10.03 | $2.70^{+0.06}_{-0.06}$ | $8.99^{+0.13}_{-0.11}$ | 0.77 |
| NGC 3521 | SABb | $13.24 \pm 1.96$ | 11.003 | $3.12^{+0.06}_{-0.06}$ | $9.75^{+0.13}_{-0.11}$ | 1.00 |
| NGC 3596 | SABc | $11.30 \pm 1.03$ | 9.66 | $2.32^{+0.07}_{-0.06}$ | $8.61^{+0.12}_{-0.10}$ | 0.91 |
| NGC 3621 | SBcd | $7.06 \pm 0.28$ | 10.06 | $2.68^{+0.06}_{-0.05}$ | $9.06^{+0.06}_{-0.06}$ | 1.00 |
| NGC 3626 | S0-a | $20.05 \pm 2.34$ | 10.46 | $2.28^{+0.05}_{-0.05}$ | $8.35^{+0.14}_{-0.11}$ | 0.98 |
| NGC 3627 | S0-a | $11.32 \pm 0.48$ | 10.84 | $3.02^{+0.05}_{-0.06}$ | $9.78^{+0.13}_{-0.11}$ | 0.98 |
| NGC 4254 | Sc | $13.10 \pm 2.01$ | 10.42 | $2.90^{+0.07}_{-0.06}$ | $9.80^{+0.13}_{-0.12}$ | 0.97 |
| NGC 4293 | S0-a | $15.76 \pm 2.38$ | 10.52 | $2.21^{+0.08}_{-0.08}$ | $8.63^{+0.15}_{-0.13}$ | 0.79 |
| NGC 4298 | Sc | $14.92 \pm 1.36$ | 10.04 | $2.55^{+0.05}_{-0.04}$ | $9.10^{+0.09}_{-0.08}$ | 0.96 |
| NGC 4303 | Sbc | $16.99 \pm 3.02$ | 10.51 | $2.91^{+0.07}_{-0.08}$ | $9.78^{+0.16}_{-0.15}$ | 0.81 |
| NGC 4457 | S0-a | $15.10 \pm 2.00$ | 10.42 | $2.41^{+0.08}_{-0.07}$ | $8.82^{+0.16}_{-0.13}$ | 0.72 |
| NGC 4496A | Scd | $14.86 \pm 1.06$ | 9.55 | $2.28^{+0.08}_{-0.09}$ | $8.38^{+0.11}_{-0.11}$ | 0.71 |
| NGC 4535 | Sc | $15.77 \pm 0.37$ | 10.54 | $3.06^{+0.04}_{-0.04}$ | $9.44^{+0.06}_{-0.05}$ | 0.98 |
| NGC 4536 | SABb | $16.25 \pm 1.12$ | 10.40 | $2.82^{+0.08}_{-0.07}$ | $9.33^{+0.10}_{-0.08}$ | 0.99 |
| NGC 4540 | SABc | $15.76 \pm 2.38$ | 9.79 | $2.23^{+0.08}_{-0.07}$ | $8.50^{+0.15}_{-0.12}$ | 0.89 |
| NGC 4689 | Sc | $15.00 \pm 2.26$ | 10.24 | $2.50^{+0.07}_{-0.06}$ | $9.04^{+0.14}_{-0.11}$ | 0.92 |
| NGC 4781 | Scd | $11.31 \pm 1.18$ | 9.54 | $2.34^{+0.06}_{-0.06}$ | $8.69^{+0.12}_{-0.10}$ | 0.99 |
| NGC 4941 | SABa | $15.00 \pm 5.00$ | 10.18 | $2.55^{+0.19}_{-0.12}$ | $8.37^{+0.41}_{-0.12}$ | 0.99 |
| NGC 4951 | SABc | $15.00 \pm 4.19$ | 9.79 | $2.36^{+0.12}_{-0.11}$ | $8.40^{+0.25}_{-0.20}$ | 0.94 |
| NGC 5042 | SABc | $16.78 \pm 2.53$ | 9.90 | $2.53^{+0.08}_{-0.07}$ | $8.52^{+0.15}_{-0.12}$ | 0.79 |
| NGC 5134 | SABb | $19.92 \pm 2.69$ | 10.41 | $2.58^{+0.08}_{-0.07}$ | $8.76^{+0.13}_{-0.11}$ | 0.80 |
| NGC 5248 | SABb | $14.87 \pm 1.32$ | 10.41 | $2.83^{+0.05}_{-0.05}$ | $9.50^{+0.08}_{-0.08}$ | 0.72 |
| NGC 5530 | SABb | $12.27 \pm 1.85$ | 10.08 | $2.52^{+0.07}_{-0.06}$ | $8.77^{+0.14}_{-0.12}$ | 0.89 |
| NGC 5643 | Sc | $12.68 \pm 0.54$ | 10.34 | $2.80^{+0.03}_{-0.03}$ | $9.41^{+0.05}_{-0.05}$ | 0.88 |
| NGC 6300 | Sbb | $11.58 \pm 1.75$ | 10.47 | $2.74^{+0.06}_{-0.06}$ | $9.25^{+0.13}_{-0.12}$ | 0.88 |
| NGC 7793 | Scd | $3.62 \pm 0.15$ | 9.36 | $2.22^{+0.07}_{-0.09}$ | $8.18^{+0.11}_{-0.12}$ | 1.00 |
|  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| GAL ID | Hubble Type | Distance | $\log(M_{\ast})$ | $\log(j_{\mathrm{H_2}})$ | $\log(M_{\mathrm{H_2}})$ | $\mathcal{R}$ |
|  |  | (Mpc) | ($M_\odot$) | (kpc km s$^{-1}$) | ($M_\odot$) |  |
|  |  |  |  |  |  |  |
| GAL ID | Hubble Type | Distance | $\log(M_{\ast})$ | $\log(j_{\mathrm{H_2}})$ | $\log(M_{\mathrm{H_2}})$ | $\mathcal{R}$ |
|  |  | (Mpc) | ($M_\odot$) | (kpc km s$^{-1}$) | ($M_\odot$) |  |
| NGC 685 | Sc | $19.94 \pm 3.01$ | 10.07 | $2.77^{+0.08}_{-0.09}$ | $8.74^{+0.11}_{-0.14}$ | 0.68 |
| NGC 1433 | SBa | $18.63 \pm 1.84$ | 10.87 | $3.13^{+0.08}_{-0.10}$ | $9.30^{+0.08}_{-0.10}$ | 0.25 |
| NGC 1809 | Sc | $19.95 \pm 5.63$ | 9.77 | $2.06^{+0.11}_{-0.13}$ | $8.13^{+0.20}_{-0.26}$ | 0.67 |
| NGC 4321 | SABb | $15.21 \pm 0.50$ | 10.75 | $3.21^{+0.05}_{-0.06}$ | $9.96^{+0.06}_{-0.07}$ | 0.53 |
| NGC 4548 | Sb | $16.22 \pm 0.38$ | 10.70 | $3.30^{+0.07}_{-0.11}$ | $9.40^{+0.10}_{-0.18}$ | 0.38 |
| NGC 4571 | Sc | $14.90 \pm 1.07$ | 10.10 | $2.89^{+0.09}_{-0.31}$ | $9.17^{+0.11}_{-0.41}$ | 0.59 |
| NGC 6744 | Sbc | $9.39 \pm 0.42$ | 10.72 | $3.26^{+0.03}_{-0.03}$ | $9.62^{+0.04}_{-0.04}$ | 0.58 |
| NGC 7456 | Sc | $15.70 \pm 2.33$ | 9.65 | $2.50^{+0.08}_{-0.09}$ | $7.98^{+0.09}_{-0.13}$ | 0.44 |
| NGC 7496 | Sb | $18.72 \pm 2.82$ | 10.00 | $2.50^{+0.06}_{-0.07}$ | $9.11^{+0.13}_{-0.14}$ | 0.67 |
|  |  |  |  |  |  |  |

: Continued.

# Including H i rotation curves

To extend the radial coverage of our sample’s kinematics, we supplemented our CO rotation curves with literature H i rotation curves when available (see Sect.[2.1](#sec:rotationcurves)). In Fig.[4](#Fig_HI) we highlight in the $j_{\rm H_2}-M_{\rm H_2}$ plane *(i)* the eight galaxies whose CO rotation curves are complemented by H i velocities (orange), *(ii)* the three galaxies for which only H i data were used (green), and *(iii)* all remaining galaxies that rely solely on CO rotation curves (pink).

We tested how including H i rotation curves could affect the $j_{\rm H_2}-M_{\rm H_2}$ relation by examining the influence of these galaxies on the best-fit parameters (Table [3](#tabRCslopes)). Any resulting changes in the slope lie within the uncertainties of our fiducial relation, confirming the robustness of our approach and indicating that the inclusion of H i rotation curves does not bias our results presented in Sect. [4](#sec:jmrela).

![](Paper_appendixHI.pdf)

| Rotation curves | N galaxies | $\alpha$ | $\beta$ | $\sigma_{\perp}$ |
|:--:|:--:|:--:|:--:|:--:|
| Fiducial | 51 | $0.53^{+0.04}_{-0.04}$ | $2.62^{+0.02}_{-0.02}$ | $0.11^{+0.02}_{-0.02}$ |
| CO & CO+H i | 48 | $0.56^{+0.05}_{-0.05}$ | $2.61^{+0.02}_{-0.02}$ | $0.12^{+0.02}_{-0.02}$ |
| CO & H i | 43 | $0.49^{+0.05}_{-0.05}$ | $2.60^{+0.02}_{-0.02}$ | $0.11^{+0.02}_{-0.02}$ |
| CO | 40 | $0.52^{+0.06}_{-0.05}$ | $2.60^{+0.02}_{-0.02}$ | $0.11^{+0.02}_{-0.02}$ |

: Impact of rotation curves on the best-fit parameters to the $j_{\rm H_2}-M_{\rm H_2}$ relation.

# Convergence criteria

We obtain the molecular $j-M$ relation by imposing a convergence limit $\mathcal{R} > 0.7$, as detailed in Sec. [3.3](#secconv). This appendix explores how robust our findings are against our $\mathcal{R}$ threshold choice.

Figure [5](#Fig_conv) shows the total sample of 60 galaxies in the $j_{\rm H_2}-M_{\rm H_2}$ plane with $\mathcal{R}$ indicated by the colour of the markers, the values of the non-converged galaxies are provided in Table [2](#tablenonconvjvals). To test the impact of our $\mathcal{R}$ threshold, we repeat our fitting procedure but include the galaxies satisfying $\mathcal{R}>0.2$ (in which our full sample is comprised) and the more restrictive $\mathcal{R}>0.9$. The figure shows the resulting best-fit relations, and the fitting parameters are provided in Table [4](#tabslopes). Typically, the galaxies with the lowest $\mathcal{R}$ lie above the fiducial relation, which may be counterintuitive, but it is likely the result of the functional forms overestimating the velocity at which the rotation curve flattens.

As can be seen from Fig. [2](#Fig_rela) and Table [4](#tabslopes), all the fitting parameters remain consistent within their uncertainties regardless of the specific convergence criterion employed. Even though the sample size decreases as we impose stricter convergence limits, we still recover slopes and intercepts that are statistically consistent. This all demonstrates the robustness of our approach and results.

![](Paperfig3.pdf)

| $\mathcal{R_{\rm min}}$ | N galaxies | $\alpha$ | $\beta$ | $\sigma_{\perp}$ |
|:--:|:--:|:--:|:--:|:--:|
| $0.2$ | 60 | $0.55^{+0.05}_{-0.05}$ | $2.65^{+0.02}_{-0.02}$ | $0.14^{+0.02}_{-0.02}$ |
| $0.7$ | 51 | $0.53^{+0.04}_{-0.04}$ | $2.62^{+0.02}_{-0.02}$ | $0.11^{+0.02}_{-0.02}$ |
| $0.8$ | 37 | $0.52^{+0.05}_{-0.05}$ | $2.60^{+0.03}_{-0.03}$ | $0.12^{+0.02}_{-0.02}$ |
| $0.9$ | 26 | $0.54^{+0.06}_{-0.06}$ | $2.60^{+0.03}_{-0.04}$ | $0.14^{+0.03}_{-0.02}$ |

: Best-fit parameters to the $j_{\rm H_2}-M_{\rm H_2}$ relation, varying the minimum required $\mathcal{R}$.

# The $j_{\rm H_2}-M_{\rm \ast}$ relation

Our analysis also allows us to explore the $j_{\rm H_2}$ content at fixed $M_\ast$, the dominant baryonic mass component for all our galaxies. The stellar masses are provided in Table [1](#tablejvals), where we adopt an uncertainty of 0.1 dex (cite: leroy_surveyphangs-alma_2021). As shown in Fig. [6](#Figappendixb), except for a few outliers, most of our converged sample follows a clear trend in the $j_{\rm H_2}-M_{\rm \ast}$ plane, which we parametrise with the relation $$\begin{align}
\log\left( \frac{j_{\rm H_2}}{\text{kpc km s}^{-1}} \right) &= \alpha \left[ \log\left( \frac{M_{\ast}}{M_{\odot}} \right) - 10 \right] + \beta~.
\label{eq: powerlawfitstar}
\end{align}$$ This expression differs from Eq. [\[eq: powerlawfit\]](#eq: powerlawfit) only in the mass shift (which affects the normalisation $\beta$). The best-fitting parameters are $\alpha = 0.66 \pm 0.08$, $\beta = 2.48 \pm 0.03$, with an orthogonal intrinsic scatter $\sigma_{\perp}=0.16 \pm 0.02$. We have checked that our fit is not significantly affected by the presence of the four outliers (see below): excluding these four galaxies does not affect the slope of either the $j_{\rm H_2}$–$M_{\rm H_2}$ or the $j_{\rm H_2}$–$M_\ast$ relations, indicating that our results are robust.

As for the $j_{\rm H_2}-M_{\rm H_2}$ relation, we look for second dependences in the $j_{\rm H_2}-M_{\ast}$ plane. In contrast with the $j_{\rm H_2}-M_{\rm H_2}$ relation (where we find an anti-correlation), we find a strong positive correlation with $M_{\rm H_2}/M_\ast$ ($p$-value = 0.00005). Furthermore, we find a significant ($p$-value = 0.0004) correlation with $\log(R_{\rm e})$, indicating that galaxies with more extended light distribution tend to have higher $j_{\rm H_2}$, as also observed for $j_\ast$ (cite: mancera_pina_baryonic_2021). We show the dependences on $\log(R_{\rm e})$ and $M_{\rm H_2}/M_\ast$, in the top and lower-middle panel of Fig. [6](#Figappendixb).

Additionally, we compute $R_{\rm e, H_2}$, the radius within which half of the molecular gas is contained. This quantity, analogous to the stellar effective radius $R_{\rm e}$, is derived from integrating the cumulative $\Sigma_{\rm H_2}$ profiles. Similar to $R_{\rm e}$, we find a robust positive correlation between $j_{\rm H_2}$ and $\log(R_{\rm e, H_2})$ with a $p$-value of $2 \times 10^{-9}$. This molecular size dependence is seen across our mass regime, but it is particularly evident at $\log(M_{\ast}/M_\odot)\approx10.5$, where we observe a tail of outliers exhibiting significantly lower $R_{\rm e, H_2}$ and $j_{\rm H_2}$, indicating that their molecular gas is significantly less extended that for the other galaxies[^6]. The tail is formed by the galaxies NGC 1317, NGC 3626, NGC 4293, and NGC 4457.

Upon inspection, we find that in addition to their very low $R_{\rm e, H_2}$, these galaxies show significantly lower molecular gas fractions, as illustrated in the lower-middle panel of Fig. [6](#Figappendixb). We also notice that none of these galaxies is a normal spiral; instead, they are classified as lenticulars (S0) or intermediate spirals (SABa) based on their morphology (bottom panel of Fig. [6](#Figappendixb), Hubble types are provided in Table [1](#tablejvals)). This was not necessarily expected, as the discs of lenticular galaxies (and we have checked this is the case for our sample) are found to lie on the same $j_\ast-M_\ast$ relation for spirals, as shown by (cite: rizzo_s0_2018; mancera_pina_baryonic_2021), see also discussion in (cite: romanowsky_angular_2012).

The combination of normal $j_\ast$ but low $j_{\rm H_2}$, $R_{\rm e, H_2}$, and $M_{\rm H_2}/M_\ast$, seen primarily for lenticular or intermediate spirals, is likely related to their formation mechanism, which remains a topic of active study (cite: deeley_sami_2020). These mechanisms include passive evolution, where cold gas is gradually consumed by star formation (cite: van_den_bergh_lenticular_2009; laurikainen_photometric_2010; bellstedt_sluggs_2017), or more violent processes such as mergers and tidal interactions that rapidly strip or deplete the gas (cite: bekki_transformation_2011; falcon-barroso_angular_2015; querejeta_formation_2015). Whatever the exact formation channel at play, our results suggest that lenticular galaxies, for example spirals, self-regulate to lie on the $j_\ast-M_\ast$ and $j_{\rm H_2}-M_{\rm H_2}$ relations (see also (cite: mancera_pina_tight_2021)) but have gone through a process that altered mostly their gas disc, preferentially removing gas from the outer, high-$j_{\rm H_2}$ regions. As a result, $j_{\rm H_2}$ and $M_{\rm H_2}$ are significantly reduced, while the dominant stellar components remain largely unaffected. These observations suggest a variety of formation paths for lenticulars, or at least diverse evolutionary paths for their molecular gas reservoirs, which may explain the large observed range of $j_{\rm H_2}$ at fixed $M_{\ast}$ for this galaxy type. This highlights the importance of angular momentum studies in understanding the diversity in galaxy morphology observed in the Universe. However, considering that our sample is predominantly composed of galaxies with minimal bulge components, a more representative sample, including a greater number of lenticular galaxies, would be necessary to draw clearer conclusions.

![](four_panel_figure.pdf)

[^1]:

[^2]:

[^3]: For consistency, $M_{\rm H_2}$ is estimated by integrating the denominator in Eq. [\[eq:specific j\]](#eq:specific j). We find great agreement when comparing our values to the CO luminosities reported in (cite: leroy_surveyphangs-alma_2021), with a median difference of 0.03 dex.

[^4]: The inclusion of H i rotation curves does not bias our results for the best-fitting relation; we verify this explicitly in Appendix [8](#apprc).

[^5]: Some models and simulations suggest a similar flattening or break at the low-mass end of the $j_{\star}-M_{\star}$ relation (cite: obreja_nihao_2016; stevens_building_2016), although it has not been seen in observations (cite: mancera_pina_baryonic_2021)

[^6]: The outliers are extreme but do not solely drive the correlation; significant $p-$values for $M_{\rm H_2}/M_\ast$ ($p$-value = 0.003), $\log(R_{\rm e})$ ($p$-value = 0.004), and $\log(R_{\rm e, H_2})$ ($p$-value = 0.00005), remain without the tail.

</paper>

Write the methods card for this paper.