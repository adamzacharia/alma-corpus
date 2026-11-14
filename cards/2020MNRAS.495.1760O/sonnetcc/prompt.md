# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2020MNRAS.495.1760O\sonnetcc\reply.txt

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
 "bibcode": "2020MNRAS.495.1760O",
 "title": "Cosmic evolution of molecular gas mass density from an empirical relationship between L<SUB>1.4 GHz</SUB> and L<SUP>'</SUP><SUB>CO</SUB>",
 "year": 2020,
 "journal": "Monthly Notices of the Royal Astronomical Society",
 "first_author": "Orellana-González, G.",
 "n_authors": 11,
 "arxiv_id": "2004.11442",
 "doi": "10.1093/mnras/staa1171",
 "alma_projects_linked_by_archive": [
  "2012.1.01080.S",
  "2013.1.00530.S"
 ]
}
```

Paper text:
<paper>
# Cosmic evolution of molecular gas mass density from an empirical relation between $L_{\rm 1.4GHz}$ and $L^{'}_{\rm CO}$

## Abstract

Historically, GHz radio emission has been used extensively to characterize the star-formation activity in galaxies. In this work, we look for empirical relations amongst the radio luminosity, the infrared luminosity, and the CO-based molecular gas mass. We assemble a sample of 278 nearby galaxies with measurements of radio continuum and total infrared emission, and the $^{12}$CO ($J = 1$–0) emission line. We find a correlation between the radio continuum and the CO emission line (with a scatter of 0.36 dex), in a large sample of different kind of galaxies. Making use of this correlation, we explore the evolution of the molecular gas mass function and the cosmological molecular gas mass density in six redshift bins up to $z = 1.5$. These results agree with previous semi-analytic predictions and direct measurements: the cosmic molecular gas density increases up to $z=1.5$. In addition, we find a single plane across five orders of magnitude for the explored luminosities, with a scatter of 0.27 dex. These correlations are sufficiently robust to be used for samples where no CO measurements exist.

radio continuum: galaxies — infrared: galaxies — galaxy: evolution — galaxies: ISM

# Introduction

Understanding galaxy evolution is a key goal of modern astrophysics. This can be tackled using a wide range of observational and theoretical prescriptions which involve complex physical processes for their interpretation (e.g. (cite: davies19)). In the cosmological context, a primary focus of this study is the evolution of the cosmic star-formation history (CSFH, e.g. (cite: tisley80; madau96)). Studies based on large galaxy samples reveal that the cosmic star-formation rate (SFR) density peaks at $z\sim2$–3 then declines steadily by $\sim\,20\times$ through to the present time (cite: madau14). The physical processes involved are not yet clear, although some of the main predictions are: the growth of the dark-matter halos (e.g. (cite: behroozi13)), the depletion of molecular gas reservoirs in galaxies (e.g. (cite: kennicutt12; genzel15; tacconi18)) and changes in the star-formation efficiency (e.g. (cite: genzel10; daddi10)).

The molecular gas is the reservoir for the future star-formation (SF) activity, so its census across cosmic time is fundamental to understand CSFH. Historically, the main proxy to trace the molecular gas mass is via the rotational low-$J$ ($J$ = 1–0) transitions of the carbon monoxide (CO) molecule (cite: bolatto13). Recently, spectroscopic surveys undertaken with the Atacama Large Millimeter/submillimeter Array (ALMA, e.g. ASPECS; (cite: walter16; decarli16)) have revealed that the molecular gas mass density changes by a factor of 3–$10\times$ across $z=0$–2. This result is in concordance with predictions from semi-analytic models (e.g. (cite: popping12; lagos18)). Nevertheless, when CO-based studies are performed via pencil-beam surveys, they are: (a) naturally affected by cosmic variance (cite: walter16); (b) biased to detect the most intensely star-forming galaxies (e.g. (cite: bothwell13)) and (c) based on small galaxy samples (e.g. (cite: daddi10; genzel10; genzel15)). These limitations are a consequence of the considerable amount of observing time needed to measure CO lines in galaxies beyond the local Universe.

An alternative but less direct method to measure the gas mass, $M_{\rm gas}$, uses the dust that is concomitant with the molecular gas. Several studies show that optically thin dust emission in the Rayleigh-Jeans regime ($\sim 350$–1000 $\rm \mu m$) is proportional to the dust mass (e.g. (cite: dunne11; clemens13; bianchi13)), where there is a strong sensitivity on dust temperature (cite: scoville14). Diffuse, cold dust ($T \leq 25$ K) dominates the dust mass in galaxies, while warmer dust ($T
  \geq 30$ K) usually dominates the dust luminosity (cite: devereux90; dunne01; draine07; clark15). According to (cite: scoville14), the molecular gas mass can be obtained from a single measurement of flux density made in a specific band on the Rayleigh-Jeans tail, assuming a typical dust temperature between 20–45 K. Adopting a dust-to-gas mass ratio, these authors then determine the molecular gas mass. Using this method, recent studies (e.g. (cite: scoville16; hughes17a)) using small samples of massive, nearby, star-forming, infrared-bright galaxies ($L_{\rm IR} > 10^{11}$ L$_{\odot}$) found empirical relations between the luminosity at 850 $\rm \mu m$ ($L_{850}$) and the total $M_{\rm gas}$. The $L_{850}$—$M_{\rm gas}$ relation is tight (scatter $\sim\,0.3$ dex), which makes it possible to obtain $M_{\rm gas}$ in an efficient, precise manner for large samples of galaxies.

Using a sample $10\times$ larger than that of (cite: scoville14), however, (cite: orellana17) found that the relation between the submillimetre (submm) emission and the gas mass determined by Scovile’s method shows a significant dispersion ($\sim\,1$ dex), as well as increased scatter towards fainter luminosities. Moreover, (cite: orellana17) found that the dust mass is a more accurate tracer of the total gas mass (atomic and molecular) than the molecular gas mass alone, in concordance with recent results obtained by (cite: casasola20) based on 436 nearby galaxies from the DustPedia Survey (cite: davies17).

In this paper we construct new scaling relations using other tracers of molecular gas which can provide more precise molecular gas mass estimates with a lower dispersion.

To tackle this problem, we make use of three well-studied relations. First, the radio continuum–infrared (RC–IR) correlation connects the non-thermal radio emission, typically at 1.4 GHz, and the IR radiation coming from dust grains heated by ultraviolet photons from young stellar populations, assuming that supernovae remnants related to massive young stars are responsible for the synchrotron radiation. The RC–IR correlation has been shown to be valid over a wide range of star-forming galaxies (e.g. (cite: bell03; ibar08; ivison10; smith14; liu15)) with little evolution across the cosmic time (cite: ivison10; magnelli15).

Second, the global Schmidt-Kennicutt (SK) relation connects the formation of stars with the fuel to produce them, i.e. the molecular gas; it can be expressed in terms $L_{\rm IR}$ and $L^{'}_{\rm CO}$ luminosities, respectively (e.g. (cite: kennicutt12)), where $L^{'}_{\rm CO}$ is the luminosity of the CO molecule, closely related to the molecular gas mass (see e.g. (cite: bolatto13)).

Third, the other widely used relation exploited here connects the RC and CO emission. The relation between CO luminosity, $L^{'}_{\rm CO}$, and radio luminosity, $L_{\rm 1.4GHz}$, has been known since early CO observations (e.g. (cite: rickard77; israel84; murgia02)) and probed in the local Universe for different type of galaxies (e.g. disk-like; dwarfs; ultraluminous IR galaxies, ULIRGs) using unresolved observations (global-scale observations; e.g. (cite: adler91; leroy05; liu15)) as well as in resolved regions down to $\sim 100$ pc (e.g. (cite: murgia05; paladino06; schinnerer13)).

This article is the first of a series in which we explore the connection between the RC and the IR and the molecular gas mass ($M_{\rm H_2}$, traced by the CO luminosity) in spatially resolved galaxies and in galaxies at higher redshifts. We show the use of RC as a relatively precise proxy for the molecular gas mass in the local Universe and beyond. We also present an empirical plane among the RC emission, the IR luminosity and the CO luminosity. We base our work on large samples of galaxies built from wide-area surveys, resulting in more statistically robust work than was previously possible.

Throughout the text, we assume a $\Lambda$-CDM cosmology with $H_0=70$  km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M} = 0.3$ and $\Omega_{\Lambda} = 0.7$.

# Sample selection

Our sample is constructed from seven surveys taken from the literature, all of which have measurements of IR, RC and low-$J$ CO lines for galaxies at redshifts, $z<0.3$:

- VALES (cite: villanueva17; hughes17a; hughes17b; cheng18; molina19) comprises 91 galaxies at ($0.02<z<0.35$) taken from H-ATLAS[^2] (cite: eales10), with 65 galaxies detected spectroscopically in low-$J$ CO ($J=1$–0 or $J=2$–1) using the Atacama Large Millimetre Array (ALMA) or the Atacama Pathfinder EXperiment (APEX). In addition, VALES has rich multi-wavelength coverage from UV to far-IR wavelengths compiled by the Galaxy And Mass Assembly survey (GAMA; (cite: driver16)), allowing us to measure $L_{\rm IR}$ by spectral energy distribution (SED) fitting. In order to homogenise the CO line measurements to $J=1$–0, we assume a luminosity ratio $L^{\prime}_{\rm CO(2-1)} /L^{\prime}_{\rm CO~(1-0)} = 0.85$ (cite: carilli13).

- The xCOLD GASS survey (cite: saintonge17) is a recent upgrade of the COLD GASS survey (cite: saintonge11a; saintonge11b) with the newest sample called COLD GASS-low. In total, xCOLD GASS contains 532 galaxies, both star-forming and passive ellipticals with stellar mass in the range $9.0 < \log (M_*/{\rm L}_{\odot}) < 11.5$, in the redshift range, $0.01 < z < 0.05$, which have been observed with the IRAM 30-m telescope in CO($J=1$–0) and with APEX in CO($J=2$–1). We use only the CO ($J=1$–0) data from this survey. The IR data comes from the *Infrared Astronomical Satellite* (*IRAS*; (cite: neugebauer84)).

- (cite: liu15) (hereafter, Liu15) contains 181 local galaxies with IR luminosities between $7.8< \log($$L_{\rm IR}$$/{\rm L}_{\odot})<12.3$, where 115 are normal spiral galaxies and the rest are ULIRGs. This sample contains CO ($J=1$–0) flux measurements from high-resolution CO maps published in the literature (cite: chung09; young08; kuno07; gao04; helfer03; sofue03) and IR data from *IRAS*.

- The APEX Low-redshift Legacy Survey for MOlecular Gas (ALLSMOG; (cite: cicone17)) comprises 97 Sloan Digital Sky Survey (SDSS DR7) galaxies at $0.01<z<0.03$, with stellar masses in the range $8.5 < \log($$M_{*}$$/{\rm L}_{\odot})< 10.0$, classified as star forming according to the BPT diagram and with a gas-phase metallicity 12 + $\log(O/H) \ge 8.5$. In addition, this sample contains measurements of CO($J=1$–0) from the IRAM 30-m telescope and of CO($J=2$–1) from APEX. We use only their CO($J=1$–0) measurements. We derive $L_{\rm IR}$ from the *Wide-field Infrared Survey Explorer (WISE)* photometry (from the ALLWISE cataloge, (cite: wright10)) at 12 $\rm \mu m$ following (cite: cluver14) .

- The ATLAS$^{\rm 3D}$ survey (cite: cappellari11) contains 260 galaxies — a volume-limited sample ($D < 42$ Mpc) of early-type galaxies (ellipticals, E, and lenticulars, S0) brighter than $M_K < -21.5$ mag ($\log$$M_{*}$$\ge  9.78$ $\rm M_{\odot}$), where 56 galaxies have both CO($J=1$–0) and ($J=2$–1) measurements from IRAM 30m (cite: young11), from which we only use the values for CO($J=1$–0). For this sample, we derive $L_{\rm IR}$ from *WISE* photometry (from the ALLWISE cataloge) at 12 $\rm \mu m$ following (cite: cluver14).

- (cite: leroy05)(hereafter, Leroy05) contains 121 nearby ($v_{\rm LSR}\leq 1,000$ km s$^{-1}$) dwarf galaxies with typical dynamical masses $M_{\rm dyn}\leq 10^{10}$ M$_{\odot}$, optical diameters $d_{25} < 5^{\prime}$, and with atomic hydrogen line widths, $W_{20}\leq 200$ km s$^{-1}$, selected from the *IRAS* Faint Source Catalog (FSC) at 60 and/or 100 $\rm \mu m$. This sample contains 28 galaxies detected (at S/N $\geq 5$) in CO ($J =1$–0) and another 16 galaxies marginally detected (S/N $\sim 3$) from the Arizona Radio Observatory’s 12-m telescope. We derive $L_{\rm IR}$ for this sample from *IRAS* 60- and 100-$\rm \mu m$ photometry, following (cite: orellana17).

- (cite: papadopolous12) (hereafter, Pap12) contains 70 local ($z<0.1$) IR galaxies ($10<\log($$L_{\rm IR}$$/{\rm L}_{\odot})<12$) selected from the *IRAS* Revised Bright Galaxy Survey (RBGS; (cite: sanders03)) — a flux-limited sample (flux density at 60 $\rm \mu m$$> 5.24$ Jy). Additionally, this sample has coverage of CO($J=1$–0) from the IRAM 30-m telescope.

 

|        |             |             |             |             |                     |     |
|:------:|:-----------:|:-----------:|:-----------:|:-----------:|:-------------------:|:---:|
|  GAMA  |   S band    |   C band    |   X band    |   Ku band   | $\rm\alpha_{radio}$ |     |
|   ID   | \[$\mu$Jy\] | \[$\mu$Jy\] | \[$\mu$Jy\] | \[$\mu$Jy\] |                     |     |
| 324931 | 510$\pm$57  |     ...     |     ...     | $138\pm30$  |   $-0.81\pm0.10$    |     |
| 543473 |     ...     | $291\pm22$  | $170\pm11$  | $154\pm20$  |   $-0.71\pm0.10$    |     |
| 491545 |     ...     | $347\pm46$  | $213\pm18$  | $164\pm23$  |   $-0.82\pm0.13$    |     |
| 15049  |     ...     |  $93\pm9$   |  $12\pm14$  |  $63\pm17$  |   $-0.58\pm0.21$    |     |
| 319660 |     ...     | $192\pm28$  | $150\pm16$  | $134\pm25$  |   $-0.40\pm0.16$    |     |
| 323772 |     ...     | $629\pm27$  |     ...     |     ...     |         ...         |     |
| 278874 |     ...     |  $68\pm11$  |     ...     |     ...     |         ...         |     |
| 346900 |     ...     | $174\pm15$  |     ...     |     ...     |         ...         |     |
| 600656 |     ...     |     ...     |     ...     |  $45\pm17$  |         ...         |     |
| 210543 | $235\pm32$  |     ...     |     ...     |     ...     |         ...         |     |
| 378002 | $391\pm47$  |     ...     |     ...     |     ...     |         ...         |     |
| 216973 | $740\pm38$  |     ...     |     ...     |     ...     |         ...         |     |

: New radio continuum data for VALES galaxies (see §2.1) in the S band ($\nu = 3$ GHz), C band ($6$ GHz), X band ($10$ GHz) and Ku band ($15$ GHz) bands. The power-law index, $\alpha_{\rm radio}$ ($S\sim\nu^{\alpha_{\rm
    radio}}$) is obtained from these JVLA measurements and we assume $\alpha_{\rm radio} = -0.7\pm0.3$ for the galaxies with RC obtained from the literature (see §[2.1](#subsec: radio date) for more details).

## Radio data

In this work, we present new radio data for the VALES sample obtained from observations taken with the Karl G. Jansky Very Large Array (JVLA; VLA/13B-376, P.I.: E. Ibar) at 3, 6, 10 and/or 15 GHz, with resolutions between 0.6$''$ and 4.0$''$ (see Table [\[tab:jvla
  data - complete\]](#tab:jvla
  data - complete)). Additionally we match the VALES sample with the publicly available Faint Images of the Radio Sky at Twenty-Centimeters (FIRST; (cite: white98)) survey at 1.4 GHz,to obtain a larger sample in the radio continuum emission.

We compute the radio spectral index $\alpha$ ($S_{\nu} \propto \nu^{\alpha}$) in five galaxies from the VALES survey with multiple JVLA detections. To measure the flux densities in galaxies with multiple radio band measurements, we use the Common Astronomy Software Applications (CASA, release 5.0.0)[^3] ((cite: mcmullin07)) task *imsmooth* to degrade the resolution of the images to a common worst resolution. Then we measure the integrated flux density using the task *imfit*, which allows us to use the same Gaussian profile in each image.

For non-VALES galaxies, the RC data were gathered as follows. In the case of the Liu15 sample, this catalogue includes its own radio data. For the xCOLD GASS catalogue, we match this sample with the FIRST survey, with a matching radius of 4$\ensuremath{''}$. For the rest of the samples (Leroy05, Pap12, ALLSMOG and ATLAS$\rm^{3D}$), the measurements at 1.4 GHz are taken from the NRAO VLA Sky Survey (NVSS; (cite: condon98)) using a matching radius of 20$\ensuremath{''}$. To discard possible mismatches, we use the SIMBAD [^4] database (cite: wenger00), and we corroborate that several of these galaxies have optical minor axis greater than 60$\ensuremath{''}$ and/or that the optical images show no other dominant galaxies within a radius of 60 arcsec.

The continuum radio luminosity was obtained in three different ways: (1) for VALES galaxies with multiple JVLA detections, we $k$-correct the flux density, $S_{\rm 1.4GHz}$, using the measured radio spectral index, including error propagation. These spectral indices and errors were obtained from the best fit based on all the JVLA measurements available; (2) for galaxies with only one JVLA, FIRST or NVSS measurement, we estimate the $k$-corrected $S_{\rm 1.4GHz}$ measurement assuming the typical radio spectral index of $-0.7\pm0.3$ ((cite: ibar09)) expected for star-forming galaxies. In this case, the error propagation includes the observed errors and the scatter of the assumed $\alpha$; (3) for galaxies in Liu15 and Leroy05, we use those directly provided by the surveys. Finally, we calculate the radio monochromatic luminosity from $\displaystyle L_{\rm 1.4GHz} = 4\pi D_{\rm L}^2 S_{\rm 1.4GHz}/(1+z),$ where $D_{\rm L}$ is the luminosity distance and $S_{\rm 1.4GHz}$ is the $k$-corrected flux density.

To discard any possible contamination from radio-loud active galactic nuclei (AGN), we matched the entire sample with the 13$\rm^{th}$ Edition of the Catalog of Quasar and AGNs (cite: veron10), finding only four galaxies of our final sample to be radio loud, a typical signature of an AGN. We also matched our final sample with the ALLWISE survey [^5], where 90 per cent of our sample have measurements at 3.4, 4.5 and 12 $\rm \mu m$, allowing us to apply the colour-colour criteria defined by (cite: jarrett11) to identify AGNs. We found five galaxies to be AGNs. In summary, $\sim 3$ per cent of our final sample have possible AGN-related contamination of their RC emission. AGN-contaminated galaxies will often show an excess of 1.4 GHz emission with respect to the sample selected as star-forming galaxies. Fig. [1](#fig:plane) shows no statistically significance from AGN contamination, confirming that making corrections for any excess in the RC emission is unnecessary.

## Final sample

|                 |                  |                        |
|:---------------:|:-----------------|:-----------------------|
|  Final Sample   | Original         | Reference              |
| (# of galaxies) | Sample           |                        |
|       30        | VALES            | (cite: villanueva17)   |
|       12        | VALES (APEX)     | (cite: cheng18)        |
|       75        | xCOLD GASS       | (cite: saintonge17)    |
|       67        | Liu15            | (cite: liu15)          |
|       36        | Pap12            | (cite: papadopolous12) |
|       28        | ATLAS$^{\rm 3D}$ | (cite: cappellari11)   |
|       17        | ALLSMOG          | (cite: cicone17)       |
|       13        | Leroy05          | (cite: leroy05)        |
|       RC        | Original         | Reference              |
| (# of galaxies) | Sample           |                        |
|       12        | VALES            | This work              |
|       189       | NVSS             | (cite: condon98)       |
|       77        | FIRST            | (cite: white98)        |
|       IR        | Original         | Reference              |
| (# of galaxies) | Sample           |                        |
|       42        | H-ATLAS          | (cite: eales10)        |
|       142       | *IRAS*           | (cite: neugebauer84)   |
|       36        | *IRAS* RBGS      | (cite: sanders03)      |
|       13        | *IRAS* FSC       | (cite: moshir90)       |
|       45        | ALLWISE          | (cite: wright10)       |
|   CO($J=1$–0)   | Original         | Reference              |
| (# of galaxies) | Sample           |                        |
|       30        | VALES            | (cite: villanueva17)   |
|       75        | xCOLD GASS       | (cite: saintonge17)    |
|       36        | Pap12            | (cite: papadopolous12) |
|       28        | ATLAS$^{\rm 3D}$ | (cite: cappellari11)   |
|       17        | ALLSMOG          | (cite: cicone17)       |
|       13        | Leroy05          | (cite: leroy05)        |
|       67        | Literature       | (cite: chung09)        |
|                 |                  | (cite: young08)        |
|                 |                  | (cite: kuno07)         |
|                 |                  | (cite: gao04)          |
|                 |                  | (cite: helfer03)       |
|                 |                  | (cite: sofue03)        |
|     12$^*$      | VALES (APEX)     | (cite: cheng18)        |

: Summary of the surveys and references used to produce our final sample, indicating the number of galaxies having RC, IR and CO data in each case.\
$^*$CO data for these galaxies have been converted from CO($J=2$–1)

.

Our final catalogue contains 278 galaxies, where 42 are part of the VALES sample, 67 from Liu15, 75 from xCOLD GASS, 36 from Pap12, 28 from ATLAS$\rm^{3D}$, 17 from ALLSMOG and 13 from Leroy05 (see Table [\[tab:details\]](#tab:details) for more details). This sample is characterised by: (1) CO line measurements with S/N $>5$ for luminosities ranging from $\displaystyle 5.78 < \log\left(L^{\prime}_{\rm CO}/{\rm [K\
    km\,s^{-1}\,pc^2]}\right)< 10.35$, (2) radio detections at S/N $>5$ resulting in a radio luminosity range of $18.64 < \log\left(L_{\rm 1.4GHz}/{\rm [W/Hz]}\right)< 23.78$, (3) redshifts, $z\leq 0.271$, with a median value, $z = 0.017$ and (4) total $L_{\rm IR}$ ranging from $7.3 < \log\left(L_{\rm IR}/{\rm [L_{\odot}]}\right) < 12.14$. While the total number of galaxies in these seven samples is $> 1,000$, we discarded the majority of them either because they are not consistent with our S/N criteria or because they do not have CO, RC or total IR measurements. Additionally, to avoid aperture inconsistencies amongst measurements from different studies, we remove from the sample all galaxies with CO apertures smaller than the Petrosian aperture[^6] in the $r$ band or the optical angular diameter obtained from NED[^7]

# Results

|  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|
| Relation | Slope | Intercept |  | Pearson |
|  | m | b | $\sigma$ | coefficient |
| $L_{\rm 1.4GHz}$–$L_{\rm IR}$ | $0.96\pm0.02$ | $11.98\pm0.23$ | 0.33 | 0.934 |
| $L^{'}_{\rm CO}$–$L_{\rm IR}$ | $0.94\pm0.02$ | $-0.98\pm0.21$ | 0.29 | 0.946 |
| $L^{'}_{\rm CO}$–$L_{\rm 1.4GHz}$ | $1.04\pm0.02$ | $-14.09\pm0.21$ | 0.36 | 0.928 |

:  Best-fit parameters for each relation shown in Fig.[1](#fig:plane) ($\log(y) = m \times \log(x) + b$). In all these relations, the null hypothesis is rejected. The $\sigma$ value is measured from the scatter, shown in the respective relations.

## The evolution of the RC–CO relation

In order to build a RC–CO relation, we first use a RC–IR correlation that is dependent on redshift, together with the IR–CO correlation. For the RC–IR correlation, we use the result obtained by (cite: magnelli15): $$\begin{equation}
 \log \left(\frac{L_{\rm IR}}{\rm
      [W]}\right) =
  \frac{(2.35\pm0.08)}{\left(1+z\right)^{\left(0.12\pm0.04\right)}} +
  \log \left(\frac{L_{\rm 1.4GHz}}{\rm [W\,Hz^{-1}]}\right) + 12.85,
 \label{eq:magnelli}
\end{equation}$$ where $L_{\rm IR}$ is the total integrated IR luminosity (rest-frame 8–1,000 $\rm \mu m$), $z$ is the redshift, and $L_{\rm 1.4GHz}$ is the radio continuum luminosity at 1.4 GHz. This relation was obtained from a sample of $\sim340,000$ galaxies at $z < 2$.

For the IR–CO correlation, we use the results obtained from (cite: villanueva17) based on the VALES sample. They showed that the global $L^{'}_{\rm CO}$-$L_{\rm IR}$ relation can be represented, thus: $$\begin{equation}
\log \left(\frac{L_{\rm IR}}{\rm [W]}\right) = (0.95\pm0.04)\times\log
\left(\frac{L^{\prime}_{\rm CO}}{\rm [K\,km\,s^{-1}\,pc^{2}]}\right) + (28.6\pm0.4), 
\label{eq:villanueva}
 
\end{equation}$$ where the $L^{'}_{\rm CO}$ is the CO ($J=1$–0) luminosity.

Finally, combining the RC–IR and the IR–CO relations (equations [\[eq:magnelli\]](#eq:magnelli) and [\[eq:villanueva\]](#eq:villanueva)), we obtain an expression for the RC–CO relation as a function of redshift: $$\begin{equation}
  \begin{aligned}
 \log &\left(\frac{L^{\prime}_{\rm CO}}{\rm [K\,km\,s^{-1}\,pc^{2}]}\right)  =  (2.47\pm0.13)\times(1+z)^{(-0.12\pm0.04)}\\
  & ~~~~~ +(1.05\pm0.04)\times\log\left(\frac{L_{\rm 1.4GHz}}{\rm [W\,Hz^{-1}]}\right)-(16.5\pm0.8).\\
\label{eq:MV}
\end{aligned} 
\end{equation}$$ Errors were propagated assuming a Gaussian probability distribution. For simplicity, we define eq. [\[eq:MV\]](#eq:MV) as $\xi\left(L_{\rm 1.4GHz},z\right)$.

Fig. [1](#fig:plane) shows the RC–IR (top panel), IR–CO (middle panel) and RC–CO (bottom panel) relations, respectively. Although the samples are different, our fitted solutions and scatter ($< 0.33$ dex, see Table [3](#tab:coeff)) for the RC–IR and the IR–CO plots are in agreement with the respective results by eq. [\[eq:magnelli\]](#eq:magnelli) and eq. [\[eq:villanueva\]](#eq:villanueva) (black line). Additionally, the newly constructed RC–CO relation, based on equations [\[eq:magnelli\]](#eq:magnelli) and [\[eq:villanueva\]](#eq:villanueva), closely matches the best fit of our sampled data.

![image](psfiles/paper-l14-lir-lco_cut.pdf) ![image](psfiles/paper-llco-lir-l14_cut.pdf) ![image](psfiles/paper-lco-l14-lir_cut.pdf)

![image](psfiles/lf_co_z005.pdf) ![image](psfiles/lf_co_z02.pdf) ![image](psfiles/lf_co_z05.pdf) ![image](psfiles/lf_co_z08.pdf) ![image](psfiles/lf_co_11.pdf) ![image](psfiles/lf_co_15.pdf)

![](psfiles/cosmoc_mmol.pdf)

## The RC–CO correlation used to estimate the molecular gas mass function

|            |             |           |       |                    |
|:-----------|:-----------:|:---------:|:-----:|:-------------------|
| Sample     | N$^{\circ}$ | Redshift  | Alias | References         |
|            |    bins     |   range   |       |                    |
| NVSS/6dFGS |      1      | 0.003–0.3 | MS07  | (cite: mauch07)    |
| FIRST/SDSS |      1      | 0.005–0.3 | Pr16  | (cite: pracy16)    |
| VLA/COSMOS |      4      |  0.1–1.3  | Sm09  | (cite: smolcic09)  |
| VLA/CDF-S  |      4      | 0.03–2.3  | Pa11  | (cite: padovani11) |
| VLA/COSMOS |     11      |  0.1–5.7  | No17  | (cite: novak17)    |

: Radio continuum luminosity function surveys.

One of our most relevant results is that we have found a RC–CO correlation for a large sample as a function of redshift, from eq. [\[eq:MV\]](#eq:MV). The sample includes galaxies with different Hubble types at distances greater than 250 Mpc over a wide range of RC and CO line measurements. Because the $L_{\rm 1.4GHz}$ is related to $L^{'}_{\rm CO}$ which is in turn related to the molecular gas mass, $M_{\rm mol}$, via a linear relation, it is possible to estimate the molecular gas mass function (MGMF, $\phi(M_{\rm mol})$) using RC luminosity function (RCLF, $\phi(L_{\rm RC})$) measured at different redshifts in samples of galaxies which exclude the galaxies contaminated by radio-loud AGN. Then, if we replace $\log L_{\rm 1.4GHz}$ by $\phi(L_{\rm RC})$ in eq. [\[eq:MV\]](#eq:MV), we obtain the CO luminosity relation as a function of the redshift. Consequently, by applying eq. [\[eq:MV\]](#eq:MV) to well-measured RCLFs from the literature (see table [4](#tab:LF)), we can obtain the CO luminosity functions across the redshift range $0.003 < z < 5.7$, subdivided into several redshift bins. Although part of the data taken from literature to construct our final sample reach almost $z\sim 6$, our results are constrained up to $z=1.5$ based mainly on the redshift constraints included in eq. [\[eq:magnelli\]](#eq:magnelli) and eq. [\[eq:villanueva\]](#eq:villanueva).

To predict radio luminosity functions independently of the availability of radio continuum data, we can use the evolution of the RCLF using the model proposed by (cite: smolcic09). In this scenario, the local RCLF is based on the model proposed by (cite: sadler02), using a combination of a power-law and a Gaussian distribution of the form: $$\begin{equation}
\phi_{z=0}\left(L_{\rm RC}\right) = \phi^* \left(\frac{L_{\rm
      RC}}{L_*}\right)^{1-\alpha}
\exp\left[\frac{-1}{2\sigma^2}\left(\log\left[1+\frac{L_{\rm RC}}{L_*}\right]\right)^2\right],
\label{eq:lumfunc} 
\end{equation}$$ with a power-law index, $\alpha = 0.84$, a luminosity function at the faint end of $\phi^*=22.9\times10^{-3}\,{\rm [Mpc^{-3}]}$, a standard deviation of the Gaussian distribution, $\sigma=0.94$, and a characteristic luminosity limit between the power-law and the Gaussian distribution, $L_*=1.95\times10^{19}\,{\rm [W\,Hz^{-1}]}$ (for more details, see (cite: sadler02; smolcic09)). Consequently, the evolution of the luminosity function is: $$\begin{equation}
    \phi\left(L_{\rm RC}, z\right) = \phi_{z=0}\left(\frac{L_{\rm
          RC}}{(1+z)^{\alpha_{\rm L}}}\right),
    \label{eq:lumfunc evol}
\end{equation}$$ where $\phi_{z=0}$ is the local luminosity function and a $\alpha_{\rm L}$ is the characteristic luminosity function parameter, with value $\alpha_{\rm L}=2.1\pm0.2$ (cite: sadler02).

$L^{'}_{\rm CO}$ is calculated using eq. [\[eq:MV\]](#eq:MV) and is used to obtain the CO luminosity functions, transforming equations [\[eq:lumfunc\]](#eq:lumfunc) and [\[eq:lumfunc evol\]](#eq:lumfunc evol) as follows: $$\begin{equation}
 \begin{aligned}
 \phi_{z=0}\left(L^{\prime}_{\rm CO}\right)  &=
 \xi\left(\phi_{z=0}\left(L_{\rm 1.4GHz}\right)\right) \\
 \phi\left(L^{\prime}_{\rm CO},z\right) &= \xi\left(\phi\left(L_{\rm 1.4GHz}, z\right)\right)
\end{aligned}
\end{equation}$$

Finally, to obtain the MGMF, we use the conversion factor between $L^{'}_{\rm CO}$ and the molecular gas mass, $M_{\rm mol} =\alpha_{\rm CO}$ $L^{'}_{\rm CO}$, with constant $L^{'}_{\rm CO}$–$\alpha_{\rm CO}$, where $\alpha_{\rm CO}$ is the molecular mass conversion factor and has a value 3.6 M$_{\odot}$/(K km s$^{-1}$ pc$^2$). Although this value for $\alpha_{\rm CO}$ does not take into account the helium contribution (the fraction of He is 36 per cent), we adopt it considering that the reference sample to compare our resulting luminosity functions, (cite: decarli16), uses this value.

We compare our results with those obtained from the semi-analytic MGMF models developed by (cite: popping12) and (cite: lagos18). Fig. [2](#fig:molecular lf) shows the MGMFs (red and cyan lines) estimated for six redshift bins centred at $<z> = 0.05, 0.2, 0.5, 0.8, 1.1$ and $1.5$, covering the redshift range from 0.003–2.3. Each sample used is identified by different symbols and colours (see the caption to Fig. [2](#fig:molecular lf)). The errors result from the addition in quadrature of the error from the original RCLF and the scatter in the $L^{'}_{\rm CO}$–$L_{\rm 1.4GHz}$ correlation. The purple (cite: popping12) and dark green (cite: lagos18) lines corresponds to semi-analytic models.

Although we could potentially construct a RCLF up to $z=5.7$, our results for the MGMF show a considerable over-estimate in comparison with the semi-analytic models for RCLF at redshifts $z > 1.5$.

This problem can be caused by: a) the $L^{'}_{\rm CO}$–$L_{\rm 1.4GHz}$ correlation function evolving with redshift in a different way than that considered in this work; b) it may be incorrect to adopt a constant $\alpha_{\rm CO}$ given that starburst galaxies are more abundant at higher redshifts; c) the RCLM at higher redshifts only characterises the galaxies richest in molecular gas, as a consequence of the detection limit in the radio images; d) semi-analytic models may under-estimate the molecular gas mass at high redshift. Additionally, with the assumption of a constant $\alpha_{\rm CO}$, we ignore any possible variation of the conversion factor as a function of galaxy properties, where the most important property is the dependence on gas-phase metallicity (e.g. (cite: wilson95; arimoto96; barone00; israel00; boselli02; magrini11; schruba12; hunt15; amorin16)).

## Cosmic molecular gas mass content

Based on the results obtained from our MGMF analysis, we can predict the molecular gas mass density and its evolution with cosmic time. Molecular gas mass density is defined as: $$\begin{equation}
\rho_{(M_{\rm mol})}=\int^{\log M_2}_{\log M_1} \frac{dN}{d\log M~ dV} ~ M~ d\log M.  
\end{equation}$$ Fig. [3](#fig:cosmic mol mass) shows the resulting $\rho_{(M_{\rm mol})}$ in the redshift range $0 < z < 1.5$, where the red points are derived using the entire mass range available from the respective RCLF. This means that this derived $\rho_{(M_{\rm mol})}$ has different integration mass limits in different redshift bins. For this reason, we make use of the RCLF from (cite: smolcic09) to obtain a continuous MGMF where we can extrapolate a fixed integration mass limit to compare our results with the predictions from semi-analytic models. After fixing the integration mass limit in the range $9 < \log(M_{\rm mol}/{\rm M}_\odot)< 11$ (the range deduced from the MGMFs obtained by (cite: decarli16), but not specified in that work) we can then determine the $\rho_{(M_{\rm mol})}$ based on our continuous MGMF (cyan diamonds). Our results fall inside the errors of the direct measurements obtained by (cite: decarli16) (gray rectangles), while the semi-analytic models show higher and lower values for the models from ((cite: popping12) (purple line) and (cite: lagos18) (green line), respectively.

The main source of uncertainty in $\rho_{(M_{\rm mol})}$ comes from the uncertainty in the measured RC luminosity functions.

## The empirical CO–RC–IR plane

![](psfiles/paper-edplane14-2.pdf)

Although the physical parameters used for the star-formation relations in this paper — the IR, CO and RC emission — are all tracers of newly formed stars, to our knowledge there is no previous use in the literature of parameter space combining all of them in a single relation. Fig. [1](#fig:plane) shows that these three parameters vary in a correlated way. Based on that, we conclude that each panel corresponds to the projection of a CO–RC–IR plane. We present the 3D view of these three relations in Fig. [4](#fig:plane-final_one) forming a plane for which we obtained a numerical expression using the MPFIT algorithm[^8] (cite: markwardt09):

$$\begin{equation}
\begin{aligned}
 \log&\rm\left(\frac{L^{\prime}_{\rm CO}}{\rm
     [K\,km\,s^{-1}\,pc^2]}\right) = (0.61\pm0.05)
 \times\log\left(\frac{L_{\rm IR}}{\rm [L_{\odot}]}\right) \\
 & ~~~~~~~~+ (0.36\pm0.05) \times\log\left(\frac{L_{\rm 1.4GHz}}{\rm [W\,Hz^{-1}]}\right) - (5.4\pm0.7) ~. 
\label{eq:plane}
\end{aligned}
\end{equation}$$

For different views of the plane based on eq. [\[eq:plane\]](#eq:plane), see Appendix [6](#ap:A).

# Discussion

## Cosmic evolution of molecular gas

The intimate connection between the RC, CO and IR emission during the process of forming stars is well established for samples of galaxies. However, understanding the mechanism that links these three parameters remains a challenge for star-formation models, considering the different physical origins for the different emission.

Several tracers of star-formation activity exist. Direct methods include tracing the UV light from young stellar populations. However, UV attenuation by dust in galaxies requires additional corrections. For example, it has been proposed that the emission at 24 $\rm \mu m$ can be used to correct the dust attenuation in far-UV (FUV) and H$\alpha$ data, resulting in more realistic estimates of the SFR in galaxies (cite: kennicutt07; calzetti07). These combined calibrations of SFR are used extensively for nearby galaxies (e.g. (cite: rahman11; ford13; momose13; casasola17))

To avoid correcting for extinction, IR emission is widely used as a star-formation tracer. Two energy sources contribute to the IR spectral energy distribution (SED): a warm dust component, where grains absorb UV photons from young, massive ($> 8$ $\rm M_{\odot}$) stars (e.g. (cite: devereux91; condon92)), and a cold dust component — a consequence of the absorption of optical photons from the interstellar radiation field (e.g. (cite: xu96)). The IR emission is a powerful star-formation tracer, better than other more direct indicators that are affected by extinction (e.g. H$_\alpha$ emission systematically under-estimates, by an order of magnitude, the formation of stars in galaxies with SFR $\geq 20$ $\rm M_{\odot}$ yr$^{-1}$ (cite: cram98)).

The RC emission results from the combined contribution of thermal emission — free-free radiation from H ii regions related to the number of massive, short-lived stars — and non-thermal emission — synchrotron radiation produced by relativistic electrons interacting with the magnetic field of the galaxy (cite: condon92). These two components dominate the RC at different frequencies, where the transition between the thermal and non-thermal component happens at $\nu \approx 30$ GHz (emission at higher frequencies is mainly thermal and at lower frequencies is mainly synchrotron). (cite: condon92) suggests that thermal radiation contributes less than 10 per cent of the total RC radiation at $\sim 1$ GHz and that the total radio luminosity at 1.4 GHz is directly proportional to the supernovae (SN) rate. Synchrotron radio emission from star-forming galaxies is produced by the interaction of energetic electrons — accelerated by the massive stars when they have reached the supernovae stage — and the ambient magnetic field (cite: israel84; voelk89). Radio emission is unaffected by dust absorption, making RC emission an ideal tool to calibrate other tracers of star formation.

Lastly, CO emission is the consequence of the interaction between CO molecules and the molecular hydrogen (H$_2$) in regions where stars are formed — giant molecular clouds (GMC). CO emission is correlated with the virial mass of GMCs observed in the Milky Way and in nearby spiral galaxies (cite: young91).

Historically, the IR–RC–CO parameters have been studied using three empirical relations, each one having different properties: first, the RC–IR correlation (e.g. (cite: yun01; ivison10; thomson14; magnelli15; dumas11; tabatabei13a; tabatabei13b)), valid up to $z \sim 2$ and at a resolution of $\ge 500$ pc. Second, the Schmidt-Kennicutt (SK) IR–CO law (cite: kennicutt98; kennicutt12), valid for high-SFR, bright galaxies as well as low-surface-brightness galaxies with low SFR. The form of the SK law is still debated because the observations of disk and starburst galaxies have shown that this relation can be fitted either by a single or a bi-modal solution for the redshifts range 0.05–2.5 (e.g. (cite: genzel10; daddi10; ivison11; kennicutt12; tacconi13; santini14; freundlich19)). The slope of the SK law, which defines the depletion time of the gas in a galaxy ($\tau_{\rm dep} \equiv M_{\rm gas}/{\rm SFR}$), is central to our understanding of the mechanisms that govern star formation. According to models, a linear slope implies that star-formation activity is not driven only by the self gravity of the galaxy (cite: semenov17; semenov19). Several studies dedicated to the spatially-resolved KS relation on sub-kpc scales found a wide range in the value of the slope (indicated by the power law index, $N \sim
  0.6$–3; $\Sigma_{\rm SFR}\propto\Sigma_{M(\rm H_2)}^N$) of the KS relation (cite: bigiel08; kennicutt12; rahman11; viaene14; casasola15). The spread in the value of $N$ may be intrinsic, suggesting that different SF relations exist; alternatively, it may be due to the assumptions adopted in each study. (cite: daddi10) suggest that $L_{\rm IR}$ (tracing SFR) and $L^{'}_{\rm CO}$ (tracing molecular gas mass) show no evolution in normal star-forming galaxies up to $z=1.5$. However, (cite: tacconi18) suggest that $\tau_{\rm dep} \propto (1+z)^{-0.62}$, implying that $\tau_{\rm dep}$ decreases by a factor of $\approx2\times$, up to the redshift limit explored in our study, $z= 1.5$. Third, the RC–CO correlation (e.g. (cite: adler91; murgia02; murgia05; leroy05; paladino06; schinnerer13; liu15)), is valid for different galaxy types and also down to scales of few hundred parsecs in some selected local galaxies.

In this work we derive eq. [\[eq:MV\]](#eq:MV) by combining RC–IR and IR–CO relations from the literature to obtain the molecular gas mass density of the Universe, after deriving the integrated MGMF from measurements of the RCLF corrected by $\alpha_{\rm CO}=3.6~{\rm [M_{\odot}/(K\,km\,s^{-1}\,pc^2)]}$. We find that the resulting molecular gas mass density increases by a factor of $4.4\times$ across $z=0.05$–1.5. As mentioned above, we expect that the evolution of the depletion time has little impact on our final gas mass densities.

## Using the CO–RC–IR plane to predict CO emission in galaxies

Several authors have proposed models to explain the physical connection between the radio, infrared and CO luminosities. One of the earliest models proposes that the RC–IR correlation is physically linked to the formation of young massive stellar populations (e.g. (cite: helou85; condon92)) since GMCs collapse to form stars of large masses, responsible for an intense radiation field in star-forming galaxies. A large fraction of the UV photons from the forming stars heat the dust grains, re-processing the UV radiation into IR emission. Considering that the main mechanism that drives this model ((cite: adler91; murgia02)) is the formation of new stars, it is expected that $L^{'}_{\rm CO}$ — a classical tracer of the gas reservoir for future star formation — is correlated with IR and RC emission. As a first approach, this model offers a simple mechanism to explain how these three parameters can be related by considering that the origin of the IR emission and the non-thermal synchrotron corresponds to newly formed stars in molecular clouds. However, this model is unable to explain several problems, e.g. why the RC–IR correlation is maintained at scales of kpc and the RC–CO relation holds at scales of $\sim100$ pc. In addition, (cite: schinnerer13) argue that this model requires too many intermediate physical processes to observationally correlate both the RC and the IR emission, where each of these processes has to contribute to a larger scatter than that obtained from observations. Alternative models, e.g. the calorimeter model ((cite: voelk89; lisenfeld96)), the magnetic field-gas density coupling ((cite: helou93; niklas97)), and the proton calorimeter model (cite: suchkov93; lacki10) also struggle to explain the physical mechanisms involved in these relations.

Our work provides an empirical solution that combines CO–RC–IR into a plane, which can be exploited to update star-formation models. We find that our proposed plane — where the CO, RC, and IR luminosities are fitted simultaneously — results in smaller scatter for each of the relations than when they are fitted independently in pairs. For example, the comparison between the estimated $L^{'}_{\rm CO}$ obtained using eq. [\[eq:plane\]](#eq:plane) and the actual measured $L^{'}_{\rm CO}$ shows a scatter of 0.27 dex (a factor $1.86\times$). The scatter between our sample and the IR–CO and RC–CO relations are 0.29 and 0.36 dex, respectively (see Table [3](#tab:coeff)). As a consequence, the CO–RC–IR plane constitutes a powerful tool to predict, in a very efficient way, the CO emission in large samples of galaxies lacking molecular mass measurements. Although the CO–RC–IR plane is fitted using a wide range of galaxy types (local LIRGs, massive star-forming galaxies, elliptical galaxies with star formation, dwarf galaxies), the scatter for the predicted CO emission from the plane is lower than the scatter from independent use of the IR–CO or RC–CO relations.

Using a sample of $\sim80$ metal-rich and -poor dwarf galaxies, (cite: filho19) studied the star-forming relations RC–IR, RC–CO and IR–CO finding that they cannot be extended down to low radio luminosity dwarfs. A breakdown for the dwarfs appears towards brighter radio luminosities in both relations with respect to the solution for bright galaxies from (cite: price92; liu10; kennicutt11; murgia05). According to (cite: filho19), the breakdown in the RC–CO and IR–CO relations reflects a depletion of CO in dwarf galaxies, which have a hard ionising radiation field, low dust shielding and slower chemical reaction rates, making this molecule an inefficient tracer of molecular gas. Cosmic rays from starburst episodes also play a role in destroying the CO molecules. We cannot directly compare (cite: filho19)’s results with our work because the range of luminosities for their sample of dwarfs is about an order of magnitude fainter than ours.

Considering that each parameter used in the construction of the plane involves observed emission coming directly or indirectly from the formation of stars, the simplest scenario to explain the existence of this three-fold relation lies with models where star formation is the main driver. Assuming that star formation is the main driver behind the observed consistency of RC, IR, CO emission, then implementing it to predict CO emission on a different sample requires the selection of star-forming galaxies only, where no contribution of AGN is present.

# Summary

In summary, we have used 278 nearby ($z < 0.27$) galaxies with measurements of global CO lines ($J=1$–0 or $J=2$–1), total IR luminosity and radio continuum flux density at 1.4 GHz to study the scaling relations between the CO, RC, and IR luminosities and to determine the cosmic evolution of the molecular gas content of the Universe. Assuming that star formation is the main mechanism that drives the existence of the SK (IR–CO) and RC–IR relations, we derive the RC–CO relation as a function of redshift. This relation allows us to estimate the molecular gas mass function (MGMF) using the radio continuum luminosity function (RCLF) from the literature, obtaining consistent results as compared with the MGMF from semi-analytic models across $0.05 <z < 1.5$. Finally, from the integration of the different MGMFs, we estimate the cosmic evolution of the molecular gas mass density ($\rho(M_{\rm mol})$) in star-forming galaxies, in six redshift bins, showing an increment of $4.4\times$ across this redshift range.

In addition, we found that these three luminosities ($L^{'}_{\rm CO}$, $L_{\rm 1.4GHz}$ and $L_{\rm IR}$) form a plane, presumably as a consequence of the common physical mechanisms behind these three observable quantities in the context of star formation in galaxies. The plane is valid across more than five orders of magnitude for each of the luminosities, across the redshift range 0.05–0.27, and it can be used to predict CO emission from the IR and radio continuum measurements of galaxies, with a scatter of 0.27 dex. The agreement of our estimates with semi-analytical models, as well as with the results from the ALMA large programme, ASPECS, is a clear indication of the power of the method presented here as a tool to predict molecular gas mass at different cosmic epochs. Future large radio surveys, such as those conducted by the Square Kilometer Array, will be able to exploit these results.

# Acknowledgements

We thank Claudia Lagos and Gerg$\rm\ddot{o}$ Popping, who provided us with data from their semi-analytic models. The authors acknowledge support provided by: FONDECYT through grant N$^\circ$ 3170942 (G.O.G.) and grant N$^\circ$ 1171710 (E.I.); CONICYT-PIA ACT N$^\circ$ 172033 and CONICYT QUIMAL N$^\circ$ 160012 (R.L.); the Young Researcher Grant of National Astronomical Observatories, Chinese Academy of Science and the National Natural Science Foundation of China, N$^\circ$ 11803044 and N$^\circ$ 11933003 (C.C.); STFC (ST/P000649/1) (A.T.); and the Chinese Academy of Sciences (CAS) and the National Commission for Scientific and Technological Research of Chile (CONICYT) through a CAS-CONICYT Joint Postdoctoral Fellowship administered by the CAS South America Center for Astronomy (CASSACA) in Santiago, Chile (T.H.); CONICYT (Chile) through Programa Nacional de Becas de Doctorado 2014 folio 21140882 (P.C.C.). We acknowledge the National Radio Astronomy Observatory, a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology. This research has made use of the SIMBAD database, operated at CDS, Strasbourg, France This work makes use of JVLA project, 13B-376. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.01080.S and ADS/JAO.ALMA#2013.1.00530.S. This publication is based on data acquired with the Atacama Pathfinder Experiment (APEX): programmes 097.F-9724(A) and 098.F-9712(B). APEX is a collaboration between the Max-Planck-Institut fur Radioastronomie, ESO, and the Onsala Space Observatory.

# The best-fit plane

This appendix includes different views of the plane $L^{'}_{\rm CO}$­–$L_{\rm 1.4GHz}$ — $L_{\rm IR}$. The black lines in Fig. [1](#fig:plane) show the best-fit plane, shown in eq. [\[eq:plane\]](#eq:plane); the red circles are the galaxies in our final sample.

Using this plane, it is clear that the dispersion shown is tiny compared with the large range of IR, RC and CO used in our work.

![image](psfiles/paper-edplane15-2.pdf) ![image](psfiles/paper-edplane16-2.pdf) ![image](psfiles/paper-edplane17-2.pdf)

99 (ref: adler91) Adler D. S., Allen R. J., Lo K. Y., 1991, ApJ, 382, 475 (ref: amorin16) Amorı́n, R., Muñoz-Tuñón, C., Aguerri, J. A. L., et al. 2016, A&A, 588, A23 (ref: arimoto96) Arimoto, N., Sofue, Y., & Tsujimoto, T. 1996, PASJ, 48, 275 (ref: barone00) Barone, L. T., Heithausen, A., Hüttemeister, S., et al. 2000, MNRAS, 317, 649 (ref: behroozi13) Behroozi, P. S., Wechsler, R. H., et al. 2013, ApJ, 770, 57 (ref: bell03) Bell, E. F. 2003, ApJ, 586, 794 (ref: bianchi13) Bianchi, S. 2013, A&A, 552, A89 (ref: bigiel08) Bigiel, F., Leroy, A., Walter, F., et al. 2008, AJ, 136, 2846 (ref: bolatto13) Bolatto, A. D., Wolfire, M., et al. 2013, ARA&A, 51, 207 (ref: boselli02) Boselli, A., Lequeux, J., & Gavazzi, G. 2002, Ap&SS, 281, 127 (ref: bothwell13) Bothwell, M. S., Smail, I., et al. 2013, MNRAS, 429, 3047 (ref: cappellari11) Cappellari, M., Emsellem, E., et al. 2011, MNRAS, 413, 813 (ref: carilli13) Carilli C. L., Walter F., 2013, ARA$\&$A, 51, 105 (ref: casasola20) Casasola, V., Bianchi, S., De Vis, P., et al. 2020, A&A, 633, A100 (ref: casasola17) Casasola, V., Cassarà, L. P., Bianchi, S., et al. 2017, A&A, 605, A18 (ref: casasola15) Casasola, V., Hunt, L., Combes, F., et al. 2015, A&A, 577, A135 (ref: calzetti07) Calzetti, D., Kennicutt, R. C., Engelbracht, C. W., et al. 2007, ApJ, 666, 870 (ref: cheng18) Cheng, C., Ibar, E., et al. 2018, MNRAS, 475, 248 (ref: chung09) Chung, A., van Gorkom, J. H., Kenney, J. D. P., et al. 2009, AJ, 138, 1741 (ref: cicone17) Cicone, C., Bothwell, M., Wagg, J., et al. 2017, A&A, 604, A53 (ref: clark15) Clark, C. J. R., Dunne, L., Gomez, H. L., et al. 2015, MNRAS, 452, 397 (ref: clemens13) Clemens, M. S., Negrello, M., De Zotti, G., et al. 2013, MNRAS, 433, 695 (ref: cluver14) Cluver, M. E., Jarrett, T. H., et al. 2014, ApJ, 782, 90 (ref: condon98) Condon, J. J., Cotton, W. D., et al. 1998, AJ, 115, 1693 (ref: condon92) Condon, J. J. 1992, ARA&A, 30, 575

(ref: cram98) Cram, L., Hopkins, A., Mobasher, B., et al. 1998, ApJ, 507, 155 (ref: daddi10) Daddi, E., Elbaz, D., et al. 2010, ApJL, 714, L118 (ref: davies17) Davies, J. I., Baes, M., Bianchi, S., et al. 2017, PASP, 129, 044102 (ref: davies19) Davies, L. J. M., Lagos, C. del P., Katsianis, A., et al. 2019, MNRAS, 483, 1881

(ref: decarli16) Decarli, R., Walter, F., et al. 2016, ApJ, 833, 69 (ref: devereux90) Devereux, N. A., & Young, J. S. 1990, ApJ, 359, 42 (ref: devereux91) Devereux, N. A., & Young, J. S. 1991, ApJ, 371, 515 (ref: draine07) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: driver16) Driver, S. P., Wright, A. H., et al. 2016, MNRAS,455, 3911 (ref: dumas11) Dumas, G., Schinnerer, E., Tabatabaei, F. S., et al. 2011, AJ, 141, 41 (ref: dunne01) Dunne, L., & Eales, S. A. 2001, MNRAS, 327, 697 (ref: dunne11) Dunne, L., Gomez, H. L., da Cunha, E., et al. 2011, MNRAS, 417, 1510 (ref: eales10) Eales, S., Dunne, L., Clements, D., et al. 2010, PASP, 122, 499 (ref: filho19) Filho, M. E., Tabatabaei, F. S., Sánchez Almeida, J., et al. 2019, MNRAS, 484, 543 (ref: ford13) Ford, G. P., Gear, W. K., Smith, M. W. L., et al. 2013, ApJ, 769, 55 (ref: freundlich19) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105 (ref: gao04) Gao, Y., & Solomon, P. M. 2004, ApJ, 606, 271 (ref: genzel10) Genzel, R., Tacconi, L. J., et al. 2010, MNRAS, 407, 2091 (ref: genzel15) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: helfer03) Helfer, T. T., Thornley, M. D., Regan, M. W., et al. 2003, ApJS, 145, 259 (ref: helou93) Helou, G., & Bicay, M. D. 1993, ApJ, 415, 93 (ref: helou85) Helou, G., Soifer, B. T., & Rowan-Robinson, M. 1985, ApJL, 298, L7

(ref: hughes17a) Hughes, T. M., Ibar, E., et al. 2017, A&A, 602, A49 (ref: hughes17b) Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, MNRAS, 468, L103 (ref: hunt15) Hunt, L. K., Garcı́a-Burillo, S., Casasola, V., et al. 2015, A&A, 583, A114 (ref: ibar08) Ibar, E., Cirasuolo, M., Ivison, R., et al. 2008, MNRAS, 386, 953 (ref: ibar09) Ibar, E., Ivison, R. J., et al. 2009, MNRAS, 397, 281 (ref: israel84) Israel, F., & Rowan-Robinson, M. 1984, ApJ, 283, 81 (ref: israel00) Israel, F. 2000, Molecular Hydrogen in Space, 293 (ref: ivison10) Ivison, R. J., Magnelli, B., Ibar, E., et al. 2010, A&A, 518, L31 (ref: ivison11) Ivison, R. J., Papadopoulos, P. P., Smail, I., et al. 2011, MNRAS, 412, 1913 (ref: jarrett11) Jarrett, T. H., Cohen, M., Masci, F., et al. 2011, ApJ, 735, 112 (ref: kennicutt12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531 (ref: kennicutt11) Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011, PASP, 123, 1347 (ref: kennicutt98) Kennicutt R. C., 1998, ApJ, 498, 541 (ref: kennicutt07) Kennicutt, R. C., Calzetti, D., Walter, F., et al. 2007, ApJ, 671, 333

(ref: kuno07) Kuno, N., Sato, N., Nakanishi, H., et al. 2007, PASJ, 59, 117 (ref: lacki10) Lacki, B. C., Thompson, T. A., & Quataert, E. 2010, ApJ, 717, 1

(ref: lagos18) Lagos, C. d. P., Tobar, R. J., et al. 2018, MNRAS, 481, 3573 (ref: leroy05) Leroy A., Bolatto A. D., Simon J. D., Blitz L., 2005, ApJ, 625, 763 (ref: lisenfeld96) Lisenfeld, U., Voelk, H. J., & Xu, C. 1996, A&A, 306, 677 (ref: liu15) Liu, L., Gao, Y., & Greve, T. R. 2015, ApJ, 805, 31 (ref: liu10) Liu, F., & Gao, Y. 2010, ApJ, 713, 524 (ref: madau14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415 (ref: madau96) Madau, P., Ferguson, H. C., Dickinson, M. E., et al. 1996, MNRAS, 283, 1388 (ref: magnelli15) Magnelli, B., Ivison, R. J., Lutz, D., et al. 2015, A&A, 573, A45

(ref: magrini11) Magrini, L., Bianchi, S., Corbelli, E., et al. 2011, A&A, 535, A13

(ref: mauch07) Mauch, T., & Sadler, E. M. 2007, MNRAS, 375, 931 (ref: markwardt09) Markwardt, C. B. 2009, Astronomical Data Analysis Software and Systems XVIII, 411, 251 (ref: mcmullin07) McMullin, J. P., Waters, B., et al. 2007, Astronomical Data Analysis Software and Systems XVI, 376, 127 (ref: molina19) Molina, J., Ibar, E., Villanueva, V., et al. 2019, MNRAS, 482, 1499 (ref: momose13) Momose, R., Koda, J., Kennicutt, R. C., et al. 2013, ApJL, 772, L13 (ref: moshir90) Moshir, M., & et al. 1990, IRAS Faint Source Catalogue (ver. 2.0; Pasadena: IPAC) (ref: murgia05) Murgia M., Helfer T. T., Ekers R., Blitz L., Moscadelli L., Wong T., Paladino R., 2005, A&A, 437, 389 (ref: murgia02) Murgia M., Crapsi A., Moscadelli L., Gregorini L., 2002, A&A, 385, 412

(ref: neugebauer84) Neugebauer, G., Habing, H. J., et al. 1984, ApJL, 278, L1 (ref: niklas97) Niklas, S., & Beck, R. 1997, A&A, 320, 54

(ref: novak17) Novak, M., Smolčić, V., Delhaize, J., et al. 2017, A&A, 602, A5 (ref: orellana17) Orellana, G., Nagar, N. M., et al. 2017, A&A, 602, A68

(ref: padovani11) Padovani, P., Miller, N., et al. 2011, ApJ, 740, 20 (ref: paladino06) Paladino, R., Murgia, M., Helfer, T. T., et al. 2006, A&A, 456, 847 (ref: papadopolous12) Papadopoulos, P. P., et al. 2012, MNRAS, 426, 2601

(ref: popping12) Popping, G., Caputi, K. I., et al.  2012, MNRAS, 425, 2386

(ref: pracy16) Pracy, M. B., Ching, J. H. Y., et al. 2016, MNRAS, 460, 2 (ref: price92) Price, R., & Duric, N. 1992, ApJ, 401, 81 (ref: rahman11) Rahman, N., Bolatto, A. D., Wong, T., et al. 2011, ApJ, 730, 72 (ref: rickard77) Rickard, L. J., Palmer, P., Morris, M., et al. 1977, ApJ, 213, 673

(ref: sadler02) Sadler, E. M., Jackson, C. A., Cannon, R. D., et al. 2002, MNRAS, 329, 227 (ref: sanders03) Sanders, D. B., Mazzarella, J. M., et al.  2003, AJ, 126, 1607 (ref: santini14) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30 (ref: saintonge17) Saintonge, A., et al. 2017, ApJS, 233, 22 (ref: saintonge11a) Saintonge, A., Kauffmann, G., et al. 2011, MNRAS, 415, 32 (ref: saintonge11b) Saintonge, A., Kauffmann, G., et al. 2011, MNRAS, 415, 61 (ref: schinnerer13) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, 42 (ref: schruba12) Schruba, A., Leroy, A. K., Walter, F., et al. 2012, AJ, 143, 138

(ref: scoville16) Scoville, N., Sheth, K., et al. 2016, ApJ, 820, 83 (ref: scoville14) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84 (ref: semenov19) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2019, ApJ, 870, 79 (ref: semenov17) Semenov, V. A., Kravtsov, A. V., & Gnedin, N. Y. 2017, ApJ, 845, 133 (ref: smith14) Smith, D. J. B., Jarvis, M. J., Hardcastle, M. J., et al. 2014, MNRAS, 445, 2232

(ref: smolcic09) Smolčić, V., Schinnerer, E., et al. 2009, ApJ, 690, 610 (ref: sofue03) Sofue, Y., Koda, J., Nakanishi, H., et al. 2003, PASJ, 55, 17 (ref: suchkov93) Suchkov, A., Allen, R. J., & Heckman, T. M. 1993, ApJ, 413, 542 (ref: tabatabei13a) Tabatabaei, F. S., Schinnerer, E., Murphy, E. J., et al. 2013, A&A, 552, A19 (ref: tabatabei13b) Tabatabaei, F. S., Berkhuijsen, E. M., Frick, P., et al. 2013, A&A, 557, A129 (ref: tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179 (ref: tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74 (ref: thomson14) Thomson, A. P., Ivison, R. J., Simpson, J. M., et al. 2014, MNRAS, 442, 577 (ref: tisley80) Tinsley, B. M., & Danly, L. 1980, ApJ, 242, 435 (ref: veron10) Véron-Cetty, M.-P., & Véron, P. 2010, A&A, 518, A10 (ref: viaene14) Viaene, S., Fritz, J., Baes, M., et al. 2014, A&A, 567, A71 (ref: villanueva17) Villanueva, V., Ibar, E., et al. 2017, MNRAS, 470, 3775 (ref: voelk89) Voelk, H. J. 1989, A&A, 218, 67 (ref: walter16) Walter, F., Decarli, et al. 2016, ApJ, 833, 67 (ref: wenger00) Wenger, M., Ochsenbein, F., Egret, D., et al. 2000, A&AS, 143, 9

(ref: white98) White, R. L., Becker, R. H., et al. 1998, ApJ, 475, 47 (ref: wilson95) Wilson, C. D. 1995, ApJL, 448, L97 (ref: wright10) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868 (ref: xu96) Xu, C., & Helou, G. 1996, ApJ, 456, 163 (ref: young11) Young, L. M., Bureau, M., et al. 2011, MNRAS, 414, 940 (ref: young08) Young, L. M., Bureau, M., & Cappellari, M. 2008, ApJ, 676, 317 (ref: young91) Young, J. S., & Scoville, N. Z. 1991, ARA&A, 29, 581 (ref: yun01) Yun, M. S., Reddy, N. A., Condon, J. J. 2001, ApJ, 554, 803

[^1]: gustavo.orellana@uv.cl

[^2]: *Herschel Astrophysical Tera-Hertz Large Area Survey*

[^3]: $\rm https://casa.nrao.edu$

[^4]: $\rm http://simbad.u-strasbg.fr/simbad/$

[^5]: https://irsa.ipac.caltech.edu/cgi-bin/Gator/nph-dd

[^6]: The Petrosian ratio $\rm R_p$ at a radius *r* from the center of an object, is the ratio of the local surface brightness in an annulus at *r* to the mean surface brightness within *r*. Then Petrosian radius $\rm r_p$ (Petrosian aperture = $\rm 2r_p$) is defined as the radius as the radius at which the Petrocian ratio equals some limit value, set to 0.2 in our case.

[^7]: https://ned.ipac.caltech.edu/

[^8]: https://www.physics.wisc.edu/$\sim$craigm/idl/fitting.html

</paper>

Write the methods card for this paper.