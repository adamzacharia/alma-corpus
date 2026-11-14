# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025SciA...11.6953M\sonnetcc\reply.txt

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
 "bibcode": "2025SciA...11.6953M",
 "title": "A misaligned protostellar disk fed by gas streamers in a barred spiral-like massive dense core",
 "year": 2025,
 "journal": "Science Advances",
 "first_author": "Mai, Xiaofeng",
 "n_authors": 45,
 "arxiv_id": "2509.15527",
 "doi": "10.1126/sciadv.ady6953",
 "alma_projects_linked_by_archive": []
}
```

Paper text:
<paper>
# A misaligned protostellar disk fed by gas streamers in a barred spiral-like massive dense core

High-mass stars, born in massive dense cores (MDCs), profoundly impact the cosmic ecosystem through feedback processes and metal enrichment, yet little is known about how MDCs assemble and transfer mass across scales to form high-mass young stellar objects (HMYSOs). Using multi-scale (40–2500 au) observations of an MDC hosting an HMYSO, we identify a coherent dynamical structure analogous to barred spiral galaxies: three $\sim$20,000 au spiral arms feed a $\sim$7,500 au central bar, which channels gas to a $\sim$2,000 au pseudodisk. Further accretion proceeds through the inner structures, including a Keplerian disk and an inner disk ($\sim$100 au), which are thought to be driving a collimated bipolar outflow. This is the first time that these multi-scale structures (spiral arms, bar, streamers, envelope, disk, and outflow) have been simultaneously observed as a physically coherent structure within an MDC. Our discovery suggests that well-organized hierarchical structures play a crucial role during the gas accretion and angular momentum build-up of a massive disk.

High-mass stars are known to form within clustered environment *(cite: Tan2014,Krum2014,2018ARA&A..56...41M,2019ARA&A..57..227K)* and the references therein). Unlike their low-mass solar-type siblings that form from the monolithic collapse of a well-defined pre-stellar core *(cite: 1987ARA&A..25...23S, 2003ApJ...585..850M, 2011A&A...527A.135C)*, the formation of the massive stars relies on multi-scale accretion from much larger ($\sim$0.1–1 pc) gas reservoirs, called massive dense cores (MDCs) *(cite: 2018ARA&A..56...41M)*. The MDCs themselves may also continuously accrete gas from their natal clouds through larger-scale ($\sim$1-10 pc) hierarchical gas structures such as filament-hub systems *(cite: 2013A&A...555A.112P,2022MNRAS.514.6038Z, 2024A&A...686A.146Z)*. However, the formation of gas structures within MDCs and their roles in protostellar mass growth remains elusive. In addition, due to the low number statistics *(cite: 2016A&ARv..24....6B,2019NatAs...3..517Z,2022NatAs...6..837L,2017NatPh..13..276C, 2023ApJ...959L..31O,2024Natur.625...55M)*, it is still under debate whether stable disks widely exist in the surroundings of HMYSOs. Therefore, understanding how mass is assembled and transferred across scales to massive disks is essential to constraining the physical mechanisms that govern high-mass star formation, including angular momentum regulation and disk evolution.

At a distance of 1.25 kpc from the Sun *(cite: 2014A&A...566A..17W)*, MDC IRAS 18134-1942 (G11.497-1.485, hereafter I18134) is a massive cloud core containing a UC Hii region *(cite: 2003MNRAS.341..270V)*, with a gas mass of 238 $M_{\odot}$ enclosed in a radius of $\sim0.23$ pc *(cite: 2018MNRAS.473.1059U)*. This MDC hosts strong, highly variable Class II methanol *(cite: 1993MNRAS.261..783S, 2005A&A...432..737P, 2010A&A...517A..56F,2000A&A...360..311S, 2004AJ....127.3479G, 2024A&A...684A..86B)* and water maser emission *(cite: 1991A&A...246..249P, 2007PASJ...59.1185S, 1996A&A...311..971C, 2010MNRAS.406.1487B)*. In particular, an intense flare of the 6.7 GHz methanol maser was detected recently, increasing by more than a factor of 10 over a four month period, indicating active high-mass star formation associated with possible intense accretion bursts *(cite: 2024A&A...684A..86B)*.

We observed the source using the Atacama Large Millimeter/submillimeter Array (ALMA) at 3 mm (Band 3, Fig. [1](#cont_b3_b6)A) and 1.3 mm (Band 6, Fig. [1](#cont_b3_b6)B and [2](#dcn_con_streamer)) wavelengths.

At resolutions of 0.03$^{\prime\prime}$–2$^{\prime\prime}$, corresponding to 37–2400 au at the source distance, we discover a remarkable “spirals-bar-disk-outflow” complex in this MDC.

Thermal molecular line emission in conjunction with the Class II methanol masers reveals a pseudodisk (or a rotating and infalling envelope, Fig. [3](#com_obs_model)) and a Keplerian disk surrounding the embedded HMYSO (Fig. [4](#maserdisk)), which drives a bipolar outflow. The pseudodisk and the disk are fed by gas streamers that are embedded in a $\sim$7,500 au long bar-like structure (“bar"). The “bar" is connected to three prominent $\sim$20,000 au long spiral arms as revealed by the 3 mm continuum emission. This discovery provides unprecedented insights into the complex interplay between the accretion disk and the hierarchical structures beyond it (Fig. [5](#cartoon)).\
\

ALMA 3 mm observations of continuum emission (Fig. [1](#cont_b3_b6)A and Fig. [6](#b3cont_spiral)) and molecular lines of $\rm H^{13}CO^+$ and CCH (Fig. [7](#spiral_h13cop)) reveal a distinct spiral system in I18134 that appears to channel material from beyond 20,000 au down to the central gravitational potential well. While spiral-arm-like structures induced by gravitational instability or by external perturbation such as flyby encounters are often witnessed in protostellar disks *(cite: 2020NatAs...4..142L,2020NatAs...4.1170C,2022NatAs...6..837L,2023NatAs...7..557B,2024Natur.633...58S)*, well-organized spiral arms in MDCs are rarely seen, with only a few candidates reported *(cite: 2015ApJ...804...37L,2021ApJ...915L..10S,2022ApJ...941...51H,2023MNRAS.520.3259X,2023ApJ...959L..31O,2024MNRAS.530.1956S)*.

Three prominent dusty spiral arms are visible in 3 mm continuum emission and can be modeled as logarithmic spirals (Materials & Methods; see Fig. [6](#b3cont_spiral)), which are further confirmed in molecular line emission (see Fig. [7](#spiral_h13cop)). One (S4) and two (S7-8) additional spiral arms can be identified in $\rm H^{13}CO^+$ and CCH, respectively, trailing in the same direction as the dusty arms (see Fig. [7](#spiral_h13cop)). Besides, four more spiral-like structures (S5, S6, S9, S10) are recognizable visually in $\rm H^{13}CO^+$ and CCH, deviating from the trailing pattern of the dusty spirals (see Fig. [7](#spiral_h13cop)). Different molecules might trace different parts of the cloud. To visualize the overall gas distribution, we stack the continuum emission and the peak intensity maps of $\rm H^{13}CO^+$ and CCH with uniform weighting, after normalizing each to their maximum (fig. S[11](#spiral_stack)). The resulting composite map reveals an intricate spiral-like system.

The apparent spatial association alone is insufficient to conclusively validate these as bona fide structures; coherent kinematics are also needed. The intensity-weighted velocity maps of $\rm H^{13}CO^+$ and CCH (see right panels in Fig. [7](#spiral_h13cop)) and the position-velocity (PV) diagrams (see Fig. [8](#h13cop_pvs) and fig. S[12](#cch_pvs)) along the spiral arms present smooth velocity gradients or flat velocity profiles along the identified narrow structures, confirming their velocity-coherent nature. We further model the spiral arms in $\rm H^{13}CO^+$ as the streamlines of a particle with an initial rotation, subject to the gravity of a central massive object *(cite: 2009MNRAS.393..579M, 2019NatAs...3..517Z, 2020NatAs...4.1158P)* (Fig. [9](#infallrotate_h13cop)). While this idealized kinematic model with a central mass of 50-80 $M_{\odot}$ successfully reproduces the gas kinematics along S2 and S5, it can not capture the entire system’s dynamics, particularly the V-shaped velocity profiles of S1 and S2 that are likely indicative of the gravity-driven accretion of the cores lying within the filaments.

Nevertheless, the velocity coherence along the spiral arms, coupled with the partial agreement between the model and the kinematics supports the idea that the gas flows in along the spiral arms with a mass inflow rate of $\sim3.4\times10^{-4}$ M$_\odot$ yr$^{-1}$ (Materials & Methods). This mass inflow rate is comparable with other high-mass star-forming regions with similar scale reported in the literature *(cite: 2018ApJ...855....9L, 2021ApJ...915L..10S,2022ApJ...936..169R, 2024MNRAS.533.1075Z)*\

A prolate structure (the central ellipse in Fig. [1](#cont_b3_b6)A) with a aspect ratio $\sim$1.5 ($\sim$ 5300$\times$3500 au) has formed in the center of I18134, fed by the 20,000-au-scale spiral-like system. The prolateness of the structure is more distinctly visible in the composite map (fig. S[11](#spiral_stack)). It is further resolved in 1.3 mm continuum emission (Fig. [1](#cont_b3_b6)B) and molecular line emission (e.g., DCN, Fig. [2](#dcn_con_streamer)B) at a high resolution of 0.3$^{\prime\prime}$, showing a more prominent bar-like elongated structure (hereafter denoted as the “bar").

The “bar" is resolved into a bright compact object (called the “nucleus") with slender extensions, referred to as streamers, stretching toward the southeast and northwest. The slender streamers and the nucleus resemble a bar-like envelope linking the spiral system to the central protostar.

The spatial distribution of DCN strongly correlates with the 1.3 mm continuum emission (Fig. [2](#dcn_con_streamer)), tracing a similar bar-like structure. The centroid velocity map of DCN (Fig. [2](#dcn_con_streamer)B) shows that the northern spiral arm is blueshifted relative to the systematic velocity of I18134, suggesting a gas streamer infalling from the north to the “bar". Additionally, the gas kinematics along the “bar" exhibit red-blueshifted symmetry around the “nucleus", further supporting the idea that these streamers are transporting gas and converging toward the “nucleus”. This hypothesis is strengthened by the PV diagrams of various molecules cutting along the “bar" (fig. S[13](#pvs)). Among these, DCN, H$_2$CO, HC$_3$N, and C$^{18}$O trace an elongated velocity-coherent structure spanning $\sim6^{\prime\prime}$ (fig. S[13](#pvs) and S[14](#intensity_profile)), indicating that the “bar" may extend to a distance of $\sim$7,500 au. The mass inflow rate from streamers to the “nucleus" is estimated to be $\sim2.6\times10^{-4}$ M$_\odot$ yr$^{-1}$ (Materials & Methods), which is similar to the mass inflow rate along the spiral arms. Therefore, the “bar" plays a key intermediary role in channeling gas from the core-scale spiral-like system and fueling the very central “nucleus".

Zooming further into the “bar", both DCN and CH$_3$OH show asymmetric spatial distribution (fig. S[15](#dcn_ch3oh)). The distribution of DCN consists of three components: the diffuse ambient gas that forms the main body of the “bar", a compact point source associated with the “nucleus", and a small tail connecting to the “nucleus". Notably, this tail extends along the southeast streamer. At the same position, a less apparent tail is also visible in the CH$_3$OH emission. Additionally, a second tail appears west of the “nucleus", extending along the northwest streamer. The alignment of the tails and dusty streamers may suggest that the tails represent the terminal ends of the streamers where the gas is transported deep into the “nucleus".

All the PV diagrams along the “bar" (fig. S[13](#pvs)), except for that of C$^{18}$O, exhibit a diamond-shaped feature peaked at the “nucleus".

These diamond-shaped PV diagrams are characteristic of an infalling-rotating envelope (IRE), e.g. a non-rotationally supported envelope/pseudodisk *(cite: 2014ApJ...791L..38S, 2015ApJ...812...59O,2016ApJ...824...88O, 2017ApJ...837..174O,2019ApJ...873...73Z)*. The continuity from the streamers to the pseudodisk suggests that the streamers are transporting material to a pseudodisk and the gas starts to rotate alongside the pseudodisk. We model the pseudodisk traced by CH$_3$OH thermal emission as an IRE to infer the geometry of the pseudodisk and the mass of the central mass (Fig. [3](#com_obs_model) and fig. S[16](#chi2)). Despite the large uncertainty of the central mass, the model indicates a nearly face-on pseudodisk with an inclination $<15^{\circ}$. Similar geometry and kinematics of the pseudodisk are also well revealed by other dense gas tracers such as CH$_3$CN lines (fig. S[17](#ch3cn_mom_pv)).

Zooming into the “nucleus” with ALMA long-baseline observation at 1.3 mm (angular resolution of $\theta\approx0.03''$, equivalent to 37 au), one single compact source which could be the disk is detected inside in the center of the “nucleus” (Fig. [4](#maserdisk)A). Besides the central compact component, one clear “mini-arm” can be identified in the south, while another three are tentatively detected in the north, west, and east, similar to the four-arm disk reported in *(cite: 2023NatAs...7..557B)*. On the basis of 2-dimensional Gaussian fitting to the disk, the size and inclination of the disk are $\sim$110 au and $\sim75^{\circ}$, respectively. This inclination differs from the pseudodisk by more than 60$^{\circ}$. Additionally, the presence of $^{12}$CO bipolar outflow suggests the disk is not face-on. The combined evidence indicates that the disk and the pseudodisk are notably misaligned.

Jansky Very Large Array observations with a resolution of $\sim0.2^{\prime\prime}$ led to the detection of 12 GHz Class II methanol masers oriented along the southeast-to-northwest direction *(cite: 2024A&A...684A..86B)*, perpendicular to the CO bipolar outflow, indicating that the Class II methanol masers may trace the disk (Fig. [4](#maserdisk)b). Specifically, the blueshifted maser cluster corresponds to the southern spiral arm seen in the long-baseline observation, the redshifted cluster aligns with the northern arm, and another cluster (in gray color) seems to align with the outflow (Fig. [4](#maserdisk)b). The linear distribution of the Class II methanol masers suggests that the disk is likely viewed at a larger inclination than the pseudodisk. This further supports that the disk is misaligned with the pseudodisk. Meanwhile, the orientation of the linear distribution likely corresponds to the major axis of the disk traced by the maser which also deviates from the major axis of the continuum disk. This might suggest that the masers and the long-baseline continuum trace different disk structures. For example, the maser and the continuum trace the outer and inner disk, respectively, and they might also be misaligned.

The most remarkable feature is that the velocity distribution of the masers is opposite to the velocity field of the pseudodisk (see Fig. [4](#maserdisk)C and the cartoon in Fig. [5](#cartoon)C). The velocity reversal may suggest opposite signs for the inclination of the disk traced by the maser and the pseudodisk. Previous observations have detected misalignment of the orientation between the disk and the envelope in low-mass star forming cores *(cite: 2022ApJ...927...54O, 2007A&A...475..915B, 2007A&A...461.1037B)*. In extreme cases, the Keplerian disk could be counter-rotating relative to the pseudodisk. While mechanisms for this extreme scenario have been proposed in low-mass star-forming regions: the interaction with the spiral arm in a circum-multiple disk *(cite: 2021PASJ...73L..25T)* and non-ideal magneto-hydrodynamics effects *(cite: 2011ApJ...738..180L, 2017PASJ...69...95T)*, it is still theoretically unclear whether this scenario could happen in massive disks. Anyway, here we provide a firm detection of a misaligned disk surrounding a HMYSO.

The opposite signs for the inclination could also arise from the nearly face-on orientation of the pseudodisk and the potential wobbling due to the non-uniform angular momentum transfer to the Keplerian disk via asymmetric accretion flows, leading to a few tens of degrees of shift in the spin axis orientation *(cite: 2017ApJ...839...69M, 2024arXiv240506520P)*. To better visualize this effect, fig. S[18](#orien_schem) provides a schematic representation of this inclination difference. After excluding the maser cluster aligned with the outflow direction, the remaining 12 GHz Class II methanol masers follow Keplerian rotation very well (Materials & Methods and Fig. [4](#maserdisk)c). We perform Keplerian curve modeling on the spatial-kinematics of the masers in the projected position-velocity diagram. The best-fit scaled enclosed mass ($M_{*,d}\times\sin^2 i$ where $M_{*,d}$ is the dynamic mass and $i$ is the inclination of the disk) is 1.93 $M_{\odot}$. If we take the best-fit inclination of the pseudodisk as the inclination of the disk, the mass of HMYSO $M_{*,d}$ would be over 180 $M_{\odot}$ which is almost the total mass of the MDC. Thus, the inclination of the maser disk should be larger than that of the pseudodisk, which further suggests the misalignment between the pseudodisk and the maser disk.

Radio continuum emission from the central UC Hii region suggests that the spectral type of the central star is between B3 and B0 *(cite: 2003MNRAS.341..270V)*, corresponding to a stellar mass of 8-16 $M_{\odot}$ *(cite: 2013ApJS..208....9P)*. Assuming this stellar mass range, the inclination of the maser disk would be $20^{\circ}$ to $30^{\circ}$.

As mentioned above, the “nucleus” in MDC IRAS 18134-1942 is fed by gas streamers within the elongated bar-like structure, indicating that the formation of the misaligned disk may be induced by gas infall, as suggested in numerical simulations *(cite: 2021A&A...656A.161K)*. Multiple or episodic gas acquisition events through the large-scale barred spiral-like system during the gas accretion and angular momentum build-up of the disk may naturally lead to the kinematical misalignment (or even counter-rotation) of components in the “nucleus”.

In addition, the shock tracers, $\rm H_2$, SiO thermal emission, and 22 GHz water masers, are well-aligned, but they deviate by approximately $30^{\circ}$ from the direction of the $^{12}$CO outflow (left panel in Fig. [2](#dcn_con_streamer)C and fig. S[19](#outflow_sio_h2_maser)). The wobbling disk due to the asymmetric accretion flow could also be the reason for the misalignment between the $^{12}$CO outflow and the shock, and the potential jet precession revealed by $^{12}$CO high-velocity emission (fig. S[20](#co_channel)).

The disk-mediated accretion rate of the HMYSO, inferred from CO outflow emission, is $\sim$2.8$\times10^{-6}\,M_{\odot}~{\rm yr}^{-1}$(Materials & Methods), which is two orders of magnitude smaller than the mass inflow rate along the spiral arms and the streamers. Since we assume $^{12}$CO emission is optically thin, and due to the potential missing flux caused by the lack of short spacing of the interferometer, this accretion rate would be the lower limit of the exact accretion rate. However, the estimated accretion rate is consistent with the accretion rates of high-mass star formation regions reported in *(cite: 2020ApJ...903..119L)*. In particular, a strong correlation between the accretion rate $\dot{M}_{\rm acc}$ and luminosity-to-mass ratio $L_{\rm bol}/M_{\rm clump}$ is reported: $\log(\dot{M}_{acc})=0.8\log(L_{\rm bol}/M_{\rm clump})-5.8$. With a $\log(L_{\rm bol}/M_{\rm clump})$ of 0.65 *(cite: 2018MNRAS.473.1059U)*, $\log(\dot{M}_{\rm acc})$ of I18134 from this relation would be -5.28 which is closed to the estimated $\log(\dot{M}_{\rm acc})$ of -5.55. The drastic decrease from the mass inflow rate of the streamers to the disk-mediated accretion rate suggests that the rotating envelope and protostellar disk may play a crucial regulatory role in the mass growth of the protostar.

The discovery of the “spirals-bar-disk-outflow” complex (see the cartoon in Figure [5](#cartoon)) in MDC IRAS 18134-1942 provides the clearest observational evidence that HMYSOs can efficiently assemble their masses through multi-scale gas accretion within a dense core ($\sim$0.1 pc). Gas flows in from spiral arms down to the “bar", and then finally onto the disk.

The gas transfer rate remains relatively constant ($\sim 10^{-4}\,M_{\odot}~{\rm yr}^{-1}$) from the spiral system to the “bar”, suggesting a hierarchical but continuous mass infall process. The asymmetric gas inflows, ending at the disk, could trigger the accretion bursts of the HMYSOs *(cite: 2023ApJ...954L..25B,2024ApJ...966..119L)*, which in turn could explain the methanol maser flares. Such inflows could also inject angular momentum non-uniformly to the HMYSO, resulting in the disk wobbling and the jet precession. The disk wobbling could cause the misalignment of the disk and envelope. Our discovery manifests that barred spiral-like structures within MDCs play an important role during the gas accretion and angular momentum build-up of massive disks. Future studies of more similar systems will be crucial for unraveling the mystery of high-mass star formation as well as massive disk formation. Furthermore, from the visual impression alone, the “spirals-bar-disk-outflow" complex (Figure [5](#cartoon)) closely resembles the morphology of a barred spiral galaxy with an active galactic nucleus (AGN) despite their very different physical scales and central engines (HMYSO versus supermassive black hole). This work demonstrates that spiral systems and bar-like structures can be formed not only in self-gravitating rotating systems like galactic discs (for example, see some state-of-the-art simulation of the formation of galactic discs in very gas-rich environments *(cite: 2024MNRAS.535..187T, 2024ApJ...968...86B, 2025arXiv250201895B)*) but also in high-mass star formation regions. This suggests that in certain systems these structures are closely linked to the mass transport process. Detailed comparison to barred spiral galaxies is beyond the scope of this work. However, insight from the formation and evolution of galaxies and AGNs would provide valuable inspiration for the high-mass star formation community, and vice versa.

![](fig/band6_band3_cont.pdf)

![](fig/cont_sio_DCN.pdf)

![](fig/obs_model_comparison.pdf)

![](fig/highres_ch3oh_maser.pdf)

![](fig/cartoon.pdf)

**ALMA observations and data reduction**\
**ALMA 3 mm observations**  

IRAS 18134-1942 was observed under the project “ALMA Three-millimeter Observations of Massive Star-forming regions (ATOMS)" with Atacama Compact 7 m Array (ACA) and 12 m ALMA arrays (C43-3 configuration) using the Band 3 receiver *(cite: 2008SPIE.7020E..1BC)* on 2019 November 1-3 (Project ID: 2019.1.00685.S; PI: Tie Liu). The standard calibration was done using Common Astronomy Software Applications (CASA) package *(cite: 2007ASPC..376..127M)* 5.6. The ACA data and 12 m-array data were combined and imaged using the same version of CASA with natural weighting, yielding an angular resolution of 2.15 arcsec $\times$ 1.72 arcsec (position angle of -81.4$^{\circ}$ ) for the 3 mm continuum emission. The continuum image is shown in Fig. [1](#cont_b3_b6); The pixel size is 0.4$^{\prime\prime}$ and it achieved an rms noise of $\rm\sim0.25\,mJy\,beam^{-1}$. We refer to the survey description paper *(cite: 2020MNRAS.496.2790L)* for the observations and data reduction details.\
**ALMA 1.3 mm observations**  

We conducted ALMA Band 6 *(cite: 2004stt..conf..181E)* observations of IRAS 18134-1942 ACA and 12 m arrays (C-2 and C-5 configurations) under the project “Querying Underlying mechanisms of massive star formation with ALMA-Resolved gas Kinematics and Structures (QUARKS)" (project code: 2021.1.00095S, PIs: Lei Zhu, Tie Liu, and Guido Garay) on 2023 April 17 (ACA), 2024 March 19 (C-2) and 2022 August 15 (C-5). The calibration, image, and self-calibration were done using CASA 6.5. We cleaned the continuum image and the cube data with a pixel size of 0.05$^{\prime\prime}$ using the *briggs* weighting. The *robust* parameter is adopted as 0.5. We conducted three rounds of phase-only self-calibration with a shortest solution interval of 12 s. For the details of observations and data reduction, we also refer to the survey description paper *(cite: 2024RAA....24b5009L)*. We achieved an angular resolution of 0.30 arcsec $\times$ 0.27 arcsec (position angle of 66.8$^{\circ}$) and an rms noise on the continuum emission of $\rm\sim0.25\,mJy\, beam^{-1}$. For the highest-resolution observation, we use the self-calibrated product image from the ALMA science archive (project code: 2021.1.00455.T, PI: Todd Hunter). The synthesized beam size is $\rm 0.05\,arcsec\times0.03\,arcsec$ (position angle of 87.4$^{\circ}$). The rms noise is $\rm \sim0.06\,mJy~beam^{-1}$.\
**Spiral-arm-like structures**\
**Morphology**

We first characterize spiral-like filaments (hereafter spiral arms) on the 3 mm continuum map. For simplicity, we model the spiral arms as logarithmic spirals, described by $R(\theta)=R_0e^{a\theta}$, where $R_0$ is the starting radius of the spiral, $a$ is the growth rate of the spiral, and the pitch angle is given by $\arctan{|a|}$. The starting radius $R_0$ of each spiral arm is manually determined from the projected polar plot. The polar plots were made via Python package *polarTransform*. Using the logarithmic spiral curve, we generated spiral model images via the Bresenham Line Algorithm and convolved them with a 2-dimensional Gaussian kernel with the same full width at half maximum (FWHM) as the synthesized beam (fig. S[21](#spiral_model_continuum)A). By calculating the Pearson correlation coefficient between the model images and the 3 mm continuum map, we identified the spiral model that best matches the original continuum map (fig. S[21](#spiral_model_continuum)B). The best fit of $a$ is robust against the choice of the FWHM. The best match spiral arms S1, S2, and S3 are outlined as cyan dashed curves in Fig. [1](#cont_b3_b6). The pitch angles of S1-3 are 49$^{\circ}$, 34$^{\circ}$, and 52$^{\circ}$, respectively. The pitch angles of S1 and S3 are quite similar which might suggest that the two arms form a symmetric grand-design spiral system.

The molecular gas distribution also exhibits a similar spiral pattern. Fig. [7](#spiral_h13cop) presents the peak intensity and centroid velocity maps of $\rm H^{13}CO^+$ $J=1-0$ and CCH $N_{J,K}=1_{3/2,2}-0_{1/2,1}$. The spiral pattern of the gas distribution is more distinctly visible in molecular gas. We employ a similar approach to identify and characterize the spiral arms in the peak intensity maps. The emission from S2 is more extended in $\rm H^{13}CO^+$ than in the continuum emission. The parameter $a$ of S2 measured in the continuum map is replaced by the best match $a$ when matching the model with the emission from $\rm H^{13}CO^+$, assuming that both map the same gas. One (S4) and three (S4, S7, S8) additional spiral arms are identified in $\rm H^{13}CO^+$ and CCH, respectively, as indicated by the orange and red dashed curves. While a logarithmic spiral curve was used to depict the gas distribution for simplicity, it can not fully capture the entire morphology. We outline manually additional filamentary structures in these peak intensity maps, as orange and red dotted lines. To examine the overall gas distribution, we stack the normalized peak intensity maps of $\rm H^{13}CO^+$ and CCH alongside with the 3 mm continuum map with uniform weighting in fig. S[11](#spiral_stack) (this neglects the relative abundance between dust, $\rm H^{13}CO^+$, and CCH).\

![](fig/3mmcontinuum_spiral.pdf)

![](fig/spiral_h13cop_cch.pdf)

**Gas Kinematics**

The PV cuts are placed along the curves we identified in the previous section. The PV diagrams are shown in Fig. [8](#h13cop_pvs) and fig. [12](#cch_pvs), which reveal that the identified structures are velocity-coherent filaments. The velocity gradients seen in the PV diagrams may indicate that the gas is infalling to the center of the clump driven by the gravitational force of the central object.

![](fig/h13cop_pvs.pdf)

**Infalling-rotating particle trajectory**

We model the kinematics of the filaments observed with $\rm H^{13}CO^+$ to validate whether the velocity gradient is consistent with infall motion using an analytic solutions *(cite: 2009MNRAS.393..579M, 2020NatAs...4.1158P)* of a particle moving within a rotating cloud toward a central mass. The model provides both the plane-of-sky position and the line-of-sight velocity along an infalling streamline. The model is defined by a central point mass, the inclination angle of the angular momentum vector of the rotating plane, and the angular velocity of the cloud assuming a rigid body rotation. The major inputs are the initial position and velocity of the particle in spherical coordinates.

We manually adjust the model and streamline parameters to find the best match parameter set. Based on the observed gas morphology, we assume the inclination angle to be between 0$^{\circ}$ to 20$^{\circ}$ (where 0$^{\circ}$ represents a face-on view). The model that best reproduces the observed features is obtained using the initial distance of 52,000 au, the position angle of 21$^{\circ}$, and the polar angle of 70$^{\circ}$ for S2, and the initial radius of 35,500 au, the azimuthal angle of 176$^{\circ}$, and the polar angle of 40$^{\circ}$ for S5. The position angle is measured from the north in a clockwise direction, and the polar angle is measured from the spin axis of the plane whose inclination angle is 10$^{\circ}$. The angular velocity is assumed as $4\times10^{-14}~{\rm rad~s^{-1}}$ and the initial radial velocity is 0.6 $\rm km~s^{-1}$. Fig. [9](#infallrotate_h13cop) shows the streamline trajectories (in coral) assuming a central mass of 50-80$\,M_{\odot}$ in S2 and S5 which spatially align with the emission in the peak intensity map (left column). The middle column shows the centroid velocity and also the trajectories color-coded by line-of-sight velocity. The right column presents the kernel density estimate (KDE) of the centroid velocity versus the projected distance from the central mass measured in the middle column.

![](fig/streamline_H13cop.pdf)

**IRE modeling**\
Based on the spatial distribution and velocity map, the $\rm CH_3OH~4_2-3_1~E1~vt=0$ emission is expected to trace the pseudodisk. Here we model the pseudodisk as a flattened infalling and rotating envelope (IRE) with the publicly available code FERIA *(cite: 2022PASP..134i4301O)*. The central mass $M_{*,e}$, the centrifugal radius $r_{\rm CB}$, the outer radius of the IRE $r_{\rm out}$ and the inclination $i$ are treated as free parameters. The position angle of the IRE model is fixed to the velocity gradient observed in the centroid velocity map. Note that the uncertainties arising from the simplicity of the model could dominate over the observational noise. For this reason, instead of conducting a precise fitting method like MCMC, we employed a $\chi^2$ grid search to explore the parameter space in this study. To reduce computational time, we began with a coarse $\chi^2$ grid search to constrain the parameter ranges, followed by a fine grid search. The parameter ranges for the fine grid search are summarized in table S[\[parameterrange\]](#parameterrange). The best-fit parameter set with the lowest $\chi^2$ value includes $M_{*,e}$ of 45 $M_{\odot}$, $i$ of $6^\circ$, $r_{\rm CB}$ of 60 au, and $r_{\rm out}$ of 950 au (fig. S[16](#chi2)). As shown in Fig. [3](#com_obs_model), the best-fit model can reproduce the overall kinematics, especially the curvature shown on the centroid velocity maps–representing the local velocity$\sim 10.6$ km s$^{-1}$–due to the infalling and rotating kinematics. Notably, the $\chi^2$ distribution in the $i$ – $M_{*,e}$ space reveals a ridge-like pattern, where central mass and inclination are correlated. The model is insensitive to central mass but tightly constrains the inclination to $<15^\circ$. The model only considers a central point mass, and the best-fit 45 $M_{\odot}$ is too massive for a protostar at a very early stage. Consequently, despite the uncertainty in the central mass, the IRE modeling robustly indicates a nearly face-on pseudodisk.

**Dynamics of the maser disk**

We manually selected two blueshifted and redshifted maser clusters in the southeast and northwest for the reason that the northeast cluster (grey spots in Fig. [4](#maserdisk)A) is possibly associated with the outflow due to the similar velocity and direction compared with the 22 GHz water masers and the $\rm H_2$ knots *(cite: 2024A&A...684A..86B)* (see fig. S[19](#outflow_sio_h2_maser)), or it is associated with the tentative eastern spiral arm. After projecting the maser spot onto a position-velocity cut, we modeled the spatial-kinematics of the maser using a Keplerian rotation model, treating the scaled enclosed mass ($M_{*,d}\times\sin i^2$ where $M_{*,d}$ is the dynamic mass and $i$ is the inclination of the disk), and the system velocity as free parameters. The position angle of the position-velocity cut was fixed as the direction of the steepest velocity gradient in the ALMA observation. The disk center was assumed to be the peak of the long-baseline 1.3 mm continuum. The best-fit Keplerian rotation profile is shown in the position-velocity diagram in Fig. [4](#maserdisk). The scaled enclosed mass was estimated using the least-square fitting, implemented in SciPy, to be $M_{*,d}\times\sin^2 i=1.93\pm0.07\,M_{\odot}$.\
**Misalignment between outflow and shocked gas**

We detect the outflow emission traced by $^{12}$CO covered in our frequency range. fig. S[19](#outflow_sio_h2_maser)A shows the red- and blueshifted outflow gas integrated between \[20, 50\] km s$^{-1}$ and \[-30, 0\] km s$^{-1}$, respectively, where it is free of $^{13}$CO and C$^{18}$O emissions. Along with the $^{12}\rm CO$ outflow gas, the shock-induced SiO, $\rm H_2$, and 22 GHz water maser emission are also shown in the same figure. SiO, $\rm H_2$, and 22 GHz water masers share a similar extended direction $\sim 253^{\circ}$, implying a common shock orgion, likely driven by the jet. The $^{12}\rm CO$ outflow is in a different direction, differing from the jet direction by $\sim30^{\circ}$.\

**Mass assembly rate at different scales**

We determine the column density of $\rm H^{13}CO^+$ $J=1-0$, CCH $N_{J,K}=1_{3/2,2}-0_{1/2,1}$ assuming optically thin conditions with *(cite: 2015PASP..127..266M)*:

$$\begin{equation}
    N=\frac{3h}{8\pi^3|\mu_{lu}|^2}\frac{Q_{\rm rot}}{g_u}\exp\left(\frac{E_u}{kT_{\rm ex}}\right)\left[\exp\left(\frac{h\nu}{kT_{\rm ex}}\right)-1\right]^{-1}\frac{\int T_{\rm B} d\nu}{T_{\rm ex}},
\end{equation}$$ where $h$, $|\mu_{lu}|^2$, $Q_{\rm rot}$, $g_{\rm u}$, $E_{\rm u}$, $k$, $T_{\rm ex}$, $\nu$, and $T_{\rm B}$ are the Planck constant, the dipole matrix element, the rotational partition function, the level degeneracy, the upper state energy, the Boltzmann constant, the excitation temperature which is adopted as 20 K, the frequency of the transitions, and the brightness temperature. The $|\mu_{lu}|^2$, $Q_{\rm rot}$, $g_{\rm u}$, and $E_{\rm u}$ are taken from CDMS Database *(cite: 2001A&A...370L..49M)*. The mass of the inflow is then calculated through $$\begin{equation}
    M_{\rm inflow}=X^{-1}m_{\rm H_2}AD^2\sum_{i,j}N_{ij},
\end{equation}$$ where $X$, $m_{\rm H_2}$, $A$, $D$, $N_{ij}$ are the molecular abundance relative to $\rm H_2$, the mass of a hydrogen molecule, the angular area of a pixel, the source distance, and the column density at the pixel$_{ij}$. We calculate the mass of the inflows seen in $\rm H^{13}CO^+$ emission and the rest seen in CCH emission. We assume the abundances of H$^{13}$CO$^+$ and CCH to be 1.28$\times10^{-10}$ *(cite: 2013ApJ...777..157H)* and 3.72$\times10^{-8}$ *(cite: 2012ApJ...756...60S)*, respectively. The total masses of the H$^{13}$CO$^+$ and CCH spiral system are 22.9 and 3.4 $M_{\odot}$, respectively. Assuming that the velocity gradient $\nabla{V}_{||}$, which is the velocity profile in the Moment 1 maps, is due to the inflow, we further calculate the inflow rate $\dot{M}_{||}$ via *(cite: 2013ApJ...766..115K)*: $$\begin{equation}
    \dot{M}_{||}=\frac{\nabla{V}_{||}M_{\rm inflow}}{\tan{\theta}},
    \label{eq:3}
\end{equation}$$ where $\theta$ is the inclination angle. We assume the inclination angle to all be 45$^{\circ}$ except for S2 and S5, which are 30$^{\circ}$ and 60$^{\circ}$, respectively, based on the previous infall-rotating particle trajectory modeling. The total inflow rate for the spirals detected in $\rm H^{13}CO^+$ and CCH is 3.4$\times10^{-4}\,M_{\odot}~{\rm yr}^{-1}$.

We estimate the total mass of the “bar” from the 1.3 mm dust continuum emission. In the optically thin limit, the mass can be calculated as $$\begin{equation}
    M=R_{\rm dg}\frac{F_{\nu}D^2}{\kappa_\nu B_\nu(T)},
\end{equation}$$ where $R_{\rm dg}$ is the gas-to-dust ratio, $F_{\nu}$ is the flux density, $\kappa_{\nu}$ is the dust opacity per gram of dust, and $B_\nu(T)$ is the Planck function at the dust temperature of $T$. We use *astrodendro* algorithm to extract the flux of the “bar” from the dendrogram which is an abstraction of the changing topology of the isosurfaces of a two-dimensional image as a function of contour levels *(cite: 2008ApJ...679.1338R)*. The algorithm organizes hierarchical structures into “*trees*” consisting of “*branches*”, formed by combining “*leaves*” in the terminology of *astrodendro*. The following parameters are used in computing the dendrogram: the minimum pixel value *min-value* is 3$\sigma_{\rm 1.3\,mm}$; the minimum difference in the peak intensity between neighboring structures *min-delta* = 1$\sigma_{\rm 1.3\,mm}$; and the minimum number of pixels required for a structure to be considered an independent entity *min-npix* $= N_{\rm beam}$, where $N_{\rm beam}$ is the number of pixels enclosed in the synthesized beam. Fig. [10](#cont_dendro) shows the identified “bar” as a tree and the potential protostars as leaves. We subtract the fluxes of two luminous leaves from the total flux of the tree to obtain the flux of the extended structure.

Adopting a $R_{\rm dg}$ of 100, $\kappa_\nu$ of $1\,{\rm cm^{2}~g^{-1}}$ *(cite: 1994A&A...291..943O)*(interpolated to 1.3 mm with the dust opacity index $\beta$ of 1.6), and a temperature of 20 K, the mass of the “bar” is 6.2 $M_{\odot}$. Besides the rotation, there is also a global velocity gradient of $\rm\sim41\,km~s^{-1}~pc^{-1}$ along the “bar” as seen in DCN (fig. S[13](#pvs)). The infall rate along the “bar” can be estimated using Eq. [\[eq:3\]](#eq:3) which is 2.6$\times10^{-4}\,M_{\odot}~{\rm yr}^{-1}$, similar to the infall rate of the spiral system.

![](fig/cont_dendro.pdf)

At the disk scale, assuming the $^{12}$CO outflow momentum is conserved from the protostellar wind momentum, we infer the accretion rate $\dot{M}_{\rm acc}$ from the mass-loss rate $\dot{M}_{\rm w}$ estimated from $^{12}$CO since $\dot{M}_{\rm acc}$ is proportional to $\dot{M}_{\rm w}$ via $\dot{M}_{\rm acc}=f\times\dot{M}_{\rm w}$ *(cite: 2013A&A...551A...5E, 2016ARA&A..54..491B)* where $f$ is the fraction between the accretion rate and mass-loss rate. We estimate the gas mass of the outflow $m_{\rm i}$ at each channel following *(cite: 2009ApJ...696...66Q)*:

$$\begin{equation}
    m_{i}=1.39\times10^{-6}\exp\left({\frac{16.59}{T_{\rm ex}}}\right)(T_{\rm ex}+0.92)D^2\int S_{i}d\Omega,
\label{eq:12co}
\end{equation}$$ where $T_{ex}$, $D$, $S_{i}$ and $\Omega$ are the excitation temperature of $^{12}$CO (2-1), the distance in kpc, the flux in Jy of each pixel at channel $i$, and the solid angle, respectively. Eq. [\[eq:12co\]](#eq:12co) is normalized to a $^{12}$CO-to-$\rm H_2$ abundance of $10^{-4}$ and a mean gas atomic weight of 1.36. We adopt a $T_{\rm ex}$ of 30 K which is slightly higher than the 20 K used above considering that the gas could be heated by the outflow. The velocity range is free of $^{13}$CO and C$^{18}$O (fig. S[22](#co_spec)), thus we assume the $^{12}$CO emission is optically thin. Measuring the $^{12}$CO outflow projection length ($\lambda_{\rm max}$), we estimate the outflow dynamical timescale ($t_{\rm dyn}$), momentum $P_{\rm out}$, mechanical force $F_{\rm out}$, and thus mass-loss rate $\dot{M}_{\rm w}$ using: $$\begin{equation}
    t_{\rm dyn}=\frac{\lambda_{\rm max}}{(v_{\rm max,b}+v_{\rm max,r})/2},
\end{equation}$$ $$\begin{equation}
    P_{\rm out}=\sum^{\rm blue} m_iv_i+\sum^{\rm red} m_iv_i,
\end{equation}$$ $$\begin{equation}
    F_{\rm out}=P_{\rm out}/t_{\rm dyn},
\end{equation}$$ $$\begin{equation}
    \dot{M}_{w}=\frac{F_{\rm out}}{v_w} \label{eq:masslossrate},
\end{equation}$$ Here $v_{\rm max,b}~{\rm and}~v_{\rm max,r}$ are the maximum blueshifted and redshifted $^{12}$CO velocities, respectively, and $v_{\rm w}$ is the wind velocity. We adopt a $v_{\rm w}$ of 500 km s$^{-1}$ *(cite: 2016ARA&A..54..491B, 1995ApJ...455..269L)*. The outflow parameters are summarized in table S[2](#tab:outflow). The mass-loss rates for the blue and red lobes are 5.7 and 3.6$\times 10^{-7}\,M_{\odot}~{\rm yr}^{-1}$, respectively, with a total of 9.3$\times 10^{-7}\,M_{\odot}~{\rm yr}^{-1}$. We adopt the fraction $f$ of 3 *(cite: 1998ApJ...502L.163T)*, resulting in an accretion rate of 2.8$\times10^{-6}\,M_{\odot}~{\rm yr}^{-1}$.

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Lobe | $\Delta v$ | $\lambda_{\rm max}$ | $t_{\rm dyn}$ | $P_{\rm out}$ | $F_{\rm out}$ | $\dot{M}_{\rm w}$ |
|  | km s$^{-1}$ | $10^{-3}$ pc | $10^3\,yr$ | $M_{\odot}~{\rm km~s^{-1}}$ | $10^{-2}~M_{\odot}~{\rm km~s^{-1}~yr^{-1}}$ | $10^{-5}\,M_{\odot}$ yr$^{-1}$ |
| Blue | \[-30,0\] | 49.91 | 1.11 | 26.93 | 2.42 | 4.85 |
| Red | \[20,50\] | 18.41 | 0.41 | 4.74 | 1.16 | 2.31 |

: Outflow parameters of I18134-1942

As we cannot derive the inclination of the outflow, the accretion rate has not been corrected for the projection with a factor of $\cos{i}/\sin^2{i}$. On a hemispherical surface, the probability distribution of the inclination angle $i$ is given by $P(i)\propto\cos{i}$, where $i$ ranges from 0 to $\pi$/2. The mean inclination angle of the outflow is calculated to be $$E(i)=\frac{\int_0^{\frac{\pi}{2}}i\cos i~{\rm d}i}{\int_0^{\frac{\pi}{2}}\cos i~{\rm d}i}=\frac{\pi}{2}-1\,{\rm radian}\approx32.7^{\circ}$$ For the mean inclination angle, the very small (i.e. 5$^{\circ}$) and large (i.e. 85$^{\circ}$) inclination angle, the correction factors applied to the accretion rate are determined to be 2.9, 131.1, and 0.09, respectively. We estimated the mass inflow rate assuming the inclination of most of the inflows to be 45$^{\circ}$. Changing the inclination to 10$^{\circ}$ or 80$^{\circ}$, would increase or reduce the inflow rate by a factor of 5.7. The disk-mediated accretion rate inferred from the outflow would be comparable to the mass inflow rate only under the extreme cases.

88 urlstyle

(ref: Tan2014) J. C. Tan, M. T. Beltrán, P. Caselli, F. Fontani, A. Fuente, M. R. Krumholz, C. F. McKee, and A. Stolte. . In Henrik Beuther, Ralf S. Klessen, Cornelis P. Dullemond, and Thomas Henning, editors, *Protostars and Planets VI*, pages 149–172, January 2014. doi: 10.2458/azu_uapress_9780816531240-ch007.

(ref: Krum2014) M. R. Krumholz, M. R. Bate, H. G. Arce, J. E. Dale, R. Gutermuth, R. I. Klein, Z. Y. Li, F. Nakamura, and Q. Zhang. . In Henrik Beuther, Ralf S. Klessen, Cornelis P. Dullemond, and Thomas Henning, editors, *Protostars and Planets VI*, pages 243–266, January 2014. doi: 10.2458/azu_uapress_9780816531240-ch011.

(ref: 2018ARA&A..56...41M) Frédérique Motte, Sylvain Bontemps, and Fabien Louvet. . *Annu. Rev. Astron. Astrophys.*, 56: 41–82, September 2018. doi: 10.1146/annurev-astro-091916-055235.

(ref: 2019ARA&A..57..227K) Mark R. Krumholz, Christopher F. McKee, and Joss Bland-Hawthorn. . *Annu. Rev. Astron. Astrophys.*, 57: 227–303, August 2019. doi: 10.1146/annurev-astro-091918-104430.

(ref: 1987ARA&A..25...23S) Frank H. Shu, Fred C. Adams, and Susana Lizano. *Annu. Rev. Astron. Astrophys.*, 25: 23–81, January 1987. doi: 10.1146/annurev.aa.25.090187.000323.

(ref: 2003ApJ...585..850M) Christopher F. McKee and Jonathan C. Tan. . *Astrophys. J.*, 585 (2): 850–871, March 2003. doi: 10.1086/346149.

(ref: 2011A&A...527A.135C) T. Csengeri, S. Bontemps, N. Schneider, F. Motte, and S. Dib. . *Astron. Astrophys.*, 527: A135, March 2011. doi: 10.1051/0004-6361/201014984.

(ref: 2013A&A...555A.112P) N. Peretto, G. A. Fuller, A. Duarte-Cabral, A. Avison, P. Hennebelle, J. E. Pineda, Ph. André, S. Bontemps, F. Motte, N. Schneider, and S. Molinari. . *Astron. Astrophys.*, 555: A112, July 2013. doi: 10.1051/0004-6361/201321318.

(ref: 2022MNRAS.514.6038Z) Jian-Wen Zhou, Tie Liu, Neal J. Evans, Guido Garay, Paul F. Goldsmith, Gilberto C. Gómez, Enrique Vázquez-Semadeni, Hong-Li Liu, Amelia M. Stutz, Ke Wang, Mika Juvela, Jinhua He, Di Li, Leonardo Bronfman, Xunchuan Liu, Feng-Wei Xu, Anandmayee Tej, L. K. Dewangan, Shanghuo Li, Siju Zhang, Chao Zhang, Zhiyuan Ren, Ken’ichi Tatematsu, Pak Shing Li, Chang Won Lee, Tapas Baug, Sheng-Li Qin, Yuefang Wu, Yaping Peng, Yong Zhang, Rong Liu, Qiu-Yi Luo, Jixing Ge, Anindya Saha, Eswaraiah Chakali, Qizhou Zhang, Kee-Tae Kim, Isabelle Ristorcelli, Zhi-Qiang Shen, and Jin-Zeng Li. . *Mon. Not. R. Astron. Soc.*, 514 (4): 6038–6052, August 2022. doi: 10.1093/mnras/stac1735.

(ref: 2024A&A...686A.146Z) J. W. Zhou, S. Dib, M. Juvela, P. Sanhueza, F. Wyrowski, T. Liu, and K. M. Menten. . *Astron. Astrophys.*, 686: A146, June 2024. doi: 10.1051/0004-6361/202449514.

(ref: 2016A&ARv..24....6B) M. T. Beltrán and W. J. de Wit. . *Astron. Astrophys. Rev.*, 24: 6, January 2016. doi: 10.1007/s00159-015-0089-z.

(ref: 2019NatAs...3..517Z) Yichen Zhang, Jonathan C. Tan, Kei E. I. Tanaka, James M. De Buizer, Mengyao Liu, Maria T. Beltrán, Kaitlin Kratter, Diego Mardones, and Guido Garay. . *Nature Astronomy*, 3: 517–523, March 2019a. doi: 10.1038/s41550-019-0718-y.

(ref: 2022NatAs...6..837L) Xing Lu, Guang-Xing Li, Qizhou Zhang, and Yuxin Lin. . *Nature Astronomy*, 6: 837–843, May 2022. doi: 10.1038/s41550-022-01681-4.

(ref: 2017NatPh..13..276C) A. Caratti o Garatti, B. Stecklum, R. Garcia Lopez, J. Eislöffel, T. P. Ray, A. Sanna, R. Cesaroni, C. M. Walmsley, R. D. Oudmaijer, W. J. de Wit, L. Moscadelli, J. Greiner, A. Krabbe, C. Fischer, R. Klein, and J. M. Ibañez. . *Nature Physics*, 13 (3): 276–279, March 2017. doi: 10.1038/nphys3942.

(ref: 2023ApJ...959L..31O) Fernando A. Olguin, Patricio Sanhueza, Huei-Ru Vivien Chen, Xing Lu, Yoko Oya, Qizhou Zhang, Adam Ginsburg, Kotomi Taniguchi, Shanghuo Li, Kaho Morii, Takeshi Sakai, and Fumitaka Nakamura. . *Astrophys. J. Lett.*, 959 (2): L31, December 2023. doi: 10.3847/2041-8213/ad1100.

(ref: 2024Natur.625...55M) Anna F. McLeod, Pamela D. Klaassen, Megan Reiter, Jonathan Henshaw, Rolf Kuiper, and Adam Ginsburg. . *Nature*, 625 (7993): 55–59, January 2024. doi: 10.1038/s41586-023-06790-2.

(ref: 2014A&A...566A..17W) Y. W. Wu, M. Sato, M. J. Reid, L. Moscadelli, B. Zhang, Y. Xu, A. Brunthaler, K. M. Menten, T. M. Dame, and X. W. Zheng. . *Astron. Astrophys.*, 566: A17, June 2014. doi: 10.1051/0004-6361/201322765.

(ref: 2003MNRAS.341..270V) D. J. van der Walt, E. Churchwell, M. J. Gaylard, and S. Goedhart. . *Mon. Not. R. Astron. Soc.*, 341 (1): 270–276, May 2003. doi: 10.1046/j.1365-8711.2003.06416.x.

(ref: 2018MNRAS.473.1059U) J. S. Urquhart, C. König, A. Giannetti, S. Leurini, T. J. T. Moore, D. J. Eden, T. Pillai, M. A. Thompson, C. Braiding, M. G. Burton, T. Csengeri, J. T. Dempsey, C. Figura, D. Froebrich, K. M. Menten, F. Schuller, M. D. Smith, and F. Wyrowski. . *Mon. Not. R. Astron. Soc.*, 473 (1): 1059–1102, January 2018. doi: 10.1093/mnras/stx2258.

(ref: 1993MNRAS.261..783S) A. J. Schutte, D. J. van der Walt, M. J. Gaylard, and G. C. MacLeod. *Mon. Not. R. Astron. Soc.*, 261: 783–794, April 1993. doi: 10.1093/mnras/261.4.783.

(ref: 2005A&A...432..737P) M. R. Pestalozzi, V. Minier, and R. S. Booth. *Astron. Astrophys.*, 432 (2): 737–742, March 2005. doi: 10.1051/0004-6361:20035855.

(ref: 2010A&A...517A..56F) F. Fontani, R. Cesaroni, and R. S. Furuya. . *Astron. Astrophys.*, 517: A56, July 2010. doi: 10.1051/0004-6361/200913679.

(ref: 2000A&A...360..311S) M. Szymczak and A. J. Kus. . *Astron. Astrophys.*, 360: 311–318, August 2000.

(ref: 2004AJ....127.3479G) John Galt. . *Astron. J.*, 127 (6): 3479–3483, June 2004. doi: 10.1086/420713.

(ref: 2024A&A...684A..86B) O. S. Bayandina, R. A. Burns, A. Caratti o Garatti, S. E. Kurtz, L. Moscadelli, N. N. Shakhvorostova, A. M. Sobolev, Y. Tanabe, I. E. Val’tts, and Y. Yonekura. . *Astron. Astrophys.*, 684: A86, April 2024. doi: 10.1051/0004-6361/202348656.

(ref: 1991A&A...246..249P) F. Palla, J. Brand, R. Cesaroni, G. Comoretto, and M. Felli. *Astron. Astrophys.*, 246: 249–263, June 1991.

(ref: 2007PASJ...59.1185S) Kazuyoshi Sunada, Takeshi Nakazato, Norio Ikeda, Satoshi Hongo, Yoshimi Kitamura, and Ji Yang. . *Publ. Astron. Soc. Jpn*, 59: 1185, December 2007. doi: 10.1093/pasj/59.6.1185.

(ref: 1996A&A...311..971C) C. Codella, M. Felli, and V. Natale. *Astron. Astrophys.*, 311: 971–980, July 1996.

(ref: 2010MNRAS.406.1487B) S. L. Breen, J. L. Caswell, S. P. Ellingsen, and C. J. Phillips. . *Mon. Not. R. Astron. Soc.*, 406 (3): 1487–1532, August 2010. doi: 10.1111/j.1365-2966.2010.16791.x.

(ref: 2020NatAs...4..142L) Chin-Fei Lee, Zhi-Yun Li, and Neal J. Turner. . *Nature Astronomy*, 4: 142–146, February 2020. doi: 10.1038/s41550-019-0905-x.

(ref: 2020NatAs...4.1170C) Xi Chen, Andrej M. Sobolev, Zhi-Yuan Ren, Sergey Parfenov, Shari L. Breen, Simon P. Ellingsen, Zhi-Qiang Shen, Bin Li, Gordon C. MacLeod, Willem Baan, Crystal Brogan, Tomoya Hirota, Todd R. Hunter, Hendrik Linz, Karl Menten, Koichiro Sugiyama, Bringfried Stecklum, Yan Gong, and Xingwu Zheng. . *Nature Astronomy*, 4: 1170–1176, January 2020. doi: 10.1038/s41550-020-1144-x.

(ref: 2023NatAs...7..557B) R. A. Burns, Y. Uno, N. Sakai, J. Blanchard, Z. Rosli, G. Orosz, Y. Yonekura, Y. Tanabe, K. Sugiyama, T. Hirota, Kee-Tae Kim, A. Aberfelds, A. E. Volvach, A. Bartkiewicz, A. Caratti o Garatti, A. M. Sobolev, B. Stecklum, C. Brogan, C. Phillips, D. A. Ladeyschikov, D. Johnstone, G. Surcis, G. C. MacLeod, H. Linz, J. O. Chibueze, J. Brand, J. Eislöffel, L. Hyland, L. Uscanga, M. Olech, M. Durjasz, O. Bayandina, S. Breen, S. P. Ellingsen, S. P. van den Heever, T. R. Hunter, and X. Chen. . *Nature Astronomy*, 7: 557–568, May 2023. doi: 10.1038/s41550-023-01899-w.

(ref: 2024Natur.633...58S) Jessica Speedie, Ruobing Dong, Cassandra Hall, Cristiano Longarini, Benedetta Veronesi, Teresa Paneque-Carreño, Giuseppe Lodato, Ya-Wen Tang, Richard Teague, and Jun Hashimoto. . *Nature*, 633 (8028): 58–62, September 2024. doi: 10.1038/s41586-024-07877-0.

(ref: 2015ApJ...804...37L) Hauyu Baobab Liu, Roberto Galván-Madrid, Izaskun Jiménez-Serra, Carlos Román-Zúñiga, Qizhou Zhang, Zhiyun Li, and Huei-Ru Chen. . *Astrophys. J.*, 804 (1): 37, May 2015. doi: 10.1088/0004-637X/804/1/37.

(ref: 2021ApJ...915L..10S) Patricio Sanhueza, Josep Miquel Girart, Marco Padovani, Daniele Galli, Charles L. H. Hull, Qizhou Zhang, Paulo Cortes, Ian W. Stephens, Manuel Fernández-López, James M. Jackson, Pau Frau, Patrick M. Kock, Benjamin Wu, Luis A. Zapata, Fernando Olguin, Xing Lu, Andrea Silva, Ya-Wen Tang, Takeshi Sakai, Andrés E. Guzmán, Ken’ichi Tatematsu, Fumitaka Nakamura, and Huei-Ru Vivien Chen. . *Astrophys. J. Lett.*, 915 (1): L10, July 2021. doi: 10.3847/2041-8213/ac081c.

(ref: 2022ApJ...941...51H) Jihye Hwang, Jongsoo Kim, Kate Pattle, Chang Won Lee, Patrick M. Koch, Doug Johnstone, Kohji Tomisaka, Anthony Whitworth, Ray S. Furuya, Ji-hyun Kang, A. Ran Lyo, Eun Jung Chung, Doris Arzoumanian, Geumsook Park, Woojin Kwon, Shinyoung Kim, Motohide Tamura, Jungmi Kwon, Archana Soam, Ilseung Han, Thiem Hoang, Kyoung Hee Kim, Takashi Onaka, Chakali Eswaraiah, Derek Ward-Thompson, Hong-Li Liu, Xindi Tang, Wen Ping Chen, Masafumi Matsumura, Thuong Duc Hoang, Zhiwei Chen, Valentin J. M. Le Gouellec, Florian Kirchschlager, Frédérick Poidevin, Pierre Bastien, Keping Qiu, Tetsuo Hasegawa, Shih-Ping Lai, Do-Young Byun, Jungyeon Cho, Minho Choi, Youngwoo Choi, Yunhee Choi, Il-Gyo Jeong, Miju Kang, Hyosung Kim, Kee-Tae Kim, Jeong-Eun Lee, Sang-Sung Lee, Yong-Hee Lee, Hyeseung Lee, Mi-Ryang Kim, Hyunju Yoo, Hyeong-Sik Yun, Mike Chen, James Di Francesco, Jason Fiege, Laura M. Fissel, Erica Franzmann, Martin Houde, Kevin Lacaille, Brenda Matthews, Sarah Sadavoy, Gerald Moriarty-Schieven, Mehrnoosh Tahani, Tao-Chung Ching, Y. Sophia Dai, Yan Duan, Qilao Gu, Chi-Yan Law, Dalei Li, Di Li, Guangxing Li, Hua-bai Li, Tie Liu, Xing Lu, Lei Qian, Hongchi Wang, Jintai Wu, Jinjin Xie, Jinghua Yuan, Chuan-Peng Zhang, Guoyin Zhang, Yapeng Zhang, Jianjun Zhou, Lei Zhu, David Berry, Per Friberg, Sarah Graves, Junhao Liu, Steve Mairs, Harriet Parsons, Mark Rawlings, Yasuo Doi, Saeko Hayashi, Charles L. H. Hull, Tsuyoshi Inoue, Shu-ichiro Inutsuka, Kazunari Iwasaki, Akimasa Kataoka, Koji Kawabata, Gwanjeong Kim, Masato I. N. Kobayashi, Tetsuya Nagata, Fumitaka Nakamura, Hiroyuki Nakanishi, Tae-Soo Pyo, Hiro Saito, Masumichi Seta, Yoshito Shimajiri, Hiroko Shinnaga, Yusuke Tsukamoto, Tetsuya Zenko, Huei-Ru Vivien Chen, Hao-Yuan Duan, Lapo Fanciullo, Francisca Kemper, Chin-Fei Lee, Sheng-Jun Lin, Sheng-Yuan Liu, Nagayoshi Ohashi, Ramprasad Rao, Ya-Wen Tang, Jia-Wei Wang, Meng-Zhe Yang, Hsi-Wei Yen, Tyler L. Bourke, Antonio Chrysostomou, Victor Debattista, David Eden, Stewart Eyres, Sam Falle, Gary Fuller, Tim Gledhill, Jane Greaves, Matt Griffin, Jennifer Hatchell, Janik Karoly, Jason Kirk, Vera Könyves, Steven Longmore, Sven van Loo, Ilse de Looze, Nicolas Peretto, Felix Priestley, Jonathan Rawlings, Brendan Retter, John Richer, Andrew Rigby, Giorgio Savini, Anna Scaife, Serena Viti, Pham Ngoc Diep, Nguyen Bich Ngoc, Le Ngoc Tram, Philippe André, Simon Coudé, C. Darren Dowell, Rachel Friesen, and Jean-Franćois Robitaille. . *Astrophys. J.*, 941 (1): 51, December 2022. doi: 10.3847/1538-4357/ac99e0.

(ref: 2023MNRAS.520.3259X) Feng-Wei Xu, Ke Wang, Tie Liu, Paul F. Goldsmith, Qizhou Zhang, Mika Juvela, Hong-Li Liu, Sheng-Li Qin, Guang-Xing Li, Anandmayee Tej, Guido Garay, Leonardo Bronfman, Shanghuo Li, Yue-Fang Wu, Gilberto C. Gómez, Enrique Vázquez-Semadeni, Ken’ichi Tatematsu, Zhiyuan Ren, Yong Zhang, L. Viktor Toth, Xunchuan Liu, Nannan Yue, Siju Zhang, Tapas Baug, Namitha Issac, Amelia M. Stutz, Meizhu Liu, Gary A. Fuller, Mengyao Tang, Chao Zhang, Lokesh Dewangan, Chang Won Lee, Jianwen Zhou, Jinjin Xie, Wenyu Jiao, Chao Wang, Rong Liu, Qiuyi Luo, Archana Soam, and Chakali Eswaraiah. . *Mon. Not. R. Astron. Soc.*, 520 (3): 3259–3285, April 2023. doi: 10.1093/mnras/stad012.

(ref: 2024MNRAS.530.1956S) Mavis Seidu, J. O. Chibueze, Gary A. Fuller, A. Avison, and N. Asabre Frimpong. . *Mon. Not. R. Astron. Soc.*, 530 (2): 1956–1967, May 2024. doi: 10.1093/mnras/stae987.

(ref: 2009MNRAS.393..579M) S. Mendoza, E. Tejeda, and E. Nagel. . *Mon. Not. R. Astron. Soc.*, 393 (2): 579–586, February 2009. doi: 10.1111/j.1365-2966.2008.14210.x.

(ref: 2020NatAs...4.1158P) Jaime E. Pineda, Dominique Segura-Cox, Paola Caselli, Nichol Cunningham, Bo Zhao, Anika Schmiedeke, Marı́a José Maureira, and Roberto Neri. . *Nature Astronomy*, 4: 1158–1163, January 2020. doi: 10.1038/s41550-020-1150-z.

(ref: 2018ApJ...855....9L) Xing Lu, Qizhou Zhang, Hauyu Baobab Liu, Patricio Sanhueza, Ken’ichi Tatematsu, Siyi Feng, Howard A. Smith, Philip C. Myers, T. K. Sridharan, and Qiusheng Gu. . *Astrophys. J.*, 855 (1): 9, March 2018. doi: 10.3847/1538-4357/aaad11.

(ref: 2022ApJ...936..169R) Elena Redaelli, Stefano Bovino, Patricio Sanhueza, Kaho Morii, Giovanni Sabatini, Paola Caselli, Andrea Giannetti, and Shanghuo Li. . *Astrophys. J.*, 936 (2): 169, September 2022. doi: 10.3847/1538-4357/ac85b4.

(ref: 2024MNRAS.533.1075Z) S. Zhang, C. J. Cyganowski, J. D. Henshaw, C. L. Brogan, T. R. Hunter, R. K. Friesen, I. A. Bonnell, and S. Viti. . *Mon. Not. R. Astron. Soc.*, 533 (1): 1075–1094, September 2024. doi: 10.1093/mnras/stae1844.

(ref: 2014ApJ...791L..38S) Nami Sakai, Yoko Oya, Takeshi Sakai, Yoshimasa Watanabe, Tomoya Hirota, Cecilia Ceccarelli, Claudine Kahane, Ana Lopez-Sepulcre, Bertrand Lefloch, Charlotte Vastel, Sandrine Bottinelli, Emmanuel Caux, Audrey Coutens, Yuri Aikawa, Shigehisa Takakuwa, Nagayoshi Ohashi, Hsi-Wei Yen, and Satoshi Yamamoto. . *Astrophys. J. Lett.*, 791 (2): L38, August 2014. doi: 10.1088/2041-8205/791/2/L38.

(ref: 2015ApJ...812...59O) Yoko Oya, Nami Sakai, Bertrand Lefloch, Ana López-Sepulcre, Yoshimasa Watanabe, Cecilia Ceccarelli, and Satoshi Yamamoto. . *Astrophys. J.*, 812 (1): 59, October 2015. doi: 10.1088/0004-637X/812/1/59.

(ref: 2016ApJ...824...88O) Yoko Oya, Nami Sakai, Ana López-Sepulcre, Yoshimasa Watanabe, Cecilia Ceccarelli, Bertrand Lefloch, Cécile Favre, and Satoshi Yamamoto. . *Astrophys. J.*, 824 (2): 88, June 2016. doi: 10.3847/0004-637X/824/2/88.

(ref: 2017ApJ...837..174O) Yoko Oya, Nami Sakai, Yoshimasa Watanabe, Aya E. Higuchi, Tomoya Hirota, Ana López-Sepulcre, Takeshi Sakai, Yuri Aikawa, Cecilia Ceccarelli, Bertrand Lefloch, Emmanuel Caux, Charlotte Vastel, Claudine Kahane, and Satoshi Yamamoto. . *Astrophys. J.*, 837 (2): 174, March 2017. doi: 10.3847/1538-4357/aa6300.

(ref: 2019ApJ...873...73Z) Yichen Zhang, Jonathan C. Tan, Nami Sakai, Kei E. I. Tanaka, James M. De Buizer, Mengyao Liu, Maria T. Beltrán, Kaitlin Kratter, Diego Mardones, and Guido Garay. . *Astrophys. J.*, 873 (1): 73, March 2019b. doi: 10.3847/1538-4357/ab0553.

(ref: 2022ApJ...927...54O) Satoshi Ohashi, Claudio Codella, Nami Sakai, Claire J. Chandler, Cecilia Ceccarelli, Felipe Alves, Davide Fedele, Tomoyuki Hanawa, Aurora Durán, Cécile Favre, Ana López-Sepulcre, Laurent Loinard, Seyma Mercimek, Nadia M. Murillo, Linda Podio, Yichen Zhang, Yuri Aikawa, Nadia Balucani, Eleonora Bianchi, Mathilde Bouvier, Gemma Busquet, Paola Caselli, Emmanuel Caux, Steven Charnley, Spandan Choudhury, Nicolas Cuello, Marta De Simone, Francois Dulieu, Lucy Evans, Siyi Feng, Francesco Fontani, Logan Francis, Tetsuya Hama, Eric Herbst, Shingo Hirano, Tomoya Hirota, Muneaki Imai, Andrea Isella, Izaskun Jı́menez-Serra, Doug Johnstone, Claudine Kahane, Romane Le Gal, Bertrand Lefloch, Luke T. Maud, Maria Jose Maureira, Francois Menard, Anna Miotello, George Moellenbrock, Shoji Mori, Riouhei Nakatani, Hideko Nomura, Yasuhiro Oba, Ross O’Donoghue, Yuki Okoda, Juan Ospina-Zamudio, Yoko Oya, Jaime Pineda, Albert Rimola, Takeshi Sakai, Dominique Segura-Cox, Yancy Shirley, Brian Svoboda, Vianney Taquet, Leonardo Testi, Charlotte Vastel, Serena Viti, Naoki Watanabe, Yoshimasa Watanabe, Arezu Witzel, Ci Xue, Bo Zhao, and Satoshi Yamamoto. . *Astrophys. J.*, 927 (1): 54, March 2022. doi: 10.3847/1538-4357/ac4cae.

(ref: 2007A&A...475..915B) C. Brinch, A. Crapsi, J. K. Jørgensen, M. R. Hogerheijde, and T. Hill. . *Astron. Astrophys.*, 475 (3): 915–923, December 2007a. doi: 10.1051/0004-6361:20078249.

(ref: 2007A&A...461.1037B) C. Brinch, A. Crapsi, M. R. Hogerheijde, and J. K. Jørgensen. . *Astron. Astrophys.*, 461 (3): 1037–1047, January 2007b. doi: 10.1051/0004-6361:20065473.

(ref: 2021PASJ...73L..25T) Daisuke Takaishi, Yusuke Tsukamoto, and Yasushi Suto. . *Publ. Astron. Soc. Jpn*, 73 (5): L25–L30, October 2021. doi: 10.1093/pasj/psab084.

(ref: 2011ApJ...738..180L) Zhi-Yun Li, Ruben Krasnopolsky, and Hsien Shang. . *Astrophys. J.*, 738 (2): 180, September 2011. doi: 10.1088/0004-637X/738/2/180.

(ref: 2017PASJ...69...95T) Yusuke Tsukamoto, Satoshi Okuzumi, Kazunari Iwasaki, Masahiro N. Machida, and Shu-ichiro Inutsuka. . *Publ. Astron. Soc. Jpn*, 69 (6): 95, December 2017. doi: 10.1093/pasj/psx113.

(ref: 2017ApJ...839...69M) Tomoaki Matsumoto, Masahiro N. Machida, and Shu-ichiro Inutsuka. . *Astrophys. J.*, 839 (1): 69, April 2017. doi: 10.3847/1538-4357/aa6a1c.

(ref: 2024arXiv240506520P) Veli-Matti Pelkonen, Paolo Padoan, Mika Juvela, Troels Haugbølle, and Åke Nordlund. . *arXiv e-prints*, art. arXiv:2405.06520, May 2024. doi: 10.48550/arXiv.2405.06520.

(ref: 2013ApJS..208....9P) Mark J. Pecaut and Eric E. Mamajek. . *Astrophys. J. Suppl. Ser.*, 208 (1): 9, September 2013. doi: 10.1088/0067-0049/208/1/9.

(ref: 2021A&A...656A.161K) M. Kuffmeier, C. P. Dullemond, S. Reissl, and F. G. Goicovic. . *Astron. Astrophys.*, 656: A161, December 2021. doi: 10.1051/0004-6361/202039614.

(ref: 2020ApJ...903..119L) Shanghuo Li, Patricio Sanhueza, Qizhou Zhang, Fumitaka Nakamura, Xing Lu, Junzhi Wang, Tie Liu, Ken’ichi Tatematsu, James M. Jackson, Andrea Silva, Andrés E. Guzmán, Takeshi Sakai, Natsuko Izumi, Daniel Tafoya, Fei Li, Yanett Contreras, Kaho Morii, and Kee-Tae Kim. . *Astrophys. J.*, 903 (2): 119, November 2020. doi: 10.3847/1538-4357/abb81f.

(ref: 2023ApJ...954L..25B) Giseon Baek, Jeong-Eun Lee, Neal J. Evans, Tomoya Hirota, Yuri Aikawa, Ji-hyun Kang, Jungha Kim, and Jes K. Jørgensen. . *Astrophys. J. Lett.*, 954 (1): L25, September 2023. doi: 10.3847/2041-8213/acef1d.

(ref: 2024ApJ...966..119L) Jeong-Eun Lee, Chul-Hwan Kim, Seokho Lee, Seonjae Lee, Giseon Baek, Hyeong-Sik Yun, Yuri Aikawa, Doug Johnstone, Gregory J. Herczeg, and Lucas Cieza. *Astrophys. J.*, 966 (1): 119, May 2024. doi: 10.3847/1538-4357/ad3106.

(ref: 2024MNRAS.535..187T) Thor Tepper-Garcı́a, Joss Bland-Hawthorn, Eugene Vasiliev, Oscar Agertz, Romain Teyssier, and Christoph Federrath. . *Mon. Not. R. Astron. Soc.*, 535 (1): 187–206, November 2024. doi: 10.1093/mnras/stae2372.

(ref: 2024ApJ...968...86B) Joss Bland-Hawthorn, Thor Tepper-Garcia, Oscar Agertz, and Christoph Federrath. . *Astrophys. J.*, 968 (2): 86, June 2024. doi: 10.3847/1538-4357/ad4118.

(ref: 2025arXiv250201895B) Joss Bland-Hawthorn, Thor Tepper-Garcia, Oscar Agertz, Christoph Federrath, Misha Haywood, Paola di Matteo, Timothy R Bedding, Takafumi Tsukui, Emily Wisnioski, Melissa Ness, and Ken Freeman. . *arXiv e-prints*, art. arXiv:2502.01895, February 2025. doi: 10.48550/arXiv.2502.01895.

(ref: 10.1046/j.1365-8711.2003.06419.x) J. M. De Buizer. . *Monthly Notices of the Royal Astronomical Society*, 341 (1): 277–298, 05 2003. ISSN 0035-8711. doi: 10.1046/j.1365-8711.2003.06419.x. URL `https://doi.org/10.1046/j.1365-8711.2003.06419.x`.

