# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...988..109H\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...988..109H",
 "title": "Comprehensive Radio Monitoring of the Black Hole X-Ray Binary Swift J1727.8−1613 during Its 2023─2024 Outburst",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Hughes, Andrew K.",
 "n_authors": 42,
 "arxiv_id": "2506.07798",
 "doi": "10.3847/1538-4357/ade2e6",
 "alma_projects_linked_by_archive": [
  "2022.1.01182.T"
 ]
}
```

Paper text:
<paper>
# Comprehensive Radio Monitoring of the Black Hole X-ray Binary Swift J1727.8$-$1613 during its 2023–2024 Outburst

## Abstract

This work presents comprehensive multi-frequency radio monitoring of the black hole low-mass X-ray binary Swift J1727.8$-$1613, which underwent its first recorded outburst after its discovery in August 2023. Through a considerable community effort, we have coalesced the data from multiple, distinct observing programs; the light curves include ${\sim}\,10$ months and 197 epochs of monitoring from 7 radio facilities with observing frequencies ranging from (approximately) 0.3–230 GHz. The primary purpose of this work is to provide the broader astronomical community with these light curves to assist with the interpretation of other observing campaigns, particularly non-radio observing frequencies. We discuss the phenomenological evolution of the source, which included: (i) multiple radio flares consistent with the launching of discrete jet ejections, the brightest of which reached $\sim$ 1 Jy; (ii) temporally evolving radio spectral indices ($\alpha$), reaching values steeper than expected for optically-thin synchrotron emission ($\alpha\,{<}\,-1$) and emission with significant radiative cooling ($\alpha\,{<}\,-1.5$). We have published a digital copy of the data and intend for this work to set a precedent for the community to continue releasing comprehensive radio light curves of future low-mass X-ray binary outbursts.

# Introduction

Astrophysical jets are highly collimated outflows that are produced by nearly all accreting compact objects (cite: livio2002; kumar2015; ruiz2021; Fender2019sscyg; DeColle2020; Gottlieb2023). Given their ubiquity, interactions between the matter accelerated by jets and the ambient environment (i.e., ‘feedback’) have played and continue to play a critical role in driving local evolution on even the largest of scales (cite: Hardcastle2020). Therefore, understanding jets is crucial for understanding the Universe as a whole. For time-domain studies, an archetypal jet ‘laboratory’ is the black hole low-mass X-ray binary (BH LMXB).

Black hole low-mass X-ray binaries are interacting binaries composed of a stellar-mass black hole (${\sim}\,10{\rm\,M_\odot}$) accreting material from a low-mass (${\lesssim}\,1{\rm\,M_\odot}$) companion star. Many BH LMXBs are transient in nature, spending the majority of their lifetimes accreting small amounts of matter in a quiescent low-luminosity state (cite: Plotkin2013QS). These objects may also sporadically enter into bright outbursts where their broadband emission brightens considerably. During the week-to-years-long outbursts (cite: btetarenko2016; BlackCAT), the accretion flow (cite: Tananbaum1972; Belloni1999) and jets (cite: Tananbaum1972; corbel2002; russel2013; atetarenko2017) evolve significantly as the system transitions through different empirically defined ‘accretion states’ (cite: fender2004; mclintock2006; belloni2010).

A typical outburst begins with a rapid increase in the X-ray luminosity and a transition (from quiescence) into the *hard state* ($10^{35}\,{\lesssim}\,L_X\,{\lesssim}\,10^{39}{\rm\,erg\,s^{-1}}$). In the hard state, the X-ray spectrum is non-thermal, with the X-rays being dominated by high energy emission (i.e., ‘hard’ X-rays) due to Compton up-scattering of seed photons by an optically thin coronal flow (cite: Thorne1975; Shapiro1976). As the accretion rate increases, the source transitions through intermediate states: first, the *hard intermediate state* followed by the *soft intermediate state*, during which the X-ray emission becomes progressively softer (i.e., more dominated by lower energy ‘soft’ disc photons). Eventually, the system enters the *soft state*, with a spectrum dominated by thermal emission from an optically thick, geometrically thin accretion disc. A BH LMXB typically remains in the soft state for weeks to months, decreasing in X-ray luminosity before transitioning back to the hard state through lower-luminosity intermediate states and finally returning to quiescence. (cite: Jhoman2005; mclintock2006; belloni2010; ingram2019; Kalemci2022review).

The properties of relativistic jets evolve with the accretion states (cite: fender2004; fender2009; fender2010). In the hard state, a continuously accelerated jet is launched (henceforth the ‘compact jet’), typically described with the stratified, conical outflow model of (cite: blandfordkonigl1979). Compact jets exhibit an optically thick, partially self-absorbed synchrotron spectrum with a (typically) flat or mildly inverted spectral index ($\alpha\,{\gtrsim}\,0$; the flux density, $F_{R,\nu}$ is proportional to the observing frequency, $\nu$, such that $F_{R,\nu} \propto \nu^\alpha$) up to a break frequency where the spectrum becomes optically thin (cite: migliari2010; russel2013; russell2014). The radio luminosity from the compact jet shows a strong, positive correlation with X-ray luminosity from the accretion flow (cite: gallo2003; corbel2013; gallo2018), consistent with continuous accretion-jet coupling in the hard state.

Monitoring campaigns following state transitions have captured ${\geq}\,3\,$orders of magnitude decreases in radio luminosity, showing that compact jets are strongly quenched in the soft state (cite: Fender1999gx339quench; coriat2011; bright2020; russell2019; russel2020; Maccarone2020quench; Carotenuto2021). Around this time, bright radio flares can be observed around the hard-to-soft state transition (cite: atetarenko2017). These flares are associated with the launching of mild-to-extremely relativistically bipolar ejecta, decoupling the jets from the accretion flow (cite: mirabel1994; Hjellming1995; Fender1999; Corbel2002Ejecta; Brocksopp2002ejection; rushton2017; millerjones2019; russel2019; bright2020; Carotenuto2021; wood2021). The radio spectra of the flares evolve rapidly in time, transitioning from optically thick to optically thin synchrotron emission as the emitting plasma expands, causing a decrease in the self-absorption frequency (cite: vdl1966; Hjellming1988; fender2019). As a result, for the majority of their lifetimes (including when they are spatially resolvable), ejecta are optically thin radio sources.

Jet ejecta can be detected from minutes to even years after launch (cite: Corbel2002Ejecta; millerjones2019; Bahramian2023; wood2021). An observational consequence is that radio emission can be detected in the soft state despite the compact jet being quenched. The longest-lasting ejecta are believed to remain bright because of the continual acceleration of particles driven by interactions with the ambient interstellar medium (cite: Corbel2002Ejecta; russell2019; Espinasse2020; bright2020; Carotenuto2021), where some BH LMXB jets produce interaction regions tens of parsecs away from the BH (cite: Tetarenko2018b). In extreme cases, ejecta that have faded below the detection threshold can remain undetected for months or years before re-brightening during jet-ISM interactions (cite: Corbel2002Ejecta; Carotenuto2021).

While there is some phenomenological understanding of the evolution of the jets through the BH LMXB accretion states, knowledge of the precise timings and causal sequence of events leading to jet quenching and transient jet launching, or the intrinsic properties such as total energy content (and thus, total energy available for feedback) is far from complete. Each subsequent BH LMXB outburst provides (often multiple) new opportunities for real-time monitoring of jet launching, disruption, and interaction events and, thus, a chance to test and refine our current understanding. Moreover, multi-wavelength observations allow us to probe the connection between jets and the accretion flow, jets and other outflows (cite: Sanchez2020maxi1820winds) or investigate how jet properties change with the observing frequency (cite: Russell2006LoLx). Naturally, bright outbursts provide the highest-quality monitoring, but only if the observing campaigns are sufficient to build a coherent picture; one such opportunity arose in 2023 when the BH LMXB Swift J1727.8$-$1613 began a bright outburst.

## The 2023–2024 Outburst of Swift J1727.8$-$1613

Swift J1727.8$-$1613 (hereafter Swift J1727) was discovered on 2023 Aug 24 (MJD 60180) by the burst alert telescope (cite: BAT2005; BAT2013) aboard the Neil Gehrels *Swift* Observatory (cite: Swift2004). Within days, the source’s X-ray flux reached ${\sim}\,7\,$Crab (at 2–20 keV), resulting in its initial classification as a gamma-ray burst (cite: page2023). Follow-up X-ray observations refuted a GRB origin, reclassifying (and renaming) the source as the Galactic transient Swift J1727.8$-$1613 (cite: Kennea2023). The rapid rise in X-ray luminosity motivated extensive multi-wavelength monitoring and identified Swift J1727 as a BH LMXB (cite: Mata2025distance1727).

Rapid radio follow-up localized the source with sub-arcsecond precision (J2000), $17$h$27$m$43.31(\,{\pm}\,0.04$s), $-16^\circ12^\prime19.23({\pm}\,0.02^{\prime\prime}$) (cite: millerjones2023a). Multi-epoch optical spectroscopy by (cite: Mata2024distance1727) estimated the properties of the companion star, favouring an early K-type companion star with an ${\sim}\,8\,$hr orbital period. (cite: Mata2024distance1727) used the orbital period and observed optical extinction to estimate an initial distance of $2.7\,{\pm}\,0.3\,$kpc; (cite: Mata2025distance1727) refined the orbital period, calculated a new distance of $3.7\,{\pm}\,0.3\,$kpc, and dynamically confirmed that Swift J1727 contained a stellar-mass black hole. The most recent analysis of optical (and near-UV) extinction by (cite: Burridge2025distance1727) reviewed the systematics in (cite: Mata2025distance1727) and favoured a larger distance of $5.5_{-1.1}^{+1.4}\,$kpc. X-ray spectral modelling revealed relativistically broadened iron lines, suggestive of a high-spin ($a\,{\sim}\,0.98$), medium-inclination system (cite: Draghis2023; Peng2024). Subsequent modelling, which also considered the X-ray polarisation properties, found a similar inclination angle ($\sim$ 30–50$^\circ$) but favoured a lower spin (cite: Svoboda2024).

The initial rise in X-ray luminosity occurred as Swift J1727 exhibited X-ray and radio properties characteristic of the hard accretion state (cite: Bollemeijer2023a; millerjones2023a; Mereminskiy2024; Peng2024; Liu2024); direct imaging of the compact jet revealed Swift J1727 to have the largest resolved compact jet seen from a BH LMXB (cite: Wood2024). As Swift J1727 evolved (through the hard intermediate state), X-ray monitoring suggested the source transitioned to soft-intermediate or soft state on 2024 October 5 (cite: Bollemeijer2023a; Bollemeijer2023b). Radio quenching accompanied the X-ray transition, followed by bright (radio) flaring, consistent with compact jet disruption and the launching of ejecta (cite: millerjones2023b). Subsequent X-ray observations, noting variability in the hardness ratio, were suggestive of multiple returns to the intermediate states (cite: Wenfei2023). Swift J1727 took ${\sim}\,6\,$months to transition back to the hard state and, by that time, its X-ray luminosity decreased by more than two orders of magnitude (cite: Podgorny2024; Russel2024). Swift J1727 has since returned to quiescence.

This paper combines observations from multiple collaborations to present a multi-wavelength, multi-facility radio light curve of Swift J1727 during its 2023–2024 outburst. In addition to flux densities, we include, when available, interband radio spectral indices but omit all other properties (e.g., morphology, proper motion, or polarization), as the comprising collaborations have identified them as the focus of *in prep* publications. Our goal is to provide the broader community with comprehensive radio light curves to aid with interpreting the evolution of Swift J1727, particularly for observing programmes at other wavelengths (e.g., X$-$ray or optical monitoring). The rest of the paper is structured as follows: Section [2](#sec:methods) describes the observing and analysis strategies for each instrument; Section [3](#sec:results) presents the light curves and a qualitatively focused interpretation of the source evolution; finally, Section [4](#sec:conclusions) presents a summary of the observations.

# Data and Analysis

This section summarizes each instrument’s data reduction, calibration, imaging, and analysis techniques. We focus on concise summaries as the collaborations will publish stand-alone papers with more comprehensive descriptions of their observation and analysis routine(s). In Figure [1](#fig:radio_coverage), we include a graphical representation of the radio coverage.

## MeerKAT

Swift J1727 was observed with the radio interferometer MeerKAT (cite: MeerKATCitation) as a part of the ThunderKAT (cite: tkat) and X-KAT programmes (MeerKAT Proposal ID: SCI-20230907-RF-01). MeerKAT is a 64-element interferometer with a maximum baseline length of 8 km. The MeerKAT monitoring includes 52 epochs taken on an approximately weekly observing cadence. Most observations (i.e., 47 epochs) used the L-band receivers ($\sim$ 1.28 GHz; 856 MHz un-flagged bandwidth). Each L-band observation consisted of a single scan of either 15 or 30 minutes on-source, flanked by two 2-minute scans of a nearby gain calibrator (J1733$-$1304). Two 5-minute scans of J1939$-$6342 (PKS B1934$-$638) were included at the beginning and end of each observation for bandpass and flux scale calibration. In addition to the weekly L-band monitoring, five epochs were acquired using MeerKAT’s S-band receivers. One of the S-band observations used the S2 ($\sim$ 2.62 GHz; 875 MHz un-flagged bandwidth) sub-band, and the other four used the S4 ($\sim$ 3.06 GHz; 875 MHz un-flagged bandwidth) sub-band. The S-band monitoring followed the L-band observing strategy.

The data were flagged, calibrated, and imaged using POLKAT[^1] (cite: polkatascl), which is based on the semi-automated routine OXKAT (cite: oxkat2020), but modified to handle full polarisation observations. This work only includes total intensity observations (i.e., Stokes $I$), and thus, OXKAT and POLKAT have near-identical workflows. Readers are directed to (cite: mightee) for a comprehensive description of the workflow but should note that calibration stopped after the direction-independent self-calibration step (2GC in OXKAT parlance). To optimize for high-sensitivity imaging, the image weighting adopted a Briggs’ robustness of 0 (cite: Briggs1995)[^2].

The source properties were measured using the Common Astronomy Software Applications package (cite: Casa2022) task IMFIT, fitting elliptical Gaussian component(s) in a small sub-region

![](images/1727_lc.pdf)

around the source. Multiple Gaussians were simultaneously fit for observations with multiple components (e.g., due to jet ejecta). As the components were unresolved point sources, the component shapes were fixed to the synthesized beam of each image. The (1$\sigma$) uncertainty on the flux densities was measured from the local root-mean-square (rms) noise extracted from an emission-free region centred near the source(s); the extraction region had an area equal to ${\sim}\,$100 PSFs. No further data manipulation was applied.

## Enhanced Multi-Element Remote-Linked Interferometer Network (e-MERLIN)

Swift J1727 was also monitored with the *e*-MERLIN radio-interferometer (cite: Garrington_2016) for 24 epochs in total, from August 2023 to March 2024 (project codes RR16003 and CY16208). *e*-MERLIN is a 7-antenna array with a maximum baseline of 217 km. The first part of the monitoring consisted of a dense coverage at the beginning of the outburst, with 19 observations performed almost daily in September 2024 and during the second half of October 2024, with durations that ranged from 1 to 5.5 hours per epoch, depending on the expected flux density of the target. In this period, observations were performed at C-band, with a central frequency of 5.07 GHz, and total bandwidth of 512 MHz.

The second part of the monitoring started on 2023 December 4 (MJD 60283) and ended on 2024 March 24 (MJD 60393), with five observations log-spaced in time and durations of up to 10 hours. In this part of the campaign, observations were performed at L-band, at a central frequency of 1.51 GHz and total bandwidth of 512 MHz.

For the entire campaign, 3C286 and OQ208 were observed as the flux and bandpass calibrators, respectively, while J1724–1443 was used as the gain calibrator. The data were processed using the *e*-MERLIN CASA Pipeline[^3] (cite: eMCP) version v1.1.19. The pipeline handles the automated *a priori* flagging with AOFLAGGER (cite: Offringa_AOFLAGGER) and the standard bandpass and gain calibration using CASA. For each epoch, since it was intended to build a homogeneous light curve from epochs with very different samplings of the *uv*-plane, the flux density of Swift J1727 was extracted through visibility-plane fitting, using UVMULTIFIT (cite: uvmultifit).

## Allen Telescope Array (ATA)

Observations of Swift J1727 with the Allen Telescope Array (ATA; (cite: bright2023); Pollack et al. *in prep,*; Farah et al. *in prep,*) began on 2023 Aug 30 with regular monitoring occurring until 2023 Nov 08. These observations used 20 (out of 42) of the ATA antenna and had a maximum baseline length of 300 m. The ATA is equipped with wide bandwidth feeds, sensitive to frequencies between ${\sim}\,1$ and ${\sim}\,10\,\rm{GHz}$. The current digitisation capabilities of the ATA backend allow for two ${\sim}\,700\,\rm{MHz}$ bandwidth tunings to be placed independently within this frequency range. The observing campaign included data at central frequencies of $1.5$, $3$, $5$, and $8\,\rm{GHz}$. The flux/bandpass and gain calibrators were 3C286 and J1733$-$1304, respectively. The gain calibrator was visited every 30 minutes at all frequencies. Following the standard procedures, data were reduced in CASA; imaging was performed using WSCLEAN; the flux density of Swift J1727 was measured following Section [2.1](#sec:methods_mkat).

## Karl G. Jansky Very Large Array (VLA)

This work includes three separate observing programs with the VLA. We combine data taken in multiple VLA configurations, and, as a result, the 27-antenna array has a (program-dependent) maximum baseline of 3–36 km. When available, we also include ${\sim}\,$0.3 GHz flux densities taken with The VLA Low-band Ionosphere and Transient Experiment (cite: Peters2023VliteJ1727). VLITE is a commensal instrument on the VLA operated by The U.S. Naval Research Laboratory (NRL); a description of the VLITE processing pipeline can be found in (cite: Polisensky2016VLITE).

The most rapid response observations presented in this work were taken on 2023 August 25 (cite: millerjones2023a) as a part of the JACPOT program (Project Code: VLA/23A–260). Initially approved for rapid response C-band (4–8 GHz) observations, JACPOT also monitored the source daily at C- and X-band (8–12 GHz) during the bright flaring seen in October 2023. The rapid response observations were taken using array’s most extended A-configuration, whereas the flaring occurred when the source was in a hybrid configuration (A$\rightarrow$D). Each JACPOT observation was 20–30 minutes long and used the VLA’s 8-bit samplers, which break each band into two base-bands with 1.024 GHz of bandwidth.

Additionally, during the rising hard state of the outburst, Swift J1727 was also observed by the PITCH-BLACK collaboration (Project Code: VLA/22B–069). The multi-hour PITCH-BLACK observations split the 27-element array (in A-configuration) into three sub-arrays of 10, 9, and 8 antennas. Observations in each sub-array were also made with the 8-bit samplers, and each sub-array observed exclusively in one frequency band: C (4–8 GHz), X (8–12 GHz), or Ku (12–14 GHz) band

Following the source’s return to the hard state, the VLA observed Swift J1727 nine additional times on an approximately weekly cadence (Project Code: VLA/23B–064). Observation durations ranged from 10 to 60 minutes, where longer epochs were taken as the source faded. Observations were recorded at C-band with 3-bit samplers, resulting in 4.096 GHz bandwidth centred at 6.2 GHz. The epochs of this final VLA program were evenly split between B- and C-configuration.

All three VLA projects used 3C286 (J1331$+$305) for bandpass and flux scale calibration and J1733$-$1304 for gain calibration. The multi-hour, sub-arrayed observations (i.e., VLA/22B–069) implemented a custom non-periodic target/calibrator cycle for each sub-array, alternating between Swift J1727 and the calibrators at one band per sub-array, such that simultaneous data in all three bands was obtained. The data were reduced and imaged within CASA, with flagging and calibration performed using the VLA CASA pipeline[^4]. The images were weighted with natural or robust weighting (robustness parameter 0). When necessary, phase-only self-calibration was used to improve image fidelity. Flux densities were measured by fitting a point source in the image plane, as outlined in Section [2.1](#sec:methods_mkat).

## Australia Telescope Compact Array (ATCA)

The Australia Telescope Compact Array (ATCA) observed Swift J1727 thirty-nine times during its 2023–2024 outburst under project codes C2601, C3057, C3362. ATCA is an East-West array with six antennas and a maximum baseline length of 6 km. For all observations, data were recorded simultaneously at central frequencies of 5.5 GHz and 9 GHz, with each frequency band having 2.048 GHz of un-flagged bandwidth. Observations used either J1939$-$6342 (PKS B1934$-$638) or PKS B0823$-$500 for bandpass and flux density calibration depending on source visibility at the time of the observation; J1939$-$6342 was the preferred calibrator. The nearby (${\sim}\,3.4^{\circ}$ away) source J1733$-$1304 (PKS B1730$-$130) was used for gain calibration. Data were first edited for RFI, before being calibrated and imaged following standard procedures within CASAv5.1.2. Imaging typically used a Briggs robust parameter of 0, balancing sensitivity and resolution. However, at later times, when the source was faint, more natural weightings (robustness parameter ${>}\,0$) were used to increase sensitivity. Data were phase-only self-calibrated when the source flux density exceeded $\sim$ 10 mJy. The flux density of the source was measured following the same procedure as Section [2.1](#sec:methods_mkat).

## Atacama Large Millimeter Array (ALMA)

Alongside the PITCH-BLACK observations taken with the VLA, Swift J1727 was observed with ALMA (Project Code: 2022.1.01182.T) four times in September 2023. Data were taken in Band 3, Band 4, and Band 6 at central frequencies of 97.5 GHz, 145.0 GHz, and 233 GHz, respectively. The ALMA correlator was set up to yield 4$\times$2 GHz wide base-bands. During the observations, the array was in its Cycle 10 C8 configuration, with 42–46 antennas and a maximum baseline length of 8.5 km. The data were reduced and imaged within CASA, with flagging and calibration performed using the ALMA CASAv6.2 pipeline. J1924$-$2914 was used as a flux/bandpass calibrator, J1733$-$1304 was used as a phase calibrator, and J1742$-$1517 was used as a check source in all bands. Phase-only self-calibration was performed, and imaging followed standard procedures with a natural weighting scheme to maximize sensitivity. Flux densities of the source were then measured by fitting a point source in the image plane (with the IMFIT task).

## Submillimeter Array (SMA)

Swift J1727 was observed with the SMA eight times in September 2023. The SMA correlator yields 12 GHz of bandwidth per sideband per polarization and was tuned to a frequency of 225.5 GHz. During the observations, the array was in the *subcompact* configuration, with seven available antennas and a maximum baseline length of 25 m. The data were reduced and imaged with multiple reduction paths using in-house pipeline routines, the in-house reduction suite MIR[^5], and MIRIAD (cite: miriad1995), assuring a consistent outcome. The flux density scale was set using MWC349A, BL Lac was the bandpass calibrator, and NRAO 530 (J1733$-$1304) was used as the gain calibrator. The target is a point source at the spatial resolution of the SMA during the observations ($\sim$ 5 arcsec), and source properties were extracted through visibility-plane fitting.

![](images/SwiftJ2727_MAXI_HID.pdf)

![](images/Full_Radio_LCs_Color.png)

![](images/Narrow_Radio_LCs_Color.pdf)

# Results and Discussion

This section presents the radio observations of the 2023–2024 outburst of Swift J1727. To highlight the simultaneous X-ray evolution, we include the X-ray hardness-intensity diagram (HID) using the publicly available data from the Monitor of All sky X-ray Image Gas Slit Camera (cite: MAXI2009; maxigsc). The HID is presented in Figure [2](#fig:XrayHID), where the arrows show the time-evolution of the source and the marker colours trace the radio flux density (scaled to 10$\,$GHz following the routine discussed in Section [3.1.1](#sec:HS_Trans)). The green diamond and yellow star correspond to the reported hard-to-soft (cite: Bollemeijer2023a; Bollemeijer2023b) and soft-to-hard (cite: Podgorny2024) state transitions, respectively. The increase in the hardness ratio following the (initial) reporting of a hard-to-soft state transition is consistent with the reporting by (cite: Wenfei2023) that stated the source returned to the hard state; as a result, Swift J1727 almost certainly underwent multiple hard-to-soft state transitions. From the HID, it is clear that Swift J1727 completed the canonical loop (or ‘turtle head’) pattern seen from BH LMXB outbursts (cite: fender2004; belloni2010), before fading below detectability, and likely returning to quiescence.

The remainder of this section focuses on the evolution of the flux densities and spectral indices from the jet. We only report statistical errors, but we note that telescopes have (frequency-dependent) systematic errors due to uncertainty in the absolute flux scale. Here, we present the integrated radio flux densities; for observations with multiple components (e.g., compact jet and jet ejecta or multiple jet ejecta), we sum the flux densities from the individual components, adding their errors in quadrature as an estimate of the integrated flux density errors. While in some cases, this will be summing information from the core and ejecta, which are physically decoupled, it mimics what would be measured with only low angular resolution monitoring and still captures much of the critical astrophysics.

Aside from the image weightings mentioned in Section [2](#sec:methods), we do not apply any further manipulation of the visibilities during imaging (e.g., no $uv$-tapering). Care should be taken when combining data from different telescopes as they will probe different angular scales and, as a result, may resolve some flux density (this is primarily an issue for jet ejecta and when comparing e-Merlin to the other non-VLBI facilities). Regarding the radio spectral indices, we exclusively calculate inter-band values given that intra-band spectral indices have known biases (cite: Heywood2016). As the source is highly variable, we only calculate these inter-band spectral indices for strictly simultaneous multi-frequency observations. By enforcing strict simultaneity, each spectral index is computed using flux densities from a single observatory (ATCA, VLA, or ATA), thereby avoiding complications arising from differences in angular scale sensitivity across telescopes. Moreover, the multi-frequency observations at these facilities are sensitive to angular scales much larger than the typical source size ($\lesssim$ 1”), mitigating the risk of artificial spectral features caused by frequency-dependent spatial filtering.

The radio properties are graphically represented in Figure [3](#fig:full_radio_LC) and [4](#fig:zoom_radio_LC). We include per-observatory light curves in Appendix A, and the raw data is presented in Appendix B. The data and plotting scripts are available via GitHub[^6].

## Radio Outburst of Swift J1727.8$-$1613

The radio evolution of Swift J1727 is shown in Figure [3](#fig:full_radio_LC): (top panel) lightcurves; (bottom panel) spectral indices. The dashed-dotted and dashed vertical lines correspond to the reported hard-to-soft (2024 October 5; MJD 60222) and soft-to-hard (2024 March 15; MJD 60385) state transitions, respectively (cite: Bollemeijer2023a; Bollemeijer2023b; Podgorny2024).

### The Initial Hard State and State Transition(s)

After the onset of the outburst (2023 August 24, MJD 60180), the source exhibited a sharp rise in its radio flux density, reaching $\sim$ 100 mJy at all frequencies due to its flat spectral index (i.e., $\alpha\,{\sim}\,0$), consistent with emission from a partially self-absorbed compact jet. Swift J1727 remained at $\sim$ 100 mJy for a few weeks before undergoing a decrease in radio flux density, followed by a period of flaring in the lead-up to (and immediately after) the reported hard-to-soft state transition. The radio flaring occurred (approximately) between 2023 September 20 (MJD 60207) and 2023 November 1 (MJD 60249), and the brightest flare reached a flux density of $\sim$ 1 Jy at $\sim$ 1.28 GHz.

Figure [4](#fig:zoom_radio_LC) shows a ‘zoomed-in’ view of the flaring period (grey region, Fig. [3](#fig:full_radio_LC)). The top panel adopts the same marker style and colour scheme as Figure [3](#fig:full_radio_LC). The middle panel presents a monochromatic light curve, where each observation is scaled to 10 GHz using the nearest spectral index measurement. We fold the error in the spectral indexes into our monochromatic flux densities, adopting Gaussian error propagation. However, we note that spectral index variability is an unaccounted-for systematic effect on the scaled flux density of single-frequency observations (i.e., observations where an inter-band spectral index was not calculated). As a result, we exclude observations with central frequencies that have more than an order of magnitude separation from 10 GHz (i.e., $<$ 1 GHz or $>$ 100 GHz) from the monochromatic light curves as large frequency separations will be more affected by errors in the adopted spectral indices. Moreover, systematic errors may significantly worsen during flaring when the radio spectral index is frequency-dependent and rapidly evolving. Despite the systematics, we include the monochromatic light curves as a qualitative description of the flaring progression, and we caution readers to view it as such.

Both the poly and monochromatic light curves clearly show multiple radio flares consistent with the reporting from (cite: Wenfei2023) that Swift J1727 underwent multiple hard-to-soft state transitions. The two most pronounced flares peaked at $\sim$ 300 mJy (0.338 GHz; MJD 60223) and $\sim$ 800 mJy (1.28 GHz; MJD 60231). Alongside the flaring, the radio spectral indices varied between $\alpha\,{\sim}$ 0.9 and $\alpha\,\,{\sim}\,-1.5$, on timescales as short as days. Simultaneous flux density and spectral evolution are typical of the flaring associated with the launching of jet ejecta (cite: fender2019), and a decrease in flux density in the lead-up to flaring (attributed to compact jet quenching) has been observed in other BH LMXBs (cite: Brocksopp2002ejection; russel2019). Recently, the launching of jet ejecta during flaring has been confirmed via direct imaging (cite: Wood2025SWJ1717Ejecta).

Following the prescription from (cite: fender2019), assuming equipartition of energy between particles and magnetic fields, and adopting distances of 3.7–5.5 kpc (cite: Mata2025distance1727; Burridge2025distance1727), we can estimate the minimum internal energy ($E_{\rm min}$) required to produce each flare. The observed flaring corresponds to an $E_{\rm min}\,{\sim}\,(0.6-2)\times10^{40}{\rm\,erg}$, consistent with the range of energies inferred from other sources (cite: fender2019; russell2019; bright2020; Carotenuto2021). It should be noted that alternative and perhaps more robust methods of minimum energy estimation regularly arrive at values orders of magnitude higher than those inferred from flaring alone (cite: bright2020; Carotenuto2022; Carotenuto2024). As a result, these estimates are likely a conservative minimum.

### The Soft State

Following the flaring, Swift J1727 transitioned to the soft state, where its flux density began decreasing, reaching $<$ 10 mJy at all observing frequencies. Swift J1727 then underwent a modest re-brightening that peaked around 2024 January 14 (MJD 60322; $\sim$ 30 mJy at 1.28 GHz), followed by a continuation of the flux density decay. Throughout the soft state, the radio spectral index was optically thin $\alpha\,{\lesssim}-0.5$, consistent with the radio emission originating from jet ejecta, which is unsurprising as radio flaring is a known signature of jet ejection events (cite: Hjellming1995; Fender1999; rushton2017; millerjones2019; bright2020; Carotenuto2021) and compact jet emission is heavily quenched in the soft state (cite: Fender1999gx339quench; coriat2011; russell2019; russel2020; Maccarone2020quench; Carotenuto2021).

Interestingly, while optically thin, the spectral index was highly variable ($-2\,{\lesssim}\,\alpha\,{\lesssim}-0.5$), suggesting a significant evolution in the population of synchrotron emitting particles (likely electrons). The temporal evolution of the spectral index in the soft state is suggestive of particle (re-)acceleration possibly due to jet-ISM interactions (cite: Corbel2002Ejecta; russell2019; bright2020; Carotenuto2021; Bahramian2023). Indeed, the archetypal long-lived ejecta from XTE J1550$-$564 showed a similar transition from $\alpha\,{\sim}\,-1.2$ to $\alpha\,{\sim}\,-0.4$ which was interpreted as an interaction-driven renewal of particle acceleration (cite: Migliori2017XTE1550).

For power-law distributed population synchrotron emitting electrons, $N(E)\text{d}E\propto E^{-p}\text{d}E$, an optically thin spectral index ($\alpha$) is related to the power-law index $p$ through $\alpha = -(p-1)/2$. Therefore, for typical values of $p\,{\sim}\,$2–3 (cite: longair2011), optically thin synchrotron emission should have a spectral index between $-$0.5 and $-$1. Synchrotron cooling can result in more steep spectrum emission as $\alpha = -p/2$; however, spectral indexes of $\alpha\,{<}\,-1.5$ still require values of $p\,{>}\,3$ (e.g., the minimum of $\alpha = -1.86\,{\pm}\,0.08$ on MJD 60293). The origin of steep-spectrum radio sources remains an open question. Prior studies have suggested thermal (or quasi-thermal) particle distributions (cite: Pacholczyk1971Text), ultra-relativistic shocks (cite: Ballard1992), or energy exchange between the particles and turbulent magnetic fields (cite: Bell2019A) can produce steep spectra. However, most BH LMXBs showing comparably steep spectral indices (cite: Russell2010XTESpectra; Shahbaz2013SteepSpectra) have typically been seen with infrared–optical observations of compact jets. Seeing such steep spectral indices for radio observations of ejecta provides an interesting case study for understanding particle acceleration from BH LMXB jets, especially through comparisons with steep-spectrum AGN (cite: Koljonen2015AGNXRBSpectra).

### The Final Hard State and the Return to Quiescence

Towards the end of the outburst, the radio emission of Swift J1727 re-brightened once more after returning to the hard state on (approximately) 2024 March 15 (cite: Podgorny2024). For example, ATCA detected an increase from ${\sim}\,0.1\,$mJy to ${\sim}\,1$ mJy in both its 5.5 and 9.0 GHz bands during observations taken within 4 days, consistent with a re-formation of the compact jet (cite: russell2014). The spectral index evolved from $-$0.5 to $\sim$ 0, where the latter value is typical of a partially self-absorbed synchrotron radiation. The emission associated with the compact jet quickly decayed as the source returned to quiescence. Despite returning to X-ray quiescence, the radio emission plateaued due to long-lasting jet ejecta, presumably interacting with the ISM. Jet ejecta are typically optically thin, consistent with our observations having lower flux densities at higher frequencies. The slow decay, ejecta interactions, and, as a result, renewed particle acceleration make Swift J1727 an ideal candidate for investigating jet-based feedback.

# Conclusion

We have presented a comprehensive multi-frequency, multi-facility radio monitoring campaign of the BH LMXB Swift J1727 during its 2023–2024 outburst. The presented monitoring period began on 2023 August 25 (MJD 60181) and ended 2024 July 27 (MJD 60518), and includes 198 individual epochs with observing frequencies ranging between 0.3 to 225 GHz, making Swift J1727 one of the most intensely monitored LMXBs to date. Our observations captured the complete outburst evolution, including both the hard-to-soft and soft-to-hard state transitions (i.e., the disruption and reformation of the compact jet) and, as a result, bright radio flares and spectral index variability. The primary motivation behind this work was to provide the community with comprehensive radio lightcurves; as a result, we only briefly (and qualitatively) interpreted the data, leaving more comprehensive targeted analyses for future publications by the comprising collaborations. We intend to continue rapidly releasing radio light curves following the cessation of future BH LMXB outbursts, as the radio properties will assist the interpretations drawn from monitoring programs at other wavelengths, akin to how the publicly available MAXI/GSC data is commonly used to interpret the X-ray and accretion state evolution for radio-centred analyses. We encourage other studies of this source to use these data where appropriate.

AKH thanks UKRI for support. AJT and EL acknowledge that this research was undertaken thanks to funding from the Canada Research Chairs Program and the support of the Natural Sciences and Engineering Research Council of Canada (NSERC; funding reference number RGPIN–2024–04458). FC acknowledges support from the Royal Society through the Newton International Fellowship programme (NIF/R1/211296). TDR is an INAF IAF fellow. RS acknowledges the INAF grant number 1.05.23.04.04. JvdE acknowledges a Warwick Astrophysics prize post-doctoral fellowship made possible thanks to a generous philanthropic donation, and was supported by funding from the European Union’s Horizon Europe research and innovation programme under the Marie Sklodowska-Curie grant agreement No 101148693 (MeerSHOCKS) for part of this work. CMW acknowledges financial support from the Forrest Research Foundation Scholarship, the Jean-Pierre Macquart Scholarship, and the Australian Government Research Training Program Scholarship. This project has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101002352, PI: M. Linares).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.1.01182.T. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. The Submillimeter Array is a joint project between the Smithsonian Astrophysical Observatory and the Academia Sinica Institute of Astronomy and Astrophysics and is funded by the Smithsonian Institution and the Academia Sinica. We recognize that Maunakea is a culturally important site for the indigenous Hawaiian people; we are privileged to study the cosmos from its summit. The MeerKAT telescope is operated by the South African Radio Astronomy Observatory, which is a facility of the National Research Foundation, an agency of the Department of Science and Innovation. We acknowledge the use of the Inter-University Institute for Data Intensive Astronomy (IDIA) data intensive research cloud for data processing. IDIA is a South African university partnership involving the University of Cape Town, the University of Pretoria and the University of the Western Cape. The Australia Telescope Compact Array is part of the Australia Telescope National Facility which is funded by the Australian Government for operation as a National Facility managed by CSIRO. We acknowledge the Gomeroi people as the traditional owners of the ATCA observatory site. *e*-MERLIN is a National Facility operated by the University of Manchester at Jodrell Bank Observatory on behalf of STFC, part of UK Research and Innovation. This research has made use of the MAXI data provided by RIKEN, JAXA and the MAXI team.

 

# Additional Figures

Figures [5](#fig:perobs1),  [6](#fig:perobs2), and  [7](#fig:perobs3) show per-observatory per-observatory light curves.

![](images/PerObs1.png)

![](images/PerObs2.png)

![](images/PerObs3.png)

# Data Tables

Table [1](#tab:radio_coverage) contains the radio flux densities and observing parameters (e.g., central frequency, duration, observing date) for each epoch.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-08-25 23:35:48 | 60181.9832 | 20 | VLA | 0.338 | $16\,{\pm}\,8$ | Miller-Jones | VLITE/23A-260 |
| 2023-08-25 23:35:48 | 60181.9832 | 20 | VLA | 5.2 | $17.64\,{\pm}\,0.03$ | Miller-Jones | 23A-260 |
| 2023-08-25 23:35:48 | 60181.9832 | 20 | VLA | 7.5 | $18.88\,{\pm}\,0.04$ | Miller-Jones | 23A-260 |
| 2023-08-27 07:13:43 | 60183.3012 | 210 | ATCA | 5.5 | $53.2\,{\pm}\,0.7$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-08-27 07:13:43 | 60183.3012 | 210 | ATCA | 9.0 | $58.5\,{\pm}\,0.3$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-08-27 15:35:25 | 60183.6496 | 15 | MeerKAT | 1.28 | $46.77\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2023-08-29 18:59:02 | 60185.791 | 265 | e-MERLIN | 5.07 | $74.4\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-08-29 23:49:29 | 60185.9927 | 20 | VLA | 5.2 | $118.73\,{\pm}\,0.03$ | Miller-Jones | 23A-260 |
| 2023-08-29 23:49:29 | 60185.9927 | 20 | VLA | 7.5 | $116.93\,{\pm}\,0.04$ | Miller-Jones | 23A-260 |
| 2023-08-30 01:43:49 | 60186.0721 | 176 | ATA | 8.0 | $103\,{\pm}\,5$ | Bright | — |
| 2023-08-30 01:43:49 | 60186.0721 | 176 | ATA | 5.0 | $107\,{\pm}\,5$ | Bright | — |
| 2023-08-30 01:54:54 | 60186.0798 | 154 | ATA | 8.0 | $105\,{\pm}\,5$ | Bright | — |
| 2023-08-30 01:54:54 | 60186.0798 | 154 | ATA | 5.0 | $108\,{\pm}\,5$ | Bright | — |
| 2023-08-30 23:53:31 | 60186.9955 | 63 | ATA | 8.0 | $113\,{\pm}\,6$ | Bright | — |
| 2023-08-30 23:53:31 | 60186.9955 | 63 | ATA | 3.0 | $104\,{\pm}\,5$ | Bright | — |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 4.75 | $105.21\,{\pm}\,0.07$ | Tetarenko | 22B-069 |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 0.338 | $86\,{\pm}\,13$ | Tetarenko | VLITE/22B-069 |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 8.5 | $108.39\,{\pm}\,0.08$ | Tetarenko | 22B-069 |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 13.5 | $112.9\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 12.5 | $111.0\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 11.0 | $107.92\,{\pm}\,0.09$ | Tetarenko | 22B-069 |
| 2023-09-03 03:59:36 | 60190.1664 | 210 | VLA | 7.5 | $105.59\,{\pm}\,0.06$ | Tetarenko | 22B-069 |
| 2023-09-03 05:54:48 | 60190.2464 | 148 | SMA | 225.0 | $162.6\,{\pm}\,0.4$ | Vrtilek/Gurwell | 2023A-S051 |
| 2023-09-04 06:41:19 | 60191.2787 | 69 | SMA | 225.0 | $156.6\,{\pm}\,0.5$ | Vrtilek/Gurwell | 2023A-S051 |
| 2023-09-04 15:55:43 | 60191.6637 | 15 | MeerKAT | 1.28 | $91.58\,{\pm}\,0.04$ | Fender | X-KAT/ThunderKAT |
| 2023-09-05 00:42:54 | 60192.0298 | 104 | ATA | 3.0 | $81\,{\pm}\,4$ | Bright | — |
| 2023-09-05 00:42:54 | 60192.0298 | 104 | ATA | 8.0 | $82\,{\pm}\,4$ | Bright | — |
| 2023-09-05 05:50:38 | 60192.2435 | 188 | SMA | 225.0 | $137.5\,{\pm}\,0.5$ | Vrtilek/Gurwell | 2023A-S025 |
| 2023-09-06 00:36:34 | 60193.0254 | 145 | ATA | 3.0 | $88\,{\pm}\,4$ | Bright | — |
| 2023-09-06 00:36:34 | 60193.0254 | 145 | ATA | 8.0 | $90\,{\pm}\,5$ | Bright | — |
| 2023-09-06 05:47:11 | 60193.2411 | 180 | SMA | 225.0 | $156.1\,{\pm}\,1.4$ | Vrtilek/Gurwell | 2023A-S025 |
|  |  |  |  |  |  |  |  |

: Table containing each epoch’s observation and flux density information. The variables $t_{\rm mid}$, $\Delta t$, $\nu_{\rm ctr}$, and $F_\nu$ correspond to the midpoint of the observation, approximate observation length, central frequency, and integrated flux density, respectively.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-09-06 15:14:06 | 60193.6348 | 15 | MeerKAT | 1.28 | $95.57\,{\pm}\,0.05$ | Fender | X-KAT/ThunderKAT |
| 2023-09-08 15:05:28 | 60195.6288 | 15 | MeerKAT | 1.28 | $86.64\,{\pm}\,0.04$ | Fender | X-KAT/ThunderKAT |
| 2023-09-09 00:33:15 | 60196.0231 | 112 | ATA | 8.0 | $81\,{\pm}\,4$ | Bright | — |
| 2023-09-09 00:33:15 | 60196.0231 | 112 | ATA | 3.0 | $81\,{\pm}\,4$ | Bright | — |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 4.75 | $92.56\,{\pm}\,0.04$ | Tetarenko | 22B-069 |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 0.338 | $93\,{\pm}\,15$ | Tetarenko | VLITE/22B-069 |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 8.5 | $93.47\,{\pm}\,0.05$ | Tetarenko | 22B-069 |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 7.5 | $92.53\,{\pm}\,0.05$ | Tetarenko | 22B-069 |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 12.5 | $98.56\,{\pm}\,0.07$ | Tetarenko | 22B-069 |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 11.0 | $93.87\,{\pm}\,0.06$ | Tetarenko | 22B-069 |
| 2023-09-09 03:29:39 | 60196.1456 | 210 | VLA | 13.5 | $98.5\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-09 06:02:52 | 60196.252 | 146 | SMA | 225.0 | $149.2\,{\pm}\,0.4$ | Vrtilek/Gurwell | 2023A-S025 |
| 2023-09-09 07:06:31 | 60196.2962 | 324 | ATCA | 5.5 | $99.5\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-09 07:06:31 | 60196.2962 | 324 | ATCA | 9.0 | $98.6\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-09 14:13:12 | 60196.5925 | 1543 | ATA | 1.5 | $83\,{\pm}\,4$ | Bright | — |
| 2023-09-09 14:13:12 | 60196.5925 | 1543 | ATA | 3.0 | $82\,{\pm}\,4$ | Bright | — |
| 2023-09-10 00:24:11 | 60197.0168 | 71 | ATA | 5.0 | $75\,{\pm}\,4$ | Bright | — |
| 2023-09-10 00:24:11 | 60197.0168 | 71 | ATA | 8.0 | $74\,{\pm}\,4$ | Bright | — |
| 2023-09-10 18:24:02 | 60197.7667 | 330 | e-MERLIN | 5.07 | $54.7\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-11 05:50:38 | 60198.2435 | 140 | SMA | 225.0 | $173.4\,{\pm}\,0.5$ | Vrtilek/Gurwell | 2023A-S025 |
| 2023-09-11 17:59:08 | 60198.7494 | 180 | e-MERLIN | 5.07 | $91.5\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-12 23:28:27 | 60199.9781 | 71 | ATA | 5.0 | $106\,{\pm}\,5$ | Bright | — |
| 2023-09-12 23:28:27 | 60199.9781 | 71 | ATA | 8.0 | $109\,{\pm}\,5$ | Bright | — |
| 2023-09-13 01:15:27 | 60200.0524 | 71 | ATA | 1.5 | $85\,{\pm}\,4$ | Bright | — |
| 2023-09-13 01:15:27 | 60200.0524 | 71 | ATA | 3.0 | $97\,{\pm}\,5$ | Bright | — |
| 2023-09-14 01:11:08 | 60201.0494 | 13 | ALMA | 145.0 | $163.5\,{\pm}\,0.04$ | Tetarenko | 2022.1.01182.T |
| 2023-09-14 01:53:11 | 60201.0786 | 15 | ALMA | 97.5 | $147.3\,{\pm}\,0.04$ | Tetarenko | 2022.1.01182.T |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 0.338 | $89\,{\pm}\,14$ | Tetarenko | VLITE/22B-069 |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 12.5 | $105.2\,{\pm}\,0.3$ | Tetarenko | 22B-069 |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 13.5 | $106.6\,{\pm}\,0.3$ | Tetarenko | 22B-069 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 4.75 | $93.31\,{\pm}\,0.03$ | Tetarenko | 22B-069 |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 7.5 | $95.53\,{\pm}\,0.06$ | Tetarenko | 22B-069 |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 8.5 | $97.93\,{\pm}\,0.07$ | Tetarenko | 22B-069 |
| 2023-09-14 02:59:42 | 60201.1248 | 210 | VLA | 11.0 | $98.77\,{\pm}\,0.07$ | Tetarenko | 22B-069 |
| 2023-09-14 17:47:02 | 60201.741 | 180 | e-MERLIN | 5.07 | $88.2\,{\pm}\,0.3$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-15 06:03:44 | 60202.2526 | 79 | SMA | 225.0 | $174\,{\pm}\,1$ | Vrtilek/Gurwell | 2023A-S024 |
| 2023-09-15 17:43:00 | 60202.7382 | 180 | e-MERLIN | 5.07 | $69.9\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-15 23:47:11 | 60202.9911 | 20 | VLA | 0.338 | $80\,{\pm}\,17$ | Miller-Jones | VLITE/23A-260 |
| 2023-09-15 23:47:11 | 60202.9911 | 20 | VLA | 5.2 | $97\,{\pm}\,8$ | Miller-Jones | 23A-260 |
| 2023-09-15 23:47:11 | 60202.9911 | 20 | VLA | 7.5 | $97\,{\pm}\,7$ | Miller-Jones | 23A-260 |
| 2023-09-16 15:30:40 | 60203.6463 | 15 | MeerKAT | 1.28 | $85.15\,{\pm}\,0.04$ | Fender | X-KAT/ThunderKAT |
| 2023-09-16 17:38:58 | 60203.7354 | 180 | e-MERLIN | 5.07 | $82.4\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-17 00:57:36 | 60204.04 | 17 | ALMA | 233.0 | $173.2\,{\pm}\,0.05$ | Tetarenko | 2022.1.01182.T |
| 2023-09-17 01:43:23 | 60204.0718 | 10 | ALMA | 97.5 | $140.8\,{\pm}\,0.03$ | Tetarenko | 2022.1.01182.T |
| 2023-09-17 02:23:51 | 60204.0999 | 13 | ALMA | 145.0 | $150.7\,{\pm}\,0.03$ | Tetarenko | 2022.1.01182.T |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 11.0 | $103.16\,{\pm}\,0.08$ | Tetarenko | 22B-069 |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 0.338 | $77\,{\pm}\,12$ | Tetarenko | VLITE/22B-069 |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 7.5 | $98.6\,{\pm}\,0.07$ | Tetarenko | 22B-069 |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 4.75 | $96.28\,{\pm}\,0.08$ | Tetarenko | 22B-069 |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 13.5 | $111.7\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 12.5 | $109.3\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-17 02:29:36 | 60204.1039 | 210 | VLA | 8.5 | $101.46\,{\pm}\,0.07$ | Tetarenko | 22B-069 |
| 2023-09-17 06:00:08 | 60204.2501 | 99 | SMA | 225.0 | $175.8\,{\pm}\,0.4$ | Vrtilek/Gurwell | 2023A-S024 |
| 2023-09-17 17:34:56 | 60204.7326 | 180 | e-MERLIN | 5.07 | $85.9\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-18 17:40:59 | 60205.7368 | 174 | e-MERLIN | 5.07 | $52.3\,{\pm}\,0.2$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-19 00:24:54 | 60206.0173 | 104 | ATA | 5.0 | $97\,{\pm}\,5$ | Bright | — |
| 2023-09-19 00:24:54 | 60206.0173 | 104 | ATA | 8.0 | $92\,{\pm}\,5$ | Bright | — |
| 2023-09-19 02:17:22 | 60206.0954 | 71 | ATA | 1.5 | $128\,{\pm}\,6$ | Bright | — |
| 2023-09-19 02:17:22 | 60206.0954 | 71 | ATA | 3.0 | $105\,{\pm}\,5$ | Bright | — |
| 2023-09-19 07:51:36 | 60206.3275 | 160 | ATCA | 5.5 | $62.1\,{\pm}\,0.3$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-09-19 07:51:36 | 60206.3275 | 160 | ATCA | 9.0 | $46.5\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-19 10:52:19 | 60206.453 | 133 | ATCA | 9.0 | $79.0\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-19 10:52:19 | 60206.453 | 133 | ATCA | 5.5 | $125.1\,{\pm}\,0.7$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-20 01:23:48 | 60207.0582 | 17 | ALMA | 233.0 | $31.3\,{\pm}\,0.04$ | Tetarenko | 2022.1.01182.T |
| 2023-09-20 01:48:08 | 60207.0751 | 112 | ATA | 5.0 | $50\,{\pm}\,3$ | Bright | — |
| 2023-09-20 01:48:08 | 60207.0751 | 112 | ATA | 8.0 | $39\,{\pm}\,2$ | Bright | — |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 0.338 | $169\,{\pm}\,30$ | Tetarenko | VLITE/22B-069 |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 13.5 | $43.7\,{\pm}\,0.4$ | Tetarenko | 22B-069 |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 12.5 | $43.3\,{\pm}\,0.3$ | Tetarenko | 22B-069 |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 11.0 | $41.6\,{\pm}\,0.3$ | Tetarenko | 22B-069 |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 8.5 | $44.7\,{\pm}\,0.3$ | Tetarenko | 22B-069 |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 7.5 | $46.5\,{\pm}\,0.1$ | Tetarenko | 22B-069 |
| 2023-09-20 02:29:36 | 60207.1039 | 210 | VLA | 4.75 | $54.8\,{\pm}\,0.1$ | Tetarenko | 22B-069 |
| 2023-09-20 04:15:53 | 60207.1777 | 112 | ATA | 1.5 | $85\,{\pm}\,4$ | Bright | — |
| 2023-09-20 04:15:53 | 60207.1777 | 112 | ATA | 3.0 | $53\,{\pm}\,3$ | Bright | — |
| 2023-09-20 07:51:10 | 60207.3272 | 372 | ATCA | 5.5 | $43.0\,{\pm}\,0.3$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-20 07:51:10 | 60207.3272 | 372 | ATCA | 9.0 | $33.4\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-20 17:25:00 | 60207.7257 | 168 | e-MERLIN | 5.07 | $30.1\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-21 09:33:07 | 60208.398 | 372 | ATCA | 5.5 | $54.1\,{\pm}\,0.6$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-21 09:33:07 | 60208.398 | 372 | ATCA | 9.0 | $47.3\,{\pm}\,0.6$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-21 17:22:59 | 60208.7243 | 180 | e-MERLIN | 5.07 | $50.4\,{\pm}\,0.2$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-22 01:16:36 | 60209.0532 | 112 | ATA | 1.5 | $97\,{\pm}\,5$ | Bright | — |
| 2023-09-22 01:16:36 | 60209.0532 | 112 | ATA | 3.0 | $86\,{\pm}\,4$ | Bright | — |
| 2023-09-22 03:44:29 | 60209.1559 | 112 | ATA | 5.0 | $85\,{\pm}\,4$ | Bright | — |
| 2023-09-22 03:44:29 | 60209.1559 | 112 | ATA | 8.0 | $86\,{\pm}\,4$ | Bright | — |
| 2023-09-22 17:18:57 | 60209.7215 | 180 | e-MERLIN | 5.07 | $58.7\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-22 23:50:21 | 60209.9933 | 20 | VLA | 0.338 | $181\,{\pm}\,30$ | Miller-Jones | VLITE/23A-260 |
| 2023-09-22 23:51:04 | 60209.9938 | 20 | VLA | 5.2 | $86\,{\pm}\,1$ | Miller-Jones | 23A-260 |
| 2023-09-22 23:51:04 | 60209.9938 | 20 | VLA | 7.5 | $87.1\,{\pm}\,1.4$ | Miller-Jones | 23A-260 |
| 2023-09-23 10:45:33 | 60210.4483 | 190 | ATCA | 5.5 | $86.9\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-09-23 10:45:33 | 60210.4483 | 190 | ATCA | 9.0 | $78.5\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-23 15:30:31 | 60210.6462 | 15 | MeerKAT | 1.28 | $101.87\,{\pm}\,0.04$ | Fender | X-KAT/ThunderKAT |
| 2023-09-23 17:18:57 | 60210.7215 | 180 | e-MERLIN | 5.07 | $54.2\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-23 23:07:52 | 60210.9638 | 51 | ATA | 1.5 | $106\,{\pm}\,5$ | Bright | — |
| 2023-09-23 23:07:52 | 60210.9638 | 51 | ATA | 3.0 | $74\,{\pm}\,4$ | Bright | — |
| 2023-09-24 00:34:50 | 60211.0242 | 51 | ATA | 5.0 | $57\,{\pm}\,3$ | Bright | — |
| 2023-09-24 00:34:50 | 60211.0242 | 51 | ATA | 8.0 | $37.2\,{\pm}\,1.9$ | Bright | — |
| 2023-09-24 01:24:14 | 60211.0585 | 10 | ALMA | 97.5 | $23.5\,{\pm}\,0.03$ | Tetarenko | 2022.1.01182.T |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 4.75 | $55.5\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 0.338 | $167\,{\pm}\,30$ | Tetarenko | VLITE/22B-069 |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 8.5 | $39.1\,{\pm}\,0.3$ | Tetarenko | 22B-069 |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 13.5 | $33.5\,{\pm}\,0.1$ | Tetarenko | 22B-069 |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 11.0 | $34.1\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 12.5 | $34.0\,{\pm}\,0.2$ | Tetarenko | 22B-069 |
| 2023-09-24 02:14:38 | 60211.0935 | 210 | VLA | 7.5 | $41.3\,{\pm}\,0.1$ | Tetarenko | 22B-069 |
| 2023-09-24 05:56:06 | 60211.2473 | 357 | ATCA | 5.5 | $41.4\,{\pm}\,0.4$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-24 05:56:06 | 60211.2473 | 357 | ATCA | 9.0 | $36.2\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-24 23:14:29 | 60211.9684 | 84 | ATA | 1.5 | $59\,{\pm}\,3$ | Bright | — |
| 2023-09-24 23:14:29 | 60211.9684 | 84 | ATA | 3.0 | $37.0\,{\pm}\,1.8$ | Bright | — |
| 2023-09-25 00:41:28 | 60212.0288 | 83 | ATA | 5.0 | $26.9\,{\pm}\,1.3$ | Bright | — |
| 2023-09-25 00:41:28 | 60212.0288 | 83 | ATA | 8.0 | $21.8\,{\pm}\,1.1$ | Bright | — |
| 2023-09-25 09:32:24 | 60212.3975 | 347 | ATCA | 5.5 | $29.6\,{\pm}\,0.8$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-25 09:32:24 | 60212.3975 | 347 | ATCA | 9.0 | $21.0\,{\pm}\,0.7$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-25 17:58:59 | 60212.7493 | 180 | e-MERLIN | 5.07 | $28.3\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-26 00:02:26 | 60213.0017 | 51 | ATA | 1.5 | $63\,{\pm}\,3$ | Bright | — |
| 2023-09-26 00:02:26 | 60213.0017 | 51 | ATA | 3.0 | $46\,{\pm}\,2$ | Bright | — |
| 2023-09-26 01:29:16 | 60213.062 | 51 | ATA | 5.0 | $34.1\,{\pm}\,1.7$ | Bright | — |
| 2023-09-26 01:29:16 | 60213.062 | 51 | ATA | 8.0 | $21\,{\pm}\,1$ | Bright | — |
| 2023-09-26 19:44:32 | 60213.8226 | 60 | e-MERLIN | 5.07 | $6.7\,{\pm}\,0.2$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-27 10:16:45 | 60214.4283 | 262 | ATCA | 5.5 | $32.5\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-09-27 10:16:45 | 60214.4283 | 262 | ATCA | 9.0 | $29.2\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-28 10:19:29 | 60215.4302 | 257 | ATCA | 5.5 | $58.3\,{\pm}\,0.4$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-28 10:19:29 | 60215.4302 | 257 | ATCA | 9.0 | $49.5\,{\pm}\,0.6$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-29 08:47:54 | 60216.3666 | 403 | ATCA | 5.5 | $20.0\,{\pm}\,0.01$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-29 08:47:54 | 60216.3666 | 403 | ATCA | 9.0 | $16.31\,{\pm}\,0.01$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-29 16:58:56 | 60216.7076 | 240 | e-MERLIN | 5.07 | $10.7\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-09-30 10:59:39 | 60217.4581 | 157 | ATCA | 5.5 | $16.2\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-09-30 10:59:39 | 60217.4581 | 157 | ATCA | 9.0 | $11.7\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-01 12:57:36 | 60218.54 | 15 | MeerKAT | 1.28 | $23.85\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-10-02 02:35:31 | 60219.108 | 165 | ATCA | 5.5 | $22.64\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-02 02:35:31 | 60219.108 | 165 | ATCA | 9.0 | $20.83\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-05 00:27:47 | 60222.0193 | 30 | VLA | 0.338 | $51\,{\pm}\,20$ | Miller-Jones | VLITE/23A-260 |
| 2023-10-05 00:27:47 | 60222.0193 | 30 | VLA | 5.2 | $8\,{\pm}\,1$ | Miller-Jones | 23A-260 |
| 2023-10-05 00:27:47 | 60222.0193 | 30 | VLA | 7.5 | $6.8\,{\pm}\,1.1$ | Miller-Jones | 23A-260 |
| 2023-10-06 00:49:58 | 60223.0347 | 30 | VLA | 8.5 | $213.57\,{\pm}\,0.06$ | Miller-Jones | 23A-260 |
| 2023-10-06 00:49:58 | 60223.0347 | 30 | VLA | 11.0 | $202.19\,{\pm}\,0.09$ | Miller-Jones | 23A-260 |
| 2023-10-06 00:49:58 | 60223.0347 | 30 | VLA | 5.2 | $233.7\,{\pm}\,1.1$ | Miller-Jones | 23A-260 |
| 2023-10-06 00:49:58 | 60223.0347 | 30 | VLA | 7.5 | $215\,{\pm}\,1$ | Miller-Jones | 23A-260 |
| 2023-10-06 00:49:58 | 60223.0347 | 30 | VLA | 0.338 | $332\,{\pm}\,50$ | Miller-Jones | VLITE/23A-260 |
| 2023-10-06 14:21:50 | 60223.5985 | 15 | MeerKAT | 1.28 | $182.03\,{\pm}\,0.06$ | Fender | X-KAT/ThunderKAT |
| 2023-10-06 22:54:02 | 60223.9542 | 30 | VLA | 10.2 | $58.86\,{\pm}\,0.07$ | Miller-Jones | 23A-260 |
| 2023-10-06 22:54:02 | 60223.9542 | 30 | VLA | 8.5 | $63.84\,{\pm}\,0.06$ | Miller-Jones | 23A-260 |
| 2023-10-06 22:54:02 | 60223.9542 | 30 | VLA | 0.338 | $245\,{\pm}\,40$ | Miller-Jones | VLITE/23A-260 |
| 2023-10-06 23:29:54 | 60223.9791 | 30 | VLA | 7.5 | $68.8\,{\pm}\,0.4$ | Miller-Jones | 23A-260 |
| 2023-10-06 23:29:54 | 60223.9791 | 30 | VLA | 5.2 | $80.8\,{\pm}\,0.3$ | Miller-Jones | 23A-260 |
| 2023-10-07 23:13:55 | 60224.968 | 30 | VLA | 10.2 | $18.94\,{\pm}\,0.07$ | Miller-Jones | 23A-260 |
| 2023-10-07 23:13:55 | 60224.968 | 30 | VLA | 8.5 | $21.07\,{\pm}\,0.06$ | Miller-Jones | 23A-260 |
| 2023-10-07 23:13:55 | 60224.968 | 30 | VLA | 0.338 | $86\,{\pm}\,14$ | Miller-Jones | VLITE/23A-260 |
| 2023-10-07 23:49:46 | 60224.9929 | 30 | VLA | 7.5 | $14.4\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
| 2023-10-07 23:49:46 | 60224.9929 | 30 | VLA | 5.2 | $19.6\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-10-08 23:22:16 | 60225.9738 | 51 | ATA | 1.5 | $38.8\,{\pm}\,1.9$ | Bright | — |
| 2023-10-08 23:22:16 | 60225.9738 | 51 | ATA | 3.0 | $25.4\,{\pm}\,1.3$ | Bright | — |
| 2023-10-08 23:44:26 | 60225.9892 | 30 | VLA | 10.2 | $17.7\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
| 2023-10-08 23:44:26 | 60225.9892 | 30 | VLA | 8.5 | $19.3\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
| 2023-10-09 00:20:18 | 60226.0141 | 30 | VLA | 0.338 | $53\,{\pm}\,12$ | Miller-Jones | VLITE/23A-260 |
| 2023-10-09 00:20:18 | 60226.0141 | 30 | VLA | 7.5 | $21.2\,{\pm}\,0.2$ | Miller-Jones | 23A-260 |
| 2023-10-09 00:20:18 | 60226.0141 | 30 | VLA | 5.2 | $25.4\,{\pm}\,0.2$ | Miller-Jones | 23A-260 |
| 2023-10-09 00:49:06 | 60226.0341 | 51 | ATA | 8.0 | $15.9\,{\pm}\,0.8$ | Bright | — |
| 2023-10-09 00:49:06 | 60226.0341 | 51 | ATA | 5.0 | $21.4\,{\pm}\,1.1$ | Bright | — |
| 2023-10-09 23:15:21 | 60226.969 | 30 | VLA | 10.2 | $15.53\,{\pm}\,0.08$ | Miller-Jones | 23A-260 |
| 2023-10-09 23:15:21 | 60226.969 | 30 | VLA | 8.5 | $15.97\,{\pm}\,0.07$ | Miller-Jones | 23A-260 |
| 2023-10-10 23:44:09 | 60227.989 | 30 | VLA | 10.2 | $5.4\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
| 2023-10-10 23:44:09 | 60227.989 | 30 | VLA | 8.5 | $5.6\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
| 2023-10-12 00:08:55 | 60229.0062 | 30 | VLA | 10.2 | $8.3\,{\pm}\,0.5$ | Miller-Jones | 23A-260 |
| 2023-10-12 00:08:55 | 60229.0062 | 30 | VLA | 8.5 | $8.6\,{\pm}\,0.2$ | Miller-Jones | 23A-260 |
| 2023-10-13 00:06:46 | 60230.0047 | 30 | VLA | 10.2 | $9.5\,{\pm}\,0.3$ | Miller-Jones | 23A-260 |
| 2023-10-13 00:06:46 | 60230.0047 | 30 | VLA | 8.5 | $10.2\,{\pm}\,0.2$ | Miller-Jones | 23A-260 |
| 2023-10-13 16:19:03 | 60230.6799 | 180 | e-MERLIN | 5.07 | $3.47\,{\pm}\,0.07$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-10-13 23:53:57 | 60230.9958 | 30 | VLA | 10.2 | $368.0\,{\pm}\,0.1$ | Miller-Jones | 23A-260 |
| 2023-10-13 23:53:57 | 60230.9958 | 30 | VLA | 8.5 | $387.76\,{\pm}\,0.09$ | Miller-Jones | 23A-260 |
| 2023-10-14 12:47:48 | 60231.5332 | 15 | MeerKAT | 1.28 | $839.4\,{\pm}\,0.3$ | Fender | X-KAT/ThunderKAT |
| 2023-10-14 16:19:03 | 60231.6799 | 180 | e-MERLIN | 5.07 | $182.2\,{\pm}\,0.4$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-10-15 00:54:34 | 60232.0379 | 30 | VLA | 10.2 | $262.9\,{\pm}\,0.3$ | Miller-Jones | 23A-260 |
| 2023-10-15 00:54:34 | 60232.0379 | 30 | VLA | 8.5 | $224.6\,{\pm}\,0.3$ | Miller-Jones | 23A-260 |
| 2023-10-15 16:19:03 | 60232.6799 | 180 | e-MERLIN | 5.07 | $53.0\,{\pm}\,0.1$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-10-15 22:21:04 | 60232.9313 | 30 | VLA | 10.2 | $71\,{\pm}\,4$ | Miller-Jones | 23A-260 |
| 2023-10-15 22:21:04 | 60232.9313 | 30 | VLA | 8.5 | $71\,{\pm}\,3$ | Miller-Jones | 23A-260 |
| 2023-10-15 23:14:47 | 60232.9686 | 51 | ATA | 3.0 | $82\,{\pm}\,4$ | Bright | — |
| 2023-10-15 23:14:47 | 60232.9686 | 51 | ATA | 1.5 | $115\,{\pm}\,6$ | Bright | — |
| 2023-10-16 03:57:27 | 60233.1649 | 65 | ATCA | 9.0 | $34.9\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-10-16 03:57:27 | 60233.1649 | 65 | ATCA | 5.5 | $58.5\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-16 11:07:26 | 60233.4635 | 50 | ATCA | 5.5 | $61.1\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-16 11:07:26 | 60233.4635 | 50 | ATCA | 9.0 | $40.5\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-16 15:57:44 | 60233.6651 | 15 | MeerKAT | 1.28 | $101.9\,{\pm}\,0.05$ | Fender | X-KAT/ThunderKAT |
| 2023-10-17 23:12:20 | 60234.9669 | 51 | ATA | 3.0 | $40\,{\pm}\,2$ | Bright | — |
| 2023-10-17 23:12:20 | 60234.9669 | 51 | ATA | 1.5 | $52\,{\pm}\,3$ | Bright | — |
| 2023-10-18 00:39:10 | 60235.0272 | 51 | ATA | 8.0 | $17.8\,{\pm}\,0.9$ | Bright | — |
| 2023-10-18 00:39:10 | 60235.0272 | 51 | ATA | 5.0 | $34.5\,{\pm}\,1.7$ | Bright | — |
| 2023-10-21 01:06:40 | 60238.0463 | 44 | ATCA | 9.0 | $7.9\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-21 01:06:40 | 60238.0463 | 44 | ATCA | 5.5 | $15.9\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-22 01:35:19 | 60239.0662 | 46 | ATCA | 9.0 | $10.1\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-22 01:35:19 | 60239.0662 | 46 | ATCA | 5.5 | $19.2\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-22 11:39:33 | 60239.4858 | 15 | MeerKAT | 1.28 | $54.84\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2023-10-23 01:35:11 | 60240.0661 | 48 | ATCA | 5.5 | $34.7\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-23 01:35:11 | 60240.0661 | 48 | ATCA | 9.0 | $29.2\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-24 23:16:30 | 60241.9698 | 71 | ATA | 5.0 | $47\,{\pm}\,2$ | Bright | — |
| 2023-10-24 23:16:30 | 60241.9698 | 71 | ATA | 8.0 | $27.4\,{\pm}\,1.4$ | Bright | — |
| 2023-10-25 09:55:52 | 60242.4138 | 122 | ATCA | 5.5 | $27.5\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-25 09:55:52 | 60242.4138 | 122 | ATCA | 9.0 | $18.69\,{\pm}\,0.07$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-25 15:11:39 | 60242.6331 | 212 | e-MERLIN | 5.07 | $6.03\,{\pm}\,0.07$ | Williams-Baldwin/Carotenuto | RR16003 |
| 2023-10-26 10:15:53 | 60243.4277 | 55 | ATCA | 9.0 | $10.6\,{\pm}\,0.5$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-26 10:15:53 | 60243.4277 | 55 | ATCA | 5.5 | $16.2\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-10-28 12:30:14 | 60245.521 | 15 | MeerKAT | 1.28 | $52.48\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2023-11-06 10:29:25 | 60254.4371 | 15 | MeerKAT | 1.28 | $57.36\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2023-11-08 22:04:39 | 60256.9199 | 71 | ATA | 3.0 | $21.5\,{\pm}\,1.1$ | Bright | — |
| 2023-11-08 22:04:39 | 60256.9199 | 71 | ATA | 1.5 | $29.4\,{\pm}\,1.5$ | Bright | — |
| 2023-11-08 23:51:12 | 60256.9939 | 71 | ATA | 5.0 | $11.9\,{\pm}\,0.6$ | Bright | — |
| 2023-11-12 11:33:30 | 60260.4816 | 15 | MeerKAT | 1.28 | $28.85\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-11-18 01:49:43 | 60266.0762 | 76 | ATCA | 5.5 | $7.53\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-11-18 01:49:43 | 60266.0762 | 76 | ATCA | 9.0 | $5.01\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2023-11-18 11:19:06 | 60266.4716 | 15 | MeerKAT | 1.28 | $16.78\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-11-21 23:09:27 | 60269.9649 | 132 | ATCA | 9.0 | $1.51\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-11-21 23:09:27 | 60269.9649 | 132 | ATCA | 5.5 | $2.79\,{\pm}\,0.05$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-11-25 11:02:41 | 60273.4602 | 15 | MeerKAT | 1.28 | $6.12\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-11-26 00:55:17 | 60274.0384 | 188 | ATCA | 9.0 | $0.85\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-11-26 00:55:17 | 60274.0384 | 188 | ATCA | 5.5 | $1.94\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-02 10:48:25 | 60280.4503 | 15 | MeerKAT | 1.28 | $8.38\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-12-04 06:48:05 | 60282.2834 | 183 | ATCA | 5.5 | $2.56\,{\pm}\,0.05$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-04 06:48:05 | 60282.2834 | 183 | ATCA | 9.0 | $1.44\,{\pm}\,0.04$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-05 00:53:34 | 60283.0372 | 336 | e-MERLIN | 1.51 | $0.58\,{\pm}\,0.08$ | Williams-Baldwin/Carotenuto | CY16208 |
| 2023-12-08 22:29:25 | 60286.9371 | 183 | ATCA | 5.5 | $3.44\,{\pm}\,0.04$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-08 22:29:25 | 60286.9371 | 183 | ATCA | 9.0 | $2.34\,{\pm}\,0.04$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-10 00:23:54 | 60288.0166 | 420 | e-MERLIN | 1.51 | $0.71\,{\pm}\,0.05$ | Williams-Baldwin/Carotenuto | CY16208 |
| 2023-12-10 08:10:36 | 60288.3407 | 15 | MeerKAT | 1.28 | $9.26\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-12-15 23:25:52 | 60293.9763 | 292 | ATCA | 9.0 | $0.83\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-15 23:25:52 | 60293.9763 | 292 | ATCA | 5.5 | $2.08\,{\pm}\,0.04$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-17 08:44:52 | 60295.3645 | 15 | MeerKAT | 1.28 | $7.66\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-12-21 01:18:28 | 60299.0545 | 497 | e-MERLIN | 1.51 | $0.99\,{\pm}\,0.07$ | Williams-Baldwin/Carotenuto | CY16208 |
| 2023-12-23 07:50:35 | 60301.3268 | 15 | MeerKAT | 1.28 | $13.08\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2023-12-29 00:09:30 | 60307.0066 | 327 | ATCA | 5.5 | $4.5\,{\pm}\,0.04$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-29 00:09:30 | 60307.0066 | 327 | ATCA | 9.0 | $2.98\,{\pm}\,0.04$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2023-12-30 07:47:08 | 60308.3244 | 15 | MeerKAT | 1.28 | $12.03\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2024-01-06 23:27:01 | 60315.9771 | 237 | ATCA | 9.0 | $10.26\,{\pm}\,0.06$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-01-06 23:27:01 | 60315.9771 | 237 | ATCA | 5.5 | $13.68\,{\pm}\,0.06$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-01-07 07:58:04 | 60316.332 | 15 | MeerKAT | 1.28 | $24.39\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2024-01-09 04:59:57 | 60318.2083 | 15 | MeerKAT | 2.62 | $17.98\,{\pm}\,0.01$ | Fender | X-KAT/ThunderKAT |
| 2024-01-14 04:54:37 | 60323.2046 | 15 | MeerKAT | 1.28 | $17.72\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2024-01-21 06:34:07 | 60330.2737 | 15 | MeerKAT | 3.06 | $5.04\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2024-01-22 05:38:49 | 60331.2353 | 15 | MeerKAT | 1.28 | $7.38\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-01-24 22:51:18 | 60333.9523 | 451 | ATCA | 9.0 | $1.52\,{\pm}\,0.05$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2024-01-24 22:51:18 | 60333.9523 | 451 | ATCA | 5.5 | $2.32\,{\pm}\,0.05$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-01-29 05:05:16 | 60338.212 | 15 | MeerKAT | 1.28 | $6.3\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-02-01 21:53:08 | 60341.9119 | 367 | ATCA | 5.5 | $2.03\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-02-01 21:53:08 | 60341.9119 | 367 | ATCA | 9.0 | $1.2\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-02-04 05:33:47 | 60344.2318 | 15 | MeerKAT | 1.28 | $5.25\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-02-10 03:46:13 | 60350.1571 | 15 | MeerKAT | 1.28 | $4.65\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-02-14 00:44:47 | 60354.0311 | 253 | ATCA | 5.5 | $1.16\,{\pm}\,0.08$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-02-14 00:44:47 | 60354.0311 | 253 | ATCA | 9.0 | $0.68\,{\pm}\,0.08$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-02-19 04:29:16 | 60359.187 | 15 | MeerKAT | 1.28 | $3.69\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-02-21 19:28:33 | 60361.8115 | 588 | e-MERLIN | 1.51 | $0.26\,{\pm}\,0.04$ | Williams-Baldwin/Carotenuto | CY16208 |
| 2024-02-25 03:30:05 | 60365.1459 | 15 | MeerKAT | 1.28 | $3.33\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-03-04 03:22:10 | 60373.1404 | 15 | MeerKAT | 1.28 | $2.41\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-03-09 04:09:24 | 60378.1732 | 15 | MeerKAT | 1.28 | $1.92\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2024-03-16 02:43:52 | 60385.1138 | 15 | MeerKAT | 1.28 | $1.5\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-03-17 23:34:30 | 60386.9823 | 187 | ATCA | 5.5 | $0.19\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-17 23:34:30 | 60386.9823 | 187 | ATCA | 9.0 | $0.1\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-19 23:48:11 | 60388.9918 | 160 | ATCA | 5.5 | $0.55\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-19 23:48:11 | 60388.9918 | 160 | ATCA | 9.0 | $0.46\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-21 21:45:21 | 60390.9065 | 287 | ATCA | 5.5 | $1.21\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-21 21:45:21 | 60390.9065 | 287 | ATCA | 9.0 | $1.29\,{\pm}\,0.03$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-24 01:59:05 | 60393.0827 | 15 | MeerKAT | 1.28 | $2.36\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-03-24 17:38:32 | 60393.7351 | 574 | e-MERLIN | 1.51 | $0.58\,{\pm}\,0.04$ | Williams-Baldwin/Carotenuto | CY16208 |
| 2024-03-24 21:54:25 | 60393.9128 | 78 | ATCA | 5.5 | $1.246\,{\pm}\,0.003$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-24 21:54:25 | 60393.9128 | 78 | ATCA | 9.0 | $1.37\,{\pm}\,0.01$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-27 00:45:38 | 60396.0317 | 8 | ATCA | 5.5 | $1.2\,{\pm}\,0.2$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-27 00:45:38 | 60396.0317 | 8 | ATCA | 9.0 | $1.1\,{\pm}\,0.1$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-31 00:52:16 | 60400.0363 | 15 | MeerKAT | 1.28 | $2.23\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-03-31 17:09:27 | 60400.7149 | 398 | ATCA | 5.5 | $1.17\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-03-31 17:09:27 | 60400.7149 | 398 | ATCA | 9.0 | $1.09\,{\pm}\,0.02$ | Russell/Carotenuto | C2601/C3057/C3362/CX550 |
| 2024-04-06 12:07:03 | 60406.5049 | 12 | VLA | 6.2 | $0.76\,{\pm}\,0.01$ | Plotkin | 23B-064 |
|  |  |  |  |  |  |  |  |

: Continued.

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  | $t_{\rm mid}$ (MJD) | $\Delta t$ (min) | Telescope | $\nu_{\rm ctr}$ (GHz) | $F_{\nu}$ (mJy) | PI Name | Project ID |
| 2024-04-07 23:19:06 | 60407.9716 | 15 | MeerKAT | 1.28 | $1.54\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-04-13 00:31:06 | 60413.0216 | 15 | MeerKAT | 1.28 | $1.37\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-04-13 13:00:11 | 60413.5418 | 12 | VLA | 6.2 | $0.58\,{\pm}\,0.01$ | Plotkin | 23B-064 |
| 2024-04-20 08:02:32 | 60420.3351 | 12 | VLA | 6.2 | $0.44\,{\pm}\,0.01$ | Plotkin | 23B-064 |
| 2024-04-21 23:38:06 | 60421.9848 | 15 | MeerKAT | 1.28 | $1.06\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-04-29 00:46:48 | 60429.0325 | 15 | MeerKAT | 1.28 | $0.89\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-05-05 22:29:42 | 60435.9373 | 15 | MeerKAT | 1.28 | $0.67\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-05-08 07:06:40 | 60438.2963 | 12 | VLA | 6.2 | $0.16\,{\pm}\,0.01$ | Plotkin | 23B-064 |
| 2024-05-11 22:51:36 | 60441.9525 | 15 | MeerKAT | 1.28 | $0.61\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-05-13 22:24:23 | 60443.9336 | 15 | MeerKAT | 3.06 | $0.36\,{\pm}\,0.02$ | Fender | X-KAT/ThunderKAT |
| 2024-05-14 09:58:01 | 60444.4153 | 27 | VLA | 6.2 | $0.14\,{\pm}\,0.01$ | Plotkin | 23B-064 |
| 2024-05-18 23:26:52 | 60448.977 | 15 | MeerKAT | 1.28 | $0.66\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-05-23 06:04:19 | 60453.253 | 26 | VLA | 6.2 | $0.2\,{\pm}\,0.01$ | Plotkin | 23B-064 |
| 2024-05-25 23:16:04 | 60455.9695 | 15 | MeerKAT | 1.28 | $0.66\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-05-29 11:14:21 | 60459.4683 | 40 | VLA | 6.2 | $0.176\,{\pm}\,0.007$ | Plotkin | 23B-064 |
| 2024-06-02 22:32:18 | 60463.9391 | 15 | MeerKAT | 1.28 | $0.7\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-06-08 21:54:43 | 60469.913 | 30 | MeerKAT | 1.28 | $0.66\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-06-10 20:21:07 | 60471.848 | 30 | MeerKAT | 3.06 | $0.36\,{\pm}\,0.01$ | Fender | X-KAT/ThunderKAT |
| 2024-06-15 20:27:01 | 60476.8521 | 15 | MeerKAT | 1.28 | $0.65\,{\pm}\,0.06$ | Fender | X-KAT/ThunderKAT |
| 2024-06-22 19:46:50 | 60483.8242 | 15 | MeerKAT | 1.28 | $0.51\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-06-29 18:06:54 | 60490.7548 | 15 | MeerKAT | 1.28 | $0.48\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-07-01 18:46:22 | 60492.7822 | 15 | MeerKAT | 3.06 | $0.26\,{\pm}\,0.01$ | Fender | X-KAT/ThunderKAT |
| 2024-07-08 17:14:47 | 60499.7186 | 15 | MeerKAT | 1.28 | $0.6\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-07-15 18:33:33 | 60506.7733 | 15 | MeerKAT | 1.28 | $0.46\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-07-21 17:46:27 | 60512.7406 | 15 | MeerKAT | 1.28 | $0.51\,{\pm}\,0.03$ | Fender | X-KAT/ThunderKAT |
| 2024-07-27 19:14:52 | 60518.802 | 15 | MeerKAT | 1.28 | $0.52\,{\pm}\,0.04$ | Fender | X-KAT/ThunderKAT |
|  |  |  |  |  |  |  |  |

: Continued.

natexlab

(ref: Bahramian2023) Bahramian, A., Tremou, E., Tetarenko, A. J., et al. 2023, ApJL, 948, L7, doi: [`10.3847/2041-8213/accde1`](http://doi.org/10.3847/2041-8213/accde1)

(ref: Ballard1992) Ballard, K. R., & Heavens, A. F. 1992, MNRAS, 259, 89, doi: [`10.1093/mnras/259.1.89`](http://doi.org/10.1093/mnras/259.1.89)

(ref: BAT2005) Barthelmy, S. D., Barbier, L. M., Cummings, J. R., et al. 2005, Space Sci. Rev., 120, 143, doi: [`10.1007/s11214-005-5096-3`](http://doi.org/10.1007/s11214-005-5096-3)

(ref: Bell2019A) Bell, A. R., Matthews, J. H., & Blundell, K. M. 2019, MNRAS, 488, 2466, doi: [`10.1093/mnras/stz1805`](http://doi.org/10.1093/mnras/stz1805)

(ref: Belloni1999) Belloni, T., Méndez, M., van der Klis, M., Lewin, W. H. G., & Dieters, S. 1999, ApJL, 519, L159, doi: [`10.1086/312130`](http://doi.org/10.1086/312130)

(ref: belloni2010) Belloni, T. M. 2010, in Lecture Notes in Physics, ed. T. Belloni, Vol. 794 (Berlin: Springer Verlag), 53, doi: [`10.1007/978-3-540-76937-83`](http://doi.org/10.1007/978-3-540-76937-83)

(ref: blandfordkonigl1979) Blandford, R. D., & Königl, A. 1979, ApJ, 232, 34, doi: [`10.1086/157262`](http://doi.org/10.1086/157262)

(ref: Bollemeijer2023a) Bollemeijer, N., Uttley, P., Buisson, D., et al. 2023a, The Astronomer’s Telegram, 16247, 1

(ref: Bollemeijer2023b) —. 2023b, The Astronomer’s Telegram, 16273, 1

(ref: Briggs1995) Briggs, D. S. 1995, in American Astronomical Society Meeting Abstracts, Vol. 187, American Astronomical Society Meeting Abstracts, 112.02

(ref: bright2020) Bright, J. S., et al. 2020, Nature Astron., 4, 697, doi: [`10.1038/s41550-020-1023-5`](http://doi.org/10.1038/s41550-020-1023-5)

(ref: bright2023) Bright, J. S., Rhodes, L., Farah, W., et al. 2023, Nature Astronomy, 7, 986, doi: [`10.1038/s41550-023-01997-9`](http://doi.org/10.1038/s41550-023-01997-9)

(ref: Brocksopp2002ejection) Brocksopp, C., Fender, R. P., McCollough, M., et al. 2002, MNRAS, 331, 765, doi: [`10.1046/j.1365-8711.2002.05230.x`](http://doi.org/10.1046/j.1365-8711.2002.05230.x)

(ref: Burridge2025distance1727) Burridge, B. J., Miller-Jones, J. C. A., Bahramian, A., et al. 2025, arXiv e-prints, arXiv:2502.06448. [`https://arxiv.org/abs/2502.06448`](https://arxiv.org/abs/2502.06448)

