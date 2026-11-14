# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...985..243B\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...985..243B",
 "title": "The ALMA-CRISTAL Survey: Weak Evidence for Star-formation-driven Outflows in z ∼ 5 Main-sequence Galaxies",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Birkin, Jack E.",
 "n_authors": 26,
 "arxiv_id": "2504.17877",
 "doi": "10.3847/1538-4357/adced3",
 "alma_projects_linked_by_archive": [
  "2017.1.00428.L",
  "2018.1.01359.S",
  "2018.1.01605.S",
  "2019.1.00226.S",
  "2019.1.01075.S",
  "2021.1.00280.L"
 ]
}
```

Paper text:
<paper>
# The ALMA-CRISTAL survey: weak evidence for star-formation driven outflows in $z$ $\sim$ 5 main-sequence galaxies

## Abstract

There is a broad consensus from theory that stellar feedback in galaxies at high redshifts is essential to their evolution, alongside conflicting evidence in the observational literature about its prevalence and efficacy. To this end, we utilize deep, high-resolution \[Cii\] emission line data taken as part of the \[Cii\] resolved ISM in star-forming galaxies with ALMA (CRISTAL) survey. Excluding sources with kinematic evidence for gravitational interactions, we perform a rigorous stacking analysis of the remaining 15 galaxies to search for broad emission features that are too weak to detect in the individual spectra, finding only weak evidence that a broad component is needed to explain the composite spectrum. Additionally, such evidence is mostly driven by CRISTAL-02, which is already known to exhibit strong outflows in multiple ISM phases. Interpreting modest residuals in the stack at $v$ $\sim$ 300 km s$^{-1}$ as an outflow, we derive a mass outflow rate of $\dot{M}_{\rm out}$ $=$ 26 $\pm$ 11 M$_\odot$ yr$^{-1}$ and a cold outflow mass-loading factor of $\eta_m$ $=$ 0.49 $\pm$ 0.20. This result holds for the subsample with the highest star-formation rate surface density ($\Sigma_{\rm{SFR}}$ $>$ 1.93 M$_\odot$ yr$^{-1}$ kpc$^{-2}$) but no such broad component is present in the composite of the lower-star-formation rate density subsample. Our results imply that the process of star-formation-driven feedback may already be in place in typical galaxies at $z$ $=$ 5, but on average not strong enough to completely quench ongoing star formation.

# Introduction

There is a general consensus that stellar feedback is an important component in galaxy formation models, and that such feedback (alongside AGN feedback) plays a key role in regulating the evolution of galaxies and producing the conditions we observe (cite: dekel1986). Massive stars inject enormous levels of energy into the interstellar medium (ISM) through supernovae and stellar winds, heating the gas and potentially expelling it from the galaxy altogether, with the possibility of later recycling it to drive further star formation (cite: oppenheimer10; henriques13; angles-alcazar17). Such feedback primarily prevents runaway star formation, regulates the metallicity of the galaxy (cite: tremonti04; dalcanton07; finlator08; lilly13; torrey19), and enables quenching. This regulation manifests in the observed mass-metallicity relation (cite: tremonti04; curti20a) and fundamental metallicity relation (cite: lequeux1978; ellison08; mannucci10). Massive galaxy-scale outflows are one of the most dramatic consequences of feedback, and therefore have a huge influence on the evolution of galaxies. This process should therefore be understood and accurately implemented in theoretical models.

Observationally, outflow signatures have been detected in multiple phases of the ISM, from cool molecular and cold dust components all the way up to hot X-ray-emitting gas (cite: veilleux20). Therefore, there are various observational indicators that can be used to search for outflow signatures. Efforts to detect outflows in galaxies and characterize their effects on the evolution of the host have been ongoing for decades. However, at high redshifts these observational indicators become fainter and much more difficult to detect. Most studies at $z$ $\sim$ 5 and beyond have therefore focused on extreme galaxies and/or quasars (cite: maiolino12; cicone15; bischetti19). In less extreme galaxies, statistical conclusions about the nature and impact of outflows are fewer and further between (cite: davies19; forster-schreiber19; leung19; swinbank19; weldon24).

At $z$ $\sim$ 4 and beyond, the emission line of singly ionized carbon at 158 $\mu$m, \[CII\] is one of the strongest lines that can be observed, originating primarily from neutral regions but with a non-negligible contribution from ionized gas (cite: croxall17; diaz-santos17; cormier19). Importantly for studies at $z$ $\sim$ 4–6, this bright line is redshifted into an atmospheric transmission window accessible from the ground by interferometers such as the Atacama Large Millimeter/submillimeter Array (ALMA). As a consequence, the \[CII\] emission line has been exploited frequently to study outflows in sources at these epochs, most prominently high-$z$ QSOs (cite: maiolino12; cicone15; bischetti19; novak20) but increasingly for star-forming galaxies in recent years (cite: gallerani18; sugahara19; ginolfi20; spilker20; herrera-camus21; kade23). On the contrary, the reliability of the \[CII\] line as a tracer of outflows was questioned by (cite: spilker20), who found no broad \[CII\] emission in sources displaying clear OH outflows.

A common thread between high-redshift \[Cii\] studies of outflows in QSOs and star-forming galaxies is the lack of a general consensus on their presence, absence, or ubiquity. Several studies of individual QSOs have found evidence for broad wings, such as (cite: tripodi22) whose study of the $z$ $\sim$ 6 QSO SDSS J2310+1855 was also supported by H$_2$O emission line observations, and (cite: maiolino12) who reported an outflow in SDSS J1148+5251 at $z$ $=$ 6.4189 (cite: cicone15). This result was later challenged by (cite: meyer22) using new NOEMA data. However, the QSOs studied in those works are extremely bright, making the detection of weaker broad line components in the line easier than for fainter star-forming galaxies (cite: herrera-camus21).

As a result of this limitation, authors have resorted to stacking techniques to improve the signal-to-noise (S/N) of their data, in an attempt to detect broad components in fainter sources (cite: decarli18; bischetti19; davies19; stanley19; jolly20; novak20). This method amplifies weak features in the emission but sacrifices information about individual sources, providing only average properties of the sample as a whole. An additional challenge arises from the intrinsic diversity among galaxies, including differences in size, brightness, and kinematics. These variations must be carefully accounted for when combining spectra to avoid skewing the interpretation toward galaxies with more extreme characteristics.

For QSOs there is a considerable amount of literature on \[CII\] stacking analyses, but with differing conclusions. (cite: bischetti19) stacked a sample of 48 $z$ $\sim$ 4.5–7.1 QSOs and found evidence of outflows with velocities greater than 1000 km s$^{-1}$, corresponding to an atomic gas mass outflow rate of $\dot{M}$ $\sim$ 100–200 M$_\odot$ yr$^{-1}$. In contrast, (cite: decarli18) stacked the spectra of 27 $z$ $\sim$ 6 QSOs and found no such evidence. (cite: novak20) came to the same conclusion from a $uv$-plane stack of a similar sample of 27 $z$ $\sim$ 6 QSOs (and a further 20 archival sources observed at lower resolution). As outflows are not likely to be isotropic, (cite: stanley19) tested the effects of orientation on stacking QSO spectra, after themselves finding only tentative evidence for broad emission from a sample of 26 $z$ $\sim$ 6 QSOs.

The various studies employ subtly different techniques, making it difficult to compare and to determine which are most likely to be accurate. Nevertheless, studies of high-redshift star-forming galaxies, particularly those on the star-formation "main sequence", are heavily reliant on stacking simply because the sources are fainter.

In one of the most ambitious attempts to characterize the typical galaxy population at $z$ $\sim$ 5, the ALMA Large Program to INvestigate \[CII\] at Early times (cite: lefevre20; bethermin20; faisst20) detected 75 galaxies in \[CII\] emission, which was later exploited by (cite: ginolfi20) to examine outflows at this epoch. carried out a stacking analysis using 50 galaxies from the ALPINE sample, excluding 25 sources morpho-kinematically identified as mergers. They tested three different techniques: stacking the residuals from single-Gaussian fits to the data, stacking the \[Cii\] spectra, and stacking the cubes. They also binned their sample by star-formation rate, finding only the composite of galaxies with higher star-formation rates to display broad emission, and interpreted this as evidence for star-formation driven outflows. This followed a similar analysis by (cite: gallerani18) of nine $z$ $\sim$ 5.5 galaxies which showed flux excess in the combined residuals extended over $\sim$ 1000 km s$^{-1}$.

The work of the ALPINE survey has been naturally extended through the \[CII\] Resolved ISM in Star-forming Galaxies with ALMA (CRISTAL; Herrera-Camus et al. in prep.) Large Program that has provided higher spatial resolution (by over a factor of 2 on average) \[CII\] data of a subsample of ALPINE galaxies, in addition to a supplementary six literature galaxies. The latter includes some galaxies from the samples studied by (cite: gallerani18) and (cite: sugahara19). The deeper data should make it easier to detect outflows, if they exist, and the higher angular resolution will enable us to more robustly identify mergers, and to spatially resolve any outflows that are present on smaller scales.

In this work, we present a stacking analysis of the CRISTAL data, with the aim of building upon the work of . The outline of this paper is as follows: in §[2](#sec:observations) we describe the observations carried out along with our data reduction methods, and in §[3](#sec:analysis) we describe our analysis of the reduced data. In §[4](#sec:results) we present the results and in §[5](#sec:discussion) we discuss their implications. In §[6](#sec:conclusions) we summarize our findings. Throughout this paper we adopt a flat $\Lambda$CDM cosmology with $\Omega_\mathrm{M}$ $=$ 0.3, $\Omega_\Lambda$ $=$ 0.7 and $H_0$ $=$ 70 km s$^{-1}$ Mpc$^{-1}$.

# Observations and data reduction

c\|c\|c\|c\|c\|c\|c CRISTAL ID & Alternate ID & & & $z_{\rm [CII]}$ & &\
\
CRISTAL-08 & vuds_efdcs_530029038 & 03:32:19.03 & $-$27:52:37.6 & 4.430 & 1.88 $\pm$ 0.23 & 9.85 $\pm$ 0.36\
CRISTAL-09a & DEIMOS_COSMOS_519281 & 09:59:00.89 & $+$02:05:27.6 & 5.575 & 1.51 $\pm$ 0.32 & 9.84 $\pm$ 0.39\
CRISTAL-11 & DEIMOS_COSMOS_630594 & 10:00:32.59 & $+$02:15:28.4 & 4.439 & 1.57 $\pm$ 0.31 & 9.68 $\pm$ 0.33\
CRISTAL-12 & CANDELS_GOODSS_21 & 03:32:11.95 & $-$27:41:57.5 & 5.572 & 0.98 $\pm$ 0.40 & 9.30 $\pm$ 0.47\
CRISTAL-19 & DEIMOS_COSMOS_494763 & 10:00:05.11 & $+$02:03:12.2 & 5.233 & 1.45 $\pm$ 0.36 & 9.51 $\pm$ 0.36\
\
CRISTAL-02 & DEIMOS_COSMOS_848185 & 10:00:21.50 & $+$02:35:11.0 & 5.294 & 2.25 $\pm$ 0.42 & 10.30 $\pm$ 0.28\
CRISTAL-03 & DEIMOS_COSMOS_536534 & 09:59:53.26 & $+$02:07:05.5 & 5.689 & 1.79 $\pm$ 0.31 & 10.40 $\pm$ 0.29\
CRISTAL-06b & – & 10:01:01.00 & $+$01:48:34.9 & 4.562 & 1.07 $\pm$ 0.33 & 9.19 $\pm$ 0.46\
CRISTAL-07a & DEIMOS_COSMOS_873321 & 10:00:04.06 & $+$02:37:35.8 & 5.154 & 1.89 $\pm$ 0.26 & 10.00 $\pm$ 0.33\
CRISTAL-09b & – & 09:59:00.78 & $+$02:05:26.9 & 5.577 & – $\pm$ – & – $\pm$ –\
CRISTAL-10a & DEIMOS_COSMOS_417567 & 10:02:04.13 & $+$01:55:44.4 & 5.671 & 1.86 $\pm$ 0.20 & 9.99 $\pm$ 0.31\
CRISTAL-15 & vuds_cosmos_5101244930 & 10:00:47.66 & $+$02:18:02.2 & 4.580 & 1.44 $\pm$ 0.24 & 9.69 $\pm$ 0.33\
CRISTAL-20 & HZ4 & 09:58:28.52 & $+$02:03:06.7 & 5.545 & 1.82 $\pm$ 0.28 & 10.11 $\pm$ 0.35\
CRISTAL-23b & – & 10:01:54.97 & $+$02:32:31.5 & 4.562 & 1.72 $\pm$ 1.33 & 10.46 $\pm$ 0.24\
CRISTAL-23c & – & 10:01:54.68 & $+$02:32:31.4 & 4.565 & – $\pm$ – & – $\pm$ –\

## The CRISTAL survey

We utilize Band 7 data from CRISTAL, an ALMA Cycle-8 Large Program (project ID 2021.1.00280.L; PI: R. Herrera-Camus) which is designed to provide spatially resolved \[Cii\] and 158 $\mu$m dust continuum maps of main sequence galaxies at $z$ $\sim$ 5. The CRISTAL sample consists of 25 main-sequence galaxies at $z$ $\sim$ 4.4–5.7 which were selected from the ALPINE sample (project ID 2017.1.00428.L; PI: O. Le Fèvre) to have existing rest-frame UV and/or optical Hubble Space Telescope (HST) detections, stellar masses greater than 10$^{9.5}$ M$_\odot$, and specific star-formation rates differing from that of the $z$ $=$ 5 main sequence by no more than a factor of 3. Fig. [1](#fig:main_sequence) shows both the ALPINE and CRISTAL samples in the stellar mass-SFR plane, with the sources used in and this work highlighted respectively. We note that CRISTAL-09b and CRISTAL-23c do not have available SED fits and are therefore not shown in Fig. [1](#fig:main_sequence). To account for this in our analysis we assign them the median $M_\ast$ and SFR of the remaining 13 galaxies.

The CRISTAL sample is comprised of 19 ALPINE sources (cite: lefevre20) along with a further six galaxies in the COSMOS field (HZ4, HZ7, HZ10, DC818760, DC873756, VC8326), that have ALMA data with similar spatial resolutions and sensitivities as CRISTAL (2018.1.01359.S and 2019.1.01075.S; PI: Manuel Aravena, 2018.1.01605.S; PI: Rodrigo Herrera-Camus, 2019.1.00226.S; PI: Edo Ibar). In the 25 fields observed as part of this sample, a total of 37 galaxies were identified by either resolving the main target into multiple objects or serendipitously detecting other sources. Herrera-Camus et al. (in prep.) will present details of the survey design and observational setup. For this work we conservatively removed 22 sources that resembled mergers or have significantly disturbed kinematics based on the classification by Lee at al. (in prep.; and see §[3.1](#sec:removing_mergers)), leaving a final sample size of 15 galaxies. The IDs, coordinates, redshifts, star-formation rates and stellar masses of the remaining 15 CRISTAL sources are shown in Table [\[tab:sample\]](#tab:sample).

## ALMA Band 7 Data Reduction

The CRISTAL and ALPINE archival observations were taken using ALMA Band 7, targeting the \[CII\] line ($\nu_{\rm rest}$ $=$ 1900.54 GHz). To detect the targets, ALPINE observations were taken using the most compact configurations (typically C43-1/2) which achieved an average beam size of 0.85$''$ $\times$ 1.13$''$ (cite: lefevre20). As one of the main goals of CRISTAL is to spatially resolve the \[CII\] emission, the new observations utilize more extended configurations (typically C43-4/5; beam sizes 0.1–0.3$''$) with the existing compact-configuration data being used to capture large-scale structures such as extended \[CII\] line emission (cite: ikeda24).

To achieve greater depths, the CRISTAL team combined the ALPINE and CRISTAL raw observations and re-processed them consistently, imaging the visibilities using both natural and Briggs (robust $=$ 0.5) weighting. In this work we utilize the natural-weighted data to maximize our sensitivity to weak outflow features. The median sensitivity achieved is 0.22 mJy in 20 km s$^{-1}$ channels and the median synthesized beam FWHM is 0.46$''$ $\times$ 0.40$''$ (2.9 $\times$ 2.5 kpc).

![](main_sequence_cristal_alpine.pdf)

![](cii_maps_full_sample.pdf)

# Analysis

## Removing potential mergers from the sample

The spectra of merging galaxies can blend multiple velocity components, from the interacting sources, disturbed gas kinematics, and the presence of tidal tails. Ultimately this results in broader spectral features which can mimic the appearance of feedback-driven outflows. Therefore, failing to account for mergers can bias the interpretation of broad emission, attributing it to outflows when it may simply reflect the dynamics of the merger. This demands a conservative approach to our analysis. identified possible mergers in their sample using the morpho-kinematic classification of ALPINE galaxies by (cite: lefevre20). However, as previously discussed, the angular resolution of the CRISTAL data is over twice as high as the ALPINE data, providing a new opportunity to examine which sources are likely to be mergers with higher precision.

A kinematic analysis of the full CRISTAL sample will be provided in Lee et al.(in prep.), and their classifications inform our choices of which sources to include. More specifically, they classified the CRISTAL galaxies as either disk-like, with types “Best disk” and “Disk”, or non-disk. Their classification is based on a combination of kinemetry to identify deviations from orderly velocity gradients and asymmetries in the velocity/velocity dispersion maps, and spectro-astrometry to identify distinct components by utilizing the full 3-D information from the cubes.

The “Best disk” category comprises isolated sources with no visible neighbors or signs of perturbations; and the “Disk” category comprises sources that exhibit disk-like kinematics, with minor perturbations in their outskirts. Therefore, there remain sources in the “Disk” category that are interacting with a nearby companion, most prominently CRISTAL-07a and CRISTAL-23b (see Fig. [2](#fig:cii_maps)). Further, separate analyses of CRISTAL-05 and CRISTAL-22 have been presented by (cite: posses24) and (cite: telikova24), both of which appear to show complex kinematics.

Considering the above, we retain the 15 sources that are classified as “Best disk” and “Disk” sources from Lee et al.(in prep.). Based on the analysis by Lee et al.(in prep.) we do not expect interacting sources in the “Disk” category to contribute substantial high-velocity emission originating from these interactions to the stack, hence their inclusion. We remove the sources classified as non-disks, which lack disk-like characteristics and potentially include both major mergers and poorly resolved sources. We also conservatively remove CRISTAL-05 and CRISTAL-22 due to their complex kinematics. While this approach limits the S/N improvement achieved by stacking, it is a necessary concession to ensure that our conclusions are unbiased. The final sample is shown in Table [\[tab:sample\]](#tab:sample), where we separate sources that were included in/excluded from the stack (see also Fig. [1](#fig:main_sequence)). Interestingly, two-thirds of our sample were excluded by on the basis of their morpho-kinematic analysis. This highlights how the differing resolution of the ALPINE and CRISTAL datasets can affect the interpretation of the same parent sample.

## Spectral extraction

For the finalized sample of 15 CRISTAL galaxies, we produce \[CII\] line maps by collapsing the continuum-subtracted cubes within $\pm$ 1 FWHM$_{\rm [CII]}$ of the \[CII\] redshift (so as to ensure full coverage of the \[CII\] emission; FWHM$_{\rm [CII]}$ measured by Herrera-Camus et al. in prep.), in a 4$''$ $\times$ 4$''$ window centered on the source position. These are shown in Fig. [2](#fig:cii_maps), in which we can clearly see the morphological complexity of many of the galaxies. This makes simple circular or elliptical apertures less effective for extracting spectra than it would be for point-like sources. Therefore for each line map we generate a mask for all pixels with flux density exceeding 2 $\sigma$, and sum all emission within the mask to extract one-dimensional (1-D) spectra for each source. To quantify the uncertainty on the flux densities, we mask channels in the 1-D spectra that are within $\pm$ 1 FWHM$_{\rm [CII]}$ of the line centroid, and calculate the root mean square (RMS) of the remaining channels (i.e. the signal-free part of the spectrum).

A visual inspection of the spectra (see Figs. [3](#fig:stack_all_2sig)–[6](#fig:stack_high_sfr) alongside the composites; §[4](#sec:results)) shows that some of the line profiles are complex, with a handful appearing asymmetric. In these cases, fitting Gaussian profiles would not give a representative model of the \[CII\] emission, and in general we prefer to derive the zeroth, first and second moments of the spectra to estimate line fluxes, centroids and linewidths, respectively (cite: birkin21). This is particularly important in deriving the velocity centroid, which must be done correctly to center each emission line before the stack. If the line centers are not aligned before stacking, this could falsely induce broad features in the composite.

We note that uncertainties on the emission centroids were not explicitly included in our analysis. These centroid uncertainties were found to be small ($<$ 20 km s$^{-1}$ for the entire sample), substantially smaller than the measured line widths (median 260 km s$^{-1}$). Nevertheless, to confirm that these uncertainties do not influence our results, we incorporated centroid errors into the Monte Carlo uncertainty analysis described above. We found that our conclusions remained unchanged.

As the S/N of the individual spectra are modest, median S/N $=$ 14 $\pm$ 3, when deriving moments we first fit an approximate Gaussian to the line profile to establish the FWHM, and then only use channels between $\pm$ 1.5 $\times$ the FWHM of the Gaussian to mitigate the influence of the continuum on the measured centroid (cite: birkin21). For the 15 CRISTAL galaxies used in the stack we measure a median FWHM$_{\rm [CII]}$ $=$ 260$^{+50}_{-80}$ km s$^{-1}$, where the uncertainties reflect the 16th–84th percentile scatter in the sample. To prepare the individual spectra for stacking we shift each velocity axis by a value equal to the first moment.

## Stacking analysis

To combine the individual spectra we sum the flux density in each channel, weighted by the uncertainty $\sigma$ (as calculated in §[3.2](#sec:spectral_extraction)) as: $$\begin{equation}
    S^{\rm stack}_i = \dfrac{\Sigma^N_{k=1} S_{i,k} \times w_k}{\Sigma^N_{k=1} w_k},
    \label{eq:stack_spectra}
\end{equation}$$ where $S$ and $w=1/\sigma^2$ are the flux density and corresponding weight, $i$ represents the channel index, and $k$ represents the source index (cite: ginolfi20). We sample the composite in bins of 50 km s$^{-1}$, ensuring that each bin contains a reasonable number of channels from the original 20 km s$^{-1}$ data. To estimate the uncertainty in each composite channel we perturb each flux density value by a random multiple of its associated error (sampled from the normal distribution) 100 times, then calculate the RMS of the resultant values.

It is not obvious what the “correct” method of normalizing the sample is, given the variety of properties, and therefore we attempt several methods:

1.  **No normalization:** purely stacking the spectra as they are. This method aligns most closely with that used by .

2.  **Scaling the linewidth by the median:** it has been shown by (cite: jolly20) that stacking lines with different widths results in a non-Gaussian composite. Therefore we measure the FWHM of each line profile from the second moment, and then stretch the emission line from each source to match the median of the sample, FWHM$_{\rm med}$ $=$ 260 km s$^{-1}$, following (cite: decarli18) and (cite: novak20). The resultant factors applied to the individual spectral axes are all in the range 0.8–2.0.

3.  **Scaling the linewidth by the median and normalizing the flux density to ensure that the total integrated flux across the emission line is conserved:** expanding on method 2), but now also adjusting the flux density by the same factor as the linewidth, so that the total integrated flux is conserved. This method should give less weight to brighter sources.

4.  **Scaling the linewidth to match the median and adjusting the flux density by the peak value:** similar to method 3) but we instead divide each spectrum by the peak emission flux density. This ensures that we are purely considering the *profile* of the emission lines. The resultant factors applied to the individual flux densities are all in the range 0.5–5.4.

We perform tests of these four methods to ensure that we understand how they affect our conclusions, which we present in §[4.3](#sec:stacking_methods). However, for the analysis presented in the rest of this paper we mainly utilize the composites derived using method 4.

## Line fitting

Having produced composite spectra, we search for broad components that may indicate outflows. To do so, we fit two models to the \[CII\] emission line, using the Markov Chain Monte Carlo (MCMC) ensemble sampler `emcee` (cite: foreman-mackey13). The first is a simple single-Gaussian model with free parameters amplitude, mean and sigma. The second is a double-Gaussian model, one narrow and one broad, each with the same three free parameters. However, in the double-Gaussian model we place a number of constraints on these parameters:

- The narrow FWHM is constrained to be between 80 km s$^{-1}$ and 400 km s$^{-1}$ and the broad FWHM is constrained to be between 400 km s$^{-1}$ and 1500 km s$^{-1}$,

- The central wavelengths of both lines are constrained to be within $\pm$ 200 km s$^{-1}$ of the systemic redshift,

- The narrow amplitude is constrained to be at least twice the broad amplitude (cite: carniani24),

- The broad FWHM is constrained to be at least 1.2 $\times$ the narrow FWHM (cite: carniani24).

To statistically conclude whether or not broad components are necessary to describe our stacks, we implement a Bayesian Information Criterion (BIC) test. Measured as BIC $=$ $\chi^2+k\log{n}$, where $\chi^2$ is the chi-squared value of the model, $k$ is the number of parameters in the model and $n$ is the number of data points used in the fit, the BIC punishes the model if using many parameters to obtain a good fit. This allows us to quantitatively decide whether adding an additional model component to describe an outflow provides a statistically better description of the data to justify the extra parameters, based on the difference in BIC between the single- and double-Gaussian models, calculated as $\Delta{\rm BIC}$ $=$ BIC$_{\rm single}$ $-$ BIC$_{\rm double}$. Although the $\Delta{\rm BIC}$ test does not give a statistical significance such as a p-value, the general rule of thumb is that $\Delta{\rm BIC}$ $>$ 10 represents overwhelming evidence for the model with the lowest BIC. In our analysis, we will measure outflow properties if the $\Delta{\rm BIC}$ $>$ 0, but require $\Delta{\rm BIC}$ $>$ 10 to securely reject the null hypothesis that the composite \[CII\] emission is satisfactorily described by a single Gaussian (cite: swinbank19; avery21; concas22; weldon24).

We note that this choice of $\Delta{\rm BIC}$ $=$ 10 is not a perfect one in the context of fitting outflows (cite: chu24), and it was mostly made to ensure comparability with other similar studies. For full transparency we include the measured $\Delta{\rm BIC}$ values with our results, and it is left up to the reader to make their own conclusions about the significance of these results.

## Bootstrap/jackknife resampling tests

Previously we have aimed to remove any obvious individual sources which may mimic outflows in the sample (see §[3.1](#sec:removing_mergers)). However, we still wish to test whether any of the remaining galaxies could potentially bias our conclusions. For example, CRISTAL-02 is known to drive a powerful outflow from its central regions (Davies et al. in prep.). To account for this, we perform a bootstrap test by resampling with replacement. For each composite, we create 100 resampled sets by randomly selecting from the included galaxies, and then apply the BIC test described in §[3.4](#sec:line_fitting). Further, we perform a separate stack of the full sample without CRISTAL-02, the individual CRISTAL galaxy with the most obvious outflow (Davies et al. in prep.), reducing the sample size to 14. We discuss the results of these tests in §[4](#sec:results).

# Results

![](all_sources_2sig.pdf)

## Global stacks

We stack the integrated spectra of all 15 \[CII\]-detected CRISTAL disk-like galaxies using method 4 (see §[3.3](#sec:stacking)), the result of which is shown in Fig. [3](#fig:stack_all_2sig). The majority of the individual line profiles, also shown in Fig. [3](#fig:stack_all_2sig), do not reveal any obvious outflow signatures, although the double-Gaussian fit appears to better match the outer parts of the composite profile. This can be seen in the single-Gaussian residuals which show a feature at $\sim$ $-$300 km s$^{-1}$ that is not present in the double-Gaussian model. Indeed, we find $\Delta{\rm BIC}$ $=$ 17 for the composite indicating that the double-Gaussian model is preferred, which has FWHM$_{\rm narrow}$ $=$ 232 $\pm$ 13 km s$^{-1}$ and FWHM$_{\rm broad}$ $=$ 501 $\pm$ 62 km s$^{-1}$. Stacks of the residuals from single-Gaussian fits to each source were found to be consistent with the residuals shown in Fig. [3](#fig:stack_all_2sig).

Applying the bootstrap test described in §[3.5](#sec:resampling), we find that in 55$\%$ of cases broad emission is identified, with only 8$\%$ of all cases having $\Delta{\rm BIC}$ $>$ 10. This implies that a small number of sources, likely including CRISTAL-02, are significantly influencing the need for a broad component when modeling the stacked spectra. Indeed, when purposefully removing CRISTAL-02 from the stack we find $\Delta{\rm BIC}$ $=$ 3.1 (shown in Fig. [4](#fig:stack_no_c02)). Given this result, and the relatively low $\ensuremath{\Delta{\rm BIC}}$, we choose to interpret our global composite as providing only modest support for outflows.

![](all_sources_2sig_noc2.pdf)

## Resolved composites

![](mask_low_sfr_vel_res_med.pdf)

![](mask_high_sfr_vel_res_med.pdf)

One of the key results obtained by showed that outflows are only present in the stacks of ALPINE galaxies with higher global star-formation rates. Other authors have found a similar result (cite: forster-schreiber19; swinbank19). This was shown by dividing the sample into low-SFR and high-SFR bins and stacking the resultant subsets. However, in reality, outflows likely occur in specific regions of galaxies rather than uniformly (cite: genzel11; newman12; davies19).

To test these findings, we build on the result by leveraging the improved resolution of CRISTAL to focus on stacking only *resolved low- and high-$\Sigma_{\rm{SFR}}$ galaxy regions* across the sample. To split the sample into low- and high-$\Sigma_{\rm{SFR}}$ galaxy regions we first convert all (2 $\sigma$-masked) \[Cii\] maps to $\Sigma_{\rm{SFR}}$ maps using the average $L_{\rm [CII]}$–SFR trend of (cite: lagache18):

$$\begin{equation}
    \log\left(\dfrac{L_{\rm [CII]}}{\rm{L}_\odot}\right) = (1.4-0.07z)\times\log\left(\dfrac{\rm SFR}{{\rm M}_\odot{\rm yr}^{-1}}\right)+7.1-0.07z,
    \label{eq:lcii-sfr}
\end{equation}$$

and dividing by the pixel area in kpc$^2$. At this point each spatial pixel has a corresponding value of $\Sigma_{\rm{SFR}}$. We then choose the median value of all pixels, $\Sigma_{\rm{SFR}}$ $=$ 1.93 M$_\odot$ yr$^{-1}$ kpc$^{-2}$, as the boundary between low- and high-$\Sigma_{\rm{SFR}}$ galaxy regions. In this regard, low- and high-$\Sigma_{\rm{SFR}}$ are meant not in the absolute sense, but in relation to the sample as a whole. Using data from the SINS/zC-SINF of $z$ $\sim$ 2 galaxies, (cite: newman12) identified a threshold of $\Sigma_{\rm{SFR}}$ $=$ 1 M$_\odot$ yr$^{-1}$ kpc$^{-2}$ above which strong outflows occurred in their sample. As our threshold between low- and high-$\Sigma_{\rm{SFR}}$ is higher than this, in theory we should see outflows in both samples, but in reality our threshold is dependent on our choice of $L_{\rm [CII]}$–SFR calibration. Given this uncertainty we prefer to interpret the results of stacking the low- and high-$\Sigma_{\rm{SFR}}$ subsets in isolation to search for a trend of outflows with $\Sigma_{\rm{SFR}}$, rather than comparing to other studies.

Some galaxies naturally will have pixels that fall into both sub-samples e.g. CRISTAL-08. We impose an additional requirement that to include a galaxy in the low/high-$\Sigma_{\rm{SFR}}$ subsample, the number of pixels that fall below/above the $\Sigma_{\rm{SFR}}$ threshold must be greater than the number of the pixels within the synthesized beam. This is to ensure that the summed spectra have adequate S/N to be used in the stack. The regions of each \[CII\] map that are classified as low-$\Sigma_{\rm{SFR}}$ and high-$\Sigma_{\rm{SFR}}$ are highlighted in Figs. [5](#fig:stack_low_sfr) and [6](#fig:stack_high_sfr).

Fig. [5](#fig:stack_low_sfr) shows the composite of all regions of the sample with $\Sigma_{\rm{SFR}}$ $<$ 1.93 M$_\odot$ yr$^{-1}$ kpc$^{-2}$, which includes 11 of the 15 galaxies used in the previous stack. Contrary to Fig. [3](#fig:stack_all_2sig), we see no evidence for broad components in this composite, with the residuals appearing random for both models and $\Delta{\rm BIC}$ $=$ $-11$. On the other hand, Fig. [6](#fig:stack_high_sfr) shows the composite of all regions of the sample with $\Sigma_{\rm{SFR}}$ $>$ 1.93 M$_\odot$ yr$^{-1}$ kpc$^{-2}$. This sample includes 9 of the original 15 sources, including CRISTAL-02 that shows a strong broad feature in its integrated spectrum (Davies et al. in prep.). This composite spectrum displays a broad feature with FWHM$_{\rm narrow}$ $=$ 245 $\pm$ 11 km s$^{-1}$ and FWHM$_{\rm broad}$ $=$ 585 $\pm$ 76 km s$^{-1}$, broader than the full-sample stack but still consistent within the uncertainties. As with the full-sample stack, the combined residuals from single-Gaussian fits to each were consistent with the residuals from fitting a single-Gaussian model to both the low-$\Sigma_{\rm{SFR}}$ and high-$\Sigma_{\rm{SFR}}$ samples. We note that it is entirely possible that this observation, namely the higher significance of broad emission in the low-$\Sigma_{\rm{SFR}}$ sample, is simply due to the \[CII\] emission being brighter in those galaxies (as a result of using \[CII\] to trace SFR). This would make any fainter broad emission easier to detect. Despite this, the low-$\Sigma_{\rm{SFR}}$ and high-$\Sigma_{\rm{SFR}}$ stacks have similar S/N, 39 and 37 respectively. Therefore, both stacks should have similar ability to yield broad line detections.

We conducted a similar test by dividing each galaxy into inner and outer regions. This division was achieved by sorting flux density values into two bins *on a source-by-source basis*, with the fainter bin representing the outer regions and the brighter bin corresponding to the inner regions. We visually inspected the resulting masks to ensure this division was accurate. In doing so, we found statistically moderate evidence of broad emission in the inner regions ($\Delta{\rm BIC}$ $=$ 5.1), but not in the outer regions, as shown in Figs. [11](#fig:stack_outer) and [12](#fig:stack_inner). This suggests that outflows predominantly originate from the center of the galaxy (which are also generally the regions with the highest $\Sigma_{\rm{SFR}}$).

c\|c\|c\|c\|c\|c\|c\|c\|c Sample & $N_{\rm gal}$ & $z_{\rm med}$ & & & $\Delta$(BIC) & Result & &\
\
Full sample & 15 & 5.230 & 52 $^{+24}_{-26}$ & 7 $^{+13}_{-4}$ & 0.4 & *Double* & 229 $\pm$ 12 & 543 $\pm$ 71\
Low-SFR & 11 & 5.230 & 35 $^{+40}_{-16}$ & 6 $^{+4}_{-3}$ & -8.8 & Single & 293 $\pm$ 14 &\
High-SFR & 9 & 4.580 & 59 $^{+17}_{-26}$ & 8 $^{+11}_{-3}$ & 8.2 & *Double* & 219 $\pm$ 14 & 492 $\pm$ 49\
\
Full sample & 15 & 5.230 & 52 $^{+24}_{-26}$ & 7 $^{+13}_{-4}$ & -2.3 & Single & 268 $\pm$ 8 &\
Low-SFR & 11 & 5.230 & 35 $^{+40}_{-16}$ & 6 $^{+4}_{-3}$ & -10.9 & Single & 297 $\pm$ 18 &\
High-SFR & 9 & 4.580 & 59 $^{+17}_{-26}$ & 8 $^{+11}_{-3}$ & -1.3 & Single & 250 $\pm$ 10 &\
\
Full sample & 15 & 5.230 & 52 $^{+24}_{-26}$ & 7 $^{+13}_{-4}$ & -7.7 & Single & 276 $\pm$ 11 &\
Low-SFR & 11 & 5.230 & 35 $^{+40}_{-16}$ & 6 $^{+4}_{-3}$ & -11.1 & Single & 289 $\pm$ 17 &\
High-SFR & 9 & 4.580 & 59 $^{+17}_{-26}$ & 8 $^{+11}_{-3}$ & -0.2 & Single & 256 $\pm$ 7 &\
\
Full sample & 15 & 5.230 & 52 $^{+24}_{-26}$ & 7 $^{+13}_{-4}$ & 17.1 & **Double** & 232 $\pm$ 13 & 501 $\pm$ 62\
Low-SFR & 11 & 5.230 & 35 $^{+40}_{-16}$ & 6 $^{+4}_{-3}$ & -10.6 & Single & 286 $\pm$ 19 &\
High-SFR & 9 & 4.580 & 59 $^{+17}_{-26}$ & 8 $^{+11}_{-3}$ & 8.5 & *Double* & 245 $\pm$ 11 & 585 $\pm$ 76\

## Effects of using different stacking methods

As discussed in §[3.3](#sec:stacking), we chose to test four different methods of normalization when stacking the CRISTAL spectra. The main aim of this test is not to show which method is best, but to characterize how the results vary depending on the choice of normalization. As our goal is to analyze the line *profiles* in our sample, we have chosen to focus on presenting and analyzing the method 4 stacks, in which all lines are normalized to the same width and peak flux density. Indeed, we have already shown the results of the method 4 stacks, in which we find only moderate evidence for broad wings in the integrated spectrum of the entire sample and in the high-$\Sigma_{\rm{SFR}}$ regions of the sample (predominantly the central regions). Here, we provide and compare the individual results for all four methods, which are shown in Table [\[tab:stack_results\]](#tab:stack_results).

If we stack the spectra purely as they are extracted with no changes (method 1), we see moderate evidence for broad emission in both the full sample and high-$\Sigma_{\rm{SFR}}$ sample. This makes sense as not normalizing the linewidths can artificially introduce broad features (cite: jolly20). In this stack the full sample shows FWHM$_{\rm broad}$ $=$ 543 $\pm$ 71 km s$^{-1}$ (broader than using method 4).

After normalizing the linewidths this evidence disappears without any flux normalization (method 2). In this case we would expect any real broad emission to be more clearly distinguished. The broad emission also remains absent when peak flux is multiplied to conserve the total flux (method 3), a method which should reduce the impact of the brighter sources in the sample. The fact that method 4 gives the clearest indication of broad emission in the stack is interesting because this method gives equal weight to all sources and would therefore imply that there is a real underlying broad signal in the full sample. However, it is also very possible that the low S/N of this data is the cause of this result, and the impact of removing CRISTAL-02 from the sample reinforces this idea.

## Comparisons with G20 analysis

The detection of broad \[Cii\] emission in high-redshift galaxies offers a potential signature of large-scale outflows driven by star formation. In a key study, stacked the global \[Cii\] spectra of 50 ALPINE galaxies and found that the composite spectrum is best described by the sum of a narrow Gaussian with FWHM$_{\rm narrow}$ $=$ 233 $\pm$ 15 km s$^{-1}$ and a broad Gaussian with FWHM$_{\rm broad}$ $=$ 531 $\pm$ 90 km s$^{-1}$. They also found even broader emission when stacking only galaxies with SFRs above the sample median.

The analysis has informed the work presented in this paper, but there are a number of important differences between the two projects, most notably in the data quality. The CRISTAL data used in this study has a median synthesized beam FWHM of 0.46 $\times$ 0.40$''$, over a factor of two improvement on the ALPINE data, which has a median of 0.85 $\times$ 1.13$''$ (cite: lefevre20). Therefore, our data probe scales of $\sim$ 3.9 kpc at $z$ $=$ 5, whereas for this value is $\sim$ 9.1 kpc. This finer resolution enables us to better resolve the internal kinematics of galaxies and mitigate the effects of beam smearing, which can artificially broaden line profiles. Indeed, five sources classified as interacting by Lee et al.(in prep.; and therefore excluded from our analysis) were included in the composite.

To test whether the broad features reported by would be recovered under our stacking methodology and data quality, we simulated their composite spectrum using their best-fit Gaussian parameters, added noise consistent with the RMS of our data, and stacked the resulting spectra using our method 4. For this comparison, we focus on the full-sample stack from (their Fig. 5). Given the deeper sensitivity of the CRISTAL data (Herrera-Camus et al. in prep.), we expect to be sensitive to faint broad components in the stack.

The results of this stack are shown in Fig. [7](#fig:g20_sims), showing marginal broad features, slightly less significant than in our full-sample composite. We measure narrow and broad line widths of 223 $\rm{km\,s}^{-1}$ and 495 $\rm{km\,s}^{-1}$ respectively, lower than the input values of 233 $\rm{km\,s}^{-1}$ and 531 $\rm{km\,s}^{-1}$, although this is simply because we normalized all spectra to the same linewidth as in our CRISTAL stacks. In general, Fig. [7](#fig:g20_sims) shows that the outflow signal measured by could be detected with the sensitivity of the CRISTAL data analyzed here. It is difficult, however, to more directly compare this result with Fig. 5 in as they do not include $\Delta{\rm BIC}$ values, but in general we do not see residuals above 3-$\sigma$, whereas they do. Several differences in sample selection, resolution, and methodology may explain these residual discrepancies between the two analyses.

Firstly, the sample utilized by is much larger than ours, 50 versus 15 (11 and 9 in the low- and high-$\Sigma_{\rm{SFR}}$ stacks respectively). As a result, the S/N gain from stacking should be a factor of $\sim$ 1.8 better in the analysis compared to ours. It is also possible that the ALPINE stacking sample includes sources with stronger outflows on average than those selected by CRISTAL. This seems unlikely if, as suggests, the outflows are primarily driven by star formation, because the CRISTAL sources are among the highest-SFR sources of the full ALPINE sample (see Fig. [1](#fig:main_sequence)). A further possibility is that there remain incorrectly classified mergers in the sample. Given that these sources likely have higher SFRs than non-merging sources, this could contribute to their interpretation that outflows are star-formation driven.

Another difference is that the coarser spatial resolution of the original ALPINE data could artificially induce broad components in the spectra, potentially from mergers. The kinematic analysis of the higher-resolution CRISTAL data provided by Lee et al.(in prep.) has allowed us to more accurately exclude mergers from the sample. Unfortunately this comes at the cost of a reduced sample size, meaning that stacking provides a smaller increase in S/N. Due to the mass-based selection of CRISTAL, the proportion of interacting sources in our sample is expected to be higher than that of ALPINE.

Additionally, the two analyses employ different methodologies. did not normalize the linewidths in their stack (most closely resembling our method 1, which could have artificially introduced broad components into their composite (cite: jolly20). However, we tested this method as part of our analysis (see §[4.3](#sec:stacking_methods)) and found that the results did not skew significantly towards double-Gaussian when compared to our method 4.

In summary, while differences in resolution, sample selection, and stacking methodology can influence the interpretation of broad emission components, both studies point toward the tentative presence of galaxy-scale outflows in normal star-forming galaxies at $z$ $\sim$ 5. A definitive understanding of these outflows will require large, statistically robust samples observed at CRISTAL-like resolution. Such a study is well within the capability of ALMA and would represent a critical next step in understanding feedback processes in the early universe.

![](g20_sims_add_rms.pdf)

# Discussion

We now discuss our findings from the various stacks and their implications for the presence or absence of feedback in $z$ $\sim$ 5 main-sequence star-forming galaxies.

## Are outflows responsible for the broad emission?

While we have found modest evidence that a broad component is required to explain the \[CII\] emission in the CRISTAL sample, this does not preclude scenarios other than outflows. In this section we discuss other possibilities and justify interpreting the broad component as an outflow.

On the marginality of the broad detection, we address here the possible biasing of our sample selection. Given our conservative approach to rejecting potential mergers, our final sample comprises strictly disk-like sources with measured inclinations in the range 43$^\circ$–84$^\circ$ (Lee et al. in prep.), meaning that most are closer to being edge-on disks. If true, outflows perpendicular to the disk will have a relatively low velocity along the line-of-sight and therefore be more difficult to detect. This is briefly discussed further in §[5.2](#sec:outflow_velocity).

As discussed in §[3.1](#sec:removing_mergers), the spectra of merging galaxies can combine multiple velocity components due to interacting sources, disturbed gas kinematics, and tidal tails, resulting in broader spectral features that can mimic feedback-driven outflows. While mergers and interactions are known to produce such broad features, our careful approach ensures these effects are minimized. If indeed there are any mergers remaining in the sample after the selection, they must be close mergers ($<$ 0.4$''$) with a small offset between velocity components ($\sim$ 100 km s$^{-1}$). Such a merger would likely involve a minor component (if not visible spatially and kinematically) and/or would not significantly broaden the line given the small velocity offset. A similar argument can be made for tidal tails.

Additionally, AGN feedback can produce very rapid outflows of gas which if present, may appear in our composite spectrum. However, AGN-driven winds can often reach thousands of $\rm{km\,s}^{-1}$(cite: bischetti19), whereas our stacks only show excess emission at velocities of a few hundred $\rm{km\,s}^{-1}$. Additionally, the majority of the sample appear to show \[NII\]/H$\alpha$ and \[OIII\]/H$\beta$ ratios that place them within the star-formation section of the classical BPT diagram (Faisst et al. in prep.).

## Outflow velocity

If we interpret the weak detection of a broad component in the composite spectrum of highly star-forming regions as outflowing gas driven by stellar feedback, we can estimate some basic properties of the potential outflow. Following (cite: lutz20) we measure the outflow velocity as:

$$\begin{equation}
    v_{\rm out} = |\Delta v| + 0.5{\rm FW}_{10\%},
    \label{eq:v_out}
\end{equation}$$

![](v_out_sig_sfr.pdf)

where $\Delta v$ is the velocity offset of the broad component and FW$_{10\%}$ is the full-width at 10$\%$ of the peak flux density. For the method 4 stacks of the full sample we find $v_{\rm out}$ $=$ 490 $\pm$ 59 km s$^{-1}$ and for the high-$\Sigma_{\rm{SFR}}$ sample we find $v_{\rm out}$ $=$ 607 $\pm$ 80 km s$^{-1}$. This is expected if sources with higher star-formation rates drive more powerful outflows, although the two values are consistent within the 1-$\sigma$ uncertainties.

As noted in §[5.1](#sec:outflows?), our sample selection results in disks that are inclined somewhere roughly in the center of edge-on and face-on. If the apparent outflows are perpendicular to the disk then some component on the outflow velocity would not be in the line-of-sight and therefore not detectable in our data. In this case, an inclination correction would be required. For the CRISTAL disks, Lee et al.(in prep.) measured a median inclination of 54$^\circ$, implying a median velocity correction of 1/sin$^2$(54$^\circ$) = 1.24. Applying this would instead yield outflow velocities of $v_{\rm out}$ $=$ 608 $\pm$ 73 km s$^{-1}$ for the full sample and $v_{\rm out}$ $=$ 753 $\pm$ 99 km s$^{-1}$ for the high-$\Sigma_{\rm{SFR}}$ sample.

Fig. [8](#fig:v_out_sig_sfr) presents the outflow velocity of the two composites as a function of the star-formation rate surface density, $\Sigma_{\rm{SFR}}$. $\Sigma_{\rm{SFR}}$ is calculated as the median value across all pixels included in the stack, with the 16th and 84th percentiles indicated by the error bars. Also included are SINFONI H$\alpha$ measurements by (cite: davies19) for $z$ $\sim$ 2–2.6 star-forming galaxies, and a literature compilation of $z$ $<$ 1.5 star-forming galaxies from (cite: schroetter24) (mostly measured from absorption lines of background QSOs). The CRISTAL composites match well with the literature data, and sit close to the measured trend of increasing outflow velocity with star-formation rate surface density measured by both (cite: heckman16) and (cite: chu24). Although this is not a highly constraining result, it is useful to see that, if interpreted as outflows, our composite properties are comparable to similar samples in the literature.

## Mass outflow rate

Following we estimate the atomic gas mass of the outflowing region using the following relation from (cite: hailey-dunsheath10):

$$\begin{equation}
    \begin{split}
            \dfrac{M_{\rm out}^{\rm atom}}{{\rm M}_\odot} &= 0.7\left(\dfrac{0.7L_{\rm [CII]}}{{\rm L}_\odot}\right) \times \left(\dfrac{1.4\times10^{-4}}{X_{C^+}}\right) \times \\ & \dfrac{1+2e^{-91{\rm K}/T}+n_{\rm crit}/n}{2e^{-91{\rm K}/T}},
    \end{split}
    \label{eq:outflow_mass}
\end{equation}$$

where the \[CII\] luminosity $L_{\rm [CII]}$ is derived from the integral of the outflowing regions. We assume a C$^+$ abundance per hydrogen atom of $X_{C^+}$ $=$ 1.4 $\times$ 10$^{-4}$, a gas density $n$ equal to the critical density $n_{\rm crit}$ $=$ 3 $\times$ 10$^3$ cm$^{-2}$, and a gas temperature of 100 K (cite: ginolfi20). To derive the mass of the outflowing material, we consider the entire broad component of the fit for consistency with . For an alternative measurement, we use Eq. [\[eq:outflow_mass\]](#eq:outflow_mass) only including velocity channels where the broad component accounts for at least half of the total flux density, following (cite: lutz20). This latter approach is more conservative as it aims to exclude flux density contributions from the main component of the galaxy. In Figs. [9](#fig:m_out_dot_sfr) and [10](#fig:mass_load_mstar), the downward-pointing red arrows indicate the extent to which this approach reduces the measured values.

We then compute the mass outflow rate as (cite: gallerani18): $$\begin{equation}
    \dot{M}_{\rm out} = \dfrac{v_{\rm out}M_{\rm out}}{R_{\rm out}},
    \label{eq:mass_outflow_rate}
\end{equation}$$ where $M_{\rm out}$ is derived using Eq. [\[eq:outflow_mass\]](#eq:outflow_mass). We adopt $R_{\rm out}$ $=$ 6 kpc, following .

The resulting mass outflow rates are $\dot{M}_{\rm out}$ $=$ 26 $\pm$ 11 M$_\odot$ yr$^{-1}$ for the full sample and $\dot{M}_{\rm out}$ $=$ 28 $\pm$ 10 M$_\odot$ yr$^{-1}$ for the low-$\Sigma_{\rm{SFR}}$ sample, although it is important to note that these values assume that only the atomic phase contributes to the outflows. To account for the other ISM phases, we follow recent work by (cite: fluetsch19), applying a factor of 3 to the atomic outflow rates, yielding total outflow rates of $\dot{M}_{\rm out}$ $=$ 78 $\pm$ 33 M$_\odot$ yr$^{-1}$ for the full sample and $\dot{M}_{\rm out}$ $=$ 85 $\pm$ 31 M$_\odot$ yr$^{-1}$ for the low-$\Sigma_{\rm{SFR}}$ sample. We stress that such a correction is based on CO observations of local galaxies, over half of which are Seyferts and LINERs. and therefore may not be applicable to our $z$ $\sim$ 5 sample. Further, an analysis of multi-phase outflows in M82 by (cite: levy23) found that the corresponding factor would only be $\sim$ 2 (cite: leroy15; martini18). In Figs. [9](#fig:m_out_dot_sfr) and [10](#fig:mass_load_mstar), the upward-pointing red arrows indicate the extent to which applying the factor of 3 increases the values.

Our mass outflow rate measurements are shown as a function of star-formation rate in Fig. [9](#fig:m_out_dot_sfr). Data from the CRISTAL survey are plotted as filled red circles for the entire sample and open red circles for regions with high star-formation rates. Additional outflow measurements from (cite: fluetsch19) and are shown, along with ionized outflow measurements from (cite: swinbank19) and (cite: weldon24) (at slightly lower redshifts of $z$ $\sim$ 1–4), although we note that the latter trace a hotter phase of outflowing material, coming from regions more directly impacted by energetic feedback processes like supernovae and stellar winds. This is in contrast with our \[CII\] data, which traces colder outflows. $\dot{M}_{\rm out}$ and SFR are generally positively correlated, and indeed our sample shows higher outflow rates than lower-SFR literature samples. The high-$\Sigma_{\rm{SFR}}$ subset of CRISTAL also shows a marginally higher $\dot{M}_{\rm out}$ than the full sample, although the two composites are consistent within their uncertainties. Further, our measured $\dot{M}_{\rm out}$ are consistent with those measured by . Compared to the other samples, particularly (cite: weldon24), our composites imply higher mass-loading factors than star-forming galaxies at lower redshifts, if indeed the broad emission we detect is driven by outflows. We discuss this further in the next section.

![](m_out_dot_sfr.pdf)

![](mass_load_mstar.pdf)

## Mass-loading factor

The efficiency of a star-formation driven outflow is typically quantified by the mass-loading factor $\eta_m$ $=$ $\dot{M}_{\rm out}/$SFR, that can be intuitively understood as the amount of mass removed per stellar mass newly formed.

For the integrated stack presented in Fig. [3](#fig:stack_all_2sig) we adopt the median SFR of the sample, 52 M$_\odot$ yr$^{-1}$. This gives a mass-loading factor of $\eta_m$ $=$ 0.49 $\pm$ 0.20 indicating the mass is lost at a slower rate than new stars are formed. When conservatively multiplying this number by a factor of 3 to account for multi-phase outflows (cite: fluetsch19) this would give $\eta_m$ $=$ 1.48 $\pm$ 0.61, consistent with scenarios ranging from no significant overall mass loss to moderate mass loss with time. Given that the (cite: fluetsch19) calibration factor is conservative, we suggest that the former scenario is more likely. For the higher-$\Sigma_{\rm{SFR}}$ sample, we find a similar mass-loading factor of $\eta_m$ $=$ 0.48 $\pm$ 0.18, implying comparable feedback efficiency between the two samples.

In Fig. [10](#fig:mass_load_mstar) we show the relationship between stellar mass and the mass-loading factor. Data from the CRISTAL survey are plotted as filled red circles for the entire sample and open red circles for regions with higher star-formation rates, both exhibiting moderate uncertainties around $\eta_m$ $=$ 0.5. Additional data points from (cite: swinbank19), (cite: concas22) and (cite: weldon24) are shown, although we again note that these additional data are derived from ionized gas, which traces a hotter phase of the interstellar medium.

For a closer comparison with our data we include results from (cite: romano23) in Fig. [10](#fig:mass_load_mstar), which were measured from observations of the \[CII\] emission line in local dwarf galaxies. These systems have stellar masses that are around an order of magnitude lower than the CRISTAL sample, but they generally have comparable mass-loading factors to CRISTAL, and both datasets lie close to the (cite: weldon24) relation. This alignment implies that the feedback efficiency, as represented by $\eta_m$, scales with stellar mass in a consistent manner across cosmic time for the two galaxy types, even though the two samples differ significantly in redshift and galaxy properties.

Theoretical predictions from the FIRE-1 (cite: muratov15) and FIRE-2 (cite: pandya21) simulations are indicated by the dashed gray and black lines, both of which predict a decrease in the mass loading factor as stellar mass increases. This can be interpreted to mean that stellar feedback is more efficient at driving gas outflows in low-mass systems due to their shallower gravitational potential wells. The predictions from FIRE-2 in particular match our full-sample composite reasonably well, but only when adjusted to account for contributions from other phases of outflowing gas.

## Contribution of outflows to observed extended \[CII\] emission

A recent development in the study of high-redshift galaxy evolution is the discovery of apparent extended \[CII\] halos on scales of $\sim$ 10 kpc. By stacking ALMA data from 18 galaxies at $z$ $\sim$ 5–7, (cite: fujimoto19) provided the first evidence for this phenomenon, along with several potential driving mechanisms. Currently there is very little consensus on which mechanism is most important, but perhaps the most discussed is outflows removing gas to large radii from the galaxy without it escaping the halo entirely. (cite: pizzati20; pizzati23) developed a semi-analytic model in which supernova-driven outflows can reproduce the \[CII\] halos. In their stacking analysis used the observed detection of broad emission to suggest that the baryon cycle is already in place in the CGM of normal star-forming galaxies at $z$ $\sim$ 5.

However, utilizing the CRISTAL sample, (cite: ikeda24) found that the \[CII\] line emission is well-described by a single extended disk component, implying that the aforementioned halos are not as significant as previously thought. Further, they found no correlation between the ratio of $R_{\rm e,[CII]}/R_{\rm e,UV}$ and SFR or $\Sigma_{\rm SFR,IR}$, which they interpreted to suggest that \[CII\] outflows are not the cause of extended emission in the sample. This is clearly consistent with the lack of strong outflows in our full-sample stack (when excluding CRISTAL-02).

# Conclusions

We have carried out a stacking analysis of ALMA Band 7 data from the CRISTAL survey of $z$ $\sim$ 5 main-sequence star-forming galaxies. The data cover the forbidden line from singly ionized carbon \[CII\](rest-frame 158 $\mu$m), which we use to search for outflow signatures in the form of broad wings. Our main conclusions are as follows:

- We adopt a conservative stacking approach, leveraging kinematic analysis of the higher-resolution CRISTAL data (compared to ALPINE) to remove 22 systems which are potentially interacting/merging, leaving a final sample size of 15. When included in a stack, these sources can easily mimic broad wings. Given that CRISTAL-02 is already known to drive a prominent outflow, we perform our stacking analysis both with and without this source.

- Given the different redshifts, masses and luminosities of the CRISTAL sources, we test several methods for aggregating the emission line profiles when stacking, including standardizing all linewidths. We find that the chosen method can meaningfully affect the conclusion on whether or not outflows are present, and therefore extreme care must be taken. We prefer to normalize both the linewidths and peak flux densities to a constant value, to ensure that we are probing only the average *shape* of the emission line profiles.

- After excluding potential mergers from the sample and combining the integrated spectra, the resultant composite shows weak evidence for outflows with $\Delta{\rm BIC}$ $=$ 17. Evidence with this significance is *only* present when normalizing the linewidths and peak flux densities – all other stacking methods show little-to-no evidence of broad emission in the composites. We measure an outflow velocity (not corrected for inclination) of $v_{\rm out}$ $=$ 490 $\pm$ 59 km s$^{-1}$, which is consistent with literature measurements for galaxies with similar $\Sigma_{\rm{SFR}}$. The result is also almost entirely driven by CRISTAL-02, without which the significance drops to $\Delta{\rm BIC}$ $=$ 3.1.

- We compare our stacking results with those obtained from the ALPINE survey by , aiming to identify any systematic differences related to data quality. Although the CRISTAL data offer higher resolution and therefore allow for more effective identification and removal of mergers, our stack reveals less significant broad emission than that reported by . Moreover, when we inject RMS noise comparable to the CRISTAL data into their composite signal, the resulting stack also shows less significant residuals than those presented in . We suggest that sample size, selection and methodology all contribute to these differences.

- We find a mass outflow rate of $\dot{M}_{\rm out}$ $=$ 26 $\pm$ 11 M$_\odot$ yr$^{-1}$ and mass loading factor of $\eta$ $=$ 0.49 $\pm$ 0.20, indicating feedback that, while relatively weak and unlikely to quench star formation, could still regulate the system over long timescales by moderating the gas supply available for star formation.

- We exploit the high resolution of the CRISTAL data to generate \[CII\] luminosity maps, which we use as a proxy for star-formation maps. By defining a threshold in star-formation rate, we stack the individual *spatial pixels* from the sample which are most highly star forming. When only considering the \[CII\]-brightest regions of the sample (again excluding mergers) which should broadly represent the most highly star forming, the resultant composite spectrum also shows moderate evidence for outflows, $\Delta{\rm BIC}$ $=$ 9, with $v_{\rm out}$ $=$ 607 $\pm$ 80 km s$^{-1}$, $\dot{M}_{\rm out}$ $=$ 28 $\pm$ 10 M$_\odot$ yr$^{-1}$, $\eta$ $=$ 0.48 $\pm$ 0.18. This could suggest that the potential outflows are driven by star formation.

Few sources in the CRISTAL sample individually show evidence for outflows. The analysis presented here indicates that any further evidence would need to be revealed with deeper \[Cii\] observations and/or larger stacking samples. JWST/NIRSpec data covering H$\alpha$, \[NII\], H$\beta$ and \[OIII\] has recently become available which will push forward our picture of the CRISTAL sample, namely allowing the ruling out of any substantial AGN activity using line ratio diagnostics, the measurement of metallicities, and searching for outflows in the ionized phase.

We would like to thank Michele Ginolfi for useful discussions regarding the ALPINE stacking analysis. M.A. acknowledges support from ANID Basal Project FB210003 and and ANID MILENIO NCN2024_112. T.D.S. acknowledges the research project was supported by the Hellenic Foundation for Research and Innovation (HFRI) under the "2nd Call for HFRI Research Projects to support Faculty Members & Researchers" (Project Number: 03382). R.L.D. is supported by the Australian Research Council through the Discovery Early Career Researcher Award (DECRA) Fellowship DE240100136 funded by the Australian Government. A.F. acknowledges support from the ERC Advanced Grant INTERSTELLAR H2020/740120. Partial support from the Carl Friedrich von Siemens-Forschungspreis der Alexander von Humboldt-Stiftung Research Award is kindly acknowledged. J.G-L., acknowledges support from ANID BASAL project FB210003 and Programa de Inserción Académica 2024 Vicerrectoría Académica y Prorrectoría Pontificia Universidad Católica de Chile. R.I. is supported by Grants-in-Aid for Japan Society for the Promotion of Science (JSPS) Fellows (KAKENHI Grant Number 23KJ1006). K.K. acknowledges support from the Knut and Alice Wallenberg Foundation (KAW 2017.0292). I.D.L. acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation program DustOrigin (ERC-2019- StG-851622) and from the Flemish Fund for Scientific Research (FWO-Vlaanderen) through the research project G0A1523N. M.R. acknowledges support from project PID2023-150178NB-I00 and PID2020-114414GB-I00, financed by MCIN/AEI/10.13039/501100011033. M.S. was financially supported by Becas-ANID scholarship #21221511, and also acknowledges support from ANID BASAL project FB210003. K.T. acknowledges support from JSPS KAKENHI grant No. 23K03466. V.V. acknowledges support from the ALMA-ANID Postdoctoral Fellowship under the award ASTRO21-0062.

# Facilities

ALMA

# Software

`astropy` (cite: astropy18), CASA (cite: casa)

# Inner and outer galaxy stacks

![](mask_outer_vel_res_med.pdf)

![](mask_inner_vel_res_med.pdf)

natexlab

(ref: angles-alcazar17) Anglés-Alcázar, D., Faucher-Giguère, C.-A., Kereš, D., et al. 2017, MNRAS, 470, 4698, doi: [`10.1093/mnras/stx1517`](http://doi.org/10.1093/mnras/stx1517)

(ref: astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: avery21) Avery, C. R., Wuyts, S., Förster Schreiber, N. M., et al. 2021, MNRAS, 503, 5134, doi: [`10.1093/mnras/stab780`](http://doi.org/10.1093/mnras/stab780)

(ref: bethermin20) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2, doi: [`10.1051/0004-6361/202037649`](http://doi.org/10.1051/0004-6361/202037649)

(ref: birkin21) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2021, MNRAS, 501, 3926, doi: [`10.1093/mnras/staa3862`](http://doi.org/10.1093/mnras/staa3862)

(ref: bischetti19) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59, doi: [`10.1051/0004-6361/201833557`](http://doi.org/10.1051/0004-6361/201833557)

(ref: carniani24) Carniani, S., Venturi, G., Parlanti, E., et al. 2024, A&A, 685, A99, doi: [`10.1051/0004-6361/202347230`](http://doi.org/10.1051/0004-6361/202347230)

(ref: cicone15) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14, doi: [`10.1051/0004-6361/201424980`](http://doi.org/10.1051/0004-6361/201424980)

(ref: concas22) Concas, A., Maiolino, R., Curti, M., et al. 2022, MNRAS, 513, 2535, doi: [`10.1093/mnras/stac1026`](http://doi.org/10.1093/mnras/stac1026)

(ref: cormier19) Cormier, D., Abel, N. P., Hony, S., et al. 2019, A&A, 626, A23, doi: [`10.1051/0004-6361/201834457`](http://doi.org/10.1051/0004-6361/201834457)

(ref: croxall17) Croxall, K. V., Smith, J. D., Pellegrini, E., et al. 2017, ApJ, 845, 96, doi: [`10.3847/1538-4357/aa8035`](http://doi.org/10.3847/1538-4357/aa8035)

(ref: curti20a) Curti, M., Mannucci, F., Cresci, G., & Maiolino, R. 2020, MNRAS, 491, 944, doi: [`10.1093/mnras/stz2910`](http://doi.org/10.1093/mnras/stz2910)

(ref: dalcanton07) Dalcanton, J. J. 2007, ApJ, 658, 941, doi: [`10.1086/508913`](http://doi.org/10.1086/508913)

(ref: davies19) Davies, R. L., Förster Schreiber, N. M., Übler, H., et al. 2019, ApJ, 873, 122, doi: [`10.3847/1538-4357/ab06f1`](http://doi.org/10.3847/1538-4357/ab06f1)

(ref: decarli18) Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: dekel1986) Dekel, A., & Silk, J. 1986, ApJ, 303, 39, doi: [`10.1086/164050`](http://doi.org/10.1086/164050)

(ref: diaz-santos17) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32, doi: [`10.3847/1538-4357/aa81d7`](http://doi.org/10.3847/1538-4357/aa81d7)

(ref: ellison08) Ellison, S. L., Patton, D. R., Simard, L., & McConnachie, A. W. 2008, ApJL, 672, L107, doi: [`10.1086/527296`](http://doi.org/10.1086/527296)

(ref: faisst20) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61, doi: [`10.3847/1538-4365/ab7ccd`](http://doi.org/10.3847/1538-4365/ab7ccd)

(ref: finlator08) Finlator, K., & Davé, R. 2008, MNRAS, 385, 2181, doi: [`10.1111/j.1365-2966.2008.12991.x`](http://doi.org/10.1111/j.1365-2966.2008.12991.x)

(ref: fluetsch19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586, doi: [`10.1093/mnras/sty3449`](http://doi.org/10.1093/mnras/sty3449)

(ref: foreman-mackey13) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306, doi: [`10.1086/670067`](http://doi.org/10.1086/670067)

(ref: forster-schreiber19) Förster Schreiber, N. M., Übler, H., Davies, R. L., et al. 2019, ApJ, 875, 21, doi: [`10.3847/1538-4357/ab0ca2`](http://doi.org/10.3847/1538-4357/ab0ca2)

(ref: fujimoto19) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107, doi: [`10.3847/1538-4357/ab480f`](http://doi.org/10.3847/1538-4357/ab480f)

(ref: gallerani18) Gallerani, S., Pallottini, A., Feruglio, C., et al. 2018, MNRAS, 473, 1909, doi: [`10.1093/mnras/stx2458`](http://doi.org/10.1093/mnras/stx2458)

(ref: genzel11) Genzel, R., Newman, S., Jones, T., et al. 2011, ApJ, 733, 101, doi: [`10.1088/0004-637X/733/2/101`](http://doi.org/10.1088/0004-637X/733/2/101)

(ref: ginolfi20) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90, doi: [`10.1051/0004-6361/201936872`](http://doi.org/10.1051/0004-6361/201936872)

(ref: hailey-dunsheath10) Hailey-Dunsheath, S., Nikola, T., Stacey, G. J., et al. 2010, ApJL, 714, L162, doi: [`10.1088/2041-8205/714/1/L162`](http://doi.org/10.1088/2041-8205/714/1/L162)

(ref: heckman16) Heckman, T. M., & Borthakur, S. 2016, ApJ, 822, 9, doi: [`10.3847/0004-637X/822/1/9`](http://doi.org/10.3847/0004-637X/822/1/9)

(ref: henriques13) Henriques, B. M. B., White, S. D. M., Thomas, P. A., et al. 2013, MNRAS, 431, 3373, doi: [`10.1093/mnras/stt415`](http://doi.org/10.1093/mnras/stt415)

(ref: herrera-camus21) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31, doi: [`10.1051/0004-6361/202039704`](http://doi.org/10.1051/0004-6361/202039704)

(ref: ikeda24) Ikeda, R., Tadaki, K.-i., Mitsuhashi, I., et al. 2024, arXiv e-prints, arXiv:2408.03374, doi: [`10.48550/arXiv.2408.03374`](http://doi.org/10.48550/arXiv.2408.03374)

(ref: jolly20) Jolly, J.-B., Knudsen, K. K., & Stanley, F. 2020, MNRAS, 499, 3992, doi: [`10.1093/mnras/staa2908`](http://doi.org/10.1093/mnras/staa2908)

(ref: kade23) Kade, K., Knudsen, K. K., Vlemmings, W., et al. 2023, A&A, 673, A116, doi: [`10.1051/0004-6361/202141839`](http://doi.org/10.1051/0004-6361/202141839)

(ref: lagache18) Lagache, G., Cousin, M., & Chatzikos, M. 2018, A&A, 609, A130, doi: [`10.1051/0004-6361/201732019`](http://doi.org/10.1051/0004-6361/201732019)

(ref: lefevre20) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1, doi: [`10.1051/0004-6361/201936965`](http://doi.org/10.1051/0004-6361/201936965)

(ref: lequeux1978) Lequeux, J., Peimbert, M., Rayo, J. F., Serrano, A., & Torres-Peimbert, S. 1979, A&A, 80, 155

(ref: leroy15) Leroy, A. K., Walter, F., Martini, P., et al. 2015, ApJ, 814, 83, doi: [`10.1088/0004-637X/814/2/83`](http://doi.org/10.1088/0004-637X/814/2/83)

(ref: leung19) Leung, G. C. K., Coil, A. L., Aird, J., et al. 2019, ApJ, 886, 11, doi: [`10.3847/1538-4357/ab4a7c`](http://doi.org/10.3847/1538-4357/ab4a7c)

(ref: levy23) Levy, R. C., Bolatto, A. D., Tarantino, E., et al. 2023, ApJ, 958, 109, doi: [`10.3847/1538-4357/acff6e`](http://doi.org/10.3847/1538-4357/acff6e)

(ref: lilly13) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119, doi: [`10.1088/0004-637X/772/2/119`](http://doi.org/10.1088/0004-637X/772/2/119)

(ref: lutz20) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134, doi: [`10.1051/0004-6361/201936803`](http://doi.org/10.1051/0004-6361/201936803)

(ref: maiolino12) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66, doi: [`10.1111/j.1745-3933.2012.01303.x`](http://doi.org/10.1111/j.1745-3933.2012.01303.x)

(ref: mannucci10) Mannucci, F., Cresci, G., Maiolino, R., Marconi, A., & Gnerucci, A. 2010, MNRAS, 408, 2115, doi: [`10.1111/j.1365-2966.2010.17291.x`](http://doi.org/10.1111/j.1365-2966.2010.17291.x)

(ref: martini18) Martini, P., Leroy, A. K., Mangum, J. G., et al. 2018, ApJ, 856, 61, doi: [`10.3847/1538-4357/aab08e`](http://doi.org/10.3847/1538-4357/aab08e)

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: meyer22) Meyer, R. A., Walter, F., Cicone, C., et al. 2022, ApJ, 927, 152, doi: [`10.3847/1538-4357/ac4e94`](http://doi.org/10.3847/1538-4357/ac4e94)

(ref: mitsuhashi24) Mitsuhashi, I., Tadaki, K.-i., Ikeda, R., et al. 2024, A&A, 690, A197, doi: [`10.1051/0004-6361/202348782`](http://doi.org/10.1051/0004-6361/202348782)

(ref: muratov15) Muratov, A. L., Kereš, D., Faucher-Giguère, C.-A., et al. 2015, MNRAS, 454, 2691, doi: [`10.1093/mnras/stv2126`](http://doi.org/10.1093/mnras/stv2126)

(ref: newman12) Newman, S. F., Genzel, R., Förster-Schreiber, N. M., et al. 2012, ApJ, 761, 43, doi: [`10.1088/0004-637X/761/1/43`](http://doi.org/10.1088/0004-637X/761/1/43)

(ref: novak20) Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131, doi: [`10.3847/1538-4357/abc33f`](http://doi.org/10.3847/1538-4357/abc33f)

(ref: oppenheimer10) Oppenheimer, B. D., Davé, R., Kereš, D., et al. 2010, MNRAS, 406, 2325, doi: [`10.1111/j.1365-2966.2010.16872.x`](http://doi.org/10.1111/j.1365-2966.2010.16872.x)

(ref: pandya21) Pandya, V., Fielding, D. B., Anglés-Alcázar, D., et al. 2021, MNRAS, 508, 2979, doi: [`10.1093/mnras/stab2714`](http://doi.org/10.1093/mnras/stab2714)

(ref: pizzati20) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 495, 160, doi: [`10.1093/mnras/staa1163`](http://doi.org/10.1093/mnras/staa1163)

(ref: pizzati23) —. 2023, MNRAS, 519, 4608, doi: [`10.1093/mnras/stac3816`](http://doi.org/10.1093/mnras/stac3816)

(ref: posses24) Posses, A., Aravena, M., González-López, J., et al. 2024, arXiv e-prints, arXiv:2403.03379, doi: [`10.48550/arXiv.2403.03379`](http://doi.org/10.48550/arXiv.2403.03379)

(ref: chu24) Reichardt Chu, B., Fisher, D. B., Chisholm, J., et al. 2024, arXiv e-prints, arXiv:2402.17830, doi: [`10.48550/arXiv.2402.17830`](http://doi.org/10.48550/arXiv.2402.17830)

(ref: romano23) Romano, M., Nanni, A., Donevski, D., et al. 2023, A&A, 677, A44, doi: [`10.1051/0004-6361/202346143`](http://doi.org/10.1051/0004-6361/202346143)

(ref: schroetter24) Schroetter, I., Bouché, N. F., Zabl, J., et al. 2024, A&A, 687, A39, doi: [`10.1051/0004-6361/202348725`](http://doi.org/10.1051/0004-6361/202348725)

(ref: speagle14) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15, doi: [`10.1088/0067-0049/214/2/15`](http://doi.org/10.1088/0067-0049/214/2/15)

(ref: spilker20) Spilker, J. S., Aravena, M., Phadke, K. A., et al. 2020, ApJ, 905, 86, doi: [`10.3847/1538-4357/abc4e6`](http://doi.org/10.3847/1538-4357/abc4e6)

(ref: stanley19) Stanley, F., Jolly, J. B., König, S., & Knudsen, K. K. 2019, A&A, 631, A78, doi: [`10.1051/0004-6361/201834530`](http://doi.org/10.1051/0004-6361/201834530)

(ref: sugahara19) Sugahara, Y., Ouchi, M., Harikane, Y., et al. 2019, ApJ, 886, 29, doi: [`10.3847/1538-4357/ab49fe`](http://doi.org/10.3847/1538-4357/ab49fe)

(ref: swinbank19) Swinbank, A. M., Harrison, C. M., Tiley, A. L., et al. 2019, MNRAS, 487, 381, doi: [`10.1093/mnras/stz1275`](http://doi.org/10.1093/mnras/stz1275)

(ref: telikova24) Telikova, K., González-López, J., Aravena, M., et al. 2024, arXiv e-prints, arXiv:2411.09033, doi: [`10.48550/arXiv.2411.09033`](http://doi.org/10.48550/arXiv.2411.09033)

(ref: torrey19) Torrey, P., Vogelsberger, M., Marinacci, F., et al. 2019, MNRAS, 484, 5587, doi: [`10.1093/mnras/stz243`](http://doi.org/10.1093/mnras/stz243)

(ref: tremonti04) Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al. 2004, ApJ, 613, 898, doi: [`10.1086/423264`](http://doi.org/10.1086/423264)

(ref: tripodi22) Tripodi, R., Feruglio, C., Fiore, F., et al. 2022, A&A, 665, A107, doi: [`10.1051/0004-6361/202243920`](http://doi.org/10.1051/0004-6361/202243920)

(ref: veilleux20) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2, doi: [`10.1007/s00159-019-0121-9`](http://doi.org/10.1007/s00159-019-0121-9)

(ref: weldon24) Weldon, A., Reddy, N. A., Coil, A. L., et al. 2024, arXiv e-prints, arXiv:2404.05725, doi: [`10.48550/arXiv.2404.05725`](http://doi.org/10.48550/arXiv.2404.05725)

</paper>

Write the methods card for this paper.