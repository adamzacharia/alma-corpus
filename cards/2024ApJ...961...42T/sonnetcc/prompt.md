# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...961...42T\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...961...42T",
 "title": "Star Formation Efficiency in Nearby Galaxies Revealed with a New CO-to-H<SUB>2</SUB> Conversion Factor Prescription",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Teng, Yu-Hsuan",
 "n_authors": 27,
 "arxiv_id": "2310.16037",
 "doi": "10.3847/1538-4357/ad10ae",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.00803.S",
  "2013.1.01161.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.01321.S",
  "2018.1.01651.S",
  "2018.A.00062.S"
 ]
}
```

Paper text:
<paper>
# Star Formation Efficiency in Nearby Galaxies Revealed with a New CO-to-H$_2$ Conversion Factor Prescription

## Abstract

Determining how galactic environment, especially the high gas densities and complex dynamics in bar-fed galaxy centers, alters the star formation efficiency (SFE) of molecular gas is critical to understanding galaxy evolution. However, these same physical or dynamical effects also alter the emissivity properties of CO, leading to variations in the CO-to-H$_2$ conversion factor ($\alpha_\mathrm{CO}$) that impact the assessment of the gas column densities and thus of the SFE. To address such issues, we investigate the dependence of $\alpha_\mathrm{CO}$ on local CO velocity dispersion at 150 pc scales using a new set of dust-based $\alpha_\mathrm{CO}$ measurements, and propose a new $\alpha_\mathrm{CO}$ prescription that accounts for CO emissivity variations across galaxies. Based on this prescription, we estimate the SFE in a sample of 65 galaxies from the PHANGS–ALMA survey. We find increasing SFE towards high surface density regions like galaxy centers, while using a constant or metallicity-based $\alpha_\mathrm{CO}$ results in a more homogeneous SFE throughout the centers and disks. Our prescription further reveals a mean molecular gas depletion time of 700 Myr in the centers of barred galaxies, which is overall 3–4 times shorter than in non-barred galaxy centers or the disks. Across the galaxy disks, the depletion time is consistently around 2–3 Gyr regardless of the choice of $\alpha_\mathrm{CO}$ prescription. All together, our results suggest that the high level of star formation activity in barred centers is not simply due to an increased amount of molecular gas but also an enhanced SFE compared to non-barred centers or disk regions.

# Introduction

Star formation in galaxies is governed by the amount of molecular gas and the efficiency with which that gas is converted into stars. To understand the evolutionary process of star formation activity within galaxies, it is critical to measure the molecular gas star formation efficiency (SFE; defined as the ratio between star formation rate, SFR, and molecular gas mass, $M_\mathrm{mol}$), or molecular gas depletion time ($t_\mathrm{dep} = 1/\mathrm{SFE}$) (cite: 2022ARA&A..60..319S). Previous studies have found that SFR and molecular gas surface densities are highly correlated (cite: 1998ApJ...498..541K) and that $t_\mathrm{dep}$ is usually at 1–4 Gyr across nearby star-forming galaxies (cite: 2008AJ....136.2846B; 2008AJ....136.2782L; 2011MNRAS.415...61S; stacking; 2017ApJ...849...26U; 2023ApJ...945L..19S). Despite the minor variation in general, $t_\mathrm{dep}$ is also found to vary systematically with local and global host galaxy properties, which could be driven by environmental and/or dynamical effects from e.g., metallicity, molecular cloud structure, bar instabilities, active galactic nuclei, or galaxy interactions (cite: 2011MNRAS.415...61S; 2012ApJ...758...73S; 2019ApJ...883....2S; 2021MNRAS.501.4777E; 2021MNRAS.505L..46E; 2021A&A...656A.133Q; 2022MNRAS.514.5035L; 2022ApJ...940..176V; 2023A&A...671A...3J; 2023ApJ...943....7M).

The assessment of molecular gas SFE relies heavily on the CO-to-H$_2$ conversion factor ($\alpha_\mathrm{CO}$)[^1]:

$$\begin{equation}
\alpha_\mathrm{CO} = \frac{M_\mathrm{mol}}{L'_\mathrm{CO(1-0)}} = \frac{\Sigma_\mathrm{mol}}{I_\mathrm{CO(1-0)}}\ \rm \left[\frac{M_\odot}{K\ km~s^{-1}\ pc^2} \right]~,
\label{def_alphaCO}
\end{equation}$$

where $M_\mathrm{mol}$ ($\Sigma_\mathrm{mol}$) is the total molecular gas mass (surface density) and $L'_\mathrm{CO(1-0)}$ ($I_\mathrm{CO(1-0)}$) is the line luminosity (intensity) of CO $J$=1–0. $\alpha_\mathrm{CO}$ is known to vary with molecular gas conditions such as density, temperature, and dynamical state (cite: co-to-h2), which are the same conditions that could also alter the intrinsic SFE of the molecular gas. Due to the lack of a widely-agreed prescription that can accurately predict $\alpha_\mathrm{CO}$, many studies could only assume a constant $\alpha_\mathrm{CO}$ referencing the Milky Way (MW) disk average (e.g., ) to convert CO observations to molecular gas mass. This has made $\alpha_\mathrm{CO}$ variation one of the dominant sources of uncertainty in current molecular gas and SFE studies (cite: 2020MNRAS.492.6027E; 2023ApJ...943....7M; 2023ApJ...945L..19S).

The impacts of $\alpha_\mathrm{CO}$ variations on both SFE and cloud evolutionary timescale estimates are particularly critical in galaxy centers (cite: 2013AJ....146...19L; 2017ApJ...849...26U; 2019PASJ...71S..15M; 2020MNRAS.492.6027E; 2021A&A...650A.134P; 2023ApJ...943....7M; 2023ApJ...945L..19S). In those environments, $\alpha_\mathrm{CO}$ can be 5–15 times lower than the Galactic disk value (cite: 2012ApJ...750....3A; 2013ApJ...777....5S; 2020A&A...635A.131I; 2022ApJ...925...72T; 2023ApJ...950..119T; 2023arXiv230203044D). The lower $\alpha_\mathrm{CO}$ in galaxy centers is likely driven by CO emissivity variations due to higher excitation and/or stronger dynamical effects such as turbulence or inflowing gas (cite: 2012MNRAS.421.3127N; 2012ApJ...751...10P; co-to-h2; 2020ApJ...903..142G; 2023ApJ...950..119T). These effects may also explain the low $\alpha_\mathrm{CO}$ seen in mergers or (ultra-)luminous infrared galaxies (U/LIRGs) (cite: 1998ApJ...507..615D; 2017ApJ...850...77K; 2017ApJ...840....8S; 2018ApJ...863..143C; 2019A&A...628A..71H).

Reducing the uncertainty in molecular gas and SFE studies, and thereby improving our understanding in star formation and galaxy evolution, requires a robust $\alpha_\mathrm{CO}$ prescription that can be systematically applied to large samples of galaxies with diverse environments. Recent studies have proposed various types of $\alpha_\mathrm{CO}$ prescription depending on metallicity, stellar mass surface density, SFR, SFE, and/or CO line-related properties (cite: 2012ApJ...746...69G; 2012MNRAS.421.3127N; co-to-h2; 2015A&A...583A.114H; 2016A&A...588A..23A; 2017MNRAS.464.3315A; 2019A&A...621A.104R; 2020ApJ...903..142G; 2020A&A...643A.141M; 2023arXiv230614881R). However, establishing a reliable $\alpha_\mathrm{CO}$ calibration remains a challenge because it requires $\alpha_\mathrm{CO}$ measurements covering a sufficient sample of galaxies spanning a broad range of molecular gas physical and dynamical conditions, and the two most realistic ways to measure $\alpha_\mathrm{CO}$ in nearby galaxies are via dust emission (which is typically restricted to kpc resolutions; (cite: 1997A&A...328..471I; 2011ApJ...737...12L; 2013ApJ...777....5S; 2017ApJ...835..278S; 2021ApJS..256....3P; 2023arXiv230203044D; 2023PASJ...75..743Y; 2023arXiv231100407C)) or multi-CO isotopologue observations (which is expensive at cloud scales; (cite: 2017ApJ...840....8S; 2018MNRAS.475.3909C; 2020A&A...635A.131I; 2022MNRAS.509.2180S; 2022ApJ...925...72T; 2023ApJ...950..119T)).

Thanks to the high resolution and sensitivity of the Atacama Large Millimeter/submillimeter Array (ALMA), CO (isotopologue) observations are now routinely possible at cloud scales in nearby galaxies (cite: 2021ApJS..257...43L; 2022MNRAS.512.1522D; 2023ApJ...949..108K; 2023MNRAS.525.4270W). In particular, recent studies modeling multi-CO isotopologues in nearby galaxy centers have revealed that CO opacity is the dominant driver of $\alpha_\mathrm{CO}$ variations (cite: 2020A&A...635A.131I; 2022ApJ...925...72T; 2023ApJ...950..119T). This strong dependence of $\alpha_\mathrm{CO}$ on CO opacity further leads to a clear anti-correlation between $\alpha_\mathrm{CO}$ and the observed line width at $\sim$100 pc scales in barred galaxy centers (cite: 2023ApJ...950..119T).

Motivated by these latest measurements of $\alpha_\mathrm{CO}$, we will test if the correlation found in also applies to the 12 galaxies (labeled with \* in Table [\[tab:sample\]](#tab:sample), including 8 barred and 4 non-barred) which have dust-inferred $\alpha_\mathrm{CO}$ values at kpc scales (from (cite: 2023arXiv231100407C); hereafter ) and molecular gas velocity dispersion measured at 150-pc scales (cite: 2021ApJS..257...43L; 2022AJ....164...43S). The results of this comparison lead us to a new $\alpha_\mathrm{CO}$ prescription capturing CO emissivity effects in star-forming galaxies. In this paper, we present this prescription, discuss its physical implications, and study its impact on SFE across a sizable sample of galaxy centers and disks with diverse properties.

# Data and Measurements

## PHANGS Datasets

Our analysis is based on various molecular gas and star formation properties, leveraging a database developed by (cite: 2022AJ....164...43S) which assembled multi-wavelength measurements of 80 galaxies from the PHANGS–ALMA survey (cite: 2021ApJS..257...43L). From this database, we extract multiple physical quantities in matched hexagonal apertures with fixed sizes of 1.5 kpc. The quantities used in this work include: intensity-weighted mean molecular gas velocity dispersion measured at 150-pc scale ($\langle \Delta v \rangle_\mathrm{150pc}$), area-weighted mean CO(2–1) line integrated intensity ($I_\mathrm{CO(2-1)}$), stellar mass surface density ($\Sigma_\mathrm{star}$), SFR surface density ($\Sigma_\mathrm{SFR}$), and gas-phase metallicity ($Z'$, normalized to the solar value $[12+\log(\mathrm{O/H})_\odot = 8.69]$ and calibrated based on (cite: 2004MNRAS.348L..59P)). All these quantities are corrected for the effects of galaxy inclination and data sensitivity limits (see (cite: 2022AJ....164...43S) for more details).

To further explore trends in galaxies with or without stellar bars, we adopt the classification of stellar bars for PHANGS galaxies (cite: 2021A&A...656A.133Q). Table [\[tab:sample\]](#tab:sample) lists the 65 galaxies included in our analysis, which is the overlap between (cite: 2021A&A...656A.133Q) and (cite: 2022AJ....164...43S). This sample from PHANGS has high-resolution CO(2–1) data with beam sizes of 150 pc or smaller. Columns (6–10) in Table [\[tab:sample\]](#tab:sample) show the measurements extracted from (cite: 2022AJ....164...43S) for the central 1.5 kpc regions of those galaxies.

lccccccccccc

\
Galaxy & Bar & Dist. & Incl. & P.A. & $Z'$ & $\log(\Sigma_\mathrm{SFR})$ & $I_\mathrm{CO(2-1)}$ & $\log(\Sigma_\mathrm{star})$ & $\langle \Delta v \rangle_\mathrm{150pc}$ & $\log(\alpha_\mathrm{CO}^\mathrm{Eq.\ref{eqn_ew21_fit}})$ & $\log(t_\mathrm{dep})$\
& & \[Mpc\] & \[deg\] & \[deg\] & \[Z$_\odot$\] & $\left[ \frac{\mathrm{M_\odot}}{\mathrm{yr~kpc^2}} \right]$ & \[K km s$^{-1}$\] & \[M$_\odot$ pc$^{-2}$\] & \[km s$^{-1}$\] & $\left[ \frac{\mathrm{M_\odot\ s}}{\mathrm{K~km~pc^2}} \right]$ & \[yr\]\
(1) & (2) & (3) & (4) & (5) & (6) & (7) & (8) & (9) & (10) & (11) & (12)\

Galaxy & Bar & Dist. & Incl. & P.A. & $Z'$ & $\log(\Sigma_\mathrm{SFR})$ & $I_\mathrm{CO(2-1)}$ & $\log(\Sigma_\mathrm{star})$ & $\langle \Delta v \rangle_\mathrm{150pc}$ & $\log(\alpha_\mathrm{CO}^\mathrm{Eq.\ref{eqn_ew21_fit}})$ & $\log(t_\mathrm{dep})$\
& & \[Mpc\] & \[deg\] & \[deg\] & \[Z$_\odot$\] & $\left[ \frac{\mathrm{M_\odot}}{\mathrm{yr~kpc^2}} \right]$ & \[K km s$^{-1}$\] & \[M$_\odot$ pc$^{-2}$\] & \[km s$^{-1}$\] & $\left[ \frac{\mathrm{M_\odot\ s}}{\mathrm{K~km~pc^2}} \right]$ & \[yr\]\
(1) & (2) & (3) & (4) & (5) & (6) & (7) & (8) & (9) & (10) & (11) & (12)\
\

\
\
IC1954 & 1 & 12.8 & 57.1 & 63.4 & 1.10 & -1.67 & 7.5 & 2.51 & 7.1 & 0.36 & 9.08\
IC5273 & 1 & 14.2 & 52.0 & 234.1 & 1.12 & -1.59 & 4.7 & 2.48 & 7.4 & 0.34 & 8.78\
NGC0253\* & 1 & 3.7 & 75.0 & 52.5 & 1.33 & 0.3166 & 198.2 & 990.2 & 28.5 & -0.15 & 8.88\
NGC0628\* & 0 & 9.8 & 8.9 & 20.7 & 1.29 & -1.82 & 6.3 & 3.03 & 5.4 & 0.45 & 9.26\
NGC0685 & 1 & 19.9 & 23.0 & 100.9 & 1.23 & -2.15 & 2.8 & 2.42 & 6.8 & 0.37 & 9.15\
NGC1087 & 1 & 15.8 & 42.9 & 359.1 & 1.19 & -1.12 & 24.7 & 2.68 & 13.4 & 0.12 & 8.82\
NGC1097 & 1 & 13.6 & 48.6 & 122.4 & 1.34 & -0.29 & 196.0 & 3.61 & 33.1 & -0.20 & 8.57\
NGC1300 & 1 & 19.0 & 31.8 & 278.0 & 1.33 & -1.57 & 44.6 & 3.25 & 23.2 & -0.07 & 9.33\
NGC1317 & 1 & 19.1 & 23.2 & 221.5 & 1.33 & -1.45 & 25.2 & 3.64 & 18.0 & 0.02 & 9.06\
NGC1365 & 1 & 19.6 & 55.4 & 201.1 & 1.36 & 0.04 & 462.4 & 3.80 & 25.6 & -0.11 & 8.70\
NGC1385 & 0 & 17.2 & 44.0 & 181.3 & 1.21 & -1.00 & 15.0 & 2.78 & 9.5 & 0.25 & 8.60\
NGC1433 & 1 & 18.6 & 28.6 & 199.7 & 1.35 & -1.46 & 44.6 & 3.63 & 17.3 & 0.03 & 9.33\
NGC1511 & 0 & 15.3 & 72.7 & 297.0 & 1.18 & -1.17 & 12.4 & 2.60 & 7.5 & 0.33 & 8.79\
NGC1512 & 1 & 18.8 & 42.5 & 261.9 & 1.34 & -1.36 & 31.9 & 3.41 & 11.3 & 0.19 & 9.24\
NGC1546 & 0 & 17.7 & 70.3 & 147.8 & 1.29 & -1.52 & 45.0 & 3.08 & 7.9 & 0.31 & 9.67\
NGC1559 & 1 & 19.4 & 65.4 & 244.5 & 1.29 & -1.47 & 10.5 & 2.77 & 6.6 & 0.38 & 9.06\
NGC1566 & 1 & 17.7 & 29.5 & 214.7 & 1.34 & -0.97 & 55.7 & 3.63 & 28.7 & -0.15 & 8.76\
NGC1637 & 1 & 11.7 & 31.1 & 20.6 & 1.20 & -0.82 & 12.2 & 2.57 & 22.8 & -0.07 & 8.03\
NGC1792 & 0 & 16.2 & 65.1 & 318.9 & 1.33 & -1.35 & 52.0 & 3.08 & 10.7 & 0.21 & 9.46\
NGC1809 & 0 & 20.0 & 57.6 & 138.2 & 1.14 & -1.71 & 2.2 & 2.19 & 3.1 & 0.65 & 8.88\
NGC2090 & 0 & 11.8 & 64.5 & 192.5 & 1.22 & -2.19 & 4.5 & 2.79 & 4.2 & 0.54 & 9.57\
NGC2283 & 1 & 13.7 & 43.7 & -4.1 & 1.18 & -1.93 & 3.0 & 2.31 & 5.1 & 0.47 & 9.07\
NGC2566 & 1 & 23.4 & 48.5 & 312.0 & 1.34 & -0.05 & 265.0 & 3.16 & 26.5 & -0.12 & 8.53\
NGC2835 & 1 & 12.2 & 41.3 & 1.0 & 1.21 & -2.23 & 2.2 & 2.47 & 4.3 & 0.53 & 9.30\
NGC2903 & 1 & 10.0 & 66.8 & 203.7 & 1.33 & -0.81 & 55.8 & 3.15 & 19.7 & -0.01 & 8.73\
NGC2997 & 0 & 14.1 & 33.0 & 108.1 & 1.34 & -0.95 & 68.5 & 3.21 & 16.2 & 0.06 & 9.03\
NGC3059 & 1 & 20.2 & 29.4 & -14.8 & 1.29 & -0.84 & 23.1 & 2.68 & 11.4 & 0.18 & 8.58\
NGC3137 & 0 & 16.4 & 70.3 & -0.3 & 1.18 & -2.53 & 3.0 & 2.19 & 3.2 & 0.64 & 9.85\
NGC3351\* & 1 & 10.0 & 45.1 & 193.2 & 1.29 & -0.71 & 34.4 & 3.18 & 19.2 & -0.01 & 8.43\
NGC3507 & 1 & 23.6 & 21.7 & 55.8 & 1.30 & -1.57 & 17.3 & 3.16 & 23.4 & -0.08 & 8.91\
NGC3511 & 1 & 13.9 & 75.1 & 256.8 & 1.22 & -1.94 & 17.2 & 2.50 & 6.6 & 0.38 & 9.74\
NGC3521\* & 0 & 13.2 & 68.8 & 343.0 & 1.36 & -1.66 & 14.8 & 3.50 & 6.7 & 0.37 & 9.40\
NGC3596 & 0 & 11.3 & 25.1 & 78.4 & 1.10 & -1.55 & 6.3 & 2.68 & 7.0 & 0.36 & 8.90\
NGC3621 & 0 & 7.1 & 65.8 & 343.8 & 1.23 & -1.86 & 8.4 & 2.66 & 5.2 & 0.46 & 9.44\
NGC3626 & 1 & 20.0 & 46.6 & 165.2 & 1.31 & -1.40 & 11.2 & 3.52 & 13.5 & 0.12 & 8.76\
NGC3627\* & 1 & 11.3 & 57.3 & 173.1 & 1.35 & -1.19 & 64.9 & 3.53 & 34.6 & -0.22 & 8.98\
NGC4254\* & 0 & 13.1 & 34.4 & 68.1 & 1.30 & -1.10 & 35.7 & 3.27 & 10.3 & 0.22 & 9.06\
NGC4293 & 1 & 15.8 & 65.0 & 48.3 & 1.31 & -1.11 & 45.0 & 2.92 & 27.4 & -0.13 & 8.82\
NGC4298 & 0 & 14.9 & 59.2 & 313.9 & 1.22 & -1.79 & 14.3 & 2.69 & 9.7 & 0.24 & 9.38\
NGC4303 & 1 & 17.0 & 23.5 & 312.4 & 1.32 & -0.83 & 70.8 & 3.52 & 16.9 & 0.04 & 8.91\
NGC4321\* & 1 & 15.2 & 38.5 & 156.2 & 1.34 & -0.78 & 101.0 & 3.35 & 19.5 & -0.01 & 8.96\
NGC4457 & 1 & 15.1 & 17.4 & 78.7 & 1.30 & -1.15 & 38.7 & 3.69 & 29.0 & -0.15 & 8.77\
NGC4496A & 1 & 14.9 & 53.8 & 51.1 & 1.04 & -2.21 & 1.6 & 2.17 & 2.8 & 0.69 & 9.29\
NGC4535 & 1 & 15.8 & 44.7 & 179.7 & 1.32 & -1.03 & 43.1 & 2.78 & 20.1 & -0.02 & 8.83\
NGC4536\* & 1 & 16.2 & 66.0 & 305.6 & 1.30 & -0.56 & 110.3 & 3.30 & 21.0 & -0.04 & 8.76\
NGC4540 & 1 & 15.8 & 28.7 & 12.8 & 1.14 & -1.90 & 3.9 & 2.65 & 6.3 & 0.40 & 9.07\
NGC4548 & 1 & 16.2 & 38.3 & 138.0 & 1.34 & -1.96 & 9.7 & 3.38 & 24.8 & -0.10 & 9.03\
NGC4569\* & 1 & 15.8 & 70.0 & 18.0 & 1.35 & -1.13 & 112.1 & 3.24 & 27.6 & -0.14 & 9.23\
NGC4571 & 0 & 14.9 & 32.7 & 217.5 & 1.23 & -2.36 & 2.5 & 2.63 & 2.7 & 0.70 & 9.63\
NGC4689\* & 0 & 15.0 & 38.7 & 164.1 & 1.26 & -1.81 & 9.2 & 2.61 & 5.6 & 0.44 & 9.40\
NGC4731 & 1 & 13.3 & 64.0 & 255.4 & 1.02 & -1.97 & 1.6 & 1.99 & 5.1 & 0.47 & 8.85\
NGC4781 & 1 & 11.3 & 59.0 & 290.0 & 1.09 & -1.76 & 9.1 & 2.59 & 8.2 & 0.30 & 9.20\
NGC4826 & 0 & 4.4 & 59.1 & 293.6 & 1.27 & -1.43 & 27.9 & 3.26 & 21.8 & -0.05 & 9.01\
NGC4941\* & 1 & 15.0 & 53.4 & 202.2 & 1.25 & -1.31 & 6.9 & 3.00 & 18.7 & 0.00 & 8.34\
NGC4951 & 0 & 15.0 & 70.2 & 91.2 & 1.15 & -1.77 & 10.0 & 2.67 & 11.4 & 0.18 & 9.14\
NGC5042 & 0 & 16.8 & 49.4 & 190.6 & 1.18 & -2.15 & 2.2 & 2.52 & 5.3 & 0.46 & 9.14\
NGC5068 & 1 & 5.2 & 35.7 & 342.4 & 0.98 & -2.01 & 1.0 & 2.33 & 3.6 & 0.60 & 8.79\
NGC5128 & 0 & 3.7 & 45.3 & 32.2 & 1.36 & -0.78 & 45.3 & 3.70 & 22.7 & -0.07 & 8.56\
NGC5134 & 1 & 19.9 & 22.7 & 311.6 & 1.30 & -1.94 & 4.9 & 3.33 & 11.4 & 0.18 & 9.00\
NGC5248\* & 1 & 14.9 & 47.4 & 109.2 & 1.30 & -0.97 & 72.6 & 3.35 & 15.7 & 0.07 & 9.08\
NGC5530 & 0 & 12.3 & 61.9 & 305.4 & 1.23 & -2.02 & 6.4 & 3.00 & 4.8 & 0.50 & 9.51\
NGC5643 & 1 & 12.7 & 29.9 & 318.7 & 1.29 & -0.29 & 42.0 & 2.88 & 26.7 & -0.12 & 7.98\
NGC6300 & 1 & 11.6 & 49.6 & 105.4 & 1.31 & -0.55 & 41.1 & 2.85 & 36.2 & -0.23 & 8.11\
NGC7456 & 0 & 15.7 & 67.3 & 16.0 & 1.09 & -2.70 & 0.9 & 1.99 & 2.7 & 0.70 & 9.56\
NGC7496 & 1 & 18.7 & 35.9 & 193.7 & 1.21 & -0.43 & 46.2 & 2.72 & 23.7 & -0.08 & 8.20\

## Dust-based $\alpha_\mathrm{CO}$ Measurements

We obtain spatially resolved $\alpha_\mathrm{CO}$ from , where $\alpha_\mathrm{CO}$ is measured at 2 kpc resolution across 41 nearby ($\leq 20$ Mpc) and moderately-inclined ($\text{Incl.}\leq 80^\circ$) spiral galaxies with resolved measurements of CO integrated intensity (including PHANGS-ALMA) and atomic gas. The authors assumed a constant dust-to-metals ratio to constrain the total gas mass with dust and metallicity measurements. In their sample, 8 barred and 4 non-barred galaxies from PHANGS have dust-based $\alpha_\mathrm{CO}$ measurements (those with an \* in Table [\[tab:sample\]](#tab:sample)). These measurements typically cover out to a galactocentric radius of $\sim$10 kpc, including $\sim$2000 Nyquist-sampled data points. It is based on these data that we examine scaling relations of $\alpha_\mathrm{CO}$ and develop an $\alpha_\mathrm{CO}$ prescription in Section [3.1](#subsec:prescription).

The $\alpha_\mathrm{CO}$ measurements in were derived based on the PHANGS CO(2–1) data, and we directly use their $\alpha_\mathrm{CO(2-1)}$ measurements to ensure methodological consistency when we derive molecular gas surface density and SFE (see Sections [3.3](#subsec:sfe_centers) and [3.4](#subsec:sfe)). To compare with most $\alpha_\mathrm{CO}$ literature using $\alpha_\mathrm{CO(1-0)}$, however, we convert the measured $\alpha_\mathrm{CO(2-1)}$ to $\alpha_\mathrm{CO(1-0)}$ by assuming a CO(2–1)/(1–0) ratio ($R_{21}$) of 0.65. Such results can be easily reverted to $\alpha_\mathrm{CO(2-1)}$ via a linear scaling with 0.65. We note that also provided $\alpha_\mathrm{CO(1-0)}$ measurements assuming a SFR-dependent $R_{21}$, and we have checked that using such $\alpha_\mathrm{CO}$ does not change any of our results qualitatively (see Section [3.1](#subsec:prescription)).

We also note that the metallicity adopted by for computing $\alpha_\mathrm{CO}$ is based on the S-calibration in (cite: 2016MNRAS.457.3678P), which is different from the O3N2 calibration used for the PHANGS dataset based on (cite: 2004MNRAS.348L..59P). Recent studies suggest that PG16S is a more reliable metallicity prescription than PP04 (cite: 2019ApJ...887...80K). With the data on 12 galaxies, we find that PP04 estimates result in $\sim$0.2 dex higher $Z'$ than PG16S (cite: 2019A&A...623A...5D), which might be due to the mismatch in the adopted solar oxygen abundance value under different calibration schemes (cite: 2022ApJ...931...92E). Throughout this work, we adopt PG16S-based $Z'$ from for analyses restricted to these 12 galaxies. However, due to the lack of PG16S-based measurements on all 65 PHANGS galaxies, we use the PP04-based $Z'$ when implementing metallicity-dependent $\alpha_\mathrm{CO}$ prescriptions across the full sample for consistency.

To evaluate the credibility of the observed $\alpha_\mathrm{CO}$ trends with our parameters of interest (i.e., $\langle \Delta v \rangle_\mathrm{150pc}$ and $Z'$), we calculate for each parameter bin the number of pixels with reliable $\alpha_\mathrm{CO}$ measurements divided by the number of pixels with measured $\Delta v$ or $Z'$. For $\Delta v$, we find the fraction of reliable pixels to be 70–100% for bins with $\langle \Delta v \rangle_\mathrm{150pc} \gtrsim 3$ km s$^{-1}$, while it drops significantly to $< 50\%$ in lower velocity dispersion bins[^2]. This means that our $\alpha_\mathrm{CO}$ data coverage is insufficient to accurately represent regions with $\Delta v \lesssim 3$ km s$^{-1}$. As for $Z'$, the corresponding completeness of $\alpha_\mathrm{CO}$ is above $60\%$ across regions with $Z' \gtrsim 0.6$, while it drops below $40\%$ at lower metallicities (where the PHANGS-ALMA dataset has poorer coverage). These “incomplete” regimes will be excluded by our fitting and analysis in Section [3.1](#subsec:prescription), where we present the new $\alpha_\mathrm{CO}$ prescription.

# Results

![](Figures/medians_alpha_vdisp_full_allfits_R21W4.pdf)

![](Figures/medians_aco_Zprime_Chiang_allfits.pdf)

\
\

![image](Figures/medians_logresidual_Zprime_Chiang_shaded.pdf)\
(a)

![image](Figures/medians_logresidual_vdisp_ZChiang_shaded.pdf)\
(b)

![image](Figures/alpha_phangs_Eq2_vs_B13_contour_percentiles.pdf)\
(a)

![image](Figures/hist_tdep_centers_TC_medians.pdf)\
(b)

## A Velocity Dispersion-based $\alpha_\mathrm{CO}$ Prescription

To investigate how the dust-based $\alpha_\mathrm{CO}$ varies with local velocity dispersion, we use nearest-neighbor matching to relate the $\alpha_\mathrm{CO}$ measurements at 2-kpc scales with the velocity dispersion which is measured at 150-pc scale and then averaged over 1.5-kpc-sized apertures via intensity weighting ($\langle \Delta v \rangle_\mathrm{150pc}$). As shown in Figure [1](#fig:dust-aco)(a), the data clearly follow an inverse power-law relation, which is in close agreement with the fit by on three barred galaxy centers at $\sim$100 pc scales (i.e., dash-dotted orange line, assuming a CO/H$_2$ abundance of $1.5\times10^{-4}$). The central regions of the 12 galaxies (vertical, gray bars in Figure [1](#fig:dust-aco)(a)) align well with the overall trend, showing that velocity dispersion can trace $\alpha_\mathrm{CO}$ variations in both the centers and disks[^3]. The green cross sign marks the typical MW disk values of $\alpha_\mathrm{CO}$$\sim$4.35 $\mathrm{M_\odot\ (K~km~s^{-1}~pc^2)^{-1}}$ and $\Delta v = 5$ km s$^{-1}$, which also agrees with the overall trend. The shaded area in Figure [1](#fig:dust-aco)(a) indicates the regime where $\alpha_\mathrm{CO}$ data is incomplete (see Section [2.2](#subsec:data_aco)).

Excluding the incomplete regime, we conduct a least-squares fitting in log-log space based on the remaining $\sim$1600 data points, using the `curve_fit` function in `scipy.optimize`. The best-fit power-law relation to these data from 12 galaxies is represented by

$$\begin{equation}
\log \alpha_\mathrm{CO} = -0.81\ \log \langle \Delta v \rangle_\mathrm{150pc} + 1.05~,
\label{eqn_ew21_fit}
\end{equation}$$

where $\alpha_\mathrm{CO}$ and $\langle \Delta v \rangle_\mathrm{150pc}$ are in units of $\mathrm{M_\odot\ (K~km~s^{-1}~pc^2)^{-1}}$ and km s$^{-1}$, respectively. The best-fit relation is shown by the black dashed line in the top panel of Figure [1](#fig:dust-aco)(a) and is consistent with the trend of the binned $\alpha_\mathrm{CO}$ medians. The dispersion of data with respect to Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit) is $\sigma \sim 0.12$ dex, and the standard deviation error returned by `curve_fit` is $\pm$0.02 for both the fitted slope and intercept. We remind readers that the $\alpha_\mathrm{CO}$ data here are converted from $\alpha_\mathrm{CO(2-1)}$ assuming $R_{21} = 0.65$, and thus it should be scaled by $R_{21}/0.65$ if $R_\mathrm{21}$ is known. If a SFR-dependent $R_{21}$ is used following , the trend of $\alpha_\mathrm{CO}$ in Figure [1](#fig:dust-aco)(a) could be shallower by 30–40%, as indicated by the red dashed line.

While the functional fit in Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit) is based on $\Delta v$ measured at 150-pc scale, we also find a similar best-fit relation (dotted line) for six of those galaxies where $\langle \Delta v \rangle_\mathrm{90pc}$ is available. Because $\Delta v$ does not vary strongly between 90 and 150 pc scales (cite: 2022AJ....164...43S), we would not expect this to change our results, and thus Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit) should be applicable with $\Delta v$ measurements around 100-pc resolutions. We note that the evaluation of $\Delta v$ can also be affected by the number of gas components overlapping along the same sightlines, which could increase $\Delta v$ in barred galaxy centers. However, such effect is found to be mild (see , Appendix A), and we expect it to be even milder in our case, as $\langle \Delta v \rangle_\mathrm{150pc}$ is averaged over kpc-sized regions.

## Comparison to Previous Literature

We compare our $\Delta v$-based prescription with existing $\alpha_\mathrm{CO}$ prescriptions in the literature, including those based on metallicity (cite: 2017MNRAS.464.3315A; 2020ApJ...892..148S) or combining metallicity and stellar mass surface density (). First, we investigate if metallicity alone could trace the observed $\alpha_\mathrm{CO}$ variations. Figure [1](#fig:dust-aco)(b) relates the measured $\alpha_\mathrm{CO}$ with metallicity, using the same metallicity as those used in to calculate $\alpha_\mathrm{CO}$ (see Section [2.2](#subsec:data_aco)). The data and the power-law fit (black dashed line) overall agrees with the purely metallicity-dependent $\alpha_\mathrm{CO}$ prescription from (cite: 2017MNRAS.464.3315A) (orange dashed line)[^4], although the data scatter is larger than the trend with velocity dispersion. In the regime where our dataset is complete, the scatter of the observed $\alpha_\mathrm{CO}$ is $\sigma \sim$0.1 dex with $\langle \Delta v \rangle_\mathrm{150pc}$ and 0.3 dex with $Z'$. This shows a significant improvement in predicting $\alpha_\mathrm{CO}$ with our $\Delta v$-based prescription, compared to current metallicity-dependent prescriptions.

In the bottom panels of Figures [1](#fig:dust-aco)(a) and (b), we relate the residuals of each $\alpha_\mathrm{CO}$ fit with $Z'$ or $\langle \Delta v \rangle_\mathrm{150pc}$, in order to check if metallicity effects can explain any residual variation of $\alpha_\mathrm{CO}$ around the $\Delta v$ trend, or the opposite. Above the completeness limit, we find no trend between the residuals from the $\Delta v$ prescription and metallicity. On the other hand, the residuals from the metallicity fit clearly decrease with $\Delta v$ above the completeness threshold. This suggests that $\Delta v$ is crucial for tracing the $\alpha_\mathrm{CO}$ changes, even without including metallicity effects. We have checked that the $\alpha_\mathrm{CO}$ correlation with $Z'$ seen in this regime may come from the correlation between $Z'$ and $\Delta v$, as both variables decrease with the galactocentric radius.

Taking both metallicity and emissivity effects into account, also suggested a tentative prescription[^5] based on $\alpha_\mathrm{CO}$ measurements in nearby disks and (U)LIRGs:

$$\begin{equation}
\alpha_\mathrm{CO} \approx 2.9\ \exp\left(\frac{0.4}{Z'}\right) \left(\frac{\Sigma_\mathrm{star} + \Sigma_\mathrm{mol}}{100\ \mathrm{M_\odot\ pc^{-2}}}\right)^{-\gamma}~,
\label{eqn_alpha_B13}
\end{equation}$$

where $\gamma = 0.5$ if $\Sigma_\mathrm{star} + \Sigma_\mathrm{mol} > 100\ \mathrm{M_\odot}$ pc$^{-2}$ or $\gamma = 0$ otherwise. To compare the derived $\alpha_\mathrm{CO}$ from our proposed prescription (Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit)) with that from , we apply both prescriptions to galaxies in the PHANGS sample (see Table [\[tab:sample\]](#tab:sample)) using kpc-scale $Z'$ and $\Sigma_\mathrm{star}$. As we find $\Sigma_\mathrm{mol} \ll \Sigma_\mathrm{star}$ even with a (likely-overestimated) Galactic $\alpha_\mathrm{CO}$ (cite: 2022AJ....164...43S), we neglect $\Sigma_\mathrm{mol}$ in Equation [\[eqn_alpha_B13\]](#eqn_alpha_B13). We note that also reported a similar $\alpha_\mathrm{CO}$ relation that scales with $\Sigma_\mathrm{star}^{-0.5}$.

Figure [2](#fig:compare-B13)(a) compares the $\alpha_\mathrm{CO}$ values predicted by Equations [\[eqn_ew21_fit\]](#eqn_ew21_fit) and [\[eqn_alpha_B13\]](#eqn_alpha_B13). Excluding the regime of $\log(\alpha_\mathrm{CO}) \gtrsim 0.65$ where enforces a MW-like $\alpha_\mathrm{CO}$ value with $\gamma = 0$ (which also corresponds to the low-confidence regime of our $\Delta v$-based prescription), the two prescriptions show an overall match with a $\sim$0.5 dex scatter. Despite a significant scatter, this general agreement may indicate that $\Delta v$ and $\Sigma_\mathrm{star}$ are tracing the same physical process that drives $\alpha_\mathrm{CO}$ variations. A likely scenario is that $\Delta v$ is set by the additional gravitational potential from stellar components, which can thus be tracked by $\Sigma_\mathrm{star}$ (see and ). It is also possible that $\Delta v$ is a proxy of molecular gas surface densities and/or local CO intensities which could also reflect opacity and $\alpha_\mathrm{CO}$ changes, as previous studies have found good correlations between these properties (cite: 2022AJ....164...43S).

The prescription was mostly based on $\alpha_\mathrm{CO}$ measurements that were independent from ours and included several U/LIRGs in their sample, and the $\sim$0.5 dex scatter with our prescription is also consistent with the uncertainty estimated by . Therefore, the rough agreement seen in Figure [2](#fig:compare-B13)(a) may also provide additional evidence for the validity of our proposed prescription. Compared to a $\Sigma_\mathrm{star}$-based prescription, one advantage of using a $\Delta v$-based prescription is that $\Delta v$ straightforwardly traces the optical depth change (cite: 2022ApJ...925...72T; 2023ApJ...950..119T), making it closer to the underlying physics that could control $\alpha_\mathrm{CO}$ variations. Another advantage is that $\Delta v$ can be directly obtained from the CO data. Thus, no ancillary multi-band data are needed to estimate $\alpha_\mathrm{CO}$, which circumvents uncertainties in translating observations into $\Sigma_\mathrm{star}$. We remind readers that our prescription is calibrated to $\langle \Delta v \rangle_\mathrm{150pc}$ in CO (2–1), which is typically consistent with $\langle \Delta v \rangle_\mathrm{150pc}$ in CO (1–0) but may be different from that measured in higher-$J$ CO lines (cite: 2020MNRAS.498.2440Y; 2022ApJ...925...72T; 2023ApJ...950..119T). We also point out that systematic measurements of $\Delta v$ at 150-pc resolutions can be difficult across more extreme starbursts like U/LIRGs (cite: 2019ApJ...882....5W), which are usually more distant and/or more morphologically-disturbed than the galaxies in our sample.

We note that the scaling of $\alpha_\mathrm{CO}$ with $\Delta v$ in Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit) is similar to what would be predicted by simple theoretical arguments. As shown by Equation 8 in (cite: 2020ApJ...903..142G), the excitation temperature ($T_\mathrm{ex}$) under Large Velocity Gradient approximation with assumptions of a two-level optically-thick system can be written as

$$\begin{equation}
T_\mathrm{ex} \propto \rho_\mathrm{mol}\ \sqrt{\frac{L_\mathrm{mol} \cdot x_\mathrm{CO}}{\Delta v}}~,
\label{eqn_gong20}
\end{equation}$$

where $\rho_\mathrm{mol}$ and $L_\mathrm{mol}$ are the density and size of a CO-emitting molecular cloud, respectively. To first order, we also have $I_\mathrm{CO} \sim T_\mathrm{ex} \cdot \Delta v$ from the cloud. Thus, combining Equation [\[def_alphaCO\]](#def_alphaCO) with Equation [\[eqn_gong20\]](#eqn_gong20), we obtain

$$\begin{equation}
\alpha_\mathrm{CO} = \frac{\Sigma_\mathrm{mol}}{I_\mathrm{CO}} \sim \frac{\rho_\mathrm{mol} \cdot L_\mathrm{mol}}{T_\mathrm{ex} \cdot \Delta v}
\propto \sqrt{\frac{L_\mathrm{mol}}{x_\mathrm{CO} \cdot \Delta v}}~.
\label{eqn_dv_theory}
\end{equation}$$

The resulting $\alpha_\mathrm{CO}$ dependence on the inverse square root of $\Delta v$ is similar to the fits in Figure [1](#fig:dust-aco). While the fitted slope for $\langle \Delta v \rangle_\mathrm{150pc}$ (Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit)) is slightly steeper than -0.5, we emphasize that the above calculation is highly simplified and is only for providing an intuitive check with theoretical expectations.

## Star Formation Efficiency in Galaxy Centers

As $\alpha_\mathrm{CO}$ determines the total molecular gas surface density ($\Sigma_\mathrm{mol}$, in units of M$_\odot$ pc$^{-2}$), the variation of $\alpha_\mathrm{CO}$ directly affects the estimation of molecular gas depletion time ($t_\mathrm{dep}$) or SFE ($=1/t_\mathrm{dep}$):

$$\begin{equation}
 \label{eqn_sfe}
t_\mathrm{dep} = \Sigma_\mathrm{mol}\ /\ \Sigma_\mathrm{SFR} = \alpha_\mathrm{CO} \cdot I_\mathrm{CO}\ /\ \Sigma_\mathrm{SFR}~. \\
\end{equation}$$ While we examine only the SFE in this work, we note that the impact of $\alpha_\mathrm{CO}$ on estimating the SFE per molecular cloud free-fall time is even more significant, as $\alpha_\mathrm{CO}$ also affects the assessment of cloud density which changes the free-fall time (cite: 2023arXiv231006501Q; 2023ApJ...945L..19S). Motivated by the clear trend of galaxy centers having lower $\alpha_\mathrm{CO}$ values (Figures [1](#fig:dust-aco)(a) and [2](#fig:compare-B13)(a)), we derive $t_\mathrm{dep}$ for the 12 galaxy centers with $\alpha_\mathrm{CO}$ measurements (; ), using kpc-scale $\Sigma_\mathrm{SFR}$ and $I_\mathrm{CO(2-1)}$ (see Table [\[tab:sample\]](#tab:sample)). Then, we examine how $t_\mathrm{dep}$ in galaxy centers derived from the measured $\alpha_\mathrm{CO}$ would differ from that using the standard MW $\alpha_\mathrm{CO}$ of 4.35 (or 6.7 in terms of $\alpha_\mathrm{CO(2-1)}$) $\mathrm{M_\odot\ (K~km~s^{-1}~pc^2)^{-1}}$.

Figure [2](#fig:compare-B13)(b) presents histograms of $t_\mathrm{dep}$ for the 12 galaxy centers. For the histogram using the measured $\alpha_\mathrm{CO}$, we separate barred and non-barred galaxies with different colors. We find that the median $t_\mathrm{dep}$ with the MW $\alpha_\mathrm{CO}$ is 4–5 times longer than that with the measured $\alpha_\mathrm{CO}$. Furthermore, adopting the MW $\alpha_\mathrm{CO}$ results in a similar $t_\mathrm{dep}$ of $\sim$3 Gyr between barred and non-barred centers. In contrast, if the measured $\alpha_\mathrm{CO}$ is used, the median $t_\mathrm{dep}$ of barred and non-barred centers becomes 0.6 Gyr and 2.0 Gyr, respectively, differing by more than a factor of three. This suggests that SFE in barred galaxy centers tend to be higher than non-barred galaxy centers, and that using a constant $\alpha_\mathrm{CO}$ can obscure such a trend.

![image](Figures/KSlaw_phangs_Teng_contour_samex.pdf)\
(a)

![image](Figures/KSlaw_phangs_MW_contour.pdf)\
(b)

![image](Figures/hist_vdisp_phangs_centers.pdf)\

![image](Figures/hist_tdep_phangs_centers_MWvsTeng_medians.pdf)\

![image](Figures/hist_tdep_phangs_centers_ZvsB13_medians.pdf)\

\

![image](Figures/hist_vdisp_phangs_disks.pdf)\

![image](Figures/hist_tdep_phangs_disks_MWvsTeng_medians.pdf)\

![image](Figures/hist_tdep_phangs_disks_ZvsB13_medians.pdf)\

## Systematic Impact on Star Formation Efficiency

With the PHANGS sample (Table [\[tab:sample\]](#tab:sample)), we investigate the impact of different $\alpha_\mathrm{CO}$ prescriptions on SFE or $t_\mathrm{dep}$ in the centers and disks of barred and non-barred galaxies. Figure [3](#fig:ks-relation) shows the molecular Kennicutt-Schmidt (mKS) relation across all 65 galaxies measured at the 1.5-kpc scale, comparing $\Sigma_\mathrm{mol}$ determined from our $\alpha_\mathrm{CO}$ prescription (Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit)) with that determined using a MW $\alpha_\mathrm{CO}$. It is clear that adopting the MW $\alpha_\mathrm{CO}$ results in a wider range of $\Sigma_\mathrm{mol}$ with values reaching $> 1000$ M$_\odot$ pc$^{-2}$ in galaxy centers, while our prescription suggests $\Sigma_\mathrm{mol} < 200$ M$_\odot$ pc$^{-2}$ in general. Furthermore, our prescription reveals a trend of higher SFE towards higher $\Sigma_\mathrm{mol}$, which steepens the mKS relation for galaxy centers and other high-$\Sigma_\mathrm{mol}$ regions. With the MW $\alpha_\mathrm{CO}$, however, both galaxy centers and disks exhibit a roughly constant SFE. These results show that $\alpha_\mathrm{CO}$ and $\Sigma_\mathrm{mol}$ in galaxy centers may overall be overestimated by a factor of 5 with the MW $\alpha_\mathrm{CO}$, and that the choice of $\alpha_\mathrm{CO}$ greatly affects our understanding of galactic-scale star formation.

Figure [4](#fig:all-phangs) presents histograms of velocity dispersion and $t_\mathrm{dep}$ across the PHANGS sample, separating centers (upper panels) and disks (lower panels) for barred (blue) and non-barred (green) galaxies. In non-barred galaxy centers, $\langle \Delta v \rangle_\mathrm{150pc}$ is typically $< 10$ km s$^{-1}$, while barred centers span a significantly wider range up to $\sim$40 km s$^{-1}$. On the other hand, barred and non-barred disks show consistent velocity dispersion, with $\langle \Delta v \rangle_\mathrm{150pc}$ typically below 5 km s$^{-1}$ but reaching up to 10 km s$^{-1}$. These distributions agree with (cite: 2020ApJ...901L...8S), who reported similar $\Delta v$ between galaxy disks and non-barred centers but an overall $\sim$5 times higher $\Delta v$ in barred centers.

We then examine the distribution of $t_\mathrm{dep}$ derived with different $\alpha_\mathrm{CO}$ prescriptions. Using our $\Delta v$-based prescription, we find distinctly different $t_\mathrm{dep}$ between barred and non-barred centers, with the mean/median of $t_\mathrm{dep}$ in barred galaxy centers ($\sim$700 Myr) being 3 times shorter than in non-barred centers (${\sim}2.1$ Gyr). The 16th–84th percentile ranges for $t_\mathrm{dep}$ in barred and non-barred centers is 0.3–1.6 and 0.8–3.6 Gyr, respectively. In contrast, all other prescriptions result in $< 0.2$ dex difference between the median $t_\mathrm{dep}$ of the two types of systems. Such a small difference between barred and non-barred centers is even true for the prescription which shows similarly short $t_\mathrm{dep}$ for all galaxy centers that generally matches our results. Particularly, the MW $\alpha_\mathrm{CO}$ leads to two completely overlapping $t_\mathrm{dep}$ distributions, overestimating the overall $t_\mathrm{dep}$ in barred galaxy centers by a factor of 3–4 if compared to our results. As for the disks, the median of $t_\mathrm{dep}$ remains consistent at 2–3 Gyr across all four prescriptions, while it is found to be systematically lower in barred galaxies than in non-barred galaxies by $\sim$0.1 dex.

Notably, our prescription reveals short $t_\mathrm{dep}$ down to $\lesssim$100 Myr in some barred galaxy centers, which is not seen with other prescriptions. Such a short time scale is supported by recent simulations of galaxy centers including effects from bar-driven inflows (cite: 2019MNRAS.490.4401A; 2020MNRAS.497.5024S; 2021ApJ...914....9M). In addition, we note that the overall $t_\mathrm{dep}$ for galaxy centers is similar between our result and ’s, both suggesting $t_\mathrm{dep} \sim$1 Gyr which is shorter than the disks value of $\sim$3 Gyr. This factor-of-three difference between centers and disks is consistent with recent simulations (cite: 2020MNRAS.492.2973T). However, using the MW or $Z$-based $\alpha_\mathrm{CO}$ for galaxy centers obscures such difference and leads to similar $t_\mathrm{dep}$ across entire galaxies.

# Discussion

The correlation of $\alpha_\mathrm{CO}$ with $\sim$100-pc scale velocity dispersion with only a $\sigma \sim 0.1$ dex scatter (see Section [3.1](#subsec:prescription)), contrary to $\sim$0.3 dex or larger scatter using $Z$- and/or $\Sigma_\mathrm{star}$-based prescriptions, shows that velocity dispersion is an excellent observational tracer for $\alpha_\mathrm{CO}$ variations in star-forming galaxies. The rationale behind such a strong relation may be that $\Delta v$ directly traces the optical depth changes that are the dominant effect responsible for altering $\alpha_\mathrm{CO}$ across these galaxies, as it has been shown that opacity variation is the primary driver of $\alpha_\mathrm{CO}$ in various galaxy centers (cite: 2020A&A...635A.131I; 2022ApJ...925...72T; 2023ApJ...950..119T). However, effects of CO-dark gas and CO excitation can also be important to explain $\alpha_\mathrm{CO}$ variations across the galaxy disks, which have therefore motivated previous $\alpha_\mathrm{CO}$ prescriptions based on metallicity and/or CO integrated intensity (cite: 2012MNRAS.421.3127N; 2015A&A...583A.114H; 2016A&A...588A..23A; 2017MNRAS.464.3315A; 2020ApJ...903..142G).

As discussed in Section [3.2](#subsec:implication), the correlation of $\alpha_\mathrm{CO}$ with metallicity ($Z'$) is indirectly included in the dependence with $\Delta v$ because both $Z'$ and $\Delta v$ vary with galactocentric radius and are thus correlated. Furthermore, statistical studies on molecular cloud properties have shown that velocity dispersion also correlates well with molecular gas surface density and the CO integrated intensity across galaxy disks (cite: 2009ApJ...699.1092H; 2020ApJ...901L...8S; 2022AJ....164...43S; 2021MNRAS.502.1218R). Therefore, it is likely that our $\Delta v$-based prescription contains opacity variations and metallicity gradients as well as the physics of the $\alpha_\mathrm{CO}$–$I_\mathrm{CO}$ correlation suggested by simulation studies (cite: 2012MNRAS.421.3127N; 2020ApJ...903..142G; 2022ApJ...931...28H). This means that the proposed prescription (Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit)) may incorporate more than one piece of physics into a single scaling relation, which could explain why the trend holds across different galactic environments. We also note that metallicity effects on $\alpha_\mathrm{CO}$ should be more drastic in low-metallicity dwarf galaxies due to the lack of dust shielding that can prevent CO from dissociation, and thus metallicity variations being included in our $\Delta v$-based prescription might only be true in the context of MW-like star-forming disk galaxies as represented by the PHANGS sample.

In Sections [3.3](#subsec:sfe_centers) and [3.4](#subsec:sfe), our prescription (based on the dust $\alpha_\mathrm{CO}$ measurements) suggests lower $\alpha_\mathrm{CO}$ in barred galaxy centers that lead to higher SFE than non-barred centers and the disks. This low $\alpha_\mathrm{CO}$ and high SFE in barred centers imply that the amount of molecular gas can be overestimated by previous studies due to inaccurate $\alpha_\mathrm{CO}$ or the assumption of a constant SFE. By comparing the derived $\Sigma_\mathrm{mol}$ under different $\alpha_\mathrm{CO}$ assumptions for all galaxies in Table [\[tab:sample\]](#tab:sample), we find that the median $\Sigma_\mathrm{mol}$ of barred centers is 3 times higher than that of non-barred centers if using a MW-like $\alpha_\mathrm{CO}$. On the other hand, our $\alpha_\mathrm{CO}$ prescription results in only 1.3 times higher $\Sigma_\mathrm{mol}$ in barred centers. Therefore, it is likely that the enhanced SFE is a more important factor causing high SFR observed in barred galaxy centers, compared to an increased amount of molecular gas driven inwards by bars.

Recent studies using $\alpha_\mathrm{CO}$ prescriptions from (cite: 2012MNRAS.421.3127N) or also show that barred galaxies tend to have higher central gas concentration than non-barred galaxies, although the degree of concentration is not as significant as using a constant $\alpha_\mathrm{CO}$ (cite: 1999ApJ...525..691S; 2005ApJ...632..217S; 2006ApJ...649..181S; 2007PASJ...59..117K). Such accumulation of gas towards the centers can increase SFR in barred centers, and it is consistent with the theoretical expectation that non-axisymmetric gravitational potential from bars can induce gas inflows and transport more gas into galaxy centers (cite: 1995MNRAS.277..433W; 2004ApJ...600..595R; 2012ApJ...747...60K; 2020MNRAS.499.4455T). Bars thus influence the secular evolution of galaxies by redistributing molecular gas mass and angular momentum (cite: 2004ARA&A..42..603K).

Studies have also shown that if $\alpha_\mathrm{CO}$ changes were treated properly, starbursts in galaxy centers and variations of SFRs across nearby galaxies are primarily driven by higher SFE rather than increased molecular gas fraction (cite: 2013AJ....146...19L; 2020MNRAS.492.6027E; 2020MNRAS.493L..39E; 2023arXiv230203044D). This is contrary to studies using constant, $Z$-based, or $\Sigma_\mathrm{star}$-based $\alpha_\mathrm{CO}$, which resulted in similar SFE between barred and non-barred galaxies (cite: 2012ApJ...758...73S; 2021A&A...656A.133Q). With our proposed $\alpha_\mathrm{CO}$ prescription, we find enhanced SFE in barred centers, which could originate from variations in molecular gas distribution, density structure, or dynamical effects of turbulence and shocks powered by stellar feedback (cite: 2009A&A...508L..35K; 2012ApJ...760L..16R; 2023ApJ...944L..19L). However, these factors driving SFE variations are the same ones that can alter CO emissivity and $\alpha_\mathrm{CO}$. Therefore, only with accurate $\alpha_\mathrm{CO}$ values can we disentangle SFE from $\alpha_\mathrm{CO}$ and unravel the physical drivers of SFR. Using the latest and best possible measurements of $\alpha_\mathrm{CO}$ and molecular gas properties across a sample of nearby galaxies, our work lays a foundation for benchmarking $\alpha_\mathrm{CO}$ calibration in star-forming galaxies (including starbursting galaxy centers) and allows for further investigation on SFE, SFE per cloud free-fall time, or other related properties that can improve our knowledge of galaxy evolution.

# Conclusions

We construct a new $\alpha_\mathrm{CO}$ prescription applicable to star-forming galaxies, where CO emissivity variations are critical in altering $\alpha_\mathrm{CO}$. The prescription is a major step towards precise calibration of $\alpha_\mathrm{CO}$ across galaxies, and it reveals unprecedented trends in star formation properties which may have been obscured by previous $\alpha_\mathrm{CO}$ prescriptions. Our key results are summarized as follows:

1.  The strong anti-correlation between measured $\alpha_\mathrm{CO}$ and CO velocity dispersion ($\Delta v$) at $\sim$100-pc scales shows that $\Delta v$ is useful for predicting $\alpha_\mathrm{CO}$, and it suggests that CO opacity altered by $\Delta v$ changes or other correlated properties of the molecular gas across the entire galaxies are primary drivers of $\alpha_\mathrm{CO}$ in star-forming galaxies.

2.  The proposed $\alpha_\mathrm{CO}$ prescription (Equation [\[eqn_ew21_fit\]](#eqn_ew21_fit)) is applicable to regions with metallicity above $0.6\ Z_\odot$ and $\langle \Delta v \rangle_\mathrm{150pc} \gtrsim 3$ km s$^{-1}$. The expected scatter in $\alpha_\mathrm{CO}$ is $\sigma \sim 0.1$ dex, which is a substantial improvement over existing $\alpha_\mathrm{CO}$ prescriptions. Our $\Delta v$-based prescription has the advantage of connecting directly to the physical causes of $\alpha_\mathrm{CO}$ change (e.g., CO opacity) as well as requiring only the CO observations which is most relevant to tracing molecular gas.

3.  With the measured $\alpha_\mathrm{CO}$, we find distinctly shorter molecular gas depletion time ($t_\mathrm{dep}$) in barred galaxy centers than non-barred galaxy centers, as well as a generally shorter $t_\mathrm{dep}$ in galaxy centers than the disks. In contrast, assuming a constant MW $\alpha_\mathrm{CO}$ results in $t_\mathrm{dep} \sim3$ Gyr for all regions, which underestimates the star formation efficiency (SFE) in galaxy centers and also obscures the difference between barred and non-barred galaxies.

4.  Our prescription reveals short $t_\mathrm{dep}$ down to 100 Myr in barred galaxy centers, with the median $t_\mathrm{dep}$ (0.7$^{+0.9}_{-0.4}$ Gyr) being 3 times shorter than in non-barred galaxy centers (2.1$^{+1.5}_{-1.3}$ Gyr). However, all other prescriptions (MW, metallicity-based, and ) show $< 0.2$ dex difference between the two regions, even if results in an overall shorter $t_\mathrm{dep}$ for galaxy centers which aligns better with our results. Thus, SFE in barred galaxy centers may be underestimated by a factor of three or more in previous studies due to $\alpha_\mathrm{CO}$ uncertainties.

5.  All four prescriptions tested in this work show similar $t_\mathrm{dep}$ of 2–3 Gyr in the disk regions and non-barred galaxy centers across the PHANGS sample, which is in good agreement with previous literature (cite: 2008AJ....136.2782L; 2011MNRAS.415...61S; 2023ApJ...945L..19S).

This work was carried out as part of the PHANGS collaboration. Y.-H.T. and K.S. acknowledge funding support from NRAO Student Observing Support Grant SOSPADA-012 and from the National Science Foundation (NSF) under grant No. 2108081. Y.-H.T. also acknowledges support by the Ministry of Education of Taiwan through Government Scholarship to Study Abroad. J.S. acknowledges support by the Natural Sciences and Engineering Research Council of Canada (NSERC) through a Canadian Institute for Theoretical Astrophysics (CITA) National Fellowship. KG is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship (project number DE220100766) funded by the Australian Government. KG is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. HAP acknowledges support by the National Science and Technology Council of Taiwan under grant 110-2112-M-032-020-MY3. MB gratefully acknowledges support from the ANID BASAL project FB210003 and from the FONDECYT regular grant 1211000. IC thanks the National Science and Technology Council for support through grant 111-2112-M-001-038-MY3, and the Academia Sinica for Investigator Award AS-IA-109-M02. JC acknowledges funding from the Belgian Science Policy Office (BELSPO) through the PRODEX project “JWST/MIRI Science exploitation” (C4000142239). MC gratefully acknowledges funding from the DFG through an Emmy Noether Research Group (grant number CH2137/1-1). COOL Research DAO is a Decentralized Autonomous Organization supporting research in astrophysics aimed at uncovering our cosmic origins. SKS acknowledges financial support from the German Research Foundation (DFG) via Sino-German research grant SCHI 536/11-1. AU acknowledges support from the Spanish grant PID2019-108765GB-I00, funded by MCIN/AEI/10.13039/501100011033. J. D. H. gratefully acknowledges financial support from the Royal Society (University Research Fellowship; URF/R1/221620).

This paper makes use of the following ALMA data:\
ADS/JAO.ALMA#2012.1.00650.S,\
ADS/JAO.ALMA#2013.1.00803.S,\
ADS/JAO.ALMA#2013.1.01161.S,\
ADS/JAO.ALMA#2015.1.00925.S,\
ADS/JAO.ALMA#2015.1.00956.S,\
ADS/JAO.ALMA#2017.1.00392.S,\
ADS/JAO.ALMA#2017.1.00766.S,\
ADS/JAO.ALMA#2017.1.00886.L,\
ADS/JAO.ALMA#2018.1.01321.S,\
ADS/JAO.ALMA#2018.1.01651.S.\
ADS/JAO.ALMA#2018.A.00062.S.\
ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This work is based in part on data products from the Wide-field Infrared Survey Explorer(cite: 2010AJ....140.1868W), which is a joint project of the University of California, Los Angeles, and the Jet Propulsion Laboratory/California Institute of Technology, funded by the National Aeronautics and Space Administration. We acknowledge the usage of the SAO/NASA Astrophysics Data System.

# Facilities

ALMA, WISE, Herschel, VLA

# Software

`matplotlib` (cite: Hunter:2007), `numpy` (cite: harris2020array), `scipy` (cite: Virtanen_2020), `astropy` (cite: 2013A&A...558A..33A; 2018AJ....156..123A), `ipython` (cite: PER-GRA:2007)

natexlab

(ref: 2017MNRAS.464.3315A) Accurso, G., Saintonge, A., Bisbas, T. G., & Viti, S. 2017, MNRAS, 464, 3315, doi: [`10.1093/mnras/stw2580`](http://doi.org/10.1093/mnras/stw2580)

(ref: 2012ApJ...750....3A) Ackermann, M., Ajello, M., Atwood, W. B., et al. 2012, ApJ, 750, 3, doi: [`10.1088/0004-637X/750/1/3`](http://doi.org/10.1088/0004-637X/750/1/3)

(ref: 2016A&A...588A..23A) Amorı́n, R., Muñoz-Tuñón, C., Aguerri, J. A. L., & Planesas, P. 2016, A&A, 588, A23, doi: [`10.1051/0004-6361/201526397`](http://doi.org/10.1051/0004-6361/201526397)

(ref: 2021MNRAS.501.3621A) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: 2019MNRAS.490.4401A) Armillotta, L., Krumholz, M. R., Di Teodoro, E. M., & McClure-Griffiths, N. M. 2019, MNRAS, 490, 4401, doi: [`10.1093/mnras/stz2880`](http://doi.org/10.1093/mnras/stz2880)

(ref: 2013A&A...558A..33A) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2008AJ....136.2846B) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846, doi: [`10.1088/0004-6256/136/6/2846`](http://doi.org/10.1088/0004-6256/136/6/2846)

(ref: co-to-h2) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: 2023arXiv231100407C) Chiang, I.-D., Sandstrom, K. M., Chastenet, J., et al. 2023, arXiv e-prints, arXiv:2311.00407, doi: [`10.48550/arXiv.2311.00407`](http://doi.org/10.48550/arXiv.2311.00407)

(ref: 2018ApJ...863..143C) Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018, ApJ, 863, 143, doi: [`10.3847/1538-4357/aad32a`](http://doi.org/10.3847/1538-4357/aad32a)

(ref: 2018MNRAS.475.3909C) Cormier, D., Bigiel, F., Jiménez-Donaire, M. J., et al. 2018, MNRAS, 475, 3909, doi: [`10.1093/mnras/sty059`](http://doi.org/10.1093/mnras/sty059)

(ref: 2022MNRAS.512.1522D) Davis, T. A., Gensior, J., Bureau, M., et al. 2022, MNRAS, 512, 1522, doi: [`10.1093/mnras/stac600`](http://doi.org/10.1093/mnras/stac600)

(ref: 2019A&A...623A...5D) De Vis, P., Jones, A., Viaene, S., et al. 2019, A&A, 623, A5, doi: [`10.1051/0004-6361/201834444`](http://doi.org/10.1051/0004-6361/201834444)

(ref: 2023arXiv230203044D) den Brok, J. S., Bigiel, F., Chastenet, J., et al. 2023, arXiv e-prints, arXiv:2302.03044, doi: [`10.48550/arXiv.2302.03044`](http://doi.org/10.48550/arXiv.2302.03044)

(ref: 1998ApJ...507..615D) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615, doi: [`10.1086/306339`](http://doi.org/10.1086/306339)

(ref: 2011piim.book.....D) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: 2021MNRAS.501.4777E) Ellison, S. L., Lin, L., Thorp, M. D., et al. 2021a, MNRAS, 501, 4777, doi: [`10.1093/mnras/staa3822`](http://doi.org/10.1093/mnras/staa3822)

(ref: 2020MNRAS.492.6027E) Ellison, S. L., Thorp, M. D., Pan, H.-A., et al. 2020a, MNRAS, 492, 6027, doi: [`10.1093/mnras/staa001`](http://doi.org/10.1093/mnras/staa001)

(ref: 2020MNRAS.493L..39E) Ellison, S. L., Thorp, M. D., Lin, L., et al. 2020b, MNRAS, 493, L39, doi: [`10.1093/mnrasl/slz179`](http://doi.org/10.1093/mnrasl/slz179)

(ref: 2021MNRAS.505L..46E) Ellison, S. L., Wong, T., Sánchez, S. F., et al. 2021b, MNRAS, 505, L46, doi: [`10.1093/mnrasl/slab047`](http://doi.org/10.1093/mnrasl/slab047)

(ref: 2022ApJ...931...92E) Esteban, C., Méndez-Delgado, J. E., Garcı́a-Rojas, J., & Arellano-Córdova, K. Z. 2022, ApJ, 931, 92, doi: [`10.3847/1538-4357/ac6b38`](http://doi.org/10.3847/1538-4357/ac6b38)

(ref: 2012ApJ...746...69G) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69, doi: [`10.1088/0004-637X/746/1/69`](http://doi.org/10.1088/0004-637X/746/1/69)

(ref: 2020ApJ...903..142G) Gong, M., Ostriker, E. C., Kim, C.-G., & Kim, J.-G. 2020, ApJ, 903, 142, doi: [`10.3847/1538-4357/abbdab`](http://doi.org/10.3847/1538-4357/abbdab)

(ref: harris2020array) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: 2019A&A...628A..71H) Herrero-Illana, R., Privon, G. C., Evans, A. S., et al. 2019, A&A, 628, A71, doi: [`10.1051/0004-6361/201834088`](http://doi.org/10.1051/0004-6361/201834088)

(ref: 2009ApJ...699.1092H) Heyer, M., Krawczyk, C., Duval, J., & Jackson, J. M. 2009, ApJ, 699, 1092, doi: [`10.1088/0004-637X/699/2/1092`](http://doi.org/10.1088/0004-637X/699/2/1092)

(ref: 2022ApJ...931...28H) Hu, C.-Y., Schruba, A., Sternberg, A., & van Dishoeck, E. F. 2022, ApJ, 931, 28, doi: [`10.3847/1538-4357/ac65fd`](http://doi.org/10.3847/1538-4357/ac65fd)

(ref: 2015A&A...583A.114H) Hunt, L. K., Garcı́a-Burillo, S., Casasola, V., et al. 2015, A&A, 583, A114, doi: [`10.1051/0004-6361/201526553`](http://doi.org/10.1051/0004-6361/201526553)

(ref: Hunter:2007) Hunter, J. D. 2007, Computing In Science & Engineering, 9, 90

(ref: 1997A&A...328..471I) Israel, F. P. 1997, A&A, 328, 471. [`https://arxiv.org/abs/astro-ph/9709194`](https://arxiv.org/abs/astro-ph/9709194)