(ref: 2008SPIE.7020E..1BC) S. Claude, F. Jiang, P. Niranjanan, P. Dindo, D. Erickson, K. Yeung, D. Derdall, D. Duncan, D. Garcia, B. Leckie, M. Pfleger, G. Rodrigues, K. Szeto, P. Welle, I. Wood, K. Caputa, A. Lichtenberger, and S. K. Pan. . In William D. Duncan, Wayne S. Holland, Stafford Withington, and Jonas Zmuidzinas, editors, *Millimeter and Submillimeter Detectors and Instrumentation for Astronomy IV*, volume 7020 of *Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series*, page 70201B, July 2008. doi: 10.1117/12.788128.

(ref: 2007ASPC..376..127M) J. P. McMullin, B. Waters, D. Schiebel, W. Young, and K. Golap. . In R. A. Shaw, F. Hill, and D. J. Bell, editors, *Astronomical Data Analysis Software and Systems XVI*, volume 376 of *Astronomical Society of the Pacific Conference Series*, page 127, October 2007.

(ref: 2020MNRAS.496.2790L) Tie Liu, Neal J. Evans, Kee-Tae Kim, Paul F. Goldsmith, Sheng-Yuan Liu, Qizhou Zhang, Ken’ichi Tatematsu, Ke Wang, Mika Juvela, Leonardo Bronfman, Maria R. Cunningham, Guido Garay, Tomoya Hirota, Jeong-Eun Lee, Sung-Ju Kang, Di Li, Pak-Shing Li, Diego Mardones, Sheng-Li Qin, Isabelle Ristorcelli, Anandmayee Tej, L. Viktor Toth, Jing-Wen Wu, Yue-Fang Wu, Hee-weon Yi, Hyeong-Sik Yun, Hong-Li Liu, Ya-Ping Peng, Juan Li, Shang-Huo Li, Chang Won Lee, Zhi-Qiang Shen, Tapas Baug, Jun-Zhi Wang, Yong Zhang, Namitha Issac, Feng-Yao Zhu, Qiu-Yi Luo, Archana Soam, Xun-Chuan Liu, Feng-Wei Xu, Yu Wang, Chao Zhang, Zhiyuan Ren, and Chao Zhang. . *Mon. Not. R. Astron. Soc.*, 496 (3): 2790–2820, August 2020. doi: 10.1093/mnras/staa1577.

