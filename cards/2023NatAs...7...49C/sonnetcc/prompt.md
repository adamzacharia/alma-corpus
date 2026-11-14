# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2023NatAs...7...49C\sonnetcc\reply.txt

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
 "bibcode": "2023NatAs...7...49C",
 "title": "UV-driven chemistry as a signpost of late-stage planet formation",
 "year": 2023,
 "journal": "Nature Astronomy",
 "first_author": "Calahan, Jenny K.",
 "n_authors": 17,
 "arxiv_id": "2212.05539",
 "doi": "10.1038/s41550-022-01831-8",
 "alma_projects_linked_by_archive": [
  "2016.1.01046.S",
  "2018.1.01055.L"
 ]
}
```

Paper text:
<paper>
# UV-driven Chemistry as a Signpost for Late-stage Planet Formation

## Abstract

The chemical reservoir within protoplanetary disks has a direct impact on planetary compositions and the potential for life. A long-lived carbon-and nitrogen-rich chemistry at cold temperatures ($\leq$ 50 K) is observed within cold and evolved planet-forming disks. This is evidenced by bright emission from small organic radicals in 1–10 Myr aged systems that would otherwise have frozen out onto grains within 1 Myr. We explain how the chemistry of a planet-forming disk evolves from a cosmic-ray/X-ray-dominated regime to a ultraviolet-dominated chemical equilibrium. This,in turn, will bring about a temporal transition in the chemical reservoir from which planets will accrete. This photochemical dominated gas phase chemistry develops as dust evolves via growth, settling and drift, and the small grain population is depleted from the disk atmosphere. A higher gas-to-dust mass ratio allows for deeper penetration of ultraviolet photons is coupled with a carbon-rich gas (C/O $>$ 1) to form carbon-bearing radicals and ions. This further results in gas phase formation of organic molecules, which then would be accreted by any actively forming planets present in the evolved disk.

# Main

Protoplanetary disks are the natal environments for planets. Disks have three main components: a pebble-rich dusty midplane (dust grain radius $>\sim$ 1mm), a gaseous atmosphere extending well above(cite: Miotello22) and radially beyond (by a factor of $\sim$2(cite: Ansdell18)) the pebble-rich midplane, and a small dust population (radius $<$ 10 $\mu$m) that is coupled to the gas. Each component of the protoplanetary disk has an impact on shaping the chemistry of actively forming planets. The solid cores of giant planets must form over a short timescale ($\sim$1 Myr) for the eventual planet to obtain its full mass over the course of a typical lifetime of gas in a disk (3-10 Myr(cite: Haisch01)) and to explain the widely observed gap and ring structures that are thought to be indicative of planet formation(cite: Andrews18). The compositions of pebbles and their icy mantles directly influence the final composition of a solid planetary core (cite: Oberg11ice; Johansen17). After a core becomes sufficiently massive, planets start to accrete material from the gaseous reservoir surrounding the pebble-rich midplane of a protoplanetary disk to form their atmospheres (cite: Lambrechts14). It remains difficult to directly probe the gas within the planet-forming midplane due to the high dust densities leading to elevated dust optical depths that mask line emission, as well as cold temperatures which leads to the freezing out common gas tracers such as CO onto dust grains. However, constraining the chemical environment of the planet-forming midplane is essential to connect sub-mm observations probing the warm intermediate regions above the disk midplane to the composition of actively forming planets.

The molecules $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ are two of many complex organic molecules (loosely defined as a molecules with at least four atoms, including multiple carbon atoms) that could act as basic precursors to prebiotic molecules(cite: Powner09; Ritson12; Sutherland15). $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ have been observed and spatially resolved towards the protoplanetary disks around six young stars: GM Aur, AS 209, HD 163296, MWC 480, LkCa 15, and V4046 Sgr (cite: Bergner18; Ilee21; Kastner18; Oberg15). $\textrm{CH}_{3}\textrm{CN}$ has also been spatially resolved observed toward the TW Hya disk(cite: Loomis18), and a couple of small ($\approx$4 source) surveys have detected unresolved $\textrm{CH}_{3}\textrm{CN}$ or $\textrm{HC}_{3}\textrm{N}$ emission from other young stellar objects(cite: Chapillon12). These molecules exhibit bright emission signifying high gas phase abundances and column densities (N$_{\rm{Total}}$=10$^{12}$-10$^{13} \rm{cm}^{-2}$ (cite: Bergner18; Ilee21)). $\textrm{CH}_{3}\textrm{CN}$ is an excellent probe of gas temperature due to multiple transitions tracing a range of energy states \[lowest energy state E$_{L} \approx$5 K, spanning lower energy states over $\Delta$E$_{L}$=$\sim$100 K\] that can be observed simultaneously. Each *J*-transition (where *J* is the rotational quanum number) has a series of *K*-ladder transitions (where *K* is the quantum number of angular momentum along the molecular axis) which are only sensitive to collisions, thus the ratio between *K*-transitions depends only on the gas density and temperature. The *K*-transitions span a large range of temperatures and are sufficiently close in frequency to observe in one spectral setting with the *Atacama Large Millimeter/submillimeter Array (ALMA)*. Analyses of rotational diagrams(cite: Goldsmith99) made from $\textrm{CH}_{3}\textrm{CN}$ observations demonstrate an origin in gas with a temperature between 25-50 K(cite: Ilee21), well below the expected desorption temperature (100-124 K(cite: Corazzi21)). Thus, the brightly observed flux from this species and similar nitriles and organics like $\textrm{HC}_{3}\textrm{N}$, and CH$_{2}$CN(cite: Canta21) present a chemical conundrum as they should not be present in the gaseous state; rather, they should be frozen on cold grain surfaces. Where $\textrm{CH}_{3}\textrm{CN}$ and other carbon-rich molecules reside and how they are replenished in the gas phase has a substantial impact on our understanding of prebiotic enrichment into gaseous planet atmospheres. The traditional solution to this apparent discrepancy has been to turn to grain-surface chemistry. Simple carbon- and nitrogen-bearing molecules can undergo hydrogenation or other reactions to form complex organics on the surface of a grain that then non-thermally desorb the grain intact. This solution has been used to explain the organic inventories locked onto pebbles and icy grains (cite: Oberg11ice; Bergner21). This dust chemistry path requires both an intact photodesorption rate of $\textrm{CH}_{3}\textrm{CN}$ from the grains of 10$^{-3}$ mols/photon(cite: Walsh14; Loomis18) and a reactive desorption efficiency(cite: Vasyunin13) of 1%. Laboratory experiments find an intact photodesorption efficiency of $\textrm{CH}_{3}\textrm{CN}$ to be orders of magnitude less efficient (10$^{-5}$ mols/photon(cite: Basalgete21)) and reactive desorption has not been well studied in laboratory experiments for these species.

We posit here that there is a simpler alternative based solely on disk evolution processes that have been previously theorized and observed which link the disk gas chemistry to planet formation. This involves two ingredients: (1) an elevated C-to-O ratio in the gas and (2) greater penetration of UV photons due to a reduction in the total surface area of small grain population due to pebble formation. These combine to power a state of photo-chemistry equilibrium.

There has been mounting evidence for an elevated C-to-O gas phase ratio at large radial distances in evolved and cool gas-rich protoplanetary disks. Brighter than expected emission from small hydrocarbons such as C$_{2}$H (cite: Miotello19; Bosman21a) and complex organics such as c-C$_{3}$H$_{2}$ (cite: Cleeves21) in disks and $\textrm{HC}_{3}\textrm{N}$ and $\textrm{CH}_{3}\textrm{CN}$ in photon-dominated regions(cite: LeGal19) have independently suggested a C-to-O ratio well above the solar abundance ratio (C-to-O$\approx$0.55) (cite: Asplund21). As a radical, C$_{2}$H has a short lifetime ($<$1000 years), but it is found to be abundant in the gas. Bosman et al. 2021(cite: Bosman21a) find that the only way to reproduce the high column densities observed was to increase the C-to-O ratio throughout the full disk to between 1-2. They found that it was also necessary for C$_{2}$H to exist in high density gas while remaining above the disk midplane (height/radius$\approx$0.1-0.2) where UV photons dominate the high-energy photon budget. Together, this produces a long-lived carbon-rich gas phase cycle in photochemical equilibrium(cite: Bosman21a). One critical factor is that C$_2$H is predicted and is observed to exist above the disk midplane(cite: Law21emit). In contrast, $\textrm{CH}_{3}\textrm{CN}$ has been observed to emit closer to the midplane(cite: Ilee21). Extending the carbon-rich chemical environment that is used to explain C$_{2}$H observations to the midplane could allow for gas phase formation of complex molecules in the planet-forming zone. Elevated C-to-O ratios would be necessary to supply the materials to create hydrocarbons and nitriles. However, this alone would not alleviate the issue of $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ existing in the gas at temperatures at which they should be frozen and locked onto grains.

A non-thermal desorption mechanism is needed to increase the number of molecules that are being desorbed from the grains, either intact or as fragments of larger molecules. If the disk atmosphere is small-dust rich, with a gas-to-dust ratio close to the typical interstellar medium (ISM) mass ratio (gas-to-dust = 100) then UV radiation cannot penetrate deep into the disk. In this case, only high energy radiation (X-rays and cosmic rays) can penetrate the dust and gas and drive the chemistry within and near the midplane. Small dust grains are the main opacity source for UV photons which are readily produced by the young and active star. As the protoplanetary disk evolves, small dust grains agglomerate and eventually settle downwards and drift inward radially as they grow in size(cite: Andrews18_dust; Birnstiel12), decreasing the total surface area of the small grain population. As the main opacity source begins to deplete, UV photons can penetrate deeper into the disk. Here, complete desorption of $\textrm{CH}_{3}\textrm{CN}$ or $\textrm{HC}_{3}\textrm{N}$ is inhibited due to the dense and cold environment(cite: LeGal19). This mechanism would have an effect on all molecules residing on grains, and a brief discussion regarding this can be found in the Supplemental Materials, in the section ‘Implications on other molecules’.

The combined effect of a high C-to-O ratio and excess UV flux allows for complex molecules to exist within the gas phase at cold, midplane temperatures. Thus bright hydrocarbon and nitrile (i.e. C$_{2}$H, CH$_{3}$CN) emission from the cold midplane acts as a signpost for an evolved dust population, coincident with an advanced stage of planet formation including the accumulation of gas-giant atmospheres. The chemical scenario we put forward, comparing early and late-stage disk environments is shown in Figure [1](#fig:schematic). The disks observed in the Molecules with ALMA at Planet-forming Scales (MAPS) large program(cite: Oberg21) provide plausible support for this theory. The youngest disks in the MAPS sample reside around IM Lup and AS 209 which are on the order of 1-2 Myr old(cite: Oberg21). Towards the youngest source, IM Lup, there is no detection of $\textrm{CH}_{3}\textrm{CN}$ nor $\textrm{HC}_{3}\textrm{N}$. AS 209 has detections of $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ which suggest both molecules emit from z/r$>$0.1. The disk systems surrounding stars $>$6 Myr have $\textrm{CH}_{3}\textrm{CN}$ detected at z/r$<$0.1 as determined by the modeled thermal structure and detected rotational temperature from the K-ladder transitions. This complex organic-rich midplane will influence the atmospheres of planetary companions. It is worth noting that the oldest disk systems in the MAPS program exist around Herbig stars while the youngest systems are T Tauri stars. The UV-bright spectrum innate to Herbig stars may additionally influence the push of complex molecules towards the planet-forming midplane. Currently, the MAPS sample contains the bulk of the resolved $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ data towards protoplanetary disks. To explore the effect of the stellar spectrum on $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ emission more disks with a wide range of stellar host masses would need to be observed.

![](figures/graphic.pdf)

To test the validity of this proposed end-stage chemistry, we first explored single point models representative of the disk midplane with corresponding cold temperatures and high gas densities (approximately 35 K, 5$\times$10$^{11}$ mol/cm$^{-3}$ ). We varied the gas-to-dust mass ratio and initial carbon abundance among other physical and chemical variables including the nitrogen abundance, dust extinction, and ionization rate. We found that the gas phase $\textrm{CH}_{3}\textrm{CN}$ abundance was the most sensitive to the gas-to-dust ratio and initial gas phase carbon abundance. We then produced a thermo-chemical model representing the disk around the Herbig Ae star HD 163296. This disk is old (approx. 7.6 Myr)(cite: Bergner19) and is nearby at 101 pc(cite: Gaia18) and has observed jets and winds (cite: Booth21; Xie21). The HD 163296 disk has been widely observed in multiple gas and dust tracers with high spatial resolution ($\sim$10 au) with clear gap and ring structures typically assumed to be associated with active planet formation(cite: Andrews18; Oberg21). There is bright $\textrm{CH}_{3}\textrm{CN}$ emission coming from $\sim$35 K gas as well as bright emission from $\textrm{HC}_{3}\textrm{N}$ and HCN(cite: Ilee21; Bergner21a). Our modeling efforts follow that of Zhang et al. 2021(cite: Zhang21), and Calahan et al. 2021b(cite: Calahan21b) which set up a thermo-chemical model of the HD 163296 disk by reproducing the mm dust-continuum observations, the spectral-energy distribution (SED), the full line intensity and morphology of six CO isotopologue transitions, and the vertical distribution of the optically thick lines. The model of HD 163296 started with a gas-to-small dust ratio of the disk equal to 500(cite: Zhang21) which was needed to reproduce the disk’s SED.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Parameters** |  | **TW Hya** |  |  | **HD 163296** |  |
|  | Gas | Small Dust | Large Dust | Gas | Small Dust | Large Dust$^{a}$ |
| Mass (M$_{\odot}$) | 0.025 | $1.0\times 10^{-4}$ | $4.0\times 10^{-4}$ | 0.14 | $2.6 \times 10^{-5}$ | 0.024 |
| $\Psi$ | 1.1 | 1.2 | 1.2 | 1.08 | 1.08 | 1.08 |
| $\gamma$ | 0.75 | 0.75 | 1.0 | 0.8 | 0.8 | 0.1 |
| h$_{c}$ (au) | 42 | 42 | 8.4 | 8.44 | 8.44 | n/a |
| r$_{c}$ (au) | 400 | 400 | 400 | 165 | 165 | n/a |
| r$_{in}$ (au) | 0.1 | 0.5 | 1 | 0.45 | 0.45 | 0.45 |
| r$_{out}$ (au) | 200 | 200 | 200 | 600 | 600 | 240 |

: Modeling Parameters: TW Hya & HD 163296

Table notes: Final values of the TW Hya and HD 163296 models that reproduce CO, HD, $\textrm{CH}_{3}\textrm{CN}$, HCN, and $\textrm{HC}_{3}\textrm{N}$ observations when available. r$_{in}$ and r$_{out}$ are the radial inner and outer limits of the disk, beyond these limits there is assumed to be no gas nor dust. $^{a}$ The surface density of the large dust distribution in HD 163296 is empirically set by continuum observations, thus it is not smooth and it is not dictated by the parametric equations.

# Results

To produce this end-stage chemical environment, we deplete the small dust mass by a factor of 10 throughout the disk of HD 163296 making the new gas-to-dust mass ratio above the pebble disk midplane equal to 5,000. We then enhanced the initial gas phase carbon abundance in the system in the form of C, CH$_{4}$, or C$_{2}$H, increasing the overall gas phase carbon-to-oxygen ratio in both disks to above unity. There are two possible sources for excess carbon in protoplanetary disks, either through the destruction of refractory carbon grains(cite: Bosman_refrac) or CO depletion through mechanisms such as reactions with ionized molecules and atoms such as He$^{+}$ or H$_{3}^{+}$(cite: Schwarz18_1) and a series of chemical and freeze-out processes. We note that while signatures of CO depletion are found in the HD 163296 disk(cite: Zhang21; Calahan21b), CO destruction likely only occurs in environments with a high cosmic-ray flux \[2$\times$10$^{-17}$s$^{-1}$\](cite: Schwarz18_1). Additionally, CO destruction would supply equal amounts of carbon and oxygen, while we seek to enhance carbon over oxygen. Our thermo-chemical model is run for a full megayear (Myr), after which the chemistry reaches an equilibrium. Notable chemical feedback due to dust evolution is predicted to occur over scales of $\sim$1 Myr(cite: Krijt18; VanClepper22), thus we use $\sim$1 Myr as an approximate length of time for the chemical environment to transition from ‘early-stage’ to ‘late-stage’ dust evolution and subsequently exist in a state of photochemical equilibrium. Gas phase chemical reactions and rates were taken from the chemical network derived in Bosman et al. 2018(cite: Bosman18) which in turn relies on the UMIST Database for Astrochemistry Rate12 version(cite: McElroy13) (see Methods section for more details). We found that regardless of the carrier of carbon, using a C/O = 1-2 and a factor of 10 depletion of small dust roughly reproduces line ratios and fluxes of the radial intensity profiles of $\textrm{CH}_{3}\textrm{CN}$, $\textrm{HC}_{3}\textrm{N}$, and HCN (see Figure [2](#fig:observations)). In this proposed scenario, $\sim$96% of the total mass of $\textrm{CH}_{3}\textrm{CN}$ continues to reside frozen out onto grains, but the increase in UV flux allows for sufficient $\textrm{CH}_{3}\textrm{CN}$ to exist and be formed in the gas to reproduce observed radial intensity profiles and column densities.

Figure [3](#fig:2d_abundances) shows the two-dimensional number densities of $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$. The inner $\sim$20 au exhibited brighter or more centrally peaked emission than was seen in observations if the C-to-O ratio = 2 throughout the full disk. To counteract this, we set the C-to-O ratio = 0.47, or the ISM ratio, inside of ($\sim$20 au) where Zhang et al. 2021(cite: Zhang21) found an ISM ratio of $\textrm{H}_{2}$/CO (See Supplementary Figure 2). The inner disk emission remains slightly brighter than observed in HCN and $\textrm{CH}_{3}\textrm{CN}$ (see Figure [2](#fig:observations)) with this alteration. This could be accounted for via a depletion in the nitrogen abundance within the N$_{2}$ ice line, a strong buildup of pebbles around the water ice line ($\sim$5au), a lower HCN desorption energy, or a combination of these effects. Additionally, the observations may also be affected by processes such as beam smearing and a higher dust opacity than modeled. A comparison model without a depletion in small dust mass is shown in Supplementary Figure 5.

![](figures/HD16_observations_ch3cn.pdf)

![](figures/abundances_2d.pdf)

# Discussion

$\textrm{HC}_{3}\textrm{N}$ and $\textrm{CH}_{3}\textrm{CN}$ are built up in the gas from simple carbon and nitrogen-based volatiles (see Methods section “Chemical Reactions" for details). A reservoir of these more simple molecules is maintained in the gas phase due to photodesorption from dust grain surfaces by an enhanced UV-field. The main destruction products from $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ are simple volatiles that can cycle back to create larger nitrile molecules including their original parent molecule. While there are enough complex organic molecules in the gas phase to observe bright emission, the majority of the $\textrm{CH}_{3}\textrm{CN}$, $\textrm{HC}_{3}\textrm{N}$, and HCN near the midplane still remains frozen out onto grains. The carbon-rich gas reservoir and UV-dominated disk together allow for a cycle of carbon chemistry to remain active in the gas phase. This implies that actively accreting gas giants will build their atmosphere out of this complex nitrile-enhanced material. Gas giant planets with atmospheres containing a chemical make-up with a C-to-O ratio $>$1 can be explained by the natural evolution of dust and the observed high C-to-O ratios within protoplanetary disks. This environment could be extended to the inner disk in some cases, as studies such as Najita et al. 2011(cite: Najita11) and Anderson et al. 2021(cite: Anderson21) posit a higher than solar C-to-O ratio within the inner disk to account for Spitzer observations of HCN and C$_{2}$H$_{2}$ around T Tauri stars.

The implications of this end-stage chemistry are far-reaching. Primarily, we put forward a new chemically and physically coupled picture of planet formation and its direct impact on the chemistry of forming planet atmospheres. Within the early stages of planet formation, pebble growth and accretion into solid planet cores has begun, and chemistry onto these cores are influenced primarily by the chemical make-up of large pebbles and their icy mantles. The chemistry active in the midplane during this stage of formation is dominated by X-rays and cosmic rays(cite: Woitke09). After timescales of order 1 Myr, at the end-stage of pebble formation, small grains have grown and settled towards the midplane, allowing for UV photons to penetrate deeper in the disk than previously assumed. This excess UV flux in concert with an above solar C-to-O ratio produces a carbon-rich gas phase cycle of production and destruction in the gas surrounding actively forming planets. Bright emission from $\textrm{CH}_{3}\textrm{CN}$, $\textrm{HC}_{3}\textrm{N}$ and other carbon-rich molecules emitting at cold temperatures are a sign-post of this evolved chemical environment. These forming gas giants may accrete this surrounding gas and its chemical signature into their atmosphere, and may be responsible for high C-to-O measurements that have been observed in exo-planetary atmospheres as compared to their host star(cite: Brewer17). Secondly, the deeper penetration of UV photons pushes the CO and H$_{2}$ self-shielding layers deeper into the disk. Due to this, there are more ions such as C$^{+}$ and H$^{+}$ throughout the disk than would have been present with a regular (ISM) level of small dust surface area. As the ion-fraction increases so does the area of the disk that is subject to magneto-rotational instability (MRI). In our final model, the UV field increases by a factor of 3-5 in the atmosphere and between 1-2 near the midplane, and thirteen times more gas mass is MRI-active, most notably the gas midplane within 10 au, and then at a z/r=0.1-0.2 within 30 au (see Figure 4). This could be a source of accretion(cite: Gammie96) for older disks. Our proposed UV-dominated carbon-rich gas phase chemistry is a major shift in our understanding of the astrochemistry of planet formation. This transition will have a strong effect on the composition of actively forming planets, disk MRI-activity, and subsequent disk accretion.

![](figures/MRI_HD16.pdf)

# Methods

## Observations

For a thorough description of the observations and the techniques used to obtain the CLEAN-ed images and radial profiles of $\textrm{CH}_{3}\textrm{CN}$, HCN, and $\textrm{HC}_{3}\textrm{N}$ towards HD 163296 see Czekala et al. 2021(cite: Czekala21), Law et al. 2021(cite: Law21rad), and Öberg et al. 2021(cite: Oberg21). A description of the observations of $\textrm{CH}_{3}\textrm{CN}$ towards TW Hya can be found in Loomis et al. 2018a(cite: Loomis18). A brief summary of these observations are as follows.

### - HD 163296 -

The data for HD 163296 is from the MAPS large program (Project ID 2018.1.01055.L)(cite: Oberg21). The image cubes were produced using the `tclean` task in the Common Astronomy Software Applications (CASA) package, version 6.1.0(cite: McMullin07). Keplerian masks based on the disk geometric parameters were used in the CLEANing process and the final images were then corrected for the Jorsater & van Moorsel effect to ensure that the image residuals are in units consistent with that of the CLEAN model. For all lines, we used the beam-circularized and uv-tapered images, which had synthesised beam sizes of 0."3. All radial intensity profiles were generated by deprojecting and azimuthally-averaging zeroth moment maps using the GoFish python package.

### -TW Hya-

$\textrm{CH}_{3}\textrm{CN}$ was observed towards TW Hya as a part of ALMA project 2016.1.01046.S. Each emission line was individually imaged using `CLEAN` and the synthesised beam for each transition were matched using small uv-tapers to 1$.\!\!^{\prime\prime}$05 x 0$.\!\!^{\prime\prime}$83. A Keplerian mask was used to extract the flux for each transition. See Loomis et al. 2018a(cite: Loomis18) for more details.

## Modeling

Simple single point models of the disk environment were utilized to quickly and efficiently understand the chemical impacts of different physical and initial chemical conditions. Our chemical network is derived from Bosman et al. 2018(cite: Bosman18) which in turn is derived from the UMIST “RATE12” network(cite: McElroy13), and for this study we disregarded most grain-surface chemical reactions in order to isolate gas-phase formation of $\textrm{CH}_{3}\textrm{CN}$. After our results from the modeling suggested a higher gas/dust ratio and carbon content, we turned to more comprehensive thermo-chemical codes which model the thermal physics and chemical evolution throughout the whole disk. The code RAC2D (https://github.com/fjdu/rac-2d)(cite: Du14), was used to create models of the disks around TW Hya and HD 163296. The 2D temperature, density, and molecular abundance results were used to simulate observations of each disk with a raytracing code: RADMC-3D(cite: radmc3d). A brief description of the physical code of RAC2D is given below; a detailed description of the code can be found in Calahan et al 2021a(cite: Calahan21a).

RAC2D takes into account a gas and dust structure and stellar radiation field and computes the gas and dust temperature and chemical structure over time. Our model consists of three mass components: gas, small dust, and large dust grains. The spatial extent of each component is given by a global surface density distribution (cite: Lynden-Bell74), which is widely used in protoplanetary disk modeling and corresponds to the self-similar solution of a viscously evolved disk.

$$\begin{equation}
\Sigma(r)=\Sigma_{c}\left(\frac{r}{r_{c}}\right)^{-\gamma}\exp{\left[-\left(\frac{r}{r_{c}}\right)^{2-\gamma}\right]},
\label{surfden_equn}
\end{equation}$$

$r_{c}$ is the characteristic radius at which the surface density is $\Sigma_{c}/\rm{e}$ where $\Sigma_{c}$ is the characteristic surface density, and $\gamma$ is the power-law index that describes the radial behavior of the surface density.

A 2D density profile for the gas and dust populations can be derived from the surface density profile and a scale height:

$$\begin{equation}
    \rho(r,z) = \frac{\Sigma(r)}{\sqrt{2\pi}h(r)} \exp{\left[-\frac{1}{2}\left(\frac{z}{h(r)}\right)^{2}\right]},
\label{density_equn}
\end{equation}$$

$$\begin{equation}
    h=h_{c}\left( \frac{r}{r_{c}}\right)^{\Psi} ,
\label{heigh_equn}
\end{equation}$$

where $h_{c}$ is the scale height at the characteristic radius, and $\Psi$ is a power index that characterizes the flaring of the disk structure. The modeling parameters used for TW Hya and HD 163296 are shown in Table 1.

For both TW Hya and HD 163296 models, each dust population follows an Mathis, Rumpl, and Nordsieck (MRN) grain distribution $n(a) \propto a^{-3.5}$ (cite: Mathis77), where ‘a’ indicates the size of the grain. The small dust grains have radii between $5 \times 10^{-3}$ - $1 \mu$m, and the large grains have radii between $5 \times 10^{-3}$ - $10^{3} \mu$m. The large dust population is settled in the midplane with a smaller vertical extent and radial extent (gas extends $\sim$5 and 2.5 times above and beyond, respectively). This settled large grain population is the result of dust evolution, namely growth in concert with vertical settling to the midplane and radial drift. For the HD 163296 model, the large grain population has a unique, non-smooth, surface density profile that reproduces the millimeter continuum observations of the HD 163296 disk(cite: Isella18; Zhang21). Opacity values for the dust are calculated based on Birnstiel et al. 2018(cite: Birnstiel18). Large dust grains consist of water ice(cite: Warren08), silicates(cite: Draine03), troilites and refractory organics(cite: Henning96). Small dust grains consist of 50% silicates and 50% refractory organics. Further discussion on the modeling efforts for TW Hya can be found in Calahan et al. 2021a(cite: Calahan21a) and for HD 163296 in Calahan et al. 2021b(cite: Calahan21b).

The thermo-chemical model resulted in 2D distributions of the gas and dust temperature, density, and molecular abundances. These were used as inputs for the raytracing code RADMC-3D(cite: radmc3d). The molecular properties of $\textrm{CH}_{3}\textrm{CN}$, $\textrm{HC}_{3}\textrm{N}$, and HCN were taken from the Leiden Atomic and Molecular Database (LAMDA(cite: Schoier05)), with some molecular parameters updated according to data from the Cologne Database for Molecular Spectroscopy (CDMS(cite: Muller01; Muller05)). The result from RADMC-3D was a 3D image cube of the molecular emission across velocity space. We utilized `GoFish`(cite: GoFish) to compress these 3D images into zeroth moment maps and radial profiles which were then directly compared to the azimuthally-averaged observations.

## Chemical Reactions

The chemical reaction network utilized in this work comes from Bosman et al. 2018(cite: Bosman18) which in turn relies on the Rate12 version of the UMIST Database for Astrochemistry(cite: McElroy13): a network that is widely used across astrochemical modeling efforts. In our network there are 6,302 gas phase reactions and we have limited the grain-surface reactions to twelve. We kept grain-surface reactions that involved the formation of H$_{2}$, CH$_{2}$OH, CH$_{3}$OH, CO$_{2}$, H$_{2}$O and NH$_{3}$ due to each of these species being well-studied in the laboratory and come with strong evidence for active two-body chemistry on dust grains(cite: Allen77; Hasegawa92; Goumans08; Ioppolo08; Ioppolo10; Fuchs09; Oba12; Ruffle01) (see Table 2). Both thermal adsorption and desorption are taken into account for every molecule in the network. Our network contains molecules with at most eleven carbon atoms, and at most twelve total atoms. We run our thermo-chemical model for 1 Myr as the $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$ chemistry reaches an equilibrium after this time period (see Supplementary Figure 3). In our evolved disk model, the main formation pathways for $\textrm{CH}_{3}\textrm{CN}$ once the chemistry has reached equilibrium is as follows:

$$\rm{CH_{3}^{+} + HCN \rightarrow CH_{3}CNH^{+} + e^{-} \rightarrow CH_{3}CN + H}$$

This reaction in the gas phase is the primary formation pathway for $\textrm{CH}_{3}\textrm{CN}$, thus there is a strong reliance on HCN existing in the gas phase even at cold temperatures below its measured sublimation temperature ($\sim$85-103 K(cite: Bergner22)) and an ionization source (UV photons) to produce CH$_{3}^{+}$. $\textrm{HC}_{3}\textrm{N}$ can be readily produced by a number of different ways including:

$$\rm{N + CH_{2}CCH \rightarrow HC_{3}N + H_{2}}$$ $$\rm{CN + C_{2}H_{2} \rightarrow HC_{3}N + H}$$ $$\rm{H + C_{3}N^{-} \rightarrow HC_{3}N + e^{-}}$$

The formation of $\textrm{HC}_{3}\textrm{N}$ strongly relies on the existence of carbon-rich molecules including radicals (CN) and ions (C$_{3}$N$^{-}$).

| **Reaction** | **Reference** |
|:--:|:--:|
| gH + gH $\rightarrow$ gH$_{2}$ | Hasegawa, Herbst, & Leung 1992(cite: Hasegawa92) |
| gH + gOH $\rightarrow$ gH$_{2}$O | Ioppolo et al. 2010(cite: Ioppolo10) |
| gH + gH$_{2}$O$_{2}$ $\rightarrow$ gH$_{2}$O + gOH | Ioppolo et al. 2008(cite: Ioppolo08) |
| gH + gCH$_{3}$OH $\rightarrow$ gH$_{2}$ + gCH$_{2}$OH | Extrapolated from Fuchs et al. 2009(cite: Fuchs09) |
| gH + gCH$_{2}$OH $\rightarrow$ gCH$_{3}$OH | Extrapolated from Fuchs et al. 2009(cite: Fuchs09) |
| gH$_{2}$ + gOH $\rightarrow$ gH$_{2}$O + gH | Oba et al 2012(cite: Oba12) |
| gOH + gCO $\rightarrow$ gCO$_{2}$ + gH $^{a}$ | Ruffle & Herbst 2001(cite: Ruffle01) |
| gO + gCO $\rightarrow$ gCO$_{2}$ $^{a}$ | Goumans & Brown 2008(cite: Goumans08) |
| gO + gHCO $\rightarrow$ gCO$_{2}$ + gH | Goumans & Brown 2008(cite: Goumans08) |
| gH + gNH$_{2}$ $\rightarrow$ gNH$_{3}$ | Allen & Robinson 1977(cite: Allen77) |

: Dust Surface Reactions

Table notes: The complete list dust surface reactions accounted for in this study. $^{a}$Have additional special treatment for three body reactions

# Supplementary Information

## TW Hya

We additionally produced a thermo-chemical model representing the disk around T Tauri star TW Hya. TW Hya is approximately 10 Myrs old(cite: Thi10) and hosts the closest Class II disk at 59.9 pc(cite: Gaia18). TW Hya has been widely observed in multiple gas and dust tracers with high spatial resolution ($\sim$10 au)(cite: Andrews12; Huang18). It also exhibits bright $\textrm{CH}_{3}\textrm{CN}$ coming from $\sim$33 K gas(cite: Loomis18). Our modeling efforts of TW Hya follow that of Calahan et al. 2021a(cite: Calahan21a) which sets up a thermo-chemical model of the disk by reproducing the spectral-energy distribution (SED), the full line intensity and morphology of seven CO isotopologue transitions, and an HD J=1-0 observation from the *Hershel* PACS instrument(cite: Bergin13). To reproduce all CO radial profiles as well as the HD flux, the small dust in the upper layers of the atmosphere of the TW Hya disk were effectively depleted slightly(cite: Calahan21a) due to having a slightly lower flaring angle than the gas population. This was enough small dust depletion to reproduce the available $\textrm{CH}_{3}\textrm{CN}$ lines from Loomis et al. 2018a given a C/O ratio equal to 1.0 (see Figure [5](#fig:TWHya)). This disk is an additional piece of evidence supporting our evolved chemistry proposal.

## Implications on Other Molecules

This introduction of a late-stage photo-chemical equilibrium was motivated by observations of $\textrm{CH}_{3}\textrm{CN}$, $\textrm{HC}_{3}\textrm{N}$, and HCN. However, the late-stage chemistry would have an effect on other molecules as well. We predict in addition to these organic molecules, molecules such as C$_{X}$H, C$_{X}$H$_{2}$, and HC$_{X}$N will be abundant in the gas, enhanced by the cycle of carbon chemistry that reproduces observed $\textrm{CH}_{3}\textrm{CN}$ and $\textrm{HC}_{3}\textrm{N}$. The main carbon carrier, CO, is largely unaffected by the increase in photo-chemistry. CO is largely in the gas phase in previous models that do not include this ‘late-stage’ chemistry and in the region in which $\textrm{CH}_{3}\textrm{CN}$ was added into the gas, CO was already primarily in the gas phase. We find a slight depletion of CO in the upper atmosphere of the disk due to the CO photodissociation layer being pushed down, and there is a slight enhancement of CO in the midplane due to the UV-enhancement. However this accounts for less than 1% of the total abundance of CO thus did not have a strong impact on the modeled radial profiles. Another key molecule is H$_{2}$O. In our models, we do not initialize our model with H$_{2}$O, thus there is very little water to be affected by this ‘late-stage’ chemistry. Observational results of Du et al. 2017(cite: Du2017) support this as they found a low overall abundance in H$_{2}$O in disks with a survey of 13 protoplanetary disks. $\textrm{CH}_{3}\textrm{CN}$ nor $\textrm{HC}_{3}\textrm{N}$ would be seen to be at a high abundance if gas-phase H$_{2}$O was in high abundance in the disk as it would disrupt the carbon-rich chemistry.

## SED Degeneracy

The depletion of small grains will affect the observed spectral energy distribution (SED) from each disk. TW Hya’s dust population was not altered from that of Calahan et al. 2021a(cite: Calahan21a) and continues to match its observed SED. A depletion of a factor of 10 in the small dust population around HD 163296 would cause a dimming in the mid-infrared part of the SED. However, the small dust abundance, the distribution of dust grain size, and the assumed dust opacity sources are degenerate in the ways they may affect the disk SED. We modeled protoplanetary disk SEDs using the code TORUS(cite: Harries04; Harries19). TORUS is a Monte Carlo radiative transfer code utilizing radiative equilibrium(cite: Lucy99) and silicate grains(cite: Draine84). In Figure [11](#fig:SED_example), we show a series of SEDs produced from models motivated by our thermo-chemical model of HD 163296 including the stellar parameters and dust distribution in Table 1 from Calahan et al. 2021b(cite: Calahan21b). We find that by varying the minimum dust grain radius or the power law index, we can account for a factor of 10 in UV attenuation. The total population mass, grain size, and how the grain sizes are distributed are strongly degenerate and can result in uncertainties of the dust mass by a factor of at least 10. Thus our depletion of small dust continues to reproduce all previous observables including the SED.

## MRI Instability

With the increase in UV flux deeper into the disk, more ions are created. Ions can be coupled with the magnetic fields that thread through the disk and interact with the bulk gas creating turbulence. This mechanism is called the magneto-rotational instability or MRI(cite: Balbus91). Magneto-hydrodynamical processes are assumed to be present throughout protoplanetary disks due to young star’s active magnetic field, and are thought to be one of the main drivers of angular momentum transport (cite: Chandrasekhar60). An MRI-active zone may drive the bulk of the mass transportation in the disk and activate accretion onto the star, two vital processes that determine the future of a young solar system. It is thought that planet formation may be aided within ‘dead-zones’ where MRI is non-active(cite: Gressel12). The magnetic Reynolds number ($Re$) and ambipolar diffusion term ($Am$) are two quantities that help quantify the presence of an MRI-active zone. The Reynolds number quantifies the level of coupling between ionized gas and magnetic fields and is defined as

$$\begin{equation}
    Re \equiv \frac{c_{s}h}{D} \approx 1 \left(\frac{\chi_{e}}{10^{-13}}\right) \left(\frac{T}{100~\rm{K}}\right)^{1/2} \left(\frac{a}{\rm{AU}}\right)^{3/2} ,
\end{equation}$$

where $c_{s}$ is the sound speed, $h$ is the scale height of the disk, D is the magnetic diffusivity parameter, $\chi_{e}$ is the electron abundance, $T$ temperature and $a$ radial location in the disk (cite: Perez-Becker11). The ambipolar diffusion term describes the coupling of ionized molecules and their interaction with neutral gas particles:

$$\begin{equation}
    Am \equiv \frac{\chi_{i} n_{\rm{H}_{2}} \beta_{\rm{in}}}{\Omega} \approx 1 \left(\frac{\chi_{i}}{10^{-8}}\right) \left(\frac{n_{\rm{H}_{2}}}{10^{10}\rm{cm^{-3}}}\right) \left(\frac{a}{\rm{AU}}\right)^{3/2} ,
\end{equation}$$

where $\chi_{i}$ is the ion abundance, $n_{\rm{H}_{2}}$ is the number density of H$_{2}$ atoms, $\Omega$ is the dynamical time, $\beta_{\rm{in}}$ is the collisional rate coefficient for singly charged species to share momentum with neutral species, and $a$ is the radial location in the disk (cite: Draine83; Perez-Becker11). For MRI to act as a turbulent driver of neutral gas, both $Re$ and $Am$ must be sufficiently high. Simulations show that values between 0.1-100 for $Am$ can trigger significant coupling between ions and neutrals (cite: Hawley98; Bai11). Models by Flock et al. 2012(cite: Flock12) suggest $Re \approx$ 3,300-5,000 is required to sustain sufficient turbulence with a critical $Re$ = 3,000. In our work, we assume a combined $Am >$100 and $Re >$ 3,000 to signify an MRI-active zone.

We calculate the regions in which the MRI is active in the HD 163296 disk in our models with an early-stage physical environment and a late-stage environment (signified by a depletion in the small dust population mass) in Figure [8](#fig:AmRe). Our solution allows for an increase of UV flux in the atmosphere by a factor of 3-5. More of the disk becomes ion-rich due to the CO and H$_{2}$ self-shielding layers being located deeper into the disk. The increase in the ion and electron abundance ($\chi_{i}$, $\chi_{e}$) are the key factors that enhance the Re and Am values and thus produce additional MRI activity (see Figure [8](#fig:AmRe)). As a result, thirteen times more mass within the disk becomes MRI-active including within the midplane. In the base model representing early stages of disk chemistry, the MRI activity at the midplane extends to 4 au. By depleting the small dust population by an order of magnitude, the MRI activity at the midplane then extends out to $\sim$10 au. This increase in MRI activity can contribute to the reason behind why older disk systems, such as TW Hya, are actively accreting. Meridional flows have been identified in the HD 163296 disk located at two of the largest dust gaps (approx. 45 and 86 AU)(cite: Teague19_flows) and these vertical flows are coincident with the lower vertical limit of the MRI-active zone. The MRI activation could have an effect on the height or continue to drive meridional flows. Turbulence measurements of the HD 163296 disk have been derived in Flaherty et al. 2015 and 2017(cite: Flaherty15; Flaherty17) using molecular tracers, and they find turbulent velocities to be 5% or less of the sound speed between 30-300 au and at all measured heights. It is not yet clear whether our MRI prediction is in tension with the observational evidence of low turbulence in HD 163296, more work needs to be done on the modeling of how MRI-active regions drive turbulence and more observational constraints are needed to constrain the inner 40 au where we find the strongest MRI-activity.

## Supplementary Figures

![](figures/Supp_Figure1.pdf)

![](figures/Supp_Figure2.pdf)

![](figures/Supp_Figure3.pdf)

![](figures/Supp_Figure4.pdf)

![](figures/Supp_Figure5.pdf)

![](figures/Supp_Figure6.pdf)

![](figures/Supp_Figure7.pdf)

# Acknowledgements

Jenny Calahan is the corresponding author and can be contacted via jcalahan@umich.edu

J.K.C. acknowledges support from the National Science Foundation Graduate Research Fellowship under Grant No. DGE 1256260 and the National Aeronautics and Space Administration FINESST grant, under Grant no. 80NSSC19K1534. E.A.B. acknowledges support from NSF AAG Grant #1907653. A.D.B. acknowledges support from NSF AAG Grant #1907653. E.A.R. acknowledges support from NSF AST 1830728. Support for J. H. was provided by NASA through the NASA Hubble Fellowship grant #HST-HF2-51460.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555. This work was supported by a grant from the Simons Foundation 686302 and by an award from the Simons Foundation 321183FY19, KÖ. This material is based upon work supported by the National Science Foundation under Grant No. AST-1907832. J.D.I. acknowledges support from an STFC Ernest Rutherford Fellowship (ST/W004119/1) and a University Academic Fellowship from the University of Leeds. C.W. acknowledges financial support from the University of Leeds, the Science and Technology Facilities Council, and UK Research and Innovation (grant numbers ST/T000287/1 and MR/T040726/1). V.V.G. gratefully acknowledges support from FONDECYT Regular 1221352, ANID BASAL projects ACE210002 and FB210003, and ANID, – Millennium Science Initiative Program – NCN19_171.

We thank Tim Harries for help with and providing access to the TORUS modeling program.

# Data Availability

The data that support the findings of this study can be obtained as part of the MAPS program and are publicly available via alma-maps.info. Data regarding TW Hya can be obtained via data-rich figures in Calahan et al 2021 published on the online publication of the Astrophysical Journal article.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01055.L. and 2016.1.01046.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

# Code availability

This study relied on the following publicly available coding packages: rac2d: https://github.com/fjdu/rac-2d, RADMC-3D: https://www.ita.uni-heidelberg.de/ dullemond/software/radmc-3d/, and GoFish: https://github.com/richteague/gofish. TORUS is a private code developed by Tim Harries and collaborators.

97 urlstyle

(ref: Allen77) M. Allen and G. W. Robinson. *ApJ*, 212: 396–415, March 1977. doi: 10.1086/155059.

(ref: Anderson21) Dana E. Anderson, Geoffrey A. Blake, L. Ilsedore Cleeves, Edwin A. Bergin, Ke Zhang, Kamber R. Schwarz, Colette Salyk, and Arthur D. Bosman. . *ApJ*, 909 (1): 55, March 2021. doi: 10.3847/1538-4357/abd9c1.

(ref: Andrews18_dust) Sean M. Andrews and Tilman Birnstiel. . In Hans J. Deeg and Juan Antonio Belmonte, editors, *Handbook of Exoplanets*, page 136. 2018. doi: 10.1007/978-3-319-55333-7_136.

(ref: Andrews12) Sean M. Andrews, David J. Wilner, A. M. Hughes, Chunhua Qi, Katherine A. Rosenfeld, Karin I. Öberg, T. Birnstiel, Catherine Espaillat, Lucas A. Cieza, Jonathan P. Williams, Shin-Yi Lin, and Paul T. P. Ho. . *ApJ*, 744 (2): 162, January 2012. doi: 10.1088/0004-637X/744/2/162.

(ref: Andrews18) Sean M. Andrews, Jane Huang, Laura M. Pérez, Andrea Isella, Cornelis P. Dullemond, Nicolás T. Kurtovic, Viviana V. Guzmán, John M. Carpenter, David J. Wilner, Shangjia Zhang, Zhaohuan Zhu, Tilman Birnstiel, Xue-Ning Bai, Myriam Benisty, A. Meredith Hughes, Karin I. Öberg, and Luca Ricci. . *ApJL*, 869 (2): L41, December 2018. doi: 10.3847/2041-8213/aaf741.

(ref: Ansdell18) M. Ansdell, J. P. Williams, L. Trapman, S. E. van Terwisga, S. Facchini, C. F. Manara, N. van der Marel, A. Miotello, M. Tazzari, M. Hogerheijde, G. Guidi, L. Testi, and E. F. van Dishoeck. . *ApJ*, 859 (1): 21, May 2018. doi: 10.3847/1538-4357/aab890.

(ref: Asplund21) M. Asplund, A. M. Amarsi, and N. Grevesse. . *A&A*, 653: A141, September 2021. doi: 10.1051/0004-6361/202140445.

(ref: Bai11) Xue-Ning Bai and James M. Stone. . *ApJ*, 736 (2): 144, August 2011. doi: 10.1088/0004-637X/736/2/144.

(ref: Balbus91) Steven A. Balbus and John F. Hawley. . *ApJ*, 376: 214, July 1991. doi: 10.1086/170270.

(ref: Basalgete21) Romain Basalgète, Antonio Jesus Ocaña, Géraldine Féraud, Claire Romanzin, Laurent Philippe, Xavier Michaut, Jean-Hugues Fillion, and Mathieu Bertin. . *ApJ*, 922 (2): 213, December 2021. doi: 10.3847/1538-4357/ac2d93.

(ref: Bergin13) Edwin A. Bergin, L. Ilsedore Cleeves, Uma Gorti, Ke Zhang, Geoffrey A. Blake, Joel D. Green, Sean M. Andrews, II Evans, Neal J., Thomas Henning, and Karin Öberg. . *Nature*, 493 (7434): 644–646, Jan 2013. doi: 10.1038/nature11805.

(ref: Bergner21) Jennifer B. Bergner and Fred Ciesla. . *ApJ*, 919 (1): 45, September 2021. doi: 10.3847/1538-4357/ac0fd7.

(ref: Bergner18) Jennifer B. Bergner, Viviana G. Guzmán, Karin I. Öberg, Ryan A. Loomis, and Jamila Pegues. . *ApJ*, 857 (1): 69, April 2018. doi: 10.3847/1538-4357/aab664.

(ref: Bergner19) Jennifer B. Bergner, Karin I. Öberg, Edwin A. Bergin, Ryan A. Loomis, Jamila Pegues, and Chunhua Qi. . *ApJ*, 876 (1): 25, May 2019. doi: 10.3847/1538-4357/ab141e.

(ref: Bergner21a) Jennifer B. Bergner, Karin I. Öberg, Viviana V. Guzmán, Charles J. Law, Ryan A. Loomis, Gianni Cataldi, Arthur D. Bosman, Yuri Aikawa, Sean M. Andrews, Edwin A. Bergin, Alice S. Booth, L. Ilsedore Cleeves, Ian Czekala, Jane Huang, John D. Ilee, Romane Le Gal, Feng Long, Hideko Nomura, François Ménard, Chunhua Qi, Kamber R. Schwarz, Richard Teague, Takashi Tsukagoshi, Catherine Walsh, David J. Wilner, and Yoshihide Yamato. . *ApJS*, 257 (1): 11, November 2021. doi: 10.3847/1538-4365/ac143a.

(ref: Bergner22) Jennifer B. Bergner, Mahesh Rajappan, and Karin I. Öberg. . *ApJ*, 933 (2): 206, July 2022. doi: 10.3847/1538-4357/ac771e.

(ref: Birnstiel12) T. Birnstiel, S. M. Andrews, and B. Ercolano. *A&A*, 544: A79, August 2012. doi: 10.1051/0004-6361/201219262.

(ref: Birnstiel18) Tilman Birnstiel, Cornelis P. Dullemond, Zhaohuan Zhu, Sean M. Andrews, Xue-Ning Bai, David J. Wilner, John M. Carpenter, Jane Huang, Andrea Isella, Myriam Benisty, Laura M. Pérez, and Shangjia Zhang. . *ApJL*, 869 (2): L45, December 2018. doi: 10.3847/2041-8213/aaf743.

(ref: Booth21) Alice S. Booth, Benoı̂t Tabone, John D. Ilee, Catherine Walsh, Yuri Aikawa, Sean M. Andrews, Jaehan Bae, Edwin A. Bergin, Jennifer B. Bergner, Arthur D. Bosman, Jenny K. Calahan, Gianni Cataldi, L. Ilsedore Cleeves, Ian Czekala, Viviana V. Guzmán, Jane Huang, Charles J. Law, Romane Le Gal, Feng Long, Ryan A. Loomis, François Ménard, Hideko Nomura, Karin I. Öberg, Chunhua Qi, Kamber R. Schwarz, Richard Teague, Takashi Tsukagoshi, David J. Wilner, Yoshihide Yamato, and Ke Zhang. . *ApJS*, 257 (1): 16, November 2021. doi: 10.3847/1538-4365/ac1ad4.

(ref: Bosman18) Arthur D. Bosman, Catherine Walsh, and Ewine F. van Dishoeck. . *A&A*, 618: A182, October 2018. doi: 10.1051/0004-6361/201833497.

(ref: Bosman21a) Arthur D. Bosman, Felipe Alarcón, Edwin A. Bergin, Ke Zhang, Merel L. R. van’t Hoff, Karin I. Öberg, Viviana V. Guzmán, Catherine Walsh, Yuri Aikawa, Sean M. Andrews, Jennifer B. Bergner, Alice S. Booth, Gianni Cataldi, L. Ilsedore Cleeves, Ian Czekala, Kenji Furuya, Jane Huang, John D. Ilee, Charles J. Law, Romane Le Gal, Yao Liu, Feng Long, Ryan A. Loomis, François Ménard, Hideko Nomura, Chunhua Qi, Kamber R. Schwarz, Richard Teague, Takashi Tsukagoshi, Yoshihide Yamato, and David J. Wilner. . *ApJS*, 257 (1): 7, November 2021a. doi: 10.3847/1538-4365/ac1435.

(ref: Bosman_refrac) Arthur D. Bosman, Felipe Alarcón, Ke Zhang, and Edwin A. Bergin. . *ApJ*, 910 (1): 3, March 2021b. doi: 10.3847/1538-4357/abe127.

(ref: Brewer17) John M. Brewer, Debra A. Fischer, and Nikku Madhusudhan. . *AJ*, 153 (2): 83, February 2017. doi: 10.3847/1538-3881/153/2/83.

(ref: Calahan21a) Jenny K. Calahan, Edwin Bergin, Ke Zhang, Richard Teague, Ilsedore Cleeves, Jennifer Bergner, Geoffrey A. Blake, Paolo Cazzoletti, Viviana Guzmán, Michiel R. Hogerheijde, Jane Huang, Mihkel Kama, Ryan Loomis, Karin Öberg, Charlie Qi, Ewine F. van Dishoeck, Jeroen Terwisscha van Scheltinga, Catherine Walsh, and David Wilner. . *ApJ*, 908 (1): 8, February 2021a. doi: 10.3847/1538-4357/abd255.

(ref: Calahan21b) Jenny K. Calahan, Edwin A. Bergin, Ke Zhang, Kamber R. Schwarz, Karin I. Öberg, Viviana V. Guzmán, Catherine Walsh, Yuri Aikawa, Felipe Alarcón, Sean M. Andrews, Jaehan Bae, Jennifer B. Bergner, Alice S. Booth, Arthur D. Bosman, Gianni Cataldi, Ian Czekala, Jane Huang, John D. Ilee, Charles J. Law, Romane Le Gal, Feng Long, Ryan A. Loomis, François Ménard, Hideko Nomura, Chunhua Qi, Richard Teague, Merel L. R. van’t Hoff, David J. Wilner, and Yoshihide Yamato. . *ApJS*, 257 (1): 17, November 2021b. doi: 10.3847/1538-4365/ac143f.

(ref: Canta21) Alessandra Canta, Richard Teague, Romane Le Gal, and Karin I. Öberg. . *ApJ*, 922 (1): 62, November 2021. doi: 10.3847/1538-4357/ac23da.

(ref: Chandrasekhar60) S. Chandrasekhar. . *Proceedings of the National Academy of Science*, 46 (2): 253–257, February 1960. doi: 10.1073/pnas.46.2.253.

(ref: Chapillon12) Edwige Chapillon, Anne Dutrey, Stéphane Guilloteau, Vincent Piétu, Valentine Wakelam, Franck Hersant, Fréderic Gueth, Thomas Henning, Ralf Launhardt, Katharina Schreyer, and Dmitry Semenov. . *ApJ*, 756 (1): 58, September 2012. doi: 10.1088/0004-637X/756/1/58.

(ref: Cleeves21) L. Ilsedore Cleeves, Ryan A. Loomis, Richard Teague, Edwin A. Bergin, David J. Wilner, Jennifer B. Bergner, Geoffrey A. Blake, Jenny K. Calahan, Paolo Cazzoletti, Ewine F. van Dishoeck, Viviana V. Guzmán, Michiel R. Hogerheijde, Jane Huang, Mihkel Kama, Karin I. Öberg, Chunhua Qi, Jeroen Terwisscha van Scheltinga, and Catherine Walsh. . *ApJ*, 911 (1): 29, April 2021. doi: 10.3847/1538-4357/abe862.

(ref: Corazzi21) Maria Angela Corazzi, John Robert Brucato, Giovanni Poggiali, Linda Podio, Davide Fedele, and Claudio Codella. . *ApJ*, 913 (2): 128, June 2021. doi: 10.3847/1538-4357/abf6d3.

(ref: Czekala21) Ian Czekala, Ryan A. Loomis, Richard Teague, Alice S. Booth, Jane Huang, Gianni Cataldi, John D. Ilee, Charles J. Law, Catherine Walsh, Arthur D. Bosman, Viviana V. Guzmán, Romane Le Gal, Karin I. Öberg, Yoshihide Yamato, Yuri Aikawa, Sean M. Andrews, Jaehan Bae, Edwin A. Bergin, Jennifer B. Bergner, L. Ilsedore Cleeves, Nicolas T. Kurtovic, François Ménard, Hideko Nomura, Laura M. Pérez, Chunhua Qi, Kamber R. Schwarz, Takashi Tsukagoshi, Abygail R. Waggoner, David J. Wilner, and Ke Zhang. . *ApJS*, 257 (1): 2, November 2021. doi: 10.3847/1538-4365/ac1430.

(ref: Draine03) B. T. Draine. . *ARA&A*, 41: 241–289, January 2003. doi: 10.1146/annurev.astro.41.011802.094840.

(ref: Draine84) B. T. Draine and H. M. Lee. . *ApJ*, 285: 89, October 1984. doi: 10.1086/162480.

(ref: Draine83) B. T. Draine, W. G. Roberge, and A. Dalgarno. *ApJ*, 264: 485–507, January 1983. doi: 10.1086/160617.

(ref: Du14) Fujun Du and Edwin A. Bergin. . *ApJ*, 792 (1): 2, Sep 2014. doi: 10.1088/0004-637X/792/1/2.

(ref: Du2017) Fujun Du, Edwin Anthony Bergin, Michiel Hogerheijde, Ewine F. van Dishoeck, Geoff Blake, Simon Bruderer, Ilse Cleeves, Carsten Dominik, Davide Fedele, Dariusz C. Lis, Gary Melnick, David Neufeld, John Pearson, and Umut Yıldız. . *ApJ*, 842 (2): 98, June 2017. doi: 10.3847/1538-4357/aa70ee.

(ref: radmc3d) C. P. Dullemond, A. Juhasz, A. Pohl, F. Sereshti, R. Shetty, T. Peters, B. Commercon, and M. Flock. . Astrophysics Source Code Library, February 2012.

(ref: Flaherty15) Kevin M. Flaherty, A. Meredith Hughes, Katherine A. Rosenfeld, Sean M. Andrews, Eugene Chiang, Jacob B. Simon, Skylar Kerzner, and David J. Wilner. . *ApJ*, 813 (2): 99, November 2015. doi: 10.1088/0004-637X/813/2/99.

(ref: Flaherty17) Kevin M. Flaherty, A. Meredith Hughes, Sanaea C. Rose, Jacob B. Simon, Chunhua Qi, Sean M. Andrews, Ágnes Kóspál, David J. Wilner, Eugene Chiang, Philip J. Armitage, and Xue-ning Bai. . *ApJ*, 843 (2): 150, July 2017. doi: 10.3847/1538-4357/aa79f9.

(ref: Flock12) M. Flock, Th. Henning, and H. Klahr. . *ApJ*, 761 (2): 95, December 2012. doi: 10.1088/0004-637X/761/2/95.

(ref: Fuchs09) G. W. Fuchs, H. M. Cuppen, S. Ioppolo, C. Romanzin, S. E. Bisschop, S. Andersson, E. F. van Dishoeck, and H. Linnartz. . *A&A*, 505 (2): 629–639, October 2009. doi: 10.1051/0004-6361/200810784.

(ref: Gaia18) Gaia Collaboration, A. G. A. Brown, A. Vallenari, T. Prusti, J. H. J. de Bruijne, C. Babusiaux, C. A. L. Bailer-Jones, M. Biermann, D. W. Evans, L. Eyer, F. Jansen, C. Jordi, S. A. Klioner, U. Lammers, L. Lindegren, X. Luri, F. Mignard, C. Panem, D. Pourbaix, S. Randich, P. Sartoretti, H. I. Siddiqui, C. Soubiran, F. van Leeuwen, N. A. Walton, F. Arenou, U. Bastian, M. Cropper, R. Drimmel, D. Katz, M. G. Lattanzi, J. Bakker, C. Cacciari, J. Castañeda, L. Chaoul, N. Cheek, F. De Angeli, C. Fabricius, R. Guerra, B. Holl, E. Masana, R. Messineo, N. Mowlavi, K. Nienartowicz, P. Panuzzo, J. Portell, M. Riello, G. M. Seabroke, P. Tanga, F. Thévenin, G. Gracia-Abril, G. Comoretto, M. Garcia-Reinaldos, D. Teyssier, M. Altmann, R. Andrae, M. Audard, I. Bellas-Velidis, K. Benson, J. Berthier, R. Blomme, P. Burgess, G. Busso, B. Carry, A. Cellino, G. Clementini, M. Clotet, O. Creevey, M. Davidson, J. De Ridder, L. Delchambre, A. Dell’Oro, C. Ducourant, J. Fernández-Hernández, M. Fouesneau, Y. Frémat, L. Galluccio, M. Garcı́a-Torres, J. González-Núñez, J. J. González-Vidal, E. Gosset, L. P. Guy, J. L. Halbwachs, N. C. Hambly, D. L. Harrison, J. Hernández, D. Hestroffer, S. T. Hodgkin, A. Hutton, G. Jasniewicz, A. Jean-Antoine-Piccolo, S. Jordan, A. J. Korn, A. Krone-Martins, A. C. Lanzafame, T. Lebzelter, W. Löffler, M. Manteiga, P. M. Marrese, J. M. Martı́n-Fleitas, A. Moitinho, A. Mora, K. Muinonen, J. Osinde, E. Pancino, T. Pauwels, J. M. Petit, A. Recio-Blanco, P. J. Richards, L. Rimoldini, A. C. Robin, L. M. Sarro, C. Siopis, M. Smith, A. Sozzetti, M. Süveges, J. Torra, W. van Reeven, U. Abbas, A. Abreu Aramburu, S. Accart, C. Aerts, G. Altavilla, M. A. Álvarez, R. Alvarez, J. Alves, R. I. Anderson, A. H. Andrei, E. Anglada Varela, E. Antiche, T. Antoja, B. Arcay, T. L. Astraatmadja, N. Bach, S. G. Baker, L. Balaguer-Núñez, P. Balm, C. Barache, C. Barata, D. Barbato, F. Barblan, P. S. Barklem, D. Barrado, M. Barros, M. A. Barstow, S. Bartholomé Muñoz, J. L. Bassilana, U. Becciani, M. Bellazzini, A. Berihuete, S. Bertone, L. Bianchi, O. Bienaymé, S. Blanco-Cuaresma, T. Boch, C. Boeche, A. Bombrun, R. Borrachero, D. Bossini, S. Bouquillon, G. Bourda, A. Bragaglia, L. Bramante, M. A. Breddels, A. Bressan, N. Brouillet, T. Brüsemeister, E. Brugaletta, B. Bucciarelli, A. Burlacu, D. Busonero, A. G. Butkevich, R. Buzzi, E. Caffau, R. Cancelliere, G. Cannizzaro, T. Cantat-Gaudin, R. Carballo, T. Carlucci, J. M. Carrasco, L. Casamiquela, M. Castellani, A. Castro-Ginard, P. Charlot, L. Chemin, A. Chiavassa, G. Cocozza, G. Costigan, S. Cowell, F. Crifo, M. Crosta, C. Crowley, J. Cuypers, C. Dafonte, Y. Damerdji, A. Dapergolas, P. David, M. David, P. de Laverny, F. De Luise, R. De March, D. de Martino, R. de Souza, A. de Torres, J. Debosscher, E. del Pozo, M. Delbo, A. Delgado, H. E. Delgado, P. Di Matteo, S. Diakite, C. Diener, E. Distefano, C. Dolding, P. Drazinos, J. Durán, B. Edvardsson, H. Enke, K. Eriksson, P. Esquej, G. Eynard Bontemps, C. Fabre, M. Fabrizio, S. Faigler, A. J. Falcão, M. Farràs Casas, L. Federici, G. Fedorets, P. Fernique, F. Figueras, F. Filippi, K. Findeisen, A. Fonti, E. Fraile, M. Fraser, B. Frézouls, M. Gai, S. Galleti, D. Garabato, F. Garcı́a-Sedano, A. Garofalo, N. Garralda, A. Gavel, P. Gavras, J. Gerssen, R. Geyer, P. Giacobbe, G. Gilmore, S. Girona, G. Giuffrida, F. Glass, M. Gomes, M. Granvik, A. Gueguen, A. Guerrier, J. Guiraud, R. Gutiérrez-Sánchez, R. Haigron, D. Hatzidimitriou, M. Hauser, M. Haywood, U. Heiter, A. Helmi, J. Heu, T. Hilger, D. Hobbs, W. Hofmann, G. Holland, H. E. Huckle, A. Hypki, V. Icardi, K. Janßen, G. Jevardat de Fombelle, P. G. Jonker, Á. L. Juhász, F. Julbe, A. Karampelas, A. Kewley, J. Klar, A. Kochoska, R. Kohley, K. Kolenberg, M. Kontizas, E. Kontizas, S. E. Koposov, G. Kordopatis, Z. Kostrzewa-Rutkowska, P. Koubsky, S. Lambert, A. F. Lanza, Y. Lasne, J. B. Lavigne, Y. Le Fustec, C. Le Poncin-Lafitte, Y. Lebreton, S. Leccia, N. Leclerc, I. Lecoeur-Taibi, H. Lenhardt, F. Leroux, S. Liao, E. Licata, H. E. P. Lindstrøm, T. A. Lister, E. Livanou, A. Lobel, M. López, S. Managau, R. G. Mann, G. Mantelet, O. Marchal, J. M. Marchant, M. Marconi, S. Marinoni, G. Marschalkó, D. J. Marshall, M. Martino, G. Marton, N. Mary, D. Massari, G. Matijevič, T. Mazeh, P. J. McMillan, S. Messina, D. Michalik, N. R. Millar, D. Molina, R. Molinaro, L. Molnár, P. Montegriffo, R. Mor, R. Morbidelli, T. Morel, D. Morris, A. F. Mulone, T. Muraveva, I. Musella, G. Nelemans, L. Nicastro, L. Noval, W. O’Mullane, C. Ordénovic, D. Ordóñez-Blanco, P. Osborne, C. Pagani, I. Pagano, F. Pailler, H. Palacin, L. Palaversa, A. Panahi, M. Pawlak, A. M. Piersimoni, F. X. Pineau, E. Plachy, G. Plum, E. Poggio, E. Poujoulet, A. Prša, L. Pulone, E. Racero, S. Ragaini, N. Rambaux, M. Ramos-Lerate, S. Regibo, C. Reylé, F. Riclet, V. Ripepi, A. Riva, A. Rivard, G. Rixon, T. Roegiers, M. Roelens, M. Romero-Gómez, N. Rowell, F. Royer, L. Ruiz-Dern, G. Sadowski, T. Sagristà Sellés, J. Sahlmann, J. Salgado, E. Salguero, N. Sanna, T. Santana-Ros, M. Sarasso, H. Savietto, M. Schultheis, E. Sciacca, M. Segol, J. C. Segovia, D. Ségransan, I. C. Shih, L. Siltala, A. F. Silva, R. L. Smart, K. W. Smith, E. Solano, F. Solitro, R. Sordo, S. Soria Nieto, J. Souchay, A. Spagna, F. Spoto, U. Stampa, I. A. Steele, H. Steidelmüller, C. A. Stephenson, H. Stoev, F. F. Suess, J. Surdej, L. Szabados, E. Szegedi-Elek, D. Tapiador, F. Taris, G. Tauran, M. B. Taylor, R. Teixeira, D. Terrett, P. Teyssand ier, W. Thuillot, A. Titarenko, F. Torra Clotet, C. Turon, A. Ulla, E. Utrilla, S. Uzzi, M. Vaillant, G. Valentini, V. Valette, A. van Elteren, E. Van Hemelryck, M. van Leeuwen, M. Vaschetto, A. Vecchiato, J. Veljanoski, Y. Viala, D. Vicente, S. Vogt, C. von Essen, H. Voss, V. Votruba, S. Voutsinas, G. Walmsley, M. Weiler, O. Wertz, T. Wevers, Ł. Wyrzykowski, A. Yoldas, M. Žerjal, H. Ziaeepour, J. Zorec, S. Zschocke, S. Zucker, C. Zurbach, and T. Zwitter. . *A&A*, 616: A1, Aug 2018. doi: 10.1051/0004-6361/201833051.

(ref: Gammie96) Charles F. Gammie and Eve C. Ostriker. *ApJ*, 466: 814, August 1996. doi: 10.1086/177556.

(ref: Goldsmith99) Paul F. Goldsmith and William D. Langer. . *ApJ*, 517 (1): 209–225, May 1999. doi: 10.1086/307195.

(ref: Goumans08) T. P. M. Goumans, Madeeha A. Uppal, and Wendy A. Brown. . *MNRAS*, 384 (3): 1158–1164, March 2008. doi: 10.1111/j.1365-2966.2007.12788.x.

(ref: Gressel12) Oliver Gressel, Richard P. Nelson, and Neal J. Turner. . *MNRAS*, 422 (2): 1140–1159, May 2012. doi: 10.1111/j.1365-2966.2012.20701.x.

(ref: Guzman21) Viviana V. Guzmán, Jennifer B. Bergner, Charles J. Law, Karin I. Öberg, Catherine Walsh, Gianni Cataldi, Yuri Aikawa, Edwin A. Bergin, Ian Czekala, Jane Huang, Sean M. Andrews, Ryan A. Loomis, Ke Zhang, Romane Le Gal, Felipe Alarcón, John D. Ilee, Richard Teague, L. Ilsedore Cleeves, David J. Wilner, Feng Long, Kamber R. Schwarz, Arthur D. Bosman, Laura M. Pérez, François Ménard, and Yao Liu. . *ApJS*, 257 (1): 6, November 2021. doi: 10.3847/1538-4365/ac1440.

(ref: Haisch01) Jr. Haisch, Karl E., Elizabeth A. Lada, and Charles J. Lada. . *ApJL*, 553 (2): L153–L156, June 2001. doi: 10.1086/320685.

(ref: Harries04) T. J. Harries, J. D. Monnier, N. H. Symington, and R. K͡urosawa. . , 350: 565–574, May 2004. doi: 10.1111/j.1365-2966.2004.07668.x.

(ref: Harries19) T. J. Harries, T. J. Haworth, D. Acreman, A. Ali, and T. Douglas. . *Astronomy and Computing*, 27: 63, April 2019. doi: 10.1016/j.ascom.2019.03.002.

(ref: Hasegawa92) Tatsuhiko I. Hasegawa, Eric Herbst, and Chun M. Leung. . *ApJS*, 82: 167, September 1992. doi: 10.1086/191713.

(ref: Hawley98) John F. Hawley and James M. Stone. . *ApJ*, 501 (2): 758–771, July 1998. doi: 10.1086/305849.

(ref: Henning96) T. Henning and R. Stognienko. *A&A*, 311: 291–303, July 1996.

(ref: Huang18) Jane Huang, Sean M. Andrews, L. Ilsedore Cleeves, Karin I. Öberg, David J. Wilner, Xuening Bai, Til Birnstiel, John Carpenter, A. Meredith Hughes, Andrea Isella, Laura M. Pérez, Luca Ricci, and Zhaohuan Zhu. . *ApJ*, 852 (2): 122, January 2018. doi: 10.3847/1538-4357/aaa1e7.

(ref: Ilee21) John D. Ilee, Catherine Walsh, Alice S. Booth, Yuri Aikawa, Sean M. Andrews, Jaehan Bae, Edwin A. Bergin, Jennifer B. Bergner, Arthur D. Bosman, Gianni Cataldi, L. Ilsedore Cleeves, Ian Czekala, Viviana V. Guzmán, Jane Huang, Charles J. Law, Romane Le Gal, Ryan A. Loomis, François Ménard, Hideko Nomura, Karin I. Öberg, Chunhua Qi, Kamber R. Schwarz, Richard Teague, Takashi Tsukagoshi, David J. Wilner, Yoshihide Yamato, and Ke Zhang. . *ApJS*, 257 (1): 9, November 2021. doi: 10.3847/1538-4365/ac1441.

(ref: Ioppolo08) S. Ioppolo, H. M. Cuppen, C. Romanzin, E. F. van Dishoeck, and H. Linnartz. . *ApJ*, 686 (2): 1474–1479, October 2008. doi: 10.1086/591506.

(ref: Ioppolo10) S. Ioppolo, H. M. Cuppen, C. Romanzin, E. F. van Dishoeck, and H. Linnartz. . *Physical Chemistry Chemical Physics (Incorporating Faraday Transactions)*, 12 (38): 12065, January 2010. doi: 10.1039/C0CP00250J.

(ref: Isella18) Andrea Isella, Jane Huang, Sean M. Andrews, Cornelis P. Dullemond, Tilman Birnstiel, Shangjia Zhang, Zhaohuan Zhu, Viviana V. Guzmán, Laura M. Pérez, Xue-Ning Bai, Myriam Benisty, John M. Carpenter, Luca Ricci, and David J. Wilner. . *ApJL*, 869 (2): L49, December 2018. doi: 10.3847/2041-8213/aaf747.

(ref: Johansen17) Anders Johansen and Michiel Lambrechts. . *Annual Review of Earth and Planetary Sciences*, 45 (1): 359–387, August 2017. doi: 10.1146/annurev-earth-063016-020226.

(ref: Kastner18) Joel H. Kastner, C. Qi, D. A. Dickson-Vandervelde, P. Hily-Blant, T. Forveille, S. Andrews, U. Gorti, K. Öberg, and D. Wilner. . *ApJ*, 863 (1): 106, August 2018. doi: 10.3847/1538-4357/aacff7.

(ref: Krijt18) Sebastiaan Krijt, Kamber R. Schwarz, Edwin A. Bergin, and Fred J. Ciesla. . *ApJ*, 864 (1): 78, September 2018. doi: 10.3847/1538-4357/aad69b.

(ref: Lambrechts14) M. Lambrechts, A. Johansen, and A. Morbidelli. . *A&A*, 572: A35, December 2014. doi: 10.1051/0004-6361/201423814.

(ref: Law21rad) Charles J. Law, Ryan A. Loomis, Richard Teague, Karin I. Öberg, Ian Czekala, Sean M. Andrews, Jane Huang, Yuri Aikawa, Felipe Alarcón, Jaehan Bae, Edwin A. Bergin, Jennifer B. Bergner, Yann Boehler, Alice S. Booth, Arthur D. Bosman, Jenny K. Calahan, Gianni Cataldi, L. Ilsedore Cleeves, Kenji Furuya, Viviana V. Guzmán, John D. Ilee, Romane Le Gal, Yao Liu, Feng Long, François Ménard, Hideko Nomura, Chunhua Qi, Kamber R. Schwarz, Anibal Sierra, Takashi Tsukagoshi, Yoshihide Yamato, Merel L. R. van’t Hoff, Catherine Walsh, David J. Wilner, and Ke Zhang. . *ApJS*, 257 (1): 3, November 2021a. doi: 10.3847/1538-4365/ac1434.

(ref: Law21emit) Charles J. Law, Richard Teague, Ryan A. Loomis, Jaehan Bae, Karin I. Öberg, Ian Czekala, Sean M. Andrews, Yuri Aikawa, Felipe Alarcón, Edwin A. Bergin, Jennifer B. Bergner, Alice S. Booth, Arthur D. Bosman, Jenny K. Calahan, Gianni Cataldi, L. Ilsedore Cleeves, Kenji Furuya, Viviana V. Guzmán, Jane Huang, John D. Ilee, Romane Le Gal, Yao Liu, Feng Long, François Ménard, Hideko Nomura, Laura M. Pérez, Chunhua Qi, Kamber R. Schwarz, Daniela Soto, Takashi Tsukagoshi, Yoshihide Yamato, Merel L. R. van’t Hoff, Catherine Walsh, David J. Wilner, and Ke Zhang. . *ApJS*, 257 (1): 4, November 2021b. doi: 10.3847/1538-4365/ac1439.

(ref: LeGal19) Romane Le Gal, Madison T. Brady, Karin I. Öberg, Evelyne Roueff, and Franck Le Petit. . *ApJ*, 886 (2): 86, December 2019. doi: 10.3847/1538-4357/ab4ad9.

(ref: Loomis18) Ryan A. Loomis, L. Ilsedore Cleeves, Karin I. Öberg, Yuri Aikawa, Jennifer Bergner, Kenji Furuya, V. V. Guzman, and Catherine Walsh. . *ApJ*, 859 (2): 131, June 2018. doi: 10.3847/1538-4357/aac169.

(ref: Lucy99) L. B. Lucy. . *A&A*, 344: 282–288, April 1999.

(ref: Lynden-Bell74) D. Lynden-Bell and J. E. Pringle. *MNRAS*, 168: 603–637, Sep 1974. doi: 10.1093/mnras/168.3.603.

(ref: Mathis77) J. S. Mathis, W. Rumpl, and K. H. Nordsieck. *ApJ*, 217: 425–433, October 1977. doi: 10.1086/155591.

(ref: McElroy13) D. McElroy, C. Walsh, A. J. Markwick, M. A. Cordiner, K. Smith, and T. J. Millar. . *A&A*, 550: A36, February 2013. doi: 10.1051/0004-6361/201220465.

(ref: McMullin07) J. P. McMullin, B. Waters, D. Schiebel, W. Young, and K. Golap. . In R. A. Shaw, F. Hill, and D. J. Bell, editors, *Astronomical Data Analysis Software and Systems XVI*, volume 376 of *Astronomical Society of the Pacific Conference Series*, page 127, October 2007.

(ref: Miotello19) A. Miotello, S. Facchini, E. F. van Dishoeck, P. Cazzoletti, L. Testi, J. P. Williams, M. Ansdell, S. van Terwisga, and N. van der Marel. . *A&A*, 631: A69, November 2019. doi: 10.1051/0004-6361/201935441.

(ref: Miotello22) A. Miotello, I. Kamp, T. Birnstiel, L. I. Cleeves, and A. Kataoka. . *arXiv e-prints*, art. arXiv:2203.09818, March 2022.

(ref: Muller01) H. S. P. Müller, S. Thorwirth, D. A. Roth, and G. Winnewisser. . *A&A*, 370: L49–L52, April 2001. doi: 10.1051/0004-6361:20010367.

(ref: Muller05) Holger S. P. Müller, Frank Schlöder, Jürgen Stutzki, and Gisbert Winnewisser. . *Journal of Molecular Structure*, 742 (1-3): 215–227, May 2005. doi: 10.1016/j.molstruc.2005.01.027.

(ref: Najita11) Joan R. Najita, Máté Ádámkovics, and Alfred E. Glassgold. . *ApJ*, 743 (2): 147, December 2011. doi: 10.1088/0004-637X/743/2/147.

(ref: Oba12) Y. Oba, N. Watanabe, T. Hama, K. Kuwahata, H. Hidaka, and A. Kouchi. . *ApJ*, 749 (1): 67, April 2012. doi: 10.1088/0004-637X/749/1/67.

(ref: Oberg11ice) Karin I. Öberg, A. C. Adwin Boogert, Klaus M. Pontoppidan, Saskia van den Broek, Ewine F. van Dishoeck, Sandrine Bottinelli, Geoffrey A. Blake, and II Evans, Neal J. . *ApJ*, 740 (2): 109, October 2011. doi: 10.1088/0004-637X/740/2/109.

(ref: Oberg15) Karin I. Öberg, Viviana V. Guzmán, Kenji Furuya, Chunhua Qi, Yuri Aikawa, Sean M. Andrews, Ryan Loomis, and David J. Wilner. . *Nature*, 520 (7546): 198–201, April 2015. doi: 10.1038/nature14276.

(ref: Oberg21) Karin I. Öberg, Viviana V. Guzmán, Catherine Walsh, Yuri Aikawa, Edwin A. Bergin, Charles J. Law, Ryan A. Loomis, Felipe Alarcón, Sean M. Andrews, Jaehan Bae, Jennifer B. Bergner, Yann Boehler, Alice S. Booth, Arthur D. Bosman, Jenny K. Calahan, Gianni Cataldi, L. Ilsedore Cleeves, Ian Czekala, Kenji Furuya, Jane Huang, John D. Ilee, Nicolas T. Kurtovic, Romane Le Gal, Yao Liu, Feng Long, François Ménard, Hideko Nomura, Laura M. Pérez, Chunhua Qi, Kamber R. Schwarz, Anibal Sierra, Richard Teague, Takashi Tsukagoshi, Yoshihide Yamato, Merel L. R. van’t Hoff, Abygail R. Waggoner, David J. Wilner, and Ke Zhang. . *ApJS*, 257 (1): 1, November 2021. doi: 10.3847/1538-4365/ac1432.

(ref: Perez-Becker11) Daniel Perez-Becker and Eugene Chiang. . *ApJ*, 735 (1): 8, July 2011. doi: 10.1088/0004-637X/735/1/8.

(ref: Powner09) Matthew W. Powner, Béatrice Gerland, and John D. Sutherland. . *Nature*, 459 (7244): 239–242, May 2009. doi: 10.1038/nature08013.

(ref: Ritson12) Dougal Ritson and John D. Sutherland. . *Nature Chemistry*, 4 (11): 895–899, November 2012. doi: 10.1038/nchem.1467.

(ref: Ruffle01) Deborah P. Ruffle and Eric Herbst. . *MNRAS*, 324 (4): 1054–1062, July 2001. doi: 10.1046/j.1365-8711.2001.04394.x.

(ref: Schoier05) F. L. Schöier, F. F. S. van der Tak, E. F. van Dishoeck, and J. H. Black. . *A&A*, 432 (1): 369–379, March 2005. doi: 10.1051/0004-6361:20041729.

(ref: Schwarz18_1) Kamber R. Schwarz, Edwin A. Bergin, L. Ilsedore Cleeves, Ke Zhang, Karin I. Öberg, Geoffrey A. Blake, and Dana Anderson. . *ApJ*, 856 (1): 85, March 2018. doi: 10.3847/1538-4357/aaae08.

(ref: Sutherland15) John D. Sutherland. . *Angewandte Chemie*, 55 (1): 104–121, October 2015. doi: 10.1002/anie.201506585.

(ref: GoFish) Richard Teague. Gofish: Fishing for line observations in protoplanetary disks. *The Journal of Open Source Software*, 4 (41): 1632, sep 2019. doi: 10.21105/joss.01632. URL `https://doi.org/10.21105/joss.01632`.

