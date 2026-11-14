# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...652A..66P\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...652A..66P",
 "title": "ALMA multiline survey of the ISM in two quasar host-companion galaxy pairs at z &gt; 6",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Pensabene, A.",
 "n_authors": 18,
 "arxiv_id": "2105.09958",
 "doi": "10.1051/0004-6361/202039696",
 "alma_projects_linked_by_archive": [
  "2015.1.01115.S",
  "2017.1.00139.S",
  "2019.1.00147.S"
 ]
}
```

Paper text:
<paper>
# An ALMA multi-line survey of the ISM in two quasar host–companion galaxy pairs at $z>6$

# Introduction

Quasars (or QSOs) beyond redshift $z\sim 6$ (when the age of the Universe was less than $1\,{\rm Gyr}$) are the most luminous non-transient sources in the Universe, and are believed to be the progenitors of present-day early-type massive galaxies. The very high luminosities ($L_{\rm bol} > 10^{13}L_{\astrosun}$) from their active nuclei (AGN) are powered by rapid accretion of matter ($> 10\,M_{\astrosun}\,{\rm yr^{-1}}$) onto central supermassive black holes (BHs, $M_{\rm BH}\apprge 10^{8}\,M_{\astrosun}$; (cite: Jiang+2007; DeRosa+2011; Mazzucchelli+2017)) and often accompanied by rapid consumption of huge gas reservoirs through vigorous episodes of star formation (${\rm SFR} > 100\,M_{\astrosun}\,{\rm yr^{-1}}$; see e.g. (cite: Bertoldi+2003b; Bertoldi+2003a; Walter+2003; Walter+2009nat; Venemans+2018)). Therefore, the host galaxies of $z>6$ quasars are ideal laboratories to characterize the physical properties of the interstellar medium (ISM) in such extreme conditions, and they provide crucial insights on the interplay between star formation and black hole accretion in massive galaxies emerging from cosmic dawn.

The redshift $z>6$ range is of particular interest as galaxies emerge from the last phase transition of the Universe, marked by a rapid shift in the ionization properties of the intergalactic medium (cite: Fan+2006; Becker+2015). Thanks to the efforts of various groups using wide field surveys (see e.g. (cite: Fan+2006b), (cite: Banados+2016; Jiang+2016; Matsuoka+2018), and references therein), $\sim 200$ quasars have been discovered at $z>6$, including the three most distant quasars known at $z>7.5$ (cite: Banados+2018; YangJ+2020; Wang+2021). The very presence of such BHs at these early epochs requires rapid build-up of black holes and galaxy assembly, challenging our understanding of how BHs form in the first place (cite: Volonteri2012; Sijacki+2015; Habouzit+2019; vanderVlugt+2019).

Models and numerical simulations of massive black hole formation predicts that $z>6$ quasars reside the extreme peaks of the large-scale density structure (cite: Begelman+2006; Overzier+2009; Bonoli+2009; Bonoli+2014; Angulo+2012; Costa+2014), and therefore, $z>6$ quasars can be used to identify the first galaxy overdensities – however the question whether there are in fact overdensities of galaxies around $z\sim6$ quasars is contested – (cite: Overzier+2009; Morselli+2014; Balmaverde+2017; Farina+2017; Mazzucchelli+2017b; Decarli+2019b). On smaller scale ($\sim 100 \,{\rm pkpc}$), the exceptional sensitivity and imaging power of the Atacama Large (sub-)Millimeter Array (ALMA) has allowed us to image the dust and cold gas reservoir of galaxies in the early Universe, leading to strong evidence of overdensities around $z>5-6$ quasars (cite: Decarli+2017; Trakhtenbrot+2017; Willott+2017; Neeleman+2019; Venemans+2019), supported by the intriguingly serendipitous discoveries of starburst and sub-millimeter galaxies (SMGs) in the close environment of the quasars, with high star formation rate (${\rm SFR} > 500-1000\,M_{\astrosun}\,{\rm yr^{-1}}$) and showing no evidence of BH accretion ((cite: Decarli+2017; Mazzucchelli+2019); but see also (cite: Connor+2019; Connor+2020; Vito+2019) for tentative evidence of X-ray emission from these companions).

In this context, these quasar host–companion galaxy pairs represent unique testing ground to study star formation, AGN feedback and structure growth in galaxies at $z>6$. Multi-line surveys of the ISM in these systems provide key diagnostics of the physical properties of the ISM, including densities, and the source of the powering radiation field (cite: CarilliWalter2013). For high-redshift galaxies, many atomic and molecular far-infrared (FIR) emission lines fall in the (sub-)mm bands, thus making them accessible to sensitive ground-based facilities such as ALMA or the Northern Extended Millimeter Array (NOEMA). Indeed, previous studies detected galaxy dust continuum and gas emission lines even in highest redshift quasars. These studies have mainly targeted the brightest emitters such as the fine-structure line (FSL) of singly-ionized carbon \[CII\]$_{\rm 158\mu m}$, and the rotational transitions of carbon monoxide (cite: Walter+2003; Walter+2004; Walter+2009nat; Maiolino+2005; Maiolino+2009; Maiolino+2015; Wang+2010; Wang+2013; Willott+2015mbh; Willott+2015; Gallerani+2014; Carniani+2017; Carniani+2019; Decarli+2017; Decarli+2018; Venemans+2017b; Venemans+2017c; Venemans+2017a; Venemans+2019; Feruglio+2018), and have revealed the ubiquitous presence of massive cold gas ($M_{\rm gas}\apprge 10^{10}\,M_{\astrosun}$) and dust ($M_{\rm dust}\apprge 10^{9}\,M_{\astrosun}$) reservoirs in high-$z$ quasar host galaxies. Indeed, \[CII\]$_{\rm 158\mu m}$ and the low-/mid-$J$ CO transitions (rotational quantum number of the CO molecule upper levels $J_{\rm up}< 7-8$) are the major coolants of the atomic and molecular ISM, respectively. The C$^+$ ion has an ionization potential energy slightly lower than that of atomic hydrogen (H), thus it traces both the atomic neutral and ionized phase of the ISM, and its $158\,{\rm \mu m}$ transition arises predominantly from photodissociation regions (PDRs, see (cite: Hollenbach+1999) for a review) at the interface between the atomic and molecular media in the outskirts of molecular clouds in galaxy star-forming regions (cite: Diaz-Santos+2017). On the other hand, the CO is the most abundant molecule of the ISM after H$_2$, and requires little energy to be excited, thus its low- and mid-$J$ upper levels can be easily populated by collisions with H$_2$. It is thus representing the best observational tracer of cold molecular ISM embedded in clouds (with a hydrogen density of $n_{\rm H}\sim 10^{3}\,{\rm cm^{-3}}$, and a kinetic gas temperature of $T<100\,{\rm K}$).

Multiple atomic FSLs and molecular transitions arising from different ISM phases provide both direct and indirect information on the ionized phase in the proximity of young (O and B) stars (e.g. the doubly-ionized oxygen \[OIII\]$_{\rm 88\mu m}$ and the singly-ionized nitrogen \[NII\]$_{\rm 122\mu m,\,205\mu m}$) or the denser and warm phases buried in the cores of molecular clouds (such e.g. the high-$J$ CO, the water vapor H$_2$O, and the hydroxyl and its anion (hydroxide) OH, OH$^+$, rotational transitions). Recent studies have started to probe such diagnostics in few $z>6$ systems (cite: Riechers+2009; Riechers+2013; Strandet+2017; Venemans+2017c; Venemans+2017a; Walter+2018; Hashimoto+2019a; Hashimoto+2019b; Novak+2019; WangF+2019; YangJ+2019; Li+2020b; Li+2020).

This work is focused on the ISM characterization of two $z>6$ quasar host galaxies, at $z\sim6.59$, and at $z\sim6.24$, and the nearby companions which were serendipitously discovered with ALMA (cite: Decarli+2017; Neeleman+2019). These companions are among the most star-forming galaxies known to date (with \[CII\]–based ${\rm SFR} \apprge 200-500\,M_{\astrosun}\,{\rm yr^{-1}}$) at $z>6$ that do not show evidence of AGN activity in the rest-frame optical/UV (cite: Decarli+2017; Mazzucchelli+2019) and in the X-rays (cite: Connor+2019; Connor+2020). For these objects, the \[CII\]$_{\rm 158\mu m}$ line and dust continuum have been clearly detected with previous ALMA observations (cite: Decarli+2017), while higher-resolution \[CII\]$_{\rm 158\mu m}$ follow-up observations have allowed study of their kinematics (cite: Decarli+2019; Neeleman+2019). The companion galaxies in the two systems, have a projected separation of $\sim 8.5\,{\rm kpc}$ and $\sim 14\,{\rm kpc}$, with a velocity offset of $+137\,{\rm km\,s^{-1}}$ and $+591\,{\rm km\,s^{-1}}$ for PJ231-20 and PJ308-21, respectively. Remarkably, the \[CII\]$_{\rm 158\mu m}$ emission of the companion galaxy in PJ308-21 system, stretches over about $25\,{\rm kpc}$ and $>1500\,{\rm km\,s^{-1}}$ towards and beyond the quasar host suggesting that the satellite galaxy is tidally stripped by the interaction with the central quasar host galaxy (cite: Decarli+2017; Decarli+2019). Furthermore, in both PJ231-20 and PJ308-21 systems, Ly$\alpha$ nebular emission have been recently discovered (cite: Farina+2019), possibly indicating that also PJ231-20 quasar recently underwent a merger event with the close companion galaxy.

Here we present ALMA band 3–6 observations of the PJ231-20 and PJ308-21 systems, in which we sampled the FIR dust continuum and various emission lines probing different ISM phases and conditions; including the FSLs of the singly-ionized atomic nitrogen \[NII\]$_{\rm 205\mu m}$, and the neutral carbon \[CI\]$_{\rm 369\mu m}$, tracers of the low-density fully ionized medium (electron density $n_{\rm e} \apprle 1\,{\rm cm^{-3}}$), and the cold dense atomic phase of the ISM ($n_{\rm H}\sim 10^3\,{\rm cm^{-3}}$), respectively. We also present observations of the molecular transitions of CO at intermediate and high-$J$ (7–6, 10–9, 15–14, 16–15), three water vapor (ortho-)H$_2$O rotational transitions ($3_{12}-2_{21}$, $3_{21}-3_{12}$, $3_{03}-2_{12}$) and the hydroxyl molecule OH$_{\rm 163\mu m}$ doublet associated with the warm dense phase of the ISM ($n_{\rm H}\apprge 10^5\,{\rm cm^{-3}}$, $T>100\,{\rm K}$). Combining the different information and making use of radiative transfer models, we study a variety of dust and gas-phase ISM physical properties in the quasar hosts and companion galaxies, allowing to discriminate line excitation by star formation and AGN processes. This study aims to provide an overview of the complex conditions of the multiphase ISM in galaxies at $z\sim6$.

+:----------------------------------------------------------------------------+:--------------------:+:--------------------:+:--------------------:+:--------------------:+:-------------------------:+:-------------------------:+
| Object ID                                                                   | **PJ231-20**                                                                              | **PJ308-21**                                          |
+-----------------------------------------------------------------------------+---------------------------------------------+---------------------------------------------+---------------------------+---------------------------+
|                                                                             | **QSO**                                     | **companion $^{(\star)}$**                  | **QSO**                   | **companion**             |
+-----------------------------------------------------------------------------+---------------------------------------------+---------------------------------------------+---------------------------+---------------------------+
| 1-7 R.A. (J2000.0)                                                          | 15h 26m 37.84s                              | 15h 26m 37.87s                              | 20h 32m 10.00s            | 20h 32m 10.17s            |
+-----------------------------------------------------------------------------+---------------------------------------------+---------------------------------------------+---------------------------+---------------------------+
| DEC. (J2000.0)                                                              | $-20^{\circ}\,50'\,0.8''$                   | $-20^{\circ}\,50'\,2.3''$                   | $-21^{\circ}\,14'\,2.4''$ | $-21^{\circ}\,14'\,2.7''$ |
+-----------------------------------------------------------------------------+---------------------------------------------+---------------------------------------------+---------------------------+---------------------------+
| redshift $^{(1)}$                                                           | $6.58651\pm0.00017$                         | $6.5900\pm0.0008$                           | $6.2342\pm0.0010$         | $6.2485\pm0.0005$         |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| **Frequency setup** $^{(2)}$                                                | A                    | B                    | C                    | D                    | A                         | D                         |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| 1-7 Band                                                                    | 3                    | 4                    | 5                    | 6                    | 3                         | 6                         |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| Central frequency (GHz) $^{(3)}$                                            | 99.755               | 146.456              | 199.350              | 234.397              | 104.901                   | 245.870                   |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| Time on source (min)                                                        | 33.82                | $19.70$              | $28.27$              | 8.72                 | 41.97                     | $39.83$                   |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| Array configuration                                                         | C43-4                | C43-2, C43-3         | C43-2                | C43-2                | C43-4                     | C43-2                     |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| No. antennas                                                                | $43$                 | $48$                 | $48$                 | $45$                 | 48                        | $44$                      |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| Baselines (m)                                                               | $15-1547$            | $15-500$             | $15-360$             | $15-483$             | $15-783$                  | $15-455$                  |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| Beam (${\rm arcsec^2}$) $^{(4)}$                                            | $0''.99\times0''.89$ | $1''.49\times1''.22$ | $1''.76\times1''.14$ | $1''.10\times1''.01$ | $1''.32\times1''.13$      | $1''.19\times0''.97$      |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| RMS cont. (${\rm mJy\,beam^{-1}}$)                                          | $0.011$              | $0.019$              | $0.029$              | $0.042$              | $0.009$                   | $0.015$                   |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| $\left\langle{\rm RMS}\right\rangle$ cube (${\rm mJy\,beam^{-1}}$) $^{(5)}$ | $0.24$               | $0.27$               | $0.47$               | $0.48$               | $0.19$                    | $0.20$                    |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+
| Observation date                                                            | 2019 Oct 6           | 2018 Apr 23          | 2018 Jun 4           | 2018 Aug 21          | 2019 Oct 14               | 2018 Aug 12               |
+-----------------------------------------------------------------------------+----------------------+----------------------+----------------------+----------------------+---------------------------+---------------------------+

Table notes: $^{(1)}$Redshift of ${\rm [CII]_{158\mu m}}$ line from (cite: Decarli+2017). $^{(2)}$Setup A refers to ALMA Cycle 7 data, while setup C, B and D refer to Cycle 5 data. $^{(3)}$Central frequency of the entire frequency setup. $^{(4)}$Beam sizes are those from the natural maps. $^{(5)}$Averaged RMS sensitivity over the entire bandwidth of the cubes (channel width of $40\,{\rm km\,s^{-1}}$). $^{(\star)}$We note that (cite: Neeleman+2019) found two companions in the PJ231-20 ALMA field located at south and south-est of the QSO. However, our observations do not allow us to spatially resolved both the sources. In this work we assume that the bulk of the emission from companion galaxies, arises from the source located at the south of the central PJ231-20 QSO, that is reported in (cite: Decarli+2017) and denoted with ’C’ in (cite: Neeleman+2019) work.

The paper is organized as follows: in Sect. [2](#sect:data_reduction) we present the ALMA observations and we describe the reduction of the data. In Sect. [3](#sect:data_presentation) we outline the analysis conducted on the calibrated data and we report FIR line emission and continuum measurements in the sources of the PJ231-20 and PJ308-21 systems. In Sect. [4](#sect:cloudy_modeling) we describe the set-up and the outputs of our CLOUDY models. In Sect. [5](#ssect:dust) we present and discuss the results obtained from the dust continuum. Then, we dedicate Sect. [6](#sect:ionized_medium) to the tracers of the ionized medium and the results obtained from them, while in Sect. [7](#sect:atomic_medium) we focused on the atomic medium and we put constraints on its physical properties. Afterward, in Sect. [8](#ssect:molecular_medium) we study the molecular phase of the ISM through the analysis of the CO, H$_2$O and OH lines. In Sect. [9](#sect:mass_contributions) we estimate the various mass budgets of the different gas components. Finally, in the last Sect. [10](#sect:conclusions) we summarize our results and we draw the conclusions.

Throughout the paper we assume a standard $\Lambda\rm{CDM}$ cosmology with $H_0=69.3\,\si{km\,s^{-1}Mpc^{-1}}$, $\Omega_{m}=0.287$, $\Omega_{\Lambda}=1-\Omega_{m}$ from (cite: Hinshaw+2013).

+-----------------------------------------------------------------+-----------------------------------+-----------------------+
| **Covered emission lines**                                      | **Rest frequency (GHz) $^{(1)}$** | **setup ID $^{(2)}$** |
+:================================================================+:=================================:+:=====================:+
| 1-3 CO($7-6$)                                                   | 806.652                           | A                     |
+-----------------------------------------------------------------+-----------------------------------+                       |
| ${\rm [CI]_{369\mu m}}$                                         | 809.342                           |                       |
+-----------------------------------------------------------------+-----------------------------------+-----------------------+
| 1-3 CO($10-9$)                                                  | 1151.985                          | B                     |
+-----------------------------------------------------------------+-----------------------------------+                       |
| ${\rm H_{2}O}\;3_{12}-2_{21}$                                   | 1153.127                          |                       |
+-----------------------------------------------------------------+-----------------------------------+                       |
| ${\rm H_{2}O}\;3_{21}-3_{12}$                                   | 1162.912                          |                       |
+-----------------------------------------------------------------+-----------------------------------+-----------------------+
| 1-3 ${\rm [NII]_{\rm 205 \mu m}}$                               | 1461.131                          | C                     |
+-----------------------------------------------------------------+-----------------------------------+-----------------------+
| 1-3 ${\rm H_{2}O}\;3_{03}-2_{12}$                               | 1716.770                          | D                     |
+-----------------------------------------------------------------+-----------------------------------+                       |
| CO($15-14$)                                                     | 1726.603                          |                       |
+-----------------------------------------------------------------+-----------------------------------+                       |
| OH $^2\Pi_{1/2}$,$\frac{3}{2}^+\!-\!\frac{1}{2}^-$ $^{(\star)}$ | 1834.744                          |                       |
+-----------------------------------------------------------------+-----------------------------------+                       |
| OH $^2\Pi_{1/2}$,$\frac{3}{2}^-\!-\!\frac{1}{2}^+$ $^{(\star)}$ | 1837.800                          |                       |
+-----------------------------------------------------------------+-----------------------------------+                       |
| CO($16-15$)                                                     | 1841.346                          |                       |
+-----------------------------------------------------------------+-----------------------------------+-----------------------+

: Covered emission lines in each frequency setup with their rest frequency.

Table notes: $^{(1)}$Rest frequency of the lines are taken from the "Splatalogue database for astronomical spectroscopy" available at <https://www.cv.nrao.edu/php/splat>, see references therein. $^{(2)}$Setup IDs are listed in Table [\[tbl:obs_data\]](#tbl:obs_data). $^{(\star)}$The $\Lambda-$doubling transitions of the Hydroxyl molecule listed here are actually two triplets produced by the hyper-fine structure splitting of the upper and lower level, that are not spectral resolved in the observations. Here we report the average rest frequency of the triplets. The six transitions are OH $^2\Pi_{1/2}$,$\frac{3}{2}^+\!-\!\frac{1}{2}^-$,$1\!-\!1$; OH $^2\Pi_{1/2}$,$\frac{3}{2}^+\!-\!\frac{1}{2}^-$,$2\!-\!1$; OH $^2\Pi_{1/2}$,$\frac{3}{2}^+\!-\!\frac{1}{2}^-$,$1\!-\!0$ and OH $^2\Pi_{1/2}$,$\frac{3}{2}^-\!-\!\frac{1}{2}^+$,$1\!-\!1$; OH $^2\Pi_{1/2}$,$\frac{3}{2}^-\!-\!\frac{1}{2}^+$,$2\!-\!1$; OH $^2\Pi_{1/2}$,$\frac{3}{2}^-\!-\!\frac{1}{2}^+$,$1\!-\!0$.

# Observations and data reduction

We present the ALMA Cycle 5 datasets of quasar PJ231-20, quasar PJ308-21 (hereafter PJ231-20 QSO and PJ308-21 QSO, respectively) and their companion galaxies (program ID: 2017.1.00139.S, PI: R. Decarli) located at redshift $z\sim6.59$ and $z\sim6.24$, respectively. The observations were executed during the period April-August 2018 using 43-48 ALMA 12m-antennas in compact configurations (C43-2, C43-3). The program comprised three frequency settings in each of ALMA bands 4, 5 and 6 respectively, that cover nine atomic fine-structure and molecular lines; \[NII\]$_{205 \rm \mu m}$, high-$J$ CO(10–9, 15–14, 16–15), H$_2$O ($3_{03}-2_{12}$, $3_{12}-2_{21}$, $3_{21}-3_{12}$), OH doublet, together with dust continuum emission. However, for PJ308-21, only the band 6 setup encompassing CO(15–14, 16–15), H$_2$O $3_{03}-2_{12}$ and the OH$_{\rm 163\mu m}$ doublet was executed.

We also present follow-up ALMA Cycle 7 observations of the same objects (program ID: 2019.1.00147.S, PI: R. Decarli) in which we sampled the atomic FSL \[CI\]$_{369 \rm \mu m}$, and the molecular mid-$J$ CO(7–6) transition together with dust continuum emission in ALMA band 3. These observations were executed in October 2019 using 43-48 ALMA 12m-antennas in the C43-4 configuration. All the observations were designed not to spatially resolve the emission of each source, but with high enough angular resolution to resolve the companions from the quasars. This allowed us to maximize the signal-to-noise ratio (S/N) within the beam. The angular resolution ranges between $\sim1''.00$ and $\sim1''.80$. In Table [\[tbl:obs_data\]](#tbl:obs_data) we summarize the ALMA observations and in Table [1](#tbl:obs_line) we report the covered emission lines in each frequency setup together with their rest frequencies.

We performed data reduction using the default calibration pipeline with the Common Astronomy Software Applications (CASA, v.5.1.1-5 and v.5.6.1-8 for Cycle 5 and Cycle 7 data respectively) package (cite: McMullin+2007). Calibrated visibilities were imaged using the CASA task `tclean` with "natural" weighting scheme in order to maximize the sensitivity of the resulting maps. Dirty images were cleaned employing two circular masks superimposed to include continuum emission of both the central quasar and the companion. In the cleaning run, we stopped the procedure when the peak flux in the residual image within the mask dropped close to the root-mean-square (RMS) noise of the image in regions with no source emission (i.e., $\sim$ 1$\sigma$ cleaning threshold). For each setup, we produce two image-frequency cubes for the lower-side band (LSB) and the upper-side band (USB) respectively, with a channel width of $40\,{\rm km\,s^{-1}}$. We obtained continuum images by combining the line-free channels from all spectral windows in multifrequency synthesis mode. The line-free channels were determined by inspecting the visibilities in all the frequency sidebands. In the case where no line was detected, we selected line-free channels by adopting a line width of $300\,{\rm km\,s^{-1}}$ and source redshift based on the \[CII\]$_{\rm 158\mu m}$ line observations published by (cite: Decarli+2017). We used the CASA task `uvcontsub` to fit the continuum visibilities in the line-free channels and we obtained continuum-subtracted cubes with $40\,{\rm km\,s^{-1}}$ of channel width. We fitted the continuum emission in the LSB and USB, separately, (maximum bandwidth of $\sim4\,{\rm GHz}$) as a constant with frequency. This gave us two continuum-subtracted cubes for each frequency setups. In order to achieve Nyquist-Shannon sampling, we set the cube pixel sizes in the image plane to $0.1\si{\arcsecond}$, equal to $\sim 1/7$ of the FWHM of the minor axis of the ALMA synthesized beam. Therefore, we obtained cubes and continuum images with a pixel size of $0.1\si{\arcsecond}$. Self-calibration was attempted but showed no additional improvement for any of the observations, so we did not use it for what follows. Finally, both continuum images and line cubes were corrected for the primary beam response. In this work we supplement our analysis making use of the ALMA Cycle 3 \[CII\]$_{158\rm \mu m}$ observations of PJ231-20 and PJ308-21 presented in (cite: Decarli+2017) (program ID: 2015.1.01115.S), that we analyzed in a consistent way.

+:-------------------------------------------------------+:----------------------------:+:--------------------:+:------------------------:+:----------------------:+:----------------------------:+:--------------------:+:------------------------:+:----------------------:+
| **PJ231-20**                                           | **QSO**                                                                                                 | **companion**                                                                                           |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
|                                                        |                              |                      |                          |                        |                              |                      |                          |                        |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| Emission line                                          | $z_{\rm line}$               | FWHM                 | $S\Delta\varv$           | $L_{\rm line}$         | $z_{\rm line}$               | FWHM                 | $S\Delta\varv$           | $L_{\rm line}$         |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
|                                                        |                              | (${\rm km\,s^{-1}}$) | (${\rm Jy\,km\,s^{-1}}$) | $(10^9L_{\astrosun})$  |                              | (${\rm km\,s^{-1}}$) | (${\rm Jy\,km\,s^{-1}}$) | $(10^9L_{\astrosun})$  |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 ${\rm [NII]_{\rm 205 \mu m}}$                      | $6.5848^{+0.0012}_{-0.0012}$ | $276^{+199}_{-97}$   | $0.21^{+0.09}_{-0.07}$   | $0.18^{+0.08}_{-0.06}$ | $6.591^{+0.002}_{-0.002}$    | $229^{+252}_{-97}$   | $0.10^{+0.07}_{-0.06}$   | $0.08^{+0.06}_{-0.05}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| ${\rm [CII]_{\rm 158 \mu m}}$                          | $6.5864^{+0.0003}_{-0.0003}$ | $372^{+23}_{-21}$    | $2.54^{+0.13}_{-0.13}$   | $2.87^{+0.15}_{-0.15}$ | $6.5897^{+0.0003}_{-0.0003}$ | $492^{+41}_{-39}$    | $2.36^{+0.16}_{-0.16}$   | $2.68^{+0.18}_{-0.18}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| ${\rm [CI]_{369\mu m}}$                                | $6.5873^{+0.0014}_{-0.0014}$ | $243^{+97}_{-70}$    | $0.11^{+0.04}_{-0.04}$   | $0.05^{+0.02}_{-0.02}$ | –                            | –                    | $<0.08$                  | $<0.04$                |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 CO($7-6$)                                          | $6.5863^{+0.0007}_{-0.0007}$ | $335^{+39}_{-34}$    | $0.46^{+0.04}_{-0.04}$   | $0.22^{+0.02}_{-0.02}$ | $6.5870^{+0.0020}_{-0.0014}$ | $614^{+242}_{-184}$  | $0.24^{+0.07}_{-0.06}$   | $0.12^{+0.03}_{-0.03}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| CO($10-9$) ${^{(\star)}}$                              | $6.5878^{+0.0005}_{-0.0005}$ | $293^{+53}_{-43}$    | $0.40^{+0.06}_{-0.06}$   | $0.28^{+0.04}_{-0.05}$ | $6.5873^{+0.0005}_{-0.0010}$ | $183^{+160}_{-67}$   | $0.11^{+0.04}_{-0.03}$   | $0.08^{+0.03}_{-0.02}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| CO($15-14$)                                            | $6.5851^{+0.0017}_{-0.0013}$ | $454^{+81}_{-128}$   | $0.33^{+0.10}_{-0.09}$   | $0.34^{+0.10}_{-0.10}$ | –                            | –                    | \<0.16                   | \<0.16                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| CO($16-15$)                                            | $6.5857^{+0.0003}_{-0.0003}$ | $83^{+72}_{-24}$     | $0.15^{+0.05}_{-0.04}$   | $0.16^{+0.06}_{-0.04}$ | –                            | –                    | \<0.16                   | \<0.17                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 ${\rm H_{2}O}\;3_{12}-2_{21}$ ${^{(\star)}}$       | $6.5874^{+0.0005}_{-0.0010}$ | $191^{+69}_{-49}$    | $0.18^{+0.06}_{-0.05}$   | $0.12^{+0.04}_{-0.03}$ | –                            | –                    | \<0.09                   | \<0.06                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| ${\rm H_{2}O}\;3_{21}-3_{12}$                          | $6.5859^{+0.0010}_{-0.0010}$ | $396^{+98}_{-75}$    | $0.33^{+0.07}_{-0.06}$   | $0.23^{+0.05}_{-0.04}$ | –                            | –                    | \<0.09                   | \<0.06                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| ${\rm H_{2}O}\;3_{03}-2_{12}$                          | $6.5853^{+0.0007}_{-0.0007}$ | $187^{+96}_{-66}$    | $0.18^{+0.07}_{-0.06}$   | $0.18^{+0.07}_{-0.06}$ | –                            | –                    | \<0.16                   | \<0.16                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 OH $^2\Pi_{1/2}$,$\frac{3}{2}^+\!-\!\frac{1}{2}^-$ | $6.5863^{+0.0006}_{-0.0006}$ | $322^{+70}_{-59}$    | $0.45^{+0.09}_{-0.08}$   | $0.49^{+0.10}_{-0.09}$ | $6.5879^{+0.0019}_{-0.0019}$ | $296^{+108}_{-118}$  | $0.19^{+0.09}_{-0.09}$   | $0.21^{+0.10}_{-0.10}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| OH $^2\Pi_{1/2}$,$\frac{3}{2}^-\!-\!\frac{1}{2}^+$     | $6.5851^{+0.0006}_{-0.0009}$ | $230^{+91}_{-66}$    | $0.34^{+0.09}_{-0.09}$   | $0.37^{+0.10}_{-0.10}$ | $6.589^{+0.002}_{-0.002}$    | $414^{+113}_{-185}$  | $0.27^{+0.12}_{-0.12}$   | $0.30^{+0.13}_{-0.13}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| Dust continuum $^{(1)}$                                | $F_{\it \nu}$ (mJy)                                                                                     | $F_{\it \nu}$ (mJy)                                                                                     |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 1-9 93.85 GHz                                          | $0.22\pm0.01$                                                                                           | $<0.033$                                                                                                |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 105.72 GHz                                             | $0.31\pm0.02$                                                                                           | $0.07\pm0.02$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 140.34 GHz                                             | $0.72\pm0.02$                                                                                           | $0.19\pm0.05$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 152.57 GHz                                             | $0.86\pm0.03$                                                                                           | $0.32\pm0.03$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 193.41 GHz                                             | $1.91\pm0.04$                                                                                           | $0.64\pm0.04$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 205.31 GHz                                             | $2.19\pm0.03$                                                                                           | $0.64\pm0.03$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 226.79 GHz                                             | $2.88\pm0.05$                                                                                           | $0.84\pm0.05$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 234.13 GHz                                             | $3.29\pm0.05$                                                                                           | $0.93\pm0.05$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 241.94 GHz                                             | $3.46\pm0.06$                                                                                           | $0.93\pm0.05$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 250.08 GHz                                             | $3.94\pm0.06$                                                                                           | $1.14\pm0.07$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| **PJ308-21**                                           | **QSO**                                                                                                 | **companion**                                                                                           |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
|                                                        |                              |                      |                          |                        |                              |                      |                          |                        |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| ${\rm [CII]_{\rm 158 \mu m}}$                          | $6.2354^{+0.0003}_{-0.0002}$ | $533^{+47}_{-43}$    | $1.65^{+0.13}_{-0.12}$   | $1.73^{+0.14}_{-0.13}$ | $6.2495^{+0.0005}_{-0.0006}$ | $239^{+46}_{-40}$    | $0.43^{+0.07}_{-0.07}$   | $0.46^{+0.08}_{-0.07}$ |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| ${\rm [CI]_{369\mu m}}$                                | –                            | –                    | \<0.06                   | \<0.03                 | –                            | –                    | \<0.06                   | \<0.03                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 CO($7-6$)                                          | –                            | –                    | \<0.06                   | \<0.03                 | –                            | –                    | \<0.06                   | \<0.03                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| CO($15-14$)                                            | $6.2364^{+0.0020}_{-0.0018}$ | $498^{+49}_{-97}$    | $0.13^{+0.04}_{-0.04}$   | $0.12^{+0.04}_{-0.04}$ | –                            | –                    | \<0.07                   | \<0.06                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| CO($16-15$)                                            | –                            | –                    | \<0.07                   | \<0.07                 | –                            | –                    | \<0.07                   | \<0.07                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 ${\rm H_{2}O}\;3_{03}-2_{12}$                      | $6.234^{+0.003}_{-0.002}$    | $264^{+134}_{-120}$  | $0.03^{+0.03}_{-0.02}$   | $0.03^{+0.03}_{-0.02}$ | –                            | –                    | \<0.07                   | \<0.06                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| 1-9 OH $^2\Pi_{1/2}$,$\frac{3}{2}^+\!-\!\frac{1}{2}^-$ | $6.2348^{+0.0030}_{-0.0017}$ | $262^{+145}_{-137}$  | $0.04^{+0.03}_{-0.02}$   | $0.04^{+0.03}_{-0.02}$ | –                            | –                    | \<0.07                   | \<0.07                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| OH $^2\Pi_{1/2}$,$\frac{3}{2}^-\!-\!\frac{1}{2}^+$     | $6.234^{+0.002}_{-0.002}$    | $400^{+113}_{-165}$  | $0.10^{+0.05}_{-0.05}$   | $0.10^{+0.05}_{-0.05}$ | –                            | –                    | \<0.07                   | \<0.07                 |
+--------------------------------------------------------+------------------------------+----------------------+--------------------------+------------------------+------------------------------+----------------------+--------------------------+------------------------+
| Dust continuum $^{(1)}$                                | $F_{\it \nu}$ (mJy)                                                                                     | $F_{\it \nu}$ (mJy)                                                                                     |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 1-9 98.95 GHz                                          | $0.03\pm0.01$                                                                                           | \<0.02                                                                                                  |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 110.87 GHz                                             | $0.04\pm0.01$                                                                                           | \<0.02                                                                                                  |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 237.99 GHz                                             | $0.45\pm0.02$                                                                                           | $0.08\pm0.02$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 246.94 GHz                                             | $0.55\pm0.04$                                                                                           | \<0.12                                                                                                  |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 253.61 GHz                                             | $0.59\pm0.02$                                                                                           | $0.06\pm0.02$                                                                                           |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
| 262.89 GHz                                             | $0.59\pm0.06$                                                                                           | \<0.09                                                                                                  |
+--------------------------------------------------------+---------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

Table notes: In those cases in which the line emission is not detected, upper limits ($3\sigma$) on continuum, line flux and luminosity are reported. $^{(1)}$Here we report the central frequency of the LSB and USB for each frequency setup in which we measured the continuum fluxes. ${^{(\star)}}$The CO(10-9) and H$_2$O $3_{1,2}-2_{2,1}$ line are partially blended.

# Line and continuum measurements

To obtain information on the different ISM phases and dust, we need to measure lines and continuum properties. The observed emission in the ALMA cubes is integrated over the beam and projected along the line of sight. If the source emission is not resolved in the observation, the spectrum measured in the brightest pixel corresponds to the integrated spectrum of the source. By inspecting the continuum and the velocity-integrated line maps we verified that the flux peak (measured in $\rm{Jy\,beam^{-1}}$ and ${\rm Jy\,beam^{-1}\,km\,s^{-1}}$, respectively) is consistent with the integrated flux over an aperture containing the observed emission for each of the objects, even in the case with high S/N and high angular resolution (such as the CO(7–6) line in PJ231-20 QSO in setup A). Therefore, the targeted sources are (at best) marginally resolved in the observations. This conclusion, at least for PJ231-20 system, is supported by the measurements of the size of continuum and \[CII\]$_{\rm 158\mu m}$ line emitting region obtained from ALMA high angular resolution observations (cite: Neeleman+2019). This allowed us to safely perform a single-pixel analysis of the data. Indeed, the uncertainties introduced ignoring the aperture correction are comparable to the typical uncertainties ($>10\%$) ascribed to the line and continuum flux measurements taking into account ALMA visibility calibration errors ($\sim20\%$). Furthermore, we take advantage of the single-pixel analysis both to maximize the S/N in the extracted spectra and to simultaneously minimize biases on the flux measurements possibly arising from the blending of quasar and companion galaxy in the frequency setups at low angular resolution. Finally, we assessed that the different beam sizes of the various data cubes in the different ALMA bands do not significantly bias the flux estimates. To do so, we tapered the highest spatial resolution data to the lowest one by using the option `restoringbeam` within the CASA task `tclean`, and we checked that the flux measurements obtained from single-pixel analysis in the tapered data are consistent within the uncertainties with those estimated form the data cubes obtained by imaging all the calibrated visibilities[^1].

Hence, we identified the brightest pixel in the continuum map of each ALMA band and we extracted the (beam-)integrated spectra of the quasars and the companion galaxies from the full data cubes (i.e., with continuum present inside) in the selected pixel. We then fit each spectrum as a constant representing the continuum[^2], and a Gaussian for the line. In order to explore the parameter space, we used the Markov chain Monte Carlo (MCMC) Ensemble sampler `emcee` (cite: Foreman+2013) and we obtained the posterior probability distributions of the free parameters. Finally, we computed the best values and uncertainties from the 50th, 16th and 84th percentile of the distributions, respectively. In addition, we derived line luminosities as (cite: CarilliWalter2013), $$\begin{align}
\label{eq:lum}
&L_{\rm line}\,[L_{\astrosun}]= 1.04\times10^{-3} S {\Delta \varv}\,\nu_{\rm obs}D_L^2\,,\\
\label{eq:lum'}
&L'_{\rm line}\,[{\rm K\,km\,s^{-1}pc^2}]=3.25\times10^7 S {\Delta \varv}\frac{D_L^2}{(1+z)^3\nu_{\rm obs}^2}\,,
\end{align}$$ where $S {\Delta \varv}$ is the line velocity-integrated flux in ${\rm Jy\,beam^{-1}\,km\,s^{-1}}$, $\nu_{\rm obs}$ is the observed central frequency of the line in GHz, and $D_L$ is the luminosity distance in Mpc. The relation between Eq. [\[eq:lum\]](#eq:lum) and  [\[eq:lum'\]](#eq:lum') is $L_{\rm line}=3\times 10^{-11}\nu_{\rm rest}^3L'_{\rm line}$.

In Table [\[tbl:line_data\]](#tbl:line_data) we report the measured and derived quantities for the observed lines and continuum emission in each frequency setup for the quasars and their companions. In order to check the robustness of the spectral fit results against spurious effects of the noise (especially in the very critical cases of low S/N, e.g. the lines in the spectra of PJ308-21 QSO), we performed different spectral fits by accurately varying the imposing priors and starting points in the MCMC fitting procedure. We therefore assessed that the line is detected (although at low significance) when the derived best-fit models in all the cases, point to a self-consistent solution. In addition, we performed all the fits to the data at a lower spectral resolution (${80\,{\rm km\,s^{-1}}}$) and we verified that all derived parameters are consistent within ${\sim1\sigma}$ with those reported in Table [\[tbl:line_data\]](#tbl:line_data). In Figs. [1](#fig:pj231_spectramaps) and  [2](#fig:pj308_spectramaps) we report the observed spectra of the PJ231-20 and PJ308-21 systems, respectively, together with the line and continuum best-fit models. We also report the corresponding continuum-subtracted line velocity-integrated maps over $360\,{\rm km\,s^{-1}}$. This value maximizes the S/N of the CO(10–9) velocity-integrated map of PJ231-20 QSO. We used this as a reference value in order to obtain all the other line maps. Then, in Fig. [3](#fig:cont_maps) we show the line-free continuum maps in the various frequency bands. In some cases (see Figs. [1](#fig:pj231_spectramaps), [2](#fig:pj308_spectramaps)) the peaks of line velocity-integrated maps of PJ231-20 and PJ308-21 systems, show a shift with respect to the reference position of the sources. However, in all the cases the shift is well inside the beam of the observed map. This effect can be likely ascribable to the continuum subtraction and/or the low S/N of the emission. Therefore, we conclude that the line and the continuum peaks are spatially consistent at the available resolution.

Throughout the text, we report the significance on the measured flux of a line emission in unit of $\sigma = \sqrt{\Delta \varv\,{\rm FWHM}} \times \left\langle{\rm RMS}\right \rangle$, where $\Delta\varv$ is the channel width ($40\,{\rm km\,s^{-1}}$), FWHM is the full width at half maximum of the line best-fit Gaussian, and the $\left\langle {\rm RMS}\right\rangle$ is the average RMS noise in the line cube (see Table [\[tbl:obs_data\]](#tbl:obs_data)). In cases in which line emission is not detected in the observation, we report $3\sigma$ upper limits assuming ${\rm FWHM} = 300\,{\rm km\,s^{-1}}$. Finally, tor the non-detections of continuum emission we report $3\sigma$ upper limit with $\sigma$ equal to RMS noise of the continuum.

![](images/PJ231-20_spectramaps.pdf)

![](images/PJ308-21_spectramaps.pdf)

![](images/continuum_maps.pdf)

# CLOUDY models of photo- and X-ray dissociation regions 

The observed molecular and atomic FSLs are key diagnostics of the physical conditions present in the ISM of galaxies. The observed FSL to dust-continuum flux ratios require a relatively efficient ($0.1 - 1\%$) mechanism to convert the continuum flux into atomic and molecular gaseous line emission. (cite: Tielens+1985a) showed that this condition is satisfied by PDRs in which dust grain photoelectric heating in regions where the far-UV (FUV) radiation ($6 < h\nu < 13.6\,{\rm eV}$) from hot stars (O and B) impinges on molecular clouds. PDRs represent the interface between the molecular and ionized medium (i.e. ’HII regions’) at the outskirt of molecular clouds, where FUV radiation plays a significant role in the heating and/or chemistry of the gas phase. (cite: Tielens+1985a; Tielens+1985b) also pointed out that the emission from such regions depends largely on the cloud density ($n_{\rm H}$) and the strength of the FUV radiation field ($G_0$) illuminating the cloud (where $G_0$ is in Habing flux units, i.e. $1.6\times10^{-3}\,{\rm erg\,s^{-1}\,cm^{-2}}$, see (cite: Habing+1968)). PDRs include all the atomic neutral medium and most of the molecular clouds, therefore the majority of the mass of the ISM is in PDRs. Densities in PDRs range from $n_{\rm H}\approx0.25\,{\rm cm^{-3}}$ to $n_{\rm H}\apprge 10^{7}\,{\rm cm^{-3}}$ and FUV flux from $G_0\apprle 1$ to $G_0\apprge 10^6$ (cite: McKee+1977; Hollenbach+1999; Kaufman+1999; Meijerink+2007).

Molecular gas can also be exposed to X-ray radiation, for example near supernova shocks or radiation emitted from accreting BH in quasars (cite: Langer+1978; Krolik+1983; Krolik+1988; Lepp+1983). X-ray photons are able to penetrate much deeper into the cloud (column density of $N_{\rm H}\apprge 10^{22}\,{\rm cm^{-2}}$) and can effect the chemical and thermal structure of FUV-opaque molecular gas. Therefore, completely analogous to the PDRs, XDRs can be defined as predominantly neutral gas in which X-rays dominate the gas heating and much of the chemistry through X-ray dissociation and ionization (e.g. (cite: Maloney+1996; Hartquist+1998);\
(cite: Hollenbach+1999)). In this case, the incident radiation field is typically expressed in terms of X-ray flux, $F_{\rm X}({\rm erg\,s^{-1}\,cm^{-2}})$, over the range $1-100\,{\rm keV}$.

Considerable effort has been made in constructing PDR/XDR models in order to constrain the physical properties of the ISM where molecular and atomic transitions take place (cite: Tielens+1985a; Meixner+1993; Maloney+1996; Spaans+1996; Kaufman+1999; Kaufman+2006; Elitzur+2006; Meijerink+2005; Meijerink+2007; vanderTak+2007; Pound+2008; Bisbas+2012; Ferland+2017). Each of these codes is optimized to simulate various astrophysical environments and are based on different assumptions of PDR geometry, thermal and chemical balance, and different implementation of radiative transfer through PDR. Here we use CLOUDY radiative-transfer code (version c.17.01, (cite: Ferland+2017)) to characterize the ISM in the quasar and companion galaxy in the PJ231-20 and PJ308-21 systems, as it is highly customizable and allows the simultaneous treatment of all the species studied in this work. We modeled the observed line-emitting region as a single plane-parallel semi-infinite cloud impinged by a radiation field in both the PDR and XDR regimes, and we obtained a suite of diagnostics to interpret the observed line ratios in these systems. In the following we describe how the models were set up.

Within CLOUDY, we ran a total of $270\times2$ PDR/XDR models assuming a 1D gas slab of constant total hydrogen density in the range $\log(n_{\rm H}/{\rm cm^{-3}}) = [2,6]$ (15 models, $\sim0.29$ dex spacing) varying the strength of the radiation field (18 models), for two values of cloud total hydrogen column density of $N_{\rm H}=10^{23},10^{24}\,{\rm cm^{-2}}$. In the case of PDR models, we defined the spectral energy distribution (SED) of the impinging radiation field as a black body emission with a temperature of $T=5\times10^4{\rm K}$ scaled to obtain Habing fluxes at the gas slab surface in the range $\log G_0 = [1,6]$ ($\sim0.29$ dex spacing). In the case of XDR, we choose a standard AGN template as the incident continuum SED, $$\begin{equation}
 f_{\nu} = \nu^{\alpha_{\rm UV}}\exp\!\left ( -h\nu/k_{\rm B}T_{\rm BB} \right )\exp\!\left ( -k_{\rm B}T_{\rm IR}/h\nu \right )+a\nu^{\alpha_X}, 
\end{equation}$$ with parameters set in order to generate the continuum used in a large atlas of model broad line region line intensities (cite: Korista+1997). We normalized this incident SED in order to have X-ray flux between $1-100\,{\rm keV}$ in the range $\log\,[F_{\rm X}/({\rm erg\,s^{-1}\,cm^{-2}})]=[-2.0,2.0]$ ($\sim0.24$ dex spacing) at the cloud surface. This range fully covers the X-ray radiation field strengths generally considered in standard XDR models (cite: Maloney+1996; Meijerink+2007).

For the gas slab we assumed the default interstellar medium metal abundances (`abundance ISM`) stored in CLOUDY. We adopted dust ISM grains (`grains ISM`) stored in CLOUDY with a size distribution and abundance from (cite: Mathis+1997). In addition, we included polycyclic aromatic hydrocarbons (PAHs, `grains PAH`) with distribution from (cite: Abel+2008), which generally dominate the grain photoelectric heating. We also included the cosmic microwave background (CMB) radiation at $z=6$ that affects the far-IR line luminosity of galaxies at high $z$. We adopted the default CLOUDY prescriptions for the cosmic ray ionization rate background (`cosmic rays background`) which are an important source of heating deep into the molecular cloud. The mean H cosmic ray ionization rate is $2\times10^{-16}\,{\rm s^{-1}}$ (cite: Indriolo+2007), and the H$_2$ secondary ionization rate is $4.6\times10^{-16}\,{\rm s^{-1}}$ (cite: Glassgold+1974). Finally, we added $1.5\,\si{km\,s^{-1}}$ in quadrature to the thermal motions within the cloud, to model the effect of line broadening produced by microturbulence.

In order to simulate the absorption of ionizing radiation due to atomic hydrogen; in both PDR and XDR case, we modified the incident continuum by extinction due to photoelectric absorption by a cold neutral slab with a column density of $10^{24}\,{\rm cm^{-2}}$ (`extinguish column 24`, see (cite: Cruddace+1974)). The code computes the radiative transfer through the slab up to total hydrogen column density of $N_{\rm H}=10^{23},10^{24}\,{\rm cm^{-2}}$. We choose this stopping criterion to fully sample the molecular component typically located at $N_{\rm H} >10^{22}\,{\rm cm^{-2}}$ as is observed in giant molecular clouds (cite: McKee+1977). However, a higher column density $N_{\rm H}\apprge 5\times10^{23}\,{\rm cm^{-2}}$ is required to properly model H$_2$O and OH emission (cite: Goicoechea+2005; Gonzalez-Alfonso+2014; Spinoglio+2005; Liu+2017).

With our PDR and XDR models we obtained grids of line intensities and emitted continuum emerging from the cloud’s surface (both in unit of ${\rm erg\,s^{-1}\,cm^{-2}}$), as function of the density of the medium (total hydrogen density, $n_{\rm H}$ ranges $10^2-10^6\,{\rm cm^{-3}}$) and the strength of the radiation field (parametrized by $G_0 = 10^1-10^6$ or $F_{\rm X}\,({\rm erg\,s^{-1}\,cm^{-2}}) = 10^{-2}-10^2$ in the case of PDR and XDR, respectively) for two values of total hydrogen column density $N_{\rm H}=10^{23}, 10^{24}\,{\rm cm^{-2}}$.

The models adopted in this work are designed to simulate a "typical" cloud in a galaxy under very simplistic assumptions. Undoubtedly, these simple models cannot provide a realistic picture of the ISM in galaxies that are composed of an ensemble of clouds and diffuse medium with a wide ranges of physical and geometrical properties. However, quantities such as line luminosity ratios can be used to mitigate the large uncertainties related to the unknown parameters, thus allowing us to quantitatively compare model predictions with observations.

In the following sections, we present various results obtained from dust FIR continuum and line detections in the targeted sources. Then, by comparing our model results with the observed emission we put constraints on the key parameters characterizing the ISM in the quasar hosts and companion galaxies.

![](images/dust_cont_comb.pdf)

# Dust properties: FIR continuum

The continuum emission detected in the FIR and (sub-)mm bands, is dominated by emission from dust distributed in the diffuse medium and star-forming regions of a galaxies. The bulk of the dust in star-forming regions is heated by the diffuse rest-frame optical/UV radiation field produced by young stars. The typical dust temperature for quasar hosts lies in the range $T_{\rm dust}\sim40-70\,{\rm K}$ (cite: Priddey+2001; Beelen+2006; Wang+2008; Leipski+2013; Leipski+2014), and increases to $\apprge 100-500\,{\rm K}$ in the proximity of the central BH accretion disk (cite: Rowan-Robinson+1995; Charmandaris+2004; Beelen+2006). Since the dust grains are in local thermodynamical equilibrium (LTE) with the radiation field, they emit thermal radiation. However, dust grains are not ideal black bodies. For this reason, dust thermal emission is usually modeled as a modified black body where the grains’ emission efficiency is expressed in terms of the dust opacity coefficient, $k_{\rm d}(\nu)\propto \nu^\beta$. Therefore, by assuming optically thin dust emission (cite: Beelen+2006), in the Rayleigh-Jeans limit, the continuum flux is proportional to the dust mass, $M_{\rm dust}$, and temperature, $T_{\rm dust}$ (cite: Downes+1992; Dunne+2000). Based on observational studies at low and high redshift (cite: Blain+2003; Conley+2011; Rangwala+2011; Casey+2012; Riechers+2013; Faisst+2020), the optically thin dust approximation may not be true at short wavelengths, however likely holds for our observations since most of the continuum data is at rest-frame $\lambda>200\,{\rm \mu m}$. In order to estimate $M_{\rm dust}$ and $T_{\rm dust}$ in the quasar host galaxies and their companions, we modeled the continuum data with a modified black body taking into account the effect of the cosmic microwave background radiation (cite: daCunha+2013) whose temperature scales as $\propto (1+z)$ and is $T_{\rm CMB}\approx 19\, {\rm K}$ at $z=6$. Indeed, at the redshifts of the sources the CMB is an additional non-negligible source of heating and provides a strong background against which we measure line and continuum emission. Therefore, following (cite: daCunha+2013) we define the flux density in the optically thin limit as: $$\begin{align}
&F_{\nu/(1+z)}^{\rm intr} = B_\nu[T_{\rm dust}(z)]k_{\rm d}(\nu)(1+z)M_{\rm dust}D_L^{-2}\,,\\
&F_{\nu/(1+z)}^{\rm obs} = \!\left ( 1 - \frac{B_{\nu}[T_{\rm CMB}(z)]}{B_{\nu}[T_{\rm dust}(z)]} \right )F_{\nu/(1+z)}^{\rm intr}\,;
\label{eq:BB_model}
\end{align}$$ where $F_{\nu/(1+z)}^{\rm intr}$ and $F_{\nu/(1+z)}^{\rm obs}$ are the intrinsic and observed flux density against the CMB, respectively; $B_\nu(T)$ is the Planck function $B_\nu(T)  = [2h\nu^3/c^2][\exp(h\nu/k_{\rm B}T)-1]^{-1}$, $k_{\rm d}(\nu)$ is the frequency-dependent dust mass opacity coefficient defined as $k_{\rm d}(\nu) = k_0 (\nu/\nu_0)^\beta$, where $\nu_0 = 352.7$ GHz, and $\beta$ is the dust spectral emissivity index (cite: Dunne+2000). (cite: daCunha+2013) also show that the observed galaxy dust temperature at certain redshift, $T_{\rm dust}(z)$, is higher than the dust temperature that we would observe at $z=0$, due to the absorption of CMB photons by the dust grains: $T_{\rm dust}(z) = \{(T_{\rm dust}^{z=0})^{4+\beta}+(T_{\rm CMB}^{z=0})^{4+\beta}[(1+z)^{4+\beta}-1]\}^{1/(4+\beta)}$. However, at $z\approx6.5$ and typical dust temperatures of $T_{\rm dust} > 35\,{\rm K}$, this correction is $<2\%$, much less than relative uncertainties that we expect on dust temperature estimate. Therefore, we ignore this correction.

Hence, we used the model defined in Eq. [\[eq:BB_model\]](#eq:BB_model) to fit the quasar and companion continuum data reported in Table [\[tbl:line_data\]](#tbl:line_data), together with ALMA band 6 data presented in (cite: Decarli+2017), from which we obtained line and continuum measurements. In order to find the best-fit model, we made use of the `emcee` code (cite: Foreman+2013), allowing $M_{\rm dust}$, and $\beta$ to freely vary during the fitting procedure. We limited the parameter space by imposing box-like priors defined as $\log M_{\rm dust}[M_{\astrosun}] > 0$, and $\beta\in(1,2.5)$. In addition, the sampled frequency range of the observations mostly covers the Rayleigh-Jeans tail of the dust thermal emission. The observed flux density in this regime is $\propto T_{\rm dust}M_{\rm dust}$, making these parameters degenerate, therefore we employed a relative tight Gaussian prior on $T_{\rm dust}$ with mean and standard deviation equal to $47\,{\rm K}$ and $5\,{\rm K}$, respectively. These choices are consistent with the typical measurements in quasar host galaxies reported in the literature (cite: Priddey+2001; Beelen+2006; Wang+2008; Leipski+2013; Leipski+2014) and also validated by the results obtained below for the water vapor lines (see Sect. [8.5](#ssect:water_tir_relation)). On the other hand, if the companion galaxies actually do not host a quasar (as suggested by rest-frame UV and X-ray studies, see (cite: Decarli+2017; Connor+2019; Connor+2020)), we expect that the dust temperature may not be as high as the quasar host galaxies due the lack of the additional dust heating by an AGN. Indeed, the non-detection of water lines in the companions also argue against a high $T_{\rm dust}$ (albeit the detections of OH$_{\rm 163\mu m}$ doublet that likely traces similar regions of those traced by H$_2$O lines, see Sects. [8.4](#ssect:water_vapor),  [8.8](#ssect:oh_lines),  [8.9](#ssect:h2o_oh_ratio)). Therefore, in the case of the companion galaxies, we also considered a lower-temperature scenario. To do so, we performed an additional fit centering the Gaussian dust temperature prior on $T_{\rm dust}=35\,{\rm K}$, that is a representative value of the population of SMGs at $z\sim 1-3$ (cite: Chapman+2005; Kovacs+2006). In the fits we also take into account the upper limit measurements on dust continuum by inserting a penalty term in the log-likelihood function in the form $\mathcal{P}=-0.5[({\rm model}-{\rm data})/{\rm data}]^2$, if ${\rm model}>{\rm data}$, else $\mathcal{P}=0$. Finally, we assumed the sources’ \[CII\]-based redshifts reported in (cite: Decarli+2017) (see Table [\[tbl:line_data\]](#tbl:line_data)). In Fig. [4](#fig:dust_continuum) we show the best-fit models of the continuum emission in PJ231-20 and PJ308-21 systems, respectively, together with the posterior probability distributions of the parameters. From these results, we estimated the total (TIR, $8-1000\,{\rm \mu m}$, (cite: Sanders+2003)) and FIR ($40-400\,{\rm \mu m}$, (cite: Helou+1988)) rest-frame luminosities of the sources, by integrating the best-fit models over the corresponding frequency ranges. Finally, we inferred the SFR, using the local scaling relation from (cite: Murphy+2011); ${\rm SFR_{IR}}/(M_{\astrosun}\,{\rm yr^{-1}}) = 1.49\times 10^{-10}L_{\rm TIR}/L_{\astrosun}$, assuming that the IR-luminosity is dominated by star formation and under the hypothesis that the entire Balmer continuum (i.e. $912\,\AA <\lambda<3646\,\AA$) is absorbed and re-irradiated by dust in the optically thin limit. Therefore, any contribution of the central AGN to the IR luminosity will result in an overestimation of the ${\rm SFR_{IR}}$. The initial mass function (IMF) implicitly assumed in this $L_{\rm TIR}$ to ${\rm SFR}$ conversion is a Kroupa IMF (cite: Kroupa2001), having a slope of $-1.3$ for stellar masses between $0.1-0.5\,M_{\astrosun}$, and $-2.3$ for stellar masses ranging between $0.5$ and $100\,M_{\astrosun}$. In Table [2](#tbl:dust_data) we report all the derived quantities obtained with the dust continuum modeling.

+:--------+:--------------:+:----------------------:+:----------------------:+:--------------------------:+:--------------------------:+:--------------------------------:+
|         | $T_{\rm dust}$ | Log $M_{\rm dust}$     | $\beta$                | Log $L_{\rm FIR}$ $^{(1)}$ | Log $L_{\rm TIR}$ $^{(2)}$ | ${\rm SFR_{IR}}$                 |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
|         | (${\rm K}$)    | ($M_{\astrosun}$)      |                        | ($L_{\astrosun}$)          | ($L_{\astrosun}$)          | ($M_{\astrosun}\,{\rm yr^{-1}}$) |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
| 1-7     | 54             | $8.71^{+0.05}_{-0.04}$ | $1.48^{+0.06}_{-0.05}$ | $13.13^{+0.06}_{-0.06}$    | $13.28^{+0.09}_{-0.09}$    | $2849^{+633}_{-533}$             |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
| 2-7     | 46             | $8.36^{+0.12}_{-0.12}$ | $1.44^{+0.18}_{-0.17}$ | $12.40^{+0.09}_{-0.10}$    | $12.47^{+0.12}_{-0.13}$    | $442^{+140}_{-112}$              |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
|         | 35             | $8.53^{+0.14}_{-0.13}$ | $1.69^{+0.21}_{-0.19}$ | $12.16^{+0.12}_{-0.10}$    | $12.18^{+0.14}_{-0.11}$    | $224^{+75}_{-55}$                |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
| 1-7     | 48             | $7.73^{+0.18}_{-0.20}$ | $1.9^{+0.3}_{-0.3}$    | $12.31^{+0.14}_{-0.13}$    | $12.42^{+0.18}_{-0.17}$    | $392^{+193}_{-128}$              |
|         |                |                        |                        |                            |                            |                                  |
| **QSO** |                |                        |                        |                            |                            |                                  |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
| 2-7     | 47             | $7.0^{+0.4}_{-0.4}$    | $1.7^{+0.5}_{-0.5}$    | $11.28^{+0.25}_{-0.19}$    | $11.4^{+0.3}_{-0.2}$       | $38^{+28}_{-16}$                 |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+
|         | 35             | $7.3^{+0.4}_{-0.4}$    | $1.7^{+0.5}_{-0.5}$    | $11.0^{+0.2}_{-0.2}$       | $11.1^{+0.2}_{-0.3}$       | $19^{+14}_{-8}$                  |
+---------+----------------+------------------------+------------------------+----------------------------+----------------------------+----------------------------------+

: Dust properties in the PJ231-20 and PJ308-21 sources.

Table notes: $^{(1),} {^{(2)}}$Far-infrared and total infrared luminosity obtained by integrating the best-fit modified black body model in the (rest-frame) wavelength range $40-400\,{\rm \mu m}$ (cite: Helou+1988), and $8-1000\,{\rm \mu m}$ (cite: Sanders+2003), respectively.

In the case of the quasar and companion galaxy in PJ231-20 system, we find good constraints both on the dust mass ($\apprle 0.1\,{\rm{dex}}$) and the spectral emissivity index (relative error of $\apprle10\%$). On the other hand, the dust temperature values obtained from the posterior probability distribution are consistent within $1\sigma$ with the imposed prior, confirming that $T_{\rm dust}$ cannot be constrained with the fit. In the case of the quasar and companion in the PJ308-21 system, we found only tentative constraints on $M_{\rm dust}$ and $\beta$ due to the poor coverage of the dust spectral energy distributions (SEDs). The best fit values of $\beta$ in both PJ231-20 and PJ308-21 quasars and companions range between $\sim1.5-1.9$, and are consistent with the values estimated in both low redshift sources (cite: Conley+2011; Casey+2012) and those at $z>5-6$ (cite: Riechers+2013; Carniani+2019; Novak+2019; YangJ+2019; Faisst+2020). We note that, although assuming different dust temperatures of $47\,{\rm K}$ and $35\,{\rm K}$ as prior in the dust SED fit of the companion galaxies, we obtained similar results that are consistent within $1.5\sigma$. As shown in Fig. [4](#fig:dust_continuum), this is mainly due to lack of high-frequency continuum measurements, where the peak of dust SED is placed. However, an additional large source of uncertainty in the dust fitting is the optically thin dust approximation. In fact, the shape of the dust SED may be altered by the dust opacity at short wavelength, thus affecting the derived $L_{\rm TIR}$. Furthermore, if a warmer dust component is present, it may significantly contributes to the infrared luminosity.

# Ionized medium

## The \[NII\]$_{\rm 205\mu m}$ and \[CII\]$_{\rm 158\mu m}$ fine-structure lines

The ionization potential of the nitrogen atom (${\rm 14.5\,eV}$), is greater than that of neutral hydrogen (${\rm 13.6\,eV}$), therefore the ${\rm N^+}$ emission is due to collisions with electrons in the fully ionized medium. For an electron temperature of 8000 K, the critical density[^3] of \[NII\]$_{\rm 205\mu m}$ line is $n_{\rm e}^{\rm crit}\approx44{\rm\,cm^{-3}}$ (cite: Oberst+2006), thus this line traces the low-density diffuse medium ($n_{\rm e}\sim0.1-1\,{\rm cm^{-3}}$) rather than the dense (HII) regions ($n_e\sim0.5-1.0\times10^{3}\,{\rm cm^{-3}}$) where it is rapidly thermalized and its emission is collisionally quenched (cite: Herrera-Camus+2016).

The fine-structure transition (${^3P_{3/2}}\!\!\to\!\!{^3P_{1/2}}$) of the C$^+$ ion is one of the major coolants of the cold gas phase ($50\,{\rm K} < T<3000\,{\rm K}$) of the ISM in star-forming galaxies, and is easily detected in ALMA band 6 at $z\apprge 6$. Singly-ionized carbon has a lower ionization potential than HI ($11.3\,{\rm eV}$), therefore \[CII\]$_{\rm 158\mu m}$ arises both from the neutral medium, including atomic clouds and PDRs on the surface of molecular clouds exposed to stellar UV radiation in star-forming regions; and from low-density ionized gas. In the ionized medium, the C$^+$ ion is excited by collisions with electrons and its $158\,{\rm\mu m}$ transition has a critical density of $n_{\rm e}^{\rm crit}\approx46\,{\rm cm^{-3}}$ (cite: Oberst+2006). On the other hand, in the neutral medium, most of the \[CII\]$_{\rm 158\mu m}$ emission is expected to arise from the dense PDRs where C$^+$ is collisionally excited by neutral and molecular hydrogen ($n_{\rm H}^{\rm crit}\simeq3.0\times10^3\,{\rm cm^{-3}}$, $n_{\rm H_2}^{crit}\simeq6.1\times10^3\,{\rm cm^{-3}}$, see (cite: Goldsmith+2012)).

The \[NII\]$_{\rm 205\mu m}$ line provides us with important clues to interpret the observed \[CII\]$_{\rm158\mu m}$ emission (cite: Decarli+2017). We detected the \[NII\]$_{\rm 205\mu m}$ (${^3P_1}\!\!\to\!\!{^3P_0}$) line in the PJ231-20 system with a significance of $\sim 4\sigma$ and $\sim2\sigma$ for the quasar and the companion galaxy respectively (see Figs. [1](#fig:pj231_spectramaps), [2](#fig:pj308_spectramaps)). The line measurements are reported in Table [\[tbl:line_data\]](#tbl:line_data).

## Fraction of \[CII\]$_{\rm 158\mu m}$ emission from PDRs

Since \[CII\]$_{\rm 158\mu m}$ and \[NII\]$_{\rm 205\mu m}$ have similar ionization potentials and critical densities, in the optically thin case, the line ratio in the ionized medium depends essentially only on their relative abundance. Therefore, the observed \[NII\]$_{\rm 205\mu m}$ line emission reveals the fraction of \[CII\]$_{\rm 158\mu m}$ arising from neutral gas. Following (cite: Diaz-Santos+2017), we estimated the fraction of \[CII\]$_{\rm 158\mu m}$ emission arising from PDRs, by assuming a typical ${\rm [CII]}^{\rm ion}_{\rm 158\mu m}/{\rm [NII]}_{\rm 205\mu m}\approx 3$ observed in HII regions (cite: Oberst+2006): $$\begin{equation}
 f({\rm [CII]}^{\rm PDR}) = \frac{{\rm [CII]}^{\rm PDR}_{\rm 158\mu m}}{{\rm [CII]}_{\rm 158\mu m}} \approx  1 - 3\frac{{\rm [NII]}_{\rm 205\mu m}}{{\rm [CII]}_{\rm 158\mu m}}. 
\end{equation}$$

![](images/CII_PDR_fraction_PJ231-20_twoT.pdf)

We note that, while the \[CII\]/\[NII\] ratio for HII regions assumes Solar metallicities, the high dust content seen in $z\apprge 6$ quasar host galaxies suggests that the metallicities are indeed high (see e.g. (cite: Novak+2019), furthermore this is also supported –although indirectly– by studies on the metallicity of the broad line region in $z\sim6$ quasars, see e.g. (cite: Pentericci+2002; Jiang+2007; Onoue+2020)). Combining our \[CII\]$_{\rm 158\mu m}$ line luminosity measurements with those of the \[NII\]$_{\rm 205\mu m}$ line (see Table [\[tbl:line_data\]](#tbl:line_data)), we conclude that PDRs account for $\apprge 80\%$ of the \[CII\]$_{\rm 158\mu m}$ emission in both the PJ231-20 QSO and its companion galaxy. This result is consistent with previous studies on local starburst galaxies showing that no more that $\sim30\%$ of the \[CII\]$_{\rm 158\mu m}$ emission is emitted by the diffuse ionized medium (cite: Carral+1994; Lord+1996; Colbert+1999). Studies of the \[CII\]/\[NII\] ratio in FIR bright galaxies at higher redshifts ($z>4-5$) have also concluded that only a small fraction of \[CII\]$_{\rm 158\mu m}$ emission arises from the ionized gas-phase ISM (cite: Decarli+2014; Pavesi+2016).

In Figure [5](#fig:cii_pdr) we compare $f({\rm [CII]}^{\rm PDR})$ and the dust temperature of the PJ231-20 QSO and its companion with a sample of local luminous infrared galaxies (LIRGs) reported in (cite: Diaz-Santos+2017), and with the value of two high-$z$ quasars: the SDSS J2310+1855 at $z=6.00$ (cite: Li+2020b; Li+2020) and the most distant quasar know so far, ULAS J1348+0928 at $z=7.54$ (cite: Novak+2019). (cite: Diaz-Santos+2017) find that galaxies with warmer $T_{\rm dust}$ show an higher $f({\rm [CII]}^{\rm PDR})$; therefore the fraction of \[CII\]$_{\rm 158\mu m}$ emitted from PDR increases in highly star-forming systems. The authors also rule out a significant role for AGN in increasing $f({\rm [CII]}^{\rm PDR})$ in galaxies. A possible interpretation is that HII regions are more enshrouded by dust in high $T_{\rm dust}$ galaxies than those of more evolved systems with lower $T_{\rm dust}$ in which stellar feedback processes have already cleared out most of the dust from the star-forming regions (cite: Diaz-Santos+2017). That is, the fractions of \[CII\]$_{\rm 158\mu m}$ arising from the ionized medium is associated with low-density ’fossil’ HII regions and diffuse ionized gas not associated with hot young stars. While the high dust temperatures ($47 - 54\,{\rm K}$) of the high-$z$ galaxies presented in this work lie outside the range of the LIRG sample, in the case of the PJ231-20 companion, the assumption of $T_{\rm dust}=35\,{\rm K}$ place this object in agreement with the trend of local LIRGs shown in Fig. [5](#fig:cii_pdr).

## IR line deficits

The ratio of the luminosity of ISM cooling lines, such as $L_{\rm [CII]{158\mu m}}$, $L_{\rm [NII]{205\mu m}}$ to the total IR luminosity ($L_{\rm TIR}$), measures the ratio of the cooling of the gas to that of the dust. These ratios decrease by $\sim1-2$ orders of magnitude with increasing dust temperature and IR luminosity in local galaxies (cite: Malhotra+1997; Gracia-Carpio+2011; Farrah+2013; Diaz-Santos+2013; Diaz-Santos+2017; Zhao+2013; Zhao+2016; Herrera-Camus+2018) and those at high-redshift (cite: Decarli+2012; Decarli+2014; Banados+2015; Novak+2019; Rybak+2019). The underlying cause of the so-called ’line deficits’ are still debated. The physical arguments most often proposed include changes in ionization parameter producing high dust to gas opacity ratio, optically thick dust screening part of the line emission, and progressive thermalization of the lines with low critical densities. However, a possible explanation is that HII regions are dustier in IR-bright galaxies than in low-luminosity systems (cite: Luhman+2003; Gonzalez-Alfonso+2008; Abel+2009; Gracia-Carpio+2011; Farrah+2013; Riechers+2014; Diaz-Santos+2017; Herrera-Camus+2018b). In this scenario, a higher fraction of UV photons produced by young stars are absorbed by dust, thus suppressing ionizing photons that would otherwise be absorbed by the neutral medium, thereby decreasing the photoionization heating efficiency the net effect is to decrease the line emission relative to the IR luminosity. On the other hand, if \[CII\]$_{\rm 158\mu m}^{\rm ion}$ and \[NII\]$_{\rm 205\mu m}$ emission arise from different ISM phases (i.e., low-density regions and diffuse ionized gas not associated with hot young stars) than the IR continuum emission, then the line deficit could be driven by a boosting of IR luminosity rather than a deficit in the observed line flux. However, consistently with what was discussed in Sect. [6.2](#ssect:cii_fraction), a fraction of this excess of energy can be transferred to the surrounding neutral/molecular medium increasing the \[CII\]$_{\rm 158\mu m}^{\rm PDR}$ emission and therefore decreasing the deficit.

In Fig. [6](#fig:line_deficit) we compare the \[CII\]$_{\rm 158\mu m}$ and \[NII\]$_{\rm 205\mu m}$ line deficits in the quasars and companion galaxies presented in this work, with the local LIRG sample of (cite: Diaz-Santos+2017) and the $z=7.54$ J1342+0928 quasar (cite: Novak+2019). Our findings are consistent within the scatter with the overall trends observed in LIRGs. In particular, the line deficit of the companion galaxy in PJ231-20 system, in the low dust temperature case ($T_{\rm dust} = 35\,{\rm K}$), is typical of the bulk of local LIRG population. Noticeably, while we find that PJ231-20 QSO host and companion galaxies show \[NII\]$_{\rm 205\mu m}$ line deficits that are consistent within the errors, the deficit in \[CII\]$_{\rm158\mu m}$ is significantly more pronounced in the quasar than in the companion galaxy. However, we do not believe that this is evidence that the presence of a powerful AGN affects the \[CII\]$_{\rm158\mu m}$ line deficit (unless the presence of an AGN biases our $L_{\rm TIR}$ measurement): this scenario is excluded from the study of local ULIRGs sample (cite: Diaz-Santos+2013; Diaz-Santos+2017; Farrah+2013) showing no strong dependence of line deficit and \[CII\]$_{\rm 158\mu m}^{\rm PDR}$ fraction with the AGN contribution. In this context, not even higher ionization lines like \[OIII\]$_{\rm 88\mu m}$ seem to be significantly influenced by AGN (cite: Walter+2018). Indeed, in the PJ308-21 system, the quasar shows similar \[CII\]$_{\rm 158\mu m}$ deficit to that of the companion galaxy, and both sources exhibit less extreme deficits than in the PJ231-20 QSO and its companion, thus suggesting that the observed line deficits is not trivially affected by the presence of an AGN. The observed scatter in the $L_{\rm [CII]{\rm 158\mu m}}/L_{\rm TIR}$ ratio could be due in fact to the variation of the PDR contribution to the total \[CII\]$_{\rm 158\mu m}$ with increasing $T_{\rm dust}$ (cite: Diaz-Santos+2017).

![](images/line_deficit_twoT.pdf)

# Atomic medium

## The \[CI\]$_{\rm 369\mu m}$ fine-structure line

We detect the atomic fine-structure line \[CI\]$_{\rm 369\mu m}$ (${^3P_2}\!\!\to\!\!{^3P_1}$) in the PJ231-20 QSO with a significance of $\sim 4.5\sigma$ while we derived upper limits for the companion and for objects in the PJ308-21 system. This line has a critical density of $1.2\times10^3\,{\rm cm^{-3}}$ (cite: CarilliWalter2013), hence it traces the cold dense atomic neutral medium. As the ionization potential of neutral carbon is close to the dissociation energy of the CO molecule it is expected to exist in a narrow range of physical conditions. The \[CI\] emission was once thought to emerge from a thin C$^+$/C/CO transition layer in the molecular clouds (cite: Tielens+1985a; Tielens+1985b; Hollenbach+1999; Kaufman+1999). However, several lines of evidence highlight a close connection between \[CI\] emission and CO rotational transitions, suggesting that the \[CI\] line traces the bulk of molecular gas in galaxies (cite: Ikeda+2002; Papadopoulos+2004; Walter+2011; Alaghband-Zadeh+2013; Israel+2015; Bothwell+2017; Valentino+2018; Valentino+2020). This is also predicted by hydrodynamic simulations (cite: Tomassetti+2014) in which CO and \[CI\] are found to co-exist throughout the bulk of the cold molecular component. A viable explanation is provided by clumpy, inhomogeneous PDR models (cite: Meixner+1993; Spaans+1996) in which the surface layers of \[CI\] are distributed across clumpy molecular clouds.

![](images/CI_FIR_twoT.pdf)

![](images/CII_CI_pdr_xdr_tir.pdf)

## The \[CI\]$_{\rm 369\mu m}/{\rm TIR}$ ratio

In Fig. [7](#fig:ci_fir) we show $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}$ ratio as a function of dust temperature for a variety of galaxies and AGN in the local and high-$z$ Universe (cite: Valentino+2020). The observed average ratio is $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}\sim 10^{-5}$, but there is a negative correlation with $T_{\rm dust}$. However, contrary to the \[NII\]$_{\rm 205\mu m}$ and \[CII\]$_{\rm 158\mu m}$ line deficits (see Fig. [6](#fig:line_deficit)), this trend is not surprising. Indeed, \[CI\] in PDR models are predicted to arise from regions with gas kinetic temperature comparable to dust temperature $T_{\rm dust}$ (cite: Tielens+1985a) with the IR luminosity rises with a high power of $T_{\rm dust}$ ($L_{\rm TIR}\propto T_{\rm dust}^{4+\beta}$), while the line emission into the cloud is only proportional to the gas temperature. Then, the trend shown in Fig. [7](#fig:ci_fir) is also driven by a redshift dependence. Indeed, (cite: Valentino+2018; Valentino+2020) found that, on average, the observed $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}$ ratios are lower in high-$z$ SMGs than in local star-forming and main sequence (MS) galaxies (i.e. those defining a relative tight distribution in SFR and stellar mass $M_\star$, see e.g. (cite: Noeske+2007; Elbaz+2011)). Hence, the most plausible underlying reason of this trend is a potential evolution in the dust temperature with redshift enhancing $L_{\rm TIR}$ (cite: Schreiber+2018; Liang+2019; Ma+2019; Faisst+2020; Riechers+2020). Furthermore, the IR luminosity measured in local AGN and high-$z$ quasars (that also are expected to have higher $T_{\rm dust}$ than star-forming galaxy) could be affected by a substantial contribution from a dusty torus, boosting the observed $L_{\rm TIR}$, thus driving the observed decrease of $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}$ with $T_{\rm dust}$. However, $L_{\rm [CI]{369\mu m}}$ and $L_{\rm TIR}$ trace the neutral gas and the SFR, respectively, thus their ratio is a proxy of the gas depletion timescale $\tau_{\rm dep} = M_{\rm gas}/{\rm SFR}$, representing the efficiency of the star formation. Therefore, the observed trend of $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}$ could be interpreted as due to a decrease of $\tau_{\rm dep}$ (or equivalently higher star-formation efficiency) in high-$z$ SMGs and quasar hosts than in MS and local star-forming galaxies. This result is consistent with several CO-based studies (cite: Daddi+2010; Genzel+2015; Tacconi+2018; Birkin+2020).

We obtained $3\sigma$ upper limits of \[CI\]$_{\rm 369\mu m}$ line for all sources in the systems studied in this paper, except the PJ231-20 QSO for which we measured $L_{\rm [CI]{369\mu m}}/L_{\rm TIR} =2.6^{+1.4}_{-1.1}\times 10^{-6}$. This value together with the assumed $T_{\rm dust}$, locate this source in the parameter ranges observed in other high-$z$ quasars. In particular a similar $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}$ ratio ($4.2^{+0.8}_{-0.8}\times10^{-6}$) has been measured by (cite: YangJ+2019) in the $z\simeq 6.5$ quasar . This result, suggests high star-formation efficiency in these sources relative to their local counterparts. For the other sources studied in this work, we obtained $L_{\rm [CI]{369\mu m}}/L_{\rm TIR} < 10^{-4}-10^{-5}$ limits that are $\sim 1-2$ order of magnitude lower than $L_{\rm [CII]{158\mu m}}/L_{\rm TIR}$. We also estimated a $L_{\rm [CI]{369\mu m}}/L_{\rm [CII]{158\mu m}} \sim 2\%$ in PJ231-20 QSO and $<2-6\%$ in all the other sources. This values are similar to that measured in the quasar host galaxy J1148+5251 at $z=6.42$ by (cite: Riechers+2009). These results support the assumption that \[CI\]$_{\rm 369 \mu m}$ is a less important coolant than the dust continuum and \[CII\]$_{\rm 158 \mu m}$ at such high redshifts. In Sect. [9](#sect:mass_contributions) we further exploit the \[CI\]$_{\rm 369\mu m}$ detections in quasar hosts and companions to put constraints on the amount of neutral carbon and molecular gas in the ISM.

## \[CII\]$_{\rm 158\mu m}$/\[CI\]$_{\rm 369\mu m}$ ratio

The \[CII\]$_{\rm 158\mu m}$/\[CI\]$_{\rm 369\mu m}$ ratio is extremely useful in discerning between PDR and XDR models, as has been used in other high-$z$ studies (cite: Venemans+2017b; Venemans+2017c; Novak+2019). In Fig. [8](#fig:cii_ci_ratio) we show the \[CII\]/\[CI\] intensity ratio obtained from our CLOUDY grids with $N_{\rm H}=10^{23}\,{\rm cm^{-2}}$. In the PDR case, the \[CII\]/\[CI\] ratio ranges between $\apprle 2$ and $\apprge 70$, while in the XDR case it does not exceed a value of $\sim 15$. These ranges are consistent with those that are found in other models in the literature (cite: Kaufman+1999; Meijerink+2007). The different values of the \[CII\]/\[CI\] ratio predicted in PDR and XDR models can be explained by the lower CO/C abundance ratio produced in the XDR regime (cite: Maloney+1996; Meijerink+2005). Indeed, while in PDRs there is a sharp C$^+$/C/CO transition layer at a certain depth in the clouds (depending on both density and FUV field strength), X-ray photons can penetrate much deeper into the cloud affecting its whole structure. As a result, in the XDR regime, both C and C$^+$ are present throughout most of the cloud and their column density increases much more gradually as a function of cloud depth, than in the PDR case.

Additional constraints on the radiation field in galaxies are provided by \[CI\]$_{\rm 369\mu m}/{\rm TIR}$ and \[CII\]$_{\rm 158\mu m}/{\rm TIR}$ luminosity ratios. Indeed, in the PDR case, for high FUV fluxes ($G_0\apprge 10^2$) these ratios are expected to decease as $G_0$ increases, with almost no dependence on ISM density. In fact, by increasing $G_0$, the C$^+$/C/CO transition layer, where \[CI\] transitions take place, is pushed deeper into the cloud while the C column density remains substantially unaffected. The gas heating efficiency due to photoelectric effect on dust grains reaches its maximum values at $G_{0}\sim 10-100$, and becomes less efficient at higher fluxes, while the dust heating per UV photon remains at the same level (cite: Kaufman+1999). In this case, the \[CII\]$_{\rm 158\mu m}$ line luminosity increases logarithmically while IR-luminosity is linearly proportional to $G_0$. As a result, both \[CI\]$_{\rm 369\mu m}$/TIR and \[CII\]$_{\rm 158\mu m}$/TIR luminosity ratios, depends mostly on $G_0$ for high UV fluxes (cite: Tielens+1985a; Kaufman+1999; Gerin+2000).

The observed luminosity ratios, corrected for the fraction of \[CII\]$_{\rm 158\mu m}$ actually arising from PDRs (see Sect. [6.2](#ssect:cii_fraction)) are $L_{\rm [CII]{158\mu m}}/L_{\rm [CI]{\rm 369\mu m}}=46^{+30}_{-14}$, for the PJ231-20 QSO, and $3\sigma$ limits of $> 55, 53, 13$ in the PJ231-20 companion, the PJ308-21 QSO, and the PJ308-21 companion galaxy respectively. Thus for all the sources, the PDR scenario is favored. In the case of the PJ231-20 QSO, this diagnostic points to a density $n_{\rm H}>10^3\,{\rm cm^{-3}}$ and a FUV radiation field strength of $> 10^3\,G_0$. Similar constraints are inferred for all the other sources (see Fig. [8](#fig:cii_ci_ratio)). In addition, by combining the estimated values of $L_{\rm [CI]{369\mu m}}/L_{\rm TIR}$ and $L_{\rm [CII]{158\mu m}}/L_{\rm TIR}$ ratios with the \[CII\]$_{\rm 158\mu m}$/\[CI\]$_{\rm 369\mu m}$ CLOUDY models (see Fig. [8](#fig:cii_ci_ratio)), we constrain FUV flux to $G_0 \simeq 3\times10^4-10^5$ in the PJ231-20 QSO. A similar value is found for the J0439+1634 quasar at $z\simeq6.5$ by (cite: YangJ+2019).

# Molecular medium

## CO rotational lines

Molecular clouds consist almost entirely of molecular hydrogen (H$_2$). Unfortunately, H$_2$ has a zero electric dipole moment, and high vibrational energy levels, thus it is a poor radiator in the physical conditions of the cold ISM. The most abundant molecule after H$_2$ is CO; it has a weak permanent dipole moment and its rotational levels are primarily populated by collisions with H$_2$. CO emission has been widely detected in normal galaxies in the local Universe (see e.g. (cite: Saintonge+2017; Saintonge+2018); and (cite: Tacconi+2020) for a review) and in the highest redshift quasars and SMGs (cite: Riechers+2013; Strandet+2017; Venemans+2017a; Novak+2019; Li+2020), and it provides key information to characterize the ISM. Low-$J$ ($J_{\rm up} < 6$) CO lines have low critical density ($n_{\rm crit}\sim10^3\,{\rm cm^{-3}}$) and excitation temperature, therefore they are associated with cold molecular gas in PDRs. In contrast, high-$J$ ($J_{\rm up} > 7$) transitions have high critical density ($n_{\rm crit}\sim10^5\,{\rm cm^{-3}}$) and mainly trace the high density and/or high temperature gas, and their excitation is typically explained by the presence of an intense X-ray radiation field impinging the molecular clouds in the central region of galaxies (XDRs), or by shocks produced by AGN-driven outflows (cite: Meijerink+2013; Gallerani+2014; Mingozzi+2018; Carniani+2019). Therefore, by combining multiple CO lines, one can study the CO spectral line energy distribution (SLED) that is a powerful tool to disentangle the contribution of star formation and AGN (PDRs vs. XDRs) to the CO line emission and to constrain the properties of different gas phases such as the density of the medium and the intensity of the radiation field (cite: Riechers+2009; Riechers+2013; Stefan+2015; Yang+2017; Canameras+2018; Carniani+2019).

We detect multiple CO lines (7–6, 10–9, 15–14, 16–15) in the PJ231-20 QSO host with various degrees of significance, while we detect only CO(7–6) and CO(10–9) in the companion galaxies. We also only have a marginal CO(15–14) detection in the PJ308-21 QSO. The measurements are reported in Table [\[tbl:line_data\]](#tbl:line_data).

## CO(1–0)–normalized SLEDs

The CO SLED shows the relative luminosity of various CO transitions in an astrophysical source. It is used to gauge the underlying physical conditions (density, intensity and source of the radiation field) of the CO-emitting gas. The intensity of the observed lines is usually normalized to the ground transition, CO(1–0), which however is not observable with ALMA in the targeted sources. Nevertheless, we estimate its intensity following empirical relations between the CO(1–0) and the IR luminosity (cite: CarilliWalter2013). Alternatively, the dust masses estimated via the Rayleigh-Jeans dust continuum (Sect. [5](#ssect:dust)) can be converted into a CO(1–0) luminosity via a gas-to-dust mass ratio, $\delta_{\rm gdr}$, and a CO-to-H$_2$ (light-to-mass) conversion factor, $\alpha_{\rm CO}$ (cite: Bolatto+2013): $L'_{\rm CO(1-0)} = M_{\rm dust} \, \delta_{\rm gdr}/\alpha_{\rm CO}$.

Therefore, by starting from the dust masses derived in Sect. [5](#ssect:dust) we first estimated the molecular gas mass $M_{\rm H_2}$ of our sources, by adopting $\delta_{\rm gdr}= 100$ (e.g. (cite: Genzel+2015), see Sect. [9](#sect:mass_contributions)) then, by employing the typical value of $\alpha_{\rm CO} = 0.8\,({\rm K\, km\,s^{-1}\,pc^2})^{-1}$ (cite: Downes+1998), adopted in the literature for SMGs and quasar hosts (see (cite: CarilliWalter2013) for a comprehensive discussion) and assuming that $75\%$ of the dust-derived gas mass is in molecular form (cite: Riechers+2013; Wang+2016; Venemans+2017a), we find $L_{\rm CO(1-0)} \sim 2.4 \times 10^6\,L_{\astrosun}$ for PJ231-20 QSO, and $L_{\rm CO(1-0)} \sim 2.6 \times 10^5\,L_{\astrosun}$ for PJ308-21 QSO. On the other hand, in the case of companions galaxies, assuming $T_{\rm dust}=47\,{\rm K}$ we find $L_{\rm CO(1-0)} \sim1.1 \times 10^6\,L_{\astrosun}$ and $\sim0.4 \times 10^5\,L_{\astrosun}$ for the source in PJ231-20 and PJ308-21 system, respectively. These values, increase by a factor of $\sim2\times$, assuming a dust temperature of $35\,{\rm K}$. However, the latter are consistent within the uncertainties with the values obtained adopting a higher dust temperature.

In Fig. [9](#fig:co_sleds_comp) we compare the CO measurements of our sources, normalizing by CO(1–0) with the average CO(1–0)–normalized SLEDs of low-$z$ starburst galaxies and AGN, respectively (cite: Mashian+2015; Rosenberg+2015), the Milky Way Galactic Center (cite: Fixsen+1999) and various measurements of $z>6$ sources retrieved from the literature. High-$z$ sources shown include the quasars at $z=6.00$ (cite: Carniani+2019; Shao+2019; Li+2020); at $z=6.12$, (cite: Wang+2013; Carniani+2019); at $z=6.4$, (cite: Walter+2003; Riechers+2009; Stefan+2015; Gallerani+2014); J0439+1634 at $z=6.52$ (cite: YangJ+2019), and , , at $z= 6.61,6.79,6.90$ respectively (cite: Venemans+2017a)[^4], and the $z=6.34$ SMG HFLS 3 (cite: Riechers+2013). For those quasars for which $L_{\rm CO(1-0)}$ was not available in the literature, we derive $L_{\rm CO(1-0)}$ from dust masses provided in (cite: Carniani+2019), using the same assumptions described above for the PJ231-20 and PJ308-21 systems. In addition, we report the CO SLED models obtained from the ASPECS ALMA large program for $z\sim 1-2$ starburst galaxies (cite: Boogaard+2020).

Despite the large uncertainties we can identify an overall trend for the low-$z$ starburst and AGN CO SLEDs. Indeed, starburst CO SLEDs typically reach a peak at $J_{\rm up} \simeq 6-7$ showing a steady decline afterwards. The average CO SLED of local AGN is more excited at high-$J$ ($J_{\rm up}\apprge9-10$) than are that of the starbursts, consistent with the scenario in which high-$J$ CO transitions are associated with a highly excited medium due to the strong radiation field or shocks produced by the AGN activity.

![](images/CO_SLEDs_comparing_twoT.pdf)

Here, the PJ231-20 QSO CO SLED is similar to those of local AGN, in particular the observed CO(10–9)/CO(1–0) luminosity ratio help us to discriminate between AGN and starbursts regime. On the other hand, the CO SLED of PJ231-20 companion galaxy is consistent within $\sim 1\sigma$ with both the starbursts and AGN population, even taking into account the upper limits on CO(15–14)/CO(1–0) and CO(16–15)/CO(1–0) luminosity ratios. On the other hand, if we assume a dust temperature of $35\,{\rm K}$, the CO SLED appears similar to the average CO SLED of starburst galaxies. However, (cite: Mazzucchelli+2019) do not detect the PJ231-20 companion in the rest-frame optical/UV wavelengths, revealing that this source is highly dust-enshrouded with a SED similar to Arp 220, that is both highly star-forming and highly dust-obscured ULIRG in the local Universe. In addition, (cite: Connor+2020) do not detect the PJ231-20 companion even in X-ray observations, thus ruling out the presence of an AGN in this source, at least with luminosity similar to those of optically selected quasars. These previous studies suggest that star formation should dominate the radiation field (and therefore the CO excitation) in this source. While little information is available for the PJ308-21 companion, in the case of the quasar host we observe a high CO(15–14)/CO(1–0) luminosity ratio, possibly revealing the contribution of the AGN exciting this high-$J$ CO ladder (cite: Schleicher+2010; Gallerani+2014; Carniani+2019). Finally, the observed CO(7–6)/CO(1–0) luminosity ratios in both PJ231-20 quasar host and the companion, and the upper limit available for PJ308-21 QSO, are lower than other $z>6$ quasars (cite: Venemans+2017a), while are consistent within uncertainties with average CO SLED model of the $z\apprge 2$ starburst galaxies in the ASPECS field. Interestingly, the latter appears fairly similar to the average CO SLED of local starburst galaxies. However, we note that the CO luminosity ratios in high-$z$ sources suffer from large uncertainties. In particular, the estimate of $L_{\rm CO(1-0)}$ is significantly affected by the assumed gas-to-dust ratio and the uncertainties on dust mass obtained from the dust SED (see e.g. Sect. [5](#ssect:dust)).

## CO SLED models

![](images/CO_SLEDs_models.pdf)

From the CLOUDY grids, we retrieved the CO line intensities and we normalized them to the CO(1–0) line intensity, thus obtaining the normalized CO SLEDs as function of $n_{\rm H}$ and radiation field flux ($G_0$ or $F_X$ in the case of PDR and XDR models, respectively). In Fig. [10](#fig:co_sled_models) we show the CO SLED models in the PDR and XDR case for two values of cloud gas density, $n_{\rm H} \simeq 0.7\times10^{3}$ and $\simeq1\times10^{5}\,{\rm cm^{-3}}$, with varying radiation field strength at fixed hydrogen column density $N_{\rm H}=10^{23}\,{\rm cm^{-2}}$. The results show that in the PDR case the CO SLED is almost independent of $G_0$, contrary to the XDR case. These behaviors are the direct consequence of a completely different heating mechanism driven by absorption of UV and X-ray photons. Indeed, X-rays have very low cross sections and therefore can penetrate much deeper into the cloud (at column densities $>10^{22}\,{\rm cm^{-2}}$), furthermore, X-ray photons have high heating efficiency compared to UV photons, thus keeping molecular clouds at high temperature even at high column density (cite: Maloney+1996; Lepp+1996; Meijerink+2005). As expected, in both the PDR and XDR cases, the peak of the CO SLED rises and shifts to higher $J$ values as the density increases. Indeed, the population of high-$J$ CO levels (set by the competition of collisional excitation and radiative de-excitation) increases with increasing cloud density due to the higher critical densities of such lines, and progressively thermalizes, saturating at a certain value. In the optically thick and high temperature (or low-frequency) limit, the luminosities (in $L_{\astrosun}$ unit) of CO rotational lines are approximately proportional to $J^3$ (cite: Obreschkow+2009; daCunha+2013; Narayanan+2014). At higher-$J$ transitions the PDR CO SLED drops considerably and flattens on a low level due to the small amount of hot gas in the outer layer of the molecular cloud. On the other hand, in XDRs, a much larger fraction of the gas is at higher temperature, thus the CO SLED does not drop as dramatically. For this reason, observations of high-$J$ CO lines should reveal the presence of an additional source of heating, such for example X-rays (cite: Schleicher+2010). We note that our CO SLED model predictions are in agreement with other PDR/XDR CLOUDY models reported in literature (cite: Vallini+2018; Vallini+2019).

For the PJ231-20 QSO, the mere detection (although at modest significance) of very high-$J$ CO transitions, with estimated $L_{\rm CO(15-14)}/L_{\rm CO(1-0)}$ and $L_{\rm CO(16-15)}/L_{\rm CO(1-0)}$ ratios of $\sim 100$, immediately points to a significant XDR contribution. In Fig. [11](#fig:co_sled_fit) we show our best-fit CLOUDY models of the CO SLED in PJ231-20 QSO obtained by minimizing $\chi^2$. The high-$J$ normalized CO fluxes ($J_{\rm up}=15, 16$) in the PJ231-20 QSO cannot be reproduced by a single PDR model. We obtained excellent agreement by using a composite (PDR+XDR) model in the form $W_{\rm PDR}F_{\rm CO}^{\rm PDR}(n_{\rm H}^{\rm PDR},G_0)+W_{\rm XDR}F_{\rm CO}^{\rm XDR}(n_{\rm H}^{\rm XDR},F_{\rm X})$, adopting $N_{\rm H}=10^{23}\,{\rm cm^{-3}}$. Here $W_{\rm PDR}$ and $W_{\rm XDR}$ are the relative contributions of the PDR ($F_{\rm CO}^{\rm PDR}$) and XDR component ($F_{\rm CO}^{\rm XDR}$) to the CO(1–0) emission, respectively. The best-fit model has $W_{\rm PDR}=0.90\pm0.04$ and $W_{\rm XDR}=0.10\pm0.04$, total hydrogen density $n_{\rm H}^{\rm PDR}\sim 4\times10^2\,{\rm cm^{-3}}$, $n_{\rm H}^{\rm XDR}\sim5\times10^{5}\,{\rm cm^{-3}}$, and UV/X-ray radiation field strength of $G_0\sim1\times10^{5}$ and $F_{\rm X}\sim10\,{\rm erg\,s^{-1}\,cm^{-2}}$, respectively. Since we consider the same column densities for PDR and XDR models, $W_{\rm PDR}$ and $W_{\rm XDR}$ are directly connected with the CO mass budget in the ISM. Therefore, this result indicates that PDRs account for $\sim90\%$ of the molecular mass in the quasar host. However, while XDRs account for a small fraction of the molecular mass, they dominate the CO emission at $J_{\rm up}\ge 10$. In the PJ231-20 QSO, we measured $L_{\rm CO(7-6)}/L_{\rm CO(1-0)}=93_{-12}^{+13}$. This ratio is $\sim 30\%$ with respect to the value expected for CO thermalized emission in the optically thick and Rayleigh-Jeans limit (described by $J^3$ curve in Fig. [11](#fig:co_sled_fit)).

![](images/CO_SLED_PJ231-20_fit_twoT.pdf)

However, although the composite model allows us to accurately reproduce the observed CO SLED in the PJ231-20 QSO, the number of free parameters is greater than data points, thus producing degeneracies in best-fit parameters. In Fig. [11](#fig:co_sled_fit), we also show the best-fit model obtained employing a single XDR component. In this case, the best-fit model is roughly in agreement with the observed CO SLED in the PJ231-20 QSO, with a value $n_{\rm H} \sim 4\times10^{2}\,{\rm cm^{-3}}$, but it points to an extreme value of the X-ray radiation field intensity of $F_{\rm X} \sim 10^2\,{\rm erg\,s^{-1}\,cm^{-2}}$, corresponding to the upper boundary of the parameter space. Therefore, this result should be taken into account with caution.

In Fig. [11](#fig:co_sled_fit) we also report the observed CO SLED in the PJ231-20 companion galaxy and the PJ308-21 QSO. Despite detecting $L_{\rm CO(7-6)}/L_{\rm CO(1-0)}$ and $L_{\rm CO(10-9)}/L_{\rm CO(1-0)}$ in the PJ231-20 companion, we cannot safely infer a significant XDR contribution in this source due to the lack of high-$J$ CO detections. On the other hand, the high $L_{\rm CO(15-14)}/L_{\rm CO(1-0)}\sim 3\times 10^2$ measured in the PJ308-21 QSO (although with low S/N), can only be reproduced with our models by adopting a strong XDR component.

Overall, our CO SLED modeling suggest that a significant contribution to CO emission arises from clouds exposed to X-ray radiation, at least in quasar hosts. This result appears to be in contrast with our ${\rm [CII]_{158\mu m}}/{\rm [CI]_{369\mu m}}$ modeling discussed in Sect. [7.3](#ssect:cii_ci). However, from our composite PDR+XDR model, we found that PDRs dominate the molecular mass budget and thus dominate the \[CII\]$_{\rm 158\mu m}$ and \[CI\]$_{\rm 369\mu m}$ emission. In this scenario, the high-$J$ CO lines arise mainly from molecular medium in the central region of quasar host galaxy, while emission from lower $J$ CO lines and FSLs trace the ISM on larger scales. Indeed, the good correlation between \[CI\] and $J\le 7$ CO lines, suggests that these lines trace the spatially extended gas reservoir associated with vigorous star formation rather than denser and more concentrated gas traced by high-$J$ CO lines (see e.g. (cite: Gerin+2000; Engel+2010; Ivison+2011; Jiao+2017) for studies on nearby sources, and e.g. (cite: Weiss+2005; Tacconi+2008; Bothwell+2010; Bothwell+2013; Riechers+2011; Walter+2011; Yang+2017; Valentino+2018; Valentino+2020), for intermediate and high-$z$ works).

Finally, we stress that the uncertainties reported in our CO(1–0)-normalized SLEDs are statistical errors, ignoring any systematic uncertainties associated with the assumption of a gas-to-dust ratio by which we estimated the CO(1–0) luminosity in this work; therefore our results should be considered tentative. In order to better constrain the relative contribution of PDRs and XDRs in these sources we need observations of other CO lines over a wide range of values of $J$. We also point out that the presented analysis does not rule out the possibility that the other source of heating such as cosmic rays, shocks or mechanical heating from turbulence may contribute significantly to the mid-/high-$J$ CO excitation (cite: Hollenbach+1989; Flower+2010; Mingozzi+2018; Godard+2019; Vallini+2019)

## H$_2$O rotational lines

Water vapor emission is a tracer of the molecular warm dense phase of the interstellar medium (cite: Liu+2017), where UV/X-ray radiation from newly formed star or powerful AGN raises the dust temperature above the ice evaporation temperature (cite: Cernicharo+2006). In such regions, the H$_2$O molecule can be released into the gas phase by photodesorption from dust grains (cite: Hollenbach+2009), or by sputtering of grains in shocked-heated regions (cite: Bergin+2003; Gonzalez-Alfonso+2012; Gonzalez-Alfonso+2013) where H$_2$O becomes the third most abundant species and the strongest molecular emitter after the high-$J$ ($J_{\rm up}>7-8$) CO transitions. The H$_2$O molecule can also be formed in the gas phase through ion-neutral chemistry and neutral-neutral endothermic reactions (cite: Graff+1987; Wagner+1987; Hollenbach+2009). Lower level transitions ($E_{\rm upper} < 200\,{\rm K}$) arise in collisionally excited gas with kinetic temperature of $\sim100\,{\rm K}$ and clump densities of the order of $3\times10^6 {\rm cm^{-3}}$ where they may play an important role as a cooling agent (cite: Neufeld+1993; Neufeld+1995; Bradford+2011). On the other hand, due to the high critical density for collisional excitation of higher levels ($n_{\rm crit} \apprge 10^7 - 10^8\,{\rm cm^{-3}}$, e.g. (cite: Faure+2007; Faure+2008; Daniel+2012)), water excitation require instead radiative excitation by intense far-IR radiation field from warm dust (cite: Weiss+2010; Gonzalez-Alfonso+2014) and the intensity of the lines is found to be nearly linear proportional with the total infrared luminosity of the galaxies (cite: Omont+2013; Yang+2013; Yang+2016; Liu+2017). As both collisions and IR pumping are responsible for populating the water energy levels, H$_2$O lines not only probe the physical conditions of the warm and dense molecular gas-phase ISM but also provide important clues about the dust IR radiation density.

Previous ground-based observations of water lines in nearby galaxies were limited by telluric atmospheric absorption, and consequently have been restricted to radio maser transitions and a few transitions in IR-luminous galaxies (cite: Combes+1997; Menten+2008). On the other hand, observational campaigns using space telescopes (e.g., Infrared Space Observatory (ISO), *Herschel*/PACS/SPIRE) have been successful in detecting H$_2$O features in local galaxies (cite: Fischer+1999; Fischer+2010; Gonzalez-Alfonso+2004; Gonzalez-Alfonso+2008; Gonzalez-Alfonso+2010; Gonzalez-Alfonso+2012; vanderWerf+2010; Weiss+2010; Rangwala+2011; Spinoglio+2012; Pereira-Santaella+2013). Furthermore, various H$_2$O emission lines have been detected at higher redshifts ($z>1-2$) in starburst galaxies and Hyper/Ultra Luminous Infrared Galaxies (cite: Bradford+2011; Lis+2011; Omont+2011; Omont+2013; vanderWerf+2011; Combes+2012; Lupu+2012; Bothwell+2013; Yang+2013; Yang+2016; Yang+2019; Yang+2020) and also in a $z>6$ SMG (cite: Riechers+2013) and a lensed $z>6$ quasar host galaxy (cite: YangJ+2019).

In this work, we present sub-mm H$_2$O emission in our two $z>6$ non-lensed quasar host galaxies. In particular, we report three H$_2$O line detections in PJ231-20 QSO ($3_{12}-2_{21}$; $3_{21}-3_{12}$; $3_{03}-2_{12}$), and a tentative detection of H$_2$O $3_{03}-2_{12}$ in PJ308-21 QSO, while we only have upper limits on water lines from the companion galaxies. The water vapor energy levels, and the targeted (ortho-)H$_2$O transitions are reported in Fig. [12](#fig:water_levels). The H$_2$O $3_{12}-2_{21}$ and $3_{21}-3_{12}$ lines are likely mainly produced by the cascade process in response to absorption of IR photons at $75\,{\rm \mu m}$, while the H$_2$O $3_{03}-2_{12}$ line is more sensitive to collisions and is enhanced in systems with higher gas kinetic temperature (cite: vanderWerf+2011; Gonzalez-Alfonso+2014; Liu+2017).

![](images/water_energy_levels.pdf)

![](images/LH2O_LTIR_twoT.pdf)

## The $L_{\rm H_2O}- L_{\rm TIR}$ relation

In the upper panel of Fig. [13](#fig:lh2o_ltir) we compare the H$_2$O $3_{21}-3_{12}$ line with the total IR luminosity obtained through the fit of the dust SED of the PJ231-20 QSO and its companion (see Table [2](#tbl:dust_data)), with a sample of nearby ULIRGs presented in (cite: Yang+2013). For this comparison, we also included H$_2$O detections of $z\sim 2.5-3.5$ Hy/ULIRGs from (cite: Yang+2016), APM 08279+5255 at $z\simeq3.9$ (cite: vanderWerf+2011), the $z=6.34$ SMG HFLS 3 (cite: Riechers+2013), and J0439+1634, a $z\simeq6.5$ quasar host galaxy (cite: YangJ+2019). Our data are consistent within the uncertainties with the almost linear relation found by (cite: Yang+2013; Yang+2016), $L_{\rm H_2O}\propto L_{\rm TIR}^{1.1-1.2}$. This correlation appears as the straightforward consequence of the IR-pumping mechanism responsible for the population of the upper level ($3_{21}$) of the H$_2$O molecules (cite: Yang+2013), that, after absorption of far-IR photons, cascade via the lines we observe in an approximately constant fraction. However, (cite: Liu+2017) emphasized that the medium-excitation H$_2$O transitions (such as $3_{21}-3_{12}$) probe the physical regions of galaxies in which a large fraction of FIR emission is generated. Therefore, the observed $L_{\rm H_2O}- L_{\rm TIR}$ correlation could be largely driven by the sizes of FIR- and water vapor-emitting regions. The H$_2$O detections presented in this work together with those of (cite: Riechers+2013; YangJ+2019), extend the redshift range explored in the previous works by (cite: Yang+2013; Yang+2016), confirming that this relation seems to hold also at very high-$z$.

(cite: Yang+2013) found slightly different values of $L_{\rm H_2O}/ L_{\rm TIR}$ ratios for the $3_{21}-3_{12}$ transition in local AGN and star-forming-dominated galaxies with possible mild AGN contribution. However, apart from individual studies (e.g. (cite: Gonzalez-Alfonso+2010) for Mrk 231, and (cite: vanderWerf+2011) for APM 08279) showing that AGN could be the main power source exciting the H$_2$O lines in this objects, it is still not clear how a strong AGN could affect the H$_2$O emission. One possibility is that the buried AGN gives a larger TIR-to-$75{\rm \mu m}$ luminosity ratio than in starburst galaxies due to the different shape of the IR SED of these sources (cite: Kirkpatrick+2015; Yang+2016). In addition, high X-ray fluxes can photodissociate H$_2$O molecules. On the other hand, high dust continuum opacity at $100\,{\rm \mu m}$ ($\tau_{100}$) and/or large velocity dispersion can enhance the H$_2$O luminosity (cite: Gonzalez-Alfonso+2014; Yang+2016).

For the $3_{21}-3_{12}$ transition toward PJ231-20 QSO, we find $L_{\rm H_2O}/ L_{\rm TIR}\sim 1.2\times10^{-5}$, comparable with the ratio measured in the $z\sim6.5$ quasar J0439+1634 (cite: YangJ+2019). This value is higher than the average ratio measured by (cite: Yang+2013) in local AGN-dominated sources ($7\pm3\times10^{-6}$) and is consistent with that measured in star-forming galaxies ($1.1\pm0.6\times 10^{-5}$), suggesting a significant contribution of star formation to the IR radiation exciting the H$_2$O line. In Fig. [13](#fig:lh2o_ltir) we also report the $L_{\rm H_2O}/ L_{\rm TIR}$ ratios for $3_{12}-2_{21}$ and $3_{03}-2_{12}$ transitions detected in the PJ231-20 QSO and the tentative H$_2$O $3_{03}-2_{12}$ detection in the PJ308-21 QSO. These values are in the range measured for the $3_{21}-3_{12}$ transition in local ULIRGs.

## H$_2$O($3_{21}-3_{12}$)–normalized SLED 

By combining the three water vapor lines detected in PJ231-20 QSO, in Fig. [14](#fig:h2osled_comparing) we trace the line flux ratios, that is the normalized H$_2$O SLED, and we compare with the results on local and high-$z$ sources found in the literature. The SLEDs were normalized to H$_2$O $3_{21}-3_{12}$, a medium-excitation line that is predicted to be easily radiatively pumped in the warm dense medium (cite: Liu+2017). Therefore the ratios with the other transitions directly reflect the effect of IR-pumping line excitation.

![](images/H2O_SLEDs_comparing.pdf)

In Fig. [14](#fig:h2osled_comparing), the average H$_2$O SLED of the local ULIRG sample by (cite: Yang+2013), shows two peaks at the energy of H$_2$O $2_{02}-1_{11}$ and $3_{21}-3_{12}$ transitions, indicating high IR pumping efficiency at $75\,{\rm \mu m}$. This is consistent with the models of (cite: Liu+2017) showing that these two lines are efficiently pumped in the warm ISM component at $T_{\rm dust}\apprge 40\,{\rm K}$. The bulk H$_2$O emission observed in star-forming galaxies of (cite: Yang+2013) is explained by (cite: Gonzalez-Alfonso+2014) by model with $T_{\rm dust}=55-75\,{\rm K}$, $\tau_{100}\sim 0.1$ and H$_2$O column density $N_{\rm H_2O}\sim (0.5-2)\times 10^{17}\,{\rm cm^{-2}}$, including a significant contribution from both collisional excitation and line radiative pumping. Despite significant uncertainties, the observed H$_2$O line ratios in the PJ231-20 QSO show a clear peak at $3_{21}-3_{12}$ transition. In particular the line ratio $3_{12}-2_{21}/3_{21}-3_{12}$ is consistent with the value observed in $z\sim6.3$ SMG HFLS 3 (cite: Riechers+2013) and in the $z\sim6.5$ quasar J0439+1634 (cite: YangJ+2019) whose H$_2$O SLEDs also peak at $3_{21}-3_{12}$. The stronger intensity of H$_2$O $3_{21}-3_{12}$ measured in the PJ231-20 QSO than the other transitions lower in the cascade, in conjunction with the high critical density of the observed transitions ($\apprge10^8\,{\rm cm^{-3}}$), suggests that the contribution from collisional excitation of the upper energy levels of the observed water vapor transitions is minor. Other factors that could contribute to the PJ231-20 QSO H$_2$O SLED’s peak at $3_{21}-3_{12}$ are the shape of the IR dust SED that peaks close to $75\,{\rm \mu m}$, thus allowing high pumping efficiency, together with the large FWHM ($\sim 400\,{\rm\, km\,s^{-1}}$) of the H$_2$O $3_{21}-3_{12}$ line, which increases the cross-sections for absorbing pumping photons (cite: Gonzalez-Alfonso+2014).

In the next section we retrieve quantitative information on the ISM associated with the H$_2$O emission by modeling the water vapor SLED using our CLOUDY models.

![](images/H2O_SLEDs_models.pdf)

## H$_2$O SLED models

Our CLOUDY outputs predict emergent intensities of a large number of water vapor transitions. In Fig. [15](#fig:h2o_sled_models) we report the H$_2$O SLED normalized to H$_2$O $3_{21}-3_{12}$ line in the PDR and XDR regimes. We do so for two representative values of total hydrogen density $n_{\rm H}\simeq 2\times 10^2\,{\rm cm^{-3}}$ and $\simeq 4\times 10^4\,{\rm cm^{-3}}$ with varying radiation field strength with fixed total hydrogen column density $N_{\rm H}=10^{24}\,{\rm cm^{-2}}$.

In both PDR and XDR cases the H$_2$O SLED flattens as the intensity of the radiation field increases. In particular, $L_{\rm H_2O}/L_{\rm H_2O(3_{21}-3_{12})}$ line ratios for transitions with energy upper level $E_{\rm up} < 300\,{\rm K}$, approach similar values varying within a factor of $\sim 4$. Since the total hydrogen density of the cloud models spans a range that is well below the typical critical density of H$_2$O lines ($\sim 10^8-10^9{\rm cm^{-3}}$), this could be explained in terms of a progressively more efficient IR pumping of the high-lying H$_2$O energy levels as the UV/X-ray photon flux increases, that subsequently cascade radiatively toward low energy levels. This implies that these H$_2$O lines tend to statistical equilibrium, in agreement with the analysis of, e.g. (cite: Gonzalez-Alfonso+2014; Liu+2017). Furthermore, as also mentioned in Sect. [8.4](#ssect:water_vapor), at gas kinetic temperature $\apprge300\,{\rm K}$, water molecules can form in the gas phase via the neutral-neutral endothermic reaction ${\rm OH + H_2\,\to\,H_2O + H}$. Therefore, an increase of the total hydrogen density ($n_{\rm H} > 10^4\,{\rm cm^{-3}}$) inside the cloud requires higher radiation field flux ($G_0>2\times10^4$, $F_{\rm X}>0.05 - 0.1\,{\rm erg\,s^{-1}\,cm^{-2}}$) to maintain gas temperature above the reaction activation barrier in a large volume of the cloud in order to produce a significant H$_2$O column density $N_{\rm H_2O}> 10^{15}\,{\rm cm^{-2}}$ (cite: Neufeld+1995; Neufeld+2002; Cernicharo+2006; Meijerink+2011). On the other hand, in XDRs, strong X-ray radiation can photodissociate a large fraction of the H$_2$O molecules, thus quenching their line emission. However, since the H$_2$O $3_{21}-3_{12}$ transition is one of the most sensitive to the pumping by IR photons (cite: Liu+2017), low UV/X-ray fluxes cannot efficiently populate its upper level, producing unphysical results in the predicted $L_{\rm H_2O}/L_{\rm H_2O(3_{21}-3_{12})}$. In Fig. [15](#fig:h2o_sled_models), to exclude such non-physical results that clearly at odds with observations, we report those H$_2$O SLEDs for which the H$_2$O $3_{12}-2_{21}$ predicted intensity is at least $10^{-2}\times$ that of CO(10–9) line, since these two lines have similar frequency and are observed to have similar fluxes (see Fig. [1](#fig:pj231_spectramaps) of this work, but see also e.g. (cite: Riechers+2013; YangJ+2019)).

By using the H$_2$O line ratios predicted by our CLOUDY models, we performed the H$_2$O SLED fit of PJ231-20 QSO. We report the results in Fig. [16](#fig:h2o_sled_fit_pj231). The observed H$_2$O line ratios of PJ231-20 QSO cannot be satisfyingly reproduced by any models with $N_{\rm H}=10^{23}\,{\rm cm^{-2}}$, while the agreement between data and best-fit model significantly improves employing higher column density PDR model with $N_{\rm H}=10^{24}\,{\rm cm^{-2}}$. The resulting best-fit model points to a high density medium with $n_{\rm H}\sim 0.8\times10^5\,{\rm cm^{-3}}$, exposed to a strong FUV radiation field with $G_{0}\sim 5\times 10^5$. The mere requirement of a high cloud column density implies that the observed water vapor transitions arise deep in the cloud where the water vapor column density reaches $N_{\rm H_2O}\apprge 3\times 10^{17}\,{\rm cm^{-2}}$. Furthermore, since the H$_2$O line ratios observed in PJ231-20 QSO are similar, and given that the three H$_2$O transitions $3_{21}-3_{12}$; $3_{12}-2_{21}$; $3_{03}-2_{12}$ have similar frequencies and are connected by a cascade process, our result suggests that these lines are near statistical equilibrium. However, the low number of data points makes the result uncertain, in particular the cloud density is poorly constrained with the fit. On the other hand, the high density value found for the PJ231-20 QSO H$_2$O lines, is in the range typically inferred from H$_2$O SLED modeling in local sources (cite: Gonzalez-Alfonso+2014; Liu+2017) and high-$z$ quasar (cite: vanderWerf+2011)

## OH transitions

The hydroxyl radical (OH) is a key intermediary molecule that forms in warm PDRs exposed to FUV radiation via the endothermic reaction between atomic oxygen and vibrationally-excited H$^*_2$. Further reaction with H$_2$ leads to the formation of H$_2$O. On the other hand, water vapor can photodissociate in gas unshielded to FUV radiation producing OH. OH can also form in shocked gas where high gas temperatures can overcome the activation barrier of the O $+$ H$_2$ reaction, or in quiescent obscured regions irradiated by cosmic rays or X-rays via ion-neutral reactions starting from H$^+_3$ (cite: Hollenbach+1997; Agundez+2010). The OH molecule has a large dipole moment ($1.668$ Debye), therefore radiative rates of its rotational transitions are generally high compared to those of CO. The critical densities of OH transitions are of the order of $10^9-10^{10}\,{\rm cm^{-3}}$ (cite: Destombes+1977; Dewangan+1987), implying that OH excitation cannot be driven by collisions, indeed radiative pumping by IR photons is typically invoked to explain its emission. The electronic ground state has two fine-structure levels, $^2\Pi_{3/2}$ (the ground state) and $^2\Pi_{1/2}$, each of which has two $\Lambda$-doubling levels (further split in two hyper-fine sublevels) . Furthermore, the OH molecule can also have rotational angular momentum ($J$), resulting in a ladder of rotational states with increasing $J$. The OH ground state $^2\Pi_{3/2}$ ($J=3/2$) can absorb IR radiation near $119\,{\rm \mu m}$, $79\,{\rm \mu m}$, $53\,{\rm \mu m}$ and $35\,{\rm \mu m}$, followed by spontaneous radiative decay which repopulates the four ground sublevels, including the FIR OH cross-ladder transitions whose radiative rates are $\sim 100\times$ weaker than the rotational transitions. OH transitions, either in absorption or emission, were detected in local Seyfert galaxies, including M82 (cite: Colbert+1999), NGC 253 (cite: Fischer+1999; Bradford+1999), IRAS 20100-4156 and 3Zw35 (cite: Kegel+1999), Arp 220 (cite: Gonzalez-Alfonso+2004), NGC 1068 (cite: Smith+2004; Spinoglio+2005), Mrk 231 (cite: Gonzalez-Alfonso+2008), and NGC 4418 (cite: Gonzalez-Alfonso+2014). Systematic searches for OH emission have revealed that some OH lines exhibit P-Cygni profiles, suggesting massive molecular outflows in samples of local (U)LIRGs and quasars (cite: Fischer+2010; Gonzalez-Alfonso+2010; Gonzalez-Alfonso+2012; Gonzalez-Alfonso+2013; Gonzalez-Alfonso+2017; Sturm+2011; Spoon+2013; Veilleux+2013; Herrera-Camus+2020). OH emission has also been detected at $z\apprge6$ in the SMG HFLS 3 (cite: Riechers+2013), and in the quasar J1319+0950 (cite: Herrera-Camus+2020), demonstrating the feasibility in detecting such lines at very high-$z$ with ground-based observations.

![](images/H2O_SLEDs_fit.pdf)

Here we present detections of $\Lambda$-doublet OH$_{\rm 163 \mu m}$ in the PJ231-20 QSO and companion galaxy together with a tentative detection in the PJ308-21 QSO. So far, this doublet, when detected in other galaxies, has been mostly observed in emission. These lines are likely produced by a fluorescent-like mechanism through absorption of IR photons at $35\,{\rm \mu m}$ and $75\,{\rm \mu m}$ emitted by warm dust, and thus they trace the warm moderate-dense molecular medium ($T\sim 150-300\,{\rm K}$, $n_{H_2}\apprle 10^4-10^{5}\,{\rm cm^{-3}}$) in star-forming regions (cite: Goicoechea+2002; Goicoechea+2005). The observed OH line fluxes in our systems are comparable with those of mid-$J$ CO, and greater than H$_2$O lines, showing that OH can be a powerful tracer of the molecular medium at $z\sim6$. We find similar $L_{\rm OH}/L_{\rm TIR}$ ratios $\sim 2-4\times10^{-5}$ in both PJ231-20 and PJ308-21 quasars, while we estimated a larger value $\sim 10^{-4}$ in the PJ231-20 companion galaxy. A similar value is found in the SMG AzTEC-3 and HFSL 3 at $z=5.3$ and $z=6.34$, respectively (cite: Riechers+2013; Riechers+2014).

## H$_2$O/OH$_{\rm 163\mu m}$ ratio

To obtain further constraints on the molecular medium in the targeted systems, we inspected the line intensity ratios between the observed H$_2$O lines and the OH$_{\rm 163\mu m}$ doublet. Indeed, formation of the OH molecule can occur through the neutral-neutral reaction ${\rm H_2 + O \to OH + H}$ that can successively react to form H$_2$O, or by destruction of water (cite: Elitzur+1978; Poelman+2005; Meijerink+2011). Furthermore, both H$_2$O and the OH molecule have very high critical densities $\apprge10^8\,{\rm cm^{-3}}$, and IR pumping possibly has a dominant role in their excitation. Therefore, the H$_2$O lines and OH$_{\rm 163\mu m}$ are expected to arise from regions with similar physical properties.

In Fig. [17](#fig:h2o_oh_lines) we compare the observed values of the H$_2$O/OH$_{\rm 163\mu m}$ line ratios with our CLOUDY predictions in a diagnostic plot. Here, we considered OH$_{\rm 163\mu m}$ as the sum of the luminosity of the two $\Lambda$-doubling transitions of the OH$_{\rm 163\mu m}$, including the hyper-fine structure lines. In the case of the PJ231-20 QSO, model predictions are fully consistent with what we found in Sect. [8.7](#ssect:h2o_models), pointing to a high density medium exposed to a strong FUV field. We also found similar constraints for the companion galaxy and the PJ308-21 QSO, with $G_0>10^4$ and $n_{\rm H}<1.5\times10^4-0.5\times10^6\,{\rm cm^{-3}}$, respectively. These findings, albeit for a lower column density, are also in broad agreement with the constraints obtained from \[CII\]$_{\rm 158\mu m}$/\[CI\]$_{\rm 369\mu m}$ ratios and the CO SLED modeling (see Sects. [7.3](#ssect:cii_ci) and  [8.3](#ssect:co_models)).

# Mass budgets

Starting from the FSL luminosities obtained in this work (see Table [\[tbl:line_data\]](#tbl:line_data)) and by adopting simplistic assumptions, we can estimate the mass contributions in our systems in the form of ionized, atomic and molecular mediums. In the 2-level approximation, assuming local thermodynamical equilibrium (LTE) and in the optically thin limit and Rayleigh-Jeans regime, the beam-averaged column density of a species $s$ in the upper level $u$ is (cite: Goldsmith+1999): $$\begin{equation}
 N_{\rm s} \approx \gamma_{\rm u}\frac{c^2}{8\pi k_{\rm B}}\nu_{\rm obs}^{-2}\,S\Delta\varv \,(1+z)^{-1}, 
\end{equation}$$ with $$\begin{equation}
 \gamma_{\rm u} = \frac{8\pi k_{\rm B} \nu_{\rm ul}^2}{hc^3A_{\rm ul}}\frac{Q(T_{\rm ex})}{g_{\rm u}}e^{E_{\rm u}/k_{\rm B} T_{\rm ex}}. 
\end{equation}$$ Here, $S\Delta\varv$ is the observed line velocity-integrated flux, $A_{\rm ul}$ is the Einstein coefficient, $Q(T_{\rm ex})$ is the partition function of the species $s$ (depending on the excitation temperature $T_{\rm ex}$), and $g_{\rm u}$ and $E_{\rm u}$ are the statistical weight and the energy of the upper level, respectively. The total number of particles of species $s$ is obtained by integrating over the size of the emitting region. Then, by using the definition of line luminosity (cite: Solomon+1992), the total mass of the species $s$ can be expressed as $$\begin{equation}
 M_{\rm s} = C m_{\rm s} \gamma_{\rm u} L'_{\rm line}, \label{eq:mass_species} 
\end{equation}$$ where $C=9.52\times10^{41}$ is the conversion factor between ${\rm km\,pc^2}$ and ${\rm cm^{3}}$, and $m_s$ is the mass of the species $s$.

![](images/mol_diagnostic_plot.pdf)

Using Eq. [\[eq:mass_species\]](#eq:mass_species) we derive the CI mass following (cite: Weiss+2003) via $$\begin{equation}
 M_{\rm CI}[M_{\astrosun}] = 4.566\times 10^{-4}Q(T_{\rm ex})\frac{1}{5}e^{62.5/T_{\rm ex}}L'_{\rm [CI]_{\rm 369\mu m}}, 
\end{equation}$$ where $Q(T_{\rm ex}) = 1+3e^{-T_1/T_{\rm ex}}+5e^{-T_2/T_{\rm ex}}$ is the CI partition function, and $T_1 = 23.6\,{\rm K}$, $T_2 = 62.5\,{\rm K}$ are the energies (per unit of $k_{\rm B}$) above the ground state of the two \[CI\] (${^3P_1}\!\!\to\!\!{^3P_0}$) and (${^3P_2}\!\!\to\!\!{^3P_1}$) transitions respectively. Assuming an excitation temperature of $T_{\rm ex}=30\,{\rm K}$ (cite: Walter+2011) we find for the PJ231-20 QSO a neutral carbon mass of $M_{\rm CI} = (0.7\pm0.3)\times10^7\,M_{\astrosun}$, and carbon mass limit of $M_{\rm CI} < 0.4-0.5\times10^7\,M_{\astrosun}$ for its companion and the sources in the PJ308-21 system. We note that if we assume a higher excitation temperature $T_{\rm ex}=50\,{\rm K}$, the derived $M_{\rm CI}$ would be $\sim 40\%$ lower. Using these mass estimates, we can put constraints on the molecular gas mass ($M_{\rm H_2}$) using the atomic carbon-to-molecular hydrogen abundance ratio derived by (cite: Walter+2011) for a sample of $z=2-3$ FIR-bright sources (SMGs and quasar host galaxies), $X[{\rm CI}]/X[{\rm H_2}] = M_{\rm CI} / (6M_{\rm H_2}) = (8.4\pm3.5)\times 10^{-5}$. Applying this abundance we obtain a molecular gas mass of $M_{\rm H_2} = 1.3^{+1.1}_{-0.6}\times10^{10}\,M_{\astrosun}$ for PJ231-20 QSO and $M_{\rm H_2} < 1.8\times10^{10}\,M_{\astrosun}$ for the companion galaxy and the other sources in the PJ308-21 system.

Following (cite: Ferkinhoff+2011), in the high-temperature limit, we can also derive the minimum mass of ionized hydrogen (H$^+$) assuming that all nitrogen in HII regions is singly ionized as $$\begin{equation}
 M_{\rm min}({\rm H^+}) = \frac{L_{{\rm [NII]}{\rm 205\mu m}} m_{\rm H}}{(g_1/Q(T_{\rm ex}))A_{10}h\nu_{10}\chi({\rm N^+})}\approx 2.27\frac{L_{{\rm [NII]}{\rm 205\mu m}}}{L_{\astrosun}}M_{\astrosun}, 
\end{equation}$$ where $A_{10}$ is the Einstein coefficient for spontaneous emission of the \[NII\]$_{\rm 205\mu m}$ (${^3P_1}\!\!\to\!\!{^3P_0}$) transition ($2.08\times10^{-6}\,{\rm s^{-1}}$), $g_1=3$ is the statistical weight of the $J=1$ level, $\nu_{10} = 1461.1318\,{\rm GHz}$ the rest-frame frequency of the transition, $m_{\rm H}$ is the mass of the hydrogen atom, and $\chi({\rm N^+})$ is the ${\rm N^+/H^+}$ abundance ratio. For the minimum mass case, in our working assumption $\chi({\rm N^+})=\chi({\rm N})$. Therefore, assuming solar metallicity, the ’HII-region’ gas-phase nitrogen abundance is $\chi({\rm N}) = 9.3\times10^{-5}$ (cite: Savage+1996). This gives $M_{\rm min}({\rm H^+})= (4.1\pm1.6)\times10^8\,M_{\astrosun}$, and $(1.8\pm1.2)\times10^8\,M_{\astrosun}$ for PJ231-20 QSO host and companion galaxy, respectively.

Starting from the dust mass budgets derived in Sect. [5](#ssect:dust), we can also obtain independent measurements of the gas masses adopting the local gas-to-dust ratio of $\delta_{\rm gdr}\sim70-100$ (cite: Draine+2007; Sandstrom+2013; Genzel+2015). Indeed, similar gas-to-dust ratio of $\sim70$ have also been found in high-$z$ starburst galaxies (cite: Riechers+2013; Wang+2016). Adopting the local value we obtain (atomic and molecular) gas masses of $M_{\rm gas} = (3.6 - 5.1)\times 10^{10}\,M_{\astrosun}$ and $(1.6 - 3.4)\times 10^{10}\,M_{\astrosun}$ for the PJ231-20 QSO host and companion galaxy respectively, and $M_{\rm gas} = (3.8 - 5.4)\times 10^{9}\,M_{\astrosun}$ and $(0.7 - 2.0)\times 10^{9}\,M_{\astrosun}$ for the PJ308-20 QSO host and companion galaxy, respectively. If we further assume that $\sim 75\%$ of the dust-derived gas mass is in molecular form (cite: Riechers+2013; Wang+2016), these values are consistent with those derived above from $M_{\rm CI}$ applying the CI-to-H$_2$ abundance ratio.

Finally, from the gas mass values derived above, we obtain a lower limit on the gas ionization percentage of $M_{\rm min}(\rm{H^+})/M_{\rm H_2} > 1-3\%$. For comparison, (cite: Ferkinhoff+2011) found values $<1\%$ for nearby galaxies (in the sample of (cite: Brauher+2008)), while high ionization percentages suggest high SFR density ($>10^2-10^3\,M_{\astrosun}\,{\rm\,yr^{-1}\,kpc^{-2}}$, see (cite: Ferkinhoff+2011)).

# Summary and conclusions

In this work, we presented ALMA observations of two quasar host–companion galaxy pairs PJ231-20 and PJ308-21 at $z>6$, captured when the Universe is $<900\,{\rm Myr}$ old. The companion galaxies were serendipitously discovered with previous ALMA observations in the field of known quasars, but they show no evidence of AGN activity. This multi-line study aimed to investigate the effect of the star formation and AGN activity on the ISM in massive galaxies at cosmic dawn.

The covered lines in the ALMA observations include tracers of the atomic ionized/neutral and molecular medium, such as \[NII\]$_{\rm 205\mu m}$, \[CI\]$_{\rm 369\mu m}$, CO(7–6, 10–9, 15–14, 16–15), H$_2$O $3_{12}-2_{21}$, $3_{21}-3_{12}$, $3_{03}-2_{12}$, and the OH$_{\rm 163\mu m}$ doublet. However, for PJ308-21 system only half of the program was executed. This work was complemented with already collected ALMA \[CII\]$_{\rm 158 \mu m}$ observations (cite: Decarli+2018), that were analyzed in a consistent way. In order to interpret our results and put quantitative constraints on the physical properties of the ISM in galaxies, we ran a set of PDR/XDR models by employing the CLOUDY radiative transfer code, with varying volume hydrogen density, radiation field strength and total hydrogen column density. The main results obtained in this work are summarized as follows:

- We modeled the FIR dust continuum on all the four targeted galaxies. We modeled this emission as a modified black body and inferred dust masses, spectral indexes, total infrared luminosities and SFRs (see Sect. [5](#ssect:dust) and Table [2](#tbl:dust_data)).

- From the analysis of the \[CII\]$_{\rm 158\mu m}$ and \[NII\]$_{\rm 205\mu m}$ lines, we found that $\apprge 80\%$ of \[CII\]$_{\rm 158\mu m}$ emission in both the quasar and companion galaxies of PJ231-20 system arises from neutral gas in the photo-dissociation regions rather from the fully (diffuse) ionized medium. Furthermore, the observed line deficits are comparable with local LIRGs.

- The \[CI\]$_{\rm 369\mu m}$/TIR luminosity ratios in the targeted systems are similar to those measured in $z\sim 2-4$ SMGs and quasars, revealing high star-formation efficiency in our galaxies.

- CLOUDY models suggest that \[CII\]$_{\rm 158\mu m}$ and \[CI\]$_{\rm 369\mu m}$ emission predominantly arise in PDRs illuminated by the FUV radiation field. In particular, constraints obtained from the \[CII\]$_{\rm 158\mu m}$/TIR and \[CI\]$_{\rm 369\mu m}$/TIR luminosity ratios for PJ231-20 QSO, point to a high FUV field intensity of $G_0\sim 10^5$ ($\sim 1.6\times 10^2\,{\rm erg\,s^{-1}\,cm^{-2}}$) and density of $n_{\rm H}>10^3$. We found similar constraints for the other sources.

- From the atomic fine-structure lines we retrieved constraints on atomic carbon, ionized hydrogen and molecular gas masses. The latter are consistent with the dust-derived gas masses assuming the local gas-to-dust ratio and that $\sim75\%$ of the gas mass is in molecular form. For both quasar and companion in PJ231-20 system, we also inferred gas ionization percentages of $>1-3\%$, greater than the typical values observed in nearby galaxies, suggesting high SFR density $> 10^{2}-10^{3}\,M_{\astrosun}{\rm \,yr^{-1}\,kpc^{-2}}$.

- The multiple mid-/high-$J$ CO line detections, allowed us to study the CO SLEDs (see Sect [8.2](#ssect:co_sleds)). Despite large uncertainties, the PJ231-20 QSO SLED resembles those of local AGNs. Similar result is obtained for the companion galaxy. On the other hand, by assuming a low dust temperature $35\,{\rm K}$, the CO SLED of the companion appears similar to the average SLED of local starburst galaxies. However, the mere detections of high-$J$ ($J_{\rm up} = 16, 15$) CO lines in the PJ231-20 and PJ308-21 quasars suggest the presence of additional heating source than PDRs. Indeed, CO SLED of the PJ231-20 QSO is well reproduced by a CLOUDY PDR+XDR composite model. The result indicates that PDRs dominate the low-/mid-$J$ CO line luminosities and account for $\sim90\%$ of the CO mass, while XDRs, that possibly represent the main drivers of high-$J$ CO emission lines, contribute to $\sim10\%$ of the mass. The latter likely resides in the central regions of the PJ231-20 QSO host galaxy, exposed to strong X-ray radiation due to the BH accretion. The best-fit PDR component indicates $n_{\rm H}^{\rm PDR}\sim4\times10^{2}\,{\rm cm^{-3}}$ and $G_0\sim1\times10^5$, while the XDR component is determined by $n_{\rm H}^{\rm XDR}\sim5\times10^5\,{\rm cm^{-3}}$ and $F_{\rm X}\sim 10\, {\rm erg\,s^{-1}\,cm^{-2}}$. However, due to the low number of data points, these results are affected by degeneracies.

- We detected three H$_2$O lines ($3_{12}-2_{21}$, $3_{21}-3_{12}$, $3_{03}-2_{12}$) in the PJ231-20 QSO, and H$_2$O $3_{03}-2_{12}$ in the PJ308-21 QSO. The PJ231-20 QSO, lies on the $L_{\rm H_2O}\propto L_{\rm TIR}^{1.1-1.2}$ trend found for low-$z$ sources, suggesting that the H$_2$O $3_{21}-3_{12}$ line is predominantly excited by pumping of IR photons of the dust UV-reprocessed radiation field. The $L_{\rm H_2O}/L_{\rm TIR}$ ratios in the PJ231-20 and PJ308-21 systems are of order of $\sim10^{-5}$, within the range observed in starburst galaxies at low $z$. The observed H$_2$O SLED in PJ231-20 QSO indicates that collisional excitation of the upper energy levels of the observed water vapor transitions, is likely minor. Furthermore, the SLED is similar to that of other high-$z$ sources. CLOUDY best-fit models are obtained using a single PDR component with $n_{\rm H}\sim 0.8\times10^5\,{\rm cm^{-3}}$, $G_0\sim 5\times10^5$ and high hydrogen column density of $N_{\rm H}=10^{24}\,{\rm cm^{-2}}$, indicating that H$_2$O emission arises deeply in the molecular clouds with high density, exposed to a strong radiation field.

- The H$_2$O/OH$_{\rm 163\mu m}$ ratios in the PJ231-20 QSO predicted by CLOUDY, are fully consistent with the results obtained from the H$_2$O SLED modeling, indicating that OH$_{\rm 163\mu m}$ doublet emission likely arises from similar regions traced by water vapor. We found similar constraints, but with large uncertainties, for the PJ231-20 companion galaxy and the PJ308-21 QSO, indicating that the ISM is exposed to strong FUV radiation field with $G_0>10^4$. These results are also in broad agreement with the analysis of CO and atomic fine-structure lines.

In conclusion, in both the PJ231-20 and PJ308-21 quasars the AGN activity is mainly revealed through high-$J$ CO line emission, requiring an additional source of heating than PDRs, possibly provided by a strong X-ray radiation field, while the CO SLEDs in conjunction with the non-detections of high-$J$ CO lines in companions, at least for PJ231-20, suggest a less excited medium, possibly as a consequence of the lack of a strong AGN as suggested by previous optical/UV and X-rays observations. Then, the analysis of the atomic fine-structure and molecular lines, in conjunction with the analysis of H$_2$O and OH$_{\rm 163\mu m}$ transitions, points to a strong radiation field in the quasar host and companion galaxies associated with massive episodes of star formation, as reflected by the enormous amount of dust ($M_{\rm dust}\approx0.5\times10^8-0.5\times10^9\,M_{\astrosun}$) heated at relatively high temperature and huge gas reservoir ($M_{\rm gas}\apprge 10^{10}\,M_{\astrosun}$) and high star-formation efficiencies. However, although the presented analysis of the ISM properties highlight differences in the quasars their companion galaxies, the current data do not allow us to definitively rule out the presence of an AGN in the companions, especially for the PJ308-21 companion galaxy for which there is little information due to the lack of line detections.

This work demonstrates that a large variety of investigations can be carried out on the ISM of quasar hosts and SMGs at such high redshift by targeting emission lines arising from different gas phases and environments. Future deeper follow-up observations have to be conducted, in order to get higher S/N and sample additional FIR emission lines to provide a better understanding of the ISM in these systems. Also, more comparisons between AGN and non-AGN environments have to be done by observing more object in this rich set of lines in the same redshift, thus providing us with a better statistics and in-depth exploration of the interplay between AGN and star formation in extreme conditions at early epochs.

# Acknowledgements

We thanks the anonymous referee for the useful comments that significantly improve the paper. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01115.S, ADS/JAO.ALMA#2017.1.00139.S, ADS/JAO.ALMA#2019.1.00147.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. MN and BV acknowledge support from the ERC Advanced Grant 740246 (Cosmic Gas). XF and JY acknowledge the supports from the US NSF grant AST 15-15115 and AST 19-08284. DR acknowledges support from the National Science Foundation under grant numbers AST-1614213 and AST-1910107. DR also acknowledges support from the Alexander von Humboldt Foundation through a Humboldt Research Fellowship for Experienced Researchers. RW acknowledges supports from the National Science Foundation of China (11721303, 11991052) and the National Key R&D Program of China (2016YFA0400703). This research made use of Astropy[^5], a community-developed core Python package for Astronomy (cite: AstropyI; AstropyII), and Matplotlib (cite: Matplotlib).

268 natexlab

(ref: Abel+2009) Abel, N. P., Dudley, C., Fischer, J., Satyapal, S., & van Hoof, P. A. M. 2009, ApJ, 701, 1147

(ref: Abel+2008) Abel, N. P., van Hoof, P. A. M., Shaw, G., Ferland , G. J., & Elwert, T. 2008, ApJ, 686, 1125

(ref: Agundez+2010) Agúndez, M., Goicoechea, J. R., Cernicharo, J., Faure, A., & Roueff, E. 2010, ApJ, 713, 662

(ref: Alaghband-Zadeh+2013) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, MNRAS, 435, 1493

(ref: Angulo+2012) Angulo, R. E., Springel, V., White, S. D. M., et al. 2012, MNRAS, 426, 2046

(ref: AstropyII) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: AstropyI) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Banados+2015) Bañados, E., Decarli, R., Walter, F., et al. 2015, ApJ, 805, L8

(ref: Banados+2016) Bañados, E., Venemans, B. P., Decarli, R., et al. 2016, ApJS, 227, 11

(ref: Banados+2018) Bañados, E., Venemans, B. P., Mazzucchelli, C., et al. 2018, Nature, 553, 473

(ref: Balmaverde+2017) Balmaverde, B., Gilli, R., Mignoli, M., et al. 2017, A&A, 606, A23

(ref: Becker+2015) Becker, G. D., Bolton, J. S., & Lidz, A. 2015, PASA, 32, e045

(ref: Beelen+2006) Beelen, A., Cox, P., Benford, D. J., et al. 2006, ApJ, 642, 694

(ref: Begelman+2006) Begelman, M. C., Volonteri, M., & Rees, M. J. 2006, MNRAS, 370, 289

(ref: Bergin+2003) Bergin, E. A., Kaufman, M. J., Melnick, G. J., Snell, R. L., & Howe, J. E. 2003, ApJ, 582, 830

(ref: Bertoldi+2003b) Bertoldi, F., Carilli, C. L., Cox, P., et al. 2003a, A&A, 406, L55

(ref: Bertoldi+2003a) Bertoldi, F., Cox, P., Neri, R., et al. 2003b, A&A, 409, L47

(ref: Birkin+2020) Birkin, J. E., Weiss, A., Wardlow, J. L., et al. 2020, arXiv e-prints, arXiv:2009.03341

(ref: Bisbas+2012) Bisbas, T. G., Bell, T. A., Viti, S., Yates, J., & Barlow, M. J. 2012, MNRAS, 427, 2100

(ref: Blain+2003) Blain, A. W., Barnard, V. E., & Chapman, S. C. 2003, MNRAS, 338, 733

(ref: Bolatto+2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Bonoli+2009) Bonoli, S., Marulli, F., Springel, V., et al. 2009, MNRAS, 396, 423

(ref: Bonoli+2014) Bonoli, S., Mayer, L., & Callegari, S. 2014, MNRAS, 437, 1576

(ref: Boogaard+2020) Boogaard, L. A., van der Werf, P., Weiß, A., et al. 2020, arXiv e-prints, arXiv:2009.04348

(ref: Bothwell+2017) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825

(ref: Bothwell+2013) Bothwell, M. S., Aguirre, J. E., Chapman, S. C., et al. 2013, ApJ, 779, 67

(ref: Bothwell+2010) Bothwell, M. S., Chapman, S. C., Tacconi, L., et al. 2010, MNRAS, 405, 219

(ref: Bradford+2011) Bradford, C. M., Bolatto, A. D., Maloney, P. R., et al. 2011, ApJL, 741, L37

(ref: Bradford+1999) Bradford, C. M., Stacey, G. J., Fischer, J., et al. 1999, in ESA Special Publication, Vol. 427, The Universe as Seen by ISO, ed. P. Cox & M. Kessler, 861

(ref: Brauher+2008) Brauher, J. R., Dale, D. A., & Helou, G. 2008, ApJS, 178, 280

(ref: Canameras+2018) Cañameras, R., Yang, C., Nesvadba, N. P. H., et al. 2018, A&A, 620, A61

(ref: CarilliWalter2013) Carilli, C. L. & Walter, F. 2013, Annual Review of Astronomy and Astrophysics, 51, 105

(ref: Carniani+2019) Carniani, S., Gallerani, S., Vallini, L., et al. 2019, MNRAS, 489, 3939

(ref: Carniani+2017) Carniani, S., Marconi, A., Maiolino, R., et al. 2017, A&A, 605, A105

(ref: Carral+1994) Carral, P., Hollenbach, D. J., Lord, S. D., et al. 1994, ApJ, 423, 223

(ref: Casey+2012) Casey, C. M. 2012, MNRAS, 425, 3094

(ref: Cernicharo+2006) Cernicharo, J., Goicoechea, J. R., Pardo, J. R., & Asensio-Ramos, A. 2006, ApJ, 642, 940

(ref: Chapman+2005) Chapman, S. C., Blain, A. W., Smail, I., & Ivison, R. J. 2005, ApJ, 622, 772

(ref: Charmandaris+2004) Charmandaris, V., Uchida, K. I., Weedman, D., et al. 2004, ApJS, 154, 142

(ref: Colbert+1999) Colbert, J. W., Malkan, M. A., Clegg, P. E., et al. 1999, ApJ, 511, 721

(ref: Combes+2012) Combes, F., Rex, M., Rawle, T. D., et al. 2012, A&A, 538, L4

(ref: Combes+1997) Combes, F. & Wiklind, T. 1997, ApJL, 486, L79

(ref: Conley+2011) Conley, A., Cooray, A., Vieira, J. D., et al. 2011, ApJL, 732, L35

(ref: Connor+2020) Connor, T., Bañados, E., Mazzucchelli, C., et al. 2020, arXiv e-prints, arXiv:2007.14571

(ref: Connor+2019) Connor, T., Bañados, E., Stern, D., et al. 2019, ApJ, 887, 171

(ref: Costa+2014) Costa, T., Sijacki, D., Trenti, M., & Haehnelt, M. G. 2014, MNRAS, 439, 2146

(ref: Cruddace+1974) Cruddace, R., Paresce, F., Bowyer, S., & Lampton, M. 1974, ApJ, 187, 497

(ref: daCunha+2013) da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13

(ref: Daddi+2010) Daddi, E., Bournaud, F., Walter, F., et al. 2010, ApJ, 713, 686

(ref: Daniel+2012) Daniel, F., Goicoechea, J. R., Cernicharo, J., Dubernet, M. L., & Faure, A. 2012, A&A, 547, A81

(ref: DeRosa+2011) De Rosa, G., Decarli, R., Walter, F., et al. 2011, ApJ, 739, 56

(ref: Decarli+2019) Decarli, R., Dotti, M., Bañados, E., et al. 2019a, ApJ, 880, 157

(ref: Decarli+2019b) Decarli, R., Mignoli, M., Gilli, R., et al. 2019b, A&A, 631, L10

(ref: Decarli+2014) Decarli, R., Walter, F., Carilli, C., et al. 2014, ApJL, 782, L17

(ref: Decarli+2012) Decarli, R., Walter, F., Neri, R., et al. 2012, ApJ, 752, 2

(ref: Decarli+2017) Decarli, R., Walter, F., Venemans, B. P., et al. 2017, Nature, 545, 457

(ref: Decarli+2018) Decarli, R., Walter, F., Venemans, B. P., et al. 2018, ApJ, 854, 97

(ref: Destombes+1977) Destombes, J. L., Marliere, C., Baudry, A., & Brillet, J. 1977, A&A, 61, 769

(ref: Dewangan+1987) Dewangan, D. P., Flower, D. R., & Alexander, M. H. 1987, MNRAS, 226, 505

(ref: Diaz-Santos+2017) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, ApJ, 846, 32

(ref: Diaz-Santos+2013) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2013, ApJ, 774, 68

(ref: Downes+1992) Downes, D., Radford, J. E., Greve, A., et al. 1992, ApJL, 398, L25

(ref: Downes+1998) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: Draine+2007) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: Dunne+2000) Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115

(ref: Elbaz+2011) Elbaz, D., Dickinson, M., Hwang, H. S., et al. 2011, A&A, 533, A119

(ref: Elitzur+2006) Elitzur, M. & Asensio Ramos, A. 2006, MNRAS, 365, 779

(ref: Elitzur+1978) Elitzur, M. & de Jong, T. 1978, A&A, 67, 323

(ref: Engel+2010) Engel, H., Tacconi, L. J., Davies, R. I., et al. 2010, ApJ, 724, 233

(ref: Faisst+2020) Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020, MNRAS, 498, 4192

(ref: Fan+2006) Fan, X., Carilli, C. L., & Keating, B. 2006a, ARA&A, 44, 415

(ref: Fan+2006b) Fan, X., Strauss, M. A., Becker, R. H., et al. 2006b, AJ, 132, 117

(ref: Farina+2019) Farina, E. P., Arrigoni-Battaia, F., Costa, T., et al. 2019, ApJ, 887, 196

(ref: Farina+2017) Farina, E. P., Venemans, B. P., Decarli, R., et al. 2017, ApJ, 848, 78

(ref: Farrah+2013) Farrah, D., Lebouteiller, V., Spoon, H. W. W., et al. 2013, ApJ, 776, 38

(ref: Faure+2007) Faure, A., Crimier, N., Ceccarelli, C., et al. 2007, A&A, 472, 1029

(ref: Faure+2008) Faure, A. & Josselin, E. 2008, A&A, 492, 257

(ref: Ferkinhoff+2011) Ferkinhoff, C., Brisbin, D., Nikola, T., et al. 2011, ApJL, 740, L29

(ref: Ferland+2017) Ferland, G. J., Chatzikos, M., Guzmán, F., et al. 2017, , 53, 385

(ref: Feruglio+2018) Feruglio, C., Fiore, F., Carniani, S., et al. 2018, A&A, 619, A39

(ref: Fischer+1999) Fischer, J., Luhman, M. L., Satyapal, S., et al. 1999, Ap&SS, 266, 91

(ref: Fischer+2010) Fischer, J., Sturm, E., González-Alfonso, E., et al. 2010, A&A, 518, L41

(ref: Fixsen+1999) Fixsen, D. J., Bennett, C. L., & Mather, J. C. 1999, ApJ, 526, 207

(ref: Flower+2010) Flower, D. R. & Pineau Des Forêts, G. 2010, MNRAS, 406, 1745

(ref: Foreman+2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, Publications of the Astronomical Society of the Pacific, 125, 306

(ref: Gallerani+2014) Gallerani, S., Ferrara, A., Neri, R., & Maiolino, R. 2014, MNRAS, 445, 2848

(ref: Genzel+2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: Gerin+2000) Gerin, M. & Phillips, T. G. 2000, ApJ, 537, 644

(ref: Glassgold+1974) Glassgold, A. E. & Langer, W. D. 1974, ApJ, 193, 73

(ref: Godard+2019) Godard, B., Pineau des Forêts, G., Lesaffre, P., et al. 2019, A&A, 622, A100

(ref: Goicoechea+2002) Goicoechea, J. R. & Cernicharo, J. 2002, ApJL, 576, L77

(ref: Goicoechea+2005) Goicoechea, J. R., Martı́n-Pintado, J., & Cernicharo, J. 2005, ApJ, 619, 291

(ref: Goldsmith+1999) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: Goldsmith+2012) Goldsmith, P. F., Langer, W. D., Pineda, J. L., & Velusamy, T. 2012, ApJS, 203, 13

(ref: Gonzalez-Alfonso+2014) González-Alfonso, E., Fischer, J., Aalto, S., & Falstad, N. 2014, A&A, 567, A91

(ref: Gonzalez-Alfonso+2013) González-Alfonso, E., Fischer, J., Bruderer, S., et al. 2013, A&A, 550, A25

(ref: Gonzalez-Alfonso+2012) González-Alfonso, E., Fischer, J., Graciá-Carpio, J., et al. 2012, A&A, 541, A4

(ref: Gonzalez-Alfonso+2010) González-Alfonso, E., Fischer, J., Isaak, K., et al. 2010, A&A, 518, L43

(ref: Gonzalez-Alfonso+2017) González-Alfonso, E., Fischer, J., Spoon, H. W. W., et al. 2017, ApJ, 836, 11

(ref: Gonzalez-Alfonso+2008) González-Alfonso, E., Smith, H. A., Ashby, M. L. N., et al. 2008, ApJ, 675, 303

(ref: Gonzalez-Alfonso+2004) González-Alfonso, E., Smith, H. A., Fischer, J., & Cernicharo, J. 2004, ApJ, 613, 247

(ref: Gracia-Carpio+2011) Graciá-Carpio, J., Sturm, E., Hailey-Dunsheath, S., et al. 2011, ApJL, 728, L7

(ref: Graff+1987) Graff, M. M. & Dalgarno, A. 1987, ApJ, 317, 432

(ref: Habing+1968) Habing, H. J. 1968, , 19, 421

(ref: Habouzit+2019) Habouzit, M., Volonteri, M., Somerville, R. S., et al. 2019, MNRAS, 489, 1206

(ref: Hartquist+1998) Hartquist, T. W. & Williams, D. A. 1998, The molecular astrophysics of stars and galaxies, 4

(ref: Hashimoto+2019a) Hashimoto, T., Inoue, A. K., Mawatari, K., et al. 2019a, PASJ, 71, 71

(ref: Hashimoto+2019b) Hashimoto, T., Inoue, A. K., Tamura, Y., et al. 2019b, PASJ, 71, 109

(ref: Helou+1988) Helou, G., Khan, I. R., Malek, L., & Boehmer, L. 1988, ApJS, 68, 151

(ref: Herrera-Camus+2016) Herrera-Camus, R., Bolatto, A., Smith, J. D., et al. 2016, ApJ, 826, 175

(ref: Herrera-Camus+2018) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018a, ApJ, 861, 94

(ref: Herrera-Camus+2018b) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018b, ApJ, 861, 95

(ref: Herrera-Camus+2020) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2020, A&A, 633, L4

(ref: Hinshaw+2013) Hinshaw, G., Larson, D., Komatsu, E., et al. 2013, The Astrophysical Journal Supplement Series, 208, 19

(ref: Hollenbach+2009) Hollenbach, D., Kaufman, M. J., Bergin, E. A., & Melnick, G. J. 2009, ApJ, 690, 1497

(ref: Hollenbach+1989) Hollenbach, D. & McKee, C. F. 1989, ApJ, 342, 306

(ref: Hollenbach+1997) Hollenbach, D. J. & Tielens, A. G. G. M. 1997, ARA&A, 35, 179

(ref: Hollenbach+1999) Hollenbach, D. J. & Tielens, A. G. G. M. 1999, Reviews of Modern Physics, 71, 173

(ref: Matplotlib) Hunter, J. D. 2007, Computing in Science Engineering, 9, 90

(ref: Ikeda+2002) Ikeda, M., Oka, T., Tatematsu, K., Sekimoto, Y., & Yamamoto, S. 2002, ApJS, 139, 467

(ref: Indriolo+2007) Indriolo, N., Geballe, T. R., Oka, T., & McCall, B. J. 2007, ApJ, 671, 1736

(ref: Israel+2015) Israel, F. P., Rosenberg, M. J. F., & van der Werf, P. 2015, A&A, 578, A95

(ref: Ivison+2011) Ivison, R. J., Papadopoulos, P. P., Smail, I., et al. 2011, MNRAS, 412, 1913

(ref: Jiang+2007) Jiang, L., Fan, X., Vestergaard, M., et al. 2007, AJ, 134, 1150

(ref: Jiang+2016) Jiang, L., McGreer, I. D., Fan, X., et al. 2016, ApJ, 833, 222

(ref: Jiao+2017) Jiao, Q., Zhao, Y., Zhu, M., et al. 2017, ApJL, 840, L18

(ref: Kaufman+2006) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, ApJ, 644, 283

(ref: Kaufman+1999) Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman, M. L. 1999, ApJ, 527, 795

(ref: Kegel+1999) Kegel, W. H., Hertenstein, T., & Quirrenbach, A. 1999, A&A, 351, 472

(ref: Kirkpatrick+2015) Kirkpatrick, A., Pope, A., Sajina, A., et al. 2015, ApJ, 814, 9

(ref: Korista+1997) Korista, K., Baldwin, J., Ferland, G., & Verner, D. 1997, ApJS, 108, 401

(ref: Kovacs+2006) Kovács, A., Chapman, S. C., Dowell, C. D., et al. 2006, ApJ, 650, 592

(ref: Krolik+1988) Krolik, J. H. & Begelman, M. C. 1988, ApJ, 329, 702

(ref: Krolik+1983) Krolik, J. H. & Kallman, T. R. 1983, ApJ, 267, 610

(ref: Kroupa2001) Kroupa, P. 2001, MNRAS, 322, 231

(ref: Langer+1978) Langer, W. D. 1978, ApJ, 225, 860

(ref: Leipski+2013) Leipski, C., Meisenheimer, K., Walter, F., et al. 2013, ApJ, 772, 103

(ref: Leipski+2014) Leipski, C., Meisenheimer, K., Walter, F., et al. 2014, ApJ, 785, 154

(ref: Lepp+1996) Lepp, S. & Dalgarno, A. 1996, A&A, 306, L21

(ref: Lepp+1983) Lepp, S. & McCray, R. 1983, ApJ, 269, 560

(ref: Li+2020b) Li, J., Wang, R., Cox, P., et al. 2020a, ApJ, 900, 131

(ref: Li+2020) Li, J., Wang, R., Riechers, D., et al. 2020b, ApJ, 889, 162

(ref: Liang+2019) Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397

(ref: Lis+2011) Lis, D. C., Neufeld, D. A., Phillips, T. G., Gerin, M., & Neri, R. 2011, ApJL, 738, L6

(ref: Liu+2017) Liu, L., Weiß, A., Perez-Beaupuits, J. P., et al. 2017, ApJ, 846, 5

(ref: Lord+1996) Lord, S. D., Hollenbach, D. J., Haas, M. R., et al. 1996, ApJ, 465, 703

(ref: Luhman+2003) Luhman, M. L., Satyapal, S., Fischer, J., et al. 2003, ApJ, 594, 758

(ref: Lupu+2012) Lupu, R. E., Scott, K. S., Aguirre, J. E., et al. 2012, ApJ, 757, 135

(ref: Ma+2019) Ma, X., Hayward, C. C., Casey, C. M., et al. 2019, MNRAS, 487, 1844

(ref: Maiolino+2015) Maiolino, R., Carniani, S., Fontana, A., et al. 2015, MNRAS, 452, 54

(ref: Maiolino+2009) Maiolino, R., Caselli, P., Nagao, T., et al. 2009, A&A, 500, L1

(ref: Maiolino+2005) Maiolino, R., Cox, P., Caselli, P., et al. 2005, A&A, 440, L51

(ref: Malhotra+1997) Malhotra, S., Helou, G., Stacey, G., et al. 1997, ApJL, 491, L27

(ref: Maloney+1996) Maloney, P. R., Hollenbach, D. J., & Tielens, A. G. G. M. 1996, ApJ, 466, 561

(ref: Mashian+2015) Mashian, N., Sturm, E., Sternberg, A., et al. 2015, ApJ, 802, 81

(ref: Mathis+1997) Mathis, J. S. 1997, Astronomical Society of the Pacific Conference Series, Vol. 122, Composition and Size of Interstellar Dust, ed. Y. J. Pendleton, 87

(ref: Matsuoka+2018) Matsuoka, Y., Strauss, M. A., Kashikawa, N., et al. 2018, ApJ, 869, 150

(ref: Mazzucchelli+2017b) Mazzucchelli, C., Bañados, E., Decarli, R., et al. 2017a, ApJ, 834, 83

(ref: Mazzucchelli+2017) Mazzucchelli, C., Bañados, E., Venemans, B. P., et al. 2017b, ApJ, 849, 91

(ref: Mazzucchelli+2019) Mazzucchelli, C., Decarli, R., Farina, E. P., et al. 2019, ApJ, 881, 163

(ref: McKee+1977) McKee, C. F. & Ostriker, J. P. 1977, ApJ, 218, 148

(ref: McMullin+2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Data Analysis Software and Systems XVI, Vol. 376, 127

(ref: Meijerink+2013) Meijerink, R., Kristensen, L. E., Weiß, A., et al. 2013, ApJL, 762, L16

(ref: Meijerink+2005) Meijerink, R. & Spaans, M. 2005, A&A, 436, 397

(ref: Meijerink+2007) Meijerink, R., Spaans, M., & Israel, F. P. 2007, A&A, 461, 793

(ref: Meijerink+2011) Meijerink, R., Spaans, M., Loenen, A. F., & van der Werf, P. P. 2011, A&A, 525, A119

(ref: Meixner+1993) Meixner, M. & Tielens, A. G. G. M. 1993, ApJ, 405, 216

(ref: Menten+2008) Menten, K. M., Lundgren, A., Belloche, A., Thorwirth, S., & Reid, M. J. 2008, A&A, 477, 185

(ref: Mingozzi+2018) Mingozzi, M., Vallini, L., Pozzi, F., et al. 2018, MNRAS, 474, 3640

(ref: Morselli+2014) Morselli, L., Mignoli, M., Gilli, R., et al. 2014, A&A, 568, A1

(ref: Murphy+2011) Murphy, E. J., Condon, J. J., Schinnerer, E., et al. 2011, ApJ, 737, 67

(ref: Narayanan+2014) Narayanan, D. & Krumholz, M. R. 2014, MNRAS, 442, 1411

(ref: Neeleman+2019) Neeleman, M., Bañados, E., Walter, F., et al. 2019, ApJ, 882, 10

(ref: Neufeld+1993) Neufeld, D. A. & Kaufman, M. J. 1993, ApJ, 418, 263

(ref: Neufeld+2002) Neufeld, D. A., Kaufman, M. J., Goldsmith, P. F., Hollenbach, D. J., & Plume, R. 2002, ApJ, 580, 278

(ref: Neufeld+1995) Neufeld, D. A., Lepp, S., & Melnick, G. J. 1995, ApJS, 100, 132

(ref: Noeske+2007) Noeske, K. G., Weiner, B. J., Faber, S. M., et al. 2007, ApJL, 660, L43

(ref: Novak+2019) Novak, M., Bañados, E., Decarli, R., et al. 2019, ApJ, 881, 63

(ref: Oberst+2006) Oberst, T. E., Parshley, S. C., Stacey, G. J., et al. 2006, ApJL, 652, L125

(ref: Obreschkow+2009) Obreschkow, D., Heywood, I., Klöckner, H. R., & Rawlings, S. 2009, ApJ, 702, 1321

(ref: Omont+2011) Omont, A., Neri, R., Cox, P., et al. 2011, A&A, 530, L3

(ref: Omont+2013) Omont, A., Yang, C., Cox, P., et al. 2013, A&A, 551, A115

(ref: Onoue+2020) Onoue, M., Bañados, E., Mazzucchelli, C., et al. 2020, ApJ, 898, 105

(ref: Overzier+2009) Overzier, R. A., Guo, Q., Kauffmann, G., et al. 2009, MNRAS, 394, 577

(ref: Papadopoulos+2004) Papadopoulos, P. P., Thi, W. F., & Viti, S. 2004, MNRAS, 351, 147

(ref: Pavesi+2016) Pavesi, R., Riechers, D. A., Capak, P. L., et al. 2016, ApJ, 832, 151

(ref: Pentericci+2002) Pentericci, L., Fan, X., Rix, H.-W., et al. 2002, AJ, 123, 2151

(ref: Pereira-Santaella+2013) Pereira-Santaella, M., Spinoglio, L., Busquet, G., et al. 2013, ApJ, 768, 55

(ref: Poelman+2005) Poelman, D. R. & Spaans, M. 2005, A&A, 440, 559

(ref: Pound+2008) Pound, M. W. & Wolfire, M. G. 2008, Astronomical Society of the Pacific Conference Series, Vol. 394, The Photo Dissociation Region Toolbox, ed. R. W. Argyle, P. S. Bunclark, & J. R. Lewis, 654

(ref: Priddey+2001) Priddey, R. S. & McMahon, R. G. 2001, MNRAS, 324, L17

(ref: Rangwala+2011) Rangwala, N., Maloney, P. R., Glenn, J., et al. 2011, ApJ, 743, 94

(ref: Riechers+2013) Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329

(ref: Riechers+2014) Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84

(ref: Riechers+2011) Riechers, D. A., Carilli, L. C., Walter, F., et al. 2011, ApJL, 733, L11

(ref: Riechers+2020) Riechers, D. A., Hodge, J. A., Pavesi, R., et al. 2020, ApJ, 895, 81

(ref: Riechers+2009) Riechers, D. A., Walter, F., Bertoldi, F., et al. 2009, ApJ, 703, 1338

(ref: Rosenberg+2015) Rosenberg, M. J. F., van der Werf, P. P., Aalto, S., et al. 2015, ApJ, 801, 72

(ref: Rowan-Robinson+1995) Rowan-Robinson, M. 1995, MNRAS, 272, 737

(ref: Rybak+2019) Rybak, M., Calistro Rivera, G., Hodge, J. A., et al. 2019, ApJ, 876, 112

(ref: Saintonge+2017) Saintonge, A., Catinella, B., Tacconi, L. J., et al. 2017, ApJS, 233, 22

(ref: Saintonge+2018) Saintonge, A., Wilson, C. D., Xiao, T., et al. 2018, MNRAS, 481, 3497

(ref: Sanders+2003) Sanders, D. B., Mazzarella, J. M., Kim, D. C., Surace, J. A., & Soifer, B. T. 2003, AJ, 126, 1607

(ref: Sandstrom+2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Savage+1996) Savage, B. D. & Sembach, K. R. 1996, ARA&A, 34, 279

(ref: Schleicher+2010) Schleicher, D. R. G., Spaans, M., & Klessen, R. S. 2010, A&A, 513, A7

(ref: Schreiber+2018) Schreiber, C., Elbaz, D., Pannella, M., et al. 2018, A&A, 609, A30

(ref: Shao+2019) Shao, Y., Wang, R., Carilli, C. L., et al. 2019, ApJ, 876, 99

(ref: Sijacki+2015) Sijacki, D., Vogelsberger, M., Genel, S., et al. 2015, MNRAS, 452, 575

(ref: Smith+2004) Smith, H., Gonzalez-Alfonso, E., Fischer, J., et al. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 320, The Neutral ISM in Starburst Galaxies, ed. S. Aalto, S. Huttemeister, & A. Pedlar, 49

(ref: Solomon+1992) Solomon, P. M., Radford, S. J. E., & Downes, D. 1992, Nature, 356, 318

(ref: Spaans+1996) Spaans, M. 1996, A&A, 307, 271

(ref: Spinoglio+2005) Spinoglio, L., Malkan, M. A., Smith, H. A., González-Alfonso, E., & Fischer, J. 2005, ApJ, 623, 123

(ref: Spinoglio+2012) Spinoglio, L., Pereira-Santaella, M., Busquet, G., et al. 2012, ApJ, 758, 108

(ref: Spoon+2013) Spoon, H. W. W., Farrah, D., Lebouteiller, V., et al. 2013, ApJ, 775, 127

(ref: Stefan+2015) Stefan, I. I., Carilli, C. L., Wagg, J., et al. 2015, MNRAS, 451, 1713

(ref: Strandet+2017) Strandet, M. L., Weiss, A., De Breuck, C., et al. 2017, ApJL, 842, L15

(ref: Sturm+2011) Sturm, E., González-Alfonso, E., Veilleux, S., et al. 2011, ApJL, 733, L16

(ref: Tacconi+2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tacconi+2008) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, ApJ, 680, 246

(ref: Tacconi+2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, arXiv e-prints, arXiv:2003.06245

(ref: Tielens+1985a) Tielens, A. G. G. M. & Hollenbach, D. 1985a, ApJ, 291, 722

(ref: Tielens+1985b) Tielens, A. G. G. M. & Hollenbach, D. 1985b, ApJ, 291, 747

(ref: Tomassetti+2014) Tomassetti, M., Porciani, C., Romano-Diaz, E., Ludlow, A. D., & Papadopoulos, P. P. 2014, MNRAS, 445, L124

(ref: Trakhtenbrot+2017) Trakhtenbrot, B., Lira, P., Netzer, H., et al. 2017, ApJ, 836, 8

(ref: Valentino+2018) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: Valentino+2020) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, ApJ, 890, 24

(ref: Vallini+2018) Vallini, L., Pallottini, A., Ferrara, A., et al. 2018, MNRAS, 473, 271

(ref: Vallini+2019) Vallini, L., Tielens, A. G. G. M., Pallottini, A., et al. 2019, MNRAS, 490, 4502

(ref: vanderTak+2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vanderVlugt+2019) van der Vlugt, D. & Costa, T. 2019, MNRAS, 490, 4918

(ref: vanderWerf+2011) van der Werf, P. P., Berciano Alba, A., Spaans, M., et al. 2011, ApJL, 741, L38

(ref: vanderWerf+2010) van der Werf, P. P., Isaak, K. G., Meijerink, R., et al. 2010, A&A, 518, L42

(ref: Veilleux+2013) Veilleux, S., Meléndez, M., Sturm, E., et al. 2013, ApJ, 776, 27

(ref: Venemans+2018) Venemans, B. P., Decarli, R., Walter, F., et al. 2018, ApJ, 866, 159

(ref: Venemans+2019) Venemans, B. P., Neeleman, M., Walter, F., et al. 2019, ApJ, 874, L30

(ref: Venemans+2017b) Venemans, B. P., Walter, F., Decarli, R., et al. 2017a, ApJL, 851, L8

(ref: Venemans+2017c) Venemans, B. P., Walter, F., Decarli, R., et al. 2017b, ApJ, 837, 146

(ref: Venemans+2017a) Venemans, B. P., Walter, F., Decarli, R., et al. 2017c, ApJ, 845, 154

(ref: Vito+2019) Vito, F., Brandt, W. N., Bauer, F. E., et al. 2019, A&A, 628, L6

(ref: Volonteri2012) Volonteri, M. 2012, Science, 337, 544

(ref: Wagner+1987) Wagner, A. F. & Graff, M. M. 1987, ApJ, 317, 423

(ref: Walter+2003) Walter, F., Bertoldi, F., Carilli, C., et al. 2003, Nature, 424, 406

(ref: Walter+2004) Walter, F., Carilli, C., Bertoldi, F., et al. 2004, ApJ, 615, L17

(ref: Walter+2009nat) Walter, F., Riechers, D., Cox, P., et al. 2009, Nature, 457, 699

(ref: Walter+2018) Walter, F., Riechers, D., Novak, M., et al. 2018, ApJL, 869, L22

(ref: Walter+2011) Walter, F., Weiß, A., Downes, D., Decarli, R., & Henkel, C. 2011, ApJ, 730, 18

(ref: WangF+2019) Wang, F., Wang, R., Fan, X., et al. 2019, ApJ, 880, 2

(ref: Wang+2021) Wang, F., Yang, J., Fan, X., et al. 2021, arXiv e-prints, arXiv:2101.03179

(ref: Wang+2010) Wang, R., Carilli, C. L., Neri, R., et al. 2010, ApJ, 714, 699

(ref: Wang+2008) Wang, R., Wagg, J., Carilli, C. L., et al. 2008, AJ, 135, 1201

(ref: Wang+2013) Wang, R., Wagg, J., Carilli, C. L., et al. 2013, ApJ, 773, 44

(ref: Wang+2016) Wang, R., Wu, X.-B., Neri, R., et al. 2016, ApJ, 830, 53

(ref: Weiss+2005) Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429, L25

(ref: Weiss+2003) Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A, 409, L41

(ref: Weiss+2010) Weiß, A., Requena-Torres, M. A., Güsten, R., et al. 2010, A&A, 521, L1

(ref: Willott+2015mbh) Willott, C. J., Bergeron, J., & Omont, A. 2015a, ApJ, 801, 123

(ref: Willott+2017) Willott, C. J., Bergeron, J., & Omont, A. 2017, ApJ, 850, 108

(ref: Willott+2015) Willott, C. J., Carilli, C. L., Wagg, J., & Wang, R. 2015b, ApJ, 807, 180

(ref: Yang+2013) Yang, C., Gao, Y., Omont, A., et al. 2013, ApJL, 771, L24

(ref: Yang+2019) Yang, C., Gavazzi, R., Beelen, A., et al. 2019a, A&A, 624, A138

(ref: Yang+2020) Yang, C., González-Alfonso, E., Omont, A., et al. 2020a, A&A, 634, L3

(ref: Yang+2017) Yang, C., Omont, A., Beelen, A., et al. 2017, A&A, 608, A144

(ref: Yang+2016) Yang, C., Omont, A., Beelen, A., et al. 2016, A&A, 595, A80

(ref: YangJ+2019) Yang, J., Venemans, B., Wang, F., et al. 2019b, ApJ, 880, 153

(ref: YangJ+2020) Yang, J., Wang, F., Fan, X., et al. 2020b, ApJL, 897, L14

(ref: Zhao+2013) Zhao, Y., Lu, N., Xu, C. K., et al. 2013, ApJL, 765, L13

(ref: Zhao+2016) Zhao, Y., Lu, N., Xu, C. K., et al. 2016, ApJ, 819, 69

[^1]: In particular, we obtained an additional data cube by imaging the calibrated visibilities of ALMA setup A of PJ231-20 system (which has the smallest restoring beam from the original data reduction) by using a "tapering" scheme resulting in a restoring beam of $1''.7\times1''.2$ (similar to that of the setup C, which has the lower angular resolution). Instead, in the case of PJ308-21 data, the beam sizes are comparable.

[^2]: For a typical ${\rm S/N}\sim60-100$ over a bandwidth of ${\sim4\,{\rm GHz}}$ in ALMA band 3-6, the continuum emission is well-described by a zeroth-order polynomial within the uncertainties.

[^3]: The density at which the rate of collisional depopulation of a quantum level equals the spontaneous radiative decay rate.

[^4]: See Table 2 in (cite: Carniani+2019) and Table 1 in (cite: Venemans+2017a) for the complete collection of measurements.

[^5]: http://www.astropy.org

</paper>

Write the methods card for this paper.