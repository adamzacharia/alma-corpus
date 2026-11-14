# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...908...15S\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...908...15S",
 "title": "Dust, Gas, and Metal Content in Star-forming Galaxies at z ∼ 3.3 Revealed with ALMA and Near-IR Spectroscopy",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Suzuki, Tomoko L.",
 "n_authors": 11,
 "arxiv_id": "2012.09447",
 "doi": "10.3847/1538-4357/abd4e7",
 "alma_projects_linked_by_archive": [
  "2018.1.00681.S"
 ]
}
```

Paper text:
<paper>
# Dust, gas, and metal content in star-forming galaxies at $z\sim3.3$ revealed with ALMA and Near-IR spectroscopy

## Abstract

We conducted sub-millimeter observations with the Atacama Large Millimeter/sub-millimeter Array (ALMA) of star-forming galaxies at $z\sim3.3$, whose gas-phase metallicities have been previously measured. We investigate the dust and gas contents of the galaxies at $z\sim3.3$ and study how galaxies are interacting with their circumgalactic/intergalactic medium at this epoch by probing their gas mass fractions and gas-phase metallicities. Single-band dust continuum emission tracing dust mass and the relation between the gas-phase metallicity and gas-to-dust mass ratio are used to estimate the gas masses. The estimated gas mass fractions and depletion timescales are $f_{\rm gas}=$ 0.20–0.75 and $t_{\rm dep}=$ 0.09–1.55 Gyr, respectively. Although the galaxies appear to tightly distribute around the star-forming main sequence at $z\sim3.3$, both quantities show a wider spread at a fixed stellar mass than expected from the scaling relation, suggesting a large diversity of fundamental gas properties among star-forming galaxies apparently on the main sequence. Comparing gas mass fraction and gas-phase metallicity between the star-forming galaxies at $z\sim3.3$ and at lower redshifts, star-forming galaxies at $z\sim3.3$ appear to be more metal-poor than local galaxies with similar gas mass fractions. Using the gas regulator model to interpret this offset, we find that it can be explained by a higher mass-loading factor, suggesting that the mass-loading factor in outflows increases at earlier cosmic times.

# Introduction

Molecular gas ($\rm H_2$) is one of the fundamental physical quantities of galaxies because it is the fuel for star formation. It is well known that the gas surface density is correlated with the star-formation rate (SFR) surface density (the Schmidt–Kennicutt relation; (cite: schmidt1959; kennicutt98)). The total gas mass is also connected with the total star-forming activity (cite: daddi10; genzel10). The typical SFR of star-forming galaxies at a given stellar mass appears to monotonically increases with increasing redshifts (cite: whitaker12; sobral14; tomczak16). More active star formation in galaxies at higher redshifts is considered to be supported by a larger amount of gas (cite: daddi10; genzel10; geach11; bothwell13_mnras429; tacconi13; birkin20). Investigating the gas contents in galaxies at high redshifts is crucial to understand formation and evolution of galaxies in the Universe (cite: walter16; riechers19).

Observational studies over the past decade revealed the gas properties not only for dusty starburst galaxies, such as sub-millimeter bright galaxies (SMGs), but also for ultraviolet (UV)/optical–selected star-forming galaxies on the stellar mass–SFR relation, the so-called “main sequence” of star-forming galaxies, at $z\gtrsim1$ (cite: daddi10; genzel10; tacconi10; tacconi13; magdis17).

The increasing number of galaxies with individual measurements of the gas mass in a wide redshift range makes it possible to establish the scaling relations for gas mass fraction and gas depletion timescale ($\rm =M_{\rm gas}/{\rm SFR}$) as a function of redshift, stellar mass, and SFR (cite: scoville17; tacconi18; freundlich19; liu19_II). At $z>3$, however, the number of UV/optical-selected star-forming galaxies with the individual measurements of gas content is still small (with CO emission lines: (cite: magdis17; cassata20), and with dust continuum: (cite: schinnerer16; wiklind19; aravena20)). How the gas properties of UV/optical-selected galaxies evolve at $z>3$ are not conclusive yet.

The atomic and/or molecular hydrogen gas mass is also said to be correlated with the gas-phase metallicity from both observations (cite: bothwell13; hunt15; bothwell16_mnras; seko16_alma; brown18) and cosmological numerical simulations (cite: lagos16; torrey19). It has been suggested that the gas mass is more fundamental than the SFR to explain the scatter of the mass–metallicity relation of star-forming galaxies (cite: bothwell13; zahid_apj791; brown18). Indeed, more gas-rich star-forming galaxies tend to be more metal-poor and more actively forming stars.

Galaxies evolve by interacting with the intergalactic medium (IGM). Gas accretes onto galaxies from the outside, chemical enrichment proceeds as stars form, and gas and metals are ejected from galaxies by outflow (cite: bouche10; dave11_1; lilly13; pengmaiolino14; tacchella20). Gas mass fraction and gas-phase metallicity are often used to investigate the relative contributions between star formation, gas outflow, and inflow (cite: erb08_apj674; cresci10; troncoso14; yabe15_apj; seko16; sanders20). Given that galaxies are more actively forming stars at higher redshifts, they are expected to be more actively interacting with the surrounding IGM via outflows and inflows (cite: yabe15_apj). At $z>3$, it has been suggested that star-forming galaxies are no longer in equilibrium (cite: mannucci10), where the gas consumption due to star formation and outflows is balanced with the gas acquisition by inflows (inflow $=$ star formation $+$ outflow), due to the intense gas inflows onto galaxies in the early Universe. Estimating both the gas mass and gas-phase metallicity for star-forming galaxies at $z>3$ allows tests of whether galaxies at $z>3$ are out of equilibrium or not.

Several methods are commonly used to estimate gas masses. The first one is using CO emission line fluxes (cite: daddi10; genzel10; tacconi10; tacconi13). This method has uncertainties on the CO-to-$\rm H_{2}$ conversion factor, which changes depending on metallicity (cite: genzel12) and on the CO excitation states when using higher-$J$ CO lines (cite: daddi15; riechers20). Furthermore, observations of CO lines for galaxies at high redshifts are observationally expensive. The second one is converting a dust mass to a gas mass with an assumed gas-to-dust mass ratio (cite: santini14; bethermin15). Because the gas-to-dust mass ratio depends on the metallicity (cite: leroy11; remy-ruyer14), metallicity measurements are crucial to estimate the gas mass accurately. Gas masses can also be estimated with an empirically calibrated relation between a single-band dust continuum flux at the Rayleigh-Jeans (R-J) tail and gas mass (cite: scoville14; scoville16; groves15). These scaling relations are calibrated with local galaxies or with local galaxies and SMGs up to $z\sim2$. In this method, the gas-to-dust mass ratio is included in the conversion factor, and thus, is not needed to be considered. It remains unclear whether the empirical calibration methods are applicable to galaxies at $z>3$ or how much scatter there is in the relationships. Given that dust continuum observations take much less time as compared to the CO observations, using dust continuum as a tracer of gas has an advantage to increase the number of galaxies at higher redshifts with individual gas estimates, but these will only be reliable when precise metallicities are also available.

In this paper, we present the results from sub-millimeter observations with the Atacama Large Millimeter/sub-millimeter Array (ALMA) of star-forming galaxies at $z=$ 3–4. High quality near-infrared (NIR) spectra obtained with Keck/MOSFIRE (cite: mclean10; mclean12) are available for all of the targets and their gas-phase metallicities are already measured (cite: onodera16; suzuki17). By observing the dust continuum emission, we can estimate their dust masses and convert them to gas masses using the relation between the metallicity and gas-to-dust mass ratio. We then investigate the gas properties, namely, gas mass fractions and gas depletion timescales, of star-forming galaxies at $z=$ 3–4. Comparing the gas contents with the gas-phase metallicities, we aim to understand how star-forming galaxies at this epoch interact with their surrounding IGM via gas inflows and outflows.

This paper is organized as follows. In Section [2](#sec:obs), we introduce our parent sample of star-forming galaxies at $z=$ 3–4 and describe the observations conducted with ALMA. We also describe the reduction and analysis for the obtained data and stacking analysis. In Section [3](#sec:physicalquantity), we present our estimates of the physical quantities, such as gas-phase metallicity, ionization parameter, and gas mass. In Section [4](#sec:results), we show our results on the dust and gas properties of the star-forming galaxies at $z=$ 3–4 and discuss their metallicity dependencies. We also compare our observational results with a gas regulator model to discuss how star-forming galaxies at this epoch interact with their surrounding IGM. We summarize this paper in Section [5](#sec:summary).

Throughout of this paper, we assume the cosmological parameters of $\rm \Omega_m = 0.3$, $\rm \Omega_{\Lambda} = 0.7$, and $H_{\rm 0} = 70\ {\rm km\ s^{-1}\ Mpc^{-1}}$. We use a Chabrier initial mass function (IMF; (cite: chabrier03)).

# Observation and reduction

## Spectroscopically confirmed galaxies at $z=$3–4

Our parent sample is constructed from the two different studies of star-forming galaxies at $3 < z < 4$ in the COSMOS field using NIR spectroscopy with Keck/MOSFIRE. One study is based on a spectroscopic and photometric redshift selection (cite: onodera16), while the other study is based on narrow-band selection (cite: suzuki17). The parent sample from both studies consists of 53 galaxies with $z_{\rm spec}\sim$ 3.0–3.8.

### UV-selected galaxies

In (cite: onodera16), targets for spectroscopic observation were originally selected from the zCOSMOS-Deep redshift catalog (cite: lilly07) and the 30-band COSMOS photometric redshift catalog (cite: mccracken12; ilbert13). conducted *H*- and *K*-band spectroscopy and confirmed 43 galaxies at $z_{\rm spec}=$ 3.0–3.8 based on the rest-frame optical emission lines. The confirmed star-forming galaxies span a stellar mass range of $\rm log(M_*/M_\odot) \sim$ 8.5–11.0 and distribute around the star-forming main sequence at $z\sim$ 3.3 .

### \[OIII\] emission line galaxies

In (cite: suzuki17), targets for spectroscopic observation were selected from a catalog of narrow-band(NB)-selected \[Oiii\]$\lambda$5007 emission line galaxies at $z=3.23$, obtained by the High-Z Emission Line Survey (HiZELS; (cite: best13; sobral13; khostovan15)). conducted *H*- and *K*-band spectroscopy and confirmed ten \[Oiii\] emitters at $z_{\rm spec}=$ 3.23–3.28. The \[Oiii\] emitters follow the star-forming main sequence at $z\sim3.2$ and the mass–metallicity relation established by .

## ALMA Band-6 observation

We selected galaxies with $\rm log(M_*/M_\odot) \ge 10$ and $\ge 3\sigma$ detection of \[Oiii\]$\lambda$5007, H$\beta$, or \[Oii\]$\lambda$3727 emission lines from the parent sample as targets for the ALMA observations. We excluded two galaxies classified as the active galactic nuclei (AGNs) in . One has an X-ray counterpart detected with *Chandra*. The other shows strong \[Neiii\]$\lambda$3869 emission and a high \[Oiii\]$\lambda$4363/H$\gamma$ ratio, which is likely to be powered by the AGN . As a result, the sample for the ALMA observations consists of 12 galaxies, two of which are \[Oiii\] emitters from (Table [\[table:obssummary\]](#table:obssummary)).

Although the potential AGNs were excluded from our ALMA targets, we found that one of the ALMA targets, 192129, is detected in X-ray with *Chandra* (cite: elvis09; civano12; civano16) and included in the X-ray-selected AGN catalog of (cite: kalfountzou14) as a type-2 AGN. The optical–NIR spectral energy distribution (SED) of this source is not peculiar as compared to the other galaxies and its H$\beta$ emission line is narrow, which is likely to be consistent with the classification by (cite: kalfountzou14). Although we expect that the optical–NIR emission is dominated by emission from the host galaxy, the physical quantities, such as stellar mass, SFR, gas-phase metallicity, and ionization parameter (Section [2.4](#subsec:magphys) and [3.1](#subsec:ism)), may be affected by the emission from the AGN. On the other hand, the dust continuum observed at ALMA Band-6 ($\lambda_{\rm rest}\sim280\ \mu {\rm m}$) is expected to be dominated by cold dust emission from star-forming regions ($T\sim$ 20–40 K). We do not exclude this source in the following analyses but distinguish it from the other sources on each figure.

Our ALMA Cycle 6 program with Band-6 was conducted during December 2018 – March 2019 (2018.1.00681.S, PI: T. Suzuki).

Frequencies of four spectral windows are slightly different among the targets depending on their spectroscopic redshifts (between $221.9$ GHz and $254.4$ GHz). We set the frequencies of the spectral windows so that we can cover the CO(9–8) line ($\nu_{\rm rest} = 1036.9$ GHz) with one of the four spectral windows. The effective bandwidth of each spectral window is $~1.875$ GHz. The data were taken with the Time Domain Mode (TDM). The total on-source time is $\sim$5–90 min depending on the stellar mass, SFR, and gas-phase metallicity of the targets as summarized in Table [\[table:obssummary\]](#table:obssummary).

The brightest source at 1.3 mm, 208681, appears to be detected with the CO(9–8) line. We will discuss the CO(9–8) line of this source in a forthcoming paper (Suzuki et al. 2020 in preparation). the contribution of the CO(9–8) line to the dust continuum flux is negligible.

We used the Common Astronomy Software Application package (casa; (cite: CASA)) to calibrate the raw data. We run the clean algorithm with natural weighting. When there are sources detected with $\ge 5\sigma$ level, we run clean again by masking the sources.

Figure [1](#fig:image) shows the ALMA maps of our target galaxies together with the *Ks*-band centroids.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID$^{\rm a}$ | R.A.$^{\rm a}$ | DEC.$^{\rm a}$ | $z_{\rm spec}$ | Exp. time$^{\rm b}$ | Central freq.$^{\rm c}$ | RMS level$^{\rm d}$ | $S_{\rm 1.3mm}$ $^{\rm e}$ | Reference |
|  | \[deg\] | \[deg\] |  | \[min\] | \[GHz\] | \[mJy $\rm beam^{-1}$\] | \[mJy\] |  |
| 208681 | 149.90551 | 2.353990 | 3.267 | 5 | 232.1 | 0.05 | $1.02\pm0.05$ |  |
| 214339 | 150.31607 | 2.372240 | 3.609 | 5 | 233.0 | 0.05 | $0.30 \pm 0.05$ | $''$ |
| 406444 | 150.33032 | 2.072270 | 3.304 | 5 | 232.1 | 0.04 | $0.12\pm0.04$ | $''$ |
| 3 | 149.97513 | 1.69375 | 3.230 | 41 | 235.6 | 0.01 | $0.11\pm0.01$ |  |
| 434585 | 149.84702 | 2.373020 | 3.363 | 11 | 230.9 | 0.03 | $0.11 \pm 0.03$ |  |
| $192129^{\rm f}$ | 150.30078 | 2.300540 | 3.495 | 49 | 237.3 | 0.01 | $0.05 \pm 0.01$ | $''$ |
| 217753 | 149.89451 | 2.383700 | 3.254 | 5 | 232.1 | 0.05 | $< 0.15$ | $''$ |
| 218783 | 149.92082 | 2.387060 | 3.297 | 5 | 232.1 | 0.04 | $< 0.11$ | $''$ |
| 212298 | 150.34268 | 2.365390 | 3.108 | 5 | 246.2 | 0.04 | $< 0.11$ | $''$ |
| 413391 | 149.78424 | 2.452890 | 3.365 | 11 | 230.9 | 0.03 | $< 0.10$ | $''$ |
| 5 | 149.95568 | 1.68044 | 3.241 | 53 | 235.6 | 0.01 | $< 0.04$ |  |
| 434618 | 149.89213 | 2.414710 | 3.285 | 88 | 233.5 | 0.01 | $< 0.03$ |  |

![](figure1.pdf)

## Stacking analysis

We stacked the Band-6 images of the ALMA non-detected sources to investigate their average dust continuum flux. As a result of SED fitting in Section [2.4](#subsec:magphys),

one source, 434618, turns out to be only $\rm log(M_*/M_\odot)=9.39_{-0.01}^{+0.12}$. Because the stellar mass of 434618 is $\gtrsim 0.6$ dex smaller than those of the other non-detected sources, we excluded this source so that we can investigate the average dust and gas properties of star-forming galaxies with similar stellar masses of $\rm log(M_{*}/M_\odot)=$ 10.0–10.4.

We cut out the tapered $20''\times20''$ ALMA images centered on the *Ks*-band position. Then, we stacked the cutout images by weighting with the RMS levels in the tapered maps (Table [\[table:obssummary\]](#table:obssummary)). The stacked image is shown in Figure [1](#fig:image).

## SED fitting

We conducted SED fitting including the dust continuum flux or limit at $1.3$ mm obtained with ALMA. We used the SED fitting code magphys (cite: dacunha08; dacunha15; battisti19), which can fit the SEDs from the optical to radio wavelengths consistently. magphys combines the emission by stellar populations with the attenuation and emission by dust in galaxies based on the energy balance technique. We used the updated version of magphys for galaxies at high redshifts (cite: dacunha15).

magphys adopts stellar population synthesis models of (cite: bc03) with the (cite: chabrier03) IMF. The metallicity range is set to be from 0.2 to 2 times solar. Star formation history is parameterized as a continuous delayed exponential function i.e., the star formation rate rises at the earlier epoch and then declines exponentially with a certain timescale between 0.075 and 1.5 $\rm Gyr^{-1}$. The age is randomly drawn between 0.1 and 10 Gyrs. magphys also includes star bursts of random duration and amplitude to account for the stochasticity on star formation history. The current SFR is determined by averaging SFH over last . As for the dust attenuation, magphys uses the two-component model of (cite: charlotfall00). A number of tests of the application of magphys to dust-obscured galaxies, including simulated galaxies from EAGLE, are discussed in (cite: dudzeviciute20).

magphys takes into account four main dust components, namely, a polycyclic aromatic hydrocarbons, hot dust at mid-infrared, warm dust, and cold dust in the thermal equilibrium. The warm and cold dust components in the thermal equilibrium emit as modified black bodies with emissivity index $\beta$ of 1.5 for the warm components and 2 for the cold components (cite: dacunha15). magphys assumes a dust mass absorption coefficient at $850\mu$m of $\kappa_{\rm abs}=0.77\ {\rm g^{-1}\ cm^2}$.

We combined the flux densities at $1.3$ mm from ALMA with the optical-NIR broad-band photometries ($u,B, V, r, i_p, z_{pp}, Y, J, H, Ks$, 3.6, 4.5, 5.8, and 8.0 $\mu$m) from the COSMOS2015 catalog (cite: cosmos2015). Because magphys does not include emission lines from the ionized gas, we subtracted the emission line fluxes measured with the NIR spectra from the *H*-band (\[Oii\]) and *Ks*-band (\[Oiii\] doublet, H$\beta$) fluxes. We took into account the upper limits for the optical-NIR photometries by giving 0 to the flux column and a $3\sigma$ value to the photometric error column according to (cite: dacunha15). As for the 1.3 mm flux of the ALMA non-detected sources, we gave a $1.5\sigma \pm 1\sigma$ value as done in (cite: dudzeviciute20). Using a $1.5\sigma \pm 1\sigma$ value provides a better weighting of the sub-millimeter constraint in the best-fit model returned by magphys than using a $3\sigma$ upper limit.

We also conducted SED fitting for the stacked sample with the obtained $1.3$ mm flux in Section [2.3](#subsec:stack). When taking an average of the optical–NIR photometries, we used the same weights as used in the ALMA image stacking (Section [2.3](#subsec:stack)).

The best-fit SEDs of the individual galaxies and the stacked sample are shown in Appendix [6](#sec:appendix1). We use the median values of the probability distribution function (PDF) for stellar mass, SFR, and dust mass in the following analyses. These physical quantities are summarized in Table [\[tab:basicquantity\]](#tab:basicquantity). The uncertainties correspond to the 16–84th percentile values of the PDF. As for the dust masses of the ALMA non-detected sources, we use the 97.5th percentile values of the PDF as the upper limits.

In order to evaluate whether the upper limits on the dust masses are reasonable, we estimated dust mass upper limits with a different method. We calculated a ratio between the dust mass and the luminosity density at $997.6$ GHz in the rest-frame, ${\rm M_{dust}}/L_{\rm 997.6~GHz}$, for each detected source. We then converted the $3\sigma$ upper limits of 1.3 mm fluxes to the dust mass upper limits with the median ${\rm M_{dust}}/L_{\rm 997.6~GHz}$ ratio. The difference of the rest-frame frequencies among the sources is corrected for assuming $L_{\nu} \propto \lambda^{-3.7}$. The estimated dust mass upper limits are similar as the 97.5th percentile values of the PDF from magphys.

One of the uncertainties on the dust mass is the assumed dust mass absorption coefficient, $\kappa_{\rm abs}$. It is reported that dust masses obtained with magphys are lower by a factor of two as compared to those estimated based on the (cite: draineli07) models, which assume the smaller dust mass absorption coefficient of $\kappa_{\rm abs}=0.38\ {\rm g^{-1}\ cm^2}$ (cite: hunt19).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | $\rm log(M_*/M_\odot)^{a}$ | $\rm log(SFR)^{a}$ | $\rm 12+log(O/H)^{\rm b}$ | log($q$) | $\delta_{\rm GDR}$ | $\rm log(M_{\rm dust}/M_\odot)^{a,c}$ | $\rm log(M_{gas}/M_\odot)$ |
|  |  | \[$\rm M_\odot\ yr^{-1}$\] |  | \[$\rm cm\ s^{-1}$\] |  |  |  |
| 208681 | $10.82_{-0.03}^{+0.00}$ | $2.10_{-0.01}^{+0.08}$ | $8.59_{-0.05}^{+0.04}$ | $7.64\pm0.03$ | $126_{-14}^{+13}$ | $8.89_{-0.08}^{+0.11}$ | $11.29_{-0.09}^{+0.11}$ |
| 214339 | $10.48_{-0.05}^{+0.04}$ | $1.76\pm0.13$ | $8.30_{-0.12}^{+0.09}$ | $7.82_{-0.06}^{+0.05}$ | $264_{-70}^{+54}$ | $8.22_{-0.16}^{+0.17}$ | $10.94_{-0.20}^{+0.19}$ |
| 406444 | $10.87_{-0.01}^{+0.08}$ | $2.31_{-0.11}^{+0.08}$ | $8.39_{-0.09}^{+0.08}$ | $7.77_{-0.09}^{+0.08}$ | $211_{-49}^{+40}$ | $7.64_{-0.13}^{+0.12}$ | $10.26_{-0.17}^{+0.15}$ |
| 3 | $10.43_{-0.08}^{+0.06}$ | $1.73_{-0.15}^{+0.18}$ | $8.40_{-0.06}^{+0.05}$ | $7.69\pm0.06$ | $205_{-29}^{+26}$ | $7.71_{-0.13}^{+0.15}$ | $10.32_{-0.14}^{+0.16}$ |
| 434585 | $10.13_{-0.12}^{+0.04}$ | $1.73_{-0.01}^{+0.17}$ | $8.47_{-0.14}^{+0.10}$ | $7.69\pm0.25$ | $172_{-64}^{+46}$ | $7.67_{-0.22}^{+0.20}$ | $10.21_{-0.28}^{+0.23}$ |
| 192129 | $10.45_{-0.00}^{+0.12}$ | $1.35_{-0.08}^{+0.00}$ | $8.41_{-0.08}^{+0.07}$ | $7.83_{-0.04}^{+0.03}$ | $199_{-41}^{+33}$ | $7.40_{-0.28}^{+0.18}$ | $10.00_{-0.29}^{+0.19}$ |
| 217753 | $10.39_{-0.06}^{+0.05}$ | $1.67_{-0.18}^{+0.12}$ | $8.57_{-0.05}^{+0.04}$ | $7.55\pm0.06$ | $131_{-17}^{+15}$ | $< 8.00$ | $< 10.42$ |
| 218783 | $10.12_{-0.07}^{+0.08}$ | $1.70_{-0.17}^{+0.16}$ | $8.42_{-0.07}^{+0.06}$ | $7.67\pm0.03$ | $197_{-35}^{+30}$ | $< 7.84$ | $< 10.43$ |
| 212298 | $10.38_{-0.08}^{+0.14}$ | $1.74_{-0.20}^{+0.26}$ | $8.39_{-0.08}^{+0.07}$ | $7.76_{-0.04}^{+0.03}$ | $213_{-43}^{+35}$ | $< 7.84$ | $< 10.47$ |
| 413391 | $10.08_{-0.01}^{+0.00}$ | $1.88\pm0.00$ | $8.33_{-0.10}^{+0.08}$ | $7.69_{-0.07}^{+0.06}$ | $246_{-56}^{+47}$ | $< 7.73$ | $< 10.42$ |
| 5 | $10.14_{-0.05}^{+0.09}$ | $1.37\pm0.15$ | $8.37\pm0.05$ | $7.59\pm0.07$ | $220_{-27}^{+25}$ | $< 7.33$ | $< 9.97$ |
| 434618 | $9.39_{-0.01}^{+0.12}$ | $1.18_{-0.09}^{+0.00}$ | $8.26_{-0.09}^{+0.08}$ | $7.78_{-0.04}^{+0.03}$ | $284_{-58}^{+49}$ | $< 7.28$ | $< 10.04$ |
| stack$^{\rm d}$ | $10.18_{-0.06}^{+0.05}$ | $1.52_{-0.14}^{+0.15}$ | $8.38\pm0.05$ | $7.62\pm0.06$ | $216\pm27$ | $7.33_{-0.15}^{+0.17}$ | $9.97_{-0.16}^{+0.18}$ |

# Analysis

## Gas-phase metallicity and ionization parameter

We recalculated the gas-phase metallicities The emission line fluxes of the sources are available in and .

We also estimated the ionization parameter, ${\rm log}(q)$, for the galaxies observed with ALMA as done in . The ionization parameter is described as the ratio of the number of the ionizing photons and the hydrogen atoms to be ionized. The definition of $q$ is as follows:

$$\begin{equation}
q = \frac{Q_{\rm H^0}}{4\pi R_s^2n_{\rm n_H}}, 
\end{equation}$$

where $Q_{\rm H^0}$ is the flux of the ionizing photons produced by the existing stars above the Lyman limit, $R_s$ is the Strömgren radius, and $n_{\rm H}$ is the local density of hydrogen atoms (cite: kewleydopita02).

We use the following relation by (cite: KK04) to estimate the ionization parameter from the \[Oiii\]$\lambda\lambda$4959,5007/\[Oii\] ratio ($O_{\rm 32}$) and gas-phase metallicity;

$$\begin{eqnarray}
    {\rm log}(q) = &\{&32.81 - 1.153y^2 + [{\rm 12+log(O/H)}] \nonumber \\ \nonumber
    &\times& (-3.396-0.025y+0.1444y^2)\} \\ \nonumber
    &\times& \{4.63-0.3119y-0.163y^2 + [{\rm 12+log(O/H)}] \\ 
    &\times& (-0.48 + 0.0271y+0.02037y^2)\}^{-1}, 
\end{eqnarray}$$

where $y={\rm log}\ O_{\rm 32}$.

## $M_*$ – SFR and $M_*$ – gas-phase metallicity diagram

Figure [2](#fig:msmz) shows the star-forming main sequence and the mass–metallicity relation for the star-forming galaxies at $z\sim3.3$. In the left panel, we also show star-forming galaxies and SMGs at $z=$ 3–4 from the literature, which are introduced in Section [3.4](#subsec:comparisonsample). Our targets distribute around the star-forming main sequence and the mass-metallicity relation, and thus, are not biased in terms of the star-forming activity and gas-phase metallicity. The stacked sample is also close to the star-forming main sequence and the mass–metallicity relation, indicating that the stacked sample has a typical SFR and gas-phase metallicity for its stellar mass.

![](figure2a.pdf)

![](figure2b.pdf)

## Gas mass

We converted the dust masses from magphys to gas masses with the relation between the gas-phase metallicity and gas-to-dust mass ratio. We use the relation shown in (cite: magdis12) as follows:

$$\begin{equation}
    {\rm log}(\delta_{\rm gdr}) = (10.54 \pm 1.0) - (0.99 \pm 0.12) \times (\rm 12+log(O/H)), 
\end{equation}$$

which is based on the relation of (cite: leroy11) and uses the metallicity estimated with the \[Nii\]/H$\alpha$ ratio of (cite: PP04). Note that the dust mass estimation in (cite: leroy11) and (cite: magdis12) is based on the (cite: draineli07) models. The scatter of this relation is $0.15$ dex (cite: magdis12).

We need to convert the gas-phase metallicity in Table [\[tab:basicquantity\]](#tab:basicquantity) to that based on the (cite: PP04) calibration. We estimated \[Nii\]/H$\alpha$ ratios using the relation between $\rm 12+log(O/H)$ and \[Nii\]/H$\alpha$ of (cite: curti16), and then, converted the estimated \[Nii\]/H$\alpha$ ratios to the gas-phase metallicities using the (cite: PP04) calibration.

Then, we estimated gas masses as follows:

$$\begin{equation}
   {\rm M_{\rm gas}} = {\rm M_{\rm dust}} \times \delta_{\rm gdr},
   \label{eq.dusttogas}
\end{equation}$$

where $\rm M_{\rm gas}$ includes both molecular and atomic hydrogen. We multiply our dust masses by a factor of two when converting them to gas masses with Eq. ([\[eq.dusttogas\]](#eq.dusttogas)) to correct for the systematic difference of the dust mass estimation between magphys and (cite: draineli07) models (Section [2.4](#subsec:magphys)). The estimated gas masses and limits of the individual sources and the stacked sample are summarized in Table [\[tab:basicquantity\]](#tab:basicquantity).

Given $\sim 0.30$ dex uncertainty coming from the assumed $\kappa_{\rm abs}$ (cite: hunt19), and $\sim0.15$ dex scatter of the relation between the gas-phase metallicity and gas-to-dust mass ratio (cite: magdis12), the systematic uncertainty of our gas mass estimate is roughly .

## Comparison sample from the literature

We next introduce samples from the literature to which we compare our data in Section [4](#sec:results). Since different works use different approaches to estimate dust and/or gas masses, these comparisons must be interpreted with care. Please refer to the papers cited below for more details about the samples selection, observations, and methods used to estimate dust and/or gas masses.

- (cite: magdis17) investigated the dust and gas masses of two massive Lyman Break Galaxies (LBGs) at $z\sim3$. The dust masses are estimated with the (cite: draineli07) models. They used several independent methods to estimate the gas masses, namely, CO(3–2) line, dust mass from the IR SED, and the empirical relation of (cite: groves15).

- (cite: wiklind19) targeted star-forming galaxies at $z\sim3$. They used the empirical relation of (cite: scoville16) to estimate molecular gas masses. We show 11 galaxies with the individual molecular gas estimates.

- ASPECS: We extract two galaxies at $z\sim3.6$ from the ASPECS $1.2$ mm continuum source catalog (cite: aravena20). The dust masses are estimated from SED fitting with magphys. We use the gas masses estimated with the dust mass and the fixed gas-to-dust mass ratio of 200 in their catalog.

- (cite: cassata20) observed CO emission lines for massive LBGs at $z\sim$ 3–4. They used the CO(5–4) emission lines to estimate molecular gas masses.

- AS2UDS is an ALMA survey targeting 700 SMGs (cite: dudzeviciute20). Here we show the AS2UDS galaxies at $z=$ 3–4. (cite: dudzeviciute20) estimated the dust masses of the AS2UDS galaxies from the SED fitting with magphys. They converted the dust mass to the gas mass assuming the fixed gas-to-dust mass ratio of 100.

- (cite: tan14) investigated the dust masses of three SMGs at $z=4.05$ with the multi-band photometry in the IR regime. They used the (cite: draineli07) dust models to estimate the dust masses.

We also introduce the following galaxy samples at lower redshifts, which have individual measurements of gas mass and gas-phase metallicity.

- (cite: saintonge13) investigated the dust and molecular gas masses of 17 gravitationally lensed star-forming galaxies at $z\sim$ 1.4–3. They used the (cite: draineli07) models to estimate dust masses. Molecular gas masses are estimated from the CO(3–2) lines. We show four galaxies at $z\sim$ 2–3 in Section [4.1](#subsec:msmdust) and [4.4](#subsec:fgas_OH_comparison).

- (cite: seko16_alma) investigated the dust and molecular gas masses of star-forming galaxies at $z\sim1.4$. They converted the dust continuum flux to a dust mass assuming modified black body with fixed $T_{\rm dust}=30$ K and $\beta=1.5$. They used the CO(5–4) line to estimate the molecular gas masses.

- xCOLD-GASS is a CO(1–0) line survey for local SDSS galaxies. We use the public catalog in (cite: saintonge17) and combine it with the catalog of the xGASS project (cite: catinella18) to estimate the total gas masses. .

- ALLSMOG is a CO(2–1) line survey for local SDSS galaxies (cite: bothwell14). Most of the ALLSMOG galaxies have the measurements of the atomic hydrogen gas by different studies (please see (cite: cicone17) for more details). .

# Results and Discussion

## Dust mass and its metallicity dependence

![](figure3a.pdf)

![](figure3b.pdf)

The dust masses of the star-forming galaxies at $z\sim3.3$ are estimated to be $\rm log(M_{dust}/M_\odot)\sim$ 7.4–8.9 (Table [\[tab:basicquantity\]](#tab:basicquantity)). The dust mass of the stacked sample is $\rm log(M_{dust}/M_\odot)=7.33^{+0.17}_{-0.15}$. The left panel of Figure [3](#fig:ms-mdust) shows the comparison of dust masses between the star-forming galaxies at $z\sim3.3$ and the galaxies at $z\sim$  in the literature (Section [3.4](#subsec:comparisonsample)). As mentioned in Section [3.4](#subsec:comparisonsample), (cite: tan14), (cite: magdis17), and estimated dust masses with the (cite: draineli07) models. To correct for the systematic difference of the dust mass estimate between magphys and (cite: draineli07) models, the dust masses of the galaxies in these studies are divided by a factor of two in the left panel of Figure [3](#fig:ms-mdust).

The right panel of Figure [3](#fig:ms-mdust) shows the relation between the gas-phase metallicity and dust-to-stellar mass ratio for the star-forming galaxies at $z\sim3.3$. Given that dust is produced from metals, we would expect galaxies with higher metallicities to have larger dust masses at a given stellar mass. We find no statistically significant trend between the dust-to-stellar mass ratio and gas-phase metallicity .

The brightest source at 1.3 mm among our sample, 208681 (Table [\[table:obssummary\]](#table:obssummary) and Figure [3](#fig:ms-mdust)), has a dust mass of $\rm log(M_{dust}/M_\odot)=8.89_{-0.08}^{+0.11}$, which is comparable to those of SMGs at $z\sim$ 3–4 (cite: tan14; dudzeviciute20). This source can be classified as a SMG in terms of its dust content. The other five galaxies and the stacked sample have $\sim1$ dex lower dust masses than the SMGs at $z\sim$ 3–4 with similar stellar masses. This brightest source, 208681, is also the most metal-rich galaxy with $\rm 12+log(O/H)=8.59_{-0.05}^{+0.04}$ among our sample

The star-forming galaxies at $z\sim$ 3–4 except for the SMGs show a positive correlation between the stellar mass and dust mass. The dust-to-stellar mass ratio takes value roughly between $1\times10^{-3}$ and $5\times 10^{-3}$ (median value is $2\times10^{-3}$) in the stellar mass range of $\rm log(M_*/M_\odot)\sim$ 10.1–11.4.

When comparing with star-forming galaxies at $z\sim1.4$ (cite: seko16_alma) and $z\sim$ 2–3 (cite: saintonge13), star-forming galaxies at lower redshifts have similar dust-to-stellar mass ratios ($1\times10^{-3}$ – $5\times10^{-3}$) as our galaxies at $z\sim3.3$ with similar stellar masses. Although a fair comparison is difficult due to different sample selection among the three studies, the evolution of the dust-to-stellar mass ratios seems to be mild since $z\sim1.4$ to 3.3 as shown in (cite: bethermin15).

## Gas properties of star-forming galaxies at $z$=3–4

![](figure4a.pdf)

![](figure4b.pdf)

Figure [4](#fig:fgas_tdep) shows the gas mass fraction, $f_{\rm gas} = {\rm M_{gas}/(M_{gas}+M_*)}$, and gas depletion timescale, $t_{\rm dep} = {\rm M_{gas}/SFR}$, as a function of stellar mass for the star-forming galaxies at $z\sim3.3$. Our estimated gas mass fractions are 0.20–0.75 and the gas depletion timescales are 0.09–1.55 Gyr. The typical uncertainties of $f_{\rm gas}$ and $t_{\rm dep}$ are $\pm0.09$ and $\pm0.22$ dex, respectively. As for the stacked sample, the gas mass fraction and gas depletion timescale are estimated to be $f_{\rm gas}=0.38_{-0.09}^{+0.10}$ and $t_{\rm dep}=0.28_{-0.14}^{+0.15}$ Gyr, respectively.

We show star-forming galaxies and SMGs at $z\sim$ 3–4 from the literature (Section [3.4](#subsec:comparisonsample)) in Figure [4](#fig:fgas_tdep). The solid line in each panel represents the scaling relation for galaxies on the star-forming main sequence at $z\sim3.3$ from (cite: tacconi18). The dashed lines correspond to the case when galaxies are at $\pm 0.3$ dex from the star-forming main sequence. Our sample including the stacking result reaches down to $f_{\rm gas}\sim$ 0.2–0.3, which is lower by a factor of $\gtrsim2$ than the scaling relation. We also find a scatter of $\gtrsim1$ dex for the gas depletion timescale at a fixed stellar mass. Such a large scatter of the gas properties is also seen in the samples of (cite: wiklind19) and (cite: dudzeviciute20).

It has been reported that the gas mass fraction and depletion timescale of the main sequence galaxies gradually change depending on the deviation from the star-forming main sequence ($\Delta_{\rm MS}$; e.g., (cite: saintonge12; sargent14; tacconi18)). We checked how the offset of the gas mass fraction or depletion timescale from the scaling relation for galaxies on the main sequence changes depending on $\rm \Delta_{MS}$. We find a trend consistent with (cite: tacconi18) when combining our sample with the samples of the literature (cite: magdis17; wiklind19; cassata20; aravena20). However, at a fixed $\Delta_{\rm MS}$, our sample shows a large scatter of the gas mass fraction and depletion timescale. The observed scatter of the gas mass fraction and depletion timescale in our sample cannot be explained by $\Delta_{\rm MS}$ alone. These results suggest that the fundamental gas properties of galaxies have a large diversity even when they have similar stellar masses and SFRs (cite: elbaz18). Given that the scaling relations are possibly biased toward dusty and gas-rich galaxies especially at higher redshifts, the scaling relations may not be representative of the majority of the galaxy populations at $z\sim$ 3–4.

## Gas mass fraction versus physical conditions of the ionized gas

![](figure5.pdf)

We note that the gas mass fraction and gas-phase metallicity (and also ionization parameter) are not independent

Given that the abundance of oxygen with respect to hydrogen changes depending on the amount of the hydrogen gas in galaxies, the gas-phase metallicity, 12+log(O/H), would be expected to decrease as the gas mass fraction increases (cite: bothwell13; zahid_apj791; bothwell16_aa; seko16_alma). However, we find no statistically significant correlation between the gas mass fraction and gas-phase metallicity for the star-forming galaxies at $z\sim3.3$, which is the same as the result obtained from the comparison between the gas-phase metallicity and dust-to-stellar mass ratio (Figure [3](#fig:ms-mdust)).

We find no clear correlation between the gas mass fraction and ionization parameter as well. According to (cite: kashino19), the gas mass fraction and ionization parameter are related indirectly via three parameters, namely, specific SFR (sSFR), gas-phase metallicity, and electron density. When the gas-phase metallicity increases or sSFR decreases, both the gas mass fraction and ionization parameter decreases. When the electron density increases, the gas mass fraction increases but the ionization parameter decreases (cite: kashino19). Because the gas mass fraction and ionization parameter depend on the three parameters in a different way, how the gas mass fraction correlates with the ionization parameter is not straightforward. We would need to fix some of the parameters to investigate the trend between the two quantities.

A lack of a clear correlation between gas mass fractions and the physical conditions of the ionized gas may reflect stochastic star-formation histories for star-forming galaxies at high redshifts. Star formation in galaxies at higher redshifts are suggested to be burstier than local galaxies (cite: yicheng16; faucher-giguere18; tacchella20). When the star-forming activity in galaxies changes on a short timescale, it becomes more difficult to identify a global trend between the physical quantities.

Note that our sample size may be too small to find any correlation. We need a larger sample of galaxies covering a wider range of stellar mass to confirm whether the gas mass fraction correlates with gas-phase metallicity and ionization parameter.

## Comparison of galaxies at $z=$ 0–3.3 on the $f_{gas}$ versus 12+log(O/H) diagram

![](figure6.pdf)

Figure [6](#fig:fgas_OH_lowz) shows the star-forming galaxies from $z=0$ to 3.3 (Section [3.4](#subsec:comparisonsample)) on the gas mass fraction versus metallicity diagram.

In the literature (cite: saintonge13; seko16_alma; saintonge17; cicone17), the gas-phase metallicities are estimated with the \[Nii\]/H$\alpha$ ratios. In order to compare with the gas-phase metallicities of our sample, which are estimated based on \[Oiii\], H$\beta$, and \[Oii\] lines (cite: curti16), we convert the given \[Nii\]/H$\alpha$ ratios in the previous studies to the gas-phase metallicities using the empirical relation between $\rm 12+log(O/H)$ and \[Nii\]/H$\alpha$ of (cite: curti16).

The gas mass fraction of the galaxies at $z\sim0$ and $3.3$ is the total (molecular$+$atomic) gas mass fraction to compare with a gas regulator model, in which the atomic and molecular hydrogen are indistinguishable, in the following sections. The gas mass fraction of the galaxies in (cite: seko16_alma) and (cite: saintonge13) is the molecular gas mass fraction. We expect that the comparison in Figure [6](#fig:fgas_OH_lowz) is not significantly affected by the fact that we do not include the atomic gas for the two samples. The fraction of the molecular gas is suggested to increase with increasing redshifts because of the higher surface density of galaxies at higher redshifts (cite: popping15). (cite: popping15) suggest the fraction of the molecular gas in the total gas is $\sim$ 0.6–0.8 at $z\sim$ 1.5–3.0 based on their simulations.

Focusing on the local galaxies in Figure [6](#fig:fgas_OH_lowz), the gas-phase metallicity gradually decreases with increasing gas mass fraction as shown in (cite: bothwell13) and (cite: hunt15). Such a gradual decrease of the gas-phase metallicity with increasing gas mass fraction indicates that we need to cover a wide range of gas mass fraction to identify the correlation between the two quantities.

Whereas the star-forming galaxies at $z\sim1.4$ from (cite: seko16_alma) appear to be located at the gas-rich end of the distribution of the local star-forming galaxies, the galaxies at $z\gtrsim2$ from this study and (cite: saintonge13) show an offset toward the lower gas-phase metallicities ($\sim0.2$ dex) with respect to the distribution of the local galaxies. This result suggests that star-forming galaxies at $z\gtrsim2$ are less chemically enriched than those at $z=0$ and even at $z\sim1.4$ with similar gas mass fractions.

The molecular gas mass is estimated with the CO lines in the literature (Section [3.4](#subsec:comparisonsample)). Although the systematic difference caused by using different methods to estimate gas mass could change the relative distribution of the galaxies in the horizontal direction, it cannot explain the offset of the galaxies at $z\sim3.3$ toward the low gas-phase metallicity with respect to the local galaxies. As for the gas-phase metallicity, (cite: curti16) showed that the offset of gas-phase metallicities calibrated with different line ratios is 0.04 dex on average. The systematic uncertainty caused by using different line ratios to calibrate the metallicity is also unlikely to affect our results.

### Comparison with a gas regulator model

“Equilibrium”, “bathtub” or “gas regulator” models are used to track the evolution of the fundamental physical quantities of galaxies, such as gas mass, SFR, and metallicity, by considering gas inflows, outflows, star formation, and metal production in galaxies (cite: finlator08; bouche10; dave12; Dayal13; lilly13; pengmaiolino14; tacchella20). We compare the observational data at $z=$ 0–3.3 with a gas regulator model by (cite: pengmaiolino14).

(cite: pengmaiolino14) derived the analytic formula to track the evolution of the physical quantities, such as gas mass, SFR, metallicity, and stellar mass. The input parameters of this model are gas inflow rate ($\Phi$), star formation efficiency ($\varepsilon =$ SFR/$\rm M_{gas}$), mass-loading factor ($\lambda=$ outflow rate/SFR), and return mass fraction ($R$). The gas accretion to the galaxy is assumed to scale with the growth rate of the dark matter halo. The dark matter halo growth rate is derived from the cosmological hydrodynamic simulations (cite: faucher-giguere11). The outflow rate is assumed to be proportional to SFR. The return mass fraction takes on values $\sim0.2$ to $\sim0.5$ depending on the IMF. This model assumes that these input parameters are constant with time or change with longer timescales than the equilibrium timescale. The equilibrium timescale is the timescale to reach the equilibrium state, where gas acquisition by inflows balance with gas consumption by star formation and outflows. The equilibrium timescale is expressed as follows:

$$\begin{equation}
    \tau_{\rm eq} = \frac{1}{\varepsilon(1-R+\lambda)}. 
    \label{eq:taueq}
\end{equation}$$

The time evolution of the gas mass fraction and gas-phase metallicity is described as follows:

$$\begin{equation}
    f_{\rm gas}(t) = \frac{1}{1 + \varepsilon (1-R) \left(\frac{t}{1-e^{-\frac{t}{\tau_{\rm eq}}}} - \tau_{\rm eq} \right)}, 
\end{equation}$$

$$\begin{equation}
    Z_{\rm gas}(t) = [Z_0 + y\tau_{\rm eq}\varepsilon(1 - e^{-\frac{t}{\tau_{\rm eq}}})][1-e^{-\frac{t}{\tau_{\rm eq}(1-e^{-t/\tau_{\rm eq}})}}], 
\end{equation}$$

where $Z_0$ is the metallicity of the infalling gas, and $y$ is the average yield per stellar generation.

In Figure [6](#fig:fgas_OH_lowz), we show the model tracks obtained from the gas regulator model of (cite: pengmaiolino14). We assume $R=0.4$ (for the Chabrier IMF; (cite: madau14)) and $y = 1.5 Z_\odot$ (cite: yabe15_apj). The gas depletion timescale ($1/\varepsilon$) is set to be $t_{\rm dep} = 0.8\ {\rm Gyr}$. Note that the normalization of model tracks in Figure [6](#fig:fgas_OH_lowz) does not depend on the absolute value of $t_{\rm dep}$. We assume five different mass-loading factors between $\lambda=$ 0.5 and 2.5 (Figure [6](#fig:fgas_OH_lowz)).

We find that the distribution of the star-forming galaxies at $z\sim3.3$ and those from (cite: saintonge13) can be broadly explained by the model tracks with the high mass-loading factor of $\lambda \sim$ 2.0–2.5 rather than the lower values such as $\lambda \sim$ 0.5 or 1. We need stronger outflow with larger $\lambda$ to achieve the lower gas-phase metallicity for star-forming galaxies at $z\gtrsim2$ than the local ones with similar gas mass fractions. This result may suggest a redshift evolution of the mass-loading factor $\lambda$ from $z=0$ to $3.3$, as we discuss below.

(cite: yabe15_apj) showed the increasing outflow rate normalized by SFR with increasing redshifts up to $z\sim2$ by comparing the observational data (stellar mass, gas mass fraction, and gas-phase metallicity) with a simple chemical evolution model (see also (cite: troncoso14)). Some theoretical studies based on analytic models or numerical simulations showed the redshift evolution of the mass-loading factor (cite: barai15; mitra15; muratov15; hayword17). Observationally, (cite: sugahara17) showed a trend that the star-forming galaxies at higher redshift (up to $z=2$) have larger mass-loading factor at a fixed circular velocity. Our results obtained from the comparison between the observational data and the model tracks support the idea that star-forming galaxies at higher redshifts have larger mass-loading factors, and thus, more massive outflow.

### Equilibrium timescale

We estimate the equilibrium timescales (Eq. ([\[eq:taueq\]](#eq:taueq))) for the star-forming galaxies at $z\sim3.3$ with the gas depletion timescale obtained from the observation and the mass-loading factor inferred from the comparison with the model tracks in Figure [6](#fig:fgas_OH_lowz). The equilibrium timescales of the ALMA-detected sources are estimated to be 0.03–2.21 Gyr (average value: 0.52 Gyr) assuming $R=0.4$ for the Chabrier IMF (cite: madau14).

According to (cite: pengmaiolino14), when the equilibrium timescale is much shorter than the Hubble time, galaxies are expected to be in the equilibrium state, where gas acquisition by inflows and gas consumption by star formation and outflows are balanced. On the other hand, when the equilibrium timescale is comparable to the Hubble time, galaxies are considered to have much larger gas reservoir and to be out of equilibrium.

The average equilibrium timescale of the detected sources is roughly one order of magnitude shorter than the Hubble time at $z=3.3$ ($2.82$ Gyr). However, not all of the galaxies necessarily start forming stars at the beginning of the Universe. Given that the age of galaxies must be smaller than the Hubble time, the equilibrium timescale should probably be compared with the age of the galaxies rather than the Hubble time.

We here use the ratio of $\rm M_*/SFR$, which can be regarded as the minimum age of a galaxy. The star-forming galaxies at $z\sim3.3$ have $\rm M_*/SFR=$ 0.25–1.25 Gyr (average: 0.57 Gyr), which is closer to the equilibrium timescales than the Hubble time. Especially, the galaxies with relatively larger gas mass fractions, $f_{\rm gas}\sim$ 0.6–0.8, in our sample tend to have the equilibrium timescales comparable to the minimum ages. This result may suggest that normal star-forming galaxies at $z\sim3$ with relatively large gas mass fractions have not yet reached the equilibrium state as suggested in (cite: mannucci10).

In the future, it will be of interest to study how our results are affected by relaxing the assumptions about galaxies being in equilibrium and by considering bursty star formation histories (cite: tacchella20).

# Summary

We conducted ALMA Band-6 observations of star-forming galaxies at $z\sim3.3$, which have measurements of their metallicities based on the rest-frame optical spectroscopy. Thus we can directly compare the metallicities with the dust and inferred gas properties from our ALMA observations for star-forming galaxies at $z\sim3.3$. We detected the dust continuum emission individually from six out of 12 galaxies. We stacked the ALMA maps of the five ALMA non-detected sources with $\rm log(M_*/M_\odot)=$ 10.0–10.4 and obtained a $\sim5\sigma$ detection of this sample.

We estimated dust masses from SED fitting with magphys including the $1.3$ mm fluxes from ALMA. We converted the dust mass to the gas mass with a relation between the gas-phase metallicity and gas-to-dust mass ratio. With the estimates of dust mass, gas mass, and the physical conditions of the ionized gas, we conclude the following:

- The median value of the dust-to-stellar mass ratios is $\rm M_{dust}/M_* \sim 3.0 \pm 2.0 \times 10^{-3}$. The dust-to-stellar mass ratio of the stacked sample is $\sim 1.4\pm0.5 \times 10^{-3}$. We find no clear trend between the dust-to-stellar mass ratio and gas-phase metallicity.

- The stacked sample shows $f_{\rm gas}=0.38_{-0.09}^{+0.10}$ and $t_{\rm dep}=0.28_{-0.14}^{+0.15}$ Gyr. The gas mass fractions and gas depletion timescales of the galaxies at $z\sim3.3$ show a wider spread at a fixed stellar mass as compared to the scaling relations of galaxies on the main sequence at $z\sim3.3$. Given that most of our galaxies at $z\sim3.3$ distribute around the star-forming main sequence with $\pm0.3$ dex, the large scatter of the gas mass fraction and depletion timescale may suggest a significant diversity of these fundamental properties within the so-called main sequence.

- We find no clear correlation between the gas mass fraction and the physical conditions of the ionized gas, namely, gas-phase metallicity and ionization parameter, at $z\sim3.3$. We may require a large sample of galaxies covering a wider range of the physical quantities to confirm whether gas mass fractions correlate with the ionized gas conditions or not.

- Comparing star-forming galaxies at different redshifts on the gas mass fraction versus metallicity diagram, we find that the star-forming galaxies at $z\gtrsim2$ show an offset toward lower metallicities as compared to the distribution of local star-forming galaxies, in the sense that star-forming galaxies at $z\gtrsim2$ appear to be more metal-poor than the local galaxies with similar gas mass fractions.

- We find that the distribution of star-forming galaxies at $z\sim3.3$ on the gas mass fraction versus gas-phase metallicity diagram can be broadly explained by models assuming higher mass-loading factors in outflows of $\lambda\sim$ 2.0–2.5 from the gas regulator model of (cite: pengmaiolino14). This result supports the idea that star-forming galaxies at higher redshfits have powerful outflows with higher mass-loading factors.

- Comparing the equilibrium timescales (cite: pengmaiolino14) and the minimum ages of the galaxies ($\rm M_*/SFR$), we find that the equilibrium timescale of the relatively gas-rich galaxies ($f_{\rm gas}\sim$ 0.7) is comparable to their minimum ages, suggesting that they may be out of equilibrium.

It remains unclear whether star-forming galaxies at high redshifts follow the same relation between gas-phase metallicity and gas-to-dust mass ratio as local galaxies ((cite: saintonge13; seko16_alma), but see also (cite: magdis12; shapley20)). Observations of independent gas tracers, such as CO or \[CI\] emission lines, will be required to investigate the relation between the gas-phase metallicity and gas-to-dust mass ratio at $z>3$.

High-resolution integral-field-unit (IFU) observation with *the James Webb Space Telescope (JWST)* will enable us to investigate the metallicity gradients within the individual galaxies and to search for the outflow signatures within them. would be useful to investigate the effects of gas inflows and outflows more directly.

# Acknowledgments

We thank the anonymous referee for careful reading and comments that improved the clarity of this paper. TLS would like to thank Ken-ichi Tadaki and Nao Fukagawa for useful comments. IRS acknowledges support from STFC (ST/T000244/1). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00681.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Some of the data presented herein were obtained at the W. M. Keck Observatory, which is operated as a scientific partnership among the California Institute of Technology, the University of California and the National Aeronautics and Space Administration. The Observatory was made possibility by the generous financial support of the W. M. Keck Foundation. The authors wish to recognize and acknowledge the very significant cultural role and reverence that the summit of Maunakea has always had within the indigenous Hawaiian community. We are most fortune to have the opportunity to conduct observations from this mountain. Data analyses were in part carried out on the open use data analysis computer system at the Astronomy Data Center, ADC, of the National Astronomical Observatory of Japan (NAOJ).

# Facilities

ALMA, Keck:I (MOSFIRE)

# Software

astropy (cite: astropy:2013; astropy:2018), casa (cite: CASA), topcat (cite: topcat)

# magphys best-fit SEDs

Figure [7](#fig:bestfit-SED) shows the best-fit SEDs from magphys for 12 galaxies observed with ALMA. We also show the best-fit SED for the stacked sample including the five ALMA non-detected sources with $\rm log(M_*/M_\odot)=$ 10.0–10.4 (Section [2.3](#subsec:stack)).

![](figure7.pdf)

natexlab

(ref: aravena20) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, arXiv e-prints, arXiv:2006.04284. [`https://arxiv.org/abs/2006.04284`](https://arxiv.org/abs/2006.04284)

