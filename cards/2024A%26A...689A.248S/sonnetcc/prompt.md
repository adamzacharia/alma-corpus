# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.248S\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.248S",
 "title": "SO<SUB>2</SUB> and OCS toward high-mass protostars: A comparative study of ice and gas",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Santos, Julia C.",
 "n_authors": 5,
 "arxiv_id": "2407.14711",
 "doi": "10.1051/0004-6361/202450736",
 "alma_projects_linked_by_archive": [
  "2019.1.00195.L"
 ]
}
```

Paper text:
<paper>
#  and toward high-mass protostars

and are both major carriers of gaseous sulfur and are the only sulfurated molecules detected in interstellar ices to date. They are thus the ideal candidates to explore the evolution of the volatile sulfur content throughout the different stages of star formation.

We aim to investigate the chemical history of interstellar and by deriving a statistically-significant sample of gas-phase column densities towards massive protostars and comparing to observations of gas and ices towards other sources spanning from dark clouds to comets.

We analyze a subset of 26 line-rich massive protostars observed by ALMA in Band 6 as part of the High Mass Protocluster Formation in the Galaxy (ALMAGAL) survey. Column densities are derived for and from their rare isotopologues and towards the compact gas around the hot cores. We compare the abundance ratios of gaseous , , and with ice detections towards both high- and low-mass sources as well as dark clouds and comets.

We find that gas-phase column density ratios of and with respect to methanol remain fairly constant as a function of luminosity between low- and high-mass sources, despite their very different physical conditions. In our dataset, and are weakly correlated. The derived gaseous and abundances relative to are overall similar to protostellar ice values, with a significantly larger scatter for than for . Cometary and dark-cloud ice values agree well with protostellar gas-phase ratios for , whereas higher abundances of are generally seen in comets compared to the other sources. Gaseous / ratios are consistent with ices toward dark clouds, protostars, and comets, albeit with some scatter.

The constant gas-phase column density ratios throughout low and high-mass sources indicate an early stage formation before intense environmental differentiation begins. Icy protostellar values are similar to the gas phase medians, compatible with an icy origin of these species followed by thermal sublimation. The larger spread in compared to ratios w.r.t. is likely due to a more water-rich chemical environment associated with the former, as opposed to a -rich origin of the latter. Post-sublimation gas-phase processing of can also contribute to the large spread. Comparisons to ices in dark clouds and comets point to a significant inheritance of from earlier to later evolutionary stages.

# Introduction

Over 240 molecules have been detected in the interstellar medium to date, among which at least 30 contain one or more sulfur atoms (cite: McGuire2022). With an abundance of S/H$\sim$1.35$\times$10$^{−5}$, sulfur is one of the most common elements in space (cite: Asplund2009). Indeed, S-bearing species are observed in the gas phase throughout most stages of star and planet formation, from diffuse and dense clouds (e.g., (cite: Drdla1989; Navarro-Almaida2020; Spezzano2022; Esplugues2022)) and protostars (e.g., (cite: Blake1987; Blake1994; vanderTak2003; Li2015; Drozdovskaya2018; Codella2021; delaVillarmois2023; Fontani2023; Kushwahaa2023)) to protoplanetary disks (cite: Fuente2010; Phuong2018; Semenov2018; LeGal2019; Riviere-Marichalar2021; LeGal2021; Booth2024). They have also been detected in solar system bodies such as comets (cite: Smith1980; Bockelee-Morvan2000; Biver2021a; Biver2021b; Calmonte2016; Altwegg2022), planets (cite: Moullet2013), and satellites (cite: Hibbitts2000; Jessup2007; Moullet2008; Cartwright2020), as well as towards extragalactic sources (cite: Henkel1985; Petuchowski1992; Mauersberger1995; Heikkila1999; Martin2003; Martin2005). Identified species range from simple diatomic molecules such as and to the complex organics methanethiol () and ethanethiol () (cite: Linke1979; Gibb2000; Cernicharo2012; Koleniskova2014; Zapata2015; Muller2016; Majumdar2016; Rodriguez-Almeida2021).

Despite this widespread detection, derived abundances in dense starless cores, protostars, and protoplanetary disks can only account for up to a few percent of the total expected cosmic value (cite: Tieftrunk1994; Wakelam2004; Anderson2013; Vastel2018; Fuente2019; LeGal2019; RiviereMarichalar2019; Riviere-Marichalar2020; LeGal2021; Bouscasse2022; Fuente2023). The bulk of the sulfur content is largely thought to be locked away in or underneath the ice mantles that shroud interstellar dust grains, in a state that challenges its detection. Such icy mantles start to form early in the interstellar evolutionary sequence, during the so-called translucent-cloud phase. Atoms of and adsorb onto dust grains and react to form , resulting in a water-rich ice layer (cite: Tielens1982; Hiraoka1998; Mokrane2009; Dulieu2010; Ioppolo2010; Cuppen2010; Romanzin2011; Oberg2011). As the density of the collapsing cloud increases, carbon monoxide () molecules present in the gas phase catastrophically freeze-out on top of the water-rich ice, forming a second coating known as the CO-rich ice layer (cite: Tielens1991; Boogert2002; Pontoppidan2003; Pontoppidan2006; Oberg2011). This ice is efficiently converted into methanol () by reactions involving atoms (cite: Tielens1982; Charnley1992; Hiraoka1994; Watanabe2002; Fuchs2009; Cuppen2009; Santos2022). Complementarily, some smaller contribution to formation from ice chemistry in less dense environments, before the catastrophic CO freeze-out, is also often invoked (e.g., (cite: Wada2006; Hodyss2009; Oberg2010; Bergner2017; Lamberts2017; Qasim2018)), although it is likely not dominant.

Eventually, the environment close to the emerging young stellar object is warmed up to temperatures of $100-300$ K, resulting in the complete thermal sublimation of the ices. This chemically-rich region surrounding the protostar is known as hot core for massive sources or hot corino for low-mass counterparts (e.g., (cite: Herbst2009)), and is thought to be representative of the bulk ice content. For simplicity, we henceforth utilize “hot core” as an umbrella term for both high- and low-mass sources. By studying the compact emission originated from the hot core in comparison to ice observations, it is possible to gain insight into the formation and destruction mechanisms of molecules both in the gas and in the solid phases.

Compared to gaseous species, the unambiguous detection of solid-state molecules embedded in interstellar ices poses significantly more challenges. Spectral features of species in the solid phase are intrinsically broad and highly degenerate, with properties such as peak position and width that vary considerably with the ice environment. Likely as a consequence of such inherent limitations, only two sulfur-bearing species have been identified in ices so far: carbonyl sulfide () and sulfur dioxide (). The former was first detected by (cite: Palumbo1995) towards the massive protostar W33A. Soon after, (cite: Boogert1997) suggested the presence of the latter towards both W33A and NGC 7538:IRS1—another massive young stellar object (MYSO). Since then, both species have been either inferred or detected in ices towards other protostars as well as dark clouds (cite: Palumbo1997; Oberg2008; Zasowski2009; Yang2022; Boogert2022; McClure2023; Rocha2024). Recently, the presence of ice was confirmed by JWST observations towards the solar-type protostar IRAS 2A by constraining the contribution of blended species, in particular , to its 7.6 $\mu$m region (cite: Rocha2024).

In the gas phase, both species are commonly detected. Gaseous is observed towards protostellar systems both through its pure rotational transitions occurring at submillimeter wavelengths and through its rovibrational lines probed by the mid-infrared (cite: Keane2001; Dungee2018; Nickerson2023; vanGelder2024). It is a good tracer of outflows, jets, and accretion shocks due to its enhanced gas-phase formation at high temperatures ($T\gtrsim$100 K) combined with either sputtering or thermal sublimation of or its precursors from icy dust grains (cite: Pineau1993; Sakai2014; Oya2019; Taquet2020; Tychoniec2021; vanGelder2021). It has also been shown to trace disk winds (cite: Tabone2017). While this is the case for the main isotopologue (i.e., ), the emission of minor isotopologues such as is expected to be mostly compact, tracing the hot core region. Moreover, in contrast to , gaseous emission is not expected to have significant contributions from outflows (cite: vanderTak2003; Drozdovskaya2018), tracing predominately the envelope surrounding protostars (e.g., (cite: Herpin2009; Oya2016)). Being the only two sulfurated molecules detected in both gas and ices, and are the ideal targets to perform a comparative study between these two physical states.

In this work we explore the origin and fate of two of the most abundant sulfur species, and , by directly comparing their solid and gaseous components during the evolution of star forming regions. We utilize data from the ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy (ALMAGAL) survey and select a subsample of 26 line-rich sources to perform the analysis, representing the first interferometric study on a statistically significant sample of detections for these two molecules in the gas. The molecular column densities are derived from the rare isotopologues and to avoid contamination from extended emission, outflows, and to limit line optical depth effects. We thus focus on the hot core region, which contains the molecular reservoir from the ices after complete thermal sublimation. Their ratios are compared to other observations in the solid and the gas phases taken from the literature. This includes recent works that utilize ground-based infrared observatories to investigate ice abundances (among other species) in a large sample of MYSOs (cite: Boogert2022), as well as space observations by the *James Webb* Space Telescope (JWST) of both and ices towards sources ranging from background stars to protostars (cite: McClure2023; Rocha2024). This study sets the stage for future gas and ice works enabled by the combination of data from the Atacama Large Millimeter/submillimeter Array (ALMA) and JWST on both low- and high-mass protostars, paving the way to a more thorough understanding of the sulfur chemical evolution of the interstellar medium.

In Section [2](#sec:observations) we describe the observational parameters and details of the dataset, as well as the procedure to fit a synthetic spectrum to the lines of interest. The resulting emission morphologies, kinematics, and column densities are presented in Section [3](#sec:results). The column density ratios with respect to methanol are discussed in Section [4](#sec:discussion) in comparison to other observations. Finally, our main findings are summarized and concluded in Section [5](#sec:conc).

# Observations and methods

## The observations

The ALMAGAL survey (2019.1.00195.L; PIs: P. Schilke, S. Molinari, C. Battersby, P. Ho) was observed by ALMA in Band 6 ($\sim$1 mm). It targeted over 1000 dense clumps across the Galaxy with $M>500$ M$_\odot$ and $d<7.5$ kpc, chosen based on the Herschel infrared Galactic Plane Survey (Hi-GAL) (cite: Molinari2010; Elia2017; Elia2021). ALMAGAL covers a statistically significant sample of sources in all stages of star formation, with many of them consisting of MYSOs. For this work we consider only archival data made publicly available before February 2021, with beam sizes between 0.5$''$ and 1.5$''$ ($\sim$1000–5000 au). The Common Astronomy Software Applications[^1] (CASA; (cite: McMullin2007)) version 5.6.1. was used to pipeline calibrate and image the data. The selection of sources was based on a subset studied in both (cite: Nazari2022) and (cite: vanGelder2022), thus culling for particularly line-rich sources for which the column densities—our benchmark for comparison—are well constrained. In (cite: vanGelder2022), the selection was based on sources with high bolometric luminosities ($L_{\text{bol}}>1000$ $L_\odot$) where complex organic molecules (COMs) such as and were detected. In (cite: Nazari2022), the selection criterium consisted of sources that contain the $12_7-11_7$ line above the $2.5-3\sigma$ level. Within this subset commonly pertaining to both studies, we exclude sources for which the line profiles of the targeted molecules differed significantly across species, to avoid probing distinct emitting regions. An example case of an excluded source is shown in Appendix [6](#appendix:bad_source). The final subset consists of 26 line-rich sources, whose properties and observational parameters are listed in Appendix [7](#appendix:source_stuff).

In this work we make use of two out of the four spectral windows in ALMAGAL, encompassing frequencies of $\sim$217.00$-$218.87 GHz and $\sim$219.07$-$220.95 GHz with a spectral resolution of $\sim$0.5 MHz ($\sim$0.7 km s$^{-1}$). The spectral windows cover 4 transitions of , 11 transitions of , and 1 transition of with upper energy $E_{\text{up}}<800$ K and Einstein $A_{\text{ij}}>1\times10^{-6}$ s$^{-1}$ (see Appendix [8](#appendix:transitions)). However, only the $11_{1,11}-10_{0,10}$ transitions of and were detected in our sources (E$_{\text{up}}$ = 60.1 K and 57.9 K, respectively). For , this corresponds to only one line, whereas for it encompasses 7 hyperfine components caused by the nuclear spin $I=3/2$ of the atom. The remaining and lines are rather weak ($A_{ij}<2.6\times10^{-5}$ s$^{-1}$) and for the most part highly blended, hampering their detections. is detected in its $18-17$ transition (E$_{\text{up}}$ = 99.5 K). No other isotopologues of , including , are covered in the ALMAGAL range. One line of is covered, but it is not included in this work due to its likely contamination from outflow emission and because it is probably optically thick.

The spectra utilized in this work are the same as in (cite: vanGelder2022). For all sources with the $8_{0,8}-7_{1,6}$ line ($E_{\text{up}}=97$ K) above the $3\sigma$ level, the spectra were extracted from the peak pixel for this line in the integrated intensity maps. This particular transition of was chosen because it is the strongest methanol line within the sample with $E_{\text{up}}>70$ K, to avoid contamination by the outflow or extended emission that are probed by lines with lower $E_{\text{up}}$. The choice of extracting the spectra from the methanol peak intends to maximize the signal-to-noise ratio of both and originating from the hot core region. In G023.3891p00.1851, the peak emission of the methanol isotopologue is offset by $\sim0.6\ensuremath{''}$ (approximately half a beam) from that of , and thus the $17_{1,16}e_0-17_{0,17}e_0$ ($E_{\text{up}}=336$ K) peak is chosen to extract the spectrum since it is a more reliable tracer of the hot core. All sources probed here show line widths of $\gtrsim3$ km s$^{-1}$, well above the spectral resolution of $\sim0.7$ km s$^{-1}$, and the spectral sensitivity corresponds to $\sim0.2$ K (for a list of rms values see Appendix [7](#appendix:source_stuff)).

## Spectral analysis

The target molecules of this study are and , the two sulfur-bearing species detected in both gas and ices so far. We analyze them by means of their rare isotopologues and in order to avoid issues with optically-thick lines and contamination from extended emission and outflows. The emission is also analyzed as a diagnostic tool to assess whether or not is indeed optically thin (Section [3.3](#subsec:34SO2_opt_thick)). We utilize the CASSIS[^2] spectral analysis tool (cite: Vastel2015) to fit the spectrum for each source and derive each species’ column density ($N$) and full width at half maximum (FWHM) assuming that the excitation is under local thermodynamic equilibrium (LTE). Since we only detect one line per species per source, the excitation temperature is fixed to $T_{\text{ex}}=150$ K in the spectral fittings—a roughly averaged value for hot cores (see, e.g., (cite: vanGelder2020; Yang2021; Nazari2022)). Fixing the $T_{\text{ex}}$ to $60-250$ K only changes the derived column densities by up to a factor of $\sim$ 3, and both molecules in the same direction. Furthermore, for $\gtrsim80\%$ of the sources in this work, excitation temperatures derived from lines range between $120 - 170$ K (cite: Nazari2022), corresponding to only up to a factor of 1.6 difference in column densities for and . Thus, the assumption of a fixed $T_{\text{ex}}=150$ K does not interfere significantly with the column density ratios—the main focus of this work. The spectroscopic properties employed in the fittings of each species are obtained from the Cologne Database for Molecular Spectroscopy (CDMS; (cite: Muller2001; Muller2005)).

The and lines analyzed in this work are mostly unblended, which allows the utilization of the grid fitting method as explained in detail previously (cite: vanGelder2020; Nazari2021; Chen2023). In summary, a grid of column densities and FWHMs is tested and the best fit model is assigned to the combination with the lowest $\chi ^2$. In this work $N$ was varied from $1\times10^{13}$ cm$^{−2}$ to $1\times10^{17}$ cm$^{−2}$ with a step of 0.1 on a logarithmic scale, and the FWHM was varied from 3 km s$^{−1}$ to 11 km s$^{−1}$ with a spacing of 0.1 km s$^{−1}$ on a linear scale. The radial velocities ($V_{\text{lsr}}$) are derived by eye using increments of 0.1 km s$^{-1}$ in a similar manner as described in (cite: Nazari2022) and (cite: Chen2023), and are fixed to the best manually-derived values for the grid fits. Their median offsets are of 0.35 km s$^{-1}$ from the velocities for in the same sources (see Section [3.2](#subsec:fitting_results)). The $2\sigma$ errors are derived from the reduced $\chi ^2$ calculated from the comparison between the resulting model of each grid point and the observed spectrum. If the $2\sigma$ uncertainties of the column densities are smaller than 20%, we assume a 20% uncertainty as a conservative estimate to account for systematic sources of errors. In some few instances, such as for in 693050, more severe blending or deviations from a Gaussian profile are observed (see Appendix [9](#appendix:best_models)). Nonetheless, the integrated line emissions are still encompassed by our models well within the adopted conservative uncertainties, and thus it does not affect our analysis. In the cases of G025.6498p01.0491 for , and 126348 and 707948 for , the emission is better described by two components (see Appendix [9](#appendix:best_models)). However, obtaining column density ratios for each velocity component separately is not possible since they are not resolved for methanol. In such cases, we perform the grid fits assuming one Gaussian and fixing the $V_{\text{lsr}}$ to the mean between the values derived by eye for each component. This procedure yields column densities within 20$\%$ of the ones obtained by manually fitting each component separately. Thus, to ensure a systematic approach to the line analysis, we utilize the column densities derived from the grid fittings to these sources. The exact source sizes are not known, so we assume that the source fully fills the beam (i.e., a beam dilution factor of unity). Since this work focuses on comparing column density ratios, this assumption does not interfere with the analysis as long as the lines are optically thin (cite: vanGelder2020; Nazari2021).

Fitting is more challenging. It is considerably less abundant than , and its only detected transitions are blended with . The fitting was thus performed by eye on top of the best models for derived by (cite: Nazari2022). The $V_{\text{lsr}}$ values of were fixed to those of , while its column densities and FWHMs were varied in steps of 0.1 in log space and 0.1 in linear space, respectively. For most sources, barely or no emission was left underfitted after accounting for . In such cases we assign as upper limits. However, for four sources (615590, 644284A, 693050, G343.1261-00.0623) the model underfitted the emission significantly ($\lesssim$50%), in which cases we can derive approximate column densities for .

![](Figures/moment0_maps_subset.pdf)

## Isotope ratio callibration

Isotopic abundances are dependent on the stellar population and therefore vary as a function of the distance to the Galactic center ($D_{\text{GC}}$). In order to obtain accurate column densities of the main and isotopologues, it is thus required to calibrate the isotope ratios of (/), (/), and (/) accordingly. Recently, (cite: Yan2023) utilized lines in a wide variety of isotopologues observed towards 110 high-mass star forming regions to derive the equations: $$\begin{equation}
(^{32}\text{S}/^{34}\text{S}) = (0.73 \pm 0.36)D_\text{GC} + (16.50 \pm 2.07),
\label{eq:32S_34S}
\end{equation}$$

$$\begin{equation}
(^{32}\text{S}/^{33}\text{S}) = (2.64 \pm 0.77)D_\text{GC} + (70.80 \pm 5.57),
\label{eq:32S_33S}
\end{equation}$$

$$\begin{equation}
(^{12}\text{C}/^{13}\text{C}) = (4.77 \pm 0.81)D_\text{GC} + (20.76 \pm 4.61).
\label{eq:12C_13C}
\end{equation}$$

$D_{\text{GC}}$ can be calculated based on the source’s distance to Earth ($d$) and its coordinates. The resulting values for each source are listed in Appendix [7](#appendix:source_stuff) and are used to derive and from the isotopologues. For the solar neighborhood, the ratios are (/)$\sim$22, (/)$\sim$92, and (/)$\sim$59. The uncertainties in the final column densities of and (henceforth simply and ) are obtained by propagating the errors in the derived column densities of the minor isotopologues together with the uncertainties in Equations [\[eq:32S_34S\]](#eq:32S_34S)$-$[\[eq:12C_13C\]](#eq:12C_13C) and the typical error of $\sim$0.5 kpc in D$_\text{GC}$ (see (cite: Nazari2022)).

# Results

## Morphology

The integrated intensity maps of and for 744757A, G318.0489p00.0854B, and G345.5043p00.3480 are presented in Figure [1](#fig:moment0_subset). These are chosen as a representative sample of the sources analyzed in this work. The emission areas of both species are compact (with typical radii of $\sim1000-3000$ au considering all sources) and mostly unresolved, in accordance with the expectation that rare isotopologues likely trace the hot core region with little to no contribution from extended emission. The case of 693050 is an exception in which the and peaks are offset from the continuum peak (as shown by the white star) by $\sim$4000 au (see Appendix [10](#appendix:moment0_693050)). This could be the result of optically thick dust at these wavelengths, leading to continuum oversubstraction or dust attenuation towards the continuum peak, which has been shown to hide molecular emission in prostellar systems (cite: deSimone2020). Indeed, the same behavior is observed for emission in 693050, in line with this hypothesis (cite: vanGelder2022a). Higher spatial resolution is required to fully distinguish the species’ emitting regions. Still, some spatial information can be acquired by comparing their best-fit parameters (see Section [3.2](#subsec:fitting_results)).

![](Figures/34SO2_O13CS_fits_subset.pdf)

## Fitting results

The best-fit parameters of and for all sources are listed in Appendix [11](#appendix:fits), together with the corresponding column densities derived for and . The best-fit models are shown in Figure [2](#fig:fittings_subset) for a set of representative sources: 744757A, G318.0489p00.0854B, and G345.5043p00.3480. The models for the remaining sources are presented in Appendix [9](#appendix:best_models). $3\sigma$ upper limits are provided when line intensities do not surpass this detection threshold. For most sources, the column densities range between $10^{15}-10^{16}$ cm$^{-2}$, which corresponds to column densities of $10^{16}-10^{17}$ cm$^{-2}$. The only exceptions to this trend are the sources for which only $N$() upper limits could be derived.

In comparison, the column densities are roughly one order of magnitude lower, but given the larger ratios of (/) compared to (/), the corresponding $N$() values also range between $10^{16}-10^{17}$ cm$^{-2}$. Absolute column densities are nevertheless subject to biases such as the assumed emitting area and thus are not ideal to be directly compared. Column density ratios are a more reliable form of comparison to provide information on the chemical inventories of different systems. The column densities derived in this work will be discussed in detail in Section [4](#sec:discussion).

Despite the emissions probed here being largely unresolved, line widths and velocities can be utilized to infer the kinematics of the gas. In Appendix [12](#appendix:FWHMs_Vlsrs_wrtCH3OH), we present a comparison between the widths and velocities for both and with respect to . The latter was obtained from the fittings performed by (cite: vanGelder2022). For some sources, (cite: vanGelder2022) did not detect , in which cases we compare to the fitting parameters of the main isotopologue (signaled by empty markers). The median offsets of the line widths and peak velocities between the three different species are, respectively, 0.15 and 0.35 km s$^{-1}$. This is in line with all three molecules tracing a similar compact gas within the hot core region and serves as validation for a comparative analysis of their column density ratios. The fact that no distinctively large discrepancy in FWHM and $V_{\text{lsr}}$ is observed for is an indication that any contribution from outflows to this line can be neglected.

## Is optically thin?

Line emissions from rare isotopologues are usually assumed to be optically thin. However, this is not necessarily always true, especially for abundant species such as . For this reason, we utilize the four sources in which is detected to assess whether is indeed optically thin. Their best-fit parameters are listed in Appendix [13](#appendix:fitting_33SO2). We derive the column densities of (i.e., of the main isotopologue) from both $N$() and $N$() separately, using their isotope ratios as described in Section [2.3](#subsec:isotope_ratios). Figure [3](#fig:SO2_34_33) shows the ratios of column densities derived from over the counterparts for the four sources. The resulting values are all remarkably close to unity, confirming that both the and lines are indeed optically thin. In fact, the larger the $N$()/$N$() ratios (indicated by the red arrow), the closer the values are to unity. Given that the lines had to be fitted on top of (see the discussion in Section [2.2](#subsec:spectral_analysis)), this strongly suggests that the small discrepancies in column densities calculated from $N$() and $N$() are mostly due to being heavily blended.

![](Figures/SO2_34_33.pdf)

# Discussion

As mentioned in Section [3.2](#subsec:fitting_results), column density ratios are a good metric to compare the chemical content of different sources and types of environments. Here we utilize the column densities derived by (cite: vanGelder2022) from minor isotopologues as a basis for comparison. Given the ice origin of methanol, it is possible to deduct information on the chemical history of and from their relative abundances with respect to . In the following subsections, we compare $N$()/$N$() and $N$()/$N$() derived in this work with relative abundances taken from the literature. These encompass gas-phase observations towards both massive and low-mass young stellar objects (MYSOs and LYSOs), ice observations towards protostars and dark clouds, as well as cometary ratios. A complete list of references from which these ratios are taken can be found in Appendix [14](#appendix:lit_ratios).

## *N*()/*N*()

![](Figures/NOCS_NCH3OH.pdf)

Figure [4](#fig:NOCS_NCH3OH) shows a comparison of the column density ratios of *N*()/*N*() for various objects. It includes gas-phase observations in low- and high-mass sources as well as ice observations in MYSOs, in dark clouds, and in comets (see Appendix [14](#appendix:lit_ratios) for a list of references). The ratios derived in this work are shown in blue. In general, no trend in ratio versus luminosity is observed. Indeed, the data points for protostars (including both ice and gas phases) result in a Pearson correlation coefficient ($r$) of only -0.11. Spearman correlation tests are also performed and yield similar results to Pearson’s for all cases explored in this work. Figure [4](#fig:NOCS_NCH3OH) also contain single-dish observations, but since these probe a much larger scale compared to interferometric counterparts, they are not included in the analysis. Furthermore, (cite: Kushwahaa2023) note that their observations could be subject to beam dilution, which could affect the gas-phase ratios for most of the low-mass sources shown in Figure [4](#fig:NOCS_NCH3OH) (with the exception of IRAS 16293-2422 B). Nonetheless, they can still provide information on general trends in abundances. The fairly constant abundance ratios observed throughout all sources indicate that must be formed under similar conditions irrespective of the mass (or luminosity) of the protostar. Considering the drastically different physical conditions experienced by MYSOs and LYSOs during their evolution, particularly regarding their temperatures and UV fields, this lack of correlation with respect to luminosity points at an early formation of the bulk of under cold and dense conditions, prior to the onset of star-formation. More data points for low-mass sources would be useful to further constrain any potential trend obscured by the scatter in the ratios.

A considerable number of data points are available for *N*()/*N*() ratios in protostellar ices (cite: Boogert2022), which enables a statistically significant analysis. Abundance distribution histograms are an instructive approach to compare different, large datasets (see, e.g., (cite: Oberg2011)). In Figure [5](#fig:hist_OCS), the log-transformed *N*()/*N*() ratios are presented for both ice and gas observations towards MYSOs, and are centered on the weighted median of the ALMAGAL dataset ($\sim$0.033). Ice lower limits affect the median value by $<5\%$ and are thus not included in the analysis. Overall, the ice ratios in MYSOs are slightly lower than the gas-phase counterparts, with a difference of a factor of $\sim$3 between their weighted medians. This discrepancy is remarkably small, and could be due to the uncertainties in the spectral analysis (especially considering the approximation of a fixed $T_{\text{ex}}$). Such strikingly similar ratios provide a strong evidence for an icy origin of .

Futhermore, both ice and gas datasets have small scatters, which suggests that the column densities of and are subject to similar dependencies. A spread factor $f$, defined by 10 to the power of the weighted 1$\sigma$ standard deviation measured in log10 space, serves as a convenient comparison basis between distinct datasets (see, e.g., (cite: Nazari2023a)). Table [1](#tab:medians) summarizes the weighted median gas-phase ratios and spread factors derived in this work for $N$()/$N$(), $N$()/$N$(), and $N$()/$N$(). For the ALMAGAL subset, the $N$()/$N$() ratios results in $f=2.8$, whereas ice observations in MYSOs have $f=1.9$. These small scatters suggest similar conditions during the formation of the bulk of and , strengthening the conclusion of an icy origin to followed by thermal sublimation. It is worth noting that the lower limits in the available ice ratios are either equivalent to or higher than the corresponding weighted median, so a high abundance tail similar to the gas-phase case could be plausible.

| Ratio       | Weighted median | Spread factor |
|:------------|:---------------:|:-------------:|
| $N$()/$N$() |      0.033      |      2.8      |
| $N$()/$N$() |      0.044      |      5.8      |
| $N$()/$N$() |      1.103      |      3.7      |

: Weighted medians of the column density ratios and spread factors derived in this work for gas-phase species in massive sources (not including upper limits).

The small scatter for points to an ice environment similar to . This agrees with the main proposed chemical routes to form OCS, which involve the sulfurization of ices. Laboratory experiments show that ice can be readily formed by the reactions ((cite: Ferrante2008; Jimenez-Escobar2014; Chen2015; Nguyen2021; Santos_submm):

$$\begin{equation}
    \ce{s-CO} + \ce{s-S} \to \ce{s-OCS}
\label{CO+S}
\end{equation}$$

$$\begin{equation}
    \ce{s-CO} + \ce{s-HS} \to \ce{s-OCS} + \ce{s-H},
\label{CO+SH}
\end{equation}$$

which can either be induced by thermalized and adsorbed on the ice or as a result of the energetic processing of larger species (e.g., and ). Indeed, (cite: Boogert2022) analyze a large sample of ice observations towards massive protostars and conclude that and column densities are correlated, pointing to an formation concomitant with during the dense pre-stellar core stage, with both sharing CO as a common precursor.

![](Figures/abundance_hist_NOCS_NCH3OH.pdf)

Comparisons with dark clouds prior to star formation and comets are also relevant to constrain the evolution of sulfur species in both solid and gas phases. Observed $N$()/$N$() ice ratios in dark clouds agree strikingly well with the protostellar observations towards both ice and gas. This is in full support of the hypothesis that is formed in the ices within pre-stellar cores. Caution should be taken when comparing these values, however, since only two data points are available for ices in prestellar cores so far (cite: McClure2023). Nonetheless, it can still provide the basis for an interesting preliminary comparison. Cometary ratios, in turn, are marginally higher (by a factor of $\sim$4) than the weighted median for ALMAGAL, although their spread encompasses both gas and ice observations. This small discrepancy could be due to additional processing of during the protostellar disk phase (as was also suggested by (cite: Boogert2022)), or as a result of selective destruction before incorporation into comets. The latter has been previously suggested by (cite: Oberg2011) as one explanation to the depletion of cometary , , and ices relative to compared to protostars. However, given that and are mixed, it seems unlikely that a destruction mechanism could affect one but not the other.

## *N*()/*N*()

![](Figures/NSO2_NCH3OH.pdf)

Figure [6](#fig:NSO2_NCH3OH) shows a comparison of the column density ratios of *N*()/*N*(). Similarly to , no correlation is observed for the column density ratios in protostars as a function of luminosity (Pearson $r=-0.08$), in support of the hypothesis of an early formation during the pre-stellar core stage. One caveat to this conclusion is that the gaseous column densities in LYSOs are derived from its major isotopologue for most sources (light-red points in Figure [6](#fig:NSO2_NCH3OH)), which could contain appreciable contamination from outflow emission and could be optically thick. In fact, (cite: delaVillarmois2023) estimate that $\sim$40$\%$ of the emission in their study is extended. The only exception among low-mass sources is the data point corresponding to IRAS 16293–2422 B, for which column densities are derived from (dark-red point in Figure [6](#fig:NSO2_NCH3OH)). Further works focused on compact, optically thin emission (as traced by, e.g., ) in low-mass sources are warranted to further evaluate this hypothesis.

In contrast to , ice ratios of *N*()/*N*() in protostars are still scarce. However, the available values so far for both high-mass and low-mass sources taken from (cite: Boogert1997; Boogert2022) and (cite: Rocha2024) agree fairly well with the median gas-phase ratios derived in this study. The weighted median for our subset of MYSOs (excluding upper limits) is $\sim$ 0.044, which is consistent with both ice ratios of 0.06$\pm$0.04 and 0.07$\pm$0.04 in a low- and high-mass source, respectively. This agrees with the hypothesis that is primarily formed in ices prior to the onset of star formation, and later sublimates upon thermal heating by the protostar.

The scatter in the ALMAGAL values is considerably larger than that for , which suggests that the column densities of and are subject to different dependencies. For the ALMAGAL subset, *N*()/*N*() ratios result in $f=5.8$. For comparison, oxygen and nitrogen-bearing COMs typically have *N*(X)/*N*() spread factors of $f\lesssim$3.5 (cite: Nazari2022; Chen2023). There are likely two reasons behind this large scatter for : one related to both and ice environments, and another related to post-desorption processing of .

Compared to methanol, the body of knowledge on interstellar formation in cold environments is still somewhat scarce. Currently, its main proposed formation routes generally involve and a source of oxygen as reactants (cite: Hartquist1980; Charnley1997; Atkinson2004; Blitz2000; Woods2015; Vidal2018; Laas2019):

$$\begin{equation}
    \ce{SO} + \ce{OH} \to \ce{SO2} + \ce{H}
\label{SO+OH}
\end{equation}$$

$$\begin{equation}
    \ce{SO} + \ce{O2} \to \ce{SO2} + \ce{O}
\label{SO+O2}
\end{equation}$$

$$\begin{equation}
    \ce{SO} + \ce{O} \to \ce{SO2}.
\label{SO+O}
\end{equation}$$

In the gas phase, such routes are usually not viable at temperatures below 100 K (e.g., (cite: vanGelder2021)). One exception might be Reaction [\[SO+OH\]](#SO+OH), for which rate constants have been predicted to range between $\sim(2-3)\times10^{-10}$ cm$^3$ s$^{-1}$ for temperatures between $10 - 100$ K (cite: Fuente2019). Still, observed gaseous abundances of in both diffuse and dense clouds are $\sim10^{-6}-10^{-5}$ with respect to ((cite: Turner1995; Cernicharo2011), see also Table 4 in (cite: Laas2019)), which are three to four orders of magnitude lower than ice abundances. Adsorption of from the gas phase therefore cannot account for the ice observations. Rather, solid-phase routes to must be considered, for which Reactions [\[SO+OH\]](#SO+OH)$-$[\[SO+O\]](#SO+O) are also good candidates (cite: Smardzewski1978; Moore2007; Ferrante2008; Chen2015; Vidal2017).

Like , gas-phase abundances of with respect to are still orders of magnitude smaller than those of in the ices (cite: Turner1995; Lique2006; Neufeld2015). Thus, even if all adsorbed from the gas phase would be converted to , it would still be insufficient to explain abundances. Alternatively, atoms adsorbed on the ices could react with or to form through:

$$\begin{equation}
    \ce{s-S} + \ce{s-O} \to \ce{s-SO},
\label{S+O}
\end{equation}$$

$$\begin{equation}
    \ce{s-S} + \ce{s-OH} \to \ce{s-SO} + \ce{s-H},
\label{S+OH}
\end{equation}$$

which in turn can lead to ice via Reactions [\[SO+OH\]](#SO+OH) $-$ [\[SO+O\]](#SO+O). Atomic can also directly form ice by reacting with :

$$\begin{equation}
    \ce{s-S} + \ce{s-O2} \to \ce{s-SO2}.
\label{S+O2}
\end{equation}$$

In addition to the atomic form, interactions of radicals with can efficiently produce ice:

$$\begin{equation}
    \ce{s-HS} + \ce{s-O} \to \ce{s-SO} + \ce{s-H}.
\label{HS+O}
\end{equation}$$

Most of these routes have been probed in the laboratory by a number of experimental works involving ices mixed with oxygen-bearing molecules (e.g., or ) and exposed to energetic processing (such as UV photons or protons) to generate the open-shell species (cite: Smardzewski1978; Moore2007; Ferrante2008; Chen2015). Indeed, radicals are thought to be formed in ices both via the hydrogenation of adsorbed atoms as well as the destruction of molecules. The latter can occur either through energetic processing, as mentioned above, or due to -induced abstraction reactions (cite: Oba2018; Oba2019; Santos2023). Furthermore, (cite: Laas2019) assert that Reactions [\[SO+O2\]](#SO+O2) and [\[SO+O\]](#SO+O) are hindered in ices due to the high diffusion and binding energies of the reactants. Radical and atom formation through energetic processing could partially circumvent this issue.

Irrespective of the mechanism to originate , all routes require an oxygen-rich environment to take place. Such an environment is more likely to occur in the earlier phases of the pre-stellar stage, during which ices grow from the hydrogenation of , , and (e.g., (cite: Tielens1982; Miyauchi2008; Ioppolo2008; Lamberts2016)). Therefore, should be formed simultaneously with during the low-density stage of pre-stellar cores. In contrast, is mainly formed at a much later stage, when densities are high enough for to catastrophically freeze-out onto the grains ($A_\text{v} > 9$, $n_H \gtrsim 10^5$ cm$^{−3}$). This discrepancy in the formation timeline of the two species means that they will be subject to different physical conditions and collapse timescales, which may explain the large scatter in the observed ratios. While it is true that ice observations of have so far been best described by laboratory measurements of in a -rich environment (cite: Boogert1997; Rocha2024), the ice feature at 7.6 $\mu$m was shown to be highly sensitive to ice mixtures and temperatures (cite: Boogert1997). Hence, further systematic infrared characterizations of , perhaps with a combination of tertiary ice mixtures including , would be beneficial to better constrain the chemical environment of this molecule.

A complementary explanation for the scatter in $N$()/$N$() is the reprocessing of in the gas phase. The emission probed in this work traces the hot core region surrounding the protostar, where thermal heating has led the volatile ice content to fully sublimate. At the typically warmer temperatures of such environments ($\gtrsim$100 K), the conditions become favorable for Reactions [\[SO+OH\]](#SO+OH)$-$[\[SO+O\]](#SO+O) to take place in the gas phase (cite: Hartquist1980; vanGelder2021). Given the large variation of source structures and physical conditions associated with massive protostars, the degree to which such reactions occur will likely vary considerably from source to source and are thus expected to result in a wide scatter of column densities. Indeed, the models in (cite: Vidal2018) predict that the gaseous abundances in protostars are particularly subject to large variations depending on the composition of the parent cloud and the temperature. Furthermore, (cite: vanGelder2021) show that gas-phase formation is strongly linked to the local UV radiation field, since the strength of the latter will largely affect the distribution of reactants. These properties are expected to vary considerably from one massive source to another.

In addition to , ices typically show considerable variations in column density from source to source (cite: Oberg2011), which could be contributing to the scatter seen for $N$()/$N$(). Nonetheless, the larger spread for $N$() compared to other species relative to $N$() (e.g., (cite: Nazari2022; Chen2023) and the $N$()/$N$() ratios in this work) points to a significant effect directly associated with . Differences in the emitting area of and could also play a part in the scatter (cite: Nazari2024), albeit to a lesser extent since experimental laboratory sublimation temperatures of and are generally quite similar (at $\sim$120 K and $\sim$145 K, respectively; (cite: Kanuchova2017; Mifsud2023; Carrascosa2023)). Codesorption with can potentially raise the sublimation temperature of , but not enough to result in an appreciable difference to (see, e.g., (cite: Fraser2001) for sublimation temperatures of ). Overall, both the origin of in ices and its fate after sublimation are likely to play a part in the large scatter seen in Figure [6](#fig:NSO2_NCH3OH).

In dark clouds, the ice ratios of $N$()/$N$() are generally lower than in the protostellar phase (both for ice and gas observations) by about one order of magnitude. This discrepancy could indicate some additional production of during the protostellar phase, conceivably due to the enhanced UV radiation field produced in such environments. Cometary ratios are marginally higher, but still in a reasonably good agreement with protostellar ices, and are larger than the weighted median for gas-phase MYSOs by a factor of $\sim6$. As for the case of , causes for this enhancement could be additional processing of during the protostellar disk phase, or as a result of selective destruction before incorporation into comets. Given that and are proposed to inhabit different ice phases, this supposition is not a priori unreasonable. In summary, the ratios shown in Figure [6](#fig:NSO2_NCH3OH) support the hypothesis of a moderate, but not complete inheritance of ices from the pre-stellar phase into comets.

##  versus 

![](Figures/abundance_hist_NSO2_NOCS.pdf)

The column density ratios for / as a function of luminosity agree with the conclusions drawn in the previous subsections (see Appendix [15](#appendix:NSO2_NOCS)). Figure [7](#fig:hist_ALMAGAL) presents the distribution histograms of $N$() and $N$() with respect to $N$() derived in this work. Each $N$(X)/$N$() is normalized to its own weighted median, so that both distributions are centered on 1 (i.e., 0 in log space). This figure clearly shows the distinctive behaviors of and , emphasizing that the latter is likely much more strongly linked to than the former. Furthermore, it suggests that reprocessing of upon desorption is much more drastic than for , in agreement with the models in (cite: Vidal2018).

Another relevant source of information is to compare the direct correlation between and abundances with respect to (Figure [8](#fig:XSO2_XOCS)). Based on the derived Pearson coefficient ($r=0.32$), a weak correlation appears to exist between $N$()/$N$() and $N$()/$N$(). This is supported by the Spearman’s correlation test, which yields a coefficient of $\rho=0.38$ with a p-value of 0.05. The fact that this association is weak is unsurprising, since the bulk of and probably originate from two different ice environments, which means that their chemistry cannot be strongly linked. Nonetheless, some modest connection seems to be present between the two sulfur-bearing species. This could be due, for instance, to one species providing a source of sulfur that is converted into the other. Indeed, ices can be dissociated into atoms upon energetic processing, which could in turn react with to form . Likewise, molecules can also yield atoms upon fragmentation, which in turn can react with to form (cite: Ferrante2008). Alternatively, this correlation could be the result of a common precursor to both species, such as atomic or radicals. We emphasize, however, that the correlation is weak and reliant on the high-abundance end of the range of values, and thus should be considered with caution.

![](Figures/XSO2_XOCS.pdf)

# Conclusions

In this work we analyze the emission of and towards 26 line-rich MYSOs observed as part of the ALMAGAL survey. We compare their abundances with respect to methanol with other gas-phase observations towards low-mass sources, as well as in interstellar ices and comets. Our main findings are summarized below:

- The gaseous column density ratios of / and / show no trend with respect to luminosity, pointing at an early onset formation of both sulfur-bearing molecules before star-formation begins. The ratios in protostellar ices are consistent with the weighted medians of the ALMAGAL dataset, suggesting an icy origin to both and followed by thermal sublimation upon heating from the protostar.

- A large scatter in relative abundances is observed with ALMAGAL for gaseous / ($f=5.8$), but not for /. Different chemical environments during the formation of and are proposed as an explanation, with the former being formed during the low-density phase of cold couds, and the latter’s formation mostly taking place during the later, high-density pre-stellar stage. and both originate from reactions with ice. Post desorption processing is also likely to contribute to the spread in $N$()/$N$().

- For , dark cloud ice values are in remarkably good agreement with both protostellar ice and gas observations. Cometary ratios are also quite similar, at only a factor of $\sim$4 higher. Some extra formation of during the protostellar disk phase has been suggested as a root for this difference, as well as selective destruction of . Nonetheless, all ratios point to a significant inheritance of ices throughout the different stages of star formation.

- The gaseous abundances of relative to derived in this work agree with both dark-cloud and cometary ice ratios. Values in comets are generally slightly higher ($\sim$6$\times$) than in protostars, which in turn are higher than in dark clouds. This could indicate some additional formation of during the protostellar and protoplanetary-disk phases, although selective destruction of could also explain such observations in the latter case.

- A weak correlation ($r=0.32$) is found between $N(\ce{SO2})/N(\ce{CH3OH})$ and $N(\ce{OCS})/N(\ce{CH3OH})$. While the bulk of these ices is likely formed in different environments during two distinct evolutionary timescales, some interconversion between and is possible and could lead to a weak association. This could also result from a common precursor among the two species, arguably or .

Overall, our findings suggest that and differ significantly in both their formation and destruction pathways, but could still potentially share a common history. It should be noted that the dataset studied here is biased in favor of line rich sources and therefore our results might nor represent all massive protostars. Furthermore, it is clear that more observational constraints on interstellar ice column densities of sulfur bearing species, and in particular of , are paramount to build a more complete understanding of the origin and fate of sulfur. The *James Webb* Space Telescope offers a unique opportunity for such constraints to be explored in depth.

# Acknowledgements

Astrochemistry at Leiden is supported by funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement No. 101019751 MOLDISK) and the Danish National Research Foundation through the Center of Excellence “InterCat” (Grant agreement no.: DNRF150).

178 natexlab

(ref: Agundez2019) Agúndez, M., Marcelino, N., Cernicharo, J., Roueff, E., & Tafalla, M. 2019, A&A, 625, A147

(ref: Altwegg2022) Altwegg, K., Combi, M., Fuselier, S. A., et al. 2022, MNRAS, 516, 3900

(ref: Anderson2013) Anderson, D. E., Bergin, E. A., Maret, S., & Wakelam, V. 2013, ApJ, 779, 141

(ref: delaVillarmois2023) Artur de la Villarmois, E., Guzmán, V. V., Yang, Y. L., Zhang, Y., & Sakai, N. 2023, A&A, 678, A124

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481

(ref: Atkinson2004) Atkinson, R., Baulch, D. L., Cox, R. A., et al. 2004, Atmospheric Chemistry & Physics, 4, 1461

(ref: Bergner2017) Bergner, J. B., Öberg, K. I., & Rajappan, M. 2017, ApJ, 845, 29

(ref: Biver2021a) Biver, N., Bockelée-Morvan, D., Boissier, J., et al. 2021a, A&A, 648, A49

(ref: Biver2021b) Biver, N., Bockelée-Morvan, D., Lis, D. C., et al. 2021b, A&A, 651, A25

(ref: Biver2015) Biver, N., Bockelée-Morvan, D., Moreno, R., et al. 2015, Science Advances, 1, 1500863

(ref: Blake1987) Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G. 1987, ApJ, 315, 621

(ref: Blake1994) Blake, G. A., van Dishoeck, E. F., Jansen, D. J., Groesbeck, T. D., & Mundy, L. G. 1994, ApJ, 428, 680

(ref: Blitz2000) Blitz, M. A., McKee, K. W., & Pilling, M. J. 2000, Proceedings of the Combustion Institute, 28, 2491

(ref: Bockelee-Morvan2000) Bockelée-Morvan, D., Lis, D. C., Wink, J. E., et al. 2000, A&A, 353, 1101

(ref: Boogert2002) Boogert, A. C. A., Blake, G. A., & Tielens, A. G. G. M. 2002, ApJ, 577, 271

(ref: Boogert2022) Boogert, A. C. A., Brewer, K., Brittain, A., & Emerson, K. S. 2022, ApJ, 941, 32

(ref: Boogert1997) Boogert, A. C. A., Schutte, W. A., Helmich, F. P., Tielens, A. G. G. M., & Wooden, D. H. 1997, A&A, 317, 929

(ref: Booth2024) Booth, A. S., Temmink, M., van Dishoeck, E. F., et al. 2024, AJ, 167, 165

(ref: Bouscasse2022) Bouscasse, L., Csengeri, T., Belloche, A., et al. 2022, A&A, 662, A32

(ref: Calmonte2016) Calmonte, U., Altwegg, K., Balsiger, H., et al. 2016, MNRAS, 462, S253

(ref: Carrascosa2023) Carrascosa, H., Satorre, M. Á., Escribano, B., Martı́n-Doménech, R., & Muñoz Caro, G. M. 2023, MNRAS, 525, 2690

(ref: Cartwright2020) Cartwright, R. J., Nordheim, T. A., Cruikshank, D. P., et al. 2020, ApJL, 902, L38

(ref: Cernicharo2012) Cernicharo, J., Marcelino, N., Roueff, E., et al. 2012, ApJL, 759, L43

(ref: Cernicharo2011) Cernicharo, J., Spielfiedel, A., Balança, C., et al. 2011, A&A, 531, A103

(ref: Cesaroni2010) Cesaroni, R., Hofner, P., Araya, E., & Kurtz, S. 2010, A&A, 509, A50

(ref: Charnley1997) Charnley, S. B. 1997, ApJ, 481, 396

(ref: Charnley1992) Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJL, 399, L71

(ref: Chen2023) Chen, Y., van Gelder, M. L., Nazari, P., et al. 2023, A&A, 678, A137

(ref: Chen2015) Chen, Y. J., Juang, K. J., Nuevo, M., et al. 2015, ApJ, 798, 80

(ref: Codella2021) Codella, C., Bianchi, E., Podio, L., et al. 2021, A&A, 654, A52

(ref: Cuppen2010) Cuppen, H. M., Ioppolo, S., Romanzin, C., & Linnartz, H. 2010, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 12, 12077

(ref: Cuppen2009) Cuppen, H. M., van Dishoeck, E. F., Herbst, E., & Tielens, A. G. G. M. 2009, A&A, 508, 275

(ref: deSimone2020) De Simone, M., Ceccarelli, C., Codella, C., et al. 2020, ApJL, 896, L3

(ref: DelloRusso1998) Dello Russo, N., DiSanti, M. A., Mumma, M. J., Magee-Sauer, K., & Rettig, T. W. 1998, Icarus, 135, 377

(ref: DelloRusso2016) Dello Russo, N., Kawakita, H., Vervack, R. J., & Weaver, H. A. 2016, Icarus, 278, 301

(ref: Drdla1989) Drdla, K., Knapp, G. R., & van Dishoeck, E. F. 1989, ApJ, 345, 815

(ref: Drozdovskaya2018) Drozdovskaya, M. N., van Dishoeck, E. F., Jørgensen, J. K., et al. 2018, MNRAS, 476, 4949

(ref: Dulieu2010) Dulieu, F., Amiaud, L., Congiu, E., et al. 2010, A&A, 512, A30

(ref: Dungee2018) Dungee, R., Boogert, A., DeWitt, C. N., et al. 2018, ApJL, 868, L10

(ref: Elia2021) Elia, D., Merello, M., Molinari, S., et al. 2021, MNRAS, 504, 2742

(ref: Elia2017) Elia, D., Molinari, S., Schisano, E., et al. 2017, MNRAS, 471, 100

(ref: Esplugues2022) Esplugues, G., Fuente, A., Navarro-Almaida, D., et al. 2022, A&A, 662, A52

(ref: Esplugues2023) Esplugues, G., Rodrı́guez-Baras, M., San Andrés, D., et al. 2023, A&A, 678, A199

(ref: Ferrante2008) Ferrante, R. F., Moore, M. H., Spiliotis, M. M., & Hudson, R. L. 2008, ApJ, 684, 1210

(ref: Fontani2023) Fontani, F., Roueff, E., Colzi, L., & Caselli, P. 2023, A&A, 680, A58

(ref: Fraser2001) Fraser, H. J., Collings, M. P., McCoustra, M. R. S., & Williams, D. A. 2001, MNRAS, 327, 1165

(ref: Fuchs2009) Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629

(ref: Fuente2010) Fuente, A., Cernicharo, J., Agúndez, M., et al. 2010, A&A, 524, A19

(ref: Fuente2019) Fuente, A., Navarro, D. G., Caselli, P., et al. 2019, A&A, 624, A105

(ref: Fuente2023) Fuente, A., Rivière-Marichalar, P., Beitia-Antero, L., et al. 2023, A&A, 670, A114

(ref: Fuente2021) Fuente, A., Treviño-Morales, S. P., Alonso-Albi, T., et al. 2021, MNRAS, 507, 1886

(ref: Gibb2000) Gibb, E., Nummelin, A., Irvine, W. M., Whittet, D. C. B., & Bergman, P. 2000, ApJ, 545, 309

(ref: Gieser2019) Gieser, C., Semenov, D., Beuther, H., et al. 2019, A&A, 631, A142

(ref: Hartquist1980) Hartquist, T. W., Dalgarno, A., & Oppenheimer, M. 1980, ApJ, 236, 182

(ref: Hatchell1998) Hatchell, J., Thompson, M. A., Millar, T. J., & MacDonald, G. H. 1998, A&A, 338, 713

(ref: Heikkila1999) Heikkilä, A., Johansson, L. E. B., & Olofsson, H. 1999, A&A, 344, 817

(ref: Henkel1985) Henkel, C. & Bally, J. 1985, A&A, 150, L25

(ref: Herbst2009) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: Herpin2009) Herpin, F., Marseille, M., Wakelam, V., Bontemps, S., & Lis, D. C. 2009, A&A, 504, 853

(ref: Hibbitts2000) Hibbitts, C. A., McCord, T. B., & Hansen, G. B. 2000, , 105, 22541

(ref: Hiraoka1998) Hiraoka, K., Miyagoshi, T., Takayama, T., Yamamoto, K., & Kihara, Y. 1998, ApJ, 498, 710

(ref: Hiraoka1994) Hiraoka, K., Ohashi, N., Kihara, Y., et al. 1994, Chemical Physics Letters, 229, 408

(ref: Hodyss2009) Hodyss, R., Johnson, P. V., Stern, J. V., Goguen, J. D., & Kanik, I. 2009, Icarus, 200, 338

(ref: Hofner2001) Hofner, P., Wiesemeyer, H., & Henning, T. 2001, ApJ, 549, 425

(ref: Honma2015) Honma, M., Nagayama, T., & Sakai, N. 2015, PASJ, 67, 70

(ref: Ioppolo2008) Ioppolo, S., Cuppen, H. M., Romanzin, C., van Dishoeck, E. F., & Linnartz, H. 2008, ApJ, 686, 1474

(ref: Ioppolo2010) Ioppolo, S., Cuppen, H. M., Romanzin, C., van Dishoeck, E. F., & Linnartz, H. 2010, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 12, 12065

(ref: Jessup2007) Jessup, K. L., Spencer, J., & Yelle, R. 2007, Icarus, 192, 24

(ref: Jimenez-Escobar2014) Jiménez-Escobar, A., Muñoz Caro, G. M., & Chen, Y. J. 2014, MNRAS, 443, 343

(ref: Jorgensen2018) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170

(ref: Kanuchova2017) Kaňuchová, Z., Boduch, P., Domaracka, A., et al. 2017, A&A, 604, A68

(ref: Keane2001) Keane, J. V., Boonman, A. M. S., Tielens, A. G. G. M., & van Dishoeck, E. F. 2001, A&A, 376, L5

(ref: Koleniskova2014) Kolesniková, L., Tercero, B., Cernicharo, J., et al. 2014, ApJL, 784, L7

(ref: Kushwahaa2023) Kushwahaa, T., Drozdovskaya, M. N., Tychoniec, Ł., & Tabone, B. 2023, A&A, 672, A122

(ref: Laas2019) Laas, J. C. & Caselli, P. 2019, A&A, 624, A108

(ref: Lamberts2017) Lamberts, T., Fedoseev, G., Kästner, J., Ioppolo, S., & Linnartz, H. 2017, A&A, 599, A132

(ref: Lamberts2016) Lamberts, T., Samanta, P. K., Köhn, A., & Kästner, J. 2016, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 18, 33021

(ref: LeGal2019) Le Gal, R., Öberg, K. I., Loomis, R. A., Pegues, J., & Bergner, J. B. 2019, ApJ, 876, 72

(ref: LeGal2021) Le Gal, R., Öberg, K. I., Teague, R., et al. 2021, ApJS, 257, 12

(ref: LeRoy2015) Le Roy, L., Altwegg, K., Balsiger, H., et al. 2015, A&A, 583, A1

(ref: Li2015) Li, J., Wang, J., Zhu, Q., Zhang, J., & Li, D. 2015, ApJ, 802, 40

(ref: Linke1979) Linke, R. A., Frerking, M. A., & Thaddeus, P. 1979, ApJL, 234, L139

(ref: Lique2006) Lique, F., Cernicharo, J., & Cox, P. 2006, ApJ, 653, 1342

(ref: Lumsden2013) Lumsden, S. L., Hoare, M. G., Urquhart, J. S., et al. 2013, ApJS, 208, 11

(ref: Majumdar2016) Majumdar, L., Gratier, P., Vidal, T., et al. 2016, MNRAS, 458, 1859

(ref: Manigand2020) Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48

(ref: Martin2005) Martı́n, S., Martı́n-Pintado, J., Mauersberger, R., Henkel, C., & Garcı́a-Burillo, S. 2005, ApJ, 620, 210

(ref: Martin2003) Martı́n, S., Mauersberger, R., Martı́n-Pintado, J., Garcı́a-Burillo, S., & Henkel, C. 2003, A&A, 411, L465

(ref: Mauersberger1995) Mauersberger, R., Henkel, C., & Chin, Y. N. 1995, A&A, 294, 23

(ref: McClure2023) McClure, M. K., Rocha, W. R. M., Pontoppidan, K. M., et al. 2023, Nature Astronomy, 7, 431

(ref: McGuire2022) McGuire, B. A. 2022, ApJS, 259, 30

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Mege2021) Mège, P., Russeil, D., Zavagno, A., et al. 2021, A&A, 646, A74

(ref: Mifsud2023) Mifsud, D. V., Herczku, P., Rahul, K. K., et al. 2023, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 25, 26278

(ref: Mininni2021) Mininni, C., Fontani, F., Sánchez-Monge, A., et al. 2021, A&A, 653, A87

(ref: Miyauchi2008) Miyauchi, N., Hidaka, H., Chigai, T., et al. 2008, Chemical Physics Letters, 456, 27

(ref: Mokrane2009) Mokrane, H., Chaabouni, H., Accolla, M., et al. 2009, ApJL, 705, L195

(ref: Molinari2010) Molinari, S., Swinyard, B., Bally, J., et al. 2010, A&A, 518, L100

(ref: Moore2007) Moore, M. H., Hudson, R. L., & Carlson, R. W. 2007, Icarus, 189, 409

(ref: Moullet2013) Moullet, A., Lellouch, E., Moreno, R., et al. 2013, ApJ, 776, 32

(ref: Moullet2008) Moullet, A., Lellouch, E., Moreno, R., Gurwell, M. A., & Moore, C. 2008, A&A, 482, 279

(ref: Muller2016) Müller, H. S. P., Belloche, A., Xu, L.-H., et al. 2016, A&A, 587, A92

(ref: Muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: Muller2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370, L49

(ref: Mumma2011) Mumma, M. J., Bonev, B. P., Villanueva, G. L., et al. 2011, ApJL, 734, L7

(ref: Navarro-Almaida2020) Navarro-Almaida, D., Le Gal, R., Fuente, A., et al. 2020, A&A, 637, A39

(ref: Nazari2022) Nazari, P., Meijerhof, J. D., van Gelder, M. L., et al. 2022, A&A, 668, A109

(ref: Nazari2024) Nazari, P., Tabone, B., Rosotti, G. P., & van Dishoeck, E. F. 2024, Correlations among complex organic molecules around protostars: Effects of physical structure

(ref: Nazari2023a) Nazari, P., Tabone, B., van’t Hoff, M. L. R., Jørgensen, J. K., & van Dishoeck, E. F. 2023, ApJL, 951, L38

(ref: Nazari2021) Nazari, P., van Gelder, M. L., van Dishoeck, E. F., et al. 2021, A&A, 650, A150

(ref: Neufeld2015) Neufeld, D. A., Godard, B., Gerin, M., et al. 2015, A&A, 577, A49

(ref: Nguyen2021) Nguyen, T., Oba, Y., Sameera, W. M. C., Kouchi, A., & Watanabe, N. 2021, ApJ, 922, 146

(ref: Nickerson2023) Nickerson, S., Rangwala, N., Colgan, S. W. J., et al. 2023, ApJ, 945, 26

(ref: Oba2019) Oba, Y., Tomaru, T., Kouchi, A., & Watanabe, N. 2019, ApJ, 874, 124

(ref: Oba2018) Oba, Y., Tomaru, T., Lamberts, T., Kouchi, A., & Watanabe, N. 2018, Nature Astronomy, 2, 228

(ref: Oberg2008) Öberg, K. I., Boogert, A. C. A., Pontoppidan, K. M., et al. 2008, ApJ, 678, 1032

(ref: Oberg2011) Öberg, K. I., Boogert, A. C. A., Pontoppidan, K. M., et al. 2011, ApJ, 740, 109

(ref: Oberg2010) Öberg, K. I., van Dishoeck, E. F., Linnartz, H., & Andersson, S. 2010, ApJ, 718, 832

(ref: Osorio2009) Osorio, M., Anglada, G., Lizano, S., & D’Alessio, P. 2009, ApJ, 694, 29

(ref: Oya2019) Oya, Y., López-Sepulcre, A., Sakai, N., et al. 2019, ApJ, 881, 112

(ref: Oya2016) Oya, Y., Sakai, N., López-Sepulcre, A., et al. 2016, ApJ, 824, 88

(ref: Palumbo1997) Palumbo, M. E., Geballe, T. R., & Tielens, A. G. G. M. 1997, ApJ, 479, 839

(ref: Palumbo1995) Palumbo, M. E., Tielens, A. G. G. M., & Tokunaga, A. T. 1995, ApJ, 449, 674

(ref: Petuchowski1992) Petuchowski, S. J. & Bennett, C. L. 1992, ApJ, 391, 137

(ref: Phuong2018) Phuong, N. T., Chapillon, E., Majumdar, L., et al. 2018, A&A, 616, L5

(ref: Pillai2011) Pillai, T., Kauffmann, J., Wyrowski, F., et al. 2011, A&A, 530, A118

(ref: Pineau1993) Pineau des Forêts, G., Roueff, E., Schilke, P., & Flower, D. R. 1993, MNRAS, 262, 915

(ref: Pontoppidan2006) Pontoppidan, K. M. 2006, A&A, 453, L47

(ref: Pontoppidan2003) Pontoppidan, K. M., Fraser, H. J., Dartois, E., et al. 2003, A&A, 408, 981

(ref: Qasim2018) Qasim, D., Chuang, K. J., Fedoseev, G., et al. 2018, A&A, 612, A83

(ref: RiviereMarichalar2019) Rivière-Marichalar, P., Fuente, A., Goicoechea, J. R., et al. 2019, A&A, 628, A16

(ref: Riviere-Marichalar2021) Rivière-Marichalar, P., Fuente, A., Le Gal, R., et al. 2021, A&A, 652, A46

(ref: Riviere-Marichalar2020) Rivière-Marichalar, P., Fuente, A., Le Gal, R., et al. 2020, A&A, 642, A32

(ref: Rocha2024) Rocha, W. R. M., van Dishoeck, E. F., Ressler, M. E., et al. 2024, A&A, 683, A124

(ref: Rodriguez-Almeida2021) Rodrı́guez-Almeida, L. F., Jiménez-Serra, I., Rivilla, V. M., et al. 2021, ApJL, 912, L11

(ref: Romanzin2011) Romanzin, C., Ioppolo, S., Cuppen, H. M., van Dishoeck, E. F., & Linnartz, H. 2011, , 134, 084504

(ref: Sahu2019) Sahu, D., Liu, S.-Y., Su, Y.-N., et al. 2019, ApJ, 872, 196

(ref: Sakai2014) Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78

(ref: Saki2020) Saki, M., Gibb, E. L., Bonev, B. P., et al. 2020, AJ, 160, 184

(ref: Santos_submm) Santos, J., Linnartz, H., & Chuang, K.-J. 2024, A&A, submitted

(ref: Santos2022) Santos, J. C., Chuang, K.-J., Lamberts, T., et al. 2022, ApJL, 931, L33

(ref: Santos2023) Santos, J. C., Linnartz, H., & Chuang, K. J. 2023, A&A, 678, A112

(ref: Schuhmann2019) Schuhmann, M., Altwegg, K., Balsiger, H., et al. 2019, ACS Earth and Space Chemistry, 3, 1854

(ref: Semenov2018) Semenov, D., Favre, C., Fedele, D., et al. 2018, A&A, 617, A28

(ref: Smardzewski1978) Smardzewski, R. R. 1978, , 68, 2878

(ref: Smith1980) Smith, A. M., Stecher, T. P., & Casswell, L. 1980, ApJ, 242, 402

(ref: Spezzano2022) Spezzano, S., Sipilä, O., Caselli, P., et al. 2022, A&A, 661, A111

(ref: Tabone2017) Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6

(ref: Tafalla2000) Tafalla, M., Myers, P. C., Mardones, D., & Bachiller, R. 2000, A&A, 359, 967

(ref: Taquet2020) Taquet, V., Codella, C., De Simone, M., et al. 2020, A&A, 637, A63

(ref: Tieftrunk1994) Tieftrunk, A., Pineau des Forets, G., Schilke, P., & Walmsley, C. M. 1994, A&A, 289, 579

(ref: Tielens1982) Tielens, A. G. G. M. & Hagen, W. 1982, A&A, 114, 245

(ref: Tielens1991) Tielens, A. G. G. M., Tokunaga, A. T., Geballe, T. R., & Baas, F. 1991, ApJ, 381, 181

(ref: Tobin2016) Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73

(ref: Turner1995) Turner, B. E. 1995, ApJ, 455, 556

(ref: Tychoniec2021) Tychoniec, Ł., van Dishoeck, E. F., van’t Hoff, M. L. R., et al. 2021, A&A, 655, A65

(ref: vanderTak2003) van der Tak, F. F. S., Boonman, A. M. S., Braakman, R., & van Dishoeck, E. F. 2003, A&A, 412, 133

(ref: vanderTak2013) van der Tak, F. F. S., Chavarrı́a, L., Herpin, F., et al. 2013, A&A, 554, A83

(ref: vanderTak2000) van der Tak, F. F. S., van Dishoeck, E. F., & Caselli, P. 2000, A&A, 361, 327

(ref: vanGelder2022) van Gelder, M. L., Jaspers, J., Nazari, P., et al. 2022a, A&A, 667, A136

(ref: vanGelder2022a) van Gelder, M. L., Nazari, P., Tabone, B., et al. 2022b, A&A, 662, A67

(ref: vanGelder2024) van Gelder, M. L., Ressler, M. E., van Dishoeck, E. F., et al. 2024, A&A, 682, A78

(ref: vanGelder2020) van Gelder, M. L., Tabone, B., Tychoniec, Ł., et al. 2020, A&A, 639, A87

(ref: vanGelder2021) van Gelder, M. L., Tabone, B., van Dishoeck, E. F., & Godard, B. 2021, A&A, 653, A159

(ref: Vastel2015) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. M., & Boiziot, M. 2015, in SF2A-2015: Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics, 313–316

(ref: Vastel2018) Vastel, C., Quénard, D., Le Gal, R., et al. 2018, MNRAS, 478, 5514

(ref: Vidal2017) Vidal, T. H. G., Loison, J.-C., Jaziri, A. Y., et al. 2017, MNRAS, 469, 435

(ref: Vidal2018) Vidal, T. H. G. & Wakelam, V. 2018, MNRAS, 474, 5575

(ref: Wada2006) Wada, A., Mochizuki, N., & Hiraoka, K. 2006, ApJ, 644, 300

(ref: Wakelam2004) Wakelam, V., Castets, A., Ceccarelli, C., et al. 2004, A&A, 413, 609

(ref: Watanabe2002) Watanabe, N. & Kouchi, A. 2002, ApJL, 571, L173

(ref: Woods2015) Woods, P. M., Occhiogrosso, A., Viti, S., et al. 2015, MNRAS, 450, 1256

(ref: Yan2023) Yan, Y. T., Henkel, C., Kobayashi, C., et al. 2023, A&A, 670, A98

(ref: Yang2020) Yang, Y.-L., Evans, Neal J., I., Smith, A., et al. 2020, ApJ, 891, 61

(ref: Yang2022) Yang, Y.-L., Green, J. D., Pontoppidan, K. M., et al. 2022, ApJL, 941, L13

(ref: Yang2021) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20

(ref: Zapata2015) Zapata, L. A., Palau, A., Galván-Madrid, R., et al. 2015, MNRAS, 447, 1826

(ref: Zasowski2009) Zasowski, G., Kemper, F., Watson, D. M., et al. 2009, ApJ, 694, 459

# Example of excluded source

Figure [9](#fig:bad_source) contains an example of a source that was excluded from the analysis because of large divergences in the spectral properties between and , in this case potentially due to self absorption of the lines.

![](Figures/lines_bad_101899.pdf)

# Source properties and observational parameters

The observational parameters for each source and their physical properties are listed in Table [\[tab:source_stuff\]](#tab:source_stuff).

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | R.A. (J2000) $^a$ | Dec. (J2000) $^a$ | Beam | Line rms $^b$ | $d$ $^c$ | $D_\text{GC}$ $^d$ | L$_{\text{bol}}$ $^e$ |
|  | (hh:mm:ss.s) | (dd:mm:ss.s) | ($\ensuremath{''}$) | \(K\) | (kpc) | (kpc) | (L$_{\odot}$) |
| 126348 | 18:42:51.98 | -03:59:54.37 | 1.26 $\times$ 1.08 | 0.16 | 4.41 | 4.67 | 6798 |
| 615590 | 09:24:41.96 | -52:02:08.04 | 0.68 $\times$ 0.59 | 0.50 | 2.70 | 8.31 | 5470 |
| 644284A | 10:31:29.78 | -58:02:19.27 | 0.96 $\times$ 0.80 | 0.32 | 4.75 | 8.20 | $-$ |
| 693050 | 12:35:35.05 | -63:02:31.19 | 1.03 $\times$ 0.94 | 0.19 | 4.31 | 6.89 | 12200 |
| 705768 | 13:12:36.17 | -62:33:34.43 | 0.93 $\times$ 0.81 | 0.24 | 6.88 | 6.93 | 91728 |
| 707948 | 13:16:43.19 | -62:58:32.83 | 0.94 $\times$ 0.80 | 0.26 | 7.14 | 6.97 | 196800 |
| 717461A | 13:43:01.68 | -62:08:51.42 | 1.34 $\times$ 1.21 | 0.22 | 4.29 | 6.31 | 3323 |
| 721992 | 13:51:58.27 | -61:15:41.04 | 0.90 $\times$ 0.79 | 0.37 | 5.38 | 6.16 | 2630 |
| 724566 | 13:59:30.92 | -61:48:38.27 | 0.87 $\times$ 0.78 | 0.34 | 4.93 | 6.10 | 226 |
| 732038 | 14:13:15.05 | -61:16:53.19 | 0.87 $\times$ 0.78 | 0.40 | 5.64 | 5.93 | 74930 |
| 744757A | 14:45:26.35 | -59:49:15.55 | 1.31 $\times$ 1.27 | 0.15 | 2.51 | 6.45 | 12381 |
| 767784 | 15:29:19.31 | -56:31:22.02 | 1.31 $\times$ 1.24 | 0.16 | 4.04 | 5.37 | 139400 |
| 865468A | 17:05:10.90 | -41:29:06.99 | 1.32 $\times$ 1.14 | 0.22 | 3.04 | 5.17 | 47824 |
| 876288 | 17:11:51.02 | -39:09:29.18 | 0.92 $\times$ 0.69 | 0.29 | 5.95 | 2.58 | 58410 |
| 881427C | 17:20:06.12 | -38:57:15.84 | 1.31 $\times$ 1.13 | 0.56 | 1.50 | 6.59 | 458 |
| G023.3891p00.1851 | 18:33:14.32 | -08:23:57.82 | 1.43 $\times$ 1.07 | 0.18 | 10.86 | 4.72 | 91560 |
| G025.6498p01.0491 | 18:34:20.92 | -05:59:42.08 | 1.24 $\times$ 1.07 | 0.15 | 12.20 | 6.05 | 424000 |
| G305.2017p00.2072A1 | 13:11:10.45 | -62:34:38.60 | 1.38 $\times$ 1.21 | 0.21 | 4.00 | 6.61 | 20301 |
| G314.3197p00.1125 | 14:26:26.25 | -60:38:31.26 | 1.36 $\times$ 1.23 | 0.21 | 8.25 | 6.33 | 66440 |
| G316.6412-00.0867 | 14:44:18.35 | -59:55:11.28 | 1.32 $\times$ 1.25 | 0.15 | 2.73 | 6.35 | 8080 |
| G318.0489p00.0854B | 14:53:42.64 | -59:08:53.02 | 1.31 $\times$ 1.27 | 0.15 | 3.18 | 6.07 | 36480 |
| G318.9480-00.1969A1 | 15:00:55.28 | -58:58:52.60 | 1.30 $\times$ 1.27 | 0.15 | 10.40 | 6.83 | 209000 |
| G323.7399-00.2617B2 | 15:31:45.45 | -56:30:49.84 | 1.29 $\times$ 1.25 | 0.15 | 3.20 | 5.79 | 1529 |
| G327.1192p00.5103 | 15:47:32.72 | -53:52:38.60 | 0.90 $\times$ 0.72 | 0.34 | 4.74 | 4.81 | 54270 |
| G343.1261-00.0623 | 16:58:17.22 | -42:52:07.54 | 1.33 $\times$ 1.15 | 0.21 | 2.00 | 6.16 | 33800 |
| G345.5043p00.3480 | 17:04:22.89 | -40:44:23.06 | 1.34 $\times$ 1.15 | 0.20 | 2.00 | 6.13 | 29498 |

$^a$ The coordinates correspond to the pixel from which the spectra were extracted.

$^b$ Line rms as computed by (cite: Nazari2022).

$^c$ Distance to the source (cite: Lumsden2013; Mege2021). Typical uncertainties are of $\sim$0.5 kpc.

$^d$ Distance to the galactic center assumind the Sun’s $D_\text{GC}$ as 8.05 kpc (cite: Honma2015).

$^e$ Bolometric luminosities corrected to the distances $d$ (cite: Lumsden2013; Elia2017). For regions with multiple cores, the fraction of each individual source was estimated by dividing the total luminosity over all the cores weighted by their peak continuum flux (see also (cite: vanGelder2022a) and (cite: Nazari2022)). No estimations for 644284A are available, so a generic L$_{\text{bol}}\sim10^4$ L$_\odot$ is assumed.

# List of transitions

Table [8](#appendix:transitions) lists all the transitions of , , and with $E_{\text{up}}<800$ K and A$_{ij}>10^{-6}$ s$^{-1}$ covered in the data.

|  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|
| Species | Transition | Frequency | $E_{\text{up}}$ | $A_{ij}$ |
|  |  | (MHz) | \(K\) | (s$^{-1}$) |
|  | 26 8 18 $-$ 27 7 21 | 217412.915 | 473.565 | 2.09$\times$10$^{-5}$ |
|  | 31 9 23 $-$ 32 8 24 | 217902.353 | 646.797 | 2.17$\times$10$^{-5}$ |
|  | 11 1 11 $-$ 10 0 10 $^{\star}$ | 219355.009 | 60.075 | 1.11$\times$10$^{-4}$ |
|  | 36 5 31 $-$ 35 6 30 | 220451.866 | 675.942 | 2.61$\times$10$^{-5}$ |
|  | 6 4 2 4.5 $-$ 7 3 5 5.5 | 217628.227 | 57.861 | 1.07$\times$10$^{-5}$ |
|  | 6 4 2 7.5 $-$ 7 3 5 8.5 | 217628.440 | 57.861 | 1.04$\times$10$^{-5}$ |
|  | 6 4 2 5.5 $-$ 7 3 5 6.5 | 217628.749 | 57.861 | 1.03$\times$10$^{-5}$ |
|  | 6 4 2 6.5 $-$ 7 3 5 7.5 | 217628.884 | 57.861 | 1.03$\times$10$^{-5}$ |
|  | 11 1 11 9.5 $-$ 10 0 10 9.5 $^{\star}$ | 220613.365 | 60.215 | 1.60$\times$10$^{-6}$ |
|  | 11 1 11 9.5 $-$ 10 0 10 8.5 $^{\star}$ | 220617.426 | 60.215 | 1.11$\times$10$^{-4}$ |
|  | 11 1 11 12.5 $-$ 10 0 10 11.5 $^{\star}$ | 220617.778 | 60.215 | 1.12$\times$10$^{-4}$ |
|  | 11 1 11 10.5 $-$ 10 0 10 10.5 $^{\star}$ | 220619.743 | 60.215 | 1.93$\times$10$^{-6}$ |
|  | 11 1 11 10.5 $-$ 10 0 10 9.5 $^{\star}$ | 220620.374 | 60.215 | 1.10$\times$10$^{-4}$ |
|  | 11 1 11 11.5 $-$ 10 0 10 10.5 $^{\star}$ | 220620.716 | 60.215 | 1.11$\times$10$^{-4}$ |
|  | 11 1 11 11.5 $-$ 10 0 10 11.5 $^{\star}$ | 220624.670 | 60.215 | 1.33$\times$10$^{-6}$ |
|  | 18 $-$ 17 $^{\star}$ | 218198.998 | 99.49 | 3.01$\times$10$^{-5}$ |

$^{\star}$ Detected transitions.

# Best-fit models for all sources

Figures [10](#fig:models_all_34SO2) and [11](#fig:models_all_O13CS) show the best-fit models derived by the grid-fitting approach for each source in the ALMAGAL subset analyzed here. The former contains the results for , and the latter for .

![](Figures/34SO2_all_fittings.pdf)

![](Figures/O13CS_all_fittings.pdf)

# Integrated intensity map of 693050

Figure [12](#fig:moment0_693050) shows the integrated intensity maps of source 693050 for 11$_{1,11}$ $-$ 10$_{0,10}$ and 18 $-$ 17. The offset in the emission to the continuum peak is likely due to effects of optically thick dust at these wavelengths.

![](Figures/moment0_maps_693050_-5_5.pdf)

# Best fit parameters of and 

Tables [\[tab:fittings_1\]](#tab:fittings_1) and [\[tab:fittings_2\]](#tab:fittings_2) list the best-fit parameters for and , respectively, obtained with the grid fitting approach toward all sources. The isotope ratios for each source and corresponding estimated column densities of the main isotopologues are also reported.

+---------------------+------------------------------------------------------------------------+----------------------------------+--------------------------------+
|                     |                                                                        | ($^{32}\ce{S}/^{34}\ce{S}$) $^c$ |                                |
+:====================+:==============================:+:=============:+:=====================:+:================================:+:==============================:+
| 2-4 Source          | $N$ $^a$                       | FWHM $^b$     | $V_{\text{lsr}}$ $^b$ |                                  | $N$ $^d$                       |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
|                     | (cm$^{-2}$)                    | (km s$^{-1}$) | (km s$^{-1}$)         |                                  | (cm$^{-2}$)                    |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 126348              | $<$4.5$\times$10$^{14}$        | \[7.5\]       | 76.9                  | 20                               | $<$8.8$\times$10$^{15}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 615590              | (4.0$\pm$0.8)$\times$10$^{16}$ | 4.3$\pm$0.4   | 40.5                  | 23                               | (9.0$\pm$2.4)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 644284A             | (2.5$\pm$0.5)$\times$10$^{16}$ | 7.4$\pm$0.5   | 2.60                  | 22                               | (5.6$\pm$1.5)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 693050              | (2.0$\pm$0.4)$\times$10$^{16}$ | 5.7$\pm$1.6   | -41.2                 | 22                               | (4.3$\pm$1.1)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 705768              | $<$6.0$\times$10$^{14}$        | \[6.7\]       | -34.1                 | 22                               | $<$1.3$\times$10$^{16}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 707948              | (2.5$\pm$0.7)$\times$10$^{16}$ | 8.5$\pm$2.5   | -32.6                 | 22                               | (5.4$\pm$1.6)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 717461A             | (5.0$\pm$1.0)$\times$10$^{15}$ | 5.7$\pm$0.5   | -51.3                 | 21                               | (1.1$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 721992              | (1.3$\pm$0.3)$\times$10$^{15}$ | 3.2$\pm$0.7   | -57.3                 | 21                               | (2.6$\pm$0.8)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 724566              | $<$7.0$\times$10$^{14}$        | \[6.0\]       | -57.3                 | 21                               | $<$1.5$\times$10$^{16}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 732038              | (4.0$\pm$0.8)$\times$10$^{15}$ | 5.2$\pm$0.6   | -62.5                 | 21                               | (8.3$\pm$2.0)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 744757A             | (2.5$\pm$0.5)$\times$10$^{15}$ | 6.2$\pm$0.7   | -40.5                 | 21                               | (5.3$\pm$1.3)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 767784              | (1.6$\pm$0.3)$\times$10$^{15}$ | 4.1$\pm$0.3   | -67.9                 | 20                               | (3.2$\pm$0.8)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 865468A             | $<$6.0$\times$10$^{14}$        | \[8.0\]       | -27.3                 | 20                               | $<$1.2$\times$10$^{16}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 876288              | $<$5.0$\times$10$^{14}$        | 4.8$\pm$0.5   | -96.2                 | 18                               | $<$9.2$\times$10$^{15}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| 881427C             | $<$1.1$\times$10$^{15}$        | \[5.5\]       | -10.4                 | 18                               | $<$2.0$\times$10$^{16}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G023.3891p00.1851   | $<$2.5$\times$10$^{14}$        | \[4.0\]       | 75.5                  | 21                               | $<$5.3$\times$10$^{15}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G025.6498p01.0491   | (3.2$\pm$0.6)$\times$10$^{15}$ | 6.2$\pm$0.9   | 42.4                  | 21                               | (6.6$\pm$1.6)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G305.2017p00.2072A1 | (1.0$\pm$0.2)$\times$10$^{15}$ | 4.2$\pm$0.5   | -40.9                 | 21                               | (2.1$\pm$0.5)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G314.3197p00.1125   | $<$3.8$\times$10$^{14}$        | 5.0$\pm$0.5   | -49.0                 | 21                               | $<$8.0$\times$10$^{15}$        |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G316.6412-00.0867   | (1.6$\pm$0.3)$\times$10$^{15}$ | 8.2$\pm$0.5   | -20.5                 | 21                               | (3.3$\pm$0.8)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G318.0489p00.0854B  | (4.0$\pm$0.8)$\times$10$^{15}$ | 6.6$\pm$0.4   | -50.6                 | 21                               | (8.3$\pm$2.1)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G318.9480-00.1969A1 | (2.0$\pm$0.5)$\times$10$^{15}$ | 7.0$\pm$4.0   | -33.5                 | 22                               | (4.3$\pm$1.3)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G323.7399-00.2617B2 | (1.3$\pm$0.3)$\times$10$^{15}$ | 6.6$\pm$0.5   | -51.4                 | 21                               | (2.6$\pm$0.6)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G327.1192p00.5103   | (6.3$\pm$1.3)$\times$10$^{15}$ | 6.0$\pm$0.7   | -83.2                 | 20                               | (1.3$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G343.1261-00.0623   | (3.2$\pm$0.6)$\times$10$^{15}$ | 7.3$\pm$0.5   | -31.5                 | 21                               | (6.6$\pm$1.6)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+
| G345.5043p00.3480   | (5.0$\pm$1.0)$\times$10$^{15}$ | 7.9$\pm$0.6   | -17.5                 | 21                               | (1.1$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+

$^a$ Column densities are calculated using the grid fitting method. $3\sigma$ upper limits are derived by manual fitting.

$^b$ Square brackets denote FWHM values kept fixed during the fitting. For the sources where no emission is detected, their FWHM and $V_{\text{lsr}}$ are fixed to the values reported for towards the same source (cite: Nazari2022). For the rest of the sources the velocities are fixed to the best-fitted values derived by the manual approach.

$^c$ Values are rounded to zero decimals.

$^d$ Column densities of the main isotopologues are derived from the fitting results of the rare isotopologues and considering the isotope ratios.

+---------------------+-------------------------------------------------------------------+-----------------------------+--------------------------------+
|                     |                                                                   | ($^{12}\ce{C}/^{13}\ce{C}$) |                                |
+:====================+:==============================:+:=============:+:================:+:===========================:+:==============================:+
| 2-4 Source          | $N$                            | FWHM          | $V_{\text{lsr}}$ |                             | $N$                            |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
|                     | (cm$^{-2}$)                    | (km s$^{-1}$) | (km s$^{-1}$)    |                             | (cm$^{-2}$)                    |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 126348              | (5.0$\pm$1.3)$\times$10$^{14}$ | 8.7$\pm$2.3   | 75.1             | 43                          | (2.2$\pm$0.6)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 615590              | (7.9$\pm$2.1)$\times$10$^{14}$ | 3.8$\pm$1.6   | 40.0             | 60                          | (4.8$\pm$1.4)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 644284A             | (6.3$\pm$1.3)$\times$10$^{14}$ | 6.2$\pm$1.7   | 1.50             | 60                          | (3.8$\pm$0.9)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 693050              | (2.5$\pm$0.7)$\times$10$^{15}$ | 4.8$\pm$0.5   | -41.4            | 54                          | (1.3$\pm$0.4)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 705768              | (7.9$\pm$2.1)$\times$10$^{14}$ | 4.4$\pm$0.9   | -34.1            | 54                          | (4.3$\pm$1.3)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 707948              | (1.0$\pm$0.3)$\times$10$^{16}$ | 11.0$\pm$2.0  | -31.3            | 54                          | (5.4$\pm$1.6)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 717461A             | (5.0$\pm$1.0)$\times$10$^{14}$ | 4.4$\pm$0.9   | -51.5            | 51                          | (2.5$\pm$0.6)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 721992              | (2.5$\pm$0.5)$\times$10$^{15}$ | 3.0$\pm$0.1   | -57.9            | 50                          | (1.3$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 724566              | (2.5$\pm$0.5)$\times$10$^{15}$ | 4.6$\pm$0.6   | -56.4            | 50                          | (1.3$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 732038              | (7.9$\pm$1.6)$\times$10$^{14}$ | 4.3$\pm$1.2   | -63.8            | 49                          | (3.9$\pm$1.0)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 744757A             | (6.3$\pm$1.3)$\times$10$^{14}$ | 5.1$\pm$1.2   | -41.0            | 52                          | (3.3$\pm$0.8)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 767784              | (6.3$\pm$1.3)$\times$10$^{14}$ | 4.0$\pm$0.7   | -67.2            | 46                          | (2.9$\pm$0.7)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 865468A             | (6.3$\pm$1.3)$\times$10$^{15}$ | 5.8$\pm$0.5   | -26.8            | 45                          | (2.9$\pm$0.7)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 876288              | (3.2$\pm$0.8)$\times$10$^{14}$ | 3.0$\pm$0.6   | -96.5            | 33                          | (1.1$\pm$0.3)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| 881427C             | (7.9$\pm$1.6)$\times$10$^{15}$ | 5.3$\pm$0.4   | -11.3            | 52                          | (4.1$\pm$1.0)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G023.3891p00.1851   | (4.0$\pm$0.8)$\times$10$^{14}$ | 3.0$\pm$0.1   | 75.6             | 43                          | (1.7$\pm$0.5)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G025.6498p01.0491   | (1.6$\pm$0.3)$\times$10$^{15}$ | 6.0$\pm$0.9   | 41.3             | 50                          | (7.9$\pm$1.9)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G305.2017p00.2072A1 | (7.9$\pm$2.1)$\times$10$^{14}$ | 3.5$\pm$1.0   | -41.7            | 52                          | (4.2$\pm$1.2)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G314.3197p00.1125   | (5.0$\pm$1.0)$\times$10$^{14}$ | 5.9$\pm$0.8   | -49.8            | 51                          | (2.6$\pm$0.6)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G316.6412-00.0867   | (2.5$\pm$0.5)$\times$10$^{15}$ | 5.5$\pm$0.4   | -19.4            | 51                          | (1.3$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G318.0489p00.0854B  | (1.0$\pm$0.3)$\times$10$^{15}$ | 5.7$\pm$1.1   | -50.9            | 50                          | (5.0$\pm$1.5)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G318.9480-00.1969A1 | (4.0$\pm$0.8)$\times$10$^{15}$ | 4.7$\pm$0.3   | -34.5            | 53                          | (2.1$\pm$0.5)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G323.7399-00.2617B2 | (2.0$\pm$0.4)$\times$10$^{15}$ | 3.9$\pm$0.5   | -52.1            | 48                          | (9.7$\pm$2.4)$\times$10$^{16}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G327.1192p00.5103   | (2.5$\pm$0.5)$\times$10$^{15}$ | 6.7$\pm$1.7   | -84.1            | 44                          | (1.1$\pm$0.3)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G343.1261-00.0623   | (2.5$\pm$0.7)$\times$10$^{15}$ | 8.9$\pm$2.1   | -32.5            | 50                          | (1.3$\pm$0.4)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+
| G345.5043p00.3480   | (4.0$\pm$1.0)$\times$10$^{15}$ | 6.9$\pm$1.9   | -17.5            | 50                          | (2.0$\pm$0.6)$\times$10$^{17}$ |
+---------------------+--------------------------------+---------------+------------------+-----------------------------+--------------------------------+

# FWHM and $V_{\text{lsr}}$ of and compared to 

Figure [13](#fig:FWHMs_Vlsrs) shows the ratios of FWHM and differences of $V_{\text{lsr}}$ for and with respect to .

![](Figures/FWHMs_Vlsrs_wrtCH3OH.pdf)

# Best-fit parameters of 

Table [\[tab:fittings_33SO2\]](#tab:fittings_33SO2) lists the best-fit parameters for the transitions in the sources where it could be constrained.

+-------------------+------------------------------------------------------------------------+----------------------------------+--------------------------------+--------------------------------+
|                   |                                                                        | ($^{32}\ce{S}/^{33}\ce{S}$) $^b$ | from                           | from                           |
+:==================+:==============================:+:=============:+:=====================:+:================================:+:==============================:+:==============================:+
| 2-4 Source        | $N$                            | FWHM $^a$     | $V_{\text{lsr}}$ $^a$ |                                  | $N$                            | $N$                            |
+-------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+--------------------------------+
|                   | (cm$^{-2}$)                    | (km s$^{-1}$) | (km s$^{-1}$)         |                                  | (cm$^{-2}$)                    | (cm$^{-2}$)                    |
+-------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+--------------------------------+
| 615590            | (1.0$\pm$0.2)$\times$10$^{16}$ | 3.7           | 40.5                  | 93                               | (9.3$\pm$0.9)$\times$10$^{17}$ | (9.0$\pm$2.4)$\times$10$^{17}$ |
+-------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+--------------------------------+
| 644284A           | (7.0$\pm$1.0)$\times$10$^{15}$ | 6.0           | 2.6                   | 92                               | (6.5$\pm$1.4)$\times$10$^{17}$ | (5.6$\pm$1.5)$\times$10$^{17}$ |
+-------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+--------------------------------+
| 693050            | (6.0$\pm$1.5)$\times$10$^{15}$ | 3.5           | -41.2                 | 89                               | (5.3$\pm$0.5)$\times$10$^{17}$ | (4.3$\pm$1.1)$\times$10$^{17}$ |
+-------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+--------------------------------+
| G343.1261-00.0623 | (9.5$\pm$1.5)$\times$10$^{15}$ | 7.3           | -31.5                 | 87                               | (8.3$\pm$1.8)$\times$10$^{17}$ | (6.6$\pm$1.6)$\times$10$^{17}$ |
+-------------------+--------------------------------+---------------+-----------------------+----------------------------------+--------------------------------+--------------------------------+

$^a$ Uncertainties in the FWHMs and $V_{\text{lsr}}$ are $\lesssim0.5$ km s$^{-1}$.

$^b$ Values are rounded to zero decimals.

# Literature ratios

Table [\[tab:lit_ratios\]](#tab:lit_ratios) lists the literature values for $N$()/$N$(), $N$(OCS)/$N$(), and $N$()/$N$() gathered in this work.

+------------------+------------------------------+--------------------------------+-----------------------------------------+
| Object           | $N$()/$N$()                  | $N$()/$N$()                    | $N$()/$N$()                             |
+:=================+:=============================+:===============================+:========================================+
| *Gas phase*                                                                                                                |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
|                  |                              |                                |                                         |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| MYSOs $^a$       | (1), (2), (4), (10), (11)    | (1), (2), (4), (10), (11)      | \(1\) $-$ (13)                          |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| LYSOs $^b$       | (15), (16), (22), (23)       | \(15\) $-$ (17), (19) $-$ (23) | \(14\) $-$ (16), (18), (22), (23), (24) |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| *Interstellar ices*                                                                                                        |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
|                  |                              |                                |                                         |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| Dark clouds $^c$ | \(25\)                       | \(25\)                         | \(25\)                                  |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| MYSOs $^d$       | (26), (27)                   | \(27\)                         | (26), (27)                              |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| LYSOs $^e$       | (28), (29)                   |                                |                                         |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| *Solar system*                                                                                                             |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
|                  |                              |                                |                                         |
+------------------+------------------------------+--------------------------------+-----------------------------------------+
| Comets $^f$      | (30), (31), (33), (36), (37) | \(30\) $-$ (38)                | (30), (31), (33), (36), (37)            |
+------------------+------------------------------+--------------------------------+-----------------------------------------+

$^a$ (1) (cite: Hatchell1998); (2) (cite: vanderTak2000); (3) (cite: Hofner2001); (4) (cite: vanderTak2003); (5) (cite: Osorio2009); (6) (cite: Herpin2009); (7) (cite: Cesaroni2010); (8) (cite: Pillai2011); (9) (cite: vanderTak2013); (10) (cite: Gieser2019); (11) (cite: Fuente2021); (12) (cite: Mininni2021); (13) (cite: Fontani2023).

$^b$ (14) (cite: Tafalla2000); (15) (cite: Jorgensen2018); (16) (cite: Drozdovskaya2018); (17) (cite: Sahu2019); (18) (cite: Agundez2019); (19) (cite: vanGelder2020); (20) (cite: Manigand2020); (21) (cite: Yang2020); (22) (cite: delaVillarmois2023); (23) (cite: Kushwahaa2023); (24) (cite: Esplugues2023).

$^c$ (25) (cite: McClure2023).

$^d$ (26) (cite: Boogert1997); (27) (cite: Boogert2022).

$^e$ (28) (cite: Tobin2016); (29) (cite: Rocha2024).

$^f$ (30) (cite: DelloRusso1998); (31) (cite: Bockelee-Morvan2000); (32) (cite: Mumma2011); (33) (cite: LeRoy2015); (34) (cite: Biver2015); (35) (cite: DelloRusso2016); (36) (cite: Calmonte2016); (37) (cite: Schuhmann2019); (38) (cite: Saki2020).

# $N$()/$N$()

The ratios of the derived column densities for and are shown in Figure [14](#fig:NSO2_NOCS) as a function of luminosity. For comparison, ratios measured in the gas-phase of low-mass sources are also shown, together with ice observations towards comets, dark clouds, as well as both low- and high-mass protostars.

![](Figures/NSO2_NOCS.pdf)

[^1]: https://casa.nrao.edu

[^2]: http://cassis.irap.omp.eu/

</paper>

Write the methods card for this paper.