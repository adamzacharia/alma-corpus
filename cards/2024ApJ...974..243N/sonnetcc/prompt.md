# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024ApJ...974..243N\sonnetcc\reply.txt

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
 "bibcode": "2024ApJ...974..243N",
 "title": "Measuring 60 pc-scale Star Formation Rate of the Nearby Seyfert Galaxy NGC 1068 with ALMA, HST, VLT/MUSE, and VLA",
 "year": 2024,
 "journal": "The Astrophysical Journal",
 "first_author": "Nagashima, Yuzuki",
 "n_authors": 10,
 "arxiv_id": "2407.15931",
 "doi": "10.3847/1538-4357/ad6312",
 "alma_projects_linked_by_archive": [
  "2011.0.00061.S",
  "2012.1.00657.S",
  "2013.1.00055.S",
  "2013.1.00060.S",
  "2013.1.00111.S",
  "2013.1.00188.S",
  "2013.1.00221.S",
  "2013.1.00279.S",
  "2015.1.00960.S",
  "2016.1.00023.S",
  "2016.1.00052.S",
  "2016.1.00232.S",
  "2017.1.01666.S",
  "2018.1.00037.S",
  "2018.1.01506.S",
  "2018.1.01684.S",
  "2019.1.00130.S",
  "2021.2.00049.S"
 ]
}
```

Paper text:
<paper>
# Measuring 60-pc-scale Star Formation Rate of the Nearby Seyfert Galaxy NGC 1068 with ALMA, HST, VLT/MUSE, and VLA

## Abstract

Star formation rate (SFR) is a fundamental parameter for describing galaxies and inferring their evolutionary course. H II regions yield the best measure of instantaneous SFR in galaxies, although the derived SFR can have large uncertainties depending on tracers and assumptions. We present an SFR calibration for the entire molecular gas disk of the nearby Seyfert galaxy NGC 1068, based on our new high-sensitivity ALMA 100 GHz continuum data at 55 pc ($=$ 0.8$''$) resolution in combination with the *HST* Pa$\alpha$ line data. In this calibration, we account for the spatial variations of dust extinction, electron temperature of H II regions, AGN contamination, and diffuse ionized gas (DIG) based on publicly available multi-wavelength data. Especially, given the extended nature and the possible non-negligible contribution to the total SFR, a careful consideration of DIG is essential. With a cross-calibration between two corrected ionized gas tracers (free-free continuum and Pa$\alpha$), the total SFR of the NGC 1068 disk is estimated to be 3.2 $\pm$ 0.5 $M_{\odot}$ yr$^{-1}$, one-third of the SFR without accounting for DIG (9.1 $\pm$ 1.4 $M_{\odot}$ yr$^{-1}$). We confirmed high SFR around the southern bar-end and the corotation radius, which is consistent with the previous SFR measurements. In addition, our total SFR exceeds the total SFR based on 8 $\mu$m dust emission by a factor of 1.5. We attribute this discrepancy to the differences in the young stars at different stages of evolution traced by each tracer and their respective timescales. This study provides an example to address the various uncertainties in conventional SFR measurements and their potential to lead to significant SFR miscalculations.

# Introduction

Star formation rate (SFR) and its surface and volume density are fundamental observable parameters characterizing galaxies and their evolution (cite: KennicuttEvans12) and even the evolution of the Universe (cite: MadauDickinson14). A spatial SFR distribution of galaxies provides key insights into where and how stars are formed in galaxies. As star formation plays an important role in the matter life cycle of galaxies by converting gas to stars and also spreading enriched materials to the surrounding interstellar medium (ISM) through stellar feedback processes, it is crucial to measure an accurate SFR distribution in galaxies in a spatially resolved manner.

Based on an assumed initial mass function (IMF) (cite: Kroupa01), SFR can be estimated by measuring the amount of young massive stars through many different electromagnetic radiation mechanisms from X-ray to radio (see the review by (cite: KennicuttEvans12)).

However, each of the current SFR measurement methods has many parameters with large uncertainties. Many previous works have derived SFR values by making assumptions about these parameters (cite: Leitherer99; Calzetti08). Examples of such parameters include electron temperature, extinction, and IMF when using SFR tracers emitted from H II regions. SFR obtained from single wavelengths is subject to biases that depend on the characteristics of each wavelength (cite: Calzetti08; Calzetti13). This was a major problem when comparing SFR obtained with other methods, as it creates a large difference and can cause significant misinterpretation of the SFR of each galaxy.

To alleviate uncertainties raised above, some studies have utilized multiple SFR tracers (cite: Calzetti08; Calzetti13) by calibrating emissions from massive stars and H II regions, with cross-calibration among different ionized gas tracers (cite: Murphy11). A key approach is using complementary tracers, e.g., hydrogen recombination lines and thermal bremsstrahlung emission (cite: Bendo15). These tracer combinations effectively offset each other’s weaknesses, enabling more accurate SFR measurements (cite: Bendo15; Bendo16; Michiyama20; MIlls21) with minimal bias and constraints of previously undetermined parameters like electron temperatures. Emissions from both tracers originate from H II regions starting shortly after star formation, providing current star formation insights. The H$\alpha$ line, a powerful SFR tracer, faces extinction by interstellar dust, which is mitigated by using the Paschen line (Pa$\alpha$), the strongest Hydrogen recombination line in near-infrared and less affected by dust (cite: Tateuchi13). Conversely, thermal bremsstrahlung (free-free radiation) is observable by ALMA at millimeter wavelengths and is free from dust extinction, a unique advantage over other SFR tracers (cite: Draine11). Despite being faint, recent ALMA observations have demonstrated its detectability in extragalactic systems with sufficient sensitivity (cite: Saito15; Kawana22).

When measuring the SFR of galaxies using an ionized gas tracer, it is necessary to exclude contributions from ionizing sources other than H II regions. One such example is diffuse ionized gas (DIG). DIG has a lower ionization state than the typical H II region (cite: Haffner09). Although DIG had been recognized, detailed studies of the DIG were not actively pursued before state-of-the-art telescopes such as VLT/MUSE came online. Recent observational studies have thus begun to report DIG-corrected SFR (cite: Momose2013; Kaplan16; Kreckel16; Morokuma17; Belfiore22). Furthermore, it has become common to derive SFR by taking into account DIG even in systematic surveys (cite: Kreckel16; Lacerda18; Tomicic21; Belfiore22).

Another ionizing source, that could contaminate the measurement of an SFR, is an active galactic nucleus (AGN). Ionization by AGN produces more harder spectrum than young massive stars. This significantly affects the SFR measurement based on ionized gas tracers. To effectively separate AGN contributions, Baldwin-Phillips Terlevich (BPT) diagram (cite: Baldwin81) is a widely employed technique. This method mainly utilizes ratios of auroral lines (\[O III\]/H$\beta$ and \[N II\]/H$\alpha$), which are highly sensitive to ionization sources, allowing for a more accurate determination of SFR.

This study aims to obtain a high-quality map of the instantaneous SFR of the nearby prototypical spiral galaxy, NGC 1068 (Figure [1](#Fig:opN1068_Fig1); $D_{\rm L}$ $=$ 13.97 Mpc, z $\simeq$ 0.0038; 1.0$''$ $=$ 72 pc; (cite: Anand2021)). NGC 1068 is known to host a biconical ionized and molecular gas outflow driven by the central AGN (cite: Das06; Garcia-Burrillo14; Garcia-Burillo2019; Saito22a), but also known as one of the ideal targets to study star formation in external galaxies because it is nearly face-on (cite: Planesas91), massive (cite: Leroy19), gas-rich ($M_{\rm H_2}$ $\simeq$ 1.5 $\times$ 10$^10$ $M_\odot$; (cite: Planesas89)) and classified as a luminous infrared galaxy ($L_{\mathrm{IR}}$ $=$ 1$0^{11.4}$ $L_{\odot}$; (cite: Armus09)). These properties make NGC 1068 easily observable and it became the subject of numerous observations and studies. Therefore, NGC 1068 serves as a laboratory-like galaxy with its rich observational data and its typical properties. By investigating the physical properties of this galaxy, we can enhance our understanding of galaxies at different ages or redshifts.

![](image/optical_NGC1068.png)

The paper is divided into the following sections: In Section [2](#sec:obs), we describe the observations and the data used in this study. In Section [3](#sec:method_result), we present the method and the procedure to obtain a plausible SFR map using Pa$\alpha$ and free-free continuum. In Section [4](#sec:disc), we discuss the characteristics of star-forming activities and electron temperature variation in NGC 1068 in comparison with other galaxies in the literature. Finally, we summarize this paper in Section [5](#sec:summary).

# Observations and Data Processing

Here we briefly describe the data we use in this study, including ALMA, *HST*, MUSE, and VLA, and the hexagonal resampling as a common post-process after the imaging of each data.

## ALMA Data

### Band 3 Continuum

We carried out two imaging spectral scans toward NGC 1068 with ALMA Band 3 and the 12-m array (2013.1.00279.S: PI=T. Nakajima; (cite: Nakajima23)) and with the 7-m array (2021.2.00049.S: PI=T. Saito). To further gain sensitivity, we utilized ten projects publicly available in the ALMA archive that cover the Band 3 frequency coverage with the 12-m or 7-m array (2011.0.00061.S, 2012.1.00657.S, 2013.1.00055.S, 2013.1.00060.S, 2013.1.00221.S, 2015.1.00960.S, 2018.1.01506.S, 2018.1.01684.S, 2018.1.01684.S, and 2019.1.00130.S). This results in extremely wide-band observations covering nearly the entire Band 3 coverage from 84 GHz to 116 GHz (i.e., $\lambda$ = 3 mm). Total integration time with the 12-m array and the 7-m array are 24.9 hours and 26.3 hours, respectively.

Following (cite: Saito22a) and (cite: Saito22b), we performed calibration with the observatory-provided calibration pipeline (cite: Hunter23) and imaging with the `PHANGS-ALMA imaging pipeline` (cite: Leroy21a). Spectral channels contaminated by strong molecular lines reported in (cite: Saito22b) and (cite: Nakajima23) are removed before imaging the continuum. We performed the continuum imaging with multi-term (multi-scale) multi-frequency synthesis (mtmfs; (cite: Rau11)) using `CASA tclean`. The reference frequency is set to be 99.7015 GHz, which is nearly the middle of the line-free frequency range. Hereafter, we call this Band 3 continuum map a 100 GHz continuum map (Figure [1](#Fig:opN1068_Fig1) right). The details of the image properties are summarized in Table [\[table:ContPropTable\]](#table:ContPropTable).

### Band 6 Continuum

We collected eight Band 6 projects that employed the 12-m array from the archive (2013.1.00111.S, 2013.1.00188.S, 2013.1.00221.S, 2016.1.00023.S, 2016.1.00052.S, 2016.1.00232.S, 2017.1.01666.S, and 2018.1.00037.S). In addition to these archive data, we carried out a Band 6 spectral scan with the 7-m array (2021.2.00049.S: PI=T. Saito) that mostly covers between 211 GHz and 275 GHz to recover extended structures possibly missed by the archival 12-m data. We performed basically the same calibration and imaging procedures for the Band 3 data. We set the reference frequency to 260.5180 GHz when imaging with the mtmfs mode (hereafter 261 GHz continuum). The details of the image properties are summarized in Table [\[table:ContPropTable\]](#table:ContPropTable).

![](image/Fluxmaps.png)

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| $\nu_{\rm rest}$ | $\theta_{\rm maj} \times \theta_{\rm min}$ | RMS$_{\rm pix}$ | RMS$_{\rm hex}$ | Med $S_{\rm hex}$ | S/N$_{\rm hex}$ | $N_{\rm hex}$ |  |  |  |  |
| (GHz) | ($^{\prime}$$^{\prime}$) | (mJy beam$^{-1}$) | (mJy beam$^{-1}$) | (mJy) | (16$^{\rm th}$–50th$^{\rm th}$–84th$^{\rm th}$–max) |  |  |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |  |  |  |  |
| 14.9 | 0.46 $\times$ 0.38 | 0.2 | 2.1 | 1.3 | 0.47 –1.49–3.5–367.16 | 993 |  |  |  |  |
| 99.7 | 0.76 $\times$ 0.66 | 0.01 | 0.1 | 0.02 | 3.6–6.6–20.9–1489.5 | 1236 |  |  |  |  |
| 260.5 | 0.44 $\times$ 0.42 | 0.07 | 0.6 | 0.3 | 4.9–11.1–27.4–632.0 | 585 |  |  |  |  |

: Imaging properties of continuum data

Table notes: Column 1: Continuum reference frequency. Column 2: Major and minor axes of the original synthesized beam in full width at half maximum (FWHM) before convolution to 55 pc ($=$0.8$''$). Column 3: Noise RMS per pixel. Column 4: Noise RMS per hexagon. Column 5: Median flux of detected hexagons. Column 6: S/N ratio distribution of detected hexagons. Column 7: Number of detected hexagons.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Line | $\lambda_{\rm rest}$ | $\theta_{\rm res}$ | RMS$_{\rm pix}$ | RMS$_{\rm hex}$ | Med $F_{\rm hex}$ | S/N$_{\rm hex}$ | $N_{\rm hex}$ |  |  |  |
|  | (${\rm \AA}$m) | ($^{\prime}$$^{\prime}$) | (10$^{-15}$ erg cm$^{-3}$ s$^{-1}$) | (10$^{-15}$ erg cm$^{-3}$ s$^{-1}$) | (10$^{-15}$ erg cm$^{-3}$ s$^{-1}$) | (16$^{\rm th}$–50th$^{\rm th}$–84th$^{\rm th}$–max) |  |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |  |  |  |
| \[O III\] | 5007 | 0.8$''$ | 1.0 | 3.5 | 2.24 | 9.2–14.0–29.5–181.9 | 2180 |  |  |  |
| H$\alpha$ | 6563 | 0.8$''$ | 0.16 | 0.6 | 5.39 | 21.4–53.8–100.6–306.6 | 2180 |  |  |  |
| \[N II\] | 6584 | 0.8$''$ | 0.5 | 1.9 | 3.63 | 15.0–27.2–44.1–155.6 | 2181 |  |  |  |
| \[S II\] | 6716 | 0.8$''$ | 0.02 | 0.08 | 0.1 | 14.6–27.6–48.5–243.0 | 2180 |  |  |  |
| \[S II\] | 6731 | 0.8$''$ | 0.02 | 0.08 | 0.1 | 14.0–24.1–38.8–183.1 | 2185 |  |  |  |
| Pa$\alpha$ | 18756 | 0.26$''$ | 0.05 | 0.3 | 4.15 | 21.5–82.5–267.8–3018.9 | 1873 |  |  |  |

: Imaging properties of line data

Table notes: Column 1: Line name. Column 2: Line rest wavelength. Column 3: Typical seeing for MUSE and PSF size for HST ($^{\dagger}$(cite: Mingozzi19), (cite: Sanchez-Garcia22)). Column 4: Noise RMS per pixel. Column 5: Noise RMS per hexagon. Column 6: Median flux of detected hexagons. Column 7: S/N ratio distribution of detected hexagons. Column 8: Number of detected hexagons.

|                   | Unit |  $r <$ 0.8 kpc  |  $r >$ 0.8 kpc  |     |     |     |     |     |     |
|:------------------|:----:|:---------------:|:---------------:|:---:|:---:|:---:|:---:|:---:|:---:|
| $S_{\rm 14.9GHz}$ |  Jy  |  2.32$\pm$0.01  |     $<$0.02     |     |     |     |     |     |     |
| $S_{\rm 100GHz}$  |  Jy  | 0.111$\pm$0.005 | 0.021$\pm$0.001 |     |     |     |     |     |     |
| $S_{\rm 261GHz}$  |  Jy  | 0.042$\pm$0.004 | 0.119$\pm$0.012 |     |     |     |     |     |     |

: Photometry for the inner and outer regions of NGC 1068

Table notes: We only consider the statistical noise in this table.

## Ancillary Data

Here we briefly describe the ancillary data we use in this study.

### HST Data

We use the drizzled and processed *HST* Pa$\alpha$ map which is provided by M. Sánchez-Garcı́a (private communication). The details of the data properties and data reduction can be found in (cite: Garcia-Burrillo14) and (cite: Sanchez-Garcia22). We conduct dust extinction correction by the Balmer decriment (cite: Calzetti00) to the Pa$\alpha$ map (See [3.2.2](#sec:method_result:extinctionCorr) for more details). The details of the image properties are summarized in Table [\[table:lineProperties\]](#table:lineProperties).

### MUSE Data

We use the calibrated data cube of the integral-field spectroscopic data of NGC 1068 in the archive, collected with the MUSE (cite: Bacon10) on the VLT (program ID: 094.B-0321 (A), PI: Marconi). We downloaded the MUSE data cube from the ESO archive, as well as publicly available $\mbox{\rm [S II]}\lambda\lambda$9069,9532/$\mbox{\rm [S II]}\lambda\lambda$6717,6731 ratio map and dust extinction map (cite: Mingozzi19). The total integration time of the data used is 2800 s. The data cube covers from 4750 ${\rm \AA}$ to 9350 ${\rm \AA}$ with a spectral resolution going from 1800 at 4650 ${\rm \AA}$ to 3750 at 9300 ${\rm \AA}$. The mean seeing for the observation is $\sim0''.8$.

Spectral extraction and measurement are performed using `Astropy` (cite: Astropy13; Astropy18; Astropy22) and `Specutils` (cite: Earl23). The details of the image properties are summarized in Table [\[table:lineProperties\]](#table:lineProperties).

### VLA Data

We downloaded a 14.9 GHz (Ku-band) radio continuum map taken by VLA from the NRAO Data Archive. The retrieved data were originally taken with the BnA configuration with 27 antennas on December 5th, 1991, and reprocessed on July 29, 2008. The achieved spatial resolution is 0.41$''$ and the achieved sensitivity is 0.157 mJy beam$^{-1}$.

## Hexagonal sampling

We align all the maps used in this paper into the same hexagonal close‐packed grid (cite: Brok21; Saito22b) that naturally covers an area without gaps or overlaps (cite: Birch2007). All images are resampled into 55 pc sized hexagonal grid pixels that are comparable to or lower than their spatial resolution, which ensures the independence of the spatial information of each pixel. Before the hexagonal regridding described below, we convolve all the ALMA and VLA maps to a round beam with 0.8$''$. That allows us to study star formation at each area covering a single or multiple H II regions. We use the MUSE and *HST* maps as is whose spatial resolutions are comparable or better than 0.8$''$. The size of each hexagon is set to be 0.8$''$ which minimizes the pixel-to-pixel correlation due to the beam oversampling when imaging. We perform this hexagonal regridding by averaging pixels over each hexagon. Then, clipping based on signal-to-noise ratio (at an S/N of 3) is done for further analyses. We evaluate the typical rms at signal-free hexagons of each map. Because the typical cloud size of the Milky Way is 40 pc in diameter (cite: Solomon87) which is comparable to the hexagon size (55 pc), we can regard each hexagon as representing at least one molecular cloud (see also (cite: Sun18; Leroy21a)). Thus, in this paper, we aim to create a “**giant molecular cloud (GMC)**-scale" SFR map, which will be used for further analysis in combination with molecular gas tracer data with **GMC**-scale spatial resolution (Nagashima et al. in preparation).

# SFR measurement

In this section, we describe our method to derive a 55 pc-scale SFR map of NGC 1068.

## Method overview

As described in Section [1](#sec:intro), the interaction between free electrons and protons/ions in the ionized ISM is the emission mechanism of the thermal free-free continuum and hydrogen recombination lines. Therefore, SFR values derived from the two ionized gas tracers should agree with each other if all the other calibrations and corrections are properly applied (cite: Michiyama20). Figure [3](#fig:FlowChart_fig3) shows a flowchart describing the process of the SFR calibration employed in this study. Below, we describe each step.

![](image/flowchart_saito.png)

## SFR prescription for Pa$\alpha$

The procedure to derive an SFR map from the calibrated *HST* Pa$\alpha$ map (cite: Garcia-Burrillo14; Sanchez-Garcia22) is listed as follows (see also the left panel of Figure [3](#fig:FlowChart_fig3)):

- Masking AGN radio jet (Section [3.2.1](#sec:method_result:MaskingAGN)).

- Correcting for dust extinction (Section [3.2.2](#sec:method_result:extinctionCorr)).

- Correcting for diffuse ionized gas (Section [3.2.3](#sec:method_result:DIGCorr)).

- Converting from Pa$\alpha$ to SFR (Section [3.2.4](#sec:method_result:convertToSFR)).

We describe this procedure step-by-step below. In Section [3.2.5](#sec:method_result:Possible_AGN_contamination_to_ionized_gas), we describe possible AGN contamination to the ionized gas tracers we employed.

### Masking AGN radio jet

In general, synchrotron emission is the dominant component in continuum emission below 10 GHz. However, due to its relatively shallower spectral index of $-$0.8 (cite: Condon92; Gallimore04), bright synchrotron emission can also significantly contribute to higher frequencies, even around 100 GHz. One should remove the contribution of synchrotron emission from the 100 GHz continuum flux to accurately extract the free-free continuum. Especially, synchrotron emission from the AGN jet is known to be bright in the center of this galaxy (cite: Michiyama22). This is demonstrated in Figure [4](#Fig:sed_fig4). Spectral energy distribution (SED) of the central r$\sim$0.8 kpc shows a decreasing trend, implying a dominant contribution from synchrotron emission. In the case of the disk, SED shows an opposite trend (e.g., free-free and thermal dust dominate). Therefore, we decided to mask the central r$\sim$0.8 kpc from further SFR analyses. This is because we can not accurately remove the contamination by synchrotron emission due to the lack of a sufficient number of SED data points. Practically, we exclude hexagons detected with more than 5 sigma in the entire VLA 14.9 GHz continuum map that traces the bright radio jet components (Figure [2](#Fig:maps_fig2); see also (cite: Gallimore04)).

In addition, we considered removing the possible contribution from the synchrotron emission in the starburst ring. However, the photometric measurements (Table [1](#table:PhotometryCenterOuter)) imply that the effect of the synchrotron emission on the 100 GHz data is negligible in the starburst ring. For pixels at $r$ $>$ 0.8 kpc (i.e., starburst ring), we estimated the expected flux of the synchrotron continuum at 100 GHz to be $<$0.40 mJy when extrapolating the 3$\sigma$ upper limit from the flux of 14.9 GHz data to 100 GHz using a spectral index of $\alpha$ = -0.8. This is $<$19$\%$ of the detectable flux (3$\sigma$ level) in the 100 GHz continuum in the starburst ring. Therefore, we conclude that synchrotron emission has negligible influence on the derivation of the free-free flux at the starburst ring.

![](image/fig2.png)

### Correcting for dust extinction

We correct the Pa$\alpha$ map for dust extinction using an extinction map publicly available. This extinction map is one of the products from the MAGNUM survey (cite: Mingozzi19), which was made by assuming a (cite: Calzetti00) extinction law with $R_{V}$ $=$ 3.1 (i.e., galactic diffuse ISM) and a fixed electron temperature $=$ 10$^5$ K. In our study, we recalculated the $A_{V}$ map by using $R_{V}$ $=$ 4.05, because Pa$\alpha$ at 1.875 $\mu$m does not meet the condition for Equation 7 of (cite: Calzetti00) (see Appendix [7](#sec:appendix:Rv) for more details). Figure [5](#Fig:A1.876mu_fig5) is the map reflecting the extinction at 1.875 $\mu$m ($A_{\rm 1.875\mu m}$), the rest wavelength of Pa$\alpha$. See Appendix [7](#sec:appendix:Rv) for the conversion from $A_{V}$ to $A_{\rm 1.875\mu m}$. In Figure [6](#Fig:subExtinctionSc_fig6), we show a pixel-by-pixel comparison between dust-corrected and uncorrected Pa$\alpha$ maps. The extinction correction does not change individual pixel values significantly (less than $\simeq$0.2 dex), although it changes the total flux by $\simeq$25%. This is comparable to or slightly higher than the uncertainty of the absolute flux calibration of the *HST* data (cite: Sanchez-Garcia22). We note that our NGC 1068 data points follow the "Nearby galaxies" trend seen in the Av-dust relation compiled by (cite: Tomicic17). We will discuss the dust properties of NGC 1068 in detail in a forthcoming paper (Nagashima et al. in prep).

![](image/APa.png)

![](image/TO0Paa-corrPaa.png)

![](image/digmap.png)

### Correcting for diffuse ionized gas

In this study, we derive an SFR map with and without the DIG correction.

We follow the DIG correction method described in (cite: Kaplan16). The authors employed the optical \[S II\]$\lambda$$\lambda$6716,6731/H$\alpha$ line ratio (hereafter \[S II\]/H$\alpha$; the lower-left panel of Figure [2](#Fig:maps_fig2)) and H$\alpha$ flux to evaluate the DIG fraction at each pixel in H$\alpha$ maps (cite: Kreckel16). This method is expected to work because the typical DIG in the Milky Way is known to have a lower H$\alpha$ surface brightness and higher \[S II\]/H$\alpha$ ratio compared to the typical H II region (cite: Madsen06). This method seems to also work for nearby galaxy data (cite: Kaplan16), and thus we decided to employ this method in this study. After creating the DIG fraction map (Figure [7](#Fig:rdig_fig7)), we apply this correction to the extinction-corrected Pa$\alpha$ map to subtract the DIG contribution. The Pa$\alpha$ maps corrected and uncorrected for DIG and extinction are shown in Figure [8](#Fig:Paaflow_fig8). The DIG-corrected map shows much less extended, low surface brightness structures implying that the method works as expected. Details of how we calculate the DIG fraction at each pixel of the Pa$\alpha$ map can be found in Appendix [9](#sec:appendix:SIIHa).

![](image/paaflow.png)

### Converting from Pa$\alpha$ to SFR

Here we describe the SFR prescription for the corrected Pa$\alpha$ line (see also (cite: Murphy11; Bendo15; Bendo16; Michiyama20)). In this study, we follow the prescription described in (cite: Bendo16). We use the Kroupa IMF (cite: Kroupa01), which assumes a mass range of 0.1–100 $M_{\odot}$ and a metallicity (fraction of heavy elements to total elements) of 0.04, double the solar metallicity.

As SFR can be obtained by converting the number of ionized photons from massive stars, we start from the ionizing photon rate, $Q$, $$\begin{equation}
\left (\frac{\mathrm{SFR}}{M_{\odot}\,\mathrm{yr}^{-1}}\right) = 5.41 \times 10^{-54}\left (\frac{Q}{\mathrm{s^{-1}}}\right).
\label{eq:1}
\end{equation}$$

$Q$ can be expresssed as,

$$\begin{eqnarray}
\lefteqn{\left (\frac{Q}{\mathrm{s^{-1}}}\right)} \nonumber \\
& = & \left (\frac{\alpha_{\mathrm{B}}}{\mathrm{cm^{-3}\ s^{-1}}}\right) \left (\frac{\epsilon}{\mathrm{erg\ s^{-1}\ cm^{-3}/}n_\mathrm{e}n_\mathrm{p}}\right)^{-1} \left (\frac{L_{\mathrm{RL}}}{\mathrm{erg\ s^{-1}}}\right),\nonumber\\ 
\label{eq:Q}
\end{eqnarray}$$

where $\alpha_{\rm B}$ is the total recombination coefficient, $\epsilon$ is the specific emissivity of each recombination line listed in (cite: StoreyandHummer95), $n_{\rm e}$ is the electron volume density, $n_{\rm p}$ is the proton volume density (see (cite: Michiyama20) for more details), and $L_{\rm{RL}}$ is the recombination line luminosity. With the case-B recombination assumption (cite: BakerandMenzel38), $\alpha_{\rm B}$ varies with electron temperature ($T_{\rm e}$) and electron density ($n_{\rm e}$). We use an interpolated relation between $\alpha_{\rm B}$ and $T_{\rm e}$ described in (cite: Michiyama20), $$\begin{equation}
\left (\frac{\alpha_{\mathrm{B}}}{\mathrm{cm^{-3}\ s^{-1}}}\right) = 3.63 \times 10^{-10} \left (\frac{T_{\mathrm{e}}}{\mathrm{K}}\right)^{-0.79}.
\label{eq:a_B}
\end{equation}$$ With fixing $n_{\rm e}$ to be 10$^3$ cm$^{-3}$ and based on the list in (cite: StoreyandHummer95), we employ the following relation between $\epsilon$ and $T_{\rm e}$ for Pa$\alpha$, $$\begin{equation}
\left (\frac{\epsilon}{\mathrm{erg\ s^{-1}\ cm^{-3}/}n_\mathrm{e}n_\mathrm{p}}\right) = 6.37 \times 10^{-24} \left (\frac{T_{\mathrm{e}}}{\mathrm{K}}\right)^{-1.05}.
\label{eq:eps}
\end{equation}$$ $\epsilon$ does not vary significantly within the range of $n_{\rm e}$ $=$ 10$^2$–10$^5$ cm$^{-3}$, while it varies within the range of $T_{\rm e}$ $=$ 1000–10000 K. We calculate $L_{\rm{RL}}$ by using the equation in (cite: Solomon05), $$\begin{eqnarray}
\lefteqn{ \left (\frac{L_{\mathrm{RL}}}{\mathrm{erg\ s^{-1}}}\right) } \nonumber \\
& = & 4.0 \times 10^{30} \left (\frac{\int{f_{\mathrm{RL}}dv}}{\mathrm{Jy\ km\ s^{-1}}}\right) \left (\frac{\nu_{\mathrm{rest}}}{\mathrm{GHz}}\right) (1+z)^{-1} \left (\frac{D_{\mathrm{L}}}{\mathrm{Mpc}}\right)^2,\nonumber\\
\label{eq:L}
\end{eqnarray}$$ where $\int{f_{\mathrm{RL}}dv}$ is the line total flux, $\nu_{\mathrm{rest}}$ is the line rest frequency, z is the source redshift ($=$ 0.003793), and $D_{\rm L}$ is the source luminosity distance ($=$ 13.97 Mpc; (cite: Anand2021)). Finally, Pa$\alpha$-based SFR (SFR$_{\rm Pa\alpha}$) can be expressed as, $$\begin{eqnarray}
\lefteqn{ \left (\frac{\mathrm{SFR}_{\mathrm{Pa}\alpha}}{M_{\odot}\ \mathrm{yr^{-1}}}\right) } \nonumber \\
& = & 5.41 \times 10^{-54} \left (\frac{\alpha_{\mathrm{B}}}{\mathrm{cm^{-3}\ s^{-1}}}\right) \left (\frac{\epsilon}{\mathrm{erg\ s^{-1}\ cm^{-3}}}\right)^{-1} \left (\frac{L_{\mathrm{RL}}}{\mathrm{erg\ s^{-1}}}\right) \nonumber \\ \label{eq:SFRPaa}\\
& \propto & \left (\frac{T_{\mathrm{e}}}{\mathrm{K}}\right)^{0.26} \left (\frac{L_{\mathrm{RL}}}{\mathrm{erg\ s^{-1}}}\right).
\label{eq:SFRPaa2}
\end{eqnarray}$$ This equation expresses that the Pa$\alpha$-based SFR has a dependence of $T_{\rm e}^{0.26}$.

We note that the conversion coefficient can vary by a factor of two depending on assumed parameters and star formation history (cite: Bendo15). The conversion coefficient in Equation [\[eq:1\]](#eq:1) were calculated using STARBURST99 (cite: Leitherer99).

### Possible AGN contamination

Here we briefly describe the possible effect of the AGN outflow to the ionized gas tracers.

The AGN outflow in NGC 1068 is known to be spatially extended and bright in NGC 1068 (cite: Das06). This outflow is a possible source of contaminating an SFR measurement using ionized gas tracers such as hydrogen recombination lines.

To investigate the AGN effect on the SFR analysis we employed, we diagnosed it with a BPT diagram on a pixel-by-pixel basis (cite: Mingozzi19). We classify whether the ionization source is starburst or AGN using the \[S II\]/H$\alpha$ and \[O III\]/H$\beta$ ratios. A small fraction of pixels in the northern part of the starburst ring (i.e., northern bar-end) is classified as pixels affected by the AGN outflow as shown in Figure D.1 of (cite: Mingozzi19). However, this classification as AGN does not mean that the star formation rate derived for the molecular gas disk is contaminated. The orientation between the disk and the outflow reported in the literature suggests that the contamination is unlikely (cite: Das06; Garcia-Burrillo14; Saito22a). Thus, the main body of the biconical ionized gas outflow is located in the extraplanar region and the ionized gas on the molecular gas disk is not directly and severely affected by the outflow except for the central kpc we masked out (as shown in Figure 17 of (cite: Garcia-Burrillo14)). Therefore, we concluded that the northern part of the disk of NGC 1068 can be used for the SFR measurement. Thus, we concluded that the northern part of the disk of NGC 1068 can be used for the SFR measurement. This is supported by the fact that the Pa$\alpha$ map shows quite similar structures seen in the 100 GHz continuum map, except for the central kpc region severely contaminated by the AGN outflow. Details of the analysis can be seen in (cite: Mingozzi19).

## SFR prescription for 100 GHz continuum

The procedure to derive an SFR map from the ALMA 100 GHz continuum map is itemized as follows (see also the middle panel of Figure [3](#fig:FlowChart_fig3)):

- Masking AGN radio jet (same as Section [3.2.1](#sec:method_result:MaskingAGN)).

- Removing cold dust (Section [3.3.1](#sec:method_result:100GHz_prescription:Remove_colddust)).

- Converting from free-free continuum to SFR (Section [3.3.2](#sec:method_result:100GHz_prescription:Conv_from_100GHz)).

We describe this procedure step-by-step in this section.

### Removing cold dust continuum

As described in Section [3.2.1](#sec:method_result:MaskingAGN), we decided to mask pixels detected within the central r$\sim$0.8 kpc of the VLA 14.9 GHz continuum map (Figure [2](#Fig:maps_fig2) top-left), which results in removing the central jet structure from the 100 GHz continuum map. The remaining pixels are free from contamination by synchrotron emission. Thus, in this study, we consider correcting the 100 GHz continuum only for the cold dust contribution. we derive the expected cold dust flux map at 100 GHz by extrapolating the ALMA 261 GHz continuum map (Figure [2](#Fig:maps_fig2) top-right) with a fixed spectral index of 4 and subtract it from the 100 GHz map. This index is a typical value for the Rayleigh-Jeans tail of nearby starburst galaxies (cite: Murphy11; Saito16). The effect of this subtraction can be visually seen in Figure [9](#Fig:coldsub_fig9).

Figure [10](#Fig:coldsub_sc_fig10) shows a pixel-by-pixel comparison between the two 100 GHz continuum maps. Most pixels distribute along the 1:1 relation (i.e., no flux change), although few pixels show $\lesssim$0.3 dex change. The difference in the total flux is 13$\pm$1 %, highlighting the importance of the subtraction of cold dust component from the 100 GHz flux. It is not that large a percentage, but it is important to note that we cannot consider all of the Band 3 continuum flux coming from free-free continuum. We regard the dust-subtracted 100 GHz map as a free-free continuum map hereafter. Note that if we assume a shallower Rayleigh-Jeans slope of 3.8 instead, the total flux of the cold dust component at 100 GHz increases by $\simeq$4%. This factor is smaller than the nominal flux accuracy of the ALMA Band 6 data (10%), and thus we regard the difference due to the assumed slopes as negligible. This could be further investigated by adding more data points to the higher frequency regime. For pixels detected in the 100 GHz continuum map but not in the 261 GHz continuum map (See Figure [2](#Fig:maps_fig2)), subtraction is not conducted.

![](image/coldsub.png)

![](image/TO0ffb6-ffb3.png)

### Converting from free-free to SFR

Following (cite: Michiyama20), free-free-based SFR (SFR$_{\rm FFC}$) can be expressed as, $$\begin{eqnarray}
\lefteqn{\left ( \frac{\mathrm{SFR_{FFC}}}{M_\odot\ \mathrm{yr^{-1}}} \right)} \nonumber \\
& = & 9.49\times10^{10}g_{\mathrm{ff}}^{-1} \left (\frac{\alpha_{\mathrm{B}}}{\mathrm{cm^3\ s^{-1}}}\right) \left (\frac{T_{\mathrm{e}}}{\mathrm{K}}\right)^{0.5} \left (\frac{D_{\mathrm{L}}}{\mathrm{Mpc}}\right)^2 \left (\frac{f_{\mathrm{FFC}}}{\mathrm{Jy}}\right), \nonumber \\
\label{eq:SFRFFC} 
\end{eqnarray}$$ where $g_{\rm ff}$ is the gaunt factor and $f_{\rm FFC}$ is the free-free continuum flux. The gaunt factor can be written as, $$\begin{equation}
g_{\mathrm{ff}} = 0.5535 \ln\left| \left (\frac{T_{\mathrm{e}}}{\mathrm{K}}\right)^{1.5} \left (\frac{\nu}{\mathrm{GHz}}\right)^{-1}Z^{-1} \right| - 1.682, \label{eq:gff}
\end{equation}$$ where Z is the ionic charge ($=$ 1). $g_{\rm ff}$ can vary by a factor of up to $\simeq$1.4 with 3000 K $<$ $T_{\rm e}$ $<$ 10000 K.

### Evaluating the effect of diffuse ionized gas on 100 GHz continuum

Our SFR prescription for the free-free continuum does not include the DIG correction, unlike the prescription for Pa$\alpha$. This is because our 100 GHz continuum map is not sensitive enough to detect free-free continuum from the DIG of NGC 1068. We estimate the expected free-free continuum flux from the DIG based on the observed Pa$\alpha$ flux of the DIG with some simple assumptions. The expected peak DIG flux at 100 GHz is 0.01 $\mu$Jy beam$^{-1}$ which is well below the sensitivity (0.9 mJy beam$^{-1}$). We refer the reader to Appendix [8](#sec:appendix:contamiDIG) for a more detailed explanation and calculation.

Our conclusion can also be supported by the visual impression of the 100 GHz continuum map, i.e., the free-free continuum map shows much less extended structures compared to the original Pa$\alpha$ map or H$\alpha$ map that contains the DIG components (Figure [2](#Fig:maps_fig2)).

## Derivation of the electron temperature

Finally, the procedure to derive the best $T_{\rm e}$ value is itemized as follows (see also the right panel of Figure [3](#fig:FlowChart_fig3)):

- Estimating $T_{\rm e}$ (Section [3.4.1](#sec:method_result:TeDerive:TeGuess)).

- Applying the best $T_{\rm e}$ and calculating SFR (Section [3.4.2](#sec:method_result:TeDerive:SFRGuess)).

We describe this procedure step-by-step in this section.

### Estimating electron temperature

We derive two independent SFR maps based on two independent ionized gas tracers, Pa$\alpha$ and free-free continuum, after 55-pc-sized hexagonal gridding and corrections as explained in the previous Sections. Because the two tracers can be assumed to come from the same ionized gas ISM in galaxies, two SFR maps should agree with each other if all the other corrections and assumptions work (e.g., DIG correction and extinction correction). Any difference between the two SFR maps arises from different parameters used in Equations [\[eq:SFRPaa\]](#eq:SFRPaa) and [\[eq:SFRFFC\]](#eq:SFRFFC), i.e., $T_{\rm e}$ (see also (cite: Michiyama20)). This is the concept of the $T_{\rm e}$ derivation employed in this study. In practice, we perform a least-squares regression with a fixed slope of unity for a scatter plot between the Pa$\alpha$-based SFR map and the free-free-based SFR map (Figure [11](#Fig:scatter_fig11)). When fitting, we weight data point located at ($x_{i}$, $y_{i}$) with $$\begin{equation}
w_{i} = \sigma_{i}^{-1} = \left( \frac{\sigma_{x,i}^{2}}{x_{i}^{2}} + \frac{\sigma_{y,i}^{2}}{y_{i}^{2}} \right)^{-0.5}
\end{equation}$$ where $\sigma_{i,{\rm x}}$ is the uncertainty of $x_i$. Any deviation of the intercept from 0 implies a wrong $T_{\rm e}$ value used for the SFR calculation. We search for the best $T_{\rm e}$ by varying the applied $T_{\rm e}$ value to calculate SFR and track the intercept (see examples in Figure [12](#Fig:Te-in_fig12)). When all the corrections work and the assumed $T_{\rm e}$ value is correct, the intercept should become 0 (i.e., Pa$\alpha$-based SFR and free-free-based SFR are matched). Note that this does not necessarily imply the total SFR derived from Pa$\alpha$ and free-free continuum agree because the number of detected pixels can be different.

We performed the regression for two cases: (1) free-free-based SFR and Pa$\alpha$-based SFR corrected for DIG, and (2) free-free-based SFR and Pa$\alpha$-based SFR not corrected for DIG. The searched $T_{\rm e}$ range is between 500 and 30000 K. The relation between $T_{\rm e}$ and the fitted intercept for cases 1 and 2 is shown in Figure [12](#Fig:Te-in_fig12). We regard the fitting error bar as the error of the intercept. Then, we calculate the error bar of $T_{\rm e}$ based on Figure [12](#Fig:Te-in_fig12).

In the case 1 (case 2), we derived $T_{\rm e}$ $=$ 6690$^{+360}_{-340}$ K (3510$^{+120}_{-110}$ K). Case 1 shows a higher value that can be naturally explained by the subtraction of Pa$\alpha$ flux due to the DIG correction.

### Applying the best $T_{\rm e}$ and calclating SFR

Finally, we make $\Sigma_{\mathrm{SFR}}$ maps in the entire starburst ring of NGC 1068 (Figure [13](#Fig:SFRs_fig13)) by applying the best-fitted $T_{\rm e}$ derived in Section [3.4.1](#sec:method_result:TeDerive:TeGuess) to the Pa$\alpha$ map. As shown in Figure [13](#Fig:SFRs_fig13), The DIG correction significantly reduces extended, low surface brightness structures seen in the DIG-uncorrected $\Sigma_{\mathrm{SFR}}$ map. The total SFR is 3.2 $\pm$ 0.5 $M_{\odot}$ yr$^{-1}$ for case 1 and 9.1 $\pm$ 1.4 $M_{\odot}$ yr$^{-1}$ for case 2 in the entire starburst ring of NGC 1068. When correcting for DIG, $T_{\rm e}$ increases and the total SFR decreases. All measured parameters including $T_{\rm e}$ and SFRs are listed in Table [\[table:comparingSFRmap\]](#table:comparingSFRmap). To make a fair comparison, we match the pixels between the case 1 and case 2 analysis, namely, we use pixels that survived in case 1 to calculate DIG-uncorrected $T_{\rm e}$ and SFR. We call this case 2b. We get $T_{\rm e}$ $=$ 2820 K, SFR $=$ 5.7 $\pm$ 1.2 $M_{\odot}$ yr$^{-1}$ in this case. In case 2b, $T_{\rm e}$ is less than half of that in case 1, while SFR is about twice larger. Therefore, we concluded that the difference between case 1 and case 2 is not due to the difference in the number of pixels but is an actual trend due to the DIG correction.

Histograms of the $\Sigma_{\mathrm{SFR}}$ are shown in Figure [14](#Fig:SFRh_fig14). The 16$^{\rm th}$–50$^{\rm th}$–84$^{\rm th}$–max percentiles are 0.2–0.6–2.1–46.7 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ and 0.5–1.2–3.5–47.1 $M_{\odot}$ yr$^{-1}$ kpc$^{-2}$ for case 1 and case 2, respectively. As expected, the DIG-corrected $\Sigma_{\mathrm{SFR}}$ distribution shifts to the lower $\Sigma_{\mathrm{SFR}}$ regime compared to the DIG-uncorrected one as seen in the percentiles. In addition, different $T_{\rm e}$ values used for the SFR derivation contribute to these pixels.

![](image/DIGconsSFRscatter.png)

![](image/DIGconsSFRcomp.png)

![](image/DIGconsSFRmap.png)

![](image/DIGconsSFRhist.png)

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  | Best $T_{\rm e}$ | SFR$_{\rm total}$ | SFR$_{\rm max}$ | SFR$_{\rm median}$ | SFR$_{\rm min}$ | $N_{\rm hex}$ |  |
|  | \(K\) | ($\rm{M_{\odot} yr^{-1}}$) | ($\rm{M_{\odot} yr^{-1} kpc^{-2}}$) | ($\rm{M_{\odot} yr^{-1} kpc^{-2}}$) | ($\rm{M_{\odot} yr^{-1} kpc^{-2}}$) |  |  |
|  | \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) |  |
| DIG-corrected case | 6690$^{+360}_{-340}$ | 3.2$\pm$0.5 | 46.7$\pm$7.0 | 0.6$\pm$0.1 | 0.002$\pm$0.0005 | 864 |  |
| DIG-uncorrected case | 3510$^{+120}_{-110}$ | 9.1$\pm$1.4 | 47.1$\pm$7.1 | 1.2$\pm$0.2 | 0.25$\pm$0.09 | 1548 |  |

: Calculated SFRs and their properties

Table notes: Column 2: Total SFR of detected hexagons. Column 3: Maximum SFR. Column 4: Median SFR. Column 5: Minimum SFR. Column 6: Number of detected hexagons.

# Discussion

## Reliability of this SFR prescription in comparison with other studies

A previous study by (cite: Tsai12) calculated the $\Sigma_{\mathrm{SFR}}$ of sub-regions of NGC 1068 by measuring 8$\mu$m dust continuum flux using box apertures with 3.46$''$ $\times$ 2.56$''$ (242 $\times$ 179 pc$^2$). Assuming Salpeter IMF (cite: Salpeter55), they measured a total SFR of 3.1 $\pm$ 0.1 $M_{\odot}$ yr$^{-1}$ in the starburst ring of NGC 1068, which is the same as our measurement range. For a fair comparison, we scale the SFR derived in (cite: Tsai12) by Salpeter-to-Kroupa conversion factor 1.6 (cite: Marchesini09) to take into account the difference between the Salpeter IMF and the Kroupa IMF we used. This results in a total SFR of 2.0 $\pm$ 0.1 $M_{\odot}$ yr$^{-1}$, which is roughly two-thirds of our total SFR value. Possible reasons for the inconsistency are as follows:

**Different prescription:** (cite: Tsai12) employed the 8$\mu$m prescription (cite: Wu05) to create their $\Sigma_{\mathrm{SFR}}$ map. This may lead to underestimating the total SFR because unobscured star-forming regions that can be detected in UV rather than IR are likely missed in the IRAC maps. We also note that the assumed star formation history for 8$\mu$m changes the resultant SFR (cite: KennicuttEvans12).

**Different timescale:** Each SFR tracer has a different physical mechanism of emission and therefore traces star-forming regions of different ages and timescales. Our method utilizes emission from ionized gas in H II regions. These emissions represent a nearly instantaneous SFR with the age of $\simeq$3–10 Myr (cite: KennicuttEvans12). Contrary to ionized gas tracers, the timescale of 8 $\mu$m dust emission exceeds 10 Myr (cite: Calzetti08; KennicuttEvans12), making it a more suitable tracer for B-stars than for O-stars traced by ionized gas (cite: Peeters04; Calzetti08; Crocker13). Thus, 8 $\mu$m dust emission is more sensitive to older stars than ionized gas. Therefore, the SFR derived from 8 $\mu$m dust emission may be lower than that derived from ionized gas, because the majority of ionizing photons come from massive young stars (cite: Jones22).

Considering the differences in methodology and timescales among studies, we conclude that our SFR measurement represents an instantaneous SFR of the disk of NGC 1068 with more realistic assumptions and corrections.

## Star-forming activities in NGC 1068

Figure [13](#Fig:SFRs_fig13) shows spatial variations of the $\Sigma_{\mathrm{SFR}}$ within NGC 1068 for cases where the DIG is corrected and uncorrected. The most prominent feature is the high $\Sigma_{\mathrm{SFR}}$ outside of the bar-end on the starburst ring (the red circle in Figure [15](#Fig:drivenSF_fig15)). In general, barred spiral galaxies show elevated star formation in bar-ends (cite: Maeda23). Our result can naturally explain the previous NGC 1068 observations ((cite: Tosaki17; Nakajima23; Sanchez-Garcia22)). Especially, our result supports the findings in (cite: Tosaki17) that significant suppression of a shock tracer CH$_3$OH in the bar-ends of NGC 1068 is due to high-temperature environments of the ISM in the bar-ends caused by active star formation.

There is a high $\Sigma_{\mathrm{SFR}}$ blob at the northern tip of the eastern spiral arm structure. We identify H II regions at the same position in the *HST* composite map by eye (The red circle in Figure [15](#Fig:drivenSF_fig15)). Considering the location of the corotation radius (1.4 kpc; (cite: Schinnerer00)) and the position of spiral shocks (cite: Tosaki17), we speculate that the molecular gas first flows into the spiral potential well where CH$_3$OH is detected, the gas compression in the potential well leads to subsequent star formation which is visible as the high $\Sigma_{\mathrm{SFR}}$ blob. A similar mechanism is suggested to explain the star formation at the corotation radius of the nearby spiral galaxy NGC 628 (cite: Herrera20). Testing this speculation by using our $\Sigma_{\mathrm{SFR}}$ maps ($=$ H II regions), molecular gas maps ($=$ molecular clouds), stellar mass map ($=$ gravitational potential), and kinematics modeling is a future direction of this work.

![](image/drivenSF.png)

## Comparing electron temperature with other galaxies

In this section, we compare $T_{\rm e}$ measurements of this study with those of other nearby well-studied galaxies (NGC 253; (cite: Bendo15) and NGC 4945; (cite: Bendo16)) utilizing the radio hydrogen recombination line to free-free continuum ratio. We discuss possible factors contributing to differences in $T_{\rm e}$ among these three galaxies.

Metallicity is a possible candidate that causes variations in $T_{\rm e}$ (cite: Shaver83; Pilyugin05; Balser24). Two empirical relations are known to control the metallicity of a galaxy: the mass-metallicity relation (MZR) (cite: Kewley01; Curti20) and the negative metallicity gradient (cite: Matteucci01; Sanchez-Menguiano16). MZR, a well-established correlation observed in galaxies (i.e., more massive galaxies tend to have higher metallicities) is likely driven by their star formation histories. The negative gradient within galaxy disks describes the trend observed in many spiral galaxies, where metallicity decreases with increasing distance from the galaxy center, a natural consequence of the inside-out evolution of galaxies (cite: Chiappini97; Fu09).

Table [\[table:Te-met\]](#table:Te-met) lists the galaxy properties necessary to discuss the origin of the $T_{\rm e}$ variation among the three galaxies. The radius $R_{25}$ is defined as the radius at which the surface brightness of a galaxy in $B$-band reaches 25 mag arcsec$^{-2}$. The ratio $R/R_{25}$ is a dimensionless radius that does not depend on the size of galaxies. It normalizes distances to a galaxy’s $R_{25}$, facilitating scale-free analysis of galactic structures and properties across galaxies. In this discussion, $R$ represents the radius of the region within each galaxy where the $T_{\rm e}$ has been measured. $M_{\star}$ expresses the total stellar mass of galaxies. In this discussion, we use $T_{\rm e}$ corrected for the DIG when comparing with NGC 253 and NGC 4945. This is because (1) our DIG-uncorrected $T_{\rm e}$ value for NGC 1068 is unreasonably low, and (2) the radio hydrogen recombination lines used for the SFR measurements for NGC 253 and NGC 4945 are too faint to detect DIG components as like free-free continuum.

Based on MZR, we expect that the galaxy-averaged metallicity of the three galaxies should be comparable, due to the flat shape of the MZR at more massive regime (See Figure 3 in (cite: Curti20)). According to (cite: Curti20), the difference in galaxy-averaged metallicity results in an $T_{\rm e}$ difference of less than 1000 K (cite: Shaver83). This expected $T_{\rm e}$ difference driven by MZR cannot account for the difference in $T_{\rm e}$ among three galaxies.

Regarding the negative metallicity gradient, $R/R_{25}$ where metallicity is measured in each galaxy is significantly different. High metallicity, typically found near galaxy centers, correlates with lower $T_{\rm e}$. NGC 253 has the lowest $T_{\rm e}$ because the measurement is done at the smallest $R/R_{25}$ among the three galaxies. In the case of NGC 1068, the highest $T_{\rm e}$ is measured because $R/R_{25}$ is the largest. Thus, the negative gradient offers a plausible explanation for the differences in $T_{\rm e}$ among the three galaxies. However, it is unclear whether the radial metallicity gradient can fully explain the variations. To verify this, it is necessary to establish a relationship among $T_{\rm e}$ (derived from the ratio of hydrogen recombination line to free-free continuum), metallicity, and galactocentric radius. To achieve this, we have to verify the conditions under which the $T_{\rm e}$ derived from free-free continuum and Pa$\alpha$ shows a good correlation with the $T_{\rm e}$ derived from auroral lines.

|  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|
| galaxy name | log$_{10}$ $M_{\star}$ | $T_{\rm e}$ | $R/R_{25}$ | DIG | tracer combination |
|  | ($M_\odot$) | \(K\) |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) |
| NGC 253 | 10.64$^{a}$ | $3900\pm300$$^b$ | $\simeq0.002^{\mathrm{b,d}}$ | non-detection | H40$\alpha$ $\&$ free-free. |
| NGC 4945 | 10.36$^{a}$ | $5400\pm600$$^c$ | $\simeq0.02^{\mathrm{c,e}}$ | non-detection | H42$\alpha$ $\&$ free-free. |
| NGC 1068 | 10.91$^{a}$ | $6690^{+360}_{-340}$ | $\simeq0.14$ | corrected | Pa$\alpha$ $\&$ free-free. |

: Ionized gas properties of nearby galaxies

Table notes: Column 2: Stellar mass (cite: Leroy19). Column 3: Best-fit $T_{\rm e}$. Column 4: Galactocentric radius at which $T_{\rm e}$ is measured and normalized by $R_{25}$. Column 5: Treatment of the DIG. Column 6: The combination of the ionized gas tracers used in the SFR calibration method. Note that here we only list measurements employing the combination between the hydrogen recombination line and free-free continuum. (a) (cite: Leroy19); (b) (cite: Bendo15); (c) (cite: Bendo16); (d) (cite: deVaucouleur10); (e) (cite: Stanghellini15).

# Summary

We present SFR measurements based on high-resolution (55 pc) and high-sensitivity observations of the 100 GHz continuum taken by ALMA and the hydrogen recombination line Pa$\alpha$ taken by *HST* toward the nearby prototypical Seyfert galaxy NGC 1068. The main goal of this study is to exploit the synergy between free-free continuum and Pa$\alpha$ for deriving reliable SFR for NGC 1068. This specific combination of ionized gas tracers allows us to derive and map accurate $\Sigma_{\mathrm{SFR}}$ distributions. We obtain the best SFR by calibrating, masking, and correcting the effect of $T_{\rm e}$, dust extinction, AGN, and diffuse ionized gas (DIG). The advantage of this synergy is that it compensates for each weakness, i.e., unavoidable dust extinction for the bright Pa$\alpha$ and faintness of the extinction-free free-free continuum. In addition, we demonstrate that consideration for the DIG is crucial for this SFR calibration method. Here we summarize this study:

- The total SFR obtained by cross-calibrating free-free continuum and Pa$\alpha$ is 3.2 $\pm$ 0.5 $M_{\odot}$ yr$^{-1}$ for DIG-corrected case and 9.1 $\pm$ 1.4 $M_{\odot}$ yr$^{-1}$ for DIG-uncorrected case . The most plausible $T_{\rm e}$ is 6690$^{+360}_{-340}$ K for the DIG-corrected case and 3510$^{+120}_{-110}$ K for the DIG-uncorrected case in the starburst ring of NGC 1068. The measurements demonstrate the effects of the DIG on this synergy. (Section [3.4.2](#sec:method_result:TeDerive:SFRGuess))

- The DIG-corrected SFR does not match IR-based SFR in the literature. The reason may come from the difference in timescales or the difference in the tracer used in the study (Section [4.1](#sec:disc:sfr_tsai)). Our new $\Sigma_{\mathrm{SFR}}$ maps are consistent with the spatially resolved trends reported in the literature (Section [4.2](#sec:disc:SFactivity1068)).

- Comparison with studies deriving the total SFR and the galaxy-averaged $T_{\rm e}$ using the same technique (i.e., utilizing a hydrogen recombination line and free-free continuum) suggests that the difference in $T_{\rm e}$ among the sample galaxies is related to the negative metallicity gradient rather than the mass-metallicity relation (Section  [4.3](#sec:disc:comparingTe)).

# acknowledgments

The authors thank an anonymous referee for comments that improved the contents of this paper. We appreciate M. Sánchez-Garcı́a and M. Pereira-Santaella for providing their calibrated *HST* Pa$\alpha$ map. We acknowledge S. Komugi, T. Michiyama, and K. Muraoka for the useful discussion. This work was supported by NAOJ ALMA Scientific Research grant No. 2021-18A. This paper makes use of the following ALMA data:

ADS/JAO.ALMA#2011.0.00061.S,

ADS/JAO.ALMA#2012.1.00657.S,

ADS/JAO.ALMA#2013.1.00055.S,

ADS/JAO.ALMA#2013.1.00060.S,

ADS/JAO.ALMA#2013.1.00111.S,

ADS/JAO.ALMA#2013.1.00188.S,

ADS/JAO.ALMA#2013.1.00221.S,

ADS/JAO.ALMA#2013.1.00279.S,

ADS/JAO.ALMA#2015.1.00960.S,

ADS/JAO.ALMA#2016.1.00023.S,

ADS/JAO.ALMA#2016.1.00052.S,

ADS/JAO.ALMA#2016.1.00232.S,

ADS/JAO.ALMA#2017.1.01666.S,

ADS/JAO.ALMA#2018.1.00037.S,

ADS/JAO.ALMA#2018.1.01506.S,

ADS/JAO.ALMA#2018.1.01684.S,

ADS/JAO.ALMA#2019.1.00130.S, and

ADS/JAO.ALMA#2021.2.00049.S.

ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. This research is based on observations made with the NASA/ESA Hubble Space Telescope, and obtained from the Hubble Legacy Archive, which is a collaboration between the Space Telescope Science Institute (STScI/NASA), the Space Telescope European Coordinating Facility (ST-ECF/ESAC/ESA) and the Canadian Astronomy Data Centre (CADC/NRC/CSA). This research is based on observations collected at the European Southern Observatory under ESO program 094.B-0321 (A). The NVAS image was produced as part of the NRAO VLA Archive Survey, (c) AUI/NRAO. This research has made use of the NASA/IPAC Extragalactic Database (NED), which is funded by the National Aeronautics and Space Administration and operated by the California Institute of Technology. Data analysis was in part carried out on the Multi-wavelength Data Analysis System operated by the Astronomy Data Center (ADC), National Astronomical Observatory of Japan. KN acknowledges support from the JSPS KAKENHI Grant Number 19K03937 and the work of KB was partially supported by the JSPS KAKENHI Grant Number 21K03547 and 23KF0008.

# Facilities

HST (NICMOS), ALMA (Band 3 and Band 6), VLT (MUSE), VLA (Ku-band)

# Software

`ALMA Interferometric Pipeline`, `Astropy` (cite: Astropy13; Astropy18), `CASA` (cite: CASATeam22), `NumPy` (cite: Harris20), `PHANGS-ALMA Pipeline` (cite: Leroy21a), `SciPy` (cite: Virtanen20), `spectral-cube` (cite: Ginsburg19), `radio-beam (`[`https://pypi.org/project/radio-beam/`](https://pypi.org/project/radio-beam/))

# Extinction correction for Pa$\alpha$

We correct dust extinction for Pa$\alpha$ as described in Section [3.2.2](#sec:method_result:extinctionCorr). We use the $A_{V}$ map of NGC 1068 produced in (cite: Mingozzi19). They assumed the selective extinction $R_V$ $=$ 3.1 and H$\beta$/H$\alpha$ $=$ 2.86. We convert $R_V$ from 3.1 to 4.05 because of the adaptation to the Pa$\alpha$ wavelength. If $R_V$ remains at 3.1, the corrected Pa$\alpha$ intensity becomes unrealistic for some pixels. We extrapolate $R_V$ from 3.1 to 4.05 using the following equation,

$$\begin{equation}
\mbox{$E (B-V)$$_{R\mathrm{v}=3.1}$}\ = \left (\frac{\mbox{A$_{V,R\mathrm{v}=3.1}$}}{\mbox{$\mathrm{\mathrm{\kappa'}}$ ($V$)}\ \times 0.44}\right),
\label{eq:}
\end{equation}$$ where $\mbox{$E (B-V)$$_{R\mathrm{v}=3.1}$}$ is the color excess and $\mathrm{\mathrm{\kappa'}} (V)$ is obtained from Equations 2 and 3 of (cite: Calzetti00). With the following equations, we get an $A_V$ map for a different $R_V$,

$$\begin{eqnarray}
\lefteqn{ E(\beta-\alpha) = } \nonumber \\
&& \left (\frac{\mathrm{\kappa'}(\beta)_{R\mathrm{v}=3.1} - \mathrm{\kappa'}(\alpha)_{R\mathrm{v}=3.1}}{\mathrm{\kappa'}(B)_{R\mathrm{v}=3.1} - \mathrm{\kappa'}(V)_{R\mathrm{v}=3.1}} \right)\times E(B-V)_{R\mathrm{v}=3.1}, \nonumber \\
\lefteqn{ E(B-V)_{R\mathrm{v}=4.05} = } \nonumber \\
&& \left (\frac{\mathrm{\kappa'}(B)_{R\mathrm{v}=4.05} - \mathrm{\kappa'}(V)_{R\mathrm{v}=4.05}}{\mathrm{\kappa'}(\beta)_{R\mathrm{v}=4.05} - \mathrm{\kappa'}(\alpha)_{R\mathrm{v}=4.05}}\right) \times E(\beta-\alpha), \nonumber \\
\lefteqn{ A_{V,R\mathrm{v}=4.05} = } \nonumber \\
&& (\mathrm{\kappa'}(V)_{R\mathrm{v}=4.05} \times 0.44) \times E(B-V)_{R\mathrm{v}=4.05}.
\end{eqnarray}$$ We refer the readers to (cite: Calzetti00) for more details. We derive A$_{\lambda 1.875}$/$A_V$ of 0.145 by extrapolating $A_V$ from $R_V$=3.1 to $R_V$=4.05. The accuracy of this value is confirmed by its agreement with the value derived by (cite: Piqueras13), using the observed central flux in the $V$-band.

# Negligible contamination of DIG for free-free continuum

Here, we demonstrate whether the free-free continuum significantly contains the DIG components in NGC 1068. First, we calculate the expected emission measure of the DIG ($EM_{\rm DIG}$) based on the Pa$\alpha$ luminosity of the DIG components,

$$\begin{equation}
   \left(\frac{L_{\mathrm{DIG}}}{\mathrm{erg\ s^{-1}}}\right) = \left(\frac{\epsilon}{{\mathrm{erg\ s^{-1}\ cm^{-3}\ /n_en_p}}}\right)\left(\frac{EM_{{\mathrm{DIG}}}}{\mathrm{cm^{-3}}}\right),
   \label{eq:Ldig}
\end{equation}$$ where $\epsilon$ comes from Equation [\[eq:eps\]](#eq:eps). Then, we measure the expected flux of the free-free continuum based on the Pa$\alpha$-based $EM_{\rm DIG}$. The equation is,

$$\begin{equation}
I^{\rm ff}_{\nu} = \frac{2\nu^2}{c^2}k \mbox{$T_{\rm e}$}\tau^{\rm ff}_\nu,
\end{equation}$$ where $I^{\rm ff}_{\nu}$ is the intensity and $\tau^{\rm ff}_\nu$ is the optical depth of free-free continuum which is given by,

$$\begin{equation}
\tau^{\rm ff}_\nu = 8.235 \times 10^{-2} \mbox{$T_{\rm e}$}^{-1.35} \left(\frac{\nu}{\rm GHz}\right)^{-2.1}\left(\frac{EM_{\rm DIG}}{\mathrm{cm^{-6}\ pc}}\right)Z^2,
\end{equation}$$

where $Z$ is the ionic charge. The typical $T_{\rm e}$ for the DIG in the Milky Way is estimated to be 6000–10000 K, the electron and proton density($n_{\rm e}$, $n_{\rm p}$) to be $\simeq$0.05 $\mathrm{cm^{-3}}$, and the scale height to be $\simeq$1000 $\mathrm{pc}$ (see (cite: Haffner09) for more details). Based on the calculation described above, the expected peak DIG flux at 100 GHz is 0.01 $\mu$Jy beam$^{-1}$ which is well below the image RMS of our ALMA 100 GHz continuum map (0.1 mJy beam$^{-1}$).

# DIG correction to the Pa$\alpha$

We use the \[S II\]/H$\alpha$ method originally proposed by (cite: Blanc09). This method has been improved to adapt external galaxies by several authors (cite: Kaplan16; Kreckel16; Poetrodjojo19). We use the prescription proposed in (cite: Kaplan16) and (cite: Kreckel16). In this method, the data showing the strong intensity of H$\alpha$ emission are defined as pure H II regions, and \[S II\]/H$\alpha$ line ratio is used to distinguish low-ionization gas and H II region. Figure [16](#fig:siiha_fig21) shows a plot necessary to calculate the fraction of DIG at each pixel. The $C_{\rm{H\,II}}$ is the fraction classified as H II region in each data and this is calculated by defining the threshold of H II region and DIG in the \[S II\]/H$\alpha$ ratio: $$\begin{equation}
   \left(\frac{\mbox{\rm [S II]}}{\mbox{H$\alpha$}}\right)_{\rm OBS} = C_{\rm{H\,II}} \left(\frac{\mbox{\rm [S II]}}{\mbox{H$\alpha$}}\right)_{\rm{H\,II}} + C_{\rm{DIG}} \left(\frac{\mbox{\rm [S II]}}{\mbox{H$\alpha$}}\right)_{\rm{DIG}},
   \label{eq:SIIHa1}
\end{equation}$$ Here, $C_{\rm{H\,II}}$ is the fraction of H$\alpha$ flux arising from the H II region in each hexagon and $C_{\rm{H\,II}}  = 1 - C_{\rm{DIG}}.$ The minimum of \[S II\]/H$\alpha$ is used as the threshold for H II regions, and the median of \[S II\]/H$\alpha$ is the threshold of DIG for a single hexagon on the map (cite: Kreckel16).

The black curve in Figure [16](#fig:siiha_fig21) shows the minimum of $C_{\rm{H\,II}}$ for the flux of H$\alpha$. The function of the black curve is defined following: $$\begin{equation}
   \left(\frac{\mbox{\rm [S II]}}{\mbox{H$\alpha$}}\right) = 1 - \left(\frac{f_0}{f(\mbox{H$\alpha$})}\right)^{\beta},
   \label{eq:SIIHa2}
\end{equation}$$ Here, *f*$_0$ is the minimum of the flux of H$\alpha$that can exit H II region, f(H$\alpha$) is the H$\alpha$ flux, and the exponent $\beta$ is used to accommodate changes in the surface brightness of DIG. The minimum value of H$\alpha$ intensity ($f_0$) at which a H II region can exist in each pixel defined by (cite: Kaplan16) was 3.25 $\times$ 10$^{-15}$ erg s$^{-1}$ cm$^{-1}$. The data points falling into the blue area of Figure [16](#fig:siiha_fig21) are known to be “pure DIG" (see (cite: Kreckel16) and (cite: Kaplan16) for more details).

![](image/rSIIHa.png)

# $\Sigma_{\mathrm{SFR}}$ distribution in NGC 1068

The distribution of $\Sigma_{\mathrm{SFR}}$ in each hexagon is nearly log-normal (Figure [14](#Fig:SFRh_fig14)). Note that this does not imply a sampling bias. We confirmed this by comparing the histograms of $L_{\rm RL}$ in the pixel bases and hexagon bases as shown in Figure [17](#fig:lognormal_fig25) and Figure [14](#Fig:SFRh_fig14) reflect the original distribution of the $\Sigma_{\mathrm{SFR}}$ ($\propto\, L_{\rm RL}$ ) histogram.

In addition, we explain below why hexagonal sampling increases the proportion of bins exceeding 3$\sigma$ in Figure [17](#fig:lognormal_fig25). The RMS value for the hexagon, $\sigma_{\text{hex}}$, can then be derived through the principle of error propagation as: $$\sigma_{\text{hex}} = \sqrt{N} \times \sigma_{\text{pixel}}$$ Here, the number of data is N and the RMS value for the pixel is $\sigma_{\text{pixel}}$. Given that a hexagon contains multiple pixels, the signal-to-noise ratio within each hexagon is reduced. Consequently, post-sampling into hexagons, an increase appears in the fraction of bins that exhibit statistically significant signals (exceeding 3 $\sigma$). Therefore, by employing hexagonal sampling, we leverage the benefit of effectively enhancing the signal-to-noise ratio.

![](image/lognormal_fig25.png)

# Spatial distribution of electron temperature

The reason for assuming a single $T_{\rm e}$ to derive SFR in Section [3.4.1](#sec:method_result:TeDerive:TeGuess) is to take advantage of the number of data points for the fitting. Here we examine whether the other manner works, i.e., deriving $T_{\rm e}$ at each hexagon by using a smaller number of data points. We use the same fitting method described in Section [3.4.1](#sec:method_result:TeDerive:TeGuess), but we perform the fitting for each hexagon with at least 6 surrounding hexagons. This method allows us to create an $T_{\rm e}$ map. This effectively degrades the spatial resolution by a factor of two compared to the original maps with 55 pc resolution. The detailed procedure for the fitting is as follows: (1) we select hexagons with at least 6 adjacent hexagons detected in both Pa$\alpha$ and free-free continuum, (2) the fitting is performed for the 6 or 7 data points to derive a single $T_{\rm e}$, and (3) the obtained $T_{\rm e}$ is assigned to the central hexagon (i.e., the neighboring hexagons assist the fitting).

The map and histogram of $T_{\rm e}$ based on this method are shown in Figure [18](#fig:Tem_fig16) and Figure [19](#fig:Teh_fig17), respectively. In the $T_{\rm e}$ map, hexagons greater than three times the fitting error are displayed. $T_{\rm e}$ of the typical H II region is around 5,000 and 14,000 K (cite: Draine11). However, as shown in Figures [18](#fig:Tem_fig16) and [19](#fig:Teh_fig17), the $T_{\rm e}$ distribution based on our method shows a wider range above 15,000 K or below 4,000 K. These extreme values are theoretically difficult to explain. This may be due to the smaller number of available data points for the fitting at each position. This result affirms the advantage of estimating a single $T_{\rm e}$ in the starburst ring.

![](image/Temap.png)

![](image/Tehist.png)

natexlab

(ref: Anand2021) Anand, G. S., Lee, J. C., Van Dyk, S. D., et al. 2021, MNRAS, 501, 3621, doi: [`10.1093/mnras/staa3668`](http://doi.org/10.1093/mnras/staa3668)

(ref: Armus09) Armus, L., Mazzarella, J. M., Evans, A. S., et al. 2009, PASP, 121, 559, doi: [`10.1086/600092`](http://doi.org/10.1086/600092)

(ref: Astropy13) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33, doi: [`10.1051/0004-6361/201322068`](http://doi.org/10.1051/0004-6361/201322068)

(ref: Astropy18) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123, doi: [`10.3847/1538-3881/aabc4f`](http://doi.org/10.3847/1538-3881/aabc4f)

(ref: Astropy22) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167, doi: [`10.3847/1538-4357/ac7c74`](http://doi.org/10.3847/1538-4357/ac7c74)

(ref: Bacon10) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508, doi: [`10.1117/12.856027`](http://doi.org/10.1117/12.856027)

(ref: BakerandMenzel38) Baker, J. G., & Menzel, D. H. 1938, ApJ, 88, 52, doi: [`10.1086/143959`](http://doi.org/10.1086/143959)

(ref: Baldwin81) Baldwin, J. A., Phillips, M. M., & Terlevich, R. 1981, PASP, 93, 5, doi: [`10.1086/130766`](http://doi.org/10.1086/130766)

(ref: Balser24) Balser, D. S., & Wenger, T. V. 2024, ApJ, 964, 47, doi: [`10.3847/1538-4357/ad2458`](http://doi.org/10.3847/1538-4357/ad2458)

(ref: Belfiore22) Belfiore, F., Santoro, F., Groves, B., et al. 2022, A&A, 659, A26, doi: [`10.1051/0004-6361/202141859`](http://doi.org/10.1051/0004-6361/202141859)

(ref: Bendo15) Bendo, G., Beswick, R., D’Cruze, M., et al. 2015, MNRAS, 450, L80, doi: [`10.1093/mnrasl/slv053`](http://doi.org/10.1093/mnrasl/slv053)

(ref: Bendo16) Bendo, G., Henkel, C., D’Cruze, M., et al. 2016, MNRAS, 463, 252, doi: [`10.1093/mnras/stw1659`](http://doi.org/10.1093/mnras/stw1659)

(ref: Birch2007) Birch, C. P., Oom, S. P., & Beecham, J. A. 2007, Ecological Modelling, 206, 347, doi: [`https://doi.org/10.1016/j.ecolmodel.2007.03.041`](http://doi.org/https://doi.org/10.1016/j.ecolmodel.2007.03.041)

(ref: Blanc09) Blanc, G. A., Heiderman, A., Gebhardt, K., Evans, Neal J., I., & Adams, J. 2009, ApJ, 704, 842, doi: [`10.1088/0004-637X/704/1/842`](http://doi.org/10.1088/0004-637X/704/1/842)

(ref: Calzetti08) Calzetti, D. 2008, in Astronomical Society of the Pacific Conference Series, Vol. 390, Pathways Through an Eclectic Universe, ed. J. H. Knapen, T. J. Mahoney, & A. Vazdekis, 121, doi: [`10.48550/arXiv.0707.0467`](http://doi.org/10.48550/arXiv.0707.0467)

(ref: Calzetti13) Calzetti, D. 2013, in Secular Evolution of Galaxies, ed. J. Falcón-Barroso & J. H. Knapen, 419, doi: [`10.48550/arXiv.1208.2997`](http://doi.org/10.48550/arXiv.1208.2997)

(ref: Calzetti00) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682, doi: [`10.1086/308692`](http://doi.org/10.1086/308692)

(ref: CASATeam22) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501, doi: [`10.1088/1538-3873/ac9642`](http://doi.org/10.1088/1538-3873/ac9642)

(ref: Chiappini97) Chiappini, C., Matteucci, F., & Gratton, R. 1997, ApJ, 477, 765, doi: [`10.1086/303726`](http://doi.org/10.1086/303726)

(ref: Condon92) Condon, J. J. 1992, ARA&A, 30, 575, doi: [`10.1146/annurev.aa.30.090192.003043`](http://doi.org/10.1146/annurev.aa.30.090192.003043)

(ref: Crocker13) Crocker, A. F., Calzetti, D., Thilker, D. A., et al. 2013, ApJ, 762, 79, doi: [`10.1088/0004-637X/762/2/79`](http://doi.org/10.1088/0004-637X/762/2/79)

(ref: Curti20) Curti, M., Mannucci, F., Cresci, G., & Maiolino, R. 2020, MNRAS, 491, 944, doi: [`10.1093/mnras/stz2910`](http://doi.org/10.1093/mnras/stz2910)

(ref: Das06) Das, V., Crenshaw, D. M., Kraemer, S. B., & Deo, R. P. 2006, AJ, 132, 620, doi: [`10.1086/504899`](http://doi.org/10.1086/504899)

(ref: deVaucouleur10) de Vaucouleurs, G., de Vaucouleurs, A., Corwin, Herold G., J., et al. 1991, Third Reference Catalogue of Bright Galaxies

(ref: Brok21) den Brok, J. S., Chatzigiannakis, D., Bigiel, F., et al. 2021, MNRAS, 504, 3221, doi: [`10.1093/mnras/stab859`](http://doi.org/10.1093/mnras/stab859)

(ref: Draine11) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: Earl23) Earl, N., Tollerud, E., O’Steen, R., et al. 2023, astropy/specutils: v1.12.0, v1.12.0, Zenodo, doi: [`10.5281/zenodo.10016569`](http://doi.org/10.5281/zenodo.10016569)

(ref: Fu09) Fu, J., Hou, J. L., Yin, J., & Chang, R. X. 2009, ApJ, 696, 668, doi: [`10.1088/0004-637X/696/1/668`](http://doi.org/10.1088/0004-637X/696/1/668)

(ref: Gallimore04) Gallimore, J. F., Baum, S. A., & O’Dea, C. P. 2004, ApJ, 613, 794, doi: [`10.1086/423167`](http://doi.org/10.1086/423167)

(ref: Garcia-Burrillo14) Garcı́a-Burillo, S., Combes, F., Usero, A., et al. 2014, A&A, 567, A125, doi: [`10.1051/0004-6361/201423843`](http://doi.org/10.1051/0004-6361/201423843)

(ref: Garcia-Burillo2019) Garcı́a-Burillo, S., Combes, F., Ramos Almeida, C., et al. 2019, A&A, 632, A61, doi: [`10.1051/0004-6361/201936606`](http://doi.org/10.1051/0004-6361/201936606)

(ref: Ginsburg19) Ginsburg, A., Koch, E., Robitaille, T., et al. 2019, radio-astro-tools/spectral-cube: v0.4.4, v0.4.4, Zenodo, doi: [`10.5281/zenodo.2573901`](http://doi.org/10.5281/zenodo.2573901)

(ref: Haffner09) Haffner, L., Dettmar, R. J., Beckman, J., et al. 2009, Reviews of Modern Physics, 81, 969, doi: [`10.1103/RevModPhys.81.969`](http://doi.org/10.1103/RevModPhys.81.969)

(ref: Harris20) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357, doi: [`10.1038/s41586-020-2649-2`](http://doi.org/10.1038/s41586-020-2649-2)

(ref: Herrera20) Herrera, C. N., Pety, J., Hughes, A., et al. 2020, A&A, 634, A121, doi: [`10.1051/0004-6361/201936060`](http://doi.org/10.1051/0004-6361/201936060)

(ref: Hunter23) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, PASP, 135, 074501, doi: [`10.1088/1538-3873/ace216`](http://doi.org/10.1088/1538-3873/ace216)

(ref: Jones22) Jones, G. T., Stanway, E. R., & Carnall, A. C. 2022, MNRAS, 514, 5706, doi: [`10.1093/mnras/stac1667`](http://doi.org/10.1093/mnras/stac1667)

(ref: Kaplan16) Kaplan, K. F., Jogee, S., Kewley, L., et al. 2016, MNRAS, 462, 1642, doi: [`10.1093/mnras/stw1422`](http://doi.org/10.1093/mnras/stw1422)

(ref: Kawana22) Kawana, Y., Saito, T., Okumura, S. K., et al. 2022, ApJ, 929, 100, doi: [`10.3847/1538-4357/ac5f41`](http://doi.org/10.3847/1538-4357/ac5f41)

(ref: KennicuttEvans12) Kennicutt, R. C., & Evans, N. J. 2012, ARA&A, 50, 531, doi: [`10.1146/annurev-astro-081811-125610`](http://doi.org/10.1146/annurev-astro-081811-125610)

(ref: Kewley01) Kewley, L. J., Dopita, M. A., Sutherland, R. S., Heisler, C. A., & Trevena, J. 2001, ApJ, 556, 121, doi: [`10.1086/321545`](http://doi.org/10.1086/321545)

(ref: Kreckel16) Kreckel, K., Blanc, G., Schinnerer, E., et al. 2016, ApJ, 827, 103, doi: [`10.3847/0004-637X/827/2/103`](http://doi.org/10.3847/0004-637X/827/2/103)

(ref: Kroupa01) Kroupa, P. 2001, MNRAS, 322, 231, doi: [`10.1046/j.1365-8711.2001.04022.x`](http://doi.org/10.1046/j.1365-8711.2001.04022.x)

(ref: Lacerda18) Lacerda, E. A. D., Cid Fernandes, R., Couto, G. S., et al. 2018, MNRAS, 474, 3727, doi: [`10.1093/mnras/stx3022`](http://doi.org/10.1093/mnras/stx3022)

(ref: Leitherer99) Leitherer, C., Schaerer, D., Goldader, J. D., et al. 1999, ApJS, 123, 3, doi: [`10.1086/313233`](http://doi.org/10.1086/313233)

(ref: Leroy19) Leroy, A. K., Sandstrom, K. M., Lang, D., et al. 2019, ApJS, 244, 24, doi: [`10.3847/1538-4365/ab3925`](http://doi.org/10.3847/1538-4365/ab3925)

(ref: Leroy21a) Leroy, A. K., Schinnerer, E., Hughes, A., et al. 2021, ApJS, 257, 43, doi: [`10.3847/1538-4365/ac17f3`](http://doi.org/10.3847/1538-4365/ac17f3)

(ref: MadauDickinson14) Madau, P., & Dickinson, M. 2014, ARA&A, 52, 415, doi: [`10.1146/annurev-astro-081811-125615`](http://doi.org/10.1146/annurev-astro-081811-125615)

(ref: Madsen06) Madsen, G., Reynolds, R., & Haffner, L. 2006, ApJ, 652, 401, doi: [`10.1086/508441`](http://doi.org/10.1086/508441)

(ref: Maeda23) Maeda, F., Egusa, F., Ohta, K., Fujimoto, Y., & Habe, A. 2023, ApJ, 943, 7, doi: [`10.3847/1538-4357/aca664`](http://doi.org/10.3847/1538-4357/aca664)

(ref: Marchesini09) Marchesini, D., van Dokkum, P. G., Förster Schreiber, N. M., et al. 2009, ApJ, 701, 1765, doi: [`10.1088/0004-637X/701/2/1765`](http://doi.org/10.1088/0004-637X/701/2/1765)

(ref: Matteucci01) Matteucci, F. 2001, The chemical evolution of the Galaxy, Vol. 253, doi: [`10.1007/978-94-010-0967-6`](http://doi.org/10.1007/978-94-010-0967-6)

(ref: Michiyama22) Michiyama, T., Inoue, Y., Doi, A., & Khangulyan, D. 2022, ApJL, 936, L1, doi: [`10.3847/2041-8213/ac8935`](http://doi.org/10.3847/2041-8213/ac8935)

(ref: Michiyama20) Michiyama, T., Iono, D., Nakanishi, K., et al. 2020, ApJ, 895, 85, doi: [`10.3847/1538-4357/ab88a5`](http://doi.org/10.3847/1538-4357/ab88a5)

(ref: MIlls21) Mills, E. A. C., Gorski, M., Emig, K. L., et al. 2021, ApJ, 919, 105, doi: [`10.3847/1538-4357/ac0fe8`](http://doi.org/10.3847/1538-4357/ac0fe8)

(ref: Mingozzi19) Mingozzi, M., Cresci, G., Venturi, G., et al. 2019, A&A, 622, A146, doi: [`10.1051/0004-6361/201834372`](http://doi.org/10.1051/0004-6361/201834372)

(ref: Momose2013) Momose, R., Koda, J., Kennicutt, Robert C., J., et al. 2013, ApJL, 772, L13, doi: [`10.1088/2041-8205/772/1/L13`](http://doi.org/10.1088/2041-8205/772/1/L13)

(ref: Morokuma17) Morokuma-Matsui, K., & Muraoka, K. 2017, ApJ, 837, 137, doi: [`10.3847/1538-4357/aa6115`](http://doi.org/10.3847/1538-4357/aa6115)

(ref: Murphy11) Murphy, E., Condon, J., Schinnerer, E., et al. 2011, ApJ, 737, 67, doi: [`10.1088/0004-637X/737/2/67`](http://doi.org/10.1088/0004-637X/737/2/67)

(ref: Nakajima23) Nakajima, T., Takano, S., Tosaki, T., et al. 2023, ApJ, 955, 27, doi: [`10.3847/1538-4357/ace4c7`](http://doi.org/10.3847/1538-4357/ace4c7)

(ref: Peeters04) Peeters, E., Spoon, H. W. W., & Tielens, A. G. G. M. 2004, ApJ, 613, 986, doi: [`10.1086/423237`](http://doi.org/10.1086/423237)

(ref: Pilyugin05) Pilyugin, L. S., & Thuan, T. X. 2005, ApJ, 631, 231, doi: [`10.1086/432408`](http://doi.org/10.1086/432408)

(ref: Piqueras13) Piqueras López, J., Colina, L., Arribas, S., & Alonso-Herrero, A. 2013, A&A, 553, A85, doi: [`10.1051/0004-6361/201220991`](http://doi.org/10.1051/0004-6361/201220991)

(ref: Planesas89) Planesas, P., Gomez-Gonzalez, J., & Martin-Pintado, J. 1989, A&A, 216, 1

(ref: Planesas91) Planesas, P., Scoville, N., & Myers, S. T. 1991, ApJ, 369, 364, doi: [`10.1086/169766`](http://doi.org/10.1086/169766)

(ref: Poetrodjojo19) Poetrodjojo, H., D’Agostino, J. J., Groves, B., et al. 2019, MNRAS, 487, 79, doi: [`10.1093/mnras/stz1241`](http://doi.org/10.1093/mnras/stz1241)

(ref: Rau11) Rau, U., & Cornwell, T. J. 2011, A&A, 532, A71, doi: [`10.1051/0004-6361/201117104`](http://doi.org/10.1051/0004-6361/201117104)

(ref: Saito15) Saito, T., Iono, D., Yun, M. S., et al. 2015, ApJ, 803, 60, doi: [`10.1088/0004-637X/803/2/60`](http://doi.org/10.1088/0004-637X/803/2/60)

(ref: Saito16) Saito, T., Iono, D., Xu, C. K., et al. 2016, PASJ, 68, 20, doi: [`10.1093/pasj/psv136`](http://doi.org/10.1093/pasj/psv136)

(ref: Saito22a) Saito, T., Takano, S., Harada, N., et al. 2022a, ApJL, 927, L32, doi: [`10.3847/2041-8213/ac59ae`](http://doi.org/10.3847/2041-8213/ac59ae)

(ref: Saito22b) —. 2022b, ApJ, 935, 155, doi: [`10.3847/1538-4357/ac80ff`](http://doi.org/10.3847/1538-4357/ac80ff)

(ref: Salpeter55) Salpeter, E. E. 1955, ApJ, 121, 161, doi: [`10.1086/145971`](http://doi.org/10.1086/145971)

(ref: Sanchez-Garcia22) Sánchez-Garcı́a, M., Garcı́a-Burillo, S., Pereira-Santaella, M., et al. 2022, A&A, 660, A83, doi: [`10.1051/0004-6361/202142396`](http://doi.org/10.1051/0004-6361/202142396)

(ref: Sanchez-Menguiano16) Sánchez-Menguiano, L., Sánchez, S. F., Pérez, I., et al. 2016, A&A, 587, A70, doi: [`10.1051/0004-6361/201527450`](http://doi.org/10.1051/0004-6361/201527450)

(ref: Schinnerer00) Schinnerer, E., Eckart, A., Tacconi, L., Genzel, R., & Downes, D. 2000, ApJ, 533, 850, doi: [`10.1086/308702`](http://doi.org/10.1086/308702)

(ref: Shaver83) Shaver, P., McGee, R., Newton, L., Danks, A., & Pottasch, S. 1983, MNRAS, 204, 53, doi: [`10.1093/mnras/204.1.53`](http://doi.org/10.1093/mnras/204.1.53)

(ref: Solomon87) Solomon, P. M., Rivolo, A. R., Barrett, J., & Yahil, A. 1987, ApJ, 319, 730, doi: [`10.1086/165493`](http://doi.org/10.1086/165493)

(ref: Solomon05) Solomon, P. M., & Vanden Bout, P. A. 2005, ARA&A, 43, 677, doi: [`10.1146/annurev.astro.43.051804.102221`](http://doi.org/10.1146/annurev.astro.43.051804.102221)

(ref: Stanghellini15) Stanghellini, L., Magrini, L., & Casasola, V. 2015, ApJ, 812, 39, doi: [`10.1088/0004-637X/812/1/39`](http://doi.org/10.1088/0004-637X/812/1/39)

(ref: StoreyandHummer95) Storey, P., & Hummer, D. 1995, MNRAS, 272, 41, doi: [`10.1093/mnras/272.1.41`](http://doi.org/10.1093/mnras/272.1.41)

(ref: Sun18) Sun, J., Leroy, A. K., Schruba, A., et al. 2018, ApJ, 860, 172, doi: [`10.3847/1538-4357/aac326`](http://doi.org/10.3847/1538-4357/aac326)

(ref: Tateuchi13) Tateuchi, K., Motohara, K., Konishi, M., et al. 2013, in Astronomical Society of the Pacific Conference Series, Vol. 476, New Trends in Radio Astronomy in the ALMA Era: The 30th Anniversary of Nobeyama Radio Observatory, ed. R. Kawabe, N. Kuno, & S. Yamamoto, 301

(ref: Tomicic17) Tomičić, N., Kreckel, K., Groves, B., et al. 2017, ApJ, 844, 155, doi: [`10.3847/1538-4357/aa7b30`](http://doi.org/10.3847/1538-4357/aa7b30)

(ref: Tomicic21) Tomičić, N., Vulcani, B., Poggianti, B. M., et al. 2021, ApJ, 922, 131, doi: [`10.3847/1538-4357/ac230e`](http://doi.org/10.3847/1538-4357/ac230e)

(ref: Tosaki17) Tosaki, T., Kohno, K., Harada, N., et al. 2017, PASJ, 69, 18, doi: [`10.1093/pasj/psw122`](http://doi.org/10.1093/pasj/psw122)

(ref: Tsai12) Tsai, M., Hwang, C.-Y., Matsushita, S., Baker, A. J., & Espada, D. 2012, ApJ, 746, 129, doi: [`10.1088/0004-637X/746/2/129`](http://doi.org/10.1088/0004-637X/746/2/129)

(ref: Virtanen20) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261, doi: [`10.1038/s41592-019-0686-2`](http://doi.org/10.1038/s41592-019-0686-2)

(ref: Wu05) Wu, H., Cao, C., Hao, C.-N., et al. 2005, ApJL, 632, L79, doi: [`10.1086/497961`](http://doi.org/10.1086/497961)

</paper>

Write the methods card for this paper.