(ref: 2020A&A...635A.131I) —. 2020, A&A, 635, A131, doi: [`10.1051/0004-6361/201834198`](http://doi.org/10.1051/0004-6361/201834198)

(ref: 2023A&A...671A...3J) Jiménez-Donaire, M. J., Brown, T., Wilson, C. D., et al. 2023, A&A, 671, A3, doi: [`10.1051/0004-6361/202244718`](http://doi.org/10.1051/0004-6361/202244718)

(ref: 2009A&A...508L..35K) Kainulainen, J., Beuther, H., Henning, T., & Plume, R. 2009, A&A, 508, L35, doi: [`10.1051/0004-6361/200913605`](http://doi.org/10.1051/0004-6361/200913605)

(ref: 1998ApJ...498..541K) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: 2012ApJ...747...60K) Kim, W.-T., Seo, W.-Y., Stone, J. M., Yoon, D., & Teuben, P. J. 2012, ApJ, 747, 60, doi: [`10.1088/0004-637X/747/1/60`](http://doi.org/10.1088/0004-637X/747/1/60)

(ref: 2023ApJ...949..108K) Koda, J., Hirota, A., Egusa, F., et al. 2023, ApJ, 949, 108, doi: [`10.3847/1538-4357/acc65e`](http://doi.org/10.3847/1538-4357/acc65e)

(ref: 2004ARA&A..42..603K) Kormendy, J., & Kennicutt, Robert C., J. 2004, ARA&A, 42, 603, doi: [`10.1146/annurev.astro.42.053102.134024`](http://doi.org/10.1146/annurev.astro.42.053102.134024)

(ref: 2019ApJ...887...80K) Kreckel, K., Ho, I. T., Blanc, G. A., et al. 2019, ApJ, 887, 80, doi: [`10.3847/1538-4357/ab5115`](http://doi.org/10.3847/1538-4357/ab5115)

(ref: 2017ApJ...850...77K) Krieger, N., Ott, J., Beuther, H., et al. 2017, ApJ, 850, 77, doi: [`10.3847/1538-4357/aa951c`](http://doi.org/10.3847/1538-4357/aa951c)

(ref: 2015arXiv151103457K) Krumholz, M. R. 2015, arXiv e-prints, arXiv:1511.03457, doi: [`10.48550/arXiv.1511.03457`](http://doi.org/10.48550/arXiv.1511.03457)

(ref: 2007PASJ...59..117K) Kuno, N., Sato, N., Nakanishi, H., et al. 2007, PASJ, 59, 117, doi: [`10.1093/pasj/59.1.117`](http://doi.org/10.1093/pasj/59.1.117)

(ref: 2020ApJ...897..122L) Lang, P., Meidt, S. E., Rosolowsky, E., et al. 2020, ApJ, 897, 122, doi: [`10.3847/1538-4357/ab9953`](http://doi.org/10.3847/1538-4357/ab9953)

(ref: 2008AJ....136.2782L) Leroy, A. K., Walter, F., Brinks, E., et al. 2008, AJ, 136, 2782, doi: [`10.1088/0004-6256/136/6/2782`](http://doi.org/10.1088/0004-6256/136/6/2782)

(ref: 2011ApJ...737...12L) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12, doi: [`10.1088/0004-637X/737/1/12`](http://doi.org/10.1088/0004-637X/737/1/12)

(ref: 2013AJ....146...19L) Leroy, A. K., Walter, F., Sandstrom, K., et al. 2013, AJ, 146, 19, doi: [`10.1088/0004-6256/146/2/19`](http://doi.org/10.1088/0004-6256/146/2/19)

(ref: 2021ApJS..257...43L) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: 2023ApJ...944L..19L) Liu, D., Schinnerer, E., Cao, Y., et al. 2023, ApJL, 944, L19, doi: [`10.3847/2041-8213/aca973`](http://doi.org/10.3847/2041-8213/aca973)

(ref: 2022MNRAS.514.5035L) Lu, A., Boyce, H., Haggard, D., et al. 2022, MNRAS, 514, 5035, doi: [`10.1093/mnras/stac1583`](http://doi.org/10.1093/mnras/stac1583)

(ref: 2020A&A...643A.141M) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141, doi: [`10.1051/0004-6361/202038860`](http://doi.org/10.1051/0004-6361/202038860)

(ref: 2023ApJ...943....7M) Maeda, F., Egusa, F., Ohta, K., Fujimoto, Y., & Habe, A. 2023, ApJ, 943, 7, doi: [`10.3847/1538-4357/aca664`](http://doi.org/10.3847/1538-4357/aca664)

(ref: 2021ApJ...914....9M) Moon, S., Kim, W.-T., Kim, C.-G., & Ostriker, E. C. 2021, ApJ, 914, 9, doi: [`10.3847/1538-4357/abfa93`](http://doi.org/10.3847/1538-4357/abfa93)

(ref: 2019PASJ...71S..15M) Muraoka, K., Sorai, K., Miyamoto, Y., et al. 2019, PASJ, 71, S15, doi: [`10.1093/pasj/psz015`](http://doi.org/10.1093/pasj/psz015)

(ref: 2012MNRAS.421.3127N) Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, MNRAS, 421, 3127, doi: [`10.1111/j.1365-2966.2012.20536.x`](http://doi.org/10.1111/j.1365-2966.2012.20536.x)

(ref: 2012ApJ...751...10P) Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak, K. G., & Gao, Y. 2012, ApJ, 751, 10, doi: [`10.1088/0004-637X/751/1/10`](http://doi.org/10.1088/0004-637X/751/1/10)

(ref: PER-GRA:2007) Pérez, F., & Granger, B. E. 2007, Computing in Science and Engineering, 9, 21, doi: [`10.1109/MCSE.2007.53`](http://doi.org/10.1109/MCSE.2007.53)

(ref: 2021A&A...650A.134P) Pessa, I., Schinnerer, E., Belfiore, F., et al. 2021, A&A, 650, A134, doi: [`10.1051/0004-6361/202140733`](http://doi.org/10.1051/0004-6361/202140733)

(ref: 2004MNRAS.348L..59P) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59, doi: [`10.1111/j.1365-2966.2004.07591.x`](http://doi.org/10.1111/j.1365-2966.2004.07591.x)

(ref: 2016MNRAS.457.3678P) Pilyugin, L. S., & Grebel, E. K. 2016, MNRAS, 457, 3678, doi: [`10.1093/mnras/stw238`](http://doi.org/10.1093/mnras/stw238)

(ref: 2021ApJS..256....3P) Pitts, R. L., & Barnes, P. J. 2021, ApJS, 256, 3, doi: [`10.3847/1538-4365/ac063d`](http://doi.org/10.3847/1538-4365/ac063d)

(ref: 2023arXiv231006501Q) Querejeta, M., Pety, J., Schruba, A., et al. 2023, arXiv e-prints, arXiv:2310.06501, doi: [`10.48550/arXiv.2310.06501`](http://doi.org/10.48550/arXiv.2310.06501)

(ref: 2021A&A...656A.133Q) Querejeta, M., Schinnerer, E., Meidt, S., et al. 2021, A&A, 656, A133, doi: [`10.1051/0004-6361/202140695`](http://doi.org/10.1051/0004-6361/202140695)

(ref: 2023arXiv230614881R) Ramambason, L., Lebouteiller, V., Madden, S. C., et al. 2023, arXiv e-prints, arXiv:2306.14881, doi: [`10.48550/arXiv.2306.14881`](http://doi.org/10.48550/arXiv.2306.14881)

(ref: 2004ApJ...600..595R) Regan, M. W., & Teuben, P. J. 2004, ApJ, 600, 595, doi: [`10.1086/380116`](http://doi.org/10.1086/380116)

(ref: 2019A&A...621A.104R) Renaud, F., Bournaud, F., Daddi, E., & Weiß, A. 2019, A&A, 621, A104, doi: [`10.1051/0004-6361/201834397`](http://doi.org/10.1051/0004-6361/201834397)

(ref: 2012ApJ...760L..16R) Renaud, F., Kraljic, K., & Bournaud, F. 2012, ApJL, 760, L16, doi: [`10.1088/2041-8205/760/1/L16`](http://doi.org/10.1088/2041-8205/760/1/L16)

(ref: 2021MNRAS.502.1218R) Rosolowsky, E., Hughes, A., Leroy, A. K., et al. 2021, MNRAS, 502, 1218, doi: [`10.1093/mnras/stab085`](http://doi.org/10.1093/mnras/stab085)

(ref: 2022ARA&A..60..319S) Saintonge, A., & Catinella, B. 2022, ARA&A, 60, 319, doi: [`10.1146/annurev-astro-021022-043545`](http://doi.org/10.1146/annurev-astro-021022-043545)

(ref: 2011MNRAS.415...61S) Saintonge, A., Kauffmann, G., Wang, J., et al. 2011, MNRAS, 415, 61, doi: [`10.1111/j.1365-2966.2011.18823.x`](http://doi.org/10.1111/j.1365-2966.2011.18823.x)

(ref: 2012ApJ...758...73S) Saintonge, A., Tacconi, L. J., Fabello, S., et al. 2012, ApJ, 758, 73, doi: [`10.1088/0004-637X/758/2/73`](http://doi.org/10.1088/0004-637X/758/2/73)

(ref: 1999ApJ...525..691S) Sakamoto, K., Okumura, S. K., Ishizuki, S., & Scoville, N. Z. 1999, ApJ, 525, 691, doi: [`10.1086/307910`](http://doi.org/10.1086/307910)

(ref: 2013ApJ...777....5S) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: 2006ApJ...649..181S) Schinnerer, E., Böker, T., Emsellem, E., & Lisenfeld, U. 2006, ApJ, 649, 181, doi: [`10.1086/506265`](http://doi.org/10.1086/506265)

(ref: 2019ApJ...883....2S) Schruba, A., Kruijssen, J. M. D., & Leroy, A. K. 2019, ApJ, 883, 2, doi: [`10.3847/1538-4357/ab3a43`](http://doi.org/10.3847/1538-4357/ab3a43)

(ref: stacking) Schruba, A., Leroy, A. K., Walter, F., et al. 2011, AJ, 142, 37, doi: [`10.1088/0004-6256/142/2/37`](http://doi.org/10.1088/0004-6256/142/2/37)

(ref: 2017ApJ...835..278S) Schruba, A., Leroy, A. K., Kruijssen, J. M. D., et al. 2017, ApJ, 835, 278, doi: [`10.3847/1538-4357/835/2/278`](http://doi.org/10.3847/1538-4357/835/2/278)

(ref: 2022MNRAS.509.2180S) Sharda, P., Menon, S. H., Federrath, C., et al. 2022, MNRAS, 509, 2180, doi: [`10.1093/mnras/stab3048`](http://doi.org/10.1093/mnras/stab3048)

(ref: 2005ApJ...632..217S) Sheth, K., Vogel, S. N., Regan, M. W., Thornley, M. D., & Teuben, P. J. 2005, ApJ, 632, 217, doi: [`10.1086/432409`](http://doi.org/10.1086/432409)

(ref: 2017ApJ...840....8S) Sliwa, K., Wilson, C. D., Matsushita, S., et al. 2017, ApJ, 840, 8, doi: [`10.3847/1538-4357/aa689b`](http://doi.org/10.3847/1538-4357/aa689b)

(ref: 2020MNRAS.497.5024S) Sormani, M. C., Tress, R. G., Glover, S. C. O., et al. 2020, MNRAS, 497, 5024, doi: [`10.1093/mnras/staa1999`](http://doi.org/10.1093/mnras/staa1999)

(ref: 2020ApJ...892..148S) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2020a, ApJ, 892, 148, doi: [`10.3847/1538-4357/ab781c`](http://doi.org/10.3847/1538-4357/ab781c)

(ref: 2020ApJ...901L...8S) Sun, J., Leroy, A. K., Schinnerer, E., et al. 2020b, ApJL, 901, L8, doi: [`10.3847/2041-8213/abb3be`](http://doi.org/10.3847/2041-8213/abb3be)

(ref: 2022AJ....164...43S) Sun, J., Leroy, A. K., Rosolowsky, E., et al. 2022, AJ, 164, 43, doi: [`10.3847/1538-3881/ac74bd`](http://doi.org/10.3847/1538-3881/ac74bd)

(ref: 2023ApJ...945L..19S) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL, 945, L19, doi: [`10.3847/2041-8213/acbd9c`](http://doi.org/10.3847/2041-8213/acbd9c)

(ref: 2022ApJ...925...72T) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2022, ApJ, 925, 72, doi: [`10.3847/1538-4357/ac382f`](http://doi.org/10.3847/1538-4357/ac382f)

(ref: 2023ApJ...950..119T) —. 2023, ApJ, 950, 119, doi: [`10.3847/1538-4357/accb86`](http://doi.org/10.3847/1538-4357/accb86)

(ref: 2020MNRAS.492.2973T) Tress, R. G., Smith, R. J., Sormani, M. C., et al. 2020a, MNRAS, 492, 2973, doi: [`10.1093/mnras/stz3600`](http://doi.org/10.1093/mnras/stz3600)

(ref: 2020MNRAS.499.4455T) Tress, R. G., Sormani, M. C., Glover, S. C. O., et al. 2020b, MNRAS, 499, 4455, doi: [`10.1093/mnras/staa3120`](http://doi.org/10.1093/mnras/staa3120)

(ref: 2017ApJ...849...26U) Utomo, D., Bolatto, A. D., Wong, T., et al. 2017, ApJ, 849, 26, doi: [`10.3847/1538-4357/aa88c0`](http://doi.org/10.3847/1538-4357/aa88c0)

(ref: 2022ApJ...940..176V) Villanueva, V., Bolatto, A. D., Vogel, S., et al. 2022, ApJ, 940, 176, doi: [`10.3847/1538-4357/ac9d3c`](http://doi.org/10.3847/1538-4357/ac9d3c)

(ref: Virtanen_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`https://doi.org/10.1038/s41592-019-0686-2`](http://doi.org/https://doi.org/10.1038/s41592-019-0686-2)

(ref: 1995MNRAS.277..433W) Wada, K., & Habe, A. 1995, MNRAS, 277, 433, doi: [`10.1093/mnras/277.2.433`](http://doi.org/10.1093/mnras/277.2.433)

(ref: 2023MNRAS.525.4270W) Williams, T. G., Bureau, M., Davis, T. A., et al. 2023, MNRAS, 525, 4270, doi: [`10.1093/mnras/stad2455`](http://doi.org/10.1093/mnras/stad2455)

(ref: 2019ApJ...882....5W) Wilson, C. D., Elmegreen, B. G., Bemis, A., & Brunetti, N. 2019, ApJ, 882, 5, doi: [`10.3847/1538-4357/ab31f3`](http://doi.org/10.3847/1538-4357/ab31f3)

(ref: 2010AJ....140.1868W) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868, doi: [`10.1088/0004-6256/140/6/1868`](http://doi.org/10.1088/0004-6256/140/6/1868)

(ref: 2023PASJ...75..743Y) Yasuda, A., Kuno, N., Sorai, K., et al. 2023, PASJ, 75, 743, doi: [`10.1093/pasj/psad034`](http://doi.org/10.1093/pasj/psad034)

(ref: 2020MNRAS.498.2440Y) Yuan, Y., Krumholz, M. R., & Burkhart, B. 2020, MNRAS, 498, 2440, doi: [`10.1093/mnras/staa2432`](http://doi.org/10.1093/mnras/staa2432)

[^1]: $\alpha_\mathrm{CO}$ is defined for the CO $J=1-0$ line in most literature, but it can also be evaluated for other transitions. In this work, when we refer to $\alpha_\mathrm{CO}$, we mean $\alpha_\mathrm{CO(1-0)}$ unless otherwise specified.

[^2]: This is likely due to a large amount of low S/N measurements clustering around $\sim$2.5 km/s, which is the velocity resolution of the PHANGS CO data

[^3]: In this paper, *center* refers to the central $\sim$2 kpc-sized aperture at $R_\mathrm{gal}$=0, and *disks* represents the rest of the measurements.

[^4]: The $Z'$ in the original prescription \[$\alpha_\mathrm{CO} = 4.35 (Z')^{-1.6}$\] was based on the PP04 calibration. Here we convert their prescription to the same (PG16S-based) metallicity scale as we adopt, using an approximate conversion based on (cite: 2019A&A...623A...5D).

[^5]: The original prescription included a molecular cloud surface density term which was assumed at 100 M$_\odot$ pc$^{-2}$. Here we adopt the same value and note that this helps avoid unrealistic $\alpha_\mathrm{CO}$ values in low surface density regions ((cite: 2023ApJ...945L..19S), ).

</paper>

Write the methods card for this paper.