(ref: astropy:2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: bpt) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [`10.1086/130766`](http://doi.org/10.1086/130766)

(ref: barai15) Barai, P., Monaco, P., Murante, G., Ragagnin, A., & Viel, M. 2015, MNRAS, 447, 266, doi: [`10.1093/mnras/stu2340`](http://doi.org/10.1093/mnras/stu2340)

(ref: battisti19) Battisti, A. J., da Cunha, E., Grasha, K., et al. 2019, ApJ, 882, 61, doi: [`10.3847/1538-4357/ab345d`](http://doi.org/10.3847/1538-4357/ab345d)

(ref: best13) Best, P., Smail, I., Sobral, D., et al. 2013, in Astrophysics and Space Science Proceedings, Vol. 37, Thirty Years of Astronomical Discovery with UKIRT, ed. A. Adamson, J. Davies, & I. Robson, 235, doi: [`10.1007/978-94-007-7432-2_22`](http://doi.org/10.1007/978-94-007-7432-2_22)

(ref: bethermin15) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113, doi: [`10.1051/0004-6361/201425031`](http://doi.org/10.1051/0004-6361/201425031)

(ref: birkin20) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2020, arXiv e-prints, arXiv:2009.03341. [`https://arxiv.org/abs/2009.03341`](https://arxiv.org/abs/2009.03341)

(ref: bothwell16_aa) Bothwell, M. S., Maiolino, R., Cicone, C., Peng, Y., & Wagg, J. 2016a, A&A, 595, A48, doi: [`10.1051/0004-6361/201527918`](http://doi.org/10.1051/0004-6361/201527918)

(ref: bothwell13) Bothwell, M. S., Maiolino, R., Kennicutt, R., et al. 2013a, MNRAS, 433, 1425, doi: [`10.1093/mnras/stt817`](http://doi.org/10.1093/mnras/stt817)

(ref: bothwell16_mnras) Bothwell, M. S., Maiolino, R., Peng, Y., et al. 2016b, MNRAS, 455, 1156, doi: [`10.1093/mnras/stv2121`](http://doi.org/10.1093/mnras/stv2121)

(ref: bothwell13_mnras429) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013b, MNRAS, 429, 3047, doi: [`10.1093/mnras/sts562`](http://doi.org/10.1093/mnras/sts562)

(ref: bothwell14) Bothwell, M. S., Wagg, J., Cicone, C., et al. 2014, MNRAS, 445, 2599, doi: [`10.1093/mnras/stu1936`](http://doi.org/10.1093/mnras/stu1936)

(ref: bouche10) Bouché, N., Dekel, A., Genzel, R., et al. 2010, ApJ, 718, 1001, doi: [`10.1088/0004-637X/718/2/1001`](http://doi.org/10.1088/0004-637X/718/2/1001)

(ref: brown18) Brown, T., Cortese, L., Catinella, B., & Kilborn, V. 2018, MNRAS, 473, 1868, doi: [`10.1093/mnras/stx2452`](http://doi.org/10.1093/mnras/stx2452)

(ref: bc03) Bruzual, G., & Charlot, S. 2003, MNRAS, 344, 1000, doi: [`10.1046/j.1365-8711.2003.06897.x`](http://doi.org/10.1046/j.1365-8711.2003.06897.x)

(ref: calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: carilliwalter13) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: cassata20) Cassata, P., Liu, D., Groves, B., et al. 2020, ApJ, 891, 83, doi: [`10.3847/1538-4357/ab7452`](http://doi.org/10.3847/1538-4357/ab7452)

(ref: catinella18) Catinella, B., Saintonge, A., Janowiecki, S., et al. 2018, MNRAS, 476, 875, doi: [`10.1093/mnras/sty089`](http://doi.org/10.1093/mnras/sty089)

(ref: chabrier03) Chabrier, G. 2003, PASP, 115, 763, doi: [`10.1086/376392`](http://doi.org/10.1086/376392)

(ref: charlotfall00) Charlot, S., & Fall, S. M. 2000, ApJ, 539, 718, doi: [`10.1086/309250`](http://doi.org/10.1086/309250)

(ref: chen17) Chen, C.-C., Hodge, J. A., Smail, I., et al. 2017, ApJ, 846, 108, doi: [`10.3847/1538-4357/aa863a`](http://doi.org/10.3847/1538-4357/aa863a)

(ref: cicone17) Cicone, C., Bothwell, M., Wagg, J., et al. 2017, A&A, 604, A53, doi: [`10.1051/0004-6361/201730605`](http://doi.org/10.1051/0004-6361/201730605)

(ref: civano12) Civano, F., Elvis, M., Brusa, M., et al. 2012, ApJS, 201, 30, doi: [`10.1088/0067-0049/201/2/30`](http://doi.org/10.1088/0067-0049/201/2/30)

(ref: civano16) Civano, F., Marchesi, S., Comastri, A., et al. 2016, ApJ, 819, 62, doi: [`10.3847/0004-637X/819/1/62`](http://doi.org/10.3847/0004-637X/819/1/62)

(ref: collacchioni20) Collacchioni, F., Lagos, C. D. P., Mitchell, P. D., et al. 2020, MNRAS, 495, 2827, doi: [`10.1093/mnras/staa1334`](http://doi.org/10.1093/mnras/staa1334)

(ref: cresci10) Cresci, G., Mannucci, F., Maiolino, R., et al. 2010, Nature, 467, 811, doi: [`10.1038/nature09451`](http://doi.org/10.1038/nature09451)

(ref: curti16) Curti, M., Cresci, G., Mannucci, F., et al. 2017, MNRAS, 465, 1384, doi: [`10.1093/mnras/stw2766`](http://doi.org/10.1093/mnras/stw2766)

(ref: curti20) Curti, M., Mannucci, F., Cresci, G., & Maiolino, R. 2020, MNRAS, 491, 944, doi: [`10.1093/mnras/stz2910`](http://doi.org/10.1093/mnras/stz2910)

(ref: dacunha08) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595, doi: [`10.1111/j.1365-2966.2008.13535.x`](http://doi.org/10.1111/j.1365-2966.2008.13535.x)

(ref: dacunha15) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110, doi: [`10.1088/0004-637X/806/1/110`](http://doi.org/10.1088/0004-637X/806/1/110)

(ref: daddi10) Daddi, E., Elbaz, D., Walter, F., et al. 2010, ApJL, 714, L118, doi: [`10.1088/2041-8205/714/1/L118`](http://doi.org/10.1088/2041-8205/714/1/L118)

(ref: daddi15) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46, doi: [`10.1051/0004-6361/201425043`](http://doi.org/10.1051/0004-6361/201425043)

(ref: dave12) Davé, R., Finlator, K., & Oppenheimer, B. D. 2012, MNRAS, 421, 98, doi: [`10.1111/j.1365-2966.2011.20148.x`](http://doi.org/10.1111/j.1365-2966.2011.20148.x)

(ref: dave11_1) Davé, R., Oppenheimer, B. D., & Finlator, K. 2011, MNRAS, 415, 11, doi: [`10.1111/j.1365-2966.2011.18680.x`](http://doi.org/10.1111/j.1365-2966.2011.18680.x)

(ref: davies19) Davies, R. L., Förster Schreiber, N. M., Übler, H., et al. 2019, ApJ, 873, 122, doi: [`10.3847/1538-4357/ab06f1`](http://doi.org/10.3847/1538-4357/ab06f1)

(ref: Dayal13) Dayal, P., Ferrara, A., & Dunlop, J. S. 2013, MNRAS, 430, 2891, doi: [`10.1093/mnras/stt083`](http://doi.org/10.1093/mnras/stt083)

(ref: draineli07) Draine, B. T., & Li, A. 2007, ApJ, 657, 810, doi: [`10.1086/511055`](http://doi.org/10.1086/511055)

(ref: dudzeviciute20) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828, doi: [`10.1093/mnras/staa769`](http://doi.org/10.1093/mnras/staa769)

(ref: elbaz18) Elbaz, D., Leiton, R., Nagar, N., et al. 2018, A&A, 616, A110, doi: [`10.1051/0004-6361/201732370`](http://doi.org/10.1051/0004-6361/201732370)

(ref: elvis09) Elvis, M., Civano, F., Vignali, C., et al. 2009, ApJS, 184, 158, doi: [`10.1088/0067-0049/184/1/158`](http://doi.org/10.1088/0067-0049/184/1/158)

(ref: erb08_apj674) Erb, D. K. 2008, ApJ, 674, 151, doi: [`10.1086/524727`](http://doi.org/10.1086/524727)

(ref: faucher-giguere18) Faucher-Giguère, C.-A. 2018, MNRAS, 473, 3717, doi: [`10.1093/mnras/stx2595`](http://doi.org/10.1093/mnras/stx2595)

(ref: faucher-giguere11) Faucher-Giguère, C.-A., Kereš, D., & Ma, C.-P. 2011, MNRAS, 417, 2982, doi: [`10.1111/j.1365-2966.2011.19457.x`](http://doi.org/10.1111/j.1365-2966.2011.19457.x)

(ref: feldmann06) Feldmann, R., Carollo, C. M., Porciani, C., et al. 2006, MNRAS, 372, 565, doi: [`10.1111/j.1365-2966.2006.10930.x`](http://doi.org/10.1111/j.1365-2966.2006.10930.x)

(ref: finlator08) Finlator, K., & Davé, R. 2008, MNRAS, 385, 2181, doi: [`10.1111/j.1365-2966.2008.12991.x`](http://doi.org/10.1111/j.1365-2966.2008.12991.x)

(ref: freundlich19) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2019, A&A, 622, A105, doi: [`10.1051/0004-6361/201732223`](http://doi.org/10.1051/0004-6361/201732223)

(ref: geach11) Geach, J. E., Smail, I., Moran, S. M., et al. 2011, ApJL, 730, L19, doi: [`10.1088/2041-8205/730/2/L19`](http://doi.org/10.1088/2041-8205/730/2/L19)

(ref: genzel10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091, doi: [`10.1111/j.1365-2966.2010.16969.x`](http://doi.org/10.1111/j.1365-2966.2010.16969.x)

(ref: genzel11) Genzel, R., Newman, S., Jones, T., et al. 2011, ApJ, 733, 101, doi: [`10.1088/0004-637X/733/2/101`](http://doi.org/10.1088/0004-637X/733/2/101)

(ref: genzel12) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69, doi: [`10.1088/0004-637X/746/1/69`](http://doi.org/10.1088/0004-637X/746/1/69)

(ref: groves15) Groves, B. A., Schinnerer, E., Leroy, A., et al. 2015, ApJ, 799, 96, doi: [`10.1088/0004-637X/799/1/96`](http://doi.org/10.1088/0004-637X/799/1/96)

(ref: yicheng16) Guo, Y., Rafelski, M., Faber, S. M., et al. 2016, ApJ, 833, 37, doi: [`10.3847/1538-4357/833/1/37`](http://doi.org/10.3847/1538-4357/833/1/37)

(ref: hayword17) Hayward, C. C., & Hopkins, P. F. 2017, MNRAS, 465, 1682, doi: [`10.1093/mnras/stw2888`](http://doi.org/10.1093/mnras/stw2888)

(ref: herrera-camus18) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 94, doi: [`10.3847/1538-4357/aac0f6`](http://doi.org/10.3847/1538-4357/aac0f6)

(ref: hunt15) Hunt, L. K., Garcı́a-Burillo, S., Casasola, V., et al. 2015, A&A, 583, A114, doi: [`10.1051/0004-6361/201526553`](http://doi.org/10.1051/0004-6361/201526553)

(ref: hunt19) Hunt, L. K., De Looze, I., Boquien, M., et al. 2019, A&A, 621, A51, doi: [`10.1051/0004-6361/201834212`](http://doi.org/10.1051/0004-6361/201834212)

(ref: ilbert13) Ilbert, O., McCracken, H. J., Le Fèvre, O., et al. 2013, A&A, 556, A55, doi: [`10.1051/0004-6361/201321100`](http://doi.org/10.1051/0004-6361/201321100)

(ref: kalfountzou14) Kalfountzou, E., Civano, F., Elvis, M., Trichas, M., & Green, P. 2014, MNRAS, 445, 1430, doi: [`10.1093/mnras/stu1745`](http://doi.org/10.1093/mnras/stu1745)

(ref: kashino19) Kashino, D., & Inoue, A. K. 2019, MNRAS, 486, 1053, doi: [`10.1093/mnras/stz881`](http://doi.org/10.1093/mnras/stz881)

(ref: kennicutt98) Kennicutt, Robert C., J. 1998, ApJ, 498, 541, doi: [`10.1086/305588`](http://doi.org/10.1086/305588)

(ref: kewleydopita02) Kewley, L. J., & Dopita, M. A. 2002, ApJS, 142, 35, doi: [`10.1086/341326`](http://doi.org/10.1086/341326)

(ref: khostovan15) Khostovan, A. A., Sobral, D., Mobasher, B., et al. 2015, MNRAS, 452, 3948, doi: [`10.1093/mnras/stv1474`](http://doi.org/10.1093/mnras/stv1474)

(ref: KK04) Kobulnicky, H. A., & Kewley, L. J. 2004, ApJ, 617, 240, doi: [`10.1086/425299`](http://doi.org/10.1086/425299)

(ref: kriek09b) Kriek, M., van Dokkum, P. G., Labbé, I., et al. 2009, ApJ, 700, 221, doi: [`10.1088/0004-637X/700/1/221`](http://doi.org/10.1088/0004-637X/700/1/221)

(ref: lagos16) Lagos, C. d. P., Theuns, T., Schaye, J., et al. 2016, MNRAS, 459, 2632, doi: [`10.1093/mnras/stw717`](http://doi.org/10.1093/mnras/stw717)

(ref: cosmos2015) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24, doi: [`10.3847/0067-0049/224/2/24`](http://doi.org/10.3847/0067-0049/224/2/24)

(ref: leroy11) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12, doi: [`10.1088/0004-637X/737/1/12`](http://doi.org/10.1088/0004-637X/737/1/12)

(ref: lilly13) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119, doi: [`10.1088/0004-637X/772/2/119`](http://doi.org/10.1088/0004-637X/772/2/119)

(ref: lilly07) Lilly, S. J., Le Fèvre, O., Renzini, A., et al. 2007, ApJS, 172, 70, doi: [`10.1086/516589`](http://doi.org/10.1086/516589)

(ref: liu19_II) Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235, doi: [`10.3847/1538-4357/ab578d`](http://doi.org/10.3847/1538-4357/ab578d)

(ref: madau14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: magdis12) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6, doi: [`10.1088/0004-637X/760/1/6`](http://doi.org/10.1088/0004-637X/760/1/6)

(ref: magdis17) Magdis, G. E., Rigopoulou, D., Daddi, E., et al. 2017, A&A, 603, A93, doi: [`10.1051/0004-6361/201731037`](http://doi.org/10.1051/0004-6361/201731037)

(ref: mannucci10) Mannucci, F., Cresci, G., Maiolino, R., Marconi, A., & Gnerucci, A. 2010, MNRAS, 408, 2115, doi: [`10.1111/j.1365-2966.2010.17291.x`](http://doi.org/10.1111/j.1365-2966.2010.17291.x)

(ref: mccracken12) McCracken, H. J., Milvang-Jensen, B., Dunlop, J., et al. 2012, A&A, 544, A156, doi: [`10.1051/0004-6361/201219507`](http://doi.org/10.1051/0004-6361/201219507)

(ref: mclean10) McLean, I. S., Steidel, C. C., Epps, H., et al. 2010, in Proc. SPIE, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, 77351E–77351E–12, doi: [`10.1117/12.856715`](http://doi.org/10.1117/12.856715)

(ref: mclean12) McLean, I. S., Steidel, C. C., Epps, H. W., et al. 2012, in Proc. SPIE, Vol. 8446, Ground-based and Airborne Instrumentation for Astronomy IV, 84460J, doi: [`10.1117/12.924794`](http://doi.org/10.1117/12.924794)

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mitra15) Mitra, S., Davé, R., & Finlator, K. 2015, MNRAS, 452, 1184, doi: [`10.1093/mnras/stv1387`](http://doi.org/10.1093/mnras/stv1387)

(ref: muratov15) Muratov, A. L., Kereš, D., Faucher-Giguère, C.-A., et al. 2015, MNRAS, 454, 2691, doi: [`10.1093/mnras/stv2126`](http://doi.org/10.1093/mnras/stv2126)

(ref: onodera16) Onodera, M., Carollo, C. M., Lilly, S., et al. 2016, ApJ, 822, 42, doi: [`10.3847/0004-637X/822/1/42`](http://doi.org/10.3847/0004-637X/822/1/42)

(ref: pengmaiolino14) Peng, Y.-j., & Maiolino, R. 2014, MNRAS, 443, 3643, doi: [`10.1093/mnras/stu1288`](http://doi.org/10.1093/mnras/stu1288)

(ref: PP04) Pettini, M., & Pagel, B. E. J. 2004, MNRAS, 348, L59, doi: [`10.1111/j.1365-2966.2004.07591.x`](http://doi.org/10.1111/j.1365-2966.2004.07591.x)

(ref: popping15) Popping, G., Caputi, K. I., Trager, S. C., et al. 2015, MNRAS, 454, 2258, doi: [`10.1093/mnras/stv2136`](http://doi.org/10.1093/mnras/stv2136)

(ref: astropy:2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: remy-ruyer14) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31, doi: [`10.1051/0004-6361/201322803`](http://doi.org/10.1051/0004-6361/201322803)

(ref: riechers19) Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7, doi: [`10.3847/1538-4357/aafc27`](http://doi.org/10.3847/1538-4357/aafc27)

(ref: riechers20) Riechers, D. A., Boogaard, L. A., Decarli, R., et al. 2020, ApJL, 896, L21, doi: [`10.3847/2041-8213/ab9595`](http://doi.org/10.3847/2041-8213/ab9595)

(ref: rupke08) Rupke, D. S. N., Veilleux, S., & Baker, A. J. 2008, ApJ, 674, 172, doi: [`10.1086/522363`](http://doi.org/10.1086/522363)

(ref: saintonge12) Saintonge, A., Tacconi, L. J., Fabello, S., et al. 2012, ApJ, 758, 73, doi: [`10.1088/0004-637X/758/2/73`](http://doi.org/10.1088/0004-637X/758/2/73)

(ref: saintonge13) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2, doi: [`10.1088/0004-637X/778/1/2`](http://doi.org/10.1088/0004-637X/778/1/2)

(ref: saintonge17) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22, doi: [`10.3847/1538-4365/aa97e0`](http://doi.org/10.3847/1538-4365/aa97e0)

(ref: sanders20) Sanders, R. L., Shapley, A. E., Jones, T., et al. 2020, arXiv e-prints, arXiv:2009.07292. [`https://arxiv.org/abs/2009.07292`](https://arxiv.org/abs/2009.07292)

(ref: santini10) Santini, P., Maiolino, R., Magnelli, B., et al. 2010, A&A, 518, L154, doi: [`10.1051/0004-6361/201014748`](http://doi.org/10.1051/0004-6361/201014748)

(ref: santini14) Santini, P., Maiolino, R., Magnelli, B., et al. 2014, A&A, 562, A30, doi: [`10.1051/0004-6361/201322835`](http://doi.org/10.1051/0004-6361/201322835)

(ref: sargent14) Sargent, M. T., Daddi, E., Béthermin, M., et al. 2014, ApJ, 793, 19, doi: [`10.1088/0004-637X/793/1/19`](http://doi.org/10.1088/0004-637X/793/1/19)

(ref: schinnerer16) Schinnerer, E., Groves, B., Sargent, M. T., et al. 2016, ApJ, 833, 112, doi: [`10.3847/1538-4357/833/1/112`](http://doi.org/10.3847/1538-4357/833/1/112)

(ref: schmidt1959) Schmidt, M. 1959, ApJ, 129, 243, doi: [`10.1086/146614`](http://doi.org/10.1086/146614)

(ref: scoville14) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84, doi: [`10.1088/0004-637X/783/2/84`](http://doi.org/10.1088/0004-637X/783/2/84)

(ref: scoville16) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83, doi: [`10.3847/0004-637X/820/2/83`](http://doi.org/10.3847/0004-637X/820/2/83)

(ref: scoville17) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150, doi: [`10.3847/1538-4357/aa61a0`](http://doi.org/10.3847/1538-4357/aa61a0)

(ref: seko16_alma) Seko, A., Ohta, K., Yabe, K., et al. 2016a, ApJ, 819, 82, doi: [`10.3847/0004-637X/819/1/82`](http://doi.org/10.3847/0004-637X/819/1/82)

(ref: seko16) —. 2016b, ApJ, 833, 53, doi: [`10.3847/1538-4357/833/1/53`](http://doi.org/10.3847/1538-4357/833/1/53)

(ref: shapley20) Shapley, A. E., Cullen, F., Dunlop, J. S., et al. 2020, arXiv e-prints, arXiv:2009.10091. [`https://arxiv.org/abs/2009.10091`](https://arxiv.org/abs/2009.10091)

(ref: sobral14) Sobral, D., Best, P. N., Smail, I., et al. 2014, MNRAS, 437, 3516, doi: [`10.1093/mnras/stt2159`](http://doi.org/10.1093/mnras/stt2159)

(ref: sobral13) Sobral, D., Smail, I., Best, P. N., et al. 2013, MNRAS, 428, 1128, doi: [`10.1093/mnras/sts096`](http://doi.org/10.1093/mnras/sts096)

(ref: speagle14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: sugahara17) Sugahara, Y., Ouchi, M., Lin, L., et al. 2017, ApJ, 850, 51, doi: [`10.3847/1538-4357/aa956d`](http://doi.org/10.3847/1538-4357/aa956d)

(ref: suzuki17) Suzuki, T. L., Kodama, T., Onodera, M., et al. 2017, ApJ, 849, 39, doi: [`10.3847/1538-4357/aa8df3`](http://doi.org/10.3847/1538-4357/aa8df3)

(ref: tacchella20) Tacchella, S., Forbes, J. C., & Caplar, N. 2020, arXiv e-prints, arXiv:2006.09382. [`https://arxiv.org/abs/2006.09382`](https://arxiv.org/abs/2006.09382)

(ref: tacconi10) Tacconi, L. J., Genzel, R., Neri, R., et al. 2010, Nature, 463, 781, doi: [`10.1038/nature08773`](http://doi.org/10.1038/nature08773)

(ref: tacconi13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74, doi: [`10.1088/0004-637X/768/1/74`](http://doi.org/10.1088/0004-637X/768/1/74)

(ref: tacconi18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179, doi: [`10.3847/1538-4357/aaa4b4`](http://doi.org/10.3847/1538-4357/aaa4b4)

(ref: tan14) Tan, Q., Daddi, E., Magdis, G., et al. 2014, A&A, 569, A98, doi: [`10.1051/0004-6361/201423905`](http://doi.org/10.1051/0004-6361/201423905)

(ref: topcat) Taylor, M. B. 2005, in Astronomical Society of the Pacific Conference Series, Vol. 347, Astronomical Data Analysis Software and Systems XIV, ed. P. Shopbell, M. Britton, & R. Ebert, 29

(ref: tomczak16) Tomczak, A. R., Quadri, R. F., Tran, K.-V. H., et al. 2016, ApJ, 817, 118, doi: [`10.3847/0004-637X/817/2/118`](http://doi.org/10.3847/0004-637X/817/2/118)

(ref: torrey19) Torrey, P., Vogelsberger, M., Marinacci, F., et al. 2019, MNRAS, 484, 5587, doi: [`10.1093/mnras/stz243`](http://doi.org/10.1093/mnras/stz243)

(ref: troncoso14) Troncoso, P., Maiolino, R., Sommariva, V., et al. 2014, A&A, 563, A58, doi: [`10.1051/0004-6361/201322099`](http://doi.org/10.1051/0004-6361/201322099)

(ref: walter16) Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67, doi: [`10.3847/1538-4357/833/1/67`](http://doi.org/10.3847/1538-4357/833/1/67)

(ref: whitaker12) Whitaker, K. E., van Dokkum, P. G., Brammer, G., & Franx, M. 2012, ApJL, 754, L29, doi: [`10.1088/2041-8205/754/2/L29`](http://doi.org/10.1088/2041-8205/754/2/L29)

(ref: wiklind19) Wiklind, T., Ferguson, H. C., Guo, Y., et al. 2019, ApJ, 878, 83, doi: [`10.3847/1538-4357/ab1089`](http://doi.org/10.3847/1538-4357/ab1089)

(ref: yabe15_apj) Yabe, K., Ohta, K., Akiyama, M., et al. 2015, ApJ, 798, 45, doi: [`10.1088/0004-637X/798/1/45`](http://doi.org/10.1088/0004-637X/798/1/45)

(ref: zahid_apj791) Zahid, H. J., Dima, G. I., Kudritzki, R.-P., et al. 2014, ApJ, 791, 130, doi: [`10.1088/0004-637X/791/2/130`](http://doi.org/10.1088/0004-637X/791/2/130)

</paper>

Write the methods card for this paper.