# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.347G\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.347G",
 "title": "Deciphering the imprint of active galactic nucleus feedback in Seyfert galaxies: Nuclear-scale molecular gas deficits",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "García-Burillo, S.",
 "n_authors": 29,
 "arxiv_id": "2406.11398",
 "doi": "10.1051/0004-6361/202450268",
 "alma_projects_linked_by_archive": [
  "2012.1.00650.S",
  "2013.1.01161.S",
  "2015.1.00121.S",
  "2015.1.00404.S",
  "2015.1.00925.S",
  "2015.1.00956.S",
  "2016.1.00232.S",
  "2016.1.00254.S",
  "2016.1.00296.S",
  "2016.1.00386.S",
  "2017.1.00082.S",
  "2017.1.00392.S",
  "2017.1.00766.S",
  "2017.1.00886.L",
  "2018.1.00113.S",
  "2019.1.00618.S",
  "2019.1.01230.S",
  "2019.1.01742.S",
  "2021.1.00812.S"
 ]
}
```

Paper text:
<paper>
# Deciphering the imprint of AGN feedback in Seyfert galaxies:

# Introduction

The optical spectral properties of active galactic nuclei (AGN) are used to classify them into two categories: type 1 AGN show both broad and narrow line regions (BLR and NLR), while type 2 AGN only show NLR. In the AGN unifying theories the central engines of type 2 objects are thought to be hidden behind large amounts of obscuring material located in a ’torus’ or disk of a few pc-size (cite: Ant85; Ant93; Kro88; Urr95). Being a key player in the last steps of the AGN fueling process, observations of tori and their surrounding regions can therefore shed light on our understanding of the feeding and feedback cycle of the gas in AGN (cite: Ram17; Sto19; Combes21; Har24).

Molecular tori are the expected launching sites of multi-scale and multi-phase outflows, a manifestation of the AGN feedback process. There is increasing multi-wavelength observational evidence for the existence of outflows that can extend from tens of parsecs to several kiloparsecs in different AGN samples (cite: Mor05; Mor15; Alat11; Aal12; Aal20; Com13; GB14; GB19; Que16b; Fio17; Alo18; Alo19; Alo23; Aud19; Flu19; Flu21; Min19; Lut20; Dom20; Vei20; Gar21; Ven21; Ram22; Uli24). Galaxy formation models and numerical simulations predict that AGN feedback is a necessary ingredient required to explain the observable properties of massive galaxies (cite: Schaye15; Ang17; Wei17; Pill18; Dav19). However, quantitatively establishing the potential impact of the feedback of nuclear activity in their host galaxies remains a matter of debate even in high luminosity AGN (cite: Har23; Har24). The impact predicted by numerical simulations is likely cumulative over the multiple short-lived episodes that are expected during the lifetime of the AGN (cite: Pio22). The recent study published by (cite: Eli21), based on kpc-scale observations of the Extragalactic Data base for Galaxy Evolution-Calar Alto Legacy Integral Field Area (EDGE-CALIFA) sample (cite: San12; Bol17), found that the molecular gas fractions ($\Sigma_{\rm gas}/\Sigma_{*}$) of central AGN regions are a factor of $\simeq$2 lower than those in non-AGN star-forming regions. However, AGN variability, linked to the chaotic nature of the black hole feeding process, tends naturally to eliminate any significant correlation between the global (kpc-scale) molecular gas content and the AGN luminosity (cite: Izu16b; Ros18; Ang21; GB21; Ram22). The search for a clear observational ‘smoking gun’ signature of AGN feedback on the distribution and kinematics of molecular gas should be conducted on spatial scales closer to the central engine (tens to hundreds of parsecs), considering the short flickering timescales ($<10^{5}$ yrs) associated with individual nuclear activity episodes (cite: Mart04; Hic14; Sch15; Kin15).

The observations of the circumnuclear disk (CND) of the Seyfert 2 galaxy NGC 1068 obtained with the Atacama Large Millimeter Array (ALMA) unveiled the dust continuum and molecular line emission in the CO(6–5) line from a 10 pc-diameter disk or torus of $M_{\rm gas}^{\rm torus}\sim1\times10^5$ M$_\ensuremath{\odot}$ (cite: GB16). This result has been confirmed by further ALMA images revealing the many ‘faces’ of the torus obtained in a set of different molecular lines showing the different layers of the disk extending from 7 to up to 30 pc scales (cite: Gal16; Ima18; Ima20; Imp19; GB19). These new high-resolution images showed that the launching of the molecular outflow is shaping not only the morphology of the torus but also its kinematics. The wide-angle AGN wind launched from the accretion disk of NGC 1068 is impacting a sizeable fraction of the gas inside the torus, driving a dusty molecular outflow, identified by vertical X-shape gas protrusions. The outflowing torus picture, also advocated to explain the ALMA observations of NGC 1377 (cite: Aal17; Aal20) and NGC 5643 (cite: Alo18), fits the scenarios predicted by radiation-driven wind models and numerical simulations (cite: Eli06; Wad12; Wad15; Wad16; Cha16; Cha17; Hoe17; Will19; Ven20; Will20). In this scenario, inflowing and outflowing components can coexist in different regions of the torus, a manifestation of the complex nature of the obscuring material around AGN (cite: Ram17; Hoe19; Gar24). On larger spatial scales, the ALMA images of NGC 1068 published by (cite: GB14) and (cite: GB19) resolved its CND as a ringed disk of $D\simeq400$ pc-size with a marked deficit of molecular gas in its central $\simeq130$ pc-region. This highly-contrasted ring morphology, reminiscent of a cavity, reflects the accumulation of molecular gas on the working surface of the AGN-driven ionized gas wind of NGC 1068. In agreement with this picture, the kinematics of molecular gas show strong deviations from circular motions modelled as a three-dimensional outflow that reflects the effects of AGN feedback.

The case of NGC 1068 is by no means unique. The existence of a cavity or lacuna in the inner 500 pc of the cold molecular gas distribution of the Seyfert 2 galaxy NGC 2110 was described by (cite: Ros19). The cavity, oriented in the direction of the radio jet and filled with warm molecular gas and an ionized gas wind, was also recently analyzed by (cite: Per23), pointing to a causal relationship similar to that favored to account for the nuclear-scale molecular gas deficit in NGC 1068. A deficit of molecular gas attributed to gas removal by the AGN wind was also identified in the CND of the Seyfert 2 galaxies NGC 5728 (cite: Shi19), ESO428-G014 (cite: Fer20), and NGC 7172 (cite: Alo23).

Significantly large (diameters $\geq$20-50 pc) and massive ($\sim 10^5-10^7M_\odot$) tori have been detected in cold molecular gas and dust in other local Seyferts, low-luminosity AGN, and compact obscured nuclei (cite: Aal17; Aal19; Alo18; Alo19; Alo20; Alo23; Izu18; Izu23; Aud19; Aud21; Com19; GB21; Tri22). In particular, (cite: GB21) used ALMA observations of the molecular gas obtained in the CO(3–2) and HCO$^+$(4–3) lines with spatial resolutions $\simeq0.1\ensuremath{''}$ ($7-13$ pc) in the CND of 19 nearby AGN, which belong to the core sample of the Galaxy Activity Torus and Outflow Survey (GATOS) and the southern hemisphere low luminosity AGN of the Nuclei of Galaxies (NUGA) sample (cite: Com19). The GATOS core sample was selected from the *Swift*/BAT catalog of AGN (cite: Bau13) with distances $<28\,$Mpc and luminosities $L_{\rm AGN}$(14-150 keV) $\ge 10^{42}\,{\rm erg~s}^{-1}$ to purposely complement the lower luminosity range covered by the NUGA survey (cite: Com19). The galaxies analyzed by (cite: GB21) share the presence of AGN ionized outflows and/or radio jets launched from the vicinity of dusty molecular disks which have median diameters and molecular gas masses of $\sim42$ pc and $\sim6\times10^5$ M$_{\ensuremath{\odot}}$, respectively. These compact disks tend to show an orientation perpendicular to the AGN outflow axes, as would be expected from an equatorial torus geometry.

(cite: GB21) analyzed the concentration of cold molecular gas (index-I in the notation used in their paper). They defined the concentration index as the ratio of gas surface densities derived at $r<50$ pc (a region characteristic of the tori and their surroundings) and $r<200$ pc (a region where molecular gas reservoirs are expected to build up and potentially reveal the smoking gun signature of AGN feedback), namely index-I$\equiv$$\log (\Sigma_{\rm H_2}^{\rm 50pc}/\Sigma_{\rm H_2}^{\rm 200pc})$. Their findings indicated that there is a statistically significant trend pointing to a decrease in molecular gas concentration indices in the higher luminosity and higher Eddington ratio sources of their sample beyond a turnover X-ray luminosity $L_{\rm 2-10keV}\simeq10^{42}$erg s$^{-1}$, suggesting the existence of two ‘branches’ in the parameter space defined by the concentration index and the AGN luminosity. AGN with luminosities below the turnover point show higher molecular gas concentration indices. This result would agree with the theoretical prediction that outflows in the highest luminosity AGN could partially clear the material around the black hole on the scales of the tori and their surrounding regions. The existence of a qualitatively similar trend was first found by (cite: Ric17b), recently confirmed by (cite: Ric22) and (cite: Ric23b), who found that the covering factor measured at X-ray wavelengths decreases with the Eddington ratio based on a survey of AGN in the local Universe, an indication that radiative feedback is an efficient mechanism capable of regulating the distribution of the gas and dust within the torus and its surrounding region preferentially in the most extreme AGN (cite: Ezh17; Gon17; Zhu18; Tob19; Tob21; Gar22). The latter is consistent with evidence from analytical models suggesting that IR-driven dusty winds can develop most favorably within a certain range of gas column densities and Eddington ratios (cite: Ven20; Alo21; Gar22).

More recently, (cite: Elf24) studied how the concentration of molecular gas as defined by (cite: GB21) changes as a function of $L_{\rm X}$ for 16 objects in the mm-Wave Interferometric Survey of Dark Object Masses project (WISDOM) sample. In their analysis they included a sizeable fraction ($\simeq$63$\%$) of early-type galaxies (ETG: 6 E and 4 SO Hubble types) that have X-ray luminosities well below the turnover identified in the distribution of concentration indices derived for the spiral galaxy sample studied by (cite: GB21). Six of the ten ETG analyzed by (cite: Elf24) showed concentration indices slightly below the range found by (cite: GB21) for very low-luminosity objects expected to be ruled by secular evolution processes rather than by AGN feedback. As we argue in Sect. [9](#summary), this discrepancy is not surprising, as we do not expect to find a direct evolutionary link that could connect bulge-dominated ETG to disk-dominated spiral galaxies in the scenario described by (cite: GB21) and this paper. In contrast, the few spiral galaxies in (cite: Elf24) with X-ray luminosities higher than 10$^{42}$ erg s$^{-1}$ closely follow the relation found by (cite: GB21).

# Aims of this paper

To verify the results of (cite: GB21) on a more robust statistical basis, we have selected for this paper a larger sample of nearby ($D_{\rm L}$=7-45 Mpc) 45 AGN and 19 non-AGN galaxies that have high-resolution multiline CO observations obtained at millimeter wavelengths by the ALMA and/or Plateau de Bure Interferometer (PdBI) arrays to study the distribution of cold molecular gas at CND scales ($r\leq200$ pc) in our sample. We explore whether the concentration and normalized radial distribution of cold molecular gas change as function of the X-ray luminosity to quantify the imprint left by AGN feedback on our sources. We purposely include in our analysis the data from a subset of 19 non-AGN galaxies used as a comparison sample. Unlike the analysis of (cite: GB21), restricted to the use of data obtained from a single CO line (the 3–2 transition), in this work we use the available data from 3 different CO transitions (the 1–0, 2–1, and 3–2 rotational lines) to investigate the dependence of molecular gas concentration on the CO line. We also use in our analysis near Infrared (NIR) integral field spectroscopy data obtained for the H$_2$ 1-0 S(1) line available for a subset of 35 targets of the CO-based sample. These observations allow us to complete using a larger sample the pioneering work of (cite: Hic13), who studied the differences in H$_2$ surface brightness profiles between quiescent and Seyfert galaxies and found evidence of higher central concentration in H$_2$ surface brightness profiles in AGN. The new data are used to derive the concentration and normalized radial distribution of the hot molecular gas phase as well as the hot-to-cold-molecular gas mass ratio as a function of the X-ray luminosity. Taken together, these observations provide the basis for an evolutionary scenario describing the feeding and feedback cycle of the gas in AGN that can be compared with the predictions of state-of-the-art numerical simulations.

The paper is organized as follows. We present in Sect. [3](#sample) the galaxy sample. Sect. [4](#observations) describes the ALMA and NIR observations used in this work. Sect. [5](#cold-H2) studies the distribution of cold molecular gas derived from CO performed by analyzing how the concentration and the radial distribution of this component changes as function of the X-ray luminosity in our sample, as detailed in Sects. [5.1](#CO-ratios), [5.2](#CO-dep), [5.3](#CO-profiles), and [5.4](#non-param). Sect. [6](#hot-H2) presents a similar analysis for the hot molecular gas component probed by the NIR observations of our sample, as detailed in Sects. [6.1](#NIR-ratios) and [6.2](#NIR-profiles). Section [7](#hot-cold) describes how the hot-to-cold molecular gas mass ratio changes as a function of the X-ray luminosity in our sample. A tentative scenario describing an evolutionary link connecting the galaxies analyzed in this work is presented in Sect [8](#discussion). The main conclusions of the paper are summarized in Sect. [9](#summary).

# The sample

Table [\[Tab1\]](#Tab1) lists the main observational parameters of the sample used in this work. We selected a sample of AGN and non-AGN spiral galaxies[^1] that have high-resolution CO(3-2), CO(2-1), and/or CO(1-0) observations obtained with ALMA and/or the PdBI arrays from different surveys. We consider a galaxy to be an AGN if it is well detected in hard X-rays and have a corresponding Seyfert/LINER classification according to NED. However, six of the galaxies detected in hard X-rays have $L_{\rm X}\leq10^{40}$erg. s$^{-1}$ but no optical identification of an AGN (see Table [\[Tab1\]](#Tab1) for details). For these sources a non-negligible contamination by X-ray binaries cannot be excluded. The combined sample includes the GATOS survey (cite: GB21; Alo21) the NUGA survey (cite: GB03; Gar12; Com19), a selection of targets of the Physics at High Angular resolution in Nearby GalaxieS survey (cite: Ler21), the WISDOM sample (cite: Oni17; Elf24) [^2], the Luminous Local AGN with Matched Analogs survey (cite: Ros18), as well as case studies of individual galaxies like M51 (cite: Sch13), NGC1068 (cite: GB19), and NGC7172 (cite: Alo23). We also used the CO(1–0) images obtained in a sample of 12 AGN observed with ALMA by (cite: Ric23a). The AGN targets are selected to lie at a range of distances $D_{\rm L}=7-45$ Mpc. We set the upper limit to the distance to image with enough spatial resolution the distribution of molecular gas in the circumnuclear disks of our targets. In particular, the median value of the spatial resolutions of the CO observations used in this work is $36$ pc and the corresponding value of the maximum recoverable scales of the images is $\simeq400$ pc. We also used a comparison sample of non-AGN drawn from the LLAMA and PHANGS surveys, with a range of distances similar to the AGN sources: $D_{\rm L}=7-41$ Mpc. The CO sample comprises 57 different images of 45 AGN as well as maps of 19 non-AGN galaxies. In our AGN sample 7 of the galaxies have images obtained in more than one CO transition. The latter includes NGC 6300, NGC 5643, NGC 7314, NGC 4388, and NGC 3227, which have data available from the 3–2 and 1–0 CO transitions, as well as NGC7172 and NGC 5728, which have data from the 3–2, 2–1, and 1–0 CO transitions. The availability of these data allows us to study the dependence of the trends analysed in this paper on the particular CO transition used to image the distribution of molecular gas in these sources.

Near-IR K-band (or H+K-band) integral field spectroscopy data are available for 46 of the galaxies of our sample, seven of which are non-AGN. Of these galaxies 35 have well detected H$_{\rm 2}$ 1–0 S(1) 2.12 $\mu$m (SNR$>$ 3) out to a radius of 200 pc. Two AGN (NGC 1365 and NGC 628) and four non-AGN (IC 5332, NGC 1079, NGC 3621, and NGC 5845) were found to have no detectable H$_{\rm 2}$ emission within this region and thus no concentration index was calculated for these targets. While NGC 4579, NGC 4501, and NGC 7465 have well detected H$_{\rm 2}$ emission out to a radius of 50 pc, available data only cover 65$\%$, 62$\%$, and 38$\%$, respectively, of the deprojected 200 pc radius aperture and thus only upper limits on the concentration index are obtained. In the majority of the 35 galaxies with well detected H$_{\rm 2}$ emission (24 galaxies) the data provide full coverage of the 200 pc radius deprojected aperture and in all other cases at least 70$\%$ of the aperture is measured and an aperture correction was applied assuming an azimuthally symmetric flux distribution.

Hard X-ray luminosities in the $2-10\,$keV band (hereafter $L_{\rm X}$) are adopted as a proxy for the AGN luminosity. For the majority of our sources we take $L_{\rm X}$ from (cite: Ric17a) rescaled to the assumed distances, except for five sources where we used archival observations to compute X-ray luminosities (see details in Table [\[Tab1\]](#Tab1) and Appendix [11](#Lx)).

Figure [1](#histo-samples) shows the distribution of independent data sets of AGN and non-AGN galaxies of our combined CO and NIR sample as a function of $L_{\rm X}$. AGN targets are evenly distributed as a function of $L_{\rm X}$ below the turnover luminosity ($L_{\rm X}$ $\simeq$ $10^{42.0}$erg s$^{-1}$), a regime for which (cite: GB21) found evidence of systematically high values of the concentration of molecular gas derived from CO(3-2). In this luminosity range ($10^{37.5}$erg s$^{-1}$ $\leq$ $L_{\rm X}$ $\leq$ $10^{42.0}$erg s$^{-1}$) the CO sample includes 27 galaxy images and NIR data from 15 targets. Beyond the turnover luminosity our CO sample includes a similar number of galaxy images: 30 CO and 17 NIR maps. Galaxies beyond the turnover are concentrated in a comparatively smaller luminosity range: $10^{42.0}$erg s$^{-1}$ $\leq$ $L_{\rm X}$ $\leq$ $10^{43.5}$erg s$^{-1}$. This uneven distribution of the sources as a function $L_{\rm X}$ ensures that the abrupt transition to lower molecular gas concentration indices, which appears beyond the turnover luminosity (cite: GB21), can be sufficiently sampled.

![](histo-samples.pdf)

![image](conc-median-Lx-samples.pdf) ![image](conc-versusLx-AGN-samples.pdf)

# Observations

## CO observations

Details on the reduction, imaging and post-processing of the CO data sets of the different surveys used in this work are included in the references listed in Sect [3](#sample). The CO-based ‘cold’ molecular gas masses were derived from the following expression, which includes the mass of Helium ($M_{\rm gas}^{\rm CO}=1.36\times M({\rm H_2})$):

$$\begin{equation}
\frac{M_{\rm gas}^{\rm CO}}{M_{\ensuremath{\odot}}}  = 1.07 \times 10^4 \times \left (\frac{\nu_{\rm 10}^2}{\nu_{\rm ij}^2} \right) \times \left (\frac{S_{\rm CO({\rm i-j})}}{{\rm Jy~km~s^{-1}}} \right) \times R_{\rm ij}^{\rm -1} \times \left (\frac{\alpha_{\rm CO}}{2\times10^{20}} \right) \times  \left (\frac{D}{\rm Mpc}\right)^2.
\label{mass-CO}
\end{equation}$$

In Eq. [\[mass-CO\]](#mass-CO), $\nu_{\rm ij}$ and $S_{\rm CO_{\rm ij}}$ are the frequency and the flux of the CO(i-j) transition (in Jy km s$^{-1}$-units), $R_{\rm ij}$ is the assumed CO(i-j)-to-CO(1-0) line ratio (in $T_{\rm mb}$-units), $\alpha_{\rm 
CO}$ is the assumed CO(1-0)-to-H$_{\rm 2}$ conversion factor in units of mol cm$^{-2}$ (K km s$^{-1}$)$^{-1}$, and $D$ is the distance in Mpc. Mass surface densities for the two representative regions used in this work ($r\leq50$ pc and $r\leq200$ pc) are derived by deprojecting the CO images using the $PA$ and $i$ values listed in Table [\[Tab1\]](#Tab1).

The estimates of the molecular gas masses derived from the different CO lines used in this work are subject to uncertainties related to the assumed $R_{\rm ij}$ ratio and to the adopted CO–to–H$_2$ conversion factor [^3]. In line with the values typically assumed in the literature (cite: Gen10; GB21) we estimate that the latter may contribute up to $\sim$0.12-0.13 dex each if we allow them to explore the typical range of values seen in the observations of different populations of galaxies on nuclear spatial scales and, also, if we assume that these uncertainties are uncorrelated. Under these extreme hypotheses the total uncertainty would amount to $\pm$0.20 dex. However, we emphasize that the analysis of the concentration indices and normalized radial distributions of molecular gas in the galaxies of the sample defined in Sect. [5](#cold-H2) would be insensitive to any galaxy-to-galaxy changes in the global conversion factors. Furthermore, any potential change of these conversion factors, which are here assumed to be the same for the two spatial scales analysed in this work ($r\leq50$ pc and $r\leq200$ pc), would likely reinforce the trends found in Sect. [5](#cold-H2) (cite: GB21).

|  |  |  |
|:--:|:--:|:--:|
| log$_{\rm 10}$$L_{\rm X}$ bin \[CO\] | number of galaxies | median $CCI$ |
| erg s$^{-1}$ | — | log units |
| bin-1: \[42.85–43.50\] | 9 | 0.10$\pm$0.04 |
| bin-2: \[42.65–42.85\] | 8 | -0.05$\pm$0.07 |
| bin-3: \[42.20–42.65\] | 8 | 0.13$\pm$0.27 |
| bin-4: \[41.73–42.20\] | 8 | 0.56$\pm$0.13 |
| bin-5: \[40.40–41.73\] | 8 | 0.58$\pm$0.23 |
| bin-6: \[39.00–40.40\] | 8 | 0.45$\pm$0.20 |
| bin-7: \[37.80–39.00\] | 8 | 0.36$\pm$0.11 |
| non-AGN bin | 19 | 0.27$\pm$0.13 |
| log$_{\rm 10}$$L_{\rm X}$ bin \[NIR\] | Number of galaxies | median $HCI$ |
| erg s$^{-1}$ | — | log units |
| bin-1: \[42.84–43.50\] | 8 | 0.16$\pm$0.18 |
| bin-2: \[42.37–42.82\] | 6 | 0.24$\pm$0.05 |
| bin-3: \[41.73–42.24\] | 6 | 0.62$\pm$0.25 |
| bin-4: \[39.68–41.42\] | 6 | 0.56$\pm$0.17 |
| bin-5: \[37.78–39.60\] | 6 | 0.46$\pm$0.07 |
| non-AGN bin | 3 | —- |
| log$_{\rm 10}$$L_{\rm X}$ bin \[hot/cold\] | Number of galaxies | hot/cold ratio concentration |
| erg s$^{-1}$ | — | log units |
| bin-1: \[42.98–43.50\] | 7 | 0.35$\pm$0.14 |
| bin-2: \[42.80–42.86\] | 7 | 0.21$\pm$0.10 |
| bin-3: \[42.37–42.67\] | 7 | 0.34$\pm$0.05 |
| bin-4: \[41.73–42.24\] | 7 | 0.06$\pm$0.16 |
| bin-5: \[39.60–41.42\] | 7 | -0.08$\pm$0.08 |
| bin-6: \[37.78–39.30\] | 7 | -0.09$\pm$0.19 |
|  |  |  |

: Median values of the concentration indices for the cold and hot molecular gas and hot-to-cold ratios.

Table notes: Column (1) identifies the range of $L_{\rm X}$ luminosities (in log units) used to define the different bins that group the CO and NIR data sets of the galaxies of the sample. Column (2) lists the number of independent data sets in each $L_{\rm X}$ bin. Column (3) lists the median values and the median absolute deviations of the concentration indices ($CCI$ and $HCI$) and the concentration of the hot-to-cold ratio (shown in Fig. [14](#hot-to-cold)) for each $L_{\rm X}$ bin.

## NIR observations

All NIR Integral Field Unit (IFU) observations were obtained with ESO SINFONI (cite: Eis03; Bon04) with the exception of NGC 7465, which was observed with OSIRIS at the W. M. Keck Observatory (cite: Lar06). Adaptive optics (AO) was employed in the acquisition of the vast majority of the data sets (31 in natural guide and 2 in laser guide star mode), and of those data sets without AO all were AGN and only one lacked a H$_2$ 2.12 $\mu$m detection (see Table [\[Tab5\]](#Tab5) for details). Reduction of the SINFONI data was performed using the SINFONI Data Reduction Software or a custom package SPRED developed at MPE (cite: Abu06). The OSIRIS data reduction pipeline was used for the single OSIRIS data set. In all cases reduction of the data followed standard reduction steps needed for near-IR spectra as well as additional routines necessary to reconstruct the data cube. For improved subtraction of OH sky emission lines the routines `mxcor` and `skysub` (cite: Dav07) were used, which correlate reconstructed object and sky cubes spectrally and shift them such that their OH line wavelengths match before subtracting the scaled sky frame. Nearby standard stars (A- or B-type) were observed close in time to the science frames and used for telluric correction and flux calibration. The typical flux calibration uncertainty is accurate to at least 10$\%$ in all data sets.

The emission-line flux distribution was extracted by fitting the H$_{\rm 2}$ 2.12 $\mu$m line profile using our custom code `LINEFIT` (cite: Dav11). This code fits the emission line in the spectrum of each spatial element, or spaxel, with an unresolved line profile (a sky line) convolved with a Gaussian, as well as a linear function to the line-free continuum. The point spread function (PSF) and the galaxy center, assumed to be coincident with the AGN location, are determined through fitting of the CO 2.29 $\mu$m bandhead. The CO bandhead was fit at each spaxel with a broadened late-type stellar template found to be well matched with our galaxy spectra. The intrinsic K-band CO equivalent width is assumed to be constant to within 20$\%$ at 12 Å, and a deviation from this value therefore represents dilution from the non-stellar continuum (cite: Dav07; Hic13; Bur15). This non-stellar continuum is assumed to represent the unresolved AGN-associated dust emission which we then utilize to establish the galaxy center and characterize the PSF.

Under the assumptions of local thermal equilibrium and an excitation temperature of 2000 K, the mass of ‘hot’ molecular gas component is obtained from (cite: Sco82; Rif14):

$$\begin{equation}
\frac{M({\rm H_2})}{M_{\ensuremath{\odot}}} = 5.0766 \times 10^{13} \left (\frac{F_{\rm H_2}}{\rm ergs^{-1} cm^{-2}}\right) \left (\frac{D}{\rm Mpc}\right)^2.
\label{hot-eq}
\end{equation}$$

As for the cold molecular gas component when we derive the hot molecular gas surface densities for $r\leq50$ pc and $r\leq200$ pc we adopt the same conversion factors for the two spatial scales and also correct for the mass of Helium using the expression $M_{\rm gas}^{\rm NIR}=1.36\times M({\rm H_2})$. As argued in Sect. [6.1](#NIR-ratios), we note that assuming common conversion factors for both spatial scales would underestimate the trends found in Sect [6](#hot-H2).

# Distribution of cold molecular gas

## Concentration indices

Following the methodology adopted by (cite: GB21) we explore below if a simple parameterization of the radial distribution of molecular gas can reveal the imprint of AGN feedback in the galaxies of the sample. To accomplish this, we first derived the average molecular gas surface densities measured from the different CO lines using two spatial scales representative of the nuclear ($r\leq50$ pc) and CND environments ($r\leq200$ pc). In our derivation we used the position angles ($PA$) and inclination angles listed in Table [\[Tab1\]](#Tab1). With this definition, nuclear scales probe the region typically occupied by the molecular tori and their immediate surroundings (cite: GB21; Alo21). We normalize the nuclear scale gas surface densities ($\Sigma^{\rm gas}_{\rm 50}$) by the corresponding densities measured on CND scales ($\Sigma^{\rm gas}_{\rm 200}$). In our estimate of $\Sigma^{\rm gas}_{\rm 50}$ and $\Sigma^{\rm gas}_{\rm 200}$ we adopted the same values of the conversion factors ($R_{\rm 31}$, $R_{\rm 21}$, and $\alpha_{\rm CO}$) for the two spatial scales. This normalization counterbalances any potential bias associated with the different overall molecular gas content of the galaxies of the sample and it therefore serves as a measurement of the concentration of molecular gas, which is the physical parameter relevant to the present analysis. Furthermore, the normalized radial distribution is by definition insensitive to any potential galaxy-to-galaxy change in the global conversion factors.

![](histo_bins_median_all-20pc.pdf)

The left panel of Figure [2](#conc-CO) illustrates how the concentration index of cold molecular gas, defined as the ratio (in logarithmic units) of the average H$_{\rm 2}$ surface densities derived from CO line emission at the two spatial scales representative of the nuclear and CND scales changes as a function of $L_{\rm X}$ in the galaxies of the sample. The concentration index (hereafter referred to as $CCI$) is therefore defined as:

$$\begin{equation}
  CCI \equiv~{\rm log}_{\rm 10}(\Sigma^{\rm gas}_{\rm 50}/\Sigma^{\rm gas}_{\rm 200}). 
\end{equation}$$

Table [\[Tab2\]](#Tab2) lists the values of $CCI$ for the sample. A visual inspection of Fig. [2](#conc-CO) indicates that the distribution of median values of the concentration index for the 7 luminosity bins listed in Table [1](#Tab3) [^4] shows evidence of a turnover at $L_{\rm X}
\simeq10^{41.5}$erg s$^{-1}$. AGN with $L_{\rm X}\leq10^{41.5}$erg s$^{-1}$ and non-AGN galaxies are located along a moderately ascending sequence, hereafter referred to as the ‘AGN build-up branch’, which is characterized by median values of $CCI$ that monotonically increase with $L_{\rm X}$ from $\simeq+0.27$$\pm$0.13 to $\simeq+0.58$$\pm$0.23. However, we note that given the associated error bars, the reported increase in $CCI$ among the galaxies of the AGN build-up branch is not statistically significant. AGN of higher luminosities lie at a descending sequence, hereafter referred to as the ‘AGN feedback branch’, which is characterized by median values of $CCI$ that sharply decrease from $\simeq+0.56$$\pm$0.13 down to $\simeq-0.05$$\pm$0.07. The concentration of molecular gas in the sample expands a statistically significant 0.63 dex range between the galaxies lying at the high end of the ‘AGN build-up branch’ and the galaxies showing the most extreme nuclear-scale molecular gas deficits in the ‘AGN feedback branch’. As illustrated in Fig. [17](#conc-CO-bis), if we adopt the region defined by the outer corona of the CND ($50$ pc$\leq r \leq 200$ pc) to normalize the molecular surface density of the nuclear region, the values of this alternative definition of the concentration of cold molecular gas expand a larger 0.72 dex range in our sample, equivalent to an overall factor $\geq$5 difference. We note that although galaxies along the AGN feedback branch tend to have higher Eddington ratios compared to the galaxies in the AGN build-up branch (as shown in the right panel of Fig. [2](#conc-CO)), the corresponding trend of $CCI$ as a function of the Eddington ratio, which is available for fewer sources in our sample, is less statistically significant than as a function of $L_{\rm X}$ (see Fig. [18](#Edd_ratio)).

To further confirm statistically the existence of two branches grouping the galaxies of the sample in the parameter space of Fig. [2](#conc-CO), we used the Multivariate Adaptive Regression Splines (`MARS`) fit routine available from the `Rstudio` package (cite: Rcorteam). The MARS algorithm gives the position of the breaking points (cut points) for a linear regression using multiple slopes. To this aim we derived the `MARS` fit on 100 Monte Carlo realisations of the $CCI$ versus $L_{\rm X}$ relation taking into account the data uncertainties in both axes due to the assumed conversion factors ($\pm0.2$ dex), and on the AGN luminosities ($\pm0.15$ dex). The result of the fit is displayed in the right panel of Fig. [2](#conc-CO). From this simulation we find a turnover for the distribution at log$_{\rm 10}L_{\rm X}=41.51$$\pm0.31$ erg s$^{-1}$ with a fit value of $CCI=0.53$$\pm$0.09, which similarly splits the sample into the two branches identified above based on the trend shown by the median values of $CCI$ as a function of $L_{\rm X}$. The power-law index found for the AGN buildup branch, $N=+0.03$$\pm$0.05, is consistent with a flat trend for $L_{\rm X}
\leq10^{41.5}$erg s$^{-1}$, confirming that the differences in $CCI$ values are not statistically significant in this luminosity regime. In contrast, the power-law index found for the AGN feedback branch, $N=-0.36$$\pm$0.08, shows a statistically significant evidence ($\simeq4.5\sigma$) of a descending trend of the concentration of molecular gas for galaxies lying beyond the turnover X-ray luminosity.

The fit of `MARS` for the distribution of $CCI$ values shown in the lower panel of Fig. [17](#conc-CO-bis), which uses the outer corona region of the CND to normalize the molecular surface densities, finds similar values for the turnover at log$_{\rm 10}L_{\rm X}=41.54$$\pm0.25$ erg s$^{-1}$ with a fit value of $CCI=0.64$$\pm$0.10, as well as power-law indices $N=+0.04$$\pm$0.06 and $N=-0.43$$\pm$0.09, for the AGN build-up and feedback branches respectively. The latter implies that the power-law index along the AGN feedback branch differs from zero by a statistically significant factor $\simeq~4.8\sigma$.

![image](histo_bin_median_comparison_1-5_zoom-20pc.pdf) ![image](histo_bin_median_comparison_1-7_zoom-20pc.pdf)

## Dependence of trends on CO transitions and conversion factors

The picture drawn from the different CO lines is overall consistent within the uncertainties regarding the existence of the two branches described above. In particular, along the AGN feedback branch, where the number of independent data sets ($N$) from the three transitions is comparable ($N$=13, 11, and 11 for the CO(3–2), CO(2–1), and CO(1–0) lines, respectively) the derived $CCI$ values concur to show a similar monotonic decline with $L_{\rm X}$ beyond the turnover (see discussion in Appendix [14](#CO-lines)). We can therefore conclude that for the typical range of physical conditions probed by the different CO transitions ($n_{\rm H_2}$$\simeq$a few 10$^{2-5}$ cm$^{-3}$, $T_{\rm K}$$\simeq$10-100 K) the decreasing trend of $CCI$ along the AGN feedback branch reported in Fig. [2](#conc-CO) shows a weak dependence on the particular line selected.

While a sizeable fraction of the data along the AGN build-up branch has been obtained only in the CO(2–1) line ($N$=6, 13, and 3 for the CO(3–2), CO(2–1), and CO(1–0) lines, respectively), the range of $CCI$ values derived from the different transitions is comparable within the errors. However, confirmation of whether the trend of $CCI$ with $L_{\rm X}$ along the AGN build-up branch is either moderately increasing or flat would require obtaining more data in the CO(3–2) and CO(2–1) lines.

While the values of $R_{\rm 31}$, $R_{\rm 21}$ for the galaxies in our sample are not constrained, we nevertheless expect that molecular gas will be comparatively less excited on nuclear scales at low AGN luminosities. Significant changes in the value $\alpha_{\rm CO}$ have only been described within galaxies on kpc-scales between their central kpc-region and their outer ($r>0.2R_{\rm 25}$) disks (cite: San13; Yas23). In any case, this is well beyond the spatial scales relevant to this work. The recent work of (cite: Ten23) found that the value of $\alpha_{\rm CO}$ in galaxy centers decreases with CO opacity and shows a strong anticorrelation with the gas velocity dispersion. Moreover, if anything, $\alpha_{\rm CO}$ values would probably have to be lowered on the nuclear ($r\leq50$ pc) as opposed to the CND-scales ($r\leq200$ pc) of the highest luminosity AGN galaxies in our sample where gas is expected to be more strongly irradiated and live in a dynamically perturbed environment characterized by an enhanced turbulence. Overall, our adopted choice of common values of the conversion factors for the nuclear and CND scales would be therefore conservative, underestimating the differences between the concentration of molecular gas measured for AGN build-up and AGN feedback branch galaxies shown in Fig. [2](#conc-CO).

![](maps-bins1-2-3.pdf)

![](maps-bins4-5-6.pdf)

![](maps-bins7-8.pdf)

## Radial distributions

We have shown in Sect. [5.1](#CO-ratios) that the distribution of $CCI$ values for the galaxies of the sample shows a turnover at log$_{\rm 10}L_{\rm X}\simeq41.5$$\pm0.3$ erg s$^{-1}$. We explore below in more detail how the shape of the radial profiles of cold molecular gas changes as a function of $L_{\rm X}$ in the sample. To this aim, we derived the radial profiles of cold molecular gas out to $r=210$ pc for each target using a radial binning $\Delta r=20$ pc, which corresponds to about half of the median value of the spatial resolutions of the CO observations used in this work. Individual profiles are further normalized by the CO flux integrated out to $r=210$ pc for each target ($I_{\rm norm}(r)$). Finally, we derived the median values of $I_{\rm norm}(r)$ and their associated median absolute deviations for the 7 $L_{\rm X}$ bins defined in Sect. [5.1](#CO-ratios).

Figure. [3](#histo-median-all) shows the $I_{\rm norm}(r)$ profiles derived from CO in the sample. As expected, the profiles show remarkable differences that fairly reflect the trends shown by the $CCI$ values as function of $L_{\rm X}$. Profiles appear as flat or inverted (i.e., with lower $I_{\rm norm}(r)$ values at small radii) for the highest X-ray luminosities of the galaxies of the AGN feedback branch grouped in $L_{\rm X}$ bins 1, 2, and 3. In contrast, galaxies in the peak phase of the AGN build-up branch, grouped in $L_{\rm X}$ bins 5, and 6, show highly concentrated molecular gas distributions. Furthermore, the lowest luminosity AGN and the non-AGN targets, grouped in bin 7 and the non-AGN bin respectively, show comparatively less concentrated radial profiles of molecular gas.

Figure  [4](#histo-median-bin1-5-7) shows that these differences are statistically significant when we compare the profiles of the highest luminosity AGN feedback branch targets (bin 1) with those of the highest luminosity AGN build-up phase targets (bin 5). A similar conclusion can be drawn when we compare the radial profiles of the galaxies belonging to the two extreme $L_{\rm X}$ classes, namely bins 1 and 7. In particular, Kolmogorov-Smirnov (KS) tests performed to reject the null hypothesis that the two pairs of radial profiles corresponding to bins 1 and 5, as well as to bins 1 and 7, are drawn from the same distribution yield consistently low $p$-values in either case ($p$-values$\leq$0.001).

Figures [5](#maps-bins1-2-3),  [6](#maps-bins4-5-6), and  [7](#maps-bins7-8) show the 2-dimensional and normalized radial distributions of the cold molecular gas in the inner $r\leq200$ pc central regions of 8 galaxies representative of the different AGN and non-AGN bin categories. The CO images help visualize directly the noticeable progression in the morphology of the distribution of the gas as a function of $L_{\rm X}$. The latter is characterized by a marked nuclear-scale ($r\leq50$ pc) deficit in the AGN feedback branch targets belonging to bins 1, 2, and 3 (NGC 7582, NGC 1068, and NGC 4388, respectively), which is reminiscent of a ring-like distribution. This is in stark contrast with the highly-concentrated nuclear-scale distribution of the gas in the targets of bins 4, 5 and 6 (NGC 6300, NGC 613, and NGC1808, respectively). The presence of a contrasted two-arm CO trailing nuclear spiral structure in NGC 613 and NGC 1808 has been interpreted as smoking gun evidence of ongoing AGN feeding in these targets (cite: Aud19; Aud21). This particular morphology would appear at an evolutionary stage where the gas is piling up on nuclear scales under the influence of negative gravity torques inside the Inner Lindblad Resonance (ILR) regions of the stellar bars (cite: Wad94; But96; Pee06; Com14). The distribution of cold molecular gas in the lower luminosity and non-AGN targets, shown in Fig. [7](#maps-bins7-8) (NGC 4826 and NGC 7727, respectively) is less centrally concentrated on average.

![image](summ-gatos-agn-Lx-vs-gini-03-v2.pdf) ![image](summ-gatos-agn-conc-vs-gini-03-v2.pdf) ![image](summ-gatos-agn-gini-vs-Rm-03-v2.pdf)

## Non-parametric analysis of the radial profiles

We confirm these results with an alternative, non-parametric method that builds on the Gini coefficient, $G$. This statistic, originally an econometric tool to measure income or wealth (in)equality, has been adopted in astronomy to e.g. quantify the (in)equality of the flux/brightness distribution in pixel sets (cite: Abr03; Lot04; Dav22). Here, we use $G$ in a different manner to assess the shape of our CO radial profiles. In short, CO flux and radius in our case respectively play the roles of people and income in the original application of $G$. More precisely, we measure the inequality in the distribution of radius$^2$, so that a flat radial profile corresponds to $G\approx1/3$, as expected for a uniform distribution. This is basically a normalization prescription that does not affect the results.

We calculate $G$ for each galaxy in our sample over the $r$=0–200 pc range with the `DescTools R` package. Associated 99% confidence intervals are derived from bootstrap percentiles. Fig. [8](#Gini) (upper panel) shows $G$ as a function of $L_X$ for the X-ray detected AGN galaxies. To first order, the overall distribution resembles that of $CCI$ in Fig. [2](#conc-CO): a virtually flat trend up to $L_X\approx10^{41.5}$ erg s$^{-1}$, at which point a noticeable drop sets in. This brings X-ray brightest galaxies close to the $G\approx1/3$ value that, as indicated above, corresponds to a flat CO radial profile. The excellent agreement between the $G$ and $CCI$ trends stems from the tight correlation between the two statistics (Spearman coefficient, $R_s$ of $\sim0.85$), which we show in Fig. [8](#Gini) (middle panel). Fig. [8](#Gini) (lower panel) displays an even tighter anticorrelation between $G$ and the flux-weighted mean radius ($R_s\sim-0.94$), which help us visualize the meaning of $G$ in this context. I.e., high $G$ values are linked with the build-up of nuclear concentrations of gas, whereas $G$ decreases as the mean radius of the CO light shifts outwards. In Fig. [8](#Gini) (lower panel), $G\approx1/3$ corresponds to mean radii of $\lesssim 140$ pc, which is close to the expectation for a radial profile flat over the $r$=0–200 pc range (2/3$\times200\approx133$ pc).

![image](conc-hot-50pc-200pc-Lx-samples.pdf) ![image](conc-hot-Lx-samples-MARS.pdf)

![](histo_NIR_bins_median_all-20pc.pdf)

![image](histo_NIR_bin_median_comparison_1-3_zoom-20pc.pdf) ![image](histo_NIR_bin_median_comparison_1-5_zoom-20pc.pdf)

# Distribution of hot molecular gas

More than half of the targets of the CO sample have available data from the H$_{\rm 2}$ 1–0 S(1) 2.12 $\mu$m line emission, a tracer of ‘hot’ molecular gas ($T_{\rm K}$$\simeq$a few 10$^3$ K). Using a similar methodology adopted in Sects. [5.1](#CO-ratios) and [5.3](#CO-profiles) to study the cold molecular gas, we use the NIR data to derive the concentration indices and the normalized radial distributions of hot molecular gas in the galaxies of our sample and investigate their potential trends with $L_{\rm X}$ in Sects. [6.1](#NIR-ratios) and [6.2](#NIR-profiles).

## Concentration indices

Figure [9](#conc-hot) shows the change with $L_{\rm X}$ of the concentration of hot molecular gas measured for the central regions of the galaxies of the sample as derived from the ratio of the average H$_{\rm 2}$ surface densities estimated from the 2.1$\mu$m line emission at the two spatial scales used in this work: nuclear ($r\leq50$pc; $\Sigma^{\rm hot}_{\rm 50}$) and CND scales ($r\leq200$pc; $\Sigma^{\rm hot}_{\rm 200}$). The concentration index of hot molecular gas (hereafter referred to as $HCI$) is therefore defined as:

$$\begin{equation}
  HCI \equiv~{\rm log}_{\rm 10}(\Sigma^{\rm hot}_{\rm 50}/\Sigma^{\rm hot}_{\rm 200}). 
\end{equation}$$

By definition, the values of $HCI$ are insensitive to any potential galaxy-to-galaxy variation of the conversion factors implicitly assumed in Eq [\[hot-eq\]](#hot-eq). Table [\[Tab2\]](#Tab2) lists the values of $HCI$ for the sample.

Figure [9](#conc-hot) shows that the trend of $HCI$ with $L_{\rm X}$, while qualitatively similar, is significantly much less pronounced than the trend shown by the $CCI$ index in Fig. [2](#conc-CO). The distribution of median values of $HCI$ for the 5 luminosity bins listed in Table [1](#Tab3) [^5] shows only tentative evidence of a turnover at $L_{\rm X}\simeq10^{42.0}$erg s$^{-1}$. The position of this break point is close to the turnover identified in the distribution of galaxies of the sample in the $CCI$-$L_{\rm X}$ parameter space of Fig. [2](#conc-CO). AGN below $L_{\rm X}\leq10^{42.0}$erg s$^{-1}$ in bins 3, 4, and 5 lie at a sequence characterized by median values of $HCI$ that monotonically increase with $L_{\rm X}$ from $\simeq+0.46$$\pm$0.07 to $\simeq+0.62$$\pm$0.25. However, we note that given the associated error bars, the reported increase in $HCI$ is not statistically significant. Beyond the turnover luminosity, AGN in bins 1 and 2 lie at a descending sequence qualitatively similar to the ‘AGN feedback branch’ of Fig. [2](#conc-CO), which is characterized by median values of $HCI$ that decrease from $\simeq+0.24$$\pm$0.05 down to $\simeq+0.16$$\pm$0.18. These values are marginally different to the ones characterizing the peak phase of the AGN build-up branch. In particular, the concentration of hot molecular gas in the sample spans a 0.46 dex range between the galaxies lying in the peak phase of the AGN build-up branch and the most extreme targets of the AGN feedback branch (see Fig. [9](#conc-hot)), namely a factor of two smaller range than shown by the $CCI$ index.

Our working hypothesis in deriving $HCI$ for the galaxies in our sample is that the conversion factor used in Eq. [\[hot-eq\]](#hot-eq) does not change between the nuclear and CND scales. Moreover, if anything, this conversion factor would probably have to be reduced on the nuclear ($r<$50 pc) scales where gas is expected to be hotter in the highest luminosity AGN sources. In this scenario we would be underestimating the differences between the concentration of hot molecular gas measured for AGN build-up and AGN feedback branch galaxies (see also a similar discussion regarding the trend of $CCI$ as a function of $L_{\rm X}$ in Sect. [5.1](#CO-ratios)).

Following the same approach of Sect. [5.1](#CO-ratios) we used the `MARS` algorithm to find the position of the breaking point and the slopes of the two AGN branches. The result of the fit is displayed in the right panel of Fig. [9](#conc-hot). From this simulation we find a turnover for the distribution at log$_{\rm 10}L_{\rm X}=42.04$$\pm0.27$ erg s$^{-1}$ with a fit value of $HCI=0.51$$\pm$0.04, which similarly splits the sample into the two branches identified above based on the trend shown by the median values of $HCI$ as a function of $L_{\rm X}$. The power-law index found for the AGN build-up branch, $N=+0.00$$\pm$0.05, is compatible with a flat trend for $L_{\rm X}\leq10^{42.04}$erg s$^{-1}$. The power-law index found for the AGN feedback branch, $N=-0.29$$\pm$0.11, shows only a very marginal statistical evidence ($\simeq2.6\sigma$) of a decreasing trend of the concentration of hot molecular gas for galaxies lying beyond the turnover X-ray luminosity. This confirms the visual impression that the decrease in molecular gas concentration identified in galaxies belonging to the AGN feedback branch most severely affects the cold phase of the gas probed by CO.

## Radial distributions

Figure [10](#histo-NIR-median-all) shows the average normalized radial distributions ($I_{\rm norm}$(r)) of hot molecular gas derived out to $r=210$ pc from the 2.1$\mu$m line emission for the 5 $L_{\rm X}$ bins defined in Sect. [6.1](#NIR-ratios). The profiles show differences that reflect the trends displayed by the $HCI$ values as function of $L_{\rm X}$ in Fig. [9](#conc-hot). Profiles appear to be nearly flat or with a moderate degree of central concentration for the higher X-ray luminosities characteristic of AGN feedback branch galaxies, grouped in $L_{\rm X}$ bins 1 and 2. Galaxies in the peak phase of the AGN build-up branch, grouped in $L_{\rm X}$ bins 3, 4, and 5, tend to show higher concentrations of hot molecular gas.

Figure [11](#histo-median-bin1-3-7) shows that these differences are marginally statistically significant when we compare the profiles of the highest luminosity AGN feedback branch targets (bin 1) with those of the highest luminosity AGN build-up phase targets (bin 3). However, the differences in the profiles between galaxies belonging to the two extreme $L_{\rm X}$ classes are not statistically significant (bins 1 and 5).

![](maps-bins1-2-3-NIR.pdf)

![](maps-bins4-5-6-NIR.pdf)

Figures [12](#maps-bins1-2-3-NIR) and  [13](#maps-bins4-5-6-NIR) show the 2-dimensional and normalized radial distributions of the hot molecular gas in the inner $r\leq200$ pc central regions of 6 galaxies representative of the different AGN and non-AGN bin categories. These images help visualize the differences in the morphology of the distribution of the hot gas as a function of $L_{\rm X}$. The latter is characterized by a low nuclear-scale ($r\leq50$ pc) concentration of hot molecular gas in the AGN feedback branch targets, belonging to bins 1, 2 (NGC 7582 and NGC 1068 respectively). This is in contrast with the more concentrated nuclear-scale distribution of the gas in the targets in the peak phase of the AGN build-up branch of bins 3, 4, and 5 (NGC6300, NGC 613, and NGC1672, respectively). The non-AGN target NGC7727 shows a concentration similar to that of NGC 1672.

![image](ratios-50pc-200pc-Lx-samples.pdf) ![image](ratio-50pc-Lx-samples.pdf)

![](bars.pdf)

![](Eddington-versusNH2-AGN-samples.pdf)

# Hot-to-cold molecular gas ratios

Taking advantage of the significant overlap between the CO and NIR samples, which span 42 independent map pairs, we also investigate the changes in the hot-to-cold molecular gas ratio as a function of $L_{\rm X}$.

The upper panel of Fig. [14](#hot-to-cold) shows how the hot-to-cold molecular gas mass surface density ratios changes between the nuclear and CND scales as a function of $L_{\rm X}$ in the sample. We estimated the ratio from the CO and 2.1$\mu$m line emissions on the nuclear ($r\leq50$pc) ($\Sigma^{\rm gas}_{\rm hot}$/$\Sigma^{\rm gas}_{\rm cold}$\[50 pc\]) and CND scales $r\leq200$pc ($\Sigma^{\rm gas}_{\rm hot}$/$\Sigma^{\rm gas}_{\rm cold}$\[200 pc\]). By definition, this ratio is insensitive to any galaxy-to-galaxy variation of conversion factors for the cold and hot molecular gas. The ratios, listed in Table [1](#Tab3) for 6 $L_{\rm X}$ luminosity bins [^6] indicate a trend suggestive of higher values of the hot-to-cold mass ratios on nuclear scales in the highest luminosity AGN sources. In particular, AGN below the turnover luminosity identified in Sect. [6.1](#NIR-ratios) ($L_{\rm X}\leq10^{42.0}$erg s$^{-1}$) in bins 4, 5, and 6 show median values approximately compatible with unity within the errors, indicating that for these range of luminosities there are no significant changes in the mass ratios between the two spatial scales. In contrast, beyond the turnover luminosity, AGN in bins 1, 2, and 3 show indications of a $\simeq1.5-2$ increase in the hot-to-cold molecular gas ratio on the nuclear scales compared to CND scales. The increase in the hot-cold-ratio reflects the factor of $\simeq1.5-2$ corresponding to the ratio 10$^{(|\Delta[CCI]|-|\Delta[HCI]|)}$, where $\Delta[CCI]$ and $\Delta[CCI]$ represent the range of variation of $CCI$ and $HCI$ measured along the AGN feedback branch.

However, the suggested twofold increase of the nuclear-scale fraction of hot molecular gas mass would not compensate for the nuclear-scale deficit of cold molecular gas mass identified in the highest-luminosity AGN sources of our sample. As illustrated in the lower panel of Fig. [14](#hot-to-cold), the hot-to-cold molecular gas mass fraction measured on nuclear scales is $\leq10^{-4}$ in all galaxies of the sample.

# An evolutionary scenario for the cycle of molecular gas at CND scales

The results obtained from the analysis of how the concentration and normalized radial distribution of cold and hot molecular gas change as function of X-ray luminosity in our sample confirm on a more robust statistical basis the previous findings of (cite: GB21). (cite: GB21) suggested the existence of two distinct categories of Local Universe spiral galaxies classified as AGN grouping them into two branches connected by an evolutionary sequence: the AGN build-up branch and the AGN feedback branch.

## The AGN build-up phase

Local Universe disk galaxies are expected to spend most of their lives either in a non-active phase or transitioning from a quiescent phase to a nascent AGN phase, moving along the AGN build-up branch. A low-luminosity AGN (log$L_{\rm X}$ $<$ 41.5-42 erg s$^{-1}$) during its build-up phase could start its activity cycle with a massive dusty molecular torus, which could have assembled following a fueling episode driven by the gas instabilities created by a stellar bar. In particular, the presence of a trailing nuclear spiral structure has been identified inside the ILR of some of the barred galaxies observed with ALMA at the highest spatial resolution ($\simeq4-9$ pc) in the sample: NGC 613, NGC 1566, NGC 1672, and NGC 1808 (cite: Com14; Com19; Aud19; Aud21). These galaxies lie at the peak phase of the AGN build-up branch, which is characterized by a high nuclear-scale concentration of molecular gas ($CCI\geq$\[+0.5,+0.8\]). The existence of a contrasting 2-arm CO trailing nuclear spiral structure in which the gas loses angular momentum has been interpreted as a smoking gun evidence of ongoing AGN feeding. Bars that are able to pile up gas close to the sphere of influence of the supermassive black hole, where the precessing frequency $\Omega-\kappa/2$ decreases with radius, can develop trailing nuclear spirals and fuel the AGN (cite: Wad94; But96; Pee06; Com14; Com21b; Com21a). In this scenario, the gas can build up the gas reservoir of the molecular torus and its surroundings, which naturally explains the high nuclear-scale concentration index measured in these objects.

Figure [15](#bars) shows how the fraction of large-scale stellar bars, identified in the Hubble SB or SAB types, is related to the $CCI$ values measured in the galaxies of our sample. Within the limits of our admittedly small statistics (eight galaxies for each of the eight $L_{\rm X}$ bins of AGN galaxies and 19 non-AGN galaxies; see Table [1](#Tab3)), Fig. [15](#bars) shows a nearly monotonic increase in both the fraction of large-scale bars and the $CCI$ values along the AGN build-up branch. The fraction of large-scale bars goes from $\simeq0.5-0.6$ for the non-AGN galaxies in our sample up to $\simeq0.9$ at luminosities just below the turnover. For galaxies belonging to the AGN feedback branch, the total fraction of large-scale bars decreases down to $\simeq$0.6-0.7, namely similar to the overall bar fraction derived from optical studies in spiral galaxies, regardless of their AGN or non-AGN classification (cite: deV91; Hun99). Taken at face value, this result might suggest that while bar-driven secular evolutionary processes regulate the CND-scale distribution of molecular gas along the AGN buildup branch, the role of large-scale bars, while still present to a significant extent, does not appear to outweigh processes specifically related to AGN feedback in redistributing molecular gas beyond a certain value of $L_{\rm X}$. However, the fact that large-scale bars are seen to be present in all galaxies in the sample at levels $\geq$2/3, suggests that the link between $CCI$ and the fraction of large-scale bars is weak.

Primary large-scale bars have timescales of $\simeq$Gyr and can eventually develop an ILR, and under certain circumstances a decoupled nuclear bar instability, a two-arm trailing spiral structure or a lopsided ($m=1$) mode can develop within this resonance. These smaller scale instabilities, with shorter associated timescales $\simeq10-100$ Myr, can help to drain the angular momentum of the gas and fuel the AGN. Numerical simulations predict that large-scale bars can become rounder and eventually get destroyed after the cumulative effect of several massive gas inflow episodes (cite: Com00; Bou02; Hop10). The timescales associated with the destruction of primary bars are $\simeq$10-100 longer than the corresponding timescales associated with the transit along the AGN feedback branch or with the black hole starvation phase, as estimated in Sect. [8.3](#timescales). Therefore, given this significant timescale mismatch, $CCI$ and the fraction of large-scale bars are not expected to be strongly linked. However, the existence of a potentially tighter correlation between the $CCI$ trends and the presence of nuclear bars or nuclear spirals should be further investigated with a larger sample.

## The AGN feedback phase

During the peak phase of the activity cycle the action of radiation pressure and/or jets could sweep away a significant fraction of the gas and dust ‘locally’ in the torus. These local (dusty) outflows could help regulate the feeding of the supermassive black hole and the growth of the molecular torus.

Figure [16](#dusty) shows the nuclear hydrogen column densities measured towards the AGN as a function of the Eddington ratio for the galaxies in our sample. Using semi-analytical models (cite: Ven20) found that the launch of polar IR-driven dusty outflows would be more favorable under certain conditions, which can be ascribed to a well defined region in the $N^{\rm AGN}_{\rm H}$-$\lambda_{\rm Edd}$ parameter space of Fig. [16](#dusty). We also plot in Fig. [16](#dusty) the predicted location of the blowout region described by (cite: Fab08), where the gas and dust are expected to be cleared by radiation-driven winds on nuclear scales. In particular, dusty winds can be launched from the torus when the acceleration due to the AGN radiation pressure and the acceleration due to the gravitational force from the central BH are balanced (cite: Ven20). For a fixed value of $\lambda_{\rm Edd}$ column densities below the value associated with the balance between the expected pressures acting on dust are conducive to the launch of dusty outflows. This mechanism is expected to be effective above column densities $N^{\rm AGN}_{\rm H}\geq10^{22}$ cm$^{-2}$ which corresponds to an opacity equal to unity in the near-IR. (cite: Alo21) analyzed the position of a sample of 13 nearby AGN including the 10 galaxies of GATOS core sample (cite: GB21), Circinus, NGC1365, and NGC 1068, and found that six galaxies have Eddington ratios and nuclear column densities favorable to the launching of IR-driven polar dusty winds. The extended MIR polar components detected by (cite: Alo21) in these candidate galaxies seemed to confirm the first predictions of (cite: Ven20). Furthermore, the analysis of the nuclear IR SED of a sample of Seyfert galaxies published by (cite: Gar22), found that galaxies close to the region favorable for the launch of dusty winds are best fit by torus models that include a wind component, while galaxies far from the IR-driven dusty wind region are best fit by classical torus models.

Figure. [16](#dusty) shows a clear dichotomy in the location of the galaxies belonging to the AGN build-up and feedback branches of our enlarged sample in the $N^{\rm AGN}_{\rm H}$-$\lambda_{\rm Edd}$ parameter space, where $N^{\rm AGN}_{\rm H}$ is the line-of-sight hydrogen column density derived from CO toward the AGN. In particular, galaxies in the AGN feedback branch with the lowest nuclear-scale molecular gas concentrations tend to be close to the region where IR-driven polar dusty outflows would be more favorably launched. In contrast, the galaxies of the AGN build-up branch with the highest nuclear scale molecular gas concentrations are located far from the region conducive to the launch of dusty outflows. Although the spatial and temporal scales associated with the launch of local dusty outflows in the torus (by the action of IR radiation pressure) and with the propagation of nuclear outflows (by the action AGN outflows and/or radio jets) are different, the distribution of the galaxies of our sample in Fig. [16](#dusty) suggests that there is a causal connection between the two outflow phenomena.

The vast majority of the sources belonging to the AGN feedback branch in our sample have ionized outflows and some have radio jets. At a later stage the propagation of AGN outflows and/or radio jets, which can be strongly coupled with the ISM of the host disk, can launch molecular outflows, entrain and in some cases clear a large fraction of the gas on larger spatial scales ($\sim$tens to hundreds of pc) as the nuclear activity cycle reaches its maximum. However, other factors beside the AGN luminosity can play a critical role in shaping the distribution, kinematics and excitation of molecular gas: the presence of an AGN wind and/or radio jet does not necessarily lead to a nuclear-scale molecular gas deficit in the disk of the host galaxy, since the latter requires that the coupling between the wind and/or jet and the ISM in the disk is strong enough to affect the redistribution of molecular gas. The impact of geometry on the coupling efficiency of AGN winds and the ISM has been shown by numerical simulations (cite: Gab14; Tor20; Mer23). For a fixed AGN luminosity, we therefore expect the distribution of concentration indices to show a scatter reflecting the intrinsic variance of the geometrical factors we may encounter (cite: Ram22).

The cases of NGC 613 and NGC 1068 are a good illustration of the importance of geometry. (cite: Aud19) imaged a fast ($v_{\rm out}\geq300$ kms$^{-1}$) $\simeq50$ pc-sized molecular outflow in the central region of NGC 613, detected in several molecular species (CO, HCN, HCO$^+$, and CS). (cite: Aud19) favored a scenario where the outflow is triggered by the 200 pc radio jet imaged by the VLA (cite: Hum92). Although the radio jet has triggered a small molecular outflow at its base, it has left the nuclear-scale in-plane distribution of the molecular gas virtually intact: NGC 613 exhibits high values of the molecular gas concentration indices. However, the low coupling efficiency of the jet with the ISM can be explained in a scenario where the jet is at a large angle relative to the disk of NGC 613, in stark contrast to the strong coupling efficiency of the radio jet and AGN wind of NGC 1068, which are at a small angle relative to the galaxy disk.

## An estimate of timescales

The sharp decline of the cold molecular gas concentration indices beyond the turnover luminosity ($L_{\rm X}\simeq10^{41.5}$erg. s$^{-1}$) shown by the distribution of $CCI$ values of Fig.[2](#conc-CO), suggests that the transition from the initial stage to the late-phase of the AGN feedback branch may occur on relatively short timescales. We can make a rough estimate of these typical transition timescales for four of the galaxies belonging to the late-phase AGN feedback branch, which are characterized firstly, by showing very low (negative) $CCI$ values and, secondly, which are known to harbor nuclear molecular outflows with $\dot{M}_{\rm out}$$\simeq$1 to a few tens of $M_{\ensuremath{\odot}}$ yr$^{-1}$ in the inner $r<50$ pc region (cite: GB14; GB19; GB21; Alo23): NGC 1068 ($CCI=-0.25$), NGC 4388 ($CCI=-0.17$), NGC 7172 ($CCI=-0.16$) , and NGC 7582 ($CCI=-0.16$). Under the hypothesis that these Seyferts had initial $CCI$ values typical of that of the late-phase AGN build-up branch sources, such as NGC 613 ($CCI=+0.82$), the transit timescale ($t_{\rm transit}$) can be estimated as:

$$\begin{equation}
 t_{\rm transit}\simeq\pi\times r^{2}\times \Delta[{\rm concentration}] \times\Sigma^{\rm gas}_{\rm 200}\times \dot{M}_{\rm out}^{-1}.
 \label{transition}
 
\end{equation}$$

In Eq. [\[transition\]](#transition), $\Delta[{\rm concentration}]=10^{CCI({\rm initial})}-10^{CCI({\rm final})}$ represents the concentration change for a particular galaxy, $r=50$ pc, and we assume that $\Sigma^{\rm gas}_{\rm 200}$ and $\dot{M}_{\rm out}^{-1}$ do not undergo a significant change during the transition. We derive for these sources: $t_{\rm transit}\simeq 1$-to a few 10 Myr, an estimate that confirms our expectation that the transition timescales are likely short.

AGN fueling is expected to be hindered on intermediate spatial scales during the late phase of the activity cycle, represented by the sources of our sample that show the most extreme nuclear-scale deficits of the AGN feedback branch and also harbour molecular outflows in the inner $r<50$ pc region. The gas reservoir in the torus of these AGN would be therefore eventually exhausted. An exhaustion timescale ($t_{\rm exhaustion}$) can be approximately estimated for the molecular tori of NGC 1068, NGC 4388, NGC 7172, and NGC 7582, using the masses of the tori ($M_{\rm torus}$) derived by (cite: GB21) and (cite: Alo23) for these sources, assuming a canonical accretion efficiency $\epsilon\simeq0.1$, and a bolometric correction $k_{\rm bol}\simeq10$ in the expression:

$$\begin{equation}
  t_{\rm exhaustion} \simeq M_{\rm torus} \times \epsilon \times c^2 \times (k_{\rm bol}\times L_{\rm X})^{-1}.
  \label{exhaustion}
 
\end{equation}$$

We derive from Eq. [\[exhaustion\]](#exhaustion) for these sources: $t_{\rm exhaustion}\simeq 1$-to a few 10 Myr. There is both observational and theoretical evidence that AGN can have much shorter *flickering* timescales ranging from a few years up to $\simeq$10$^5$ yr (cite: Sch15; Kin15). With the values of $t_{\rm exhaustion}$ estimated above, AGN activity could still continue in these Seyfert galaxies for a time span $\simeq10-100$ longer than the expected *flickering* timescale.

Once the gas reservoir in the torus is exhausted, a BH ‘starvation’ or build-down phase should follow. During this phase we might expect, first, that the CND-scale distribution of molecular gas does not change significantly (namely the $CCI$ index remains approximately constant) as AGN feedback is progressively turned off, and second, that the AGN luminosity decreases on short timescales. Thus, in the $L_{\rm X}-CCI$ parameter space, galaxies would move along quasi-horizontal trajectories during the BH starvation phase as they leave the feedback branch. The described evolutionary cycle could be restarted after the completion of another AGN fueling phase leading to a secular increase in the $CCI$ index and $L_{\rm X}$ along the AGN build-up phase. The fact that we see only one galaxy (ESO-093-G003, classified as non-AGN) in our sample with a low cold molecular gas concentration (negative $CCI$; $\sim$-0.02 in ESO-093-G003) and a very low AGN luminosity ($L_{\rm X}<<$10$^{41.5}$ erg. s$^{-1}$) suggests that the BH starvation phase should be very short. Alternatively, the striking lack of targets in the lower left region of the $L_{\rm X}-CCI$ diagram could be explained if galaxies did not necessarily leave the AGN build-up branch during the build-down phase; in this scenario, half of the targets in the AGN build-up branch would actually be in the build-down evolutionary phase.

A proper dating of the transition timescales relevant to the parameter space of Fig [2](#conc-CO) would require self-consistent numerical simulations of the gas cycle capable of following the evolution of the CND-scale distribution of cold molecular gas in realistic AGN environments similar to those characterizing the Seyfert galaxies in our sample. These simulations could be used to verify/falsify the validity of the different evolutionary scenarios.

## The hot molecular gas cycle

That the hot molecular gas follows a qualitatively similar trend to that seen in the central concentration index of cold molecular gas can be explained in a scenario in which the hot molecular gas is entrained in the outflow as is suggested to be the case in NGC 5728 (cite: Shi19). In some galaxies, rather than AGN feedback removing all molecular gas within the central region, the cold molecular gas “hole” has been observed to be filled with hot molecular and/or highly ionized gas (cite: Ros19; Fer20). However, as noted in Sect. [7](#hot-cold), the hot molecular gas within this CO “hole” does not account for the deficit of gas and thus to some extent the AGN feedback has successfully cleared a significant portion of the gas. (cite: Shi19) found in NGC 5728 that within the cold molecular gas “holes” in the outflow region there is a highly stratified structure of highly ionized gas surrounded by an outer layer of hot molecular gas. This stratified outflow is interpreted as an outflow which has successfully cleared the central region of molecular gas but is oriented such that this outflow disrupts the circumnuclear disk. The hot molecular gas within the disk rotates into the outflow region and becomes entrained in it along the outer extent of the outflow. This emphasizes the importance of the geometry of the disk and outflow orientations in that a coupling of the outflow with the ISM is necessary to effectively redistribute molecular gas. In such a case both the cold and hot molecular gas will be cleared, although to varying degrees depending on the disk and outflow geometries. Whether the nuclear-scale deficit shared by the ’cold’ and ’hot’ phases of H$_{\rm 2}$ can be partly compensated by the ’warm’ phase (T$_{k}$$\simeq$a few 100 K) of the molecular gas remains to be confirmed by future observations of the sample with facilities such as the James Webb Space Telescope.

# Summary and conclusions

We selected a sample of nearby ($D_{\rm L}=7-45$ Mpc) 45 AGN and 19 non-AGN galaxies that have high-resolution multiline CO observations obtained at millimeter wavelengths by the ALMA and/or PdBI arrays to study the distribution of cold molecular gas on CND scales ($r\leq200$ pc) in the galaxies of our sample. We analyzed whether the concentration and normalized radial distribution of cold molecular gas change as function of the X-ray luminosity to decipher the imprint potentially left by AGN feedback. We also incorporated NIR integral field spectroscopy data obtained for the H$_2$ 1-0 S(1) line available for a subset of 35 targets of the CO-based sample used in this work. These data allowed us to study the concentration and normalized radial distribution of the hot molecular gas phase as well as the hot-to-cold-molecular gas mass ratio as a function of the X-ray luminosity in this subsample. The main results of this paper are summarized as follows:

- The cold molecular gas concentration, defined by the ratio $CCI \equiv$ log$_{\rm 10}(\Sigma^{\rm gas}_{\rm 50}/\Sigma^{\rm gas}_{\rm 200}$), shows a statistically significant turnover at a luminosity breakpoint $L_{\rm X}\simeq10^{41.5}$erg s$^{-1}$, which divides the sample into two branches in the $CCI$-$L_{\rm X}$ parameter space. AGN and non-AGN below the luminosity breakpoint, located along the ‘AGN build-up branch’, have $CCI$ values that increase with $L_{\rm X}$ from $\simeq+0.27$$\pm$0.13 to $\simeq+0.58$$\pm$0.23. Higher luminosity AGN beyond the luminosity breakpoint, located along the ‘AGN feedback branch’, show a sharp decrease in the concentration of molecular gas from $\simeq+0.56$$\pm$0.12 down to $\simeq-0.05$$\pm$0.07. The cold molecular gas concentration spans a factor $\simeq$4.3 between the galaxies lying at the high end of the AGN build-up branch and the galaxies showing the most extreme nuclear-scale molecular gas deficits in the AGN feedback branch. These trends confirm, on a three times larger sample, previous evidence found in the context of the GATOS survey by (cite: GB21).

- The normalized radial profiles ($I_{\rm norm}(r)$) of the cold molecular gas in the galaxies of our sample reflect the trends shown by the $CCI$ values as function of $L_{\rm X}$. The profiles appear as flat or inverted in the AGN feedback branch galaxies. In contrast, galaxies in the peak phase of the AGN build-up branch show highly concentrated molecular gas distributions. In addition, lower luminosity AGN galaxies and non-AGN targets show comparatively less concentrated molecular gas radial profiles.

- We performed an independent non-parametric analysis of the CND-scale distribution of the cold molecular gas in our sample by deriving the Gini coefficients associated with their radial profiles. The radial Gini coefficients are shown to be strongly correlated with the molecular gas concentration. On the other hand, the radial Gini coefficients are shown to be strongly anticorrelated with the flux-weighted mean radius of the distribution of the gas. The distribution of the radial Gini coefficients with $L_{\rm X}$ show a similar turnover at a luminosity breakpoint $L_{\rm X}\simeq10^{41.5-42.0}$erg s$^{-1}$.

- The hot molecular gas concentration, defined by the ratio $HCI \equiv$ log$_{\rm 10}(\Sigma^{\rm hot}_{\rm 50}/\Sigma^{\rm hot}_{\rm 200}$) shows a qualitatively similar but less pronounced turnover compared to the trend shown by the $CCI$ index. We identify a luminosity breakpoint $L_{\rm X}\simeq10^{42.0}$erg s$^{-1}$ dividing the sample into the AGN build-up and feedback branches. The concentration of hot molecular gas in the sample spans a factor $\simeq2.9$ range between the galaxies lying in the peak phase of the AGN build-up branch and the most extreme AGN feedback branch targets. The normalized radial profiles ($I_{\rm norm}(r)$) of the hot molecular gas reflect the $HCI$-$L_{\rm X}$ trends.

- We find higher values of the hot-to-cold molecular gas mass ratios on nuclear scales in the highest luminosity AGN sources of the AGN feedback branch. In particular, beyond the turnover luminosity, AGN show indications of a twofold increase in the hot-to-cold molecular gas ratio on the nuclear scales compared to CND scales. However, this twofold increase does not compensate for the nuclear-scale deficit of cold molecular gas mass identified in the highest luminosity AGN.

- We present a tentative scenario describing an evolutionary link connecting the galaxies analyzed in this work. While most of galaxies are expected to spend most of their lives transitioning from a quiescent phase to a nascent AGN phase, moving along the AGN build-up branch, the sharp decline of the cold molecular gas concentration indices beyond the turnover luminosity ($L_{\rm X}\simeq10^{41.5}$erg. s$^{-1}$) suggests that the transition from the initial stage to the late-phase of the AGN feedback branch occurs on short timescales ($\simeq1$-to a few 10 Myr). At the end of the AGN feedback phase the gas reservoir in the torus would be eventually exhausted. Similarly, the timescales associated to the ensuing BH starvation phase are estimated to be very short.

The evolutionary scenario described in this paper would outline the cycle of molecular gas at CND scales in spiral disk galaxies undergoing an AGN episode. However, the secular evolution processes in active galaxies classified as ETG (E and S0) are expected to be very different from those governing the redistribution of molecular gas in later-type spiral galaxies, which are in all likelihood related to the action of stellar bars or spiral density waves absent in E galaxies in particular. Furthermore, the CND-scale distribution of molecular gas in ETG may rather reflect the evolutionary stage of the gas settling process, which in E and S0 objects is often associated with an external accretion event during an interaction (cite: Dav14; Dav17). Therefore, we do not expect to find a direct evolutionary link that could connect bulge-dominated ETG to disk-dominated spiral galaxies in the scenario described in this paper. Taken together, this could explain that while the spiral galaxies in (cite: Elf24) with X-ray luminosities higher than 10$^{42}$ erg s$^{-1}$ closely follow the relation found by (cite: GB21) and this work, the fraction ($\simeq 60\%$) of the low-luminosity ETG analyzed by (cite: Elf24) would deviate from the general trend followed by spiral galaxies in the AGN build-up branch.

During the low-luminosity and low Eddington ratio phases, the kinetic feedback mode associated with radio jets can compete with, or even overtake, the radiative feedback mode that dominates at higher luminosities. Jets can sweep away interstellar gas provided that the coupling with the ISM in the disk of the host is sufficient. In some cases the jet ejected from the central engine can impact a significant fraction of the plane of the galaxy, due to the random orientation of the accretion disk and the tori, which are generally decoupled from the orientation of the large-scale disk (cite: Mor13; Mor15; GB14; Das15; Alo18; Ang21; Gar21; Ram22; Ruf22; Rao23; Aud23). The potential role of jets in AGN feedback for different radio power regimes has been demonstrated by numerical simulations (cite: Wag11; Wag12; Muk18a; Muk18b; Mek22). Unfortunately, the influence that radio jets can have on the distribution of molecular gas cannot be studied to the same extent as for $L_{\rm X}$ in most of the galaxies in our sample, because high spatial resolution and high sensitivity radio images are only available for a small fraction of our targets.

# Acknowledgements

We thank the referee for his thorough and constructive report. This paper makes use of the following ALMA data, which have been processed as part of 1) the GATOS survey: ADS/JAO.ALMA $\#$2016.1.00232.S, $\#$2016.1.00254.S., $\#$2017.1.00082.S, $\#$2018.1.00113.S, and $\#$ 2019.1.00618.S 2)the NUGA survey: $\#$2015.1.00404.S and $\#$2016.1.00296.S 3) the LLAMA survey: $\#$2019.1.01742.S 4)the WISDOM survey:

$\#$2017.1.00517.S, $\#$2018.1.00572.S, and $\#$2019.1.00363.S 4)the survey PI-ed by Claudio Ricci $\#$2019.1.01230.S and $\#$2021.1.00812.S 5) the PHANGS-ALMA CO(2-1) survey: ADS/JAO.ALMA$\#$2012.1.00650.S, ADS/JAO.ALMA$\#$2 013.1.00803.S, ADS/JAO.ALMA$\#$2013.1.01161.S, ADS/ JAO.ALMA$\#$2015.1.00121.S, ADS/JAO.ALMA$\#$2015.1.00 782.S, ADS/JAO.ALMA$\#$2015.1.00925.S, ADS/JAO. ALMA$\#$2015.1.00956.S, ADS/JAO.ALMA$\#$2016.1. 00386.S, ADS/JAO.ALMA$\#$2017.1.00392.S, ADS/JAO. ALMA$\#$2017.1.00766.S, ADS/JAO.ALMA$\#$2017.1.00886. L, ADS/JAO.ALMA$\#$2018.1.00484.S, ADS/JAO. ALMA$\#$2018.1.01321.S, ADS/JAO.ALMA$\#$2018.1.01 651.S, ADS/JAO.ALMA$\#$2018.A.00062.S, ADS/JAO. ALMA$\#$2019.1.01235.S, ADS/JAO.ALMA$\#$2019.2.00129.S

ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

This work is also based on observations carried out with the IRAM PdBI Interferometer in the context of the NUGA (PIs: S. Garcı́a-Burillo & and F. Combes) and PAWS (PI: E. Schinnerer) projects. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain). We acknowledge the IRAM staff from the Plateau de Bure and from Grenoble for carrying out the observations and help provided during the data reduction. We acknowledge the use of the following data reduction and software packages: `CASA` (cite: McM07), `astropy` (cite: Astropy2013; Astropy2018), and `Rstudio package` (cite: Rcorteam)

SGB, AU, and MQ acknowledge support from the Spanish grant PID2022-138560NB-I00, funded by MCIN/AEI/10.13039/501100011033/FEDER, EU. MPS acknowledges support from grant RYC2021-033094-I funded by MICIU/AEI/10.13039/501100011033 and the European Union NextGenerationEU/PRTR. IGB acknowledges support from STFC through grants ST/S000488/1 and ST/W000903/1. MTL acknowledges grant support from the Space Telescope Science Institute (ID: JWST-GO-01670.007-A). MS acknowledges support by the Ministry of Science, Technological Development and Innovation of the Republic of Serbia (MSTDIRS) through contract no. 451-03-66/2024-03/200002 with the Astronomical Observatory (Belgrade). AAH acknowledges support from grant PID2021-124665NB-I00 funded by MCIN/AEI/10.13039/501100011033 and by ERDF A way of making Europe. EB acknowledges the María Zambrano program of the Spanish Ministerio de Universidades funded by the Next Generation European Union and is also partly supported by grant RTI2018-096188-B-I00 funded by the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033. CRA acknowledges support from project "Tracking active galactic nuclei feedback from parsec to kiloparsec scales", with reference PID2022-141105NB-I00. DJR acknowledges support from the UK STFC through grant ST/X001105/1. CR acknowledges support from Fondecyt Regular grant 1230345 and ANID BASAL project FB210003. OGM acknowledges financial support from UNAM through the project PAPIIT IN109123 and CONAHCyT through the project "Ciencia de Frontera 2023" CF-2023-G-100.

162 natexlab

(ref: Aal20) Aalto, S., Falstad, N., Muller, S., et al. 2020, A&A, 640, A104

(ref: Aal12) Aalto, S., Garcia-Burillo, S., Muller, S., et al. 2012, A&A, 537, A44

(ref: Aal17) Aalto, S., Muller, S., Costagliola, F., et al. 2017, A&A, 608, A22

(ref: Aal19) Aalto, S., Muller, S., König, S., et al. 2019, A&A, 627, A147

(ref: Abr03) Abraham, R. G., van den Bergh, S., & Nair, P. 2003, ApJ, 588, 218

(ref: Abu06) Abuter, R., Schreiber, J., Eisenhauer, F., et al. 2006, New A Rev., 50, 398

(ref: Alat11) Alatalo, K., Blitz, L., Young, L. M., et al. 2011, ApJ, 735, 88

(ref: Alo21) Alonso-Herrero, A., Garcı́a-Burillo, S., Hönig, S. F., et al. 2021, A&A, 652, A99

(ref: Alo19) Alonso-Herrero, A., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2019, A&A, 628, A65

(ref: Alo23) Alonso-Herrero, A., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2023, A&A, 675, A88

(ref: Alo18) Alonso-Herrero, A., Pereira-Santaella, M., Garcı́a-Burillo, S., et al. 2018, ApJ, 859, 144

(ref: Alo20) Alonso-Herrero, A., Pereira-Santaella, M., Rigopoulou, D., et al. 2020, A&A, 639, A43

(ref: Ang17) Anglés-Alcázar, D., Davé, R., Faucher-Giguère, C.-A., Özel, F., & Hopkins, P. F. 2017, MNRAS, 464, 2840

(ref: Ang21) Anglés-Alcázar, D., Quataert, E., Hopkins, P. F., et al. 2021, ApJ, 917, 53

(ref: Ant93) Antonucci, R. 1993, ARA&A, 31, 473

(ref: Ant85) Antonucci, R. R. J. & Miller, J. S. 1985, ApJ, 297, 621

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Aud19) Audibert, A., Combes, F., Garcı́a-Burillo, S., et al. 2019, A&A, 632, A33

(ref: Aud21) Audibert, A., Combes, F., Garcı́a-Burillo, S., et al. 2021, A&A, 656, A60

(ref: Aud23) Audibert, A., Ramos Almeida, C., Garcı́a-Burillo, S., et al. 2023, A&A, 671, L12

(ref: Bau13) Baumgartner, W. H., Tueller, J., Markwardt, C. B., et al. 2013, ApJS, 207, 19

(ref: Bol13) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Bol17) Bolatto, A. D., Wong, T., Utomo, D., et al. 2017, ApJ, 846, 159

(ref: Bon04) Bonnet, H., Abuter, R., Baker, A., et al. 2004, The Messenger, 117, 17

(ref: Bou02) Bournaud, F. & Combes, F. 2002, A&A, 392, 83

(ref: Bur15) Burtscher, L., Orban de Xivry, G., Davies, R. I., et al. 2015, A&A, 578, A47

(ref: Busch2017) Busch, G., Eckart, A., Valencia-S., M., et al. 2017, A&A, 598, A55

(ref: But96) Buta, R. & Combes, F. 1996, , 17, 95

(ref: Caglar2020) Caglar, T., Burtscher, L., Brandl, B., et al. 2020, A&A, 634, A114

(ref: Cha16) Chan, C.-H. & Krolik, J. H. 2016, ApJ, 825, 67

(ref: Cha17) Chan, C.-H. & Krolik, J. H. 2017, ApJ, 843, 58

(ref: Com00) Combes, F. 2000, in Astronomical Society of the Pacific Conference Series, Vol. 197, Dynamics of Galaxies: from the Early Universe to the Present, ed. F. Combes, G. A. Mamon, & V. Charmandaris, 15

(ref: Combes21) Combes, F. 2021a, Active Galactic Nuclei: Fueling and Feedback

(ref: Com21b) Combes, F. 2021b, in Nuclear Activity in Galaxies Across Cosmic Time, ed. M. Pović, P. Marziani, J. Masegosa, H. Netzer, S. H. Negu, & S. B. Tessema, Vol. 356, 177–183

(ref: Com21a) Combes, F. 2021c, IAU Symposium, 359, 312

(ref: Com19) Combes, F., Garcı́a-Burillo, S., Audibert, A., et al. 2019, A&A, 623, A79

(ref: Com13) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2013, A&A, 558, A124

(ref: Com14) Combes, F., Garcı́a-Burillo, S., Casasola, V., et al. 2014, A&A, 565, A97

(ref: Das15) Dasyra, K. M., Bostrom, A. C., Combes, F., & Vlahakis, N. 2015, ApJ, 815, 34

(ref: Dav19) Davé, R., Anglés-Alcázar, D., Narayanan, D., et al. 2019, MNRAS, 486, 2827

(ref: Dav11) Davies, R., Förster Schreiber, N. M., Cresci, G., et al. 2011, ApJ, 741, 69

(ref: Dav07) Davies, R. I. 2007, MNRAS, 375, 1099

(ref: Dav17) Davies, R. I., Hicks, E. K. S., Erwin, P., et al. 2017, MNRAS, 466, 4917

(ref: Dav14) Davies, R. I., Maciejewski, W., Hicks, E. K. S., et al. 2014, ApJ, 792, 101

(ref: Davies2007) Davies, R. I., Müller Sánchez, F., Genzel, R., et al. 2007, ApJ, 671, 1388

(ref: Dav22) Davis, T. A., Gensior, J., Bureau, M., et al. 2022, MNRAS, 512, 1522

(ref: deV91) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, Herold G., J., et al. 1991, Third Reference Catalogue of Bright Galaxies

(ref: Dom20) Domı́nguez-Fernández, A. J., Alonso-Herrero, A., Garcı́a-Burillo, S., et al. 2020, A&A, 643, A127

(ref: Eis03) Eisenhauer, F., Abuter, R., Bickert, K., et al. 2003, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4841, Instrument Design and Performance for Optical/Infrared Ground-based Telescopes, ed. M. Iye & A. F. M. Moorwood, 1548–1561

(ref: Elf24) Elford, J. S., Davis, T. A., Ruffa, I., et al. 2024, MNRAS, 528, 319

(ref: Eli06) Elitzur, M. & Shlosman, I. 2006, ApJL, 648, L101

(ref: Eli21) Ellison, S. L., Wong, T., Sánchez, S. F., et al. 2021, MNRAS, 505, L46

(ref: Ezh17) Ezhikode, S. H., Gandhi, P., Done, C., et al. 2017, MNRAS, 472, 3492

(ref: Fab08) Fabian, A. C., Vasudevan, R. V., & Gandhi, P. 2008, MNRAS, 385, L43

(ref: Fazeli2020a) Fazeli, N., Busch, G., Eckart, A., et al. 2020a, A&A, 638, A53

(ref: Fazeli2020b) Fazeli, N., Eckart, A., Busch, G., et al. 2020b, A&A, 638, A36

(ref: Fer20) Feruglio, C., Fabbiano, G., Bischetti, M., et al. 2020, ApJ, 890, 29

(ref: Fio17) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: Flu21) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2021, MNRAS, 505, 5753

(ref: Flu19) Fluetsch, A., Maiolino, R., Carniani, S., et al. 2019, MNRAS, 483, 4586

(ref: Gab14) Gabor, J. M. & Bournaud, F. 2014, MNRAS, 441, 1615

(ref: Gal16) Gallimore, J. F., Elitzur, M., Maiolino, R., et al. 2016, ApJL, 829, L7

(ref: Gal23) Gallimore, J. F. & Impellizzeri, C. M. V. 2023, ApJ, 951, 109

(ref: Gar21) Garcı́a-Bernete, I., Alonso-Herrero, A., Garcı́a-Burillo, S., et al. 2021, A&A, 645, A21

(ref: Gar22) Garcı́a-Bernete, I., González-Martı́n, O., Ramos Almeida, C., et al. 2022, A&A, 667, A140

(ref: Gar24) Garcı́a-Bernete, I., Pereira-Santaella, M., González-Alfonso, E., et al. 2024, A&A, 682, L5

(ref: GB21) Garcı́a-Burillo, S., Alonso-Herrero, A., Ramos Almeida, C., et al. 2021, A&A, 652, A98

(ref: Gar12) Garcı́a-Burillo, S. & Combes, F. 2012, in Journal of Physics Conference Series, Vol. 372, Journal of Physics Conference Series, 012050

(ref: GB03) Garcı́a-Burillo, S., Combes, F., Hunt, L. K., et al. 2003, A&A, 407, 485

(ref: GB19) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2019, A&A, 632, A61

(ref: GB16) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2016, ApJL, 823, L12

(ref: GB14) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125

(ref: Gen10) Genzel, R., Tacconi, L. J., Gracia-Carpio, J., et al. 2010, MNRAS, 407, 2091

(ref: Gon17) González-Martı́n, O., Masegosa, J., Hernán-Caballero, A., et al. 2017, ApJ, 841, 37

(ref: Gon09) González-Martı́n, O., Masegosa, J., Márquez, I., Guainazzi, M., & Jiménez-Bailón, E. 2009, A&A, 506, 1107

(ref: Har23) Harrison, C. M., Girdhar, A., & Ward, S. R. 2023, arXiv e-prints, arXiv:2307.03770

(ref: Har24) Harrison, C. M. & Ramos Almeida, C. 2024, Galaxies, 12, 17

(ref: Hic14) Hickox, R. C., Mullaney, J. R., Alexander, D. M., et al. 2014, ApJ, 782, 9

(ref: Hic13) Hicks, E. K. S., Davies, R. I., Maciejewski, W., et al. 2013, ApJ, 768, 107

(ref: Hoe19) Hönig, S. F. 2019, ApJ, 884, 171

(ref: Hoe17) Hönig, S. F. & Kishimoto, M. 2017, ApJL, 838, L20

(ref: Hop10) Hopkins, P. F. & Quataert, E. 2010, MNRAS, 407, 1529

(ref: Hum92) Hummel, E. & Jorsater, S. 1992, A&A, 261, 85

(ref: Hun99) Hunt, L. K. & Malkan, M. A. 1999, ApJ, 516, 660

(ref: Ima18) Imanishi, M., Nakanishi, K., Izumi, T., & Wada, K. 2018, ApJL, 853, L25

(ref: Ima20) Imanishi, M., Nguyen, D. D., Wada, K., et al. 2020, ApJ, 902, 99

(ref: Imp19) Impellizzeri, C. M. V., Gallimore, J. F., Baum, S. A., et al. 2019, ApJL, 884, L28

(ref: Izu16b) Izumi, T., Kawakatu, N., & Kohno, K. 2016, ApJ, 827, 81

(ref: Izu18) Izumi, T., Wada, K., Fukushige, R., Hamamura, S., & Kohno, K. 2018, ApJ, 867, 48

(ref: Izu23) Izumi, T., Wada, K., Imanishi, M., et al. 2023, arXiv e-prints, arXiv:2305.03993

(ref: Kin15) King, A. & Nixon, C. 2015, Monthly Notices of the Royal Astronomical Society, 453, L46

(ref: Kra06) Krajnović, D., Cappellari, M., de Zeeuw, P. T., & Copin, Y. 2006, MNRAS, 366, 787

(ref: Kro88) Krolik, J. H. & Begelman, M. C. 1988, ApJ, 329, 702

(ref: Lar06) Larkin, J., Barczys, M., Krabbe, A., et al. 2006, New A Rev., 50, 362

(ref: Ler21) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43

(ref: Lot04) Lotz, J. M., Primack, J., & Madau, P. 2004, AJ, 128, 163

(ref: Lut20) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134

(ref: Mart04) Martini, P. 2004, in The Interplay Among Black Holes, Stars and ISM in Galactic Nuclei, ed. T. Storchi-Bergmann, L. C. Ho, & H. R. Schmitt, Vol. 222, 235–241

(ref: Mazzalay2013) Mazzalay, X., Saglia, R. P., Erwin, P., et al. 2013, MNRAS, 428, 2389

(ref: McM07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mek22) Meenakshi, M., Mukherjee, D., Wagner, A. Y., et al. 2022, MNRAS, 516, 766

(ref: Mer23) Mercedes-Feliz, J., Anglés-Alcázar, D., Hayward, C. C., et al. 2023, MNRAS, 524, 3446

(ref: Min19) Mingozzi, M., Cresci, G., Venturi, G., et al. 2019, A&A, 622, A146

(ref: Mor13) Morganti, R., Frieswijk, W., Oonk, R. J. B., Oosterloo, T., & Tadhunter, C. 2013, A&A, 552, L4

(ref: Mor15) Morganti, R., Oosterloo, T., Oonk, J. B. R., Frieswijk, W., & Tadhunter, C. 2015, A&A, 580, A1

(ref: Mor05) Morganti, R., Tadhunter, C. N., & Oosterloo, T. A. 2005, A&A, 444, L9

(ref: Muk18a) Mukherjee, D., Bicknell, G. V., Wagner, A. Y., Sutherland, R. S., & Silk, J. 2018a, MNRAS, 479, 5544

(ref: Muk18b) Mukherjee, D., Wagner, A. Y., Bicknell, G. V., et al. 2018b, MNRAS, 476, 80

(ref: FMS2009) Müller Sánchez, F., Davies, R. I., Genzel, R., et al. 2009, ApJ, 691, 749

(ref: FMS2018) Müller-Sánchez, F., Hicks, E. K. S., Malkan, M., et al. 2018, ApJ, 858, 48

(ref: Nowak2010) Nowak, N., Thomas, J., Erwin, P., et al. 2010, MNRAS, 403, 646

(ref: Oni17) Onishi, K., Iguchi, S., Davis, T. A., et al. 2017, MNRAS, 468, 4663

(ref: Pee06) Peeples, M. S. & Martini, P. 2006, ApJ, 652, 1097

(ref: Per23) Peralta de Arriba, L., Alonso-Herrero, A., Garcı́a-Burillo, S., et al. 2023, A&A, 675, A58

(ref: Pill18) Pillepich, A., Springel, V., Nelson, D., et al. 2018, MNRAS, 473, 4077

(ref: Pio22) Piotrowska, J. M., Bluck, A. F. L., Maiolino, R., & Peng, Y. 2022, MNRAS, 512, 1052

(ref: Que16b) Querejeta, M., Schinnerer, E., Garcı́a-Burillo, S., et al. 2016, A&A, 593, A118

(ref: Rcorteam) R Core Team. 2021, R: A Language and Environment for Statistical Computing, R Foundation for Statistical Computing, Vienna, Austria

(ref: Ram22) Ramos Almeida, C., Bischetti, M., Garcı́a-Burillo, S., et al. 2022, A&A, 658, A155

(ref: Ram17) Ramos Almeida, C. & Ricci, C. 2017, Nature Astronomy, 1, 679

(ref: Rao23) Rao, V. V., Kharb, P., Rubinur, K., et al. 2023, MNRAS, 524, 1615

(ref: Ric22) Ricci, C., Ananna, T. T., Temple, M. J., et al. 2022, ApJ, 938, 67

(ref: Ric23a) Ricci, C., Chang, C.-S., Kawamuro, T., et al. 2023a, ApJL, 952, L28

(ref: Ric23b) Ricci, C., Ichikawa, K., Stalevski, M., et al. 2023b, ApJ, 959, 27

(ref: Ric17a) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017a, ApJS, 233, 17

(ref: Ric17b) Ricci, C., Trakhtenbrot, B., Koss, M. J., et al. 2017b, Nature, 549, 488

(ref: Rif14) Riffel, R. A., Vale, T. B., Storchi-Bergmann, T., & McGregor, P. J. 2014, MNRAS, 442, 656

(ref: Ros18) Rosario, D. J., Burtscher, L., Davies, R. I., et al. 2018, MNRAS, 473, 5658

(ref: Ros19) Rosario, D. J., Togi, A., Burtscher, L., et al. 2019, ApJL, 875, L8

(ref: Ruf22) Ruffa, I., Prandoni, I., Davis, T. A., et al. 2022, MNRAS, 510, 4485

(ref: San12) Sánchez, S. F., Kennicutt, R. C., Gil de Paz, A., et al. 2012, A&A, 538, A8

(ref: San13) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Sch15) Schawinski, K., Koss, M., Berney, S., & Sartori, L. F. 2015, Monthly Notices of the Royal Astronomical Society, 451, 2517

(ref: Schaye15) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, MNRAS, 446, 521

(ref: Sch13) Schinnerer, E., Meidt, S. E., Pety, J., et al. 2013, ApJ, 779, 42

(ref: Sco82) Scoville, N. Z., Hall, D. N. B., Ridgway, S. T., & Kleinmann, S. G. 1982, ApJ, 253, 136

(ref: Shi19) Shimizu, T. T., Davies, R. I., Lutz, D., et al. 2019, MNRAS, 490, 5860

(ref: Smajic2015) Smajić, S., Moser, L., Eckart, A., et al. 2015, A&A, 583, A104

(ref: Sto19) Storchi-Bergmann, T. & Schnorr-Müller, A. 2019, Nature Astronomy, 3, 48

(ref: Ten23) Teng, Y.-H., Sandstrom, K. M., Sun, J., et al. 2023, ApJ, 950, 119

(ref: Tob21) Toba, Y., Ueda, Y., Gandhi, P., et al. 2021, ApJ, 912, 91

(ref: Tob19) Toba, Y., Ueda, Y., Matsuoka, K., et al. 2019, MNRAS, 484, 196

(ref: Tor20) Torrey, P., Hopkins, P. F., Faucher-Giguère, C.-A., et al. 2020, MNRAS, 497, 5292

(ref: Tri22) Tristram, K. R. W., Impellizzeri, C. M. V., Zhang, Z.-Y., et al. 2022, A&A, 664, A142

(ref: Uli24) Ulivi, L., Venturi, G., Cresci, G., et al. 2024, arXiv e-prints, arXiv:2403.01258

(ref: Urr95) Urry, C. M. & Padovani, P. 1995, PASP, 107, 803

(ref: Vei20) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2

(ref: Ven20) Venanzi, M., Hönig, S., & Williamson, D. 2020, ApJ, 900, 174

(ref: Ven21) Venturi, G., Cresci, G., Marconi, A., et al. 2021, A&A, 648, A17

(ref: Vit14) Viti, S., Garcı́a-Burillo, S., Fuente, A., et al. 2014, A&A, 570, A28

(ref: Wad94) Wada, K. 1994, PASJ, 46, 165

(ref: Wad12) Wada, K. 2012, ApJ, 758, 66

(ref: Wad15) Wada, K. 2015, ApJ, 812, 82

(ref: Wad16) Wada, K., Schartmann, M., & Meijerink, R. 2016, ApJL, 828, L19

(ref: Wag11) Wagner, A. Y. & Bicknell, G. V. 2011, ApJ, 728, 29

(ref: Wag12) Wagner, A. Y., Bicknell, G. V., & Umemura, M. 2012, ApJ, 757, 136

(ref: Wei17) Weinberger, R., Springel, V., Hernquist, L., et al. 2017, MNRAS, 465, 3291

(ref: Will19) Williamson, D., Hönig, S., & Venanzi, M. 2019, ApJ, 876, 137

(ref: Will20) Williamson, D., Hönig, S., & Venanzi, M. 2020, ApJ, 897, 26

(ref: Yas23) Yasuda, A., Kuno, N., Sorai, K., et al. 2023, PASJ, 75, 743

(ref: Zhu18) Zhuang, M.-Y., Ho, L. C., & Shangguan, J. 2018, ApJ, 862, 118

# Object tables

For more details, readers can refer to Tables [\[Tab1\]](#Tab1) and [\[Tab5\]](#Tab5)

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | $\alpha_{\rm 2000}^{\rm (a)}$ | $\delta_{\rm 2000}^{\rm (a)}$ | D$^{\rm (b)}$ | log$_{\rm 10}$$L_{\rm X}^{\rm 2-10keV~(c)}$ | $\lambda_{\rm Edd}$$^{\rm (d)}$ | Hubble & AGN type$^{\rm (e)}$ | Hubble stage $T^{\rm (e)}$ | $PA^{\rm (f)}$ | $i^{\rm (f)}$ |  |
| —- | $^{\rm h}$ $^{\rm m}$ $^{\rm s}$ | $^{\circ}$ $\ensuremath{'}$ $\ensuremath{''}$ | Mpc | erg s$^{-1}$ | —- | —- | —- | $^{\rm o}$ | $^{\rm o}$ |  |
|  |  |  |  |  |  |  |  |  |  |  |
| NGC1566 | 04:20:00.395 | -54:56:16.60 | 7.2 | 40.50 | -2.89 | (R’$_{1}$)SAB(rs)bc; Sy1.5 | 4.0 | 44 | 49 |  |
| NGC1808 | 05:07:42.329 | -37:30:45.85 | 9.3 | 39.80 | -4.51 | (R’$_{1}$)SAB(s:)b; Sy2 | 1.2 | 146 | 83 |  |
| NGC1672 | 04:45:42.496 | -59:14:49.92 | 11.4 | 39.10 | -6.41 | (R’$_{1}$)SB(r)bc; Sy2 | 3.3 | 155 | 29 |  |
| NGC1068 | 02:42:40.709 | -00:00:47.94 | 14.0 | 42.82 | -0.70 | (R)SA(rs)b; Sy2 | 3.0 | 289 | 41 |  |
| NGC6300 | 17:16:59.543. | -62:49:14.04 | 14.0 | 41.73 | -1.72 | SB(rs)b Sy2 | 3.1 | 95 | 57 |  |
| NGC1326 | 03:23:56.416 | -36:27:52.68 | 14.9 | 39.90 | -4.02 | (R$_1$)SB(rl)0/a; LINER | -0.7 | 71 | 53 |  |
| NGC5643 | 14:32:40.699 | -44:10:27.93 | 16.9 | 42.41 | -1.23 | SAB(rs)c; Sy2 | 5.0 | 301 | 30 |  |
| NGC613 | 01:34:18.189 | -29:25:06.59 | 17.2 | 41.20 | -3.48 | SB(rs)bc; HII Sy | 4.0 | 122 | 36 |  |
| NGC7314 | 22:35:46.201 | -26:03:01.58 | 17.4 | 42.18 | -2.07 | SAB(rs)bc; Sy1.9 | 4.0 | 191 | 55 |  |
| NGC4388 | 12:25:46.781 | +12:39:43.75 | 18.1 | 42.45 | -1.07 | SA(s)b: sp; Sy2 Sy1.9 | 2.8 | 82 | 79 |  |
| NGC1365 | 03:33:36.369 | -36:08:25.50 | 18.3 | 42.09 | -2.15 | (R’)SBb(s)b; HII Sy1.8 | 3.2 | 40 | 41 |  |
| NGC4941 | 13:04:13.103 | -05:33:05.73 | 20.5 | 41.40 | -2.10 | (R)SAB(r)ab:; Sy2 | 2.1 | 212 | 41 |  |
| NGC7213 | 22:09:16.209 | -47:10:00.12 | 22.0 | 41.85 | -3.01 | SA(s)a:; LINER Sy1.5 | 0.9 | 133 | 35 |  |
| NGC7582 | 23:18:23.643 | -42:22:13.54 | 22.5 | 43.49 | -1.70 | (R’$_1$)SB(s)ab; Sy2 | 2.1 | 344 | 59 |  |
| NGC6814 | 19:42:40.587 | -10:19:25.10 | 22.8 | 42.24 | -1.62 | SAB(rs)bc; HII Sy1.5 | 4.0 | 84 | 57 |  |
| NGC3227 | 10:23:30.577 | +19:51:54.28 | 23.0 | 42.37 | -1.20 | SAB(s) pec; Sy1.5 | 1.5 | 152 | 52 |  |
| NGC5506 | 14:13:14.878 | -03:12:27.66 | 26.4 | 42.98 | -1.22 | Sa pec sp ; Sy1.9 | 1.2 | 275 | 80 |  |
| NGC7465 | 23:02:00.961 | +15:57:53.21 | 27.2 | 41.93 | -2.10 | (R’)SB(s)0; Sy2 | -1.8 | 66 | 54.5 |  |
| NGC7172 | 22:02:01.891 | -31:52:10.48 | 37.0 | 42.84 | -1.60 | Sa pec sp; Sy2 HII | 0.6 | 92 | 85 |  |
| NGC5728 | 14:42:23.872 | -17:15:11.01 | 44.5 | 43.19 | -1.72 | (R$_1$)SAB(r)a; HII Sy2 | 1.2 | 15 | 59 |  |
|  |  |  |  |  |  |  |  |  |  |  |
| NGC4826 | 12:56:43.643 | +21:40:59.30 | 4.4 | 37.78 | -6.66 | (R)SA(rs)ab; HII Sy2 | 2.2 | 112 | 60 |  |
| NGC5236 | 13:37:00.94 | -29:51:56.16 | 4.9 | 38.70 | —- | SAB(s)c; HII Sbrst | 5.0 | 225 | 24 |  |
| NGC2903 | 09:32:10.10 | +21:30:02.88 | 10.0 | 38.00 | -6.62 | SAB(rs)bc; HII | 4.0 | 204 | 67 |  |
| NGC3351 | 10:43:57.731 | +11:42:13.35 | 10.0 | 38.03 | -6.75 | SB(r)b; HII Sbrst | 3.1 | 193 | 45 |  |
| NGC1637 | 04:41:28.10 | -02:51:28.80 | 11.7 | 38.04 | —- | SAB(rs)c; AGN | 5.0 | 21 | 31 |  |
| NGC4501 | 12:31:59.220 | 14:25:12.69 | 14.0 | 39.68 | -5.78 | SAb -SA(rs)b; HII Sy2 | 3.3 | 135 | 59 |  |
| NGC4438 | 12:27:45.675 | 13:00:31.18 | 16.5 | 38.72 | -6.35 | SA(s)0/a pec:; LINER | 2.8 | 30 | 60 |  |
| NGC4569 | 12:36:49.80 | +13:09:46.30 | 16.8 | 39.60 | -5.50 | SAB(rs)ab; LINER Sy | 2.4 | 23 | 70 |  |
| NGC4579 | 12:37:43.58 | +11:49:02.49 | 16.8 | 41.42 | -3.82 | SAB(rs)b; LINER Sy1.9 | 2.8 | 95 | 36 |  |
| NGC3718 | 11:32:34.880 | +53:04:04.32 | 17.0 | 40.64 | -4.64 | SB(s)a pec; Sy1 LINER | 1.1 | . 120 | 60 |  |
| NGC3368 | 10: 46:45.50 | 11:49:12.00 | 18.0 | 39.30 | -5.53 | SABab SAB(rs)ab;Sy LINER | 2.1 | 165 | 60 |  |
| NGC2110 | 05:52:11.377 | -07:27:22.48 | 34.8 | 42.67 | -1.87 | SAB0-; Sy2 | -3.0 | 175 | 46 |  |
| NGC2782 | 09:14:05.111 | 40:06:49.24. | 35.0 | 39.50 | -6.10 | SAB(rs)a; Sy1 Sbrst | 1.1 | 75 | 20 |  |
| NGC7172 | 22:02:01.891 | -31:52:10.48 | 37.0 | 42.84 | -1.60 | Sa pec sp; Sy2 HII | 0.6 | 92 | 85 |  |
| MCG-06-30-15 | 13:35:53.770 | -34:17:44.16 | 38.3 | 42.86 | -1.28 | S?; Sy1.2 | 2.0 | 116 | 59 |  |
| NGC2992 | 09:45:41.943 | -14:19:34.57 | 39.2 | 42.20 | -2.29 | Sa pec; Sy1.9 | 0.9 | 29 | 80 |  |
| NGC3081 | 09:59:29.546 | -22:49:34.78 | 40.3 | 43.10 | -1.47 | ( R$_1$)SAB(r)0/a; Sy2 | 0.0 | 71 | 60 |  |
| ESO137-34 | 16:35:13.996 | -58:04:47.77 | 41.5 | 42.80 | -1.99 | SAB(s)0/a? Sy2 | 0.6 | 18 | 41 |  |
| NGC5728 | 14:42:23.872 | -17:15:11.01 | 44.5 | 43.19 | -1.72 | (R$_1$)SAB(r)a; HII Sy2 | 1.2 | 15 | 59 |  |
| ESO21-g004 | 13:32:40.621 | -77:50:40.40 | 45.1 | 42.32 | —- | SA(s)0/a: | 0.20 | 100 | 65 |  |
|  |  |  |  |  |  |  |  |  |  |  |
| M51 | 13:29:52.68 | +47:11:42.72 | 8.6 | 39.00 | -5.25 | SA(s)bc pec; HII Sy2.5 | 4.0 | 173 | 21 |  |
| NGC6300 | 17:16:59.543. | -62:49:14.04 | 14.0 | 41.73 | -1.72 | SB(rs)b Sy2 | 3.1 | 95 | 57 |  |
| NGC4321 | 12:22:54.954 | +15:49:20.49 | 16.8 | 40.40 | -3.80 | SAB(s)bc; LINER HII | 4.0 | 153 | 32 |  |
| NGC5643 | 14:32:40.699 | -44:10:27.93 | 16.9 | 42.41 | -1.23 | SAB(rs)c; Sy2 | 5.0 | 301 | 30 |  |
| NGC7314 | 22:35:46.201 | -26:03:01.58 | 17.4 | 42.18 | -2.07 | SAB(rs)bc; Sy1.9 | 4.0 | 191 | 55 |  |
| NGC4388 | 12:25:46.781 | +12:39:43.75 | 18.1 | 42.45 | -1.07 | SA(s)b: sp; Sy2 Sy1.9 | 2.8 | 82 | 79 |  |
| NGC6221 | 16:52:46.346 | -59:13:01.08 | 22.9 | 41.26 | -2.90 | Sb: pec ; HII LIRG | 3.1 | 1 | 51 |  |
| NGC3227 | 10:23:30.577 | +19:51:54.28 | 23.0 | 42.37 | -1.20 | SAB(s) pec; Sy1.5 | 1.5 | 152 | 52 |  |
| NGC4180 | 12:13:03.072 | +07:02:19.95 | 36.0 | 42.08 | —- | Sab:; Sy LINER | 2.0 | 21 | 80 |  |
| NGC7172 | 22:02:01.891 | -31:52:10.48 | 37.0 | 42.84 | -1.60 | Sa pec sp; Sy2 HII | 0.6 | 92 | 85 |  |
| NGC4593 | 12:39:39.444 | -05:20:39.03 | 41.8 | 43.02 | -0.98 | (R)SB(rs)b Sy1 | 3.0 | 38 | 33 |  |
| NGC1125 | 02:51:40.459 | -16:39:02.34 | 42.6 | 42.65 | -2.15 | (R’)SAB(rl:)0$^+$; Sy2 | 0.0 | 54 | 75 |  |
| NGC5728 | 14:42:23.872 | -17:15:11.01 | 44.5 | 43.19 | -1.72 | (R$_1$)SAB(r)a; HII Sy2 | 1.2 | 15 | 59 |  |
| NGC3281 | 10:31:52.082 | -34:51:13.38 | 52.0 | 43.22 | -2.06 | SAB(rs+)a; Sy2 | 2.4 | 140 | 60 |  |
|  |  |  |  |  |  |  |  |  |  |  |
| NGC5068 | 13:18:54.700 | -21:02:19.32 | 5.2 | —- | —- | SB(s)d | 6.0 | 342 | 36 |  |
| NGC3621 | 11:18:16.296 | \- 32:48:45.36 | 7.1 | —- | —- | SA(s)d; HII | 6.9 | 344 | 66 |  |
| IC5332 | 23:34:27.480 | -36:06:03.9 | 9.0 | —- | —- | SA(s)d | 6.8 | 74 | 27 |  |
| NGC3596 | 11:15:06.100 | +14:47:13.56 | 11.3 | —- | —- | SAB(rs)c; HII | 5.2 | 169 | 15 |  |
| NGC4781 | 12:54:23.800 | -10:32:13.56 | 11.3 | —- | —- | SB(rs)d; HII | 7.0 | 290 | 59 |  |
| NGC2835 | 09:17:52.800 | -22:21:16.92 | 12.2 | —- | —- | SAB(rs)c; HII | 5.0 | 1 | 41 |  |
| NGC5530 | 14:18:27.300 | -43:23:17.88 | 12.3 | —- | —- | SA(rs)bc | 4.2 | 305 | 62 |  |
| NGC1947 | 05:26:47.545 | -63:45:35.82 | 17.2 | —- | —- | S0- pec; LINER | -2.8 | 119 | 29 |  |
| NGC1079 | 02:43:44.337 | -29:00:11.75 | 18.9 | —- | —- | (R)SAB(rs)0/a pec | 0.6 | 90 | 56 |  |
| NGC3717 | 11:31:31.878 | -30:18:27.78 | 19.1 | —- | —- | SAb: sp; HII | 3.1 | 32 | 79 |  |
| NGC7727 | 23:39:53.804 | -12:17:34.18 | 21.0 | —- | —- | SAB(s)a pec | 1.1 | 0 | 26 |  |
| NGC5921 | 15:21:56.487 | +05:04:14.27 | 21 | —- | —- | SB(r)bc; LINER | 4.0 | 140 | 50 |  |
| NGC3175 | 10:14:42.111 | -28:52:19.42 | 21.0 | —- | —- | SAB(s)b; HII | 2.0 | 55 | 76 |  |
| NGC718 | 01:53:13.282 | +04:11:44.93 | 21.4 | —- | —- | SAB(s)a | 1.0 | 150 | 50 |  |
| NGC5845 | 15:06:00.787 | +01:38:01.77 | 27.0 | —- | —- | E | -4.9 | 153 | 50 |  |
| ESO-093-g003 | 10:59:26.062 | -66:19:58.31 | 29.8 | —- | —- | SAB(r)0/a? | 0.3 | 145 | 66 |  |
| NGC5037 | 13:14:59.357 | -16:35:24.99 | 35.0 | —- | —- | SA(s)a | 1.2 | 44 | 74 |  |
| NGC3749 | 11:35:53.192 | -37:59:50.90 | 41.0 | —- | —- | SA(s)a pec sp; HII | 1.1 | 109 | 65 |  |
| NGC4224 | 12:16:33.782 | +07:27:43.54 | 41.0 | —- | —- | SA(s)cd: sp; HII | 6.0 | 56 | 59 |  |
|  |  |  |  |  |  |  |  |  |  |  |

Table notes: $^{\rm (a)}$ Positions of the AGN continuum sources derived from the ALMA and PdBI CO mages taken from the references listed in Sect. [3](#sample). $^{\rm (b)}$ Median value of redshift-independent distances taken from the Nasa Extragalactic Database (NED). $^{\rm (c)}$ Luminosities of hard X-rays in the 2-10 keV range are taken from (cite: Ric17a; Com19; GB21) or redetermined in this work (see Appendix [11](#Lx)); luminosities are intrinsic (corrected for absorption) and re-scaled to the adopted distances. $^{\rm (d)}$ Eddington ratios adopted from (cite: GB21) and references therein, except for NGC 1068 where we used the most recent determination of the BH mass published by (cite: Gal23) and the bolometric AGN luminosity derived by the torus model of (cite: GB14). $^{\rm (e)}$ Hubble classification, stage type $T$-parameter, and AGN classification (when available) are taken from NED. $^{\rm (f)}$ Position and inclination angles used in the deprojection of the images are taken from HyperLEDA or redetermined in this work using the software package `kinemetry` (cite: Kra06) for the galaxies published by (cite: GB21).

|               |        |             |                           |
|:--------------|:-------|:------------|:--------------------------|
| Name          | Filter | Plate Scale | Reference or ESO Prog. ID |
| —-            | —-     | arcsec      | —-                        |
|               |        |             |                           |
| ESO137-34     | H+K    | 0.050       | (cite: Caglar2020)        |
| MCG-05-23-016 | H+K    | 0.050       | (cite: Caglar2020)        |
| MCG-06-30-015 | H+K    | 0.125       | (cite: Caglar2020)        |
| NGC613        | K      | 0.050       | 0102.B-0365 (PI: Erwin)   |
| NGC628        | K      | 0.125       | (cite: Hic13)             |
| NGC1068       | H+K    | 0.050       | (cite: FMS2009)           |
| NGC1326       | K      | 0.125       | (cite: Fazeli2020a)       |
| NGC1365       | H+K    | 0.050       | (cite: Bur15)             |
| NGC1433       | K      | 0.125       | (cite: Smajic2015)        |
| NGC1566       | K      | 0.125       | (cite: Bur15)             |
| NGC1672       | K      | 0.125       | (cite: Fazeli2020b)       |
| NGC1808       | K      | 0.125       | (cite: Busch2017)         |
| NGC2110       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC2992       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC3081       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC3227       | K      | 0.125       | (cite: Davies2007)        |
| NGC3281       | H+K    | 0.050       | (cite: Bur15)             |
| NGC3351       | K      | 0.125       | (cite: Mazzalay2013)      |
| NGC3368       | K      | 0.050       | (cite: Nowak2010)         |
| NGC3783       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC4261       | K      | 0.125       | (cite: Bur15)             |
| NGC4388       | K      | 0.050       | (cite: Bur15)             |
| NGC4435       | K      | 0.050       | (cite: Bur15)             |
| NGC4438       | K      | 0.050       | (cite: Bur15)             |
| NGC4501       | K      | 0.050       | (cite: Bur15)             |
| NGC4569       | K      | 0.050       | (cite: Bur15)             |
| NGC4579       | K      | 0.050       | (cite: Bur15)             |
| NGC4593       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC4826       | K      | 0.125       | 078.B-0289 (PI: Israel)   |
| NGC5236       | K      | 0.050       | 078.B-0505 (PI: Davies)   |
| NGC5506       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC5643       | K      | 0.125       | (cite: Hic13)             |
| NGC5728       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC6300       | K      | 0.125       | (cite: Hic13)             |
| NGC6814       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC7172       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC7213       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC7465       | Kbb    | 0.035       | (cite: FMS2018)           |
| NGC7582       | H+K    | 0.050       | (cite: Caglar2020)        |
|               |        |             |                           |
| IC5332        | K      | 0.125       | 095.B-0660 (PI: Georgiev) |
| NGC718        | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC1079       | H+K    | 0.125       | 0102.B-0365 (PI: Erwin)   |
| NGC3175       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC3621       | K      | 0.050       | 60.A-9800                 |
| NGC5845       | H+K    | 0.050       | (cite: Caglar2020)        |
| NGC7727       | H+K    | 0.050       | (cite: Caglar2020)        |

# Estimate of $L_{\rm X}$ for a fraction of the lower luminosity sample galaxies

In order to complete the X-ray luminosities for the sources in our sample, we checked in the *XMM*-Newton and *Chandra* archives for observations when the objects were not included in the BASS sample. We found *XMM*-Newton observations for five objects (namely NGC 3718, NGC 4321, NGC 4569, NGC 4579 and NGC 6951) and *Chandra* for six sources (namely NGC 2782, NGC 3718, NGC 4321, NGC 4569, NGC 4579, and NGC 5953). Four targets have been observed with both satellites. Unfortunately, after processing the data, the observations of NGC 5953 and NGC 6951 resulted in less than 5 ksec that were not enough to obtain a spectrum for these two sources. Only one *XMM*-Newton observations was available for each of the targets. Among *Chandra* observations, we chose the one with the longest exposure time when more than one observation is available. Table [\[Tab4\]](#Tab4) contains the information of the five sources with available spectra together with the spectral fitting results.

*Chandra* and *XMM*-Newton observations were processed using the standard pipelines CIAO and SAS, respectively. We extracted the nuclear spectrum, coincident with the coordinates of the targets using a 0.5 and 20 arcsec radial aperture, respectively. A background region was manually selected in a source-free region close to the target extraction. We grouped the spectra with a minimum of 20 counts per bin using the command line grppha within `Heasoft` software. We then used the latest version of the `XSPEC` software to perform spectral fitting.

Our simplest model accounts for partial observed intrinsic emission. This in the nomenclature of the software is written as *pcfabs $\times$ powerlaw* (M1 in Table [\[Tab4\]](#Tab4)). Clear contribution from extended host diffuse emission is found for most of the targets when using *XMM*-Newton observations due to the poorer spatial resolution compared to *Chandra*. To account for this emission, we added a thermal component to the model when needed. This new baseline model is written in the nomenclature of the software as *apec + pcfabs $\times$ powerlaw* (M2 in Table [\[Tab4\]](#Tab4)). In two sources (NGC 2782 and NGC 4579), we found clear signatures of the $\rm{FeK\alpha}$ emission line. In these two case we added to M2, a reflection component to account for this line. This final baseline model is written in the software nomenclature of the software as *pexmon + apec + pcfabs $\times$ powerlaw* (M3 in Table [\[Tab4\]](#Tab4)). When both satellites are available, we link all the parameters between observations except for the normalizations of the intrinsic continuum (to allow plausible changes in flux). No significative variations are found in our analysis. The photon index was poorly constrained in three sources. In these cases, we fixed it to the standard value of $\rm{\Gamma = 1.8}$. Although some objects do show a complex behavior that might require additional components, this analysis is good enough to reproduce the data in order to obtain the X-ray observation corrected luminosity used in this work.

The existence of the $\rm{FeK\alpha}$ line and/or the reflection component confirm the AGN nature except for NGC 4321 and NGC 4569, where the luminosity and spectral shape could be consistent with a stellar nature. Indeed, NGC 4321 was classified as non-AGN by (cite: Gon09). Therefore, the AGN nature of these two sources is still uncertain.

|  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | OBSID | Exptime | Model | log$_{\rm 10}(L_{\rm X})$ | kT(keV) | $\rm{\Gamma}$ | $N_{\rm H}$ | $f_{\rm cov}$ | $\rm{\chi / dof}$ |
| NGC2782 | 3014 | 29.58 | M3 | ${39.5_{0.5}^{0.3}}$ | ${1.02\rm0.05}$ | 1.8$^{*}$ | $\rm{3.6_{-3.5}^{+6.6}}$ | $\rm{0.8\pm0.2}$ | 13.6/19 |
| NGC3718 | 0795730101/3993 | 16.14/0.5 | M1 | ${40.64\pm 0.01}$/${40.84\pm 0.01}$ |  | $\rm{1.7\pm0.1}$ | $\rm{0.90\pm0.05}$ | $\rm{0.98\pm0.01}$ | 182.0/200 |
| NGC4321 | 0106860201/14230 | 1.0/78.8 | M2 | ${40.4\pm 0.2}$/${39.2_{-0.2}^{+0.7}}$ | ${0.65_{-0.03}^{+0.09}}$ | 1.8$^{*}$ | $\rm{76_{-38}^{+113}}$ | $\rm{0.6\pm0.2}$ | 107.1/86 |
| NGC4569 | 0200650101/5911 | 40.0/29.9 | M2 | ${39.64\pm 0.06}$/${39.22\pm 0.07}$ | ${0.76\rm0.01}$ | 1.8$^{*}$ | $\rm{16.8\pm0.5}$ | $\rm{0.4\pm0.1}$ | 221.3/152 |
| NGC4579 | 0790840201/807 | 17.1/31.4 | M3 | ${41.42\pm 0.01}$/${41.29\pm 0.01}$ | ${0.84\rm0.06}$ | $\rm{1.76\pm0.01}$ | $\rm{1.20\pm0.05}$ | $\rm{0.68\pm0.01}$ | 1081.0/994 |
|  |  |  |  |  |  |  |  |  |  |

Table notes: Table of the results for the X-ray spectral fitting. $N_{\rm H}$ are in units of $\rm{10^{22}cm^{-2}}$. M1: *pcfabs $\times$ powerlaw*, M2: *apec + pcfabs $\times$ powerlaw*, M3: *apec + pexmon + pcfabs$\times$ powerlaw*.

# Molecular gas surface densities and concentration indices

We list in Table [\[Tab2\]](#Tab2) the cold and hot molecular gas surface densities and concentration indices ($CCI$ and $HCI$) obtained for the galaxies of the sample used in this paper.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | D | log$_{10}$$\Sigma^{\rm gas}_{50}$ | log$_{10}$$\Sigma^{\rm gas}_{200}$ | $CCI$ | log$_{10}$$\Sigma^{\rm hot}_{50}$ | log$_{10}$$\Sigma^{\rm hot}_{200}$ | $HCI$ |
| —- | Mpc | M$_{\ensuremath{\odot}}$pc$^{-2}$ | M$_{\ensuremath{\odot}}$pc$^{-2}$ | —- | M$_{\ensuremath{\odot}}$pc$^{-2}$ | M$_{\ensuremath{\odot}}$pc$^{-2}$ | —- |
|  |  |  |  |  |  |  |  |
| NGC1566 | 7.2 | 2.58 | 1.89 | 0.69 | -3.10 | -3.54 | 0.44 |
| NGC1808 | 9.3 | 2.68 | 2.20 | 0.48 | -2.83 | -3.23 | 0.40 |
| NGC1672 | 11.4 | 3.16 | 2.22 | 0.83 | -2.65 | -3.20 | 0.55 |
| NGC1068 | 14.0 | 2.69 | 2.94 | -0.25 | -1.41 | -1.61 | 0.20 |
| NGC6300 | 14.0 | 3.09 | 2.42 | 0.68 | -3.19 | -3.93 | 0.74 |
| NGC1326 | 14.9 | 2.51 | 1.77 | 0.74 | -2.79 | -3.47 | 0.68 |
| NGC5643 | 16.9 | 3.17 | 2.61 | 0.56 | -2.54 | -3.38 | 0.85 |
| NGC613 | 17.2 | 3.22 | 2.51 | 0.82 | -1.81 | -2.65 | 0.85 |
| NGC7314 | 17.4 | 2.22 | 1.53 | 0.69 | — | — | — |
| NGC4388 | 18.1 | 1.97 | 2.13 | -0.17 | -2.47 | -2.64 | 0.17 |
| NGC1365 | 18.3 | 2.22 | 1.52 | 0.70 | -4.91 | -4.18 | -0.73 |
| NGC4941 | 20.5 | 2.21 | 1.42 | 0.79 | — | — | — |
| NGC7213 | 22.0 | \<1.18 | 0.63 | \<0.55 | -2.98 | -3.87 | 0.89 |
| NGC7582 | 22.5 | 2.77 | 2.93 | -0.16 | -3.35 | -3.53 | 0.18 |
| NGC6814 | 22.8 | 1.66 | 0.96 | 0.70 | -2.35 | -3.21 | 0.86 |
| NGC3227 | 23.0 | 2.88 | 2.74 | 0.14 | -2.60 | -3.11 | 0.50 |
| NGC5506 | 26.4 | 2.42 | 2.34 | 0.07 | -2.03 | -2.47 | 0.43 |
| NGC7465 | 27.2 | 2.65 | 2.07 | 0.57 | -2.28 | -2.78 | 0.50 |
| NGC7172 | 37.0 | 1.81 | 1.97 | -0.16 | -5.53 | -5.68 | 0.15 |
| NGC5728 | 44.5 | 2.65 | 2.55 | 0.10 | -4.86 | -5.31 | 0.45 |
|  |  |  |  |  |  |  |  |
| NGC4826 | 4.4 | 2.67 | 2.28 | 0.39 | -2.92 | -3.19 | 0.27 |
| NGC5236 | 4.9 | 2.87 | 2.62 | 0.25 | — | — | — |
| NGC2903 | 10.0 | 2.40 | 2.31 | 0.09 | — | — | — |
| NGC3351 | 10.0 | 2.52 | 2.21 | 0.32 | -3.31 | -3.77 | 0.46 |
| NGC1637 | 11.7 | 2.68 | 2.20 | 0.48 | — | — | — |
| NGC4569 | 16.8 | 2.41 | 2.31 | 0.10 | -2.90 | -2.84 | -0.06 |
| NGC4579 | 16.8 | 1.76 | 1.45 | 0.32 | -1.89 | -2.62 | 0.73 |
| NGC3718 | 17.0 | 1.26 | 0.80 | 0.46 | — | — | — |
| NGC2110 | 34.8 | \<1.39 | 1.41 | \<-0.02 | -5.09 | -5.32 | 0.23 |
| NGC2782 | 35.0 | 2.77 | 2.34 | 0.42 | — | — | — |
| NGC7172 | 37.0 | 2.07 | 2.16 | -0.08 | -5.53 | -5.68 | 0.15 |
| MCG-06-30-15 | 38.3 | 2.27 | 2.05 | 0.22 | -3.33 | -3.38 | 0.05 |
| NGC2992 | 39.2 | 1.70 | 1.99 | -0.30 | -5.73 | -5.79 | 0.06 |
| NGC3081 | 40.3 | 2.03 | 1.88 | 0.14 | -5.84 | -5.75 | -0.09 |
| ESO137-34 | 41.5 | 2.42 | 2.21 | 0.21 | -2.21 | -2.45 | 0.24 |
| NGC5728 | 44.5 | 2.68 | 2.64 | 0.04 | -4.86 | -5.31 | 0.45 |
| ESO21-g004 | 45.1 | 1.70 | 1.57 | 0.13 | — | — | — |
| NGC4826 | 4.4 | 2.71 | 2.23 | 0.47 | -2.92 | -3.19 | 0.27 |
| NGC3351 | 10.0 | 2.50 | 1.91 | 0.55 | -3.31 | -3.57 | 0.46 |
| NGC4501 | 14.0 | 2.73 | 2.36 | 0.37 | -2.88 | -3.09 | 0.21 |
| NGC4438 | 16.5 | 2.75 | 2.49 | 0.25 | -1.87 | -2.38 | 0.51 |
| NGC3368 | 18.0 | 2.93 | 2.67 | 0.25 | -2.48 | -2.94 | 0.46 |
| NGC7172 | 37.0 | 2.10 | 2.16 | -0.06 | -5.53 | -5.68 | 0.15 |
|  |  |  |  |  |  |  |  |
| M51 | 8.6 | 2.84 | 2.18 | 0.66 | — | — | — |
| NGC6300 | 14.0 | 3.48 | 2.64 | 0.84 | -3.19 | -3.93 | 0.74 |
| NGC4321 | 16.8 | 3.35 | 2.91 | 0.44 | — | — | — |
| NGC5643 | 16.9 | 2.75 | 2.38 | 0.37 | -2.54 | -3.38 | 0.85 |
| NGC7314 | 17.4 | 2.86 | 2.31 | 0.55 | — | — | — |
| NGC4388 | 18.1 | 2.31 | 2.43 | -0.12 | -2.47 | -2.64 | 0.17 |
| NGC6221 | 22.9 | 3.33 | 3.03 | 0.30 | — | — | — |
| NGC3227 | 23.0 | \< 2.33 | 2.49 | \<-0.15 | -2.60 | -3.11 | 0.50 |
| NGC4180 | 36.0 | 3.22 | 2.79 | 0.43 | — | — | — |
| NGC7172 | 37.0 | 2.69 | 2.72 | -0.04 | -5.53 | -5.68 | 0.15 |
| NGC4593 | 41.8 | 2.78 | 2.65 | 0.14 | -4.85 | -5.65 | 0.80 |
| NGC1125 | 42.6 | \< 2.79 | 2.60 | \<0.19 | — | — | — |
| NGC5728 | 44.5 | 2.99 | 3.05 | -0.06 | -4.86 | -5.31 | 0.45 |
| NGC3281 | 52.0 | 3.00 | 2.89 | 0.10 | -2.29 | -2.38 | 0.09 |
|  |  |  |  |  |  |  |  |
| NGC5068 | 5.2 | 0.75 | 0.29 | 0.46 | — | — | — |
| NGC3621 | 7.1 | 0.68 | 0.54 | 0.14 | — | — | — |
| IC5332 | 9.0 | 0.25 | -0.01 | 0.25 | — | — | — |
| NGC3596 | 11.3 | 1.67 | 1.58 | 0.09 | — | — | — |
| NGC4781 | 11.3 | 1.38 | 1.11 | 0.27 | — | — | — |
| NGC2835 | 12.2 | 1.24 | 0.99 | 0.25 | — | — | — |
| NGC5530 | 12.3 | 1.54 | 1.13 | 0.41 | — | — | — |
| NGC1947 | 17.2 | 3.46 | 2.70 | 0.76 | — | — | — |
| NGC1079 | 18.9 | 2.12 | 1.63 | 0.48 | — | — | — |
| NGC3717 | 19.1 | 2.88 | 2.49 | 0.39 | — | — | — |
| NGC7727 | 21.0 | 2.36 | 2.02 | 0.34 | -2.97 | -3.45 | 0.48 |
| NGC5921 | 21.0 | 2.73 | 2.26 | 0.47 | — | — | — |
| NGC3175 | 21.0 | 2.67 | 2.50 | 0.17 | -3.30 | -3.55 | 0.25 |
| NGC718 | 21.4 | 2.18 | 1.78 | 0.41 | -2.98 | -3.77 | 0.79 |
| NGC5845 | 27.0 | 1.73 | 1.01 | 0.62 | — | — | — |
| ESO-093-g003 | 29.8 | 1.97 | 1.99 | -0.02 | — | — | — |
| NGC5037 | 35.0 | 2.59 | 2.34 | 0.25 | — | — | — |
| NGC3749 | 41.0 | 2.84 | 2.63 | 0.20 | — | — | — |
| NGC4224 | 41.0 | 1.86 | 1.70 | 0.16 | — | — | — |
|  |  |  |  |  |  |  |  |

Table notes: Columns (3) and (4) list the surface densities of the cold molecular derived from different CO lines on the nuclear ($r\leq50$ pc; $\Sigma^{\rm gas}_{50}$) and circumnuclear ($r\leq200$ pc; $\Sigma^{\rm gas}_{200}$) disk scales of the AGN and non-AGN galaxies of the sample. The target names and their distances are listed in columns (1) and (2). The concentration indices of cold molecular gas ($CCI$) are listed in column (5). Columns (6), (7) and (8) list the corresponding surface densities and concentration indices ($\Sigma^{\rm hot}_{50}$, $\Sigma^{\rm hot}_{200}$, and $HCI$) derived for the hot molecular gas component.

# Other trends of the cold molecular gas concentration index

Fig. [17](#conc-CO-bis) shows the trend with $L_{\rm X}$ of an alternative definition of the concentration of cold molecular gas, which adopts the region defined by the outer corona of the CND ($50$ pc$\leq r \leq 200$ pc) to normalize the molecular surface density of the nuclear region (r$\leq50$ pc).

![image](conc-median-corona-Lx-samples.pdf) ![image](conc-corona-Lx-samples-MARS.pdf)

Fig. [18](#Edd_ratio) shows the $CCI$ values as a function of the Eddington ratio for the 27 galaxies in our sample for which an estimate of $\lambda_{\rm Edd}$ is available.

![](conc-Edd-samples.pdf)

# CND-scale distribution of molecular gas from different CO line transitions

![](maps-ngc7172.pdf)

![](maps-ngc5728.pdf)

Figures [19](#maps-ngc7172) and [20](#maps-ngc5728) show the images of the CND of the AGN feedback branch targets NGC 7172 and NGC 5728 obtained in the 3–2, 2–1, and 1–0 transitions of CO. In spite of the different spatial resolutions used in these observations, the derived 2D distributions, normalized radial profiles, and $CCI$ values show a weak dependence on the CO transition used to image the distribution of molecular gas in these sources.

[^1]: With the exception of one elliptical galaxy classified as non-AGN, NGC 5845, our sample only includes disk galaxies; the median value of the Hubble stage T parameter for our sample is 2.2, which corresponds to a Sab spiral galaxy type; see Table [\[Tab1\]](#Tab1).

[^2]: We do not expect to find a direct evolutionary link that could connect ETG to spiral (disk) galaxies, as argued in Sect. [8](#discussion), therefore, we have only included in our combined sample the WISDOM sources that are not classified as ETG.

[^3]: We assume common values of $R_{\rm ij}$ and $\alpha_{\rm CO}$ for the two spatial scales used in this work: $R_{\rm 31}$=2.9 and $R_{\rm 21}$=2.5 measured by (cite: Vit14) in NGC 1068, and a Milky-Way value of $\alpha_{\rm CO}=2\times10^{20}$mol cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: Bol13).

[^4]: The binning used along the $L_{\rm X}$ axis is designed to have a similar number of 8-9 independent CO data sets per luminosity bin.

[^5]: The binning used along the $L_{\rm X}$ axis is chosen to have a similar number of 6-8 independent NIR data sets per luminosity bin.

[^6]: The binning used along the $L_{\rm X}$ axis is chosen to have a 7 independent data sets per luminosity bin.

</paper>

Write the methods card for this paper.