(ref: Teague19_flows) Richard Teague, Jaehan Bae, and Edwin A. Bergin. . *Nature*, 574 (7778): 378–381, October 2019. doi: 10.1038/s41586-019-1642-0.

(ref: Thi10) W. F. Thi, G. Mathews, F. Ménard, P. Woitke, G. Meeus, P. Riviere-Marichalar, C. Pinte, C. D. Howard, A. Roberge, G. Sandell, I. Pascucci, B. Riaz, C. A. Grady, W. R. F. Dent, I. Kamp, G. Duchêne, J. C. Augereau, E. Pantin, B. Vandenbussche, I. Tilling, J. P. Williams, C. Eiroa, D. Barrado, J. M. Alacid, S. Andrews, D. R. Ardila, G. Aresu, S. Brittain, D. R. Ciardi, W. Danchi, D. Fedele, I. de Gregorio-Monsalvo, A. Heras, N. Huelamo, A. Krivov, J. Lebreton, R. Liseau, C. Martin-Zaidi, I. Mendigutı́a, B. Montesinos, A. Mora, M. Morales-Calderon, H. Nomura, N. Phillips, L. Podio, D. R. Poelman, S. Ramsay, K. Rice, E. Solano, H. Walker, G. J. White, and G. Wright. . *A&A*, 518: L125, July 2010. doi: 10.1051/0004-6361/201014578.

