# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...976...95A\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...976...95A",
 "title": "Synthesis and Spectroscopic Characterization of Interstellar Candidate Ethynyl Thiocyanate: HCCSCN",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Alonso, Elena R.",
 "n_authors": 13,
 "arxiv_id": "2411.11802",
 "doi": "10.3847/1538-4357/ad85ce",
 "alma_projects_linked_by_archive": [
  "2015.A.00022.T"
 ]
}
```

Paper text:
<paper>
# Synthesis and Spectroscopic Characterization of Interstellar Candidate Ethynyl Thiocyanate: HCCSCN

## Abstract

This work aims to spectroscopically characterize and provide for the first time direct experimental frequencies of the ground vibrational state and two excited states of the simplest alkynyl thiocyanate (HCCSCN) for astrophysical use. Both microwave (8-16 GHz) and millimeter wave regions (50-120 GHz) of the spectrum have been measured and analyzed in terms of Watson’s semirigid rotor Hamiltonian. A total of 314 transitions were assigned to the ground state of HCCSCN and a first set of spectroscopic constants have been accurately determined. Spectral features of the molecule were then searched for in Sgr B2(N), NGC 6334I, G+0.693-0.027 and TMC-1 molecular clouds. Upper limits to the column density are provided.

# Introduction

In the last years, there has been a renewed interest on the chemistry of sulfur in the interstellar medium, aiming to shed light on the long-standing problem of the missing sulfur. That is, in cold dense clouds, all detected S-bearing molecules only account for a very small fraction of sulfur, meaning that the main reservoir of sulfur is unknown (cite: vidal_reservoir_2017). Motivated by this interest, a large variety of sulfur-bearing molecules have been detected in the interstellar medium on the basis of their pure rotational spectrum. Recent detections of S-bearing molecules include S$_2$H (cite: Fuente2017), NS$^+$ (cite: cernicharo2018), HCS, HSC (cite: Agundez2018), HC$_3$S$^+$ (cite: Cernicharo2021a), NCS, HCCS, H$_2$CCS, H$_2$CCCS, C$_4$S, C$_5$S (cite: Cernicharo2021b), HC(O)SH, C$_2$H$_5$SH (cite: Rodriguez-Almeida2021), HCSCN, HCSCCH (cite: Cernicharo2021c), HCCS$^+$ (cite: Cabezas2022), HC$_4$S (cite: Fuentetaja2022), HSO (cite: Marcelino2023), HCNS (cite: Cernicharo2024), HOCS$^+$ (cite: Sanz-Novo2024a), and HNSO (cite: Sanz-Novo2024b). Although the problem of the missing sulfur remains open, this plethora of detections has shown that sulfur participates in a particularly rich chemistry.

A particularly interesting case of S-bearing molecules is the CHNS family, in which three different isomers have been detected in the interstellar medium. The three detected isomers, in increasing energy, are thioisocyanic acid (HNCS, (cite: Frerking1979)), thiocyanic acid (HSCN, (cite: Brunken2009a; Halfen2009; Adande2010)), and thiofulminic acid (HCNS, (cite: McGuire2016HNCS; Cernicharo2024)). The most stable isomer is HNCS, while HSCN and HCNS lie 3200 K and 17300 K above, respectively (cite: Wierzejewska2003; McGuire2016HNCS). In spite of this ordering in energy, it turns out that in the cold starless core TMC-1, the most abundant isomer is HSCN, which is not the most stable one (cite: Cernicharo2024). Given that these molecules are relatively abundant in interstellar clouds such as Sgr B2N, NGC 63341, G+0.693$-$0.027, TMC-1, derivatives in which a CN or CCH group substitutes one hydrogen atom are good targets for astronomical detection. Taking into account the observed abundance of HSCN, it seems promising to search for the CN and CCH derivatives of HSCN, in particular HCCSCN which is an isomer of the recently detected NCCHCS species in TMC-1 (cite: Cabezas_2024).

In this paper, we present the first measurements of the pure rotational spectrum of ethynyl thiocyanate (HCCSCN), the CCH derivative of HSCN (see Figure [1](#molecule)), and an astronomical search for it toward several molecular clouds. The molecule has been first synthesized by (cite: Lu2021) and only characterized by UV-Vis and IR spectroscopy. HCCSCN is predicted as the third most stable acyclic structure in the HC$_{3}$NS family of isomers, right after NCC(H)CS and HCCNCS (cite: Lu2021).

![](HCCSCN1_freq.pdf)

# EXPERIMENTAL METHODOLOGY

Searching for and detecting a new molecule in the ISM typically begins on Earth at a spectroscopic laboratory. This work has been carried out in synergy between an organic chemist, spectroscopists and astrophysicists. This work tandem has been very successful in the detection of more than 310 molecules in the interstellar medium or circumstellar shells up to the present day (cite: endres_cologne_2016). The followed working procedure to obtain a set of parameters that the astrophysicist uses to carry out the complex search for molecules in the different regions of the ISM, includes, in many cases, complex chemical synthesis, the use of home-built and expensive experimental techniques, as well as computational methodology for the calculation of molecular structures.

## Chemical Synthesis

The ethynyl thiocyanate has been synthesized by reacting alkynyl(phenyl)iodonium trifluoromethanesulfonate with sodium thiocyanate (cite: Lu2021). In this work, it has been prepared by reacting tributylethynylstannane with sulfur cyanide, with a yield $63\%$. A similar approach has been used in the past to synthesize 1,2-propadien-1-ylthiocyanate. The compound, which is kinetically unstable, was stabilized in a high-boiling solvent (diethyleneglycol dibutyl ether) in the presence of small amounts of duroquinone (a high-boiling radical inhibitor), and conserved in dry ice.

![](CP.pdf)

## Rotational spectra

In the first step, the broadband rotational spectrum of HCCSCN was recorded from 8-21 GHz employing the Chirped-Pulse Fourier Transform Microwave (CP-FTMW) spectrometer of the Universidad de Valladolid (cite: CP-FTMWVALLADOLID; Leon2019). The synthesized liquid sample, highly volatile, was deposited in a small sealed container through which a carrier gas, Neon, was passed at a pressure of 10-12 bar. This container was introduced in a cooling bath with dry ice to minimize the quick decomposition of the sample. The molecules seeded in the carrier gas were adiabatically expanded through a nozzle (1 mm in diameter) and probed in the cold and efficiently isolated conditions of a supersonic expansion. Then, sequentially, the molecules were polarized using a high power excitation pulse of 300 W, to then capture up to 60000 free induction decays that were averaged in the time domain and Fourier transformed to obtain the spectrum in the frequency domain. The Figure [2](#CP) shows the obtained CP-FTMW spectrum.

After completing the broadband microwave range experiment, we moved on to the millimeter-wave range, recording the room temperature rotational spectrum using the Valladolid home-built millimeter wave absorption spectrometer (cite: Daly2014; Kolesnikova2017a). Employing a multiplication (4x and 6x, VDI. Inc) of the basic synthesizer frequency (Agilent, 250 kHz-20 GHz), the frequency range from 50-120 GHz was reached. The synthesizer output was frequency modulated at 10.2 kHz **with a** modulation depth between 50 and 60 kHz. A Schottky diode detector (VDI, Inc.) was used to capture the signal after a double radiation pass through the cell, and then it was introduced in a lock-in amplifier. A second derivative shape of the lines resulting from 2f detection was fitted to the Gaussian profile function. The uncertainty of the line center frequency is estimated to be better than 50 kHz.

## Quantum-chemical calculations

To be able to interpret the rotational spectra, it is very useful to have theoretically predicted rotational parameters. For this, it is necessary to have an optimized geometry of the molecule, which can be obtained using computational calculations. Since HCCSCN has only 6 atoms, a triple bond between the carbons and a thiocyanate group, it can form only a single conformation, thereby simplifying the computational process.

The geometry optimization was done employing both DFT and *ab initio* computational methods implemented in Gaussian 16 (cite: g16). The levels of theory used were the B3LYP density functional (cite: Becke1993; Becke1992), including the Grimme D3 dispersion interactions (cite: Grimme2010) with Becke–Johnson damping (cite: Grimme2011)), and the Møller–Plesset second-order method (cite: MP2), respectively. The basis set employed in both cases is the Pople split-valence triple-zeta basis set augmented with diffuse and polarization functions on all atoms (the 6-311++G (d,p) basis set (cite: Frisch1984)).

Furthermore, the frequencies of the vibrational modes were also calculated at the same B3LYP density functional and the same basis set employed in the geometry optimization mentioned above. The calculation of the first-order vibration-rotation correction constants $\alpha_{i}$, that define the well-known vibrational dependence of rotational constants, was used to derive the changes in rotational constants according to the equation: $B_{v}=B_{e}-\sum_{i}\alpha_{i}(v_{i}+1/2)$, where $B_{v}$ and $B_{e}$ substitute all three rotational constants in a given vibrational state and in equilibrium, respectively. $v_{i}$ is the vibrational quantum number of the *i*th vibrational mode. This allowed to assign the two excited states found in our spectra based on the differences between theoretical and experimental rotational constants.

# Analysis of the spectra

The observation of characteristic transition patterns is extremely helpful in searches and assignments of the spectrum of a new species and, if possible, it is useful to start at the lower frequency range. We therefore first relied on our broadband spectra measurements carried out with the CP-FTMW spectrometer. HCCSCN is a prolate asymmetric rotor and is predicted to have dipole moment components along the $a$ and $b$ inertial axes. ($|\mu_{a}|=$ 3.2 D, $|\mu_{b}| =$ 1.2 D).

The recorded broadband spectrum indeed presented very intense lines. The assignment of these intense lines was straightforward to the $a$-type R-branch typical triad of transitions: $2_{0,2}\leftarrow1_{0,1}; 2_{1,1} \leftarrow 1_{1,0}; 2_{1,2}\leftarrow1_{1,1}$ and $3_{0,3}\leftarrow2_{0,2}; 3_{1,3}\leftarrow2_{1,2}; 3_{1,2}\leftarrow2_{1,1}$. Then $b$-type R-branch transitions were also measured. We could observe that all these transitions present hyperfine structure (see Figure [2](#CP)) due to the presence of $^{14}$N in the molecule, with nuclear spin (*I* = 1) and nonzero electric quadrupole moment, which interacts with the electric field gradient of the molecule at the position of this nucleus and causes the splitting of each rotational level into several sublevels (cite: Gordy). A total of 13 transitions with 43 hyperfine components were measured with an assumed frequency accuracy of 10 kHz. A first set of rotational constants was obtained using a Watson’s A-reduced semi-rigid rotor analysis in the I$^{r}$-representation, adding a term to account for the nuclear quadrupole coupling contribution (cite: Foley1947; Robinson1953), enabling the determination of the $^{14}$N nuclear quadrupole coupling constants. **Some lines in the spectrum remain unassigned and could be attributed to transitions of some compounds from the synthesis or some perturbed and unassigned excited vibrational states. The most prominent spectral features are accounted in our analyses and follow the expected spectral pattern of HCCSCN.**

![](MW-lines.pdf)

| Parameter | G.S.$^{a}$ | $v_{9}=1$$^{a}$ | $v_{9}=2$$^{a}$ | Calculated$^{b}$ |  |
|:---|---:|---:|---:|---:|---:|
| $A$ /MHz | 10294.7535(31) | 10390.088(34) | 10486.759(48) | 10458 |  |
| $B$ /MHz | 2771.73159(44) | 2782.19440(92) | 2792.5389(18) | 2717 |  |
| $C$ /MHz | 2179.00087(41) | 2180.95866(55) | 2182.85772(97) | 2156 |  |
| $\mathit{\Delta_{J}}$ /kHz | 1.95771(80) | 1.97331(69) | 1.9898(13) | 1.78 |  |
| $\mathit{\Delta_{JK}}$ /kHz | -32.1930(30) | -32.4694(59) | -32.759(11) | -31.02 |  |
| $\mathit{\Delta_{K}}$ /kHz | 195.19(63) | 201.7(13) | 211.1(19) | 199.07 |  |
| $\delta_{J}$ /kHz | 0.76512(25) | 0.77350(38) | 0.78425(75) | 0.68 |  |
| $\delta_{K}$ /kHz | 2.843(21) | 3.570(30) | 4.365(47) | 2.39 |  |
| $\mathit{\Phi_{J}}$ /mHz | 9.11(78) | 9.11$^{g}$ | 9.11$^{g}$ | 8.64 |  |
| $\mathit{\Phi_{JK}}$ /mHz | -87.5(37) | -95.6(61) | -87.5$^{g}$ | -64.39 |  |
| $\mathit{\Phi_{KJ}}$ / Hz | -1.1064(59) | -1.1064$^{g}$ | -1.1064$^{g}$ | -1.21 |  |
| $\mathit{\Phi_{K}}$ / Hz | \[11.85\]$^{f}$ | \[11.85\]$^{f}$ | \[11.85\]$^{f}$ | 11.85 |  |
| $\phi_{J}$ /mHz | \[ 4.14\]$^{f}$ | \[ 4.14\]$^{f}$ | \[ 4.14\]$^{f}$ | 4.14 |  |
| $\phi_{JK}$ /mHz | \[ 5.47\]$^{f}$ | \[ 5.47\]$^{f}$ | \[ 5.47\]$^{f}$ | 5.47 |  |
| $\phi_{K}$ / Hz | \[1.36\]$^{f}$ | \[1.36\]$^{f}$ | \[1.36\]$^{f}$ | 1.36 |  |
| $\chi_{aa}$ /MHz | -1.5260(73) | \- | \- | -1.69 |  |
| $\chi_{bb}$ /MHz | 0.290(10) | \- | \- | 0.49 |  |
| $\chi_{cc}$ /MHz | 1.236(10) | \- | \- | 1.20 |  |
| $J_{\text{min}}/J_{\text{max}}$ | 1/25 | 9/26 | 11/24 |  |  |
| $K_{a}^{\text{min}}/K_{a}^{\text{max}}$ | 0/20 | 0/15 | 0/7 |  |  |
| $N$$^{c}$ | 314 | 165 | 43 |  |  |
| $\sigma_{\text{fit}}$$^{d}$/MHz | 0.020 | 0.043 | 0.028 |  |  |
| $\sigma_{\text{w}}$$^{e}$ | 0.88 | 0.87 | 0.94 |  |  |

.

With this first set of rotational parameters a prediction of the transitions at higher frequencies was done, and we proceeded to the analysis of the millimeter-wave spectrum in the 50-120 GHz frequency range. The prediction presented a shift in the frequency of the transitions with respect to the experimental ones due to the centrifugal distortion effects, but it was not difficult to find the transition patterns that led to measure a total of 271 additional transitions of the molecule with an assumed frequency accuracy of 30 kHz. In this frequency range, the hyperfine structure collapses into a single line, simplifying the spectra. The final fit, combining the transitions from both microwave and millimeter-wave experiments with their corresponding weights, was obtained using Watson’s A-reduced Hamiltonian in the I$^r$-representation (cite: Watson1977) and the Pickett’s SPFIT/SPCAT program suite (cite: Pickett1991). (All measured transitions are available in a machine-readable form in the online journal.) The spectroscopic data obtained in this work allowed the determination of the rotational constants, nuclear quadrupole coupling constants as well as the full set of quartic and some sextic centrifugal distortion constants presented in Table [\[constants\]](#constants). This spectroscopic information thus enables a search for this newly characterized molecule in different regions of the ISM.

Further inspection of the spectrum revealed the existence of satellite lines in the neighborhood of the ground state. These lines most likely belong to pure rotational transitions in excited vibrational states. Under the $C_{s}$ point group, the lowest-frequency normal vibrational mode is $\nu_{9}$ ($A'$) with the anharmonic frequency predicted at 118 cm$^{-1}$. This vibrational mode corresponds to scissoring bending vibration. As Figure [3](#mw) shows, we were able to follow two successive excitations of this mode and to assign over 160 and 40 lines for $v_{9}=1$ and $v_{9}=2$ excited vibrational states, respectively. The assignment was carried out by comparing the values of their experimental changes in rotational constants relative to the ground state with their calculated counterparts. Only *a*-type transitions have been observed for both excited vibrational states. (All measured transitions are available in a machine-readable form in the online journal.)

+--------------------+---------------------------------+--------------------------------+
|                    | $v_{9}=1$                       | $v_{9}=2$                      |
+:===================+=============:+=================:+=============:+================:+
|                    | Exp.         | Calculated$^{a}$ | Exp.         | Estimated$^{b}$ |
+--------------------+--------------+------------------+--------------+-----------------+
| $A_{v}-A_{0}$ /MHz | -95.334(34)  | -102.21          | -192.005(48) | -190.67         |
+--------------------+--------------+------------------+--------------+-----------------+
| $B_{v}-B_{0}$ /MHz | -10.4628(10) | -9.36            | -20.8073(19) | -20.93          |
+--------------------+--------------+------------------+--------------+-----------------+
| $C_{v}-C_{0}$ /MHz | -1.95779(68) | -1.75            | -3.8569(11)  | -3.92           |
+--------------------+--------------+------------------+--------------+-----------------+

# OBSERVATIONAL SEARCHES

#### Sgr B2N

We have searched for signal from HCCSCN in the Prebiotic Interstellar Molecular Survey (PRIMOS) project observations toward Sgr B2(N) using the 100 m Robert C Byrd Green Bank Telescope (GBT). Sgr B2(N) is a massive star-forming region (cite: Turner:1991:617) located at a distance of $\sim$8.3 kpc (cite: Reid:2014:130). The details of this dataset are presented elsewhere (cite: Neill:2012:153) and only a few pertinent details will be summarized. The observations were taken in position switched mode, with the pointing position set to (J2000) $\alpha = 17^h47^m19^s.8, \delta = -28^\circ22^\prime17^{\prime\prime}$. The bandwidth covers a total range of 1–50 GHz with a few gaps, primarily at the lower frequencies, and at a resolution of $\sim$24 kHz corresponding to 2–0.14 km s$^{-1}$ across the band. The RMS sensitivity ranges from a few to a few tens of mK.

Molecules in Sgr B2(N) observations typically fall into one of two categories: cold, extended, and in absorption (e.g., (cite: McGuire:2016:1449)) or warm, compact, and in emission (e.g., (cite: Belloche:2013:A47)). We therefore searched for HCCSCN under two sets of conditions using a single-excitation model: a cold model with $T_{ex} = 5.8$ K with a 20$^{\prime\prime}$ source size and a warm model with $T_{ex} = 150$ K with a 5$^{\prime\prime}$ source size. The linewidth was 8 km s$^{-1}$ and the $V_{LSR}$ was +64 km s$^{-1}$ in both cases. At any reasonable linewidth, splitting due to hyperfine components is negligible and unresolved. The 3$\sigma$ upper limit was set using what would be the highest signal-to-noise ratio line in the case of a detection. No signal was seen consistent with either scenario, and explorations of the data preclude any detection at other excitation temperatures as well. The 3$\sigma$ upper limit for warm HCCSCN was $N_T \leq 5\times10^{15}$ cm$^{-2}$ and for cold HCCSCN was $N_T \leq 8\times10^{12}$ cm$^{-2}$. This corresponds to a fractional abundance of $X_{\ce{H2}} \leq 8\times10^{-12}$ cm$^{-2}$ assuming an $N_{\ce{H2}} = 1\times10^{24}$ cm$^{-2}$ (cite: Lis:1990:195). The much more stringent limit in the case of cold HCCSCN is due to the substantially reduced partition function, which would result in far stronger transitions (relatively speaking) at these frequencies. The rotational partition function $(Q_{rot})$ was evaluated by summation of the Boltzmann factors over the energy levels in the ground vibrational state, see Table [1](#partition). We used the SPCAT program (cite: pickett1998) to undertake this summation numerically employing the spectroscopic constants from Table [\[constants\]](#constants) and all rotational states up to J= 250 and $K_{a}$= 150. Figure [4](#primos) shows the constraining transitions in each case.

|  $T$ (K) | $Q_{\text{rot}}$ | $Q_{\text{vib}}$ |
|---------:|-----------------:|-----------------:|
| 1000.000 |       2063131.21 |           1851.5 |
|  500.000 |        724859.39 |             39.6 |
|  300.000 |        335584.98 |              6.3 |
|  225.000 |        217628.24 |              3.2 |
|  150.000 |        118273.41 |              1.7 |
|   75.000 |         41753.40 |              1.1 |
|   37.500 |         14755.85 |              1.0 |
|   18.750 |          5219.50 |              1.0 |
|    9.375 |          1848.40 |              1.0 |
|    5.000 |           722.22 |              1.0 |
|    3.000 |           337.21 |              1.0 |

: Rotational and vibrational partition functions for HCCSCN at different temperatures.

![image](primos_cold.pdf) ![image](primos_warm.pdf)

#### NGC 6334I

We have also searched for signal in Atacama Large Millimeter/sub-Millimeter Array (ALMA) observations of the massive star-forming region NGC 6334I. The dataset used here is the same that was used for the first interstellar detection of methoxymethanol (; (cite: McGuire:2017:L46)). The most constraining transition is located near $\sim$280.8 GHz in data from Project #2015.A.00022.T. The phase center for the observations was (J2000) $\alpha = 17^h20^m53^s.36, \delta = -35^\circ47^\prime00^{\prime\prime}.0$. The angular resolution achieved was 0$^{\prime\prime}$.25$\times$0.$^{\prime\prime}$19, with a spectral resolution of 1.1 km s$^{-1}$ and a sensitivity of 2.0 mJy beam$^{-1}$. The extraction position for the spectra that were investigated was (J2000) $\alpha = 17^h20^m53^s.373, \delta = -35^\circ46^\prime58^{\prime\prime}.14$, the same position in which was originally detected. We use the same excitation temperature ($T_{ex}  = 200$ K), linewidth ($\Delta V = 2.4$ km s$^{-1}$), and $V_{lsr}$ = -7 km s$^{-1}$ as in that work, and assume the source fills the beam. As with Sgr B2(N), hyperfine splitting is unresolved. We derive an upper limit of $N_T \leq 5\times10^{15}$ cm$^{-2}$. This corresponds to a fractional abundance of $X_{\ce{H2}} \leq 2\times10^{-9}$ cm$^{-2}$ assuming an $N_{\ce{H2}} = 3\times10^{24}$ cm$^{-2}$ (cite: Zernickel:2012:A87). We note that the column density is derived from Herschel observations of the source and assume a homogenous gas distribution over a 10$^{\prime\prime}$ emitting region toward the hot core. ALMA observations show this overall size is realistic, but that the underlying gas distribution is heterogenous (cite: El-Abd:2024:). As a result, this column is a lower limit.

![image](HCCSCN_32207849800.pdf) ![image](HCCSCN_34394137800.pdf) ![image](HCCSCN_36696506800.pdf)

#### G+0.693-0.027

We also searched for the species toward the G+0.693-0.027 (hereafter G+0.693) molecular cloud located in the Sgr B2 complex in the Galactic Center. This cloud is a well suited target to address the search for HCCSCN because it exhibits an extremely rich chemical content (e.g. (cite: zeng_complex_2018; zeng2021; zeng2023; rivilla2018; rivilla_abundant_2019; rivilla2020b; rivilla2021a; rivilla2021b; rivilla2022a; rivilla2022b; rivilla2022c; rivilla2023; rodriguez-almeida2021b; jimenez-serra2022; colzi2022; massalkhi2023; sanz-novo2023; san-andres2024)). In the last five years, 18 new interstellar molecules have been identified, and among them several with sulfur, such as thioformic acid (HCOSH, (cite: rodriguez-almeida2021a)), the O-protonated carbonyl sulfide (HOCS$^{+}$, (cite: Sanz-Novo2024a)), and thionylimide (HNSO, (cite: Sanz-Novo2024b)). Moreover, it has been found that the relative abundances of S-bearing species with O-analogs are significantly higher than in other molecular clouds, suggesting that S is much less depleted in G+0.693, likely due to the action of large-scale shocks ((cite: Sanz-Novo2024a)).

We performed the search of HCCSCN using a high-sensitivity spectral survey carried out with the Yebes 40m and IRAM 30m telescopes. The observations were carried out during sessions between March 2021 and March 2022, with a total telescope scheduled time of 230 hours, of which 110 hours were on source. We used the position switching mode, centering the observations at $\alpha$ = $\,$17$^{\rm h}$47$^{\rm m}$22$^{\rm s}$, $\delta$ = $\,-$28$^{\circ}$21$^{\prime}$27$^{\prime\prime}$, with the off position shifted by $\Delta\alpha$ = $-885$$^{\prime\prime}$ and $\Delta\delta$ = $290$$^{\prime\prime}$. The noise at this spectral resolution is 0.25$-$0.9 mK, depending on the spectral range. The line intensity of the spectra was measured in units of $T_{\mathrm{A}}^{\ast}$, since the molecular emission toward G+0.693 is extended over the beams (e.g. (cite: brunken_interstellar_2010)). More details of these observations were provided on (cite: rivilla2023).

We implemented the spectroscopic entry of HCCSCN presented in this work into the MADCUBA package [^1]; version 04/07/2023; (cite: martin2019)). Using the SLIM (Spectral Line Identification and Modeling) tool of MADCUBA, we generated a synthetic spectra under the assumption of Local Thermodynamic Equilibrium (LTE), and compared with the observed spectra. The species is not identified in the survey. Figure [5](#g0693) shows the three brightest transitions according to the LTE model that are not blended with line emission of other molecules. We have thus derived with SLIM a 3$\sigma$ upper limit (in integrated intensity), using typical parameters derived for other species in this cloud (line width of 20 km s$^{-1}$, excitation temperature of 8 K, and a velocity of 68 km s$^{-1}$). We obtained a value of $N<$1.1$\times$10$^{12}$ cm$^{-2}$. This translates into a fractional abundance with respect to H$_2$ of $<$ 8.1 $\times$ 10$^{-12}$, using $N$(H$_{2}$) = 1.35$\times$10$^{23}$ cm$^{-2}$ from (cite: martin2008).

![](fig_tmc1.pdf)

#### TMC-1

The observations of TMC-1 are part of the QUIJOTE[^2] line survey (cite: Cernicharo2021d; Cernicharo2024). The data were gathered with the Yebes 40m radio telescope equipped with the Q-band receivers and spectrometers built under the Nanocosmos project[^3]. The selected position corresponds to the cyanopolyyne peak (CP) in TMC-1 ($\alpha_{J2000}=4^{\rm h} 41^{\rm  m} 41.9^{\rm s}$ and $\delta_{J2000}= +25^\circ 41' 27.0''$). The receivers consist of two cold high-electron mobility transistor amplifiers covering the 31.0-50.3 GHz band with horizontal and vertical polarizations. The receiver temperatures are 16 K at 32 GHz and 30 K at 50 GHz. The backends are $2\times8\times2.5$ GHz fast Fourier transform spectrometers with a spectral resolution of 38 kHz, providing the whole coverage of the Q-band in both polarizations. A more detailed description of the system is given by (cite: Tercero2021).

The data of the QUIJOTE line survey presented here were gathered in several observing runs between November 2019 and July 2023. All observations are performed using frequency-switching observing mode with a frequency throw of 8 and 10 MHz. The total observing time on the source is 737 (frequency throw of 8 MHz) and 465 hours (frequency throw of 10 MHz). Hence, the total observing time on source is 1202 hours. The measured sensitivity varies between 0.08 mK at 32 GHz and 0.2 mK at 49.5 GHz. The data analysis procedure has been described by (cite: Cernicharo2022).

As a consequence of the unprecedented sensitivity of the QUIJOTE line survey, more than 50 new molecular species have been found in the last four years in TMC-1, including protonated species of abundant species, pure hydrocarbons and radicals (cite: Cernicharo2024). Among these new molecules it is worth noting the detection of the S-bearing species NCS, HCCS, H$_2$CCS, H$_2$CCCS, C$_4$S, HCSCN, HCSCCH, HC$_4$S, HCCCS$^+$, HCCS, HCCS$^+$, HSO, HCNS, and NCCHCS (cite: Cernicharo2021b; Cernicharo2021c; Cabezas2022; Fuentetaja2022; Marcelino2023; Cernicharo2024; Cabezas_2024). The presence of a large reservoir of S-bearing species in TMC-1, in particular of HCSCN, HCSCCH, NCCHCS, HCNS, HCSN and HSCN (cite: Cernicharo2021c; Cernicharo2024; Cabezas_2024), indicates that HCCSCN deserves to be searched in this source as it could be the CCH derivative of HSCN. The latter molecule has been found to be a factor $\sim$3 more abundant than HNCS with a column density of 8.3$\times$10$^{11}$ cm$^{-2}$ (cite: Cernicharo2024).

The spectroscopic information of HCCSCN derived in this work has been implemented in the MADEX[^4] code. Because of the much larger value of the $a$-component of the dipole moment, only $a$-type transitions have been searched for. As the kinetic temperature of the cloud is 9 K (cite: Agundez2023), we limited the energy of the upper levels of the transitions to 14 K ($J$=10, $K_a$=0,1). In order to model the expected intensity we have assumed a source of uniform brightness temperature with a diameter of 80$''$ (cite: Fosse2001; Cernicharo2023). The adopted linewidth is 0.6 km s$^{-1}$, i.e., identical to that derived for similar species such as the CCH and CN derivative of thioformaldeyde, HCSCCH and HCSCN (cite: Cernicharo2021c), and the CN derivative of thioketene, NCCHCS (cite: Cabezas_2024). We also adopted a rotational temperature of 5 K similar to that derived for HCSCN. A total of fifteen individual transitions were searched as shown in Figure [6](#fig_tmc1). Only a few of the generated synthetic spectra have a counterpart in the data and, hence, we conclude that the molecule is not present in TMC-1 with a 3$\sigma$ upper limit to its column density, based on each individual line, of 5$\times$10$^{10}$cm$^{-2}$.

# ASTROCHEMICAL IMPLICATIONS

Sulfur molecules, in general, are of great astrochemical interest, in part, because of the longstanding mystery of “missing sulfur,” based on the apparent drop in observable sulfur species when comparing diffuse environments - where the abundances are roughly the solar values - to dense molecular clouds - where the combined abundances of all sulfur-bearing species can be three orders of magnitude less. It seems fairly clear that the sulfur is not disapearing, per se, but rather, is being chemically converted to some reservoir species, which has not yet been conclusively identified. Sulfur is also an important element for Terrestrial organisms, being a key constituent of biomolecules such as the amino acids cysteine and methionine, and thus, a better understanding of interstellar sulfur chemistry is an important step in understanding the inventory of prebiotic molecules which may be available for delivery to the surfaces of exoplanets and implicated in the origins of life.

In astrophysical environments, the synthesis pathways used to produce HCCSCN for this study would not occur. Indeed, unsaturated species such as HCCSCN are typical of the kinds of molecules formed via gas-phase reactions, which are almost exclusively barrierless, exothermic, two-body processes given the low temperatures ($\sim$ 10 K) and densities ($\sim\;10^{4}$ cm$^{-3}$) of molecular clouds. To the best of our knowledge, the only such reaction leading to HCCSCN that has been the subject of laboratory investigations is

$$\begin{equation}
        \ce{HCCH + SCN -> HCCSCN + H}
    
\end{equation}$$

though, as reported by (cite: Chen2003), this is an endothermic process with a substantial barrier, which is consistent with the upper limit of 10$^{-14}$ cm$^3$ s$^{-1}$ experimentally determined for the rate coefficient by (cite: Baren1999) in the temperature range 298-620 K. Therefore, this is not a viable formation pathway in cold astrophysical environments. Nevertheless, recent observations of other sulfur-bearing species in TMC-1 (cite: Cernicharo2021b; Cernicharo2021c; Cernicharo2024) yield some clues that could point to other possible formation pathways to HCCSCN. One possibility are the reactions of CN with and . The first one is calculated to be endothermic by 10.3 kcal mol$^{-1}$, although the second is exothermic and could provide a valid route. Another possibility are the reactions of HCCS with HCN and HNC, although in this case the two are calculated to be endothermic by 44.1 and 29.2 kcal mol$^{-1}$, respectively. The exploration of the potential energy surface for the different reactions was done using the Molpro 2020.2 *ab initio* program package (cite: MOLPRO_brief). All the stationary points were fully optimized using the coupled cluster method (CCSD(T)) (cite: RAGHAVACHARI1989479) along with Dunning’s correlation consistent polarized valence triple-z (cc-pVTZ) basis set (cite: dunningCCST), and the energies are relative to that of the separated reactants. The reaction is calculated to be exothermic although it is likely that it occurs with a barrier because there is an important rearrangement. Finally, the reaction could be a source of HCCSCN at low temperatures because it is calculated to be exothermic and could occur with a minimal rearrangement.

However formed, gas-phase could be depleted via, e.g., photodissociation, reactions with other gas-phase species, or accretion onto grains. Once accreted onto the surfaces of dust grains or dust-grain ice mantles, the dominant chemical destruction pathway is via reaction with hydrogen atoms, which can remain comparatively mobile even at the very low temperature of 10 K. Previous quantum-chemical calculations of the reaction of highly unsaturated interstellar molecules with H has found that such processes are often barrierless and exothermic, and yield one or more stable, more highly saturated end products (cite: shingledecker_case_2019; shingledecker_grain-surface_2022). If formed on the surfaces of grains in cold molecular clouds, these stable, more highly-saturated products can become covered by the continuous accretion of yet more gas-phase species, thereby becoming trapped within the dust-grain ice mantle. If the astrophysical environment subsequently warms, such as happens during star-formation, these trapped molecules can be liberated into the gas-phase, where they can be observed. Thus, it is often possible to surmise a chemical link between an unsaturated carbon chain molecule seen in a cold core with a more saturated species seen in a hot core. In the absence of detailed quantum calculations, it is not possible to say with a high degree of certainty what the grain-surface saturation of would yield, but we here suggest two possibilities by way of speculation. The first possibility is the species , i.e. the ethyl ester of thiocyanic acid. Another, more astrochemically interesting possible saturation product is , the heterocyclic molecule thiazole. This latter species would be of particular interest since, though now several cyclic or polycyclic species have been detected in the ISM, there are to date no detections of heterocycles with a sulfur atom, and certainly not of cycles with two heteroatoms such as thiazole, and if it were detected, it would suggest a grain-surface origin for other similar species.

# CONCLUSIONS

We have determined for the first time precise rotational and centrifugal distortion constants for the derivative of () from accurate laboratory measurements. This new laboratory data allowed us to search for it towards several interstellar sources without success. Several possible formation paths of this species are discussed, emphasizing that it could be formed from the reaction of with . Similar reactions have been previously proposed for other S-bearing species found in TMC-1 such as , , and which are and derivatives of and are very abundant in that cloud. Although no spectral features of were found, present data can be used with confidence in future searches in other interstellar sources.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.A.00022.T. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory operated by ESO, AUI/NRAO and NAOJ. E.R.A. and I.L. acknowledge funding from Ministerio de Ciencia e Innovación (PID2019-111396GB-I00), and Junta de Castilla y León (VA244P20). V.M.R., I.J-S. and J.M-P acknowledges support from the grant No. PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. VMR also acknowledges support from the grant number RYC2020-029387-I funded by MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", and from the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC). J.C., C.C., and M.A. thank the Spanish Ministry of Science, Innovation and Universities for funding support through projects PID2019-106110GB-I00, and PID2019-106235GB-I00 and ERC for funding through grant ERC-2013-Syg-610256-NANOCOSMOS. M.A. thanks the Consejo Superior de Investigaciones Científicas (CSIC; Spain) for funding through project PIE 202250I097.J.-C.G. thanks the Programme National “Physique et Chimie du Milieu Interstellaire” (PCMI) of CNRS Terre @ Univers with CNRS Physique & CNRS Chimie, co-funded by CEA and CNES.

natexlab

(ref: Adande2010) Adande, G. R., Halfen, D. T., Ziurys, L. M., Quan, D., & Herbst, E. 2010, ApJ, 725, 561, doi: [`10.1088/0004-637X/725/1/561`](http://doi.org/10.1088/0004-637X/725/1/561)

(ref: Agundez2018) Agúndez, M., Marcelino, N., Cernicharo, J., & Tafalla, M. 2018, A&A, 611, L1, doi: [`10.1051/0004-6361/201832743`](http://doi.org/10.1051/0004-6361/201832743)

(ref: Agundez2023) Agúndez, M., Marcelino, N., Tercero, B., & Cernicharo, J. 2023, A&A, 677, L13, doi: [`10.1051/0004-6361/202347524`](http://doi.org/10.1051/0004-6361/202347524)

(ref: Baren1999) Baren, R. E., & Hershberger, J. F. 1999, The Journal of Physical Chemistry A, 103, 11340, doi: [`10.1021/jp992930e`](http://doi.org/10.1021/jp992930e)

(ref: Becke1992) Becke, A. D. 1992, Journal of Chemical Physics, 96, 2155, doi: [`10.1063/1.462066`](http://doi.org/10.1063/1.462066)

(ref: Becke1993) —. 1993, The Journal of Chemical Physics, 98, 1372, doi: [`10.1063/1.464304`](http://doi.org/10.1063/1.464304)

(ref: Belloche:2013:A47) Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013, Astronomy and Astrophysics, 559, A47, doi: [`10.1051/0004-6361/201321096`](http://doi.org/10.1051/0004-6361/201321096)

(ref: Brunken2009a) Brünken, S., Yu, Z., Gottlieb, C. A., McCarthy, M. C., & Thaddeus, P. 2009, ApJ, 706, 1588, doi: [`10.1088/0004-637X/706/2/1588`](http://doi.org/10.1088/0004-637X/706/2/1588)

(ref: brunken_interstellar_2010) Brünken, S., Belloche, A., Martín, S., Verheyen, L., & Menten, K. M. 2010, Astronomy and Astrophysics, 516, A109, doi: [`10.1051/0004-6361/200912456`](http://doi.org/10.1051/0004-6361/200912456)

(ref: Cabezas_2024) Cabezas, C., Agúndez, M., Endo, Y., et al. 2024, Astronomy Astrophysics, 686, L3, doi: [`10.1051/0004-6361/202450323`](http://doi.org/10.1051/0004-6361/202450323)

(ref: CP-FTMWVALLADOLID) Cabezas, C., Varela, M., & Alonso, J. L. 2017, Angewandte Chemie International Edition, 56, 6420, doi: [`https://doi.org/10.1002/anie.201702425`](http://doi.org/https://doi.org/10.1002/anie.201702425)