(ref: Carotenuto2024) Carotenuto, F., Fender, R., Tetarenko, A. J., et al. 2024, arXiv e-prints, arXiv:2405.16624, doi: [`10.48550/arXiv.2405.16624`](http://doi.org/10.48550/arXiv.2405.16624)

(ref: Carotenuto2022) Carotenuto, F., Tetarenko, A. J., & Corbel, S. 2022, MNRAS, 511, 4826, doi: [`10.1093/mnras/stac329`](http://doi.org/10.1093/mnras/stac329)

(ref: Carotenuto2021) Carotenuto, F., Corbel, S., Tremou, E., et al. 2021, MNRAS, 504, 444, doi: [`10.1093/mnras/stab864`](http://doi.org/10.1093/mnras/stab864)

(ref: Casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: corbel2013) Corbel, S., Coriat, M., Brocksopp, C., et al. 2013, MNRAS, 428, 2500, doi: [`10.1093/mnras/sts215`](http://doi.org/10.1093/mnras/sts215)

(ref: corbel2002) Corbel, S., & Fender, R. P. 2002, ApJL, 573, L35, doi: [`10.1086/341870`](http://doi.org/10.1086/341870)

(ref: Corbel2002Ejecta) Corbel, S., Fender, R. P., Tzioumis, A. K., et al. 2002, Science, 298, 196, doi: [`10.1126/science.1075857`](http://doi.org/10.1126/science.1075857)

(ref: coriat2011) Coriat, M., Corbel, S., Prat, L., et al. 2011, MNRAS, 414, 677, doi: [`10.1111/j.1365-2966.2011.18433.x`](http://doi.org/10.1111/j.1365-2966.2011.18433.x)

(ref: BlackCAT) Corral-Santana, J. M., Casares, J., Muñoz-Darias, T., et al. 2016, A&A, 587, A61, doi: [`10.1051/0004-6361/201527130`](http://doi.org/10.1051/0004-6361/201527130)

(ref: DeColle2020) De Colle, F., & Lu, W. 2020, New A Rev., 89, 101538, doi: [`10.1016/j.newar.2020.101538`](http://doi.org/10.1016/j.newar.2020.101538)

(ref: Draghis2023) Draghis, P. A., Miller, J. M., Homan, J., et al. 2023, The Astronomer’s Telegram, 16219, 1

(ref: Espinasse2020) Espinasse, M., Corbel, S., Kaaret, P., et al. 2020, ApJL, 895, L31, doi: [`10.3847/2041-8213/ab88b6`](http://doi.org/10.3847/2041-8213/ab88b6)

(ref: fender2010) Fender, R. 2010, in Lecture Notes in Physics, ed. T. Belloni, Vol. 794 (Berlin: Springer Verlag), 115, doi: [`10.1007/978-3-540-76937-85`](http://doi.org/10.1007/978-3-540-76937-85)

(ref: fender2019) Fender, R., & Bright, J. 2019, MNRAS, 489, 4836, doi: [`10.1093/mnras/stz2000`](http://doi.org/10.1093/mnras/stz2000)

(ref: Fender2019sscyg) Fender, R., Bright, J., Mooley, K., & Miller-Jones, J. 2019, MNRAS, 490, L76, doi: [`10.1093/mnrasl/slz145`](http://doi.org/10.1093/mnrasl/slz145)

(ref: Fender1999gx339quench) Fender, R., Corbel, S., Tzioumis, T., et al. 1999a, ApJL, 519, L165, doi: [`10.1086/312128`](http://doi.org/10.1086/312128)

(ref: tkat) Fender, R., Woudt, P. A., Corbel, S., et al. 2016, in MeerKAT Science: On the Pathway to the SKA, 13, doi: [`10.22323/1.277.0013`](http://doi.org/10.22323/1.277.0013)

(ref: fender2004) Fender, R. P., Belloni, T. M., & Gallo, E. 2004, MNRAS, 355, 1105, doi: [`10.1111/j.1365-2966.2004.08384.x`](http://doi.org/10.1111/j.1365-2966.2004.08384.x)

(ref: Fender1999) Fender, R. P., Garrington, S. T., McKay, D. J., et al. 1999b, MNRAS, 304, 865, doi: [`10.1046/j.1365-8711.1999.02364.x`](http://doi.org/10.1046/j.1365-8711.1999.02364.x)

(ref: fender2009) Fender, R. P., Homan, J., & Belloni, T. M. 2009, MNRAS, 396, 1370, doi: [`10.1111/j.1365-2966.2009.14841.x`](http://doi.org/10.1111/j.1365-2966.2009.14841.x)

(ref: gallo2018) Gallo, E., Degenaar, N., & van den Eijnden, J. 2018, MNRAS, 478, L132, doi: [`10.1093/mnrasl/sly083`](http://doi.org/10.1093/mnrasl/sly083)

(ref: gallo2003) Gallo, E., Fender, R. P., & Pooley, G. G. 2003, MNRAS, 344, 60, doi: [`10.1046/j.1365-8711.2003.06791.x`](http://doi.org/10.1046/j.1365-8711.2003.06791.x)

(ref: Garrington_2016) Garrington, S., & Beswick, R. 2016, Astronomy and Geophysics, 57, 3.28, doi: [`10.1093/astrogeo/atw101`](http://doi.org/10.1093/astrogeo/atw101)

(ref: Swift2004) Gehrels, N., Chincarini, G., Giommi, P., et al. 2004, ApJ, 611, 1005, doi: [`10.1086/422091`](http://doi.org/10.1086/422091)

(ref: Gottlieb2023) Gottlieb, O., Metzger, B. D., Quataert, E., et al. 2023, ApJL, 958, L33, doi: [`10.3847/2041-8213/ad096e`](http://doi.org/10.3847/2041-8213/ad096e)

(ref: Hardcastle2020) Hardcastle, M. J., & Croston, J. H. 2020, New A Rev., 88, 101539, doi: [`10.1016/j.newar.2020.101539`](http://doi.org/10.1016/j.newar.2020.101539)

(ref: oxkat2020) Heywood, I. 2020, oxkat: Semi-automated imaging of MeerKAT observations, Astrophysics Source Code Library, record ascl:2009.003. [`http://ascl.net/2009.003`](http://ascl.net/2009.003)

(ref: Heywood2016) Heywood, I., Jarvis, M. J., Baker, A. J., et al. 2016, MNRAS, 460, 4433, doi: [`10.1093/mnras/stw1250`](http://doi.org/10.1093/mnras/stw1250)

(ref: mightee) Heywood, I., Jarvis, M. J., Hale, C. L., et al. 2022, MNRAS, 509, 2150, doi: [`10.1093/mnras/stab3021`](http://doi.org/10.1093/mnras/stab3021)

(ref: Hjellming1988) Hjellming, R. M., & Johnston, K. J. 1988, ApJ, 328, 600, doi: [`10.1086/166318`](http://doi.org/10.1086/166318)

(ref: Hjellming1995) Hjellming, R. M., & Rupen, M. P. 1995, Nature, 375, 464, doi: [`10.1038/375464a0`](http://doi.org/10.1038/375464a0)

(ref: Jhoman2005) Homan, J., & Belloni, T. 2005, Ap&SS, 300, 107, doi: [`10.1007/s10509-005-1197-4`](http://doi.org/10.1007/s10509-005-1197-4)

(ref: polkatascl) Hughes, A. K., Cowie, F. J., Heywood, I., & Hugo, B. 2025, polkat: Semi-automate full polarization of MeerKAT observations, Astrophysics Source Code Library, record ascl:2502.026

(ref: ingram2019) Ingram, A. R., & Motta, S. E. 2019, New A Rev., 85, 101524, doi: [`10.1016/j.newar.2020.101524`](http://doi.org/10.1016/j.newar.2020.101524)

(ref: MeerKATCitation) Jonas, J., & MeerKAT Team. 2016, in MeerKAT Science: On the Pathway to the SKA, 1, doi: [`10.22323/1.277.0001`](http://doi.org/10.22323/1.277.0001)

(ref: Kalemci2022review) Kalemci, E., Kara, E., & Tomsick, J. A. 2022, in Handbook of X-ray and Gamma-ray Astrophysics, ed. C. Bambi & A. Sangangelo, 9, doi: [`10.1007/978-981-16-4544-0_100-1`](http://doi.org/10.1007/978-981-16-4544-0_100-1)

(ref: Kennea2023) Kennea, J. A., & Swift Team. 2023, GRB Coordinates Network, 34540, 1

(ref: Koljonen2015AGNXRBSpectra) Koljonen, K. I. I., Russell, D. M., Fernández-Ontiveros, J. A., et al. 2015, ApJ, 814, 139, doi: [`10.1088/0004-637X/814/2/139`](http://doi.org/10.1088/0004-637X/814/2/139)

(ref: BAT2013) Krimm, H. A., Holland, S. T., Corbet, R. H. D., et al. 2013, ApJS, 209, 14, doi: [`10.1088/0067-0049/209/1/14`](http://doi.org/10.1088/0067-0049/209/1/14)

(ref: kumar2015) Kumar, P., & Zhang, B. 2015, Phys. Rep., 561, 1, doi: [`10.1016/j.physrep.2014.09.008`](http://doi.org/10.1016/j.physrep.2014.09.008)

(ref: Liu2024) Liu, H.-X., Xu, Y.-J., Zhang, S.-N., et al. 2024, arXiv e-prints, arXiv:2406.03834, doi: [`10.48550/arXiv.2406.03834`](http://doi.org/10.48550/arXiv.2406.03834)

(ref: livio2002) Livio, M. 2002, Nature, 417, 125, doi: [`10.1038/417125a`](http://doi.org/10.1038/417125a)

(ref: longair2011) Longair, M. S. 2011, High Energy Astrophysics (Cambridge University Press)

(ref: Maccarone2020quench) Maccarone, T. J., Osler, A., Miller-Jones, J. C. A., et al. 2020, MNRAS, 498, L40, doi: [`10.1093/mnrasl/slaa120`](http://doi.org/10.1093/mnrasl/slaa120)

(ref: uvmultifit) Martı́-Vidal, I., Vlemmings, W. H. T., Muller, S., & Casey, S. 2014, A&A, 563, A136, doi: [`10.1051/0004-6361/201322633`](http://doi.org/10.1051/0004-6361/201322633)

(ref: Mata2024distance1727) Mata Sánchez, D., Muñoz-Darias, T., Armas Padilla, M., Casares, J., & Torres, M. A. P. 2024, A&A, 682, L1, doi: [`10.1051/0004-6361/202348754`](http://doi.org/10.1051/0004-6361/202348754)

(ref: Mata2025distance1727) Mata Sánchez, D., Torres, M. A. P., Casares, J., et al. 2025, A&A, 693, A129, doi: [`10.1051/0004-6361/202451960`](http://doi.org/10.1051/0004-6361/202451960)

(ref: MAXI2009) Matsuoka, M., Kawasaki, K., Ueno, S., et al. 2009, PASJ, 61, 999, doi: [`10.1093/pasj/61.5.999`](http://doi.org/10.1093/pasj/61.5.999)

(ref: mclintock2006) McClintock, J. E., & Remillard, R. A. 2006, Black hole binaries, Vol. 39 (Cambridge University Press), 157–213

(ref: Mereminskiy2024) Mereminskiy, I., Lutovinov, A., Molkov, S., et al. 2024, MNRAS, 531, 4893, doi: [`10.1093/mnras/stae1393`](http://doi.org/10.1093/mnras/stae1393)

(ref: migliari2010) Migliari, S., Tomsick, J. A., Miller-Jones, J. C. A., et al. 2010, ApJ, 710, 117, doi: [`10.1088/0004-637X/710/1/117`](http://doi.org/10.1088/0004-637X/710/1/117)

(ref: Migliori2017XTE1550) Migliori, G., Corbel, S., Tomsick, J. A., et al. 2017, MNRAS, 472, 141, doi: [`10.1093/mnras/stx1864`](http://doi.org/10.1093/mnras/stx1864)

(ref: maxigsc) Mihara, T., Nakajima, M., Sugizaki, M., et al. 2011, PASJ, 63, S623, doi: [`10.1093/pasj/63.sp3.S623`](http://doi.org/10.1093/pasj/63.sp3.S623)

(ref: millerjones2023b) Miller-Jones, J. C. A., Bahramian, A., Altamirano, D., et al. 2023a, The Astronomer’s Telegram, 16271, 1

(ref: millerjones2023a) Miller-Jones, J. C. A., Sivakoff, G. R., Bahramian, A., & Russell, T. D. 2023b, The Astronomer’s Telegram, 16211, 1

(ref: millerjones2019) Miller-Jones, J. C. A., Tetarenko, A. J., Sivakoff, G. R., et al. 2019, Nature, 569, 374, doi: [`10.1038/s41586-019-1152-0`](http://doi.org/10.1038/s41586-019-1152-0)

(ref: mirabel1994) Mirabel, I. F., & Rodrı́guez, L. F. 1994, Nature, 371, 46, doi: [`10.1038/371046a0`](http://doi.org/10.1038/371046a0)

(ref: eMCP) Moldon, J. 2018, in 14th European VLBI Network Symposium & Users Meeting (EVN 2018), 152

(ref: Offringa_AOFLAGGER) Offringa, A. R. 2010, AOFlagger: RFI Software. [`http://ascl.net/1010.017`](http://ascl.net/1010.017)

(ref: Pacholczyk1971Text) Pacholczyk, A. G., & Roberts, J. A. 1971, Physics Today, 24, 57, doi: [`10.1063/1.3022939`](http://doi.org/10.1063/1.3022939)

(ref: page2023) Page, K. L., Dichiara, S., Gropp, J. D., et al. 2023, GRB Coordinates Network, 34537, 1

(ref: Peng2024) Peng, J.-Q., Zhang, S., Shui, Q.-C., et al. 2024, ApJL, 960, L17, doi: [`10.3847/2041-8213/ad17ca`](http://doi.org/10.3847/2041-8213/ad17ca)

(ref: Peters2023VliteJ1727) Peters, W. M., Polisensky, E., Clarke, T. E., Giacintucci, S., & Kassim, N. E. 2023, The Astronomer’s Telegram, 16279, 1

(ref: Plotkin2013QS) Plotkin, R. M., Gallo, E., & Jonker, P. G. 2013, ApJ, 773, 59, doi: [`10.1088/0004-637X/773/1/59`](http://doi.org/10.1088/0004-637X/773/1/59)

(ref: Podgorny2024) Podgorny, J., Svoboda, J., & Dovciak, M. 2024, The Astronomer’s Telegram, 16541, 1

(ref: Polisensky2016VLITE) Polisensky, E., Lane, W. M., Hyman, S. D., et al. 2016, ApJ, 832, 60, doi: [`10.3847/0004-637X/832/1/60`](http://doi.org/10.3847/0004-637X/832/1/60)

(ref: ruiz2021) Ruiz, M., Shapiro, S. L., & Tsokaros, A. 2021, Frontiers in Astronomy and Space Sciences, 8, 39, doi: [`10.3389/fspas.2021.656907`](http://doi.org/10.3389/fspas.2021.656907)

(ref: rushton2017) Rushton, A. P., Miller-Jones, J. C. A., Curran, P. A., et al. 2017, MNRAS, 468, 2788, doi: [`10.1093/mnras/stx526`](http://doi.org/10.1093/mnras/stx526)

(ref: Russell2006LoLx) Russell, D. M., Fender, R. P., Hynes, R. I., et al. 2006, MNRAS, 371, 1334, doi: [`10.1111/j.1365-2966.2006.10756.x`](http://doi.org/10.1111/j.1365-2966.2006.10756.x)

(ref: Russell2010XTESpectra) Russell, D. M., Maitra, D., Dunn, R. J. H., & Markoff, S. 2010, MNRAS, 405, 1759, doi: [`10.1111/j.1365-2966.2010.16547.x`](http://doi.org/10.1111/j.1365-2966.2010.16547.x)

(ref: russel2013) Russell, D. M., Markoff, S., Casella, P., et al. 2013, MNRAS, 429, 815, doi: [`10.1093/mnras/sts377`](http://doi.org/10.1093/mnras/sts377)

(ref: Russel2024) Russell, T. D., Carotenuto, F., Miller-Jones, J. C. A., et al. 2024, The Astronomer’s Telegram, 16552, 1

(ref: russell2014) Russell, T. D., Soria, R., Miller-Jones, J. C. A., et al. 2014, MNRAS, 439, 1390, doi: [`10.1093/mnras/stt2498`](http://doi.org/10.1093/mnras/stt2498)

(ref: russell2019) Russell, T. D., Tetarenko, A. J., Miller-Jones, J. C. A., et al. 2019a, ApJ, 883, 198, doi: [`10.3847/1538-4357/ab3d36`](http://doi.org/10.3847/1538-4357/ab3d36)

(ref: russel2019) —. 2019b, ApJ, 883, 198, doi: [`10.3847/1538-4357/ab3d36`](http://doi.org/10.3847/1538-4357/ab3d36)

(ref: russel2020) Russell, T. D., Lucchini, M., Tetarenko, A. J., et al. 2020, MNRAS, 498, 5772, doi: [`10.1093/mnras/staa2650`](http://doi.org/10.1093/mnras/staa2650)

(ref: Sanchez2020maxi1820winds) Sánchez-Sierras, J., & Muñoz-Darias, T. 2020, A&A, 640, L3, doi: [`10.1051/0004-6361/202038406`](http://doi.org/10.1051/0004-6361/202038406)

(ref: miriad1995) Sault, R. J., Teuben, P. J., & Wright, M. C. H. 1995, in Astronomical Society of the Pacific Conference Series, Vol. 77, Astronomical Data Analysis Software and Systems IV, ed. R. A. Shaw, H. E. Payne, & J. J. E. Hayes, 433, doi: [`10.48550/arXiv.astro-ph/0612759`](http://doi.org/10.48550/arXiv.astro-ph/0612759)

(ref: Shahbaz2013SteepSpectra) Shahbaz, T., Russell, D. M., Zurita, C., et al. 2013, MNRAS, 434, 2696, doi: [`10.1093/mnras/stt1212`](http://doi.org/10.1093/mnras/stt1212)

(ref: Shapiro1976) Shapiro, S. L., Lightman, A. P., & Eardley, D. M. 1976, ApJ, 204, 187, doi: [`10.1086/154162`](http://doi.org/10.1086/154162)

(ref: Svoboda2024) Svoboda, J., Dovčiak, M., Steiner, J. F., et al. 2024, arXiv e-prints, arXiv:2403.04689, doi: [`10.48550/arXiv.2403.04689`](http://doi.org/10.48550/arXiv.2403.04689)

(ref: Tananbaum1972) Tananbaum, H., Gursky, H., Kellogg, E. M., et al. 1972, ApJL, 174, L143, doi: [`10.1086/180968`](http://doi.org/10.1086/180968)

(ref: Tetarenko2018b) Tetarenko, A. J., Freeman, P., Rosolowsky, E. W., Miller-Jones, J. C. A., & Sivakoff, G. R. 2018, MNRAS, 475, 448, doi: [`10.1093/mnras/stx3151`](http://doi.org/10.1093/mnras/stx3151)

(ref: atetarenko2017) Tetarenko, A. J., Sivakoff, G. R., Miller-Jones, J. C. A., et al. 2017, MNRAS, 469, 3141, doi: [`10.1093/mnras/stx1048`](http://doi.org/10.1093/mnras/stx1048)

(ref: btetarenko2016) Tetarenko, B. E., Sivakoff, G. R., Heinke, C. O., & Gladstone, J. C. 2016, ApJS, 222, 15, doi: [`10.3847/0067-0049/222/2/15`](http://doi.org/10.3847/0067-0049/222/2/15)

(ref: Thorne1975) Thorne, K. S., & Price, R. H. 1975, ApJL, 195, L101, doi: [`10.1086/181720`](http://doi.org/10.1086/181720)

(ref: vdl1966) van der Laan, H. 1966, Nature, 211, 1131, doi: [`10.1038/2111131a0`](http://doi.org/10.1038/2111131a0)

(ref: wood2021) Wood, C. M., Miller-Jones, J. C. A., Homan, J., et al. 2021, MNRAS, 505, 3393, doi: [`10.1093/mnras/stab1479`](http://doi.org/10.1093/mnras/stab1479)

(ref: Wood2024) Wood, C. M., Miller-Jones, J. C. A., Bahramian, A., et al. 2024, arXiv e-prints, arXiv:2405.12370, doi: [`10.48550/arXiv.2405.12370`](http://doi.org/10.48550/arXiv.2405.12370)

(ref: Wood2025SWJ1717Ejecta) —. 2025, arXiv e-prints, arXiv:2503.03073, doi: [`10.48550/arXiv.2503.03073`](http://doi.org/10.48550/arXiv.2503.03073)

(ref: Wenfei2023) Yu, W. 2023, The Astronomer’s Telegram, 16276, 1

[^1]: <https://github.com/AKHughes1994/polkat>

[^2]: MeerKAT’s synthesized beam becomes non-Gaussian for robustness weightings that would typically be used when maximizing for sensitivity (i.e., ${>}\,0$); non-Gaussian beam shapes can inhibit accurate deconvolution, thereby raising the image-plane noise.

[^3]: <https://github.com/e-merlin/eMERLIN_CASA_pipeline>

[^4]: The VLA programs used CASA version 6.2, 6.2, and 6.3 for project codes VLA/23A–260, VLA/22B–069, and Project code VLA/23B–064, respectively

[^5]: <https://lweb.cfa.harvard.edu/rtdc/SMAdata/process/mir/>

[^6]: <https://github.com/AKHughes1994/SwJ1727_2023_Outburst> with DOI:

</paper>

Write the methods card for this paper.