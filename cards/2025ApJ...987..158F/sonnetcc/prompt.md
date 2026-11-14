# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...987..158F\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...987..158F",
 "title": "A Comparative Study of the Ground State Transitions of CO and C I as Molecular Gas Tracers at High Redshift",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Frias Castillo, Marta",
 "n_authors": 25,
 "arxiv_id": "2404.05596",
 "doi": "10.3847/1538-4357/adc4e0",
 "alma_projects_linked_by_archive": [
  "2021.1.01342.S"
 ]
}
```

Paper text:
<paper>
# A Comparative Study of the Ground State Transitions of CO and \[C I\] as Molecular Gas Tracers at High Redshift

## Abstract

The CO(1–0) and \[C I\](1–0) emission lines are well-established tracers of cold molecular gas mass in local galaxies. At high redshift, where the interstellar medium (ISM) is likely to be denser, there have been limited direct comparisons of both ground state transitions. Here we present a study of CO(1–0) and \[C I\](1–0) emission in a sample of 20 unlensed dusty, star-forming galaxies at $z~=~2-5$. The CO(1–0)/\[C I\](1–0) ratio is constant up to at least $z=5$, supporting the use of \[CI\](1-0) as a gas mass tracer. PDR modelling of the available data indicates a median H$_2$ density of log$(n~[$cm$^{-3}])=4.7\pm0.2$, and UV radiation field log$(G_{\mathrm{UV}}~[G_0])=3.2\pm0.2$. We use the CO(1–0), \[C I\](1–0) and 3mm dust continuum measurements to cross–calibrate the respective gas mass conversion factors, finding no dependence of these factors on either redshift or infrared luminosity. Assuming a variable CO conversion factor then implies \[C I\] and dust conversion factors that differ from canonically assumed values but are consistent with the solar/super–solar metallicities expected for our sources. Radiative transfer modelling shows that the warmer CMB at high redshift can significantly affect the \[C I\] as well as CO emission, which can change the derived molecular gas masses by up to 70% for the coldest kinetic gas temperatures expected. Nevertheless, we show that the magnitude of the effect on the ratio of the tracers is within the known scatter of the $L'_\mathrm{CO}-L'_\mathrm{[CI]}$ relation. Further determining the absolute decrease of individual line intensities will require well–sampled spectral line energy distributions (SLEDs) to model the gas excitation conditions in more detail.

# Introduction

The cold gas content of galaxies is expected to be one of the main drivers of the cosmic star formation rate (SFR) density of the Universe. Deep, blind surveys over modest volumes of the cosmic gas density reveal an evolutionary trend resembling that of the cosmic SFR density (cite: decarli2020; walter2020), with both quantities peaking at $z=1-3$. Moreover, the gas fractions of star–forming galaxies have been shown to increase at earlier times (from $\sim$5% at $z\sim$0 to $\sim$50% at $z\sim$3), supporting the fact that the increased availability of molecular gas reservoirs at $z=$1–3 is likely to be the primary factor driving the higher SFRs seen in the early Universe (cite: tacconi2010; tacconi2020; saintonge2013; bethermin2015; decarli2020; dessauges-zavadsky2020; birkin2020).

The main component of the molecular gas, molecular hydrogen (H$_2$), cannot be excited in its rotational/vibrational transitions in the low temperatures of the interstellar medium (ISM) of galaxies due to the large separation between its energy levels ($\sim$500 K). Therefore, studies have traditionally relied on observations of carbon monoxide ($^{12}$CO, hereafter CO) emission lines, particularly the ground $J=1-0$ transition, as an alternative tracer of the cold molecular gas reservoirs of galaxies (cite: solomon2005; hainline2006; frayer2011; ivison2011; harris2012; thompson2012; bothwell2014; saintonge2017; huynh2017). However, this tracer requires the assumption of a CO-to-H$_2$ conversion factor, $\alpha_\mathrm{CO}$, which increases with decreasing metallicity (cite: bolatto2013) and has been suggested to vary between normal, star–forming galaxies and starbursts (cite: downes1998). Due to the lack of sufficient data to independently derive $\alpha_\mathrm{CO}$ in most galaxies, it is often assumed to be bimodal, with $\alpha_\mathrm{CO}\sim$3.6 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for galaxies on the main sequence and $\sim$1 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for ULIRG–like, starburst galaxies (cite: bolatto2013).

Further, due to the technical challenges of detecting the faint CO(1–0) line emission at high redshift, studies of molecular gas at high redshift commonly rely on the brighter mid–$J_\mathrm{up}$ CO lines (cite: bothwell2013; tacconi2013; boogaard2020; decarli2020; birkin2020). Obtaining molecular gas masses from these lines then depends on line excitation corrections that introduce additional uncertainty (cite: bothwell2013; carilli-walter2013; sharon2016; boogaard2020; riechers2020a-vlaspecs; birkin2020; friascastillo2023). At high redshift ($z>$ 3), this is further complicated by the cosmic microwave background (CMB), which acts as an additional excitation source for the gas and reduces the contrast between the background and the CO line emission. This can bias the information derived from line intensity measurements and imaging of the CO gas distribution of high-redshift galaxies (cite: dacunha2013; zhang2016).

A separate way to indirectly estimate molecular gas masses is via the long wavelength dust continuum emission (cite: hildebrand1983; scoville2016; liu2019; kaasinen2019; wang2022). Observations of the dust continuum are generally less observationally expensive, allowing for larger samples to be studied. This method, however, requires the assumption of a mass-weighted cold dust temperature (typically assumed to be $T_\mathrm{dust}$ = 25 K, which is claimed to be a representative value for both local star-forming galaxies and high-redshift galaxies, (cite: scoville2016; scoville2017)), and knowledge (or the assumption) of the gas–to–dust abundance ratio, which is dependent on a number of factors, e.g., optical depth, geometry, galaxy metallicity and dust grain properties (cite: bolatto2013; popping2022; popping2023).

The ground state atomic carbon \[C I\]($^3$P$_1$–$^3$P$_0$) emission line ($\nu_\mathrm{rest}$=492.161 GHz, hereafter \[C I\](1-0)), may provide a promising alternative direct molecular gas tracer (cite: papadopoulos2004; papadopoulos2012; walter2011). Early, simple plane-parallel modeling of star–forming regions predicted that the \[C I\] emission arose only from narrow gas layers between the CO and \[C II\] emitting regions (cite: tielens1985). However, subsequent observational work on nearby galaxies (cite: keene1997; ojha2001; jiao2019) and theoretical work (cite: tomasetti2014) have shown CO and \[C I\] emission to be fully concomitant, with tightly correlated intensities over a wide range of environments. \[C I\] emission is typically found to be optically thin (cite: ikeda2002; weiss2003; harrington2021), which means it can probe high column density environments, while its energy above ground is sufficiently low (24 K) to trace the bulk of the cold gas content, proving itself as a powerful alternative tool to measuring total molecular gas masses. Furthermore, when combined with CO line ratios, the \[C I\] lines reflect ISM properties such as density and UV radiation field strength (cite: hollenbach1999; kaufman2006; alaghband2013; israel2015; bothwell2017; andreani2018; valentino2018; valentino2020).

As with CO(1–0), the warmer CMB can have a significant impact at high redshift, but so far this effect has not been studied observationally.

At high redshift, the \[C I\] emission line luminosity is correlated with that of CO in a variety of galaxy populations, from star–forming galaxies on the main–sequence (cite: popping2017; bourne2019; valentino2018; valentino2020; dunne2022) to more extreme submillimeter galaxies (cite: smail1997; hughes1998; hodge+dacunha2020) and quasar (QSO) hosts at $z\sim2.5$ up to $z\sim4$ (cite: walter2011; alaghband2013; bothwell2017; yang2017; andreani2018; birkin2020; gururajan2023). Many of these studies, however, suffer from one or more of three shortcomings. Firstly, several use galaxy–scale strong gravitationally lensed systems. This introduces potential differential magnification effects and biases studies towards the most extreme sources (cite: yang2017). Second, in many non–lensed galaxies, CO(1–0) is too faint to detect in reasonable exposure times. As a result, the majority of studies rely on $J_\mathrm{up}>2$ CO line observations and need to assume uncertain excitation corrections, which result in uncertainties in the derived CO(1–0) luminosity of up to 0.5 dex (cite: friascastillo2023). Finally, the few studies that have both \[C I\](1–0) and CO(1–0) ground-state transitions have relied on individual, targeted sources (cite: danielson2011), and it is thus challenging to draw statistically significant conclusions. Recently, (cite: dunne2022) compiled all of the available literature studies using CO(1–0), \[C I\](1–0) and dust to provide a cross-calibration for metal-rich galaxies from $z\sim0$ to $z\sim5$, arguing that a single \[C I\]-to-H$_2$ conversion factor is applicable for both main sequence and starburst galaxies. However, the number of unlensed $z>2$ sources with both ground-state CO and \[C I\] observations in their compilation was still $<$10, suggesting the need for further investigation.

+:-------------+:----------:+:-------------:+:-----:+:----------:+:--------------------:+:---------------------------:+:----------------:+:---------------:+
| Target       | R.A.       | Dec           | $z$   | Date       | rms per channel $^a$ | Beam                        | Phase calibrator | Flux calibrator |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
|              | \[J2000\]  | \[J2000\]     |       |            | \[mJy beam$^{-1}$\]  | \[maj $\times$ min, PA\]    |                  |                 |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0001.1 | 10:00:08.0 | +02:26:12.3   | 4.625 | 05-03-2022 | 0.32                 | 4.6$''\times$3.3$''$,$-$66  | J0948+0022       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0002.1 | 10:00:15.6 | +02:15:49.0   | 4.595 | 05-03-2022 | 0.33                 | 4.7$''\times$3.2$''$,$-$66  | J0948+0022       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0008.1 | 10:02:49.2 | +02:32:55.5   | 3.581 | 02-03-2022 | 0.25                 | 3.5$''\times$3.0$''$,85     | J1008-0029       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0009.1 | 10:00:28.7 | +02:32:03.6   | 2.260 | 02-03-2022 | 0.25                 | 2.42$''\times$2.1$''$,$-$73 | J0948+0022       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0014.1 | 10:01:41.0 | +02:04:04.9   | 2.921 | 21-03-2022 | 0.39                 | 3.7$''\times$2.1$''$,$-$60  | J0948+0022       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0023.1 | 09:59:42.9 | +02:29:38.2   | 4.341 | 05-03-2022 | 0.33                 | 4.4$''\times$3.2$''$,75     | J0948+0022       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0044.1 | 9:59:10.3  | +02:48:55.7   | 2.580 | 07-03-2022 | 0.20                 | 4.3$''\times$3.1$''$,75     | J1016+0513       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0065.1 | 09:58:40.3 | +02:05:14.7   | 2.414 | 07-03-2022 | 0.20                 | 2.8$''\times$2.0$''$,68     | J0948+0022       | J0854+2006      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2COS0066.1 | 09:59:46.6 | +01:57:15.1   | 3.247 | 05-03-2022 | 0.46                 | 3.1$''\times$2.6$''$,80     | J0948+0022       | J1058+0133      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2UDS012.0  | 02:18:03.6 | $-$04:55:27.2 | 2.520 | 02-03-2022 | 0.26                 | 2.6$''\times$2.0$''$,87     | J0228–0337       | J0238+1636      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2UDS026.0  | 02:19:02.1 | $-$05:28:56.9 | 3.296 | 01-03-2022 | 0.40                 | 3.2$''\times$2.6$''$,$-$78  | J0217–0820       | J0238+1636      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| AS2UDS126.0  | 02:15:46.7 | $-$05:18:49.2 | 2.436 | 02-03-2022 | 0.23                 | 3.0$''\times$1.9$''$,72     | J0217–0820       | J0238+1636      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
|              |            |               |       | 13–03–2022 |                      |                             |                  | J0423–0120      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
|              |            |               |       | 22–03–2022 |                      |                             |                  | J2258–2758      |
+--------------+------------+---------------+-------+------------+----------------------+-----------------------------+------------------+-----------------+
| $^a$ For channels of 60 km s$^{-1}$.                                                                                                                     |
+----------------------------------------------------------------------------------------------------------------------------------------------------------+

In this paper, we present ALMA Band 3 and 4 observations of the \[C I\](1–0) emission line in a sample of 12 unlensed SMGs which are part of a new VLA survey of molecular gas in massive star-forming galaxies at high redshift (cite: friascastillo2023). SMGs are dusty, high-infrared-luminosity ($L_\mathrm{IR} >$ 10$^{12}$ L$_\odot$; (cite: magnelli2012lir_smg)) galaxies harboring some of the most intense starbursts that have ever occurred (SFR $\sim$100 – 1000 M$_\odot$ yr$^{-1}$; (cite: magnelli2012lir_smg; swinbank2014; dacunha2015; Dudzeviciute2020; AS2COSPEC_II2024)), fueled by large molecular gas reservoirs of 10$^{10}$ – 10$^{11}$ M$_\odot$ (cite: greve2005; tacconi2008; bothwell2013; aravena2016; birkin2020; friascastillo2023). Such luminous, massive galaxies are therefore the ideal targets to detect the faint CO(1–0) line with current facilities without the need for gravitational lensing. Combined with eight previously published \[C I\](1–0) detections from galaxies in the parent sample (cite: birkin2020; AS2COSPEC_II2024), this makes a total of 20 high–redshift, unlensed SMGs with observation of the ground transition of both CO and \[C I\].

This paper is structured as follows: we present the sample and ALMA observations, line emission and continuum detections in Section [2](#sec:Sample). In Section [3](#sec:Analysis) we probe the relation between the \[C I\] and infrared luminosities, as well as the relation between the CO(1–0) and \[C I\](1–0) luminosities. We use line and line–to–continuum ratios to constrain the physical conditions in the ISM of our galaxies, and present a cross–calibration of \[C I\] as a gas mass tracer through a comparison with CO(1–0) and dust continuum emission. We then model the effect of the CMB on line emission at high redshift. Finally, we present a discussion of our results in Section [4](#sec:Discussion) and our conclusions in Section [5](#sec:Conclusions). Throughout this paper we assume a standard $\Lambda$CDM cosmology with $H_0$ = 67.8 km s$^{-1}$ Mpc$^{-1}$, $\Omega_\mathrm{M}$ = 0.310 and $\Omega_\Lambda$ = 0.690 (cite: planck2016).

# Data Reduction and Results

## Sample

We analyse \[C I\](1–0) observations of 20 galaxies selected from an on–going *Karl G. Jansky* Very Large Array (JVLA) survey, in which a total of 30 sources have been observed in CO(1–0) line emission in the K- and Ka-bands (cite: friascastillo2023). The targets were selected from a sample of sources detected within 4 deg$^2$ of SCUBA-2 850$\mu$m imaging in the UKIDSS Ultra Deep Survey (UDS), Cosmological Evolution Survey (COSMOS), Chandra Deep Field North (CDFN), and Extended Groth Strip (EGS) fields from the S2CLS (cite: geach2017) and S2COSMOS (cite: simpson2019) surveys. The brightest submillimeter sources in these fields were subsequently followed up with ALMA (AS2UDS, (cite: stach2018); AS2COSMOS, (cite: simpson2020)) and SMA (cite: hill2018) continuum imaging and further targeted with blind line scans using ALMA or NOEMA to obtain precise redshifts (cite: birkin2020; AS2COSPEC2022; AS2COSPEC_II2024). We refer the reader to (cite: friascastillo2023) for further details of the sample selection. Of the original parent sample, eight sources have published \[C I\](1–0) emission line detections (cite: birkin2020; AS2COSPEC_II2024), and we present new ALMA Band 3 and 4 observations for 12 more sources. Our sample thus comprises a total of 20 sources with \[C I\](1–0) and CO(1–0) line observations.

## JVLA CO(1–0) Data

Observations of the CO(1–0) emission (rest-frame frequency: $\nu_\mathrm{rest}$ = 115.2712 GHz) in our sample were carried out with the JVLA between 2021 March and 2024 January (project 21A-254, P.I.: Hodge). The K- or Ka-band receivers were used in combination with the WIDAR correlator configured to 8-bit sampling mode to observe a contiguous bandwidth of 2 GHz (dual polarization) at 2MHz spectral resolution. Eight of the SMGs in this sample have CO(1–0) fluxes or upper limits reported in (cite: friascastillo2023), so we take the line luminosities and recalculate the upper limits for consistency with our analysis (see Sec. [2.4](#sec:detections) for details on the flux extraction). For the rest of the sample, we calibrated the new data and obtained fluxes following (cite: friascastillo2023). The final line luminosities are reported in Table [\[tab:results\]](#tab:results).

-1.9cm

+:---------------------------:+:---------------------------:+:---------------------------:+:---------------------------:+:----------------------------------:+:---------------------------:+:----------------------------------:+:---------------------------:+:-----------------------------------:+:---------------------------:+:---------------------------:+
| Target                      | $z$                         | I$_\mathrm{[CI]}$           | FWHM$_\mathrm{[CI]}$        | L$'_\mathrm{[CI]}$                 | $M_\mathrm{gas,[CI]}$       | $L'_\mathrm{CO(1-0)}$              | $J_\mathrm{up}$             | $L'_\mathrm{CO(J_{up}-(J_{up}-1))}$ | $L_\mathrm{IR}$             | $S_\mathrm{3mm}$            |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
|                             |                             | \[Jy km s$^{-1}$\]          | \[km s$^{-1}$\]             | \[10$^{10}$ K km s$^{-1}$ pc$^2$\] | \[10$^{10}$ $M_\odot$\]     | \[10$^{10}$ K km s$^{-1}$ pc$^2$\] |                             | \[10$^{10}$ K km s$^{-1}$ pc$^2$\]  | \[10$^{12}$ $L_\odot$\]     | \[mJy\]                     |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0001.1                | 4.625                       | 0.54$\pm$0.20               | 680$\pm$170                 | 2.44$\pm$0.91                      | 9.9$\pm$3.7                 | $<$19.8$^f$                        | 5                           | 2.7$\pm$0.6$^c$                     | 36.3$^{+5.0}_{-6.7}$        | 0.38$\pm$0.04               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0002.1                | 4.595                       | 0.39$\pm$0.15               | –                           | 1.75$\pm$0.67                      | 7.1$\pm$2.7                 | $<$20.8$^f$                        | 5                           | 3.8$\pm$0.8$^c$                     | 9.5$^{+3.1}_{-2.9}$         | 0.22$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0008.1                | 3.581                       | 1.03$\pm$0.14               | 700$\pm$90                  | 3.12$\pm$0.42                      | 12.7$\pm$1.7                | 11.6$\pm$3.9$^b$                   | 4                           | 5.2$\pm$0.6$^c$                     | 15.9$^{+0.2}_{-1.1}$        | 0.40$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0009.1                | 2.260                       | $<0.42$                     | 840$\pm$350                 | $<$0.6                             | $<$2.3                      | $<$6.4$^b$                         | 3                           | 8.4$\pm$1.2$^c$                     | 4.4$^{+0.8}_{-0.1}$         | 0.58$\pm$0.04               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0014.1                | 2.921                       | 0.76$\pm$0.35               | 750$\pm$160                 | 1.65$\pm$0.76                      | 6.7$\pm$3.1                 | 9.1$\pm$3.4$^f$                    | 3                           | 9.1$\pm$1.5$^c$                     | 10.7$^{+0.7}_{-1.0}$        | 0.62$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0023.1                | 4.341                       | 0.70$\pm$0.14               | 480$\pm$80                  | 2.87$\pm$0.57                      | 11.6$\pm$2.3                | 7.0$\pm$3.1$^b$                    | 4                           | 9.1$\pm$0.7$^c$                     | 20.4$^{+0.7}_{-0.5}$        | 0.21$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0044.1                | 2.580                       | $<$0.27                     | –                           | $<$0.47                            | $<$2.0                      | $<$13.3$^f$                        | 3                           | 5.0$\pm$0.6$^c$                     | 3.1$^{+0.6}_{-0.7}$         | 1.34$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0065.1                | 2.414                       | 1.44$\pm$0.16               | 580$\pm$50                  | 2.27$\pm$0.25                      | 9.2$\pm$1.0                 | $<$13.2$^f$                        | 3                           | 8.1$\pm$0.8$^c$                     | 9.3$^{+0.9}_{-0.7}$         | 0.46$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0066.1$^*$            | 3.247                       | 0.61$\pm$0.29               | 160$\pm$50                  | 1.45$\pm$0.36                      | 5.6$\pm$1.5                 | 4.9$\pm$2.5$^f$                    | 4                           | 3.7$\pm$0.4$^c$                     | 6.8$^{+0.9}_{-0.9}$         | 0.23$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2UDS012.0                 | 2.520                       | 0.72$\pm$0.26               | 740$\pm$140                 | 1.22$\pm$0.44                      | 5.0$\pm$1.8                 | 11.1$\pm$2.3$^b$                   | 3                           | 4.0$\pm$0.8$^d$                     | 4.3$^{+0.1}_{-0.1}$         | 0.32$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2UDS026.0                 | 3.296                       | 0.99$\pm$0.31               | 700$\pm$150                 | 2.63$\pm$0.82                      | 10.6$\pm$3.3                | 6.3$\pm$2.9$^b$                    | 4                           | 4.3$\pm$0.8$^d$                     | 4.5$^{+0.8}_{-0.9}$         | 0.19$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2UDS126.0                 | 2.436                       | 1.17$\pm$0.19               | 680$\pm$70                  | 1.87$\pm$0.30                      | 7.6$\pm$1.2                 | 4.9$\pm$2.9$^b$                    | 3                           | 4.3$\pm$0.8$^d$                     | 9.3$^{+2.6}_{-1.9}$         | 0.43$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0011.1                | 4.78                        | 1.1$\pm$0.3$^c$             | 640$\pm$60                  | 5.1$\pm$1.7                        | 20.7$\pm$6.9                | $<$35$^a$                          | 5                           | 6.7$\pm$0.8$^c$                     | 12.6$^{+2.6}_{-2.3}$        | 0.47$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2COS0031.1                | 3.64                        | 1.0$\pm$0.2$^c$             | 400$\pm$60                  | 3.1$\pm$0.7                        | 12.6$\pm$2.8                | 12.7$\pm$3.5$^b$                   | 4                           | 8.9$\pm$0.7$^c$                     | 14.8$^{+0.3}_{-0.3}$        | 0.28$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2UDS011.0                 | 4.07                        | 0.73$\pm$0.24$^d$           | 610$\pm$220                 | 2.7$\pm$0.9                        | 10.9$\pm$3.6                | 4.7$\pm$2.7$^b$                    | 4                           | 3.9$\pm$1.0$^d$                     | 11.8$^{+1.6}_{-2.0}$        | 0.12$\pm$0.02               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AS2UDS014.0$^{**}$          | 3.8                         | 0.23$\pm$0.36$^d$           | 1560$\pm$5                  | $<3.6$                             | $<$14.6                     | $<$15.2$^b$                        | 4                           | 9.9$\pm$1.2$^d$                     | 8.7$^{+1.9}_{-0.2}$         | 0.19$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| CDFN2                       | 4.42                        | 0.90$\pm$0.10$^e$           | 500$\pm$50                  | 3.79$\pm$0.4                       | 15.4$\pm$1.6                | 12.9$\pm$3.8$^b$                   | 4                           | 8.2$\pm$0.3$^e$                     | 17.0$^{+0.8}_{-0.5}$        | 0.35$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| CDFN8                       | 4.14                        | 0.61$\pm$0.12$^e$           | 650$\pm$70                  | 2.32$\pm$0.44                      | 9.4$\pm$1.8                 | 7.0$\pm$4.3$^b$                    | 4                           | 4.6$\pm$0.3$^e$                     | 8.0$^{+1.8}_{-1.2}$         | 0.20$\pm$0.04               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AEG2                        | 3.67                        | 0.70$\pm$0.13$^e$           | 830$\pm$80                  | 2.21$\pm$0.39                      | 9.0$\pm$1.6                 | 11.4$\pm$3.4$^b$                   | 4                           | 4.4$\pm$0.2$^e$                     | 5.8$^{+0.1}_{-0.1}$         | 0.23$\pm$0.04               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| AEG3                        | 4.05                        | 0.35$\pm$0.07$^e$           | 600$\pm$70                  | 1.29$\pm$0.22                      | 5.2$\pm$0.9                 | $<$6.0$^b$                         | 4                           | 2.7$\pm$0.2$^e$                     | 6.9$^{+2.7}_{-1.2}$         | 0.11$\pm$0.03               |
+-----------------------------+-----------------------------+-----------------------------+-----------------------------+------------------------------------+-----------------------------+------------------------------------+-----------------------------+-------------------------------------+-----------------------------+-----------------------------+
| $a$ We downloaded and calibrated the data from the NRAO archive, project 21A-254 (P.I.: Hodge). Fluxes were calculated following (cite: friascastillo2023).                                                                                                                                                                                                   |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Line luminosities taken from: $b$) (cite: friascastillo2023); $c$) (cite: AS2COSPEC_II2024); $d$) (cite: birkin2020), $e$) Huber A. in prep., $f$) Hodge, J. priv.comm.                                                                                                                                                                                       |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^*$ AS2COS0066.1 falls on the edge of the ALMA Band, so we only cover the velocity range spanned by the main component of the emission seen in                                                                                                                                                                                                               |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CO(4–3) (cite: AS2COSPEC2022). This component represents $\sim$75% of the total flux, so we scale the inferred CO(1–0) luminosity down by 25%, and note that this                                                                                                                                                                                             |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| measurement is a lower limit of the total \[C I\] line flux.                                                                                                                                                                                                                                                                                                  |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{**}$ Although AS2UDS014.0 is reported as a detection in (cite: birkin2020), it does not pass our 2$\sigma$ criterion for a detection. Therefore, we take the three times the reported error on the                                                                                                                                                         |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| line luminosity as an upper limit for this source.                                                                                                                                                                                                                                                                                                            |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

![](detections_noCO.pdf)

## ALMA Data and Reduction

We obtained ALMA Band 3 and 4 observations during Cycle 8 (Project ID: 2021.1.01342.S). Data were collected in configurations C43–1/C43–2 between March 1 and 22 2022.

We adopt calibrations performed in the second level of quality assurance (QA2). Flagging and calibrations were done using CASA version 6.2.1.7 (cite: casa), which was also used for imaging. We first subtracted the continuum using the task UVCONTSUB in CASA after excluding the channels containing line emission. A priori, we used the line widths of the mid–$J_\mathrm{up}$ CO line emission reported in (cite: birkin2020) and (cite: AS2COSPEC_II2024) and masked channels within $\pm$2$\times$ the Full Width Half Maximum (FWHM) of the expected line, centered on the expected frequency of the \[C I\](1–0) line. We then imaged the line–free channels in the continuum–subtracted image cubes to verify that all emission had been fully removed. No further continuum subtraction was necessary.

The continuum–subtracted visibilities were then imaged and cleaned using the TCLEAN algorithm in CASA, with a cleaning threshold of 2$\sigma$. We adopted natural weighting to maximise the signal-to-noise ratio (SNR) of the detections, which resulted in final beam sizes ranging from 2.6$''$ to 4.7$''$ (Table [\[tab:sample\]](#tab:sample)) at FWHM. At this resolution, the targeted galaxies are not (or only marginally) spatially resolved. We binned the data cubes spectrally to channels of 60 km s$^{-1}$ to increase the SNR. The resulting data cubes reach a noise level of 0.2–0.5 mJy beam$^{-1}$ per channel (see Table [\[tab:sample\]](#tab:sample)), estimated over the emission–free region of the channels.

## \[C I\] Line and Continuum Detections

We began by collapsing the cleaned line cubes over the velocity width of the corresponding mid–$J_\mathrm{up}$ CO line from (cite: birkin2020) or (cite: AS2COSPEC_II2024). This allows us to initially assess whether there is a spatial offset between the \[C I\] emission and the coordinates given in Table [\[tab:sample\]](#tab:sample), derived from the ALMA and SMA continuum imaging (cite: stach2018; simpson2020). Only AS2COS0001.1 and AS2COS0002.1 show an offset of $\sim$0.5$''$. This offset might be caused by the low SNR of the emission in AS2COS0002.1. In the case of AS2COS0001.1, the source has a known companion only a few arcseconds away (cite: AS2COSPEC2022), which we do not resolve due to the resolution of our observations and might skew the position of the peak emission. We extract the line spectra from the position of the peak emission using an aperture of 5$''$ in diameter, to maximise the SNR. We detect \[C I\](1–0) emission in 10 out of the 12 sources in the new \[C I\](1–0) sample. The undetected sources, AS2COS0009.1 and AS2COS0044.1, are amongst the faintest far–infrared sources in the sample, which may explain their non–detections (Table [\[tab:results\]](#tab:results)). For the detected sources, the FWHM was derived from a single–Gaussian fitting to the spectra shown in Fig. [1](#detections).

To avoid any bias due to line structure and to be consistent with the analysis performed for CO(1–0) in (cite: friascastillo2023), we derive line fluxes using the intensity-weighted (0$^\mathrm{th}$–moment) maps collapsed over a velocity range twice the corresponding mid–$J_\mathrm{up}$ CO line width for each source (cite: birkin2020; AS2COSPEC_II2024):

$$\begin{equation}
    M_0 = I_\mathrm{CO} = \int I_\nu d\nu.
\end{equation}$$

The median line-width ratio of CO(4–3) or CO(3–2) to \[C I\](1–0) is 1.0 $\pm$ 0.1, and therefore the choice of FWHM (CO or \[C I\]) does not systematically impact the final recovered flux. Additionally, for the sources for which the SNR of the CO(1–0) data allows the fitting of a Gaussian profile to derive the FWHM, both the \[C I\](1–0) and CO(1–0) emission lines show consistent FWHM (FWHM$_\mathrm{[CI](1-0)}$/FWHM$_\mathrm{CO(1-0)}=$1.03$\pm$0.3).

In order to determine the optimal aperture to obtain the line fluxes, we perform a curve-of-growth analysis on these 0$^\mathrm{th}$–moment maps by extracting flux densities from a set of circular apertures of increasing diameter, from 1.5$''$ to 40$''$. We find that an aperture of diameter 2$\times$ the synthesised beam FWHM recovers most of the line flux while maximising the SNR, so we adopt that aperture size to extract final fluxes. This is consistent with the fluxes obtained using the CASA task IMFIT, which conducts 2D Gaussian fitting on the 0$^\mathrm{th}$–moment maps. For the two sources without detections, AS2COS0009.1 and AS2COS0044.1, we place 3$\sigma$ upper limits on the emission by calculating the RMS over an aperture covering a region of the 0$^\mathrm{th}$–moment map away from the position of the target, and then correcting for an aperture of 2$\times$ the synthesised beam size. We extract continuum fluxes in a similar manner by using a circular aperture of size 2$\times$ the synthesised beam size on the continuum images. The final fluxes and FWHM are compiled in Table [\[tab:results\]](#tab:results).[^1]

We convert the \[C I\] line intensities into line luminosities following (cite: solomon2005): $$\begin{equation}
    L'_\mathrm{[CI](1-0)} = 3.25 \times 10^7 \ I_\mathrm{[CI]} \ \mathrm{\nu{^{-2}_{obs}}} \ D\mathrm{{^2_{L}}} \ (1+\mathrm{z})^{-3} \ \mathrm{K \ km \  s^{-1} \ pc^2} ,
\end{equation}$$ where $I_\mathrm{[CI]}$ is the integrated line flux from the 0$^\mathrm{th}$–moment map in Jy km s$^{-1}$, $\mathrm{\nu_{\text{obs}}}$ is the observed frequency in GHz and $D\mathrm{_{\text{L}}}$ is the luminosity distance in Mpc. We derive line luminosities in the range $<$0.47–3.1$\times$10$^{10}$ K km s$^{-1}$  pc$^2$. Combined with the eight sources with published \[CI\](1–0) luminosities, our total sample spans the luminosity range $<$0.47–5.1$\times$10$^{10}$ K km s$^{-1}$  pc$^2$ (see Table [\[tab:results\]](#tab:results)).

# Analysis

## \[C I\] Line Luminosities

![image](lci_v_lir.pdf) ![image](luminosity_ratio_v_z_Mar22.pdf)

First, we put the \[C I\] luminosities of the galaxies in our sample in the context of other low–and high–redshift observations. Fig. [2](#lci_lum) (left) shows the $L'_\mathrm{[CI](1-0)}$ line luminosities as a function of infrared luminosity, $L_\mathrm{IR}$. $L_\mathrm{IR}$ was estimated through SED fitting with MAGPHYS (cite: highz_magphys), integrating over 8–1000$\mu$m. For details of the photometry used, we refer the reader to (cite: simpson2020) for sources in AS2COSMOS, (cite: Dudzeviciute2020) for AS2UDS and (cite: friascastillo2023) for sources in the CDFN and EGS fields. If we take $L'_\mathrm{[CI](1-0)}$ and $L_\mathrm{IR}$ as proxies for gas mass and SFR, respectively, their relation is equivalent to the spatially–integrated Schmidt–Kennicutt relation (cite: schmidt1959; kennicutt1998; kennicutt+evans2012). We compare them with the local ULIRGs from (cite: liu2019), (cite: kamenetzky2016) and (cite: montoya2023); the $z\sim$1 MS galaxies from (cite: valentino2018) and (cite: boogaard2020); and the SMGs from (cite: walter2011; danielson2011; alaghband2013; bothwell2017; Canameras2018; harrington2018; nesvadba2019; dannerbauer2019). We exclude galaxies classified as AGN according to (cite: valentino2020), and we restrict our compilation to only sources with either CO(1–0) or CO(2–1) observations to minimise the uncertainty introduced by excitation corrections. The literature data with mid–$J_\mathrm{up}$ CO observations has been converted to CO(1–0) using $r_\mathrm{21}$ = $L'_\mathrm{\text{CO(2-1)}}$/$L'_\mathrm{\text{CO(1-0)}}$ = 0.9 (cite: birkin2020). When necessary, fluxes and luminosities have been corrected for magnification. Although the SMGs in this work are marginally above the $L'_\mathrm{[CI](1-0)}$–$L_\mathrm{IR}$ relation found for other ULIRGs and main–sequence galaxies (cite: valentino2018), they are mostly within the 0.26 dex scatter of the relation (we assess whether our sample could be drawn from the $L'_\mathrm{[CI](1-0)}$–$L_\mathrm{IR}$ relation from (cite: valentino2018) using a $\chi^2$ test and find a $p$–value = 0.7, consistent with being drawn from the same distribution).

As shown in Fig. [2](#lci_lum) (left) and Table [\[tab:results\]](#tab:results), we do not detect \[C I\] emission in two sources, AS2COS0009.1 and AS2COS00044.1. Their 3$\sigma$ upper limits fall within the $L'_\mathrm{[C1]](1-0)}$–$L_\mathrm{IR}$ relation, so it is possible that they are too gas–poor to be detected given the sensitivity of our data.

The right panel of Fig. [2](#lci_lum) shows the $L'_\mathrm{[CI]](1-0)}$/$L'_\mathrm{\text{CO(1-0)}}$ ratio as a function of redshift. We calculate a median ratio of log($L'_\mathrm{[CI](1-0)}$/$L'_\mathrm{\text{CO(1-0)}}$) = $-$0.62$\pm$0.14, comparable with the value for the high–redshift SMG literature sample and the local ULIRGs ($-$0.74$\pm$0.12). This ratio is also consistent with the value of log($L'_\mathrm{[CI](1-0)}$/$L'_\mathrm{\text{CO(2--1)}}$) = ($-$0.69$\pm$0.04) found by (cite: valentino2018). The $z\sim1$ main sequence galaxies have a lower median value ($-$0.85$\pm$0.16), although it is still consistent with our sample. We also find no difference in $L'_\mathrm{[CI]](1-0)}$/$L'_\mathrm{\text{CO(1-0)}}$ ratios when compared to total $L_\mathrm{IR}$. Therefore, \[C I\](1–0) and CO(1–0) appear to be correlated on global scales regardless of galaxy type, $L_\mathrm{IR}$ and redshift.

## PDR Modelling

![](PDRToolbox_G0color_boxes.pdf)

How do the physical conditions (density, UV irradiation) of the interstellar medium in our sample compare to other high- and low-redshift galaxies? To answer this question, we use photo-dissociation region (PDR) modelling of the CO, \[C I\] and far-infrared continuum data available for our sources. For our analysis, we use the PDRTOOLBOX (cite: kaufman2006; pound2008) suite of one-dimensional, semi–infinite slab models with constant density. These models solve simultaneously for the chemistry, thermal balance, and radiative transfer, assuming metal, dust, and polycyclic aromatic hydrocarbons abundances, and a gas microturbulent velocity dispersion. For each combination of properties, every model is described in terms of the (number) density of H nuclei ($n$ \[cm$^{-3}$\]) and the intensity of the incident far–ultraviolet radiation ($G_\mathrm{UV}$, in units of the local interstellar field $G_0=1.6\times10^{-3}$ erg cm$^{-2}$ s$^{-1}$, (cite: hanbing1968)).

For the PDR modelling, we consider the \[C I\](1–0), CO(1–0), mid-$J$ CO and $L_\mathrm{FIR}$. The CMB heating is not implemented in the PDRTOOLBOX. We compare the data to default, solar-metallicity PDRTOOLBOX models - we consider them to be a good “default” scenario for dusty SMGs (see Section  [4](#sec:Discussion)). As the PDRTOOLBOX models consider only a single illuminated cloud face, we need to implement corrections for the optically thin tracers (in our case, FIR continuum and \[C I\] which will emit from both the near and far side of the clouds, whereas optically thick tracers (CO) will only be seen from the near side of the cloud. Namely, for the FIR continuum and \[C I\], we multiply the predicted fluxes by a factor of 2.

The \[C I\](1–0)/$L_\mathrm{FIR}$ and CO(1–0)/$L_\mathrm{FIR}$ ratio, with \[C I\] and CO tracing the extended gas mass and $L_\mathrm{FIR}$ tracing the SFR, allows us to constrain G$_\mathrm{UV}$. On the other hand, the ratio of \[C I\](1–0) or CO(1–0) and a mid–$J_\mathrm{up}$ CO line effectively traces the gas density, while being almost insensitive to $G_\mathrm{UV}$. We thus use a combination of these ratios to determine the PDR properties for this sample of SMGs. Where appropriate, we use the 3$\sigma$ upper/lower limits. We repeat the process excluding the CO(1–0) line: the results do not change appreciably except for AS2COS0009.1 ($G_\mathrm{UV}$ increases by 0.8 dex), AS2UDS12.0 ($n$ increases by 0.5 dex) and AS2UDS126.0 ($G_\mathrm{UV}$ increases by $\sim$2 dex). For a consistent comparison, we take the luminosities of the comparison sample and calculate the densities and radiation field strengths.

|              |                        |                        |
|:-------------|:----------------------:|:----------------------:|
| Target       |    $G_\mathrm{UV}$     |    $n_\mathrm{H_2}$    |
|              |     \[log $G_0$\]      |   \[log cm$^{-3}$\]    |
| AS2COS0001.1 | $3.86^{+0.94}_{-0.30}$ | $4.43^{+0.35}_{-1.42}$ |
| AS2COS0002.1 | $3.63^{+0.93}_{-0.34}$ | $4.79^{+0.38}_{-1.70}$ |
| AS2COS0008.1 | $3.26^{+0.05}_{-0.05}$ | $4.58^{+0.07}_{-0.08}$ |
| AS2COS0009.1 | $3.26^{+0.04}_{-0.05}$ | $5.23^{+0.12}_{-0.11}$ |
| AS2COS0014.1 | $3.19^{+0.08}_{-0.09}$ | $4.86^{+0.15}_{-0.16}$ |
| AS2COS0023.1 | $3.42^{+0.10}_{-0.09}$ | $4.85^{+0.10}_{-0.12}$ |
| AS2COS0044.1 | $3.52^{+0.06}_{-0.05}$ | $5.05^{+0.07}_{-0.08}$ |
| AS2COS0065.1 | $3.39^{+0.07}_{-0.06}$ | $4.46^{+0.07}_{-0.09}$ |
| AS2COS0066.1 | $3.44^{+0.09}_{-0.09}$ | $4.77^{+0.11}_{-0.13}$ |
| AS2UDS012.0  | $2.67^{+0.05}_{-0.05}$ | $4.79^{+0.09}_{-0.09}$ |
| AS2UDS026.0  | $2.78^{+0.11}_{-0.11}$ | $4.48^{+0.16}_{-0.21}$ |
| AS2UDS126.0  | $2.60^{+0.20}_{-0.20}$ | $4.19^{+0.11}_{-0.14}$ |
| AS2COS0011.1 | $3.14^{+1.09}_{-0.28}$ | $4.64^{+0.23}_{-0.49}$ |
| AS2COS0031.1 | $3.11^{+0.06}_{-0.06}$ | $4.87^{+0.10}_{-0.11}$ |
| AS2UDS011.0  | $3.30^{+0.13}_{-0.13}$ | $4.39^{+0.19}_{-0.29}$ |
| AS2UDS014.0  | $3.03^{+0.07}_{-0.07}$ | $4.99^{+0.08}_{-0.08}$ |
| CDFN2        | $2.03^{+0.11}_{-0.11}$ | $4.65^{+0.07}_{-0.08}$ |
| CDFN8        | $3.11^{+0.10}_{-0.09}$ | $4.60^{+0.09}_{-0.11}$ |
| AEG2         | $2.83^{+0.05}_{-0.05}$ | $4.69^{+0.07}_{-0.08}$ |
| AEG3         | $3.45^{+0.37}_{-0.18}$ | $4.64^{+0.10}_{-0.12}$ |

: Results of PDR modelling for individual sources. We list inferred $G_\mathrm{UV}$ and $n_\mathrm{H_2}$ values

We show the results of the PDR modelling in Fig. [\[pdr\]](#pdr) and Table [1](#tab:pdr). The SMGs show fairly high densities, with a median $n=$10$^{4.7\pm0.2}$ cm$^{-3}$. We refit the literature sample of MS and local galaxies from (cite: valentino2020), and high–redshift SMGs (cite: alaghband2013; bothwell2017) for consistency with our models. The UV radiation field has a median value of $G_\mathrm{UV}$ = 10$^{3.2\pm0.2}$ $G_0$. While $G_{UV}$ and $n$ likely vary significantly across individual galaxies (see, e.g., the resolved study of SDP.81 by (cite: rybak2020)), overall, SMGs in our sample occupy a similar parameter space as the main–sequence galaxies, as well as other high–redshift SMGs. The large spread in $G_\mathrm{UV}$ reflects the varied nature of the SMGs in our sample, as indicated by the wide range of CO excitation (i.e., CO(3–2)/CO(1–0) ratios spanning more than 1 dex; (cite: friascastillo2023)).

## Comparison Between Molecular Gas Tracers

We now cross–calibrate CO(1–0), \[C I\](1–0) and dust continuum as gas mass tracers and test their agreement. Fig. [2](#lci_lum) (right) shows that the SMGs in this work follow the correlation between CO(1–0) and \[C I\](1–0) line luminosities seen at low redshift (cite: jiao2017; jiao2019; montoya2023), at least when averaged over global scales. This relation, along with the similarity in FWHM of the line profiles, suggests that the line emission from both lines arises from similar volumes in the galaxy and has been one of the main arguments for the use of \[C I\] as a molecular gas tracer.

The absolute values of the light–to–mass conversion factors for \[C I\] and CO(1–0) have been the subject of extensive study in the literature. For \[C I\], the conversion is directly dependent on the assumed carbon abundance, $X_\mathrm{[CI]}$, which varies with metallicity (cite: heintz_watson2020). $X_\mathrm{[CI]}$ estimates in the literature range from $\sim1-2\times10^{-5}$ for MS galaxies (cite: valentino2018; jiao2019; boogaard2020) to $\sim4-8\times10^{-5}$ for ULIRGs and SMGs (cite: walter2011; alaghband2013; bothwell2017; jiao2017; gururajan2023). CO(1–0), on the other hand, relies on the choice of $\alpha_\mathrm{CO}$, which also depends on metallicity, turbulence and gas kinematics (cite: bolatto2013). Empirical calibrations for $\alpha_\mathrm{CO}$ derive values from $\sim0.8-1$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for local ULIRGs and some SMGs (cite: downes1998; danielson2011; papadopoulos2012; chen2017; calistro-rivera2018; birkin2020; amvrosiadis2023) to $\sim3-5$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for local discs and main sequence galaxies at high redshift (cite: sandstrom2013; remy2017; cormier2018; dunne2022).

### \[C I\](1–0) Line Emission as a Gas Mass Tracer

![image](conversion_factor_v_z_Mar25_G0.pdf) ![image](conversion_factor_v_Lir_Mar25_G0.pdf)

Following (cite: papadopoulos2004) and (cite: dunne2022), we calculate the total molecular gas mass from the \[C I\] line luminosity using the following expression:

$$\begin{equation}
 \label{ci_equation}
    \begin{aligned}
         M_\mathrm{H_2}^\mathrm{[CI]} = & \frac{0.0127}{X_{\mathrm{[CI]}} \ Q_{10}} \ \biggl(\frac{D_L^2}{1+z}\biggl) \ I_{\mathrm{[CI](1-0)}} \ \ M_\odot,
    \end{aligned}
\end{equation}$$

or in terms of line luminosity:

$$\begin{equation}
 \label{ci_gas}
M_\mathrm{H_2}^\mathrm{[CI]} = \frac{9.51 \times 10^{-5}}{X_{\mathrm{[CI]}} \ Q_{10}} \ L'_{\mathrm{[CI}](1-0)} \ M_\odot,
\end{equation}$$

where $X_\mathrm{[CI]}$ is the C/H$_2$ abundance ratio and $Q_\mathrm{10}$ is the \[C I\] excitation factor of the \[C I\] $J$ = 1 $\rightarrow$ 0 level. The value of $Q_\mathrm{10}$ is straightforward to calculate under the assumption of local thermodynamic equilibrium (LTE):

$$\begin{equation}
    Q(T_\mathrm{ex}) = 3e^{(-T_1/T_\mathrm{ex})} / (1 + 3e^{(-T_1/T_\mathrm{ex})} + 5e^{(-T_2/T_\mathrm{ex})}),
\end{equation}$$

where $T_1$ = 23.6 K and $T_2$ = 62.5 K are the excitation energy levels of atomic carbon. We adopt a typical value of $T_\mathrm{ex}$ = 30 K (cite: weiss2003; walter2011; harrington2021), which results in $Q_\mathrm{10}$ = 0.46. We note that, above $T_\mathrm{ex}\sim$20 K, the derived carbon masses depend very weakly on the assumed temperature (cite: weiss2005a). (cite: papadopoulos2022) found however that the \[C I\] lines are sub–thermally excited in the ISM of galaxies, which means that $Q_\mathrm{10}$ becomes a non–trivial function of density and temperature. Our choice of $T_\mathrm{ex}$ = 30 K and LTE only implies a 4% higher mass compared more complex non–LTE approaches (cite: harrington2021; dunne2022; papadopoulos2022), which is negligible compared to the uncertainty in $X_\mathrm{[CI]}$.

We obtain the CO(1–0)–based molecular gas masses following the standard equation:

$$\begin{equation}
 \label{co_gas}
    M_\mathrm{H_2}^\mathrm{CO} = \alpha_\mathrm{CO} \ L'_\mathrm{CO(1-0)} \ M_\odot,
\end{equation}$$

where $\alpha_\mathrm{CO}$ is the CO-to-H$_2$ conversion factor, which we take to be 1 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: danielson2011; hodge2012; debreuck2014; chen2017; calistro-rivera2018; xue2018; riechers2020b-coldz; friascastillo2022; amvrosiadis2023).

Combining Eq. [\[ci_gas\]](#ci_gas) and [\[co_gas\]](#co_gas), we can constrain the product of the two main unknowns for each tracer (for $Q_\mathrm{10}$ = 0.46):

$$\begin{equation}
    X_\mathrm{[CI]}\times\alpha_\mathrm{CO} = 2.07\times10^{-4}\frac{L'_\mathrm{[CI]}}{L'_\mathrm{CO}}.
\end{equation}$$

In Fig. [4](#conversion_factor) we show $X_\mathrm{[CI]}\times\alpha_\mathrm{CO}$ as a function of redshift and L$_\mathrm{IR}$, color–coded by the intensity of the FUV radiation field, $G_\mathrm{UV}$. We do not show the sources where neither CO(1–0) nor \[C I\](1–0) are detected. The factor does not appear to be correlated with $G_\mathrm{UV}$, suggesting that it could be insensitive to local conditions of the ISM in our sample. We look for any trends in the sample with LINMIX (cite: kelly2007), a Bayesian linear regression fitting model which can fit data with errors along with the upper limits. Our fits return a slope of 0.02$\pm$0.02 and 0.01$\pm$0.05 for the dependence on redshift and L$_\mathrm{IR}$, respectively. The full sample has a scatter of 0.12 dex in both cases. This is consistent with no dependence on either parameter, and we can thus compute a constant conversion factor. We find a median $X_\mathrm{[CI]}\times\alpha_\mathrm{CO}$ = (5.1$\pm$1.8)$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and a mean (5.4$\pm$2.6)$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for the galaxies in our sample (not including those with both CO and \[C I\] non–detections).

### Dust Continuum Emission as a Gas Mass Tracer

Because the Rayleigh-Jeans (RJ) tail of the dust emission is almost always optically thin, it can trace the total dust mass, and therefore potentially the molecular gas mass, provided that the dust emissivity per unit mass and the dust-to-gas abundance ratio can be constrained. Under the assumption of a mass-weighted cold dust temperature, $T_\mathrm{dust}$ (25 K is typically considered to be representative for both local star-forming and high-redshift galaxies), and a dust emissivity index, $\beta$ (generally taken to be 1.8), the CO(1–0) luminosity and rest–frame 850 $\mu$m continuum flux have been shown to correlate for a range of galaxy populations (e.g., (cite: scoville2016) for local SFGs, ULIRGs and high-redshift SMGs, and (cite: kaasinen2019) for $z\sim$2 SFGs). From a single–band continuum flux measurement, the $L_\mathrm{850\mu m,rest}$ can be calculated following (cite: scoville2016; scoville2017):

$$\begin{multline}
 L_\mathrm{850\mu m,rest} = 1.19\times10^{27} S_{\nu_\mathrm{obs}}(1+z)^{-(3+\beta)} \times \\ \Big(\frac{\nu_{850}}{\nu_\mathrm{obs}}\Big)^{2+\beta} \ D_\mathrm{L}^2 \ \frac{\Gamma_0(T_\mathrm{dust})}{\Gamma_{RJ}(T_\mathrm{dust},z)}  \  \mathrm{erg \ s^{-1} Hz^{-1}}, 
\end{multline}$$

where $\nu_\mathrm{obs}$ is the observed–frame frequency where the continuum flux density is measured and $\Gamma_\mathrm{RJ}$ is the correction for departures in the rest frame of the Planck function from Rayleigh–Jeans. The $H_2$ mass is then obtained via:

$$\begin{equation}
 \label{dust_gas}
    M_\mathrm{H_2}^\mathrm{dust} =\frac{L_\mathrm{850\mu m,rest}}{\alpha_\mathrm{850}} \ M_\odot,
\end{equation}$$

where $\alpha_\mathrm{850}$ is the luminosity–to–gas mass conversion factor for dust at rest–frame 850 $\mu$m. The 3 mm dust–continuum emission measurements for our sample probe rest–frame wavelengths in the range $\lambda_\mathrm{rest}\sim650-520 \mu m$, so we calculate the extrapolated $L_\mathrm{850\mu m,rest}$ and compare them against the CO and \[C I\] line luminosities to constrain the product of their conversion factors. Firstly, we need to make an assumption for $T_\mathrm{dust}$ and $\beta$. Studies on the dust SED of SMGs find that they are characterised by warmer temperatures and steeper $\beta$ (cite: saintonge2013; dacunha2021; dunne2022; shouwen2022; AS2COSPEC_II2024) than the typically assumed $T_\mathrm{dust}$ = 25 K and $\beta=1.8$. Following (cite: AS2COSPEC_II2024), who performed SED fitting with CIGALE for a subsample of the sources in this work, we set $T_\mathrm{dust}$ = 30 K and $\beta$ = 2.1 and calculate $L_\mathrm{850\mu m,rest}$. If we had chosen $T_\mathrm{dust}$ = 25 K and $\beta=1.8$ instead, the luminosities would have been 15% higher[^2].

![image](ratio_xd_v_z_Mar22.pdf) ![image](ratio_ad_v_z_Mar22.pdf)

In Fig. [5](#dust_factor) we show the distribution of $\alpha_\mathrm{CO}\times\alpha_\mathrm{850}$ and $X_\mathrm{[CI]}/\alpha_\mathrm{850}$ for our sample as a function of redshift. We fit the distributions again using LINMIX. In all cases, the fits have a slope consistent with no trend with either parameter, so we compute a mean constant conversion factor for the whole sample of: $$\begin{align*}
    \alpha_\mathrm{CO}\times\alpha_\mathrm{850} = \frac{L_\mathrm{850\mu m,rest}}{L'_\mathrm{CO}} = \\ (2.4 \pm 1.0) \times 10^{20} \ \mathrm{erg} \  \mathrm{s}^{-1} \mathrm{Hz}^{-1} \ (\mathrm{K} \ \mathrm{km} \ \mathrm{s}^{-1}\ \mathrm{pc}^2)^{-1}
\end{align*}$$ $$\begin{align*}
    X_\mathrm{[CI]}/\alpha_\mathrm{850} = 2.07\times10^{-4}\frac{L'_\mathrm{[CI]}}{L_\mathrm{850\mu m,rest}} = \\ (2.2 \pm 1.0) \times 10^{-25} \ (\mathrm{erg} \ \mathrm{s}^{-1} \ \mathrm{Hz}^{-1})^{-1}.
\end{align*}$$

## CMB Effect on CO and \[C I\] Emission at High Redshift

![image](radex_co.pdf) ![image](radex_c_noleg.pdf) ![image](radex_ratio_ylim_noleg.pdf)

Our sample of SMGs spans a redshift range $\sim2-5$. Therefore, it is important to consider the effect that the CMB will have on the recoverable emission of the ground state transitions for both CO and \[C I\], as its temperature increases (cite: dacunha2013; zhang2016). We model how the measured CO(1–0) and \[C I\](1–0) intensities, as well as their ratio, vary with increasing $T_\mathrm{CMB}$ for a range of gas densities and kinetic temperatures, and we show the results in Fig. [6](#ratio_z). We use RADEX (cite: radex2007) for the models, a non-LTE radiative transfer code which uses the escape probability method, and we take collisional data between each molecule and H$_2$ from the LAMBDA database (cite: lambda_database). We fix the H$_2$ ortho–to–para ratio to 3:1 and set log($N_\mathrm{CO}$/$d$v) = log($N_\mathrm{C}$/$d$v) = 18.

Our models indicate a non-negligible decrease in the recovered \[C I\](1–0) intensity for a given gas kinetic temperature and density. The magnitude of the effect is mostly determined by the kinetic temperature of the gas, with the density having barely any impact on the resulting emission. However, the decrease in recovered line intensities for both CO(1–0) and \[C I\](1–0) offset each other, such that there is a negligible effect on the measured luminosity ratio for the warmer gas temperatures ($T_\mathrm{kin} \geq 50 K$). For the colder temperatures, the ratio can decrease by up to $\sim$30%. As a lower bound for the $T_\mathrm{kin}$ in our sample, we can consider the excitation temperature of the CO(1–0)-emitting layer from our PDR models; this is 18–20 K, though the real $T_\mathrm{kin}$ is likely significantly higher. Given the current scatter of the CO(1–0) and \[C I\](1–0) data, it is challenging to detect a suppression of this magnitude in the ratio. We perform the same analysis for dust emission (see Appendix), and find that the CO/dust and \[C I\]/dust flux ratios also stay approximately constant with redshift, as the effect of the CMB is of a similar order of magnitude for all tracers individually (assuming $T_\mathrm{dust}$=$T_\mathrm{kin}\sim30$ K).

How would these effects impact the observed luminosity ratios? The warmer CMB background would act to increase the $X_\mathrm{[CI]}\times\alpha_\mathrm{CO}$ factor needed for higher–redshift sources. This is not immediately evident from Fig. [4](#conversion_factor), as the fit to the data is consistent with no evolution with redshift. If we separate our sources in two bins at $z<3.5$ and $z>3.5$, we find consistent mean factors for both bins (5.6$\pm$2.0$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ versus 5.1$\pm$1.8$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$). This suggests that, at least out to $z\sim5$, the ratio of both tracers is not obviously suppressed compared to that of local ULIRGs. This could be a selection effect, as we are currently restricted to the most massive, dusty, star–forming galaxies at higher redshifts, where gas temperatures and densities, as well as metallicities, are expected to be higher than in normal, main–sequence galaxies (cite: valentino2020-co; harrington2021; Jarugula2021). We also caution that there is a larger spread in ratios for the high–redshift sources compared to the $z=0$ ULIRGs. For the conversion factors involving dust, we find 1.5$\pm$1.0$\times$10$^{-25}$ versus 2.7$\pm$1.0$\times$10$^{-25}$ erg s$^{-1}$ Hz$^{-1}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$ for $\alpha_\mathrm{CO}\times\alpha_\mathrm{850}$, and 1.8$\pm$0.8$\times$10$^{20}$ versus 3.1$\pm$0.8$\times$10$^{20}$ K km s$^{-1}$ pc$^{2}$ (erg s$^{-1}$ Hz$^{-1}$)$^{-1}$ for $X_\mathrm{[CI]}/\alpha_\mathrm{850}$ for the lower and higher redshift bins, respectively – again consistent with no evolution with redshift.

# Discussion

The observations of CO(1–0) and \[C I\](1–0) presented here for a sample of dusty, star–forming galaxies at $z\sim2-5$ obviate the need for excitation corrections, allowing us to directly confirm that the relation found in the local Universe remains in place for the ground state transition of both species out to $z\sim5$. This suggests that \[C I\] coexists with CO in the cold gas reservoirs of high–redshift galaxies and is therefore a good tracer of the total molecular gas mass. However, as we do not yet have a calibration of \[C I\] as a tracer of molecular gas mass fully independent of CO; we can only constrain the product $X_\mathrm{[CI]}\times\alpha_\mathrm{CO}$ and relate it to the choice of $\alpha_\mathrm{CO}$. We find a median $X_\mathrm{[CI]}\times\alpha_\mathrm{CO}$ = (5.1$\pm$1.8)$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and a mean of (5.4$\pm$2.6)$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (without including three sources that are undetected in both lines). This mean product is consistent with the value found for the SPT lensed galaxies by (cite: gururajan2023) of (6.3$\pm$0.7)$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ and the value obtained in the study by (cite: dunne2022) of (3.98$\pm$0.19)$\times$10$^{-5}$ M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$, which included a compilation of published CO(1–0) and \[C I\](1–0) observations available at that time.

![image](final_plot_z.pdf) ![image](final_plot_alpha.pdf)

Assuming a Milky–Way value of $\alpha_\mathrm{CO}$=3.6, we derive a median $X_\mathrm{[CI]}=(1.4\pm0.5)\times10^{-5}$, which would be in agreement with abundances derived for local (cite: jiao2019) and $z\sim1$ main–sequence galaxies (cite: valentino2018; boogaard2020), as well as the sample from (cite: dunne2022) ($1.6^{+0.5}_{-0.4}\times10^{-5}$). On the other hand, if we adopt $\alpha_\mathrm{CO}\sim$1, as is common for high–redshift SMGs and local ULIRGs, we obtain a mean carbon abundance of $X_\mathrm{[CI]}=(5.1\pm1.8)\times10^{-5}$, higher than the commonly adopted value of 3$\times$10$^{-5}$ (cite: weiss2003; papadopoulos2004; bothwell2017) or the values found for main sequence galaxies. Higher carbon abundances have been derived for local ULIRGs (cite: jiao2017; jiao2019) and high–redshift SMGs (cite: walter2011; alaghband2013; gururajan2023), although the latter have commonly targeted lensed sources and relied on $J_\mathrm{up}>2$ CO observations. These higher values can be caused by regions with higher cosmic ray ionization rates or stronger FUV radiation field (Fig. [\[pdr\]](#pdr)), which would dissociate CO into \[C I\] (cite: bisbas2021). Higher carbon abundances could also be explained by galaxies having higher metallicities – we return to this point below.

Finally, assuming $X_\mathrm{[CI]}=5.1\times10^{-5}$ and $\alpha_\mathrm{CO}=1$, we derive consistent mean values for the dust conversion factor $\alpha_\mathrm{850}=(2.2\pm1.0)\times10^{20}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$ and $(2.4\pm1.0)\times10^{20}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$, respectively. This is a factor of two lower than the mean value of $(4.4\pm1.1)\times10^{20}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$ derived in (cite: scoville2016) (correcting their value for $\alpha_\mathrm{CO}=1$ and removing the Helium contribution, as we are only dealing with $M_\mathrm{H_2}$).

Previous studies reported a discrepancy between the $H_2$ masses derived from CO and \[C I\] observations (cite: bothwell2017; valentino2018; montoya2023). This can be explained by the fact that these studies used a bi–modal $\alpha_\mathrm{CO}$ while keeping the carbon abundance constant for all galaxy populations (X$_\mathrm{[CI]}$ = 3$\times$10$^{-5}$), which naturally results in a mismatch in the derived H$_2$ masses. We show this effect in Fig. [7](#final_fig), where we have compiled the carbon abundances reported in previous studies. When corrected to the same $\alpha_\mathrm{CO}$, the values of X$_\mathrm{[CI]}$ show a fairly linear distribution with $L_\mathrm{IR}$ and redshift, as previously noted by (cite: dunne2022). However, if we adopt different values for $\alpha_\mathrm{CO}$ for different galaxy populations, studies that adopt a ULIRG–like value generally find higher carbon abundances than those that use a Milky–Way value instead.

Although (cite: dunne2022) argued for near–universal values of X$_\mathrm{[CI]}$ = 1.6$\times$10$^{-5}$ and $\alpha_\mathrm{CO}$ = 3.6 M$_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$, multiple high–resolution studies of gas kinematics in SMGs have noted the difficulty of reconciling such a high $\alpha_\mathrm{CO}$ with the derived stellar and dynamical masses, consistently finding that $\alpha_\mathrm{CO}\sim1$ (and therefore X$_\mathrm{[CI]}\sim$ 5$\times$10$^{-5}$) is preferred for this population (cite: danielson2011; hodge2012; debreuck2014; chen2017; calistro-rivera2018; xue2018; birkin2020; riechers2020b-coldz; friascastillo2022; amvrosiadis2023). Following (cite: heintz_watson2020), the values of $X_\mathrm{[CI]}$ derived for our sources assuming $\alpha_\mathrm{CO}=1$ would imply solar or super–solar metallicities (Fig. [8](#metallicity_fig)).

This is in line with SMGs being dust enriched and is consistent with recent results from rest-frame optical spectroscopy with VLT’s KMOS (cite: birkin2022PhDT.........6B) and JWST’s NIRSpec (cite: Birkin2023), although some SMGs might have sub-solar metallicities (e.g., (cite: Rigopoulou2018; Rybak2023)). This re-affirms our choice of $\alpha_\mathrm{CO}$ and derived $X_\mathrm{[CI]}$. Assuming $X_\mathrm{[CI]}\sim$5$\times$10$^{-5}$, we derive gas masses $M_\mathrm{H_2,[CI]}$ in the range 5–21$\times10^{10} M_\odot$, consistent with $M_\mathrm{H_2,CO}$ = 4–13$\times10^{10} M_\odot$ using $\alpha_\mathrm{CO}=1$. Therefore, it is possible to obtain gas mass estimates from either tracer that agree within the uncertainties, so long as consistent assumptions are made when converting luminosities into gas masses. Finally, we note that, due to the relative brightness of \[C I\] compared to CO(1–0), \[C I\] will thus provide more precise gas mass estimates than CO(1–0) for the same integration time (though subject to the same systematic uncertainties).

![](alpha_z.pdf)

The constant conversion factor that we have derived relies on the linear correlation between $L'_\mathrm{CO}$ and $L'_\mathrm{[CI]}$ observed out to $z\sim 5$, as well as the lack of evolution of the ratio of both quantities with either redshift or $L_\mathrm{IR}$. We have shown that the warmer CMB at higher redshifts has a moderate impact on the ratio, which can be suppressed by up to $30\%$ for the lowest kinetic gas temperatures (Fig. [6](#ratio_z)). In Fig. [2](#lci_lum) (right) we show the impact that this could have on the measured ratio at high redshift. We have taken the mean value of the line luminosity ratio $L'_\mathrm{[CI]}$/$L'_\mathrm{CO}$ for local ULIRGs (0.21) as the intrinsic value that an SMG would have at $z=0$, and applied the correction for the effect of the CMB for different $T_\mathrm{kin}$. The effect on the ratio is too small to be differentiated from the current scatter of the data, which is likely driven by the uncertainties in the measurements as well as the internal conditions of individual galaxies (cite: gururajan2023). We caution that this only applies to the ratio of both tracers, and that the CMB effect can be significant on individual lines, which in turns affects the absolute value of the molecular gas masses that we obtain at high redshift. In order to determine the absolute decrease of the line intensities due to the CMB of individual lines, it will be necessary to obtain more complete SLEDs to perform complex, non–LTE modelling of the gas excitation conditions (cite: harrington2021) and extend the sample to galaxies of lower mass and metallicities.

# Conclusions

We have presented ALMA Band 3 and 4 observations targeting \[C I\](1–0) in a sample of twelve $z\sim2-5$ unlensed, massive, gas–rich galaxies with CO(1–0) observations from a new VLA survey of molecular gas in massive star-forming galaxies at high redshift (cite: friascastillo2023). Combining these data with eight archival detections in the CO(1–0) sample, we have compiled a total of 20 galaxies with observations of the ground state transitions of both species. This dataset allows us to directly compare CO(1–0) and \[C I\](1–0) as tracers of the cold molecular gas reservoirs in galaxies at high redshift. The main conclusions are as follows:

- We detect \[C I\](1–0) line emission in 10 out of 12 galaxies observed. The full sample has \[C I\](1–0) line luminosities in the range 1.2–3.1$\times$10$^{10}$ K km s$^{-1}$ pc$^2$. The \[C I\](1–0)/CO(1–0) line luminosity ratio is consistent with the one found at lower redshifts for ULIRGs and main–sequence galaxies, and shows no deviation out to $z\sim5$.

- Combining the mid–$J_\mathrm{up}$ CO and \[C I\] line luminosities with infrared luminosities, we constrain the conditions of the ISM of our sample using PDR models. We find a median density log$(n \ [$cm$^{-3}])=4.7\pm0.2$, and a median UV radiation field log$(G_{\mathrm{UV}} \ [G_0]) = 3.2\pm0.2$. There is a significant overlap in the parameter space occupied by our sources and local ULIRGs, $z\sim1$ main sequence galaxies and published high–redshift SMGs.

- We compare our measurements of $L'_\mathrm{CO(1-0)}$, $L'_\mathrm{[CI](1-0)}$ and 3mm dust continuum to provide a cross–calibration for their conversion factors, $\alpha_\mathrm{CO}$, $X_\mathrm{[CI]}$, and $\alpha_\mathrm{850}$, respectively. The conversion factors do not evolve with redshift or $L_\mathrm{IR}$. We find that the product $X_\mathrm{[CI]}\times\alpha_\mathrm{CO}$ is remarkably similar for local ULIRGs, main sequence galaxies and high–redshift SMGs, and this affects the derived $X_\mathrm{[CI]}$ values when different values of $\alpha_\mathrm{CO}$ are assumed for various galaxy populations. Taking $\alpha_\mathrm{CO}=1$ for our sample of SMGs, we derive a median $X_\mathrm{[CI]}=(5.1\pm1.8)\times10^{-5}$. This results in gas masses $M_\mathrm{H_2,[CI]}$ in the range 5–21$\times10^{10} M_\odot$. Likewise, these choices of $\alpha_\mathrm{CO}$ and $X_\mathrm{[CI]}$ result in values of $\alpha_\mathrm{850}=(2.2\pm1.0)\times10^{20}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$ and $(2.4\pm1.0)\times10^{20}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$, respectively. These values differ from the canonically assumed $X_\mathrm{[CI]}=3\times10^{-5}$ and $\alpha_\mathrm{850}=4.4\times10^{20}$ erg s$^{-1}$ Hz$^{-1}$ M$_\odot^{-1}$, but are supported by predictions for the solar/super–solar metallicities expected for our sources.

- We model the effect of the warmer CMB at high redshift on the measured intensities of CO(1–0) and \[C I\](1–0). The absolute effect on both individual lines can be quite severe, but the relative effect between the lines is much smaller, such that the ratio between the lines decreases by up to $\sim30\%$ for the coldest gas kinetic temperatures expected. A comparison of the $L'_\mathrm{CO(1-0)}/$$L'_\mathrm{[CI](1-0)}$ ratio between local ULIRGs and our sources shows both populations have similar values, suggesting that the ratio is not obviously suppressed out to $z\sim5$.

We caveat that current constraints on the conversion factors at high redshift are limited to typically very active sources. To improve the calibration of $X_\mathrm{[CI]}$, $\alpha_\mathrm{CO}$ and $\alpha_\mathrm{850}$ at high redshift, as well as the constrains on the effects of the CMB, it is necessary to obtain samples of galaxies spanning a larger range of masses and metallicities. Additionally, well–sampled CO and \[C I\] SLEDs will facilitate a more accurate modeling of properties of their cold ISM. The galaxies presented in this work constitute the largest sample of un-lensed galaxies with CO(1–0) and \[C I(1–0)\] observations, which will be crucial for understanding the physical conditions of cold ISM at high redshift.

# Acknowledgments

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01342.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This paper makes use of data from IRAM/NOEMA program S19CV (PI: Chapman). M. R. is supported by the NWO Veni project “*Under the lens*” (VI.Veni.202.225). J.H. acknowledges support from the ERC Consolidator Grant 101088676 (VOYAJ) and the VIDI research programme with project number 639.042.611, which is (partly) financed by the Netherlands Organisation for Scientific Research (NWO). J.B. has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme MOPPEX 833460. Part of this work was supported by the German *Deut­sche For­schungs­ge­mein­schaft, DFG* project number Ts 17/2–1. T.T. gratefully acknowledges the Collaborative Research Center 1601 (SFB 1601 subproject A6) funded by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) – 500700252. C.C.C and C.-L.L. acknowledge support from the National Science and Technology Council of Taiwan (NSTC 111-2112M-001-045-MY3), as well as Academia Sinica through the Career Development Award (AS-CDA-112-M02). IRS and AMS acknowledge support from STFC (ST/T000244/1 and ST/X001075/1). E.F.-J.A. acknowledge support from UNAM-PAPIIT project IA102023, and from CONAHCyT Ciencia de Frontera project ID: CF-2023-I-506. HD acknowledges financial support from the Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (AEI-MCINN) under grant (La evolución de los cúmulos de galaxias desde el amanecer hasta el mediodía cósmico) with reference (PID2019-105776GB-I00/DOI:10.13039/501100011033) and the Ministerio de Ciencia, Innovación y Universidades (MCIU/AEI) under grant (Construcción de cúmulos de galaxias en formación a través de la formación estelar oscurecida por el polvo) and the European Regional Development Fund (ERDF) with reference (PID2022-143243NB-I00/DOI:10.13039/501100011033). This work was supported by NAOJ ALMA Scientific Research Grant Code 2021-19A (H.S.B.A). The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. The authors acknowledge assistance from Allegro, the European ALMA Regional Center node in the Netherlands.

## CMB Effect on Dust Emission

![image](cmb_dust.pdf) ![image](cmb_dust_co.pdf) ![image](cmb_dust_ci.pdf)

natexlab

(ref: alaghband2013) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, MNRAS, 435, 1493, doi: [`10.1093/mnras/stt1390`](http://doi.org/10.1093/mnras/stt1390)

(ref: amvrosiadis2023) Amvrosiadis, A., Wardlow, J. L., Birkin, J. E., et al. 2023, arXiv e-prints, arXiv:2312.08959, doi: [`10.48550/arXiv.2312.08959`](http://doi.org/10.48550/arXiv.2312.08959)

(ref: andreani2018) Andreani, P., Retana-Montenegro, E., Zhang, Z.-Y., et al. 2018, A&A, 615, A142, doi: [`10.1051/0004-6361/201732560`](http://doi.org/10.1051/0004-6361/201732560)

(ref: aravena2016) Aravena, M., Spilker, J. S., Bethermin, M., et al. 2016, MNRAS, 457, 4406, doi: [`10.1093/mnras/stw275`](http://doi.org/10.1093/mnras/stw275)

(ref: highz_magphys) Battisti, A. J., da Cunha, E., Grasha, K., et al. 2019, ApJ, 882, 61, doi: [`10.3847/1538-4357/ab345d`](http://doi.org/10.3847/1538-4357/ab345d)

(ref: bethermin2015) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113, doi: [`10.1051/0004-6361/201425031`](http://doi.org/10.1051/0004-6361/201425031)

(ref: birkin2022PhDT.........6B) Birkin, J. E. 2022, PhD thesis, Durham University, UK

(ref: birkin2020) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926, doi: [`10.1093/mnras/staa3862`](http://doi.org/10.1093/mnras/staa3862)

(ref: Birkin2023) Birkin, J. E., Hutchison, T. A., Welch, B., et al. 2023, ApJ, 958, 64, doi: [`10.3847/1538-4357/acf712`](http://doi.org/10.3847/1538-4357/acf712)

(ref: bisbas2021) Bisbas, T. G., Tan, J. C., & Tanaka, K. E. I. 2021, MNRAS, 502, 2701, doi: [`10.1093/mnras/stab121`](http://doi.org/10.1093/mnras/stab121)

(ref: bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207, doi: [`10.1146/annurev-astro-082812-140944`](http://doi.org/10.1146/annurev-astro-082812-140944)

(ref: boogaard2020) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109, doi: [`10.3847/1538-4357/abb82f`](http://doi.org/10.3847/1538-4357/abb82f)

(ref: bothwell2013) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, MNRAS, 429, 3047, doi: [`10.1093/mnras/sts562`](http://doi.org/10.1093/mnras/sts562)

(ref: bothwell2014) Bothwell, M. S., Wagg, J., Cicone, C., et al. 2014, MNRAS, 445, 2599, doi: [`10.1093/mnras/stu1936`](http://doi.org/10.1093/mnras/stu1936)

(ref: bothwell2017) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825, doi: [`10.1093/mnras/stw3270`](http://doi.org/10.1093/mnras/stw3270)

(ref: bourne2019) Bourne, N., Dunlop, J. S., Simpson, J. M., et al. 2019, MNRAS, 482, 3135, doi: [`10.1093/mnras/sty2773`](http://doi.org/10.1093/mnras/sty2773)

(ref: Canameras2018) Cañameras, R., Yang, C., Nesvadba, N. P. H., et al. 2018, A&A, 620, A61, doi: [`10.1051/0004-6361/201833625`](http://doi.org/10.1051/0004-6361/201833625)

(ref: calistro-rivera2018) Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56, doi: [`10.3847/1538-4357/aacffa`](http://doi.org/10.3847/1538-4357/aacffa)

(ref: carilli-walter2013) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: chen2017) Chen, C.-C., Hodge, J. A., Smail, I., et al. 2017, ApJ, 846, 108, doi: [`10.3847/1538-4357/aa863a`](http://doi.org/10.3847/1538-4357/aa863a)

(ref: AS2COSPEC2022) Chen, C.-C., Liao, C.-L., Smail, I., et al. 2022, ApJ, 929, 159, doi: [`10.3847/1538-4357/ac61df`](http://doi.org/10.3847/1538-4357/ac61df)

(ref: cormier2018) Cormier, D., Bigiel, F., Jiménez-Donaire, M. J., et al. 2018, MNRAS, 475, 3909, doi: [`10.1093/mnras/sty059`](http://doi.org/10.1093/mnras/sty059)

(ref: dacunha2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13, doi: [`10.1088/0004-637X/766/1/13`](http://doi.org/10.1088/0004-637X/766/1/13)

(ref: dacunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: dacunha2021) da Cunha, E., Hodge, J. A., Casey, C. M., et al. 2021, ApJ, 919, 30, doi: [`10.3847/1538-4357/ac0ae0`](http://doi.org/10.3847/1538-4357/ac0ae0)

(ref: danielson2011) Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2011, MNRAS, 410, 1687, doi: [`10.1111/j.1365-2966.2010.17549.x`](http://doi.org/10.1111/j.1365-2966.2010.17549.x)

(ref: dannerbauer2019) Dannerbauer, H., Harrington, K., Dı́az-Sánchez, A., et al. 2019, AJ, 158, 34, doi: [`10.3847/1538-3881/aaf50b`](http://doi.org/10.3847/1538-3881/aaf50b)

(ref: debreuck2014) De Breuck, C., Williams, R. J., Swinbank, M., et al. 2014, A&A, 565, A59, doi: [`10.1051/0004-6361/201323331`](http://doi.org/10.1051/0004-6361/201323331)

(ref: decarli2020) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110, doi: [`10.3847/1538-4357/abaa3b`](http://doi.org/10.3847/1538-4357/abaa3b)

(ref: dessauges-zavadsky2020) Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5, doi: [`10.1051/0004-6361/202038231`](http://doi.org/10.1051/0004-6361/202038231)

(ref: downes1998) Downes, D., & Solomon, P. M. 1998, ApJ, 507, 615, doi: [`10.1086/306339`](http://doi.org/10.1086/306339)

(ref: Dudzeviciute2020) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, Monthly Notices of the Royal Astronomical Society, 494, 3828–3860, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: dunne2022) Dunne, L., Maddox, S. J., Papadopoulos, P. P., Ivison, R. J., & Gomez, H. L. 2022, MNRAS, doi: [`10.1093/mnras/stac2098`](http://doi.org/10.1093/mnras/stac2098)

(ref: frayer2011) Frayer, D. T., Harris, A. I., Baker, A. J., et al. 2011, ApJL, 726, L22, doi: [`10.1088/2041-8205/726/2/L22`](http://doi.org/10.1088/2041-8205/726/2/L22)

(ref: friascastillo2022) Frias Castillo, M., Rybak, M., Hodge, J., et al. 2022, ApJ, 930, 35, doi: [`10.3847/1538-4357/ac6105`](http://doi.org/10.3847/1538-4357/ac6105)

(ref: friascastillo2023) Frias Castillo, M., Hodge, J., Rybak, M., et al. 2023, ApJ, 945, 128, doi: [`10.3847/1538-4357/acb931`](http://doi.org/10.3847/1538-4357/acb931)

(ref: geach2017) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789, doi: [`10.1093/mnras/stw2721`](http://doi.org/10.1093/mnras/stw2721)

(ref: greve2005) Greve, T. R., Bertoldi, F., Smail, I., et al. 2005, MNRAS, 359, 1165, doi: [`10.1111/j.1365-2966.2005.08979.x`](http://doi.org/10.1111/j.1365-2966.2005.08979.x)

(ref: gururajan2023) Gururajan, G., Béthermin, M., Sulzenauer, N., et al. 2023, A&A, 676, A89, doi: [`10.1051/0004-6361/202346449`](http://doi.org/10.1051/0004-6361/202346449)

(ref: hanbing1968) Habing, H. J. 1968, , 19, 421

(ref: hainline2006) Hainline, L. J., Blain, A. W., Greve, T. R., et al. 2006, ApJ, 650, 614, doi: [`10.1086/507443`](http://doi.org/10.1086/507443)

(ref: harrington2018) Harrington, K. C., Yun, M. S., Magnelli, B., et al. 2018, MNRAS, 474, 3866, doi: [`10.1093/mnras/stx3043`](http://doi.org/10.1093/mnras/stx3043)

(ref: harrington2021) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, ApJ, 908, 95, doi: [`10.3847/1538-4357/abcc01`](http://doi.org/10.3847/1538-4357/abcc01)

(ref: harris2012) Harris, A. I., Baker, A. J., Frayer, D. T., et al. 2012, ApJ, 752, 152, doi: [`10.1088/0004-637X/752/2/152`](http://doi.org/10.1088/0004-637X/752/2/152)

(ref: heintz_watson2020) Heintz, K. E., & Watson, D. 2020, ApJL, 889, L7, doi: [`10.3847/2041-8213/ab6733`](http://doi.org/10.3847/2041-8213/ab6733)

(ref: hildebrand1983) Hildebrand, R. H. 1983, QJRAS, 24, 267

(ref: hill2018) Hill, R., Chapman, S. C., Scott, D., et al. 2018, MNRAS, 477, 2042, doi: [`10.1093/mnras/sty746`](http://doi.org/10.1093/mnras/sty746)

(ref: hodge2012) Hodge, J. A., Carilli, C. L., Walter, F., et al. 2012, ApJ, 760, 11, doi: [`10.1088/0004-637X/760/1/11`](http://doi.org/10.1088/0004-637X/760/1/11)

(ref: hodge+dacunha2020) Hodge, J. A., & da Cunha, E. 2020, Royal Society Open Science, 7, 200556, doi: [`10.1098/rsos.200556`](http://doi.org/10.1098/rsos.200556)

(ref: hollenbach1999) Hollenbach, D. J., & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173, doi: [`10.1103/RevModPhys.71.173`](http://doi.org/10.1103/RevModPhys.71.173)

(ref: hughes1998) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, Nature, 394, 241, doi: [`10.1038/28328`](http://doi.org/10.1038/28328)

(ref: huynh2017) Huynh, M. T., Emonts, B. H. C., Kimball, A. E., et al. 2017, MNRAS, 467, 1222, doi: [`10.1093/mnras/stx156`](http://doi.org/10.1093/mnras/stx156)

(ref: ikeda2002) Ikeda, M., Oka, T., Tatematsu, K., Sekimoto, Y., & Yamamoto, S. 2002, ApJS, 139, 467, doi: [`10.1086/338761`](http://doi.org/10.1086/338761)

(ref: israel2015) Israel, F. P., Rosenberg, M. J. F., & van der Werf, P. 2015, A&A, 578, A95, doi: [`10.1051/0004-6361/201425175`](http://doi.org/10.1051/0004-6361/201425175)

(ref: ivison2011) Ivison, R. J., Papadopoulos, P. P., Smail, I., et al. 2011, MNRAS, 412, 1913, doi: [`10.1111/j.1365-2966.2010.18028.x`](http://doi.org/10.1111/j.1365-2966.2010.18028.x)

(ref: Jarugula2021) Jarugula, S., Vieira, J. D., Weiss, A., et al. 2021, ApJ, 921, 97, doi: [`10.3847/1538-4357/ac21db`](http://doi.org/10.3847/1538-4357/ac21db)

(ref: jiao2017) Jiao, Q., Zhao, Y., Zhu, M., et al. 2017, ApJL, 840, L18, doi: [`10.3847/2041-8213/aa6f0f`](http://doi.org/10.3847/2041-8213/aa6f0f)

(ref: jiao2019) Jiao, Q., Zhao, Y., Lu, N., et al. 2019, ApJ, 880, 133, doi: [`10.3847/1538-4357/ab29ed`](http://doi.org/10.3847/1538-4357/ab29ed)

(ref: jin2019) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, ApJ, 887, 144, doi: [`10.3847/1538-4357/ab55d6`](http://doi.org/10.3847/1538-4357/ab55d6)

(ref: shouwen2022) —. 2022, A&A, 665, A3, doi: [`10.1051/0004-6361/202243341`](http://doi.org/10.1051/0004-6361/202243341)

(ref: kaasinen2019) Kaasinen, M., Scoville, N., Walter, F., et al. 2019, ApJ, 880, 15, doi: [`10.3847/1538-4357/ab253b`](http://doi.org/10.3847/1538-4357/ab253b)

(ref: kamenetzky2016) Kamenetzky, J., Rangwala, N., Glenn, J., Maloney, P. R., & Conley, A. 2016, ApJ, 829, 93, doi: [`10.3847/0004-637X/829/2/93`](http://doi.org/10.3847/0004-637X/829/2/93)

(ref: kaufman2006) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ, 644, 283, doi: [`10.1086/503596`](http://doi.org/10.1086/503596)

(ref: keene1997) Keene, J., Lis, D. C., Phillips, T. G., & Schilke, P. 1997, IAU Symposium, 178, 129

(ref: kelly2007) Kelly, B. C. 2007, ApJ, 665, 1489, doi: [`10.1086/519947`](http://doi.org/10.1086/519947)

(ref: kennicutt1998) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: kennicutt+evans2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: AS2COSPEC_II2024) Liao, C.-L., Chen, C.-C., Wang, W.-H., et al. 2024, ApJ, 961, 226, doi: [`10.3847/1538-4357/ad148c`](http://doi.org/10.3847/1538-4357/ad148c)

(ref: liu2019) Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235, doi: [`10.3847/1538-4357/ab578d`](http://doi.org/10.3847/1538-4357/ab578d)

(ref: magdis2011) Magdis, G. E., Daddi, E., Elbaz, D., et al. 2011, ApJL, 740, L15, doi: [`10.1088/2041-8205/740/1/L15`](http://doi.org/10.1088/2041-8205/740/1/L15)

(ref: magnelli2012lir_smg) Magnelli, B., Lutz, D., Santini, P., et al. 2012, A&A, 539, A155, doi: [`10.1051/0004-6361/201118312`](http://doi.org/10.1051/0004-6361/201118312)

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: montoya2023) Montoya Arroyave, I., Cicone, C., Makroleivaditi, E., et al. 2023, A&A, 673, A13, doi: [`10.1051/0004-6361/202245046`](http://doi.org/10.1051/0004-6361/202245046)

(ref: nesvadba2019) Nesvadba, N. P. H., Cañameras, R., Kneissl, R., et al. 2019, A&A, 624, A23, doi: [`10.1051/0004-6361/201833777`](http://doi.org/10.1051/0004-6361/201833777)

(ref: ojha2001) Ojha, R., Stark, A. A., Hsieh, H. H., et al. 2001, ApJ, 548, 253, doi: [`10.1086/318693`](http://doi.org/10.1086/318693)

(ref: papadopoulos2022) Papadopoulos, P., Dunne, L., & Maddox, S. 2022, MNRAS, 510, 725, doi: [`10.1093/mnras/stab3194`](http://doi.org/10.1093/mnras/stab3194)

(ref: papadopoulos2004) Papadopoulos, P. P., & Greve, T. R. 2004, ApJL, 615, L29, doi: [`10.1086/426059`](http://doi.org/10.1086/426059)

(ref: papadopoulos2012) Papadopoulos, P. P., van der Werf, P. P., Xilouris, E. M., et al. 2012, MNRAS, 426, 2601, doi: [`10.1111/j.1365-2966.2012.21001.x`](http://doi.org/10.1111/j.1365-2966.2012.21001.x)

(ref: planck2016) Planck Collaboration, Ade, P. A. R., Aghanim, N., et al. 2016, A&A, 594, A13, doi: [`10.1051/0004-6361/201525830`](http://doi.org/10.1051/0004-6361/201525830)

(ref: popping2022) Popping, G., & Péroux, C. 2022, MNRAS, 513, 1531, doi: [`10.1093/mnras/stac695`](http://doi.org/10.1093/mnras/stac695)

(ref: popping2017) Popping, G., Decarli, R., Man, A. W. S., et al. 2017, A&A, 602, A11, doi: [`10.1051/0004-6361/201730391`](http://doi.org/10.1051/0004-6361/201730391)

(ref: popping2023) Popping, G., Shivaei, I., Sanders, R. L., et al. 2023, A&A, 670, A138, doi: [`10.1051/0004-6361/202243817`](http://doi.org/10.1051/0004-6361/202243817)

(ref: pound2008) Pound, M. W., & Wolfire, M. G. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 394, Astronomical Data Analysis Software and Systems XVII, ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654

(ref: remy2017) Remy, Q., Grenier, I. A., Marshall, D. J., & Casandjian, J. M. 2017, A&A, 601, A78, doi: [`10.1051/0004-6361/201629632`](http://doi.org/10.1051/0004-6361/201629632)

(ref: riechers2020a-vlaspecs) Riechers, D. A., Boogaard, L. A., Decarli, R., et al. 2020a, ApJL, 896, L21, doi: [`10.3847/2041-8213/ab9595`](http://doi.org/10.3847/2041-8213/ab9595)

(ref: riechers2020b-coldz) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020b, ApJ, 895, 81, doi: [`10.3847/1538-4357/ab8c48`](http://doi.org/10.3847/1538-4357/ab8c48)

(ref: Rigopoulou2018) Rigopoulou, D., Pereira-Santaella, M., Magdis, G. E., et al. 2018, MNRAS, 473, 20, doi: [`10.1093/mnras/stx2311`](http://doi.org/10.1093/mnras/stx2311)

(ref: rybak2020) Rybak, M., Hodge, J. A., Vegetti, S., et al. 2020, MNRAS, 494, 5542, doi: [`10.1093/mnras/staa879`](http://doi.org/10.1093/mnras/staa879)

(ref: Rybak2023) Rybak, M., van Marrewijk, J., Hodge, J. A., et al. 2023, A&A, 679, A119, doi: [`10.1051/0004-6361/202347315`](http://doi.org/10.1051/0004-6361/202347315)

(ref: saintonge2013) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2, doi: [`10.1088/0004-637X/778/1/2`](http://doi.org/10.1088/0004-637X/778/1/2)

(ref: saintonge2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: sandstrom2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5, doi: [`10.1088/0004-637X/777/1/5`](http://doi.org/10.1088/0004-637X/777/1/5)

(ref: schmidt1959) Schmidt, M. 1959, ApJ, 129, 243, doi: [`10.1086/146614`](http://doi.org/10.1086/146614)

(ref: lambda_database) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369, doi: [`10.1051/0004-6361:20041729`](http://doi.org/10.1051/0004-6361:20041729)

(ref: scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: scoville2017) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150, doi: [`10.3847/1538-4357/aa61a0`](http://doi.org/10.3847/1538-4357/aa61a0)

(ref: sharon2016) Sharon, C. E., Riechers, D. A., Hodge, J., et al. 2016, ApJ, 827, 18, doi: [`10.3847/0004-637X/827/1/18`](http://doi.org/10.3847/0004-637X/827/1/18)

(ref: simpson2019) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43, doi: [`10.3847/1538-4357/ab23ff`](http://doi.org/10.3847/1538-4357/ab23ff)

(ref: simpson2020) Simpson, J. M., Smail, I., Dudzevičiūtė, U., et al. 2020, MNRAS, 495, 3409, doi: [`10.1093/mnras/staa1345`](http://doi.org/10.1093/mnras/staa1345)

(ref: smail1997) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5, doi: [`10.1086/311017`](http://doi.org/10.1086/311017)

(ref: solomon2005) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: stach2018) Stach, S. M., Smail, I., Swinbank, A. M., et al. 2018, ApJ, 860, 161, doi: [`10.3847/1538-4357/aac5e5`](http://doi.org/10.3847/1538-4357/aac5e5)

(ref: swinbank2014) Swinbank, A. M., Simpson, J. M., Smail, I., et al. 2014, MNRAS, 438, 1267, doi: [`10.1093/mnras/stt2273`](http://doi.org/10.1093/mnras/stt2273)

(ref: tacconi2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157, doi: [`10.1146/annurev-astro-082812-141034`](http://doi.org/10.1146/annurev-astro-082812-141034)

(ref: tacconi2008) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246, doi: [`10.1086/587168`](http://doi.org/10.1086/587168)

(ref: tacconi2010) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781, doi: [`10.1038/nature08773`](http://doi.org/10.1038/nature08773)

(ref: tacconi2013) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: thompson2012) Thomson, A. P., Ivison, R. J., Smail, I., et al. 2012, MNRAS, 425, 2203, doi: [`10.1111/j.1365-2966.2012.21584.x`](http://doi.org/10.1111/j.1365-2966.2012.21584.x)

(ref: tielens1985) Tielens, A. G. G. M., & Hollenbach, D. 1985, ApJ, 291, 722, doi: [`10.1086/163111`](http://doi.org/10.1086/163111)

(ref: tomasetti2014) Tomassetti, M., Porciani, C., Romano-Diaz, E., Ludlow, A. D., & Papadopoulos, P. P. 2014, MNRAS, 445, L124, doi: [`10.1093/mnrasl/slu137`](http://doi.org/10.1093/mnrasl/slu137)

(ref: valentino2018) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27, doi: [`10.3847/1538-4357/aaeb88`](http://doi.org/10.3847/1538-4357/aaeb88)

(ref: valentino2020) Valentino, F., Daddi, E., Puglisi, A., et al. 2020a, A&A, 641, A155, doi: [`10.1051/0004-6361/202038322`](http://doi.org/10.1051/0004-6361/202038322)

(ref: valentino2020-co) —. 2020b, A&A, 641, A155, doi: [`10.1051/0004-6361/202038322`](http://doi.org/10.1051/0004-6361/202038322)

(ref: radex2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627, doi: [`10.1051/0004-6361:20066820`](http://doi.org/10.1051/0004-6361:20066820)

(ref: walter2011) Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011, ApJ, 730, 18, doi: [`10.1088/0004-637X/730/1/18`](http://doi.org/10.1088/0004-637X/730/1/18)

(ref: walter2020) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111, doi: [`10.3847/1538-4357/abb82e`](http://doi.org/10.3847/1538-4357/abb82e)

(ref: wang2022) Wang, T.-M., Magnelli, B., Schinnerer, E., et al. 2022, A&A, 660, A142, doi: [`10.1051/0004-6361/202142299`](http://doi.org/10.1051/0004-6361/202142299)

(ref: weiss2005a) Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429, L25, doi: [`10.1051/0004-6361:200400085`](http://doi.org/10.1051/0004-6361:200400085)

(ref: weiss2003) Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A, 409, L41, doi: [`10.1051/0004-6361:20031337`](http://doi.org/10.1051/0004-6361:20031337)

(ref: xue2018) Xue, R., Fu, H., Isbell, J., et al. 2018, ApJL, 864, L11, doi: [`10.3847/2041-8213/aad9a9`](http://doi.org/10.3847/2041-8213/aad9a9)

(ref: yang2017) Yang, C., Omont, A., Beelen, A., et al. 2017, A&A, 608, A144, doi: [`10.1051/0004-6361/201731391`](http://doi.org/10.1051/0004-6361/201731391)

(ref: zhang2016) Zhang, Z.-Y., Papadopoulos, P. P., Ivison, R. J., et al. 2016, Royal Society Open Science, 3, 160025, doi: [`10.1098/rsos.160025`](http://doi.org/10.1098/rsos.160025)

[^1]: AS2COS0001.1 and AS2COS0008.1 have companion galaxies nearby (cite: AS2COSPEC2022) which we cannot resolve at the resolution of our observations. Although the bulk of the emission is most likely dominated by the primary source, the \[C I\] line flux densities are likely overestimated. Since the CO(1–0) measured fluxes also suffer from the same problem, we do not correct the fluxes presented and treat both sources as a single target.

[^2]: While the choices of $T_\mathrm{dust}$ and $\beta$ have a relatively minor effect on the derived $L_\mathrm{850\mu m,rest}$ from the observed–frame 3mm dust continuum, the impact becomes more severe if the observed wavelength does not probe the RJ tail of the dust emission. If we had used observed–frame 850 $\mu$m dust continuum observations, which are more commonly available at high redshift, the derived luminosities could have been overestimated by more than 50%.

</paper>

Write the methods card for this paper.