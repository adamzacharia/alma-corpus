# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...646A..72H\sonnetcc\reply.txt

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
 "bibcode": "2021A&A...646A..72H",
 "title": "Resolved molecular line observations reveal an inherited molecular layer in the young disk around TMC1A",
 "year": 2021,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Harsono, D.",
 "n_authors": 7,
 "arxiv_id": "2010.13722",
 "doi": "10.1051/0004-6361/202038697",
 "alma_projects_linked_by_archive": [
  "2015.1.01549.S",
  "2016.1.00711.S",
  "2017.1.00212.S"
 ]
}
```

Paper text:
<paper>
# Resolved molecular line observations reveal an inherited molecular layer in the young disk around TMC1A

Physical processes that govern the star and planet formation sequence influence the chemical composition and evolution of protoplanetary disks. Recent studies allude to an early start to planet formation already during the formation of a disk. To understand the chemical composition of protoplanets, we need to constrain the composition and structure of the disks from whence they are formed.

We aim to determine the molecular abundance structure of the young disk around the TMC1A protostar on au scales in order to understand its chemical structure and any possible implications for disk formation.

We present spatially resolved Atacama Large Millimeter/submillimeter Array observations of CO, HCO$^{+}$, HCN, DCN, and SO line emission, as well as dust continuum emission, in the vicinity of TMC1A. Molecular column densities are estimated both under the assumption of optically thin emission from molecules in local thermodynamical equilibrium (LTE) as well as through more detailed non-LTE radiative transfer calculations.

Resolved dust continuum emission from the disk is detected between 220 and 260 GHz. Rotational transitions from , , and are also detected from the inner 100 au region. We further report on upper limits to vibrational HCN $\upsilon_2 = 1$, DCN, and lines. The emission appears to trace both the Keplerian disk and the surrounding infalling rotating envelope. HCN emission peaks toward the outflow cavity region connected with the CO disk wind and toward the red-shifted part of the Keplerian disk. From the derived abundance, we estimate the ionization fraction of the disk surface, and find values that imply that the accretion process is not driven by the magneto-rotational instability. The molecular abundances averaged over the TMC1A disk are similar to its protostellar envelope and other, older Class II disks. We meanwhile find a discrepancy between the young disk’s molecular abundances relative to Solar System objects.

Abundance comparisons between the disk and its surrounding envelope for several molecular species reveal that the bulk of planet-forming material enters the disk unaltered. Differences in and molecular abundances between the disk around TMC1A, Class II disks, and Solar System objects trace the chemical evolution during disk and planet formation.

# Introduction

The properties of newborn planets will likely reflect the environment in which they formed. Thus, knowing the physical and chemical structure of protoplanetary disks is absolutely necessary in order to understand the process of planet formation. Evidence for on-going planet formation has been captured by recent high-spatial resolution millimeter and high-contrast IR observations that reveal gaps, rings, and spiral dust substructures in protoplanetary disks (cite: hltau2014; lperez16sci; flong18; huang18). The immediate emerging paradigm is that planet formation starts early during the embedded stage of star formation (cite: harsono18). This is supported by cosmochemical measurements of calcium aluminium inclusions and chondrules that are found in chondritic meteorites formed in the early Solar System (cite: connelly12; bollard2017; jacquet19; haugbolle2019). A spatially resolved molecular studies of a young disk can reveal the environment of the early stages of planet formation.

Understanding the physical and chemical structure of planet-forming disks relies on both high-spatial resolution and spectrally resolved observations. From dust continuum observations, the physical structure of Class II disks have been constructed and compared to theoretical studies of disk evolution (cite: wc11; manara17; tazzari17; manara19b). Once a physical structure is determined, the chemical structure can be studied and compared with evolutionary models coupled to chemistry (cite: dutrey97; zadelhoff01; aikawa03; ceccarelli05; pietu07; bergin10; bruderer12; chapillon12; vandermarel14; loomis15; guzman15; fedele16; salinas16; kama16; mcclure16; oberg17; carney18). Meanwhile, on-going planet formation can also affect the strength of molecular line emission, as suggested by a decreasing / mid-IR line flux ratio with decreasing disk mass observed toward Class II disks (cite: najita13). However, similar studies towards embedded, young stellar objects are still difficult.

Detailed studies of the physical and chemical structure of young, embedded disks are hindered by the surrounding, obscuring protostellar envelope. In addition, since the chemical evolutionary timescale in the disk is typically longer than the envelope infall timescale, the final chemical structure of the disk also depends on the physical and chemical evolution of the protostellar envelope (cite: bergin97; aikawa99; visser09; hincelin13; yoneda16). In this regard, chemical studies with single-dish telescopes have been instrumental in determining the bulk chemical structure of large-scale envelopes around low-mass stars (cite: blake95; vandishoeck98; jorgensen04c; graninger16) down to the scales of a few hundred au with millimeter interferometers such as the Submillimeter Array and IRAM NOrthern Extended Millimeter Array (cite: jorgensen05b; prosac07; bisschop08; maury14; taquet15). With the Atacama Large Millimeter/submillimeter Array, it is now possible to spatially and spectrally resolve the molecular emission to isolate the Keplerian disk from the surrounding envelope (cite: sakai14; delavillarmois18; delavillarmois19b). This aspect makes it possible to explore the chemical structure of young disks and examine the early stages of planet formation.

Many inferred chemical compositions demonstrate a link between Solar System comets and young stellar objects, while others indicate differences since formation (cite: schoier02; visser09; pontoppidan14; persson14; garrod19). For example, the most recent comparison between the young stellar object IRAS 16293–2422 and comet 67P/Churyumov–Gerasimenko shows a correlation in the CHO-, N- and S-bearing molecules (cite: drozdovskaya19). Meanwhile molecular species such as , , and are elevated compared to comets, which indicates some degree of processing. Further evidence for a direct link between the birth environment of a planet and the initial structure of the proto-Solar disk can be found in the elemental enhancement of Jupiter’s atmosphere with respect to solar (cite: owen99; asplund09; oberg19; bosman19). It is therefore crucial to understand the chemistry and variation of molecular abundances during the early stages of disk evolution to be able to draw conclusions about the details of planetary composition.

In the classical theory of a disk (cite: lodato08; armitage11), a protoplanetary disk is characterized by its Keplerian motion. Hence, molecular emission from rotationally supported object will more likely trace the chemical structure of an early disk. A few young stellar objects show a clear sign of an embedded Keplerian disk (cite: prosac09; harsono14; yen17; delavillarmois19a). Only a handful of these targets are less embedded and at a favorable orientation such that there is a direct line-of-sight to the disk through the tenuous envelope. One of those targets is TMC1A (IRAS 04365+2535) with $i \sim 60^{\circ}$ and a $\sim$0.1 $M_{\odot}$ envelope, which makes it a “Stage I” embedded young stellar object (cite: robitaille06; kristensen12). A “Stage I” system refers to a protostellar object with an envelope mass that is similar to its protostellar mass. High-spatial resolution observations of , , and  demonstrate a clear distinction between outflowing gas (cite: bjerkeli2016), the Keplerian disk, and the large-scale envelope (cite: harsono18). The relatively simple geometry of TMC1A with its well-defined disk, makes it an ideal laboratory for determining the distribution and abundances of common, simple molecules on scales of $\sim 15$ au. This paper presents such an analysis and compares the inferred chemistry to that of the Solar System as well as more evolved young stellar objects. Thereby it also helps shedding light on which molecules can serve as fingerprints of disk formation and evolution.

This paper presents the detection of simple molecules in the young disk around TMC1A. By determining their molecular column densities, we constrain the molecular abundance structure of its Keplerian disk with respect to . The paper outline is as follows. Section [2](#sec:obsdetails) presents the observational details. Dust continuum emission and the detected molecular lines are presented in Sect. [3](#sec:obsresults). HCN and DCN lines are analyzed further using the  spectral cube as a proxy mask. In Sect. [4](#sec:colden_excitation), optically thin, thermalized molecular emission and non-LTE radiative transfer calculations are been used to determine the molecular column densities and their excitation conditions. Using these column densities, we estimate the molecular abundances and temperature structure of the young disk around TMC1A. By utilizing a reduced chemical network, the ionization fraction of the disk is approximated in order to understand the physical processes that drive its accretion. The derived abundances are compared with the protostellar envelope, Class II protoplanetary disks, and Solar System objects in Sect. [5](#sec:molecularlayer). Finally, the summary and conclusions can be found in Sect. [6](#sec:summaryconclude).

+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Date         | Bandpass   | Phase      | Flux       | Bl. coverage (km) | $N_{\rm ant.}$ | PWV (mm) | WVR corr. $^{a}$ |
+:============:+:==========:+:==========:+:==========:+:=================:+:==============:+:========:+:================:+
| 2015.1.01549.S                                                                                                         |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Oct 16, 2015 | J0510+1800 | J0440+2728 | J0433+2905 | 0.04 – 16.2       | 42             | 1.8      | Yes              |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Oct 23, 2015 | J0510+1800 | J0440+2728 | J0433+2905 | 0.04 – 16.2       | 40             | 0.6      | Yes              |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Oct 30, 2015 | J0510+1800 | J0440+2728 | J0433+2905 | 0.04 – 16.2       | 40             | 0.3      | Yes              |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| 2016.1.00711.S                                                                                                         |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Sep 22, 2017 | J0510+1800 | J0438+3004 | J0510+1800 | 0.04 – 12.1       | 42             | 0.7      | No               |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Sep 23, 2017 | J0510+1800 | J0438+3004 | J0510+1800 | 0.04 – 12.1       | 40             | 0.4      | No               |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| 2017.1.00212.S                                                                                                         |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+
| Oct 19, 2017 | J0510+1800 | J0438+3004 | J0510+1800 | 0.04 – 16.2       | 51             | 1.1      | No               |
+--------------+------------+------------+------------+-------------------+----------------+----------+------------------+

Table notes:

# Observations

TMC1A was observed during long baselines campaigns (LBC, 16 km) of the Atacama Large Millimeter/submillimeter Array (ALMA) on three occasions. We have concatenated three LBC projects: 2015.1.01549.S (PI: van der Wiel), 2016.1.00711.S (PI: van der Wiel), and 2017.1.00212.S (PI: Bjerkeli). The first data set (2015.1.01549.S, tuned to frequencies of CO and its isotopologs) was published in (cite: bjerkeli2016) and (cite: harsono18). We also use water ( $3_{1,3} - 2_{2,0}$ at 203 GHz) observations taken with the NOrthern Extended Millimeter Array (NOEMA), and which are presented in (cite: harsono20). Here, we present observational details of the second (2016.1.00711.S, Sect. [2.1](#sub:obs_hcn)) and third (2017.1.00212.S, Sect. [2.2](#sub:obs_continuum)) ALMA data sets, while we refer to (cite: harsono18; harsono20) for details on the imaging and calibration of the first ALMA data set and the NOEMA data, respectively. Table [\[tbl:obsdetails\]](#tbl:obsdetails) lists the observational details of the ALMA programs used in this paper.

## ALMA observations: 2016.1.00711.S

ALMA observed TMC1A on September 22 and 23 in 2017. The observations were taken with $\sim$40 antennas under very good weather conditions with a precipitable water vapor (PWV) of 0.35 mm. The baseline coverage was between 40 m and 12 km, which translates to 30 k$\lambda$ up to 10$^{4}$ k$\lambda$. The bandpass, phase, and flux calibrators are indicated in Table [\[tbl:obsdetails\]](#tbl:obsdetails). Four spectral windows were utilized in this program. Three narrow high resolution windows were centered on HCN $J=3-2$ (265.8861800 GHz), HCO$^{+}$ $J=3-2$ (267.8527094 GHz), and SO $N_{J} = 5_6 - 4_5$ (251.82577000 GHz), respectively. A wide spectral window (1.8 GHz) was centered at 253.2 GHz to measure the dust continuum. Rest line frequencies are obtained from the JPL (cite: JPLdb) and CDMS catalogs (cite: cdms1; cdms2). The data were calibrated using the Cycle 4 pipeline of CASA 4.7.2 (cite: CASA).

## ALMA observations: 2017.1.00212.S

This ALMA project was executed on October 19 2017. The observations were taken with $\sim$51 antennas. The baseline coverage was between 40 m and 16.2 km, which translates to 30 k$\lambda$ to $10^{4}$ k$\lambda$. The bandpass, phase, and flux calibrators are also indicated in Table [\[tbl:obsdetails\]](#tbl:obsdetails). Four broadband continuum spectral windows (1.8 GHz) were used in this program. Molecular lines are not clearly detected because of the low spectral resolution. The data was calibrated using the Cycle 5 pipeline of CASA 5.1.1.

## Self-calibration and combined ALMA data

|  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | Frequency | $E_{\rm up}$ | $\log_{10} A_{\rm ul}$ | Beam$^{a}$ | Noise | Int. time | Integrated flux density |
|  | (GHz) | \(K\) | (s$^{-1}$) | ($'' \times '', ^{\circ}$) | (mJy bm$^{-1}$) | (min.) | (mJy / mJy km s$^{-1}$) |
| NOEMA Continuum | 203 | ... | ... | $0.78 \times 0.72, 62$ | 1.1 | 180 | $210\pm20$ |
| NOEMA Continuum | 220 | ... | ... | $0.79 \times 0.61, 54$ | 1.2 | 180 | $170 \pm 17$ |
| ALMA Continuum | 220 | ... | ... | $0.031\times 0.020, -3$ | 0.08 | 170 | $220 \pm 22$ |
| ALMA Continuum | 230 | ... | ... | $0.032\times 0.021, 1$ | 0.05 | 111 | $240 \pm 24$ |
| ALMA Continuum | 240 | ... | ... | $0.028\times 0.018, 0$ | 0.08 | 90 | $280 \pm 28$ |
| ALMA Continuum | 260 | ... | ... | $0.049\times 0.032, 11$ | 0.05 | 63 | $190 \pm 19$ |
|  $3_{1,3} - 2_{2,0}$ | 203.4075 | 203.7 | $-5.32$ | $0.78 \times 0.72$, 59 | 8 | 180 | $< 11$ |
| 3–2 | 217.2385 | 20.85 | $-3.34$ | $0.13 \times 0.10$, 32 | 1.5 | 91 | $< 8$ |
| 2–1 | 219.5604 | 15.80 | $-6.22$ | $0.13 \times 0.10$, 31 | 1.8 | 91 | $330 \pm 33$ |
| 2–1 | 220.3987 | 15.87 | $-6.22$ | $0.13 \times 0.10$, 32 | 2.4 | 85 | $290 \pm 30$ |
| 2–1 | 230.5380 | 16.60 | $-6.16$ | $0.12 \times 0.10$, 0.5 | 2.5 | 83 | $1740 \pm 174$ |
| $J = 3 -2$ | 231.3216 | 22.20 | $-2.67$ | $0.12 \times 0.10$, 32 | 0.8 | 91 | $100 \pm 22$ |
| $N=6_{5}-5_{4}$ | 251.8258 | 50.66 | $-3.71$ | $0.13 \times 0.11$, 0.1 | 1.0 | 71 | $460 \pm 46$ |
| $v_2 = 1$ $J=3-2e$ | 265.8527 | 1050 | $-2.64$ | $0.092 \times 0.07$, 0.4 | 0.9 | 71 | $< 20$ |
| $3-2$ | 265.8862 | 25.52 | $-3.55$ | $0.12 \times 0.10$, 0.1 | 1.3 | 71 | $160 \pm 20$ |
| $v_2 = 1$ $J=3-2f$ | 267.1993 | 1050 | $-2.63$ | $0.092 \times 0.07$, 20 | 0.9 | 71 | $< 20$ |
| $J=3-2$ | 267.5576 | 25.68 | $-2.84$ | $0.12 \times 0.11$, 3.5 | 1.2 | 71 | $640 \pm 64$ |

Table notes:

We combined these ALMA projects into a single measurement set using the CASA task CONCAT to improve the $S/N$ of the dust continuum model. The concatenated data allows for simultaneous phase and amplitude self-calibrations to produce better flux calibration across the three data sets. This self-calibration is based on the line-free channels in each spectral window, and was performed with CASA 5.4.1. We fixed the phase center of each measurement to the value obtained in (cite: harsono18) utilizing the data with the most stable weather conditions. The phase center of J2000 04h39m35.203s +25d41m44.21s is determined by fitting an elliptical Gaussian to the continuum visibilities with CASA task UVFIT. The phase solutions obtained from the broadband windows are applied across the narrow spectral windows. The imaging of the continuum is performed with TCLEAN using Briggs weighting (cite: briggs95) to minimize the side lobes. Spectral windows containing the targeted molecular lines are continuum subtracted in the (u,v) plane with the task UVCONTSUB.

The targeted molecular lines are listed in Table [\[tbl:imgs\]](#tbl:imgs) along with the noise level per spectral resolution element. The spectral lines are imaged at 0.3 km s$^{-1}$ velocity resolution including a spatial tapering at 0.08$''$, resulting in the synthesized beam sizes indicated in Table [\[tbl:imgs\]](#tbl:imgs). Appendix [7](#app:undetected) lists a few molecular lines that were present in our spectral set up, but not detected in our data sets.

# Observational results

![](aa38697_fig1.pdf)

## Spatially resolved dust continuum

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| Name | Size | $i$ | $PA$ | Offset | Flux density |
|  | ($''$) | ($^{\circ}$) | ($^{\circ}$) | ($''$,$''$) | (mJy) |
| NOEMA 203 | ... | ... | ... | ... | ... |
| NOEMA 220 | $0.2 \pm 0.1$ | $45^{+26}_{-30}$ | $80^{+60}_{-50}$ | 0,-0.13 | $250^{+2100}_{-220}$ |
| ALMA 220 | $0.1 \pm 0.01$ | $52\pm 3$ | $76\pm 5$ | 0.01,-0.02 | $300^{+18}_{-16}$ |
| ALMA 230 | $0.1 \pm 0.01$ | $51\pm 3$ | $75\pm 3$ | 0.01,0.001 | $310^{+12}_{-11}$ |
| ALMA 240 | $0.1 \pm 0.01$ | $49 \pm 3$ | $76 \pm 3$ | 0.01,-0.02 | $350^{+13}_{-12}$ |
| ALMA 260 | $0.1 \pm 0.01$ | $49 \pm 3$ | $76 \pm 6$ | 0.004,-0.02 | $302^{+17}_{-16}$ |

: Best-fit parameters for the Gaussian intensity profile model. The stated uncertainties are the 1$\sigma$ deviation from the mean of the last 1000 steps of the MCMC fit with walkers whose acceptance fraction is $>$ 20% (see text).

The continuum images of TMC1A between 203 and 260 GHz from the NOEMA and ALMA observations are shown in Fig. [1](#fig:contimages). The NOEMA observation does not spatially resolve the disk, which is evidenced by the lack of elongation present in the ALMA images. However, the deconvolved size ($0.56\ensuremath{''}\times 0.44\ensuremath{''}$), as determined by fitting an elliptical Gaussian to the observed visibilities, indicates that the dust continuum is mostly tracing the Keplerian disk ($\sim\, 100$ au, (cite: harsono14)). The peak intensities of the different continuum images are 93 mJy beam$^{-1}$ at 203 GHz, 5.1 mJy beam$^{-1}$ at 242 GHz, 5 mJy beam$^{-1}$ at 240 GHz, and 9.8 mJy beam$^{-1}$ at 260 GHz.

![](aa38697_fig2.pdf)

Continuum visibilities at various frequencies are shown in Fig. [2](#fig:contdata) including the Sub-millimeter Array (SMA) data from (cite: prosac09) and NOEMA data from (cite: harsono14). The binned SMA data are scaled to 1.3 mm using a frequency dependence of $S_{\nu} \propto \nu^{2.5}$. The phase as a function of projected baselines is close to zero for the ALMA observations, indicating the high data quality. The large standard deviation in the NOEMA data reflects the lower number of (u,v) points relative to the ALMA data. From the comparison between the integrated flux density of the NOEMA and ALMA data at 220 GHz, the uncertainty in the absolute flux density is within 10%. It is interesting to note that the amplitude of the 260 GHz observations is lower than the values at 220 GHz at short baselines ($< 1000 \ {\rm k} \lambda$) while the opposite is true at long baselines ($> 1000 \ {\rm k} \lambda$). The peak intensity of the dust continuum image at 260 GHz is indeed higher than the peak at the lower frequencies. However, as indicated in Table [\[tbl:imgs\]](#tbl:imgs), the integrated continuum flux density at 260 GHz is lower than at 203 GHz in the image plane. The lower flux density at 260 GHz may indicate resolved-out continuum emission at the higher frequency.

To characterize the dust disk, we utilize GALARIO (cite: galario); GALARIO calculates the synthetic (u,v) visibilities given an intensity profile and makes it possible to fit Gaussian intensity profiles to the observed visibilities while simultaneously constraining the flux density and the deconvolved size. The free parameters are the peak intensity $I$ in Jy sr$^{-1}$, size of the emitting region, inclination $i$, position angle $PA$, and position offset. The Markov Chain Monte Carlo (MCMC) Python package EMCEE (cite: emcee) is used to efficiently explore a wide range of parameters. At each observed frequency, a first run is performed with 60 walkers ($10 \times$ free parameters) and 1000 steps. Each walker explores the parameter space by gradually stepping into a region with the lowest $\chi^2$. The best-fit values are obtained by calculating the mean of the last 100 steps of all walkers. Then, a second run is performed with 120 walkers initialized by uniformly distributing them around the best-fit values obtained from the first run. This second run is performed with 10000 steps to obtain the final set of best-fit parameters. The best-fit values are determined statistically taking the mean of the last 1000 steps of the walkers with acceptance ratios greater than 20%. These best-fit values and their $1\sigma$ errors are listed in Table [1](#tbl:fitdust).

The MCMC modelling of this high-fidelity data allow us to accurately determine that the TMC1A protostellar system is inclined at 50$^{\circ} \pm 3$ with a position angle of 75$^{\circ}\pm 4$. The size of the dust disk is of the order of $0.1\ensuremath{''}$ ($FWHM = 0.23\ensuremath{''}$ or 30 au at 140 pc). The deconvolved dust disk size determined from the high angular resolution ALMA data is smaller than the 100 au radius gaseous Keplerian disk (cite: harsono14). Most of the dust continuum flux density is emitted from the region probed by our ALMA data since the difference between the flux density obtained by ALMA and NOEMA data is small ($<20\%$) at 220 GHz.

## Molecular gas observations

![](aa38697_fig3.pdf)

![](aa38697_fig4.pdf)

![](aa38697_fig5.pdf)

In Fig. [3](#fig:rotspectra), we present spectra of the targeted molecular lines integrated over a 1$\ensuremath{''}$ box centered on TMC1A. Out of the many targeted molecular lines ( $2-1$,  $2-1$,  $2-1$, DCN $3-2$, $3-2$, HCN $3-2$, HCO$^{+}$ $3-2$, SO $5_6 - 4_5$, p- 3$_{1,3}-2_{2,0}$, and Appendix  [7](#app:undetected)), only a few are strongly detected in emission. While can be identified spectrally, its emission cannot be imaged with the current baselines coverage, suggesting that it is present in the diffuse large-scale envelope (cite: crapsi05a; tobin13). The channel maps and zeroth moment maps of the strong lines are shown in Figs. [4](#fig:chanmaps) and [5](#fig:mom0maps).

In the inner 1$\ensuremath{''}$ square aperture,  line emission is the strongest with a peak of 0.5 Jy. The peak line flux densities of , , and SO are similar with a maximum of $\sim 0.1$ Jy. The weaker lines are  and HCN. The integrated flux densities are listed in Table [\[tbl:imgs\]](#tbl:imgs) including the upper limits for a few molecular lines of interest. The tabulated integrated flux densities are calculated considering pixels whose intensities $> 3 \sigma$ over the entire image. The upper limits are calculated using a spatial mask ($x,y$) over the dust continuum emission following the methods outlined in (cite: carney19) assuming a Gaussian linewidth of 1 km s$^{-1}$ (see (cite: harsono20)). We also report upper limits to the rotational transitions in the vibrational bending mode of HCN ($v_2 = 1$). Their spectra are shown in Appendix [8](#app:vibrational). The bending mode of HCN should be detectable toward the inner regions of protoplanetary disks in order to constrain the structure of the inner hot disk (cite: bruderer15). The non-detection of these hot HCN lines limits the existence of hot gas to the inner 10 au of TMC1A.

The spectral line profile of  $2-1$ is symmetric about the systemic velocity as would be expected from a rotating structure. A similar line profile is seen for  $2-1$, while the  $2-1$ line shows a stronger blue-shifted emission reflecting the presence of the extended disk wind (cite: bjerkeli2016). The , SO, and HCN molecular lines exhibit narrow line profiles between $2 - 12$ km s$^{-1}$ similar to  and . The $J=3-2$ line has 6 hyperfine components (cite: mullins16) that could be responsible for the narrow absorption features (1-2 channels wide) seen in the spectrum at velocities significantly offset from systemic. Despite the weak HCN line profile, the channel maps in Fig. [4](#fig:chanmaps) clearly indicate that its emission is detected in multiple channels.

![](aa38697_fig6.pdf)

![](aa38697_fig7.pdf)

The channel maps in Fig. [4](#fig:chanmaps) show that most of these molecular lines are detected in the vicinity of the millimeter dust continuum continuum emission. , , , and  show strong molecular emission from $1-12$ km s$^{-1}$ while both HCN and SO are detected between $2.5 - 10$ km s$^{-1}$. The  and  show emissions that are co-spatial. The channel maps also show extended arc features in both  and HCN lines that are due to filtered-out emission (Tychoniec et al. in prep.). The zeroth moment maps (Fig. [5](#fig:mom0maps)) show clearly these arcs. The observed molecular lines avoid the central 30 au radius due to the optically thick dust and forms a ring-like structure (cite: harsono18). Meanwhile, the integrated SO emission is in a shape of a ring that extends up to $0.5\ensuremath{''}$ away, which has been observed toward other protostars (cite: sakai14nat).

The observed HCN emission peaks at two locations that are marked by pink and orange boxes in Fig. [5](#fig:mom0maps). In order to investigate the origin of these HCN peaks, we extract an average spectrum over the two regions. Figure [6](#fig:hcnspectra43) shows the spectrum of HCN compared to  and  in the region to the north of the disk (pink box). The broad  emission indicates a molecular emission from the outflow cavity wall (with a peak at $\approx$2.5 km s$^{-1}$; (cite: bjerkeli2016)) and a faster outflow/molecular wind component at $\approx$-3 km s$^{-1}$ ($\approx v_{\rm sys} - 9$ km s$^{-1}$). The narrow peak of HCN emission (at $\approx$5 km s$^{-1}$) is similar to that of . The other region we highlight is located to the west (orange box). Figure [7](#fig:hcnspectra87) shows the comparison between HCN, , SO, and  spectra in this region. The similarity in their line profiles are indicating a common origin.

![](aa38697_fig8.pdf)

In an attempt to extract the DCN emission, a proxy mask is created from the  spectral cube by taking pixels ($x,y,v$) that are $>3 \sigma$. Figure [8](#fig:maskeddcn) demonstrates that it can extract the HCN emission corresponding to the red-shifted Keplerian disk at $v \sim 9$ km s$^{-1}$) as evidenced by its similarity to the  spectra. The DCN emission is, however, still not clearly detected over the same regions that  is observed.

# Modeling results: molecular column densities and excitation conditions

## Molecular column density of the disk

![](aa38697_fig9.pdf)

The molecular abundance structure of the TMC1A disk can be derived from the spatially resolved molecular column densities. To zeroth order, the molecular column density of the emitting gas can be determined by assuming a thermalized, optically thin layer of emission (cite: goldsmith99; mangum15). As an example, we first present the detailed analysis of the  emission and compare the results from the optically thin approximation to a non-LTE radiative transfer analysis of a slab. The same analysis is applied to the other molecular lines.

The integrated strength of the  emission across the map ranges from 6 – 15 mJy km s$^{-1}$ per beam, which translates to 12 – 30 K km s$^{-1}$. In the optically thin approximation, adopting an excitation temperature of 30 K, the integrated column density of  along the line of sight is then $\approx$ 10$^{16}$ cm$^{-2}$ ($\tau \approx 1$). A temperature of 30 K is usually adopted to convert the dust thermal emission to dust mass and, in the case of  at least, most of the molecular emission is emitted from a region where $T_{\rm gas} = T_{\rm dust}$ (cite: ceccarelli96; doty02). A non-LTE radiative transfer calculation of a slab using RADEX (cite: radex) is also performed as a check on the column density and excitation temperature. These models predict a kinetic temperature of  between 5–30 K with $\tau = 0.1 - 1$. The $N_{\rm{C^{18}O}}$ is between $10^{15}$ to $10^{16}$  cm$^{-2}$. Therefore, the optically thin limit provides a reasonable estimate for the  emitting layer.

Since the  emission can be marginally optically thick ($\tau \approx 1$), line emission from the other observed CO isotopologs will definitely be optically thick ($\tau \approx 10$) simply from the isotopic ratios. Therefore, we present the non-LTE calculations here, and adopt the CO collisional rate coefficients from (cite: corates), obtained from the Leiden Atomic and Molecular Database (LAMDA; (cite: lamda)). These rates coefficients consider two collisional partners of ortho- and para-H$_2$ (cite: jankowski05). The integrated line intensity of  is between 16 – 55 K km s$^{-1}$ while it is 30 – 300 K km s$^{-1}$ for . The non-LTE radiative transfer model yields a suitable range of the excitation temperatures in between 15 to $\sim 70$ K to reproduce the observed integrated  emission with column densities between $10^{16}$ – 10$^{17}$ cm$^{-2}$. In the case of   the range of kinetic temperature is 50 to 300 K and  column densities between $10^{17}-10^{19}$ cm$^{-2}$ ($\tau = 1 - 7$). Since both  and  lines are optically thick, the observed line emission comes from a surface layer (a slab) above the midplane. This implies that the derived column densities are lower limits to the total column density of the gas that is present in the system.

The non-LTE radiative transfer calculations for HCN, , and SO lines also use the LAMDA collisional rate coefficients. The rates for HCN from LAMDA are based on HCN-He collisions of (cite: hcnrate1), scaled to H$_2$. The collisional rates for  are estimated using the dipole moment of (cite: botschwina93). SO- collisional rates are scaled from SO- calculations of (cite: lique06). All of these rates consider a single collisional partner, H$_2$, without taking into account its ortho-to-para ratio.

In the optically thin limit, the observed HCN, , and SO emissions are produced by $N_{\ce{HCN}} = 5 \times 10^{12} - 10^{13}$ cm$^{-2}$, $N_{\ce{HCO^{+}}} = 5 \times 10^{12} - 10^{13}$ cm$^{-2}$, and $N_{\ce{SO}} = 10^{14} - 6 \times 10^{14}$ cm$^{-2}$, respectively, with an adopted excitation temperature of 30 K. Figure [9](#fig:columnave) shows the azimuthally averaged integrated line intensities and associated column densities in the optically thin limit (including  and ). With the non-LTE slab model, the observed emission can be reproduced by kinetic temperatures between 30 – 50 K and column densities of $10^{13}$ cm$^{-2}$, which are similar to the derived values presented in Fig. [9](#fig:columnave) ($\tau \approx 1$). Similar temperatures can also reproduce the observed HCN emission with $N_{\rm HCN} \approx 10^{12} - 10^{13}$ cm$^{-2}$, $\tau < 1$. Finally, the observed SO emission can be reproduced with similar kinetic temperatures as the previous two molecules and higher column densities of $10^{14} - 10^{15}$ cm$^{-2}$. The physical conditions of SO along the line of sight are consistent with , which is optically thick. The optically thin local thermodynamic equilibrium (LTE) calculations can provide useful limits to the the column densities of the detected molecules.

Since we have observed the same rotational transition in HCN and DCN, albeit only an upper limit on the DCN emission, we can place constraints on the D/H ratio in the vicinity of TMC1A. We restrict this analysis to the disk-averaged value by determining the column density and temperature of the upper limit to the integrated line intensity obtained from the HCN and DCN spectra, summed over the Keplerian disk. As a check, we determined that the physical conditions derived from the averaged HCN spectrum are similar to the azimuthally-averaged values in the previous section. For a range of excitation temperatures between 15 to 50 K, an average value of $N_{\ce{HCN}} \sim 1.1 \times 10^{12}$ cm$^{-2}$ is derived for the TMC1A disk. The same analysis provides an upper limit for the DCN column density of $\sim 3 \times 10^{11}$ cm$^{-2}$, resulting in a DCN$/$HCN ratio of $<$0.3. If we instead only consider the HCN emission between 8 to 10 km s$^{-1}$ (where the HCN emission is strongest), the upper limit of DCN$/$HCN is then $<0.26$.

## Temperature structure of the disk

![](aa38697_fig10.pdf)

Spatially resolved observations of dust continuum and molecular line emission can be used to estimate the temperature structure of the disk. To this end, Figure [10](#fig:TMC1Atemp) shows the observed dust continuum brightness temperature at 230 and 240 GHz, as well as the molecular line peak brightness temperatures, as a function of the deprojected radius. The flattening in the inner $<10$ au is caused by unresolved continuum emission. If the dust emission is optically thick within the inner 30 au, however, the peak continuum brightness temperature gives indications on the disk’s temperature profile.

Using the high-velocity channels ($1 < v < 4$ km s$^{-1}$ and $9< v <12$ km s$^{-1}$; to avoid resolved-out emission near the systemic velocity), the peak brightness temperature of , , HCN and SO molecular lines as a function of the deprojected radius is shown in Fig. [10](#fig:TMC1Atemp). There are only small differences between the  and  brightness temperatures, and only at $> 30$ au radius, so only  is plotted. After acknowledging the decrease in molecular emission in the inner 30 au radius, as well as optically thin components, the remaining few optically thick emission data points can provide the additional constraints on the disk temperature profile. Their approximate average values and locations are indicated by the large symbols in Fig. [10](#fig:TMC1Atemp).

The equilibrium midplane temperature of a circumstellar disk can be characterized using a power-law in radius with an index between -0.4 to -0.5 (cite: chiang97; vanthoff18b). We find that, by eye, a temperature profile given by $2000 \times \left ( R/0.1 \ {\rm au} \right )^{-0.6}$ seems to be consistent with our dust and gas observations of TMC1A. It reproduces the dust brightness temperature profile in the inner 30 au and intersects the peak of the  emission. The derived temperature structure is similar to the disk around L1527 ($L_{\rm bol} = 1.9-2.6 \ L_{\odot}$) as measured by (cite: vanthoff18b). Furthermore, the slope of the temperature profile is steeper than expected from purely re-radiated stellar photons ($q\simeq -0.4$), implying that the observed emitting surface shifts from the hot disk surface to the cold disk/envelope gas at large radii. The estimated temperature of 1000-2000 K at 0.1 au is also consistent with the observed $L_{\rm bol}$ ($2.7 \ L_{\odot}$) for a 4000 K protostar ($R_{\star} \sim 3.4$ $R_{\odot}$). The derived temperature structure implies that the warm TMC1A disk does not have a CO freeze-out region ($T_{\rm dust} = 30$ K) in the inner 100 au of the disk (cite: vanthoff18b). Recent observations presented by (cite: vanthoff20) also indicate the lack of CO freeze-out region in TMC1A disk.

# Discussion: the molecular layer of disks

The unprecedented spatial resolution of these observations allows us to disentangle molecular emission from the disk and from the large-scale envelope. The simple molecules targeted in our data set are , , , SO, , HCN, and DCN, plus the spectrally unresolved . These molecules can be used to better understand the evolution of the physical and chemical structure of disks during the embedded stage of star and planet formation.

## Physical components of embedded protostars traced by molecular lines

![](aa38697_fig11.pdf)

The observed molecular lines trace different physical components of an embedded protostellar system, i.e., the inner envelope ($R < 500$ au), Keplerian disk, disk wind, and the cold, infalling envelope. The schematic in Fig. [11](#fig:cartoon) summarizes the observed molecular tracers, their emitting regions, and the physical component that we associate each tracer to. As done previously, we use the symmetric line profile of  and  2–1 to establish the location of the Keplerian disk. We then compare the other molecular line profiles with  and  to provide a first look into the physical components traced by these other lines in TMC1A. Finally, we add the channel maps and zeroth moment maps comparison to give the complete understanding on the emitting regions of these molecules and the structure of the TMC1A system.

From the line profiles in Fig. [3](#fig:rotspectra), the roughly symmetric  3–2 line profile indicates that it is tracing the Keplerian disk. This is not unexpected since  is mainly formed through reactions that involve CO (see Section [5.3](#sub:accretion)), and, thus,  emission should coincide with the CO emission. On the surface of the disk with low densities, chemical reactions tend to favor the production of (cite: aikawa15) and the destruction of  by water vapor (cite: jorgensen13; vanthoff18a). The emitting  layer in the disk is confined to a small outer layer (see (cite: mathews13)).

The asymmetric line profiles of HCN and SO, meanwhile, strongly indicate that these lines are tracing multiple physical components along the line of sight (Fig. [7](#fig:hcnspectra87)). For example, both HCN and SO show red-shifted emission to the west that corresponds (both spatially and in velocity space) to the Keplerian disk as traced by  and .

The narrow line profile of HCN 3–2 (Figs. [6](#fig:hcnspectra43) and [7](#fig:hcnspectra87)) strongly indicates emission from quiescent gas, and this gas could be in either the envelope or Keplerian disk. The similarity in the line shape and velocity peak of  and  in Fig. [7](#fig:hcnspectra87) points to the Keplerian disk as the origin of the red-shifted HCN emission. At lower velocities, the HCN line profiles shows evidence of some contribution from the surrounding envelope. Therefore, we conclude that the HCN line traces the disk-envelope transition region. A detailed 2D physical and chemical model is required to quantify the exact location of the molecular emission, but this is beyond the scope of the current work. Finally, the morphology and velocity of 3–2 emission (Figs. [5](#fig:mom0maps), [6](#fig:hcnspectra43)) does not appear to be connected to the outflow observed previously in CO (cite: bjerkeli2016).

![](aa38697_fig12.pdf)

Our spatially resolved SO observations show morphological features (Figs. [4](#fig:chanmaps) and [5](#fig:mom0maps)) that are similar to CO and . The narrow line profile of SO in Fig. [7](#fig:hcnspectra87) and the low peak temperatures of SO in Fig. [10](#fig:TMC1Atemp) meanwhile rule out an accretion shock origin (cite: sakai14nat). A comparison between the zeroth moment maps of , HCN, and  is shown in Fig. [12](#fig:TMC1ASO). Since the SO and  molecular emission are not co-spatial, it excludes a disk wind origin for SO (cite: tabone17) for TMC1A. However, the blue-shifted HCN emission in Fig. [12](#fig:TMC1ASO) peaks at the location near the blue-shifted CO emission suggesting a region where the wind and the envelope interact. The combination of the SO line profile and its peak brightness temperature (Fig. [10](#fig:TMC1Atemp)) indicates that it originates from the infalling, warm inner envelope along the line of sight. The location of the SO emission with respect to the disk wind (blue-shifted emission at 4.3 km s$^{-1}$) and the Keplerian disk further supports that SO is located along the outflow cavity wall. This is also hinted by the presence of lower velocity component in the spectrum shown in Fig. [7](#fig:hcnspectra87). The favorable orientation of TMC1A and these deep spectrally resolved molecular line observations allow us to disentangle the different physical components of this embedded disk. Such an empirical derivation of the origin of SO would have been impossible in an edge-on system and without additional gas line tracers.

## Molecular abundances in the TMC1A disk.

![](aa38697_fig13.pdf)

One of the major questions in star and planet formation is whether or not planet-forming materials enter the disk from the envelope unaltered. Alteration of planet-forming materials require high temperatures that can generally only be achieved in interstellar shocks and the inner regions of protostellar systems. These changes would be relevant for the accretion history of the protostar (e.g., dust sublimation in the inner regions of the disk or protostellar accretion bursts) and disk formation (e.g., accretion shocks at the disk-envelope interface that affect the chemistry and ionization fraction) that can be explored by comparing the chemical abundances of young stellar objects at different scales. Indeed, differences in chemical content between the embedded disk and its surrounding envelope may point to on-going physical processes during the early stages of star and planet formation.

The molecular line spectra and the kinetic temperature analysis presented in this work identify some regions and velocity intervals that emission from the disk, but also indicate that some lines of sight toward TMC1A are contaminated by its surrounding envelope. We showed in Sect. [4.1](#sub:diskcolden) that assuming the optically thin limit can provide useful constraints on the emitting molecular layer and the column densities of the disk. Furthermore, with the azimuthally averaged column densities in hand, we can constrain the molecular abundances in the disk. In addition, since these observations use the longest baselines configuration of ALMA, they are only sensitive up to a maximum recoverable scale of $\sim 0.5\ensuremath{''}$ ($\sim$ 70 au). Thus, the observed molecular emission is restricted to the inner hundred au of TMC1A, however, the chemical timescales in these regions are indeed longer than the infall timescale (the time for the gas to fall onto the disk). Therefore, we expect that the derived molecular abundances on the observed scales of these observations should not significantly change before the molecular gas enters the disk.

By comparing the derived column densities of the different species, we obtain $N_{\rm HCO^{+}}/N_{\rm ^{13}CO} \sim 10^{-4} - 10^{-3}$ and $N_{\rm SO}/N_{\rm ^{13}CO} = 10^{-3} - 10^{-1}$. The HCN abundance is meanwhile estimated through comparison with the  column density, giving $N_{\ce{HCN}}/N_{\ce{C^{18}O}} = 10^{-4}-10^{-2}$. The proxy mask (see Sect. [3.2](#sub:rottrans)) using the  spectral cube recovers more HCN flux than a proxy mask using the  spectral cube. Although some envelope material is contaminating the detected emission, it is still useful to calculate the relative abundances for the disk, which are shown graphically in Fig. [13](#fig:TMC1Amolabun). Adopting the ISM isotopic ratios of $\ce{^{12}C}:\ce{^{13}C} = 70$ and $\ce{^{16}O}:\ce{^{18}O} = 540$ (cite: wilson94), the derived molecular abundances relative to  are then $X_{\ce{HCO^{+}}}/X_{\ce{CO}} \sim 10^{-6}-10^{-5}$, $X_{\ce{HCN}}/X_{\ce{CO}} \sim 10^{-7}-10^{-5}$, and $X_{\ce{SO}}/X_{\ce{CO}} \sim 10^{-5}-10^{-3}$.

It has been demonstrated that the CO gas abundance in young disks remains close to the canonical ISM value of $X_{\ce{CO}} =$ $10^{-4}$ relative to (cite: harsono14; vanthoff18b; kzhang20). Adopting this value, we estimate abundances of $X_{\ce{HCO^{+}}} = 10^{-10}$–$10^{-9}$, $X_{\ce{HCN}} = 10^{-11}$–$10^{-9}$ and $X_{\ce{SO}} = 10^{-9}$–$10^{-7}$ in the disk of TMC1A, where $X$ denotes an abundance with respect to . One should keep in mind, however, that these abundance fractions are valid in the emitting regions of the inner warm envelope and the layers of the young disk above the dust photosphere.

Remarkably, the gas abundance ratios in the disk around TMC1A are similar to its protostellar envelope (Fig. [13](#fig:TMC1Amolabun)). This implies a smooth transport of materials without the presence of strong shocks ($T > 100$ K) that modify the molecular composition of the material en route to the disk (cite: visser09).  and show features of filtered out molecular emission. The comparison of the total  and  integrated emission between this study and (cite: harsono14) also indicate 90% of the emission is filtered out as a result of going from $0.5\ensuremath{''}$ to $0.1\ensuremath{''}$ resolution. However, the lack of absorption in the SO line profile suggests that our studies recover most of its emission. Thus, the range of the SO/CO abundance ratio shown in Fig. [13](#fig:TMC1Amolabun) may instead be explained by filtered out CO emission. It further indicates that and SO are not drastically affected by the physical processes that take place during disk formation.

The chemical composition of the TMC1A disk is also similar to that of Class II disks. The main difference is the lower absolute CO gas abundance that is inferred from CO observations of Class II disks (cite: miotello17; kzhang20). CO depletion during star and planet formation is linked to the formation of complex organics, on-going planet formation, and the UV field around low-mass stars (cite: moyu17; bosman18; dodson18; mcclure19). As such, gas abundance ratios (as compared to absolute abundances) may be less sensitive to variations between objects and better reflect how chemistry changes with evolutionary state. Therefore, the similar gas molecular abundance ratios between the TMC1A disk and Class II disks may indicate that the molecular layer of protoplanetary disks do not change significantly once the disk is formed ($M_{\rm d}/M_{\rm env} \sim 0.5$).

Interestingly, for the most part, the abundance ratios between protostellar systems and Solar System objects do show significant differences. In order to assess whether SO is truly being affected by disk formation, deep observations of other S-bearing species (e.g., , , ) in combination with multi-resolution CO observations are needed to recover the total emission from the inner 500 au of the TMC1A system. Without observations of other S-bearing molecules, it is difficult to conclude the origin of this discrepancy. A comparison between S-bearing species in IRAS 16293–2422 and comet 67P imply that the Solar System formed in a higher UV field than IRAS 16293–2422 (cite: drozdovskaya18) since S is a volatile element and sensitive to the changes in the UV field. Thus, it would seem that the differences in S-bearing molecules may trace the strength of the UV field during protostellar evolution.

With regards to HCN and DCN, (cite: huang17) show that there is a spread in DCN abundances in disks that stems from the different cold and warm routes of DCN formation (cite: aikawa99; willacy07). Unfortunately, neither HCN nor DCN were detected toward TMC1A in the single-dish survey of (cite: jorgensen04c) which hinders us from a straight comparison between disk and envelope values; the ratio in Fig. [13](#fig:TMC1Amolabun) instead adopts the prestellar core value. Our upper limits to the DCN/HCN fraction in the TMC1A disk are, meanwhile, consistent with other various young stellar objects and Solar System objects. A small variation in DCN/HCN in protostellar envelopes has been observed (cite: jorgensen04c), which seems to be related to the bolometric luminosity of the source. However, it is still not well understood whether the level of deuteration is modified during disk formation. For example, an older disk presented in (cite: huang17) seems to have a DCN/HCN ratio consistent with comet Hale-Bopp, which favors the idea of an evolving DCN/HCN ratio. Meanwhile, the DCN/HCN ratio of Titan is different than that of both disks and comets, indicating a different origin for the observed deuteration fraction.

A large variation across different types of objects is also seen in and abundance ratios. Interestingly, abundance variations in both and HCN have been linked to angular momentum transport (cite: cuzzi06a; kalyaan19) and planet formation (cite: najita13; krijt16; du17; najita18). Our sub-mm column density for TMC1A is adopted from the upper limit in (cite: harsono20) ($N$(H$_2$O)/$N$(H$_2$) $< 10^{-6}$) that probes the inner 10 au of the disk. Hot water observations in the mid-IR around Class II disks (cite: carr08; salyk11; najita13) meanwhile probe the inner 2 au where terrestrial planets are expected to form. The observed correlation between the / mid-IR line flux ratios and the disk mass (via the millimeter flux density) has been suggested to trace planetesimal formation inside of 5 au (cite: najita13; najita18). If the observed mid-IR line flux ratios correspond to the relative abundances in the emitting layers (cite: bruderer15), then they are consistent with the gas molecular abundance ratios derived in this work. The differences between the abundance ratios in the large-envelope and disk (Fig. [13](#fig:TMC1Amolabun)) thus suggests that / is set during disk formation, which is indeed supported by the similar abundance ratio observed in comets 67P and Hale-Bopp. On the other hand, both and abundances (relative to ) differ between the TMC1A disk, inner disks as observed in the mid-IR, and comets. However, much deeper and spatially resolved HCN and water observations are needed to fully reveal the physical processes that can cause these variations.

## Accretion processes in a young disk

| No.  | Reaction $^{a}$       |          $a$          |  $b$  |
|:----:|:----------------------|:---------------------:|:-----:|
| 1\.  | \+ CR $\rightarrow$ + |       ...$^{b}$       |  ...  |
| 2\.  | \+ $\rightarrow$ + H  |   $2\times 10^{-9}$   |   0   |
| 3\.  | \+ $\rightarrow$ +    | $1.70\times 10^{-9}$  |   0   |
| 4\.  | \+ $\rightarrow$ +    | $1.61\times 10^{-9}$  |   0   |
| 5\.  | \+ $\rightarrow$ +    | $8.8 \times 10^{-10}$ |   0   |
| 6\.  | \+ $\rightarrow$ +    | $2.8 \times 10^{-7}$  | -0.69 |
| 7\.  | \+ $\rightarrow$ +    | $1.3 \times 10^{-8}$  | -0.84 |
| 8\.  | \+ $\rightarrow$ +    | $2.47 \times 10^{-7}$ | -0.84 |
| 9\.  | \+ $\rightarrow$ +    | $2.34\times 10^{-8}$  | -0.52 |
| 10\. | \+ $\rightarrow$ + +  | $4.36\times 10^{-8}$  | -0.52 |

: Reaction network used to calculate the abundance given values for , , and CO. Reactions with a cosmic ray (CR) is also included. Reaction rate coefficients are obtained from the Kinetic Database for Astrochemistry (cite: kida).

Table notes:

During the formation of a star and disk, mass flows from the large-scale envelope to the disk and the young protostar. Previously, disk accretion rates have been measured through the bolometric luminosity and/or molecular emission at large radii ($> 500$ au). On the other hand, a detailed 2D model of a bursting Class I protostar can capture the current disk structure and infer the more accurate accretion rate during the burst (cite: GBaek20; LeeYH20). From the bolometric luminosity of TMC1A ($L_{\rm bol} = 2.7$ $L_{\odot}$, (cite: kristensen12)), the accretion rate is inferred to be $\sim 3\times 10^{-7}$ $M_{\odot}$ yr$^{-1}$. Similar values are derived from molecular line observations (cite: aso15; mottram17). These inferred accretion rates usually refer to the mass flow from envelope-to-disk or from disk-to-star (i.e. stellar). With our spatially resolved molecular line observations and associated analysis, it is possible to re-examine the accretion rate and investigate the dominant accretion mechanism in the TMC1A disk.

An accretion disk mediates the mass transfer between the large-scale envelope and the young protostar. It does so by shifting angular momentum from the accreting the mass, which, e.g., can result in a viscously growing disc. One of the major uncertainties and sources of continued debate in understanding the evolution of disks is the physical driver of accretion. A parameterized and constant viscosity (cite: SS73) is typically adopted to describe the transport of angular momentum through the disk (cite: hueso05; visser09), but this alone does not reveal the physical driver. In rotating magnetized disks, the magnetorotational instability (cite: balbus91; balbus03) can drive accretion (and turbulence) if the disk is sufficiently ionized (cite: balbus00). These proposed theories rely on the kinematical structure of the disk being nearly Keplerian. In order to constrain whether MRI is active in the TMC1A disk, which is indeed a Keplerian disk, we need to estimate the ionization fraction, and  can be used to do this.

The abundance of  is chemically linked to the electron abundance, $X_e$, which can be used to determine the ionization fraction. A simple chemical model that links CO to  and can be found in (cite: aikawa15). Table [2](#tab:chemical) lists the reaction network from (cite: aikawa15) that we employ here. We adopt a fixed CO abundance of $10^{-4}$ and a abundance of $3 \times 10^{-6}$ relative to . The high relative abundance of CO leads to it dominating the chemistry, and the adopted value of abundance does not affect our results. We compute the electron number density from the cosmic ray (CR) ionization rate $\zeta$ using $n_{e^{-}} = 2\sqrt{\zeta / \left ( 2 k_{6} n_{\rm H} \right )} n_{\ce{H2}}$ (cite: aikawa15) where $k_{6}$ is the rate coefficient of the sixth reaction in Table [2](#tab:chemical). A range of densities, temperature, and $\zeta$ values are explored to investigate the effect on the resulting  abundance. With , , , and abundances known, we solve for the equilibrium abundance of .

Using these approximations, the inferred  abundance can be reproduced with $\zeta \sim 10^{-17}$ s$^{-1}$, densities of $10^{6}$ cm$^{-3}$, and a gas temperature of 20 K. We find that the gas density $n_{\ce{H2}}$ is the dominant factor in the calculation, while the gas temperature does not strongly affect the results; the variance in  abundance is less than a factor of 2 for temperatures between 20 and 100 K. From varying the density, we find that  emission seems to be confined to regions with $n_{\ce{H2}}< 10^{8}$ cm$^{-3}$ (see (cite: mathews13)).

An MRI active region is defined by its magnetic Reynolds number $$\begin{equation}
    R_{\rm e} = \frac{c_{\rm s} h}{D} \approx
    1 \left ( \frac{X_{\ce{e}}}{10^{-13}} \right )
    T_{\rm 100K}^{1/2} R_{\rm au}^{3/2},
\end{equation}$$ where $c_{\rm s}$ is the sound speed, $h$ is the disk scale height, $D$ is the magnetic diffusivity, $T_{\rm 100K}$ is the gas temperature normalized to 100 K, and $R_{\rm au}$ is the radial distance from the star normalized to 1 au (cite: perezbecker11). A secondary condition for a MRI unstable disk is a high ion-neutral collision rate, i.e., that the turbulence is efficiently transferred to the bulk neutral disk. The ion-neutral collision rate can be expressed using $$\begin{equation}
    Am \approx 1 \left ( \frac{X_{i}}{10^{-8}} \right ) n_{\rm 10}
    R_{\rm au}^{3/2},
\end{equation}$$ where $X_{i}$ is the abundance of a singly ionized species and $n_{\rm 10}$ is the gas number density normalized to $10^{10}$ cm$^{-3}$ (cite: perezbecker11). Here, we assume that  is the dominant ion. Given the estimated abundance of the  emitting layer, and the inferred electron abundance $X_e$ (using $n_{\ce{H2}} = 10^{6}$ cm$^{-3}$ and $\zeta = 10^{-17}$ s$^{-1}$; see above), we estimate that $R_{\rm e} > 10^{6}$ and $Am < 0.1$. Depending on the disk structure and the magnetic field orientation, the region of the disk needs to be above the critical $R_{\rm e} = 10^2$–$10^4$ (cite: fleming00; flock12) for MRI to be active. Magneto-hydrodynamic disk shearing box simulations by (cite: xnbai11) meanwhile suggest that MRI can be active in disks at any given $Am$ if the disk is sufficiently weakly magnetized. Therefore, unless the TMC1A disk is weakly magnetized, which is in contrast to the magnetically-powered disk wind observed in TMC1A (cite: bjerkeli2016), MRI is likely not active in the observed molecular layer.

The current disk accretion rate can also be inferred through the location of the water snow surface. We use the brightness temperature profile in Fig. [10](#fig:TMC1Atemp) to estimate that the water snow surface in TMC1A is located at $\simeq$10 au (i.e. where $T < 160$ K), which is consistent with the non-detection of millimeter emission from this disk (cite: harsono20). The relation between the midplane water snowline and the disk accretion rate in embedded disks was explored in (cite: harsono15b). From those results, and the non-detection of the water line, we infer that the stellar accretion rate is $\lesssim 10^{-5}$ M$_{\odot}$ yr$^{-1}$ in TMC1A.

The observed brightness temperature profile (Sect. [4.2](#sub:tempstructure)) likely traces the irradiated disk surface ($T_{\rm eff} \sim L_{\star}^{1/4} R^{-1/2}$). From the inferred water snowline location and the current bolometric luminosity, we estimate that the current stellar accretion rate is close to $10^{-6}$ M$_{\odot}$ yr$^{-1}$. Note that the current TMC1A disk accretion rate ($\sim 10^{-6}$ $M_{\odot}$ yr$^{-1}$) is higher than the values obtained from its bolometric luminosity and previous large-scale molecular emission. A more detailed 2D physical structure (cite: cleeves13; cleeves17) of the disk+envelope is, however, required to more accurately assess these values.

Other sources of angular momentum transport which could drive the accretion in the TMC1A disk could be magnetically-powered winds (cite: xnbai13; ramsey2019), and gravitational (GI) or hydrodynamical instabilities (cite: lyra19). Due to the absence of observable dust substructures in TMC1A, (cite: harsono18) suggest that $M_{\rm disk}/M_{\star} \lesssim 0.1$, yielding $\alpha_{\rm GI} \lesssim 0.06$ (i.e. a long cooling timescale $t_{\rm cool} \sim 10 \Omega^{-1}$).

# Summary and Conclusions

This paper presents spatially resolved observations of dust and gas with ALMA toward the young disk around TMC1A. The high-spatial resolution provided by 16 km baselines has proven crucial in isolating the emission of the young disk from its surrounding envelope. Studies such as this are critical to tracing the evolution of various molecules during the early stages of planet formation. The results and conclusions of this paper are as follows.

- The dust disk is detected at 203, 220, 230, 240, and 260 GHz. Dust continuum visibilities are analyzed with Gaussian intensity profiles at each frequency to constrain the orientation of the disk around TMC1A to $i=50^{\circ} \pm 3^{\circ}$ and $PA = 76^{\circ} \pm 4^{\circ}$.

- We present high-spatial observations of 3–2, 3–2,  3–2, and SO $5_6$–$4_5$, as well as a hint of spectrally unresolved emission. The emission cannot be imaged because it is mostly filtered out.

- High-spatial-resolution CO observations are essential to distinguish the molecular emission associated with the disk wind, the envelope, and the Keplerian disk. By comparing the morphology of the  emission to CO, we determine that  traces the upper layers of the disk and parts of the infalling envelope.

- Two HCN emission peaks are located to the west on the red-shifted side of the disk and to the north of the blue-shifted side of the disk. By comparing the HCN to  and , the narrow line profile suggests that the emission to the north of the disk traces the protostellar envelope near the outflow cavity wall. Meanwhile, the red-shifted HCN emission to the west is co-spatial with the  emission and emanates from the surface of the embedded Keplerian disk.

- The zeroth moment map of SO shows a partial ring-like structure that has been seen towards other protostellar systems. Owing to the orientation of the TMC1A system, we are able to differentiate between the plane of SO emission and the Keplerian disk as traced by . The combination of the SO line profile and its low brightness temperature indicates that the emission originates from the dense and warm inner envelope close to the outflow cavity wall.

- The molecular emission is analyzed considering thermalized, optically thin emission as well as non-LTE models using the RADEX radiative transfer code. We find that the optically thin limit provides a reasonable estimate of the emitting column densities of the detected molecular lines. With the derived column densities, we infer the abundance structure of the disk relative to CO. The disk-averaged abundances are then $X_{\ce{HCO^{+}}} = 10^{-10}$ – $10^{-9}$, $X_{\ce{HCN}} = 10^{-11}$ – $10^{-9}$ and $X_{\ce{SO}} = 10^{-9}$ – $10^{-7}$. With an upper limit to the DCN emission, we estimate a / ratio of $<0.26$ for the TMC1A disk.

- The comparison of molecular abundances of the disk to its surrounding envelope shows that the observed molecular layer of the disk is composed of unaltered infalling gas. This indicates a smooth transition between the envelope and the young disk. Furthermore, the similarity of the relative abundances of , HCN, and SO between the young TMC1A disk and Class II disks suggest that some parts of the molecular layer in disks are set during the disk formation phase.

- The derived HCN, DCN, and molecular abundances of the TMC1A disk show larger discrepancies relative to Class II disks and Solar System objects (comet 67P, Hale Bopp, and Titan). While the / ratio of the TMC1A disk is consistent with observed inner disks and comets, the ratio is different from values typically found in protostellar envelopes. Similarly, the individual abundance of the TMC1A disk is different from Solar System comets despite that it is within the range of other Class II disks. From these comparisons, it would seem that the ratio of / is established during the disk formation process. We propose that deeper observations of HCN isotopologs and are crucial to understand the early physical and chemical evolution of planet-forming disks.

- Explaining the accretion process in disks is one of the fundamental problems in astrophysics. With the derived  abundance, we find that the observed molecular layer of the TMC1A disk is not sufficiently ionized to be MRI unstable. The ionization rate is obtained using a reduced chemical network to reproduce the observed  abundance. We estimate an accretion rate of the TMC1A disk of $\sim 10^{-6}$ $M_{\odot}$ yr$^{-1}$. Other physical processes such as disk winds, gravitational instability, or hydrodynamical instabilities are thus needed to drive accretion in TMC1A.

These results are one of the first that directly compare the relative molecular abundances (six species) in a young disk with its own envelope, Class II disks, and Solar System objects. The aim of this comparison is to provide molecular tracers that can probe the physics of disk formation and accretion. In addition,  and observations are crucial in revealing the accretion process (envelope-to-disk, disk-to-star) during the embedded stage of star formation. These observations support the idea that the composition of the molecular layer of planet-forming disks is determined during the disk formation phase. Future deep observations that require ALMA LBC ($> 16$ km baselines) per target ($L_{\rm bol} \sim 3 L_{\odot}$) within 200 pc will be needed to further unravel the chemical structure of Keplerian disks around young stellar objects.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.01549.S, ADS/JAO.ALMA#2016.1.00711.S, and ADS/JAO.ALMA#2017.1.00212.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.

This work uses observations carried out under project number V064 and X065 with the IRAM NOEMA Interferometer/PdBI. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain).

This work is based on observations collected at the European Southern Observatory Very Large Telescope under program ID 179.C-0151. We thank Klaus Pontoppidan and Greg Herczeg for providing the calibrated data.

We thank the anonymous referee for carefully reading the manuscript and their constructive feedback that improved this paper. Astrochemistry in Leiden is supported by the European Union A-ERC grant 291141 CHEMPLAN, by the Netherlands Research School for Astronomy (NOVA) and by a Royal Netherlands Academy of Arts and Sciences (KNAW) professor prize. D.H. acknowledges support from the EACOA Fellowship from the East Asian Core Observatories Association. P.B. acknowledges the support of the Swedish Research Council (VR) through contracts 2013-00472 and 2017-04924. J.P.R. acknowledges support from Virginia Initiative on Cosmic Origins (VICO), and the National Science Foundation (NSF) under grant nos. AST-1910106 and AST-1910675. J.K.J. acknowledges support by the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme through Cosolidator Grant “S4F" (grant agreement No 646908).

This research made use of Astropy community-developed Python package for Astronomy (cite: astropy18), numpy, matplotlib (cite: Hunter2007), and python package CASACORE to handle CASA products (images and measurement sets).

155 natexlab

(ref: aikawa15) Aikawa, Y., Furuya, K., Nomura, H., & Qi, C. 2015, ApJ, 807, 120

(ref: aikawa03) Aikawa, Y., Momose, M., Thi, W.-F., et al. 2003, PASJ, 55, 11

(ref: aikawa99) Aikawa, Y., Umebayashi, T., Nakano, T., & Miyama, S. M. 1999, ApJ, 519, 705

(ref: hltau2014) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: armitage11) Armitage, P. J. 2011, ARA&A, 49, 195

(ref: delavillarmois19a) Artur de la Villarmois, E., Jørgensen, J. K., Kristensen, L. E., et al. 2019a, A&A, 626, A71

(ref: delavillarmois19b) Artur de la Villarmois, E., Kristensen, L. E., & Jørgensen, J. K. 2019b, A&A, 627, A37

(ref: delavillarmois18) Artur de la Villarmois, E., Kristensen, L. E., Jørgensen, J. K., et al. 2018, A&A, 614, A26

(ref: aso15) Aso, Y., Ohashi, N., Saigo, K., et al. 2015, ApJ, 812, 27

(ref: asplund09) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481

(ref: astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: GBaek20) Baek, G., MacFarlane, B. A., Lee, J.-E., et al. 2020, ApJ, 895, 27

(ref: xnbai13) Bai, X.-N. 2013, ApJ, 772, 96

(ref: xnbai11) Bai, X.-N. & Stone, J. M. 2011, ApJ, 736, 144

(ref: balbus03) Balbus, S. A. 2003, ARA&A, 41, 555

(ref: balbus91) Balbus, S. A. & Hawley, J. F. 1991, ApJ, 376, 214

(ref: balbus00) Balbus, S. A. & Hawley, J. F. 2000, Space Sci. Rev., 92, 39

(ref: bast11) Bast, J. E., Brown, J. M., Herczeg, G. J., van Dishoeck, E. F., & Pontoppidan, K. M. 2011, A&A, 527, A119

(ref: bergin10) Bergin, E. A., Hogerheijde, M. R., Brinch, C., et al. 2010, A&A, 521, L33

(ref: bergin97) Bergin, E. A. & Langer, W. D. 1997, ApJ, 486, 316

(ref: bisschop08) Bisschop, S. E., Jørgensen, J. K., Bourke, T. L., Bottinelli, S., & van Dishoeck, E. F. 2008, A&A, 488, 959

(ref: bjerkeli2016) Bjerkeli, P., van der Wiel, M. H. D., Harsono, D., Ramsey, J. P., & Jørgensen, J. K. 2016, Nature, 540, 406

(ref: blake95) Blake, G. A., Sandell, G., van Dishoeck, E. F., et al. 1995, ApJ, 441, 689

(ref: bockelee00) Bockelée-Morvan, D., Lis, D. C., Wink, J. E., et al. 2000, A&A, 353, 1101

(ref: bollard2017) Bollard, J., Connelly, J. N., Whitehouse, M. J., et al. 2017, Science Advances, 3, e1700407

(ref: booth19) Booth, A. S., Walsh, C., & Ilee, J. D. 2019, A&A, 629, A75

(ref: bosman19) Bosman, A. D., Cridland, A. J., & Miguel, Y. 2019, A&A, 632, L11

(ref: bosman18) Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018, A&A, 618, A182

(ref: botschwina93) Botschwina, P., Horn, M., Flügge, J., & Seeger, S. 1993, J. Chem. Soc., Faraday Trans., 89, 2219

(ref: briggs95) Briggs, D. S. 1995, in Bulletin of the American Astronomical Society, Vol. 27, American Astronomical Society Meeting Abstracts, 1444

(ref: bruderer15) Bruderer, S., Harsono, D., & van Dishoeck, E. F. 2015, A&A, 575, A94

(ref: bruderer12) Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541, A91

(ref: calvet92) Calvet, N., Hartmann, L., & Hewett, R. 1992, ApJ, 386, 229

(ref: carney18) Carney, M. T., Fedele, D., Hogerheijde, M. R., et al. 2018, A&A, 614, A106

(ref: carney19) Carney, M. T., Hogerheijde, M. R., Guzmán, V. V., et al. 2019, A&A, 623, A124

(ref: carr08) Carr, J. S. & Najita, J. R. 2008, Science, 319, 1504

(ref: caselli12b) Caselli, P., Keto, E., Bergin, E. A., et al. 2012, ApJL, 759, L37

(ref: ceccarelli05) Ceccarelli, C., Dominik, C., Caux, E., Lefloch, B., & Caselli, P. 2005, ApJL, 631, L81

(ref: ceccarelli96) Ceccarelli, C., Hollenbach, D. J., & Tielens, A. G. G. M. 1996, ApJ, 471, 400

(ref: chapillon12) Chapillon, E., Guilloteau, S., Dutrey, A., Piétu, V., & Guélin, M. 2012, A&A, 537, A60

(ref: chiang97) Chiang, E. I. & Goldreich, P. 1997, ApJ, 490, 368

(ref: cleeves13) Cleeves, L. I., Adams, F. C., & Bergin, E. A. 2013, ApJ, 772, 5

(ref: cleeves17) Cleeves, L. I., Bergin, E. A., Öberg, K. I., et al. 2017, ApJL, 843, L3

(ref: cleeves18) Cleeves, L. I., Öberg, K. I., Wilner, D. J., et al. 2018, ApJ, 865, 155

(ref: connelly12) Connelly, J. N., Bizzarro, M., Krot, A. N., et al. 2012, Science, 338, 651

(ref: crapsi05a) Crapsi, A., Caselli, P., Walmsley, C. M., et al. 2005, ApJ, 619, 379

(ref: cuzzi06a) Cuzzi, J. N. & Alexander, C. M. O. 2006, Nature, 441, 483

(ref: dodson18) Dodson-Robinson, S. E., Evans, Neal J., I., Ramos, A., Yu, M., & Willacy, K. 2018, ApJL, 868, L37

(ref: doty02) Doty, S. D., van Dishoeck, E. F., van der Tak, F. F. S., & Boonman, A. M. S. 2002, A&A, 389, 446

(ref: drozdovskaya18) Drozdovskaya, M. N., van Dishoeck, E. F., Jørgensen, J. K., et al. 2018, MNRAS, 476, 4949

(ref: drozdovskaya19) Drozdovskaya, M. N., van Dishoeck, E. F., Rubin, M., Jørgensen, J. K., & Altwegg, K. 2019, MNRAS, 490, 50

(ref: du17) Du, F., Bergin, E. A., Hogerheijde, M., et al. 2017, ApJL, 842, 98

(ref: dutrey97) Dutrey, A., Guilloteau, S., & Guelin, M. 1997, A&A, 317, L55

(ref: cdms2) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. 2016, Journal of Molecular Spectroscopy, 327, 95, new Visions of Spectroscopic Databases, Volume II

(ref: fedele16) Fedele, D., van Dishoeck, E. F., Kama, M., Bruderer, S., & Hogerheijde, M. R. 2016, A&A, 591, A95

(ref: fleming00) Fleming, T. P., Stone, J. M., & Hawley, J. F. 2000, ApJ, 530, 464

(ref: flock12) Flock, M., Henning, T., & Klahr, H. 2012, ApJ, 761, 95

(ref: emcee) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125, 306

(ref: garrod19) Garrod, R. T. 2019, ApJ, 884, 69

(ref: goldsmith99) Goldsmith, P. F. & Langer, W. D. 1999, ApJ, 517, 209

(ref: graninger16) Graninger, D. M., Wilkins, O. H., & Öberg, K. I. 2016, ApJ, 819, 140

(ref: hcnrate1) Green, S. & Thaddeus, P. 1974, ApJ, 191, 653

(ref: guzman15) Guzmán, V. V., Öberg, K. I., Loomis, R., & Qi, C. 2015, ApJ, 814, 53

(ref: harsono18) Harsono, D., Bjerkeli, P., van der Wiel, M. H. D., et al. 2018, Nature Astronomy, 2, 646

(ref: harsono15b) Harsono, D., Bruderer, S., & van Dishoeck, E. F. 2015, A&A, 582, A41

(ref: harsono14) Harsono, D., Jørgensen, J. K., van Dishoeck, E. F., et al. 2014, A&A, 562, A77

(ref: harsono20) Harsono, D., Persson, M. V., Ramos, A., et al. 2020, A&A, 636, A26

(ref: haugbolle2019) Haugbølle, T., Weber, P., Wielandt, D. P., et al. 2019, AJ, 158, 55

(ref: herczeg11) Herczeg, G. J., Brown, J. M., van Dishoeck, E. F., & Pontoppidan, K. M. 2011, A&A, 533, A112

(ref: hincelin13) Hincelin, U., Wakelam, V., Commerçon, B., Hersant, F., & Guilloteau, S. 2013, ApJ, 775, 44

(ref: huang18) Huang, J., Andrews, S. M., Pérez, L. M., et al. 2018, ApJL, 869, L43

(ref: huang17) Huang, J., Öberg, K. I., Qi, C., et al. 2017, ApJ, 835, 231

(ref: hueso05) Hueso, R. & Guillot, T. 2005, A&A, 442, 703

(ref: Hunter2007) Hunter, J. D. 2007, Computing in Science & Engineering, 9, 90

(ref: jacquet19) Jacquet, E., Pignatale, F. C., Chaussidon, M., & Charnoz, S. 2019, ApJ, 884, 32

(ref: jankowski05) Jankowski, P. & Szalewicz, K. 2005, , 123, 104301

(ref: prosac07) Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2007, ApJ, 659, 479

(ref: jorgensen05b) Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2005, ApJ, 632, 973

(ref: jorgensen04c) Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2004, A&A, 416, 603

(ref: prosac09) Jørgensen, J. K., van Dishoeck, E. F., Visser, R., et al. 2009, A&A, 507, 861

(ref: jorgensen13) Jørgensen, J. K., Visser, R., Sakai, N., et al. 2013, ApJL, 779, L22

(ref: kalyaan19) Kalyaan, A. & Desch, S. J. 2019, ApJ, 875, 43

(ref: kama16) Kama, M., Bruderer, S., van Dishoeck, E. F., et al. 2016, A&A, 592, A83

(ref: krijt16) Krijt, S., Ciesla, F. J., & Bergin, E. A. 2016, ApJL, 833, 285

(ref: kristensen12) Kristensen, L. E., van Dishoeck, E. F., Bergin, E. A., et al. 2012, A&A, 542, A8

(ref: LeeYH20) Lee, Y.-H., Johnstone, D., Lee, J.-E., et al. 2020, arXiv e-prints, arXiv:2009.05268

(ref: lique06) Lique, F., Spielfiedel, A., Dhont, G., & Feautrier, N. 2006, A&A, 458, 331

(ref: lodato08) Lodato, G. 2008, New A Rev., 52, 21

(ref: flong18) Long, F., Pinilla, P., Herczeg, G. J., et al. 2018, ApJ, 869, 17

(ref: loomis15) Loomis, R. A., Cleeves, L. I., Öberg, K. I., Guzman, V. V., & Andrews, S. M. 2015, ApJL, 809, L25

(ref: lyra19) Lyra, W. & Umurhan, O. M. 2019, PASP, 131, 072001

(ref: manara19b) Manara, C. F., Mordasini, C., Testi, L., et al. 2019, A&A, 631, L2

(ref: manara17) Manara, C. F., Testi, L., Herczeg, G. J., et al. 2017, A&A, 604, A127

(ref: mangum15) Mangum, J. G. & Shirley, Y. L. 2015, PASP, 127, 266

(ref: mathews13) Mathews, G. S., Klaassen, P. D., Juhász, A., et al. 2013, A&A, 557, A132

(ref: maud17wvr) Maud, L. T., Tilanus, R. P. J., van Kempen, T. A., et al. 2017, A&A, 605, A121

(ref: maury14) Maury, A. J., Belloche, A., André, P., et al. 2014, A&A, 563, L2

(ref: mcclure19) McClure, M. K. 2019, A&A, 632, A32

(ref: mcclure16) McClure, M. K., Bergin, E. A., Cleeves, L. I., et al. 2016, ApJ, 831, 167

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: meier98) Meier, R., Owen, T. C., Jewitt, D. C., et al. 1998, Science, 279, 1707

(ref: meijerink09) Meijerink, R., Pontoppidan, K. M., Blake, G. A., Poelman, D. R., & Dullemond, C. P. 2009, ApJ, 704, 1471

(ref: miotello17) Miotello, A., van Dishoeck, E. F., Williams, J. P., et al. 2017, A&A, 599, A113

(ref: molter16) Molter, E. M., Nixon, C. A., Cordiner, M. A., et al. 2016, AJ, 152, 42

(ref: mottram17) Mottram, J. C., van Dishoeck, E. F., Kristensen, L. E., et al. 2017, A&A, 600, A99

(ref: cdms1) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of Molecular Structure, 742, 215

(ref: mullins16) Mullins, A. M., Loughnane, R. M., Redman, M. P., et al. 2016, MNRAS, 459, 2882

(ref: najita13) Najita, J. R., Carr, J. S., Pontoppidan, K. M., et al. 2013, ApJ, 766, 134

(ref: najita18) Najita, J. R., Carr, J. S., Salyk, C., et al. 2018, ApJ, 862, 122

(ref: oberg17) Öberg, K. I., Guzmán, V. V., Merchantz, C. J., et al. 2017, ApJ, 839, 43

(ref: oberg19) Öberg, K. I. & Wordsworth, R. 2019, AJ, 158, 194

(ref: owen99) Owen, T., Mahaffy, P., Niemann, H. B., et al. 1999, Nature, 402, 269

(ref: lperez16sci) Pérez, L. M., Carpenter, J. M., Andrews, S. M., et al. 2016, Science, 353, 1519

(ref: perezbecker11) Perez-Becker, D. & Chiang, E. 2011, ApJ, 735, 8

(ref: persson14) Persson, M. V., Jørgensen, J. K., van Dishoeck, E. F., & Harsono, D. 2014, A&A, 563, A74

(ref: JPLdb) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883

(ref: pietu07) Piétu, V., Dutrey, A., & Guilloteau, S. 2007, A&A, 467, 163

(ref: pontoppidan11) Pontoppidan, K. M., Blake, G. A., & Smette, A. 2011, ApJ, 733, 84

(ref: pontoppidan14) Pontoppidan, K. M., Salyk, C., Bergin, E. A., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, C. Dullemond, & T. Henning (Univ. of Arizona Press, Tucson), 363–386

(ref: ramsey2019) Ramsey, J. P. & Clarke, D. A. 2019, MNRAS, 484, 2364

(ref: roberts02) Roberts, H., Fuller, G. A., Millar, T. J., Hatchell, J., & Buckle, J. V. 2002, A&A, 381, 1026

(ref: robitaille06) Robitaille, T. P., Whitney, B. A., Indebetouw, R., Wood, K., & Denzmore, P. 2006, ApJS, 167, 256

(ref: rubin19) Rubin, M., Altwegg, K., Balsiger, H., et al. 2019, MNRAS, 489, 594

(ref: sakai14) Sakai, N., Oya, Y., Sakai, T., et al. 2014a, ApJL, 791, L38

(ref: sakai14nat) Sakai, N., Sakai, T., Hirota, T., et al. 2014b, Nature, 507, 78

(ref: salinas16) Salinas, V. N., Hogerheijde, M. R., Bergin, E. A., et al. 2016, A&A, 591, A122

(ref: salyk11) Salyk, C., Pontoppidan, K. M., Blake, G. A., Najita, J. R., & Carr, J. S. 2011, ApJ, 731, 130

(ref: schmalzl14) Schmalzl, M., Visser, R., Walsh, C., et al. 2014, A&A, 572, A81

(ref: schoier02) Schöier, F. L., Jørgensen, J. K., van Dishoeck, E. F., & Blake, G. A. 2002, A&A, 390, 1001

(ref: lamda) Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005, A&A, 432, 369

(ref: SS73) Shakura, N. I. & Sunyaev, R. A. 1973, A&A, 24, 337

(ref: tabone17) Tabone, B., Cabrit, S., Bianchi, E., et al. 2017, A&A, 607, L6

(ref: tafalla06) Tafalla, M., Santiago-Garcı́a, J., Myers, P. C., et al. 2006, A&A, 455, 577

(ref: taquet15) Taquet, V., López-Sepulcre, A., Ceccarelli, C., et al. 2015, ApJ, 804, 81

(ref: galario) Tazzari, M., Beaujean, F., & Testi, L. 2018, MNRAS, 476, 4527

(ref: tazzari17) Tazzari, M., Testi, L., Natta, A., et al. 2017, A&A, 606, A88

(ref: teague15) Teague, R., Semenov, D., Guilloteau, S., et al. 2015, A&A, 574, A137

(ref: tobin13) Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2013, ApJ, 771, 48

(ref: vandermarel14) van der Marel, N., van Dishoeck, E. F., Bruderer, S., & van Kempen, T. A. 2014, A&A, 563, A113

(ref: radex) van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck, E. F. 2007, A&A, 468, 627

(ref: vandishoeck98) van Dishoeck, E. F. & Blake, G. A. 1998, ARA&A, 36, 317

(ref: vanthoff20) van ’t Hoff, M. L. R., Harsono, D., Tobin, J. J., et al. 2020, ApJ, 901, 166

(ref: vanthoff18a) van ’t Hoff, M. L. R., Persson, M. V., Harsono, D., et al. 2018a, A&A, 613, A29

(ref: vanthoff18b) van ’t Hoff, M. L. R., Tobin, J. J., Harsono, D., & van Dishoeck, E. F. 2018b, A&A, 615, A83

(ref: zadelhoff01) van Zadelhoff, G. J., van Dishoeck, E. F., Thi, W. F., & Blake, G. A. 2001, A&A, 377, 566

(ref: visser09) Visser, R., van Dishoeck, E. F., Doty, S. D., & Dullemond, C. P. 2009, A&A, 495, 881

(ref: kida) Wakelam, V., Herbst, E., Loison, J.-C., et al. 2012, ApJS, 199, 21

(ref: willacy07) Willacy, K. 2007, ApJ, 660, 441

(ref: wc11) Williams, J. P. & Cieza, L. A. 2011, ARA&A, 49, 67

(ref: wilson94) Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191

(ref: corates) Yang, B., Stancil, P. C., Balakrishnan, N., & Forrey, R. C. 2010, ApJ, 718, 1062

(ref: yen17) Yen, H.-W., Koch, P. M., Takakuwa, S., et al. 2017, ApJ, 834, 178

(ref: yoneda16) Yoneda, H., Tsukamoto, Y., Furuya, K., & Aikawa, Y. 2016, ApJ, 833, 105

(ref: moyu17) Yu, M., Evans, Neal J., I., Dodson-Robinson, S. E., Willacy, K., & Turner, N. J. 2017, ApJ, 841, 39

(ref: kzhang20) Zhang, K., Schwarz, K. R., & Bergin, E. A. 2020, ApJL, 891, L17

# Undetected molecular lines

|  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|
| Molecular line transition | Frequency | $E_{\rm up}$ | $\log_{10} A_{\rm ul}$ | Beam$^{a}$ | Noise |
|  | (GHz) | \(K\) | (s$^{-1}$) | ($'' \times '', ^{\circ}$) | (mJy bm$^{-1}$) |
| $J=5-4$ | 217.10450 | 31.26 | $-3.28$ | $0.13 \times 0.10$, 32 | 1.6 |
| $N_J = 2_{3/2} - 1_{1/2}, F_1,F = 1,1-0,1$ | 217.27768 | 10.88 | $-4.24$ | $0.08 \times 0.07$, 78 | $\sim5$ |
| $J=5 - 4$ | 231.22069 | 33.29 | $-3.60$ | $0.12 \times 0.10$, 32 | 1 |
| $N_J=3_4 - 4_3$ | 267.19774 | 19.93 | $-6.15$ | $0.13 \times 0.10$, 3 | 1.3 |

Table notes:

There are additional molecular lines present in our ALMA spectral set ups that are not detected in our data. Table [\[tbl:upperlims\]](#tbl:upperlims) lists these lines. The line is weakly apparent in the visibilities and could be identified in a spectrum taken over a large area ($> 10$ beams). However, it cannot be imaged properly even including some tapering. The noise level per channel is higher than the other lines because low-level permeates the spectral cube. This implies that most of the emission is filtered out in our long baseline data. SO $N_{J} = 3_4 - 4_3$ is likely not detected because of its low Einstein A coefficient; for the physical conditions that produce the detected SO $5_6 - 4_5$ line, the strength of the $3_4 - 4_3$ line would be a factor of 100 weaker.

# Molecular lines: vibrational transitions

![](aa38697_appfig1.pdf)

Our spectral cubes also contain the HCN bending mode ($\upsilon_2 = 1$) rotational transitions at 265.8527 GHz and 267.1993 GHz, as shown in Fig. [14](#fig:rovibspectra). These lines are not detected toward TMC1A. They do, however, provide a constraint on the physical structure of TMC1A disk due to their high upper energy level ($E_{\rm up} \sim 1000$ K). The peak flux density of each line has a 0.9 mJy upper limit. For comparison, we also present the fundamental vibrational CO lines taken with CRIRES on the VLT (cite: herczeg11) in the same figure with upper energy levels $\sim 3000$ K. These spectra are taken with a 0.2$\ensuremath{''}$ slit at a $PA$ of 64$^{\circ}$, which is along the major axis of the Keplerian disk. A deep absorption is apparent at the systemic velocity of the coadded  $\upsilon=1-0$ and  $v=1-0$ spectra, and is similar to what we see in the rotational spectra in the ground vibrational state (Fig. [3](#fig:rotspectra)). The broad blue absorption in the CO fundamental vibrational line is, meanwhile, a strong indication of a disk wind (cite: calvet92; pontoppidan11; bast11; herczeg11).

In order to further constrain the HCN $\upsilon_2=1$ emission, the weighted average of the two spectra ($e$,$f$) is also shown in black in Fig. [14](#fig:rovibspectra). The stacked spectrum shows tantalizing features of beam diluted vibrational HCN emission. We expect that the emission should follow the  $\upsilon=1-0$ line profile as the red-shifted emission ($> 8$ km s$^{-1}$) comes from the hot surface layer of the disk instead of the disk wind (cite: herczeg11). Therefore, we believe that the absorption feature in the stacked HCN spectrum and emission near the systemic velocity could be firmly detected with deeper observations.

</paper>

Write the methods card for this paper.