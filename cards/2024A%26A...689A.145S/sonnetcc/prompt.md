# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...689A.145S\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...689A.145S",
 "title": "The ALMA-CRISTAL survey: Discovery of a 15 kpc-long gas plume in a z = 4.54 Lyman-α blob",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Solimano, M.",
 "n_authors": 28,
 "arxiv_id": "2401.04919",
 "doi": "10.1051/0004-6361/202449192",
 "alma_projects_linked_by_archive": [
  "2012.1.00978.S",
  "2017.1.00428.L",
  "2019.1.01587.S",
  "2021.1.00280.L"
 ]
}
```

Paper text:
<paper>
# The ALMA-CRISTAL survey

# Introduction

The multiphase gas envelope around galaxies, known as the circumgalactic medium (cite: Tumlinson2017CircumgalacticMediumReview), plays a major role in galaxy growth and evolution. In particular, its cool phase ($T\lesssim \SI{1e4}{\kelvin}$) hosts the gas reservoirs needed to fuel star formation and supermassive black hole accretion. The regulation of these activities requires cool gas to be transported in and out of the interstellar medium (ISM), in what is called the baryon cycle (cite: PerouxHowk2020CosmicBaryonAndMetalCycles), a process where the CGM is the main stage. For example, the CGM is the site where galactic scale outflows expand into (cite: Veilleux2020CoolOutflowsReview), and where narrow, cold accretion streams flow into galaxies (cite: Dekel2009ColdModeAccretion).

Observationally, cool CGM gas manifests in several ways. For example, it is routinely detected as H i and/or metal absorption against the backlight of distant quasars at any redshift (cite: Werk2013CosHalos; ZhuAndMenard2013SdssMgiiAbsorbers; Turner2014MetalLineAbsorptionKeck). In recent years, high metallicity ($[\mathrm{M}/\mathrm{H}]\approx-1$), high column density ($N_\mathrm{H} \gtrsim \SI{2e20}{\per\centi\meter\squared}$) absorbers at $z\gtrsim4$ have been found at distances as large as 15  –45   from their host galaxies (cite: Neeleman2017CiiFromDlaHost; Neeleman2019CiiEmissionFromHighzDLAs), further away than similar galaxy-absorber pairs at low redshift. These results suggest that at high redshift, the cool CGM was particularly gas-rich.

Additional evidence comes from the diffuse H i Lyman-$\alpha$ (Ly$\alpha$) emission that surrounds almost every star-forming galaxy at $z\gtrsim2$, with exponential scale lengths of 1  –10   for individual systems (cite: Wisotzki2016ExtendedLyaHalosMUSE; Leclerq2017MuseHudfLyaHaloes; Claeyssens2022LlamasPaper1) and up to 100   for the so-called Ly$\alpha$“blobs” (cite: Francis1996LyaGroup; LeFevre1996ClusteringAroundRadioGalaxy; Steidel2000LyaProtoCluster; Venemans2002ProtoclusterRedshiftFour; Matsuda2004SubaruLyaBlobs), which often host several galaxies, but not necessarily AGN (cite: Geach2009LabsPoweredByHeating). Given the intrinsic complexities in interpreting the resonant, and highly dust-sensitive Ly$\alpha$ line, the origins of extended Ly$\alpha$ emission are still unclear. However, most of the proposed scenarios involve the presence of neutral hydrogen clouds in the CGM (cite: Ouchi2020LymanAlphaReview).

Moving away from the challenges of Ly$\alpha$, deep (sub)millimeter observations have revealed extended gas reservoirs of colder gas around high-$z$ galaxies in a variety of environments. For example, several studies report extended CO and/or \[C i\] emission around $z\approx2$ protocluster cores (cite: Emonts2014CoSurveyHighzRGs; Emonts2015CoRichMergerDragonfly; Emonts2016MolGasClusterHighZ; Emonts2018SpiderwebCircumgalacticCi; Emonts2019ColdCgmMammoth1; Ginolfi2017Molecular; Frayer2018MassiveMolecularComponentSmg; Li2021OutflowAndColdHaloQso; Umehata2021CiiObsOfLAB1; Cicone2021GiantMolecHaloRedshiftTwo). At even higher redshifts, the \[C ii\] 158 μm line becomes easily observable from the ground, and in the past decade it has proven very efficient at tracing extended gas in both extremely active (cite: Carniani2013ExtendedCiiComplexMerger; Cicone2015ExtendedHaloQso; Ginolfi2020AlpineMergerTidal) and normal, less massive systems (cite: Fujimoto2019CiiHalos; Fujimoto2020AlpineHalos; HerreraCamus2021OutflowHZ4; Akins2022ExtendedCoolGasOutflowRedshift7; Lambert2023CiiHaloAroundHz7). In particular, (cite: Fujimoto2020AlpineHalos) finds that roughly 30% of massive, isolated main sequence galaxies at $4<z<6$ display 10  -scale “\[C ii\] halos”, defined as the cases where significant \[C ii\] emission is detected at 10   from the source while the UV and far infrared (FIR) emission are not. Similar objects have been reported with deeper, higher angular resolution Atacama Large Millimeter/Submillimeter Array (ALMA) observations than those used by (cite: Fujimoto2020AlpineHalos) (cite: HerreraCamus2021OutflowHZ4; Lambert2023CiiHaloAroundHz7). In all of these cases, however, the origin of extended \[C ii\] line emission remains unclear.

In dense regions, tidal interactions, cold accretion, outflows and AGN feedback seem to contribute to the presence of extended \[C ii\] line emission. In contrast, star-formation-driven outflows are often quoted as the most likely origin of extended \[C ii\] emission around individual and more isolated UV-bright galaxies (cite: Fujimoto2020AlpineHalos; HerreraCamus2021OutflowHZ4; Pizzati2020OutflowsCiiHaloes; Pizzati2023CiiHaloesSmokingGun). However, confirming and understanding extended \[C ii\] emission at high redshift requires deeper and higher angular resolution ALMA observations.

CRISTAL stands for “\[C ii\] Resolved ISm in STar-forming galaxies with ALma” (Herrera-Camus et al. in prep.), and is an ALMA Cycle 8 Large Program that observed the \[C ii\] line and dust continuum emission of 19 main-sequence, star-forming galaxies at $4 < z < 6$ with a $\sim \ang{;;0.2}$ resolution. CRISTAL builds on top of the highly successful ALPINE survey (cite: LeFevre2020AlpineSurveyDesign), which conducted a wider census of \[C ii\] and dust at $\approx \ang{;;1}$ resolution in the COSMOS and GOODS-S fields. Out of the 75 \[C ii\]-detected galaxies in the ALPINE sample (cite: Bethermin2020DataProcessing), and based on the multiwavelength properties presented by (cite: Faisst2020AlpineMultiWavelength), CRISTAL selected 19 sources that (1) have a specific SFR within a factor of 3 of the star-forming main sequence at their corresponding redshift; (2) have HST imaging available; and (3) have a stellar mass larger than $\log\left(M_\mathrm{star}/\mathrm{M}_\odot\right)\geq 9.5$. In addition, six sources from the ALMA archive that met the selection criteria were added to the sample, hence the total size of the sample is 25. The survey is designed to unveil detailed kinematics, search for resolved outflows, constrain ISM excitation and also probe extended emission.

Since the CRISTAL program targets the massive end of its parent sample, it is not surprising that many of them show clear signs of multiplicity or interaction (e.g., Ikeda et al. in prep, Lee et al. in prep., Posses et al. in prep.). Among them, CRISTAL-01 stands out due to its proximity ($\sim$1.6″) to the well-known sub-millimeter galaxy at $z=4.54$ (cite: Capak2008ExtremeStarburst; Aretxaga2011AztecSurveyCosmos). Here, we present new ALMA observations of this system and report the discovery of a puzzling \[C ii\]-emitting gas plume that extends from the center of the system.

The paper is organized as follows: in Sec. [2](#sec:backstory) we give an overview of the literature on this particular system. Sec. [3](#sec:data) describes the observations and reduction of the new ALMA dataset and the ancillary VLT/MUSE and HST data. In Sec. [4](#sec:results) we detail the analysis steps and present the results characterizing the \[C ii\] plume. Next, in Sec. [5](#sec:discussion) we explore different physical scenarios that could give rise to the observed emission. Finally, Sec. [6](#sec:conclusions) closes with a summary and the main conclusions.

Throughout the paper, we adopt a flat $\Lambda$CDM cosmology with $H_0=\SI{70}{\kilo\meter\per\second\per\mega\parsec}$ and $\Omega_{m,0}=0.3$. Under this assumption, 1 ″ corresponds to 6.57   of proper physical scale at $z=4.54$. When relevant, we adopted a (cite: Chabrier2003IMF) initial stellar mass function (IMF).

# The J1000+0234 system

+------------------------------------------------------------------+------------------------------------+----------------------------------+
| Property                                                         | J1000+0234-North                   | CRISTAL-01a                      |
+:================================================================:+:=======================:+:========:+:=======================:+:======:+
| 2-5                                                              | Value                   | Ref.     | Value                   | Ref.   |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| redshift                                                         | 4.5391                  | 1        | 4.5537                  | 2      |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| $\log\left(M_\mathrm{stars}\right)\,[\si{M\ensuremath{_\odot}}]$ | 10.14 ± 0.08            | 3        | 9.16 ± 0.07             | 3      |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| $\log\left(M_\mathrm{dyn}\right)\,[\si{M\ensuremath{_\odot}}]$   | 11.15 ± 0.19            | 1        | \-                      | \-     |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| UV slope $(\beta_\mathrm{UV})$                                   | $-1.01_{-0.32}^{+0.39}$ | 3        | $-2.04_{-0.11}^{+0.12}$ | 3      |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| SFR$_\mathrm{UV}$ \[M $_\odot$ ^−1^\]                            | 52.6 ± 8.5              | 3        | 147.6 ± 7.4             | 3      |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| SFR$_\mathrm{IR}$ \[M $_\odot$ ^−1^\]                            | $440_{-320}^{+1200}$    | 3        | 56 ± 35$^{a}$           | \-     |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+
| SFR$_\mathrm{tot}$ \[M $_\odot$ ^−1^\]                           | $490_{-320}^{+1200}$    | 3        | 204 ± 35                | \-     |
+------------------------------------------------------------------+-------------------------+----------+-------------------------+--------+

: Global properties of the two main galaxies in the J1000+0234 system.

Table notes:

In this paper, we study the core region of the J1000+0234 system at $z=4.54$, first reported by (cite: Capak2008ExtremeStarburst) as a bright sub-millimeter source with an associated Ly$\alpha$ blob. This region (see Fig. [1](#fig:maps)) hosts two highly star-forming galaxies within $\approx \SI{20}{\kilo\parsec}$ in projection (cite: GomezGuijarro2018AlmaMinorMergersSmgs). It is embedded in a larger scale overdensity of galaxies (cite: Smolcic2017SmgEnvironments; Loiacono2021AlpineCiiLf), and possibly linked to the PCI J1001+0220 protocluster (cite: Lemaux2018VudsProtoCluster). One of the central galaxies, previously known as J1000+0234-South but hereafter called CRISTAL-01a, contributes $\approx$75% of the total the rest-frame UV emission of the pair, and belongs to the sample of Lyman-break galaxies (LBGs) targeted by both the ALPINE and CRISTAL surveys. The other galaxy, J1000+0234-North, lies merely 1.6″ from CRISTAL-01a and accounts for all of the observed submillimeter flux ($S_{\SI{870}{\micro\meter}} = \SI{7.8+-0.2}{\milli\jansky}$; ) and most of the stellar mass ($\approx \SI{2e10}{M\ensuremath{_\odot}}$; e.g., (cite: Schinnerer2008MolGasMajorMerger); ). Hereafter, we will also refer to it as “the DSFG” (dusty star-forming galaxy). The global properties of each galaxy are extracted from the literature and listed in Table [1](#tab:glob_tab).

Multiple follow-up studies have targeted J1000+0234 as one of the brightest and most extreme non-quasar systems known at $z\gtrsim4$. Until recently, the general picture depcits CRISTAL-01a and the DSFG undergoing a merger event, which potentially drives the elevated SFRs ((cite: Capak2008ExtremeStarburst; Schinnerer2008MolGasMajorMerger; Smolcic2015PhysicalPropertiesSmgsCosmos); ). Yet ALMA observations of the \[C ii\] line later revealed that the DSFG rotates fast at $V_\mathrm{rot}\approx\SI{500}{\kilo\meter\per\second}$ with $V/\sigma \gtrsim 9$, suggesting a dynamically cold gas component (cite: Jones2017DynamicsTiltedRingSmgs; Fraternali2021FastRotators). In other words, the merger is either not massive enough or has not had time to dynamically disrupt the internal kinematics of the DSFG. This is consistent with SED models that put the stellar mass ratio between CRISTAL-01a and the DSFG at $\sim$1:10 .

Current Chandra pointings do not detect X-rays from J1000+0234, putting an upper limit on luminosity of about 1.3 × 10^43^  s^−1^ in the 0.5-2 keV band (cite: Smolcic2015PhysicalPropertiesSmgsCosmos). This value is considerably higher than the 1 × 10^42^  s^−1^ traditional threshold for AGN identification (cite: Szokoly2004Cdfs). Moreover the DSFG’s radio emission is weak (cite: Carilli2008RadioLbgs), and consistent with the infrared-radio correlation (cite: Smolcic2015PhysicalPropertiesSmgsCosmos). However, (cite: Jimenez-Andrade2023LyaNebulaeGalaxyPair) recently obtained VLT/MUSE observations of J1000+0234, that yielded not only a very high fidelity 3D IFU map of the LAB in which J1000+0234 is embedded, but also the detection of spatially extended C iv and He ii emission. The authors argue that the high C iv/Ly$\alpha$ and He ii/Ly$\alpha$ ratios can be explained by the presence of an AGN in the DSFG. While this claim still needs confirmation, provided a first view of the complex CGM of J1000+0234, as well as spectroscopic evidence for the overdensity, after identifying five Ly$\alpha$ emitters within the MUSE field of view ($1\times1\,\mathrm{arcmin}^2$).

In parallel to the studies focusing on the massive DSFG, CRISTAL-01a was independently targeted by the ALMA ALPINE survey of \[C ii\] emission in bright LBGs (cite: LeFevre2020AlpineSurveyDesign). A successful detection of the line provided the first systemic redshift of this source at $z=4.5537$ (cite: Bethermin2020DataProcessing), closely matching the previously reported Ly$\alpha$ redshift (cite: Hasinger2018DeimosCosmos). In the next section, we describe the high-angular resolution ALMA observations obtained by CRISTAL, along with the rest of the observations used in this article.

# Observations & data reduction

## ALMA

We use CASA (cite: CasaTeam2022CasaRefPaper) to combine ALMA observations of the redshifted \[C ii\] 158 μm line targeting J1000+0234 from three different programs, namely the ALPINE survey (cite: LeFevre2020AlpineSurveyDesign), the CRISTAL survey (Herrera-Camus et al. in prep.), and an archival dataset from project 2019.1.01587.S (PI: F. Lelli). The ALPINE observations were carried out with the most compact configuration (C43-1), tuned to cover the line at 349.1 GHz with a velocity resolution of 40 km s^−1^ and a natural weighting beam size of $\SI{1.25}{\arcsecond}\times\SI{0.78}{\arcsecond}$ (cite: Bethermin2020DataProcessing). The CRISTAL data, on the other hand, include deeper integrations in two antenna configurations, namely C43-1 and C43-4, and with a higher spectral resolution (10 km s^−1^ per channel) than that of the ALPINE data. These observations were designed to resolve the \[C ii\] emission with a beam of $\sim$0.25 ″, equivalent to 1.65   at $z = 4.54$. Finally, the 2019.1.01587.S dataset was observed using a longer baseline configuration (C43-6), providing a nominal resolution of 0.06″. However, the spectral windows were tuned around the DSFG’s rest-frame velocity, so the frequency overlap with previous data is partial and only covers the red half of CRISTAL-01a’s emission line. We do not include data from the Cycle 2 program 2012.1.00978.S (cite: Jones2017DynamicsTiltedRingSmgs; Fraternali2021FastRotators) into the combined dataset, because its shallower depth plus the complexities of weighting data that was processed with old versions of the pipeline[^1] would have resulted in a marginal improvement.

In addition, thanks to the brightness of the DSFG we performed self-calibration on the continuum visibilities of both ALPINE and CRISTAL datasets before combination. This was done in two “phase-only” rounds for each observation, the first one combining spectral windows and scans, and the second one only the scans (of average length $\approx\SI{180}{\second}$). This process resulted in a $\approx$11% decrease in continuum rms and the mitigation of patchy patterns in the noise.

Finally, the self-calibrated and combined measurement sets were processed with CRISTAL’s reduction pipeline as described in Herrera-Camus et al. (in prep.). Briefly, it starts by subtracting the continuum on the visibility space using CASA’s `uvcontsub` task. After that, it runs `tclean` with automasking multiple times, producing cubes with different weightings and channel widths. In all cases the data are cleaned down to $1\sigma$. In this paper, we use datacubes with 20 km s^−1^ channel width and either natural or Briggs (`robust=0.5`) weighting.

Since the data combines different array configurations, it is important to measure and apply the “JvM” correction (cite: JorsaterAndvonMoorsel1995BarredSpiralHI). We do this by following the method of (cite: Czekala2021JvMGuidelines). This correction takes into account the significant deviations from Gaussianity that the core of the dirty beam can have in multi-array observations and ensures that both the convolved CLEAN model and the residuals have compatible units. While the CRISTAL pipeline provides JvM-corrected products, it uses a single correction factor per spectral window. Since we combine multiple datasets from different projects, the uv coverage has significant variations within a spectral window. For this reason, we compute and apply the correction in channel ranges with similar beam properties. We find a mean multiplicative correction factor of $\epsilon\approx 0.37$ in the channels covering the \[C ii\] line emission when using Briggs weighting, and $\epsilon\approx0.31$ when using natural weighting.

## MUSE

We retrieved observations of the J1000+0234 field from the ESO archive taken with the Multi Unit Spectroscopic Explorer (MUSE) instrument mounted on the Very Large Telescope (UT4-Yepun) using ground-layer adaptive optics and the Wide Field Mode. These observations, comprising 16 exposures of 900 s (total 4 h), were taken as part of ESO GTO programs 0102.A-0448 (PI: S. Lilly) and 0103.A-0272 (PI: S. Cantalupo) under good weather conditions with average seeing of 0.9 ″ and airmass below 1.4. Here we use an independent reduction from that of , but we refer the reader to their work for further details about the observations.

The standard calibrations and procedures are performed using the MUSE pipeline (cite: Weilbacher2020MUSE_DPP) within the ESO Recipe Execution Tool (EsoRex) environment (cite: ESO2015CPL). The wavelength solution is set to vacuum. We then apply the Zurich Atmosphere Purge (cite: Soto2016ZAP) post-processing tool to further remove sky line residuals. As described by , half of the exposures were affected by intra-dome light contamination, resulting in excess counts between 8000 Å and 9000 Å. We decided to use all the exposures in the combined datacube regardless, since the issue does not affect wavelengths near the Ly$\alpha$ emission at 6742 Å. We then follow the steps described in (cite: Solimano2022LymanAlphaSGASJ1226) to scale the variance cube and match the observed noise levels. Finally, we apply a simple 2D translation to the WCS to match the positions of the two Gaia DR2 (cite: GaiaCollaboration2018Release2) sources in the field. We check the alignment of the cube with respect to HST by producing pseudo broadband image from the ACS/F814W filter curve. Matching sources in the MUSE pseudo-F814W image and the ACS/F814W image yield an astrometric rms of 220 mas, or about one MUSE pixel.

The resulting datacube yields a $1\sigma$ noise level of $\approx$1 × 10^−19^  s cm^2^ $''$^−−−2^ per spectral layer around 6750 Å, computed from randomly placed apertures of 1 $''$^2^ area. The datacube is sampled at pixel scale 0.2″ and spectral layers have a width of 1.25 Å. We fit a Moffat profile to an $r=19\,\mathrm{mag}$ G-type star in the field and find a point spread function (PSF) FWHM of 0.6″ around 6750 Å. At this wavelength, the instrument yields a resolving power of $R=\num{2538}$.

## HST

We retrieved from MAST[^2] all the available HST data for the J1000+0234 field. We found observations in the ACS/F606W, ACS/F814W, WFC3/F105W, WFC3/F125W and WFC3/F160W bands, covering 1000 Å–3200 Å in the rest-frame at $z=4.54$. Images were processed using the standard pipeline, co-added and aligned to Gaia DR2 (cite: GaiaCollaboration2018Release2). All images were then drizzled with a square kernel and a pixel fraction of 0.5 using the ASTRODRIZZLE routine from DRIZZLEPAC (cite: Stsci2012DrizzlePac; Hack2021DrizzlePacv3), executed within the GRIZLI pipeline (cite: Brammer2021GrizliSoftware). ACS images were drizzled to a common pixel size of 0.03″ while for WFC3/IR images we used a pixel size of 0.06″.

![](figures/moments.pdf)

# Results & Analysis

## Adaptive masking of datacubes

Extracting the total flux and spatial extent of the different types of emission considered here, requires taking into account the contributions of faint and diffuse components. Now, given the complexity and spatial variations of the Ly$\alpha$ and \[C ii\] profiles in the J1000+0234 system, a simple pseudo-narrowband “collapse” around the line will hide narrow and low surface brightness (SB) features below the noise level. Instead, we adopt an adaptive approach based on the “matched filtering” technique. This involves creating a 3D mask that takes into account the line morphology. For the MUSE data, we used the off-the-shelf software LSDCAT (cite: Herenz2017LsdCat), while for the ALMA cubes we used a custom script.

LSDCAT works by building an optimized S/N detection derived from the cross-correlation of the data with a template signal. Here, we first removed the continuum emission by running a median filter over the spectral axis across the full wavelength range of the cube, using the default window width of 151 spectral pixels (188.75 Å). This step yields a continuum-only datacube which is then subtracted from the original cube. The next step is optimized for our blind search of Ly$\alpha$ emitters in the cube, but it also performs well on enhancing the low SB features. The results of our search and the subsequent characterization of the detected objects will be presented in a separate paper.

Following (cite: Herenz2017LsdCat) we built our template as a point-like source with a Gaussian spectral profile of $\mathrm{FWHM}=\SI{250}{\kilo\meter\per\second}$, a choice that maximizes sensitivity to faint and compact line emitters. After convolving the continuum-subtracted cube by the PSF (spatial filter), we convolved the resulting cube with a 250 km s^−1^ Gaussian kernel (spectral filter) to construct the 3D matched filter output. We took into account the wavelength dependence of the PSF by fitting 2D Moffat profiles to an isolated bright star in the original cube, using 20 wavelength bins. We simultaneously fit the Moffat parameters’ dependence on wavelength using 3^rd^ and 2^nd^ order polynomials, for the FWHM and power index parameters, respectively. These polynomials were then used to interpolate the PSF to all the channels of the cube. Then, we computed the detection S/N cube as the voxel-by-voxel ratio between the filtered datacube and the square root of the propagated variances.

Finally, we selected all voxels with $\mathrm{S/N}\geq 2$ between 6729 Å and 6776 Å (equivalent to a velocity range of \[−947 km s^−1^, 1135 km s^−1^\]). To refine the selection, we exclude spaxels in which less than three voxels are above the S/N threshold. Furthermore, we create a 2D mask of the spaxels that satisfy these conditions and subsequently prune the regions with less than 55 connected spaxels. We find that this number successfully masks any remaining spurious signal. After we remove the corresponding voxels, we apply the resulting 3D mask to the data, and integrate along the wavelength axis. The result is shown in Fig. [1](#fig:maps)a as filled contours overlaid on top of an HST image. We recover an irregular and extended Ly$\alpha$ morphology down to 1 × 10^−18^  s cm^2^ $''$^−−−2^, in agreement with . The highest SB emission is centered on CRISTAL-01a, but extends to a secondary peak $\sim\ang{;;1.5}$ to the southwest.

We applied a similar procedure to the \[C ii\] cube. Starting from the naturally-weighted cube binned in 20 km s^−1^ channels, we convolved with a $\sigma=\SI{30}{\kilo\meter\per\second}$ Gaussian kernel along the velocity axis, and a $\sigma=\ang{;;0.1}$ 2D Gaussian kernel in the spatial axes. We then measured the rms in the signal-free regions of the convolved cube. Finally, we split cells above and below a $2\times\mathrm{rms}$ threshold into a 3D mask, which we then fed to CASA task `immoments` to obtain the intensity, velocity, and velocity dispersion maps from the original cube (as shown from panels b to d in Fig. [1](#fig:maps)).

This approach recovers the bright \[C ii\] emission from the DSFG but also reveals faint and extended emission in CRISTAL-01a, and most notably, in a 2.4″-long plume extending north of the DSFG. We note, however, that this elongated diffuse emission was already apparent in the individual channels of our cubes, as will be discussed in Sec. [4.3](#sec:results:cii_spectral). The intensity map spans more than two orders of magnitude in SB, from 0.01  km s ^−−1^ (outermost contour in Fig. [1](#fig:maps)b-d) to 2.5  km s ^−−1^ at the center of the DSFG, equivalent to 5 × 10^5^  ^−1^ ^2^ and 1.25 × 10^8^  ^−1^ ^2^ respectively at $z=4.54$. If we take the \[C ii\] SB as a tracer of SFR surface density, according to the local $\Sigma_\mathrm{[CII]}-\Sigma_\mathrm{SFR}$ relation (cite: HerreraCamus2015CiiAsSfrTracerKingFish), the lower limit would correspond to $\Sigma_\mathrm{SFR}=\SI{0.01}{M\ensuremath{_\odot}\per\year\per\kilo\parsec\squared}$, which is well within the regime of normal star-forming galaxies in the Local Universe from the KINGFISH sample (cite: Kennicutt2011KingfishSample).

In the velocity space, significant \[C ii\] emission spans from −500 km s^−1^ to 850 km s^−1^ across smooth gradients (see Fig. [1](#fig:maps)c). The main gradient goes along the major axis of the DSFG, as previously found by (cite: Jones2017DynamicsTiltedRingSmgs) and (cite: Fraternali2021FastRotators). Interestingly, the plume displays a gradient along its long axis, with a mild increase in velocity as one moves away from the DSFG. While the plume meets the DSFG in the approaching side, the velocity of the plume overlaps with that of the receding side of the DSFG. Finally, CRISTAL-01a’s \[C ii\] emission is centered at $v\approx\SI{800}{\kilo\meter\per\second}$, and shows a more irregular gradient approximately aligned with the minor axis.

The velocity dispersion (Fig. [1](#fig:maps)d), on the other hand, is largest at the center of the DSFG, with the other structures showing low values ($\sigma \lesssim \SI{100}{\kilo\meter\per\second}$) and little to no variation.

## Parametric morphology

In this section we study the morphological parameters of the two galaxies, CRISTAL-01a and the DSFG, in the J1000+0234 system. To this end, we make use of 2D light profile modeling code PYAUTOGALAXY (cite: Nightingale2023PyAutoGalaxy) built on top of the PYAUTOFIT (cite: Nightingale2021PyAutoFit) probabilistic programming framework. While PYAUTOGALAXY is capable of directly fitting the interferometric visibilities, in this paper we used the image-based fitter for a faster workflow. We account for the noise correlation in the images by feeding the full covariance matrix into the calculation of the likelihood. The covariance matrix is estimated in source-free regions of the image using the method and the code[^3] presented by (cite: Tsukui2022CorrelatedNoiseInterferometry).

We start by modeling the DSFG, which shows a regular and almost symmetric shape. For this reason, we choose to fit a single 2D Sérsic profile (cite: Sersic1968AtlasdeGalaxias), with a total of seven free parameters.

We performed two independent fits. One for the rest-frame 160 μm continuum map shown in panel b of Fig. [1](#fig:maps), and the other for the \[C ii\] integrated intensity map. However, we refrained from using the adaptive intensity map, since the noise properties are not well defined after the masking procedure. Instead, we used regular, unmasked intensity maps integrated within a given velocity range. For the DSFG, we integrated between 342.293 GHz and 344.006 GHz, corresponding to a bandwidth of 1492.7 km s^−1^. For the center coordinates and the effective radius, we adopted broad Gaussian priors centered on previously published values (cite: Fraternali2021FastRotators). For the intensity parameter we adopted a uniform prior between 0 and the maximum surface brightness of the image. Finally, based on previous work that characterized this source as a disk (cite: Jones2017DynamicsTiltedRingSmgs), we adopt a Gaussian prior for the Sérsic index centered at $n=1$ (exponential disk) with a $\sigma=1$, but allowed $n$ to vary between 0.2 and 10.

The parameter space was explored using the DYNESTY (cite: Speagle2020Dynesty; Koposov2022DynestyZenodoV203) nested sampler backend with 50 live points. Table [2](#tab:dsfg_param) lists the results of fitting with the parameters values and uncertainties drawn from the Bayesian posterior probability distribution.

+-------------------------------+----------------------------------------------------------------------+
| Property                      | Value                                                                |
+:==============================+:====================================================================:+
| *160 μm continuum*                                                                                   |
+-------------------------------+----------------------------------------------------------------------+
| Center (RA)                   | $10^\mathrm{h}00^\mathrm{m}54.49129^\mathrm{s}\pm0.00002^\mathrm{s}$ |
+-------------------------------+----------------------------------------------------------------------+
| Center (Dec.)                 | $\ang{+02;34;36.120}\,\pm\,\ang{;;0.0002}$                           |
+-------------------------------+----------------------------------------------------------------------+
| $R_\mathrm{eff}$ \[pkpc\]     | 0.740 ± 0.003                                                        |
+-------------------------------+----------------------------------------------------------------------+
| Sérsic index ($n$)            | 1.29 ± 0.01                                                          |
+-------------------------------+----------------------------------------------------------------------+
| Axis ratio (minor/major)      | 0.400 ± 0.002                                                        |
+-------------------------------+----------------------------------------------------------------------+
| Flux density \[ \]            | 8.03 ± 0.03                                                          |
+-------------------------------+----------------------------------------------------------------------+
| PA \[degrees\]                | 57.8 ± 0.1                                                           |
+-------------------------------+----------------------------------------------------------------------+
| *\[C ii\] emisison*                                                                                  |
+-------------------------------+----------------------------------------------------------------------+
| Center (RA)                   | $10^\mathrm{h}00^\mathrm{m}54.4904^\mathrm{s}\pm0.0003^\mathrm{s}$   |
+-------------------------------+----------------------------------------------------------------------+
| Center (Dec.)                 | $\ang{+02;34;36.140}\,\pm\,\ang{;;0.005}$                            |
+-------------------------------+----------------------------------------------------------------------+
| $R_\mathrm{eff}$ \[pkpc\]     | 1.13 ± 0.04                                                          |
+-------------------------------+----------------------------------------------------------------------+
| Sérsic index ($n$)            | 0.71 ± 0.08                                                          |
+-------------------------------+----------------------------------------------------------------------+
| Axis ratio (minor/major)      | 0.34 ± 0.01                                                          |
+-------------------------------+----------------------------------------------------------------------+
| Integrated flux \[ km s^−1^\] | 7.8 ± 0.3                                                            |
+-------------------------------+----------------------------------------------------------------------+
| PA \[degrees\]                | 57.4 ± 0.8                                                           |
+-------------------------------+----------------------------------------------------------------------+

: Results of the parametric 2D fitting of exponential profiles to the 160 μm continuum and \[C ii\] line maps of the DSFG.

Table notes: Radii are circularized and given in physical kiloparsecs (pkpc).

Our analysis reveals that the \[C ii\] and dust morphologies are slightly different in the DSFG. The effective radius of the gas component is approximately 1.5 times larger than that of the dust, while the axis ratio is smaller. However, since the Sérsic indices and the S/N are not equal between \[C ii\] line and 160 μm continuum, we refrain from claiming the gas is more extended than the dust. Assuming instead that the dust and gas both have disk-like geometries, share the same inclination, and are optically thin, the difference in axis ratio suggests that the dust component is thicker in the polar direction relative to the gas component. The higher Sérsic index also indicates that dust is more centrally concentrated, yet the residual continuum map shows significant features that extend beyond the central region and do not follow axial symmetry (see middle row of Fig. [2](#fig:residuals)).

Next, we move to CRISTAL-01a and fit only the \[C ii\] emission, since the continuum was not detected. We construct the unmasked intensity map by integrating the cube between 342.088 GHz and 342.454 GHz, which encloses only 85% of the total line flux but maximizes the S/N of the map. The source clearly breaks into two subcomponents, resembling the rest-frame UV morphology, albeit offset $\approx$0.3″ to the Southwest. We thus model the emission with two independent profiles, an elliptical 2D Sérsic for the brighter component (hereafter SW clump) and a circular Gaussian profile for the fainter component (hereafter NE clump). This model has a total of 11 free parameters. For the SW clump we use the same prior on the Sérsic index as before. For the rest of the quantities we use either broad uniform or Gaussian priors covering reasonable limits in the parameter space.

![](figures/alma_sersic2d_residuals.pdf)

The best-fit parameters and uncertainties from this fit are listed in Table [3](#tab:c1a_param). The right panel of Fig. [2](#fig:residuals) shows the 2D residuals. Notably, the SW clump alone has twice the effective radius of the DSFG’s \[C ii\] emission and more than three times the radius of its dust emission. This size is comparable to previous measurements performed on the F814W imaging (cite: Fujimoto2020AlpineHalos). If we were to associate the \[C ii\] clumps to the two UV clumps seen by HST, we notice the brightness order is inverted. The SW clump’s \[C ii\] line flux density is about ten times that of than the NE clump. Yet in the UV, the NE clump is brighter. This discrepancy could be attributed to differences in dust attenuation. In fact, provided maps of the rest-frame UV $\beta_\mathrm{UV}$ slope based on the HST imaging, and they show that the southern part of CRISTAL-01a is slightly redder ($\beta_\mathrm{UV}\approx-2.0$) than the northern part ($\beta_\mathrm{UV}\approx-2.2$).

+-----------------------------------------+------------------------------------------------------------------+
| Property                                | Value                                                            |
+:========================================+:================================================================:+
| *SW clump*                                                                                                 |
+-----------------------------------------+------------------------------------------------------------------+
| Center (RA)                             | $10^\mathrm{h}00^\mathrm{m}54.505^\mathrm{s}\pm0.003^\mathrm{s}$ |
+-----------------------------------------+------------------------------------------------------------------+
| Center (Dec.)                           | $\ang{+02;34;34.34}\,\pm\,\ang{;;0.02}$                          |
+-----------------------------------------+------------------------------------------------------------------+
| $R_\mathrm{eff}$ \[pkpc\]               | 2.4 ± 0.4                                                        |
+-----------------------------------------+------------------------------------------------------------------+
| Sérsic index ($n$)                      | 1.0 ± 0.3                                                        |
+-----------------------------------------+------------------------------------------------------------------+
| Axis ratio (minor/major)                | 0.82 ± 0.09                                                      |
+-----------------------------------------+------------------------------------------------------------------+
| Integrated flux \[ km s^−1^\]           | 0.39 ± 0.08                                                      |
+-----------------------------------------+------------------------------------------------------------------+
| PA \[degrees\]                          | 175 ± 45                                                         |
+-----------------------------------------+------------------------------------------------------------------+
| *NE clump*                                                                                                 |
+-----------------------------------------+------------------------------------------------------------------+
| Center (RA)                             | $10^\mathrm{h}00^\mathrm{m}54.537^\mathrm{s}\pm0.02^\mathrm{s}$  |
+-----------------------------------------+------------------------------------------------------------------+
| Center (Dec.)                           | $\ang{+02;34;34.75}\,\pm\,\ang{;;0.03}$                          |
+-----------------------------------------+------------------------------------------------------------------+
| $R_\mathrm{eff}$ \[pkpc\]               | 0.8 ± 0.3                                                        |
+-----------------------------------------+------------------------------------------------------------------+
| Integrated flux \[ km s^−1^\]           | 0.03 ± 0.02                                                      |
+-----------------------------------------+------------------------------------------------------------------+
| Total flux$^{a}$ (SW + NE)\[ km s^−1^\] | 0.5 ± 0.2                                                        |
+-----------------------------------------+------------------------------------------------------------------+
| Centroid separation \[arcsec\]          | 0.63 ± 0.06                                                      |
+-----------------------------------------+------------------------------------------------------------------+

: Results of the parametric 2D fitting to the \[C ii\] line map of CRISTAL-01a.

Table notes: The table separates the fitted parameters for each clump. Radii are circularized and given in physical kiloparsec (pkpc).

## Spectral properties of the \[C II\]-emitting plume

While the adaptive masking scheme described in Sect. [4.1](#sec:results:masking) helped us identify all the \[C ii\] signal present in the cube and unveil the general kinematic trends, the noise properties of the masked maps in Fig. [1](#fig:maps) remain undefined. Moreover, since our data display a large dynamic range in both surface brightness and velocity dispersion, the details of the plume are partly outshined by the DSFG. In order to get a clearer picture of the plume, Fig. [3](#fig:channel-maps) displays eight consecutive channel maps of 40 km s^−1^ width, covering from 200 km s^−1^ to 480 km s^−1^ relative to the systemic velocity of the DSFG.

![](figures/tidal_tail_channel_maps.pdf)

The limits of the colormap in Fig. [3](#fig:channel-maps) were chosen to highlight the faint extended emission and to give a visual reference of the noise amplitude. On top of it, we show contours at different levels of statistical significance. All eight channel maps exhibit large patches of $\geq 3\sigma$ emission distributed between 0.2″ and 2.5″ northward from the DSFG kinematic center (purple cross). In the first row of panels we can see that the plume grows longer at higher velocities, reaching a maximum isophotal extent of $\approx \ang{;;2.1} = \SI{13.8}{\kilo\parsec}$ at 360 km s^−1^ (bottom left panel). In the subsequent channels, the plume becomes fainter and clumpy in appearance, possibly due to the lower S/N. We note that the DSFG centroid shifts coherently to the southeast as a result of rotation.

We now want to quantify the spatial variations of the spectral profile along the plume with a proper treatment of the noise. To this end, we place six adjacent rectangular $\ang{;;0.4}\times\ang{;;0.9}$ apertures covering the full extent of the plume as seen in Fig. [4](#fig:radial_tail), oriented with a position angle of 14° east of north. We extract the spectra from the Briggs-weighted (robust=0.5) datacube without continuum subtraction. With this weighting, the synthesized beam ($\ang{;;0.25}\times\ang{;;0.23}$) fits comfortably within each aperture, making them independent.

We then fit each extracted spectrum independently with a single 1D Gaussian, except for the first two apertures, where we include a first-order polynomial to model the continuum from the DSFG. In these apertures we also mask emission from −700 km s^−1^ to 0 km s^−1^ to avoid contamination from the approaching side of the DSFG.

Once again, we use PYAUTOFIT with the DYNESTY (cite: Speagle2020Dynesty; Koposov2022DynestyZenodoV203) static nested sampler as a backend. We assume a Gaussian likelihood for the sum of the rms-weighted residuals (data minus model). For every channel (of width 20 km s^−1^), we measure the rms as the $3\sigma-$clipped standard deviation of the flux densities of 300 random apertures with the same size and orientation as the extraction apertures. We adopt uniform priors for the three fitted parameters, namely the velocity center between −200 km s^−1^ and 1000 km s^−1^; the FWHM between 60 and 1000 km s^−1^; and the total flux between 0 and 1.0  km s^−1^.

Figure [4](#fig:radial_tail) and Table [\[tab:radial_values\]](#tab:radial_values) show the results of these fits as a function of the distance of each aperture from the center of the DSFG. We recognize radial trends in all the three parameters, and a large gap between apertures #1 and #2. This apparent discontinuity could be due to additional contamination in aperture #1’s spectrum at positive velocities. For this reason, we subtract a velocity-inverted spectrum from an aperture that mirrors aperture #1 by the projected rotation axis (dashed line Fig. [4](#fig:radial_tail)) and repeat the fit. After this correction, we find both lower fluxes and FWHM, but a consistent central velocity, as shown by the white-filled markers in Fig. [4](#fig:radial_tail). These differences illustrate the systematic uncertainties associated with aperture #1, that make flux and FWHM less reliable.

Regardless of which fit we consider for the first aperture, we identify a radially decreasing trend for the flux density (or surface brightness). From 5   to 15   the flux drops almost exponantially, with an excess at $\approx$13  . Summing apertures from #2 to #6 yields a total flux of 0.50 ± 0.04  km s^−1^, which closely matches CRISTAL-01a’s total flux (Table [3](#tab:c1a_param)) and amounts to a \[C ii\] luminosity of 3.1 ± 0.25 × 10^8^. Adding aperture #1 will raise this number by a factor of 2.53 under the original fitting scheme, and by a factor of 1.61 with the corrected fit.

In the middle panel of the left row we can see a decrease in the line width as one moves further out in the plume. Starting from $400-600\,\si{\kilo\meter\per\second}$ at 2.5  , the plume narrows down to $180_{-38}^{+64}\,\si{\kilo\meter\per\second}$ in the outermost aperture. We note that at low S/N the fits tend to bias the FWHM to larger values, hence the intrinsic FWHMs of the outermost bins might be even lower than depicted here.

Our aperture-based measurements recover the velocity gradient that we had seen in the velocity map in Fig. [1](#fig:maps)c. Here, both methods to extract the spectrum of aperture #1 yield consistent central velocities at $v_\mathrm{cen}\approx\SI{180}{\kilo\meter\per\second}$. The next aperture (#2) is already at 300 km s^−1^, suggesting a steep velocity gradient between apertures #1 and #2. In the subsequent apertures, the increase in velocity is less abrupt, going from $\approx \SI{300}{\kilo\meter\per\second}$ to $\approx \SI{400}{\kilo\meter\per\second}$ in the outer 10  .

In addition, we create custom intensity maps for each aperture, integrating over a velocity window of size 1.1 times the best-fit spectral FWHM for maximal S/N. On these maps we obtain 1D spatial profiles along the long side of the corresponding aperture, but extended to $\pm\SI{3}{\ensuremath{''}}$. We then fit a Gaussian to these profiles to obtain the transversal (spatial) FWHM of the plume. After deconvolving the beam width, we obtain FWHMs between 0.4″ and 0.8″ with an average of 0.6″, but no clear radial trend.

Finally, we put upper limits on the FIR luminosity surface density of each aperture based on the continuum depth. To this end, we randomly placed 600 rectangular apertures of size $\ang{;;0.9}\times\ang{;;0.4}$ on the rest-frame 160 μm, `robust=0.5` continuum map (without JvM correction). We obtain a distribution of flux densities with $\sigma-$clipped standard deviation of $\sigma=\SI{38.8}{\micro\jansky}$. Taking $5\sigma$ as the detection limit, we convert the flux density into FIR luminosity[^4] assuming an underlying $T_\mathrm{dust}=\SI{45}{\kelvin}$ modified blackbody dust SED, with a dust emissivity index $\beta_\mathrm{dust}=1.5$ (a choice that roughly describes the average SED of star-forming galaxies at $z>4$, e.g., (cite: Bethermin2020DataProcessing)). Such an SED gives the ratio $\nu L_\nu(\SI{158}{\micro\meter})/L_\mathrm{FIR} = 0.185$. After correcting for primary beam gain decrement, we quote the resulting limits in Table [\[tab:radial_values\]](#tab:radial_values), except for aperture #1 where emission from the DSFG dominates. We note, however, that these values depend on the assumed temperature. For example, choosing $T_\mathrm{dust}=\SI{55}{\kelvin}$ and $T_\mathrm{dust}=\SI{65}{\kelvin}$ produce $1.7\times$ and $2.4\times$ higher $L_\mathrm{FIR}$ limits, respectively. In any case, these measurements allow us to estimate the \[C ii\]/FIR diagnostic, which informs about the heating mechanism of the gas. At $T_\mathrm{dust}=\SI{45}{\kelvin}$ we obtain lower limits on the \[C ii\]/FIR ratio between $\approx$0.2% (aperture #6) and $\approx$0.6% (aperture #2). Unfortunately, these lower limits are not high enough to rule out UV photoelectric heating, characteristic of photodisocciation regions (PDRs; with typical \[C ii\]/FIR ratios between 0.01% and 2%, e.g., (cite: HerreraCamus2018Shining1)), in favor of other mechanisms such as shock heating ($\gtrsim 4\%$, e.g., (cite: Appleton2013ShockCiiSQ; Peterson2018TaffyCiiBridge)). Only at the coldest possible temperatures, $T_\mathrm{dust}\lesssim\SI{20}{\kelvin}$ ($T_\mathrm{CMB}=\SI{15}{\kelvin}$), the highest limit becomes \[C ii\]/FIR $>6.8\%$, and thus harder to explain with UV photoelectric heating alone.

![](figures/tail_radial_quantities.pdf)

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Aperture | Flux density | $v_\mathrm{cen}$ | FWHM | $\Sigma_\mathrm{[CII]}$ | ${\Sigma_\mathrm{FIR}}$$^{b}$ | $v_\mathrm{out}$ | $M_\mathrm{out}$ | $\dot{M}_\mathrm{out}$ |
| \# |  km s^−1^ | km s^−1^ | km s^−1^ | 1 × 10^6^  ^−1^ ^2^ | 1 × 10^10^  ^−1^ ^2^ | km s^−1^ | 1 × 10^7^ M $_\odot$ | M $_\odot$ ^−1^ |
| 1$^{a}$ | $0.27_{-0.03}^{+0.05}$ | $166_{-54}^{+31}$ | $454_{-81}^{+65}$ | $10.6_{-1.3}^{+2.1}$ | \- | 551 ± 75 | 25 ± 3 | 83 ± 18 |
| 2 | $0.18_{-0.02}^{+0.03}$ | $297_{-17}^{+19}$ | $377_{-59}^{+73}$ | $7.3_{-0.9}^{+1.0}$ | $<1.3$ | 617 ± 56 | 17 ± 2 | 64 ± 11 |
| 3 | $0.10_{-0.02}^{+0.02}$ | $318_{-23}^{+27}$ | $306_{-58}^{+86}$ | $4.0_{-0.7}^{+0.7}$ | $<1.3$ | 578 ± 66 | 9 ± 2 | 32 ± 7 |
| 4 | $0.08_{-0.01}^{+0.01}$ | $336_{-25}^{+17}$ | $228_{-42}^{+40}$ | $3.1_{-0.4}^{+0.5}$ | $<1.3$ | 530 ± 41 | 7 ± 1 | 23 ± 4 |
| 5 | $0.09_{-0.01}^{+0.01}$ | $379_{-18}^{+15}$ | $210_{-32}^{+36}$ | $3.5_{-0.6}^{+0.5}$ | $<1.3$ | 558 ± 33 | 8 ± 1 | 28 ± 4 |
| 6 | $0.05_{-0.01}^{+0.01}$ | $409_{-24}^{+27}$ | $180_{-38}^{+64}$ | $2.0_{-0.5}^{+0.5}$ | $<1.4$ | 561 ± 50 | 5 ± 1 | 16 ± 4 |

Table notes: From left to right, the columns display the aperture number, the flux density, the central line velocity, the FWHM, and the surface brigthness of \[C ii\] line emission, followed by the inferred maximum outflow velocity, gas mass, and mass outflow rates as described in Sec. [5.1](#sec:discussion:outflow).

# Discussion

The main question we want to answer in this paper is what caused the \[C ii\] plume in the J1000+0234 system. In this section we discuss possible scenarios such as outflows, inflows, ram pressure stripping, and tidal interactions.

## Conical outflow

A first hypothesis on the nature of the \[C ii\] plume is to interpret it as a collimated outflow launched by the DSFG, driven by stellar feedback, AGN activity, or both. The first case is compelling because the DSFG hosts a vigorous starburst in its center, which translates into a high rate of supernovae explosions that could potentially accelerate gas out of the galaxy. The theoretical and observational evidence suggests that starburst-driven outflows escape along the minor axis of disk galaxies, because it is the path of least resistance, leading to (bi-)conical structures that extend perpendicular to the disk, with M82 (cite: BlandAndTully1988BipolarWindM82) and NGC 1482 (cite: VeilleuxAndRupke2002GalacticWindNgc1482) being archetypal examples in the local Universe. In contrast, AGN-driven outflows do not show a preferential alignment with the host minor axis (cite: Schmitt2003ExtendedOiiiSeyferts; RuschelDutra2021AgnifsOutflows) and can have very narrow opening angles (cite: Sakamoto2014MergerWithMolecularOutflows; Aalto2020ResolvedMolecularJet).

In the J1000+0234 system, the \[C ii\] plume diverges from the DSFG’s minor axis by $\sim$40° clockwise, thus favoring an AGN origin. Furthermore, the plume width remains narrow (transversal FWHM of $\approx$0.6″, see Sec. [4.3](#sec:results:cii_spectral)) along its full extent, showing little to no broadening towards the top (North). In aperture #6 of Fig. [4](#fig:radial_tail), the transversal FWHM is 0.8″. Taking that as the opening of the cone at a distance of 2.4″ of its vertex at the center of the DSFG, we derive a projected angle of $\theta_\mathrm{p} = 2\arctan\left(0.4/2.4\right)\approx\ang{19}$, which is a projection of the true angle $\theta=2\times\arctan[\sin(i)\times\tan(\theta_\mathrm{p} / 2)]$. Using the expectation value for a random uniform distribution of inclination angles, $\left<\sin{i}\right>=0.79$ (see the derivation in (cite: Law2009HighRedshiftKinematics)), we estimate $\theta\approx\ang{15}$. This angle falls short of typical outflow opening angle observed in low redshift starbursts (cite: HjelmAndLindblad1996OutflowNgc1365; Veilleux2001BiconicalOutflowNgc2992; SeaquistAndClark2001CoInOutflowM82; Westmoquette2011SuperwindNgc253; Rubin2014EvidenceCollimatedOutflows) and in simulations (cite: Cooper2008ThreeDimSimWind; Nelson2019Tng50SimOutflows; Schneider2020SbDrivenOutflowsSim). This again favors AGN as the driver of the outflow, although a high gas density surrounding a central starburst can also lead to a strong collimation effect, especially in the molecular phase (cite: PereiraSantaella2016ExtendedMolecularOutflowLirg).

On a side note, the fact we see only one cone instead of a symmetric bi-cone could be explained by power source being located above the midplane of the disk. In that case, the outflow would need to be much stronger to blow out into the other side.

Since \[C ii\] is the only line available, the dominant gas phase producing the emission remains unknown. One possibility is that most of the \[C ii\] flux arises from a population of clumps of cold (molecular and/or atomic) gas entrained in the hot outflowing plasma, as illustrated in the upper left panel of Fig. [5](#fig:scenarios). Such arrangement of the cold medium is predicted by the theory (cite: Schneider2020SbDrivenOutflowsSim; Kim2020MultiphaseOutflowsTigress; FieldingAndBryan2022MultiphaseGalacticWinds) and validated by a large set of observations (cite: Shapley2003RestUvSpectraLbgs; Rubin2014EvidenceCollimatedOutflows; PereiraSantaella2016ExtendedMolecularOutflowLirg; PereiraSantaella2018SpatiallyResolvedOutflowsUlirgs). Yet only a few studies exist reporting \[C ii\] outflows at high-$z$. On one hand, high-velocity wings have been detected in individual (cite: HerreraCamus2021OutflowHZ4) and stacked spectra of main sequence galaxies (cite: Gallerani2018AlmaOutflowsRedshift5; Ginolfi2020AlpineOutflowsCGM), and QSO hosts (cite: Bischetti2019QsoCiiOutflows), but they usually come without any constraint on the state of the emitting gas. On the other hand, (cite: Spilker2020MolecularOutflowsSPT) showed that 7 out of a sample of 11 lensed DSFGs host unambiguous molecular outflow signatures in the form of blueshifted OH 119 μm absorption, yet none of these galaxies display broad \[C ii\] emission. These results led (cite: Spilker2020MolecularOutflowsSPT) to conclude that \[C ii\] line is an unreliable tracer of molecular outflows. Since the DSFG has similar intrinsic properties as the sources in the (cite: Spilker2020MolecularOutflowsSPT) sample, we argue that it is unlikely for \[C ii\] to be tracing molecular gas in the plume. Instead, the gas could be composed of mainly atomic hydrogen.

Alternatively, the emission is dominated by ionized ($T\gtrsim\SI{1e4}{\kelvin}$) gas and we are seeing the outflow cone walls from the side, similar to what optical nebular lines show in low-redshift edge-on outflows. When sufficient spatial resolution allows it, such cases exhibit a hallmark limb-brightening effect near the edges of the cone (cite: Strickland2004HighResXrayHalphaHotGasDisks; Westmoquette2011SuperwindNgc253; Venturi2017MagnumIonizedOutflows; Rupke2019AHundredKpcWindCgm; Herenz2023OutflowConeMetalPoor). Here, the plume is resolved in the transverse direction, but the S/N is too low to draw any conclusion about the structure. Nevertheless, detected C iv at the position of the DSFG, with a velocity shift comparable to what we measure in the plume ($\sim$300 km s^−1^). This would support the idea of a physical association of the \[C ii\] plume with warmer gas and hence a with a more energetic origin.

Regardless of the launching mechanism, we can now quantify some outflow properties based on the \[C ii\] line emission. In particular, we can estimate the mass of the plume enclosed in each of the apertures of Fig. [4](#fig:radial_tail) from the measured \[C ii\] fluxes. In the optically thin limit, and assuming negligible background emission, the gas mass in each aperture is $M_\mathrm{out}=\kappa_\mathrm{[CII]}\times L_\mathrm{[CII]}$, where the conversion factor $\kappa_\mathrm{[CII]}$ depends strongly on the temperature, density and carbon abundance of the gas. Following (cite: HerreraCamus2021OutflowHZ4), we assume the collisions are dominated by atomic hydrogen and adopt $\kappa_\mathrm{[CII]}=\SI{1.5}{M\ensuremath{_\odot}\per\lumsol}$ which corresponds to maximal excitation ($T\gg\SI{90}{\kelvin}$, $n\gg n_\mathrm{crit}\sim\SI{1e3}{\per\cubic\centi\meter}$), and solar abundance patterns. Since lower densities, temperatures and abundances yield higher values of $\kappa_\mathrm{[CII]}$, the masses we derive will effectively represent lower limits. For example, $\kappa_\mathrm{[CII]}$ becomes $3\times$ and $27\times$ larger when the metallicity drops to half solar, and one-tenth solar, respectively (cite: HerreraCamus2021OutflowHZ4).

In this way, we measure gas masses from 5 × 10^7^ M $_\odot$ in the outermost aperture (#6) to 2.5 × 10^8^ M $_\odot$ in the innermost aperture (#1, corrected by symmetric difference method). The sum of all the apertures gives 7.1 ± 0.4 × 10^8^ M $_\odot$. We now exploit the spectral information to derive mass outflow rates as $\dot{M}_\mathrm{out} = M_\mathrm{out}\times v_\mathrm{out} \times \tan{(i)} / R$, where $v_\mathrm{out}$ represents the projected maximum outflow velocity and $R=\SI{2.63}{\kilo\parsec}$ is the projected length of the aperture in the short side (parallel to the flow). For the maximum outflow velocity we use the prescription of (cite: Genzel2011SinsSurvey) for outflows detected as broad emission components with Gaussian profile width $\sigma_\mathrm{broad}$ and velocity offset of $\left|\Delta v\right|$ with respect to the narrow component: $v_\mathrm{out}=\left|\Delta v\right| + 2\sigma_\mathrm{broad}$. Since we only detect a single spectral component along the plume, we take $\left|\Delta v\right|=v_\mathrm{cen}$ as the velocity centroid relative to the DSFG’s systemic velocity. Both $v_\mathrm{out}$ and $M_\mathrm{out}$ values are listed in Table [\[tab:radial_values\]](#tab:radial_values).

Assuming $\left<i\right>=\ang{57.3}$, we obtain mass outflow rates between 15 M $_\odot$ ^−1^ and 85 M $_\odot$ ^−1^ (see last column of Table [\[tab:radial_values\]](#tab:radial_values)). At face value, such an outflow will take several hundreds of mega-years to deplete the DSFG’s gas reservoir of $\approx\SI{1e11}{M\ensuremath{_\odot}}$ (cite: Fraternali2021FastRotators), and hence it’s unlikely to quench the observed SFR anytime soon. We stress, however, that \[C ii\] conditions that differ from maximal excitation and solar abundance would drastically increase the inferred mass outflow rates.

Mass outflow rates in starburst-driven winds scale with the SFR, and typically share the same order of magnitude (cite: Veilleux2020CoolOutflowsReview). When taken as lower limits, our fiducial mass outflow rates are roughly consistent with the DSFG’s SFR given its large uncertainties.

Are these values consistent with AGN-driven outflows? Recalling that the X-ray luminosity of the DSFG is $L_\mathrm{2-10keV} < \SI{1.3e43}{\erg\per\second}$ (cite: Smolcic2015PhysicalPropertiesSmgsCosmos), we estimate a bolometric luminosity of $L_\mathrm{bol} < \SI{1.3e44}{\erg\per\second}$ assuming a bolometric correction of 10, appropriate for low-luminosity broad line AGN (cite: VasudevanAndFabian2007BolCorrAGN). According to the AGN wind scaling relations presented by (cite: Fiore2017AgnWindScaling), our adopted $L_\mathrm{bol}$ upper limit allows for molecular outflows with mass outflow rates of up to 100 M $_\odot$ ^−1^ and maximum velocities of $\approx\SI{400}{\kilo\meter\per\second}$. In contrast, ionized outflows yield mass outflow rates of $\lesssim \SI{0.1}{M\ensuremath{_\odot}\per\year}$. In summary, our mass outflow rates are consistent with the scaling relations for molecular outflows in both starbursts and AGN.

The main caveat of the outflow interpretation is that it struggles to explain the kinematic structure of the \[C ii\] plume. Specifically, most spatially resolved observations of galactic-scale outflows find a high velocity dispersion (FWHM $\gtrsim \SI{600}{\kilo\meter\per\second}$) with a flat, if not increasing, radial profile (cite: Venturi2018MagnumNgc1365; Bao2019XshapedBicone; McPherson2023DuvetOutflowsMrk1486). This is also true in idealized high-resolution simulations such as the one presented by (cite: Schneider2020SbDrivenOutflowsSim), since outflows that start as laminar, low-turbulence flows can develop and maintain instabilities as they interact with the CGM, thus increasing the velocity dispersion. These examples contrast with our measurement of radially decreasing line widths (middle panel of left row in Fig. [4](#fig:radial_tail)). Also, if the emission is optically thin, the dispersion must increase with radius because the volume of the cone slice probed by the beam gets bigger, and thus includes a larger range of projected kinematic components. In other words, the dispersion should increase due to beam smearing even if the turbulence remains low.

In conclusion, the outflow scenario is a natural explanation for the observed \[C ii\] plume, as it fits some of the expected properties an outflow would have given the nature of the DSFG. Future observations will be essential to rule out or confirm this scenario. For example, upcoming JWST/NIRSpec IFU observations will tell if there is any broad H$\alpha$ emission–tracer of ionized gas and a better-established indicator of outflows–associated with the \[C ii\] plume. In addition, deep rest-frame UV spectroscopy is needed to probe absorption by low-ionization metal species against the UV-bright regions of the system. Blueshifted lines will then unambiguously confirm the presence of cold outflows.

## Gas accretion

We now consider a different possibility: the \[C ii\] plume traces a filament of inflowing gas. Cosmological simulations have long predicted that massive halos at high-$z$ can be fed by narrow streams of cold gas, provided that the cooling timescale is shorter than the free-fall time (cite: DekelAndBirnboim2006ColdFlowsShockHeating). Moreover, if the galaxy at the center is a rotating disk, it is expected that such streams reach the ISM along its minor axis. If the accretion is co-rotating with the disk, the disk structure is reinforced, whereas in the opposite case the disk might be disrupted (cite: Danovich2015AngularMomentumBuildUp).

As pointed out in Sec. [4.1](#sec:results:masking), the plume meets the DSFG at the receding end of the rotation, although it appears to overlap with the opposite side in the intensity map. This configuration resembles what could be observed in an accreting filament along the edge of a disk. Such interpretation would explain the relatively low-velocity dispersion, since cold streams are protected from virial shocks.

In cosmological hydrodynamical simulations, cold gas flows in with a speed comparable to the virial velocity, and the speed is approximately uniform along the filaments (cite: GoerdtAndCeverino2015InflowVelocitiesColdStreams). Following the estimation of (cite: Fraternali2021FastRotators) for the J1000+0234 system, we assume a virial mass of $M_\mathrm{vir}=\SI{2e12}{M\ensuremath{_\odot}}$ and virial radius of $R_\mathrm{vir}=\SI{70}{\kilo\parsec}$, yielding a virial velocity of $V_\mathrm{vir}=\sqrt{M_\mathrm{vir}G/R_\mathrm{vir}}\approx\SI{350}{\kilo\meter\per\second}$. (cite: GoerdtAndCeverino2015InflowVelocitiesColdStreams) found that halos of similar mass at $z \sim 4$ accrete at $V_\mathrm{stream}\approx 0.9 V_\mathrm{vir}$, so for the DSFG we would expect $V_\mathrm{stream}=\SI{315}{\kilo\meter\per\second}$ which is excellent agreement with our measured \[C ii\] velocities at 5-10  . Now, since these velocities are projected into the line of sight, the actual transversal speed could be much higher, depending on the inclination of the stream. Using again the average inclination for a random distribution of viewing angles, $\left<\sin{i}\right>=0.79$, we obtain $v/\left<\sin{i}\right> \approx \SI{400}{\kilo\meter\per\second}$. This implies that the gas is moving faster than expected for a cold inflow stream. We caution, however, that (cite: GoerdtAndCeverino2015InflowVelocitiesColdStreams)’s simulations only track gas down to $0.2 R_\mathrm{vir}$, while the gas plume discussed here appears projected into smaller radii, from roughly zero to $0.2 R_\mathrm{vir}$, thus preventing a direct comparison.

If the gas retains or gradually loses angular momentum, it will follow a curved path as it falls. In that case, the observed velocity gradient can be due to a projection of a filament with relatively uniform gas inflow speed (cite: Rose2023Abell2390Plume). But we observe the plume being approximately straight, so either the curvature is parallel to the line-of-sight or the gas is truly following a straight path. The latter seems more likely since it does not require a special orientation. So, if we assume the gas is falling straight into the galaxy, the positive velocity gradient we observe implies the gas is slowing down. This is contrary to the expectation of a free fall, where the gas will accelerate towards the center of the potential, but it is a plausible hydrodynamic effect where the pressure in the immediate vicinity of the DSFG exerts a force against falling gas.

Since we detect the plume in \[C ii\], the gas cannot be pristine but must have a significant mixture of processed material, even if the exact amount is not possible to constrain with the data in hand. Enrichment can occur by mixing of the infalling gas with the metals already present in the CGM thanks to past outflow activity. Alternatively, the gas is being enriched by star-formation ocurring in-situ. In fact, cosmological simulations also predict that accretion streams carry dwarf galaxies and star-forming clumps into the central halos (cite: Dekel2009ColdModeAccretion; Ceverino2010HighzClumpyDisks; Fumagalli2011AbsorptionInSimulatedColdStreams; Mandelker2018ColdFilamentaryAccretion). This idea has been recently proposed to explain the 100   filament of gas that feeds the massive radio-galaxy 4C 41.17, detected via its \[C i\] emission (cite: Emonts2023CarbonCosmicStream). To test this scenario we stacked the HST images from the four WFC3-IR filters available to search for associated UV sources (see Appendix [8](#sec:appendixB)). We find two faint compact sources: one of them lies slightly outside the plume’s \[C ii\] footprint to the North, while the other falls within the footprint at the the Eastern edge of aperture #4, but only at S/N$\approx$3 (see Fig. [7](#fig:hst_stack)). For this reason, we deem it a tentative detection and refrain from claiming a physical association with the plume. Otherwise, we do not detect UV emission in the HST images at a stacked $5\sigma$ depth of 26.2  $''$^−2^. This corresponds to an unobscured SFR density limit of roughly 2.7 M $_\odot$  ^−−1^ ^2^, assuming the (cite: Kennicutt98SFR) prescription scaled to the (cite: Chabrier2003IMF) IMF.

Finally, a third possibility is that of gas recycling in a “galactic fountain”, this is, gas ejected by the DSFG falls back in. However, recycled gas in cosmological simulations typically rains down in the outer parts of the disk, rather than in a collimated stream onto the center (cite: AnglesAlcazar2017BaryonCycleInFIRE; Grand2019AccretionAndFountainFlowsInAuriga).

In summary, interpreting the \[C ii\] plume as a cold accretion filament is qualitatively sound, although it requires some mechanism to slow down the gas as it falls, and a significant degree of metal enrichment. Theoretical predictions for the behavior of cold streams in the inner part of halos (below $0.2R_\mathrm{vir}$) will enable stronger conclusions.

## Ram pressure stripping

In certain conditions, galaxies lose their ISM through hydrodynamic interactions with their environment. Whenever a galaxy encounters a dense medium at high relative velocity, it will experience a drag force arising from the ram pressure acting on its ISM gas. If the drag force exceeds that of gravity, the gas becomes unbound. Known as ram pressure stripping (cite: GunAndGott1972InfallClusters) this process is one of the main ways disk galaxies quench their star formation in galaxy clusters, but it can also be an efficient quenching mechanism for dwarf satellites around groups or individual massive galaxies (cite: Boselli2022RpsReview). RPS in action is responsible for the existence of “jellyfish” galaxies, identifiable by their one-sided tails of stripped gas (cite: Chung2009VirgoVlaAtomicGas; Bekki2009RpsInDiscs; Smith2010UvTailsClusters; Ebeling2014Jellyfish; Poggianti2017GaspI).

In this section we discuss a scenario where the extended \[C ii\] feature is one of such tails (see lower left panel of Fig. [5](#fig:scenarios)). Since the integrated \[C ii\] luminosity is comparable to that of the CRISTAL-01a galaxy, we could be seeing gas stripped from a galaxy with similar properties. In fact, the innermost tip of the feature closely matches the position of the UV-bright spot in the DSFG. While this light could be escaping through an opening in the dusty ISM of the DSFG (as suggested by its redder UV slope, $\beta_\mathrm{UV}\approx-1$; cf. Table [1](#tab:glob_tab)), we cannot rule out it belongs to a separate smaller galaxy currently orbiting the DSFG. In this interpretation, the UV-bright region plus the \[C ii\] tail would represent the farthest example yet of a jellyfish galaxy.

How realistic is this scenario? RPS needs special conditions to be effective. Since the drag force is proportional to the density and the square of the relative velocity (cite: GunAndGott1972InfallClusters), the medium has to be dense, volume-filling, and fast-moving. Galaxy clusters are thus the ideal environment for RPS, since they are filled with a hot dense plasma (the intracluster medium, ICM, e.g., (cite: Sarazin1986IntraclusterMedium)), and their huge gravitational potential allows members to acquire large orbital velocities. The J1000+0234 system is not a galaxy cluster, despite containing an excess number of LAEs and LBGs (cite: Smolcic2017SmgEnvironments; Jimenez-Andrade2023LyaNebulaeGalaxyPair). If anything, it could be classified as a protocluster, which means the structure is only loosely bound and cluster virialization has not happened yet (cite: Overzier2016ProtoclusterReview). Gas therefore has not reached the very high temperatures of typical clusters and is more likely dominated by small clouds and filaments of colder gas (cite: Hennawi2006ThickAbsorbersAroundQsos; Cantalupo2014CosmicWebFilament; ArrigoniBattaia2015CompactGasClumpsCgmQuasar). Nevertheless, reported extended He ii and C iv emission around the DSFG, with ratios (relative to Ly$\alpha$) that suggest strong ionization induced by AGN. The gas is then arguably warmer than $T=\SI{1e4}{\kelvin}$, increasing the cross section for a strong RPS interaction in a fast-passing satellite.

![](figures/scenarios_4panels.pdf)

Given the observed velocity difference $V$ between the DSFG and the base of the plume, we can estimate the minimum density the CGM must have in order to induce RPS. According to (cite: GunAndGott1972InfallClusters), the requirement of ram pressure force being larger than the force holding the ISM of the satellite translates into the criterion $$\begin{equation}
      \rho_\mathrm{CGM}V^2 > \frac{\Sigma_\mathrm{gas}v_\mathrm{rot}^2}{R_\mathrm{gal}},
  
\end{equation}$$ where $\Sigma_\mathrm{gas}$, $v_\mathrm{rot}$, and $R_\mathrm{gal}$ are the gas surface density, rotational velocity, and effective radius of the satellite, respectively, assuming a thin stellar disk structure. Using the inferred gas mass and aperture area of aperture #1 (Table [\[tab:radial_values\]](#tab:radial_values)), we adopt $\Sigma_\mathrm{gas}=\SI{1.6e7}{M\ensuremath{_\odot}\per\kilo\parsec\squared}$. Then, taking $v_\mathrm{rot}=\SI{100}{\kilo\meter\per\second}$, $R_\mathrm{gal}=\SI{200}{\parsec}$ and $V=\SI{166}{\kilo\meter\per\second}$, we obtain $n_\mathrm{CGM}=\rho_\mathrm{CGM}/m_{H}\gtrsim\SI{1}{\per\cubic\centi\meter}$. This is 3 to 4 orders of magnitude denser than typical ICM densities, and is comparable to the densities of H ii regions and the warm neutral medium in the Milky Way (cite: Draine2011IsmBook). On one hand, these gas phases are normally clumpy in the Local Universe, so they would not fill enough volume to sustain effective RPS along 15  . On the other hand, we know little about the structure of the high redshift CGM, so this concern may not apply.

The RPS scenario, however, is at odds with our observation of a decreasing linewidth as a function of distance along the plume. In the context of galaxy clusters, evidence suggests that stripped cold gas interacts with the hot ICM either heating it or inducing instabilities that build up turbulence with time. This effect is most clearly observed in ESO 137-001, a nearby edge-on jellyfish galaxy with a 40   H$\alpha$ tail (cite: Sun2007Eso137HalphaTail). MUSE observations resolve the trailing diffuse H$\alpha$ emisison into three almost parallel tails, and all of them show a mild but significant increase in velocity dispersion in the direction away from the disk in the first 20   (cite: Luo2023MuseKinematicsJellyfishEso137; Li2023TurbulenceJellyfish). Beyond that distance the dispersion remains more or less uniform. RPS in idealized numerical simulations generally reproduce this behavior, regardless of whether cooling (cite: RoedigerAndBruggen2008RamPressureStrippingWakes; Tonnesen2010RpsSignatures) and/or magnetic fields are included (cite: Tonnesen2014RpsMagneticFields).

## Gravitational interactions

Finally, we consider the scenario where the plume is formed as the result of a gravitational disturbance. We know that J1000+0234 is a complex multiple system (see Section [2](#sec:backstory)), so we expect frequent interactions among its members. It is thus very plausible that a close encounter with the massive DSFG at the center of the group induced the formation of a tidal tail. This explanation is simpler than the RPS scenario, as it does not require special hydrodynamic conditions but only gravity.

Here we present a qualitative discussion of three different ways this interaction could have happened. First, we consider the case where CRISTAL-01a made a flyby close to the DSFG. Second, we assume the progenitors already merged and the plume is the lasting debris of such encounter. And third, we consider the plume as a separate dwarf galaxy altogether, currently in the process of being stripped by the tidal forces exerted by the DSFG.

The idea that CRISTAL-01a and the DSFG are interacting was already suggested by several authors (e.g., (cite: Capak2008ExtremeStarburst; Schinnerer2008MolGasMajorMerger); ; ), although it was mostly based on the short projected distance between the two objects. also took the UV and Ly$\alpha$ elongated morphologies of CRISTAL-01a as evidence of ongoing tidal effects. With reliable \[C ii\]-based redshifts at hand, we now know CRISTAL-01a moves at a projected speed of 800 km s^−1^ relative to the DSFG, exceeding by a factor of 2.5 the escape velocity at a proper distance of 10   (314 km s^−1^; assuming a point mass of $M_\mathrm{dyn} = \SI{2.3e11}{M\ensuremath{_\odot}}$ located in the center of the DSFG, (cite: Fraternali2021FastRotators)). This implies CRISTAL-01a is not gravitationally bound to the DSFG, indicating that if CRISTAL-01a actually interacted with the DSFG, it was in a high-speed flyby.

The main issue with this first tidal scenario is the mass ratio between CRISTAL-01a and the DSFG. Decades of work on numerical simulations of galaxy collisions have found that the largest and longest-lived tails are produced in “major” interactions (cite: DucAndRenaud2013TidesInCollidingGalaxiesReview). In contrast, the stellar mass ratio here ($\sim 1:10$, ) belongs to the “minor” regime. Tidal features tend to be more prominent when the encounter occurs at low speeds, although it has been shown that high-speed flybys can also lead to the formation of gas-rich tails, provided the progenitors are both massive (cite: Bekki2005GasTailVirgo21; DucAndBournaud2008Virgo21HighSpeedFlyby). In conclusion, even if CRISTAL-01a shows some evidence of ongoing interaction with the DSFG, its relatively low mass make it an unlikely candidate to be responsible for the \[C ii\] plume.

Based on these considerations, we now discuss the second scenario, where two massive progenitors already merged into the DSFG, ejecting the \[C ii\] plume as a tidal tail. The fact that the DSFG is rotation-supported does not necessarily rule out a merger origin, since simulations have shown that is possible for two massive galaxies to collide and result in a disk, provided they have high gas fractions (cite: SpringelAndHernquist2005FormationOfSpiralInMerger; Peschken2020DiscGalaxiesMergersIllustris). In fact, this type of merger is expected to trigger very intense starbursts, just as the one we see in the DSFG. But did the merger have time to coalesce into a disk while still exhibiting a tidal tail? To answer this we need to estimate the dynamical age of the tail. To first order, we divide the length of the plume by the velocity difference between its two ends. In practice, we only consider apertures from #2 to #6, where the radial velocities are reliable. In this way we get $\tau_\mathrm{dyn}=\SI{13.15}{\kilo\parsec}/\SI{112}{\kilo\meter\per\second} = \SI{115}{\mega\year}$. On the other hand, the DSFG has a maximum rotation velocity of 550 km s^−1^ at a radius of 3.5   (cite: Fraternali2021FastRotators), translating into a dynamical timescale of merely $\approx$40  . Since the age of the plume is almost three times this value, we deem plausible that the tail persists after the merger has settled.

Tidal tails in the Local Universe usually come in pairs, as in the well-known examples of the Antennae Galaxies or the Mice (cite: ToomreAndToomre1972TidalTailsAndBridges). In contrast, the DSFG only shows one. While some examples of one-sided tails in late-stage mergers exist (cite: Sanders1988UlirgsAndOriginOfQsos), their formation involves highly inclined encounters (cite: Howard1993TidalSimAtlas). However, those configurations are not well suited for the survival of disks (cite: Cox2006KinMergerRemnants; Hopkins2013StarFormationMergers).

Finally, we consider the case of extreme tidal stripping of a satellite of the DSFG. In this picture, a dwarf galaxy orbiting the DSFG passes too close to the center, where tidal forces are strong enough to disrupt the intruder’s ISM into a long stream of gas. Depending on the central density of the intruder, it may not be totally disrupted, leaving its core relatively intact. If that is the case, the UV-bright region near the DSFG would be a natural candidate for the remnant, as it appears connected to the bottom of the plume. This idea could be tested with upcoming spectroscopy from JWST/NIRSpec.

Since gravity also acts on the stars, the three cases discussed here should produce a stellar stream associated with the plume, similar to those that populate the Milky Way halo (cite: Malhan2018HaloStellarStreamsGaiaDr2) or the surroundings of nearby massive galaxies (cite: MartinezDelgado2023StellarStreamLegacySurvey). Here, as mentioned in Sec. [5.2](#sec:discussion:inflow) we do not detect stellar emission from the plume in the HST images at a $5\sigma$ depth of 26.2  $''$^−2^, corresponding to an intrinsic SB of 18.8  $''$^−2^ after correcting for cosmological dimming. However, typical stellar streams in the Local Universe are much fainter, and only become detectable at sensitivities of $\approx\SI{28.5}{\mag\per\ensuremath{''}\squared}$ or higher (cite: BullockAndJohnston2005StellarHalosOne; MartinezDelgado2010StellarTidalStreamsSpirals). In addition, our HST filters probe the rest-frame UV emission, and hence only trace young stars and not the bulk of the stellar mass. Upcoming JWST/NIRCam observations will be significantly deeper, and trace the rest-frame optical light. But even then, a detection would need the tail or stream to be remarkably bright.

We conclude that gravitational interactions are more than capable of creating extended gas structures such as the \[C ii\] plume we observe, although the details are very uncertain. In fact, the three tidal scenarios presented here are only illustrative, and do not pretend to exhaust all the possible interactions that might produce a \[C ii\] plume. A more systematic approach would involve a series of numerical experiments to constrain the parameters that best reproduce the observed morphology and kinematics, but that goes beyond the scope of this paper.

# Summary & conclusions

We have presented new ALMA Band 7 observations of the inner region of the J1000+0234 system at $z=4.54$ located at the center of a bright Ly$\alpha$ blob. These observations are part of the ALMA-CRISTAL Large Program, targeting \[C ii\] 158 μm emission and the underlying dust continuum in a sample of 25 star-forming galaxies at $4 < z < 6$. The high sensitivity and angular resolution of these data reveal the detailed structure of the star-forming galaxies in the J1000+0234 system. We report the discovery of a faint and diffuse \[C ii\]-emitting plume extending up to 2.4″ ($\approx$15  ) from the central massive DSFG (J1000+0234-North). Complemented with archival MUSE and HST data, we analyzed the spatial and spectral properties of the plume and the two main galaxies of the system. Our main findings can be summarized as follows:

1.  The DSFG is detected in both \[C ii\] and dust continuum, and it shows a compact disk-like morphology. On one hand, dust emisison is fitted by a single 2D Sérsic profile with circularized effective radius of $R_\mathrm{eff}\approx\SI{0.74}{\kilo\parsec}$, Sérsic index $n\approx1.29$ and axis ratio $\approx0.4$. On the other hand, the \[C ii\] emission is fitted by 2D Sérsic profile of $R_\mathrm{eff}\approx\SI{1.13}{\kilo\parsec}$, $n\approx0.7$ and axis ratio $\approx\num{.34}$.

2.  CRISTAL-01a sits at a projected distance of 1.6″ from the DSFG, and recedes 800 km s^−1^ faster. It is detected in \[C ii\] emission but not in dust continuum, and its \[C ii\] morphology resembles that of the rest-frame UV emission. This means it is elongated and resolved into two clumps, although they are offset by 0.3″ from the corresponding UV-bright clumps. We model the northeastern clump with a circular exponential profile of $R_\mathrm{eff}\approx\SI{0.8}{\kilo\parsec}$, and the southwestern clump with an elliptical exponential of $R_\mathrm{eff}\approx\SI{2.4}{\kilo\parsec}$ and axis ratio $\approx0.82$.

3.  The \[C ii\] plume starts at the center of the DSFG and extends northward with a position angle that is offset by 40° clockwise from the DSFG’s minor axis. The \[C ii\] surface brightness declines rapidly along the plume, becoming undetected at $\approx\SI{15}{\kilo\parsec}$ from the center of the DSFG. In the transverse direction we measure an average FWHM extent of $\approx\SI{4}{\kilo\parsec}$.

4.  The plume exhibits a clear velocity gradient, increasing the line central velocity as a function of radial distance from 180 km s^−1^ to 400 km s^−1^, relative to the DSFG’s systemic velocity. Moreover, the line FWHM also evolves with radius, showing a smooth drop from 450 km s^−1^ at the center of the DSFG to 190 km s^−1^ at the farthest measured point.

5.  We detect no dust continuum at rest-frame 160 μm from the plume down to $5\sigma=\SI{194}{\micro\jansky}$ per $\ang{;;0.9}\times\ang{;;0.4}$ aperture. At an assumed dust temperature of $T_\mathrm{dust}=\SI{45}{\kelvin}$, we obtain lower limits on the \[C ii\]/FIR ratio between $\approx0.2\%$ and $\approx 0.6\%$, consistent with UV photoelectric heating of the gas.

6.  We estimate a minimum total mass for the plume of 7.1 ± 0.4 × 10^8^ M $_\odot$, asuming a conversion factor $\kappa_\mathrm{[CII]} = \SI{1.5}{M\ensuremath{_\odot}\per\lumsol}$ that corresponds to the limit of maximal excitation of the line in a medium dominated by atomic hydrogen, with solar-like carbon abundance.

We discuss four scenarios to explain the results outlined above: (1), the plume is a conical outflow. (2), the plume traces a filament of inflowing gas. (3), the plume is a ram-pressure stripped tail of an infalling satellite. (4), the plume is tidal debris from past gravitational interactions.

In the first scenario (1), we infer resolved mass outflow rates between 16 M $_\odot$ ^−1^ and 83 M $_\odot$ ^−1^. The maximum outflow velocities across the plume range from 530 km s^−1^ to 620 km s^−1^. These values are roughly consistent with literature scaling relations for SFR and $L_\mathrm{bol}$ in the case of starburst-driven and AGN-driven outflows, respectively. Given the very low ($\theta\approx\ang{15}$) opening angle we derive under the assumption of a simple conical geometry, plus the misalignment with the DSFG’s minor axis, the putative outflow appears more likely to have originated in a central AGN. However, the observed kinematic radial trends are in mild tension with the expected properties of an outflow.

Scenario (2) is qualitatively consistent with theoretical expectations for cold accretion streams, except for our inference of a slow-down of the gas as it falls, although this can be accomodated by pressure gradients in the CGM. Moreover, the fact the putative filament emits in \[C ii\] rules out a chemically pristine gas composition. Still, simulations suggest that gas enrichment can happen concurrently during the inflow, either by gas mixing in the CGM or by in-situ star formation.

Scenario (3) requires the UV-bright region of the DSFG to be a satellite galaxy that is crossing the DSFG’s CGM. In addition, the CGM must be dense ($\gtrsim \SI{1}{\per\cubic\centi\meter}$) in order to exert a significant ram pressure capable of stripping off the satellite’s ISM. Moreover, observations and simulations of ram pressure stripping predict an increase of velocity dispersion along the stripped tails, contrary to what we observe in J1000+0234.

Finally, scenario (4) is motivated by the fact J1000+0234 is an overdense environment and close interactions must be frequent. We explored three possible ways a gravitational interaction can lead to the formation of a one-sided tidal tail. Namely, a high-speed flyby of CRISTAL-01a, a late-stage major merger in which the \[C ii\] plume is its remaining debris, and the tidal stripping of a minor satellite in a radial orbit. While a proper assessment of these configurations using tailored numerical simulations remains pending, heuristic arguments slightly disfavor the first two.

Besides scenario (3), which requires very special hydrodynamic conditions, outflows, inflows and tidal tails all have their pros and cons. Further observations and modeling are needed to discriminate between them. Promisingly, upcoming JWST/NIRCam and JWST/NIRSpec observations will deliver a high angular resolution view of the rest-frame optical morphology and spectral properties. For example, narrow H$\alpha$ spectral imaging with NIRSpec IFU will constrain the star formation rate density in the \[C ii\] plume. In addition, the detection of a broad H$\alpha$ component would support the outflow scenario. At the same time, NIRCam broad band observations will uncover the obscured regions of the DSFG and potentially discover a diffuse stellar stream associated with the \[C ii\] plume, providing further evidence to the tidal tail scenario.

Our results highlight the power of ALMA for characterizing the cold CGM in emission at high redshift, but also the difficulty of their interpretation. Disentangling the physical mechanisms that produce a given \[C ii\] observation is nevertheless very important for understanding how galaxies and their surroundings evolve.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00428.L, ADS/JAO.ALMA#2021.1.00280.L, ADS/JAO.ALMA#2019.1.01587.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This paper is partly based on observations collected at the European Southern Observatory under ESO programs 0102.A-0448 and 0103.A-0272. M. S. was financially supported by Becas-ANID scolarship #21221511, and also acknowledges ANID BASAL project FB210003. M. A. acknowledges support from FONDECYT grant 1211951 and ANID BASAL project FB210003. A.F. acknowledges support from the ERC Advanced Grant INTERSTELLAR H2020/740120. E. J. J. acknowledges support from FONDECYT Iniciación en investigación 2020 Project 11200263 and the ANID BASAL project FB210003. I. DL. and S. vdG. acknowledge funding support from ERC starting grant 851622 DustOrigin. K. T. acknowledges support from JSPS KAKENHI Grant Number 23K03466. L. G. thanks support from FONDECYT regular proyecto No1230591. R. I. is financially supported by Grants-in-Aid for Japan Society for the Promotion of Science (JSPS) Fellows (KAKENHI Grant Number 23KJ1006). R. J. A. was supported by FONDECYT grant number 123171 and by the ANID BASAL project FB210003. I.M. thanks the financial support by Grants-in-Aid for Japan Society for the Promotion of Science (JSPS) Fellows (KAKENHI Number 22KJ0821). R. L. D. is supported by the Australian Research Council Centre of Excellence for All Sky Astrophysics in 3 Dimensions (ASTRO 3D), through project number CE170100013. M. R. acknowledges support from project PID2020-114414GB-100, financed by MCIN/AEI/10.13039/501100011033.

161 natexlab

(ref: Aalto2020ResolvedMolecularJet) Aalto, S., Falstad, N., Muller, S., et al. 2020, A&A, 640, A104

(ref: Akins2022ExtendedCoolGasOutflowRedshift7) Akins, H. B., Fujimoto, S., Finlator, K., et al. 2022, ApJ, 934, 64

(ref: AnglesAlcazar2017BaryonCycleInFIRE) Anglés-Alcázar, D., Faucher-Giguère, C.-A., Kereš, D., et al. 2017, MNRAS, 470, 4698

(ref: Appleton2013ShockCiiSQ) Appleton, P. N., Guillard, P., Boulanger, F., et al. 2013, ApJ, 777, 66

(ref: Aretxaga2011AztecSurveyCosmos) Aretxaga, I., Wilson, G. W., Aguilar, E., et al. 2011, MNRAS, 415, 3831

(ref: ArrigoniBattaia2015CompactGasClumpsCgmQuasar) Arrigoni Battaia, F., Hennawi, J. F., Prochaska, J. X., & Cantalupo, S. 2015, ApJ, 809, 163

(ref: Bao2019XshapedBicone) Bao, M., Chen, Y.-m., Yuan, Q.-r., et al. 2019, MNRAS, 490, 3830

(ref: Bekki2009RpsInDiscs) Bekki, K. 2009, MNRAS, 399, 2221

(ref: Bekki2005GasTailVirgo21) Bekki, K., Koribalski, B. S., & Kilborn, V. A. 2005, MNRAS, 363, L21

(ref: Bethermin2020DataProcessing) Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2

(ref: Bischetti2019QsoCiiOutflows) Bischetti, M., Maiolino, R., Carniani, S., et al. 2019, A&A, 630, A59

(ref: BlandAndTully1988BipolarWindM82) Bland, J. & Tully, B. 1988, Nature, 334, 43

(ref: Boselli2022RpsReview) Boselli, A., Fossati, M., & Sun, M. 2022, A&ARv, 30, 3

(ref: Bouchet1985SmcExtinctionLaw) Bouchet, P., Lequeux, J., Maurice, E., Prevot, L., & Prevot-Burnichon, M. L. 1985, A&A, 149, 330

(ref: Brammer2021GrizliSoftware) Brammer, G. 2023, grizli, Zenodo

(ref: BullockAndJohnston2005StellarHalosOne) Bullock, J. S. & Johnston, K. V. 2005, ApJ, 635, 931

(ref: Cantalupo2014CosmicWebFilament) Cantalupo, S., Arrigoni-Battaia, F., Prochaska, J. X., Hennawi, J. F., & Madau, P. 2014, Nature, 506, 63

(ref: Capak2008ExtremeStarburst) Capak, P., Carilli, C. L., Lee, N., et al. 2008, ApJL, 681, L53

(ref: Carilli2008RadioLbgs) Carilli, C. L., Lee, N., Capak, P., et al. 2008, ApJ, 689, 883

(ref: Carniani2013ExtendedCiiComplexMerger) Carniani, S., Marconi, A., Biggs, A., et al. 2013, A&A, 559, A29

(ref: CasaTeam2022CasaRefPaper) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Ceverino2010HighzClumpyDisks) Ceverino, D., Dekel, A., & Bournaud, F. 2010, MNRAS, 404, 2151

(ref: Chabrier2003IMF) Chabrier, G. 2003, PASP, 115, 763

(ref: Chung2009VirgoVlaAtomicGas) Chung, A., van Gorkom, J. H., Kenney, J. D. P., Crowl, H., & Vollmer, B. 2009, AJ, 138, 1741

(ref: Cicone2021GiantMolecHaloRedshiftTwo) Cicone, C., Mainieri, V., Circosta, C., et al. 2021, A&A, 654, L8

(ref: Cicone2015ExtendedHaloQso) Cicone, C., Maiolino, R., Gallerani, S., et al. 2015, A&A, 574, A14

(ref: Claeyssens2022LlamasPaper1) Claeyssens, A., Richard, J., Blaizot, J., et al. 2022, A&A, 666, A78

(ref: Cooper2008ThreeDimSimWind) Cooper, J. L., Bicknell, G. V., Sutherland, R. S., & Bland-Hawthorn, J. 2008, ApJ, 674, 157

(ref: Cox2006KinMergerRemnants) Cox, T. J., Dutta, S. N., Di Matteo, T., et al. 2006, ApJ, 650, 791

(ref: Czekala2021JvMGuidelines) Czekala, I., Loomis, R. A., Teague, R., et al. 2021, ApJS, 257, 2

(ref: Danovich2015AngularMomentumBuildUp) Danovich, M., Dekel, A., Hahn, O., Ceverino, D., & Primack, J. 2015, MNRAS, 449, 2087

(ref: DekelAndBirnboim2006ColdFlowsShockHeating) Dekel, A. & Birnboim, Y. 2006, MNRAS, 368, 2

(ref: Dekel2009ColdModeAccretion) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Draine2011IsmBook) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: DucAndBournaud2008Virgo21HighSpeedFlyby) Duc, P.-A. & Bournaud, F. 2008, ApJ, 673, 787

(ref: DucAndRenaud2013TidesInCollidingGalaxiesReview) Duc, P.-A. & Renaud, F. 2013, in Lecture Notes in Physics, Berlin Springer Verlag, ed. J. Souchay, S. Mathis, & T. Tokieda, Vol. 861, 327

(ref: Ebeling2014Jellyfish) Ebeling, H., Stephenson, L. N., & Edge, A. C. 2014, ApJL, 781, L40

(ref: Emonts2019ColdCgmMammoth1) Emonts, B. H. C., Cai, Z., Prochaska, J. X., Li, Q., & Lehnert, M. D. 2019, ApJ, 887, 86

(ref: Emonts2018SpiderwebCircumgalacticCi) Emonts, B. H. C., Lehnert, M. D., Dannerbauer, H., et al. 2018, MNRAS, 477, L60

(ref: Emonts2016MolGasClusterHighZ) Emonts, B. H. C., Lehnert, M. D., Villar-Martı́n, M., et al. 2016, Science, 354, 1128

(ref: Emonts2023CarbonCosmicStream) Emonts, B. H. C., Lehnert, M. D., Yoon, I., et al. 2023, Science, 379, 1323

(ref: Emonts2015CoRichMergerDragonfly) Emonts, B. H. C., Mao, M. Y., Stroe, A., et al. 2015, MNRAS, 451, 1025

(ref: Emonts2014CoSurveyHighzRGs) Emonts, B. H. C., Norris, R. P., Feain, I., et al. 2014, MNRAS, 438, 2898

(ref: ESO2015CPL) ESO CPL Development Team. 2015, EsoRex: ESO Recipe Execution Tool, Astrophysics Source Code Library, record ascl:1504.003

(ref: Faisst2020AlpineMultiWavelength) Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020, ApJS, 247, 61

(ref: FieldingAndBryan2022MultiphaseGalacticWinds) Fielding, D. B. & Bryan, G. L. 2022, ApJ, 924, 82

(ref: Fiore2017AgnWindScaling) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: Francis1996LyaGroup) Francis, P. J., Woodgate, B. E., Warren, S. J., et al. 1996, ApJ, 457, 490

(ref: Fraternali2021FastRotators) Fraternali, F., Karim, A., Magnelli, B., et al. 2021, A&A, 647, A194

(ref: Frayer2018MassiveMolecularComponentSmg) Frayer, D. T., Maddalena, R. J., Ivison, R. J., et al. 2018, ApJ, 860, 87

(ref: Fujimoto2019CiiHalos) Fujimoto, S., Ouchi, M., Ferrara, A., et al. 2019, ApJ, 887, 107

(ref: Fujimoto2020AlpineHalos) Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, ApJ, 900, 1

(ref: Fumagalli2011AbsorptionInSimulatedColdStreams) Fumagalli, M., Prochaska, J. X., Kasen, D., et al. 2011, MNRAS, 418, 1796

(ref: GaiaCollaboration2018Release2) Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1

(ref: Gallerani2018AlmaOutflowsRedshift5) Gallerani, S., Pallottini, A., Feruglio, C., et al. 2018, MNRAS, 473, 1909

(ref: Geach2009LabsPoweredByHeating) Geach, J. E., Alexander, D. M., Lehmer, B. D., et al. 2009, ApJ, 700, 1

(ref: Genzel2011SinsSurvey) Genzel, R., Newman, S., Jones, T., et al. 2011, ApJ, 733, 101

(ref: Ginolfi2020AlpineMergerTidal) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020a, A&A, 643, A7

(ref: Ginolfi2020AlpineOutflowsCGM) Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020b, A&A, 633, A90

(ref: Ginolfi2017Molecular) Ginolfi, M., Maiolino, R., Nagao, T., et al. 2017, MNRAS, 468, 3468

(ref: GoerdtAndCeverino2015InflowVelocitiesColdStreams) Goerdt, T. & Ceverino, D. 2015, MNRAS, 450, 3359

(ref: GomezGuijarro2018AlmaMinorMergersSmgs) Gómez-Guijarro, C., Toft, S., Karim, A., et al. 2018, ApJ, 856, 121

(ref: Grand2019AccretionAndFountainFlowsInAuriga) Grand, R. J. J., van de Voort, F., Zjupa, J., et al. 2019, MNRAS, 490, 4786

(ref: GunAndGott1972InfallClusters) Gunn, J. E. & Gott, J. Richard, I. 1972, ApJ, 176, 1

(ref: Hack2021DrizzlePacv3) Hack, W. J., Cara, M., Sosey, M., et al. 2021, spacetelescope/drizzlepac: Drizzlepac v3.3.0, Zenodo

(ref: Hasinger2018DeimosCosmos) Hasinger, G., Capak, P., Salvato, M., et al. 2018, ApJ, 858, 77

(ref: Hennawi2006ThickAbsorbersAroundQsos) Hennawi, J. F., Prochaska, J. X., Burles, S., et al. 2006, ApJ, 651, 61

(ref: Herenz2023OutflowConeMetalPoor) Herenz, E. C., Inoue, J., Salas, H., et al. 2023, A&A, 670, A121

(ref: Herenz2017LsdCat) Herenz, E. C. & Wisotzki, L. 2017, A&A, 602, A111

(ref: HerreraCamus2015CiiAsSfrTracerKingFish) Herrera-Camus, R., Bolatto, A. D., Wolfire, M. G., et al. 2015, ApJ, 800, 1

(ref: HerreraCamus2021OutflowHZ4) Herrera-Camus, R., Förster Schreiber, N., Genzel, R., et al. 2021, A&A, 649, A31

(ref: HerreraCamus2018Shining1) Herrera-Camus, R., Sturm, E., Graciá-Carpio, J., et al. 2018, ApJ, 861, 94

(ref: HjelmAndLindblad1996OutflowNgc1365) Hjelm, M. & Lindblad, P. O. 1996, A&A, 305, 727

(ref: Hopkins2013StarFormationMergers) Hopkins, P. F., Cox, T. J., Hernquist, L., et al. 2013, MNRAS, 430, 1901

(ref: Howard1993TidalSimAtlas) Howard, S., Keel, W. C., Byrd, G., & Burkey, J. 1993, ApJ, 417, 502

(ref: Jimenez-Andrade2023LyaNebulaeGalaxyPair) Jiménez-Andrade, E. F., Cantalupo, S., Magnelli, B., et al. 2023, MNRAS, 521, 2326

(ref: Jones2017DynamicsTiltedRingSmgs) Jones, G. C., Carilli, C. L., Shao, Y., et al. 2017, ApJ, 850, 180

(ref: JorsaterAndvonMoorsel1995BarredSpiralHI) Jorsater, S. & van Moorsel, G. A. 1995, AJ, 110, 2037

(ref: Kennicutt98SFR) Kennicutt, Robert C., J. 1998, ARA&A, 36, 189

(ref: Kennicutt2011KingfishSample) Kennicutt, R. C., Calzetti, D., Aniano, G., et al. 2011, PASP, 123, 1347

(ref: Kim2020MultiphaseOutflowsTigress) Kim, C.-G., Ostriker, E. C., Fielding, D. B., et al. 2020, ApJL, 903, L34

(ref: Koposov2022DynestyZenodoV203) Koposov, S., Speagle, J., Barbary, K., et al. 2022, joshspeagle/dynesty: v2.0.3, Zenodo

(ref: Lambert2023CiiHaloAroundHz7) Lambert, T. S., Posses, A., Aravena, M., et al. 2023, MNRAS, 518, 3183

(ref: Law2009HighRedshiftKinematics) Law, D. R., Steidel, C. C., Erb, D. K., et al. 2009, ApJ, 697, 2057

(ref: LeFevre2020AlpineSurveyDesign) Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1

(ref: LeFevre1996ClusteringAroundRadioGalaxy) Le Fevre, O., Deltorn, J. M., Crampton, D., & Dickinson, M. 1996, ApJL, 471, L11

(ref: Leclerq2017MuseHudfLyaHaloes) Leclercq, F., Bacon, R., Wisotzki, L., et al. 2017, A&A, 608, A8

(ref: Lemaux2018VudsProtoCluster) Lemaux, B. C., Le Fèvre, O., Cucciati, O., et al. 2018, A&A, 615, A77

(ref: Li2021OutflowAndColdHaloQso) Li, J., Emonts, B. H. C., Cai, Z., et al. 2021, ApJL, 922, L29

(ref: Li2023TurbulenceJellyfish) Li, Y., Luo, R., Fossati, M., Sun, M., & Jáchym, P. 2023, MNRAS, 521, 4785

(ref: Loiacono2021AlpineCiiLf) Loiacono, F., Decarli, R., Gruppioni, C., et al. 2021, A&A, 646, A76

(ref: Luo2023MuseKinematicsJellyfishEso137) Luo, R., Sun, M., Jáchym, P., et al. 2023, MNRAS, 521, 6266

(ref: Malhan2018HaloStellarStreamsGaiaDr2) Malhan, K., Ibata, R. A., & Martin, N. F. 2018, MNRAS, 481, 3442

(ref: Mandelker2018ColdFilamentaryAccretion) Mandelker, N., van Dokkum, P. G., Brodie, J. P., van den Bosch, F. C., & Ceverino, D. 2018, ApJ, 861, 148

(ref: MartinezDelgado2023StellarStreamLegacySurvey) Martı́nez-Delgado, D., Cooper, A. P., Román, J., et al. 2023, A&A, 671, A141

(ref: MartinezDelgado2010StellarTidalStreamsSpirals) Martı́nez-Delgado, D., Gabany, R. J., Crawford, K., et al. 2010, AJ, 140, 962

(ref: Matsuda2004SubaruLyaBlobs) Matsuda, Y., Yamada, T., Hayashino, T., et al. 2004, AJ, 128, 569

(ref: McPherson2023DuvetOutflowsMrk1486) McPherson, D. K., Fisher, D. B., Nielsen, N. M., et al. 2023, MNRAS, 525, 6170

(ref: Meurer1999IrxBetaRelation) Meurer, G. R., Heckman, T. M., & Calzetti, D. 1999, ApJ, 521, 64

(ref: Neeleman2017CiiFromDlaHost) Neeleman, M., Kanekar, N., Prochaska, J. X., et al. 2017, Science, 355, 1285

(ref: Neeleman2019CiiEmissionFromHighzDLAs) Neeleman, M., Kanekar, N., Prochaska, J. X., Rafelski, M. A., & Carilli, C. L. 2019, ApJL, 870, L19

(ref: Nelson2019Tng50SimOutflows) Nelson, D., Pillepich, A., Springel, V., et al. 2019, MNRAS, 490, 3234

(ref: Nightingale2023PyAutoGalaxy) Nightingale, J., Amvrosiadis, A., Hayes, R., et al. 2023, The Journal of Open Source Software, 8, 4475

(ref: Nightingale2021PyAutoFit) Nightingale, J., Hayes, R., & Griffiths, M. 2021, The Journal of Open Source Software, 6, 2550

(ref: Ouchi2020LymanAlphaReview) Ouchi, M., Ono, Y., & Shibuya, T. 2020, ARA&A, 58, 617

(ref: Overzier2016ProtoclusterReview) Overzier, R. A. 2016, A&ARv, 24, 14

(ref: PereiraSantaella2016ExtendedMolecularOutflowLirg) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2016, A&A, 594, A81

(ref: PereiraSantaella2018SpatiallyResolvedOutflowsUlirgs) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2018, A&A, 616, A171

(ref: PerouxHowk2020CosmicBaryonAndMetalCycles) Péroux, C. & Howk, J. C. 2020, ARA&A, 58, 363

(ref: Peschken2020DiscGalaxiesMergersIllustris) Peschken, N., Łokas, E. L., & Athanassoula, E. 2020, MNRAS, 493, 1375

(ref: Peterson2018TaffyCiiBridge) Peterson, B. W., Appleton, P. N., Bitsakis, T., et al. 2018, ApJ, 855, 141

(ref: Pizzati2020OutflowsCiiHaloes) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 495, 160

(ref: Pizzati2023CiiHaloesSmokingGun) Pizzati, E., Ferrara, A., Pallottini, A., et al. 2023, MNRAS, 519, 4608

(ref: Poggianti2017GaspI) Poggianti, B. M., Moretti, A., Gullieuszik, M., et al. 2017, ApJ, 844, 48

(ref: RoedigerAndBruggen2008RamPressureStrippingWakes) Roediger, E. & Brüggen, M. 2008, MNRAS, 388, 465

(ref: Rose2023Abell2390Plume) Rose, T., McNamara, B. R., Combes, F., et al. 2023, arXiv e-prints, arXiv:2310.16892

(ref: Rubin2014EvidenceCollimatedOutflows) Rubin, K. H. R., Prochaska, J. X., Koo, D. C., et al. 2014, ApJ, 794, 156

(ref: Rupke2019AHundredKpcWindCgm) Rupke, D. S. N., Coil, A., Geach, J. E., et al. 2019, Nature, 574, 643

(ref: RuschelDutra2021AgnifsOutflows) Ruschel-Dutra, D., Storchi-Bergmann, T., Schnorr-Müller, A., et al. 2021, MNRAS, 507, 74

(ref: Sakamoto2014MergerWithMolecularOutflows) Sakamoto, K., Aalto, S., Combes, F., Evans, A., & Peck, A. 2014, ApJ, 797, 90

(ref: Sanders1988UlirgsAndOriginOfQsos) Sanders, D. B., Soifer, B. T., Elias, J. H., et al. 1988, ApJ, 325, 74

(ref: Sarazin1986IntraclusterMedium) Sarazin, C. L. 1986, Reviews of Modern Physics, 58, 1

(ref: Schinnerer2008MolGasMajorMerger) Schinnerer, E., Carilli, C. L., Capak, P., et al. 2008, ApJL, 689, L5

(ref: Schmitt2003ExtendedOiiiSeyferts) Schmitt, H. R., Donley, J. L., Antonucci, R. R. J., et al. 2003, ApJ, 597, 768

(ref: Schneider2020SbDrivenOutflowsSim) Schneider, E. E., Ostriker, E. C., Robertson, B. E., & Thompson, T. A. 2020, ApJ, 895, 43

(ref: SeaquistAndClark2001CoInOutflowM82) Seaquist, E. R. & Clark, J. 2001, ApJ, 552, 133

(ref: Sersic1968AtlasdeGalaxias) Sersic, J. L. 1968, Atlas de Galaxias Australes

(ref: Shapley2003RestUvSpectraLbgs) Shapley, A. E., Steidel, C. C., Pettini, M., & Adelberger, K. L. 2003, ApJ, 588, 65

(ref: Smith2010UvTailsClusters) Smith, R. J., Lucey, J. R., Hammer, D., et al. 2010, MNRAS, 408, 1417

(ref: Smolcic2015PhysicalPropertiesSmgsCosmos) Smolčić, V., Karim, A., Miettinen, O., et al. 2015, A&A, 576, A127

(ref: Smolcic2017SmgEnvironments) Smolčić, V., Miettinen, O., Tomičić, N., et al. 2017, A&A, 597, A4

(ref: Solimano2022LymanAlphaSGASJ1226) Solimano, M., González-López, J., Aravena, M., et al. 2022, ApJ, 935, 17

(ref: Soto2016ZAP) Soto, K. T., Lilly, S. J., Bacon, R., Richard, J., & Conseil, S. 2016, MNRAS, 458, 3210

(ref: Speagle2020Dynesty) Speagle, J. S. 2020, MNRAS, 493, 3132

(ref: Spilker2020MolecularOutflowsSPT) Spilker, J. S., Phadke, K. A., Aravena, M., et al. 2020, ApJ, 905, 85

(ref: SpringelAndHernquist2005FormationOfSpiralInMerger) Springel, V. & Hernquist, L. 2005, ApJL, 622, L9

(ref: Steidel2000LyaProtoCluster) Steidel, C. C., Adelberger, K. L., Shapley, A. E., et al. 2000, ApJ, 532, 170

(ref: Strickland2004HighResXrayHalphaHotGasDisks) Strickland, D. K., Heckman, T. M., Colbert, E. J. M., Hoopes, C. G., & Weaver, K. A. 2004, ApJ, 606, 829

(ref: Stsci2012DrizzlePac) STSCI Development Team. 2012, DrizzlePac: HST image software, Astrophysics Source Code Library, record ascl:1212.011

(ref: Sun2007Eso137HalphaTail) Sun, M., Donahue, M., & Voit, G. M. 2007, ApJ, 671, 190

(ref: Szokoly2004Cdfs) Szokoly, G. P., Bergeron, J., Hasinger, G., et al. 2004, ApJS, 155, 271

(ref: Tonnesen2010RpsSignatures) Tonnesen, S. & Bryan, G. L. 2010, ApJ, 709, 1203

(ref: Tonnesen2014RpsMagneticFields) Tonnesen, S. & Stone, J. 2014, ApJ, 795, 148

(ref: ToomreAndToomre1972TidalTailsAndBridges) Toomre, A. & Toomre, J. 1972, ApJ, 178, 623

(ref: Tsukui2022CorrelatedNoiseInterferometry) Tsukui, T., Iguchi, S., Mitsuhashi, I., & Tadaki, K. 2022, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 12190, Millimeter, Submillimeter, and Far-Infrared Detectors and Instrumentation for Astronomy XI, ed. J. Zmuidzinas & J.-R. Gao, 121901C

(ref: Tsukui2023Essence) Tsukui, T., Iguchi, S., Mitsuhashi, I., & Tadaki, K. 2023, ESSENCE: Evaluate spatially correlated noise in interferometric images, Astrophysics Source Code Library, record ascl:2306.055

(ref: Tumlinson2017CircumgalacticMediumReview) Tumlinson, J., Peeples, M. S., & Werk, J. K. 2017, ARA&A, 55, 389

(ref: Turner2014MetalLineAbsorptionKeck) Turner, M. L., Schaye, J., Steidel, C. C., Rudie, G. C., & Strom, A. L. 2014, MNRAS, 445, 794

(ref: Umehata2021CiiObsOfLAB1) Umehata, H., Smail, I., Steidel, C. C., et al. 2021, ApJ, 918, 69

(ref: VasudevanAndFabian2007BolCorrAGN) Vasudevan, R. V. & Fabian, A. C. 2007, MNRAS, 381, 1235

(ref: Veilleux2020CoolOutflowsReview) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2

(ref: VeilleuxAndRupke2002GalacticWindNgc1482) Veilleux, S. & Rupke, D. S. 2002, ApJL, 565, L63

(ref: Veilleux2001BiconicalOutflowNgc2992) Veilleux, S., Shopbell, P. L., & Miller, S. T. 2001, AJ, 121, 198

(ref: Venemans2002ProtoclusterRedshiftFour) Venemans, B. P., Kurk, J. D., Miley, G. K., et al. 2002, ApJL, 569, L11

(ref: Venturi2017MagnumIonizedOutflows) Venturi, G., Marconi, A., Mingozzi, M., et al. 2017, Frontiers in Astronomy and Space Sciences, 4, 46

(ref: Venturi2018MagnumNgc1365) Venturi, G., Nardini, E., Marconi, A., et al. 2018, A&A, 619, A74

(ref: Weilbacher2020MUSE_DPP) Weilbacher, P. M., Palsa, R., Streicher, O., et al. 2020, A&A, 641, A28

(ref: Werk2013CosHalos) Werk, J. K., Prochaska, J. X., Thom, C., et al. 2013, ApJS, 204, 17

(ref: Westmoquette2011SuperwindNgc253) Westmoquette, M. S., Smith, L. J., & Gallagher, J. S., I. 2011, MNRAS, 414, 3719

(ref: Wisotzki2016ExtendedLyaHalosMUSE) Wisotzki, L., Bacon, R., Blaizot, J., et al. 2016, A&A, 587, A98

(ref: ZhuAndMenard2013SdssMgiiAbsorbers) Zhu, G. & Ménard, B. 2013, ApJ, 770, 130

# Symmetric difference correction of aperture #1’s \[C ii\] spectrum

As described in Sec. [4.3](#sec:results:cii_spectral), the aperture #1 in Fig. [4](#fig:radial_tail) contains significant emission from the dust continuum and the approaching side of the DSFG rotator. To mitigate the contamination, we performed continuum subtraction and masked negative velocities before fitting the line, yet the resulting 1D Gaussian parameters deviate significantly from the parameters of the line in the subsequent apertures, suggesting additional contamination at positive velocities. Motivated by this, we attempt in this section to remove the additional emission before repeating the Gaussian fit.

If the DSFG rotator is axially symmetric, we expect any aperture-extracted spectrum from one side of the DSFG to be similar–although with inverted velocities–to a spectrum extracted from a mirrored aperture, reflected with respect to the projected rotation axis. So in principle, differences in these spectra will uncover asymmetric emission in the cube, such as the plume we are studying.

Here, we take the projected rotation axis to be parallel to the minor axis of the DSFG’s \[C ii\] emission (see dashed line in Fig. [4](#fig:radial_tail)) and crossing the position of the steepest velocity gradient. In practice, we choose the point where the 2^nd^ moment (velocity dispersion) is maximal. Once we have defined the axis, we calculate the geometrical reflection of aperture #1. However, the rotation axis crosses through the aperture, which would lead to an overlapping region between the aperture and its mirrored version. To avoid this, we crop the corner of aperture #1 that goes over the eastern side of the axis before the reflection.

We then extract the \[C ii\] spectrum from the `robust=0.5`, 20 km s^−1^ channel width cube without continuum subtraction, from both the cropped aperture #1 and its reflection. We then apply a simple continuum subtraction by fitting a first-order polynomial to channels between $\pm\SI{1330}{\kilo\meter\per\second}$ and $\pm\SI{1000}{\kilo\meter\per\second}$ independently for each spectrum. We show the resulting spectra in Fig. [6](#fig:sym_diff).

![](figures/spectra_aperture_01_symmetrization.pdf)

After flipping the mirrored spectrum in velocity space and comparing it with the original, we find the horns have different peak heights and are offset by $\approx$47 km s^−1^, but have similar overall shape. We thus shift and scale the mirrored spectrum to match the peak of the original and then perform the subtraction. The resulting spectrum is shown in the lower panel of Fig. [6](#fig:sym_diff). The difference is mostly consistent with zero, except for a strong but narrow negative difference around −250 km s^−1^ and a broad positive difference between 0 km s^−1^ and 400 km s^−1^. The former arises from an excess or quirk in the spectrum from the mirrored aperture at 250 km s^−1^, while the latter we assume to be associated with the \[C ii\] plume.

Finally, we model the difference spectrum with the method described in Sec. [4.3](#sec:results:cii_spectral). This is, we fit a 1D Gaussian using PYAUTOFIT. Once again, we mask the negative velocities down to −700 km s^−1^ to avoid fitting the residual negative feature. Compared to our fiducial method, this fit yields a significantly lower flux ($\approx\SI{0.3}{\jansky\kilo\meter\per\second}$) and FWHM ($\approx\SI{420}{\kilo\meter\per\second}$), although the central velocities are consistent. In conclusion, both the flux and FWHM in aperture #1 are affected by contamination from the host, but the central velocity is not.

# Stack of HST images

In this section we present the stack of HST imaging in the F105W, F125W, F140W and F160W filters. We converted the image units to nJy per pixel, and then computed a pixel-by-pixel weighted sum. The weigths correspond to the inverse variance of the full frames. We then measure fluxes in 5000 random apertures of 1 $''$^2^ area, and obtain a $5\sigma$ depth of 26.2  $''$^−2^ Fig. [7](#fig:hst_stack) shows the result of the stacking in the region close to the J1000+0234 system, and reveals two tentative sources near the \[C ii\] plume that were not detected in the individual images.

![](figures/hst_wfc3_ir_stack_cii_contours.pdf)

[^1]: <https://casaguides.nrao.edu/index.php/DataWeightsAndCombination>

[^2]: <https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html>

[^3]: ESSENCE, (cite: Tsukui2023Essence)

[^4]: Defined as the integral of the rest-frame SED between 42 μm and 122 μm.

</paper>

Write the methods card for this paper.