(ref: 2004stt..conf..181E) G. A. Ediss, M. Carter, J. Cheng, J. E. Effland, W. Grammer, Jr. Horner, N., A. R. Kerr, D. Koller, E. F. Lauria, G. Morris, S. K. Pan, G. Reiland, and M. Sullivan. . In Gopal Narayanan, editor, *Fifteenth International Symposium on Space Terahertz Technology*, pages 181–188, January 2004.

(ref: 2024RAA....24b5009L) Xunchuan Liu, Tie Liu, Lei Zhu, Guido Garay, Hong-Li Liu, Paul Goldsmith, Neal Evans, Kee-Tae Kim, Sheng-Yuan Liu, Fengwei Xu, Xing Lu, Anandmayee Tej, Xiaofeng Mai, Leonardo Bronfman, Shanghuo Li, Diego Mardones, Amelia Stutz, Ken’ichi Tatematsu, Ke Wang, Qizhou Zhang, Sheng-Li Qin, Jianwen Zhou, Qiuyi Luo, Siju Zhang, Yu Cheng, Jinhua He, Qilao Gu, Ziyang Li, Zhenying Zhang, Suinan Zhang, Anindya Saha, Lokesh Dewangan, Patricio Sanhueza, and Zhiqiang Shen. . *Research in Astronomy and Astrophysics*, 24 (2): 025009, February 2024. doi: 10.1088/1674-4527/ad0d5c.

