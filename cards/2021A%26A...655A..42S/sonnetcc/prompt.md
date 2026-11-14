# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...655A..42S\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...655A..42S",
 "title": "Molecular gas budget and characterization of intermediate-mass star-forming galaxies at z ≈ 2-3",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Solimano, M.",
 "n_authors": 12,
 "arxiv_id": "2107.09769",
 "doi": "10.1051/0004-6361/202141835",
 "alma_projects_linked_by_archive": [
  "2018.1.01142.S"
 ]
}
```

Paper text:
<paper>
# Molecular gas budget and characterization of intermediate-mass star-forming galaxies at $z\approx 2-3$

# Introduction

New stars are born from giant, cold molecular gas clouds in dusty environments within the interstellar medium (ISM) of star-forming galaxies (cite: Bolatto2008ExtragalacticGMCs; KennicuttAndEvans2012ReviewSFLocalUniverse), although the detailed physical mechanisms by which galaxies acquire gas and then convert it into stars are still poorly understood (cite: McKeeAndOstriker2007TheoryOfSF). However, theoretical and observational efforts in the past decades have contributed to linking the evolution of galactic-scale parameters of star formation (e.g., star formation rate, SFR; stellar mass, M~stars~; gas depletion timescale, $t_\text{dep}=\text{M}_\text{mol}/\text{SFR}$; etc.) with the abundance and physical conditions of the cold ISM from the Local Universe up to redshift $z\sim4$ (cite: Hodge&daCunha2020Review; Tacconi2020EvolutionISMReview; ForsterShreiberAndWuyts2020CosmicNoonSFReview).

The advent of large samples of massive SFGs with targeted dust continuum and/or CO line observations (the two most common molecular gas tracers at high redshift) revealed a number of key trends: a tight correlation between the gas fraction (M~mol~/M~stars~) and the specific star formation rate (sSFR$\equiv \text{SFR}/\text{M}_\text{stars}$), a decrease in $t_\text{dep}$ with redshift, and an increase in the gas fraction with redshift (cite: Scoville2017EvolutionISM; Tacconi2018PHIBSS2MainSequence). These results imply that galaxies with higher levels of star formation also have larger molecular gas reservoirs, and that these reservoirs were on average larger in the first gigayears of the universe. The current explanation is that the ability of a galaxy to form stars is regulated by a feedback loop between the cosmological accretion of gas and the return of that gas to the ambient via galactic outflows, a picture that is often refered to as the "equilibrium model" (cite: Dave2012EquilibriumModelAnalytical; Lilly2013GasRegulation; Walter2020EvolutionOfBaryons). Furthermore, deep blind (cite: Decarli2019ASPECS-CO-LF; Decarli2020ASPECSMultiBandLineLuminosityAndGasDensity) and archival (cite: Liu2019A3COSMOScoldGasEvolution) surveys conducted with the Atacama Large Millimeter/Submillimeter Array (ALMA) confirm that the cosmic molecular gas density follows roughly the same evolution as the cosmic star formation density, that is with a global maximum occurring around $z\approx 2$ (cite: Madau&Dickinson2014Review). However, at $z\gtrsim1$ this picture is necessarily incomplete, since the current statistical samples are limited to the highest-mass systems ($\SI{e10}{M\ensuremath{_\odot}} \leq M_\text{stars} \leq \SI{e11.5}{M\ensuremath{_\odot}}$) despite lower mass galaxies being more numerous. Unfortunately, directly probing the gas budget of the $<\SI{e10}{M\ensuremath{_\odot}}$ galaxies at $z\sim 2$ is still a major observational challenge, even with the exquisite sensitivity of ALMA, and has so far been achieved only through stacking techniques (cite: Inami20202StacksAspecsCO). Low-mass galaxies tend to have a low oxygen abundance (hereafter metallicity) as expected from the mass-metallicity relation (cite: Tremonti2004MassMetallicityRelation). This makes the detection of dust and CO even more difficult, since dust is less abundant in low-metallicity environments, favoring the photodissociation of CO molecules (cite: Leroy2011COtoH2; Genzel2012MetallicityCOtoH2; Bolatto2013COtoH2).

A popular alternative for exploring the low-mass regime at high-redshift is to take advantage of strong gravitational lensing. This phenomenon occurs when a distant galaxy is closely aligned along the line of sight with a foreground massive galaxy or cluster of galaxies. The space-time deflection induced by the intervening mass – the lens – produces distorted, magnified, and in some cases, multiple images of the background galaxy projected in the sky, often forming rings or giant arcs. The lensed images appear brighter than they would in the absence of this effect, providing a boost in intrinsic flux limit, that is, at a given instrumental sensitivity, lensing enables the detection of intrinsically fainter sources. Since the lensing effect is stronger toward massive galaxy clusters, the brightest giant arcs are typically found near their cores. Thus, targeting cluster-lensed galaxies became a common strategy for pushing molecular gas studies to fainter and higher redshift galaxies, which provides reliable results if a good model of the lens deflection is available (cite: Smail1997SubmmSurveyOfLensingClusters; Baker2004MolGasInCB58; Danielson2011StarformingGalaxyAtRedshift2; Saintonge2013MolGasLensedGalaxies; Sharon2013MappingCOinLensedSMG; DessaugesZavadsky2015MolGasLensedSFGs; Spingola2020SHARP6ExtendedCOLensed).

Although giant arcs are rare, directed searches in wide field optical imaging surveys have successfully identified several dozens to this date (cite: Hennawi2008SGAS1; Kubo2010SGAS; Stark2013CassowaryLensedSample; Khullar2021COOLLAMPSBrightestLensedGalaxy). This number is expected to grow substantially with upcoming surveys such as the Rubin Observatory Legacy Survey of Space and Time (cite: Ivezic2019LSST), the Euclid mission (cite: Laureijs2011EuclidDefinition), or the Roman Space Telescope (cite: Spergel2015RomanReport). For example, Euclid is expected to detect $\sim 2\,000$ giant arcs in galaxy clusters with a contrast of at least $3\sigma$ above the background (cite: Boldrin2012PredictedGiantArcsNumber). The detection of lensed systems in broadband rest-frame UV imaging ensures that the sources are not heavily dust-obscured and can be selected as SFGs by their photometric colors. In contrast to the massive and dust-rich submillimeter-selected galaxies (SMGs), sources selected by their colors represent the bulk of the SFG population at $z=2$, which has moderate dust and gas content.

The study of cold gas in UV-selected lensed SFGs dates back to the pre-ALMA era. (cite: Saintonge2013MolGasLensedGalaxies) obtained far infrared photometry (using the *Herschel* Space Telescope) and CO line measurements for 17 lensed galaxies selected from the literature as optically-bright giant gravitational arcs. These galaxies lie in the star-forming main sequence (MS) with stellar masses in the  × 10^9.7^ M $_\odot$– × 10^10.8^ M $_\odot$ range. Their analysis revealed lower depletion timescales and similar gas fractions than $z \sim 1$ MS galaxies, suggesting a flattening in the trend of increasing gas fraction with redshift. They also provide evidence for redshift evolution of the gas-to-dust ratio, a quantity that is commonly assumed to be constant. (cite: DessaugesZavadsky2015MolGasLensedSFGs) found similar results by combining five additional lensed galaxies with larger samples of SFGs at $z > 1$. The inclusion of galaxies with even lower stellar masses (down to  × 10^9.4^ M $_\odot$), clearly showed the effect of “downsizing” in the gas fraction versus redshift relation: the increase in the gas fraction with redshift is more pronounced for low M~stars~ systems.

Both studies are based on unresolved observations of the cold ISM. With ALMA, it is now possible to exploit the enhanced resolving power delivered by gravitational lensing to characterize the molecular gas and dust at sub-kiloparsec scales (cite: ALMAPartnership2015LensedSMGz3). This has allowed to gain unprecedented insight about the kinematics, sizes, distribution and CO excitation of individual star-forming clumps. Recent work has revealed that the high redshift ISM has more compact dusty cores, increased turbulence, higher densities relative to local SFGs, together with deviations from the Schmidt-Kennicutt law (cite: Messias2014HATLAS-J1429Merger; Swinbank2015ResolvedALMADiskAtz3; Canameras2017DustyGemsResolved60pc; Apostolovski2019ImagingMolGasSPTatz5.7; Rybak2020FullOfOrions; Rizzo2020ColdDiskSPT). However, the majority of the high-resolution studies still focus on the most massive dusty systems and not on the more common low mass, low metallicity galaxies. The reason for this is that strong lensing multiplies intrinsic area by a factor $\mu$, but surface brightness remains constant. While this effectively boosts flux by the same factor $\mu$, resolving the emission requires significant integration time regardless of lensing. Interferometric follow-up campaigns on UV-selected, intermediate- to low-mass lensed SFGs have faced mixed success: on one side, some studies detect dust continuum and CO line emission at high significance, enabling an state-of-the-art analysis of the properties of the cold ISM and their connection to star formation within very small physical scales ((cite: DessaugesZavadsky2017MolGasLensedCaseStudy; Gonzalez-Lopez2017LensedMolGasInRCS0327); in the case of the "Cosmic Snake", down to $\sim \SI{30}{\parsec}$ at $z=1$, (cite: Dessauges-Zavadsky2019CosmicSnake)). On the other side, some studies can only provide upper limits on gas and dust mass, due to the nondetection of the lensed galaxy (cite: Livermore2012NonDetectionGasRedshift5; Rybak2021UltrafaintLensedCII)

Even with the help of lensing, measuring the cold ISM in high-$z$ dwarf galaxies is challenging because the high magnifications do not guarantee detection. For this reason, we have launched a low-resolution exploratory campaign to detect mid-J CO line emission and dust continuum in the optically brightest giant arcs known, to systematically expand the number of lensed low-mass SFGs with measured cold ISM properties.

In this paper we present the first results from this program, where we conducted low resolution interferometric observations of four extremely magnified systems at $z \sim 2.5$ with the Atacama Compact Array (ACA). The detections are used to locate the intrinsic properties of the galaxies within the scaling relations found in previous works and also as a starting point for future follow-up campaigns with extended ALMA configurations.

The paper is organized as follows. In Sect. [2](#sec:obs) we describe the sources selected for this study , the observing setup, and the ancillary dataset. In Sect. [3](#sec:results) we explain our methods and present our main results. Finally, the interpretation and discussion of the results is given in Sect. [4](#sec:discussion).

We adopt a flat $\Lambda$CDM cosmology with $h=0.7$, $\Omega_m = 0.3$ and $\Omega_\Lambda = 0.7$. All position angles are quoted east of north and all magnitudes are given in the AB system. Star formation rates and stellar masses are derived assuming a (cite: Chabrier2003IMF) initial mass function (IMF). Also, relative velocities follow the radio convention (i.e., linear approximation in frequency, rather than wavelength).

# Observations

## Sample selection and prior identification

We targeted four giant gravitational arcs selected for their extreme brightness in optical bands ($m_{V} < 21$). The first one, nicknamed the Sunburst Arc, was discovered in an optical follow-up of the Planck Sunyaev-Zeldovich cluster candidate (hereafter PSZ1G311) and identified as a SFG at $z=2.37$ (cite: Dahle2016SunburstArcDiscovery). Since discovery, it holds the title of the brightest lensed image of a galaxy known to this date, and has been confirmed to be leaking significant amounts of ionizing photons (cite: Rivera-Thorsen2017SunburstArcLymanEscape; Rivera-Thorsen2019SunburstArcEscapeFractions). The galaxy is lensed into multiple images, grouped in four distinct arc segments. Hereafter, we refer to each segment S1, S2, S3 as in the discovery paper (see Fig. [1](#fig:rb7_continua)). The second and third targets are the two components of (hereafter SGASJ1226) at $z=2.92$, which were discovered in the Sloan Digital Sky Survey (cite: Blanton2017SloanIV) imaging data as a part of the Sloan Giant Arc Survey (cite: Hennawi2008SGAS1) using the Lyman Break technique (cite: Koester2010ArcJ1226Discovery). The brightest arc is the two-fold almost symmetric pair of images (cite: Dai2020AsymmetricBrightnessJ1226Arc) we refer to as SGASJ1226-A.1 (see Fig. [1](#fig:rb7_continua)). An additional but less magnified image of the same galaxy (SGASJ1226-A.2) appears roughly 15″ to the east. We call the source galaxy producing these images SGASJ1226-A. The southern, optically fainter arc is the second component of SGASJ1226, identified as companion galaxy at the same redshift (cite: Koester2010ArcJ1226Discovery), hereafter labeled SGASJ1226-B.1 (SGASJ1226-B in the source plane). Since A and B lie within 15″ in the image plane, a single ACA pointing of the lensing cluster core was needed to cover both targets. The fourth target, (hereafter SGASJ0033) at $z=2.39$, was also discovered in SDSS data and it was first reported in (cite: Rigby2018MegaSauraI). The source galaxy SGASJ0033-A is lensed into four different images: the first two are blended in a 5″-long bright arc we call SGASJ0033-A.1. The remaining less magnified images are SGASJ0033-A.2 and SGASJ0033-A.3 (see Fig. [1](#fig:rb7_continua)).

Both SGASJ0033-A and SGASJ1226-A are part of the Magellan Evolution of Galaxies Spectroscopic and Ultraviolet Reference Atlas (cite: Rigby2018MegaSauraI), a catalog of moderate resolution rest-frame ultraviolet spectra of 15 gravitationally lensed galaxies at $z\sim 2$ taken with the MagE instrument on the *Magellan* telescopes. The Sunburst Arc has comparable MagE data as part of the Extended MegaSaura Survey (Rigby et al. in prep.). The MegaSaura spectra provide secure spectroscopic redshifts as well as robust estimates on the age and metallicities of the young stellar populations (cite: Chisholm2019MegaSauraMetallicity). Unfortunately, a MagE spectrum for SGASJ1226-B is not available. In what follows, we adopt the stellar metallicity of SGASJ1226-B to be the same of SGASJ1226-A.

Promisingly, the *James Webb* Space Telescope (JWST) will target two of the sources presented here, namely SGASJ1226-A (ERS 1355, PIs: Rigby & Vieira) and the Sunburst Arc (GO 2555, PI: Rivera-Thorsen). The characterization we give here of the cold ISM in these galaxies will provide crucial insight to interpret the upcoming data.

+:------------:+:-----------------------:+:--------------:+:-------------------------------------:+:------------:+:------------:+:--------:+:--------:+:-:+
| Target       | Coordinates (ICRS)      | $z^\text{ref}$ | Discovery paper                       | B4 RMS$^{a}$ | B7 RMS$^{b}$ | Resolution$^{c}$    |   |
|              +-------------------------+                |                                       +--------------+--------------+----------+----------+---+
|              | RA, Dec                 |                |                                       |   km s^−1^   |              | B4       | B7       |   |
+--------------+-------------------------+----------------+---------------------------------------+--------------+--------------+----------+----------+---+
| Sunburst Arc | 15:49:59.7, -78:11:13.6 | 2.371^1^       | (cite: Dahle2016SunburstArcDiscovery) | 16.8         | 245          | 11.1″    | 4.9″     |   |
+--------------+-------------------------+----------------+---------------------------------------+--------------+--------------+----------+----------+---+
| SGASJ1226    | 12:26:51.3, +21:52:19.8 | 2.923^2^       | (cite: Koester2010ArcJ1226Discovery)  | 26.4         | 170          | 9.4″     | 4.3″     |   |
+--------------+-------------------------+----------------+---------------------------------------+--------------+--------------+----------+----------+---+
| SGASJ0033    | 00:33:41.6, +02:42:17.4 | 2.388^2^       | (cite: Rigby2018MegaSauraI)           | 16.8         | 170          | 9.5″     | 3.6″     |   |
+--------------+-------------------------+----------------+---------------------------------------+--------------+--------------+----------+----------+---+

Table notes: Coordinates indicate the phase center of the ACA pointing.

## Atacama Compact Array data

Our data includes observations with ACA obtained under ALMA program 2018.1.01142.S (PI: González-López). ACA – also known as the Morita Array – is a fixed configuration of twelve 7-meter antennas with a maximum baseline of 48.9 meters located at the Llano of Chajnantor (cite: Iguchi2009AtacamaCompactArray). Our sources are lensed arcs that extend over several arcseconds on the sky, and ACA offers an optimal combination of an angular resolution that is high enough to deblend the sources while remaining sensible to large scale emission.

For all targets we set up observations to detect mid-$J$ emission lines in ALMA Band 4 ($\nu\sim\SI{140}{\giga\hertz}$) and continuum dust emission in ALMA Band 7 ($\nu\sim\SI{350}{\giga\hertz}$). Mid-$J$ transitions have been reported to be one of the brightest for most of star-forming galaxies (cite: Carilli&Walter2013Review; Daddi2015COexciation; Boogaard2020ASPECS-COExcitation) while also providing information about the molecular gas budget. Band 7 observations, on the other hand, are regularly used to trace dust-obscured star formation and also molecular gas mass (cite: Schinnerer2016GasFractionAndDepletion; Scoville2017EvolutionISM; Miettinen2017AlmaCosmosSED; Darvish2018GasScalingRelations; Casey2019Mambo9; Magnelli2020ASPECSDustAndGasDensity). In addition, Band 7 photometry for sources at $z\sim 2.5$ puts important constraints on their overall far-infrared (FIR) luminosity.

All ACA data were calibrated and reduced using the Common Astronomy Software Application[^1] (cite: McMullin2007CASA) version 5.4.0-70 following the standard pipeline scripts. We assumed a flux calibration accuracy of 10% throughout. All subsequent imaging was done with CASA task `tclean` and using natural weights to maximize signal-to-noise ratio. The resulting cubes and images are sampled at pixel size equal to 1/5 of beam minor axis, and the astrometry is expected to be accurate to 0.6″.

### The Sunburst Arc

We used a standard continuum setup for observing the Sunburst Arc with Band 7 receivers. This comprises a total of four spectral windows with 31.250 MHz wide channels. Two adjacent spectral windows cover from 335.504 GHz–339.426 GHz and the other two from 347.504 GHz–351.483 GHz.

From the observed visibilities, we performed dirty imaging in multifrequency synthesis mode. The process yielded a synthesized beam of $\ang{;;5.1}\times\ang{;;4.8}$ with position angle (PA) of 5.6°. The resulting continuum intensity map achieved a root-mean-square (RMS) sensitivity of $1\sigma \simeq \SI{245}{\micro\jansky}$ over a total bandwidth of 7.5 GHz and 145 minutes on source. We found no peaks higher than $3\sigma$ within the primary beam (43″ in diameter), accounting for a nondetection of the arc in this experiment (see Fig. [1](#fig:rb7_continua))

The spectral configuration for Band 4 included two main spectral windows. The first one was tuned to the frequency of the $\ensuremath{\element[][12]{CO}\left(4\to 3\right)}$ transition at $z=2.37$, covering from 134.472 GHz–137.469 GHz at a channel resolution of 3.904 MHz (equivalent to 8.5 km s^−1^ at the CO central frequency). The other one targeted the $\ensuremath{\left[C i\right]_{1 \to 0}}$ atomic line by covering from 145.553 GHz–147.526 GHz at the same resolution (8 km s^−1^). The setup also included two adjacent sidebands to constrain the underlying continuum emission.

We then synthesized data-cubes keeping the native channel resolution (3.9 MHz). We reached a sensitivity of $1\sigma\simeq\SI{2.1}{\milli\jansky\per\beam}$ per channel and a median synthesized beam of $\ang{;;11.74} \times \ang{;;11.15}$ (PA=-17°) for the $\ensuremath{\element[][12]{CO}\left(4\to 3\right)}$ spectral window and $\ang{;;10.85}\times\ang{;;10.35}$ (PA=-17°) for the $\ensuremath{\left[C i\right]_{1 \to 0}}$ spectral window. We found that the cube contains no evident emission line signatures, that is, none of the targeted lines were detected in this experiment. However, we found a tentative ($\lesssim 3\sigma$) detection of a continuum source over the S1 arc segment (see Fig. [1](#fig:rb7_continua)) after averaging all the channels, including the sidebands. We then repeated the imaging process excluding channels within 250 km s^−1^ to each side of the expected central frequency for the $\ensuremath{\element[][12]{CO}\left(4\to 3\right)}$ and $\ensuremath{\left[C i\right]_{1 \to 0}}$ lines. To clean out the dirty beam we manually placed a 10″ mask over the peak and cleaned down to the $1\sigma$ level. The final image has a beam of $\ang{;;11.5} \times \ang{;;10.7}$ (PA=-15.9°) and residual RMS of 80.4   ^−1^ achieved with 226 minutes of on-source integration time.

### SGASJ1226

For the SGASJ1226 system we used the same spectral setup used for Band 7 continuum detection in the Sunburst Arc, with the same coverage in frequency and spectral resolution. The synthesis of the dirty image revealed two sources with signal-to-noise ratio greater than five: A $5.5\sigma$ peak that is cospatial with SGASJ1226-B.1 (southward of the BCG, Fig. [1](#fig:rb7_continua)), and a $6.2\sigma$ peak which we associate with a known Mg ii absorber galaxy at $z=0.77$ (cite: Mortensen2021ScoopArctomoJ1226; Tejos2021ArctomoJ1226Kinematic). We cleaned the images by placing clean masks on top of the two detected sources and iterating down to $2\sigma$ level. The cleaned image allowed to resolve both sources unambiguously with a synthesized beam size of $\ang{;;4.9}\times\ang{;;3.8}$ (PA=-57°) and RMS of $1\sigma \simeq \SI{170}{\micro\jansky\per\beam}$ obtained with 202 minutes of on-source integration time (see Fig. [1](#fig:rb7_continua)).

Due to the higher redshift of the SGASJ1226 source ($z=2.92$), we used Band 4 receivers to observe only the $\ensuremath{\element[][12]{CO}\left(5\to 4\right)}$ transition, as no other strong lines are expected at this redshift. Thus the setup covers with 3.9 MHz resolution ($\sim\SI{8}{\kilo\meter\per\second}$) from 145.034 GHz–146.905 GHz and from 146.894 GHz–148.765 GHz, with an effective overlap of three channels. The corresponding sidebands cover from 132.906 GHz–134.890 GHz and 134.905 GHz–136.890 GHz at a channel width of 31.25 MHz. We constructed the dirty cube using `tclean` in cube mode and using natural weighting of the visibilities. We get a median beam of $\ang{;;9.9} \times \ang{;;9.0}$ (PA=-70°) and a sensitivity of $1\sigma \simeq \SI{3.3}{\milli\jansky\per\beam}$ per channel using a total of 145.3 minutes of on-source integration time. However the result showed no significant emission anywhere in the cube, nor in the channel-averaged image.

### SGASJ0033

For SGASJ003341 we used again the standard Band 7 continuum setup configuration. The dirty image showed three bright sources within the primary beam (see Fig. [1](#fig:rb7_continua)). The first two are spatially coincident with the optical arc and a strong Mg ii absorber at $z=1.17$ (hereafter labeled SGASJ0033-G1, Ledoux et al., in prep.), respectively. The third one is a previously unreported, very bright ($\gtrsim \SI{5}{\milli\jansky}$) source with no evident optical counterpart. For this reason we refer to it as SGASJ0033-SMG (sub-millimeter galaxy). A tentative counterpart on that position is seen only in the near infrared WFC3/F140W image of the *Hubble* Space Telescope (HST; as shown in the inset of the third panel of Fig. [1](#fig:rb7_continua)), and not in the bluer filters. The lack of an optical detection further supports the idea that the object is a high-redshift dusty SFG. Then we cleaned the image to the 2$\sigma$ level taking advantage of the automatic masking feature of `tclean`. With a total of 203 minutes of on-source integration time, the resulting image reached a continuum RMS of 0.17   ^−1^, with a beam size of $\ang{;;4.5} \times \ang{;;2.9}$ (PA=-89.7°).

Band 4 spectral configuration is similar to the one used for PSZ1G311. We targeted the $\ensuremath{\element[][12]{CO}\left(4\to 3\right)}$ line (expected to lie at 136 GHz at $z=\num{2.39}$) on the first spectral window and the $\ensuremath{\left[C i\right]_{1 \to 0}}$ line (145.180 GHz at $z=\num{2.39}$) on the second. The channel bandwidth of these spectral windows was 3.906 MHz or 8.6 km s^−1^ at 136 GHz. After flagging the channels were we expect the CO and \[C i\] lines to be, we performed first order continuum subtraction in the $uv$-plane using the CASA task `uvcontsub`, since this source is also a bright continuum emitter. We then carried out the imaging process with `tclean` using natural weighting and manually defined clean region boxes. With 202 minutes of on-source integration time, we achieve a sensitivity of $1\sigma \simeq \SI{2.1}{\milli\jansky\per\beam}$ per channel and a median synthesized beam size of $\ang{;;13.1}\times\ang{;;6.9}$ at a PA of -77.6°. Preliminary analysis revealed a $10\sigma$ detection of the CO line and a $4\sigma$ detection of \[C i\], both cospatial with the optical arc. We also report the detection of a broad ($\sim \SI{400}{\kilo\meter\per\second}$) emission line at $\nu=\SI{135.6}{\giga\hertz}$, roughly cospatial with SGASJ0033-SMG (see lower panels of Fig. [2](#fig:coline0033)).

+----------------:+:-------------------------------:+:-------------------------------:+
| Source          | $S_\nu(\SI{870}{\micro\meter})$ | $S_\nu(\SI{2.1}{\milli\meter})$ |
+-----------------+---------------------------------+---------------------------------+
|                 |                                 |                                 |
+-----------------+---------------------------------+---------------------------------+
| SGASJ1226-A.1   | $<\num{0.51}$                   | $<\num{0.28}$                   |
+-----------------+---------------------------------+---------------------------------+
| SGASJ1226-A.2   | $<\num{1.0}$                    | $<\num{0.56}$                   |
+-----------------+---------------------------------+---------------------------------+
| SGASJ1226-B.1   | 1.12 ± 0.30                     | $<\num{0.28}$                   |
+-----------------+---------------------------------+---------------------------------+
| SGASJ0033-A.1   | 4.0 ± 0.4                       | \-                              |
+-----------------+---------------------------------+---------------------------------+
| SGASJ0033-A.2   | 0.9 ± 0.3                       | \-                              |
+-----------------+---------------------------------+---------------------------------+
| A.1+A.2$^{a}$   | 4.9 ± 0.5                       | 0.37 ± 0.10                     |
+-----------------+---------------------------------+---------------------------------+
| Sunburst Arc-S2 | $<\num{0.83}$                   | $<\num{0.24}$                   |
+-----------------+---------------------------------+---------------------------------+
| *Nontarget detections*                                                              |
+-----------------+---------------------------------+---------------------------------+
| SGASJ1226-G1    | 1.20 ± 0.33                     | $<\num{0.28}$                   |
+-----------------+---------------------------------+---------------------------------+
| SGASJ0033-G1    | 5.0 ± 0.9                       | $<\num{0.35}$                   |
+-----------------+---------------------------------+---------------------------------+
| SGASJ0033-SMG   | 5.1 ± 1.1                       | $<\num{0.35}$                   |
+-----------------+---------------------------------+---------------------------------+

: ACA continuum photometry in bands 7 and 4.

Table notes: Labels for the targeted sources in the first column are defined in Sec. [2.1](#sec:selection), whereas the names for the nontarget sources are introduced in subsections [2.2.2](#sec:j1226_aca_description) and [2.2.3](#sec:j0033_aca_description). All quantities are quoted in the image plane, i.e., not corrected for lensing magnification. Upper limits correspond to three times the RMS divided by the primary beam attenuation factor at the source position.

## Ancillary data

### HST data

The three lensing clusters have been observed with the HST at multiple wide band filters. We retrieved the available data from the Mikulski Archive for Space Telescopes[^2] (MAST) to perform photometric extraction of each source in order to constrain their spectral energy distribution (SED). The PSZ1G311 field was observed in bands F606W and F160W with the Wide Field Camera 3 (WFC3; GO15377, PI: Bayliss), and the F814W filter with the Advanced Camera for Surveys (ACS; GO15101, PI: Dahle). For SGASJ1226, bands F110W and F160W of the near infrared channel of WFC3 were available (GO15378, PI: Bayliss), as well as bands F606W and F814W with the ACS (GO12368, PI: Morris). Finally, data for SGASJ0033 comprises bands F555W, F814W, F105W and F140W taken with the WFC3 (GO14170, PI: Wuyts). All imaging data were aligned with DRIZZLEPAC routine `tweakreg`, and drizzled to a common pixel size of 0.03″ with `astrodrizzle` using Gaussian kernels with drop size of 0.8. We performed additional cosmic ray removal in Sunburst Arc’s F606W drizzled frame using ASTROSCRAPPY (cite: McCully2018AstroScrappy). As a last step, we check the absolute astrometric accuracy of our WCS solution by comparing the centroid positon of foreground stars in the drizzled images with the Gaia DR2 catalog (cite: GaiaCollaboration2018Release2). We find no systematic offset nor rotation, and the observed shift is at most 0.1″.

Since the lensed arcs are very extended in the sky and show complex morphologies, standard extraction routines are not well suited for obtaining reliable photometry of the sources. Instead, we employed ad-hoc polygonal apertures defined in the filter with the largest PSF for each target. We note that the background in SGASJ1226 and SGASJ0033 is dominated by the light from the brightest cluster galaxy (BCG) or other bright members of the foreground cluster. For this reason, we modeled the two elliptical isophotes of the BCG that encompass the arc extent, to isolate an area with similar contamination and background level as the source. Then we randomly placed two thousand 10 pixel wide apertures between these two isophotes and we take the resulting flux mean and variance as the background level and noise variance respectively for the science aperture, after properly scaling for the aperture area. For the Sunburst Arc, we used rectangular apertures enclosing each of the main arc segments. We estimated the background in nearby sky regions to each side of the arc.

### *Spitzer*

Observing programs #70154 (PI: Gladders) and #13111 (PI: Dahle) of the *Spitzer* Space Telescope include observations of SGASJ1226 and the Sunburst Arc respectively, at 3.6 μm and 4.5 μm wavelengths using the Infrared Array Camera (IRAC). At $z\sim3$ these bands trace the older stellar populations of the source galaxies and hence are very important for constraining their total stellar mass. We retrieve the IRAC mosaics from the NASA/IPAC Infrared Science Archive reduced with the stock calibration pipeline.

Photometry for SGASJ1226-A.1 was obtained following the method outlined in (cite: Saintonge2013MolGasLensedGalaxies): using curve of growth arguments, we determine the optimal sized circular aperture and background annulus for computing the flux of SGASJ1226-A.1. The measured flux is 54 ± 11   and 47 ± 9   at 3.6 μm and 4.5 μm respectively. These values agree with the ones reported by (cite: Saintonge2013MolGasLensedGalaxies), 52.8 ± 6.0   and 47.2 ± 4.2  . The extraction of the southern arc, SGASJ1226-B, required a segment of an annulus instead of a circular aperture due to its larger extension. The annulus was centered on the core of the BCG and the complementary segment was used for background subtraction. The resulting image plane fluxes are 46 ± 13   at 3.6 μm and 44 ± 8   at 4.5 μm.

Unfortunately, the Sunburst Arc field suffers from severe crowding, and the arc appears blended with foreground galaxies and stars at the IRAC resolution. Thus, aperture photometry was not an option in this case. To avoid the introduction of additional uncertainties and assumptions, we did not attempt a prior-based PSF-fitting approach, but completely exclude these two bands from the analysis.

The effect on the determination of stellar mass when the IRAC bands are not included in the SED fitting was explored in (cite: Mitchell2013StellarMassSystematics) by analyzing mock galaxy SEDs with known physical parameters. In that study, the exclusion of IRAC bands resulted in a bias in M~stars~ of $-0.04$ and $-0.03$ dex at $z=2$ and $z=3$, respectively, after removing the contribution from dust and metallicity effects. The scatter in the recovered M~stars~ is, however, on the order of 0.1 dex. Although these values were obtained in the idealized situation where the SED fitting code matches the IMF and stellar population model used for generating the SED, we can interpret them as an indication that our M~stars~ estimate for SGASJ0033-A and the Sunburst Arc has larger uncertainties but not a significant bias. As a complementary test, we ran MAGPHYS on SGASJ1226-A and SGASJ1226-B again but turning off the fitting for the IRAC bands. The median value of the marginal posterior probability distribution for M~stars~ was $+0.02$ and $-0.11$ dex for SGASJ1226-A and SGASJ1226-B, respectively, relative to the fiducial values listed in Table [\[tab:sed_results\]](#tab:sed_results). In both cases, the offset is much smaller than the uncertainty returned by the code. This again indicates that the lack of IRAC bands only affects the uncertainty but not the nominal value.

### Lens models and source plane reconstruction

Lens models for the three clusters were developed with the parametric LENSTOOL (cite: Jullo&Kneib2009LensTool) software based on identification of multiple images of the same lensed features in the HST imaging data, following the same methodology detailed in (cite: Sharon2020ClusterLensModelsSGAS). The models consist of a collection of parametric dark matter halo profiles centered on the cluster galaxies and assuming all members lie on the same plane (thin lens approximation). Once a set of parameters that minimize the spatial offset between predicted and observed image pairs is obtained, the best fit model provides the deflection matrices and magnification maps that are used to reconstruct the source plane properties of the lensed galaxies. The models for the three lensing clusters in this work were already published in the literature and all of them were fit with at least 10 lensing constraints, including features in the giant arcs as well as other multiply-imaged sources at different redshifts. We refer the reader to the following references for details on each model: the lens model for the PSZ1G311 cluster is published in (cite: Rivera-Thorsen2019SunburstArcEscapeFractions); for the SGASJ1226 cluster, in (cite: Dai2020AsymmetricBrightnessJ1226Arc) and (cite: Tejos2021ArctomoJ1226Kinematic); and for SGASJ0033, in (cite: Fischer2019outflowJ0033).

Throughout this paper, we report average magnifications computed as the area ratio between the image plane and the source plane within a given aperture defined in the image plane. Whenever the aperture includes multiple images, the magnification factor $\mu$ accounts for this to match the source plane area of the image with the largest footprint. For example, the arc SGASJ1226-A.1 is divided into two images by the lensing critical line. Each half maps to the same (partial) region of the source galaxy. SGASJ1226-A.2, on the other hand, is a less magnified version of the whole source galaxy, as it has a larger footprint in the source plane. Then, we set the magnification factor so that the joint image plane area of both halves of SGASJ1226-A.1 divided by $\mu$ yielded the source plane area of SGASJ1226-A.2. We adopted an uncertainty on magnification of 20% for all images to account for the statistical error in cluster lens modeling. We note, however, that the uncertainties are possibly dominated by systematics (cite: Raney2020FrontierFieldsLensingUncertainties).

An advantage of observing this kind of systems with millimeter and submillimeter interferometers is that the model to be used is developed from independent data. Models created with deep optical images can be used to interpret the observed emission, avoiding the use of the same data to characterize the models. This approach has proven to be the only reliable method for dealing with cluster-scale strong lensing (cite: Saintonge2013MolGasLensedGalaxies; Gonzalez-Lopez2017LensedMolGasInRCS0327; Laporte2017ALMA-FFphotometry1.1mm; Sharon2019MolGasLensedJ0901; Dessauges-Zavadsky2019CosmicSnake). However, it is important to acknowledge that several studies of galaxy-scale systems – which have a single or very few lensing halos – have successfully used the interferometric data alone to fit lens models, provided such data reaches high angular resolution (cite: Hezaveh2013ALMA-SPT; Bussmann2013SMALensedz1.5; Messias2014HATLAS-J1429Merger; Rybak2015SDP.81Continuum; Rybak2015SDP.81EmissionLine; Spilker2016ALMALensModelsForSPT; Apostolovski2019ImagingMolGasSPTatz5.7; Rizzo2020ColdDiskSPT)

# Data analysis & results

## Emission lines in the SGASJ0033 system

![](continuum_contours_vertical_layout_v4.pdf)

To search for lower S/N emission lines within the ACA cubes, we conducted two experiments: first, we selected and integrated along the velocity axis the channels where lines are expected according to redshift priors from literature (cite: Koester2010ArcJ1226Discovery; Tejos2021ArctomoJ1226Kinematic) using a fixed width of 200 km s^−1^. We retrieved the frequencies of the expected lines at each redshift prior using the web-based SPLATALOGUE[^3] tool. This experiment resulted in no detections above $3\sigma$, other than the lines that were already identified (see Sect. [2.2](#sec:aca_data)). For the second experiment we proceed with a blind search of emission lines, via the automated LINESEEKER software (cite: Gonzalez-Lopez2017ALMA-FFat1.1mm; Gonzalez-Lopez2019ASPECS-COLineScanAnd3mm). Again, we found no detections within the SGASJ1226 and the Sunburst Arc Band 4 cubes. The software correctly identified two of the three lines in SGASJ0033 already detected by visual inspection: the bright $\ensuremath{\element[][12]{CO}\left(4\to 3\right)}$ line associated with the arc (SGASJ0033-A) and the dimmer but broader emission feature at 135.6 GHz toward the south east (SMG). LINESEEKER did not detect the \[C i\] line, however we consider it a reliable signal based on the strong priors on the frequency, position an width imposed by the $\ensuremath{\element[][12]{CO}\left(4\to 3\right)}$ line. To confirm the detection, we extracted the \[C i\] spectrum from the same spatial region as the CO line and convolve it with the best fit Gaussian profile of CO, resulting in a peak correlation $\sim\SI{25}{\kilo\meter\per\second}$ redward of CO’s central velocity (see Fig. [3](#fig:ciline0033)).

![](coline_sgasj0033_v5.pdf)

To extract line width and central velocity, we fit one dimensional Gaussian profiles to the CO spectra of SGASJ0033-A and SGASJ0033-SMG using non linear least squares minimization. Motivated by the marginal asymmetry of the line (see upper right panel of Fig. [2](#fig:coline0033)) and the recent discovery of broad velocity components of nebular, rest-frame optical lines in this object (cite: Fischer2019outflowJ0033), we tested for the presence of a similar feature in the observed CO profile. We fit single, double and triple Gaussian models, but only the single Gaussian achieved optimal corrected Akaike Information criterion (cite: Cavanaugh1997CorrectedAkaikeCriterion) and Bayesian Information criterion (cite: Wit2012StatsModelUncertainty) scores. These scores calculate a goodness-of-fit estimate (e.g.,  $\chi^2$) but penalize overfitting by taking into account the number of degrees of freedom of the model. According to these criteria, double and triple Gaussian models are not as significant as the single Gaussian model. Thus, the results indicate no evidence of broad nor high velocity components within current data.

The total flux for each line was computed from the velocity integrated intensity maps (zeroth moment). Centered at the best fit central frequency, we used symmetric integration ranges spanning from $-0.85$ to $+0.85$ times the best-fit Gaussian FWHM. In this way we recover $\sim 99.5\%$ of the flux while keeping S/N$\gtrsim 3$ per channel. The resulting moment maps were then fit with a 2D Gaussian profile using CASA task `imfit`, using the coordinates of the peak pixel as a prior on their position. The inferred fluxes with their respective uncertainties are listed in Table [\[tab:lineflux\]](#tab:lineflux). The results of the fits are consistent with the sources being unresolved by the ACA Band 4 beam. For the CO nondetections (SGASJ1226-A, SGASJ1226-B and Sunburst Arc) we report $3\sigma$ point source upper limits assuming a fixed integration range width of 200 km s^−1^ around the best spectroscopic redshift available.

![](ciline_sgasj0033_v4.pdf)

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Aperture | Central Frequency | Species | Redshift | FWHM | Bandwidth $\Delta v$ | $\mu \Delta v S_\nu$ | $\mu L^\prime_\text{line}$ |
|  | GHz |  |  | km s^−1^ | km s^−1^ |  km s^−1^ | $10^{10}$ K km s^−1^ ^2^ |
| A.1+A.2 | $136.004 \pm 0.001$ | CO(4-3) | 2.3899 ± 0.000025 | $85 \pm 7$ | 164.2 | $1.96 \pm 0.15$ | $3.30 \pm 0.25$ |
| A.1+A.2 | $145.176 \pm 0.004$ | \[C i\] | 2.39010 ± 0.0009 | $75 \pm 26$ | 67.2 | $0.36 \pm 0.13$ | $0.53 \pm 0.19$ |
| A.3 | $135.993 \pm 0.005$ | CO(4-3) | 2.39018 ± 0.00012 | $94 \pm 20$ | 135.4 | $0.66 \pm 0.22$ | $1.1 \pm 0.4$ |
| SMG | $135.643 \pm 0.017$ | CO(4-3)$^{a}$ | 2.3989 ± 0.0005 | $430 \pm 87$ | 412.7 | $1.42 \pm 0.33$ | $2.4 \pm 0.6$ |

Table notes:

## Continuum photometry

The flux of the 870 μm continuum detection was determined in a similar way to the CO line flux (see Sect [3.1](#sec:emission_lines)): we fit single 2D Gaussians to each source using `imfit` on the cleaned continuum maps. In this case, the SGASJ0033 arc A.1 is resolved from the counter-image A.2 so we employed one Gaussian for each image. The (image plane) size of the best fit model for A.1 indicate that the arc is partially resolved along the major axis. Again, for the targets that were not detected, we quote the $3\sigma$ upper-limit for point sources based on the observed RMS and corrected by primary beam attenuation. We also measured the continuum flux on Band 4 ($\lambda_\text{obs}=\SI{2.1}{\milli\meter}$) data in a similar fashion. First we built dirty images after masking out the channels with detected and undetected line emission. Once again, SGASJ0033 is the only source with a reliable signal. The results are presented in Table [1](#tab:continuum_flux).

## SED fitting

![](sgasj0033_joint_sed_arc_v3.pdf)

We combined image plane optical HST photometry (four bands), ACA submillimeter continuum photometry (two bands) and IRAC near infrared photometry (two bands) when available to fit templates of spectral energy distributions (SEDs) and derive estimates of stellar mass and star formation rate. For this purpose, we used the high-$z$ version of the Multi-wavelength Analysis of Galaxy Physical Properties package (cite: daCunha2015HighZMagphysALESS). MAGPHYS uses precomputed grids of stellar emission (cite: Bruzual&Charlot2003SSP) and dust emission models (cite: daCunha2008MagphysPaper) to evaluate the likelihood that the observed multi-band photometry comes from each combination of stars plus dust models. The results are given as samples of the posterior probability distribution of the parameters of the models. The code operates under the principle of energy balance, which states that all the energy of the UV radiation field absorbed by the dust in the interstellar medium is re-emitted in the far infrared as a thermal continuum. When both the UV and FIR fluxes are observed, and a given attenuation law is assumed (cite: Charlot&Fall2000DustAttenuation), this principle provides a useful constraint that can break the degeneracies associated with galaxy reddening. Still, with no data in the mid infrared and a low total number of bands observed, SED fitting suffers from large uncertainties (e.g., from the unconstrained contribution of AGN). In order to address possible systematics we also ran CIGALE (cite: Boquien2019CIGALEpaper), another SED fitting code, and then compare with our MAGPHYS results. CIGALE allows more flexibility in the modeling choices, like the shape of the star formation history (SFH), the attenuation law or the inclusion of other components like radio synchrotron emission. For this experiment, we used the same stellar templates and attenuation law as MAGPHYS, but assumed a delayed exponential SFH and a nebular emission component (cite: Inoue2011NebularTemplates). We also used the simpler dust emission model proposed by (cite: Dale2014DustTemplate), which is a grid of templates that depend on two parameters: $\alpha_\text{SF}$, which governs the strength of the dust heating intensity, and $f_\text{AGN}$, the AGN fraction. Here we have chosen to fix $f_\text{AGN}=0$ and vary $\alpha_\text{SF}$ between 0 and 4. We found that both CIGALE and MAGPHYS offer reasonable fits to the observed bands, but the former produces on average $\sim 0.15$ dex and $\sim 0.3$ dex higher estimates of SFR and $M_\text{stars}$ respectively than MAGPHYS. These differences are consistent with the results of a comparison between MAGPHYS masses and EAGLE/SKIRT simulated galaxies (cite: Dudzeviciute2020AS2UDS). However, the Bayesian posterior probability distributions of these parameters produced by either codes do overlap within their 68% confidence intervals (see Figure [4](#fig:sed_j0033) for an example), so we do not consider the differences to be statistically significant. In what follows, we report MAGPHYS derived values corrected by magnification (see Table [\[tab:sed_results\]](#tab:sed_results)).

| Name | $\mu$ | $\log(\text{SFR}_{100})$ | $\log(M_\text{stars})$ | $\log(
    L_\text{dust})$ | $\log\left(M^{\text{SED}}_\text{dust}\right)$ | $\log\left(M^{\SI{870}{\micro\meter}}_\text{dust}\right)$ | $\log\left(M^{\SI{2.1}{\milli\meter}}_\text{dust}\right)$ |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  | M $_\odot$ ^−1^ | M $_\odot$ |  | M $_\odot$ | M $_\odot$ | M $_\odot$ |
| Sunburst Arc | 171 | $1.20_{-0.13}^{+0.07}$ | $9.44_{-0.11}^{+0.17}$ | $10.98_{-0.30}^{+0.18}$ | $<7.1$ | $<6.8$ | $<7.0$ |
| SGASJ1226-A$^{a}$ | 87 | $0.65_{-0.05}^{+0.11}$ | $9.38_{-0.11}^{+0.11}$ | $<10.7$ | $<6.4$ | $<6.5$ | $<7.4$ |
| SGASJ1226-B | 30 | $1.12_{-0.08}^{+0.21}$ | $9.73_{-0.16}^{+0.17}$ | $10.87_{-0.12}^{+0.37}$ | $6.8_{-0.2}^{+0.2}$ | $7.3\pm0.1$ | $<7.8$ |
| SGASJ0033-A$^{a}$ | 67 | $1.12_{-0.19}^{+0.22}$ | $10.10_{-0.17}^{+0.16}$ | $11.12_{-0.24}^{+0.25}$ | $7.10_{-0.14}^{+0.19}$ | $7.59 \pm 0.04$ | $7.65 \pm 0.14$ |
| SGASJ1226-G1$^{b}$ | 2.7 | $1.20_{-0.20}^{+0.17}$ | $10.09_{-0.08}^{+0.08}$ | $11.24_{-0.18}^{+0.15}$ | $8.01_{-0.15}^{+0.17}$ | $8.22 \pm 0.12$ | $<8.9$ |
| SGASJ0033-G1$^{c}$ | 5.4 | $1.81_{-0.33}^{+0.34}$ | $10.55_{-0.24}^{+0.27}$ | $11.89_{-0.32}^{+0.33}$ | $8.19_{-0.16}^{+0.18}$ | $8.63 \pm 0.08$ | $<8.8$ |

Table notes: The second column shows the fiducial magnification factor applied to bring values into the source plane. Below the horizontal rule, we add (for completeness) the results for the foreground galaxies detected in Band 7 except for the SMG which has a single detection in the near infrared and lacks a spectroscopic redshift. The last two columns, separated by a vertical line, contain the dust masses inferred from the continuum measurements in bands 7 and 4.

## Dust mass

The MAGPHYS fits to the far infrared SED deliver posterior probability distributions of the total dust mass, but since that part of the SED is sparsely sampled (single band detection or upper limits) the uncertainties are large. An alternative way to estimate the dust mass directly from the single band sub-millimetric flux is by using the framework proposed by (cite: Dunne2000SLUGS). This method is based on the assumption that optically thin dust traces the cold ISM, and therefore the observed continuum flux is proportional to the dust mass (cite: Eales2012DustEmissionAsMassProbe; Scoville2014DustEmissionAsGasProbeEvolution; Scoville2016MainSequenceAndGasMass). Following (cite: Scoville2016MainSequenceAndGasMass), we set the global mass-weighted dust temperature to $T_d=\SI{25}{\kelvin}$ and the dust emissivity index to $\beta=1.8$. Then, the dust mass is computed as, $$\begin{equation}
    \text{M}_\text{dust} = \frac{S_{\nu_\text{obs}} D_L^2 (1+z)^{-(3+\beta)}}{\kappa(\nu_\text{ref}) B_\nu(\nu_\text{ref}, T_d)} \left(\frac{\nu_\text{ref}}{\nu_\text{obs}}\right)^{2+\beta}\left(\frac{\Gamma_{\text{RJ(ref, 0)}}}{\Gamma_\text{RJ}}\right),
\end{equation}$$ where $\nu_\text{obs}$ is the observed frequency, $S_{\nu_\text{obs}}$ the measured flux and $D_L$ the luminosity distance. The quantity $\kappa(\nu_\text{ref})$ is the dust mass absorption coefficient at rest frame $\nu_\text{ref}$; here we adopted $\kappa(\SI{450}{\micro\meter})=\SI{1.3}{\centi\meter\squared\per\gram}$ (cite: Li&Draine2001DustISM). $B_\nu$ is the Planck function and $\Gamma_\text{RJ}\left(\nu,\, z,\, T_d\right)$ is a factor that accounts for the deviation of the Planck function from the Rayleigh-Jeans (RJ) law. The intrinsic dust masses (or upper limits) obtained with this method are presented along the SED results in Table [\[tab:sed_results\]](#tab:sed_results).

The validity of this method relies on the restriction $\lambda_\text{rest}>\SI{250}{\micro\meter}$, which ensures that one is probing the Rayleigh-Jeans tail and dust is optically thin (cite: Scoville2016MainSequenceAndGasMass). Here, the condition is met for SGASJ0033 and the Sunburst Arc, but not for the SGASJ1226 galaxies since 870 μm at $z=2.92$ becomes 222 μm. However, low metallicity galaxies –like SGASJ1226-A and B– typically have higher dust temperatures than their solar metallicity equivalents at fixed redshift (cite: RemyRuyer2013DwarfGalaxySurveyPhotometry; Saintonge2013MolGasLensedGalaxies). In such cases, the SED peak and Rayleigh-Jeans tail are shifted toward shorter wavelengths, hence relaxing the $\lambda_\text{rest}$ restriction. Also, the calibration of (cite: Scoville2016MainSequenceAndGasMass) did include 870 μm flux measurements of SMGs at $z\gtrsim 2.5$, since they were found to follow the same $L^\prime_\text{CO}-L_\nu(\SI{850}{\micro\meter})$ trend as local spirals and ULIRGs. For these two reasons, we believe that $\lambda_\text{obs}=\SI{870}{\micro\meter}$ remains a good tracer of dust mass for the two lensed galaxies in the SGASJ1226 system, and the method outlined above still applies. In any case, we repeated the measurement with the Band 4 continuum ($\lambda_\text{obs}=\SI{2.1}{\milli\meter}$), obtaining a very similar value for SGASJ0033 as with 870 μm ($\mu M_\text{dust}^{\SI{870}{\micro\meter}}=\SI{2.5+-0.3e9}{M\ensuremath{_\odot}}$ vs $\mu M_\text{dust}^{\SI{2.1}{\milli\meter}}=\SI{3.0+-0.8e9}{M\ensuremath{_\odot}}$), though with higher uncertainty. Despite tracing a rest-wavelength that is well within the RJ regime and closer to the reference wavelength of 850 μm, the 2.1 mm continuum is expected to be much fainter than 870 μm at these redshifts, hence the upper limits obtained with Band 4 measurements are less restrictive (see Fig. [5](#fig:tracer_comparison)).

## Molecular gas mass

A major goal of this paper is to constrain the molecular gas content of the source galaxies producing the giant arcs. To estimate the global molecular gas mass, we employ at least one of the following methods:

(i) *Based on $\element[][12]{CO}\left(J\to J-1\right)$ luminosity*: The observed CO line flux can be converted to the ground transition $\element[][12]{CO}\left(1\to 0\right)$ luminosity, which is the traditional and best calibrated H~2~ tracer. To correct for the excitation level, here we adopt the median ratios $r_{J1}=L^\prime_{\text{CO}(J\to J -1)} / L^\prime_{\text{CO}(1 \to 0)}$ from (cite: Kirkpatrick2019COEmissionAGN) calibrated in a sample of matched redshift and intrinsic infrared luminosity. Once $L^\prime_{\text{CO}(1\to 0)}$ is computed, we apply the (cite: Genzel2015DustAndCOscalingRelations) recipe for estimating the CO-to-H~2~ conversion factor (hereafter $\alpha_\text{CO}$) based on gas-phase metallicity. Without a homogeneous metallicity indicator for every target, we adopt the stellar metallicities reported by (cite: Chisholm2019MegaSauraMetallicity) as a proxy. A discussion on the validity of this choice can be found in Appendix [6](#sec:metallicity).

(ii) *Based on M~dust~:* Giant molecular clouds in the ISM of star-forming galaxies contain cold dust that can be detected in long-wavelength thermal continuum emission (cite: Eales2012DustEmissionAsMassProbe; Magdis2012EvolvingISMatRedshiftTwo). With a measurement of the dust mass available (see Sect. [3.4](#sec:dust_mass)), one can use the gas-to-dust mass ratio ($\delta_\text{GDR} = M_\text{mol}/M_\text{dust}$) to infer the total molecular mass (cite: Scoville2016MainSequenceAndGasMass). Here we adopt a scaling with gas-phase metallicity as $\delta_\text{GDR}\propto Z^\gamma$, normalized at $\delta_\text{GDR}(Z_\odot)=100$ (cite: Draine2007Dust) and a power-law index $\gamma=-0.85$ taken from (cite: Tacconi2018PHIBSS2MainSequence). This calibration should be valid for solar to slightly subsolar metallicities (cite: Leroy2011COtoH2; Remy-Ruyer2014GasToDustLocalGalaxies), but will be revisited in Sect. [4.3](#sec:co_deficit). As presented in Sect. [3.4](#sec:dust_mass), we derive dust mass from both Band 7 (870 μm) and Band 4 (2.1 mm) continuum.

(iii) *Based on $\left[C i\right]_{1 \to 0}$ luminosity:* The fine structure lines of atomic carbon have been proposed as reliable tracers of cold gas (cite: PapadopoulosAndGreve2004CIasGasTracer; Danielson2011StarformingGalaxyAtRedshift2; Popping2017CIandCOatZ2). In order to convert $\left[C i\right]_{1 \to 0}$ luminosity to H~2~ mass one first has to compute the total atomic carbon mass. Since both $\element[][3]{P_2}\to\element[][3]{P_1}$ and $\element[][3]{P_1}\to\element[][3]{P_0}$ lines are optically thin and have low critical densities, the mass only depends on the luminosity and excitation temperature $T_\text{ex}$ (cite: Weiss2003GasAndDustCloverleaf; Weiss2005AtomicCarbon). The excitation temperature can be estimated from the luminosity ratio of both transitions, but since our data only covers the $\element[][3]{P_1}\to\element[][3]{P_0}$ transition, we set $T_\text{ex}=\SI{30}{\kelvin}$ as typically assumed in the literature (cite: Bothwell2017AtomicCarbonSPT; Popping2017CIandCOatZ2; Valentino2018SurveyOfAtomicCarbon; Brisbin2019NeutralCarbonAndCOMassiveSFG; Boogaard2020ASPECS-COExcitation; Boogaard2021ColdGasLowMassSFGs). At $T_\text{ex}=\SI{30}{\kelvin}$, a 20% temperature variation produces a $\lesssim 1\%$ variation in M~\[CI\]~ (cite: Weiss2005AtomicCarbon; Boogaard2020ASPECS-COExcitation). Once the atomic carbon mass has been computed (i.e., with Eq. (1) of (cite: Weiss2005AtomicCarbon)), we use the metallicity dependent prescription of (cite: Heintz&Watson2020CItoH2) for the carbon abundance to convert to molecular gas mass. Unlike method (ii) whose $\delta_\text{GDR}(Z)$ scaling is calibrated on CO-derived gas masses, the (cite: Heintz&Watson2020CItoH2) relation was obtained directly from the \[C i\]/H~2~ column density ratio observed in a sample of quasar and gamma ray burst absorbers at high-$z$, and hence is independent of the $\alpha_\text{CO}$ factor. For this reason, the \[C i\]-based M~mol~ provides useful consistency checks on the previous two methods.

Since SGASJ0033-A has detections of CO, \[C i\] and dust continuum, we can use it as a benchmark for the three methods listed above. Following method (i) we adopted $r_{41}=0.37\pm0.12$ (cite: Kirkpatrick2019COEmissionAGN) and $\alpha_\text{CO}=\SI{4.5+-0.1}{M\ensuremath{_\odot}}\,(\si{\kelvin\kilo\meter\per\second\parsec\squared})^{-1}$ based in our fiducial metallicity $Z/Z_\odot=\num{0.84+-0.02}$ (Appendix [6](#sec:metallicity)). We then converted the observed image plane CO flux into $\mu M_\text{mol, CO}^{A.1+A.2}=\SI{4.0+-1.3e11}{M\ensuremath{_\odot}}$, where $A.1+A.2$ indicates that the value considers the blended flux of the two lensed images. With $\delta_\text{GDR}(Z)=117$ and $X_\text{[CI]}(Z)=\num{1.3+-0.8e-5}$ (for reference, the typical value assumed for high-$z$ studies is 3 × 10^−5^, (cite: Valentino2018SurveyOfAtomicCarbon)) results from methods (ii) and (iii) are $\mu M_\text{mol, dust}^{A.1+A.2} = \SI{2.9+-0.3e11}{M\ensuremath{_\odot}}$ and $\mu M_\text{mol, [CI]}^{A.1+A.2} = \SI{1.1+-0.7e11}{M\ensuremath{_\odot}}$ respectively. While the values obtained with methods (i) and (ii) are in reasonable agreement for both tracers of M~dust~, the (iii) method yields an estimate that is $\sim 2\sigma$ lower. This can be a result of the low significance of the \[C i\] detection or a systematic effect driven by the uncertain carbon abundance factor. In what follows, we adopt the CO estimate as the fiducial value of M~mol~ for SGASJ0033-A.

![](gasmass_different_tracers_v1.pdf)

# Discussion

## Lensed galaxies in context

In order to locate our derived ISM properties of lensed galaxies within the context of high-$z$ scaling relations, we compare our results with a pair of reference samples. The main reference sample is the latest release of the IRAM Plateau de Bure High-z Blue Sequence Survey (cite: Tacconi2013PHIBSS1; Tacconi2018PHIBSS2MainSequence) containing 1444 molecular gas measurements at $0\leq z \leq 4$ and covering a stellar mass range from $\log\left(\text{M}_\text{stars}/\text{M}_\odot\right)=9$ to 11.9. The sample includes both individual galaxies and stacked measurements from surveys with high detection rates. The sample was selected to represent the overall SFG population in a wide range of basic galaxy parameters. The bulk of the sample are galaxies that belong to the star-forming main sequence, with a modest contribution from star-bursting outliers (cite: Tacconi2018PHIBSS2MainSequence). From this parent sample we selected two subsets: firstly, a high-$z$ sample defined as all the sources in the PHIBSS 1/2 catalog with spectroscopic redshift greater than 2, excluding lensed galaxies. This subset contains 138 objects with stellar masses between  × 10^9.8^ M $_\odot$ and  × 10^11.8^ M $_\odot$ and a median redshift of 2.3. The molecular gas masses were derived from CO luminosity for 59 sources and from dust continuum for the other 79 sources. Secondly, the entire xCOLD GASS sample (cite: Saintonge2011xCOLDGASSp1) as appears in PHIBSS 1/2. Contains 306 galaxies at $z\sim 0$ with CO measurements and stellar masses ranging from  × 10^9^ M $_\odot$– × 10^11.3^ M $_\odot$.

We also compiled a sample of molecular gas measurements in UV-bright strongly-lensed galaxies from and . These two studies provide global properties and molecular gas masses for several giant arcs, most of them selected from optical surveys. In both studies, a complete sampling of the infrared SED with *Spitzer* and *Herschel* is combined with dedicated PdBI or IRAM 30m CO line observations to constrain the parameters of the cold ISM of these galaxies. After we remove duplicate objects between the two samples and exclude the SGASJ1226-A arc from the table, this sample comprises 17 sources at mean redshift of $z\approx 2.1$ and a de-lensed stellar mass range of  × 10^9.3^ M $_\odot$– × 10^11.5^ M $_\odot$.

Each sample uses their own set of calibrations and tracers for the molecular gas. On one hand, the PHIBSS catalog uses the metallicity-dependent recipe for estimating $\alpha_\text{CO}$, while used the (cite: Genzel2012MetallicityCOtoH2) recipe. On the other hand, assumed a constant Galactic value of $\alpha_\text{CO} = 4.6\,\si{M\ensuremath{_\odot}}(\si{\kelvin\kilo\meter\per\second\parsec\squared})^{-1}$. Here, we attempted to standardize the reference samples to a common scheme for unbiased comparison with our sample. We updated the $M_\text{H2}$ values in Table 6 of to the calibration based on the metallicities provided in their Table 5. With this calibration, the molecular gas mass estimations become 0.2 dex lower on average. For the sample we retrieved metallicities from for the duplicate sources cB58 and the *Cosmic Eye*. For the rest of their sample, we computed metallicities from the MZR as appears in and then converted to the (cite: Denicolo2002MetallicityCalibration) scale for consistency with . We finally applied the recipe to get $\alpha_\text{CO}$ and updated the reported values of $M_\text{mol}$ accordingly. This resulted in $\sim 0.1$ dex higher gas mass estimations relative to their published values.

We also checked that the STARBURST99 stellar metallicities from (cite: Chisholm2019MegaSauraMetallicity) in our sample are consistent with the expectations from the mass metallicity relation (MZR; see Sect. [1](#sec:intro)): we fed the SED-derived stellar masses into the MZR recipe used by and converted them to the (cite: Denicolo2002MetallicityCalibration) scale. The resulting oxygen abundances are all within 0.2 dex of the (cite: Chisholm2019MegaSauraMetallicity) value. Thus, even if the intrinsic scatter of the MZR is lower than 0.2 dex at these resdhifts, the deviations we observe are fully consistent with our $M_\text{stars}$ uncertainty.

![](SF_MS_scaling_v8.pdf)

Figure [6](#fig:ms) shows the ranges of stellar mass and star formation rate that become accessible with the help of strong gravitational lensing. Compared to the unlensed high-$z$ PHIBSS1/2 sample, the lensed galaxies occupy a much wider range in both SFR and $M_\text{stars}$, while still being located near (within $1\sigma$ errors) the empirical MS proposed in . In particular, the four sources in our sample have stellar masses well within the range of the $z\sim 0$ SFGs represented by the xCOLD GASS sample, a regime not yet explored by unlensed surveys at this redshift.

The ratio between the total molecular gas mass and the total stellar mass (hereafter gas fraction, $M_\text{mol} / M_\text{stars}$) is a crucial parameter to characterize the galaxy-integrated ISM properties, since it relates the amount of gas available to produce stars in relatively short timescales with the accumulated stellar mass buildup. There is a growing consensus that high-redshift galaxies have larger gas fractions than local galaxies for a given stellar mass (cite: Scoville2017EvolutionISM; Tacconi2018PHIBSS2MainSequence; Liu2019A3COSMOScoldGasEvolution), a fact that might be explained by increased rates of gas accretion from the cosmic web at earlier times (cite: Dekel2009ColdModeAccretion; Walter2020EvolutionOfBaryons). However, the current surveys of molecular gas at high redshift are not sensitive to lower mass ($M_\text{stars} \lesssim \SI{e10}{M\ensuremath{_\odot}}$) systems (cite: Hodge&daCunha2020Review), so it remains unclear whether galaxies in this regime follow the same trends (cite: Coogan2019SuppressedCOinLowMetGals; Boogaard2021ColdGasLowMassSFGs).

In Fig. [7](#fig:moneyplot), we compare the gas fractions of our sample with the literature samples mentioned above. We observe that the $z\sim2$ lensed galaxies do, in fact, have larger gas fractions than the local xCOLD GASS sample, but these values are lower than expected for their redshift and mass range based on the extrapolation of the relation. Our detections and upper limits reach values that are below the sensitivities of individual ALMA observations of low mass galaxies at $z\approx 2$ (cite: Coogan2019SuppressedCOinLowMetGals) and deep stacked measurements from the ASPECS survey (cite: Inami20202StacksAspecsCO).

In the left panel we see that gas fraction is anticorrelated with stellar mass for the high-$z$ PHIBSS 1/2 galaxies, that is, more massive galaxies have relatively smaller gas reservoirs. In the stellar mass interval between  × 10^10.3^ M $_\odot$ and  × 10^11.5^ M $_\odot$, both the high-$z$ and the local sample follow similar trends, but at lower masses, the local sample reveals a flattening of the relation. According to , this nonlinear behavior can be interpreted as a manifestation of the "mass-quenching" feature of the main sequence (cite: Whitaker2014MainSequence; Schreiber2015MainSequence), though it has also been suggested that this is just a selection effect due to mass incompleteness (cite: Liu2019A3COSMOScoldGasEvolution). Here we show that the lensed galaxies distribute at $\log(M_\text{mol}/M_\text{stars})\lesssim - 0.5$, with no clear indication of M~stars~ dependence. Although the scatter is large and the number of sources small, the lensed galaxies have, on average, gas fractions one order of magnitude below the value one would obtain by extrapolating the linear relation beyond the PHIBSS 1/2 mass range at $z>2$. In detail, the offsets from the linear (red line in Fig. [7](#fig:moneyplot)) relation are 0.7, 0.8, $>1.2$ and $>1.1$ dex for SGASJ0033-A, SGASJ1226-B, SGASJ1226-A and the Sunburst Arc, respectively. An alternative second-order relation is also given in (dotted gray line in Fig. [7](#fig:moneyplot)), which accounts for the low mass flattening, but even with this correction the lensed galaxies show a lower gas fraction than predicted.

The right panel of Fig. [7](#fig:moneyplot), shows a comparison of the gas depletion timescale ($M_\text{mol}/\text{SFR}$) as a function of redshift. This plot also includes the intermediate-redshift sources we had excluded from the PHIBSS 1/2 subsample. While the scatter of points with respect to the scaling relation is large ($0.4$ dex), the lensed galaxies from this work present gas depletion timescales that are shorter than expected based on the relation by 0.6, 0.6, $>0.8$ and $>0.8$ dex for SGASJ0033-A, SGASJ1226-B, SGASJ1226-A and the Sunburst Arc, respectively. SGASJ0033-A is in agreement with other (albeit more massive) sources at the same redshift, but the tension is higher for the nondetected Sunburst Arc and SGASJ1226-A, whose gas will deplete in less than 100   at the current SFR. Taken at face value, these results suggest that the lensed galaxies track a gas-deficient population that contrasts with the more massive galaxy population at high-redshift. In the following, we discuss on possible biases affecting the measurements.

![](logGasfrac_vs_logTdepl_vs_redshift_v7.pdf)

## The molecular gas deficit cannot be explained by systematics in M~stars~ or SFR

Before we can ascribe the observed deficit in the gas fraction and depletion time to the properties of the sampled galaxy population, we explore potential systematic effects on the measured quantities that can explain the discrepancy. For this, we temporarily adopt the hypothesis that our sample should strictly follow the scaling relations. Under this hypothesis, the low gas fraction and depletion time can be driven, for example, by a systematic underestimation of the molecular gas mass, or conversely, by an overestimation of the stellar mass and SFR. In this section we focus on the latter effect, while a discussion on a possible underestimation of molecular gas mass is postponed to section [4.3](#sec:co_deficit).

A shift on the measured stellar mass (keeping everything else constant) would need to be on the order of 0.7-1.2 dex to reconcile the observed gas fraction with . Some degree of offset in this direction could be achieved, for example, if MAGPHYS systematically overpredicts the stellar mass when the rest-frame near and mid infrared photometry are poorly constrained (cite: daCunha2015HighZMagphysALESS). However, if the measured metallicity is correct (see Appendix [6](#sec:metallicity)), then a lower estimate of the stellar mass (e.g., from a different SED fitting code) will create tension with the MZR (as parameterized by (cite: Genzel2015DustAndCOscalingRelations)). In other words, the gas fraction relation favors a lower stellar mass whereas the MZR favors a higher stellar mass.

Another possibility to reconcile the measured gas fraction with is that magnification factor is systematically over-estimated: lower values of $\mu$ will displace points horizontally in the left panel of Fig. [7](#fig:moneyplot), since ratios of flux-dependent quantities cancel out the factor $\mu$ (under the assumption that the differential lensing effect is not too severe). But in the gas fraction versus stellar mass diagram the horizontal offsets from the relation are at least $\sim 1$ dex larger than the vertical offsets (listed in section [4.1](#sec:scaling_relations)), so magnification alone cannot explain them. Even if we used the image plane uncorrected values (i.e., $\mu=1$), the square symbols in Fig. [7](#fig:moneyplot) would remain below the relations.

However, in the high magnification regime, differential lensing can become significant. There are at least three geometrical conditions that can produce a higher magnification for the stellar component relative to the gas component, thus lowering the derived gas fraction: (1) if the UV emission from stars is spatially offset from the molecular gas reservoirs and closer to the lensing caustic lines; (2) if the stars’ brightness distribution is more compact than the gas distribution; or (3), with a combination of the previous two effects. The first condition is certainly possible, since spatial offsets between gas and stars are commonly observed in resolved studies of unlensed, high-redshift galaxies (cite: Hodge&daCunha2020Review). For example, (cite: Chen2015ALMAeCDFSMorph) found an average intrinsic scatter in the positional offsets between ALMA 870 μm detections and their HST counterparts of $\approx\ang{;;0.3}$, in a sample of 48 SMGs at $z=1-3$. Similar offsets are found for other gas tracers such as CO lines (cite: CalistroRivera2018CoAndDustDistributionALESS). But for any given system, the actual configuration of gas and stars is random and independent of the foreground lens. Even if we are selecting sources with a highly magnified stellar component, there is nothing in our selection function that favors a less magnified gas component. This means that, statistically, the magnification bias due to spatial offsets in the source plane plays in both directions and eventually cancels out. Then, based on spatial offsets alone, it is unlikely that both our lensed sources and the ones from and have a systematically more magnified stellar component. Most importantly, large offsets between unobscured UV emission and dust or gas tracer are preferentially seen in galaxies with high dust obscuration such as in GN20 (cite: Hodge2015ResolvedGN20), but less commonly in low metallicity galaxies. Regarding the sizes of each component, observational evidence suggest that the background population will have a more compact dust component than the stellar component. This is true for both massive galaxies and intermediate mass galaxies (cite: Fujimoto2017DancingALMA1; Kaasinen2020DustSizeAndKinematicsThreeASPECSgxs). So if this was the case for the galaxies in our sample, it will drive larger magnifications for the gas component pushing the gas fraction to higher values, not lower. In conclusion, it is still possible to have a geometrical configuration of the source system in which lensing preferentially boosts the stellar component over the gas component, for example, with an extended gas distribution relative to stars coupled with a large spatial offset, but such configurations are extremely rare, making it unlikely to produce a systematic effect. Unfortunately, we cannot currently provide a quantitative estimation of the bias in the magnification. That will require matching HST resolution with ALMA observations of the gas/dust in the arcs.

Now, we consider the case where SFR is overestimated but M~stars~ is not. Then, at fixed M~mol~, the depletion timescale appears lower than it actually is. Also, for a fixed stellar mass and redshift, predicts higher gas fractions at higher SFR. Again, this effect can be due to MAGPHYS using priors that prefer templates with higher specific SFR (SFR/M~stars~). But the best fit MAGPHYS models are already on or slightly below the MS, so if the stellar masses are correct, then a lower value for the SFR will displace them even further from the MS, toward the locus of quenched galaxies. This is again an implausible scenario, for these galaxies have strong indications of star formation activity (e.g., young ages, blue colors, nebular emission lines, etc.).

Moreover, independent measures of stellar mass and SFR for some of the lensed galaxies in this work have been reported in the literature. For example, found SGASJ1226-A to have $\log(\mu M_\text{stars}/\text{M}_\odot)=11.32\pm0.15$ and $\log(\mu\text{SFR}/(\text{M}_\odot\,\text{yr}^{-1}))= 3.15\pm0.08$, which convert to $9.38\pm0.15$ and $1.2\pm0.08$ respectively when matched to our fiducial magnification $\mu=87$. While the SFR reported here is three times lower, the stellar mass is in excellent agreement. More recently, (cite: Vanzella2021SunburstArcClusterFormationEfficiency) reported $\log(M_\text{stars}/\text{M}_\odot)\approx 9.0$ and $\log(\text{SFR}/(\text{M}_\odot\,\text{yr}^{-1}))\approx 1$ for the *Sunburst* galaxy, also consistent with our estimates within the uncertainties. The considerations above plus the agreement with values obtained by other teams suggest that the SED-derived quantities alone cannot account for the tension with relations, thus disfavoring the hypothesis that they hold true in this region of the parameter space.

## Low metallicity as the driver of the apparent gas deficit

If the cold gas deficit is not caused by a systematic overestimation of M~stars~ and SFR, then the conclusion is that the molecular gas mass might be underestimated. Before exploring this idea, we first note that the gas deficit is observed not only in the four galaxies in our sample, but also in the compilation of lensed sources from and . Our results provide additional evidence for a divergence from standard scaling relations in intermediate- to low-mass SFGs at $z\gtrsim 2$. But this result is not exclusive to strongly lensed galaxies. For example, (cite: Coogan2019SuppressedCOinLowMetGals) put stringent upper limits on the molecular gas mass of five $z\sim 2$ Lyman Break Galaxies (LBGs), with values that also challenge the scaling relations. More recently, (cite: Boogaard2021ColdGasLowMassSFGs) used data from the ASPECS Large Program (cite: Aravena2019ASPECSMolGasEvolution) to constrain the gas content of 24 MUSE-selected SFGs at $z=3-4$ in the Hubble Ultra Deep Field (HUDF). At the standard Galactic value for $\alpha_\text{CO}$, (cite: Boogaard2021ColdGasLowMassSFGs) also obtain gas fractions upper limits which are in tension with scaling relations from and (cite: Liu2019A3COSMOScoldGasEvolution).

In both lensed and unlensed studies, metallicity is often pointed out as the main driver of these discrepancies. In particular, it seems that the effect of low metallicity has a stronger impact in the tracer-to-gas conversion factor than expected. In other words, the lack of CO, dust or neutral carbon emission in high-$z$ galaxies may reflect a redshift evolution of $\alpha_\text{CO}$, $\delta_\text{GDR}$, and $X_{[C i]}$ , respectively. For example, at a fixed metallicity, $\alpha_\text{CO}$ in a high-$z$ SFG should be 5 to 30 times larger than in a local SFG in order to explain the deficit. Such high values of $\alpha_\text{CO}$ can be produced by CO-faint gas: a decreased metal abundance implies fewer C and O atoms but also a lower proportion of dust grains (high $\delta_\text{GDR}$), thus providing less shielding from the far-ultraviolet radiation that causes CO dissociation. As H~2~ is less impacted by this effect (cite: GnedinAndDraine2014SelfShieldingMolecularHydrogen), the abundance of CO relative to H~2~ becomes much lower (cite: Bolatto2013COtoH2). In the Milky Way, a significant amount of H~2~ resides outside the CO-bright cores of molecular clouds, as inferred from independent tracers such as $\gamma$-rays (cite: Grenier2005DarkGasSolarNeighborhood). But in low-metallicity star-forming local dwarf galaxies the CO-faint gas is much more pervasive, filling the regions where most of the carbon is occupying its first ionized state. In such cases, CO emission cannot trace the bulk of the molecular gas budget and the \[C ii\] 158 μm line emerges as an alternative tracer (cite: Wolfire2010DarkMolGas; GloverAndClark2012StarFormationInMetalPoorGas; Schruba2012LowCOLuminosityDwarfs; Amorin2016COtoH2; Madden2020TotalMolecularGasDark).

In principle, $\alpha_\text{CO}(Z)$ should account for the CO-faint gas at low metallicity, but several prescriptions exist in the literature and there is no consensus on the slope of the relation. While most of the published recipes agree that $\alpha_\text{CO, MW} \approx 4.5\,\si{M\ensuremath{_\odot}}(\si{\kelvin\kilo\meter\per\second\parsec\squared})^{-1}$ at solar metallicity, the dispersion is very large at lower metallicities. The power-law index $\gamma$ can vary from $-0.65$ (cite: Narayanan2010FormationOfSMGs) to $-3.39$ (cite: Madden2020TotalMolecularGasDark), but only the steeper laws ($\gamma\lesssim -2.0$, normalized to $\alpha_\text{CO}(Z_\odot)=\alpha_\text{CO, MW}$) are able to boost M~mol~ up to $\sim 1.2$ dex at the metallicity range studied here. Using such recipes (cite: Schruba2012LowCOLuminosityDwarfs; Madden2020TotalMolecularGasDark) could put our galaxies closer to the scaling relations found for the gas fraction and depletion time, especially for the SGASJ1226 system which has the lowest metallicities.

A similar argument can be made regarding $\delta_\text{GDR}$. In both observations of local galaxies and predictions from ISM models $\delta_\text{GDR}$ is found to increase inversely proportional to Z, with a power-law index close to unity (cite: Leroy2011COtoH2; Magdis2012EvolvingISMatRedshiftTwo; Sandstrom2013AlphaCOandGDRLocal). Other authors find that the scaling steepens at lower metallicity and thus a double power-law is best suited (cite: Remy-Ruyer2014GasToDustLocalGalaxies). At higher redshift, studies of low mass galaxies have shown that either a shift in normalization or a steeper relation is needed to account for the low dust luminosity observed (cite: Coogan2019SuppressedCOinLowMetGals).

Finally, large uncertainties also affect the determination of the neutral carbon abundance $X_{[C i]}$ calibration. On one hand, theoretical prescriptions are strongly sensitive to modeling choices, such as the physics of cosmic rays and molecular cloud evolutionary states (cite: Hodge&daCunha2020Review). On the other hand, fully empirical calibrations are not yet available. ALMA is starting to fill the gap with observations of \[C i\] emission in the local (cite: Crocker2019ResolvedAtomicCarbonLocal) and distant (cite: Valentino2018SurveyOfAtomicCarbon) Universe, but those results are still dependent on CO or dust-based estimates of M~mol~, which suffer from the aforementioned uncertainties. Here we have used a recipe that was calibrated independently from CO, but has some other caveats: (cite: Heintz&Watson2020CItoH2) used a small sample of quasar and gamma ray burst absorbers with abundance measurements of both C i^\*^ and H~2~. Absorption lines yield line-of-sight column densities, rather than surface densities, so the authors assume that the ratio between column densities of C i and H~2~ is equal to the surface density ratio. Furthermore, a single line of sight does not necessarily probes all the phases and conditions where neutral carbon and H~2~ coexist. Metallicities are also derived in absorption, hence are not directly comparable to the standard nebular emission line determination of oxygen abundances.

Given the large dispersion in tracer-to-gas calibrations in the subsolar metallicity regime and the small size of our sample, it remains difficult to falsify the hypothesis proposed above. In other words, the molecular gas scaling relations of massive galaxies at high redshift may not apply to lower mass galaxies. For example, one could envision a scenario in which recent starburst consumed or dispersed most of the gas available. But this claim cannot be confirmed without a more systematic calibration of gas tracers. Deciding whether the gas deficit in star-forming galaxies with $\text{M}_\text{stars} \lesssim \SI{e10}{M\ensuremath{_\odot}}$ is real will require larger samples and deeper integration times using the full ALMA array, even with the aid of strong lensing.

# Summary and conclusions

In this paper, we have reported ACA observations of the molecular gas on four star-forming systems at $z\gtrsim 2.5$ that are strongly-lensed by foreground clusters and were selected as bright giant arcs in the optical. We used different methods and tracers, in order to assess possible systematic effects. The resulting detections and upper limits, in combination with ancillary multiwavelength data, allowed us to characterize the global properties of the cold ISM such as gas fraction and gas depletion timescale in these galaxies compared to existing scaling relations.

Out of four galaxies of similar masses and SFR, only the most massive, SGASJ0033, was detected in CO(4-3), $\left[C i\right]_{1 \to 0}$ and dust continuum emission (see Fig. [2](#fig:coline0033)). The galaxy exhibits a very narrow (FWHM $\approx \SI{85}{\kilo\meter\per\second}$) line profile coupled with a low significance asymmetric wing at high velocity. The highly magnified SGASJ1226-A was not detected in either CO(5-4) nor dust continuum. Instead, a companion lensed galaxy at the same redshift, SGASJ1226-B, was detected in Band 7 continuum (see Fig. [1](#fig:rb7_continua)) implying larger amounts of gas than in the A component. Also, no detections were made toward the extremely bright giant arc known as the Sunburst Arc. However, due to the high magnification of the source, the intrinsic upper limits can probe down to $\SI{e9}{M\ensuremath{_\odot}}$ in molecular gas mass (assuming the typical tracer-to-gas calibrations, see Fig. [5](#fig:tracer_comparison)). Remarkably, this result implies a gas depletion timescale shorter than $\sim\SI{70}{\mega\year}$.

The inferred gas fraction in the sample is higher than in $z=0$ SFGs, in agreement with the trend of increasing gas fraction at high redshift. However, the gas fraction is roughly $0.5$ to $1.0$ dex lower than predicted by the (cite: Tacconi2018PHIBSS2MainSequence) () scaling relations based on stellar mass, redshift and offset from the MS (see Fig. [7](#fig:moneyplot)). Similarly, gas depletion timescale is also below the expected value based in the relation but with a milder offset. The lensed galaxies studied here lie only $\sim 0.6$ to $\sim 0.8$ dex below the locus of more massive unlensed galaxies at the same redshifts (see Fig. [7](#fig:moneyplot)).

To investigate whether the apparent gas deficit is real, we explored systematic offsets that could be driving it. We find that the result is not strongly affected by systematic effects on SED fitting, as it would take unrealistic offsets in M~stars~ and SFR to drive the measured discrepancies with the scaling relations. We also explore the effect of differential lensing, but we conclude that it is unlikely to drive a large systematic offset in our sample of lensed galaxies plus the ones from literature. We propose that the apparent gas deficit is rather due to systematic uncertainties in the tracer-to-gas conversion factor dependence on metallicity. Our results favor a scenario in which the emission of CO, dust continuum, and \[C i\] are more strongly suppressed than what typical calibrations predict. Of course, this does not rule out the possibility of these galaxies actually have less gas than expected, due for example, to recent starburst episodes having consumed most of the available gas.

Finally, we stress that in using shallow ACA observations in combination with the lensing effect of massive clusters, it is possible to detect the molecular gas in a $\text{M}_\text{stars}\sim\SI{e10}{M\ensuremath{_\odot}}$ galaxy and to put constraints on the molecular gas content of less massive galaxies. Expanding this technique to a statistical sample of giant arcs will tell if the apparent gas deficit is a common feature in lower mass galaxies at high-redshift. However, in order to get accurate estimates of the molecular gas mass, it is necessary to build improved calibrations of the known tracers with respect to metallicity.

# Acknowledgements

We thank the anonymous referee for the constructive feedback and helpful comments. We also thank Ian Smail for the feedback about the manuscript. This paper makes use of the following ALMA 7m array data: ADS/JAO.ALMA#2018.1.01142.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research is also based on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with programs 15377, 15101, 15378, 12368 and 14170. In addition, this paper has made use of *Spitzer* Space Telescope data from the NASA/IPAC Infrared Science Archive, which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology. SL was funded by project FONDECYT 1191232. LFB was partially supported by CONICYT Project BASAL AFB-170002. MA acknowledges support from FONDECYT grant 1211951, CONICYT + PCI + INSTITUTO MAX PLANCK DE ASTRONOMIA MPG190030 and CONICYT+PCI+REDES 190194. This research made use of Astropy,[^4] a community-developed core Python package for Astronomy (cite: Astropy2013PaperI; Astropy2018PaperII). All figures were prepared using Matplotlib (cite: Hunter2007MatplotlibPaper) and Seaborn (cite: Waskom2020Seaborn). The scaling relations used in this paper were obtained from convenience routines included in the A^3^COSMOS gas evolution library [^5] (cite: Liu2019A3COSMOScoldGasEvolution).

147 natexlab

(ref: ALMAPartnership2015LensedSMGz3) ALMA Partnership, Vlahakis, C., Hunter, T. R., et al. 2015, ApJL, 808, L4

(ref: Amorin2016COtoH2) Amorı́n, R., Muñoz-Tuñón, C., Aguerri, J. A. L., & Planesas, P. 2016, A&A, 588, A23

(ref: Apostolovski2019ImagingMolGasSPTatz5.7) Apostolovski, Y., Aravena, M., Anguita, T., et al. 2019, A&A, 628, A23

(ref: Aravena2019ASPECSMolGasEvolution) Aravena, M., Decarli, R., Gónzalez-López, J., et al. 2019, ApJ, 882, 136

(ref: Astropy2018PaperII) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Astropy2013PaperI) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Baker2004MolGasInCB58) Baker, A. J., Tacconi, L. J., Genzel, R., Lehnert, M. D., & Lutz, D. 2004, ApJ, 604, 125

(ref: Baldwin1981BPTpaper) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5

(ref: Blanton2017SloanIV) Blanton, M. R., Bershady, M. A., Abolfathi, B., et al. 2017, AJ, 154, 28

(ref: Bolatto2008ExtragalacticGMCs) Bolatto, A. D., Leroy, A. K., Rosolowsky, E., Walter, F., & Blitz, L. 2008, ApJ, 686, 948

(ref: Bolatto2013COtoH2) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Boldrin2012PredictedGiantArcsNumber) Boldrin, M., Giocoli, C., Meneghetti, M., & Moscardini, L. 2012, MNRAS, 427, 3134

(ref: Boogaard2021ColdGasLowMassSFGs) Boogaard, L. A., Bouwens, R. J., Riechers, D., et al. 2021, arXiv e-prints, arXiv:2105.12489

(ref: Boogaard2020ASPECS-COExcitation) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, ApJ, 902, 109

(ref: Boquien2019CIGALEpaper) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: Bothwell2017AtomicCarbonSPT) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, MNRAS, 466, 2825

(ref: Brisbin2019NeutralCarbonAndCOMassiveSFG) Brisbin, D., Aravena, M., Daddi, E., et al. 2019, A&A, 628, A104

(ref: Bruzual&Charlot2003SSP) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Bussmann2013SMALensedz1.5) Bussmann, R. S., Pérez-Fournon, I., Amber, S., et al. 2013, ApJ, 779, 25

(ref: Canameras2017DustyGemsResolved60pc) Cañameras, R., Nesvadba, N., Kneissl, R., et al. 2017, A&A, 604, A117

(ref: CalistroRivera2018CoAndDustDistributionALESS) Calistro Rivera, G., Hodge, J. A., Smail, I., et al. 2018, ApJ, 863, 56

(ref: Carilli&Walter2013Review) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105

(ref: Casey2019Mambo9) Casey, C. M., Zavala, J. A., Aravena, M., et al. 2019, ApJ, 887, 55

(ref: Cavanaugh1997CorrectedAkaikeCriterion) Cavanaugh, J. E. 1997, Statistics & Probability Letters, 33, 201

(ref: Chabrier2003IMF) Chabrier, G. 2003, PASP, 115, 763

(ref: Charlot&Fall2000DustAttenuation) Charlot, S. & Fall, S. M. 2000, ApJ, 539, 718

(ref: Chen2015ALMAeCDFSMorph) Chen, C.-C., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 194

(ref: Chisholm2019MegaSauraMetallicity) Chisholm, J., Rigby, J. R., Bayliss, M., et al. 2019, ApJ, 882, 182

(ref: Coogan2019SuppressedCOinLowMetGals) Coogan, R. T., Sargent, M. T., Daddi, E., et al. 2019, MNRAS, 485, 2092

(ref: Crocker2019ResolvedAtomicCarbonLocal) Crocker, A. F., Pellegrini, E., Smith, J. D. T., et al. 2019, ApJ, 887, 105

(ref: daCunha2008MagphysPaper) da Cunha, E., Charlot, S., & Elbaz, D. 2008, MNRAS, 388, 1595

(ref: daCunha2015HighZMagphysALESS) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110

(ref: Daddi2015COexciation) Daddi, E., Dannerbauer, H., Liu, D., et al. 2015, A&A, 577, A46

(ref: Dahle2016SunburstArcDiscovery) Dahle, H., Aghanim, N., Guennou, L., et al. 2016, A&A, 590, L4

(ref: Dai2020AsymmetricBrightnessJ1226Arc) Dai, L., Kaurov, A. A., Sharon, K., et al. 2020, MNRAS, 495, 3192

(ref: Dale2014DustTemplate) Dale, D. A., Helou, G., Magdis, G. E., et al. 2014, ApJ, 784, 83

(ref: Danielson2011StarformingGalaxyAtRedshift2) Danielson, A. L. R., Swinbank, A. M., Smail, I., et al. 2011, MNRAS, 410, 1687

(ref: Darvish2018GasScalingRelations) Darvish, B., Scoville, N. Z., Martin, C., et al. 2018, ApJ, 860, 111

(ref: Dave2012EquilibriumModelAnalytical) Davé, R., Finlator, K., & Oppenheimer, B. D. 2012, MNRAS, 421, 98

(ref: Decarli2020ASPECSMultiBandLineLuminosityAndGasDensity) Decarli, R., Aravena, M., Boogaard, L., et al. 2020, ApJ, 902, 110

(ref: Decarli2019ASPECS-CO-LF) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138

(ref: Dekel2009ColdModeAccretion) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Denicolo2002MetallicityCalibration) Denicoló, G., Terlevich, R., & Terlevich, E. 2002, MNRAS, 330, 69

(ref: Dessauges-Zavadsky2019CosmicSnake) Dessauges-Zavadsky, M., Richard, J., Combes, F., et al. 2019, Nature Astronomy, 3, 1115

(ref: DessaugesZavadsky2017MolGasLensedCaseStudy) Dessauges-Zavadsky, M., Zamojski, M., Rujopakarn, W., et al. 2017, A&A, 605, A81

(ref: DessaugesZavadsky2015MolGasLensedSFGs) Dessauges-Zavadsky, M., Zamojski, M., Schaerer, D., et al. 2015, A&A, 577, A50

(ref: Draine2007Dust) Draine, B. T., Dale, D. A., Bendo, G., et al. 2007, ApJ, 663, 866

(ref: Dudzeviciute2020AS2UDS) Dudzevičiūtė, U., Smail, I., Swinbank, A. M., et al. 2020, MNRAS, 494, 3828

(ref: Dunne2000SLUGS) Dunne, L., Eales, S., Edmunds, M., et al. 2000, MNRAS, 315, 115

(ref: Eales2012DustEmissionAsMassProbe) Eales, S., Smith, M. W. L., Auld, R., et al. 2012, ApJ, 761, 168

(ref: Fischer2019outflowJ0033) Fischer, T. C., Rigby, J. R., Mahler, G., et al. 2019, ApJ, 875, 102

(ref: ForsterShreiberAndWuyts2020CosmicNoonSFReview) Förster Schreiber, N. M. & Wuyts, S. 2020, ARA&A, 58, 661

(ref: Fujimoto2017DancingALMA1) Fujimoto, S., Ouchi, M., Shibuya, T., & Nagai, H. 2017, ApJ, 850, 83

(ref: GaiaCollaboration2018Release2) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: Genzel2012MetallicityCOtoH2) Genzel, R., Tacconi, L. J., Combes, F., et al. 2012, ApJ, 746, 69

(ref: Genzel2015DustAndCOscalingRelations) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, ApJ, 800, 20

(ref: GloverAndClark2012StarFormationInMetalPoorGas) Glover, S. C. O. & Clark, P. C. 2012, MNRAS, 426, 377

(ref: GnedinAndDraine2014SelfShieldingMolecularHydrogen) Gnedin, N. Y. & Draine, B. T. 2014, ApJ, 795, 37

(ref: Gonzalez-Lopez2017LensedMolGasInRCS0327) González-López, J., Barrientos, L. F., Gladders, M. D., et al. 2017a, ApJL, 846, L22

(ref: Gonzalez-Lopez2017ALMA-FFat1.1mm) González-López, J., Bauer, F. E., Aravena, M., et al. 2017b, A&A, 608, A138

(ref: Gonzalez-Lopez2019ASPECS-COLineScanAnd3mm) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139

(ref: Grenier2005DarkGasSolarNeighborhood) Grenier, I. A., Casandjian, J.-M., & Terrier, R. 2005, Science, 307, 1292

(ref: Heintz&Watson2020CItoH2) Heintz, K. E. & Watson, D. 2020, ApJL, 889, L7

(ref: Hennawi2008SGAS1) Hennawi, J. F., Gladders, M. D., Oguri, M., et al. 2008, AJ, 135, 664

(ref: Hezaveh2013ALMA-SPT) Hezaveh, Y. D., Marrone, D. P., Fassnacht, C. D., et al. 2013, ApJ, 767, 132

(ref: Hodge&daCunha2020Review) Hodge, J. A. & da Cunha, E. 2020, Royal Society Open Science, 7, 200556

(ref: Hodge2015ResolvedGN20) Hodge, J. A., Riechers, D., Decarli, R., et al. 2015, ApJL, 798, L18

(ref: Hunter2007MatplotlibPaper) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: Iguchi2009AtacamaCompactArray) Iguchi, S., Morita, K.-I., Sugimoto, M., et al. 2009, PASJ, 61, 1

(ref: Inami20202StacksAspecsCO) Inami, H., Decarli, R., Walter, F., et al. 2020, ApJ, 902, 113

(ref: Inoue2011NebularTemplates) Inoue, A. K. 2011, MNRAS, 415, 2920

(ref: Ivezic2019LSST) Ivezić, Ž., Kahn, S. M., Tyson, J. A., et al. 2019, ApJ, 873, 111

(ref: Jullo&Kneib2009LensTool) Jullo, E. & Kneib, J. P. 2009, MNRAS, 395, 1319

(ref: Kaasinen2020DustSizeAndKinematicsThreeASPECSgxs) Kaasinen, M., Walter, F., Novak, M., et al. 2020, ApJ, 899, 37

(ref: KennicuttAndEvans2012ReviewSFLocalUniverse) Kennicutt, R. C. & Evans, N. J. 2012, ARA&A, 50, 531

(ref: Khullar2021COOLLAMPSBrightestLensedGalaxy) Khullar, G., Gozman, K., Lin, J. J., et al. 2021, ApJ, 906, 107

(ref: Kirkpatrick2019COEmissionAGN) Kirkpatrick, A., Sharon, C., Keller, E., & Pope, A. 2019, ApJ, 879, 41

(ref: Koester2010ArcJ1226Discovery) Koester, B. P., Gladders, M. D., Hennawi, J. F., et al. 2010, ApJL, 723, L73

(ref: Kubo2010SGAS) Kubo, J. M., Allam, S. S., Drabek, E., et al. 2010, ApJL, 724, L137

(ref: Laporte2017ALMA-FFphotometry1.1mm) Laporte, N., Bauer, F. E., Troncoso-Iribarren, P., et al. 2017, A&A, 604, A132

(ref: Laureijs2011EuclidDefinition) Laureijs, R., Amiaux, J., Arduini, S., et al. 2011, arXiv e-prints, arXiv:1110.3193

(ref: Leroy2011COtoH2) Leroy, A. K., Bolatto, A., Gordon, K., et al. 2011, ApJ, 737, 12

(ref: Li&Draine2001DustISM) Li, A. & Draine, B. T. 2001, ApJ, 554, 778

(ref: Lilly2013GasRegulation) Lilly, S. J., Carollo, C. M., Pipino, A., Renzini, A., & Peng, Y. 2013, ApJ, 772, 119

(ref: Liu2019A3COSMOScoldGasEvolution) Liu, D., Schinnerer, E., Groves, B., et al. 2019, ApJ, 887, 235

(ref: Livermore2012NonDetectionGasRedshift5) Livermore, R. C., Swinbank, A. M., Smail, I., et al. 2012, ApJL, 758, L35

(ref: Madau&Dickinson2014Review) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Madden2020TotalMolecularGasDark) Madden, S. C., Cormier, D., Hony, S., et al. 2020, A&A, 643, A141

(ref: Magdis2012EvolvingISMatRedshiftTwo) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, ApJ, 760, 6

(ref: Magnelli2020ASPECSDustAndGasDensity) Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66

(ref: McCully2018AstroScrappy) McCully, C., Crawford, S., Kovacs, G., et al. 2018, Astropy/Astroscrappy: V1.0.5 Zenodo Release

(ref: McGaugh1991MetallicityR23) McGaugh, S. S. 1991, ApJ, 380, 140

(ref: McKeeAndOstriker2007TheoryOfSF) McKee, C. F. & Ostriker, E. C. 2007, ARA&A, 45, 565

(ref: McMullin2007CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Messias2014HATLAS-J1429Merger) Messias, H., Afonso, J. M., Salvato, M., Mobasher, B., & Hopkins, A. M. 2014, A&A, 562, A144

(ref: Miettinen2017AlmaCosmosSED) Miettinen, O., Delvecchio, I., Smolčić, V., et al. 2017, A&A, 606, A17

(ref: Mitchell2013StellarMassSystematics) Mitchell, P. D., Lacey, C. G., Baugh, C. M., & Cole, S. 2013, MNRAS, 435, 87

(ref: Mortensen2021ScoopArctomoJ1226) Mortensen, K., Keerthi Vasan, G. C., Jones, T., et al. 2021, ApJ, 914, 92

(ref: Narayanan2010FormationOfSMGs) Narayanan, D., Hayward, C. C., Cox, T. J., et al. 2010, MNRAS, 401, 1613

(ref: PapadopoulosAndGreve2004CIasGasTracer) Papadopoulos, P. P., Thi, W. F., & Viti, S. 2004, MNRAS, 351, 147

(ref: PettiniAndPagel2004Metallicity) Pettini, M. & Pagel, B. E. J. 2004, MNRAS, 348, L59

(ref: Popping2017CIandCOatZ2) Popping, G., Decarli, R., Man, A. W. S., et al. 2017, A&A, 602, A11

(ref: Raney2020FrontierFieldsLensingUncertainties) Raney, C. A., Keeton, C. R., Brennan, S., & Fan, H. 2020, MNRAS, 494, 4771

(ref: Remy-Ruyer2014GasToDustLocalGalaxies) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2014, A&A, 563, A31

(ref: RemyRuyer2013DwarfGalaxySurveyPhotometry) Rémy-Ruyer, A., Madden, S. C., Galliano, F., et al. 2013, A&A, 557, A95

(ref: Rigby2018MegaSauraI) Rigby, J. R., Bayliss, M. B., Sharon, K., et al. 2018, AJ, 155, 104

(ref: Rivera-Thorsen2019SunburstArcEscapeFractions) Rivera-Thorsen, T. E., Dahle, H., Chisholm, J., et al. 2019, Science, 366, 738

(ref: Rivera-Thorsen2017SunburstArcLymanEscape) Rivera-Thorsen, T. E., Dahle, H., Gronke, M., et al. 2017, A&A, 608, L4

(ref: Rizzo2020ColdDiskSPT) Rizzo, F., Vegetti, S., Powell, D., et al. 2020, Nature, 584, 201

(ref: Rybak2021UltrafaintLensedCII) Rybak, M., da Cunha, E., Groves, B., et al. 2021, ApJ, 909, 130

(ref: Rybak2020FullOfOrions) Rybak, M., Hodge, J. A., Vegetti, S., et al. 2020, MNRAS, 494, 5542

(ref: Rybak2015SDP.81Continuum) Rybak, M., McKean, J. P., Vegetti, S., Andreani, P., & White, S. D. M. 2015a, MNRAS, 451, L40

(ref: Rybak2015SDP.81EmissionLine) Rybak, M., Vegetti, S., McKean, J. P., Andreani, P., & White, S. D. M. 2015b, MNRAS, 453, L26

(ref: Saintonge2011xCOLDGASSp1) Saintonge, A., Kauffmann, G., Kramer, C., et al. 2011, MNRAS, 415, 32

(ref: Saintonge2013MolGasLensedGalaxies) Saintonge, A., Lutz, D., Genzel, R., et al. 2013, ApJ, 778, 2

(ref: Sandstrom2013AlphaCOandGDRLocal) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Schinnerer2016GasFractionAndDepletion) Schinnerer, E., Groves, B., Sargent, M. T., et al. 2016, ApJ, 833, 112

(ref: Schreiber2015MainSequence) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, A&A, 575, A74

(ref: Schruba2012LowCOLuminosityDwarfs) Schruba, A., Leroy, A. K., Walter, F., et al. 2012, AJ, 143, 138

(ref: Scoville2014DustEmissionAsGasProbeEvolution) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84

(ref: Scoville2017EvolutionISM) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150

(ref: Scoville2016MainSequenceAndGasMass) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83

(ref: Sharon2013MappingCOinLensedSMG) Sharon, C. E., Baker, A. J., Harris, A. I., & Thomson, A. P. 2013, ApJ, 765, 6

(ref: Sharon2019MolGasLensedJ0901) Sharon, C. E., Tagore, A. S., Baker, A. J., et al. 2019, ApJ, 879, 52

(ref: Sharon2020ClusterLensModelsSGAS) Sharon, K., Bayliss, M. B., Dahle, H., et al. 2020, ApJS, 247, 12

(ref: Smail1997SubmmSurveyOfLensingClusters) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5

(ref: Spergel2015RomanReport) Spergel, D., Gehrels, N., Baltay, C., et al. 2015, arXiv e-prints, arXiv:1503.03757

(ref: Spilker2016ALMALensModelsForSPT) Spilker, J. S., Marrone, D. P., Aravena, M., et al. 2016, ApJ, 826, 112

(ref: Spingola2020SHARP6ExtendedCOLensed) Spingola, C., McKean, J. P., Vegetti, S., et al. 2020, MNRAS, 495, 2387

(ref: Stark2013CassowaryLensedSample) Stark, D. P., Auger, M., Belokurov, V., et al. 2013, MNRAS, 436, 1040

(ref: Swinbank2015ResolvedALMADiskAtz3) Swinbank, A. M., Dye, S., Nightingale, J. W., et al. 2015, ApJL, 806, L17

(ref: Tacconi2018PHIBSS2MainSequence) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, ApJ, 853, 179

(ref: Tacconi2020EvolutionISMReview) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, ARA&A, 58, 157

(ref: Tacconi2013PHIBSS1) Tacconi, L. J., Neri, R., Genzel, R., et al. 2013, ApJ, 768, 74

(ref: Tejos2021ArctomoJ1226Kinematic) Tejos, N., López, S., Ledoux, C., et al. 2021, MNRAS, 507, 663

(ref: Tremonti2004MassMetallicityRelation) Tremonti, C. A., Heckman, T. M., Kauffmann, G., et al. 2004, ApJ, 613, 898

(ref: Valentino2018SurveyOfAtomicCarbon) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, ApJ, 869, 27

(ref: Vanzella2021SunburstArcClusterFormationEfficiency) Vanzella, E., Castellano, M., Bergamini, P., et al. 2021, arXiv e-prints, arXiv:2106.10280

(ref: Vanzella2020BowenFluoresenceSunburstArc) Vanzella, E., Meneghetti, M., Pastorello, A., et al. 2020, MNRAS, 499, L67

(ref: Walter2020EvolutionOfBaryons) Walter, F., Carilli, C., Neeleman, M., et al. 2020, ApJ, 902, 111

(ref: Waskom2020Seaborn) Waskom, M., Gelbart, M., Botvinnik, O., et al. 2020, mwaskom/seaborn: v0.11.1 (December 2020)

(ref: Weiss2005AtomicCarbon) Weiß, A., Downes, D., Henkel, C., & Walter, F. 2005, A&A, 429, L25

(ref: Weiss2003GasAndDustCloverleaf) Weiß, A., Henkel, C., Downes, D., & Walter, F. 2003, A&A, 409, L41

(ref: Whitaker2014MainSequence) Whitaker, K. E., Franx, M., Leja, J., et al. 2014, ApJ, 795, 104

(ref: Wit2012StatsModelUncertainty) Wit, E., Heuvel, E. v. d., & Romeijn, J.-W. 2012, Statistica Neerlandica, 66, 217

(ref: Wolfire2010DarkMolGas) Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191

(ref: Wuyts2012StellarPopsLensed) Wuyts, E., Rigby, J. R., Gladders, M. D., et al. 2012, ApJ, 745, 86

# Stellar $Z$ as a proxy of gas-phase metallicity

The scaling relations for $\alpha_\text{CO}$ or $\delta_\text{GDR}$ are calibrated against gas-phase metallicity (parameterized as the oxygen abundance, $12 + \log(\text{O/H})$), which is obtained via rest-frame optical nebular line ratio indicators such as N2, O3N2 (\[N II\]$\lambda 6584$/H$\alpha$ and \[O III\]$\lambda 5007$/H$\beta$/N2 respectively, (cite: PettiniAndPagel2004Metallicity)) or $R_{23}$ ((\[O II\]$\lambda 3727$ + \[O III\]$\lambda\lambda 4959,5007$)/H$\beta$, (cite: McGaugh1991MetallicityR23)). At the redshifts considered here, these lines can only be accessed through near-infrared bands. In the case of SGASJ1226, H$\alpha$ is shifted outside the atmospheric NIR window and hence can only be observed from space. Nevertheless, (cite: Wuyts2012StellarPopsLensed) presented a Keck NIRSPEC spectrum of SGASJ1226 in which \[O II\]$\lambda 3727$, \[O III\]$\lambda\lambda 4959, 5007$ and H$\beta$ were successfully identified and the reported fluxes were later used by (cite: Saintonge2013MolGasLensedGalaxies) to infer $12+\log(\text{O/H})=8.27\pm0.19$ based on the $R_{23}$ index. For the Sunburst Arc, ESO X-Shooter NIR spectra was presented in (cite: Vanzella2020BowenFluoresenceSunburstArc), but without reporting any metallicity indicator nor individual line fluxes. Finally, as we already mentioned in the text, SGASJ0033 was observed with the SINFONI instrument on the VLT by (cite: Fischer2019outflowJ0033), who measured the flux of several diagnostic lines but also excluded an estimate of metallicity. In summary, the rest-frame optical spectrum of our sample has already been explored, but the diversity of instruments and the lack of consistent metallicity indicators prevent us from using gas-phase oxygen abundances in the $\alpha_\text{CO}, \delta_\text{GDR}$ or X~\[CI\]~ recipes.

Fortunately, the high quality MegaSaura spectra permitted (cite: Chisholm2019MegaSauraMetallicity) to fit STARBURST99 single stellar population models and infer ages and stellar metallicities. Here we used the latter as a proxy of gas-phase metallicity, as pointed out in Sect. [3.5](#sec:gas_mass), so we can compare three values determined in a uniform way from the same instrument. The rationale behind this choice is that, due to the young age of the UV-bright population accessible in the $\sim$1200 Å–3000 Å rest-frame range, the fitted stellar metallicity is likely equal to the gas-phase metallicity. This hypothesis was already tested by (cite: Chisholm2019MegaSauraMetallicity), who found a tight agreement between these two metallicities for the subset of MegaSaura galaxies which had both measurements available. To further validate the star-gas metallicity equivalence, we performed an additional test: taking SGASJ0033 as a benchmark, we used the published (narrow) line fluxes to infer oxygen abundance form the N2 and O3N2 indicators and compare to both stellar metallicities reported by (cite: Chisholm2019MegaSauraMetallicity), namely $Z_\text{SB99}^{\star}$ and $Z_\text{BPASS}^{\star}$.

We obtained the reddening-corrected narrow line fluxes from Table 1 of (cite: Fischer2019outflowJ0033). These measurements correspond to the central $\ang{;;0.5}\times\ang{;;0.5}$ region of the SGASJ0033 arc, but we do not expect significant AGN contamination since the two-component analysis presented in their Figure 4 predicts the narrow component to be well within the star formation dominated region of the (cite: Baldwin1981BPTpaper) diagram (BPT). We computed the N2 and O3N2 indices and converted them to oxygen abundance using the (cite: PettiniAndPagel2004Metallicity) calibration. The results are shown in Table [2](#tab:metal_j0033), where all metallicity indicators displayed in the second column are consistent within 0.2 dex.

| Method | $12 + \log\text{(O/H)}$ | $\alpha_\text{CO}$$^{a}$ | $\delta_\text{GDR}$$^{b}$ | $X_\text{[C I]}^{c}\times10^5$ |
|:---|:--:|:--:|:--:|:--:|
| $Z^{\star}_\text{SB99}$ | $8.59\pm 0.02$$^{d}$ | $4.5\pm 0.1$ | $117 \pm 5$ | 1.3 ± 0.8 |
| $Z^{\star}_\text{BPASS}$ | $8.54\pm 0.02$$^{d}$ | $4.8 \pm 0.1$ | $129 \pm 5$ | 1.2 ± 0.7 |
| N2~PP04~ | $8.65 \pm 0.10$$^{e}$ | $4.3 \pm 0.4$ | $104 \pm 20$ | 1.5 ± 1.0 |
| O3N2~PP04~ | $8.45 \pm 0.10$$^{e}$ | $5.3\pm 0.7$ | $154 \pm 30$ | 0.9 ± 0.6 |
| MZR~G12~ | $8.54\pm0.20$ | $4.8\pm 1.1$ | $129 \pm 40$ | 1.2 ± 0.9 |

: Different metallicity indicators for SGASJ0033 and their effect in gas tracer conversion factors

Table notes:

[^1]: <https://casa.nrao.edu/>

[^2]: <https://archive.stsci.edu/>

[^3]: <https://www.cv.nrao.edu/php/splat/>

[^4]: <http://www.astropy.org>

[^5]: <https://ascl.net/1910.003>

</paper>

Write the methods card for this paper.