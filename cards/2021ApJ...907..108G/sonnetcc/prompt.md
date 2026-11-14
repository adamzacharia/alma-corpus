# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2021ApJ...907..108G\sonnetcc\reply.txt

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
 "bibcode": "2021ApJ...907..108G",
 "title": "Identification of Methyl Isocyanate and Other Complex Organic Molecules in a Hot Molecular Core, G31.41+0.31",
 "year": 2021,
 "journal": "The Astrophysical Journal",
 "first_author": "Gorai, Prasanta",
 "n_authors": 7,
 "arxiv_id": "2011.02226",
 "doi": "10.3847/1538-4357/abc9c4",
 "alma_projects_linked_by_archive": [
  "2015.1.01193.S"
 ]
}
```

Paper text:
<paper>
# Identification of Methyl Isocyanate and Other Complex Organic Molecules in a Hot Molecular Core, G31.41+0.31

## Abstract

G31.41+0.31 is a well known chemically rich hot molecular core (HMC). Using Band 3 observations of Atacama Large Millimeter Array (ALMA), we have analyzed the chemical and physical properties of the source. We have identified methyl isocyanate (CH$_3$NCO), a precursor of prebiotic molecules, towards the source. In addition to this, we have reported complex organic molecules (COMs) like methanol (CH$_3$OH), methanethiol (CH$_3$SH), and methyl formate (CH$_3$OCHO). Additionally, we have used transitions from molecules like HCN, HCO$^+$, SiO to trace the presence of infall and outflow signatures around the star-forming region. For the COMs, we have estimated the column densities and kinetic temperatures, assuming molecular excitation under local thermodynamic equilibrium (LTE) conditions. From the estimated kinetic temperatures of certain COMs, we found that multiple temperature components may be present in the HMC environment. Comparing the obtained molecular column densities between the existing observational results toward other HMCs, it seems that the COMs are favourably produced in the hot-core environment ($\sim 100$ K or higher). Though the spectral emissions towards G31.41+0.31 are not fully resolved, we find that CH$_3$NCO and other COMs are possibly formed on grain/ice phase and populate the gas environment similar to other hot cores like Sgr B2, Orion KL, and G10.47+0.03, etc.

# Introduction

Chemistry in high-mass star-forming regions (HMSFRs) is very rich, and it has a significant impact on the evolution of the Interstellar Medium (ISM) (cite: vand98; tan14). Over the years, numerous complex organic molecules (COMs) were identified in hot molecular cores (HMCs) (cite: herb09). Hot molecular cores are compact, hot, dense, and associated with luminous infra-red (IR) or with ultra-compact (UC) HII regions (cite: cesa10; bonf17). To date, a number of HMCs were discovered (cite: Kurt00), while a limited number of circumstellar disks were found around B type stars such as the disks in Cepheus A HW2 (cite: pate05), HH80-81 (cite: gira18) and the disk in the late-O-type star, IRAS 13481-6124 (cite: krau10). Their dust emission has identified the majority of these disk structures. However, they are also associated with molecular emission. Complex organic molecules, CH$_3$CN, was observed in Cepheus A HW2 and P-V diagram of CH$_3$CN transitions used to understand the velocity gradient that explains gravitationally bound rotational motion.

Many complex physical processes, such as accretion, infall, and outflows are present in the earliest phase of HMSFRs during their various evolutionary stages. Therefore the chemistry of these regions is used as a diagnostic tool to examine the nature of them. Complex organic molecules are omnipresent in the HMCs and show rich chemistry. Chemistry of these regions plays an essential role, which helps trace the physical parameters associated with particular regions, such as density, temperature, and ionization rate. Since the abundances of chemical species are time dependent and collapsing time of a HMSFR is short, a comparison of observed abundance with modeling can be used to trace the chemical diversity of those region. For HMCs, both grain-surface and gas-phase processes are efficient. Various desorption mechanisms, such as thermal (active in hot core temperature) and non-thermal desorption (dominant at low temperature) processes help release the grain surface species to the gas phase.

G31.41+0.31 (hereafter G31) is an HMC that is thought to be located at a 7.9 kpc distance from the Earth (cite: chur90). This source has a luminosity of about $\rm{\sim 3\times10^{5}}$$L_\odot$. It is supposed to be heated by O and B type stars (cite: cesa10; belt09). Previous studies (cite: cesa11; cesa17) found some hints of the existence of disk in G31.41+0.31. (cite: osor09) performed detailed modeling of the SED of dust to obtain the physical parameters of the star and the core. Using these parameters, they estimated the ammonia emission and compared it with the VLA observation having a sub-arcsec resolution of G31. They obtained the mass of the central star $\sim$ 20-25 M$_{\odot}$ and significantly higher mass (1400-1800 M$_{\odot}$) of the envelope by considering envelope size, R$_{env}$ = 30000 AU. Recently, (cite: belt18) observed G31 with ALMA at $1.4$ mm resolved G31 into two cores, namely main and NE. They observed the physical properties such as accelerating infall, rotational spin up, red-shifted absorption, and possible outflow directions associated with this source. The UC HII region is situated at the North-East side of G31 and separated by $\sim 5^{''}$ from the main core (cite: cesa10). The main core’s estimated mass is 120 M$_{\odot}$, which is based on old distance 7.9 kpc (cite: belt18). However, new parallax measurement suggests that G31 is located at a distance of 3.7 kpc. Therefore the luminosity of the source would be $\rm{\sim 4\times10^{4}}$$L_\odot$ and estimated mass of the main core ($M_c$) of G31 is $\sim$ 26 M$_{\odot}$ (cite: ried19; esta19; belt19). However, this estimation should be considered the lower limit because high angular resolution might have filtered spatially extended emission (cite: belt19).

A wide variety of species (around $70$) were already identified in G31. The simplest form of sugar, glycolaldehyde (HOCH$_2$CHO), was observed in G31 with IRAM PdBI at $1.4$, $2.1$, and $2.9$ mm observations (cite: belt09). This is the earliest evidence of the presence of sugar outside our Galactic center. A large number of COMs such as methanol (CH$_3$OH), methyl cyanide (CH$_3$CN), ethanol (C$_2$H$_5$OH), ethyl cyanide (C$_2$H$_5$CN), methyl formate (CH$_3$OCHO), dimethyl ether (CH$_3$OCH$_3$), ethylene glycol (CH$_2$OH)$_2$, and acetone (CH$_3$COCH$_3$) had already been identified in G31 by using both single dish (IRAM 30m, GBT) and Submillimeter Array (SMA) observations (cite: rivi17; isok13).

The presence of a large number of COMs, including branched chain molecule might be an indication of the existence of prebiotic molecules and essential building blocks of life in space (cite: bell14; chak15; maju15; sil18; sahu20). (cite: goes15) detected various COMs (e.g., methyl isocyanate, formamide, glycolaldehyde, ethylamine etc.) in a Jupiter family comet, 67P/Churyumov-Gerasimenko (67P/C-G). Among them, methyl isocyanate (CH$_3$NCO) was found to be relatively abundant as compared to other observed COMs. However, (cite: altw17) reported the resulting CH$_3$NCO abundance as an upper limit. The presence of CH$_3$NCO in space is supposed to be important because of its peptide-like bond. Detection of CH$_3$NCO was first claimed by (cite: half15) in a massive hot molecular core, Sgr B2. It was also detected in Orion KL (cite: cern16). It has recently been observed in G10.47+0.03 (cite: gora20). Here, in G31, we have identified some transitions of this species.

Methanethiol ($\rm{CH_3SH}$) is a sulfur analog of methanol, where the S atom is replaced by an O atom. To date, this is the only complex sulfur-bearing species (having 6 atoms) which has been firmly detected in the ISM. Tentative identification of higher-order thiols, ethanethiol ($\rm{C_2H_5SH}$) has been reported in Sgr B2N (cite: mull16). Identification of $\rm{CH_3SH}$ was also reported toward the Galactic center (cite: Link79; mull16), Orion KL (cite: kole14) and chemically rich massive hot core, G327.3-6 (cite: gibb00) and 67P/C-G comet (cite: calm16).

In this work, we present the interferometric (ALMA archival data) observation towards G31. We report first detection of CH$_3$NCO and CH$_3$SH in G31 and discuss the kinematics associated with this HMC. We also discuss the chemistry of other complex species in this source. The remainder of this paper is summarized as follows. In Section 2, we describe observational details and data reduction processes. All results are presented and discussed in Section 3 and Section 4 respectively. Finally, we draw our conclusion in Section 5.

# ALMA archival data

In this paper, we used Atacama Large Millimeter/submillimeter Array (ALMA) cycle 3 archival data (#2015.1.01193.S) to study COMs in G31. The observation was performed during June, 2016 using forty 12 m antennas. The shortest and the longest baseline was $15$ m, and $783.0$ m, respectively, and synthesized beam size was $\sim$ 1.1 $''$. Four spectral windows (86.559-87.028 GHz, 88.479-88.947 GHz, 98.977-99.211 GHz, and 101.076-101.545 GHz) of width $~0.47$ GHz was set up to observe the target source, G31; phase center was $\alpha$(J2000) = 18$^h$47$^m$34.309$^s$, $\delta$ =-1$^{o}$12$'$46.00$''$. The flux calibrator was Titan, the phase calibrator was J1824+0119, and the bandpass calibrator was J1751+0939. The data cube has a spectral resolution of 244 kHz ($\sim$0.84 km s$^{-1}$) with a synthesized beam of $\sim$ $\rm{1.19^{''}\times 0.98^{''}}$ having position angle (PA) $\sim$ 76$^{o}$. The systematic velocity of the source is known to be $\sim$ $97$ km s$^{-1}$ (cite: cesa10; rivi17). Image analysis was done using CASA 4.7.2 software (cite: mcmu07). Implementing the first-order baseline fit and by using ‘uvcontsub’ command available in the CASA program, we separated each spectral window into two data: continuum and line emission. The identification of lines of all the observed species presented in this paper is carried out using CASSIS (This software was developed by IRAP-UPS/CNRS, http://cassis.irap.omp.eu) together with the spectroscopic database ‘Cologne Database for Molecular Spectroscopy’ (cite: mull01; mull05) [^1] and Jet Propulsion Laboratory (cite: pick98)[^2] database.

# Results

## Continuum emission and $\rm{H_2}$ column density estimation

![](G31-cont.pdf)

The continuum image of G31 at $94.3$ GHz is shown in Figure [1](#fig:cont). The synthesized beam size of the continuum is $\rm{1.19^{''}\times 0.98^{''}}$ with PA $\sim$76$\degree$. Using two-dimensional Gaussian fitting over the dust continuum emission, we obtained the deconvolved size of G31 $\sim 0.90 '' \times 0.68''$ .

Assuming the distance to the source $7.9$ kpc, we obtained a source size $\sim 7110 \times5372$ AU. This source size changes to $3330 \times 2516$ AU, while $\sim 3.7$ kpc distance is used.

(cite: belt18) observed G31 with an angular resolution of 0.22$''$ and found the continuum brightness temperature $\sim$132 K, which is comparable to the dust temperature ($\sim 150$ K). This suggests that the dust continuum emission observed at $217$ GHz is optically thick. (cite: rivi17) also observed that dust opacity is high ($\tau$ = 2.6) at 220 GHz.

We have observed peak intensity of the continuum is $\sim$158 mJy/beam which corresponds to a brightness temperature $18$ K (using Rayleigh-Jeans approximation, 1 Jy/beam $\equiv$ 118 K). This estimation is much smaller than the assumed dust temperature of 150 K, this indicates a small optical depth ($\rm{\tau_\nu}$) $\sim$ 0.12 (using $T_{mb}=T_d(1-exp(-\tau_\nu))$.

It should be noted that in our observation, the source was not resolved or at best marginally resolved; therefore, the estimated brightness temperature could be underestimated.. After adding the beam dilution correction for the unresolved source, the brightness temperature is estimated to be $\sim$36 K. Considering this value of brightness temperature; dust emission remains optically thin ($\tau_\nu \sim 0.24$). Due to the collapsing envelope, we can expect higher density and temperature toward the inner region than the outer envelope of this source. Since dust density is higher towards the inner region, opacity would be higher, as observed by (cite: belt18). It may reduce the true line intensity of the observed transitions. However, due to the lower angular resolution, our present data would not provide further details about the dust opacity of the whole region of G31.

Assuming the dust continuum to be optically thin, flux density can be written as,

$$\begin{equation}
S_\nu^{beam} =\Omega_{beam} \tau_\nu B_\nu (T_d),
\end{equation}$$ where $\Omega_{beam}$=$\frac{\pi}{4ln2}$ $\times \theta_{major} \times \theta_{minor}$ is solid angle of the synthesized beam, S$_\nu^{beam}$ is the peak flux density measured in unit of mJy/beam, $\tau_\nu$ is optical depth, and $\rm{T_d}$ is dust temperature and $\rm{B_\nu(T_d)}$ is Planck function (cite: whit92). Optical depth can be expressed as, $$\begin{equation}
 \tau_\nu =\rho_d\kappa_\nu L,
\end{equation}$$ where $\rho_d$ is the mass density of dust, $\kappa_\nu$ is the mass absorption coefficient, and L is the path length. Using the dust to gas mass ratio ($Z$), the mass density of the dust can be written as, $$\begin{equation}
\rho_d = Z\mu_H\rho_{H_2}=2Z{  \mu_H}N_{H_2}m_H/L,
\end{equation}$$ where $\rho_{H_2}$ is the mass density of hydrogen molecule, $\rm{N_{H_2}}$ is the column density of hydrogen, $\rm{m_H}$ is the hydrogen mass, and $\rm{\mu_H}$ is the mean atomic mass per hydrogen atom. Here, we used $Z=0.01$, $\mu_H=1.41$ (cite: cox00), and dust temperature 150 K. Two dimensional Gaussian fitting of the continuum yields a peak intensity (S$_\nu^{beam}$) of dust continuum of 158.4 mJy/beam and integrated flux (F$_\nu$) of 242.4 mJy. RMS noise of the continuum map was found to be $5$ mJy/beam. From the above equations column density of molecular hydrogen can be written as,

$$\begin{equation}
N_{H_2} = \frac{S_\nu^{beam} /\Omega_{beam}}{2\kappa_\nu B_\nu(T_d)Z\mu_H m_H}.
\end{equation}$$

According to the interpolation of the data presented in (cite: osse94), we estimated the mass absorption coefficient. By considering a thin ice condition, here, we obtained the mass absorption coefficient at 94 GHz ($3187.90$ micron) $\sim 0.176$ cm$^2$/g. By using equation 4, total hydrogen column density of G31 source is $\sim{\rm1.53\times10^{25}}$ cm$^{-2}$.

## Line analysis, molecular emission and spectral fitting

Observed spectra are obtained within the circular region having a diameter of 1.1$''$ centered at RA (J2000) = 18$^h$47$^m$34.309$^s$, Dec (J2000) =-1$^{o}$12$'$46.00$''$. Line parameters of all the observed transitions are obtained using a single Gaussian fit. From fitting, we have estimated the line width (FWHM), LSR velocity, and the integrated intensity. All the line parameters of observed molecules such as molecular transitions (quantum numbers) along with their rest frequency ($\nu$), line width (FWHM, $\Delta V$), integrated intensity ($\rm{\int T_{mb}dV}$), upper state energy (E$_u$), $\rm{V_{LSR}}$, and transition line intensity (S$\mu^{2}$, where S is the transition line strength and $\mu$ is the dipole moment) are presented in Table [\[table:line-parameters\]](#table:line-parameters). Overall, we have observed a broad line width ($\ge$ 5 km s$^{-1}$) and all lines are at the center around the systematic velocity of the source ($\rm{\sim97\ km\ s^{-1}}$) (see Table [\[table:line-parameters\]](#table:line-parameters)). In the Appendix, we have presented observed and Gaussian fitted spectra (see Figures [11](#Gfit-CH3OH)-[15](#Gfit-other)).

![](absorption.pdf)

### Simple Molecules

We have observed SO$_2$ ($86.63908$ GHz) and H$_2$CO ($101.33299$ GHz) in G31. We have also identified some simple molecules such as HCN, H$^{13}$CO$^{+}$, and SiO, which are widely used to trace various physical processes of star-forming regions. The observed spectral profile of H$^{13}$CO$^{+}$ shows red-shifted absorption, which is shown in Figure [2](#abs-sp)a. This is a signature of inverse P-Cygni profile. This suggests that the source has an infall nature. Observed emission of SiO and HCN traces the outflows in this source.

Figure [2](#abs-sp)b shows the observed spectral profile of HCN. Here, we have identified three hyperfine transitions of HCN (F = 1$\rightarrow$1, 2$\rightarrow$1, and 1$\rightarrow$0 hyperfine components of the J=1$\rightarrow$0 transition, see Table [\[table:absorption\]](#table:absorption)). Three hyperfine transitions of HCN are appeared in absorption and blended together. These three absorption lines together resulting in a broad feature. HCN traces the outflow associated with the source. The observed transitions of both HCN and H$^{13}$CO$^{+}$ are found to be optically thick.

Here, we have also detected one transition of SiO at 86.84696 GHz (J=2$\rightarrow$1). SiO shows the absorption feature towards the center of the dust continuum and emission profile at all other positions. (cite: belt18) also observed similar spectral feature of SiO (5-4, 217.10498 GHz). SiO traces outflows associated with this source.

### Complex Organic Molecules

We have observed numerous COMs that were previously reported in G31 (cite: rivi17). Additionally, for the first time in this source, we are reporting the detection of two new molecules, methyl isocyanate (CH$_3$NCO) and methanethiol (CH$_3$SH). Altogether, we have identified six transitions of CH$_3$NCO with the ground vibrational state ($v_b=0$) and one transition with $v_b=1$. Among the six transitions of CH$_3$NCO, one transition (86.86674 GHz) is blended with ethylene glycol (confirmed from LTE modeling).

We have identified three different peaks of CH$_3$SH, where each peak contains multiple transitions. These transitions are reported in Table [\[table:line-parameters\]](#table:line-parameters). We are unable to separate these observed transitions. Because of closely spaced transitions, it is difficult to distinguish two or more different transitions from a single observed peak of CH$_3$SH. Thus, to obtain the observed line parameters of CH$_3$SH transitions, we have fitted multiple Gaussian components to the observed spectra. For multiple Gaussian fitting, we have used fixed values of velocity separation and expected line intensity ratio. Only FWHM is kept as a free parameter. This method works well in the observed spectral profile 1 and 3 around 101.139 GHz and 101.167 GHz of CH$_3$SH, where there are two transitions around each profile (see Table [\[table:line-parameters\]](#table:line-parameters)). Two-component Gaussian fitting corresponding to the two transitions are used to fit those spectral profiles (see Table [\[table:line-parameters\]](#table:line-parameters) and Figure [14](#Gfit-ch3sh)). However, this method does not work well for spectral profile 2, around 101.159 GHz, where four transitions are present. The four transitions can be classified into two classes based on their expected peak intensity (equivalent to S$\mu^{2}$) and E$_{up}$. The expected intensity ratio between these four transitions is 1:0.58:0.58:0.58. We have used two-component Gaussian fitting corresponding to the two classes of transitions, one for 101.15933 GHz (S$\mu^{2}$ =4.96, E$_{up}$=31.26 K) transition and another component for the other three transitions, 101.15999 GHz, 101.16066 GHz, 101.16069 GHz (S$\mu^{2}$ = 2.90, E$_{up}$ = 52.55 K) around 101.159 GHz line profile. For the fitting, we have used 1:1.74 (1.74 is the sum of intensity of three transitions) intensity ratio for these two components. Therefore, resultant Gaussian corresponding to the three transitions can be obtained via this method; as these transitions are equally intense and have similar excitation temperature, the area under Gaussian can be divided by three to get the contribution from each transition multiplets. We have used only one transition from these multiplets for the rotation diagram of CH$_3$SH since the integrated area of all these three transitions are the same and have similar upper state energy (E$_{up}$). Therefore, these fitting results are used meaningfully to estimate rotational temperature using the rotation diagram method. Obtained line parameters are further used in the rotation diagram of CH$_3$SH. For the rotation diagram of CH$_3$SH, we use 101.13915 GHz, 101.13965 GHz, 101.15933 GHz, 101.1599 GHz, 101.16715 GHz, and 101.16830 GHz transitions. Gaussian fits of CH$_3$SH observed spectra are provided in Figure [14](#Gfit-ch3sh).

![](integrated-maps.pdf)

We also have identified the presence of two abundant COMs methanol and methyl formate in this source. Methanol is one of the most abundant COMs in star-forming regions. Here, we have identified seven transitions of CH$_3$OH with different upper state energy in the ALMA band 3 regions. We have also identified CH$_3$OCHO transitions with a wide range of upper-level energies ($17-207$ K), which are listed in Table [\[table:line-parameters\]](#table:line-parameters). The integrated intensity maps of some unblended transitions of SO$_2$, H$_2$CO, CH$_3$SH, CH$_3$OH, CH$_3$OHCO, and CH$_3$NCO are shown in Figures [\[int-int\]](#int-int)(a-f) where continuum is overlaid on the integrated intensity map, and all other maps correspond to different frequencies are given in the Appendix (see Figures [18](#int-int-ch3oh)-[21](#int-int-ch3sh)). Using local thermodynamic equilibrium modeling and comparing with the integrated intensities of observed molecular transitions, we found that various transitions of CH$_3$OH, CH$_3$NCO, and CH$_3$OCHO are optically thin.

For example, in LTE and optically thin condition, the expected line ratio between the 87.01608 GHz and 86.68019 GHz transitions of CH$_3$NCO is 1.6 while the observed intensity (brightness temperature) ratio is 1.44. This suggests that these two lines are optically thin. Similarly for 86.78078 GHz and 86.68019 GHz transitions of CH$_3$NCO, the observed intensity ratio between these two lines is 1.35, and the expected line ratio is 1.30. For the 101.12685 GHz and 101.46980 GHz transitions of CH$_3$OH, the observed intensity ratio is 2.3, which is consistent with the expected LTE line ratio of 2.2. For of CH$_3$OCHO, the observed line ratio between 88.68688 GHz and 88.85160 GHz transition is 4, which is similar to the observed integrated intensity ratio 3.7. The similarity between the expected and observed line ratios of these transitions suggest that they are optically thin.

## Rotation diagram analysis: estimation of gas temperature

We have detected multiple transitions of CH$_3$OH, CH$_3$OCHO, CH$_3$SH, and CH$_3$NCO, with different $\rm{E_{u}}$. Thus, we employed the rotation diagram analysis to obtain the rotational temperatures. We performed the rotation diagram analysis by assuming the observed transitions to be optically thin and are in Local Thermodynamic Equilibrium (LTE). For optically thin lines, column density can be expressed as (cite: gold99), $$\begin{equation}
\frac{N_u^{thin}}{g_u}=\frac{3k_B\int{T_{mb}dV}}{8\pi^{3}\nu S\mu^{2}},
\end{equation}$$ where g$_u$ is the degeneracy of the upper state, $\rm{k_B}$ is the Boltzmann constant, $\rm{\int T_{mb}dV}$ is the integrated intensity, $\nu$ is the rest frequency, $\mu$ is the electric dipole moment, and S is the transition line strength. Under LTE conditions, the total column density can be written as,

$$\begin{equation}
\frac{N_u^{thin}}{g_u}=\frac{N_{total}}{Q(T_{rot})}\exp^{-E_u/k_{B}T_{rot}},
\end{equation}$$ where $T_{rot}$ is the rotational temperature, E$_u$ is the upper state energy, $\rm{Q(T_{rot})}$ is the partition function at rotational temperature. The equation 6 can be rearranged as, $$\begin{equation}
log\Bigg(\frac{N_u^{thin}}{g_u}\Bigg)=-\Bigg(\frac{log\ e}{T_{rot}}\Bigg)\Bigg(\frac{E_u}{k_B}\Bigg)+log\Bigg(\frac{N_{total}}{Q(T_{rot})}\Bigg).
\end{equation}$$ Equation 7 shows that there is a linear relationship between E$_u$ and $\rm{log(N_u/g_u)}$. Two parameters, column density and rotational temperature can be obtained by fitting a straight line to the values of $\rm{log(N_u/g_u)}$ plotted as a function of E$_u$, where $\rm{N_u/g_u}$ is obtained from the observations through equation 5.

Rotational diagrams of methyl isocyanate, methanol, methanethiol, and methyl formate are presented in Figure [4](#rot-diagram). For CH$_3$OCHO, we have several transitions, but we do not see two components. Hence we fit all the data points with a line, which are not aligned. Though we did not find a very good fitting, the obtained rotational temperature of methyl formate $\sim 162$ K is consistent with the previously measured value in this source for the same molecule (cite: belt05; rivi17). We have obtained a rotational temperature of 76 K for CH$_3$SH and 48 K for CH$_3$NCO. The rotational diagram analysis suggests two temperature components of methanol, one is a cold component, and another is a hot component. Cold component (solid black line, see Figure [4](#rot-diagram)b) temperature is obtained 33 K. In contrast, hot component (solid blue line, see Figure [4](#rot-diagram)b) temperature is 181 K. Rotational diagram of CH$_3$OH suggests that the transitions associated with the higher $\rm{E_{u}}$ transitions (86.61557 GHz, 86.90291 GHz, 88.59478 GHz, 88.93997 GHz; hot component) are mainly arising from the hot gas surrounding the G31. In contrast, the emissions associated with the lower $E_{u}$ (101.12685 GHz, 101.29341 GHz,101.46980 GHz; cold component) transitions are from the cold region of the HMC. However, due to our observation’s lower angular and spatial resolution, we marginally resolved these transitions. Therefore, it is not possible to provide a clear insight into the spatial distribution of methanol in this source.

The error bars (vertical red bars) in Figure [4](#rot-diagram) are the absolute uncertainty in a log of (N$_u$/g$_u$), and this arises from the error of the observed integrated intensity that we measured using a single Gaussian fitting to the observed profile of each transition. The integrated intensities with their uncertainties of all observed transitions are provided in Table [\[table:line-parameters\]](#table:line-parameters). Our estimated rotational temperatures for methyl formate and the hot component of methanol are similar to the typical hot core temperature. On the other hand, methyl isocyanate and the cold component of methanol have lower rotational temperatures (33-48 K). However, due to poor angular resolution, we could not provide further details about these two temperature components’ spatial distribution.

To obtain the molecular column density of the observed chemical species, we used LTE modeling with CASSIS. For this modeling, we used the estimated rotational temperature discussed above. We calculated beam average column density (N$_b$), where the effect of beam dilution was not taken into consideration. For the model, we used five parameters; (i) column density, (ii) excitation temperature (T$_{ex}$), (iii) line width ($\Delta$V), (iv) velocity (V$_{LSR}$), and (v) source size ($\theta_s$). To obtain the best fit with the observation, only column density was varied by keeping all other parameters (Tex, source size, FWHM, and hydrogen column density) fixed and we choose the best fitted-results when LTE model spectra are the same as the observed spectra. For LTE fitting, we used the source sizes for molecular emission similar to the deconvolved size as we obtained from 2D Gaussian fitting. Line width (FWHM) for molecular transitions are estimated from the Gaussian fitting of spectral profiles, and excitation temperature (Tex) is assumed to be $\sim$ 150 K, a typical hot core temperature. Fixed parameters are noted in Table [\[table:lte-para\]](#table:lte-para). We did not have a rotation diagram for all the species (e.g., SO$_2$, H$_2$CO) presented here. Thus, we followed the LTE model to derive the column density of all the species. We have also compared the column densities of CH$_3$OH, CH$_3$SH, CH$_3$NCO, and CH$_3$OCHO between rotation diagram analysis and LTE model (see Table [\[table:frac-abun\]](#table:frac-abun) and Section 3.6). Observed column densities and fractional abundances of all the species are presented in Table [\[table:frac-abun\]](#table:frac-abun). Abundances of all species are noted w.r.to H$_2$.

![](ch3nco-rev-rot.pdf)

![](ch3oh-rev-rot.pdf)

![](ch3sh-new-2020.pdf)

![](ch3ocho-rev-rot.pdf)

NOTES: $^{1}$ Spectral profile 1, $^{2}$ Spectral profile 2, $^{3}$ Spectral profile 3, $^{i}$ velocity with respect to 101.13915 GHz transition, $^{ii}$ velocity w.r.t 101.15933 GHz transition, $^{iii}$ velocity w.r.t 101.16715 GHz transition.

+:-------------------:+:----------------------------:+:--------------------:+:--------------------------:+:-------------------------:+:-------------------------:+:--------------------------:+
| Species             | G31.41+0.31,                                        | Sgr B2 (N)                 | Orion KL                  | G10.47+0.03               | Chemical Model             |
+---------------------+-----------------------------------------------------+----------------------------+---------------------------+---------------------------+----------------------------+
|                     | Column density                                      | Column density             | Column density            | Column density            | Column density             |
+---------------------+-----------------------------------------------------+----------------------------+---------------------------+---------------------------+----------------------------+
|                     | \[Abundance\]                                       | \[Abundance\]              | \[Abundance\]             | \[Abundance\]             | \[Abundance\]              |
+---------------------+-----------------------------------------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| 2-3                 | LTE cm Rotation Diagram                             |                            |                           |                           |                            |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$OH            | 1.84(19)\[1.2(-6)\]$^{*}$    | 2.94(19)\[1.92(-6)\] | 4.00(19)\[1.14(-5)\]$^{a}$ | 3.24(18)\[1.62(-6\]$^{f}$ | 9.0(18)\[1.8(-6)\]$^{m}$  | 7.56(19)\[2.10(-5)\]$^{n}$ |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$OCHO          | 6.50(18)\[4.25(-7)\]         | 4.30(18)\[2.81(-7)\] | 1.20(18)\[3.33(-7)\]$^{b}$ | 1.04(17)\[5.2(-8)\]$^{g}$ | 7.0(17)\[1.4(-7)\]$^{m}$  | 3.31(17)\[9.20(-8)\]$^{n}$ |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$NCO           | 7.22(17)\[4.72(-8)\]$^{*}$   | 1.58(16)\[1.04(-9)\] | 2.20(17)\[6.11(-8)\]$^{c}$ | 7.0(15)\[3.5(-9)\]$^{h}$  | 1.2(17)\[8.88(-9)\]$^{o}$ | 4.68(16)\[1.30(-8)\]$^{b}$ |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$SH            | 4.13(17)\[2.70(-8)\]         | 2.85(16)\[1.86(-9)\] | 3.40(17)\[9.44(-8)\]$^{a}$ | 2.0(15)\[1.0(-9)\]$^{i}$  | –                         | 1.33(16)\[3.70(-9)\]$^{a}$ |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| SO$_2$              | 2.88(18)\[1.88(-7)\]         |                      | 8.28(16)\[2.30(-8)\]$^{d}$ | 1.0(17)\[5.0(-8)\]$^{j}$  | 3.0(17)\[6.0(-8)\]$^{m}$  |                            |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| H$_2$CO             | 2.90(18)\[1.90(-7)\]         |                      | 1.82(17)\[5.06(-8)\]$^{e}$ | 1.5(17)\[7.5(-8)\]$^{k}$  | 3.0(18)\[6.0(-7)\]$^{m}$  |                            |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| SiO                 | 1.46(15)\[9.54(-11)\]$^{**}$ |                      | 4.32(15)\[1.20(-9)\]$^{d}$ | 5.4(14)\[2.7(-10)\]$^{l}$ | –                         |                            |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$SH/CH$_3$OH   | 0.0225                       | 0.0010               | 0.0082                     | 0.0006                    |                           | 0.0002                     |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$OCHO/CH$_3$OH | 0.3541                       | 0.1463               | 0.0292                     | 0.0321                    | 0.0778                    | 0.0044                     |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+
| CH$_3$NCO/CH$_3$OH  | 0.0393                       | 0.0005               | 0.0054                     | 0.0022                    | 0.0049                    | 0.0006                     |
+---------------------+------------------------------+----------------------+----------------------------+---------------------------+---------------------------+----------------------------+

\
$^{a}$(cite: mull16), $^{b}$(cite: bell16), $^{c}$(cite: bell17), $^{d}$(cite: higu15), $^{e}$(cite: bell13), $^{f}$(cite: favr15), $^{g}$(cite: favr11), $^{h}$(cite: cern16), $^{i}$(cite: kole14), $^{j}$(cite: terc18), $^{k}$(cite: espl13), $^{l}$(cite: schi01), $^{m}$(cite: rolf11),$^{n}$(cite: garr13), $^{o}$(cite: gora20)\
 

Orion KL ($\rm{N_{H_2}}$)= $\rm{2.0\times10^{24}}$cm$^{-2}$, Sgr B2(N) ($\rm{N_{H_2}}$)= $\rm{3.6\times10^{24}}$cm$^{-2}$, G10.47+0.03 ($\rm{N_{H_2}}$)= $\rm{5.0\times10^{24}}$cm$^{-2}$, G31.41+0.31 ($\rm{N_{H_2}}$)= $\rm{1.53\times10^{25}}$cm$^{-2}$\
$^{*}$ For hot component of methanol, column density is derived using higher value of excitation temperature T = 300 K. Using LTE, we have found opacities $\geqslant$1 for a few transitions of CH$_3$OH (86.68655 GHz, 86.68019 GHz, 86.78077 GHz, and 86.80502 GHz) and CH$_3$NCO (86.68019 GHz and 86.68655 GHz). Thus, the column density estimated for CH$_3$OH and CH$_3$NCO by using LTE should be considered as lower limit.\
$^{**}$ SiO column density and fractional abundance calculated in the outflowing gas measured at V$_{LSR}$ =94.1 km s$^{-1}$ by averaging over the box (7${''}$$\times$${7''}$) centered at ($\alpha$(J2000), $\delta$ (J2000)) = \[18$^h$47$^m$34.121$^s$, -1$^{o}$12$'$48.975$''$\].

## Radiative transfer modeling

Absorption studies are best-suited to trace the physical conditions (e.g., density, kinetic temperature) of the ISM because it is not induced by beam dilution as long as the absorbing layer is larger than the continuum source. Here, we used non-LTE modeling to derive excitation conditions and physical properties from these absorption features. For the non-LTE modeling, we use RADEX program (cite: vand07). The collisional rates were taken from LAMDA database and the spectroscopic constants were taken from JPL/CDMS catalog. In RADEX, we used the continuum background temperature (T$_c$) of 36 K, which corresponds to the peak brightness temperature of the 3.2 mm continuum by considering the beam dilution. For this modeling, we have used colum density $\rm{3.55 \times 10^{15} \ cm^{-2}}$, $\rm{8.92 \times 10^{15} \ cm^{-2}}$, and $\rm{1.18 \times 10^{15} \times cm^{-2}}$ for H$^{13}$CO$^{+}$, HCN, and SiO respectively. Figures [5](#contour-radiative-transfer)(a)-(c) shows the variation of radiation temperature of HCN (1-0), $\rm{H^{13}CO^{+}}$ (1-0), and SiO (2-1) respectively for a wide range of parameter space. Our parameter space consists of the number density of hydrogen (varies in between $\rm{10^3-10^7\ cm^{-3})}$ and kinetic temperature (varies in between 1-100 K). Figures [5](#contour-radiative-transfer)(a)-(c) shows the parameter space for the absorption features of HCN, $\rm{H^{13}CO^{+}}$, and SiO respectively. We have estimated the critical density of HCN (1-0), $\rm{H^{13}CO^{+}}$ (1-0), and SiO (2-1), which are 1.51$\times$10$^{6}$ cm$^{-3}$, 1.83$\times$10$^{5}$ cm$^{-3}$, and 2.26$\times$10$^{5}$ cm$^{-3}$ respectively. We have shown that for hydrogen density $\geq$ 1.0$\times$10$^{5}$ cm$^{-3}$, all these transitions are showing absorption features. If H$_2$ density is below the critical density, level populations are mostly governed by collisional excitation and de-excitation rather than Boltzmann distribution. . Thus these molecules might show emission even at T$\leq$T$_c$. The observed spectral profile of SiO is in line with this results. We found SiO emission at all positions except the source’s central region (where density is high, which is probably greater than critical density).

![](contour.pdf)

## Physical properties of the source

In this source, we obtained a temperature range 33 to 180 K. Hydrogen column density of this source is estimated $\sim{\rm1.53\times10^{25}}$ cm$^{-2}$. Various observed molecular emissions are discussed below.

### Infalling envelope

Infall nature was observed in G31 earlier by various authors (cite: gira09; gijo14; belt18). (cite: gira09) observed an inverse P-Cygni profile in G31 with low energy lines of C$^{34}$S (7-6). Recently, (cite: belt18) identified red-shifted absorption of H$_2$CO and CH$_3$CN and its isotopologues towards the dust continuum of the main core with different upper state energy. (cite: gijo14) observed various inversion transitions (2,2), (3,3), (4,4), (5,5) and (6,6) of ammonia by using Very Large Array (VLA) observations to understand the infall motion in G31. To explain the infall motion in G31, they used a different approach called the central blue spot which can be easily identified in the first-order moment maps. The central blue spot consists of blue-shifted emission in the first-order moment towards the zeroth-order moment map’s peak position. They found the central blue spot infall signature in all observed transitions of ammonia. In this work, we have detected one transition of H$^{13}$CO$^{+}$ (1-0) at frequency $86.75430$ GHz, which shows both absorption and emission nature (see Figure [2](#abs-sp)a). This is an inverse P-Cygni profile. The infall velocity can be estimated as the difference between systematic velocity and the velocity at the observed inverse P-Cygni profile’s absorption feature. The infall velocity of the source is obtained to be 4.5 km s$^{-1}$. This suggests that matter is infalling from the envelope towards the source’s central region, which is consistent with the earlier observations (cite: gira09; belt18).

### Molecular outflow

![](sio-emission.pdf)

Many authors previously studied molecular outflows associated with G31 (cite: cesa11; olmi96; belt18). SiO and $\rm{^{13}CO}$ revealed the presence of two molecular outflows: One in the East-West (E-W) direction and another one in the North-South (N-S) direction. SiO is an excellent tracer of shock and molecular outflow associated with the star-forming regions (cite: zapa09; leur14). (cite: belt18) showed average red-shifted and blue-shifted wings of SiO emission, which reveals three outflow directions associated with this source: E-W, N-S, and NE-SW. . Among these three outflow directions, N-S and E-W components are clearly present in our observation. However, NE-SW component is not very evident (see original Figure [7](#outflow-sio) and illustrated in Figure [10](#G31-diagram)). Channel maps of SiO emission is shown in Figure [6](#channel-maps-sio). The blue-shifted and red-shifted integrated emission of SiO along with the continuum, is depicted in Figure [7](#outflow-sio). The presence of HCN is widespread in diverse interstellar environments ranging from dark cloud to star-forming region and circumstellar envelope of a carbon-rich star (cite: snyd71; ziur86). HCN also traces molecular outflow in G31. The observed spectrum profile of HCN (see Figure [2](#abs-sp)b) is symmetric with respect to the systematic velocity of the source. However, the intensity of emission wings associated with the absorption profile is asymmetric. This may be due to the asymmetry in molecular distributions. Figure [8](#outflow-hcn) shows the red-shifted and blue-shifted integrated emissions of HCN overlaid on the continuum.

![](SiO-physical.pdf)

![](hcn-review.pdf)

| Parameters | SiO | HCN |
|:---|:--:|:--:|
| Distance from continuum position to outer contour (pc) |  |  |
| Red lobe (lr1) | 0.117 (0.055) | 0.118 (0.055) |
| Red lobe (lr2) | 0.087 (0.041) | – |
| Blue lobe1 (lb1) | 0.108 (0.051) | 0.09 (0.042) |
| Blue lobe2 (lb2) | 0.135 (0.063) | – |
| Typical outflow velocity: V$_{outflow}$ (km s$^{-1}$) |  |  |
| Red lobe | 33.0 | 40.0 |
| Blue lobe | 23.0 | 30.0 |
| Dynamical time: t$_{dyn}$ (yr) |  |  |
| Blue lobe | $\rm{4.59\times10^{3}}$ ($\rm{1.62\times10^{3}}$) | $\rm{2.87\times10^{3}}$ ($\rm{1.35\times10^{3}}$) |
|  | $\rm{5.74\times10^{3}}$ ($\rm{1.21\times10^{3}}$) | – |
| Red lobe | $\rm{3.47\times10^{3}}$ ($\rm{2.16\times10^{3}}$) | $\rm{2.90\times10^{3}}$ ($\rm{1.36\times10^{3}}$) |
|  | $\rm{2.58\times10^{3}}$ ($\rm{2.70\times10^{3}}$) | – |
| Average | $\rm{4.10\times10^{3}}$ ($\rm{1.92\times10^{3}}$) | $\rm{2.88\times10^{3}}$ ($\rm{1.36\times10^{3}}$) |
| Outflow mass ($\rm{M_\odot}$) |  |  |
| Blue lobe | 27 (6) | 12 (2.6) |
| Red lobe | 24 (5) | 55 (12) |
| Total | 51 (11) | 67 (14.6) |
| Momentum ($\rm{M_\odot}$ km s$^{-1}$) |  |  |
| Blue lobe | 619 (136) | 352 (77) |
| Red lobe | 790 (173) | 2213 (485) |
| Total | 1409 (309) | 2565 (562) |
| Kinetic energy ($\rm{L_\odot}$ yr) |  |  |
| Blue lobe | $\rm{7.1\times10^{3}}$ ($\rm{1.6\times10^{3}}$) | $\rm{5.3\times10^{3}}$ ($\rm{1.2\times10^{3}}$) |
| Red lobe | $\rm{1.3\times10^{4}}$ ($\rm{8.8\times10^{3}}$) | $\rm{4.4\times10^{4}}$ ($\rm{9.7\times10^{3}}$) |
| Total | $\rm{2.0\times10^{4}}$ ($\rm{1.0\times10^{4}}$) | $\rm{4.9\times10^{4}}$ ($\rm{1.1\times10^{4}}$) |
| Mass loss ($\rm{M_\odot}$ yr$^{-1}$) |  |  |
| Blue lobe | $\rm{5.2\times10^{-3}}$ ($\rm{4.1\times10^{-3}}$) | $\rm{4.1\times10^{-3}}$ ($\rm{1.9\times10^{-3}}$) |
| Red lobe | $\rm{7.9\times10^{-3}}$ ($\rm{2.1\times10^{-3}}$) | $\rm{1.9\times10^{-2}}$ ($\rm{8.9\times10^{-3}}$) |
| Total | $\rm{1.3\times10^{-2}}$ ($\rm{6.2\times10^{-3}}$) | $\rm{2.3\times10^{-2}}$ ($\rm{10.8\times10^{-3}}$) |
| Momentum loss ($\rm{M_\odot}$ km s$^{-1}$ yr$^{-1}$) |  |  |
| Blue lobe | 0.12 (0.09) | 0.12 (0.06) |
| Red lobe | 0.26 (0.07) | 0.76 (0.35) |
| Total | 0.38 (0.16) | 0.88 (0.41) |
| Energy loss ($\rm{L_\odot}$) |  |  |
| Blue lobe | 1.38 (1.10) | 1.84 (0.85) |
| Red lobe | 4.31 (3.63) | 15.26 (7.14) |
| Total | 5.69 (4.73) | 17.10 (7.99) |

\
Note: To estimate the SiO outflow physical parameters, we considered average value of red lobe (r$_r$=$\frac{lr1+lr2}{2}$) and blue lobe (r$_b$=$\frac{lb1+lb2}{2}$) and their corresponding average time scale of blue lobe and red lobe. We have calculated the lobe distance in arcsec and then convert into parsec by considering source distance 7.9 kpc. In parenthesis, we have noted the outflows parameters by considering the new distance 3.7 kpc of G31.

To obtain the outflow parameters, we estimated the outflow velocity as the maximum velocity of outflow emission with respect to the systematic LSR velocity ($97$ km s$^{-1}$). For the blue lobe and red lobe of SiO outflow, velocities are found to be $23$ km s$^{-1}$ and $33$ km s$^{-1}$. We estimated the dynamical timescale of outflow by using t$_{dyn}$ =$\frac{l(b,r)}{V_{max}(b,r)}$. For this, we calculate two different lengths (lb1, lb2) of the blue lobe and two lengths (lr1, lr2) for red lobes (see Figure [7](#outflow-sio)-[8](#outflow-hcn)). We obtained the average dynamical time scale of outflow $\sim$ $\rm{4\times10^{3}}$ years by considering the maximum velocity of SiO of the blue lobe and red lobe. The dynamical time scale of HCN outflow is obtained to be $\sim$ $\rm{3\times10^{3}}$ years. These values are in good agreement with the dynamical time scale of outflow of $^{12}$CO and SiO, as previously reported in G31 by (cite: cesa11) and (cite: belt18). For all individual positions, the different dynamical time scales for both blue and red lobe are presented in Table [\[table:outflow-parameters\]](#table:outflow-parameters). For HCN, we calculate the outflow parameters for one blue lobe (lb1) and one red lobe (lr1). To estimate the other outflow parameters such as mass, momentum, energy, mass loss, momentum loss, and energy loss per year, we used the formula mentioned in (cite: cabr90). To estimate the outflow parameters, we assumed same abundance ($\rm{1.0\times10^{-8}}$) and excitation temperature ($20$ K) of SiO (cite: code13) and HCN. All the outflow parameters are summarized in Table [\[table:outflow-parameters\]](#table:outflow-parameters). All these outflow parameters are in good agreement with the observed values of (cite: arya08).

In Figure [6](#channel-maps-sio), we have shown the channel maps of SiO emission associated with the HMC. This figure depicts that blue-shifted channels are distributed in the southwest region and red-shifted channels toward the south-east and north-east regions. Bipolar lobe morphology observed from 93.2 km s$^{-1}$ and 103.1 km s$^{-1}$ channels suggest wide-angle bipolar outflow. Integrated emission of SiO and HCN transition (Figures [7](#outflow-sio) and [8](#outflow-hcn)) shows that there is a clear outflow direction along the East-West direction. In the integrated emission, the red lobe of outflow is slightly tilted to the south-east. This may occur due to another outflow direction along the southwest-northeast direction. There is also an outflow in the N-S direction. Outflow of HCN along the N-S direction is wider (see Figure [8](#outflow-hcn)) as compared to the SiO outflow (see Figure [7](#outflow-sio)). This may be attributed to the excitation conditions and chemical origin of HCN. The estimated outflow is massive, 50 M$_\odot$ for SiO and 67 M$_\odot$ for HCN and the outflow is characterized as young (3-4$\rm{\times10^{3}}$ years). However, by considering the new distance measurement of $\sim 3.7$ kpc of this source, we obtained the dynamical time scale of outflow around 1-2$\rm{\times10^{3}}$ years. The estimated outflow mass is $\sim$11 M$_\odot$ for SiO and $\sim$14.6 M$_\odot$ for HCN.

## Molecular distributions and abundances

In this section, we present the molecular abundance of all the observed species. We compare the abundance of all detected species between G31 and other sources, which is presented in Table [\[table:frac-abun\]](#table:frac-abun). All the molecular abundances are reported w.r.t. H$_2$. Figure [10](#G31-diagram) in the Appendix shows the schematic diagram of kinematics and molecular distributions of G31 based on present observation. There are three outflow directions one is along the E-W direction, one is along the N-S direction, and another is along the NE-SW direction (only for SiO). Outflow components are traced by HCN and SiO emissions. Here, we have obtained different molecular distributions of COMs. The emitting regions of different transitions of COMs are different. We have separated those into three regions such as the emitting region is smaller than the beam size ($\rm{\theta \sim 0.8^{''}}$, see the purple circle in the Figure [10](#G31-diagram)), comparable to the beam size ($\rm{\theta \sim 1.1^{''}}$, see green circle outer edge in the Figure [10](#G31-diagram)), and greater than the beam size ($\rm{\theta \sim 1.4^{''}}$, see cyano circle in the Figure [10](#G31-diagram)). Emitting region of all observed species are provided in Table [1](#table:emitting-regions) (see in Appendix). The uncertainties of emitting regions listed in Table [1](#table:emitting-regions) are the lower limit of true values as estimated emitting regions might be affected by several issues such as poor angular resolution, image noise, and non-Gaussian shape of the source. Emitting regions of CH$_3$OH and CH$_3$OCHO are comparable or slightly greater as compared to the beam size. Molecular distributions show that CH$_3$NCO and CH$_3$SH have a slightly lower-emitting region as compared to beam size (marginally resolved). The data presented in this paper suggests possibly different emitting regions for different COMs, but these are not conclusive because of comparable beam and source size. High sensitivity data with high angular and spatial resolution is required to understand the spatial distributions of these molecules.

### Sulfur dioxide, SO$_2$

SO$_2$ is a good tracer of dense and hot gas of typical hot core (cite: char97; leur07). In this source, we detected a strong transition ($\rm{8_{3,5}-9_{2,8}}$) of SO$_2$. Using LTE model, we estimated the column density and the fractional abundance of SO$_2$, which are $\sim 2.88 \rm{\times10^{18}}$ cm$^{-2}$ and 1.88$\rm{\times10^{-7}}$. The observed abundance of SO$_2$ in G31 is one order of magnitude higher as compared to Srg B2, Orion KL and G10.47+0.03.

### Formaldehyde, H$_2$CO

The presence of H$_2$CO with its ortho, para, and isotopic form within the frequency range of $218-364$ GHz was previously reported by (cite: isok13). Red-shifted strong absorption of H$_2$CO (E$_{up}$=21 K, 68 K) had recently been observed in G31, which supports the existence of infall in the core (cite: belt18). Previously, (cite: fran01) reported a similar kind of inverse P-Cygni profile and found that H$_2$CO traces infall in IRAS 4A and they also detected the outflow from both 4A and 4B position by observing bright wing emission of H$_2$CO. Formaldehyde, along with its deuterated counterpart, has also been observed in outflows toward other sources (cite: sahu18). The presence of H$_2$CS in G31 has previously been reported by (cite: ligt15). Here, we also have detected one strong emission line of H$_2$CS at 101.478 GHz. However, the observed spectrum of H$_2$CS shows that there is a blending with other molecular lines (methyl formate, confirmed from LTE modeling). “H$_2$CO and H$_2$CS are ubiquitous in the ISM. These two species have similar chemical structures; just O atom of H$_2$CO is replaced by S atom in H$_2$CS.

### Methanol, CH$_3$OH

Methanol is a well-known and one of the most abundant COMs in hot cores. Here, we have identified several transitions of methanol. LTE model suggests that it has a high fractional abundance $\sim 1.2\rm{\times10^{-6}}$. We have also estimated methanol abundance following rotation diagram analysis.The obtained abundance using rotation diagram analysis is $\sim 1.2\rm{\times10^{-6}}$, which is similar to the estimated results using the LTE model. A comparison of fractional abundance of methanol between G31 and other hot molecular core is presented in Table [\[table:frac-abun\]](#table:frac-abun).

### Methanethiol, CH$_3$SH

Methanethiol has a similar chemical structure as methanol; just O atom of methanol is replaced by S atom of methanethiol. In Figure [16](#lte-ch3sh), we show the observed and model (LTE) spectra of CH$_3$SH. Best fitted abundance and column density of methanethiol are $\sim 2.70\rm{\times10^{-8}}$ and $\sim 4.13\rm{\times10^{-17}}$ respectively. We also estimated the column density and fractional abundance of this species using rotation diagram analysis, which is one order of magnitude lower as compared to LTE model fitted results. The observed emitting region of methanethiol is comparable to the beam size. The spatial distribution of its emission is as compact as the dust continuum. Since our beam size is comparable to the source size. Therefore, we have uncertainties in determining the emitting regions of this species. For detail knowledge about the distribution of this species, we need a high angular and spatial resolution data.

### Methyl formate, CH$_3$OCHO

CH$_3$OCHO is one of the most abundant COMs, which was observed in both low-mass and high-mass star-forming regions (cite: brow95; caza03). Previously, numerous transitions of CH$_3$OCHO were identified in G31 (cite: isok13; rivi17; belt18). Column density, fractional abundance, and a comparison of fractional abundance of methyl formate with other hot cores are provided in Table [\[table:frac-abun\]](#table:frac-abun). The estimated column density and fractional abundance of methyl formate are similar using both rotation diagram and LTE model fitting analysis. Emitting diameters of various transitions of CH$_3$OCHO are noted down in Table [1](#table:emitting-regions).

### Methyl isocyanate, CH$_3$NCO

In the case of CH$_3$NCO, we have obtained a lower value of rotational temperature (48 K, see Figure. [4](#rot-diagram)a), which is low as compared to a typical hot core. Methyl isocyanate transitions are compact and yield lower value rotational temperature. A similar trend has also been observed for cold component of methanol. Figure [17](#lte-ch3nco) shows the observed and model (LTE) spectra of CH$_3$NCO. The LTE model suggests that for a column density of $\rm{7.22\times10^{17}}$ cm$^{-2}$, we have a good fit with the observed spectra. We have also estimated the column density of CH$_3$NCO using rotation diagram analysis, which is one order higher as compared to LTE model fitting result. CH$_3$NCO emissions are also concentrated towards the center of the source’s dust continuum. However, all these transitions are marginally resolved. Thus, we can not provide the detailed distributions of this molecule.

![](abundance-compare.pdf)

# Discussions

Synthesis of many COMs (e.g., ethylene glycol, methyl formate, etc.) in G31 has been discussed by (cite: rivi17). They discussed the formation routes of a few COMs. Thus, we do not concentrate on the synthesis of all the species which are identified in the present observation. Here, we mainly focus on the chemistry of two newly reported molecules, CH$_3$NCO and CH$_3$SH and two other COMs such as CH$_3$OH and CH$_3$OCHO that are discussed in the text. Here, we have discussed the possible synthesis routes of these species and compared their observed abundance/molecular ratio between G31 and other hot molecular cores. We have also shown a comparison between observed results and existing astrochemical simulation of these species. For the modeling results, we mainly followed (cite: garr13). They considered an isothermal collapse phase, which is followed by a static warm-up phase. In the first phase, the density increases from $\rm{n_H=3\times10^3}$ to $\rm{10^7 \ cm^{-3}}$ under the free-fall collapse. At the initial phase, dust temperature falls to 8 K from 16 K. In the second phase; the temperature varies from 8 K to 400 K, where density remains fixed at $\rm{10^{7} \ cm^{-3}}$. The temperature of this source is $\sim$150 K, which is typical hot core temperature, and the number density ($\rm{n_H}$) of this source is $\sim$ $\rm{10^{7}\ cm^{-3}}$ (cite: belt18). Thus, the hot core model of (cite: garr13) is suitable for understanding chemical evolution of COMs in this source. They used three different warm-up models based on the time scale (i.e., fast, medium, and slow) and the final temperature of their model is much larger than one that is observed in this source. The timescale of the fast warm-up model is more suitable for studying the chemical evolution in high-mass star-forming regions. We used peak gas-phase abundances of all the species around 100-200 K of fast warm-up timescale model to compare with the observed values. Figure [9](#abundance-comparison) compares the observed fractional abundance of CH$_3$OH, CH$_3$SH, CH$_3$OCHO, and CH$_3$NCO between G31 and other sources. The chemistry of these COMs is discussed in the following subsections.

## CH$_3$OH and CH$_3$SH

CH$_3$OH and CH$_3$SH molecules are the chemical analog of each other and have a similar structure only difference is that one has an oxygen atom another sulfur atom. Emitting regions of CH$_3$SH transitions are compact and marginally resolved, whereas the emitting region of methanol is slightly extended compared to CH$_3$SH. A large number of previous experimental, theoretical, and observed results suggest that these two species are mainly produced on the grain surface via successive hydrogen addition reactions (cite: das08; fedo15; mull16; gora17; vida17) with CO and CS, respectively. The main route of formation of methanol and methanethiol is given below,

cm CO $\xrightarrow{\text{H}}$ HCO $\xrightarrow{\text{H}}$ H$_2$CO $\xrightarrow{\text{H}}$ CH$_3$O $\xrightarrow{\text{H}}$ CH$_3$OH cm and cm CS $\xrightarrow{\text{H}}$ HCS $\xrightarrow{\text{H}}$ H$_2$CS $\xrightarrow{\text{H}}$ CH$_3$S $\xrightarrow{\text{H}}$ CH$_3$SH.\
For the above reaction schemes, the first and third steps posses an activation barrier, whereas the second and fourth steps are barrier-less (cite: hase92; gora17). At low-temperature regions, methanol and methanethiol are efficiently produced on the grain surface and released to the gas phase via non-thermal desorption in the cold phase and during the warm-up stage via thermal desorption process. From the astrochemical simulation, (cite: mull16) found that peak abundance of methanol arises around $130$ K. Here, our observed results of methanol predict the gas temperature $\sim 180$ K, which is similar to the typical hot core temperature. In addition to grain surface reactions, H$_2$CS can also be produced in the gas phase. In the gas phase, H$_2$CS is mainly produced from H$_3$CS$^{+}$, where H$_3$CS$^{+}$ is formed via the ion-neutral reaction between S$^{+}$ and CH$_4$. Below $\sim$20 K with a density ($\rm{n_H}$) around $\rm{10^{4}-10^{5} \ cm^{-3}}$, H$_2$CS is accreted onto the grain surface directly from gas phase, which may also contribute to the CH$_3$SH formation (cite: bonf19).

The observed abundance of CH$_3$SH in G31 is $\rm{2.7\times10^{-08}}$ and $\rm{1.0\times10^{-09}}$ in Orion KL (cite: kole14). The observed abundance of methanethiol in Sgr B2 is $\sim$3.5 times higher than the G31. Methanol abundance is almost similar in G31, Orion KL, G10.47+0.03, and 10 times higher in Sgr B2 (see Figure [9](#abundance-comparison)). The observed CH$_3$SH/CH$_3$OH ratio in G31 is similar to Orion KL and it is eight times higher in Sgr B2. Modeling results of these two species also have comparable abundances and molecular ratio (see Table [\[table:frac-abun\]](#table:frac-abun)).

## CH$_3$OCHO

Methyl formate can efficiently be produced on the surface of dust-grains through the reaction between methoxy radical (CH$_3$O) and formyl radical (HCO) (cite: garr08; garr13). Their simulation shows that, around 30-40 K, these radicals are mobile, and the reaction is efficient. It is clear from their simulation that gas phase CH$_3$OCHO is mainly coming from the ice phase (cite: garr13). Increased UV photodissociation of CH$_3$OH leads to the formation of various radicals CH$_3$, CH$_3$O, and CH$_2$O, around 40 K temperature, these are mobile and form the COMs (e.g., CH$_3$OCHO, CH$_3$OCH$_3$). In the gas phase, when T $\sim$ 40 K, protonated methanol and H$_2$CO (when it is abundantly released to the gas phase) react and form HC(OH)OCH$_3$$^{+}$. Then electron recombination of HC(OH)OCH$_3$$^{+}$ produce CH$_3$OCHO (cite: bonf19). An efficient gas-phase reaction of methyl formate production was proposed by (cite: balu15) for the cold environment, where dimethyl ether is the precursor of methyl formate. Dimethyl ether is also present in this source (cite: isok13). Therefore methyl formate can be produced through both grain surface and gas-phase reactions. The observed abundance of CH$_3$OCHO in G31 is $\rm{4.25\times10^{-7}}$, which is similar to the observed abundance in Sgr B2, G10.47+0.03 and ten times higher as compared to the Orion KL and modeling results. In G31, we have observed CH$_3$OCHO/CH$_3$OH abundance ratio $\sim$ 0.14-0.35. For other high-mass star-forming regions, this ratio is found to be $0.03$, $0.03$, and $0.08$ in Sgr B2, Orion KL, and G10.47+0.03, respectively (see Table [\[table:frac-abun\]](#table:frac-abun)).

## CH$_3$NCO

In this work, we find emitting regions of CH$_3$NCO is compact. In this source, (cite: rivi17) also observed a similar emitting region of ethylene glycol. It is primarily produced on the grain surface via recombination of two HCO radicals followed by successive hydrogen addition reactions (cite: cout17). In case of CH$_3$NCO formation, (cite: half15) proposed two routes (i) reaction between HNCO(HOCN) and CH$_3$, and (ii) reaction between HNCO(HOCN) and $\rm{CH_5^{+}}$. (cite: cern16) proposed that it could be produced on the grain surface. The experiment result suggests that CH$_3$NCO can efficiently be produced on the solid phase through the reaction between CH$_3$ and (H)NCO (cite: ligt17). The hot core model suggests that it could be produced via a radical-radical reaction between CH$_3$ and OCN (cite: bell17). Since the reaction mentioned above is exothermic and barrier-less, it can efficiently be produced on the grain surface at a little warmer temperature ($>$30 K), when radical get enough mobility. Though CH$_3$NCO is efficiently produced on the grain surface, it could also be destructed by hydrogen addition reactions and produce n-methyl formamide (cite: bell17). (cite: quen18) also considered similar radical-radical reactions in their chemical model to study the evolution of CH$_3$NCO under hot core conditions. In the hot core, when the temperature reaches around 100 K, CH$_3$ and HNCO can thermally desorb from the grain surface and increase the formation of CH$_3$NCO (cite: mart17; gora20). Our estimated CH$_3$NCO abundance in G31 is $\sim$ $\rm{4.72\times10^{-8}}$. For other hot molecular cores (e.g., Sgr B2, Orion KL), we have found a comparable abundance of CH$_3$NCO. The observed fractional abundance of CH$_3$NCO in this work is well within the modeled results (model 5) of (cite: bell17).

The identification of CH$_3$OH, CH$_3$OCHO, CH$_3$NCO, and CH$_3$SH in G31 suggesting both grain surface and gas phase chemistry is efficient in this source for the formation of COMs. However, we can not distinguish the contribution from the gas and grain phase separately due to the observational limit. To explain the various observed line profile in this work, it requires a combined chemical and radiative transfer model, which will be carried out in our follow-up study.

# Conclusions

We analyzed ALMA band 3 data of a hot molecular core, G31.41+0.31, and the following conclusions are made.

- We detected methyl isocyanate (CH$_3$NCO) and methanethiol (CH$_3$SH), for the first time in G31.\

- We obtained two temperature components by using rotation diagram analysis. The cold component is obtained by CH$_3$OH and CH$_3$NCO where temperature varies between 33 and 48 K. Hot component is obtained by CH$_3$SH, CH$_3$OH and CH$_3$OCHO where the temperature ranges between 143 and 181 K. Estimated hydrogen ($\rm{N_{H_2}}$) column density is $\sim$ 1.53$\times10^{25}$ cm$^{-2}$ and dust is optically thin at 94 GHz.\

- We estimated column density and fractional abundances of various complex species CH$_3$NCO, CH$_3$SH, CH$_3$OH, and CH$_3$OCHO in G31. A comparison of column density/fractional abundances of these species between G31 and other hot molecular cores is discussed. We also compared our observed results with available chemical modeling under hot core conditions. Our observed abundances of COMs in G31 are consistent with other hot cores, Sgr B2, Orion KL, and G10.47+0.03, which suggests similar formation mechanisms of these complex species in these sources.\

- For the kinematics of this source, a low excitation line of $\rm{H^{13}CO^{+}}$ is observed as an inverse P-Cygni profile, which suggests that there is an infall toward the center of this source, i.e., this source is in the younger stage of its evolution.\

- Protostellar outflows are traced by SiO and HCN. Their blue-shifted and red-shifted emission clearly trace outflow along East-West direction. We estimated various outflow parameters. The average dynamical time scale of outflow is $\sim$ $10^{3}$ years.\

# Acknowledgement

This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.01193.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSC, and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and NAOJ. We are grateful to the anonymous referee for numerous comments and suggestions, which improved the manuscript. PG acknowledges CSIR extended SRF fellowship (Grant No. 09/904 (0013) 2018 EMR-I) and and Chalmers Cosmic Origins postdoctoral fellowship. AD acknowledges ISRO respond project (Grant No. ISRO/RES/2/402/16-17) for partial financial support. B.B. acknowledges DST-INSPIRE Fellowship \[IF170046\] for providing partial financial assistance. SKM acknowledges CSIR fellowship (Ref no. 18/06/2017(i) EU-V). This work is partially supported by Consortium for the Development of Human Resources in Science and Technology by Japan Science and Technology Agency. This research was possible in part due to a Grant-In-Aid from the Higher Education Department of the Government of West Bengal. DS acknowledges ASIAA postdoctoral research fund and travel grant. AD and TS also acknowledge support from DST JSPS grant.

# Software

CASA (cite: mcmu07), CASSIS (Cassis Team At CESR/IRAP 2014), RADEX (cite: vand07)

(ref: arya08) Araya, E., Hofner, P., Kurtz, P., Olmi, L. & Linz, H, 2008, ApJ, 675, 420 (ref: altw17) Altwegg K., Balsiger, H., Berthelieret, J. J. et al. 2017, MNRAS, 469, S130 (ref: esta19) Estalella, R., Anglada, G., Díaz-Rodríguez, A. K., Mayen-Gijon, J. M. 2019, A&A, 626, A84 (ref: balu15) Balucani N., Ceccarelli C., Taquet V. 2015, MNRAS, 449, L16 (ref: bell08) Belloche, A., Menten, K. M., Comito, C. et al. 2008, A&A, 482, 179 (ref: bell13) Belloche, A., Müller, H. S. P., Menten, K. M. et al. 2013, A&A, 559, A47 (ref: bell14) Belloche, A., Garrod, R.T. , Müller, H. S. P., & Menten, K. M. 2014, Science, 345, 158 (ref: bell16) Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, A&A, 587, A91 (ref: bell17) Belloche, A., Meshcheryakov, A. A., Garrodet, R. T. et al. 2017, A&A, 601, A49 (ref: belt05) Beltrán M. T., Cesaroni R., Neri R. et al. 2005, A&A, 435, 90 (ref: belt09) Beltrán, M.T., Codella, C., S. Viti, S. et al. 2009, 690, L93 (ref: belt16) Beltrán, M. T. & de Wit, W. J. 2016, A&A Rev., 24, 6 (ref: belt18) Beltrán, M. T., Cesaroni, R., Rivilla, V. M. et al. 2018, A&A, 615,141 (ref: belt19) Beltrán et al. 2019, A&A, 630, 54 (ref: black87) Blake, G. A., Sutton, E., Masson, C., & Phillips, T. 1987, ApJ, 315, 621 (ref: boeh17) Boehler, Y., Weaver, E., Isella, A., et al. 2017, ApJ, 840, 60 (ref: bonf17) Bonfand, M., Belloche, A., Menten, K. M. et al. 2017, A&A, 604, 60 (ref: bonf19) Bonfand, M., Belloche, A., Garrod, R.T., et al. A&A, 628, A27 (ref: brow95) Brown, R.D., Crofts, J.G., Godfrey, P.D. et al. 1975, ApJ, 197, L29. (ref: cabr90) Cabrit, S., & Bertout, C. 1992, A&A, 261, 276 (ref: calm16) Calmonte, U., Altwegg, K., Balsiger, H. et al. 2016, MNRAS, 462, S253 (ref: casa13) Casassus, S., van der Plas, G., M, S. P., et al. 2013, Nature, 493, 191 (ref: caza03) Cazaux, S., Tielens, A. G. G. M., Ceccarelli, C. et al. 2003, ApJ. 593, L51 (ref: cern16) Cernicharo J., Kisiel, Z., Tercero, B., et al., 2016, A&A, 587, L4 (ref: cesa10) Cesaroni, R., Hofner, P., Araya, E., & Kurtz, S. 2010, A&A, 509, 50 (ref: cesa11) Cesaroni, R., Beltrán, M. T., Zhang, Q. et al. 2011, A&A, 533, A73 (ref: cesa17) Cesaroni, R., Sánchez-Monge, Á., Beltrán, M. T., et al. 2017, A&A, 602, A59 (ref: char97) Charnley, S. B. 1997, ApJ, 481, 396 (ref: chak15) Chakrabarti, S.K., Majumdar, L., Das, A., Chakrabarti, S., 2015, APSS, 2015, 357, 90 (ref: chur90) Churchwell E., Walmsley C. M., Cesaroni R., 1990, A&AS, 83, 119 (ref: cout17) Coutens, A., Viti, S., Rawlings, J.M.C. et al. 2017, MNRAS, 475, 2016 (ref: code13) Codella, C., Beltrán, M. T., Cesaroni, R., et al. 2013, A&A, 550, A81 (ref: cox00) Cox, A. N. 2000, Allen’s Astrophysical Quantities (New York: AIP Press) (ref: daly13) Daly, A., Bermúdez, C., López, A. et al. 2013, ApJ, 768, 81 (ref: das08) Das, A., Acharyya, K., Chakrabarti, S. & Chakrabarti, S. K. 2008b, A&A, 486, 209 (ref: das10) Das, A., Acharyya, K. & Chakrabarti, S. K., 2010, MNRAS 409, 789 (ref: das11) Das, A. & Chakrabarti, S. K., 2011, MNRAS, 418, 545 (ref: das16) Das, A., Sahu, D., Majumdar, L., & Chakrabarti, S. K., 2016, MNRAS, 455, 540. (ref: demy07) Demyk, K., Mäder, H.; Tercero, B. et al. 2007, A&A, 466, 255 (ref: fran01) Di Francesco, J., Myers, P. C., Wilner, D. J. et al. 2001, ApJ, 562, 770 (ref: espl13) Esplugues, G. B., Tercero, B., Cernicharo, J., et al. 2013, A&A, 556, A143 (ref: favr11) Favre, C., Despois, D., Brouillet, N., et al. 2011, A&A, 532, A32 (ref: favr15) Favre, C., Bergin, E. A., Neill, J. L., et al. 2015, ApJ, 808, 155 (ref: fedo15) Fedoseev, G., Cuppen, H. M., Ioppolo, S., Lamberts, T., & Linnartz, H. 2015, MNRAS, 448, 1288 (ref: garr08) Garrod R. T., Weaver S. L. W., Herbst E., 2008, ApJ, 682, 283 (ref: garr13) Garrod R. T., 2013, ApJS, 765, 60 (ref: gibb00) Gibb, E., Nummelin, A., Irvine, W. M. et al. 2000, ApJ, 545, 309 (ref: gira09) Girart, J. M., Beltrán, M. T., Zhang, Q. et al. 2009, Science, 324, 1408 (ref: gira18) Girart, J. M., Fernández-López, M., Li, Z. -Y., et al. 2018, ApJL, 856, L27 (ref: goes15) Goesmann F. et al., 2015, Science, 346, 6247 (ref: gora17) Gorai, P., Das, A., Das, A., et al. 2017, ApJ, 836, 70 (ref: gora20) Gorai, P., Bhat, B., Sil, M., Mondal, S. K., Ghosh, R., Das, A., 2020, ApJ, 895, 86 (ref: gold99) Goldsmith, P. F., & Langer, W. D. 1999, ApJ, 517, 209 (ref: half15) Halfen D. T., Ilyushin V. V., Ziurys L. M., 2015, ApJ, 812, L5 (ref: hase92) Hasegawa, T. I., Herbst, E. & Leung, C. M. 1992, ApJS, 82, 167 (ref: herb09) Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427 (ref: higu15) Higuchi, A. E., Hasegawa, T., Saigo, K. et al. J. O. 2015, ApJ, 815, 106 (ref: holl04) Hollis, J, M., Jewell., P.R., Lovas, F.J.,& Remijan, A. 2004, ApJ, 613, L45 (ref: isel16) Isella, A., Guidi, G., Testi, L., et al. 2016, PhRvL, 117, 25 (ref: isok13) Isokoski K., Bottinelli S., van Dishoeck E. F., 2013, A&A, 554, A100 (ref: jin16) Jin, S., Li, S., Isella, A., Li, H., & Ji, J. 2016, ApJ, 818, 76 (ref: kole14) Kolesniková, L., Tercero, B., Cernicharo, J., et al. 2014, ApJ, 784, L7 (ref: krau10) Kraus, S., Hofmann, K-H., Menten, K. M., et al. 2010, Nature, 466, 339 (ref: Kurt00) Kurtz S., Cesaroni R., Churchwell E. et al. 2000, Protostars and Planets IV ed V. Mannings, A. P. Boss and S. S. Russell (Tucson, AZ: Univ. Arizona Press) 299 (ref: leur07) Leurini, S., Beuther, H., Schilke, P. et al. 2007, A&A, 475, 925 (ref: leur14) Leurini, S., Codella, C., López-Sepulcre, A. et al. 2014, A&A, 570, A49 (ref: ligt15) Ligterink, N. F. W, Tenenbaum, E. D., & van Dishoeck, E. F, 2015, A&A, 576, A35 (ref: ligt17) Ligterink N. F. W., et al., 2017, MNRAS, 469, 2219 (ref: Link79) Linke, R. A., Frerking, M. A., & Thaddeus, P., 1979, ApJ, 234, L139 (ref: maju15) Majumdar, L., Gorai, P., Das, Ankan., Chakrabarti, S. K., 2015, APSS, 360, 64 (ref: mcgu16) McGuire, B. A., Carroll, P. B., Loomis, R. A. et al. 2016, Science, 352, 1449-1552. (ref: mcmu07) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Data Analysis Software and Systems XVI (ASP Conf. Ser. 376), ed. R. A. Shaw, F. Hill, & D. J. Bell (San Francisco, CA: ASP), 127 (ref: marg16) Margulés, L, Belloche, A., Müller, H.S.P., Motiyenko, R. A. et al. A&A, 2016 (ref: mart17) Martín-Doménech, R., Rivilla, V. M., Jiménez-Serra, I., et al. 2017, MNRAS, 469, 2230 (ref: mull16) Müller, H.S.P., Belloche, A., Xu, L. et al. 2016, A&A, 587, A92 (ref: mull08) Müller, H. S. P., Belloche, A., Menten, K. M., et al. 2008, J. Mol. Spectr., 251, 319 (ref: mull01) Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A 370, L49 (ref: mull05) Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, J. Mol. Str, 742, 215 (ref: gijo14) Mayen-Gijon, J. M. Anglada, G., Osorio, M., et al. 2014, MNRAS, 437, 3766 (ref: ober11) Öberg K. I., Boogert A. C. A., Pontoppidan K. M., et al. eds, IAU Symposium Vol. 280, 2011, The Molecular Universe. pp 65– (arXiv:1107.5826), doi:10.1017/S1743921311024872 (ref: osse94) Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943 (ref: olmi96) Olmi, L., Cesaroni, R., & Walmsley, C. M. 1996, A&A, 307, 599 (ref: oya16) Oya, Y., Nami Sakai, N., López-Sepulcre, A. et al. 2016, ApJ, 824, 88 (ref: osor09) Osorio, M., Anglada, G., Lizano, S. et al. 2009, ApJ, 694, 29. (ref: pate05) Patel, N. A., Curiel, S., Sridharan, T. K et al. 2005, Nature, 437, 109 (ref: pick98) Pickett, H. M., Poynter, R. L., Cohen, E. A. et al. 1998, JQSRT, 60, 883 (ref: piro97) Pirogov, L., Zinchencko, I., Lapinov, A. et al. 1995, A&AS, 09, 333 (ref: quen18) Quénard, D., Jiménez-Serra, I., Viti, S.,et al. 2018, MNRAS, 474, 2796 (ref: ried19) Reid, M., et al. 2019, ApJ, 885, 131 (ref: rivi17) Rivilla, V.M., Beltrán, M.T., Cesaroni, R. et al. 2017, A&A, 598, 59 (ref: rolf11) Rolffs, R., Schilke, P., Zhang, Q., & Zapata, L., 2011, A&A, 536, A33 (ref: schi01) Schilke, P., Benford, D. J., Hunter, T. R. et al. 2001, ApJS, 132, 281 (ref: sahu18) Sahu, D., Minh., Y.C., Lee, C-F. et al. 2018, MNRAS, 475, 5322 (ref: sahu20) Sahu, D., Liu, S-Y., Das, A., et al. 2020, ApJ, 899, 65 (ref: sil18) Sil, M., Gorai, P., Das, A. et al. ApJ, 2018, 853, 2 (ref: snyd71) Snyder, L. E., & Buhl, D. 1971, ApJ. 163, L47 (ref: sutt95) Sutton, E. C., Peng, R., Danchi, W.C. et al. 1995, ApJS, 97, 455 (ref: tan14) Tan, J. C., Beltrán, M. T., Caselli, P. et al. 2014, Protostars and Planets VI, 149 (ref: terc18) Tercero, B., Cuadrado, S., López, A., et al. 2018, A&A, 620, L6 (ref: vida17) Vidal, T. H. G., Loison, J-C., Jaziri, A. Y., et al. 2017, MNRAS, 469, 435 (ref: vand98) van Dishoeck E. F., Blake G. A. 1998, Annu Rev Astron Astrophys, 36, 317 (ref: vand07) Van der Tak, F. F. S., Black, J. H., Schöier, et al. 2007, A&A 468, 627 (ref: vand16) van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A 585, A58 (ref: weav18) Weaver, E., Isella, A., & Boehler, Y. 2018, ApJ, 853, 113 (ref: whit92) Whittet, D. C. B. 1992, Dust in the Galactic Environment (Bristol: IOP Publishing) (ref: ziur86) Ziurys, L. M., & Turner, B. E. 1986, ApJ, 300, L19 (ref: zapa09) Zapata, L. A., Ho, P. T. P., Schilke, P. et al. 2009, ApJ, 698, 1422

# Fitted spectra, LTE model spectra, moment maps, and schematic diagram of G31 based on present observation.

cm

![](G31-physical-structure.pdf)

![](CH3OH-86615.pdf)

![](CH3OH-86902.pdf)

![](CH3OH-88594.pdf)

![](CH3OH-88939.pdf)

![](CH3OH-101126.pdf)

![](CH3OH-101293.pdf)

![](CH3OH-101469.pdf)

![](CH3OCHO-86917.pdf)

![](CH3OCHO-88723.pdf)

![](CH3OCHO-88843.pdf)

![](CH3OCHO-88851.pdf)

![](CH3OCHO-88862.pdf)

![](CH3OCHO-88868.pdf)

![](CH3OCHO-88770.pdf)

![](CH3OCHO-101370.pdf)

![](CH3OCHO-101414.pdf)

![](CH3NCO-86680.pdf)

![](CH3NCO-86686.pdf)

![](CH3NCO-86780.pdf)

![](CH3NCO-86805.pdf)

![](CH3NCO-87016.pdf)

![](CH3NCO-86866.pdf)

![](101139-normal-lines-new.pdf)

![](101159-normal-lines-new.pdf)

![](101167-normal-lines-new.pdf)

![](SO2.pdf)

![](H2CO.pdf)

![](ch3sh-lte-new.pdf)

![](LTE-ch3nco.pdf)

![](ch3oh-725-634.pdf)

![](ch3oh-725-716-SPW7.pdf)

![](ch3oh-826-817.pdf)

![](ch3oh-15312-14411.pdf)

![](ch3oh-15313-14410.pdf)

![](ch3oh-524-514.pdf)

![](ch3ocho-716-615A.pdf)

![](ch3ocho-716-615E.pdf)

![](ch3ocho-13311-13212A.pdf)

![](ch3ocho-13311-13212E.pdf)

![](ch3ocho-1139-11210A.pdf)

![](ch3ocho-1139-11210E.pdf)

![](ch3nco-1029-928.pdf)

![](ch3nco-1020-920.pdf)

![](ch3nco-1000-909.pdf)

![](ch3nco-10010-909.pdf)

![](ch3nco-10-30-9-30.pdf)

![](ch3sh-404-303.pdf)

![](ch3sh-422-321.pdf)

# Summary of the emitting regions of the observed species.

|            |                 |                |             |     |
|:----------:|:---------------:|:--------------:|:-----------:|:---:|
|  Species   |   Transition    |    Emitting    | Upper State |     |
|            |    Frequency    |     region     |   Energy    |     |
|            |      (GHz)      |     ($''$)     |    \(K\)    |     |
|  CH$_3$SH  | 101.13915$^{a}$ | 0.89$\pm$0.06  |    12.14    |     |
|            | 101.15999$^{b}$ | 0.80$\pm$0.02  |    52.39    |     |
|            | 101.16830$^{c}$ | 0.80$\pm$0.05  |    30.27    |     |
|            |                 |                |             |     |
|  CH$_3$OH  |    86.61557     | 1.35$\pm$0.01  |   102.70    |     |
|            |    86.90291     | 1.35$\pm$0.02  |   102.72    |     |
|            |    88.59478     | 1.29$\pm$0.02  |   328.28    |     |
|            |    88.93997     | 1.27$\pm$0.01  |   328.28    |     |
|            |    101.12685    | 1.14$\pm$0.03  |    60.73    |     |
|            |    101.29341    | 1.21 $\pm$0.02 |    90.91    |     |
|            |    101.46980    | 1.23 $\pm$0.03 |   109.49    |     |
|            |                 |                |             |     |
| CH$_3$NCO  |    86.68019     | 0.82$\pm$0.01  |    22.82    |     |
|            |    86.68655     | 0.83$\pm$0.02  |    34.97    |     |
|            |    86.78077     | 0.78$\pm$0.02  |    46.73    |     |
|            |    86.80502     | 0.77$\pm$0.01  |    46.74    |     |
|            |    87.01607     | 0.76$\pm$0.02  |    58.88    |     |
|            |                 |                |             |     |
| CH$_3$OCHO |     88.6869     | 1.37$\pm$0.04  |    44.97    |     |
|            |    88.72326     | 1.10$\pm$0.03  |    44.96    |     |
|            |    88.84318     | 1.36$\pm$0.02  |    17.96    |     |
|            |    88.85160     | 1.42$\pm$0.02  |    17.94    |     |
|            |    88.86241     | 1.15$\pm$0.04  |   207.10    |     |
|            |    101.37054    | 1.46$\pm$0.05  |    59.64    |     |
|            |    101.41474    | 1.33$\pm$0.06  |    59.63    |     |
|            |                 |                |             |     |
|   SO$_2$   |    86.63908     | 0.71$\pm$0.01  |    55.20    |     |
|  H$_2$CO   |    101.33299    | 1.31$\pm$0.02  |    87.57    |     |

: Emitting region of observed transitions of COMs

\
NOTES: $^{a}$ multiple transitions: 101.13915/101.13965 GHz, $^{b}$ multiple transitions: 101.15999/101.15933/101.16066/101.16069 GHz, $^{c}$ multiple transitions: 101.16715/101.16830 GHz.

[^1]: [(https://www.astro.uni-koeln.de/cdms)]((https://www.astro.uni-koeln.de/cdms))

[^2]: [(http://spec.jpl.nasa.gov/)]((http://spec.jpl.nasa.gov/))

</paper>

Write the methods card for this paper.