(ref: 2022PASP..134i4301O) Yoko Oya, Hirofumi Kibukawa, Shota Miyake, and Satoshi Yamamoto. . *Publ. Astron. Soc. Pac.*, 134 (1039): 094301, September 2022. doi: 10.1088/1538-3873/ac8839.

(ref: 2015PASP..127..266M) Jeffrey G. Mangum and Yancy L. Shirley. . *Publ. Astron. Soc. Pac.*, 127 (949): 266, March 2015. doi: 10.1086/680323.

(ref: 2001A&A...370L..49M) H. S. P. Müller, S. Thorwirth, D. A. Roth, and G. Winnewisser. . *Astron. Astrophys.*, 370: L49–L52, April 2001. doi: 10.1051/0004-6361:20010367.

(ref: 2013ApJ...777..157H) Sadia Hoq, James M. Jackson, Jonathan B. Foster, Patricio Sanhueza, Andrés Guzmán, J. Scott Whitaker, Christopher Claysmith, Jill M. Rathborne, Tatiana Vasyunina, and Anton Vasyunin. . *Astrophys. J.*, 777 (2): 157, November 2013. doi: 10.1088/0004-637X/777/2/157.

(ref: 2012ApJ...756...60S) Patricio Sanhueza, James M. Jackson, Jonathan B. Foster, Guido Garay, Andrea Silva, and Susanna C. Finn. . *Astrophys. J.*, 756 (1): 60, September 2012. doi: 10.1088/0004-637X/756/1/60.

