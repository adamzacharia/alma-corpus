# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025ApJ...992..187F\sonnetcc\reply.txt

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
 "bibcode": "2025ApJ...992..187F",
 "title": "Rotational Spectroscopy and Tentative Interstellar Detection of 3-hydroxypropanal (HOCH<SUB>2</SUB>CH<SUB>2</SUB>CHO) in the G+0.693-0.027 Molecular Cloud",
 "year": 2025,
 "journal": "The Astrophysical Journal",
 "first_author": "Fried, Zachary T. P.",
 "n_authors": 15,
 "arxiv_id": "2508.15911",
 "doi": "10.3847/1538-4357/adfc62",
 "alma_projects_linked_by_archive": [
  "2012.1.00712.S",
  "2013.1.00278.S",
  "2015.1.00150.S",
  "2015.A.00022.T",
  "2016.1.00074.S",
  "2016.1.00383.S",
  "2017.1.00661.S"
 ]
}
```

Paper text:
<paper>
# Rotational Spectroscopy and Tentative Interstellar Detection of 3-Hydroxypropanal () in the G+0.693-0.027 Molecular Cloud

## Abstract

We synthesized the astrochemically relevant molecule 3-hydroxypropanal () and subsequently measured and analyzed its rotational spectrum in several frequency regions ranging from 130 to 485 GHz. We analyzed the ground vibrational state as well as the two perturbed lowest-lying vibrationally excited states. With the resulting rotational parameters, we searched for this molecule in the Sagittarius B2(N) and NGC 6334I hot cores, the IRAS 16293-2422B hot corino, and the G+0.693-0.027 and TMC-1 molecular clouds. Rotational emission of 3-hydroxypropanal was tentatively detected toward G+0.693-0.027 and a column density of (8.6$\pm$1.4)$\times$10$^{12}$ cm$^{-2}$ was determined. However, this molecule was not detected in the other sources that were investigated. The chemical implications of this tentative discovery are analyzed and several potential chemical formation pathways of this species are discussed.

# Introduction

Recently, the isomers have been of particular astrochemical interest. Three of these isomers, namely ethyl formate (cite: ethyl_formate; rivilla_ethylformate_2017; peng_alma_2019), methyl acetate (cite: methyl_acetate), and hydroxyacetone (cite: hydroxyacetone), have been detected toward various interstellar sources. That being said, the most thermodynamically stable isomer propanoic acid was not detected in searches toward Orion KL and Sagittarius (Sgr) B2 (cite: ilyushin_submillimeter_2021; 2025A&A...698A.143B), thus suggesting that the gas-phase interstellar abundances do not solely follow trends of thermodynamic stability – a phenomenon observed in several other isomeric families (e.g. (cite: loomis_investigating_2015; shingledecker_case_2019; mininni_guapos_2020; agundez_chemistry_2023; rivilla_first_2023; san_andres_first_2024)). The higher-energy isomers methoxyacetaldehyde (cite: methoxyacetaldehyde) and lactaldehyde (also known as 2-hydroxypropanal) (cite: lactaldehyde) were also not detected in searches toward these same star-forming regions.

An additional isomer of astrochemical interest is 3-hydroxypropanal (). This species has been recommended as a strong detection target by several groups (e.g. (cite: wang23), (cite: fried)). Notably, (cite: wang23) recently investigated the formation of various isomers from methanol-acetaldehyde ices that were irradiated with energetic electrons at low temperatures, simulating molecular cloud conditions. They ultimately observed the formation of hydroxyacetone and methyl acetate (which were both detected in the interstellar medium) along with 3-hydroxypropanal. They note that 3-hydroxypropanal is formed via the recombination of the and radicals, which may be hydrogen loss products of methanol and acetaldehyde:

$$\begin{equation}
 \label{eq:radical_recomb}
        \ce{CH2OH + CH2CHO -> HOCH2CH2CHO}
\end{equation}$$

Prop-1-ene-1,3-diol, which is the enol tautomer of 3-hydroxypropanal, was also observed. (cite: wang23) proposed that this species forms from keto-enol tautomerization of 3-hydroxypropanal, which has been shown to be possible in irradiated ice experiments that mimic the interaction of cosmic rays with interstellar ices under molecular cloud conditions (cite: kleimeier_interstellar_2021).

Additionally, (cite: wang_interstellar_2024) also observed that 3-hydroxypropanal was formed (along with lactaldehyde, ethyl formate, and prop-1-ene-1,3-diol) in irradiated CO-ethanol ices via Reaction [\[eq:radical_recomb2\]](#eq:radical_recomb2):

$$\begin{equation}
 \label{eq:radical_recomb2}
        \ce{HCO + CH2CH2OH -> HOCH2CH2CHO}
\end{equation}$$

Moreover, 3-hydroxypropenal () was detected toward IRAS 16293-2422B (cite: hydroxypropenal; muller_rotation-tunneling_2024). This molecule is structurally similar to 3-hydroxypropanal, with the only difference being a single extra degree of unsaturation. The formation pathway of this molecule is also proposed to have commonalities with 3-hydroxypropanal, as they both stem from reactions with the radical (cite: hydroxypropenal). This further suggests that 3-hydroxypropanal may be generated in this source.

In order to detect this molecule in radio astronomical observations, we must first measure and analyze its rotational spectrum. For detection in the star-forming regions in which other isomers have been observed, an analysis of the millimeter and sub-millimeter wave spectrum is necessary. The warm temperatures of these regions, possibly reaching several hundred Kelvin, cause the most intense rotational transitions to occur within these frequency ranges. That being said, a rotational investigation of this molecule had not been previously conducted. Therefore, in this work, we synthesized 3-hydroxypropanal and subsequently collected and fitted its millimeter and sub-millimeter wave rotational spectrum. This rotational data then enabled a search for the molecule in the Sgr B2(N) and NGC 6334I hot cores, the IRAS 16293-2422B hot corino, and the G+0.693-0.027 and TMC-1 molecular clouds. Section [\[sec:calc\]](#sec:calc) outlines the quantum chemical calculations performed to support the experiments. Sections [3](#sec:exp_description) and [4](#sec:exp_results) then detail the experimental procedure to synthesize the molecule along with the spectroscopic experiments and results. Finally, in Section [5](#sec:obs_results), we present the observational search for 3-hydroxypropanal in the various interstellar sources and discuss some potential chemical formation pathways of this species.

# Quantum Chemical Calculations

The conformational space of 3-hydroxypropanal is potentially vast due to the three single-bond rotations in its backbone. In order to determine which conformers would be present in our experimental sample, we conducted a conformational search using a Mixed torsional/Large-Scale Low-Mode sampling method as implemented in MacroModel (cite: mohamadi_macromodelintegrated_1990). For each identified conformer, the geometries were optimized, and zero-point corrected energies were calculated using Gaussian 16 (cite: g16) with the B3LYP/6-311++G(3df,2pd) functional and basis set. (cite: Masato2001) reported four possible forms of 3-hydroxypropanal, however, we obtained 13 conformations in the energy window of 16 kJ/mol. For the four most stable conformers, we then re-calculated the relative energies with the CCSD/aug-cc-pVDZ level of theory. The relative energies and dipole moments of these four conformers are displayed in Figure [1](#fig:conformers).

![](conformer_figure.png)

Conformer 1 was predicted as the most stable form of 3-hydroxypropanal also by (cite: Masato2001). It adopts a pseudo cyclic structure in which the hydroxyl hydrogen and carbonyl oxygen are in close proximity and thus allow for a stabilizing intramolecular hydrogen bonding interaction. This intramolecular hydrogen bonding results in Conformer 1 being 6.7 kJ/mol (803 K) more stable than the next conformation which has an extended structure. Therefore, it is the only conformer that is expected to have a notable population in our spectrum. Of the four displayed conformers, Conformer 1, 3, and 4 all have two equivalent configurations connected by rotations around single bonds. This effective doubling increases the statistical weight of Conformer 1, further making it the predominant species in the gas phase of our sample. To guide its assignment, rotational constants, centrifugal distortion constants, and electric dipole moment components were calculated at three different levels of theory: B2PLYPD3/6-311++G(3df,2pd) and MP2/aug-cc-pVTZ as implemented in the Gaussian 16 software (cite: g16), and CCSD/aug-cc-pVDZ available in the CFOUR program package (cite: cfour). The harmonic and anharmonic force field calculations were carried out in all cases. The convergence criteria for energies were set to 10$^{-11}$ atomic units. The obtained sets of spectroscopic parameters are provided in Table [\[table:constants\]](#table:constants).

![](3-HP-spectrum.png)

# Experimental Description

## Synthesis of 3-Hydroxypropanal

The synthesis of (cite: roldan) was modified to obtain the product in the gas phase. 3,3-Diethoxy-1-propanol (1.0 g, 6.75 mmol) was slowly added to a cooled (0°C) 1 M aqueous solution of (5 mL). The reaction was stirred at 20 °C for 30 minutes. This mixture was then added to a suspension of (6.3 g, 75 mmol) in dichloromethane (50 mL). At the end of bubbling, the organic phase was separated and the residual organic compounds in the aqueous phase extracted twice with dichloromethane (25 mL). The organic phases were mixed and dried over . After filtration, the solvent was removed at room temperature under vacuum until approximately 2-3 mL of solution was obtained. 3-hydroxypropanal was purified by trap-to-trap distillation under vacuum (0.1 mbar) and selective trapping in a U-tube immersed in a bath cooled at –40°C. (Yield: 0.17 g, 2.3 mmol, 34%). Revaporization in the cell of the spectrometer enabled the millimeter wave spectrum to be recorded.

3-Hydroxypropanal is not very kinetically stable in pure form at room temperature in the condensed phase. The use of a crude mixture (obtained after evaporation of the solvent at 0°C under 0.1 mbar before connecting the sample to the spectrometer cell) stabilizes the product considerably, but ethanol was also observed in the spectrum. The yield of the product (based on the starting material 3,3-diethoxy-1-propanol) vaporized in the gas phase is no greater than 20%.

The following is the nuclear magnetic resonance (NMR) data for the synthesized molecule: $^{1}$H NMR (, 400 MHz) $\delta$ 9.87 (t, 1H, $^{3}$J~HH~ = 1.0 Hz, CHO), 3.96 (t, 2H, $^{3}$J~HH~ = 5.4 Hz, ), 2.77 (2H, td, $^{3}$J~HH~ = 5.4, 1.0 Hz, ). $^{13}$C NMR (, 100 MHz) $\delta$ 202.4 (CHO), 56.5 (), 46.1 ().

## Spectroscopic Experiments

The rotational spectrum of 3-hydroxypropanal was measured in the frequency region 130–485 GHz using two spectrometers. The frequency-modulated absorption spectrum was first measured at room temperature over most of the frequency range spanning $150-190\,$GHz, $225-325\,$GHz, and $367-485\,$GHz using the FLASH (Fast Lille Absorption emiSsion High resolution) spectrometer (cite: lille; fast_scan; zou2020). Its fast scan design is achieved by mixing a direct digital synthesizer (DDS) signal with the signal from an Agilent synthesizer (up to 20 GHz), followed by a multiplication chain consisting of various passive and active multipliers. The FLASH spectrometer is particularly notable for incorporating the chirped-pulse technique. While this technique is well-established in the centimeter range, its application in the THz domain is still innovative, making the FLASH spectrometer a unique and versatile tool capable of operating up to 1.5 THz in absorption mode and 0.5 THz in chirped-pulse mode. Due to the instability of 3-hydroxypropanal, the measurements were conducted in “flow" mode. In this configuration, the spectrometer features a 220 cm long Pyrex glass tube with a 10 cm diameter and Teflon windows. The sample was continuously injected into the cell and pumped out from the opposite side.

In this specific experiment, the frequency was modulated at $40.5\,$kHz, and $2f$ frequency demodulation was employed. Once again, because of the low molecular stability, the frequency range needed to be scanned fairly quickly. Thus, a frequency step 20% larger than usual was used, ranging from 36 kHz at 150 GHz to 63 kHz at 400 GHz and above. The step size was increased at higher frequencies due to the heightened Doppler broadening of the lines. Throughout most of the frequency range, the spectra were averaged four times and the scanning rate was 1 ms/point. The sample pressure and temperature during measurements were about 2-3 Pa and room temperature. Absorption signals were detected by zero-bias Schottky diodes.

The Prague semiconductor millimeter wave spectrometer (cite: Kania2006) was also used to record the spectra in selected sections between 130 and 175 GHz. The required frequencies were obtained by multiplying the Agilent synthesizer produced frequency ($\leq$50 GHz) using a tripler or a pair of doublers. The synthesizer output was modulated at a frequency of 28 kHz. The stability of the sample signal was ensured by establishing a slow flow through the Pyrex free-space cell (8 cm in diameter, 280 cm long) at a pressure of around 4 Pa. The optical path length was doubled using a roof-top mirror. The signal was detected by zero-bias detectors and further processed by a lock-in amplifier that was tuned to twice the modulation frequency. The final spectrum was obtained as an average of scans sweeping forwards and backwards in a double acquisition cycle.

The estimated frequency uncertainties over the entire measurement range were either 30 kHz, 50 kHz, or, in a small number of cases, 100 kHz. These uncertainties were primarily determined by the signal-to-noise ratio of each line. For instance, strong b-type R branch transitions of the ground state generally had uncertainties of 30 kHz, while some very weak a-type lines were assigned uncertainties of 100 kHz.

# Spectroscopic Analysis and Results

## Ground State

The fit was initiated using a simulated spectrum that was generated with the theoretical ground state rotational constants and distortion constants using SPCAT in Pickett’s CALPGM suite of programs (cite: spcat). Overall, the fit contains 1194 distinct transition frequencies. Including blended lines, this corresponds to 2342 transitions in the fit. The transitions range from $J^{\prime} = 8-76$ and $K_a^{\prime} = 0-40$. Because this molecule is a relatively prolate asymmetric top ($\kappa = -0.642$), the fit was conducted with the A reduction and $I^r$ representation using ASFIT (cite: asfit). The values of each of the determined rotational and centrifugal distortion constants are listed in Table [\[table:constants\]](#table:constants). Because Conformer 1 has a large b-type electric dipole moment component, 1794 of the fitted transitions are b-type. As displayed in Figure [2](#fig:spectrum), the strongest lines correspond to the low $K_a$ R-branch b-type transitions. Several of the high $K_a$ (e.g. $K_a{\prime} = 24-40$) Q-branch b-type transitions were also measured and fitted, albeit with much lower line intensities. The remaining 548 transitions in the fit were a-type lines; however, a fairly notable number of these are blended with b-type transitions (i.e. overlapping a-type and b-type R-branch transitions). The unblended a-type lines were generally very weak due to the smaller a-type dipole moment component. No c-type transitions were observed. The calculated rotational constants of Conformer 1 agree with the experimentally determined values within 3% for each of the functional/basis set combinations. The signs and magnitudes of the computed centrifugal distortion constants also agree well with the experimental values. Following the fitting using ASFIT, the determined parameters were outputted by the program in the file format required for SPFIT/SPCAT. Thus, we subsequently used these resulting files to produce a spectroscopic catalog in the standard .cat format using SPCAT to compare the fitted spectrum (including line intensities) to both our experimental and astronomical data. The spectroscopic catalog along with both the ASFIT and SPCAT files are provided in the Supplementary Information. The predicted spectra are also available in different formats including standard .cat format (cite: spcat) from the new database of the Lille spectroscopy group called the Lille Spectroscopic Database[^1]. The predictions can be generated using various options (e.g., intensity units, temperature, and frequency range) that provide additional flexibility in the data access. The partition function of 3-hydroxypropanal is listed in Table [1](#table:partition). The rotational partition function was calculated with SPCAT by simulating the spectrum up to $J$ = 200. The vibrational partition function was computed using the approximation formalism presented in (cite: gordy_cooke) with the anharmonic CCSD/aug-cc-pVDZ fundamental vibrational mode frequencies. The total partition function was calculated as $Q_{\mbox{vib}} (T) \times Q_{\mbox{rot}} (T)$ at each temperature.

Note that in the calculation of higher-order spectroscopic constants (e.g., centrifugal distortion and Coriolis coupling constants), the choice of quantum chemical method plays a critical role. Although B3LYP/6-311++G(3df,2pd) offers a clear advantage in terms of computational efficiency, it often falls short in accurately describing these properties due to its limited treatment of electron correlation. In a previous study on the FSO$_3$ radical (cite: Uhlikova_fso3_2011), several computational approaches were evaluated for the calculation of higher-order spectroscopic constants. The results demonstrated that CCSD yielded the best agreement with experimental data, further highlighting the limitations of B3LYP in this context and reinforcing the theoretical robustness of coupled-cluster methods for spectroscopic applications. Nevertheless, using the anharmonic fundamental vibrational frequencies from the other two methods in Table [\[table:constants\]](#table:constants) results in vibrational partition functions that differ from CCSD by less than 2% at 300 K.

+--------------------------------------+-------------------------------------------------------+---+--------------------------------+
|                                      | Experiment                                            |   | Theory                         |
+:=====================================+:=================+:================+:=================+:==+:=========+:=========+:=========+
| 2-4 Parameter                        | Ground State     | $v_{27}=1$      | $v_{26}=1$       |   | I        | II       | III      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $A$ (MHz)                            | $8657.60135(34)$ | 8693.8551(12)   | 8688.5405(12)    |   | 8513     | 8661     | 8606     |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $B$ (MHz)                            | $4116.27295(17)$ | 4083.01(26)     | 4087.07(26)      |   | 3993     | 4054     | 4103     |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $C$ (MHz)                            | $3125.63135(11)$ | 3112.7252(10)   | 3114.7592(12)    |   | 3049     | 3089     | 3118     |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
|                                      |                  |                 |                  |   |          |          |          |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Delta_{J}$ (kHz)                   | $4.010060(69)$   | 4.4948(78)      | 3.6876(77)       |   | 3.663    | 3.675    | 3.834    |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Delta_{JK}$ (kHz)                  | $-9.53279(46)$   | $-$11.687(27)   | $-$8.722(28)     |   | $-$8.238 | $-$8.280 | $-$8.344 |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Delta_{K}$ (kHz)                   | 12.99819(71)     | 16.299(20)      | 12.487(22)       |   | 11.168   | 11.535   | 11.033   |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\delta_{J}$ (kHz)                   | 1.274532(30)     | 1.4779(40)      | 1.1381(39)       |   | 1.142    | 1.156    | 1.200    |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\delta_{K}$ (kHz)                   | 5.30738(43)      | \[5.30738\]     | 5.7674(25)       |   | 4.851    | 4.966    | 4.937    |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
|                                      |                  |                 |                  |   |          |          |          |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Phi_{J}$ (Hz)                      | $-$0.019624(13)  | $-$0.01875(10)  | $-$0.019507(11)  |   | $-$0.013 | $-$0.010 | $-$0.016 |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Phi_{JK}$ (Hz)                     | 0.12908(25)      | 0.10550(85)     | 0.16475(63)      |   | 0.095    | 0.086    | 0.110    |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Phi_{KJ}$ (Hz)                     | $-$0.28906(53)   | $-$0.3020(18)   | $-$0.3456(19)    |   | $-$0.223 | $-$0.220 | $-$0.241 |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\Phi_{K}$ (Hz)                      | 0.25706(76)      | 0.3476(17)      | \[0.25706\]      |   | 0.194    | 0.200    | 0.199    |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\phi_{J}$ (Hz)                      | $-$0.0091793(59) | $-$0.008748(50) | \[$-$0.0091793\] |   | $-$0.006 | $-$0.005 | $-$0.007 |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\phi_{JK}$ (Hz)                     | $-$0.06190(11)   | $-$0.07923(54)  | $-$0.05572(66)   |   | $-$0.037 | $-$0.032 | $-$0.041 |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\phi_{K}$ (Hz)                      | $-$0.08147(63)   | \[$-$0.08147\]  | \[$-$0.08147\]   |   | $-$0.037 | $-$0.018 | $-$0.046 |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
|                                      |                  |                 |                  |   |          |          |          |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $L_{JJK}$ (mHz)                      | 0.001124(38)     | \[0.001124\]    | \[0.001124\]     |   | ...      | ...      | ...      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $L_{JK}$ (mHz)                       | $-$0.00480(11)   | \[$-$0.00480\]  | \[$-$0.00480\]   |   | ...      | ...      | ...      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $L_{KKJ}$ (mHz)                      | 0.00828(15)      | \[0.00828\]     | \[0.00828\]      |   | ...      | ...      | ...      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $L_{K}$ (mHz)                        | $-$0.00664(25)   | \[$-$0.00664\]  | \[$-$0.00664\]   |   | ...      | ...      | ...      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
|                                      |                  |                 |                  |   |          |          |          |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $G_a$ (MHz)                          | ...              | \[1559.2\]                         |   | 1559.2   | 1544.6   | 1510.2   |
+--------------------------------------+------------------+------------------------------------+---+----------+----------+----------+
| $G_b$ (MHz)                          | ...              | 3088(54)                           |   | 2433.1   | 2463.8   | 2465.3   |
+--------------------------------------+------------------+------------------------------------+---+----------+----------+----------+
| $G_b^J$ (MHz)                        | ...              | $-$0.0534(23)                      |   | ...      | ...      | ...      |
+--------------------------------------+------------------+------------------------------------+---+----------+----------+----------+
| $G_b^K$ (MHz)                        | ...              | 0.1065(28)                         |   | ...      | ...      | ...      |
+--------------------------------------+------------------+------------------------------------+---+----------+----------+----------+
| $\Delta E$ (cm$^{-1}$)               | ...              | 43.8611(18)                        |   | 43.5     | 69.3     | 64.1     |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
|                                      |                  |                 |                  |   |          |          |          |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $|\mu_a|$ (D)                        | ...              | ...             | ...              |   | 1.0      | 1.0      | 1.0      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $|\mu_b|$ (D)                        | ...              | ...             | ...              |   | 2.8      | 2.8      | 2.8      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $|\mu_c|$ (D)                        | ...              | ...             | ...              |   | 0.1      | 0.1      | 0.2      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
|                                      |                  |                 |                  |   |          |          |          |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $N\textsubscript{lines}$             | 1194             | 484             | 316              |   | ...      | ...      | ...      |
+--------------------------------------+------------------+-----------------+------------------+---+----------+----------+----------+
| $\sigma\textsubscript{rms}$ (MHz)    | 0.0420           | 0.0635                             |   |          | ...      | ...      |
+--------------------------------------+------------------+------------------------------------+---+----------+----------+----------+
| $\sigma\textsubscript{rms,weighted}$ | 0.84             | 0.97                               |   |          | ...      | ...      |
+--------------------------------------+------------------+------------------------------------+---+----------+----------+----------+

I: CCSD/aug-cc-pVDZ, II: B2PLYPD3/6-311++g(3df,2pd), III: MP2/aug-cc-pVTZ. Rotational and centrifugal distortion constants correspond to the ground state.

Number of distinct frequencies included in the fit.

Bracketed distortion constants were fixed to the ground state values.

Fixed to value calculated at CCSD/aug-cc-pVDZ functional and basis set.

The $G_a$ and $G_b$ parameters from theory were determined using Equation [\[eq:coriolis\]](#eq:coriolis) with the computed $\zeta$ and energy values and the experimental ground state rotational constants.

Energy difference between the $v_{27}=1$ and $v_{26}=1$ states.

| Temperature (K) | $Q_{\mbox{rot}} (T)$ | $Q_{\mbox{vib}} (T)$ | $Q_{\mbox{tot}} (T)$ |
|:--:|:--:|:--:|:--:|
| 300.000 | 83321.061 | 8.99 | 749274.02 |
| 225.000 | 54070.707 | 4.20 | 227222.08 |
| 150.000 | 29408.229 | 2.06 | 60609.93 |
| 75.000 | 10391.237 | 1.16 | 12017.88 |
| 37.500 | 3674.599 | 1.01 | 3711.28 |
| 18.750 | 1300.583 | 1.00 | 1300.67 |
| 9.375 | 460.987 | 1.00 | 460.99 |

: Partition function of Conformer 1 of 3-hydroxypropanal.

## Vibrationally Excited States

The two lowest energy vibrationally excited states were also clearly visible in the spectrum. These were the $v_{27}=1$ and $v_{26}=1$ states. The corresponding normal vibrational modes are fairly similar torsional vibrations. The $v_{27}$ mode is predominantely a torsion around the C–C bond containing the aldehyde carbon. The $v_{26}$ mode is then a torsional motion around both C–C bonds with differing proportions. The two states were calculated to be 125.0 and 168.5 cm$^{-1}$ above the ground state, respectively. This computed difference of only 43.5 cm$^{-1}$ (63K, 0.52 kJ/mol) resulted in some observable Coriolis coupling between the two states that impacted a fairly small number of transitions. Therefore, these states were fitted with a combined fit using SPFIT code (cite: spcat). The PIFORM code (cite: kisiel_assignment_2001) was employed to format the output.

In general, the lines that displayed a notable and observable perturbation were typically the low-to-mid $K_a$ R-branch transitions. The most significant perturbations were Coriolis couplings of $\Delta K_a = 5$ beginning at $K_a^{\prime} = 1$ for $v_{26}=1$ and $K_a^{\prime} = 6$ for $v_{27}=1$. The frequency perturbations of the transition frequencies generally ranged from approximately 300 kHz to 4 MHz. An example of these perturbed transitions is displayed in the resonance plot in Figure [3](#fig:perturbation). Unfortunately, however, while there were clear perturbations of $v_{26}=1$ $K_a^{\prime} =$ 5 and 6 transitions, the perturbing counterparts $K_a^{\prime} =$ 10, 11, and 12 lines of $v_{27}=1$ became too weak to observe. Thus, there were only a very small number of paired perturbing transitions that we were able to include in the fit, making it challenging to constrain the required Coriolis coupling parameters. Additionally, since the largest observed perturbations in the transition frequencies were slightly above 4 MHz, these fairly small deviations further complicated the task of constraining the coupling parameters.

The fit was initialized with the computed energy difference between the two states, and the $G_a$ and $G_b$ parameters calculated using the following general equation:

$$\begin{equation}
G_a = \frac{\omega_{27}+\omega_{26}}{\sqrt{\omega_{27}\times\omega_{26}}}\zeta^{a}_{27,26}A
\label{eq:coriolis}
\end{equation}$$ where $\omega$ is the computed vibrational frequency of the two interacting modes, and $\zeta$ was computed from the anharmonic CCSD/aug-cc-pVDZ calculations. For computing $G_b$, Equation [\[eq:coriolis\]](#eq:coriolis) is used with $\zeta^{b}_{26,27}$ and $B$ substituted in. The fitting procedure was carried out using a conventional bootstrap approach. Initially, the parameter $\Delta E$ was fixed to a range of values between 35 and 55 cm$^{-1}$, while the parameter $G_b$ was allowed to vary. We then searched for a global minimum of the RMS deviation, following the method described by (cite: motiyenko_internal_2018). Once the global minimum was identified, $\Delta E$ was also treated as an adjustable parameter. Given the limited number of observed perturbed transitions, the final fit was performed by fixing $G_a$ to its computed value while allowing $G_b$, $\Delta E$, $G_b^{J}$, and $G_b^{K}$ to vary. $G_b^{J}$ and $G_b^{K}$ are centrifugal distortion correction terms to the $G_b$ Coriolis coupling constant. The frequency uncertainty of the perturbed transitions was extended to 100 kHz in the fit.

Ultimately, a total of 2172 transitions were included in the excited-state fit, corresponding to 800 distinct lines. The fitted rotational, distortion, and Coriolis coupling constants are displayed in Table [\[table:constants\]](#table:constants). The perturbed transitions are much more accurately reproduced using the two-state fit with Coriolis coupling parameters rather than single-state fits. However, some of these lines still exhibit notable deviations from the fit, leading to a relatively large RMS deviation of approximately 63 kHz. The unblended a-type transitions, which were already extremely weak in the ground state, are too faint to be observed in the spectrum for the vibrationally excited states. The energy difference between the two states from the fit is exceptionally close to the difference of the computed anharmonic fundamental frequencies from the CCSD/aug-cc-pVDZ calculation. Each of the fitted centrifugal distortion constants in the excited states have the same sign and similar magnitude to the ground state values. However, as can be seen, several of the centrifugal distortion constants in the two vibrationally excited states have fairly equal and opposite differences from the ground-state value. This is likely suggesting that a notable amount of the Coriolis coupling is being absorbed into the centrifugal distortion constants. If greater signal-to-noise ratio could be achieved in future work, more perturbed transitions could be included in the fit and the determined distortion and Coriolis-coupling constants could therefore be improved. However, due to the very unstable nature of the sample, this would likely be a challenging task.

![](perturbation.png)

# Observational Searches and Results

## G+0.693-0.027 Molecular Cloud

We have searched for 3-hydroxypropanal towards the Galactic Center molecular cloud G+0.693-0.027 (hereafter G+0.693), which is located in the Sgr B2 complex.

The molecular clouds in the Galactic Centre exhibit high gas kinetic temperatures ranging from $\sim$50 to $\sim$150 K ((cite: guesten1985; huettemeister1993; rodriguez-fernandez2001; ginsburg2016; krieger2017)), low dust temperatures of $\leq$ 20$-$30 K ((cite: rodriguez-fernandez2004; battersby2024)), and relatively low H$_2$ gas densities around $10^{4}\text{--}10^{5}$ cm$^{-3}$ ((cite: guesten1983; bally1987b; rodriguez-fernandez2000)).

The G+0.693 cloud, located around 55$^{\prime\prime}$ northeast of Sgr B2(N), is not an exception, and exhibits high kinetic temperatures of 70$-$150 K ((cite: Zeng2018)), and densities of 10$^{4\text{--}5}$ cm$^{-3}$ ((cite: zeng2020; colzi2022; colzi2024)).

![](3-hydroxypropanal693_revised.png)

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Frequency | Transition $^{(a)}$ | log *I* | *g*$\mathrm{_u}$ | $E$$\mathrm{_{up}}$ | Blending |  |  |  |  |  |
| (GHz) |  | (nm$^2$ MHz) |  | \(K\) |  |  |  |  |  |  |
| 32.1896471 (13) | 5$_{0,5}$ – 4$_{1,4}$ | –5.6326 | 11 | 5.0 | Slightly blended: |  |  |  |  |  |
| 32.8739195 (29) | 7$_{4,3}$ – 7$_{3,4}$ | –5.6233 | 15 | 13.6 | Slightly blended: |  |  |  |  |  |
| 35.3495481 (13) | 3$_{2,2}$ – 2$_{1,1}$ | –5.8750 | 7 | 3.0 | U-line |  |  |  |  |  |
| 39.0659430 (15) | 6$_{0,6}$ – 5$_{1,5}$ | –5.3517 | 13 | 6.9 | $c$- |  |  |  |  |  |
| 40.6636428 (15) | 6$_{1,6}$ – 5$_{0,5}$ | –5.3091 | 13 | 6.9 |  |  |  |  |  |  |
| 45.6874831 (17) | 7$_{0,7}$ – 6$_{1,6}$ | –5.1292 | 15 | 9.1 | Slightly blended: |  |  |  |  |  |
| 46.5490784 (17) | 7$_{1,7}$ – 6$_{0,6}$ | –5.1103 | 15 | 9.1 | Unblended |  |  |  |  |  |
| 78.9556730 (29) | 6$_{4,2}$ – 5$_{3,3}$ | –4.8794 | 13 | 11.1 |  |  |  |  |  |  |
| 81.5594297 (34) | 5$_{5,1}$ – 4$_{4,0}$ | –4.7334 | 11 | 11.2 |  |  |  |  |  |  |
| 81.5605329 (34) | 5$_{5,0}$ – 4$_{4,1}$ | –4.7334 | 11 | 11.2 |  |  |  |  |  |  |
| 88.1236563 (27) | 13$_{1,12}$ – 12$_{2,11}$ | –4.3761 | 27 | 31.2 |  |  |  |  |  |  |
| 96.1288496 (35) | 7$_{5,2}$ – 6$_{4,3}$ | –4.6019 | 15 | 15.7 | Unblended |  |  |  |  |  |
| 97.0383121 (32) | 9$_{4,6}$ – 8$_{3,5}$ | –4.7138 | 19 | 19.5 | Slightly blended: |  |  |  |  |  |
| 98.8733057 (40) | 6$_{6,1}$ – 5$_{5,0}$ | –4.4842 | 13 | 11.2 |  |  |  |  |  |  |
| 98.8733818 (40) | 6$_{6,0}$ – 5$_{5,1}$ | –4.4842 | 13 | 11.2 |  |  |  |  |  |  |
| 102.3378081 (33) | 16$_{0,16}$ – 15$_{1,15}$ | –4.0589 | 33 | 42.3 |  |  |  |  |  |  |
| 102.3381298 (33) | 16$_{1,16}$ – 15$_{1,15}$ | –4.9124 | 33 | 42.3 |  |  |  |  |  |  |
| 102.3385252 (33) | 16$_{0,16}$ – 15$_{0,15}$ | –4.9124 | 33 | 42.3 |  |  |  |  |  |  |
| 102.3388468 (33) | 16$_{1,16}$ – 15$_{0,15}$ | –4.0589 | 33 | 42.3 |  |  |  |  |  |  |
| 106.1583426 (40) | 7$_{6,2}$ – 6$_{5,1}$ | –4.4294 | 15 | 18.3 | Unblended |  |  |  |  |  |
| 106.1591837 (40) | 7$_{6,1}$ – 6$_{5,2}$ | –4.4294 | 15 | 18.3 | Unblended |  |  |  |  |  |
| 113.4294989 (40) | 8$_{6,3}$ – 7$_{5,2}$ | –4.3771 | 17 | 21.1 | and $n$- |  |  |  |  |  |
| 113.4345521 (40) | 8$_{6,2}$ – 7$_{5,3}$ | –4.3771 | 17 | 21.1 | and $n$- |  |  |  |  |  |
| 133.4964353 (49) | 8$_{8,1}$ – 7$_{7,0}$ | –4.1035 | 17 | 27.8 |  |  |  |  |  |  |
| 133.4964356 (49) | 8$_{8,0}$ – 7$_{7,1}$ | –4.1035 | 17 | 27.8 |  |  |  |  |  |  |
| 138.0143053 (45) | 10$_{7,4}$ – 9$_{6,3}$ | –4.1474 | 21 | 30.8 |  |  |  |  |  |  |
| 138.0165330 (45) | 10$_{7,3}$ – 9$_{6,4}$ | –4.1474 | 21 | 30.8 |  |  |  |  |  |  |
| 140.7843737 (48) | 9$_{8,2}$ – 8$_{7,1}$ | –4.0650 | 19 | 30.9 | AgG’-(CH$_2$OH)$_2$ |  |  |  |  |  |
| 140.7843783 (48) | 9$_{8,1}$ – 8$_{7,2}$ | –4.0650 | 19 | 30.9 | AgG’-(CH$_2$OH)$_2$ |  |  |  |  |  |
| 145.2523185 (44) | 11$_{7,5}$ – 10$_{6,4}$ | –4.1089 | 23 | 34.7 |  |  |  |  |  |  |
| 145.2612631 (45) | 11$_{7,4}$ – 10$_{6,5}$ | –4.1088 | 23 | 34.7 |  |  |  |  |  |  |

Due to the low H$_2$ densities, the molecules are generally sub-thermally excited, and hence the excitation temperatures in most cases are significantly lower than the gas kinetic temperatures ($\sim$5$–$20 K; (cite: requena-torres2006; martin2008tracing; Zeng2018; Jimenez-Serra2020; Rivilla2022_nitriles)). For this reason, the resulting spectra are less crowded than in high-$T_{\rm ex}$ sources such as hot cores/corinos, which alleviates line confusion, and helps the identification of new interstellar molecules. Moreover, the region harbors large-scale shocks, as seen through the bright emission of SiO and HNCO, which has been attributed to a cloud-cloud collision ((cite: zeng2020)). These shocks have sputtered the icy mantles of dust grains, ejecting into the gas phase molecules formed via grain surface chemistry. Furthermore, the high cosmic-ray ionization rate of the cloud, 10$^{-14}-$10$^{-15}$ s$^{-1}$, inferred by the chemical modeling of molecular cations such as PO$^+$ and HOCS$^+$ ((cite: Rivilla2022_PO+; Sanz-Novo2024a)), has been proposed to trigger the formation of reactive radicals on the ices, which can rapidly combine in-situ to synthetize more complex molecules ((cite: rivilla_first_2023)). From all this, G+0.693 stands as one of the most chemically rich reservoirs in the Galaxy, and nearly 25 new interstellar species have been discovered towards this source (e.g. (cite: Rivilla2020b; Rivilla2021a; rivilla_first_2023)), including complex O-bearing species such as (*Z*)-1,2-ethenediol ((CHOH)$_2$, (cite: Rivilla2022a)), propanol (C$_3$H$_7$OH; (cite: Jimenez-Serra2022)), and carbonic acid (HOCOOH; (cite: Sanz-Novo2023)). Moreover, other O-bearing molecules such as propenal or propanal are abundant toward this source ((cite: requena-torres_galactic_2008)), which makes G+0.693 a good target for the interstellar search of 3-hydroxypropanal.

We used an ultra-sensitive spectral survey towards this cloud that comprised $Q$-band observations at centimeter wavelengths (31.075-50.424 GHz), conducted with the Yebes 40$\,$m radiotelescope (Guadalajara, Spain), and observations across several millimeter-wavelength frequency windows (83.2–115.41 GHz, 132.28–140.39 GHz, and 142.00–173.81 GHz), conducted with the 30$\,$m IRAM radio telescope in Granada (Spain). The position switching mode was used, centered at $\alpha$ = $\,$17$^{\rm h}$47$^{\rm m}$22$^{\rm s}$, $\delta$ = $\,-$28$^{\circ}$21$^{\prime}$27$^{\prime\prime}$, with the off position shifted by $\Delta\alpha$ = $-885$$^{\prime\prime}$ and $\Delta\delta$ = $290$$^{\prime\prime}$. The half power beam width (HPBW) of the Yebes 40$\,$m telescope varies between $\sim$35$^{\prime\prime}$-55$^{\prime\prime}$ (at 50 and 31 GHz, respectively; (cite: Tercero2021)) and the HPBW of the IRAM 30$\,$m radiotelescope is $\sim$14$^{\prime\prime}$$-$29$^{\prime\prime}$ across the frequency range covered. The line intensity of the spectra is presented in units of antenna temperature ($T_{\mathrm{A}}^{\ast}$) since the molecular emission towards G+0.693 is extended beyond the telescope primary beams ((cite: Brunken2010; Jones2012; Li2020; Santa-Maria2021; colzi2024)). Further details on these observations, including resolution and final noise levels of the molecular line survey, are given in (cite: rivilla_first_2023) and (cite: Sanz-Novo2023). We note that for the frequency ranges not covered by these new observations, we used data from our previous IRAM 30m survey (see (cite: Rodriguez-Almeida2021a) for additional information).

We implemented the spectroscopic entry of 3-hydroxypropanal into the analysis software MADCUBA[^2]. Using the Spectral Line Identification and Modelling (SLIM) tool of the MADCUBA package (cite: Martin2019), we generated the expected local thermodynamic equilibrium (LTE) synthetic spectra of 3-hydroxypropanal to search for it in the G+0.693 spectral survey. We note that, given the low excitation temperatures of the molecules in G+0.693 (as described above), we did not include the vibrational contribution to the partition function ($Q_{\mbox{vib}}$) in this case.

In Figure [4](#f:LTEspectrumG0693) we show the brightest transitions of 3-hydroxypropanal, according to the LTE modeled spectra, some of which have been tentatively identified toward G+0.693. Their spectroscopic information is reported in Table [\[tab:transitions693\]](#tab:transitions693). Besides the clear detection of several relatively bright $b$-type $R$-branch lines, only a few appear to be unblended or only slightly blended with the emission from other molecules previously detected in this cloud. We highlight the 7$_{6,2}$ – 6$_{5,1}$ and 7$_{6,1}$ – 6$_{5,2}$ transitions (located at 106.1483426 GHz and 106.1591837 GHz, respectively) which coalesce into a single, stronger spectral feature owing to the broad linewidths of the molecular emission observed in this source (FWHM $\sim$ 15$-$20 km s$^{-1}$; (cite: Requena-Torres2008; Zeng2018; Rivilla2022_nitriles)), and the 7$_{0,7}$ – 6$_{1,6}$ transition (located at 45.6874831 GHz) that is only slightly contaminated by . Overall, the inclusion of 3-hydroxypropanal greatly enhances the agreement between the model and the observed spectra (see Figure [4](#f:LTEspectrumG0693)). Moreover, even with a non-negligible line blending, 3-hydroxypropanal appears to be the main carrier of most of the observed spectral features (e.g., the lines at $\sim$81.560 GHz and $\sim$ 39.066 GHz), further supporting its tentative detection. In Figures [9](#f:LTEall1) and [10](#f:LTEall2), we present the remaining brightest transitions of 3-hydroxypropanal covered by the survey, not shown in Figure 4, corresponding to a total of $\sim$45 additional lines. As can be seen in both figures, the majority of these lines are severely contaminated by emission from other molecules previously identified in this survey, yet they do not show clear discrepancies between the model and the observed data.

To derive the column density, we employed the AUTOFIT-SLIM tool (cite: Martin2019) and conducted a nonlinear least-squares LTE fit of the 3-hydroxypropanal emission to the observed spectra. We used the subset of transitions reported in Table [\[tab:transitions693\]](#tab:transitions693), taking into account the contribution to the emission from other species. We adopted the excitation temperature ($T_{\rm ex}$), radial velocity ($v_{\rm LSR}$) and line width (FWHM) values derived for $s$-propanal in (cite: sanz-novo2022a): $T_{\rm ex}$ = 12 K, $v_{\rm LSR}$ = 69 km s$^{-1}$ and FWHM = 21 km s$^{-1}$, leaving the column density as the only free parameter in the fit. We obtained a $N$ = (8.6$\pm$1.4)$\times$10$^{12}$ cm$^{-2}$, which translates into a molecular abundance with respect to H$_2$ of (6.4$\pm$1.4) $\times$10$^{-11}$, adopting a $N_{\rm H_2}$ = 1.35$\times$10$^{23}$ cm$^{-2}$ (cite: martin2008tracing) and assuming an uncertainty of 15% of its value. The derived value not only accurately constrains the abundance of 3-hydroxypropanal in the ISM but also implies that this species is a factor of 9$\pm$2 less abundant than $s$-propanal in G+0.693 ($N$ = (7.4$\pm$1.5$\times$10$^{13}$ cm$^{-2}$) and a factor of $\sim$60 less abundant than acetaldehyde (5.0$\pm$0.1$\times$10$^{14}$ cm$^{-2}$) (cite: sanz-novo2022a). Therefore, we observed a drop in abundance of nearly one order of magnitude as chemical complexity increased (i.e., with the addition of an OH group), which is in remarkable agreement with the results obtained for the related $n$-butanal toward the same molecular cloud ($s$-propanal/$ct$-$n$-butanal $>$ 9; (cite: sanz-novo2022a)). The column densities of 3-hydroxypropanal, acetaldehyde and propanal in each of the sources investigated in this work are displayed in Table [\[table:column_densities\]](#table:column_densities).

## Sgr B2(N) Star-Forming Region

Sagittarius (Sgr) B2(N) is a high-mass star forming protocluster located in the molecular cloud complex Sgr B2 in the central molecular zone of our Galaxy, at a distance of 8.2 kpc (cite: Reid19). Sgr B2(N) contains numerous hot molecular cores and H II regions (cite: Gaume95; Bonfand17; SanchezMonge17). It was the target of the imaging spectral line survey Reexploring Molecular Complexity with ALMA (ReMoCA) that was performed with the Atacama Large Millimeter/submillimeter Array (ALMA) between 84.1 and 114.4 GHz. Details about the data reduction and the method of analysis can be found in (cite: Belloche19; 2025A&A...698A.143B). The survey was analyzed by comparing the observed spectra to synthetic spectra computed assuming LTE with the software Weeds (cite: Maret11). For this work we focused on the position located at ($\alpha, \delta$)$_{\rm J2000}$= ($17^{\rm h}47^{\rm m}19{s}87, -28^\circ22'19{\ensuremath{''}}48$). This position, called Sgr B2(N1S), is about 1$\ensuremath{''}$ to the south of the main hot core Sgr B2(N1). It was chosen by (cite: Belloche19) as a compromise between reducing the dust optical depth and keeping a high enough H$_2$ column density to detect less abundant molecules.

![](hoch2ch2cho_ve0_n1s_1.png)

In order to search for 3-hydroxypropanal toward Sgr B2(N1S), we assumed the same LTE parameters as acetaldehyde ($T_{ex}$ = 250 K, $\Delta V$ = 5.0 km s$^{-1}$, see Table [\[t:coldens\]](#t:coldens) and Table [\[table:column_densities\]](#table:column_densities) for remaining parameters), keeping only the column density as a free parameter. As shown in Fig. [5](#f:remoca_hoch2ch2cho_ve0_n1s), 3-hydroxypropanal is not detected toward Sgr B2(N1S) and an upper limit column density of $7.9 \times 10^{16}$cm$^{-2}$ was determined. Table [\[t:coldens\]](#t:coldens) reports this upper limit as well as results obtained previously by (cite: sanz-novo2022a) and (cite: Koucky22) for acetaldehyde, lactaldehyde, 3-hydroxypropenal, propanal, and 2-hydroxyprop-2-enal. Table [\[t:coldens\]](#t:coldens) indicates that the upper limit derived for 3-hydroxypropanal is slightly more stringent than the upper limit obtained for its structural isomer lactaldehyde by (cite: Koucky22). We find that 3-hydroxypropanal is at least 8.5 times less abundant than acetaldehyde in Sgr B2(N1S).

## IRAS 16293-2422B Star-Forming Region

We utilized data from the ALMA Protostellar Interferometric Line Survey (PILS; (cite: jor16)) to search for 3-hydroxypropanal toward the “B” component of the Class 0 protostar IRAS 16293-2422 (IRAS 16293B). The PILS data consist of a full spectral survey of the source between 329.15 and 362.90 GHz at 0.5$''$ angular resolution using ALMA (for details see (cite: jor16)). We examined the spectra toward a position one beam offset from IRAS 16293B that has been the subject of several other studies as part of the PILS program: the position is characterized by bright but narrow emission lines (FWHM of approx 1 km s$^{-1}$) that makes it ideal to search for new species and provide meaningful upper limits with line blending significantly reduced. Adopting an excitation temperature of 125 K and calculating synthetic spectra for 3-hydroxypropanal, we do not see any indications of lines that can be attributed to the species down to the RMS noise level of the data (4–5 mJy km s$^{-1}$). The $3\sigma$ upper limit to the column density for 3-hydroxypropanal derived from these fits comes out to 1.5$\times 10^{14}$ cm$^{-2}$ for the assumed temperature. All assumed source parameters along with the determined upper limit are displayed in Table [\[table:column_densities\]](#table:column_densities). The vibrational partition function at 125K was considered when determining this upper limit.

## NGC 6334I Star-Forming Region

NGC 6334I is a high-mass star forming region that is host to a variety of complex organic molecules. Recently, several especially large oxygen-bearing species have been detected toward this source (cite: fried_methoxyethanol_2024; mcguire_methoxymethanol_2017), thus making it a strong target to search for 3-hydroxypropanal. The observational data toward this source was collected using ALMA, with a pointing position focused on the MM1 hot core of this source (J2000 $\alpha$ = 17$^h$20$^m$53.387$^s$ $\delta$ = -35$^{\circ}$46$^{\prime}$57.533$^{\prime\prime}$). These observations span across regions of ALMA Bands 4, 7, 9, and 10. To ensure uniformity, the data were smoothed using the standard CASA `imsmooth` routine to achieve a consistent angular resolution of $0.26'' \times 0.26''$ across all frequency bands. The observational details are described in the works of (cite: mcguire_band10_2018), (cite: mcguire_methoxymethanol_2017), and (cite: fried_methoxyethanol_2024).

![](ngc_ulims_plot_final.png)

The molecular emission was simulated using the `molsim` Python package (cite: molsim). This program assumes that the molecular signal is described by a single excitation temperature. The parameters employed for the simulation toward NGC 6334I were an excitation temperature of 225 K, a $v_{lsr}$ of -5.2 km s$^{-1}$, and a linewidth of 3.0 km s$^{-1}$ (cite: Ligterink2020). The vibrational partition function and conformational correction at 225 K was taken into account when determining the upper limit column density. To establish the upper limit, we identified the 3-hydroxypropanal line in the observations with the highest signal-to-noise ratio under the given simulation parameters that was not blended with the emission of other molecular species. We then calculated the column density necessary for this peak to reach an intensity at least three times the RMS noise level. Since the observations are line confusion limited, we visually determined the RMS noise around the line used to derive the upper limit to be 13 mJy/beam. Ultimately, the 3$\sigma$ column density upper limit was found to be $4.2 \times 10^{16}$ cm$^{-2}$. This upper limit along with the simulation parameters are noted in Table [\[table:column_densities\]](#table:column_densities). Figure [6](#fig:ngc_ulims) displays many of the strongest lines of 3-hydroxypropanal toward NGC 6334I simulated at the upper limit column density. It is clear that molecular emission of 3-hydroxypropanal is not detected at this abundance.

## TMC-1 Molecular Cloud

TMC-1 is a cold molecular cloud that has been extensively observed via several broadband line surveys. The detected molecules in this source are most commonly unsaturated carbon-chain species (i.e. (cite: burkhardt_detection_2018; gotham_obs; loomis_stacking_2021)) or cyclic molecules (cite: mcguire_benzonitrile_2018; mcguire_CNP_2021; cernicharo_indene_2021; sita_cyanoindene_2022; loru_ethynylbenzene_2023; cernicharo_ace_2024; wenzel_1pyrene_2024; wenzel_detections_2025; wenzel_coronene_2025). However, more recently, several large oxygen-bearing fairly saturated species, such as propanal and ethanol, have been observed (cite: agundez_detection_2023).

We searched for 3-hydroxypropanal in the fifth data reduction (DR5) of the GOTHAM (GBT Observations of TMC-1: Hunting Aromatic Molecules) observations. This line survey was observed using the Robert C. Byrd Green Bank Telescope (GBT). The GOTHAM project is described by (cite: gotham_obs), while the data reduction process for DR5 will be outlined in a forthcoming paper (Xue et al. in review). This survey has a frequency coverage spanning from 3.9 to 36.4 GHz (with some gaps). The data has an extremely high frequency resolution of 1.43 kHz and a noise level generally around 4-15 mK. The pointing position is focused on the cyanopolyyne peak of TMC-1 at (J2000) $\alpha$ = 04$^h$41$^m$42.5$^s$ $\delta$ = +25$^{\circ}$41$^{\prime}$26.8$^{\prime\prime}$. The molecular emission was again simulated using `molsim`, assuming an excitation temperature of 7 K, a $v_{lsr}$ of 5.8 km s$^{-1}$, and a linewidth of 0.3 km s$^{-1}$—parameters that are generally representative of the molecules detected in this source (e.g., (cite: burkhardt_detection_2018)). The upper limit was determined using the same method as Section [5.4](#subsec:ngc). In summary, the 3-hydroxypropanal transition with the strongest signal-to-noise ratio under the simulation parameters was determined. The column density required for this transition to have an intensity three times the RMS noise level around this line was then derived. The upper limit column density was found to be $8.6 \times 10^{11}$ cm$^{-2}$. Some of the most intense lines of 3-hydroxypropanal toward TMC-1 (simulated at the upper limit column density) are displayed in Figure [7](#fig:tmc_ulims).

![](tmc_ulim_grid.png)

This, unfortunately, is not an extremely stringent column density upper limit due to the weak transitions of the molecule within the frequency range of the GOTHAM observations. In fact, propanal (which is a less complex species than 3-hydroxypropanal) was observed in the QUIJOTE (Q-band Ultrasensitive Inspection Journey to the Obscure TMC-1 Environment) survey (cite: quijote) of TMC-1 with a column density of $(1.9 \pm 0.7) \times 10^{11}$ cm$^{-2}$ (cite: agundez_detection_2023). The frequency range of the QUIJOTE survey is 31.0-50.3 GHz. Under the assumed simulation parameters, the strongest simulated line in this range is around twice the intensity of the transition used to derive the upper limit. Moreover, the QUIJOTE survey has a noise level between 0.06 mK at 32 GHz and 0.18 mK at 49.5 GHz (cite: quijote_params), which is more than ten times lower than the GOTHAM survey. Thus, with additional investigation, this upper limit could likely be further refined toward TMC-1.

## Discussion of Chemical Implications

As mentioned previously, one of the main formation pathways of 3-hydroxypropanal that has been proposed in the literature under astrophysically relevant conditions is the radical recombination of and (Reaction [\[eq:radical_recomb\]](#eq:radical_recomb)). Although has not been detected in the interstellar medium, it has been shown experimentally to form from common interstellar precursors, such as hydrogenation of formaldehyde and hydrogen abstraction from methanol (cite: radical_gas; radical_ice; desorption4). Moreover, as discussed in (cite: wang23), could feasibly be formed via hydrogen abstraction of acetaldehyde (). However, such production of from acetaldehyde may be inefficient.

![](acetaldehyde_plot.png)

.

The C-H bond on the methyl group of acetaldehyde has a higher dissociation energy than the aldehyde hydrogen (cite: berkowitz_three_1994). Therefore, several gas phase experiments have shown that the radical is by-far the dominant hydrogen abstraction product of acetaldehyde when reacting with OH (cite: cameron_reaction_2002; butkovskaya_branching_2004). Moreover, an investigation of interstellar ice analogs found that the predominate initial reaction of acetaldehyde and hydrogen atoms is hydrogen abstraction to form and (cite: molpeceres_hydrogenation_2025). Additionally, during the aforementioned experiments of (cite: wang23), the radical was detected in FTIR data of the irradiated methanol-acetaldehyde ices, whereas was not directly observed above the detection limit.

Although it is clear that the production of is the primary product of the hydrogen abstraction of acetaldehyde, the enhanced cosmic ray ionization rate in G+0.693 may still result in a non-negligible formation of . Several previous chemical modeling studies toward G+0.693 have found that a notably enhanced cosmic-ray ionization rate (factor of more than 100 greater than the standard Galactic disk value) is required to reproduce the observed abundances of some molecular cations in this source (cite: Sanz-Novo2024a; Rivilla2022_PO+). This greater flux of cosmic rays would likely promote the production of radical species in the interstellar ices. These radicals could then recombine on the grain surface, where the surface acts to stabilize the association process and absorb the additional energy. The shocks produced by cloud-cloud collisions in G+0.693 would then cause the molecular inventory stored in interstellar ices to desorb into the gas phase, making them detectable with radio telescopes.

The column density ratio of acetaldehyde to 3-hydroxypropanal in each of the sources investigated is displayed in Figure [8](#fig:acetaldehyde). The lower limit ratio in TMC-1, Sgr B2(N), and NGC 6334I is below the tentatively derived value in G+0.693. Since these are lower limit ratios, it is challenging to draw any conclusions regarding the relative abundances in these three sources compared to G+0.693. For example, the true ratio for TMC-1, Sgr B2(N) and NGC 6334I could in theory be either above or below the tentatively determined value for G+0.693. However, this ratio is notably greater in IRAS 16293B than in G+0.693, thus indicating that there is a clear chemical differentiation in these two sources. One possible explanation is that differences in radiation environments, such as the elevated cosmic ray ionization rate in the Galactic Center, may lead to a higher rate of acetaldehyde dissociation in G+0.693, thereby enhancing the formation of . Furthermore, the elevated cosmic ray ionization rate could also result in a higher abundance of atomic hydrogen or carbon, potentially enhancing addition and abstraction reactions on dust grains and promoting the formation of the necessary precursor radical species (cite: requena-torres_galactic_2008; jimenez-serra_observations_2025). Alternatively, the destruction of 3-hydroxypropanal may be more efficient at the higher temperatures characteristic of the IRAS 16293B hot corino, or it may have been more extensively destroyed during ice processing in the warm-up phase of IRAS 16293B.

Another potential formation route of 3-hydroxypropanal could be the insertion of singlet-excited oxygen atoms (O(^1^D)) into the C-H bonds of the terminal group of propanal (). Singlet oxygen has been shown to form quite efficiently via the photolysis of molecules that are known to be abundant in interstellar ices. For example, experimental studies have shown that UV photolysis of can produce O(^1^D) at around a 10% yield (cite: slanger_photodissociative_1982; stief_flasch_1975). Moreover, O(^1^D) is formed at nearly 100% efficiency following the photolysis of at various UV wavelengths (cite: zhu_production_1990; slanger_co2_1971). Once produced, these excited oxygen atoms can efficiently insert into the bonds of hydrocarbon species (cite: hays13; bergner17; bergner19; daniely_photochemical_2025). For example, it was found in astrophysical ice analogs that the insertion of O(^1^D) into the C-H bonds of methane and ethane can form methanol and ethanol with negligible reaction barriers (cite: bergner17; bergner19). Thus, it may be possible for a similar reaction to occur with propanal on interstellar ices. To the best of our knowledge, among the sources examined in this study, column densities of propanal have been previously reported in the literature for G+0.693 (cite: sanz-novo2022a), IRAS 16293B (cite: lykke_alma-pils_2017), and TMC-1 (cite: agundez_detection_2023). Of note, some propanal transitions were observed in GBT observations of the Sgr B2(N-LMH) (cite: hollis_green_2004). However, since the observed lines are mainly in absorption, this indicates that the observations are likely probing the colder, extended gas around the source. On the other hand, only an upper limit column density of propanal has been determined in the ReMoCA observations of Sgr B2(N) analyzed in this paper (cite: sanz-novo2022a). Additionally, as mentioned previously, the derived column density of propanal from the QUIJOTE survey of TMC-1 is below the upper limit column density of 3-hydroxypropanal that we have derived in the GOTHAM observations; thus, no useful conclusions can be drawn from this result.

The column density of propanal was found to be $2.2 \times 10^{15}$ cm$^{-2}$ toward IRAS 16293B (cite: lykke_alma-pils_2017), which would suggest a propanal/3-hydroxypropanal ratio $\geq 14.7$ in this source. On the other hand, as noted in Section [5.1](#g693_description), this ratio has been tentatively determined to be around 9 in G+0.693. The high cosmic ray flux in G+0.693 could result in a strong field of secondary UV photons resulting from the interaction of these cosmic rays with molecular hydrogen (cite: prasad_uv_1983). This UV-field could therefore promote the production of singlet excited oxygen atoms in the ices in this source, thus resulting in 3-hydroxypropanal formation.

# Conclusions

In this work, we sought to detect 3-hydroxypropanal in the interstellar medium. This molecule shares chemical similarities with several previously detected interstellar species and has been predicted by multiple studies to be a promising detection target. To achieve this, we first synthesized the compound and then measured and analyzed the rotational spectrum of its most stable conformer within the 130–485 GHz range. In the process, we also fitted the rotational spectra of the two lowest lying vibrationally excited states. Due to the relatively small energy gap between these two excited states, some transition frequencies exhibited noticeable perturbations. Thus, we attempted to fit the energy difference between the states along with several Coriolis coupling parameters. Unfortunately, many of the perturbed lines were either extremely weak or below the noise level. Thus, only a small number of perturbed transitions could be incorporated into the fit, which resulted in several of the parameters only being determined with moderate precision. These parameter values could be much improved if better signal-to-noise ratio is achieved for these transitions in future work.

After analyzing and fitting the spectrum of the ground vibrational state, we searched for this molecule in the radio astronomical observations toward the IRAS 16293-2422B hot corino, the Sagittarius B2(N) and NGC 6334I hot cores, as well as the G+0.693-0.027 and TMC-1 molecular clouds. Molecular emission of 3-hydroxypropanal was tentatively detected for the first time toward G+0.693-0.027 and a column density of (8.6$\pm$1.4)$\times$10$^{12}$ cm$^{-2}$ was derived at an excitation temperature of 12 K. This value suggests that 3-hydroxypropanal is $9\pm2$ times less abundant than propanal in this source.

Unfortunately, no molecular emission of 3-hydroxypropanal was observed in any of the other sources that were investigated in this work. Column density upper limits were therefore determined. We then discussed some potential formation pathways of this molecule, including radical-recombination reactions and oxygen-insertion processes.

Although a fairly comprehensive number of interstellar sources were analyzed in this work, the measurement of the spectrum across a broadband frequency range and into the submillimeter wave regime now makes it possible to search for 3-hydroxypropanal in various other astronomical objects. One additional potentially strong candidate would be Orion KL, where other isomers have been detected (cite: methyl_acetate; peng_alma_2019). Additionally, The tentative detection of 3-hydroxypropanal reported here prompts the search for other isomers toward G+0.693.

**Acknowledgements**

We would like to sincerely thank the three anonymous referees, who each provided expert criticisms that substantially improved the quality of this manuscript. The authors gratefully acknowledge Dr. Isabelle Kleiner and Dr. Ha Vinh Lam Nguyen for providing additional spectroscopic catalogs for our analysis. This work has been funded by the Czech Science Foundation (GACR, grant No. 24-12586S). Prague authors gratefully acknowledge this financial support. Computational resources were provided by the e-INFRA CZ project (ID:90254), supported by the Ministry of Education, Youth and Sports of the Czech Republic. Z.T.P.F and B.A.M gratefully acknowledge the support of Schmidt Family Futures. B.A.M gratefully acknowledges the support of the Arnold and Mabel Beckman Foundation Beckman Young Investigator Award. B.A.M and C.X gratefully acknowledge support of National Science Foundation grant AST-2205126. V.M.R. acknowledges support through the grant RYC2020-029387-I funded by MICIU/AEI/10.13039/501100011033 and by "ESF, Investing in your future", and from the Consejo Superior de Investigaciones Científicas (CSIC) and the Centro de Astrobiología (CAB) through the project 20225AT015 (Proyectos intramurales especiales del CSIC); and from the grant CNS2023-144464 funded by MICIU/AEI/10.13039/501100011033 and by “European Union NextGenerationEU/PRTR". M.S.N. acknowledges a Juan de la Cierva Postdoctoral Fellowship, project JDC2022-048934-I, funded by MCIN/AEI/10.13039/501100011033 and by the European Union “NextGenerationEU/PRTR". I.J.-S., V.M.R. and M.S.-N. acknowledge support from the grant PID2022-136814NB-I00 by the Spanish Ministry of Science, Innovation and Universities/State Agency of Research MICIU/AEI/10.13039/501100011033 and by ERDF, UE. I.J.-S. also acknowledges funding from the European Research Council (ERC) under European Union’s Horizon Europe research and innovation programme OPENS (GA 101125858). The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. J.-C.G. thanks the Centre National d’Etudes Spatiales (CNES) for a grant. L.M., R.M. and J.-C.G. were supported by the Programme National “Physique et Chimie du Milieu Interstellaire" (PCMI) of CNRS/INSU with INC/INP co-funded by CEA and CNES

**Statement of Efforts.** All authors contributed to the writing and editing of the manuscript.

natexlab

(ref: quijote_params) Agúndez, M., Molpeceres, G., Cabezas, C., et al. 2025, Astronomy & Astrophysics, 693, L20, doi: [`10.1051/0004-6361/202453459`](http://doi.org/10.1051/0004-6361/202453459)

(ref: agundez_chemistry_2023) Agúndez, M., Roncero, O., Marcelino, N., et al. 2023a, Astronomy & Astrophysics, 673, A24, doi: [`10.1051/0004-6361/202346279`](http://doi.org/10.1051/0004-6361/202346279)

(ref: agundez_detection_2023) Agúndez, M., Loison, J.-C., Hickson, K. M., et al. 2023b, Astronomy & Astrophysics, 673, A34, doi: [`10.1051/0004-6361/202346076`](http://doi.org/10.1051/0004-6361/202346076)

(ref: lactaldehyde) Alonso, E. R., McGuire, B. A., Kolesniková, L., et al. 2019, The Astrophysical Journal, 883, 18, doi: [`10.3847/1538-4357/ab3463`](http://doi.org/10.3847/1538-4357/ab3463)

(ref: bally1987b) Bally, J., Stark, A. A., Wilson, R. W., & Henkel, C. 1987, ApJS, 65, 13, doi: [`10.1086/191217`](http://doi.org/10.1086/191217)

(ref: battersby2024) Battersby, C., Walker, D. L., Barnes, A., et al. 2025, The Astrophysical Journal, 984, 156, doi: [`10.3847/1538-4357/adb5f0`](http://doi.org/10.3847/1538-4357/adb5f0)

(ref: Belloche19) Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10, doi: [`10.1051/0004-6361/201935428`](http://doi.org/10.1051/0004-6361/201935428)

(ref: 2025A&A...698A.143B) —. 2025, A&A, 698, A143, doi: [`10.1051/0004-6361/202554411`](http://doi.org/10.1051/0004-6361/202554411)

(ref: ethyl_formate) Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2009, Astronomy & Astrophysics, 499, 215, doi: [`10.1051/0004-6361/200811550`](http://doi.org/10.1051/0004-6361/200811550)

(ref: Belloche16) Belloche, A., Müller, H. S. P., & Garrod, R. T. a nd Menten, K. M. 2016, A&A, 587, A91, doi: [`10.1051/0004-6361/201527268`](http://doi.org/10.1051/0004-6361/201527268)

(ref: bergner17) Bergner, J. B., Öberg, K. I., & Rajappan, M. 2017, The Astrophysical Journal, 845, 29, doi: [`10.3847/1538-4357/aa7d09`](http://doi.org/10.3847/1538-4357/aa7d09)

(ref: bergner19) —. 2019, The Astrophysical Journal, 874, 115, doi: [`10.3847/1538-4357/ab07b2`](http://doi.org/10.3847/1538-4357/ab07b2)

(ref: berkowitz_three_1994) Berkowitz, J., Ellison, G. B., & Gutman, D. 1994, The Journal of Physical Chemistry, 98, 2744, doi: [`10.1021/j100062a009`](http://doi.org/10.1021/j100062a009)

(ref: Bonfand17) Bonfand, M., Belloche, A., Menten, K. M., Garrod, R. T., & Müller, H. S. P. 2017, A&A, 604, A60, doi: [`10.1051/0004-6361/201730648`](http://doi.org/10.1051/0004-6361/201730648)

(ref: Brunken2010) Brünken, S., Belloche, A., Martı́n, S., Verheyen, L., & Menten, K. M. 2010, A&A, 516, A109, doi: [`10.1051/0004-6361/200912456`](http://doi.org/10.1051/0004-6361/200912456)

(ref: burkhardt_detection_2018) Burkhardt, A. M., Herbst, E., Kalenskii, S. V., et al. 2018, Monthly Notices of the Royal Astronomical Society, 474, 5068, doi: [`10.1093/mnras/stx2972`](http://doi.org/10.1093/mnras/stx2972)

(ref: butkovskaya_branching_2004) Butkovskaya, N. I., Kukui, A., & Le Bras, G. 2004, The Journal of Physical Chemistry A, 108, 1160, doi: [`10.1021/jp036740m`](http://doi.org/10.1021/jp036740m)

(ref: cameron_reaction_2002) Cameron, M., Sivakumaran, V., Dillon, T. J., & Crowley, J. N. 2002, Physical Chemistry Chemical Physics, 4, 3628, doi: [`10.1039/B202586H`](http://doi.org/10.1039/B202586H)

(ref: cernicharo_indene_2021) Cernicharo, J., Agúndez, M., Cabezas, C., et al. 2021a, Astronomy & Astrophysics, 649, L15, doi: [`10.1051/0004-6361/202141156`](http://doi.org/10.1051/0004-6361/202141156)

(ref: quijote) Cernicharo, J., Agúndez, M., Kaiser, R. I., et al. 2021b, Astronomy & Astrophysics, 652, L9, doi: [`10.1051/0004-6361/202141660`](http://doi.org/10.1051/0004-6361/202141660)

(ref: cernicharo_discovery_2020) Cernicharo, J., Marcelino, N., Agúndez, M., et al. 2020, Astronomy & Astrophysics, 642, L17, doi: [`10.1051/0004-6361/202039351`](http://doi.org/10.1051/0004-6361/202039351)

(ref: cernicharo_ace_2024) Cernicharo, J., Cabezas, C., Fuentetaja, R., et al. 2024, Astronomy & Astrophysics, 690, L13, doi: [`10.1051/0004-6361/202452196`](http://doi.org/10.1051/0004-6361/202452196)

(ref: colzi2022) Colzi, L., Martín-Pintado, J., Rivilla, V. M., et al. 2022, ApJL, 926, L22, doi: [`10.3847/2041-8213/ac52ac`](http://doi.org/10.3847/2041-8213/ac52ac)

(ref: colzi2024) Colzi, L., Martı́n-Pintado, J., Zeng, S., et al. 2024, A&A, 690, A121, doi: [`10.1051/0004-6361/202451382`](http://doi.org/10.1051/0004-6361/202451382)

(ref: hydroxypropenal) Coutens, A., Loison, J.-C., Boulanger, A., et al. 2022, Astronomy & Astrophysics, 660, L6, doi: [`10.1051/0004-6361/202243038`](http://doi.org/10.1051/0004-6361/202243038)

(ref: daniely_photochemical_2025) Daniely, A., Zamir, A., Eisenberg, H. R., et al. 2025, The Journal of Chemical Physics, 162, 014303, doi: [`10.1063/5.0214165`](http://doi.org/10.1063/5.0214165)

(ref: fried) Fried, Z. T. P., Lee, K. L. K., Byrne, A. N., & McGuire, B. A. 2023, Digital Discovery, 2, 952, doi: [`10.1039/D3DD00020F`](http://doi.org/10.1039/D3DD00020F)

(ref: fried_methoxyethanol_2024) Fried, Z. T. P., El-Abd, S. J., Hays, B. M., et al. 2024, The Astrophysical Journal Letters, 965, L23, doi: [`10.3847/2041-8213/ad37ff`](http://doi.org/10.3847/2041-8213/ad37ff)

(ref: g16) Frisch, M. J., Trucks, G. W., Schlegel, H. B., et al. 2016, Gaussian˜16 Revision C.01

(ref: Gaume95) Gaume, R. A., Claussen, M. J., de Pree, C. G., Goss, W. M., & Mehringer, D. M. 1995, ApJ, 449, 663, doi: [`10.1086/176087`](http://doi.org/10.1086/176087)

(ref: ginsburg2016) Ginsburg, A., Henkel, C., Ao, Y., et al. 2016, A&A, 586, A50, doi: [`10.1051/0004-6361/201526100`](http://doi.org/10.1051/0004-6361/201526100)

(ref: gordy_cooke) Gordy, W., & Cook, R. 1970, Microwave Molecular Spectra, Chemical applications of spectroscopy (Interscience Pub.). <https://books.google.com/books?id=_BF2xwEACAAJ>

(ref: guesten1983) Guesten, R., & Henkel, C. 1983, A&A, 125, 136

(ref: guesten1985) Guesten, R., Walmsley, C. M., Ungerechts, H., & Churchwell, E. 1985, A&A, 142, 381

(ref: hays13) Hays, B. M., & Widicus Weaver, S. L. 2013, The Journal of Physical Chemistry A, 117, 7142, doi: [`10.1021/jp400753r`](http://doi.org/10.1021/jp400753r)

(ref: desorption4) He, J., Simons, M., Fedoseev, G., et al. 2022, Astronomy & Astrophysics, 659, A65, doi: [`10.1051/0004-6361/202142414`](http://doi.org/10.1051/0004-6361/202142414)

(ref: hollis_green_2004) Hollis, J. M., Jewell, P. R., Lovas, F. J., Remijan, A., & Møllendal, H. 2004, The Astrophysical Journal, 610, L21, doi: [`10.1086/423200`](http://doi.org/10.1086/423200)

(ref: huettemeister1993) Huettemeister, S., Wilson, T. L., Bania, T. M., & Martin-Pintado, J. 1993, A&A, 280, 255

(ref: ilyushin_submillimeter_2021) Ilyushin, V. V., Margulès, L., Tercero, B., et al. 2021, Journal of Molecular Spectroscopy, 379, 111454, doi: [`10.1016/j.jms.2021.111454`](http://doi.org/10.1016/j.jms.2021.111454)

(ref: radical_ice) Ishibashi, A., Hidaka, H., Sameera, W. M. C., Oba, Y., & Watanabe, N. 2023, The Astrophysical Journal, 960, 90, doi: [`10.3847/1538-4357/acfb82`](http://doi.org/10.3847/1538-4357/acfb82)

(ref: jimenez-serra_observations_2025) Jimenez-Serra, I., Codella, C., & Belloche, A. 2025, Observations of complex organic molecules in the gas phase of the interstellar medium, arXiv, doi: [`10.48550/arXiv.2503.17104`](http://doi.org/10.48550/arXiv.2503.17104)

(ref: Jimenez-Serra2020) Jiménez-Serra, I., Martín-Pintado, J., Rivilla, V. M., et al. 2020, Astrobiology, 20, 1048, doi: [`10.1089/ast.2019.2125`](http://doi.org/10.1089/ast.2019.2125)

(ref: Jimenez-Serra2022) Jiménez-Serra, I., Rodríguez-Almeida, L. F., Martín-Pintado, J., et al. 2022, A&A, 663, A181, doi: [`10.1051/0004-6361/202142699`](http://doi.org/10.1051/0004-6361/202142699)

(ref: Jones2012) Jones, P. A., Burton, M. G., Cunningham, M. R., et al. 2012, MNRAS, 419, 2961, doi: [`10.1111/j.1365-2966.2011.19941.x`](http://doi.org/10.1111/j.1365-2966.2011.19941.x)

(ref: jor16) Jørgensen, J. K., Wiel, M. H. D. v. d., Coutens, A., et al. 2016, Astronomy & Astrophysics, 595, A117, doi: [`10.1051/0004-6361/201628648`](http://doi.org/10.1051/0004-6361/201628648)

(ref: jorgensen_alma-pils_2018) Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, Astronomy & Astrophysics, 620, A170, doi: [`10.1051/0004-6361/201731667`](http://doi.org/10.1051/0004-6361/201731667)

(ref: Kania2006) Kania, P., Střı́teská, L., Šimečková, M., & Urban, Š. 2006, Journal of Molecular Structure, 795, 209, doi: [`10.1016/j.molstruc.2006.02.025`](http://doi.org/10.1016/j.molstruc.2006.02.025)

(ref: kisiel_assignment_2001) Kisiel, Z. 2001, in Spectroscopy from Space, ed. J. Demaison, K. Sarka, & E. A. Cohen (Dordrecht: Springer Netherlands), 91–106, doi: [`10.1007/978-94-010-0832-7_6`](http://doi.org/10.1007/978-94-010-0832-7_6)

(ref: asfit) Kisiel, Z., & Białkowska-Jaworska, E. 2019, Journal of Molecular Spectroscopy, 359, 16, doi: [`10.1016/j.jms.2019.03.005`](http://doi.org/10.1016/j.jms.2019.03.005)

(ref: Masato2001) Kitamura, M., Nakano, K., Miki, T., Okada, M., & Noyori, R. 2001, J. Am. Chem. Soc., 123, 8939, doi: [`10.1021/ja0110978`](http://doi.org/10.1021/ja0110978)

(ref: kleimeier_interstellar_2021) Kleimeier, N. F., & Kaiser, R. I. 2021, ChemPhysChem, 22, 1229, doi: [`10.1002/cphc.202100111`](http://doi.org/10.1002/cphc.202100111)

(ref: methoxyacetaldehyde) Kolesniková, L., Peña, I., Alonso, E. R., et al. 2018, Astronomy & Astrophysics, 619, A67, doi: [`10.1051/0004-6361/201833773`](http://doi.org/10.1051/0004-6361/201833773)

(ref: Koucky22) Koucký, J., Kolesniková, L., Luková, K., et al. 2022, A&A, 666, A158, doi: [`10.1051/0004-6361/202244376`](http://doi.org/10.1051/0004-6361/202244376)

(ref: krieger2017) Krieger, N., Ott, J., Beuther, H., et al. 2017, ApJ, 850, 77, doi: [`10.3847/1538-4357/aa951c`](http://doi.org/10.3847/1538-4357/aa951c)

(ref: Li2020) Li, J., Wang, J., Qiao, H., et al. 2020, MNRAS, 492, 556, doi: [`10.1093/mnras/stz3337`](http://doi.org/10.1093/mnras/stz3337)

(ref: Ligterink2020) Ligterink, N. F. W., El-Abd, S. J., Brogan, C. L., et al. 2020, ApJ, 901, 37, doi: [`10.3847/1538-4357/abad38`](http://doi.org/10.3847/1538-4357/abad38)

(ref: loomis_investigating_2015) Loomis, R. A., McGuire, B. A., Shingledecker, C., et al. 2015, The Astrophysical Journal, 799, 34, doi: [`10.1088/0004-637X/799/1/34`](http://doi.org/10.1088/0004-637X/799/1/34)

(ref: loomis_stacking_2021) Loomis, R. A., Burkhardt, A. M., Shingledecker, C. N., et al. 2021, Nature Astronomy, 5, 188, doi: [`10.1038/s41550-020-01261-4`](http://doi.org/10.1038/s41550-020-01261-4)

(ref: loru_ethynylbenzene_2023) Loru, D., Cabezas, C., Cernicharo, J., Schnell, M., & Steber, A. L. 2023, Astronomy & Astrophysics, 677, A166, doi: [`10.1051/0004-6361/202347023`](http://doi.org/10.1051/0004-6361/202347023)

(ref: lykke_alma-pils_2017) Lykke, J. M., Coutens, A., Jørgensen, J. K., et al. 2017, Astronomy & Astrophysics, 597, A53, doi: [`10.1051/0004-6361/201629180`](http://doi.org/10.1051/0004-6361/201629180)

(ref: Maret11) Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, A&A, 526, A47, doi: [`10.1051/0004-6361/201015487`](http://doi.org/10.1051/0004-6361/201015487)

(ref: Martin2019) Martín, S., Martín-Pintado, J., Blanco-Sánchez, C., et al. 2019, A&A, 631, A159, doi: [`10.1051/0004-6361/201936144`](http://doi.org/10.1051/0004-6361/201936144)

(ref: martin2008tracing) Martı́n, S., Requena-Torres, M. A., Martı́n-Pintado, J., & Mauersberger, R. 2008, ApJ, 678, 245, doi: [`10.1086/533409`](http://doi.org/10.1086/533409)

(ref: cfour) Matthews, D. A., Cheng, L., Harding, M. E., et al. 2020, J. Chem. Phys, 152, 214108, doi: [`10.1063/5.0004837`](http://doi.org/10.1063/5.0004837)

(ref: mcguire_benzonitrile_2018) McGuire, B. A., Burkhardt, A. M., Kalenskii, S., et al. 2018a, Science, 359, 202, doi: [`10.1126/science.aao4890`](http://doi.org/10.1126/science.aao4890)

(ref: molsim) McGuire, B. A., Xue, C., Lee, K. L. K., El-Abd, S., & Loomis, R. A. 2024, molsim, v0.5.0, Zenodo, doi: [`10.5281/zenodo.12697227`](http://doi.org/10.5281/zenodo.12697227)

(ref: mcguire_methoxymethanol_2017) McGuire, B. A., Shingledecker, C. N., Willis, E. R., et al. 2017, The Astrophysical Journal Letters, 851, L46, doi: [`10.3847/2041-8213/aaa0c3`](http://doi.org/10.3847/2041-8213/aaa0c3)

(ref: mcguire_band10_2018) McGuire, B. A., Brogan, C. L., Hunter, T. R., et al. 2018b, The Astrophysical Journal Letters, 863, L35, doi: [`10.3847/2041-8213/aad7bb`](http://doi.org/10.3847/2041-8213/aad7bb)

(ref: gotham_obs) McGuire, B. A., Burkhardt, A. M., Loomis, R. A., et al. 2020, The Astrophysical Journal Letters, 900, L10, doi: [`10.3847/2041-8213/aba632`](http://doi.org/10.3847/2041-8213/aba632)

(ref: mcguire_CNP_2021) McGuire, B. A., Loomis, R. A., Burkhardt, A. M., et al. 2021, Science, 371, 1265, doi: [`10.1126/science.abb7535`](http://doi.org/10.1126/science.abb7535)

(ref: mininni_guapos_2020) Mininni, C., Beltrán, M. T., Rivilla, V. M., et al. 2020, Astronomy & Astrophysics, 644, A84, doi: [`10.1051/0004-6361/202038966`](http://doi.org/10.1051/0004-6361/202038966)

(ref: mohamadi_macromodelintegrated_1990) Mohamadi, F., Richards, N. G. J., Guida, W. C., et al. 1990, Journal of Computational Chemistry, 11, 440, doi: [`10.1002/jcc.540110405`](http://doi.org/10.1002/jcc.540110405)

(ref: molpeceres_hydrogenation_2025) Molpeceres, G., Nguyen, T., Oba, Y., & Watanabe, N. 2025, Astronomy & Astrophysics, 694, A299, doi: [`10.1051/0004-6361/202451990`](http://doi.org/10.1051/0004-6361/202451990)

(ref: fast_scan) Motiyenko, R. A., Armieieva, I. A., Margulès, L., Alekseev, E. A., & Guillemin, J.-C. 2019, Astronomy & Astrophysics, 623, A162, doi: [`10.1051/0004-6361/201834587`](http://doi.org/10.1051/0004-6361/201834587)

(ref: motiyenko_internal_2018) Motiyenko, R. A., Margulès, L., Senent, M. L., & Guillemin, J.-C. 2018, J. Phys. Chem. A, 122, 3163, doi: [`10.1021/acs.jpca.7b12051`](http://doi.org/10.1021/acs.jpca.7b12051)

(ref: muller_rotation-tunneling_2024) Müller, H. S. P., Coutens, A., Jørgensen, J. K., et al. 2024, Astronomy & Astrophysics, 687, A8, doi: [`10.1051/0004-6361/202450029`](http://doi.org/10.1051/0004-6361/202450029)

(ref: radical_gas) Ocaña, A. J., Blázquez, S., Potapov, A., et al. 2019, Physical Chemistry Chemical Physics, 21, 6942, doi: [`10.1039/c9cp00439d`](http://doi.org/10.1039/c9cp00439d)

(ref: peng_alma_2019) Peng, Y., Rivilla, V. M., Zhang, L., Ge, J. X., & Zhou, B. 2019, The Astrophysical Journal, 871, 251, doi: [`10.3847/1538-4357/aafad4`](http://doi.org/10.3847/1538-4357/aafad4)

(ref: spcat) Pickett, H. M. 1991, Journal of Molecular Spectroscopy, 148, 371, doi: [`10.1016/0022-2852(91)90393-O`](http://doi.org/10.1016/0022-2852(91)90393-O)

(ref: prasad_uv_1983) Prasad, S. S., & Tarafdar, S. P. 1983, The Astrophysical Journal, 267, 603, doi: [`10.1086/160896`](http://doi.org/10.1086/160896)

(ref: Reid19) Reid, M. J., Menten, K. M., Brunthaler, A., et al. 2019, ApJ, 885, 131, doi: [`10.3847/1538-4357/ab4a11`](http://doi.org/10.3847/1538-4357/ab4a11)

(ref: Requena-Torres2008) Requena-Torres, M. A., Martı́n-Pintado, J., Martı́n, S., & Morris, M. R. 2008, ApJ, 672, 352, doi: [`10.1086/523627`](http://doi.org/10.1086/523627)

(ref: requena-torres2006) Requena-Torres, M. A., Martı́n-Pintado, J., Rodrı́guez-Franco, A., et al. 2006, A&A, 455, 971, doi: [`10.1051/0004-6361:20065190`](http://doi.org/10.1051/0004-6361:20065190)

(ref: requena-torres_galactic_2008) Requena-Torres, M. A., Martín-Pintado, J., Martín, S., & Morris, M. R. 2008, The Astrophysical Journal, 672, 352, doi: [`10.1086/523627`](http://doi.org/10.1086/523627)

(ref: rivilla_ethylformate_2017) Rivilla, V. M., Beltrán, M. T., Martín-Pintado, J., et al. 2017, Astronomy & Astrophysics, 599, A26, doi: [`10.1051/0004-6361/201628823`](http://doi.org/10.1051/0004-6361/201628823)

(ref: Rivilla2020b) Rivilla, V. M., Martı́n-Pintado, J., Jiménez-Serra, I., et al. 2020, ApJL, 899, L28, doi: [`10.3847/2041-8213/abac55`](http://doi.org/10.3847/2041-8213/abac55)

(ref: Rivilla2021a) Rivilla, V. M., Jiménez-Serra, I., Martín-Pintado, J., et al. 2021, Proceedings of the National Academy of Science, 118, e2101314118, doi: [`10.1073/pnas.2101314118`](http://doi.org/10.1073/pnas.2101314118)

(ref: Rivilla2022_nitriles) Rivilla, V. M., Jiménez-Serra, I., Martı́n-Pintado, J., et al. 2022a, Frontiers in Astronomy and Space Sciences, 9, 876870, doi: [`10.3389/fspas.2022.876870`](http://doi.org/10.3389/fspas.2022.876870)

(ref: Rivilla2022_PO+) Rivilla, V. M., García De La Concepción, J., Jiménez-Serra, I., et al. 2022b, Frontiers in Astronomy and Space Sciences, 9, 829288, doi: [`10.3389/fspas.2022.829288`](http://doi.org/10.3389/fspas.2022.829288)

(ref: Rivilla2022a) Rivilla, V. M., Colzi, L., Jiménez-Serra, I., et al. 2022c, ApJL, 929, L11, doi: [`10.3847/2041-8213/ac6186`](http://doi.org/10.3847/2041-8213/ac6186)

(ref: rivilla_first_2023) Rivilla, V. M., Sanz-Novo, M., Jiménez-Serra, I., et al. 2023, The Astrophysical Journal Letters, 953, L20, doi: [`10.3847/2041-8213/ace977`](http://doi.org/10.3847/2041-8213/ace977)

(ref: Rodriguez-Almeida2021a) Rodríguez-Almeida, L. F., Jiménez-Serra, I., Rivilla, V. M., et al. 2021, ApJL, 912, L11, doi: [`10.3847/2041-8213/abf7cb`](http://doi.org/10.3847/2041-8213/abf7cb)

(ref: rodriguez-fernandez2000) Rodrı́guez-Fernández, N. J., Martı́n-Pintado, J., de Vicente, P., et al. 2000, Astronomy and Astrophysics, 356, 695

(ref: rodriguez-fernandez2001) Rodrı́guez-Fernández, N. J., Martı́n-Pintado, J., Fuente, A., et al. 2001, A&A, 365, 174, doi: [`10.1051/0004-6361:20000020`](http://doi.org/10.1051/0004-6361:20000020)

(ref: rodriguez-fernandez2004) Rodrı́guez-Fernández, N. J., Martı́n-Pintado, J., Fuente, A., & Wilson, T. L. 2004, A&A, 427, 217, doi: [`10.1051/0004-6361:20041370`](http://doi.org/10.1051/0004-6361:20041370)

(ref: roldan) Roldán, R., Hernandez, K., Joglar, J., et al. 2018, ACS Catalysis, 8, 8804, doi: [`10.1021/acscatal.8b02486`](http://doi.org/10.1021/acscatal.8b02486)

(ref: san_andres_first_2024) San Andrés, D., Rivilla, V. M., Colzi, L., et al. 2024, The Astrophysical Journal, 967, 39, doi: [`10.3847/1538-4357/ad3af3`](http://doi.org/10.3847/1538-4357/ad3af3)

(ref: SanchezMonge17) Sánchez-Monge, Á., Schilke, P., Schmiedeke, A., et al. 2017, A&A, 604, A6, doi: [`10.1051/0004-6361/201730426`](http://doi.org/10.1051/0004-6361/201730426)

(ref: Santa-Maria2021) Santa-Maria, M. G., Goicoechea, J. R., Etxaluze, M., Cernicharo, J., & Cuadrado, S. 2021, A&A, 649, A32, doi: [`10.1051/0004-6361/202040221`](http://doi.org/10.1051/0004-6361/202040221)

(ref: sanz-novo2022a) Sanz-Novo, M., Belloche, A., Rivilla, V. M., et al. 2022, A&A, 666, A114, doi: [`10.1051/0004-6361/202142848`](http://doi.org/10.1051/0004-6361/202142848)

(ref: Sanz-Novo2023) Sanz-Novo, M., Rivilla, V. M., Jiménez-Serra, I., et al. 2023, ApJ, 954, 3, doi: [`10.3847/1538-4357/ace523`](http://doi.org/10.3847/1538-4357/ace523)

(ref: Sanz-Novo2024a) —. 2024, ApJ, 965, 149, doi: [`10.3847/1538-4357/ad2c01`](http://doi.org/10.3847/1538-4357/ad2c01)

(ref: shingledecker_case_2019) Shingledecker, C. N., Álvarez Barcia, S., Korn, V. H., & Kästner, J. 2019, The Astrophysical Journal, 878, 80, doi: [`10.3847/1538-4357/ab1d4a`](http://doi.org/10.3847/1538-4357/ab1d4a)

(ref: sita_cyanoindene_2022) Sita, M. L., Changala, P. B., Xue, C., et al. 2022, The Astrophysical Journal Letters, 938, L12, doi: [`10.3847/2041-8213/ac92f4`](http://doi.org/10.3847/2041-8213/ac92f4)

(ref: slanger_co2_1971) Slanger, T. G., & Black, G. 1971, The Journal of Chemical Physics, 54, 1889, doi: [`10.1063/1.1675114`](http://doi.org/10.1063/1.1675114)

(ref: slanger_photodissociative_1982) —. 1982, The Journal of Chemical Physics, 77, 2432, doi: [`10.1063/1.444111`](http://doi.org/10.1063/1.444111)

(ref: stief_flasch_1975) Stief, L. J., Payne, W. A., & Klemm, R. B. 1975, The Journal of Chemical Physics, 62, 4000, doi: [`10.1063/1.430323`](http://doi.org/10.1063/1.430323)

(ref: methyl_acetate) Tercero, B., Kleiner, I., Cernicharo, J., et al. 2013, The Astrophysical Journal Letters, 770, L13, doi: [`10.1088/2041-8205/770/1/L13`](http://doi.org/10.1088/2041-8205/770/1/L13)

(ref: Tercero2021) Tercero, F., López-Pérez, J. A., Gallego, J. D., et al. 2021, A&A, 645, A37, doi: [`10.1051/0004-6361/202038701`](http://doi.org/10.1051/0004-6361/202038701)

(ref: Uhlikova_fso3_2011) Uhlı́ková, T., & Urban, v. 2011, Structural Chemistry, 22, 551, doi: [`10.1007/s11224-010-9727-2`](http://doi.org/10.1007/s11224-010-9727-2)

(ref: wang23) Wang, J., Marks, J. H., Turner, A. M., et al. 2023, Physical Chemistry Chemical Physics, 25, 936, doi: [`10.1039/D2CP03543J`](http://doi.org/10.1039/D2CP03543J)

(ref: wang_interstellar_2024) Wang, J., Zhang, C., Marks, J. H., et al. 2024, Nature Communications, 15, 10189, doi: [`10.1038/s41467-024-54562-x`](http://doi.org/10.1038/s41467-024-54562-x)

(ref: wenzel_1pyrene_2024) Wenzel, G., Cooke, I. R., Changala, P. B., et al. 2024, Science, 386 (6723), 810, doi: [`10.1126/science.adq6391`](http://doi.org/10.1126/science.adq6391)

(ref: wenzel_detections_2025) Wenzel, G., Speak, T. H., Changala, P. B., et al. 2025a, Nature Astronomy, 9, 262, doi: [`10.1038/s41550-024-02410-9`](http://doi.org/10.1038/s41550-024-02410-9)

(ref: wenzel_coronene_2025) Wenzel, G., Gong, S., Xue, C., et al. 2025b, The Astrophysical Journal Letters, 984, L36, doi: [`10.3847/2041-8213/adc911`](http://doi.org/10.3847/2041-8213/adc911)

(ref: lille) Zakharenko, O., Motiyenko, R. A., Margulès, L., & Huet, T. R. 2015, Journal of Molecular Spectroscopy, 317, 41, doi: [`10.1016/j.jms.2015.09.005`](http://doi.org/10.1016/j.jms.2015.09.005)

(ref: Zeng2018) Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, MNRAS, 478, 2962, doi: [`10.1093/mnras/sty1174`](http://doi.org/10.1093/mnras/sty1174)

(ref: zeng2020) Zeng, S., Zhang, Q., Jiménez-Serra, I., et al. 2020, MNRAS, 497, 4896, doi: [`10.1093/mnras/staa2187`](http://doi.org/10.1093/mnras/staa2187)

(ref: hydroxyacetone) Zhou, Y., Quan, D.-H., Zhang, X., & Qin, S.-L. 2020, Research in Astronomy and Astrophysics, 20, 125, doi: [`10.1088/1674-4527/20/8/125`](http://doi.org/10.1088/1674-4527/20/8/125)

(ref: zhu_production_1990) Zhu, Y., & Gordon, R. J. 1990, The Journal of Chemical Physics, 92, 2897, doi: [`10.1063/1.457937`](http://doi.org/10.1063/1.457937)

(ref: zou2020) Zou, L., Motiyenko, R. A., Margulès, L., & Alekseev, E. A. 2020, Review of Scientific Instruments, 91 ( 063104). [doi.org/10.1063/5.0004461](doi.org/10.1063/5.0004461)

# Complementary Figures

In Figures [9](#f:LTEall1) and [10](#f:LTEall2) we report the remaining brightest transitions of 3-hydroxypropanal that are also covered by the survey conducted toward the molecular cloud G+0.693-0.027 but are not shown in Figure [4](#f:LTEspectrumG0693), spanning lines down to an intensity comparable to the weakest transition shown in Figure [4](#f:LTEspectrumG0693). The vast majority of these lines appear heavily blended with the emission from other brighter species previously identified in this survey or fall within a region with lower sensitivity.

![](Fig_A1.png)

![](Fig_A2.png)

# Complementary Tables

Table [\[t:coldens\]](#t:coldens) summarizes key details of the search for 3-hydroxypropanal in Sgr B2(N1S), including the source parameters such as temperature, source size, and line width, as well as the column densities determined for chemically related molecules.

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:--:|---:|:--:|:--:|---:|:--:|:--:|:--:|:--:|---:|
| Molecule | Status | $N_{\rm det}$ | Size | $T_{\mathrm{rot}}$ | $N$ | $F_{\rm vib}$ | $F_{\rm conf}$ | $\Delta V$ | $V_{\mathrm{off}}$ | $\frac{N_{\rm ref}}{N}$ |
|  |  |  | ($''$) | \(K\) | (cm$^{-2}$) |  |  | (km s$^{-1}$) | (km s$^{-1}$) |  |
| CH$_3$CHO $^\star$ | d | 31 | 2.0 | 250 | 6.7 (17) | 1.09 | 1.00 | 5.0 | 0.0 | 1 |
| C$_2$H$_5$CHO | n | 0 | 2.0 | 250 | $<$ 1.6 (17) | 4.46 | 1.18 | 5.0 | 0.0 | $>$ 4.3 |
| HOCH$_2$CH$_2$CHO, $v=0$ | n | 0 | 2.0 | 250 | $<$ 7.9 (16) | 5.39 | 1.05 | 5.0 | 0.0 | $>$ 8.5 |
| CH$_3$CH(OH)CHO, $v=0$ | n | 0 | 2.0 | 250 | $<$ 1.7 (17) | 5.68 | 1.01 | 5.0 | 0.0 | $>$ 3.9 |
| HOCHCHCHO, $v=0$ | n | 0 | 2.0 | 250 | $<$ 7.0 (16) | 2.00 | 1.00 | 5.0 | 0.0 | $>$ 9.6 |
| CH$_2$C(OH)CHO, $v=0$ | n | 0 | 2.0 | 250 | $<$ 7.2 (16) | 2.41 | 1.00 | 5.0 | 0.0 | $>$ 9.3 |

d: detection, n: nondetection.

Number of detected lines (cite: Belloche16). One line of a given species may mean a group of transitions of that species that are blended together.

Source diameter (FWHM).

Rotational temperature.

Total column density of the molecule. $x$ ($y$) means $x \times 10^y$.

Correction factor that was applied to the column density to account for the contribution of vibrationally excited states, in the cases where this contribution was not included in the partition function of the spectroscopic predictions.

Correction factor that was applied to the column density to account for the contribution of other conformers in the cases where this contribution could be estimated but was not included in the partition function of the spectroscopic predictions.

Linewidth (FWHM).

Velocity offset with respect to the assumed systemic velocity of Sgr B2(N1S), $V_{\mathrm{sys}} = 62$ km s$^{-1}$.

Column density ratio, with $N_{\rm ref}$ the column density of the previous reference species marked with a $\star$.

The parameters were derived from the ReMoCA survey by (cite: sanz-novo2022a).

The parameters were derived from the ReMoCA survey by (cite: Koucky22).

[^1]: https://lsd.univ-lille.fr

[^2]: Madrid Data Cube Analysis on ImageJ is a software developed at the Centre of Astrobiology (CAB) in Madrid: <https://cab.inta-csic.es/madcuba/>; see (cite: Martin2019)

</paper>

Write the methods card for this paper.