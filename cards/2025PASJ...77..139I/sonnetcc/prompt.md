# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025PASJ...77..139I\sonnetcc\reply.txt

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
 "bibcode": "2025PASJ...77..139I",
 "title": "Detection of the [O I] 63 µm emission line from the z = 6.04 quasar J2054-0005",
 "year": 2025,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Ishii, Nozomi",
 "n_authors": 26,
 "arxiv_id": "2408.09944",
 "doi": "10.1093/pasj/psae105",
 "alma_projects_linked_by_archive": [
  "2016.1.01063.S"
 ]
}
```

Paper text:
<paper>
# Detection of the \[O i\] $63$ $\mu$m emission line from the $z = 6.04$ quasar J2054-0005

## Abstract

We report the highest-redshift detection of \[O i\] 63 $\mu$m from a luminous quasar, J2054-0005, at $z=6.04$ based on the Atacama Large Millimeter/sub-millimeter Array Band 9 observations. The \[O i\] 63 $\mu$m line luminosity is $(4.5\pm1.5) \times 10^{9}~L_{\rm \odot}$, corresponding to the \[O i\] 63 $\mu$m-to-far-infrared luminosity ratio of $\approx 6.7\times10^{-4}$, which is consistent with the value obtained in the local universe. Remarkably, \[O i\] 63 $\mu$m is as bright as \[C ii\] 158 $\mu$m, resulting in the \[O i\]-to-\[C ii\] line luminosity ratio of $1.3\pm0.5$. Based on a careful comparison of the luminosity ratios of \[O i\] 63 $\mu$m, \[C ii\] 158 $\mu$m, and dust continuum emission to models of photo-dissociation regions, we find that J2054-0005 has a gas density log($n_{\rm H}$/cm$^{-3}$)$=3.7\pm0.3$ and an incident far-ultraviolet radiation field of log($G/G_{\rm 0}$) $= 3.0\pm0.1$, showing that \[O i\] 63 $\mu$m serves as an important coolant of the dense and warm gas in J2054-0005. A close examination of the \[O i\] and \[C ii\] line profiles suggests that the \[O i\] line may be partially self-absorbed, however deeper observations are needed to verify this conclusion. Regardless, the gas density and incident radiation field are in a broad agreement with the values obtained in nearby star-forming galaxies and objects with \[O i\] 63 $\mu$m observations at $z=1-3$ with the Herschel Space Observatory. These results demonstrate the power of ALMA high-frequency observations targeting \[O i\] 63 $\mu$m to examine the properties of photo-dissociation regions in high-redshift galaxies.

Graduate School of Pure and Applied Sciences, University of Tsukuba, 1-1-1 Tennodai, Tsukuba, Ibaraki 305-8571, Japan Systems Engineering Consultants Co.,LTD. (SEC) Setagaya Business Square 4-10-1 Yoga, Setagaya-ku, Tokyo 158-0097, Japan Tomonaga Center for the History of the Universe, University of Tsukuba, 1-1-1 Tennodai, Tsukuba, Ibaraki 305-8571, Japan Department of Physics, Winona State University, Winona, MN 55987, USA Faculty of Electrical Engineering, Mathematics and Computer Science, Delft University of Technology, Mekelweg 4, 2628 CD Delft, The Netherlands Leiden Observatory, Leiden University, P.O. Box 9513, 2300 RA Leiden, The Netherlands SRON - Netherlands Institute for Space Research, Niels Bohrweg 4, 2333 CA Leiden, The Netherlands Department of Physics, School of Advanced Science and Engineering, Faculty of Science and Engineering, Waseda University, 3-4-1 Okubo, Shinjuku, Tokyo 169-8555, Japan Waseda Research Institute for Science and Engineering, Faculty of Science and Engineering, Waseda University, 3-4-1 Okubo, Shinjuku, Tokyo 169-8555, Japan Faculty of Information Science, Shunan University, 843-4-2 Gakuendai, Shunanshi, Yamaguchi 745-8566, Japan National Center for Nuclear Research, Pasteura 7, 02-093 Warsaw, Poland SISSA, Via Bonomea 265, 34136 Trieste, Italy Department of Astronomy, The University of Texas at Austin, Austin, TX 78712, USA Institute for the Advancement of Higher Education, Hokkaido University, Kita 17 Nishi 8, Kita-ku, Sapporo, Hokkaido 060-0817, Japan Department of Cosmosciences, Graduate School of Science, Hokkaido University, Kita 10 Nishi 8, Kita-ku, Sapporo, Hokkaido 060-0810, Japan National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan The Graduate University for Advanced Studies (SOKENDAI), 2-21-1 Osawa, Mitaka, Tokyo 181-8588, Japan Department of Physics, Graduate School of Science, Nagoya University Furo, Chikusa, Nagoya, Aichi 464-8602, Japan Research Center for Space and Cosmic Evolution, Ehime University, 2-5 Bunkyo-cho, Matsuyama, Ehime 790-8577, Japan Department of Physics, The University of Tokyo, 7-3-1 Hongo, Bunkyo, Tokyo 113-0033, Japan Center for Computational Sciences, University of Tsukuba, 1-1-1 Tennodai, Tsukuba, Ibaraki 305-8577, Japan Department of Earth and Space Sciences, Chalmers University of Technology, Onsala Observatory, 439 94 Onsala, Sweden Center for Frontier Science, Chiba University, 1-33 Yayoi-cho, Inage-ku, Chiba 263-8522, Japan Department of Astronomy, University of Geneva, Chemin Pegasi 51, 1290 Versoix, Switzerland Max-Planck-Institut für Astronomie, Königstuhl 17, D-69117 Heidelberg, Germany Kavli Institute for the Physics and Mathematics of the Universe (WPI), UT Institute for Advanced Study, The University of Tokyo, Kashiwa, Chiba 277-8583, Japan Research Center for the Early Universe, School of Science, The University of Tokyo, 7-3-1 Hongo, Bunkyo, Tokyo 113-0033, Japan

# Introduction

Quasars are powered by supermassive black holes (SMBHs) with masses of $\sim 10^{8-10} M_{\rm \odot}$ (e.g., (cite: inayoshi2020) and references therein). In the local Universe, there is a well-known correlation between the central black hole mass and the bulge mass (e.g., (cite: kormendy2013)). Given the coevolution of SMBHs and their host galaxies, understanding detailed properties of the host galaxies in the early universe is a key to understand the formation and evolution of SMBHs (e.g., (cite: valiante2017)).

The interstellar medium (ISM) of high-redshift ($z$) quasar host galaxies is often studied with the brightest far-infrared (FIR) fine structure line, \[C ii\] 158 $\mu$m, as well as with carbon monoxide (CO) emission lines, and dust continuum emission (e.g., (cite: venemans2018; decarli2018; izumi2019; decarli2020; pensabene2024; tripodi2024)). These studies have shown that the quasar host galaxies can be characterized by high star-formation rates (SFR $\sim50-3000$ $M_{\rm \odot}$ yr$^{-1}$), molecular gas masses ($\sim 10^{10}$ $M_{\rm \odot}$), and dust masses ($\sim 10^{7-9}$ $M_{\rm \odot}$).

The \[O i\] $^{3}P_{2} \rightarrow ^{3}P_{1}$ line at the rest-frame wavelength of $63$ $\mu$m (rest-frame frequency of $4744.77749$ GHz), hereafter \[O i\] 63 $\mu$m, has a critical density of $n_{\rm H, crit.} \sim 2.5 \times 10^{5}$ cm$^{-3}$ at the temperature of 100 K and emitting level with an equivalent temperature of $T_{\rm *} = \Delta E/k = 228$ K above the ground ((cite: draine2011)). Compared to the critical density of \[C ii\] 158 $\mu$m, $n_{\rm H, crit.} \sim 3 \times 10^{3}$ cm$^{-3}$ at the temperature of 100 K, and the equivalent temperature $T_{\rm *} = \Delta E/k = 91.25$ K, the \[O i\] 63 $\mu$m line traces high-density, high-temperature neutral gas ((cite: kaufman1999; kaufman2006; narayanan2017)). Thus, combinations of \[O i\] 63 $\mu$m, \[C ii\] 158 $\mu$m, and dust continuum data allow us to estimate the gas density and temperature in photo-dissociated regions (PDRs). Due to the high equivalent temperature, \[O i\] 63 $\mu$m also has an advantage that it is less affected by the cosmic microwave background radiation, which makes it a reliable tracer of neutral ISM at high redshift.

Initial campaigns for the \[O i\] 63 $\mu$m line observations include the NASA Lear jet telescope system targeting the Orion nebula (M42) and Omega nebular (M17) ((cite: melnick1979)) and a balloon-borne telescope targeting the Orion nebula ((cite: furniss1983)).

The \[O i\] 63 $\mu$m line was observed in external galaxies with the Infarad Space Observatory (ISO) (e.g., (cite: malhotra2001; brauher2008)) and the Herschel Space Observatory (hereafter Herschel) (e.g., (cite: farrah2013; madden2013; cormier2015; diaz-santos2017; herrera-camus2018)) in metal-rich spiral galaxies, ultra-luminous infrared galaxies (ULIRGs), and blue compact dwarf galaxies.

These observations showed that \[O i\] 63 $\mu$m is a dominant coolant in dense PDRs, with a typical \[O i\]-to-FIR luminosity ratio $L_{\rm [OI]63\ensuremath{\mu}m}/L_{\rm FIR}$ $\approx 10^{-4} - 10^{-3}$, where $L_{\rm FIR}$ is integrated over $42-122~\ensuremath{\mu}m$.

The \[O i\] 63 $\mu$m line observations at $z\sim1-3$ were conducted by Herschel, mainly in gravitationally-lensed sub-millimeter galaxies (SMGs) (e.g., (cite: sturm2010; coppin2012; brisbin2015; wardlow2017; zhang2018; wagg2020)) and in the Cloverleaf quasar at $z=2.46$ ((cite: uzgil2016)).

The detections unveiled enhanced luminosity ratios, $L_{\rm [OI]63\ensuremath{\mu}m}/L_{\rm FIR}$ ranging from $\approx 10^{-3}$ to $10^{-2}$, but still with a limited number of detections ($N\sim 15$).

On the other hand, a stacking of the non-detections of individual SMGs in (cite: wardlow2017) resulted in a detection of \[O i\] 63 $\mu$m, yielding $L_{\rm [OI]63\ensuremath{\mu}m}/L_{\rm FIR} = (3.6 \pm 1.2) \times 10^{-4}$, showing a diversity in the ISM properties of high-$z$ galaxies.

At $z \sim 4-7$, the \[O i\] 63 $\mu$m line can be observed from the ground with e.g., the Atacama Large Millimeter/sub-millimeter Array (ALMA) in Band 9 - 10.

The \[O i\] 63 $\mu$m line observation at $z>4$ has been first reported by (cite: rybak2020). The authors observed a gravitationally-lensed SMG, G09 83808, at $z=6.027$ with the Atacama Pathfinder EXperiment (APEX) 12-m telescope. Although a $5\sigma$ \[O i\] 63 $\mu$m line was initially reported, subsequent follow-up observations with ALMA Band 9 did not confirm the line ((cite: rybak2023)).

(cite: litke2022) targeted \[O i\] 63 $\mu$m along with other FIR lines in a gravitationally-lensed SMG, SPT 0346-52, at $z=5.656$ with ALMA Band 9, resulting in a non-detection of \[O i\] 63 $\mu$m.

The first detection of \[O i\] 63 $\mu$m at $z>4$ was recently made with ALMA Band 10 in a non-lensed hyper-luminous ($L_{\rm FIR} \sim 3.5\times10^{13}~L_{\odot}$) active galactic nucleus (AGN), W2246-0526, at $z=4.6$ ((cite: fernandez_aranda2024)).

Clearly, the number of \[O i\] 63 $\mu$m observations at $z>4$ is still scarce.

A contributing factor to this scarcity may be that \[O i\] 63 $\mu$m emission is typically optically thick (e.g., (cite: goldsmith2021)), unlike most of far-IR fine-structure lines like \[C ii\] 158 $\mu$m. As such, \[O i\] 63 $\mu$m emission is detected only from front faces of emitting clouds. Additionally, if sufficient neutral oxygen is along the line-of-sight in a galaxy, the \[O i\] 63 $\mu$m line can be readily self-absorbed. For example, self-absorption is seen in a nearby large molecular cloud DR 21 ((cite: poglitsch1996)), a diffused nebula NGC 6334 ((cite: kraemer1998)), and a highly obscured H ii region Sgr B2 ((cite: baluteau1997)) with massive star formation activity. In extra-galactic sources, nearly half of the local ULIRGS in (cite: rosenberg2015) show significant missing flux with several sources show the 63 $\mu$m line nearly completely absorbed out (see also (cite: gonzalez-alfonso2012)). Determining if \[O i\] 63 $\mu$m emission is optically thick requires comparing the line to the optically thin \[O i\] 145 $\mu$m line, while assessing self-absorption requires a significant signal-to-noise ratio in the spectrum to identify absorption features. (cite: fernandez_aranda2024) detect both the \[O i\] 63 and 145 $\mu$m lines, and show their line ratios suggest the \[O i\] 63 $\mu$m line emission is indeed optically thick. However, the data were not sensitive enough to identify the narrow absorption feature in W2246-0526.

In this paper, we report a new detection of \[O i\] $63$ $\mu$m in a distant quasar, SDSS J2054-0005, at $z = 6.0$ based on ALMA Band 9 archival data (§[2](#sec:sample_data)). To date, this is the most distant detection of \[O i\] 63 $\mu$m. We present our calculations on the \[O i\] 63 $\mu$m luminosity and its luminosity ratios against $L_{\rm FIR}$ and the \[C ii\] 158 $\mu$m luminosity in §[3](#sec:results). In §[4](#sec:discussion), we perform PDR modeling to constrain the neutral gas properties. We summarize our results in §[5](#sec:summary).

Through out this paper, we assume a $\Lambda$ cold dark matter cosmology with $\Omega_{m} = 0.272$, $\Omega_{\Lambda} = 0.728$, and $H_{0} = 70.4$ km s$^{-1}$ Mpc$^{-1}$ ((cite: komatsu2011)). At the redshift of the source ($z = 6.04$), the age of the universe is 0.946 Gyr and an angular size of $1''$ corresponds to a proper distance of 5.85 kpc. The solar luminosity is $L_{\odot} = 3.839 \times 10^{33}$ erg s$^{-1}$.

# Observations and Data

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Data | Achieved sensitivity in r.m.s. | Beam size FWHM | Beam PA |
|  | (mJy/beam) | $\rm{(arcsec \times arcsec)}$ | (degree) |
| Dust continuum | 0.55 | $0.64 \times 0.56$ | 72 |
| \[O$\rm I$\] 63 $\mu$m cube (50 km s$^{-1}$ bin) | 3.68 | $0.65 \times 0.56$ | 83 |

## The target: J2054-0005

The quasar J2054-0005 was originally discovered in the Sloan Digital Sky Survey (SDSS) ((cite: jiang2008)), and later detected in various emission lines of \[C ii\] $158$ $\mu$m (e.g., (cite: wang2013; venemans2020)), \[O iii\] $88$ $\mu$m ((cite: hashimoto2019)), CO(2-1) and CO(6-5) ((cite: shao2019)), CO(7-6) ((cite: decarli2020)), as well as in the OH $119$ $\mu$m absorption and emission ((cite: salak2024)). The redshift determined from these lines is $6.0391 \pm 0.0002$. J2054-0005 was also observed in \[C i\](2-1), however, it resulted in a non-detection ((cite: decarli2020)).

J2054-0005 is a non-lensed quasar, and has a bolometric luminosity of $\approx 3 \times 10^{13}~L_{\odot}$ ((cite: wang2013; farina2022)). The black hole mass is estimated to be $\sim (1.5-10.2) \times 10^{9}~M_{\odot}$ based on the single-epoch technique with an Eddington ratio of $\lambda_{\rm Edd} \sim 0.1-0.7$ ((cite: farina2022)). Based on a fit to multi-wavelength dust continuum data, J2054-0005 has a total infrared luminosity integrated over $8-1000$ $\mu$m, $L_{\rm TIR}$, $\approx 1 \times 10^{13}~L_{\odot}$ (cite: wang2013; hashimoto2019; tripodi2024), making it one of the brightest quasars at $z\gtrsim6$. The SFR estimated from $L_{\rm TIR}$ is $\approx 800~M_{\odot}$ yr$^{-1}$ after a correction of the AGN contribution (cite: salak2024).

![](Fig1.eps)

## ALMA Band 9 Data

ALMA Band 9 observation was carried out on 2017 March 22 as part of the ALMA Cycle 4 program (Project ID: 2016.1.01063.S, PI: C. Ferkinhoff). The antennas of the 12 m array observed a single field centered at ($\alpha_{\rm ICRS}$, $\delta_{\rm ICRS}$) = ($20^h 54^m 06.490s, -00\ensuremath{^\circ} 05' 14.80\ensuremath{''}$). Forty-two antennas were used, with baseline lengths ranging from $15.1 - 278.9$ m. This resulted in a maximum recoverable scale of $4.2\ensuremath{''}$ and a field-of-view of $8.6\ensuremath{''}$. The on-source integration time was $39$ minutes.

Four spectral windows were set at central frequencies of $672.3$, $674.1$, $676.0$, and $677.8$ GHz, referred to as SPW1, SPW2, SPW3, and SPW4, respectively. SPW2 observed the \[O i\] 63 $\mu$m line, whereas the other three SPWs observed dust continuum emission.

The quasar J1924-2914 and J2025-0735 was used for the bandpass and complex gain calibration, respectively. The flux was scaled using Titan, yielding a calibration uncertainty of less than 20% in ALMA Band 9, according to the ALMA Cycle 4 Proposer’s Guide[^1].

The data were reduced with the Common Astronomy Software Applications (CASA, (cite: mcmullin2022)) version 4.7.0. The CASA `tclean` task was used for imaging, with a natural weighting to optimize the point-source sensitivity. Table [\[tab1\]](#tab1) summarizes the resulting resolution and sensitivity of the data.

Continuum maps were created using all channels except for SPW2 that included \[O i\] 63 $\mu$m. The synthesized beam has a size of $0.64\ensuremath{''} \times 0.56\ensuremath{''}$ in the FWHM and a positional angle of $72^{\circ}$. The rms of the map is $0.55~\rm{mJy~beam^{-1}}$.

To create line cubes in SPW2, the CASA task `imcontsub`[^2] was first applied to subtract the continuum emission. We then created cubes with a velocity width of $50$ km s$^{-1}$ without *uv*-tapering. The cube has a synthesized beam size of $0.65\ensuremath{''} \times 0.56\ensuremath{''}$ and a positional angle of $83^{\circ}$. A typical rms sensitivity of the cube is $3.68$ mJy beam$^{-1}$ per $50$ km s$^{-1}$ bin.

# Results

## $63$-$\mu$m continuum emission

The data probe the dust continuum emission at a rest-frame wavelength of $\lambda_{\rm rest} \approx 63$ $\mu$m. The dust continuum emission is detected at a peak significance of $13\sigma$, as shown in the left panel of figure [1](#fig1). With the CASA task `imfit`, we obtain the flux density of $S_{\rm \nu, 63 \mu m} = 9.6 \pm 1.0$ mJy (table [1](#tab2)). The peak position is at ($\alpha_{\rm ICRS}$, $\delta_{\rm ICRS}$) = ($20^h 54^m 06.495s, -00\ensuremath{^\circ} 05' 14.46\ensuremath{''}$), well consistent with previous dust continuum positions (e.g., (cite: wang2013; hashimoto2019; salak2024)). The beam-deconvolved size of the continuum-emitting region is $(0.42\ensuremath{''} \pm 0.13\ensuremath{''}) \times (0.23\ensuremath{''} \pm 0.09\ensuremath{''})$, consistent with previous measurements within $2\sigma$ uncertainties: $(0.23\ensuremath{''} \pm 0.01\ensuremath{''}) \times (0.15\ensuremath{''} \pm 0.02\ensuremath{''})$ at $\lambda_{\rm rest} \approx87$ $\mu$m (cite: hashimoto2019) and $(0.27\ensuremath{''} \pm 0.03\ensuremath{''}) \times (0.26\ensuremath{''} \pm 0.03\ensuremath{''})$ at $\lambda_{\rm rest} \approx160$ $\mu$m (cite: wang2013). Finally, we note that the results on ALMA Band 9 dust continuum are recently reported in (cite: tripodi2024) based on the same data set. Our results are consistent with their results in the size and flux density measurements. Hereafter, we focus on \[O i\] 63 $\mu$m in this study.

|  | \[O i\] 63 $\mu$m |
|:--:|:--:|
| $z$ | $6.0385 \pm 0.0005$ |
| FWHM (km s$^{-1}$) | $192 \pm 49$ |
| $S_{\rm [OI]63}\Delta v$ (Jy km s$^{-1}$) | $1.81 \pm 0.61$ |
| $L_{\rm [OI]63}$ ($L_{\rm \odot}$) | $(4.5\pm1.5)\times10^{9}$ |
| size (beam-convolved) | ($0.58\ensuremath{''} \pm 0.11\ensuremath{''}$) $\times$ ($0.51\ensuremath{''} \pm 0.08\ensuremath{''}$) |
| size (beam-deconvolved) | $< (0.42\ensuremath{''} \times 0.23\ensuremath{''})$ |
|  | dust continuum |
| $S_{\rm \nu, 63 \ensuremath{\mu}m}$ (mJy) | $9.6\pm1.0$ |
| size (beam-convolved) | ($0.76\ensuremath{''} \pm 0.02\ensuremath{''}$) $\times$ ($0.61\ensuremath{''} \pm 0.02\ensuremath{''}$) |
| size (beam-deconvolved) | ($0.42\ensuremath{''} \pm 0.13\ensuremath{''}$) $\times$ ($0.23\ensuremath{''} \pm 0.09\ensuremath{''}$) |

: Summary of Observational Results

## \[O i\] $63$ $\mu$m 

The middle panel of figure [1](#fig1) shows the \[O i\] 63 $\mu$m intensity map (i.e., moment 0 map) integrated over the frequency range of $673.96 - 674.44$ GHz, corresponding to a velocity width of $250$ km s$^{-1}$ ($\approx$ FWHMs of \[C ii\] 158 $\mu$m and \[O iii\] 88 $\mu$m) centered at the observed redshift of $6.0391$. The noise level of the map is $\sigma = 0.42$ Jy beam$^{-1}$ km s$^{-1}$. The line is detected at the peak significance level of $5.0\sigma$. The peak position is at ($\alpha_{\rm ICRS}$, $\delta_{\rm ICRS}$) = ($20^h 54^m 06.501s, -00\ensuremath{^\circ} 05' 14.42\ensuremath{''}$), well consistent with those for other emission lines (see (cite: salak2024) for a detailed comparison on the peak positions of emission lines and the optical continuum emission from the quasar).

The right panel of figure [1](#fig1) shows the continuum-subtracted spectrum extracted from an aperture that encloses the $2\sigma$-region in the integrated intensity map. We apply a Gaussian profile to the spectrum with the *scipy* `curve_fit` function, where we use the SPWs of 1, 2, and 3. To obtain uncertainties on fitting parameters, the noise level is measured from the frequency ranges in \[671.3:673.5\] GHz and \[674.6:676.8\] GHz. We obtain the line FWHM of $192\pm49$ km s$^{-1}$ and $z=6.0385\pm0.0005$. We measure the line flux with the CASA task `imfit` assuming a 2D Gaussian profile for the intensity map integrated over a velocity width of 500 km s$^{-1}$ ($\approx 2.6\times$FWHM), resulting in $1.81 \pm 0.61$ Jy km s$^{-1}$. With Equation ([\[equ:lumi\]](#equ:lumi)) ((cite: solomon1992)), the luminosity is estimated to be $(4.53 \pm 1.52) \times 10^{9}L_{\odot}$,

$$\begin{eqnarray}
  L_{\rm line} = 1.04 \times 10^{-3} \left(\frac{S_{\rm line}\Delta v}{\rm Jy\, km\, s^{-1}}\right) \left(\frac{D_{\rm L}}{\rm Mpc}\right)^{2} \left(\frac{\nu_{\rm obs}}{\rm GHz}\right)L_{\odot},
  \label{equ:lumi}
\end{eqnarray}$$

where ${S_{\rm line} \Delta v}$, $D_{\rm L}$, and $\nu_{\rm obs}$ are the line flux, luminosity distance, and observed frequency, respectively. The \[O i\] 63 $\mu$m-emitting region is not spatially resolved. Under a reasonable assumption that the region has a smaller size than the continuum-emitting region (figure [1](#fig1)), we obtain the upper limit on the size to be $0.42\ensuremath{''}\times0.23\ensuremath{''}$.

Table [1](#tab2) summarizes the observational results.

## Luminosity Ratios

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Lines | FWHM | Luminosity | References |  |  |
|  | (km s$^{-1}$) | ($L_{\odot}$) |  |  |  |
|  $63$ $\mu$m  | $192\pm49$ | $(4.5 \pm 1.5) \times 10^{9}$ | This Study |  |  |
|  $158$ $\mu$m  | $243\pm 10$ | $(3.4 \pm 0.5) \times 10^{9}$ | (cite: wang2013) |  |  |
|  $88$ $\mu$m  | $282 \pm 17$ | $(6.8 \pm 0.6) \times 10^{9}$ | (cite: hashimoto2019) |  |  |
| (2-1) | \- | $< 1.1 \times 10^{8}$ | (cite: decarli2020) |  |  |
| FIR | \- | $(6.8 \pm 0.2) \times 10^{12}$ | (cite: salak2024) |  |  |

![image](Fig2_right.png) ![image](Fig2_left.png)

Table [\[tab3\]](#tab3) summarizes the previous line observations for J2054-0005[^3].

We also list $L_{\rm FIR}$ obtained in (cite: salak2024) who have performed multi-wavelength spectral energy distribution (SED) fitting for J2054-0005 using `CIGALE` ((cite: boquien2019)) that includes the contribution from both star-formation and AGN activity. We obtain $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR} = (6.7 \pm 2.2) \times 10^{-4}$ and $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm [CII] 158 \ensuremath{\mu}m} = 1.3 \pm 0.5$.

### $L_{\rm FIR}$ vs. $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$

The left panel of figure [2](#fig2) shows a comparison of $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ with the literature values.

These include nearby (U)LIRGs in the GOALS survey ((cite: diaz-santos2017); small grey circles), blue compact dwarf galaxies in the Herschel Dwarf Galaxy survey ((cite: cormier2015); small blue circles), and a compilation of other local galaxies observed by ISO ((cite: coppin2012); small black circles[^4]). (cite: delooze2014) have obtained an empirical relation between SFR and $L_{\rm [OI]63\ensuremath{\mu}m}$ in the local universe. The horizontal line with a shaded region indicates the relation between $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ and $L_{\rm FIR}$, where we convert SFR into $L_{\rm FIR}$ under the assumption of the Salpeter initial mass function ((cite: salpeter1955; kennicutt2012)).

The data also include the individual detections and non-detections of \[O i\] 63 $\mu$m at $z\sim 1-3$ ((cite: coppin2012; brisbin2015; wardlow2017; zhang2018; wagg2020); cyan squares), where the $3\sigma$ upper limits are shown with inverted triangles. The detection of \[O i\] 63 $\mu$m in a stacked spectrum of five lensed SMGs at $z\sim1-3$ is also shown ((cite: wardlow2017); cyan diamond).

We also include the data points of $z>4$ ALMA observations, where the inverted triangle indicate the $3\sigma$ upper limits: detection in J2054-0005 (this study; red star), a $z=4.601$ hyper-luminous AGN W2246-0526 ((cite: fernandez_aranda2024); green circle), non-detection of two sub-millimeter galaxies (SMGs), G09.83808 at $z = 6.027$ ((cite: rybak2023); purple inverted triangle) and SPT 0346–52 at $z=5.656$ ((cite: litke2022); orange inverted triangle). In this plot, we have corrected for the lensing magnification factors, if any.

The left panel of figure [2](#fig2) shows that the data points of two \[O i\]-detections at $z>4$ (J2054-0005 and W2246-0526) are well within the range of the local relation in (cite: delooze2014), but are lower $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ than those in the individual detections at $z=1-3$.

As discussed in (cite: wardlow2017), the initial campaign of \[O i\] 63 $\mu$m observations in high-$z$ SMGs in (cite: sturm2010) and (cite: coppin2012) have indicated that $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ may be high in the high-$z$ SMG population (cyan squares). On the other hand, the luminosity ratio in the stacked data of high-$z$ SMGs in (cite: wardlow2017) (cyan diamond) is consistent with the value obtained in the local universe. Interestingly, the three SMGs in (cite: coppin2012)[^5] and one SMG in (cite: sturm2010)[^6] have AGN activity, which (cite: wardlow2017) have attributed to a possible explanation for the enhanced luminosity ratio. However, the situation is complicated as the sample of six SMGs at $z=1-2$ in (cite: brisbin2015) uniformly shows high $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ regardless of the presence of AGN activity, where three of the six objects have AGN activity (cyan squares). Based on the fact that $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ of the four objects at $z>4$ is consistent with that in the local universe, we conclude that high-$z$ SMGs do not necessarily have high $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$.

### $L_{\rm FIR}$ vs. $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m}$

The right panel of figure [2](#fig2) shows a comparison of $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm [CII] 158 \ensuremath{\mu}m}$ with the literature values. The symbols are the same as those in the left panel, where the data points of $z=1-3$ are plotted if the line ratio is available.

The median and standard deviation of $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm [CII] 158 \ensuremath{\mu}m}$ in the local samples are $0.6$ and $0.3$, respectively (horizontal black line and grey shaded region).

The line ratios in the $z=1-3$ sample range from 0.5 to 2.0. The line raitos in the $z>4$ objects are $1.3\pm0.5$, $4.91\pm0.72$, $0.22$ ($3\sigma$) and $1.5$ ($3\sigma$) for J2054-0005, W2246-0526, G09.83808, and SPT 0346–52, respectively.

$L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm [CII] 158 \ensuremath{\mu}m}$ in J2054-0005 is consistent with the typical value obtained in the local universe within the uncertainty. On the other hand, W2246-0562 shows the second highest line ratio among the $z=0-6$ samples.

# Discussion

## AGN contribution to \[O i\] 63 $\mu$m in J2054-0005

Previous studies have shown that $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m}$ is enhanced in the presence of AGN activity. Based on the observations of 52 objects in the Herschel SHINING survey, (cite: herrera-camus2018) have found that only objects with AGN activity reach $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m} \gtrsim 1.6$ in the local universe (see also (cite: fukuchi2022)).

This is consistent with a theoretical study of (cite: abel2009) that predicts $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [C II] 158 \ensuremath{\mu}m}$ becomes higher in the presence of AGN activity. The calculations of (cite: abel2009) are based on CLOUDY ((cite: ferland2013)) that include both star-formation and AGN activity, and adopt an one-dimensional spherical geometry. The authors have found that $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m} \gtrsim 2$ can be achieved only in the presence of AGN activity (see their figure 6). According to (cite: abel2009), the higher line ratio is due to the fact that X-rays emitted by the AGN activity can penetrate deep into the cloud and heat the gas through photodissociatin and photoion-ization. Similarly, (cite: meijerink2007) have presented theoretical predictions for the $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [C II] 158 \ensuremath{\mu}m}$ ratio based on models accounting for both star formation and AGN activity. The result is consistent with (cite: abel2009) in the sense that the line ratio becomes higher in the presence of AGN activity. However, (cite: meijerink2007) have also shown that the line ratio can reach as high as $\sim 40$ with PDR models alone (i.e., without AGN acitivity) if the gas column density of PDR is sufficiently high (see their figure 2). Altogether, both the observational and theoretical studies show that $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m}$ is enhanced in the presence of AGN activity, although the exact value of the ratio is model-dependent.

In J2054-0005, the observed line ratio of $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m} = 1.3\pm0.5$ is close to the criterion presented in (cite: abel2009) and (cite: herrera-camus2018) within uncertainties, which does not allow us to strongly conclude whether the AGN activity affects the \[O i\] 63 $\mu$m line emission.

To further check if the AGN activity in J2054-0005 affects \[O i\] 63 $\mu$m, we refer to the results of (cite: decarli2020) who have concluded that PDRs rather than X-ray dominated regions (XDRs) better reproduce the observed lines of \[C ii\] 158 $\mu$m, \[C i\](2-1), and CO in a sample of $z\sim6$ luminous quasars including J2054-0005. Briefly, the authors have constructed PDR and XDR models with a wide variety of parameter space in the hydrogen density ($n_{\rm H}$), incident radiation field, incident X-ray flux, and the total hydrogen column density ($N_{\rm HI}$) based on CLOUDY. The authors have found that the line ratio of $L_{\rm [CII] 158 \ensuremath{\mu}m\ }/L_{\rm [CI](2-1)} > 10$ is achieved in PDRs, while it is $<10$ in XDRs at the column density of $N_{\rm HI}\gtrsim 10^{22}$ cm$^{-2}$ [^7]. The observed line ratio of $L_{\rm [CII] 158 \ensuremath{\mu}m\ }/L_{\rm [CI](2-1)} > 30$ indicates that the XDR does not strongly affect the emission lines in J2054-0005 ((cite: decarli2020)). In conclusion, we do not find evidence in J2054-0005 that the emission lines are strongly powered due to the AGN activity.

## PDR Modeling

Under the assumption that the \[O i\] 63 $\mu$m and \[C ii\] 158 $\mu$m lines are emitted not from XDRs but from PDRs in J2054-0005 (§[4.1](#subsec:discussion1)), we examine the PDR properties of J2054-0005 based on comparisons of the observed line luminosities of \[O i\] 63 $\mu$m, \[C ii\] 158 $\mu$m, and dust continuum emission (i.e., $L_{\rm FIR}$) to model predictions. These luminosities are commonly used to examine PDR properties (e.g., (cite: hollenbach1999; malhotra2001)). The $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m}$ ratio is sensitive to $n_{\rm H}$ because the line ratio strongly depends on density beyond the critical density of \[C ii\] 158 $\mu$m, $n_{\rm H, crit.} \sim 3 \times 10^{3}$ cm$^{-3}$, and \[O i\] 63 $\mu$m becomes an important coolant in the PDR at $G/G_{\rm 0}\gtrsim100$ ((cite: wolfire2022)). The ratio of $(L_{\rm [OI] 63 \ensuremath{\mu}m} + L_{\rm [CII] 158 \ensuremath{\mu}m})/L_{\rm FIR}$ traces the heating efficiency ((cite: wolfire2022)).

![](Fig3.pdf)

### Model Descriptions

We employ PDR Toolbox (PDRT; (cite: pound_wolfire2008; pound_wolfire2023)). The models have two codes, the “Wolfire-Kauffman" code and the KOSMA-tau code ((cite: rollig2013; pound_wolfire2023)). Following recent observational studies of high-$z$ quasars (e.g., (cite: shao2019; yang2019)), we use the latest version of the “Wolfire-Kauffman" code, which is referred to as the “wk2020" model in (cite: pound_wolfire2023). The model assumptions are summarized in table 1 in (cite: pound_wolfire2023). Briefly, the model assumes a plane-parallel geometry with UV radiation field, cosmic rays, and soft X-rays incident on one side. The model also assumes abundances of e.g., carbon, oxygen, and polycyclic aromatic hydrocarbons (PAHs). The “wk2020” models have two sets of metallicity, $Z/Z_{\odot} = 0.5$ and $1.0$. In this study, we adopt the case of $Z/Z_{\odot}=1.0$[^8].

The two main input parameters are the radiation field strength in terms of Habing fields ($G_{\rm 0} = 1.6 \times 10^{-3}$ erg cm$^{-2}$ s$^{-1}$) and a constant hydrogen nucleus density, $n_{\rm H}$. With these two parameters, the model calculates local chemical equilibrium to determine local density, solves local energy balance to estimate temperature and pressure, and performs radiative transfer through a PDR layer to output line intensities from one side. Thus, if more than two intensity ratios are available, one can constrain $n_{\rm H}$ and the FUV radiation field based on comparisons of the models with observed line intensities. Note that PDRT assumes that \[C ii\] 158 $\mu$m is purely emitted from the PDR. In this study, we further assume that \[C ii\], \[O i\], and dust continuum emission are co-spatial, but discuss this limitation in §[4.2.3](#subsubsec:discussion2_3).

### Corrections to Input Luminosities

Before comparing the models to the line luminosity ratios in J2054-0005, we apply the following three corrections to the data. First, although we assume that the \[O i\] 63 $\mu$m and \[C ii\] 158 $\mu$m lines are emitted from PDRs (§[4.1](#subsec:discussion1)), it is possible that the dust continuum emission is partly powered by the AGN activity in J2054-0005. Based on the results of multi-wavelength SED fitting with `CIGALE` in (cite: salak2024), we find that the AGN activity contributes to $\approx 78$% of the FIR luminosity on the galactic scale in J2054-0005[^9]. We thus adopt the far-infrared luminosity from star formation activity, $L_{\rm FIR}$(PDR) $= 0.22~L_{\rm FIR} = (1.5\pm0.1)\times10^{12}~L_{\rm \odot}$.

Secondly, although the PDRT models assume that \[C ii\] 158 $\mu$m is purely emitted from PDRs, \[C ii\] originates from both the Hii regions and PDR in reality (e.g., (cite: Oberst2006; herrera-camus2016)). We assume that $17$% of \[C ii\] 158 $\mu$m is emitted from the Hii regions based on a result of a similarly FIR-luminous quasar, J2310+1855 at $z=6.0$[^10] ((cite: li2020)). The \[C ii\] 158 $\mu$m luminosity emitted from PDR, $L_{\rm [CII] 158 \ensuremath{\mu}m}$(PDR), is estimated to be $0.83~L_{\rm [CII] 158 \ensuremath{\mu}m} = (2.8\pm0.4)\times10^{9}~L_{\rm \odot}$.

Finally, in a more realistic geometry of spherical clouds, the optically thin emission (FIR continuum and \[C ii\] 158 $\mu$m) would be detected from both the front and back sides of the cloud, whereas the optically thick emission (\[O i\] 63 $\mu$m) would be detected only from the front side[^11] ((cite: kaufman1999; rollig2007; yang2019)). Following previous studies (e.g., (cite: wardlow2017; yang2019; hashimoto2023)), we multiply the observed luminosity of \[O i\] 63 $\mu$m by a factor of two, $L_{\rm [OI] 63\ensuremath{\mu}m, corr.} = 2~L_{\rm [OI] 63\ensuremath{\mu}m} = (9.1\pm3.0)\times10^{9}~L_{\rm \odot}$.

### Results of PDR Modeling

Figure [3](#fig3) shows the results of PDR modeling in J2054-0005. The darker red and blue shaded regions indicate the parameter space allowed by $L_{\rm [OI]63\ensuremath{\mu}m}/L_{\rm [CII]158\ensuremath{\mu}m}$ and $(L_{\rm [CII]158\ensuremath{\mu}m} + L_{\rm [OI]63\ensuremath{\mu}m})/L_{\rm FIR}$, respectively. We obtain a fiducial result, log($n_{\rm H}$/cm$^{-3}$)$=3.7\pm0.3$ and log($G/G_{\rm 0}$) $= 3.0\pm0.1$, as indicated by a thick black circle. Here, we only consider the solution with log($G/G_{\rm 0})$ $\gtrsim 1$ as physically plausible following the discussion in (cite: brisbin2015).

Because the correction to $L_{\rm FIR}$ in §[4.2.2](#subsubsec:discussion2_2) is not usually applied even in the presence of AGN activity (e.g., (cite: brisbin2015)), as a comparison, we also perform PDR modeling with the same models without applying the correction to $L_{\rm FIR}$ (purple shaded region). As indicated by a black dotted circle, the result, log($n_{\rm H}$/cm$^{-3}$)$=3.4\pm0.4$ and log($G/G_{\rm 0}$) $= 3.7\pm0.3$, is shifted toward a higher FUV radiation field compared to the fiducial case. Given the possible uncertainty in the correction of $L_{\rm FIR}$, the FUV radiation field of log($G/G_{\rm 0}$) $\sim 3.7$ can be regarded as the upper limit.

We further discuss two considerations in the PDR modeling. Firstly, the \[O i\] 63 $\mu$m line may be self-absorbed as described above. Given the limited quality of our data, it is difficult to determine conclusively if the line in J2054-0005 is indeed self-absorbed. However, by closely comparing the \[O i\] 63 $\mu$m line profile to that of \[C ii\] 158 $\mu$m as shown in figure [4](#fig4), we can make a tentative assessment. In this figure, we show the spectrum at a finer resolution of 30 km s$^{-1}$. Examining the two lines in figure [4](#fig4), if we assume that the \[O i\] 63 $\mu$m line is not self-absorbed, then its line peak is $\sim 50$ km s$^{-1}$ blueward of the \[C ii\] peak, with a line width about half as narrow as the \[C ii\] line. While this scenario is not impossible, especially if the \[C ii\] line is more spatially extended, it may also be hinting that some of the \[O i\] line has been self-absorbed. To assess how much, a two component-gaussian fit is made to the \[O i\] data. For the fit we assume that the \[O i\] emission should arise in the same regions as the \[C ii\] so we force one component to the same line-center and line-width as the \[C ii\] line, letting only its amplitude vary. The second component is left completely unconstrained. The result of the non-linear least-squares fit via *Scipy*’s `ODR` module is shown in figure [4](#fig4). The best fit model includes an absorption component at $\sim 100$ km s$^{-1}$ with a FWHM of $\sim 80$ km s$^{-1}$. Integrating the emission component we get an estimated line-flux of $2.9 \pm 0.7$ Jy km s$^{-1}$, about 50% higher than if we assume the line is not self-absorbed. Given the low signal-to-noise ratio of the spectrum, this exact value should be treated cautiously, but it does suggest that the \[O i\] 63 $\mu$m line in J2054-0005 may indeed be self-absorbed. To account for this possibility, we also perform PDR modeling by multiplying the \[O i\] 63 $\mu$m line luminosity by an additional factor of two[^12] (lighter red and blue shaded regions in figure [3](#fig3)).

As indicated by a black dashed circle, the result, log($n_{\rm H}$/cm$^{-3}$) $=4.3\pm0.3$ and log($G/G_{\rm 0}$) $= 3.0\pm0.4$, is slightly shifted toward a higher gas density.

![](Fig4.pdf)

Secondly, the \[C ii\] 158 $\mu$m, \[O i\] 63 $\mu$m, and dust continuum emission are not necessarily co-spatial. Deep ALMA imaging has revealed extended, diffuse \[C ii\]-“halos” around high-$z$ star-forming galaxies (e.g., (cite: gullberg2018; fujimoto2019; fujimoto2020; rybak2019; rybak2020; ikeda2024)). Recently, based on the high-angular resolution data of \[C ii\] 158 $\mu$m in the ALMA-CRISTAL survey, (cite: ikeda2024) have found that the spatial extent of \[C ii\] can be explained by PDRs, while the contribution from diffuse neutral medium (atomic gas) and the effects of mergers may further expand the \[C ii\] line distributions. In case of J2054-0005, high-resolution ALMA imaging indicates that the \[C ii\] emission is a factor of $\approx 2$ more extended than dust ((cite: venemans2020)). In figure [3](#fig3), we show an arrow indicating the direction of the correction due to the extended \[C ii\], where we divide the \[C ii\] luminosity by a factor of two. A detailed discussion is hampered by the fact that the spatial extent of \[O i\] is not known. Future higher-resolution observation of \[O i\] 63 $\mu$m is crucial for more sophisticated PDR modeling.

### Comparisons of Our PDR Modeling to the Literatures

![](Fig5.pdf)

In figure [5](#fig5), we compare the results of J2054-0005 with the literature values. Black crosses and a black triangle show the results in nearby star-forming galaxies ((cite: malhotra2001)) and a lensed $z\sim1$ SMG ((cite: sturm2010)), respectively. These results are obtained based on the models of (cite: kaufman1999) with the \[O i\] 63 $\mu$m, \[C ii\] 158 $\mu$m, and IR luminosities.

Black diamonds indicate the results in non-lensed SMGs at $z\sim1-2$ ((cite: brisbin2015)). The authors have used the PDR models of (cite: pound_wolfire2008) with the \[O i\] 63 $\mu$m, \[C ii\] 158 $\mu$m, and IR luminosities.

A black circle shows the result of (cite: wagg2020) in a BzK galaxy at $z\sim1$. The PDR modeling is based on the models of (cite: wolfire2022) with the \[O i\] 63 $\mu$m, CO(2-1), and IR luminosities.

Finally, we also plot the result of (cite: wardlow2017) who have performed PDR modeling for a stacked spectrum of $z\sim1-3$ SMGs. The authors have used the models of (cite: pound_wolfire2008) and \[O i\] 63 $\mu$m, \[C ii\] 158 $\mu$m, \[Si iii\] 34 $\mu$m, and IR luminosities.

As can be seen in figure [5](#fig5), the samples of nearby star-forming galaxies and $z=1-3$ SMGs with individual detections of \[O i\] 63 $\mu$m exhibit a broad range of gas density, ranging from log($n_{\rm H}$/cm$^{-3}$) $\sim~2$ to $>~4$. The PDR properties of J2054-0005 are broadly consistent with these galaxies, however, we note that J2054-0005 falls within the region that overlaps with the high log($n_{\rm H}$) objects among the star-forming galaxies. This is consistent with a picture that the gas is centrally concentrated in the quasar host galaxy, leading to the stimulation of both intense nuclear star formation and central supermassive black hole accretion (e.g., (cite: hopkins2008)).

# Summary

We have presented \[O i\] 63 $\mu$m data of a luminous quasar, J2054-0005 at $z=6.04$ obtained with ALMA Band 9. The \[O i\] 63 $\mu$m line is detected at the peak significance level of $5.0$ at the expected position and frequency (figure [1](#fig1)). To date, this is the highest-$z$ detection of \[O i\] 63 $\mu$m, and only the second case of \[O i\] 63 $\mu$m detection at $z>4$ after a hyper-luminous AGN, W2246-0526 ((cite: fernandez_aranda2024)). Our findings are summarized as follows.

- In J2054-0005, the \[O i\] 63 $\mu$m line luminosity is $(4.5\pm1.5)~\times~10^{9}~L_{\rm \odot}$, corresponding to $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}~=~(6.7\pm2.2)\times10^{-4}$. We have compiled the data points of objects with \[O i\] 63 $\mu$m observations at $z=0-4$, and compared them with J2054-0005. In contrast to the previous \[O i\] 63 $\mu$m detections in individual SMGs at $z=1-3$ that show enhanced $L_{\rm [OI] 63 \ensuremath{\mu}m}/L_{\rm FIR}$ against the local value, we have found that the values in J2054-0005 and W2246-0526 at $z=4-6$ are consistent with those in the local universe (left panel of figure [2](#fig2)). In J2054-0005, \[O i\] 63 $\mu$m is as bright as \[C ii\] 158 $\mu$m, resulting in $L_{\rm [OI]63\ensuremath{\mu}m}/L_{\rm [CII]158\ensuremath{\mu}m} = 1.3\pm0.5$ (right panel of figure [2](#fig2)).

- Analyzing the \[O i\] 63 $\mu$m spectrum and fitting a two-component Gaussian model suggests that the \[O i\] 63 $\mu$m line may be self-absorbed. Deeper observations of the line, to significantly detect the absorption feature are necessary to conclusively determine the degree of self-absorption (figure [4](#fig4)).

- We have performed PDR modeling with PDRT ((cite: pound_wolfire2023)) based on the luminosity ratios of $L_{\rm [OI] 63 \ensuremath{\mu}m\ }/L_{\rm [CII] 158 \ensuremath{\mu}m}$ and $(L_{\rm [OI] 63 \ensuremath{\mu}m} + L_{\rm [CII] 158 \ensuremath{\mu}m})/L_{\rm FIR}$. We have carefully removed the possible contribution of AGN activity to $L_{\rm FIR}$ and H ii contribution to $L_{\rm [CII]158\ensuremath{\mu}m}$. We have obtained the gas density of log($n_{\rm H}$/cm$^{-3}$)$=3.7\pm0.3$ and FUV radiation field of log($G/G_{\rm 0}$) $= 3.0\pm0.1$, although the results can slightly change if we consider the self-absorption effect on \[O i\] 63 $\mu$m. The PDR properties are in a broad agreement with those obtained in nearby star-forming galaxies and other $z=1-3$ SMGs with individual \[O i\] 63 $\mu$m detections (figures [3](#fig3) and [5](#fig5)). We note that J2054-0005 falls within the region that overlaps with the high log($n_{\rm H}$) objects among the star-forming galaxies.

In this work, we have demonstrated the power of \[O i\] 63 $\mu$m to probe the dense neutral gas in high-$z$ galaxies. Although \[O i\] 63 $\mu$m is not easy to observe in $z\sim4-7$ galaxies because the line is redshifted in high-frequency bands of ALMA (Band 9 and 10), a statistical sample of \[O i\] 63 $\mu$m observations is crucial to study the PDR gas in quasar host galaxies and compare them with those in normal star-forming galaxies at similar epochs.

# Acknowledgments

The authors thank the anonymous referee for comments and suggestions that helped us improve the manuscript. We also acknowledge Ken Ohsuga, Ryota Ikeda, Atsushi Yasuda, Saho Kawahara, Ryota Ura, Tatsuya Matsumura, Yu Nagai for useful discussion.

N.I. was supported by the ALMA Japan Research Grant of NAOJ ALMA Project, NAOJ-ALMA-341. T.H. was supported by Leading Initiative for Excellent Young Researchers, MEXT, Japan (HJH02007) and by JSPS KAKENHI grant Nos. 20K22358 and 22H01258. M.R. was supported by the NWO Veni project “*Under the lens*" (VI.Veni.202.225). T.M. was supported by a University Research Support Grant from the National Astronomical Observatory of Japan (NAOJ). D.D acknowledges support from the National Science Center (NCN) grant SONATA (UMO-2020/39/D/ST9/00720). K.M. acknowledges support from the JapanSociety for the Promotion of Science (JSPS) through KAKENHI grant No. 20K14516. Y.T. was supported by KAKENHI grant Nos. 22H04939 and 23K20035. T.I. was supported by KAKENHI No. 23K03462. Y.N. acknowledges funding from JSPS KAKENHI Grant Number 23KJ0728.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01063.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

79 natexlab

(ref: abel2009) Abel, N. P., Dudley, C., Fischer, J., Satyapal, S., & van Hoof, P. A. M. 2009, ApJ, 701, 1147

(ref: baluteau1997) Baluteau, J.-P., Cox, P., Cernicharo, J., & Pequignot, D. 1997, Astronomy & Astrophysics, 322

(ref: boquien2019) Boquien, M., Burgarella, D., Roehlly, Y., Buat, V., Ciesla, L., Corre, D., Inoue, A. K., & Salas, H. 2019, A&A, 622, A103

(ref: brauher2008) Brauher, J. R., Dale, D. A., & Helou, G. 2008, The Astrophysical Journal Supplement Series, 178, 280

(ref: brisbin2015) Brisbin, D., Ferkinhoff, C., Nikola, T., Parshley, S., Stacey, G. J., Spoon, H., Hailey-Dunsheath, S., & Verma, A. 2015, ApJ, 799, 13

(ref: mcmullin2022) CASA Team et al. 2022, PASP, 134, 114501

(ref: coppin2012) Coppin, K. E. K., et al. 2012, Monthly Notices of the Royal Astronomical Society, 427, 520

(ref: cormier2015) Cormier, D., et al. 2015, Astronomy & Astrophysics, 578, A53

(ref: delooze2014) De Looze, I., et al. 2014, Astronomy & Astrophysics, 568, A62

(ref: decarli2018) Decarli, R., et al. 2018, The Astrophysical Journal, 854, 97

(ref: decarli2020) Decarli, R., et al. 2022, A&A, 662, A60

(ref: diaz-santos2017) Diaz-Santos, T., et al. 2017, The Astrophysical Journal, 846, 32

(ref: draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: farina2022) Farina, E. P., et al. 2022, ApJ, 941, 106

(ref: farrah2013) Farrah, D., et al. 2013, The Astrophysical Journal, 776, 38

(ref: ferland2013) Ferland, G. J., et al. 2013, RMxAA, 49, 137

(ref: fernandez_aranda2024) Fernández Aranda, R., et al. 2024, A&A, 682, A166

(ref: fritz2006) Fritz, J., Franceschini, A., & Hatziminaoglou, E. 2006, MNRAS, 366, 767

(ref: fujimoto2019) Fujimoto, S., et al. 2019, ApJ, 887, 107

(ref: fujimoto2020) —. 2020, ApJ, 900, 1

(ref: fukuchi2022) Fukuchi, H., et al. 2022, ApJ, 940, 7

(ref: furniss1983) Furniss, I., Jennings, R. E., King, K. J., Lightfoot, J. F., Emery, R. J., Naylor, D. A., & Fitton, B. 1983, MNRAS, 202, 859

(ref: goldsmith2021) Goldsmith, P. F., Langer, W. D., Seo, Y., Pineda, J., Stutzki, J., Guevara, C., Aladro, R., & Justen, M. 2021, ApJ, 916, 6

(ref: gonzalez-alfonso2012) González-Alfonso, E., et al. 2012, Astronomy & Astrophysics, 541, A4

(ref: gullberg2018) Gullberg, B., et al. 2018, ApJ, 859, 12

(ref: hashimoto2019) Hashimoto, T., Inoue, A. K., Tamura, Y., Matsuo, H., Mawatari, K., & Yamaguchi, Y. 2019, Publications of the Astronomical Society of Japan, 71, 109

(ref: hashimoto2023) Hashimoto, T., et al. 2023, ApJ, 952, 48

(ref: herrera-camus2016) Herrera-Camus, R., et al. 2016, The Astrophysical Journal, 826, 175

(ref: herrera-camus2018) —. 2018, The Astrophysical Journal, 861, 94

(ref: hollenbach1999) Hollenbach, D. J., & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173

(ref: hopkins2008) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, The Astrophysical Journal Supplement Series, 175, 356

(ref: ikeda2024) Ikeda, R., et al. 2024, arXiv e-prints, arXiv:2408.03374

(ref: inayoshi2020) Inayoshi, K., Visbal, E., & Haiman, Z. 2020, Annual Review of Astronomy and Astrophysics, 58, 27

(ref: izumi2019) Izumi, T., et al. 2019, Publications of the Astronomical Society of Japan, 71, 111

(ref: izumi2020) Izumi, T., et al. 2020, ApJ, 898, 75

(ref: jiang2008) Jiang, L., et al. 2008, The Astronomical Journal, 135, 1057

(ref: kaasinen2023) Kaasinen, M., et al. 2023, A&A, 671, A29

(ref: kaufman2006) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, The Astrophysical Journal, 644, 283

(ref: kaufman1999) Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman, M. L. 1999, The Astrophysical Journal, 527, 795

(ref: kennicutt2012) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531

(ref: komatsu2011) Komatsu, E., et al. 2011, The Astrophysical Journal Supplement Series, 192, 18

(ref: kormendy2013) Kormendy, J., & Ho, L. C. 2013, Annual Review of Astronomy and Astrophysics, 51, 511

(ref: kraemer1998) Kraemer, K. E., & Jackson, J. M. 1998

(ref: li2020) Li, J., et al. 2020, ApJ, 900, 131

(ref: litke2022) Litke, K. C., et al. 2022, ApJ, 928, 179

(ref: madden2013) Madden, S. C., et al. 2013, PASP, 125, 600

(ref: malhotra2001) Malhotra, S., et al. 2001, ApJ, 561, 766

(ref: meijerink2007) Meijerink, R., Spaans, M., & Israel, F. P. 2007, A&A, 461, 793

(ref: melnick1979) Melnick, G., Gull, G. E., & Harwit, M. 1979, ApJL, 227, L29

(ref: narayanan2017) Narayanan, D., & Krumholz, M. 2017, Monthly Notices of the Royal Astronomical Society, 467, 50

(ref: novak2019) Novak, M., et al. 2019, The Astrophysical Journal, 881, 63

(ref: Oberst2006) Oberst, T. E., et al. 2006, The Astrophysical Journal, 652, L125

(ref: pensabene2024) Pensabene, A., et al. 2024, A&A, 684, A119

(ref: poglitsch1996) Poglitsch, A., Herrmann, F., Genzel, R., Madden, S. C., Nikola, T., Timmermann, R., Geis, N., & Stacey, G. J. 1996, ApJL, 462, L43

(ref: pound_wolfire2008) Pound, M. W., & Wolfire, M. G. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 394, Astronomical Data Analysis Software and Systems XVII, ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654

(ref: pound_wolfire2023) Pound, M. W., & Wolfire, M. G. 2023, AJ, 165, 25

(ref: rollig2013) Röllig, M., Szczerba, R., Ossenkopf, V., & Glück, C. 2013, A&A, 549, A85

(ref: rollig2007) Röllig, M., et al. 2007, Astronomy & Astrophysics, 467, 187

(ref: rosenberg2015) Rosenberg, M. J. F., et al. 2015, The Astrophysical Journal, 801, 72

(ref: russell1980) Russell, R. W., Melnick, G., Gull, G. E., & Harwit, M. 1980, ApJL, 240, L99

(ref: rybak2020) Rybak, M., Zavala, J. A., Hodge, J. A., Casey, C. M., & van der Werf, P. 2020, The Astrophysical Journal, 889, L11

(ref: rybak2019) Rybak, M., et al. 2019, ApJ, 876, 112

(ref: rybak2023) —. 2023, Research Notes of the American Astronomical Society, 7, 188

(ref: salak2024) Salak, D., et al. 2024, ApJ, 962, 1

(ref: salpeter1955) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: shao2019) Shao, Y., et al. 2019, The Astrophysical Journal, 876, 99

(ref: solomon1992) Solomon, P. M., Downes, D., & Radford, S. J. E. 1992, The Astrophysical Journal, 387, L55

(ref: sturm2010) Sturm, E., et al. 2010, A&A, 518, L36

(ref: tripodi2024) Tripodi, R., et al. 2024, A&A, 689, A220

(ref: uzgil2016) Uzgil, B. D., Bradford, C. M., Hailey-Dunsheath, S., Maloney, P. R., & Aguirre, J. E. 2016, ApJ, 832, 209

(ref: valiante2017) Valiante, R., Agarwal, B., Habouzit, M., & Pezzulli, E. 2017, Publications of the Astronomical Society of Australia, 34, e031

(ref: venemans2020) Venemans, B., et al. 2020, The Astrophysical Journal, 904, 130

(ref: venemans2018) Venemans, B. P., et al. 2018, ApJ, 866, 159

(ref: wagg2020) Wagg, J., et al. 2020, Monthly Notices of the Royal Astronomical Society, 499, 1788

(ref: wang2013) Wang, R., et al. 2013, The Astrophysical Journal, 773, 44

(ref: wardlow2017) Wardlow, J. L., et al. 2017, The Astrophysical Journal, 837, 12

(ref: wolfire2022) Wolfire, M. G., Vallini, L., & Chevance, M. 2022, ARA&A, 60, 247

(ref: yang2019) Yang, J., et al. 2019, ApJ, 880, 153

(ref: zhang2018) Zhang, Z.-Y., et al. 2018, MNRAS, 481, 59

[^1]: https://almascience.nao.ac.jp/proposing/documents-and-tools/cycle4/alma-proposers-guide

[^2]: The phase-tracking center of the ALMA Band 9 observation is slightly offset from the position of J2054-0005, ($\alpha_{\rm ICRS}$, $\delta_{\rm ICRS}$) = ($20^h 54^m 06.503s, -00\ensuremath{^\circ} 05' 14.43\ensuremath{''}$) in (cite: hashimoto2019). In this case, `imcontsub` optimally subtracts the continuum compared with the CASA task `uvcontsub` (see e.g., (cite: kaasinen2023) for the choice of `imcontsub` due to the same issue).

[^3]: The line luminosities of \[C ii\] 158 $\mu$m ((cite: wang2013)) and \[O iii\] 88 $\mu$m ((cite: hashimoto2019)) are obtained in the same manner as in \[O i\] 63 $\mu$m.

[^4]: We have removed objects overlapped with (cite: diaz-santos2017).

[^5]: The object IDs are LESS66, 88, and 102.

[^6]: The object ID is MIPS J1248.

[^7]: This is due to the result of X-rays penetrate deeper into the clouds than UV photons, thus heating the cloud cores to enhance \[C i\](2-1) ((cite: decarli2020); see also (cite: izumi2020) for the use of \[C ii\]/\[C i\] to examine the presence of AGN).

[^8]: Although the metallicity is not obtained for J2054-0005 in the literature due to the lack of lines necessary to estimate it, the choice of the value is motivated by the metallicity estimates in two similarly FIR-luminous quasars: (cite: li2020) and (cite: novak2019) have obtained $Z/Z_{\odot} = 1.5 - 2.1$ and $0.7 - 2.0$ for J2310+1855 at $z=6.0$ and J1342+0928 at $z=7.54$, respectively.

[^9]: In (cite: salak2024), the fractional AGN contribution to the IR luminosity is computed based on (cite: fritz2006) that assumes three components through a radiative transfer: primary source located in the torus, the scattered emission by dust, and the thermal dust emission.

[^10]: The contribution from the Hii regions can be estimated with the luminosity ratio of \[C ii\]-to-\[N ii\] 205 $\mu$m. However, \[N ii\] 205 $\mu$m is not observed in J2054-0005.

[^11]: \[C ii\] 158 $\mu$m becomes optically thick at the column density of $N$(C$^{+}$) $=$ $5\times10^{17}$ cm$^{-2}$ at a velocity width of 4 km s$^{-1}$ ((cite: russell1980)). On the other hand, the optical depth of \[O i\] 63 $\mu$m becomes unity at a column density of $N$(O$^{0}$) $=$ $2\times10^{17}$ cm$^{-2}$ at a velocity width of 1 km s$^{-1}$ ((cite: wolfire2022)). Because O$^{0}$ is present up to higher optical depth clouds than C$^{+}$, \[O i\] 63 $\mu$m becomes opitcally-thick faster than \[C ii\] 158 $\mu$m ((cite: malhotra2001)).

[^12]: As discussed in (cite: wolfire2022), the correction to \[O i\] 63 $\mu$m in the case of self-absorption is typically $2-4$. This is also in agreement, within the uncertainties, with the un-absorbed flux estimated via our gaussian fitting.

</paper>

Write the methods card for this paper.