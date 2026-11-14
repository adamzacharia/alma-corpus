# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...681A.117P\sonnetcc\reply.txt

Use the Write tool for that file. Quote the paper verbatim in every evidence quote (the quotes are checked mechanically against the paper text). Copying LaTeX as it appears is fine: the checker normalises markup, whitespace and line breaks on both sides, so keep the numbers inside the quote rather than quoting around them. Every stated fact needs at least one quote; leave a field "not stated" rather than filling it without one. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

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
 "bibcode": "2024A&A...681A.117P",
 "title": "The CO-to-H<SUB>2</SUB> conversion factor of molecular outflows. Rovibrational CO emission in NGC 3256-S resolved by JWST/NIRSpec",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Pereira-Santaella, M.",
 "n_authors": 5,
 "arxiv_id": "2309.06486",
 "doi": "10.1051/0004-6361/202347942",
 "alma_projects_linked_by_archive": [
  "2015.1.00412.S",
  "2015.1.00714.S",
  "2018.1.00223.S"
 ]
}
```

Paper text:
<paper>
# The CO-to-H$_2$ conversion factor of molecular outflows. Rovibrational CO emission in NGC 3256-S resolved by *JWST*/NIRSpec

# Introduction

Feedback from active galactic nuclei (AGN) has been invoked to explain key properties of galaxies like the observed stellar mass function or the quenching of the star-formation (SF) in quiescent galaxies (e.g., (cite: Somerville2015)). This SF quenching can be caused by the removal of cold gas from the host galaxy by massive outflows. These outflows seem to be dominated by the cold molecular phase and have mass outflow rates, $\dot{M}_{\rm out}$, from a few $M_{\rm \odot}$ yr$^{-1}$ to $>$100 $M_{\rm \odot}$ yr$^{-1}$ and mass loading factors, $\dot{M}_{\rm out}$ /star-formation rate (SFR), which can exceed 1 in extreme cases like ultra-luminous infrared galaxies (ULIRGs; (cite: Harrison2018; Veilleux2020)).

A commonly used tracer of cold molecular outflows are rotational CO transitions in the mm and sub-mm ranges (e.g., (cite: Combes2013; Cicone2014; GarciaBurillo2015; Pereira2018; Lutz2020; GarciaBernete2021; Lamperti2022; RamosAlmeida2022; AlonsoHerrero2018; AlonsoHerrero2019; AlonsoHerrero2023)). To transform the observed CO luminosities ($L_{\rm CO}$), into molecular masses ($M_{\rm mol}$), and the latter into outflow rates, it is necessary to apply a CO-to-H$_2$ conversion factor, $\alpha_{\rm CO}=M_{\rm mol}\slash L_{\rm CO}$, which in most cases is not constrained by the observations and a fixed value is assumed. A $\sim$1 dex wide range of $\alpha_{\rm CO}$ between 0.3 and 2.0 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ has been suggested for outflows from observations of multiple $[$C i$]$ and rotational CO transitions in few objects (e.g., (cite: Dasyra2016; Cicone2018; Saito2022; Ueda2022)). According to these works, possible explanations for the reduced $\alpha_{\rm CO}$ in outflows are: non-virialized molecular clouds; optically thin rotational CO emission; and/or CO being destroyed becoming C i. Here, we present an alternative method to estimate the $\alpha_{\rm CO}$ factor using the fundamental rovibrational CO $v$=1–0 4.67 $\upmu$m band that now can be observed by the NIRSpec instrument (cite: Jakobsen2022; Boker2022) on board the James Webb Space Telescope (*JWST*).

The 4.67 $\upmu$m rovibrational CO band has been previously observed in extragalactic objects from space with *Spitzer* and *AKARI* at low spectral resolution ($R$\<150) which was not enough to spectrally resolve the individual transitions of the band (cite: Spoon2004; Baba2018; Baba2022). It has also been observed from the ground at high spectral resolution $R$$\sim$5000–10000 (to allow for the correction of the atmospheric absorption) in a few deeply obscured objects (e.g., IRAS 08572+3915, NGC 4945, and NGC 4418; (cite: Spoon2003; Geballe2006; Shirahata2013; Onishi2021; Ohyama2023)). All these works focused on detecting the CO rovibrational band in absorption toward dusty bright IR nuclei to probe the conditions of the gas close to the central source (AGN and/or compact starburst). In this work, thanks to the sensitivity and spatial resolution of *JWST*, we for the first time disentangle the rovibrational CO absorption toward the obscured AGN located in the southern nucleus of the luminous infrared (IR) merger NGC 3256 and the spatially extended CO emission around this nucleus using the integral field unit (IFU) of NIRSpec. So far, detections of the CO band in emission have been scarce and only in Galactic sources (e.g., (cite: GonzalezAlfonso2002; Najita2003; Rettig2005; Herczeg2011)). With *JWST*, detection of the CO band in emission is likely to become common in spatially resolved objects hosting bright mid-IR sources.

## NGC 3256

NGC 3256 is a nearby ($d$=40 Mpc; $z$=0.00916; 190 pc arcsec$^{-1}$) gas-rich advanced merger (projected nuclear separation $<$1 kpc) with a high IR luminosity ($L_{\rm IR}$=10$^{11.6}$ $L_\odot$) which places it in the luminous IR galaxy (LIRG) range. The southern component of NGC 3256 (NGC 3256 S) is an edge-on disk with a position angle (PA) of $\sim$90$\ensuremath{^\circ}$. It is located in front of the northern component, which is an almost face-on disk (see e.g., (cite: Sakamoto2014)).

The northern component is powered by a bright starburst with a nuclear star-formation rate (SFR) of $\sim$15 $M_\odot$ yr$^{-1}$ (cite: Lira2008). The southern component instead hosts an extremely dust-embedded nucleus with a very deep 9.7 $\upmu$m silicate absorption feature (cite: Pereira2010; DiazSantos2010). The modeling of near-IR, mid-IR, and X-ray observations of the southern nucleus suggests that it is powered by a low-luminosity ($L_{\rm 2-10\,keV}\sim10^{40}$ erg s$^{-1}$) obscured AGN (cite: Ohyama2015). However, because of the extreme dust obscuration, no high-ionization transitions neither direct X-ray emission from the AGN are detected (e.g., (cite: Lira2002; AAH2012a; Pereira2011)).

This AGN has a collimated bipolar outflow which is perpendicular to the disk. A massive outflow ($\dot{M}_{\rm out}>$50 $M_\odot$ yr$^{-1}$) has been detected in the cold molecular phase, through CO, HCN, and HCO$^+$ rotational emission (cite: Sakamoto2014; Michiyama2018), as well as in the hot molecular gas phase, through near-IR rovibrational H$_2$ transitions (cite: Emonts2014) and the ionized gas phase (cite: Leitherer2013). A bipolar radio-jet has been proposed as the launching mechanism of the outflow (cite: Sakamoto2014), although it might not be powerful enough to explain the outflow mass. Alternatively, radiation pressure and an ionized wind from the AGN could drive this outflow (cite: Emonts2014).

This paper is organized as follows: the data reduction is presented in Section [2](#s:data). In Section [3](#s:analysis), maps of the mid-IR continuum and ionized and molecular gas tracers are presented. We also extract the spectra of selected regions and fit the observed spectral features. In Section [4](#s:co_rovib_model), we present a model for the rovibrational CO band emission. Three methods to derive the $\alpha_{\rm CO}$ factor from the CO band emission are discussed in Section [5](#s:conv_factor). Finally, in Section [7](#s:summary), we summarize the main results of the paper.

+:--------------------+:----------:+:--------:+:-:+:-:+:-:+:-:+
|                     |            |          |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| Name                | $\lambda$  | Ref.     |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
|                     | ($\mu$m)   |          |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| CO $v$=1–0 band fit                         |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 1–0 O(9)      | 4.5755     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| $[$K iii$]$         | 4.6180     | 4        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| Aliphatic D$_n$-PAH | 4.645$^a$  | 5,6      |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H i 7–5             | 4.6538     | 3        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 1–1 S(10)     | 4.6558     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H i 11–6            | 4.6725     | 3        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| $^{12}$CO $v$=1–0   | 4.6742$^b$ | 1        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 0–0 S(9)      | 4.6946     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| $^{13}$CO $v$=1–0   | 4.7792$^b$ | 1        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| C$^{18}$O $v$=1–0   | 4.7882$^b$ | 1        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| Additional transitions                      |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 0–0 S(10)     | 4.4098     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 1–1 S(11)     | 4.4166     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 1–1 S(9)      | 4.9541     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H$_2$ 0–0 S(8)      | 5.0531     | 2        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+
| H i 10–6            | 5.1287     | 3        |   |   |   |   |
+---------------------+------------+----------+---+---+---+---+

: Spectral features

Table notes: List of spectral features used during the fitting of the CO $v$=1–0 band. $^{(a)}$ The D$_n$-PAH emission is modeled as a Gaussian profile with $\sigma$=0.0091 $\upmu$m(see Section [3.3.4](#ss:dpah) and Figure [8](#fig_dnpah)). $^{(b)}$ Wavelength of the P(1) transition of the rovibrational band.

# Data reduction

![image](fig_nircam_maps_panel_v4.pdf) ![image](fig_line_maps_n3256_v5.pdf)

## *JWST* NIRSpec integral field spectroscopy

We present the high spectral resolution ($R$$\sim$1900–3600) 2.87–5.27 $\upmu$m *JWST*/NIRSpec integral-field spectroscopy of NGC 3256 obtained with the grating/filter pair G395H/F290LP. These NIRSpec observations are part of the Director’s Discretionary Early Release Science (DD-ERS) Program #1328 (PI: L. Armus and A. Evans). The data were obtained with the NRSIR2RAPID readout using 18 groups and a 4-point cycling dither pattern. The field of view is 3.1$''$ $\times$ 3.1$''$, with a spaxel size of 0.1$''$.

We downloaded the uncalibrated level 1 data from the *JWST* archive[^1]. The NIRSpec IFU observations were processed using the *JWST* Calibration pipeline (version 1.9.4) together with the calibration context 1063 from the Calibration References Data System (CRDS). First, we processed the raw data for detector-level corrections using the standard Detector1 module of the pipeline. MSA leakage correction exposures (i.e., leakal files) are also corrected during this stage. Then, we subtracted a residual bias level by masking the slits in the ramp-fitted products (i.e., count rate files). We built a bad-pixel mask based on the leakal exposures and updated the data quality extensions of both source and leakal observations. The masked pixels are interpolated based on the neighbour spaxels (3$\times$3 box) when possible.

Then, we calibrated count rate files using the Spec2 module. This module corrects flat-fielding and applies flux calibration and world coordinate system corrections. We used the Spec3 module to build the two 3D spectral sub-cubes (NIRSpec detectors 1 and 2) from the fully calibrated Spec2 products. We used the drizzle weighing and spaxel size of 0.1$''$ in the cube build algorithm.

![](fig_line_maps_v_n3256_v3.pdf)

## NIRCam imaging

NIRCam imaging was also available as part of the DD-ERS Program #1328. We downloaded the fully reduced and calibrated F150W (1.50 $\upmu$m), F200W (1.99 $\upmu$m), and F335M (3.36 $\upmu$m) images from the *JWST* archive. We combined these three filters to produce a reference color image of the system showing the near-IR stellar morphology (F150W and F200W filters) and the more extended PAH3.3 $\upmu$m emission included in the F335M filter (Figure [1](#fig_nircam)).

## Ancillary ALMA data

We retrieved archival ALMA observations of the $^{12}$CO rotational lines $J$=1–0 (115.27 GHz) and $J$=2–1 (230.54 GHz) from programs 2018.1.00223.S (PI: K. Sakamoto) and 2015.1.00714.S (PI: K. Sliwa), respectively. We combined data from compact and extended 12-m array configurations to improve the coverage of $uv$-plane. We also retrieved observations of the CO isotopologues $^{13}$CO $J$=2–1 (220.40 GHz) and C$^{18}$O $J$=2–1 (219.56 GHz), both from program 2015.1.00412.S (PI: N. Harada).

The data were processed using the ALMA reduction software CASA (v6.4.1; (cite: McMullin2007)) following (cite: Pereira2021). The $^{12}$CO cubes were smoothed to a common beam with a FWHM of 0.39$''$$\times$0.37$''$, which is comparable to the *JWST*/NIRSpec resolution ($\sim$0.2$''$), using the CASA task IMSMOOTH. The beam FWHM of the $^{13}$CO and C$^{18}$O cubes is 0.85$''$$\times$0.81$''$.

We calculated the zeroth moment maps of all the CO transitions following the method described in (cite: SanchezGarcia2022). The top right panel of Figure [1](#fig_nircam) shows the $^{12}$CO(2–1) zeroth moment map around the two nuclei of NGC 3256.

The absolute flux accuracy for Band 3 ($^{12}$CO $J$=1–0) and Band 6 ($J$=2–1 transitions) is 10% and 20%, respectively (ALMA Technical Handbook).

# Analysis and results

In this paper, we focus on the rich 4.52–4.87 $\upmu$m spectral range observed by *JWST*/NIRSpec where the rovibrational bands of $^{12}$CO (4.67 $\upmu$m), $^{13}$CO (4.78 $\upmu$m), and C$^{18}$O (4.79 $\upmu$m) are located. In addition to the CO bands, this spectral range also contains pure rotational and rovibrational H$_2$ transitions as well as hydrogen recombination lines and ionized gas tracers. Table [1](#tbl_feature_list) shows the full list of spectral features used in this work.

To analyze the NIRSpec data cubes, we first produced spectral maps to extract the spatial information at the native NIRSpec resolution ($\sim$0.2$''$ at $\sim$4.6 $\upmu$m; Sections [3.1](#ss:spectral_maps) and [3.2](#ss:spectral_co_maps)). Then, we analyzed the spectra from selected regions of interest using larger apertures (0.5$''$ diameter; $\sim$ 100 pc) to increase the signal-to-noise ratio (SNR; Section [3.3](#ss:sp_regions)).

![](fig_co_class_v4.pdf)

![](fig_co_class_map_v3.pdf)

## Mid-IR continuum, ionized, and molecular gas maps

We first produced spectral maps of various tracers in the spectral range around the $^{12}$CO band (4.59–4.75 $\upmu$m) to trace the morphology and kinematics of the ionized and molecular gas phases and the mid-IR continuum (Figures [1](#fig_nircam) and [2](#fig_vel)). To do so, we extracted the spectrum of each spaxel and fitted a model including the features listed in Table [1](#tbl_feature_list). For reference, Figure [3](#fig_co_class_sp) shows the annotated spectra of three regions of NGC 3256 (see Section [3.3](#ss:sp_regions) for details).

We fitted the local continuum level in the 4.59–4.75 $\upmu$m range using a linear function. For the spectral features we used Gaussian profiles. We tied the velocity and dispersion for groups of lines tracing the same phase of the gas: warm/hot molecular gas (H$_2$ lines), and ionized gas (H i and $[$K iii$]$4.62 $\upmu$m). The relative velocity of the D$_n$-PAH band (Section [3.3.4](#ss:dpah)) is tied to the H$_2$ lines. The wavelength and width of the individual R- and P-branch CO transitions were also tied to a common line of sight velocity and velocity dispersion. In addition, the intensity of the H i lines were tied according to the expected case B ratios at 10 000 K (7–5/11–6=6.43; (cite: Storey1995)). These two transitions are very close in wavelength (4.65 and 4.67 $\upmu$m), so the differential extinction is minimal and its effect on their ratio negligible. The intensity of the $[$K iii$]$4.62 $\upmu$m was tied to that of the H i 7–5 line since the former is fainter and blended with the CO R(5) transition. We estimated an average $[$K iii$]$4.62 $\upmu$m/H i 7–5 4.65 $\upmu$m ratio of 0.104 in this object from the average ratio measured in regions with no CO R(5) detected. To create these maps, we did not include in the model either the $^{13}$CO or the C$^{18}$O $v$=1–0 bands since they are not blended with any of these H i or H$_2$ transitions.

This spectral range contains numerous overlapping spectral features, so to obtain an initial guess for the velocity and width of the lines in each spaxel, we used those derived from the H$_2$ S(8) 5.05 $\upmu$m and H i 10–6 5.13 $\upmu$m lines, which are isolated in a less crowded spectral range.

From these fits, we obtained the intensity maps of the 4.6 $\upmu$m continuum, the ionized gas traced by H i 7–5 4.65 $\upmu$m line, the molecular gas traced by H$_2$ 0–0 S(9) 4.69 $\upmu$m, and the CO 1–0 P(5) transition, which is not strongly blended with other spectral features (see second and third rows of Figure [1](#fig_nircam)).

### Southern rotating disk. Ionized, molecular, and continuum emissions

In addition to the compact and bright 4.6 $\upmu$m continuum and ionized gas emission from the southern nucleus (second row of Figure [1](#fig_nircam)), the southern disk is clearly seen extended along the East-West direction. The ionized gas is likely tracing star-forming regions in the disk, while the extended continuum is likely produced by hot dust heated by these star-forming regions.

The velocity field of the ionized gas traced by H i 7–5 4.65 $\upmu$m (first panel of Figure [2](#fig_vel)) is also consistent with a distorted rotating disk due to the galaxy interaction and it is compatible with previous near-IR kinematic studies of this system (cite: Piqueras2012). We note that the central $\sim$100 pc velocity field is uncertain since the H$_2$ and H i lines are heavily affected by the multi-component CO $v$=1–0 nuclear absorption (Section [3.2](#ss:spectral_co_maps)).

The hot ($T>$1000 K) molecular gas traced by H$_2$ 0–0 S(9) 4.69 $\upmu$m ($E_{\rm up}$=10261 K; (cite: Roueff2019)) shows a more complex morphology (third row of Figure [1](#fig_nircam)). Some emitting regions are detected in the disk and the hot molecular gas kinematics also shows an East-West velocity gradient compatible with a distorted rotating disk (second panel of Figure [2](#fig_vel)). However, the brightest hot molecular emission is located perpendicular to the rotating disk and it is likely related to the massive molecular outflow ((cite: Emonts2014); Section [3.1.2](#ss:molecular_outflow)).

### Molecular outflow. H$_2$ and CO emissions

The southern AGN produces a high-velocity (${\rm v}>1000$ km s$^{-1}$) bipolar collimated molecular outflow perpendicular to the rotating disk (e.g., (cite: Sakamoto2014; Emonts2014)). The hot molecular phase of this outflow has been detected using near-IR H$_2$ transitions (cite: Emonts2014). The H$_2$ 0–0 S(9) 4.69 $\upmu$m emission also traces hot molecular gas and the emission perpendicular to the disk is likely related to this outflow (see Section [3.1.1](#ss:rotating_disk)). However, we note that due to the small field of view of NIRSpec, the brightest hot H$_2$ clumps of the outflow, which also have the highest velocity dispersion ($\sigma\sim$190 km s$^{-1}$; (cite: Emonts2014; Piqueras2012)), are not covered by these observations.

The cold molecular phase of the outflow is traced by the sub-mm/mm rotational CO transitions (cite: Sakamoto2014). The top row of Figure [1](#fig_nircam) shows the morphology of the CO(2–1) 230.54 GHz transition. Although some CO(2–1) emission is detected in the southern disk, most of the emission around this nucleus is instead extended perpendicular to the disk up to $\sim$400 pc away. Thanks to the high angular resolution of the ALMA data, it is clear that this emission is not part of the spiral arms of the northern galaxy and, therefore, it is likely located above and below the southern nucleus and its origin likely connected to the molecular outflow. Consequently, we consider the emission from these regions as part of the outflow. Moreover, the outflow direction is close to the plane of the sky ($i\sim80\deg$; (cite: Sakamoto2014)), so even if the observed line of sight velocity is not particularly high (${\rm v}$\<150 km s$^{-1}$), the inclination corrected velocity can be much higher (see (cite: Sakamoto2014)).

The bottom row of Figure [1](#fig_nircam) presents the CO $v$=1–0 rovibrational emission map as traced by the P(5) transition. It is similar to the CO(2–1) 230.54 GHz emission, and it is relatively brighter in the outflow direction compared to the disk emission (see Section [3.2](#ss:spectral_co_maps)). In Figure [5](#fig_pv_co), we compare the position-velocity (PV) plot along the outflow axis for the CO(2–1) and P(5) transitions. Excluding the strong nuclear absorption affecting the P(5) transition (Section [3.2](#ss:spectral_co_maps)), the two PV plots show a similar morphology. In particular, the higher-velocity blue-shifted ($-$100–$-$200 km s$^{-1}$) outflow emission between $-$1.1$''$ and $-$0.3$''$ is detected in both transitions. Thus, based on the similar morphology and kinematics, we conclude that the rovibrational CO emission is related to the cold molecular outflow identified in the ALMA data.

![image](fig_pv_co21.pdf) ![image](fig_pv_P5.pdf)

## Origin of the rovibrational CO $v$=1–0 band

The ratio between the P- and R-branch transitions of the CO $v$=1–0 band can be used to investigate the physical conditions of the molecular gas as traced by CO.

The R(2) 4.641 $\upmu$m and P(5) 4.709 $\upmu$m transitions are not blended with other features so they are ideal to compare the P- and R-branches. We fitted a Gaussian profile to these two lines with tied velocity and velocity dispersion. We leave the peak of the Gaussian free allowing for both absorption and emission profiles. The R(2) and P(5) transitions are detected in emission and absorption in different regions. According to the emission or absorption profiles, we classify the spaxels in three groups: (a) both transitions in absorption; (b) R(2) in absorption and P(5) in emission (P-R asymmetry); and (c) both transitions in emission. The integrated spectra of these regions are shown in Figure [3](#fig_co_class_sp) and the spatial classification in Figure [4](#fig_co_class_map). From this map it is clear that (a) spaxels correspond to the nucleus where the strong 4.6 $\upmu$m continuum favors the detection of the CO $v$=1–0 band in absorption. Also, we note that the nuclear CO $v$=1–0 spectrum has two velocity components: a low-velocity colder component only detected in the low-$J$ transitions (up to $J$$\sim$6); and a blue-shifted (v=160 km s$^{-1}$) possibly outflowing component detected up to $J$=19. The (b) spaxels showing the P-R asymmetry are mostly located along the disk of the galaxy. This P-R asymmetry has been detected in Galactic star-forming regions (e.g., (cite: GonzalezAlfonso2002; GonzalezAlfonso1998)), which is consistent with the spatial location of these regions in NGC 3256.

Finally, the (c) spaxels with both P- and R-branches in emission are detected perpendicular to the disk in the molecular outflow region. The CO $v$=1–0 band can be radiatively excited by $\sim$4.7 $\upmu$m photons. Therefore, it is possible to explain this CO $v$=1–0 emission if the mid-IR radiation from the AGN is illuminating the cold molecular outflowing gas (see Figure [6](#fig_sketch)). This scenario and the method to derive the cold molecular gas properties from the CO $v$=1–0 band are further explored in Sections [4](#s:co_rovib_model) and [5](#s:conv_factor).

![](fig_rad_pump.pdf)

## Spectra from regions with CO $v$=1–0 in emission

We extracted the spectra from eight circular apertures (0.5$''$ diameter) in the outflow region where both the P- and R-branches are detected in emission (green area in Figure [4](#fig_co_class_map); see also Section [3.2](#ss:spectral_co_maps)). The location of these apertures is plotted in the bottom-right panel of Figure [1](#fig_nircam). These apertures follow the outflow axis (N1, N2, and S1) and few clumps seen in the CO $v$=1–0 map (Figure [1](#fig_nircam) bottom right panel; N3, N4, N5, S2, and S3).

Since the nuclear emission is compact and relatively bright (Figure [1](#fig_nircam)), we need to subtract its contribution to the spectrum of these apertures. We calculated this contribution at each wavelength using point-spread functions (PSFs) created with WebbPSF (v1.1.1; (cite: Perrin2014)). These PSFs were rotated and convolved with a Gaussian kernel (FWHM=0.130$''$$\times$0.077$''$) to match the orientation and FWHM of the southern nucleus of NGC 3256. Using these PSFs, we estimated the scaling factor between the emission at the aperture position and that from a fiducial aperture (0.4$''$ diameter) centered on the PSF. Then, using the fiducial aperture, we measured the NGC 3256 S nuclear emission and applied the scaling factor to subtract its contribution to the aperture spectrum.

We fitted the spectral features in the 4.52–4.87 $\upmu$m range following a procedure similar to that described in Section [3.1](#ss:spectral_maps). However, because of the higher SNR of these spectra, compared to the individual spaxel spectra, we used a more detailed model which includes additional spectral features and components. We describe the main elements of this more detailed model in Sections [3.3.1](#ss:baseline) through [3.3.5](#ss:12co_band).

### Continuum baseline

The shape of the continuum around the CO $v$=1–0 rovibrational band can be affected by absorption bands produced by various ice species (OCN$^-$ 4.62 $\upmu$m, $^{12}$CO 4.67 $\upmu$m, and $^{13}$CO 4.78 $\upmu$m; e.g., (cite: Gibb2004; McClure2023)).

To take into account these effects on the continuum shape, we defined a spline-interpolated baseline. The pivot points (4.395, 4.530, 4.586, 4.667, 4.845, and 4.980 $\upmu$m) are selected to track the continuum level avoiding known emission features. This baseline reproduces well the underlying continuum and ice absorptions (e.g., Figure [7](#fig_cont_spline)) and was subtracted from the spectra before fitting the emission lines.

![](fig_cont_v1.pdf)

### Optically thin $^{13}$CO and C$^{18}$O $v$=1–0 bands

The R-branch of the $^{13}$CO and C$^{18}$O $v$=1–0 bands overlaps with the P-branch of the $^{12}$CO band (see Figure [3](#fig_co_class_sp)). Although, the $^{13}$CO and C$^{18}$O bands are weaker than the band produced by the main isotopologue $^{12}$CO, for P-branch transitions with $J>$8, the intensities of the overlapping R-branch transitions from the isotopologues are comparable or brighter than the $^{12}$CO lines. To disentangle the bands from the three species, we used Gaussian profiles to fit the P-branch and the R(0) transition of $^{13}$CO, which are not affected by $^{12}$CO band. The widths and velocities of these profiles were tied and we fitted them independently of the kinematics obtained for the $^{12}$CO band. The $^{13}$CO P(2)/R(0) ratio is consistent with the optically thin limit, $\sim$1.96 (see Section [4.1](#ss:model_p2r)), within $\pm$1 $\sigma$ for all the regions (except for S3 where the $^{13}$CO band spectral range is noisier). Therefore, it is reasonable to assume that the $^{13}$CO (and also the C$^{18}$O) emission is optically thin. Under this assumption, it is possible to determine the flux of the R-branch using the measured P-branch fluxes (Section [4.1](#ss:model_p2r)). We estimate the intensity of the C$^{18}$O band assuming that both $^{13}$CO and C$^{18}$O share the same excitation temperatures and have abundance ratio of $\sim$7.4. We derived this abundance ratio from the $^{13}$CO(2–1)/C$^{18}$O(2–1) ratio measured at the southern nucleus using a circular aperture ($r$=1$''$). This abundance ratio agrees with that obtained by (cite: Harada2018), 5.6–6.6, for the same region using a slightly larger aperture.

The model for the $^{13}$CO and C$^{18}$O band emission is also subtracted from the spectra of the eight circular apertures before fitting the $^{12}$CO band.

Under the optically thin limit, the fluxes predicted for the R-branch lines based on the P-branch observations, agree with the observed spectra for all the regions including region S3 (Figure [9](#fig_fit_model)).

### Molecular hydrogen and recombination lines

There are two H$_2$ transitions (0–0 S(9) 4.69 $\upmu$m and 1–1 S(10) 4.66 $\upmu$m) and two H I recombination lines (7–5 4.65 $\upmu$m and 11–6 4.67 $\upmu$m) that lie close to the center of the $^{12}$CO band. The fluxes of the S(9) 4.69 $\upmu$m and 7–5 4.65 $\upmu$m transitions are similar to the CO band fluxes, while the fluxes of the remaining two transitions are fainter.

To help constraining the contribution of all these lines, we make use of additional H$_2$ and H I recombination lines in the NIRSpec range (see Table [1](#tbl_feature_list)).

We determined the profile of the H$_2$ lines by fitting a Gaussian (or two Gaussians when a single Gaussian cannot reproduce the observed profile) to the 0–0 S(8) 5.05 $\upmu$m profile. For the 0–0 S(9) 4.69 $\upmu$m transition, we used this profile fixing its wavelength (velocity) and width (velocity dispersion) and allowing only the integrated flux to vary during the fit. The fainter 1–1 S(10) 4.66 $\upmu$m, is very close in wavelength to the CO R(0) and 7–5 transitions so its flux is not well constrained. Therefore, we estimated its intensity assuming an excitation temperature equal to that derived from the 1–1 S(11) 4.42 $\upmu$m and 1–1 S(9) 4.95 $\upmu$m transitions and an ortho-to-para ratio of 3.

We fixed the velocity and width of the H I lines taking the H I 10–6 5.13 $\upmu$m profile as reference. The integrated flux of the 7–5 transition is fitted while for the 11–6 transition we assume the case B ratio (see Section [3.1](#ss:spectral_maps)).

### The 4.65 $\upmu$m D$_n$-PAH profile

The aliphatic C-D stretch in deuterated PAH (D$_n$-PAH) produces a broad band at $\sim$4.65 $\upmu$m. This band has been detected in Galactic sources and is predicted by quantum chemical computations (e.g., (cite: Peeters2004DPAH; Onaka2014; Doney2016; Buragohain2020; Yang2023)). An accurate profile of this feature is not yet available due to the limited SNR and/or spectral resolution of these observations. Therefore, we determined the D$_n$-PAH profile from the observations of NGC 3256-S.

We used the spectrum from the P-R asymmetry region (middle panel of Figure [3](#fig_co_class_sp)) where the low-$J$ R-branch transitions of the CO $v$=1–0 band are detected in absorption over the 4.65 $\upmu$m D$_n$-PAH feature. We fitted a Gaussian to the continuum subtracted spectrum between 4.62 and 4.67 $\upmu$m after masking the CO absorptions and the H I 7–5 and H$_2$ 1–1 S(10) transitions (Figure [8](#fig_dnpah)). The redshift of this spectrum was determined using the H$_2$ 0–0 S(8) line as reference. The central wavelength of the best-fit Gaussian is 4.6452 $\pm$ 0.0004 $\pm$ 0.0014 $\upmu$m, where the uncertainties are statistical and due to the redshift, respectively. The width of this Gaussian profile is $\sigma$=0.0091 $\pm$ 0.0003 $\upmu$m. The D$_n$-PAH band has been detected in Galactic sources using NIRSpec observations (cite: Boersma2023). The central wavelength and width we obtained are compatible with the Galactic profile, although we note that they report a SNR of the band lower than in the spectrum analyzed here (5.25 vs. 11).

![](fig_dpah_2.pdf)

### $^{12}$CO $v$=1–0 band

After subtracting the continuum baseline (Section [3.3.1](#ss:baseline)) and the $^{13}$CO and C$^{18}$O bands (Section [3.3.2](#ss:13cothin)), we fitted the $^{12}$CO band together with the H$_2$ and H I transitions (Section [3.3.3](#ss:h2_hi_lines)) and the 4.65 $\upmu$m D$_n$-PAH band (Section [3.3.4](#ss:dpah)) considering all the constraints described before.

We first attempted the fit using a single Gaussian profile for each CO transition. Two regions (N1 and N2) show a second broader kinematic component in the residuals. For these regions, we repeated the fit using two Gaussians for the CO band. We note that the fluxes of the broad component are not well constrained for the R(2) and R(3) transitions which are close to the D$_n$-PAH band and the H I 7–5 transition. Thus, we did not attempt to disentangle the fluxes of the narrow and broad components for these regions and only considered the integrated flux of the line.

The best-fit model for each region are shown in Figure [9](#fig_fit_model). From these fits, we obtained the fluxes of the P- and R-branch transitions (Table [\[tbl_line_fluxes\]](#tbl_line_fluxes)) which we used to calculate the ratios discussed in Sections [4](#s:co_rovib_model) and [5](#s:conv_factor).

![image](fig_sp_N1.pdf) ![image](fig_sp_N2.pdf) ![image](fig_sp_N3.pdf) ![image](fig_sp_N4.pdf) ![image](fig_sp_N5.pdf) ![image](fig_sp_S1.pdf) ![image](fig_sp_S2.pdf) ![image](fig_sp_S3_v1.pdf)

+:--------------------------------------+:----------:+:----------------------:+:---------------:+:---------------:+:---------------:+:---------------:+:----------------------:+:---------------:+:---------------:+:-:+:-:+:-:+:-:+
|                                       |            |                        |                 |                 |                 |                 |                        |                 |                 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| Transition                            | Wavelength | Region                                                                                                                                                      |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| 3-10                                  |            |                        |                 |                 |                 |                 |                        |                 |                 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
|                                       |  $\upmu$m  | N1                     | N2              | N3              | N4              | N5              | S1                     | S2              | S3              |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| $^{12}$CO $v$=1–0                     |            |                        |                 |                 |                 |                 |                        |                 |                 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| $\sigma_1 \slash$(km s$^{-1}$) $^{a}$ |            | 34 $\pm$ 1             | 36 $\pm$ 1      | 55 $\pm$ 2      | 45 $\pm$ 2      | 51 $\pm$ 3      | 86 $\pm$ 3             | 67 $\pm$ 3      | 52 $\pm$ 2      |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| $\sigma_2 \slash$(km s$^{-1}$) $^{a}$ |            | 78 $\pm$ 3             | 105 $\pm$ 4     |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(9)                                  | 4.5876     | 0.80 $\pm$ 0.64        |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(8)                                  | 4.5950     | 2.68 $\pm$ 0.64        |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(7)                                  | 4.6024     | 5.98 $\pm$ 0.64        | 0.93 $\pm$ 0.28 | 0.52 $\pm$ 0.10 | 0.41 $\pm$ 0.11 | 0.00 $\pm$ 0.09 | 0.78 $\pm$ 0.14        | 0.63 $\pm$ 0.10 | 0.23 $\pm$ 0.11 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(6)                                  | 4.6100     | 9.53 $\pm$ 0.64        | 2.05 $\pm$ 0.28 | 0.54 $\pm$ 0.10 | 0.34 $\pm$ 0.11 | 0.00 $\pm$ 0.08 | 1.14 $\pm$ 0.14        | 0.76 $\pm$ 0.10 | 0.24 $\pm$ 0.11 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(5)                                  | 4.6177     | 15.1 $\pm$ 0.6         | 3.51 $\pm$ 0.28 | 1.01 $\pm$ 0.10 | 1.22 $\pm$ 0.21 | 0.50 $\pm$ 0.10 | 1.18 $\pm$ 0.14        | 0.76 $\pm$ 0.10 | 0.44 $\pm$ 0.26 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(4)                                  | 4.6254     | 19.0 $\pm$ 0.6         | 4.79 $\pm$ 0.28 | 1.11 $\pm$ 0.10 | 0.94 $\pm$ 0.11 | 0.21 $\pm$ 0.10 | 1.52 $\pm$ 0.14        | 1.16 $\pm$ 0.10 | 0.93 $\pm$ 0.15 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(3)                                  | 4.6333     | 27.7 $\pm$ 0.7         | 7.06 $\pm$ 0.28 | 1.72 $\pm$ 0.11 | 1.54 $\pm$ 0.12 | 0.68 $\pm$ 0.11 | 2.64 $\pm$ 0.17        | 1.94 $\pm$ 0.10 | 1.73 $\pm$ 0.11 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(2)                                  | 4.6412     | 36.8 $\pm$ 0.7         | 10.0 $\pm$ 0.3  | 1.80 $\pm$ 0.19 | 1.78 $\pm$ 0.20 | 0.76 $\pm$ 0.12 | 2.69 $\pm$ 0.20        | 2.64 $\pm$ 0.12 | 2.13 $\pm$ 0.12 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(1)                                  | 4.6493     | 46.6 $\pm$ 1.1         | 14.8 $\pm$ 0.4  | 2.97 $\pm$ 0.27 | 3.07 $\pm$ 0.21 | 2.04 $\pm$ 0.12 | 3.91 $\pm$ 0.31        | 3.74 $\pm$ 0.12 | 3.82 $\pm$ 0.22 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(0)                                  | 4.6575     | 52.5 $\pm$ 1.3         | 18.8 $\pm$ 0.5  | 4.77 $\pm$ 0.25 | 4.45 $\pm$ 0.26 | 3.07 $\pm$ 0.12 | 6.28 $\pm$ 0.29        | 3.86 $\pm$ 0.11 | 5.53 $\pm$ 0.23 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(1)                                  | 4.6742     | 60.7 $\pm$ 1.1         | 24.8 $\pm$ 0.6  | 6.91 $\pm$ 0.16 | 6.86 $\pm$ 0.14 | 4.91 $\pm$ 0.12 | 7.25 $\pm$ 0.18        | 5.60 $\pm$ 0.15 | 5.69 $\pm$ 0.13 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(2)                                  | 4.6826     | 85.2 $\pm$ 1.6         | 37.2 $\pm$ 0.8  | 13.0 $\pm$ 0.2  | 12.1 $\pm$ 0.2  | 9.18 $\pm$ 0.12 | 11.3 $\pm$ 0.3         | 8.92 $\pm$ 0.16 | 9.01 $\pm$ 0.16 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(3)                                  | 4.6912     | 105.6 $\pm$ 2.1        | 46.0 $\pm$ 0.9  | 16.5 $\pm$ 0.2  | 16.0 $\pm$ 0.3  | 13.4 $\pm$ 0.3  | 15.7 $\pm$ 0.5         | 13.7 $\pm$ 0.3  | 12.6 $\pm$ 0.3  |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(4)                                  | 4.6999     | 112.1 $\pm$ 2.5        | 45.4 $\pm$ 1.2  | 15.0 $\pm$ 0.2  | 16.0 $\pm$ 0.4  | 11.8 $\pm$ 0.4  | 14.3 $\pm$ 0.5         | 12.8 $\pm$ 0.2  | 11.4 $\pm$ 0.3  |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(5)                                  | 4.7088     | 105.4 $\pm$ 2.1        | 39.0 $\pm$ 0.8  | 11.0 $\pm$ 0.1  | 13.0 $\pm$ 0.1  | 9.98 $\pm$ 0.15 | 12.8 $\pm$ 0.2         | 10.3 $\pm$ 0.1  | 9.55 $\pm$ 0.12 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(6)                                  | 4.7177     | 86.3 $\pm$ 1.7         | 27.0 $\pm$ 0.6  | 6.36 $\pm$ 0.12 | 8.84 $\pm$ 0.14 | 6.31 $\pm$ 0.15 | 8.75 $\pm$ 0.18        | 7.45 $\pm$ 0.11 | 6.28 $\pm$ 0.11 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(7)                                  | 4.7267     | 62.0 $\pm$ 1.3         | 15.7 $\pm$ 0.3  | 3.40 $\pm$ 0.13 | 6.34 $\pm$ 0.12 | 3.50 $\pm$ 0.11 | 5.72 $\pm$ 0.19        | 4.77 $\pm$ 0.10 | 4.44 $\pm$ 0.11 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(8)                                  | 4.7359     | 35.8 $\pm$ 0.7         | 6.86 $\pm$ 0.27 | 1.27 $\pm$ 0.10 | 2.46 $\pm$ 0.11 | 1.35 $\pm$ 0.10 | 3.19 $\pm$ 0.19        | 2.30 $\pm$ 0.13 | 2.17 $\pm$ 0.10 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(9)                                  | 4.7451     | 17.4 $\pm$ 0.6         | 2.20 $\pm$ 0.26 | 0.35 $\pm$ 0.10 | 0.84 $\pm$ 0.17 | 0.25 $\pm$ 0.15 | 2.12 $\pm$ 0.14        | 0.66 $\pm$ 0.13 | 1.31 $\pm$ 0.10 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(10)                                 | 4.7545     | 6.32 $\pm$ 0.61        |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(11)                                 | 4.7640     | 3.73 $\pm$ 0.61        |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| $^{13}$CO $v$=1–0                     |            |                        |                 |                 |                 |                 |                        |                 |                 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| $\sigma \slash$(km s$^{-1}$) $^{a}$   |            | 39 $\pm$ 6             | 50 $\pm$ 4      | 100 $\pm$ 20    | 30 $\pm$ 5      | 45 $\pm$ 6      | 130 $\pm$ 20           | 63 $\pm$ 5      | 90 $\pm$ 15     |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| R(0)                                  | 4.7626     | 7.66 $\pm$ 0.62 $^{b}$ | 3.26 $\pm$ 0.16 | 1.31 $\pm$ 0.16 | 0.62 $\pm$ 0.08 | 0.62 $\pm$ 0.10 | 1.25 $\pm$ 0.21 $^{b}$ | 0.50 $\pm$ 0.09 | 1.63 $\pm$ 0.20 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(1)                                  | 4.7792     | 6.61 $\pm$ 0.38        | 4.07 $\pm$ 0.15 | 1.27 $\pm$ 0.15 | 0.85 $\pm$ 0.08 | 0.48 $\pm$ 0.10 | 0.75 $\pm$ 0.13        | 0.47 $\pm$ 0.06 | 1.69 $\pm$ 0.14 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(2)                                  | 4.7877     | 9.34 $\pm$ 0.42        | 5.66 $\pm$ 0.18 | 1.97 $\pm$ 0.14 | 1.32 $\pm$ 0.09 | 1.34 $\pm$ 0.13 | 0.99 $\pm$ 0.14        | 0.86 $\pm$ 0.06 | 2.06 $\pm$ 0.17 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(3)                                  | 4.7963     | 11.1 $\pm$ 0.5         | 5.49 $\pm$ 0.19 | 1.76 $\pm$ 0.13 | 1.44 $\pm$ 0.10 | 1.39 $\pm$ 0.14 | 1.61 $\pm$ 0.16        | 1.05 $\pm$ 0.07 | 1.77 $\pm$ 0.17 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(4)                                  | 4.8050     | 9.54 $\pm$ 0.43        | 3.53 $\pm$ 0.16 | 1.26 $\pm$ 0.14 | 1.13 $\pm$ 0.09 | 0.89 $\pm$ 0.11 |  $\cdots$              | 0.71 $\pm$ 0.07 | 1.26 $\pm$ 0.16 |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(5)                                  | 4.8138     | 5.04 $\pm$ 0.37        | 1.64 $\pm$ 0.14 |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              | 0.39 $\pm$ 0.06 |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(6)                                  | 4.8227     | 2.22 $\pm$ 0.35        | 0.74 $\pm$ 0.13 |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+
| P(7)                                  | 4.8317     | 1.12 $\pm$ 0.34        |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$       |  $\cdots$              |  $\cdots$       |  $\cdots$       |   |   |   |   |
+---------------------------------------+------------+------------------------+-----------------+-----------------+-----------------+-----------------+------------------------+-----------------+-----------------+---+---+---+---+

Table notes: The fluxes are in 10$^{-17}$ erg cm$^{-2}$ s$^{-1}$ units. These fluxes include both the narrow and broad velocity components for the regions where two Gaussians were used.

## ALMA rotational $^{12}$CO emission

Using the ALMA observations of NGC 3256-S (Section [2.3](#ss:data_alma)), we measured the fluxes of the CO(1–0) 115.27 GHz and CO(2–1) 230.54 GHz transitions in the selected regions (see Section [3.3](#ss:sp_regions)). We extracted the spectra of the each region from the ALMA data cubes and integrated the line profile. The fluxes are listed in Table [\[tbl_line_fluxes_rot\]](#tbl_line_fluxes_rot). We also calculated the $r_{21}$ ratio between the fluxes of the CO(2–1) and CO(1–0) transitions in K km s$^{-1}$ units.

+:---------------+:----------:+:------:+:------:+:------:+:------:+:------:+:------:+:------:+:------:+:-:+:-:+:-:+:-:+
|                |            |        |        |        |        |        |        |        |        |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+
| CO transition  | Frequency  | Region                                                                |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+
| 3-10           |            |        |        |        |        |        |        |        |        |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+
|                | GHz        | N1     | N2     | N3     | N4     | N5     | S1     | S2     | S3     |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+
| 1–0            | 115.271    | 4.59   | 3.15   | 1.61   | 2.21   | 2.44   | 1.03   | 1.42   | 1.56   |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+
| 2–1            | 230.538    | 16.72  | 9.55   | 5.00   | 6.07   | 7.81   | 4.69   | 5.88   | 5.68   |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+
| $r_{21}$$^{a}$ |  $\cdots$  | 0.91   | 0.76   | 0.77   | 0.69   | 0.80   | 1.14   | 1.04   | 0.91   |   |   |   |   |
+----------------+------------+--------+--------+--------+--------+--------+--------+--------+--------+---+---+---+---+

Table notes: The fluxes are in Jy km s$^{-1}$ units. The flux uncertainties are dominated by the calibration uncertainties which are 10% for CO(1–0) and 20% for CO(2–1).

# Rovibrational CO $v$=1–0 emission model

As mentioned in Section [3.2](#ss:spectral_co_maps), in the outflow region of NGC 3256 S, the CO $v$=1–0 emission can be excited by radiative pumping. The AGN is deeply dust embedded (cite: Ohyama2015) and this dust absorbs and re-emits part of the AGN radiation in the mid-IR at $\sim$4.7 $\upmu$m. This re-emitted light behaves as a lamp that directly illuminates molecular clouds above and below the disk and excites the $v$=1 levels of CO through the absorption of $\sim$4.7 $\upmu$m continuum photons. Then, the excited molecules decay to the fundamental $v$=0 levels emitting in the $v$=1–0 P- and R-branches (see sketch in Figure [6](#fig_sketch)). For the P-branch transitions $J_{\rm up}-J_{\rm lo}=-1$, while for the R-branch transitions $J_{\rm up}-J_{\rm lo}=+1$, where $J$ is the rotational quantum number.

Under this geometry every absorbed $\sim$4.7 $\upmu$m continuum photon results in the emission of a single P- or R-branch photon (according to the transition probabilities). In this case, the radiation field from the AGN is not intense enough to affect the excitation of the molecular cloud (see Section [4.2](#ss:rp_heating)). Instead, the rovibrational CO emission acts as a probe of the physical conditions (temperature and column density) of the molecular gas in the illuminated clouds.

Here, we discuss ratios between P- and R-branch lines which trace the physical conditions of the molecular gas when the CO band is detected in emission. We used in our analysis the CO molecular data from (cite: Goorvitch1994) and the collisional coefficients from (cite: Yang2010).

## The P($J$+2)/R($J$) ratio

![](fig_models_v2.pdf)

We define the ratio between the P($J$+2) and R($J$) transitions as $f_J\equiv F_{{\rm P}(J+2)}\slash F_{{\rm R}(J)}$, where $F$ is the flux of each line. In this section, we determine the value of this ratio in the optically thin and thick limits and then we use non-local thermodynamic equilibrium (non-LTE) models to determine its dependence on the CO column density ($N({\rm CO})$), kinetic temperature ($T_{\rm kin}$), and number density ($n_{\rm H_2}$).

### Optically thin limit

In the optically thin limit, the flux of a transition is

$$\begin{equation}
F = \Omega \frac{h \nu_{ul}}{4 \pi} A_{ul} N_{\rm up}
\label{eq_flux_thin}
\end{equation}$$ where $\Omega$ is the solid angle, $h$ the Planck constant, $N_{\rm up}$ the column density of the upper level, and $\nu_{ul}$ and $A_{ul}$ are the rest frequency and Einstein $A$-coefficient of the transition, respectively.

The P($J$+2) and R($J$) transitions share the same vibrationally excited upper level ($v_{\rm up}$=1, $J_{\rm up}=J+1$). Thus, their ratio only depends on molecular constants: $$\begin{equation}
f_J^{\rm thin} = \nu_{{\rm P}(J+2)}\slash \nu_{{\rm R}(J)} \times A_{{\rm P}(J+2)}\slash A_{{\rm R}(J)}.
\end{equation}$$ The gray crosses in Figure [10](#fig_pj2_models) show the optically thin limit ratios. The observed ratios, filled red circles in the left panel of Figure [10](#fig_pj2_models), clearly deviate from this limit.

### Optically thick limit

Alternatively, if the CO rovibrational emission is optically thick, the flux of an emission line can be approximated by $$\begin{equation}
F = \Omega \Delta {\rm v} \frac{2 h \nu_{ul}^4}{c^3} \frac{N_{\rm up}\slash g_{\rm up}}{N_{\rm lo}\slash g_{\rm lo}} 
\label{eq_flux_thick}
\end{equation}$$ where $c$ is the speed of light, $g$ is the level degeneracy, $2J+1$, of the upper and lower levels, $N_{\rm lo}$ the column density of the lower level, and $\Delta {\rm v}$ the width of the line.

Therefore, the $f_J$ ratio is connected to the level population of the ground ($v$=0) CO states through this relation (cite: Sahai1985; GonzalezAlfonso2002): $$\begin{equation}
f_J^{\rm thick} = \left( \nu_{{\rm P}(J+2)}\slash \nu_{{\rm R}(J)} \right)^4  \times \frac{N_{0,J}/g_J}{N_{0,J+2}/g_{J+2}}
\label{eq_thick}
\end{equation}$$ where, $N_{v,J}$ is the population of the level with vibrational quantum number $v$ and rotational quantum number $J$, and $g_J$ is the level degeneracy. In these equations it is assumed that the population of the vibrationally excited levels ($v$=1) is much smaller than that of the ground ($v$=0) levels ($N_{0,J}/N_{1,J} \gg 1$), which is reasonable for cold molecular regions detached from the mid-IR continuum source that excites the CO rovibrational emission by radiative pumping.

Equation [\[eq_thick\]](#eq_thick) contains the ratio between the $v$=0 populations of the $J$ and $J+2$ levels, so it is also possible to connect the $f_J^{\rm thick}$ ratio and the excitation temperature, $T_{\rm rot}(J,J+2)$, within the $v$=0 state:

$$\begin{equation}
f_J^{\rm thick} = \left( \nu_{{\rm P}(J+2)}\slash \nu_{{\rm R}(J)} \right)^4 \times \exp \left( \left( E_{0,J+2} - E_{0,J}  \right)\slash T_{\rm rot}(J,J+2) \right)
\label{eq_trot}
\end{equation}$$

where $E_{v,J}$ is the energy of the level with quantum numbers $v$ and $J$. Figure [10](#fig_pj2_models) shows the optically thick limit for three temperatures (15–35 K; black lines) which, in a semi-log plot, is a straight line whose slope and $y$-intercept depend on $T_{\rm rot}$.

For $J$\<4, the observed $f_J$ (red circles in the left panel of Figure [10](#fig_pj2_models)) approximately follow a straight line, which indicates that these transitions are optically thick. For higher $J$, the observed ratios deviate from the optically thick limit toward the optically thin limit. This is expected since $N_{0,J}$, and the optical depth of the transitions, are expected to decrease with increasing $J$ for a sufficiently high $J$ and a finite column density as in real molecular clouds.

### Non-LTE models

We produced a grid of non-LTE radiative transfer models to determine the dependence of the $f_J$ ratios on $T_{\rm kin}$ and $N({\rm CO})\slash \sigma_{\rm v}$, where $\sigma_{\rm v}$ is the velocity dispersion, and the H$_2$ density, $n_{\rm H_2}$. First, we used RADEX (cite: vanderTak2007) to determine the CO $v$=0 level populations for $T_{\rm kin}$ between 12 and 50 K, $N({\rm CO})\slash \sigma_{\rm v}$ between 10$^{16.0}$ and 10$^{20}$ cm$^{-2}$/(km s$^{-1}$), and $n_{\rm H_2}$ between 10$^{2}$ and 10$^{6}$ cm$^{-3}$ with 50 log steps for each parameter (125 000 models in total).

Then, the flux of each transition is derived from the following radiative transfer equations:

$$\begin{equation}
\sigma = \nu_{ul} \times \sigma_{\rm v}\slash c \label{eq_rt_1}
\end{equation}$$ $$\begin{equation}
\phi(\nu) = \frac{1}{(2\pi)^{1/2}\sigma}\times \exp \left(-\frac{\left(\nu - \nu_{ul} \right)^2}{2\sigma^2}\right)
\end{equation}$$ $$\begin{equation}
r = \frac{N_{\rm lo}\slash g_{\rm lo}}{N_{\rm up}\slash g_{\rm up}}
\end{equation}$$ $$\begin{equation}
\tau(\nu) = \frac{c^2 A_{ul}}{8\pi\nu^2} \times N_{\rm up} \times (r - 1) \times \phi(\nu)
\end{equation}$$ $$\begin{equation}
I(\nu) = \frac{2h \nu^3}{c^2 \left( r - 1 \right)} \times \left(1 - e^{-\tau(\nu)}\right) + B_\nu(T_{\rm CMB})\times \left( e^{-\tau(\nu)} - 1 \right) \label{eq_rt_5}
\end{equation}$$

where $N$ and $g$ the column density and degeneracy of the lower and upper levels of the transition, respectively, and $B_\nu(T_{\rm CMB})$ is the black body emission of the cosmic microwave background (CMB) at 2.73 K. The CMB emission does not affect the rovibrational band, but it is needed to calculate the emission of the CO rotational transitions in Section [5](#s:conv_factor). We note that for the rovibrational transitions $r-1\simeq r$ since $N_{\rm lo}\gg N_{\rm up}$. Equation [\[eq_rt_5\]](#eq_rt_5) is the continuum subtracted emission, which we integrated over frequencies to determine the intensities of the transitions.

By using these equations we ignore line overlaps. The separation between the observed rovibrational transitions is $>470$ km s$^{-1}$ for $J$\<10, so even for the broad outflow profiles (see Figure [9](#fig_fit_model)), the effects of line overlapping are limited. In Equation [\[eq_rt_5\]](#eq_rt_5), we also ignore the term accounting for the mid-IR background continuum in our line of sight since it has a low flux compared to that of the CO rovibrational lines.

For the $v$=0 level populations we used those calculated by RADEX while for the $v$=1 populations, we assumed that $N_{1,J}= k \times N_{0,J}$, where $k \ll 1$ is a constant scaling factor.

We note that $k$ cancels out in the $f_j$ ratio, so its actual value is not relevant. Radiative excitation slightly alters the excitation temperature of the $v$=1 and $v$=0 levels, so the assumption $N_{1,J}= k \times N_{0,J}$ is not completely valid. However, when the excitation of the $v$=0 levels is dominated by collisions (see Section [4.2](#ss:rp_heating)), a grid of full radiative transfer models, created using an updated version of the (cite: GonzalezAlfonso1998) code, indicates that this is an adequate approximation since deviations are small for optically thick lines ($<$30 %). For optically thin lines the deviations are also small resulting in rotational temperatures of the $v$=1 levels 3–5 K higher than the rotational temperature of the $v$=0 levels.

Figure [10](#fig_pj2_models) shows the $f_{\rm J}$ ratios predicted by these models.

The first panel shows the dependence on $N({\rm CO})\slash \sigma_{\rm v}$ for fixed $T_{\rm kin}$ and $n_{\rm H_2}$. The ratios remain close to the optically thick limit up to a given $J$ which increases with increasing $N({\rm CO})\slash \sigma_{\rm v}$. This is because the optical depth of the transitions, $\tau$, increases with $N({\rm CO})\slash \sigma_{\rm v}$.

The middle panel of Figure [10](#fig_pj2_models) shows the dependence on $T_{\rm kin}$. For fixed $N({\rm CO})\slash \sigma_{\rm v}$ and $n_{\rm H_2}$, the low-$J$ ratios (e.g., $f_{\rm 0}$) increase with decreasing $T_{\rm kin}$. Thus, the $J$ at which the observed ratios deviate from the optically thick limit together with the low-$J$ ratios can constrain both the CO column density and $T_{\rm kin}$.

The dependence on $n_{\rm H_2}$ is presented in the right panel of Figure [10](#fig_pj2_models). For $n_{\rm H_2}\leq10^3$ cm$^{-3}$, the $f_{\rm J}$ ratios have a positive curvature before reaching the maximum value. For $n_{\rm H_2}>10^4$ cm$^{-3}$, the ratios are almost equal to the LTE limit and are not sensitive to $n_{\rm H_2}$. This positive curvature is only observed in one of the regions studied here (N5) where it can help constraining $n_{\rm H_2}$. However, in most cases this curvature is not present and we can only estimate that their $n_{\rm H_2}$ is larger than $10^{3-4}$ cm$^{-3}$.

In Section [5](#s:conv_factor), we use these non-LTE models to estimate the CO-to-H$_2$ conversion factor.

## Collisions vs. IR radiative pumping

In this section, we investigate if the excitation of the pure rotational $v$=0 levels of CO is affected by the IR radiative pumping in these regions as occurs for other molecules when the ratio between the intensity of the radiation and $n_{\rm H_2}$ is high enough (e.g., HNC and HCN; (cite: Aalto2007; Imanishi2017)).

The de-excitation of the $v$=1 CO levels is dominated by the spontaneous emission of photons in the $v$=1–0 band, which has transitions probabilities much higher than the rotational transitions within two $v$=1 levels. Moreover, the densities expected in molecular outflows are well below the critical density ($n^{\rm cr}_{\rm H_2}$$>$10$^{17}$ cm$^{-3}$ at 160 K for collisions with H$_2$; see (cite: GonzalezAlfonso2002)) of these transitions. Therefore, collisional and rotational de-excitation of the $v$=1 levels can be neglected.

In this context, it is reasonable to assume that every absorbed $\sim$4.7 $\upmu$m continuum photon is re-emitted as a single photon in the $v$=1–0 P- or R-branch. Thus, assuming that the CO $v$=1–0 emission is isotropic, we transformed the observed CO $v$=1–0 fluxes (Table [\[tbl_line_fluxes\]](#tbl_line_fluxes)) into the rate of $v$=1–0 emitted photons, that is, the IR radiative pumping rate $R_{\rm IR}$ (e.g., (cite: GonzalezAlfonso2022)). We find the rates in the range (0.3–4.1)$\times$10$^{51}$ s$^{-1}$.

To estimate the rate of collisions, first we obtained the number of CO molecules, $\mathcal{N}_{\rm CO}$, in each region from the CO(1–0) 115.27 GHz luminosity (Table [\[tbl_line_fluxes_rot\]](#tbl_line_fluxes_rot)) assuming an $\alpha_{\rm CO}$ factor and a CO abundance relative to H$_2$, $[$CO/H$_2]$. The rate of collisions is $\gamma_{ul} n_{\rm H_2} \mathcal{N}_{\rm CO}$ where $\gamma_{ul}$ are the collisional de-excitation coefficients with H$_2$ for the lowest CO $v$=0 rotational levels ((0.35–1.6) $\times$10$^{-10}$ cm$^3$ s$^{-1}$; (cite: Yang2010)).

We find that the ratio between the IR radiative pumping rate and the rate of collisions is $$\begin{multline}
\frac{R_{\rm IR}}{\gamma_{ul} n_{\rm H_2} \mathcal{N}_{\rm CO}} = (0.2-5.8)\times10^{-3}  \\
\times \frac{0.8 M_\odot\,{\rm (K\,km\,s^{-1}\,pc^2})^{-1}}{\alpha_{\rm CO}} \times 
\frac{10^4\,{\rm cm^{-3}}}{n_{\rm H_2}} \times \frac{3.2 \times 10^{-4}}{{\rm [CO\slash H_2]}}
\end{multline}$$

Thus, for the ULIRG-like $\alpha_{\rm CO}$ (0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$; (cite: Bolatto2013)) usually assumed for outflows, the excitation of the rotational CO levels is dominated by collisions for densities $n_{\rm H_2}>$10$^2$ cm$^{-2}$.

Even if the $\alpha_{\rm CO}$ of outflows is down to a factor of two lower than the ULIRG-like factor (see Section [5](#s:conv_factor)), the contribution from radiative pumping to the rotational excitation of CO would be two times higher but still not dominant ($<$2%).

![image](fig_ratio_N1_v1.pdf) ![image](fig_ratio_N2.pdf) ![image](fig_ratio_N3.pdf) ![image](fig_ratio_N4.pdf) ![image](fig_ratio_N5.pdf) ![image](fig_ratio_S1.pdf) ![image](fig_ratio_S2.pdf) ![image](fig_ratio_S3.pdf)

# CO-to-H$_2$ conversion factor

It is possible to determine the CO-to-H$_2$ conversion factor ($\alpha_{\rm CO}=M_{\rm mol}\slash L_{\rm CO(1-0)}$) if the physical conditions, $T_{\rm kin}$ and $N({\rm CO})\slash \sigma_{\rm v}$, of the gas are known. Using Equations [\[eq_rt_1\]](#eq_rt_1)-[\[eq_rt_5\]](#eq_rt_5), we derived the integrated intensity, $W$(CO(1–0)), of the CO(1–0) 115.27 GHz transition in K km s$^{-1}$. $N({\rm H_2})$ is calculated as $(N({\rm CO})\slash \sigma_{\rm v})\times \sigma_{\rm v} \slash[$CO/H$_2]$. Then, the ratio $N({\rm H_2})$/$W$(CO(1–0)), known as $X_{\rm CO}$, is converted to $\alpha_{\rm CO}$ multiplying the H$_2$ mass by 1.36 to account for helium and other elements (cite: Bolatto2013). Knowing the exact value of $\sigma_{\rm v}$ is not critical since, in the optically thick limit, $W$(CO(1–0)) $\propto T_{\rm b}\times \sigma_{\rm v}$, where $T_{\rm b}$ is the peak brightness temperature, so it cancels out in the $X_{\rm CO}$ definition.

We discuss three different methods to measure $\alpha_{\rm CO}$ using the CO $v$=1–0 band. We used a single component non-LTE model (see Section [4.1.3](#ss:nonLTE)) to fit the P($J$+2)/R($J$) ratios (Section [5.1](#ss:one_comp)). This single component models fail to reproduce the higher-$J$ ratios, so we included a second component in Section [5.2](#ss:two_comp). Finally, for the regions where the $^{13}$CO $v$=1–0 band is well detected, we used it to constrain the excitation temperature of the $^{12}$CO $v$=0 levels (Section [5.3](#ss:13co_model)).

## Single component model

Figure [11](#fig_one_comp) shows the best-fit for each region using a single non-LTE model. A single component is not able to simultaneously reproduce the low- and high-$J$ P($J$+2)/R($J$) ratios. We focus on fitting the low-$J$ transitions since these are likely tracing the bulk of the molecular gas mass.

The higher-$J$ ratio used in the fit for each region is set as the maximum $J$ that can be reproduced by a single component model (i.e., when $\chi^2$ does not significantly increases when adding that ratio). This single component model can fit between four and six ratios. The physical conditions of the gas derived for each region are listed in Table [\[tbl_single_component\]](#tbl_single_component).

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |  |  |  |  |
| Region | $T_{\rm kin}$ | $\log N({\rm CO})\slash \sigma_{\rm v}$ | $\log n_{\rm H_2}$ | $\alpha_{\rm CO}\slash\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}$ | $r_{21}$$^{b}$ | $r_{31}$$^{b}$ |  |  |  |  |
|  | K | cm$^{-2}$ (km s$^{-1}$)$^{-1}$ | cm$^{-3}$ | $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |  |  |  |  |  |  |
| N1 | 31.0 $\pm$ 1.3 | 17.71 $\pm$ 0.12 | $>$3.9 | 0.34 $\pm$ 0.07 | 1.23 $\pm$ 0.03 | 1.24 $\pm$ 0.05 |  |  |  |  |
| N2 | 22.8 $\pm$ 0.9 | 17.63 $\pm$ 0.12 | $>$3.4 | 0.40 $\pm$ 0.12 | 1.11 $\pm$ 0.03 | 1.05 $\pm$ 0.05 |  |  |  |  |
| N3 | 14.9 $\pm$ 1.1 | 17.47 $\pm$ 0.08 | $>$2.9 | 0.40 $\pm$ 0.05 | 1.05 $\pm$ 0.03 | 0.85 $\pm$ 0.05 |  |  |  |  |
| N4 | 14.9 $\pm$ 0.4 | 17.63 $\pm$ 0.08 | $>$3.0 | 0.53 $\pm$ 0.08 | 1.00 $\pm$ 0.03 | 0.85 $\pm$ 0.05 |  |  |  |  |
| N5 | 14.1 $\pm$ 0.8 | 17.96 $\pm$ 0.25 | $>$2.5 | 1.09 $\pm$ 0.56 | 1.00 $\pm$ 0.03 | 0.75 $\pm$ 0.05 |  |  |  |  |
| S1 | 27.0 $\pm$ 5.0 | $>$17.0 | $>$2.5 | $>$0.2 | 1.05 $\pm$ 0.12 | 1.05 $\pm$ 0.10 |  |  |  |  |
| S2 | 18.7 $\pm$ 0.8 | 17.31 $\pm$ 0.09 | $>$3.3 | 0.26 $\pm$ 0.02 | 1.17 $\pm$ 0.03 | 1.05 $\pm$ 0.05 |  |  |  |  |
| S3 | 26.2 $\pm$ 5.0 | $>$16.9 | $>$3.1 | $>$0.2 | 1.05 $\pm$ 0.12 | 0.95 $\pm$ 0.10 |  |  |  |  |
| Mean |  $\cdots$  $^{a}$ | 17.62 $\pm$ 0.24 |  $\cdots$  | 0.50 $\pm$ 0.30 | 1.08 $\pm$ 0.09 | 0.97 $\pm$ 0.16 |  |  |  |  |
| Median |  $\cdots$  $^{a}$ | 17.63 $\pm$ 0.20 |  $\cdots$  | 0.40 $\pm$ 0.15 | 1.05 $\pm$ 0.07 | 1.00 $\pm$ 0.15 |  |  |  |  |

Table notes: Parameters of the best-fit single component model for the selected regions (Section [5.1](#ss:one_comp)).

$T_{\rm kin}$ varies between 14 and 35 K. For these regions, we find a temperature gradient with decreasing $T_{\rm kin}$ at further distances from the nucleus. To investigate this gradient, we created a 2D map of rotational temperature using the $f_0$ ratio measured in each spaxel (Section [3.1](#ss:spectral_maps)) assuming the optically thick limit (Equation [\[eq_thick\]](#eq_thick)). In this limit, the rotational temperature is equal to $T_{\rm kin}$ if the low-$J$ levels are thermalized. Figure [12](#fig_temp_map) clearly shows, specially at the northern outflow region, that the molecular gas cools down from $>$40 K at the central 100 pc to $<$15 K at $\sim$250 pc. This result is also consistent with the low kinetic temperature ($\sim$9 K) in the molecular outflow compared to the nuclear gas temperature ($\sim$40 K) measured in the LIRG ESO 320-G030 at similar spatial scales (cite: Pereira2020).

The number density $n_{\rm H_2}$ is not well constrained in general with lower limits around 10$^{2.5-4}$ cm$^{-3}$. $N({\rm CO})\slash \sigma_{\rm v}$ is better constrained and it varies between $>$10$^{16.9}$ and 10$^{18.0}$ cm$^{-2}$ (km s$^{-1}$)$^{-1}$.

From these physical conditions, we also calculated the $\alpha_{\rm CO}$ conversion factor as described above in Section [5](#s:conv_factor). We find $\alpha_{\rm CO}$ between (0.26–0.53)$\times\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ with a median (mean) of 0.40 $\pm$ 0.15 (0.50 $\pm$ 0.30). This is $\sim$10 times lower than the Galactic $\alpha_{\rm CO}$ (4.3 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$; e.g., (cite: Bolatto2013)), and also $\sim$2 times lower than the ULIRG $\alpha_{\rm CO}$ (0.8 $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$) which is typically used to estimate the mass of cold molecular outflows (e.g., (cite: Cicone2014; Fiore2017; Pereira2018; Lutz2020; Lamperti2022)).

It is also common to observe alternative low-$J$ CO rotational transitions, like the 2–1 or the 3–2 at 230.54 and 345.80 GHz, respectively, instead of the CO(1–0). In these cases, the observed flux must be converted to an equivalent CO(1–0) flux before using the $\alpha_{\rm CO}$ factor by assuming a CO(2–1) to CO(1–0) ratio ($r_{21}$) or CO(3–2) to CO(1–0) ratio ($r_{32}$). From the models, we also determined the expected $r_{21}$ and $r_{31}$ ratios. The mean ratios are 1.08 $\pm$ 0.09 and 0.97 $\pm$ 0.16, respectively. The measured $r_{21}$ in the outflow regions are between 0.69 and 1.14 (Table [\[tbl_line_fluxes_rot\]](#tbl_line_fluxes_rot)), with a mean ratio of 0.88 $\pm$ 0.15, that is in good agreement with the models.

![](fig_ratio_temp_v1.pdf)

## Two component model

![image](fig_ratio_2c_N1_v1.pdf) ![image](fig_ratio_2c_N2.pdf) ![image](fig_ratio_2c_N3.pdf)

![image](fig_ratio_2c_S1.pdf) ![image](fig_ratio_2c_S2.pdf)

+:-------+:-------------:+:---------------------------------------:+:-:+:-------------:+:---------------------------------------:+:---------------------------------------------------------------------------:+:---------------:+:---------------:+:-:+:-:+:-:+:-:+:-:+:-:+
|        |               |                                         |   |               |                                         |                                                                             |                 |                 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| Region | Component 1                                             |   | Component 2                                             | $\alpha_{\rm CO}\slash\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}$ | $r_{21}$$^{a}$  | $r_{31}$$^{a}$  |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| 2-3    |               |                                         |   |               |                                         |                                                                             |                 |                 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
|        | $T_{\rm kin}$ | $\log N({\rm CO})\slash \sigma_{\rm v}$ |   | $T_{\rm kin}$ | $\log N({\rm CO})\slash \sigma_{\rm v}$ |                                                                             |                 |                 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
|        | K             | cm$^{-2}$ (km s$^{-1}$)$^{-1}$          |   | K             | cm$^{-2}$ (km s$^{-1}$)$^{-1}$          | $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$                                     |                 |                 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| N1     | 20 $\pm$ 7    | 18.5 $\pm$ 0.9                          |   | 39 $\pm$ 7    | 17.9 $\pm$ 0.3                          | 0.61$^{+1.06}_{-0.21}$                                                      | 1.23 $\pm$ 0.09 | 1.21 $\pm$ 0.09 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| N2     | 17 $\pm$ 3    | 18.2 $\pm$ 0.7                          |   | 32 $\pm$ 10   | 17.8 $\pm$ 0.5                          | 0.71$^{+1.23}_{-0.25}$                                                      | 1.13 $\pm$ 0.10 | 1.03 $\pm$ 0.13 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| N3     | 14 $\pm$ 1    | 17.6 $\pm$ 0.6                          |   | 23 $\pm$ 12   | 17.8 $\pm$ 0.8                          | 0.53$^{+0.73}_{-0.19}$                                                      | 1.04 $\pm$ 0.06 | 0.88 $\pm$ 0.10 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| S1     | 19 $\pm$ 5    | 18.1 $\pm$ 0.9                          |   | 31 $\pm$ 9    | 17.7 $\pm$ 0.7                          | 0.61$^{+1.32}_{-0.21}$                                                      | 1.13 $\pm$ 0.12 | 1.03 $\pm$ 0.13 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| S2     | 15 $\pm$ 2    | 17.7 $\pm$ 0.9                          |   | 25 $\pm$ 8    | 17.9 $\pm$ 0.6                          | 0.61$^{+1.06}_{-0.21}$                                                      | 1.10 $\pm$ 0.08 | 0.95 $\pm$ 0.12 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| Mean   | 17 $\pm$ 5    | 18.0 $\pm$ 0.8                          |   | 30 $\pm$ 10   | 17.8 $\pm$ 0.4                          | 0.62 $\pm$ 0.20                                                             | 1.13 $\pm$ 0.07 | 1.02 $\pm$ 0.12 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+
| Median | 17 $\pm$ 4    | 18.1 $\pm$ 0.6                          |   | 31 $\pm$ 8    | 17.8 $\pm$ 0.3                          | 0.61 $\pm$ 0.17                                                             | 1.13 $\pm$ 0.04 | 1.03 $\pm$ 0.12 |   |   |   |   |   |   |
+--------+---------------+-----------------------------------------+---+---------------+-----------------------------------------+-----------------------------------------------------------------------------+-----------------+-----------------+---+---+---+---+---+---+

Table notes: Parameters of the best-fit two-component model for the selected regions (Section [5.2](#ss:two_comp)). $\alpha_{\rm CO}$ is weighted by the intensity of the CO(1–0) 115.27 GHz intensity of each component.

The single component models are not able to reproduce all the $f_J$ ratios simultaneously. In this section, we add a second component to the models of regions with six or more $f_J$ ratios detected where a single component clearly fails to reproduce the observations. To find the best-fit model, we calculated the $\chi^2$ for all the possible combinations of two models of the grid leaving only a scaling factor between the two models (ratio between their solid angles) as a free parameter. To limit the number of combinations, we only considered three number densities: 10$^3$, 10$^4$, and 10$^5$ cm$^{-3}$ given that the CO $v$=1–0 band is not very sensitive to $n_{\rm H_2}$. In total, we explored 56 million combinations of models for each region.

The best-fit models are shown in Figure [13](#fig_two_comp). With two components, it is now possible to fit all the observed ratios. To determine the likelihood function of the parameters, we assigned a probability to each model of $\exp(-\chi^2\slash 2)$ and then calculated the marginalized likelihoods for each parameter. The parameter values are listed in Table [\[tbl_two_component\]](#tbl_two_component). We find that the best-fit models include a “cold” (Component 1), with a mean $T_{\rm kin}$ of 17 K, and a “warmer” component (Component 2), with a mean $T_{\rm kin}$ of 30 K. The $N({\rm CO})\slash \sigma_{\rm v}$ of the cold component is $\sim$10$^{18.0}$ cm$^{-2}$ (km s$^{-1}$)$^{-1}$, which is $\sim$0.2 dex higher than that of the warm component. We calculated the $\alpha_{\rm CO}$ weighted by the intensity of the CO(1–0) 115.27 GHz intensity of each component. The $\alpha_{\rm CO}$ are between (0.5–0.7)$\times\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ with a median value of 0.61 $\pm$ 0.17. These $\alpha_{\rm CO}$ are 1.3–2.3 times higher than the $\alpha_{\rm CO}$ derived using a single component model for the individual regions. It is $>$7 times lower than the Galactic $\alpha_{\rm CO}$, and slightly lower ($\sim$30%) than the ULIRG-like $\alpha_{\rm CO}$. We find that the $r_{21}$ and $r_{31}$ ratios are consistent, within the uncertainties, with those derived using a single component model (Section [5.1](#ss:one_comp)).

## Optically thin $^{13}$CO $v$=1–0 band

The P-R line ratio $f_0$ indicates that the $^{13}$CO $v$=1–0 band is optically thin (Section [3.3.2](#ss:13cothin)). Therefore, it can be used to estimate the mass of the molecular clouds in a similar way to the standard method for the sub-mm/mm $^{13}$CO rotational transitions (e.g., (cite: Papadopoulos2012b)).

From Equation [\[eq_flux_thin\]](#eq_flux_thin), for $^{13}$CO in the optically thin limit, the population of the upper level is: $$\begin{equation}
\Omega N^{\rm ^{13}CO}_{\rm up} = \frac{4 \pi}{h \nu_{ul} A_{ul}}  F^{\rm ^{13}CO} .
\label{eq_13co_pop}
\end{equation}$$

For $^{12}$CO in the optically thick limit using Equation [\[eq_flux_thick\]](#eq_flux_thick) we find:

$$\begin{equation}
\frac{\Omega N^{\rm ^{12}CO}_{\rm up}}{N^{\rm ^{12}CO}_{\rm lo} \slash \Delta {\rm v}} =  \frac{c^3}{2 h \nu_{ul}^4} \frac{g_{\rm up}}{g_{\rm lo}}  F^{\rm ^{12}CO} .
\label{eq_12co_pop}
\end{equation}$$

Thus, assuming that $\Omega$ and the excitation temperature of the $v$=1 and $v$=0 levels is the same for $^{12}$CO and $^{13}$CO, the ratio between Equations [\[eq_13co_pop\]](#eq_13co_pop) and [\[eq_12co_pop\]](#eq_12co_pop) gives for the left-hand side of the ratio (${N^{\rm ^{12}CO}_{\rm lo} \slash \Delta {\rm v}}$)$\slash [^{12}$CO/$^{13}$CO$]$. From the $^{13}$CO and $^{12}$CO R(0) transitions, we estimate $N^{\rm ^{12}CO}_{{\rm v}=0,J=0}$ /$\Delta {\rm v}$. To determine the intensity of the CO(1–0) 115.27 GHz transition using Equations [\[eq_rt_1\]](#eq_rt_1)–[\[eq_rt_5\]](#eq_rt_5), we need the population of the $N^{\rm ^{12}CO}_{{\rm v}=0,J=1}$ level, which we estimated based on the excitation temperature of the low-$J$ levels, 15–30 K, of these regions derived in Section [5.1](#ss:one_comp) (see also Table [\[tbl_single_component\]](#tbl_single_component) and Figure [12](#fig_temp_map)). The population of the remaining $N^{\rm ^{12}CO}_{{\rm v}=0,J}$ levels is also estimated using the Section [5.1](#ss:one_comp) excitation temperatures. We also need to transform the observed $\Delta {\rm v}$ (FWHM) into the $\sigma_{\rm v}$ used in Equation [\[eq_rt_1\]](#eq_rt_1). To do this, we first divided $\Delta {\rm v}$ by $\sim$2.355 to account for the ratio between FWHM and $\sigma$. The observed $\Delta {\rm v}$ also depends on the optical depths of the $^{12}$CO $v$=1–0 transitions which are unknown. To account for this uncertainty, we divided $\Delta {\rm v}$ by an extra factor between 1.2 and 2.6 (valid for $\tau$ between 1–100).

Then, estimating $M_{\rm mol}$ as described at the beginning of Section [5](#s:conv_factor), we derived the $\alpha_{\rm CO}$ conversion factor for these eight regions (Table [2](#tbl_13co_models)). The $\alpha_{\rm CO}$ values are between $(0.15-0.59)\times\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}\times\frac{[{\rm ^{12}CO}\slash {\rm ^{13}CO}]}{60}$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ with a median range of 0.19–0.36. The median $\alpha_{\rm CO}$ are 1.1–2.1 times lower than those derived using the single component non-LTE model (Section [5.1](#ss:one_comp)) and 1.7–3.2 times lower than those obtained from the two-component models (Section [5.2](#ss:two_comp)). These $\alpha_{\rm CO}$ derived from $^{13}$CO are also more than 2 and 10 times lower than the ULIRG-like and Galactic $\alpha_{\rm CO}$ factors, respectively. We note that the $\alpha_{\rm CO}$ derived using the $^{13}$CO band depend on the $^{12}$CO abundance and the $^{13}$CO to $^{12}$CO abundance ratio in the outflow, which are both uncertain. Therefore, these $\alpha_{\rm CO}$ are more uncertain than those derived using the single and two component methods (Sections [5.1](#ss:one_comp) and [5.2](#ss:two_comp)) which only depend on the $^{12}$CO abundance.

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  |  |  |  |  |  |  |  |  |
| Region | $T_{\rm kin}$ | $\alpha_{\rm CO}\slash (\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}\times\frac{[{\rm ^{12}CO}\slash {\rm ^{13}CO}]}{60})$ |  |  |  |  |  |  |  |  |
|  | K | $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ |  |  |  |  |  |  |  |  |
| N1 | 30 | 0.15–0.32 |  |  |  |  |  |  |  |  |
| N2 | 22 | 0.19–0.44 |  |  |  |  |  |  |  |  |
| N3 | 15 | 0.23–0.56 |  |  |  |  |  |  |  |  |
| N4 | 15 | 0.19–0.40 |  |  |  |  |  |  |  |  |
| N5 | 14 | 0.18–0.32 |  |  |  |  |  |  |  |  |
| S1 | 27 | 0.20–0.31 |  |  |  |  |  |  |  |  |
| S2 | 19 | 0.17–0.27 |  |  |  |  |  |  |  |  |
| S3 | 26 | 0.20–0.59 |  |  |  |  |  |  |  |  |
| Mean |  $\cdots$  | 0.19–0.40 |  |  |  |  |  |  |  |  |
| Median |  $\cdots$  | 0.19–0.36 |  |  |  |  |  |  |  |  |

: $^{13}$CO models

Table notes: Parameters of the best-fit $^{13}$CO models. The uncertainty range for $\alpha_{\rm CO}$ is related to the range of correction factors needed to take into account the unknown optical depth of the $^{12}$CO $v$=1–0 transitions (see Section [5.3](#ss:13co_model)).

# Discussion

We found that the $\alpha_{\rm CO}$ factors in the molecular outflow are 1.3–2 times lower than the ULIRG conversion factor and 6–8 times lower than the Galactic factor (assuming $[$CO/H$_2$$]$=3.2$\times$10$^{-4}$; Section [5](#s:conv_factor)). We discuss here several options to explain the origin of this reduced $\alpha_{\rm CO}$ in outflows.

For individual molecular clouds, the existence of an $\alpha_{\rm CO}$ factor, which relates the total molecular mass and the luminosity of the CO(1–0) 115.27 GHz line, relies on several assumptions: (1) the CO(1–0) emission is optically thick; (2) the molecular clouds are virialized; and (3) the mass is dominated by H$_2$ (see e.g., (cite: Bolatto2013)). Under these conditions $$\begin{equation}
\alpha_{\rm CO} \propto \frac{\sqrt{n_{\rm H_2}}}{T_{\rm kin}}. \label{eq_alphaco}
\end{equation}$$

All these assumptions seem to be valid for molecular clouds in the Milky Way and nearby spiral galaxies where $\alpha_{\rm CO}$=3.1–4.3 $M_\odot\,{\rm (K\,km\,s^{-1}\,pc^2})^{-1}$ (e.g., (cite: Sandstrom2013; Bolatto2013)). The temperatures (15–40 K) and densities ($>$10$^3$ cm$^{-3}$) we measured in the molecular outflow do not significantly differ from those observed in the molecular clouds found in disks. Thus, the $n_{\rm H_2}$ and $T_{\rm kin}$ dependencies shown in Equation [\[eq_alphaco\]](#eq_alphaco) would not explain the low $\alpha_{\rm CO}$ in the outflow.

(cite: Dasyra2016) found that the rotational CO emission in the jet-driven outflow of IC 5063 is optically thin, so $\alpha_{\rm CO}$ reaches a lower limit of 0.11 $M_\odot\,{\rm (K\,km\,s^{-1}\,pc^2})^{-1}$ (for $T_{\rm ex}$=30 K and $[$CO/H$_2$$]$=3.2$\times$10$^{-4}$). However, this explanation does not work for NGC 3256-S since the CO emission from the outflow is optically thick.

The lower $\alpha_{\rm CO}$ of ULIRGs (0.8 $M_\odot\,{\rm (K\,km\,s^{-1}\,pc^2})^{-1}$; (cite: Downes1998)) is explained because the molecular clouds of these interacting/merging systems are not virialized and the width of the line is affected by large scale motions and turbulence. This argument fits well with the conditions in outflows where the clouds are not self-gravitating (e.g., (cite: Pereira2020)). This increased velocity dispersion of the clouds increases the observed flux for optically thick lines (as in this outflow) and this results in a reduced $\alpha_{\rm CO}$ factor for the outflow.

We derived an $\alpha_{\rm CO}$ factor which depends on the $[$CO/H$_2$$]$ abundance ratio. The CO abundance in molecular outflows has not been firmly established yet, so this is a major uncertainty for these results. We assumed a standard CO abundance of 3.2$\times$10$^{-4}$ (e.g., (cite: Bolatto2013)), but CO might be dissociated in molecular outflows and become C i (cite: Cicone2018; Saito2022). If so, our $\alpha_{\rm CO}$ values would increase. However, we note that it is not possible to accurately quantify the CO to C i dissociation in outflows. The $[$C i$]$ emission is optically thin (e.g., (cite: Papadopoulos2004CI)), so the total molecular mass, including molecular gas without CO, derived from its emission depends on the assumed $[$C i/H$_2$$]$ abundance ratio which is also uncertain for outflows.

# Summary and conclusions

We studied the spatially resolved $^{12}$CO $v$=1–0 and $^{13}$CO $v$=1–0 bands, at 4.67 $\upmu$m and 4.78 $\upmu$m, respectively, around the dust-embedded AGN in the southern nucleus of NGC 3256. We modeled the ratios between the P($J$+2) and R($J$) transitions of the CO $v$=1–0 emission using a non-LTE approximation. Using these models, we constrained the column density, kinetic temperature, and $\alpha_{\rm CO}$ conversion factor of the cold molecular gas in the outflow. The main results of the paper are the following:

1.  *CO band classification.* Based on the detection in absorption or emission of the P- and R-branches of the CO $v$=1–0 band, we classify the observed spectra into three categories: (a) both branches in absorption seen basically toward the mid-IR bright nucleus; (b) P-R asymmetry (i.e., P-branch in emission and R-branch in absorption) which is detected along the disk of the galaxy; and (c) both branches in emission detected above and below the disk in the outflow region. We focused on the later to determine the physical conditions of the cold molecular gas in this AGN launched outflow.

2.  *Origin of the CO $v$=1–0 band emission.* Detecting the band in emission can be explained as follows: the radiation from the deeply embedded AGN is reprocessed by dust which emits intense mid-IR $\sim$4.7 $\upmu$m continuum radiation. Then, this continuum illuminates the molecular clouds in the outflow and excites the vibrational levels of CO resulting in the $v$=1–0 bands seen in emission in our line of sight.

3.  *Temperature gradient in the outflow.* From the spatially resolved map of the $^{12}$CO $v$=1–0 P(2)/R(0) ratio, we identify a temperature gradient in the outflow from $>$40 K in the central 100 pc to $<$15 K at 250 pc. This temperature gradient is similar to that found in the molecular outflow of the local LIRG ESO 320-G030 (cite: Pereira2020).

4.  *Reduced $\alpha_{\rm CO}$ in the outflow.* We derived the $\alpha_{\rm CO}$ conversion factor in the outflow by fitting the observed P($J$+2)/R($J$) ratios in eight 100 pc (0.5$''$) apertures in the outflow region. We used three different approaches (single non-LTE component, two non-LTE components, and $^{13}$CO models). We find $\alpha_{\rm CO}$ between (0.26–1.09)$\times \frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}$  $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$ for the non-LTE modeling with median values of 0.40 $\pm$ 0.15 and 0.61 $\pm$ 0.17 for the single and two components models, respectively. These are 1.3–2 times lower than the ULIRG-like $\alpha_{\rm CO}$ typically assumed for outflows. From the $^{13}$CO models, we find a median $\alpha_{\rm CO}$=(0.19–0.36)$\times\frac{3.2 \times10^{-4}}{[{\rm CO}\slash {\rm H_2}]}\times\frac{[{\rm ^{12}CO}\slash {\rm ^{13}CO}]}{60}$ $M_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$, which is lower than those derived from the non-LTE models, although it is subject to the uncertain $[{\rm ^{12}CO}\slash {\rm ^{13}CO}]$ abundance ratio in the outflow. The most likely explanation for this reduced $\alpha_{\rm CO}$ is that the molecular clouds in the outflow are not virialized.

5.  *D$_n$-PAH detection.* We detected a broad ($\sigma$=0.0091 $\pm$ 0.0003 $\upmu$m) spectral feature at 4.645 $\pm$ 0.002 $\upmu$m which is produced by the aliphatic C-D stretch mode in deuterated PAH (D$_n$-PAH). The D$_n$-PAH emission is detected in the disk of the galaxy and also in the apertures selected in the outflow, although the latter could be background or foreground emission not directly connected to the outflow.

6.  *Optically thick $^{12}$CO emission in the outflow.* The observed ratios indicate that the $^{12}$CO $v$=1–0 emission is optically thick, at least for $J$\<4, while the $^{13}$CO $v$=1–0 emission remains optically thin.

# Acknowledgements

We thank the referee for their useful comments and suggestions. We thank A. Alonso-Herrero for the careful reading of the manuscript and useful discussion. The authors acknowledge the GOALS DD-ERS team for developing their observing program.

MPS acknowledges funding support from the Ramón y Cajal programme of the Spanish Ministerio de Ciencia e Innovación (RYC2021-033094-I). EG-A thanks the Spanish MICINN for support under projects PID2019-105552RB-C41 and PID2022-137779OB-C41. IGB acknowledges support from STFC through grant ST/S000488/1.

This work is based on observations made with the NASA/ESA/CSA James Webb Space Telescope. The data were obtained from the Mikulski Archive for Space Telescopes at the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5-03127 for JWST; and from the European JWST archive (eJWST) operated by the ESAC Science Data Centre (ESDC) of the European Space Agency. These observations are associated with program #1328.

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00412.S, ADS/JAO.ALMA#2015.1.00714.S, ADS/JAO.ALMA#2018.1.00223.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

75 natexlab

(ref: Aalto2007) Aalto, S., Spaans, M., Wiedner, M. C., & Hüttemeister, S. 2007, A&A, 464, 193

(ref: AlonsoHerrero2019) Alonso-Herrero, A., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2019, A&A, 628, A65

(ref: AlonsoHerrero2023) Alonso-Herrero, A., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2023, A&A, 675, A88

(ref: AlonsoHerrero2018) Alonso-Herrero, A., Pereira-Santaella, M., Garcı́a-Burillo, S., et al. 2018, ApJ, 859, 144

(ref: AAH2012a) Alonso-Herrero, A., Pereira-Santaella, M., Rieke, G. H., & Rigopoulou, D. 2012, ApJ, 744, 2

(ref: Baba2022) Baba, S., Imanishi, M., Izumi, T., et al. 2022, ApJ, 928, 184

(ref: Baba2018) Baba, S., Nakagawa, T., Isobe, N., & Shirahata, M. 2018, ApJ, 852, 83

(ref: Boersma2023) Boersma, C., Allamandola, L. J., Esposito, V. J., et al. 2023, arXiv e-prints, arXiv:2310.05774

(ref: Boker2022) Böker, T., Arribas, S., Lützgendorf, N., et al. 2022, A&A, 661, A82

(ref: Bolatto2013) Bolatto, A. D., Wolfire, M., & Leroy, A. K. 2013, ARA&A, 51, 207

(ref: Buragohain2020) Buragohain, M., Pathak, A., Sakon, I., & Onaka, T. 2020, ApJ, 892, 11

(ref: Cicone2014) Cicone, C., Maiolino, R., Sturm, E., et al. 2014, A&A, 562, A21

(ref: Cicone2018) Cicone, C., Severgnini, P., Papadopoulos, P. P., et al. 2018, ApJ, 863, 143

(ref: Combes2013) Combes, F., Garcı́a-Burillo, S., Braine, J., et al. 2013, A&A, 550, A41

(ref: Dasyra2016) Dasyra, K. M., Combes, F., Oosterloo, T., et al. 2016, A&A, 595, L7

(ref: DiazSantos2010) Dı́az-Santos, T., Alonso-Herrero, A., Colina, L., et al. 2010, ApJ, 711, 328

(ref: Doney2016) Doney, K. D., Candian, A., Mori, T., Onaka, T., & Tielens, A. G. G. M. 2016, A&A, 586, A65

(ref: Downes1998) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615

(ref: Emonts2014) Emonts, B. H. C., Piqueras-López, J., Colina, L., et al. 2014, A&A, 572, A40

(ref: Feuchtgruber1997) Feuchtgruber, H., Lutz, D., Beintema, D. A., et al. 1997, ApJ, 487, 962

(ref: Fiore2017) Fiore, F., Feruglio, C., Shankar, F., et al. 2017, A&A, 601, A143

(ref: GarciaBernete2021) Garcı́a-Bernete, I., Alonso-Herrero, A., Garcı́a-Burillo, S., et al. 2021, A&A, 645, A21

(ref: GarciaBurillo2015) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2015, A&A, 580, A35

(ref: Geballe2006) Geballe, T. R., Goto, M., Usuda, T., Oka, T., & McCall, B. J. 2006, ApJ, 644, 907

(ref: Gibb2004) Gibb, E. L., Whittet, D. C. B., Boogert, A. C. A., & Tielens, A. G. G. M. 2004, ApJS, 151, 35

(ref: GonzalezAlfonso1998) González-Alfonso, E., Cernicharo, J., van Dishoeck, E. F., Wright, C. M., & Heras, A. 1998, ApJL, 502, L169

(ref: GonzalezAlfonso2022) González-Alfonso, E., Fischer, J., Goicoechea, J. R., et al. 2022, A&A, 666, L3

(ref: GonzalezAlfonso2002) González-Alfonso, E., Wright, C. M., Cernicharo, J., et al. 2002, A&A, 386, 1074

(ref: Goorvitch1994) Goorvitch, D. 1994, ApJS, 95, 535

(ref: Harada2018) Harada, N., Sakamoto, K., Martı́n, S., et al. 2018, ApJ, 855, 49

(ref: Harrison2018) Harrison, C. M., Costa, T., Tadhunter, C. N., et al. 2018, Nature Astronomy, 2, 198

(ref: Herczeg2011) Herczeg, G. J., Brown, J. M., van Dishoeck, E. F., & Pontoppidan, K. M. 2011, A&A, 533, A112

(ref: Imanishi2017) Imanishi, M., Nakanishi, K., & Izumi, T. 2017, ApJ, 849, 29

(ref: Jakobsen2022) Jakobsen, P., Ferruit, P., Alves de Oliveira, C., et al. 2022, A&A, 661, A80

(ref: Lamperti2022) Lamperti, I., Pereira-Santaella, M., Perna, M., et al. 2022, A&A, 668, A45

(ref: Leitherer2013) Leitherer, C., Chandar, R., Tremonti, C. A., Wofford, A., & Schaerer, D. 2013, ApJ, 772, 120

(ref: Lira2008) Lira, P., Gonzalez-Corvalan, V., Ward, M., & Hoyer, S. 2008, MNRAS, 384, 316

(ref: Lira2002) Lira, P., Ward, M., Zezas, A., Alonso-Herrero, A., & Ueno, S. 2002, MNRAS, 330, 259

(ref: Lutz2020) Lutz, D., Sturm, E., Janssen, A., et al. 2020, A&A, 633, A134

(ref: McClure2023) McClure, M. K., Rocha, W. R. M., Pontoppidan, K. M., et al. 2023, Nature Astronomy, 7, 431

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Michiyama2018) Michiyama, T., Iono, D., Sliwa, K., et al. 2018, ApJ, 868, 95

(ref: Najita2003) Najita, J., Carr, J. S., & Mathieu, R. D. 2003, ApJ, 589, 931

(ref: Ohyama2023) Ohyama, Y., Onishi, S., Nakagawa, T., et al. 2023, ApJ, 951, 87

(ref: Ohyama2015) Ohyama, Y., Terashima, Y., & Sakamoto, K. 2015, ApJ, 805, 162

(ref: Onaka2014) Onaka, T., Mori, T. I., Sakon, I., et al. 2014, ApJ, 780, 114

(ref: Onishi2021) Onishi, S., Nakagawa, T., Baba, S., et al. 2021, ApJ, 921, 141

(ref: Papadopoulos2004CI) Papadopoulos, P. P. & Greve, T. R. 2004, ApJL, 615, L29

(ref: Papadopoulos2012b) Papadopoulos, P. P., van der Werf, P., Xilouris, E., Isaak, K. G., & Gao, Y. 2012, ApJ, 751, 10

(ref: Peeters2004DPAH) Peeters, E., Allamandola, L. J., Bauschlicher, C. W., J., et al. 2004, ApJ, 604, 252

(ref: Pereira2010) Pereira-Santaella, M., Alonso-Herrero, A., Rieke, G. H., et al. 2010, ApJS, 188, 447

(ref: Pereira2011) Pereira-Santaella, M., Alonso-Herrero, A., Santos-Lleo, M., et al. 2011, A&A, 535, A93

(ref: Pereira2018) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2018, A&A, 616, A171

(ref: Pereira2020) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2020, A&A, 643, A89

(ref: Pereira2021) Pereira-Santaella, M., Colina, L., Garcı́a-Burillo, S., et al. 2021, A&A, 651, A42

(ref: Perrin2014) Perrin, M. D., Sivaramakrishnan, A., Lajoie, C.-P., et al. 2014, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 9143, Space Telescopes and Instrumentation 2014: Optical, Infrared, and Millimeter Wave, ed. J. Oschmann, Jacobus M., M. Clampin, G. G. Fazio, & H. A. MacEwen, 91433X

(ref: Piqueras2012) Piqueras López, J., Colina, L., Arribas, S., Alonso-Herrero, A., & Bedregal, A. G. 2012, A&A, 546, A64

(ref: RamosAlmeida2022) Ramos Almeida, C., Bischetti, M., Garcı́a-Burillo, S., et al. 2022, A&A, 658, A155

(ref: Rettig2005) Rettig, T. W., Brittain, S. D., Gibb, E. L., Simon, T., & Kulesa, C. 2005, ApJ, 626, 245

(ref: Roueff2019) Roueff, E., Abgrall, H., Czachorowski, P., et al. 2019, A&A, 630, A58

(ref: Sahai1985) Sahai, R. & Wannier, P. G. 1985, ApJ, 299, 424

(ref: Saito2022) Saito, T., Takano, S., Harada, N., et al. 2022, ApJ, 935, 155

(ref: Sakamoto2014) Sakamoto, K., Aalto, S., Combes, F., Evans, A., & Peck, A. 2014, ApJ, 797, 90

(ref: SanchezGarcia2022) Sánchez-Garcı́a, M., Pereira-Santaella, M., Garcı́a-Burillo, S., et al. 2022, A&A, 659, A102

(ref: Sandstrom2013) Sandstrom, K. M., Leroy, A. K., Walter, F., et al. 2013, ApJ, 777, 5

(ref: Shirahata2013) Shirahata, M., Nakagawa, T., Usuda, T., et al. 2013, PASJ, 65, 5

(ref: Somerville2015) Somerville, R. S. & Davé, R. 2015, ARA&A, 53, 51

(ref: Spoon2004) Spoon, H. W. W., Armus, L., Cami, J., et al. 2004, ApJS, 154, 184

(ref: Spoon2003) Spoon, H. W. W., Moorwood, A. F. M., Pontoppidan, K. M., et al. 2003, A&A, 402, 499

(ref: Storey1995) Storey, P. J. & Hummer, D. G. 1995, MNRAS, 272, 41

(ref: Ueda2022) Ueda, J., Michiyama, T., Iono, D., Miyamoto, Y., & Saito, T. 2022, PASJ, 74, 407

(ref: vanderTak2007) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: Veilleux2020) Veilleux, S., Maiolino, R., Bolatto, A. D., & Aalto, S. 2020, A&ARv, 28, 2

(ref: Yang2010) Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062

(ref: Yang2023) Yang, X. J. & Li, A. 2023, arXiv e-prints, arXiv:2308.04085

[^1]: <https://mast.stsci.edu/portal/Mashup/Clients/Mast/Portal.html>

</paper>

Write the methods card for this paper.