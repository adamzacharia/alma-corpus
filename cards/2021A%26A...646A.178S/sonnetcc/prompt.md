# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...646A.178S\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...646A.178S",
 "title": "Detection of H<SUB>2</SUB>O and OH<SUP>+</SUP> in z &gt; 3 hot dust-obscured galaxies",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Stanley, F.",
 "n_authors": 6,
 "arxiv_id": "2011.09991",
 "doi": "10.1051/0004-6361/202037888",
 "alma_projects_linked_by_archive": [
  "2017.1.00123.S"
 ]
}
```

Paper text:
<paper>
# Detection of H$_2$O and OH$^+$ in $z>3$ Hot Dust-Obscured Galaxies

In this paper we present the detection of H$_{2}$O and OH$^+$ emission in $z>3$ hot dust-obscured galaxies (Hot DOGs).

Using ALMA Band-6 observations of two Hot DOGs, we have detected H$_{2}$O($2_{02}-1_{11}$) in W0149$+$2350, and H$_{2}$O($3_{12}-3_{03}$) and the multiplet OH$^+$($1_{1}-0_{1}$) in W0410$-$0913. These detections were serendipitous, falling within the side-bands of Band-6 observations aimed to study CO(9$-$8) in these Hot DOGs.

We find that both sources have luminous H$_{2}$O emission with line luminosities of $L_{\rm H_2O(2_{02}-1_{11})} > 2.2\times10^8 L_\odot$ and $L_{\rm H_2O(3_{12}-3_{03})} = 8.7\times10^8 L_\odot$ for W0149$+$2350 and W0410$-$0913, respectively. The H$_{2}$O line profiles are similar to those seen for the neighbouring CO(9$-$8) line, with linewidths of FWHM $\sim 800-1000$ km s$^{-1}$. However, the H$_{2}$O emission seems to be more compact than the CO(9$-$8). OH$^+$($1_{1}-0_{1}$) is detected in emission for W0410$-$0913, with a FWHM$=1000$ km s$^{-1}$ and a line luminosity of $L_{\rm OH^+(1_{1}-0_{1})} = 6.92\times10^8 L_\odot$. The ratio of the observed H$_{2}$O line luminosity over the IR luminosity, for both Hot DOGs, is consistent with previously observed star forming galaxies and AGN. The H$_2$O/CO line ratio of both Hot DOGs and the OH$^+$/H$_2$O line ratio of W0410$-$0913 are comparable to those of luminous AGN found in the literature.

The bright H$_2$O($2_{02}-1_{11}$), and H$_2$O($3_{12}-3_{03}$) emission lines are likely due to the combined high star-formation levels and luminous AGN in these sources. The presence of OH$^+$ in emission, and the agreement of the observed line ratios of the Hot DOGs with luminous AGN in the literature, would suggest that the AGN emission is dominating the radiative output of these galaxies. However, follow-up multi-transition observations are needed to better constrain the properties of these systems.

# Introduction

Energetic feedback from active galactic nuclei (AGN) has the potential to heat and remove the cold molecular gas from the interstellar medium (ISM), consequently suppressing the star-formation of the host galaxy. The most successful models of galaxy formation and evolution require AGN feedback to explain many of the puzzling properties of local massive galaxies and the intergalactic medium (e.g., red colours, steep luminosity function, black-hole – spheroid relationship, metal enrichment of the intergalactic medium; see (cite: AlexanderHickox12), and (cite: Fabian12) for reviews). Understanding the properties of the molecular gas in the ISM of active galaxies is key to constraining and disentangling the effects of AGN and star formation.

Within the past few years the Wide-Infrared Survey Explorer (cite: Wright10) has led to the discovery of a population of luminous, dust-obscured AGN (cite: Eisenhardt12; Bridge13; Lonsdale15). Selected to be the reddest sources in the WISE colour-colour plot (\[3.4-4.6\] $\mu$m vs \[4.6-12\] $\mu$m), they are by definition highly obscured and dusty galaxies. They are commonly referred to as Hot Dust Obscured Galaxies (Hot DOGs). This new class of galaxies is a rare sample with only 1000 over the entire sky (cite: Eisenhardt12). They are mostly high-redshift objects, at $1<z<4$ (cite: Wu12; Tsai15), and extremely luminous with $L_{bol} > 10^{13}L_\odot$ (cite: Jones14; Wu14). Based on X-ray observations and spectral energy distribution (SED) studies, there is clear evidence that they host highly dust-obscured AGN (cite: Stern14; Piconcelli15; Assef15; Assef16; Fan16b).

Hot DOGs are found in predominantly over-dense regions (cite: Jones17), and the most luminous among them show evidence of a high merger fraction (cite: Fan16a). This supports a scenario where Hot DOGs could represent the post-merger transitional phase from a dusty starburst dominated phase to an optically bright quasar phase (cite: Eisenhardt12; Wu12; Fan16a). Their rarity could be a result of rare events such as major mergers, the relative briefness of the transitional phase they represent, and/or the population is tracing the tail end of the mass function.

In this paper we present the detection of H$_2$O, and OH$^+$ emission lines for the first time in Hot DOGs. In the past few years there have been a number of detections of H$_2$O transitions in the far-infrared (FIR) and sub-mm wavelengths with the advent of observatories such as *Herschel*, NOEMA, and ALMA. Studies of nearby galaxies have shown that H$_2$O is the third most abundant species in dense warm star-forming regions, and shock heated regions (cite: Cernicharo06; Bergin03; Gonzalez-Alfonso13). Detections of H$_2$O transitions in high-$z$ and lensed sub-mm galaxies confirm that they are among the strongest molecular lines in starburst galaxies and also show similar line profiles and spatial distribution as the high-$J$ CO emission (cite: Lis11; vanderWerf11; Bradford11; Combes12; Lupu12; Bothwell13; Omont13; Riechers13; Weiss13; Yang16; Oteo17; Yang19; Apostolovski19; Casey19; Jarugula19; Yang20). Furthermore, there is a correlation between the line luminosity and the IR luminosity, extending over three orders of magnitude (cite: Omont13; Yang13; Yang16). Modelling of H$_2$O emission in extragalactic sources has shown that the combination of different transitions can help disentangle the different components of the molecular ISM (cite: Gonzalez-Alfonso14; Liu17).

OH$^+$ is an important part of the chemical network for the formation of H$_2$O, and can trace the ionisation rate of atomic/molecular gas (cite: Neufeld10; Hollenbach12), as well as the turbulent gas component (cite: Gonzalez-Alfonso18). OH$^+$ is observed both in emission and absorption in both low and high-$z$ galaxies (cite: vanderWerf10; Spinoglio12; Kamenetzky12; Pereira-Santaella13; Riechers13; Gallerani14; vanderTak16; Li20). Interestingly, OH$^+$ is observed in emission for sources with a strong AGN component, (cite: vanderWerf10; Spinoglio12; Pereira-Santaella13; Li20), while starburst galaxies show OH$^+$ in absorption (cite: Kamenetzky12; Riechers13; vanderTak16).

The two Hot DOGs discussed in this paper, W0149+2350 and W0410-0913, were selected to be among the most starbursting Hot DOGs, with massive molecular gas reservoirs discovered in CO(4$-$3) (Fan et al. 2018). Both sources have exceptionally wide CO lines in multiple transitions, with FWHM$\approx 750-950$ km s$^{-1}$ (cite: Fan18) and large molecular gas masses of $10^{10} - 10^{11} M_\odot$.

In section 2 we present the ALMA observations and the extraction of the spectra. In section 3 we present our results for the two sources, and in section 4 we discuss the cause of excitation of the observed emission and compare it to the literature. Finally, in section 5 we give a summary and conclusions. Throughout this paper we assume a WMAP7 cosmology.

# ALMA observations and analysis

We obtained multi-band observations of W0149$+$2350 and W0410$-$0913 in project 2017.1.00123.S to study CO rotational transitions, and these data yielded three serendipitous detections of other molecular lines. Observations were carried out using the band-6 receivers, where one side-band was tuned to the redshifted CO(9-8) with the correlator used in frequency domain mode with each spectral window (spw) having a bandwidth of 1.875 GHz, the other sideband used a continuum setup. Observations of W0149$+$2350 were carried out on 24th of September 2018, with a total of 49 min of on-source integration time. The observed frequencies cover the ranges of 229.82–233.60 GHz, and 243.68–245.55 GHz, which include the redshifted H$_{2}$O($2_{02}-1_{11}$) transition in addition to the targeted CO(9-8). Observations of W0410$-$0913 were carried out on the 07th of September 2018, with a total of 6 min of on-source integration time. The observed frequencies cover the ranges of 221.08–224.81 GHz, and 236.28–240.57 GHz, which include the H$_{2}$O($3_{12}-3_{03}$) transition, and the OH$^+$($1_1-0_1$) multiplet in addition to the targeted CO(9-8). Flux and bandpass calibration was done using J0006$-$0623 and J0423$-$0120, and gain calibration was done with J0152+2207 and J0407$-$1211, for W0149$+$2350 and W0410$-$0913, respectively. Beam sizes correspond to $0.53\hbox{$^{\prime\prime}$}\times0.32\hbox{$^{\prime\prime}$}$, and $0.67\hbox{$^{\prime\prime}$}\times0.52\hbox{$^{\prime\prime}$}$, for W0149$+$2350 and W0410$-$0913 respectively.

Reduction, calibration, and imaging was done using CASA (Common Astronomy Software Application[^2]; (cite: McMullin07)). The pipeline reduced data delivered from the observatory were of sufficient quality, no or little additional flagging and further calibration was necessary. The steps required for standard reduction and calibration included in the pipeline include flagging, bandpass calibration, as well as flux and gain calibration. For our imaging process we applied natural weighting. A conservative estimate of the error on the absolute flux calibration is $10\%$. Continuum emission was subtracted using the line-free channels identified in both sidebands for each source. For both sources, the channel width was set to 60 km s$^{-1}$.

To extract the spectrum we used the following procedure. We created the moment-0 map of each emission line, and used the imfit tool of casa to get an estimate of the extent of the emission. We then extracted the spectrum from a region that is equivalent to two times the size estimate of the source.

In this paper we also show the CO(9$-$8) emission for comparison. This data has been extracted and analysed in the same way as the H$_{2}$O and OH$^+$ emission that are the focus of this paper. However, the CO(9$-$8) data will be presented in more detail in Knudsen et al. (in prep) along with other CO transitions.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | RA | DEC | $z_{\rm CO(4-3)}$ | $L'_{\rm CO(4-3)}$ | $L_{\rm IR,AGN}$ | $L_{\rm IR,SF}$ |  |  |  |
|  | \[J2000\] | \[J2000\] |  | \[K km s$^{-1}$ pc$^2$\] | \[$L_\odot$\] | \[$L_\odot$\] |  |  |  |
| W0149$+$2350 | 01:49:46.16 | $+$23:50:14.6 | 3.237 | $2.4 \times 10^{10}$ | $7.6\times10^{13}$ | $1.14\times10^{13}$ |  |  |  |
| W0410$-$0913 | 04:10:10.60 | $-$09:13:05.2 | 3.631 | $1.8 \times 10^{11}$ | $1.5 \times 10^{14}$ | $4.7\times10^{13}$ |  |  |  |

# Results

|                                  |                  |                  |
|:---------------------------------|:----------------:|:----------------:|
| Line                             | $\nu_{\rm rest}$ | RMS$_{\rm spec}$ |
|                                  |     \[GHz\]      |     \[mJy\]      |
| H$_2$O($2_{02}-1_{11}$)          |     987.937      |       0.28       |
| H$_2$O($3_{12}-3_{03}$)          |     1097.365     |       0.30       |
| OH$^+$($1_{1}-0_{1}$) multiplet: |                  |       0.57       |
| OH$^+$($1_{11}-0_{11}$)          |     1032.998     |                  |
| OH$^+$($1_{12}-0_{11}$)          |     1033.004     |                  |
| OH$^+$($1_{11}-0_{12}$)          |     1033.113     |                  |
| OH$^+$($1_{12}-0_{12}$)          |     1033.118     |                  |

: Identified lines based on the CDMScatalogue entries, and corresponding RMS of their spectrum (RMS$_{\rm spec}$).

## H$_2$O(2$_{02}$–1$_{11}$) in W0149$+$2350

For W0149$+$2350 we have detected H$_2$O emission in the transition of H$_2$O(2$_{02}$–1$_{11}$), see Fig. [1](#fig:specfit_w0149) (in yellow). Although the line is truncated, it covers $\rm \sim1000\,km\,s^{-1}$ with a line profile that cannot be described by a single Gaussian. This type of line profile is also seen in their CO(9-8) line emission, see Fig. [1](#fig:specfit_w0149) (in grey; Knudsen et al. in prep).

In Fig. [1](#fig:specfit_w0149) we show the line, with the fit of a single Gaussian, and a double Gaussian. A double Gaussian fit to the line improves the $\chi^2$ by 22% compared to the single Gaussian fit. In Table [\[tab:results\]](#tab:results) we give the fit results for the two component fit to the line. However, as the line is truncated, we integrate the measured flux of the line, to calculate a lower limit of the total integrated line flux (see Table [\[tab:results\]](#tab:results)).

In Fig. [2](#fig:hst_w0149) we show the HST map from (cite: Fan16a), with the moment-0 map contours of the H$_2$O emission in blue, and the CO contours in yellow for comparison. To estimate the extent of the emission observed, we use the imfit tool of casa, to fit to the moment-0 maps of each line. However, as the H$_2$O line is truncated, to have a meaningful comparison of the extent of the emission we create moment-0 maps limited to the velocity range of $-300 < \upsilon < 750$ km s$^{-1}$, for both the H$_2$O and CO emission. We find that the H$_2$O emission of W0149$+$2350 extends across $2.3\pm0.6$ kpc, while the CO(9$-$8) emission extends across $3.3\pm0.5$ kpc (see Table [\[tab:size\]](#tab:size)).

![](w0149_spec_h2o_wfit_nCO_resub.pdf)

![image](W0149+2350_HST_waterCOcontours_plneg.png)\

|  |  |  |  |  |  |  |  |  |  |
|:---|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | line | $\upsilon_{\rm cen}$ | $S_{\rm peak}$ | FWHM | $S_{\rm int}$ | $L_{\rm line}$ |  |  |  |
|  |  | \[km s$^{-1}$\] | \[mJy\] | \[km s$^{-1}$\] | \[Jy km s$^{-1}$\] | \[$\times10^{8}L_\odot$\] |  |  |  |
| W0149$+$2350 | H$_2$O($2_{02}-1_{11}$) |  |  |  |  |  |  |  |  |
|  | comp1 | $-219\pm103$ | $1.3\pm0.2$ | $564\pm413$ | $0.80\pm0.60$ | $1.58\pm1.17$ |  |  |  |
|  | comp2 | $396\pm58$ | $1.4\pm0.2$ | $421\pm99$ | $0.63\pm0.18$ | $1.24\pm0.36$ |  |  |  |
|  | **total** |  |  |  | $>$1.12 | $>2.2$ |  |  |  |
| W0410$-$0913 | H$_2$O($3_{12}-3_{03}$) |  |  |  |  |  |  |  |  |
|  | comp1 | $-307\pm44$ | $1.2\pm0.7$ | $256\pm167$ | $0.31 \pm 0.29$ | $0.83\pm0.76$ |  |  |  |
|  | comp2 | $99\pm54$ | $3.8\pm0.2$ | $737\pm103$ | $2.99\pm0.46$ | $7.90\pm1.23$ |  |  |  |
|  | **total** |  |  |  | $3.30\pm0.54$ | $8.73\pm 1.44$ |  |  |  |
|  | OH$^+$($1_{1}-0_{1}$) | $-100\pm83$ | $2.6\pm0.3$ | $1000\pm196$ | $2.78\pm0.62$ | $6.92\pm1.55$ |  |  |  |

## H$_2$O(3$_{12}$–3$_{03}$) and OH$^+$($1_1-0_1$) in W0410$-$0913

For W0410$-$0913 we have detected the H$_2$O($3_{12} - 3_{03}$), and the OH$^+$($1_1-0_1$) multiplet with transitions at 1032.998–1033.118 GHz (see Table [1](#tab:lines), although unresolved). Similar to what is seen for W0149$+$2350, the H$_2$O($3_{12} - 3_{03}$) line also shows a very wide profile, that is similar to that of the CO(9$-$8).

In Fig. [3](#fig:specfit_w0410) we show the H$_2$O($3_{12} - 3_{03}$) line, with the fit of a single Gaussian, and a double Gaussian. A double Gaussian fit to the line improves the $\chi^2$ by 12% compared to the single Gaussian fit. In Table [\[tab:results\]](#tab:results) we give the results for the two component fit to the line.

Due to their large linewidths the CO(9$-$8) and OH$^+$ lines are partially blended. We perform a simultaneous fit of the CO(9$-$8) and OH$^+$ emission. We do this by using a double Gaussian fit for the CO(9$-$8), and a single Gaussian for the OH$^+$ emission. We allow all three parameters of the Gaussians to vary during the fit, restricting the central velocity ($\upsilon_{\rm cen}$) of each component of the CO line within a range of 400 km s$^{-1}$, and for the OH$^+$ line within 200 km s$^{-1}$ of the expected $\upsilon_{\rm cen}$. In Fig. [5](#fig:specfitoh_w0410) we show the double Gaussian fit to the CO(9$-$8) line (blue dotted curve), and the resulting fit to the OH$^+$ emission (blue dashed curve). In Table [\[tab:results\]](#tab:results) we give line properties based on the fit. In this case the integrated line flux ($S_{\rm int}$) is based on the fit. We note that in our analysis we have assumed that the OH$^+$ is in emission based on the observed spectrum; however, it is possible that it has a different line profile, such as a P-Cygni profile, that is not visible due to the blending with the CO(9$-$8) line. In some starburst galaxies OH$^+$ has been found to have a P-Cygni line profile. An example is NGC253, for which it is concluded that the OH$^+$ is primarily arising in cold diffuse foreground gas (cite: vanderTak16). If indeed the OH$^+$ multiplet observed here had a P-Cygni profile, it would require a strongly asymmetric line profile for the CO(9-8) in order to compensate for the superimposed absorption feature of the OH$^+$. This would require luminous CO(9$-$8) emission at $\sim$1000 km s$^{-1}$ from the line centre. Such a peculiar line profile is unlikely, and is not seen for the lower$-J$ CO (cite: Fan18) and H$_2$O transitions. It could also be possible for the emission identified as OH$^+$ to be alternatively interpreted as a massive and highly excited molecular outflow. However, such a scenario would require a combination of orientation and foreground absorption that would allow us to see the red component of the outflow while not seeing emission from the blue component. Furthermore, there is no evidence for such a massive outflow in the lower$-J$ CO transitions (cite: Fan18).

In Fig. [4](#fig:hst_w0410) we show the HST map from (cite: Fan16a), with the moment-0 map contours of the H$_2$O emission in blue, the OH$^+$ emission in white, and the CO contours in yellow for comparison. The OH$^+$ emission follows closely the extent seen in the CO(9$-$8), that shows an extended non-uniform structure, but the H$_2$O emission is more compact. We estimate the extent of the emission observed using the imfit tool of casa. Following the analysis of W0149$+$2350, we create moment-0 maps limited to the velocity range of $-500 < \upsilon < 500$ km s$^{-1}$, for the H$_2$O, CO, and OH$^+$ emission, to match to the velocity range covered by the H$_2$O line. The OH$^+$ is extended across $9.3\pm2.1$ kpc, similar to the CO($9-8$) emission extending over $5.7\pm0.6$ kpc, while the H$_2$O is more compact covering $3.0\pm0.6$ kpc. The extent of the CO(9$-$8) and OH$^+$ emission is significantly larger than the H$_2$O; however, deeper and higher resolution observations are needed to better constrain these properties and to further interpret these results.

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Source | line | size | PA |
|  |  | \[arcsec$^2$\] | \[deg\] |
| W0149$+$2350: | H$_2$O($2_{02}-1_{11}$) | $(0.30\pm0.08)\times(0.22\pm0.08)$ | $43\pm89$ |
|  | CO(9$-$8) | $(0.43\pm0.07)\times(0.31\pm0.06)$ | $4\pm26$ |
| W0410$-$0913: | H$_2$O($3_{12}-3_{03}$) | $(0.41\pm0.08)\times(0.33\pm0.09)$ | $126\pm86$ |
|  | OH$^+$($1_{1}-0_{1}$) | $(1.3\pm0.3)\times(0.8\pm0.2)$ | $107\pm30$ |
|  | CO(9$-$8) | $(0.77\pm0.08)\times(0.43\pm0.05)$ | $108\pm8$ |

![](w0410_spec_h2o_wfit_nCO_resub.pdf)

![image](W0410-0913_HST_waterCOcontours_plneg.png)\

![](w0410_spec_OHp_wsimfit_resub.pdf)

For both sources we find that the high-density gas traced by H$_2$O extends over a few kpc scales. Based on the total gas masses estimated by (cite: Fan18), and if we assume a spherical geometry[^3] with radii of 1-2 kpc and a volume filling factor of 0.01-0.1%, then the estimated gas density is of the range of $n(H_2)\sim10^5-10^6$ cm$^{-3}$. This is in agreement with what is required for the excitation of the observed H$_2$O emission. Therefore, the extent of the observed emission is consistent with the gas mass estimated for these galaxies.

# Discussion

## Excitation of the H$_2$O and OH$^+$ emission

In a detailed study of H$_2$O submillimetre lines in the nuclei of nearby star-forming galaxies, (cite: Liu17) used modelling to determine the physical conditions and excitation mechanisms needed for the H$_2$O transitions of low, medium, and high energy transition. (cite: Liu17) examined three components of the molecular ISM: a cold component with densities of $n(H_2)\sim10^4-10^6$ cm$^{-3}$, dust temperatures of $T_d\sim20-30$ K, and column densities of $N(H_2)\sim10^{23}$ cm$^{-2}$; a warm component with $n(H_2)\sim10^5-10^6$ cm$^{-3}$, $T_d\sim40-70$ K, and $N(H_2)\sim1-4\times10^{24}$ cm$^{-2}$; and a hot component with $n(H_2)\geq 10^6$ cm$^{-3}$, $T_d\sim100-200$ K, $N(H_2)\geq 5\times10^{24}$ cm$^{-2}$. Interestingly, the H$_2$O($2_{02}-1_{11}$) transition can trace both the warm and hot components, but the H$_2$O($3_{12} - 3_{03}$) transition is stronger in the warm component of the ISM, and is not strongly produced in hot ISM conditions. Based on the radiative-transfer analysis of (cite: Liu17) the H$_2$O($2_{02}-1_{11}$) and H$_2$O($3_{12} - 3_{03}$) transitions can be produced by collisional excitation alone, while higher energy transitions characteristic of the hot ISM component require IR pumping to reach the observed intensities. However, (cite: Gonzalez-Alfonso14), that also modelled the H$_2$O submillimetre lines for IR galaxies, argue that IR pumping has a significant role in producing the H$_2$O($2_{02}-1_{11}$) and H$_2$O($3_{12} - 3_{03}$) line emission. In both cases, higher energy transitions are more likely to exclusively trace the hot component of the ISM surrounding AGN. Indeed, there was recently a detection of H$_2$O($4_{14}-3_{21}$) from the circumnuclear disk of a lensed quasar (cite: Stacey20).

As we only have a single H$_2$O line detection for each source, it is not possible to make an extensive analysis. But we take a simplistic modelling approach using the non-LTE molecular radiative transfer code radex (cite: vanderTak07), to provide some constraints on the possible excitation of the observed H$_2$O emission.

We use the peak fluxes for each of the observed H$_2$O lines and the corresponding CO($9-8$) line, for each source. We assume a spherical symmetry, and CO column densities in the range of $10^{16}-10^{17}$ cm$^{-2}$ to avoid optically thin emission at the low end and too high opacities at the high end. Based on the SED fit and decomposition of these sources (cite: Tsai15; Fan16b), we expect an AGN torus dust temperature of 450 K, and a dust temperature due to star-formation of 51 K and 63 K.

For W0149$+$2350 we find that the H$_2$O($2_{02}-1_{11}$) transition, at 987.94 GHz (E$_{\rm L}=$53 K), may be collisionally excited. For intermediate densities ($\leq 10^6$ cm$^{-3}$) relatively high H$_2$O($2_{02}-1_{11}$) abundances ($>10^{-6}$) are required. At higher densities ($> 10^6$ cm$^{-3}$), lower abundances of $10^{-7}-10^{-8}$ are possible. For W0410$-$0913 we find that the H$_2$O($3_{12}-3_{03}$) transition, at 1097.36 GHz (E$_{\rm L}=$196 K), may be collisionally excited, but that would require densities $> 10^6$ cm$^{-3}$. Even for these high densities, the H$_2$O($3_{12}-3_{03}$) abundance is rather high ($10^{-5}-10^{-6}$). However, for both sources, having such high densities filling the region corresponding to the beam at these distances (i.e. $\sim$4–5 kpc) is unlikely. This can either be solved with a small filling factor of dense clumps and/or the emission emerging from a dense nuclear structure (e.g. the AGN torus). Alternatively, all or parts of the H$_2$O emission are being influenced by IR pumping, which would allow it to arise also in lower density gas. This is in agreement with what is argued by (cite: Gonzalez-Alfonso14).

Based on the results of our simplistic RADEX modelling and what has been found by (cite: Gonzalez-Alfonso14) and (cite: Liu17), we expect that the transitions that we have detected are due to the high levels of star-formation in our sources, with a possibly significant contribution from the AGN (through IR pumping).

So far in the literature, sources where the OH$^+$ line is in emission have been galaxies with significant AGN contributions such as Mrk231 (cite: vanderWerf10), NGC1068 (cite: Spinoglio12), and NGC7130 (cite: Pereira-Santaella13). Therefore, the detection of OH$^+$ in emission for W0410$-$0913, could be indicative of excitation from cosmic rays and X-rays from the AGN (cite: vanderWerf10; Spinoglio12; Pereira-Santaella13; Li20). The relative line intensities between the CO($9-8$), the OH$^+$($1_1-0_1$) multiplet, and the H$_2$O($3_{12}-3_{03}$) observed for W0410$-$0913 are consistent with those of Mrk231 (cite: vanderWerf10), for which it was shown that the combination of strong high$-J$ CO, and OH$^+$ emission indicate X-ray driven excitation from the AGN of Mrk231. However, due to the limitations of our data, and the lack of other H$_n$O$^+$ transitions, we cannot confirm that the OH$^+$ emission is due to the AGN through radiative transfer modelling.

## The H$_2$O–IR luminosity ratio of Hot DOGs

The relationship between the H$_2$O line luminosity with IR luminosity (from 8 to 1000 $\mu m$; $L_{\rm IR}$), and the ratio of the two, has been well studied for low and high-$z$ dusty star-forming galaxies (cite: Yang13; Yang16; Jarugula19). Here we compare the two detected Hot-DOGs of this paper to low and high-$z$ ultra-luminous IR galaxies (ULIRGs), sub-millimetre galaxies (SMGs) and AGN in the literature. We only compare to sources with the same H$_2$O transition available, as each of the sources.

As our sources have both a strong AGN and star formation contribution to the total $L_{\rm IR}$, it is important to consider how we compare the H$_2$O line luminosity and the IR luminosity. For example, if the observed H$_2$O emission is primarily tracing the star formation in our source, then we should take the ratio with the IR luminosity due to star formation ($L_{\rm IR, SF}$); however, if the emission is tracing both AGN and star formation regions then the total IR luminosity should be considered ($L_{\rm IR, tot}$). It is not possible in our analysis to confidently distinguish if the H$_2$O emission is only due to the star-formation of the source, as excitation from the AGN could also be contributing significantly. For this reason we examine both of the possible scenarios when comparing to the literature.

In Fig. [6](#fig:lir_lh2o)*(top)* we show the ratio of the line luminosity for the $\rm H_2O(2_{02}-1_{11})$ transition over $L_{\rm IR}$ ($L_{\rm H_2O(2_{02}-1_{11})}$/$L_{\rm IR}$) as a function of $L_{\rm IR}$. Here we plot two values for W0149$+$2350, $L_{\rm H_2O(2_{02}-1_{11})}$/$L_{\rm IR, tot} > 0.25\times10^{-5}$ (solid star) and $L_{\rm H_2O(2_{02}-1_{11})}$/$L_{\rm IR,SF} > 2\times10^{-5}$ (hollow star), in comparison to both strong AGN and ULIRGs/SMGs that have been detected in the same transition. As we only have a lower limit for W0149$+$2350 the $L_{\rm H_2O(2_{02}-1_{11})}$/$L_{\rm IR, tot}$ ratio, although low, is consistent with both AGN and ULIRGs/SMGs at low and high-$z$. However, the lower limit for $L_{\rm H_2O(2_{02}-1_{11})}$/$L_{\rm IR, SF}$, is only consistent with luminous high-$z$ ULIRGs/SMGs, as can be expected if the source of the H$_2$O emission are the star formation regions.

In Fig. [6](#fig:lir_lh2o)*(bottom)* we show the ratio for the $\rm H_2O(3_{12}-3_{03})$ transition ($L_{\rm H_2O(3_{12}-3_{03})}$/$L_{\rm IR}$) as a function of $L_{\rm IR}$. Again, we plot two values corresponding to W0410$-$0913, $L_{\rm H_2O(3_{12}-3_{03})}$/$L_{\rm IR,tot} = 0.44\times10^{-5}$ (solid star) and $L_{\rm H_2O(3_{12}-3_{03})}$/$L_{\rm IR,SF} = 1.86\times10^{-5}$ (hollow star). In this case the $L_{\rm H_2O(3_{12}-3_{03})}$/$L_{\rm IR,tot}$ ratio of W0410$-$0913 is consistent with low-$z$ AGN and ULIRGs, but is significantly below what is seen for high-$z$ ULIRGs/SMGs, while the $L_{\rm H_2O(3_{12}-3_{03})}$/$L_{\rm IR,SF}$ ratio is consistent with the high-$z$ ULIRGs/SMGs.

![image](W0149_Lh2o_Lir_litcomp.pdf) ![image](W0410_Lh2o_Lir_litcomp.pdf)

## The H$_2$O and OH$^+$ line ratios of Hot DOGs

In this section we compare the observed H$_2$O and OH$^+$ line ratios of our sources to the ratios in other galaxies found in the literature.

We find that for W0149$+$2350 the $H_2O(2_{02}-1_{11})$/CO(9$-$8) ratio is $>0.5$. This is in agreement with what is seen in the literature for high–$z$ ULIRGs/SMGs and AGN (cite: Apostolovski19; Bradford09; Jarugula19; Li20; Oteo17; Riechers13; vanderWerf11; Weiss07). However, the ratio of $H_2O(2_{02}-1_{11})$/CO(4$-$3) is $>1.4$, which is significantly higher than what has been observed for high–$z$ ULIRGs/SMGs (cite: Bradford09; Jarugula19; Omont13; Yang16; Yang17), although consistent with the luminous AGN APM08279$+$5255 that has a $H_2O(2_{02}-1_{11})$/CO(4$-$3) of 2.4 (cite: vanderWerf11; Weiss07).

For W0410$-$0913 we calculate line ratios of $\rm H_2O(3_{12}-3_{03})/CO(9-8) = 0.8\pm0.2$, $\rm H_2O(3_{12}-3_{03})/CO(4-3) = 0.6\pm0.1$, and $\rm OH^+(1_{1}-0_{1})/H_2O(3_{12}-3_{03}) = 0.8\pm0.2$. In this case the available similar measurements in the literature are limited. However, the $\rm H_2O(3_{12}-3_{03})/CO(9-8)$ ratio of W0410$-$0913 is consistent if somewhat higher than high–$z$ ULIRGs/SMGs (cite: Oteo17; Riechers13). The $\rm OH^+(1_{1}-0_{1})/H_2O(3_{12}-3_{03})$ ratio is consistent with low–$z$ luminous AGN (cite: vanderWerf10; Liu17; Spinoglio12).

The nearby ULIRG Mrk231 is particularly interesting to compare to as it has a luminous AGN that contributes 70% of the IR luminosity, similar to what is found for our Hot DOGs with 87% and 77% in W0149$+$2350 and W0410$-$0913, respectively (cite: Fan16b). Mrk231 has $\rm H_2O(2_{02}-1_{11})$/CO(4$-$3) and $\rm H_2O(3_{12}-3_{03})/CO(4-3)$ line ratios of 0.4 (cite: vanderWerf10; Papadopoulos07), and an $\rm OH^+(1_{1}-0_{1})/H_2O(3_{12}-3_{03})$ ratio of 0.65 (cite: vanderWerf10; Liu17). Overall, W0410$-$0913 seems most consistent with what is seen for Mrk231, while for W0149$+$2350 the $\rm H_2O(2_{02}-1_{11})$/CO(4$-$3) ratio is significantly larger than for Mrk231. Interestingly, W0149$+$2350 also has a significantly larger AGN contribution to the IR luminosity than W0410$-$0913 and Mrk231.

# Summary and Conclusions

In this paper we have presented the recent detection of H$_2$O and OH$^+$ in $z>3$ Hot DOGs. This is the first detection of these emission lines for this class of galaxies, and one of the few in high-$z$ non-lensed galaxies (cite: Casey19). Specifically, we have detected the $\rm H_2O(2_{02}-1_{11})$ transition from W0149$+$2350, and the $\rm H_2O(3_{12}-3_{03})$, and the OH$^+$($1_{1}-0_{1}$) multiplet from W0410$-$0913. These were serendipitous detections in an observation program targeting the CO(9$-$8) emission of these sources (Knudsen et al. in prep).

Similar to what has been found for previously observed high-$z$ ULIRGs and SMGs, the line profile of the H$_2$O emission lines follows that of the high-$J$ CO(9$-$8) emission. But the extent of the H$_2$O emission seems to be more compact than that of CO(9$-$8), and in the case of W0410$-$0913 it is more compact than the OH$^+$($1_{1}-0_{1}$) emission too. However, deeper and higher resolution observations are needed to better constrain the emission properties and to further interpret these results.

A single H$_2$O line detection does not allow for the disentangling of the ISM components and determining the molecular gas properties. However, the luminous H$_2$O emission in these two Hot DOGs indicate the existence of warm dense molecular gas conditions ($n(H_2)\sim10^5-10^6$ cm$^{-3}$, $T_d\sim40-70$ K), possibly dominated by collisional excitation, with likely contribution from IR pumping from the AGN. We cannot confidently distinguish between excitation due to the AGN or star-formation or both for the H$_2$O emission. However, the detection of OH$^+$($1_{1}-0_{1}$) in emission for W0410$-$0913, and the agreement of the observed line ratios with luminous AGN in the literature indicate that the energy output from the AGN is dominating the radiative output of this galaxy, even though there is significant ongoing star formation (1000–5000 M$_\odot$ yr$^{-1}$). This is consistent with the fact that these galaxies host AGN that dominate the IR luminosity, contributing $\gtrsim70\%$ (cite: Fan16b). This would also be consistent with the scenario that Hot DOGs are going through a transitional phase from a starburst–dominated to an AGN–dominated phase (cite: Eisenhardt12; Wu12; Fan16a).

In order to break the degeneracies and disentangle the relative contributions from the AGN and the star formation, a multi-transitional approach is required. Based on the results of modelling studies (cite: Gonzalez-Alfonso14; Liu17), it is possible to design observational programs targeting a combination of H$_2$O transitions that trace different components of the molecular gas. Transitions such as $\rm H_2O(2_{02}-1_{11})$ and $\rm H_2O(3_{12}-3_{03})$, with energies of $E_{up} < 250-350$ K, can be produced by collisional excitation alone or a combination of collisional excitation and IR pumping. However, higher energy transitions, such as H$_2$O($4_{14}-3_{21}$) or $\rm H_2O(4_{22}-4_{13})$, require IR pumping and are therefore more likely to directly trace excitation from the AGN. A combination of H$_2$O transitions from low, medium, and high energy levels, could be a useful tool for disentangling the AGN and star formation contributions to the excitation of the dense molecular gas. Furthermore, targeting additional H$_n$O$^+$ transitions, such as H$_2$O$^+$ and H$_3$O$^+$ in combination with OH$^+$, would allow for constraints on the chemistry and excitation of the diffuse gas of these galaxies, possibly directly connected to the AGN (cite: Gonzalez-Alfonso13; Gonzalez-Alfonso18).

# Acknowledgements

We thank the anonymous referee for constructive comments. We thank the staff of the Nordic ALMA Regional Center node for their support and helpful discussions. We thank Dr Hannah Calcutt and Dr Pierre Cox for helpful discussions. KK acknowledges support from the Knut and Alice Wallenberg Foundation. SA acknowledges support from the European Research Council (ERC) and the Swedish Research Council. LF acknowledges the support from the National Natural Science Foundation of China (NSFC Nos. 11822303, 11773020 and 11421303) and Shandong Provincial Natural Science Foundation (JQ201801). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00123.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

59 natexlab

(ref: AlexanderHickox12) Alexander, D. M. & Hickox, R. C. 2012, New A Rev., 56, 93

(ref: Apostolovski19) Apostolovski, Y., Aravena, M., Anguita, T., et al. 2019, A&A, 628, A23

(ref: Assef15) Assef, R. J., Eisenhardt, P. R. M., Stern, D., et al. 2015, ApJ, 804, 27

(ref: Assef16) Assef, R. J., Walton, D. J., Brightman, M., et al. 2016, ApJ, 819, 111

(ref: Bergin03) Bergin, E. A., Kaufman, M. J., Melnick, G. J., Snell, R. L., & Howe, J. E. 2003, ApJ, 582, 830

(ref: Bothwell13) Bothwell, M. S., Aguirre, J. E., Chapman, S. C., et al. 2013, ApJ, 779, 67

(ref: Bradford09) Bradford, C. M., Aguirre, J. E., Aikin, R., et al. 2009, ApJ, 705, 112

(ref: Bradford11) Bradford, C. M., Bolatto, A. D., Maloney, P. R., et al. 2011, ApJL, 741, L37

(ref: Bridge13) Bridge, C. R., Blain, A., Borys, C. J. K., et al. 2013, ApJ, 769, 91

(ref: Casey19) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55

(ref: Cernicharo06) Cernicharo, J., Goicoechea, J. R., Daniel, F., et al. 2006, ApJL, 649, L33

(ref: Combes12) Combes, F., Rex, M., Rawle, T. D., et al. 2012, A&A, 538, L4

(ref: Eisenhardt12) Eisenhardt, P. R. M., Wu, J., Tsai, C.-W., et al. 2012, ApJ, 755, 173

(ref: Fabian12) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: Falstad17) Falstad, N., González-Alfonso, E., Aalto, S., & Fischer, J. 2017, A&A, 597, A105

(ref: Falstad15) Falstad, N., González-Alfonso, E., Aalto, S., et al. 2015, A&A, 580, A52

(ref: Fan16a) Fan, L., Han, Y., Fang, G., et al. 2016a, ApJL, 822, L32

(ref: Fan16b) Fan, L., Han, Y., Nikutta, R., Drouart, G., & Knudsen, K. K. 2016b, ApJ, 823, 107

(ref: Fan18) Fan, L., Knudsen, K. K., Fogasy, J., & Drouart, G. 2018, ApJL, 856, L5

(ref: Gallerani14) Gallerani, S., Ferrara, A., Neri, R., & Maiolino, R. 2014, MNRAS, 445, 2848

(ref: Gonzalez-Alfonso14) González-Alfonso, E., Fischer, J., Aalto, S., & Falstad, N. 2014, A&A, 567, A91

(ref: Gonzalez-Alfonso18) González-Alfonso, E., Fischer, J., Bruderer, S., et al. 2018, ApJ, 857, 66

(ref: Gonzalez-Alfonso13) González-Alfonso, E., Fischer, J., Bruderer, S., et al. 2013, A&A, 550, A25

(ref: Hollenbach12) Hollenbach, D., Kaufman, M. J., Neufeld, D., Wolfire, M., & Goicoechea, J. R. 2012, ApJ, 754, 105

(ref: Jarugula19) Jarugula, S., Vieira, J. D., Spilker, J. S., et al. 2019, ApJ, 880, 92

(ref: Jones17) Jones, S. F., Blain, A. W., Assef, R. J., et al. 2017, MNRAS, 469, 4565

(ref: Jones14) Jones, S. F., Blain, A. W., Stern, D., et al. 2014, MNRAS, 443, 146

(ref: Kamenetzky12) Kamenetzky, J., Glenn, J., Rangwala, N., et al. 2012, ApJ, 753, 70

(ref: Li20) Li, J., Wang, R., Riechers, D., et al. 2020, ApJ, 889, 162

(ref: Lis11) Lis, D. C., Neufeld, D. A., Phillips, T. G., Gerin, M., & Neri, R. 2011, ApJL, 738, L6

(ref: Liu17) Liu, L., Weiß, A., Perez-Beaupuits, J. P., et al. 2017, ApJ, 846, 5

(ref: Lonsdale15) Lonsdale, C. J., Lacy, M., Kimball, A. E., et al. 2015, ApJ, 813, 45

(ref: Lupu12) Lupu, R. E., Scott, K. S., Aguirre, J. E., et al. 2012, ApJ, 757, 135

(ref: McMullin07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Neufeld10) Neufeld, D. A., Goicoechea, J. R., Sonnentrucker, P., et al. 2010, A&A, 521, L10

(ref: Omont13) Omont, A., Yang, C., Cox, P., et al. 2013, A&A, 551, A115

(ref: Oteo17) Oteo, I., Zwaan, M. A., Ivison, R. J., Smail, I., & Biggs, A. D. 2017, ApJ, 837, 182

(ref: Papadopoulos07) Papadopoulos, P. P., Isaak, K. G., & van der Werf, P. P. 2007, ApJ, 668, 815

(ref: Pereira-Santaella13) Pereira-Santaella, M., Spinoglio, L., Busquet, G., et al. 2013, ApJ, 768, 55

(ref: Piconcelli15) Piconcelli, E., Vignali, C., Bianchi, S., et al. 2015, A&A, 574, L9

(ref: Riechers13) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: Spinoglio12) Spinoglio, L., Pereira-Santaella, M., Busquet, G., et al. 2012, ApJ, 758, 108

(ref: Stacey20) Stacey, H. R., Lafontaine, A., & McKean, J. P. 2020, MNRAS, 493, 5290

(ref: Stern14) Stern, D., Lansbury, G. B., Assef, R. J., et al. 2014, ApJ, 794, 102

(ref: Tsai15) Tsai, C.-W., Eisenhardt, P. R. M., Wu, J., et al. 2015, ApJ, 805, 90

(ref: vanderTak07) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vanderTak16) van der Tak, F. F. S., Weiß, A., Liu, L., & Güsten, R. 2016, A&A, 593, A43

(ref: vanderWerf11) van der Werf, P. P., Berciano Alba, A., Spaans, M., et al. 2011, ApJL, 741, L38

(ref: vanderWerf10) van der Werf, P. P., Isaak, K. G., Meijerink, R., et al. 2010, A&A, 518, L42

(ref: Weiss13) Weiß, A., De Breuck, C., Marrone, D. P., et al. 2013, ApJ, 767, 88

(ref: Weiss07) Weiß, A., Downes, D., Neri, R., et al. 2007, A&A, 467, 955

(ref: Wright10) Wright, E. L., Eisenhardt, P. R. M., Mainzer, A. K., et al. 2010, AJ, 140, 1868

(ref: Wu14) Wu, J., Bussmann, R. S., Tsai, C.-W., et al. 2014, ApJ, 793, 8

(ref: Wu12) Wu, J., Tsai, C.-W., Sayers, J., et al. 2012, ApJ, 756, 96

(ref: Yang13) Yang, C., Gao, Y., Omont, A., et al. 2013, ApJL, 771, L24

(ref: Yang19) Yang, C., Gavazzi, R., Beelen, A., et al. 2019, A&A, 624, A138

(ref: Yang20) Yang, C., González-Alfonso, E., Omont, A., et al. 2020, A&A, 634, L3

(ref: Yang17) Yang, C., Omont, A., Beelen, A., et al. 2017, A&A, 608, A144

(ref: Yang16) Yang, C., Omont, A., Beelen, A., et al. 2016, A&A, 595, A80

[^1]: flora.stanley@chalmers.se

[^2]: https://casa.nrao.edu

[^3]: We note that if we instead assume a cylindrical geometry with a radius based on the estimated sizes from Table [\[tab:size\]](#tab:size) and a height of 0.5 kpc, our results remain the same.

</paper>

Write the methods card for this paper.