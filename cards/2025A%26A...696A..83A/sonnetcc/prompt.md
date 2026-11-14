# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A..83A\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...696A..83A",
 "title": "Deep kiloparsec view of the molecular gas in a massive star-forming galaxy at cosmic noon",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Arriagada-Neira, Sebastián",
 "n_authors": 13,
 "arxiv_id": "2410.14781",
 "doi": "10.1051/0004-6361/202452652",
 "alma_projects_linked_by_archive": [
  "2013.1.00059.S",
  "2017.1.00856.S",
  "2017.1.01045.S",
  "2019.1.01362.S"
 ]
}
```

Paper text:
<paper>
# Deep kiloparsec view of the molecular gas in a massive star-forming galaxy at cosmic noon

We present deep ($\sim$$\,$$\rm {20}~{hr}$), high-angular resolution Atacama Large Millimeter/submillimeter Array (ALMA) observations of the $\rm CO ~ (4-3)$ and $\rm [CI] ~ (1-0)$ transitions, along with the rest-frame $\rm 630 ~{\rm {\mu}m}$ dust continuum, in BX610—a massive, main-sequence galaxy at the peak epoch of cosmic star formation $(z = 2.21)$. Combined with deep Very Large Telescope (VLT) SINFONI observations of the $\rm H{\alpha}$ line, we characterize the molecular gas and star formation activity on kiloparsec scales. Our analysis reveals that the excitation of the molecular gas, as traced by the $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio, decreases with increasing galactocentric radius. While the line luminosity ratios in the outskirts are similar to those typically found in main-sequence galaxies at $z \sim 1$, the ratios in the central regions of BX610 are comparable to those observed in local starbursts. There is also a giant extra-nuclear star-forming clump in the southwest of BX610 that exhibits high star formation activity, molecular gas abundance, and molecular gas excitation. Furthermore, the central region of BX610 is rich in molecular gas $(M_{\rm mol} / M_{\rm \star} \approx 1)$; however, at the current level of star formation activity, such molecular gas is expected to be depleted in $\sim$$\,$$450~ {\rm Myr}$. This, along with recent evidence for rapid inflow toward the center, suggests that BX610 may be experiencing an evolutionary phase often referred to as wet compaction, which is expected to lead to central gas depletion and subsequent inside-out quenching of star formation activity.

# Introduction

The epoch known as cosmic noon, when the Universe was $\sim$$\,$$\rm {2-3}~{Gyr}$ old, represents the peak of the cosmic star formation rate (SFR) density (cite: madau+14), making it a critical period for studying galaxy evolution. Recent galaxy surveys have shown that the increased star formation activity during this time was primarily driven by abundant reservoirs of cold molecular gas, the fuel for star formation (cite: Tacconi+18; Walter+20; Tacconi+20). Notably, the molecular gas fraction in massive star-forming galaxies $(M_{\star} \gtrsim 10^{10.5} ~ {\rm M_{\odot}})$ at $z \sim 1-3$ was close to unity $(M_{\rm mol} / M_{\star} \approx 1)$, highlighting the important role of molecular gas in sustaining the observed high star formation rates during this epoch.

A new generation of mm/sub-mm facilities, including the Atacama Large Millimeter/submillimeter Array (ALMA), the NOrthern Extended Millimeter Array (NOEMA), and the Karl G. Jansky Very Large Array (JVLA), has provided the advanced capabilities necessary for detailed studies of molecular gas properties in normal, star-forming galaxies at high redshift. The most widely used molecular gas tracer has been the carbon monoxide (CO) molecule (cite: Bolatto+13). However, in recent years, the lower fine-structure line of atomic carbon $\rm [CI]$ $(^{3}P_{1}$ $\to$ $^{3}P_{0})$ (hereafter $\rm [CI]~({1} - {0})$) has emerged as an alternative molecular gas tracer (cite: Papadopoulos+04; Alaghband-Zadeh+13; Bothwell+17; Michiyama+21). Both theoretical (cite: Offner+14; Glover+15) and observational (cite: Ikeda+02; Kulesa+05; Requena-Torres+16; Okada+19) studies have shown that \[CI\] emission is associated with CO emission, regardless of the environment, making it a potential robust tracer of the bulk molecular gas mass (cite: Papadopoulos+04; Walter+11; Henríquez-Brocal+22). Even in metal-poor and high cosmic-ray environments where CO could be significantly photodissociated, \[CI\] emission can persist throughout the molecular gas cloud (cite: Papadopoulos+04; Bisbas+15; Bisbas+17; Glover+16). Furthermore, studies by (cite: Valentino+18; Valentino+20) have identified a tight correlation between \[CI\] and CO emission lines that is independent of redshift (for $z \lesssim 3$) and galaxy type. They also found that the \[CI\] transition can trace molecular gas mass comparably to low-*J* CO lines and dust continuum emission.

To date, estimates of molecular gas content in high-$z$ galaxies have been obtained either from large-scale surveys of star-forming galaxies (cite: Genzel+10; Tacconi+13; Daddi+10; Valentino+18; Valentino+20), or from a limited number of spatially resolved studies focusing on various subset of galaxies, including bright submillimeter galaxies (cite: Hodge+15; Chen+17), protocluster galaxies at high redshift (cite: Lee+17; Lee+21), cluster galaxies (cite: Ikeda+22), gravitationally lensed dusty galaxies (cite: Spilker+15), and compact star-forming galaxies (cite: Spilker+19). Despite significant progress, the molecular gas properties of more typical star-forming galaxies at cosmic noon on $\sim$kiloparsec scales remain relatively understudied. One area where progress has been made is in understanding the spatially resolved Kennicutt-Schmidt (KS) relation (cite: Kennicutt+98a) between total molecular gas and SFR. Studies, for example, by (cite: Genzel+13) and (cite: Freundlich+13) have demonstrated that both the slope of the KS relation and the molecular gas depletion timescale $(t_{\rm dep} = M_{\rm mol} / {\rm SFR})$ in galaxies at cosmic noon are broadly consistent with those observed in the local Universe (cite: Bolatto+17; Sun+23).

Motivated by the need to characterize the molecular gas properties on $\sim$kiloparsec scales of representative galaxies at cosmic noon, we present the deepest ALMA observation to date of a typical main-sequence galaxy at $z \sim 2$. The focus of our study, Q2343-BX610 (hereafter BX610), is a main-sequence star-forming galaxy at $z = 2.2103$ with a stellar mass of $M_{\star} = 1.55 \times 10^{11} ~ {\rm M_{\odot}}$ (cite: Tacchella+15) and a SFR ranging from $60$ to $200 ~ {\rm M_{\odot}~yr^{-1}}$, depending on the tracer or the level of dust obscuration assumed (cite: ForsterSchreiber+09; ForsterSchreiber+14; Brisbin+19). BX610 has been extensively studied across various wavelengths, including optical/near-infrared (cite: ForsterSchreiber+09; ForsterSchreiber+11A; ForsterSchreiber+11B; ForsterSchreiber+14; ForsterSchreiber+18) and far-infrared (cite: Tacconi+13; Aravena+14; Bolatto+15; Brisbin+19). $\rm H{\alpha}$ observations characterize BX610 as a rotating disk with a massive star-forming clump and no evidence of a nearby companion (cite: ForsterSchreiber+11B; ForsterSchreiber+18). The galaxy rest-frame optical morphology reveals bar- and spiral-like features (cite: ForsterSchreiber+11A). Additionally, observational evidence suggests that BX610 may host an active galactic nucleus (AGN), but it appears to be relatively weak (cite: ForsterSchreiber+14; newman+14).

Previous observational efforts to investigate the physical conditions of the molecular gas in BX610 include JVLA $\rm CO~({1} - {0})$ observations by (cite: Bolatto+15), and IRAM Plateau De Bure Interferometer (PdBI) $\rm CO~(4-3, ~7-6)$ and $\rm [CI]~(1-0, ~2-1)$ observations by (cite: Brisbin+19). However, due to depth and/or angular resolution limitations, these studies have provided only a broad overview of BX610 molecular gas properties. In this context, the new deep ($\sim$$\,$$\rm {20}~{hr}$ of ALMA time), $\sim$kiloparsec scale ALMA observations presented in this work represent a significant improvement in depth and spatial resolution. The kinematic properties of BX610 based on this dataset have already been analyzed by (cite: Genzel+23), who find that the velocity field of BX610 traced by the $\rm CO~({4} - {3})$ emission line reveals a well-defined rotating disk, with evidence for a rapid inflow of gas towards the central region. The velocity of the radial gas motion is $\sim$$\,$$\rm {95}~{km~s^{-1}}$, approximately one-third of the rotational velocity.

This paper is organized as follows. In Section [2](#sec:sec02), we present the new ALMA observations and the further data reduction, as well as the archive observations used in this work. In Section [3](#sec:sec03), we explain the methods applied to analyze the data and the equations used to derive the physical quantities. In Section [4](#sec:sec04), we present our results and discussion, and finally, in Section [5](#sec:sec05), we summarize the main conclusions. Throughout this paper, we assume a Chabrier initial mass function (IMF; (cite: Chabrier+03)) and a $\rm {\Lambda}CDM$ cosmology with $H_{0} = 70 ~ {\rm km~s^{-1}~Mpc^{-1}}$, $\Omega_{\rm M} = 0.3$, and $\Omega_{\Lambda} = 0.7$. For this cosmology, $1\ensuremath{''}$ corresponds to $\rm {8.259}~{kpc}$ at $z = 2.2103$.

# Data Products

![](Images/Figure_01.jpeg)

.

|  |  |  |  |
|:---|:--:|:--:|:--:|
|  |  |  |  |
| Parameter | Unit | Value | Reference |
|  |  |  |  |
| RA | hh:mm:ss.ss | 23:46:09.43 | (cite: Erb+06) |
| Dec | dd:mm:ss.ss | 12:49:19.21 | (cite: Erb+06) |
| Redshift |  | 2.2103 | (cite: ForsterSchreiber+09) |
| $R_{\rm eff, \,\star}$ | $\rm kpc$ | $4.44 \pm 0.08$ | (cite: ForsterSchreiber+11A) |
| $S_{\rm CO~(1-0)} {\Delta}{v}$ | $\rm Jy~km~s^{-1}$ | $0.105 \pm 0.015$ | (cite: Bolatto+15) |
| FWHM | $\rm km~s^{-1}$ | $294 \pm 49$ | (cite: Bolatto+15) |
| $S_{\rm CO~(4-3)} {\Delta}{v}$ | $\rm Jy~km~s^{-1}$ | $1.55 \pm 0.03$ | This work |
| FWHM | $\rm km~s^{-1}$ | $280 \pm 12$ | This work |
| $S_{\rm [CI]~(1-0)} {\Delta}{v}$ | $\rm Jy~km~s^{-1}$ | $0.54 \pm 0.04$ | This work |
| FWHM | $\rm km~s^{-1}$ | $296 \pm 32$ | This work |
| $S_{\rm 630 ~ {{\mu}m}}$ | $\rm mJy$ | $0.18 \pm 0.01$ | This work |
| $M_{\star}$ | $\rm 10^{11}~M_{\odot}$ | $1.55$ | (cite: Tacchella+15) |
| $\rm SFR(SED)$ | $\rm M_{\odot}~yr^{-1}$ | $144 \pm 6$ | (cite: Brisbin+19) |
| $M_{\rm mol}{\rm (CO)}$ | $\rm 10^{11}~M_{\odot}$ | $1.2 \pm 0.2$ | This work |
| $M_{\rm mol}{\rm ([CI])}$ | $\rm 10^{11}~M_{\odot}$ | $1.3 \pm 0.1$ | This work |

: Observed and derived properties of BX610.

To analyze the physical conditions of the ISM in BX610, we use ALMA observations along with archival data from the Very Large Telescope (VLT) and Hubble Space Telescope (HST). The key features of these datasets are summarized in the following subsections. The observed and derived properties of BX610 are shown in Table [1](#tab:tab01).

## ALMA

ALMA Band 4 observations of BX610 were carried out in July 2021 as part of Cycle 7 (Project ID: 2019.1.01362.S, PI: R. Herrera-Camus). The details of the data calibration and reduction were presented in (cite: Genzel+23) and (cite: Lee+24). In summary, we centered two spectral windows (SPWs) set in the Frequency-Division Mode to detect the redshifted $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ transitions with channel widths of $\rm {3.906}~{MHz}$, and the two remaining SPWs were set in the Time-Division Mode to detect the rest-frame $\rm {630}~{{\mu}m}$ dust continuum. The quasar J2253+1608 was used as the flux and bandpass calibrator, and the quasar J2350+1106 was used as the phase calibrator. The ALMA array configurations were chosen to achieve a physical resolution comparable to the Toomre length at this redshift. This resulted in observations with projected baselines of 15 m - 3.7 km that produced an angular resolution of $\approx\,0.2\ensuremath{''}$, which at the redshift of BX610 corresponds to $\approx$$\,$$\rm {1.6}~{kpc}$. We integrated for a total of $\rm {13.6}~{hr}$, which resulted in a total observing time of $\sim$$\,$$\rm {20}~{hr}$ when including the overheads.

The data were processed using the Common Astronomy Software Applications package (cite: McMullin+07) version 6.1.1.15. For visibility calibration, we used the pipeline script provided by the ALMA Regional Center staff. Continuum and cube images were produced by the `TCLEAN` task and deconvolved down to ${2} \sigma$ noise level, initially measured from the dirty map. We finally produced $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ line cubes and a $\rm {630}~{\mu m}$ dust continuum map with a matched, circular beam of $0.18\ensuremath{''} \times 0.18\ensuremath{''}$ using Briggs weighting.

To obtain the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ integrated intensity maps, we used the PYTHON package `BETTERMOMENTS`[^1] (cite: Teague+18), applying a mask based on a ${2} \sigma$ clipping of the $\rm 2 \times FWHM$ convolved spatial data. The resulting integrated intensity maps of the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ transitions and the dust continuum are shown in Figure [1](#fig:fig01). Using the 2D-Gaussian fitting task `IMFIT`, the integrated flux of the dust continuum emission was found to be $0.18 \pm 0.01 ~ {\rm mJy}$. As discussed by (cite: Lee+24), this flux value is consistent with previous ALMA Band 4 observations (#2013.1.00059S, #2017.1.00856.S, #2017.1.01045.S) within the errors, but a factor of $\sim\,2$ lower than the flux reported by (cite: Brisbin+19) based on PdBI observations.

## Very Large Telescope

We include in our study VLT/SINFONI Adaptive Optics (AO)-assisted $\rm H{\alpha}$ observations from the SINS/zC-SINF survey (cite: ForsterSchreiber+09; ForsterSchreiber+14; ForsterSchreiber+18). We refer to (cite: ForsterSchreiber+18) for a detailed description of the observation and further data reduction. In summary, the galaxy was observed in the *K*-band for an on-source time of 8.3 hr in LGS-SE AO mode. The achieved angular resolution was $0.24\ensuremath{''}$ (a physical resolution of $\approx$$\,$$\rm {2}~{kpc}$). To obtain the $\rm H{\alpha}$ flux map, we followed the line fitting described in (cite: ForsterSchreiber+18). The right-most panel of Figure [1](#fig:fig01) shows the integrated $\rm H{\alpha}$ map. The emission peaks off-center, on a region of $\sim$kiloparsec size in the southwest, and is faint in the central region of BX610 as expected from dust obscuration.

## Hubble Space Telescope

We include HST imaging of the rest-frame optical light based on WFC3/IR observations using the F160W and F110W filters. A detailed description of the observations is provided by (cite: Tacchella+15). We also use the stellar mass and visual extinction $(A_{\rm V})$ maps derived based on optical to NIR broadband spectral energy distributions as described in the same study.

# Methods

## Stacking the \[CI\] Spectra

Since one of our main goals is to analyze radial trends in the molecular gas content and excitation properties in BX610, we need to maximize the detectability of the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ emission lines across the entire galaxy. However, the signal-to-noise ratio (S/N) of the $\rm [CI]~({1} - {0})$ emission line decreases more rapidly than that of the $\rm CO~({4} - {3})$ line towards the outer regions. To enhance the detection of the $\rm [CI]~({1} - {0})$ line, we employ a spectral stacking method as described by, for example, (cite: Schruba+11) and (cite: Villanueva+21).

The stacking procedure is as follows. First, we determine the central velocity of each spaxel in the $\rm CO~({4} - {3})$ cube. Next, each $\rm [CI]~({1} - {0})$ spaxel is shifted according to the $\rm CO~({4} - {3})$ velocity field, to align the spectrum of each line of sight to zero velocity. The spectra are then averaged into radial bins defined by the galactocentric radius, with a bin width of $0.09\ensuremath{''}$—half the beamsize of the data. This approach ensures that the radial bins do not oversample the radial profiles. To extract the line intensity, we fit a single-Gaussian profile to the averaged-stacked spectra. The uncertainties for each radial bin are calculated using the following equation, $$\begin{equation}
        u = \sigma \sqrt{N} \Delta v,
    
\end{equation}$$ where $\sigma$ is the RMS of the emission-free portion of the stacked spectrum, $N$ is the number of channels included in the mask, and $\Delta v$ is the channel width in $\rm km~s^{-1}$. To ensure reliable detection, we only consider $\rm [CI]~({1} - {0})$ averaged-stacked spectra that exceed the $5 \sigma$ level. Without stacking, the $\rm [CI]~({1} - {0})$ line is initially detected up to 0.7 times one effective stellar radius. By stacking the data, on the other hand, we extend the reliable detection range beyond one stellar effective radius.

## Molecular Gas Mass

Molecular gas masses are computed from the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ line luminosities, which are defined by (cite: Solomon+05) as, $$\begin{equation}
        L'_{\rm line} ~ {\rm \Big[ K ~ km ~ s^{-1} ~ pc^{2} \Big]} = 3.25 \times 10^{7} S_{\rm line} ~ {\Delta}{v} ~ \nu_{\rm obs}^{-2} ~ (1 + z)^{-3} ~ D_{\rm L}^{2},
    
\end{equation}$$ where $S_{\rm line} {\Delta}{v}$ is the measured velocity-integrated line flux in $\rm Jy~km~s^{-1}$, $\nu_{\rm obs}$ is the observed line frequency in $\rm GHz$, $z$ is the redshift of the source, and $D_{\rm L}$ is the luminosity distance in $\rm Mpc$.

The total cold molecular gas mass, $M_{\rm mol}$, is then derived from the $\rm CO~({4} - {3})$ line luminosity as, $$\begin{equation}
        M_{\rm mol} ~ {\rm \big[M_{\odot}\big]} = \alpha_{\rm CO} ~ R_{14} ~ L'_{\rm CO~(4-3)},
    
\end{equation}$$ where $\alpha_{\rm CO}$ is the luminosity-to-molecular-gas-mass conversion factor, including a 36% contribution from helium, and $R_{14} = L'_{\rm CO~(1-0)} / L'_{\rm CO~(4-3)}$ is the line luminosity ratio between the $J = 4 \to 3$ and $J = 1 \to 0$ transitions.

Several studies (cite: Leroy+11; Genzel+12; Narayanan+12; Bolatto+13; Sandstrom+13) have shown that the $\alpha_{\rm CO}$ conversion factor can result in a wide range of values depending on the galaxy properties, including the density, temperature, and metallicity of the molecular clouds. While for local (U)LIRGs and starburst galaxies a value of $\alpha_{\rm CO} = 0.8 ~ {\rm M_{\odot}~(K~km~s^{-1}~pc^{2})^{-1}}$ is typically assumed (cite: Downes+98), high redshift star-forming galaxies at the massive end of the main-sequence tend to have $\alpha_{\rm CO}$ values comparable to the standard Milky Way value of $\alpha_{\rm MW} = 4.36 ~ {\rm M_{\odot}~(K~km~s^{-1}~pc^{2})^{-1}}$ (cite: Bolatto+13; Tacconi+20).

To derive the $\alpha_{\rm CO}$ value for BX610, we follow the calibration presented in (cite: Genzel+15) (cite: Tacconi+18), which combines the recipes given by (cite: Genzel+12) and (cite: Bolatto+13) through the geometric mean of both empirical functions. The $\alpha_{\rm CO}$ value based on the metallicity of the gas is given by, $$\begin{align}
        \alpha_{\rm CO} & = \alpha_{\rm MW} \sqrt{10^{-1.27 \times \left(12 + \log{\rm (O/H)} - 8.67\right)}} \nonumber\\
                        & \qquad \qquad \quad \times \sqrt{0.67 \exp{\left[0.36 \times 10^{- \left(12 + \log{\rm (O/H)} - 8.67\right)}\right]}}
    
\end{align}$$ where $\rm 12 + \log{(O/H)}$ is the metallicity on the (cite: Pettini+04) calibration scale, denoted as, $$\begin{equation}
        {\rm 12 + \log{(O/H)}}_{\rm PP04} = a - 0.087 \left[\log{(M_{\star}) - b}\right]^{2},
    
\end{equation}$$ with $a = 8.74 \pm 0.06$ and $b = (10.4 \pm 0.05) + (4.46 \pm 0.3) \times \log{(1 + z)} - (1.78 \pm 0.4) \times [\log{(1 + z)}]^{2}$ (cite: Genzel+15). Based on the total stellar mass of BX610, we find a metallicity value of $\rm 12 + \log{(O/H)} = 8.65 \pm 0.07$, which yields an $\alpha_{\rm CO} = 4.51 \pm 0.60 ~ {\rm M_{\odot}~(K~km~s^{-1}~pc^{2})^{-1}}$.

The $R_{14}$ line luminosity ratio converts the observed $\rm CO~({4} - {3})$ line luminosity into the $\rm CO~({1} - {0})$ line luminosity. (cite: Bolatto+15) conducted $\rm CO~({1} - {0})$ observations on BX610 using the JVLA and detect a total line luminosity of $L'_{\rm CO~(1-0)} = (2.6 \pm 0.2) \times 10^{10} ~ {\rm K~km~s^{-1}~pc^{2}}$, which yields a line luminosity ratio of $R_{14} = 1.1 \pm 0.1$. Under these assumptions and values, we find a molecular gas mass of $M_{\rm mol} = (1.2 \pm 0.2) \times 10^{11} ~ {\rm M_{\odot}}$.

Alternatively, $M_{\rm mol}$ can be derived from the $\rm [CI]~({1} - {0})$ emission line (cite: Weiss+05; Walter+11; Alaghband-Zadeh+13; Bothwell+17; Popping+17; Valentino+18), based on an estimated atomic mass of carbon, $M_{\rm [CI]}$, and the assumption of a given neutral atomic carbon abundance $X{\rm [CI]} / X{\rm [H_{2}]}$. The atomic carbon mass is estimated from the $\rm [CI]~({1} - {0})$ line luminosity emission following the formula presented by (cite: Weiss+05), $$\begin{equation}
        M_{\rm [CI]} ~ {\rm \big[M_{\odot}\big]} = 5.706 \times 10^{-4} ~ Q(T_{\rm ex}) ~ \frac{\exp{(T_{1} / T_{\rm ex})}}{3} ~ L'\:\!\!_{\rm [CI]~(1-0)},
    
\end{equation}$$ where $Q(T_{\rm ex}) = 1 + 3 \exp{(-T_{1} / T_{\rm ex})} + 5 \exp{(T_{2} / T_{\rm ex})}$ is the partition function, $T_{\rm ex}$ is the excitation temperature, and $T_{1} = 23.6 ~ {\rm K}$ and $T_{2} = 62.5 ~ {\rm K}$ are the transition energy levels above ground state. (cite: Brisbin+19) recently measured $T_{\rm ex}$ for BX610 based on the $L'\:\!\!_{\rm [CI]~(2-1)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio and obtained a value of $T_{\rm ex} = 31.8 \pm 6.9 ~ {\rm K}$, which is comparable to the typical dust temperature of $T_{\rm dust} \sim 32 ~ {\rm K}$ found in massive $(M_{\star} \sim 10^{11}-10^{11.5} ~ {\rm M_{\odot}})$, main-sequence galaxies at $z \sim 2$ (cite: Magnelli+14; Genzel+15; Schreiber+18). We then estimate an atomic carbon mass value of $M_{\rm [CI]} = (8.3 \pm 0.9) \times 10^{6} ~ {\rm M_{\odot}}$.

To convert the carbon mass into a molecular gas mass, we need to assume a neutral atomic carbon abundance, $X{\rm [CI]} / X{\rm [H_{2}]} = M_{\rm [CI]} / 6 M_{\rm H_{2}}$. For instance, (cite: Valentino+18) compare the molecular hydrogen masses derived from CO and dust in a sample of main-sequence galaxies at $z \sim 1.2$ and find abundances that range between $1-13 \times 10^{-5}$, with a weighted mean of $1.5 \times 10^{-5}$. Assuming this mean abundance, we measure a molecular hydrogen mass of $M_{\rm H_{2}} = (9.5 \pm 0.7) \times 10^{10} ~ {\rm M_{\odot}}$, which results in a molecular gas mass of $M_{\rm mol} = (1.3 \pm 0.1) \times 10^{11} ~ {\rm M_{\odot}}$ (i.e., consistent with our CO-based measurement).

These CO- and \[CI\]-based molecular gas masses agree with the value reported previously by (cite: Bolatto+15), who estimated a molecular gas mass of $M_{\rm mol} = (1.1 \pm 0.1) \times 10^{11} ~ {\rm M_{\odot}}$. However, these are a factor of $\sim\,2$ lower than the value found by (cite: Brisbin+19), who reported a molecular gas mass of $M_{\rm mol} = (2.1 \pm 0.3) \times 10^{11} ~ {\rm M_{\odot}}$. This could be explained because (cite: Brisbin+19), as described in Section [2.1](#sec:alma), measured a PdBI dust continuum that is a factor of $\sim\,2$ larger than the value reported in this work and in (cite: Lee+24).

## Star Formation Rate

We measure the SFR from the $\rm H{\alpha}$ line using the calibration by (cite: Kennicutt+98a), modified for a (cite: Chabrier+03) IMF, as follows, $$\begin{equation}
        {\rm SFR_{H{\alpha}} ~ \Big[ M_{\odot} ~ yr^{-1} \Big]} = 4.7 \times 10^{-42} ~ L_{\rm H{\alpha}, \,corr},
    
\end{equation}$$ where $L_{\rm H{\alpha}, \,corr}$ is the $\rm H{\alpha}$ luminosity in $\rm erg~s^{-1}$ corrected for attenuation $A_{\rm H\alpha}$, i.e., $L_{\rm H{\alpha}, \,corr} = L_{\rm H{\alpha}, \,obs} \times 10^{0.4 A_{\rm H{\alpha}}}$. For the attenuation $A_{\rm H\alpha}$, we use the extinction radial profiles measured by (cite: Tacchella+18) based on HST observations of the F438W $(B)$ $-$ F814W $(I)$ index color. We assume a $E(B-V)_{\rm star} / E(B-V)_{\rm gas}$ ratio of 0.44 (cite: Calzetti+00). Under these assumptions, we obtain a SFR of $140 ~ {\rm M_{\odot}~yr^{-1}}$.

![](Images/Figure_02.jpeg)

Additionally, in dusty environments such as the center of galaxies, the luminosity of young massive stars is frequently absorbed and then re-emitted in the IR, with an emission peak near $\rm {100}~{{\mu}m}$ (cite: Lutz+16). Therefore, the infrared emission can be a proxy for estimating the dust-obscured star formation. As can be seen from Figure [1](#fig:fig01), the molecular gas content as traced by the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ transitions peaks at the center of the galaxy; however, the $\rm H{\alpha}$ line in this region is very faint. This is the result of strong dust obscuration in the center, where a correction based on the attenuation $A_{\rm H{\alpha}}$ measured from HST imaging is likely to underestimate the total star formation activity significantly. For this reason, in the central region of BX610, we use the ALMA dust continuum to measure the obscured star formation. First, we scale the ALMA Band 4 dust continuum flux to calculate the rest-frame $\rm {70}~{{\mu}m}$ flux assuming a modified black-body (cite: Casey+12) with a spectral emissivity index $\beta = 2$ and a dust temperature $T_{\rm dust} = 30 ~ {\rm K}$, as determined by (cite: Brisbin+19). The resulting flux is $S_{\rm cont, \,70 ~ {\mu}m} = 13.2 ~ {\rm mJy}$. Finally, we use the calibration by (cite: Calzetti+10) to measure the SFR based on the $\rm {70}~{{\mu}m}$ continuum emission, which is given by, $$\begin{equation}
        {\rm SFR_{70} ~ \Big[ M_{\odot} ~ yr^{-1} \Big]} = 5.9 \times 10^{-44} ~ L_{70},
    
\end{equation}$$ where $L_{70}$ is the luminosity at $\rm {70}~{{\mu}m}$. Under these assumptions, we obtain a SFR of $114 ~ {\rm M_{\odot}~yr^{-1}}$. Nevertheless, the dust continuum-based method has its own limitations. If we assume a dust temperature of $T_{\rm dust} = 40 ~ {\rm K}$, the resulting SFR increases by a factor of 3.8. On the other hand, assuming a spectral emissivity index of $\beta = 1.5$, the SFR decreases by a factor of 3.0. Despite all these limitations, if we compare the obscured and unobscured SFR as traced by the dust continuum and uncorrected $\rm H{\alpha}$ emission, respectively, we measure an obscured fraction of star formation of $0.84$. This is consistent with what has been observed in other massive star-forming galaxies at $z \sim 2$ (cite: Bethermin+15).

# Results

## Molecular Gas Excitation

With the development of wideband receivers that can simultaneously detect the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ transitions in galaxies within certain redshift ranges (such as BX610 at $z \approx 2$), the $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio has become an important tracer of both molecular gas chemistry and excitation (cite: Alaghband-Zadeh+13; Bisbas+15; Bothwell+17; Valentino+18; Valentino+20; Michiyama+21). However, considering that the excitation temperature of the $\rm [CI]~({1} - {0})$ emission line is only about 1.5 times higher than that of the $\rm CO~({2} - {1})$ emission line, and the critical density of the $\rm [CI]~({1} - {0})$ line is approximately 4.4 times lower than that of the $\rm CO~({1} - {0})$ transition (cite: Carilli+13), we expect molecular gas excitation to be the dominant effect traced by the $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio.

![](Images/Figure_03.jpeg)

To date, most studies have focused on global measurements of the $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio at high redshift. For example, in main-sequence star-forming galaxies at $z \sim 1$, (cite: Valentino+20) find an average value of $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)} = 2.13 \pm 0.31$. In the case of BX610, however, we now have the opportunity to explore excitation conditions on kiloparsec scales, extending out to one stellar effective radius thanks to our stacking technique. The left panel of Figure [2](#fig:fig02) presents the $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio map, normalized to the average value found in $z \sim 1$ main-sequence galaxies (cite: Valentino+20). We note that the molecular gas in the central regions of BX610 is significantly more excited than in the outskirts, with a line ratio nearly twice the typical global value found in $z \sim 1$ main-sequence galaxies. Interestingly, the spiral arm extending southward, next to the giant star-forming clump detected in $\rm H\alpha$ emission, exhibits a line ratio comparable to that of $z \sim 1$ main-sequence galaxies.

The right panel of Figure [2](#fig:fig02) displays the radial profile of the $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio, with the radius normalized to the effective stellar radius in the bottom x-axis. At each radius, the profile is calculated by taking the ratio of the summed $\rm CO~({4} - {3})$ line luminosities to the stacked $\rm [CI]~({1} - {0})$ line luminosities. The emission from the star-forming clump is masked (based on the area marked by the red dashed aperture on the left panel) and shown separately (in red). In the central region $(\lesssim 0.5 ~ {R_{\rm eff, \,\star}})$ of BX610, the line luminosity ratio is comparable to that found in local (U)LIRGs (cite: Papadopoulos+12). Moving outwards, at around $r \sim 0.5 ~ {R_{\rm eff, \,\star}}$, the ratio decreases to levels similar to those observed in SMGs at $z \sim 2-4$ (cite: Valentino+20). Finally, in the range of $r \sim [0.75 - 1.25] ~ {R_{\rm eff, \,\star}}$, the line luminosity ratio is comparable to the typical values found in main-sequence star-forming galaxies at $z \sim 1$ (cite: Valentino+20). The star-forming clump, located at $r \sim 0.8 ~ {R_{\rm eff, \,\star}}$, exhibits a line luminosity ratio similar to that in the center of BX610, indicating elevated molecular gas excitation due to intense star formation. Notably, the global line luminosity ratio in BX610, $L'_{\rm CO~(4-3)} ~ \big/ ~ L'\:\!\!_{\rm [CI]~(1-0)} = 2.7 \pm 0.7$, is consistent with that observed in $z \sim 1$ main-sequence galaxies (cite: Valentino+20). This highlights the importance of spatially resolved observations in revealing the full range of molecular excitation conditions within galaxies, especially in regions of elevated star formation activity, such as central areas or extra-nuclear star-forming clumps.

## Stellar, Molecular, and Star Formation Rate Radial Profiles

![](Images/Figure_04.jpeg)

Figure [3](#fig:fig03) presents, from left to right, the radial profiles of stellar mass $(\Sigma_{\star})$, molecular gas mass $(\Sigma_{\rm mol})$, and SFR $(\Sigma_{\rm SFR})$ surface densities in BX610. Similar to Figure [2](#fig:fig02), we mask the emission from the star-forming clump in all three panels and represent it as a single red point. The middle panel shows the molecular gas radial profile based on the CO emission. We choose the CO-based over the \[CI\]-based profile because CO emission extends farther across the disk, enabling the study of molecular gas surface density up to a radius of $\sim$$\,$$\rm {1.5}~{\textit{R}_{eff, \,\star}}$. In the right panel, we present the radial profile of the SFR derived from extinction-corrected $\rm H{\alpha}$ emission (black squares) and from dust continuum emission (green squares). In the central region $(\lesssim 0.5 ~ {R_{\rm eff, \,\star}})$, where ALMA detects dust continuum and $\rm H{\alpha}$ emission is faint, the dust continuum-based SFR is approximately five times higher than the extinction-corrected $\rm H{\alpha}$-based SFR. This discrepancy is likely due to the optical extinction correction from (cite: Tacchella+18) being insufficient to fully account for the significant dust obscuration in the central region of BX610. However, it is important to note that the infrared-based SFR here is derived from dust continuum observations at a wavelength away from the peak of the infrared SED, introducing significant uncertainties. To obtain a more accurate measurement of the total SFR in the central region of BX610, ALMA dust continuum observations closer to the SED peak, such as those in Bands 8 or 9 (rest-frame $\sim$$\,$$\rm {150}~{{\mu}m}$), are required.

Additionally, we observe that both the star-forming clump and the disk have similar stellar mass surface densities values at $r \sim 0.8 ~ {R_{\rm eff, \,\star}}$. However, the clump shows slightly higher average values of $\Sigma_{\rm mol}$ and significantly higher values of $\Sigma_{\rm SFR}$ at this galactocentric distance than the latter. This suggests that the elevated star formation activity in the clump is a result of the greater concentration of molecular gas compared to other regions of the disk. The similarity in $\Sigma_{\star}$ values between the disk and the clump at $r \sim 0.8 ~ {R_{\rm eff, \,\star}}$ suggests that the star formation activity is so recent that it has not yet led to a significant increase in the stellar mass of the clump region.

The left panel of Figure [4](#fig:fig04) shows the radial profile of the molecular gas fraction, $\mu_{\rm mol} = M_{\rm mol} / M_{\star}$, which serves as an indicator of the gas available for star formation relative to the existing stellar content. We observe that in the central region $(\lesssim 0.4 ~ {R_{\rm eff, \,\star}})$ of BX610, the molecular gas fraction is close to unity, and then it decreases to $\mu_{\rm mol} \approx 0.5$ beyond one stellar effective radius. The global molecular gas fraction in BX610 is comparable to that measured in main-sequence star-forming galaxies at $z \sim 2$ (cite: Tacconi+20), but this is a result of averaging the high molecular gas fraction of $\mu_{\rm mol} \approx 1$ measured at the central $\sim$$\,$$\rm {2}~{kpc}$ of BX610 with the $\mu_{\rm mol} \approx 0.5$ in the outer parts. The star-forming clump in the southwest has an even higher molecular gas fraction than the central region $(\mu_{\rm mol} \approx 1.4)$, which is consistent with the elevated star formation activity traced by the $\rm H{\alpha}$ line. However, it is important to note that in the dusty central region of BX610, the SED-derived stellar mass may be underestimated.

The right panel of Figure [4](#fig:fig04) shows the molecular gas depletion time, $t_{\rm dep} = M_{\rm mol} / {\rm SFR}$, which represents the time required to deplete the molecular gas reservoirs at the current rate of star formation. In the inner $\sim$$\,$$\rm {0.5}~{\textit{R}_{eff, \,\star}}$ ($\sim$$\,$$\rm {2}~{kpc}$) radius, the depletion timescale varies depending on whether we assume the extinction-corrected $\rm H{\alpha}$-based (black squares) or the dust continuum-based SFR (green squares). Given the elevated concentration of molecular gas in the center and the strong dust continuum detected with ALMA, it is possible that the latter may be more representative of the total SFR in the nuclear region of BX610. If that is the case, then the depletion time decreases towards the center, reaching values of $\approx 450 ~ {\rm Myr}$, which is consistent with depletion timescales measured in massive, star-forming galaxies at $z \sim 2$ (cite: Tacconi+20). The star-forming clump is the region with the lowest depletion time in BX610: the current level of star formation activity should exhaust the molecular gas in only $\approx$$\,$$\rm {250}~{Myr}$. Moreover, the estimates derived on the timescales for gas to be depleted by $\rm SFR$ could be even shorter, given that ionized gas outflows are also observed at those locations (cite: ForsterSchreiber+14).

Placing these results in the broader context of galaxy evolution at cosmic noon, we infer that BX610 is likely in a phase where the rapid inflow of molecular gas into the central region, as reported by (cite: Genzel+23), has created a gas-rich nucleus $(\mu_{\rm mol} \approx 1)$, driving a high central star formation rate. This phase is commonly referred to as the wet compaction (cite: Dekel+14; Zolotov+15; Tacchella+16b). Following this phase, galaxies are expected to cease star formation in their centers before the outskirts, driven by a steep decline in the molecular gas fraction in the central kiloparsec region—a pattern opposite to what is observed in BX610 but consistent with findings in compact star-forming galaxies at $z \sim 2$ in the process of inside-out quenching (cite: Spilker+19).

## Kennicutt-Schmidt Law

![](Images/Figure_05.jpeg)

We explore the relationship between molecular gas surface density $(\Sigma_{\rm mol})$ and star formation rate surface density $(\Sigma_{\rm SFR})$, as described by the Kennicutt-Schmidt law (cite: Schmidt+59; Kennicutt+98a). This relationship is key to understanding how efficiently cold gas is converted into stars across different environments (cite: Genzel+10; Freundlich+13; Tacconi+13; Hodge+15; Chen+17; Sun+23; Villanueva+24). Figure [5](#fig:fig05) shows the resolved KS relation for BX610, with data points color-coded by radial distance and distinguished by shape according to specific regions within the galaxy. The figure is based on measurements from apertures across BX610, each with a diameter of $0.18\ensuremath{''}$ (matching the beam size) and centers separated by $0.09\ensuremath{''}$ to minimize flux loss from overlapping apertures. For the disk and clump regions, SFR values are derived from extinction-corrected $\rm H{\alpha}$ fluxes, while for the central regions, they are based on the ALMA dust continuum emission. Note that the use of $\rm H{\alpha}$-based $\rm SFR$ for the center regions would result in a higher value of the molecular gas depletion time, as can be seen in the right panel of Figure [4](#fig:fig04).

Overall, the $\sim$kiloparsec-scale regions in BX610 align with the trend observed in spatially resolved studies of other massive, star-forming galaxies at $z \sim 1-2$ (cite: Tacconi+13; Freundlich+13; Genzel+13). Disk regions (circles) exhibit depletion timescales that scatter around $\sim$$\,$$\rm {1}~{Gyr}$, with variations of about a factor of $\sim\,2$. As regions approach the center of BX610 (crosses), depletion times shorten, reaching close to $\sim$$\,$$\rm {450}~{Myr}$. Notably, the extra-nuclear star-forming clump (stars) is the region in BX610 with the highest star formation efficiency, with a short depletion time of only $\sim$$\,$$\rm {250}~{Myr}$. Applying an ordinary least-squares bisector fit to all the regions in BX610, we find that $\log{(\Sigma_{\rm SFR})} = (1.27 \pm 0.05) \times \log{(\Sigma_{\rm mol})} - (3.68 \pm 0.17)$.

Similar to the case of the star-forming galaxy EGS13011166 at $z \approx 1.5$ (cite: Genzel+13), the fit will depend on the method by which the correction for dust obscuration is implemented. For EGS13011166, the slope ranges from 0.8 to 1.7, depending on the chosen extinction model. However, for the preferred mixed dust-gas model, (cite: Genzel+13) reported a super-linear slope of $N = 1.14 \pm 0.1$, which is comparable, within uncertainties and assumptions, to the measured slope in BX610 of $N = 1.27 \pm 0.1$.

# Conclusions

We have conducted deep, high-angular-resolution $(0.18\ensuremath{''})$ ALMA Band 4 observations targeting the molecular gas traced by the $\rm CO~({4} - {3})$ and $\rm [CI]~({1} - {0})$ transitions in BX610, a massive main-sequence galaxy at $z = 2.21$. These observations, combined with VLT/SINFONI AO-assisted $\rm H{\alpha}$ emission line data (cite: ForsterSchreiber+18), have allowed us to characterize the molecular gas properties and star formation activity on $\sim$kiloparsec scales, spanning from the central regions to at least $\sim\,1.5$ ($\sim$$\,$$\rm {7}~{kpc}$) stellar effective radius in this typical star-forming galaxy at cosmic noon.

Our key findings are as follows:

1.  By using the $L'_{\rm CO~(4-3)} / L'\:\!\!_{\rm [CI]~(1-0)}$ line luminosity ratio as a tracer of molecular gas excitation in BX610, we find that the central region and the extra-nuclear, giant star-forming clump exhibit excitation levels comparable to those observed in nearby (U)LIRGs (cite: Papadopoulos+12). Beyond $\sim$$\,$$\rm {0.5}~{\textit{R}_{eff, \,\star}}$, and on average across the disk, the molecular gas excitation conditions in BX610 resemble those typically found in normal star-forming galaxies at $z \sim 1$ (cite: Valentino+20).

2.  The molecular gas fraction measured in the inner $\sim$$\,$$\rm {2}~{kpc}$ ($\sim$$\,$$\rm {0.5}~{\textit{R}_{eff, \,\star}}$) of BX610 and the giant star-forming clump in the southwest is high $(\mu_{\rm mol} \approx 1)$, resulting in intense star formation activity. Overall, the molecular gas fraction in the disk $(\mu_{\rm mol} \approx 0.5-0.7)$ is comparable to that globally measured in main-sequence, massive star-forming galaxies at $z \approx 2$ (cite: Tacconi+20). The molecular gas depletion times measured in the central region and in the giant star-forming clump are $\sim$$\,$$\rm {450}~{Myr}$ and $\sim$$\,$$\rm {250}~{Myr}$, respectively.

3.  The rapid transport of molecular gas to the central region of BX610 (cite: Genzel+23), combined with the high central molecular gas fraction and short depletion timescale, suggests that BX610 may be undergoing a phase similar to the wet compaction scenario described in models by (cite: Dekel+14), (cite: Zolotov+15), and (cite: Tacchella+18). In this phase, the concentration of gas in the galaxy’s core drives intense star formation, which eventually leads to the inside-out quenching of star formation.

4.  The $\sim$kiloparsec-scale regions in BX610 exhibit significant variations but generally align with the spatially-resolved KS relation observed in other massive, star-forming galaxies at $z \sim 1-2$ (cite: Freundlich+13; Genzel+13; Tacconi+13). The overall slope and the depletion timescale measured in BX610 are $N = 1.27 \pm 0.05$ and $t_{\rm dep}\approx 800 \pm 400 ~ {\rm Myr}$, respectively.

In summary, the deep, spatially-resolved ALMA and VLT/SINFONI observations of BX610 provide one of the most detailed maps of molecular gas and star formation activity in a main-sequence, star-forming galaxy at cosmic noon. However, the absence of reliable measurements of obscured star formation in the central region limits our ability to interpret its physical conditions fully. Future ALMA observations at wavelengths closer to the SED peak (Band 8 or Band 9) or measurements of the Paschen-$\alpha$ line with JWST/MIRI are essential for addressing this issue and obtaining a more comprehensive understanding of the BX610 central region.

# Acknowledgements

S.A.-N. and R.H.-C. thank the Max Planck Society for support under the Partner Group project “The Baryon Cycle in Galaxies” between the Max Planck for Extraterrestrial Physics and the Universidad de Concepción. S.A.-N. and R.H.-C. also gratefully acknowledge financial support from ANID BASAL projects FB210003. V. V. acknowledges support from the ALMA-ANID Postdoctoral Fellowship under the award ASTRO21-0062. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01362.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

80 natexlab

(ref: Alaghband-Zadeh+13) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, MNRAS, 435, 1493

(ref: Aravena+14) Aravena, M., Hodge, J. A., Wagg, J., et al. 2014, MNRAS, 442, 558

(ref: Bethermin+15) Béthermin, M., Daddi, E., Magdis, G., et al. 2015, A&A, 573, A113

(ref: Bisbas+15) Bisbas, T. G., Papadopoulos, P. P., & Viti, S. 2015, ApJ, 803, 37

(ref: Bisbas+17) Bisbas, T. G., van Dishoeck, E. F., Papadopoulos, P. P., et al. 2017, ApJ, 839, 90

(ref: Bolatto+15) Bolatto, A. D., Warren, S. R., Leroy, A. K., et al. 2015, ApJ, 809, 175

(ref: Bolatto+13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Bolatto+17) Bolatto, A. D., Wong, T., Utomo, D., et al. 2017, ApJ, 846, 159

(ref: Bothwell+17) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825

(ref: Brisbin+19) Brisbin, D., Aravena, M., Daddi, E., et al. 2019, A&A, 628, A104

(ref: Calzetti+00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Calzetti+10) Calzetti, D., Wu, S. Y., Hong, S., et al. 2010, ApJ, 714, 1256

(ref: Carilli+13) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Casey+12) Casey, C. M. 2012, MNRAS, 425, 3094

(ref: Chabrier+03) Chabrier, G. 2003, PASP, 115, 763

(ref: Chen+17) Chen, C.-C., Hodge, J. A., Smail, I., et al. 2017, ApJ, 846, 108

(ref: Daddi+10) Daddi, E., Bournaud, F., Walter, F., et al. 2010, ApJ, 713, 686

(ref: Dekel+14) Dekel, A. & Burkert, A. 2014, MNRAS, 438, 1870

(ref: Downes+98) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: Erb+06) Erb, D. K., Steidel, C. C., Shapley, A. E., et al. 2006, ApJ, 646, 107

(ref: ForsterSchreiber+09) Förster Schreiber, N. M., Genzel, R., Bouché, N., et al. 2009, ApJ, 706, 1364

(ref: ForsterSchreiber+14) Förster Schreiber, N. M., Genzel, R., Newman, S. F., et al. 2014, ApJ, 787, 38

(ref: ForsterSchreiber+18) Förster Schreiber, N. M., Renzini, A., Mancini, C., et al. 2018, ApJS, 238, 21

(ref: ForsterSchreiber+11A) Förster Schreiber, N. M., Shapley, A. E., Erb, D. K., et al. 2011a, ApJ, 731, 65

(ref: ForsterSchreiber+11B) Förster Schreiber, N. M., Shapley, A. E., Genzel, R., et al. 2011b, ApJ, 739, 45

(ref: Freundlich+13) Freundlich, J., Combes, F., Tacconi, L. J., et al. 2013, A&A, 553, A130

(ref: Genzel+23) Genzel, R., Jolly, J. B., Liu, D., et al. 2023, ApJ, 957, 48

(ref: Genzel+12) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69

(ref: Genzel+10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: Genzel+13) Genzel, R., Tacconi, L. J., Kurk, J., et al. 2013, ApJ, 773, 68

(ref: Genzel+15) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: Glover+16) Glover, S. C. O. & Clark, P. C. 2016, MNRAS, 456, 3596

(ref: Glover+15) Glover, S. C. O., Clark, P. C., Micic, M., & Molina, F. 2015, MNRAS, 448, 1607

(ref: Henríquez-Brocal+22) Henrı́quez-Brocal, K., Herrera-Camus, R., Tacconi, L., et al. 2022, A&A, 657, L15

(ref: Hodge+15) Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJL, 798, L18

(ref: Ikeda+02) Ikeda, M., Oka, T., Tatematsu, K., Sekimoto, Y., & Yamamoto, S. 2002, ApJS, 139, 467

(ref: Ikeda+22) Ikeda, R., Tadaki, K.-i., Iono, D., et al. 2022, ApJ, 933, 11

(ref: Kennicutt+98a) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: Kulesa+05) Kulesa, C. A., Hungerford, A. L., Walker, C. K., Zhang, X., & Lane, A. P. 2005, ApJ, 625, 194

(ref: Lee+24) Lee, M. M., Steidel, C. C., Brammer, G., et al. 2024, MNRAS, 527, 9529

(ref: Lee+21) Lee, M. M., Tanaka, I., Iono, D., et al. 2021, ApJ, 909, 181

(ref: Lee+17) Lee, M. M., Tanaka, I., Kawabe, R., et al. 2017, ApJ, 842, 55

(ref: Leroy+11) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12

(ref: Lutz+16) Lutz, D., Berta, S., Contursi, A., et al. 2016, A&A, 591, A136

(ref: madau+14) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Magnelli+14) Magnelli, B., Lutz, D., Saintonge, A., et al. 2014, A&A, 561, A86

(ref: McMullin+07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Michiyama+21) Michiyama, T., Saito, T., Tadaki, K.-i., et al. 2021, ApJS, 257, 28

(ref: Narayanan+12) Narayanan, D., Krumholz, M. R., Ostriker, E. C., & Hernquist, L. 2012, MNRAS, 421, 3127

(ref: newman+14) Newman, S. F., Buschkamp, P., Genzel, R., et al. 2014, ApJ, 781, 21

(ref: Offner+14) Offner, S. S. R., Bisbas, T. G., Bell, T. A., & Viti, S. 2014, MNRAS, 440, L81

(ref: Okada+19) Okada, Y., Güsten, R., Requena-Torres, M. A., et al. 2019, A&A, 621, A62

(ref: Papadopoulos+12) Papadopoulos, P. P. & Geach, J. E. 2012, ApJ, 757, 157

(ref: Papadopoulos+04) Papadopoulos, P. P., Thi, W. F., & Viti, S. 2004, MNRAS, 351, 147

(ref: Pettini+04) Pettini, M. & Pagel, B. E. J. 2004, MNRAS, 348, L59

(ref: Popping+17) Popping, G., Decarli, R., Man, A. W. S., et al. 2017, A&A, 602, A11

(ref: Requena-Torres+16) Requena-Torres, M. A., Israel, F. P., Okada, Y., et al. 2016, A&A, 589, A28

(ref: Sandstrom+13) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Schmidt+59) Schmidt, M. 1959, ApJ, 129, 243

(ref: Schreiber+18) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: Schruba+11) Schruba, A., Leroy, A. K., Walter, F., et al. 2011, AJ, 142, 37

(ref: Solomon+05) Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677

(ref: Spilker+15) Spilker, J. S., Aravena, M., Marrone, D. P., et al. 2015, ApJ, 811, 124

(ref: Spilker+19) Spilker, J. S., Bezanson, R., Weiner, B. J., Whitaker, K. E., & Williams, C. C. 2019, ApJ, 883, 81

(ref: Sun+23) Sun, J., Leroy, A. K., Ostriker, E. C., et al. 2023, ApJL, 945, L19

(ref: Tacchella+18) Tacchella, S., Carollo, C. M., Förster Schreiber, N. M., et al. 2018, ApJ, 859, 56

(ref: Tacchella+16b) Tacchella, S., Dekel, A., Carollo, C. M., et al. 2016, MNRAS, 458, 242

(ref: Tacchella+15) Tacchella, S., Lang, P., Carollo, C. M., et al. 2015, ApJ, 802, 101

(ref: Tacconi+18) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tacconi+20) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: Tacconi+13) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: Teague+18) Teague, R. & Foreman-Mackey, D. 2018, Research Notes of the American Astronomical Society, 2, 173

(ref: Valentino+18) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: Valentino+20) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24

(ref: Villanueva+21) Villanueva, V., Bolatto, A., Vogel, S., et al. 2021, ApJ, 923, 60

(ref: Villanueva+24) Villanueva, V., Bolatto, A. D., Vogel, S. N., et al. 2024, ApJ, 962, 88

(ref: Walter+20) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111

(ref: Walter+11) Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011, ApJ, 730, 18

(ref: Weiss+05) Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429, L25

(ref: Zolotov+15) Zolotov, A., Dekel, A., Mandelker, N., et al. 2015, MNRAS, 450, 2327

[^1]: <https://github.com/richteague/bettermoments>

</paper>

Write the methods card for this paper.