(ref: 2013ApJ...766..115K) Helen Kirk, Philip C. Myers, Tyler L. Bourke, Robert A. Gutermuth, Abigail Hedden, and Grant W. Wilson. . *Astrophys. J.*, 766 (2): 115, April 2013. doi: 10.1088/0004-637X/766/2/115.

(ref: 2008ApJ...679.1338R) E. W. Rosolowsky, J. E. Pineda, J. Kauffmann, and A. A. Goodman. . *Astrophys. J.*, 679 (2): 1338–1351, June 2008. doi: 10.1086/587685.

(ref: 1994A&A...291..943O) V. Ossenkopf and Th. Henning. *Astron. Astrophys.*, 291: 943–959, November 1994.

(ref: 2013A&A...551A...5E) L. E. Ellerbroek, L. Podio, L. Kaper, H. Sana, D. Huppenkothen, A. de Koter, and L. Monaco. . *Astron. Astrophys.*, 551: A5, March 2013. doi: 10.1051/0004-6361/201220635.

(ref: 2016ARA&A..54..491B) John Bally. . *Annu. Rev. Astron. Astrophys.*, 54: 491–528, September 2016. doi: 10.1146/annurev-astro-081915-023341.

(ref: 2009ApJ...696...66Q) Keping Qiu, Qizhou Zhang, Jingwen Wu, and Huei-Ru Chen. . *Astrophys. J.*, 696 (1): 66–74, May 2009. doi: 10.1088/0004-637X/696/1/66.

