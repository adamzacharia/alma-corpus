# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...650A..37D\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...650A..37D",
 "title": "A search for signatures of interactions of X-ray binary outflows with their environments with ALMA",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Díaz Trigo, M.",
 "n_authors": 5,
 "arxiv_id": "2104.05384",
 "doi": "10.1051/0004-6361/202040160",
 "alma_projects_linked_by_archive": [
  "2016.1.00496.S"
 ]
}
```

Paper text:
<paper>
# A search for signatures of interactions of X-ray binary outflows with their environments with ALMA

# Introduction

Accretion onto stellar-mass black holes (BHs) and neutron stars (NSs) in X-ray binaries (XRBs) releases copious amounts of radiation into the interstellar medium (cite: frank92apia). X-ray binaries also show the two other fundamental ingredients of accretion onto compact objects: relativistic jets (cite: cygx1:stirling01mnras; scox1:fomalont01apj) and hot, dense winds (cite: gx13:ueda04apj; 1655:miller06nat; v404:munoz-darias16nature).

Given the similarity between accretion processes in XRBs and other compact objects, such as supermassive BHs, where radiation and outflows interact with their host galaxy (cite: mcnamara07araa; fabian12araa) and even regulate galaxy growth (cite: maiolino17nat), we also expect the XRB environments to be affected by the expelled material, energy, and momentum. As an example, jets are likely at the origin of the parsec-scale bubbles observed around ultra-luminous X-ray sources (cite: pakull10nature) that are generally identified with (extragalactic) XRBs containing NSs or stellar-mass BHs and accreting well above the Eddington limit, or, in a few cases, intermediate-mass BHs accreting at the Eddington limit. However, in our galaxy, and despite extensive searches for signatures of an interaction between XRB jets and the ISM (cite: miller-jones08aip), direct observational evidence of jet-inflated bubbles has only been reported in two cases (cite: ss433:dubner98aj; cygx1:gallo05nature; cygx1:russell07mnras); one of these two cases, SS 433, is the only known galactic ultra-luminous X-ray source (cite: ss433:begelman06mnras).

Recently, and following previous work by (cite: rodriguez98aa) and (cite: 1915:chaty01aa), (cite: 1915:tetarenko18mnras) searched for molecular line emission in the IRAS 19132+1035 region near the microquasar GRS 1915+105. They identified a zone with significant molecular line emission that could be traced back to a jet-ISM interaction but concluded that the jet did not appear to be powering the entire region. (cite: tetarenko20mnras) also reported a detection of molecular line emission in the central molecular zone coinciding with candidate jet-ISM interaction zones near the BH XRBs GRS  1758–258 and 1E 1740.7–2942 that may trace the cavities in the gas surrounding those systems. Importantly, all these works report on jet-ISM interactions taking place relatively far from the XRBs, at parsec scales.

At smaller scales (a few tens of AU), (cite: scox1:fomalont01apj) detected radio lobes dominated by compact hot spots along the jet direction of the NS XRB Sco X$-$1; they speculated that the radio lobes were generated at the working surface where the highly relativistic jet impacted the ambient medium. At even smaller scales, the effect of wide-angle X-ray winds from the accretion disc could become noticeable. Being dense ($\sim$10$^{12}$–10$^{13}$ cm$^{-3}$), relatively slow (with velocities of a few hundred km s$^{-1}$), and with estimated mass loss rates of 10$^{18}$–10$^{19}$ g s$^{-1}$(cite: gx13:ueda04apj; 1630:kubota07pasj; 1915:ueda09apj), such winds could have a significant impact close to the XRBs by sweeping up the ambient gas and compressing it. Alternatively, winds could cool, form cold clumps, and result in molecular outflows, at least in luminous quasars (cite: richings18mnras). However, to our knowledge, the effect of XRB winds in the ISM or their evolution as they leave the binary system has not yet been investigated.

While in terms of energetics XRB winds have been estimated to be less powerful than jets (cite: king13apj; fender16lnp), the wind power estimates suffer uncertainties related to the wind optical thickness, the spectral energy distribution that is illuminating it, and the portion of the wind that is invisible via X-ray spectroscopy due to being fully ionised (cite: diaz16an). Moreover, the duty cycle of winds is still uncertain, the question being whether they co-exist with jets throughout an accretion outburst (cite: 1915:neilsen09nat; homan16apj). If so, their duty cycle would be longer than that of jets, making the total energy deposited over time more similar for both output channels. Finally, the high collimation and speed of jets may make a significant energy deposit in their environments unlikely until they encounter a dense medium (cite: heinz02aa; miller-jones08aip) or are significantly decelerated (cite: 1550:corbel02science). In contrast, accretion disc winds may be more efficient at depositing energy in low density environments at sub-parsec scales due to their lower velocity and wide-angle geometry. In the end, the relative impact of jets, winds, and radiation will not only depend on their properties but also on the properties of the ISM where the XRBs reside. For example, (cite: haid18mnras) found that stellar winds couple more efficiently to the ISM than ionising radiation but that the relative impact of those winds and the ionising radiation is strongly dependent on the properties of the ambient medium.

We observed five XRBs at millimetre wavelengths with the Atacama Large Millimeter/submillimeter Array (ALMA) with the goal of exploring the existence of atomic and molecular line emission from their accretion discs, both close to the XRBs, where powerful X-ray and optical winds are expelled, and farther away, where there are known sites of jet-ISM interaction and where shocks are expected. For this exploratory study we chose a sample of persistently accreting sources that includes both NS and BH systems and both low- and high-mass stellar companions. All sources are known jet emitters, and strong wide-angle winds have been well studied for a subset of them. We targeted molecular lines that trace high density gas commonly found in shocks and atomic recombination lines. In this paper, we report on the results of these observations.

# Characteristics of the sample

## Cir X$-$1

Cir X$-$1 is the youngest known XRB, with an estimated age of $<$5400 years (cite: cirx1:heinz13apj). It is located at a distance of 9.4 $^{+0.8}_{-1.0}$ kpc (cite: cirx1:heinz15apj). It contains a star, the type of which remains in dispute (cite: cirx1:jonker07mnras; cirx1:johnston16mnras), that orbits a NS (cite: cirx1:tennant86mnras; linares10apj) in an eccentric orbit ($e \sim$ 0.4–0.45). Periodic flares at radio, infrared (IR), and X-ray frequencies every 16.6 d were interpreted as enhanced accretion close to periastron (cite: cirx1:murdin80aa; cirx1:nicolson80mnras). Radio observations at 5.5 and 9 GHz covering the full binary orbit showed that significant emission is present throughout the orbit, although the flux level is very low, $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$<$}}}$1 mJy, at phases outside periastron (cite: cirx1:calvelo12mnrasb). The same observations showed that the spectra evolve from optically thick to thin during the course of a flare, reaching already optical thinness by orbital phases of 0.05.

(cite: cirx1:calvelo12mnras) reported, for the first time, millimetre emission (at 33 and 35 GHz) during a periastron flare that had structures at sub-arcsecond scales (1$^{\prime\prime}$ corresponding to 0.04 pc at the distance of Cir X$-$1) and decayed over the following four days. A comparison of the structure of this emission with the radio emission resolved at milliarcsecond scales by (cite: miller-jones12mnras) revealed a change in the position angle of the elongated structure, which has a size of 185 AU and had been identified as the jet, suggesting that it could be precessing. Indeed, (cite: cirx1:coriat19mnras) successfully modelled the emission observed at different frequencies and angular scales from sub-arcsecond to arcminutes as a jet precessing over a five-year period and with mildly relativistic ejecta. Jets have also been observed in X-rays and are spatially coincident with the radio jets (cite: cirx1:heinz07apj; cirx1:sell10apj). The same X-ray observations show two diffuse X-ray caps that could be terminal shocks resulting from powerful jets running into the ISM (cite: cirx1:sell10apj). Besides the collimated jets, an accretion disc wind likely driven by thermal and radiation pressure has been inferred from the detection of X-ray P–Cygni profiles (cite: cirx1:brandt00apjl; cirx1:schulz02apj), and a stellar wind from the companion has been inferred from the detection of blueshifted X-ray emission lines at a different epoch (cite: cirx1:schulz20apj).

Cir X$-$1 is embedded in a radio nebula that extends over several parsecs (cite: haynes86nat) and is attributed to the supernova remnant at which Cir X$-$1 originated (cite: cirx1:heinz13apj). Although not at the origin of the nebula as initially suggested (cite: cirx1:stewart93mnras), there is increasing evidence that the precessing jets of Cir X$-$1 may be shaping it by injecting energy at different scales and in different directions over its five-year cycle (cite: cirx1:coriat19mnras).

## Sco X$-$1

At a distance of 2.8 $\pm$ 0.3 kpc (cite: bradshaw99apjl), Sco X$-$1 is the closest known ‘persistent’ NS XRB. It constantly radiates at or near Eddington luminosity and has a period of 0.787 days (cite: gottlieb75apj). (cite: steeghs02apj) performed high-resolution IR spectroscopy throughout 75% of the orbit of Sco X$-$1 and suggested that the companion star must be a significantly evolved subgiant with a radius of more than twice the main-sequence radius of 0.5 R$_\odot$ and a mass of $\sim$ 0.42 M$_\odot$. Radio emission from the source was first detected by (cite: andrew68nat). Measurements with the Very Large Baseline Array (VLBA) spanning three years revealed the existence of two components at $\sim$20–40 milliarcseconds of the radio core (corresponding to $\sim$20–170 AU at the distance of Sco X$-$1), which are moving away from it and are reminiscent of the hot spots found in many extragalactic radio double sources (cite: scox1:fomalont01apj). Their relative motion and flux densities implied an average component speed of $v/c$ = 0.45 $\pm$ 0.03 at 44$\pm$6$^{\circ}$ to the line of sight. (cite: scox1:fomalont01apj) suggested that the two radio components consisted of ultra-relativistic plasma produced at a working surface where the highly relativistic beams impacted the ambient medium.

Evidence of a high-velocity outflow was also reported at near-infrared (NIR) frequencies based on the detection of a P-Cygni profile in the Brackett $\gamma$ line of Sco X$-$1 (cite: gx13:bandyo99mnras). The existence of the Brackett $\gamma$ line was later confirmed, and its width was measured to be $\sim$ 480 km s$^{-1}$, consistent with that of H $\alpha$ (cite: scox1:matasanchez15mnras), although the P-Cygni profile indicative of a wind was not confirmed.

## GRS 1915+105

GRS 1915+105 is a low-mass XRB (LMXB) at a distance of 8.6 kpc (cite: 1915:reid14apj) that consists of a K$_{III}$ companion (cite: 1915:greiner01aa) orbiting a 12 M$_{\odot}$ BH with a period of 33.85 $\pm$ 0.16 days (cite: 1915:steeghs13apj). It was the first XRB to show episodic radio jets with apparently superluminal velocities (cite: 1915:mirabel94nature). Besides the episodic jets, a compact radio jet of 2.5–7 AU was resolved in observations at 15–43 GHz (cite: 1915:dhawan00apj).

(cite: rodriguez98aa) first studied the surroundings of GRS 1915+105 and investigated the possible relation of the XRB with two IR-to-radio sources that appear symmetrically located with respect to GRS 1915+105 and aligned with the position angle of the relativistic ejecta. They reported on a potential non-thermal structure in one of these regions, IRAS 19132+1035, that could be related to either a bow shock or an ionisation front. (cite: 1915:chaty01aa) explored these regions further and reported that the evidence for the non-thermal structure being a jet-ISM interaction zone was indecisive. A similar conclusion was reached by (cite: miller-jones08aip), who set upper limits to the presence of X-ray emission that could signal the presence of shock acceleration. Finally, (cite: 1915:tetarenko18mnras) re-observed the zone of significant molecular line emission and concluded instead that it could be traced back to a jet-ISM interaction but also that the jet did not appear to be powering the entire region.

Similarly to other LMXBs observed at high inclination, GRS 1915+105 also shows an accretion disc wind, observed via blueshifted absorption lines in X-ray spectra (cite: 1915:kotani00apj; 1915:lee02apj; 1915:ueda09apj). The wind is generally visible whenever the jet is absent (cite: 1915:neilsen09nat) and has been shown to react to changes in the broadband X-ray spectrum on timescales as short as 5 seconds (cite: 1915:neilsen11apj).

## GX 13+1

GX 13+1 is a NS LMXB (cite: gx13:fleischman85aa; gx13:matsuba95pasj) observed at a high inclination (cite: gx13:diaz12aa; gx13:iaria14aa). The companion star was identified as an evolved late-type K5 iii star, located at a distance of 7$\pm$1 kpc (cite: gx13:bandyo99mnras). An orbital period of 24.7 days was determined from IR and X-ray modulations (cite: gx13:bandyopadhyay02apj; gx13:corbet03apj; gx13:corbet10apj) and later refined to 24.5274(2) days based on the timing of X-ray dips (cite: gx13:iaria14aa). Radio emission at centimetre wavelengths was first detected by (cite: gx13:grindlay86apj). The similarity of the radio flux levels, spectral indices, and their variability with those of other NSs accreting at high Eddington luminosities was interpreted as an indication of the presence of relativistic jets (cite: gx13:garcia88apj; gx13:homan04aa).

In addition to jets, GX 13+1 shows narrow absorption lines in the X-ray band that have been interpreted as a wide-angle accretion disc wind outflowing at $\sim$ 400 km s$^{-1}$ (cite: gx13:ueda01apjl; gx13:sidoli02aa; gx13:ueda04apj; gx13:diaz12aa; gx13:madej14mnras; gx13:allen18apj). Evidence for a disc wind was also reported at NIR frequencies based on the presence of a Brackett $\gamma$ line with a P-Cygni profile that indicates an outflow velocity of $\sim$2400 km s$^{-1}$ (cite: gx13:bandyo99mnras).

The existence of an extended nebula surrounding the source similar to those of Cir X$-$1 (cite: haynes86nat) and Cyg X$-$1 (cite: cygx1:gallo05nature) has not been reported so far, and (cite: gx13:garcia88apj) attribute extended emission found in the area around GX 13+1 to unassociated galactic H$_{II}$ regions. They also set a 2$\sigma$ upper limit of 0.1 mJy at 6 cm and 1.0 mJy at 20 cm to the existence of Sco X$-$1-like lobes within 1$^\prime$ of GX 13+1 (equivalent to $\sim$2 pc at a distance of 7 kpc).

## Cyg X$-$1

Cyg X$-$1 is one of the best studied BH XRBs and the only confirmed high-mass XRB (HMXB) in our sample. The binary has a period of 5.6 days (cite: cygx1:holt79apj), was most likely born in the stellar association Cygnus OB3 (cite: cygx1:mirabel03science), and consists of a BH accreting from the stellar wind of a supergiant O9.7 star (cite: cygx1:webster72nat; cygx1:walborn73apj). At a distance of 2.22 $^{+0.18}_{-0.17}$ kpc, according to the most recent estimate with VLBA (cite: miller-jones21science), the BH would have a mass of 21.2 M$_{\odot}$. Cyg X$-$1 is one of the few persistently accreting BHs (GRS 1915+105 is another) and is predominantly in a spectrally hard accretion state (cite: grinberg13aa). During such a state, the spectrum between 2 and 220 GHz shows a flat spectral index (cite: cygx1:fender00mnras) and is attributed to a compact jet, resolved at milliarcsecond scales (cite: cygx1:stirling01mnras). The line-driven stellar wind, focused towards the BH (cite: cygx1:gies03apj), is clumpy (cite: cygx1:rahoui11apj; cygx1:hirsch19aa), dominates mass transfer, and is in turn affected by the X-rays of the BH (cite: cygx1:gies03apj; cygx1:gies08apj; cygx1:nowak11apj).

Cyg X$-$1 is the only source in our sample associated with a parsec-scale nebula detected in radio (cite: cygx1:gallo05nature) and bright in H$\alpha$ and \[O$_{III}$\] (5007 $\rm\AA$) emission (cite: cygx1:russell07mnras) that is thought to be inflated by the BH jet or the wind of the O star (cite: sell15mnras). Remarkably, the energy output of the O star wind is estimated to be of the order of that of the BH jet, indicating that, in addition to the two feedback channels considered here for XRBs (jets and accretion disc winds), stellar winds also have to be considered for HMXBs (we note that stellar winds from massive stars continue to be investigated as a source of feedback, and some authors even consider them to be more disruptive for molecular clouds than supernovae, e.g. (cite: reyraposo2017mnras); however, these investigations often do not consider the role of the compact object in shaping the stellar wind). Finally, the nebula around Cyg X$-$1 has an age similar to the time that the XRB was close to a bright H$_{II}$ region, indicating that a dense local medium may be required to form the shock wave (cite: cygx1:russell07mnras).

# Observations and data analysis

|  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Type | Compact | Orbital | Distance | Inclination | Observation date |
|  |  | object | period (d) | (kpc) | (degrees) |  |
| Cir X$-$1  | HMXB/LMXB? | NS | 16.6 | 9.4 | $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$>$}}}$70 | 23 Oct 2016 17:26 – 18:45 |
| Sco X$-$1  | LMXB | NS | 0.79 | 2.8 | $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$<$}}}$40 | 25 Oct 2016 16:50 – 17:38 |
| GRS 1915+105  | LMXB | BH | 33.8 | 8.6 | 66 $\pm$ 2 | 25 Oct 2016 17:41 – 18:23 |
| GX 13+1  | LMXB | NS | 24.5 | 7 | $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$>$}}}$70 | 05 Nov 2016 22:46 – 23:27 |
| Cyg X$-$1  | HMXB | BH | 5.6 | 2.22 | 27.1 $\pm$ 0.8 | 06 Nov 2016 21:02 – 22:02 |
|  |  |  |  |  |  | 29 Nov 2016 20:39 – 21:40 |
|  |  |  |  |  |  |  |

(cite: cirx1:jonker07mnras; cirx1:johnston16mnras)

(cite: cirx1:tennant86mnras; linares10apj)

(cite: cirx1:kaluzienski76apjl)

(cite: cirx1:heinz15apj)

From the presence of dips in its light curve (cite: cirx1:clarkson04mnras)

(cite: steeghs02apj)

(cite: gottlieb75apj)

(cite: bradshaw99apjl)

(cite: scox1:matasanchez15mnras)

(cite: 1915:greiner01aa)

(cite: greiner01nat)

(cite: 1915:steeghs13apj)

(cite: 1915:reid14apj)

(cite: gx13:fleischman85aa; gx13:matsuba95pasj)

(cite: gx13:bandyopadhyay02apj)

(cite: gx13:bandyo99mnras)

From the presence of dips in its light curve (cite: gx13:diaz12aa; gx13:iaria14aa)

(cite: cygx1:webster72nat)

(cite: cygx1:orosz11apj)

(cite: cygx1:holt79apj)

(cite: miller-jones21science)

ALMA observed the XRBs Cir X$-$1, Sco X$-$1, GRS 1915+105, GX 13+1, and Cyg X$-$1 from October to November 2016 (see Table [\[tab:obslog\]](#tab:obslog)). For these exploratory observations we only used the 12 m array due to its superior sensitivity and angular resolution, which was a better match for our search for weak and small regions of line emission. All observations were set up to use six spectral windows centred at 84.68117, 85.64439, 86.24337, 86.84696, 96.49964, 97.5, and 99.02295 GHz (Band 3). The characteristics of the spectral windows are listed in Table [\[tab:spwlog\]](#tab:spwlog). The observations were performed using a number of 12 m antennas, between 37 and 44, and maximum baseline lengths between 0.7 and 1.8 km. One pointing was performed in the direction of each source, and we performed additional pointings for Cir X$-$1 along the jet direction (a total of five pointings extending over a total of 189$^{\prime\prime}$$\times$63$^{\prime\prime}$ centred on the source; see Fig. [1](#fig:cirx_atca)) and for Cyg X$-$1 at the shell of the nebula surrounding it (a total of five pointings extending over 189$^{\prime\prime}$$\times$63$^{\prime\prime}$ and centred at position 19:57:55.0 +35:18:30.0; see Fig. [2](#fig:cygx_gallo)). Further technical characteristics of the observations are listed in Table [\[tab:obslog2\]](#tab:obslog2).

![](cirx1_wcontours.eps)

![](cygx1_wcontours.eps)

We first examined the ALMA calibrated products. Re-calibration for all datasets as well as image generation and analysis was done with CASA version 5.6.1-8 (cite: emonts19casa) and the integrated ALMA pipeline. We re-generated images from the calibrated products following standard procedures and applying natural weighting. We then applied phase-only self-calibration with solution intervals of 15, 90, 90, and 45 s for Cir X$-$1, Sco X$-$1, GRS 1915+105, and Cyg X$-$1, respectively. We did not apply self-calibration to GX 13+1 as we deemed it too faint. We found that self-calibration significantly improved the images, recovering $\sim$ 30–45% of the flux at the source position that was otherwise spread outside of one synthesised beam due to phase decoherence. We attribute this phase decoherence to the relatively poor ($\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$>$}}}$ 30$^{\circ}$) phase rms conditions during all the observations except for GX 13+1 (see Table [\[tab:obslog2\]](#tab:obslog2)). While ALMA antennas are equipped with water vapour radiometers, which are used to correct differential phase errors introduced by precipitable water vapour (PWV) over the array, this correction is less efficient in conditions of very low PWV, as is the case for our observations (for reference, the maximum PWV value required for Band 3 observations is 5.186 mm[^1]).

We also extracted data cubes at the spectral resolution of the cubes, $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$<$}}}$1 km s$^{-1}$, and inspected them for the presence of line emission. Unless otherwise indicated, the reported flux density for all sources in this paper corresponds to the peak flux from the elliptical Gaussian fitted to the source emission in the image plane after primary beam correction, and the error corresponds to the rms of the image measured far away from the source position.

|                           |                |           |            |     |     |
|:--------------------------|:---------------|:----------|:-----------|:----|:----|
| Line                      | Rest frequency | Bandwidth | Resolution | Spw |     |
|                           | (GHz)          | (MHz)     | (MHz)      |     |     |
| Upper Side Band           |                |           |            |     |     |
| H (40) $\alpha$           | 99.02295       | 937.5     | 0.488      | 0   |     |
| Continuum                 | 97.495         | 468.75    | 0.488      | 1   |     |
| H$_2$O v2=1 4(4,0)-5(3,3) | 96.49964       | 468.75    | 0.488      | 2   |     |
| Lower Side Band           |                |           |            |     |     |
| SiO v=1 2-1               | 86.24337       | 468.75    | 0.488      | 3   |     |
| SiO v=0 2-1               | 86.84696       | 468.75    | 0.488      | 4   |     |
| CH$_3$OH                  | 84.68628       | 468.75    | 0.488      | 5   |     |
| H (42) $\alpha$           | 85.64956       | 468.75    | 0.488      | 6   |     |
|                           |                |           |            |     |     |

+:--------------+:------+:-------------+:-------------+:-------------+:----------------+:-------------------+:-------------------+:---------------------+:-------+:--------------------------+
| Source        | ToS   | Calibrators                                | FoV                                  | Synthesised beam                          | PWV    | Phase rms                 |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
|               | \(s\) | Bandpass     | Flux         | Phase        | (arcsec)        | (parsec)           | (arcsec)           | (parsec)             | \(mm\) | before/after ($^{\circ}$) |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
| Cir X$-$1     | 4768  | J1617$-$5848 | Titan        | J1531$-$5108 | 63 $\times$ 189 | 2.87 $\times$ 8.61 | 0.67 $\times$ 0.63 | 0.030 $\times$ 0.029 | 1.5    | 63/29                     |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
| Sco X$-$1     | 2928  | J1517$-$2422 | Callisto     | J1629$-$1720 | 63 $\times$ 63  | 0.86 $\times$ 0.86 | 0.78 $\times$ 0.65 | 0.011 $\times$ 0.009 | 0.6    | 54/46                     |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
| GRS 1915+105  | 2527  | J1751+0939   | J1751+0939   | J1922+1530   | 63 $\times$ 63  | 2.63 $\times$ 2.63 | 1.44 $\times$ 0.63 | 0.060 $\times$ 0.026 | 0.5    | 32/24                     |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
| GX 13+1       | 2421  | J1924$-$2914 | J1924$-$2914 | J1832$-$2039 | 63 $\times$ 63  | 2.14 $\times$ 2.14 | 1.34 $\times$ 0.80 | 0.045 $\times$ 0.027 | 1.7    | 14/10                     |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
| Cyg X$-$1     | 7249  | J2025+3343   | J2148+0657   | J1953+3537   | 63 $\times$ 63  | 0.57 $\times$ 0.57 | 1.65 $\times$ 0.96 | 0.015 $\times$ 0.009 | 2.9    | 44/34                     |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+
|               |       |              |              |              |                 |                    |                    |                      |        |                           |
+---------------+-------+--------------+--------------+--------------+-----------------+--------------------+--------------------+----------------------+--------+---------------------------+

![](cont.eps)

# Results

We detected significant spatially unresolved continuum emission at the position of all the XRBs in our sample (see Fig. [3](#fig:cont_images) and Table [1](#tab:fluxlog)). The flux densities range from 0.7 to 13.7 mJy/beam, and the spectral index between 84 and 99 GHz is flat or inverted for all the sources except for Cir X$-$1.

In contrast, we did not detect line emission at the position of any source down to 3 $\sigma$ limits of 0.65 –3.7 K km s$^{-1}$ (see Table [2](#tab:linelog)). However, we did detect line emission at three different positions within the field of view of GX 13+1 (see Table [\[tab:lineloggx\]](#tab:lineloggx) and Fig. [4](#fig:gx13_composite)). This is the only source in the sample that shows line emission in its surroundings. Interestingly, we did not detect continuum emission down to noise levels of 30 $\mu$Jy/beam in any of the positions that show significant line emission. In addition, the lines have different spatial properties since one is spatially unresolved and the others are spatially resolved at scales of up to $\sim$6$^{\prime\prime}$ (see Figs. [5](#fig:line_images)–[7](#fig:line_maps2)).

|               |                  |                  |     |     |     |     |
|:--------------|:-----------------|:-----------------|:----|:----|:----|:----|
| Source        | Peak flux        | Spectral index   |     |     |     |     |
|               | (mJy/beam)       |                  |     |     |     |     |
| Cir X$-$1     | 13.69 $\pm$ 0.05 | -0.09 $\pm$0.01  |     |     |     |     |
| Sco X$-$1     | 2.48 $\pm$ 0.03  | -0.007$\pm$0.008 |     |     |     |     |
| GRS 1915+105  | 3.63 $\pm$ 0.04  | 0.015$\pm$0.008  |     |     |     |     |
| GX 13+1       | 0.75 $\pm$ 0.02  | 0.005$\pm$0.005  |     |     |     |     |
| Cyg X$-$1     | 5.69 $\pm$ 0.05  | -0.02 $\pm$ 0.01 |     |     |     |     |
|               |                  |                  |     |     |     |     |

: Flux densities of the continuum emission at the positions of the observed XRBs and spectral index, $\alpha$, between 85.764 and 97.878 GHz, where $F_\nu \propto \nu^{\alpha}$.

+:--------------+:----------------+:----------------+
| Source        | Line intensity (K km s$^{-1}$)    |
+---------------+-----------------+-----------------+
|               | Lower Side Band | Upper Side Band |
+---------------+-----------------+-----------------+
| Cir X$-$1     | $<$3.3          | $<$3.7          |
+---------------+-----------------+-----------------+
| Sco X$-$1     | $<$2.1          | $<$2.4          |
+---------------+-----------------+-----------------+
| GRS 1915+105  | $<$1.5          | $<$1.5          |
+---------------+-----------------+-----------------+
| GX 13+1       | $<$0.65         | $<$0.65         |
+---------------+-----------------+-----------------+
| Cyg X$-$1     | $<$1.0          | $<$1.0          |
+---------------+-----------------+-----------------+
|               |                 |                 |
+---------------+-----------------+-----------------+

: 3 $\sigma$ upper limits to line intensities at the position of the XRBs in the data cubes for the lower and upper side bands, with central frequencies of 85.764 and 97.878 GHz, respectively.

+:----------------+:------------+:------------+:-----------------+:---------------+:--+:--+:--+:--+
| Frequency range | Position                  | Peak temperature | Peak frequency |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+
| (GHz)           | RA (J2000)  | Dec (J2000) | (K km s$^{-1}$)  | (GHz)          |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+
| 86.2344–86.2369 | 18 14 30.35 | -17 09 01.0 | 340.8 $\pm$ 1.5  | 86.2362        |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+
| 96.7326–96.7333 | 18 14 33.13 | -17 09 50.9 | 8.3 $\pm$ 1.0    | 96.7329        |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+
| 99.2928–99.2940 | 18 14 33.12 | -17 09 50.9 | 10.4 $\pm$ 1.5   | 99.2933        |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+
| 99.2928–99.2940 | 18 14 30.38 | -17 09 33.3 | 5.0 $\pm$ 0.7    | 99.2938        |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+
|                 |             |             |                  |                |   |   |   |   |
+-----------------+-------------+-------------+------------------+----------------+---+---+---+---+

![](composite.eps)

![](mom0maps.eps)

![](96_chmaps.eps)

![](99_chmaps.eps)

# Discussion

Radio continuum emission at centimetre wavelengths was previously detected for all the XRBs in our sample and was identified with a jet origin. Emission up to at least $\sim$40 GHz has also been observed for all the sources except GX 13+1, for which reported detections span up to approximately 10 GHz. Given the previous measurements at lower frequencies and the spectral index of the emission at each accretion state of each source, the flux densities reported here are not unexpected. We give a detailed comparison for each source in Sect. [5.1](#sec:cont).

We also searched for line emission down to a spectral resolution of $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$<$}}}$ 1 km s$^{-1}$ at the positions of the XRBs and their surroundings. Water maser emission has been observed in the accretion discs of supermassive BHs (cite: humphreys13apj) and at the regions where their jets impact molecular clouds (cite: peck03apj). Given the similarities between accretion processes in XRBs and supermassive BHs, we would expect line emission to also be present in XRBs. While the upper limits to the presence of lines in our observations are quite stringent, all the observations showed continuum emission from the jet, which at the same time may hinder the detection of disc lines. Alternatively, strong line emission may only become significant over the continuum in the presence of flares. For example, (cite: 1915:eikenberry98apjl) identified the NIR He$_{I}$ and Brackett $\gamma$ emission lines in GRS 1915+105 as arising in the accretion disc and found that their flux varied proportionally with the IR continuum flux, indicating that the lines were radiatively pumped by the flares. In this sense, our observations show relatively weak jet emission compared to the radio flares observed up to Jansky levels in these sources during other periods, such as changes of accretion state. For comparison, the Brackett $\gamma$ emission line reported by (cite: 1915:eikenberry98apjl) is only $\sim$ 5 mJy above the continuum when the continuum is 40 mJy, but it brightens to $\sim$ 10 mJy above the continuum when the continuum increases up to 60 mJy (see their Fig. 1).

As opposed to the positions of the XRBs, continuum emission is unlikely to be the reason for not detecting line emission near the XRBs and at the regions close to Cir X$-$1 and Cyg X$-$1, where evidence for jet-ISM interaction had previously been observed. A potential reason for the lack of lines is that the lines are weak or extend over large regions. For comparison, the molecular lines of SiO and CH$_3$OH reported by (cite: 1915:tetarenko18mnras; tetarenko20mnras) and traced back to jet-ISM interactions have temperatures generally below 0.6 K km s$^{-1}$ and are extended over relatively large regions, at near-arcminute scales. Therefore, they would not be detected in our observations, which reached sensitivities of 0.6–4 K km s$^{-1}$ (see Table [2](#tab:linelog)) and could only recover angular scales up to $\sim$15$^{\prime\prime}$. Another potential reason could be that the medium that the jet or the wind is propagating through has a low density compared to the average ISM density, $\sim$1 cm$^{-3}$. Based on the observation of GRS 1915+105 jet ejections travelling at a constant speed to distances of at least $\sim$0.04 pc (cite: 1915:mirabel94nature; fender99mnras; 1915:miller-jones07mnras) and on jet energetic arguments, (cite: heinz02aa) estimated that the density around this XRB was $\sim$10$^{-3}$ cm$^{-3}$ (unless the jets were narrower than 0.15$^{\circ}$ or extremely energetic, 10$^{47}$ ergs). They suggested that the region around GRS 1915+105 was occupied by the hot ISM phase or that previous activity of the jets (or the supernova at which the progenitor formed) could have created an evacuated bubble around it. Interestingly, (cite: haid18mnras) found that, in the warm ionised ISM, stellar winds dominate the momentum injection when compared to ionising radiation for massive stars. Therefore, in LMXBs, accretion disc winds could provide an alternative to stellar winds for creating a cavity around the XRB or as a source of momentum injection in a previously evacuated bubble. A dedicated study considering the ratio of wind to XRB ionising radiation is needed to advance further on this topic.

Finally, while the shocked region around Cir X$-$1, between 20 and 50$^{\prime\prime}$ from the source (corresponding to $\sim$0.9–2.3 pc at the distance of the source), was found to be bright in diffuse X-rays and radio emission (cite: cirx1:sell10apj), we did not detect any continuum emission in the same areas down to noise levels of 45 $\mu$Jy/beam (but we note that we cannot exclude emission at the low level of $\sim$24 $\mu$Jy/beam that was detected in the previous radio observations at 5.5 GHz). In contrast to Cir X$-$1, the shocked emission region around Cyg X$-$1 is bright in H$\alpha$ and O$_{III}$ emission and in 1.4 GHz radio continuum emission and is located at the rim of a jet-inflated nebula of $\sim$5 pc in diameter (cite: cygx1:gallo05nature; cygx1:russell07mnras). However, our continuum maps again show no significant emission (noise level of 40 $\mu$Jy/beam) in the region where the ring in radio emission at 1.4 GHz was previously observed at a flux level of 0.2 mJy/beam. A potential reason for the non-detection of the continuum in this case may be a spatial extent larger than that recoverable with our observations, $\sim$15$^{\prime\prime}$ (0.16 pc at the distance of Cyg X$-$1).

In summary, we found neither continuum nor line emission that could signal the presence of shocks at regions near the probed XRBs, including regions around Cir X$-$1 and Cyg X$-$1 where evidence for jet-ISM interaction had been previously observed. However, we also note that many of the molecular tracers of jet-ISM interactions, such as the shock tracer CS or the high-density tracers HNCO or HCO+, remain unexplored for the sources of this study. Nevertheless, we discovered three different line emission features in the field of view of GX 13+1 that could signal the presence of a yet unknown star-forming region, albeit one probably unrelated to GX 13+1. We discuss these features in detail in Sect. [5.2](#sec:linegx).

## Continuum emission from a jet

### Cir X$-$1

Using the ephemeris in (cite: cirx1:nicolson07atel) derived from the onset times of 21 well-observed radio flares spanning the past 28 years, the ALMA observation occurred at phase $\sim$0.08. This is $\sim$6 days later than the X-ray peak detected in the Monitor of All-Sky X-ray Image (MAXI) light curves between Modified Julian Date (MJD) 57675.5 and 57677.5, and it is consistent with previous observations that indicated that the radio flares occur later in the orbit compared to the X-ray flares.

We detected significant continuum emission with a peak flux of 13.69 $\pm$ 0.05 mJy/beam and a spectral index of – 0.09 $\pm$ 0.01 between 84 and 99 GHz. The emission is unresolved, implying a region of emission smaller than $\sim$10$^{17}$ cm for the reported beam of 0.67$^{\prime\prime}$ $\times$ 0.63$^{\prime\prime}$ and the distance of the source. In observations performed with the Australian Telescope Compact Array (ATCA) at a resolution of 0.44$^{\prime\prime}$ $\times$ 0.23$^{\prime\prime}$ and frequencies of 33 and 35 GHz, extended emission was reported on two different occasions (cite: cirx1:calvelo12mnras; cirx1:coriat19mnras). The flux in our observations is stronger than that previously reported at 33–35 GHz at the core ($\sim$7 and 0.7 mJy/beam). If the extension of the emission had been similar to that reported at 33-35 GHz, we would have detected it despite our slightly poorer resolution. Thus, we conclude that our non-detection of extended emission is more likely related to the higher frequency of our observations since the extension of the emission significantly decreases as the frequency increases (cite: cirx1:coriat19mnras).

This source is the only one in our sample that shows a negative spectral index. This indicates optically thin emission, and it is consistent both with previous radio measurements at similar orbital phases that were interpreted as the decline of a periastron passage flare (cite: cirx1:calvelo12mnras) and with the flux decay observed in the light curve of the ALMA observation (see Fig. [8](#fig:cirx1lc)).

![](cirx1lc.eps)

### Sco X$-$1

We detected unresolved emission with a flux density of 2.48 mJy/beam and a flat spectral index between 84 and 99 GHz at the position of Sco X$-$1. Previous emission from lobes moving away from the core, such as those detected by (cite: scox1:fomalont01apj), occurred at milliarcsecond scales (1 mas corresponding to 2.8 AU at the distance of Sco X$-$1) and would not have been resolved at the resolution of our images (see Table [\[tab:obslog2\]](#tab:obslog2)). However, the flat spectral index indicates that we are most likely detecting core-only (or core-dominated) emission since the lobe emission always had negative spectral indices, as expected from optically thin emission (cite: scox1:fomalont01apj). Based on a timing analysis of contemporaneous X-ray observations, (cite: scox1:motta19mnras) associated the launch of the ultra-relativistic outflows causing the lobe emission with particular accretion states (between the so-called ‘normal’ and ‘horizontal’ branches). We produced X-ray colour-colour diagrams with data from MAXI (see Appendix [7](#sec:app1)) and found that, at the time of the ALMA observations, the source was instead at the so-called ‘flaring branch’, a state associated with the weakest and least variable radio emission (cite: scox1:hjellming90apj). The flux level detected by ALMA is of the order of the fluxes detected at such a state by (cite: scox1:hjellming90apj) between 1 and 8 GHz and with flat spectral index, although they also detected additional components during the same state with a negative spectral index. In conclusion, our detection is consistent with the jet emission extending from centimetre to millimetre wavelengths with a flat spectral index during the flaring branch, although simultaneous measurements at both wavelengths are needed to confirm this.

### GRS 1915+105

We detected spatially unresolved emission with a flux density of 3.63 mJy/beam and a slightly inverted spectral index between 84 and 99 GHz at the position of GRS 1915+105. Based on MAXI colour-colour diagrams, we infer that, at the time of the ALMA observations (see Appendix [7](#sec:app1)), the source was most likely in the ‘A’ or ‘B’ state, according to the classification of (cite: 1915:belloni00aa), characterised by a substantial contribution of a disc component to the X-ray spectrum and low-level radio emission. (cite: 1915:klein-wolt02mnras) associated the radio emission during those states with either a hard component or a relic from a previous large radio event. The low flux density of the ALMA observation within this accretion state is consistent with a relatively radio-quiet period during that state.

### GX 13+1

We detected, for the first time, compact continuum emission at a frequency of 92 GHz from GX 13+1. The flux density at centimetre wavelengths ranges from $\sim$0.25 mJy/beam to $\sim$1.3–7.2 mJy/beam and is correlated with the accretion state of the source as determined from X-ray observations (cite: gx13:garcia88apj; gx13:homan04aa). The ALMA observations indicate a flux of 0.75 $\pm$ 0.02 mJy/beam, in between the two ranges. The spectral index is flat, similar to that observed at radio frequencies during states with weak radio emission.

### Cyg X$-$1

The second observation of Cyg X$-$1, based on hardness-intensity diagrams extracted from MAXI data (see Appendix [7](#sec:app1)), was performed during a spectrally hard state. While the MAXI light curves do not cover the date of the first observation, we conclude, based on the similarity of the hardness and intensity before and after that observation, that the accretion state most likely did not change between the two observations. Our detection of continuum emission with a flat spectral index is consistent with previous findings of a flat spectra from radio to millimetre wavelengths and attributed to a compact jet (cite: cygx1:fender00mnras).

## Line emission in the field of view of GX 13+1

Similarly to all the other observed sources, no spectral lines were observed at the position of GX 13+1. In contrast, we detected three different line emission features in its field of view.

The strongest feature was observed 27$^{\prime\prime}$ north-west (NW) of GX 13+1 at a frequency of 86.2361 GHz (see Table [\[tab:lineloggx\]](#tab:lineloggx) and Fig. [5](#fig:line_images)). We tentatively identified the line with emission from vibrationally excited SiO (v=1, J=2-1) with a redshift of 25 km s$^{-1}$. The emission is spatially unresolved, implying an emission size of less than 8 $\times$ 10$^{16}$ cm assuming the source is at a similar distance as GX 13+1 (i.e. 7 kpc). Assuming the line identification is correct and that its shift is not intrinsic to the source but is instead due to its position in the galaxy, we obtain 2.5 and 13.3 kpc as near and far kinematic distances, implying emission sizes of less than $\sim$5 $\times$ 10$^{16}$ cm and $\sim$3 $\times$ 10$^{17}$ cm, respectively.

We found a source coincident with the position of the line in the galactic young stellar object (YSO) catalogue of (cite: marton19cat), which was produced by running a supervised machine learning algorithm on the combined data from the Gaia DR2 database, the Wide-field Infrared Survey Explorer (WISE), and Planck. The source coincident with the SiO emission, J181430.35-170901.0, has a 57% and 42% probability of being a YSO or an evolved star, respectively, when all the WISE bands are used, and a 43% and 55% probability if WISE bands W3 and W4 are neglected. SiO masers are uncommon in star-forming regions (cite: zapata09apj), with only six reported detections in YSOs so far (cite: cho16apj). Additionally, if the SiO maser is associated with a star-forming region, we would expect to detect continuum emission in the ALMA maps unless the region is quite distant. For reference, a one-solar-mass core would have a flux of 0.3 mJy if placed at the near kinematic distance of 2.5 kpc, thus easily detectable in our maps (for this estimate we considered a $\sim$20 K dust temperature, the typically adopted dust opacity, and a gas-to-dust mass ratio of 100, and we assumed that the emission at 90 GHz was optically thin). Conversely, assuming the source of the SiO to be an evolved star at a distance of 2.5 kpc, we estimate, following calculations by (cite: muller07apj; muller08apj), a stellar flux of $\sim$25 $\mu$Jy/beam and a dust envelope flux of $\sim$65 $\mu$Jy/beam for a mass loss rate of $\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$>$}}}$6 $\times$10$^{-6}~M_\odot$ at 90 GHz. Therefore, our 3$\sigma$ upper limit of 90 $\mu$Jy/beam indicates that our maps are not sensitive enough to detect the combined flux of the star and the dust envelope of a typical evolved star such as W Hya, for which a mass loss rate of 4.9 $\times$ 10$^{-7}~M_\odot$ within a radius of about 70 AU has been derived (cite: vlemmings11apj). Consequently, an evolved star origin for the SiO line remains a viable solution. Alternatively, if the source is relatively far ($\mathrel{\hbox{\rlap{\lower.55ex \hbox {$\sim$}}
        \kern-.3em \raise.4ex \hbox{$>$}}}$4 kpc), both a YSO and an evolved star remain possibilities. Further observations of the detected line and of other SiO transitions at a higher angular resolution are necessary to confirm the maser nature of the emission and the line identification.

In addition to the potential SiO maser NW of GX 13+1, we also detected spatially extended line emission with a frequency of $\sim$99.2935 GHz at 12$^{\prime\prime}$ south-west (SW) and 38$^{\prime\prime}$ south-east (SE) of GX 13+1. If associated with H(40) $\alpha$, the line has a blueshift of 820 km s$^{-1}$ or, if associated with SO, a redshift of 18 km s$^{-1}$. At the SE position, we detected a second line with a frequency of 96.7329 GHz. If associated with H$_2$O, the line has a blueshift of 725 km s$^{-1}$ or, if associated, with CH$_3$OH, a redshift of 20 km s$^{-1}$. The spatial coincidence of two lines at the SE position indicates that a similar redshift of 18–20 km s$^{-1}$ for the lines, and thus an identification with SO and CH$_3$OH, is more plausible. The detection of the same line in the SE and SW positions may indicate that both regions are also related.

Given the uncertain origin of the SiO emission (YSO or evolved star) and the occurrence of CH$_3$OH and SO molecules in regions of star formation (cite: oberg14fa; li15apjl; aikawa20apj), we searched for the signature of a parent molecular cloud in archival millimetre single-dish images that would indicate the existence of such a star-forming region, thus linking the three line emission regions. None of the positions were detected in the ATLASGAL survey at 850 $\mu$m with a noise level of 50 mJy/beam (but we note the coarse resolution of this survey, 20$^{\prime\prime}$) nor in the James Clerk Maxwell Telescope (JCMT) continuum maps at the same wavelength. This excludes the existence of at least an OB star cluster in this region and is consistent with the absence of any continuum detection in our images down to an rms of 30 $\mu$Jy/beam. We also inspected the images of the *Spitzer* MIPSGAL 24 $\mu$m (cite: carey09pasp) and GLIMPSE 8 $\mu$m (cite: churchwell09pasp) surveys (see Fig. [9](#fig:mipsgal)). The source coincident with the SiO emission, J181430.35-170901.0, is clearly visible at micrometre wavelengths in both images. It is also apparent that the positions of GX 13+1 and the line detections SE and SW of GX 13+1 are instead located in a relatively dark area in the MIPSGAL 24 $\mu$m image, suggesting that no dust is present in that region. This is consistent with the absence of significant CO (3-2) emission in the JCMT/HARPS 345 GHz map (project code: M10AU20) of the same region (see Fig. [10](#fig:jcmt)), although we note that the cavity, or ‘dark’ region, surrounding GX 13+1 in the MIPSGAL image is significantly smaller than that of the CO (3-2) map. The existence of such a dark region around GX 13+1 could suggest a link between the XRB and the line emission regions, but this possibility remains speculative at this stage. Finally, we note that an old 20 cm image of the region (cite: gx13:garcia88apj) seems to show emission at the position of GX 13+1 and the SE line emission region at a level of $\sim$1 mJy but no emission at the NW or SW positions. Additionally, a 6 cm Very Large Array (VLA) image in August 1999 covering the region of the ALMA observation down to an rms of 50 $\mu$Jy/beam only shows significant radio emission at the position of GX 13+1.

![](test2.eps)

![](jcmt_co_cutout.eps)

In summary, the field of view of GX 13+1 shows a set of features of which the strongest (SiO) is best interpreted in the context of an evolved star or a star-forming region that is currently unknown or has not been detected in continuum emission to date. The origin of the other features remains unexplained.

# Summary and conclusions

We observed five XRBs at millimetre wavelengths with ALMA with the goal of exploring the existence of atomic and molecular line emission from their accretion discs, both close to the XRBs, where powerful X-ray and optical winds are expelled, and farther away, where sites of jet-ISM interaction are known and shocks are expected. All the sources show continuum emission consistent with a jet origin and previous observations below 40 GHz. In contrast, our exploratory search for line emission only resulted in upper limits at the position of all sources and at the sites near Cir X$-$1 and Cyg X$-$1, where previous signatures of jet-ISM interaction had been detected. Further searches for disc lines could specifically target either accretion states during which no, or only weak, jet emission is detected or, alternatively, states during which bright flares could pump line emission. Instead, searches for lines in the XRB environments should be complemented with searches of line emission at arcminute angular scales and target additional lines.

Interestingly, the field of view of GX 13+1 shows a set of features whose origin remains enigmatic. While the strongest feature (SiO) can be interpreted as originating in an evolved star, it is better interpreted (if it is related to the other two line emission regions) in the context of a star-forming region that is currently unknown or has not yet been detected in continuum emission. An association of these features with GX 13+1 remains speculative at this stage. Follow-up observations of CO at higher sensitivities could help us understand whether the sites of emission are related and shed light on the nature of this region. This should be complemented with observations of other transitions of the candidate molecules to confirm line identification.

# Acknowledgements

We thank the anonymous referee for a very useful report that helped to improve the quality of this paper. We also thank Mickael Coriat for providing the radio maps for Cir X$-$1 and Elena Gallo and Dave Russell for those of Cyg X$-$1. MDT thanks Yuxin Lin for help in producing figure 9. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00496.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

118 natexlab

(ref: aikawa20apj) Aikawa, Y., Furuya, K., Yamamoto, S., & Sakai, N. 2020, ApJ, 897, 110

(ref: gx13:allen18apj) Allen, J. L., Schulz, N. S., Homan, J., et al. 2018, ApJ, 861, 26

(ref: andrew68nat) Andrew, B. H. & Purton, C. R. 1968, Nature, 218, 855

(ref: gx13:bandyopadhyay02apj) Bandyopadhyay, R. M., Charles, P. A., Shahbaz, T., & Wagner, R. M. 2002, ApJ, 570, 793

(ref: gx13:bandyo99mnras) Bandyopadhyay, R. M., Shahbaz, T., Charles, P. A., & Naylor, T. 1999, MNRAS, 306, 417

(ref: ss433:begelman06mnras) Begelman, M. C., King, A. R., & Pringle, J. E. 2006, MNRAS, 370, 399

(ref: 1915:belloni00aa) Belloni, T., Klein-Wolt, M., Méndez, M., van der Klis, M., & van Paradijs, J. 2000, A&A, 355, 271

(ref: bradshaw99apjl) Bradshaw, C. F., Fomalont, E. B., & Geldzahler, B. J. 1999, ApJL, 512, L121

(ref: cirx1:brandt00apjl) Brandt, W. N. & Schulz, N. S. 2000, ApJL, 544, L123

(ref: cirx1:calvelo12mnras) Calvelo, D. E., Fender, R. P., Tzioumis, A. K., & Broderick, J. W. 2012a, MNRAS, 419, L54

(ref: cirx1:calvelo12mnrasb) Calvelo, D. E., Fender, R. P., Tzioumis, A. K., et al. 2012b, MNRAS, 419, 436

(ref: carey09pasp) Carey, S. J., Noriega-Crespo, A., Mizuno, D. R., et al. 2009, PASP, 121, 76

(ref: 1915:chaty01aa) Chaty, S., Rodrı́guez, L. F., Mirabel, I. F., et al. 2001, A&A, 366, 1035

(ref: cho16apj) Cho, S.-H., Yun, Y., Kim, J., et al. 2016, ApJ, 826, 157

(ref: churchwell09pasp) Churchwell, E., Babler, B. L., Meade, M. R., et al. 2009, PASP, 121, 213

(ref: cirx1:clarkson04mnras) Clarkson, W. I., Charles, P. A., & Onyett, N. 2004, MNRAS, 348, 458

(ref: 1550:corbel02science) Corbel, S., Fender, R. P., Tzioumis, A. K., et al. 2002, Science, 298, 196

(ref: gx13:corbet03apj) Corbet, R. H. D. 2003, ApJ, 595, 1086

(ref: gx13:corbet10apj) Corbet, R. H. D., Pearlman, A. B., Buxton, M., & Levine, A. M. 2010, ApJ, 719, 979

(ref: cirx1:coriat19mnras) Coriat, M., Fender, R. P., Tasse, C., et al. 2019, MNRAS, 484, 1672

(ref: 1915:dhawan00apj) Dhawan, V., Mirabel, I. F., & Rodrı́guez, L. F. 2000, ApJ, 543, 373

(ref: diaz16an) Dı́az Trigo, M. & Boirin, L. 2016, Astronomische Nachrichten, 337, 368

(ref: gx13:diaz12aa) Dı́az Trigo, M., Sidoli, L., Boirin, L., & Parmar, A. N. 2012, A&A, 543, A50

(ref: ss433:dubner98aj) Dubner, G. M., Holdaway, M., Goss, W. M., & Mirabel, I. F. 1998, AJ, 116, 1842

(ref: 1915:eikenberry98apjl) Eikenberry, S. S., Matthews, K., Murphy, T. W., J., et al. 1998, ApJL, 506, L31

(ref: emonts19casa) Emonts, B., Raba, R., Moellenbrock, G., et al. 2019, arXiv e-prints, arXiv:1912.09437

(ref: fabian12araa) Fabian, A. C. 2012, ARA&A, 50, 455

(ref: fender16lnp) Fender, R. & Muñoz-Darias, T. 2016, The Balance of Power: Accretion and Feedback in Stellar Mass Black Holes, ed. F. Haardt, V. Gorini, U. Moschella, A. Treves, & M. Colpi, Vol. 905, 65

(ref: fender99mnras) Fender, R. P., Garrington, S. T., McKay, D. J., et al. 1999, MNRAS, 304, 865

(ref: cygx1:fender00mnras) Fender, R. P., Pooley, G. G., Durouchoux, P., Tilanus, R. P. J., & Brocksopp, C. 2000, MNRAS, 312, 853

(ref: gx13:fleischman85aa) Fleischman, J. R. 1985, A&A, 153, 106

(ref: scox1:fomalont01apj) Fomalont, E. B., Geldzahler, B. J., & Bradshaw, C. F. 2001, ApJ, 558, 283

(ref: frank92apia) Frank, J., King, A. R., & Raine, D. J. 1992, Accretion power in astrophysics (Cambridge and New York, Cambridge University Press)

(ref: cygx1:gallo05nature) Gallo, E., Fender, R., Kaiser, C., et al. 2005, Nature, 436, 819

(ref: gx13:garcia88apj) Garcia, M. R., Grindlay, J. E., Molnar, L. A., et al. 1988, ApJ, 328, 552

(ref: cygx1:gies08apj) Gies, D. R., Bolton, C. T., Blake, R. M., et al. 2008, ApJ, 678, 1237

(ref: cygx1:gies03apj) Gies, D. R., Bolton, C. T., Thomson, J. R., et al. 2003, ApJ, 583, 424

(ref: gottlieb75apj) Gottlieb, E. W., Wright, E. L., & Liller, W. 1975, ApJL, 195, L33

(ref: greiner01nat) Greiner, J., Cuby, J. G., & McCaughrean, M. J. 2001a, Nature, 414, 522

(ref: 1915:greiner01aa) Greiner, J., Cuby, J. G., McCaughrean, M. J., Castro-Tirado, A. J., & Mennickent, R. E. 2001b, A&A, 373, L37

(ref: grinberg13aa) Grinberg, V., Hell, N., Pottschmidt, K., et al. 2013, A&A, 554, A88

(ref: gx13:grindlay86apj) Grindlay, J. E. & Seaquist, E. R. 1986, ApJ, 310, 172

(ref: haid18mnras) Haid, S., Walch, S., Seifried, D., et al. 2018, MNRAS, 478, 4799

(ref: hasinger89aa) Hasinger, G. & van der Klis, M. 1989, A&A, 225, 79

(ref: haynes86nat) Haynes, R. F., Komesaroff, M. M., Little, A. G., et al. 1986, Nature, 324, 233

(ref: heinz02aa) Heinz, S. 2002, A&A, 388, L40

(ref: cirx1:heinz15apj) Heinz, S., Burton, M., Braiding, C., et al. 2015, ApJ, 806, 265

(ref: cirx1:heinz07apj) Heinz, S., Schulz, N. S., Brandt, W. N., & Galloway, D. K. 2007, ApJL, 663, L93

(ref: cirx1:heinz13apj) Heinz, S., Sell, P., Fender, R. P., et al. 2013, ApJ, 779, 171

(ref: cygx1:hirsch19aa) Hirsch, M., Hell, N., Grinberg, V., et al. 2019, A&A, 626, A64

(ref: scox1:hjellming90apj) Hjellming, R. M., Stewart, R. T., White, G. L., et al. 1990, ApJ, 365, 681

(ref: cygx1:holt79apj) Holt, S. S., Kaluzienski, L. J., Boldt, E. A., & Serlemitsos, P. J. 1979, ApJ, 233, 344

(ref: homan16apj) Homan, J., Neilsen, J., Allen, J. L., et al. 2016, ApJL, 830, L5

(ref: gx13:homan04aa) Homan, J., Wijnands, R., Rupen, M. P., et al. 2004, A&A, 418, 255

(ref: humphreys13apj) Humphreys, E. M. L., Reid, M. J., Moran, J. M., Greenhill, L. J., & Argon, A. L. 2013, ApJ, 775, 13

(ref: gx13:iaria14aa) Iaria, R., Di Salvo, T., Burderi, L., et al. 2014, A&A, 561, A99

(ref: cirx1:johnston16mnras) Johnston, H. M., Soria, R., & Gibson, J. 2016, MNRAS, 456, 347

(ref: cirx1:jonker07mnras) Jonker, P. G., Nelemans, G., & Bassa, C. G. 2007, MNRAS, 374, 999

(ref: cirx1:kaluzienski76apjl) Kaluzienski, L. J., Holt, S. S., Boldt, E. A., & Serlemitsos, P. J. 1976, ApJL, 208, L71

(ref: king13apj) King, A. L., Miller, J. M., Raymond, J., et al. 2013, ApJ, 762, 103

(ref: 1915:klein-wolt02mnras) Klein-Wolt, M., Fender, R. P., Pooley, G. G., et al. 2002, MNRAS, 331, 745

(ref: 1915:kotani00apj) Kotani, T., Ebisawa, K., Dotani, T., et al. 2000, ApJ, 539, 413

(ref: 1630:kubota07pasj) Kubota, A., Dotani, T., Cottam, J., et al. 2007, PASJ, 59, 185

(ref: 1915:lee02apj) Lee, J. C., Reynolds, C. S., Remillard, R., et al. 2002, ApJ, 567, 1102

(ref: li15apjl) Li, J., Wang, J., Zhu, Q., Zhang, J., & Li, D. 2015, ApJ, 802, 40

(ref: linares10apj) Linares, M., Watts, A., Altamirano, D., et al. 2010, ApJL, 719, L84

(ref: gx13:madej14mnras) Madej, O. K., Jonker, P. G., Dı́az Trigo, M., & Miškovičová, I. 2014, MNRAS, 438, 145

(ref: maiolino17nat) Maiolino, R., Russell, H. R., Fabian, A. C., et al. 2017, Nature, 544, 202

(ref: marton19cat) Marton, G., Abraham, P., Szegedi-Elek, E., et al. 2019, VizieR Online Data Catalog, II/360

(ref: scox1:matasanchez15mnras) Mata Sanchez, D., Munoz-Darias, T., Casares, J., et al. 2015, MNRAS, 449, L1

(ref: gx13:matsuba95pasj) Matsuba, E., Dotani, T., Mitsuda, K., et al. 1995, PASJ, 47, 575

(ref: mcnamara07araa) McNamara, B. R. & Nulsen, P. E. J. 2007, ARA&A, 45, 117

(ref: 1655:miller06nat) Miller, J. M., Raymond, J., Fabian, A., et al. 2006, Nature, 441, 953

(ref: miller-jones08aip) Miller-Jones, J., Kaiser, C., Maccarone, T., et al. 2008, in American Institute of Physics Conference Series, Vol. 1010, A Population Explosion: The Nature & Evolution of X-ray Binaries in Diverse Environments, ed. R. M. Bandyopadhyay, S. Wachter, D. Gelino, & C. R. Gelino, 50–56

(ref: miller-jones21science) Miller-Jones, J. C. A., Bahramian, A., Orosz, J. A., et al. 2021, arXiv e-prints, arXiv:2102.09091

(ref: miller-jones12mnras) Miller-Jones, J. C. A., Moin, A., Tingay, S. J., et al. 2012, MNRAS, 419, L49

(ref: 1915:miller-jones07mnras) Miller-Jones, J. C. A., Rupen, M. P., Fender, R. P., et al. 2007, MNRAS, 375, 1087

(ref: cygx1:mirabel03science) Mirabel, I. F. & Rodrigues, I. 2003, Science, 300, 1119

(ref: 1915:mirabel94nature) Mirabel, I. F. & Rodriguez, L. F. 1994, Nature, 371, 46

(ref: scox1:motta19mnras) Motta, S. E. & Fender, R. P. 2019, MNRAS, 483, 3686

(ref: v404:munoz-darias16nature) Muñoz-Darias, T., Casares, J., Mata Sánchez, D., et al. 2016, Nature, 534, 75

(ref: muller08apj) Muller, S., Dinh-V-Trung, He, J.-H., & Lim, J. 2008, ApJL, 684, L33

(ref: muller07apj) Muller, S., Dinh-V-Trung, Lim, J., et al. 2007, ApJ, 656, 1109

(ref: cirx1:murdin80aa) Murdin, P., Jauncey, D. L., Haynes, R. F., et al. 1980, A&A, 87, 292

(ref: 1915:neilsen09nat) Neilsen, J. & Lee, J. C. 2009, Nature, 458, 481

(ref: 1915:neilsen11apj) Neilsen, J., Remillard, R. A., & Lee, J. C. 2011, ApJ, 737, 69

(ref: cirx1:nicolson07atel) Nicolson, G. D. 2007, The Astronomer’s Telegram, 985, 1

(ref: cirx1:nicolson80mnras) Nicolson, G. D., Glass, I. S., & Feast, M. W. 1980, MNRAS, 191, 293

(ref: cygx1:nowak11apj) Nowak, M. A., Hanke, M., Trowbridge, S. N., et al. 2011, ApJ, 728, 13

(ref: oberg14fa) Öberg, K. I., Fayolle, E. C., Reiter, J. B., & Cyganowski, C. 2014, Faraday Discussions, 168, 81

(ref: cygx1:orosz11apj) Orosz, J. A., McClintock, J. E., Aufdenberg, J. P., et al. 2011, ApJ, 742, 84

(ref: pakull10nature) Pakull, M. W., Soria, R., & Motch, C. 2010, Nature, 466, 209

(ref: peck03apj) Peck, A. B., Henkel, C., Ulvestad, J. S., et al. 2003, ApJ, 590, 149

(ref: cygx1:rahoui11apj) Rahoui, F., Lee, J. C., Heinz, S., et al. 2011, ApJ, 736, 63

(ref: 1915:reid14apj) Reid, M. J., McClintock, J. E., Steiner, J. F., et al. 2014, ApJ, 796, 2

(ref: reyraposo2017mnras) Rey-Raposo, R., Dobbs, C., Agertz, O., & Alig, C. 2017, MNRAS, 464, 3536

(ref: richings18mnras) Richings, A. J. & Faucher-Giguère, C.-A. 2018, MNRAS, 474, 3673

(ref: rodriguez98aa) Rodriguez, L. F. & Mirabel, I. F. 1998, A&A, 340, L47

(ref: cygx1:russell07mnras) Russell, D. M., Fender, R. P., Gallo, E., & Kaiser, C. R. 2007, MNRAS, 376, 1341

(ref: cirx1:schulz02apj) Schulz, N. S. & Brandt, W. N. 2002, ApJ, 572, 971

(ref: cirx1:schulz20apj) Schulz, N. S., Kallman, T. E., Heinz, S., et al. 2020, ApJ, 891, 150

(ref: cirx1:sell10apj) Sell, P. H., Heinz, S., Calvelo, D. E., et al. 2010, ApJL, 719, L194

(ref: sell15mnras) Sell, P. H., Heinz, S., Richards, E., et al. 2015, MNRAS, 446, 3579

(ref: gx13:sidoli02aa) Sidoli, L., Parmar, A. N., Oosterbroek, T., & Lumb, D. 2002, A&A, 385, 940

(ref: steeghs02apj) Steeghs, D. & Casares, J. 2002, ApJ, 568, 273

(ref: 1915:steeghs13apj) Steeghs, D., McClintock, J. E., Parsons, S. G., et al. 2013, ApJ, 768, 185

(ref: cirx1:stewart93mnras) Stewart, R. T., Caswell, J. L., Haynes, R. F., & Nelson, G. J. 1993, MNRAS, 261, 593

(ref: cygx1:stirling01mnras) Stirling, A. M., Spencer, R. E., de la Force, C. J., et al. 2001, MNRAS, 327, 1273

(ref: cirx1:tennant86mnras) Tennant, A. F., Fabian, A. C., & Shafer, R. A. 1986, MNRAS, 221, 27P

(ref: 1915:tetarenko18mnras) Tetarenko, A. J., Freeman, P., Rosolowsky, E. W., Miller-Jones, J. C. A., & Sivakoff, G. R. 2018, MNRAS, 475, 448

(ref: tetarenko20mnras) Tetarenko, A. J., Rosolowsky, E. W., Miller-Jones, J. C. A., & Sivakoff, G. R. 2020, MNRAS, 497, 3504

(ref: gx13:ueda01apjl) Ueda, Y., Asai, K., Yamaoka, K., Dotani, T., & Inoue, H. 2001, ApJL, 556, L87

(ref: gx13:ueda04apj) Ueda, Y., Murakami, H., Yamaoka, K., Dotani, T., & Ebisawa, K. 2004, ApJ, 609, 325

(ref: 1915:ueda09apj) Ueda, Y., Yamaoka, K., & Remillard, R. 2009, ApJ, 695, 888

(ref: vlemmings11apj) Vlemmings, W. H. T., Humphreys, E. M. L., & Franco-Hernández, R. 2011, ApJ, 728, 149

(ref: cygx1:walborn73apj) Walborn, N. R. 1973, ApJL, 179, L123

(ref: cygx1:webster72nat) Webster, B. L. & Murdin, P. 1972, Nature, 235, 37

(ref: zapata09apj) Zapata, L. A., Menten, K., Reid, M., & Beuther, H. 2009, ApJ, 691, 332

# Hardness-intensity diagrams

Figure [11](#fig:maxihid) shows the hardness-intensity and colour-colour diagrams from MAXI data used to determine the accretion states of Sco X$-$1, GRS 1915+105, and Cyg X$-$1 at the time of the ALMA observations. Based on the colour-colour diagrams (cite: hasinger89aa), we infer that the Sco X$-$1 observation was performed in the flaring branch. With only the MAXI data we cannot infer a state classification for GX 13+1 since no branches are distinguishable in the respective diagrams, as in, for example, (cite: homan16apj). For Cyg X$-$1 we instead used the hardness-intensity diagram and followed the classification from (cite: grinberg13aa) to infer that it was in a spectrally hard state. Finally, for GRS 1915+105 we used the colour-colour diagram and the classification from (cite: 1915:belloni00aa) and classify the ALMA observation as occurring during the A or B states.

![image](scox1_hid.eps) ![image](scox1_cc.eps) ![image](grs_hid.eps) ![image](grs_cc.eps) ![image](gx13_hid.eps) ![image](gx13_cc.eps) ![image](cygx1_hid.eps) ![image](cygx1_cc.eps)

[^1]: Remijan, A., Biggs, A., Cortes, P., A., Dent, B., Di Francesco, J., Fomalont, E., Hales, A., Kameno, S., Mason, B., Philips, N., Saini, K., Stoehr, F., Vila Vilaro, B., Villard, E. 2019, ALMA Technical Handbook, ALMA Doc. 7.3, ver. 1.1

</paper>

Write the methods card for this paper.