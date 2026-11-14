# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024PASJ...76...54L\sonnetcc\reply.txt

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
 "bibcode": "2024PASJ...76...54L",
 "title": "Tentative detection of cyanoformamide NCCONH<SUB>2</SUB> in space",
 "year": 2024,
 "journal": "Publications of the Astronomical Society of Japan",
 "first_author": "Li, Juan",
 "n_authors": 15,
 "arxiv_id": "2311.01721",
 "doi": "10.1093/pasj/psad079",
 "alma_projects_linked_by_archive": [
  "2016.1.00243.S"
 ]
}
```

Paper text:
<paper>
# Tentative detection of cyanoformamide NCCONH$_2$ in space

## Abstract

The peptide-like molecules, cyanoformamide (NCCONH$_2$), is the cyano (CN) derivative of formamide (NH$_2$CHO). It is known to play a role in the synthesis of nucleic acid precursors under prebiotic conditions. In this paper, we present a tentative detection of NCCONH$_2$ in the interstellar medium (ISM) with the Atacama Large Millimeter/submillimeter Array (ALMA) archive data. Ten unblended lines of NCCONH$_2$ were seen around 3$\sigma$ noise levels toward Sagittarius B2(N1E), a position that is slightly offset from the continuum peak. The column density of NCCONH$_2$ was estimated to be 2.4$\times 10^{15}$cm$^{-2}$, and the fractional abundance of NCCONH$_2$ toward Sgr B2(N1E) was $6.9\times10^{-10}$. The abundance ratio between NCCONH$_2$ and NH$_2$CHO is estimated to be $\sim$0.01. We also searched for other peptide-like molecules toward Sgr B2(N1E). The abundances of NH$_2$CHO, CH$_3$NCO and CH$_3$NHCHO toward Sgr B2(N1E) were about one tenth of those toward Sgr B2(N1S), while the abundances of CH$_3$CONH$_2$ was only one twentieth of that toward Sgr B2(N1S).

Department of Radio Science and Technology, Shanghai Astronomical observatory, 80 Nandan RD, Shanghai 200030, China Key Laboratory of Radio Astronomy, Chinese Academy of Sciences, China Research Center for Intelligent Computing Platforms, Zhejiang Laboratory, Hangzhou 311100, PR China Department of Chemistry, Eastern Kentucky University, Richmond, KY 40475, USA Guangxi key Laboratory for Relativistic Astrophysics, Department of Physics, Guangxi University, Nanning 530004, PR China Xinjiang Astronomical Observatory, Chinese Academy of Sciences, 150 Science 1-Street, Urumqi 830011, PR China School of Chemistry and Chemical Engineering, Chongqing University, Daxuecheng South Rd. 55, 401331, Chongqing, PR China Hamburger Sternwarte, Universität Hamburg, Gojenbergsweg 112, 21029, Hamburg, Germany Department of Astronomy, University of Michigan, Ann Arbor, MI 48109, USA Max Planck Institute for Astronomy, Königstuhl 17, D-69117 Heidelberg, Germany Purple Mountain Observatory, Chinese Academy of Sciences, Nanjing 210034, PR China University of Chinese Academy of Sciences, 19A Yuquanlu, Beijing 100049, PR China School of Astronomy and Space Science, Nanjing University, Nanjing 210093, China

# Introduction

Peptide bonds, -NHCO-, are bridges that connect amino acids to form proteins, which are the basis of life on Earth (cite: Kaiser13). Studies of molecules with peptide-like bonds are thus important for our understanding of the origin of life (cite: Halfen11; Belloche17). A number of peptide-like molecules have been detected in space. Formamide (NH$_2$CHO), which is a potential precursor of various organic compounds essential to life (cite: Lopez2019), was the first peptide-like molecule detected in space. (cite: Rubin71) reported the detection of formamide in Sagittarius B2 (hereafter Sgr B2) with the 140-foot telescope of the National Radio Astronomy Observatory (NRAO). After that, formamide was detected in a number of massive star-forming regions, including Orion KL (cite: Turner1989; Turner1991), W3(H$_2$O) (cite: Bisschop2007), and W51e1/e2 (cite: Suzuki2018) and so on. It was also found in some solar-mass protostellar cores, including the well-studied protobinary IRAS 16293-1622 (cite: Coutens16), the protostellar shock region L1157-B1 (cite: Mendoza14) and so on. Formamide was also detected in the gas and ices of some comets (cite: Altwegg17). The next peptide-like molecule, acetamide (CH$_3$CONH$_2$), was also first detected toward Sgr B2(N) (cite: Hollis06; Halfen11), and later detected in more high-mass star forming regions (cite: Ligterink20; Colzi21). N-methylformamide (CH$_3$NHCHO), the isomer of acetamide, was detected towards Sgr B2(n1S), NGC 6334I, G31.41+0.31 and so on (cite: Belloche17; Belloche19; Ligterink20; Colzi21; Zeng23). Urea (NH$_2$C(O)NH$_2$), were first identified toward Sgr B2(N) with the ALMA (cite: Belloche17; Belloche19), and later detected in molecular cloud G+0.693-0.027 in the Sgr B2 complex (cite: Jimenez20). In addition, propionamide C$_2$H$_5$CONH$_2$ was tentatively detected toward Sgr B2(N1E) (cite: Li21). These observations suggest that peptide-like molecules might be widespread in space.

The organic species cyanoformamide (NCCONH$_2$) is the cyano (CN) derivative of formamide (NH$_2$CHO), a known interstellar molecule with a role in the synthesis of nucleic acid precursors under prebiotic conditions (cite: Winnewisser05). Cyanoformamide could form from the reaction between CN and formamide (cite: Winnewisser05). As both CN and formamide are observed to be abundant in the ISM, cyanoformamide is expected to be detectable in the ISM (cite: Winnewisser05). At room temperature and normal terrestrial pressure, this molecule is rather unstable. The microwave and millimeter-wave spectrum of the gas-phase species was not studied until 2005 (cite: Christiansen05; Winnewisser05). Recently, (cite: Colzi21) searched cyanoformamide toward hot core G31.41+0.31 but got a negative result.

Sgr B2, the giant molecular cloud located in the Galactic central region, is the most massive star-forming region in the Galaxy. It has long been regarded as the best hunting grounds for complex organic molecules (COMs) due to the extraordinary molecular richness (cite: Belloche13; Li17; Li20). Most O-bearing COMs were first detected toward Sgr B2 (cite: McGuire18; McGuire22), such as the branched molecule i-C$_3$H$_7$CN (cite: Belloche14) and the chiral molecule CH$_3$CHCH$_2$O (cite: McGuire16). There are two main sites of star formation regions in Sgr B2, namely Sgr B2(N) and Sgr B2(M), both of which host several dense, compact, hot cores that are rich in COMs (cite: Bonfand17). Recently, (cite: Li21) found evidence for the possible presence of C$_2$H$_5$CONH$_2$, the largest peptide-like molecule, toward Sgr B2(N1E), suggesting that peptide-like molecules are abundant in this region.

In this paper, we present a tentative detection of NCCONH$_2$ toward Sgr B2(N1E). Section 2 introduces the observations and data reduction. Section 3 presents the observational results. Section 4 discusses the observing results and possible formation mechanisms of NCCONH$_2$. The summary of the work is presented in Section 5.

# OBSERVATIONS AND DATA REDUCTION

The data used for this study were acquired from the ALMA Science archive of the ReMoCA survey (Re-exploring Molecular Complexity with ALMA) (cite: Belloche19). The ReMoCA survey was conducted with ALMA during Cycle 4 between 2016 and 2017. Detailed description about the observations is presented in (cite: Belloche19). This is a compete spectral line survey toward Sgr B2(N) covering from 84.1 to 114.4 GHz. Five spectral setups were used in total. The on-source time for each frequency windows range from 47 to 50 minutes. The spectral resolution is 0.488 MHz, which corresponds to a velocity resolution of 1.3-1.7 km s$^{-1}$ across the observing band. The phase center of the observations is $\alpha_{\rm J2000}=17^{\rm h}47^{\rm m}19.87^{\rm s}$, $\delta_{\rm J2000}=-28^\circ 22'16''$, which locates half way between the two main hot molecular hot cores Sgr B2(N1) and N2.

Our data reduction procedure has been introduced in (cite: Li21). The data was calibrated using the standard ALMA data calibration pipeline with the Common Astronomy Software Applications package (CASA). CASA version 4.7.0-1 was used for the first spectral setup, while CASA version 4.7.2 was used for the other four spectral setups. The CASA version 5.6.1-8 was used to image the calibrated data. The quasar J1924-2914 was used to calibrate the bandpass for most of the data, while the quasar J1517-2422 was used to calibrate the bandpass for on execution in the second spectral setup. Quasars J1924-2914 or J1733-1304 were used to derive the absolute flux density scale. The quasar J1744-3116 was used to calibrate the phase and amplitude. The TCLEAN deconvolution algorithm in CASA was used to produce the images. Self-calibration is known to introduce artificial features into imaging by including manually chosen clean components if the structure of the target is complicated (i.e., if it is not a simple point source). Sgr B2(N) has complicated substructures (cite: Bonfand17; Belloche19), therefore, self-calibration will likely introduce artifacts into images, which may affect spectral line identification, especially for the weak lines in our case. We did not perform self-calibration, but still achieved a sufficiently high imaging rms of 0.4 $\sim$ 1 mJy beam$^{-1}$, which is not much higher than that in (cite: Belloche19). Therefore, we believe that this strategy is suitable for our purpose of identification of weak lines.

Because of high number of spectral lines detected toward hot cores in Sgr B2, the determination of baseline is challenging. As pointed out by (cite: sanchez2018), a broad frequency coverage is necessary to ensure the presence of enough line-free frequency intervals to determine the continuum level. They think that a bandwidth of at least 1 GHz is needed. (cite: sanchez2018) have simulated spectra that dominated by emission features, and eight methods were used to determine the continuum level of the spectra. We could see from Table 1 in (cite: sanchez2018) that all the method over-estimated the rms noise levels by 2% to 113%. We could see from Figure 1(b) in (cite: sanchez2018) that the continuum level of the spectra could be better determined with several groups of lowest values in the spectra after masking absorption lines. We first compared with spectra toward HII regions to mask absorption lines, then we chose several groups of lowest values to determine the continuum levels. This could properly determine the continuum levels for spectra dominated by emission lines.

The rms noise levels for the spectra window were determined using the median values of channel maps. We first investigated the rms noise levels in regions without either continuum emission or molecular lines. Then we investigated the rms noise level in regions with strong continuum emission, which are significantly larger than rms noise levels in regions without either molecular lines or continuum emission. The median values of rms noise levels were adopted in this paper.

# RESULTS

## Identification of NCCONH$_2$

Weeds in Gildas package was used for line identification and spectral modeling. The Jet Population Laboratory (JPL) (cite: Pickett98) and the Cologne Database for Molecular Spectroscopy (CDMS) (cite: CDMS2; Endres16) databases were used. The microwave and millimeter-wave spectrum of NCCONH$_2$ was reported by (cite: Christiansen05) and (cite: Winnewisser05). The 3-mm emission of NCCONH$_2$ is modeled assuming LTE conditions with five parameters: column density, temperature, source size, velocity offset, and linewidth. Each spectral window of each observed setup was modeled separately to account for the varying angular resolution, but with a same set of parameters.

Approximately 120 NCCONH$_2$ lines were expected to be seen in the observed frequency ranges. Ten unblended transitions, and 21 partially blended transitions of NCCONH$_2$ were possibly seen toward Sgr B2(N1E) (Figure [1](#f:sgrb2)), which is about 1.5$''$ to the east of the hot core Sgr B2(N1). However, since their signal-to-noise levels are around 3$\sigma$, it is not possible to claim secure detection of NCCONH$_2$ with these data. The large peptide-like molecule, propionamide has been tentatively found to be relatively abundant toward Sgr B2(N1E) (cite: Li21). We also searched for NCCONH$_2$ toward other regions of Sgr B2(N1). However, serious line-blending prevents detection of this molecule toward other directions. The tentatively detected lines are presented in Figures [2](#f:clean) and  [4](#f:partial), and Table [\[tab:freq\]](#tab:freq). Though the remaining $\sim$ 90 lines that match the considered frequency range and noise level threshold are contaminated by those of other species, the observed results do not contradict with the expected intensities. In Figure [2](#f:clean), the black dashed lines show the 3$\sigma$ noise levels adopted in Section 2.

Because of low abundance of NCCONH$_2$ and serious line blending in Sgr B2(N1), all of these unblended lines detected toward Sgr B2(N1E) suffer from line blending toward other directions. Thus we could not get the spatial distribution of NCCONH$_2$ in Sgr B2(N1).

## Search of related molecules toward Sgr B2(N1E)

Some related molecules were also searched toward Sgr B2(N1E). Based on observing results of (cite: Belloche19), we searched for nine relatively clean and strong transitions of CH$_3$NCO v=0 toward Sgr B2(N1E). The CDMS database is used for the identification. Nine clean lines were detected. As nine lines are enough for the detection and modelling of molecule in Sgr B2, we did not search for all the CH$_3$NCO v=0 toward Sgr B2(N1E). The spectra were shown in Figure [5](#f:ch3nco). The intensity of CH$_3$NCO lines toward Sgr B2(N1E) were weaker than those toward Sgr B2(N1S) (See Figure A.6 in (cite: Belloche19)).

Thirteen relatively clean and strong transitions of CH$_3$NHCHO v=0 were searched toward Sgr B2(N1E). The Lille Spectrascopic Database (https://lsd.univ-lille.fr/) is used for the identification. All of these lines were detected. The spectra were shown in Figure [6](#f:ch3nhcho). The intensity of CH$_3$NHCHO lines toward Sgr B2(N1E) were significantly weaker than those toward Sgr B2(N1S) (See Figure A.3 in (cite: Belloche19)).

We also searched for urea (NH$_2$CONH$_2$) toward Sgr B2(N1E). To our knowledge, this molecule was only detected toward Sgr B2(N1S) (cite: Belloche19) and G+0.693-0.027 (cite: Jimenez20), a molecular cloud located in the Sgr B2 complex. It was tentatively detected toward NGC6334I(cite: Ligterink20). Based on observing results of (cite: Belloche19), we searched for four clean and strong NH$_2$CONH$_2$ v=0 transitions toward Sgr B2(N1E). Unfortunately, all of these lines blend seriously with other molecules.

## Column densities of NCCONH$_2$ and related molecules

The column densities of NCCONH$_2$ and related molecules are obtained by eye-fitting the spectra in Weeds. The physical size of the emission region is hard to determine, as the morphology of molecules in Sgr B2(N1) does not simply follow a 2D Gaussian profile (cite: Busch22). The emitting size was assumed to be 2.3$''$, thus the beam filling factor is $\sim$1. With a linewidth measurement of 3.0 km s$^{-1}$, and an assumption of excitation temperature of 150 K (which is very close to what was obtained for molecules toward Sgr B2(N1S) by (cite: Belloche19), the column density and centroid velocity are varied to fit the detected transitions. In this way, a column density of $2.4\times10^{15}$ cm$^{-2}$ was obtained for cyanoformamide (see Table [2](#tab:column)). By adopting the H$_2$ column density of 3.5$\times 10^{24}$ cm$^{-2}$ derived with C$^{18}$O (cite: Li21), the abundance relative to H$_2$ was estimated to be $6.9\times10^{-10}$ for NCCONH$_2$.

We also modeled the emission of CH$_3$NCO and CH$_3$NHCHO toward Sgr B2(N1E) with the same size and excitation temperature (see Table [2](#tab:column)). A column density of 2.4$\times 10^{16}$ cm$^{-2}$ was obtained for CH$_3$NCO. A column density of $2.1\times10^{16}$ cm$^{-2}$ was obtained for CH$_3$NHCHO.

Based on the estimated column density of NCCONH$_2$ toward Sgr B2(N1E), the abundance ratio between NCCONH$_2$ and formamide is found to be $\sim$0.01. This value is consistent with result in (cite: Colzi21). They found that the abundance ratio of NCCONH$_2$ to formamide was lower than 0.05 in G31.41+0.31.

# DISCUSSION

## Comparison of Sgr B2(N1E) and Sgr B2(N1S)

Sgr B2(N1S) is a position that is about 1$''$ to the south of Sgr B2(N1) (see Figure [1](#f:sgrb2), also see Figs. 2 and 3 in (cite: Belloche19)), while Sgr B2(N1E) is about 1.5$''$ to the east of Sgr B2(N1) (see Figure [1](#f:sgrb2), also see Figure 2 in (cite: Li21)). As Sgr B2(N1E) is on the edge of hot core, the excitation temperature and column density should be lower than those toward Sgr B2(N1S).

All the peptide-like molecules detected toward Sgr B2(N1S) were also detected toward Sgr B2(N1E). Table [2](#tab:column) presents the column densities obtained for peptide-like molecules toward Sgr B2(N1E). We compared these results with those of Sgr B2(N1S) presented in (cite: Belloche19). The abundances of NH$_2$CHO, CH$_3$NCO and CH$_3$NHCHO toward Sgr B2(N1E) were about one tenth of those toward Sgr B2(N1S). The abundance ratio of CH$_3$NCO to NH$_2$CHO, was 0.086 toward Sgr B2(N1E), which is in agreement with that of Sgr B2(N1S) (cite: Belloche19). However, the abundances of CH$_3$CONH$_2$ toward Sgr B2(N1E) was only one twentieth of those toward Sgr B2(N1S). A possible explanation for the low abundance of CH$_3$CONH$_2$ and undetection of NH$_2$CONH$_2$ is that the desorption energy required by CH$_3$CONH$_2$ and NH$_2$CONH$_2$ are higher in comparison with NH$_2$CHO, CH$_3$NCO and CH$_3$NHCHO. According to laboratory studies in (cite: Ligterink18), the desorption peak of NH$_2$CONH$_2$ is $\sim$265 K, while the desorption peak of NH$_2$CHO is $\sim$210 K, and the desorption peak of CH$_3$CONH$_2$ is $\sim$219 K. In this case, both CH$_3$CONH$_2$ and NH$_2$CONH$_2$ may not efficiently desorb into gas phase, which is consistent with results present here. It is noted that the derived rotational temperature of NH$_2$CONH$_2$ toward Sg B2(N1S) seems to be higher than other molecules (see Table 5 in (cite: Belloche19)), while the rotational temperature of CH$_3$CONH$_2$ is also higher than NH$_2$CHO, CH$_3$NCO and CH$_3$NHCHO (cite: Belloche19). We did not search for C$_2$H$_5$CONH$_2$ and NCCONH$_2$ toward Sgr B2(N1S) because of serious line blending from other molecules.

## Possible formation mechanism for interstellar cyanoformamide

The formation of NCCONH$_2$ in the ISM is yet unclear. (cite: Winnewisser05) proposed that NCCONH$_2$ could form from the formamide and CN: $$\begin{equation}
CN + NH_2CHO \longrightarrow NCCONH_2 + H.
\end{equation}$$ We ran quantum chemical calculations to further study this reaction. The structures of all the species studied in this work (reactants, intermediates, transition states, and products) were first optimized in the framework of the density functional theory (DFT) employing the M06-2X (cite: zhao08) in conjunction with the 6-311+G(d,p) basis set (cite: ditchfield71), from which rotational constants, harmonic vibrational frequencies, and zero-point energies(ZPEs) were obtained. High-performance single point energies were also calculated at the M06-2X/aug-cc-pVTZ (cite: dunning89) level using the M06-2X structures. All quantum chemical calculations were run with the Gaussian 16 (cite: frisch16).

NH$_2$CHO molecule has several spots that could be attacked by the CN radical: the N, C, and O atoms. Therefore, besides Reaction (1), the following reactions might be also possible. Thus, we ran quantum mechanical calculations to evaluate these two reactions. $$\begin{equation}
CN + NH_2CHO \longrightarrow NH_2CN + HCO,  
\end{equation}$$ $$\begin{equation}
CN + NH_2CHO \longrightarrow trans$-$/cis$-$NCOCHNH + H. 
\end{equation}$$ A schematic of the full PES for the reaction between CN and NH$_2$CHO can be seen in Figure [7](#f:energy). Reaction (1) may initially proceed via the formation of intermediate I1 (NH$_2$C(O)HCN) via transition state TS1. Then the intermediate II is linked to the formation of the products P1 (NH$_2$COCN + H) via transition state TS2, as this involves the elimination of an H-atom. The reaction is exothermic. The barrier energy of this reaction is equal to the energy of transition state minus the energy of the two reactants, which is 9.7 kJ/mol (=1,167 K). We have calculated the rate coefficients of Reaction (1) by the modified Arrhenius equation. The rate coefficients are $2.4 \times 10^{-13}$ and $1.94 \times 10^{-12}$ cm$^3$ s$^{-1}$ at T = 150 and 200 K, respectively. This means that the exothermic formation reaction (1) is slow in the gas-phase. Reaction (2) is via transition state TS3 to form products P2 (NH$_2$CN + HCO), and Reaction (3) firstly form the intermediate I2 (NH$_2$C(H)OCN), then via transition state TS4 and TS5 to form two products P3 (cis-NCOCHNH + H) and P4 (trans-NCOCHNH + H), respectively. As Figure [7](#f:energy) shows, both reactions (2) and (3) are endothermic with high barriers ($>$55 kJ/mol). Their rates would be very low under the ISM conditions.

Besides, we propose another possible reaction route of NCCONH$_2$, where it might be formed upon recombination of two free radicals on the grain surface at low temperature as the following: $$\begin{equation}
CN + NH_2CO \longrightarrow NCCONH_2. 
\end{equation}$$ The radical NH$_2$CO can be formed by CN with water molecules of the ice mantle as reported by (cite: Rimola18).

# CONCLUSIONS

In this paper, we present the tentative detection of NCCONH$_2$ in ISM for the first time. The main results are summarized as follows:

1\. Ten unblended transitions, and twenty one partially-blended transition of NCCONH$_2$ were detected around 3$\sigma$ noise levels toward Sgr B2(N1E) with the ALMA archive data at 3-mm wavelength.

2\. The column density of NCCONH$_2$ toward Sgr B2(N1E) was estimated to be $2.4\times10^{15}$ cm$^{-2}$, while the abundance relative to H$_2$ was estimated to be $6.9\times10^{-10}$. The abundance ratio of NCCONH$_2$ to formamide is $\sim$ 0.01.

3\. Some related molecules were also searched toward Sgr B2(N1E). Both CH$_3$NCO and CH$_3$NHCHO were detected. The abundance ratio between NH$_2$CHO, CH$_3$NCO and CH$_3$NHCHO toward Sgr B2(N1E) is same to that toward Sgr B2(N1S), while the abundance of CH$_3$CONH$_2$ toward Sgr B2(N1E) was much lower than those toward Sgr B2(N1S).

It is highly desirable to conduct confirmation observations on the existence of NCCONH$_2$ in space.

# ACKNOWLEDGEMENTS

We thank the referee, for his/her critical reading of the paper, and very constructive suggestions and comments of our work. JL would like to thank Dr. Laura Colzi for suggestions about this work. JL thank Prof. Vadim Illyushin, Roman Motiyenko, Laurent Margules and Yong Zhang for helpful discussions. This work made use of the High Performance Computing Resource in the Core Facility for Advanced Research Computing at Shanghai Astronomical Observatory. This work has been supported by the National Key R&D Program of China (No. 2022YFA1603101), the National Natural Science Foundation of China (Grant Nos. 11973075, U1931104), Chongqing Talents: Exceptional Young Talents Project (Grant No. cstc2021ycjh-bgzxm0027), and Fundamental Research Funds for the Central Universities (Grant No. 2020CDJXZ002). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00243.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. Data analysis was in part carried out on the open-use data analysis computer system at the Astronomy Data Center (ADC) of NAOJ. This research has made use of NASA’s Astrophysics Data System.

![image](nh2cho_map.ps)

![image](86036.ps) ![image](94117.ps) ![image](95310.ps) ![image](95565.ps) ![image](97481.ps) ![image](99819.ps) ![image](106434.ps) ![image](107207.ps) ![image](108243.ps) ![image](108734.ps)

![image](93247.ps) ![image](93810.ps) ![image](94272.ps) ![image](94636.ps)

![image](100344.ps) ![image](101226.ps) ![image](102567.ps) ![image](103170.ps) ![image](103625.ps) ![image](105396.ps)

![image](105867.ps) ![image](106600.ps) ![image](107618.ps) ![image](108057.ps) ![image](108433.ps)

![image](108630.ps) ![image](109524.ps) ![image](110410.ps)

![image](ch3nco_85687MHz.ps) ![image](ch3nco_85940MHz.ps) ![image](ch3nco_86473MHz.ps) ![image](ch3nco_86683MHz.ps) ![image](ch3nco_95260MHz.ps) ![image](ch3nco_111520MHz.ps) ![image](ch3nco_112388MHz.ps)

![image](ch3nhcho_89030MHz.ps) ![image](ch3nhcho_90900MHz.ps) ![image](ch3nhcho_93400MHz.ps) ![image](ch3nhcho_99732MHz.ps) ![image](ch3nhcho_101309MHz.ps) ![image](ch3nhcho_102025MHz.ps) ![image](ch3nhcho_102192MHz.ps) ![image](ch3nhcho_102600MHz.ps) ![image](ch3nhcho_103082MHz.ps)

![image](fig6.ps)

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Number | Rest Freq. | Transition | $E_{u}$ | $\log_{10}A_{ul}$ | $S_{ij} \mu^2$ |  |  |
|  | (MHz) | $J'(Ka', Kc') - J''(Ka'', Kc'')$ | \(K\) | (s$^{-1}$) | (D$^2$) |  |  |
|  |  | unblended lines |  |  |  |  |  |
| \(1\) | 86036.25670(0.0053) | 20(5, 16) - 20(4, 17) | 85.0 | -4.665 | 119.7 |  |  |
| \(2\) | 94117.1956(0.0059) | 19(7, 13)- 19(6, 14) | 86.3 | -4.505 | 125.6 |  |  |
| \(3\) | 95286.1509(.0053) | 23(7, 17)-23(6, 18) | 117.7 | -4.4649 | 160.0 |  |  |
| \(4\) | 95565.0503(.0061) | 20(4,17) - 20(3, 18) | 80.9 | -4.645 | 91.5 |  |  |
| \(5\) | 97481.6183(.0068) | 13(7, 6) - 13(6, 7) | 50.4 | -4.553 | 70.027 |  |  |
| \(6\) | 99819.5119(0.0082) | 35(8, 27)-35(7, 28) | 256.7 | -4.359 | 268.3 |  |  |
| \(7\) | 106434.0041(0.0058) | 24(8,17) - 24(7, 18) | 131.6 | -4.326 | 164.9 |  |  |
| \(8\) | 107207.9828(0.0067) | 22(3, 19)-22( 2, 20) | 95.7 | -4.534 | 91.8 |  |  |
| \(9\) | 108243.4630(0.0056) | 15(3, 13) - 14(3, 12) | 45.7 | -4.465 | 71.9 |  |  |
| \(10\) | 108734.3241(0.0057) | 16(1,15) - 15(1, 14) | 47.3 | -4.449 | 78.4 |  |  |
|  |  | partially blended lines |  |  |  |  |  |
| \(1\) | 93247.9712(0.0064) | 20(3, 17)-20(2, 18) | 80.7 | -4.675 | 91.8 |  |  |
| \(2\) | 93805.0949(0.0057) | 20(7, 14)-20(6,15) | 93.5 | -4.500 | 134.9 |  |  |
| \(3\) | 94272.7316(0.0054) | 22(7, 16)-22(6, 17) | 109.3 | -4.481 | 152.4 |  |  |
| \(4\) | 94636.0867(0.0061) | 18(7, 12)-18(6, 13) | 79.4 | -4.509 | 116.2 |  |  |
| \(5\) | 100344.5329(0.0066) | 21( 3, 18)-21(2,19) | 88.1 | -4.600 | 91.8 |  |  |
| \(6\) | 101226.7711(0.0082) | 32(7, 25)-32(6, 26) | 214.0 | -4.375 | 226.9 |  |  |
| \(7\) | 102576.1442(0.0056) | 15(1,14)-14(1,13) | 42.1 | -4.527 | 73.4 |  |  |
| \(8\) | 103170.9109(0.0053) | 13(3,10)-12(3, 9) | 37.2 | -4.529 | 62.5 |  |  |
| \(9\) | 103625.1683(0.0058) | 25(6, 20) - 25(5, 21) | 130.9 | -4.414 | 151.9 |  |  |
| \(10\) | 105396.9363(0.0055) | 15(2,13)-14(3,12) | 45.6 | -4.407 | 89.2 |  |  |
| \(11\) | 105867.1182(0.0054) | 14(5,10)-13(5, 9) | 46.9 | -4.531 | 61.9 |  |  |
| \(12\) | 106600.4540(0.0057) | 26(8,19)-26(7, 20) | 150.3 | -4.313 | 182.9 |  |  |
| \(13\) | 107618.0350(0.006) | 22(8,15)-22(7,16) | 114.4 | -4.328 | 145.6 |  |  |
| \(14\) | 108057.9882(0.0066) | 22(4,19)-22(3, 20) | 95.8 | -4.524 | 91.7 |  |  |
| \(15\) | 108433.6177(0.0061) | 21(8,14)-21(7,15) | 106.4 | -4.329 | 136.0 |  |  |
| \(16\) | 108612.1374(0.0058) | 17(0,17)-16(1,16) | 48.1 | -4.106 | 183.8 |  |  |
| \(17\) | 108613.2479(0.0058) | 17(1,17)-16(1,16) | 48.1 | -4.440 | 85.1 |  |  |
| \(18\) | 108614.3824(0.0058) | 17(0,17)-16(0,16) | 48.1 | -4.440 | 85.1 |  |  |
| \(19\) | 108615.4928(0.0058) | 17(1,17)-16(0,16) | 48.1 | -4.106 | 183.9 |  |  |
| \(20\) | 109524.0529(0.0065) | 19(8, 11)-19(7,12) | 91.5 | -4.338 | 117.0 |  |  |
| \(21\) | 110410.4446(0.0085) | 36(8, 28)-36(7, 29) | 270.4 | -4.252 | 260.6 |  |  |

:  Rest frequencies and transition parameters of NCCONH$_2$ lines tentatively detected toward Sgr B2(N1E).

Notes. Col. (2): Rest frequencies with calculated uncertainties given in parentheses; Col. (3): Transition; Col. (4): Upper level energy; Col. (5): Base 10 logarithm of the Einstein $A_{ul}$ coefficient; Col. (6): Line strength $\mathrm{S}_{ij}\mu^2$.

|  |  |  |  |  |  |  |  |
|:---|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Molecule | Size | $T_{rot}$ | $N_{N1E}$ | $\Delta V$ | $V_{off}$ | $N_{N1S}^{**}$ |  |
|  | (") | \(K\) | ($cm^{-2}$) | ($km s^{-1}$) | ($km s^{-1}$) | ($cm^{-2}$) |  |
| NCCONH$_2$, v=0 | 2.3 | 150 | 2.4(15) | 3 | -1 | \- |  |
| CH$_3$NCO | 2.3 | 150 | 2.4(16) | 5 | 0 | 2.5(17) |  |
| HCONH$_{2}$, v=0$^*$ | 2.3 | 150 | 2.8(17) | 6 | -1 | 2.9(18) |  |
| CH$_3$CONH$_{2}$, v=0$^*$ | 2.3 | 150 | 2.5(16) | 3.6 | -1 | 4.1(17) |  |
| CH$_3$NHCHO, v=0 | 2.3 | 150 | 2.1(16) | 5 | 0 | 2.6(17) |  |

: Parameters of LTE model of NCCONH$_2$ and related molecules toward Sgr B2(N1E).

Notes. Col. (1): Molecule name; Col. (2): Source diameter (FWHM), Col. (3): Rotational temperature; Col. (4): Total column density of the molecule. x(y) means $x \times 10^y$; Col. (5): Linewidth (FWHM); Col. (6): Velocity offset with respect to the assumed systemic velocity of Sgr B2(N1), $V_{sys}=64$ km s$^{-1}$; Col (7): column density of the molecule toward Sgr B2(N1S) (cite: Belloche19). $^*$: cited from (cite: Li21). $^{**}$: cited from (cite: Belloche19).

(ref: Altwegg17) Altwegg, K., Balsiger, H., Berthelier, J. J., et al. 2017, MNRAS, 469, S130. doi:10.1093/mnras/stx1415

(ref: Belloche13) Belloche, A., Müller, H. S. P., Menten, K. M., et al. 2013, A&A, 559, A47. doi:10.1051/0004-6361/201321096

(ref: Belloche14) Belloche, A., Garrod, R.T., Holger, S.P., Müller, H. S. P., Menten, K. M., 2014, Science, 345, 1584. doi:10.1126/science.1256678

(ref: Belloche16) Belloche, A., Müller, H. S. P., Garrod, R. T., et al. 2016, A&A, 587, A91. doi:10.1051/0004-6361/201527268

(ref: Belloche17) Belloche, A., Meshcheryakov, A. A., Garrod, R. T., et al. 2017, A&A, 601, A49. doi:10.1051/0004-6361/201629724

(ref: Belloche19) Belloche, A., Garrod, R. T., Müller, H. S. P., et al. 2019, A&A, 628, A10. doi:10.1051/0004-6361/201935428

(ref: Bisschop2007) Bisschop, S. E., Jørgensen, J. K., vn Dishoeck, E. F., de Wachter, E. B. M. 2007, A&A, 465, 913. doi:10.1051/0004-6361:20065963

(ref: Bonfand17) Bonfand, M., Belloche, A., Menten, K. M., et al. 2017, A&A, 604, A60. doi:10.1051/0004-6361/201730648

(ref: Busch22) Busch, L.A., Belloche, A., Garrod, R.T., et al. 2022, A&A, 665, 96. doi:10.1051/0004-6361/202243383

(ref: Christiansen05) Christiansen, J. J. 2005, Journal of Molecular Spectroscopy, 231, 131. doi:10.1016/j.jms.2005.01.004

(ref: Colzi21) Colzi, L., Rivilla, V. M., Beltrán, M. T., et al. 2021, A&A, 653, A129. doi:10.1051/0004-6361/202141573

(ref: Coutens16) Coutens, A., Jørgensen, J. K., van der Wiel, M. H. D. et al. 2016, A&A, 590, L6, doi: 10.1051/0004-6361/201628612

(ref: ditchfield71) Ditchfield R., Hehre, W.J., Pople, J.A., 1971, J Chem Phys, 54, 724. doi:10.1063/1.1674902

(ref: dunning89) Dunning, T.H.J., 1989, J. Chem. Phys., 90, 1007. doi: 10.1063/1.456153

(ref: Endres16) Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., Ml̆ler, H. S. P., 2016, J. Mol. Spectrosc., 327, 95. doi:10.1016/j.jms.2016.03.005

(ref: frisch16) Frisch, M. J., Trucks, G. W., Schlegel, H. B., et al. 2016, Gaussian 16, Revision A.03 (Wallingford, CT: Gaussian, Inc.)

(ref: Halfen11) Halfen, D. T., Ilyushin, V., & Ziurys, L. M. 2011, ApJ, 743, 60. doi:10.1088/0004-637X/743/1/60

(ref: Hollis06) Hollis, J. M., Lovas, F. J., Remijan, A. J., et al. 2006, ApJL, 643, L25. doi:10.1086/505110

(ref: Jimenez20) J Jiménez-Serra, I., Martı́n-Pintado, J., Rivilla, V. M., et al. 2020, Astrobiology, 20, 1048. doi:10.1089/ast.2019.2125

(ref: Kaiser13) Kaiser, R. I., Stockton, A. M., Kim, Y. S., et al. 2013, ApJ, 765, 111. doi:10.1088/0004-637X/765/2/111

(ref: Li20) Li, J., Wang, J., Qiao, H., et al. 2020, MNRAS, 492, 556. doi:10.1093/mnras/stz3337

(ref: Li17) Li, J., Shen, Z., Wang, J., et al. 2017, ApJ, 849, 115. doi:10.3847/1538-4357/aa9069

(ref: Li21) Li, J., Wang, J., Lu, X., et al. 2021, ApJ, 919, 4. doi:10.3847/1538-4357/ac091c

(ref: Ligterink18) Ligterink, N. F. W., Terwisscha van Scheltinga, J., Taquet, V., et al. 2018, MNRAS, 480, 3628. doi:10.1093/mnras/sty2066

(ref: Ligterink20) Ligterink, N. F. W., El-Abd, S. J., Brogan, C. L., et al. 2020, ApJ, 901, 37. doi:10.3847/1538-4357/abad38

(ref: Lopez2019) López-Sepulcre, A., Balucani, N., Ceccarelli, C., et al. 2019, ACS Earth and Space Chemistry, 3, 2122. doi:10.1021/acsearthspacechem.9b00154

(ref: McGuire16) McGuire, B. A., Carroll, P. B., Loomis, R. A., et al. 2016, Science, 352, 1449. doi:10.1126/science.aae0328

(ref: McGuire18) McGuire, B. A. 2018, ApJS, 239, 17. doi:10.3847/1538-4365/aae5d2

(ref: McGuire22) McGuire, B. A. 2022, ApJS, 259, 30. doi:10.3847/1538-4365/ac2a48

(ref: Mendoza14) Mendoza, E., Lefloch, B., López-Sepulcre, A., et al. 2014, MNRAS, 445, 151. doi:10.1093/mnras/stu1718

(ref: CDMS2) Müller, H. S. P., Schlöder, F., Stutzki, J. & Winnewisser, G. 2005, J. Mol. Struct., 742, 215. doi:10.1016/j.molstruc.2005.01.027

(ref: Pickett98) Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, JQSRT, 60, 883. doi:10.1016/S0022-4073(98)00091-0

(ref: Rimola18) Rimola, A., Skouteris, D., Balucani, N., Ceccarelli, C., Enrique-Romero, J., Taquet, V., Ugliengo, P., 2018, ACS Earth Space Chem., 2, 720. doi:10.1021/acsearthspacechem.7b00156

(ref: Rubin71) Rubin, R. H., Swenson, G. W., Benson, R. C., et al. 1971, ApJL, 169, L39. doi:10.1086/180810s

(ref: sanchez2018) Sánchez-Monge, Á., Schilke, P., Ginsburg, A., et al. 2018, A&A, 609, A101. doi:10.1051/0004-6361/201730425

(ref: Suzuki2018) Suzuki, T., Ohishi, M., Saito, M. et al. 2018, ApJS, 237, 3. doi:10.3847/1538-4365/aac8db

(ref: Turner1989) Turner, B.E. 1989, ApJS, 70, 539. doi:10.1086/191348

(ref: Turner1991) Turner, B.E. 1991, ApJS, 76, 617. doi:10.1086/191577

(ref: Winnewisser05) Winnewisser, M., Medvedev, I. R., De Lucia, F. C., et al. 2005, ApJS, 159, 189. doi:10.1086/430470

(ref: Zeng23) Zeng, S., Rivilla, V. M., Jiménez-Serra, I., et al. 2023, MNRAS, 523, 1448. doi:10.1093/mnras/stad1478

(ref: zhao08) Zhao, Y., Truhlar, D.-G., 2008, Theor. Chem. Acc., 120, 215

</paper>

Write the methods card for this paper.