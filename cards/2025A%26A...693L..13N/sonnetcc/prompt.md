# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...693L..13N\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...693L..13N",
 "title": "Dense gas scaling relations at kiloparsec scales across nearby galaxies with the ALMA ALMOND and IRAM 30 m EMPIRE surveys",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Neumann, Lukas",
 "n_authors": 20,
 "arxiv_id": "2412.10506",
 "doi": "10.1051/0004-6361/202453208",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.01161.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00230.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00815.S",
  "2017.1.00886.L",
  "2018.1.01171.S",
  "2018.1.01651.S",
  "2018.A.00062.S",
  "2019.2.00134.S",
  "2021.1.00740.S"
 ]
}
```

Paper text:
<paper>
# Dense gas scaling relations at kiloparsec scales across nearby galaxies with the ALMA ALMOND and IRAM 30m EMPIRE surveys

# Introduction

Stars form from the coldest, densest substructures within molecular clouds. Higher-critical-density molecular lines (‘dense gas tracers’) trace this denser subset of molecular gas, in contrast to the less dense gas probed by low-J CO lines.

The brightest and most commonly used extragalactic dense gas tracers are $\mathrm{HCN(1-0)}$ and $\text{HCO}^+\mathrm{(1-0)}$, hereafter HCN and HCO$^+$. A nearly linear correlation has been observed between the star formation rate (SFR) and dense gas tracer luminosity across a wide range of scales (cite: Gao2004; Wu2010; Garcia-Burillo2012; Usero2015; Chen2017). This has been interpreted as an indication that dense gas plays a regulating role in the star formation process. This prompts the question of what determines the amount of dense gas. Moreover, these early studies suggested that the rate of star formation per unit dense gas tracer luminosity or dense gas mass (SFE$_{\rm dense} \equiv {\rm SFR}/M_{\rm dense}$) is not universal, but varies from galaxy to galaxy and location to location (cite: Garcia-Burillo2012; Usero2015; Chen2015).

Recently, the first dense gas tracer mapping surveys that cover whole galaxies have emerged. The Institut de Radioastronomie Millimétrique (IRAM) 30m large programme EMPIRE[^3] (cite: Bigiel2016; Jimenez-Donaire2017; Jimenez-Donaire2019) obtained approximately kiloparsec-resolution maps of dense gas tracers (HCN, HCO$^+$, and $\mathrm{HNC(1-0)}$) and CO isotopologues for nine nearby galaxies. The ALMA ALMOND[^4] survey (cite: Neumann2023a) used the Morita Atacama Compact Array (ACA) to map HCN, HCO$^+$, and $\mathrm{CS(2-1)}$ emission from 25 nearby galaxies that were also mapped by the Physics at High Angular resolution in Nearby GalaxieS (PHANGS)–ALMA $\mathrm{CO(2-1)}$ survey (cite: Leroy2021a). Meanwhile, a number of smaller surveys observed dense gas tracers in samples of one to four galaxies (cite: Tan2018; Gallagher2018a; Gallagher2018b; Querejeta2019; Beslic2021; Heyer2022; Neumann2024; Lin2024).

These mapping surveys confirmed significant variations in the SFR/HCN and HCN/CO ratios. SFR/HCN serves as a proxy for the star formation efficiency in denser gas. HCN/CO contrasts high and low critical gas density tracers and so probes the physical density distribution. Both quantities correlate with the local stellar and gas surface density, dynamical equilibrium pressure, and other environmental factors such that denser gas (higher HCN/CO) and lower SFR/HCN is found in high-surface-density, high-pressure regions (cite: Jimenez-Donaire2019). At face value, this implies an environment-dependent dense gas star formation efficiency and gas density across the discs of star-forming galaxies.

This Letter presents new measurements of HCN/CO and SFR/HCN as a function of local conditions for the 25 galaxies in the ALMA ALMOND survey, which is the largest mapping survey of dense gas tracers in galaxy discs. We synthesised ALMOND data with the IRAM 30m EMPIRE survey, the first large dense gas tracer mapping survey, to present a homogeneously measured set of kiloparsec-resolution scaling relations that connect star formation, dense gas, and total molecular gas to these local environmental quantities for a total of 31 local spiral galaxies.

# Data and methods

We used the HCN data presented in (cite: Jimenez-Donaire2019) and (cite: Neumann2023a).

The two datasets are well matched in terms of sensitivity and resolution (see Appendix [5](#sec:app:empire_vs_almond); median 1.47 kpc, 16-84% range 1.09-1.76 kpc). We convolved all supporting data to the angular resolution of the HCN observations using the [PyStructure](https://zenodo.org/records/13787728) package[^5]. We sampled all maps with a half-beam-spaced hexagonal grid and computed the integrated intensities of the HCN and CO lines by integrating over a velocity range determined by the velocity extent of the CO emission. The velocity integration mask was built from 4-sigma CO peaks and expanded into adjacent 2-sigma channels. We treated the ratios HCN/CO and SFR/HCN as the quantities of interest and measured how they vary as a function of the molecular gas mass surface density ($\Sigma_{\rm mol}$), stellar mass surface density ($\Sigma_\star$), and dynamical equilibrium pressure ($P_{\rm DE}$).

#### Galaxy sample.

Table [\[tab:sample\]](#tab:sample) lists our targets, their integrated properties, survey coverage, and the resolution of the HCN observations. ALMOND and EMPIRE target nearby ($d<25\,\mathrm{Mpc}$), $i<75^\circ$, star-forming ($\mathrm{SFR}\sim0.2-17\,M_\odot\,\mathrm{yr}^{-1}$) galaxies, which span stellar masses from 8 × 10^9^ M $_\odot$ to 1 × 10^11^ M $_\odot$ and SFRs from 0.2 M $_\odot$ ^−1^ to 17 M $_\odot$ ^−1^. We stress that ALMOND significantly increases the dynamic range of SFR and $M_{\star}$(by approximately a factor of 2) compared to the previous largest sample (i.e. EMPIRE; see Fig. [1](#fig:sfms)). Combining the surveys yields 31 unique galaxies. NGC 628, 2903, and 4321 were observed by both surveys, and their measurements are consistent (see Appendix [5](#sec:app:empire_vs_almond)). To avoid duplicates, we employed the ALMOND data for these galaxies.

![](Figures/ALMOND+EMPIRE_SFMS_compressed_v2.pdf)

#### Star formation rate.

We estimate the kiloparsec-scale SFR and SFR surface density ($\Sigma_{\rm SFR}$) following the methodology of the original ALMOND paper (cite: Neumann2023a), which used a combination of infrared (IR; 22 $\mu$ m) maps from Wide-field Infrared Survey Explore (cite: Wright2010) and far-ultraviolet (FUV; 154 nm) maps from Galaxy Evolution Explorer (cite: Martin2005). These maps were taken from the z0MGS atlas (cite: Leroy2019) and converted to SFR following their best FUV+22$\mu$m prescription. Although EMPIRE employed *Spitzer* and *Herschel* IR measurements to estimate the SFR, here we adopted the same methodology across EMPIRE and ALMOND, using the FUV+22$\mu$m-based SFR maps for the full sample.

#### Stellar mass.

We estimated the stellar mass surface density ($\Sigma_{\star}$) from *Spitzer* 3.6 $\mu$ m observations (cite: Sheth2010; Querejeta2021b). We used the dust-corrected maps from (cite: Querejeta2015) and adopted a mass-to-light ratio of $\Upsilon_\star = 0.6$ M$_\odot$ L$_\odot^{-1}$.

#### Dynamical equilibrium pressure.

The dynamical equilibrium pressure ($P_{\text{DE}}$) expresses the total interstellar pressure needed to support a disc in vertical dynamical equilibrium (cite: Ostriker2022; Schinnerer2024). We estimated $P_{\text{DE}}$ by calculating the weight of the interstellar medium in the galaxy potential via$$\begin{align}
    \ensuremath{P_{\text{DE}}}= \dfrac{\pi G}{2}\ensuremath{\Sigma_{\text{gas}}}^2 + \ensuremath{\Sigma_{\text{gas}}}\, \sqrt{2G\ensuremath{\rho_{\star}}} \, \sigma_{\rm gas, z} \;,
\end{align}$$ where $\ensuremath{\Sigma_{\text{gas}}}=\ensuremath{\Sigma_{\text{mol}}}+ \ensuremath{\Sigma_{\text{atom}}}$ is the total gas surface density, $\ensuremath{\rho_{\star}}$ is the stellar mass volume density, and $\sigma_{\rm gas, z}=\SI{15}{\km\per\s}$ (cite: Sun2018) is the gas velocity dispersion perpendicular to the galactic disc. Computing $\rho_{\star}$ required estimates of the stellar scale heights, which were estimated from measured stellar disc scale lengths by assuming a typical disc flattening ratio (cite: Sun2020b; Sun2022). Estimating $P_{\text{DE}}$ additionally required measurements of the atomic gas content, which were taken from $\text{H}\,{\scriptstyle\text{I}}$ 21 cm line observations (all with angular resolutions similar to or higher than that of HCN). These observations were available for 26 galaxies of our sample (Table [\[tab:sample\]](#tab:sample)), hence limiting the analysis of $P_{\text{DE}}$ relations to those 26 galaxies.

![](Figures/GS_relation_literature_compilation_compressed.pdf)

+:-----------------:+:-----------------------------------------------------------------------:+:--------------------------------------------------------------:+:------------------------------------------------------------:+:---------------:+
| Regime            | $\log_{10}\,$SFR/HCN                                                    | $\log_{10}\,$IR/HCN                                            | $\log_{10}\,\ensuremath{\tau_\mathrm{dep}^\mathrm{dense}}$   | $\sigma$        |
|                   +-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
|                   | \[$\SI{}{M\ensuremath{_\odot}\per\year}/(\SI{}{\kkms\square\parsec})$\] | \[$\SI{}{L\ensuremath{_\odot}}/(\SI{}{\kkms\square\parsec})$\] | \[$\SI{}{\year}$\]                                           | $[\SI{}{\dex}]$ |
|                   +-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
|                   | (16$^\mathrm{th}$, 50$^\mathrm{th}$, 84$^\mathrm{th}$) perc.            | (16$^\mathrm{th}$, 50$^\mathrm{th}$, 84$^\mathrm{th}$) perc.   | (16$^\mathrm{th}$, 50$^\mathrm{th}$, 84$^\mathrm{th}$) perc. |                 |
+-------------------+-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
| Clouds & Clumps   | $(-7.43,-6.89,-6.27)$                                                   | $(2.40,2.94,3.56)$                                             | $(7.45,8.07,8.61)$                                           | $0.70$          |
+-------------------+-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
| Parts of Galaxies | $(-7.23,-6.98,-6.65)$                                                   | $(2.60,2.85,3.18)$                                             | $(7.82,8.16,8.41)$                                           | $0.46$          |
+-------------------+-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
| Entire Galaxies   | $(-7.16,-6.85,-6.56)$                                                   | $(2.67,2.98,3.27)$                                             | $(7.74,8.03,8.33)$                                           | $0.27$          |
+-------------------+-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
| Combined          | $(-7.17,-6.87,-6.48)$                                                   | $(2.66,2.96,3.35)$                                             | $(7.66,8.05,8.34)$                                           | $0.52$          |
+-------------------+-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+
| ALMOND & EMPIRE   | $(-7.14,-6.84,-6.44)$                                                   | $(2.69,2.99,3.39)$                                             | $(7.62,8.02,8.31)$                                           | $0.35$          |
+-------------------+-------------------------------------------------------------------------+----------------------------------------------------------------+--------------------------------------------------------------+-----------------+

**Notes** – Median dense gas ratios across the combined literature sample presented in Fig. [2](#fig:gao_solomon_relation), including ALMOND and EMPIRE, and for respective subsamples, including clouds and clumps and resolved and integrated galaxy surveys. The values across the ‘Parts of Galaxies’ studies are computed from unique targets (cite: Bigiel2015; Kepley2014; Jimenez-Donaire2019; Sanchez-Garcia2022; Neumann2023a; Beslic2024). The ‘Combined’ measurements are computed from the medians of each respective study. ‘ALMOND & EMPIRE’ results were obtained from the medians of each respective galaxy (i.e. from 31 galaxies) and consider non-detections (in contrast to the other columns, which only consider 3-sigma detected data). All values are on a logarithmic scale. Columns 2 and 3 list the 16th percentiles, medians, and 84th percentiles of $\log_{10}\,$SFR/HCN and $\log_{10}\,$IR/HCN. Column 4 displays the dense gas depletion time ($\tau_\mathrm{dep}^\mathrm{dense}$) in units of years, and Col. 5 the 1-sigma scatter ($\sigma$) of the detected HCN data around the median value in units of dex. See Appendix [6](#sec:app:literature) for details of the compilation.

#### Conversion factors, molecular gas surface density, and dense gas fraction.

We focused on the ratios HCN/CO and SFR/HCN. For reference, we converted them to fiducial physical quantities using fixed conversion factors, $\ensuremath{\alpha_{\text{CO}}}\equiv\ensuremath{M_{\text{mol}}}/\ensuremath{L_{\text{CO}}}\equiv\ensuremath{\Sigma_{\text{mol}}}/\ensuremath{W_{\text{CO}}}$ and $\ensuremath{\alpha_{\text{HCN}}}\equiv\ensuremath{M_{\text{dense}}}/\ensuremath{L_{\text{HCN}}}\equiv\ensuremath{\Sigma_{\text{dense}}}/\ensuremath{W_{\text{HCN}}}$, adopting $\ensuremath{\alpha_{\text{CO}}}^{\rm fix}=\SI{4.35}{M\ensuremath{_\odot}\per\square\parsec}\,(\SI{}{\kkms})^{-1}$ (cite: Bolatto2013) and $\ensuremath{\alpha_{\text{HCN}}}=\SI{15}{M\ensuremath{_\odot}\per\square\parsec}\,(\SI{}{\kkms})^{-1}$ (cite: Schinnerer2024). Aside from aiming to remain ‘close to the observations’, we did this because the environmental dependence of the HCN-to-dense gas conversion factor, $\alpha_{\rm HCN}$, remains unclear, with no obvious best prescription and likely significant covariance with $\alpha_{\rm CO}$ (cite: Usero2015).

Nevertheless, to leverage recent progress in understanding $\alpha_{\text{CO}}$ variations, we employed a variable $\alpha_{\text{CO}}$(hereafter $\ensuremath{\alpha_{\text{CO}}}^{\rm var}$) when considering molecular gas surface density, $\Sigma_{\text{mol}}$, or dynamical equilibrium pressure ($P_{\text{DE}}$; see the paragraphs below) as independent variables (i.e. on the $x$-axis). We calculated $$\begin{align}
\left(\dfrac{\ensuremath{\Sigma_{\text{mol}}}}{\SI{}{M\ensuremath{_\odot}\per\square\parsec}}\right) = \ensuremath{\alpha_{\text{CO}}}^{\rm var}\,\left(\dfrac{\ensuremath{W_{\text{CO}}}}{\SI{}{\kkms}}\right) \cos(i) \;,
\end{align}$$ adopting the $\ensuremath{\alpha_{\text{CO}}}^{\rm var}$ prescription from (cite: Schinnerer2024). This $\ensuremath{\alpha_{\text{CO}}}^{\rm var}$ depends on metallicity and $\Sigma_\star$ (see Appendix [7](#sec:app:conversion_factors) for more details on the variable conversion factor and line ratio prescriptions, including references to the works synthesised by (cite: Schinnerer2024)).

When quoting HCN/CO, we cast our results in terms of $\mathrm{CO(1-0)}$ and employed the $\ensuremath{\mathrm{CO(2-1)}}/\ensuremath{\mathrm{CO(1-0)}}$ line ratio calibration as a function of $\Sigma_{\text{SFR}}$ to convert PHANGS–ALMA $\mathrm{CO(2-1)}$ to $\mathrm{CO(1-0)}$ intensities (see Appendix [7](#sec:app:conversion_factors)). EMPIRE already has $\mathrm{CO(1-0)}$ maps.

For both quantities, we provide reference conversions to physical units. We calculated the ‘dense gas fraction’ as the ratio between dense and bulk molecular gas using fixed conversion factors, $\ensuremath{f_{\text{dense}}}\equiv \ensuremath{M_{\text{dense}}}/\ensuremath{M_{\text{mol}}}\propto {\rm HCN/CO}$, as $$\begin{align}
\ensuremath{f_{\text{dense}}}\approx \num{3.5}\,\left(\dfrac{\ensuremath{W_{\text{HCN}}}}{\SI{}{\kkms}}\right)\left(\dfrac{\ensuremath{W_{\text{CO}}}}{\SI{}{\kkms}}\right)^{-1} \;.
\end{align}$$

We converted SFR/HCN to an approximate star formation efficiency of dense molecular gas, $\ensuremath{\text{SFE}_{\text{dense}}}\equiv \rm{SFR}/\ensuremath{M_{\text{dense}}}$, via$$\begin{align}
\left(\dfrac{\ensuremath{\text{SFE}_{\text{dense}}}}{\SI{}{\per\year}}\right) \approx \num{6.7e-2}\,\left(\dfrac{\ensuremath{\Sigma_{\text{SFR}}}}{\SI{}{M\ensuremath{_\odot}\per\year\per\square\parsec}}\right)\left(\dfrac{\ensuremath{W_{\text{HCN}}}}{\SI{}{\kkms}}\right)^{-1} \;.
\end{align}$$

# Results and discussion

## Gao–Solomon relation

In Fig. [2](#fig:gao_solomon_relation) we present the ‘Gao–Solomon’ relation (cite: Gao2004), the scaling relationship between SFR and $L_{\rm HCN}$. We placed ALMOND and EMPIRE in the context of a literature compilation that comprises 31 HCN surveys spanning from the Milky Way to the high-redshift universe. This includes observations of individual cores and molecular clouds within the Milky Way and the Local Group, spatially resolved maps of galaxies, and integrated galaxy data. On the $x$- and $y$-axes, we indicate both the observed luminosities (HCN and IR) and the inferred physical quantities ($M_{\text{dense}}$ and SFR), assuming linear conversions with fixed conversion factors $\alpha_{\text{HCN}}$ and $C_\mathrm{IR}$[^6]. ALMOND and EMPIRE form the largest resolved galaxy dataset, filling in the large gap in spatial scale, SFR, and $L_{\rm HCN}$ between integrated galaxy and individual cloud studies.

In the bottom panel of Fig. [2](#fig:gao_solomon_relation), the $y$-axis displays the ratio between SFR and $L_{\text{HCN}}$. Across the full literature sample, we find a median SFR/HCN of $\SI{1.3e-07}{M\ensuremath{_\odot}\per\year}\,(\SI{}{\kkms\square\parsec})^{-1}$ with a 1-sigma scatter of $\SI{0.52}{\dex}$, which is consistent with previous literature compilations (cite: Jimenez-Donaire2019; Beslic2024). We also computed the respective median $\text{SFE}_{\text{dense}}$ values and scatter for the individual subsamples: clumps and clouds (squares), resolved galaxy observations (circles), and entire galaxies (diamonds). The values, along with the values specifically for ALMOND and EMPIRE, are listed in Table [\[tab:gao_solomon\]](#tab:gao_solomon). Overall, the literature compilation demonstrates that the HCN luminosity is a reasonable predictor of the SFR from cloud to galaxy scales across ten orders of magnitude. However, at any given HCN luminosity, there is a significant scatter, $\sigma\sim\SI{0.5}{\dex}$. Moreover, the scatter increases from large (entire galaxy; $\sigma=\SI{0.27}{\dex}$) to small scales (clouds; $\sigma=\SI{0.70}{\dex}$), suggesting that there are significant variations in $\text{SFE}_{\text{dense}}$ within galaxies (discussed in Sect. [3.2](#sec:environment_relations)) that average out at integrated galaxy scales.

SFR/HCN can be interpreted, with significant uncertainty due to the uncertain conversion factor, as the rate per unit mass at which dense molecular gas converts into stars. Across the detected sightlines of the full literature sample, we find a median $\ensuremath{\text{SFE}_{\text{dense}}}\approx \SI{8.9e-09}{\per\year}$, or equivalently a median dense gas depletion time of $\ensuremath{\tau_\mathrm{dep}^\mathrm{dense}}\approx \SI{112}{\mega\year}$, indicating that the rate of present-day star formation would consume the available dense gas in this time period. For reference, this is $\approx 10$ times lower than estimates for $\tau^{\text{mol}}_{\rm dep}$, the overall molecular gas depletion time in similar samples (cite: Sun2023). The star formation efficiency per freefall time, $\ensuremath{\epsilon_\mathrm{ff}^\mathrm{dense}}=\ensuremath{\text{SFE}_{\text{dense}}}\cdot\ensuremath{t_\mathrm{ff}^\mathrm{dense}}$, is of theoretical interest (cite: Krumholz2005; Federrath2012) because it captures the efficiency of star formation relative to the timescale expected for gravitational collapse, and so normalises for density. The freefall time of the dense molecular gas was computed as $\ensuremath{t_\mathrm{ff}^\mathrm{dense}}=\SI{0.8}{\mega\year}$, assuming that HCN traces gas above a density of $\ensuremath{n_\mathrm{\ensuremath{\text{H}_2}}^\mathrm{dense}}\approx \SI{3e3}{\per\cubic\centi\metre}$ (cite: Jones2023; Bemis2024). Across the full literature sample, we obtain a median $\ensuremath{\epsilon_\mathrm{ff}^\mathrm{dense}}\approx\SI{0.7}{\percent}$, which suggests that only 0.7 % of the dense molecular gas is converted into stars per gravitational collapse timescale. This demonstrates that even in the dense gas, star formation appears to be an extremely inefficient process.

![](Figures/HCN_scaling_relations_centre_vs_disc_compressed_v2.pdf)

## Dense gas relations with environmental conditions

Figure [2](#fig:gao_solomon_relation) shows significant scatter in SFR/HCN. Previous works have found that both SFR/HCN and HCN/CO depend systematically on environmental factors, including the stellar mass surface density ($\Sigma_{\star}$), the molecular gas mass surface density ($\Sigma_{\text{mol}}$), and the interstellar pressure inferred from dynamical equilibrium ($P_{\text{DE}}$; (cite: Usero2015; Gallagher2018a; Jimenez-Donaire2019)). The combined ALMOND and EMPIRE samples are ideal for measuring these environmental variations. Individual regions follow the overall Gao–Solomon relation and show a comparable scatter to the full literature sample. The kiloparsec-scale resolution is, on the one hand, high enough to resolve galaxies into discrete regions, including centres, bars, and spiral arms, but is, on the other hand, coarse enough to average over many individual regions to access the time-averaged mean HCN/CO and SFR/HCN.

In Fig. [3](#fig:hcn_scaling_relations) we use ALMOND and EMPIRE to make the most rigorous measurement to date of the scaling relations relating HCN/CO and SFR/HCN to these environmental factors. For each galaxy we spectrally stacked the $\mathrm{HCN(1-0)}$ and $\mathrm{CO(1-0)}$ lines in bins of $\Sigma_{\star}$, $\Sigma_{\text{mol}}$, and $P_{\text{DE}}$ using `PyStacker`[^7]. We used the CO data, which have a much higher signal-to-noise ratio than the HCN, to determine the local mean reference velocity for the stacks (cite: Neumann2023b). For bins in which the stacks do not yield 3-sigma HCN detections, we estimated upper limits for HCN/CO and lower limits for SFR/HCN. We fitted the combined set of stacks (including upper limits) for all galaxies using a linear function of the form $$\begin{align}
        \log_{10} Y = b + m \cdot (\log_{10} X - x_0)\;,
    \label{equ:fit_function}
\end{align}$$ where $X=\{\ensuremath{\Sigma_{\star}}, \ensuremath{\Sigma_{\text{mol}}}, \ensuremath{P_{\text{DE}}}\}$ and $Y=\{\mathrm{HCN/CO}, \mathrm{SFR/HCN}\}$ are the $x$- and $y$-axis variables, respectively. The slopes and intercepts are denoted as $m$ and $b$, and $x_0=\{2.4, 1.4, 5.0\}$ is a value close to the median $X$ value. Centring the fit at $x_0$ minimises the covariance between $m$ and $b$. The fitting was performed with the linear regression tool `LinMix`[^8], which takes measurement uncertainties and 3-sigma upper (lower) limits on HCN/CO (SFR/HCN) into account (cite: Neumann2023a). The fit parameters are presented in Table [1](#tab:environment). We note that the range of $\Sigma_\star$, $\Sigma_{\rm mol}$, and $P_{\rm DE}$ covered by these results corresponds to the inner, molecular-gas-dominated parts of galaxies, where most stars form.

We find strong correlations between the stacked HCN/CO and all three quantities, and anti-correlations between SFR/HCN and the same quantities (Fig. [3](#fig:hcn_scaling_relations) and Table [1](#tab:environment)). HCN/CO increases and SFR/HCN decreases with increasing $\Sigma_{\star}$, $\Sigma_{\text{mol}}$, and $P_{\text{DE}}$. The slopes are significant, with both HCN/CO and SFR/HCN changing by $\sim\SI{1}{\dex}$ across our sample. ALMOND and EMPIRE have consistent results despite using different telescopes and using different CO lines (see Appendix [5](#sec:app:empire_vs_almond)).

+----------------+-----------------------------------------+-------+------------------+------------------+----------+----------------------+
| $\log_{10}(Y)$ | $\log_{10}(X)$                          | $x_0$ | $m$ (unc.)       | $b$ (unc.)       | $\sigma$ | $r_\mathrm{Pearson}$ |
+:==============:+:=======================================:+:=====:+:================:+:================:+:========:+:====================:+
| HCN/CO         | $\Sigma_{\star}$                        | $2.4$ | $0.55$ $(0.03)$  | $-1.71$ $(0.01)$ | $0.21$   | $0.77$               |
|                +-----------------------------------------+-------+------------------+------------------+----------+----------------------+
|                | $\Sigma_{\text{mol}}$                   | $1.4$ | $0.65$ $(0.05)$  | $-1.79$ $(0.02)$ | $0.23$   | $0.70$               |
|                +-----------------------------------------+-------+------------------+------------------+----------+----------------------+
|                | $\ensuremath{P_{\text{DE}}}/\SI{}{\kB}$ | $5.0$ | $0.48$ $(0.04)$  | $-1.81$ $(0.02)$ | $0.22$   | $0.76$               |
+----------------+-----------------------------------------+-------+------------------+------------------+----------+----------------------+
| SFR/HCN        | $\Sigma_{\star}$                        | $2.4$ | $-0.61$ $(0.04)$ | $-6.84$ $(0.02)$ | $0.28$   | $-0.70$              |
|                +-----------------------------------------+-------+------------------+------------------+----------+----------------------+
|                | $\Sigma_{\text{mol}}$                   | $1.4$ | $-0.67$ $(0.08)$ | $-6.77$ $(0.02)$ | $0.34$   | $-0.56$              |
|                +-----------------------------------------+-------+------------------+------------------+----------+----------------------+
|                | $\ensuremath{P_{\text{DE}}}/\SI{}{\kB}$ | $5.0$ | $-0.55$ $(0.05)$ | $-6.73$ $(0.03)$ | $0.34$   | $-0.66$              |
+----------------+-----------------------------------------+-------+------------------+------------------+----------+----------------------+

: Dense gas tracer and environment in ALMOND and EMPIRE.

**Notes** – Fit parameters obtained via linear regression with `LinMix` via Eq. [\[equ:fit_function\]](#equ:fit_function) to the data shown in Fig. [3](#fig:hcn_scaling_relations). The parameters $x_0$, $m$, $b,$ and $\sigma$ are the $x$-axis offset, slope, intercept, and scatter of the relation. $r_\mathrm{Pearson}$ denotes the Pearson correlation coefficient; all $p$-values are much less than $0.01$. $\Sigma_{\star}$ and $\Sigma_{\text{mol}}$ are given in units of  M$_\odot$ ; and $\ensuremath{P_{\text{DE}}}/\SI{}{\kB}$ in  K cm^−3^.\

The enhanced HCN/CO in high-surface-density, high-pressure environments indicates that a deeper gravitational potential and more abundant overall molecular gas lead to the formation of denser molecular clouds. This picture agrees well with the one that has emerged from high-physical-resolution CO imaging, which shows that the mean cloud-scale gas surface density and velocity dispersion correlate with these same environmental factors (cite: Sun2022). In fact, one of the main results from ALMOND has been a good direct correlation between the cloud-scale gas properties and the density-sensitive HCN/CO line ratio (cite: Neumann2023a). The fact that spectroscopic (presented here) and CO imaging results show similar trends as a function of galactic environment provides strong evidence that the physical properties of molecular clouds vary as a function of the galactic environment. The HCN/CO variations that we observe are continuous across the whole range of our sample, with a $\sim\SI{0.2}{\dex}$ scatter about the correlation.

SFR/HCN anti-correlates with $\Sigma_{\star}$, $\Sigma_{\text{mol}}$, and $P_{\text{DE}}$. This anti-correlation is also significant, though the correlation coefficient is weaker, and the data show more residual scatter in SFR/HCN compared to the trends in HCN/CO. At face value, this indicates that the denser molecular gas that effectively emits HCN is less efficiently converted to stars in high-surface-density, high-pressure parts of galaxies. A popular explanation for this trend has been that HCN-emitting material in these denser environments does not necessarily uniquely correspond to the overdense, self-gravitating parts of clouds that collapse to form stars (cite: Krumholz2007; Shetty2014; Gallagher2018b; Neumann2023a; Bemis2023; Bemis2024)

## Dense gas ratios in galaxy centres

The centres of galaxies often exhibit high $\Sigma_{\text{mol}}$, $\Sigma_{\star}$, and $P_{\text{DE}}$; hence, one expects high HCN/CO and low SFR/HCN in galaxy centres compared to the discs. In Fig. [3](#fig:hcn_scaling_relations) we separately indicate galaxy centres in contrast to the rest of the galaxy. For this exercise, we considered the central kiloparsec-scale, beam-size aperture as the centre and refer to the remaining galaxy parts as the disc.

We find that centres typically have high HCN/CO (median of $0.045$; see Table [\[tab:centres\]](#tab:centres)) compared to the discs (median of $0.013$) that are not consistent within the 1-sigma scatter and low SFR/HCN (median of $\SI{7.8e-8}{M\ensuremath{_\odot}\per\year\per\square\parsec}\,(\SI{}{\kkms})^{-1}$ compared to the disc median of $\SI{1.3e-7}{M\ensuremath{_\odot}\per\year\per\square\parsec}\,(\SI{}{\kkms})^{-1}$ (but overlapping 1-sigma intervals). In the following, we base our discussion of the centre-disc comparison on the relations with $\Sigma_{\star}$, which have uncorrelated axes, in contrast to the relations with $\Sigma_{\text{mol}}$ and $P_{\text{DE}}$, which depend on the CO line intensity. To first order, centres appear to follow the same average HCN/CO and SFR/HCN against $\Sigma_{\star}$ trend, showing a continuous extension of the disc trends. The higher HCN/CO (lower SFR/HCN) in galaxy centres then simply results from the high $\Sigma_{\star}$($\Sigma_{\text{mol}}$, $P_{\text{DE}}$) environment of centres. However, there are some deviations from this simple picture in the SFR/HCN against $\Sigma_{\star}$ relation. On the one hand, the disc measurements in intermediate $\Sigma_{\star}$ environments ($\ensuremath{\Sigma_{\star}}\approx\SI{2e2}{M\ensuremath{_\odot}\per\square\parsec}-\SI{1e3}{M\ensuremath{_\odot}\per\square\parsec}$) tend to have low SFR/HCN compared to the average trend, while centres show high SFR/HCN across the same $\Sigma_{\star}$ range. These deviations could be explained via variations with dynamical environments (e.g. (cite: Neumann2024) found a low SFR/HCN in the galactic bar) but remain speculative due to the coarse, kiloparsec-scale resolution of the ALMOND and EMPIRE observations and hence require higher-resolution observations that resolve these morphological regions.

If taken at face value, the low $\text{SFE}_{\text{dense}}$ in galaxy centres could imply that these environments are typically less efficient at forming stars per unit of dense gas mass, which could be explained by the higher gas turbulence in these environments acting against gravitational collapse (cite: Usero2015; Neumann2023a). However, a similarly likely explanation is that HCN might not be a robust tracer of dense gas in galaxy centres – for example due to increased optical depth, IR pumping (e.g. (cite: Matsushita2015)), or electron excitation, (e.g. (cite: Goldsmith2018)) – and potentially trace more of the bulk gas in these high-density regions (see the explanation above). Therefore, we might expect $\alpha_{\text{HCN}}$ to vary between disc and centre regions. For instance, if one assumes that $\alpha_{\text{HCN}}$ variations are driven by optical depth effects and vary similarly to $\alpha_{\text{CO}}$(cite: Teng2023; Bemis2024), $\alpha_{\text{HCN}}$ would be lower in galaxy centres and thus yield higher $\text{SFE}_{\text{dense}}$ that are more comparable to disc values.

One might expect that active galactic nuclei (AGNs) boost HCN emission (cite: Goldsmith2018; Matsushita2015), deplete gas (cite: Ellison2021), or quench star formation (cite: Nelson2019). In Fig. [3](#fig:hcn_scaling_relations) we additionally indicate the presence of an AGN (cross; 14 galaxies) for the galaxy centres and show their median and distribution in the right panels. We find that active centres have 50 % higher HCN/CO and lower SFRs, though distributions are similar to those found in non-active galaxies and the differences are not significant at the 1-sigma level. The variations in dense gas and star formation in AGN-affected regions are likely not well resolved at the scales probed in this study ($\sim 1-2\,$kpc) and require sub-kiloparsec-resolution observations.

# Conclusions

We present the resolved $1{-}2$ kpc resolution dense gas tracer scaling relations for ALMA ALMOND, a survey of HCN emission from 25 star-forming disc galaxies. Combining ALMOND with the IRAM 30m EMPIRE survey, we measured how HCN/CO and SFR/HCN, observational quantities sensitive to the gas density and star formation efficiency of dense gas, depend on the local stellar and molecular gas mass surface density ($\Sigma_\star$ and $\Sigma_{\rm SFR}$) and the estimated dynamical equilibrium pressure ($P_{\rm DE}$). Our total sample of 31 resolved galaxies represents a factor of $>3$ increase in the number of galaxies compared to the previous state-of-the-art dense gas mapping surveys. HCN/CO correlates with all three environmental measures, showing similar trends to those found for cloud-scale ($\sim 100$ pc) CO imaging. Our results support the view that the physical state of molecular gas depends on the galactic environment. SFR/HCN anti-correlates with surface density and $P_{\rm DE}$, though they show moderately more scatter than the HCN/CO correlations. This reinforces the notion that the scatter in the Gao–Solomon relation is physical in origin and that the relation between any specific dense gas tracer and star formation activity is environment-dependent. While the physical explanations for each of these trends remain subjects of active research, their presence in the data is clear, and ALMA ALMOND + IRAM 30m EMPIRE provides the best measurement to date in the molecular-gas-dominated, star-forming parts of massive disc galaxies.

# Acknowledgements

We would like to thank the referee, Mark Heyer, for his constructive and concise feedback that helped improve the paper. This work was carried out as part of the PHANGS collaboration. LN acknowledges funding from the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - 516405419. AKL gratefully acknowledges support by grants 1653300 and 2205628 from the National Science Foundation, by award JWST-GO-02107.009-A, and by a Humboldt Research Award from the Alexander von Humboldt Foundation. AU acknowledges support from the Spanish grants PGC2018-094671-B-I00, funded by MCIN/AEI/10.13039/501100011033 and by “ERDF A way of making Europe”, and PID2019-108765GB-I00, funded by MCIN/AEI/10.13039/501100011033. RSK acknowledges financial support via the ERC Synergy Grant “ECOGAL” (project ID 855130), via the Heidelberg Cluster of Excellence (EXC 2181 - 390900948) “STRUCTURES”, and via the BMWK project “MAINN” (funding ID 50OO2206). RSK also thanks the 2024/25 Class of Radcliffe Fellows for highly interesting and stimulating discussions. FHL gratefully acknowledges funding from the European Research Council’s starting grant ERC StG-101077573 (“ISM-METALS”). HAP acknowledges support from the National Science and Technology Council of Taiwan under grant 110-2112-M-032-020-MY3.

This paper makes use of the following ALMA data, which have been processed as part of the ALMOND and PHANGS–ALMA surveys:\
ADS/JAO.ALMA#2012.1.00650.S,\
ADS/JAO.ALMA#2013.1.01161.S,\
ADS/JAO.ALMA#2015.1.00925.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2017.1.00230.S,\
ADS/JAO.ALMA#2017.1.00392.S,\
ADS/JAO.ALMA#2017.1.00766.S,\
ADS/JAO.ALMA#2017.1.00815.S,\
ADS/JAO.ALMA#2017.1.00886.L,\
ADS/JAO.ALMA#2018.1.01171.S,\
ADS/JAO.ALMA#2018.1.01651.S,\
ADS/JAO.ALMA#2018.A.00062.S.\
ADS/JAO.ALMA#2019.2.00134.S,\
ADS/JAO.ALMA#2021.1.00740.S,\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory (NRAO) is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work makes use of data products from the Wide-field Infrared Survey Explorer (WISE), which is a joint project of the University of California, Los Angeles, and the Jet Propulsion Laboratory/California Institute of Technology, funded by NASA.

This work is based in part on observations made with the Galaxy Evolution Explorer (GALEX). GALEX is a NASA Small Explorer, whose mission was developed in cooperation with the Centre National d’Etudes Spatiales (CNES) of France and the Korean Ministry of Science and Technology. GALEX is operated for NASA by the California Institute of Technology under NASA contract NAS5-98034.

This paper makes use of MeerKAT observations. The MeerKAT telescope is operated by the South African Radio Astronomy Observatory, which is a facility of the National Research Foundation, an agency of the Department of Science and Innovation.

# Data availability

The HCN and CO data products used in this paper are publicly available via <https://www.iram.fr/ILPA/LP015/> (EMPIRE), <https://www.canfar.net/storage/list/phangs/RELEASES/ALMOND/> (ALMOND), and <https://www.canfar.net/storage/list/phangs/RELEASES/PHANGS-ALMA/> (PHANGS–ALMA). The HCN literature compilation, data products and tables presented in this work are publicly available via <https://www.canfar.net/storage/list/phangs/RELEASES/Neumann_etal_2024b/>. The Python scripts used to create the data products, figures and tables are available via <https://github.com/lukas-neumann-astro/publications/tree/main/Neumann_etal_2024b/>.

84 natexlab

(ref: Anand2021) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621

(ref: Barnes2017) Barnes, A. T., Longmore, S. N., Battersby, C., et al. 2017, MNRAS, 469, 2263

(ref: Bemis2023) Bemis, A. R. & Wilson, C. D. 2023, ApJ, 945, 42

(ref: Bemis2024) Bemis, A. R., Wilson, C. D., Sharda, P., Roberts, I. D., & He, H. 2024, A&A, 692, A146

(ref: Beslic2024) Bešlić, I., Barnes, A. T., Bigiel, F., et al. 2024, A&A, 689, A122

(ref: Beslic2021) Bešlić, I., Barnes, A. T., Bigiel, F., et al. 2021, MNRAS, 506, 963

(ref: Bigiel2015) Bigiel, F., Leroy, A. K., Blitz, L., et al. 2015, ApJ, 815, 103

(ref: Bigiel2016) Bigiel, F., Leroy, A. K., Jiménez-Donaire, M. J., et al. 2016, ApJL, 822, L26

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Braine2017) Braine, J., Shimajiri, Y., André, P., et al. 2017, A&A, 597, A44

(ref: Brouillet2005) Brouillet, N., Muller, S., Herpin, F., Braine, J., & Jacq, T. 2005, A&A, 429, 153

(ref: Buchbender2013) Buchbender, C., Kramer, C., Gonzalez-Garcia, M., et al. 2013, A&A, 549, A17

(ref: Chen2017) Chen, H., Braine, J., Gao, Y., Koda, J., & Gu, Q. 2017, ApJ, 836, 101

(ref: Chen2015) Chen, H., Gao, Y., Braine, J., & Gu, Q. 2015, ApJ, 810, 140

(ref: Chin1998) Chin, Y. N., Henkel, C., Millar, T. J., Whiteoak, J. B., & Marx-Zimmer, M. 1998, A&A, 330, 901

(ref: Chin1997) Chin, Y. N., Henkel, C., Whiteoak, J. B., et al. 1997, A&A, 317, 548

(ref: Chung2009) Chung, A., van Gorkom, J. H., Kenney, J. D. P., Crowl, H., & Vollmer, B. 2009, AJ, 138, 1741

(ref: Crocker2012) Crocker, A., Krips, M., Bureau, M., et al. 2012, MNRAS, 421, 1298

(ref: deBlok2024) de Blok, W. J. G., Healy, J., Maccagni, F. M., et al. 2024, A&A, 688, A109

(ref: denBrok2021) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS \[\]

(ref: Eibensteiner2022) Eibensteiner, C., Barnes, A. T., Bigiel, F., et al. 2022, A&A, 659, A173

(ref: Eibensteiner2024) Eibensteiner, C., Sun, J., Bigiel, F., et al. 2024, A&A, 691, A163

(ref: Ellison2021) Ellison, S. L., Wong, T., Sánchez, S. F., et al. 2021, MNRAS, 505, L46

(ref: Evans2014) Evans, Neal J., I., Heiderman, A., & Vutisalchavakul, N. 2014, ApJ, 782, 114

(ref: Federrath2012) Federrath, C. & Klessen, R. S. 2012, ApJ, 761, 156

(ref: Gallagher2018b) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018a, ApJL, 868, L38

(ref: Gallagher2018a) Gallagher, M. J., Leroy, A. K., Bigiel, F., et al. 2018b, ApJ, 858, 90

(ref: Gao2007) Gao, Y., Carilli, C. L., Solomon, P. M., & Vanden Bout, P. A. 2007, ApJL, 660, L93

(ref: Gao2004) Gao, Y. & Solomon, P. M. 2004, ApJ, 606, 271

(ref: Garcia-Burillo2012) Garcı́a-Burillo, S., Usero, A., Alonso-Herrero, A., et al. 2012, A&A, 539, A8

(ref: Goldsmith2018) Goldsmith, P. & Kauffmann, J. 2018, in American Astronomical Society Meeting Abstracts, Vol. 231, American Astronomical Society Meeting Abstracts #231, 130.06

(ref: Gracia-Carpio2008) Graciá-Carpio, J., Garcı́a-Burillo, S., Planesas, P., Fuente, A., & Usero, A. 2008, A&A, 479, 703

(ref: Herrera-Endoqui2015) Herrera-Endoqui, M., Dı́az-Garcı́a, S., Laurikainen, E., & Salo, H. 2015, A&A, 582, A86

(ref: Heyer2022) Heyer, M., Gregg, B., Calzetti, D., et al. 2022, ApJ, 930, 170

(ref: Jimenez-Donaire2017) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2017, MNRAS, 466, 49

(ref: Jimenez-Donaire2019) Jiménez-Donaire, M. J., Bigiel, F., Leroy, A. K., et al. 2019, ApJ, 880, 127

(ref: Jones2023) Jones, G. H., Clark, P. C., Glover, S. C. O., & Hacar, A. 2023, MNRAS, 520, 1005

(ref: Jones2012) Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2012, MNRAS, 419, 2961

(ref: Juneau2009) Juneau, S., Narayanan, D. T., Moustakas, J., et al. 2009, ApJ, 707, 1217

(ref: Kepley2014) Kepley, A. A., Leroy, A. K., Frayer, D., et al. 2014, ApJL, 780, L13

(ref: Krips2008) Krips, M., Neri, R., Garcı́a-Burillo, S., et al. 2008, ApJ, 677, 262

(ref: Krumholz2005) Krumholz, M. R. & McKee, C. F. 2005, ApJ, 630, 250

(ref: Krumholz2007) Krumholz, M. R. & Thompson, T. A. 2007, ApJ, 669, 289

(ref: Lada2012) Lada, C. J., Forbrich, J., Lombardi, M., & Alves, J. F. 2012, ApJ, 745, 190

(ref: Lang2020) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122

(ref: Leroy2021a) Leroy, A. K., Hughes, A., Liu, D., et al. 2021a, ApJS, 255, 19

(ref: Leroy2022) Leroy, A. K., Rosolowsky, E., Usero, A., et al. 2022, ApJ, 927, 149

(ref: Leroy2019) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24

(ref: Leroy2021b) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021b, ApJS, 257, 43

(ref: Lin2024) Lin, L., Pan, H.-A., Ellison, S. L., et al. 2024, ApJ, 963, 115

(ref: Martin2005) Martin, D. C., Fanson, J., Schiminovich, D., et al. 2005, ApJL, 619, L1

(ref: Matsushita2015) Matsushita, S., Trung, D.-V., Boone, F., et al. 2015, Publication of Korean Astronomical Society, 30, 439

(ref: Murphy2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: Nelson2019) Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234

(ref: Neumann2024) Neumann, L., Bigiel, F., Barnes, A. T., et al. 2024, A&A, 691, A121

(ref: Neumann2023b) Neumann, L., den Brok, J. S., Bigiel, F., et al. 2023a, A&A, 675, A104

(ref: Neumann2023a) Neumann, L., Gallagher, M. J., Bigiel, F., et al. 2023b, MNRAS, 521, 3348

(ref: Ostriker2022) Ostriker, E. C. & Kim, C.-G. 2022, ApJ, 936, 137

(ref: Privon2015) Privon, G. C., Herrero-Illana, R., Evans, A. S., et al. 2015, ApJ, 814, 39

(ref: Querejeta2015) Querejeta, M., Meidt, S. E., Schinnerer, E., et al. 2015, ApJS, 219, 5

(ref: Querejeta2021b) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133

(ref: Querejeta2019) Querejeta, M., Schinnerer, E., Schruba, A., et al. 2019, A&A, 625, A19

(ref: Rybak2022) Rybak, M., Hodge, J. A., Greve, T. R., et al. 2022, A&A, 667, A70

(ref: Sanchez2019) Sánchez, S. F., Barrera-Ballesteros, J. K., López-Cobá, C., et al. 2019, MNRAS, 484, 3042

(ref: Sanchez2014) Sánchez, S. F., Rosales-Ortega, F. F., Iglesias-Páramo, J., et al. 2014, A&A, 563, A49

(ref: Sanchez-Garcia2022) Sánchez-Garcı́a, M., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2022, A&A, 660, A83

(ref: Schinnerer2024) Schinnerer, E. & Leroy, A. K. 2024, arXiv e-prints, arXiv:2403.19843

(ref: Schinnerer2013) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, 42

(ref: Sheth2010) Sheth, K., Regan, M., Hinz, J. L., et al. 2010, PASP, 122, 1397

(ref: Shetty2014) Shetty, R., Clark, P. C., & Klessen, R. S. 2014, MNRAS, 442, 2208

(ref: Stephens2016) Stephens, I. W., Jackson, J. M., Whitaker, J. S., et al. 2016, ApJ, 824, 29

(ref: Stuber2023) Stuber, S. K., Pety, J., Schinnerer, E., et al. 2023, A&A, 680, L20

(ref: Sun2020a) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020a, ApJ, 892, 148

(ref: Sun2023) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL, 945, L19

(ref: Sun2022) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43

(ref: Sun2020b) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020b, ApJL, 901, L8

(ref: Sun2018) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172

(ref: Tan2018) Tan, Q.-H., Gao, Y., Zhang, Z.-Y., et al. 2018, ApJ, 860, 165

(ref: Teng2023) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2023, ApJ, 950, 119

(ref: Usero2015) Usero, A., Leroy, A. K., Walter, F., et al. 2015, AJ, 150, 115

(ref: Veron2010) Véron-Cetty, M. P. & Véron, P. 2010, A&A, 518, A10

(ref: Walter2008) Walter, F., Brinks, E., de Blok, W. J. G., et al. 2008, AJ, 136, 2563

(ref: Wright2010) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: Wu2010) Wu, J., Evans, Neal J., I., Shirley, Y. L., & Knez, C. 2010, ApJS, 188, 313

# EMPIRE versus ALMOND

There are three galaxies (i.e. NGC 628, NGC 2903, NGC 4321) that have been mapped in dense gas tracers (e.g. $\mathrm{HCN(1-0)}$) by both surveys, EMPIRE, using the IRAM 30 m, and ALMOND, using the ACA at similar spectral (a few  km s^−1^) and angular resolution (a few tenths of arcseconds) and sensitivity (a few mK). In Figs. [4](#fig:empire_vs_almond_spectra) to [6](#fig:empire_vs_almond_intensity) we compare the $\mathrm{HCN(1-0)}$ data from both surveys. We homogenise the two datasets by convolving to the best common spectral (i.e. 10 km s^−1^) and spatial (i.e. 33″) resolution and re-project to the same half-beam size hexagonal pixel grid.

Figure [4](#fig:empire_vs_almond_spectra) shows average $\mathrm{HCN(1-0)}$ spectra computed across all sightlines within 5   from the galactic centre. We additional overlay $\mathrm{CO(2-1)}$ average spectra obtained from PHANGS–ALMA (cite: Leroy2021b), to indicate molecular line emission from a highly significant tracer. This line has been used to infer the velocity-integration window from which we compute $\mathrm{HCN(1-0)}$ integrated intensities of $41.6 \pm \SI{7.3}{\kkms}$, $39.5 \pm \SI{10.7}{\kkms}$ in NGC 628, $427.8 \pm \SI{47.5}{\kkms}$, $495.7 \pm \SI{143.5}{\kkms}$ in NGC 2903, and $475.0 \pm \SI{34.6}{\kkms}$, $570.2 \pm \SI{84.8}{\kkms}$ in NGC 4321 from ALMOND and EMPIRE, respectively. The average spectra show similar shape and amplitude, demonstrating little to no bias between ALMOND and EMPIRE observations. The integrated line intensities yield consistent values within their uncertainties. The largest deviations are observed at large velocity offsets from the galaxies’ systemic velocities, potentially linked to poor baseline subtraction.

Figures [5](#fig:empire_vs_almond_brightness_temp) and [6](#fig:empire_vs_almond_intensity) present a voxel-by-voxel, or pixel-by-pixel comparison between the ALMOND and EMPIRE $\mathrm{HCN(1-0)}$ brightness temperatures (ppv cube) and integrated intensities (moment-0 map). We find that brightness temperatures and integrated intensities agree well between ALMOND and EMPIRE in all galaxies (deviations $\leq\SI{50}{\percent}$ across most detected sightlines) and show little bias ($\leq\SI{10}{\percent}$ on average across all data). At lower integrated intensities ($\lesssim\SI{e-1}{\kkms}$), EMPIRE yields moderately larger values than ALMOND, which could indicate differences in the calibration and data reduction pipelines.

The comparison between ALMOND and EMPIRE demonstrated that both datasets yield consistent $\mathrm{HCN(1-0)}$ intensities and subsequent data products. In this work, we employ the ALMOND data for the three galaxies NGC 628, NGC 2903, NGC 4321, due to the slightly better angular resolution and sensitivity of the ALMOND survey.

![](Figures/ALMOND_vs_EMPIRE_spectra_compressed_v2.pdf)

![](Figures/ALMOND_vs_EMPIRE_brightness_temperatures_compressed_v2.pdf)

![](Figures/ALMOND_vs_EMPIRE_integrated_intensities_compressed_v2.pdf)

Figure [7](#fig:hcn_scaling_relations_almond_vs_empire) shows the HCN/CO and SFR/HCN versus $\Sigma_{\star}$, $\Sigma_{\text{mol}}$, and $P_{\text{DE}}$ scaling relations across ALMOND (blue hexagons) and EMPIRE (red circles) at kiloparsec resolution. Our best-fit relations are similar, though slightly steeper, to those reported by (cite: Jimenez-Donaire2019) but are now measured for a larger and more diverse sample of galaxies. The steeper slopes have two reasons: a) the ALMOND sample shows steeper trends, and (b) the inclusion of non-detections into the fitting routines yields $\sim\SI{10}{\percent}$ steeper slopes. We observe a larger scatter across the full sample of 31 galaxies compared to the nine EMPIRE galaxies alone, suggesting that the more diverse sample captures a wider range of conditions not captured by the simple scaling relations.

![](Figures/HCN_scaling_relations_empire_vs_almond_compressed_v2.pdf)

# Dense gas literature

In Fig. [2](#fig:gao_solomon_relation) we present a literature compilation of HCN surveys from local parsec scale over resolved, kiloparsec scale, to unresolved, entire galaxy observations. The cloud- and clump-scale measurements are taken from observations within the Milky Way (cite: Wu2010; Lada2012; Evans2014; Stephens2016), the CMZ (cite: Jones2012; Barnes2017), and the Local Group, namely the Large and Small Magellanic Clouds (LMC, SMC) (cite: Chin1997; Chin1998), M31 (cite: Brouillet2005), M33 (cite: Buchbender2013), and low-metallicity local group galaxies (cite: Braine2017). Resolved galaxy observations, typically from nearby galaxies at $100\,$pc to $2\,$kiloparsec scales, include M82 (cite: Kepley2014), M51 (cite: Usero2015; Chen2017; Querejeta2019; Stuber2023), NGC 4038/39 (cite: Bigiel2015), NGC 3351, NGC 3627, NGC 4254, NGC 4321, NGC 5194 (cite: Gallagher2018a), NGC 3627 (cite: Beslic2021), NGC 1068 (cite: Sanchez-Garcia2022), NGC 6946 (cite: Eibensteiner2022), NGC 4321 (cite: Neumann2024), NGC 253 (cite: Beslic2024), and the two larger-sample surveys EMPIRE (cite: Jimenez-Donaire2019) and ALMOND (cite: Neumann2023a). Integrated-galaxy data cover Luminous Infrared Galaxies (LIRGs), Ultra-Luminous Infrared Galaxies (ULIRG), and AGN galaxies (cite: Krips2008; Gracia-Carpio2008; Juneau2009; Garcia-Burillo2012; Privon2015), early-type galaxies (cite: Crocker2012), and high-redshift galaxies (cite: Gao2007; Rybak2022).

# Conversion factors

For EMPIRE, we use the $\mathrm{CO(1-0)}$ maps obtained as part of the survey. For ALMOND, we use PHANGS–ALMA $\mathrm{CO(2-1)}$ maps, which we convert to an equivalent $\mathrm{CO(1-0)}$ intensity before applying $\ensuremath{\alpha_{\text{CO}}}$. To do this, we estimate a line ratio, $R_{21}$, based on the local SFR surface density ($\Sigma_{\text{SFR}}$) following (cite: denBrok2021), (cite: Leroy2022), and (cite: Schinnerer2024): $$\begin{align}
    R_{21} = \frac{\ensuremath{\mathrm{CO(2-1)}}}{\ensuremath{\mathrm{CO(1-0)}}} = 0.65 \,  \left(\frac{\ensuremath{\Sigma_{\text{SFR}}}}{\SI{1.8e-2}{M\ensuremath{_\odot}\per\year\per\square\kilo\parsec}}\right)^{0.125}  \;,
\end{align}$$ with minimum $R_{21}$ of 0.35 and maximum 1.0. Then we scale the $\mathrm{CO(2-1)}$ intensity by $R_{21}^{-1}$ to present our results in terms of $\mathrm{CO(1-0)}$ intensity.

To compute $\Sigma_{\text{mol}}$ and $P_{\text{DE}}$, we adopt the variable $\alpha_{\text{CO}}$ prescription from (cite: Schinnerer2024), which accounts for variations with metallicity ($Z$; is the solar metallicity) and stellar mass surface density ($\Sigma_{\star}$): $$\begin{align}
    \ensuremath{\alpha_{\text{CO}}}^{\rm var} = \ensuremath{\alpha_{\text{CO}}}^{\rm fix} \, \left(\dfrac{Z}{\SI{}{\zsun}}\right)^{-1.5} \, \left(\dfrac{\mathrm{max}(\ensuremath{\Sigma_{\star}},\,\SI{100}{M\ensuremath{_\odot}\per\square\parsec})}{\SI{100}{M\ensuremath{_\odot}\per\square\parsec}}\right)^{-0.25} \;.
\end{align}$$ Stellar mass maps are inferred from *Spitzer* 3.6 $\mu$ m observations as explained in Sect. [2](#sec:data). Metallicities are estimated based on simple scaling relations, following (cite: Sun2020a). These use a global mass-metallicity relation (cite: Sanchez2019) and employ a radial metallicity relation with a fixed gradient of −0.1 normalised by the effective radius of each galaxy (cite: Sanchez2014).

# Spectral stacking of HCN and CO

![](Figures/ngc4321_almond_stacked_spectra_via_INT_VAL_SD_STAR_compressed.pdf)

We compute spectral stacks of $\mathrm{HCN(1-0)}$ and $\mathrm{CO(1-0)}$ line emission in bins of stellar mass surface density, $\Sigma_{\star}$, molecular gas surface density, $\Sigma_{\text{mol}}$, and dynamical equilibrium pressure, $P_{\text{DE}}$, across the merged sample of 31 galaxies studied in this work. For the ALMOND sample, the $\mathrm{CO(2-1)}$ intensities from PHANGS–ALMA are first converted into $\mathrm{CO(1-0)}$ intensities using the line ratio calibration from Sect. [7](#sec:app:conversion_factors). We note, however, that this has no effect on the stacking procedure. We stack in logarithmic bins for each galaxy individually, selecting ten bins from a fixed minimum ($\ensuremath{\Sigma_{\star}}=\SI{3e1}{M\ensuremath{_\odot}\per\square\parsec}$, $\ensuremath{\Sigma_{\text{mol}}}=\SI{5e0}{M\ensuremath{_\odot}\per\square\parsec}$, $\ensuremath{P_{\text{DE}}}=\SI{1e4}{\kB\kelvin\per\cubic\cm}$) to the maximum value of each galaxy. For the centres versus disc HCN scaling relations (Fig. [3](#fig:hcn_scaling_relations)), we exclude the centres from the stacking and stacks across the remaining sightlines adopting nine bins. Figure [8](#fig:ngc4321_stacks) shows exemplary spectral stacks of $\mathrm{HCN(1-0)}$ and $\mathrm{CO(1-0)}$ as a function of $\Sigma_{\star}$ across the galaxy NGC 4321.

# Additional tables

Table [\[tab:sample\]](#tab:sample) presents the combined galaxy sample composed of 31 galaxies from the EMPIRE and ALMOND surveys, along with their coordinates and global properties.

+:--------:+:-----------------:+:---------------:+:-----------------------:+:------------------:+:-------------------------------:+:----------------------------------------:+:-----------------------------------:+:-----:+:------:+:----------:+:-----------------------------------------:+:-----------:+:----------:+:---------------------:+:-------:+
| Galaxy   | R.A.              | Dec.            | $d$                     | $i$                | $\log_{10}\,M_\star$            | $\log_{10}\,$SFR                         | $\log_{10}\,(\mathrm{SFR}/M_\star)$ | Bar   | AGN    | SFR tracer | $\text{H}\,{\scriptstyle\text{I}}$ survey | CO survey   | HCN survey | HCN resolution                  |
|          +-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+       |        |            |                                           |             |            +-----------------------+---------+
|          | (J2000)           | (J2000)         | ($\SI{}{\mega\parsec}$) | ($\SI{}{\degree}$) | ($\SI{}{M\ensuremath{_\odot}}$) | ($\SI{}{M\ensuremath{_\odot}\per\year}$) | ($\SI{}{\per\year}$)                |       |        |            |                                           |             |            | ($\SI{}{\arcsecond}$) | (kpc)   |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| \(1\)    | \(2\)             | \(3\)           | \(4\)                   | \(5\)              | \(6\)                           | \(7\)                                    | \(8\)                               | \(9\) | \(10\) | \(11\)     | \(12\)                                    | \(13\)      | \(14\)     | \(15\)                | \(16\)  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 0628 | 01°36′41.7252″    | 15°47′01.1148″  | $9.84$                  | $8.90$             | $10.34$                         | $0.24$                                   | $-10.10$                            |       |        | W4+FUV     | THINGS                                    | PHANGS-ALMA | ALMOND     | $18.60$               | $0.89$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1097 | 02°46′18.94968″   | -30°16′28.83″   | $13.58$                 | $48.60$            | $10.76$                         | $0.68$                                   | $-10.08$                            |       |        | W4+FUV     | PHANGS-MeerKAT                            | PHANGS-ALMA | ALMOND     | $19.40$               | $1.28$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1365 | 03°33′36.3648″    | -36°08′25.4544″ | $19.57$                 | $55.40$            | $10.99$                         | $1.23$                                   | $-9.76$                             |       |        | W4+FUV     |                                           | PHANGS-ALMA | ALMOND     | $20.60$               | $1.95$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1385 | 03°37′28.5636″    | -24°30′04.1832″ | $17.22$                 | $44.00$            | $9.98$                          | $0.32$                                   | $-9.66$                             |       |        | W4+FUV     | PHANGS-VLA                                | PHANGS-ALMA | ALMOND     | $19.90$               | $1.66$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1511 | 03°59′36.5904″    | -67°38′02.148″  | $15.28$                 | $72.70$            | $9.91$                          | $0.36$                                   | $-9.55$                             |       |        | W4+FUV     | PHANGS-MeerKAT                            | PHANGS-ALMA | ALMOND     | $17.60$               | $1.30$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1546 | 04°14′36.2928″    | -56°03′39.2328″ | $17.69$                 | $70.30$            | $10.35$                         | $-0.08$                                  | $-10.43$                            |       |        | W4+FUV     |                                           | PHANGS-ALMA | ALMOND     | $18.90$               | $1.62$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1566 | 04°20′00.3816″    | -54°56′16.836″  | $17.69$                 | $29.50$            | $10.78$                         | $0.66$                                   | $-10.13$                            |       |        | W4+FUV     | MHONGOOSE                                 | PHANGS-ALMA | ALMOND     | $19.70$               | $1.69$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1672 | 04°45′42.4896″    | -59°14′50.1252″ | $19.40$                 | $42.60$            | $10.73$                         | $0.88$                                   | $-9.85$                             |       |        | W4+FUV     | MHONGOOSE                                 | PHANGS-ALMA | ALMOND     | $18.20$               | $1.71$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 1792 | 05°05′14.3256″    | -37°58′50.016″  | $16.20$                 | $65.10$            | $10.61$                         | $0.57$                                   | $-10.04$                            |       |        | W4+FUV     |                                           | PHANGS-ALMA | ALMOND     | $18.70$               | $1.47$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 2566 | 08°18′45.6072″    | -25°29′58.272″  | $23.44$                 | $48.50$            | $10.71$                         | $0.94$                                   | $-9.77$                             |       |        | W4         | PHANGS-VLA                                | PHANGS-ALMA | ALMOND     | $18.50$               | $2.10$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 2903 | 09°32′10.1064″    | 21°30′03.0276″  | $10.00$                 | $66.80$            | $10.63$                         | $0.49$                                   | $-10.15$                            |       |        | W4+FUV     | THINGS                                    | PHANGS-ALMA | ALMOND     | $18.30$               | $0.89$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 2997 | 09°45′38.7936″    | -31°11′27.924″  | $14.06$                 | $33.00$            | $10.73$                         | $0.64$                                   | $-10.09$                            |       |        | W4+FUV     | PHANGS-VLA                                | PHANGS-ALMA | ALMOND     | $20.40$               | $1.39$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 3059 | 09°50′08.16″      | -73°55′19.902″  | $20.23$                 | $29.40$            | $10.38$                         | $0.38$                                   | $-10.00$                            |       |        | W4         | PHANGS-MeerKAT                            | PHANGS-ALMA | ALMOND     | $16.70$               | $1.64$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 3184 | 10°18′16.9416″    | 41°25′27.6348″  | $12.58$                 | $16.00$            | $10.36$                         | $0.11$                                   | $-10.24$                            |       |        | W4+FUV     | THINGS                                    | EMPIRE      | EMPIRE     | $33.30$               | $2.03$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 3521 | 11°05′48.576″     | -00°02′09.4164″ | $13.24$                 | $68.80$            | $11.02$                         | $0.57$                                   | $-10.45$                            |       |        | W4         | THINGS                                    | PHANGS-ALMA | ALMOND     | $21.10$               | $1.35$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 3621 | 11°18′16.3008″    | -32°48′45.36″   | $7.06$                  | $65.80$            | $10.06$                         | $-0.00$                                  | $-10.06$                            |       |        | W4+FUV     | THINGS                                    | PHANGS-ALMA | ALMOND     | $18.90$               | $0.65$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 3627 | 11°20′15.0048″    | 12°59′29.4″     | $11.32$                 | $57.30$            | $10.83$                         | $0.58$                                   | $-10.25$                            |       |        | W4+FUV     | THINGS                                    | EMPIRE      | EMPIRE     | $33.30$               | $1.83$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4254 | 12°18′49.632″     | 14°24′59.0832″  | $13.10$                 | $34.40$            | $10.42$                         | $0.49$                                   | $-9.94$                             |       |        | W4+FUV     | VLA-HERACLES                              | EMPIRE      | EMPIRE     | $33.30$               | $2.11$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4303 | 12°21′54.9312″    | 04°28′25.4784″  | $16.99$                 | $23.50$            | $10.52$                         | $0.73$                                   | $-9.80$                             |       |        | W4+FUV     | PHANGS-VLA                                | PHANGS-ALMA | ALMOND     | $20.20$               | $1.66$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4321 | 12°22′54.9288″    | 15°49′20.2944″  | $15.21$                 | $38.50$            | $10.75$                         | $0.55$                                   | $-10.19$                            |       |        | W4+FUV     | VLA-HERACLES                              | PHANGS-ALMA | ALMOND     | $19.60$               | $1.45$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4535 | 12°34′20.304″     | 08°11′52.7028″  | $15.77$                 | $44.70$            | $10.53$                         | $0.33$                                   | $-10.20$                            |       |        | W4+FUV     | PHANGS-MeerKAT                            | PHANGS-ALMA | ALMOND     | $22.80$               | $1.74$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4536 | 12°34′27.0672″    | 02°11′17.6748″  | $16.25$                 | $66.00$            | $10.40$                         | $0.54$                                   | $-9.86$                             |       |        | W4+FUV     | VLA-HERACLES                              | PHANGS-ALMA | ALMOND     | $21.50$               | $1.69$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4569 | 12°36′49.824″     | 13°09′46.35″    | $15.76$                 | $70.00$            | $10.81$                         | $0.12$                                   | $-10.68$                            |       |        | W4+FUV     | VIVA                                      | PHANGS-ALMA | ALMOND     | $19.20$               | $1.47$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 4826 | 12°56′43.6416″    | 21°40′59.0988″  | $4.41$                  | $59.10$            | $10.24$                         | $-0.69$                                  | $-10.93$                            |       |        | W4+FUV     | THINGS                                    | PHANGS-ALMA | ALMOND     | $18.70$               | $0.40$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 5055 | 13°15′49.296″     | 42°01′45.4008″  | $9.02$                  | $59.00$            | $10.79$                         | $0.31$                                   | $-10.48$                            |       |        | W4+FUV     | THINGS                                    | EMPIRE      | EMPIRE     | $33.30$               | $1.46$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 5194 | 13°29′52.6896″    | 47°11′42.5472″  | $8.56$                  | $21.00$            | $10.65$                         | $0.64$                                   | $-10.01$                            |       |        | W4+FUV     | THINGS                                    | PAWS        | EMPIRE     | $33.30$               | $1.38$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 5248 | 13°37′32.0064″    | 08°53′06.702″   | $14.87$                 | $47.40$            | $10.41$                         | $0.36$                                   | $-10.05$                            |       |        | W4+FUV     | PHANGS-VLA                                | PHANGS-ALMA | ALMOND     | $19.90$               | $1.43$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 5643 | 14°32′40.776″     | -44°10′28.596″  | $12.68$                 | $29.90$            | $10.34$                         | $0.41$                                   | $-9.92$                             |       |        | W4         |                                           | PHANGS-ALMA | ALMOND     | $18.00$               | $1.11$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 6300 | 17°16′59.472″     | -62°49′13.98″   | $11.58$                 | $49.60$            | $10.47$                         | $0.28$                                   | $-10.19$                            |       |        | W4         |                                           | PHANGS-ALMA | ALMOND     | $17.70$               | $0.99$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 6946 | 20°34′52.6032″    | 60°09′12.654″   | $7.34$                  | $33.00$            | $10.47$                         | $0.77$                                   | $-9.70$                             |       |        | W4+FUV     | THINGS                                    | EMPIRE      | EMPIRE     | $33.30$               | $1.18$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+
| NGC 7496 | 23°09′47.2848″    | -43°25′40.26″   | $18.72$                 | $35.90$            | $10.00$                         | $0.35$                                   | $-9.64$                             |       |        | W4+FUV     | PHANGS-MeerKAT                            | PHANGS-ALMA | ALMOND     | $17.90$               | $1.62$  |
+----------+-------------------+-----------------+-------------------------+--------------------+---------------------------------+------------------------------------------+-------------------------------------+-------+--------+------------+-------------------------------------------+-------------+------------+-----------------------+---------+

**Notes** – (2) Right ascension, (3) declination, (4) distance (cite: Anand2021), and (5) inclination angle (cite: Lang2020). Integrated galaxy properties, (6) global stellar mass and (7) global SFR, taken from (cite: Leroy2019). (9) Presence of a galactic bar (cite: Herrera-Endoqui2015; Querejeta2021b), and/or (10) AGN (cite: Veron2010). (11) Employed SFR tracers using WISE 22 $\mu$ m (cite: Wright2010) or a combination of WISE and GALEX-FUV (cite: Martin2005), aopted from (cite: Leroy2019). (12) Archival $\text{H}\,{\scriptstyle\text{I}}$ 21-cm line emission data, taken from THINGS (cite: Walter2008), VIVA (cite: Chung2009), VLA–HERACLES, PHANGS–VLA (Utomo et al. in prep.), PHANGS–MeerKAT (cite: Eibensteiner2024), and MHONGOOSE (cite: deBlok2024). (13) Archival CO observations from PHANGS–ALMA (cite: Leroy2021b) for ALMOND galaxies, and EMPIRE (cite: Jimenez-Donaire2019), PAWS (cite: Schinnerer2013) for EMPIRE galaxies. (14) Adopted HCN data from ALMOND (cite: Neumann2023a) and EMPIRE (cite: Jimenez-Donaire2019). (15) HCN native angular resolution and (16) corresponding linear resolution, given the distance $d$.

Table [\[tab:centres\]](#tab:centres) lists percentile and median HCN/CO and SFR/HCN values for centre and discs environments discussed in Sect. [3.3](#sec:centres).

+----------------+------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
| $\log_{10}(Y)$ | environment      | (16$^\mathrm{th}$, 50$^\mathrm{th}$, 84$^\mathrm{th}$) perc. ($\ensuremath{\mathrm{S}/\mathrm{N}}\geq 3$) | median (all $\mathrm{S}/\mathrm{N}$) |
+:==============:+:================:+:=========================================================================================================:+:====================================:+
| HCN/CO         | disc             | $(-1.96,-1.72,-1.51)$                                                                                     | $-1.87$                              |
|                +------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
|                | centre           | $(-1.60,-1.35,-1.04)$                                                                                     | $-1.35$                              |
|                +------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
|                | centre (AGN)     | $(-1.43,-1.30,-1.03)$                                                                                     | $-1.28$                              |
|                +------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
|                | centre (non-AGN) | $(-1.62,-1.43,-1.22)$                                                                                     | $-1.43$                              |
+----------------+------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
| SFR/HCN        | disc             | $(-7.21,-6.93,-6.56)$                                                                                     | $-6.85$                              |
|                +------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
|                | centre           | $(-7.39,-7.13,-6.57)$                                                                                     | $-7.11$                              |
|                +------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
|                | centre (AGN)     | $(-7.44,-7.19,-6.70)$                                                                                     | $-7.23$                              |
|                +------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+
|                | centre (non-AGN) | $(-7.31,-7.11,-6.57)$                                                                                     | $-7.11$                              |
+----------------+------------------+-----------------------------------------------------------------------------------------------------------+--------------------------------------+

**Notes** – 16$^\mathrm{th}$ percentiles, medians, and 84$^\mathrm{th}$ percentiles of HCN/CO and SFR/HCN across significant data ($\ensuremath{\mathrm{S}/\mathrm{N}}\geq 3$) in disc and centre environments. For the centres, we also present percentile values among centres with and without AGNs. The last column additionally lists the median values across all $\mathrm{S}/\mathrm{N}$ data, this means including non-detections, which yields 0.15 lower HCN/CO and 0.08 higher SFR/HCN across galaxy discs, which are affected by $\mathrm{S}/\mathrm{N}$-clipping (and similar values in centres, which have $\ensuremath{\mathrm{S}/\mathrm{N}}\geq 3$ for 29 out of 31 galaxies).

[^1]: lukas.neumann.astro@gmail.com

[^2]: Jansky Fellow of the National Radio Astronomy Observatory

[^3]: Eight MIxing Receiver (EMIR) Multiline Probe of the Interstellar medium (ISM) Regulating galaxy Evolution; <https://empiresurvey.yourwebsitespace.com>

[^4]: ACA Large-sample Mapping Of Nearby galaxies in Dense gas.

[^5]: <https://github.com/jdenbrok/PyStructure>

[^6]: All data here have observed HCN, but for the $y$-axis we adopted the best-estimate SFR and converted it to the equivalent $L_{\rm IR}$ using a constant IR-to-SFR conversion factor, $\ensuremath{C_\mathrm{IR}}=\SI{1.48e-10}{M\ensuremath{_\odot}\per\year\perL\ensuremath{_\odot}}$ (cite: Murphy2011).

[^7]: <https://github.com/PhangsTeam/PyStacker>

[^8]: <https://github.com/jmeyers314/linmix>

</paper>

Write the methods card for this paper.