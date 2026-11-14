# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...682L...3P\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024A&A...682L...3P",
 "title": "Ordered magnetic fields around the 3C 84 central black hole",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Paraschos, G. F.",
 "n_authors": 283,
 "arxiv_id": "2402.00927",
 "doi": "10.1051/0004-6361/202348308",
 "alma_projects_linked_by_archive": [
  "2016.1.01154.V"
 ]
}
```

Paper text:
<paper>
# Ordered magnetic fields around the 3C 84 central black hole

3C 84 is a nearby radio source with a complex total intensity structure, showing linear polarisation and spectral patterns. A detailed investigation of the central engine region necessitates the use of very-long-baseline interferometry (VLBI) above the hitherto available maximum frequency of 86 GHz. Using ultrahigh resolution VLBI observations at the currently highest available frequency of 228 GHz, we aim to perform a direct detection of compact structures and understand the physical conditions in the compact region of 3C 84. We used Event Horizon Telescope (EHT) 228 GHz observations and, given the limited $(u, v)$-coverage, applied geometric model fitting to the data. Furthermore, we employed quasi-simultaneously observed, ancillary multi-frequency VLBI data for the source in order to carry out a comprehensive analysis of the core structure. We report the detection of a highly ordered, strong magnetic field around the central, supermassive black hole of 3C 84. The brightness temperature analysis suggests that the system is in equipartition. We also determined a turnover frequency of $\nu_\textrm{m}=(113\pm 4)\,\textrm{GHz}$, a corresponding synchrotron self-absorbed magnetic field of $B_\textrm{SSA} = (2.9\pm 1.6)\,\textrm{G}$, and an equipartition magnetic field of $B_\textrm{eq} = (5.2\pm 0.6)\,\textrm{G}$. Three components are resolved with the highest fractional polarisation detected for this object ($m_\textrm{net} = (17.0\pm 3.9)\%$). The positions of the components are compatible with those seen in low-frequency VLBI observations since 2017-2018. We report a steeply negative slope of the spectrum at 228 GHz. We used these findings to test existing models of jet formation, propagation, and Faraday rotation in 3C 84. The findings of our investigation into different flow geometries and black hole spins support an advection-dominated accretion flow in a magnetically arrested state around a rapidly rotating supermassive black hole as a model of the jet-launching system in the core of 3C 84. However, systematic uncertainties due to the limited $(u, v)$-coverage, however, cannot be ignored. Our upcoming work using new EHT data, which offer full imaging capabilities, will shed more light on the compact region of 3C 84.

# Introduction

The formation of relativistic astrophysical jets is a manifestation of the activity of accreting supermassive black holes residing in the nuclei of galaxies. Such jets can have an immense impact on their surroundings, either by stunting or enhancing the evolution of their host galaxy. Despite substantial efforts dedicated to understanding the physics governing jets, a number of open questions remain, including questions relating to the launching mechanism of these jets. The radio source 3C 84 (NGC 1275; $D_\textrm{L} = 78.9\pm2.4\,\textrm{Mpc}$, $z = 0.0176$, (cite: Strauss92), corresponding to a conversion factor $\uppsi=0.36$ pc/mas; see also Sect. [2.1](#ssec:Data)) is a nearby active galactic nucleus (AGN) and one of a handful of objects for which the jet formation zone can be resolved and probed with very-long-baseline interferometry (VLBI). Thus, 3C 84 is an ideal test bed for distinguishing between jet-launching models based on the resulting predictions for observables such as magnetic field strength. Using the unique polarimetric 1.3 mm VLBI observations of 3C 84, conducted with the Event Horizon Telescope (EHT; see (cite: EHT19a; EHT22a)), we are now able to distinguish between such models.

According to the current understanding, the linear polarisation is present in both the downstream jet (cite: Nagai17) and the compact region (cite: Kim19) of 3C 84, although its amplitude is low. A quantitative characterisation of the location of the 1.3 mm polarisation within the jet flow is crucial in order to distinguish between the different jet-launching models. To illustrate this, an interesting comparison can be made between the jet collimation near the jet base in M 87 (exhibiting a narrower opening angle, as seen, e.g. in (cite: Kim18)) and 3C 84 (featuring instead a wide structure as seen by *RadioAstron* and reported in (cite: Giovannini18)). Given this elongated structure, a disc-launched jet (cite: Blandford82) threaded by toroidal magnetic field lines is a possible explanation. The alternative scenario is the more commonly invoked black hole launched jet (cite: Blandford77) associated with poloidal magnetic field lines. Polarimetry at 1.3 mm is less affected by opacity effects and can therefore be used to test the necessary conditions for different jet-launching scenarios, as presented in this work. We therefore employed high-resolution millimetre VLBI to investigate how the substantial increase in polarisation with frequency in 3C 84 can be explained by the prevalent magnetic field.

# Data, analysis, and results

## Data description and analysis

In this work, we examined the first total intensity and polarimetric VLBI observations of 3C 84 at 228 GHz taken with the Event Horizon Telescope (EHT) and compared them with quasi-simultaneous VLBI observations at lower frequencies. 3C 84 was observed during the EHT 2017 campaign (cite: EHT19a; EHT22a) at 228 GHz on April 7 between 18:30 and 19:40 UTC, with six scans each around 5 mins in length. Five telescopes at three geographical sites participated in the observation: Atacama Large Millimeter/submillimeter Array (cite: Goddi19) and the Atacama Pathfinder Experiment (APEX) telescope in Chile; the Submillimeter Telescope (SMT) in Arizona; and the James Clerk Maxwell Telescope (JCMT) and the Submillimeter Array (SMA) in Hawai’i. Following the correlation, observations were subjected to the standard EHT data reduction path (cite: EHT19b; EHT19c; EHT22b), including the `EHT-HOPS` fringe-fitting and post-processing pipeline (cite: Blackburn19). Additional comments on the data reduction are given in Appendix [5](#app:AppData). The single-dish data used in this paper were observed by the POLAMI (cite: Thum08; Agudo18a) and QUIVER (cite: Myserlis18; Kraus03) programmes on April 4 and April 8, 2017, respectively.

As 3C 84 exhibits a low jet expansion velocity inside the submilliarcsecond (submas) region, we are able to use quasi-simultaneous VLBI observations of 3C 84 taken in March and April, 2017, at 15, 43, and 86 GHz to complement our analysis and assist our interpretation of the underlying jet physics without suffering from time-variability effects. Here, we define as compact region the entire region probed by the long EHT baselines, with an angular size of smaller than $200\,\upmu\textrm{as}$. Specifically, we used the publicly available Very Long Baseline Array (VLBA) epochs from April 22, 2017 at 15 GHz (cite: Lister18) and April 16, 2017 at 43 GHz (cite: Jorstad17). As both monitoring programs publish fully calibrated and imaged data sets, we opted to use them as provided.

At 86 GHz, we used the Global Millimeter VLBI Array (GMVA) epoch from March 30, 2017 (cite: Paraschos22). The antenna instrumental polarisation calibration (D-terms) was performed using the software `polsolve` (cite: MartiVidal21) and the data were imaged using the `CLEAN` algorithm (cite: Shepherd94; Shepherd95). The combined $(u, v)$-coverage of our multi-wavelength observations is shown in Fig. [1](#fig:UV).

For our analysis we assumed a BH mass of ${M_{\mathbin{\vcenter{\hbox{$\bullet$}}}}=8\times10^8\,M_\odot}$ (cite: Scharwaechter13), for which $100\,\upmu\textrm{as}$ corresponds to ${\sim500\,R_\textrm{s}}$ ($\sim800\,R_\textrm{s}$ deprojected). We used $H_0=69.6$ and ${\Omega_\textrm{M} = 0.286}$ in a flat cosmology (cite: Bennet14), yielding a length scale of $\uppsi=0.36$ pc/mas. Hence, $250\,{\rm R_S}\approx 54\, {\rm \upmu as} \approx 0.02\,{\rm pc}$ ($0.032$ pc de-projected) at $z=0.0176$.

![](coverage_3C84_alldata-2.pdf)

## Results

We find evidence of a highly ordered, strong magnetic field in the submas compact region of 3C 84. This region is best fitted by three circular Gaussian components, labelled core (‘C’), east (‘E’), and west (‘W’), as shown in Fig. [2](#fig:MultiF) (the method we used is described in Appendix [6](#app:Modelling)). The extended flux density detected on the short ALMA-APEX and JCMT-SMA baselines, while resolved out on all long EHT baselines, was fitted by a $\sim5000$ microarcseconds ($\upmu\textrm{as}$) circular Gaussian component with a flux density of $S_\textrm{core}^\textrm{228\,GHz} \sim 6.4\,\textrm{Jy}$. Furthermore, by averaging[^1] the linear fractional polarisation measurements of these three components, we determined the net linear fractional polarisation in the compact region to be $m_\textrm{net}=(17.0\pm 3.9)\%$. The short baseline between ALMA and APEX yielded an estimate for the linear fractional polarisation on larger arcsecond scales, of $\sim6\%$ (denoted in the bottom panel of Fig. [3](#fig:FFF) with the grey marker).

We cross-referenced the submas compact region model fit components at lower frequencies following the method detailed in (cite: Savolainen08) and Appendix [7](#sec:AppTemplate). While at 15 GHz the submas region appears fully blended, we are able to recover the 228 GHz structure at 86 GHz and even at 43 GHz. The results are reported in Table [\[table:Params\]](#table:Params).

We also measured both the total intensity $I$ and linearly polarised emission $P$ in the submas region of 3C 84 in the 15, 43, and 86 GHz images. The values of linear fractional polarisation at these three lower frequencies are considered as upper limit estimates. The results are shown in Fig. [3](#fig:FFF). The VLBI total intensity increases up to the 86 GHz measurement, and then decreases towards 228 GHz.

Close-in-time single-dish measurements at 8, 86, and 228 GHz are also shown in Fig. [3](#fig:FFF) (see also Table [1](#tab:sd)). The 86 GHz flux density is higher than that at 228 GHz. However, the 8 GHz measurement is also higher than at 86 GHz, suggesting a significant contribution from the parsec-scale jet. Furthermore, at 228 GHz, the compact-scale VLBI flux density is significantly lower than the corresponding extended flux density, as long EHT baselines over-resolve the large-scale jet emission structure (cite: EHT19d). In terms of fractional polarisation, it is evident that there is a significant increase at 228 GHz, indicating a transition in the accretion flow to the optically thin regime.

![](EHT_paper_blackbg-02.jpg)

![](Flux_Frapol_freq_v4.pdf)

# Discussion

## Insights from the synchrotron spectrum

Our analysis shows that the east–west elongated core structure (cite: Giovannini18) also persists at 1.3 mm, and in lower frequencies (as reported at 7 mm by (cite: Punsly21) and 3 mm by (cite: Oh22)). Interpretation of the nature of the components comprising this broad core structure heavily depends on the uncertain jet viewing angle ($\upxi$). An upper limit of $\upxi\sim40^\circ$ was reported by (cite: Oh22) based on a VLBI analysis of the compact region, but much lower values have also been found, for example based on $\gamma$-ray analysis (cite: Abdo09). The historically subluminal jet component velocities in the compact region (cite: Punsly21; Hodgson21; Paraschos22) point towards an increased viewing angle. Moreover, different parts of the jet have been reported to be moving with different velocities, which is related to the so-called ‘Doppler crisis’ phenomenon (cite: Henri06) and jet stratification (cite: Nagai14).

The high-resolution, high-frequency EHT observation enables a novel diagnosis of the state of plasma surrounding the central black hole via calculation of the turnover frequency $\upnu_\textrm{m}$ and the synchrotron self-absorption magnetic field strength $B_\textrm{SSA}$. Assuming $\upnu_\textrm{m}$ to be 86 GHz, (cite: Hodgson18) and (cite: Kim19) computed the $B_\textrm{SSA}$ to be $\sim21\,\textrm{G}$. Using additional EHT flux density measurements, we can directly measure $\upnu_\textrm{m}$. While the different observations correspond to different $(u, v)$ coverages, we fitted a focused Gaussian model to the high-signal-to-noise ratio ($S/N$) data at 228 GHz, finding core diameters within the order of magnitude of the diffraction limit. We also fixed the sizes of the components for all the frequencies in order to mitigate the effects of the different $(u, v)$ coverages (see Table [\[table:Params\]](#table:Params)). Subsequently, fitting, then, Eq. 5.90 from (cite: Condon16) (see also (cite: Rybicki79) and Appendix [8](#sec:AppMagField)) to the data yields $\upnu_\textrm{m} = (113\pm 4)\,\textrm{GHz}$ (cite: Tuerler00). We computed a core brightness temperature of $T_\textrm{B}=(3.6\pm 1.5)\times 10^{11}\,\textrm{K}$ from $\upnu_\textrm{m}$, assuming that the angular size of the components at $\upnu_\textrm{m}$ is the same as at 228 GHz (as the system is optically thin at both frequencies). Within the error budget, the system seems to be in equipartition (cite: Singal86) between kinetic and magnetic energies (cite: Paraschos23).

Furthermore, we computed $B_\textrm{SSA} = (2.9\pm 1.6)\,\textrm{G}$ using Eq. 2 from (cite: Marscher83) (see also Appendix [8](#sec:AppMagField)). We also calculated an equipartition magnetic field strength of $B_\textrm{eq} = (5.2\pm 0.6)\,\textrm{G}$. The uncertainties were calculated through standard error propagation. The two values agree with each other within the error budget. Our results also tentatively agree within the error budget with the magnetic field reported by (cite: Kim19). The equipartition Doppler factor is $\updelta_\textrm{eq} = 1.5\pm 0.4$, suggesting that the acceleration happens further downstream, which is in line with lower frequency observations of 3C 84 (cite: Hodgson18; Paraschos22).

Moreover, the equipartition magnetic field strength $B_\textrm{eq}$ in the vicinity of the jet apex was computed to reach up to 4 G in a core shift analysis carried out by (cite: Paraschos21). However, the magnetic field value mentioned by these latter authors was calculated at the distance between the extrapolated jet apex and the 86 GHz core, resulting in a slightly lower estimate than that found in this work. Nevertheless, it is important to exercise caution when interpreting both $\upnu_\textrm{m}$ and $B_\textrm{SSA}$. 3C 84 is a variable source (recently up to 20-30% variation in total intensity and linear polarised flux density at 43 GHz within a year based on the monitoring program VLBA-BU-BLAZAR), which means that these observables might be time dependent (cite: Hodgson18). Moreover, our models still contain large uncertainties due to the sparsity of the $(u, v)$ coverage, which may not be fully accounted for.

## Model interpretation

Possible interpretations of the physical mechanisms driving the wide core structure largely depend on the exact location of the central engine with regard to the observed core. The current understanding is that the central engine is located north or northwest of the 86 GHz VLBI core (cite: Giovannini18; Paraschos21). As its exact location is still ambiguous, it is unclear whether or not some of the identified components in this work correspond to the core (Case I) or a counter-jet (Case II).

Simulations of the radio jet of M 87 (cite: Moscibrodzka17) show that the linear polarisation is produced inside the approaching jet, while the dense accretion disc depolarises any radiation reaching us from the counter-jet. In 3C 84, circumnuclear free-free absorption has already been reported for example by (cite: Walker00), who cite a possible connection to the accretion disc. It is thought that the presence of this disc obscures the counter-jet in the milliarcsecond (mas) region of 3C 84, which only becomes visible at a distance of $>2\,\textrm{mas}$ at higher frequencies (as reported e.g. in (cite: Wajima20) at 86 GHz). As both E and W in Fig. [6](#fig:FIm) are highly linearly polarised (20-80%), this points towards Case I, meaning that the two components might be at the origin of the double-rail structure seen on larger scales, as opposed to a jet and counter-jet geometry. However, we note that this interpretation remains speculative, given the uncertainties.

This high fractional polarisation in E and W could be evidence for highly ordered magnetic field lines in the jet plasma with almost no Faraday depolarisation present. On the other hand, C has lower fractional polarisation and the synchrotron opacity should be nearly negligible at 228 GHz according to the Stokes I spectrum shown in Fig [3](#fig:FFF). This may indicate that the main source of depolarisation in the compact region probed by the EHT is beam depolarisation of complex magnetic field patterns or mild Faraday depolarisation, rather than opacity effects. Consequently, a possible Faraday screen located in the compact region could be at most the size of C, which is $\sim20$ $\upmu\textrm{as}$. However, it should be noted here that W is the most uncertain low-total-intensity component, hindering a reliable conclusion about its nature (see also Appendices [5](#app:AppData) and  [6](#app:Modelling)).

3C 84 is known to show high amounts of Faraday rotation (RM) and the presence of circular polarisation (cite: Agudo18a; Myserlis18). Using the SMA and CARMA, (cite: Plambeck14) reported an RM of as high as $\sim9\times10^5\,\textrm{rad/m}^2$, indicative of the presence of a strong magnetic field. This places 3C 84 in a small group of known radio sources exhibiting similarly high RMs, such as Sgr A$^*$ ($\sim5\times10^5\,\textrm{rad/m}^2$; (cite: Wielgus22) and references therein), M 87 ($\sim 10^5\,\textrm{rad/m}^2$; (cite: Goddi2021)), and PKS 1830-211 ($\sim10^8\,\textrm{rad/m}^2$; (cite: MartiVidal15)). However, whether this RM occurs in the medium surrounding the jet (e.g. from a disc wind) or is connected to the accretion flow remains unknown. The origin of the RM can be explored by determining its dependence on the observing frequency (cite: Plambeck14; Goddi2021) or the distance from the central engine (cite: Park15).

The density of the accretion flow, which is a related quantity that can be estimated via the RM, is required in order to constrain the mass-accretion rate around BHs (cite: Nagai17) for different accretion flow models, such as advection-dominated accretion flows (ADAFs; see (cite: Narayan95)) and convection-dominated accretion flows (CDAFs; see (cite: Narayan00)).

Different plausible depolarisation mechanisms have been proposed for 3C 84, that is, originating from such an accretion flow and the jet itself (cite: Li16; Kim19). Combining the single-dish data presented in Fig. [3](#fig:FFF), which were taken quasi-simultaneously with the EHT observations, allows us to estimate an estimate of the RM present in 3C 84. We find that $\textrm{RM} = (6.06\pm 0.01)\times 10^6\,\textrm{rad/m}^2$ by determining the gradient of the EVPAs as a function of the wavelength squared (cite: Kim19). The $n\uppi$ ambiguity was resolved beforehand, as described in (cite: Hovatta12). Such large RM values could be produced by the presence of relativistic and thermal electrons in the boundary layer between the jet and the interstellar medium, as reported in (cite: Goddi2021) for the jet in M 87.

## Physical consequences

The high fractional linear polarisation in the innermost region of 3C 84, revealed at 228 GHz, clearly indicates that we are probing a previously elusive region, as we are able to achieve higher resolution while being less affected by opacity effects. We are probing the innermost region of 3C 84 at $\sim500\,R_\textrm{s}$, which appears to be an optically thin region with an ordered magnetic field framing the core.

Furthermore, this region is so compact that an association between the broad jet of 3C 84 and the accretion disk can be ruled out. However, it should be pointed out that both a BH-driven jet and a disc-driven wind could coexist and the present EHT observations are a better probe of the former. In a BH-driven jet scenario, jet launching in 3C 84 might be attributed to a magnetically arrested disc (MAD; see similar simulations carried out for M 87 in (cite: Chael19)), as opposed to a thin, broad disc structure (cite: Liska19). Jets in MAD ADAF systems are likely launched by the Blandford-Znajek mechanism (cite: Blandford77), which is the case where a powerful jet spine is powered directly by the energy extracted from the ergosphere of the BH.

Using our estimate of the RM at 228 GHz, it is possible to test whether the magnetic field reaches saturation strength; that is, whether the system is in the MAD state (cite: Narayan00; Tchekhovskoy11). Under the assumptions described in Appendix [9](#sec:AppMagFieldM), we find that the dimensionless magnetic flux $\upphi = 41-93$ (cite: Tchekhovskoy11). Values above the saturation value $\upphi_\textrm{max} = 50$ indicate that the jet is in a magnetically arrested state, and therefore our analysis suggests that jet launching in 3C 84 is MAD. As higher BH spin values and $\upbeta=1.5$ produce values close to $\upphi_\textrm{max}$, our result indicates a preference for a high BH spin and the ADAF model. 3C 84 is also classified as a low-luminosity AGN for which ADAF models are commonly invoked (cite: deMenezes20), further strengthening our conclusion. The mass-accretion rate estimated in Appendix [9](#sec:AppMagFieldM) corresponds to $\dot{M} \sim 10^{-5}-10^{-4}\dot{M}_\textrm{Edd}$, which is somewhat larger than in the case of M 87 MAD models (see e.g. (cite: EHT21b)). This suggests that a non-negligible dynamical impact of radiation is possible, which could challenge the applicability of the presented analysis. It should be pointed out here that it is unclear whether Faraday rotation takes place exclusively inside the accretion flow. Our analysis described in Appendix [9](#sec:AppMagFieldM) is based on the assumption that the accretion flow is dominant.

If a spine-sheath geometry (cite: Tavecchio14) is present, manifested in the observations as a transverse velocity gradient, it could also be the underlying depolarising structure. In this case the rotation of the central BH leads to an inhomogeneous and twisted magnetic field topology (cite: Tchekhovskoy15). Furthermore, this scenario would also provide an explanation for the Doppler crisis. As discussed in (cite: Hodgson21), so-called ‘jet-in-jet’ formations (cite: Giannios09) associated with velocity stratification in the bulk jet flow could be responsible for the enhanced $\gamma$-ray emission observed in 3C 84. Such a spine-sheath geometry has already been shown by the EHT to exist on small scales in the jet-launching region of Centaurus A (cite: Janssen21).

Ultimately, our detection of the exceptionally high fractional polarisation at 228 GHz, the peculiar jet morphology, and the detailed radio spectrum suggest that the jet in 3C 84 might be launched from both the central BH and the surrounding accretion disc (cite: Blandford22). As shown by the present findings, millimetre VLBI observations pave the way towards probing the ultimate vicinity of BHs. Future 3C 84 EHT observations with added antennas on short and intermediate baselines will help to constrain the jet morphology and improve the fidelity of the model.

# Conclusions

In this work we present the first detection of microarcsecond-scale polarised structures with the EHT. Our findings can be summarised as follows:

- We report the first ever 228 GHz VLBI model of 3C 84, which reveals that the compact region is made up of three components.

- We find a high degree of net fractional polarisation $m_\textrm{net} = (17.0\pm 3.9)\%$. The brightness temperature is $T_\textrm{b} = (3.6\pm 1.5)\times 10^{11}\,\textrm{K}$, which suggests that the system is in equipartition.

- Using quasi-simultaneous observations of 3C 84 at 15, 43, 86, and 228 GHz, we compute a turnover (optical depth $\tau = 1$) frequency of $\nu_\textrm{m} = (113\pm 4)\,\textrm{GHz}$, a synchrotron self-absorbed magnetic field of $B_\textrm{SSA} = (2.9\pm 1.6)\,\textrm{G}$, and an equipartition magnetic field of $B_\textrm{eq} = (5.2\pm 0.6)\,\textrm{G}$. However, these values might be influenced by the known variability of the source.

- The increased values of linear polarisation suggest that the observed structure is the approaching jet, which is consistent with the large opening angle. Such a geometry can be produced by a thick disc associated with a (cite: Blandford77) jet-launching scenario.

- We find indications of a preference for higher values of BH spin and the ADAF model in the context of the MAD jet launching prevalent in 3C 84.

The EHT is an excellent instrument for probing AGN cores in nearby radio galaxies. Combined with lower frequency VLBI arrays, such as the GMVA and the VLBA, the EHT makes it possible to conduct multi-frequency studies, which provide valuable insights into jet formation and jet launching. New EHT and GMVA observations have already been carried out, with 3C 84 as the main target. The increased sensitivity and $(u, v)$ coverage will enable us to conduct follow-up studies with higher fidelity. Total intensity images of the compact region will shed more light on whether or not the components we were able to identify here correspond to the broad structure seen with *RadioAstron* (cite: Giovannini18). Spectral index maps of EHT and GMVA images observed quasi-simultaneously might also assist in pinpointing the exact location of the BH (cite: Paraschos22b) and in discriminating between jet launching-scenarios.

# Acknowledgements

We thank the anonymous referee for the constructive suggestions which improved this manuscript. The Event Horizon Telescope Collaboration thanks the following organizations and programs: the Academia Sinica; the Academy of Finland (projects 274477, 284495, 312496, 315721); the Agencia Nacional de Investigación y Desarrollo (ANID), Chile via NCN$19\_058$ (TITANs) and Fondecyt 1221421, the Alexander von Humboldt Stiftung; an Alfred P. Sloan Research Fellowship; Allegro, the European ALMA Regional Centre node in the Netherlands, the NL astronomy research network NOVA and the astronomy institutes of the University of Amsterdam, Leiden University, and Radboud University; the ALMA North America Development Fund; the Astrophysics and High Energy Physics programme by MCIN (with funding from European Union NextGenerationEU, PRTR-C17I1); the Black Hole Initiative, which is funded by grants from the John Templeton Foundation and the Gordon and Betty Moore Foundation (although the opinions expressed in this work are those of the author(s) and do not necessarily reflect the views of these Foundations); the Brinson Foundation; “la Caixa” Foundation (ID 100010434) through fellowship codes LCF/BQ/DI22/11940027 and LCF/BQ/DI22/11940030; Chandra DD7-18089X and TM6-17006X; the China Scholarship Council; the China Postdoctoral Science Foundation fellowships (2020M671266, 2022M712084); Consejo Nacional de Ciencia y Tecnologı́a (CONACYT, Mexico, projects U0004-246083, U0004-259839, F0003-272050, M0037-279006, F0003-281692, 104497, 275201, 263356); the Consejería de Economía, Conocimiento, Empresas y Universidad of the Junta de Andalucía (grant P18-FR-1769), the Consejo Superior de Investigaciones Científicas (grant 2019AEP112); the Delaney Family via the Delaney Family John A. Wheeler Chair at Perimeter Institute; Dirección General de Asuntos del Personal Académico-Universidad Nacional Autónoma de México (DGAPA-UNAM, projects IN112417 and IN112820); the Dutch Organization for Scientific Research (NWO) for the VICI award (grant 639.043.513), the grant\
OCENW.KLEIN.113, and the Dutch Black Hole Consortium (with project No. NWA 1292.19.202) of the research programme the National Science Agenda; the Dutch National Supercomputers, Cartesius and Snellius (NWO grant 2021.013); the EACOA Fellowship awarded by the East Asia Core Observatories Association, which consists of the Academia Sinica Institute of Astronomy and Astrophysics, the National Astronomical Observatory of Japan, Center for Astronomical Mega-Science, Chinese Academy of Sciences, and the Korea Astronomy and Space Science Institute; the European Research Council (ERC) Synergy Grant “BlackHoleCam: Imaging the Event Horizon of Black Holes" (grant 610058); the European Union Horizon 2020 research and innovation programme under grant agreements RadioNet (No. 730562) and M2FINDERS (No. 101018682); the Horizon ERC Grants 2021 programme under grant agreement No. 101040021; the Generalitat Valenciana (grants APOSTD/2018/177 and ASFAE/2022/018) and GenT Program (project CIDEGENT/2018/021); MICINN Research Project PID2019-108995GB-C22; the European Research Council for advanced grant ‘JETSET: Launching, propagation and emission of relativistic jets from binary mergers and across mass scales’ (grant No. 884631); the FAPESP (Fundação de Amparo á Pesquisa do Estado de São Paulo) under grant 2021/01183-8; the Institute for Advanced Study; the Istituto Nazionale di Fisica Nucleare (INFN) sezione di Napoli, iniziative specifiche TEONGRAV; the International Max Planck Research School for Astronomy and Astrophysics at the Universities of Bonn and Cologne; DFG research grant “Jet physics on horizon scales and beyond” (grant No. FR 4069/2-1); Joint Columbia/Flatiron Postdoctoral Fellowship (research at the Flatiron Institute is supported by the Simons Foundation); the Japan Ministry of Education, Culture, Sports, Science and Technology (MEXT; grant JPMXP1020200109); the Japan Society for the Promotion of Science (JSPS) Grant-in-Aid for JSPS Research Fellowship (JP17J08829); the Joint Institute for Computational Fundamental Science, Japan; the Key Research Program of Frontier Sciences, Chinese Academy of Sciences (CAS, grants QYZDJ-SSW-SLH057, QYZDJSSW-SYS008, ZDBS-LY-SLH011); the Leverhulme Trust Early Career Research Fellowship; the Max-Planck-Gesellschaft (MPG); the Max Planck Partner Group of the MPG and the CAS; the MEXT/JSPS KAKENHI (grants 18KK0090, JP21H01137, JP18H03721, JP18K13594, 18K03709, JP19K14761, 18H01245, 25120007); the Malaysian Fundamental Research Grant Scheme\
(FRGS) FRGS/1/2019/STG02/UM/02/6; the MIT International Science and Technology Initiatives (MISTI) Funds; the Ministry of Science and Technology (MOST) of Taiwan (103-2119-M-001-010-MY2, 105-2112-M-001-025-MY3, 105-2119-M-001-042, 106-2112-M-001-011, 106-2119-M-001-013, 106-2119-M-001-027, 106-2923-M-001-005, 107-2119-M-001-017, 107-2119-M-001-020, 107-2119-M-001-041, 107-2119-M-110-005, 107-2923-M-001-009, 108-2112-M-001-048, 108-2112-M-001-051, 108-2923-M-001-002, 109-2112-M-001-025, 109-2124-M-001-005, 109-2923-M-001-001, 110-2112-M-003-007-MY2, 110-2112-M-001-033, 110-2124-M-001-007, and 110-2923-M-001-001); the Ministry of Education (MoE) of Taiwan Yushan Young Scholar Program; the Physics Division, National Center for Theoretical Sciences of Taiwan; the National Aeronautics and Space Administration (NASA, Fermi Guest Investigator grant 80NSSC20K1567, NASA Astrophysics Theory Program grant 80NSSC20K0527, NASA NuSTAR award 80NSSC20K0645); NASA Hubble Fellowship grants HST-HF2-51431.001-A, HST-HF2-51482.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555; the National Institute of Natural Sciences (NINS) of Japan; the National Key Research and Development Program of China (grant 2016YFA0400704, 2017YFA0402703, 2016YFA0400702); the National Science Foundation (NSF, grants AST-0096454, AST-0352953, AST-0521233, AST-0705062, AST-0905844, AST-0922984, AST-1126433,\
AST-1140030, DGE-1144085, AST-1207704, AST-1207730, AST-1207752, MRI-1228509, OPP-1248097, AST-1310896, AST-1440254, AST-1555365,\
AST-1614868, AST-1615796, AST-1715061, AST-1716327, AST-1716536, OISE-1743747, AST-1816420, AST-1935980, AST-2034306); NSF Astronomy and Astrophysics Postdoctoral Fellowship (AST-1903847); the Natural Science Foundation of China (grants 11650110427, 10625314, 11721303, 11725312, 11873028, 11933007, 11991052, 11991053, 12192220, 12192223); the Natural Sciences and Engineering Research Council of Canada (NSERC, including a Discovery Grant and the NSERC Alexander Graham Bell Canada Graduate Scholarships-Doctoral Program); the National Youth Thousand Talents Program of China; the National Research Foundation of Korea (the Global PhD Fellowship Grant: grants NRF-2015H1A2A1033752, the Korea Research Fellowship Program:\
NRF-2015H1D3A1066561, Brain Pool Program: 2019H1D3A1A01102564, Basic Research Support Grant 2019R1F1A1059721, 2021R1A6A3A01086420,\
2022R1C1C1005255); Netherlands Research School for Astronomy (NOVA) Virtual Institute of Accretion (VIA) postdoctoral fellowships; Onsala Space Observatory (OSO) national infrastructure, for the provisioning of its facilities/observational support (OSO receives funding through the Swedish Research Council under grant 2017-00648); the Perimeter Institute for Theoretical Physics (research at Perimeter Institute is supported by the Government of Canada through the Department of Innovation, Science and Economic Development and by the Province of Ontario through the Ministry of Research, Innovation and Science); the Princeton Gravity Initiative; the Spanish Ministerio de Ciencia e Innovación (grants PGC2018-098915-B-C21, AYA2016-80889-P, PID2019-108995GB-C21, PID2020-117404GB-C21); the University of Pretoria for financial aid in the provision of the new Cluster Server nodes and SuperMicro (USA) for a SEEDING GRANT approved toward these nodes in 2020; the Shanghai Pilot Program for Basic Research, Chinese Academy of Science, Shanghai Branch (JCYJ-SHFY-2021-013); the State Agency for Research of the Spanish MCIU through the “Center of Excellence Severo Ochoa” award for the Instituto de Astrofísica de Andalucía (SEV-2017- 0709); the Spanish Ministry for Science and Innovation grant CEX2021-001131-S funded by MCIN/AEI/10.13039/501100011033; the Spinoza Prize SPI 78-409; the South African Research Chairs Initiative, through the South African Radio Astronomy Observatory (SARAO, grant ID 77948), which is a facility of the National Research Foundation (NRF), an agency of the Department of Science and Innovation (DSI) of South Africa; the Toray Science Foundation; the Swedish Research Council (VR); the US Department of Energy (USDOE) through the Los Alamos National Laboratory (operated by Triad National Security, LLC, for the National Nuclear Security Administration of the USDOE, contract 89233218CNA000001); and the YCAA Prize Postdoctoral Fellowship.

We thank the staff at the participating observatories, correlation centers, and institutions for their enthusiastic support. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.01154.V. ALMA is a partnership of the European Southern Observatory (ESO; Europe, representing its member states), NSF, and National Institutes of Natural Sciences of Japan, together with National Research Council (Canada), Ministry of Science and Technology (MOST; Taiwan), Academia Sinica Institute of Astronomy and Astrophysics (ASIAA; Taiwan), and Korea Astronomy and Space Science Institute (KASI; Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, Associated Universities, Inc. (AUI)/NRAO, and the National Astronomical Observatory of Japan (NAOJ). The NRAO is a facility of the NSF operated under cooperative agreement by AUI. This research used resources of the Oak Ridge Leadership Computing Facility at the Oak Ridge National Laboratory, which is supported by the Office of Science of the U.S. Department of Energy under contract No. DE-AC05-00OR22725; the ASTROVIVES FEDER infrastructure, with project code IDIFEDER-2021-086; the computing cluster of Shanghai VLBI correlator supported by the Special Fund for Astronomy from the Ministry of Finance in China; We also thank the Center for Computational Astrophysics, National Astronomical Observatory of Japan. This work was supported by FAPESP (Fundacao de Amparo a Pesquisa do Estado de Sao Paulo) under grant 2021/01183-8.

APEX is a collaboration between the Max-Planck-Institut für Radioastronomie (Germany), ESO, and the Onsala Space Observatory (Sweden). The SMA is a joint project between the SAO and ASIAA and is funded by the Smithsonian Institution and the Academia Sinica. The JCMT is operated by the East Asian Observatory on behalf of the NAOJ, ASIAA, and KASI, as well as the Ministry of Finance of China, Chinese Academy of Sciences, and the National Key Research and Development Program (No. 2017YFA0402700) of China and Natural Science Foundation of China grant 11873028. Additional funding support for the JCMT is provided by the Science and Technologies Facility Council (UK) and participating universities in the UK and Canada. The LMT is a project operated by the Instituto Nacional de Astrófisica, Óptica, y Electrónica (Mexico) and the University of Massachusetts at Amherst (USA). The IRAM 30-m telescope on Pico Veleta, Spain is operated by IRAM and supported by CNRS (Centre National de la Recherche Scientifique, France), MPG (Max-Planck-Gesellschaft, Germany), and IGN (Instituto Geográfico Nacional, Spain). The SMT is operated by the Arizona Radio Observatory, a part of the Steward Observatory of the University of Arizona, with financial support of operations from the State of Arizona and financial support for instrumentation development from the NSF. Support for SPT participation in the EHT is provided by the National Science Foundation through award OPP-1852617 to the University of Chicago. Partial support is also provided by the Kavli Institute of Cosmological Physics at the University of Chicago. The SPT hydrogen maser was provided on loan from the GLT, courtesy of ASIAA.

This work used the Extreme Science and Engineering Discovery Environment (XSEDE), supported by NSF grant ACI-1548562, and CyVerse, supported by NSF grants DBI-0735191, DBI-1265383, and DBI-1743442. XSEDE Stampede2 resource at TACC was allocated through TG-AST170024 and TG-AST080026N. XSEDE JetStream resource at PTI and TACC was allocated through AST170028. This research is part of the Frontera computing project at the Texas Advanced Computing Center through the Frontera Large-Scale Community Partnerships allocation AST20023. Frontera is made possible by National Science Foundation award OAC-1818253. This research was done using services provided by the OSG Consortium (cite: osg07; osg09), which is supported by the National Science Foundation award Nos. 2030508 and 1836650. Additional work used ABACUS2.0, which is part of the eScience center at Southern Denmark University. Simulations were also performed on the SuperMUC cluster at the LRZ in Garching, on the LOEWE cluster in CSC in Frankfurt, on the HazelHen cluster at the HLRS in Stuttgart, and on the Pi2.0 and Siyuan Mark-I at Shanghai Jiao Tong University. The computer resources of the Finnish IT Center for Science (CSC) and the Finnish Computing Competence Infrastructure (FCCI) project are acknowledged. This research was enabled in part by support provided by Compute Ontario (http://computeontario.ca), Calcul Quebec (http://www.calculquebec.ca), and Compute Canada (http://www.computecanada.ca).

The EHTC has received generous donations of FPGA chips from Xilinx Inc., under the Xilinx University Program. The EHTC has benefited from technology shared under open-source license by the Collaboration for Astronomy Signal Processing and Electronics Research (CASPER). The EHT project is grateful to T4Science and Microsemi for their assistance with hydrogen masers. This research has made use of NASA’s Astrophysics Data System. We gratefully acknowledge the support provided by the extended staff of the ALMA, from the inception of the ALMA Phasing Project through the observational campaigns of 2017 and 2018. Partly based on observations with the 100-m telescope of the MPIfR (Max-Planck-Institut für Radioastronomie) at Effelsberg. We would like to thank A. Deller and W. Brisken for EHT-specific support with the use of DiFX. We thank Jack Livingston for his comments. We acknowledge the significance that Maunakea, where the SMA and JCMT EHT stations are located, has for the indigenous Hawaiian people.\

86 natexlab

(ref: Abdo09) Abdo, A. A., Ackermann, M., Ajello, M., et al. 2009, ApJ, 699, 31

(ref: Agudo18a) Agudo, I., Thum, C., Molina, S. N., et al. 2018, MNRAS, 474, 1427

(ref: Beck05) Beck, R. & Krause, M. 2005, Astronomische Nachrichten, 326, 414

(ref: Bell78) Bell, A. R. 1978, MNRAS, 182, 443

(ref: Bennet14) Bennett, C. L., Larson, D., Weiland, J. L., & Hinshaw, G. 2014, ApJ, 794, 135

(ref: Biermann87) Biermann, P. L. & Strittmatter, P. A. 1987, ApJ, 322, 643

(ref: Blackburn19) Blackburn, L., Chan, C.-k., Crew, G. B., et al. 2019, ApJ, 882, 23

(ref: Blandford22) Blandford, R. & Globus, N. 2022, MNRAS, 514, 5141

(ref: Blandford82) Blandford, R. D. & Payne, D. G. 1982, MNRAS, 199, 883

(ref: Blandford77) Blandford, R. D. & Znajek, R. L. 1977, MNRAS, 179, 433

(ref: Chael19) Chael, A., Narayan, R., & Johnson, M. D. 2019, MNRAS, 486, 2873

(ref: Chael16) Chael, A. A., Johnson, M. D., Narayan, R., et al. 2016, ApJ, 829, 11

(ref: Chamani21) Chamani, W., Savolainen, T., Hada, K., & Xu, M. H. 2021, A&A, 652, A14

(ref: Condon16) Condon, J. J. & Ransom, S. M. 2016, Essential Radio Astronomy

(ref: deMenezes20) de Menezes, R., Nemmen, R., Finke, J. D., Almeida, I., & Rani, B. 2020, MNRAS, 492, 4120

(ref: EHT22a) EHTC, Akiyama, K., Alberdi, A., et al. 2022a, ApJL, 930, L12

(ref: EHT22b) EHTC, Akiyama, K., Alberdi, A., et al. 2022b, ApJL, 930, L13

(ref: EHT19a) EHTC, Akiyama, K., Alberdi, A., et al. 2019a, ApJL, 875, L1

(ref: EHT19b) EHTC, Akiyama, K., Alberdi, A., et al. 2019b, ApJL, 875, L2

(ref: EHT19c) EHTC, Akiyama, K., Alberdi, A., et al. 2019c, ApJL, 875, L3

(ref: EHT19d) EHTC, Akiyama, K., Alberdi, A., et al. 2019d, ApJL, 875, L4

(ref: EHT21a) EHTC, Akiyama, K., Algaba, J. C., et al. 2021a, ApJL, 910, L12

(ref: EHT21b) EHTC, Akiyama, K., Algaba, J. C., et al. 2021b, ApJL, 910, L13

(ref: Gardner66) Gardner, F. F. & Whiteoak, J. B. 1966, ARA&A, 4, 245

(ref: Giannios09) Giannios, D., Uzdensky, D. A., & Begelman, M. C. 2009, MNRAS, 395, L29

(ref: Giovannini18) Giovannini, G., Savolainen, T., Orienti, M., et al. 2018, Nature Astronomy, 2, 472

(ref: Goddi2021) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2021, ApJL, 910, L14

(ref: Goddi19) Goddi, C., Martı́-Vidal, I., Messias, H., et al. 2019, PASP, 131, 075003

(ref: Henri06) Henri, G. & Saugé, L. 2006, ApJ, 640, 185

(ref: Hodgson18) Hodgson, J. A., Rani, B., Lee, S.-S., et al. 2018, MNRAS, 475, 368

(ref: Hodgson21) Hodgson, J. A., Rani, B., Oh, J., et al. 2021, ApJ, 914, 43

(ref: Hovatta12) Hovatta, T., Lister, M. L., Aller, M. F., et al. 2012, AJ, 144, 105

(ref: Issaoun22) Issaoun, S., Wielgus, M., Jorstad, S., et al. 2022, ApJ, 934, 145

(ref: Janssen21) Janssen, M., Falcke, H., Kadler, M., et al. 2021, Nature Astronomy, 5, 1017

(ref: Janssen19) Janssen, M., Goddi, C., van Bemmel, I. M., et al. 2019, A&A, 626, A75

(ref: Jorstad2023) Jorstad, S., Wielgus, M., Lico, R., et al. 2023, ApJ, 943, 170

(ref: Jorstad17) Jorstad, S. G., Marscher, A. P., Morozova, D. A., et al. 2017, ApJ, 846, 98

(ref: Kim18) Kim, J. Y., Krichbaum, T. P., Lu, R. S., et al. 2018, A&A, 616, A188

(ref: Kim19) Kim, J. Y., Krichbaum, T. P., Marscher, A. P., et al. 2019, A&A, 622, A196

(ref: Kovalev08) Kovalev, Y. Y., Lobanov, A. P., Pushkarev, A. B., & Zensus, J. A. 2008, A&A, 483, 759

(ref: Kraus03) Kraus, A., Krichbaum, T. P., Wegner, R., et al. 2003, A&A, 401, 161

(ref: Li16) Li, Y.-P., Yuan, F., & Xie, F.-G. 2016, ApJ, 830, 78

(ref: Liska19) Liska, M., Tchekhovskoy, A., Ingram, A., & van der Klis, M. 2019, MNRAS, 487, 550

(ref: Lister18) Lister, M. L., Aller, M. F., Aller, H. D., et al. 2018, ApJS, 234, 12

(ref: Marrone06) Marrone, D. P., Moran, J. M., Zhao, J.-H., & Rao, R. 2006, ApJ, 640, 308

(ref: Marscher83) Marscher, A. P. 1983, ApJ, 264, 296

(ref: MartiVidal12) Martı́-Vidal, I., Krichbaum, T. P., Marscher, A., et al. 2012, A&A, 542, A107

(ref: MartiVidal15) Martı́-Vidal, I., Muller, S., Vlemmings, W., Horellou, C., & Aalto, S. 2015, Science, 348, 311

(ref: MartiVidal21) Martı́-Vidal, I., Mus, A., Janssen, M., de Vicente, P., & González, J. 2021, A&A, 646, A52

(ref: Moscibrodzka17) Mościbrodzka, M., Dexter, J., Davelaar, J., & Falcke, H. 2017, MNRAS, 468, 2214

(ref: Myserlis18) Myserlis, I., Angelakis, E., Kraus, A., et al. 2018, A&A, 609, A68

(ref: Nagai17) Nagai, H., Fujita, Y., Nakamura, M., et al. 2017, ApJ, 849, 52

(ref: Nagai14) Nagai, H., Haga, T., Giovannini, G., et al. 2014, ApJ, 785, 53

(ref: Narayan00) Narayan, R., Igumenshchev, I. V., & Abramowicz, M. A. 2000, ApJ, 539, 798

(ref: Narayan95) Narayan, R. & Yi, I. 1995, ApJ, 452, 710

(ref: Oh22) Oh, J., Hodgson, J. A., Trippe, S., et al. 2022, MNRAS, 509, 1024

(ref: Pacholczyk70) Pacholczyk, A. G. 1970, Radio astrophysics. Nonthermal processes in galactic and extragalactic sources

(ref: Paraschos22b) Paraschos, G., Kim, J. Y., Krichbaum, T., et al. 2022a, in European VLBI Network Mini-Symposium and Users’ Meeting 2021, Vol. 2021, 43

(ref: Paraschos21) Paraschos, G. F., Kim, J. Y., Krichbaum, T. P., & Zensus, J. A. 2021, A&A, 650, L18

(ref: Paraschos22) Paraschos, G. F., Krichbaum, T. P., Kim, J. Y., et al. 2022b, A&A, 665, A1

(ref: Paraschos23) Paraschos, G. F., Mpisketzis, V., Kim, J. Y., et al. 2023, A&A, 669, A32

(ref: Park15) Park, J. H., Trippe, S., Krichbaum, T. P., et al. 2015, A&A, 576, L16

(ref: Plambeck14) Plambeck, R. L., Bower, G. C., Rao, R., et al. 2014, ApJ, 797, 66

(ref: osg07) Pordes, R., Petravick, D., Kramer, B., et al. 2007, in 78, Vol. 78, J. Phys. Conf. Ser., 012057

(ref: Punsly21) Punsly, B., Nagai, H., Savolainen, T., & Orienti, M. 2021, ApJ, 911, 19

(ref: Rafferty06) Rafferty, D. A., McNamara, B. R., Nulsen, P. E. J., & Wise, M. W. 2006, ApJ, 652, 216

(ref: Rybicki79) Rybicki, G. B. & Lightman, A. P. 1979, Radiative processes in astrophysics

(ref: Savolainen08) Savolainen, T., Wiik, K., Valtaoja, E., & Tornikoski, M. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 386, Extragalactic Jets: Theory and Observation from Radio to Gamma Ray, ed. T. A. Rector & D. S. De Young, 451

(ref: Scharwaechter13) Scharwächter, J., McGregor, P. J., Dopita, M. A., & Beck, T. L. 2013, MNRAS, 429, 2315

(ref: osg09) Sfiligoi, I., Bradley, D. C., Holzman, B., et al. 2009, in 2, Vol. 2, 2009 WRI World Congress on Computer Science and Information Engineering, 428–432

(ref: Shepherd94) Shepherd, M. C., Pearson, T. J., & Taylor, G. B. 1994, in Bulletin of the American Astronomical Society, Vol. 26, 987–989

(ref: Shepherd95) Shepherd, M. C., Pearson, T. J., & Taylor, G. B. 1995, in Bulletin of the American Astronomical Society, Vol. 27, 903

(ref: Singal86) Singal, A. K. 1986, A&A, 155, 242

(ref: Strauss92) Strauss, M. A., Huchra, J. P., Davis, M., et al. 1992, ApJS, 83, 29

(ref: Tavecchio14) Tavecchio, F. & Ghisellini, G. 2014, MNRAS, 443, 1224

(ref: Tchekhovskoy15) Tchekhovskoy, A. 2015, in Astrophysics and Space Science Library, Vol. 414, The Formation and Disruption of Black Hole Jets, ed. I. Contopoulos, D. Gabuzda, & N. Kylafis, 45

(ref: Tchekhovskoy10) Tchekhovskoy, A., Narayan, R., & McKinney, J. C. 2010, ApJ, 711, 50

(ref: Tchekhovskoy11) Tchekhovskoy, A., Narayan, R., & McKinney, J. C. 2011, MNRAS, 418, L79

(ref: Thompson17) Thompson, A. R., Moran, J. M., & Swenson, George W., J. 2017, Interferometry and Synthesis in Radio Astronomy, 3rd Edition

(ref: Thum08) Thum, C., Wiesemeyer, H., Paubert, G., Navarro, S., & Morris, D. 2008, PASP, 120, 777

(ref: Tuerler00) Türler, M., Courvoisier, T. J. L., & Paltani, S. 2000, A&A, 361, 850

(ref: 2020SciPy-NMeth) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Wajima20) Wajima, K., Kino, M., & Kawakatu, N. 2020, ApJ, 895, 35

(ref: Walker00) Walker, R. C., Dhawan, V., Romney, J. D., Kellermann, K. I., & Vermeulen, R. C. 2000, ApJ, 530, 233

(ref: Wielgus22) Wielgus, M., Moscibrodzka, M., Vos, J., et al. 2022, A&A, 665, L6

(ref: Zamaninasab14) Zamaninasab, M., Clausen-Brown, E., Savolainen, T., & Tchekhovskoy, A. 2014, Nature, 510, 126

# Additional methodology comments

![](data_fit.pdf)

| Frequency \[GHz\] | ID | Flux density \[Jy\] | $T_\textrm{B}$ \[$10^{10}\,$K\] | FWHM \[$\upmu$as\] | Polarisation \[%\] | Position \[$\upmu$as, $\upmu$as\] |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 15 | E+C+W | 1.77 | $253.7 \pm 76.3$ | $62.1\pm8.1$ | \<2.0 | (0.0, 0.0) |
| 43 | E | 0.07 | $3.6 \pm 1.5$ | $35.5\pm7.1$ | \<7.0 | (34.4, -20.1) |
|  | C | 1.69 | $411.4 \pm 175.8$ | $16.6\pm3.3$ | \<1.0 | (0.0, 0.0) |
|  | W | 0.80 | $535.5 \pm 228.8$ | $10.0\pm2.0$ | \<2.0 | (-26.1, -8.58) |
| 86 | E | 1.49 | $19.8 \pm 8.4$ | $35.5\pm7.1$ | \<1.0 | (34.4, -20.1) |
|  | C | 3.06 | $186.2 \pm 79.5$ | $16.6\pm3.3$ | \<1.0 | (0.0, 0.0) |
|  | W | 0.58 | $97.6 \pm 41.7$ | $10.0\pm2.0$ | \<2.0 | (-26.1, -8.58) |
| 228 | E | 0.93 | $1.8 \pm 0.8$ | $35.5\pm7.1$ | $20.0\pm5.8$ | (34.4, -20.1) |
|  | C | 1.02 | $8.8 \pm 3.8$ | $16.6\pm3.3$ | $11.0\pm2.0$ | (0.0, 0.0) |
|  | W | 0.04 | $1.0 \pm 0.4$ | $10.0\pm2.0$ | $40.0-80.0$ | (-26.1, -8.58) |

\

At 15 GHz the image resolution is insufficient to confidently distinguish between the compact region components, and so we limit ourselves to reporting the integrated flux density and fractional polarisation values instead. The positional uncertainty is of the order of $\leq2\%$ for E in the east–west and north–south directions, and $\leq7\%$ in the east–west and $\leq60\%$ in north–south direction for W. Here, C is fixed at (0, 0). The uncertainties of the flux density measurements are of the order of $20\%$ at 15 GHz, $30\%$ at 43 GHz, $50\%$ at 86 GHz, and $15\%$ at 228 GHz (cite: EHT19c). The large relative uncertainty in the fractional polarisation of W is related to its small total flux density. The FWHM and positions of the 43, 86, and 228 GHz components have been fixed in the multi-frequency template-matching framework. Error margins indicate the 68% confidence level.

| Frequency \[GHz\] |      Flux \[Jy\]      |
|:-----------------:|:---------------------:|
|         8         |  $40.1\,\pm\,8.5$\*   |
|        86         | $22.2\,\pm\,1.1$\*\*  |
|        228        | $10.9\,\pm\,0.55$\*\* |

: Extended flux measurements

\

QUIVER (Effelsberg 100m Telescope)\
\*\*POLAMI (IRAM 30m Telescope)

![](cphase_XZJ_time_3C84_3g_2g_chi2.pdf)

The frequency setup of the EHT in 2017 consisted of two bands, each of 2 GHz in width, centred at 227.1 GHz (LO band) and 229.1 GHz (HI band): see (cite: EHT19b) for details. For all the presented analyses, we combined data sets from both bands, using data points averaged over 2 GHz in frequency and for 120 s in time. In the EHT data sets, the polarimetric calibration relies on the calibration of ALMA (cite: Goddi19), which provides the absolute EVPA and serves as a reference site for the computation of the complex polarimetric gains for the entire EHT array (cite: EHT21a). As ALMA was present in only one-sixth of the observing scans of 3C 84, we only obtained the ALMA-based calibration for the single scan. The corresponding EVPA measurement on the short ALMA-APEX baseline is close to the north–south axis, consistent with POLAMI observations. This is in contrast to previous polarimetric analyses with the EHT (cite: EHT21a; Issaoun22; Jorstad2023), where the absolute EVPA reference was always constrained by ALMA. As a consequence, the absolute EVPA calibration was found to be challenging and dependent on additional assumptions for the remaining part of the observations, with the additional difficulties related to APEX drop-outs in the HI band and JCMT observing only the right-hand circular polarisation component, which was used as as proxy for the total intensity in a similar way to in the previous EHT analyses (cite: EHT19a; EHT22a). Hence, in the fitting to the linearly polarised source structure, we made a choice to only fit the absolute values of the fractional Fourier polarisation (corresponding to $|\breve{m}|$, the amplitude ratio of cross-hand and parallel-hand visibility components, following the notation of (cite: EHT21a)), as shown in the right panel of Fig. [4](#fig:Fit). We therefore neglect the corrupted linear polarisation phase information. As a consequence, we only interpret the absolute values of fractional polarisation of the fitted Gaussian components. In astrophysical synchrotron plasma, the following order of Stokes parameters magnitude is generally expected: $I>|P| \gg V$; circular polarisation $V$ is consequently neglected in the studies of total intensity I and linear polarisation P. Under this assumption, we can use single-polarisation JCMT data in the fitting to absolute values of Fourier fractional linear polarisation.

The high quality of the fit is quantified with the reduced $\chi^2$, which is provided in Fig. [4](#fig:Fit) for different data products used for the simultaneous fitting: visibility amplitudes, closure phases, and fractional Fourier linear polarisation (cite: EHT21a). Additionally, in Fig. [5](#fig:cphases), the closure phases observed on the APEX-SMT-JCMT triangle are compared with our model (model 3g, with three Gaussian components representing the compact region emission). Non-zero closure phases are an immediate indication of a resolved structure, inconsistent with a circular symmetry of the source (cite: Thompson17).

The dominant systematic uncertainty in the linear polarisation analysis results comes from the lack of the polarimetric leakage calibration (cite: EHT21a), which could not be directly employed for the 3C 84 data set, given the aforementioned data set issues pertaining to the uncertain, time-dependent EVPA calibration. In order to obtain a rough characterisation of the impact of the leakage on the resulting polarimetric quantities, we performed a small survey of data sets calibrated with different D-terms. We assumed the magnitude of the complex EHT array D-terms estimated and verified in previous EHT publications (cite: EHT21a; Issaoun22; Jorstad2023), but generated ten random realisations of D-term phases, subsequently refitting the polarimetric source model to data sets with different leakage calibration variants. The fractional polarisation uncertainties reported in Table [\[table:Params\]](#table:Params) reflect the results of the D-term calibration survey.

# Modelling the EHT data

![](Frapol_image.pdf)

We modelled the EHT data with circular Gaussian components, because the $(u,v)$ coverage is too sparse to reconstruct an image from it. Circular instead of elliptical Gaussian components were preferred in order to reduce the number of degrees of freedom. We used the forward modelling `eht-imaging` software (cite: Chael16) and leveraged heuristic optimisation tools implemented in `SciPy` (cite: 2020SciPy-NMeth) to search for the best-fit solution in terms of a minimum of an error function. Figure [4](#fig:Fit) presents our best-fit model to the visibility amplitudes, closure phases, and fractional polarisation as a function of the $(u,v)$ distance. Figure [6](#fig:FIm) shows the fractional polarisation of the best-fit solution. See Appendix [5](#app:AppData) for additional comments on the fitting procedure.

A certain degree of ambiguity in the compact source structure and the number of components is expected due to the large asymmetry of the EHT $(u,v)$ coverage, which provides resolving power primarily along the south–east/north–west axis; see Fig. [1](#fig:UV). In particular, we considered the choice between a two-component (2g) and a three-component (3g) model of the compact emission. The former corresponds to ten geometric degrees of freedom (i.e., not counting the amplitude gains) for the compact emission and three for the extended emission. The latter adds six degrees of freedom to the compact emission part. While in the data set used for fitting there are 86 visibility amplitudes, 14 non-trivial closure phases (all shown in Fig. [5](#fig:cphases)), and 80 absolute values of fractional linear polarisations, there are strong correlations between data points in time, frequency, and location on the $(u,v)$ plane. The presence of such correlations reduces the effective constraining power of the data set. Hence, the model selection becomes a non-trivial problem. The best-fit 2g model essentially recovers the presented geometry of E and C components with the same fractional polarisation of C and around 35% polarisation of E. While the 2g model fits the amplitudes and fractional polarisations well, it is not capable of reproducing the closure phase measurements in a joint fit to all data products, which we demonstrate in Fig. [5](#fig:cphases). This, along with earlier results obtained at lower observing frequencies (cite: Punsly21), motivates the selection of the 3g model for the presented analysis, despite it being slightly over-fitted according to the $\chi^2$ values reported in Fig. [4](#fig:Fit). Such behaviour is generally expected for an accurate model given the strong correlations present in the data.

# Multi-frequency template matching

We used circular Gaussian components to model the EHT data, determining the number of degrees of freedom required to accurately fit visibility amplitudes, closure phases, and fractional Fourier polarisation, including the modelling of station-based, time-dependent amplitude gains. This is made possible by using the template-matching technique (cite: Savolainen08; Kovalev08), which leverages prior knowledge of the source’s brightness distribution from high-frequency measurements (here 228 GHz) to estimate the source structure at lower frequencies, even if they are closer together than the lower frequency beam size. Given sufficient S/N, structures smaller than the diffraction-limited interferometric resolution can be constrained (cite: MartiVidal12). For our observations, $S/N\sim550$ at 43 GHz and $S/N\sim375$ at 86 GHz, resulting in nominal resolution limits $d_\textrm{lim}^{43\,\textrm{GHz}}=19\,\upmu\textrm{as}$ and $d_\textrm{lim}^{86\,\textrm{GHz}}=6\,\upmu\textrm{as}$, respectively. Therefore, we were able to apply the high-frequency template, given that the separation between the components comprising the template was sufficiently large. It should be noted here, that these calculations are performed under the assumption that the source’s morphology is a Gaussian. However, given the complex structure in the compact region of 3C 84 revealed here, the actual resolution may be worse. We therefore adopted the more conservative approach of restricting the resolution limit to the typical value of approximately one-fifth of the beam size (cite: Oh22). This was still possible in our case at 43 GHz (beam size $\sim100\,\upmu\textrm{as}$) and 86 GHz (beam size $\sim50\,\upmu\textrm{as}$). As in our work we investigate the overall spectral behaviour of the submas region, this approach is sufficient to get an estimate for the flux densities and fractional polarisations for each component. We also disregarded the core shift effects (cite: Paraschos21; Oh22; Paraschos23) between the images at different frequencies, because their effect is negligible for our analysis (of the order of a few tens of $\upmu$as). Our results are summarised in Table [\[table:Params\]](#table:Params). The uncertainties of the flux density measurements are on the order of $20\%$ at 15 GHz, $30\%$ at 43 GHz, $50\%$ at 86 GHz, and $15\%$ at 228 GHz (cite: EHT19c).

# Magnetic field estimate

We estimated the magnetic field strength in the core via synchrotron turnover frequency fitting. The synchrotron spectrum takes the following form (cite: Condon16): $$\begin{equation}
    S(\upnu) = S_0 \left( \frac{\upnu}{\upnu_\textrm{1}}  \right)^{\upalpha_\textrm{thick}} \left\{  1-\exp \left[ -  \left( \frac{\upnu}{\upnu_\textrm{1}}  \right)^{-(p+4)/2} \right]   \right\}, \label{eq:Turnover}
\end{equation}$$ for a homogeneous and cylindrical source, where $\upnu_\textrm{1}$ is the frequency where the opacity reaches unity, $\tau=1$, and $S_0=5.7\pm 0.3\,\textrm{Jy}$ is a multiplication constant, determined from the fit. Subsequently, $\upnu_\textrm{m}$ is calculated by determining the peak of the fitted spectrum. Following (cite: Kim19), we set $\upalpha_\textrm{thick}=0.51\pm0.10$. The parameter $p$ is the power-law slope of the electron energy distribution function and is set to $p=2$ (cite: Condon16).

We used two different prescriptions for the magnetic field strength. First we calculated the equipartition magnetic field $B_\textrm{eq}$ using (cite: Pacholczyk70) with the following form[^2]: $$\begin{equation}
    \begin{split}
    \left(\frac{B_\textrm{eq}}{\textrm{G}}\right)&= 2.7\times10^{-7}\\
    &\left[ \frac{\left(1+k_\textrm{u}\right)c_{12}\upkappa_\upnu}{f} \frac{S_\textrm{m}/\textrm{Jy}}{(\uptheta/\textrm{mas})^3}\frac{\upnu_\textrm{m}/\textrm{Hz}}{D_\textrm{L}/\textrm{Gpc}} \frac{\left(1+z\right)^{10}}{\updelta^4} \right]^{2/7}
    \end{split}
     \label{eq:Beq}.
\end{equation}$$ We note that the exponent $2/7$ only holds for $\upalpha_\textrm{thin} = 0.5$ (cite: Beck05). Here, $k_\textrm{u}$ is a ratio that provides an estimate of the energy in relativistic protons compared to electrons and $f$ is a factor denoting the fraction of the total volume of the emitting region occupied by the plasma and magnetic field in equipartition. Under the assumption of an electron-positron pair plasma (cite: Paraschos23), which is volume filling, $k_\textrm{u} = 0$ and $f = 1$. The uncertainties for $k_\textrm{u}$ and $f$ are difficult to constrain; their impact on the magnetic field strength computation is discussed below. The constant $c_{12}$ (in cgs units) is given by the following expression: $$\begin{equation}
    c_{12} = c_1^{1/2}c_2^{-1}\left(\frac{2+2\upalpha_\textrm{thick}}{1+2\upalpha_\textrm{thick}}\right)\left(\frac{\upnu_\textrm{min}^{(1+2\upalpha_\textrm{thick})/2}-\upnu_\textrm{max}^{(1+2\upalpha_\textrm{thick})/2}}{\upnu_\textrm{min}^{1+\upalpha_\textrm{thick}} - \upnu_\textrm{max}^{1+\upalpha_\textrm{thick}}}\right),
\end{equation}$$ where $c_1 = \frac{3e}{4\uppi m^3_\textrm{e}c^5} = 6.27\times10^{18}\,\textrm{[cgs]}$ and $c_2 = \frac{2e^4}{3 m^4_\textrm{e}c^7} = 2.37\times10^{-3}\,\textrm{[cgs]}$; $e$ and $m_\textrm{e}$ are the charge and mass of the electron respectively and $c$ is the speed of light. Furthermore, $\upkappa_\upnu$ is defined as $$\begin{equation}
    \upkappa_\upnu \equiv \frac{\left(\upnu_\textrm{max}/\upnu_\textrm{m}\right)^{1+\upalpha_\textrm{thick}}-1}{1+\upalpha_\textrm{thick}} \frac{\left(\upnu_\textrm{min}/\upnu_\textrm{m}\right)^{1+\upalpha_\textrm{thin}}-1}{1+\upalpha_\textrm{thin}},
\end{equation}$$ where $\upnu_\textrm{min}$ and $\upnu_\textrm{max}$ are the minimum and maximum frequency range of synchrotron radiation. We used $\upnu_\textrm{min} = 10^7\,\textrm{Hz}$ (lowest possible frequency for synchrotron emission) and $\upnu_\textrm{max} = 3\times10^{14}\,\textrm{Hz}$ (cite: Biermann87). As $[\upnu_\textrm{min}, \upnu_\textrm{max}]$ constitute an assumed frequency range, their values are presented without uncertainties. The optically thin spectral index is $\upalpha_\textrm{thin}=-0.5$ (cite: Kim19). The angular diameter is denoted as $\uptheta$ and the synchrotron peak flux density as $S_{\rm m}=9.0\pm 0.5\,\textrm{Jy}$ at the frequency $\upnu_{\rm m}$, extrapolated from the optically thin flux density (cite: Chamani21). We assumed $\updelta=1.1\pm0.1$ for the Doppler factor based on observations presented in (cite: Kim19; Punsly21; Paraschos21) and used $\uptheta=(144\pm 18)\,\upmu\textrm{as}$ (this value already includes the geometric correction discussed in (cite: Marscher83)).

Additionally, using Eq. 2 in (cite: Marscher83): $$\begin{equation}
   \left(\frac{B_\textrm{SSA}}{\rm G}\right) =10^{-50} b(\upalpha_\textrm{thin}) \left(\frac{{\uptheta}}{\rm mas}\right)^4 \left(\frac{\upnu_{\rm m}}{\rm Hz}\right)^5 \left(\frac{S_{\rm m}}{\rm Jy}\right)^{-2} \left(  \frac{\updelta}{1+z} \right).
\end{equation}$$ Our choice of $\upalpha_\textrm{thin}=-0.5$ results in $b(\upalpha_\textrm{thin})=3.2$. The resulting estimates for the magnetic field are $B_\textrm{SSA} = (2.9\pm 1.6)\,\textrm{G}$ and $B_\textrm{eq} = (5.2\pm 0.6)\,\textrm{G}$ for the core component C at 228 GHz. We point out that the $B_\textrm{SSA}$ calculation is strongly impacted by the value of $\upnu_\textrm{m}$. An increase or decrease of a few GHz would vary the value of $B_\textrm{SSA}$ by two orders of magnitude. Similarly, the $B_\textrm{eq}$ calculation strongly depends on the assumption of $k_\textrm{u}$, that is, the particle composition of the jet. Alternative assumptions of the jet composition resulting in an increase in $k_\textrm{u}$ (diffusive shock acceleration would result in values of $k_\textrm{u}\leq50$, see e.g. (cite: Bell78)) would increase the value of $B_\textrm{eq}$ by up to a factor of 3. Likewise, decreasing the value of $f$ (assuming a clumpier medium, filling only half of the total emitting region for example), would result in an increase in $B_\textrm{eq}$ by a factor of $1.2$. However, we note that the good agreement between the two magnetic field estimates indicates that the choice of $k_\textrm{u} = 0$ and $f = 1$ is reasonable. The equipartition Doppler factor required for $B_\textrm{SSA}$ to match $B_\textrm{eq}$ is $\updelta_\textrm{eq}=1.5\pm 0.4$.

Finally, we can compare $B_\textrm{eq}$ and $B_\textrm{SSA}$ to the strength of the coherent field based on the observed RM. Using Eq. 15 from (cite: Gardner66), written: $$\begin{equation}
    \textrm{RM} = 8.1\times10^5\int n_\textrm{e} B^\textrm{tot}_\parallel \textrm{d}l,
\end{equation}$$ we can compute the lower limit of the strength of the ordered field, $B^\textrm{tot}_\parallel$. Here, $n_\textrm{e}$ is the number density of the thermal electrons, which we set to $n_\textrm{e}=3\times10^4\,\textrm{cm}^{-3}$ (cite: Scharwaechter13). The path length of integration through the plasma is $\textrm{d}l$ and can be approximated by $\uppsi\times\uptheta$. Using these values, $B^\textrm{tot}_\parallel = 4.7\pm 0.6\,\textrm{mG}$, which is consistent as a lower limit to our calculations of $B_\textrm{eq}$ and $B_\textrm{SSA}$.

# Dimensionless magnetic flux

We calculated the dimensionless magnetic flux $\upphi$ using the expression for the jet power $P_\textrm{jet}$ (cite: Tchekhovskoy10), which holds for black hole spin values $\upalpha_*\leq1$: $$\begin{equation}
    \left(\frac{P_\textrm{jet}}{\dot{M}\textrm{c}^2}\right) = \frac{\upkappa}{4\uppi}\upphi^2\Omega_\textrm{H}^2\left[1+1.38\Omega_\textrm{H}^2-9.2\Omega_\textrm{H}^4\right].
\end{equation}$$ Here, $\Omega_\textrm{H}\equiv\frac{\lvert\upalpha_*\rvert}{2\left(1+\sqrt{1-\upalpha_*^2}\right)}$, $\dot{M}$ is the mass-accretion rate of 3C 84, and $\upkappa=0.05$ is a constant depending on the initial field geometry.

To determine the mass-accretion rate, we use Eq. 9 from (cite: Marrone06), in the following form (as also shown in (cite: Nagai17)): $$\begin{equation}
    \begin{split}
    \left(\frac{\dot{M}}{M_\odot\,\textrm{yr}^{-1}}\right)&= 1.3\times10^{-10}\left(1-\left(\frac{r_\textrm{out}}{r_\textrm{in}}\right)^{-(3\upbeta-1)/2}\right)^{-2/3}\\
    &\left(\frac{M_\textrm{BH}}{8.0\times10^8\,M_\odot}\right)^{4/3}
    \left(\frac{2}{3\upbeta-1}\right)^{-2/3}r_\textrm{in}^{7/6}\left(\frac{\textrm{RM}}{\textrm{rad\,m}^{-2}}\right)^{2/3}.\label{eq:mdot}
    \end{split}
\end{equation}$$ where $\upbeta=0.5$ for CDAF or $\upbeta=1.5$ for ADAF and $r_\textrm{in}$ and $r_\textrm{out}$ are the inner and outer effective radii of the accretion flow. Furthermore, $\dot{M}_\textrm{Edd} = L_\textrm{Edd}/(\epsilon c^2)$, where $\epsilon$ is an efficiency factor. Using $L_\textrm{Edd} \sim 10^{47}\,\textrm{erg\,s}^{-1}$ (cite: Plambeck14), $\epsilon=0.1$, $r_\textrm{out}\sim10^5\,R_\textrm{s}$ (cite: Nagai17), $r_\textrm{in} \sim 90\,R_\textrm{s}$ (size of C), and $\textrm{RM}=(6.06\pm 0.01)\times 10^6\,\textrm{rad/m}^2$ yields $\dot{M}=0.3\times10^{-3}M_\odot\,\textrm{yr}^{-1}$ for $\upbeta=0.5$ and $\dot{M}\sim1.1\times10^{-3}M_\odot\,\textrm{yr}^{-1}$ $\upbeta=1.5$. This computation rests on the assumption that the Faraday screen is external. Our assumption is physically motivated; the jet viewing angle used in our computations ($\upxi\sim40^\circ$) is larger than half of the intrinsic jet opening angle ($i\lesssim20^\circ$; see e.g. (cite: Paraschos21)), suggesting that we are peering through the jet sheath and boundary layer (cite: Plambeck14; Nagai17). Furthermore, at 1.3 mm, we are able to directly examine the environment of the central engine, because the opacity effects become comparatively minor.

Finally, the total luminosity of the jet in 3C 84 (cite: Rafferty06) is $P_\textrm{jet}=1.5\times 10^{44}\,\textrm{erg\,s}^{-1}$. Thus, setting $a_*=1$, we computed a range of $\upphi=41-93$. Values of $\upphi \gtrsim 50$ refer to MAD models (cite: Tchekhovskoy11; Zamaninasab14). We note here that the RM would need to be underestimated by more than an order of magnitude (e.g. due to the Faraday screen not being external) for $\upphi$ to equal its MAD saturation value. Our investigation of different flow geometries and black hole spins supports an advection-dominated accretion flow in a magnetically arrested state as a model of the jet launching system in the core of 3C 84.

[^1]: We used the formula $100\%\times\lvert\sum(Q+\upiota U)\rvert/\sum{I}$, with $I$, $Q$, and $U$ being the image domain Stokes parameters, and performed the pixel-wise summation over the whole field of view.

[^2]: Here, we assume equipartition between cosmic-ray and magnetic energy density.

</paper>

Write the methods card for this paper.