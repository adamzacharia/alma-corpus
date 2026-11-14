# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A.222K\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694A.222K",
 "title": "ALMA observations of CO isotopologues towards six obscured post-asymptotic giant branch stars",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Khouri, T.",
 "n_authors": 16,
 "arxiv_id": "2501.04492",
 "doi": "10.1051/0004-6361/202452500",
 "alma_projects_linked_by_archive": [
  "2021.1.01259.S"
 ]
}
```

Paper text:
<paper>
# ALMA observations of CO isotopologues towards six obscured post-AGB stars

Low- and intermediate-mass stars evolve through the asymptotic giant branch (AGB), when an efficient mass-loss process removes a significant fraction of their initial mass. For most sources, this mass-loss process relies on the interplay between convection, stellar pulsations, and dust formation. However, predicting the mass-loss history of a given star from first principles is complex and still not possible. At the end of the AGB at least some stars experience a substantial increase in their mass-loss rate for unknown reasons, creating post-AGB objects that are completely enshrouded in thick dusty envelopes. Recent studies have suggested that some of these sources may be the product of interactions between an evolved star with a close companion.

We observed six obscured post-AGB stars (four C-rich and two O-rich sources) to constrain the properties of their circumstellar envelopes, recent mass-loss histories, and initial mass of the central stars.

We use observations of the $J$=2$-$1  line of $^{13}$CO, C$^{17}$O, and C$^{18}$O with the Atacama Large Millimeter / submillimeter Array (ALMA) to determine the circumstellar gas masses and the $^{17}$O/$^{18}$O isotopic ratios, which correlate with initial mass. These are interpreted based on results from stellar evolution models in the literature and existing observations of other post-AGB stars.

Based on the inferred $^{17}$O/$^{18}$O isotopic ratios, we find all stars to have relatively low initial masses ($< 2~M_\odot$) contrary to suggestions in the literature of higher masses for some sources. One of the C-rich sources, HD 187885, has a low $^{17}$O/$^{18}$O ratio, which together with a low metallicity implies a relatively low mass ($\sim 1.15~M_\odot$) for a carbon star. For all but one source (GLMP 950), we observe kinematic components with velocities $\gtrsim 30$ km s$^{-1}$, which are faster than typical AGB wind expansion velocities. For most sources, these higher-velocity outflows display point-symmetric morphologies. The case of Hen 3-1475 is particularly spectacular, with the high-velocity molecular outflow appearing interleaved with the high-velocity outflow of ionised gas observed at optical wavelengths. Based on the size of the emission regions of the slow components of the outflows, we derive typical kinematic ages associated with the C$^{18}$O $J=2-1$ emission $\lesssim 1500$ years and obtain relatively high associated mass-loss rates ($\gtrsim10^{-4}~M_\odot~{\rm yr}^{-1}$). The sources with known spectral types are found to have evolved faster than expected based on stellar evolutionary models.

# Introduction

Stars with initial masses between roughly 1 and 8 $M_\odot$ evolve through the the asymptotic giant branch (AGB) at the end of their lives (cite: Karakas2014). In this phase, nuclear burning of helium and hydrogen happens in separate layers around the inert core rich in carbon and oxygen (cite: Herwig2005). The dense, stratified inner region is surrounded by a large ($\sim 1$ au) convective stellar envelope, making AGB stars large red giants. The combination of large sizes, low values of surface gravity, and cool and pulsating outer layers leads to such a strong mass-loss process on the AGB phase (cite: Hoefner2018) that it dominates the evolution of the star from its onset. This process continues until the stellar envelope has essentially been stripped away. The high-energy radiation field from the newly exposed core eventually ionises the ejected gas. If the timing between outflow expansion and evolution of the central remnant is in the right range, the envelope will be visible as a planetary nebula (cite: Kwok1994).

Explaining the shapes and properties of planetary nebulae (PNe) has been a long-standing problem in astrophysics. The transition from the mostly spherically symmetric outflows of AGB stars to the complex morphologies of PNe (cite: Sahai1998; Parker2006; Sahai2007; Sahai2011) has been a particularly challenging problem to solve. Recent observations of AGB stars have revealed distributions of the circumstellar molecular gas (cite: Decin2020) which are reminiscent of complex patterns of arcs and shells seen in the haloes of some PNe. These structures have been suggested to be created by stellar or even planetary companions. The ejection of clumps of gas in random directions due to convection has also been proposed as an important shaping mechanism of AGB outflows (cite: Velilla-Prieto2023). However, the evolution of the structures of the density distributions into later evolutionary phases, their prevalence in the envelopes of AGB stars, and the average fraction of the circumstellar envelope (CSE) mass contained in such structures remains not well constrained. On large scales and at lower resolutions, the molecular CSEs of AGB stars appear spherically symmetric on average (cite: Ramstedt2020).

One important process invoked to explain the circumstellar masses of PNe is the so-called super-wind, which has been proposed to be a short phase of intense mass loss (with rates $\sim 10^{-4}~M_\odot~{\rm yr}^{-1}$) taking place at the end of the AGB (cite: Renzini1981; Vassiliadis1993). One possibility is that PNe are mostly the outcome of binary interactions, in which a type of common-envelope phase takes place (cite: Jones2017; Boffin2019). However, only a relatively small fraction ($\sim 20\%$) of stars evolving through the AGB are expected to have stellar companions at small-enough separations to potentially induce this type of evolution (cite: Boffin2019; Khouri2022). This relatively low fraction might not be in tension with the observed number of PNe because population synthesis calculations indicate that only a fraction of low- and intermediate-mass stars produce bright PNe (cite: Moe2006; DeMarco2009). Moreover, single-star models do not maintain the required rotation rates to reproduce the observed fraction of non-symmetric PNe (cite: GarciaSegura2014). Finally, the empirical binarity fraction of central-stars of PNe is only a lower limit $\gtrsim 20~\%$ (cite: Jones2017) to the actual fraction, given the observational challenges for this type of study (cite: DeMarco2015). Nonetheles, the clear correlation between the orientation of the PNe axis and the axis of the orbital plane in PNe with known binary central stars (cite: Hillwig2016) implies that companions strongly affect the shape of PNe.

Given the observational evidence and the current limitations to studies of PNe and AGB stars, studying the phase before the PN stage and immediately after the AGB, the post-AGB phase, is crucial for understanding the final stages of the lives of low- and intermediate-mass stars. A subclass of post-AGB sources with dusty discs (containing $> 80$ objects) are known to very often have detectable close companions (cite: vanWinckel2007; Oomen2018). Some of these sources even display gaseous discs with Keplerian rotation that remain stable over long timescales (cite: vanWinckel2018; GallardoCava2021). Although determining binary fractions in post-AGB stars more obscured by circumstellar dust is difficult, observations of the morphology and dynamical components of their CSEs provides important clues. Studies of such objects have found high-velocity outflows with excess momentum that cannot be explained by radiation-driven outflows (cite: Bujarrabal2001) and complex morphologies (cite: Sahai2007; Lagadec2011). In fact, jets or bipolar outflows are expected to be one of the main agents affecting the morphologies of these systems and of PNe (cite: Sahai1998; Sahai2011; Soker2020). Circumstellar masses derived based on CO observations of post-AGB sources range broadly from $10^{-2}$ to $1~M_\odot$ (cite: Bujarrabal2001; SanchezContreras2012). The different configurations of binary systems leading to the observed post-AGB morphology and CSE components remain under investigation.

Another important diagnostic is the study of the isotopic ratios of the ejected material, which can be interpreted using our understanding of nucleosynthesis and stellar evolution. The isotopes of oxygen, and specifically the $^{17}$O/$^{18}$O ratio, provide particularly powerful constraints on the initial masses of stars in this mass range. For most low- and intermediate-mass stars, the significant changes to the oxygen isotopic ratios take place between the main sequence and the red giant branch phases, when convective streams in the stellar envelope reach material processed by nucleosynthesis in the stellar interior in a process referred to as the first dredge up (cite: Karakas2014). There is overall agreement between different stellar evolution models on the quantitative values of oxygen isotopic ratios after the first dredge up (cite: DeNutte2017). However, the expected dependence of this ratio on the initial stellar mass of stars has not been fully validated by observations thus far (cite: Abia2017). The oxygen isotopic ratios have been extensively studied for AGB stars (cite: Harris1987; Smith1990; Hinkle2016; Abia2017; Danilovich2017; DeNutte2017; Lebzelter2019), but less often for post-AGB objects.

Stellar evolution models also predict whether or not stars with a given initial mass and metallicity become carbon-rich at the end of the AGB. The increase of the carbon abundance in excess of that of oxygen in the stellar envelope happens for stars with initial mass between $\sim 1.5$ and $\sim 4$ $M_\odot$ during the third dredge up (cite: Karakas2014), which is a mixing event that takes place during the AGB phase itself (cite: Iben1983). The lower mass limit for stars to become carbon rich is defined by whether the enrichment is efficient and proceeds for long enough, while the upper mass limit depends on whether the temperature at the base of the convective envelope is high enough to convert carbon mainly into nitrogen in a process known as Hot Bottom Burning (cite: Herwig2005). The efficiency of the third dredge up in enriching the stellar envelope with carbon depends on many parameters, including mixing efficiency, AGB lifetimes, and prescriptions for the mass-loss rate included in stellar evolution models (cite: Stancliffe2004; Abia2017; Rees2024). If HBB takes place, $^{18}$O is expected to be very efficiently destroyed leading to very low $^{18}$O abundances, but the minimum initial stellar mass for which HBB becomes important is fairly uncertain (cite: Ventura2018). A few AGB stars with extreme mass-loss rates seem to belong to this class (cite: Justtanont2012), while no post-AGB stars with very low $^{18}$O abundances have been identified thus far to our knowledge. In fact, recent studies of oxygen isotopic ratios in post-AGB stars (cite: Khouri2022; Alcolea2022) have indicated that some of the most obscured post-AGB sources have relatively low initial masses ($\lesssim 3~M_\odot$), contrary to the expectation that these were more massive stars with initial masses $\gtrsim 5~M_\odot$.

A small subclass of post-AGB stars termed water fountains accounts for a significant fraction of the post-AGB objects with determined oxygen isotopic ratios (cite: Khouri2022). These sources show water maser emission with expansion velocities higher than those of their own OH maser emission, which is not observed in any other class of AGB or post-AGB stars. The water maser emission is thought to arise from the interaction of a nascent jet with a dense CSE (cite: Imai2007). The envelopes present tori-like structure oriented mostly perpendicularly to bipolar lobes sculpted by high-velocity jets (cite: Sahai2017; Gomez2018; Tafoya2020). The ejection of large amounts of mass in these systems seems to have occurred $\lesssim 100$ years ago (cite: Boboltz2007; Day2010). The compactness of the emission observed towards water fountains and other highly obscured sources suggests a period of very intense mass loss, which has been proposed to be triggered by interactions with a nearby companion (cite: Khouri2022; Alcolea2022). The process experienced by these sources could be connected to the super-wind phase, but whether these are the same, or related at all, remains presently unknown.

Regarding carbon enrichment, a lot of effort has been put into reproducing the mass range for which stars become carbon rich in stellar evolution models. Observations of carbon-rich stars in open clusters indicate that the lower limit in initial mass for forming carbon-rich stars is $\sim~1.5~M_\odot$ (cite: Groenewegen1995) at solar metallicity. A similar limit is obtained by fitting the luminosity function of carbon stars in the Milky Way and satellite galaxies using stellar evolution codes (cite: Groenewegen2002), but the initial mass might extend down to $\sim 1~M_\odot$ at lower metallicities (cite: Stancliffe2005). However, the predicted minimum luminosity is high compared to observations. Stellar evolution models are able to reproduce carbon stars with initial masses as low as $\sim 1.5~M_\odot$ by including extra mixing for the third dredge-up to be efficient enough (cite: Weiss2009; Cristallo2015; Karakas2016; Ventura2018; Goriely2018; Rees2024).

In this paper, we study a small sample of six obscured post-AGB objects and investigate the $^{17}$O/$^{18}$O ratio, their recent mass-loss rates, and the CSE morphology at scales of a few thousand au using the $J$=2$-$1  transitions of isotopologues of CO. In Section [2](#sec:sample) we list the sample stars and their relevant characteristics from literature. In Sections [3](#sec:obs) and [4](#sec:obsRes) we describe the observations and present the results, respectively. The results are discussed in the context of our current understanding in Section [6](#sec:disc). Finally, a summary and conclusions are presented in Section [7](#sec:conc).

# Sample

## Sample selection

We observed six post-AGB stars selected for having very red colours. To select our sample, we obtained magnitudes in the $J$ band from 2MASS and in the $S9W$ and $L18W$ bands from AKARI using the catalogue by (cite: Ita2010) for post-AGB stars listed in (cite: Szczerba2007). We selected sources with $J-L18W > 8$ and $S9W-L18W > 2$. When the magnitudes for AKARI filters were missing, we obtained values by interpolating the spectral energy distribution (SED) of the given source using the VizieR photometry tool. The colour-colour diagram containing the sample of post-AGB stars is shown in Fig. [1](#fig:colour-colour). The sources presented in this paper are shown by the blue pentagons, while water fountain sources studied in (cite: Khouri2022) (cite: Szczerba2007) are shown by the green squares. Our original sample of post-AGB stars consisted of twenty sources, but only six were successfully observed with ALMA within this project. Four of these (GLMP 950, GLMP 953, AFGL 5385, and HD 187885) are rich in carbon, while the other two (Hen 3-1475 and M1-92) have oxygen-rich composition. The bluer colors of the two oxygen-rich stars in our sample could in principle be linked to a systematic lower absorption opacity of oxygen-rich relatively to carbon-rich dust or to lower gas-to-dust ratios in C-rich sources. This is especially intriguing when considering the similar gas mass-loss rates and timescales derived below. However, the small number of sources in our sample prevents us from investigating this difference further.

![](Fig_color-color_AKARI_pilotSample.pdf)

## Relevant information on individual sources

GLMP 950 (IRAS 19454+2920) and GLMP 953 (IRAS 19480+2504) were imaged by (cite: Lagadec2011) at wavelengths between 8 and 13 $\mu$m using VISIR/Very Large Telescope (VLT). The authors found GLMP 950 to be spatially resolved in the images, with a somewhat elliptical shape extending in the east-west direction to a maximum size of $\sim 2 \ensuremath{''}$. GLMP 953 was not spatially resolved in the observations with a full-width at half maximum (FWHM) of the Gaussian beam of $\sim 0.54\ensuremath{''}$.

AFGL 5385 (IRAS 17441-2411, the Silkworm Nebula) displays an edge-on torus oriented in the southeast-northwest direction and bipolar lobes oriented roughly in the north-south direction. An S-shaped structure is also visible within the lobes. This nebula has been imaged in visible light (cite: Su1998) and in the near-IR (cite: Su2003) with the *Hubble Space Telescope (HST)*, and in the mid-IR with T-ReCS/Gemini South (cite: Volk2007) and VISIR/VLT (cite: Lagadec2011). The bipolar lobes have a total extent of $\sim 4\ensuremath{''}$, while the torus has a size of $\sim 1\ensuremath{''}$.

HD 187885 (IRAS 19500-1709) is commonly classified as a carbon-rich post-AGB star, but its determined elemental abundances indicate a carbon-to-oxygen ratio close to unity (cite: vanWinckel1996; vanWinckel2000). The source was also determined to be more metal poor than the Sun, with \[Fe/H\] = $-0.6$ (cite: vanWinckel2000). (cite: Lagadec2011) observed a slightly elliptical source with size $\sim 3\ensuremath{''}$ at 11.85 and 12.81 $\mu$m using VISIR/VLT. They find an inner radius of the CSE of $\sim 0.4\ensuremath{''}$, which confirmed previous indications from images at 10 and 20 $\mu$m obtained using the OSCIR/Gemini North (cite: Clube2004). Modelling of the spectral energy distribution (SED) indicates a dust mass in the CSE of $\sim 7 \times 10^{-4}~M_\odot$ and an associated duration of the high-mass-loss phase of 4000 yr (cite: Clube2004), where both values have been converted to the distance of 2.4 kpc adopted in this work. As discussed by the authors, under the assumption of a gas-to-dust ratio of 220 these results imply a mass-loss rate of $\sim 4 \times 10^{-4}~M_\odot~{\rm yr}^{-1}$, which is large in comparison to other determinations also through SED modelling (cite: Guertler1996). (cite: Bujarrabal2001) found a clear separation between a slow (expansion velocity $\sim 10$ km s$^{-1}$) and a faster (expansion velocity $\sim 50$ km s$^{-1}$) components of the outflow in CO emission lines. The authors derived a total circumstellar gas mass of $\sim 7 \times 10^{-3}$ and $\sim 2.6 \times 10^{-2}~M_\odot$ for the fast and slow outflows, respectively, considering a distance of 1 kpc. At the distance of 2.4 kpc adopted by us, the fast and slow outflows would contain masses of $\sim 4 \times 10^{-2}$ and $\sim 0.15~M_\odot$, respectively.

Hen 3-1475 (IRAS 17423-1755) displays a bipolar morphology in images in visible light with a northwest-southeast orientation of the lobes and atomic line widths which imply a velocity range of $\sim1000$ km s$^{-1}$ (cite: Bobrowsky1995). Within the bipolar lobes, a point-symmetric structure with knots is visible in emission of atomic lines (cite: Borkowski1997). Hen 3-1475 is the only post-AGB object where an ultrafast ($\sim 2300$ km s$^{-1}$) collimated jet, presumably in a pristine stage before interacting with the surrounding nebula, has been identified with HST/STIS (cite: SanchezContreras2001). The inclination of the ultrafast wind is $\sim75^\circ$ with respect to the plane of the sky, whereas the mean inclination of the nebula (reflecting lobes and CO hourglass) is $\sim 50^\circ$. (cite: Borkowski2001) determined a distance of 8.3 kpc to Hen 3-1475 based on proper motions of the jet knots, implying a luminosity of $25000~L_\odot$. This led them to conclude that Hen 3-1475 is a massive AGB star or the product of binary evolution. (cite: Riera2003) finds a smaller distance ($5.8 \pm 0.9$ kpc), but also suggests a high initial mass based on a nitrogen overabundance reported by (cite: Riera1995). A distance of 5.8 kpc implies a luminosity of $\sim 12000~{\rm L}_\odot$. (cite: Bujarrabal2001) identified a slow (with expansion velocity $\sim 7$ km s$^{-1}$) and a faster (with expansion velocity $\sim 50$ km s$^{-1}$) component in the outflow of Hen 3-1475 based on CO and $^{13}$CO $J$=1$-$0  and $J$=2$-$1  lines. They inferred a mass of 0.16 $M_\odot$ and 0.47 $M_\odot$ for the two dynamical components, respectively, for a distance of 5 kpc. (cite: Huggins2004) derived a circumstellar mass of 0.64 $M_\odot$ based on the measured continuum emission of $5.3 \pm 1.2$ and $31 \pm 4$ mJy at 2.6 and 1.3 mm, respectively, for a distance of 5.8 kpc and a gas-to-dust ratio of 100. The CO $J$=1$-$0  and $J$=2$-$1  lines were most likely affected by optical depth effects and implied a lower limit for the circumstellar mass of 0.19 $M_\odot$. (cite: Manteiga2011) suggest Hen 3-1475 to be a high-mass ($M > 3~M_\odot$) O-rich post-AGB star based on the presence of water ice absorption. We adopt a distance of 5.8 kpc to Hen 3-1475, following (cite: Riera1995).

M1-92 (IRAS 19343+2926, Minkowski’s Footprint) displays a bipolar shape at optical wavelengths (cite: Trammell1996). The strong molecular emission has been extensively observed and modelled in detail (cite: Bujarrabal1997; Alcolea2007; Alcolea2022). The lines of the isotopologues of CO have been studied previously. In particular, emission from C$^{17}$O and C$^{18}$O have been used to determine a $^{17}$O/$^{18}$O ratio of $1.6\pm0.15$ (cite: Alcolea2022). Given these detailed studies, we refrain from discussing the morphology of this source extensively, and only report the values measured by us highlighting differences to values in the literature.

We adopt distances to each object from (cite: Vickers2015), with the exception of Hen 3-1475, for which we adopt the value from (cite: Riera1995). The distances used in this work, and their respective references, are provided in Table [\[tab:cont\]](#tab:cont).

|  |  |  |  |
|:---|:--:|:--:|:--:|
| Source | Beam | Noise level | MRS |
|  | \[FWHM and PA\] | \[mJy/beam\] | \[$\ensuremath{''}$\] |
| GLMP 950 | $1.09\ensuremath{''} \times 0.77\ensuremath{''}$ / -6$^\circ$ | 2.5 | 10.4 |
| GLMP 953 | $1.00\ensuremath{''} \times 0.78\ensuremath{''}$ / -8$^\circ$ | 2.5 | 9.8 |
| AFGL 5385 | $1.19\ensuremath{''} \times 0.63\ensuremath{''}$ / -87$^\circ$ | 1.9 | 9.8 |
| HD 187885 | $0.93\ensuremath{''} \times 0.78\ensuremath{''}$ / -77$^\circ$ | 1.9 | 8.0 |
| Hen 3-1475 | $1.22\ensuremath{''} \times 0.65\ensuremath{''}$ / -84$^\circ$ | 1.6 | 10.0 |
| M1-92 | $1.10\ensuremath{''} \times 0.77\ensuremath{''}$ / -11$^\circ$ | 2.2 | 10.3 |

: Parameters of the observations for each source.

Table notes: The beam FWHM is an average value for the spectral window with lowest frequencies (between $\sim 219.44$ GHz and $\sim 221.31$ GHz) and the noise level in the spectral cube is given at a reference frequency of 221 GHz towards the position of the continuum peak.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $d$ | $L$ | Chem. | Spec. | $\upsilon_{\rm LSR}$ | $S^{\rm cont}_\nu$ | $\alpha^{\rm cont}$ | $\delta^{\rm cont}$ | FWHM and PA of cont |  |
|  | \[kpc\] | \[$10^3 L_\odot$\] | Type | Type | \[km s$^{-1}$\] | \[mJy\] |  |  | \[$\ensuremath{''} \times~ \ensuremath{''} / ^\circ$\] |  |
| GLMP 950 | 3.9$^{\rm a}$ | 6 | C$^{\rm c}$ | ? | 22 | $5.2 \pm 0.6$ | $19^{\rm h}47^{\rm m}24^{\rm s}.43$ | $+29^{\rm \circ}28\ensuremath{'}13\ensuremath{''}6$ | $0.48 (0.04) \times 0.39 (0.03)/170 (20)$ |  |
| GLMP 953 | 3.8$^{\rm a}$ | 6 | C$^{\rm c}$ | ? | 42 | $119 \pm 12$ | $19^{\rm h}50^{\rm m}08^{\rm s}.20$ | $+25^{\rm \circ}11\ensuremath{'}57\ensuremath{''}1$ | $0.24(0.02) \times 0.26(0.01)/170(70)$ |  |
| AFGL 5385 | 3.4$^{\rm a}$ | 12 | C$^{\rm d}$ | F4I$^{\rm f}$ | 7 | $12.9 \pm 1.4$ | $17^{\rm h}47^{\rm m}13^{\rm s}.50$ | $-24^{\rm \circ}12\ensuremath{'}51\ensuremath{''}6$ | $1.4 (0.1) \times 0.79(0.09)/59(8)$ |  |
| HD 187885 | 2.4$^{\rm a}$ | 6 | C$^{\rm e}$ | F0Ie$^{\rm f}$ | 25 | $6.3 \pm 0.7$ | $19^{\rm h}52^{\rm m}52^{\rm s}.70$ | $-17^{\rm \circ}01\ensuremath{'}50\ensuremath{''}3$ | $1.67(0.06)\times1.43(0.06)/39(12)$ |  |
| Hen 3-1475 | 5.8$^{\rm b}$ | 11 | O | B7e$^{\rm b}$ | 49 | $29 \pm 3$ | $17^{\rm h}45^{\rm m}14^{\rm s}.18$ | $-17^{\rm \circ}56\ensuremath{'}46\ensuremath{''}9$ | $1.10(0.09) \times1.00(0.07)/$– |  |
| M1-92 | 2.6$^{\rm a}$ | 6 | O | B0.5IV$^{\rm g}$ | 2 | $127 \pm 13$ | $19^{\rm h}36^{\rm m}18^{\rm s}.88$ | $+29^{\rm \circ}32\ensuremath{'}49\ensuremath{''}6$ | – / – |  |

Table notes: Adopted distances and corresponding luminosities, chemical types, spectral types, systemic velocities measured from the spectra, and measured integrated continuum flux densities at 1.31 mm ($S^{\rm cont}_\nu$), continuum-peak positions, and FWHM sizes and position angle from Gaussian fit to continuum images.

# Observations

The observations were carried out using the Atacama Large Millimeter / submillimeter Array (ALMA) in the context of project 2021.1.01259.S. The data reduction was performed by the observatory using the standard ALMA pipeline and the Common Astronomy Software Applications for Radio Astronomy (cite: CASA2022) versions 6.2.1.7 for HD 187885 and 6.4.1.12 for the other five sources. We obtained the reduced cubes made available through the ALMA archive. The telescope setting was planned in Band 6 so that the $J$=2$-$1  lines of C$^{17}$O (at 224.714 GHz) and C$^{18}$O (at 219.560 GHz) could be observed in the same frequency tuning. The same line of $^{13}$CO (at 220.399 GHz) was also observed in the spectral window used to observe the C$^{18}$O line. No $^{12}$CO line was observed as part of this program.

The four spectral windows covered frequencies ranging in the rest frame of the sources from $\sim 219.44$ GHz to $\sim 221.31$ GHz, $\sim 222.93$ GHz to $\sim 224.80$ GHz, $\sim 234.05$ GHz to $\sim 234.92$ GHz, and $\sim 235.95$ GHz to $\sim 237.81$ GHz. The exact frequency ranges varied slightly from one source to the other. We adopt an absolute flux calibration uncertainty of $10\%$[^2]. This does not apply to the calculations of line ratios, for which the relative flux calibration is much more accurate. Hence, the relative flux calibration between the different molecular lines is negligible compared to the uncertainty from integrating the line emission.

The details of the obtained cubes are given in Table [1](#tab:obs). The resolution of the maps varies between $0.63\ensuremath{''}$ and $0.78\ensuremath{''}$ for the different sources, while the sensitivity in the continuum-subtracted maps varies between 1.6 and 2.5 mJy/beam for a channel resolution of $\sim1$ MHz ($\sim 1.4$ km s$^{-1}$). The maximum recoverable scale (MRS) is significantly larger than the extent of all sources in any given channel, with the exception of the continuum emission in M1-92 (see below). Even in this case, the observations presented here seem to recover all continuum emission as discussed in Section [4.7](#sec:M1-92).

The continuum maps produced by the ALMA pipeline include the four spectral windows and have a representative frequency of 228.6 GHz, which corresponds to a wavelength of 1.31 mm.

# Observational results

The $J$=2$-$1  lines of the three targeted isotopologues of CO ($^{13}$CO, C$^{17}$O, and C$^{18}$O) were detected for all sources. About $30$ other lines emitted by $\sim 10$ other molecules were also detected (Table [2](#tab:lines)). The vast majority of these lines was detected only towards the C-rich sources GLMP 950 and GLMP 953. The detections towards these two sources include lines assigned by us to NaCl, SiC$_2$, K$^{37}$Cl (tentative), and HC$_3$N. We also detect a few unidentified lines. The spectra of the two other C-rich sources display almost no lines besides those from CO isotopologues, with only an HC$_3$N line detected towards AFGL 5385, and no other lines detected towards HD 187885. The lack of lines in the spectrum of HD 187885 might be caused by its low initial metallicity.

The two O-rich sources show a smaller number of lines. Hen 3-1475 is the most line rich of the two, with five lines detected besides those from CO isotopologues. We assign the detected lines to emission from SO, SiS, and SO$_2$. M1-92 shows emission lines of SO and SO$_2$.

## Methodology for line and continuum measurements

To determine the sizes of the apertures for measuring the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  line emission and the continuum fluxes, we employ the following procedure. First, we obtain the line profiles from circular regions with 5$''$  in diameter for each source. Then, we measure the full-width at zero intensity of the C$^{17}$O and C$^{18}$O $J$=2$-$1  lines, which are very similar for all sources. Using the velocity range measured for the C$^{18}$O $J$=2$-$1  line, we produced moment-zero (integrated in velocity) maps of the $^{13}$CO $J$=2$-$1  line. This was done to obtain a map of the brightest line ($^{13}$CO $J$=2$-$1 ) while excluding any velocity components not detected in C$^{18}$O $J$=2$-$1. If the contour marking emission three times above the root mean square (3-$\sigma$) of this $^{13}$CO $J$=2$-$1  moment-zero map was larger than the 5$''$  aperture, we used an aperture of 7$''$  instead, which proved sufficiently large to enclose the 3-$\sigma$ contour for all sources. We use circular apertures of similar size when possible for simplicity because the uncertainties introduced by the aperture shape are small for sources that are nearly circular. Following this procedure, we obtain aperture diameters of 5$''$  for GLMP 950 and Hen 3-1475 and 7$''$  for GLMP 953, AFGL 5385 and HD 187885. For M1-92, we integrated the emission with a non-circular aperture equal to the 3-$\sigma$ contour. This was motivated by the very elongated morphology and large size of the emission region in M1-92 (see Fig. [9](#fig:13CO)). The high-velocity emission discussed below observed towards different sources are produced in regions within the circular apertures described above for all sources but Hen 3-1475. Hence, to obtain the spectra of the high-velocity component of Hen 3-1475, we used a rectangular aperture oriented along the axis of the high-velocity emission as described below. The obtained moment-zero maps of the C$^{13}$O, C$^{17}$O and C$^{18}$O $J$=2$-$1  lines are shown in Figs. [9](#fig:13CO), [10](#fig:C17O), and [11](#fig:C18O), respectively.

The continuum emission is expected to be dominated by dust emission at these wavelengths, with only a very small contribution from free-free emission at 1.3 mm for the two objects with B-type central stars, Hen 3-1475 and M1-92 (cite: SanchezContreras2017). The continuum flux density reported in Table [1](#tab:obs) were obtained by integrating the emission within the same apertures used to extract the line profiles, and, hence, adapted to fully enclose the emitting area of each source. The FWHM sizes of the continuum emission reported below were measured using the Interactive 2D fitting tool in CASA to fit a Gaussian function convolved with the beam to the maps in the image plane. Hence, the sizes we report are beam-deconvolved FWHM of the best-fitting Gaussian distributions. The measured continuum flux density, position of the emission centre, and continuum FWHM are given in Table [\[tab:cont\]](#tab:cont). All coordinates throughout the paper are given in the equatorial system (J2000).

## GLMP 950 (IRAS 19454+2920)

The continuum image and the line profiles of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  extracted towards GLMP 950 from a circular region centered on the source and with $5\ensuremath{''}$ in diameter are shown in Fig. [2](#fig:GLMP950). The line fluxes obtained from integrating the $J$=2$-$1  lines from $^{13}$CO, C$^{17}$O, and C$^{18}$O over the same region are given in Table [\[tab:meas\]](#tab:meas).

![image](Fig_GLMP_950_13CO.pdf) ![image](Fig_spectrum_GLMP950.pdf)

### Continuum

The original pointing direction was $\alpha = 19^{\rm h}47^{\rm m}24^{\rm s}.835$ and $\delta = 29^{\rm \circ}28\ensuremath{'}10\ensuremath{''}817$ based on the visible position assigned by the Simbad database (cite: Simbad2000) at the time of our observations, which was that of the source Gaia DR3 2031794791233840128 (cite: Gaia2021). That position also corresponds to the near-infrared source 2MASS J19472480+2928108. However, we detected a mm continuum source at $\alpha = 19^{\rm h}47^{\rm m}24^{\rm s}.43$ and $\delta =29^{\rm \circ}28\ensuremath{'}13\ensuremath{''}556$, which lies $5.96\ensuremath{''}$ away from the 2MASS and Gaia coordinates. We inspected publicly available Spitzer/IRAC images downloaded from the IRSA archive, and noticed two individual sources, one at the optical/near-infrared position and another one at the location of our mm source (Fig. [12](#fig:Spitzer_GLMP950)). The latter is brighter at longer Spitzer wavelengths. We conclude that our mm source corresponds to the far-infrared source IRAS 19454+2920 and the GLMP entry. Therefore, the position we report is the actual position of GLMP 950.

The fit of an elliptical Gaussian source to our continuum image reveals a deconvolved FWHM significantly smaller than the beam, with a major axis of $485 \pm 40$ milliarcsecond (mas), a minor axis of $390 \pm 30$ mas and a position angle of $170 \pm 20^\circ$. The orientation we find is similar to that of the beam and, hence, it is unclear whether this an observational effect or a real feature. Moreover, the orientation reported by (cite: Lagadec2011) in the mid-IR ($\sim 100^\circ$) is significantly different from the one we find. Higher-angular-resolution observations are necessary to confirm whether this difference is real given the small size of the source compared to the resolution of the observations we report. A flux density of $5.0 \pm 0.5$ mJy is recovered from the fit. A slightly larger flux density, of $5.2\pm0.6$ mJy is obtained from integrating the continuum image within a region of $5\ensuremath{''}$ in diameter.

### Line emission

The bulk of the emission in the $^{13}$CO $J$=2$-$1  line is seen at velocities, $|\upsilon - \upsilon_{\rm LSR}| \lesssim 16$ km s$^{-1}$ from the systemic velocity with respect to the local standard of rest (LSR), $\upsilon_{\rm LSR} \approx 22$ km s$^{-1}$, while a weaker component extends to $|\upsilon - \upsilon_{\rm LSR}| \lesssim 20$ km s$^{-1}$. Integrating the $^{13}$CO $J$=2$-$1  line over the interval 16 km s$^{-1} \leq |\upsilon - \upsilon_{\rm LSR}| \leq$ 20 km s$^{-1}$ produces maps that peak essentially at the same position as that produced by integrating the central region of the line, $|\upsilon - \upsilon_{\rm LSR}| \leq$ 16 km s$^{-1}$. Hence, no sign of a more complex morphology of the line emission as a function of velocity is detected at the resolution of the observations we report.

A Gaussian fit to the map produced integrating the $^{13}$CO $J$=2$-$1  line over the whole profile reveals an essentially circular source with deconvolved FWHM of major and minor axes of $1.13\ensuremath{''} \pm 0.08\ensuremath{''}$ and $1.02\ensuremath{''} \pm 0.07\ensuremath{''}$, respectively, and an unconstrained position angle.

Neither the continuum nor the moment-zero maps of the $^{13}$CO $J$=2$-$1  line reveal a significantly elongated source. This differs from the 2$''$ east-west source size reported by (cite: Lagadec2011) from observations of dust emission in the mid-IR.

## GLMP 953 (IRAS 19480+2504)

The continuum image and the profiles of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines extracted towards GLMP 953 using an aperture of 7$''$ centered on the continuum peak are shown in Fig. [3](#fig:GLMP953). The fluxes of the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O integrated over the same region are given in Table [\[tab:meas\]](#tab:meas).

![image](Fig_GLMP_953_HighVel.pdf) ![image](Fig_spectrum_GLMP953.pdf) ![image](Fig_spectrum_GLMP953_13CO_centralPixel.pdf)

### Continuum

Similarly to the case of GLMP 950 mentioned above, the original pointing direction was $\alpha = 19^{\rm h}50^{\rm m}08^{\rm s}.281$ and $\delta = +25^{\rm \circ}12\ensuremath{'}00\ensuremath{''}813$, based on the position reported in the Simbad database (cite: Simbad2000), which corresponds to the optical source Gaia DR3 2026709201998745472 (cite: Gaia2021), also positionally coincident with the near-IR source 2MASS J19500826+2512008 (cite: Cutri2003). However, we detected a mm continuum source centered at $\alpha = 19^{\rm h}50^{\rm m}08^{\rm s}.203$ and $\delta = +25^{\rm \circ}11\ensuremath{'}57\ensuremath{''}14$. The position we find differs by 3.83$''$ from those in the Gaia and 2MASS catalogues. Spitzer/IRAC images also show two distinct sources (Fig. [13](#fig:Spitzer_GLMP953)), one coinciding with the position of the mm continuum and another coinciding with the optical/near-IR source, which is significantly weaker in all Spitzer bands. We thus conclude that our position (rather than the one reported by Simbad at the time of our observations) corresponds to that of the GLMP entry and the far-IR source IRAS 19480+2504, and should be adopted as the actual position of GLMP 953.

By fitting an elliptical Gaussian to the mm-continuum source, we obtain a nearly circular intensity distribution, with deconvolved FWHM of $240 \pm 20$ mas along the major axis and $225 \pm 10$ mas along the minor axis, which is roughly a factor of four smaller than the beam size. The position angle and the flux density retrieved from the fit are $170 \pm 70^\circ$ and $118 \pm 12$ mJy, respectively. Integrating the continuum emission within an aperture of $5\ensuremath{''}$ in diameter reveals an essentially equal value of $119\pm12$ mJy. The size we report is consistent with the unresolved source between 8 and 13 $\mu$m reported by (cite: Lagadec2011) based on observations with a beam size of $\sim 0.54\ensuremath{''}$.

### Line emission

Most of the emission in the $^{13}$CO $J$=2$-$1  line lies within $|\upsilon - \upsilon_{\rm LSR}| \lesssim 16.5$ km s$^{-1}$ with $\upsilon_{\rm LSR} \approx 42$ km s$^{-1}$. A weaker, higher-velocity component extending roughly between $-60$ km s$^{-1}$ and 125 km s$^{-1}$ is also observed. Hence, the total line width is $\sim 185$ km s$^{-1}$. Integrating the emission from the high-velocity component, from $|\upsilon - \upsilon_{\rm LSR}| \gtrsim 16.5$ km s$^{-1}$ to the extreme of the line wings (range marked in gray in Fig. [3](#fig:GLMP953)), reveals emission regions slightly offset from the centre of the continuum peak. The distance between the centers of the red- and blue-shifted high-velocity components is $\sim 0.35\ensuremath{''}$ and the position angle is $\sim -10^\circ$, with a high associated uncertainty because of the small separation between the two components.

## AFGL 5385 (IRAS 17441-2411, the Silkworm Nebula)

The continuum image and the profiles of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines extracted towards AFGL 5385 using a circular region with $7\ensuremath{''}$ in diameter are shown in Fig. [4](#fig:AFGL_highVel). The fluxes of the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O integrated over the same region are given in Table [\[tab:meas\]](#tab:meas).

![image](Fig_AFGL_5385_HighVel.pdf) ![image](Fig_spectrum_AFGL5385.pdf)

### Continuum

Fitting a Gaussian source, we obtain deconvolved FWHM axes of $1.4\ensuremath{''} \pm 0.1\ensuremath{''}$ and $0.79\ensuremath{''} \pm 0.09\ensuremath{''}$ and a position angle of $59^\circ \pm 8^\circ$. The integrated flux density obtained from the fit is $11.8 \pm 1.3$ mJy. The continuum map shows an S-shaped morphology with two extensions in a roughly perpendicular direction to the elliptical central source. These reach $\sim 2.3\ensuremath{''}$ in radius from the centre, and are not captured by the Gaussian fit. Including these extensions in the continuum integration using the $7\ensuremath{''}$ aperture leads to a flux density of $12.9\pm1.4$ mJy.

An additional point-like source is detected at $\alpha = 17^{\rm h}47^{\rm m}14^{\rm s}.03$ and $\delta = -24^{\rm \circ}12\ensuremath{'}52\ensuremath{''}8$, i.e. at $\sim 7.5\ensuremath{''}$ ($\sim 2.5\times10^4$ au at 3.4 kpc) to the east of AFGL 5385. The flux density of this second source peaks at 0.4 mJy, which is $\sim 9$ times above the root-mean-square noise level of the continuum map. The continuum image including this additional source is shown in Fig. [14](#fig:AFGL_cont). It is unclear whether this second 1.3 mm continuum source is associated to AFGL 5385, or is a field object. The brightness ratio between the two sources at 1.3 mm and the coincidence of the position of the 1.3 mm emission of AFGL 5385 and that from the 2MASS maps imply that this secondary source does not affect the photometry obtained towards AFGL 5385 significantly.

### Line emission

We obtain $\upsilon_{\rm LSR}\approx 7$ km s$^{-1}$ based on the approximate centres of the C$^{18}$O and C$^{17}$O $J$=2$-$1  lines. This value, however, leads to the main component of the $^{13}$CO $J$=2$-$1  line to show more red-shifted than blue-shifted emission, which could be a sign of relatively high optical depths affecting the $^{13}$CO line shape as this produces the well-known effect of blue-wing self-absorption (cite: Morris1985).

The bulk of the $^{13}$CO $J$=2$-$1  line emission arises from $-2.5~{\rm km}$ s$^{-1} \lesssim \upsilon \lesssim 20$ km s$^{-1}$. A weaker, higher-velocity component extending from $\upsilon \approx -19$ km s$^{-1}$ to $\upsilon \approx 30$ km s$^{-1}$ is also present. Interestingly, the line shape of this higher-velocity component is much more symmetric about the systemic velocity. This reinforces the suggestion that the velocity shift observed in the bulk of the $^{13}$CO $J$=2$-$1  emission is due to optical depth effects in the CSE.

Integrating the higher-velocity components in frequency over the interval marked in gray in Fig. [4](#fig:AFGL_highVel) reveals emission produced by gas offset from the position of the continuum. The displacement of the emission peak in the integrated images with respect to the continuum peak is $\sim 1.1\ensuremath{''}$ for the red-shifted emission and $\sim 1.5\ensuremath{''}$ for the blue-shifted emission. The high-velocity gas appears where the extensions of the continuum emission are also seen.

The position angle of the continuum emission region at millimeter wavelengths ($59^\circ \pm 8^\circ$) differs significantly from that observed in the mid-IR of $\sim 130^\circ$ (cite: Volk2007; Lagadec2011). Nonetheless, the S-shaped profile seen in those images is also clearly visible in the images we present. The emission regions of the higher-velocity gas are aligned roughly in the north-south direction, in apparent agreement with the orientation of the bipolar nebula seen in visible light (cite: Su1998). This high-velocity emission also follows the tips of the S-shaped continuum emission region. The total size of the emission region of the $^{13}$CO $J$=2$-$1  line is $\sim 5\ensuremath{''}$, which is comparable to the size of the bipolar lobes in the *HST* images (cite: Ueta2007) and of the mid-IR nebulosity (cite: Lagadec2011).

![image](Fig_HD_187885_HighVel.pdf) ![image](Fig_spectrum_HD187885.pdf) ![image](Fig_spectrum_HD187885_13CO_zoom.pdf)

## HD 187885 (IRAS 19500-1709)

The continuum image and the profiles of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines extracted towards HD 187885 using a circular region with 7$''$  in diameter are shown in Fig. [5](#fig:HD187885_highVel). The fluxes of the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O integrated over the same region are given in Table [\[tab:meas\]](#tab:meas).

### Continuum

The continuum source is spatially resolved by the observations, with a Gaussian fit revealing an elongated morphology with a deconvolved FWHM of $1.67\ensuremath{''} \pm 0.06\ensuremath{''}$ for the major axis and of $1.43\ensuremath{''} \pm 0.06\ensuremath{''}$ for the minor axis and a position angle of $39^\circ \pm 12^\circ$. The flux density obtained with the fit is $6.1 \pm 0.6$ mJy. Integrating the continuum using an aperture of 7$''$  in diameter reveals a similar flux density of $6.3\pm0.3$ mJy. This value is consistent with the upper limit reported for the flux density of this source at 1.2 mm of 23 mJy by (cite: Dehaes2007). The observations we report do not reveal an inner cavity in the disk as spotted in the mid-IR by (cite: Lagadec2011) and suggest based on modelling by (cite: Clube2004) before, but this is most likely due to the worse spatial resolution of the ALMA data relatively to that from VISIR.

### Line emission

The profile of the $^{13}$CO $J$=2$-$1  line (Fig. [5](#fig:HD187885_highVel)) shows three different components. The central and intermediate components comprise velocities $|\upsilon - \upsilon_{\rm LSR} | \lesssim 11$ km s$^{-1}$ and $|\upsilon - \upsilon_{\rm LSR} | \lesssim 27$ km s$^{-1}$, respectively, with $\upsilon_{\rm LSR} = 25$ km s$^{-1}$. The high-velocity component is significantly weaker and spans a velocity range of $\sim 145$ km s$^{-1}$.

Integrating the emission of this high-velocity component over the spectral region indicated in gray in Fig. [5](#fig:HD187885_highVel) reveals two elongated structures that extend away from the continuum peak in opposite directions. The elongations also curve in opposite directions, suggesting a point-symmetric structure. The continuum is elongated in a direction perpendicular to that of the high-velocity outflow. The red-shifted feature seems to align well with an emission hole in the 8.59 $\mu$m images presented by (cite: Lagadec2011). Whether there is a physical connection between these two features is unknown.

The peak value of the $^{13}$CO $J$=2$-$1  line (2.45 Jy) is compatible with the value of 2.6 Jy observed by (cite: Bujarrabal2001) using the IRAM 30m telescope. We converted the main beam temperature presented by the authors to flux density using historic values for the efficiencies of the IRAM 30m telescope available at the website of the observatory. Therefore, given the similarity between the two flux values and the beam size of the IRAM 30m telescope, which covers the entire extent of the nebula, the structures traced by our ALMA observations contain most of the emission in the $^{13}$CO $J$=2$-$1  line, with no significant emission coming from more extended structures.

![image](Fig_Hen_3-1475_HighVel.pdf) ![image](Fig_spectrum_Hen_3-1475.pdf) ![image](Fig_spectrum_Hen_3-1475_13CO_zoom.pdf)

## Hen 3-1475 (IRAS 17423-1755)

The continuum image and the profiles of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines extracted towards Hen 3-1475 using a circular region with 5$''$  in diameter are shown in Fig. [6](#fig:Hen_highVel). The fluxes of the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O integrated over the same region are given in Table [\[tab:meas\]](#tab:meas).

### Continuum

The continuum emission is spatially resolved in the observations and a fit of an elliptical Gaussian source provides a deconvolved FWHM of $1.10\ensuremath{''} (\pm 0.09\ensuremath{''}) \times 1.00\ensuremath{''} (\pm 0.07\ensuremath{''})$. Since the source is closer to appearing circular on the sky, the position angle is not well constrained. The Gaussian fit reveals a flux density of $27 \pm 3$ mJy. By integrating the continuum using a circular aperture of $5\ensuremath{''}$ in diameter, we obtain a flux density of $29\pm3$ mJy. These values are consistent with the previous determination of $31 \pm 4$ mJy (cite: Huggins2004).

### Line emission

The $\upsilon_{\rm LSR}$ of $\sim 49$ km s$^{-1}$ was derived using the peak of the narrow feature in the C$^{18}$O and C$^{17}$O lines, and it agrees fairly well with the peak of the $^{13}$CO line.

Different velocity components are observed in the lines of the CO isotopologues. A central core is apparent in the lines of C$^{18}$O and C$^{17}$O between velocities $|\upsilon - \upsilon_{\rm LSR}| \lesssim 9$ km s$^{-1}$ (with $\upsilon_{\rm LSR} = 48.5$ km s$^{-1}$), but is less clearly discernible in the $^{13}$CO line. Wings extending up to $|\upsilon - \upsilon_{\rm LSR}| \lesssim 45$ km s$^{-1}$ are prominent even in the lines of the two rarer isotopologues. In the $^{13}$CO line, the wings extend to even higher velocities $|\upsilon - \upsilon_{\rm LSR}| \lesssim 65$ km s$^{-1}$. The difference between the velocity range spanned by the wings in the different lines is most likely only due to the higher signal-to-noise in the $^{13}$CO line. The tips of these wings are marked in dark gray in Fig. [6](#fig:Hen_highVel). Integrating the line emission over this spectral region reveals emission regions with peaks offset from the continuum peak emission by $\sim 1.0\ensuremath{''}$ and $\sim 1.1\ensuremath{''}$ for the blue-shifted and red-shifted components, respectively.

The peak of the emission in the $^{13}$CO $J$=2$-$1  line ($\sim 0.9$ Jy) is comparable to the single-dish measurements of $\sim 0.7$ Jy (cite: Bujarrabal2001). The flux density was again calculated using historic values for the efficiencies of the IRAM 30m telescope. The difference is most likely due to the uncertainty in flux calibration of the single-dish data and implies that no flux is lost in the ALMA data we present.

At larger scales (up to $\sim 8\ensuremath{''}$ from the central source), we find an even weaker component of the $^{13}$CO line, which is marked in intermediate-dark and light gray in Fig. [6](#fig:Hen_highVel). To maximize the signal-to-noise of the high-velocity spectral features, we extracted spectra using a rectangular aperture of $3.5\ensuremath{''} \times 17\ensuremath{''}$ and oriented along the high-velocity-emission direction (Fig. [6](#fig:Hen_highVel)). This emission appears at more extreme projected velocities up to $\sim 240$ km s$^{-1}$ from the $\upsilon_{\rm LSR}$. Integrating over the intermediate-dark spectral regions reveals two emission regions with peak emission offset from the continuum peak by $\sim 4\ensuremath{''}$ for the blue- and red-shifted components. Emission at the extreme-velocity component (marked in light gray), at projected velocities $\sim 240$ km s$^{-1}$ from the $\upsilon_{\rm LSR}$, are produced still farther away. Hence, there is a positive velocity gradient in this high-velocity, point-symmetric molecular emission. To our knowledge, this is the first time these components with projected expansion velocities $> 50$ km/s have been detected towards Hen 3-1475 in observations of molecular lines. Previous observations recovered only the central component of the line with projected velocities up to $\sim 50$ km s$^{-1}$ from the $\upsilon_{\rm LSR}$ (cite: Bujarrabal2001; Huggins2004).

Interestingly, two different orientation directions can be identified in the high-velocity outflow. The inner, lower-velocity emission component displays a position angle relative to the north direction of $\sim -70^\circ$, while the outer, higher-velocity components display a position angle of $\sim -45^\circ$. In both cases, point symmetry about the continuum peak is observed.

## M1-92 (IRAS 19343+2926, Minkowski’s Footprint)

The continuum image and the profiles of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines extracted towards M1-92 using a region equal to the 3-$\sigma$ contour of the $^{13}$CO $J$=2$-$1  line are shown in Fig. [7](#fig:M1-92_highVel). The fluxes of the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O integrated over the same region are given in Table [\[tab:meas\]](#tab:meas).

![image](Fig_M1-92_HighVel.pdf) ![image](Fig_spectrum_M1-92.pdf)

### Continuum

The continuum emission shows a complex morphology with many different components. In light of this, we did not fit a Gaussian source to the continuum maps. We obtain an integrated flux density of $130 \pm 13$ mJy by integrating the emission over the 3-$\sigma$ emission contour of the $^{13}$CO $J$=2$-$1  line. This is very similar to the value of $127 \pm 13$ mJy obtained from integrating the emission over a circular region with diameter of 12$''$. The observed value agrees within uncertainties with previous single-dish measurements (cite: SanchezContreras1998; SanchezContreras2017). Hence, no loss of flux is caused by the relatively large extent of the continuum emission.

### Line emission

The line peaks indicate a systemic velocity of $\sim 2$ km s$^{-1}$. The lines are about 85 km s$^{-1}$ broad and tentatively display two main components, a central one spanning a range of velocities $|\upsilon -  \upsilon_{\rm LRS}| \lesssim 10~{\rm km}$ s$^{-1}$ which appears on top of the broader emission. The central component appears stronger relative to the broader component in the $^{13}$CO line than in those of the rarer isotopologues. However, the distinction between the two components is not very clear, and might not reflect two distinct physical velocity structures.

Integrating the high-velocity end of the line profiles reveals two emission regions which peak just outside of the region from where the continuum arises, and in the same region as extensions are observed in the continuum emission.

# Analysis

Based on the observed angular sizes of the emission regions and the strengths of the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O listed in Table [\[tab:meas\]](#tab:meas), we derive linear sizes of the C$^{18}$O emission region based on the assumed distances ($\Delta D_{3\sigma}^{\rm C^{18}O}$), $^{17}$O/$^{18}$O ratios, circumstellar masses ($M_{\rm gas}$), recent mass-loss rates ($\dot{M}$), and $^{13}$CO abundances ($f^{\rm ^{13}CO}$). Based on the $^{17}$O/$^{18}$O ratios we obtain, we infer initial masses using the MONASH ($M^{\rm KL16}_{\rm init}$) and FRUITY ($M^{\rm FRUITY}_{\rm init}$) models, maximum luminosities using the evolutionary models of (cite: MillerBertolami2016) ($L_{\rm PAGB}$), and maximum distances given these luminosities ($d_{\rm max}$). These derived quantities are given in Table [\[tab:isot\]](#tab:isot). For these calculations, we assume optically thin emission and an excitation temperature, $T_{\rm exc}$, of 10 K for all three isotopologues of CO. The value of the excitation temperature is motivated by the low values usually observed towards post-AGB stars with high molecular content (cite: Bujarrabal2001).

For the calculation of the $^{17}$O/$^{18}$O ratios, total circumstellar masses and $^{13}$CO abundances, we used the line fluxes extracted from the regions enclosing the 3-$\sigma$ contour of the $^{13}$CO $J$=2$-$1  moment-zero maps for each source as discussed above. The line fluxes obtained from these regions are referred to as $S^{\rm ^{13}CO}$, $S^{\rm C^{17}O}$, and $S^{\rm C^{18}O}$. For the calculation of the mass-loss rates at the end of the AGB ($\dot{M}$), we measure the C$^{18}$O $J$=2$-$1  line fluxes extracted from smaller regions defined by the 3-$\sigma$ contours of the C$^{18}$O $J$=2$-$1  line (Fig. [11](#fig:C18O)), with sizes $\Delta \theta_{3\sigma}^{\rm C^{18}O}$ (Table [\[tab:meas\]](#tab:meas)).

|  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $S^{\rm ^{13}CO}$ | $S^{\rm C^{17}O}$ | $S^{\rm C^{18}O}$ | $S_{3\sigma}^{\rm C^{18}O}$ | $\Delta \theta_{3\sigma}^{\rm C^{18}O}$ | $\Delta\upsilon^{\rm C^{18}O}$ |  |  |
|  | \[Jy km s$^{-1}$\] | \[Jy km s$^{-1}$\] | \[Jy km s$^{-1}$\] | \[Jy km s$^{-1}$\] | \[$\ensuremath{''}$\] | \[km s$^{-1}$\] |  |  |
| GLMP 950 | 15.3 (1.6) | 1.9 (0.3) | 1.13 (0.15) | 1.03 (0.14) | $2.4 \times 2.4$ | 41 |  |  |
| GLMP 953 | 23.3 (2.5) | 2.7 (0.3) | 2.1 (0.3) | 1.9 (0.3) | $3.0\times2.5$ | 37 |  |  |
| AFGL 5385 | 49 (5) | 2.3 (0.4) | 3.6 (0.5) | 3.8 (0.5) | $4.2\times3.5$ | 45 |  |  |
| HD 187885 | 64 (7) | 1.5 (0.3) | 2.4 (0.3) | 2.2 (0.3) | $3.2\times3.2$ | 61 |  |  |
| Hen 3-1475 | 39 (4) | 2.8 (0.3) | 2.2 (0.3) | 1.7 (0.3) | $2.8\times2.4$ | 100 |  |  |
| M1-92 | 210 (20) | 16 (2) | 8.9 (1.3) | 7.6 (1.3) | $8.6 \times 4.4$ | 89 |  |  |

Table notes: The uncertainties shown here include those from flux-calibration, which were not considered when calculating line-ratio uncertainties.

## $^{17}$O/$^{18}$O isotopic ratios

We use the observed fluxes of the $J$=2$-$1  lines of C$^{17}$O and C$^{18}$O to infer the $^{17}$O/$^{18}$O ratio. For this, we assume that the $^{17}$O/$^{18}$O isotopic ratio is equal to the C$^{17}$O/C$^{18}$O abundance ratio. Given the low value assumed for the excitation temperature (10 K) and the slightly different energy levels of C$^{17}$O and C$^{18}$O, the fractions of molecules in the $J=2$ level differ between the two isotopologues. Considering the excitation effects and the different Einstein-$A$ coefficients and central frequencies of the lines ($\nu_\circ$), the $^{17}$O/$^{18}$O ratio can be derived from the line flux ratio using $$\begin{equation*}
\frac{^{17}\rm O}{^{18}\rm O}= \frac{S^{\rm C^{17}O}_{J=2-1}} {S^{\rm C^{18}O}_{J=2-1}} \frac{[A \nu_\circ]_{J=2-1}^{\rm C^{18}O}}{[A \nu_\circ]_{J=2-1}^{\rm C^{17}O}} 
\frac{Q^{\rm C^{17}O}}{Q^{\rm C^{18}O}} e^{(E^{\rm C^{17}O}_{J=2}-E^{\rm C^{18}O}_{J=2})/kT_{\rm exc}} \approx 0.95 \frac{S^{\rm C^{17}O}_{J=2-1}} {S^{\rm C^{18}O}_{J=2-1}}
\\
\end{equation*}$$ where $S$, $Q$, $E$, and $k$ are the frequency-integrated line flux density, the partition function, the energy of the upper state, and the Boltzmann constant, respectively. The small difference between the energies of the $J=2$ levels of C$^{17}$O and C$^{18}$O implies that assuming an excitation temperature of 40 K instead of 10 K causes the derived abundance ratio to be only $\sim 3\%$ lower for a given observed line ratio. Hence, the isotopic ratios we obtain are virtually independent of the assumed excitation temperature as long as the excitation of both molecules share the same value. The derived isotopic ratios are given in Table [\[tab:isot\]](#tab:isot).

## Circumstellar gas masses, recent mass-loss rates, and $^{13}$CO abundances

The molecular abundance with respect to hydrogen is a critical parameter required to derive the hydrogen gas masses in the CSEs from observed molecular lines. Since the abundances of the CO isotopologues at the end of the AGB vary significantly as a function of stellar mass, we selected the isotopologue with the smallest expected change for this calculation, C$^{18}$O. For stars with initial masses between 1 and 4 $M_\odot$, the final $^{18}$O abundance is at most $\sim 30\%$ lower than the initial value for the models of (cite: Karakas2016), with more massive stars reaching larger differences than lower-mass ones. For comparison, the final $^{13}$C and $^{17}$O abundance can vary by an order of magnitude or more from the initial value. For the circumstellar mass calculations, we assume an average value of the $^{18}$O (and C$^{18}$O) abundance, $f^{\rm C^{18}O}$, of $8.5 \times 10^{-7}$ relative to the number of hydrogen nuclei (cite: Karakas2016), which is based on an initial solar abundance of $\sim 1.1\times 10^{-6}$. For HD 187885, which has been determined to have a lower metallicity ($Z=0.0035$), we adopt an abundance of $2.1 \times 10^{-7}$, also based on the models presented by (cite: Karakas2016). The total circumstellar gas mass is calculated using the following expression $$\begin{equation}
\label{eq:Mgas}
M_{\rm gas} = \frac{M_{\rm H}}{0.7} = \frac{1}{0.7}\frac{4~\pi~d^2~Q^{\rm C^{18}O}~m_{\rm H}}{g_{J=2}~A~h~\nu_\circ~f^{\rm C^{18}O}} e^{\frac{E_{J=2}}{T_{\rm exc}}}~S^{\rm C^{18}O},
\end{equation}$$ where $d$ is the distance to the source, $g_{J=2}$ is the statistical weight of the $J=2$ level, and $M_{\rm H}$ and $m_{\rm H}$ are the total hydrogen mass and the mass of a hydrogen atom, respectively. The factor 0.7 corresponds to the approximate fraction of the total mass accounted for by hydrogen at the end of the AGB (cite: Karakas2016). The derived circumstellar gas masses are given in Table [\[tab:isot\]](#tab:isot).

The recent mass-loss rates are determined using Eq. [\[eq:Mgas\]](#eq:Mgas) with $S^{\rm C^{18}O}$ replaced by $S^{\rm C^{18}O}_{3\sigma}$. This approach is chosen because most of the C$^{18}$O $J$=2$-$1  emission is produced in smaller regions (Fig. [11](#fig:C18O)), than those defined by the 3-$\sigma$ $^{13}$CO $J$=2$-$1  contours (Fig. [9](#fig:13CO)). The kinematic ages ($\Delta t$) of the C$^{18}$O $J$=2$-$1  emission regions are also determined using the 3-$\sigma$ C$^{18}$O $J$=2$-$1  contours. The line widths used for the calculation of the kinematic ages of the C$^{18}$O $J$=2$-$1  emission regions correspond to the widths of the C$^{18}$O $J$=2$-$1  line profiles at zero intensity. Using the derived expansion velocity, the size of the emission region and the adopted distances, we determined kinematic ages of the C$^{18}$O $J=2-1$ emission ($\Delta t$). Based on these ages and on the gas masses within the 3-$\sigma$ C$^{18}$O $J$=2$-$1  regions, we determine a recent mass-loss rate for each source. These mass-loss rates represent lower limits to the maximum mass-loss rates experienced by each source recently, because the phase of high AGB mass loss probably ceased even hundreds of years ago for some sources (see Section [6.4](#sec:disc_mdot)).

Using an analogous expression to Eq. [\[eq:Mgas\]](#eq:Mgas), we also derive the $^{13}$CO abundance relative to hydrogen nuclei ($f^{\rm ^{13}CO}$) that would make the estimated gas masses consistent with those derived based on the C$^{18}$O $J$=2$-$1  line. Although we assume optically thin emission, optical depth effects seem to affect the $^{13}$CO emission to some extent because for all sources the brightness temperatures observed towards the peak of the integrated emission reach values (between 7 and 13 K) comparable to the excitation temperature we assume. If our assumed excitation temperature is correct, this implies optical depths $\gtrsim 1$. Nonetheless, the relatively high values of the $^{13}$CO abundances we derive (see below) suggest that the optical depth effects are not very strong.

# Discussion

## Isotopic ratios

The $^{17}$O/$^{18}$O isotopic ratios allow us to estimate the initial masses of the sample stars using results from stellar evolution models. These are powerful constraints for understanding the properties and evolution of these sources, and allow us to infer stellar luminosities and distances and investigate whether the sources with known spectral types have evolved within the expected timescales.

### Comparison to other sources

To put the values of the $^{17}$O/$^{18}$O ratios determined for the sample stars in context, we compare them to those available in the literature for AGB stars using the sample of C-rich AGB stars studied by (cite: Abia2017), with a total of 29 objects, and the samples of O-rich AGB stars studied by (cite: Hinkle2016) and (cite: Lebzelter2019), which include a total of 80 sources.

The minimum and maximum values reported by (cite: Abia2017) for C-rich sources are $\sim 0.5$ and $\sim 2.5$. Only three sources ($\sim 10\%$) display ratios $\lesssim 0.6$. Hence, the values we obtain for AFGL 5385 (0.61) and HD 187885 (0.59) do occur in AGB stars as well, but are relatively rare. The values we report for GLMP 950 and GLMP 953 are very typical for C-rich AGB stars based on the sample of (cite: Abia2017). The value of the $^{17}$O/$^{18}$O ratio is not expected to change during the AGB or post-AGB for stars that become rich in carbon and do not experience HBB. Hence, comparing the values for post-AGB and AGB C-rich stars is meaningful. Nonetheless, we note that a direct comparison of the observed distributions is not straight-forward, because the duration of the carbon-rich phase in the AGB and that of the post-AGB phase depend strongly on initial mass and metallicity.

The $^{17}$O/$^{18}$O ratios reported by (cite: Hinkle2016) and (cite: Lebzelter2019) for O-rich AGB stars cover a broad range of values, from $\sim 0.05$ to $\sim 16$. Nonetheless, extreme values are relatively rare, with only $\sim 11\%$ having ratios lower than 0.2 and $\sim 11\%$ having values larger than 2. Hence, the values we obtain for Hen 3-1475 (1.29) and M1-92 (1.8) are typical for O-rich AGB stars. However, we emphasize that these ratios were determined at different points during the AGB for each source, and at least some of the O-rich stars studied by (cite: Hinkle2016) and (cite: Lebzelter2019) will become C-rich or experience HBB before entering the post-AGB phase.

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | $\Delta D_{3\sigma \ensuremath{^{\dag}}}^{\rm C{18}O}$ | $M_{\rm gas}\ensuremath{^{\ddag}}$ | $f^{^{13}\rm CO}$ | $\Delta t$ | $\dot{M}$ | $^{17}$O/$^{18}$O | $M^{\rm KL16}_{\rm init}$ | $M^{\rm FRUITY}_{\rm init}$ | $L_{\rm PAGB}$ | $d_{\rm max}$ |
|  | \[au\] | \[$M_\odot$\] | \[$\times10^{-5}$\] | \[yr\] | \[$M_\odot~{\rm yr}^{-1}$\] |  | \[$M_\odot$\] | \[$M_\odot$\] | \[$10^3~L_\odot$\] | \[kpc\] |
| GLMP 950 | 9360 | 0.10 | 1.1 | 1085 | $\phantom{1.}8\times10^{-5}$ | 1.7 (0.2) | 1.8 | $\phantom{<~} 1.8$ | $\phantom{\sim~} 6.9$ | $\phantom{\sim~} 4.2$ |
| GLMP 953 | 11400 | 0.17 | 0.9 | 1460 | $1.1\times10^{-4}$ | 1.3 (0.2) | 1.7 | $\phantom{<~} 1.7$ | $\phantom{\sim~} 6.7$ | $\phantom{\sim~} 4.0$ |
| AFGL 5385 | 14280 | 0.24 | 1.1$^{$\ast$}$ | 1510 | $1.7\times10^{-4}$ | 0.61 (0.10) | 1.4 | $\phantom{<~} 1.5$ | $\phantom{\sim~} 5.9$ | $\phantom{\sim~} 2.4$ |
| HD 187885$^ \dag$ | 8000 | 0.35 | $\phantom{^\star}$0.55$^{$\ast$}$ | 620 | $\phantom{1.}5\times10^{-4}$ | 0.59 (0.12) | $1.15$ | $< 1.3$ | $\sim 6.2$ | $\sim 2.5$ |
| Hen 3-1475 | 16240 | 0.42 | 1.5 | 770 | $\phantom{1.}4\times10^{-4}$ | 1.29 (0.15) | 1.7 | $\phantom{<~} 1.7$ | $\phantom{\sim~} 6.7$ | $\phantom{\sim~} 4.5$ |
| M1-92 | 22360 | 0.35 | 2.0 | 1190 | $2.5\times10^{-4}$ | 1.8 (0.2) | 1.8 | $\phantom{<~} 1.8$ | $\phantom{\sim~} 6.9$ | $\phantom{\sim~} 2.8$ |

Table notes:

Observations of isotopic ratios in post-AGB stars are much rarer, and to our knowledge only six C-rich and ten O-rich sources have had $^{17}$O/$^{18}$O ratios determined thus far (cite: Khouri2022; GallardoCava2022). These samples are also heavily biased by observations of specific subgroups of post-AGB stars, such as the eight O-rich water fountain sources studied by (cite: Khouri2022). The observed values range roughly from 0.3 to 4 for C-rich objects and from 0.2 to 6 for O-rich ones. Hence, the values reported by us are within the observed ranges.

### Derived initial masses

We compare the isotopic ratios derived in this work to stellar evolution models using the MONASH code (cite: Karakas2016; Karakas2018) and the FRUITY database (cite: Cristallo2015). These models assume a solar-like composition scaled to different metallicities. While there is no strong disagreement between the predictions of the models regarding the first dredge up, which has the dominant effect on the oxygen isotopic ratios for stars with initial masses $\lesssim 4$ $M_\odot$, the effects of the third dredge up are much more uncertain (cite: Palmerini2021). The uncertain aspects relative to the third dredge-up relevant for the analysis presented here concern the mass ranges for which stars become carbon rich and for which HBB destroys $^{18}$O in the stellar envelope efficiently.

The observed isotopic ratios imply remarkably similar initial masses for a given metallicity for the two models. The derived values are given in Table [\[tab:isot\]](#tab:isot) for solar metallicity, with the exception of HD 187885 for which we consider a metallicity $Z=0.0035$ (cite: vanWinckel2000). M1-92 is the only object with a previous determination of the $^{17}$O/$^{18}$O ratio. Our value of $1.8\pm0.1$ is in agreement within uncertainties with the value reported in the literature (cite: Alcolea2022). The value that we obtain implies an initial mass $\sim 1.8~M_\odot$ for solar composition, similar to the value obtained by (cite: Alcolea2022), $\sim 1.7~M_\odot$.

While the MONASH and FRUITY models with the exact metallicity of HD 187885 (\[Fe/H\] = -0.6, or $Z=0.0035$) are not available in the literature, we can conclude that the predicted trends in the $^{17}$O/$^{18}$O ratio with metallicity imply an initial mass smaller than $<1.3~M_\odot$ in both cases. In the case of the MONASH code, the predicted $^{17}$O/$^{18}$O ratios imply an initial mass of $\sim 1.15~M_\odot$ for $Z=0.0028$ (cite: Karakas2018), which is the closest metallicity to that of HD 187885 for which the models have been calculated. For the FRUITY database, the models with lowest initial mass available ($1.3~M_\odot$) predict larger $^{17}$O/$^{18}$O values for both $Z=0.003$ and $Z=0.006$, and the predicted value decreases with decreasing initial mass in this range. The relatively low mass and carbon-rich nature of this source is in agreement with the findings from (cite: Karakas2018), which imply that stars with masses as low as 1.15 $M_\odot$ become rich in carbon by the end of the AGB for $Z=0.0028$. Hence, the initial mass of HD 187885 seems to be very close to the minimum mass required for becoming a carbon star given its initial metallicity. We note that the models of (cite: Karakas2018) assume initial isotopic ratios equal to solar even at lower metallicities, which might not be representative of the initial isotopic ratios of HD 187885. Our results imply initial masses for GLMP 950 and GLMP 953 (1.8 and 1.7 $M_\odot$, respectively) within the range usually attributed to carbon stars.

Interestingly, the derived initial masses for Hen 3-1475 and M1-92 also fall in the range expected for stars to become carbon rich. The fact that these sources are observed to still be oxygen rich in the post-AGB phase might be explained by an interrupted evolution, for instance with the envelope being ejected by interactions with a close companion (cite: Khouri2022; Alcolea2022). Alternatively, these sources might have an initial metallicity higher than solar and initial masses between 2.0 to 2.4 $M_\odot$. In this scenario, their O-rich nature could be consistent with stellar evolution models, which remain oxygen rich up to initial masses $\sim 2.4~M_\odot$ at higher metallicity (e.g. $Z=0.03$).

Despite the encouraging agreement between the two evolutionary models considered for the interpretation of the derived $^{17}$O/$^{18}$O ratios, we note that the initial masses we derive are fairly uncertain both because of uncertainties in the model calculations and in the initial composition of these sources. More robust results can be obtained using larger statistical samples.

### Implications for luminosities and distances

The initial masses we derive are relatively low, and set limits on the maximum luminosities reached by each star. To assess how these limits compare to our assumptions, we determine the maximum expected post-AGB luminosity for each source from evolutionary models presented by (cite: MillerBertolami2016) given the inferred initial masses. Using these luminosities (presented in Table [\[tab:isot\]](#tab:isot)), we scaled the distance for each sources based on the luminosities adopted from the literature (Table [\[tab:cont\]](#tab:cont)). These distances are also given in Table [\[tab:isot\]](#tab:isot). The distances for GLMP 950, GLMP 953, HD 187885, and M1-92 are consistent with those adopted from the literature with differences $< 10\%$, while those for AFGL 5385 and Hen 3-1475 show larger discrepancies of 30% and 22%, respectively. Nonetheless, considering the uncertainties in the derived initial masses and on the determination of distances, the overall agreement is good. We note that distances up to 8.3 kpc have been reported for Hen 3-1475 (cite: Borkowski2001). Our results indicate that such large distances are not realistic. (cite: Riera2003) derived a distance of 5.8 kpc based on improved measurements of radial velocities and proper motions of the jet features. Our results suggest an even smaller distance which, based on the discussion in (cite: Riera2003), implies a larger value $(\gtrsim 55^\circ)$ for the inclination angle of the jet than what is assumed in their calculations ($50^\circ$).

### Implications for post-AGB lifetimes

Given the definition of the beginning of the post-AGB as when the mass of the envelope becomes 0.01 times the present-day mass of the given star (cite: MillerBertolami2016), the large circumstellar masses we derive imply that these sources must have been on the AGB when the high-mass-loss phase started. Hence, the kinematic ages given in Table [\[tab:isot\]](#tab:isot) represent an upper limit for the duration of the post-AGB evolution of these sources up to now. Using the spectral types available in the literature for four of the sources (AFGL 5385, HD 187885, Hen 3-1475, and M1-92, see Table [\[tab:cont\]](#tab:cont)) we are able to compare the time these objects took to transition between the end of the AGB and their present position in the Hertzsprung–Russell (HR) diagram with predictions from evolutionary models.

Relatively large uncertainties are associated with the timescales predicted by stellar evolution models mostly because of the unknown evolution of the mass-loss rate in the post-AGB phase. This is particularly critical in the beginning of the post-AGB, because stellar temperatures are still relatively low in this phase and AGB-like mass loss can still take place (cite: MillerBertolami2016). (cite: MillerBertolami2016) divides the evolution during the post-AGB phase in two stages, the early and late post-AGB, with associated timescales $\tau_{\rm tr}$ and $\tau_{\rm cross}$, respectively. The final point of the post-AGB evolution is defined when the maximum effective temperature is reached, which corresponds to $T_{\rm eff} > 10^5$ K in all models presented by (cite: MillerBertolami2016).

Since the changes experienced by the stars are gradual, definitions of transition points are to a large extent arbitrary. Nonetheless, the general trend is that model stars move to the blue in the HR diagram as the envelope mass decreases. This change is slow at first and accelerates strongly as the envelope mass becomes lower. At the start of the post-AGB (envelope mass equal to 0.01 of present-day mass), the effective temperature of the model stars are relatively low ($\lesssim 4000$ K) for initial stellar mass between 1.2 and 2 $M_\odot$, as inferred from Fig. 8 in (cite: MillerBertolami2016). The point of transition between early and late post-AGB phase is set by (cite: MillerBertolami2016) to be log($T_{\rm eff}$) = 3.85 ($T_{\rm eff} \sim 7080$ K). Since the change in temperature as a function of time is fast in the late post-AGB, the definition of this transition point is of relative little consequence for the derived timescales according to the author, as long as the temperatures are relatively low but high enough to prevent AGB-like outflows.

AFGL 5385, HD 187885, Hen 3-1475, and M1-92 have effective temperatures ranging between $\sim 6800$ K and $\sim 30000$ K based on their spectral types (Table [\[tab:cont\]](#tab:cont)). Hence, they have evolved significantly beyond what would be considered the start of the post-AGB phase. Moreover, only the source with the lowest effective temperature (AFGL 5385) would be classified as an early post-AGB source, but even this object is relatively close to transitioning into the late post-AGB in which a rapid evolution of the effective temperature takes place.

By comparing the predicted times for stars to evolve from the beginning of the post-AGB to effective temperatures $\sim 7000$ K ($\tau_{\rm tr}$) to the kinematic ages of the C$^{18}$O $J=2-1$ emission, it is clear that these four sources had an evolution faster than predicted by models by a factor of a few, at least. By interpolating the values for $Z=0.02$ and $Z=0.01$ in Table 3 in (cite: MillerBertolami2016), we find that $\tau_{\rm tr}$ varies between $\sim 4400$ yr for 1.25 $M_\odot$ stars to $\sim 2370$ yr for 2.0 $M_\odot$ for solar metallicity ($Z=0.014$). At lower metallicities ($Z=0.001$), $\tau_{\rm tr}$ becomes shorter and varies between $\sim 3700$ yr and $\sim 1600$ yr for models with 1.15 and 2.0 $M_\odot$. AFGL 5385, HD 187885, Hen 3-1475, and M1-92 all seem to have reached their present position at least two times faster (and even faster in most cases) than expected. This particularly striking for M1-92 and Hen 3-1475 which have B-type central stars, with $T_{\rm eff} > 10000$ K, and kinematic ages $\lesssim 1000$ yr. HD 187885 also seems to have evolved more than five times faster than expected into the late post-AGB phase.

Previous models for post-AGB evolution presented by (cite: Vassiliadis1994) display on average a slower evolution between the end of the strong AGB-like mass loss and the less intense post-AGB one. However, the comparison between different stellar evolution models is not completely straight forward because of different definitions of transitions points. In contrast to (cite: MillerBertolami2016), (cite: Vassiliadis1994) define the beginning of the post-AGB phase as when the stellar temperature in the models increases by a factor of two from the value during the AGB. For solar composition, this results in stellar temperatures at the beginning of the post-AGB varying between $\sim 4500$ K and $\sim 4200$ K for star with initial masses between 1.5 and 2 M$_\odot$, respectively. From these starting points, the models reached stellar temperatures of $10^4$ K in $\gtrsim 8000$ yr for initial masses $\gtrsim 1.5~{\rm M}_\odot$. For a metallicity $Z=0.004$ comparable to that of HD 187885 ($Z=0.0035$) and an initial mass equal to 1 $M_\odot$, the evolution is shorter $\sim 6000$ yr from an initial post-AGB stellar temperature $\sim 5600$ K.

The timescales reported by (cite: Vassiliadis1994) are almost an order of magnitude larger than that inferred for the evolution of Hen 3-1475 and M1-92, which have evolved to stellar temperature larger than 10$^4$ K. A comparison to HD 187885 and AFGL 5385 is not as clear because these sources have stellar temperatures lower than 10$^4$ K, and the durations of shorter steps of evolution below this limit are not specified. According to the models, AFGL 5385 and HD 187885 should have had stellar temperatures at the beginning of the post-AGB phase of $\sim 4500$ K and $\sim 5600$ K, respectively. The evolution of AFGL 5385 to the present value of $\sim 7300$ K in 1500 yr seems to have happened faster than predicted considering that the source has experienced half the evolution to 10$^4$ K (expected to happen in $\sim 8600$ yr) and that the pace of evolution is slower at lower stellar temperatures. For HD 187885, the change in temperature to the present value of $\sim 6800$ K is relatively small, and we refrain from making a comparison that would require too many assumptions.

The fast evolution we infer with respect to those predicted by models discussed above might be caused by a different evolutionary path from the single-star evolution considered in the models. However, if at least some of these four sources evolved without the direct effect of a close companion, our results indicate that the central remnant warms up faster than expected. (cite: SanchezContreras2017) also suggested a faster evolution of the central source in the post-AGB phase based on high mass-loss rates derived for a small sample of post-AGB sources.

## $^{13}$CO and C$^{18}$O abundances

For the stars assumed to have initial solar composition, we find $^{13}$CO abundances between $0.9\times 10^{-5}$ and $2.0\times 10^{-5}$ with respect to the total number density of hydrogen atoms (including atomic and molecular sources). We find the largest values of 1.5 and $2.0\times10^{-5}$ for Hen 3-1475 and M1-92, which are oxygen-rich sources. This fits the expectation that the abundance of $^{13}$C is larger in O-rich stars, but the values are 1.5 and 2 times larger than often assumed for post-AGB stars with solar-like elemental abundances and high molecular content, $\sim 1\times10^{-5}$ (cite: Bujarrabal2001; Bujarrabal2017). The values for C-rich sources with assumed solar metallicity are lower with respect to the O-rich ones, but the values for these five sources differ only by roughly a factor of two. The relatively high abundances of $^{13}$C we find are somewhat surprising because optical depth effects are expected to affect the $^{13}$CO lines more strongly than the C$^{18}$O ones, which should lead to lower inferred values for the $^{13}$CO abundances than the real ones. From this, it seems that optical depth effects are at most mild in the $^{13}$CO lines.

If the C$^{18}$O envelope is much smaller than the $^{13}$CO because of more efficient dissociation, we would overestimate the $^{13}$CO abundances. To examine this possibility, we compared the ratio between intensities of the $^{13}$CO and C$^{18}$O $J=2-1$ lines in the central beam of the maps to the same ratio between the line fluxes given in Table [\[tab:meas\]](#tab:meas), which are integrated over larger apertures. We find larger ratios for all sources when larger apertures are used, implying that the C$^{18}$O emission is more centrally peaked than the that of $^{13}$CO. This could be caused by the $^{13}$CO emission being either optically thick in the central beam or more extended than that of C$^{18}$O. Nonetheless, compared to the ratios from $^{13}$CO $J$=2$-$1  3-$\sigma$ regions, those measured from the central beams are only between 15 and 20% smaller for GLMP 950, GLMP 953, HD 187885, and M1-92, and 30% smaller for AFGL 5385 and Hen 3-1475. Furthermore, the different sizes of the 3-$\sigma$ contours of the $J$=2$-$1emission of $^{13}$CO and C$^{18}$O are consistent with the lower signal-to-noise in the maps of the C$^{18}$O lines. Based on these considerations, we conclude that, if present, the effect of different dissociation radii on the line ratios seems to be relatively small, and the $^{13}$CO abundance seems to be indeed relatively high in these sources.

Interestingly, the three C-rich sources with assumed solar metallicity display $^{13}$CO/C$^{18}$O ratios between 10 and 13, while the C-rich source with lower metallicity (HD 187885) shows a value of $\sim 26$, which is even larger than the values of 18 (Hen 3-1475) and 24 (M1-92) determined for the two O-rich sources. This might be caused by the chemical composition of HD 187885 not having been as strongly affected by the third dredge-up as those of the other C-rich sources, given the relatively low value of its C/O ratio $\sim 1$ (cite: vanWinckel1996; vanWinckel2000).

## Circumstellar gas masses

### Uncertainties

The uncertainties on the circumstellar masses determined by us arise from uncertainties on the excitation temperature, the distance, and the C$^{18}$O abundance. The circumstellar masses depend on the assumed excitation temperature in a non-linear manner. Increasing the excitation temperature from 10 K to 20 K causes the derived masses to decrease by approximately 20%, while increasing it from 10 K to 40 K causes the derived masses to increase by about 10%. Hence, we estimate the uncertainty on the excitation temperature translates to an uncertainty of at most $\sim 20\%$ on the derived circumstellar gas masses. The circumstellar masses are proportional to the square of the adopted distance, which we assume to be uncertain by 30%. Considering the uncertainty of 30% from $^{18}$O abundance variation (Section [5.2](#sec:mdot)), we find the circumstellar masses to be uncertain by a factor of 1.7. This does not account for uncertainties regarding the initial metallicity or, more specifically, the initial $^{18}$O abundance.

### Comparison to the literature

The derived circumstellar gas masses correspond to a substantial fraction of the initial stellar mass of each source, given the initial masses $< 2~M_\odot$. These values are on the high end when compared to those observed in a sample of 21  post-AGB stars, pre-PN and PN, for which circumstellar masses between $\sim 10^{-2}$ and 1 $M_\odot$ were inferred (cite: SanchezContreras2012).

(cite: Oppenheimer2005) modelled the spectral energy distribution of AFGL 5385 and derived a dust mass-loss rate of $\sim 10^{-6}~M_\odot~{\rm yr}^{-1}$. This is somewhat high compared to gas mass-loss rate of $1.7 \times 10^{-4}~M_\odot~{\rm yr}^{-1}$ derived by us, and would imply a gas-to-dust ratio of 170. This relatively low value implies substantial depletion of refractory elements, but is comparable to values $\sim 200$ determined for AGB stars with large mass-loss rates $\gtrsim 10^{-5}~M_\odot~{\rm yr}^{-1}$ (cite: Blommaert2018; Olofsson2022). The outer radius derived from their model implied a timescale for building up the envelope larger than 2000 yr for an assumed expansion velocity of 15 km s$^{-1}$. The expansion velocity we find using the C$^{18}$O $J$=2$-$1  line (22.5 km s$^{-1}$) would imply a timescale for the dust envelope larger than 1300 yr, which is consistent with the kinematic ages of the C$^{18}$O $J$=2$-$1  emission, $\sim 1500$ yr.

The total circumstellar masses derived by (cite: Bujarrabal2001) of $\sim 2.6 \times 10^{-2}~M_\odot$ and 0.63 $M_\odot$ for HD 187885 and Hen 3-1475, respectively, can be compared to the values we find by using the distances assumed by them (1 kpc for HD 187885 and 5 kpc for Hen 3-1475). We find a circumstellar mass of $6 \times 10^{-2}$ and 0.32 $M_\odot$, for HD 187885 and Hen 3-1475, respectively. The discrepancy is mostly explained by the different value of the $^{13}$CO abundance relative to hydrogen adopted by (cite: Bujarrabal2001), $1\times10^{-5}$, compared to that derived by us, $1.5\times10^{-5}$ and $0.55\times10^{-5}$ for Hen 3-1475 and HD 187885, respectively.

A significantly larger circumstellar gas mass ($\sim 1~M_\odot$) has been determined for M1-92 (cite: Alcolea2022) than what we find ($0.35~M_\odot$). This can also be mostly explained by a difference between the $^{13}$CO abundance assumed by (cite: Alcolea2022) ($1\times10^{-5}$) and that determined by us ($2\times10^{-5}$). (cite: Li2024) also find a circumstellar mass $\sim 1~M_\odot$ based on observations of optical scattered light and an assumed gas-to-dust ratio of 200. The lower circumstellar gas mass we find would imply a lower gas-to-dust ratio $\sim 70$, which is quite low even if full condensation of refractory elements is considered.

## Recent mass-loss rates

The mass-loss rates we derive $\sim 10^{-4}$ M$_\odot$ yr$^{-1}$ are roughly an order of magnitude higher than the peak values achieved by stars with initial masses between 1 and 2 M$_\odot$ ($\sim 10^{-5}$ M$_\odot$ yr$^{-1}$) in commonly used mass-loss-rate prescriptions (cite: Vassiliadis1993). Nonetheless, our calculations might even underestimate the actual peak mass-loss rates experienced by these sources. For instance, the inner radius of the envelope of HD 187885 observed by (cite: Lagadec2011), of 0.4$''$, implies a timescale for the cessation of mass loss $\sim 160$ yr ago assuming the same expansion velocity we use, $\sim 30$ km s$^{-1}$. This is only four times smaller than kinematic age of the C$^{18}$O $J$=2$-$1  derived by us. The dust model calculated by (cite: Oppenheimer2005) for AFGL 5385 also implies a cessation of the high-mass-loss-rate phase $\sim 300$ years ago (at the distance of 3.4 kpc considered by us). Hence, these non-negligible times since copious mass loss has ceased imply lower times spent in the phase of large mass-loss rates than given in Table [\[tab:isot\]](#tab:isot), indicating that the maximum instantaneous mass-loss rates experienced by these sources are even larger than the average values we report.

We also note that the derived timescales pertain to the region traced by the $J$=2$-$1  line of the observed isotopologues. If the size of the emission region is being determined by dissociation or excitation of the $J=2$ levels, rather than by the onset of the high-mass-loss-rate phase, the timescales and circumstellar masses we infer will be lower than those experienced by the sources. Nonetheless, the obtained mass-loss rates are independent of whether the high-mass-loss-rate phase has been ongoing for longer than listed in Table [\[tab:isot\]](#tab:isot).

## Progenitor sources

One interesting question is whether the oxygen-rich stars in our sample could be an evolved stage of water fountain sources. The inferred kinematic ages for the C$^{18}$O $J=2-1$ emission for M1-92 and Hen 3-1475 ($\sim 1190$ and $\sim 770$ years, respectively) are a factor of at least four larger than typical ages for the envelopes of water fountains (cite: Khouri2022). When compared to average mass-loss rates derived for water fountains (cite: Khouri2022), the values we present here are lower. However, this mostly reflects the larger timescales since the creation of the envelopes. If the intense mass-loss process of M1-92 and Hen 3-1475 lasted $\lesssim 200$ years instead of the kinetic ages of the C$^{18}$O $J$=2$-$1  we determine, their mass-loss rates would have been $\sim 10^{-3}~M_\odot$ yr$^{-1}$, in the same range derived for water fountains. In fact, (cite: Alcolea2022) argues that it is not possible to exclude scenarios in which the whole envelope of M1-92 was created in a short mass-loss event. Moreover, the large excess momentum in the outflow compared to that provided by the radiation field in these two sources (cite: Bujarrabal2001) imply an acceleration mechanism that probably requires the action of a companion. (cite: Khouri2022) suggested water fountains to have experienced common-envelope evolution, and similar suggestions have been made for M1-92 (cite: Alcolea2022; Li2024) and Hen 3-1475 (cite: Borkowski2001). The redder colours of water fountains (see Fig. [1](#fig:colour-colour)) are most likely caused at least in part by their envelopes being more compact, with shorter timescales since the start of their high-mass-loss phase. Moreover, the high-velocity water masers, which are the distinguishing feature of water fountains, are only expected to be produced in the $\sim 200$ years that define the class. Whether M1-92 and Hen 3-1475 displayed such high-velocity masers several hundred years ago is possible but unknown.

Confirming that these classes of sources are associated is not straight-forward, but statistical studies that include more sources at different evolutionary stages and should reveal whether this scenario is in agreement with observations when taking into account the different relevant timescales. Moreover, hydrodynamical modeling of the evolution of water fountain systems should also indicate whether the evolution of spectral energy distributions and morphologies are consistent. Another interesting question that deserves further investigation is whether an evolutionary relationship exists between post-AGB stars with dusty discs (cite: vanWinckel2007) and the objects studies here and water fountains.

Regarding the carbon-rich stars, their expected too-low water abundances imply that water masers are not produced, which would prevent these sources from even being classified as water fountains. Nonetheless, their compact envelopes and high mass-loss rates suggests that sources like HD 187885, GLMP 950, GLMP 953, and AFGL 5385 might be carbon-rich stars that have taken the same evolutionary path as that associated with water-fountain sources, i.e., common-envelope evolution.

## High-velocity outflow of Hen 3-1475

As shown in Fig. [8](#fig:Hen3-1475_Hubble), the high-velocity molecular outflow observed in Hen 3-1475 is well aligned with the images of \[NII\] emission obtained with the *HST*. Interestingly, the molecular gas appears in the dark regions between the bright clumps. The clumps observed by the *HST* show no significant proper motion, which has been interpreted as an indication that these structures trace quasi-stationary shocks (cite: Fang2018).

![](Hen_3-1475_ALMA_Hubble.pdf)

The projected velocity of the $^{13}$CO emission increases with distance from the star up to $\sim 240$ km s$^{-1}$ at the emission clumps observed the farthest away from the star (at $\sim 5\ensuremath{''}$). The ionised gas displays velocities that also increase up to the same distance, but to a maximum of $\sim 600$ km s$^{-1}$ at $\sim 5\ensuremath{''}$. The ionised gas, then, decelerate outwards by $\sim 100$ km s$^{-1}$ up to $\sim 9\ensuremath{''}$ from the central source (cite: Bobrowsky1995). Hence, the velocity of the molecular gas is a factor of roughly two lower than that of the ionised gas at a similar distance from the star, indicating that most of the molecular material is entrained by a faster outflow.

The bright knot to the northeast has been detected in X-rays (cite: Sahai2003b). Strong emission of energetic radiation in the clumps of ionised gas could be the cause for the lack of molecular emission from them. It is also possible that molecules are destroyed by the shock, but form again after (part of) the gas cools in the post-shock region.

The oxygen isotopic ratio we determine implies that Hen 3-1475 is not a high-mass O-rich post-AGB star, as suggested in the literature (cite: Borkowski2001; Manteiga2011), but had a more typical initial mass for a post-AGB star ($\lesssim 2~M_\odot$). The interpretation of this object (and similar ones) as the product of binary interactions (cite: Borkowski2001) seems the most plausible option.

## Comparison between GLMP 950 and GLMP 953

GLMP 950 and GLMP 953 display many similarities, but also striking differences. For instance, while the fluxes of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines (Table [\[tab:meas\]](#tab:meas)) and the derived circumstellar masses (Table [\[tab:isot\]](#tab:isot)) differ by less than a factor of two between the two sources, the continuum emission measured at $\sim 1.3$ mm (Table [\[tab:cont\]](#tab:cont)) differs by more than a factor of twenty. GLMP 953 shows higher values in both line and continuum emission.

Another significant difference is that high-velocity emission ($\upsilon > 30$ km s$^{-1}$ from the systemic velocity) is observed towards GLMP 953, but not towards GLMP 950.

The large difference in continuum emission is puzzling, given the other similarities, the similar kinematic ages, initial masses, circumstellar gas masses and averaged mass-loss rates derived for the two sources. One possibility is that the emission from GLMP 953 at these wavelengths is mainly due to free-free rather than dust emission. However, the flux density of this source at 353 GHz of 0.32 Jy (cite: Eden2017) implies a spectral index between 353 and 228 GHz of $\sim 2.3$, which does not suggest strong free-free emission.

The number of detected lines is similar towards the two sources. However, on the one hand, we observe lines we assign to K$^{37}$Cl towards GLMP 953 (if confirmed, most likely produced in the inner and denser CSE), but not towards GLMP 950. On the other hand, a few unidentified lines are clearly detected towards GLMP 950, but not towards GLMP 953.

The cause of these differences is not obvious from the observations we report. While a different inclination could explain why we do not see high-velocity emission towards GLMP 950, it does not account for the much weaker continuum emission and the slightly different molecular spectra. A difference in C/O ratio could potentially explain the different chemistry and stronger continuum if it leads to the formation of more dust in GLMP 953, or of different types of dust between the two sources. Additionally, the high-velocity emission towards GLMP 953 hints at the presence of a companion in that system. If that is indeed the case, and the lack of high-velocity emission towards GLMP 950 indicates no companion is present, the observed differences might be all related to GLMP 953 being in a binary system and GLMP 950 not.

# Summary and conclusions

We observed the $J$=2$-$1  lines of $^{13}$CO, C$^{17}$O, and C$^{18}$O with ALMA towards a sample of six obscured post-AGB stars: four carbon-rich (GLMP 950, GLMP 953, AFGL 5385, and HD 187885) and two oxygen-rich sources (Hen 3-1475 and M1-92). Emission was detected and emission-region sizes were determined for all sources in the three lines and 1.3 mm continuum. The richness of the spectra varies strongly within the sample, with detection of emission lines assigned by us to NaCl, SiC$_2$, SiS, K$^{37}$Cl (tentative), and HC$_3$N towards the carbon-rich sources and SO, SO$_2$, and SiS towards the O-rich sources. The two sources with by far the largest number of detected lines (GLMP 950 and GLMP 953) have comparable strengths of the lines of CO isotopologues and similar luminosities, initial masses, and kinematic ages of the C$^{18}$O $J=2-1$ emission, but continuum emission at 238 GHz that differs by a factor of $\sim 20$.

All but one source (GLMP 950) show high-velocity emission in the form of low-intensity wings ($\upsilon \gtrsim 30$ km s$^{-1}$) in the $^{13}$CO $J=2-1$ line. The emission regions of these components show point-symmetric structure in all cases. The high-velocity molecular outflow of Hen 3-1475 was found to be particularly remarkable, with expansion velocities $> 200$ km s$^{-1}$ and emission regions that are interleaved with emission from hotter ionized gas observed by the *HST*. The lower velocities of the molecular gas with respect to the ionized gas at the same distance from the central source suggests that the molecules are entrained in the atomic outflow.

We inferred initial masses between 1.15 and 1.8 for the stars in our sample using the $^{17}$O/$^{18}$O isotopic ratio, which we derived based on the observed ratios of the C$^{17}$O and C$^{18}$O lines. We found high circumstellar masses (between $\sim 0.1$ and $\sim 0.42$ $M_\odot$) and low kinematic ages (ranging from $\sim 600$ to $\sim 1500$ yr) corresponding to the C$^{18}$O $J=2-1$ emission. Together, these values imply very large recent mass-loss rates ($\gtrsim 10^{-4}~M_\odot$ yr$^{-1}$). The high effective temperatures of AFGL 5385, HD 187885, Hen 3-1475, and M1-92 and the relatively short times since the phases of strong mass loss imply that the central sources have evolved faster than expected for single stars.

Our results highlight how our understanding of post-AGB stars can advance using ALMA observations of galactic sources and through a comprehensive study of their properties (circumstellar mass, kinematic ages, and isotopic ratios). The extent to which the population of obscured post-AGB stars are the product of single-star evolution or binary interactions remains open, but we confirmed that their characteristics are similar to those of water fountains, which are suggested to be the product of binary interactions. Moreover, the two O-rich sources M1-92 and Hen 3-1475 have remained rich in oxygen despite having initial masses in the range for which becoming carbon rich is expected. In conclusion, observations of this type of a larger sample of objects have the potential to substantially advance our understanding of post-AGB stars, of planetary nebulae, and of the end of the AGB.

# Acknowledgements

The authors thank the referee Eric Lagadec for his questions and suggestions which improved the quality of the manuscript. The authors thank Marcelo Miller Bertolami for helpful discussions regarding the interpretation of timescales for post-AGB evolution in his models. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.01259.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. T.K. acknowledges support from the Swedish Research Council through grants 2019-03777. JA, VB, CSC are partially supported by I+D+i project, PID2019-105203GB-C21/C22, funded by the Spanish MICIU/AEI/10.13039/501100011033. JFG is financially supported by grants PID2020-114461GB-I00, PID2023-146295NB-I00, and CEX2021-001131-S, funded by MCIN/AEI /10.13039/501100011033. L.V.-P. acknowledges support from the grant PID2020-117034RJ-I00 funded by the Spanish MCIN/AEI/10.13039/501100011033. R.S.’s contribution to the research described here was carried out at the Jet Propulsion Laboratory, California Institute of Technology, under a contract with NASA, and funded in part by NASA via multiple ADAP and HST GO awards. AK was supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. MS acknowledges support from the Research Council of Norway via ESGC project (project No. 335497).

101 natexlab

(ref: Abia2017) Abia, C., Hedrosa, R. P., Domı́nguez, I., & Straniero, O. 2017, A&A, 599, A39

(ref: Alcolea2022) Alcolea, J., Agúndez, M., Bujarrabal, V., et al. 2022, Galaxies, 10, 47

(ref: Alcolea2007) Alcolea, J., Neri, R., & Bujarrabal, V. 2007, A&A, 468, L41

(ref: Allen1976) Allen, D. A. & Swings, J. P. 1976, A&A, 47, 293

(ref: Blommaert2018) Blommaert, J. A. D. L., Groenewegen, M. A. T., Justtanont, K., & Decin, L. 2018, MNRAS, 479, 3545

(ref: Boboltz2007) Boboltz, D. A. & Marvel, K. B. 2007, ApJ, 665, 680

(ref: Bobrowsky1995) Bobrowsky, M., Zijlstra, A. A., Grebel, E. K., et al. 1995, ApJL, 446, L89

(ref: Boffin2019) Boffin, H. M. J. & Jones, D. 2019, The Importance of Binaries in the Formation and Evolution of Planetary Nebulae

(ref: Borkowski1997) Borkowski, K. J., Blondin, J. M., & Harrington, J. P. 1997, ApJL, 482, L97

(ref: Borkowski2001) Borkowski, K. J. & Harrington, J. P. 2001, ApJ, 550, 778

(ref: Bujarrabal1997) Bujarrabal, V., Alcolea, J., Neri, R., & Grewing, M. 1997, A&A, 320, 540

(ref: Bujarrabal2001) Bujarrabal, V., Castro-Carrizo, A., Alcolea, J., & Sánchez Contreras, C. 2001, A&A, 377, 868

(ref: Bujarrabal2017) Bujarrabal, V., Castro-Carrizo, A., Alcolea, J., et al. 2017, A&A, 597, L5

(ref: CASA2022) CASA-Team, Bean, B., Bhatnagar, S., et al. 2022, Publications of the Astronomical Society of the Pacific, 134, 114501

(ref: Clube2004) Clube, K. L. & Gledhill, T. M. 2004, MNRAS, 355, L17

(ref: Cristallo2015) Cristallo, S., Straniero, O., Piersanti, L., & Gobrecht, D. 2015, ApJS, 219, 40

(ref: Cutri2003) Cutri, R. M., Skrutskie, M. F., van Dyk, S., et al. 2003, VizieR Online Data Catalog, 2246

(ref: Danilovich2017) Danilovich, T., Lombaert, R., Decin, L., et al. 2017, A&A, 602, A14

(ref: Day2010) Day, F. M., Pihlström, Y. M., Claussen, M. J., & Sahai, R. 2010, ApJ, 713, 986

(ref: DeMarco2009) De Marco, O. 2009, PASP, 121, 316

(ref: DeMarco2015) De Marco, O., Long, J., Jacoby, G. H., et al. 2015, MNRAS, 448, 3587

(ref: DeNutte2017) De Nutte, R., Decin, L., Olofsson, H., et al. 2017, A&A, 600, A71

(ref: Decin2020) Decin, L., Montargès, M., Richards, A. M. S., et al. 2020, Science, 369, 1497

(ref: Dehaes2007) Dehaes, S., Groenewegen, M. A. T., Decin, L., et al. 2007, MNRAS, 377, 931

(ref: Eden2017) Eden, D. J., Moore, T. J. T., Plume, R., et al. 2017, MNRAS, 469, 2163

(ref: Fang2018) Fang, X., Gómez de Castro, A. I., Toalá, J. A., & Riera, A. 2018, ApJL, 865, L23

(ref: Gaia2021) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2021, A&A, 649, A1

(ref: GallardoCava2022) Gallardo Cava, I., Bujarrabal, V., Alcolea, J., Gómez-Garrido, M., & Santander-Garcı́a, M. 2022, A&A, 659, A134

(ref: GallardoCava2021) Gallardo Cava, I., Gómez-Garrido, M., Bujarrabal, V., et al. 2021, A&A, 648, A93

(ref: GarciaSegura2014) Garcı́a-Segura, G., Villaver, E., Langer, N., Yoon, S. C., & Manchado, A. 2014, ApJ, 783, 74

(ref: Gomez2018) Gómez, J. F., Niccolini, G., Suárez, O., et al. 2018, MNRAS, 480, 4991

(ref: Goriely2018) Goriely, S. & Siess, L. 2018, A&A, 609, A29

(ref: Groenewegen2002) Groenewegen, M. A. T. 2002, arXiv e-prints, astro

(ref: Groenewegen1995) Groenewegen, M. A. T., van den Hoek, L. B., & de Jong, T. 1995, A&A, 293, 381

(ref: Guertler1996) Guertler, J., Koempe, C., & Henning, T. 1996, A&A, 305, 878

(ref: Harris1987) Harris, M. J., Lambert, D. L., Hinkle, K. H., Gustafsson, B., & Eriksson, K. 1987, ApJ, 316, 294

(ref: Herwig2005) Herwig, F. 2005, ARA&A, 43, 435

(ref: Hillwig2016) Hillwig, T. C., Jones, D., De Marco, O., et al. 2016, ApJ, 832, 125

(ref: Hinkle2016) Hinkle, K. H., Lebzelter, T., & Straniero, O. 2016, ApJ, 825, 38

(ref: Hoefner2018) Höfner, S. & Olofsson, H. 2018, A&ARv, 26, 1

(ref: Huggins2004) Huggins, P. J., Muthu, C., Bachiller, R., Forveille, T., & Cox, P. 2004, A&A, 414, 581

(ref: Iben1983) Iben, Jr., I. & Renzini, A. 1983, ARA&A, 21, 271

(ref: Imai2007) Imai, H. 2007, in Astrophysical Masers and their Environments, ed. J. M. Chapman & W. A. Baan, Vol. 242, 279–286

(ref: Ita2010) Ita, Y., Matsuura, M., Ishihara, D., et al. 2010, A&A, 514, A2

(ref: Jones2017) Jones, D. & Boffin, H. M. J. 2017, Nature Astronomy, 1, 0117

(ref: Justtanont2012) Justtanont, K., Khouri, T., Maercker, M., et al. 2012, A&A, 537, A144

(ref: Karakas2014) Karakas, A. I. & Lattanzio, J. C. 2014, PASA, 31, e030

(ref: Karakas2016) Karakas, A. I. & Lugaro, M. 2016, ApJ, 825, 26

(ref: Karakas2018) Karakas, A. I., Lugaro, M., Carlos, M., et al. 2018, MNRAS, 477, 421

(ref: Khouri2022) Khouri, T., Vlemmings, W. H. T., Tafoya, D., et al. 2021, Nature Astronomy, 6, 275

(ref: Kwok1994) Kwok, S. 1994, PASP, 106, 344

(ref: Lagadec2011) Lagadec, E., Verhoelst, T., Mékarnia, D., et al. 2011, MNRAS, 417, 32

(ref: Lebzelter2019) Lebzelter, T., Hinkle, K. H., Straniero, O., et al. 2019, ApJ, 886, 117

(ref: Li2024) Li, Y. Q., Morris, M. R., & Sahai, R. 2024, Galaxies, 12

(ref: Manteiga2011) Manteiga, M., Garcı́a-Hernández, D. A., Ulla, A., Manchado, A., & Garcı́a-Lario, P. 2011, AJ, 141, 80

(ref: MillerBertolami2016) Miller Bertolami, M. M. 2016, A&A, 588, A25

(ref: Moe2006) Moe, M. & De Marco, O. 2006, ApJ, 650, 916

(ref: Morris1985) Morris, M., Lucas, R., & Omont, A. 1985, A&A, 142, 107

(ref: Olofsson2022) Olofsson, H., Khouri, T., Sargent, B. A., et al. 2022, A&A, 665, A82

(ref: Omont1993) Omont, A., Loup, C., Forveille, T., et al. 1993, A&A, 267, 515

(ref: Oomen2018) Oomen, G.-M., Van Winckel, H., Pols, O., et al. 2018, A&A, 620, A85

(ref: Oppenheimer2005) Oppenheimer, B. D., Bieging, J. H., Schmidt, G. D., et al. 2005, ApJ, 624, 957

(ref: Palmerini2021) Palmerini, S., Cristallo, S., Piersanti, L., Vescovi, D., & Busso, M. 2021, Universe, 7, 175

(ref: Parker2006) Parker, Q. A., Acker, A., Frew, D. J., et al. 2006, MNRAS, 373, 79

(ref: Ramstedt2020) Ramstedt, S., Vlemmings, W. H. T., Doan, L., et al. 2020, A&A, 640, A133

(ref: Rees2024) Rees, N. R., Izzard, R. G., & Karakas, A. I. 2024, MNRAS, 527, 9643

(ref: Renzini1981) Renzini, A. 1981, Red giants as precursors of planetary nebulae, ed. J. Iben, I. & A. Renzini, Vol. 88, 431–446

(ref: Riera2003) Riera, A., Garcı́a-Lario, P., Manchado, A., Bobrowsky, M., & Estalella, R. 2003, A&A, 401, 1039

(ref: Riera1995) Riera, A., Garcia-Lario, P., Manchado, A., Pottasch, S. R., & Raga, A. C. 1995, A&A, 302, 137

(ref: Sahai2003b) Sahai, R., Kastner, J. H., Frank, A., Morris, M., & Blackman, E. G. 2003, ApJL, 599, L87

(ref: Sahai2007) Sahai, R., Morris, M., Sánchez Contreras, C., & Claussen, M. 2007, AJ, 134, 2200

(ref: Sahai2011) Sahai, R., Morris, M. R., & Villar, G. G. 2011, AJ, 141, 134

(ref: Sahai1998) Sahai, R. & Trauger, J. T. 1998, AJ, 116, 1357

(ref: Sahai2017) Sahai, R., Vlemmings, W. H. T., Gledhill, T., et al. 2017, ApJL, 835, L13

(ref: SanchezContreras1998) Sánchez Contreras, C., Alcolea, J., Bujarrabal, V., & Neri, R. 1998, A&A, 337, 233

(ref: SanchezContreras2017) Sánchez Contreras, C., Báez-Rubio, A., Alcolea, J., Bujarrabal, V., & Martı́n-Pintado, J. 2017, A&A, 603, A67

(ref: SanchezContreras2001) Sánchez Contreras, C. & Sahai, R. 2001, ApJL, 553, L173

(ref: SanchezContreras2012) Sánchez Contreras, C. & Sahai, R. 2012, ApJS, 203, 16

(ref: Smith1990) Smith, V. V. & Lambert, D. L. 1990, ApJS, 72, 387

(ref: Soker2020) Soker, N. 2020, Galaxies, 8, 26

(ref: Stancliffe2005) Stancliffe, R. J., Izzard, R. G., & Tout, C. A. 2005, MNRAS, 356, L1

(ref: Stancliffe2004) Stancliffe, R. J., Tout, C. A., & Pols, O. R. 2004, MNRAS, 352, 984

(ref: Su2003) Su, K. Y. L., Hrivnak, B. J., Kwok, S., & Sahai, R. 2003, AJ, 126, 848

(ref: Su1998) Su, K. Y. L., Volk, K., Kwok, S., & Hrivnak, B. J. 1998, ApJ, 508, 744

(ref: Suarez2006) Suárez, O., Garcı́a-Lario, P., Manchado, A., et al. 2006, A&A, 458, 173

(ref: Szczerba2007) Szczerba, R., Siódmiak, N., Stasińska, G., & Borkowski, J. 2007, A&A, 469, 799

(ref: Tafoya2020) Tafoya, D., Imai, H., Gómez, J. F., et al. 2020, ApJL, 890, L14

(ref: Trammell1996) Trammell, S. R. & Goodrich, R. W. 1996, ApJL, 468, L107

(ref: Ueta2007) Ueta, T., Murakawa, K., & Meixner, M. 2007, AJ, 133, 1345

(ref: vanWinckel2007) Van Winckel, H. 2007, Baltic Astronomy, 16, 112

(ref: vanWinckel2018) Van Winckel, H. 2018, arXiv e-prints, arXiv:1809.00871

(ref: vanWinckel2000) Van Winckel, H. & Reyniers, M. 2000, A&A, 354, 135

(ref: vanWinckel1996) Van Winckel, H., Waelkens, C., & Waters, L. B. F. M. 1996, A&A, 306, L37

(ref: Vassiliadis1993) Vassiliadis, E. & Wood, P. R. 1993, ApJ, 413, 641

(ref: Vassiliadis1994) Vassiliadis, E. & Wood, P. R. 1994, ApJS, 92, 125

(ref: Velilla-Prieto2023) Velilla-Prieto, L., Fonfrı́a, J. P., Agúndez, M., et al. 2023, Nature, 617, 696

(ref: Ventura2018) Ventura, P., Karakas, A., Dell’Agli, F., Garcı́a-Hernández, D. A., & Guzman-Ramirez, L. 2018, MNRAS, 475, 2282

(ref: Vickers2015) Vickers, S. B., Frew, D. J., Parker, Q. A., & Bojičić, I. S. 2015, MNRAS, 447, 1673

(ref: Volk2007) Volk, K., Kwok, S., & Hrivnak, B. J. 2007, ApJ, 670, 1137

(ref: Weiss2009) Weiss, A. & Ferguson, J. W. 2009, A&A, 508, 1343

(ref: Simbad2000) Wenger, M., Ochsenbein, F., Egret, D., et al. 2000, A&AS, 143, 9

# Additional table

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  | GLMP | GLMP | AFGL | HD | Hen | M1-92 |
| Spectral lines | Freq. \[GHz\] | 950 | 953 | 5385 | 187885 | 3-1475 |  |
| NaCl $v=1, J=17-16$ | 219.61498 |  | X |  |  |  |  |
| SO 3$\Sigma,~J=6_5-5_4$ | 219.94944 |  |  |  |  | X | X |
| Si$^{13}$CC $J=17_{2,15}-17_{2,16}$ (?) | 220.598 | X |  |  |  |  |  |
| ? | 220.643 | X |  |  |  |  |  |
| ? | 220.685 | X |  |  |  |  |  |
| ? | 220.714 | X | X |  |  |  |  |
| ? | 220.746 | X | X |  |  |  |  |
| SiC$_2$ $J=10_{0,10} - 9_{0,9}$ | 220.77369 | X | X |  |  |  |  |
| NaCl $J=17-16$ | 221.26016 | X | X |  |  |  |  |
| ? | 221.297 |  | X |  |  |  |  |
| ? | 223.303 | X |  |  |  |  |  |
| K$^{37}$Cl $J=30-29$ (?) | 223.78283 |  | X |  |  |  |  |
| NaCl $J=18-17$ | 234.25192 | X | X |  |  |  |  |
| SiC$_2$ $J=10_{8,2} - 9_{8,1}$ | 234.53401 | X | X |  |  |  |  |
| SiC$_2$ $J=10_{8,3} - 9_{8,2}$ | 234.53401 | X | X |  |  |  |  |
| SiS $v=1, J=13-12$ | 234.814 |  | X |  |  |  |  |
| SO$_2$ $J=4_{2,2}-3_{1,3}$ | 235.15172 |  |  |  |  | X | X |
| SiC$_2$ $J=10_{6,5} - 9_{6,4}$ | 235.71301 | X | X |  |  |  |  |
| SiC$_2$ $J=10_{6,4} - 9_{6,3}$ | 235.71307 | X | X |  |  |  |  |
| K$^{37}$Cl $v=2, J=32-31$ (?) | 235.766 |  | X |  |  |  |  |
| SiS $J=13-12$ (incomplete profile) | 235.96135 | X | X |  |  | X |  |
| SO$_2$ $J=16_{1,15}-15_{2,14}$ | 236.21669 |  |  |  |  | X |  |
| HC$_3$N $~J=26-25$ | 236.51279 | X | X | X |  |  |  |
| SO$_2$ $J=12_{3,9}-12_{2,10}$ | 237.06883 |  |  |  |  | X |  |
| HC$_3$N $~v_7=1, J=26-25, I=1e$ | 237.09318 | X | X |  |  |  |  |
| HC$_3$N $~v_6=1, J=26-25, I=1f$ | 237.09318 | X | X |  |  |  |  |
| SiC$_2$ $J=10_{4,7} - 9_{4,6}$ | 237.15002 | X | X |  |  |  |  |
| SiC$_2$ $J=10_{4,7} - 9_{4,6}$ | 237.33131 | X | X |  |  |  |  |
| HC$_3$N $~v_7=1, J=26-25, I=1f$ | 237.43205 | X | X |  |  |  |  |

: Lines other than those of CO isotopologues detected towards the six post-AGB sources.

# Velocity-integrated maps of the $^{13}$CO, C$^{17}$O, and C$^{18}$O $J$=2$-$1  lines

![](Fig_13CO_all.pdf)

![](Fig_C17O_all.pdf)

![](Fig_C18O_all.pdf)

# Spitzer images of GLMP 950 and GLMP 953

![image](Fig_SPITZER_GLMP950_3.6um.pdf) ![image](Fig_SPITZER_GLMP950_4.5um.pdf)

![image](Fig_SPITZER_GLMP953.pdf) ![image](Fig_SPITZER_GLMP953_4.5um.pdf)

# Continuum image of AFGL 5385 with additional source

![](Fig_AFGL_5385_cont.pdf)

[^1]: *Send offprint requests to T. Khouri*\

[^2]: ALMA Technical Handbook for Cycle 8

</paper>

Write the methods card for this paper.