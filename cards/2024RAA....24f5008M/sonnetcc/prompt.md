# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024RAA....24f5008M\sonnetcc\reply.txt

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
 "bibcode": "2024RAA....24f5008M",
 "title": "Study of Complex Nitrogen and Oxygen-bearing Molecules toward the High-mass Protostar IRAS 18089─1732",
 "year": 2024,
 "journal": "Research in Astronomy and Astrophysics",
 "first_author": "Manna, Arijit",
 "n_authors": 4,
 "arxiv_id": "2404.02857",
 "doi": "10.1088/1674-4527/ad3b3c",
 "alma_projects_linked_by_archive": [
  "2016.2.00005.S"
 ]
}
```

Paper text:
<paper>
# Study of Complex Nitrogen and Oxygen-bearing Molecules toward the High-mass Protostar IRAS 18089–1732

# Introduction

The study of complex organic molecules (COMs) from massive stars ($M$ $>$ 8 $M_{\odot}$) is important for understanding the chemical complexity in the interstellar medium (ISM) (cite: van98; her09). High-mass stars generate a significant amount of heavy atomic elements, produce large amounts of UV radiation, and implement turbulent energy into the ISM (cite: zap06). High-mass protostars are located in a rich cluster environment, and it is challenging to understand the physical and chemical formation processes (cite: de05). High-mass protostars are highly luminous ($\ge$10$^{3}$ L$_{\odot}$), and these sources are deeply embedded in massive envelopes that contain a high gas temperature ($\ge$100 K) and gas density above 10$^{6}$ cm$^{-3}$ (cite: li21). The study of the physical phenomena of high-mass protostellar disks is a major concern in high-mass star-forming regions. Over the past few years, indirect evidence for the existence of massive disks has accumulated, but there is still no clear proof of massive disks. Additionally, there are several methods for directly studying massive disks. Infrared and millimeter-wavelength continuum observations discover several attractive disk candidates, but they are unable to provide kinematic proof of potential accretion disks owing to a lack of velocity information (cite: sh00; ch04). On the other hand, class II methanol () and water () maser emission found kinematic signatures from the massive disk candidates, but since maser emission is extremely selective and demands specific conditions, such studies do not permit more statistical analysis of massive disk properties (cite: tor96; pes04). The most likely method to find and investigate disks in high-mass star formations is to detect thermal molecular line emissions, which are predicted to be sensitive to the gas properties and kinematics of the disks. Therefore, spectral line surveys in the millimeter and sub-millimeter wavelengths are crucial for understanding molecular gas properties, such as column density and excitation temperature. The best method is to search the rotational emission lines of acetonitrile () and methyl acetylene () because both molecules are known as gas thermometers for interstellar gas in massive protostars, hot molecular cores, and hot corinos (cite: and18). The prebiotic chemistry of high- and low-mass protostellar candidates may be the same, and a detailed analysis of the chemical evolution of high- and low-mass protostellar sources is not only important for astrochemistry but also crucial for understanding the process of star formation. Over the past decade, a variety of COMs have been discovered in protostellar cores on the scale of a few thousand astronomical units (cite: sak13). Two different scenarios were identified: (1) prebiotic chemistry in hot corinos, which is characterized by the richness of saturated COMs (cite: caz03; her09; cas12), and (2) warm carbon chain chemistry, which is characterized by the richness of unsaturated hydrocarbons (cite: sak08). Studying the chemical evolution of protostellar sources requires the study of isolated sources that are unaffected by nearby protostellar feedback. Isolated protostellar sources are excellent laboratories for theories of both chemical evolution and star formation (cite: ev15).

![](fig1.pdf)

Most chemical models of protostellar sources and hot molecular cores utilize grain surface chemistry to produce different types of complex organic compounds (cite: ti97; gar13; man24). The hydrogenation of solid oxygen (O), carbon (C), nitrogen (N), and carbon monoxide (CO) in the cold ($\leq$20 K) prestellar phase produces and other hydrogenated species such as , , and (cite: ti82). Ultraviolet radiation photodissociates these surface ices, and when the cloud core heats up during the protostellar phase, the fragments become mobile. Consequently, complex molecules are formed during the subsequent recombination of the photofragments and evaporate when the grain temperature increases above the ice sublimation temperature of $\geq$100 K (cite: gar06; gar08; man24). For example, , , and are formed by UV processing of ice (cite: ob09). Finally, the hot-core gas phase chemistry between evaporated molecules may cause second-generation species to become more complex (cite: mil91; cha92). One of the most significant impacts of an equatorial rather than a spherical structure is that UV light may more easily exit from the central source and illuminate the surface layers of the surrounding disk or toroid, as well as the larger-scale envelope (cite: bru09; bru10; iso13) (Figure [2](#fig:dia)). This can result in ice-producing COMs that are faster than . Another effect of UV radiation is enhanced photodissociation of gaseous and CO. Consequently, more atomic N and C are easily accessible for grain surface chemistry, which might result in an increased abundance of species such as HNCO and (cite: gar13).

IRAS 18089–1732 (hereafter IRAS 18089) is a well-known high-mass protostar that contains an ultra-compact (UC) Hii region (cite: li21). That source is located at a distance of 2.34 kpc from the Earth (cite: xu11). The luminosity and gaseous mass of IRAS 18089 are 1.3$\times$10$^{4}$ $L_{\odot}$ and 1000 $M_{\odot}$, which is estimated from the single-dish millimeter wavelength continuum emission (cite: sri02; beu02a). Earlier, the emission lines of , SO, SO$_{2}$, H$_{2}$S, and many other COMs were detected towards the IRAS 18089, but no column densities or abundances were reported (cite: beu04; iso13). Earlier estimated excitation temperature of ($\sim$ 350 K) towards IRAS 18089 indicated that the source deeply embedded the hot core (cite: beu04). The molecular outflow of SiO (J = 5–4) is also evident towards the IRAS 18089, which was detected using the Submillimeter Array (SMA) (cite: beu04). Additionally, the Goldreich-Kylafis effect was observed for the CO (J = 3–2) emission line, which revealed a linear polarization fraction of up to 8% (cite: beu10). The H$_{2}$O and CH$_{3}$OH maser emissions were also detected towards the IRAS 18089 (cite: beu02b). Recently, (cite: qi22) made a spectral line survey of the rotational emission lines of ethyl cyanide (), methyl formate (), and methanol () towards the 146 high-mass star-forming regions using the ATOMS survey data (cite: li20). (cite: qi22) mentioned the detection of only two and six transition lines of and towards IRAS 18089 among which one transition line of and two transition lines of are blended with other molecules (see supplementary data of (cite: qi22)). (cite: qi22) also does not discuss the abundance and proper gas phase and grain surface chemistry of those molecules towards IRAS 18089. This indicates that another detailed molecular spectral line study is needed to understand the abundance and prebiotic chemistry of different COMs towards IRAS 18089.

![](fig2.pdf)

In this paper, we present the detection of rotational emission lines of , , , and towards the IRAS 18089. The chemical diagram of those molecules is created using the molecular modelling software `Avogadro` (cite: han12) is shown in Figure [1](#fig:proto). Previously, the emission lines of , , , and was detected towards hot molecular cores G10.47+0.03 (cite: gor20; mon21; man23; mon23), G31.41+0.31 (cite: min23), Orion KL (cite: beu05a), Sgr B2 (N) (cite: bel13), and low-mass protostar IRAS 16293-2422 (cite: jo16; cal18). The paper is organized in the following manner. The observations and data reduction are presented in Section [2](#sec:obs). The result of the detection of emission lines of complex molecules is shown in Section [3](#res). The discussion and conclusion of the detection of complex molecules are shown in Section [4](#dis) and [5](#con).

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Observation date | Integration time | Frequency range | Spectral resolution | Sensitivity (10 km s$^{-1}$) | Field of view (FOV) |  |  |  |  |  |  |
| (yyyy-mm-dd) | \(s\) | (GHz) | (kHz) | (mJy beam$^{-1}$) | ($^{\prime\prime}$) |  |  |  |  |  |  |
| 2017-09-18 | 5624.64 | 127.49–128.48 | 488.28 | 5.91 | 74.23 |  |  |  |  |  |  |
| – | – | 129.75–130.75 | 488.28 | 5.37 | – |  |  |  |  |  |  |
| – | – | 139.09–140.09 | 488.28 | 5.15 | – |  |  |  |  |  |  |
| – | – | 140.45–141.45 | 488.28 | 5.01 | – |  |  |  |  |  |  |

# Observations and data reductions

We used the cycle 4 archival data of IRAS 18089, observed using the 7-m Atacama Compact Array (ACA) of the Atacama Large Millimeter/Submillimeter Array (ALMA) (ID: 2016.2.00005.S. PI: Rivilla, Victor). The observations were performed in Band 4 (frequency range 127.49 GHz – 141.45 GHz). The observed phase centre of IRAS 18089 was ($\alpha,\delta$)$_{\rm J2000}$ = 18:11:51.400, –17:31:28.00. The observation was carried out on September 18, 2017, using eight antennas. The observations were made with spectral ranges of 127.49–128.48 GHz, 129.75–130.75 GHz, 139.09–140.09 GHz, and 140.45–141.45 GHz, with a corresponding spectral resolution of 488 kHz. During the observation of IRAS 18089, the flux calibrator and bandpass calibrator were J1924–2914, and the phase calibrator was taken as J1833–210B. The observation summary is shown in Table [\[tab:data\]](#tab:data).

We used the Common Astronomy Software Application (CASA 5.4.1) with the data reduction automated pipeline for data reduction and spectral imaging of IRAS 18089 (cite: mc07). For flux calibration of IRAS 18089, we used the Perley-Butler 2017 flux calibrator model for each baseline to scale the continuum flux density of the flux calibrator using the CASA task `SETJY` with 5% accuracy (cite: per17). Using the CASA pipeline tasks `hifa bandpassflag` and `hifa flagdata`, we create the flux and bandpass calibration after flagging the defective channels and antenna data. After the initial data reduction, we used the CASA task `MSTRANSFORM` with all available rest frequencies to separate the target data of IRAS 18089. We created the continuum emission maps of IRAS 18089 for line-free channels using the CASA task `TCLEAN` with `HOGBOM` deconvolver. After the production of the continuum images, we used the task `UVCONTSUB` in the UV plane of separated calibrated data of IRAS 18089 for the continuum subtraction. To create the spectral images of IRAS 18089, we used the CASA task `TCLEAN` with `SPECMODE = CUBE` parameter and Briggs weighting robust value of 0.5. Both the continuum map and spectral cube were corrected for the primary beam using the CASA `IMPBCOR` task.

# Result

## Dust continuum emission

The 2.1-mm dust continuum image of IRAS 18089 is shown in Figure [3](#fig:continuum). We employ the CASA `IMFIT` task to estimate parameters of the central core, such as integrated flux density, peak flux density, corresponding position angle, and RMS noise level. The estimated peak flux density and integrated flux density of the source are 274.9$\pm$6.5 mJy beam$^{-1}$ and 346.1$\pm$14 mJy, respectively, with a RMS noise of 26.63 mJy beam$^{-1}$. The deconvolved source size is 5.14$''\times$3.59$''$ at a position angle of 89.8$^{\circ}$. The synthesised beam size of the continuum image is 12.78$^{\prime\prime}$$\times$7.20$^{\prime\prime}$. Thus, the continuum core is not resolved in the IRAS 18089 region.

![](fig3.pdf)

### Estimation of hydrogen (H$_{2}$) column density

For optically thin dust continuum emission, the peak flux density ($S_\nu$) can be expressed as\
$S_\nu = B_\nu(T_d)\tau_\nu\Omega_{beam}$ (cite: gor20)                                                (1)\
\
where $B_\nu(T_d)$ presents the Planck function at dust temperature $T_d$ (cite: whi92), $\tau_\nu$ indicates the optical depth, and $\Omega_{beam} = (\pi/4 \ln 2)\times \theta_{major} \times \theta_{minor}$ indicates the solid angle of the synthesized beam. The equation of optical depth in terms of the mass density of dust can be written as,\
$\tau_\nu =\rho_d\kappa_\nu L$ (cite: gor20)                                                              (2)\
\
where $\rho_d$ presents the mass density of dust, $\kappa_{\nu}$ is the mass absorption coefficient, and $L$ defines the path length. The mass density of the dust can be expressed in terms of the dust-to-gas mass ratio ($Z$),\
$\rho_d = Z\mu_H\rho_{H_2}=Z\mu_HN_{H_2}2m_H/L$    (cite: gor20)                       (3)\
\
where $\mu_H$ defines the mean atomic mass per hydrogen, $\rho_{H_2}$ is the hydrogen mass density, $m_H$ presents the mass of hydrogen, and $N_{H_2}$ is the column density of molecular hydrogen. We take the dust temperature $T_d$ = 30 K (cite: san21), $\mu_H = 1.41$, and $Z = 0.01$ (cite: cox00). The estimated peak flux density of the dust continuum of IRAS 18089 at frequency 140.955 GHz is 274.9$\pm$6.5 mJy beam$^{-1}$. From equations 1, 2, and 3, the column density of molecular hydrogen can be expressed as,\
$N_{H_2} = \frac{S_\nu /\Omega}{2\kappa_\nu B_\nu(T_d)Z\mu_H m_H}$    (cite: gor20)                                         (4)\
\
For estimation of the mass absorption coefficient ($\kappa_{\nu}$), we adopt the formula $\kappa_\nu = 0.90(\nu/230~\textrm{GHz})^{\beta}\ \textrm{cm}^{2}\ \textrm{g}^{-1}$ (cite: moto19), where $k_{230} = 0.90$ cm$^{2}$ g$^{-1}$ indicates the emissivity of the dust grains at a gas density of $\rm{10^{6}\ cm^{-3}}$, which is covered by a thin ice mantle at 230 GHz. The dust spectral index ($\beta$) of $\sim$1.6 towards IRAS 18089 is adopted from (cite: san21). Using the mass absorption coefficient formula, the estimated value of $\kappa_{\nu}$ is 0.411. Using equation 4, we estimate the column density of the molecular hydrogen ($N_{H_{2}}$) towards the IRAS 18089 to be (8.01$\pm$0.4)$\times$10$^{23}$ cm$^{-2}$. The earlier estimated column density of molecular towards the IRAS 18089 at wavelength 1.2 mm using the SMA is 9.5$\times$10$^{23}$ cm$^{-2}$ (cite: beu05b), which is nearly similar to our derived column density of ((8.01$\pm$0.4)$\times$10$^{23}$ cm$^{-2}$) using the ACA at wavelength 2.1 mm.

![](fig4a.pdf)

![](fig4b.pdf)

![image](fig5a.pdf)\

![image](fig5b.pdf) ![image](fig5c.pdf) ![image](fig5d.pdf)

## Spectral line analysis of IRAS 18089

We extracted the molecular spectrum of the high-mass protostar IRAS 18089 for a 20.2$^{\prime\prime}$ diameter circular region centering at ($\alpha,\delta$)$_{\rm J2000}$ = 18:11:51.400, –17:31:28.00. The synthesised beam sizes of the spectral images of IRAS 18089 at frequency ranges of 127.49–128.48 GHz, 129.75–130.75 GHz, 139.09–140.09 GHz, and 140.45–141.45 GHz are 12.82$^{\prime\prime}\times$6.40$^{\prime\prime}$, 12.90$^{\prime\prime}\times$6.32$^{\prime\prime}$, 12.66$^{\prime\prime}\times$6.02$^{\prime\prime}$, and 12.18$^{\prime\prime}\times$6.09$^{\prime\prime}$ respectively. The systemic velocity ($V_{LSR}$) of the IRAS 18089 is 33.8 km s$^{-1}$ (cite: beu05b). For identification of the emission line of COMs in the spectra, we use local thermodynamic equilibrium (LTE) model spectra with the Cologne Database for Molecular Spectroscopy (CDMS) molecular database (cite: mu05). For LTE analysis, we use the LTE-RADEX module in CASSIS (cite: vas15). The LTE assumption is valid in this case as the gas density of the warm inner region of the target is 1.3$\times$10$^{7}$ cm$^{-3}$ (cite: san21). The identification of the different types of COMs is discussed below.

### Ethyl cyanide ()

We detected a total of four rotational emission lines of the complex N-bearing molecule towards the IRAS 18089 using the LTE-modelled spectra. The upper-state energies ($E_{u}$) of the detected emission lines of vary between 47.23 K and 57.48 K. A Gaussian fit to the observed spectra of was performed to estimate the proper FWHM in km s$^{-1}$ and integrated intensity ($\rm{\int T_{mb}dV}$) in K km s$^{-1}$. The resultant LTE and Gaussian fitting spectral lines of are shown in Figure [4](#fig:coms), and the corresponding spectral parameters are listed in Table [\[tab:MOLECULAR DATA1\]](#tab:MOLECULAR DATA1). We also confirmed that the detected emission lines of are non-blended, and all detected emission lines of exhibit above 5$\sigma$ significance. The best-fit column density of is (1.13$\pm$0.4)$\times$10$^{14}$ cm$^{-2}$ with an excitation temperature of 200$\pm$54 K, which is obtained using the LTE modeling. The fractional abundance of towards the IRAS 18089 with respect to is (1.40$\pm$0.5)$\times$10$^{-10}$.

### Methyl formate ()

We identified a total of sixteen rotational emission lines of towards the IRAS 18089 using the LTE model with more than 5$\sigma$ significance level. The resultant LTE and Gaussian-fitted spectral profiles of are shown in Figure [4](#fig:coms), and the spectral line parameters of are presented in Table [\[tab:MOLECULAR DATA1\]](#tab:MOLECULAR DATA1). We observed the V$_{t}$ = 0 and V$_{t}$ = 1 states in the transitions of the . The V$_{t}$ = 0 and V$_{t}$ = 1 states indicate the ground and first torsionally excited states of . We find that the upper state energies ($E_{u}$) of the detected emission lines of (V$_{t}$ = 0) vary between 40.71 K and 114.60 K. Similarly, the upper state energies ($E_{u}$) of the (V$_{t}$ = 1) vary between 223.32 K and 235.0 K. We also observe the torsional substates A and E in the transitions of the due to the internal rotation of the methyl () group. During the spectral fitting using the LTE model, we observed that the J = 17(6,11)–17(5,12)A transition line of (V$_{t}$ = 0) is not fitted well because that emission line is blended with . In the Table [\[tab:MOLECULAR DATA1\]](#tab:MOLECULAR DATA1), the transitions of are presented corresponding to V$_{t}$ = 0 and V$_{t}$ = 1 states. Using the LTE model, the best-fit column density of the V$_{t}$ = 0 is (1.5$\pm$0.3)$\times$10$^{15}$ cm$^{-2}$ and V$_{t}$ = 1 is (7.1$\pm$0.5)$\times$10$^{14}$ cm$^{-2}$ with excitation temperatures of 200$\pm$48 K and 196$\pm$74 K. The column density of varies between the V$_{t}$ = 0 and V$_{t}$ = 1 torsional excited states because the first torsional excited state (V$_{t}$ = 1) of is located at about 132 cm$^{-1}$ above the ground state (V$_{t}$ = 0), where 1 cm$^{-1}$ = 1.438 K (cite: tu12). The estimated abundances of with respect to towards the IRAS 18089 are (1.90$\pm$0.9)$\times$10$^{-9}$ (for V$_{t}$ = 0) and (8.90$\pm$0.8)$\times$10$^{-10}$ (for V$_{t}$ = 1).

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Observed frequency$^{\dagger}$ | Transition$^{\dagger}$ | $E_{u}$$^{\dagger}$ | $A_{ij}$$^{\dagger}$ | FWHM$^{*}$ | $\rm{\int T_{mb}dV}$$^{*}$ | Column density | Excitation temperature | Remark$^{\bullet}$ |  |  |  |  |  |  |  |
|  | (GHz) |  | \(K\) | (s$^{-1}$) | (km s$^{-1}$) | (K km s$^{-1}$) | (cm$^{-2}$) | \(K\) |  |  |  |  |  |  |  |  |
| C$_{2}$H$_{5}$CN | 127.520 | 14(2,12)–13(2,11) | 50.02 | 1.69$\times$10$^{-4}$ | 5.52$\pm$0.24 | 0.587 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 127.618 | 14(1,13)–13(1,12) | 47.23 | 1.72$\times$10$^{-4}$ | 5.16$\pm$0.28 | 0.563 | (1.13$\pm$0.4)$\times$10$^{14}$ cm$^{-2}$ | 200$\pm$54 K | Non blended |  |  |  |  |  |  |  |
| 2-7 | 129.795 | 15(1,15)–14(1,14) | 51.09 | 1.82$\times$10$^{-4}$ | 4.82$\pm$0.64 | 0.255 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 139.335 | 16(0,16)–15(0,15) | 57.48 | 2.26$\times$10$^{-4}$ | 5.16$\pm$0.22 | 0.621 |  |  | Non blended |  |  |  |  |  |  |  |
| CH$_{3}$OCHO, $v_{t}$ = 0 | 130.010 | 11(2,10)–10(2,9)E | 40.71 | 3.12$\times$10$^{-5}$ | 3.36$\pm$0.35 | 0.284 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 130.016 | 11(2,10)–10(2,9)A | 40.70 | 3.12$\times$10$^{-5}$ | 3.56$\pm$0.42 | 0.293 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 139.565 | 11(2,10)–10(1,9)E | 40.71 | 3.82$\times$10$^{-6}$ | 3.10$\pm$0.36 | 0.063 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 139.569 | 11(2,10)–10(1,9)A | 40.70 | 3.80$\times$10$^{-6}$ | 3.23$\pm$0.28 | 0.081 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 141.037 | 12(2,11)–11(2,10)E | 47.48 | 4.01$\times$10$^{-5}$ | 3.72$\pm$0.29 | 0.784 | (1.5$\pm$0.3)$\times$10$^{15}$ cm$^{-2}$ | 200$\pm$48 K | Non blended |  |  |  |  |  |  |  |
| 2-7 | 141.044 | 12(2,11)–11(2,10)A | 47.47 | 4.01$\times$10$^{-5}$ | 4.22$\pm$0.89 | 0.875 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 141.244 | 11(3,8)–10(3,7)E | 47.77 | 3.87$\times$10$^{-5}$ | 3.90$\pm$0.31 | 0.995 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 141.260 | 11(3,8)–10(3,7)A | 47.75 | 3.87$\times$10$^{-5}$ | 4.01$\pm$0.35 | 0.846 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 141.350 | 17(6,11)–17(5,12)A | 114.59 | 4.09$\times$10$^{-6}$ | 5.86$\pm$1.09 | 0.199 |  |  | Blended with CH$_{3}$OCH$_{3}$ |  |  |  |  |  |  |  |
| 2-7 | 141.354 | 17(6,11)–17(5,12)E | 114.60 | 3.98$\times$10$^{-6}$ | 3.37$\pm$0.50 | 0.054 |  |  | Non blended |  |  |  |  |  |  |  |
| CH$_{3}$OCHO, $v_{t}$ = 1 | 127.836 | 10(2,8)–9(2,7)A | 223.96 | 2.95$\times$10$^{-5}$ | 4.59$\pm$0.78 | 0.102 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 128.273 | 10(2,8)–9(2,7)E | 223.32 | 2.99$\times$10$^{-5}$ | 3.96$\pm$0.69 | 0.076 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 139.381 | 11(3,8)–10(3,7)A | 233.19 | 3.70$\times$10$^{-5}$ | 4.63$\pm$0.86 | 0.133 | (7.1$\pm$0.5)$\times$10$^{14}$ cm$^{-2}$ | 196$\pm$74 K | Non blended |  |  |  |  |  |  |  |
| 2-7 | 139.635 | 11(3,8)–10(3,7)E | 232.67 | 3.72$\times$10$^{-5}$ | 4.36$\pm$0.44 | 0.124 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 140.020 | 12(2,11)–11(2,10)A | 235.00 | 3.92$\times$10$^{-5}$ | 4.05$\pm$0.23 | 0.144 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 140.622 | 11(2,9)–10(2,5)E | 230.07 | 3.98$\times$10$^{-5}$ | 4.81$\pm$0.73 | 0.253 |  |  | Non blended |  |  |  |  |  |  |  |
| , $v$7=1 | 127.680 | J = 14–13, $l$ = 1$e$ | 366.80 | 1.61$\times$10$^{-4}$ | 7.22$\pm$0.30 | 1.258 | (6.02$\pm$0.5)$\times$10$^{13}$ cm$^{-2}$ | 160$\pm$25 K | Non blended |  |  |  |  |  |  |  |
| 2-7 | 127.863 | J = 14–13, $l$ = 1$f$ | 366.86 | 1.62$\times$10$^{-4}$ | 6.98$\pm$0.22 | 1.072 |  |  | Non blended |  |  |  |  |  |  |  |
| , $v$7=2 | 128.169 | J = 14–13, $l$ = 0 | 687.82 | 1.63$\times$10$^{-4}$ | 3.61$\pm$0.53 | 0.112 | (2.50$\pm$0.3)$\times$10$^{13}$ cm$^{-2}$ | 180$\pm$20 K | Non blended |  |  |  |  |  |  |  |
| 2-7 | 128.175 | J = 14–13, $l$ = 2$e$ | 691.09 | 1.60$\times$10$^{-4}$ | 3.89$\pm$0.82 | 0.233 |  |  | Non blended |  |  |  |  |  |  |  |
| 2-7 | 128.182 | J = 14–13, $l$ = 2$f$ | 691.10 | 1.60$\times$10$^{-4}$ | 3.96$\pm$0.68 | 0.349 |  |  | Non blended |  |  |  |  |  |  |  |
|  | 128.102 | J = 6(2,4)–5(2,3), F = 6–5 | 33.38 | 1.28$\times$10$^{-4}$ | 5.20$\pm$0.86 | 0.429 | (5.01$\pm$0.2)$\times$10$^{13}$ cm$^{-2}$ | 180$\pm$62 K | Non blended |  |  |  |  |  |  |  |

\
${\dagger}$–Frequency, transitions, $E_{u}$, A$_{ij}$ are obtained from the LTE modelling.\
${*}$ – FWHM and $\rm{\int T_{mb}dV}$ are an estimate from the Gaussian fitting over the molecular lines.\
${\bullet}$–Blended and non-blended effects in the observed spectral lines are verified by the LTE modelling and online molecular line list database Splatalogue.\

### Cyanoacetylene ()

We detected two vibrationally excited states of ($v$7 = 1 and $v$7 = 2) towards the IRAS 18089. Using the LTE-modelled spectra, we identified two rotational emission lines of $v$7 = 1 state and three rotational emission lines of $v$7 = 2 states of . The detected vibrationally excited emission lines exhibit the higher upper-state energies of $E_{up}$/k $\sim$ 366.80–366.86 K (for $v$7 = 1) and $\sim$ 687.82–691.10 K (for $v$7 = 2). The higher vibrational states of ($v$7 = 1 and $v$7 = 2) with higher upper state energies have the ability to trace the inner hot gas near the central star. The resultant detected spectral lines of ($v$7 = 1 and $v$7 = 2) are shown in Figure [4](#fig:coms), and the spectral line parameters of ($v$7 = 1 and $v$7 = 2) are presented in Table [\[tab:MOLECULAR DATA1\]](#tab:MOLECULAR DATA1). Using the LTE model, the best-fit column density of the with $v$7 = 1 and $v$7 = 2 excited states are (6.02$\pm$0.5)$\times$10$^{13}$ cm$^{-2}$ and (2.50$\pm$0.3)$\times$10$^{13}$ cm$^{-2}$ respectively, with excitation temperatures of 160$\pm$25 K and 180$\pm$20 K. The estimated fractional abundances of towards the IRAS 18089 are (7.5$\pm$0.7)$\times$10$^{-11}$ (for $v$7 = 1) and (3.1$\pm$0.4)$\times$10$^{-11}$ (for $v$7 = 2).

### Formamide()

We have detected a single transition line of towards IRAS 18089 using the LTE-modelled spectra. We detected the J = 6(2,4)–5(2,3), F = 6–5 transition line of . We do not observe any other transition lines of in the entire data. The upper-state energy ($E_{u}$) of the detected emission line of is 33.38 K. To estimate the proper FWHM in km s$^{-1}$ and integrated intensity ($\rm{\int T_{mb}dV}$) in K km s$^{-1}$ of the emission line of , we fitted the Gaussian model over the observed spectra of . The resultant LTE and Gaussian fitting spectral lines of are shown in Figure [4](#fig:coms), and the corresponding spectral parameters are listed in Table [\[tab:MOLECULAR DATA1\]](#tab:MOLECULAR DATA1). We observed that the detected emission lines of are non-blended and exhibit above 5$\sigma$ significance. Using the LTE spectral modelling, the best-fit column density of , based on the single transition line, is (5.01$\pm$0.2)$\times$10$^{13}$ cm$^{-2}$ with an excitation temperature of 180$\pm$62 K. The fractional abundance of with respect to towards the IRAS 18089 is (6.25$\pm$0.8)$\times$10$^{-11}$.

|  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Observed frequency | Transition | Emitting region | Physical scale$^{\dagger}$ |  |  |  |  |  |  |  |  |  |  |  |  |
|  | (GHz) |  | ($^{\prime\prime}$) | (pc) |  |  |  |  |  |  |  |  |  |  |  |  |
| C$_{2}$H$_{5}$CN | 127.520 | 14(2,12)–13(2,11) | 12.09$\pm$0.61 | 29.43 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 127.618 | 14(1,13)–13(1,12) | 12.10$\pm$0.65 | 29.45 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 129.795 | 15(1,15)–14(1,14) | 12.12$\pm$0.59 | 29.50 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 139.335 | 16(0,16)–15(0,15) | 12.11$\pm$0.60 | 29.47 |  |  |  |  |  |  |  |  |  |  |  |  |
| CH$_{3}$OCHO, $v_{t}$ = 0 | 130.010 | 11(2,10)–10(2,9)E | 12.08$\pm$0.58 | 29.40 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 130.016 | 11(2,10)–10(2,9)A | 12.07$\pm$0.57 | 29.38 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 139.565 | 11(2,10)–10(1,9)E | 12.09$\pm$0.59 | 29.43 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 139.569 | 11(2,10)–10(1,9)A | 12.11$\pm$0.61 | 29.47 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 141.037 | 12(2,11)–11(2,10)E | 12.14$\pm$0.58 | 29.55 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 141.044 | 12(2,11)–11(2,10)A | 12.09$\pm$0.55 | 29.43 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 141.244 | 11(3,8)–10(3,7)E | 12.15$\pm$0.59 | 29.57 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 141.260 | 11(3,8)–10(3,7)A | 12.11$\pm$0.58 | 29.47 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 141.354 | 17(6,11)–17(5,12)E | 12.08$\pm$0.61 | 29.40 |  |  |  |  |  |  |  |  |  |  |  |  |
| CH$_{3}$OCHO, $v_{t}$ = 1 | 127.836 | 10(2,8)–9(2,7)A | 12.11$\pm$0.58 | 29.48 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 128.276 | 10(2,8)–9(2,7)E | 12.10$\pm$0.61 | 29.45 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 139.381 | 11(3,8)–10(3,7)A | 12.14$\pm$0.59 | 29.55 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 139.635 | 11(3,8)–10(3,7)E | 12.07$\pm$0.57 | 29.38 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 140.020 | 12(2,11)–11(2,10)A | 12.11$\pm$0.60 | 29.47 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 140.622 | 11(2,9)–10(2,5)E | 12.09$\pm$0.56 | 29.43 |  |  |  |  |  |  |  |  |  |  |  |  |
| , $v$7=1 | 127.680 | J = 14–13, $l$ = 1$e$ | 12.11$\pm$0.62 | 29.47 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 127.863 | J = 14–13, $l$ = 1$f$ | 12.12$\pm$0.63 | 29.50 |  |  |  |  |  |  |  |  |  |  |  |  |
| , $v$7=2 | 128.169 | J = 14–13, $l$ = 0 | 12.10$\pm$0.58 | 29.45 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 128.175 | J = 14–13, $l$ = 2$e$ | 12.11$\pm$0.60 | 29.47 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 128.182 | J = 14–13, $l$ = 2$f$ | 12.10$\pm$0.59 | 29.45 |  |  |  |  |  |  |  |  |  |  |  |  |
|  | 128.102 | J = 6(2,4)–5(2,3), F = 6–5 | 12.13$\pm$0.62 | 29.52 |  |  |  |  |  |  |  |  |  |  |  |  |

\
$\dagger$–During the estimation of the physical scale of the emitting regions of different molecules, we used the cosmological parameters using Plank with Hubble constant $H_{0}$ = 0.6731, $\Omega_{M}$ = 0.315, and $\Omega_{L}$ = 0.685 (cite: ag20).

## Spatial distribution of detected COMs

We create the integrated intensity maps of the non-blended transitions of , (V$_{t}$ = 0 and V$_{t}$ = 1), ($v$7 = 1 and $v$7 = 2), and using the CASA task `IMMOMENTS` towards the IRAS 18089. The integrated intensity maps of detected COMs towards the IRAS 18089 are created by integrating the spectral data cubes over carefully determined channel ranges where COMs are detected (see Figure [5](#fig:emissionmap)). We notice that the integrated intensity maps of different COMs have a peak at the position of the continuum. From the integrated emission maps it is clear that the emission lines of different COMs may have arised from the extended envelope of the IRAS 18089. We also estimated the emitting regions of COMs towards the IRAS 18089 by fitting the 2D Gaussian over the integrated intensity maps using the CASA `IMFIT` task. The deconvolved beam size of the emitting region of COMs is estimated by using the following equation,\
$\theta_{S}=\sqrt{\theta^2_{50}-\theta^2_{beam}}$                          (5)\
\
where $\theta_{50} = 2\sqrt{A/\pi}$ denotes the diameter of the circle with area, $A$ is the area that encloses 50% of the peak intensity, and $\theta_{beam}$ is the half-power width of the synthesised beam of the integrated emission maps (cite: riv17). The value of $\theta_{50}$ is estimated using the task `IMFIT`. The estimated emitting regions of COMs are shown in Table [\[tab:emitting region\]](#tab:emitting region). The emitting regions of vary between 12.09$^{\prime\prime}$ (29.43 pc)–12.12$^{\prime\prime}$ (29.50 pc). The emitting regions of with V$_{t}$ = 0 and V$_{t}$ = 1 states vary between 12.07$^{\prime\prime}$ (29.38 pc)–12.15$^{\prime\prime}$ (29.57 pc) and 12.07$^{\prime\prime}$ (29.38 pc)–12.14$^{\prime\prime}$ (29.55 pc). The emitting regions of with vibrationally excited states $v$7 = 1 and $v$7 = 2 vary between 12.11$^{\prime\prime}$ (29.47 pc)–12.12$^{\prime\prime}$ (29.50 pc) and 12.10$^{\prime\prime}$ (29.45 pc)–12.11$^{\prime\prime}$ (29.47 pc). Similarly, the emitting region of is 12.13$^{\prime\prime}$ (29.52 pc). A smaller emitting region of COMs in comparison to the synthesised beam size implies that the emitting area of COMs is spatially unresolved in the current data set. Further high-resolution observations of these lines are required, possibly using an ALMA 12-m array, to examine the distribution and chemical morphology of COMs in the IRAS 18089 region.

# Discussion

## Possible formation mechanism of COMs

### Ethyl cyanide ():

The N-bearing molecule, , is formed on the grain surface of the high-mass protostars and hot molecular cores (cite: meh04; gar13; gar17; gar22). (cite: gar13) showed that the subsequential hydrogenation of in the free-fall collapse phase can form the vinyl cyanide () ( + 2H $\rightarrow$ ). The subsequential hydrogenation of the form in the grain surface of the hot molecular cores and high-mass protostars (cite: gar13), through barrierless and exothermic radical-radical reactions (cite: sin21). This particular chemical reaction is demonstrated to be the most efficient way for the formation of towards the Sgr B2, G10.47+0.03, G31.41+0.31, and other molecular cores (cite: bel09; man23; min23). This reaction may be most efficient towards IRAS 18089 because acts as a possible precursor of , and we detected the emission lines of from this source, which we already discussed in this paper.

### Methyl formate ():

In this article, we present the first detection of with V$_{t}$ = 0 and V$_{t}$ = 1 states towards the IRAS 18089 using the ACA. In the hot molecular cores and high-mass protostars, molecule can efficiently be formed by the reaction of and HCO radicals on the surface of dust grains ( + HCO $\rightarrow$ ) (cite: gar08). Earlier, (cite: man22) showed that the reactions between radical and radical HCO produce towards the hot molecular core IRAS 18566+0408. (cite: gar13) showed the chemical reaction between and is mobile between 30–40 K, and this chemical reaction is the most efficient pathway to the formation of towards the hot molecular cores and high-mass protostars. According to the chemical modelling of (cite: gar13), the gas phase mainly comes from the ice phase of massive protostars. Earlier, (cite: gor21) reported that the UV photodissociation of leads to the formation of , , and at around 40 K temperature, and these molecules create the COMs, like , . At temperature $T\sim$ 40 K in the gas phase, the reaction of protonated and creates $^{+}$ (cite: gor21). The is created in the hot molecular cores and massive protostars via the electron recombination of $^{+}$ ($^{+}$+e$^{-}\longrightarrow$ +H) (cite: bon19; gor21). Earlier, (cite: bal15) proposed an efficient gas phase reaction of in a cold environment where behaves as a possible precursor of . Therefore, it is evident that can be produced through both grain surface and gas phase reactions in the hot molecular cores and high-mass protostars. Note that (cite: beu05b) detected with transition J = 19(1,18)–18(2,17)AA towards IRAS 18089 using SMA. However, such detection of a single transition line of one complex molecule could not be considered as conclusive evidence of the presence of the molecule in high-mass protostars.

### Cyanoacetylene ():

In the ISM, acetylene () is one of the known compounds that is formed in the grain surfaces (cite: ch09). After the evaporation of in the grains, there are two possible scenarios.\
1. When the UV field is strong, like in photodissociation regions (PDR), then photo-dissociates into the ethynyl radical () ( + $h\nu$$\rightarrow$ + H) (cite: ch93; me05).\
2. In the weak UV field regime (without PDR) in the presence of cyano radical (CN), reacts with the CN to create ( + CN $\rightarrow$ + H) (cite: fu97; me05; ch09). Recently, (cite: tan22) claimed that the is created in the high-mass protostars and UC Hii regions when immediately reacts with the CN. The molecule is associated with highly dense, warm, and shielded gas in the star-forming regions or high-mass protostars (cite: tan22).

In the star-forming regions, with the presence of UV radiation, the molecule is easily destroyed by reacting with C+ ions (cite: rod98; me05). After the destruction, converts into or if is photo-dissociated (cite: ch93). Similarly, converts into or if reacts with C+ (cite: bo85). The possible destruction reactions are:\
\
+ $h\nu$ $\rightarrow$ + CN              (1)\
\
+ $h\nu$ $\rightarrow$ + H                 (2)\
\
+ C$^{+}$ $\rightarrow$ $^{+}$ + CN           (3)\
\
+ C$^{+}$ $\rightarrow$ $^{+}$ + H              (4)\
\
The rates of the above reaction are reported in (cite: ch93), and (cite: tan22) showed that these destruction pathways are the most efficient towards the high-mass protostars and UC Hii regions.

### Formamide ()

In the ISM, the formation pathways of are still a topic of debate in both gas phase and solid state ice mantle formation routes (cite: gar08). Previously, (cite: gar13) showed that is created in the gas phase barrierless reaction between and ( + $\rightarrow$ + H). Earlier, (cite: gar13) and (cite: suz18) showed that reaction is the most efficient for the formation of towards hot molecular cores. After that, (cite: gor20) claimed that reaction is responsible for the production of towards G10.47+0.03.

## Comparision between the observed and modelled abundance of COMs

Here we compare the estimated fractional abundances of , , , and towards the IRAS 18089 with the existing three-phase warm-up chemical model abundances of (cite: suz18). For chemical modelling, (cite: suz18) used the gas-grain chemical kinetics code NAUTILUS in the environment of hot molecular cores and massive protostars. During the chemical modelling of complex molecules, (cite: suz18) assumed an isothermal collapse phase after a static warm-up phase. In the first phase, the gas density increases from 3$\times$10$^{3}$ cm$^{-3}$ to 2$\times$10$^{7}$ cm$^{-3}$ and dust temperature decreases from 16 K to 8 K under the free-fall collapse (cite: suz18). In the second phase, known as the warm-up phase, the dust temperature increases from 8 to 400 K, and the gas density remains fixed at 2$\times$10$^{7}$ cm$^{-3}$. For the chemical modelling, (cite: suz18) used the following reactions in the grain surfaces to produce the , , and .\
\
+ 2H $\rightarrow$                     (5)\
\
+ HCO $\rightarrow$                      (6)\
\
+ CN $\rightarrow$ + H                           (7)\
\
+ $\rightarrow$ + H                  (8)\
\
We explain reactions 5, 6, 7, and 8 in Section [4.1](#formation). The three-phase warm-up chemical modelling of (cite: suz18) is appropriate for explaining the chemical abundance and evolution of COMs towards the IRAS 18089 because the gas density of IRAS 18089 is 1.3$\times$10$^{7}$ cm$^{-3}$ (cite: san21) and the gas temperature is above 100 K (cite: beu041). After the chemical modelling, (cite: suz18) determined the modelled abundance of , , , and to be 6.3$\times$10$^{-10}$, 4.9$\times$10$^{-9}$, 1.1$\times$10$^{-11}$, and 4.0$\times$10$^{-11}$ respectively using the fast warm-up model with the help of reactions 5, 6, 7, and 8 on the grain surfaces and gas phases of hot molecular cores and massive prostars. Our estimated abundances of , (V$_{t}$ = 0), , and is shown in Section [3.2](#coms). We find that our estimated abundances of , , , and are nearly similar to the chemical modelling abundances of (cite: suz18). This result indicates that reactions 5, 6, 7, and 8 may be responsible for the production of , , , and towards the IRAS 18089.

# Conclusion

In this article, we present the identification of the rotational emission lines of , (V$_{t}$ = 0 and V$_{t}$ = 1), ($v$7 = 1 and $v$7 = 2), and towards the IRAS 18089. The estimated abundance of towards the IRAS 18089 is (1.40$\pm$0.5)$\times$10$^{-10}$. The estimated abundance of with respect to is (1.90$\pm$0.9)$\times$10$^{-9}$ and (8.90$\pm$0.8)$\times$10$^{-10}$ for V$_{t}$ = 0 and V$_{t}$ = 1, respectively. The abundance of towards the IRAS 18089 is (7.5$\pm$0.7)$\times$10$^{-11}$ (for $v$7 = 1) and (3.1$\pm$0.4)$\times$10$^{-11}$ (for $v$7 = 2). Similarly, the abundance of towards IRAS 18089 is (6.25$\pm$0.8)$\times$10$^{-11}$. We created the integrated emission maps of detected COMs, and we observed that the detected emission lines of different COMs arise from the extended envelope of the protostar. We also compare the estimated abundances of , , , and with the existing three-phase warm-up modelling abundances of those molecules. After the comparisons, we notice that the observed and modelled abundances are nearly similar. So, the N-bearing molecules and are most probably created via the subsequential hydrogenation of the and the reactions between and CN on the grain surface of IRAS 18089. The O-bearing molecule is probably created via the reactions between radical and radical HCO on the grain surface of IRAS 18089. Similarly, the O- and N-bearing molecule is most probably formed between the reactions of and in the gas phase of IRAS 18089. The prebiotic chemistry of , , , and towards the IRAS 18089 suggests that both gas phase and grain surface chemistry are efficient for the production of other COMs in that protostar, including those molecules that are chemically connected with those detected molecules. The detections of both N- and O-bearing molecules towards IRAS 18089 indicate that IRAS 18089 is a reservoir of several other COMs. A spectral line survey is needed using the ALMA 12-m arrays to understand the prebiotic chemistry in this high-mass protostar, which will be carried out in our follow-up study.

# acknowledgements

We thank the anonymous referee for the helpful comments that improved the manuscript. A.M. acknowledges the Swami Vivekananda Merit-cum-Means Scholarship (SVMCM) for financial support for this research. This paper makes use of the following ALMA data: ADS /JAO.ALMA#2016.2.00005.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ.

# Conflicts of interest

The authors declare no conflict of interest.

natexlab

(ref: ag20) Aghanim, N., Akrami, Y., Ashdown, M., et al. 2020, A&A, 641, 67

(ref: and18) Andron, I., Gratier, P., Majumdar, L., et al. 2018, MNRAS, 481, 5651

(ref: bel09) Belloche, A. Garrod, R. T., Müller, H. S. P., Menten, K. M., Comito, C., Schilke, P., 2009, A&A, 499, 215

(ref: bel13) Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., Comito, C., 2013, A&A, 559, A47

(ref: bal15) Balucani N., Ceccarelli C., Taquet V. 2015, MNRAS, 449, L16

(ref: beu02a) Beuther, H., Schilke, P., Menten, K. M., et al. 2002a, [ApJ](https://iopscience.iop.org/article/10.1086/338334/meta), 566, 945

(ref: beu02b) Beuther, H., Walsh, A., Schilke, P., et al. 2002b, [A&A](https://doi.org/10.1051/0004-6361:20020710), 390, 289

(ref: beu04) Beuther, H., Zhang, Q., Hunter, T. R., et al. 2004a, [ApJL](https://iopscience.iop.org/article/10.1086/422500/meta), 616, L19

(ref: beu041) Beuther H., Hunter T. R., Zhang, Q., et al., 2004b, [ApJL](https://iopscience.iop.org/article/10.1086/383570), 616, L23

(ref: beu10) Beuther, H., Vlemmings, W. H. T., Rao, R., & van der Tak, F. F. S. 2010, [ApJL](https://iopscience.iop.org/article/10.1088/2041-8205/724/1/L113/meta), 724, L113

(ref: beu05a) Beuther, H., Zhang, Q., Greenhill, L. J., et al. 2005, ApJ, 632, 355

(ref: beu05b) Beuther, H., Zhang, Q., Sridharan, T. K., & Chen, Y. 2005, [ApJ](https://iopscience.iop.org/article/10.1086/431277/meta), 628, 800

(ref: bo85) Bohme, D. K., & Raksit, A. B. 1985, MNRAS, 213, 717

(ref: bon19) Bonfand, M., Belloche, A., Garrod, R.T., et al. 2019, A&A, 628, A27

(ref: bru09) Bruderer, S., Benz, A. O., Doty, S. D., van Dishoeck, E. F., & Bourke, T. L. 2009, ApJ, 700, 872

(ref: bru10) Bruderer, S., Benz, A. O., Stäuber, P., & Doty, S. D. 2010, ApJ, 720, 1432

(ref: cal18) Calcutt, H., Jørgensen, J. K., Müller, H. S. P. et al. 2018, A&A, 616, A90

(ref: ch09) Chapman, J. F., Millar, T. J., Wardle, M., Burton, M. G., & Walsh, A. J. 2009, MNRAS, 394, 221

(ref: ch93) Cherchneff, I., Glassgold, A. E., & Mamon, G. A. 1993, ApJ, 410, 188

(ref: ch04) Chini, R., Hoffmeister, V., Kimeswenger, S., et al., 2004, Nature, 429, 155

(ref: cox00) Cox, A. N., & Pilachowski, C. A. 2000, Physics Today, 53, 77

(ref: cha92) Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJ, 399, L71

(ref: cas12) Caselli, P., & Ceccarelli, C. 2012, A&ARv, 20, 56

(ref: caz03) Cazaux, S., Tielens, A. G. G. M., Ceccarelli, C., et al. 2003, ApJL, 593, L151

(ref: de05) de Wit W. J., Testi L., Palla F., Zinnecker H., 2005, A&A, 437, 247

(ref: ev15) Evans, N. J., II, Di Francesco, J., Lee, J.-E., et al. 2015, ApJ, 814, 22

(ref: fu97) Fukuzawa, K., & Osamura, Y. 1997, ApJ, 489, 113

(ref: gor21) Gorai, P., Das, A., Shimonishi, T., et al. 2021, ApJ, 907, 108

(ref: gor20) Gorai, P., Bhat, B., et al. 2020, ApJ 895 86

(ref: gar17) Garrod, R. T., Belloche, A., Müller, H. S. P., and Menten, K. M., 2017, [A&A]( https://doi.org/10.1051/0004-6361/201630254 ), 601, A48

(ref: gar06) Garrod, R. T., & Herbst, E. 2006, A&A, 457, 927

(ref: gar13) Garrod R. T. 2013, [ApJS](https://doi.org/10.1088/0004-637X/765/1/60), 765, 60

(ref: gar08) Garrod, R. T., Weaver, S. L. W., & Herbst, E. 2008, ApJ, 682, 283

(ref: gar22) Garrod, R. T., Jin, M., Matis, K. A., Jones, D., Willis, E. R., Herbst, E., 2022, [ApJS](https://doi.org/10.3847/1538-4365/ac3131), 259, 1

(ref: her09) Herbst, E., & van Dishoeck, E.F. 2009, ARA&A, 47, 427

(ref: han12) Hanwell, M.D., Curtis, D.E., Lonie, D.C. et al. 2012, J Cheminform, 4, 17

(ref: iso13) Isokoski, K., Bottinelli, S., & van Dishoeck, E. F. 2013, [A&A](https://doi.org/10.1051/0004-6361/201220959), 554, A100

(ref: jo16) Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595, A117

(ref: li20) Liu, T., Evans, N. J., Kim, K. T., et al. 2020, MNRAS, 496, 2790

(ref: li21) Liu H.-L., Liu T., Evans N. J., Wang K., Garay G., Qin S.-L., Li S., et al., 2021, MNRAS, 505, 2801

(ref: man22) Manna, A., & Pal, S. 2022, Astrophys Space Sci, 367, 94

(ref: man23) Manna, A., & Pal, S. 2023, Astrophys Space Sci, 368, 44

(ref: man24) Manna, A., Pal, S., 2024, [ACS Earth and Space Chemistry](https://doi.org/10.1016/j.newast.2024.102199), <https://doi.org/10.1021/acsearthspacechem.3c00245>

(ref: mon21) Mondal, S. K., Gorai, P., Sil, M., et al. 2021, ApJ, 922, 194

(ref: mon23) Mondal, S. K., Iqbal, W., Gorai, P., et al. 2023, A&A, 669, A71

(ref: me05) Meier, D. S., & Turner, J. L. 2005, ApJ, 618, 259

(ref: moto19) Motogi, K., Hirota, T., Machida, M. N., et al. 2019, [ApJL](https://iopscience.iop.org/article/10.3847/2041-8213/ab212f/meta), 877, L25

(ref: mc07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., Golap, K. 2007. CASA Architecture and Applications. Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: mu05) Müller, H. S. P., SchlM$\ddot{o}$der, F., Stutzki, J. Winnewisser, G., 2005, [Journal of Molecular Structure](https://ui.adsabs.harvard.edu/abs/2005JMoSt.742..215M/abstract), 742, 215

(ref: meh04) Mehringer, D. M., Pearson, J. C., Keene, J., & Phillips, T. G. 2004, [ApJ](https://doi.org/10.1086/386357), 608, 306

(ref: mil91) Millar, T. J., Herbst, E., & Charnley, S. B. 1991, ApJ, 369, 147

(ref: min23) Mininni, C., Beltr$\acute{a}$n, M. T., Colzi, L., et al. 2023, A&A, 677, A15

(ref: ob09) Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Linnartz, H. 2009, A&A, 504, 891

(ref: per17) Perley, R. A., Butler, B. J. 2017, [ApJs](https://iopscience.iop.org/article/10.3847/1538-4365/aa6df9/meta), 230, 1538

(ref: pes04) Pestalozzi, M. R., Elitzur, M., Conway, J. E., & Booth, R. S. 2004, ApJ, 603, L113

(ref: qi22) Qin, S.-L., Liu, T., Liu, X., et al. 2022, MNRAS, 511, 3463

(ref: rod98) Rodriguez-Franco, A., Martin-Pintado, J., & Fuente, A. 1998, A&A, 329, 1097

(ref: riv17) Rivilla V. M., Beltrán M. T., Cesaroni R., et al. 2017, A&A, 598, A59

(ref: san21) Sanhueza, P., Girart, J. M., Padovani, M., et al., [ApJL](https://iopscience.iop.org/article/10.3847/2041-8213/ac081c/meta), 2021, 1, L10

(ref: sri02) Sridharan, T. K., Beuther, H., Schilke, P., Menten, K. M., & Wyrowski, F. 2002, [ApJ](https://iopscience.iop.org/article/10.1086/338332/meta), 566, 931

(ref: sin21) Singh, K. K. Tandon, P., Misra, A., Shivani, Yadav, M., Ahmad, A. 2021, [International Journal of Astrobiology](https://doi.org/10.1017/S147355042000035X), 20, 62

(ref: suz18) Suzuki, T., Majumdar, L., Ohishi, M., 2018, ApJ, 863, 51

(ref: sh00) Shepherd, D. S., Yu, K. C., Bally, J., & Testi, L. 2000, ApJ, 535, 833

(ref: sak13) Sakai, N., & Yamamoto, S. 2013, ChRv, 113, 8981

(ref: sak08) Sakai, N., Sakai, T., Hirota, T., et al. 2008, ApJ, 672, 371

(ref: tan22) Taniguchi, K., et al. 2022, APJ, 931, 99

(ref: tu12) Tudorie M., Ilyushin V., vander Auwera J. et al. 2012, JCP, 137, 064304

(ref: tor96) Torrelles, J. M., Gomez, J. F., Rodriguez, L. F., Curiel, S., Ho, P. T. P., & Garay, G. 1996, ApJ, 457, L107

(ref: ti97) Tielens, A. G. G. M., & Charnley, S. B. 1997, Origins of Life and Evolution of the Biosphere, 27, 23

(ref: ti82) Tielens, A. G. G. M., & Hagen, W. 1982, A&A, 114, 245

(ref: van98) van Dishoeck E. F. & Blake G. A., 1998, Annu Rev Astron Astrophys, 36, 317

(ref: vas15) Vastel, C., Bottinelli, S., Caux, E., Glorian, J. -M., Boiziot, M., 2015, [Proceedings of the Annual meeting of the French Society of Astronomy and Astrophysics](https://ui.adsabs.harvard.edu/abs/2015sf2a.conf..313V/abstract), 313-316

(ref: whi92) Whittet, D. C. B. 1992, [Journal of the British Astronomical Association](https://ui.adsabs.harvard.edu/abs/1992JBAA..102..230W/abstract), 102, 230

(ref: xu11) Xu, Y., Moscadelli, L., Reid, M. J., et al. 2011, [ApJ](https://iopscience.iop.org/article/10.1088/0004-637X/733/1/25/meta), 733, 25

(ref: zap06) Zapata, L. A., Rodrı́guez, L. F., Ho, P. T. P., et al. 2006, AJ, 131, 939

</paper>

Write the methods card for this paper.