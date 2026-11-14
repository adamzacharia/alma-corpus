# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...972..116I\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...972..116I",
 "title": "Merging Gas-rich Galaxies That Harbor Low-luminosity Twin Quasars at z = 6.05: A Promising Progenitor of the Most Luminous Quasars",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Izumi, Takuma",
 "n_authors": 18,
 "arxiv_id": "2405.02468",
 "doi": "10.3847/1538-4357/ad57c6",
 "alma_projects_linked_by_archive": [
  "2019.A.00019.S"
 ]
}
```

Paper text:
<paper>
# Merging gas-rich galaxies that harbor low-luminosity twin quasars at $z = 6.05$:\
a promising progenitor of the most luminous quasars

## Abstract

We present ALMA \[C II\] 158 $\ensuremath{\mu}m$ line and underlying far-infrared (FIR) continuum emission observations ($0''.57 \times 0''.46$ resolution) toward a quasar-quasar pair system recently discovered at $z = 6.05$ (Matsuoka et al. 2024). The quasar nuclei (C1 and C2) are faint ($M_{\rm 1450} \gtrsim -23$ mag), but we detect very bright \[C II\] emission bridging the 12 kpc between the two objects and extending beyond them (total luminosity $L_{\rm [CII]} \simeq 6 \times 10^9~L_\odot$). The \[C II\]-based total star formation rate of the system is $\sim 550~M_\odot$ yr$^{-1}$ (IR-based dust-obscured SFR is $\sim 100~M_\odot$ yr$^{-1}$), with a \[C II\]-based total gas mass of $\sim 10^{11}~M_\odot$. The dynamical masses of the two galaxies are large ($\sim 9 \times 10^{10}~M_\odot$ for C1 and $\sim 5 \times 10^{10}~M_\odot$ for C2). There is a smooth velocity gradient in \[C II\], indicating that these quasars are a tidally interacting system. We identified a dynamically distinct, fast \[C II\] component around C1: detailed inspection of the line spectrum there reveals the presence of a broad wing component, which we interpret as the indication of fast outflows with a velocity of $\sim 600$ km s$^{-1}$. The expected mass loading factor of the outflows, after accounting for multiphase gas, is $\gtrsim 2-3$, which is intermediate between AGN-driven and starburst-driven outflows. Hydrodynamic simulations in the literature predicted that this pair will evolve to a luminous ($M_{\rm 1450} \lesssim -26$ mag), starbursting ($\gtrsim 1000~M_\odot$ yr$^{-1}$) quasar after coalescence, one of the most extreme populations in the early universe.

# Introduction

In the hierarchical structure formation scenario, galaxies undergo multiple mergers over cosmic time. Models show that mergers of gas-rich galaxies trigger intense star formation and fueling onto the central supermassive black holes (SMBHs), which appear as luminous quasars (cite: 1988ApJ...325...74S; 2005Natur.433..604D; 2006ApJS..163....1H). Some theoretical models predict that subsequent feedback from the quasars, or active galactic nuclei (AGNs), plays a crucial role in driving the co-evolution of SMBHs and host galaxies (cite: 2015ARA&A..53..115K; 2020A&ARv..28....2V), leading to the observed tight correlation between the masses of SMBHs ($M_{\rm BH}$) and those of the host galaxy bulges observed in the local universe (cite: 2013ARA&A..51..511K). Detections of galaxy-scale AGN-driven outflows in multiphase gas (cite: 2008A&A...491..407N; 2012A&A...537A..44A; 2014A&A...562A..21C), a higher AGN fraction in interacting/merging systems (cite: 2011ApJ...743....2S; 2018PASJ...70S..37G; 2018Natur.563..214K), and the global similarity in star-formation and SMBH accretion histories over cosmic time (cite: 2014ARA&A..52..415M), support this scenario.

It is intriguing in this context that massive ($\sim 10^{11}~M_\odot$), quiescent, and old galaxies are already formed at $z \sim 4-5$ (cite: 2023Natur.619..716C; 2023ApJ...947...20V), suggesting that a phase of rapid growth of galaxies and SMBHs, and their associated feedback, had happened at even higher redshifts. Indeed, more than 400 quasars with rest-UV magnitude of $M_{\rm 1450} < -22$ mag are known at $z > 5.7$ to date (cite: 2020ARA&A..58...27I; 2023ARA&A..61..373F), most of which have been identified by wide-field optical and near-infrared surveys (cite: 2016ApJ...833..222J; 2016ApJS..227...11B; 2016ApJ...828...26M; 2018PASJ...70S..35M; 2018ApJS..237....5M). Sub/millimeter observations of the rest-frame far-infrared (FIR) continuum and C$^+$ $^2P_{3/2}$ $\rightarrow$ $^2P_{1/2}$ 157.74 $\ensuremath{\mu}m$ line (\[C II\] 158 $\ensuremath{\mu}m$) emission, the latter is one of the prime coolants of the cold interstellar medium/ISM (cite: 2022ARA&A..60..247W), toward optically luminous quasars ($M_{\rm 1450} \lesssim -26$ mag) by the Atacama Large Millimeter/submillimeter Array (ALMA), have revealed that vigorous starburst (star formation rate SFR $\gtrsim 100-1000~M_\odot$ yr$^{-1}$) and huge amounts of dust ($\sim 10^8~M_\odot$) and gas ($\sim 10^{10}~M_\odot$) are usually associated with these quasars (cite: 2013ApJ...773...44W; 2016ApJ...816...37V; 2020ApJ...904..130V; 2022A&A...662A..60D). Although the prevalence of massive AGN-driven outflows remains unclear from observations of the neutral ISM (cite: 2019A&A...630A..59B; 2020ApJ...904..131N; 2024ApJ...962....1S), fast ionized outflows (probed by, e.g., \[O III\] 5007Å) are frequently seen in $z > 6$ quasars with recent James Webb Space Telescope (JWST) observations (cite: 2023A&A...678A.191M; 2023arXiv230904614Y; 2023ApJ...951L...5Y; 2024arXiv240213319L).

While multiwavelength observations of quasars were progressed significantly in recent years, understanding of their progenitors lags behind. Some limited studies on partially dust-obscured quasars (cite: 2022Natur.604..261F) and starburst galaxies (cite: 2013Natur.496..329R; 2018Natur.553...51M; 2018NatAs...2...56Z), both of which may represent earlier evolutionary phases than UV-bright quasar phase, indeed revealed very rapid mass assembly in these systems at $z > 6-7$. Closely interacting galaxies are considered to be an earlier evolutionary stage than these, yet there are very few examples known to host SMBHs at $z \gtrsim 6$ (cite: 2021ApJ...921L..27Y; 2023AJ....165..191Y). For example, (cite: 2019ApJ...882...10N) studied five pairs of quasar host-companion galaxy at \[C II\], and identified evidence of tidal interaction in three of them. Some other works have also found companion galaxies around quasars at $z > 5-6$ (cite: 2017Natur.545..457D; 2020ApJ...904..130V). (cite: 2019ApJ...880..157D) performed high resolution \[C II\] and FIR continuum observations of another quasar-galaxy pair PJ308$-$21 at $z = 6.23$ that hosts an SMBH of $\sim 3 \times 10^9~M_\odot$ (cite: 2024arXiv240213319L), revealing a large amount of cold ISM and the highly interacting nature of the system (two companions with a projected distance of $\sim 5$ and $\gtrsim 10$ kpc, respectively).

However, the interacting quasars targeted in the above papers are intrinsically as luminous as those of the other, isolated luminous quasars at $z > 6$ (such as those discovered by SDSS), suggesting that the phase of active galaxy interaction had already happened. On the other hand, hydrodynamic simulations of mergers of galaxies predict that both SFR and quasar luminosity increase by orders of magnitude when gas-rich galaxies merge (cite: 2006ApJS..163....1H). Thus, progenitors in the earlier interaction phase, that will evolve to the luminous quasars currently observed, are anticipated to be much fainter. Wide-field optical deep imaging surveys such as the Subaru Hyper Suprime-Cam (HSC) Strategic Survey (cite: 2018PASJ...70S...8A) are useful to search for such faint objects. Indeed, we have established a multi-wavelength follow-up consortium for $z \gtrsim 6$ quasars discovered by the HSC survey, the Subaru High-z Exploration of Low-Luminosity Quasars (cite: 2016ApJ...828...26M; 2018PASJ...70S..35M; 2018ApJS..237....5M; 2019ApJ...883..183M; 2022ApJS..259...18M), and so far discovered $> 150$ low-luminosity quasars down to $M_{\rm 1450} \sim -22$ mag at $z > 6$.

## Our target: a pair of quasars at z = 6.05

This paper presents our ALMA Cycle 7 observations of the \[C II\] 158 $\ensuremath{\mu}m$ line and the underlying rest-frame FIR continuum emission toward the twin quasar system at $z = 6.05$ discovered by our Subaru HSC survey, namely HSC $J$121503.42$-$014858.7 and HSC $J$121503.55$-$014859.3 (C1 and C2, hereafter), separated by 12 kpc projected on the sky (cite: Matsuoka2024). This is the most distant quasar pairs (projected separation $\lesssim 10$ kpc, $\Delta z \lesssim 0.01$) known to date: the discovery and rest-UV properties of these quasars are reported in our companion paper (cite: Matsuoka2024). The presence of pair quasars is a natural consequence of the hierarchical structure formation, yet the sample is very limited due to the rarity of SMBHs and the relatively short duration of the AGN phase.

The two quasars in this study have similar rest-UV properties with $M_{\rm 1450} = -23.11$ mag (C1) and $M_{\rm 1450} = -22.66$ mag (C2): these correspond to quasar bolometric luminosities ($L_{\rm Bol}$) of $6.2 \times 10^{45}$ erg s$^{-1}$ (C1) and $4.1 \times 10^{45}$ erg s$^{-1}$ (C2). The UV magnitudes of these are roughly 10 times higher than the knee of the galaxy luminosity function at $z \sim 6$ (cite: 2022ApJS..259...20H), but are fainter than the characteristic value of the $z \sim 6$ quasar luminosity function (cite: 2018ApJ...869..150M). The quasar nature of C1 + C2 has been further confirmed by the detections of broad Ly$\alpha$ (FWHM $> 1000$ km s$^{-1}$) in both objects with high luminosities ($>10^{43}$ erg s$^{-1}$). The broad Ly$\alpha$ components are sensitive to $M_{\rm BH}$ (cite: 2024ApJ...960..112T); (cite: Matsuoka2024) estimated their masses to be $\log (M_{\rm BH}/M_\odot) \simeq 8.1$ each, corresponding to Eddington ratios of $\sim 0.4$ (C1) and $\sim 0.3$ (C2).

Throughout this work, we adopt the concordant Lambda Cold Dark Matter ($\Lambda$CDM) cosmology with $H_0$ = 70 km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm M} = 0.3$, and $\Omega_{\rm \Lambda} = 0.7$. At the redshift of the source ($z = 6.05$), the age of the universe is 0.905 Gyr and an angular size of $1\ensuremath{''}$ corresponds to a proper distance of 5.68 kpc.

# ALMA Observations

Our observations were conducted as an ALMA Director’s Discretionary (DDT) program (2019.A.00019.S, PI = T. Izumi). There were two executions in ALMA Band 6 (centered on $\lambda_{\rm obs} = 1.1$ mm) on 2020 Feb 29, in a $\sim 23\ensuremath{''}$ diameter field of view with 41 antennas. Three spectral windows (each $\sim 1.875$ GHz wide) were placed on one side-band to maximize the contiguous frequency coverage. We set the phase-tracking center of this pointing to ($\alpha_{\rm ICRS}$, $\delta_{\rm ICRS}$) = (12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.420, $-$01$^\circ$48$'$58$''$.70), which corresponds to the optical position of C1. The baseline length ranged from 15.1 m to 783.5 m, resulting in a maximum recoverable scale of $\sim 5\ensuremath{''}$. Two quasars, J1256$-$0547 and J1217$-$0029, were observed as a flux/bandpass calibrator and a phase calibrator, respectively. The total on-source time was 106 minutes.

The data were first pipeline-processed using `CASA` (cite: 2007ASPC..376..127M; 2022PASP..134k4501C) v.5.6 and further analyzed with v.6.1. All images presented in this work were reconstructed using the `tclean` task down to $3\sigma$ level, with Briggs weighting (robust = 2.0) to maximize the point source sensitivity. For the \[C II\] cube, we averaged several channels to obtain a velocity resolution of 50 km s$^{-1}$, which resulted in a 1$\sigma$ channel sensitivity of 0.14 mJy beam$^{-1}$ (beam size = $0\ensuremath{''}.57 \times 0\ensuremath{''}.46$, P.A. = $-41\ensuremath{^\circ}.2$). Line-free channels were integrated to generate a continuum map ($0\ensuremath{''}.56 \times 0\ensuremath{''}.45$, P.A. = $-43\ensuremath{^\circ}.1$, 1$\sigma$ = 17.2 $\mu$Jy beam$^{-1}$), which we subtracted in the $uv$ plane using the task `uvcontsub` with a first-order polynomial function, before making the line cube. This continuum map was made with the multi-frequency synthesis (MFS) mode of the `tclean` task. In this paper, we show only statistical errors unless mentioned otherwise. The absolute flux uncertainty is $\sim 10\%$ (ALMA Cycle 7 Proposer’s Guide). We also used the `MIRIAD` software (cite: 1995ASPC...77..433S) for some analyses.

# Results

## A galaxy merger caught in the act

We detected the \[C II\] emission from both C1 and C2, and FIR continuum emission mainly from C1, as shown in Figure [1](#fig1)a. The emission properties as well as relevant physical quantities are summarized in Table [1](#tbl1). It is noteworthy that the location of C1 (defined from the HSC $z$-band map; Figure [1](#fig1)b) precisely coincides with the peak position of the \[C II\] velocity-integrated intensity map, confirming the astrometric accuracy of our observations. However, we found that the location of C2 is offset from the nearest local maximum of the \[C II\] emission by $0''.42$ or 2.4 kpc. This local maximum lies between C1 and C2, and we refer to it as the $``$Bridge$"$ hereafter. Note that the location of C2 is determined as the flux-weighted center of the HSC $z$-band map. As the $z$-band emission is spatially extended, this location does not necessarily correspond to the exact location of the quasar. However, it is evident that the bright $z$-band emitting region is offset from this Bridge. We also found significant \[C II\] emission north-west of C1 (offset by $\sim 1''.6$ or 9.3 kpc), which we refer to the $``$Tail$"$ in this work. Both the Bridge and the Tail are most likely formed by interactions of the host galaxies of C1 and C2.

Figure [1](#fig1)c compares the position-velocity diagram (PVD) of Ly$\alpha$ (cite: Matsuoka2024) and that of \[C II\]. It is also clear from this comparison that C2 (bright in Ly$\alpha$) and the Bridge (bright in \[C II\]) are spatially offset. In addition, it is evident that the \[C II\] redshift[^1] of C2 is blueshifted relative to the Ly$\alpha$ redshift reported in (cite: Matsuoka2024) by $z_{\rm [CII]} - z_{\rm Ly\alpha} = -0.008$ (or $\sim -400$ km s$^{-1}$). This velocity offset would be due at least partly to strong Ly$\alpha$ absorption by the intergalactic medium. Indeed, this velocity offset lies nearly at the highest values found in comparably high redshift galaxies, and those galaxies with high velocity offset tend to show low Ly$\alpha$ escape fractions (cite: 2020A&A...643A...6C). Another plausible explanation would be that the Bridge is actually the satellite galaxy itself, and its quasar nucleus (C2) is located at the outskirt of this galaxy. In this case, C2 may have been kicked-out from the host galaxy (Bridge) during this interaction event with the main galaxy (host of C1), which have caused the velocity offset between Ly$\alpha$ and \[C II\] as well. Future JWST observations of the stellar light distribution will allow us to assess whether this offset is due to a real displacement of the quasar from the gravitational center of the host galaxy.

Figure [2](#fig2) shows the velocity channel maps of \[C II\] emission. There is a clear velocity gradient from C2 to the Tail through the Bridge and C1, on scales of $\sim 4''$ or 23 kpc. This clearly indicates that the pair of galaxies are dynamically coupled. Thus, these galaxies will merge in a short time (cite: 2008ApJS..175..356H) to form a single massive galaxy. In addition to this, we found bright \[C II\] emission at C1 in multiple channels of $>170$ km s$^{-1}$, suggesting a presence of dynamically distinct fast component there (see § [3.4](#sec3.4)).

![](fig1.eps)

+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
|                                          | C1                                               | C2 + Bridge                                      | Tail                                             |
+:========================================:+:================================================:+:================================================:+:================================================:+
| R.A. (ICRS)                              | 12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.423         | 12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.536         | 12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.340         |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| Dec (ICRS)                               | $-$01$^\circ$48$'$58$''$.77                      | $-$01$^\circ$48$'$59$''$.28                      | $-$01$^\circ$48$'$57$''$.70                      |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
|                                          | \[C II\] Emission                                                                                                                                      |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $z_{\rm [CII]}$                          | 6.0561 $\pm$ 0.0002                              | 6.0447 $\pm$ 0.0003                              | 6.0566 $\pm$ 0.0003                              |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| Velocity offset (km s$^{-1}$)            | 0                                                | $-481 \pm 13$                                    | $22 \pm 14$                                      |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| FWHM (km s$^{-1}$)                       | $594 \pm 20$                                     | $361 \pm 30$                                     | $317 \pm 34$                                     |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $S_{\rm [CII]}\Delta V$ (Jy km s$^{-1}$) | $3.67 \pm 0.19$                                  | $0.91 \pm 0.13$                                  | $0.52 \pm 0.13$                                  |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $L_{\rm [CII]}$ (10$^9$ $L_\odot$)       | $3.50 \pm 0.18$                                  | $0.87 \pm 0.12$                                  | $0.49 \pm 0.12$                                  |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| SFR$_{\rm [CII]}$ ($M_\odot$ yr$^{-1}$)  | $305 \pm 16$                                     | $75 \pm 11$                                      | $43 \pm 11$                                      |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $M_{\rm H2}$ ($10^{10}~M_\odot$)         | $\sim 10$                                        | $\sim 2.6$                                       | $\sim 1.5$                                       |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
|                                          | Continuum Emission ($T_{\rm dust}$ = 35 K, $\beta$ = 1.6, $\kappa_\lambda = 0.77 ({\rm 850 \ensuremath{\mu}m}/\lambda)^\beta$ cm$^2$ g$^{-1}$)         |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $f_{\rm 1.1mm}$ (mJy)                    | $0.63 \pm 0.05$                                  | $< 0.09$                                         | $< 0.09$                                         |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $L_{\rm FIR}$ (10$^{11}$ $L_\odot$)      | $4.57 \pm 0.36$                                  | $< 0.71$                                         | $< 0.71$                                         |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $L_{\rm TIR}$ (10$^{11}$ $L_\odot$)      | $5.99 \pm 0.48$                                  | $< 0.94$                                         | $< 0.94$                                         |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| $M_{\rm dust}$ (10$^8$ $M_\odot$)        | $1.58 \pm 0.13$                                  | $< 0.25$                                         | $< 0.25$                                         |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+
| SFR$_{\rm TIR}$ ($M_\odot$ yr$^{-1}$)    | $89 \pm 7$                                       | $< 12$                                           | $< 12$                                           |
+------------------------------------------+--------------------------------------------------+--------------------------------------------------+--------------------------------------------------+

: Rest-FIR Properties of the Pair System

Table notes: Coordinates indicate the peak positions of the \[C II\] emission for C1 and Tail. For C2, we adopt the flux-weighted centroid of the HSC $z$-band map (cite: Matsuoka2024). This is spatially averaged with the position of the Bridge to define the position of C2 + Bridge. We used 1$''$.5 and 1$''$.0 diameter apertures to extract the emission properties of C1 and the other components, respectively. Upper limits indicate $3\sigma$ values. The redshifts were determined from single Gaussian fittings to the \[C II\] spectra (see Appendix-[5](#App-I)), but the line fluxes were based on the integrated intensity map (Figure [1](#fig1)).

![](fig2.eps)

## Star-forming nature

With the \[C II\] line and FIR continuum luminosities, we estimate basic star formation properties of this pair system (Table [1](#tbl1)). In order to encompass the emitting region sufficiently, we used a circular aperture of $1''.5$ diameter and $1''.0$ diameter respectively, to measure the fluxes of C1 and the remaining notable regions of C2 + Bridge, and Tail. Note that, as the spatial separation of C2 (12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.55, $-$01$^\circ$48$'$59$''$.3) and the Bridge (12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.522, $-$01$^\circ$48$'$59$''$.26) is only $0''.42$, we present the value at “C2 + Bridge" by placing the aperture at the middle point (12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.536, $-$01$^\circ$48$'$59$''$.28) of C2 and the Bridge. The individual \[C II\] spectra of these regions, as well as the velocity channel maps made with a smoothed $1''.0$ resolution, are presented in Appendix-[5](#App-I) and [6](#App-II).

### From \[C II\] emission

Following (cite: 2005ARA&A..43..677S), the \[C II\] line luminosity is calculated as $$\begin{equation}
L_{\rm [CII]}/L_\odot = 1.04 \times 10^{-3}~S_{\rm [CII]}\Delta V~\nu_{\rm rest}~(1+z)^{-1}~D^2_L,
\end{equation}$$ where $S_{\rm [CII]}\Delta V$ is the \[C II\] line flux in Jy km s$^{-1}$, $\nu_{\rm rest}$ is the rest frequency of 1900.5369 GHz, and $D_L$ is the luminosity distance to the target. The line luminosities of these regions lie in the range $(0.5-3.5) \times 10^9~L_\odot$. The brightest \[C II\] emission originates from C1 ($3.5 \times 10^9~L_\odot$), which is the highest \[C II\] luminosity reported for HSC low-luminosity quasars to date that typically have $L_{\rm [CII]} < 10^9~L_\odot$ (cite: 2018PASJ...70...36I; 2019PASJ...71..111I; 2021ApJ...908..235I; 2021ApJ...914...36I), and is as high as those of optically luminous quasars (cite: 2016ApJ...816...37V; 2020ApJ...904..130V; 2018ApJ...854...97D). This luminosity is also comparable to the luminosities of PJ308$-$21 (cite: 2019ApJ...880..157D), although C1 ($M_{\rm 1450} = -23.1$ mag) is $\sim 20\times$ fainter than the quasar nucleus of PJ308$-$21 ($M_{\rm 1450} = -26.3$ mag) at rest-UV wavelength. We speculate that we are witnessing the recent onset of AGN, which will evolve to a more luminous quasar, in our pair system.

By further assuming that the \[C II\] line is excited primarily by star formation, we can estimate the SFR using the (cite: 2014A&A...568A..62D) calibration based on local H II/starburst galaxies: $\log ({\rm SFR_{[CII]}}/M_\odot~{\rm yr^{-1}}) = -7.06 + 1.0 \times \log (L_{\rm [CII]}/L_\odot)$, with a factor of two calibration uncertainty. This relation is applicable to high redshift ($z \sim 4-8$) star-forming galaxies as demonstrated by (cite: 2020A&A...643A...3S) and (cite: 2020A&A...643A...1L). With this, we find SFR$_{\rm [CII]} = 305 \pm 16~M_\odot$ yr$^{-1}$ in C1 and $75 \pm 11~M_\odot$ yr$^{-1}$ in C2 + Bridge. If some of the \[C II\] excitation is due to the quasars, our derived SFRs are upper limits.

The \[C II\] line luminosity can be used to estimate the molecular gas mass ($M_{\rm H2}$) as well (cite: 2020A&A...643A.141M). Using the calibration of (cite: 2018MNRAS.481.1976Z) for a collection of main sequence and starburst galaxies at intermediate redshifts ($M_{\rm H2}/M_\odot \sim 30 \times L_{\rm [CII]}/L_\odot$), we found $M_{\rm H2} \sim 10, 2.6, 1.5 \times 10^{10}~M_\odot$ in the regions of C1, C2 + Bridge, and Tail, respectively. Note that $L_{\rm [CII]}$ has a better correlation with $M_{\rm H2}$ than SFR (cite: 2022ApJ...929...92V), which support a reliability of this line luminosity as a molecular gas mass tracer, and also suggest that the $L_{\rm [CII]}$–SFR relation may arise from the combination of $L_{\rm [CII]}$–$M_{\rm H2}$ relation and $M_{\rm H2}$–SFR relation (cite: 2012ARA&A..50..531K). Hence, the \[C II\]-based $M_{\rm H2}$ and SFR$_{\rm [CII]}$ reported here are not necessarily independent.

The total \[C II\] line flux measured with a $6''.0$ diameter aperture is 6.6 Jy km s$^{-1}$, which translates to $L_{\rm [CII]}$, SFR$_{\rm [CII]}$, and $M_{\rm H2}$ of $6.3 \times 10^9~L_\odot$, 550 $M_\odot$ yr$^{-1}$, and $1.9 \times 10^{11}~M_\odot$, respectively. These values are among the highest ones found in $z > 6$ quasars of all UV luminosities (cite: 2010ApJ...714..699W; 2017ApJ...845..154V; 2022A&A...662A..60D), demonstrating the presence of active star formation and an immense gaseous reservoir. Note that (cite: 2022A&A...662A..60D) pointed out discrepancies between \[C II\]-based $M_{\rm H2}$ and CO-based, \[C I\]-based, and dust continuum-based $M_{\rm H2}$: \[C II\]-based values are systematically greater than the others by a factor of $\sim 3-5$. Even so, we claim that the total molecular gas mass of this pair is on the order of $10^{10}~M_\odot$, which is enough to sustain high SFR (e.g., 500 $M_\odot$ yr$^{-1}$) and luminous quasar activity (mass accretion rate $\sim 10~M_\odot$ yr$^{-1}$) expected to happen after a galaxy merger over $\sim 10^8$ yrs.

### From FIR continuum emission

The rest-FIR continuum emission mainly originates from the regions around C1 (Figure [1](#fig1)a). Our 2D Gaussian fit to the FIR continuum distribution using the CASA task `imfit` found a peak position of (RA, Dec) = (12$^{\rm h}$15$^{\rm m}$03$^{\rm s}$.426, $-$01$^\circ$48$'$58$''$.73), which agrees well with the optical coordinates of C1 (cite: Matsuoka2024). The beam-deconvolved size of this 2D Gaussian is $(1''.19 \pm 0''.14) \times (0''.54 \pm 0''.07)$ or (6.76 kpc $\pm$ 0.80 kpc) $\times$ (3.04 kpc $\pm$ 0.40 kpc), and the peak and area-integrated total flux densities are 220 $\pm$ 18 $\mu$Jy beam$^{-1}$ and 814 $\pm$ 84 $\mu$Jy, respectively. This high S/N is well above the threshold of 10 required to make a robust size measurement (cite: 2018ApJ...854...97D; 2018ApJ...866..159V). The tidal interaction between the host galaxies would have stretched the star-forming regions, and this intrinsic size is at the extreme of the FIR size distribution of $z \gtrsim 6$ quasars observed so far (cite: 2019PASJ...71..111I; 2020ApJ...904..130V).

From the measured continuum fluxes, we determined the FIR luminosity ($L_{\rm FIR}$; 42.5–122.5 $\ensuremath{\mu}m$) and the total IR luminosity ($L_{\rm TIR}$; 8–1000 $\ensuremath{\mu}m$) assuming an optically thin modified black-body spectrum and values of dust temperature ($T_{\rm dust}$) and emissivity index $\beta$. Note that previous studies on $z > 6$ luminous quasars with starburst (SFR $\gg 100~M_\odot$ yr$^{-1}$) nature have typically adopted canonical values of $T_{\rm dust} = 47$ K and $\beta = 1.6$, based on the averaged IR spectral energy distribution of high redshift optically-luminous quasars (cite: 2006ApJ...642..694B; 2013ApJ...772..103L). Recent ALMA Band 9 observations toward one of the most luminous quasars at $z > 6$, J0100$+$2802 at $z = 6.3$, revealed its $T_{\rm dust}$ as 48 K that is similar to the above value, although its $\beta$ is as high as 2.6 (cite: 2023ApJ...946L..45T).

However, it seems inappropriate to use such high $T_{\rm dust}$ for the galaxies likely in an earlier evolutionary phase, where AGN and star formation are both much less active than the averaged sample of, for example, (cite: 2006ApJ...642..694B). Hence, for the time being until we are constrained by multi-band observations, we assume $T_{\rm dust} = 35$ K, a typical value in local LIRGs (cite: 2012ApJS..203....9U). This value (35 K) is still within a range of $T_{\rm dust}$ observed in $z \sim 6$ main-sequence (normal) galaxies (cite: 2021MNRAS.508L..58B).

We also correct for the contrast and the additional heating effects of the cosmic microwave background (CMB) radiation (cite: 2013ApJ...766...13D) in Table [1](#tbl1). Dust mass is estimated by adopting a rest-frame mass absorption coefficient of $\kappa_\lambda = 0.77 ({\rm 850 \ensuremath{\mu}m}/\lambda)^\beta$ cm$^2$ g$^{-1}$ (cite: 2000MNRAS.315..115D). We emphasize that these results are sensitive to the assumed values of $T_{\rm dust}$ and $\beta$, which are known to be different in different sources (cite: 2013ApJ...772..103L; 2018ApJ...866..159V; 2019MNRAS.489.1397L) [^2]. The resultant value of $L_{\rm [CII]}/L_{\rm FIR}$, which is sensitive to the physical state of the ISM (cite: 2013ApJ...774...68D; 2018ApJ...861...95H), is $7.7 \times 10^{-3}$. This is a factor $\sim 2$ higher than the value for the Milky Way (cite: 2013ARA&A..51..105C), but still within the range of nearby LIRGs (cite: 2013ApJ...774...68D).

By assuming that the TIR continuum emission originates solely from star-forming regions, we estimate the SFR$_{\rm TIR}$ in Table [1](#tbl1) with the conversion ${\rm SFR_{TIR}} = 1.49 \times 10^{-10} L_{\rm TIR}/L_\odot$ (cite: 2011ApJ...737...67M). This conversion is based on the Kroupa initial mass function (cite: 2001MNRAS.322..231K), but is adjustable for different IMFs if necessary. Although some works on luminous quasars claim the existence of quasar-heated dust at rest-FIR wavelengths (cite: 2014ApJ...785..154L; 2021ApJ...914...36I; 2023MNRAS.523.4654T), that effect may not be significant for these low-luminosity quasars. We also found that there is a significant discrepancy between SFR$_{\rm [CII]}$ and SFR$_{\rm TIR}$ particularly at C2 + Bridge and the Tail. Although one possible explanation is that the actual $T_{\rm dust}$ is much higher than the adopted 35 K, it is also plausible that dust-unobscured star formation dominates the total SFR at least at C2 + Bridge and the Tail, and would contribute significantly at C1, as \[C II\] is sensitive to both obscured and unobscured star formation. Future multi-wavelength observations of the host galaxy-scale star formation, such as provided by JWST, will fully characterize the star forming activity of these host galaxies.

## Global gas dynamics

Figure [3](#fig3) shows an intensity-weighted mean \[C II\] velocity map (moment-1) generated with the CASA task `immoments` with $3.5\sigma$ clipping to avoid noisy pixels. As we already saw in the channel maps (Figure [2](#fig2)), there is a clear, *global* velocity gradient over the system, on scales of $\sim 4''$. Similar velocity gradients have also been observed in some quasars on a few kpc scales (cite: 2016ApJ...816...37V; 2018ApJ...854...97D; 2021ApJ...914...36I), as well as in PJ308$-$21 (cite: 2019ApJ...880..157D).

![](fig3.eps)

This global dynamics can be explained by the following steps of tidal disruption of a satellite galaxy (host galaxy of C2) in close interaction with the heavier host galaxy of C1 (Figure [3](#fig3)b). Note that our attempt here is to explain the global behavior in a qualitative manner, rather than to fit the data with a physical model. We also note that the actual gravitational center of the host galaxy of C2 remains unclear (§ [3.1](#sec3.1)). Future JWST observations will elucidate the mass distribution of the system and the dynamical nature more properly.

- Close encounter: Two galaxies hosting C1 and C2 start to encounter.

- Fly-by: The galaxies are passing by one another. Gaseous material starts to be expelled from the two galaxies due to tidal interaction, which will eventually form the Bridge structure between them, as well as extended structures at the opposite sides of the galaxies (i.e., Tail).

- Braking phase: This process happens due to the gravitational deceleration and energy dissipation of the two galaxies.

- The observed stage: Both of the Bride and the Tail are well developed due to the tidal force between the galaxies.

This situation is very similar to what has been observed in PJ308$-$21 (cite: 2019ApJ...880..157D), and this close interaction indicates that the two galaxies will merge into one in a short time.

The actual masses of the host galaxies of C1 and C2, and their ratio, are hard to estimate at this moment given the highly dynamic nature of the system. Nevertheless, we crudely estimate the dynamical mass ($M_{\rm dyn}$) of these host galaxies, by following the standard description in studies of $z > 6$ quasars (cite: 2016ApJ...816...37V; 2015ApJ...801..123W; 2018PASJ...70...36I). Here, the \[C II\] emission of these galaxies is assumed to be mainly originating from thin rotating disks. The inclination angles ($i$) of the disks are determined from the axis ratios of the beam-deconvolved Gaussian fits to the emitting regions. We used the CASA task `imfit` for this purpose, and found the beam deconvolved major ($a_{\rm maj}$) and minor ($a_{\rm min}$) axis sizes as $a_{\rm maj} \times a_{\rm min} = (0''.96 \pm 0''.09) \times (0''.68 \pm 0''.07)$ and $i = 45\ensuremath{^\circ}$ for C1, and $(0''.85 \pm 0''.26) \times (0''.35 \pm 0''.17)$ and $i = 66\ensuremath{^\circ}$ for C2 + Bridge regions, respectively. Although the latter was measured within a $1''$ box placed at the midpoint of C2 and the Bridge, we decided to use this to represent the host galaxy of C2, considering the spatial distribution of the \[C II\] emission around there. The disk size is approximated as $D = 1.5 \times a_{\rm maj}$ to account for spatially extended low-level emission, and the circular velocity as $V_{\rm circ} = 0.75 \times {\rm FWHM}_{\rm [CII]}/\sin i$, where FWHM$_{\rm [CII]}$ is the Gaussian FWHM of the \[C II\] line profile measured on the region (594 km s$^{-1}$ for C1 and 361 km s$^{-1}$ for C2 + Bridge). With these, we estimate that $M_{\rm dyn} \sim 9 \times 10^{10}~M_\odot$ for C1, and $\sim 5 \times 10^{10}~M_\odot$ for C2, respectively. Given these estimates, we found that their $M_{\rm dyn}$ are comparable to $M_{\rm H2}$, suggesting that this is a major merger system of gas-rich galaxies. The comparable $M_{\rm BH}$ of C1 and C2 (cite: Matsuoka2024) also supports this scenario.

## Potential indication of AGN feedback

Figure [4](#fig4)a shows the intensity-weighted \[C II\] velocity dispersion map made with the same CASA immoments task with $3.5\sigma$ clipping: if the line profile is purely Gaussian, this dispersion indicates the Gaussian sigma. Overall, the dispersion ranges from 50 to 100 km s$^{-1}$ over the system, which is comparable to nearby merging galaxies (cite: 2015ApJ...803...60S; 2018ApJ...863..143C). On the other hand, we found globally elevated dispersions around C1 ($\sim 100-150$ km s$^{-1}$), as well as linearly-distributed high dispersion regions from north-east to south-west across C1. We specified two representative positions along this line, marked with plus signs in Figure [4](#fig4)a, which are referred to as High Dispersion North-East (NE) and South-West (SW) in the following. As these regions are distributed roughly symmetrically to C1, and the regions of high dispersion are relatively localized, we speculate that this is a hint of two-directional (e.g., bi-conical) AGN-driven outflows, rather than violent shocks due to the merger of galaxies (cite: 2016ApJ...816L...6D; 2018Sci...362.1034D; 2020ApJ...890..149T).

We first inspected the \[C II\] line spectrum of C1 (Figure [4](#fig4)b), which was measured with a single synthesized beam. We first fit the spectrum with a single Gaussian model, which returned (peak amplitude, center, FWHM) = ($2.8 \pm 0.1$ mJy beam$^{-1}$, $269.313 \pm 0.005$ GHz, $447 \pm 12$ km s$^{-1}$). It is intriguing that there is excess emission from the single Gaussian up to $\pm 1000$ km s$^{-1}$, which is also seen in the high velocity components in the channel maps (Figure [2](#fig2)). Thus, we next fit the data with a double Gaussian model (Figure [4](#fig4)c) by fixing the centroid of the second Gaussian to that of the first Gaussian, and found that the narrow core component has (peak amplitude, center, FWHM) = ($2.5 \pm 0.3$ mJy beam$^{-1}$, $269.314 \pm 0.005$ GHz, $355 \pm 21$ km s$^{-1}$), and the broad wing component has (peak amplitude, center, FWHM) = ($0.48 \pm 0.11$ mJy beam$^{-1}$, 269.314 GHz (fixed), $1194 \pm 193$ km s$^{-1}$). The addition of this second broad Gaussian is assessed with the standard $\chi^2$ value: the single Gaussian fit returns $\chi^2$/d.o.f. = 85.5/56 = 1.53 whereas the double Gaussian fit returns $\chi^2$/d.o.f. = 42.7/54 = 0.79 when evaluated over the velocity range of $\pm 1500$ km s$^{-1}$. Hence, the double Gaussian fit is statistically preferred. Furthermore, we found that the line profiles measured at the high dispersion regions are unusually broad as well (FWHM = $928 \pm 72$ km s$^{-1}$ at NE, $602 \pm 75$ km s$^{-1}$ at SW), although it is well-fit by a single Gaussian profile (Figure [4](#fig4)d,e).

![](fig4.eps)

The nearly symmetric appearance of the broad wing at C1 disfavors nearby (unseen) companions as its physical origin: multiple companions at a range of velocity offsets would be required within this single synthesized beam. Hence we hereafter interpret this broad wing as a potential indication of fast \[C II\] outflows. We emphasize that such fast neutral outflows (including \[C II\] and OH 119 $\ensuremath{\mu}m$) in quasars have been observed in only a few cases at $z > 6$ (cite: 2021ApJ...914...36I; 2024ApJ...962....1S). Note that, however, further higher angular resolution, higher sensitivity observations are definitely required to confirm the presence of \[C II\] outflows.

Assuming that the wing has appeared due to outflows, we roughly estimate some basic physical properties. First, the line flux of the broad component at C1 ($0.61 \pm 0.17$ Jy beam$^{-1}$ km s$^{-1}$) corresponds to $L_{\rm [CII]} = (5.83 \pm 0.16) \times 10^8~L_\odot$. The outflowing atomic mass in neutral hydrogen gas (cite: 2010ApJ...714L.162H; 2020A&A...633A..90G) is $$\begin{equation}
\begin{split}
\frac{M_{\rm out}}{M_\odot} &= 0.77 \left( \frac{0.7 L_{\rm [CII],broad}}{L_\odot} \right) \left( \frac{1.4 \times 10^{-4}}{X_{\rm C^+}} \right) \\
& \times \frac{1 + 2e^{-91/T_{\rm ex}} + n_{\rm crit}/n}{2e^{-91/T_{\rm ex}}}, 
\end{split}
\end{equation}$$ where $X_{\rm C^+}$ is the ratio of C$^+$ abundance to H, $T_{\rm ex}$ is the gas excitation temperature in K, $n$ is the gas volume density in cm$^{-3}$, and $n_{\rm crit}$ is the critical density of the line ($\sim 3 \times 10^3$ cm$^{-3}$). We assumed that 70% of the \[C II\] emission originates from neutral photodissociation regions (cite: 1997ARA&A..35..179H). Following previous studies on \[C II\] outflows (cite: 2012MNRAS.425L..66M; 2020A&A...633A..90G; 2021ApJ...914...36I), we estimated $M_{\rm out} = (5.6 \pm 1.5) \times 10^8~M_\odot$ for $X_{\rm C^+} = 1.4 \times 10^{-4}$ and $T_{\rm ex} = 200$ K, in the high density limit ($n \gg n_{\rm crit}$). As the outflows may smoothly propagate from the quasar outward along the linear regions of high dispersion (Figure [4](#fig4)a), here we measure the values within the single synthesized beam placed at C1. This gives the characteristic size (spatial extent) of $R_{\rm out} = 1.5$ kpc. Assuming an outflow velocity of $V_{\rm out} = {\rm FWHM}/2 = 597 \pm 97$ km s$^{-1}$ which stays constant throughout the flow (cite: 2020A&A...633A.134L), we obtain a neutral outflow rate of $\dot{M}_{\rm out, neutral} = M_{\rm out}V_{\rm out}/R_{\rm out} = 229 \pm 73~M_\odot$ yr$^{-1}$. This is comparable to the SFR$_{\rm [CII]}$ measured at C1 (Table [1](#tbl1)).

(cite: 2019MNRAS.483.4586F) studied multiphase outflows in nearby star-forming galaxies and AGNs, and found that the total outflow rate $\dot{M}_{\rm out,total}$, including the cold molecular phase, is typically $3 \times$ greater than the atomic-only value. Following this, we speculate that the actual mass loading factor $\eta = \dot{M}_{\rm out,total}/{\rm SFR}$ (cite: 2020A&ARv..28....2V) would be $\gtrsim 2-3$ when we adopt the \[C II\]-based SFR at C1. This indicates that a significant quenching of star formation is happening, while the gas depletion time is still as long as $\sim 3 \times 10^8$ yr, as compared to $\sim 10^7$ yr scales found in other quasars (cite: 2024ApJ...962....1S), owing to the rich amount of cold gas in the system.

The driver of this feedback remains unclear as starburst-driven outflows typically show $\eta \sim 1-3$ (cite: 2014A&A...562A..21C; 2018MNRAS.473.1909G; 2020A&A...633A..90G) and AGN-driven outflows have $\eta \gtrsim 5$ (cite: 2014A&A...562A..21C; 2017A&A...601A.143F; 2019MNRAS.483.4586F): our resultant $\eta$ is thus intermediate. We note, however, it is rare at any redshift for starburst-driven outflows to reach $V_{\rm out} > 500$ km s$^{-1}$ (cite: 2005ApJ...621..227M; 2020A&A...633A..90G). Supposing the factor of 3 difference from the neutral outflow rate to the total outflow rate, we compute its kinetic energy as $\sim 2.6 \times 10^{43}$ erg s$^{-1}$. This is only 0.4% of the quasar bolometric luminosity of C1 (cite: Matsuoka2024), and is much smaller than the value expected in the blast energy-conserving AGN feedback frequently invoked in co-evolution scenario, even if it exists, to quench star formation of a host galaxy (cite: 2014MNRAS.444.2355C; 2015ARA&A..53..115K).

# Discussion and Summary

We have performed ALMA \[C II\] line and FIR continuum emission observations toward the $z = 6.05$ quasar-quasar pair recently discovered by our Subaru/HSC observations (cite: Matsuoka2024). These quasars are faint at rest-UV ($M_{\rm 1450} \gtrsim -23$ mag) with modest values of SMBH mass ($\sim 10^8~M_\odot$), but we detected very bright \[C II\] emission, demonstrating that the system is rich in gas. Indeed, we estimated the total H$_2$ mass of the system as $\sim 10^{11}~M_\odot$ (or at least on the order of $10^{10}~M_\odot$) from the \[C II\] luminosity. The masses of the host galaxies, crudely estimated from the \[C II\] spatial distributions and line widths, are on the same order, showing that the system is very gas-rich. The \[C II\]-based total SFR of the system is $\sim 550~M_\odot$ yr$^{-1}$ (dust-obscured SFR traced by the IR continuum emission is $\sim 100~M_\odot$ yr$^{-1}$). The large amount of gas sustains this high star-forming activity, which is most likely triggered by the galaxy-galaxy interaction.

Recent simulations predict an increase in the fraction of SMBH-SMBH pairs with increasing redshift due to higher rates of galaxy-galaxy mergers (cite: 2016MNRAS.460.2979V; 2022MNRAS.514..640V; 2019NewAR..8601525D). ALMA observations of $z \gtrsim 5$ quasars have revealed the presence of companion galaxies (separation $\lesssim 50$ kpc) around up to 30–50% of the systems (cite: 2017Natur.545..457D; 2017ApJ...836....8T; 2017ApJ...850..108W; 2019ApJ...882...10N; 2020ApJ...895...74N). Recent JWST observations have started to reveal close companion galaxies or mergers in many high-$z$ quasars, which were overlooked in previous works due to insufficient resolutions (cite: 2023A&A...678A.191M; 2023A&A...679A..89P). These works demonstrate the importance of mergers of galaxies as the triggering mechanism of luminous quasars at high redshift. These are also in line with the recent hydrodynamic simulations that predict $z \sim 6$ quasars are a part of complex, gas- and dust-rich merging systems containing multiple sources (cite: 2021MNRAS.503.2349D; 2022MNRAS.514.1672V).

However, while some JWST observations have also uncovered dual AGNs (i.e., mergers) in lower luminosity ($L_{\rm Bol} \lesssim 10^{45}$ erg s$^{-1}$) and lower BH mass ($M_{\rm BH} \lesssim 10^7~M_\odot$) populations (cite: 2023ApJ...959...39H; 2023arXiv230801230M; 2023arXiv231203589U), previous works on massive BH pairs with $M_{\rm BH} \gtrsim 10^8~M_\odot$ were solely performed for luminous quasars with $M_{\rm 1450} \lesssim -26$ mag. Our observations now probe a much lower luminosity pair of quasars ($M_{\rm 1450} \gtrsim -23$ mag), which can serve as a benchmark of this unexplored regime of low-luminosity, but massive BH of $\sim 10^8~M_\odot$. It is interesting that AGN feedback might be happening already in this early stage (§ [3.4](#sec3.4)), although its impact on the host galaxy would yet be small. Hence, powerful AGN feedback typically invoked in galaxy evolution models, if exists, will happen at later evolutionary phases (i.e., coalescent phase or UV-bright quasar phase).

According to models of merger-driven galaxy evolution (cite: 1988ApJ...325...74S; 2005Natur.433..604D; 2006ApJS..163....1H; 2019MNRAS.488.4004L), both star formation and AGN are activated by the interaction of gas-rich galaxies. But the activity is further boosted by factors of 10–100 when the actual coalescence/merger happens (cite: 2008ApJS..175..356H; 2022ApJ...936..118Y). Thus, we expect that this pair will evolve to a luminous quasar ($M_{\rm 1450} \lesssim -26$ mag) with high SFR of $> 1000~M_\odot$ yr$^{-1}$, comparable to the value for optically luminous (i.e., SDSS-class) quasars observed so far at high redshifts (cite: 2018ApJ...866..159V; 2021A&A...645A..33B). Such evolution can be sustained by the rich amount of ISM available in this system (Table [1](#tbl1)). That is, this pair system may well correspond to a progenitor of the most luminous quasars in the early universe. Future multiwavelength observations, including JWST measurements of the stellar mass distribution and ionized outflows (cite: 2023A&A...678A.191M; 2023Natur.621...51D), aided with dedicated hydrodynamic simulations, will characterize the nature of this system, and allow us to predict its fate in greater detail.

We appreciate the anonymous reviewer’s very constructive comments to improve this manuscript. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.A.00019.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. We appreciate the ALMA Director for granting the observing time for the DDT program presented here.

T.I., Y.M., Y.T., M.I., H.U., K.K. are supported by Japan Society for the Promotion of Science (JSPS) KAKENHI Grant Number JP23K03462, JP21H04494, JP23K22537, JP21K03632, \[JP20H01953, JP22KK0231, JP23K20240\], and \[JP17H06130, JP22H04939, JP23K20035\], respectively. K.I. acknowledges support under the grant PID2022-136827NB-C44 provided by MCIN/AEI/10.13039/501100011033 / FEDER, UE. T.I. is supported by the ALMA Japan Research Grant for the NAOJ ALMA Project, NAOJ-ALMA-319.

# \[C II\] line spectra

The \[C II\] line spectra measured at the positions of C1, C2, Bridge, Tail (see Figure [1](#fig1)), as well as that of C2 + Bridge, are presented in Figure [5](#fig_App1). Results of our single Gaussian fits to these spectra are summarized in Table [1](#tbl1).

![](fig_App1.eps)

# Smoothed velocity channel maps

![](fig_App2.eps)

natexlab

(ref: 2012A&A...537A..44A) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, A&A, 537, A44, doi: [`10.1051/0004-6361/201117919`](http://doi.org/10.1051/0004-6361/201117919)

(ref: 2018PASJ...70S...8A) Aihara, H., Armstrong, R., Bickerton, S., et al. 2018, PASJ, 70, S8, doi: [`10.1093/pasj/psx081`](http://doi.org/10.1093/pasj/psx081)

(ref: 2016ApJS..227...11B) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11, doi: [`10.3847/0067-0049/227/1/11`](http://doi.org/10.3847/0067-0049/227/1/11)

(ref: 2021MNRAS.508L..58B) Bakx, T. J. L. C., Sommovigo, L., Carniani, S., et al. 2021, MNRAS, 508, L58, doi: [`10.1093/mnrasl/slab104`](http://doi.org/10.1093/mnrasl/slab104)

(ref: 2006ApJ...642..694B) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694, doi: [`10.1086/500636`](http://doi.org/10.1086/500636)

(ref: 2019A&A...630A..59B) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59, doi: [`10.1051/0004-6361/201833557`](http://doi.org/10.1051/0004-6361/201833557)

(ref: 2021A&A...645A..33B) Bischetti, M., Feruglio, C., Piconcelli, E., et al. 2021, A&A, 645, A33, doi: [`10.1051/0004-6361/202039057`](http://doi.org/10.1051/0004-6361/202039057)

(ref: 2013ARA&A..51..105C) Carilli, C. L., & Walter, F. 2013, ARA&A, 51, 105, doi: [`10.1146/annurev-astro-082812-140953`](http://doi.org/10.1146/annurev-astro-082812-140953)

(ref: 2023Natur.619..716C) Carnall, A. C., McLure, R. J., Dunlop, J. S., et al. 2023, Nature, 619, 716, doi: [`10.1038/s41586-023-06158-6`](http://doi.org/10.1038/s41586-023-06158-6)

(ref: 2022PASP..134k4501C) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: 2020A&A...643A...6C) Cassata, P., Morselli, L., Faisst, A., et al. 2020, A&A, 643, A6, doi: [`10.1051/0004-6361/202037517`](http://doi.org/10.1051/0004-6361/202037517)

(ref: 2014A&A...562A..21C) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21, doi: [`10.1051/0004-6361/201322464`](http://doi.org/10.1051/0004-6361/201322464)

(ref: 2018ApJ...863..143C) Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018, ApJ, 863, 143, doi: [`10.3847/1538-4357/aad32a`](http://doi.org/10.3847/1538-4357/aad32a)

(ref: 2014MNRAS.444.2355C) Costa, T., Sijacki, D., & Haehnelt, M. G. 2014, MNRAS, 444, 2355, doi: [`10.1093/mnras/stu1632`](http://doi.org/10.1093/mnras/stu1632)

(ref: 2013ApJ...766...13D) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13, doi: [`10.1088/0004-637X/766/1/13`](http://doi.org/10.1088/0004-637X/766/1/13)

(ref: 2014A&A...568A..62D) De Looze, I., Cormier, D., Lebouteiller, V., et al. 2014, A&A, 568, A62, doi: [`10.1051/0004-6361/201322489`](http://doi.org/10.1051/0004-6361/201322489)

(ref: 2019NewAR..8601525D) De Rosa, A., Vignali, C., Bogdanović, T., et al. 2019, New A Rev., 86, 101525, doi: [`10.1016/j.newar.2020.101525`](http://doi.org/10.1016/j.newar.2020.101525)

(ref: 2017Natur.545..457D) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457, doi: [`10.1038/nature22358`](http://doi.org/10.1038/nature22358)

(ref: 2018ApJ...854...97D) —. 2018, ApJ, 854, 97, doi: [`10.3847/1538-4357/aaa5aa`](http://doi.org/10.3847/1538-4357/aaa5aa)

(ref: 2019ApJ...880..157D) Decarli, R., Dotti, M., Bañados, E., et al. 2019, ApJ, 880, 157, doi: [`10.3847/1538-4357/ab297f`](http://doi.org/10.3847/1538-4357/ab297f)

(ref: 2022A&A...662A..60D) Decarli, R., Pensabene, A., Venemans, B., et al. 2022, A&A, 662, A60, doi: [`10.1051/0004-6361/202142871`](http://doi.org/10.1051/0004-6361/202142871)

(ref: 2021MNRAS.503.2349D) Di Mascia, F., Gallerani, S., Behrens, C., et al. 2021, MNRAS, 503, 2349, doi: [`10.1093/mnras/stab528`](http://doi.org/10.1093/mnras/stab528)

(ref: 2005Natur.433..604D) Di Matteo, T., Springel, V., & Hernquist, L. 2005, Nature, 433, 604, doi: [`10.1038/nature03335`](http://doi.org/10.1038/nature03335)

(ref: 2013ApJ...774...68D) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68, doi: [`10.1088/0004-637X/774/1/68`](http://doi.org/10.1088/0004-637X/774/1/68)

(ref: 2016ApJ...816L...6D) Dı́az-Santos, T., Assef, R. J., Blain, A. W., et al. 2016, ApJL, 816, L6, doi: [`10.3847/2041-8205/816/1/L6`](http://doi.org/10.3847/2041-8205/816/1/L6)

(ref: 2018Sci...362.1034D) —. 2018, Science, 362, 1034, doi: [`10.1126/science.aap7605`](http://doi.org/10.1126/science.aap7605)

(ref: 2023Natur.621...51D) Ding, X., Onoue, M., Silverman, J. D., et al. 2023, Nature, 621, 51, doi: [`10.1038/s41586-023-06345-5`](http://doi.org/10.1038/s41586-023-06345-5)

(ref: 2000MNRAS.315..115D) Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115, doi: [`10.1046/j.1365-8711.2000.03386.x`](http://doi.org/10.1046/j.1365-8711.2000.03386.x)

(ref: 2023ARA&A..61..373F) Fan, X., Bañados, E., & Simcoe, R. A. 2023, ARA&A, 61, 373, doi: [`10.1146/annurev-astro-052920-102455`](http://doi.org/10.1146/annurev-astro-052920-102455)

(ref: 2017A&A...601A.143F) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143, doi: [`10.1051/0004-6361/201629478`](http://doi.org/10.1051/0004-6361/201629478)

(ref: 2019MNRAS.483.4586F) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586, doi: [`10.1093/mnras/sty3449`](http://doi.org/10.1093/mnras/sty3449)

(ref: 2022Natur.604..261F) Fujimoto, S., Brammer, G. B., Watson, D., et al. 2022, Nature, 604, 261, doi: [`10.1038/s41586-022-04454-1`](http://doi.org/10.1038/s41586-022-04454-1)

(ref: 2018MNRAS.473.1909G) Gallerani, S., Pallottini, A., Feruglio, C., et al. 2018, MNRAS, 473, 1909, doi: [`10.1093/mnras/stx2458`](http://doi.org/10.1093/mnras/stx2458)

(ref: 2020A&A...633A..90G) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020, A&A, 633, A90, doi: [`10.1051/0004-6361/201936872`](http://doi.org/10.1051/0004-6361/201936872)

(ref: 2018PASJ...70S..37G) Goulding, A. D., Greene, J. E., Bezanson, R., et al. 2018, PASJ, 70, S37, doi: [`10.1093/pasj/psx135`](http://doi.org/10.1093/pasj/psx135)

(ref: 2010ApJ...714L.162H) Hailey-Dunsheath, S., Nikola, T., Stacey, G. J., et al. 2010, ApJL, 714, L162, doi: [`10.1088/2041-8205/714/1/L162`](http://doi.org/10.1088/2041-8205/714/1/L162)

(ref: 2022ApJS..259...20H) Harikane, Y., Ono, Y., Ouchi, M., et al. 2022, ApJS, 259, 20, doi: [`10.3847/1538-4365/ac3dfc`](http://doi.org/10.3847/1538-4365/ac3dfc)

(ref: 2023ApJ...959...39H) Harikane, Y., Zhang, Y., Nakajima, K., et al. 2023, ApJ, 959, 39, doi: [`10.3847/1538-4357/ad029e`](http://doi.org/10.3847/1538-4357/ad029e)

(ref: 2018ApJ...861...95H) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 95, doi: [`10.3847/1538-4357/aac0f9`](http://doi.org/10.3847/1538-4357/aac0f9)

(ref: 1997ARA&A..35..179H) Hollenbach, D. J., & Tielens, A. G. G. M. 1997, ARA&A, 35, 179, doi: [`10.1146/annurev.astro.35.1.179`](http://doi.org/10.1146/annurev.astro.35.1.179)

(ref: 2006ApJS..163....1H) Hopkins, P. F., Hernquist, L., Cox, T. J., et al. 2006, ApJS, 163, 1, doi: [`10.1086/499298`](http://doi.org/10.1086/499298)

(ref: 2008ApJS..175..356H) Hopkins, P. F., Hernquist, L., Cox, T. J., & Kereš, D. 2008, ApJS, 175, 356, doi: [`10.1086/524362`](http://doi.org/10.1086/524362)

(ref: 2020ARA&A..58...27I) Inayoshi, K., Visbal, E., & Haiman, Z. 2020, ARA&A, 58, 27, doi: [`10.1146/annurev-astro-120419-014455`](http://doi.org/10.1146/annurev-astro-120419-014455)

(ref: 2018PASJ...70...36I) Izumi, T., Onoue, M., Shirakata, H., et al. 2018, PASJ, 70, 36, doi: [`10.1093/pasj/psy026`](http://doi.org/10.1093/pasj/psy026)

(ref: 2019PASJ...71..111I) Izumi, T., Onoue, M., Matsuoka, Y., et al. 2019, PASJ, 71, 111, doi: [`10.1093/pasj/psz096`](http://doi.org/10.1093/pasj/psz096)

(ref: 2021ApJ...908..235I) —. 2021a, ApJ, 908, 235, doi: [`10.3847/1538-4357/abd7ef`](http://doi.org/10.3847/1538-4357/abd7ef)

(ref: 2021ApJ...914...36I) Izumi, T., Matsuoka, Y., Fujimoto, S., et al. 2021b, ApJ, 914, 36, doi: [`10.3847/1538-4357/abf6dc`](http://doi.org/10.3847/1538-4357/abf6dc)

(ref: 2016ApJ...833..222J) Jiang, L., McGreer, I. D., Fan, X., et al. 2016, ApJ, 833, 222, doi: [`10.3847/1538-4357/833/2/222`](http://doi.org/10.3847/1538-4357/833/2/222)

(ref: 2012ARA&A..50..531K) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: 2015ARA&A..53..115K) King, A., & Pounds, K. 2015, ARA&A, 53, 115, doi: [`10.1146/annurev-astro-082214-122316`](http://doi.org/10.1146/annurev-astro-082214-122316)

(ref: 2013ARA&A..51..511K) Kormendy, J., & Ho, L. C. 2013, ARA&A, 51, 511, doi: [`10.1146/annurev-astro-082708-101811`](http://doi.org/10.1146/annurev-astro-082708-101811)

(ref: 2018Natur.563..214K) Koss, M. J., Blecha, L., Bernhard, P., et al. 2018, Nature, 563, 214, doi: [`10.1038/s41586-018-0652-7`](http://doi.org/10.1038/s41586-018-0652-7)

(ref: 2001MNRAS.322..231K) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: 2020A&A...643A...1L) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1, doi: [`10.1051/0004-6361/201936965`](http://doi.org/10.1051/0004-6361/201936965)

(ref: 2013ApJ...772..103L) Leipski, C., Meisenheimer, K., Walter, F., et al. 2013, ApJ, 772, 103, doi: [`10.1088/0004-637X/772/2/103`](http://doi.org/10.1088/0004-637X/772/2/103)

(ref: 2014ApJ...785..154L) —. 2014, ApJ, 785, 154, doi: [`10.1088/0004-637X/785/2/154`](http://doi.org/10.1088/0004-637X/785/2/154)

(ref: 2019MNRAS.489.1397L) Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397, doi: [`10.1093/mnras/stz2134`](http://doi.org/10.1093/mnras/stz2134)

(ref: 2024arXiv240213319L) Loiacono, F., Decarli, R., Mignoli, M., et al. 2024, arXiv e-prints, arXiv:2402.13319, doi: [`10.48550/arXiv.2402.13319`](http://doi.org/10.48550/arXiv.2402.13319)

(ref: 2019MNRAS.488.4004L) Lupi, A., Volonteri, M., Decarli, R., et al. 2019, MNRAS, 488, 4004, doi: [`10.1093/mnras/stz1959`](http://doi.org/10.1093/mnras/stz1959)

(ref: 2020A&A...633A.134L) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134, doi: [`10.1051/0004-6361/201936803`](http://doi.org/10.1051/0004-6361/201936803)

(ref: 2014ARA&A..52..415M) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: 2020A&A...643A.141M) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141, doi: [`10.1051/0004-6361/202038860`](http://doi.org/10.1051/0004-6361/202038860)

(ref: 2012MNRAS.425L..66M) Maiolino, R., Gallerani, S., Neri, R., et al. 2012, MNRAS, 425, L66, doi: [`10.1111/j.1745-3933.2012.01303.x`](http://doi.org/10.1111/j.1745-3933.2012.01303.x)

(ref: 2023arXiv230801230M) Maiolino, R., Scholtz, J., Curtis-Lake, E., et al. 2023, arXiv e-prints, arXiv:2308.01230, doi: [`10.48550/arXiv.2308.01230`](http://doi.org/10.48550/arXiv.2308.01230)

(ref: 2018Natur.553...51M) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, Nature, 553, 51, doi: [`10.1038/nature24629`](http://doi.org/10.1038/nature24629)

(ref: 2023A&A...678A.191M) Marshall, M. A., Perna, M., Willott, C. J., et al. 2023, A&A, 678, A191, doi: [`10.1051/0004-6361/202346113`](http://doi.org/10.1051/0004-6361/202346113)

(ref: 2005ApJ...621..227M) Martin, C. L. 2005, ApJ, 621, 227, doi: [`10.1086/427277`](http://doi.org/10.1086/427277)

(ref: 2016ApJ...828...26M) Matsuoka, Y., Onoue, M., Kashikawa, N., et al. 2016, ApJ, 828, 26, doi: [`10.3847/0004-637X/828/1/26`](http://doi.org/10.3847/0004-637X/828/1/26)

(ref: 2018PASJ...70S..35M) —. 2018a, PASJ, 70, S35, doi: [`10.1093/pasj/psx046`](http://doi.org/10.1093/pasj/psx046)

(ref: 2018ApJS..237....5M) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2018b, ApJS, 237, 5, doi: [`10.3847/1538-4365/aac724`](http://doi.org/10.3847/1538-4365/aac724)

(ref: 2018ApJ...869..150M) Matsuoka, Y., Strauss, M. A., Kashikawa, N., et al. 2018c, ApJ, 869, 150, doi: [`10.3847/1538-4357/aaee7a`](http://doi.org/10.3847/1538-4357/aaee7a)

(ref: 2019ApJ...883..183M) Matsuoka, Y., Iwasawa, K., Onoue, M., et al. 2019, ApJ, 883, 183, doi: [`10.3847/1538-4357/ab3c60`](http://doi.org/10.3847/1538-4357/ab3c60)

(ref: 2022ApJS..259...18M) —. 2022, ApJS, 259, 18, doi: [`10.3847/1538-4365/ac3d31`](http://doi.org/10.3847/1538-4365/ac3d31)

(ref: Matsuoka2024) Matsuoka, Y., Izumi, T., Onoue, M., et al. 2024, ApJL, 965, L4, doi: [`10.3847/2041-8213/ad35c7`](http://doi.org/10.3847/2041-8213/ad35c7)

(ref: 2007ASPC..376..127M) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: 2011ApJ...737...67M) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: 2019ApJ...882...10N) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10, doi: [`10.3847/1538-4357/ab2ed3`](http://doi.org/10.3847/1538-4357/ab2ed3)

(ref: 2008A&A...491..407N) Nesvadba, N. P. H., Lehnert, M. D., De Breuck, C., Gilbert, A. M., & van Breugel, W. 2008, A&A, 491, 407, doi: [`10.1051/0004-6361:200810346`](http://doi.org/10.1051/0004-6361:200810346)

(ref: 2020ApJ...895...74N) Nguyen, N. H., Lira, P., Trakhtenbrot, B., et al. 2020, ApJ, 895, 74, doi: [`10.3847/1538-4357/ab8bd3`](http://doi.org/10.3847/1538-4357/ab8bd3)

(ref: 2020ApJ...904..131N) Novak, M., Venemans, B. P., Walter, F., et al. 2020, ApJ, 904, 131, doi: [`10.3847/1538-4357/abc33f`](http://doi.org/10.3847/1538-4357/abc33f)

(ref: 2023A&A...679A..89P) Perna, M., Arribas, S., Marshall, M., et al. 2023, A&A, 679, A89, doi: [`10.1051/0004-6361/202346649`](http://doi.org/10.1051/0004-6361/202346649)

(ref: 2013Natur.496..329R) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329, doi: [`10.1038/nature12050`](http://doi.org/10.1038/nature12050)

(ref: 2015ApJ...803...60S) Saito, T., Iono, D., Yun, M. S., et al. 2015, ApJ, 803, 60, doi: [`10.1088/0004-637X/803/2/60`](http://doi.org/10.1088/0004-637X/803/2/60)

(ref: 2024ApJ...962....1S) Salak, D., Hashimoto, T., Inoue, A. K., et al. 2024, ApJ, 962, 1, doi: [`10.3847/1538-4357/ad0df5`](http://doi.org/10.3847/1538-4357/ad0df5)

(ref: 1988ApJ...325...74S) Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325, 74, doi: [`10.1086/165983`](http://doi.org/10.1086/165983)

(ref: 1995ASPC...77..433S) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433

(ref: 2020A&A...643A...3S) Schaerer, D., Ginolfi, M., Béthermin, M., et al. 2020, A&A, 643, A3, doi: [`10.1051/0004-6361/202037617`](http://doi.org/10.1051/0004-6361/202037617)

(ref: 2011ApJ...743....2S) Silverman, J. D., Kampczyk, P., Jahnke, K., et al. 2011, ApJ, 743, 2, doi: [`10.1088/0004-637X/743/1/2`](http://doi.org/10.1088/0004-637X/743/1/2)

(ref: 2005ARA&A..43..677S) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: 2024ApJ...960..112T) Takahashi, A., Matsuoka, Y., Onoue, M., et al. 2024, ApJ, 960, 112, doi: [`10.3847/1538-4357/ad045e`](http://doi.org/10.3847/1538-4357/ad045e)

(ref: 2017ApJ...836....8T) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8, doi: [`10.3847/1538-4357/836/1/8`](http://doi.org/10.3847/1538-4357/836/1/8)

(ref: 2020ApJ...890..149T) Treister, E., Messias, H., Privon, G. C., et al. 2020, ApJ, 890, 149, doi: [`10.3847/1538-4357/ab6b28`](http://doi.org/10.3847/1538-4357/ab6b28)

(ref: 2023ApJ...946L..45T) Tripodi, R., Feruglio, C., Kemper, F., et al. 2023, ApJL, 946, L45, doi: [`10.3847/2041-8213/acc58d`](http://doi.org/10.3847/2041-8213/acc58d)

(ref: 2023MNRAS.523.4654T) Tsukui, T., Wisnioski, E., Krumholz, M. R., & Battisti, A. 2023, MNRAS, 523, 4654, doi: [`10.1093/mnras/stad1464`](http://doi.org/10.1093/mnras/stad1464)

(ref: 2012ApJS..203....9U) U, V., Sanders, D. B., Mazzarella, J. M., et al. 2012, ApJS, 203, 9, doi: [`10.1088/0067-0049/203/1/9`](http://doi.org/10.1088/0067-0049/203/1/9)

(ref: 2023arXiv231203589U) Übler, H., Maiolino, R., Pérez-González, P. G., et al. 2023, arXiv e-prints, arXiv:2312.03589, doi: [`10.48550/arXiv.2312.03589`](http://doi.org/10.48550/arXiv.2312.03589)

(ref: 2023ApJ...947...20V) Valentino, F., Brammer, G., Gould, K. M. L., et al. 2023, ApJ, 947, 20, doi: [`10.3847/1538-4357/acbefa`](http://doi.org/10.3847/1538-4357/acbefa)

(ref: 2020A&ARv..28....2V) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2, doi: [`10.1007/s00159-019-0121-9`](http://doi.org/10.1007/s00159-019-0121-9)

(ref: 2016ApJ...816...37V) Venemans, B. P., Walter, F., Zschaechner, L., et al. 2016, ApJ, 816, 37, doi: [`10.3847/0004-637X/816/1/37`](http://doi.org/10.3847/0004-637X/816/1/37)

(ref: 2017ApJ...845..154V) Venemans, B. P., Walter, F., Decarli, R., et al. 2017, ApJ, 845, 154, doi: [`10.3847/1538-4357/aa81cb`](http://doi.org/10.3847/1538-4357/aa81cb)

(ref: 2018ApJ...866..159V) Venemans, B. P., Decarli, R., Walter, F., et al. 2018, ApJ, 866, 159, doi: [`10.3847/1538-4357/aadf35`](http://doi.org/10.3847/1538-4357/aadf35)

(ref: 2020ApJ...904..130V) Venemans, B. P., Walter, F., Neeleman, M., et al. 2020, ApJ, 904, 130, doi: [`10.3847/1538-4357/abc563`](http://doi.org/10.3847/1538-4357/abc563)

(ref: 2022MNRAS.514.1672V) Vito, F., Di Mascia, F., Gallerani, S., et al. 2022, MNRAS, 514, 1672, doi: [`10.1093/mnras/stac1422`](http://doi.org/10.1093/mnras/stac1422)

(ref: 2022ApJ...929...92V) Vizgan, D., Greve, T. R., Olsen, K. P., et al. 2022, ApJ, 929, 92, doi: [`10.3847/1538-4357/ac5cba`](http://doi.org/10.3847/1538-4357/ac5cba)

(ref: 2016MNRAS.460.2979V) Volonteri, M., Dubois, Y., Pichon, C., & Devriendt, J. 2016, MNRAS, 460, 2979, doi: [`10.1093/mnras/stw1123`](http://doi.org/10.1093/mnras/stw1123)

(ref: 2022MNRAS.514..640V) Volonteri, M., Pfister, H., Beckmann, R., et al. 2022, MNRAS, 514, 640, doi: [`10.1093/mnras/stac1217`](http://doi.org/10.1093/mnras/stac1217)

(ref: 2010ApJ...714..699W) Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714, 699, doi: [`10.1088/0004-637X/714/1/699`](http://doi.org/10.1088/0004-637X/714/1/699)

(ref: 2013ApJ...773...44W) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44, doi: [`10.1088/0004-637X/773/1/44`](http://doi.org/10.1088/0004-637X/773/1/44)

(ref: 2015ApJ...801..123W) Willott, C. J., Bergeron, J., & Omont, A. 2015, ApJ, 801, 123, doi: [`10.1088/0004-637X/801/2/123`](http://doi.org/10.1088/0004-637X/801/2/123)

(ref: 2017ApJ...850..108W) —. 2017, ApJ, 850, 108, doi: [`10.3847/1538-4357/aa921b`](http://doi.org/10.3847/1538-4357/aa921b)

(ref: 2022ARA&A..60..247W) Wolfire, M. G., Vallini, L., & Chevance, M. 2022, ARA&A, 60, 247, doi: [`10.1146/annurev-astro-052920-010254`](http://doi.org/10.1146/annurev-astro-052920-010254)

(ref: 2023ApJ...951L...5Y) Yang, J., Wang, F., Fan, X., et al. 2023, ApJL, 951, L5, doi: [`10.3847/2041-8213/acc9c8`](http://doi.org/10.3847/2041-8213/acc9c8)

(ref: 2021ApJ...921L..27Y) Yue, M., Fan, X., Yang, J., & Wang, F. 2021, ApJL, 921, L27, doi: [`10.3847/2041-8213/ac31a9`](http://doi.org/10.3847/2041-8213/ac31a9)

(ref: 2023AJ....165..191Y) —. 2023a, AJ, 165, 191, doi: [`10.3847/1538-3881/acc2be`](http://doi.org/10.3847/1538-3881/acc2be)

(ref: 2023arXiv230904614Y) Yue, M., Eilers, A.-C., Simcoe, R. A., et al. 2023b, arXiv e-prints, arXiv:2309.04614, doi: [`10.48550/arXiv.2309.04614`](http://doi.org/10.48550/arXiv.2309.04614)

(ref: 2022ApJ...936..118Y) Yutani, N., Toba, Y., Baba, S., & Wada, K. 2022, ApJ, 936, 118, doi: [`10.3847/1538-4357/ac87a2`](http://doi.org/10.3847/1538-4357/ac87a2)

(ref: 2018MNRAS.481.1976Z) Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976, doi: [`10.1093/mnras/sty2394`](http://doi.org/10.1093/mnras/sty2394)

(ref: 2018NatAs...2...56Z) Zavala, J. A., Montaña, A., Hughes, D. H., et al. 2018, Nature Astronomy, 2, 56, doi: [`10.1038/s41550-017-0297-8`](http://doi.org/10.1038/s41550-017-0297-8)

[^1]: The \[C II\] redshifts of C1 and C2 have been slightly updated from the values we reported in (cite: Matsuoka2024).

[^2]: For example, if we adopt $T_{\rm dust} = 47$ K, the resultant $L_{\rm TIR}$ and SFR will become $\sim 2.5\times$ higher than the values in Table [1](#tbl1).

</paper>

Write the methods card for this paper.