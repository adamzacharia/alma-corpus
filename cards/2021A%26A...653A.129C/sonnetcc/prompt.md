# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...653A.129C\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2021A&A...653A.129C",
 "title": "The GUAPOS project. II. A comprehensive study of peptide-like bond molecules",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Colzi, L.",
 "n_authors": 15,
 "arxiv_id": "2107.11258",
 "doi": "10.1051/0004-6361/202141573",
 "alma_projects_linked_by_archive": [
  "2013.1.00489.S",
  "2017.1.00501.S"
 ]
}
```

Paper text:
<paper>
# The GUAPOS project\
II. A comprehensive study of peptide-like bond molecules

Peptide-like molecules, which can take part to the formation of proteins in a primitive Earth environment, have been detected up to now only towards a few hot cores and hot corinos. We present a study of HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, CH$_{3}$NHCHO, CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$towards the hot core G31.41+0.31. The aim of this work is to study these species together to allow a consistent study among them. We have used the spectrum obtained from the ALMA 3mm spectral survey GUAPOS, with a spectral resolution of $\sim$0.488 MHz ($\sim$1.3–1.7 km s$^{-1}$) and an angular resolution of 1.2$''$$\times$1.2$''$ ($\sim$4500 au), to derive column densities of all the molecular species presented in this work, together with 0.2$''$$\times$0.2$''$ ($\sim$750 au) ALMA observations from another project to study the morphology of HNCO, HC(O)NH$_{2}$and CH$_{3}$C(O)NH$_{2}$. We have detected HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHO, but no CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$. This is the first time that these molecules have been detected all together outside the Galactic center. We have obtained molecular fractional abundances with respect to H$_{2}$ from 10$^{-7}$ down to a few 10$^{-9}$ and abundances with respect to CH$_{3}$OH from 10$^{-3}$ to $\sim$4$\times$10$^{-2}$, and their emission is found to be compact ($\sim$2$^{\prime\prime}$, i.e. $\sim$7500 au). From the comparison with other sources, we find that regions in an earlier stage of evolution, such as pre-stellar cores, show abundances at least two orders of magnitude lower than those in hot cores, hot corinos or shocked regions. Moreover, molecular abundance ratios towards different sources are found to be consistent between them within $\sim$1 order of magnitude, regardless of the physical properties (e.g. different masses and luminosities), or the source position throughout the Galaxy. Correlations have also been found between HNCOand HC(O)NH$_{2}$, and CH$_{3}$NCOand HNCOabundances, and for the first time between CH$_{3}$NCOand HC(O)NH$_{2}$, CH$_{3}$C(O)NH$_{2}$and HNCO, and CH$_{3}$C(O)NH$_{2}$and HC(O)NH$_{2}$abundances. These results suggest that all these species are formed on grain surfaces in early evolutionary stages of molecular clouds, and that they are subsequently released back to the gas-phase through thermal desorption or shock-triggered desorption.

# Introduction

![](fig-molecules-new.pdf)

The study of the origin of life on Earth is one of the main challenges among biologists, chemists, geologists, and, in recent years, also astrophysicists. In fact, the advent of more sensitive and higher spatial and spectral resolution astronomical instruments, like the Atacama Large Millimeter Array (ALMA), allowed the detection of $\sim$240 molecular species in the interstellar medium (ISM), about 100 of which are complex organic molecules (COMs), i.e. molecules containing carbon with 6 or more atoms ((cite: mcguire2018)). In particular, COMs have been detected ubiquitously in the ISM towards high-mass and low-mass star-forming regions (e.g. (cite: hollis2004); (cite: beltran2009); (cite: belloche2013); (cite: jorgensen2012)), protostellar molecular outflows (e.g. (cite: arce2008); (cite: codella2020)), photon-dominated regions (e.g. (cite: guzman2013); (cite: cuadrado2017)), dark clouds cores and pre-stellar cores (e.g. (cite: marcelino2007); (cite: bacmann2012); (cite: jimenez-serra2016)), and Galactic Center (GC) molecular clouds (e.g. (cite: requena-torres2006); (cite: zeng2018); (cite: rivilla2019); (cite: jimenez-serra2020); (cite: rivilla2021)).

Among prebiotic COMs, those containing peptide-like bonds (NCO backbone) are of great interest because they can participate in the link of amino acids forming proteins (e.g. (cite: pascal2005)). Peptide-like bond molecules detected to date in the ISM are isocyanic acid (HNCO), formamide (HC(O)NH$_{2}$), methyl isocyanate (CH$_{3}$NCO), acetamide (CH$_{3}$C(O)NH$_{2}$) and its isomer N-methylformamide (CH$_{3}$NHCHO), and urea (NH$_{2}$C(O)NH$_{2}$). Unlike these species, ethyl isocyanate (CH$_{3}$CH$_{2}$NCO), cyanoformamide (NH$_{2}$C(O)CN), and glycolamide (HOCH$_{2}$C(O)NH$_{2}$), which also contain the peptide-like bond, have never been detected in the ISM. (cite: kolesnikova2018) report the rotational spectrum of CH$_{3}$CH$_{2}$NCOfrom 80 to 340 GHz, and searched for it towards the Orion KL and Sgr B2 hot molecular cores (HMCs) without success. (cite: sanz-novo2020) provided experimental frequencies of the rotational lines in the ground vibrational state of HOCH$_{2}$C(O)NH$_{2}$and searched for it towards SgrB2(N) also without success. Finally, NH$_{2}$C(O)CNsearches in the ISM have never been reported. Isocyanic acid, HNCO, was detected towards HMCs, low-mass protostars, translucent molecular clouds, molecular outflows, and extragalactic regions (e.g. (cite: snyder1972); (cite: turner1999); (cite: helmich1997); (cite: bisschop2007); (cite: zeng2018); (cite: rodriguez-fernandez2010); (cite: nguyen-q-rieu1991); (cite: nazari2021); (cite: canelo2021)). Formamide, HC(O)NH$_{2}$, has been also detected towards many different high- and low-mass star-forming regions (e.g. (cite: lopez-sepulcre2019)). Methyl isocyanate, CH$_{3}$NCO  was detected towards Sgr B2(N), Orion KL, the low-mass protostars IRAS 16293-2422 A and B, the high-mass protostellar object G328.2551-0.5321, the G10.47+0.03 and G31.41+0.31 HMCs, and the Serpens SMM1 hot corino ((cite: halfen2015); (cite: cernicharo2016); (cite: martin-domenech2017); (cite: ligterink2017); (cite: ligterink2018); (cite: manigand2020); (cite: csengeri2019); (cite: gorai2020; gorai2021); (cite: ligterink2021)). Acetamide, CH$_{3}$C(O)NH$_{2}$, was detected towards different high-mass star-forming regions ((cite: hollis2006); (cite: halfen2011); (cite: cernicharo2016); (cite: belloche2017); (cite: ligterink2020)) and tentatively detected towards IRAS 16293-2422 B ((cite: ligterink2018)). Moreover, the second most stable C$_{2}$H$_{5}$NO isomer after CH$_{3}$C(O)NH$_{2}$, N-methylformamide, CH$_{3}$NHCHO((cite: lattelais2010)), was detected towards Sgr B2(N1S) and NGC 6334I and tentatively detected towards Sgr B2(N2) ((cite: belloche2017); (cite: belloche2019), (cite: ligterink2020)). Recently, urea, NH$_{2}$C(O)NH$_{2}$, has been detected towards Sgr B2(N1) and the GC molecular cloud G+0.693-0.027 ((cite: belloche2019), (cite: jimenez-serra2020)), and tentatively detected towards NGC 7538 IRS9, Sgr B2(N-LMH), and NGC 6334I ((cite: raunier2004); (cite: remijan2014); (cite: ligterink2020)).

These peptide-like bond species have preferentially been detected so far in massive and clustered star-forming regions. In this sense it is worth noting that our Sun is thought to have been formed in a clustered environment in the presence of massive stars (e.g (cite: adams2010); (cite: lichtenberg2019); (cite: wallner2020); (cite: korschinek2020)). Therefore, the study of the chemical reservoir of the birth environment of massive stars, known as HMCs, can give us important hints about the chemical heritage that our own Solar System received from its natal environment.

For all of these species, different chemical formation and destruction pathways, both on grain surfaces and in gas-phase, have been proposed (e.g. (cite: agarwal1985); (cite: grim1989); (cite: garrod2008); (cite: jones2011); (cite: noble2015); (cite: fedoseev2016); (cite: belloche2017); (cite: quenard2018)). However, chemical networks still need important new inputs from observations in different astronomical environments to be properly constrained.

In this paper we study molecules with one or more peptide-like bond (see Fig. [1](#fig-molecules)) towards the HMC G31.41+0.31 (hereafter G31) in the context of the G31 Unbiased ALMA sPectral Observational Survey (GUAPOS, (cite: mininni2020)). All these molecules are reported for the first time in this paper towards G31, with the exceptions of HC(O)NH$_{2}$, recently detected by (cite: coletta2020) using single-dish data, and CH$_{3}$NCO, recently reported by (cite: gorai2021). G31 is a HMC located at a distance of 3.75 kpc ((cite: immer2019)), with a luminosity of $\sim$4.5$\times$10$^{4}$ L$_{\odot}$ (from (cite: osorio2009)) and a mass of $\sim$70 M$_{\odot}$ ((cite: cesaroni2019)). The core harbours two free-free continuum sources separated by $\sim$0.2$''$ ((cite: cesaroni2010)), and new VLA and ALMA observations show that there are at least 4 massive star-forming regions in the core ((cite: beltran2021)). Moreover, few molecular lines present an inverse P-Cygni profile, indicating that the core is collapsing and rotating with respect to the direction of a magnetic field, revealed by polarization measurements ((cite: girart2009); (cite: beltran2019)). G31 is an excellent source to search for complex molecules since it presents a very rich chemistry, as already shown by previous works (e.g. (cite: beltran2005); (cite: beltran2009); (cite: rivilla2017); (cite: beltran2018); (cite: mininni2020), (cite: gorai2021)). This is the second paper from this survey, after the first one which presented the GUAPOS project and the analysis of the three energetically most stable C$_{2}$H$_{4}$O$_{2}$ isomers ((cite: mininni2020)).

In Sect. [2](#observations) and [3](#results) we present the observations and the results, respectively. In Sect. [4](#discussion) we provide a detailed comparison with previous observations towards other sources and a discussion of the main formation and destruction reactions proposed for these species, giving new inputs for future chemical models. Finally, the conclusions are summarised in Sect. [5](#conclusions).

# Observations and data analysis

## ALMA data

Observations towards the HMC G31 were taken with ALMA during Cycle 5 (project 2017.1.00501.S, P.I.: M. T. Beltrán) obtaining an unbiased spectral survey in Band 3, from 84.05 GHz up to 115.91 GHz. The frequency resolution is 0.49 MHz, corresponding to a velocity resolution of $\sim$1.6 km s$^{-1}$ at 90 GHz. The final angular resolution is $\sim$1.2$''$ ($\sim$4500 au). The root mean square (rms) noise of the maps varies between 0.5 mJy beam$^{-1}$ and 1.9 mJy beam$^{-1}$. The pointing center of the observations is $\alpha_{\rm J2000}$ = 18$^{\rm h}$47$^{\rm m}$34$^{\rm s}$ and $\delta_{\rm J2000}$ = -0.1$^{\prime}$45$^{\prime\prime}$. The uncertainty on the flux calibration is of $\sim$5%. For more details see (cite: mininni2020).

In this work, as in (cite: mininni2020), we have analysed a spectrum extracted inside an area equal to the beam size towards the continuum peak position ($\alpha_{\rm J2000}$ = 18$^{\rm h}$47$^{\rm m}$34$^{\rm s}$.321 and $\delta_{\rm J2000}$ = $-$0.1$^{\prime}$45.977$''$). The rms noise of the spectrum varies from 7 mK to 27 mK. The spectrum of G31 is very line rich, which prevents to subtract the continuum by simply using line-free channels. Thus, we have applied the corrected sigma clipping method (c-SMC) approach of the Python-based tool STATCONT[^1] ((cite: sanchez-monge2018)) to subtract the continuum. A detailed discussion of the results of this method is presented in Appendix [6](#cont-sub). The error associated with the final Band 3 spectrum is of $\pm$1.2 K, which corresponds to the 11% of the continuum level at a reference frequency of 84.579 GHz. This error is included as an additional error on the parameters derived from the fit to the spectrum.

## Additional high-angular resolution data

Interferometric observations of G31 at higher angular resolution were carried out with ALMA in Cycle 2 in July and September 2015 as part of project 2013.1.00489.S. (P.I.: R. Cesaroni). The observations were carried out in Band 6 with the array in an extended configuration. The digital correlator was configured in thirteen spectral windows (SPW), one broad window for the continuum and twelve narrow ones for the lines, covering different bandwidths from $\sim$217 GHz to $\sim$236.5 GHz. The phase reference center of the observations is $\alpha_{\rm J2000}$= 18$^{\rm h}$47$^{\rm m}$34$^{\rm s}$.315, $\delta_{\rm J2000}$ = -01$^\prime$45.90$''$. The resulting synthesized cleaned beam of the maps is 0.2$''$$\times$0.2$''$ ($\sim$750 au) for the lines analysed in this work. The rms noise of the maps is $\sim$1.3 mJy beam$^{-1}$ at $\sim$217 GHz and 218 GHz, $\sim$1.5 mJy beam$^{-1}$ at $\sim$219 GHz, and $\sim$2 mJy beam$^{-1}$ at $\sim$220 GHz. We refer to (cite: cesaroni2017) and (cite: beltran2018) for detailed information on the observations.

## Spectral analysis

The line identification of the molecular species present in the GUAPOS spectrum has been done using the version 01/12/2020 of the SLIM (Spectral Line Identification and Modeling) tool within the MADCUBA package[^2] ((cite: martin2019)). SLIM uses the spectroscopic entries from the Cologne Database for Molecular Spectroscopy[^3] (CDMS, (cite: muller2001; muller2005); (cite: endres2016)), the Jet Propulsion Laboratory[^4] (JPL, (cite: pickett1998)), and for species whose spectroscopy was not present in the catalogues we have added entries using available spectroscopic works. Then, SLIM generates a synthetic spectrum, assuming local thermodynamic equilibrium (LTE) conditions and taking into account the line opacity. In this study, we focused the analysis on the molecules containing one or more peptide-like bonds (NCO backbone) HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, CH$_{3}$NHCHO, CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$(Fig. [1](#fig-molecules)). Details on the spectroscopic entries used for these species can be found in Appendix [7](#spectroscopy). Beside the analysis of the peptide-like bond molecules, a preliminary identification of other molecular species has been done to evaluate the effect of possible line contaminations (e.g. thin red line of Fig. [2](#fig-res-ia)). For each molecular species we used the MADCUBA-AUTOFIT tool to compare the observed spectrum with the LTE synthetic one. This fitting tool provides the best non-linear least-squared fit to all the transitions taken into account by using the Levenberg-Marquardt algorithm. The free parameters of the fitting are the column density of the molecule, $N$, the excitation temperature, $T_{\rm ex}$, the peak velocity, $\varv_{\rm LSR}$, and the full-width-half-maximum (FWHM), $\Delta \varv$. As described by (cite: mininni2020), the LTE assumption is well justified because of the high volume density $n$(H$_{2}$) $\sim$ 10$^{8}$ cm$^{-3}$. Since the emission of the HMC fills the beam (i.e. the region from which we have extracted the spectrum, see Sect. [3.2](#integrated-maps) and (cite: mininni2020)), we did not consider beam-dilution in the fitting procedure. Moreover, since we have also considered the possible contamination from other molecular species, we have limited the fit to non-contaminated or slightly contaminated transitions. In particular, we have considered (i) non-contamination from a line of another species if its peak is at a distance larger than FWHM from the peak of the considered line, and ii) in case of blending with peak separation $<$FWHM, the contamination of the line of the other species should be $<$ 15%. Thus, the parameters above are left free to obtain the best-LTE fit whenever the algorithm reaches the convergence. If convergence cannot be reached, FWHM, $\varv_{\rm LSR}$, and/or $T_{\rm ex}$ have been fixed as explained in Sect. [3.1](#sect-result-fit). When the algorithm converges, it also provides the errors on the parameters. The transitions used for the fit of each molecule are listed in Table [1](#transitions). When the spectroscopic information of vibrationally excited states is present, the total partition function used for the fit ($Q_{\rm vibrot}$) has been derived taking into account the contribution of both the rotational partition function, $Q_{\rm rot}$, and the vibrational one, $Q_{\rm vib}$, $Q_{\rm vibrot}$=$Q_{\rm rot} \times Q_{\rm vib}$ (see Appendix [7](#spectroscopy)). The final relative error on the total column densities has been derived as the square root of the quadratic sum of the relative error given by the fit algorithm and the error on the continuum level (11%, see Sect. [2.1](#observation-data)). Finally, the molecular abundances ($X$) were derived using the column density of H$_{2}$, obtained from the continuum emission inside the area from which we extracted the spectrum, $N_{\rm H_{2}}$ = (1.0$\pm$0.2)$\times$10$^{25}$ cm$^{-2}$ (see (cite: mininni2020)).

The analysis of the different vibrational states has been done separately for HNCO, HC(O)NH$_{2}$, and CH$_{3}$NCO, because of the difficulty to fit all of the transitions of a molecule with a single $T_{\rm ex}$. In fact, it is well know that the HMC G31 has a temperature gradient, with temperatures of $\sim$100 K towards the outer part (at $\sim$0.03 pc from the center), and of $\sim$450 K towards its center ((cite: beltran2018)). Moreover, as we discuss in Sects. [3.1.1](#res-ia), [3.1.2](#res-fm) and [3.1.3](#res-mi), the ground vibrational states of these molecules are optically thicker than the vibrationally excited ones. Thus, we only discuss the results obtained from the $^{13}$C-isotopologues, or from the vibrationally excited states if the $^{13}$C-isotopologues have not been detected. Conversely, the resulting fit for CH$_{3}$C(O)NH$_{2}$was obtained taking into account the $v$=0, and $v_{\rm t}$=1, 2 transitions all together, because we find that they all are optically thin. For CH$_{3}$NHCHO, only the ground vibrational state transitions have been detected and analysed, and upper limits will be provided for its excited states transitions. Finally, CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$have not been detected, and only upper limits of the ground vibrational state will be provided.

# Results

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
|  | FWHM | $\varv_{\rm LSR}$ | $T_{\rm ex}$ | $N$ | $X$ |
|  | (km s$^{-1}$) | (km s$^{-1}$) | \(K\) | ($\times$10$^{16}$ cm$^{-2}$) | ($\times$10$^{-9}$) |
| HNCO, $v$=0 | 8 | 97$\pm$17 | 217$\pm$22 | 11.5$\pm$1.8 | 11$\pm$3 |
| HNCO, $v_{4}$=1 | 8 | 97 | 217 | 63$\pm$8$^{a}$ | 63$\pm$15$^{a}$ |
| HNCO, $v_{5}$=1 | 8 | 97 | 217 | 79$\pm$17$^{a}$ | 79$\pm$23$^{a}$ |
| HNCO, $v_{6}$=1 | 8 | 97 | 217 | $\le$95$^{d}$ | $\le$95 |
| HN$^{13}$CO, $v$=0 | 8 | 97 | 217 | 3.8$\pm$0.5 | 3.8$\pm$0.9 |
| HNCO$^{b}$ |  |  |  | 141$\pm$49$^{c}$ | 141$\pm$57$^{c}$ |
| H$^{15}$NCO, $v$=0 | 8 | 97 | 217 | 0.49$\pm$0.09 $^{a}$ | 0.49$\pm$0.13$^{a}$ |
| HC(O)NH$_{2}$, $v$=0 | 8.6$\pm$0.2 | 97$\pm$13 | 150$\pm$26 | 5.4$\pm$1.1 | 5.4$\pm$1.5 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 8.4$\pm$0.2 | 97 | 245$\pm$88 | 15$\pm$2 | 15$\pm$4 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 8.6 | 97 | 150 | 0.47$\pm$0.07 | 0.47$\pm$0.11 |
| HC(O)NH$_{2}$$^{b}$ |  |  |  | 17$\pm$6$^{c}$ | 17$\pm$7$^{c}$ |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 7.15$\pm$0.15 | 97$\pm$11 | 122$\pm$7 | 4.3$\pm$0.6 | 4.3$\pm$1.0 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 7.15 | 97 | 91$\pm$37 | 12$\pm$3$^{c}$ | 12$\pm$4$^{c}$ |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 7.15 | 97 | 122 | 0.49$\pm$0.09$^{a}$ | 0.49$\pm$0.13$^{a}$ |
| CH$_{3}$N$^{13}$CO, $v_{\rm b}$=0 | 7.15 | 97 | 122 | $\l\le$0.63$^{d}$ | $<$0.63 |
| CH$_{3}$NCO$^{b}$ |  |  |  | 18$\pm$7 | 18$\pm$9 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0, $v_{\rm t}$=1, 2 | 6.2$\pm$0.4 | 96.7 | 285$\pm$50 | 8$\pm$4$^{c}$ | 8$\pm$4$^{c}$ |
| CH$_{3}$NHCHO, $v$=0 | 7 | 96.5 | 285 | 3.7$\pm$1.6$^{c}$ | 3.7$\pm$1.7$^{c}$ |
| CH$_{3}$NHCHO, $v_{\rm t}$=1 | 7 | 96.5 | 285 | $\le$2.3$^{d}$ | $\le$2.3 |
| CH$_{3}$NHCHO, $v_{\rm t}$=2 | 7 | 96.5 | 285 | $\le$2.1$^{d}$ | $\le$2.1 |
| CH$_{3}$CH$_{2}$NCO, $v$=0 | 7.15 | 97 | 91 | $\le$0.5$^{d}$ | $\le$0.5 |
| NH$_{2}$C(O)NH$_{2}$$v$=0 | 7 | 96.5 | 150 | $\le$0.016$^{d}$ | $\le$0.016 |
| NH$_{2}$C(O)CN, $v$=0 | 7 | 96.5 | 150 | $\le$0.3$^{d}$ | $\le$0.3 |
| HOCH$_{2}$C(O)NH$_{2}$, $v$=0 | 7 | 96.5 | 150 | $\le$0.07$^{d}$ | $\le$0.07 |
|  |  |  |  |  |  |

Table notes: $N$ is the average column density inside the beam of 1.2$''$; $X$ is the abundance inside a beam calculated as $N$/$N_{\rm H_{2}}$, where $N_{\rm H_{2}}$ = (1.0$\pm$0.2)$\times$10$^{25}$ cm$^{-2}$. Parameters without errors are fixed in the fitting procedure, as explained in Sect. [2.3](#analysis).\
.

In this section we show the results obtained from the line fitting procedure performed with MADCUBA-SLIM for the nine species (Sects. [3.1.1](#res-ia)–[3.1.6](#res-ei) and Appendix [9](#figure-tentative)). The non-contaminated transitions used to fit the molecular lines are listed in Table [1](#transitions). Moreover, we present the integrated emission maps of the molecular species obtained from the GUAPOS survey ($\sim$1.2$''$), and higher angular resolution observations ($\sim$0.2$''$) for HNCO, HC(O)NH$_{2}$, and CH$_{3}$NCO(Sect. [3.2](#integrated-maps)). The results from the fitting procedure are listed in Table [\[table-fitresult-v0\]](#table-fitresult-v0), and the total spectrum with the fit to all of the molecules studied in this paper is given in Appendix [10](#spectra). This is the first time that HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHOhave been detected together towards G31 and outside the GC, after the detections in Sgr B2(N2) ((cite: belloche2017)).

## LTE fits

### Isocyanic acid (HNCO)

![](GUAPOSIAusedfinal.eps)

The HNCO and HN$^{13}$CO molecules have a similar center of mass and for this reason the frequencies of their rotational transitions are very close ($\sim$1.8 MHz of difference). Thus, since the typical line width towards G31 is of $\sim$6–8 km s$^{-1}$ ($\sim$2.0–2.6 MHz at 100 GHz, see e.g. (cite: mininni2020)) the lines of the two species appear blended. We have performed the fit of both species simultaneously (magenta and green curves in Fig. [2](#fig-res-ia)) using MADCUBA, considering also the contribution from other species already identified in the GUAPOS survey (thin red line in Fig. [2](#fig-res-ia)).

To perform the final fit of HNCO and HN$^{13}$CO we have fixed the FWHM to 8 km s$^{-1}$, which best reproduce the observed line profiles (Fig. [2](#fig-res-ia)). The best fit of HNCO provided $T_{\rm ex}$ = 217$\pm$22 K, $N$ = (1.15$\pm$0.18)$\times$10$^{17}$ cm$^{-2}$, and molecular abundance with respect to H$_{2}$, $X$ = (1.1$\pm$0.3)$\times$10$^{-8}$. To derive the best fit for HN$^{13}$CO we fixed $T_{\rm ex}$ to the same estimated value for HNCO because the fit did not converge leaving it free, and we have obtained $N$ = (3.8$\pm$0.5)$\times$10$^{16}$ cm$^{-2}$, and $X$ = (3.8$\pm$0.9)$\times$10$^{-9}$.

Moreover, we have also tentatively detected the vibrationally excited states $v_{4}$=1 and $v_{5}$=1, while an upper limit to the $v_{6}$=1 state is given. MADCUBA derives the upper limits to the integrated intensity using the formula 3$\times$rms$\times\Delta$v/$\sqrt{n_{\rm chan}}$, where rms is the root-mean-square measured over a line-free spectral range, and $n_{\rm chan}$ is the number of channels covered by the FWHM, $\Delta \varv$. As shown in Figs. [21](#fig-res-ia-va) and [22](#fig-res-ia-vb), only five and three rotational transitions of the $v_{4}$=1 and $v_{5}$=1 states, respectively, have been tentatively detected, since they are partially contaminated with other molecules. The main contaminants of the $v_{4}$=1 transitions are HNCO, $v_{5}$=1 at 110.086 GHz, CH$_{3}$COCH$_{3}$ at 110.089 GHz, HCOOC$_{2}$H$_{5}$ at 110.417 GHz and 110.103 GHz, CH$_{2}$DOH at 110.105 GHz, and CH$_{3}$CHO at 106.792 GHz. The main contaminant of the $v_{5}$=1 transitions is ethylene glycol at 87.739 GHz. To perform the final fit we have fixed FWHM, $T_{\rm ex}$, and $\varv_{\rm LSR}$ as those of the ground state of HNCO (Table [\[table-fitresult-v0\]](#table-fitresult-v0)). The best fit gave as output $N$ = (6.3$\pm$0.8)$\times$10$^{17}$ cm$^{-2}$, and $X$ = (6.3$\pm$1.5)$\times$10$^{-8}$ for $v_{4}$=1, and $N$ = (7.9$\pm$1.7)$\times$10$^{17}$ cm$^{-2}$, and $X$ = (7.9$\pm$2.3)$\times$10$^{-8}$ for $v_{5}$=1. Moreover, for $v_{6}$=1 we have derived a rough estimate of the upper limit of the column density using MADCUBA-SLIM given the difficulty of obtaining a precise result due to the blending with lines of other species. Thus, we have assumed $T_{\rm ex}$, $\varv_{\rm LSR}$, and FWHM derived for HNCO$v_{\rm b}$=0, and have increased $N$ to the maximum value compatible with the observed spectrum. We have obtained $N$ $\le$ 9.5$\times$10$^{17}$ cm$^{-2}$ and an abundance $X$ $\le$ 9.5 $\times$10$^{-8}$. We have also found hints of possible emission of three transitions of H$^{15}$NCO, at 106.224, 106.578, and 106.614 GHz, respectively (Fig. [23](#fig-ia-15N)). The transition at 106.224 GHz is partially contaminated by n-C$_{3}$H$_{7}$CN, $v$=0 (20% of contamination). Moreover, the transition at 106.614 GHz seems to be contaminated by a non-identified line. Taking into account these transitions, and fixing all the parameters as those estimated for HNCO, we have derived a tentative $N$ = (4.9$\pm$0.9)$\times$10$^{15}$ cm$^{-2}$, and $X$ = (4.9$\pm$1.3)$\times$10$^{-10}$.

From the results of the fit we have derived a $^{12}$C/$^{13}$Cratio of 3.0$\pm$0.6 and a $^{14}$N/$^{15}$Nratio of 23$\pm$6 using HNCO, $v$=0. The low $^{12}$C/$^{13}$Cis probably due to the line opacity, $\tau$, of the optically thick main isotopologue. In fact, from the fit of HN$^{13}$CO we obtain values of $\tau$ as high as 0.04, while the $\tau$ obtained for HNCO, $v$=0 are one order of magnitude higher (see Table [1](#transitions)). Moreover, this is also confirmed by the low $^{14}$N/$^{15}$Nratio (23) measured. This is by far the lowest ratio ever estimated towards massive star-forming regions, for which typical values range between 200 and 1000 (e.g., (cite: colzi18b)), and it is even lower that the values measured in the pristine material of meteorites (see e.g. (cite: bonal2009)).

Since HNCO is optically thick, we have derived the column density using the optically thinner $^{13}$C-isotopologue (see Table [1](#transitions)), correcting it by the $^{12}$C/$^{13}$Cratio derived following the galactocentric trend recently obtained by (cite: yan2019). At the galactocentric distance of G31, $D_{\rm GC}$=5.02 kpc, the $^{12}$C/$^{13}$Cratio is 37$\pm$12. Thus, the corrected column density is $N$ = (1.4$\pm$0.5)$\times$10$^{18}$ cm$^{-2}$, and the corrected abundance is $X$=(1.4$\pm$0.6)$\times$10$^{-7}$. If we simulate the spectrum of the transitions in Fig. [2](#fig-res-ia) of HNCO, $v$=0 with this corrected column density, the derived line opacities are in the range 1.3–3.4 confirming that HNCO, $v$=0 is optically thick. This column density and abundance will be used for the discussion presented in Sect. [4](#discussion) and are consistent with those derived from the tentatively detected vibrationally excited state $v_{5}$=1. Moreover, the \[HN$^{13}$CO/H$^{15}$NCO\]$\times$37 value derived, 287$\pm$66, is consistent with the Galactic $^{14}$N/$^{15}$Nvalue of 340$\pm$90 derived from the linear relation found by (cite: colzi18b), which suggests that both isotopologues are reasonably optically thin.

### Formamide (HC(O)NH$_{2}$)

![](GUAPOSFMusedfinal.eps)

![](GUAPOS13FMusedfinal.eps)

![](GUAPOSFM-v1-usedfinal.eps)

Figures [3](#fig-res-fm) and [4](#fig-res-13fm) show the non-contaminated transitions used to fit HC(O)NH$_{2}$and H$^{13}$C(O)NH$_{2}$, while Fig. [5](#fig-res-fm-v1) shows the non-contaminated transitions of the vibrationally excited state $v_{12}$=1. The best-fit parameters obtained with MADCUBA for the ground state are $T_{\rm ex}$ = 150$\pm$26 K, FWHM = 8.6$\pm$0.2 km s$^{-1}$, $N$ = (5.4$\pm$1.1)$\times$10$^{16}$ cm$^{-2}$, and $X$ = (5.4$\pm$1.5)$\times$10$^{-9}$ (Table [\[table-fitresult-v0\]](#table-fitresult-v0)). For its $^{13}$C-isotopologue, H$^{13}$C(O)NH$_{2}$, we have fixed the FWHM, the $T_{\rm ex}$, and the $\varv_{\rm LSR}$ as those estimated for HC(O)NH$_{2}$and found $N$ = (4.7$\pm$0.7)$\times$10$^{15}$ cm$^{-2}$ and $X$ = (4.7$\pm$1.1)$\times$10$^{-10}$.

From the fit results we have derived a $^{12}$C/$^{13}$Cratio of 12$\pm$3. As in the case of HNCO, this low $^{12}$C/$^{13}$Cratio is probably affected by opacity effects. As already done for HNCO, we discuss the column density and abundance of HC(O)NH$_{2}$assuming the $^{12}$C/$^{13}$Cratio from the galactocentric distance dependence and deriving the values from those of the $^{13}$C-isotopologue. Thus, the corrected column density is $N$ = (1.7$\pm$0.6)$\times$10$^{17}$ cm$^{-2}$, and the corrected abundance is $X$ = (1.7$\pm$0.7)$\times$10$^{-8}$. These values will be used for the discussion presented in Sect. [4](#discussion).

The best-fit parameters obtained with MADCUBA for the $v_{\rm 12}$=1 state are $T_{\rm ex}$ = 245$\pm$88 K (consistent within the error with that obtained for $v$=0), FWHM = 8.4$\pm$0.2 km s$^{-1}$, $N$ = (1.5$\pm$0.2)$\times$10$^{17}$ cm$^{-2}$, and $X$ = (1.5$\pm$0.4)$\times$10$^{-8}$. Note that the column density and the abundance derived from the $^{13}$C-isotopologue multiplied by the $^{12}$C/$^{13}$Cratio, are consistent, within the errors, with those derived separately from the HC(O)NH$_{2}$$v_{\rm 12}$=1 state (see Table [\[table-fitresult-v0\]](#table-fitresult-v0)). This result is also consistent with what was found for HNCO, HN$^{13}$CO and the tentatively detected vibrationally excited states. It should be noted that if we fix $T_{\rm ex}$ of H$^{13}$C(O)NH$_{2}$ to that obtained for the HC(O)NH$_{2}$$v_{\rm 12}$=1 state (245 K), we obtain $N$ = (9.1$\pm$1.4)$\times$10$^{15}$ cm$^{-2}$. Thus, the $N$ corrected for the $^{12}$C/$^{13}$Cratio would be $N$ = (3.4$\pm$1.2)$\times$10$^{17}$ cm$^{-2}$, a factor of two higher with respect to the result obtained for the $v_{\rm 12}$=1 state of the main species, but consistent within the errors.

Since we have found that rotational transitions of the vibrationally excited state are optically thin, this could be an indication that the $v$=0 state is affected by opacity effects, and that the assumed $^{12}$C/$^{13}$Cratio to obtain the final results is a good approximation. In fact, if we simulate the spectrum of the transitions in Fig. [3](#fig-res-fm) of HC(O)NH$_{2}$, $v$=0 with the column density derived from the $^{13}$C-isotopologue ($N$=1.7$\times$10$^{17}$ cm$^{-2}$), the derived line opacities are in the range 0.3–1.1.

### Methyl isocyanate (CH$_{3}$NCO)

![](GUAPOSCH3NCOusedfinal-1.eps)

![](GUAPOSCH3NCOusedfinal-2.eps)

![](GUAPOSMI-v1-usedfinal.eps)

Figure [6](#fig-res-mi-1) shows the non-contaminated transitions used to fit the ground vibrational state of CH$_{3}$NCO. The best-fit parameters obtained with MADCUBA are $T_{\rm ex}$ = 122$\pm$7 K, FWHM = 7.15$\pm$0.15 km s$^{-1}$, $N$ = (4.3$\pm$0.6)$\times$10$^{16}$ cm$^{-2}$, and $X$ = (4.3$\pm$1.0)$\times$10$^{-9}$.

Figure [8](#fig-res-mi-v1) shows the non-contaminated transitions for the vibrationally excited state $v_{\rm b}$=1. The best fit has been obtained fixing the same FWHM as the ground state, and resulted in $T_{\rm ex}$ = 91$\pm$37 K, $N$ = (1.2$\pm$0.3)$\times$10$^{17}$ cm$^{-2}$, and $X$ = (1.2$\pm$0.4)$\times$10$^{-8}$.

One $^{13}$C-isotopologue, $^{13}$CH$_{3}$NCO, is tentatively detected because most of the transitions are contaminated or partially blended with those of other molecular species. Figure [24](#fig-mi-13C) shows the less contaminated transitions of $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0. In particular, the main contaminants are $^{33}$SO$_{2}$ at 93.070 GHz, 93.071 GHz, and 93.073 GHz, CH$_{3}$NHCHOat 93.406 GHz, CH$_{3}$C(O)NH$_{2}$ at 93.459 GHz, CH$_{3}$OCHO at 93.457 GHz, CH$_{3}$COOH at 100.203 GHz, and 100.942 GHz, CH$_{3}$CHO at 101.892 GHz, and CH$_{3}$O$^{13}$CHO at 108.576 GHz. Moreover, at 108.406 GHz the baseline derived from STATCONT is slightly high, and the simulated spectra do not match exactly the observed one. However, the peak of the simulated transition is of $\sim$1 K and it is consistent with the error on the derived baseline (see Sect. [6](#cont-sub)). To perform the final fit we have fixed the FWHM, the $T_{\rm ex}$, and the $\varv_{\rm LSR}$ as those of the ground state of CH$_{3}$NCO(Sect. [3.1.3](#res-mi)). The best fit gave as $N$ = (4.9$\pm$0.9)$\times$10$^{15}$ cm$^{-2}$ and $X$ = (4.9$\pm$1.3)$\times$10$^{-10}$. Conversely, CH$_{3}$N$^{13}$CO was not detected and only an upper limit, consistent with what is obtained for $^{13}$CH$_{3}$NCO, can be provided for the column density and abundance (Table [\[table-fitresult-v0\]](#table-fitresult-v0)). As with HNCO, $v_{6}$=1, it was not possible to directly derive the upper limit of the CH$_{3}$N$^{13}$CO column density due to the blending with other species, and we roughly estimated the column density by assuming the same $T_{\rm ex}$, $\varv_{\rm LSR}$, and FWHM of the ground state of CH$_{3}$NCO.

For this molecular species, the ground vibrational state has $\tau$ up to 0.12, while the $v_{\rm b}$=1 is optically thin ($\tau\le$0.05). Moreover, from the tentative detection of $^{13}$CH$_{3}$NCO, and correcting for the same $^{12}$C/$^{13}$Cused above, we obtain $N$ = (1.8$\pm$0.7)$\times$10$^{17}$ cm$^{-2}$, and $X$ = (1.8$\pm$0.8)$\times$10$^{-8}$, consistent with the results obtained for the $v_{\rm b}$=1 state, as already found for HNCO and HC(O)NH$_{2}$. If we simulate the spectrum of the transitions in Fig. [6](#fig-res-mi-1) of CH$_{3}$NCO, $v_{\rm b}$=0 with the column density obtained from the $v_{\rm b}$=1 states, the derived line opacities are up to 0.4 confirming that CH$_{3}$NCO, $v_{\rm b}$=0 is partially optically thick. Thus, we discuss the results obtained for CH$_{3}$NCOtaking into account the best fit of the vibrationally excited state (Sect. [4](#discussion)).

CH$_{3}$NCOis the molecule that presents the lowest $T_{\rm ex}$ with respect to the other species studied in this work (Table [\[table-fitresult-v0\]](#table-fitresult-v0)). First of all, the $T_{\rm ex}$ found for the ground vibrational state could be affected by the opacity of these rotational transitions. Secondly, the transitions of the $v_{\rm b}$=1 state, from which we take the final result, present a very small range of $E_{\rm up}$ (from 285 K up 350 K). This means that the $T_{\rm ex}$ could not be well constrained. However, even considering a higher $T_{\rm ex}$ of 300 K, the derived $N$ varies only by a factor of 1.2, consistent within the errors with the $N$ derived leaving $T_{\rm ex}$ free.

### Acetamide (CH$_{3}$C(O)NH$_{2}$)

![](GUAPOSAM-allusedfinal-1.eps)

Figure [9](#fig-res-am1) shows the non-contaminated or slightly contaminated transitions used to fit CH$_{3}$C(O)NH$_{2}$. This is the first time that CH$_{3}$C(O)NH$_{2}$is detected towards this source. In this case, both the ground vibrational state and the excited ones ($v_{\rm t}$=1, 2) are optically thin ($\tau <$0.01), and the range of upper energies of the levels is similar for the three vibrational states ($E_{\rm up}$ from $\sim$50 up to 250 K, see Table [1](#transitions)). Moreover, since all the vibrational levels are optically thin, we have been able to fit them simultaneously with a single LTE fit. The best-fit parameters obtained with MADCUBA are $T_{\rm ex}$ = 285$\pm$50 K, FWHM = 6.2$\pm$0.4 km s$^{-1}$, $N$ = (8$\pm$4)$\times$10$^{16}$ cm$^{-2}$, and $X$ = (8$\pm$4)$\times$10$^{-9}$.

### N-methylformamide (CH$_{3}$NHCHO)

![](GUAPOSNMusedfinal.eps)

Figure [10](#fig-res-nm) shows the non-contaminated and slightly contaminated transitions used to fit the ground vibrational state of CH$_{3}$NHCHO. Only the transition at 102.434 GHz is slightly contaminated ($\sim$50% of contamination) with ethylene glycol at the same frequency. This is the first time that CH$_{3}$NHCHOis detected towards this source.

To fit this molecule we have fixed $T_{\rm ex}$ to 285 K (same value as for its isomer CH$_{3}$C(O)NH$_{2}$), $\varv_{\rm LSR}$ to 96.5 km s$^{-1}$, and FWHM to 7 km s$^{-1}$, because the fit did not converge leaving them free. The best fit of the column density obtained with MADCUBA gives $N$ = (3.7$\pm$1.6)$\times$10$^{16}$ cm$^{-2}$, and $X$ = (3.7$\pm$1.7)$\times$10$^{-9}$. In this case, the vibrationally excited states were not detected and upper limits to their column densities and abundances are provided (Table [\[table-fitresult-v0\]](#table-fitresult-v0)). In particular, the column density upper limits have been derived like for HNCO $v_{6}$=1, assuming the same $T_{\rm ex}$, $\varv_{\rm LSR}$, and FWHM of CH$_{3}$C(O)NH$_{2}$, and increasing $N$ until the observed spectrum could be reproduced. The derived upper limits are consistent with the column density found for the ground state, within the errors.

### Non detections

Unlike for the other species, no unblended transitions of CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$were found. Thus, we have derived upper limits for the column densities of the ground vibrational state. All of the transitions of these molecules are contaminated with those of other species, making it difficult to derive upper limits for the column densities. Thus, for CH$_{3}$CH$_{2}$NCOwe have assumed $T_{\rm ex}$, $\varv_{\rm LSR}$, and FWHM derived for CH$_{3}$NCO$v_{\rm b}$=1 (since the ground state is optically thick, see Sect. [3.1.3](#res-mi)), and have increased $N$ to the maximum value compatible with the observed spectrum. We have obtained $N\le$5$\times$10$^{15}$ cm$^{-2}$, and a molecular abundance $X\le$5$\times$10$^{-10}$. This gives a CH$_{3}$NCO/CH$_{3}$CH$_{2}$NCOratio $>$24, which is consistent with the CH$_{3}$NCO/CH$_{3}$CH$_{2}$NCOratio $>$10 found towards the HMCs Orion KL and Sgr B2 by (cite: kolesnikova2018). Moreover, for NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$we have assumed $T_{\rm ex}$ = 150 K, $\varv_{\rm LSR}$=96.5 km s$^{-1}$, and FWHM = 7 km s$^{-1}$. Also in this case we have increased $N$ to the maximum value compatible with the observed spectrum, and found $N\le$1.6$\times$10$^{14}$ cm$^{-2}$ for NH$_{2}$C(O)NH$_{2}$, $N\le$3$\times$10$^{15}$ cm$^{-2}$ for NH$_{2}$C(O)CN, and $N\le$7$\times$10$^{14}$ cm$^{-2}$ for HOCH$_{2}$C(O)NH$_{2}$.

## Integrated intensity maps

![](mappe_all_energies_label.pdf)

![](comparison_fluxes-0.5.eps)

![](comparison_molecules-0.5.eps)

![](map-highres.pdf)

Figure [11](#fig-maps-allenergies) shows the 1.2$''$ resolution integrated intensity maps of the 3mm GUAPOS survey of the most unblended transitions of HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHO, with different values of the upper energy level ($E_{\rm up}$). The velocity range used for the integrated intensity maps goes from 93 to 100 km s$^{-1}$. CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$are not included in the figure because they were not detected, as explained in Sect. [3.1.6](#res-ei). The transitions of HNCO overlap with those of HN$^{13}$CO, and therefore both species contribute to the integrated emission maps.

These integrated intensity maps have been obtained from the final cubes after the calibration carried out with the CASA[^5] (Common Astronomy Software Applications) package ((cite: mcmullin2007)). In particular, for each transitions we have cropped the cube to frequencies $\pm$20 MHz around the rest frequency. Then, in the GUAPOS spectrum we have identified the channels in which the line intensity is zero and we have used these spectral windows to subtract the continuum pixel by pixel. Finally, we obtained the integrated intensity maps from the four channels around the rest frequencies. In fact, taking into account the spectral resolution of $\sim$0.48 MHz, the width of four channels at $\sim$90 GHz corresponds to 6.5 km s$^{-1}$, comparable to the FWHM of the molecular lines in this source. All these operations were made with the MADCUBA software.

The emission of the molecular species studied here arises entirely from the HMC, and comes from a region of $\sim$2$^{\prime\prime}$($\sim$ 7500 au, see Fig. [11](#fig-maps-allenergies)). Moreover, the derivation of column densities from transitions at different energies is reasonable when their emission comes from the same region. Thus, we have compared the emission of the different molecules and of different range of energies for the transitions studied in this work. Figure [12](#fig-comparison-fluxes) shows the comparison between the emitting region of different upper energy levels of the same molecule taken from maps of Fig. [11](#fig-maps-allenergies). Moreover, Fig. [13](#fig-comparison-molecules) shows the comparison among transitions with similar upper energy levels of different molecular species. From these figures it is clear that the emission of different transitions arises from the same region regardless of the molecule and of the upper energy level. Furthermore, we found a similar result when comparing different molecules. Only N-methylformamide (CH$_{3}$NHCHO) presents some shifts that are not significant since they are smaller than the beam size of 1.2$''$. Thus, we can conclude that the column densities derived from transitions at different upper energy levels and the ratios derived between molecules are not affected by a different spatial distribution of different transitions or molecules.

Note, however, that this similar spatial distribution could be in part due to the fact that the emission is only partially resolved at an angular resolution of 1.2$''$. Therefore, to test this and eventually unveil spatial differences unresolved at 1.2$''$ resolution, we have also analysed higher angular resolution (0.2$''$) data at 1.4 mm obtained with ALMA. Figure [14](#fig-maps-high-res) shows the integrated emission maps of the ground vibrational state $J_{K_{\rm a},K_{\rm c}}$ = 10$_{1,9}$–9$_{1,8}$ rotational transition of HC(O)NH$_{2}$, of the ground vibrational state $J_{K_{\rm a},K_{\rm c}}$ = 10$_{3,8}$–9$_{3,7}$, 10$_{3,7}$–9$_{3,6}$[^6], and 10$_{1,9}$–9$_{1,8}$ rotational transitions of HNCO, and of the ground vibrational state $J_{K_{\rm a},K_{\rm c},m}$ = 25$_{2,23,0}$–24$_{2,22,0}$ and the $J_{K,m}$ = 25$_{-3,1}$–24$_{-3,1}$ rotational transitions of CH$_{3}$NCO. The map of the latter molecule was obtained by combining two transitions because they emit at similar frequencies and have a similar upper energy level of about 160-200 K. Note that the $E_{\rm up}$ chosen for each of these transitions was comparable to that used for the analysis and the results of the 1.2$''$ resolution data. Moreover, we have also selected a higher $E_{\rm up}$ transition of HNCO (432 K) to show possible spatial differences. In this case, despite the different $E_{\rm up}$ of the two HNCO levels (101 K and 432 K), both transitions fill the beam of the GUAPOS observations (bottom panels of Fig. [14](#fig-maps-high-res)).

We did not find strong and unblended transitions of CH$_{3}$C(O)NH$_{2}$and CH$_{3}$NHCHOin the narrow spectral bands of the high-angular resolution observations at 1.4 mm. Thus, these two molecules will not be discussed in the following of this section.

The 0.2$''$ resolution integrated intensity maps show that the overall behaviour at 1.4 mm of these molecules (HNCO, HC(O)NH$_{2}$, and CH$_{3}$NCO) is quite similar. One of the main differences is that the maps at higher $E_{\rm up}$ (159-201 K, and 432 K, of CH$_{3}$NCOand HNCO, respectively) present a more compact structure than the lower energy ones (61 and 101 K, of HC(O)NH$_{2}$and HNCO, respectively). This is expected because of the temperature gradient present towards the HMC, with higher temperatures to the center with respect to the outer part as already discussed in Sect. [2.3](#analysis). A striking feature of the integrated emission at high angular resolution is its ring-like morphology. This spatial distribution is similar to that traced by other COMs, such as CH$_{3}$CN and CH$_{3}$OCHO, observed with the same angular resolution of 0.2$''$ ((cite: beltran2018)). The explanation for this morphology is that most of the emission comes from a rotating and infalling toroid surrounding a small protocluster of 4 massive protostars (indicated as black squares and named A, B, C, and D in Fig. [14](#fig-maps-high-res), see also (cite: beltran2021)). Since the material is flowing inwards and locally the continuum temperature is higher than the $T_{\rm ex}$ of the molecules, the gas is seen in red-shifted absorption towards the center (see (cite: beltran2018) for more details), and the integrated emission shows this characteristic ring structure.

The high-angular resolution maps at 1.4 mm show that the molecular emission arise from the whole HMC, filling the 1.2$''$ beam of GUAPOS (black dashed line in Fig. [14](#fig-maps-high-res)). The column densities obtained from a region of 1.2$''$ in the high-angular resolution maps are consistent to those derived from the GUAPOS data. In fact, if we fix $T_{\rm ex}$, $\varv_{\rm LSR}$ and FWHM to the values derived at 3 mm (Table [\[table-fitresult-v0\]](#table-fitresult-v0)), the column densities of the three molecules obtained at 1.4 mm are consistent within a factor of 2 with those obtained at 3 mm. In particular, from 1.4 mm observations, $N$(HC(O)NH$_{2}$)=(2.5$\pm$1.9)$\times$10$^{16}$ cm$^{-2}$, $N$(HNCO)=(1.12$\pm$0.04)$\times$10$^{17}$ cm$^{-2}$, $N$(HNCO)=(9.1$\pm$1.8)$\times$10$^{16}$ cm$^{-2}$, from the transitions at 219.656 and 219.656 GHz, respectively, and $N$(CH$_{3}$NCO)=(6.9$\pm$1.8)$\times$10$^{16}$ cm$^{-2}$. This mean that both observations (at 1.4 and 3 mm), despite of the different angular resolution, are sensitive to approximately the same gas.

# Discussion

To obtain a complete overview of the chemical processes that lead to the formation of peptide-like bond molecules in the ISM, we have compared the results obtained in G31 with those in other interstellar sources. Comparisons have been made with works containing at least the detection of HC(O)NH$_{2}$together with that of CH$_{3}$NCOand/or CH$_{3}$C(O)NH$_{2}$. These sources are the HMCs in the GC Sgr B2(N) ((cite: belloche2013)), Sgr B2(N2) ((cite: belloche2017)), Sgr B2(N1S) ((cite: belloche2019)), Sgr B2(N3) and Sgr B2(N5) ((cite: bonfand2019)), the HMCs in the Galactic disk G10.47+0.03 (hereafter G10.47), Orion BN/KL A and B, and NGC 6334I ((cite: gorai2020); (cite: cernicharo2016); (cite: ligterink2020), respectively), the hot core precursor G328.2551-0.5321 (hereafter G328.2551) A, B (related to accretion shock positions), and envelope (hereafter env) positions ((cite: csengeri2019)), the hot corinos IRAS 16293-2422 (hereafter IRAS 16293) A and B ((cite: martin-domenech2017); (cite: ligterink2017); (cite: ligterink2018); (cite: manigand2020)), and the GC molecular cloud G+0.693-0.027 (hereafter G+0.693, (cite: zeng2018)). The Sgr B2(N) and G+0.693 observations were taken with different single-dish telescope (IRAM 30m and Green Bank Telescope) while the rest were observed using ALMA. Moreover, we have also compared the column densities with those of HNCOand HC(O)NH$_{2}$and the upper limits of CH$_{3}$NCOand CH$_{3}$C(O)NH$_{2}$estimated in the comet 67P/Churyumov-Gerasimenko (hereafter 67P) by the ROSINA experiment on ESA’s Rosetta mission reported by (cite: altwegg2017).

## Molecular abundances

![](Comparison-abundances-legend.pdf)

![](CorrelationAbundances-legend.pdf)

Six of the works listed above provide an estimate of $N$(H$_{2}$) and make it possible to compare with the molecular abundances obtained in this work. Figure [15](#fig-comp-ab) shows the molecular abundances derived in G31 and in the other regions. For abundances whose errors were not provided we assumed a value of 25%. We note however that the $N$(H$_{2}$) used for IRAS 16293 B should be considered as a lower limit since dust might be optically thick (e.g. (cite: jorgensen2016), and thus the abundances for this source should be taken as upper limits. At a glance, we can see that G31, in addition to Sgr B2(N2), is the only other source in which all of the five molecules (HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHO) have been detected. The behaviour of these two HMCs looks similar, except for HC(O)NH$_{2}$, which shows an over-abundance towards Sgr B2(N2). In most of the sources HNCOis the most abundant species, followed by HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHO. The only exceptions are IRAS 16293 B and Sgr B2(N2), whose HNCO and HC(O)NH$_{2}$abundances are similar between them, and G10.47, for which CH$_{3}$NCOis more abundant than HC(O)NH$_{2}$. Moreover, both HNCOand HC(O)NH$_{2}$abundances towards G31 are comparable with those of the GC molecular cloud G+0.693 ((cite: zeng2018)). HC(O)NH$_{2}$and CH$_{3}$NCOabundances together are similar to those derived towards the HMCs G10.47 and Sgr B2(N5), and the HMC precursor G328.2551 ((cite: gorai2020); (cite: bonfand2019); (cite: csengeri2019)), while only the HC(O)NH$_{2}$abundance is similar to that of the low-mass protostar IRAS 16293 B ((cite: martin-domenech2017)). All these similarities are within a factor of 4, and should be taken with caution since possible opacity effects of HNCO and HC(O)NH$_{2}$might have affected the derived abundances towards some of these sources (see Sect. [3](#results)). For G31 this is not the case since column densities, and thus abundances, have been derived from the $^{13}$C-isotopologues or the vibrationally excited states, which are optically thin (see Table [1](#transitions)).

The high molecular abundances found in HMCs, hot corinos, and G+0.693 (10$^{-10}$–10$^{-6}$) are consistent with their formation through pathways on the surface of dust grains at earlier phases, and subsequent desorption, induced by thermal heating (for HMCs and hot corinos) or by grain sputtering produced by shocks (for G+0.693 and the accretion shocks G328.2551 A and B, (cite: zeng2020); (cite: csengeri2019)). In fact, in absence of efficient desorption mechanisms, the gas-phase abundances are expected to be lower, as occurs in low-mass pre-stellar cores such as L1544 where the upper limits for the abundances of HC(O)NH$_{2}$and CH$_{3}$NCOthat have been reported are very low ($X$(HC(O)NH$_{2}$)$<$8.7$\times$10$^{-13}$ and $X$(CH$_{3}$NCO)$<$4.2$\times$10$^{-11}$, (cite: jimenez-serra2016)).

Figure [16](#fig-corr-ab) shows the comparison between pairs of molecular abundances, HC(O)NH$_{2}$and HNCO, CH$_{3}$NCOand HNCO, and CH$_{3}$NCOand HC(O)NH$_{2}$. It is already known from previous observations that there is a correlation between HNCO and HC(O)NH$_{2}$((cite: lopez-sepulcre2015; lopez-sepulcre2019); (cite: allen2020)). In the top-left panel of Fig. [16](#fig-corr-ab) the best power-law fits derived by (cite: lopez-sepulcre2015), $X$\[HC(O)NH$_{2}$\]=0.04$\times$ $X$\[HNCO\]$^{0.93}$, and by (cite: quenard2018), $X$\[HC(O)NH$_{2}$\]=32.14$\times$ $X$\[HNCO\]$^{1.29}$, are compared with the one derived here, $X$\[HC(O)NH$_{2}$\]=0.006$\times$ $X$\[HNCO\]$^{0.73}$ (with a Pearson coefficient of 0.99 and a P-value $<$0.05, indicating a strong positive correlation). Thus, the sample of sources discussed in this work, which also includes HMCs and a shock-dominated molecular cloud, is in agreement with the correlation found previously for low- and intermediate-mass pre-stellar and protostellar objects, which holds across several orders of magnitude in abundance. Based on this tight correlation, it has been proposed that the two species are chemically related and that the formation of HC(O)NH$_{2}$might occur through H-addition to solid-phase HNCO (e.g. (cite: tielens1982); (cite: charnley2004)). Experimental works first suggested that this process is not efficient ((cite: noble2015); (cite: fedoseev2015)), while recent works revised this possibility and found that a correlation between these two molecular species can be understood by H-abstraction and addition reactions (e.g. (cite: nguyen2011); (cite: haupa2019); (cite: suhasaria2020)). Moreover, hydrogenation of NO combined with UV-photon exposure and radical-radical reactions on grains has been suggested as the main formation pathways for both HNCOand HC(O)NH$_{2}$(e.g. (cite: jones2011); (cite: fedoseev2016); (cite: ligterink2018); (cite: dulieu2019)). (cite: coutens2016) found that the deuteration (D/H ratio) of HC(O)NH$_{2}$in IRAS 16293 B is similar to that of HNCO, in agreement with the hypothesis that both species are chemically related via grain-surface reactions. Gas-phase formation routes have also been proposed (see e.g. NH$_{2}$ + H$_{2}$CO, (cite: barone2015); (cite: skouteris2017)). Laboratory experiments by (cite: martin-domenech2020) show that both HNCOandHC(O)NH$_{2}$could form upon UV photoprocessing or electron irradiation of ice samples, indicating that energetic processing (like UV photons and cosmic rays) of ISM CO-rich ices could form both species, without the need of a chemical link and/or a similar precursor between the two. This was predicted by the chemical modelling of (cite: quenard2018), who showed that the formation of HC(O)NH$_{2}$at different temperature regimes is governed by different chemical processes. While at low temperatures the formation of HC(O)NH$_{2}$is driven by gas-phase formation via the reaction NH$_{2}$ + H$_{2}$CO $\rightarrow$ HC(O)NH$_{2}$ + H, at high temperature its formation occurs on the surface of dust grains via radical-radical addition reactions. Moreover, they showed that for HNCO grain-surface and gas-phase reactions are equally efficient at low temperature, while at high temperatures the gas-phase formation predominates and the small fraction formed on grains is released into the gas phase via thermal desorption. (cite: rimola2018) also showed via theoretical quantum chemical computations that HC(O)NH$_{2}$can form on grain surfaces starting from CN, which can quickly react with water-rich amorphous ices. Thus, the correlation between HNCOand HC(O)NH$_{2}$is mainly due to a similar response to the temperature of the two molecules, and not to a direct chemical link. In fact, the increase of the temperature triggers processes on the ice-mantle of grains, such as thermal evaporation. Moreover, as discussed above, other processes, like UV photons, cosmic rays and shocks, could help both on the formation of these molecules on grain surfaces and on their desorption in the gas.

Similarly to the HNCO vs. HC(O)NH$_{2}$relation, we have found similar correlations (Fig. [16](#fig-corr-ab)) between CH$_{3}$NCOand HNCO, $X$\[CH$_{3}$NCO\] = 0.0015$\times$ $X$\[HNCO\]$^{0.73}$, and between CH$_{3}$NCOandHC(O)NH$_{2}$, $X$\[CH$_{3}$NCO\]=0.02$\times$ $X$\[HC(O)NH$_{2}$\]$^{0.84}$ (both with a Pearson coefficient of 0.99 and a P-value $<$0.05, indicating strong positive correlations), suggesting links also between CH$_{3}$NCOand HNCO, and HC(O)NH$_{2}$. A correlation between CH$_{3}$NCOand HNCOwas already suggested by (cite: ligterink2021), who found that the CH$_{3}$NCOand HNCOcolumn density ratio is almost constant in different regions. It was proposed by (cite: halfen2015) that CH$_{3}$NCO could form in gas-phase through HNCO from the reaction: $$\begin{equation}
\label{HNCO-CH3}
{\rm HNCO} + {\rm CH}_{3} \rightarrow {\rm CH}_{3}{\rm NCO}+ {\rm H},
\end{equation}$$ or from $$\begin{align}
&{\rm HNCO} + {\rm CH}_{5}^{+} \rightarrow {\rm CH}_{3}{\rm NCOH}^{+} + {\rm H}_{2} \\
&{\rm CH}_{3}{\rm NCOH}^{+} + {\rm e}^{-} \rightarrow {\rm CH}_{3}{\rm NCO}+ {\rm H}.
\end{align}$$ (cite: cernicharo2016) found a similar spatial distribution for HNCO, HC(O)NH$_{2}$and CH$_{3}$NCOtowards Orion BN/KL, as observed for G31 in this work (Fig. [14](#fig-maps-high-res)), and suggested reaction [\[HNCO-CH3\]](#HNCO-CH3) as a possible grain-surface reaction to form CH$_{3}$NCO. Moreover, the HNCO/CH$_{3}$NCOabundance ratio found for G31 of 12$\pm$6 is consistent with the range of values predicted by the HMC model of (cite: belloche2017), who proposed CH$_{3}$NCOgrain-surface formation and ice sublimation during the warm-up phase (e.g. through thermal desorption as suggested for HNCOand HC(O)NH$_{2}$). Formation of CH$_{3}$NCOthrough HNCOand methane has also been considered on ices, where favourable thermodynamic conditions could be created (e.g. reduction of the energy barrier, (cite: cassone2021)). More recently (cite: majumdar2018) found that reaction [\[HNCO-CH3\]](#HNCO-CH3) is endothermic, and they proposed alternative routes for the formation of methyl-isocyanate on grains: $$\begin{align}
\label{}
&{\rm CH}_{3} + {\rm OCN} \rightarrow {\rm CH}_{3}{\rm NCO},\\
&{\rm N} + {\rm CH}_{3}{\rm CO} \rightarrow {\rm CH}_{3}{\rm C(N)O} \rightarrow {\rm CH}_{3}{\rm NCO},
\end{align}$$ or through the HCN$\cdots$CO van der Waals complex $$\begin{align}
\label{}
&{\rm H} + {\rm HCN \cdots CO} \rightarrow {\rm H}_{2}{\rm CN \cdots CO} \rightarrow {\rm H}_{2}{\rm CNCO} \\
&{\rm H} + {\rm H}_{2}{\rm CNCO} \rightarrow {\rm CH}_{3}{\rm NCO}.
\end{align}$$ Interestingly a similar process has also been found to be important for the formation of HNCO: $$\begin{equation}
\label{}
{\rm N \cdots CO} + {\rm H} \rightarrow {\rm HNCO},
\end{equation}$$ indicating that a possible link between the two species could be the van der Waals complexes involving CO. Finally, the correlation between CH$_{3}$NCOand HC(O)NH$_{2}$(bottom panel of Fig. [16](#fig-corr-ab)) is probably due to the fact that both molecules form on grains and are desorbed on gas-phase because of similar physical effects. For example, both molecules are expected to be already efficiently thermally desorbed at the high temperatures of HMCs ($>$100 K). In fact, temperature-programmed desorption experiments show that the HC(O)NH$_{2}$peak desorption temperature is around 200 K ((cite: ligterink2018)), while that of CH$_{3}$NCOis around 150 K ((cite: ligterink2017)). Thus, we expect most of both molecules to have been already released back to the gas-phase in hot cores.

Thus, a strong correlation between two molecules in a sample of sources does not directly imply that these molecules are chemically related (e.g. (cite: belloche2020)). Whether these results are a consequence of a direct chemical link or an effect caused by similar chemical responses to physical conditions cannot be firmly concluded yet, and more dedicated physico-chemical models are needed to disentangle all of the possible effects.

## Abundances with respect to CH$_{3}$OH

![](Comparison-abundances-legend-meth.pdf)

![](CorrelationAbundances-legend-meth.pdf)

In this section we have performed an analysis similar to that shown in Sect. [4.1](#disc-ab) comparing the abundances derived with respect to methanol, CH$_{3}$OH. All the sources are included, except Sgr B2 (N1S) for which the CH$_{3}$OH column density is not found in the literature, and G10.47 for which whose CH$_{3}$OH column density has been derived from Submillimeter Array observations ((cite: rolffs2011)) and not from ALMA observations as for the rest of the sources. Thus, these two sources are excluded from the discussion in this section. Moreover, for G31, G+0.693, Sgr B2(N), NGC 6334I, and IRAS 16293 A and B, $N$(CH$_{3}$OH) has been derived from the optically thin isotopologues $^{13}$CH$_{3}$OH (for G31, Mininni et al. in prep) and CH$_{3}^{18}$OH (for the other sources, (cite: rodriguez-almeida2021); (cite: belloche2013); (cite: bogelund2018); (cite: manigand2020); (cite: jorgensen2018)), after taking into account the $^{12}$C/$^{13}$Cand $^{16}$O/$^{18}$O ratios corrections as a function of the galactocentric distance ((cite: yan2019) for G31; (cite: wilson1994) for G+0.693, Sgr B2(N), and IRAS 16293 B; (cite: wilson1999) for NGC 6334I and IRAS 16293 A). Conversely, $N$(CH$_{3}$OH) for Sgr B2(N2), Sgr B2(N3), Sgr B2(N5), Orion BN/KL and G328.2551 has been obtained from the main isotopologue and could be affected by line opacity effects ((cite: belloche2016); (cite: bonfand2019); (cite: cernicharo2016); (cite: csengeri2019)).

Figure [17](#fig-comp-ab-meth) shows the abundances with respect to CH$_{3}$OH ($N$/$N$(CH$_{3}$OH)). First of all, G328.2551 and Sgr B2(N3) present similar $N$/$N$(CH$_{3}$OH) for HC(O)NH$_{2}$ and CH$_{3}$NCOwith respect to G31, and Sgr B2(N2) presents similar $N$/$N$(CH$_{3}$OH) for all the molecules except for HC(O)NH$_{2}$. Except for HNCO, Sgr B2(N) and Sgr B2(N5) present higher column density ratios than G31 with respect to CH$_{3}$OH. Moreover, NGC 6334I has similar $N$/$N$(CH$_{3}$OH) with respect to G31 towards all the positions, except for MM1-v for which higher ratios have been found for HNCO, HC(O)NH$_{2}$, and CH$_{3}$NHCHO. Orion BN/KL A and B have ratios similar to those of G31 for all the peptide-like bond molecular species, while IRAS 16293 A and B have lower $N$/$N$(CH$_{3}$OH) ratios. Finally, with respect to G31, G+0.693 presents higher ratios for HNCOand HC(O)NH$_{2}$, and a similar one for CH$_{3}$NCO. It should be noted that all the similarities are within a factor of 4.

The general trend is that most of the sources show similar $N$/$N$(CH$_{3}$OH) ratios, except for IRAS 16293 A and B, which present lower values, and Sgr B2(N), Sgr B2(N5), and G+0.693 that show higher values with respect to G31 and the other sources. Moreover, on average the $N$/$N$(CH$_{3}$OH) of HNCOis the highest, followed by that of HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHO, similar to what was found for the abundances derived with respect to $N$(H$_{2}$).

In Fig. [18](#fig-corr-ab-meth) we show the comparison between pairs of $N$/$N$(CH$_{3}$OH) ($X_{{\rm CH}_{3}{\rm OH}}$). In particular the best power-law fits are: $$\begin{align}
\label{}
& X_{{\rm CH}_{3}{\rm OH}}({\rm HC(O)NH}_{2})=0.18\times X_{{\rm CH}_{3}{\rm OH}}({\rm HNCO})^{0.92}, \\
& X_{{\rm CH}_{3}{\rm OH}}({\rm CH}_{3}{\rm NCO})=0.032\times X_{{\rm CH}_{3}{\rm OH}}({\rm HNCO})^{0.69}, \\
& X_{{\rm CH}_{3}{\rm OH}}({\rm CH}_{3}{\rm NCO})=0.05\times X_{{\rm CH}_{3}{\rm OH}}({\rm HC(O)NH}_{2})^{0.48}, \\
& X_{{\rm CH}_{3}{\rm OH}}({\rm CH}_{3}{\rm C(O)NH}_{2})=0.022\times X_{{\rm CH}_{3}{\rm OH}}({\rm HNCO})^{0.74}, \\
& X_{{\rm CH}_{3}{\rm OH}}({\rm CH}_{3}{\rm C(O)NH}_{2})= 0.042\times X_{{\rm CH}_{3}{\rm OH}}({\rm HC(O)NH}_{2})^{0.69}. 
\end{align}$$ Thus, also in this case we have found positive correlations between HC(O)NH$_{2}$and HNCO, CH$_{3}$NCOand HNCO, and CH$_{3}$NCOand HNCO, as already discussed in Sect. [4.1](#disc-ab). Moreover, thanks to the available data we have also found for the first time correlations between CH$_{3}$C(O)NH$_{2}$and HNCO, and CH$_{3}$C(O)NH$_{2}$and HC(O)NH$_{2}$.

## Column density ratios

![](ColumnDensities-vsHCONH2.pdf)

Figure [19](#fig-colden) shows the column density ratios of HNCO, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, and CH$_{3}$NHCHOwith respect to HC(O)NH$_{2}$in the different astronomical sources. For column densities whose errors were not provided we assumed a value of 25%. For IRAS 16293 B two values are shown, corresponding to those derived by (cite: martin-domenech2017), (cite: ligterink2017), and (cite: ligterink2018). From the left to the right, Fig. [19](#fig-colden) shows massive and low-mass star-forming regions, the GC G+0.693 molecular cloud, and the comet 67P values.

We note that overall there are similarities between molecular abundance ratios towards different regions, typically within $\sim$1 order of magnitude in the 80% of the sources. The HNCO/HC(O)NH$_{2}$ratio found in G31 is similar, within the errors, to those derived towards Orion BN/KL-A, NGC 6334I MM1-v, MM2-i, and MM2-ii, G10.47, IRAS 16293 B, and G+0.693 (top-left panel of Fig. [19](#fig-colden)). The CH$_{3}$NCO/HC(O)NH$_{2}$ratio is consistent, within the errors, to those of Sgr B2(N), Sgr B2(N1S), IRAS 16293 B, G328.2551 B and env, and G+0.693 (top-right panel of Fig. [19](#fig-colden)). The CH$_{3}$C(O)NH$_{2}$/HC(O)NH$_{2}$ratio is consistent, within the errors, to those of Sgr B2(N1S), Orion BN/KL-A, NGC 6334I MM1-iv, MM2-i, and MM2-ii, and IRAS 16293 B (bottom-left panel of Fig. [19](#fig-colden)). The CH$_{3}$NHCHO/HC(O)NH$_{2}$ratio is similar, within the errors, to those of Sgr B2(N1S), NGC 6334I MM1-v, MM1-vi, MM1-vii, MM1-viii, and MM1-nmf, which are all the sources in which CH$_{3}$NHCHOhas been detected, except Sgr B2(N2) (bottom-right panel of Fig. [19](#fig-colden)). The CH$_{3}$NHCHO/CH$_{3}$C(O)NH$_{2}$ratio is overall similar in all the sources, as observed in the bottom panels of Fig. [19](#fig-colden) where their column density ratios with respect to HC(O)NH$_{2}$are shown.

The similarities of the different molecular ratios in interstellar regions with very different physical properties (e.g. masses from $\sim$0.5 M$_{\odot}$ up to $\sim$100 M$_{\odot}$ and luminosities from $\sim$1 L$_{\odot}$ up to $\sim$10$^{7}$ L$_{\odot}$) and location in the Galaxy, such as high-mass and low-mass star-forming regions (HMCs and hot corinos, respectively) in the GC and in the galactic disk, and a GC molecular cloud with no signs of star formation yet ((cite: zeng2020)), suggest that these molecules were formed during very early phases of evolution. In fact, as discussed in Sect. [4.1](#disc-ab), these species could have been formed mostly on grains, and, in a later stage, released back to gas-phase through thermal desorption, in HMCs and hot corinos, or through shock-induced grain sputtering, in the case of G+0.693 and G328.2551 accretion shock positions. This has also been suggested by (cite: coletta2020), who found constant abundance ratios for H$_{3}$OCHO, CH$_{3}$OCH$_{3}$, C$_{2}$H$_{5}$CN and HC(O)NH$_{2}$towards low- and high-mass star-forming regions in different evolutionary stages. For the GC a similar conclusion has been proposed by (cite: requena-torres2006) who compared the abundances of O-bearing COMs derived towards giant molecular clouds in the GC with those measured in hot corinos and hot cores. They found that all of these abundances are consistent within a factor of 10 and suggested that COMs are ejected from grain mantles by shocks.

Regarding the formation of CH$_{3}$C(O)NH$_{2}$, (cite: quan2007) have proposed that it could be formed in gas-phase via radiative association reaction, like: $$\begin{align}
\label{}
&{\rm HC(O)NH}_{2} + {\rm CH}_{3}^{+} \rightarrow {\rm CH}_{3}{\rm CHONH}_{2}^{+} + h\nu \label{am1}\\
&{\rm CH}_{3}{\rm CHONH}_{2}^{+} + {\rm e}^{-} \rightarrow {\rm CH}_{3}{\rm C(O)NH}_{2} + {\rm  H}, \label{am2}
\end{align}$$ (cite: halfen2011) have suggested that ion-molecule processes might lead to the formation of both CH$_{3}$C(O)NH$_{2}$and CH$_{3}$NHCHO, and more recently (cite: redondo2014) have studied the viability of ion-molecule gas-phase reactions, such as CH$_{5}^{+}$ + HC(O)NH$_{2}$, to form CH$_{3}$C(O)NH$_{2}$. However, only gas-phase reactions are not enough to reproduce the observed abundances and the CH$_{3}$C(O)NH$_{2}$/HC(O)NH$_{2}$ratios in the ISM. (cite: frigge2018) show that CH$_{3}$NHCHOcould form in a mixture of methylamine (CH$_{3}$NH$_{2}$) and CO ices, upon irradiation with energetic electrons. In particular, they proposed the following reactions on grain surfaces: $$\begin{align}
&{\rm CH}_{3}{\rm NH}_{2} + {\rm CR} \rightarrow {\rm CH}_{3}{\rm NH} + {\rm H} \\
&{\rm CH}_{3}{\rm NH} + {\rm HCO} \rightarrow {\rm CH}_{3}{\rm NHCHO},
\end{align}$$ where CR are the cosmic rays simulated by energetic electrons. Moreover, (cite: garrod2008) have proposed CH$_{3}$ + HNCO as a possible formation route on grains, while (cite: belloche2017) suggest that CH$_{3}$C(O)NH$_{2}$is predominantly formed by H-abstraction from HC(O)NH$_{2}$, followed by methyl-group (CH$_{3}$) addition, and by the reaction NH$_{2}$ + CH$_{3}$CO. Moreover, these authors found that CH$_{3}$NHCHOcould be formed on grains either through the direct addition of functional-group radicals (e.g. CH$_{3}$ + HNCHO) or through the hydrogenation of CH$_{3}$NCO. CH$_{3}$C(O)NH$_{2}$has also been identified in carbonaceous chondrites ((cite: cooper1995)), and was found to form in experiments with irradiated ices (e.g. (cite: berger1961); (cite: ligterink2018)), favouring also the grain-surface formation.

The lower left panel of Fig. [19](#fig-colden) shows that CH$_{3}$C(O)NH$_{2}$is well correlated with HC(O)NH$_{2}$, as we already found from the correlation of their abundances with respect to CH$_{3}$OH (see Sect. [4.2](#ab-meth)). The CH$_{3}$C(O)NH$_{2}$/HC(O)NH$_{2}$ratios are all within $\sim$1 order of magnitude. This might indicate a direct chemical link, as suggested by reactions [\[am1\]](#am1) and [\[am2\]](#am2), or that both molecules are mainly formed on grain surface and desorb under similar physical conditions, as proposed by (cite: quenard2018) for HNCO and HC(O)NH$_{2}$. Indeed, this hypothesis is supported by the temperature programmed desorption experiment of (cite: ligterink2018), who have showed that the peak desorption temperatures of CH$_{3}$C(O)NH$_{2}$and HC(O)NH$_{2}$are very similar (219 and 210 K, respectively, see also (cite: corazzi2020)).

Finally, a comparison with the values found in the comet 67P shows that the CH$_{3}$C(O)NH$_{2}$/HC(O)NH$_{2}$and CH$_{3}$NHCHO/HC(O)NH$_{2}$upper limits (bottom-right panel of Fig. [19](#fig-colden)) are consistent with the values observed in the ISM, while the HNCO/HC(O)NH$_{2}$ratio is smaller than the ISM values. This could be due to an over-abundance of HC(O)NH$_{2}$in the 67P comet with respect to the ISM that could indicate a chemical reprocessing during later stages, e.g. the protoplanetary disk phase. However, the measurements with Rosina (Rosetta Orbiter Spectrometer for Ion and Neutral Analysis) cannot distinguish between the different structural isomers, so, if the other isomers were also formed, the abundance of HC(O)NH$_{2}$would be lower.

# Conclusions

In this work we have studied the peptide-like bond molecules HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, CH$_{3}$NHCHO, CH$_{3}$CH$_{2}$NCO, NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$in the context of the GUAPOS spectral survey, obtained with the ALMA interferometer towards the HMC G31. This is the first time that all of these molecules have been studied together towards G31 and outside the Galactic center. The main results and conclusions of our study are summarised below:

1.  The column densities of HNCO, HC(O)NH$_{2}$, and CH$_{3}$NCOhave been derived from their optically thin $^{13}$C-isotopologues, or from vibrationally excited states in case the $^{13}$C-species were only tentatively detected. CH$_{3}$C(O)NH$_{2}$is found to be optically thin in all the vibrational states allowing the derivation of the column density taking into account all the states together, while for CH$_{3}$NHCHOonly transitions from the optical thin ground vibrational state have been detected. CH$_{3}$CH$_{2}$NCOhas not been detected and the upper limit derived provides a CH$_{3}$NCO/CH$_{3}$CH$_{2}$NCOratio $>$24, consistent with what previously measured towards Orion KL and Sgr B2. On the other hand, also NH$_{2}$C(O)NH$_{2}$, NH$_{2}$C(O)CN, and HOCH$_{2}$C(O)NH$_{2}$have not been detected and we have derived their upper limits. Our findings in G31 show that the molecules follow the subsequent order of abundances compared to H$_{2}$ (from 10$^{-7}$ down to a few 10$^{-9}$): $X$(HNCO) $>$ $X$(HC(O)NH$_{2}$) $\ge$ $X$(CH$_{3}$NCO) $\ge$ $X$(CH$_{3}$C(O)NH$_{2}$) $\ge$ $X$(CH$_{3}$NHCHO). Moreover, we have found abundances with respect to CH$_{3}$OH that range from 10$^{-3}$ to $\sim$4$\times$10$^{-2}$.

2.  The emission of all the species towards the HMC is compact ($\sim$2$^{\prime\prime}$, i.e. $\sim$7500 au), and this has also been confirmed with higher angular resolution observations for HNCO, HC(O)NH$_{2}$, and CH$_{3}$NCO. The five molecular species trace hot molecular gas (temperature higher than 100 K), without significant spatial emission differences among them.

3.  The comparison with other sources in the ISM (HMCs in the GC and in the Galactic disk, hot corinos, and a shock-dominated GC molecular cloud) shows tight correlations between the abundances of HNCOand HC(O)NH$_{2}$, CH$_{3}$NCOand HNCO, and for the first time between CH$_{3}$NCOand HC(O)NH$_{2}$, CH$_{3}$C(O)NH$_{2}$and HNCO, and CH$_{3}$C(O)NH$_{2}$and HC(O)NH$_{2}$abundances. This suggests either a possible chemical link between these species, a common precursor, or a similar response to the physical conditions of the molecular clouds.

4.  The column density abundance ratios are quite similar in all the sources investigated, regardless of their physical conditions (e.g. mass and luminosity), and Galactic environment (GC or Galactic disk). Moreover, HMC, hot corinos and the shock-induced G+0.693 molecular cloud show abundances several orders of magnitude higher than low-mass pre-stellar cores. This suggests that most of the observed molecular abundances come from surface chemistry formation at early evolutionary stages. These molecules are subsequently released back to the gas phase, either by thermal (HMCs, hot corinos) or shock-induced desorption (G+0.693 and G328.2551 A and B).

# Acknowledgements

We thank the anonymous referee for the careful reading of the article and the useful comments. L. C. acknowledges financial support from the Spanish State Research Agency (AEI) through the project No. ESP2017-86582-C4-1-R. L. C. and V. M.R. acknowledge support from the Comunidad de Madrid through the Atracción de Talento Investigador Senior Grant (COOL: Cosmic Origins Of Life; 2019-T1/TIC-15379). I. J.-S. has received partial support from the Spanish State Research Agency (AEI; project number PID2019-105552RB-C41). C. M. acknowledges support from the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012 - iALMA (CUP C52I13000140001). C. .M akso acknowledges funding from the European Research Council (ERC) under the European Union’s Horizon 2020 program, through the ECOGAL Synergy grant (grant ID 855130). A. S.-M. carried out this research within the Collaborative Research Centre 956 (subproject A6), funded by the Deutsche Forschungsgemeinschaft (DFG) - project ID 184018867. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00489.S and ADS/JAO.ALMA#2017.1.00501.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We thank Arnaud Belloche for providing us the CH$_{3}$C(O)NH$_{2}$, $v$=0, $v_{\rm t}$=1, 2 spectroscopic entries. Most of the figures were generated with the PYTHON-based package MATPLOTLIB ((cite: hunter2007)).

154 natexlab

(ref: adams2010) Adams, F. C. 2010, ARA&A, 48, 47

(ref: agarwal1985) Agarwal, V. K., Schutte, W., Greenberg, J. M., et al. 1985, Origins of Life, 16, 21

(ref: allen2020) Allen, V., van der Tak, F. F. S., López-Sepulcre, A., et al. 2020, A&A, 636, A67

(ref: altwegg2017) Altwegg, K., Balsiger, H., Berthelier, J. J., et al. 2017, MNRAS, 469, S130

(ref: arce2008) Arce, H. G., Santiago-Garcı́a, J., Jørgensen, J. K., Tafalla, M., & Bachiller, R. 2008, ApJL, 681, L21

(ref: bacmann2012) Bacmann, A., Taquet, V., Faure, A., Kahane, C., & Ceccarelli, C. 2012, A&A, 541, L12

(ref: barone2015) Barone, V., Latouche, C., Skouteris, D., et al. 2015, MNRAS, 453, L31

(ref: belloche2019) Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10

(ref: belloche2020) Belloche, A., Maury, A. J., Maret, S., et al. 2020, A&A, 635, A198

(ref: belloche2017) Belloche, A., Meshcheryakov, A. A., Garrod, R. T., et al. 2017, A&A, 601, A49

(ref: belloche2016) Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, A&A, 587, A91

(ref: belloche2013) Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013, A&A, 559, A47

(ref: beltran2005) Beltrán, M. T., Cesaroni, R., Neri, R., et al. 2005, A&A, 435, 901

(ref: beltran2018) Beltrán, M. T., Cesaroni, R., Rivilla, V. M., et al. 2018, A&A, 615, A141

(ref: beltran2009) Beltrán, M. T., Codella, C., Viti, S., Neri, R., & Cesaroni, R. 2009, ApJL, 690, L93

(ref: beltran2013) Beltrán, M. T., Olmi, L., Cesaroni, R., et al. 2013, A&A, 552, A123

(ref: beltran2019) Beltrán, M. T., Padovani, M., Girart, J. M., et al. 2019, A&A, 630, A54

(ref: beltran2021) Beltrán, M. T., Rivilla, V. M., Cesaroni, R., et al. 2021, A&A, 648, A100

(ref: berger1961) Berger, R. 1961, Proc. Natl. Acad. Sci., 47(9), 1434

(ref: bisschop2007) Bisschop, S. E., Jørgensen, J. K., van Dishoeck, E. F., & de Wachter, E. B. M. 2007, A&A, 465, 913

(ref: blanco2006) Blanco, S., López, J. C., Lesarri, A., & Alonso, J. L. 2006, Journal of the American Chemical Society, 128, 12111

(ref: bogelund2018) Bøgelund, E. G., McGuire, B. A., Ligterink, N. F. W., et al. 2018, A&A, 615, A88

(ref: bonal2009) Bonal, L., Huss, G. R., Nagashima, K., & Krot, A. N. 2009, Meteoritics and Planetary Science Supplement, 72, 5178

(ref: bonfand2019) Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27

(ref: brown1975) Brown, R. D., Godfrey, P. D., & Storey, J. 1975, Journal of Molecular Spectroscopy, 58, 445

(ref: brown1997raman) Brown, S. S., Berghout, H. L., & Crim, F. F. 1997, J. Chem. Phys., 107, 9764

(ref: canelo2021) Canelo, C. M., Bronfman, L., Mendoza, E., et al. 2021, MNRAS, 504, 4428

(ref: cassone2021) Cassone, G., Saija, F., Sponer, J., et al. 2021, MNRAS, 504, 1565

(ref: cernicharo2016) Cernicharo, J., Kisiel, Z., Tercero, B., et al. 2016, A&A, 587, L4

(ref: cesaroni2019) Cesaroni, R. 2019, A&A, 631, A65

(ref: cesaroni2010) Cesaroni, R., Hofner, P., Araya, E., & Kurtz, S. 2010, A&A, 509, A50

(ref: cesaroni2017) Cesaroni, R., Sánchez-Monge, Á., Beltrán, M. T., et al. 2017, A&A, 602, A59

(ref: charnley2004) Charnley, S. B., Ehrenfreund, P., Millar, T. J., et al. 2004, MNRAS, 347, 157

(ref: christiansen2005) Christiansen, J. J. 2005, Journal of Molecular Spectroscopy, 231, 131

(ref: codella2020) Codella, C., Ceccarelli, C., Bianchi, E., et al. 2020, A&A, 635, A17

(ref: coletta2020) Coletta, A., Fontani, F., Rivilla, V. M., et al. 2020, A&A, 641, A54

(ref: colzi18b) Colzi, L., Fontani, F., Rivilla, V. M., et al. 2018b, MNRAS, 478, 3693

(ref: cooper1995) Cooper, G. W. & Cronin, J. R. 1995, , 59, 1003

(ref: corazzi2020) Corazzi, M. A., Fedele, D., Poggiali, G., & Brucato, J. R. 2020, A&A, 636, A63

(ref: coutens2016) Coutens, A., Jørgensen, J. K., van der Wiel, M. H. D., et al. 2016, A&A, 590, L6

(ref: csengeri2019) Csengeri, T., Belloche, A., Bontemps, S., et al. 2019, A&A, 632, A57

(ref: cuadrado2017) Cuadrado, S., Goicoechea, J. R., Cernicharo, J., et al. 2017, A&A, 603, A124

(ref: dulieu2019) Dulieu, F., Nguyen, T., Congiu, E., Baouche, S., & Taquet, V. 2019, MNRAS, 484, L119

(ref: durig2010conformational) Durig, J. R., Zhou, S. X., Zheng, C., & Durig, D. T. 2010, J. Mol. Struct., 971, 23

(ref: endres2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95

(ref: fedoseev2016) Fedoseev, G., Chuang, K. J., van Dishoeck, E. F., Ioppolo, S., & Linnartz, H. 2016, MNRAS, 460, 4297

(ref: fedoseev2015) Fedoseev, G., Ioppolo, S., Zhao, D., Lamberts, T., & Linnartz, H. 2015, MNRAS, 446, 439

(ref: frigge2018) Frigge, R., Zhu, C., Turner, A. M., et al. 2018, ApJ, 862, 84

(ref: gardner1980) Gardner, F. F., Godfrey, P. D., & Williams, D. R. 1980, MNRAS, 193, 713

(ref: garrod2008) Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ, 682, 283

(ref: girart2009) Girart, J. M., Beltrán, M. T., Zhang, Q., Rao, R., & Estalella, R. 2009, Science, 324, 1408

(ref: gorai2020) Gorai, P., Bhat, B., Sil, M., et al. 2020, ApJ, 895, 86

(ref: gorai2021) Gorai, P., Das, A., Shimonishi, T., et al. 2021, ApJ, 907, 108

(ref: gordy1984microwave) Gordy, W., Cook, R. L., & Weissberger, A. 1984, Microwave molecular spectra, Vol. 18 (Wiley New York)

(ref: grim1989) Grim, R. J. A., Greenberg, J. M., de Groot, M. S., et al. 1989, A&AS, 78, 161

(ref: guzman2013) Guzmán, V. V., Goicoechea, J. R., Pety, J., et al. 2013, A&A, 560, A73

(ref: halfen2011) Halfen, D. T., Ilyushin, V., & Ziurys, L. M. 2011, ApJ, 743, 60

(ref: halfen2015) Halfen, D. T., Ilyushin, V. V., & Ziurys, L. M. 2015, ApJL, 812, L5

(ref: haupa2019) Haupa, K. A., Tarczay, G., & Lee, Y.-P. 2019, in 74th International Symposium on Molecular Spectroscopy

(ref: heineking1994microwave) Heineking, N., Grabow, J.-U., & Stahl, W. 1994, Mol. Phys., 81, 1177

(ref: helmich1997) Helmich, F. P. & van Dishoeck, E. F. 1997, A&AS, 124, 205

(ref: hirota1974) Hirota, E., Sugisaki, R., Nielsen, C. J., & Sørensen, G. O. 1974, Journal of Molecular Spectroscopy, 49, 251

(ref: hocking1975microwave) Hocking, W., Gerry, M., & Winnewisser, G. 1975, Can. J. Phys., 53, 1869

(ref: hocking1975) Hocking, W. H., Gerry, M. C. L., & Winnewisser, G. 1975, Canadian Journal of Physics, 53, 1869

(ref: hollis2004) Hollis, J. M., Jewell, P. R., Lovas, F. J., Remijan, A., & Møllendal, H. 2004, ApJL, 610, L21

(ref: hollis2006) Hollis, J. M., Lovas, F. J., Remijan, A. J., et al. 2006, ApJL, 643, L25

(ref: hunter2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: ilyushin2004) Ilyushin, V. V., Alekseev, E. A., Dyubko, S. F., Kleiner, I., & Hougen, J. T. 2004, Journal of Molecular Spectroscopy, 227, 115

(ref: immer2019) Immer, K., Li, J., Quiroga-Nuñez, L. H., et al. 2019, A&A, 632, A123

(ref: jimenez-serra2020) Jiménez-Serra, I., Martı́n-Pintado, J., Rivilla, V. M., et al. 2020, Astrobiology, 20, 1048

(ref: jimenez-serra2016) Jiménez-Serra, I., Vasyunin, A. I., Caselli, P., et al. 2016, ApJL, 830, L6

(ref: jones2011) Jones, B. M., Bennett, C. J., & Kaiser, R. I. 2011, ApJ, 734, 78

(ref: jorgensen2012) Jørgensen, J. K., Favre, C., Bisschop, S. E., et al. 2012, ApJL, 757, L4

(ref: jorgensen2018) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170

(ref: jorgensen2016) Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595, A117

(ref: kasten1986a) Kasten, W. & Dreizler, H. 1986a, Zeitschrift Naturforschung Teil A, 41, 637

(ref: kasten1986b) Kasten, W. & Dreizler, H. 1986b, Zeitschrift Naturforschung Teil A, 41, 1173

(ref: kolesnikova2018) Kolesniková, L., Alonso, E. R., Tercero, B., Cernicharo, J., & Alonso, J. L. 2018, A&A, 616, A173

(ref: kolesnikova2019) Kolesniková, L., Kisiel, Z., Alonso, E. R., et al. 2019, ApJS, 245, 31

(ref: koput1986) Koput, J. 1986, Journal of Molecular Spectroscopy, 115, 131

(ref: korschinek2020) Korschinek, G., Faestermann, T., Poutivtsev, M., et al. 2020, Phys. Rev. Lett., 125, 031101

(ref: kretschmer1996) Kretschmer, U., Consalvo, D., Knaack, A., et al. 1996, Molecular Physics, 87, 1159

(ref: kryvda2009) Kryvda, A. V., Gerasimov, V. G., Dyubko, S. F., Alekseev, E. A., & Motiyenko, R. A. 2009, Journal of Molecular Spectroscopy, 254, 28

(ref: kukolich1971b) Kukolich, S. G. & Nelson, A. C. 1971, Chemical Physics Letters, 11, 383

(ref: kukolich1971a) Kukolich, S. G., Nelson, A. C., & Yamanashi, B. S. 1971, Journal of the American Chemical Society, 93, 6769

(ref: kurland1957) Kurland, R. J. & Bright Wilson, E., J. 1957, , 27, 585

(ref: lapinov2007) Lapinov, A. V., Golubiatnikov, G. Y., Markov, V. N., & Guarnieri, A. 2007, Astronomy Letters, 33, 121

(ref: lattelais2010) Lattelais, M., Pauzat, F., Ellinger, Y., & Ceccarelli, C. 2010, A&A, 519, A30

(ref: li2001) Li, A. & Draine, B. T. 2001, ApJ, 554, 778

(ref: lichtenberg2019) Lichtenberg, T., Golabek, G. J., Burn, R., et al. 2019, Nature Astronomy, 3, 307

(ref: ligterink2021) Ligterink, N. F. W., Ahmadi, A., Coutens, A., et al. 2021, A&A, 647, A87

(ref: ligterink2017) Ligterink, N. F. W., Coutens, A., Kofman, V., et al. 2017, MNRAS, 469, 2219

(ref: ligterink2020) Ligterink, N. F. W., El-Abd, S. J., Brogan, C. L., et al. 2020, ApJ, 901, 37

(ref: ligterink2018) Ligterink, N. F. W., Terwisscha van Scheltinga, J., Taquet, V., et al. 2018, MNRAS, 480, 3628

(ref: lopez-sepulcre2019) López-Sepulcre, A., Balucani, N., Ceccarelli, C., et al. 2019, ACS Earth and Space Chemistry, 3, 2122

(ref: lopez-sepulcre2015) López-Sepulcre, A., Jaber, A. A., Mendoza, E., et al. 2015, MNRAS, 449, 2438

(ref: majumdar2018) Majumdar, L., Loison, J. C., Ruaud, M., et al. 2018, MNRAS, 473, L59

(ref: manigand2020) Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48

(ref: marcelino2007) Marcelino, N., Cernicharo, J., Agúndez, M., et al. 2007, ApJL, 665, L127

(ref: maris2004) Maris, A. 2004, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 6, 2611

(ref: martin2019) Martı́n, S., Martı́n-Pintado, J., Blanco-Sánchez, C., et al. 2019, A&A, 631, A159

(ref: martin-domenech2020) Martı́n-Doménech, R., Öberg, K. I., & Rajappan, M. 2020, ApJ, 894, 98

(ref: martin-domenech2017) Martı́n-Doménech, R., Rivilla, V. M., Jiménez-Serra, I., et al. 2017, MNRAS, 469, 2230

(ref: mcguire2018) McGuire, B. A. 2018, ApJS, 239, 17

(ref: mcmullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mininni2020) Mininni, C., Beltrán, M. T., Rivilla, V. M., et al. 2020, A&A, 644, A84

(ref: miyake1993) Miyake, K. & Nakagawa, Y. 1993, Icarus, 106, 20

(ref: moskienko1991) Moskienko, E. M. & Dyubko, S. F. 1991, Radiophysics and Quantum Electronics, 34, 181

(ref: motiyenko2012) Motiyenko, R. A., Tercero, B., Cernicharo, J., & Margulès, L. 2012, A&A, 548, A71

(ref: muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: nazari2021) Nazari, P., van Gelder, M. L., van Dishoeck, E. F., et al. 2021, arXiv e-prints, arXiv:2104.03326

(ref: nguyen2011) Nguyen, V. S., Abbott, H. L., Dawley, M. M., et al. 2011, Journal of Physical Chemistry A, 115, 841

(ref: nguyen-q-rieu1991) Nguyen-Q-Rieu, Henkel, C., Jackson, J. M., & Mauersberger, R. 1991, A&A, 241, L33

(ref: niedenhoff1996pure) Niedenhoff, M., Yamada, K., & Winnewisser, G. 1996, J. Mol. Spectrosc., 176, 342

(ref: niedenhoff1995) Niedenhoff, M., Yamada, K. M. T., Belov, S. P., & Winnewisser, G. 1995, Journal of Molecular Spectroscopy, 174, 151

(ref: noble2015) Noble, J. A., Theule, P., Congiu, E., et al. 2015, A&A, 576, A91

(ref: osorio2009) Osorio, M., Anglada, G., Lizano, S., & D’Alessio, P. 2009, ApJ, 694, 29

(ref: pascal2005) Pascal, R., Boiteau, L., & Commeyras, A. 2005, From the Prebiotic Synthesis of $\alpha$-Amino Acids Towards a PrimitiveTranslation Apparatus for the Synthesis of Peptides, ed. P. Walde (Berlin, Heidelberg: Springer Berlin Heidelberg), 69–122

(ref: perez2012) Pérez, L. M., Carpenter, J. M., Chand ler, C. J., et al. 2012, ApJL, 760, L17

(ref: pickett1991) Pickett, H. M. 1991, J. Mol. Spectrosc., 148, 371

(ref: pickett1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: quan2007) Quan, D. & Herbst, E. 2007, A&A, 474, 521

(ref: quenard2018) Quénard, D., Jiménez-Serra, I., Viti, S., Holdship, J., & Coutens, A. 2018, MNRAS, 474, 2796

(ref: raunier2004) Raunier, S., Chiavassa, T., Duvernay, F., et al. 2004, A&A, 416, 165

(ref: redondo2014) Redondo, P., Barrientos, C., & Largo, A. 2014, ApJ, 793, 32

(ref: remijan2014) Remijan, A. J., Snyder, L. E., McGuire, B. A., et al. 2014, ApJ, 783, 77

(ref: requena-torres2006) Requena-Torres, M. A., Martı́n-Pintado, J., Rodrı́guez-Franco, A., et al. 2006, A&A, 455, 971

(ref: rimola2018) Rimola, A., Skouteris, D., Balucani, N., et al. 2018, ACS Earth and Space Chemistry, 2, 720

(ref: rivilla2017) Rivilla, V. M., Beltrán, M. T., Cesaroni, R., et al. 2017, A&A, 598, A59

(ref: rivilla2021) Rivilla, V. M., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2021, Proceedings of the National Academy of Sciences, 118 \[\]

(ref: rivilla2019) Rivilla, V. M., Martı́n-Pintado, J., Jiménez-Serra, I., et al. 2019, MNRAS, 483, L114

(ref: rodriguez-almeida2021) Rodrı́guez-Almeida, L. F., Jiménez-Serra, I., Rivilla, V. M., et al. 2021, ApJL, 912, L11

(ref: rodriguez-fernandez2010) Rodrı́guez-Fernández, N. J., Tafalla, M., Gueth, F., & Bachiller, R. 2010, A&A, 516, A98

(ref: rolffs2011) Rolffs, R., Schilke, P., Zhang, Q., & Zapata, L. 2011, A&A, 536, A33

(ref: sakaizumi1976microwave) Sakaizumi, T., Yamada, O., Ushida, K., Ohashi, O., & Yamaguchi, I. 1976, Bull. Chem. Soc. Jpn, 49, 2908

(ref: sanchez-monge2018) Sánchez-Monge, Á., Schilke, P., Ginsburg, A., Cesaroni, R., & Schmiedeke, A. 2018, A&A, 609, A101

(ref: sanz-novo2020) Sanz-Novo, M., Belloche, A., Alonso, J. L., et al. 2020, A&A, 639, A135

(ref: skouteris2017) Skouteris, D., Vazart, F., Ceccarelli, C., et al. 2017, MNRAS, 468, L1

(ref: snyder1972) Snyder, L. E. & Buhl, D. 1972, ApJ, 177, 619

(ref: stubgaard1978) Stubgaard, M. 1978, PhD thesis, Københavns Universitet

(ref: suhasaria2020) Suhasaria, T. & Mennella, V. 2020, A&A, 641, A88

(ref: tielens1982) Tielens, A. G. G. M. & Hagen, W. 1982, A&A, 114, 245

(ref: turner1999) Turner, B. E., Terzieva, R., & Herbst, E. 1999, ApJ, 518, 699

(ref: vorobeva1994) Vorob’eva, E. M. & Dyubko, S. F. 1994, Radiophysics and Quantum Electronics, 37, 155

(ref: wallner2020) Wallner, A., Feige, J., Fifield, L. K., et al. 2020, Proceedings of the National Academy of Sciences, 117, 21873

(ref: wilson1999) Wilson, T. L. 1999, Reports on Progress in Physics, 62, 143

(ref: wilson1994) Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191

(ref: winnewisser2005) Winnewisser, M., Medvedev, I. R., De Lucia, F. C., et al. 2005, ApJS, 159, 189

(ref: yamada1977type) Yamada, K. 1977, J. Mol. Spectrosc., 68, 423

(ref: yamada1977b) Yamada, K. & Winnewisser, M. 1977, J. Mol. Spectrosc., 68, 307

(ref: yan2019) Yan, Y. T., Zhang, J. S., Henkel, C., et al. 2019, ApJ, 877, 154

(ref: zeng2018) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, MNRAS, 478, 2962

(ref: zeng2020) Zeng, S., Zhang, Q., Jiménez-Serra, I., et al. 2020, MNRAS, 497, 4896

# Continuum determination

![](STATCONT-continuum.eps)

In this appendix we present the results from the continuum determination and subtraction procedure. First, we have divided the final spectrum obtained by (cite: mininni2020) in 32 spectral windows of 1 GHz each. Then, we have applied the corrected sigma clipping method (c-SMC) of STATCONT ((cite: sanchez-monge2018)) to each of them, which produces continuum-subtracted spectra. Secondly, we have averaged them together with the MADCUBA software. The final spectrum is shown in Fig. [25](#fig-total-spectra-1).

STATCONT gives also the continuum emission levels, with its uncertainty, for each of the 32 spectral windows, which are shown in Fig. [20](#fig-contsub) as black dots. The synthesized beam brightness temperature can be described with the function: $$\begin{equation}
\label{func-T}
T_{\rm SB}(\nu)=T_{\rm SB}(\nu_{0}) \biggl(\frac{\nu}{\nu_{0}}\biggr)^{\beta},
\end{equation}$$ where $\nu_{0}$=84.579 GHz, and $\beta$ is the spectral index of the dust opacity $\kappa_{\rm \nu}$ ($\kappa_{\rm \nu} \propto \nu^{\rm \beta}$), which is related to the slope $\alpha$ of the spectral energy distribution ($S_{\rm \nu} \propto \nu^{\rm \alpha}$), by $$\begin{equation}
\alpha = 2 + \beta,
\end{equation}$$ for optically thin dust emission (e.g. (cite: miyake1993)). Equation [\[func-T\]](#func-T) can be written as: $$\begin{equation}
\log(T_{\rm SB}) = \log (T_{\rm SB}(\nu_{0})) + \beta \log\biggl(\frac{\nu}{\nu_{0}}\biggr),
\end{equation}$$ where log indicates the logarithm to base 10. We applied the linear regression fit to the latter equation, obtaining $\beta$=0.71$\pm$0.06 and $\log(T_{\rm SB}(\nu_{0})$)=1.048$\pm$0.005, which corresponds to $T_{\rm SB}(\nu_{0})$=11$\pm$1.

The millimeter dust opacity slope for small ISM dust grains is $\beta \sim$1.7 ((cite: li2001)). The $\beta$ of 0.7 obtained towards G31 is lower, and could indicate a larger sized grain (centimeter-size) distribution (e.g. (cite: perez2012)). This value is also consistent with what found by (cite: beltran2013) ($\beta$=0.8) from the SED fitting towards the G29.96-0.02 hot molecular core.

The red solid line of Fig. [20](#fig-contsub) represents Eq. [\[func-T\]](#func-T), with $\beta$=0.71. The orange solid lines correspond to the error of $\pm$1 found from the fit to $T_{\rm SB}(\nu_{0})$. The error of 1 K obtained with this procedure is consistent with the uncertainty of 1.2 K obtained from the combination of the spectra to derive the final spectra performed by (cite: mininni2020). Thus, being conservative, we adopted an uncertainty value of $\pm$1.2 K for the continuum determination, which corresponds to the 11% of $T_{\rm SB}(\nu_{0})$, as an additional error in the derivation of the molecular parameters from the fit procedure (see Sects. [2.3](#analysis) and [3](#results)).

# Spectroscopy

+:---------------------------------------------:+:---------------:+:-------:+:-------------:+:-------------------------------------------------:+:-------------:+
| Molecule                                      | Catalogue$^{a}$ | Entry   | Date          | Line list                                         | Dipole moment |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
|                                               |                 |         |               | reference                                         | reference     |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| Isocyanic acid                                                                                                                                                |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HNCO, $v$=0                                   | CDMS            | 43511   | May 2009      | (1), (2), (3), (4)                                | \(3\)         |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HNCO, $v_{4}$=1                               | MADCUBA         | –       | December 2020 | (5), (6), (7), Appendix [7.1](#spectroscopy-HNCO) | \(3\)         |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HNCO, $v_{5}$=1                               | MADCUBA         | –       | December 2020 | Appendix [7.1](#spectroscopy-HNCO)                | \(3\)         |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HNCO, $v_{6}$=1                               | MADCUBA         | –       | December 2020 | Appendix [7.1](#spectroscopy-HNCO)                | \(3\)         |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HN$^{13}$CO, $v$=0                            | JPL             | 44008   | July 1987     | \(3\)                                             | \(3\)         |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| H$^{15}$NCO, $v$=0                            | JPL             | 44007   | July 1987     | \(3\)                                             | \(3\)         |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| Formamide                                                                                                                                                     |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HC(O)NH$_{2}$, $v$=0                          | CDMS            | 455512  | April 2013    | (8), (9), (10), (11),                             | \(16\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
|                                               |                 |         |               | (12), (13), (14), (15)                            |               |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HC(O)NH$_{2}$, $v_{12}$=1                     | CDMS            | 45516   | April 2013    | (9), (11), (12), (14), (15)                       | \(16\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| H$^{13}$C(O)NH$_{2}$, $v$=0                   | CDMS            | 46512   | April 2013    | (10), (13), (14), (15), (17)                      | \(16\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| Methyl isocyanate                                                                                                                                             |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| CH$_{3}$NCO, $v_{\rm b}$=0                    | CDMS            | 57505   | March 2016    | (18), (19), (20)                                  | \(21\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| CH$_{3}$NCO, $v_{\rm b}$=1                    | CDMS            | 57506   | March 2016    | (18), (19), (20)                                  | \(21\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0,1           | MADCUBA         | –       | December 2020 | \(20\)                                            | \(21\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| CH$_{3}$N$^{13}$CO, $v_{\rm b}$=0,1           | MADCUBA         | –       | December 2020 | \(20\)                                            | \(21\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| Acetamide                                                                                                                                                     |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| CH$_{3}$C(O)NH$_{2}$, $v$=0, $v_{\rm t}$=1, 2 | MADCUBA         | –       | December 2020 | (22), (23)                                        | \(22\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| N-methylformamide                                                                                                                                             |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| CH$_{3}$NHCHO,$v$=0, $v_{\rm t}$=1, 2         | MADCUBA         | –       | December 2020 | \(23\)                                            | \(23\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| Ethyl isocyanate                                                                                                                                              |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| CH$_{3}$CH$_{2}$NCO, $v$=0                    | MADCUBA         | –       | December 2020 | (24), Appendix [7.2](#spectroscopy-CH3NCO)        | \(25\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| NH$_{2}$C(O)NH$_{2}$$v$=0                     | CDMS            | 60517   | October 2017  | (26), (27), (28), (29)                            | \(27\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| NH$_{2}$C(O)CN, $v$=0                         | CDMS            | 70504   | June 2006     | (30), (31)                                        | \(30\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
| HOCH$_{2}$C(O)NH$_{2}$, $v$=0                 | CDMS            | 75517   | December 2020 | \(32\)                                            | \(33\)        |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+
|                                               |                 |         |               |                                                   |               |
+-----------------------------------------------+-----------------+---------+---------------+---------------------------------------------------+---------------+

Table notes:

The transitions of the molecules studied in this work (HNCO, HC(O)NH$_{2}$, CH$_{3}$NCO, CH$_{3}$C(O)NH$_{2}$, CH$_{3}$NHCHO, and CH$_{3}$CH$_{2}$NCO) were taken from the catalogues and spectroscopic works listed in Table [\[tab-spectroscopy\]](#tab-spectroscopy). We have taken the entries from the Cologne Database for Molecular Spectroscopy[^7](CDMS, (cite: muller2001; muller2005); (cite: endres2016)) and the Jet Propulsion Laboratory[^8] (JPL, (cite: pickett1998)) catalogues. Moreover, for species whose spectroscopy was not present in the catalogues, we have added to MADCUBA-SLIM entries using available spectroscopic works. A detailed explanation about how we evaluate the partition function of HNCOand CH$_{3}$CH$_{2}$NCOis given in Sects. [7.1](#spectroscopy-HNCO) and [7.2](#spectroscopy-CH3NCO), respectively.

## HNCOdata and partition function evaluation

The spectral predictions of HNCO in the three lowest vibrationally excited states ((cite: brown1997raman)), namely $v_4=1$ ($E=776.6$ cm$^{-1}$), $v_5=1$ ($E=577.4$ cm$^{-1}$), and $v_6=1$ ($E=656.3$ cm$^{-1}$), have been obtained using the spectroscopic data reported in (cite: yamada1977type; yamada1977b; niedenhoff1996pure). The dipole moment components ($\mu_a = 1.58$ D and $\mu_b = 1.35$ D) were assumed to be identical to those determined for the ground vibrational state (cite: hocking1975microwave).

The ro-vibrational partition function of HNCO has been computed at temperatures, $T$, between 2.725 and 300 K using the rotational partition function values from CDMS (see Col. 2 of Table [\[tab:qrot1\]](#tab:qrot1)) and calculating the vibrational correction ((cite: gordy1984microwave)) as:

$$\begin{equation}
\label{eq:vibfact}
    Q_\mathrm{vib} = \left[ \prod_{k=1}^{3N-6} \left( 1 - e^{-\frac{h \omega_{\rm k}}{k_{\rm B} T}} \right) \right]^{-1} \,,
\end{equation}$$ where $\omega_{\rm k}$ is the vibrational harmonic frequency of the $k$-th vibrational mode, $h$ is the Planck constant, and $k_{\rm B}$ is the Boltzmann constant. The sum runs over the $k = 6$ normal modes of HNCO, with the harmonic frequencies ($\omega_k$) taken from (cite: brown1997raman). The values of $Q_\mathrm{vibrot}$ are listed in Table [\[tab:qrot1\]](#tab:qrot1).

. .c.\
& & &\
\
300.000 & 2695.3359 & 1.14437 & 3084.4546\
225.000 & 1742.4282 & 1.04874 & 1827.3538\
150.000 & 943.7057 & 1.00639 & 949.7374\
75.000 & 331.9879 & 1.00002 & 331.9943\
37.500 & 117.3039 & 1.00000 & 117.3039\
18.750 & 42.8291 & 1.00000 & 42.8291\
9.375 & 18.4492 & 1.00000 & 18.4492\
5.000 & 9.8228 & 1.00000 & 9.8228\
2.725 & 5.5129 & 1.00000 & 5.5129\

Table notes:

## CH$_{3}$CH$_{2}$NCOdata and partition function evaluation

The spectral predictions of C$_{2}$H$_{5}$NCO in the ground and the first three torsional excited states have been obtained using the recent spectroscopic data of (cite: kolesnikova2018), which also contain transitions from (cite: heineking1994microwave). The values of the dipole moment components, $\mu_a = 2.81(2)$ D and $\mu_b = 0.03$ D, were derived in (cite: sakaizumi1976microwave).

In order to evaluate the ro-vibrational partition function of C$_{2}$H$_{5}$NCO, an approach similar to that used in (cite: cernicharo2016) has been adopted. First, the rotational partition function was computed analytically using the following equation:

$$\begin{equation}
\label{eq:qrot-analyt}
    Q_\mathrm{rot}(T) = 5.3311 \times 10^6 \times\sqrt{\frac{T^3}{(A \times B \times C)}},
\end{equation}$$ where the factor 5.3311$\times$10$^6$ is derived from the units used for the temperature ($T$), K, and for the rotational constants $A$, $B$ and $C$, MHz. The values thus obtained were used to check whether the numerical computation of `SPCAT` (cite: pickett1991) was close to convergence or not. The two methods gave comparable results, with differences smaller than 1%. Therefore, we decided to use the values computed numerically.

As far as the vibrational partition function is concerned, we decided to account for only the vibrational states below 400 cm$^{-1}$, as done by (cite: cernicharo2016). This choice allowed a fair determination of the \[CH$_{3}$NCO\]/\[C$_{2}$H$_{5}$NCO\] abundance ratio.

CH$_{3}$CH$_{2}$NCOpossesses three vibrational modes below 400 cm$^{-1}$ ($\sim$600 K), namely the C-N torsion ($E = 40$ cm$^{-1}$ (cite: kolesnikova2018)), the CNC bending ($E = 122$ cm$^{-1}$ (cite: durig2010conformational)), and the CH$_{3}$ torsion ($E = 265$ cm$^{-1}$ (cite: durig2010conformational)). We considered all the multiple and combined excitations of these three modes within our threshold energy of 400 cm$^{-1}$ and computed the value of $Q_\mathrm{vib}$ at different temperatures using the following equation ((cite: gordy1984microwave)):

$$\begin{equation}
\label{eq:qvibfact2}
    Q_\mathrm{vib} = \sum_{E_{\rm i}=0~\mathrm{cm}^{-1}}^{E_i \le 400~\mathrm{cm}^{-1}} e^{-\frac{E_{\rm i}}{k_{\rm B} T}} \,,
\end{equation}$$ where $E_{\rm i}$ is the vibrational energy of the $i$-th level. Finally, $Q_\mathrm{vibrot}$ was obtained as the product of $Q_\mathrm{rot}$ and $Q_\mathrm{vib}$. All these values, computed at temperatures between 2.725 and 300 K, are listed in Table [\[tab:qrot2\]](#tab:qrot2).

. .c.\
& & &\
\
300.000 & 83423.9162 & 9.96669 & 831460.1637\
225.000 & 54116.8299 & 7.38116 & 399445.2080\
150.000 & 29365.9661 & 4.54674 & 133519.4629\
75.000 & 10348.8360 & 2.07522 & 21476.0934\
37.500 & 3655.0733 & 1.28668 & 4702.9099\
18.750 & 1292.7145 & 1.04879 & 1355.7917\
9.375 & 457.8892 & 1.00216 & 458.8790\
5.000 & 179.0092 & 1.00001 & 179.0110\
2.725 & 72.5214 & 1.00000 & 72.5214\

Table notes:

# Identified Spectral Lines

In this Appendix we list the unblended or slightly blended transitions of the molecules studied in this work. These transitions are also shown in Figs. [2](#fig-res-ia)–[10](#fig-res-nm), [21](#fig-res-ia-va), [22](#fig-res-ia-vb), [23](#fig-ia-15N), and [24](#fig-mi-13C).

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Molecule | Frequency | Transition$^{a}$ | log$I$ | $E_{\rm up}$ | $\tau$ |
|  | (MHz) |  | (nm$^{2}$ MHz) | \(K\) |  |
|  |  |  |  |  |  |
| Molecule | Frequency | Transition$^{a}$ | log$I$ | $E_{\rm up}$ | $\tau$ |
|  | (MHz) |  | (nm$^{2}$ MHz) | \(K\) |  |
| HNCO, $v$=0 | 87925.2334 | 4,0,4–3,0,3 | -3.8060 | 10.55 | 0.18$\pm$0.04 |
| HNCO, $v$=0 | 109495.9991 | 5,1,5–4,1,4 | -3.6057 | 59.04 | 0.21$\pm$0.04 |
| HNCO, $v$=0 | 109872.3731 | 5,2,4–4,2,3 | -3.8446 | 186.11 | 0.10$\pm$0.02 |
| HNCO, $v$=0 | 109872.7789 | 5,2,3–4,2,2 | -3.8446 | 186.11 | 0.10$\pm$0.02 |
| HNCO, $v$=0 | 109905.7485 | 5,0,5–4,0,4 | -3.5221 | 15.83 | 0.27$\pm$0.06 |
| HNCO, $v$=0 | 110298.0874 | 5,1,4–4,1,3 | -3.5995 | 59.16 | 0.21$\pm$0.04 |
| HNCO, $v_{4}$=1 | 106791.4186 | 17,0,17–16,1,16 | -4.8853 | 992.59 | 0.0192$\pm$0.0012 |
| HNCO, $v_{4}$=1 | 110084.3531 | 5,0,5–4,0,4 | -4.7236 | 846.79 | 0.032$\pm$0.002 |
| HNCO, $v_{4}$=1 | 110089.7202 | 5,3,3–4,3,2 | -5.1069 | 977.73 | 0.0114$\pm$0.0007 |
| HNCO, $v_{4}$=1 | 110089.7207 | 5,3,2–4,3,1 | -5.1069 | 977.73 | 0.0114$\pm$0.0007 |
| HNCO, $v_{4}$=1 | 110104.0506 | 5,2,4–4,2,3 | -4.8776 | 900.99 | 0.0213$\pm$0.0014 |
| HNCO, $v_{4}$=1 | 110105.2994 | 5,2,3–4,2,2 | -4.8776 | 900.99 | 0.0213$\pm$0.0014 |
| HNCO, $v_{4}$=1 | 110418.9327 | 5,1,4–4,1,3 | -4.7579 | 860.07 | 0.029$\pm$0.002 |
| HNCO, $v_{5}$=1 | 87738.9007 | 4,2,3–3,2,2 | -5.3855 | 1014.08 | 0.0091$\pm$0.0016 |
| HNCO, $v_{5}$=1 | 87740.6295 | 4,2,2–3,2,1 | -5.3854 | 1014.08 | 0.0091$\pm$0.0016 |
| HNCO, $v_{5}$=1 | 88064.919 | 4,3,2–3,3,1 | -5.7274 | 1090.86 | 0.0037$\pm$0.0007 |
| HNCO, $v_{5}$=1 | 88064.9193 | 4,3,1–3,3,0 | -5.7274 | 1090.86 | 0.0037$\pm$0.0007 |
| HNCO, $v_{5}$=1 | 88131.9182 | 4,1,3–3,1,2 | -5.2254 | 973.16 | 0.014$\pm$0.003 |
| HN$^{13}$CO, $v$=0 | 87926.8683 | 4,0,4,3–3,0,3,3 | -5.3655 | 10.55 | 0.0014$\pm$0.0001 |
| HN$^{13}$CO, $v$=0 | 87927.64 | 4,0,4,3–3,0,3,2 | -4.3075 | 10.55 | 0.0160$\pm$0.0011 |
| HN$^{13}$CO, $v$=0 | 87927.64 | 4,0,4,4–3,0,3,3 | -4.1894 | 10.55 | 0.0210$\pm$0.0014 |
| HN$^{13}$CO, $v$=0 | 87927.64 | 4,0,4,5–3,0,3,4 | -4.0743 | 10.55 | 0.027$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 109497.4203 | 5,1,5,4–4,1,4,4 | -5.3589 | 58.94 | 0.00107$\pm$0.00007 |
| HN$^{13}$CO, $v$=0 | 109498.34 | 5,1,5,5–4,1,4,4 | -3.9787 | 58.94 | 0.026$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 109498.34 | 5,1,5,4–4,1,4,3 | -4.0701 | 58.94 | 0.021$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 109498.34 | 5,1,5,6–4,1,4,5 | -3.8884 | 58.94 | 0.032$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 109499.1736 | 5,1,5,5–4,1,4,5 | -5.3589 | 58.94 | 0.00107$\pm$0.00007 |
| HN$^{13}$CO, $v$=0 | 109875.3019 | 5,2,4,4–4,2,3,4 | -5.6014 | 188.51 | 0.00052$\pm$0.00004 |
| HN$^{13}$CO, $v$=0 | 109875.7012 | 5,2,3,4–4,2,2,4 | -5.6014 | 188.51 | 0.00052$\pm$0.00004 |
| HN$^{13}$CO, $v$=0 | 109875.73 | 5,2,4,5–4,2,3,4 | -4.2212 | 188.51 | 0.0124$\pm$0.0009 |
| HN$^{13}$CO, $v$=0 | 109875.73 | 5,2,4,6–4,2,3,5 | -4.131 | 188.51 | 0.0153$\pm$0.0010 |
| HN$^{13}$CO, $v$=0 | 109875.73 | 5,2,4,4–4,2,3,3 | -4.3126 | 188.51 | 0.0100$\pm$0.0007 |
| HN$^{13}$CO, $v$=0 | 109876.08 | 5,2,3,5–4,2,2,4 | -4.2212 | 188.51 | 0.0124$\pm$0.0009 |
| HN$^{13}$CO, $v$=0 | 109876.08 | 5,2,3,6–4,2,2,5 | -4.1309 | 188.51 | 0.0153$\pm$0.0011 |
| HN$^{13}$CO, $v$=0 | 109876.08 | 5,2,3,4–4,2,2,3 | -4.3126 | 188.51 | 0.0101$\pm$0.0007 |
| HN$^{13}$CO, $v$=0 | 109876.0808 | 5,2,4,5–4,2,3,5 | -5.6014 | 188.51 | 0.00052$\pm$0.00004 |
| HN$^{13}$CO, $v$=0 | 109876.4797 | 5,2,3,5–4,2,2,5 | -5.6014 | 188.51 | 0.00052$\pm$0.00004 |
| HN$^{13}$CO, $v$=0 | 109908.0277 | 5,0,5,4–4,0,4,4 | -5.2755 | 15.83 | 0.00137$\pm$0.00009 |
| HN$^{13}$CO, $v$=0 | 109908.95 | 5,0,5,4–4,0,4,3 | -3.9867 | 15.83 | 0.027$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 109908.95 | 5,0,5,5–4,0,4,4 | -3.8953 | 15.83 | 0.033$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 109908.95 | 5,0,5,6–4,0,4,5 | -3.805 | 15.83 | 0.040$\pm$0.003 |
| HN$^{13}$CO, $v$=0 | 109909.5554 | 5,0,5,4–4,0,4,4 | -5.2755 | 15.83 | 0.0014$\pm$0.0001 |
| HN$^{13}$CO, $v$=0 | 110301.5491 | 5,1,4,4–4,1,3,4 | -5.3527 | 59.05 | 0.00108$\pm$0.00008 |
| HN$^{13}$CO, $v$=0 | 110301.98 | 5,1,4,5–4,1,3,4 | -3.9725 | 59.05 | 0.026$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 110301.98 | 5,1,4,4–4,1,3,3 | -4.0639 | 59.05 | 0.021$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 110301.98 | 5,1,4,6–4,1,3,5 | -3.8822 | 59.058 | 0.032$\pm$0.002 |
| HN$^{13}$CO, $v$=0 | 110302.4762 | 5,1,4,5–4,1,3,5 | -5.3527 | 59.05 | 0.00108$\pm$0.00007 |
| H$^{15}$NCO, $v$=0 | 106223.92 | 5,1,5–4,1,4 | -3.5257 | 58.13 | 0.0097$\pm$0.0015 |
| H$^{15}$NCO, $v$=0 | 106578.32 | 5,2,4–4,2,3 | -3.7669 | 186.69 | 0.0047$\pm$0.0007 |
| H$^{15}$NCO, $v$=0 | 106578.6409 | 5,2,3–4,2,2 | -3.7669 | 186.69 | 0.0047$\pm$0.0007 |
| H$^{15}$NCO, $v$=0 | 106614.42 | 5,0,5–4,0,4 | -3.4429 | 15.35 | 0.012$\pm$0.002 |
| HC(O)NH$_{2}$, $v$=0 | 84542.3304 | 4,0,4–3,0,3 | -3.6043 | 10.16 | 0.30$\pm$0.09 |
| HC(O)NH$_{2}$, $v$=0 | 84807.7953 | 4,2,3–3,2,2 | -3.7436 | 22.10 | 0.20$\pm$0.06 |
| HC(O)NH$_{2}$, $v$=0 | 85093.2721 | 4,2,2–3,2,1 | -3.7407 | 22.12 | 0.20$\pm$0.06 |
| HC(O)NH$_{2}$, $v$=0 | 87848.8735 | 4,1,3–3,1,2 | -3.6036 | 13.52 | 0.28$\pm$0.09 |
| HC(O)NH$_{2}$, $v$=0 | 105972.5989 | 5,2,4–4,2,3 | -3.4106 | 27.19 | 0.34$\pm$0.10 |
| HC(O)NH$_{2}$, $v$=0 | 106107.8695 | 5,4,2–4,4,1 | -3.8292 | 62.95 | 0.11$\pm$0.03 |
| HC(O)NH$_{2}$, $v$=0 | 106107.8951 | 5,4,1–4,4,0 | -3.8292 | 62.95 | 0.11$\pm$0.03 |
| HC(O)NH$_{2}$, $v$=0 | 106134.4272 | 5,3,3–4,3,2 | -3.5489 | 42.10 | 0.23$\pm$0.07 |
| HC(O)NH$_{2}$, $v$=0 | 106141.3997 | 5,3,2–4,3,1 | -3.5489 | 42.10 | 0.23$\pm$0.07 |
| HC(O)NH$_{2}$, $v$=0 | 106541.6799 | 5,2,3–4,2,2 | -3.4060 | 27.24 | 0.34$\pm$0.11 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 84481.506 | 4,0,4–3,0,3 | -4.2069 | 425.96 | 0.044$\pm$0.017 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 85021.4563 | 4,2,2–3,2,1 | -4.3431 | 437.74 | 0.031$\pm$0.012 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 87728.805 | 4,1,3–3,1,2 | -4.2066 | 429.27 | 0.042$\pm$0.016 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 102051.892 | 5,1,5–4,1,4 | -3.9736 | 433.45 | 0.06$\pm$0.03 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 105392.39 | 5,0,5–4,0,4 | -3.9246 | 431.02 | 0.07$\pm$0.03 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 105890.6281 | 5,2,4–4,2,3 | -4.0129 | 442.80 | 0.05$\pm$0.02 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 106023.1054 | 5,4,2–4,4,1 | -4.4307 | 478.01 | 0.0201$\pm$0.008 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 106023.1303 | 5,4,1–4,4,0 | -4.4307 | 478.012 | 0.0201$\pm$0.008 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 106049.2003 | 5,3,3–4,3,2 | -4.1509 | 457.48 | 0.039$\pm$0.015 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 106056.0192 | 5,3,2–4,3,1 | -4.1509 | 457.48 | 0.039$\pm$0.015 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 106448.387 | 5,2,3–4,2,2 | -4.0084 | 442.85 | 0.05$\pm$0.02 |
| HC(O)NH$_{2}$, $v_{12}$=1 | 109604.533 | 5,1,4–4,1,3 | -3.9129 | 434.54 | 0.07$\pm$0.03 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 84390.6787 | 4,0,4–3,0,3 | -3.6117 | 10.14 | 0.025$\pm$0.002 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 105260.2704 | 5,0,5–4,0,4 | -3.3296 | 15.19 | 0.037$\pm$0.003 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 105803.157 | 5,2,4–4,2,3 | -3.4173 | 26.85 | 0.029$\pm$0.003 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 105947.1307 | 5,4,2–4,4,1 | -3.8344 | 61.67 | 0.010$\pm$0.001 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 105947.1608 | 5,4,1–4,4,0 | -3.8344 | 61.67 | 0.010$\pm$0.001 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 106411.1376 | 5,2,3–4,2,2 | -3.4123 | 26.90 | 0.029$\pm$0.003 |
| H$^{13}$C(O)NH$_{2}$, $v$=0 | 109656.8289 | 5,1,4–4,1,3 | -3.3163 | 18.70 | 0.036$\pm$0.003 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 85938.962 | 10,1,10,0–9,1,9,0 | -4.5727 | 28.64 | 0.083$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 86680.19 | 10,0,10,0–9,0,9,0 | -4.5525 | 22.88 | 0.088$\pm$0.012 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 86686.556 | 10,0,0,1–9,0,0,1 | -4.5697 | 34.97 | 0.080$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 86780.778 | 10,2,9,0–9,2,8,0 | -4.6038 | 46.73 | 0.070$\pm$0.009 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 86805.027 | 10,2,8,0–9,2,7,0 | -4.6035 | 46.74 | 0.070$\pm$0.009 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 87016.078 | 10,2,0,1–9,2,0,1 | -4.6219 | 58.81 | 0.063$\pm$0.008 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 87114.738 | 10,0,0,2–9,0,0,2 | -4.6289 | 75.86 | 0.057$\pm$0.007 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 87116.22 | 9,3,0,1–8,3,0,1 | -4.83 | 84.85 | 0.034$\pm$0.004 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 87153.379 | 10,1,0,2–9,1,0,2 | -4.6418 | 81.82 | 0.054$\pm$0.007 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 87281.104 | 10,-2,–,1–9,-2,–,1 | -4.6219 | 58.83 | 0.063$\pm$0.008 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 87592.56 | 10,-1,–,0–9,-1,–,0 | -4.7237 | 143.73 | 0.033$\pm$0.004 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 94529.761 | 11,1,11,0–10,1,10,0 | -4.4541 | 33.18 | 0.097$\pm$0.013 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95115.214 | 11,3,8,0–10,3,7,0 | -4.5445 | 81.09 | 0.062$\pm$0.008 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95115.214 | 11,3,9,0–10,3,8,0 | -4.5445 | 81.09 | 0.062$\pm$0.008 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95455.814 | 11,2,10,0–10,2,9,0 | -4.4828 | 51.31 | 0.082$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95488.131 | 11,2,9,0–10,2,8,0 | -4.4825 | 51.32 | 0.0822$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95765.763 | 11,-1,0,2–10,-1,0,2 | -4.5232 | 86.39 | 0.063$\pm$0.008 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95826.264 | 10,3,0,1–9,3,0,1 | -4.6883 | 89.02 | 0.042$\pm$0.005 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 95958.329 | 11,1,–,-3–10,1,–,-3 | -4.6064 | 149.20 | 0.038$\pm$0.004 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 96120.05 | 11,2,0,3–10,2,0,3 | -4.6492 | 166.01 | 0.032$\pm$0.003 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 96120.05 | 11,2,–,-3–10,2,–,-3 | -4.6504 | 166.87 | 0.032$\pm$0.003 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 96253.318 | 11,1,10,0–10,1,9,0 | -4.439 | 33.68 | 0.098$\pm$0.013 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 96328.605 | 11,2,0,4–10,2,0,4 | -4.7763 | 253.64 | 0.0155$\pm$0.0015 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 96328.605 | 11,2,0,4–10,2,0,4 | -4.7763 | 253.64 | 0.0155$\pm$0.0015 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 102819.142 | 12,-1,–,1–11,-1,–,1 | -4.3571 | 50.45 | 0.102$\pm$0.013 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 103022.546 | 12,1,0,1–11,1,0,1 | -4.3571 | 50.45 | 0.102$\pm$0.013 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 103119.703 | 12,1,12,0–11,1,11,0 | -4.347 | 38.13 | 0.111$\pm$0.015 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104130.01 | 12,2,11,0–11,2,10,0 | -4.3741 | 56.31 | 0.095$\pm$0.012 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104171.962 | 12,2,10,0–11,2,9,0 | -4.3737 | 56.32 | 0.095$\pm$0.012 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104424.13 | 12,2,0,1–11,2,0,1 | -4.3921 | 68.39 | 0.085$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104470.566 | 12,-1,–,2–11,-1,–,2 | -4.4162 | 91.39 | 0.072$\pm$0.009 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104532.714 | 12,0,0,2–11,0,0,2 | -4.4046 | 85.43 | 0.076$\pm$0.009 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104535.872 | 11,3,0,1–10,3,0,1 | -4.563 | 93.60 | 0.051$\pm$0.006 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104671.232 | 12,0,0,3–11,0,0,3 | -4.4943 | 147.16 | 0.046$\pm$0.005 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104679.971 | 12,1,–,-3–11,1,–,-3 | -4.4994 | 154.24 | 0.044$\pm$0.005 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104793.013 | 12,-3,–,2–11,-3,–,2 | -4.5102 | 139.05 | 0.046$\pm$0.005 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104842.449 | 12,-2,–,1–11,-2,–,1 | -4.3921 | 68.41 | 0.085$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 104998.886 | 12,1,11,0–11,1,10,0 | -4.3321 | 38.72 | 0.113$\pm$0.015 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 105132.553 | 12,-1,–,3–11,-1,–,3 | -4.4982 | 153.39 | 0.044$\pm$0.005 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 111634.362 | 13,1,0,1–12,1,0,1 | -4.2599 | 55.86 | 0.115$\pm$0.015 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 111708.707 | 13,1,13,0–12,1,12,0 | -4.2498 | 43.49 | 0.12$\pm$0.02 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 112395.756 | 13,3,10,0–12,3,9,0 | -4.3315 | 91.50 | 0.08$\pm$0.01 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 112395.756 | 13,3,11,0–12,3,10,0 | -4.3315 | 91.50 | 0.08$\pm$0.01 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 112803.258 | 13,2,12,0–12,2,11,0 | -4.2755 | 61.73 | 0.107$\pm$0.014 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 113129.051 | 13,2,0,1–12,2,0,1 | -4.2935 | 73.80 | 0.096$\pm$0.012 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 113591.533 | 13,2,0,3–12,2,0,3 | -4.4417 | 176.42 | 0.041$\pm$0.004 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 113591.533 | 13,2,–,-3–12,2,–,-3 | -4.443 | 177.28 | 0.041$\pm$0.004 |
| CH$_{3}$NCO, $v_{\rm b}$=0 | 113631.453 | 13,-2,–,1–12,-2,–,1 | -4.2935 | 73.83 | 0.096$\pm$0.012 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 85948.138 | 10,-1,–,1–9,-1,–,1 | -4.9638 | 304.20 | 0.028$\pm$0.014 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 86624.236 | 10,0,0,1–9,0,0,1 | -4.9509 | 298.28 | 0.030$\pm$0.015 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 86674.929 | 10,0,10,0–9,0,9,0 | -4.932 | 285.04 | 0.034$\pm$0.017 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 87105.592 | 10,0,–,-2–9,0,–,-2 | -5.0152 | 342.76 | 0.018$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 87139.46 | 10,-1,–,-2–9,-1,–,-2 | -5.0282 | 348.72 | 0.017$\pm$0.011 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 87535.51 | 10,1,9,0–9,1,8,0 | -4.9372 | 291.21 | 0.032$\pm$0.016 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 95335.299 | 11,0,11,0–10,0,10,0 | -4.8142 | 289.62 | 0.04 $\pm$.02 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 95539.843 | 11,2,9,0–10,2,8,0 | -4.8627 | 313.46 | 0.029$\pm$0.016 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 102699.98 | 12,3,10,0–11,3,9,0 | -4.813 | 348.16 | 0.024$\pm$0.015 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 102699.98 | 12,3,9,0–11,3,8,0 | -4.813 | 348.16 | 0.024$\pm$0.015 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 103108.301 | 12,1,12,0–11,1,11,0 | -4.7267 | 300.28 | 0.04$\pm$0.02 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 103765.305 | 12,0,0,1–11,0,0,1 | -4.7266 | 307.84 | 0.04$\pm$0.02 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 103993.608 | 12,0,12,0–11,0,11,0 | -4.7078 | 294.61 | 0.04$\pm$0.02 |
| CH$_{3}$NCO, $v_{\rm b}$=1 | 111696.508 | 13,1,13,0–12,1,12,0 | -4.6294 | 305.64 | 0.05$\pm$0.02 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 93071.391 | 11,2,0,1–10,2,0,1 | -4.5009 | 63.27 | 0.0086 0.0013 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 93405.042 | 11,-3,–,-2–10,-3,–,-2 | -4.6222 | 133.93 | 0.0046$\pm$0.0007 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 93458.719 | 11,2,0,3–10,2,0,3 | -4.6492 | 165.88 | 0.0037$\pm$0.0006 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 93458.822 | 11,2,0,3–10,2,0,3 | -4.6504 | 166.74 | 0.0037$\pm$0.0006 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 93577.977 | 11,1,10,0–10,1,9,0 | -4.439 | 33.55 | 0.0114$\pm$0.0018 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 100201.619 | 12,1,0,1–11,1,0,1 | -4.3571 | 50.32 | 0.0119$\pm$0.0018 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 100942.013 | 12,3,9,0–11,3,8,0 | -4.4325 | 85.95 | 0.0083$\pm$0.0013 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 100942.013 | 12,3,10,0–11,3,9,0 | -4.4325 | 85.95 | 0.0083$\pm$0.0013 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 101894.392 | 12,-3,–,-2–11,-3,–,-2 | -4.5102 | 138.91 | 0.0053 $\pm$0.0008 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 108406.444 | 13,2,–,-2–12,2,–,-2 | -4.3527 | 114.44 | 0.0081$\pm$0.0013 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 108575.945 | 13,1,0,1–12,1,0,1 | -4.2599 | 55.72 | 0.013$\pm$0.002 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 108639.42 | 13,1,13,0–12,1,12,0 | -4.2498 | 43.34 | 0.015$\pm$0.002 |
| $^{13}$CH$_{3}$NCO, $v_{\rm b}$=0 | 109304.924 | 13,0,0,1–12,0,0,1 | -4.2487 | 49.79 | 0.014$\pm$0.002 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 86161.9164 | 19,14,6–19,13,7 | -4.9115 | 177.62 | 0.006$\pm$0.004 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 88256.3587 | 13,4,9–13,3,10 | -5.1006 | 74.48 | 0.004$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 89977.0936 | 17,8,9–17,7,10 | -4.8582 | 130.04 | 0.007$\pm$0.004 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 94017.835 | 16,14,3–16,13,4 | -5.0692 | 136.42 | 0.004$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 97943.8728 | 9,0,9–8,1,8 | -4.6386 | 24.49 | 0.011$\pm$0.007 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 97943.8739 | 9,1,9–8,1,8 | -5.8455 | 24.49 | 0.0007$\pm$0.0005 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 97943.8816 | 9,0,9–8,0,8 | -5.8455 | 24.49 | 0.0007$\pm$0.0005 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 97943.8828 | 9,1,9–8,0,8 | -4.6386 | 24.49 | 0.011$\pm$0.007 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 100405.9333 | 23,13,10–23,12,11 | -4.8242 | 243.83 | 0.007$\pm$0.004 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 103515.4785 | 23,17,6–23,16,7 | -4.8556 | 258.25 | 0.006$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108190.1973 | 10,0,10–9,1,9 | -4.5115 | 35.74 | 0.013$\pm$0.009 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108190.1975 | 10,1,10–9,1,9 | -5.9118 | 35.74 | 0.0005$\pm$0.0003 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108190.1993 | 10,0,10–9,0,9 | -5.9118 | 35.74 | 0.0005$\pm$0.0003 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108190.1996 | 10,1,10–9,0,9 | -4.5115 | 35.74 | 0.013$\pm$0.009 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108255.2324 | 10,0,10–9,1,9 | -4.5097 | 29.68 | 0.013$\pm$0.009 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108255.2325 | 10,1,10–9,1,9 | -5.7188 | 29.68 | 0.0008$\pm$0.0005 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108255.2335 | 10,0,10–9,0,9 | -5.7188 | 29.68 | 0.0008$\pm$0.0005 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 108255.2336 | 10,1,10–9,0,9 | -4.5097 | 29.68 | 0.013$\pm$0.009 |
| CH$_{3}$C(O)NH$_{2}$, $v$=0 | 109024.8757 | 22,13,10–22,12,11 | -4.8380 | 222.25 | 0.006$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 86858.4501 | 11,3,8–11,2,9 | -5.1832 | 84.12 | 0.003$\pm$0.002 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 87178.4897 | 8,4,5–7,4,4 | -5.1062 | 88.30 | 0.004$\pm$0.0038 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 87286.7553 | 8,3,5–7,3,4 | -5.0846 | 87.87 | 0.004$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 92337.5385 | 8,1,7–7,1,7 | -5.0641 | 85.46 | 0.004$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 95161.9961 | 9,8,1–9,8,2 | -5.1689 | 92.62 | 0.003$\pm$0.002 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 98960.6476 | 8,2,6–7,2,5 | -4.9910 | 87.28 | 0.005$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 99191.9445 | 9,1,9–8,0,8 | -4.6669 | 58.50 | 0.010$\pm$0.007 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 101612.5722 | 12,10,2–12,10,3 | -4.9402 | 121.72 | 0.005$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 108074.6337 | 14,12,3–14,11,4 | -4.8381 | 146.88 | 0.006$\pm$0.004 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 110000.2604 | 10,1,9–9,2,8 | -4.6286 | 95.56 | 0.010$\pm$0.006 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=1 | 110000.8655 | 13,8,5–13,7,7 | -5.7590 | 118.19 | 0.0007$\pm$0.0005 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=2 | 85735.8766 | 16,8,8–16,8,9 | -5.1089 | 229.90 | 0.004$\pm$0.002 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=2 | 103232.6376 | 16,9,7–16,9,8 | -4.9038 | 239.40 | 0.005$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=2 | 103790.5952 | 9,0,9–8,0,8 | -4.8414 | 139.75 | 0.006$\pm$0.004 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=2 | 106117.5341 | 16,5,11–16,4,12 | -4.8027 | 198.22 | 0.007$\pm$0.004 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=2 | 109284.7294 | 11,5,7–11,4,8 | -4.9046 | 144.84 | 0.005$\pm$0.003 |
| CH$_{3}$C(O)NH$_{2}$, $v_{\rm t}$=2 | 114811.2701 | 20,7,13–20,6,14 | -4.7166 | 264.28 | 0.007$\pm$0.004 |
| CH$_{3}$NHCHO,$v$=0 | 89031.2613 | 8,2,7–7,2,6 | -4.9300 | 22.13 | 0.002$\pm$0.001 |
| CH$_{3}$NHCHO,$v$=0 | 89034.2847 | 20,4,16–20,3,17 | -5.0052 | 131.00 | 0.0020$\pm$0.0008 |
| CH$_{3}$NHCHO,$v$=0 | 90764.7877 | 8,6,3–7,6,2 | -5.2730 | 44.28 | 0.0011$\pm$0.0004 |
| CH$_{3}$NHCHO,$v$=0 | 90764.8105 | 8,6,2–7,6,1 | -5.2730 | 44.28 | 0.0011$\pm$0.0004 |
| CH$_{3}$NHCHO,$v$=0 | 91888.7598 | 8,2,6–7,2,5 | -4.9222 | 27.17 | 0.002$\pm$0.001 |
| CH$_{3}$NHCHO,$v$=0 | 93406.3797 | 9,0,9–8,0,8 | -4.8163 | 23.10 | 0.0030$\pm$0.0012 |
| CH$_{3}$NHCHO,$v$=0 | 102434.8736 | 9,5,4–8,5,3 | -4.9138 | 41.68 | 0.0022$\pm$0.0009 |
| CH$_{3}$NHCHO,$v$=0 | 104818.4432 | 28,6,22–28,5,23 | -4.7632 | 251.09 | 0.0029$\pm$0.0012 |
| CH$_{3}$NHCHO,$v$=0 | 106004.4774 | 23,4,19–23,3,20 | -4.8749 | 167.88 | 0.0022$\pm$0.0009 |
| CH$_{3}$NHCHO,$v$=0 | 107852.5468 | 9,2,7–8,2,6 | -4.7119 | 28.22 | 0.0033$\pm$0.0013 |
| CH$_{3}$NHCHO,$v$=0 | 112875.4833 | 11,0,11–10,0,10 | -4.5701 | 37.13 | 0.0044$\pm$0.0018 |

: Continued.

**Note.** $^{a}$For all the molecules the levels are indicated as ($J$, $K_{\rm a}$, $K_{\rm c}$), except for HN$^{13}$CO for which also the hyperfine state is indicated, ($J$, $K_{\rm a}$, $K_{\rm c}$, $F$), and for CH$_{3}$NCOand $^{13}$CH$_{3}$NCO for which the levels are labelled as ($J$, $K_{\rm a}$, $K_{\rm c}$, $m$). The quantum numbers $m$ or $K_a$ may carry a sign; in the latter case, $K_c$ is not reported and we indicated it as $K_{\rm c}$= "–".

# Tentative detections

In this Appendix we show the transitions used for the fit of the $v_{4}$=1 and $v_{5}$=1 states of HNCO, of H$^{15}$NCO, and of $^{13}$CH$_{3}$NCO.

![](GUAPOSIA-va-usedfinal.eps)

![](GUAPOSIA-vb-usedfinal.eps)

![](GUAPOSIA15N-usedfinal.eps)

![](GUAPOSMI13C-usedfinal.eps)

# Full GUAPOS spectrum

In this Appendix we show the total observed spectra with the best LTE fit of the molecular species studied in this work. Moreover, the synthesised spectrum taking into account the contribution of all the possible molecular species is also shown.

![](GUAPOSfull-apr2021-all_5.pdf)

![](GUAPOSfull-apr2021-all_11.pdf)

![](GUAPOSfull-apr2021-all_17.pdf)

![](GUAPOSfull-apr2021-all_23.pdf)

![](GUAPOSfull-apr2021-all_29.pdf)

![](GUAPOSfull-apr2021-all_35.pdf)

![](GUAPOSfull-apr2021-all_41.pdf)

![](GUAPOSfull-apr2021-all_47.pdf)

![](GUAPOSfull-apr2021-all_53.pdf)

![](GUAPOSfull-apr2021-all_59.pdf)

![](GUAPOSfull-apr2021-all_65.pdf)

![](GUAPOSfull-apr2021-all_71.pdf)

![](GUAPOSfull-apr2021-all_77.pdf)

![](GUAPOSfull-apr2021-all_83.pdf)

![](GUAPOSfull-apr2021-all_89.pdf)

[^1]: STATCONT is freely accessible here: <https://hera.ph1.uni-koeln.de/~sanchez/statcont>.

[^2]: Madrid Data Cube Analysis on ImageJ is a software developed at the Center of Astrobiology (CAB) in Madrid; <http://cab.intacsic.es/madcuba/Portada.html>.

[^3]: <http://cdms.astro.uni-koeln.de/classic/>.

[^4]: <https://spec.jpl.nasa.gov/ftp/pub/catalog/catdir.html>.

[^5]: https://casa.nrao.edu

[^6]: It is a doublet transition that is not resolved in frequency because the line width ($\sim$8 km s$^{-1}$) is higher than the spectral separation between the two lines (1.8$\times$10$^{-3}$ km s$^{-1}$ at 219.656 GHz).

[^7]: <http://cdms.astro.uni-koeln.de/classic/>.

[^8]: <https://spec.jpl.nasa.gov/ftp/pub/catalog/catdir.html>.

</paper>

Write the methods card for this paper.