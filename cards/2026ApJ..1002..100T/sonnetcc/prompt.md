# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2026ApJ..1002..100T\sonnetcc\reply.txt

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
 "bibcode": "2026ApJ..1002..100T",
 "title": "Multiphase Gas Structure in the Circumnuclear Region of NGC 5506 Observed with ALMA",
 "year": 2026,
 "journal": "The Astrophysical Journal",
 "first_author": "Takechi, Kana",
 "n_authors": 10,
 "arxiv_id": "2604.07587",
 "doi": "10.3847/1538-4357/ae5703",
 "alma_projects_linked_by_archive": [
  "2017.1.00082.S",
  "2022.1.00410.S"
 ]
}
```

Paper text:
<paper>
# Multiphase Gas Structure in the Circumnuclear Region of NGC 5506 Observed with ALMA

## Abstract

We present a study of the multiphase gas structure and kinematics of the circumnuclear disk (CND) of NGC 5506, a nearby edge-on Seyfert galaxy, at a spatial resolution of $\sim20$ pc. Observations of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3) obtained with the Atacama Large Millimeter/submillimeter Array reveal the CND dominated by rotational motion on scales of several hundred parsecs. No significant differences in geometrical thickness or velocity structure are found between \[C I\](1–0) and CO(3–2) across the CND, whereas HCO$^{+}$(4–3) emission is more concentrated toward the disk plane. The ratio of velocity dispersion to rotational velocity, a proxy for disk scale height-to-radius ratio, is high ($\gtrsim0.9$) in the central region ($\lesssim30$ pc) for both \[C I\](1–0) and CO(3–2), indicating geometrically thick structures in both tracers. Regions where the \[C I\](1–0)/CO(3–2) ratio exceeds the CND average are spatially correlated with the \[O III\]$\lambda5007$ bicone observed with the Hubble Space Telescope, suggesting that CO is preferentially dissociated by the AGN-driven biconical ionized outflow. The observed CND scale height and velocity dispersions traced by \[C I\](1–0) and CO(3–2) are consistent with a model in which supernova-driven turbulence provides the vertical support for the CND.

# Introduction

An active galactic nucleus (AGN) is the compact central region of a galaxy characterized by intense electromagnetic radiation. In the AGN unified model, the presence or absence of broad emission lines is attributed to the viewing angle relative to a geometrically and optically thick torus-shaped structure (cite: Antonucci1993; Urry1995). Constraining the physical properties of the torus is essential for understanding supermassive black hole (SMBH)–host galaxy coevolution (cite: Kormendy2013), as this structure is thought to play a crucial role in the mass supply from the host galaxy to the SMBH.

The torus has been investigated both theoretically and observationally. Early continuous dust torus models failed to reproduce the observed 9.7 $\mathrm{\mu m}$ silicate feature (cite: Pier1992; Pier1993). This motivated the development of clumpy dust models (cite: Nenkova2002; Nenkova2008a; Nenkova2008b; Elitzur2006b; Honig2006; Schartmann2008; Schartmann2009; Levenson2009). The high observed fraction of type-2 AGN implies that the torus is geometrically thick (cite: Lawrence2010; Merloni2014; Davies2015). However, the mechanism responsible for supporting this geometrical thickness remains uncertain. (cite: Krolik2007) presented an axisymmetric torus model supported by infrared radiation pressure (cite: Shi2008). Several models have incorporated the effects of nuclear starburst activity, which is commonly observed in AGN host galaxies (cite: Heckman1997; Cid2001; Gonzalez2001; Davies2007). (cite: Ohsuga1999; Ohsuga2001) proposed that radiation pressure from both the AGN and the nuclear starburst can support a dusty obscuring wall. A supernova (SN)-driven turbulent torus model was introduced by (cite: Wada2002). (cite: Kawakatu2020) subsequently investigated the dependence of the AGN obscuring fraction on black hole mass and AGN luminosity, incorporating both SN-driven turbulence and AGN radiative feedback.

Polar elongation observed in the mid-infrared (cite: Tristram2014; Asmus2016) suggests that the torus is dynamically formed rather than static. The radiation-driven fountain model (cite: Wada2012) was proposed to explain these observations. Three-dimensional hydrodynamic simulations based on this framework demonstrate that the torus thickness can be dynamically maintained through gas circulation (cite: Wada2012). The model was extended to include SN feedback and nonequilibrium chemistry in X-ray-dominated regions (cite: Wada2016), allowing detailed predictions for the distributions of atomic, molecular, and ionized gas. This model has been tested against multiwavelength observations of the Circinus galaxy, a nearby Seyfert galaxy (cite: Izumi2018; Wada2018a; Wada2018b; Uzuo2021; Tanimoto2023; Baba2024). In particular, (cite: Izumi2018) identified kinematic signatures in \[C I\](1–0) and CO(3–2) consistent with the model predictions, although these were not evident in subsequent higher-resolution observations (cite: Izumi2023).

The development of high angular resolution facilities such as the Atacama Large Millimeter/submillimeter Array (ALMA) has enabled observations of AGN circumnuclear regions on scales of a few to several tens of parsecs (cite: Imanishi2018; Combes2019; Garcia2021; Izumi2023). Nevertheless, the physical properties and formation mechanisms of the torus remain poorly constrained, motivating high-resolution observations of additional nearby systems. In this study, we analyze ALMA and Hubble Space Telescope (HST) observations of the circumnuclear region of NGC 5506 to characterize the distribution and kinematics of atomic, molecular, and ionized gas, and to compare these results with theoretical models.

NGC 5506 is a nearby Seyfert galaxy classified in the literature as type-2 (cite: Trippe2010), type-1.9 (cite: Maiolino1995), or narrow-line Seyfert 1 (cite: Nagar2002). The circumnuclear disk (CND) of NGC 5506 is viewed at a nearly edge-on inclination, which enhances the sensitivity to differences in geometrical thickness among multiple gas phases. Throughout this paper, we define the CND of NGC 5506 as the region where emission is detected at $>3.5\sigma$ within a 5$^{\prime\prime}\times1^{\prime\prime}.4$ box centered on the AGN. NGC 5506 hosts an SMBH with a mass of $2.0^{+8.0}_{-1.6}\times 10^7~M_{\odot}$ (cite: Gofford2015), derived as the logarithmic mean of two independent estimates: $8.8\times10^{7}~M_{\odot}$ (cite: Papadakis2004), and $5.11\times10^{6}~M_{\odot}$ (cite: Nikolajuk2009). The bolometric luminosity is 1.3 $\times$ 10$^{44}$ erg s$^{-1}$ (cite: Davies2020), and the Eddington ratio is $\lambda_{\rm Edd} = 0.05^{+0.21}_{-0.04}$ (cite: Esposito2024). Outflow activity in NGC 5506 has been confirmed by the detection of an ultrafast outflow (cite: Gofford2013; Gofford2015) and radio jet emission (cite: Kinney2000; Roy2000; Roy2001). HST imaging and kinematic modeling of \[O III\]$\lambda5007$ reveal a biconical ionized outflow with an inclination of $10^\circ$ and a maximum velocity of 550 km s$^{-1}$ on scales of 300 pc (cite: Fischer2013). We assume a flat $\Lambda$CDM cosmology with $H_0=67.66$ km s$^{-1}$ Mpc$^{-1}$, $\Omega_{\rm m}=0.3111$, and $\Omega_{\Lambda}=0.6889$ (cite: Planck2020). We adopt a luminosity distance of 23.8 Mpc for NGC 5506 (cite: Karachensev2014), at which 1$^{\prime\prime}$ corresponds to 114 pc.

# Observation and Data Analysis

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line Name | Species | Transition | Wavelength | Frequency | Critical Density | Reference$^{1}$ |
|  |  |  | ($\mathrm{\mu m}$) | (GHz) | (cm$^{-3}$) |  |
| $[$C I$]$(1–0) | C | $^3P_1\rightarrow^3P_0$ | 370.4 $\rm$ | 492.2 | $4.7\times10^2$ | \(1\) |
| CO(3–2) | CO | $J=3\rightarrow2$ | 867.0 | 345.8 | $8.4\times10^3$ | \(2\) |
| HCO$^{+}$(4–3) | HCO$^{+}$ | $J=4\rightarrow3$ | 840.4 | 356.7 | $1.8\times10^6$ | \(2\) |
| $[$O III$]$$\lambda5007$ | $\rm O^{2+}$ | $^1D_2\rightarrow^3P_2$ | $500.7\times10^{-3}$ | $598.7\times10^3$ | $6.8\times10^5$ | \(3\) |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | Project ID | Date$^1$ | $\#$ Antennas$^2$ | Baseline$^3$ | On-source Time$^4$ | Pipeline Version$^5$ |
|  |  | (UT) |  | \(m\) | (h:mm:ss) |  |
| (1–0) | 2022.1.00410.S | 2023 Apr 13, 20 | 42 | 14–1198 | 2:00:57 | 2022.2.0.68 |
| CO(3–2) | 2017.1.00082.S | 2017 Dec 31 | 44 | 14–2309 | 0:33:24 | Pipeline-CASA51-P2-B |
| HCO$^{+}$(4–3) | 2017.1.00082.S | 2017 Dec 31 | 44 | 14–2309 | 0:33:24 | Pipeline-CASA51-P2-B |

|  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Emission | Telescope | $\nu_{\rm rest}$ | Beamsize, PA | Beamsize | rms | Peak |
|  |  | (GHz) | (arcsec $\times$ arcsec), (deg) | (pc $\times$ pc) | (mJy beam$^{-1}$) | (mJy beam$^{-1}$) |
| (1–0)$^1$ | ALMA | 492.2 | 0.166 $\times$ 0.143, (70.6) | 19.1 $\times$ 16.4 | 7.7 | 87 |
| CO(3–2)$^2$ | ALMA | 345.8 | 0.176 $\times$ 0.135, (-52.8) | 20.2 $\times$ 15.5 | 2.2 | 56 |
| HCO$^{+}$(4–3)$^2$ | ALMA | 356.7 | 0.174 $\times$ 0.134, (-54.4) | 20.0 $\times$ 15.4 | 0.69 | 4.7 |
| $[$O III$]$ $\lambda5007^3$ | HST | $598.7\times10^{3}$ | ... | ... | ... | ... |

We analyze ALMA and HST observations of NGC 5506 to investigate the multiphase gas structure and kinematics of the CND. The emission lines used in this study are \[C I\](${}^3P_1-{}^3P_0$; hereafter 1–0), CO($J=3\textrm{--}2$; hereafter 3–2), HCO$^{+}$($J=4\textrm{--}3$; hereafter 4–3), and \[O III\]$\lambda$5007, which trace atomic, molecular, dense molecular, and ionized gas, respectively. Line properties are listed in Table [\[tbl:lines\]](#tbl:lines). The \[O III\]$\lambda$5007 line was observed with HST (observation ID: x2740302t); the other lines were observed with ALMA in Cycle 5 (project ID: 2017.1.00082.S) and Cycle 9 (project ID: 2022.1.00410.S). Observational parameters are summarized in Table [\[tbl2\]](#tbl2).

## ALMA

We observed \[C I\](1–0) with ALMA Band 8 in Cycle 9. CO(3–2) and HCO$^{+}$(4–3) were obtained from archival Band 7 observations. Baseline lengths are 14–1198 m for \[C I\](1–0) and 14–2309 m for CO(3–2) and HCO$^{+}$(4–3); the ranges of $\it{uv}$-distance in units of wavelength are comparable across all three datasets. Calibration was performed using the ALMA pipeline in Common Astronomy Software Applications (cite: Casa2022), with one, two, and two antennas flagged for \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3), respectively. Calibrated data were imaged using CASA (version 6.5.6) task `tclean` with a channel width of 20 km s$^{-1}$. Automasking was applied following the parameters recommended in the CASA automasking guide. We set the `nsigma` parameter to 2, corresponding to a cleaning threshold of $2\times$ the rms noise (cite: Casa2022). Because this study compares geometrical thicknesses among different gas phases, the Briggs `robust` parameter was adjusted to synthesize comparable beam sizes across all three lines. HCO$^{+}$(4–3) data were imaged with `robust` = 2.0 (natural weighting), resulting in a synthesized beam size of $0.^{\prime\prime}174\times0.^{\prime\prime}134$. For \[C I\](1–0) and CO(3–2), `robust` values of 0.8 and 1.3 were used, producing synthesized beam sizes of $0.^{\prime\prime}166 \times 0.^{\prime\prime}143$ and $0.^{\prime\prime}176 \times 0.^{\prime\prime}135$, respectively. Imaging properties are summarized in Table [\[tbl1\]](#tbl1). The ALMA Cycle 9 Proposer’s Guide indicates absolute flux uncertainties of $\sim10\%$ for both Band 7 and 8. Throughout this paper, error values represent only statistical uncertainties unless otherwise noted.

## HST

\[O III\]$\lambda$5007 was observed with the HST Faint Object Camera (FOC) using the f/96 aperture and the F501N filter (cite: Nota1996). The dataset covers only the northern side of the emission (cite: Ruiz2005). The FOC image exhibits an astrometric offset of approximately 3$\ensuremath{''}$. To correct the WCS coordinates, we used an HST STIS image and two reference stars within the field of view: Star A at (R.A., decl.) = (14$^{\rm h}$13$^{\rm m}$15$^{\rm s}$.91, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$21$\ensuremath{''}$.07) and Star B at (R.A., Decl.) = (14$^{\rm h}$13$^{\rm m}$14$^{\rm s}$.82, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$22$\ensuremath{''}$.42). Star A is listed in the Pan-STARRS1 (PS1) catalog and serves as the primary astrometric reference (cite: Chambers2016), but is not detected in the FOC image. Star B is detected in the FOC image but not listed in the PS1 catalog. The STIS image was used to transfer the astrometric reference between Stars A and B. Centroids of both stars were measured using `DAOStarFinder` from the `photutils` package (cite: Bradley2024). The STIS image was first aligned to the PS1 catalog, then used to determine the position of Star B. The FOC image was subsequently adjusted such that Star B coincides with this position, resulting in an astrometric accuracy better than 0$\ensuremath{''}$.2. The point spread function (PSF) of the \[O III\]$\lambda$5007 image was measured using `SExtractor` (cite: Bertin1996) by fitting a point source at (R.A., Decl.) = (14$^{\rm h}$13$^{\rm m}$14$^{\rm s}$.69, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$24$\ensuremath{''}$.90). This yields a full width at half-maximum (FWHM) of 0$^{\prime\prime}$.054.

# Results

![](Fig1_v2.pdf)

![](Fig2_v2.pdf)

![](Fig3_v2.pdf)

![](Fig4_v2.pdf)

![](Fig5_v2.pdf)

Figure [1](#fig:momentmaps) presents the moment maps of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3), generated using pixels with a signal-to-noise ratio $>3.5$. The CND is defined as the region with emission detected at $>3.5\sigma$ within a 5$^{\prime\prime}$$\times$1$^{\prime\prime}.4$ box centered on the AGN. The red plus sign in each panel marks the AGN position (R.A., decl.) = (14$^{\rm h}$13$^{\rm m}$14$^{\rm s}$.877, $-$3$\ensuremath{^\circ}$12$\ensuremath{'}$27$\ensuremath{''}$.66). This position is determined from the peak of the Band 7 continuum (Figure [2](#fig:cont)), and is consistent with the Band 8 continuum peak. Figure [3](#fig:OIII) shows the HST/FOC F501N image tracing \[O III\]$\lambda$5007 emission, with contours at 1$\sigma$, 2$\sigma$, 3$\sigma$, 5$\sigma$, 7$\sigma$, 9$\sigma$, 11$\sigma$, and 13$\sigma$. The red line marks the edge of the HST field of view.

## Gas Morphology

Figure [4](#fig:mom0)(a), (d), and (g) show zoomed-in moment 0 maps of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3). The white line in each panel indicates the major axis of the CND (position angle (PA)$=268^{\circ}$), determined from kinematic modeling with 3D-Based Analysis of Rotating Objects via Line Observations (`3D Barolo`; see Section [4.2.1](#subsec:vdisp)).

Figure [5](#fig:majslice) shows the intensity profiles along the major axis extracted from the moment 0 maps of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3). All tracers exhibit two primary peaks to the east and west of the AGN, at $21\pm9$ pc and $64\pm9$ pc for \[C I\](1–0), $35\pm9$ pc and $60\pm9$ pc for CO(3–2), and $5\pm9$ pc and $51\pm9$ pc for HCO$^{+}$(4–3). No emission peak is detected at the AGN position in \[C I\](1–0) or CO(3–2), whereas HCO$^{+}$(4–3) shows a peak within one beam of the AGN. In all tracers, the midpoint between the two peaks is offset to the west of the AGN.

## Velocity structure

The moment 1 maps (Figure [4](#fig:mom0)(b), (e), and (h)) show the flux-weighted mean line-of-sight velocity. The systemic velocity ($V_{\rm sys}$) of the CND was determined by fitting a rotating disk model to CO(3–2) data ($1872\pm10$ km s$^{-1}$; see Section [4.2.1](#subsec:vdisp)), and adopted for \[C I\](1–0) and HCO$^{+}$(4–3) as well. In all three tracers, the western side is redshifted, and the eastern side is blueshifted, consistent with rotational motion. At the AGN position, the flux-weighted mean line-of-sight velocities are $1859\pm10$ km s$^{-1}$, $1865\pm10$ km s$^{-1}$, and $1889\pm10$ km s$^{-1}$ for \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3), respectively. The velocity of HCO$^{+}$(4–3) at the AGN position is redshifted by $\sim +17$ km s$^{-1}$ relative to $V_{\rm sys}$, which may indicate inflow motion toward the AGN. The systemic velocity contours of \[C I\](1–0) and CO(3–2) in the moment 1 maps (black lines in Figure [4](#fig:mom0)(b) and (e)) deviate from the kinematic minor axis.

![](Fig6_v2.pdf)

Figure [6](#fig:pvd) shows the position–velocity diagrams (PVDs) extracted along the major axis of the CND. The PVDs appear symmetric about both the systemic velocity and the AGN position, confirming the validity of these reference values. No signatures of a bar structure are evident in the PVDs.

# Discussion

## Geometrical Structure

### Overall Structure

As described in Section [3.1](#sec:resmor), the moment 0 maps of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3) each exhibit two intensity peaks, consistent with a torus-shaped CND. Similar off-nuclear double-peaked CO emission has been reported in other highly inclined galaxies, including NGC 7314 (cite: Garcia2021) and NGC 1380 (cite: Kabasares2022). In contrast, \[O III\]$\lambda$5007 shows a conical morphology confirmed spectroscopically by (cite: Fischer2013).

### Geometrical Thickness of the Circumnuclear Disk

![](Fig7_v2.pdf)

We compare the geometrical thickness of the CND among different gas phases. Because NGC 5506 is highly inclined (inclination $i=79^{\circ}$; see Section [4.2.1](#subsec:vdisp)), the geometrical thickness of the CND can be inferred from the emission width along the minor axis direction [^1]. Slice profiles of the moment 0 maps are extracted along lines parallel to the minor axis (e.g., Figure [7](#fig:slice)(a)) at 4 pixel ($\sim9$ pc) intervals along the major axis and averaged over a 3 pixel ($\sim7$ pc) width. Each profile is fitted with a Gaussian (solid lines in Figure [7](#fig:slice)(b)), with the peak fixed to the corresponding major axis position. The FWHM of each best-fit Gaussian is then derived as a measure of the emission width.

Figure [7](#fig:slice)(c) compares the FWHM values of the three tracers from $-90$ to 90 pc. HCO$^{+}$(4–3) exhibits the smallest FWHM at nearly all positions (18 out of 19). Within 20 pc of the AGN, CO(3–2) shows a marginally larger FWHM than \[C I\](1–0), although most differences are within the uncertainties. At larger radii, \[C I\](1–0) tends to have a larger FWHM, except in the western region beyond 50 pc of the AGN, where the trend reverses. Throughout the CND, the FWHM values of \[C I\](1–0) and CO(3–2) differ by less than a factor of 2 without a systematic trend. We therefore conclude that these two tracers have comparable geometrical thicknesses. Both \[C I\](1–0) and CO(3–2) reach maximum FWHM values of $\gtrsim 80$ pc, whereas HCO$^{+}$(4–3) forms a thinner disk with a maximum FWHM of $\sim 50$ pc.

## Gas Dynamics

### Disk Thickness Inferred from Gas Dynamics

![](Fig8_v2.pdf)

We model the kinematics of the CND in NGC 5506 using a three-dimensional tilted-ring approach with `3D BAROLO` (cite: DiTeodoro&Fraternali2015). The systemic velocity ($V_{\rm sys}$), inclination ($i$), and PA are first determined from the CO(3–2) data cube, which has the highest signal-to-noise ratio among the three lines. During this step, the radial velocity is fixed to $0$ km s$^{-1}$. The fit is restricted to radii smaller than 200 pc to focus on the AGN vicinity and avoid contamination from a redshifted region southeast of the AGN that appears unrelated to disk rotation. The ring separation is set to 0.176$^{\prime\prime}$, comparable to the major-axis FWHM of the CO(3–2) synthesized beam. The innermost radius is fixed at 0.088$^{\prime\prime}$, ensuring that the first ring lies outside a single beam element. A single-plane disk model is adopted with warping disabled, as no evidence for a warped disk has been reported in NGC 5506. The fit yields $V_{\rm sys}$ = 1872 km s$^{-1}$, $i=79^{\circ}$, and PA $=268^{\circ}$, consistent with the values reported by (cite: Esposito2024) ($V_{\rm sys}=1872$ km s$^{-1}$, $i=80^{\circ}$, and PA$=265^{\circ}$). With $V_{\rm sys}$, $i$, and PA fixed to these values, `3D BAROLO` is then applied independently to the \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3) data cubes. At each radius, the rotational velocity ($V_{\rm rot}$) and the velocity dispersion ($V_{\rm disp}$) are treated as free parameters.

The ratio $V_{\rm {disp}}$/$V_{\rm {rot}}$ is plotted as a function of radius in Figure [8](#fig:disptorot)(a). Under the assumption of hydrostatic equilibrium, this ratio serves as a proxy for the disk scale height-to-radius ratio ($H/R$; (cite: Izumi2018)). HCO$^{+}$(4–3) exhibits lower $V_{\rm {disp}}$/$V_{\rm {rot}}$ than the other two tracers at most radii, although the differences are largely within the uncertainties. Within 100 pc, no significant difference in $V_{\rm {disp}}$/$V_{\rm {rot}}$ is found between \[C I\](1–0) and CO(3–2). At radii beyond 100 pc, CO(3–2) tends to show higher $V_{\rm {disp}}$/$V_{\rm {rot}}$ than \[C I\](1–0) and HCO$^{+}$(4–3). The ratio reaches particularly high values ($\gtrsim 0.9$) at the innermost radius for both \[C I\](1–0) and CO(3–2) (see Section [4.4](#sec:interp) for further discussion), suggesting a high $H/R$. The large uncertainties in $V_{\rm {disp}}$/$V_{\rm {rot}}$ of \[C I\](1–0) and HCO$^{+}$(4–3) at the innermost radius arise from the small rotational velocity at that radius. The comparable $V_{\rm {disp}}$/$V_{\rm {rot}}$ of \[C I\](1–0) and CO(3–2) and the lower ratio of HCO$^{+}$(4–3) within 100 pc are consistent with the geometrical thickness comparison presented in Section [4.1.2](#subsec:geom).

### Radial Velocity

![](Fig9_v2.pdf)

We derive the mean radial velocities of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3). Figure [9](#fig:outflows)(a), (e), and (i) show the best-fit moment 1 maps without an outflow component. The corresponding residual maps (Figure [9](#fig:outflows)(b), (f), and (j)) exhibit a systematic redshift on the northern side and blueshift on the southern side, consistent with a radial outflow. We therefore include a constant outward radial velocity (hereafter outflow velocity, $V_{\rm out}$) and repeat the fitting with $V_{\rm out}$ values from 0 to 40 km s$^{-1}$ in steps of 10 km s$^{-1}$. The best-fit models, including the optimal outflow that minimizes the residual rms are shown in Figure [9](#fig:outflows)(c), (g), and (k). The optimal outflow velocities are 20$~\pm~5$ km s$^{-1}$ for \[C I\](1–0), 30$~\pm~5$ km s$^{-1}$ for CO(3–2), and 20$~\pm~5$ km s$^{-1}$ for HCO$^{+}$(4–3). The optimal outflow velocity of CO(3–2) is consistent with the value reported by (cite: Esposito2024). Because CO(3–2) has the largest spatial extent among the three tracers, it samples emission from outer radii where the outflow velocity is higher (Figure [9](#fig:outflows)(f)). This likely accounts for the higher $V_{\rm out}$ inferred from CO(3–2) relative to \[C I\](1–0) and HCO$^{+}$(4–3).

## \[C I\](1–0)/CO(3–2) Line Ratio

![](Fig10_v2.pdf)

We derive \[C I\](1–0)/CO(3–2) integrated intensity ratio ($R_{\rm [C~I]/CO}$) from the moment 0 maps. Because atomic carbon can be produced through CO dissociation by high-energy photons, this ratio is sensitive to the local radiation field and thus provides insight into the origin of the multiphase gas.

The color map in Figure [10](#fig:lineratoiii) shows the spatial distribution of $R_{\rm [C~I]/CO}$ on a brightness temperature scale. The mean ratio across the entire CND is $0.52\pm0.07$, higher than values typical of star-forming galaxies (cite: Liu2023). This suggests that high $R_{\rm [C~I]/CO}$ is driven by nonstellar processes, such as X-ray irradiation from the AGN or interactions between the CND and an AGN-driven biconical ionized outflow. Additionally, regions to the northeast and southwest of the AGN exhibit particularly elevated ratios. Although AGN X-ray emission likely contributes to CO dissociation across the CND, it cannot account for the nonaxisymmetric distribution of the elevated $R_{\rm [C~I]/CO}$ regions. We therefore focus on the outflow interaction scenario in this section.

|                    | $R_{\rm [C~I]/CO}$ |     |     |
|:------------------:|:------------------:|:---:|:---:|
|        CND         |   $0.52\pm0.07$    |     |     |
| Inside the bicone  |   $0.82\pm0.11$    |     |     |
| Outside the bicone |   $0.47\pm0.07$    |     |     |

: Integrated Line Ratio ($R_{\rm [C~I]/CO}$)

The $R_{\rm [C~I]/CO}$ map in Figure [10](#fig:lineratoiii) is overlaid with contours of \[O III\]$\lambda$5007 emission (white) and the corresponding biconical outflow model (cite: Fischer2013). The figure shows a spatial correlation between the \[O III\]$\lambda$5007 emission and the elevated $R_{\rm [C~I]/CO}$ regions.

Ionized gas on the southern side of the AGN has been detected in \[O III\] (cite: Esposito2024) and \[Ne V\] (cite: Zhang2024), but the southern ionization cone is not detected in the HST observations presented here for the following reasons.

The CND has an inclination of $79^{\circ}$, with the northern face tilted 11$^\circ$ from edge-on toward the observer. The southern cone thus lies on the far side of the disk and is projected against the foreground molecular disk traced by CO(3–2) (Figure [1](#fig:momentmaps)(d)), where line-of-sight obscuration by molecular gas and/or dust likely suppresses the \[O III\] emission. Furthermore, the less obscured regions of the southern cone are outside the field of view of this observation.

Table [1](#tbl:linerat) summarizes the mean $R_{\rm [C~I]/CO}$ for the entire CND and for regions inside and outside the bicone. The mean ratio inside the bicone ($0.82\pm0.11$) is higher than that outside the bicone ($0.47\pm0.07$). This suggests that CO is preferentially dissociated at the interface where the ionized outflow interacts with the CND. A plausible mechanism is that the outflow drives shocks into the molecular gas, and the resulting shock heating and/or shock-accelerated cosmic rays enhance CO dissociation. A similar trend has been reported in another Seyfert 2 galaxy, NGC 1068. The \[C I\](1–0)/CO(1–0) intensity ratio in NGC 1068 is spatially correlated with the \[S III\]/\[S II\], a tracer of the ionization cone (cite: Saito2022). (cite: Saito2022) suggest that this correlation arises from the dissociation of CO into atomic carbon by the AGN-driven biconical ionized outflow, consistent with the scenario proposed here for NGC 5506.

## Interpretation of Morphology and Kinematics of \[C I\](1–0) and CO(3–2) Lines

In this section, we discuss the factors contributing to the geometrical thickness of the CND. As shown in Figure [7](#fig:slice)(c), \[C I\](1–0) and CO(3–2) show no significant differences in geometrical thickness, whereas HCO$^{+}$(4–3) is more concentrated toward the disk plane. These results are supported by the $V_{\rm disp}/V_{\rm rot}$ ratio, a proxy for $H/R$, shown in Figure [8](#fig:disptorot)(a). Within a radius of 100 pc, this ratio is comparable between \[C I\](1–0) and CO(3–2). The ratio reaches particularly high values ($\gtrsim 0.9$) in the central region ($\lesssim30$ pc), higher than the value reported for the Circinus galaxy (cite: Izumi2018). High $H/R$ values in molecular gas have also been reported in other Seyfert galaxies based on the H$_2(\nu=$1–0 S(1), rest frame 2.1 $\mu$m) line (cite: Hicks2009).

The radiation-driven fountain model (cite: Wada2012) proposes that a geometrically thick torus-shaped structure can be supported through gas circulation driven by AGN radiative feedback. (cite: Schartmann2014) demonstrate that such fountain flows reproduce the observed differences in the spectral energy distributions (SEDs) of type-1 and type-2 Seyfert galaxies. Additionally, the polar dust emission that dominates the mid-infrared range (cite: Asmus2016) is naturally explained within this framework. (cite: Wada2016) extend the radiation-driven fountain model to incorporate SN feedback and nonequilibrium chemistry in X-ray-dominated regions. Their simulations show that atomic hydrogen forms a geometrically thick torus, molecular hydrogen (H$_2$) is confined primarily to the disk plane, and ionized gas forms a biconical structure. Simulations by (cite: Baba2024) further predict distinct spatial distributions for C, CO, and HCO$^{+}$; neutral carbon forms a geometrically thick torus while CO and HCO$^{+}$ are confined primarily to the disk plane.

(cite: Wada2015) shows that the structure of the fountain flow depends on both the black hole mass and the AGN luminosity (or Eddington ratio); the scale height increases with Eddington ratio and decreases with black hole mass. Once the fountain flow is established, variations in the radiation field and thermal conditions produce distinct spatial distributions of atomic and molecular gas. However, when the Eddington ratio is too low (e.g., $\lambda_{\rm Edd}\sim 0.01$), a stable fountain flow cannot be sustained, and clear differences between the atomic and molecular gas distributions are not expected. For NGC 5506, the Eddington ratio $\lambda_{\rm Edd}=0.05^{\rm +0.21}_{\rm -0.04}$ (cite: Esposito2024) is lower than the value adopted in the simulation ($\lambda_{\rm Edd}=0.2$), and the black hole mass $M_{\rm BH}=2.0^{+8.0}_{-1.6}\times 10^7 M_{\odot}$ (cite: Gofford2015) exceeds that assumed in the simulation ($M_{\rm BH}=2.0\times 10^6 M_{\odot}$). These differences suggest that the fountain flow in NGC 5506 is likely less prominent than in the simulation, and the structural differences predicted by this model may not be detectable in this system.

![](Fig11_v2.pdf)

The high $H/R$ in NGC 5506 is consistent with the SN-driven turbulence model of (cite: Kawakatu2020), which examines the combined effects of SN and AGN feedback. The SN feedback is based on the SMBH–CND coevolution model of (cite: Kawakatu2008). In their model, SN feedback increases the disk scale height, while AGN feedback expels gas and reduces it. (cite: Kawakatu2020) derive the AGN luminosity and black hole mass dependence of the obscuring fraction $f_{\rm obs}$ ($=\cos{\theta_{\rm CND}}$, where $\theta_{\rm CND}$ is the minimum opening angle of the CND), a measure of the disk thickness. As illustrated in Figure [11](#fig:fobs), $f_{\rm obs}$ reaches a maximum at Eddington ratios of $0.01\text{--}0.1$ and black hole masses of $10^{7\text{--}8}~M_\odot$. Within this framework, $f_{\rm obs}$ is estimated to be $\gtrsim0.6$ for NGC 5506, and $\sim0.3$ for the Circinus galaxy. These values ($f_{\rm obs} = 0.3$ and 0.6) correspond to $H/R \approx 0.3$ and $\approx~$0.9, respectively, via the relation $H/R=f_{\rm obs}$/$\sqrt{(1-f_{\rm obs}^2})$. These theoretical predictions are consistent with the values measured in NGC 5506 in this work and in the Circinus galaxy (cite: Izumi2018), indicating that this model can explain the larger scale height of the CND in NGC 5506 relative to the Circinus galaxy.

Furthermore, the SN-driven turbulent velocity predicted by this model is broadly consistent with the velocity dispersion observed in NGC 5506 at a radius of 100 pc. The turbulent velocity ($v_{\rm t}$) is given by $$\begin{equation}
    v_{\rm t}=18~\mathrm{km~s^{-1}}\bigg(\frac{C_\ast}{10^{-8}\mathrm{yr^{-1}}}\bigg)^{1/2}\bigg(\frac{M_{\rm BH}}{10^7M_\odot}\bigg)^{-1/4}\bigg(\frac{r}{30~\mathrm{pc}}\bigg)^{3/4},
\end{equation}$$ where $C_\ast=\mathrm{star\ formation\ rate\ (SFR)}/M_{\rm gas}$ is the star formation efficiency, $M_{\rm BH}$ is the black hole mass, and $r$ is the distance from the black hole (cite: Kawakatu2020). The star formation rate of NGC 5506 is SFR$=0.3^{+0.7}_{-0.2}~M_\odot~\mathrm{yr^{-1}}$, derived from the 11.3 $\mu$m polycyclic aromatic hydrocarbon feature (cite: Ruschel2017), and the molecular gas mass ($M_{\rm gas}$) is  $(4.1\pm 0.6)\times10^{7}~M_\odot$ (Appendix [6](#subsec:coldens)). The predicted turbulent velocity is $v_{\rm t}\sim30~\mathrm{km~s^{-1}}$ at $r\sim100$ pc. This is consistent with the observed velocity dispersion of \[C I\](1–0) and CO(3–2), $V_{\rm disp}=20\text{--}40~\mathrm{km~s^{-1}}$. Because the radial dependence of the velocity dispersion differs between the model and the observation, the agreement between $v_{\rm t}$ and $V_{\rm disp}$ is less robust at radii other than 100 pc. Nevertheless, the order-of-magnitude consistency supports the interpretation that SN-driven turbulence provides the dominant source of vertical support for the CND in NGC 5506. A similar correspondence between observed velocity dispersion and modeled turbulent velocity has been reported for NGC 1275 (cite: Nagai2021).

# Conclusion

We investigated the multiphase gas morphology and kinematics in the circumnuclear region of the nearby Seyfert galaxy, NGC 5506. We used ALMA observations of \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3) at a spatial resolution of $\sim$20 pc and HST observations of \[O III\]$\lambda$5007. The main findings are summarized as follows:

1.  \[C I\](1–0), CO(3–2), and HCO$^{+}$(4–3) trace circumnuclear disk structures on scales of several hundred parsecs, while \[O III\]$\lambda$5007 exhibits a conical morphology. The geometrical thicknesses of \[C I\](1–0) and CO(3–2) are comparable, whereas HCO$^{+}$(4–3) is more concentrated toward the disk plane.

2.  The velocity structures of \[C I\](1–0) and CO(3–2) are similar. Three-dimensional rotating disk modeling with `3D BAROLO` reveals comparable velocity dispersion to rotational velocity ratios ($V_{\rm {disp}}$/$V_{\rm {rot}}$, a proxy for disk scale height-to-radius ratio) for \[C I\](1–0) and CO(3–2), while HCO$^{+}$(4–3) exhibits systematically lower $V_{\rm {disp}}$/$V_{\rm {rot}}$. In the central region ($\lesssim30$ pc), $V_{\rm {disp}}$/$V_{\rm {rot}}$ is high ($\gtrsim0.9$) for both \[C I\](1–0) and CO(3–2), indicating geometrically thick structures. These kinematic results are consistent with the direct comparison of geometrical thickness.

3.  The \[C I\](1–0)/CO(3–2) ratio ($R_{\rm [C~I]/CO}$) is elevated within the AGN-driven biconical ionized outflow traced by \[O III\]$\lambda$5007, with mean values of $0.82\pm0.11$ inside the bicone and $0.47\pm0.07$ outside the bicone. This spatial correlation suggests that CO is preferentially dissociated at the interface where the ionized outflow interacts with the CND.

4.  The observed CND properties are consistent with a scenario in which SN-driven turbulence provides the vertical support for the CND. The relatively low Eddington ratio and high black hole mass of NGC 5506 suggest that a stable radiation-driven fountain flow may not be established. This may explain the absence of significant differences in geometrical thickness between \[C I\](1–0) and CO(3–2). Instead, SN feedback can effectively increase the CND scale height for the black hole mass and luminosity of NGC 5506, consistent with the higher $V_{\rm {disp}}$/$V_{\rm {rot}}$ observed here compared to the Circinus galaxy. The order-of-magnitude agreement between the SN-driven turbulent velocity and the observed velocity dispersion further supports this interpretation.

We thank the anonymous referee for constructive comments that greatly improved this manuscript. K.T. thanks Dai Hirashima for valuable discussions. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00082.S, ADS/JAO.ALMA#2022.1.00410.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research is also based on observations made with the NASA/ESA Hubble Space Telescope obtained from the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., under NASA contract NAS 5–26555. These observations are associated with program 5144. *HST* data analyzed in this paper can be found in MASTat . The Pan-STARRS1 Surveys (PS1) and the PS1 public science archive have been made possible through contributions by the Institute for Astronomy, the University of Hawaii, the Pan-STARRS Project Office, the Max-Planck Society and its participating institutes, the Max Planck Institute for Astronomy, Heidelberg and the Max Planck Institute for Extraterrestrial Physics, Garching, The Johns Hopkins University, Durham University, the University of Edinburgh, the Queen’s University Belfast, the Harvard-Smithsonian Center for Astrophysics, the Las Cumbres Observatory Global Telescope Network Incorporated, the National Central University of Taiwan, the Space Telescope Science Institute, the National Aeronautics and Space Administration under Grant No. NNX08AR22G issued through the Planetary Science Division of the NASA Science Mission Directorate, the National Science Foundation Grant No. AST-1238877, the University of Maryland, Eotvos Lorand University (ELTE), the Los Alamos National Laboratory, and the Gordon and Betty Moore Foundation. ChatGPT was used to assist with English polishing. This work is supported by the JSPS KAKENHI grant Nos. JP19K03918 (N.K.), JP21H04496 (K.W. and T.I.), JP22H00157 (M.K.), and JP24K07091 (M.S.).

# Facilities

ALMA, HST (STIS)

K.T. analyzed the data, produced figures, and wrote and submitted the manuscript. H.N. developed the initial research concept and supervised K.T. M.S. calibrated the HST data. All authors contributed to the scientific discussion.

99

(ref: Antonucci1993) Antonucci, R. 1993, ARA&A, 31, 473. doi:10.1146/annurev.aa.31.090193.002353

(ref: Asmus2016) Asmus, D., Hönig, S. F., & Gandhi, P. 2016, ApJ, 822, 109. doi:10.3847/0004-637X/822/2/109

(ref: Baba2024) Baba, S., Wada, K., Izumi, T., et al. 2024, ApJ, 966, 15. doi:10.3847/1538-4357/ad34d3

(ref: Bertin1996) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393. doi:10.1051/aas:1996164

(ref: Bradley2024) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2024, Zenodo, 1.12.0. doi:10.5281/zenodo.10967176

(ref: Carilli2013) Carilli, C. L. & Walter, F. 2013, ARA&A, 51, 105. doi:10.1146/annurev-astro-082812-140953

(ref: Casa2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501. doi:10.1088/1538-3873/ac9642

(ref: Chambers2016) Chambers, K. C., Magnier, E. A., Metcalfe, N., et al. 2016, arXiv:1612.05560. doi:10.48550/arXiv.1612.05560

(ref: Cid2001) Cid Fernandes, R., Heckman, T., Schmitt, H., et al. 2001, ApJ, 558, 81. doi:10.1086/322449

(ref: Combes2019) Combes, F., Garcı́a-Burillo, S., Audibert, A., et al. 2019, A&A, 623, A79. doi:10.1051/0004-6361/201834560

(ref: Davies2007) Davies, R., Genzel, R., Tacconi, L., et al. 2007, The Central Engine of Active Galactic Nuclei, 373, 639. doi:10.48550/arXiv.astro-ph/0612009

(ref: Davies2015) Davies, R. I., Burtscher, L., Rosario, D., et al. 2015, ApJ, 806, 127. doi:10.1088/0004-637X/806/1/127

(ref: Davies2020) Davies, R., Baron, D., Shimizu, T., et al. 2020, MNRAS, 498, 4150. doi:10.1093/mnras/staa2413

(ref: DiTeodoro&Fraternali2015) Di Teodoro, E. M. & Fraternali, F. 2015, MNRAS, 451, 3021. doi:10.1093/mnras/stv1213

(ref: Downes&Solomon1998) Downes, D. & Solomon, P. M. 1998, ApJ, 507, 615. doi:10.1086/306339

(ref: Elitzur2006b) Elitzur, M. 2006, New A Rev., 50, 728. doi:10.1016/j.newar.2006.06.027

(ref: Esposito2024) Esposito, F., Alonso-Herrero, A., Garcı́a-Burillo, S., et al. 2024, A&A, 686, A46. doi:10.1051/0004-6361/202449245

(ref: Fischer2013) Fischer, T. C., Crenshaw, D. M., Kraemer, S. B., et al. 2013, ApJS, 209, 1. doi:10.1088/0067-0049/209/1/1

(ref: Garcia2021) Garcı́a-Burillo, S., Alonso-Herrero, A., Ramos Almeida, C., et al. 2021, A&A, 652, A98. doi:10.1051/0004-6361/202141075

(ref: Gofford2013) Gofford, J., Reeves, J. N., Tombesi, F., et al. 2013, MNRAS, 430, 60. doi:10.1093/mnras/sts481

(ref: Gofford2015) Gofford, J., Reeves, J. N., McLaughlin, D. E., et al. 2015, MNRAS, 451, 4169. doi:10.1093/mnras/stv1207

(ref: Gonzalez2001) González Delgado, R. M., Heckman, T., & Leitherer, C. 2001, ApJ, 546, 845. doi:10.1086/318295

(ref: Greve2009) Greve, T. R., Papadopoulos, P. P., Gao, Y., et al. 2009, ApJ, 692, 1432. doi:10.1088/0004-637X/692/2/1432

(ref: Heckman1997) Heckman, T. M., González-Delgado, R., Leitherer, C., et al. 1997, ApJ, 482, 114. doi:10.1086/304139

(ref: Honig2006) Hönig, S. F., Beckert, T., Ohnaka, K., et al. 2006, A&A, 452, 459. doi:10.1051/0004-6361:20054622

(ref: Hicks2009) Hicks, E. K. S., Davies, R. I., Malkan, M. A., et al. 2009, ApJ, 696, 1, 448. doi:10.1088/0004-637X/696/1/448

(ref: Imanishi2018) Imanishi, M., Nakanishi, K., Izumi, T., et al. 2018, ApJL, 853, L25. doi:10.3847/2041-8213/aaa8df

(ref: Izumi2018) Izumi, T., Wada, K., Fukushige, R., et al. 2018, ApJ, 867, 48. doi:10.3847/1538-4357/aae20b

(ref: Izumi2023) Izumi, T., Wada, K., Imanishi, M., et al. 2023, Science, 382, 554. doi:10.1126/science.adf0569

(ref: Kabasares2022) Kabasares, K. M., Barth, A. J., Buote, D. A., et al. 2022, ApJ, 934, 162. doi:10.3847/1538-4357/ac7a38

(ref: Karachensev2014) Karachentsev, I. D., Karachentseva, V. E., & Nasonova, O. G. 2014, Astrophysics, 57, 457. doi:10.1007/s10511-014-9349-2

(ref: Kawakatu2008) Kawakatu, N. & Wada, K. 2008, ApJ, 681, 73. doi:10.1086/588574

(ref: Kawakatu2020) Kawakatu, N., Wada, K., & Ichikawa, K. 2020, ApJ, 889, 84. doi:10.3847/1538-4357/ab5f60

(ref: Kinney2000) Kinney, A. L., Schmitt, H. R., Clarke, C. J., et al. 2000, ApJ, 537, 152. doi:10.1086/309016

(ref: Kormendy2013) Kormendy, J. & Ho, L. C. 2013, ARA&A, 51, 511. doi:10.1146/annurev-astro-082708-101811

(ref: Krolik2007) Krolik, J. H. 2007, ApJ, 661, 52. doi:10.1086/515432

(ref: Lawrence2010) Lawrence, A. & Elvis, M. 2010, ApJ, 714, 561. doi:10.1088/0004-637X/714/1/561

(ref: Levenson2009) Levenson, N. A., Radomski, J. T., Packham, C., et al. 2009, ApJ, 703, 390. doi:10.1088/0004-637X/703/1/390

(ref: Liu2023) Liu, D., Schinnerer, E., Saito, T., et al. 2023, A&A, 672, A36. doi:10.1051/0004-6361/202244564

(ref: Maiolino1995) Maiolino, R. & Rieke, G. H. 1995, ApJ, 454, 95. doi:10.1086/176468

(ref: Merloni2014) Merloni, A., Bongiorno, A., Brusa, M., et al. 2014, MNRAS, 437, 3550. doi:10.1093/mnras/stt2149

(ref: Nagai2021) Nagai, H. & Kawakatu, N. 2021, ApJL, 914, L11. doi:10.3847/2041-8213/ac03ba

(ref: Nagar2002) Nagar, N. M., Oliva, E., Marconi, A., et al. 2002, A&A, 391, L21. doi:10.1051/0004-6361:20021039

(ref: Nenkova2002) Nenkova, M., Ivezić, Ž., & Elitzur, M. 2002, ApJL, 570, L9. doi:10.1086/340857

(ref: Nenkova2008a) Nenkova, M., Sirocky, M. M., Ivezić, Ž., et al. 2008, ApJ, 685, 147. doi:10.1086/590482

(ref: Nenkova2008b) Nenkova, M., Sirocky, M. M., Nikutta, R., et al. 2008, ApJ, 685, 160. doi:10.1086/590483

(ref: Nikolajuk2009) Nikołajuk, M., Czerny, B., & Gurynowicz, P. 2009, MNRAS, 394, 2141. doi:10.1111/j.1365-2966.2009.14478.x

(ref: Nota1996) Nota, A. et al. 1996, .

(ref: Ohsuga1999) Ohsuga, K. & Umemura, M. 1999, ApJL, 521, L13. doi:10.1086/312181

(ref: Ohsuga2001) Ohsuga, K. & Umemura, M. 2001, ApJ, 559, 157. doi:10.1086/322398

(ref: Osterbrock2006) Osterbrock, D. E. & Ferland, G. J. 2006, Astrophysics of gaseous nebulae and active galactic nuclei, 2nd. ed. by D.E. Osterbrock and G.J. Ferland. Sausalito, CA: University Science Books, 2006

(ref: Papadakis2004) Papadakis, I. E. 2004, MNRAS, 348, 207. doi:10.1111/j.1365-2966.2004.07351.x

(ref: Pier1992) Pier, E. A. & Krolik, J. H. 1992, ApJ, 401, 99. doi:10.1086/172042

(ref: Pier1993) Pier, E. A. & Krolik, J. H. 1993, ApJ, 418, 673. doi:10.1086/173427

(ref: Planck2020) Planck Collaboration, Aghanim, N., Akrami, Y., et al. 2020, A&A, 641, A6. doi:10.1051/0004-6361/201833910

(ref: Roy2000) Roy, A. L., Ulvestad, J. S., Wilson, A. S., et al. 2000, Perspectives on Radio Astronomy: Science with Large Antenna Arrays, 173. doi:10.48550/arXiv.astro-ph/9909105

(ref: Roy2001) Roy, A. L., Wrobel, J. M., Wilson, A. S., et al. 2001, Galaxies and their Constituents at the Highest Angular Resolutions, 205, 70. doi:10.48550/arXiv.astro-ph/0012159

(ref: Ruiz2005) Ruiz, J. R., Crenshaw, D. M., Kraemer, S. B., et al. 2005, AJ, 129, 73. doi:10.1086/426372

(ref: Ruschel2017) Ruschel-Dutra, D., Rodrı́guez Espinosa, J. M., González Martı́n, O., et al. 2017, MNRAS, 466, 3353. doi:10.1093/mnras/stw3276

(ref: Saito2022) Saito, T., Takano, S., Harada, N., et al. 2022, ApJL, 927, L32. doi:10.3847/2041-8213/ac59ae

(ref: Sani2012) Sani, E., Davies, R. I., Sternberg, A., et al. 2012, MNRAS, 424, 3, 1963. doi:10.1111/j.1365-2966.2012.21333.x

(ref: Schartmann2008) Schartmann, M., Meisenheimer, K., Camenzind, M., et al. 2008, A&A, 482, 67. doi:10.1051/0004-6361:20078907

(ref: Schartmann2009) Schartmann, M., Meisenheimer, K., Klahr, H., et al. 2009, MNRAS, 393, 759. doi:10.1111/j.1365-2966.2008.14220.x

(ref: Schartmann2014) Schartmann, M., Wada, K., Prieto, M. A., et al. 2014, MNRAS, 445, 3878. doi:10.1093/mnras/stu2020

(ref: Shi2008) Shi, J. & Krolik, J. H. 2008, ApJ, 679, 1018. doi:10.1086/587507

(ref: Solomon&Bout2015) Solomon, P. M. & Vanden Bout, P. A. 2005, ARA&A, 43, 677. doi:10.1146/annurev.astro.43.051804.102221

(ref: Tanimoto2023) Tanimoto, A., Wada, K., Kudoh, Y., et al. 2023, ApJ, 958, 150. doi:10.3847/1538-4357/ad06ac

(ref: Trippe2010) Trippe, M. L., Crenshaw, D. M., Deo, R. P., et al. 2010, ApJ, 725, 1749. doi:10.1088/0004-637X/725/2/1749

(ref: Tristram2014) Tristram, K. R. W., Burtscher, L., Jaffe, W., et al. 2014, A&A, 563, A82. doi:10.1051/0004-6361/201322698

(ref: Urry1995) Urry, C. M. & Padovani, P. 1995, PASP, 107, 803. doi:10.1086/133630

(ref: Uzuo2021) Uzuo, T., Wada, K., Izumi, T., et al. 2021, ApJ, 915, 89. doi:10.3847/1538-4357/ac013d

(ref: Wada2002) Wada, K. & Norman, C. A. 2002, ApJL, 566, L21. doi:10.1086/339438

(ref: Wada2012) Wada, K. 2012, ApJ, 758, 66. doi:10.1088/0004-637X/758/1/66

(ref: Wada2015) Wada, K. 2015, ApJ, 812, 82. doi:10.1088/0004-637X/812/1/82

(ref: Wada2016) Wada, K., Schartmann, M., & Meijerink, R. 2016, ApJL, 828, L19. doi:10.3847/2041-8205/828/2/L19

(ref: Wada2018a) Wada, K., Fukushige, R., Izumi, T., et al. 2018, ApJ, 852, 88. doi:10.3847/1538-4357/aa9e53

(ref: Wada2018b) Wada, K., Yonekura, K., & Nagao, T. 2018, ApJ, 867, 49. doi:10.3847/1538-4357/aae204

(ref: Zhang2024) Zhang, L., Packham, C., Hicks, E. K. S., et al. 2024, ApJ, 974, 2, 195. doi:10.3847/1538-4357/ad6a4b

# Molecular Gas Mass and Column Density

The H$_2$ gas mass and column density are derived from the moment 0 map of CO(3–2), following (cite: Izumi2018). The CO(3–2) line luminosity $L^\prime_{\rm CO(3-2)}$ is given by $$\begin{equation}
    L^\prime_{\rm CO(3-2)}=3.25\times10^7S_{\rm CO(3-2)}\Delta v~\nu^{-2}_{\rm obs}D_{\rm L}^2(1+z)^{-3},
    \label{eq:solomon}
\end{equation}$$ where $S_{\rm CO(3-2)}\Delta v$ is the velocity-integrated flux density in Jy km s$^{-1}$, $\nu_{\rm obs}$ is the observed frequency in GHz, $D_{\rm L}$ is the luminosity distance in Mpc, and $z$ is the redshift (cite: Solomon&Bout2015). Assuming CO(3–2) emission is thermalized with that of CO(2–1) (cite: Solomon&Bout2015), we adopt the canonical CO-to-H$_2$ conversion factor for active environments $M_{\rm H_{2}} / L^{\prime}_{\rm CO} = 0.8 M_{\odot}$ (K km s$^{-1}$ pc$^2$)$^{-1}$ (cite: Downes&Solomon1998). The resulting total molecular hydrogen mass is $M_{\rm H_2}=(4.1\pm 0.6)\times10^7$ $M_\odot$, and the mean column density is $N_{H_2}=(4.3 \pm 0.6)\times10^{22}$ cm$^{-2}$.

[^1]: Figure 2 of (cite: Baba2024) shows that simulations based on the radiation-driven fountain model at $i=80^{\circ}$ predict \[C I\] to be geometrically thicker than CO and HCO$^{+}$. If NGC 5506 ($i=79^{\circ}$) has a similar structure, differences in geometrical thickness among the multiphase gas components are expected to be observable.

</paper>

Write the methods card for this paper.