(ref: 1995ApJ...455..269L) Henny J. G. L. M. Lamers, Theodore P. Snow, and Douglas M. Lindholm. . *Astrophys. J.*, 455: 269, December 1995. doi: 10.1086/176575.

(ref: 1998ApJ...502L.163T) Kohji Tomisaka. . *Astrophys. J. Lett.*, 502 (2): L163–L167, August 1998. doi: 10.1086/311504.

(ref: harris2020array) Charles R. Harris, K. Jarrod Millman, Stéfan J. van der Walt, Ralf Gommers, Pauli Virtanen, David Cournapeau, Eric Wieser, Julian Taylor, Sebastian Berg, Nathaniel J. Smith, Robert Kern, Matti Picus, Stephan Hoyer, Marten H. van Kerkwijk, Matthew Brett, Allan Haldane, Jaime Fernández del Río, Mark Wiebe, Pearu Peterson, Pierre Gérard-Marchant, Kevin Sheppard, Tyler Reddy, Warren Weckesser, Hameer Abbasi, Christoph Gohlke, and Travis E. Oliphant. Array programming with NumPy. *Nature*, 585 (7825): 357–362, September 2020. doi: 10.1038/s41586-020-2649-2. URL `https://doi.org/10.1038/s41586-020-2649-2`.

