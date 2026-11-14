# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...989....7T\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...989....7T",
 "title": "The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO). VII. Testing Accretion Mechanisms from Disk Population Synthesis",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Tabone, Benoît",
 "n_authors": 27,
 "arxiv_id": "2506.10742",
 "doi": "10.3847/1538-4357/adc7b1",
 "alma_projects_linked_by_archive": [
  "2021.1.00128.L"
 ]
}
```

Paper text:
<paper>
# The ALMA Survey of Gas Evolution of PROtoplanetary Disks (AGE-PRO):\
VII. Testing accretion mechanisms from disk population synthesis

## Abstract

The architecture of planetary systems depends on the evolution of the disks in which they form. In this work, we develop a population synthesis approach to interpret the AGE-PRO measurements of disk gas mass and size considering two scenarios: turbulence-driven evolution with photoevaporative winds and MHD disk-wind-driven evolution. A systematic method is proposed to constrain the distribution of disk parameters from the disk fractions, accretion rates, disk gas masses, and CO gas sizes. We find that turbulence-driven accretion with initially compact disks ($R_0 \simeq 5-20~$au), low mass-loss rates, and relatively long viscous timescales ($t_{\nu,0} \simeq 0.4-3~$Myr or $\alpha_{SS} \simeq 2-4 \times 10^{-4}$) can reproduce the disk fraction and gas sizes. However, the distribution of apparent disk lifetime defined as the $M_D/\dot{M}_*$ ratio is severely overestimated by turbulence-driven models. On the other hand, MHD wind-driven accretion can reproduce the bulk properties of the disk populations from Ophiuchus to Upper Sco assuming compact disks with an initial magnetization of about $\beta \simeq 10^5$ ($\alpha_{DW} \simeq 0.5-1 \times 10^{-3}$) and a magnetic field that declines with time. More studies are needed to confirm the low masses found by AGE-PRO, notably for compact disks that question turbulence-driven accretion. The constrained synthetic disk populations can now be used for realistic planet population models to interpret the properties of planetary systems on a statistical basis.

# Introduction

With more than 5000 exoplanets detected so far[^1], planet formation appears to be a widespread phenomenon in disks orbiting young stars (cite: 2019ApJ...874...81F). The more striking results obtained by the exoplanet community are the large diversity in the properties of exoplanetary systems and the occurrence of specific kinds of systems. The next challenge is to understand how different evolutionary pathways of planet-forming disks lead to the diversity and occurrence of planetary systems (cite: 2016JGRE..121.1962M).

Recent models have already attempted to include many steps of planet formation in disk evolution models to predict the properties of exoplanets at a population level (cite: 2023ASPC..534..717D). Yet the evolution of gaseous disks remains vastly unknown despite its paramount importance in every step of planet formation (cite: 2023ASPC..534..501M). One of the main limiting factors is the need for unbiased surveys of young stars of different ages since an individual disk cannot be followed up across its lifetime. Pioneering surveys have already unveiled some of the basic properties of disks. Infrared excess and accretion signatures in clusters of different ages indicate that disks disperse quickly after a typical timescale of 2-5 Myr (cite: 2010A&A...510A..72F; 2014A&A...561A..54R), depending on the mass of the host star and the vicinity of massive stars (cite: 2015A&A...576A..52R; 2022EPJP..137.1132W). Surveys from the UV to the near-IR have also shown that almost all disks exhibit signs of accretion with accretion rates scaling with stellar mass and declining with time (cite: 2016ARA&A..54..135H; 2017A&A...600A..20A; 2017A&A...604A.127M; 2023ApJ...945..112F).

Over the past decades, disk dispersal and disk accretion have been explained by two distinct processes. In the classical picture of viscous disks, popularized by (cite: 1973A&A....24..337S), disks accrete via the radial transport of angular momentum mediated by turbulence. The origin of turbulence can be the magnetorotational instability (MRI) or hydrodynamical instabilities such as the vertical shear instability or the gravitational instability (cite: 2023ASPC..534..465L; 2016ARA&A..54..271K). On the other hand, disk dispersal is explained by photoevaporative winds launched from the disk atmosphere heated by energetic radiation from the star (cite: 1994ApJ...428..654H; 2014prpl.conf..475A). The relevant energy of the photons remains debated. Hydrogen ionizing UV photons (EUV) would have a limited impact due to efficient screening of the disk layers but either X-ray or FUV photons can penetrate the disk’s upper layers and deposit enough energy to drive a thermal wind outward of 1-10 au (cite: 2010MNRAS.401.1415O; 2009ApJ...690.1539G; 2018ApJ...857...57N). Early models combining turbulence-driven accretion and photoevaporation were able to account for the observed accretion rates and disk dispersal time (cite: 2006MNRAS.369..229A; 2012MNRAS.422.1880O).

However, theoretical works including the weak coupling between the magnetic field and the gas show that MRI cannot be triggered in large portions of disks called dead-zones (cite: 1996ApJ...457..355G; 2011ApJ...736..144B; delage2022). Alternatively, MHD disk-winds can efficiently drive accretion across both the dead zones and MRI active regions by extracting angular momentum vertically (cite: 1982MNRAS.199..883B; 1997A&A...319..340F; 2013ApJ...769...76B). MHD disk winds would naturally account for the observations of winds revealed by a wide range of tracers from the millimeter to the optical (cite: 2017A&A...607L...6T; 2018A&A...618A.120L; 2025NatAs...9...81P). The only requirement is that the disk is embedded in a magnetic field with a non-vanishing magnetic flux. It should be noted that while early MHD disk-wind models used strongly magnetized disks, resulting in very low disk masses, recent theoretical work demonstrated the ability of MHD disk-winds to operate even with a mid-plane magnetization as low as $\beta = 10^5$ where the $\beta$ parameter is the ratio between thermal and magnetic pressure (cite: 2017A&A...600A..75B). Disk dispersal in MHD wind-driven accretion remains an open question due to the lack of numerical simulations running on the long-time scale. Still, simple disk evolution models show that if the magnetic field strength does not decline too fast, disks can be dispersed in a short dispersal phase (cite: 2013ApJ...778L..14A; 2016ApJ...821...80B; 2022MNRAS.512.2290T).

Today, our lack of knowledge on which mechanism drives disk accretion and dispersal constitutes a fundamental hurdle in our understanding of planet formation and migration. If accretion is driven by MHD disk-winds, every step of planet formation will be impacted. To name a few examples, MHD disk-winds can create pressure bumps where dust grows (cite: 2018MNRAS.477.1239S; 2020A&A...639A..95R), pebble accretion is expected to be amplified in low-turbulence disks (cite: 2024Icar..41716085Y), and planet migration pattern can be profondly impacted by the different local gas flow (cite: 2022A&A...658A..32L; 2023A&A...677A..70W) with possibly outward type-II planet migration for highly magnetized disks (cite: 2020A&A...633A...4K). 1D disk evolution models, under specific prescriptions, also predict the formation of a gas depletion in the inner disk, altering type-I migration (cite: 2015A&A...584L...1O; 2018A&A...615A..63O), a proposal that calls for global numerical simulation running on secular timescale. In other words, if accretion is effectively driven by MHD winds, planet-formation scenarios and planet population synthesis models need to be revised.

However, infrared excess or accretion signatures are indirect probes of the evolution of the bulk disk. It is only with ALMA that fundamental properties like disk masses and sizes can now be probed on statistically representative samples. The first surveys focused on the millimeter (mm) dust emission giving access to the continuum flux and continuum size in the close-by star-forming regions (cite: andrews2005; andrews2013; ricci2010; 2016ApJ...827..142B; 2017AJ....153..240A; 2019A&A...626A..11C; 2022A&A...661A..53V).

It is unclear though to what extent dust mm flux can inform us about the gas. Because of dust radial drift, one would naturally expect the continuum disk size and the continuum luminosity to be poor proxies for the disk gas size and mass (cite: 2014prpl.conf..339T; 2020MNRAS.498.2845S; 2021MNRAS.507..818T; 2022MNRAS.514.1088Z).

Yet, using mm continuum luminosity, (cite: 2016A&A...591L...3M) found a correlation between disk mass (assumed to be 100 times the dust disk mass) and accretion rate with a typical ratio of $M_D/\dot{M}_{*} \simeq 1-3~$Myr.

Surveys at the population level offer a unique opportunity to challenge disk evolution scenarios and the recent ALMA observations have triggered a renewed interest in disk evolution models. (cite: 2017MNRAS.472.4700L) and (cite: 2017ApJ...847...31M) showed that the $M_D - \dot{M}_{*}$ correlation

can be naturally reproduced by viscous models with a significant spread in the viscous timescale and disk’s age. Yet, these models did not consider disk dispersal, which can affect the $M_D - \dot{M}_{*}$ correlation (cite: 2020MNRAS.492.1120S). When photoevaporation is included, viscous models can still reproduce the overall $M_D - \dot{M}_{*}$ but remain dependent on dust evolution models (cite: 2019A&A...628A..95M; 2020MNRAS.498.2845S; 2023A&A...673A..78E). The development of 1D disk evolution models including MHD disk-winds (cite: 2016A&A...596A..74S; 2016ApJ...821...80B; 2022MNRAS.512.2290T) now permits confronting the predictions of MHD wind-driven accretion with disk demographics. In this context, (cite: 2022MNRAS.512L..74T) showed that simple MHD wind-driven evolution models can naturally reproduce the $M_D - \dot{M}_{*}$ correlation and the rapidity of disk dispersal.

Today, the ALMA large program AGE-PRO (cite: AGEPRO_I_overview), gives access to the gas evolution thanks to deep observations of molecular lines over a sample of 30 disks located in three star-forming regions of different ages: Ophiuchus (cite: AGEPRO_II_Ophiuchus), Lupus (cite: AGEPRO_III_Lupus), and Upper Scorpius (cite: AGEPRO_IV_UpperSco). The outcome of AGE-PRO is twofold. First, the inclusion of N$_2$H$^+$ and CO isotopologues in the spectral setup permits estimates of disk gas masses (cite: 2019ApJ...881..127A; 2022ApJ...926L...2T) using extensive grids of thermochemical models (cite: AGEPRO_V_gasmasses). The disk mass estimates are therefore not hampered by assumptions on dust optical properties and gas-to-dust ratio.

Secondly, the CO disk sizes, a key diagnostic for disk physical size (cite: 2023MNRAS.518L..69T; 2023ApJ...954...41T), are now measured taking into account beam convolution effects (cite: AGEPRO_XI_gas_disk_sizes).

In this paper, we develop a disk population synthesis approach to interpret the results of the ALMA AGE-PRO large program. A systematic approach is proposed to constrain the distribution of disk parameters from not only the disk mass and size inferred by AGE-PRO but also accretion properties and disk fraction. In Sec. [2](#sec:model), the disk evolution models are presented along with the observational constraints and the population synthesis approach. The fitting procedure is then applied to each scenario in Sec. [3](#sec:results). The implications of the present work and its limitations are discussed in Sec. [4](#sec:discusion) and the findings are summarized in Sec. [\[sec:conclusion\]](#sec:conclusion).

# Model

## Individual disks

The evolution of an individual disk is computed using a 1D formalism, where the MHD equations are integrated in the vertical direction. The radial transport of angular momentum is described following the (cite: 1973A&A....24..337S) parametrization with the generalization proposed by (cite: 2022MNRAS.512.2290T). Our choice in the parameterization of disk evolution has the major advantage of facilitating the comparison between turbulence-driven and MHD wind-driven evolution. The values of the parameters can also be easily compared with the results of numerical simulations. The parameters of the model are summarized in Table [1](#table:model). In both scenarios, the evolution of an individual disk is set by 4 parameters: initial disk mass $M_0$ and radius $R_0$, the generalized $\alpha$ parameter (or equivalently the accretion timescale $t_{acc, 0}$ or the viscous timescale $t_{\nu, 0}$), and a parameter quantifying the wind mass-loss rate. For the MHD disk-wind model, an additional parameter, $\omega$, controls the secular evolution of the magnetic field. We only consider isolated disks that are not fed by any envelope or streamer. The time $t=0$ can therefore be considered as the end of the Class I phase, and as several of the AGE-PRO Oph targets are Class I, we assume that the Oph disks represent the time zero in our models. Neglecting the impact of early accretion is further justified by the mass of the residual envelope around the Ophiuchus sources being smaller than the disk masses (cite: AGEPRO_II_Ophiuchus). We further neglect the impact of mild external UV irradiation, which is futher studied in the case of turbulence-driven accretion by (cite: AGE-PRO_externalPE) for the Upper Sco AGE-PRO sample.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
| Parameter | Symbol | Range of median value | Adopted |
|  |  |  | spread$^{(a)}$ |
|  |  | **Initial conditions** |  |
| **Initial disk size** | $R_0$ | 5-20 au | 0.3 |
| **Initial disk mass** | $M_0$ | $10^{-4}$ - $10^{-1}$ $M_{\odot}$ | 0.6 |
|  |  | **MHD wind model** |  |
| **$\alpha$ parameter** | $\alpha_{DW}$ | $10^{-4}-10^{-2}$ | 0.2 |
| Accretion timescale | $t_{acc,0}$ | $0.1-2\,$Myr | \*\* |
| **$\omega$ parameter** | $\omega$ | $0.25-0.5$ | 0 |
| **Magnetic lever arm** | $\lambda$ | 2-20 | 0 |
| Ejection-to-accretion | $f_M$ | 0.1-10 | \*\* |
|  |  | **Turbulent model** |  |
| **$\alpha$ parameter** | $\alpha_{SS}$ | $10^{-4}-10^{-2}$ | 0.2 |
| Viscous timescale | $t_{\nu,0}$ | $0.1-5\,$Myr | \*\* |
| **Wind mass-loss rate** | $\dot{M}_{PEW}$ | $10^{-11}$-$10^{-6}$ M$_{\odot}$/yr  | 0.3 |

: Summary of the parameters of the population models with the free parameters outlined in bold font.

\
$^{(a)}$ This corresponds to the spread of the lognormal distributions used for synthetic populations and measured in dex. Zero range corresponds to parameters constant across a disk population. \*\* correspond to parameters which are derived from other parameters.

### Turbulence-driven evolution

![](example_turbulence_v3.pdf)

In the turbulence-driven scenario, the evolution of the surface density profile $\Sigma(r,t)$ is governed by $$\begin{equation}
\begin{split}
       \frac{\partial \Sigma}{\partial t} = \frac{3}{R}\frac{\partial}{\partial R} \left\{ \frac{1}{R \Omega} \frac{\partial}{\partial R} \left(R^2\alpha_{SS} \Sigma c_s^2 \right) \right\}
       - \dot{\Sigma}_{PEW}(R),
\end{split}
\label{eq:master-eq-viscous}
\end{equation}$$ where $\alpha_{SS}$ is the Shakura-Sunyaev parameter and $\dot{\Sigma}_{PEW}(R)$ is the photoevporative wind mass-loss rate per unit surface area. In this work, we adopt the radial profile of $\dot{\Sigma}_{PEW}(R)$ computed by (cite: 2021MNRAS.508.3611P) for a stellar mass of $M_*= 0.5~$M$_{\odot}$. The latter work utilizes hydrodynamical simulations including heating by stellar X-rays and neglecting molecule formation or shielding by a putative inner disk-wind ($\lesssim 1~$au). Instead of relying on the values of mass-loss rates computed by numerical simulations, we take the total mass-loss rate as a free parameter to scale the mass-loss rate profile. This allows us to mitigate the discrepancies in terms of mass-loss rates found in different numerical simulations (cite: 2023ASPC..534..567P). The importance of the radial profile of $\dot{\Sigma}_{PEW}(R)$ and the comparison with the total mass-loss rate provided in the literature is discussed in Sec. [4](#sec:discusion). We further assume that the mass-loss rate is constant over time. This implies that we neglect the dependency of the photoevaporation rate on the disk structure, in line with the findings of (cite: 2012MNRAS.422.1880O) and the effect of the attenuation of the stellar radiation field by an evolving inner wind, as well as an evolving stellar radiation field and flares. We stress that the photoevaporative mass-loss rates $\dot{M}_{PEW}$ reported in this study are effective mass-loss rates formally calculated as $\dot{M}_{PEW} = \int_0^{+\infty} \dot{\Sigma}_{PEW}(R) 2 \pi R dR$ and used to normalize the $\dot{\Sigma}_{PEW}(R)$ profile. When the local surface density drops to zero, no mass-loss rate is assumed. Therefore, for compact disks for which the surface density rapidly drops to zero in the outer region where $\dot{\Sigma}_{PEW}(R)$ is non-vanishing, or for disks with gaps, the true mass-loss rate is lower than the reported $\dot{M}_{PEW}$ value.

Numerical simulations of MRI turbulence predict a weak correlation between the value of $\alpha_{SS}$ and the disk magnetisation as quantified by $\beta$, the ratio between the gas and magnetic pressure (cite: 2023ASPC..534..465L). As a consequence, $\alpha_{SS}$ could vary in time as the disk evolves but this also depends on the poorly known evolution of the magnetic field strength. For simplicity, we assume $\alpha_{SS}$ to be constant in time.

The radial profile of $\alpha_{SS}$ is taken to be constant, as often assumed in disk evolution models (cite: 2017ApJ...847...31M; 2017MNRAS.472.4700L). Theoretical works predict steep variations in the $\alpha_{SS}$ profile depending on the ability of the MRI to be triggered. Notably within $~0.1-0.5~$au, the ionisation of alkali metals ensures efficient MRI, possibly coupled to MHD disk-winds. The bulk part of the disk and the stellar accretion rate are not expected to be affected by such a high $\alpha_{SS}$ region as the gas slowly advected from the outer to the inner regions will rapidly flow across the inner highly turbulent region down to the magnetosphere of the star. Our value of $\alpha_{SS}$ is therefore representative of the bulk part of the disk and we adopt an inner disk radius of 0.1 au.

Initially, the surface density profile follows the self-similar solution of (cite: 1974MNRAS.168..603L) with $$\begin{equation}
    \Sigma(R,t) = \frac{M_0}{2\pi R_0^2} \left( \frac{R}{R_0}\right)^{-1} e^{-R/R_0},
\end{equation}$$ where $M_0$ is the initial disk mass and $R_0$ is the initial disk characteristic size. We further define the initial viscous timescale as $$\begin{equation}
    t_{\nu,0} \equiv \frac{R_0}{3 \epsilon_{0} c_{S,0} \alpha_{SS}} 
    \label{eq:def-tnu}
\end{equation}$$ where $c_{s,0}$ and $\epsilon_0$ are the sound speed and the disk aspect ratio at $R_0$. In this work, we assume that $T \propto R^{-1/2}$ and $\epsilon(R=1~\text{au}) = 3.33 \times 10^{-2}~(M_*/1M_{\odot})^{-1/2}$. This leads to the following relation $$\begin{equation}
    t_{\nu,0} = 0.34~\text{Myr}~\left( \frac{\alpha_{SS}}{10^{-3}}  \right)^{-1} \left( \frac{R_0}{10~au}  \right) \left( \frac{M_*}{0.5~M_{\odot}}  \right)^{1/2}.
\end{equation}$$

The different evolution pathways under the effect of turbulence and photoevaporative wind are illustrated in Fig. [1](#fig:example_turbulence) with two solutions. The solutions share the same viscous timescale, initial disk mass, and total mass-loss rate but differ in their initial disk size. Both lead to a disk dispersal time, defined as the time when accretion stops, of about 3-4 Myr. The first example (top left panel) has already been extensively described in the literature and corresponds to a relatively large disk of $R_0=20~$au. As the disk evolves, it spreads radially until photoevaporation opens a gap around 2-5 au where the mass-loss rate profile $\dot{\Sigma}_{PEW}$ peaks (cite: 2021MNRAS.508.3611P). Following the gap opening, the inner disk is rapidly drained and a relic disk remains. This behavior is reflected in the evolution of the accretion rate and disk mass (right panels, blue lines): after a decline of a typical timescale of $t_{\nu,0}$, the accretion rate quickly vanishes whereas the disk mass remains relatively constant, even after the accretion stops. We however stress that this so-called "relic disk problem" is only the result of our simple prescription of photoevaporation mass-loss rate profile which does not account for the direct irradiation of the cavity following gap opening. In the following, a disk is considered to be dispersed when the stellar accretion rate drops below a threshold of $10^{-12}~M_{\odot}/yr$.

In the second solution, the initially more compact disk ($R_0 = 10~$au) does not spread despite radial transport of angular momentum. This surprising feature is because the bulk of the disk and its outermost region reside where the wind-mass-loss rate is significant. The consequence is that the wind does not open a gap but truncates the disk. This results in a drastically different evolution: the outer disk is eroded by the wind and the the inner disk is drained due to turbulent accretion. Therefore, the disk mass, accretion rate, and size jointly decrease before full disk dispersal. This evolution is somewhat similar to that of a large disk exposed to external UV since external photoevaporation removes mass from the outer disk (cite: clarke2007).

### MHD wind-driven evolution

![](example_wind-MHD_v3.pdf)

Following the formalism of (cite: 2022MNRAS.512.2290T) the evolution of the surface density under the effect of an MHD disk-wind is described as

$$\begin{equation}
       \frac{\partial \Sigma}{\partial t} = 
       \frac{3}{2 R}  \frac{\partial}{\partial R} \left[ \frac{\alpha_{DW} \Sigma c_s^2}{\Omega} \right] + \frac{3}{R}\frac{\partial}{\partial R} \left\{ \frac{1}{r\Omega} \frac{\partial}{\partial R} \left(r^2\alpha_{SS} \Sigma c_s^2 \right) \right\} - \dot{\Sigma}_{MHD-DW},
\label{eq:master-eq-MHD-DW}
\end{equation}$$ where $\alpha_{DW}$ parameterizes the wind torque and $\dot{\Sigma}_{MHD-DW}$ the mass-loss rate of the wind. In contrast with photoevaporative winds, the mass-loss rate of the MHD disk-wind depends on the extraction of angular momentum as $$\begin{equation}
\dot{\Sigma}_{MHD-DW} = \frac{3 \alpha_{DW} \Sigma c_s^2}{ \textcolor{black}{4} (\lambda-1) R^2 \Omega},
\label{eq:sigma_dot_MHD-DW}
\end{equation}$$ where $\lambda$, the magnetic lever arm parameter (cite: 1982MNRAS.199..883B), quantifies the efficiency of the wind to carry out angular momentum. The lower the $\lambda$, the more mass is required to be launched to drive disk accretion. A considerable advantage of this parameter is that $\lambda$ can be estimated from wind observations (cite: 2006A&A...453..785F; 2020A&A...640A..82T). Observations typically find $\lambda \simeq 2-6$ (cite: 2017A&A...607L...6T; 2020A&A...634L..12D; 2021ApJS..257...16B; 2024A&A...686A.201N) and in this work we explore a wide range of $\lambda$ values (Table [1](#table:model)). In Eq. ([\[eq:master-eq-MHD-DW\]](#eq:master-eq-MHD-DW)), $\alpha_{SS}$ quantifies radial transport by either turbulence or by a laminar torque emerging from the radial component of the magnetic field which is usually negligible compared to vertical torque.

In this work, we adopt the analytical solutions of (cite: 2022MNRAS.512.2290T) in the absence of radial transport of angular momentum ($\alpha_{SS} = 0$). The analytical solutions further assume a constant $\lambda$ value in space and time and a constant $\alpha_{DW}$ across the disk. The surface density profile is given by $$\begin{equation}
       \Sigma(R,t) = \Sigma_c(t) (R/R_0)^{-1+\xi} e^{-R/R_0},
\label{eq:sigma_ansatz}
\end{equation}$$ where $\Sigma_c(t)$ is the characteristic surface density, $\xi = 1/[2(\lambda-1)]$ is the mass ejection index, and $R_0$ is the characteristic disk radius. A considerable source of uncertainty in MHD wind-driven disk evolution is the secular evolution of the magnetic field strength since $\alpha_{DW} \propto B_z B_{\phi}/\Sigma$. Here, we use the "$\Sigma_c$ dependent wind torque" solutions of (cite: 2022MNRAS.512.2290T) where the evolution of the wind torque is parameterized as $\alpha_{DW} = \alpha_{DW}(0) (\Sigma_c(t)/\Sigma_c(0))^{-\omega}$, where $\alpha_{DW}(0)$ is the initial $\alpha_{DW}$ and $\omega$ is a free parameter. The case $\omega=1$ describes a constant magnetic field strength (assuming a constant $B_z/B_{\phi}$ ratio). This leads to the following evolution of the disk mass and accretion rate: $$\begin{equation}
\begin{split}
    M_{D}(t)& = M_0 \left( 1-\frac{\omega}{2 t_{acc,0}} t \right)^{1/\omega}, \\
    \dot{M}_{*}(t)& = \frac{M_0}{2 t_{acc,0} (1+f_{M})} \left( 1-\frac{\omega}{2 t_{acc,0}}t \right)^{-1+1/\omega},
\end{split}
\label{eq:MHD-DW_anal-solution}
\end{equation}$$

where $$\begin{equation}
    f_M  \equiv \dot{M}_W/\dot{M}_*= \left(R_0/R_{in} \right)^{\xi}-1
\end{equation}$$ is the mass ejection-to-accretion ratio. $t_{acc,0}$ is a generalization of the viscous timescale (see Eq. ([\[eq:def-tnu\]](#eq:def-tnu))). Following the same assumption about the disk thermal structure as for the turbulent case, the accretion timescale is: $$\begin{equation}
    t_{acc,0} = 0.34~\text{Myr}~\left( \frac{\alpha_{DW}}{10^{-3}}  \right)^{-1} \left( \frac{R_0}{10~\text{au}}  \right) \left( \frac{M_*}{0.5~\text{M}_{\odot}}  \right)^{1/2}.
\end{equation}$$

The essential features of the solution is illustrated in Fig. [2](#fig:example_MHD-wind) with two values of $\omega$. In both cases, the surface density profiles preserve their shape while decreasing in absolute value. The angular momentum is indeed transported vertically without the need for radial expansion. We however stress that this is a property of the solution related to its initial condition. For sharp cuts in the outer disk, the disk can shrink since wind-driven accretion acts as an advection of gas. The latter situation is however not realistic since any turbulent or laminar radial stress in the early phase leads to a smoothly declining outer surface density profile. We note that the alternative model of (cite: 2016A&A...596A..74S) predicts the formation of a cavity, reminiscent of transition disks. Whereas cavities sustained by MHD disk-winds are a stable configuration (cite: 2022A&A...667A..17M), gap opening has never been characterized in global numerical simulations. Pending simulations on secular timescales, we adopt here disk evolution solutions that do not introduce artificial features in the surface density profile. The second property of MHD wind-driven evolution is the dispersal of the disk after a finite time due to rapid disk draining. Therefore, our MHD wind-driven solution accounts for both, accretion and dispersal. More specifically, the disk dispersal time depends on $t_{acc,0}$ and $\omega$ as $$\begin{equation}
   t_{disp} = 2 t_{acc,0}/ \omega.
\end{equation}$$ In both solutions, we choose $t_{acc,0}$ so that the two cases share the same dispersal time (see Fig. [2](#fig:example_MHD-wind), right panels). This highlights the essential effect of the $\omega$ parameter, which describes the evolution of the magnetic field strength. Higher values of $\omega$ lead to a rather constant disk mass and a high stellar accretion rate before dispersal. Therefore, for a given dispersal time, a disk with a higher $\omega$ value spends more time in a high mass and high accretion rate phase. This property is essential for the evolution of synthetic populations. Finally, we note that from Eq. [\[eq:MHD-DW_anal-solution\]](#eq:MHD-DW_anal-solution) the value of $\lambda$ does not affect the disk mass but the accretion rate by a factor $f_M +1 = (R_0/R_{in})^{1/2[\lambda-1]}$.

## Population synthesis with `Diskpop`

The observations provide us with the properties of disk populations of different ages and not with the evolution of individual disks. To simulate the evolution of disk populations, we use the `Diskpop` python package (cite: 2024arXiv240721101S). As a first step, the code randomly picks the values of the parameters for a sample of disks following a user-defined probability distribution and possible correlations between these parameters. The gas evolution of each disk is then computed by solving numerically Eq. ([\[eq:master-eq-viscous\]](#eq:master-eq-viscous)) or ([\[eq:master-eq-MHD-DW\]](#eq:master-eq-MHD-DW)), or using analytical solutions with the option of including dust evolution. The output of `Diskpop` is then analyzed using the `Popcorn` package (cite: 2024arXiv240721101S).

Throughout this paper, the synthetic populations are made of 400 disks by default and we consider only gas evolution. When building a synthetic disk population, the 4 free disk parameters outlined in bold font in Table [1](#table:model) and detailed above translate into 4 probability distributions. We assume that the distributions of the 4 disk parameters are not correlated and follow a log-normal distribution. Therefore, our population model is controlled by 8 free population parameters: a median and a spread for each disk parameter. The MHD disk-wind model has a fifth free parameter, $\omega$, for which only two values are explored. Following (cite: 2022MNRAS.512L..74T), a too-low value of $\omega$ produces disks with no detectable accretion signatures but significant mass which would lead to a strong difference between the dispersal time inferred from accretion signatures and IR excess. $\omega >1$ are also unrealistic since they would correspond to disks with increasing magnetic field strength (cite: 2022MNRAS.512.2290T).

Fitting the properties of disk populations using a population synthesis approach can appear as an under-constrained problem. Here, we propose a rationalized approach to map the parameter space and alleviate the degeneracies in a step-by-step process.

### Observational data

![](Observables_v6.pdf)

The main observational data to be confronted with population synthesis are shown in Figure [3](#fig:observables). Our synthetic populations are designed to describe the evolution of isolated disks. Therefore, we consider the t=0 age as the end of the Class I phase and take the Ophiuchus AGE-PRO sample as representative of this initial condition. As discussed in (cite: AGE-PRO_I-overview), there is a significant spread in the isochronal ages of each source for the Lupus and Upper Sco AGE-PRO samples with overlap between the two regions. Considering the considerable systematic uncertainties in the age determination, we adopt a median age of 2 Myr for the Lupus and 4 Myr for the Upper Scorpius AGE-PRO sample with a typical range of 2 and 4 Myr, respectively. We note that the sources selected by AGE-PRO in Upper Sco are part of the youngest sources of this star-forming region. Therefore, our adopted median age of the AGE-PRO Upper Sco sample is shorter than the median age of the entire cluster which is taken to be $7~Myr$. This results in an age difference between the median disk mass and size, estimated from the AGE-PRO sub-sample (Fig. [3](#fig:observables), bottom panels), and the median accretion rate evaluated from a less biased sample (top right panel).

The disk fraction (top left panel) stems from the compilation of (cite: 2010A&A...510A..72F) of infrared excess which is consistent with other works (cite: 2014A&A...561A..54R) and representative of the stellar mass targeted by AGE-PRO (cite: 2015A&A...576A..52R). In our models, we neglect the effect of multiplicity which significantly reduces the disk lifetime for close-in binaries (cite: kraus2012). We corrected the disk fraction of (cite: 2010A&A...510A..72F) by applying a multiplicative factor of 1.2 to match the disk fraction around single or wide binaries determined by (cite: kraus2012). The disk fraction is interpreted as the cumulative probability distribution of the disk lifetime. By assuming that disk lifetimes follow a lognormal distribution, we fit the disk fraction by an error function (see black line Fig. [3](#fig:observables), top left). We estimate a spread of about 0.3 dex and a median value of the disk lifetime of $3\,$Myr.

The accretion rates shown in Figure [3](#fig:observables) stem from the compilation of (cite: alcala2014; alcala2017; 2023ASPC..534..539M) for Lupus and (cite: 2023ApJ...945..112F) for the Upper Sco star-forming regions. We selected the stars that are within the bin of AGE-PRO stellar masses ($M_*=0.3-0.7M_{\odot}$). We stress that the sample of (cite: 2023ApJ...945..112F) reports upper limits for $50\%$ of the sources. Therefore, the median value of the accretion rate should be considered as an upper limit. Compared to the pioneering survey of (cite: 2020A&A...639A..58M) the sample of (cite: 2023ApJ...945..112F) is larger (12 versus 29 sources within the AGE-PRO stellar mass range) thought using only H$\alpha$ line flux as a proxy of the accretion rate. Still, the two studies lead to similar median accretion rates for Upper Sco.

Overall, we find that the median accretion rate decreases by a factor of at least 3 from Lupus to Upper Sco with a large spread of $0.8$ dex for each region.

The distribution of disk size and mass obtained by the AGE-PRO program is also represented in Figure [3](#fig:observables) as derived in (cite: AGEPRO_XI_gas_disk_sizes) and (cite: AGEPRO_V_gasmasses), respectively. The observed CO gas sizes, denoted as $R_{CO,90\%}$ or simply $R_{CO}$, correspond to the radius that encompasses 90$\%$ of the total CO flux and are evaluated by correcting for the beam of the observations. A major caveat when analyzing disk size is the conversion between the actual disk size, i.e. the radius encompassing the majority of disk mass, and the observed CO disk size (cite: 2023ApJ...954...41T). A possible strategy to extract the predicted value of $R_{CO,90\%}$ in the population model is to run radiative transfer calculations using the surface density calculated by the 1D disk evolution model and assuming either standard CO abundances or CO abundances computed with thermochemical models. This method is however computationally prohibitive and in this work, we use a simple analytical formula derived from (cite: 2023ApJ...954...41T) who show that the $R_{CO,90\%}$ size is given by the radius where the total gas column density drops below a given critical column density of hydrogen denoted as $N_{gas}(R_{CO,90\%})$. However, (cite: 2023ApJ...954...41T) does not consider the depletion of gas-phase carbon, which can be substantial in Class II disks (cite: 2013ApJ...776L..38F). Following (cite: 2023MNRAS.518L..69T), we increased the threshold column density by the carbon depletion fraction, as: $$\begin{equation}
       N_{gas}(R_{CO,90\%}) = \textcolor{black}{3.7} \times 10^{21} \delta_C^{-1} \left( M_{D} / M_{\odot}\right)^{0.34} \text{cm}^{-2}.
\label{eq:trapman_2023}
\end{equation}$$ Throughout this work we adopt $\delta_C = 0.2$, in line with the under-abundance of CO found in (cite: AGEPRO_V_gasmasses) for the Lupus and Upper Sco AGE-PRO sample. Therefore, by finding the radius where the column density reaches $N_{gas}(R_{CO,90\%})$, we determine for each simulated disk the $R_{CO,90\%}$ radius.

The disk masses in Lupus and Upper Sco are calculated by matching the N$_2$H$^+$ and CO line fluxes, and CO gas size (cite: AGEPRO_V_gasmasses). For Ophiuchus, the younger disk population, only CO isotopologue lines are used. Overall, we find a drop in disk mass from Ophiuchus to Lupus by about an order of magnitude. From Lupus to Upper Sco, the median CO size and mass do not change significantly.

### Fitting procedure

![](fit_flow_chart_v3.pdf)

Our goal is to reproduce the disk fraction and the median values of the accretion rate, disk mass, and disk size. The spreads of the parameters are therefore of less importance and we keep the 4 spreads fixed to meaningful values provided in Table [1](#table:model). As explained below (see Sec. [3](#sec:results) and Fig. [13](#fig:CDF_best_fit)), these values adequately fit the dropping rate of the disk fraction, the spread in observed disk mass, and disk sizes. The main challenge is then to constrain 4 free population parameters. These 4 free parameters are constrained by sequentially reproducing (1) the disk fraction (through the disk dispersal timescale), (2) the median accretion rate in Lupus, (3) the median CO gas size inferred in Lupus, and (4) the median gas mass estimated in Lupus. The workflow is summarized in Fig. [4](#fig:scheme_fitting) for the two scenarios. The middle-aged Lupus population is used to constrain the parameters before a detailed comparison with the old Upper Sco and the young Ophiuchus populations. The choice of the Lupus population as a reference point is justified by the systematic measurement of accretion rates for all the Lupus AGE-PRO sources, the relatively narrow range in stellar age compared with Upper Sco, and the measurement of the CO disk size, which is challenging in Ophiuchus due to the presence of envelopes (cite: AGEPRO_II_Ophiuchus).

Because disk dispersal is not controlled by the same parameters (see Sec. [2.1](#subsec:indiv-disk)), the parameter adjusted for each stage differs in the two scenarios. In the first stage (fit of the disk fraction), it is the median mass-loss rate $<\dot{M}_{PEW}>$ that is adjusted for the turbulence-driven scenario, while for the MHD disk-wind scenario it is the accretion timescale $<t_{acc,0}>$. For the second stage (fit of the median accretion rate in Lupus), the initial disk mass is adjusted in both scenarios, since accretion rates are proportional to $M_0$. The third stage (fit of the median CO gas size in Lupus) constrains the initial disk size $R_0$, and the last stage constrains the remaining parameters, namely the viscous timescale for the turbulence-driven case and the wind-to-accretion mass ratio in the MHD disk-wind case. These four stages allow us to confront the predictions of the population synthesis models to the full AGE-PRO data with very limited degeneracy in the parameters.

# Results

## MHD wind driven evolution

### Disk dispersal

In the analytical solution of (cite: 2022MNRAS.512.2290T), the theoretical disk dispersal time, as defined by the time when disk mass drops to zero, depends only on the accretion timescale $t_{acc,0}$ and the $\omega$ parameter, which quantifies the evolution of the magnetic field strength. For $\omega > 0$ and a stellar mass of $M_* = 0.5~M_{\odot}$, an individual disk disperses at a time $$\begin{equation}
   t_{disp} = 2 t_{acc,0}/ \omega = 0.68~\text{Myr} \left( \frac{\alpha_{DW}}{10^{-3}}  \right)^{-1} \left( \frac{R_0}{10~\text{au}}  \right) \omega^{-1}.
 
\end{equation}$$ In this work, our definition of disk dispersal time as the time when the stellar accretion rate drops below $10^{-12}~M_{\odot}/yr$, leads to very similar disk dispersal time for $\omega \gtrsim 0.2$. Therefore, one can associate for each individual disk, a dispersal time $t_{disp}$. Because $\alpha_{DW}$ and $R_0$ follow log-normal probability distributions, the disk dispersal time will also follow a log-normal distribution with a median value and a spread of $$\begin{equation}
\begin{split}
<t_{disp}> &= 0.68~\text{Myr} \left( \frac{<\alpha_{DW}>}{10^{-3}}  \right)^{-1} \left( \frac{<R_0>}{10~\text{au}}  \right) \omega^{-1} \\
\sigma_{t_{disp}}^2 &= \sigma_{\alpha_{DW}}^2  + \sigma_{R_0}^2,
\label{eq:tdisp_MHD-DW}
\end{split}
\end{equation}$$ where $\sigma_X$ is the spread of the quantity $X$ measured in dex.

In the first stage of the fitting process, we consider $R_0$ as a free parameter which will be constrained from the observed CO size in stage 3 (see Fig. [4](#fig:scheme_fitting)). Therefore, to fit a median disk dispersal time of 3 Myr, one needs to set the median value of $\alpha_{DW}$ for each value of $R_0$ to $$\begin{equation}
    <\alpha_{DW}> = 2.3 \times 10^{-4}  \left( \frac{<R_0>}{10~\text{au}}  \right) \omega^{-1}. 
    \label{eq:alphaDW_for-dispersal}
\end{equation}$$ Equation ([\[eq:tdisp_MHD-DW\]](#eq:tdisp_MHD-DW)) also justifies the adopted spread in $R_0$ and $\alpha_{DW}$ (see values in Table [1](#table:model)). We indeed choose the spreads such that $\sqrt{\sigma_{\alpha_{DW}}^2  + \sigma_{t_{R_0}}^2} = 0.36$, a value close to the spread in the disk lifetime inferred from the decline of the disk fraction.

### Accretion rates

![](constraint_stage2_MHD-DW_v5.pdf)

As discussed in (cite: 2022MNRAS.512L..74T), once the distribution of $t_{acc,0}$ is set, some essential properties of accretion are set since $t_{acc,0}$ also controls the ratio between the accretion rate and the disk mass. In particular, Eq. ([\[eq:MHD-DW_anal-solution\]](#eq:MHD-DW_anal-solution)) shows that the absolute value of the accretion rate scales with the initial disk mass. Therefore, in the second stage of our fitting procedure, we adjust the median disk mass $<M_0>$ for each value of $\omega$, $f_M$, and $<R_0>$ to match a median accretion rate of $\dot{M}_* = 10^{-9}$ M$_{\odot}$/yr measured in Lupus.

Practically, we start with a first guess of the initial disk mass to compute the evolution of a population and measure the median accretion rate at an age of $2\,$Myr. The initial median disk mass is subsequently increased (resp. decreased) if the median accretion is higher (resp. lower) than $10^{-9}$ M$_{\odot}$/yr. A tolerance of $10 \%$ on the median accretion rate is adopted.

The resulting values of $<M_0>$ as a function of the remaining free parameters ($<R_0>$, $\omega$, $<f_M>$) are shown in Fig. [5](#fig:stage2_MHD-DW). When plotted as a function of the ejection-to-accretion mass ratio $f_M = (R_0/R_{in})^{1/[2(\lambda-1)]}-1$, the results do not depend on the assumed initial disk sizes. This is because the time evolution of the accretion rate is primarily driven by the accretion timescale $t_{acc,0}$ and not directly the disk size.

From Eq. [\[eq:MHD-DW_anal-solution\]](#eq:MHD-DW_anal-solution), increasing the ejection-to-accretion mass ratio $f_M$ reduces all the accretion rates by a factor of $1/(1+f_M)$. Therefore, the value of $<M_0>$ required to reproduce the accretion rate in Lupus increases with $f_M$ as $1+f_M$ (see black curve in Fig. [5](#fig:stage2_MHD-DW)), and the impact of mass-loss rate is significant only for $f_M \gtrsim 1$. Finally, lower values of $\omega$ require higher disk masses to fit the accretion rates. The effect of $\omega$ is more subtle to grasp but can be understood from the inspection of Fig. [2](#fig:example_MHD-wind). For the same disk dispersal time, a lower value of $\omega$ leads to an accretion rate with a steeper drop before dispersal. This implies that lower values of $\omega$ lead to lower accretion rates at $2\,$Myr. As a consequence, the initial disk mass $<M_0>$ required to fit the observed accretion rate in Lupus needs to be increased when decreasing the $\omega$ value.

Overall, we find that initial median disk masses of at least $<M_0> \simeq 8 \times 10^{-3}~M_{\odot}$ are required to reproduce the median accretion rate measured in Lupus. The median gas mass of $<M_D> \simeq 7^{+4}_{-2} \times 10^{-3} M_{\odot}$ obtained by AGE-PRO in Ophiuchus (cite: AGEPRO_II_Ophiuchus) favors low ejection-to-accretion ratios $f_M \lesssim 1$ and relatively high values of $\omega$. Interestingly, large mass ejection ratios $f_M$ are excluded since this would require disks that are initially unstable against gravitational instability.

### Constraints from AGE-PRO results on Lupus

At this stage, we are in a position to compare the results of AGE-PRO to synthetic populations which are consistent with disk dispersal and the accretion rate in Lupus (stage 3 and 4 in Fig. [4](#fig:scheme_fitting)). The initial disk mass and accretion timescale are already constrained and only the initial disk size, the $f_M$ parameter, and $\omega$ remain free parameters. In Fig. [6](#fig:stage3_MHD-DW), we show the predicted median CO disk size and the median disk mass after 2 Myr, corresponding to the age of Lupus. As expected, a population of initially larger disks has a larger $<R_{CO}>$ size after $2\,$Myr (Fig. [6](#fig:stage3_MHD-DW) top panel).

It is immediately apparent that only initially compact disks can fit the observed CO disk sizes in Lupus with a median disk radius of $<R_0> \simeq 10~$au. We stress that this does not imply that the characteristic size at the age of Lupus is that small since compact disks have shorter accretion timescales and therefore are dispersed first (see Fig. [14](#fig:survivors)).

![](fig_MHD-DW_summary_age-pro_v5.pdf)

The median disk mass $<M_D>$ at $2$ Myr increases with the mass ejection-to-accretion ratio $f_M$. This is simply because higher $f_M$ values correspond to higher initial mass $<M_0>$; a requirement to fit the median accretion rate in Lupus (see Fig. [5](#fig:stage2_MHD-DW) and Sec. [3.1.2](#subsubsec:MHD-DW_stage2)). Interestingly, we find that lower values of $\omega$ produce lower disk masses even though the initial disk mass is larger. This is an essential effect of $\omega$: for a single disk, the mass decreases more steeply before disk dispersal for low $\omega$ values (see example Fig. [2](#fig:example_MHD-wind)). Therefore, lower value of $\omega$ result in lower disk mass at the age of Lupus.

When compared with the median disk mass estimated by AGE-PRO in Lupus (Fig. [6](#fig:stage3_MHD-DW), bottom panel), the half of the synthetic populations that fit disk dispersal, accretion rate, and disk size are excluded. Most of the predicted median disk masses lie indeed above the median disk mass of Lupus. For $\omega = 0.25$, values of $f_M$ smaller than 1 reproduce well the low disk masses measured in Lupus even though $\omega = 0.5$ and $f_M \lesssim 1$ remains a good fit considering the large uncertainty on the estimated median disk mass.

![](best_fit_MHD-DW_v5_rev.pdf)

### Best fit MHD disk-wind model

Putting all the constraints stemming from the properties of the Lupus population and disk fraction, we find best-fit models with an $\omega = 0.25-0.5$, low mass ejection-to-accretion $f_M \lesssim 1$, initially compact disks $<R_0> = 10~$au, and $\alpha_{DW} \simeq 5 \times 10^{-4} - 10^{-3}$. Reproducing the essential features of the Lupus population constitutes the first success of the MHD disk-wind models. This also considerably reduces the parameter space before comparing the time evolution of the median accretion rate, mass, and CO gas size. Here, we retained two best-fit models from stage 4, which corresponds to $\omega=0.25$ (steep decline) and $\omega=0.5$ (shallow decline).

In Fig. [7](#fig:best-fit-MHD-DW), we present the time evolution of the median disk mass $<M_D>$, accretion rate $<\dot{M}_*>$, CO gas size $<R_{CO}>$ and compare them to the available observational constraints. By construction, the two synthetic populations reproduce the Lupus population at 2 Myr. We recall that higher $\omega$ values (right panels) correspond to a shallower evolution of the medians. Of the two models, the synthetic population with a higher value of $\omega=0.5$ reproduces better the evolution from Ophiuchus to Upper Sco. Overall, the match between the observations and the best-fit model is excellent. This is particularly clear with the disk mass. AGE-PRO finds a decrease in median disk mass of about 10 from Ophiuchus to Lupus which is well reproduced by $\omega =0.5$ and overestimated by $\omega =0.25$. The importance of having estimates for a young star-forming region was also highlighted in Fig. [5](#fig:stage2_MHD-DW) where we present the initial disk mass required to fit disk fraction and accretion rate; only $\omega=0.5$ and low $f_M$ values led to initial disk masses consistent with Ophiuchus. An $\omega=0.5$ value is also consistent with the relatively constant median disk mass found from Lupus to Upper Sco (Fig. [7](#fig:best-fit-MHD-DW)).

Both models also reproduce the shallow evolution of the CO disk size with a small increase in $<R_{CO}>$ from Lupus to Upper Sco. In the models, the increase in $<R_{CO}>$ is exclusively a survivorship bias. In fact, for an individual disk, $R_{CO}$ is rather slowly decreasing as an effect of the decrease in the disk mass. However, small disks are dispersed first due to their smaller $t_{acc,0}$ , driving an increase in median disk size. The result on the median accretion rate is similar to the disk mass; an $\omega=0.5$ value does a slightly better job at reproducing the shallow evolution from Lupus to Upper Sco.

## Turbulence-driven evolution with internal photoevaporation

### Disk dispersal

In the case of turbulent disks, the dispersal time for an individual disk depends not only on the accretion timescale (often also referred to as viscous timescale), but also on the 3 other disk parameters: the wind mass-loss rate $\dot{M}_{PEW}$ , the initial disk mass $M_0$ and, to a lesser extent, the disk size $R_0$ . This means that fitting disk dispersal does not provide a constraint on only one parameter, as in the case of MHD wind-driven accretion, but a joint constraint on the four parameters. In the first stage (see workflow in Fig. [4](#fig:scheme_fitting)), we determine the median photoevaporative wind mass-loss rate $<\dot{M}_{PEW}>$ required to fit disk fraction for all possible values of the viscous timescale $<t_{\nu,0}>$ (or, equivalently $<\alpha_{SS}>$), initial disk size $<R_0>$ , and mass $<M_0>$ .

Quantitatively, we find that for $t_{disp} > t_{\nu,0}$ the dispersal time of an individual disk is roughly a power-law of the disk parameters: $$\begin{equation}
    t_{disp} \simeq 2.9~\text{Myr} \left( \frac{t_{\nu,0}}{1~\text{Myr}} \right)^{1/3} \left(\frac{M_{0}}{10^{-1}~\text{M}_{\odot}} \right)^{2/3}  \left( \frac{\dot{M}_{W}}{1 \times 10^{-8}~\text{M}_{\odot}/\text{yr}} \right)^{-2/3}.
    \label{eq:disk_dispersal_time}
\end{equation}$$ This equation is motivated by the idea that a disk disperses when its accretion rate as predicted by the pure viscous evolution drops below the wind mass-loss rate (cite: clarke2001; alexander2008). This reasoning provides the power-law indexes in Eq. ([\[eq:disk_dispersal_time\]](#eq:disk_dispersal_time)). We also note that this simple equation predicts that to first order, the dispersal time is sensitive to the viscous timescale, which is proportional to the ratio $R_0/\alpha_{SS}$ (Eq. [\[eq:def-tnu\]](#eq:def-tnu)).

![](fig_PEW_constraints_disk_fraction_example_tdisp_v4_rev.pdf)

The idea behind the fitting procedure is illustrated in Fig. [8](#fig:PEW_constraints_disk_fraction_example_tdisp): for given values of the median $<R_0>$ , $<M_0>$ , and $<t_{\nu,0}>$ , the decline of the disk fraction with the age of the population depends on the value of $<\dot{M}_{PEW}>$ . We therefore assume a fixed value of $<R_0>$ , $<M_0>$ , and $<t_{\nu,0}>$ , and run a synthetic disk population using a guessed value for $<\dot{M}_{PEW}>$ . From Eq. ([\[eq:disk_dispersal_time\]](#eq:disk_dispersal_time)), the guessed value to obtain a disk dispersal time of $t_{disp} = 3~$Myr is: $$\begin{equation}
\begin{split}
    <\dot{M}_{PEW}> \simeq 1 \times 10^{-8}~\text{M}_{\odot}/\text{yr} \left( \frac{<t_{\nu,0}>}{1~\text{Myr}} \right)^{1/2}   \left( \frac{<M_{0}>}{0.1~\text{M}_{\odot}} \right) \\
    \simeq 5.8 \times 10^{-9}~\text{M}_{\odot}/\text{yr} \left( \frac{\alpha_{SS}}{10^{-3}} \right)^{-1/2} \left( \frac{R_0}{10~\text{au}} \right)^{1/2}   \left(\frac{<M_{0}>}{0.1~\text{M}_{\odot}} \right) 
    \label{eq:disk_dispersal_M0}
\end{split}
\end{equation}$$ If the disk fraction at the age of $3\,$Myr is larger (resp. smaller) than 50$\%$, the mass-loss rate is reduced (resp. increased) in proportion, and a new population is calculated. Convergence is typically reached after 2-4 iterations with a tolerance on the disk fraction of 6$\%$.

The inferred median mass-loss rate $<\dot{M}_{PEW}>$ as a function of the assumed $<t_{\nu,0}>$ and $<M_0>$ is shown in Fig. [9](#fig:PEW_stage1)-a for $<R_0> =10~$au. The global evolution of $<\dot{M}_{PEW}>$ with $<t_{\nu,0}>$ is similar for different values of $<R_0>$ as shown in the Appendix. As expected from Eq. ([\[eq:disk_dispersal_M0\]](#eq:disk_dispersal_M0)), the inferred mass-loss rate $<\dot{M}_{PEW}>$ is larger for higher disk mass $<M_0>$ , and longer viscous timescale $<t_{\nu,0}>$ . The mass-loss rate is also relatively insensitive to the initial disk size $<R_0>$ solely but on the viscous timescale $<t_{\nu,0}>$ , which is the ratio between the initial characteristic size $R_0$ and $\alpha_{SS}$. Interestingly, the increase in the mass-loss rate $<\dot{M}_{PEW}>$ with $<t_{\nu,0}>$ is steeper above $<t_{\nu,0}> \simeq 2\,$Myr. This is because, for very low values of $\alpha_{SS}$ (i.e., long $t_{\nu,0}$), the timescale to drain the innermost regions of the disk becomes of the same order of magnitude as the dispersal timescale. Therefore, the outer disk, where the photoevaporative wind is emitted from, needs to be very quickly dispersed, explaining the steep increase in wind mass-loss rate[^2] with $t_{\nu,0}$. Even longer viscous timescales are excluded since they lead to too long dispersal time due to the long lifetime of the inner regions that are not affected by photoevaporation.

![](fig_stage1_PEW_v6_rev_v2.pdf)

![](fit_summary_PEW_v6_rev.pdf)

### Accretion rates

The constraints on the median mass-loss rate obtained from disk fraction are converted into median initial accretion rates in Fig. [9](#fig:PEW_stage1)-b for a reference initial disk size of $<R_0> = 10~$au. The initial $<\dot{M}_{*}>$ scales as $\propto t_{\nu,0}^{-1  }$ since $<\dot{M}_{*}>$ =$<M_0/2 t_{\nu,0}>$ and since the mass loss-rate does not influence the initial accretion rate. In Fig. [9](#fig:PEW_stage1)-c, we further plot the median accretion rate of each synthetic population after $2\,$Myr. Due to the decline of the accretion rate of each disk, the median accretion rate is shown to drop between $t=0$ and $2\,$Myr. The drop is more pronounced for short viscous timescales due to the faster disk evolution. We also note that photoevaporation tends to disperse the lightest disks, that have higher accretion rates, limiting the drop in the median accretion rates. Overall, this leads to the counterintuitive result that the viscous timescale has little impact on the median accretion rate at 2 Myr, except for very long viscous timescales.

Figure [9](#fig:PEW_stage1)-c illustrates our method to constrain the initial disk mass from the median accretion rate estimated in Lupus using the example of an initial disk size of $<R_0> =10~$au. The median accretion rate of the Lupus disk population is depicted by a grey area. From this figure, it is evident that for $<R_0> = 10~$au and $<t_{\nu,0}>$ $\simeq 0.2-1.5\,$Myr, an initial median disk mass of about $1 \times 10^{-2}~M_{\odot}$ is required to match the Lupus median accretion rate. For long viscous timescales, the behaviors change. For $<t_{\nu,0}>$ $= 2\,$Myr, slightly higher disk masses of $\simeq 3 \times 10^{-2}$ are required. Longer viscous timescales are excluded since they produce too low accretion rates at $2~$Myr even for gravitationally unstable disks ($<M_0> =0.1~M_{\odot}$). As mentioned above, for even longer viscous timescales, the synthetic population cannot match the disk fraction.

To find the value of the median disk mass that matches the median accretion rate for every value of $<t_{\nu,0}>$ and $<R_0>$ , we interpolate the value of $<M_0>$ and $<\dot{M}_{PEW}>$ . For that, we start with the grid of $<R_0>$ , $<t_{\nu,0}>$ , and $<M_0>$ over which the value of $<\dot{M}_{PEW}>$ has been computed in stage 1. We then find, for each value of $<t_{\nu,0}>$ and $<R_0>$ the two populations that predict accretion rates at the age of Lupus bracketing the observed rate of $10^{-9}~M_{\odot}/yr$. We finally compute the value of $<M_0>$ and $<\dot{M}_{PEW}>$ using a linear interpolation. We further check that the populations with the interpolated value of $<M_0>$ and $<\dot{M}_{PEW}>$ does predict a disk dispersal time of about $3\,$Myr and a median accretion rate of $10^{-9}~M_{\odot}/yr$ at $2\,$Myr.

The result of the method is shown in Fig. [10](#fig:fig_stage_2-3_PEW), top panels. It highlights that the two observational constraints used so far, namely disk fraction and accretion rate in Lupus, can be framed as constrained mass-loss rates $<\dot{M}_{PEW}>$ and initial disk masses $<M_0>$ as a function of the two free parameters: the viscous timescale $<t_{\nu,0}>$ and initial disk size $<R_0>$ . In Fig. [10](#fig:fig_stage_2-3_PEW), we recover the result of Fig. [9](#fig:PEW_stage1)-c that the initial median disk mass required to fit disk dispersal and accretion rate in Lupus for $<R_0> =10~$au is constant for short viscous timescale and increases at longer viscous timescales. The corresponding mass-loss rate also increases with the viscous timescale as suggested by Eq. ([\[eq:disk_dispersal_M0\]](#eq:disk_dispersal_M0)). Its value is typically above $10^{-9}~M_{\odot}/yr$ and can reach few times $10^{-8}~M_{\odot}/yr$ for long viscous timescales and compact disks. Interestingly, compared to the value predicted by the hydrodynamical model of (cite: 2021MNRAS.508.3611P), we find that only very specific values of $<t_{\nu,0}>$ and $<R_0>$ are in line with their theoretical results.

### Constraints from AGE-PRO results on Lupus

![](best_fit_viscous_v7_rev.pdf)

At this stage, we are in a position to compare the results of AGE-PRO to synthetic populations which are consistent with disk dispersal and the median accretion rate in Lupus. The leftover free parameters are $<t_{\nu,0}>$ (or, equivalently, $<\alpha_{SS}>$) and $<R_0>$ . In Fig. [10](#fig:fig_stage_2-3_PEW) bottom panels, we show the Lupus median CO size and median gas mass for all the synthetic populations that fit the disk fraction and the median accretion rate in Lupus. As expected, a population of initially larger disks or shorter viscous timescales predicts a larger $<R_{CO}>$ size after $2\,$Myr.

The median CO gas size is particularly sensitive to $<t_{\nu,0}>$ for initially compact disk populations with a drop in $<R_{CO}>$ with $<t_{\nu,0}>$ for $<R_0>$ $\le 20~$au. This is not only due to limited viscous spreading but also to the onset of disk dispersal by outside-in pathways occurring for disks that remain compact over their lifetime.

Compared with the AGE-PRO measurements of the CO gas size in Lupus, it is immediately apparent that only initially compact disks can fit the observations with a median disk radius of $<R_0> \simeq 5-20~$au (see models outlined by black circles and squares in Fig. [10](#fig:fig_stage_2-3_PEW)-c). We also find a degeneracy between initially compact disks with short viscous timescales and larger disks with longer viscous timescales. This results in a relatively well constrained $\alpha_{SS}$ parameter of $\alpha_{SS} = 2-4\times 10^{-4}$. In the next section, we adopt the three best-fit models highlighted by black points in Fig. [10](#fig:fig_stage_2-3_PEW).

The predicted median disk mass at $2\,$Myr appears to be the main tension with the observations. All the models that reproduce the median CO size consistently produce a median disk mass of about $5 \times 10^{-3}~M_{\odot}$ (see models outlined by black circles in Fig. [10](#fig:fig_stage_2-3_PEW)-d). This is a factor five to ten above the disk mass estimated in Lupus by AGE-PRO (see the grey shaded area in Fig. [10](#fig:fig_stage_2-3_PEW), bottom right). The only synthetic populations that are closer to the median Lupus disk mass have compact disks and long viscous timescales. In this extreme regime, photoevaporation removes a significant fraction of the disk mass because most of the disk mass resides where the mass loss-rate profile peaks. However, these models strongly underpredict the $<R_{CO}>$ size since the low disk masses are reproduced at the expense of a dramatic shrinking of the disk.

### Best fit viscous model with PEW

Putting together all the constraints stemming from the properties of the Lupus population and disk fraction, we find that the disks should be initially compact ($R_0 \simeq 5-20~$au) with relatively long viscous timescales of $t_{\nu,0} \simeq 0.4-3\,$Myr even though no models can simultaneously reproduce disk accretion rate, disk mass, and size in Lupus. We show three best-fit models in Fig. [11](#fig:best-fit-viscous) encompassing the parameter space of the best fit and already outlined in Fig.[10](#fig:fig_stage_2-3_PEW) (see black circles and squares). By construction, the model reproduces the median value of $<R_{CO}>$ and $<\dot{M}_*>$ at the age of Lupus ($2\,$Myr).

We recover that the essential tension between the models and the observations is the median disk mass. In both models, the median disk mass is remarkably constant even after $10\,$Myr. This is not only the result of a slow evolution of individual disks since the disk mass is rather flat even after 10 times the viscous timescale but also the result of disk dispersal which preferentially removes light disks. Such a survivorship bias on median disk mass or accretion rates can also be seen in former population models but, to our knowledge, has never been discussed (cite: 2009ApJ...704..989A). The drop in median disk mass between Ophiuchus and Lupus cannot be reproduced by the turbulence-driven model.

The median accretion rate is predicted to drop by about a factor of 5-10 within the first $2\,$Myr before experiencing a relatively shallow decline at a longer time. Compared with the evolution of the median accretion rates between Lupus and Upper Sco, the best-fit models tend to overestimate the accretion rate in Upper Sco.

In the three models, we predict an increase in the CO gas size with time but the Upper Sco AGE-PRO population is not old enough to test this increase. Therefore, the median CO disk size for Upper Sco is consistent with the models. An increase in gas size is expected from turbulence-driven models due to disk spreading (cite: 2020A&A...640A...5T; 2023MNRAS.518L..69T). However, disk dispersal also removes disks with small radii (i.e. short viscous timescales), enhancing the increase in disk size. We also refer to (cite: AGE-PRO_externalPE) for a detailed discussion of the effect of external photoevaporation in Upper Sco.

# Discussion

## Constraints on disk evolution mechanisms

| Parameter | Symbol | Best fit value |
|:--:|:--:|:--:|
|  | **MHD wind model** |  |
| **Initial disk size** | $R_0$ | 10 au |
| **Initial disk mass** | $M_0$ | $7.5 \times 10^{-3}$ $M_{\odot}$ |
| **$\alpha$ parameter** | $\alpha_{DW}$ | $4.6 \times 10^{-4}$ |
| Accretion timescale | $t_{acc,0}$ | $0.75\,$Myr |
| **$\omega$ parameter** | $\omega$ | $0.5$ |
| **Magnetic lever arm** | $\lambda$ | $> 8$ $^{(b)}$ |
| Ejection-to-accretion | $f_M$ | $<0.5$ |
|  | **Turbulent model$^{(a)}$** |  |
| **Initial disk size** | $R_0$ | 10 au |
| **Initial disk mass** | $M_0$ | $1.2 \times 10^{-2}~M_{\odot}$ |
| **$\alpha$ parameter** | $\alpha_{SS}$ | $3.4 \times 10^{-4}$ |
| Viscous timescale | $t_{\nu,0}$ | $1.0 \,$Myr |
| **Wind mass-loss rate** | $\dot{M}_{PEW}$ | $4.4 \times 10^{-9}$ M$_{\odot}$/yr  |

: Summary of the best-fit parameters for the two scenarios.

\
$^{(a)}$ No set of parameters for turbulence-driven model fits all the observational constraints. The parameters correspond to a model that fits the accretion rate but not the disk mass. There is also a degeneracy between $R_0$ and $t_{\nu,0}$ outlined in Fig. [10](#fig:fig_stage_2-3_PEW).\
$^{(b)}$ Above this value the accretion-to-ejection ratio is small and $\lambda$ has a negligible impact on the properties of the synthetic population.

### Summary of the results

Our study demonstrates that reproducing only the median values of the fundamental population parameters such as accretion rate, disk fraction, disk size, and disk mass is a discriminant test for disk evolution models. We choose to follow a step-by-step approach summarized in Fig. [4](#fig:scheme_fitting), adopting simple disk evolution models and assuming that Ophiuchus, Lupus, and Upper Scorpius are representative of the same population at different ages. The best-fit parameters obtained in the previous section are summarized in Table [2](#table:best-fit).

We find that the adopted MHD wind-driven model can reproduce very well the main properties of the three populations with the gas mass and gas size estimates provided by the AGE-PRO ALMA large program (see Fig. [7](#fig:best-fit-MHD-DW)). Notably, the best-fit accretion timescale of $t_{acc,0} \simeq 0.75~$Myr along with an initial disk size of $<R_0> = 10~$au give an initial value of $\alpha_{DW}=5 \times 10^{-4}$. Following (cite: 2022MNRAS.512.2290T), $\alpha_{DW}$ is related to the disk magnetization often parameterized by the thermal-to-magnetic pressure ratio denoted as $\beta$. Our constraints translate to $\beta_0 \simeq 10^5$, depending on the unknown $B_{\phi}/B_z$ in the disk atmosphere (cite: 2022MNRAS.512.2290T).

In contrast, following our fitting procedure, we find that turbulence-driven models with a constant $\alpha_{SS}$ and a photoevaporative mass-loss rate profile of (cite: 2021MNRAS.508.3611P) can match successively disk fraction, disk accretion rate, and disk size (Fig. [11](#fig:best-fit-viscous)). This requires relatively long viscous timescales $t_{\nu,0}=0.4-3~$Myr, compact disks of $<R_0> \simeq 5-20$ au, and low wind mass-loss rates of $<\dot{M}_{PEW}> \lesssim 10^{-8}~M_{\odot}/yr$. However, when the three previously mentioned observational constraints are matched, the median disk mass at the age of Lupus and Upper Scorpius is overestimated by a factor of 5-10.

### Origin of the discrepancy with turbulent models

![](MD-Macc_corr_v5_rev.pdf)

![](best_fit_CBF_v3.pdf)

Compared with e.g., MCMC fits, our step-by-step fitting method summarized in Fig. [4](#fig:scheme_fitting) has the advantage of being intuitive and computationally efficient at finding best-fit solutions. However, in the absence of a set of parameters that fits all the constraints, the order in which the observations are fitted matters. In the case of turbulent models, one can naively conclude that the disk mass is the *experimentum crucis*. However, the observed Lupus median disk mass can also be matched in stage 2 instead of adjusting for the observed accretion rate. By doing so, we identified the two fundamental origins of the discrepancy between the turbulence-driven scenario and the observations.

First, matching median disk mass derived by AGE-PRO in stage 2, requires low initial disk masses in the range of $1-2 \times 10^{-3}~M_{\odot}$. This is a factor 2-5 smaller than the median disk mass inferred in the young Ophiuchus sample. In other words, the turbulence-driven model fails to reproduce the significant drop in median disk mass between Ophiuchus and Lupus. This is primarily due to the slow evolution of disk mass for viscous disks: ignoring dispersal, the mass of individual disks drops by a factor of $(1+t/t_{\nu,0})^{1/2}$. Even for $t_{\nu,0} = 0.2~$Myr, this only gives a drop of a factor of 3 from Ophiuchus to Lupus. Disk dispersal worsens this trend by preferentially removing light disks and reducing the dropping rate of the median disk mass, in particular at the age of Upper Sco. In contrast, MHD wind-driven accretion can produce a quick drop in disk mass and match the decline of the median disk mass from Ophiuchus to Lupus. However, we acknowledge that the disk masses in Ophiuchus versus Lupus and Upper Sco are estimated following slightly different approaches (cite: AGEPRO_V_gasmasses) such that the dropping rate of disk mass remains a loose constraint.

The major tension between the turbulence-driven model and the observations lies in the ratio between the disk mass and the accretion rate, also called apparent disk lifetime $t_{lt}= M_D/\dot{M}_*$. Specifically, the fact that the apparent disk lifetime estimated by AGE-PRO is on average shorter than the age of the disk excludes turbulence-driven accretion with a constant $\alpha_{SS}$ profile. We show in Figure [12](#fig:MD-Macc) the AGE-PRO sources in the $M_D-\dot{M}_*$ plane, focusing on stellar ages between 1 and 3 Myr. This includes the 10 Lupus and two Upper Sco sources. Figure [12](#fig:MD-Macc) also depicts the predictions for the best-fit MHD disk-wind model and turbulence-driven models as probability density maps. Because the uncertainties on the disk mass and the variability in the accretion rates can strongly affect the correlations in the $M_D-\dot{M}_*$ plane, we take into account a lognormal error on the disk mass of $\sigma=0.7$ dex (cite: AGEPRO_V_gasmasses) and on the accretion rate of $\sigma=0.3$ dex (cite: 2014A&A...570A..82V).

We recover that the turbulence-driven model predicts a correlation between disk mass and accretion rate (cite: 2017MNRAS.468.1631R). This is reminiscent of the population synthesis models of (cite: 2017MNRAS.472.4700L) and (cite: 2017ApJ...847...31M) with the addition that our population model also includes disk dispersal by photoevaporation, which alters the simple linear relationship. In particular, the predicted correlation flattens toward low-mass disks producing a subpopulation of low-mass disks ($M_D \lesssim 10^{-4}~M_{\odot}$) with a short apparent disk lifetime of $M_D/\dot{M}_* \simeq 0.1-1~$Myr. This behavior contrasts with the results of (cite: 2020MNRAS.492.1120S) who find that photoevaporation tends to produce lower accretors in the low-mass part of the $M_D-\dot{M}_*$ plane (bottom left region in Fig. [12](#fig:MD-Macc)). This difference is due to the initial disk sizes, which are now constrained by the AGE-PRO data. In our best-fit model, the disks, which are on average compact, tend to experience an outside-in dispersal pathway outlined in Fig. [1](#fig:example_turbulence), leading to short $M_D/\dot{M}_*$ before dispersal.

Our AGE-PRO sample does not recover the correlation between the disk gas masses and the accretion rates found by (cite: 2016A&A...591L...3M) on larger samples and using dust emission. This is likely due to too low statistics and large uncertainties in the retrieved gas mass. As detailed in Sec. [3](#sec:results) and further highlighted in Fig. [13](#fig:CDF_best_fit) (top and middle panels) the turbulent model fits well the accretion rates but overpredicts the disk masses. However, we recall that the model can alternatively fit the disk masses but would then underpredict the accretion rates. The true discrepancy between the turbulent model and the observations is the short apparent disk lifetime $M_D/\dot{M}_*$ found in AGE-PRO. As seen in the $M_D-\dot{M}_*$ plane (Fig. [12](#fig:MD-Macc)) and in the cumulative distribution of $M_D/\dot{M}_*$ (Fig. [13](#fig:CDF_best_fit), bottom panel), half of the AGE-PRO sample is below 1 Myr with 2 disks below 0.1 Myr. As demonstrated in (cite: 2012MNRAS.419..925J) and (cite: 2017MNRAS.468.1631R), turbulent-driven evolution leads to $M_D/\dot{M}_*$ longer or about the disk age, regardless of the details of the turbulence-driven model. This result is fully recovered in our synthetic population in Fig. [12](#fig:MD-Macc) (right panel) and Fig. [13](#fig:CDF_best_fit) (bottom panel) with the difference that the large uncertainty in disk mass makes very short $M_D/\dot{M}_*$ a possible but unlikely outcome of retrieval. In addition, outside-in disk dispersal, discussed by (cite: 2017MNRAS.468.1631R) in the context of external photoevaporation, produces low mass disks with short $M_D/\dot{M}_*$ ratio. Still, because these disks are short-lived, they should represent a minor fraction of sources. Moreover, they cluster in the very low disk mass region. Therefore outside-in disk dispersal cannot account for the short disk lifetime found by AGE-PRO. We conclude that the tension with turbulence-driven models arises from the combination of accretion rate and disk mass with a disk mass to accretion rate ratio too short to be matched by population synthesis models.

In contrast, the MHD wind-driven model reproduces very well the distribution of disk gas mass, accretion rate, and disk lifetime (Fig. [12](#fig:MD-Macc), left panel and Fig. [13](#fig:CDF_best_fit) red curve). The simulated population exhibits a large scatter, even before taking into account the uncertainty on the derived disk mass and the variability in the accretion rate (see black points versus probability distribution in Fig. [12](#fig:MD-Macc)). Overall, the 2D probability distribution encompasses very well the AGE-PRO measurements. The short disk lifetime reproduced by the model is due to the evolutionary tracks of individual disks (cite: 2022MNRAS.512.2290T): before disk dispersal, a disk moves horizontally in the $M_D-\dot{M}_*$ plane, producing a population of low-mass disks with high accretion rates. It is this population of disks about to be dispersed that matches the disks with a very short disk lifetime. Interestingly, disks with a low mass and short lifetime are also compact. This is consistent with MHD wind dispersal process since the disk dispersal time is set by the ratio between disk size and $\alpha_{DW}$ .

## Perspectives on the observational data

### Representativeness of the AGE-PRO star-forming regions

One of the fundamental assumptions behind our analysis is that the Ophiuchus, Lupus, and Upper Sco populations are representative of the same population at different ages. Based on the analysis presented in the Oph, Lupus, and Upper Sco AGE-PRO papers (cite: AGEPRO_II_Ophiuchus; AGEPRO_III_Lupus; AGEPRO_IV_UpperSco) the AGE-PRO sample is representative of the whole population in each region, based on the comparison with the available accretion rates (not applicable to Oph) and millimeter luminosities for similar spectral types. Surveys of young star-forming regions of a similar age as Lupus (1-3 Myr) show little variation in their distribution of continuum mm luminosity and accretion rates except for CrA that show weaker mm continuum fluxes (cite: 2019A&A...626A..11C). Our knowledge of old star-forming regions similar to Upper Sco is more limited. It remains unclear whether the median accretion rate declines with cluster age, as the measurements of (cite: 2023ApJ...945..112F) used in the present work suggest, or if they remain comparable to young star-forming regions even when corrected for the stellar mass dependency (cite: 2022A&A...663A..98T). Surveys of old star-forming regions in the mm are also lacking, making Upper Sco our unique reference point with a complex star formation history (cite: 2022A&A...667A.163M; 2023A&A...678A..71R). Therefore, variations in terms of gas content between different star-forming regions remains to be probed, targeting the well-known middle-aged but also less-known old star-forming regions.

Another important caveat for the Upper Sco region is the importance of external irradiation in the disk evolution. Throughout this work, we neglected external photoevaporation which can affect disk evolution (cite: 2022MNRAS.514.2315C). Only strong external FUV of $G_0>10^3$ are expected to significantly affect the dispersal time and all the properties of the disks (cite: 2017AJ....153..240A; 2023A&A...679A..82M; garate2024), but the modest FUV strength experienced by the AGE-PRO Upper Sco sample can slightly affect the disk gas mass but largely decrease gas disk size (cite: AGE-PRO_externalPE).

### Disk gas mass

It is commonly suggested that the measurement of the disk size alone constitutes a decisive test for disk evolution models. This comes from the idea that turbulence-driven accretion requires viscous expansion and MHD wind-driven accretion does not. Our work demonstrates that disk sizes constitute an essential constraint for disk evolution models but also shows that the latter idea is somewhat misleading. First, as demonstrated in Fig. [1](#fig:example_turbulence), turbulence-driven disks can shrink over time due to internal photoevaporation. The requirement is that the disk is compact enough such that the local wind mass-loss rate is large enough out to the disk edge. Since AGE-PRO shows that the disks are on average compact ($R_{CO}\simeq 70-110~$au), internal photoevaporation is expected to affect the evolution of the disk size in the case of turbulence-driven evolution. External photoevaporation would be even more efficient (cite: AGE-PRO_externalPE). On the other hand, the survivorship bias can greatly affect disk sizes: in MHD wind-driven models, we find that CO disk size slightly increases due to the removal of compact disks. The measurement of CO size alone, even in regions of different age, is not a decisive test for disk evolution scenarios.

However, combining disk gas size, disk gas mass, and stellar accretion rate measurements brings solid constraints on disk evolution models. This is demonstrated in Fig. [10](#fig:fig_stage_2-3_PEW) which shows that turbulence-driven models can not simultaneously reproduce disk mass, accretion rate, and CO size. Overall, we find that disk mass is a crucial parameter along with accretion rates but indubitably the most uncertain. It is the relatively low median disk gas mass found in Lupus and Upper Sco that questions the turbulence-driven paradigm.

If disk masses in these regions were to be systematically underestimated by a factor of five to ten, turbulence-driven models would be compatible with the data with an apparent lifetime of $M_D/\dot{M}_* > 1~$Myr. MHD wind-driven models would also be able to fit the data with a higher ejection-to-accretion mass ratio $f_M$ and higher initial disk mass $<M_0>$. This can be seen in Fig. [6](#fig:stage3_MHD-DW): if the median disk mass at Lupus age were to be an order of magnitude higher, the best-fit ejection-to-accretion mass ratio would be about $f_M = 1-10$. Such high values of the ejection rate are in fact not irrealistic comprared with theoretical MHD wind models and numerical simulations (cite: 2019ApJ...874...90W). In this case, the initial disk mass would need to be increased (see Fig. [5](#fig:stage2_MHD-DW)).

The estimates of the disk gas mass are subject to considerable challenges (cite: 2023ASPC..534..501M). Within the AGE-PRO large programme, the DALI thermochemical model is used (cite: AGEPRO_V_gasmasses) to retrieve disk gas masses from CO and N$_2$H$^+$ but the retrieval based solely on the CO line fluxes and using (cite: 2022ApJ...925...49R) models give similar results in Lupus (cite: AGEPRO_III_Lupus). Overall, our estimates depend on our understanding of the chemistry and physics of disks and one can expect considerable progress in the future. Benchmarks between mass estimates based on N$_2$H$^+$ (cite: 2019ApJ...881..127A; 2022ApJ...926L...2T), kinematics (cite: 2024A&A...686A...9M), and HD (cite: 2017A&A...605A..69T) show relatively consistent results for large and massive disks (cite: 2023ASPC..534..501M). However, we stress that the lowest disk masses found in AGE-PRO are for very compact disks. Deep observations designed to characterize the chemistry of compact disks ($<R_{CO}> \lesssim 60~$au) should be performed. Our fitting strategy allows one to investigate how the best-fit model will be affected by a revision of the disk gas masses since the constraints from the gas masses are, on purpose, taken into account at the final stage of the fit (see Fig. [4](#fig:scheme_fitting)).

A final caveat behind disk mass estimates is that the molecular lines trace the outer disk where it is assumed that the bulk mass resides. The regions inside of $\simeq 10~$au could hide a large fraction of the mass which would remain poorly traced by ALMA due to optical depth effects. This would require a significant jump in the surface density profile. Since disks accrete, a jump in the surface density profile implies a jump in $\alpha$ values (either radial or vertical torque). In the turbulence-driven scenario, a massive inner disk with very low $\alpha$ values is expected to have a long survival timescale since photoevaporation does not operate in that region (cite: hartmann2006; Morishima2012; garate2021). One can then speculate that such a setup would lead to a population of extremely compact but accreting disks. Detailed models including radial variation in $\alpha$ values (cite: 2024MNRAS.533.1211T) are deferred to future work. In parallel, constraints on the absolute value of the column density in the inner disk can be obtained by line pressure broadening of CO (cite: 2022ApJ...937L..14Y).

## Disk dispersal and the survivorship bias

![](survivors_v2.pdf)

Because the evolution of a disk cannot be observationally monitored, the use of surveys at a population level is needed. However, in the presence of disk dispersal, the evolution of the properties of a population is not only determined by the evolution of individual disks but also by the properties of the survivors. Our population synthesis approach highlights the importance of this bias, a.k.a. *survivorship bias*, when interpreting the results of surveys. The evolution of the median disk mass in the turbulence-driven scenario is undoubtedly the most striking example: whereas the mass of individual disks declines, disk dispersal removes light disks resulting in a shallow evolution of the disk mass. This selection process, identified by (cite: 2020MNRAS.492.1120S), is evidenced by the dramatic increase in the initial mass of the surviving disks shown in Fig. [14](#fig:survivors) (see left panel). MHD wind-driven evolution also introduces a survivorship bias: compact disks evolve and disperse faster since they have shorter accretion timescales $t_{acc,0}$ . This results in an increase in the initial median disk size of the surviving disks highlighted in Fig. [14](#fig:survivors) (right panel). This effect drives the small increase in CO gas size seen in Fig. [7](#fig:best-fit-MHD-DW).

We stress that the survivorship bias is different from the selection bias induced by the definition of a sample. It is a bias that does not depend on the choice of the observer but arises because the defined population of disk loses members due to dispersal. One could instead follow the population of all the stars but in this case, the median disk mass drops to zero as soon as the disk fraction drops below $50\%$. We call it bias because it is a selection process that prevents us from probing directly the evolution of the disk properties. The implication is that the survivorship bias is a fundamental bias that is difficult to correct in the observations. This requires knowing which disk in a young population survives at a later stage. For a given disk evolution model, the effect of survivorship bias can still be qualitatively assessed since the population parameters that are the most affected are those that control disk dispersal. On the other hand, survivorship bias constitutes a promising way to constrain disk evolution mechanisms. As an example, X-ray photoevaporation is expected to disperse not only light disks but also disks around X-ray bright stars. This idea has been explored to test the relevance of X-ray photoevaporation (cite: 2005ApJS..160..401P; 2021A&A...648A.121F; 2022ApJ...935..111L) even though the interpretations of the results are complicated by the possible quenching of X-ray emission by the accretion flow.

## Spreads and correlations between disk parameters

Throughout this work, we assumed that $\alpha$, $R_0$, $M_0$, and the parameter controlling the wind mass-loss rate ($\dot{M}_{PEW}$ or $f_M$) are independent and follow lognormal distributions with fixed spreads. We recall that the spreads have been chosen to reproduce the decline of the disk fraction but no further adjustment has been made to fit the spread in the observed disk mass and accretion rates. We however note that our best-fit models reproduce well the spread in the accretion rate (Fig. [13](#fig:CDF_best_fit), middle panel), especially if we consider the effect of variability. The spread in the distribution of disk mass is also well matched (see Fig. [13](#fig:CDF_best_fit), top panel) even though the spreads are dominated by the large statistical uncertainties in the retrieved gas mass.

Interestingly, we note that the spreads in the disk parameters impact the evolution of the medians. This is again due to the survivorship bias. The clearest example is the evolution of the median CO disk size in MHD wind-driven evolution. Disks are removed according to their $t_{acc,0}$ values which is the ratio between $\alpha_{DW}$ and $R_0$. This drives the increase in $<R_{CO}>$. However, in the absence of any spread in initial disk size, $<R_{CO}>$ would remain constant in time.

The effect of the correlations between the disk parameters is an interesting avenue to explore. Due to survivorship bias, a parameter that is not related to disk dispersal can be greatly affected if it is correlated with a key parameter for dispersal. The most obvious correlation is probably between the initial disk mass and the initial disk size even though observations of Class I disks suggest a rather weak dependency between disk mass and disk size (cite: 2020ApJ...890..130T). For example, the disks could be born with similar values of the surface density and differ in mass only because they differ in size. In the case of our MHD wind-driven model, small disks are dispersed first such that a positive correlation would produce a shallower evolution in disk mass. For our turbulence-driven model, light disks are dispersed first such that a positive correlation would steepen the evolution of the CO disk size.

All in all, our best-fit models constitute a baseline for a full exploration of the effect of the spreads and the correlations between the disk parameters. Such models will add new free parameters and additional observational constraints should be taken into account to limit the degeneracies.

## Limits and perspective on 1D disk evolution models

Our work aims to test and quantify disk evolution processes by confronting existing surveys and in particular AGE-PRO to population synthesis models. Our goal is not to propose new disk evolution models but to provide reference population models based on existing 1D evolution models. These models are meant to capture the essential features of either turbulence-driven evolution or MHD wind-driven evolution. Here, we outline the simplifications of these models and discuss future disk evolution models that remain to be built.

### Turbulence-driven case

For the turbulence-driven model, one of the uncertainties is the photoevaporative wind model (cite: 2023ASPC..534..567P). The wind properties are the result of the spectral distribution of high energy photons (from $\simeq10$ eV to $\simeq1$ keV), radiative transfer, and gas thermal balance of the disk upper layers. Over the past decades, several studies have been conducted to establish mass-loss rate profiles along with absolute mass-loss rates with contradictory results (cite: 2017ApJ...847...11W; 2021ApJ...910...51K; 2021MNRAS.508.3611P). In our work, we kept the total mass-loss rate as a free parameter to avoid biases due to the use of a specific study and we adopted the mass-loss rate profile of (cite: 2021MNRAS.508.3611P) for a $0.5~M_{\odot}$ mass star. Our best-fit models have a typical mass-loss rate of $\simeq 3 \times 10^{-9} - 10^{-8}~$M$_{\odot}$/yr, which is smaller than the mass-loss rate of $\simeq 2 \times 10^{-8}~M_{\odot}/yr$ predicted by (cite: 2021MNRAS.508.3611P) for a $0.5~M_{\odot}$ stellar mass. Similar results were also found by analyzing the distribution of the accretion rates alone (cite: alexander2023). Our findings are also well in line with the recent work of (cite: 2024arXiv240800848S) who showed that the inclusion of collisions of O with neutral H, which was not included in (cite: 2021MNRAS.508.3611P), and subsequent line cooling, decreases the mass-loss rate by a factor of 5-10.

Our study demonstrates that internal photoevaporative winds control not only the disk dispersal time but also the overall evolution of the disk properties, notably the disk size as illustrated in Fig. [1](#fig:example_turbulence). In this context, the exact mass-loss rate profile matters. If the local mass-loss rate were to be significant at large distances, as in the calculations of (cite: 2009ApJ...690.1539G), disks could be initially more extended.

An important simplification of the model is the absence of attenuation of the stellar radiation by an inner MHD disk-wind. MHD disk-winds launched from the inner disks ($\lesssim 1~$au) are likely ubiquitous (cite: 2016ApJ...831..169S; 2018ApJ...868...28F; 2020ApJ...903...78P) and attenuation could reduce the heating of the outer disk where photoevaporative winds are launched. Our estimate of the median wind mass-loss rate should therefore be considered as time-averaged. Consistent models would require identifying which photon energy drives the wind and the composition of the inner MHD wind (dust content, metallicity). More detailed models including the attenuation by an evolving inner MHD disk-wind should be explored (cite: 2023A&A...674A.165W).

The assumption of constant $\alpha_{SS}$ in space and time is also an important simplification of the turbulence-driven model used in this work. The presence of a dead zone with a limited radial extent can create a steep transition in the $\alpha_{SS}$ profile (cite: delage2022). A systematic study exploring sophisticated profiles of $\alpha_{SS}$ is beyond the scope of the paper. Preliminary tests show that a population of disks with a highly turbulent outer region ($r>20~$au) and low $\alpha_{SS}$ inner disk tends to behave like a population of disks with constant $\alpha_{SS}$ values. In particular, an $\alpha_{SS}$ with step function does not seem to solve the tension with the observations but more work remains to be done in that regard.

### MHD wind-driven case

In contrast to turbulence-driven models, 1D disk evolution models including MHD disk-winds are relatively recent (cite: 2016A&A...596A..74S; 2016ApJ...821...80B; 2022MNRAS.512.2290T). Throughout this work, we adopted the simple model of (cite: 2022MNRAS.512.2290T) which has the advantage of relying on limited assumptions and being directly comparable to numerical simulations. The wind torque is parameterized by the $\alpha_{DW}$ parameter which is proportional to the mid-plane magnetization, traditionally quantified by the thermal-to-magnetic pressure ratio $\beta$.

The secular evolution of the magnetic field strength, which controls the wind torque, is notably a major uncertainty in secular evolution models. As shown by (cite: 2013ApJ...778L..14A) and (cite: 2016ApJ...821...80B), if the disk preserves its magnetic field, the disk can be quickly dispersed. This is the situation explored in this work where the $\omega$ parameter controls the time evolution of $\alpha_{DW}$ . In the framework of this model, we show that a slowly decreasing magnetic field producing an increased magnetization with $\beta \propto \sqrt{M_D}$ can naturally account for the observational data. Numerical simulation running on a secular timescale opened by GPU-accelerated codes (cite: 2023A&A...677A...9L) are warranted to interpret these constraints.

The wind mass-loss rate and the impact of the high-energy photons are also a major uncertainty in MHD wind-driven models. In this work, we use the magnetic lever arm parameter $\lambda$ to parameterize the wind mass-loss rate (see Eq. [\[eq:sigma_dot_MHD-DW\]](#eq:sigma_dot_MHD-DW)). In a realistic setup, the value of $\lambda$ is the result of the field morphology, field strength, and heating of the disk surface (cite: 2016ApJ...821...80B). The contrast between photoevaporative winds and MHD disk-winds is commonly made in the literature. We recall that MHD wind winds emerge when a magnetic field with a net flux threatens the disk but thermal effects are fundamental in the wind launching process (cite: 2000A&A...361.1178C; 2016ApJ...821...80B). The transition between photoevaporative winds and MHD disk-winds is often presented as the transition when the MHD wind mass-loss rate is about that predicted in the absence of any net magnetic flux. (cite: 2017A&A...600A..75B) found that the wind mass-loss rate decreases with disk magnetization as $\dot{M}_{MHD-DW} \propto \beta^{-1/2}$. (cite: 2020A&A...633A..21R) further confirmed this trend showing that for a given disk setup, the wind mass-loss rate reaches the threshold value of photoevaporation for $\beta \gtrsim 10^7$. Within our modeling framework, it means that $\lambda$ is predicted to decline with $\beta$ or, equivalently increase with $\alpha_{DW}$ . However, in the absence of systematic theoretical constraints on how $\lambda$ varies with disk fundamental properties, we simply assumed $\lambda$ to be constant in space and time. We also note that our best-fit MHD disk-wind model predicts disks with increasing magnetizations but decreasing mass-loss rates. In the literature, 1D evolution models have attempted to couple MHD disk-winds and photoevaporative winds by simply adding the MHD disk-wind mass-loss rate and the photoevaporative mass-loss rate (cite: 2020MNRAS.492.3849K; 2023A&A...674A.165W). A promising avenue to consistently describe the transition between photoevaporation and MHD disk-wind would be to determine how $\lambda$ varies with at least $\alpha_{DW}$ , and with the impinging radiation field using a wide grid of numerical simulations including detailed micro-physics.

# Conclusion

In this work, we developed a disk population synthesis approach to challenge existing disk evolution models in the framework of the AGE-PRO large program. The use of population synthesis is essential since the evolution of a population is not only set by the evolution of each individual disk but also by the properties of the survivors. To obtain robust constraints we used not only the results of AGE-PRO, namely the disk gas sizes and masses, but also the disk fractions and the accretion rates. Each free population parameter is constrained sequentially using the disk fractions and the properties of the middle-aged Lupus population. This allows us to considerably reduce the parameter space before confronting the two scenarios with the AGE-PRO results. Our results are the following.

- The analysis of disk surveys requires adopting a disk population synthesis approach to reproduce simultaneously all the available observational constraints. This approach is key to include the fact that the evolution of a population is not only the result of the evolution of individual disks but also of disk dispersal that selects disks with specific properties, a phenomenon that we call here *survivorship bias*.

- MHD wind-driven models mimicking the evolution of the disk magnetization can reproduce disk fraction and the overall properties of the Ophiuchus, Lupus, and Upper Sco populations. It requires initially compact ($R_0 \simeq 10~$au) disks with a moderate mass-loss rate $\dot{M}_W / \dot{M}_* \lesssim 1$, and an accretion timescale of about $t_{acc,0} \simeq 0.4-0.8\,$Myr ($\alpha_{DW,0} = 5 \times 10^{-4} - 10^{-3}$). This corresponds to disks with an initial magnetization of about $\beta \simeq 10^{5}$.

- Turbulence-driven models with internal photoevaporation can reproduce disk dispersal and gas size but fail to reproduce simultaneously the accretion rates and the disk masses. The short apparent disk lifetimes of $M_D/\dot{M}_* \simeq 0.1-1~$Myr for half of the middle-aged disks are the major tension with turbulence-driven models. Still, detailed studies of compact disks that have the lowest masses and the shortest apparent disk lifetimes should be conducted to confirm their low masses.

This work tends to favor the emerging MHD wind-driven disk accretion scenario, which has major implications for planet formation and migration. The increasing number of disk wind detections with ALMA and JWST will enable constraining some of the key input parameters of these models such as the wind mass-loss rates and the lever arm. This work provides the community with observationally constrained synthetic disk populations that are required to study dust evolution and planet formation. We, however, acknowledge that the disk evolution models cannot capture the full complexity of the disk physics. This first study warrants the development of more sophisticated disk evolution models that are timely in the era of disk surveys.

# Acknowledgment

The authors thank the referee for a rigorous and constructive report. B.T. thanks Min Fang for sharing data on Upper Sco. This work was supported by the Programme National PCMI of CNRS/INSU with INC/INP co-funded by CEA and CNES. G.R. acknowledges funding from the Fondazione Cariplo, grant no. 2022-1217, and the European Research Council (ERC) under the European Union’s Horizon Europe Research & Innovation Programme under grant agreement no. 101039651 (DiscEvol). Views and opinions expressed are however those of the author(s) only, and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them. RA acknowledges funding from the Science & Technology Facilities Council (STFC) through Consolidated Grant ST/W000857/1. L.T. and K. Z. acknowledge the support of the NSF AAG grant #2205617. P.P. and A.S. acknowledge the support from the UK Research and Innovation (UKRI) under the UK government’s Horizon Europe funding guarantee from ERC (under grant agreement No 101076489). A.S. also acknowledges support from FONDECYT de Postdoctorado 2022 $\#$3220495. I.P. and D.D. acknowledge support from Collaborative NSF Astronomy & Astrophysics Research grant (ID: 2205870). C.A.G. and L.P. acknowledge support from FONDECYT de Postdoctorado 2021 #3210520. L.P. also acknowledges support from ANID BASAL project FB210003. L.A.C and C.G.R. acknowledge support from the Millennium Nucleus on Young Exoplanets and their Moons (YEMS), ANID - Center Code NCN2021_080 and L.A.C. also acknowledges support from the FONDECYT grant #1241056. N.T.K. acknowledges support provided by the Alexander von Humboldt Foundation in the framework of the Sofja Kovalevskaja Award endowed by the Federal Ministry of Education and Research. K.S. acknowledges support from the European Research Council under the Horizon 2020 Framework Program via the ERC Advanced Grant Origins 83 24 28. GL has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie-Sklodowska Curie grant agreement No. 823823738 (DUSTBUSTERS) and from PRIN-MUR 20228JPA3A. All figures were generated with the `PYTHON`-based package `MATPLOTLIB` (cite: 2007CSE.....9...90H). This research made use of Astropy,[^3] a community-developed core Python package for Astronomy (cite: 2018AJ....156..123A).

# Facilities

ALMA

# Software

astropy (cite: 2018AJ....156..123A), *Diskpop* (cite: 2024arXiv240721101S)

# Constraints on $<\dot{M}_{PEW}>$ and $<M_0>$ for turbulence-driven populations

![](appendix_stage1_PEW_overview_rev-v2.pdf)

natexlab

(ref: AGEPRO_IV_UpperSco) Agurto-Gangas, C., Pérez, L. M., Sierra, A., et al. 2025, in press, ApJ

(ref: alcala2014) Alcalá, J. M., Natta, A., Manara, C. F., et al. 2014, A&A, 561, A2, doi: [`10.1051/0004-6361/201322254`](http://doi.org/10.1051/0004-6361/201322254)

(ref: 2017A&A...600A..20A) Alcalá, J. M., Manara, C. F., Natta, A., et al. 2017a, A&A, 600, A20, doi: [`10.1051/0004-6361/201629929`](http://doi.org/10.1051/0004-6361/201629929)

(ref: alcala2017) —. 2017b, A&A, 600, A20, doi: [`10.1051/0004-6361/201629929`](http://doi.org/10.1051/0004-6361/201629929)

(ref: alexander2008) Alexander, R. 2008, New A Rev., 52, 60, doi: [`10.1016/j.newar.2008.04.004`](http://doi.org/10.1016/j.newar.2008.04.004)

(ref: 2014prpl.conf..475A) Alexander, R., Pascucci, I., Andrews, S., Armitage, P., & Cieza, L. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 475, doi: [`10.2458/azu_uapress_9780816531240-ch021`](http://doi.org/10.2458/azu_uapress_9780816531240-ch021)

(ref: alexander2023) Alexander, R., Rosotti, G., Armitage, P. J., et al. 2023, MNRAS, 524, 3948, doi: [`10.1093/mnras/stad1983`](http://doi.org/10.1093/mnras/stad1983)

(ref: 2009ApJ...704..989A) Alexander, R. D., & Armitage, P. J. 2009, ApJ, 704, 989, doi: [`10.1088/0004-637X/704/2/989`](http://doi.org/10.1088/0004-637X/704/2/989)

(ref: 2006MNRAS.369..229A) Alexander, R. D., Clarke, C. J., & Pringle, J. E. 2006, MNRAS, 369, 229, doi: [`10.1111/j.1365-2966.2006.10294.x`](http://doi.org/10.1111/j.1365-2966.2006.10294.x)

(ref: AGE-PRO_externalPE) Anania, R. 2025, ApJ. [`https://arxiv.org/abs/xxxx.xxxx`](https://arxiv.org/abs/xxxx.xxxx)

