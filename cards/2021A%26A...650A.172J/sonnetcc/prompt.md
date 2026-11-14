# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...650A.172J\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...650A.172J",
 "title": "ALMA observations of doubly deuterated water: inheritance of water from the prestellar environment",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Jensen, S. S.",
 "n_authors": 8,
 "arxiv_id": "2104.13411",
 "doi": "10.1051/0004-6361/202140560",
 "alma_projects_linked_by_archive": [
  "2017.1.00693.S",
  "2019.1.00720.S"
 ]
}
```

Paper text:
<paper>
# ALMA observations of doubly deuterated water: Inheritance of water from the prestellar environment

Establishing the origin of the water D/H ratio in the Solar System is central to our understanding of the chemical trail of water during the star and planet formation process. Recent modeling suggests that comparisons of the D$_2$O/HDO and HDO/H$_2$O ratios are a powerful way to trace the chemical evolution of water and, in particular, determine whether the D/H ratio is inherited from the molecular cloud or established locally.

We seek to determine the D$_2$O column density and derive the D$_2$O/HDO ratios in the warm region toward the low-mass Class 0 sources B335 and L483. The results are compared with astrochemical models and previous observations to determine their implications for the chemical evolution of water.

We present ALMA observations of the D$_2$O $1_{1,0}$–$1_{0,1}$ transition at 316.8 GHz toward B335 and L483 at $\lesssim 0.\!\!^{\prime\prime}5$ ($\lesssim 100~$au) resolution, probing the inner warm envelope gas. The column densities of D$_2$O, HDO, and H$_{2}^{18}$O are determined by synthetic spectrum modeling and direct Gaussian fitting, under the assumption of a single excitation temperature and similar spatial extent for the three water isotopologs.

D$_2$O is detected toward both sources in the inner warm envelope. The derived D$_2$O/HDO ratio is $(1.0\pm0.2)\times10^{-2}$ for L483 and $(1.4\pm0.1)\times10^{-2}$ for B335. These values indicate that the D$_2$O/HDO ratio is higher than the HDO/H$_2$O ratios by a factor of $\gtrsim2$ toward both sources.

The high D$_2$O/HDO ratios are a strong indication of chemical inheritance of water from the prestellar phase down to the inner warm envelope. This implies that the local cloud conditions in the prestellar phase, such as temperatures and timescales, determine the water chemistry at later stages and could provide a source of chemical differentiation in young systems. In addition, the observed D$_2$O/H$_2$O ratios support an observed dichotomy in the deuterium fractionation of water toward isolated and clustered protostars, namely, a higher D/H ratio toward isolated sources.

# Introduction

Addressing when and how water is synthesized during the formation of stars and planetary systems is essential to our understanding of the delivery of water, and other volatiles, to young planets. Water is a requirement for life as we know it and therefore central for the habitability of planets (cite: chyba2005). Additionally, water acts as a coolant in molecular gas and is a major constituent of the solid mass reservoirs in protoplanetary disks (cite: dishoeck2014; karska2018).

![](./figures/grain_updated.png)

Water is among the most abundant molecules in the interstellar medium and has been observed at all major stages of star and planet formation. In prestellar cores, water is a major constituent of the thick ice caps with $X_\mathrm{ice}\sim10^{-4}$ with respect to H$_2$ (cite: whittet1996; bergin2002; boogert2015). In the inner warm envelope toward Class 0 sources, water ice is thermally desorbed, and the derived gas-phase water abundance reaches $X_\mathrm{gas}\sim10^{-7}$–$10^{-4}$ (cite: ceccarelli2000; persson2016). In outflows, water is sputtered off the grains or synthesized directly in the gas phase, and the abundances can reach $X_\mathrm{gas}\sim10^{-6}$–$10^{-4}$ (cite: kristensen2017). Meanwhile, a recent search for water toward nearby Class I sources shows that gas-phase water abundances are low in young disks($X_\mathrm{gas}\lesssim10^{-6}$), indicating that most of the water remains locked in ice at this stage (cite: harsono2020). These observations provide vital constraints on the chemical evolution of water and reveal that water is formed as ice at high abundance in molecular clouds and prestellar cores (cite: vandishoeck2020). This is confirmed by models of the chemical evolution during star formation (cite: taquet2013model; furuya2016; coutens2020). However, a central question remains as to what extent is water in protoplanetary disk inherited from the prestellar cloud or synthesized locally in the disk (cite: visser2009; cleeves2014). If prestellar inheritance is the dominant source of water in the protoplanetary disk, then the water chemistry is set by the conditions in the local cloud environment (e.g., the temperature, radiation field, and duration). This could promote some chemical differentiation in planetary systems. Conversely, if local processing in the disk is significant, then local conditions in the disk may strongly influence the chemistry of water and other volatiles.

By studying the deuterium fractionation of water, we can determine how the physical conditions affect the water chemistry and track the chemical evolution during star and planet formation (cite: ceccarelli2014). Deuterium fractionation occurs as a consequence of several chemical processes that depend sensitively on the temperature, density, visual extinction, and ionization sources (cite: caselli2012). At low temperatures ($\lesssim50~$K), the prominent pathway is the gas-phase exchange reaction H$_{3}^{+}$ + HD $\rightleftharpoons$ H$_2$D$^{+}$ + H$_2$ + $\Delta E$, where $\Delta E$ depends on the spin state of the involved reactants. This forward reaction is endothermic, and the backward reaction is inhibited at low temperatures, thereby leading to an enrichment of H$_2$D$^{+}$ relative to H$_{3}^{+}$. H$_2$D$^+$ (and D$_2$H$^+$, D$_{3}^{+}$) dissociatively recombines with free electrons to form atomic D, thus increasing the local atomic D/H ratio in the gas phase and ultimately on dust grain surfaces where water and other molecules are formed through hydrogenation (cite: tielens1983; roberts2003). Detections of gas phase H$_2$D$^{+}$ confirm that this enrichment is occurring in the gas phase in prestellar cores (cite: caselli2003; vastel2004).

Observations of HDO and H$_{2}^{18}$O toward Class 0 source show that the degree of deuterium fractionation varies on different spatial scales (cite: persson2014). Single-dish observations, some of which may arise in the cold extended envelope, reveal high D/H ratios of water; HDO/H$_2$O ratios range from 10$^{-3}$ to 10$^{-2}$ (cite: stark2004; parise2005; coutens2012). Meanwhile, interferometric observations targeting the inner warm region have found much lower water deuteration; in these observations HDO/H$_2$O ratios range from $10^{-4}-10^{-3}$ (cite: jorgensen2010a; taquet2013observation; persson2014; jensen2019). The first detection of interstellar D$_2$O was presented by (cite: butner2007), who derived a D$_2$O/HDO ratio of 1.7$\times10^{-3}$ toward IRAS16293–2422 based on single-dish observations. In a later work, (cite: coutens2012) found a higher D$_2$O/HDO ratio of $\sim$0.06 toward the same source using *Herschel* HIFI data. Interferometric detections of D$_2$O on inner envelope scales prior to this work are limited to (cite: coutens2014), who found a high D$_2$O/HDO ratio of $\sim 1\%$ and D$_2$O/H$_2$O $\sim$ 2$\times$10$^{-5}$ toward NGC1333 IRAS 2A. The current observational understanding is outlined in Fig. [1](#fig:schematic).

The observed difference in D/H ratios on different spatial scales can be understood as a result of the chronological evolution of water chemistry during star formation (cite: dartois2003; taquet2013model; furuya2016). Before cloud collapse, water ice is formed in the molecular cloud with a lower deuterium fraction, as a result of higher temperatures and moderate extinction in this phase ($T\sim20$ K, $A_\mathrm{v}\lesssim5$ mag). Later, as the cloud core cools and contracts, the extinction increases and CO is depleted (cite: caselli1999). During this phase, the deuterium fractionation becomes highly efficient, and a second generation of highly deuterated water ice is formed. This chronology leads to two distinct components in the interstellar ice: the bulk ice mantle consists of a water-rich ice with lower D/H ratio, and the surface consists of a mix of highly deuterated water, CO, and complex organics (see Fig. [1](#fig:schematic)). This scenario can explain the observed deuterium fractionations: on larger spatial scales, the bulk water reservoir remains in the solid phase, and the observed gas phase primarily consists of water with a high D/H ratio. This gas-phase water is either photo-desorbed from the ice surface layers or formed directly in the gas phase at low temperature and high extinction, that is, with a high D/H ratio (cite: taquet2013model; furuya2016). Meanwhile, in the inner warm gas, where the ice is entirely sublimated, the gas-phase HDO/H$_2$O ratio of water is lowered, since the ice reservoir with a lower D/H ratio is released from the dust grains. The similarity between D$_2$O/HDO ratios on larger and smaller scales support this scenario; the abundance of deuterated water isotopologs is low in the bulk water ice, and consequently the ratio is largely unaffected by the sublimation of the bulk water ice.

A consequence of the above scenario for water formation is that the D/H ratio of water could depend on the physical conditions in the molecular cloud and prestellar core prior to and during the protostellar collapse. Lower temperatures or a longer duration of the deeply embedded phase would increase the D/H ratio observed in the inner warm region. Conversely, a faster collapse or warmer gas temperature could lower the D/H ratio in the inner warm region. This would imply a relation between the bulk water D/H ratio and the dynamics of the formation environment. Isolated protostars may collapse more slowly than clustered counterparts because the stability of the cloud is determined solely by the internal cloud structure (cite: ward-thompson2007; enoch2008). Moreover, the temperature in clustered regions could be higher owing to, for instance, more external radiation or shock heating (cite: krumholz2014; hocuk2017). Either of these scenarios would enhance the D/H ratio toward isolated protostars in contrast to clustered protostars, in which external factors can influence the physical conditions. Such a differentiation was recently suggested based on ALMA observations of HDO and H$_{2}^{18}$O in the warm inner envelope toward three isolated protostars (cite: jensen2019). If the enhanced HDO/H$_2$O ratio is a consequence of environmental effects, then the same might also apply to D$_2$O.

In this work, we present the first ALMA detections of D$_2$O in the inner warm region toward the isolated low-mass Class 0 protostars B335 and L483. We combine the D$_2$O detections with previous detections of HDO and H$_{2}^{18}$O toward the sources to derive D$_2$O/HDO, D$_2$O/H$_2$O and HDO/H$_2$O ratios consistently. This work aims to constrain the chemical evolution of water between the molecular cloud and the inner warm envelope toward Class 0 sources. Furthermore, accurate determination of the D/H ratio in the warm envelope allow for comparison between the deuterium fractionation in protoplanetary disk and warm envelopes toward Class 0 sources, thereby establishing a possible link between these regimes.

The paper is organized as follows. In Section 2, the observations and data reduction are presented. The data analysis is presented in Section 3, and the results are discussed in Section 4. Throughout the paper we refer to NGC1333 IRAS 2A as IRAS 2A. We denote HDO/H$_2$O as f$_\mathrm{D1}$ and D$_2$O/HDO as f$_\mathrm{D2}$, and use both terms interchangeably. Furthermore, we refer to the inner warm gas component, where $r \lesssim 100$ au and $T \gtrsim 100$ K, as the warm envelope.

# Observations

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Date | Phase calibrator | Bandpass calibrator | Max. baseline (m) | n$_{\mathrm{antennas}}$ | $v_\mathrm{LSR}$(km/s) |
| L483 | 2019 October 29 | J1743$-$0350 | J1924$-$2914 | 697 | 42 | 4.5 |
| B335 | 2019 October 8 | J1938$+$0448 | J1924$-$2914 | 784 | 42 | 8.3 |
|  |  |  |  |  |  |  |

![](./figures/all_cont_D2Odata.pdf)

![](./figures/2x2_figure_moment0.pdf)

The low-mass protostars B335 and L483 were observed with ALMA during Cycle 7 (PI: Sigurd S. Jensen, projectid: 2019.1.00720.S). Information on the observation dates and calibration sources can be found in Table [\[table:observations\]](#table:observations). In the present analysis, we also utilize additional spectral windows from the data presented in (cite: jensen2019) toward both sources; this latter work gives a detailed description of those observations.

The spectral setup targeted the D$_2$O $1_{1,0}$–$1_{0,1}$ transition at 316.8119 GHz in the ALMA band 7. The imaged spectral windows contain 1920 channels with a width of 122 kHz (0.11 km s$^{-1}$). The observed phase centers are $\alpha_\mathrm{J2000}:$ 19:37:00.89, $\delta_\mathrm{J2000}:$ +07:34:09.5 for B335, and $\alpha_\mathrm{J2000}:$ 18:17:29.91, $\delta_\mathrm{J2000}:$ -04:39:39.6 for L483. The source velocities applied to the spectral tunings are listed in Table [\[table:observations\]](#table:observations).

Each dataset was pipeline-calibrated using casa 5.6 (cite: casa). Subsequent phase self-calibration was attempted for each dataset with casa 5.6. For B335, self-calibration was successful with an improved signal-to-noise ratio (S/N) of $\sim 25\%$; however, for L483, no improvement in S/N level was achieved, and therefore the ALMA pipeline product was preferred.

Imaging was performed with the tclean algorithm with a robust parameter of 0.5. Toward each source, a continuum image at 302 GHz was created and compared with previous ALMA observations toward the sources. The intensities and morphologies of the continuum images are consistent with previous interferometric observations of the sources (cite: imai2016; oya2017; jacobsen2018; imai2019). The final continuum images are shown in Fig. [2](#fig:cont). The synthesized beam size in spectral window centered on the D$_2$O transition are $0.\!\!^{\prime\prime}38\times0.\!\!^{\prime\prime}37$ and $0.\!\!^{\prime\prime}56\times0.\!\!^{\prime\prime}46$ for B335 and L483, respectively.

Continuum subtraction for each spectral window was performed using the sigma-clipping method with the statcont code presented in detail in (cite: statcont). We preferred to use this method because both sources display rich hot corino emission, which made continuum subtraction through the uvcontsub routine in casa challenging (cite: jorgensen2016). For the line analysis, we extracted the spectrum from a single pixel toward the continuum peak position for each source.

The emission lines presented in this work are identified using data from the Jet Propulsion Laboratory (cite: JPL) and the Cologne Database for Molecular Spectroscopy (cite: CDMS). The spectroscopic data used to identify D$_2$O, HDO, H$_{2}^{18}$O are from (cite: D2O_ref), (cite: hdo_ref), and (cite: h218o_ref), respectively. Furthermore, spectroscopic data for CH$_3$OCH$_3$, and CH$_3$OD are from (cite: CH3OCH3_ref) and (cite: CH3OD_ref), respectively. For CH$_3$OD, the exact partition function is unknown, and the current analysis relies on a partition function scaled from the CH$_{3}^{18}$OH partition function, similar to (cite: jorgensen2018). All querying was done through the Splatalogue interface[^2]. Throughout this work, the H$_2$O column density is estimated from H$_{2}^{18}$O by adopting a ${}^{16}$O/${}^{18}$O ratio of 560 (cite: wilson1994).

# Results

The D$_2$O lines were detected toward both sources as part of a broad emission feature. The emission feature was identified as D$_2$O blended with two CH$_3$OD transitions and, potentially, one CH$_3$OCH$_3$ transition. This identification is consistent with the observed feature toward IRAS 2A (cite: coutens2014). As the line is heavily blended, estimation of the column density is challenging, and two complimentary methods were employed. The spatial extent of the D$_2$O and CH$_3$OD emission is confined to the inner envelope, as shown in Fig. [3](#fig:moment0).

![](./figures/B335_D2O.pdf)

![](./figures/L483_D2O.pdf)

## Synthetic spectrum modeling

The first method for the estimation of the D$_2$O column density relies on a synthetic spectrum of the sources. Combining the ALMA data from (cite: jensen2019) with those presented in this work, spectral coverage extends to several spectral windows in ALMA bands 5, 6, and 7. For B335, two unblended transitions of CH$_3$OD and four unblended transitions of CH$_3$OCH$_3$ were identified. For L483, three unblended transitions of CH$_3$OD and three unblended transitions of CH$_3$OCH$_3$ were identified. This allowed for accurate modeling of the blended emission feature around the D$_2$O line (i.e., the combined emission from D$_2$O, CH$_3$OD, and CH$_3$OCH$_3$). The best fit was determined by $\chi^2$ minimization of the data around emission lines. Blended lines and transitions with high optical thickness were manually excluded from the $\chi^2$ estimation. The synthetic spectrum was calculated following the methodology presented in (cite: moller2017) with the addition of an optical depth correction from (cite: goldsmith1999). Toward B335, the observed spectrum was best reproduced by a synthetic model with $N$(D$_2$O) = $3.5\times10^{15}$ cm$^{-2}$, $N$(CH$_3$OD) = $2.5\times10^{17}$ cm$^{-2}$, and $N$(CH$_3$OCH$_3$) = $1.3\times10^{17}$ cm$^{-2}$. For the water isotopologs, the synthetic spectrum model yields HDO/H$_2$O $= (6.3\pm1.5)\times10^{-3}$ and D$_2$O/HDO $= (1.4\pm0.1)\times10^{-2}$ for B335.

For L483, the synthetic spectrum modeling yields column densities of $N$(D$_2$O) = $1.1\times10^{15}$ cm$^{-2}$, $N$(CH$_3$OD) = $1.7\times10^{17}$ cm$^{-2}$, and $N$(CH$_3$OCH$_3$) = $7.9\times10^{16}$ cm$^{-2}$. The D/H ratios toward this source are then HDO/H$_2$O $= (4.0\pm0.5)\times10^{-3}$ and D$_2$O/HDO $= (1.0\pm0.2)\times10^{-2}$. The synthetic spectra are presented in the left panels of Figs. [4](#fig:B335_spectra) and [5](#fig:L483_spectra). For L483, the best-fit spectral model shows some deviation from the observed profile, however, the D$_2$O column density is robust: changing the parameters of the CH$_3$OD and CH$_3$OCH$_3$ components has little impact on the D$_2$O abundance. We note that for L483, many emission lines are double-peaked Gaussians (cite: oya2017; jacobsen2018). The parameters for the best-fit synthetic spectrum are presented in Table [\[table:fit\]](#table:fit), for B335 and L483. The full spectral models for both sources are shown in Appendix [6](#app:fullspectrum).

## Least-squares fitting

In the second, complimentary method, the line profiles were fitted using the least-squares method with the scipy routine curve_fit. Toward B335, the fit was allowed to include up to four Gaussian line profiles, one for each potential transition in the blended emission feature. Bounds on the fits were estimated from the HDO data, and other non-blended emission lines in the dataset. The best fit does not include a fourth component, corresponding to either the CH$_3$OCH$_3$ line at 316.7904 GHz or the CH$_3$OD transition at 316.7916 GHz (i.e., only three Gaussian profiles were included in the final fit). The exclusion of a fourth component has limited impact on the Gaussian profile for D$_2$O. The resulting fit is shown the right panel of Fig. [4](#fig:B335_spectra). The column density is estimated from the fitted line profile by assuming local thermodynamic equilibrium (LTE) (cite: mangum2015). We adopted an excitation temperature of 220 K, which is derived from the synthetic spectrum; this method results in a D$_2$O column density of $4.0\times10^{15}$ cm$^{-2}$. The HDO transitions presented in (cite: jensen2019) give a HDO column density of $1.9\times10^{17}$ cm$^{-2}$ at the same excitation temperature, when a beam filling factor is applied for a source size of $0.\!\!^{\prime\prime}2$. This method then results in a D$_2$O/HDO ratio of $(2.1\pm0.6)\times10^{-2}$. Evidently, the D$_2$O/HDO ratios toward B335 are somewhat higher when using the Gaussian fits, however both methods yield high D$_2$O/HDO ratios $\gtrsim 10^{-2}$. We note that the HDO column density is different from that presented in (cite: jensen2019) because a higher excitation temperature of 220 K and a smaller source size are used in this work. Furthermore, the synthetic model includes an optical depth correction and identifies a slight blending of the H$_{2}^{18}$O line, increasing the HDO/H$_2$O ratio. Because of this, we consider the column densities presented in this work as more accurate. However, this does not impact the results and discussions of the relative HDO/H$_2$O abundances in (cite: jensen2019), in which identical excitation temperatures were used for all sources. The differences in the reported HDO/H$_2$O ratios in this work and in (cite: jensen2019) illustrate the dependence on the methodology and assumptions, however, the observed dichotomy between isolated and clustered protostars reported in that paper is robust. To remove the observed dichotomy requires consistently adopting lower excitation temperatures for the isolated sources, independent of the luminosity of the respective sources.

In the case of L483, the emission lines are generally double-peaked Gaussian profiles (cite: jensen2019). These features are more challenging to fit when strongly blended and attempts to fit double-peaked Gaussians to all four potential emission lines did not produce good results. Instead, single Gaussians were fitted to each transition, which provided reasonable fits (as shown in the right panel of Fig. [5](#fig:L483_spectra)). The fitted Gaussian profiles result in $N$(D$_2$O) = $1.7\times10^{15}$ cm$^{-2}$, which, combined with $N$(HDO) = $1.2\times10^{17}$ cm$^{-2}$, yield D$_2$O/HDO $= (1.4\pm0.4)\times10^{-2}$. Again, this method returns a higher D$_2$O/HDO than the synthetic spectrum model. For L483, an excitation temperature of 165 K was used, which was derived from the synthetic spectrum model. Overall, both methods agree, given the inherent flux density uncertainty of ALMA ($\sim10\%$) and the uncertainties in the fitting ($\sim10\%$).

Both methods assume that water emission from the warm envelope is in LTE. Previous studies of water isotopologs with interferometers have assessed the validity of this approach. (cite: persson2014) compare the optically thin LTE approximation to radiative transfer models for two Class 0 sources and find agreement between the two methods. (cite: coutens2014) compare non-LTE radex calculations and LTE calculations for the same HDO transitions presented in this work and found that the LTE approach is valid for these transitions. Generally, the LTE approach is suitable for water emission in the inner envelope, where the densities are similar or higher than the critical densities for the targeted transitions.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | $N_\mathrm{model}$ (cm$^{-2}$) | $N_\mathrm{fit}$ (cm$^{-2}$) | FWHM (km/s) | $v_\mathrm{LSR}$ (km/s) | $T_\mathrm{ex}$ (K) |
|  |  |  |  |  |  |
| D$_2$O | $1.1\times10^{15}$ | $1.7\times10^{15}$ | (4.5, 5.2) | (1.75, 7.65) | 165 |
| HDO | $1.1\times10^{17}$ | $1.2\times10^{17}$ | (4.9, 5.7) | (1.75, 7.65) | 165 |
| H$_{2}^{18}$O | $5.1\times10^{16}$ | $5.9\times10^{16}$ | (6.2, 7.1) | (1.75, 7.65) | 165 |
|  |  |  |  |  |  |
| D$_2$O | $3.5\times10^{15}$ | $4.0\times10^{15}$ | 4.25 | 7.6 | 220 |
| HDO | $2.5\times10^{17}$ | $1.9\times10^{17}$ | 4.0 | 7.9 | 220 |
| H$_{2}^{18}$O | $6.3\times10^{16}$ | $7.1\times10^{16}$ | 5.65 | 7.9 | 220 |
|  |  |  |  |  |  |

# Discussion

The observed sources show high abundances of doubly deuterated water, D$_2$O, with D$_2$O/HDO $\gtrsim$ $10^{-2}$ and D$_2$O/HDO \> HDO/H$_2$O for both sources. The derived f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratios for L483 and B335 are $\sim$2.5 and $\sim$2, respectively. This is similar to the previous determination of D$_2$O/HDO in the warm envelope toward IRAS 2A presented in (cite: coutens2014), who reported D$_2$O/HDO $\gtrsim$ $10^{-2}$ and f$_\mathrm{D2}$/f$_\mathrm{D1} \gtrsim 7$. Table [\[table:deuteration\]](#table:deuteration) presents an overview of the HDO/H$_2$O and D$_2$O/HDO ratios toward low-mass Class 0 sources, limited to data which are determined with interferometric observations of the warm envelope. The high D$_2$O abundances reported in this work has several implications for the inheritance of water and the tentative correlation between protostellar environment and D/H ratio in water, which is discussed below.

| Object | HDO/H$_2$O ($\times10^{-4}$) | D$_2$O/HDO ($\times10^{-2}$) | f$_\mathrm{D2}$/f$_\mathrm{D1}$ | Reference |
|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |
| NGC1333 IRAS 2A | $7.4\pm2.1$ | ... | ... | 1 |
| – | $17\pm8$ | $1.2\pm0.5$ | $7\pm4$ | 2 |
| NGC1333 IRAS 4A-NW | $5.4\pm1.5$ | ... | ... | 1,3 |
| NGC1333 IRAS 4B | $5.9\pm2.6$ | ... | ... | 1 |
| IRAS 16293–2422 | $9.2\pm2.6$ | ... | ... | 1 |
|  |  |  |  |  |
| BHR71–IRS1 | $18\pm4$ | ... | ... | 3 |
| B335 | $17\pm3$ | ... | ... | 3 |
| – | $63\pm15$ | $1.4\pm0.1$ | $2.2\pm0.5$ | 4 |
| L483 | $22\pm4$ | ... | ... | 3 |
| – | $40\pm5$ | $1.0\pm0.2$ | $2.5\pm0.3$ | 4 |
|  |  |  |  |  |

Table notes: The table only include interferometric observations of the inner warm region toward low-mass Class 0 protostars.

## Inheritance of water D/H ratio

The D/H ratio of water is an essential tool for determining the chemical evolution of water during star and planet formation. Deuterium fractionation of water can proceed through multiple pathways during the evolutionary stages of star and planet formation with varying efficiency (cite: caselli2012; dishoeck2014). In a recent work, (cite: furuya2017) studied the evolution of the water D/H ratio during the star formation process from cloud to disk for hundreds of tracer particles in a 2D axisymmetric model, including both the protostellar collapse and the protoplanetary disk phases. These authors showed that water formation with HDO/H$_2$O ratios in the range $10^{-4}$–$10^{-3}$ can occur both through prestellar inheritance and in situ water formation in the cold midplane of the protoplanetary disk. Hence, distinguishing between inheritance and in situ formation based solely on the HDO/H$_2$O ratio is challenging. Meanwhile, models suggest that the formation of D$_2$O is inefficient in protoplanetary disks when compared to the prestellar core phase. Therefore, (cite: furuya2017) suggest that the ratio of f$_\mathrm{D2}$/f$_\mathrm{D1}$ is a more robust tracer of chemical inheritance for water. Quantitatively, the model of (cite: furuya2017) shows that a f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratio around $\sim10$ is formed in the prestellar phase, while a much lower ratio of f$_\mathrm{D2}$/f$_\mathrm{D1} \sim0.1$ is found for water formed within the protoplanetary disk.

For L483 and B335, the observed f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratios are $\gtrsim$2. Prior to this work, f$_\mathrm{D2}$/f$_\mathrm{D1}$ was determined in the hot corino toward IRAS 2A, where the ratio is $\gtrsim7$. The observed ratios, f$_\mathrm{D2}$/f$_\mathrm{D1} > 1$, suggest that water in the warm envelope is predominantly inherited from the prestellar phase and has not undergone reprocessing during accretion from the cloud to the warm envelope toward these sources.

Recently, (cite: jensen2021) studied the D/H ratio of water during the formation of several low-mass protostars in a dynamic 3D magnetohydrodynamics simulation of a molecular cloud region. For each protostar, thousands of tracer particles recorded the physical evolution during the accretion process from the large-scale environment down to the warm envelope. The temperature structure of the envelopes was calculated using the Monte Carlo radiative transfer code radmc-3d (cite: dullemond2012). Subsequently, the chemical evolution along each particle trajectory was modeled to determine the gas-phase f$_\mathrm{D2}$ and f$_\mathrm{D1}$ ratios in the warm envelope. These authors find that f$_\mathrm{D2}$/f$_\mathrm{D1}$ depends on the choice of initial conditions in the prestellar cloud (e.g., the duration and temperature of this phase). A similar conclusion is presented in (cite: taquet2013model), in which the authors study the formation of deuterated water for a broad range of initial conditions in the prestellar phase. These results suggest that the lower f$_\mathrm{D2}$/f$_\mathrm{D1}$ ratios may stem from different prestellar conditions, which was not included in the study by (cite: furuya2017). By studying a range of initial conditions, (cite: jensen2021) show that the D/H ratio of water in the warm envelope is determined by the conditions in the prestellar phase and is not sensitive to variations during the protostellar collapse itself, in other words, suggestive of chemical inheritance of water from the prestellar stages. A high degree of inheritance for water is also suggested by (cite: cleeves2014), who show that the D/H ratio of water synthesized in situ in protoplanetary disks is low, and find that a high degree of inheritance is necessary to explain the D/H ratios of comets in the Solar System with low ionization rates.

With the high observed D$_2$O/HDO ratios in the warm envelope, the case for a high degree of inheritance from the prestellar core stage down to the warm envelope ($\lesssim 100~$au) appears strong.

The physical and chemical link between the warm envelope and the formation of protoplanetary disks and planets is unclear (cite: harsono2020). Recently, the evidence for early planet formation is growing with a number of detections of planetary signatures in young systems (cite: keppler2018; teague2018; harsono2018; pinte2020; alves2020). Furthermore, advances in planet formation theory suggest that planet formation may be a fast process and can occur early (cite: johansen2017). If planet formation starts early, the chemical inheritance observed in these Class 0 sources may directly impact the chemistry at the onset of planet formation. Currently, the D/H ratio of water in bona fide protoplanetary disks is unknown. An alternative tracer for the chemistry during planet formation is the study of the chemical composition of comets, including the D/H ratio (cite: mumma2011; bockelee2015). Comets are planetesimals in the outer solar nebula that record the pristine ice composition in the Solar System during planet formation. Tentative evidence for a chemical link between the warm envelope and protoplanetary disks is emerging. (cite: altwegg2017) determine the D/H ratios of water in the coma of comet 67P/Churyumov-Gerasimenko (hereafter comet 67P) with the ROSINA instrument. They found D$_2$O/HDO $= (1.8\pm0.9)\times10^{-2}$ and HDO/H$_2$O $= (1.05\pm0.14)\times10^{-3}$, corresponding to f$_\mathrm{D2}$/f$_\mathrm{D1} \sim 17$, which is incompatible with in situ D$_2$O formation in the protoplanetary disk (cite: furuya2017). This suggests a high degree of inheritance, and furthermore the measured D$_2$O/HDO ratio is similar to the ratios observed in warm envelopes. Overall, current estimates of the D/H ratios of water in comets and warm envelopes could indicate a similar chemical evolution for the cold icy component that constitute comets such as comet 67P, and the material that enters the warm envelope, where ice is sublimated off the dust grains. A chemical link between the warm envelope and cometary bodies is also supported by the apparent correlation between complex organic molecules (COMs) in the hot corino of IRAS16293–2422 and comet 67P, which may indicate a link between the chemical inventory in cold icy planetesimals and hot corinos (cite: drozdovskaya2019). Similarly, a recent study by (cite: bianchi2019) also finds a correlation between the abundances of COMs in protostars and comets. The authors compared the inventory of COMs for a larger sample of Class 0 and Class I sources to cometary values in the literature and find good agreement between the abundances of COMs in Class 0 sources and comets, while the Class I sources showed more variation.

## Environmental impact on the D/H ratio

The D$_2$O/HDO ratios toward B335 and L483 are on the order of $10^{-2}$, similar to the lower limit derived in (cite: coutens2014) toward IRAS 2A. Following the definitions of (cite: jensen2019), B335 and L483 are isolated protostars (i.e., not associated with any cloud complexes) while IRAS 2A is located in NGC1333. Given the higher HDO/H$_2$O ratios in the isolated sources, these results appear to follow the same trend between water deuterium fractionation and protostellar environment. The isolated protostars show higher D/H ratios in HDO and similar D$_2$O/HDO ratios, that is, the overall D/H ratio is higher than in clustered counterparts. Another way to illustrate this is to look at the D$_2$O/H$_2$O ratio. For L483, B335, and IRAS 2A, the D$_2$O/H$_2$O is $9\times10^{-5}$, $4\times10^{-5}$, and $2\times10^{-5}$, respectively. Hence, the D$_2$O/H$_2$O ratios toward the isolated protostars are a factor $\gtrsim2$ higher than the clustered source observed so far. The D$_2$O abundances therefore corroborate a higher D/H ratio of water toward isolated protostars, similar to the trend observed in HDO. However, the sample size remains too small to draw definite conclusions and should be further expanded.

(cite: jensen2019) propose that the observed trend in D/H ratios could originate from either higher temperatures or stronger irradiation in star-forming clusters, or a difference in the collapse timescale between isolated cores, which is subject to limited external perturbations, and clustered sources for which several mechanisms may perturb the dynamics of the cores, such as jets and outflows from nearby stars. Clustered star-forming regions may also be intrinsically more turbulent; that is, the probability of multiple star formation events may correlate with the turbulence in the region (cite: ward-thompson2007; krumholz2014).

The physicochemical 3D models of water deuteration presented in (cite: jensen2021) find that variations in the temperature or duration of the prestellar phase can induce the observed dichotomy in water D/H ratios. Higher temperatures during both the prestellar core phase and protostellar collapse lead to lower D/H ratios of water. Similarly, a shorter embedded phase (i.e., a shorter prestellar core duration) leads to a lower D/H ratio, which is consistent with the hypothesis that clustered sources collapse on shorter timescales. Both effects can drive the differences in D/H ratios between clustered and isolated low-mass protostars. Meanwhile, variations in irradiation appear unlikely to directly drive the dichotomy in observed D/H water ratios in the warm envelope toward low-mass protostars. The study by (cite: jensen2021) demonstrates a link between the chemistry in the prestellar stages and gas-phase water D/H ratio in the warm envelope, which is corroborated by the observed D/H ratios of water from this region toward Class 0 sources. This link motivates further study, both observationally and theoretically, to determine whether other molecules exhibit a similar link between conditions in the environment and the chemistry in the warm envelope region toward young embedded protostars.

# Summary and outlook

This work presents the first ALMA observations of D$_2$O in the warm envelope toward low-mass protostars. We determine HDO/H$_2$O and D$_2$O/HDO ratios by combining the column densities of D$_2$O with HDO and H$_{2}^{18}$O data. These ratios provide new insights into the chemical evolution of water during the star formation process.

- Both L483 and B335 have D$_2$O/HDO ratios $\gtrsim 10^{-2}$. When combined with previous ALMA estimates of the HDO/H$_2$O ratios, the \[D$_2$O/HDO\]/\[HDO/H$_2$O\] ratios are derived to be $\sim$2.5 and $\sim$2, respectively. D/H ratios of this magnitude are strong evidence of chemical inheritance from the prestellar core stage. Chemical models suggest that a D$_2$O/HDO ratio of this magnitude can only form during the cold phase prior to star formation.

- Both sources are isolated and show enhanced D$_2$O/H$_2$O ratios compared to a clustered counterpart by a factor of $\gtrsim 2$. The high D$_2$O/H$_2$O ratios strengthen the evidence for a correlation between the D/H ratio of water and the protostellar environment, as suggested in (cite: jensen2019). This is consistent with a high degree of inheritance from the prestellar phases and provides a mechanism for chemical diversity in the envelopes surrounding embedded protostars (e.g., through a longer duration or colder temperatures in the prestellar phase).

- The observed D$_2$O/HDO ratios in hot corinos are similar to the value measured in Comet 67P of $\sim 10^{-2}$, providing tentative evidence of a common chemical evolution of the water that sublimates in the warm envelope and water incorporated in comets and icy planetesimals that are the building blocks of planets in the Solar System.

These observations highlight the power of the deuterium fractionation as a tracer for the chemical trail during star formation. More observations of the D/H ratios of water at different stages of star and planet formation will provide further constraints on the amount of inheritance between the evolutionary stages and establish the impact of the local environment on the chemical evolution. The relation between the local cloud environment and isotope fractionation should be explored further by studying, for example, nitrogen or carbon fractionation, toward both isolated and clustered sources at various evolutionary stages.

# Acknowledgements

The authors thank the referee for useful comments that helped improve the manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00693.S, ADS/JAO.ALMA#2019.1.00720.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The group of JKJ acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No 646908) through ERC Consolidator Grant "S4F". AC acknowledges financial support from the Agence Nationale de la Recherche (grant ANR-19-ERC7-0001-01). This paper makes use of matplotlib (cite: hunter2007) and scipy (cite: 2020SciPy-NMeth).

72 natexlab

(ref: altwegg2017) Altwegg, K., Balsiger, H., Berthelier, J. J., et al. 2017, Philosophical Transactions of the Royal Society of London Series A, 375, 20160253

(ref: alves2020) Alves, F. O., Cleeves, L. I., Girart, J. M., et al. 2020, The Astrophysical Journal, 904, L6

(ref: CH3OD_ref) Anderson, T., Herbst, E., & Delucia, F. C. 1993, Journal of Molecular Spectroscopy, 159, 410

(ref: bergin2002) Bergin, E. A. & Snell, R. L. 2002, ApJ, 581, L105

(ref: bianchi2019) Bianchi, E., Codella, C., Ceccarelli, C., et al. 2019, MNRAS, 483, 1850

(ref: bockelee2015) Bockelée-Morvan, D., Calmonte, U., Charnley, S., et al. 2015, Space Sci. Rev., 197, 47

(ref: boogert2015) Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541

(ref: D2O_ref) Brünken, S., Müller, H. S. P., Endres, C., et al. 2007, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 9, 2103

(ref: butner2007) Butner, H. M., Charnley, S. B., Ceccarelli, C., et al. 2007, ApJL, 659, L137

(ref: caselli2012) Caselli, P., Keto, E., Bergin, E. A., et al. 2012, ApJ, 759, L37

(ref: caselli2003) Caselli, P., van der Tak, F. F. S., Ceccarelli, C., & Bacmann, A. 2003, A&A, 403, L37

(ref: caselli1999) Caselli, P., Walmsley, C. M., Tafalla, M., Dore, L., & Myers, P. C. 1999, ApJL, 523, L165

(ref: ceccarelli2014) Ceccarelli, C., Caselli, P., Bockelée-Morvan, D., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 859

(ref: ceccarelli2000) Ceccarelli, C., Castets, A., Caux, E., et al. 2000, A&A, 355, 1129

(ref: chyba2005) Chyba, C. F. & Hand, K. P. 2005, ARA&A, 43, 31

(ref: cleeves2014) Cleeves, L. I., Bergin, E. A., Alexand er, C. M. O. D., et al. 2014, Science, 345, 1590

(ref: coutens2020) Coutens, A., Commerçon, B., & Wakelam, V. 2020, A&A, 643, A108

(ref: coutens2014) Coutens, A., Jørgensen, J. K., Persson, M. V., et al. 2014, ApJ, 792, L5

(ref: coutens2012) Coutens, A., Vastel, C., Caux, E., et al. 2012, A&A, 539, A132

(ref: dartois2003) Dartois, E., Thi, W. F., Geballe, T. R., et al. 2003, A&A, 399, 1009

(ref: h218o_ref) de Lucia, F. C., Helminger, P., Cook, R. L., & Gordy, W. 1972, Physical Review A, 6, 1324

(ref: drozdovskaya2019) Drozdovskaya, M. N., van Dishoeck, E. F., Rubin, M., Jørgensen, J. K., & Altwegg, K. 2019, MNRAS, 490, 50

(ref: dullemond2012) Dullemond, C. P., Juhasz, A., Pohl, A., et al. 2012, RADMC-3D: A multi-purpose radiative transfer tool

(ref: CH3OCH3_ref) Endres, C. P., Drouin, B. J., Pearson, J. C., et al. 2009, A&A, 504, 635

(ref: enoch2008) Enoch, M. L., Evans, Neal J., I., Sargent, A. I., et al. 2008, ApJ, 684, 1240

(ref: furuya2017) Furuya, K., Drozdovskaya, M. N., Visser, R., et al. 2017, A&A, 599, A40

(ref: furuya2016) Furuya, K., van Dishoeck, E. F., & Aikawa, Y. 2016, A&A, 586, A127

(ref: goldsmith1999) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: harsono2018) Harsono, D., Bjerkeli, P., van der Wiel, M. H. D., et al. 2018, Nature Astronomy, 2, 646

(ref: harsono2020) Harsono, D., Persson, M. V., Ramos, A., et al. 2020, A&A, 636, A26

(ref: hocuk2017) Hocuk, S., Szűcs, L., Caselli, P., et al. 2017, A&A, 604, A58

(ref: hunter2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: imai2019) Imai, M., Oya, Y., Sakai, N., et al. 2019, ApJ, 873, L21

(ref: imai2016) Imai, M., Sakai, N., Oya, Y., et al. 2016, ApJL, 830, L37

(ref: jacobsen2018) Jacobsen, S. K., Jørgensen, J. K., Di Francesco, J., et al. 2019, A&A, 629, A29

(ref: jensen2021) Jensen, S. S., Jørgensen, J. K., Furuya, K., Haugbølle, T., & Aikawa, Y. 2021, A&A, 649, A66

(ref: jensen2019) Jensen, S. S., Jørgensen, J. K., Kristensen, L. E., et al. 2019, A&A, 631, A25

(ref: johansen2017) Johansen, A. & Lambrechts, M. 2017, Annual Review of Earth and Planetary Sciences, 45, 359

(ref: jorgensen2018) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170

(ref: jorgensen2016) Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595, A117

(ref: jorgensen2010a) Jørgensen, J. K. & van Dishoeck, E. F. 2010, ApJ, 725, L172

(ref: karska2018) Karska, A., Kaufman, M. J., Kristensen, L. E., et al. 2018, ApJS, 235, 30

(ref: keppler2018) Keppler, M., Benisty, M., Müller, A., et al. 2018, A&A, 617, A44

(ref: kristensen2017) Kristensen, L. E., van Dishoeck, E. F., Mottram, J. C., et al. 2017, A&A, 605, A93

(ref: krumholz2014) Krumholz, M. R. 2014, Phys. Rep., 539, 49

(ref: mangum2015) Mangum, J. G. & Shirley, Y. L. 2015, PASP, 127, 266

(ref: casa) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: hdo_ref) Messer, J., Lucia, F. C. D., & Helminger, P. 1984, Journal of Molecular Spectroscopy, 105, 139

(ref: moller2017) Möller, T., Endres, C., & Schilke, P. 2017, A&A, 598, A7

(ref: CDMS) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: mumma2011) Mumma, M. J. & Charnley, S. B. 2011, ARA&A, 49, 471

(ref: oya2017) Oya, Y., Sakai, N., Watanabe, Y., et al. 2017, ApJ, 837, 174

(ref: parise2005) Parise, B., Caux, E., Castets, A., et al. 2005, A&A, 431, 547

(ref: persson2016) Persson, M. V., Harsono, D., Tobin, J. J., et al. 2016, A&A, 590, A33

(ref: persson2014) Persson, M. V., Jørgensen, J. K., van Dishoeck, E. F., & Harsono, D. 2014, A&A, 563, A74

(ref: JPL) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883

(ref: pinte2020) Pinte, C., Price, D. J., Ménard, F., et al. 2020, ApJL, 890, L9

(ref: roberts2003) Roberts, H., Herbst, E., & Millar, T. J. 2003, ApJL, 591, L41

(ref: statcont) Sánchez-Monge, Á., Schilke, P., Ginsburg, A., Cesaroni, R., & Schmiedeke, A. 2018, A&A, 609, A101

(ref: stark2004) Stark, R., Sandell, G., Beck, S. C., et al. 2004, ApJ, 608, 341

(ref: taquet2013observation) Taquet, V., López-Sepulcre, A., Ceccarelli, C., et al. 2013a, ApJ, 768, L29

(ref: taquet2013model) Taquet, V., Peters, P. S., Kahane, C., et al. 2013b, A&A, 550, A127

(ref: teague2018) Teague, R., Bae, J., Bergin, E. A., Birnstiel, T., & Foreman-Mackey, D. 2018, ApJL, 860, L12

(ref: tielens1983) Tielens, A. G. G. M. 1983, A&A, 119, 177

(ref: dishoeck2014) van Dishoeck, E. F., Bergin, E. A., Lis, D. C., & Lunine, J. I. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 835

(ref: vandishoeck2020) van Dishoeck, E. F., Kristensen, L. E., Mottram, J. C., et al. 2021, A&A, 648, A24

(ref: vastel2004) Vastel, C., Phillips, T. G., & Yoshida, H. 2004, ApJL, 606, L127

(ref: 2020SciPy-NMeth) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: visser2009) Visser, R., van Dishoeck, E. F., Doty, S. D., & Dullemond, C. P. 2009, A&A, 495, 881

(ref: ward-thompson2007) Ward-Thompson, D., André, P., Crutcher, R., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 33

(ref: whittet1996) Whittet, D. C. B., Schutte, W. A., Tielens, A. G. G. M., et al. 1996, A&A, 315, L357

(ref: wilson1994) Wilson, T. L. & Rood, R. 1994, Annual Review of Astronomy and Astrophysics, 32, 191

# Full synthetic models

The complete synthetic spectrum models for H$_{2}^{18}$O, HDO , D$_2$O, CH$_3$OD, CH$_3$OCH$_3$ are shown in the Figs. [6](#fig:B335_spectrum1) and [7](#fig:L483_spectrum1).

![](./figures/B335_model.pdf)

![](./figures/L483_model.pdf)

[^1]:

[^2]: <https://splatalogue.online>

</paper>

Write the methods card for this paper.