(ref: 2020SciPy-NMeth) Pauli Virtanen, Ralf Gommers, Travis E. Oliphant, Matt Haberland, Tyler Reddy, David Cournapeau, Evgeni Burovski, Pearu Peterson, Warren Weckesser, Jonathan Bright, Stéfan J. van der Walt, Matthew Brett, Joshua Wilson, K. Jarrod Millman, Nikolay Mayorov, Andrew R. J. Nelson, Eric Jones, Robert Kern, Eric Larson, C J Carey, İlhan Polat, Yu Feng, Eric W. Moore, Jake VanderPlas, Denis Laxalde, Josef Perktold, Robert Cimrman, Ian Henriksen, E. A. Quintero, Charles R. Harris, Anne M. Archibald, Antônio H. Ribeiro, Fabian Pedregosa, Paul van Mulbregt, and SciPy 1.0 Contributors. . *Nature Methods*, 17: 261–272, 2020. doi: 10.1038/s41592-019-0686-2.

(ref: 2013A&A...558A..33A) Astropy Collaboration, Thomas P. Robitaille, Erik J. Tollerud, Perry Greenfield, Michael Droettboom, Erik Bray, Tom Aldcroft, Matt Davis, Adam Ginsburg, Adrian M. Price-Whelan, Wolfgang E. Kerzendorf, Alexander Conley, Neil Crighton, Kyle Barbary, Demitri Muna, Henry Ferguson, Frédéric Grollier, Madhura M. Parikh, Prasanth H. Nair, Hans M. Unther, Christoph Deil, Julien Woillez, Simon Conseil, Roban Kramer, James E. H. Turner, Leo Singer, Ryan Fox, Benjamin A. Weaver, Victor Zabalza, Zachary I. Edwards, K. Azalee Bostroem, D. J. Burke, Andrew R. Casey, Steven M. Crawford, Nadia Dencheva, Justin Ely, Tim Jenness, Kathleen Labrie, Pey Lian Lim, Francesco Pierfederici, Andrew Pontzen, Andy Ptak, Brian Refsdal, Mathieu Servillat, and Ole Streicher. . *Astron. Astrophys.*, 558: A33, October 2013. doi: 10.1051/0004-6361/201322068.

(ref: Hunter:2007) J. D. Hunter. Matplotlib: A 2d graphics environment. *Computing in Science & Engineering*, 9 (3): 90–95, 2007. doi: 10.1109/MCSE.2007.55.

(ref: 2019ascl.soft07016R) Thomas Robitaille, Tom Rice, Chris Beaumont, Adam Ginsburg, Braden MacDonald, and Erik Rosolowsky. . Astrophysics Source Code Library, record ascl:1907.016, July 2019.

**Acknowledgements** X.M. is grateful to the financial support from China Scholarships Concil. We acknowledge all the developers for their open-source codes and packages **Numpy *(cite: harris2020array)***, **Scipy *(cite: 2020SciPy-NMeth)***, **Astropy *(cite: 2013A&A...558A..33A)***, **Matplotlib *(cite: Hunter:2007)***, **Astrodendro *(cite: 2019ascl.soft07016R)***, and **FERIA *(cite: 2022PASP..134i4301O)***, which were crucial in this work.