(ref: 2019ApJ...881..127A) Anderson, D. E., Blake, G. A., Bergin, E. A., et al. 2019, ApJ, 881, 127, doi: [`10.3847/1538-4357/ab2cb5`](http://doi.org/10.3847/1538-4357/ab2cb5)

(ref: andrews2013) Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner, D. J. 2013, ApJ, 771, 129, doi: [`10.1088/0004-637X/771/2/129`](http://doi.org/10.1088/0004-637X/771/2/129)

(ref: andrews2005) Andrews, S. M., & Williams, J. P. 2005, ApJ, 631, 1134, doi: [`10.1086/432712`](http://doi.org/10.1086/432712)

(ref: 2017AJ....153..240A) Ansdell, M., Williams, J. P., Manara, C. F., et al. 2017, AJ, 153, 240, doi: [`10.3847/1538-3881/aa69c0`](http://doi.org/10.3847/1538-3881/aa69c0)

(ref: 2013ApJ...778L..14A) Armitage, P. J., Simon, J. B., & Martin, R. G. 2013, ApJL, 778, L14, doi: [`10.1088/2041-8205/778/1/L14`](http://doi.org/10.1088/2041-8205/778/1/L14)

(ref: 2018AJ....156..123A) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: 2016ApJ...821...80B) Bai, X.-N. 2016, ApJ, 821, 80, doi: [`10.3847/0004-637X/821/2/80`](http://doi.org/10.3847/0004-637X/821/2/80)

(ref: 2011ApJ...736..144B) Bai, X.-N., & Stone, J. M. 2011, ApJ, 736, 144, doi: [`10.1088/0004-637X/736/2/144`](http://doi.org/10.1088/0004-637X/736/2/144)

(ref: 2013ApJ...769...76B) —. 2013, ApJ, 769, 76, doi: [`10.1088/0004-637X/769/1/76`](http://doi.org/10.1088/0004-637X/769/1/76)

(ref: 2016ApJ...827..142B) Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A. 2016, ApJ, 827, 142, doi: [`10.3847/0004-637X/827/2/142`](http://doi.org/10.3847/0004-637X/827/2/142)

(ref: 2017A&A...600A..75B) Béthune, W., Lesur, G., & Ferreira, J. 2017, A&A, 600, A75, doi: [`10.1051/0004-6361/201630056`](http://doi.org/10.1051/0004-6361/201630056)

(ref: 1982MNRAS.199..883B) Blandford, R. D., & Payne, D. G. 1982, MNRAS, 199, 883, doi: [`10.1093/mnras/199.4.883`](http://doi.org/10.1093/mnras/199.4.883)

(ref: 2021ApJS..257...16B) Booth, A. S., Tabone, B., Ilee, J. D., et al. 2021, ApJS, 257, 16, doi: [`10.3847/1538-4365/ac1ad4`](http://doi.org/10.3847/1538-4365/ac1ad4)

(ref: 2000A&A...361.1178C) Casse, F., & Ferreira, J. 2000, A&A, 361, 1178. [`https://arxiv.org/abs/astro-ph/0008244`](https://arxiv.org/abs/astro-ph/0008244)

(ref: 2019A&A...626A..11C) Cazzoletti, P., Manara, C. F., Liu, H. B., et al. 2019, A&A, 626, A11, doi: [`10.1051/0004-6361/201935273`](http://doi.org/10.1051/0004-6361/201935273)

(ref: clarke2007) Clarke, C. J. 2007, MNRAS, 376, 1350, doi: [`10.1111/j.1365-2966.2007.11547.x`](http://doi.org/10.1111/j.1365-2966.2007.11547.x)

(ref: clarke2001) Clarke, C. J., Gendrin, A., & Sotomayor, M. 2001, MNRAS, 328, 485, doi: [`10.1046/j.1365-8711.2001.04891.x`](http://doi.org/10.1046/j.1365-8711.2001.04891.x)

(ref: 2022MNRAS.514.2315C) Coleman, G. A. L., & Haworth, T. J. 2022, MNRAS, 514, 2315, doi: [`10.1093/mnras/stac1513`](http://doi.org/10.1093/mnras/stac1513)

(ref: 2020A&A...634L..12D) de Valon, A., Dougados, C., Cabrit, S., et al. 2020, A&A, 634, L12, doi: [`10.1051/0004-6361/201936950`](http://doi.org/10.1051/0004-6361/201936950)

(ref: delage2022) Delage, T. N., Okuzumi, S., Flock, M., Pinilla, P., & Dzyurkevich, N. 2022, A&A, 658, A97, doi: [`10.1051/0004-6361/202141689`](http://doi.org/10.1051/0004-6361/202141689)

(ref: AGEPRO_III_Lupus) Deng, D., Vioque, M., Pascucci, I., et al. 2025, in press, ApJ

(ref: 2023ASPC..534..717D) Drazkowska, J., Bitsch, B., Lambrechts, M., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 717, doi: [`10.48550/arXiv.2203.09759`](http://doi.org/10.48550/arXiv.2203.09759)

(ref: 2023A&A...673A..78E) Emsenhuber, A., Burn, R., Weder, J., et al. 2023, A&A, 673, A78, doi: [`10.1051/0004-6361/202244767`](http://doi.org/10.1051/0004-6361/202244767)

(ref: 2023ApJ...945..112F) Fang, M., Pascucci, I., Edwards, S., et al. 2023, ApJ, 945, 112, doi: [`10.3847/1538-4357/acb2c9`](http://doi.org/10.3847/1538-4357/acb2c9)

(ref: 2018ApJ...868...28F) —. 2018, ApJ, 868, 28, doi: [`10.3847/1538-4357/aae780`](http://doi.org/10.3847/1538-4357/aae780)

(ref: 2013ApJ...776L..38F) Favre, C., Cleeves, L. I., Bergin, E. A., Qi, C., & Blake, G. A. 2013, ApJL, 776, L38, doi: [`10.1088/2041-8205/776/2/L38`](http://doi.org/10.1088/2041-8205/776/2/L38)

(ref: 2010A&A...510A..72F) Fedele, D., van den Ancker, M. E., Henning, T., Jayawardhana, R., & Oliveira, J. M. 2010, A&A, 510, A72, doi: [`10.1051/0004-6361/200912810`](http://doi.org/10.1051/0004-6361/200912810)

(ref: 2019ApJ...874...81F) Fernandes, R. B., Mulders, G. D., Pascucci, I., Mordasini, C., & Emsenhuber, A. 2019, ApJ, 874, 81, doi: [`10.3847/1538-4357/ab0300`](http://doi.org/10.3847/1538-4357/ab0300)

(ref: 1997A&A...319..340F) Ferreira, J. 1997, A&A, 319, 340. [`https://arxiv.org/abs/astro-ph/9607057`](https://arxiv.org/abs/astro-ph/9607057)

(ref: 2006A&A...453..785F) Ferreira, J., Dougados, C., & Cabrit, S. 2006, A&A, 453, 785, doi: [`10.1051/0004-6361:20054231`](http://doi.org/10.1051/0004-6361:20054231)

(ref: 2021A&A...648A.121F) Flaischlen, S., Preibisch, T., Manara, C. F., & Ercolano, B. 2021, A&A, 648, A121, doi: [`10.1051/0004-6361/202039746`](http://doi.org/10.1051/0004-6361/202039746)

(ref: 1996ApJ...457..355G) Gammie, C. F. 1996, ApJ, 457, 355, doi: [`10.1086/176735`](http://doi.org/10.1086/176735)

(ref: garate2024) Gárate, M., Pinilla, P., Haworth, T. J., & Facchini, S. 2024, A&A, 681, A84, doi: [`10.1051/0004-6361/202347850`](http://doi.org/10.1051/0004-6361/202347850)

(ref: garate2021) Gárate, M., Delage, T. N., Stadler, J., et al. 2021, A&A, 655, A18, doi: [`10.1051/0004-6361/202141444`](http://doi.org/10.1051/0004-6361/202141444)

(ref: 2009ApJ...690.1539G) Gorti, U., & Hollenbach, D. 2009, ApJ, 690, 1539, doi: [`10.1088/0004-637X/690/2/1539`](http://doi.org/10.1088/0004-637X/690/2/1539)

(ref: hartmann2006) Hartmann, L., D’Alessio, P., Calvet, N., & Muzerolle, J. 2006, ApJ, 648, 484, doi: [`10.1086/505788`](http://doi.org/10.1086/505788)

(ref: 2016ARA&A..54..135H) Hartmann, L., Herczeg, G., & Calvet, N. 2016, ARA&A, 54, 135, doi: [`10.1146/annurev-astro-081915-023347`](http://doi.org/10.1146/annurev-astro-081915-023347)

(ref: 1994ApJ...428..654H) Hollenbach, D., Johnstone, D., Lizano, S., & Shu, F. 1994, ApJ, 428, 654, doi: [`10.1086/174276`](http://doi.org/10.1086/174276)

(ref: 2007CSE.....9...90H) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90, doi: [`10.1109/MCSE.2007.55`](http://doi.org/10.1109/MCSE.2007.55)

(ref: 2012MNRAS.419..925J) Jones, M. G., Pringle, J. E., & Alexander, R. D. 2012, MNRAS, 419, 925, doi: [`10.1111/j.1365-2966.2011.19730.x`](http://doi.org/10.1111/j.1365-2966.2011.19730.x)

(ref: 2020A&A...633A...4K) Kimmig, C. N., Dullemond, C. P., & Kley, W. 2020, A&A, 633, A4, doi: [`10.1051/0004-6361/201936412`](http://doi.org/10.1051/0004-6361/201936412)

(ref: 2021ApJ...910...51K) Komaki, A., Nakatani, R., & Yoshida, N. 2021, ApJ, 910, 51, doi: [`10.3847/1538-4357/abe2af`](http://doi.org/10.3847/1538-4357/abe2af)

(ref: 2016ARA&A..54..271K) Kratter, K., & Lodato, G. 2016, ARA&A, 54, 271, doi: [`10.1146/annurev-astro-081915-023307`](http://doi.org/10.1146/annurev-astro-081915-023307)

(ref: kraus2012) Kraus, A. L., Ireland, M. J., Hillenbrand, L. A., & Martinache, F. 2012, ApJ, 745, 19, doi: [`10.1088/0004-637X/745/1/19`](http://doi.org/10.1088/0004-637X/745/1/19)

(ref: 2020MNRAS.492.3849K) Kunitomo, M., Suzuki, T. K., & Inutsuka, S.-i. 2020, MNRAS, 492, 3849, doi: [`10.1093/mnras/staa087`](http://doi.org/10.1093/mnras/staa087)

(ref: 2022ApJ...935..111L) Laos, S., Wisniewski, J. P., Kuchner, M. J., et al. 2022, ApJ, 935, 111, doi: [`10.3847/1538-4357/ac8156`](http://doi.org/10.3847/1538-4357/ac8156)

(ref: 2022A&A...658A..32L) Lega, E., Morbidelli, A., Nelson, R. P., et al. 2022, A&A, 658, A32, doi: [`10.1051/0004-6361/202141675`](http://doi.org/10.1051/0004-6361/202141675)

(ref: 2023ASPC..534..465L) Lesur, G., Flock, M., Ercolano, B., et al. 2023a, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 465, doi: [`10.48550/arXiv.2203.09821`](http://doi.org/10.48550/arXiv.2203.09821)

(ref: 2023A&A...677A...9L) Lesur, G. R. J., Baghdadi, S., Wafflard-Fernandez, G., et al. 2023b, A&A, 677, A9, doi: [`10.1051/0004-6361/202346005`](http://doi.org/10.1051/0004-6361/202346005)

(ref: 2017MNRAS.472.4700L) Lodato, G., Scardoni, C. E., Manara, C. F., & Testi, L. 2017, MNRAS, 472, 4700, doi: [`10.1093/mnras/stx2273`](http://doi.org/10.1093/mnras/stx2273)

(ref: 2018A&A...618A.120L) Louvet, F., Dougados, C., Cabrit, S., et al. 2018, A&A, 618, A120, doi: [`10.1051/0004-6361/201731733`](http://doi.org/10.1051/0004-6361/201731733)

(ref: 1974MNRAS.168..603L) Lynden-Bell, D., & Pringle, J. E. 1974, MNRAS, 168, 603, doi: [`10.1093/mnras/168.3.603`](http://doi.org/10.1093/mnras/168.3.603)

(ref: 2023ASPC..534..539M) Manara, C. F., Ansdell, M., Rosotti, G. P., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 539, doi: [`10.48550/arXiv.2203.09930`](http://doi.org/10.48550/arXiv.2203.09930)

(ref: 2016A&A...591L...3M) Manara, C. F., Rosotti, G., Testi, L., et al. 2016, A&A, 591, L3, doi: [`10.1051/0004-6361/201628549`](http://doi.org/10.1051/0004-6361/201628549)

(ref: 2017A&A...604A.127M) Manara, C. F., Testi, L., Herczeg, G. J., et al. 2017, A&A, 604, A127, doi: [`10.1051/0004-6361/201630147`](http://doi.org/10.1051/0004-6361/201630147)

(ref: 2019A&A...628A..95M) Manara, C. F., Tazzari, M., Long, F., et al. 2019, A&A, 628, A95, doi: [`10.1051/0004-6361/201935964`](http://doi.org/10.1051/0004-6361/201935964)

(ref: 2020A&A...639A..58M) Manara, C. F., Natta, A., Rosotti, G. P., et al. 2020, A&A, 639, A58, doi: [`10.1051/0004-6361/202037949`](http://doi.org/10.1051/0004-6361/202037949)

(ref: 2022A&A...667A..17M) Martel, É., & Lesur, G. 2022, A&A, 667, A17, doi: [`10.1051/0004-6361/202142946`](http://doi.org/10.1051/0004-6361/202142946)

(ref: 2024A&A...686A...9M) Martire, P., Longarini, C., Lodato, G., et al. 2024, A&A, 686, A9, doi: [`10.1051/0004-6361/202348546`](http://doi.org/10.1051/0004-6361/202348546)

(ref: 2023A&A...679A..82M) Maucó, K., Manara, C. F., Ansdell, M., et al. 2023, A&A, 679, A82, doi: [`10.1051/0004-6361/202347627`](http://doi.org/10.1051/0004-6361/202347627)

(ref: 2023ASPC..534..501M) Miotello, A., Kamp, I., Birnstiel, T., Cleeves, L. C., & Kataoka, A. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 501, doi: [`10.48550/arXiv.2203.09818`](http://doi.org/10.48550/arXiv.2203.09818)

(ref: 2022A&A...667A.163M) Miret-Roig, N., Galli, P. A. B., Olivares, J., et al. 2022, A&A, 667, A163, doi: [`10.1051/0004-6361/202244709`](http://doi.org/10.1051/0004-6361/202244709)

(ref: 2016JGRE..121.1962M) Morbidelli, A., & Raymond, S. N. 2016, Journal of Geophysical Research (Planets), 121, 1962, doi: [`10.1002/2016JE005088`](http://doi.org/10.1002/2016JE005088)

(ref: Morishima2012) Morishima, R. 2012, MNRAS, 420, 2851, doi: [`10.1111/j.1365-2966.2011.19940.x`](http://doi.org/10.1111/j.1365-2966.2011.19940.x)

(ref: 2017ApJ...847...31M) Mulders, G. D., Pascucci, I., Manara, C. F., et al. 2017, ApJ, 847, 31, doi: [`10.3847/1538-4357/aa8906`](http://doi.org/10.3847/1538-4357/aa8906)

(ref: 2018ApJ...857...57N) Nakatani, R., Hosokawa, T., Yoshida, N., Nomura, H., & Kuiper, R. 2018, ApJ, 857, 57, doi: [`10.3847/1538-4357/aab70b`](http://doi.org/10.3847/1538-4357/aab70b)

(ref: 2024A&A...686A.201N) Nazari, P., Tabone, B., Ahmadi, A., et al. 2024, A&A, 686, A201, doi: [`10.1051/0004-6361/202348676`](http://doi.org/10.1051/0004-6361/202348676)

(ref: 2018A&A...615A..63O) Ogihara, M., Kokubo, E., Suzuki, T. K., & Morbidelli, A. 2018, A&A, 615, A63, doi: [`10.1051/0004-6361/201832720`](http://doi.org/10.1051/0004-6361/201832720)

(ref: 2015A&A...584L...1O) Ogihara, M., Morbidelli, A., & Guillot, T. 2015, A&A, 584, L1, doi: [`10.1051/0004-6361/201527117`](http://doi.org/10.1051/0004-6361/201527117)

(ref: 2012MNRAS.422.1880O) Owen, J. E., Clarke, C. J., & Ercolano, B. 2012, MNRAS, 422, 1880, doi: [`10.1111/j.1365-2966.2011.20337.x`](http://doi.org/10.1111/j.1365-2966.2011.20337.x)

(ref: 2010MNRAS.401.1415O) Owen, J. E., Ercolano, B., Clarke, C. J., & Alexander, R. D. 2010, MNRAS, 401, 1415, doi: [`10.1111/j.1365-2966.2009.15771.x`](http://doi.org/10.1111/j.1365-2966.2009.15771.x)

(ref: 2023ASPC..534..567P) Pascucci, I., Cabrit, S., Edwards, S., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Protostars and Planets VII, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 567, doi: [`10.48550/arXiv.2203.10068`](http://doi.org/10.48550/arXiv.2203.10068)

(ref: 2020ApJ...903...78P) Pascucci, I., Banzatti, A., Gorti, U., et al. 2020, ApJ, 903, 78, doi: [`10.3847/1538-4357/abba3c`](http://doi.org/10.3847/1538-4357/abba3c)

(ref: 2025NatAs...9...81P) Pascucci, I., Beck, T. L., Cabrit, S., et al. 2025, Nature Astronomy, 9, 81, doi: [`10.1038/s41550-024-02385-7`](http://doi.org/10.1038/s41550-024-02385-7)

(ref: 2021MNRAS.508.3611P) Picogna, G., Ercolano, B., & Espaillat, C. C. 2021, MNRAS, 508, 3611, doi: [`10.1093/mnras/stab2883`](http://doi.org/10.1093/mnras/stab2883)

(ref: 2005ApJS..160..401P) Preibisch, T., Kim, Y.-C., Favata, F., et al. 2005, ApJS, 160, 401, doi: [`10.1086/432891`](http://doi.org/10.1086/432891)

(ref: 2023A&A...678A..71R) Ratzenböck, S., Großschedl, J. E., Alves, J., et al. 2023, A&A, 678, A71, doi: [`10.1051/0004-6361/202346901`](http://doi.org/10.1051/0004-6361/202346901)

(ref: 2015A&A...576A..52R) Ribas, Á., Bouy, H., & Merı́n, B. 2015, A&A, 576, A52, doi: [`10.1051/0004-6361/201424846`](http://doi.org/10.1051/0004-6361/201424846)

(ref: 2014A&A...561A..54R) Ribas, Á., Merı́n, B., Bouy, H., & Maud, L. T. 2014, A&A, 561, A54, doi: [`10.1051/0004-6361/201322597`](http://doi.org/10.1051/0004-6361/201322597)

(ref: ricci2010) Ricci, L., Testi, L., Natta, A., et al. 2010, A&A, 512, A15, doi: [`10.1051/0004-6361/200913403`](http://doi.org/10.1051/0004-6361/200913403)

(ref: 2020A&A...639A..95R) Riols, A., Lesur, G., & Menard, F. 2020, A&A, 639, A95, doi: [`10.1051/0004-6361/201937418`](http://doi.org/10.1051/0004-6361/201937418)

(ref: 2020A&A...633A..21R) Rodenkirch, P. J., Klahr, H., Fendt, C., & Dullemond, C. P. 2020, A&A, 633, A21, doi: [`10.1051/0004-6361/201834945`](http://doi.org/10.1051/0004-6361/201834945)

(ref: 2017MNRAS.468.1631R) Rosotti, G. P., Clarke, C. J., Manara, C. F., & Facchini, S. 2017, MNRAS, 468, 1631, doi: [`10.1093/mnras/stx595`](http://doi.org/10.1093/mnras/stx595)

(ref: 2022ApJ...925...49R) Ruaud, M., Gorti, U., & Hollenbach, D. J. 2022, ApJ, 925, 49, doi: [`10.3847/1538-4357/ac3826`](http://doi.org/10.3847/1538-4357/ac3826)

(ref: AGEPRO_II_Ophiuchus) Ruiz-Rodriguez, D. A., González-Ruilova, C., Cieza, L. A., et al. 2025, in press, ApJ

(ref: 2020MNRAS.498.2845S) Sellek, A. D., Booth, R. A., & Clarke, C. J. 2020, MNRAS, 498, 2845, doi: [`10.1093/mnras/staa2519`](http://doi.org/10.1093/mnras/staa2519)

(ref: 2024arXiv240800848S) Sellek, A. D., Grassi, T., Picogna, G., et al. 2024, arXiv e-prints, arXiv:2408.00848, doi: [`10.48550/arXiv.2408.00848`](http://doi.org/10.48550/arXiv.2408.00848)

(ref: 1973A&A....24..337S) Shakura, N. I., & Sunyaev, R. A. 1973, A&A, 500, 33

(ref: 2016ApJ...831..169S) Simon, M. N., Pascucci, I., Edwards, S., et al. 2016, ApJ, 831, 169, doi: [`10.3847/0004-637X/831/2/169`](http://doi.org/10.3847/0004-637X/831/2/169)

(ref: 2020MNRAS.492.1120S) Somigliana, A., Toci, C., Lodato, G., Rosotti, G., & Manara, C. F. 2020, MNRAS, 492, 1120, doi: [`10.1093/mnras/stz3481`](http://doi.org/10.1093/mnras/stz3481)

(ref: 2024arXiv240721101S) Somigliana, A., Testi, L., Rosotti, G., et al. 2024, arXiv e-prints, arXiv:2407.21101, doi: [`10.48550/arXiv.2407.21101`](http://doi.org/10.48550/arXiv.2407.21101)

(ref: 2018MNRAS.477.1239S) Suriano, S. S., Li, Z.-Y., Krasnopolsky, R., & Shang, H. 2018, MNRAS, 477, 1239, doi: [`10.1093/mnras/sty717`](http://doi.org/10.1093/mnras/sty717)

(ref: 2016A&A...596A..74S) Suzuki, T. K., Ogihara, M., Morbidelli, A., Crida, A., & Guillot, T. 2016, A&A, 596, A74, doi: [`10.1051/0004-6361/201628955`](http://doi.org/10.1051/0004-6361/201628955)

(ref: 2022MNRAS.512.2290T) Tabone, B., Rosotti, G. P., Cridland, A. J., Armitage, P. J., & Lodato, G. 2022a, MNRAS, 512, 2290, doi: [`10.1093/mnras/stab3442`](http://doi.org/10.1093/mnras/stab3442)

(ref: 2022MNRAS.512L..74T) Tabone, B., Rosotti, G. P., Lodato, G., et al. 2022b, MNRAS, 512, L74, doi: [`10.1093/mnrasl/slab124`](http://doi.org/10.1093/mnrasl/slab124)

(ref: 2017A&A...607L...6T) Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6, doi: [`10.1051/0004-6361/201731691`](http://doi.org/10.1051/0004-6361/201731691)

(ref: 2020A&A...640A..82T) Tabone, B., Cabrit, S., Pineau des Forêts, G., et al. 2020, A&A, 640, A82, doi: [`10.1051/0004-6361/201834377`](http://doi.org/10.1051/0004-6361/201834377)

(ref: 2014prpl.conf..339T) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339–361, doi: [`10.2458/azu_uapress_9780816531240-ch015`](http://doi.org/10.2458/azu_uapress_9780816531240-ch015)

(ref: 2022A&A...663A..98T) Testi, L., Natta, A., Manara, C. F., et al. 2022, A&A, 663, A98, doi: [`10.1051/0004-6361/202141380`](http://doi.org/10.1051/0004-6361/202141380)

(ref: 2020ApJ...890..130T) Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130, doi: [`10.3847/1538-4357/ab6f64`](http://doi.org/10.3847/1538-4357/ab6f64)

(ref: 2023MNRAS.518L..69T) Toci, C., Lodato, G., Livio, F. G., Rosotti, G., & Trapman, L. 2023, MNRAS, 518, L69, doi: [`10.1093/mnrasl/slac137`](http://doi.org/10.1093/mnrasl/slac137)

(ref: 2021MNRAS.507..818T) Toci, C., Rosotti, G., Lodato, G., Testi, L., & Trapman, L. 2021, MNRAS, 507, 818, doi: [`10.1093/mnras/stab2112`](http://doi.org/10.1093/mnras/stab2112)

(ref: 2024MNRAS.533.1211T) Tong, S., Alexander, R., & Rosotti, G. 2024, MNRAS, 533, 1211, doi: [`10.1093/mnras/stae1748`](http://doi.org/10.1093/mnras/stae1748)

(ref: 2017A&A...605A..69T) Trapman, L., Miotello, A., Kama, M., van Dishoeck, E. F., & Bruderer, S. 2017, A&A, 605, A69, doi: [`10.1051/0004-6361/201630308`](http://doi.org/10.1051/0004-6361/201630308)

(ref: 2020A&A...640A...5T) Trapman, L., Rosotti, G., Bosman, A. D., Hogerheijde, M. R., & van Dishoeck, E. F. 2020, A&A, 640, A5, doi: [`10.1051/0004-6361/202037673`](http://doi.org/10.1051/0004-6361/202037673)

(ref: 2023ApJ...954...41T) Trapman, L., Rosotti, G., Zhang, K., & Tabone, B. 2023, ApJ, 954, 41, doi: [`10.3847/1538-4357/ace7d1`](http://doi.org/10.3847/1538-4357/ace7d1)

(ref: 2022ApJ...926L...2T) Trapman, L., Zhang, K., van’t Hoff, M. L. R., Hogerheijde, M. R., & Bergin, E. A. 2022, ApJL, 926, L2, doi: [`10.3847/2041-8213/ac4f47`](http://doi.org/10.3847/2041-8213/ac4f47)

(ref: AGEPRO_V_gasmasses) Trapman, L., Zhang, K., Rosotti, G., et al. in press, 2025a, ApJ

(ref: AGEPRO_XI_gas_disk_sizes) Trapman, L., Vioque, M., Kurtovic, N., et al. in press, 2025b, ApJ

(ref: 2022A&A...661A..53V) van Terwisga, S. E., Hacar, A., van Dishoeck, E. F., Oonk, R., & Portegies Zwart, S. 2022, A&A, 661, A53, doi: [`10.1051/0004-6361/202141913`](http://doi.org/10.1051/0004-6361/202141913)

(ref: 2014A&A...570A..82V) Venuti, L., Bouvier, J., Flaccomio, E., et al. 2014, A&A, 570, A82, doi: [`10.1051/0004-6361/201423776`](http://doi.org/10.1051/0004-6361/201423776)

(ref: 2023A&A...677A..70W) Wafflard-Fernandez, G., & Lesur, G. 2023, A&A, 677, A70, doi: [`10.1051/0004-6361/202245305`](http://doi.org/10.1051/0004-6361/202245305)

(ref: 2019ApJ...874...90W) Wang, L., Bai, X.-N., & Goodman, J. 2019, ApJ, 874, 90, doi: [`10.3847/1538-4357/ab06fd`](http://doi.org/10.3847/1538-4357/ab06fd)

(ref: 2017ApJ...847...11W) Wang, L., & Goodman, J. 2017, ApJ, 847, 11, doi: [`10.3847/1538-4357/aa8726`](http://doi.org/10.3847/1538-4357/aa8726)

(ref: 2023A&A...674A.165W) Weder, J., Mordasini, C., & Emsenhuber, A. 2023, A&A, 674, A165, doi: [`10.1051/0004-6361/202243453`](http://doi.org/10.1051/0004-6361/202243453)

(ref: 2022EPJP..137.1132W) Winter, A. J., & Haworth, T. J. 2022, European Physical Journal Plus, 137, 1132, doi: [`10.1140/epjp/s13360-022-03314-1`](http://doi.org/10.1140/epjp/s13360-022-03314-1)

(ref: 2024Icar..41716085Y) Yap, T. E., & Batygin, K. 2024, Icarus, 417, 116085, doi: [`10.1016/j.icarus.2024.116085`](http://doi.org/10.1016/j.icarus.2024.116085)

(ref: 2022ApJ...937L..14Y) Yoshida, T. C., Nomura, H., Tsukagoshi, T., Furuya, K., & Ueda, T. 2022, ApJL, 937, L14, doi: [`10.3847/2041-8213/ac903a`](http://doi.org/10.3847/2041-8213/ac903a)

(ref: 2022MNRAS.514.1088Z) Zagaria, F., Rosotti, G. P., Clarke, C. J., & Tabone, B. 2022, MNRAS, 514, 1088, doi: [`10.1093/mnras/stac1461`](http://doi.org/10.1093/mnras/stac1461)

(ref: AGE-PRO_I-overview) Zhang, K. 2025, ApJ. [`https://arxiv.org/abs/xxxx.xxxx`](https://arxiv.org/abs/xxxx.xxxx)

(ref: AGEPRO_I_overview) Zhang, K., Pérez, L., Pascucci, I., et al. 2025, in press, ApJ

[^1]: On April 2024, from <https://exoplanets.nasa.gov/>.

[^2]: We recall here that the parameter $\dot{M}_{PEW}$ is an effective mass-loss rate used to scale the $\dot{\Sigma}_{PEW}$ profile. When a disk is compact, which is the case for long $t_{\nu,0}$ and small $R_0$, the true mass-loss rate is smaller.

[^3]: http://www.astropy.org

</paper>

Write the methods card for this paper.