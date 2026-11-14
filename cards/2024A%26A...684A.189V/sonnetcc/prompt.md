# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...684A.189V\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...684A.189V",
 "title": "FAUST. XI. Enhancement of the complex organic material in the shocked matter surrounding the [BHB2007] 11 protobinary system",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Vastel, C.",
 "n_authors": 23,
 "arxiv_id": "2403.07757",
 "doi": "10.1051/0004-6361/202348481",
 "alma_projects_linked_by_archive": [
  "2018.1.01205.L"
 ]
}
```

Paper text:
<paper>
# FAUST XI: Enhancement of the complex organic material in the shocked matter surrounding the \[BHB2007\] 11 protobinary system

Interstellar complex organic molecules (iCOMs) are species commonly found in the interstellar medium. They are believed to be crucial seed species for the build-up of chemical complexity in star forming regions as well as our own Solar System. Thus, understanding how their abundances evolve during the star formation process and whether it enriches the emerging planetary system is of paramount importance. We use data from the ALMA Large Program FAUST (Fifty AU STudy of the chemistry in the disk and envelope system of solar protostars) to study the compact line emission towards the \[BHB2007\] 11 proto-binary system (sources A and B), where a complex structure of filaments connecting the two sources with a larger circumbinary disk has previously been detected. More than 45 methyl formate (CH$_3$OCHO) lines are clearly detected with upper energies in the \[123, 366\] K range, as well as 8 dimethyl ether transitions (CH$_3$OCH$_3$) in the \[93, 191\] K range, 1 ketene transition (H$_{2}$CCO) and 4 formic acid transitions (t-HCOOH). We compute the abundance ratios with respect to CH$_3$OH for CH$_3$OCHO, CH$_3$OCH$_3$, H$_{2}$CCO, t-HCOOH (as well as an upper limit for CH$_{3}$CHO) through a radiative transfer analysis. We also report the upper limits on the column densities of nitrogen bearing iCOMs, $N$(C$_2$H$_5$CN) and $N$(C$_2$H$_3$CN).

The emission from the detected iCOMs and their precursors is compact and encompasses both protostars, which are separated by only 0.2$^{\prime\prime}$ ($\sim$ 28 au). The integrated intensities tend to align with the Southern filament, revealed by the high spatial resolution observations of the dust emission at 1.3 mm. A Position-Velocity and 2D analysis are performed on the strongest and uncontaminated CH$_3$OCH$_3$ transition and show three different spatial and velocity regions, two of them being close to 11B (Southern filament) and the third one near 11A.

All our observations suggest that the detected methanol, as well as the other iCOMs, are generated by the shocked gas from the incoming filaments streaming towards \[BHB2007\] 11A and 11B, respectively, making this source one of the few where chemical enrichment of the gas caused by the streaming material is observed.

# Introduction

Interstellar complex organic molecules (also called iCOMs) are defined in the astronomical community as carbon-bearing species containing at least six atoms (cite: Herbst2009; Ceccarelli2017). The detection of iCOMs in solar-type protostars and their precursors in the prestellar core phase is crucial for understanding how molecular complexity emerges and evolves in the different stages that lead to the formation of a solar system such our own. The protostellar phase starts with the young accreting protostar phase with a central object at T $\ge$ 100 K that eventually will become a star, surrounded by a colder envelope from which the future star accretes matter (also called Class 0). In a simple scenario, the molecules trapped in the ices are injected back into the gas phase due to thermal desorption, giving rise to a rich and peculiar chemistry in which iCOMS are found in these regions, called hot corinos (cite: Cazaux2003; Bottinelli2004; Ceccarelli2004). The name comes from their high-mass analogues, which are called hot cores (cite: Morris1980). Many iCOMS have been detected in these objects, such as methyl formate (CH$_3$OCHO), dimethyl ether (CH$_3$OCH$_3$), acetaldehyde (CH$_3$CHO), ethanol (CH$_3$CH$_2$OH), and formamide (NH$_2$CHO) (cite: Ceccarelli2023).\
In this context, the Atacama Large Millimeter/submillimeter Array (ALMA) Large Program[^1] Fifty AU STudy of the chemistry in the disk and envelope system of Solar-like protostars: 2018.1.01205.L (FAUST) is designed to survey the chemical composition of a sample of 13 Class 0/I protostars at a scale of about 50 to 1000 au (all sources have a distance smaller than 250 pc). The description of the project is reported in (cite: Codella2021). One of these sources is the \[BHB2007\] 11 protobinary system, which is embedded in the darkest parts of the Pipe nebula. This is a quiescent complex of interstellar clouds located at a distance of 163 $\pm$ 5 pc (cite: Dzib2018) from the Sun. Only a handful of embedded sources are known in the entire complex in the B59 molecular cloud, with \[BHB2007\] 11 being the youngest member of a protocluster of low-mass young stellar objects (cite: Brooke2007). At a higher angular resolution ($\sim$ 0.04$^{\prime\prime}$), (cite: Alves2019) previously uncovered a young binary protostar system embedded in circumstellar disks with radii of 2 to 3 au. The protostars are named \[BHB2007\] 11 A (hereafter 11A) for the northern source and \[BHB2007\] 11 B (hereafter 11B) for the southern source. Both cores are surrounded by a complex filamentary structure (within $\sim$ 100$^{\prime\prime}$) connecting to the larger circumbinary disk. (cite: Alves2019) suggested that these filaments are inflow streamers (also called accretion streamers) from the extended circumbinary disk onto the circumstellar disks of the protobinary system. Their CO observations primarily trace the outflow emission, but the high-velocity components indicate acceleration of infalling gas from the circumbinary disk onto \[BHB2007\] 11 B. No high-velocity components are detected near \[BHB2007\] 11 A. (cite: Evans2023) recently presented large-scale formaldehyde emission that seems to be consistent with an asymmetric molecular outflow launched by a wide-angle disk wind. (cite: Vastel2022) reported the emission of a compact hot methanol emission with three velocity components at -2, 2.8, and 9.9 km s$^{-1}$ and surprisingly found that the methanol components are not associated with the dust emission peaks, which would suggest a hot-corino origin. An estimation of the dust opacities using the 225 GHz dust continuum emission, which could lead to a high attenuation of the methanol emission at the dust peak, had uncertainties that were too large for any conclusive evidence of whether the foreground dust could completely attenuate the methanol emission from the hot corinos. Another possibility would be that methanol emission originates from the shocked positions at the intersection of intertwined filaments, leading to a different origin than the classical hot-corino origin. This could result in the sputtering of the grain mantles in these shocked regions due to the streaming of the gas towards 11A and 11B, which impacts the quiescent gas of the circumbinary envelope or, possibly, the two circumstellar disks (cite: Vastel2022). (cite: Evans2023) also presented some HDCO and D$_2$CO emission that was only found at the same location of the methanol compact emission, deriving an average D/H ratio of 0.02$^{+0.02}_{-0.01}$.\
In the present work, we investigate the iCOM emission found in the FAUST observations towards \[BHB2007\] 11 as well as some precursors. Our goal is to understand the origin of the detected iCOM emission by locating and comparing it with the most simple iCOM, methanol, which was previously studied by (cite: Vastel2022). We present in Section [2](#sec: obs) the observations and describe in Section [3](#sec: line-id) the method we used for the line identification of the iCOMs and precursors. Section [4](#sec: results) presents the spatial distribution of isolated transitions in order to determine the location of their emission. To compute the column densities of the species of interest, we perform a radiative transfer analysis of the emission lines in Section [5](#sec: modelling). A discussion is finally developed in Section [6](#sec: discussion) to understand the origin of the emission of the iCOMs in \[BHB2007\] 11 and compare with other protostellar sources.

# Observations

The observations were centred at $\alpha$ (2000) = 17h11m23.125s, $\delta$ (2000) = -27$^{\circ}$24$^{\prime}$32.87$^{\prime\prime}$. They consisted of three frequency setups and 13 spectral windows (*spw*), as explained in previous FAUST papers on \[BHB2007\] 11 (cite: Vastel2022; Evans2023). Table [1](#tab: spw) presents the *spw* for the FAUST \[BHB2007\] 11 observations, specifically, those in which detections are presented in this study (in bold), as well as those used to compute the upper limits. All the $spw$ were used to search for transitions of the species of interest. We used the 12m array (TM 1 and TM 2) due to the compact emission of the iCOMs transitions. The bandwidth is 59 MHz for the 12m array, except for the continuum window, with a 1.875 GHz bandwidth. Spectral line imaging was performed with the Common Astronomy Software Applications package (CASA) 5.6.1-8 [^2] with a modified version of the ALMA calibration pipeline and additional in-house calibration routine[^3] (Chandler in prep.). The systemic velocity of \[BHB2007\] 11 is 3.6 km s$^{-1}$ with respect to the local standard of rest (cite: Onishi1999). For the following line identification, we extracted two spectra from the *spw* continuum bands to cover the broad velocity emission, which extends within 0.82$^{\prime\prime}$ $\times$ 0.77$^{\prime\prime}$ centred at $\alpha$ (2000) = 17h11m23.107s, $\delta$ (2000) = -27$^{\circ}$24$^{\prime}$33.005$^{\prime\prime}$. The two spectra are presented in Fig [1](#fig: cont-spectra), and the resulting beams and spectral resolutions are quoted in Table [2](#tab: spectro). Based on the high spatial resolution observations of the dust emission at 1.3 mm with ALMA by (cite: Alves2019), the coordinates for the two cores are $\alpha$ (2000) = 17h11m23.1058s, $\delta$ (2000) = -27$^{\circ}$24$^{\prime}$32.828$^{\prime\prime}$ for 11A and $\alpha$ (2000) = 17h11m23.1015s, $\delta$ (2000) = -27$^{\circ}$24$^{\prime}$32.987$^{\prime\prime}$ for 11B. There was a small error in the coordinates, as quoted in the Introduction of (cite: Vastel2022).

|                 |                 |                 |            |
|:---------------:|:---------------:|:---------------:|:----------:|
| Spectral window |     setup 1     |     setup 2     |  setup 3   |
|                 |      (GHz)      |      (GHz)      |   (GHz)    |
|     spw 25      |     216.113     |     243.916     |   93.181   |
|     spw 27      |     216.563     |     244.049     |   94.405   |
|     spw 29      |     217.105     |     244.936     | 95.000$^a$ |
|     spw 31      |     217.822     |     245.606     |  107.014   |
|     spw 33      |     218.222     | **246.700**$^a$ |  108.040   |
|     spw 35      |     218.440     |   **260.189**   |  104.239   |
|     spw 37      |     219.560     |     260.255     |  105.799   |
|     spw 39      |     219.949     |     261.687     |            |
|     spw 41      |     231.061     |     262.004     |            |
|     spw 43      |     213.221     |   **257.896**   |            |
|     spw 45      |     231.322     |     258.256     |            |
|     spw 47      |     231.410     |   **258.549**   |            |
|     spw 49      | **233.796**$^a$ |   **259.035**   |            |

: Spectral windows presented in this study for the detected iCOMs (in bold) in the observed FAUST \[BHB2007\] 11 dataset.

Table notes: $^a$: continuum windows. The *spw* that are not indicated in bold were also used in the search for iCOMs transitions.

# Line identification

In this section, we describe the line identification method for the exploration of the molecular complexity in \[BHB2007\] 11. The line identification was performed using the CASSIS[^4] software, which connects to the JPL (cite: Pickett1998) and CDMS (cite: Muller2005) databases with direct access to VAMDC[^5] as well to verify all the available spectroscopic databases.

![](FIGURES/Continuum.eps)

## Methyl formate (CH$_3$OCHO)

The large bandwidth of the continuum window led to the detection of more than 45 transitions of methyl formate in setup 1 at 233.796 GHz and setup 2 at 259.035 GHz. We also tentatively identified four CH$_{3}$O$^{13}$CHO transitions blended in one broad feature (see discussion in Sec. [5](#sec: modelling)). Table [2](#tab: spectro) lists the spectroscopic parameters for the lines found in the two continuum bands as well as the transitions detected in the other *spw*. In the interstellar medium, methyl formate is the most abundant of its isomers, namely acetic acid (CH$_{3}$COOH, TAG=60523) and glycolaldehyde (HCOCH$_{2}$OH, TAG=60006), which have not been detected in our observations.

## Dimethyl ether (CH$_3$OCH$_3$)

Two strong lines of dimethyl ether were detected at 257.9 GHz and 258.5 GHz (see Table [2](#tab: spectro)). No lines were detected in the continuum *spw*, probably because the Einstein coefficients are too low to detect any line above the noise: $A_{ul}$ $\le$ 10$^{-5}$ s$^{-1}$ at 233 GHz and $A_{ul}$ $\le$ 10$^{-8}$ s$^{-1}$ at 246 GHz. In addition, the detected 258.5 GHz line is affected by the emission of a blended transition of CH$_3$OCHO (listed in Table [2](#tab: spectro)).

## Formamide (NH$_{2}$CHO) and ketene (H$_{2}$CCO)

Formamide (NH$_{2}$CHO) was targeted in *spw* 35 of setup 2 through its 12$_{2,10}$–11$_{2,9}$ transition at 260.190 GHz (see Table [\[tab: spectroND\]](#tab: spectroND)). A line is indeed present at the quoted frequency at a 0.1 K level. To confirm the detection, we checked for additional transitions with similar spectroscopic parameters (Einstein coefficient, upper energy level, and statistical weight). One transition at 247.391 GHz should present a similar peak intensity given the similar Einstein coefficient, upper level energy, and degeneracy, but it has not been detected at a 4$\sigma$ level (0.07 K). Similarly, two other transitions at 234.316 GHz and 233.897 GHz (see Table [\[tab: spectroND\]](#tab: spectroND) for the spectroscopic parameters) are not detected either at a 0.1 K $rms$. On the other hand, ketene (H$_{2}$CCO) seems the most likely candidate with its transition at 260.192 GHz (see Table [2](#tab: spectro)). Unfortunately, there are no other potential transitions for ketene in the continuum *spw*, and it is the only transition that is covered within our observations. The line width and $V_{LSR}$ are compatible with CH$_3$OH, CH$_3$OCH$_3$, and CH$_3$OCHO lines at -2, 2.8, and 9.9 km s$^{-1}$, and we can safely conclude that the species is detected in \[BHB2007\] 11. Although it is not an iCOM in the strict sense, it is thought to be involved in grain-surface reactions to form iCOMs such as formic acid, ethanol, and acetaldehyde (cite: Charnley1997; Charnley2008; Garrod2008; Hudson2013; Ferrero2023).

## Formic acid (t-HCOOH)

We also detected formic acid in its trans form. However, only four detectable lines lie in our frequency coverage, three of which are blended with CH$_3$OCHO at 246.1 and 247.5 GHz. Although it is not an iCOM by the above strict definition, t-HCOOH is important as it contains three heavy atoms and is the simplest organic acid. The spectroscopic parameters are listed in Table [2](#tab: spectro).

## Unidentified lines

In addition, two unidentified transitions have been detected at 246.522 GHz and 246.209 GHz that do not correspond to any firm detected transition, according to the CDMS and JPL databases. For the first transition, a CH$_{3}$CDO (TAG=45524) transition (13$_{3,11}$ – 12$_{3,10}$, $E_{up}$ = 98.14 K, $A_{ul}$ = 5.01 10$^{-4}$ s$^{-1}$) lies at that exact frequency (246522.1360 MHz). However, no other transitions with similar $E_{up}$ and $A_{ul}$ were detected in the continuum *spw* within the noise. For the second transition, a c-$^{13}$CCCH (TAG=38005) transition (N$_{K_{-1},K_{+1}}$ = 5$_{1,4}$–4$_{1,3}$, J = 9/2–7/2, F1 = 5–4, F = 11/2–9/2, $E_{up}$ = 39.54 K, $A_{ul}$ = 3.45 10$^{-4}$ s$^{-1}$) lies at the same frequency (246209.0970 MHz). However, no other transitions with similar $E_{up}$ and $A_{ul}$ were detected in the continuum *spw* within the noise. No conclusion can be determined so far.

## Non-detected iCOMs

#### Acetaldehyde

Acetaldehyde (CH$_{3}$CHO) was not detected in our observations. This might be surprising since it is routinely detected in hot corinos (cite: Cazaux2003; Jorgensen2016; Bianchi2022) and protostellar shocks (cite: Arce2008; Lefloch2017; DeSimone2020-I4outflow). It is the most abundant iCOM after methanol (cite: Ceccarelli2023). Twenty potential transitions are spread over the two continuum bands and are listed in Table [\[tab: spectroND\]](#tab: spectroND) in the appendix. However, the most likely line candidate for detection in these bands has a low Einstein coefficient (6.6 $\times$ 10$^{-5}$ s$^{-1}$), a relatively high upper energy of 96 K, and is blended with a bright CH$_3$OCHO transition ($A_{ul}$ = 2 $\times$ 10$^{-4}$ s$^{-1}$).

#### Nitrogen-bearing iCOMs

We also note that ethyl cyanide (C$_2$H$_5$CN) and vinyl cyanide (C$_2$H$_3$CN), which are often observed in high-mass star-forming regions (cite: Fontani2007), were not detected. Within the observed frequency range, the C$_2$H$_5$CN transition at 246.2687 GHz and the C$_2$H$_3$CN transition at 247.0870 GHz are expected to be brightest, but neither is detected (see Table [\[tab: spectroND\]](#tab: spectroND) in the appendix).

## Other lines

Finally, in the two continuum windows (see Table [1](#tab: spw)), we identified and detected the CH$_3$OH  transitions published by (cite: Vastel2022), one HDCO transition published by (cite: Evans2023), two SO$_2$ transitions, as well as one SO and S$^{34}$O transition (to be published in a subsequent FAUST publication).

# Spatial distribution

The maps presented in the following were obtained using the IRAM/GILDAS[^6] package (version dec22a). Figure [2](#fig: mom0-ch3och3) shows the moment 0 maps for the two strong CH$_3$OCH$_3$ transitions. The spectra from both transitions were extracted from a $\sim$ 0.4$^{\prime\prime}$ beam size, corresponding to the beam for both transitions (see Table [2](#tab: spectro)), which includes the 11A and 11B cores. This corresponds to $\sim$ 30$\sigma$ for the 258.5 GHz transition (upper energy level of 93 K) and also corresponds to $\sim$ 4$\sigma$ for the 257.9 GHz emission (upper energy level at 191 K). The line profiles are presented in Fig. [3](#fig: spec-ch3och3). The 257.911 GHz line profile is more widespread in frequency and does not present a simple three-component feature because of some blending with CH$_3$OCHO transitions at 257.9 GHz (see Table [2](#tab: spectro), $\rm E_{up}$ = 306.01 K). The 258.549 GHz transition of dimethyl ether is the strongest line of the detected iCOMs presented in this study that is not affected by blending from other transitions. The profile is a simple three-fit Gaussian, and we used it to try to determine the exact location, assuming that the emission is compact. In Fig. [2](#fig: mom0-ch3och3) (bottom), the image component size deconvolved from the beam for the central component (2.8 km s$^{-1}$) is more extended than the other, and we cannot yet deduce a clear location (see more details in Sec. [6](#sec: discussion)). Furthermore, we used the unblended 258.549 GHz transition of dimethyl ether to compute the velocity field (moment 1) around \[BHB2007\] 11. The left side of Fig. [4](#fig: moment1-ch3och3) shows a clear northwest-southeast gradient centred in between 11A and 11B at the systemic velocity of the source. The same velocity field has been obtained for the methanol transition (cite: Vastel2022).

![image](FIGURES/CH3OCH3_257911MHz_moment0.pdf) ![image](FIGURES/CH3OCH3_258549MHz_moment0_with2Ddeconvolved.pdf)  

![](FIGURES/CH3OCH3.eps)

![image](FIGURES/CH3OCH3_258549MHz_moment1.pdf) ![image](FIGURES/PV_CH3OCH3.pdf)

In order to better understand the left side of Fig. [4](#fig: moment1-ch3och3), we created a position-velocity (PV) diagram for the same transition. The PV plot shown on the right side of the figure was produced from a cut oriented parallel to the velocity gradient observed in the moment 1 map of the dimethyl ether emission at 258.549 GHz, whose PA is 140$^{\circ}$ east of north. The cut width is 0.5$^{\prime\prime}$, comparable to the angular resolution of the FAUST data, and it encompasses cores 11A and 11B, which are separated by 0.2$^{\prime\prime}$. This figure clearly shows the three velocity structures that were identified with methanol (cite: Vastel2022) and does not show a smooth Keplerian profile over the velocity range from the circumbinary envelope, as was shown using formaldehyde by (cite: Alves2019).

Considering the angular resolution of the present observations, we cannot determine the exact location of the iCOMs emission within the binary system. However, we applied the same method as in (cite: Vastel2022) and present on the left side of Fig. [5](#fig: 3comp-ch3och3) the red- and blueshifted emission for CH$_3$OCH$_3$ in the high-velocity channels where the S/N is higher than five (the channel at -3.69 km s$^{-1}$ in the blue and the channel at 11.18 km s$^{-1}$ in the red). Both components tend to be aligned with source 11B, like the high-velocity components of the CO emission (cite: Alves2019) and the methanol emission (cite: Vastel2022). The emission in the 2.8 km s$^{-1}$ channel (yellow) peaks near 11A in the same way as CO and CH$_3$OH. The three CH$_3$OCH$_3$ components appear in a compact configuration that is compatible with the compact emission seen in the moment 0 map (see Fig. [2](#fig: mom0-ch3och3)).

![image](FIGURES/Figure_3components_CH3OCH3.pdf) ![image](FIGURES/CO+CH3OCH3.pdf)

Since the iCOMs emission in each velocity channel is compact and centrally peaked, we performed 2D Gaussian fits on the CH$_3$OCH$_3$ transition at 258.549 GHz (the strongest unblended transition with a high S/N) in each channel to obtain the position of their intensity peak in the three components \[-5, 1\] km s$^{-1}$, \[1, 6\] km s$^{-1}$, and \[6, 13\] km s$^{-1}$. The right side of Fig. [5](#fig: 3comp-ch3och3) shows this 2D analysis. The accuracy on the relative position is given by $\theta/(2 \times S/N)$, where $\theta$ is the synthesised beam size, and S/N is the signal-to-noise ratio of the peak with respect to the map noise (cite: Condon1997; Condon1998). Consequently, the uncertainty on the position will be lower for higher S/N line intensities. In other words, a centroid fitting to the compact molecular emission yields astrometry with a precision better than that of the spatial resolution in the case of a high S/N. For this calculation, we only considered intensity peaks brighter than five times its Gaussian fit error and a S/N higher than ten, corresponding to a position accuracy better than 0.02$^{\prime\prime}$. This 2D analysis is similar to our analysis of methanol, except for the middle component at $\sim$ 3 km s$^{-1}$, which is more localised on the B source instead of in between the two cores. We note, however, the limited number of channels satisfying the requirements (S/N $>$ 10, intensity/error $>$ 5) compared to methanol. Fig. [5](#fig: 3comp-ch3och3) (right) shows no clear acceleration of the iCOMs material towards \[BHB2007\] 11 B (circles with red edges for velocities greater than 6 km s$^{-1}$ and circles with blue edges for velocities lower than 1 km s$^{-1}$), in contrast to what is seen in the high-velocity component of CO (circles with green edges) with a darker colour inside the circles nearby the source.

Many transitions of methyl formate (CH$_3$OCHO) were detected in the continuum band (Fig. [1](#fig: cont-spectra)), and Fig. [6](#fig: mom0-ch3ocho) shows the moment 0 maps for three isolated transitions covering a wide upper energy range between 115 and 333 K. The smaller beam of the transition at 233 GHz shows that the emission peaks south of \[BHB2007\] 11 B appear to clearly show a lack of emission towards \[BHB2007\] 11 A. There is a good correlation between this higher intensity in the southern region with the kinematic structure in the form of a clear velocity gradient around source \[BHB2007\] 11 B (see Fig. [5](#fig: 3comp-ch3och3), right). Figure [7](#fig: spec-ch3ocho) shows the spectra of some isolated transitions of CH$_3$OCHO in the continuum *spw*.\

![image](FIGURES/CH3OCHO_233754MHz_moment0.eps) ![image](FIGURES/CH3OCHO_234125MHz_moment0.eps) ![image](FIGURES/CH3OCHO_247469MHz_moment0.eps)  

![](FIGURES/CH3OCHO.eps)

The left side of Fig. [8](#fig: spec-h2cco) shows the moment 0 map for the only transition of ketene, again, with an enhancement in intensity in the southern region of 11B, following the filament traced with the dust continuum emission presented by (cite: Alves2019), as shown in Fig. [5](#fig: 3comp-ch3och3) (right).

![image](FIGURES/H2CCO260192MHz_moment0-new.pdf) ![image](FIGURES/Figure_H2CCO.eps)

# Radiative transfer modelling

We first performed a local thermodynamic equilibrium (LTE) analysis to estimate the CH$_3$OCH$_3$/CH$_3$OH and CH$_3$OCHO/CH$_3$OH abundance ratios. The methanol column density was computed from non-LTE modelling using its $^{13}$C isotopologue (cite: Vastel2022). For methyl formate and dimethyl ether, we extracted the spectra from the same region as for the CH$_3$OCH$_3$  transition at 257.911 GHz, corresponding to $\sim$ 0.4$^{\prime\prime}$.

We then used the parameters (column density, source size, and kinetic temperatures) found from the non-LTE modelling of the methanol transitions (cite: Vastel2022) to compute the column densities of CH$_3$OCH$_3$ and CH$_3$OCHO using the CASSIS software. We fixed the source sizes and let the best-fit model converge around the $V_{LSR}$ line width for the Gaussian fits and the kinetic temperatures of methanol for the excitation temperatures of the three components. We then let the source size vary. Table [\[tab: LTE\]](#tab: LTE) lists the results from the best fit obtained using all transitions in both continuum windows and in setup 2, *spw* 47 and 43, taking into account the blended lines of CH$_3$OCH$_3$  and CH$_3$OCHO. Figures [3](#fig: spec-ch3och3) and [7](#fig: spec-ch3ocho) show the best-fit LTE model (in red) obtained by simultaneously fitting all lines of CH$_3$OCH$_3$  and CH$_3$OCHO. The corresponding $V_{LSR}$ for the three components are -1.9, 3.0, and 9.2 km s$^{-1}$, and the FWHM values are 2, 5, and 4 km s$^{-1}$ respectively.\
With methanol as a reference, the CH$_3$OCH$_3$/CH$_3$OH ratio is \[5, 8\] $\times$ 10$^{-3}$ and the CH$_3$OCHO/CH$_3$OH ratio is \[2.5, 4.5\] $\times$ 10$^{-2}$ for the three components.\

|  |  | Velocity components |  |
|:--:|:--:|:--:|:--:|
|  | -2 km s$^{-1}$ | 2.8 km s$^{-1}$ | 9.9 km s$^{-1}$ |
| N(CH$_3$OH) (cm$^{-2}$) | ($1.4 \pm 0.6$) $\times 10^{18}$ | ($4.0 \pm 1.0$) $\times 10^{18}$ | ($3.0 \pm 0.8$) $\times 10^{18}$ |
| T (K) | $110 \pm 10$ | $130 \pm 10$ | $130 \pm 10$ |
| n$_{H_{2}}$ (cm$^{-3}$) | ($1.0^{+3}_{-0.5}$) $\times 10^{7}$ | ($2.0 \pm 0.5$) $\times 10^{6}$ | ($2.5 \pm 2.2$) $\times 10^{7}$ |
| $\theta_{S}$ ($^{\prime\prime}$) | $0.15^{\prime\prime} \pm 0.10^{\prime\prime}$ | $0.13^{\prime\prime} \pm 0.10^{\prime\prime}$ | 0.12$^{\prime\prime} \pm 0.10^{\prime\prime}$ |
| N(CH$_3$OCHO) (cm$^{-2}$) | \[1.0, 3.4\] $\times 10^{16}$ | \[2.2, 10.0\] $\times 10^{16}$ | \[3.0, 13.0\] $\times 10^{16}$ |
| N(CH$_3$OCH$_3$) (cm$^{-2}$) | \[3.5, 11.0\] $\times 10^{15}$ | \[6, 20\] $\times 10^{15}$ | \[6, 25\] $\times 10^{15}$ |
| N(t-HCOOH) (cm$^{-2}$) | \[0.6, 2.5\] $\times 10^{15}$ | \[0.55, 1.5\] $\times 10^{15}$ | \[1.0, 3.5\] $\times 10^{15}$ |
| N(H$_{2}$CCO) (cm$^{-2}$) | \[2.5, 20\] $\times 10^{14}$ | \[6, 25\] $\times 10^{14}$ | \[4, 20\] $\times 10^{14}$ |
| $\theta_{S}$ ($^{\prime\prime}$) | \[0.15, 0.30\] | \[0.13, 0.26\] | \[0.12, 0.24\] |
| T$_{ex}$ (K) | \[80, 100\] | \[80, 100\] | \[80, 100\] |

Table notes: The methanol non-LTE analysis and the three velocity components identifications are from (cite: Vastel2022).

We detected a line at 246.79 GHz (see Fig. [11](#fig: ch3o13cho)) that may correspond to the blending of four 13C$_{2}$ methyl formate (CH$_{3}$O$^{13}$CHO) transitions. The spectroscopic parameters are listed in Table [\[tab: spectroND\]](#tab: spectroND). Many lines have previously been detected in the spectrum of the Orion star-forming region (cite: Carvajal2009) at the IRc2 position. Combining our CH$_3$OCHO column density with its isotopologue, we used a $^{12}$C/$^{13}$C ratio of 68 (cite: Milam2005) to compute a CH$_{3}$O$^{13}$CHO ratio of \[1.5, 5.0\] $\times$ 10$^{14}$, \[3.2, 15\] $\times$ 10$^{14}$ and \[4.4, 19\] $\times$ 10$^{14}$ cm$^{-2}$. With the same source size and excitation temperatures as for CH$_3$OCHO and CH$_3$OCH$_3$, the modelled transitions using an LTE radiative transfer analysis in the two continuum bands are compatible with the observations within the noise. However, the LTE spectrum (Fig. [11](#fig: ch3o13cho), at the frequency of the middle group of 246788.406 MHz) presents a shift in velocity for the three components that might be explained by an unidentified transition at this position that is not reported in the CDMS and JPL databases, or by an incorrect frequency in the CH$_{3}$O$^{13}$CHO database. The quoted uncertainty of the database frequency is only 2 kHz, which cannot explain this shift. The 246.788 GHz line also appears in the Orion spectra (cite: Carvajal2009), and it is well underestimated by the model with a clear shift as well. However, the authors did not explain this particular shift. Considering the noise and the spectral resolution of our observations for this transition, we cannot conclude on a firm detection of the methyl formate isotopologue.

We used the CH$_{3}$OCHO and CH$_{3}$OCH$_{3}$ LTE modelling to obtain a good estimate of the formic acid column density. The 246.106 and 247.514 GHz lines are blended with methyl formate and are underestimated by the LTE model when formic acid is not taken into account. Taking the three components with the same beam size, excitation temperature, and $V_{LSR}$ as derived from the methyl formate and dimethyl ether into account, we obtained the column densities quoted in Table [\[tab: LTE\]](#tab: LTE). The 246.106 and 247.514 GHz lines are now better reproduced by the LTE model. When methanol is again used as a reference, we obtain a t-HCOOH/CH$_3$OH  ratio of \[0.01, 0.5\] $\%$.\
We present on the right side of Fig. [8](#fig: spec-h2cco) the only transition for ketene, as discussed in Sect. [3](#sec: line-id). The column densities can be constrained from the LTE modelling, again using the excitation temperature, filling factor, and FWHM as for CH$_3$OCH$_3$ and CH$_3$OCHO. The results are presented in Table [\[tab: LTE\]](#tab: LTE) with a H$_2$CCO/CH$_3$OH ratio of \[0.01, 0.1\] $\%$, which is very similar to the t-HCOOH/CH$_3$OH ratio.\
An upper limit for acetaldehyde column density can be estimated at about 1/70th compared to the methanol column density. In Fig. [7](#fig: spec-ch3ocho), the transition at 234.486 GHz (see Table [2](#tab: spectro)) is not well reproduced. However, it might be contaminated by an acetaldehyde transition at 234.486 GHz (see Table [\[tab: spectroND\]](#tab: spectroND)), which is within the upper limit value calculated above (0.15 K for this transition for a 0.115 K $rms$). We also evaluated the upper limit of the C$_2$H$_5$CN and C$_2$H$_3$CN column densities for each velocity component with the LTE analysis. The derivation of the upper limits is described in the appendix. We obtained C$_2$H$_5$CN/CH$_3$OH and C$_2$H$_3$CN/CH$_3$OH to be $<$0.066 % and $<$0.018 %, respectively.

# Discussion

## Origin of the emission of iCOMs in \[BHB2007\] 11

The spatial distribution of iCOMs in hot corinos around Class 0 protostars is known to be compact and to peak at the location of the dust continuum peak, which corresponds to the location of the central source (cite: LopezSepulcre2017; Jorgensen2018). In contrast, \[BHB2007\] 11 shows hot methanol gas that is not exactly associated with the location of the central protostars of the binary system, 11A and 11B, but distributed across the circumbinary disk (cite: Vastel2022). Even though the binary system cannot be resolved in the FAUST images, the 2D Gaussian centroid map of the hot methanol line at 243.916 GHz reveals that this emission appears to be slightly offset with respect to 11A ($\sim$ 20 au) and towards the north-west and south-east of 11B ($\sim$ 20 au from the hot core), at the intersection between filaments seen in the dust emission. The non-LTE analysis of the methanol lines tells us that the gas is hot ($\sim$ 120 K) and dense \[0.2, 25\] $\times$ 10$^{7}$ cm$^{-3}$ (cite: Vastel2022). The dust in between 11A and 11B could be warm enough for the methanol to sublimate, but the iCOM emission does not peak on the hot cores themselves, which seems to rule this hypothesis out. Alternatively, the hot methanol gas could be associated with shocked gas. From the theoretical point of view, shocks may occur in mass-transferring binary systems, where spiral shocks are induced by disturbances and accretion within the disk (cite: Spruit1987; Ju2016). They also occur as streaming gas from the circumbinary disk to the circumstellar disks (cite: Mosta2019) and impact streams close to the inner edge of the circumbinary disk (cite: Shi2012).

In (cite: Vastel2022), we proposed that hot methanol arises from shocked gas associated with an accretion gas streamer falling onto source 11B, which induces a shock interaction that is strong enough to inject species from the ice mantles in the gas phase. The impact is sufficient to overcome the binding energies, and this mechanism is called sputtering (cite: Draine1995). (cite: Alves2019) already suggested that the filaments surrounding \[BHB2007\] 11 are accretion streamers from the extended circumbinary disk onto the circumstellar disks of the protobinary system, from large- to small-scale structures. This streaming material would impact either on the quiescent gas of the circumbinary envelope or possibly on the two circumstellar disks. Recently, the impact of these accreting streamers on the gas chemical enrichment has been observed in some very few sources, in addition to the indirect case of \[BHB2007\] 11 : the Class II sources DG Tau and HL Tau (cite: Garufi2022), and the Class I source SVS13 A (cite: Bianchi2023; Hsieh2023). In addition, only a few simple species have been detected in these streamer-triggered shocks so far: SO, SO$_2$, DCN, and HDO (cite: Garufi2022; Hsieh2023), and only one iCOM, formamide (cite: Bianchi2023). In this context, it is very important to assess whether the detected methyl formate, dimethyl ether, formic acid, and ketene towards \[BHB2007\] 11 can be attributed to shocks caused by gas streamers because this would be the richest gas enrichment observed so far. On the right side of Fig. [5](#fig: 3comp-ch3och3), we showed that the emission from hot CH$_3$OCH$_3$ gas presents a 2D Gaussian centroid distribution that is similar to the distribution for hot methanol, indicating that the two species are affected by the same physical process. The moment 0 maps of CH$_3$OCH$_3$ and CH$_3$OCHO presented in Fig. [2](#fig: mom0-ch3och3) and [6](#fig: mom0-ch3ocho) clearly show a shifted peaked emission in the southern region of 11B. This southern emission can be compared with the high spatial resolution dust continuum map from (cite: Alves2019), where the two hot cores are identified with a complex filamentary structure in their surroundings (right side of Fig. [5](#fig: 3comp-ch3och3)). This supports the idea of the release into the gas phase of molecular species from shocks close to 11B rather than the emission from thermally desorbed species. In the latter case, the emission should have been symmetric and centred towards the two sources, 11A and 11B, whereas the maps show a compact emission in the southern position alone. On the other hand, the moment 0 map of ketene (see Fig. [8](#fig: spec-h2cco)) shows that the emission is likely peaked in between 11A and 11B. In addition, it shows extended emission that follows the bright southern filament (Fig. [5](#fig: 3comp-ch3och3)) observed by (cite: Alves2019) in the dust continuum. Therefore, ketene could be tracing a more extended region, likely the warm gas streaming in from the circumbinary disk, rather than the shocked regions at the end of the streamer.

The compact emission of iCOMs and the more extended emission of ketene would not be surprising from a chemical point of view. While iCOMs have very low abundances in cold ($\leq20$ K) gas (cite: Vastel2014; Jimenez2016)because of their formation routes and binding energies (cite: Ceccarelli2023), ketene is observed in cold gas with an abundance about a factor 10 higher than iCOMs (cite: Jaber2014; Vastel2014), in agreement with the more extended emission in our observations.

As mentioned in the Introduction, the protobinary system is still deeply embedded in its natal cloud and far from any variable stars. Therefore, although external irradiation could produce shifted emission of molecular species from a protostellar core like this (cite: Lindberg2012; Lindberg2015), the location of \[BHB2007\] 11 and the derived high gas temperature at which the iCOMs are emitted rules this possibility out.

In summary, our observations suggest that the shocks caused by the streaming gas crashing onto quiescent material surrounding \[BHB2007\] 11, likely its circumbinary disk, enrich the gas in iCOMs. We clearly detect methanol, methyl formate, and dimethyl ether, which are among the iCOMs with the highest observed abundances in molecular shocks: X(CH$_3$OH)=(5.0$\pm$1.0)$\times$10$^{-7}$, X(CH$_3$OCHO)=(2.7$\pm$0.7)$\times$10$^{-8}$, and X(CH$_3$OCH$_3$)=(2.5$\pm$0.7)$\times$10$^{-8}$ for L1157-B1 (cite: Lefloch2017), and CH$_3$OH/CH$_3$OCH$_3$$\sim$ 1 for the IRAS 4A outflow (cite: DeSimone2020-I4outflow).

## Comparison with other protostellar sources

The possible presence of shocks associated with accretion or ejection occurring very close to the central accreting objects and at the origin of iCOM emission, such as in \[BHB2007\] 11, has also been invoked towards G328.2551-0.5321 (cite: Csengeri2019), IRAS16293 A (cite: Maureira2022), and SVS13A (cite: Bianchi2023). Towards the high-mass star-forming region G328.2551-0.5321, (cite: Csengeri2019) reported a differential distribution of some O-bearing iCOMs (ethanol, acetone, and ethylene glycol) with respect to some N-bearing iCOMs (vinyl and ethyl cyanide), as found in \[BHB2007\] 11, and the other detected iCOMs (e.g. methanol, acetaldehyde, and methyl cyanide). Specifically, the emission from ethanol, acetone, and ethylene glycol peaks roughly perpendicular to the outflow direction and is offset from the continuum emission peak by about 700 au (i.e. one beam), whereas the emission peak of the remaining iCOMs coincides with the dust peak. (cite: Csengeri2019) argued that the iCOM emission offset from the dust peak is due to accretion shocks resulting from the impact of infalling gas. However, higher spatial resolution observations are necessary to resolve the iCOM emission, and thereby, confirm their exact origin (shocks associated with accretion, ejection, or different processes). In addition, our non-detection of C$_2$H$_5$CN and C$_2$H$_3$CN (see the appendix) provides an upper limit to the C$_2$H$_5$CN/CH$_3$OH and C$_2$H$_3$CN/CH$_3$OH abundance ratios of $<$0.07 % and $<$0.02 %, respectively, which are much lower than those measured in G328.2551-0.5321, namely 0.57 and 0.17 %, respectively (cite: Csengeri2019). Therefore, the comparison between \[BHB2007\] 11and G328.2551-0.5321 is inconclusive.\
In the same context, in IRAS16293 A, (cite: Maureira2022) found hot ($\geq$ \[50, 120\] K) spots of dust continuum emission, which the authors interpreted as due to shocks from infalling or outflowing gas very close to the central object (on scales of $\sim$10 au). The line emission from formamide and formic acid also seems to be slightly enhanced in these shocks (cite: Maureira2020; Maureira2022).\
It is worth mentioning that the dust opacity could be a major actor in the observed apparent spatial distribution of iCOMs, as shown by (cite: Vastel2022; Desimone2020-VLA) (see also the discussion in (cite: Rivilla2017) and (cite: Lee2022)). Specifically, (cite: Desimone2020-VLA) showed that towards the hot corino NGC1333 IRAS 4A1, methanol line emission is easily detected in the radio by VLA, but is undetected in the 1 and 2 millimeter by ALMA and NOEMA (cite: LopezSepulcre2017). Both G328.2551-0.5321 and IRAS16293 A have high dust column densities, and the observations were carried out at frequencies of about 350 and 220 GHz, respectively, where the dust opacity is likely to be higher than in NGC1333 IRAS 4A1, especially towards G328.2551-0.5321.

Finally, for SVS13A, (cite: Bianchi2023) imaged (on scales of $\sim$50 au) three features elongated in the direction of known larger-scale streamers of gas falling towards the two central objects of the binary system VLA4A and VLA4B. The features are enriched in formamide (the only iCOM they searched for in their observations), in addition to HDO and SO$_2$. In this case, the image clearly shows formamide emission at the base of the gas streamers. The iCOMs observed towards \[BHB2007\] 11  are likely due to similar shocks.

To evaluate even further whether the iCOMs emission detected towards \[BHB2007\] 11  arise from shocked accreting gas, we list in Table [\[tab: comp\]](#tab: comp) the abundance ratios with respect to methanol of the iCOMs and some precursors detected in this work, as measured towards \[BHB2007\] 11  and of the solar-like Class 0 and I hot corinos of IRAS 16293 A (cite: Manigand2020) and SVS13A (cite: Bianchi2019; Bianchi2022), respectively, along with the protostellar shock region L1157-B1 (cite: Lefloch2017). In the following, we briefly discuss the five species reported in the table.

|  |  |  | X(iCOMs)/X(CH$_3$OH) |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Species |  | \[BHB2007\] 11 | IRAS 16293 A | L1157-B1 | SVS 13-A |
| Methyl formate | CH$_3$OCHO | \[2.5, 4.5\] $\%$ | $(2\pm 1)\%$ | (5.4$\pm$1.0)$\%$ | (1.9$\pm$0.4)$\%$ |
| Dimethyl ether | CH$_3$OCH$_3$ | \[0.5, 0.8\] $\%$ | $(4\pm 2)\%$ | (4.9$\pm$1.0)$\%$ | (2.1$\pm$0.7)$\%$ |
| Formic acid | t-HCOOH | \[0.01, 0.5\] $\%$ | $(0.10\pm0.04)\%$ | (1.7$\pm$0.3)$\%$ | $\le 0.07\%$ |
| Ketene | H$_2$CCO | \[0.01, 0.1\] $\%$ | $(0.07\pm 0.03)\%$ | (1.7$\pm$0.7)$\%$ | (0.19$\pm$0.06)$\%$ |
| Acetaldehyde | CH$_{3}$CHO | $\le$ 1.5$\%$ | $(0.03 \pm 0.01)\%$ | (0.6$\pm$0.10)–(4.2$\pm$0.1)$\%$ | (0.18$\pm$0.11)$\%$ |

#### Methyl formate and dimethyl ether

The CH$_3$OCHO/CH$_3$OH  abundance ratio derived in \[BHB2007\] 11 is consistent with that measured in the Class 0 and I hot corinos of Table [\[tab: comp\]](#tab: comp) (see also Fig. 3 of (cite: Bianchi2019) and Fig. 4 of (cite: vanGelder2020)) as well as towards the shocked region L1157-B1 (cite: Lefloch2017). Likewise, the CH$_3$OCH$_3$/CH$_3$OH  abundance ratio towards \[BHB2007\] 11  is comparable to that measured in other hot corinos (cite: Bianchi2019; vanGelder2020). Conversely, CH$_3$OCH$_3$/CH$_3$OH  is slightly lower than that measured towards the shocked regions L1157-B1 (cite: Lefloch2017) and in the outflow shocks of NGC1333 IRAS 4A (cite: DeSimone2020-I4outflow). The CH$_3$OCH$_3$/CH$_3$OCHO  abundance ratio \[0.1, 0.3\] in \[BHB2007\] 11 lies at the lower end of the correlation observed by several authors between these two molecules (cite: Jaber2014; Brouillet2013; Belloche2020; Coletta2020; Yang2021; Chahine2022). The observed correlation (CH$_3$OCH$_3$/CH$_3$OCHO$\sim$ 1) may imply a sister-sister or mother-daughter relation between methyl formate and dimethyl ether. (cite: Balucani2015) suggested that the second relation applies: Methyl formate is synthesised from methyl ether via a chain of two gas-phase reactions. Alternatively, both species are synthesised on the grain surfaces (cite: Garrod2008). However, these routes have been studied theoretically and their efficiency is not obvious, given the competition of the combination of radicals with the H atom abstraction in each reaction (cite: Enrique-Romero2022). However, the recent model by (cite: Garrod2022) needs the introduction of poorly studied diffusive reactions to enhance the dimethyl ether to the observed values. (cite: Chahine2022) measured CH$_3$OCH$_3$/CH$_3$OCHO equal to $\sim0.2$ towards the HOPS-108 hot corino in the OMC-2 FIR 4 protocluster. This value is similar to that measured towards \[BHB2007\] 11. These authors tried to verify whether a very different cosmic-ray ionisation rate could explain this difference with respect to the other sources. They concluded, however, that cosmic rays do not play a role in shaping the abundance of CH$_3$OCH$_3$ relative to that of CH$_3$OCHO  (see their Fig. B.10). If the two species are linked by gas-phase reactions, another poorly known parameter that could affect the CH$_3$OCHO/CH$_3$OCH$_3$  ratio is the abundance of atomic oxygen, which may be different in the shocked gas of \[BHB2007\] 11 .

#### Formic acid

Table [\[tab: comp\]](#tab: comp) shows that the formic acid versus methanol ratio estimated in our observations is lower by a factor of 3 than the shocked region of L1157 (cite: Lefloch2017), but comparable to the value found in IRAS 16293 B (cite: Manigand2020).

#### Ketene

Like in the case of formic acid, the H$_2$CCO/CH$_3$OH  abundance ratio in \[BHB2007\] 11  is more similar to that measured in hot corinos than in the L1157-B1 shock. However, the latter is the only reported ketene detection in a shocked region so far, and it is therefore premature to draw firm conclusions. In addition, we report that in \[BHB2007\] 11, ketene emission is more extended than in the other detected iCOMs (see Sec. [4](#sec: results)), which is an argument for an origin in the gas phase likely belonging to the extended envelope surrounding \[BHB2007\] 11. As several simple hydrocarbons, ketene is observed in hot and cold gas (cite: Jaber2014; Zhou2022). In the gas phase, it is formed from the oxidation of smaller hydrocarbons (e.g. C$_2$H$_3$ + O), while on the grain surface, it can be formed by the reaction of C atoms landing on CO-rich ice (cite: Ferrero2023). In the case of \[BHB2007\] 11, the extended emission would be more easily explained by gas-phase reactions.

#### Acetaldehyde

Table [\[tab: comp\]](#tab: comp) shows that the upper limit that we derived from the observations towards \[BHB2007\] 11  is consistent with the values observed in hot corino IRAS 16293 B (cite: Manigand2020) and the shocked region L1157-B1 (cite: Lefloch2017). Our $rms$ is too high to be able to explain the non-detection of this species.

# Conclusions

We presented the ALMA observations towards the protobinary system \[BHB2007\] 11 within the framework of the FAUST Large Program. We reported the detection of iCOMs and iCOMs precursors, such as CH$_3$OCH$_3$, CH$_3$OCHO, t-HCOOH, and H$_2$CCO. The spatial distribution showed that the emission is confined within the ALMA beam, and the velocity distribution shows three different spatial regions. They are comparable with the methanol emission from previous observations of (cite: Vastel2022). The detected iCOMs are associated with three hot spots, two of which lie close to 11B, and the third hot spot lies near 11A, with a source size of $\sim$ 0.15$^{\prime\prime}$, which is well below the $\sim$ 0.4$^{\prime\prime}$ beam size. These molecular species are likely the result of the shocked material from the incoming filaments that streams towards \[BHB2007\] 11 A and B, shown in our integrated intensity maps compared to the dust emission revealing the filamentary structures. Radiative transfer modelling was used to reproduce the many detected transitions and compute the abundance ratios with respect to methanol for methyl formate, dimethyl ether, ketene, formic acid, and an upper limit for acetaldehyde. We then compared the ratios to Class 0 and Class I protostars as well as with the L1157-B1 shocked region. The CH$_3$OCHO/CH$_3$OH as well as CH$_{3}$CHO/CH$_3$OH ratios are similar in all sources, but H$_{2}$CCO/CH$_3$OH and t-HCOOH/CH$_3$OH are much lower. Our CH$_3$OCH$_3$/CH$_3$OCHO ratio of \[0.1, 0.3\] is slightly lower (factor of 3 to 10) than the correlation found in low- and high-mass protostars. Our observations suggest that the shocks caused by the streaming gas crashing onto quiescent material surrounding \[BHB2007\] 11 can enrich the gas in iCOMs.

# Acknowledgements

This project has received funding within the European Union’s Horizon 2020 research and innovation program from the European Research Council (ERC) for the project *The Dawn of Organic Chemistry* (DOC, grant agreement No. 741002) and for the project *Dust2Planets* (grant agreement No. 101053020), and from the Marie Sklodowska-Curie action for the project *Astro-Chemical Origins* (ACO, grant agreement No. 811312). S.B.C. was supported by the NASA Planetary Science Division Internal Scientist Funding Program through the Fundamental Laboratory Research work package (FLaRe). M.B. acknowledges support from the ERC under the European Union’s Horizon 2020 research and innovation program MOPPEX 833460. I.J-.S acknowledges funding from grants No. PID2019-105552RB-C41 and PID2022-136814NB-I00 from the Spanish Ministry of Science and Innovation/State Agency of Research MCIN/AEI/10.13039/501100011033 and by *ERDF A way of making Europe*. S.Y. thanks the support by Grant-in-Aids from Ministry of Education, Culture, Sports, Science, and Technologies of Japan (18H05222). L.L. acknowledges DGAPA PAPIIT grants IN112820 and IN108324, and CONAHCYT-CF grant 263356. G.S., C.C. and L.P. acknowledge the project PRIN-MUR 2020 MUR BEYOND-2p *Astrochemistry beyond the second period elements*, Prot. 2020AFB3FX. G.S. also acknowledges support from the INAF-Minigrant 2023 TRIESTE *TRacing the chemIcal hEritage of our originS: from proTostars to planEts*. T.S. thanks the support by Grant-in-Aids from Ministry of Education, Culture, Sports, Science, and Technologies of Japan (20K04025, 20H05845, and 18H05222).

72 natexlab

(ref: Alves2019) Alves, F. O., Caselli, P., Girart, J. M., et al. 2019, Science, 366, 90

(ref: Arce2008) Arce, H. G., Santiago-Garcı́a, J., Jørgensen, J. K., Tafalla, M., & Bachiller, R. 2008, ApJL, 681, L21

(ref: Balucani2015) Balucani, N., Ceccarelli, C., & Taquet, V. 2015, MNRAS, 449, L16

(ref: Belloche2020) Belloche, A., Maury, A. J., Maret, S., et al. 2020, A&A, 635, A198

(ref: Bianchi2019) Bianchi, E., Codella, C., Ceccarelli, C., et al. 2019, MNRAS, 483, 1850

(ref: Bianchi2022) Bianchi, E., López-Sepulcre, A., Ceccarelli, C., et al. 2022, ApJL, 928, L3

(ref: Bianchi2023) Bianchi, E., López-Sepulcre, A., Ceccarelli, C., et al. 2023, Faraday Discussions, 245, 164

(ref: Bottinelli2004) Bottinelli, S., Ceccarelli, C., Lefloch, B., et al. 2004, ApJ, 615, 354

(ref: Brooke2007) Brooke, T. Y., Huard, T. L., Bourke, T. L., et al. 2007, ApJ, 655, 364

(ref: Brouillet2013) Brouillet, N., Despois, D., Baudry, A., et al. 2013, A&A, 550, A46

(ref: Brown1990) Brown, R. D., Godfrey, P. D., McNaughton, D., Pierlot, A. P., & Taylor, W. H. 1990, Journal of Molecular Spectroscopy, 140, 340

(ref: Carvajal2010) Carvajal, M., Kleiner, I., & Demaison, J. 2010, ApJS, 190, 315

(ref: Carvajal2009) Carvajal, M., Margulès, L., Tercero, B., et al. 2009, A&A, 500, 1109

(ref: Cazaux2003) Cazaux, S., Tielens, A. G. G. M., Ceccarelli, C., et al. 2003, ApJL, 593, L51

(ref: Ceccarelli2004) Ceccarelli, C. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 323, Star Formation in the Interstellar Medium: In Honor of David Hollenbach, ed. D. Johnstone, F. C. Adams, D. N. C. Lin, D. A. Neufeeld, & E. C. Ostriker, 195

(ref: Ceccarelli2017) Ceccarelli, C., Caselli, P., Fontani, F., et al. 2017, ApJ, 850, 176

(ref: Ceccarelli2023) Ceccarelli, C., Codella, C., Balucani, N., et al. 2023, in Astronomical Society of the Pacific Conference Series, Vol. 534, Astronomical Society of the Pacific Conference Series, ed. S. Inutsuka, Y. Aikawa, T. Muto, K. Tomida, & M. Tamura, 379

(ref: Chahine2022) Chahine, L., López-Sepulcre, A., Neri, R., et al. 2022, A&A, 657, A78

(ref: Charnley1997) Charnley, S. B. 1997, in IAU Colloq. 161: Astronomical and Biochemical Origins and the Search for Life in the Universe, ed. C. Batalli Cosmovici, S. Bowyer, & D. Werthimer, 89

(ref: Charnley2008) Charnley, S. B. & Rodgers, S. D. 2008, Space Sci. Rev., 138, 59

(ref: Codella2021) Codella, C., Ceccarelli, C., Chandler, C., et al. 2021, Frontiers in Astronomy and Space Sciences, 8, 227

(ref: Codella2015) Codella, C., Fontani, F., Ceccarelli, C., et al. 2015, MNRAS, 449, L11

(ref: Coletta2020) Coletta, A., Fontani, F., Rivilla, V. M., et al. 2020, A&A, 641, A54

(ref: Condon1997) Condon, J. J. 1997, PASP, 109, 166

(ref: Condon1998) Condon, J. J., Cotton, W. D., Greisen, E. W., et al. 1998, AJ, 115, 1693

(ref: Csengeri2019) Csengeri, T., Belloche, A., Bontemps, S., et al. 2019, A&A, 632, A57

(ref: Desimone2020-VLA) De Simone, M., Ceccarelli, C., Codella, C., et al. 2020a, ApJL, 896, L3

(ref: DeSimone2020-I4outflow) De Simone, M., Codella, C., Ceccarelli, C., et al. 2020b, A&A, 640, A75

(ref: Draine1995) Draine, B. T. 1995, Ap&SS, 233, 111

(ref: Dzib2018) Dzib, S. A., Loinard, L., Ortiz-León, G. N., Rodrı́guez, L. F., & Galli, P. A. B. 2018, ApJ, 867, 151

(ref: Endres2009) Endres, C. P., Drouin, B. J., Pearson, J. C., et al. 2009, A&A, 504, 635

(ref: Enrique-Romero2022) Enrique-Romero, J., Rimola, A., Ceccarelli, C., et al. 2022, ApJS, 259, 39

(ref: Evans2023) Evans, L., Vastel, C., Fontani, F., et al. 2023, A&A, 678, A160

(ref: Ferrero2023) Ferrero, S., Ceccarelli, C., Ugliengo, P., Sodupe, M., & Rimola, A. 2023, ApJ, 951, 150

(ref: Fontani2007) Fontani, F., Pascucci, I., Caselli, P., et al. 2007, A&A, 470, 639

(ref: Garrod2022) Garrod, R. T., Jin, M., Matis, K. A., et al. 2022, ApJS, 259, 1

(ref: Garrod2008) Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ, 682, 283

(ref: Garufi2022) Garufi, A., Podio, L., Codella, C., et al. 2022, A&A, 658, A104

(ref: Herbst2009) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427

(ref: Hsieh2023) Hsieh, T. H., Segura-Cox, D. M., Pineda, J. E., et al. 2023, A&A, 669, A137

(ref: Hudson2013) Hudson, R. L. & Loeffler, M. J. 2013, ApJ, 773, 109

(ref: Ilyushin2009) Ilyushin, V., Kryvda, A., & Alekseev, E. 2009, Journal of Molecular Spectroscopy, 255, 32

(ref: Jaber2014) Jaber, A. A., Ceccarelli, C., Kahane, C., & Caux, E. 2014, ApJ, 791, 29

(ref: Jimenez2016) Jiménez-Serra, I., Vasyunin, A. I., Caselli, P., et al. 2016, ApJL, 830, L6

(ref: Jorgensen2018) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170

(ref: Jorgensen2016) Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595, A117

(ref: Ju2016) Ju, W., Stone, J. M., & Zhu, Z. 2016, ApJ, 823, 81

(ref: Kleiner1996) Kleiner, I., Lovas, F. J., & Godefroid, M. 1996, Journal of Physical and Chemical Reference Data, 25, 1113

(ref: Kryvda2009) Kryvda, A. V., Gerasimov, V. G., Dyubko, S. F., Alekseev, E. A., & Motiyenko, R. A. 2009, Journal of Molecular Spectroscopy, 254, 28

(ref: Lee2022) Lee, C.-F., Codella, C., Ceccarelli, C., & López-Sepulcre, A. 2022, ApJ, 937, 10

(ref: Lefloch2017) Lefloch, B., Ceccarelli, C., Codella, C., et al. 2017, MNRAS, 469, L73

(ref: Lindberg2012) Lindberg, J. E. & Jørgensen, J. K. 2012, A&A, 548, A24

(ref: Lindberg2015) Lindberg, J. E., Jørgensen, J. K., Watanabe, Y., et al. 2015, A&A, 584, A28

(ref: LopezSepulcre2017) López-Sepulcre, A., Sakai, N., Neri, R., et al. 2017, A&A, 606, A121

(ref: Manigand2020) Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48

(ref: Maureira2022) Maureira, M. J., Gong, M., Pineda, J. E., et al. 2022, ApJL, 941, L23

(ref: Maureira2020) Maureira, M. J., Pineda, J. E., Segura-Cox, D. M., et al. 2020, ApJ, 897, 59

(ref: Milam2005) Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005, ApJ, 634, 1126

(ref: Morris1980) Morris, M., Palmer, P., & Zuckerman, B. 1980, ApJ, 237, 1

(ref: Mosta2019) Mösta, P., Taam, R. E., & Duffell, P. C. 2019, ApJL, 875, L21

(ref: Muller2005) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: Onishi1999) Onishi, T., Kawamura, A., Abe, R., et al. 1999, PASJ, 51, 871

(ref: Pickett1998) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: Rivilla2017) Rivilla, V. M., Beltrán, M. T., Cesaroni, R., et al. 2017, A&A, 598, A59

(ref: Shi2012) Shi, J.-M., Krolik, J. H., Lubow, S. H., & Hawley, J. F. 2012, ApJ, 749, 118

(ref: Spruit1987) Spruit, H. C. 1987, A&A, 184, 173

(ref: vanGelder2020) van Gelder, M. L., Tabone, B., Tychoniec, Ł., et al. 2020, A&A, 639, A87

(ref: Vastel2022) Vastel, C., Alves, F., Ceccarelli, C., et al. 2022, A&A, 664, A171

(ref: Vastel2014) Vastel, C., Ceccarelli, C., Lefloch, B., & Bachiller, R. 2014, ApJL, 795, L2

(ref: Winnewisser2002) Winnewisser, M., Winnewisser, B. P., Stein, M., et al. 2002, Journal of Molecular Spectroscopy, 216, 259

(ref: Yang2021) Yang, Y.-L., Sakai, N., Zhang, Y., et al. 2021, ApJ, 910, 20

(ref: Zhou2022) Zhou, C., Vastel, C., Montillaud, J., et al. 2022, A&A, 658, A131

# Details for the observed transitions

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Frequency | Quantum numbers | $E_{up}$ | $A_{ul}$ | $g_{up}$ | Original beam, $PA$ | $rms$ | $\delta V$ |
| (MHz) | ($J, K_{a}, K_{c}, v_{t}$) | \(K\) | (s$^{-1}$) |  | ($^{\prime\prime} \times ^{\prime\prime}$,$^{\circ}$) | \(K\) | (km s$^{-1}$) |
|  |  |  |  |  |  |  |  |
| Frequency | Quantum numbers | $E_{up}$ | $A_{ul}$ | $g_{up}$ | Original beam, $PA$ | $rms$ | $\delta V$ |
| (MHz) | ($J, K_{a}, K_{c}, v_{t}$) | \(K\) | (s$^{-1}$) |  | ($^{\prime\prime} \times ^{\prime\prime}$,$^{\circ}$) | \(K\) | (km s$^{-1}$) |
|  |  |  | CH$_3$OCH$_3$$^{a}$ |  |  |  |  |
| 257915.5190 | 18$_{5,13,0}$ – 18$_{4,14,0}$ | 190.97 | 8.76 10$^{-5}$ | 222 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257913.3120 | 18$_{5,13,1}$ – 18$_{4,14,1}$ | 190.97 | 8.76 10$^{-5}$ | 592 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257911.1750 | 18$_{5,13,3}$ – 18$_{4,14,3}$ | 190.97 | 8.76 10$^{-5}$ | 148 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257911.0360 | 18$_{5,13,5}$ – 18$_{4,14,5}$ | 190.97 | 8.77 10$^{-5}$ | 74 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 258549.3080 | 14$_{1,14,0}$ – 13$_{0,13,0}$ | 93.33 | 1.31 10$^{-4}$ | 290 | 0.44 $\times$ 0.38, -82 | 0.1469 | 0.14 |
| 258549.0630 | 14$_{1,14,1}$ – 13$_{0,13,1}$ | 93.33 | 1.31 10$^{-4}$ | 464 | 0.44 $\times$ 0.38, -82 | 0.1469 | 0.14 |
| 258548.8190 | 14$_{1,14,3}$ – 13$_{0,13,3}$ | 93.33 | 1.31 10$^{-4}$ | 116 | 0.44 $\times$ 0.38, -82 | 0.1469 | 0.14 |
| 258548.8190 | 14$_{1,14,5}$ – 13$_{0,13,5}$ | 93.33 | 1.31 10$^{-4}$ | 174 | 0.44 $\times$ 0.38, -82 | 0.1469 | 0.14 |
|  |  |  | CH$_3$OCHO$^{b}$ |  |  |  |  |
| 233212.773 | 19$_{4,16,1}$ – 18$_{4,15,1}$ | 123.26 | 1.82 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233226.788 | 19$_{4,16,0}$ – 18$_{4,15,0}$ | 123.25 | 1.82 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233649.88 | 19$_{12,7,2}$ – 18$_{12,6,2}$ | 207.62 | 1.16 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233655.342 | 19$_{12,8,0}$ – 18$_{12,7,0}$ | 207.62 | 1.16 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233655.342 | 19$_{12,7,0}$ – 18$_{12,6,0}$ | 207.62 | 1.16 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233670.980 | 19$_{12,8,1}$ – 18$_{12,7,1}$ | 207.60 | 1.16 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233753.960 | 18$_{4,14,2}$ – 17$_{4,13,2}$ | 114.37 | 1.84 10$^{-4}$ | 74 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233777.521 | 18$_{4,14,0}$ – 17$_{4,13,0}$ | 114.36 | 1.84 10$^{-4}$ | 74 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233845.233 | 19$_{11,8,2}$ – 18$_{11,7,2}$ | 192.39 | 1.29 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233854.286 | 19$_{11,9,0}$ – 18$_{11,8,0}$ | 192.39 | 1.29 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233854.286 | 19$_{11,8,0}$ – 18$_{11,7,0}$ | 192.39 | 1.29 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 233867.193 | 19$_{11,9,1}$ – 18$_{11,8,1}$ | 192.38 | 1.29 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234112.330 | 19$_{10,9,2}$ – 18$_{10,8,2}$ | 178.51 | 1.40 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234124.883 | 19$_{10,9,0}$ – 18$_{10,8,0}$ | 178.50 | 1.40 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234124.883 | 19$_{10,10,0}$ – 18$_{10,9,0}$ | 178.50 | 1.40 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234134.600 | 19$_{10,10,1}$ – 18$_{10,9,1}$ | 178.50 | 1.40 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234486.395 | 19$_{9,10,2}$ – 18$_{9,9,2}$ | 165.98 | 1.51 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234502.2407 | 19$_{9,11,0}$ – 18$_{9,10,0}$ | 165.97 | 1.51 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234502.4315 | 19$_{9,10,0}$ – 18$_{9,9,0}$ | 165.97 | 1.51 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 234508.614 | 19$_{9,11,1}$ – 18$_{9,10,1}$ | 165.97 | 1.51 10$^{-4}$ | 78 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |
| 245883.179 | 20$_{13,7,2}$ – 19$_{13,6,2}$ | 235.98 | 1.30 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 245885.243 | 20$_{13,7,0}$ – 19$_{13,6,0}$ | 235.98 | 1.30 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 245885.243 | 20$_{13,8,0}$ – 19$_{13,7,0}$ | 235.98 | 1.30 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 245903.680 | 20$_{13,8,1}$ – 19$_{13,7,1}$ | 235.97 | 1.30 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246187.016 | 21$_{2,19,3}$ – 20$_{2 ,18,3}$ | 326.63 | 2.18 10$^{-4}$ | 86 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246600.012 | 20$_{10,10,2}$ – 19$_{10,9,2}$ | 190.35 | 1.70 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246613.392 | 20$_{10,10,0}$ – 19$_{10,9,0}$ | 190.34 | 1.70 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246613.392 | 20$_{10,11,0}$ – 19$_{10,10,0}$ | 190.34 | 1.70 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246615.129 | 20$_{5,16,3}$ – 19$_{5,15,3}$ | 328.24 | 2.12 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246623.190 | 20$_{10,11,1}$ – 19$_{10,10,1}$ | 190.33 | 1.70 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246891.611 | 19$_{4,15,2}$ – 18$_{4,14,2}$ | 126.22 | 2.18 10$^{-4}$ | 78 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 246914.658 | 19$_{4,15,0}$ – 18$_{4,14,0}$ | 126.21 | 2.18 10$^{-4}$ | 78 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247040.65 | 20$_{9,11,2}$ – 19$_{9,10,2}$ | 177.84 | 1.82 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247044.146 | 21$_{3,19,1}$ – 20$_{3,18,1}$ | 139.90 | 2.21 10$^{-4}$ | 86 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247053.453 | 21$_{3,19,0}$ – 20$_{3,18,0}$ | 139.89 | 2.21 10$^{-4}$ | 86 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247057.2591 | 20$_{9,12,0}$ – 19$_{9,11,0}$ | 177.83 | 1.82 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247057.7373 | 20$_{9,11,0}$ – 19$_{9,10,0}$ | 177.83 | 1.82 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247063.662 | 20$_{9,12,1}$ – 19$_{9,11,1}$ | 177.82 | 1.82 10$^{-4}$ | 82 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247469.2492 | 23$_{1,23,3}$ – 22$_{1,22,3}$ | 332.88 | 2.28 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247469.5853 | 23$_{0,23,3}$ – 22$_{0,22,3}$ | 332.88 | 2.28 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247516.3123 | 23$_{0,23,5}$ – 22$_{0,22,5}$ | 332.13 | 2.29 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247516.0121 | 23$_{1,23,4}$ – 22$_{1,22,4}$ | 332.13 | 2.29 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 257919.89 | 21$_{16,5,2}$ – 20$_{16,4,2}$ | 306.01 | 1.09 10$^{-4}$ | 86 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257910.566 | 21$_{16,5,0}$ – 20$_{16,4,0}$ | 306.01 | 1.09 10$^{-4}$ | 86 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257910.566 | 21$_{16,6,0}$ – 20$_{16,5,0}$ | 306.01 | 1.09 10$^{-4}$ | 86 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257906.128 | 21$_{8,13,3}$ – 20$_{8,12,3}$ | 365.98 | 2.22 10$^{-4}$ | 86 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
| 257889.872 | 21$_{8,14,3}$ – 20$_{8,13,3 }$ | 365.98 | 2.22 10$^{-4}$ | 86 | 0.44 $\times$ 0.38, -83 | 0.1494 | 0.14 |
|  |  |  | H$_2$CCO$^{c}$ |  |  |  |  |
| 260191.982 | 13$_{1,13}$ – 12$_{1,12}$ | 100.5 | 1.98 10$^{-4}$ | 81 | 0.44 $\times$ 0.37, -83 | 0.1071 | 0.14 |
|  |  |  | t-HCOOH$^{d}$ |  |  |  |  |
| 246105.9739 | 11$_{2,10}$–10$_{2,9}$ | 83.74 | 1.62 10$^{-4}$ | 23 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247446.2439 | 11$_{6,6}$–10$_{6,5}$ | 185.63 | 1.20 10$^{-4}$ | 23 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247513.9713 | 11$_{5,7}$–10$_{5,6}$ | 150.71 | 1.35 10$^{-4}$ | 23 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |
| 247514.1176 | 11$_{5,6}$–10$_{5,5}$ | 150.71 | 1.35 10$^{-4}$ | 23 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |

: continued.

Table notes:\
\
\
\

# Upper limits of $\rm N(C_2H_5CN)$ and $\rm N(C_2H_3CN)$

We present in this section the computation for the upper limits on the nitrogen bearing iCOMs.\
Figure [9](#fig: a1) shows the observed spectra of three C$_2$H$_5$CN lines within 0.82$^{\prime\prime}$$\times$0.77$^{\prime\prime}$ centred at $\alpha$(2000) = 17h11m23.107s, $\delta$(2000) = -27$^{\circ}$24$^{\prime}$33.005$^{\prime\prime}$. The quantum numbers (and spectroscopic parameters from CDMS) associated for the three transitions are listed in Table [\[tab: spectroND\]](#tab: spectroND). Of the three transitions, the 28$_{2,27}$–26$_{2,26}$ line is expected to be strongest. Some features can be seen in Figure [9](#fig: a1), but they are all offset from the velocity of the three velocity components (-2, 2.8, and 9.9 km s$^{-1}$). We can safely conclude that the C$_2$H$_5$CN emission is not detected within the noise.\
Figure [10](#fig: a2) shows the observed spectra of three C$_2$H$_3$CN lines whose quantum numbers (and spectroscopic parameters from CDMS) are listed in Table [\[tab: spectroND\]](#tab: spectroND). Of the three transitions, the C$_2$H$_3$CN 26$_{3,24}$–25$_{3,23}$ line is expected to be strongest. In Figure [10](#fig: a2), we can safely conclude that no C$_2$H$_3$CN emission is detected within the noise. From the observed transitions of C$_2$H$_5$CN 28$_{2,27}$–26$_{2,26}$ and C$_2$H$_3$CN 26$_{3,24}$–25$_{3,23}$, we can evaluate an upper limit on their column densities. For the derivation, we assumed an LTE condition and used the following equation: $$\begin{equation}
N_{total}=\frac{3h}{8\pi^3 \mu^2 S f}Q \frac{\exp\left(\frac{E_{u}}{kT_{\rm ex}}\right)}{\exp\left(\frac{h \nu}{kT_{\rm ex}}\right)-1} \frac{W_u}{J(T_{\rm ex})-J(T_{\rm BB})},
\end{equation}$$ where $h$ is the Planck constant, $Q$ is the partition function, $\nu$ is the rest frequency, $\mu$ is the electric dipole moment, $S$ is the line strength, $f$ is the beam filling factor, $E_{up}$ is the upper state energy, $T_{\rm ex}$ is the excitation temperature, $T_{\rm BB}$ is the temperature of the cosmic background radiation (2.73 K), $W_u$ is the upper limit of integrated intensity, $k$ is the Boltzmann constant, and $J$ is the Planck function for the given temperature and frequency ($\nu$) as $$\begin{equation}
J(T) = \frac{\frac{h\nu}{k}}{\exp\left(\frac{h\nu}{kT}\right)-1}.
\end{equation}$$ The upper limit of the integrated intensity (in K km s$^{-1}$) was calculated from the following equation: $$\begin{equation}
W_{u}= \sigma \delta V \sqrt{\frac{\Delta V}{\delta V}},
\end{equation}$$ where $\sigma$ is the $rms$ noise level of the spectra at the channel width of $\delta V$ (Table [2](#tab: spectro)), and $\Delta V$ is the velocity width of a target. For the calculations, we adopted the parameters from Table [3](#tab: a1). The partition function $Q$ was evaluated using the values reported in the CDMS database. We fit the CDMS data to the function of $Q$($T$) = $a$$\times$$T^b$, where $a$ and $b$ are fitting parameters. For C$_2$H$_5$CN, ($a$, $b$)=(7.2158, 1.4995). For C$_2$H$_3$CN, ($a$, $b$)=(0.95923, 2.0865). The derived upper limits are presented in Table [3](#tab: a1).

![](FIGURES/C2H5CNF.pdf)

![](FIGURES/C2H3CNF.pdf)

|  |  | Velocity components |  |
|:--:|:--:|:--:|:--:|
|  | -2 km s$^{-1}$ | 2.8 km s$^{-1}$ | 9.9 km s$^{-1}$ |
| $N$(C$_2$H$_5$CN) (cm$^{-2}$) | $<$3.5$\times$10$^{14}$ | $<$1.9$\times$10$^{15}$ | $<$2.0$\times$10$^{15}$ |
| $N$(C$_2$H$_3$CN) (cm$^{-2}$) | $<$2.4$\times$10$^{14}$ | $<$5.2$\times$10$^{14}$ | $<$5.4$\times$10$^{14}$ |
| $\theta_S$ ($^{\prime\prime}$) | 0.15 | 0.13 | 0.12 |
| $\Delta V$ (km s$^{-1}$) | 2 | 5 | 4 |
| Temperature (K) | 80 | 80 | 80 |

: Upper limits for $N$(C$_2$H$_5$CN) and $N$(C$_2$H$_3$CN).

Table notes: The identification of the three velocity components is based on the methanol analysis described in (cite: Vastel2022).

# Spectroscopic parameters for the non-detected transitions

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Frequency | Quantum numbers | $E_{up}$ | $A_{ul}$ | $g_{up}$ | Original beam, $PA$ | $rms$$^{a}$ | $\delta V$ |  |
| (MHz) | ($J, K_{a}, K_{c}, v_{t}$) | \(K\) | (s$^{-1}$) |  | ($^{\prime\prime} \times ^{\prime\prime}$,$^{\circ}$) | \(K\) | (km s$^{-1}$) |  |
|  |  |  | CH$_{3}$CHO$^{b}$ |  |  |  |  |  |
| 232980.5688 | 5$_{2,3,2}$ – 4$_{1,3,2}$ | 23.03 | 1.34 10$^{-5}$ | 22 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234469.2610 | 3$_{3,1,1}$ – 3$_{2,2,1}$ | 25.84 | 2.08 10$^{-5}$ | 14 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234241.5647 | 3$_{3,0,2}$ – 3$_{2,1,2}$ | 25.94 | 2.08 10$^{-5}$ | 14 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 247432.9970 | 6$_{2,5,1}$ – 5$_{1,4,2}$ | 28.46 | 2.48 10$^{-5}$ | 26 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 234437.9503 | 4$_{3,2,1}$ – 4$_{2,3,1}$ | 29.53 | 2.92 10$^{-5}$ | 18 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234198.3312 | 4$_{3,1,2}$ – 4$_{2,2,2}$ | 29.64 | 2.91 10$^{-5}$ | 18 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234396.7456 | 5$_{3,3,1}$ – 5$_{2,4,1}$ | 34.16 | 3.30 10$^{-5}$ | 22 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234091.1815 | 5$_{3,2,2}$ – 5$_{2,3,2}$ | 34.26 | 3.29 10$^{-5}$ | 22 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234385.7553 | 6$_{3,4,1}$ – 6$_{2,5,1}$ | 39.71 | 3.40 10$^{-5}$ | 26 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 233845.3823 | 6$_{3,3,2}$ – 6$_{2,4,2}$ | 39.81 | 3.38 10$^{-5}$ | 26 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234486.2127 | 7$_{3,5,1}$ – 7$_{2,6,1}$ | 46.19 | 3.26 10$^{-5}$ | 30 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234144.5136 | 7$_{3,4,0}$ – 7$_{2,5,0}$ | 46.29 | 3.80 10$^{-5}$ | 30 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 233341.7003 | 7$_{3,4,2}$ – 7$_{2,5,2}$ | 46.29 | 3.22 10$^{-5}$ | 30 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 233124.9632 | 8$_{3,5,0}$ – 8$_{2,6,0}$ | 53.69 | 3.88 10$^{-5}$ | 34 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 247142.155 | 14$_{0,14,0}$ – 13$_{1,13,0}$ | 95.68 | 6.64 10$^{-5}$ | 58 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 247341.3322 | 14$_{0,14,2}$ – 13$_{1,13,1}$ | 95.76 | 6.63 10$^{-5}$ | 58 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 246330.7304 | 15$_{3,13,0}$ – 15$_{2,14,0}$ | 131.49 | 4.89 10$^{-5}$ | 62 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 234401.4565 | 18$_{2,17,1}$ – 18$_{1,18,1}$ | 166.47 | 2.71 10$^{-5}$ | 74 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 245939.644 | 19$_{2,18,0}$ – 19$_{1,19,0}$ | 183.86 | 3.04 10$^{-5}$ | 78 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 233048.5159 | 12$_{2,11,4}$ – 11$_{2,10,4}$ | 285.13 | 4.15 10$^{-5}$ | 50 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
|  |  |  | NH$_2$CHO$^{c}$ |  |  |  |  |  |
| 247390.719 | 12$_{0,12}$ – 11$_{0,11}$ | 78.12 | 1.10 10$^{-3}$ | 25 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 260189.0898 | 12$_{2,10}$ – 11$_{2,9}$ | 92.35 | 1.25 10$^{-3}$ | 25 | 0.44 $\times$ 0.37, -83 | 0.1071 | 0.14 |  |
| 233896.577 | 11$_{3,9}$ – 10$_{3,8}$ | 94.11 | 8.62 10$^{-4}$ | 23 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
| 234315.498 | 11$_{3,8}$ – 10$_{3,7}$ | 94.16 | 8.67 10$^{-4}$ | 23 | 0.38 $\times$ 0.34, 70 | 0.115 | 0.63 |  |
|  |  |  | CH$_{3}$O$^{13}$CHO$^{d}$ |  |  |  |  |  |
| 246787.916 | 23$_{1,23,1}$ – 22$_{1,22,1}$ | 144.64 | 2.31 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 246788.142 | 23$_{0,23,1}$ – 22$_{0,22,1}$ | 144.64 | 2.31 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 246788.838 | 23$_{1,23,0}$ – 22$_{1,22,0}$ | 144.62 | 2.31 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 246789.063 | 23$_{0,23,0}$ – 22$_{0,22,0}$ | 144.62 | 2.31 10$^{-4}$ | 94 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
|  |  |  | C$_2$H$_5$CN |  |  |  |  |  |
| 246268.7369 | 27$_{2,25}$–26$_{2,24}$ | 169.80 | 1.26 10$^{-3}$ | 55 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 246421.9174 | 28$_{2,27}$–26$_{2,26}$ | 177.26 | 1.26 10$^{-3}$ | 57 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 246548.6987 | 27$_{3,24}$-26$_{3,23}$ | 174.065 | 1.25 10$^{-3}$ | 55 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
|  |  |  | C$_2$H$_3$CN |  |  |  |  |  |
| 247087.0333 | 26$_{3,24}$–25$_{3,23}$ | 179.49 | 3.33 10$^{-3}$ | 159 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 247171.5135 | 25$_{6,20}$–26$_{5,21}$ | 225.85 | 3.17 10$^{-5}$ | 153 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |
| 247181.6118 | 25$_{6,19}$–26$_{5,22}$ | 225.85 | 3.17 10$^{-5}$ | 153 | 0.46 $\times$ 0.39, -80 | 0.0373 | 1.19 |  |

Table notes:\
\
\
\

![](FIGURES/Figure_CH3O13CHO.eps)

[^1]: <http://faust-alma.riken.jp>

[^2]: <https://casa.nrao.edu/>

[^3]: <https://faust-imaging.readthedocs.io/en/latest/>

[^4]: <http://cassis.irap.omp.eu>

[^5]: <http://www.vamdc.org/>

[^6]: <http://www.iram.fr/IRAMFR/GILDAS>

</paper>

Write the methods card for this paper.