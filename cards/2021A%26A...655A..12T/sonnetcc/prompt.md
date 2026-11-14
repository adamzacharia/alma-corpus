# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...655A..12T\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...655A..12T",
 "title": "Kinetic temperature of massive star-forming molecular clumps measured with formaldehyde. IV. The ALMA view of N113 and N159W in the LMC",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Tang, X. D.",
 "n_authors": 28,
 "arxiv_id": "2108.10519",
 "doi": "10.1051/0004-6361/202141804",
 "alma_projects_linked_by_archive": [
  "2012.1.00554.S",
  "2013.1.01136.S",
  "2015.1.01388.S"
 ]
}
```

Paper text:
<paper>
# Kinetic temperature of massive star-forming molecular clumps measured with formaldehyde

We mapped the kinetic temperature structure of two massive star-forming regions, N113 and N159W, in the Large Magellanic Cloud (LMC). We have used $\sim$1$\,.\!\!^{\prime\prime}$6 ($\sim$0.4 pc) resolution measurements of the para-H$_2$CO $J_{\rm K_ aK_c}$ = 3$_{03}$–2$_{02}$, 3$_{22}$–2$_{21}$, and 3$_{21}$–2$_{20}$ transitions near 218.5 GHz to constrain RADEX non-LTE models of the physical conditions. The gas kinetic temperatures derived from the para-H$_2$CO line ratios 3$_{22}$–2$_{21}$/3$_{03}$–2$_{02}$ and 3$_{21}$–2$_{20}$/3$_{03}$–2$_{02}$ range from 28 to 105 K in N113 and 29 to 68 K in N159W. Distributions of the dense gas traced by para-H$_2$CO agree with those of the 1.3 mm dust and *Spitzer* 8.0 $\mu$m emission, but do not significantly correlate with the H$\alpha$ emission. The high kinetic temperatures ($T_{\rm kin}$ $\gtrsim$ 50 K) of the dense gas traced by para-H$_2$CO appear to be correlated with the embedded infrared sources inside the clouds and/or YSOs in the N113 and N159W regions. The lower temperatures ($T_{\rm kin}$ $<$ 50 K) are measured at the outskirts of the H$_2$CO-bearing distributions of both N113 and N159W. It seems that the kinetic temperatures of the dense gas traced by para-H$_2$CO are weakly affected by the external sources of the H$\alpha$ emission. The non-thermal velocity dispersions of para-H$_2$CO are well correlated with the gas kinetic temperatures in the N113 region, implying that the higher kinetic temperature traced by para-H$_2$CO is related to turbulence on a $\sim$0.4 pc scale. The dense gas heating appears to be dominated by internal star formation activity, radiation, and/or turbulence. It seems that the mechanism heating the dense gas of the star-forming regions in the LMC is consistent with that in Galactic massive star-forming regions located in the Galactic plane.

# Introduction

Molecular gas is the fuel for star formation. Increasing evidence indicates that its physical properties affect star formation rate, spatial distribution, and essential properties of the next generation of stars, like elemental composition and initial mass function (e.g., (cite: Paumard2006; Kennicutt1998a; Kennicutt1998b; Klessen2007; Papadopoulos2011; Zhang2018; Tang2019)). Unfortunately, the most readily accessible molecular transitions, those of CO, suffer from radiative transfer effects such as high optical depths or subthermal excitation, and are not a reliable probe of these physical conditions. Furthermore, many molecules tracing the molecular mass in external galaxies (e.g., (cite: Gao2004a; Gao2004b; Wu2005; Zhang2014; Henkel2018; Li2021)), including CO, HCN, HCO$^+$, HNC, and CS, suffer from a coupled sensitivity to kinetic temperature and density, making them degenerately sensitive to high spatial densities and low kinetic temperatures or vice versa. Obtaining information about the individual physical conditions in these regions requires a molecular tracer that possesses singular sensitivity to kinetic temperature and that can then be used to also determine, in a second step, the number density of molecular hydrogen, $n$(H$_2$).

Formaldehyde (H$_2$CO), a slightly asymmetric rotor molecule, is a ubiquitous molecule in the interstellar medium (e.g., (cite: Downes1980; Bieging1982; Henkel1991; Zylka1992; Liszt2006; Mangum2008; Mangum2013; Mangum2019; Ao2013; Tang2013; Tang2014; Ginsburg2015; Ginsburg2016; Guo2016; Yan2019)). H$_2$CO can be formed on the surface of dust grains by successive hydrogenation of CO (CO$\rightarrow$HCO$\rightarrow$H$_2$CO) (cite: Watanabe2002; Woon2002; Hidaka2004; Yan2019). It is then released into the gas phase by shocks or UV heating and destroyed by photodissociation. Alternatively, gas phase formation is also possibly contributing to the total H$_2$CO abundance in Galactic environments such as the dark cloud TMC-1 (e.g., (cite: Soma2018)). CH$_3$OH, which is also the product of hydrogenation of CO on grain surfaces and is hardly formed in the gas phase, is deficient in the the Large Magellanic Cloud (LMC) (e.g., (cite: Shimonishi2016)). In the LMC where dust is less abundant than in the Galaxy, gas phase formation of H$_2$CO may thus be relevant.

H$_2$CO has a stable fractional abundance in star formation regions. Variations in fractional abundance of H$_2$CO rarely exceed one order of magnitude at various stages of star formation (e.g., (cite: Mangum1990; Mangum1993b; Caselli1993; Johnstone2003; Gerner2014; Tang2017a; Tang2017b; Tang2018b; Zhu2020)). As further demonstrated in recent studies of formaldehyde in the LMC, the fractional abundance of para-H$_2$CO in its star-forming regions has similar values as in Galactic regions of massive star formation (cite: Tang2017a; Tang2017b; Tang2018b). H$_2$CO has a rich variety of millimeter and submillimeter transitions which are a reliable probe to trace physical conditions of molecular clouds (e.g., (cite: Henkel1980; Henkel1983; Mangum1993a; Muhle2007; Mangum2008; Mangum2013; Mangum2019; Ginsburg2011; Tang2017a; Tang2017b; Tang2018a; Tang2018b)). Since the relative populations of the $K_{\rm a}$ ladders of H$_2$CO are governed by collisions, line ratios involving different $K_{\rm a}$ ladders are good tracers of the kinetic temperature (cite: Mangum1993a). Therefore, these H$_2$CO line ratios are an ideal thermometer for tracing the temperature of dense gas in low-metallicity galaxies with strong UV radiation (cite: Tang2017b).

The Large Magellanic Cloud is the closest star-forming galaxy to our Milky Way ($\sim$50 kpc, e.g., (cite: Pietrzynski2013; Pietrzynski2019)). In the LMC, the far-ultraviolet (FUV) radiation field is stronger than in the Milky Way while metallicities are lower (cite: Westerlund1990; Rolleston2002). The LMC provides an ideal laboratory for studying star formation, particularly massive star formation associated with its numerous stellar clusters in such an active low-metallicity galaxy. Previous observations of CO $J$ = 1–0 and 3–2 show that the higher gas temperatures in low/moderate density regions ($n$(H$_2$) $\sim$ a few $\times$ 10$^3$ cm$^{-3}$ in most cases) are correlated with stronger H$\alpha$ flux in giant molecular clouds of the LMC (cite: Minamidani2008; Minamidani2011). Further observations of CO $J$ = 4–3 to 12–11 indicate that the gas temperatures are high ($T_{\rm kin}$ \> 150 K) at densities $\sim$10$^3$ cm$^{-3}$ in active star-forming regions of the LMC (cite: Lee2016). These suggest that FUV heating may strongly impact on the molecular gas in low density regions ($n$(H$_2$) $<$ 10$^5$ cm$^{-3}$) of the LMC. In contrast, recent low-resolution (30$''$ or $\sim$7 pc) observations of para-H$_2$CO $J$ = 3–2 show that the kinetic temperatures of the dense gas ($n$(H$_2$) $\sim$ 10$^5$ cm$^{-3}$) are correlated with the ongoing massive star formation in the LMC (cite: Tang2017b). This suggests that inside the LMC the gas heating may be different between molecular cloud layers of lower and higher density. Although gas heating in low density regions of molecular clouds of the LMC can be expected to be due to the exciting OB stars of photon dominated regions (PDRs) (e.g., (cite: Kaufman1999; Lee2019)), the detailed relationship between the temperature of the dense gas and the star formation in the LMC is still under debate.

In this paper, we aim to map the kinetic temperature structure of two massive star-forming regions, N113 and N159W, in the LMC with the para-H$_2$CO triplet ($J_{\rm K_aK_c}$ = 3$_{03}$–2$_{02}$, 3$_{22}$–2$_{21}$, and 3$_{21}$–2$_{20}$) near 218.5 GHz and to investigate the gas heating process affecting the dense gas. In Sects. [2](#sect:Targets-observations-data-reduction) and [3](#sect:Results), we introduce our targets, observations of the para-H$_2$CO triplet, data reduction, and results. We discuss the resulting kinetic temperatures derived from para-H$_2$CO in Sect. [4](#sect:discussion). Our main conclusions are summarized in Sect. [5](#sect:summary). This paper is part of the "Kinetic temperature of massive star-forming molecular clumps measured with formaldehyde" series of studies exploring H$_2$CO as a probe of gas conditions in a variety of Galactic and extragalactic sources.

# Targets, observations, and data reduction

## Targets

The two massive star-forming regions, N113 and N159W, in the LMC were selected from previous single dish observations with the Atacama Pathfinder EXperiment telescope (APEX) (beam size $\sim$30$''$) in the course of which three transitions of para-H$_2$CO ($J$ = 3–2) near $\sim$218.5 GHz were detected (cite: Tang2017b). The dense gas kinetic temperatures of N113 and N159W derived from these para-H$_2$CO line ratios are 54 $\pm$ 7 K and 35 $\pm$ 4 K, respectively, on a scale of $\sim$7 pc (cite: Tang2017b).

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Central frequency | Bandwidth | Channel width | Beam size | Position angle | RMS |  |
|  | MHz | MHz | km s$^{-1}$ | "$\times$" | $^\circ$ | mJy beam$^{-1}$ |  |
| N113 | 217104.980 | 937.5 | 1.35 | 1.7$\times$1.3 | 60 | $\sim$2.0 |  |
|  | 218475.632 | 937.5 | 1.34 | 1.6$\times$1.3 | 61 | $\sim$2.0 |  |
|  | 230538.000 | 937.5 | 1.27 | 1.6$\times$1.2 | 61 | $\sim$2.0 |  |
| N159W | 217104.980 | 937.5 | 1.35 | 1.6$\times$1.3 | 55 | $\sim$2.0 |  |
|  | 218475.632 | 937.5 | 1.34 | 1.6$\times$1.3 | 56 | $\sim$2.0 |  |
|  | 230538.000 | 937.5 | 1.27 | 1.5$\times$1.3 | 56 | $\sim$2.0 |  |

Below follows a brief description of the selected targets.\
**N113**, located in the central part of the LMC, contains the most intense H$_2$O maser of the Magellanic Clouds (cite: Ellingsen2010), which indicates active star formation activity at an early stage. A large number of molecular transitions have been reported in N113 (e.g., (cite: Chin1996; Chin1997; Heikkila1998; Wang2009; Paron2014; Nishimura2016; Tang2017b; Sewilo2018; Sewilo2019)), while interferometric data from HCN, HCO$^+$, HNC, CH$_3$OH, and 1.3 mm continuum (cite: Wong2006; Seale2012; Sewilo2018; Sewilo2019) reveal a filamentary structure elongated roughly North-South with a length of $\sim$6 pc, including a few dense clumps with radius $\sim$0.5 pc.\
**N159W**, located at the southwestern tip of 30 Doradus, one of the most intense star-forming regions in the LMC, contains a large number of O- and B-type stars, embedded young stellar objects (YSOs), and ultracompact H II regions (e.g., (cite: Jones2005; Farina2009; Chen2010; Carlson2012)). It shows the brightest single-dish CO ($J$ = 1–0) peak in the LMC (e.g., (cite: Johansson1994; Fukui1999; Wong2011)) and has been frequently observed with a large number of molecular transitions (e.g., (cite: Johansson1994; Chin1996; Chin1997; Heikkila1998; Heikkila1999; Paron2014; Pineda2008; Lee2016; Nishimura2016; Tang2017b)). High resolution observations reveal a complex filamentary distribution of molecular gas (cite: Seale2012; Fukui2015). The gas temperature obtained from the NH$_3$(2,2)/(1,1) line ratio at $\sim$19$''$ resolution is $\sim$16 K (cite: Ott2010), which is only about half the temperatures derived from low resolution ($\sim$30$''$) para-H$_2$CO and the dust (cite: Tang2017b). After deriving kinetic temperatures from our high resolution H$_2$CO data, this difference will be discussed in more detail in Sect. [4.1](#sect:Comparison-Tk).

## Observations and data reduction

Our observations were carried out with the 12 m array of the Atacama Large Millimeter/submillimeter Array (ALMA) at Band 6 (Project: 2013.1.01136.S). Two Execution Blocks were conducted using 35 and 38 antennas in January 17 and April 8, 2015, respectively. The projected baseline lengths ranged from 15 to 349 m. The primary beam (FWHM) and the maximum recoverable scale are $\sim$$29''$ and $\sim$$13''$, respectively. The flux, bandpass, and phase calibrators were J0519-454, J0519-4546, and J0635-7516, respectively. Three spectral windows were centered on SiO (5–4), H$_2$CO (3$_{22}$–2$_{21}$), and CO (2–1), respectively, with a $\sim$937.5 MHz bandwidth and 960 channels for each band, yielding a channel width of 976.562 kHz, corresponding to 1.27–1.35 km s$^{-1}$. For the para-H$_2$CO triplet the synthesized beam size is $\sim$1$\,.\!\!^{\prime\prime}$6$\times$1$\,.\!\!^{\prime\prime}$3 ($\sim$0.4$\times$0.3 pc$^2$ at 50 kpc distance). The surveyed areas of N113 and N159W are centered on $\alpha_{2000}$ = 05:13:18.2, $\delta_{2000}$ = –69:22:25.0 and $\alpha_{2000}$ = 05:39:36.0, $\delta_{2000}$ =– 69:45:25.0, respectively. Detailed observational parameters are listed in Table [\[table:Observational_parameters\]](#table:Observational_parameters). The para-H$_2$CO $J_{\rm K_aK_c}$ = 3$_{03}$–2$_{02}$, 3$_{22}$–2$_{21}$, and 3$_{21}$–2$_{20}$ transitions have rest frequencies of 218.222, 218.475, and 218.760 GHz, respectively.

The data were calibrated using the CASA[^1] version 4.2.2 pipeline and were then imaged using CASA version 5.6.1. We imaged the calibrated data using a modified script associated with the data release. No primary beam correction has been applied for Figs. [1](#fig:N113+N159W-maps), [8](#fig:N113-channel-maps), and [9](#fig:N159W-channel-maps), but it has been applied for data analysis. Data analysis associated with spectral lines and images was performed using GILDAS[^2]. A typical rms noise level is $\sim$2.0 mJy beam$^{-1}$ for a 1.34 km s$^{-1}$ wide channel (see Table [\[table:Observational_parameters\]](#table:Observational_parameters)).

As mentioned in Sect. [2.1](#sect:Targets), the para-H$_2$CO (3–2) triplet has been observed before with the APEX 12 m telescope in N113 and N159W (cite: Tang2017b). We integrate all the emission within our ALMA data and compare it to the single-dish APEX 12 m data (beam size $\sim$30$''$). The fluxes recovered by our interferometer data are $\sim$75%, $\sim$80%, and $\sim$80% for para-H$_2$CO 3$_{03}$–2$_{02}$, 3$_{21}$–2$_{20}$, and 3$_{22}$–2$_{21}$, respectively, in N113. We find that $\sim$45%, $\sim$50%, and $\sim$50% of the para-H$_2$CO 3$_{03}$–2$_{02}$, 3$_{21}$–2$_{20}$, and 3$_{22}$–2$_{21}$ integrated flux observed by the APEX 12 m telescope is recovered for N159W by our ALMA data, respectively. These indicate that the para-H$_2$CO (3–2) triplets have, for a given source, similar missing flux percentages.

We note that our observational field centers of N113 and N159W have $\sim$6" and $\sim$13" offsets with respect to those used by (cite: Tang2017b), respectively. This may affect the comparison of our ALMA and single-dish data, especially for N159W. Our central positions are farther to the east (N113) and north (N159W) of the bulk of the emission shown in Fig. [1](#fig:N113+N159W-maps), so that part of the missing flux in our ALMA data may not be due to a lack of short baselines but due to the chosen field centers. In the optically thin regime, the critical density of the para-H$_2$CO 3$_{03}$–2$_{02}$ transition is $\sim$6$\times$10$^5$ cm$^{-3}$ at kinetic temperature 50 K (cite: Shirley2015), so the para-H$_2$CO (3–2) triplet probes compact emission regions. Considering that the para-H$_2$CO (3–2) triplet is a dense gas tracer and has similar missing flux percentages within N113 and N159W, the line ratios of the para-H$_2$CO (3–2) transitions are likely only weakly influenced by missing flux.

![](N113+N159W-map-H2CO.pdf)

# Results

## Overview

The integrated intensity distributions of the para-H$_2$CO triplet in N113 and N159W are shown in Fig. [1](#fig:N113+N159W-maps). The observed spectra from the H$_2$CO peaks in N113 and N159W are shown in Fig. [2](#fig:N113+N159W-Clump-spectrum). The location of the seven dense H$_2$CO clumps in each of the two massive star forming regions, selected by eye, are indicated in Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios), left panels, and are listed in Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters).

## Distribution of H$_2$CO

In both sources, N113 and N159W, para-H$_2$CO (3$_{03}$–2$_{02}$) shows extended distributions and clearly traces dense molecular structure, which is consistent with previous observational results probed with other gas tracers of e.g. $^{13}$CO, HCN, HNC, HCO$^+$ (cite: Wong2006; Seale2012; Fukui2015; Sewilo2018). The para-H$_2$CO 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ lines are only detected in the densest regions of N113 and N159W, and show less extended distributions than the para-H$_2$CO 3$_{03}$–2$_{02}$ transition.

The para-H$_2$CO 3$_{03}$–2$_{02}$ velocity channel maps of N113 and N159W are shown in Figs. [8](#fig:N113-channel-maps) and [9](#fig:N159W-channel-maps) of Appendix A, respectively. In N113, the filamentary structure, roughly elongated in North-South direction with a length of $\sim$25$''$, is prominent at low velocities, $\sim$232–236 km s$^{-1}$, while the northeastern clump (clump 1 following the nomenclature of Fig. [3](#fig:N113-Tk-H2CO-ratios) and Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters)) becomes visible at higher velocities, $\sim$236–238 km s$^{-1}$. In the N159W region, there appear to be two velocity components centered at $\sim$236 and $\sim$240 km s$^{-1}$ spreading from the northeast to the southwest.

## H$_2$CO line ratios

As mentioned in Sect. [1](#sect:Introduction), the intensity ratio of para-H$_2$CO lines involving different $K_{\rm a}$ ladders yields estimates of the kinetic temperature of the gas (cite: Mangum1993a). Generally, higher line ratios of para-H$_2$CO (3$_{22}$–2$_{21}$/3$_{03}$–2$_{02}$ and 3$_{21}$–2$_{20}$/3$_{03}$–2$_{02}$) indicate higher kinetic temperatures (e.g., (cite: Mangum1993a; Ao2013; Ginsburg2016; Tang2017b; Tang2018a; Tang2018b); see also Fig. [5](#fig:Tk-H2CO-ratios) for a more detailed view). Therefore, the ratio maps can be used as a proxy for relative kinetic temperature. The upper levels of the para-H$_2$CO 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ transitions have almost the same energy above the ground state ($E_{\rm u}$ $\simeq$ 68 K). They show similar spatial distributions (see Fig. [1](#fig:N113+N159W-maps)), similar line profiles (for brightness temperature, linewidth, and velocity in our observations; see Fig. [2](#fig:N113+N159W-Clump-spectrum) and also (cite: Tang2017a; Tang2017b; Tang2018a; Tang2018b)), and are often detected simultaneously in molecular clouds (e.g., (cite: Bergman2011; Wang2012; Lindberg2012; Ao2013; Immer2014; Trevino2014; Ginsburg2016; Ginsburg2017; Tang2017a; Tang2017b; Tang2018a; Tang2018b; Lu2017; Lu2021; Mangum2019)). Therefore, we use the averaged ratio para-H$_2$CO 0.5$\times$\[(3$_{22}$–2$_{21}$ + 3$_{21}$–2$_{20})$/3$_{03}$–2$_{02}$\] between para-H$_2$CO 3$_{22}$–2$_{21}$/3$_{03}$–2$_{02}$ and 3$_{21}$–2$_{20}$/3$_{03}$–2$_{02}$ for the first highly qualitative analysis below.

Averaged para-H$_2$CO (3–2) line ratio maps of N113 and N159W are shown in the left panels of Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios), respectively. The line ratios are calculated by velocity-integrated intensities where the para-H$_2$CO 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ lines are detected with signal-to-noise ratios (S/N) $\gtrsim$ 3$\sigma$. Para-H$_2$CO line ratios range from 0.10 to 0.38 with an average of 0.22 $\pm$ 0.01 (errors given here and elsewhere are standard deviations of the mean) in N113 and from 0.10 to 0.28 with an average of 0.20 $\pm$ 0.01 in N159W (see also Table [\[table:Parameters\]](#table:Parameters)). The lower ratios ($<$0.2) occur in the outskirts of the N113 and N159W H$_2$CO clouds (see Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios)). Higher ratios ($\gtrsim$0.2) associate with dense clumps, YSOs (or YSO candidates) (cite: Chen2010; Carlson2012), and/or H$_2$O masers (cite: Ellingsen2010) in N113 and N159W.

## Kinetic temperatures from H$_2$CO line ratios

According to Sect. [3.3](#sect:H$_2$CO-line-ratio), the para-H$_2$CO 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ transitions have almost the same upper-state energies above the ground state and similar observed line profiles. Para-H$_2$CO 3$_{22}$–2$_{21}$/3$_{03}$–2$_{02}$ and 3$_{21}$–2$_{20}$/3$_{03}$–2$_{02}$ ratios are both good thermometers to determine kinetic temperatures ($T_{\rm kin}$ \< 150 K; (cite: Mangum1993a; Tang2018b)) and show a similar behavior to kinetic temperature and spatial density at densities $n$(H$_2$) $\gtrsim$ 10$^5$ cm$^{-3}$ (cite: Lindberg2015; Tang2017a). Therefore, we continue to use the averaged para-H$_2$CO ratio 0.5$\times$\[(3$_{22}$–2$_{21}$ + 3$_{21}$–2$_{20})$/3$_{03}$–2$_{02}$\] to directly determine gas kinetic temperatures.

Using the RADEX[^3] non-LTE modeling program (cite: van2007) with collisional rate coefficients from (cite: Wiesenfeld2013), we modeled the relation between the gas kinetic temperature and the measured average of para-H$_2$CO 0.5$\times$\[(3$_{22}$–2$_{21}$ + 3$_{21}$–2$_{20})$/3$_{03}$–2$_{02}$\] ratios, adopting a 2.73 K background temperature, an average observational linewidth of 4.0 km s$^{-1}$, and column densities $N$(para-H$_2$CO) = 2.7$\times$10$^{12}$ and 3.7$\times$10$^{12}$ cm$^{-2}$ for N113 and N159W, respectively. The results are shown in Fig. [5](#fig:Tk-H2CO-ratios). The values of the para-H$_2$CO column density were obtained with APEX data (beam size $\sim$ 30$''$; (cite: Tang2017b)), which cover similar regions. Different column densities of para-H$_2$CO only weakly affect derived kinetic temperatures (see Fig. 3 in (cite: Tang2017b) or Fig. 4 in (cite: Tang2018a); this was also shown in Fig. 13 and discussed in Sect. 4.3.1 of (cite: Mangum1993a)) as long as all lines are optically thin. Considering that the relation between the gas temperature and the para-H$_2$CO line ratio may vary at different spatial densities (see Fig. 2 in (cite: Tang2017b)), we modeled it at spatial densities 10$^{4}$, 10$^{5}$, and 10$^{6}$ cm$^{-3}$ in Fig. [5](#fig:Tk-H2CO-ratios). It appears that $T_{\rm kin}$ at $n$(H$_2$) = 10$^{5}$ cm$^{-3}$ is consistently lower than values at 10$^{4}$ and 10$^{6}$ cm$^{-3}$ by $\lesssim$23% and $\lesssim$34%, respectively, for $T_{\rm kin}$ $\lesssim$ 100 K. Local thermodynamic equilibrium (LTE) is a good approximation for the H$_2$CO level populations under optically thin and high-density conditions (cite: Mangum1993a; Tang2017a; Tang2017b; Tang2018b). Following the method applied by (cite: Tang2017b) in their Eq. (2), we plot the relation between the LTE kinetic temperature, $T_{\rm LTE}$, and the para-H$_2$CO (3–2) line ratio in Fig. [5](#fig:Tk-H2CO-ratios). Apparently, $T_{\rm LTE}$ agrees well with $T_{\rm non-LTE}$ at volume densities $n$(H$_2$) $\sim$ 10$^{5}$ cm$^{-3}$ as long as $T_{\rm kin}$ $\lesssim$ 100 K. Previous observations show that para-H$_2$CO (3–2) is sensitive to gas temperature at density 10$^{5}$ cm$^{-3}$ (cite: Ginsburg2016; Immer2016; Tang2017b). The spatial density measured with para-H$_2$CO (3$_{03}$–2$_{02}$) and C$^{18}$O (2–1) in N113 and N159W is $n$(H$_2$) $\sim$ 10$^{5}$ cm$^{-3}$ on a size of $\sim$30$''$ (cite: Tang2017b). Therefore, here we adopt 10$^{5}$ cm$^{-3}$ as an averaged spatial gas density in the N113 and N159W regions.

![](N113+N159W-Clump-spectrum.pdf)

![](N113-map-H2CO-ratio-Tkin-Mach.pdf)

![](N159W-map-H2CO-ratio-Tkin-Mach.pdf)

We use the relation between kinetic temperature and para-H$_2$CO line ratios at averaged spatial density 10$^5$ cm$^{-3}$and averaged column densities of N113 and N159W (shown in Fig. [5](#fig:Tk-H2CO-ratios)) to convert ratio maps to temperature maps in Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios). The gas kinetic temperatures derived from the para-H$_2$CO line ratios are warm at density $n$(H$_2$) = 10$^5$ cm$^{-3}$, ranging from 28 to 105 K in N113 and from 29 to 68 K in N159W on a scale of $\sim$0.4 pc (see also Table [\[table:Parameters\]](#table:Parameters)). It seems that higher temperatures ($T_{\rm kin}$ $\gtrsim$ 50 K) associate with dense clumps, YSOs (or YSO candidates), and/or H$_2$O masers in N113 and N159W (see Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios)). Gas with lower temperatures ($T_{\rm kin}$ $<$ 50 K) is located at the outskirts of the H$_2$CO distributions of both N113 and N159W. The kinetic temperatures of the dense gas are high ($T_{\rm kin}$ = 44–96 K) in the dense H$_2$CO clumps (see Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters)), which is consistent with previous observational results measured with para-H$_2$CO ($J$=3–2 and 4–3) from dense clumps representing various evolutionary stages of high-mass star formation in the Galactic plane (cite: Tang2018b). The gas kinetic temperatures show apparent gradients in these dense H$_2$CO clumps of N113 and N159W (e.g., clumps 2, 3, 4, 5, and 7 in N113 and clumps 1, 4, and 6 in N159W; see Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios)) on a clump scale of $\sim$1 pc.

As mentioned in Sect. [2.1](#sect:Targets), the dense gas kinetic temperatures in N113 and N159W have been estimated with the same transitions of para-H$_2$CO ($J$=3–2) observed by the APEX 12-m telescope (beam size $\sim$30$''$; (cite: Tang2017b)). For a comparison with the lower resolution APEX data, we have therefore averaged our data for areas, where the presence of the dense gas shown in Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios) could be identified by the para-H$_2$CO 3$_{03}$–2$_{02}$ line. The averaged temperatures are 48 and 36 K in N113 and N159W, respectively, which are consistent with previous results in N113 (54 $\pm$ 7 K) and N159W (35 $\pm$ 4 K) obtained with the single-dish observations (cite: Tang2017b).

Previous observations toward the Galactic central molecular zone (CMZ) clouds and dense massive star-forming clumps in the Galactic plane show that the opacities of para-H$_2$CO ($J$=3–2) lines influence only weakly the measurements of gas kinetic temperature (cite: Ginsburg2016; Immer2016; Tang2018b). Nevertheless, a major caveat in our discussion are the poorly known opacities of para-H$_2$CO ($J$=3–2) lines in N113 and N159W. While the para-H$_2$CO 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ lines, being much weaker than the 3$_{03}$–2$_{02}$ line, appear to be optically thin, this is not necessarily the case for our strongest emitter, the 3$_{03}$–2$_{02}$ transition. If this line were optically thick in the molecular cores we have observed, line ratios would be too close to unity, and we would overestimate, relative to the optically thin case, the para-H$_2$CO 0.5$\times$\[(3$_{22}$–2$_{21}$ + 3$_{21}$–2$_{20})$/3$_{03}$–2$_{02}$\] intensity ratios and kinetic temperatures. This implies that in case of saturation we would obtain upper limits to the kinetic temperature only. This could easily mimic the high temperatures in the cores and the lower temperatures in the optically thin outskirts of the N113 and N159W clouds, we have mentioned above, possibly providing a good agreement with the low kinetic temperature derived from ammonia (beam size 18$\,.\!\!^{\prime\prime}$6$\times$15$\,.\!\!^{\prime\prime}$7; (cite: Ott2010)), since the gas traced by ammonia presumably resides in a well shielded highly obscured cloud core.

A first estimate of optical depth can be attained by a comparison of para-H$_2$CO 3$_{03}$–2$_{02}$ main beam brightness temperatures with the temperatures derived from the dust and from the line temperature ratios. On our 0.4 pc scale, observed main beam brightness temperatures should be close to the real brightness temperatures of the emission (e.g. (cite: Tang2018a)), which should reach values of order of 16 K (the $T_{\rm kin}$ value from the NH$_3$(2,2)/(1,1) line ratio; (cite: Ott2010)) or higher to reveal strong indications of saturation. Converting with $T_{\rm mb}$ = $S$ $\times$ $\lambda$$^2$/(2.65 $\times$ $\theta_b$$^2$) ($T_{\rm mb}$: main beam brightness temperature in units of K; $S$: flux density in units of Jy; $\lambda$: wavelength in units of cm; $\theta_b$: our beam size in units of arcmin) the flux density scale into units of main beam brightness temperature and accounting for typical total linewidths of $\sim$4.0 km s$^{-1}$ in case of N113 and N159W (see Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters)), we obtain peak temperatures of only $\sim$2.5 K. This is well below the low ammonia temperature from (cite: Ott2010) and indicates either highly subthermal excitation with potentially saturated para-H$_2$CO 3$_{03}$–2$_{02}$ line emission or a purely optically thin scenario.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Source | Clump | Offset | Transition | $\int$Flux d$v$ | $V_{\rm LSR}$ | FWHM | Flux | $\sigma_{\rm T}$ | $\sigma_{\rm NT}$ | $c_{\rm s}$ | $\mathcal{M}$ | $T_{\rm kin}$ | $T_{\rm turb}$ |  |  |  |
|  |  | " , " |  | Jy km s$^{-1}$ | km s$^{-1}$ | km s$^{-1}$ | Jy | km s$^{-1}$ | km s$^{-1}$ | km s$^{-1}$ |  | K | K |  |  |  |
| N113 | 1 | –2.4, 4.0 | 3$_{03}$–2$_{02}$ | 0.530 (0.006) | 236.9 (0.1) | 3.3 (0.1) | 0.150 | 0.11 (0.01) | 1.41 (0.02) | 0.40 (0.02) | 3.5 | 50.4 (5.1) | 50 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.110 (0.006) | 236.9 (0.1) | 3.0 (0.2) | 0.035 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.114 (0.007) | 236.7 (0.1) | 3.4 (0.3) | 0.032 |  |  |  |  |  |  |  |  |  |
|  | 2 | –5.4, 3.8 | 3$_{03}$–2$_{02}$ | 1.226 (0.019) | 233.5 (0.1) | 5.8 (0.1) | 0.198 | 0.16 (0.01) | 2.46 (0.04) | 0.56 (0.02) | 4.4 | 96.2 (5.8) | 93 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.429 (0.006) | 233.3 (0.1) | 5.2 (0.1) | 0.077 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.435 (0.008) | 233.4 (0.1) | 5.2 (0.1) | 0.078 |  |  |  |  |  |  |  |  |  |
|  | 3 | –4.0, 1.2 | 3$_{03}$–2$_{02}$ | 1.258 (0.005) | 233.7 (0.1) | 5.5 (0.1) | 0.216 | 0.13 (0.01) | 2.32 (0.01) | 0.47 (0.01) | 5.0 | 67.7 (2.6) | 67 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.350 (0.008) | 233.8 (0.1) | 4.8 (0.1) | 0.068 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.345 (0.007) | 233.9 (0.1) | 5.0 (0.1) | 0.065 |  |  |  |  |  |  |  |  |  |
|  | 4 | –2.8, –2.0 | 3$_{03}$–2$_{02}$ | 0.886 (0.007) | 232.4 (0.1) | 4.8 (0.1) | 0.173 | 0.12 (0.01) | 2.04 (0.02) | 0.44 (0.01) | 4.6 | 60.7 (2.3) | 60 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.231 (0.006) | 232.3 (0.1) | 4.2 (0.1) | 0.051 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.225 (0.005) | 232.2 (0.1) | 4.4 (0.1) | 0.048 |  |  |  |  |  |  |  |  |  |
|  | 5 | –4.2, –5.2 | 3$_{03}$–2$_{02}$ | 0.409 (0.005) | 233.9 (0.1) | 3.6 (0.1) | 0.108 | 0.11 (0.01) | 1.52 (0.02) | 0.38 (0.01) | 4.0 | 44.0 (2.5) | 44 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.090 (0.006) | 234.2 (0.2) | 4.6 (0.4) | 0.019 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.073 (0.006) | 234.2 (0.1) | 3.2 (0.3) | 0.022 |  |  |  |  |  |  |  |  |  |
|  | 6 | –3.8, –8.6 | 3$_{03}$–2$_{02}$ | 0.203 (0.005) | 234.9 (0.1) | 3.3 (0.1) | 0.057 | ... | ... | ... | ... | ... | ... |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | ... |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | ... |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 7 | –5.4, –13.4 | 3$_{03}$–2$_{02}$ | 0.710 (0.010) | 234.3 (0.1) | 3.0 (0.1) | 0.220 | 0.12 (0.01) | 1.28 (0.02) | 0.41 (0.02) | 3.1 | 52.5 (4.5) | 52 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.159 (0.012) | 234.5 (0.1) | 2.9 (0.3) | 0.052 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.165 (0.017) | 234.3 (0.2) | 3.2 (0.4) | 0.049 |  |  |  |  |  |  |  |  |  |
| N159W | 1 | 0.8, 0.4 | 3$_{03}$–2$_{02}$ | 0.245 (0.003) | 238.4 (0.1) | 1.8 (0.1) | 0.128 | 0.11 (0.01) | 0.79 (0.03) | 0.41 (0.01) | 1.9 | 51.8 (4.4) | 51 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.048 (0.003) | 238.0 (0.1) | 2.2 (0.1) | 0.020 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.045 (0.003) | 238.3 (0.1) | 2.0 (0.2) | 0.021 |  |  |  |  |  |  |  |  |  |
|  | 2 | 10.4, 0.4. | 3$_{03}$–2$_{02}$ | 0.114 (0.005) | 239.7 (0.1) | 1.6 (0.4) | 0.066 | ... | ... | ... | ... | ... | ... |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | ... |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | ... |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 3 | 7.8, –1.2 | 3$_{03}$–2$_{02}$ | 0.141 (0.006) | 236.0 (0.1) | 3.1 (0.2) | 0.043 | 0.12 (0.01) | 1.31 (0.07) | 0.43 (0.03) | 3.1 | 56.0 (9.2) | 55 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.030 (0.006) | 236.4 (0.3) | 2.6 (0.6) | 0.011 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.035 (0.004) | 236.3 (0.2) | 2.8 (0.4) | 0.012 |  |  |  |  |  |  |  |  |  |
|  | 4 | 5.0, –2.0 | 3$_{03}$–2$_{02}$ | 0.309 (0.006) | 238.0 (0.1) | 4.3 (0.1) | 0.068 | 0.13 (0.01) | 1.86 (0.05) | 0.46 (0.01) | 4.0 | 65.5 (5.1) | 65 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.104 (0.005) | 238.5 (0.1) | 5.9 (0.4) | 0.017 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.081 (0.006) | 238.3 (0.2) | 4.5 (0.4) | 0.017 |  |  |  |  |  |  |  |  |  |
|  | 5 | 5.2, –10.4 | 3$_{03}$–2$_{02}$ | 0.527 (0.013) | 235.4 (0.1) | 5.4 (0.2) | 0.091 | 0.11 (0.01) | 2.32 (0.08) | 0.38 (0.01) | 6.1 | 45.2 (4.0) | 46 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.101 (0.008) | 234.8 (0.2) | 4.8 (0.4) | 0.020 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.115 (0.008) | 234.8 (0.2) | 4.6 (0.4) | 0.023 |  |  |  |  |  |  |  |  |  |
|  | 6 | 3.4, –13.0 | 3$_{03}$–2$_{02}$ | 0.914 (0.009) | 236.9 (0.1) | 4.5 (0.1) | 0.190 | 0.11 (0.01) | 1.94 (0.03) | 0.41 (0.01) | 4.8 | 51.3 (3.3) | 51 |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | 0.189 (0.008) | 237.0 (0.1) | 3.6 (0.2) | 0.049 |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | 0.200 (0.011) | 237.0 (0.1) | 3.8 (0.3) | 0.049 |  |  |  |  |  |  |  |  |  |
|  | 7 | –0.6, –16.4 | 3$_{03}$–2$_{02}$ | 0.272 (0.013) | 235.8 (0.1) | 3.1 (0.2) | 0.081 | ... | ... | ... | ... | ... | ... |  |  |  |
|  |  |  | 3$_{22}$–2$_{21}$ | ... |  |  |  |  |  |  |  |  |  |  |  |  |
|  |  |  | 3$_{21}$–2$_{20}$ | ... |  |  |  |  |  |  |  |  |  |  |  |  |

Table notes: Offsets relative to our reference positions for N113 and N159W (see Figs. [1](#fig:N113+N159W-maps), [3](#fig:N113-Tk-H2CO-ratios), and [4](#fig:N159W-Tk-H2CO-ratios)). Velocity-integrated flux, $\int$Flux d$v$, local standard of rest velocity, $V_{\rm LSR}$, full width at half maximum line width (FWHM), and peak flux (Flux) were obtained from Gaussian fits using CLASS as part of the GILDAS software. For the thermal and non-thermal velocity dispersions, $\sigma_{\rm T}$ and $\sigma_{\rm NT}$, the sound velocity $c_{\rm s}$, the Mach number $\mathcal{M}$, the kinetic temperature $T_{\rm kin}$, and the turbulent temperature $T_{\rm turb}$, see Sects. [3.5](#Sec:Non-thermal motions) and [4.3](#Sec:Turbulence). Values in parenthesis are uncertainties.

+---------------------------------+---------------------------------------+---+--------------------------------------+
| Parameter                       | N113                                  |   | N159W                                |
+:================================+:==========:+:======:+:===============:+:=:+:=========:+:======:+:===============:+
| 2-4                             | Range      | Median | Mean            |   | Range     | Median | Mean            |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+
| H$_2$CO line ratio              | 0.10–0.38  | 0.21   | 0.22 $\pm$ 0.01 |   | 0.10–0.28 | 0.20   | 0.20 $\pm$ 0.01 |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+
| $T_{\rm gas}$ /K                | 27.6–105.4 | 48.5   | 51.4 $\pm$ 0.4  |   | 28.7–67.8 | 47.5   | 47.6 $\pm$ 0.3  |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+
| $\sigma_{\rm T}$ / km s$^{-1}$  | 0.08–0.16  | 0.11   | 0.11 $\pm$ 0.01 |   | 0.09–0.13 | 0.11   | 0.11 $\pm$ 0.01 |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+
| $\sigma_{\rm NT}$ / km s$^{-1}$ | 0.93–2.76  | 1.64   | 1.69 $\pm$ 0.01 |   | 0.57–2.74 | 1.85   | 1.74 $\pm$ 0.02 |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+
| $c_{\rm s}$ / km s$^{-1}$       | 0.30–0.58  | 0.40   | 0.40 $\pm$ 0.01 |   | 0.31–0.47 | 0.39   | 0.39 $\pm$ 0.01 |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+
| $\mathcal{M}$                   | 2.3–6.2    | 4.2    | 4.2 $\pm$ 0.1   |   | 1.6–8.3   | 4.5    | 4.5 $\pm$ 0.1   |
+---------------------------------+------------+--------+-----------------+---+-----------+--------+-----------------+

Table notes: For the meaning of the parameters in column 1, see Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters). The errors shown in columns 4 and 7 are the standard deviations of the mean.

To discriminate between these two possibilities, we used again the RADEX non-LTE program (cite: van2007). Setting $T_{\rm kin}$ to 16 K, the low value derived by (cite: Ott2010) from ammonia, and a linewidth of 3  km s$^{-1}$ we can reproduce the $T_{\rm mb}$ (H$_2$CO 3$_{03}$–2$_{02}$) line intensity of $\sim$2.5 K with $N$(para-H$_2$CO) = 1.4 $\times$ 10$^{14}$ cm$^{-2}$, but the resulting para-H$_2$CO 0.5 $\times$ \[(3$_{22}$–2$_{21}$ + 3$_{21}$–2$_{20}$)/3$_{03}$–2$_{02}$\] line ratio is $\sim$0.04, far below and thus inconsistent with the obtained data. At $T_{\rm kin}$ $\sim$ 50 K, however, $N$(para-H$_2$CO) $\sim$5$\times$10$^{13}$ cm$^{-2}$ leads to $T_{\rm mb}$ (H$_2$CO 3$_{03}$–2$_{02}$) $\sim$ 2.5 K and line ratios of order 0.23–0.24. In this case the para-H$_2$CO 3$_{03}$–2$_{02}$ line is slightly optically thick ($\tau$ $\sim$ 1.1), while the weaker 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ transitions are characterized by $\tau$ $\sim$ 0.3. Compared to the optically thin case shown by Fig. [5](#fig:Tk-H2CO-ratios), this leads to a slight overestimate of $T_{\rm kin}$. Adopting the optically thin scenario, line ratios of 0.25–0.30 lead to kinetic temperatures of 55 to 70 K instead of the 50 K adopted in the non-LTE model also accounting for line saturation effects. Interestingly, even H$_2$CO 3$_{03}$–2$_{02}$ line opacities of order 5–10 do not lead to larger inaccuracies (see Fig. G. 2 in (cite: Immer2016)). While increasing line saturation has a tendency to yield line intensity ratios closer to unity, this trend is not seen in this case because excitation temperatures of the H$_2$CO 3$_{22}$–2$_{21}$ and 3$_{21}$–2$_{20}$ transitions are then significantly below that of the H$_2$CO 3$_{03}$–2$_{02}$ transition. To summarize: While our $T_{\rm kin}$ values toward the cloud cores might be overestimated, they are not grossly overestimated and still clearly favor values well in excess of the 16 K derived from ammonia.

In Galactic dense massive star-forming clumps the para-H$_2$CO 3$_{03}$–2$_{02}$ line tends to be optically thin (cite: Tang2018b). Since dust is less prevalent in the LMC than in the Galaxy (e.g. (cite: Wang2009)) leading to reduced shielding, we may see denser regions with H$_2$CO in the LMC than in the Galaxy, again not supporting the highly subthermal low kinetic temperature excitation scenario mentioned above. On the other hand, N113 and N159W are the most intense star-forming regions of the LMC (e.g., (cite: Wang2009; Lee2016)), which may yield particularly large H$_2$CO column densities. The peak column densities $N$(para-H$_2$CO) obtained from the para-H$_2$CO (3$_{03}$–2$_{02}$) brightness temperatures of dense H$_2$CO clumps in N113 and N159W (see Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters)) using the method of (cite: Tang2017a) range from 0.7 to 9.0$\times$10$^{13}$ cm$^{-2}$ with an average of $\sim$4.0$\times$10$^{13}$ cm$^{-2}$ at a density of 10$^5$ cm$^{-3}$ and from 0.3 to 3.8$\times$10$^{13}$ cm$^{-2}$ with an average of $\sim$1.4$\times$10$^{13}$ cm$^{-2}$ at a density of 10$^6$ cm$^{-3}$, which are a few times higher than averaged results obtained from entire regions with the APEX telescope (cite: Tang2017b).

![](Tk-ratio.pdf)

## Thermal and non-thermal motions

Using the kinetic temperatures derived from the para-H$_2$CO line ratios, we can derive thermal and non-thermal linewidths i.e. $\sigma_{\rm T}=\sqrt{\frac{kT_{\rm kin}}{m_{\rm H_2CO}}}$ and $\sigma_{\rm NT}=\sqrt{\frac{\Delta v^2}{8{\rm ln}2}-\sigma^2_{\rm T}}\thickapprox\Delta v/2.355$, where $k$ is the Boltzmann constant, $T_{\rm kin}$ is the kinetic temperature of the gas, $m_{\rm H_2CO}$ is the mass of the formaldehyde molecule, and $\Delta v$ is the measured FWHM linewidth of para-H$_2$CO 3$_{03}$–2$_{02}$ (cite: Pan2009). Thermal and non-thermal linewidth ranges are listed in Table [\[table:Parameters\]](#table:Parameters). Thermal and non-thermal linewidths of the individual dense clumps are given in Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters). The thermal linewidth is significantly smaller than the non-thermal linewidth in N113 and N159W, which indicates that the dense gas traced by para-H$_2$CO is dominated by non-thermal motions. This agrees with previous measurements derived from para-H$_2$CO (3–2 and 4–3) in the Galactic star-forming region OMC-1 and massive clumps of the Galactic disk (cite: Tang2017a; Tang2018a; Tang2018b). Distributions of the non-thermal linewidth in N113 and N159W are shown in Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios), respectively. They may suggest that the higher non-thermal linewidths ($\sigma_{\rm NT}$ \> 1.5 km s$^{-1}$) associate with the dense clumps and the lower non-thermal linewidths ($\sigma_{\rm NT}$ $\lesssim$ 1.5) are located in the outskirts of the dense clumps in our two massive star-forming regions, indicating that the dense gas traced by para-H$_2$CO is strongly influenced by star-forming activity.

![](N113_N159W_H2CO+Ha+um+mm.pdf)

Distributions of the Mach number ($\mathcal{M}=\sigma_{\rm NT}/c_{\rm s}$, where $c_{\rm s}$=$\sqrt{\frac{kT_{\rm kin}}{\mu m_{\rm H}}}$ is the sound speed, $\mu$ = 2.37 is the mean molecular weight for molecular clouds, and $m_{\rm H}$ is the mass of the hydrogen atom) in N113 and N159W are shown in Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios), right panels, respectively. The Mach numbers of the individual dense clumps in N113 and N159W are listed in Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters). The Mach numbers range from 2.3 to 6.2 with an average of 4.2 $\pm$ 0.1 in N113 and from 1.6 to 8.3 with an average of 4.5 $\pm$ 0.1 in N159W (see also Table [\[table:Parameters\]](#table:Parameters)). This suggests that supersonic non-thermal motions (e.g., turbulence, outflows, shocks, and/or magnetic fields) are dominant in the dense gas traced by H$_2$CO. Locations that are situated in the outskirts of the clumps of N113 and in the outer regions of the northern clumps of N159W (see Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios)), have low Mach numbers ($\mathcal{M}$ $\lesssim$ 3.5). The distribution of Mach numbers may suggest apparent gradients from southeast to northwest along clumps 5 and 6 of N159W (see Fig. [4](#fig:N159W-Tk-H2CO-ratios)). Meanwhile, there is a YSO (or YSO candidate) located in the eastern region of these clumps. This may imply that dense gas probed by para-H$_2$CO may be influenced by this YSO (or YSO candidate). Higher Mach numbers ($\mathcal{M}$ \> 3.5) are associated with the dense clumps in N113 and N159W, again suggesting that dense gas traced by H$_2$CO is strongly influenced by non-thermal motions (e.g., outflows and shocks) in these regions. The averaged Mach numbers in N113 and N159W are consistent with previous observational results in Galactic massive clumps on scales of $\sim$0.1–1.8 pc (mean value $\sim$4.2 obtained from para-H$_2$CO (3–2 and 4–3); (cite: Tang2018b)), but are higher than the values measured with the same transitions of para-H$_2$CO (3–2) in OMC-1 on a scale of $\sim$0.06 pc (mean value $\sim$2.3; (cite: Tang2018a)). We have smoothed the OMC-1 para-H$_2$CO (3–2) data to a linear resolution of 0.4 pc. The derived Mach numbers are 3.0 and 3.5 in the Orion KL and Orion South regions, respectively, which is still slightly lower than the values in N113 and N159W.

One should note that para-H$_2$CO (3$_{03}$–2$_{02}$) linewidths in the northern edges of clump 1 and 2 of N113 and in the outskirts of clump 1 and 4 of N159W are narrow \<3.0 km s$^{-1}$ (see Figs. [2](#fig:N113+N159W-Clump-spectrum), [3](#fig:N113-Tk-H2CO-ratios), and [4](#fig:N159W-Tk-H2CO-ratios)), which is corresponding to only 2–3 channels of our H$_2$CO data. Furthermore, there are two velocity components around clump 1 of N113 and in the northern region of the clump 4 of N159W (see Figs. [8](#fig:N113-channel-maps) and [9](#fig:N159W-channel-maps)). For two velocity components the typical linewidths are $\sim$2–3 and $\sim$4–6 km s$^{-1}$ in these regions of N113 and N159W. Our observational set can not well identify the velocity components with narrow linewidths using Gaussian profiles in these regions. Therefore, the non-thermal linewidths and the Mach numbers are likely overestimated in these regions. For the locations with two velocity components in N113 and N159W, the non-thermal linewidths and the Mach number are weighted with para-H$_2$CO (3$_{03}$–2$_{02}$) integrated intensity in Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios).

+------------+-----------------------------------------------------------------------+---+---------------------------------------------+---+---------------------------------------------+---+---------------------------------------------+---+---+---+
|            | YSO                                                                   |   | $R$ = 0.2 pc                                |   | $R$ = 0.4 pc                                |   | $R$ = 1.0 pc                                |   |   |   |
+:==========:+:==============:+:=================:+:================================:+:=:+:==================:+:======================:+:=:+:==================:+:======================:+:=:+:==================:+:======================:+:=:+:=:+:=:+
| 2-4 Source | R.A.(J2000)    | DEC.(J2000)       | Luminosity                       |   | $T_{\rm kin}$(Rad) | $T_{\rm kin}$(H$_2$CO) |   | $T_{\rm kin}$(Rad) | $T_{\rm kin}$(H$_2$CO) |   | $T_{\rm kin}$(Rad) | $T_{\rm kin}$(H$_2$CO) |   |   |   |
+------------+----------------+-------------------+----------------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+---+---+
| 6-7        | $^h$ $^m$ $^s$ | $^\circ$ $'$ $''$ | $\times$10$^5$ ${\rm L}_{\odot}$ |   | K                                           |   | K                                           |   | K                                           |   |   |   |
+------------+----------------+-------------------+----------------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+---+---+
| N113       | 05:13:17.28    | –69:22:36.7       | 0.16                             |   | 36                 | 35                     |   | 27                 | 45                     |   | 19                 | 34                     |   |   |   |
+------------+----------------+-------------------+----------------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+---+---+
|            | 05:13:17.69    | –69:22:25.0       | 1.26                             |   | 54                 | 48                     |   | 41                 | 57                     |   | 29                 | 53                     |   |   |   |
+------------+----------------+-------------------+----------------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+---+---+
| N159W      | 05:39:37.09    | –69:45:36.7       | 0.82                             |   | 50                 | 56                     |   | 37                 | 44                     |   | 26                 | 72                     |   |   |   |
+------------+----------------+-------------------+----------------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+---+---+
|            | 05:39:37.56    | –69:45:25.3       | 2.40                             |   | 61                 | 69                     |   | 46                 | 54                     |   | 32                 | 41                     |   |   |   |
+------------+----------------+-------------------+----------------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+--------------------+------------------------+---+---+---+

Table notes: The young stellar objects or candidates and their luminosity are taken from (cite: Chen2010), (cite: Sewilo2010), and (cite: Carlson2012).

# Discussion

## Comparison of temperatures obtained from H$_2$CO, CO, and NH$_3$

Observations of CO $J$ = 1–0 to 3–2 indicate that the molecular gas traced by CO in lower density regions ($n$(H$_2$) $<$ 10$^5$ cm$^{-3}$) may be strongly influenced by the external FUV emission irradiating giant molecular clouds of the LMC on a scale of $\sim$10 pc (cite: Minamidani2008; Minamidani2011). The physical and chemical processes in these regions such as formation and destruction of molecules as well as ionization are dominated by the intense FUV field, which has been modeled as PDRs (e.g., (cite: Kaufman1999; Minamidani2011; Lee2016; Lee2019)). The gas temperature is $T_{\rm kin}$ \> 150 K at densities $\sim$10$^3$ cm$^{-3}$ derived from multitransition data of CO in N159W on a scale of $\sim$10 pc (cite: Lee2016). Our results determined from para-H$_2$CO line ratios range from 29 to 68 K with an average of 47.6 $\pm$ 0.3 K at density 10$^5$ cm$^{-3}$ on a scale of 0.4 pc (see Table [\[table:Parameters\]](#table:Parameters)), which are much lower than values obtained from CO at lower density and even may have to be slightly modified to the lower side to account for moderate saturation effects (see Sect. [3.4](#sect:Kinetic-temperature)). This indicates that para-H$_2$CO and CO trace different kinetic temperature layers in N159W. There is no available gas temperature derived from multitransition data of CO in N113, so we can not compare it with our para-H$_2$CO results.

We did not find any evidence for the low $T_{\rm kin}$ value ($\sim$16 K) determined from the NH$_3$ (2,2)/(1,1) line ratio by (cite: Ott2010). This is interpreted in terms of a highly embedded extremely obscured dense molecular gas component, which we do not see in H$_2$CO. A similar situation has also been encountered in M 82 (cite: Weiss2001; Muhle2007), where ammonia suggests $T_{\rm kin}$ $\sim$ 60 K, while H$_2$CO represents gas with temperatures well in excess of 100 K. We get moderately high $T_{\rm kin}$ values derived from H$_2$CO in the cores but (cite: Ott2010) obtain a low $T_{\rm kin}$ value determined from NH$_3$, presumably also from a core. Ammonia has a particularly low energy threshold for photodissociation ($\sim$4.1 eV; (cite: Weiss2001)). Low metallicity environments with low nitrogen abundance and strong UV radiation (e.g., (cite: Westerlund1990; Chin1997; Rolleston2002; Wang2009; Ott2010)) in the LMC may allow ammonia to survive only in the most UV-shielded regions, leading to a low fractional NH$_3$ abundance and a low kinetic temperature of the NH$_3$ emitting gas (cite: Tang2017b). It could be explained in the sense, that NH$_3$ is only there, where no protostar has yet heated its environment. In the outskirts, $T_{\rm kin}$ values from H$_2$CO are low, but CO suggests that there temperatures are high. This might be explained by the idea that even the H$_2$CO outskirts are far inside the volume of the CO emitting gas.

## Radiative heating

We compare para-H$_2$CO (3$_{03}$–2$_{02}$) integrated intensity distributions with the H$\alpha$ emission (observed with the UM/CTIO Curtis Schmidt telescope; (cite: Smith1998)), *Spitzer* 8.0 $\mu$m (cite: Meixner2006), and 1.3 mm continuum (observed with ALMA Band 6; (cite: Fukui2015; Sewilo2018)) emission of N113 and N159W in Fig. [6](#fig:N113_N159W_H2CO+Ha+5.8um+1.3mm). Obviously, the spatial distributions of para-H$_2$CO (3$_{03}$–2$_{02}$) and H$\alpha$ emission are not well correlated in the two massive star-forming regions. This suggests that dense gas traced by para-H$_2$CO may only be weakly affected by the stars exciting the H$\alpha$ emission in N113 and N159W. Such offsets between molecular and H$\alpha$ emissions are seen in evolved systems (e.g., (cite: Fukui2010)), where newly formed massive stars have already dispersed a part of the original molecular gas. The para-H$_2$CO (3$_{03}$–2$_{02}$) integrated intensity distributions agree much better with the *Spitzer* 8.0 $\mu$m emission excited by young massive stars in the N113 and N159W regions (see Fig. [6](#fig:N113_N159W_H2CO+Ha+5.8um+1.3mm)). The para-H$_2$CO (3$_{03}$–2$_{02}$) integrated intensity distribution agrees best with the 1.3 mm continuum emission in N113 and N159W, including the dense molecular structure and dust emission peaks (see Fig. [6](#fig:N113_N159W_H2CO+Ha+5.8um+1.3mm)), which implies that H$_2$CO associates with the dense gas traced by the dust emission. This is consistent with previous observational results in our Galactic massive star-forming regions at various evolutionary stages (cite: Immer2014; Tang2017a; Tang2018a; Tang2018b).

As mentioned, there is no spatial correlation between the dense gas traced by para-H$_2$CO and the H$\alpha$ distributions in N113 and N159W (see Fig. [6](#fig:N113_N159W_H2CO+Ha+5.8um+1.3mm)). There also appears to be no significant correlation between the gas temperature structures derived from para-H$_2$CO line ratios and the H$\alpha$ emission distribution in these two regions (Figs. [3](#fig:N113-Tk-H2CO-ratios), [4](#fig:N159W-Tk-H2CO-ratios), and [6](#fig:N113_N159W_H2CO+Ha+5.8um+1.3mm)). These findings indicate that dense gas traced by H$_2$CO is weakly affected by the external FUV radiation in N113 and N159W. The dense molecular gas ($\gtrsim$ 10$^5$ cm$^{-3}$) may be effectively shielded by the lower density molecular gas envelopes in the massive star-forming regions of the LMC.

Previous observations of e.g. H$_2$CO, NH$_3$, CH$_3$CN, CH$_3$CCH, or CH$_3$OH in Galactic massive star-forming regions (cite: Lu2014; Giannetti2017; Tang2018a; Tang2018b; Gieser2021) suggest internal radiative heating of embedded infrared sources of their surrounding dense gas. Present observations of H$_2$CO in massive star-forming regions of the LMC imply that the kinetic temperatures traced by para-H$_2$CO (3–2) transitions in dense regions ($\sim$10$^5$ cm$^{-3}$) are correlated with the ongoing massive star formation (cite: Tang2017b). As mentioned in Sect. [3.4](#sect:Kinetic-temperature), it appears that high gas temperatures obtained from para-H$_2$CO line ratios associate with dense clumps, YSOs (or YSO candidates), and/or H$_2$O masers in N113 and N159W regions (see Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios)). This indicates that the warm dense gas traced by para-H$_2$CO is influenced by radiation from internal embedded infrared sources and/or nearby YSOs in the low-metallicity environment of the LMC.

We determine the gas temperature in regions heated by YSOs following the modified Stefan-Boltzmann blackbody radiation law, adjusting the emissivity of dust grains smaller than the wavelength at the characteristic blackbody temperature (cite: Wiseman1998; Tang2018a), $$\begin{eqnarray}
\label{equation:radiation}
T_{\rm kin}=2.7\times(\frac{L}{{\rm L}_{\odot}})^{1/5}(\frac{R}{\rm pc})^{-2/5}~{\rm K},
\end{eqnarray}$$ where the luminosity $L$ is in ${\rm L}_{\odot}$ and the distance $R$ is in parsecs. Four YSOs (or YSO candidates) with luminosities of 0.16, 0.82, 1.26, and 2.40 $\times$ 10$^5$ ${\rm L}_{\odot}$ are found in N113 and N159W (cite: Chen2010; Sewilo2010; Carlson2012). Assuming these YSOs (or YSO candidates) are the dominant sources at their locations, the derived gas temperatures at radii of 0.2, 0.4, and 1.0 pc from Eq. ([\[equation:radiation\]](#equation:radiation)) are listed in Table [\[table:Tkin-YSO\]](#table:Tkin-YSO). Measured gas temperatures around the four young stellar objects or candidates derived from para-H$_2$CO line ratios are also listed in Table [\[table:Tkin-YSO\]](#table:Tkin-YSO), which agrees well with the results obtained from the radiation law at a radius of 0.2 pc. This indicates that dense gas traced by H$_2$CO is significantly influenced by radiation from YSOs (or YSO candidates). One should note that the distances among YSOs (or YSO candidates), H$_2$O masers, and 1.3 mm dust emission peaks are approximately $\sim$1 pc in the N113 and N159W regions (see Figs. [3](#fig:N113-Tk-H2CO-ratios), [4](#fig:N159W-Tk-H2CO-ratios), and [6](#fig:N113_N159W_H2CO+Ha+5.8um+1.3mm)). It also shows that the YSO’s radiation heating could contribute to a gas temperature (e.g. $T_{\rm kin}$ $\sim$ 19 K for the lowest luminosity YSO (or candidate) with $L$ = 1.6 $\times$ 10$^4$ ${\rm L}_{\odot}$; see Table [\[table:Tkin-YSO\]](#table:Tkin-YSO)) even far out, at a radius of 1 pc. This implies that the complex temperature structure of the dense gas in N113 and N159W regions may be also affected by multiple YSOs and/or embedded infrared sources. For large areas of N113 and N159W the H$\alpha$ radiation regions and the general stellar radiation field may also contribute to the temperature of the dense gas.

Due to the limited spatial resolution ($\sim$0.4 pc) of the ALMA data and our limited 2-dimensional perspective, the relation between gas temperature and distance from YSOs is not perfectly revealed. A follow-up sub-arcsecond angular resolution (corresponding to $\lesssim$ 0.1 pc) mapping study of the massive star-forming clump’s temperature structure with H$_2$CO in the LMC will be indispensable and meaningful in the future.

## Turbulent heating

Turbulent heating seems to be widespread in Galactic massive star-forming regions on a $\sim$0.1–1.8 pc scale (cite: Tang2018a; Tang2018b). It may play an important role in heating the dense gas in star-forming regions. Present observations toward Galactic CMZ clouds with para-H$_2$CO (3–2 and 4–3) show that the warm dense gas is heated most likely by turbulence on a scale of $\sim$1 pc (cite: Ao2013; Ginsburg2016; Immer2016). Observations of, e.g. H$_2$CO, NH$_3$, and CH$_3$CCH in Galactic star formation regions suggest that the linewidth is correlated with gas kinetic temperature (cite: Wouterloot1988; Molinari1996; Jijina1999; Wu2006; Urquhart2011; Urquhart2015; Wienen2012; Lu2014; Tang2017a; Tang2018a; Tang2018b; Giannetti2017). Correlations between the kinetic temperature and linewidth are expected in the case of conversion of turbulent energy into heat (cite: Gusten1985; Molinari1996; Ginsburg2016).

We examine whether there is a relationship between the turbulence and the gas temperature derived from the para-H$_2$CO line ratio on a $\sim$0.4 pc scale in N113. As discussed in Sect. [3.5](#Sec:Non-thermal motions), our observational sets have low channel width ($\sim$1.34 km s$^{-1}$) for para-H$_2$CO data, which strongly affects the estimation of para-H$_2$CO linewidths in the N159W region, but weakly influences the N113 region which has wider linewidths. Therefore, we did not examine this relationship in N159W. We adopt the non-thermal velocity dispersion ($\sigma_{\rm NT}$) of para-H$_2$CO (3$_{03}$–2$_{02}$) in good approximation as proxy for the turbulence, and the kinetic temperature derived from the para-H$_2$CO line ratio as the gas kinetic temperature. We select positions with strong non-thermal motions ($\mathcal{M}$ $\gtrsim$ 3.5) located near the dense clumps (see Figs. [3](#fig:N113-Tk-H2CO-ratios) and [4](#fig:N159W-Tk-H2CO-ratios)). The relation between kinetic temperature and non-thermal velocity dispersion is shown in Fig. [7](#fig:Tk-width). It indicates that the non-thermal velocity dispersion of para-H$_2$CO is positively correlated with the gas kinetic temperatures, by a power-law of the form $T_{\rm kin}\,\propto\,\sigma_{\rm NT}^{1.03\pm0.03}$ with a correlation coefficients $R$ of 0.78, which agrees with results from Galactic massive star-forming regions ($T_{\rm kin} \propto \sigma_{\rm NT}^{0.66-1.26}$; gas kinetic temperature measured with para-H$_2$CO 3–2 and 4–3 line ratios; (cite: Tang2018a; Tang2018b)). The intercept and absolute values of the $T_{\rm kin}$–$\sigma_{\rm NT}$(H$_2$CO) relation in N113 are also consistent with previous results from Galactic massive star-forming regions on scales of $\sim$0.1–1.8 pc (cite: Tang2018a; Tang2018b). These imply that the higher temperature traced by para-H$_2$CO is related to higher turbulence on a scale of $\sim$0.4 pc. To our knowledge, this is the first evidence for dense gas heated in a star-forming region of the LMC by turbulence. Our $T_{\rm kin}$–$\sigma_{\rm NT}$(H$_2$CO) relation agrees with previous observational results ($T_{\rm kin}\propto\sigma_{\rm NT}^{0.8-1.0}$; gas kinetic temperature measured with NH$_3$ and H$_2$CO) in molecular clouds of the Galactic center (cite: Gusten1985; Mauersberger1987; Immer2016), only in terms of slope, not of intercept and absolute value.

We derive the gas kinetic temperature, $T_{\rm turb}$, assuming turbulent heating is the dominant heating process of the molecular gas in N113 and N159W, following the method applied by (cite: Tang2018a) in their Eq. (2), $$\begin{eqnarray}
3.3\times10^{-27}~n~\sigma_{\rm NT}^3~L^{-1} = 4\times10^{-33}~n^2~T_{\rm turb}^{1/2}(T_{\rm turb}-T_{\rm dust}) \nonumber \\
+~6\times10^{-29}~n^{1/2}~T_{\rm turb}^3~{\rm d}v/{\rm d}r.
\end{eqnarray}$$ The gas density $n$ is in units of cm$^{-3}$, the velocity gradient d$v$/d$r$ is in units of km s$^{-1}$pc$^{-1}$, the one-dimensional non-thermal velocity dispersion $\sigma_{\rm NT}$ is in units of km s$^{-1}$, and the cloud size $L$ is in units of pc, and the temperatures $T_{\rm turb}$ and $T_{\rm dust}$ are in K. We assume a cloud size of $\sim$1 pc (see Fig. [1](#fig:N113+N159W-maps)), a typical velocity gradient of 1 km s$^{-1}$ pc$^{-1}$, a measured para-H$_2$CO (3$_{03}$–2$_{02}$) non-thermal velocity dispersion (see Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters), column 5), and an averaged gas spatial density $n$(H$_2$) = 10$^5$ cm$^{-3}$ (cite: Tang2017b). Previous observations have shown that the gas kinetic temperatures derived from para-H$_2$CO (3–2) line ratios and the dust temperatures obtained from *Herschel* data are in good agreement in the dense star-forming regions of the LMC (cite: Tang2017b), so here we adopt the gas temperatures obtained from our H$_2$CO line ratios as the dust temperatures. The derived gas kinetic temperatures $T_{\rm turb}$ are listed in Table [\[table:Clumps-Parameters\]](#table:Clumps-Parameters). It seems that the derived $T_{\rm turb}$ values are reasonably well consistent with the gas kinetic temperatures $T_{\rm kin}$(H$_2$CO) obtained from our H$_2$CO line ratios. This indicates that turbulent heating contributes to the gas temperature on a scale of $\sim$0.4 pc. As discussed in Sect. [4.2](#Sec:Radiation-heating), gas in these dense clumps is also affected by internal star formation activity and/or nearby YSOs. Therefore, turbulent heating may play an important role in heating the dense gas in the star-forming regions of N113 and N159W.

![](Tkin-Vnt-N113.pdf)

Observations of the transitions of the para-H$_2$CO (3–2) lines with the APEX 12 m telescope in the Galactic star-forming region OMC-1 ($\sim$1.1$\times$1.7 pc$^2$) on a scale of $\sim$0.06 pc suggest complex gas heating which is most likely due to a number of different processes, e.g. star formation activity, radiation, and turbulence (cite: Tang2018a). Further observations of para-H$_2$CO (3–2 and 4–3) toward dense clumps representing various evolutionary stages of high-mass star formation in the Galactic plane on scales of $\sim$0.1–1.8 pc indicate similar gas heating processes for the dense gas (cite: Tang2018b). Our observations reveal also similar gas heating mechanisms in a relatively large area of N113 ($\sim$2.4$\times$6.1 pc$^2$) and N159W ($\sim$3.6$\times$5.1 pc$^2$) on a scale of $\sim$0.4 pc in the LMC. These imply that the gas heating for the dense gas of star-forming regions in low metallicity environments with strong UV radiation in the LMC may be dominated by internal star formation activity, radiation, and/or turbulence. The physical and chemical processes of dense gas on a scale of $\sim$0.4 pc in star-forming regions of the LMC might be different from those in low density regions ($n$(H$_2$) $<$ 10$^5$ cm$^{-3}$), so the very dense gas clouds should not be simply modeled as PDRs in low metallicity environments.

# Summary

We have mapped the kinetic temperature structures of two star formation regions, N113 and N159W, in the LMC in the para-H$_2$CO  $J_{\rm K_aK_c}$ = 3$_{03}$–2$_{02}$, 3$_{22}$–2$_{21}$, and 3$_{21}$–2$_{20}$ lines using ALMA Band 6. The main results are the following:

1.  There is no significant correlation between the spatial distributions of the dense gas traced by para-H$_2$CO and H$\alpha$ emission in N113 and N159W. However, the integrated intensity distributions of para-H$_2$CO are similar to those of the 1.3 mm dust emission in N113 and N159W, indicating that the H$_2$CO emission associates well with dense gas traced by the emission of the cold dust. There is also some agreement with the *Spitzer* 8.0 $\mu$m emission in N113 and N159W, which suggests that dense gas traced by para-H$_2$CO associates with massive star-forming regions.

2.  Using the RADEX non-LTE program, we derive the gas kinetic temperature by modeling the measured para-H$_2$CO 0.5$\times$\[(3$_{22}$–2$_{21}$+3$_{21}$–2$_{20}$)/3$_{03}$–2$_{02}$\] line ratios. The gas kinetic temperatures derived from para-H$_2$CO line ratios are warm at a spatial density of 10$^5$ cm$^{-3}$, ranging from 28 to 105 K in N113 and 29 to 68 K in N159W. The aforementioned upper bounds to the kinetic temperature, arising from the cores, may be affected by moderate line saturation and thus may be slightly overestimated.

3.  The high kinetic temperatures ($T_{\rm kin}$ $\gtrsim$ 50 K) of the dense gas traced by para-H$_2$CO appear to be correlated with the internal embedded infrared sources and/or YSOs in the N113 and N159W regions. The lower temperatures ($T_{\rm kin}$ $<$ 50 K) are located at the outskirts of the H$_2$CO distributions of both N113 and N159W. The gas kinetic temperatures show apparent gradients in some dense H$_2$CO clumps of N113 and N159W.

4.  The kinetic temperatures of the dense gas traced by para-H$_2$CO appear to be only weakly affected by the external FUV radiation.

5.  The non-thermal velocity dispersions of para-H$_2$CO are correlated with the gas kinetic temperatures in N113, implying that higher temperatures traced by para-H$_2$CO are related to turbulence on a $\sim$0.4 pc scale.

6.  In the LMC, the gas heating for the dense gas may be dominated by internal star formation activity, radiation, and/or turbulence in star-forming regions with low metallicity environments, which is consistent with our Galactic massive star-forming regions located in the Galactic plane.

# Acknowledgements

The authors thank the anonymous referee for helpful comments. This work acknowledges support by the Heaven Lake Hundred-Talent Program of Xinjiang Uygur Autonomous Region of China, the National Natural Science Foundation of China under Grant 11903070, 11433008, and 11973076, the "TianShan Youth Plan" under Grant 2018Q084, the CAS “Light of West China” Program under Grant Nos. 2018-XBQNXZ-B-024 and 2020-XBQNXZ-017, and the Collaborative Research Council 956, subproject A6, funded by the Deutsche Forschungsgemeinschaft (DFG). C. H. acknowledges support by Chinese Academy of Sciences President’s International Fellowship Initiative under Grant No. 2021VMA0009. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00554.S, 2013.1.01136.S, and 2015.1.01388.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research has used NASA’s Astrophysical Data System (ADS).

111 natexlab

(ref: Ao2013) Ao, Y., Henkel, C., Menten, K. M., et al. 2013, A&A, 550, A135

(ref: Bergman2011) Bergman, P., Parise, B., Liseau, R., & Larsson, B. 2011, A&A, 527, A39

(ref: Bieging1982) Bieging, J. H., Wilson, T. L., & Downes, D. 1982, A&AS, 49, 607

(ref: Carlson2012) Carlson, L. R., Sewiło, M., Meixner, M., Romita, K. A., & Lawton, B. 2012, A&A, 542, A66

(ref: Caselli1993) Caselli, P., Hasegawa, T. I., & Herbst, E. 1993, ApJ, 408, 548

(ref: Chen2010) Chen, C. H. R., Indebetouw, R., Chu, Y.-H., et al. 2010, ApJ, 721, 1206

(ref: Chin1996) Chin, Y. N., Henkel, C., Millar, T. J., Whiteoak, J. B., & Mauersberger, R. 1996, A&A, 312, L33

(ref: Chin1997) Chin, Y. N., Henkel, C., Whiteoak, J. B., et al. 1997, A&A, 317, 548

(ref: Downes1980) Downes, D., Wilson, T. L., Bieging, J., & Wink, J. 1980, A&AS, 40, 379

(ref: Ellingsen2010) Ellingsen, S. P., Breen, S. L., Caswell, J. L., Quinn, L. J., & Fuller, G. A. 2010, MNRAS, 404, 779

(ref: Farina2009) Fariña, C., Bosch, G. L., Morrell, N. I., Barbá, R. H., & Walborn, N. R. 2009, AJ, 138, 510

(ref: Fukui2015) Fukui, Y., Harada, R., Tokuda, K., et al. 2015, ApJL, 807, L4

(ref: Fukui2010) Fukui, Y. & Kawamura, A. 2010, ARA&A, 48, 547

(ref: Fukui1999) Fukui, Y., Mizuno, N., Yamaguchi, R., et al. 1999, PASJ, 51, 745

(ref: Gao2004a) Gao, Y. & Solomon, P. M. 2004a, ApJ, 606, 271

(ref: Gao2004b) Gao, Y. & Solomon, P. M. 2004b, ApJS, 152, 63

(ref: Gerner2014) Gerner, T., Beuther, H., Semenov, D., et al. 2014, A&A, 563, A97

(ref: Giannetti2017) Giannetti, A., Leurini, S., Wyrowski, F., et al. 2017, A&A, 603, A33

(ref: Gieser2021) Gieser, C., Beuther, H., Semenov, D., et al. 2021, A&A, arXiv:2102.11676

(ref: Ginsburg2015) Ginsburg, A., Bally, J., Battersby, C., et al. 2015, A&A, 573, A106

(ref: Ginsburg2011) Ginsburg, A., Darling, J., Battersby, C., Zeiger, B., & Bally, J. 2011, ApJ, 736, 149

(ref: Ginsburg2017) Ginsburg, A., Goddi, C., Kruijssen, J. M. D., et al. 2017, ApJ, 842, 92

(ref: Ginsburg2016) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50

(ref: Guo2016) Guo, W. H., Esimbek, J., Tang, X. D., et al. 2016, Ap&SS, 361, 264

(ref: Gusten1985) Güsten, R., Walmsley, C. M., Ungerechts, H., & Churchwell, E. 1985, A&A, 142, 381

(ref: Heikkila1998) Heikkilä, A., Johansson, L. E. B., & Olofsson, H. 1998, A&A, 332, 493

(ref: Heikkila1999) Heikkilä, A., Johansson, L. E. B., & Olofsson, H. 1999, A&A, 344, 817

(ref: Henkel1991) Henkel, C., Baan, W. A., & Mauersberger, R. 1991, A&ARv, 3, 47

(ref: Henkel2018) Henkel, C., Mühle, S., Bendo, G., et al. 2018, A&A, 615, A155

(ref: Henkel1980) Henkel, C., Walmsley, C. M., & Wilson, T. L. 1980, A&A, 82, 41

(ref: Henkel1983) Henkel, C., Wilson, T. L., Walmsley, C. M., & Pauls, T. 1983, A&A, 127, 388

(ref: Hidaka2004) Hidaka, H., Watanabe, N., Shiraki, T., Nagaoka, A., & Kouchi, A. 2004, ApJ, 614, 1124

(ref: Immer2014) Immer, K., Galván-Madrid, R., König, C., Liu, H. B., & Menten, K. M. 2014, A&A, 572, A63

(ref: Immer2016) Immer, K., Kauffmann, J., Pillai, T., Ginsburg, A., & Menten, K. M. 2016, A&A, 595, A94

(ref: Jijina1999) Jijina, J., Myers, P. C., & Adams, F. C. 1999, ApJS, 125, 161

(ref: Johansson1994) Johansson, L. E. B., Olofsson, H., Hjalmarson, A., Gredel, R., & Black, J. H. 1994, A&A, 291, 89

(ref: Johnstone2003) Johnstone, D., Boonman, A. M. S., & van Dishoeck, E. F. 2003, A&A, 412, 157

(ref: Jones2005) Jones, T. J., Woodward, C. E., Boyer, M. L., Gehrz, R. D., & Polomski, E. 2005, ApJ, 620, 731

(ref: Kaufman1999) Kaufman, M. J., Wolfire, M. G., Hollenbach, D. J., & Luhman, M. L. 1999, ApJ, 527, 795

(ref: Kennicutt1998a) Kennicutt, Robert C., J. 1998a, ApJ, 498, 541

(ref: Kennicutt1998b) Kennicutt, Robert C., J. 1998b, ARA&A, 36, 189

(ref: Klessen2007) Klessen, R. S., Spaans, M., & Jappsen, A.-K. 2007, MNRAS, 374, L29

(ref: Lee2019) Lee, M. Y., Madden, S. C., Le Petit, F., et al. 2019, A&A, 628, A113

(ref: Lee2016) Lee, M. Y., Madden, S. C., Lebouteiller, V., et al. 2016, A&A, 596, A85

(ref: Li2021) Li, F., Wang, J., Gao, F., et al. 2021, MNRAS, 503, 4508

(ref: Lindberg2012) Lindberg, J. E. & Jørgensen, J. K. 2012, A&A, 548, A24

(ref: Lindberg2015) Lindberg, J. E., Jørgensen, J. K., Watanabe, Y., et al. 2015, A&A, 584, A28

(ref: Liszt2006) Liszt, H. S., Lucas, R., & Pety, J. 2006, A&A, 448, 253

(ref: Lu2021) Lu, X., Li, S., Ginsburg, A., et al. 2021, ApJ, 909, 177

(ref: Lu2017) Lu, X., Zhang, Q., Kauffmann, J., et al. 2017, ApJ, 839, 1

(ref: Lu2014) Lu, X., Zhang, Q., Liu, H. B., Wang, J., & Gu, Q. 2014, ApJ, 790, 84

(ref: Mangum2013) Mangum, J. G., Darling, J., Henkel, C., & Menten, K. M. 2013, ApJ, 766, 108

(ref: Mangum2008) Mangum, J. G., Darling, J., Menten, K. M., & Henkel, C. 2008, ApJ, 673, 832

(ref: Mangum2019) Mangum, J. G., Ginsburg, A. G., Henkel, C., et al. 2019, ApJ, 871, 170

(ref: Mangum1993a) Mangum, J. G. & Wootten, A. 1993, ApJS, 89, 123

(ref: Mangum1990) Mangum, J. G., Wootten, A., Loren, R. B., & Wadiak, E. J. 1990, ApJ, 348, 542

(ref: Mangum1993b) Mangum, J. G., Wootten, A., & Plambeck, R. L. 1993, ApJ, 409, 282

(ref: Mauersberger1987) Mauersberger, R., Henkel, C., & Wilson, T. L. 1987, A&A, 173, 352

(ref: Meixner2006) Meixner, M., Gordon, K. D., Indebetouw, R., et al. 2006, AJ, 132, 2268

(ref: Minamidani2008) Minamidani, T., Mizuno, N., Mizuno, Y., et al. 2008, ApJS, 175, 485

(ref: Minamidani2011) Minamidani, T., Tanaka, T., Mizuno, Y., et al. 2011, AJ, 141, 73

(ref: Molinari1996) Molinari, S., Brand, J., Cesaroni, R., & Palla, F. 1996, A&A, 308, 573

(ref: Muhle2007) Mühle, S., Seaquist, E. R., & Henkel, C. 2007, ApJ, 671, 1579

(ref: Nishimura2016) Nishimura, Y., Shimonishi, T., Watanabe, Y., et al. 2016, ApJ, 818, 161

(ref: Ott2010) Ott, J., Henkel, C., Staveley-Smith, L., & Weiß, A. 2010, ApJ, 710, 105

(ref: Pan2009) Pan, L. & Padoan, P. 2009, ApJ, 692, 594

(ref: Papadopoulos2011) Papadopoulos, P. P., Thi, W.-F., Miniati, F., & Viti, S. 2011, MNRAS, 414, 1705

(ref: Paron2014) Paron, S., Ortega, M. E., Cunningham, M., et al. 2014, A&A, 572, A56

(ref: Paumard2006) Paumard, T., Genzel, R., Martins, F., et al. 2006, ApJ, 643, 1011

(ref: Pietrzynski2019) Pietrzyński, G., Graczyk, D., Gallenne, A., et al. 2019, Nature, 567, 200

(ref: Pietrzynski2013) Pietrzyński, G., Graczyk, D., Gieren, W., et al. 2013, Nature, 495, 76

(ref: Pineda2008) Pineda, J. L., Mizuno, N., Stutzki, J., et al. 2008, A&A, 482, 197

(ref: Rolleston2002) Rolleston, W. R. J., Trundle, C., & Dufton, P. L. 2002, A&A, 396, 53

(ref: Seale2012) Seale, J. P., Looney, L. W., Wong, T., et al. 2012, ApJ, 751, 42

(ref: Sewilo2019) Sewiło, M., Charnley, S. B., Schilke, P., et al. 2019, ACS Earth and Space Chemistry, 3, 2088

(ref: Sewilo2010) Sewiło, M., Indebetouw, R., Carlson, L. R., et al. 2010, A&A, 518, L73

(ref: Sewilo2018) Sewiło, M., Indebetouw, R., Charnley, S. B., et al. 2018, ApJL, 853, L19

(ref: Shimonishi2016) Shimonishi, T., Onaka, T., Kawamura, A., & Aikawa, Y. 2016, ApJ, 827, 72

(ref: Shirley2015) Shirley, Y. L. 2015, PASP, 127, 299

(ref: Smith1998) Smith, R. C. & MCELS Team. 1998, PASA, 15, 163

(ref: Soma2018) Soma, T., Sakai, N., Watanabe, Y., & Yamamoto, S. 2018, ApJ, 854, 116

(ref: Tang2013) Tang, X. D., Esimbek, J., Zhou, J. J., et al. 2013, A&A, 551, A28

(ref: Tang2014) Tang, X. D., Esimbek, J., Zhou, J. J., Wu, G., & Okoh, D. 2014, RAA, 14, 959

(ref: Tang2017b) Tang, X. D., Henkel, C., Chen, C. H. R., et al. 2017b, A&A, 600, A16 (Paper II)

(ref: Tang2019) Tang, X. D., Henkel, C., Menten, K. M., et al. 2019, A&A, 629, A6

(ref: Tang2018a) Tang, X. D., Henkel, C., Menten, K. M., et al. 2018a, A&A, 609, A16 (Paper III)

(ref: Tang2017a) Tang, X. D., Henkel, C., Menten, K. M., et al. 2017a, A&A, 598, A30 (Paper I)

(ref: Tang2018b) Tang, X. D., Henkel, C., Wyrowski, F., et al. 2018b, A&A, 611, A6

(ref: Trevino2014) Treviño-Morales, S. P., Pilleri, P., Fuente, A., et al. 2014, A&A, 569, A19

(ref: Urquhart2015) Urquhart, J. S., Figura, C. C., Moore, T. J. T., et al. 2015, MNRAS, 452, 4029

(ref: Urquhart2011) Urquhart, J. S., Morgan, L. K., Figura, C. C., et al. 2011, MNRAS, 418, 1689

(ref: van2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: Wang2009) Wang, M., Chin, Y. N., Henkel, C., Whiteoak, J. B., & Cunningham, M. 2009, ApJ, 690, 580

(ref: Wang2012) Wang, Y., Beuther, H., Zhang, Q., et al. 2012, ApJ, 754, 87

(ref: Watanabe2002) Watanabe, N. & Kouchi, A. 2002, ApJL, 571, L173

(ref: Weiss2001) Weiß, A., Neininger, N., Henkel, C., Stutzki, J., & Klein, U. 2001, ApJL, 554, L143

(ref: Westerlund1990) Westerlund, B. E. 1990, A&ARv, 2, 29

(ref: Wienen2012) Wienen, M., Wyrowski, F., Schuller, F., et al. 2012, A&A, 544, A146

(ref: Wiesenfeld2013) Wiesenfeld, L. & Faure, A. 2013, MNRAS, 432, 2573

(ref: Wiseman1998) Wiseman, J. J. & Ho, P. T. P. 1998, ApJ, 502, 676

(ref: Wong2011) Wong, T., Hughes, A., Ott, J., et al. 2011, ApJS, 197, 16

(ref: Wong2006) Wong, T., Whiteoak, J. B., Ott, J., Chin, Y.-n., & Cunningham, M. R. 2006, ApJ, 649, 224

(ref: Woon2002) Woon, D. E. 2002, ApJ, 569, 541

(ref: Wouterloot1988) Wouterloot, J. G. A., Walmsley, C. M., & Henkel, C. 1988, A&A, 203, 367

(ref: Wu2005) Wu, J., Evans, Neal J., I., Gao, Y., et al. 2005, ApJL, 635, L173

(ref: Wu2006) Wu, Y., Zhang, Q., Yu, W., et al. 2006, A&A, 450, 607

(ref: Yan2019) Yan, Y. T., Zhang, J. S., Henkel, C., et al. 2019, ApJ, 877, 154

(ref: Zhang2014) Zhang, Z.-Y., Gao, Y., Henkel, C., et al. 2014, ApJL, 784, L31

(ref: Zhang2018) Zhang, Z.-Y., Romano, D., Ivison, R. J., Papadopoulos, P. P., & Matteucci, F. 2018, Nature, 558, 260

(ref: Zhu2020) Zhu, F.-Y., Wang, J.-Z., Liu, T., et al. 2020, MNRAS, 499, 6018

(ref: Zylka1992) Zylka, R., Guesten, R., Henkel, C., & Batrla, W. 1992, A&AS, 96, 525

# H$_2$CO velocity channel maps

![](N113-H2CO_303-Channell-map.pdf)

![](N159W-H2CO_303-Channell-map.pdf)

[^1]: https://casa.nrao.edu

[^2]: http://www.iram.fr/IRAMFR/GILDAS

[^3]: http://var.sron.nl/radex/radex.php

</paper>

Write the methods card for this paper.