**Funding** T.L. acknowledges the supports by the National Key R&D Program of China (No. 2022YFA1603100), National Natural Science Foundation of China (NSFC) through grants No.12073061 and No.12122307, and the Tianchi Talent Program of Xinjiang Uygur Autonomous Region. B.Z. acknowledges support by the Natural Science Foundation of China (NSFC, grant No. U1831136 and U2031212) and Shanghai Astronomical Observatory (N-2020-06-09005). X.M acknowledges financial support from the program of China Scholarships Council 202304910546. G.G. and L.B. gratefully acknowledge support by the ANID BASAL project FB210003. A.H. thanks the support by the S. N. Bose National Centre for Basic Sciences under the Department of Science and Technology, Govt. of India and the the CSIR-HRDG, Govt. of India for the funding of the fellowship. X.L. acknowledges support from Strategic Priority Research Program of the Chinese Academy of Sciences Grant XDB0800100. PS was partially supported by a Grant-in-Aid for Scientific Research (KAKENHI Number JP23H01221) of JSPS. E.M. acknowledges funding from the Vilho, Yrjö ja Kalle Väisälän rahasto from the Finnish Academy of Science and Letters. M.J., J.V., and D.T. acknowledge support from the Research Council of Finland grant 348342. J.-E.L. was supported by the National Research Foundation of Korea (NRF) grant funded by the Korea government (MSIT) (grant numbers 2021R1A2C1011718 and RS-2024-00416859). This research was carried out in part at the Jet Propulsion Laboratory, which is operated by the California Institute of Technology under a contract with the National Aeronautics and Space Administration (80NM0018D0004). P.G., G.G. and L.Z. are supported by Chinese Academy of Sciences South America Center for Astronomy (CASSACA) Key Research Project E52H540201. N.J.E thanks the Astronomy Department of the University of Texas for research support.

**Author contributions** Conceptualization: XM, TL, XL, NJE, JH, CWL, SZ, KT, SD, QZ, JEL, MJ, LZ, GG Methodology: XM, QL, TL, XC, JH, KT, QZ, XL Investigation: XM, TL, XL, XC, JH, CWL, SD, DY, SRD, QZ, JOC Visualization: XM, TL, EM, SRD Supervision: TL, GLW, CWL, MJ, XL Writing–original draft: XM, TL, XL, KTK, QL, PFG, SZ, KT, SD Writing–review & editing: XM, TL, BZ, PFG, NJE, QZ, KTK, MJ, FX, WJ, HL, PS, GG, SQ, JMV, AT, ZR, SD, SL, QL, JH, PG, AH, YZ, JEL, SZ, EM, DT, LD, LB, PrG, XT, SRD, GW, CWL, JOC, YKZ, QG, KT, GLW, ZS Validation: XM, QL, TL, ZR, SL, HL, JH, CWL, YKZ, XL, JOC, XC, PFG Formal analysis: XM, QL, TL, XC, DY, JOC Funding acquisition: TL, BZ, CWL, GLW, XL, LZ Data curation: XM, TL, SZ, WJ, FX, LZ Software: XM, TL, FX Project administration: TL, GLW Resources: CWL, BZ, GLW, DY, XL, TL

**Competing interests** The authors declare they have no competing interests.

**Materials Availability** All data needed to evaluate the conclusions in the paper are present in the paper and/or the Supplementary Materials. The ALMA data presented in this work can be found on ALMA Science Archive under project codes 2019.1.00685.S, 2021.1.00095.S, and 2021.1.00455.T.

The maser data is available via <https://cdsarc.cds.unistra.fr/viz-bin/cat/J/A+A/684/A86>.

**Content for supplementary materials:**\
Figures:\
Fig. S[11](#spiral_stack): Stacked image of various gas tracers\
Fig. S[12](#cch_pvs): The position-velocity diagrams of CCH. The elements in this figure are the same as in Fig. [8](#h13cop_pvs)\
Fig. S[13](#pvs): The PV diagrams of various molecules.\
Fig. S[14](#intensity_profile): The intensity profiles of continuum emission and different molecular line emission\
Fig. S[15](#dcn_ch3oh): The moment maps of DCN and CH$_3$OH\
Fig. S[16](#chi2): The $\chi^2$ cube of the IRE fitting\
Fig. S[17](#ch3cn_mom_pv): The moment maps and PV diagrams of CH$_3$CN J=12-11 K=3-5 transitions\
Fig. S[18](#orien_schem): The schematic representation of the configuration of the envelope-disk system\
Fig. S[19](#outflow_sio_h2_maser): The spatial distribution of the outflow and shocked gas\
Fig. S[20](#co_channel): The channel maps of the blue lobe of CO outflow\
Fig. S[21](#spiral_model_continuum): The spiral model with the highest Pearson correlation coefficient.\
Fig. S[22](#co_spec): The spectra of CO, $\rm ^{13}CO$, and $\rm C^{18}O$\
Tables:\
Table S[\[parameterrange\]](#parameterrange): The parameter range and the best-fit parameter set in the $\chi^2$ grid search\
Table S[2](#tab:outflow): The outflow parameters\
Table S[3](#moltrans): The molecule species and transitions used in this study

**Content:**\
Figures:\
Fig. S[11](#spiral_stack): Stacked image of various gas tracers\
Fig. S[12](#cch_pvs): The position-velocity diagrams of CCH. The elements in this figure are the same as in Fig. [8](#h13cop_pvs)\
Fig. S[13](#pvs): The PV diagrams of various molecules.\
Fig. S[14](#intensity_profile): The intensity profiles of continuum emission and different molecular line emission\
Fig. S[15](#dcn_ch3oh): The moment maps of DCN and CH$_3$OH\
Fig. S[16](#chi2): The $\chi^2$ cube of the IRE fitting\
Fig. S[17](#ch3cn_mom_pv): The moment maps and PV diagrams of CH$_3$CN J=12-11 K=3-5 transitions\
Fig. S[18](#orien_schem): The schematic representation of the configuration of the envelope-disk system\
Fig. S[19](#outflow_sio_h2_maser): The spatial distribution of the outflow and shocked gas\
Fig. S[20](#co_channel): The channel maps of the blue lobe of CO outflow\
Fig. S[21](#spiral_model_continuum): The spiral model with the highest Pearson correlation coefficient.\
Fig. S[22](#co_spec): The spectra of CO, $\rm ^{13}CO$, and $\rm C^{18}O$\
Tables:\
Table S[\[parameterrange\]](#parameterrange): The parameter range and the best-fit parameter set in the $\chi^2$ grid search\
Table S[2](#tab:outflow): The outflow parameters\
Table S[3](#moltrans): The molecule species and transitions used in this study

Supplementary Fig. S[11](#spiral_stack) presents the stacked image of $\rm H^{13}CO^+$, CCH and 3 mm continuum.

Supplementary Fig. S[12](#cch_pvs) shows the PV diagrams of CCH along the selected paths.

Supplementary Fig. S[13](#pvs) shows the PV diagrams for DCN, H$_2$CO, HC$_3$N, SO, CH$_3$OH and C$^{18}$O cut along the major axis of the “bar". The gas kinematics can be decomposed into two modes: the elongated and velocity-coherent structure extending beyond 4$^{\prime\prime}$ and the diamond-shape structure with the clear spin-up feature. The velocity-coherent mode indicates the gas inflow along the “bar” while the “diamond” mode indicates the rotating and infalling motion at the center. The smooth transition between two modes may suggest that the gas is being transported to the central envelope and starts rotating.

Supplementary Fig. S[14](#intensity_profile) presents the intensity profiles of continuum emission and different molecular line emission along the “bar". The H$^{13}$CO$^+$ shows extended emission along the “bar” while CCH is less abundant at the center. Interestingly, despite the different angular resolution, the 3 mm continuum dust and C$^{18}$O in 1.3 mm observation show a similar extent, suggesting that C$^{18}$O is tracing a more flattened gas reservoir than DCN and 1.3 mm continuum, which is central dominant (the “nucleus”) with two shoulders and long tails (the “bar”) on both sides in the profiles.

Supplementary Fig. S[15](#dcn_ch3oh) shows the zoomed-in Moment 0 and Moment 1 maps of DCN and CH$_3$OH. Close to the “nucleus", both molecular lines show tails connected to larger-scale gas streamers, as outlined by cyan dashed lines.

Supplementary Fig. S[16](#chi2) shows the $\chi^2$ cube of the IRE fitting.

Supplementary Fig. S[17](#ch3cn_mom_pv) shows the moment maps and PV diagrams of CH$_3$CN J=12-11 K=3-5 transitions, which well reveal the geometry and kinematics of the pseudodisk.

Supplementary Fig. S[18](#orien_schem) is a schematic representation of the inversion of the line-of-sight velocity field between the envelope and the disk.

Supplementary Fig. S[19](#outflow_sio_h2_maser) shows the spatial distribution of CO outflow and shocked gas traced by SiO, $\rm H_2$, masers.

Supplementary Fig. S[20](#co_channel) shows the channel maps of $^{12}$CO blueshifted high-velocity emission. The jet direction revealed in higher-velocity channels is remarkably different from the one seen in lower-velocity channels, indicating potential jet precession.

Supplementary Table  S[\[parameterrange\]](#parameterrange) lists the parameter space of the $\chi^2$ search, and the best-fit parameter set with the corresponding lowest $\chi^2$ value.

Supplementary Table  S[2](#tab:outflow) summarizes the calculated outflow parameters.

Supplementary Table S[3](#moltrans) summarizes the molecule species and the transitions used in this study.

Supplementary Fig. S[21](#spiral_model_continuum) presents the best spiral model on the 3 mm continuum emission data.

Supplementary Fig. S[22](#co_spec) shows the spectra of $^{12}$CO, $^{13}$CO, and C$^{18}$O, and the selected velocity ranges for outflow.

![](fig/spiral_stackmom8.pdf)

![](fig/cch_pvs.pdf)

![](fig/pv_6mols.pdf)

![](fig/intensity_profile.pdf)

![](fig/DCN_CH3OH.pdf)

![](fig/chi2grid_CH3OH.pdf)

![](fig/ch3cn_mom_pv.pdf)

![](fig/orientation.pdf)

![](fig/cont_sio_co_maser.pdf)

![](fig/co_channelmap.pdf)

![](fig/model_pearson.pdf)

![](fig/CO_spec.pdf)

| Parameters                    |  Range   | Best value | Reduced $\chi^2$ |
|:------------------------------|:--------:|:----------:|:----------------:|
| $M \ [M_\odot]$               |  20–70   |     45     |       3.4        |
| $i$ $\ [^\circ]$              |   0–20   |     6      |                  |
| $r_{\text{CB}} \ [{\rm au}]$  |  0–200   |     60     |                  |
| $r_{\text{out}} \ [{\rm au}]$ | 800–1200 |    950     |                  |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Lobe | $\Delta v$ | $\lambda_{\rm max}$ | $t_{\rm dyn}$ | $P_{\rm out}$ | $F_{\rm out}$ | $\dot{M}_{\rm w}$ |
|  | km s$^{-1}$ | $10^{-3}$ pc | $10^3\,yr$ | 10$^{-1}\,M_{\odot}~{\rm km~s^{-1}}$ | $10^{-3}~M_{\odot}~{\rm km~s^{-1}~yr^{-1}}$ | $10^{-7}\,M_{\odot}$ yr$^{-1}$ |
| Blue | \[-30,0\] | 49.91 | 1.11 | 3.16 | 2.85 | 5.70 |
| Red | \[20,50\] | 18.41 | 0.41 | 0.73 | 1.79 | 3.59 |

: Outflow parameters of I18134-1942

| Species |  | Rest Frequency (GHz) | $E_u$ (K) |
|:---|:---|:---|:---|
| 3 mm |  |  |  |
| $\rm H^{13}CO^+$ | $J=1-0$ | 86.754288 | 4.16 |
| CCH | $N_{J,K}=1_{3/2,2}-0_{1/2,1}$ | 87.316898 | 4.19 |
| 1.3 mm |  |  |  |
| SiO | $J=5-4$ | 217.10498 | 31.26 |
| $\rm H_2CO$ | 3(0, 3)-2(0, 2) | 218.222192 | 20.96 |
| DCN | $J=3-2$ | 217.238538 | 20.85 |
| $\rm HC_3N$ | $J=24-23$ | 218.324723 | 130.98 |
| $\rm CH_3OH$ | $4_2-3_1~E1~vt=0$ | 218.440063 | 45.46 |
| $\rm CH_3CN$ | $J=12-11, K=3$ | 220.7090165 | 133.16 |
|  | $J=12-11, K=4$ | 220.6792869 | 183.15 |
|  | $J=12-11, K=5$ | 220.6410839 | 247.40 |
| C$^{18}$O | $J=2-1$ | 219.560354 | 15.81 |
| SO | 6(5)-5(4) | 219.949442 | 34.98 |
| $^{12}$CO | $J=2-1$ | 230.538 | 16.59 |

: The molecule species and transitions used in this study

</paper>

Write the methods card for this paper.