(ref: Cabezas2022) Cabezas, C., Agúndez, M., Marcelino, N., et al. 2022, A&A, 657, L4, doi: [`10.1051/0004-6361/202142815`](http://doi.org/10.1051/0004-6361/202142815)

(ref: Cernicharo2024) Cernicharo, J., Agúndez, M., Cabezas, C., et al. 2024, A&A, 682, L4, doi: [`10.1051/0004-6361/202349105`](http://doi.org/10.1051/0004-6361/202349105)

(ref: Cernicharo2021d) Cernicharo, J., Agúndez, M., Kaiser, R. I., et al. 2021a, A&A, 652, L9, doi: [`10.1051/0004-6361/202141660`](http://doi.org/10.1051/0004-6361/202141660)

(ref: Cernicharo2021c) Cernicharo, J., Cabezas, C., Endo, Y., et al. 2021b, A&A, 650, L14, doi: [`10.1051/0004-6361/202141297`](http://doi.org/10.1051/0004-6361/202141297)

(ref: Cernicharo2021a) —. 2021c, A&A, 646, L3, doi: [`10.1051/0004-6361/202040013`](http://doi.org/10.1051/0004-6361/202040013)

(ref: cernicharo2018) Cernicharo, J., Lefloch, B., Agúndez, M., et al. 2018, ApJ, 853, L22, doi: [`10.3847/2041-8213/aaa83a`](http://doi.org/10.3847/2041-8213/aaa83a)

(ref: Cernicharo2021b) Cernicharo, J., Cabezas, C., Agúndez, M., et al. 2021d, A&A, 648, L3, doi: [`10.1051/0004-6361/202140642`](http://doi.org/10.1051/0004-6361/202140642)

(ref: Cernicharo2022) Cernicharo, J., Fuentetaja, R., Cabezas, C., et al. 2022, A&A, 663, L5, doi: [`10.1051/0004-6361/202244255`](http://doi.org/10.1051/0004-6361/202244255)

(ref: Cernicharo2023) Cernicharo, J., Tercero, B., Marcelino, N., Agúndez, M., & de Vicente, P. 2023, A&A, 674, L4, doi: [`10.1051/0004-6361/202346722`](http://doi.org/10.1051/0004-6361/202346722)

(ref: Chen2003) Chen, H.-T., & Ho, J.-J. 2003, The Journal of Physical Chemistry A, 107, 7004, doi: [`10.1021/jp022613z`](http://doi.org/10.1021/jp022613z)

(ref: colzi2022) Colzi, L., Martı́n-Pintado, J., Rivilla, V. M., et al. 2022, ApJL, 926, L22, doi: [`10.3847/2041-8213/ac52ac`](http://doi.org/10.3847/2041-8213/ac52ac)

(ref: Daly2014) Daly, A., Kolesniková, L., Mata, S., & Alonso, J. 2014, J. Mol. Spectrosc., 306, 11 , doi: [`http://dx.doi.org/10.1016/j.jms.2014.10.003`](http://doi.org/http://dx.doi.org/10.1016/j.jms.2014.10.003)

(ref: dunningCCST) Dunning, Thom H., J. 1989, The Journal of Chemical Physics, 90, 1007, doi: [`10.1063/1.456153`](http://doi.org/10.1063/1.456153)

(ref: El-Abd:2024:) El-Abd, S. J., Brogan, C. L., Hunter, T. R., et al. 2024, An Automated Chemical Exploration of NGC 6334I at 340 au Resolution, doi: [`10.48550/arXiv.2402.13913`](http://doi.org/10.48550/arXiv.2402.13913)

(ref: endres_cologne_2016) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, Journal of Molecular Spectroscopy, 327, 95, doi: [`10.1016/j.jms.2016.03.005`](http://doi.org/10.1016/j.jms.2016.03.005)

(ref: Foley1947) Foley, H. M. 1947, Physical Review, 71, 747, doi: [`10.1103/PhysRev.71.747`](http://doi.org/10.1103/PhysRev.71.747)

(ref: Fosse2001) Fossé, D., Cernicharo, J., Gerin, M., & Cox, P. 2001, ApJ, 552, 168, doi: [`10.1086/320471`](http://doi.org/10.1086/320471)

(ref: Frerking1979) Frerking, M. A., Linke, R. A., & Thaddeus, P. 1979, ApJ, 234, L143, doi: [`10.1086/183126`](http://doi.org/10.1086/183126)

(ref: Frisch1984) Frisch, M. J., Pople, J. A., & Binkley, J. S. 1984, The Journal of Chemical Physics, 80, 3265, doi: [`10.1063/1.447079`](http://doi.org/10.1063/1.447079)

(ref: g16) Frisch, M. J., Trucks, G. W., Schlegel, H. B., et al. 2016, Gaussian16 Revision B.01

(ref: Fuente2017) Fuente, A., Goicoechea, J. R., Pety, J., et al. 2017, ApJL, 851, L49, doi: [`10.3847/2041-8213/aaa01b`](http://doi.org/10.3847/2041-8213/aaa01b)

(ref: Fuentetaja2022) Fuentetaja, R., Agúndez, M., Cabezas, C., et al. 2022, A&A, 667, L4, doi: [`10.1051/0004-6361/202245018`](http://doi.org/10.1051/0004-6361/202245018)

(ref: Gordy) Gordy, W., & Cook, R. L. 1984, Microwave molecular spectra (Wiley Interscience, New York)

(ref: Grimme2010) Grimme, S., Antony, J., Ehrlich, S., & Krieg, H. 2010, Journal of Chemical Physics, 132, 154104, doi: [`10.1063/1.3382344`](http://doi.org/10.1063/1.3382344)

(ref: Grimme2011) Grimme, S., Ehrlich, S., & Goerigk, L. 2011, Journal of Computational Chemistry, 32, 1456, doi: [`10.1002/jcc.21759`](http://doi.org/10.1002/jcc.21759)

(ref: Halfen2009) Halfen, D. T., Ziurys, L. M., Brünken, S., et al. 2009, ApJ, 702, L124, doi: [`10.1088/0004-637X/702/2/L124`](http://doi.org/10.1088/0004-637X/702/2/L124)

(ref: jimenez-serra2022) Jiménez-Serra, I., Rodrı́guez-Almeida, L. F., Martı́n-Pintado, J., et al. 2022, A&A, 663, A181, doi: [`10.1051/0004-6361/202142699`](http://doi.org/10.1051/0004-6361/202142699)

(ref: Kolesnikova2017a) Kolesniková, L., Alonso, E. R., Mata, S., & Alonso, J. L. 2017, ApJS, 229, 26, doi: [`10.3847/1538-4365/aa5d13`](http://doi.org/10.3847/1538-4365/aa5d13)

(ref: Leon2019) León, I., Alonso, E. R., Cabezas, C., Mata, S., & Alonso, J. L. 2019, Communications Chemistry, 2, 3, doi: [`10.1038/s42004-018-0103-2`](http://doi.org/10.1038/s42004-018-0103-2)

(ref: Lis:1990:195) Lis, D. C., & Goldsmith, P. F. 1990, The Astrophysical Journal, 356, 195, doi: [`10.1086/168830`](http://doi.org/10.1086/168830)

(ref: Lu2021) Lu, B., Wu, Z., Wang, L., et al. 2021, Chem. Commun., 57, 3343, doi: [`10.1039/D1CC00629K`](http://doi.org/10.1039/D1CC00629K)

(ref: Marcelino2023) Marcelino, N., Puzzarini, C., Agúndez, M., et al. 2023, A&A, 674, L13, doi: [`10.1051/0004-6361/202346935`](http://doi.org/10.1051/0004-6361/202346935)

(ref: martin2019) Martı́n, S., Martı́n-Pintado, J., Blanco-Sánchez, C., et al. 2019, A&A, 631, A159, doi: [`10.1051/0004-6361/201936144`](http://doi.org/10.1051/0004-6361/201936144)

(ref: martin2008) Martín, S., Requena-Torres, M. A., Martín-Pintado, J., & Mauersberger, R. 2008, The Astrophysical Journal, 678, 245, doi: [`10.1086/533409`](http://doi.org/10.1086/533409)

(ref: massalkhi2023) Massalkhi, S., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2023, A&A, 678, A45, doi: [`10.1051/0004-6361/202346822`](http://doi.org/10.1051/0004-6361/202346822)

(ref: McGuire:2016:1449) McGuire, B. A., Carroll, P. B., Loomis, R. A., et al. 2016, Science, 352, 1449, doi: [`10.1126/science.aae0328`](http://doi.org/10.1126/science.aae0328)

(ref: McGuire2016HNCS) McGuire, B. A., Martin-Drumel, M.-A., Thorwirth, S., et al. 2016, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 18, 22693, doi: [`10.1039/C6CP03871A`](http://doi.org/10.1039/C6CP03871A)

(ref: McGuire:2017:L46) McGuire, B. A., Shingledecker, C. N., Willis, E. R., et al. 2017, The Astrophysical Journal, 851, L46, doi: [`10.3847/2041-8213/aaa0c3`](http://doi.org/10.3847/2041-8213/aaa0c3)

(ref: MP2) Møller, C., & Plesset, M. S. 1934, Physical Review, 46, 618, doi: [`10.1103/PhysRev.46.618`](http://doi.org/10.1103/PhysRev.46.618)

(ref: Neill:2012:153) Neill, J. L., Muckle, M. T., Zaleski, D. P., et al. 2012, The Astrophysical Journal, 755, 153, doi: [`10.1088/0004-637X/755/2/153`](http://doi.org/10.1088/0004-637X/755/2/153)

(ref: pickett1998) Pickett, H., Poynter, R., Cohen, E., et al. 1998, J. Quant. Spectrosc. Rad. Transfer, 60, 883, doi: [`https://doi.org/10.1016/S0022-4073(98)00091-0`](http://doi.org/https://doi.org/10.1016/S0022-4073(98)00091-0)

(ref: Pickett1991) Pickett, H. M. 1991, J. Mol. Spectrosc., 148, 371

(ref: RAGHAVACHARI1989479) Raghavachari, K., Trucks, G. W., Pople, J. A., & Head-Gordon, M. 1989, Chemical Physics Letters, 157, 479, doi: [`https://doi.org/10.1016/S0009-2614(89)87395-6`](http://doi.org/https://doi.org/10.1016/S0009-2614(89)87395-6)

(ref: Reid:2014:130) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2014, The Astrophysical Journal, 783, 130, doi: [`10.1088/0004-637X/783/2/130`](http://doi.org/10.1088/0004-637X/783/2/130)

(ref: rivilla2018) Rivilla, V. M., Martı́n-Pintado, J., Jiménez-Serra, I., et al. 2018, MNRAS: Letters, 483, L114, doi: [`10.1093/mnrasl/sly228`](http://doi.org/10.1093/mnrasl/sly228)

(ref: rivilla_abundant_2019) Rivilla, V. M., Martín-Pintado, J., Jiménez-Serra, I., et al. 2019, Monthly Notices of the Royal Astronomical Society: Letters, 483, L114, doi: [`10.1093/mnrasl/sly228`](http://doi.org/10.1093/mnrasl/sly228)

(ref: rivilla2020b) Rivilla, V. M., Martı́n-Pintado, J., Jiménez-Serra, I., et al. 2020, ApJL, 899, L28, doi: [`10.3847/2041-8213/abac55`](http://doi.org/10.3847/2041-8213/abac55)

(ref: rivilla2021a) Rivilla, V. M., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2021a, Proceedings of the National Academy of Science, 118, 2101314118, doi: [`10.1073/pnas.2101314118`](http://doi.org/10.1073/pnas.2101314118)

(ref: rivilla2021b) Rivilla, V. M., Jiménez-Serra, I., Garcı́a de la Concepción, J., et al. 2021b, MNRAS, 506, L79, doi: [`10.1093/mnrasl/slab074`](http://doi.org/10.1093/mnrasl/slab074)

(ref: rivilla2022a) Rivilla, V. M., Colzi, L., Jiménez-Serra, I., et al. 2022a, ApJL, 929, L11, doi: [`10.3847/2041-8213/ac6186`](http://doi.org/10.3847/2041-8213/ac6186)

(ref: rivilla2022b) Rivilla, V. M., Garcı́a De La Concepción, J., Jiménez-Serra, I., et al. 2022b, Frontiers in Astronomy and Space Sciences, 9, 829288, doi: [`10.3389/fspas.2022.829288`](http://doi.org/10.3389/fspas.2022.829288)

(ref: rivilla2022c) Rivilla, V. M., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2022c, Frontiers in Astronomy and Space Sciences, 9, 876870, doi: [`10.3389/fspas.2022.876870`](http://doi.org/10.3389/fspas.2022.876870)

(ref: rivilla2023) Rivilla, V. M., Sanz-Novo, M., Jiménez-Serra, I., et al. 2023, ApJL, 953, L20, doi: [`10.3847/2041-8213/ace977`](http://doi.org/10.3847/2041-8213/ace977)

(ref: Robinson1953) Robinson, G. W., & Cornwell, C. D. 1953, The Journal of Chemical Physics, 21, 1436, doi: [`10.1063/1.1699275`](http://doi.org/10.1063/1.1699275)

(ref: Rodriguez-Almeida2021) Rodrı́guez-Almeida, L. F., Jiménez-Serra, I., Rivilla, V. M., et al. 2021a, ApJL, 912, L11, doi: [`10.3847/2041-8213/abf7cb`](http://doi.org/10.3847/2041-8213/abf7cb)

(ref: rodriguez-almeida2021b) Rodrı́guez-Almeida, L. F., Rivilla, V. M., Jiménez-Serra, I., et al. 2021b, A&A, 654, L1, doi: [`10.1051/0004-6361/202141989`](http://doi.org/10.1051/0004-6361/202141989)

(ref: rodriguez-almeida2021a) Rodrı́guez-Almeida, L. F., Jiménez-Serra, I., Rivilla, V. M., et al. 2021c, ApJL, 912, L11, doi: [`10.3847/2041-8213/abf7cb`](http://doi.org/10.3847/2041-8213/abf7cb)

(ref: san-andres2024) San Andrés, D., Rivilla, V. M., Colzi, L., et al. 2024, arXiv e-prints, arXiv:2404.03334, doi: [`10.48550/arXiv.2404.03334`](http://doi.org/10.48550/arXiv.2404.03334)

(ref: sanz-novo2023) Sanz-Novo, M., Rivilla, V. M., Jiménez-Serra, I., et al. 2023, arXiv e-prints, arXiv:2307.08644, doi: [`10.48550/arXiv.2307.08644`](http://doi.org/10.48550/arXiv.2307.08644)

(ref: Sanz-Novo2024a) —. 2024a, arXiv e-prints, arXiv:2402.15405, doi: [`10.48550/arXiv.2402.15405`](http://doi.org/10.48550/arXiv.2402.15405)

(ref: Sanz-Novo2024b) Sanz-Novo, M., Rivilla, V. M., Müller, H. S. P., et al. 2024b, arXiv e-prints, arXiv:2404.01044, doi: [`10.48550/arXiv.2404.01044`](http://doi.org/10.48550/arXiv.2404.01044)

(ref: shingledecker_grain-surface_2022) Shingledecker, C. N., Banu, T., Kang, Y., et al. 2022, Journal of Physical Chemistry A, 126, 5343, doi: [`10.1021/acs.jpca.2c01447`](http://doi.org/10.1021/acs.jpca.2c01447)

(ref: shingledecker_case_2019) Shingledecker, C. N., Álvarez Barcia, S., Korn, V. H., & Kästner, J. 2019, The Astrophysical Journal, 878, 80, doi: [`10.3847/1538-4357/ab1d4a`](http://doi.org/10.3847/1538-4357/ab1d4a)

(ref: Tercero2021) Tercero, F., López-Pérez, J. A., Gallego, J. D., et al. 2021, A&A, 645, A37, doi: [`10.1051/0004-6361/202038701`](http://doi.org/10.1051/0004-6361/202038701)

(ref: Turner:1991:617) Turner, B. E. 1991, The Astrophysical Journal Supplement Series, 76, 617, doi: [`10.1086/191577`](http://doi.org/10.1086/191577)

(ref: vidal_reservoir_2017) Vidal, T. H. G., Loison, J.-C., Jaziri, A. Y., et al. 2017, Monthly Notices of the Royal Astronomical Society, 469, 435, doi: [`10.1093/mnras/stx828`](http://doi.org/10.1093/mnras/stx828)

(ref: Watson1977) Watson, J. K. G. 1977, in Vibrational Spectra and Structure, ed. J. R. Durig, Vol. 6 (Amsterdam: Elsevier), 1–89

(ref: MOLPRO_brief) Werner, H.-J., Knowles, P. J., et al. 2020, MOLPRO, 2020.2 , a package of ab initio programs. <https://www.molpro.net>

(ref: Wierzejewska2003) Wierzejewska, M., & Moc, J. 2003, The Journal of Physical Chemistry A, 107, 11209, doi: [`10.1021/jp030971b`](http://doi.org/10.1021/jp030971b)

(ref: zeng_complex_2018) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, Monthly Notices of the Royal Astronomical Society, 478, 2962, doi: [`10.1093/mnras/sty1174`](http://doi.org/10.1093/mnras/sty1174)

(ref: zeng2021) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2021, ApJL, 920, L27, doi: [`10.3847/2041-8213/ac2c7e`](http://doi.org/10.3847/2041-8213/ac2c7e)

(ref: zeng2023) Zeng, S., Rivilla, V. M., Jiménez-Serra, I., et al. 2023, MNRAS, doi: [`10.1093/mnras/stad1478`](http://doi.org/10.1093/mnras/stad1478)

(ref: Zernickel:2012:A87) Zernickel, A., Schilke, P., Schmiedeke, A., et al. 2012, Astronomy and Astrophysics, 546, A87, doi: [`10.1051/0004-6361/201219803`](http://doi.org/10.1051/0004-6361/201219803)

[^1]: Madrid Data Cube Analysis on ImageJ is a software developed at the Center of Astrobiology (CAB) in Madrid; http://cab.inta-csic.es/madcuba/

[^2]: **Q**-band **U**ltrasensitive **I**nspection **J**ourney to the **O**bscure **T**MC-1 **E**nvironment

[^3]: `https://nanocosmos.iff.csic.es/`

[^4]: `https://nanocosmos.iff.csic.es/?page`$\_$`id=1619`

</paper>

Write the methods card for this paper.