(ref: VanClepper22) Eric Van Clepper, Jennifer B. Bergner, Arthur D. Bosman, Edwin Bergin, and Fred J. Ciesla. . *ApJ*, 927 (2): 206, March 2022. doi: 10.3847/1538-4357/ac511b.

(ref: Vasyunin13) A. I. Vasyunin and Eric Herbst. . *ApJ*, 769 (1): 34, May 2013. doi: 10.1088/0004-637X/769/1/34.

(ref: Walsh14) Catherine Walsh, Tom. J. Millar, Hideko Nomura, Eric Herbst, Susanna Widicus Weaver, Yuri Aikawa, Jacob C. Laas, and Anton I. Vasyunin. . *A&A*, 563: A33, March 2014. doi: 10.1051/0004-6361/201322446.

(ref: Warren08) Stephen G. Warren and Richard E. Brandt. . *Journal of Geophysical Research (Atmospheres)*, 113 (D14): D14220, July 2008. doi: 10.1029/2007JD009744.

(ref: Woitke09) P. Woitke, I. Kamp, and W. F. Thi. . *A&A*, 501 (1): 383–406, July 2009. doi: 10.1051/0004-6361/200911821.

(ref: Xie21) C. Xie, S. Y. Haffert, J. de Boer, M. A. Kenworthy, J. Brinchmann, J. Girard, I. A. G. Snellen, and C. U. Keller. . *A&A*, 650: L6, June 2021. doi: 10.1051/0004-6361/202140602.

(ref: Zhang21) Ke Zhang, Alice S. Booth, Charles J. Law, Arthur D. Bosman, Kamber R. Schwarz, Edwin A. Bergin, Karin I. Öberg, Sean M. Andrews, Viviana V. Guzmán, Catherine Walsh, Chunhua Qi, Merel L. R. van’t Hoff, Feng Long, David J. Wilner, Jane Huang, Ian Czekala, John D. Ilee, Gianni Cataldi, Jennifer B. Bergner, Yuri Aikawa, Richard Teague, Jaehan Bae, Ryan A. Loomis, Jenny K. Calahan, Felipe Alarcón, François Ménard, Romane Le Gal, Anibal Sierra, Yoshihide Yamato, Hideko Nomura, Takashi Tsukagoshi, Laura M. Pérez, Leon Trapman, Yao Liu, and Kenji Furuya. . *ApJS*, 257 (1): 5, November 2021. doi: 10.3847/1538-4365/ac1580.

</paper>

Write the methods card for this paper.