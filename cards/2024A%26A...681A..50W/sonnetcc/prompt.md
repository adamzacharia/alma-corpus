# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...681A..50W\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...681A..50W",
 "title": "ATOMIUM: Molecular inventory of 17 oxygen-rich evolved stars observed with ALMA",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Wallström, S. H. J.",
 "n_authors": 38,
 "arxiv_id": "2312.03467",
 "doi": "10.1051/0004-6361/202347632",
 "alma_projects_linked_by_archive": [
  "2018.1.00659.L"
 ]
}
```

Paper text:
<paper>
# ATOMIUM: Molecular inventory of 17 oxygen-rich evolved stars observed with ALMA[^2]

The dusty winds of cool evolved stars are a major contributor of the newly synthesised material enriching the Galaxy and future generations of stars. However, the details of the physics and chemistry behind dust formation and wind launching have yet to be pinpointed. Recent spatially resolved observations show the importance of gaining a more comprehensive view of the circumstellar chemistry, but a comparative study of the intricate interplay between chemistry and physics is still difficult because observational details such as frequencies and angular resolutions are rarely comparable.

Aiming to overcome these deficiencies, ATOMIUM is an ALMA Large Programme to study the physics and chemistry of the circumstellar envelopes of a diverse set of oxygen-rich evolved stars under homogeneous observing conditions at three angular resolutions between $\sim$0.02$\ensuremath{''} - 1.4\ensuremath{''}$. Here we summarize the molecular inventory of these sources, and the correlations between stellar parameters and molecular content.

Seventeen oxygen-rich or S-type asymptotic giant branch (AGB) and red supergiant (RSG) stars have been observed in several tunings with ALMA Band 6, targeting a range of molecules to probe the circumstellar envelope and especially the chemistry of dust formation close to the star. We systematically assigned the molecular carriers of the spectral lines and measured their spectroscopic parameters and the angular extent of the emission of each line from integrated intensity maps.

Across the ATOMIUM sample, we detect 291 transitions of 24 different molecules and their isotopologues. This includes several first detections in oxygen-rich AGB/RSG stars: PO $\varv=1$, SO$_2$ $\varv_1=1$ and $\varv_2=2$, and several high energy H$_2$O transitions. We also find several first detections in S-type AGB stars: vibrationally excited HCN $\varv_2=2,3$ and SiS $\varv=4,5,6$, as well as first detections of the molecules SiC, AlCl, and AlF in W Aql. Overall, we find strong correlations between the following molecular pairs: CS and SiS, CS and AlF, NaCl and KCl, AlO and SO, SO$_2$ and SO, and SO$_2$ and H$_2$O; meaning both molecules tend to have more detected emission lines in the same sources. The measured isotopic ratios of Si and S are found to be consistent with previous measurements, except for an anomalously high $^{29}$Si/$^{30}$Si ratio of $4 \pm 1$ in the RSG VX Sgr.

This paper presents the overall molecular inventory and an initial analysis of the large ATOMIUM dataset, laying the groundwork for future work deriving molecular abundances and abundance profiles using radiative transfer modeling which will provide more rigorous tests for chemical models.

# Introduction

Cool evolved stars are a major contributor of the gas and dust returned to the interstellar medium (cite: tielens_physics_2005) through their dusty winds which can reach mass-loss rates of up to 10$^{-4}$ M$_\odot$ yr$^{-1}$ (cite: hofner_mass_2018). Low- and intermediate-mass ($\sim$0.8 – 8 M$_\odot$) asymptotic giant branch (AGB) stars are known to have dust-driven winds, while the mass-loss mechanism of the rarer, more massive red supergiant (RSG) stars remains uncertain. In both cases, however, the details of the physics and chemistry behind dust formation and wind launching have yet to be pinpointed, a vital step in understanding how newly synthesised material from AGB and RSG stars enriches the Galaxy and future generations of stars.

These AGB and RSG stars and their accompanying circumstellar envelopes (CSEs) provide useful chemical laboratories for studying dust and molecule formation due to their relatively simple overall spherical structure and their (mostly) radial velocity fields. Other chemically interesting cool environments, such as star-forming regions or (proto)planetary disks, tend to have more complex spatial and velocity structures, making it more difficult to disentangle the effects of chemistry. The overall chemical composition of an AGB CSE depends on the C/O ratio of the central star (cite: habing_asymptotic_2003), as most of the less abundant element is locked up in CO. An oxygen-rich or M-type star (C/O \< 1) has more free oxygen to form for example silicate dust and oxygen-bearing molecules – such as SO, TiO, AlO – while a carbon-rich star (C/O \> 1) has more free carbon to form for example amorphous carbon dust and molecules such as HC$_3$N and SiC$_2$. Stars with C/O $\sim$ 1 are called S-type stars and have a mixed chemistry. The more massive RSGs are all oxygen-rich stars, due to extra nucleosynthesis processes such as hot-bottom burning (cite: herwig_evolution_2005), resulting in oxygen-rich CSEs.

To date more than 100 molecules and 15 dust species have been detected around AGB and RSG stars (cite: decin_evolution_2021). The difficult-to-observe H$_2$ is by far the most abundant molecule, but it is followed in abundance by CO, whose lower energy rotational transitions are easily excited over much of the CSE and readily observable with ground-based telescopes. Observations of CO and other molecular lines provide dynamical and physical information about the CSE, and help constrain chemical models of dust and molecule formation. A very efficient means of determining the molecular contents of diverse Galactic sources are spectral line surveys, covering wide frequency bands in the millimeter and sub-millimeter domain. A range of surveys has been carried out for evolved stars with single-dish telescopes, which have discovered a wealth of new molecules. For example, (cite: tenenbaum_arizona_2010) report the first detections of PO, AlO and AlOH in space, in the RSG VY CMa, as well as the first detections of NaCl, PN, NS, and HCO$^+$ in an oxygen-rich source; (cite: velilla_prieto_millimeter_2017) report the first detections of NO and H$_2$CO in an oxygen-rich source, namely IK Tau (a.k.a. NML Tau); (cite: de_beck_surprisingly_2020) report the first detections of silicon- and carbon-bearing species SiC$_2$, SiN, C$_2$H, and HC$_3$N towards an S-type star, W Aql; and in the extensively studied, high mass-loss rate carbon-rich star CW Leo (a.k.a. IRC+10216) refractory metal-containing species such as AlCl, AlF, MgNC, MgCN, NaCN, NaCl, and KCl are reported by (cite: cernicharo_2_2000; he_spectral_2008; pardo_ultra-deep_2022), alongside cyanopolyynes of the family HC$_{2n+1}$N, carbon chain radials up to C$_8$H, and cyclic compounds such as c-C$_3$H$_2$.

However, these single-dish observations at low angular resolution (typically $10\ensuremath{''} - 40\ensuremath{''}$) struggle to probe the spatial distributions of molecules in the CSE, which provide further vital constraints on chemical models. Greatly increased angular resolution is achieved with interferometry, alongside increased sensitivity allowing fainter molecular lines to be detected. This results in more accurate information on the relative excitation and formation of different species, and is especially useful for detecting rarer or short-lived species which are typically only seen close to the star especially those suspected to play a part in dust condensation, such as AlO or carbon chains (cite: agundez_chemical_2020). To date, only a handful of interferometric molecular line surveys of AGB stars have been carried out due to the large observing time requirements. These include studies of some sources that also were covered by single-dish surveys: the carbon-rich CW Leo (cite: patel_interferometric_2011) and the two oxygen-rich stars R Dor and IK Tau (cite: decin_study_2017; decin_alma_2018). The RSG VY CMa has also been studied in this way (cite: kaminski_interferometric_2013).

(cite: patel_interferometric_2011) observed the carbon-rich AGB star CW Leo with a 3$\ensuremath{''}$ beam using the Submillimeter Array (SMA). They detect $\sim$200 new lines of the molecules known from previous single-dish surveys, including narrow vibrationally excited lines (many from HCN) close to the star (cite: patel_submillimeter_2009). They note that many of their unassigned lines are also narrow, possibly produced by vibrationally excited transitions of polyatomic molecules for which laboratory measurements of rest frequencies were not yet available. With measurements of both emission sizes and velocities for a range of lines they are also able to characterise the wind acceleration, parameterised by a beta law velocity profile (cite: lamers_introduction_1999) with a fast acceleration ($\beta=0.5$).

(cite: kaminski_interferometric_2013) observed the very high mass-loss rate ($4\times10^{-4}$ M$_\odot$ yr$^{-1}$) and asymmetric RSG VY CMa with a 0.9$\ensuremath{''}$ beam, again using the SMA. They detect over 200 lines from 19 molecules, including AlCl, rotational emission from TiO for the first time in an oxygen-rich evolved star, and TiO$_2$ for the first time in space. A large number of lines of oxygen-rich molecules like SO$_2$ and SO are seen, as well as many lines of the relatively refractory NaCl including vibrationally excited transitions up to $\varv=3$. Most of the observed lines show multiple velocity components, and the molecular emission shows similar spatial complexity.

(cite: decin_study_2017; decin_alma_2018) observed two archetypal oxygen-rich AGB stars, the high mass-loss rate ($5\times10^{-6}$ M$_\odot$ yr$^{-1}$) IK Tau and the low mass-loss rate ($1\times10^{-7}$ M$_\odot$ yr$^{-1}$) R Dor, at $\sim$0.15$\ensuremath{''}$ angular resolution with the Atacama Large Millimeter and sub-millimeter Array (ALMA). They detect $\sim$200 lines from 15 different molecules, including dust precursors such as SiO, AlO, AlOH, TiO, and TiO$_2$. Highly vibrationally excited SiO (up to $\varv=5$) is detected in both sources close to the star, and AlO is detected far beyond the dust condensation radius showing that this molecule does not become entirely locked up in dust grains. The data is also used to characterise the wind acceleration of both sources, showing much slower accelerations than for the carbon-rich CW Leo ($\beta \sim 5-10$).

These interferometric surveys demonstrate the importance of spatially resolved observations for obtaining a more comprehensive view of the circumstellar chemistry, as different molecules and transitions can show emission at different spatial scales and with different morphologies. However, it is difficult to draw more general conclusions about AGB or RSG stars from the study of single sources. Even in aggregate, various studies have different sensitivities, frequency coverage, and angular resolutions, and hence are difficult to compare. The next step to elucidate the circumstellar chemistry is to observe a sample of stars with a range of stellar parameters, with identical observing setups. By performing homogeneous high-angular-resolution observations, we can directly compare the chemical inventories of different sources, and compare them with stellar parameters.

ALMA Tracing the Origins of Molecules formIng dUst in oxygen-rich M-type stars (ATOMIUM, Program ID: 2018.1.00659.L) is an ALMA Large Programme to observe 17 oxygen-rich AGB and RSG stars at high angular resolution in a range of molecular transitions (cite: decin_substellar_2020; gottlieb_atomium_2022). The ATOMIUM targets were chosen to represent a range of AGB mass-loss rates, chemical types (M-type and S-type stars), and pulsation behaviors (semi-regular variables (SR), long-period variables (LPV), and regular Mira variables). The sample also includes three RSG stars, and is summarised in Table [\[tab:sources\]](#tab:sources). ATOMIUM is the first ALMA Large Programme for stellar evolution, and consists of a set of homogeneous high-resolution observations that allow unambiguous comparison of the physicochemical properties of the winds of the 17 evolved stars, expanding the sample of evolved stars studied at such high angular resolution by a factor of four. It also provides a detailed picture of the chemical and dynamical processes throughout the stellar wind, including measurements of isotopic ratios which provide an important tracer of nucleosynthesis in the core of the star. Alongside the ATOMIUM overview paper (cite: gottlieb_atomium_2022), several in-depth studies of individual sources (cite: homan_atomium_2020; homan_atomium_2021; danilovich_chemical_2023), specific molecules (cite: danilovich_atomium_2021; baudry_atomium_2023), and comparisons with optical polarized light (cite: montarges_vltsphere_2023) have already resulted from this data.

This paper presents the molecular inventory of the 17 oxygen-rich AGB and RSG sources of the ATOMIUM sample. Section 2 briefly describes the observations undertaken with ALMA as part of the ATOMIUM Large Programme, and we summarize how the carriers of the spectral lines were assigned to specific molecules and how the spectroscopic parameters of the rotational lines (flux density, line width, and integrated area) were determined. In Section 3 we present our results, and Section 4 contains the conclusions. Additionally, the accompanying online tables include full lists of the molecular lines identified in the sample and in each source, including line parameters and molecular emission sizes, and all the spectra.

+:---------------------------+:--------------------------:+:--------------------------:+:--------------------------:+:--------------------------:+:--------------------------:+:--------------------------:+:--------------------------:+:--------------------------:+:--------------------------:+
| Source                     | Stellar                    | Pulsation                  | $P$                        | $T_\mathrm{eff}$           | Diameter$^{(1)}$           | $R_\ast ^{(2)}$            | MLR$^{(3)}$                | $v_\mathrm{exp}$           | $D^{(4)}$                  |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
|                            | type                       | type                       | \[days\]                   | \[K\]                      | \[mas\]                    | \[cm\]                     | \[M$_\odot$/yr\]           | \[km/s\]                   | \[pc\]                     |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| S Pav                      | M-type                     | SRa                        | 381                        | 3100                       | 12.0                       | 1.7E+13                    | 1.3E-07                    | 13.0                       | 190                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| RW Sco                     | M-type                     | Mira                       | 389                        | 3300                       | 4.9                        | 2.1E+13                    | 1.3E-07                    | 18.5                       | 560                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| T Mic                      | M-type                     | SRb                        | 347                        | 3300                       | 9.3                        | 1.2E+13                    | 1.4E-07                    | 12.7                       | 175                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| R Hya                      | M-type                     | Mira                       | 366                        | 2100                       | 23.0                       | 2.2E+13                    | 1.8E-07                    | 22.2                       | 126                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| SV Aqr                     | M-type                     | LPV                        | –                          | 3400                       | 4.4                        | 1.5E+13                    | 2.7E-07                    | 15.9                       | 445                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| U Her                      | M-type                     | Mira                       | 402                        | 3100                       | 11.0                       | 2.2E+13                    | 3.2E-07                    | 19.7                       | 266                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| U Del                      | M-type                     | SRb                        | 119                        | 2800                       | 7.9                        | 2.0E+13                    | 3.7E-07                    | 14.6                       | 330                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| V PsA                      | M-type                     | SRb                        | 148                        | 2400                       | 13.0                       | 2.7E+13                    | 4.8E-07                    | 18.8                       | 278                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| $\pi^1$ Gru                | S-type                     | SRb                        | 150                        | 2300                       | 21.0                       | 2.6E+13                    | 9.2E-07                    | 64.5                       | 164                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| R Aql                      | M-type                     | Mira                       | 268                        | 2800                       | 12.0                       | 2.1E+13                    | 1.6E-06                    | 12.8                       | 230                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| GY Aql                     | M-type                     | Mira                       | 468                        | 3100                       | 21.0                       | 6.4E+13                    | 2.3E-06                    | 15.0                       | 410                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| W Aql                      | S-type                     | Mira                       | 479                        | 2800                       | 11.0                       | 3.1E+13                    | 2.7E-06                    | 24.6                       | 375                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| KW Sgr                     | RSG                        | SRc                        | 647                        | 3700                       | 3.9                        | 7.0E+13                    | 3.6E-06                    | 27.7                       | 2400                       |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| IRC-10529                  | M-type                     | Mira                       | 680                        | 2700                       | 6.5                        | 4.5E+13                    | 1.0E-05                    | 21.8                       | 930                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| AH Sco                     | RSG                        | SRc                        | 738                        | 3700                       | 5.8                        | 9.8E+13                    | 1.0E-05                    | 35.4                       | 2260                       |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| IRC+10011                  | M-type                     | Mira                       | 660                        | 2700                       | 6.5                        | 3.6E+13                    | 1.9E-05                    | 23.1                       | 740                        |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| VX Sgr                     | RSG                        | SRc                        | 732                        | 3500                       | 8.8                        | 1.0E+14                    | 6.0E-05                    | 32.9                       | 1560                       |
+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+----------------------------+
| **Notes:** $^{(1)}$ Optical angular diameter.                                                                                                                                                                                                                                                   |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(2)}$ Calculated from the stellar angular diameter and distance.                                                                                                                                                                                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(3)}$ Scaled to the new distance estimate, see Section [2.3](#sect:mlrs).                                                                                                                                                                                                                    |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(4)}$ Several distances have been updated with respect to the values given in (cite: gottlieb_atomium_2022).                                                                                                                                                                                 |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **References:** $^{(a)}$ (cite: olofsson_mass_2002); $^{(b)}$ (cite: marigo_evolution_2008); $^{(c)}$ (cite: gottlieb_atomium_2022); $^{(d)}$ (cite: gaia_collaboration_gaia_2018);                                                                                                             |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(e)}$ (cite: bailer-jones_estimating_2021); $^{(f)}$ (cite: andriantsaralaza_distance_2022); $^{(g)}$ (cite: groenewegen_millimeter_1999); $^{(h)}$ (cite: perryman_hipparcos_1997);                                                                                                         |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(i)}$ (cite: de_beck_probing_2010); $^{(j)}$ (cite: young_co3–2_1995); $^{(k)}$ (cite: vlemmings_improved_2007); $^{(l)}$ (cite: doan_extended_2017); $^{(m)}$ (cite: loup_co_1993);                                                                                                         |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(n)}$ (cite: ramstedt_circumstellar_2017); $^{(o)}$ (cite: wittkowski_vltiamber_2017); $^{(p)}$ (cite: mauron_mass-loss_2011); $^{(q)}$ (cite: arroyo-torres_atmospheric_2013);                                                                                                              |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(r)}$ (cite: kiss_variability_2006); $^{(s)}$ (cite: jura_mass-losing_1990); $^{(t)}$ (cite: chen_structure_2008); $^{(u)}$ (cite: samus_general_2017); $^{(v)}$ (cite: chen_measuring_2007)                                                                                                 |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

# Data

## ALMA observations

The ATOMIUM ALMA Large Programme covers a frequency range of $\sim$213–270 GHz in 16 spectral tunings, with a total bandwidth of 27 GHz. Observations were carried out at three different spatial resolutions – low-resolution with beam sizes of $\sim0.8\ensuremath{''} - 1.4\ensuremath{''}$, medium-resolution with beam sizes of $\sim0.2\ensuremath{''} - 0.5\ensuremath{''}$, and high-resolution with beam sizes of $\sim0.02\ensuremath{''} - 0.05\ensuremath{''}$. The maximum scales which can be imaged (maximum recoverable scale, MRS) for each resolution are approximately $8 - 10\ensuremath{''}$, $1.5 - 4\ensuremath{''}$, and $0.4 - 0.6\ensuremath{''}$, respectively (cite: gottlieb_atomium_2022). The field of view (to half maximum sensitivity) is $22\ensuremath{''} - 26\ensuremath{''}$, depending on frequency. Only half the tunings, covering CO and some of the other lines with the most extended emission, were observed at the lowest spatial resolution. There is, however, missing flux for at least some molecules (notably CO) in some of our sources. This can occur both for lines with angular extent larger than the field of view, and for emission which is smooth on scales larger than the MRS. For example, in R Hya about 40% of the CO flux is resolved out (cite: homan_atomium_2021), $\pi^1$ Gru is missing $\sim$30–70% of the CO flux (cite: homan_atomium_2020), and W Aql is missing 66% of the CO flux (cite: danilovich_chemical_2023). There is likely also missing flux for other molecules such as HCN and some transitions of SO$_2$, in at least some sources. The full extent of missing flux has not been quantified as single-dish spectra of the same frequency ranges are not available for most of our sources.

Observations took place between 2018–2021. All the high resolution data were taken during June–July in 2019, and hence essentially samples, for each source, only one part of the stellar phase (cite: gottlieb_atomium_2022). Calibration and imaging were performed in CASA (cite: mcmullin_casa_2007) following standard ALMA procedures. The line-free continuum (mostly stellar emission) was identified and used for self-calibration, which was applied to all data, ensuring that the data for each star had a consistent position and flux density scale (measured in Jy/beam for the image cubes, and Jy for the extracted spectra). See Table E.2 in (cite: gottlieb_atomium_2022) for details of the continuum image properties. Image cubes were made (after continuum subtraction) for each separate spatial resolution. The channel spacing of 0.9765625 MHz gives a velocity resolution of 1.1–1.4 km s$^{-1}$ depending on frequency. The rms noise $\sigma_\mathrm{rms}$ per spectral channel is $\sim1-5$ mJy, depending on target elevation and requested noise level; the high-resolution data usually have the lowest noise and are the most sensitive to compact or clumpy emission, while the low-resolution data has the greatest surface brightness sensitivity. The observations and data reduction are described fully in (cite: gottlieb_atomium_2022), and the characteristics such as the rms noise level, $\sigma_\mathrm{rms}$, and angular resolution of each spectral cube are given in their Table E.3. Note that in some cases (such as very bright, compact emission or weak, extended emission) the standard reduction parameters may leave low-level artefacts in the images for individual lines; papers on specific lines or targets, using optimised imaging and combination of the different spatial resolutions, may give slightly different values from those reported here (cite: gottlieb_atomium_2022). To allow for this and for the propagation of errors when combining data taken at different epochs, we adopt a conservative flux scale uncertainty of 15% (although in some cases it may be much better than this).

## Processing and analysis

We used spectra of each source at high, medium, and low angular resolution to identify the various molecular transitions. Spectra were extracted in circular apertures, centered on the continuum peak, with diameters of 0.04$\ensuremath{''}$, 0.08$\ensuremath{''}$, and 0.12$\ensuremath{''}$ for the high-resolution data; diameters of 0.4$\ensuremath{''}$, 1.2$\ensuremath{''}$, and 3.6$\ensuremath{''}$ for the medium-resolution data; and diameters of 1.2$\ensuremath{''}$, 3.6$\ensuremath{''}$, and 10.8$\ensuremath{''}$ for the low-resolution data. At each resolution, the smallest aperture was chosen to be the average beam size rounded up to one significant figure, for consistency.

In each spectrum the line identification was carried out in a systematic way. Starting from a list of expected lines based on the line survey of IK Tau and R Dor by (cite: decin_alma_2018), at the position of each potential line a soft parabola function (cite: de_beck_probing_2010) was fit with a least squares fitting algorithm. A visual inspection then ruled out spurious fits, added missing lines, and adjusted the fit of weak and blended lines. The rms ($\sigma$) was measured from the parts of the spectrum more than three times the wind expansion velocity ($v_\mathrm{exp}$) away from any line, and any potential lines below 2.5$\sigma$ are considered non-detections. Any previously unknown lines were added to the line list, and identified if possible. Inspection of integrated intensity (moment 0) maps by eye further ensured any weak lines correspond to coherent emission across several channels rather than a noise fluctuation. We have also checked the intrinsic brightness (at 300 K) of the various transitions to ensure that the detected lines of each molecule are among the brightest lines in our frequency range. We do not exclude the possibility that further lines may be detected with a different data reduction method or by stacking data; however, we leave this to future papers.

+:-----------------+:----------------------+:-----------------+:-----------------+----------------------:+-----------------:+-------------------:+-----------------:+-----------------:+-----------------:+----------------------:+
| Source           | Line                  | $\nu_0$          | Res.$^{(1)}$     | Ap.$^{(2)}$           | $F_{peak}$       | $I$                | RW$^{(3)}$       | BW$^{(4)}$       | $w_{vel}$        | $r$$^{(5)}$           |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
|                  |                       | \[GHz\]          |                  | \[$\ensuremath{''}$\] | \[Jy\]           | \[Jy km s$^{-1}$\] | \[km s$^{-1}$\]  | \[km s$^{-1}$\]  | \[km s$^{-1}$\]  | \[$\ensuremath{''}$\] |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| AH Sco           | SiO $\varv=2$ $J=5-4$ | 214.089          | high             | 0.04                  | 1.103            | 7.765              | 23.5             | -21.6            | 45.1             | 0.08                  |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| AH Sco           | SiO $\varv=2$ $J=5-4$ | 214.089          | high             | 0.12                  | 1.679            | 11.892             | 23.5             | -18.9            | 42.4             | 0.08                  |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| AH Sco           | SiO $\varv=2$ $J=5-4$ | 214.089          | high             | 0.08                  | 1.644            | 11.594             | 23.5             | -18.9            | 42.4             | 0.08                  |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| AH Sco           | SiO $\varv=2$ $J=5-4$ | 214.089          | med              | 3.6                   | 2.604            | 15.148             | 15.3             | -14.7            | 30.1             | 0.37                  |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| AH Sco           | SiO $\varv=2$ $J=5-4$ | 214.089          | med              | 1.2                   | 2.616            | 15.449             | 18.1             | -14.7            | 32.8             | 0.37                  |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| AH Sco           | SiO $\varv=2$ $J=5-4$ | 214.089          | med              | 0.4                   | 2.552            | 14.964             | 20.8             | -20.2            | 41.0             | 0.37                  |
+------------------+-----------------------+------------------+------------------+-----------------------+------------------+--------------------+------------------+------------------+------------------+-----------------------+
| $\cdots$                                                                                                                                                                                                                        |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **Notes:** $^{(1)}$Spatial resolution of the data; $^{(2)}$Aperture diameter used to extract the spectrum; $^{(3)}$ Velocity of the red line wing;                                                                              |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(4)}$ Velocity of the blue line wing; $^{(5)}$ Angular emission radius.                                                                                                                                                      |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| The full version of the table (which also includes columns for uncertainties) is available at the CDS.                                                                                                                          |
+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example medium and high angular resolution spectra of R Hya are shown in Appendix C, with molecular identifications, while Appendix A contains more detailed information about the identified lines. Additional information about the lines and molecular data can be found in Appendix [5.1](#sect:app:lab-spec-data), Table A.1 gives a full list of identified molecules by source, Table A.2 gives the maximum radial extent of each molecule in each source, Table A.3 lists all identified molecular lines with references for the line parameters, and Table A.4 lists all the unidentified lines. Table A.5 list all detected lines in each source, and gives measurements taken at each spatial resolution (high, medium, low) where the line was detected. Each line was measured separately in the spectra extracted with the three different apertures given above.

Line parameters were extracted from each spectrum, and for each detected line its peak flux, integrated intensity, velocity width (full width at zero power), and angular extent (from its integrated intensity map, see below) was measured. The peak flux was taken to be the flux in the brightest channel included within the line extent. The spectral extent of a line was measured between the channels where each line wing reaches 2.5$\sigma$, with a minimum width of four channels ($\approx$5 km s$^{-1}$), thus defining the velocity width and integrated intensity. As this was done automatically, broad weak lines may have their velocity widths and hence integrated intensities underestimated. The uncertainty on the peak flux was taken to be the rms plus the 15% absolute flux uncertainty (see Section [2.1](#sect:data_alma)), and the uncertainty on the line width was taken to be the channel width.

Potentially blended lines and lines with absorption or double-peaked profiles were checked manually to ensure that the correct line region was chosen. For lines which are blended or truncated by the edge of an observing band, only a peak flux is reported, as measured at the line center, and for lines with absorption the "peak" flux value is actually the positive or negative extremum value. Note that some lines show (partial) absorption only at certain apertures, most commonly the smaller apertures. The measured line width was used to make integrated intensity (moment 0) maps by summing the intensities of all the spectral channels covered by a line. From these maps the maximum radial extent of the emission from each line was measured, defined as the maximum radial extent of the 3$\sigma$ contour enclosing the star (centered on the peak of the continuum emission). The contours were azimuthally smoothed (in bins with at least ten samples, corresponding to angular ranges of $\geq$60$^\circ$) to limit deviations due to noise, following the method in (cite: danilovich_atomium_2021). Note that for transitions with clumpy emission, this method may underestimate the extent of the emission. For transitions with no measured extent from this method an upper limit is given, equal to half the major axis of the restoring beam ($b_{maj}$/2). We also note that there may be diffuse extended emission of various molecules which is not properly imaged, or which is filtered out if its size is similar to (or greater than) the maximum recoverable scale. Such emission may be brought out with different data reduction techniques or spectral averaging.

A majority of detected lines are seen in the data at multiple angular resolutions, as expected; however some transitions are only seen in the high-resolution data. We note that this data is more sensitive so faint lines are more likely to be detected. Furthermore, very compact emission (less than a few hundred milliarcsec in diameter) is best detected in the highest angular resolution data, as it may otherwise be diluted in large extraction apertures or with larger beams, or have its apparent flux reduced by imaging artefacts.

## Mass-loss rate uncertainties

Mass-loss rates ($\dot{M}$) for the ATOMIUM sample were gathered from literature studies (see references in Table [\[tab:sources\]](#tab:sources)). However, these mass-loss rate determinations often assumed different distances to the stars than is used in this paper, and hence the mass-loss rate must be scaled to the new distance. This has been done using a simple formula to account for the dilution factor stemming from the distance to the star: $$\begin{equation}
    \dot{M}_\mathrm{new} = \dot{M}_\mathrm{old} \left( \frac{D_\mathrm{new}}{D_\mathrm{old}} \right)^2.
\end{equation}$$ Table [1](#tab:mlr_update) lists the factor by which this has changed the literature mass-loss rate, alongside more details about how the mass-loss rates were derived.

+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| Source          | $D_\mathrm{old}$ | $\dot{M}_\mathrm{old}^{(1)}$ | Deriv.$^{(2)}$  | N$_\mathrm{obs}$ | $\frac{\dot{M}_\mathrm{new}}{\dot{M}_\mathrm{old}}$ |
+:================+=================:+:============================:+:===============:+:================:+:===================================================:+
| AH Sco          | 2000             | 8.0E-06                      | a               | 1                | 1.3                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| GY Aql          | 540              | 4.0E-06                      | b               | 1                | 0.6                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| IRC-10529       | 620              | 4.5E-06                      | c               | 2                | 2.2                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| **IRC+10011**   | 740              | 1.9E-05                      | c               | **16**           | 1.0                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| KW Sgr          | 3000             | 5.6E-06                      | a               | 1                | 0.6                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| **$\pi^1$ Gru** | 150              | 7.7E-07                      | d               | **4**            | 1.2                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| R Aql           | 190              | 1.1E-06                      | e               | 2                | 1.5                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| **R Hya**       | 118              | 1.6E-07                      | c               | **7**            | 1.1                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| RW Sco          | 700              | 2.1E-07                      | f               | 2                | 0.6                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| S Pav           | 150              | 8.0E-08                      | g               | 1                | 1.6                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| SV Aqr          | 470              | 3.0E-07                      | g               | 2                | 0.9                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| T Mic           | 130              | 8.0E-08                      | g               | 2                | 1.8                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| U Del           | 210              | 1.5E-07                      | g               | 2                | 2.5                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| U Her           | 360              | 5.9E-07                      | e               | 1                | 0.5                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| V PsA           | 220              | 3.0E-07                      | g               | 1                | 1.6                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| **VX Sgr**      | 1570             | 6.1E-05                      | c               | **3**            | 1.0                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| **W Aql**       | 395              | 3.0E-06                      | g               | **21**           | 0.9                                                 |
+-----------------+------------------+------------------------------+-----------------+------------------+-----------------------------------------------------+
| $^{(1)}$ These values typically have large uncertainties of a factor $\sim$3–10.                                                                             |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| $^{(2)}$ Description of the various mass-loss rate derivations:                                                                                              |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| a: Empirical formula for 60 $\mu$m flux from (cite: jura_mass-losing_1990).                                                                                  |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| b: Empirical formula for CO flux based on (cite: knapp_mass_1985),                                                                                           |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| updated using (cite: mamon_photodissociation_1988).                                                                                                          |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| c: Empirical formula for CO flux derived from a grid of 1D                                                                                                   |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| radiative transfer models from (cite: de_beck_probing_2010).                                                                                                 |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| d: 3D non-LTE radiative transfer modeling using                                                                                                              |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| SHAPEMOL (cite: santander-garcia_shapemol_2015).                                                                                                             |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| e: 1D radiative transfer modeling, LVG model from (cite: morris_molecular_1980).                                                                             |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| f: Empirical formula for CO flux from (cite: olofsson_study_1993).                                                                                           |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| g: 1D non-LTE radiative transfer modeling using                                                                                                              |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| MCP (cite: schoier_models_2001).                                                                                                                             |
+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

: Mass-loss rates from literature.

Updating the distances to these sources has changed the derived mass-loss rate by at most a factor of 2.5. However, we expect the literature mass-loss rate values to have uncertainties larger than this (though they are seldom quantified), with determinations frequently based on only one or two independent observations which makes it difficult to disentangle the degeneracies between for example the mass-loss rate, temperature profile, and the outer radius of the wind. Sources with derived mass-loss rates based on more than two independent observational data points are highlighted in green, which is the case for only five sources: IRC+10011, $\pi^1$ Gru, R Hya, VX Sgr, and W Aql. W Aql has undoubtedly the best constrained mass-loss rate as it is based on direct modeling of 21 individual CO lines, and even here the model has an estimated uncertainty of a factor $\sim$3 (cite: danilovich_detailed_2014; ramstedt_circumstellar_2017). Furthermore, many of the mass-loss rates are derived using empirical formulae, based on CO line fluxes and some stellar parameters, rather than direct radiative transfer modelling of CO observations. These formulae involve a large number of assumptions resulting in uncertainties of at least a factor $\sim$3–5 (cite: de_beck_probing_2010; olofsson_study_1993), when they are quantified at all. Two of the mass-loss rates are derived from empirical formulae using the observed 60 $\mu$m flux (labeled "a" in Table [1](#tab:mlr_update)), which requires further assumptions about the wind velocity, dust properties, and gas-to-dust ratio.

The derived mass-loss rates also generally assume a constant and spherically symmetric mass loss, but the ATOMIUM observations have shown this is not true for any of our sources (cite: decin_substellar_2020): they all show significant structure in their winds, and some like $\pi^1$ Gru and R Hya are highly asymmetric. This is interpreted as the likely presence of a companion. If the companion shapes the wind into an equatorial density enhancement, this could change the derived mass-loss rate by a factor of up to three if the system is seen face-on, and potentially much more if the system is seen edge-on (cite: el_mellah_wind_2020). Furthermore, simply the assumption of a constant mass-loss rate has been shown to change the derived mass-loss rate by a factor of a few (cite: kemper_mass_2003; decin_variable_2007).

Taken together, these factors result in typical uncertainties on the mass-loss rates of up to an order of magnitude. However, the mass-loss rate still provides a useful way to order the sources to look for general trends, and in the absence of more precise estimates we will continue to use the values in Table [\[tab:sources\]](#tab:sources) in our analysis. Improving the mass-loss rate estimates for the ATOMIUM sources will be undertaken in a future publication, using radiative transfer modelling of homogeneous single-dish observations of at least four CO transitions per source, combined with the spatial information from the ALMA observations.

# Results and discussion

This section presents an overview of the molecular inventory in Section [3.1](#sect:atomium_stats), molecular emission sizes in Section [3.2](#sect:extents), correlations between various stellar parameters and their molecular content in Section [3.3](#sect:corr), an analysis of the spatial distributions of SO and SO$_2$ in Section [3.4](#sect:so_so2), isotopic ratios for a subset of the molecules in Section [3.5](#sect:isotopic_ratios), and a discussion of the unidentified lines in Section [3.6](#sect:ulines)

## Overview of molecular inventory

Across the variety of 17 AGB and RSG sources in the ATOMIUM sample, we detect 287 molecular lines of which 29 remain unidentified. Emission from a total of 24 molecules has been identified, namely: AlCl, AlF, AlO, AlOH, CO, CN, CS, H$_2$O, H$_2$S, HC$_3$N, HCN, KCl, NaCl, OH, PO, SO, SO$_2$, SiC, SiC$_2$, SiN, SiO, SiS, TiO, and TiO$_2$; and 19 isotopologues thereof containing one or more of atoms of $^{13}$C, $^{17}$O, $^{29}$Si, $^{30}$Si, $^{33}$S, $^{34}$S, and $^{37}$Cl.

This includes some first detections in oxygen-rich AGB and RSG stars:

- PO in the vibrationally excited $\varv=1$ transition, detected in the RSG AH Sco and the AGB stars IRC+10011, IRC-10529, R Hya, and S Pav.

- SO$_2$ in the high-energy vibrationally excited $\varv_2=2$ and $\varv_1=1$ transitions, detected in the RSGs AH Sco and VX Sgr, respectively.

- Of the ten detected rotational transitions from various vibrational states of H$_2$O, all but one are the first identifications in space, as is one high energy transition of OH (cite: baudry_atomium_2023).

and first detections in S-type AGB stars:

- High vibrational level transitions of HCN $\varv_2 = 2,3$ in $\pi^1$ Gru and W Aql. Vibrationally excited HCN has been studied for C-rich AGB stars by (cite: jeste_vibrationally_2022).

- High vibrational level transitions of SiS $\varv=4,5,6$ in $\pi^1$ Gru and W Aql. Such high vibrational levels have previously been observed in CW Leo by (cite: patel_interferometric_2011).

- Two transitions of the SiS double isotopologue $^{29}$Si$^{33}$S in W Aql, previously observed in CW Leo by (cite: patel_interferometric_2011).

- Four transitions of HC$_3$N in W Aql, confirming the tentative stacking detection by (cite: de_beck_surprisingly_2020).

- One transition of SiC in W Aql, to be more thoroughly discussed in (cite: danilovich_chemical_2023). SiC has previously been detected in 12 C-rich sources by (cite: massalkhi_abundance_2018).

- Several transitions of AlCl and one transition of AlF in W Aql, as discussed in (cite: danilovich_atomium_2021).

A visual overview of the molecules detected in each source can be seen in Figure [1](#fig:mol_MLR), where the sources are arranged in order of increasing mass-loss rate (note that molecules detected in only one source TiO$_2$ in VX Sgr; and AlCl, $^{13}$CN, SiN, SiC, SiC$_2$, and HC$_3$N in W Aql are not included).

![](lineID_MLRtable.pdf)

Looking at the overall molecular content, we can group together some similar sources:

- The two S-type sources, $\pi^1$ Gru and W Aql, are unsurprisingly different from the other, oxygen-rich sources. They are notably lacking in oxygen-bearing molecules, such as SO and SO$_2$, and show a large number of SiS lines, however W Aql is significantly more molecule-rich than $\pi^1$ Gru.

- IRC+10011 and IRC-10529 are very similar in molecular content, showing, for example, a range of Al- and Cl-bearing molecules, relatively few SO$_2$ lines, and a relatively large number of SiS lines. GY Aql also has a similar molecular content to IRC+10011 and IRC-10529, though it shows comparatively more SO$_2$ and fewer SiS lines.

- Two sources are very line-poor: U Del and the RSG KW Sgr. Beyond the molecules seen in all sources (CO, SiO, HCN) these two sources only contain a single H$_2$O line each and KW Sgr exhibits two SO lines. An explanation may lie in the lack of detection of high-$\varv$ SiO lines (see below) in both sources, which may indicate weak shocks in the inner wind and hence post-shock temperatures too low to drive a rich chemistry and excite many of the high-$\varv$ molecular lines. Furthermore, KW Sgr is a younger RSG than AH Sco or VX Sgr, with a spectral classification of M2, similar to Betelgeuse which is also known to be relatively poor in molecules (cite: huggins_neutral_1994).

From Figure [1](#fig:mol_MLR) we can see that CO, HCN, and SiO are ubiquitous, as expected from previous studies, with similar numbers of lines detected in almost all sources (excepting the large number of vibrationally excited HCN lines in W Aql). All sources show vibrationally excited (up to $\varv=4$) lines of SiO except the line-poor KW Sgr (up to $\varv=2$) and U Del (up to $\varv=1$), and also SV Aqr (up to $\varv=1$). Three sources also show $^{30}$SiO lines up to $\varv=5$: R Aql, R Hya, and S Pav. Note that the $\varv=5$ transitions of the main SiO isotopologue were not covered by our observations. Many of the SiO lines have maser components, especially the high-$\varv$ lines but also some $\varv=0$ lines (Pimpanuwat et al., in prep.).

SO and SO$_2$ are detected in a majority of sources, excepting the line-poor U Del and KW Sgr (in which SO but not SO$_2$ is seen), and the S-type sources $\pi^1$ Gru and W Aql. A large number of SO$_2$ $\varv=0$ and $\varv_2=1$ lines are detected in many sources, and the two RSGs AH Sco and VX Sgr also show a few high-energy $\varv_1=1$ or $\varv_2=2$ transitions. SO$_2$ is one of the most widespread species in our sample, partially due to its nature as an asymmetric top which exhibits many different energy levels throughout its energy ladder, which are fairly easily populated by radiation and collisions. The other sulfur-bearing molecules H$_2$S, SiS, and CS are expected to have abundances that scale with mass-loss rate, and hence are more likely to be seen in high mass-loss-rate sources (cite: decin_alma_2018; danilovich_sulphur-bearing_2017; danilovich_sulphur-bearing_2018). Indeed, we only see H$_2$S in the highest mass-loss-rate sources, but for SiS and CS there is no clear trend with mass-loss rate. (cite: danilovich_sulphur_2016; danilovich_rotational_2020) also found a difference in the spatial distributions of SO and SO$_2$ in low- and high-mass-loss-rate sources, which is discussed further in Section [3.4](#sect:so_so2).

SiS shows transitions from several isotopologues, and high-$\varv$ lines (up to $\varv=5-6$) are seen in both S-type sources, $\pi^1$ Gru and W Aql, which are expected to have higher SiS abundances (cite: schoier_abundance_2007; danilovich_sulphur-bearing_2018). All other sources only show lines of SiS up to $\varv=1$, except IRC+10011 and IRC-10529 where $\varv=3$ is reached.

H$_2$O is detected in all the sources in our sample except the two S-type stars, in several high-lying rotational transitions with lower state energy levels above $\sim$3900 K, including high vibrational energy states. Four OH hyperfine split transitions with similar high energies ($E_\mathrm{low} \gtrsim 4800$ K) are also detected. This includes many first detections of these transitions in space; they are discussed in detail in (cite: baudry_atomium_2023) and hence will not be extensively discussed here.

The halide-bearing molecules AlF, NaCl, and KCl are mostly found in high mass-loss-rate sources, although AlF (and AlOH) are also seen in the intermediate mass-loss-rate source U Her. Specifically the chlorine-bearing molecules KCl and NaCl are found only in IRC+10011, IRC-10529, and GY Aql. It is perhaps unexpected that the chlorides are missing in the RSGs AH Sco and VX Sgr, as NaCl is very strong in the RSG VY CMa (cite: tenenbaum_arizona_2010; quintana-lacaci_history_2023), however VY CMa is a more evolved RSG with a higher mass-loss rate than the RSGs in our sample. Furthermore, another chlorine-bearing molecule, AlCl, is only found in the S-type star W Aql, in which we do not detect NaCl or KCl, so AlCl seems to require different formation and/or excitation conditions.

W Aql is also the only source to show transitions of $^{13}$CN, SiN, SiC, SiC$_2$, and HC$_3$N (note $^{12}$CN was not covered by our observations). This is unsurprising as it is a bright, nearby S-type star with a fairly carbon-rich outflow (cite: de_beck_surprisingly_2020). The other molecule only seen in a single source is TiO$_2$ in VX Sgr, which may be because VX Sgr is the highest-mass-loss-rate source in our sample and so its denser wind may allow less abundant molecules to be detected.

## Angular extents of molecules

+:----------------+:----------------------------:+:----------------------------:+:------------------------------------:+-----------------:+
| Mol.            | Range in                     | Median                       | Max                                  | N$_\mathrm{sou}$ |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
|                 | $r_\mathrm{max}$ ($R_\star$) | $r_\mathrm{max}$ ($R_\star$) | $r_\mathrm{max}$ ($\ensuremath{''}$) |                  |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SiC             | 2.1                          | –                            | 0.01                                 | 1                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| TiO$_2$         | 14                           | –                            | 0.06                                 | 1                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| OH              | 3.0 – 17                     | 6                            | 0.20                                 | 6                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| AlOH            | 1.3 – 45                     | 4                            | 0.20                                 | 5                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| AlF             | 2.8 – 81                     | 12                           | 0.44                                 | 7                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| PO              | 2.0 – 120                    | 26                           | 0.33                                 | 11               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| AlCl            | 130                          | –                            | 0.69                                 | 1                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| AlO             | 1.2 – 150                    | 3                            | 0.67                                 | 9                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| KCl             | 140 – 150                    | 145                          | 0.50                                 | 2                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| TiO             | 1.5 – 160                    | 6                            | 0.47                                 | 7                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| HC$_3$N         | 210                          | –                            | 1.14                                 | 1                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| H$_2$O          | 5.3 – 230                    | 36                           | 0.66                                 | 15               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SiC$_2$         | 270                          | –                            | 1.47                                 | 1                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| NaCl            | 1.5 – 280                    | 250                          | 0.90                                 | 3                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SiN             | 390                          | –                            | 2.14                                 | 1                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| H$_2$S          | 7.2 – 490                    | 140                          | 1.60                                 | 5                |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| HCN             | 22 – 590                     | 120                          | 1.92                                 | 17               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SiS             | 5.5 – 610                    | 210                          | 1.97                                 | 10               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| CS              | 13 – 640                     | 150                          | 3.51                                 | 10               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SO$_2$          | 4.3 – 710                    | 290                          | 2.31                                 | 13               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SO              | 5.1 – 780                    | 340                          | 2.53                                 | 14               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| SiO             | 140 – 1100                   | 440                          | 3.42                                 | 17               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| CO              | 29 – 2400                    | 1300                         | 7.87                                 | 17               |
+-----------------+------------------------------+------------------------------+--------------------------------------+------------------+
| **Notes:** Maximum extents in CO are likely underestimated                                                                              |
+-----------------------------------------------------------------------------------------------------------------------------------------+
| and are marked with $^\dagger$. Transitions with no measurable                                                                          |
+-----------------------------------------------------------------------------------------------------------------------------------------+
| extent are noted as upper limits equal to the radius of the                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------+
| beam ($b_{maj}$/2). The molecules are arranged according to                                                                             |
+-----------------------------------------------------------------------------------------------------------------------------------------+
| the maximum measured $r_\mathrm{max}$ in $R_\star$.                                                                                     |
+-----------------------------------------------------------------------------------------------------------------------------------------+

: Maximum measured radial extent of each molecule across all sources.

While a full analysis of the spatial distributions of various molecules is beyond the scope of this paper, we found it useful as a first step to simply compare their observationally measured extents, as defined in Section [2.2](#sect:analysis). Table [2](#tab:molext_permol) shows the measured angular extent of each molecule across the 17 ATOMIUM sources. For each molecule, we have taken the maximum measured angular extent ($r_\mathrm{max}$) in each source, and then give the range and median of these measurements in units of the stellar radius, $R_\star$ (see Table [\[tab:sources\]](#tab:sources) for $R_\star$ values of each source). The maximum $r_\mathrm{max}$ for each molecule is also given in arcseconds. The maximum extents of CO are almost certainly underestimates because the emission of this molecule typically extends beyond the field of view of the observations.

Some of the smallest emission extents are found for the molecules TiO$_2$, OH, AlOH, and AlF. It is not surprising that these molecules are mainly seen close to the star, in the densest part of the wind, as this is predicted by chemical models (cite: agundez_chemical_2020; mangan_kinetic_2021), especially for the Al-bearing molecules which are expected to participate in dust formation. However, OH is a special case as the observed transitions all have very high lower state energies ($E_\mathrm{low} \geq 4800$ K) which will only be excited close to the star. In fact, 1.6 GHz OH maser emission has been measured up to $\sim$$100-1000$ R$_\star$ in for example IRC+10011 and R Aql (cite: bowers_circumstellar_1983), U Her (cite: chapman_oh_1994), and the RSG VX Sgr (cite: szymczak_polarization_1997).

The largest angular extents, $>$1.5$\ensuremath{''}$, are mainly found for molecules which are seen in a majority of sources: CO, SiO, SO, SO$_2$, CS, SiS, and HCN. However, for almost all molecules there are some sources where the maximum measured extent is very small. Which source it is varies by molecule, and its value is often an outlier among the sample. For example, in CO the smallest $r_\mathrm{max}$ of 29 $R_\star$ in the line-poor RSG KW Sgr is much smaller than the next smallest value of 530 $R_\star$ in AH Sco. V PsA has the smallest measured $r_\mathrm{max}$ in HCN, SO, and SO$_2$; R Hya shows the smallest extents in SiS and CS; and the smallest measured $r_\mathrm{max}$ in SiO is in $\pi^1$ Gru.

There are some interesting observations to be made from this summary from a chemical standpoint. First, AlO extends further out than AlOH, though this is only true for the RSGs VX Sgr and AH Sco, which have much larger AlO extents than the other sources: $\geq$100 $R_\star$. They also have the largest $r_\mathrm{max}$ in AlOH, at 45 and 8 $R_\star$, respectively smaller than their AlO extents. This is unexpected as AlOH is formed from AlO (by reaction with H$_2$O and H$_2$), although AlOH is also easily photolysed back to AlO (cite: mangan_kinetic_2021). The other three AGB sources with detections of both AlOH and AlO show slightly larger extents in AlOH. So here we have a dichotomy between the RSG and AGB sources, where perhaps the photolysis of AlOH to AlO is more efficient in the RSGs explaining their large AlO extents.

Another surprising observation is that TiO extends further out than TiO$_2$ in the only star where TiO$_2$ is detected: the RSG VX Sgr. VX Sgr shows a maximum extent in TiO of 65 $R_\star$, larger than the 14 $R_\star$ extent in TiO$_2$. This might indicate that TiO$_2$ is depleted because it is taking part in the formation of dust particles in the inner wind.

## Correlations

To get an overview of how the molecular content varies by source, we have calculated Kendall’s $\tau_b$ rank correlation coefficients (cite: kendall_treatment_1945) for various stellar parameters and the molecular content of each source. These are shown in Figure [2](#fig:corr_table). Kendall’s rank correlations are chosen as a non-parametric measure of correlation, that does not assume linear relationships between variables and is applicable to ordinal data. This allows us to use the differing number of detected lines of a given molecule as a (very rough) proxy for its relative abundance in different sources. The number of detected lines is a function of molecular parameters and excitation conditions as well as abundance, which we cannot properly take into account without radiative transfer modeling. However, by ranking the sources by the number of detected lines we can nevertheless determine which groups of molecules tend to coincide by having relatively large numbers of lines in the same sources. We also negate the need to normalize different molecules by the absolute number of potentially detectable lines in our frequency range. Many alternative techniques, such as Pearson’s correlations or principal component analysis, assume linear relationships between variables and hence are less applicable to our data at this initial analysis stage.

To calculate the Kendall’s $\tau_b$ correlation coefficients the sources were ranked (by measured value for stellar parameters and by number of detected lines for molecules) for each variable, and the ranks between every pair of variables were compared (adjusting for ties). This assesses how well the relationship between the two variables can be described by a monotonic function, that is, whether the first variable tends to increase as the second does and vice versa. The variables being correlated are the effective temperatures, mass-loss rates, terminal expansion velocities, and pulsation periods (as given in Table [\[tab:sources\]](#tab:sources)), and the number of lines detected for each molecule and its isotopologues. Molecules which are found in only one source (TiO$_2$ in VX Sgr, and AlCl, HC$_3$N, SiC$_2$, SiN, and $^{13}$CN in W Aql) have not been included. Generally, we assume that a larger number of detected lines of a given molecule implies a higher molecular abundance; however there may be additional effects making the detection of, for example, highly vibrationally excited lines more likely. These will be discussed for each molecule in the following sections.

![](correlation_table_pval.pdf)

As we have more than ten sources to compare, the sampling distribution of Kendall’s $\tau_b$ is approximately a normal Gaussian distribution (cite: kendall_new_1938). We therefore use p-values[^3] corresponding to 1$\sigma$ (p \< 0.15865), 2$\sigma$ (p \< 0.02275), and 3$\sigma$ (p \< 0.00135) to determine which correlations are significant. We consider a correlation coefficient $\gtrsim$0.5 to be a strong correlation, which is generally only seen for correlations with at least 2$\sigma$ significance. Correlations with 3$\sigma$ significance have coefficients $\geq$0.64 and hence will be termed very strong correlations. For simplicity, we use a single term to refer to both significance and strength of correlation, as they are strongly related, and will refer to correlations with 2$\sigma$ significance as strong correlations, and those with 1$\sigma$ significance as weak correlations. Figure [2](#fig:corr_table) is colorized by the value of the correlation coefficient, with stronger positive correlations in a darker blue. For further visual differentiation, 3$\sigma$ correlation coefficients are written in boldface, 2$\sigma$ in regular font, and 1$\sigma$ in small italics. Correlation coefficients with p-values above 0.15865 (that is lower than 1$\sigma$ significance) are not included in our analysis or in the figure.

![](dendrogram_complete.pdf)

The molecular correlations with at least a 1$\sigma$ significance were then used to calculate a dendrogram (see Figure [3](#fig:dendrogram)) of the hierarchical relationships between the different parameters, using the farthest point (a.k.a. complete linkage) algorithm for hierarchical clustering. This dendrogram shows which parameters are most similar to each other in terms of their correlations to all the other parameters, and groups them into seven clusters shown with different colors. Note that this grouping may split up pairs of parameters that are strongly correlated with each other but have dissimilar correlations with other parameters. These clusters are reflected in Figure [2](#fig:corr_table), and the calculated correlations will now be discussed cluster by cluster for simplicity.

Cluster 1: HCN and CO is shown with green lines in Figure [3](#fig:dendrogram) and discussed in Sect [3.3.1](#sect:cluster1); Cluster 2: AlF, CS, H$_2$S, and AlOH is shown with red lines and discussed in Sect [3.3.2](#sect:cluster2); Cluster 3: $v_\mathrm{exp}$ and $P$ is shown with cyan lines and discussed in Sect [3.3.3](#sect:cluster3); Cluster 4: SiS, $\dot{M}$, NaCl, and KCl is shown with purple lines discussed in Sect [3.3.4](#sect:cluster4); Cluster 5: AlO and SO is shown with yellow lines and discussed in Sect [3.3.5](#sect:cluster5); Cluster 6: PO, TiO, SO$_2$, H$_2$O, OH, and SiO is shown with black lines and discussed in Sect [3.3.6](#sect:cluster6); and Cluster 7: $T_\mathrm{eff}$ is discussed in Sect [3.3.7](#sect:cluster7).

### Cluster 1: HCN, CO

The first cluster contains the correlated molecules HCN and CO. For these molecules the $\varv=0$ transitions of the main isotopologues are seen in all sources, so more detected lines means the detection of isotopologues ($^{13}$CO, C$^{17}$O, H$^{13}$CN) or vibrationally excited transitions (CO $\varv=1$; HCN $\varv_2=1,2,3$; H$^{13}$CN $\varv_2=1$).

The isotopologues of HCN and CO tend to be detected in the same sources, as one might expect for both isotopologues with $^{13}$C. $^{13}$CO is detected in all sources except SV Aqr, and H$^{13}$CN is detected in all sources except SV Aqr, U Del, and V PsA. C$^{17}$O is only detected in two sources: IRC-10529 and W Aql. From this we can assume that SV Aqr, U Del, and V PsA either have relatively low $^{13}$C abundances or faint HCN emission, while IRC-10529 may have relatively high $^{17}$O abundances and W Aql is the source with by far the brightest emission in the main CO isotopologue. Similarly, the vibrationally excited transitions in HCN and CO tend to coincide. Vibrationally excited HCN is detected in six sources: IRC+10011, $\pi^1$ Gru, R Hya, W Aql, and the RSGs AH Sco and VX Sgr, four of which also show vibrationally excited H$^{13}$CN. These six sources are also among the 11 which show emission in the CO $\varv=1$ line.

Detecting more lines of HCN and CO is correlated with more detected lines of AlF, CS, SiS, AlO, TiO, and SiO, as well as a higher mass-loss rate ($\dot{M}$). Additionally, CO is correlated with detecting more lines of H$_2$S, NaCl, KCl, and PO; while HCN is correlated with detecting more lines of AlOH, SO, and SO$_2$, as well as a larger expansion velocity ($v_\mathrm{exp}$). The detection of more isotopologues and vibrationally excited lines of CO and HCN at higher mass-loss rates is due to a denser wind, and most of the correlated molecules are also preferentially seen in denser winds. Some of these molecules, such as SiS and H$_2$S, are known tracers of higher mass-loss rate winds (cite: danilovich_sulphur-bearing_2017; danilovich_sulphur-bearing_2018). Others, such as AlF, AlOH, AlO, and KCl, are expected to have fairly low abundances (cite: agundez_chemical_2020) and hence would only be detectable in a sufficiently dense wind. To further explain the observed correlations, a higher $\dot{M}$ is also correlated with a higher expansion velocity, and some of the molecules like SiO, PO, and SO$_2$ show vibrationally excited transitions in similar sources as vibrationally excited CO and HCN, which may imply these molecules are excited in similar regions of the wind.

### Cluster 2: AlF, CS, H$_2$S, AlOH

The second cluster contains the molecules AlF, CS, H$_2$S, and AlOH. AlF is detected in 7/17 sources GY Aql, IRC+10011, IRC-10529, U Her, W Aql, and the RSGs AH Sco and VX Sgr of which W Aql also shows the corresponding $\varv=1$ transition. CS is detected in one transition in 10/17 sources, of which five sources also show a $^{13}$CS line: GY Aql, IRC+10011, IRC-10529, VX Sgr, and W Aql. H$_2$S has one detected transition, in 5/17 sources: AH Sco, GY Aql, IRC+10011, IRC-10529, and VX Sgr. AlOH has two $\varv=0$ transitions, and is detected in 5/17 sources: AH Sco, GY Aql, IRC+10011, U Her, and VX Sgr.

AlF and CS are very strongly correlated, with all five sources showing $^{13}$CS also detected in AlF. Further, all four molecules in this cluster are strongly correlated with each other and tend to be detected in the same sources. 4/5 sources showing H$_2$S also show AlOH, and all sources with either molecule also show AlF. All four molecules are also correlated with a longer pulsation period ($P$), higher mass-loss rate ($\dot{M}$), and detecting more lines of SiS, NaCl, AlO, and SO. Three-out-of-four molecules are further correlated with detecting more lines of HCN, CO, KCl, and PO, as well as a larger expansion velocity ($v_\mathrm{exp}$).

These correlations can largely be explained by the similarities between the four sources AH Sco, GY Aql, IRC+10011, and VX Sgr. These sources have the second to eighth longest periods, and highest to seventh highest mass-loss rates. They all show a fair number of SiS lines, and include two of the three sources with detections of NaCl (see Sect [3.3.4](#sect:cluster4)). The RSGs AH Sco and VX Sgr are the two sources which show the most lines of both AlO and SO (see further discussion in Sect [3.3.5](#sect:cluster5)). Regarding HCN and CO: all four sources show their $^{13}$C isotopologues and the CO $\varv=1$ transition, three show vibrationally excited HCN and two also show vibrationally excited H$^{13}$CN. IRC+10011 is one of two sources showing KCl emission. All four sources are among the 11 showing PO emission, and the group contains 2/5 sources showing vibrationally excited transitions of PO. Finally, these four sources have the third to ninth largest expansion velocities.

The strong correlation between AlOH and AlO is expected due to their close chemical coupling (cite: mangan_kinetic_2021; gobrecht_bottom-up_2022). The strong correlation between AlOH and AlF probably comes from AlF’s formation reaction AlOH + HF $\rightarrow$ AlF + H$_2$O; and the correlation between AlO and AlF also follows from the lesser formation reaction AlO + HF $\rightarrow$ AlF + OH (cite: danilovich_atomium_2021).

### Cluster 3: v$_\mathrm{exp}$, $P$

The third cluster contains expansion velocity (v$_\mathrm{exp}$) and pulsation period ($P$), which are weakly correlated with each other. The clustering of these parameters is not unexpected, as for AGB stars both expansion velocity and pulsation period tend to increase as they evolve (cite: habing_asymptotic_2003), along with the mass-loss rate. In fact, for a constant and spherical mass loss we expect a perfect correlation between v$_\mathrm{exp}$ and the mass-loss rate, so the correlation of 0.48 seen here is further evidence of wind asymmetries.

A larger expansion velocity and longer pulsation period is correlated with detecting more lines of AlF, H$_2$S, AlOH, and SiS, as well as a larger mass-loss rate. The expansion velocity is also correlated with detecting more lines of HCN, while the pulsation period is correlated with detecting more lines of CS, AlO, and SO. As discussed in Section [3.3.1](#sect:cluster1), most of these molecules are preferentially detected in a dense (higher $\dot{M}$) wind.

### Cluster 4: SiS, $\dot{M}$, NaCl, KCl

The fourth cluster contains the molecules SiS, NaCl, and KCl, along with the mass-loss rate ($\dot{M}$). NaCl is detected in three sources: GY Aql, IRC+10011, and IRC-10529, of which IRC+10011 and IRC-10529 also show vibrationally excited transitions and transitions of Na$^{37}$Cl. KCl is detected only in these same two sources: IRC+10011 and IRC-10529. SiS is detected in 10/17 sources, while its various isotopologues of $^{29}$Si, $^{30}$Si, $^{33}$S, and $^{34}$S are detected in between five and seven sources, including GY Aql, IRC+10011, and IRC-10529. GY Aql also shows vibrationally excited transitions of SiS up to $\varv=1$, while IRC+10011 and IRC-10529 show vibrationally excited transitions up to $\varv=3$. The only sources showing higher vibrationally excited transitions of SiS (up to $\varv=6$) are the two S-type sources $\pi^1$ Gru and W Aql, which are expected to have higher SiS abundances (cite: danilovich_sulphur-bearing_2018), and also show transitions in all the isotopologues. Furthermore, IRC+10011, IRC-10529, GY Aql, $\pi^1$ Gru, and W Aql have between the second and ninth highest mass-loss rates in our sample.

Detecting more lines of SiS and a higher mass-loss rate are correlated with detecting more lines of HCN, CO, AlF, CS, H$_2$S, AlOH, and of course NaCl and KCl, along with larger expansion velocities (v$_\mathrm{exp}$) and longer pulsation periods ($P$). These correlations can largely be explained by the molecular content of GY Aql, IRC+10011, IRC-10529, $\pi^1$ Gru, and W Aql. As noted above, these sources show many lines of SiS and high mass-loss rates. Most of them are detected in vibrationally excited transitions of HCN, and IRC-10529 and W Aql are the only sources to show a transition of the $^{17}$O isotopologue of CO. All but $\pi^1$ Gru show transitions of AlF and CS, and they make up 3/5 and 2/5 of the sources showing transitions of H$_2$S and AlOH, respectively. When it comes to expansion velocities $\pi^1$ Gru has by far the largest, and the other sources are up to the tenth largest. They also have the fourth to eighth longest periods, except $\pi^1$ Gru which instead has one of the shortest periods in our sample. Furthermore, as noted in Section [3.3.3](#sect:cluster3), AGB stars tend to increase in mass-loss rate, expansion velocity, and pulsation period as they evolve, explaining their correlation.

Within this cluster, the chemically similar KCl and NaCl are very strongly correlated with each other. They are also correlated with detecting more lines of CO, AlF, CS, H$_2$S, and PO. NaCl is additionally correlated with detecting more lines of AlOH. The strong correlation between KCl and NaCl is because they are both formed from reactions of the metal atom with HCl (cite: plane_experimental_1989; helmer_experimental_1993). The correlation with another halogen-bearing molecule, AlF, implies that these chemically related molecules may coexist in similar environments in the stellar wind, though note that the only source where AlCl is detected, W Aql, does not show any transitions of KCl or NaCl. Through AlF the correlations with AlOH and the sulfur-bearing CS and H$_2$S can be explained (see Section [3.3.2](#sect:cluster2)), and the correlation with PO may be due to the main sources containing NaCl and KCl IRC+10011 and IRC-10529 also showing all the detected PO transitions, although they are only 2/5 sources to do so.

### Cluster 5: AlO, SO

The fifth cluster contains the molecules AlO and SO, which are strongly correlated with each other. AlO is detected in 9/17 sources of which four also show vibrationally excited transitions: R Aql, U Her, and the RSGs AH Sco and VX Sgr. SO is detected in 14/17 sources, ten of which also show $^{34}$SO. The less abundant isotopologue $^{33}$SO is detected in five sources, and the single detected SO $\varv=1$ transition is observed in seven sources. Of the sources showing transitions of AlO, the vast majority are detected in either both isotopologues or one isotopologue and the $\varv=1$ transition of SO. Three of these sources AH Sco, U Her, and VX Sgr are seen in both SO isotopologues and its $\varv=1$ transition.

The detection of more lines of AlO and SO is correlated with detecting more lines of HCN, AlF, CS, H$_2$S, AlOH, PO, TiO, SO$_2$, H$_2$O, and OH, as well as longer pulsation periods ($P$). Additionally, detecting more lines of AlO is correlated with detecting more lines of CO and a higher mass-loss rate ($\dot{M}$). Overall, AlO and SO are correlated with the other oxygen-bearing molecules, as expected, but also with the molecules in Cluster 1 (HCN, CO) and Cluster 2 (AlF, CS, H$_2$S, AlOH). As explained in Sect [3.3.2](#sect:cluster2), the strong correlation between AlO and AlOH stems from their close chemical coupling, but the chemical links to SO and H$_2$S are less clear. One might suspect a connection through the sulfur chemistry, as both AlO and SO are also correlated with CS, but neither is correlated with SiS. However, it may be that the conditions required to populate the higher energy levels of SiS (and hence have more detected lines of SiS) differ from the conditions that excite more transitions of (vibrationally excited) AlO and (vibrationally excited and/or isotopologues of) SO. Overall, both Cluster 1 and Cluster 2 molecules tend to have many detected lines in the three sources showing the most lines of AlO and SO AH Sco, U Her, and VX Sgr which may explain the correlations. The grouping of the low mass-loss rate AGB star U Her with the high mass-loss rate RSGs AH Sco and VX Sgr here is unexpected, and will be explored further in a future paper.

### Cluster 6: PO, TiO, SO$_2$, H$_2$O, OH, SiO

The sixth cluster contains the remaining oxygen-bearing molecules: PO, TiO, SO$_2$, H$_2$O, OH, and SiO. A PO doublet is detected in 11/17 sources, of which five sources IRC+10011, IRC-10529, R Hya, S Pav, and the RSG AH Sco also show the corresponding $\varv=1$ doublet. TiO is detected in 7/17 sources, with vibrationally excited transitions detected in three sources: R Hya, and the RSGs AH Sco and VX Sgr. SO$_2$ is detected in 13/17 sources, with $^{34}$SO$_2$ in nine sources and vibrationally excited transitions detected in seven sources. Six of these sources have detections of both $^{34}$SO$_2$ and vibrationally excited SO$_2$: AH Sco, R Aql, R Hya, RW Sco, U Her, and VX Sgr. H$_2$O is detected in 15/17 sources, with intrinsically fainter and/or higher energy transitions in progressively fewer sources. OH is detected in 6/17 sources, of which five show both detected $\varv=0$ doublets: R Aql, R Hya, S Pav, T Mic, and VX Sgr. SiO is detected in all sources: the main isotopologue in $\varv=0$ and $\varv=1$ and both $^{29}$SiO and $^{30}$SiO in a $\varv=0$ transition. So more detected transitions implies the detection of more highly vibrationally excited transitions: up to $\varv=4$ in the main isotopologue, which is seen in 13/17 sources; up to $^{29}$SiO $\varv=3$ which is seen in six sources IRC+10011, IRC-10529, R Aql, R Hya, S Pav, and W Aql; and up to $^{30}$SiO $\varv=5$ which is seen in four sources IRC+10011, R Aql, R Hya, and S Pav.

The molecules in this cluster are all correlated with each other, as expected, and most also show correlations with the other oxygen-bearing molecules. PO, TiO, and SiO are correlated with CO; PO, TiO, SO$_2$, and H$_2$O are correlated with AlOH; and all except SiO are correlated with AlO and SO.

PO is very strongly correlated with H$_2$O, which supports experimental findings that the reaction of excited P atoms with H$_2$O is a major formation route for PO (cite: douglas_experimental_2022). The five sources with the most detected PO lines that is the ones showing the $\varv=1$ transition: AH Sco, IRC+10011, IRC-10529, R Hya, and S Pav are also among the sources with the most detected H$_2$O lines, including R Hya which is the only source to show all ten H$_2$O transitions. Conversely, the six sources with no detected PO transitions KW Sgr, $\pi^1$ Gru, SV Aqr, U Del, V PsA, and W Aql also show the fewest detected H$_2$O lines. The two S-type sources, $\pi^1$ Gru and W Aql, show neither PO nor H$_2$O lines, and the others only have one to two H$_2$O lines and are overall quite line-poor. However, from the dendrogram in Figure [3](#fig:dendrogram) we can see that PO is less closely grouped with H$_2$O than SO$_2$, TiO, and OH are. This is likely due to PO showing correlations that H$_2$O lacks with a range of molecules CO, CS, H$_2$S, NaCl, and KCl in addition to their shared correlations with the other oxygen-bearing molecules. This may be mostly due to IRC+10011 and IRC-10529 which are, for example, two of the three sources with detected NaCl or KCl, and two of the five sources showing H$_2$S. Conversely, in R Hya and S Pav, which show the most H$_2$O lines, we do not detect any transitions of NaCl, KCl, or H$_2$S.

Detecting more lines of TiO is correlated with detecting more lines of HCN, CO, and H$_2$S, alongside its correlations with the other oxygen-bearing molecules. There are up to nine TiO lines, with vibrationally excited transitions in $\varv=1$, with $E_\mathrm{low}$ values around 1500 K, and $\varv=2$, with $E_\mathrm{low}$ values around 3000 K. Hence detecting more lines of TiO implies more vibrationally excited lines, as is also the case for HCN and CO. The three sources with the most TiO lines AH Sco, R Hya, and VX Sgr are also the only sources to show vibrationally excited TiO transitions. The $^{13}$C isotopologues of HCN and CO are detected in all three of these sources, as are the CO $\varv=1$ and HCN $\varv_2=1$ transitions. The vibrationally excited CO $\varv=1$ has an $E_\mathrm{low}$ value around 3000 K, just as the $\varv=2$ transitions of TiO do, and the HCN $\varv_2=1$ transitions have $E_\mathrm{low}$ values around 1000 K, roughly similar to the $\varv=1$ transitions of TiO. This implies that these vibrationally excited transitions may originate in similar regions of the circumstellar envelope, potentially explaining their correlation.

SO$_2$ and H$_2$O are very strongly correlated with each other, and SO$_2$ is also very strongly correlated with SO. The four sources with the most transitions of SO$_2$ AH Sco, R Hya, U Her, and VX Sgr are also the four with the most SO transitions: this includes transitions of its $^{33}$S and $^{34}$S isotopologues, as well as the one vibrationally excited SO transition. These four sources are also in the half of the sample with the most detected H$_2$O transitions, as indeed are all seven of the sources with the most SO$_2$ transitions.

SO$_2$ and SO are chemically connected by the fast reaction SO + OH $\rightarrow$ SO$_2$ + H (cite: demore_chemical_1997). As SO$_2$ is created from SO, one would expect these molecules to be anti-correlated, but this is probably ameliorated by photolysis of SO$_2$ back to SO. This reaction also helps explain the strong correlation between SO$_2$ and OH, and its correlation with H$_2$O as observationally the photodissociation of H$_2$O into OH is linked with an abundance peak in SO (cite: danilovich_sulphur_2016). We detect up to 66 lines of SO$_2$ in our sources, with vibrational levels up to $\varv_2=2$. A majority ($\sim$65%) of all the detected SO$_2$ lines are in the $\varv=0$ state, and most of the rest are in the $\varv_2=1$ state. The energy of the lower transition level ($E_\mathrm{low}$) values are up to 2300 K, with the $\varv=0$ transitions spanning the whole range, while the $\varv_2=1$ transitions have $E_\mathrm{low}$ values above 750 K, and the four $\varv_1=1$ and three $\varv_2=2$ transitions all have energies above 1500 K. The single vibrationally excited transition of SO has an $E_\mathrm{low}$ value around 1600 K. The ten detected H$_2$O lines have much higher $E_\mathrm{low}$ values ($\geq$3900 K) and many are in vibrationally excited states. There is some indication that in sources with more detected transitions of SO$_2$, SO, and H$_2$O, these transitions are probing a hotter gas as they generally have high $E_\mathrm{low}$ values. However, the H$_2$O transitions we can detect have much higher energies than any SO$_2$ or SO transitions, implying they are probing a different region of the wind, and furthermore these sources also show more transitions of $^{33}$S and $^{34}$S isotopologues. Therefore, the strong correlations between SO$_2$ and SO, and SO$_2$ and H$_2$O seem to also reflect increased abundances of all three molecules in certain sources.

OH only shows significant correlations with the other oxygen-bearing molecules: strong correlations with SO$_2$, H$_2$O, and TiO, and weak correlations with AlO, SO, PO, and SiO. The strong correlation between OH and SO$_2$ can be explained by the fast SO$_2$ formation reaction described above. OH and H$_2$O are expected to be chemically related, we only detect transitions at high energies $\geq$3900 K for H$_2$O, and $\geq$4700 K for OH which are likely to be excited in similar regions around the star. The strong correlation between OH and TiO is surprising from a chemical standpoint as they would be expected to be anti-correlated due to the fast reaction TiO + OH $\rightarrow$ TiO$_2$ + H. However, the two molecules are not necessarily co-located even if they are found in the same sources, so this reaction may not be very prominent. The detection of TiO$_2$ does not help resolve this issue as its transitions are inherently fairly weak, and hence not unexpectedly TiO$_2$ is detected in only the highest mass-loss rate source, VX Sgr,

SiO shows strong correlations with CO, H$_2$O, and PO; and weak correlations with larger pulsation amplitudes, and detecting more lines of HCN, SO$_2$, TiO, and OH. SiO is seen in every source due to its strong $\varv=0$ and $\varv=1$ lines, but some sources show more highly vibrationally excited transitions up to $\varv=5$, and lines from the $^{29}$SiO and $^{30}$SiO isotopologues. The five sources with the most PO transitions AH Sco, IRC+10011, IRC-10529, R Hya, and S Pav are among the seven sources with the most SiO transitions. These sources also have among the most CO and H$_2$O transitions. Most of the SiO transitions with $\varv>0$ are dominated by maser emission and weak masers are seen even in $\varv=0$ for some stars (Pimpanuwat et al., in prep). The strong correlations with CO, H$_2$O and PO may indicate these high-$\varv$ SiO masers, with $E_\mathrm{low}$ values up to $\sim$8600 K, form in similar regions around the star as the high-energy lines of H$_2$O and PO, and the $\varv=1$ line of CO. Similarly, sources with more detected transitions of HCN, SO$_2$, TiO, and OH also tend to show vibrationally excited lines of these molecules, which may also form in similar regions.

### Cluster 7: $T_\mathrm{eff}$

Finally, we have a cluster containing only the effective temperature of the star, $T_\mathrm{eff}$, which shows the only significant negative correlation: a weak negative correlation with detecting more lines of AlOH. There are two detected lines of AlOH, and both are low energy $\varv=0$ transitions. Two lines of AlOH are detected in GY Aql, IRC+10011, and the RSG VX Sgr, while a single line is detected in U Her and the RSG AH Sco. GY Aql, IRC+10011, and U Her have effective temperatures at or below the median value for our sources, while the RSGs VX Sgr and AH Sco have the highest effective temperatures. So this negative correlation between effective temperature and detections of AlOH seems to mainly hold for AGB sources. The correlation might potentially be explained by a relative lack of alumina dust (and hence more free Al to form AlOH) in these sources. There is some evidence for alumina dust being the major dust component in warmer semi-regular variable AGB stars, as it can form and survive at higher temperatures than silicate dust (cite: gobrecht_dust_2016), and GY Aql, IRC+10011, and U Her are all relatively cool Mira variables.

## SO and SO$_2$ spatial distributions

While a full analysis of the spatially resolved molecular data, including a radiative transfer analysis to obtain molecular abundance distributions, is beyond the scope of this paper, we have performed an initial analysis of the spatial distributions of SO and SO$_2$ and how they relate to the mass-loss rate of the source. As was first put forward by (cite: danilovich_sulphur_2016), there are two classes of SO distributions around AGB stars. For the lower mass-loss rate stars, the SO abundance peak is centred on the star, whereas for the higher mass-loss rate AGB stars, the relative SO abundance has a shell-like distribution. (cite: danilovich_sulphur_2016) found that the $e$-folding radius (the radius at which the abundance has dropped by a factor of $1/e$) of SO for the low mass-loss rate stars and the radius of the abundance peak for the higher mass-loss rate stars closely corresponded to the photodissociation radius of H$_2$O (cite: netzer_mass_1987; maercker_hifi_2016). This was interpreted to be the result of different SO formation pathways with varying wind density. A similar analysis could not be performed in that work for SO$_2$ since there were not enough detected lines for the higher mass-loss rate stars.

Here, we carefully examine the data to ascertain whether our observations are consistent with the distributions first proposed by (cite: danilovich_sulphur_2016). Hence we must define the two classes of SO and SO$_2$ distributions observationally. We consider a centralized SO or SO$_2$ distribution to be one where, for the majority of detected lines, the peak of the molecular emission in centred on the continuum peak and decreases monotonically with distance from the star. Conversely, for a shell-like distribution, the molecular emission for most lines does not decrease uniformly with angular distance from the star: the radial distribution is either flat or shows a second peak offset from the continuum peak and often associated with a (broken) ring-like structure. The shell-like distributions may be apparent in integrated intensity maps, but are generally more clearly seen in channel maps (see Appendix [6](#app:so_so2_distr)). They are also more clearly detectable in lower-energy lines.

SO and SO$_2$ were detected for most of the stars in the ATOMIUM sample. The only stars without SO and SO$_2$ detections are the two S-type stars, W Aql and $\pi^1$ Gru, and the line-poor U Del. The line-poor RSG KW Sgr was detected in SO but not in SO$_2$. Henceforth, when referring to "all" stars in discussing SO and SO$_2$ detections, these sources are not included.

In Appendix [6](#app:so_so2_distr) we show channel maps of the bright SO$_2$ $\varv=0$ $J_{K_a,K_c}=14_{0,14}-13_{1,13}$ line at 244.254 GHz in all the sources. The channel maps of R Aql, GY Aql, IRC-10529, and IRC+10011 (Figures [11](#fig:raql_so2)–[14](#fig:irc+10011_so2)), as well as VX Sgr (Figure [16](#fig:vxsgr_so2)), clearly show an overall shell-like structure. A similar shell-like structure is also seen for SO in these sources (shown around R Aql in the $\varv=0$ $N_J=5_{5}-4_{4}$ line at 215.221 GHz in Fig. [17](#fig:raql_so)), but the SO emission is brighter closer to the continuum peak that is, the star itelf with fainter extended structures distributed similarly to the SO$_2$. These minor differences suggest that SO$_2$ is predominantly found further from the star than SO is, which could be the result of SO$_2$ being a daughter species (formed from SO) for this group of stars. A similar trend is not seen for the stars with centralized SO$_2$ emission, where SO and SO$_2$ are both distributed similarly close to the continuum peaks. If anything, there is a slight tendency among the centralized SO$_2$ sources for the SO emission to be more extended than the SO$_2$ emission, but this could be a result of different abundances, some SO lines being inherently brighter than many SO$_2$ lines, or differing excitation conditions between the examined lines.

### AGB stars

The two brightest SO lines covered by our frequency setup are $N_J=5_5-4_4$ at 215.221 GHz and $N_J=6_5-5_4$ at 251.826 GHz, the two lines with $\Delta N = \Delta J = -1$ and $\varv=0$. These two lines are detected for all 14 stars with any SO detections. Overall six SO lines in the $\varv=0$ vibrational ground state are detected in our sample, with $E_\mathrm{low} \sim 10 - 90$ K. The most energetic line detected in our sample is the $N_J=6_7-5_6$ line at 259.857 GHz ($E_\mathrm{low}=1635$ K) in the first vibrationally excited state ($\varv=1$), which was detected for ten stars. The only other line in $\varv=1$ that was covered by our observations has a predicted intensity (cite: pickett_submillimeter_1998) almost three orders of magnitude lower than the detected line, so we do not expect to detect it. With such a small number of SO lines covered over a relatively narrow range of energies, aside from the single line in $\varv=1$, it is difficult to draw any firm conclusions about trends across the sample. Without a more detailed analysis involving radiative transfer modelling, which is beyond the scope of the present work, we cannot easily determine which lines were not detected for a particular source because of excitation conditions in the CSE or because of the sensitivity of our observations.

SO$_2$ gives us more opportunity for such an analysis since many more lines, coming from a wide range of energy levels, fall in the covered frequency range and many of these were detected by our observations. One source, V PsA shows only two detected SO$_2$ lines: $J_{K_a,K_c} = 14_{0,14}-13_{1,13}$ at 244.254 GHz and $J_{K_a,K_c} = 30_{4,26}-30_{3,27}$ at 259.599 GHz. These are the lines with the highest predicted intensities (at 300 K) suggesting that sensitivity is the main limitation to detecting further SO$_2$ lines. With so few lines, we cannot draw any further conclusions for V PsA and exclude it from further discussion of SO$_2$. The other ten AGB stars for which we detect SO$_2$ (GY Aql, IRC+10011, IRC$-$10529, R Aql, R Hya, RW Sco, S Pav, SV Aqr, T Mic, and U Her), all have detections of at least six lines in the ground vibrational state (with $30~\mathrm{K} \leq E_\mathrm{low} \leq 280~\mathrm{K}$). Four stars (R Aql, R Hya, U Her and S Pav) also have detections of at least four lines in the $\varv_2=1$ vibrational state.

The observational categories defined above, with shell-like or centralized SO$_2$ distributions, approximately correspond to the categories put forward by (cite: danilovich_sulphur_2016) for SO, and are applicable to SO$_2$ as the emission of these two molecules for the same star tends to be broadly similar. Ordering the sources with SO$_2$ detections by mass-loss rate, as in Table [3](#tab:so2E), shows a general tendency for the low mass-loss-rate sources to have centralized distributions and higher mass-loss-rate sources to have shell-like distributions. We note, however, that the mass-loss rates for many of the stars in the ATOMIUM sample are uncertain (see Section [2.3](#sect:mlrs)).

+:------------------+:-----------------:+:---------------------:+:-----------------:+:----------------------+
| Source            | Max $r$           | Med. $E_\mathrm{low}$ | N                 | SO$_2$                |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
|                   | R$_\ast$          | \[K\]                 |                   | distribution          |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| S Pav             | 144               | 443                   | 35                | centralized           |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| RW Sco            | 451               | 83                    | 17                | centralized$^\dagger$ |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| T Mic             | 214               | 119                   | 21                | centralized           |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| R Hya             | 51                | 281                   | 33                | centralized           |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| SV Aqr            | 282               | 61                    | 7                 | centralized$^\dagger$ |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| U Her             | 289               | 489                   | 38                | centralized           |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| R Aql             | 510               | 138                   | 23                | shell-like            |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| GY Aql            | 188               | 82                    | 15                | shell-like            |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| IRC-10529         | 711               | 66                    | 10                | shell-like            |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| IRC+10011         | 692               | 82                    | 11                | shell-like            |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| AH Sco            | 342               | 816                   | 55                | centralized           |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| VX Sgr            | 400               | 816                   | 57                | shell-like            |
+-------------------+-------------------+-----------------------+-------------------+-----------------------+
| **Notes:** Spatial distributions with uncertain classifications due                                       |
+-----------------------------------------------------------------------------------------------------------+
| to faint SO$_2$ emission are marked with $^\dagger$. AGB stars are listed                                 |
+-----------------------------------------------------------------------------------------------------------+
| above the horizontal line and RSGs below.                                                                 |
+-----------------------------------------------------------------------------------------------------------+

: SO$_2$ spatial distributions, radial extents, and median lower level energies in all sources.

From an examination of the detected SO$_2$ lines for each AGB source, we also found a tendency for the sources with shell-like emission to be detected in lower-energy SO$_2$ lines, while the sources with centralized emission tended to be detected in more higher-energy lines (in addition to the lower-energy lines). Three out of the six stars with centralized distributions (R Hya, U Her and S Pav) also show vibrationally excited emission. In contrast, only one star with shell-like emission (R Aql) has vibrationally excited SO$_2$ detections. Furthermore, some of the highest energy SO$_2$ lines in the ground vibrational state (such as $J_{K_a,K_c} = 45_{6,40} - 44_{7,37}$ at 229.750 GHz with $E_\mathrm{low} = 1034$ K) are only detected in the centralized AGB sources. To quantify this trend, Table [3](#tab:so2E) includes the average of the lower energy levels of each detected line for each star. Overall, there is a trend for the sources with a shell-like distribution to have lower median $E_\mathrm{low}$ values than the sources with a centralized distribution. This trend is confounded by RW Sco and SV Aqr, two centralized sources with median $E_\mathrm{low}$ values below 100 K. However, these sources both show faint SO$_2$ emission, making the classification of their emission distribution more difficult. They also have the fewest SO$_2$ detections among the centralized sources, tending to show only the brightest SO$_2$ lines which generally have low $E_\mathrm{low}$ values.

The observed trend between SO$_2$ line energy and spatial distribution is not a consequence of naturally having greater spatial resolution for the nearest sources, since our two most distant sources (IRC$-$10529 and IRC+10011 see Table [\[tab:sources\]](#tab:sources)) have shell-like distributions of SO$_2$ lines, while two of the nearest sources (T Mic and R Hya) have centralized SO$_2$ lines. It is also not caused by lines with different energies being excited at different distances from the star, since this dichotomy holds if we use only the $J_{K_a,K_c}=14_{0,14}-13_{1,13}$ line at 244.254 GHz, which is one of the brightest and most frequently detected lines, to make the determination. We also note that there is a general tendency for centralized sources to have more SO$_2$ lines detected than the shell-like sources: the maximum radial extent of SO$_2$ is found to be negatively correlated ($r \sim -0.3$) with the median $E_\mathrm{low}$ values and the number of SO$_2$ lines detected in each source. This is most likely a consequence of the excitation conditions. The SO$_2$ in centralized sources is found closer to the star and hence in a warmer environment, while a significant portion of the shell-like emission originates further out in a cooler region of the wind. At higher temperatures where there are more potential SO$_2$ transitions to be excited, and hence unsurprising that more (and more energetic) SO$_2$ lines are detected.

![](SO2_obs_vs_modelled_MLRorder.png)

We can also compare the measured extents of SO$_2$ in our AGB sources with what is expected from the chemical model of (cite: van_de_sande_determining_2018), for which calculations for each ATOMIUM source (using the stellar parameters in Table [\[tab:sources\]](#tab:sources)) is shown in Figure [4](#fig:so2_chem_models). The sources are arranged as in Table [3](#tab:so2E), in order of increasing mass-loss rate, and for each the colored bar shows the modeled $e$-folding radius of the SO$_2$ abundance, and the black line the maximum measured 3$\sigma$ extent of SO$_2$ lines from our observations. The chemical model assumes a power-law temperature profile with exponent $\varepsilon$, as implemented in (cite: van_de_sande_determining_2018) and (cite: maes_sensitivity_2023): $$\begin{equation}
T = T_\star \left(\frac{r}{R_\star}\right)^{-\varepsilon},
\end{equation}$$ where $T_\star$ is the surface temperature of the AGB star and $R_\star$ the stellar radius. As the temperature profile in the outflows is generally not known, a range of models with different temperature profiles, varying $\varepsilon$ from 0.3 to 1.0 (in steps of 0.05), were calculated. This range of models is included in Figure [4](#fig:so2_chem_models) as an uncertainty on the model result.

An increase in the SO$_2$ radius with increasing mass-loss rate is clearly seen from the model results, and the observationally measured extents broadly follow the same trend. In general, the measured SO$_2$ extents are larger than the modeled $e$-folding radii, and some discrepancy is expected when comparing modeled abundances with measured emission intensities, which does not take, for example, excitation effects into account. There are, however, two significant outliers: RW Sco which has a much larger measured SO$_2$ extent than expected from the models, and R Hya whose measured extent is much smaller than expected. There are several reasons to suspect the mass-loss rate we use for RW Sco is underestimated, which would explain its larger measured extent. First, its SO$_2$ distribution is shell-like rather than centralized, suggesting it should have a relatively high mass-loss rate to follow the SO$_2$ distribution trend. Second, the mass-loss rate value is taken from (cite: groenewegen_millimeter_1999), who use an empirical formula from (cite: olofsson_study_1993) linking the integrated CO intensity with the mass-loss rate. (cite: olofsson_study_1993) see evidence that their formula underestimates the mass-loss rates for low mass-loss rate objects, like RW Sco. This is in addition to the inherent uncertainties in the formula, which are a factor of $\sim$5. The discrepancy between the measured extent of SO$_2$ and the prediction from the chemical model is further evidence that the mass-loss rate of RW Sco may be underestimated. As for the unexpectedly small observed extent of SO$_2$ in R Hya, its geometry may provide an explanation: (cite: homan_atomium_2021) find evidence for an equatorial density enhancement, and possible rotating disk, in the inner 0.4$\ensuremath{''}$ of the wind, which corresponds to $\sim$35 $R_\star$. This is similar to the maximum measured extent of SO$_2$ (51 $R_\star$), so it may be that SO$_2$ is largely confined to this disk, or not abundant enough to be detected outside it. Furthermore, the equatorial density enhancement increases the uncertainty of the calculated mass-loss rate by a factor of a few (cite: el_mellah_wind_2020). Some discrepancy may also be caused by the limitations of the chemical model: it assumes a smooth, spherically symmetric outflow, with a constant expansion velocity and mass-loss rate. R Hya, with its equatorial density enhancement, deviates significantly from these assumptions. Additionally, most of the ATOMIUM sources show additional structure or deviations from spherical symmetry (cite: decin_substellar_2020; gottlieb_atomium_2022) which may affect the chemistry in the wind.

### RSG stars

The two red supergiants, VX Sgr and AH Sco, are detected in seven and six SO transitions, respectively, out of the seven total detected in ATOMIUM. They are also extensively detected in SO$_2$, with more than 45 lines seen for each star, and approximately a third of this count lying in the $\varv_2=1$ excited state. There are additionally three tentative detections of SO$_2$ towards AH Sco in the $\varv_2=2$ state and four tentative detections towards VX Sgr in the $\varv_1=1$ state. Previous studies of the more massive and highly evolved red supergiants VY CMa and NML Cyg (cite: adande_sulfur_2013; Andrews2022) report asymmetric and localised emission for both stars, including multiple components of SO and SO$_2$. In contrast, when considering only the lower-energy ground vibrational state SO and SO$_2$ emission observed by ATOMIUM, we do not see directed outflows for VX Sgr or AH Sco. Based on observations of other molecular lines, it is likely that both of these stars have complex circumstellar structures. However, when considering only the SO and SO$_2$ lines, we can place both RSGs into the categories we have defined here for AGB stars: VX Sgr has shell-like SO$_2$ and SO emission, while AH Sco has more uniform emission resembling the centralized AGB stars. Since both stars have high mass-loss rates and many high-energy SO$_2$ line detections, making them the two stars with the highest mean energy levels across the SO$_2$ lines, they do not fit the trends observed for AGB stars. In light of this and the previous studies of SO and SO$_2$ for RSGs, it is likely that different factors contribute to RSG SO and SO$_2$ distributions, possibly including different formation mechanisms, compared with the AGB stars. However, a more detailed analysis of the ATOMIUM RSGs is beyond the scope of this paper.

## Isotopic ratios

In order to calculate molecular abundances from our observational data, extensive radiative transfer modeling would be required. However, with a few assumptions we can calculate isotopic ratios from observations of different isotopologues in the same transitions. These ratios provide constrains on the nucleosynthesis within AGB and RSG stars, their stellar mass and age, and the Galactic environment in which they were born. We have limited the calculation of isotopic ratios to pairs of transitions in $\varv=0$ with at least one minor isotope in both molecules, to avoid the problem of potential missing flux or high optical depth in the main isotopologue lines. Hence we assume all the lines used to calculate isotopic ratios are optically thin and have no missing flux; assumptions which are supported by their narrow line shapes and limited angular extents. We have also checked that the chosen lines don’t appear to be masing, as none are excessively bright or narrow. In practise, this limits us to calculations with isotopologues of SiS, as some lines of for example SiO isotopologues fall outside our observed frequency ranges.

We also need to account for the differences in line strength between different isotopologues, so to calculate the isotopic ratio between example isotopologues $^{a}X$ and $^{b}X$ we have used the following formula (cite: danilovich_alma_2020): $$\begin{equation}
\frac{^{a}X}{^{b}X} = \frac{I(^{a}X)}{I(^{b}X)} \left( \frac{\nu_{^{a}X}}{\nu_{^{b}X}} \right) ^{-2},
\end{equation}$$ where $I$ is the integrated intensity and $\nu$ the transition frequency for each isotopologue. For each pair of transitions we measured the integrated intensity in the spectrum where the sum of the intensities of both transitions is maximized. By taking the integrated intensities from spectra extracted at the same angular resolution and aperture size, the beam filling factors should be the same for both transitions. The calculated ratios are given in Table [4](#tab:isorat). In cases where an isotopic ratio can be calculated from multiple pairs of transitions for a single source, Table [4](#tab:isorat) contains the weighted average of these ratios.

| Source      | Isotopologues       |           Ratio |
|:------------|:--------------------|----------------:|
| GY Aql      | $^{29}$Si/$^{30}$Si |   $1.3 \pm 0.3$ |
| IRC+10011   | $^{29}$Si/$^{30}$Si |   $1.7 \pm 0.1$ |
| IRC-10529   | $^{29}$Si/$^{30}$Si |   $1.2 \pm 0.1$ |
| $\pi^1$ Gru | $^{29}$Si/$^{30}$Si |   $0.9 \pm 0.5$ |
| VX Sgr      | $^{29}$Si/$^{30}$Si |       $4 \pm 1$ |
| W Aql       | $^{29}$Si/$^{30}$Si |   $1.5 \pm 0.5$ |
| W Aql       | $^{33}$S/$^{34}$S   |   $0.4 \pm 0.3$ |
| IRC+10011   | $^{34}$S/$^{32}$S   | $0.11 \pm 0.06$ |
| IRC-10529   | $^{34}$S/$^{32}$S   | $0.04 \pm 0.02$ |
| W Aql       | $^{34}$S/$^{32}$S   | $0.06 \pm 0.02$ |

: Isotopic ratios calculated from single and double isotopologues of SiS.

The silicon $^{29}$Si/$^{30}$Si isotopic ratios are found to be generally in the range 1–2 for our oxygen-rich and S-type AGB stars, with the RSG VX Sgr showing a larger ratio of $\sim$4. Previously measured values in oxygen-rich sources are also in the range 1–2: 1.7 in IK Tau (cite: danilovich_alma_2019); 1.58 in R Dor (cite: de_beck_circumstellar_2018); between 0.99 and 1.35 in a sample of ten M-type AGB stars, and around 1.5 in two RSG stars (cite: peng_silicon_2013). The solar value of 1.52 (cite: asplund_chemical_2021) is similarly in the same range as the AGB stars.

The high $^{29}$Si/$^{30}$Si ratio of $4\pm1$ measured in VX Sgr is outside the range of almost all measured Si ratios in evolved stars and in the local galaxy in general. $^{29}$Si/$^{30}$Si ratios measured from presolar SiC grains are all close to the solar ratio of 1.52 (cite: zinner_silicon_2006), as are measurements of various sources at different Galactic radii (cite: monson_uniform_2017). The only literature ratio we were able to find that matches VX Sgr are ratios $\sim$1–10 from infrared observations of the red giant EU Del (cite: pavlenko_analysis_2020). EU Del is a very low-mass and metal-poor star, located below the tip of the red giant branch (cite: mcdonald_eu_2016), so it is not similar to the high mass-loss rate RSG VX Sgr. $^{29}$Si/$^{30}$Si ratios above 2 have also been measured in the AGB stars $\chi$ Cyg (2.4) and V1111 Oph (2.9) by (cite: ukita_sio_1988), as well as a measured value of $3 \pm 1.5$ in IK Tau by (cite: decin_circumstellar_2010), consistent with the value of 1.7 cited above. We note that VX Sgr has been shown to have some puzzling characteristics (cite: tabernero_nature_2021), so this anomalous $^{29}$Si/$^{30}$Si ratio may be another signature of its odd nature.

For most oxygen-rich AGB stars we do not expect the $^{29}$Si/$^{30}$Si ratio to change during the AGB phase (cite: zinner_silicon_2006), so the measured ratios reflect those from the stars’ natal clouds. The primary isotope of silicon, $^{28}$Si, is an $\alpha$-process element, while the two isotopes $^{29}$Si and $^{30}$Si form largely from $^{25}$Mg and $^{26}$Mg during Ne burning, which creates similar amounts of both isotopes (cite: woosley_evolution_1995), as well as during core-collapse Type II supernovae. According to the models of (cite: kobayashi_evolution_2011), $^{29}$Si/$^{30}$Si ratios of $\sim$2–4 can be formed in the core-collapse supernovae of 25–30 M$_\odot$ progenitors, though the supernovae of both lower and higher mass progenitors produce much lower ratios. Some $^{29}$Si and $^{30}$Si also forms from $^{28}$Si in the He-burning shells of AGB stars, but in small and similar amounts (cite: monson_uniform_2017).

The sulfur $^{33}$S/$^{34}$S isotopic ratio is only measured in the S-type star W Aql, where it is found to be $0.4\pm0.3$. This ratio has been measured to be 0.19 $\pm$ 0.03 in IK Tau (cite: danilovich_alma_2019), and 0.17 $\pm$ 0.02 in R Dor (cite: danilovich_alma_2020). The solar value is 0.17 (cite: asplund_chemical_2021), consistent with the two oxygen-rich AGB stars and also with W Aql within the uncertainties.

The sulfur $^{34}$S/$^{32}$S isotopic ratio is found to be $0.06\pm0.02$ in the S-type star W Aql, and $0.04\pm0.02$ and $0.11\pm0.06$ in IRC+10011 and IRC-10529, two high mass-loss rate oxygen-rich sources. A slightly lower ratio of 0.03 is found in IK Tau (cite: danilovich_alma_2019), while a value of 0.04 is found in the oxygen-rich RN Cnc (cite: winters_molecules_2022), and both R Dor and the Sun have similar values of 0.05 (cite: danilovich_alma_2020; asplund_chemical_2021). Hence all our measured $^{34}$S/$^{32}$S ratios are consistent with the solar value, within uncertainties.

Both the main sulfur isotope $^{32}$S and the second most abundant isotope $^{34}$S are primarily produced through explosive nucleosynthesis during Type II supernovae, so these values measured in AGB stars reflect the abundances in the stars’ natal clouds. However, the abundance of the $^{33}$S isotope may increase during the AGB phase via the slow neutron capture process (cite: anders_abundances_1989). This is consistent with its detection in the S-type star W Aql, which is more evolved than the oxygen-rich stars in our sample.

## Unidentified lines

Table A.4 lists the 28 unidentified lines in the ATOMIUM sample, and in which sources they are detected. Four of these lines U221.507, U254.791, U255.023, and U259.329 are coincident with calculated lines of SO$_2$ in its $\varv_3$=1 state. The lines were observed toward stars with SO$_2$ lines in $\varv=0$ and $\varv_2=1$ such that the assignments appear to be reasonable. On the other hand, except for S Pav, toward which two such lines were detected, only one line was detected for the other stars and none of these stars displayed emissions in $\varv_2=2$ or $\varv_1=1$. We would therefore have to invoke very selective excitations, which appears to be too speculative at present even if this cannot be ruled out entirely. Therefore, we refrain from viewing these assignments even as tentative ones.

U253.973, seen in AH Sco, IRC-10529, and VX Sgr, is possibly due to NS, a blend of its $\varv=0~J=11/2-9/2, \Omega=1/2, F=13/2-11/2^f$ transition at 253.968 GHz, and $J=11/2-9/2, \Omega=1/2, F=11/2-9/2^f$ at 253.971 GHz. Facts in favor of this assignment are that these are the brightest NS lines covered by our observations, and the NS molecule has been detected in IK Tau (cite: velilla_prieto_millimeter_2017). Unfortunately, the corresponding $F=13/2-11/2^e$ and $F=11/2-9/2^e$ transitions around 253.570 GHz are not covered by our observations, and the U-line is blended with an SO$_2$ line in AH Sco and VX Sgr, making the assignment to NS very tentative.

Comparing all the U-line frequencies with the rotational lines of the following species MgO, CaO, NaO, FeO, ZrO, MgOH, CaOH, NaOH, ZrS, MgS, and CaS we tentatively conclude that there is no evidence for new metal oxides, hydroxides, and sulfides in the ATOMIUM survey. Furthermore, we would not expect most of these species to exist at observable levels because of the high concentrations of H and H$_2$ in the winds of these stars (cite: decin_alma_2018).

# Conclusions

We have observed 17 oxygen-rich AGB and RSG sources at high angular resolution ($0.02\ensuremath{''} - 0.05\ensuremath{''}$), and complementary lower resolutions (up to 1.4$\ensuremath{''}$), with the ALMA interferometer as part of the ATOMIUM Large Programme, detecting 291 transitions of 24 different molecules and their isotopologues.

We find a range of conclusions, both major and minor:

- We have first detections in oxygen-rich AGB and RSG stars of several vibrationally excited transitions: PO $\varv=1$, SO$_2$ $\varv_1=1$ and $\varv_2=2$, and high energy H$_2$O transitions (cite: baudry_atomium_2023).

- We also have several first detections in S-type AGB stars: vibrationally excited HCN $\varv_2=2,3$ and SiS $\varv=4,5,6$; as well as first detections of the molecules SiC, AlCl, and AlF in W Aql (cite: danilovich_atomium_2021; danilovich_chemical_2023).

- We have calculated correlations between the molecular content of different sources, finding strong correlations (with 3$\sigma$ significance and correlation coefficients above 0.64) between sources with more detected lines of: CS and SiS, CS and AlF, NaCl and KCl, AlO and SO, SO$_2$ and SO, and SO$_2$ and H$_2$O. Some of these correlations are expected from previous results (for example, CS and SiS both trace more dense winds) or chemical reactions (for example, NaCl and KCl both form from reactions of the metal atom with HCl), while the correlations of, for example, CS and AlF, or AlO and SO, have less clear origins.

- Two of our sources are found to be extremely line-poor: the AGB star U Del and the RSG KW Sgr. We speculate this may be indicative of weak shocks in the inner wind.

- The spatial distributions of SO and SO$_2$ are found to be generally consistent with previous results, with a centralized distribution for low mass-loss rate sources and a shell-like distribution for high mass-loss rate sources.

- The isotopic ratios of Si and S are generally in line with previously measured ratios (including solar ratios) except for an anomalously high $^{29}$Si/$^{30}$Si ratio of $4 \pm 1$ in the RSG VX Sgr.

This paper has presented the overall molecular inventory and an initial analysis of the large ATOMIUM dataset, laying the groundwork for future work deriving molecular abundances and abundance profiles using radiative transfer modeling which will provide more rigorous tests for chemical models.

# Acknowledgements

We thank the referee for their helpful comments improving the manuscript, and Kelvin Lee for his contributions to the line identification strategy. SHJW acknowledges support from the Research Foundation Flanders (FWO) through grant 1285221N, and the ERC consolidator grant 646758 AEROSOL. TD acknowledges support from the Research Foundation Flanders (FWO) through grant 12N9920N, and the Australian Research Council through a Discovery Early Career Researcher Award (DE230100183). HSPM acknowledges support by the Deutsche Forschungsgemeinschaft through the collaborative research grant SFB 956 (project ID 184018867). SM and LD acknowledge support from the ERC consolidator grant 646758 AEROSOL, from the KU Leuven C1 excellence grant C16/17/007 MAESTRO, and from the FWO research grant 6099720N. MVdS acknowledges support from the European Union’s Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 882991. AB and FH acknowledge funding from the French National Research Agency (ANR) project PEPPER (ANR-20- CE31- 0002). DG was funded by the project grant ‘The Origin and Fate of Dust in Our Universe’ from the Knut and Alice Wallenberg Foundation. MM acknowledges funding from the Programme Paris Region fellowship supported by the Région Ile-de-France. JMCP was supported by STFC grant number ST/T000287/1. RS’s contribution to the research described in this publication was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA. KTW acknowledges support from the ERC under the European Union’s Horizon 2020 research and innovation programme (Grant agreement no. 883867, project EXWINGS).

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00659.L. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. We also acknowledge excellent support from the UK ALMA Regional Centre (UK ARC), which is hosted by the Jodrell Bank Centre for Astrophysics (JBCA) at the University of Manchester. The UK ARC Node is supported by STFC Grant ST/P000827/1.

This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Skłodowska-Curie Grant agreement No. 945298, and was supported in part by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D) through project number CE170100013.

This work has made use of Python packages Astropy (cite: robitaille_astropy_2013; price-whelan_astropy_2018; price-whelan_astropy_2022), SciPy (cite: virtanen_scipy_2020), pandas (cite: mckinney_data_2010), NumPy (cite: harris_array_2020), and Matplotlib (cite: hunter_matplotlib_2007).

169 natexlab

(ref: adande_sulfur_2013) Adande, G. R., Edwards, J. L., & Ziurys, L. M. 2013, The Astrophysical Journal, 778, 22

(ref: agundez_chemical_2020) Agúndez, M., Martínez, J. I., Andres, P. L. d., Cernicharo, J., & Martín-Gago, J. A. 2020, Astronomy & Astrophysics, 637, A59

(ref: HCN_v0_rot_2002) Ahrens, V., Lewen, F., Takano, S., et al. 2002, Z. Naturforsch. A, 57, 669

(ref: SO2_v0_v2_34_rot_1996) Alekseev, E. A., Dyubko, S. F., Ilyushin, V. V., & Podnos, S. V. 1996, J. Mol. Spectrosc., 176, 316

(ref: anders_abundances_1989) Anders, E. & Grevesse, N. 1989, Geochimica et Cosmochimica Acta, 53, 197

(ref: Andrews2022) Andrews, H., De Beck, E., & Hirvonen, P. 2022, MNRAS, 510, 383

(ref: andriantsaralaza_distance_2022) Andriantsaralaza, M., Ramstedt, S., Vlemmings, W. H. T., & De Beck, E. 2022, Astronomy & Astrophysics

(ref: AlOH_rot_1993) Apponi, A. J., Barclay, W. L., J., & Ziurys, L. M. 1993, ApJL, 414, L129

(ref: arroyo-torres_atmospheric_2013) Arroyo-Torres, B., Wittkowski, M., Marcaide, J. M., & Hauschildt, P. H. 2013, Astronomy & Astrophysics, 554, A76

(ref: asplund_chemical_2021) Asplund, M., Amarsi, A. M., & Grevesse, N. 2021, Astronomy & Astrophysics, 653, A141

(ref: bailer-jones_estimating_2021) Bailer-Jones, C. A. L., Rybizki, J., Fouesneau, M., Demleitner, M., & Andrae, R. 2021, The Astronomical Journal, 161, 147

(ref: PO_vibs_rot_2002) Bailleux, S., Bogey, M., Demuynck, C., Liu, Y., & Walters, A. 2002, J. Mol. Spectrosc., 216, 465

(ref: baudry_atomium_2023) Baudry, A., Wong, K. T., Etoka, S., et al. 2023, Astronomy & Astrophysics, 674, A125, publisher: EDP Sciences

(ref: SO2_isos_rot_1998) Belov, S. P., Tretyakov, M. Y., Kozin, I. N., et al. 1998, J. Mol. Spectrosc., 191, 17

(ref: SiN_rot_2006) Bizzocchi, L., Degli Esposti, C., & Dore, L. 2006, A&A, 455, 1161

(ref: SO_rot_1997) Bogey, M., Civiš, S., Delcroix, B., et al. 1997, J. Mol. Spectrosc., 182, 85

(ref: SiC_isos_rot_1990) Bogey, M., Demuynck, C., & Destombes, J. L. 1990, A&A, 232, L19

(ref: bowers_circumstellar_1983) Bowers, P. F., Johnston, K. J., & Spencer, J. H. 1983, The Astrophysical Journal, 274, 733

(ref: TiO2_rot_2008) Brünken, S., Müller, H. S. P., Menten, K. M., McCarthy, M. C., & Thaddeus, P. 2008, ApJ, 676, 1367

(ref: SiO_isos_IR_1995) Campbell, J. M., Klapstein, D., Dulick, M., Bernath, P. F., & Wallace, L. 1995, ApJS, 101, 237

(ref: KCl_rot_2004) Caris, M., Lewen, F., Müller, H. S. P., & Winnewisser, G. 2004, J. Mol. Struct., 695-696, 243

(ref: NaCl_rot_2002) Caris, M., Lewen, F., & Winnewisser, G. 2002, Z. Naturforsch. A, 57, 663

(ref: HC-13-N_v0_rot_2005) Cazzoli, G. & Puzzarini, C. 2005, J. Mol. Spectrosc., 233, 280

(ref: SiC_rot_det_1989) Cernicharo, J., Gottlieb, C. A., Guelin, M., Thaddeus, P., & Vrtilek, J. M. 1989, ApJL, 341, L25

(ref: cernicharo_2_2000) Cernicharo, J., Guélin, M., & Kahane, C. 2000, Astronomy and Astrophysics Supplement Series, 142, 181

(ref: chapman_oh_1994) Chapman, J. M., Sivagnanam, P., Cohen, R. J., & Le Squeren, A. M. 1994, Monthly Notices of the Royal Astronomical Society, 268, 475

(ref: chen_structure_2008) Chen, X. & Shen, Z. Q. 2008, IAU Symposium, 252, 247

(ref: chen_measuring_2007) Chen, X., Shen, Z.-Q., & Xu, Y. 2007, Chinese Journal of Astronomy and Astrophysics, 7, 531

(ref: H2O_2nd-Triad_2014) Coudert, L. H., Martin-Drumel, M.-A., & Pirali, O. 2014, J. Mol. Spectrosc., 303, 36

(ref: danilovich_detailed_2014) Danilovich, T., Bergman, P., Justtanont, K., et al. 2014, Astronomy & Astrophysics, 569, A76

(ref: danilovich_sulphur_2016) Danilovich, T., De Beck, E., Black, J. H., Olofsson, H., & Justtanont, K. 2016, Astronomy & Astrophysics, 588, A119

(ref: danilovich_rotational_2020) Danilovich, T., Gottlieb, C. A., Decin, L., et al. 2020a, The Astrophysical Journal, 904, 110

(ref: danilovich_chemical_2023) Danilovich, T., Malfait, J., Van de Sande, M., & Montargès, M. 2023, Accepted for publication in Nature Astronomy

(ref: danilovich_sulphur-bearing_2018) Danilovich, T., Ramstedt, S., Gobrecht, D., et al. 2018, Astronomy and Astrophysics, 617, A132

(ref: danilovich_alma_2020) Danilovich, T., Richards, A. M. S., Decin, L., Van de Sande, M., & Gottlieb, C. A. 2020b, Monthly Notices of the Royal Astronomical Society, 494, 1323

(ref: danilovich_alma_2019) Danilovich, T., Richards, A. M. S., Karakas, A. I., et al. 2019, Monthly Notices of the Royal Astronomical Society, 484, 494

(ref: danilovich_sulphur-bearing_2017) Danilovich, T., Van de Sande, M., De Beck, E., et al. 2017, Astronomy and Astrophysics, 606, A124

(ref: danilovich_atomium_2021) Danilovich, T., Van de Sande, M., Plane, J. M. C., et al. 2021, Astronomy & Astrophysics, 655, A80

(ref: de_beck_probing_2010) De Beck, E., Decin, L., de Koter, A., et al. 2010, Astronomy & Astrophysics, 523, A18

(ref: de_beck_circumstellar_2018) De Beck, E. & Olofsson, H. 2018, Astronomy & Astrophysics, 615, A8

(ref: de_beck_surprisingly_2020) De Beck, E. & Olofsson, H. 2020, Astronomy & Astrophysics, 642, A20

(ref: decin_evolution_2021) Decin, L. 2021, Annual Review of Astronomy and Astrophysics, 59, 337, \_eprint: https://doi.org/10.1146/annurev-astro-090120-033712

(ref: decin_circumstellar_2010) Decin, L., De Beck, E., Brünken, S., et al. 2010, Astronomy and Astrophysics, 516, A69

(ref: decin_variable_2007) Decin, L., Hony, S., de Koter, A., et al. 2007, Astronomy and Astrophysics, 475, 233

(ref: decin_substellar_2020) Decin, L., Montargès, M., Richards, A. M. S., et al. 2020, Science, 369, 1497

(ref: decin_alma_2018) Decin, L., Richards, A. M. S., Danilovich, T., Homan, W., & Nuth, J. A. 2018, Astronomy and Astrophysics, 615, A28

(ref: decin_study_2017) Decin, L., Richards, A. M. S., Waters, L. B. F. M., et al. 2017, Astronomy & Astrophysics, 608, A55

(ref: demore_chemical_1997) DeMore, W., Sander, S., Golden, D., et al. 1997, JPL Publication 97-4, 1

(ref: doan_extended_2017) Doan, L., Ramstedt, S., Vlemmings, W. H. T., et al. 2017, Astronomy & Astrophysics, 605, A28

(ref: douglas_experimental_2022) Douglas, K. M., Gobrecht, D., & Plane, J. M. C. 2022, Monthly Notices of the Royal Astronomical Society, stac1684

(ref: OH_analysis_2013) Drouin, B. J. 2013, J. Phys. Chem. A, 117, 10076

(ref: el_mellah_wind_2020) El Mellah, I., Bolte, J., Decin, L., Homan, W., & Keppens, R. 2020, Astronomy & Astrophysics, 637, A91

(ref: CDMS_2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, J. Mol. Spectrosc., 327, 95

(ref: SO2_IR_5states_1993) Flaud, J. M., Perrin, A., Salah, L. M., Lafferty, W. J., & Guelachvili, G. 1993, J. Mol. Spectrosc., 160, 272

(ref: SiS_isos_IR_1990) Frum, C. I., Engleman, R., J., & Bernath, P. F. 1990, , 93, 5457

(ref: HCN-isos_rot_2004) Fuchs, U., Bruenken, S., Fuchs, G. W., et al. 2004, Z. Naturforsch. A, 59, 861

(ref: H2O_W2020) Furtenbacher, T., Tóbiás, R., Tennyson, J., Polyansky, O. L., & Császár, A. G. 2020, J. Phys. Chem. Ref. Data, 49, 033101

(ref: gaia_collaboration_gaia_2018) Gaia Collaboration, T., Brown, A. G. A., Vallenari, A., et al. 2018, Astronomy & Astrophysics, 616, A1

(ref: gobrecht_dust_2016) Gobrecht, D., Cherchneff, I., Sarangi, A., Plane, J. M. C., & Bromley, S. T. 2016, Astronomy & Astrophysics, 585, A6

(ref: gobrecht_bottom-up_2022) Gobrecht, D., Plane, J. M. C., Bromley, S. T., et al. 2022, Astronomy & Astrophysics, 658, A167

(ref: HITRAN2020_2022) Gordon, I. E., Rothman, L. S., Hargreaves, R. J., et al. 2022, JQSRT, 277, 107949

(ref: AlO_vibs_rot_1994) Goto, M., Takano, S., Yamamoto, S., Ito, H., & Saito, S. 1994, Chem. Phys. Lett., 227, 287

(ref: gottlieb_atomium_2022) Gottlieb, C. A., Decin, L., Richards, A. M. S., et al. 2022, Astronomy & Astrophysics, 660, A94

(ref: SiC2_rot_1989) Gottlieb, C. A., Vrtilek, J. M., & Thaddeus, P. 1989, ApJL, 343, L29

(ref: groenewegen_millimeter_1999) Groenewegen, M. a. T., Baas, F., Blommaert, J. a. D. L., et al. 1999, Astronomy and Astrophysics Supplement Series, 140, 197

(ref: habing_asymptotic_2003) Habing, H. & Olofsson, H., eds. 2003, Asymptotic Giant Branch Stars (A&A Library (Springer))

(ref: harris_array_2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: he_spectral_2008) He, J. H., Kwok, S., Müller, H. S. P., et al. 2008, The Astrophysical Journal Supplement Series, 177, 275

(ref: AlF_IR_1992) Hedderich, H. G. & Bernath, P. F. 1992, J. Mol. Spectrosc., 153, 73

(ref: AlCl_IR_1993) Hedderich, H. G., Dulick, M., & Bernath, P. F. 1993, , 99, 8363

(ref: helmer_experimental_1993) Helmer, M. & Plane, J. M. C. 1993, The Journal of Chemical Physics, 99, 7696

(ref: SO2_v0_v2_34_rot_1985) Helminger, P. A. & De Lucia, F. C. 1985, J. Mol. Spectrosc., 111, 66

(ref: div-MX_rot_1993) Hensel, K. D., Styger, C., Jäger, W., Merer, A. J., & Gerry, M. C. L. 1993, , 99, 3320

(ref: herwig_evolution_2005) Herwig, F. 2005, Annual Review of Astronomy and Astrophysics, 43, 435

(ref: AlF_rot_1970Zb) Hoeft, J., Lovas, F. J., Tiemann, E., & Törring, T. 1970, Z. Naturforsch. A, 25, 1029

(ref: hofner_mass_2018) Höfner, S. & Olofsson, H. 2018, Astronomy and Astrophysics Review, 26, 1

(ref: homan_atomium_2020) Homan, W., Montargès, M., Pimpanuwat, B., et al. 2020, Astronomy & Astrophysics, 644, A61

(ref: homan_atomium_2021) Homan, W., Pimpanuwat, B., Herpin, F., et al. 2021, Astronomy & Astrophysics, 651, A82

(ref: huggins_neutral_1994) Huggins, P. J., Bachiller, R., Cox, P., & Forveille, T. 1994, The Astrophysical Journal, 424, L127

(ref: hunter_matplotlib_2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: jeste_vibrationally_2022) Jeste, M., Gong, Y., Wong, K. T., et al. 2022, Astronomy & Astrophysics, 666, A69, publisher: EDP Sciences

(ref: jura_mass-losing_1990) Jura, M. & Kleinmann, S. G. 1990, The Astrophysical Journal Supplement Series, 73, 769

(ref: kaminski_interferometric_2013) Kamiński, T., Gottlieb, C. A., Young, K. H., Menten, K. M., & Patel, N. A. 2013, The Astrophysical Journal Supplement Series, 209, 38

(ref: TiO_isos_rot_2008) Kania, P., Giesen, T. F., Müller, H. S. P., Schlemmer, S., & Brünken, S. 2008, in 2008 33rd International Conference on Infrared, Millimeter and Terahertz Waves, 1–2

(ref: TiO2_rot_2011) Kania, P., Hermanns, M., Brünken, S., Müller, H. S. P., & Giesen, T. F. 2011, J. Mol. Spectrosc., 268, 173

(ref: PO_rot_1983) Kawaguchi, K., Saito, S., & Hirota, E. 1983, , 79, 629

(ref: kemper_mass_2003) Kemper, F., Stark, R., Justtanont, K., et al. 2003, Astronomy & Astrophysics, 407, 609

(ref: kendall_new_1938) Kendall, M. G. 1938, Biometrika, 30, 81

(ref: kendall_treatment_1945) Kendall, M. G. 1945, Biometrika, 33, 239

(ref: OH_highly-ex_2019) Khouri, T., Velilla-Prieto, L., De Beck, E., et al. 2019, A&A, 623, L1

(ref: kiss_variability_2006) Kiss, L. L., Szabó, G. M., & Bedding, T. R. 2006, Monthly Notices of the Royal Astronomical Society, 372, 1721

(ref: SO_isos_rot_1996) Klaus, T., Saleck, A. H., Belov, S. P., et al. 1996, J. Mol. Spectrosc., 180, 197

(ref: knapp_mass_1985) Knapp, G. R. & Morris, M. 1985, The Astrophysical Journal, 292, 640

(ref: kobayashi_evolution_2011) Kobayashi, C., Karakas, A. I., & Umeda, H. 2011, \\mnras, 414, 3231

(ref: lamers_introduction_1999) Lamers, H. J. G. L. M. & Cassinelli, J. P. 1999, Introduction to stellar winds

(ref: TiO-isos_rot_2016) Lincowski, A. P., Halfen, D. T., & Ziurys, L. M. 2016, ApJ, 833, 9

(ref: loup_co_1993) Loup, C., Forveille, T., Omont, A., & Paul, J. F. 1993, Astronomy and Astrophysics, Suppl. Ser., Vol. 99, p. 291-377 (1993), 99, 291

(ref: maercker_hifi_2016) Maercker, M., Danilovich, T., Olofsson, H., et al. 2016, Astronomy & Astrophysics, 591, A44

(ref: maes_sensitivity_2023) Maes, S., Van de Sande, M., Danilovich, T., De Ceuster, F., & Decin, L. 2023, Monthly Notices of the Royal Astronomical Society, 522, 4654

(ref: HCN_isos_IR_2000) Maki, A. G., Mellau, G. C., Klee, S., Winnewisser, M., & Quapp, W. 2000, J. Mol. Spectrosc., 202, 67

(ref: mamon_photodissociation_1988) Mamon, G. A., Glassgold, A. E., & Huggins, P. J. 1988, The Astrophysical Journal, 328, 797

(ref: mangan_kinetic_2021) Mangan, T. P., Douglas, K. M., Lade, R. E., et al. 2021, ACS Earth and Space Chemistry, 5, 3385

(ref: marigo_evolution_2008) Marigo, P., Girardi, L., Bressan, A., et al. 2008, Astronomy & Astrophysics, 482, 883

(ref: massalkhi_abundance_2018) Massalkhi, S., Agúndez, M., Cernicharo, J., et al. 2018, Astronomy & Astrophysics, 611, A29

(ref: mauron_mass-loss_2011) Mauron, N. & Josselin, E. 2011, Astronomy & Astrophysics, 526, A156

(ref: mcdonald_eu_2016) McDonald, I., Zijlstra, A. A., Sloan, G. C., et al. 2016, Monthly Notices of the Royal Astronomical Society, 456, 4542

(ref: mckinney_data_2010) McKinney, W. 2010, Proceedings of the 9th Python in Science Conference, 56

(ref: mcmullin_casa_2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, 376, 127

(ref: SiO_rot_1991) Mollaaghababa, R., Gottlieb, C. A., Vrtilek, J. M., & Thaddeus, P. 1991, ApJL, 368, L19

(ref: monson_uniform_2017) Monson, N. N., Morris, M. R., & Young, E. D. 2017, The Astrophysical Journal, 839, 123

(ref: montarges_vltsphere_2023) Montargès, M., Cannon, E., Koter, A. d., et al. 2023, Astronomy & Astrophysics, 671, A96, publisher: EDP Sciences

(ref: morris_molecular_1980) Morris, M. 1980, The Astrophysical Journal, 236, 823

(ref: SO2_v0_v2_rot_2005) Müller, H. S. P. & Brünken, S. 2005, J. Mol. Spectrosc., 232, 213

(ref: SiC2_HIFI_analysis_2012) Müller, H. S. P., Cernicharo, J., Agúndez, M., et al. 2012, J. Mol. Spectrosc., 271, 50

(ref: CDMS_2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, J. Mol. Struct., 742, 215

(ref: SiO_isos_rot_2013) Müller, H. S. P., Spezzano, S., Bizzocchi, L., et al. 2013, J. Phys. Chem. A, 117, 13843

(ref: muller_cologne_2001) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, \\aap, 370, L49

(ref: TiO-rot_1998) Namiki, K.-i., Saito, S., Robinson, J. S., & Steimle, T. C. 1998, J. Mol. Spectrosc., 191, 176

(ref: netzer_mass_1987) Netzer, N. & Knapp, G. R. 1987, The Astrophysical Journal, 323, 734

(ref: olofsson_mass_2002) Olofsson, H., Delgado, D. G., Kerschbaum, F., & Schöier, F. L. 2002, Astronomy & Astrophysics, 391, 1053

(ref: olofsson_study_1993) Olofsson, H., Eriksson, K., Gustafsson, B., & Carlstrom, U. 1993, The Astrophysical Journal Supplement Series, 87, 267

(ref: pardo_ultra-deep_2022) Pardo, J. R., Cernicharo, J., Tercero, B., et al. 2022, Astronomy & Astrophysics, 658, A39

(ref: patel_submillimeter_2009) Patel, N. A., Young, K. H., Brünken, S., et al. 2009, The Astrophysical Journal, 692, 1205

(ref: patel_interferometric_2011) Patel, N. A., Young, K. H., Gottlieb, C. A., et al. 2011, The Astrophysical Journal Supplement Series, 193, 17

(ref: pavlenko_analysis_2020) Pavlenko, Y. V., Yurchenko, S. N., & Tennyson, J. 2020, Astronomy & Astrophysics, 633, A52

(ref: intro_JPL-catalog) Pearson, J. C., Müller, H. S. P., Pickett, H. M., Cohen, E. A., & Drouin, B. J. 2010, J. Quant. Spectrosc. Radiat. Transfer, 111, 1614

(ref: peng_silicon_2013) Peng, T.-C., Humphreys, E. M. L., Testi, L., et al. 2013, Astronomy & Astrophysics, 559, L8

(ref: perryman_hipparcos_1997) Perryman, M. a. C., Lindegren, L., Kovalevsky, J., et al. 1997, Astronomy and Astrophysics, Vol. 500, p. 501-504 (2009), 500, 501

(ref: spfit_1991) Pickett, H. M. 1991, J. Mol. Spectrosc., 148, 371

(ref: pickett_submillimeter_1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, Journal of Quantitative Spectroscopy and Radiative Transfer, 60, 883

(ref: SO2_AlPIne_1996) Pine, A. S., Suenram, R. D., Brown, E. R., & McIntosh, K. A. 1996, J. Mol. Spectrosc., 175, 37

(ref: plane_experimental_1989) Plane, J. M. C., Rajasekhar, B., & Bartolotti, L. 1989, The Journal of Chemical Physics, 91, 6177

(ref: price-whelan_astropy_2022) Price-Whelan, A. M., Lim, P. L., Earl, N., et al. 2022, The Astrophysical Journal, 935, 167

(ref: price-whelan_astropy_2018) Price-Whelan, A. M., Sipőcz, B. M., Günther, H. M., et al. 2018, The Astronomical Journal, 156, 123

(ref: quintana-lacaci_history_2023) Quintana-Lacaci, G., Velilla-Prieto, L., Agúndez, M., et al. 2023, Astronomy & Astrophysics, 669, A56, publisher: EDP Sciences

(ref: ramstedt_circumstellar_2017) Ramstedt, S., Mohamed, S., Vlemmings, W. H. T., et al. 2017, Astronomy & Astrophysics, 605, A126

(ref: robitaille_astropy_2013) Robitaille, T. P., Tollerud, E. J., Greenfield, P., et al. 2013, Astronomy & Astrophysics, 558, A33

(ref: SiN_rot_1983) Saito, S., Endo, Y., & Hirota, E. 1983, , 78, 6447

(ref: samus_general_2017) Samus’, N. N., Kazarovets, E. V., Durlevich, O. V., Kireeva, N. N., & Pastukhova, E. N. 2017, Astronomy Reports, 61, 80

(ref: santander-garcia_shapemol_2015) Santander-García, M., Bujarrabal, V., Koning, N., & Steffen, W. 2015, Astronomy & Astrophysics, 573, A56

(ref: SiO_SiS_SO_FTMW_2003) Sanz, M. E., McCarthy, M. C., & Thaddeus, P. 2003, J. Chem. Phys., 119, 11715

(ref: SO2_nu1_1981) Sattler, J. P., Worchesky, T. L., & Lafferty, W. J. 1981, J. Mol. Spectrosc., 88, 364

(ref: schoier_abundance_2007) Schöier, F. L., Bast, J., Olofsson, H., & Lindqvist, M. 2007, Astronomy & Astrophysics, 473, 871

(ref: schoier_models_2001) Schöier, F. L. & Olofsson, H. 2001, Astron. Astrophys., 368, 969

(ref: SO2_vibs_rot_1968) Steenbeckeliers, G. 1968, Ann Soc Sci Bruxelles, Ser III, 82, 331

(ref: szymczak_polarization_1997) Szymczak, M. & Cohen, R. J. 1997, Monthly Notices of the Royal Astronomical Society, 288, 945

(ref: tabernero_nature_2021) Tabernero, H. M., Dorda, R., Negueruela, I., & Marfil, E. 2021, Astronomy & Astrophysics, 646, A98

(ref: tenenbaum_arizona_2010) Tenenbaum, E. D., Dodd, J. L., Milam, S. N., Woolf, N. J., & Ziurys, L. M. 2010, The Astrophysical Journal Supplement Series, 190, 348

(ref: HCN_v2_2003) Thorwirth, S., Müller, H. S. P., Lewen, F., et al. 2003, ApJL, 585, L163

(ref: HC3N_rot_2000) Thorwirth, S., Müller, H. S. P., & Winnewisser, G. 2000, J. Mol. Spectrosc., 204, 133

(ref: tielens_physics_2005) Tielens, A. G. G. M. 2005, The Physics and Chemistry of the Interstellar Medium

(ref: AlO_rot_1989) Törring, T. & Herrmann, R. 1989, Mol. Phys., 68, 1379

(ref: ukita_sio_1988) Ukita, N. & Kaifu, N. 1988, in Atmospheric Diagnostics of Stellar Evolution: Chemical Peculiarity, Mass Loss, and Explosion, ed. K. Nomoto, Lecture Notes in Physics (Berlin, Heidelberg: Springer), 51–52

(ref: van_de_sande_determining_2018) Van de Sande, M., Sundqvist, J. O., Millar, T. J., et al. 2018, Astronomy & Astrophysics, 616, A106

(ref: velilla_prieto_millimeter_2017) Velilla Prieto, L., Sánchez Contreras, C., Cernicharo, J., et al. 2017, Astronomy & Astrophysics, 597, A25

(ref: virtanen_scipy_2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: vlemmings_improved_2007) Vlemmings, W. H. T. & Langevelde, H. J. v. 2007, Astronomy & Astrophysics, 472, 547

(ref: winters_molecules_2022) Winters, J. M., Hoai, D. T., Wong, K. T., et al. 2022, Astronomy & Astrophysics, 658, A135

(ref: TiO_isos_IR_2021) Witsch, D., Breier, A. A., Döring, E., et al. 2021, J. Mol. Spectrosc., 377, 111439

(ref: wittkowski_vltiamber_2017) Wittkowski, M., Arroyo-Torres, B., Marcaide, J. M., et al. 2017, Astronomy & Astrophysics, 597, A9

(ref: woosley_evolution_1995) Woosley, S. E. & Weaver, T. A. 1995, The Astrophysical Journal Supplement Series, 101, 181

(ref: AlCl_rot_1972) Wyse, F. C. & Gordy, W. 1972, , 56, 2130

(ref: AlF_rot_1970a) Wyse, F. C., Gordy, W., & Pearson, E. F. 1970, , 52, 3887

(ref: AlO_rot_1990) Yamada, C., Fujitake, M., Hirota, E., & Cohen, E. A. 1990, , 92, 2146

(ref: HC3N_rot_1995) Yamada, K. M. T., Moravec, A., & Winnewisser, G. 1995, Z. Naturforsch. A, 50, 1179

(ref: young_co3–2_1995) Young, K. 1995, The Astrophysical Journal, 445, 872

(ref: H2O_5states_rot_2012) Yu, S., Pearson, J. C., Drouin, B. J., et al. 2012, J. Mol. Spectrosc., 279, 16

(ref: HCN_high-v_rot_2003) Zelinger, Z., Amano, T., Ahrens, V., et al. 2003, J. Mol. Spectrosc., 220, 223

(ref: zinner_silicon_2006) Zinner, E., Nittler, L. R., Gallino, R., et al. 2006, The Astrophysical Journal, 650, 350

# Molecular data, line identifications and measured parameters

## Laboratory spectroscopic background on line identifications

Spectroscopic data were retrieved from the Cologne Database for Molecular Spectroscopy, CDMS,[^4] (cite: muller_cologne_2001; CDMS_2005; CDMS_2016) unless stated otherwise. Several of the accessed entries were created, updated, or extended in vibrational quanta $\varv$ to support the ATOMIUM project. While all of the relevant laboratory or observational data were considered for these entries, other data are not always up-to-date. We mention only cases in which our observations may be affected. We usually list the most important references for species with more than one line in ATOMIUM, possibly supplemented by references for data that encompass the ATOMIUM frequency range or are close to it. We list in Table A.3 references of lines identified in ATOMIUM; we may refrain from listing additional background information for species with only one or two lines in ATOMIUM.

We point out that Hund’s case (b) quantum numbers are given in the CDMS catalog throughout because of the `spfit` and `spcat` programs (cite: spfit_1991) employed for most of the CDMS entries. Hund’s case (a) quantum numbers may be more appropriate for some of the radical species, and these are listed in most cases in Table A.3. The CDMS documentation file usually contains information on how to convert Hund’s case (b) quantum numbers to Hund’s case (a). The quantum numbers $N$, $J$, and $F$ indicate the total rotational angular momentum, the total rotational angular momentum including the electronic spin, and the total rotational angular momentum including the electronic and nuclear spin, respectively. For non-radicals, $J = N$, and $J$ is usually given instead of $N$. The quantum numbers $K_a$ and $K_c$ designate projection of the total rotational angular momentum onto the $a$- and $c$-axis, respectively, in the case of asymmetric top molecules such as SO$_2$, H$_2$O, TiO$_2$, and SiC$_2$. Rotational levels are usually designated as $J_{K_a,K_c}$. Vibrational quanta are usually designated with $\varv$; a subscript indicated the number of the vibrational mode. The triply excited bending mode of a triatomic molecule is indicated as $\varv_2 = 3$. Multiple excitations of triatomics, for example, $\varv_2 = 3$, $\varv_3 = 1$, are often given as triple $(\varv_1\varv_2\varv_3)$, where $\varv_i$ indicates the excitation in the vibrational mode $i$; in the above case (031). The Greek letter $\nu$ is used to designate vibrational bands; $\nu_1$ could also be witten as $(100)-(000)$ and $\nu_1 - \nu_3$ as $(100)-(001)$.

The references for CO, CS, H$_2$S, and $^{13}$CN are given in Table A.3 only.

The HCN rest frequencies are from a combined fit to laboratory data for $\varv_2 \le 3$, $\varv_3 = 1$, and $\varv_1 = 1$. The rotational data for $\varv_2 = 0$ and 1 are largely from (cite: HCN_v0_rot_2002) and (cite: HCN_v2_2003), respectively; data for higher excited rotational data are largely from (cite: HCN_high-v_rot_2003). The H$^{13}$CN rest frequencies are from an equvalent fit. The $\varv_2 = 0$ and 1 data are from (cite: HCN-isos_rot_2004); additional extensive $\varv = 0$ data were taken from (cite: HC-13-N_v0_rot_2005). Important for both fits were IR data from (cite: HCN_isos_IR_2000).

The SiO rest frequencies were derived from (cite: SiO_isos_rot_2013) who performed Fourier transform microwave (FTMW) spectroscopy on several isotopic species up to very high vibrational states along with millimeter and submillimeter measurements of several isotopic species in their ground vibrational states. Additional FTMW data of SiO, $^{29}$SiO (and Si$^{18}$O) were taken from (cite: SiO_SiS_SO_FTMW_2003). Excited vibrational data of the main isotopologue were published by (cite: SiO_rot_1991). Noteworthy are furthermore IR data from (cite: SiO_isos_IR_1995).

The current rest frequencies of SO rely mostly on (cite: SO_rot_1997) and (cite: SO_isos_rot_1996), those of the isotopic species mostly on the latter work. Additional older data were also used at lower frequencies; some references are given in Table A.3. We point out that Hund’s case (a) quantum numbers may be found in the older literature, usually designated as $J_N$, whereas Hund’s case (b) quantum numbers are more common in the more recent literature, designated as $N_J$.

The SO$_2$ $\varv_2 = 0$ and 1 data were derived from (cite: SO2_v0_v2_rot_2005) with important additional rest frequencies for $\varv = 0$ from (cite: SO2_isos_rot_1998) and for both vibrational states from (cite: SO2_v0_v2_34_rot_1996) and (cite: SO2_v0_v2_34_rot_1985). The $\varv_2 = 2$ and $\varv_1 = 1$ data are based on an unpublished fit by one of us (HSPM) and employ besides own new data published rotational transition frequencies from (cite: SO2_vibs_rot_1968), unpublished data communicated by the late Walter Lafferty, presumably associated with (cite: SO2_AlPIne_1996), and IR data from (cite: SO2_nu1_1981) and (cite: SO2_IR_5states_1993). The $^{34}$SO$_2$ $\varv = 0$ data are largely based on (cite: SO2_isos_rot_1998) with important additional rest frequencies from (cite: SO2_v0_v2_34_rot_1996) and (cite: SO2_v0_v2_34_rot_1985).

The SiS rest frequencies were derived from (cite: SiO_isos_rot_2013) who performed Fourier transform microwave (FTMW) spectroscopy on several isotopic species up to very high vibrational states along with millimeter and submillimeter measurements of several isotopic species mostly in their ground vibrational states. Additional FTMW data of SiS, $^{29}$SiS and Si$^{34}$S) were taken from (cite: SiO_SiS_SO_FTMW_2003). Important were also IR data, in particular from (cite: SiS_isos_IR_1990).

The H$_2$O data pertaining to the lowest five vibrational states were based on the JPL catalog (cite: pickett_submillimeter_1998; intro_JPL-catalog) entry which, in turn, is based on (cite: H2O_5states_rot_2012). Besides extensive new data, this work employs additional rotational and rovibrational data from a plethora of sources.

(cite: H2O_2nd-Triad_2014) presented a similar study including the next three vibrational states, but, unfortunately, calculated transition frequencies for these start only at 300 GHz. Therefore, we inspected the HITRAN2020 (cite: HITRAN2020_2022) and W2020 (cite: H2O_W2020) compilations for highly vibrationally excited H$_2$O transitions. As these were deemed to be quite uncertain, we resorted to the transition frequencies determined in our study on H$_2$O and OH (cite: baudry_atomium_2023).

The initial OH data were taken from the JPL catalog and bear on (cite: OH_analysis_2013). This analysis is based on a plethora of laboratory spectroscopic investigations. The $\Lambda$-doubling transitions with high rotational quanta, however, are rather uncertain and display systematic deviations, see for example (cite: OH_highly-ex_2019) and (cite: baudry_atomium_2023). In our study on H$_2$O and OH (cite: baudry_atomium_2023), we combined the data gathered in (cite: OH_analysis_2013) with $\Lambda$-doubling transition frequencies from our own astronomical observations and those from (cite: OH_highly-ex_2019) to improve the calculations of the OH $\Lambda$-doubling transition frequencies in the upper millimeter and submillimeter regions (cite: baudry_atomium_2023).

Calculations of the PO rest frequencies rely mainly on (cite: PO_vibs_rot_2002) with additional $\varv = 0$ data from (cite: PO_rot_1983).

The TiO rest frequencies are based on an unpublished isotopic invariant fit by one of us (HSPM). The main source of experimental data are those from the minor Ti isotopologues from (cite: TiO-isos_rot_2016). Additional important data relevant for our study are the ground state rotational data of $^{46,48,50}$TiO from (cite: TiO_isos_rot_2008), those of $^{48}$TiO from (cite: TiO-rot_1998), and the extensive IR data for all Ti isotopologues from (cite: TiO_isos_IR_2021).

Calculations on the rotational spectrum of TiO$_2$ are based on (cite: TiO2_rot_2011). Besides our own upper millimeter and lower submillimeter data of $^{46,48,50}$TiO$_2$, the analysis also employs microwave data of the same isotopologues from (cite: TiO2_rot_2008). The rotational temperatures were of order of 30 K and 3 K, respectively, which limited the quantum number range accessed. Transition frequencies involving higher rotational excitation may be quite uncertain as a consequence. The $K_a$ = 6$-$5 $Q$-branch transitions with $J$ = 25, 27, and 29 display larger uncertainties, such that their true transition freaquencies may differ from the calculated ones by more than 1 MHz.

The ground state rotational data of AlO were taken from (cite: AlO_rot_1990) and from (cite: AlO_rot_1989); transition frequencies of $\varv = 1$ and 2 were published by (cite: AlO_vibs_rot_1994).

The AlOH data were taken from the JPL catalog; they are derived from (cite: AlOH_rot_1993).

The AlF rest frequencies are mainly based on the rotational data of (cite: AlF_rot_1970a). Additional rotational data are from (cite: AlF_rot_1970Zb), and rovibrational data are mainly from (cite: AlF_IR_1992).

Calculations of the rotational spectrum of AlCl and Al$^{37}$Cl depends mainly on rotational data of (cite: AlCl_rot_1972). Very accurate frequencies of the $J = 1 - 0$ transitions by (cite: div-MX_rot_1993) were also employed as were rovibrational transitions taken from (cite: AlCl_IR_1993).

The NaCl and KCl rest frequencies rely mainly on measurements by (cite: NaCl_rot_2002) and (cite: KCl_rot_2004), respectively.

The SiN rest frequencies are based on (cite: SiN_rot_2006), with the important lower frequency data taken from (cite: SiN_rot_1983).

The SiC transition frequencies are based on (cite: SiC_isos_rot_1990) and on (cite: SiC_rot_det_1989).

The current calculation of SiC$_2$ $\varv=0$ transition frequencies were derived from (cite: SiC2_HIFI_analysis_2012). Important additional data besides HIFI-Herschel data from that work come from laboratory measurements by (cite: SiC2_rot_1989) and from astronomical observations by (cite: cernicharo_2_2000).

The ground state rotational data of HC$_3$N depend on (cite: HC3N_rot_2000) with additional contributions mainly from (cite: HC3N_rot_1995).

# SO$_2$ and SO channel maps

![](S_Pav_mid_SO2_224_channels.pdf)

![](RW_Sco_mid_SO2_224_channels.pdf)

![](T_Mic_mid_SO2_224_channels.pdf)

![](R_Hya_mid_SO2_224_channels.pdf)

![](SV_Aqr_compact_SO2_244_channels.pdf)

![](U_Her_mid_SO2_224_channels.pdf)

![](R_Aql_mid_SO2_244_channels.pdf)

![](GY_Aql_mid_SO2_244_channels.pdf)

![](IRC-10529_compact_SO2_244_channels.pdf)

![](IRC+10011_compact_SO2_244_channels.pdf)

![](AH_Sco_mid_SO2_224_channels.pdf)

![](VX_Sgr_mid_SO2_224_channels.pdf)

![](R_Aql_mid_SO_215_channels.pdf)

# Spectra

\

\

\

\

\

\

\

\

[^1]: email: sofia.wallstrom@kuleuven.be

[^2]: Tables A.1–A.5 are only available in electronic form at the CDS via anonymous ftp to cdsarc.cds.unistra.fr (130.79.128.5) or via https://cdsarc.cds.unistra.fr/cgi-bin/qcat?J/A+A/

[^3]: A p-value measures the probability of obtaining the observed results "by chance", assuming that the null hypothesis of no correlation is true. Therefore, a smaller p-value indicates a greater statistical significance.

[^4]: https://cdms.astro.uni-koeln.de/

</paper>

Write the methods card for this paper.