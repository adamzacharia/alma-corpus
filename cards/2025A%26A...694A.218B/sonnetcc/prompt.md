# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...694A.218B\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...694A.218B",
 "title": "Revealing the hidden cosmic feast: A z = 4.3 galaxy group hosting two optically dark, efficiently star-forming galaxies",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Brinch, Malte",
 "n_authors": 14,
 "arxiv_id": "2501.05288",
 "doi": "10.1051/0004-6361/202451448",
 "alma_projects_linked_by_archive": [
  "2016.1.00463.S",
  "2021.1.00246.S",
  "2022.1.00884.S"
 ]
}
```

Paper text:
<paper>
# Revealing the hidden cosmic feast: A z=4.3 galaxy group hosting two optically dark, efficiently star-forming galaxies

# Introduction

Within the modern $\Lambda$CDM paradigm, a major goal is to understand the formation and evolution of massive galaxies ($\rm M_{\star}>10^{11}\,\rm M_{\odot}$) and the structures they inhabit (clusters and groups). For a $\Lambda$CDM cosmology, massive galaxies are thought to form through the hierarchical clustering of lower mass galaxies and their dark matter halos (cite: Springel2005). From cosmological simulations, the growth of massive galaxies has been shown to be in a heightened phase prior to cosmic noon ($z>2$) due to a combination of in situ gas accretion and the merging of low-mass ($\rm M_{\star}\lesssim 10^{10}\,\rm M_{\odot}$) satellite galaxies (cite: Hopkins2009; Oser2010; Benson2012; Hirschmann2012). Overdense structures such as protoclusters or galaxy groups are prime locations to investigate the growth of massive galaxies, as these structures initially formed in the peaks of the primordial density field. They are thought to undergo a downsizing effect, where the galaxies in the overdense structure (especially in the center of the structure) will become more evolved, compared to the field population (cite: Overzier2016; Chiang2017; Marrone2018). These overdense structures are typically found through either the use of large-scale surveys of specific types of galaxies such as Lyman-break galaxies or Lyman-alpha emitters (cite: Harikane2019; Brinch2023; Brinch2024). They can also be found using signpost galaxies such as submillimeter (submm) galaxies (SMGs) or quasi-stellar objects (QSOs) that are biased tracers of overdensities, where their nearby environment can then be investigated (cite: Capak2011; Walter2012; Lewis2018; Calvi2023). Wide-field submillimeter-millimeter (submm/mm) and interferometric observations with instruments such as Submillimetre Common-User Bolometer Array 2 (SCUBA-2) on the *James Clark Maxwell* Telescope (JCMT), Northern Extended Millimeter Array (NOEMA), and the Atacama Large Millimeter/submillimeter Array (ALMA) have allowed for the study of massive, highly star-forming galaxies in the high-redshift Universe thanks to their high spectral coverage and sensitivity (cite: Dannerbauer2014; Oteo2018; Miller2018). In conjunction with optical and near-infrared (NIR) surveys, these observations enable us to identify and study the dense and compact structures where these galaxies assemble (e.g., (cite: Wang2016; Daddi2021; Daddi2022; Jones2017; Diaz-Santos2018; Cooper2022; Ginolfi2022; Sillassen2022; Sillassen2024; Jin2023; Jin2024)).

Meanwhile, studies have revealed a population of optically/NIR dark dusty star-forming galaxies (DSFGs) that drop out in deep optical images (cite: Smail1999; Higdon2008; Wang2019; Algera2020; Smail2021; Talia2021; Guijarro2022; Shu2022; Vlugt2023; Xiao2023). They are found to play a critical role in the dust-obscured cosmic star-formation density (SFRD), with a contribution of up to 50% at high redshift and likely dominate at the massive end ($\rm log(M_{\odot}/M_\odot)>10.5$) of the stellar mass function (SMF) at $z\sim3-7$ (cite: Wang2019). With the advent of the James Webb Space Telescope (JWST), The search for optically faint and dark galaxies has been pushed to redshifts of $z\sim8$, where they have been shown to be an important contribution to the high-mass end of the galaxy stellar mass function and the cosmic SFRD up to $z\sim7-8.$ Furthermore, a significant fraction of $z>3$ galaxies, especially massive galaxies, has gone unaccounted for (cite: Barrufet2023; Gottumukkala2024). However, the majority of literature studies of this population at high redshift rely heavily on photometric redshifts. The spectroscopically confirmed sample of optically dark galaxies is still small, with their environments and ISM properties remaining largely unknown.

In this work, we present the discovery of a compact galaxy group (which we dub CGG-z4) and study the member galaxies’ star formation and ISM properties. This paper is organized as follows. We describe the observational data and selection in Sect. 2. Section 3 describes the methods for redshift confirmation, spectral stacking, and SED fittings. In Sect. 4, we present the results and analysis, including different physical properties such as SFR and gas mass estimates. We discuss relevant science in Sect. 5 and summarize our conclusions in Sect. 6. Throughout the paper, we have adopted a standard $\Lambda$CDM cosmology with $H_{\rm 0}=70\,{\rm km\,s^{-1}\,Mpc^{-1}}$, $\Omega_{\rm m} = 0.3$, and $\Omega_{\rm \Lambda} = 0.7$. All magnitudes are expressed in the AB system (cite: Oke1974). We adopted a (cite: Chabrier2003) stellar initial mass function (IMF). The results are reported with uncertainties within the 68% confidence interval.

# Selection and data

![image](Figures/Kband.pdf) ![image](Figures/VLA9334_contour_5710sigma.pdf.pdf) ![image](Figures/CGG-z4ab.pdf)

![image](Figures/VLA9334-cont-98GHz.pdf) ![image](Figures/source_a_CO4-3.pdf) ![image](Figures/source_b_CO4-3.pdf) ![image](Figures/source_a_CO5-4.pdf) ![image](Figures/source_b_CO5-4.pdf) ![image](Figures/source_a_CI1-0.pdf)

## Selection

CGG-z4.a was initially selected as a radio source by the VLA 3GHz Large Program in the COSMOS field (cite: Smolcic2017) at $8\sigma$. It was included in the COSMOS Super-deblended catalog (cite: Jin2018) as an additional radio prior in combination with the low-angular resolution Herschel bands and with no optical/NIR counterpart in the COSMOS2015 catalog (cite: Laigle2016). It was observed by an ALMA 3mm line scan as a bright SCUBA-2 source in the (cite: Simpson2019) map, a part of the ALMA project 2021.1.00246.S, (PI: C. Chen). Our initial FIR SED analysis with deblended FIR photometry suggested a $z_{\rm FIR}\sim6$; this was followed up with an ALMA 3mm line scan in program 2022.1.00884.S (PI: R. Gobat). CGG-z4.b has been observed in the ALMA pointing as well, and is also included among the radio sources in the (cite: Smolcic2017) catalog at $8\sigma$. The remaining candidate members of CGG-z4 are selected from the COSMOS2020 CLASSIC catalog (cite: Weaver2022). We adopted a photometric redshift selection of $4.0<z_{\rm phot}<4.6$ from the EAZY spectral energy distribution (SED) fitting (cite: Brammer2008) with UV/optical to NIR photometry in COSMOS2020, corrected for Galactic extinction using the (cite: Schlafly2011) dust map. The galaxies are not part of the area covered by the JWST treasury program COSMOS-Web (ID:1727, PI: J. Kartaltepe, (cite: Casey2023)).

## ALMA

The two ALMA 3mm line scan programs continuously cover the frequency range from 84.1 to 113.2 GHz in Band 3 (cite: ALMAband3). Program 2021.1.00246.S yielded a continuum sensitivity of $0.02\,\rm mJy/Beam$, an angular resolution of $1.6\ensuremath{''}$ and a velocity resolution of $84\,\rm km/s$ observed over a $26\,\rm min$ scan. Program 2022.1.00884.S yielded a continuum sensitivity of $0.02\,\rm mJy/Beam$, an angular resolution of $1.1\ensuremath{''}$ and a velocity resolution of $23\,\rm km/s$ observed over three $20\,\rm min$ scans. ALMA $870\,\rm \mu m$ continuum detections were obtained as part of the program 2016.1.00463.S (PI: Y. Matsuda), in which CGG-z4 was observed over $0.7\,\rm min$ in Band 7 (cite: ALMAband7-2005; ALMAband7-2006) with a continuum sensitivity of $0.27\,\rm mJy/Beam$, an angular resolution of $0.8\ensuremath{''}$ and a velocity resolution of $27\,\rm km/s$. The ALMA data were reduced and calibrated using the standard ALMA CASA pipeline (cite: CASA). Following our established pipeline from (cite: Jin2019; Jin2022; Jin2024cosbo7), the calibrated measurement sets were then converted to uvfits format for further analysis in uv space with the GILDAS software (cite: Gildas2013). For the galaxies with a continuum detection, the spectrum was extracted using Gildas `uv_fit`, in which we fit $uv$ visibility at each frequency using a point source model fixed at the position of continuum peak. For sources without strong continuum detection, their spectra were extracted based on positions from the COSMOS2020 catalog. We note that program 2021.1.00246.S contains 20 spectral windows (SPWs), and project 2021.1.00246.S contains 12 SPWs. We extracted the 3mm 1D spectrum of each SPW and combined the spectra of all SPWs in the observed frame to enhance the signal-to-noise ratio (S/N) at overlapped frequencies. This resulted an average $1\sigma$ spectral line sensitivity of 0.05 Jy km s$^{-1}$ beam$^{-1}$ over a 500 km s$^{-1}$ width in Band 3. The continuum fluxes were measured by combining all line-free channels and fitting the sources in $uv$ space with point-source models. The clean residuals indicate the sources are well-fitted and are unresolved in the dust continuum. The resulting synthesized beam size is $\approx2.7\ensuremath{''}$ for the 3mm data, while the $870\,\rm \mu m$ data has a synthesized beam of $\approx0.8\ensuremath{''}$. The spectra of CGG-z4.a and CGG-z4.b are shown in Fig. [1](#fig:color-image), while line and continuum maps are shown in Fig. [2](#fig:linemaps).

## Ancillary data

We use VISTA images from (cite: Weaver2022) for visualization, as shown in Fig. [1](#fig:color-image). To identify the candidate members in this group, we utilized the optical/NIR photometry and photometric redshifts in the COSMOS2020 catalog (cite: Weaver2022). We note that the area of CGG-z4 was masked in the COSMOS2020 Farmer catalog, so instead we used the COSMOS2020 Classic catalog which fully cataloged galaxies in this area. To constrain the FIR SED of CGG-z4, we make use of MIPS (cite: LeFloch2009), Herschel (cite: Lutz2011PACS; Oliver2012SPIRE), SCUBA-2 (cite: Simpson2019), and VLA images (cite: Smolcic2017) to measure the FIR-to-radio photometry with the Super-deblending technique (cite: Jin2018; Liu2018).

# Method

## Line detections and Redshift determination

We use the `LMfit` package (cite: Newville2014) to fit the emission lines and continuum simultaneously. Emission lines were fitted as Gaussians. When multiple emission lines were present in the same spectra, we fixed the sigma value of the Gaussian to be the same when performing the fitting, which, in turn, means the full width at half maximum (FWHM) is fixed. the continuum is fitted as a power law using the formula $y=A\times \nu^{P}$, where A is the amplitude and $P=3.7$ following (cite: Magdis2012; Jin2022). The line fits are shown in Fig. [1](#fig:color-image) and the derived properties are reported in Table [\[tab:line\]](#tab:line).

With line detections of CO(4-3) and CO(5-4), we measured a redshift of $z=4.331\pm0.001$ and $4.324\pm0.001$ for CGG-z4.a and b, respectively. The CO(4-3) lines are detected with an integrated line flux significance of 11.6$\sigma$, 8.4$\sigma$, and CO(5-4) is detected with 7.7$\sigma$, 4.8$\sigma$ respectively. The redshift difference between the two sources is $\Delta z=0.007$, which is equivalent to an on-sky projected line of sight distance of $0.829\,\rm pMpc$ ($395\,\rm km/s$). Notably, we also detect the \[Ci\](1-0) emission line in CGG-z4.a with 4.3$\sigma$ and ortho-H$_2$O(1$_{1,0}$-1$_{0,1}$) absorption line in CGG-z4.b with 3.5$\sigma$. The detection of water absorption in CGG-z4.b adds to a growing list of lines observed in the high redshift universe, including the H$_2$O(1$_{1,0}$-1$_{0,1}$) absorption in HFLS3 at $z=6.34$ (cite: Riechers2022) and in ID 9316 at $z=4.07$ (cite: Jin2022). The water line is an indicator that the galaxy is currently undergoing a starburst, as the intense radiation field from the starburst results in a line excitation temperature that is lower than the CMB temperature, resulting in absorption against the CMB. This also allows the line to be a probe of the CMB temperature (cite: Riechers2022).

|  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|
| ID | RA, Dec | $z_{\rm spec}$ | I$_{\rm CO(4-3)}$ | I$_{\rm [C_{\rm I}](1-0)}$ | I$_{\rm CO(5-4)}$ | I$_{\rm H_{2}O(1_{1,0}-1_{0,1})}$ | FWHM |
|  | \[hh:mm:ss, dd:mm:ss\](J2000) |  | \[Jy km/s\] | \[Jy km/s\] | \[Jy km/s\] | \[Jy km/s\] | \[km/s\] |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) |
| CGG-z4.a | 10:02:40.4313, 01:45:44.0860 | 4.331$\pm$0.001 | 0.67$\pm0.06$ | 0.22$\pm 0.05$ | 1.02$\pm 0.13$ | $<0.11$ ($2\sigma$) | 588 |
| CGG-z4.b | 10:02:39.9297, 01:45:46.3900 | 4.324$\pm$0.001 | 0.39$\pm0.05$ | $<0.09$ ($2\sigma$) | 0.55$\pm 0.12$ | -0.15$\pm 0.04$ | 545 |

Table notes: Columns: (1) Name; (2) RA, Dec; (3) $z_{\rm spec}$; (4) CO(4-3) line emission; (5) \[Ci\](1-0) line emission; (6) CO(5-4) line emission; (7) H$_2$O($1_{1,0}-1_{0,1}$) line absorption; (8) FWHM. Fluxes have been primary beam-corrected.

## Spectral stacking

To identify potential CO emissions from the optical/NIR-detected members, we extracted spectra at the positions of all candidate galaxy group members and stacked them at the redshift of CGG-z4.a. We calculated the S/Ns at CO(5-4) and CO(4-3) frequencies and we found no definitive detections at the $2\sigma$ level (0.06 Jy km/s for CO(5-4) and 0.04 Jy km/s for CO(4-3)), nor a continuum detection. This indicates that the two optically dark galaxies dominate the total SFR and gas content of this group.

## SED fitting

To estimate the physical characteristics of the CGG-$z4$.a and CGG-$z4$.b, we performed a detailed SED analysis by fitting the integrated FIR, (sub-)mm, and radio photometry. The integrated FIR to radio photometry is measured using the Super-deblending technique (cite: Jin2018; Liu2018), following the identical pipeline adopted for high-redshift groups as in (cite: Daddi2021; Sillassen2022; Zhou2023; Sillassen2024). We used the SED fitting code MICHI2 (cite: Liu2020; Liu2021) that simultaneously fits components of stellar (cite: Bruzual2003), mid-IR active galactic nuclei (cite: Mullaney2011) and dust (cite: Draine2007), as well as a radio component derived from IR-radio correlation (cite: Magnelli2015), without the assumption of energy balance. Given the optically dark nature of CGG-z4.a and CGG-z4.a, we fit the MIPS/24$\rm \mu m$, Herschel, SCUBA2, and ALMA photometry, with a mid-IR AGN, warm photodissociation region (PDR), and cold and ambient dust components. Figure [3](#fig:MICHI2) shows the full fit, with the photometry used shown in Table [1](#tab:MICHI2). For comparison with the ALMA and radio data where the two galaxies are resolved, we scaled the combined SED with the ALMA 870 $\mu$m flux of CGG-z4.a and CGG-z4.b. We observe that scaled SED fits align with the data, with the exception of the radio data of CGG-z4.a, which is below the expected value from the IR-radio correlation.

![](Figures/SED.pdf)

When fitting the optically detected COSMOS2020 galaxies, it should be noted that the SED fits from EAZY are a linear combination of 12 preselected flexible stellar population synthesis (FSPS) templates. EAZY primarily excels in determining the redshift probability distribution of large galaxy samples. Other SED fitting codes are more suited when estimating the physical properties of individual galaxies. To that end, we use the SED fitting code Bagpipes (cite: Carnall2018) to fit the COSMOS2020 classic photometry for physical parameters like stellar mass and star formation rate (SFR). We followed the approach of (cite: Carnall2023; Heintz2023; Jin2023) and assumed a constant star formation history (SFH) and the attenuation curve of (cite: Salim2018), which mimics a bursty SFH on short timescales. A (cite: Salim2018) curve better represents low-mass, low-metallicity galaxies. We note that we tried using an exponential SFH, which resulted in virtually identical results since our current data only allows us to probe the recent burst for the optical/NIR galaxies due to the outshining effect from the massive young stars in the galaxies. We ran Bagpipes with the following parameters: formation mass $\rm log(M_{\rm \star})\in[6.0:12.0]\, log(M_{\rm \odot})$, metallicity $\rm Z\in[0.01:2.00]\, Z_{\rm \odot}$, reddening $\rm A_{\rm v}\in[0.0:4.0],$ and the $U$ parameter, which is the strength of the nebular radiation field to $\log(U) \in[-4.0:-1.0]$. We ran the fitting for each COSMOS2020 galaxy at the spectroscopic redshift of CGG-z4.a ($z=4.331$), assuming they are all part of the galaxy group. The resulting SED fits are shown in Fig. [7](#fig:BPSEDS) and a summary of all the values obtained from the SED fitting is shown in Table [2](#tab:SED). We note that allowing the photometric redshift to vary in Bagpipes results in changes to the posterior fit values that are (at most) at the $1\sigma$ level, with the exception being the age of ID361346 having a higher metallicity of $0.54^{+0.66}_{-0.37}\,\rm Z_{\odot}$ and a younger age of $0.13^{+0.18}_{-0.10}\,\rm Gyr$. This does not change any of the conclusions drawn in this paper.

# Results and analysis

## A $z\approx4.3$ compact galaxy group

Figure [1](#fig:color-image) presents color images of CGG-z4, comprised of Hyper Suprime-Cam (HSC) and Visible and Infrared Survey Telescope for Astronomy (VISTA) bands with SCUBA2 and ALMA contours overlaid. The Ks-band image highlights the region where the original SCUBA source was detected, while the Ks,J,i true color image shows the ALMA continuum contours of the two optical/NIR dark sources, as well as the optically/NIR, detected galaxies that are within the COMOS2020 catalog. The ALMA 3mm spectra for the two sources with multiple line detections, CGG-z4.a and CGG-z4.b, are shown in the bottom panel of Fig. [1](#fig:color-image). CGG-z4.b is within 1$''$ of a $z=0.8$ galaxy identified in the COSMOS2020 catalog with ID 357498. Similar to the SMGs of (cite: Smail2021), CGG-z4.a and CGG-z4.b are not detected in the Ks-band with Ks\>25.3 mag in the COSMOS2020 catalog (cite: Weaver2022), with the combination of no detection blueward of the Ks-band classifying them as Ks-band dropouts. Figure [2](#fig:linemaps) Shows the ALMA 3mm continuum map and line emission maps for CGG-z4.a and CGG-z4.b, with the members found in COSMOS2020 overlaid. We see a high sky overdensity of galaxies within a small region, with 13 galaxies over a region of $13\ensuremath{''}\times31\ensuremath{''}$ ($89\times209\,\rm kpc^2$). For any galaxy group or protocluster to grow into a cluster over time, it requires material (other halos with galaxies and gas) to be fed into the structure. It is therefore important to consider the large-scale environment that the group is part of when considering if it will end up as a cluster by $z=0$. Performing an overdensity analysis for galaxies at $z=4.0-4.6$ in the COSMOS field in the same manner as (cite: Brinch2023), utilizing a weighted adaptive kernel estimator and including the spectroscopic redshifts of Khostovan et al. (in prep.), we find that CGG-z4 appears to be in an overdense environment at the $3\sigma$ level ($\delta_{\rm OD}=2.16$). This significance is similar to other studies that have used SMGs as tracers of overdense environments (cite: Calvi2023).

## Stellar mass

The results of EAZY and Bagpipes SED fitting are listed in Table [2](#tab:SED). The EAZY median redshift in the tables is shown to highlight the uncertainty of the redshifts. Given the optically dark nature of CGG-z4.a and b, coupled with the fact that they are only detected in IRAC channel 2, we applied two methods to estimate their stellar masses. First, we scaled their IRAC channel 2 peak fluxes to the IRAC fluxes of the COSMOS2020 sources with photometric redshifts between $4.0<z<4.6$ and then scaled the average stellar mass to CGG-z4.a and b. This yielded log$M_*/M_\odot\sim10.4$ for both galaxies. A caveat is that the inferred stellar masses are prone to be uncertain as they are based on one-band photometry. Second, given their robust detections in sub-mm and mm wavelengths, we inferred their stellar masses using dust mass with empirical stellar-to-dust mass ratios. By fitting optically thick blackbody models to their FIR and ALMA photometry (e.g., (cite: Lamperti2019)), we obtained dust masses of $\rm log(M_{\rm dust}\,\rm [M_{\odot}])=9.10^{+0.29}_{-0.28}$ and $\rm log(M_{\rm dust}\,\rm [M_{\odot}])=8.80^{+0.29}_{-0.29}$ for a and b, respectively. Then we adopted a range of stellar-to-dust mass ratios $M_*/M_{\rm dust}=50-100$, a typical value for starburst galaxies at high-redshifts (cite: Donevski2020). We obtained stellar masses of $\rm log(M_{\rm \star}\,\rm [M_{\odot}])=10.98^{+0.30}_{-0.37}$ and $\rm log(M_{\rm \star}\,\rm [M_{\odot}])=10.68^{+0.30}_{-0.38}$. The $\rm M_{\rm dust}$-based stellar masses are 0.62 and 0.29 dex higher than IRAC-scaled ones, which is understandable as the IRAC fluxes (rest-frame of 0.8$\,\rm \mu$m) can be severely attenuated in optically dark galaxies (e.g., (cite: Kokorev2023HSTdark)). To reconcile the results from the two methods, we conservatively adopted the average stellar masses with uncertainties compassing both results, as listed in Table [2](#tab:SED). Future observations with JWST will be essential to constrain their stellar content robustly.

## Halo mass

We applied five methods to estimate the dark matter halo mass. We followed the identical pipeline by (cite: Sillassen2024), which was intricately designed for eight massive groups at $1.5<z<4$ in the COSMOS field, where they applied six methods for estimating the dark matter masses, including the stellar-mass-to-halo-mass relations (SHMR), overdensity with galaxy bias, and NFW profile fitting to radial stellar mass densities (see details in (cite: Sillassen2024), Sect. 4.4).

First, using the stellar mass of the central galaxy CGG-z4.a with a SHMR from (cite: Behroozi2013), we obtained a lower limit of halo mass $\rm log(M_{\rm DM}[M_{\rm \odot}])>12.2$. Second, based on the stellar masses above the completeness limit of the COS- MOS survey and an SMF (cite: Muzzin2013), we obtained a sum of stellar masses within a posterior virial radius of 105 kpc determined on the basis of the best halo mass from different methods. Then we derived a halo mass of $\rm log(M_{\rm DM}[M_{\rm \odot}])=12.4\pm0.4,$ using the dynamical mass-constrained SHMR for $z\sim1$ clusters (cite: van_der_Burg2014). Third, based on the same total stellar mass, this yielded $\rm log(M_{\rm DM}[M_{\rm \odot}])=12.6\pm0.3$ by adopting SHMR from (cite: Shuntov2022). Fourth, based on the overdensity level of CGG-z4 above the whole COSMOS field and adopting a galaxy bias factor, we obtained $\rm log(M_{\rm DM}[M_{\rm \odot}])=13.5\pm0.3$. Fifth, utilizing the newly invented NFW profile fitting to the radial stellar mass densities by (cite: Sillassen2024), we obtained $\rm log(M_{\rm DM}[M_{\rm \odot}])=13.1_{-0.5}^{+0.2}$. Given the five results above, we adopted their average of $\rm log(M_{\rm DM}[M_{\rm \odot}])=12.8\pm0.4$ as the best estimate.

## Star formation and ISM properties

The best-fit MICHI2 model yields a total IR $\rm SFR=2111\pm98\,\rm M_{\odot}/yr$, mean radiation field of $U=56\pm5$, and dust mass of $\rm log(M_{\rm dust} [M_{\odot}])=9.42\pm0.03$. We obtained a total IR luminosity of $\rm log(L_{\rm IR} [L_{\odot}])=13.32\pm0.02$ from integrating the SED fit between 8-1000$\rm \mu m$. We find no evidence of mid-IR AGN contribution, with the AGN luminosity being 0.36% of the total IR luminosity, which is within the uncertainty of the fit. To derive the FIR properties of individual galaxies, we assumed that CGG-z4.a and CGG-z4.b share the same SED shape as the integrated SED. We then scaled the SED to the ALMA 870$\,\rm \mu m$ flux of each source, which is $10.0\pm0.4$ mJy and $5.0\pm0.6$ mJy, respectively. The SFR of individual sources is listed in Table [2](#tab:SED), with IR $\rm SFR=1408\pm86\,\rm M_{\odot}/yr$ and $703\pm65\,\rm M_{\odot}/yr$ for CGG-z4.a and CGG-z4.b, respectively. The galaxy main sequence (MS) is shown in Fig. [4](#fig:MS/LL)a, showing both the (cite: Speagle2014) and (cite: Schreiber2015) MS. CGG-z4.a and CGG-z4.b are seen as clearly being above the main sequence at $z=4.3$, at $\times6$ and $\times4.5,$ respectively. The most massive member besides CGG-z4.a and CGG-z4.b with optical/NIR data is ID:361388, with a stellar mass of $\rm log(M_{\star}[M_{\odot}])=10.44\pm0.23$ and an SFR of $115^{+121}_{-55}\,\rm M_{\odot}\,\rm yr^{-1}$. It is placed within the scatter of the (cite: Schreiber2015) main sequence at $z\sim4$. Furthermore, ID:361388 is also the most dust-obscured source in our sample, with $A_{\rm v}=3$. The galaxies of CGG-z4 are a mixture of massive and star-forming galaxies with SFRs of $\approx41-241\,\rm M_{\odot}\,\rm yr^{-1}$, along with less massive galaxies with lower SFRs with stellar masses as low as $\rm log(M_{\star}[M_{\odot}])=8.51$ and SFRs of $\approx2-17\,\rm M_{\odot}\,\rm yr^{-1}$, as seen in Table [2](#tab:SED). The combined stellar mass of the group is $\rm log(M_{\star}[M_{\odot}])=11.29^{+0.38}_{-0.33}$ and the combined SFR is $2837^{+731}_{-472}\,\rm M_{\odot}\,\rm yr^{-1}$.

Figure [4](#fig:MS/LL)b shows the relationship between L$^\prime_{\rm [C{\sc I}](1-0)}$ and L$^\prime_{\rm CO(4-3)}$. When compared to the relations using data from (cite: Spilker2014; Boogaard2020; Valentino2018; Valentino2020; Lee2021), CGG-z4.a appears to be linear or slightly superlinear, while CGG-z4.b is very faint in \[Ci\](1-0) and appears superlinear. The fact that the relationship is superlinear indicates that the CO(4-3) emission is tracing the dense gas that forms stars and as a result is also tracing star formation; meanwhile \[CI\](1-0) traces the total gas mass, resembling the effects of the global Kennicutt–Schmidt law (cite: Schmidt1959; Kennicutt1998; Lee2021).

## Gas mass estimates

To estimate the gas mass from the dust emission in CGG-z4.a and CGG-z4.b, we used a $850\,\rm \mu m$ conversion from (cite: Dunne2022). The method was originally pioneered by (cite: Scoville2013; Genzel2015; Scoville2016). They investigated a number of $\alpha_{\rm X}$ conversion factors by dividing their galaxy sample into two. The first group is extreme starburst "SMGs" containing the high-redshift sub-mm selected galaxies that were discovered pre-ALMA; as such, these are extreme star-forming systems (based on their detection), along with the local ULIRGs and some LIRGs that have evidence for being very intensely star-forming and obscured regions where conditions are likely to be extreme (cite: Santos2017; Falstad2021). The second group is main sequence galaxies that contain the lower luminosity local disc galaxies, along with the LIRGS (which are not extreme), intermediate redshift sources selected at 250$\mu$m from the Herschel-ATLAS, $z=0.35$ galaxies from (cite: Dunne2021) and the $z<0.3$ VALES galaxies (cite: Hughes2017), the $z\sim1$ galaxies (cite: Valentino2018; Bourne2019), and the ASPECs sources denoted as "MS" in that survey (cite: Boogaard2020). We refer to Table 1. in (cite: Dunne2022) for a full reference list.

We used an $\alpha_{850}$ value of $7.3\pm0.1\times10^{12}\,\rm W\, Hz^{-1}\, M_{\odot}^{-1}$, such that M$_{\rm gas}=\rm L_{850}/\alpha_{850}$. $\rm L_{850}$ is calculated as follows $$\begin{equation}
    \rm L_{850}=4\pi S_{\nu(obs)} \times K \left(\frac{D_{L}^{2}}{1 + z}\right)\, W Hz^{-1}
,
\end{equation}$$ where $\rm D_{L}$ is the luminosity distance, $\rm S_{\nu(obs)}$ is the observed flux density and K is the K-correction to rest-frame $850\,\rm \mu m$, which is defined as $$\begin{equation}
    \rm K =\left(\frac{353\,\rm GHz}{\nu_{\rm rest}}\right)^{3+\beta}\left(\frac{e^{h\nu_{\rm rest}/kT_{d}} - 1}{e^{16.956\,\rm K/T_{d}} - 1}\right)
,
\end{equation}$$ where $\nu_{\rm rest} = \nu_{\rm obs}(1 + z)$, $\rm T_{\rm d}$ is the luminosity-weighted dust temperature, from an isothermal fit to the SED with the dust emissivity, $\beta$. Given their sub-mm brightness and the fact that they are optical/NIR dark, CGG-z4.a and CGG-z4.b are likely starbursts with optically thick dust emission. To account for this possibility, we performed a modified black body fitting using a thin- and thick-dust model following (cite: Lamperti2019). The values we found for the thin dust model are: $\rm T_{\rm d}=40.23^{+2.92}_{-2.82}\,\rm K$, $\beta=1.85^{+0.16}_{-0.15}$; for the thick dust model, these are: $\rm T_{\rm d}=57.57^{+10.36}_{-11.53}\,\rm K$, $\beta=1.93^{+0.27}_{-0.16}$. We note that using a higher $\beta\approx1.9$ for the power law continuum fit changes its value by (at most) $3.4\%$ and does not change the value of any line fluxes at the level of precision reported in this paper. The resulting K corrections are $\rm K_{\rm thin}=4.8\pm1.3\times10^{-3}$ and $\rm K_{\rm thick}=2.9\pm1.1\times10^{-3}$. By scaling the SCUBA-2 $850\,\rm \mu m$ flux by the ALMA $870\,\rm \mu m$ flux for CGG-z4.a and CGG-z4.b, we find the following luminosities, $\rm L_{850,thin,a}=1.4\pm0.4\times10^{24}\,\rm WHz^{-1}$, $\rm L_{850,thin,b}=7.2\pm2.3\times10^{23}\,\rm WHz^{-1}$, $\rm L_{850,thick,a}=9.0\pm4.0\times10^{23}\,\rm WHz^{-1}$, and $\rm L_{850,thick,b}=4.3\pm1.8\times10^{23}\,\rm WHz^{-1}$. The resulting gas masses are $\rm log(M_{\rm gas,thin,a}[M_{\odot}])=11.29^{+0.12}_{-0.16}$, $\rm log(M_{\rm gas,thin,b}[M_{\odot}])=10.99^{+0.12}_{-0.17}$, $\rm log(M_{\rm gas,thick,a}[M_{\odot}])=11.07^{+0.15}_{-0.24}$, and $\rm log(M_{\rm gas,thick,a}[M_{\odot}])=10.77^{+0.15}_{-0.24}$. In combination with the stellar mass estimates, we can estimate the gas mass fraction $\rm M_{\rm gas}/M_{\star}$, with CGG-z4.a and CGG-z4.b having inferred gas mass fractions (estimated through Monte Carlo sampling) of $\rm M_{\rm gas}/M_{\star}=1.7^{+3.6}_{-0.9}$ and $\rm M_{\rm gas}/M_{\star}=1.7^{+3.4}_{-0.9}$ using a thin dust model and $\rm M_{\rm gas}/M_{\star}=1.0^{+2.2}_{-0.6}$ and $\rm M_{\rm gas}/M_{\star}=1.0^{+2.1}_{-0.6}$ using a thick dust model. The ratio M$_{\rm gas}$/SFR approximates the gas depletion timescale, which is the inverse of the star formation efficiency (SFE). Given the gas mass and SFR of CGG-z4.a and CGG-z4.b both have gas depletion times of $140\pm(44,46)\,\rm Myr$ using a thin dust model and $84\pm(36,37)\,\rm Myr$ using a thick dust model. The thick dust model results in 0.22 dex lower gas masses, which, in turn, means that the gas mass factions and gas depletion times are 60% of the thin dust model values. For comparison, we used our available CO lines and an $\alpha_{\rm CO}$ conversion to estimate M$_{\rm gas, H2}=\alpha_{\rm CO}\times\rm L^{\prime}_{\rm CO(1-0)}$. Since we did not have data for the CO(1-0) line, we instead converted the $\rm L^{\prime}_{\rm CO(4-3)}$ to $\rm L^{\prime}_{\rm CO(1-0)}$ first. By comparing the flux ratio of CO(5-4) and CO(4-3) lines for CGG-z4.a and CGG-z4.b, we find that they have values of $1.52\pm0.24$ and $1.41\pm0.36$, which is close to the thermalization limit of $\rm (J=5)^{2}/(J=4)^{2}=1.56$ (cite: Narayanan2014); therefore, we obtained the ratio r$_{\rm L^{\prime}41}=\rm L^{\prime}_{\rm CO(1-0)}/L^{\prime}_{\rm CO(4-3)}\sim1.0$. We note that there is a systematic error in using a value of r$_{\rm L^{\prime}41}=1.0$ that is unaccounted for. For the value of $\alpha_{\rm CO}$, we used the canonical value for star-bursting high-$z$ SMGs of $\alpha_{\rm CO}=0.8\,\rm [M_{\odot}\, pc^{-2}\, (K\, km\, s^{-1})^{-1}]$ (cite: Downes1998; Tacconi2008; Carilli2010). Multiplying by a factor $\times1.36$ to account for the contribution from helium, this gives a gas mass of $\rm log(M_{\rm gas}[M_{\odot}])=10.51^{+0.04}_{-0.04}$ and $\rm log(M_{\rm gas}[M_{\odot}])=10.28^{+0.05}_{-0.06}$ for CGG-z4.a and CGG-z4.b, respectively. These values are $\sim0.7, 0.5$ dex lower than the ones estimated using the fit values and result in both lower gas mass ratio ($0.3^{+0.6}_{-0.1}$ and $0.3^{+0.6}_{-0.2}$) and lower gas depletion times ($23\pm2$ Myr and $27\pm4$ Myr).

It has been argued in recent times that there is no bimodality in the $\alpha_{\rm CO}$ value between star-bursting SMGs and main sequence galaxies as investigated in (cite: Dunne2022). (cite: Dunne2022) reported a value of $\alpha_{\rm CO}=3.8\pm0.1 \,\rm [M_{\odot}\, pc^{-2}\, (K\, km\, s^{-1})^{-1}]$ (including a factor 1.36 to account for He). (cite: Harrington2021) similarly found $\alpha_{\rm CO}=3.4-4.2 \,\rm [M_{\odot}\, pc^{-2}\, (K\, km\, s^{-1})^{-1}]$ for lensed SMGs at $z\sim1.0-3.5$. Using the $\alpha_{\rm CO}$ value of (cite: Dunne2022), we obtained estimates for the gas mass: $\rm log(M_{\rm gas}[M_{\odot}])=11.05^{+0.04}_{-0.04}$ and $\rm log(M_{\rm gas}[M_{\odot}])=10.82^{+0.05}_{-0.06}$ for CGG-z4.a and CGG-z4.b. Compared to the two dust models, these estimates are closer to the ones using the thick dust model, though the $1\sigma$ errors overlap with both dust models. The gas mass ratios for CGG-z4.a and CGG-z4.b are $1.0^{+2.1}_{-0.5}$ and $1.2^{+2.3}_{-0.6}$ and gas depletion times are $80\pm9$ Myr and $94\pm15$ Myr, respectively. Lastly, we can estimate the gas mass from the $[\rm C_{\rm I}](1-0)$ line following (cite: Dunne2022), giving us a value of $\alpha_{\rm CI}=16.2 \pm 0.4 \,\rm [M_{\odot}\, pc^{-2}\, (K\, km\, s^{-1})^{-1}]$ for SMGs. We used the $2\sigma$ upper limit for CGG-z4.b. We estimated the gas masses for CGG-z4.a and CGG-z4.b as $\rm log(M_{\rm gas}[M_{\odot}])=11.14^{+0.09}_{-0.11}$ and $\rm log(M_{\rm gas}[M_{\odot}])<10.66$. We note that using Eq. 8 in (cite: Dunne2022) also gives consistent results for the gas mass. This results in gas mass ratios of $1.2^{+2.5}_{-0.6}$ and $<2.3$ and gas depletion times of $99\pm23$ Myr and $<69$ Myr, respectively. The estimate for CGG-z4.a is in agreement with the ones using the two dust models (with the thick dust model being closer) and an $\alpha_{\rm CO}=3.8 \,\rm [M_{\odot}\, pc^{-2}\, (K\, km\, s^{-1})^{-1}]$; whereas for CGG-z4.b, the upper limit is in a good general agreement with all the other estimates.

A summary of the different estimates is given in Table [3](#tab:Gasvalue). Apart from the upper limit based on using $[\rm C_{\rm I}](1-0)$, the ratio between the objects is consistent, with the gas mass ratio and gas depletion times essentially being the same. To constrain the estimates of M$_{\rm gas}$ better, observations of the $115\,\rm GHz$ CO(1-0) line are needed.

![image](Figures/MS.pdf) ![image](Figures/CICO43.pdf)

# Discussion

## Line ratios and ISM conditions

To investigate the physical state of CGG-z4.a and CGG-z4.b, we compare their available line ratios with public data from different types of sources. The literature sources include luminous IR galaxies (LIRGs) from (cite: Lu2017), star-forming galaxies (SFGs) from (cite: Valentino2020), SMGs from (cite: Bothwell2017; Valentino2020), QSOs from (cite: Barvainis1997; Pety2004). Figure [5](#fig:lineratios) shows the relationship between the flux ratios of r$_{\rm [CI]10/CO43}=[\rm C_{\rm I}](1-0)/CO(4-3)$ and r$_{54}=\rm CO(5-4)/\rm CO(4-3)$. The ratio r$_{\rm [CI]10/CO43}$ is a proxy for the ratio between the amount of total gas present in the galaxy and the amount of dense gas present to form stars, which, in turn, means it is indicative of the ratio between the total gas mass and the SFR. The low values of r$_{\rm CI43}$ for CGG-z4.a,b are consistent with our low estimates for the gas depletion time of the galaxies. The values of r$_{\rm CI43}$ are close to the ones that are lowest in our reference sample; namely, the two quasars Cloverleaf (cite: Barvainis1997) and PSS-2322+1944 (cite: Pety2004). However, in the case of these quasars, the detectability of molecular and neutral atomic transitions is in large part due to the high emissivity of the gas and magnification from gravitational lensing, as opposed to a high (dense) gas mass. The r$_{54}$ ratio describes the excitation state of the galaxies. However, we note that to fully characterize the galaxies, a full CO SLED should be constructed. CGG-z4.a and CGG-z4.b have relatively high values of r$_{54}$, close to the 1.56 limit for a fully thermalized gas. The high values of r$_{54}$ can indicate different gas conditions in the two galaxies, such as high temperatures, high densities, and/or high pressures.

We further attempted to investigate the gas density using a PDR model. The PDR model combines available line ratios to constrain the radiation field intensity and the hydrogen nucleus volume density. To constrain the PDR model, typically three line ratios are needed. Utilizing the Python package photodissociation region toolbox (cite: Pound2023), we found the Wolfire-Kaufman 2006 model (cite: Kaufman2006), with a constant density and solar metallicity, to have three available line ratios: r$_{\rm [CI]10/CO43}$, r$_{\rm [CI]10/CO54}$, and r$_{\rm [CI]10/I_{\rm FIR}}$. Here, $\rm I_{\rm FIR}$ is the total FIR intensity, which we have access to from the SED fitting, and (as with the SFR) we scaled to CGG-z4.a and CGG-z4.b using their ALMA $870\,\rm \mu m$ flux. We determine a value from the full SED of $\rm I_{\rm FIR,8-1000\, \mu m}=(4.35\pm0.20)\times10^{-16}\,\rm W m^{-2}$. The package was run using the built-in emcee Markov chain Monto Carlo sampler (cite: Foreman-Mackey2013), with 2000 steps and 200 walkers to sample the posterior distribution for the model parameters. For CGG-z4.a, the density is $\rm n_{\rm H}=(3.14\pm 0.67)\times10^{4}\,\rm cm^{-3}$ and radiation field $\rm G_{0}=(1.17\pm 0.49)\times10^{3}$ Habing (the local Galactic interstellar radiation field, which has a value of $1.6\times10^{-6}\,\rm W m^{-2}$). For CGG-z4.b, we only have an upper limit available for the \[CI\](1-0) line and therefore the pdr models are poorly constrained. Given the available models, we can determine that $\rm n_{\rm H}>3.0\times10^{4}\,\rm cm^{-3}$ and $\rm G_{0}>10.0$ Habing.

To make a comparison with SMGs in the literature, we used a wavelength range of $42.5-122.5\,\rm \mu m$ in the rest-frame (cite: Wardlow2017) and determined $\rm I_{\rm FIR,42.5-122.5\, \mu m}=(2.61\pm0.12)\times10^{-16}\,\rm W m^{-2}$. We obtained $\rm n_{\rm H}=(3.08\pm0.67)\times10^{4}\,\rm cm^{-3}$, $\rm G_{0}=(6.63\pm2.62)\times10^{2}$ Habing for CGG-z4.a and $\rm n_{\rm H}>3.0\times10^{4}\,\rm cm^{-3}$ and $\rm G_{0}>6.0$ Habing for CGG-z4.b. Compared to the SMGs in (cite: Wardlow2017), which have densities of $\rm n_{\rm H}\sim3\times10^{4}\,\rm cm^{-3}$ and intensities of $\rm G_{0}\sim7\times10^{3}$ Habing, CGG-z4.a has a similar density and an intensity that is slightly below their sample. It should be noted that the (cite: Wardlow2017) sample mainly consists of $z=1-3$ galaxies. Their lensed galaxy G15v2.779 at $z=4.243$ has the closest redshift to CGG-z4.a, which shows a similar $\rm I_{\rm FIR,42.5-122.5\, \mu m}$ of $2.93\times10^{-16}\,\rm W m^{-2}$ after a correction for magnification.

![](Figures/rci43r54.pdf)

## Gas depletion times

To compare the efficiency with which these galaxies form stars to test if CGG-z4.a and CCG-z4.b differ from both other SMGs and field galaxies, we compared the depletion times of the CCG-z4 galaxies with those from SPT2349-56 and the sample of $z>4$ SMGs of (cite: Jin2019; Jin2022). We compared these to the scaling relations of field samples (cite: Scoville2017; Tacconi2018; Liu2019; Kokorev2021), normalized to a redshift of $z=4.3$ and $\rm log(M_{\star}[M_{\odot}])=10.67$ (the average stellar mass of CGG-z4.a and CGG-z4.b). We use the gas depletion times estimated using the \[CI\](1-0) line for CGG-z4.a and CGG-z4.b, since it is the estimate least reliant on conversions that could have systematic uncertainties, such as the choice of dust model or the conversion from CO(4-3) to CO(1-0). From Fig. [6](#fig:tdeplvsDMS), we see that the CGG-z4.a and CGG-z4.b both have low depletion times (high SFEs) and are above the main sequence, being slightly below the field relation at $z=4.3$. CGG-z4.b appears to be more offset from the field relations than CGG-z4.a, with both being closest to the relations from (cite: Scoville2017) and (cite: Tacconi2020). When comparing with the galaxies of (cite: Jin2019; Jin2022), they appear to be following the field relation, being similarly offset from the galaxy main sequence as CGG-z4.a and CGG-z4.b and having higher gas depletion times. The GN20 protocluster galaxies follow the field relation and are close to the ones from (cite: Jin2019; Jin2022); however, it is worth noting that their gas masses were calculated using an $\alpha_{\rm CO}$ derived from a gas-to-dust mass ratio method and dynamical modeling, which differs for each object. Compared to the galaxies of SPT2349-56, both CGG-z4.a and CGG-z4.b have similar depletion times, but the galaxies of SPT2349-56 are less offset from the main sequence; therefore, they appear offset from the field relations. This offset to the field relation can be explained by multiple factors. First, the gas mass used to calculate the depletion times was estimated using a $\alpha_{\rm CO}$ numerical value of 1.0 and taken from (cite: Hill2020), where they argued in favor of the use of this value for the sake of simplicity. Since they have a mix of the main sequence and starburst galaxies, it is possible that some of them should instead be using a $\alpha_{\rm CO}$ numerical value of $\sim4$ (or even higher) due to the low metallicity of main sequence galaxies at high-z (i.e., the evolution of mass-metallicity relation and the dependence of $\alpha_{\rm CO}$ versus metallicity), which would place the galaxies closer to the field relations. Secondly, it is possible that the stellar masses of (cite: Hill2020) could have a large uncertainty due to such factors as the unknown IMF and metallicity. Therefore, these values could be overestimated, resulting in an overly low offset from the (cite: Speagle2014) main sequence.

![](Figures/tdeplvsDMS.pdf)

## Onset of quenching

With the low gas depletion times (high SFE), on the order of $\sim100\,\rm Myr$ for the two dusty galaxies in CCG-z4, it is possible that they will become quiescent at $z\sim4.0$. Under the assumption that their SFE is constant, all the gas is converted into stars, and there is no gas replenishment, their final stellar masses would be $\sim10^{11}\,\rm M_{\odot}$ (with some variation, depending on the gas estimate used). This stellar mass is consistent with that of the massive quiescent galaxies in $z>3$ dense environments (cite: Kubo2021quiescent; Kubo2022quiescent; McConachie2022; Jin2024). For comparison, the large-scale structure Cosmic Vine (cite: Jin2024) at $z=3.44$ contains two massive quiescent galaxies with stellar masses close to $10^{11}\,\rm M_{\odot}$, and with star-formation histories from SED fitting suggesting they were quenched at $4 < z < 6$. The fact that one of these massive galaxies has formed outside the protocluster core region disfavors environmental quenching with the prerequisite of a virialized cluster core. (cite: Jin2024) argued that it is likely the two galaxies were quenched by merger-triggered starbursts in the past 500 Myr. In comparison, CGG-z4.a and CGG-z4.b are still in their starbursting phase at $z=4.33$. The time between $z=4.33$ and $z=4.0$ is $\approx 140\,\rm Myr$, and given their short gas depletion times it is possible for the CGG-z4 to evolve into galaxies similar to those of the Cosmic Vine. Due to the CGG-z4 galaxies’ optical/NIR dark nature, it is difficult to ascertain the morphology of the galaxies and comment on whether the galaxies have undergone a merger, similar to what is observed with galaxy A in the Cosmic Vine, where a compact bulge and tidal tail has been observed, both servings as indicators of a merger. Studying the morphology of the CGG-z4 optical/NIR galaxies would require deeper photometry than what is currently available in this part of the COSMOS field.

## Comparison with literature samples

Here, we consider how CGG-z4 compares to other compact galaxy groups in the literature. As a compact galaxy group at $z\sim5.2$ (cite: Jin2023), CGG-z5 has six members within a projected area of $1.5\ensuremath{''}\times3\ensuremath{''}$ (10$\times$20 kpc$^2$), which is more compact compared to the 13 members of CGG-z4 that are over a projected area of $13\ensuremath{''}\times31\ensuremath{''}$ ($89\times209\,\rm kpc^2$). The galaxies of CGG-z5 have low stellar masses and SFRs, which is in line with the low mass and low SFR galaxies in CGG-z4. The galaxies of CGG-z5 also appear to have lower A$_{\rm V}$’s ($\approx0.38$), higher metallicities ($\approx0.54\,\rm Z_{\odot}$), and slightly higher ages ($\approx0.14\,\rm Gyr$) to those in CGG-z4. CGG-z5 is expected to merge and grow into a $\rm log(M/M_{\rm \odot})\sim10.7$ galaxy at $z\sim4$ with a merging timescale of $\sim400\,\rm Myr$ when comparing with similar galaxies to CGG-z5 in the EAGLE simulation (cite: Crain2015; Schaye2015).

The compact group HPC1001 at $z=3.61$ (cite: Sillassen2022) has a similar total mass and $\sim1/3$ the SFR to CGG-z4, but a higher number density, with ten total members and eight members within $10\ensuremath{''}\times10\ensuremath{''}$ ($70\times70\,\rm kpc^2$). Comparing the most massive galaxy in the group, HPC1001.b (with a mass of $10^{11}\,\rm M_{\odot}$) to CGG-z4.a and CGG-z4.b, it is placed $\times3$ below the main sequence at $z=3.7$; whereas the two galaxies in CGG-z4 are $\times6$ and $\times4.5$ above the main sequence, respectively, at $z=4.3$. Utilizing a dust-to-gas mass ratio of 1:100, HPC1001.b has a gas mass ratio of $\rm M_{gas}/M_{\star}=0.2\pm0.1$. Nonetheless, their gas depletion timescales are comparable, $200\,\rm Myr$ for HPC1001.b and $\approx100\,\rm Myr$ for the CGG-z4 galaxies, with some variation depending on the method used, with the exception being the method using a $\alpha_{\rm CO}$ numerical value of 0.8.

A group that appears to have similar galaxies to CGG-z4 is the star-bursting galaxy group AzTEC5 at $z\sim3.6$ containing four members within $5\ensuremath{''}\times5\ensuremath{''}$ (cite: Guijarro2018). AzTEC5-1,2 have ALMA 870$\,\rm \mu m$ counterparts with SFRs and dust masses on a similar level to CGG-z4.a,b, with the ratio between the two galaxy pairs even being similar. Given that the stellar mass of CGG-z4.b is likely overestimated, the ratios of the stellar mass may also be similar; however, in the case of AzTEC5, it is the less actively star-forming galaxy AzTEC5-1 that has the higher stellar mass.

A protocluster found close to the redshift of CCG-z4 is GN20 at $z=4.05$ (cite: Tan2014). The structure contains the GN20 SMG, which is one of the brightest sources in the GOODS-N field, as well as two additional SMGs, GN20.2a and GN20.2b, located within $\sim25\ensuremath{''}$(projected $170\,\rm kpc$) of GN20. Much like CCG-z4, the GN20 galaxies are all starburst with large amounts of molecular gas surrounded by 14 B-band dropout galaxies within $25\ensuremath{''}$ of GN20. Their gas depletion times are similar to CGG-z4 (at least when comparing their CO estimates of $\sim200\,\rm Myr$). While the CGG-z4 galaxies are optical/NIR dark, the GN20 galaxies do have counterparts, although they appear offset from the sub-mm emission.

We also compare CGG-z4 to the $z=4.3$ protocluster SPT2349-56. The protocluster has a 130 kpc core region that contains 14 star-forming (total $\rm SFR \sim 5000\, M_{\odot} yr^{-1}$) and massive galaxies ($\rm M_{\star} \sim 10^{10}\, M_{\odot}$) (cite: Miller2018; Hill2020; Hill2022). The size of the structure and number of sources in the core are comparable to CGG-z4, but the SPT sources are all highly star-forming and detected in either CO(4-3) or \[CII\] emission. The gas masses of CGG-z4.a and CGG-z4.b are slightly higher compared to the SPT galaxies, with ranges between $\rm 9.30<log(M_{\rm gas}[M_{\odot}])<10.88$, while the stellar masses are comparable with ranges between $\rm 10.08<log(M_{\rm gas}[M_{\odot}])<11.35$. While the gas mass ratios are generally lower for the SPT galaxies, ranging from $0.06-0.77$, their gas depletion times are similar to the CGG-z4 galaxies, ranging from $\rm 43\, Myr-119\, Myr$.

## Comparison with simulations

To understand how CGG-z4 would evolve with time, we compare it to massive structures in simulations with similar dark matter halo mass, $\rm log(M_{\rm DM}[M_{\rm \odot}])=12.8\pm0.4$. Comparing with the curves of (cite: Chiang2013) for the most massive progenitor of present-day clusters in a cluster halo merger tree, we find that CGG-z4 is expected to grow into a Virgo- or Coma-like cluster over the next 10 billion years. It should be noted that halo mass estimates can vary greatly between different models (compare the different estimates in Sect. [4.3](#sec:halo mass)) due to the different assumptions that go into estimating the dark matter halo mass. Given these caveats, a conservative prediction would be that CGG-z4 is likely to grow into a $\rm log(M_{\rm DM}[M_{\rm \odot}])>14.0$ by $z=0$. The presence of highly star-forming galaxies, with large amounts of dense gas in a compact environment, aligns with what we expect from a protocluster in its growing phase at $z>3$ (cite: Shimakawa2018). In the case that CGG-z4 will go on to form a galaxy cluster, we attempt to assess the fate of the two most massive galaxies, CGG-z4.a and CGG-z4.b, by making a comparison with the TNG300 simulation (cite: Pillepich2018TNG300). (cite: Taborda2023) selected 280 systems with $M_{200}>10^{14}\,\rm M_\odot$ at $z=0$ in the TNG300 simulation and traced their progenitors and proto-BCGs at high redshift. Using the results of BCG progenitors by (cite: Taborda2023), the BCG stellar masses at $z=4.3$ are expected to be on the order of $\rm log(M_{\rm BCG}[M_{\odot}])=10.5^{+0.7}_{-0.9}$, consistent with the stellar masses of CGG-z4.a and CGG-z4.b. On the other hand, the halo mass of CGG-z4 $\rm log(M_{DM}[M_{\odot}])=12.8\pm0.4$ is above the statistical mass $\rm log(M_{200}[M_{\odot}])=12.3^{+0.3}_{-0.5}$ of the clusters at $z\sim4$. These comparisons support the idea that CGG-z4.a and CGG-z4.b are BCGs undergoing formation in a massive cluster.

# Conclusions

Thanks to the use of ALMA and ancillary data in the COSMOS field, we have discovered a compact galaxy group, CGG-z4, hosting two optically/NIR dark galaxies at z=4.3. We report the following conclusions:

1.  CCG-z4 contains two optically/NIR dark galaxies with spectroscopic redshifts at $z=4.3$ and 11 optical/NIR-detected candidate members, with photometric redshifts at $4.0<z<4.6$. The galaxies are spread out over a projected area of $13\ensuremath{''}\times31\ensuremath{''}$ ($89\times209\,\rm kpc^2$).

2.  The two optically/NIR dark galaxies, CGG-z4.a and CGG-z4.b, both have robust detections of CO(5-4) and CO(4-3) emission from ALMA 3mm line scans. CGG-z4.a has a detection of \[CI\](1-0) emission, while CGG-z4.b has a detection of H$_2$O($1_{1,0}-1_{0,1}$) in absorption. We performed spectral stacking of all the optically/NIR-detected galaxies in CGG-z4 and found no definitive detection of spectral lines at the 2$\sigma$ level.

3.  Using dust continuum, CO, and CI lines as gas tracers, we found CGG-z4.a and CGG-z4.b are starburst galaxies with large amount of gas reservoirs (log($\rm M_{\rm gas}[M_{\odot}]$)$\sim11.0$), massive stellar masses (log($\rm M_{\rm \star}[M_{\odot}]$)$\sim10.7$), and short gas depletion times ($\sim100\,\rm Myr$).

4.  We compared the line ratios of CGG-z4.a and CGG-z4.b with literature sample and found the ratio $\rm r_{54}$ is close to the thermalization, while $\rm r_{CI43}$ is among the lowest values compared to galaxies from the literature, indicating a high excitation of the ISM and efficient star formation.

5.  The high SFEs in CGG-z4.a and CGG-z4.b suggest the onset of quenching. Assuming all of the gas reservoirs are converted to stars under the current SFR, these galaxies would grow $\sim2\times$ their stellar masses up to $\sim10^{11}\,\rm M_\odot$ and would enter a quiescent phase at $z\sim4.0$, which would be similar to massive quiescent galaxies found in other overdense structures at $z>3$.

6.  We used multiple approaches to estimate the dark matter halo mass of CGG-z4 and found a best estimate of log($\rm M_{\rm DM}[M_{\odot}]$)$=12.8\pm0.4$. Comparisons with the simulations suggest that CGG-z4 is a forming protocluster, which is likely to form a cluster with $\rm M>10^{14}\, M_\odot$ by $z\sim0$, and the two massive dusty galaxies will form BCGs in the cluster.

Spectroscopic follow-up of the nearby optically/NIR detected galaxies in CGG-z4 would further improve the completeness of the membership. JWST follow-up would also robustly constrain the stellar mass of optically/NIR dark galaxies, and further ALMA \[CII\] observations would be the key to unveiling the inter-group medium and allow us to assess the dynamic state of this structure.

# Acknowledgements

The Cosmic Dawn Center (DAWN) is funded by the Danish National Research Foundation under grant No. 140. SJ and ML acknowledge the financial support from the European Union’s Horizon Europe research and innovation program under the Marie Skłodowska-Curie grant agreement No. 101060888 and 101107795. JH acknowledges support from the ERC Consolidator Grant 101088676 (VOYAJ). This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00463.S, ADS/JAO.ALMA#2021.1.00246.S, ADS/JAO.ALMA#2022.1.00884.S. ALMA is a partnership of ESO (representing its member states), NSF (USA), and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We acknowledge the following open-source software packages used in the analysis: Astropy (cite: AstropyCollaboration2013), Matplotlib (cite: Hunter2007), Numpy (cite: Harris2020), Scipy (cite: Virtanen2020), Uncertainties: a Python package for calculations with uncertainties, Eric O. Lebigot, <http://pythonhosted.org/uncertainties/>.

147 natexlab

(ref: Alaghband-Zadeh2013) Alaghband-Zadeh, S., Chapman, S. C., Swinbank, A. M., et al. 2013, [MNRAS](http://dx.doi.org/10.1093/mnras/stt1390), [435, 1493](https://ui.adsabs.harvard.edu/abs/2013MNRAS.435.1493A)

(ref: Algera2020) Algera, H. S. B., van der Vlugt, D., Hodge, J. A., et al. 2020, [ApJ](http://dx.doi.org/10.3847/1538-4357/abb77a), [903, 139](https://ui.adsabs.harvard.edu/abs/2020ApJ...903..139A)

(ref: Aravena2013) Aravena, M., Murphy, E. J., Aguirre, J. E., et al. 2013, [MNRAS](http://dx.doi.org/10.1093/mnras/stt741), [433, 498](https://ui.adsabs.harvard.edu/abs/2013MNRAS.433..498A)

(ref: AstropyCollaboration2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, [A&A](http://dx.doi.org/10.1051/0004-6361/201322068), [558, A33](https://ui.adsabs.harvard.edu/abs/2013A&A...558A..33A)

(ref: Barrufet2023) Barrufet, L., Oesch, P. A., Weibel, A., et al. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad947), [522, 449](https://ui.adsabs.harvard.edu/abs/2023MNRAS.522..449B)

(ref: Barvainis1997) Barvainis, R., Maloney, P., Antonucci, R., & Alloin, D. 1997, [ApJ](http://dx.doi.org/10.1086/304382), [484, 695](https://ui.adsabs.harvard.edu/abs/1997ApJ...484..695B)

(ref: Behroozi2013) Behroozi, P. S., Wechsler, R. H., & Conroy, C. 2013, [The Astrophysical Journal](http://dx.doi.org/10.1088/0004-637X/770/1/57), 770, 57

(ref: Benson2012) Benson, A. J., Borgani, S., De Lucia, G., Boylan-Kolchin, M., & Monaco, P. 2012, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2011.20002.x), [419, 3590](https://ui.adsabs.harvard.edu/abs/2012MNRAS.419.3590B)

(ref: Boogaard2020) Boogaard, L. A., van der Werf, P., Weiss, A., et al. 2020, [ApJ](http://dx.doi.org/10.3847/1538-4357/abb82f), [902, 109](https://ui.adsabs.harvard.edu/abs/2020ApJ...902..109B)

(ref: Bothwell2017) Bothwell, M. S., Aguirre, J. E., Aravena, M., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stw3270), [466, 2825](https://ui.adsabs.harvard.edu/abs/2017MNRAS.466.2825B)

(ref: Bothwell2013) Bothwell, M. S., Smail, I., Chapman, S. C., et al. 2013, [MNRAS](http://dx.doi.org/10.1093/mnras/sts562), [429, 3047](https://ui.adsabs.harvard.edu/abs/2013MNRAS.429.3047B)

(ref: Bourne2019) Bourne, N., Dunlop, J. S., Simpson, J. M., et al. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/sty2773), [482, 3135](https://ui.adsabs.harvard.edu/abs/2019MNRAS.482.3135B)

(ref: Brammer2008) Brammer, G. B., van Dokkum, P. G., & Coppi, P. 2008, [ApJ](http://dx.doi.org/10.1086/591786), [686, 1503](https://ui.adsabs.harvard.edu/abs/2008ApJ...686.1503B)

(ref: Brinch2024) Brinch, M., Greve, T. R., Sanders, D. B., et al. 2024, [MNRAS](http://dx.doi.org/10.1093/mnras/stad3409), [527, 6591](https://ui.adsabs.harvard.edu/abs/2024MNRAS.527.6591B)

(ref: Brinch2023) Brinch, M., Greve, T. R., Weaver, J. R., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac9d96), [943, 153](https://ui.adsabs.harvard.edu/abs/2023ApJ...943..153B)

(ref: Bruzual2003) Bruzual, G. & Charlot, S. 2003, [MNRAS](http://dx.doi.org/10.1046/j.1365-8711.2003.06897.x), [344, 1000](https://ui.adsabs.harvard.edu/abs/2003MNRAS.344.1000B)

(ref: Canameras2015) Cañameras, R., Nesvadba, N. P. H., Guery, D., et al. 2015, [A&A](http://dx.doi.org/10.1051/0004-6361/201425128), [581, A105](https://ui.adsabs.harvard.edu/abs/2015A&A...581A.105C)

(ref: Calvi2023) Calvi, R., Castignani, G., & Dannerbauer, H. 2023, [A&A](http://dx.doi.org/10.1051/0004-6361/202346200), [678, A15](https://ui.adsabs.harvard.edu/abs/2023A&A...678A..15C)

(ref: Capak2011) Capak, P. L., Riechers, D., Scoville, N. Z., et al. 2011, [Nature](http://dx.doi.org/10.1038/nature09681), [470, 233](https://ui.adsabs.harvard.edu/abs/2011Natur.470..233C)

(ref: Carilli2010) Carilli, C. L., Daddi, E., Riechers, D., et al. 2010, [ApJ](http://dx.doi.org/10.1088/0004-637X/714/2/1407), [714, 1407](https://ui.adsabs.harvard.edu/abs/2010ApJ...714.1407C)

(ref: Carnall2023) Carnall, A. C., Begley, R., McLeod, D. J., et al. 2023, [MNRAS](http://dx.doi.org/10.1093/mnrasl/slac136), [518, L45](https://ui.adsabs.harvard.edu/abs/2023MNRAS.518L..45C)

(ref: Carnall2018) Carnall, A. C., McLure, R. J., Dunlop, J. S., & Davé, R. 2018, [MNRAS](http://dx.doi.org/10.1093/mnras/sty2169), [480, 4379](https://ui.adsabs.harvard.edu/abs/2018MNRAS.480.4379C)

(ref: Casey2023) Casey, C. M., Kartaltepe, J. S., Drakos, N. E., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/acc2bc), [954, 31](https://ui.adsabs.harvard.edu/abs/2023ApJ...954...31C)

(ref: Chabrier2003) Chabrier, G. 2003, [Publications of the Astronomical Society of the Pacific](http://dx.doi.org/10.1086/376392), 115, 763

(ref: Chiang2013) Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, [ApJ](http://dx.doi.org/10.1088/0004-637X/779/2/127), [779, 127](https://ui.adsabs.harvard.edu/abs/2013ApJ...779..127C)

(ref: Chiang2017) Chiang, Y.-K., Overzier, R. A., Gebhardt, K., & Henriques, B. 2017, [ApJL](http://dx.doi.org/10.3847/2041-8213/aa7e7b), [844, L23](https://ui.adsabs.harvard.edu/abs/2017ApJ...844L..23C)

(ref: ALMAband3) Claude, S., Jiang, F., Niranjanan, P., et al. 2006, in Seventeenth International Symposium on Space Terahertz Technology, ed. A. Hedden, M. Reese, D. Santavicca, L. Frunzio, D. Prober, P. Piitz, C. Groppi, & C. Walker, [154–157](https://ui.adsabs.harvard.edu/abs/2006stt..conf..154C)

(ref: Cooper2022) Cooper, O. R., Casey, C. M., Zavala, J. A., et al. 2022, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac616d), [930, 32](https://ui.adsabs.harvard.edu/abs/2022ApJ...930...32C)

(ref: Cox2011) Cox, P., Krips, M., Neri, R., et al. 2011, [ApJ](http://dx.doi.org/10.1088/0004-637X/740/2/63), [740, 63](https://ui.adsabs.harvard.edu/abs/2011ApJ...740...63C)

(ref: Crain2015) Crain, R. A., Schaye, J., Bower, R. G., et al. 2015, [MNRAS](http://dx.doi.org/10.1093/mnras/stv725), [450, 1937](https://ui.adsabs.harvard.edu/abs/2015MNRAS.450.1937C)

(ref: Daddi2009) Daddi, E., Dannerbauer, H., Stern, D., et al. 2009, [ApJ](http://dx.doi.org/10.1088/0004-637X/694/2/1517), [694, 1517](https://ui.adsabs.harvard.edu/abs/2009ApJ...694.1517D)

(ref: Daddi2022) Daddi, E., Rich, R. M., Valentino, F., et al. 2022, [ApJL](http://dx.doi.org/10.3847/2041-8213/ac531f), [926, L21](https://ui.adsabs.harvard.edu/abs/2022ApJ...926L..21D)

(ref: Daddi2021) Daddi, E., Valentino, F., Rich, R. M., et al. 2021, [A&A](http://dx.doi.org/10.1051/0004-6361/202038700), [649, A78](https://ui.adsabs.harvard.edu/abs/2021A&A...649A..78D)

(ref: Dannerbauer2014) Dannerbauer, H., Kurk, J. D., De Breuck, C., et al. 2014, [A&A](http://dx.doi.org/10.1051/0004-6361/201423771), [570, A55](https://ui.adsabs.harvard.edu/abs/2014A&A...570A..55D)

(ref: Santos2017) Dı́az-Santos, T., Armus, L., Charmandaris, V., et al. 2017, [ApJ](http://dx.doi.org/10.3847/1538-4357/aa81d7), [846, 32](https://ui.adsabs.harvard.edu/abs/2017ApJ...846...32D)

(ref: Diaz-Santos2018) Dı́az-Santos, T., Assef, R. J., Blain, A. W., et al. 2018, [Science](http://dx.doi.org/10.1126/science.aap7605), [362, 1034](https://ui.adsabs.harvard.edu/abs/2018Sci...362.1034D)

(ref: Donevski2020) Donevski, D., Lapi, A., Małek, K., et al. 2020, [A&A](http://dx.doi.org/10.1051/0004-6361/202038405), [644, A144](https://ui.adsabs.harvard.edu/abs/2020A&A...644A.144D)

(ref: Downes1998) Downes, D. & Solomon, P. M. 1998, [ApJ](http://dx.doi.org/10.1086/306339), [507, 615](https://ui.adsabs.harvard.edu/abs/1998ApJ...507..615D)

(ref: Draine2007) Draine, B. T. & Li, A. 2007, [ApJ](http://dx.doi.org/10.1086/511055), [657, 810](https://ui.adsabs.harvard.edu/abs/2007ApJ...657..810D)

(ref: Dunne2022) Dunne, L., Maddox, S. J., Papadopoulos, P. P., Ivison, R. J., & Gomez, H. L. 2022, [MNRAS](http://dx.doi.org/10.1093/mnras/stac2098), [517, 962](https://ui.adsabs.harvard.edu/abs/2022MNRAS.517..962D)

(ref: Dunne2021) Dunne, L., Maddox, S. J., Vlahakis, C., & Gomez, H. L. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/staa3526), [501, 2573](https://ui.adsabs.harvard.edu/abs/2021MNRAS.501.2573D)

(ref: Falstad2021) Falstad, N., Aalto, S., König, S., et al. 2021, [A&A](http://dx.doi.org/10.1051/0004-6361/202039291), [649, A105](https://ui.adsabs.harvard.edu/abs/2021A&A...649A.105F)

(ref: Foreman-Mackey2013) Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, [PASP](http://dx.doi.org/10.1086/670067), [125, 306](https://ui.adsabs.harvard.edu/abs/2013PASP..125..306F)

(ref: Genzel2015) Genzel, R., Tacconi, L. J., Lutz, D., et al. 2015, [ApJ](http://dx.doi.org/10.1088/0004-637X/800/1/20), [800, 20](https://ui.adsabs.harvard.edu/abs/2015ApJ...800...20G)

(ref: Gildas2013) Gildas Team. 2013, GILDAS: Grenoble Image and Line Data Analysis Software, Astrophysics Source Code Library, record ascl:1305.010

(ref: Ginolfi2022) Ginolfi, M., Piconcelli, E., Zappacosta, L., et al. 2022, [Nature Communications](http://dx.doi.org/10.1038/s41467-022-32297-x), [13, 4574](https://ui.adsabs.harvard.edu/abs/2022NatCo..13.4574G)

(ref: Guijarro2022) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202141615), [658, A43](https://ui.adsabs.harvard.edu/abs/2022A&A...658A..43G)

(ref: Guijarro2018) Gómez-Guijarro, C., Toft, S., Karim, A., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aab206), [856, 121](https://ui.adsabs.harvard.edu/abs/2018ApJ...856..121G)

(ref: Gottumukkala2024) Gottumukkala, R., Barrufet, L., Oesch, P. A., et al. 2024, [MNRAS](http://dx.doi.org/10.1093/mnras/stae754), [530, 966](https://ui.adsabs.harvard.edu/abs/2024MNRAS.530..966G)

(ref: Harikane2019) Harikane, Y., Ouchi, M., Ono, Y., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab2cd5), [883, 142](https://ui.adsabs.harvard.edu/abs/2019ApJ...883..142H)

(ref: Harrington2021) Harrington, K. C., Weiss, A., Yun, M. S., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/abcc01), [908, 95](https://ui.adsabs.harvard.edu/abs/2021ApJ...908...95H)

(ref: Harrington2016) Harrington, K. C., Yun, M. S., Cybulski, R., et al. 2016, [MNRAS](http://dx.doi.org/10.1093/mnras/stw614), [458, 4383](https://ui.adsabs.harvard.edu/abs/2016MNRAS.458.4383H)

(ref: Harris2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, [Nature](http://dx.doi.org/10.1038/s41586-020-2649-2), [585, 357](https://ui.adsabs.harvard.edu/abs/2020Natur.585..357H)

(ref: Heintz2023) Heintz, K. E., Giménez-Arteaga, C., Fujimoto, S., et al. 2023, [ApJL](http://dx.doi.org/10.3847/2041-8213/acb2cf), [944, L30](https://ui.adsabs.harvard.edu/abs/2023ApJ...944L..30H)

(ref: Higdon2008) Higdon, J. L., Higdon, S. J. U., Willner, S. P., et al. 2008, [ApJ](http://dx.doi.org/10.1086/591069), [688, 885](https://ui.adsabs.harvard.edu/abs/2008ApJ...688..885H)

(ref: Hill2022) Hill, R., Chapman, S., Phadke, K. A., et al. 2022, [MNRAS](http://dx.doi.org/10.1093/mnras/stab3539), [512, 4352](https://ui.adsabs.harvard.edu/abs/2022MNRAS.512.4352H)

(ref: Hill2020) Hill, R., Chapman, S., Scott, D., et al. 2020, [MNRAS](http://dx.doi.org/10.1093/mnras/staa1275), [495, 3124](https://ui.adsabs.harvard.edu/abs/2020MNRAS.495.3124H)

(ref: Hirschmann2012) Hirschmann, M., Naab, T., Somerville, R. S., Burkert, A., & Oser, L. 2012, [Monthly Notices of the Royal Astronomical Society](http://dx.doi.org/10.1111/j.1365-2966.2011.19961.x), 419, 3200

(ref: Hopkins2009) Hopkins, P. F., Somerville, R. S., Cox, T. J., et al. 2009, [Monthly Notices of the Royal Astronomical Society](http://dx.doi.org/10.1111/j.1365-2966.2009.14983.x), 397, 802

(ref: Hughes2017) Hughes, T. M., Ibar, E., Villanueva, V., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnrasl/slx033), [468, L103](https://ui.adsabs.harvard.edu/abs/2017MNRAS.468L.103H)

(ref: Hunter2007) Hunter, J. D. 2007, [Computing in Science and Engineering](http://dx.doi.org/10.1109/MCSE.2007.55), [9, 90](https://ui.adsabs.harvard.edu/abs/2007CSE.....9...90H)

(ref: Jin2018) Jin, S., Daddi, E., Liu, D., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aad4af), [864, 56](https://ui.adsabs.harvard.edu/abs/2018ApJ...864...56J)

(ref: Jin2019) Jin, S., Daddi, E., Magdis, G. E., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab55d6), [887, 144](https://ui.adsabs.harvard.edu/abs/2019ApJ...887..144J)

(ref: Jin2022) Jin, S., Daddi, E., Magdis, G. E., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202243341), [665, A3](https://ui.adsabs.harvard.edu/abs/2022A&A...665A...3J)

(ref: Jin2024cosbo7) Jin, S., Sillassen, N. B., Hodge, J., et al. 2024a, [A&A](http://dx.doi.org/10.1051/0004-6361/202451445), [690, L16](https://ui.adsabs.harvard.edu/abs/2024A&A...690L..16J)

(ref: Jin2024) Jin, S., Sillassen, N. B., Magdis, G. E., et al. 2024b, [A&A](http://dx.doi.org/10.1051/0004-6361/202348540), [683, L4](https://ui.adsabs.harvard.edu/abs/2024A&A...683L...4J)

(ref: Jin2023) Jin, S., Sillassen, N. B., Magdis, G. E., et al. 2023, [A&A](http://dx.doi.org/10.1051/0004-6361/202245724), [670, L11](https://ui.adsabs.harvard.edu/abs/2023A&A...670L..11J)

(ref: Jones2017) Jones, S. F., Blain, A. W., Assef, R. J., et al. 2017, [MNRAS](http://dx.doi.org/10.1093/mnras/stx1141), [469, 4565](https://ui.adsabs.harvard.edu/abs/2017MNRAS.469.4565J)

(ref: Kaufman2006) Kaufman, M. J., Wolfire, M. G., & Hollenbach, D. J. 2006, [ApJ](http://dx.doi.org/10.1086/503596), [644, 283](https://ui.adsabs.harvard.edu/abs/2006ApJ...644..283K)

(ref: Kennicutt1998) Kennicutt, Robert C., J. 1998, [ARA&A](http://dx.doi.org/10.1146/annurev.astro.36.1.189), [36, 189](https://ui.adsabs.harvard.edu/abs/1998ARA&A..36..189K)

(ref: Kokorev2023HSTdark) Kokorev, V., Jin, S., Magdis, G. E., et al. 2023, [ApJL](http://dx.doi.org/10.3847/2041-8213/acbd9d), [945, L25](https://ui.adsabs.harvard.edu/abs/2023ApJ...945L..25K)

(ref: Kokorev2021) Kokorev, V. I., Magdis, G. E., Davidzon, I., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac18ce), [921, 40](https://ui.adsabs.harvard.edu/abs/2021ApJ...921...40K)

(ref: Kubo2021quiescent) Kubo, M., Umehata, H., Matsuda, Y., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac0cf8), [919, 6](https://ui.adsabs.harvard.edu/abs/2021ApJ...919....6K)

(ref: Kubo2022quiescent) Kubo, M., Umehata, H., Matsuda, Y., et al. 2022, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac7f2d), [935, 89](https://ui.adsabs.harvard.edu/abs/2022ApJ...935...89K)

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, [ApJS](http://dx.doi.org/10.3847/0067-0049/224/2/24), [224, 24](https://ui.adsabs.harvard.edu/abs/2016ApJS..224...24L)

(ref: Lamperti2019) Lamperti, I., Saintonge, A., De Looze, I., et al. 2019, [MNRAS](http://dx.doi.org/10.1093/mnras/stz2311), [489, 4389](https://ui.adsabs.harvard.edu/abs/2019MNRAS.489.4389L)

(ref: LeFloch2009) Le Floc’h, E., Aussel, H., Ilbert, O., et al. 2009, [ApJ](http://dx.doi.org/10.1088/0004-637X/703/1/222), [703, 222](http://adsabs.harvard.edu/abs/2009ApJ...703..222L)

(ref: Lee2021) Lee, M. M., Tanaka, I., Iono, D., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/abdbb5), [909, 181](https://ui.adsabs.harvard.edu/abs/2021ApJ...909..181L)

(ref: Lestrade2011) Lestrade, J.-F., Carilli, C. L., Thanjavur, K., et al. 2011, [ApJL](http://dx.doi.org/10.1088/2041-8205/739/1/L30), [739, L30](https://ui.adsabs.harvard.edu/abs/2011ApJ...739L..30L)

(ref: Lewis2018) Lewis, A. J. R., Ivison, R. J., Best, P. N., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aacc25), 862, 96

(ref: Liu2020) Liu, D. 2020, michi2: SED and SLED fitting tool, Astrophysics Source Code Library, record ascl:2005.002

(ref: Liu2018) Liu, D., Daddi, E., Dickinson, M., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aaa600), [853, 172](https://ui.adsabs.harvard.edu/abs/2018ApJ...853..172L)

(ref: Liu2021) Liu, D., Daddi, E., Schinnerer, E., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/abd801), [909, 56](https://ui.adsabs.harvard.edu/abs/2021ApJ...909...56L)

(ref: Liu2019) Liu, D., Schinnerer, E., Groves, B., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab578d), [887, 235](https://ui.adsabs.harvard.edu/abs/2019ApJ...887..235L)

(ref: Lu2017) Lu, N., Zhao, Y., Dı́az-Santos, T., et al. 2017, [ApJS](http://dx.doi.org/10.3847/1538-4365/aa6476), [230, 1](https://ui.adsabs.harvard.edu/abs/2017ApJS..230....1L)

(ref: Lutz2011PACS) Lutz, D., Poglitsch, A., Altieri, B., et al. 2011, [A&A](http://dx.doi.org/10.1051/0004-6361/201117107), [532, A90](https://ui.adsabs.harvard.edu/abs/2011A&A...532A..90L)

(ref: Magdis2012) Magdis, G. E., Daddi, E., Béthermin, M., et al. 2012, [ApJ](http://dx.doi.org/10.1088/0004-637X/760/1/6), [760, 6](https://ui.adsabs.harvard.edu/abs/2012ApJ...760....6M)

(ref: Magnelli2015) Magnelli, B., Ivison, R. J., Lutz, D., et al. 2015, [A&A](http://dx.doi.org/10.1051/0004-6361/201424937), [573, A45](https://ui.adsabs.harvard.edu/abs/2015A&A...573A..45M)

(ref: ALMAband7-2005) Mahieu, S., Lazareff, B., Maier, D., et al. 2005, in Sixteenth International Symposium on Space Terahertz Technology, [99–104](https://ui.adsabs.harvard.edu/abs/2005stt..conf...99M)

(ref: ALMAband7-2006) Maier, D., Barbier, A., Lazareff, B., & Schuster, K. F. 2005, in Sixteenth International Symposium on Space Terahertz Technology, [428–431](https://ui.adsabs.harvard.edu/abs/2005stt..conf..428M)

(ref: Marrone2018) Marrone, D. P., Spilker, J. S., Hayward, C. C., et al. 2018, [Nature](http://dx.doi.org/10.1038/nature24629), [553, 51](https://ui.adsabs.harvard.edu/abs/2018Natur.553...51M)

(ref: McConachie2022) McConachie, I., Wilson, G., Forrest, B., et al. 2022, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac2b9f), [926, 37](https://ui.adsabs.harvard.edu/abs/2022ApJ...926...37M)

(ref: CASA) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, [127](https://ui.adsabs.harvard.edu/abs/2007ASPC..376..127M)

(ref: Miller2018) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, [Nature](http://dx.doi.org/10.1038/s41586-018-0025-2), [556, 469](https://ui.adsabs.harvard.edu/abs/2018Natur.556..469M)

(ref: Taborda2023) Montenegro-Taborda, D., Rodriguez-Gomez, V., Pillepich, A., et al. 2023, [MNRAS](http://dx.doi.org/10.1093/mnras/stad586), [521, 800](https://ui.adsabs.harvard.edu/abs/2023MNRAS.521..800M)

(ref: Mullaney2011) Mullaney, J. R., Alexander, D. M., Goulding, A. D., & Hickox, R. C. 2011, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2011.18448.x), [414, 1082](https://ui.adsabs.harvard.edu/abs/2011MNRAS.414.1082M)

(ref: Muzzin2013) Muzzin, A., Marchesini, D., Stefanon, M., et al. 2013, [ApJ](http://dx.doi.org/10.1088/0004-637X/777/1/18), [777, 18](http://adsabs.harvard.edu/abs/2013ApJ...777...18M)

(ref: Narayanan2014) Narayanan, D. & Krumholz, M. R. 2014, [MNRAS](http://dx.doi.org/10.1093/mnras/stu834), [442, 1411](https://ui.adsabs.harvard.edu/abs/2014MNRAS.442.1411N)

(ref: Newville2014) Newville, M., Stensitzki, T., Allen, D. B., & Ingargiola, A. 2014, LMFIT: Non-Linear Least-Square Minimization and Curve-Fitting for Python

(ref: Oke1974) Oke, J. B. 1974, [ApJS](http://dx.doi.org/10.1086/190287), [27, 21](https://ui.adsabs.harvard.edu/abs/1974ApJS...27...21O)

(ref: Oliver2012SPIRE) Oliver, S. J., Bock, J., Altieri, B., et al. 2012, [MNRAS](http://dx.doi.org/10.1111/j.1365-2966.2012.20912.x), [424, 1614](https://ui.adsabs.harvard.edu/abs/2012MNRAS.424.1614O)

(ref: Omont2013) Omont, A., Yang, C., Cox, P., et al. 2013, [A&A](http://dx.doi.org/10.1051/0004-6361/201220811), [551, A115](https://ui.adsabs.harvard.edu/abs/2013A&A...551A.115O)

(ref: Oser2010) Oser, L., Ostriker, J. P., Naab, T., Johansson, P. H., & Burkert, A. 2010, [ApJ](http://dx.doi.org/10.1088/0004-637X/725/2/2312), [725, 2312](https://ui.adsabs.harvard.edu/abs/2010ApJ...725.2312O)

(ref: Oteo2018) Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aaa1f1), [856, 72](https://ui.adsabs.harvard.edu/abs/2018ApJ...856...72O)

(ref: Overzier2016) Overzier, R. A. 2016, [A&ARv](http://dx.doi.org/10.1007/s00159-016-0100-3), [24, 14](https://ui.adsabs.harvard.edu/abs/2016A&ARv..24...14O)

(ref: Pety2004) Pety, J., Beelen, A., Cox, P., et al. 2004, [A&A](http://dx.doi.org/10.1051/0004-6361:200400096), [428, L21](https://ui.adsabs.harvard.edu/abs/2004A&A...428L..21P)

(ref: Pillepich2018TNG300) Pillepich, A., Nelson, D., Hernquist, L., et al. 2018, [MNRAS](http://dx.doi.org/10.1093/mnras/stx3112), [475, 648](https://ui.adsabs.harvard.edu/abs/2018MNRAS.475..648P)

(ref: Pound2023) Pound, M. W. & Wolfire, M. G. 2023, [AJ](http://dx.doi.org/10.3847/1538-3881/ac9b1f), [165, 25](https://ui.adsabs.harvard.edu/abs/2023AJ....165...25P)

(ref: Riechers2022) Riechers, D. A., Weiss, A., Walter, F., et al. 2022, [Nature](http://dx.doi.org/10.1038/s41586-021-04294-5), [602, 58](https://ui.adsabs.harvard.edu/abs/2022Natur.602...58R)

(ref: Salim2018) Salim, S., Boquien, M., & Lee, J. C. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aabf3c), [859, 11](https://ui.adsabs.harvard.edu/abs/2018ApJ...859...11S)

(ref: Schaye2015) Schaye, J., Crain, R. A., Bower, R. G., et al. 2015, [MNRAS](http://dx.doi.org/10.1093/mnras/stu2058), [446, 521](https://ui.adsabs.harvard.edu/abs/2015MNRAS.446..521S)

(ref: Schlafly2011) Schlafly, E. F. & Finkbeiner, D. P. 2011, [ApJ](http://dx.doi.org/10.1088/0004-637X/737/2/103), [737, 103](https://ui.adsabs.harvard.edu/abs/2011ApJ...737..103S)

(ref: Schmidt1959) Schmidt, M. 1959, [ApJ](http://dx.doi.org/10.1086/146614), [129, 243](https://ui.adsabs.harvard.edu/abs/1959ApJ...129..243S)

(ref: Schreiber2015) Schreiber, C., Pannella, M., Elbaz, D., et al. 2015, [A&A](http://dx.doi.org/10.1051/0004-6361/201425017), [575, A74](https://ui.adsabs.harvard.edu/abs/2015A&A...575A..74S)

(ref: Scoville2013) Scoville, N., Arnouts, S., Aussel, H., et al. 2013, [ApJS](http://dx.doi.org/10.1088/0067-0049/206/1/3), [206, 3](https://ui.adsabs.harvard.edu/abs/2013ApJS..206....3S)

(ref: Scoville2017) Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, [ApJ](http://dx.doi.org/10.3847/1538-4357/aa61a0), [837, 150](https://ui.adsabs.harvard.edu/abs/2017ApJ...837..150S)

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, [ApJ](http://dx.doi.org/10.3847/0004-637X/820/2/83), [820, 83](https://ui.adsabs.harvard.edu/abs/2016ApJ...820...83S)

(ref: Shimakawa2018) Shimakawa, R., Koyama, Y., Röttgering, H. J. A., et al. 2018, [MNRAS](http://dx.doi.org/10.1093/mnras/sty2618), [481, 5630](https://ui.adsabs.harvard.edu/abs/2018MNRAS.481.5630S)

(ref: Shu2022) Shu, X., Yang, L., Liu, D., et al. 2022, [ApJ](http://dx.doi.org/10.3847/1538-4357/ac3de5), [926, 155](https://ui.adsabs.harvard.edu/abs/2022ApJ...926..155S)

(ref: Shuntov2022) Shuntov, M., McCracken, H. J., Gavazzi, R., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202243136), [664, A61](https://ui.adsabs.harvard.edu/abs/2022A&A...664A..61S)

(ref: Sillassen2024) Sillassen, N. B., Jin, S., Magdis, G. E., et al. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202450760), [690, A55](https://ui.adsabs.harvard.edu/abs/2024A&A...690A..55S)

(ref: Sillassen2022) Sillassen, N. B., Jin, S., Magdis, G. E., et al. 2022, [A&A](http://dx.doi.org/10.1051/0004-6361/202244661), [665, L7](https://ui.adsabs.harvard.edu/abs/2022A&A...665L...7S)

(ref: Simpson2019) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab23ff), [880, 43](https://ui.adsabs.harvard.edu/abs/2019ApJ...880...43S)

(ref: Smail2021) Smail, I., Dudzevičiūtė, U., Stach, S. M., et al. 2021, [MNRAS](http://dx.doi.org/10.1093/mnras/stab283), [502, 3426](https://ui.adsabs.harvard.edu/abs/2021MNRAS.502.3426S)

(ref: Smail1999) Smail, I., Morrison, G., Gray, M. E., et al. 1999, [ApJ](http://dx.doi.org/10.1086/307934), [525, 609](https://ui.adsabs.harvard.edu/abs/1999ApJ...525..609S)

(ref: Smolcic2017) Smolčić, V., Novak, M., Bondi, M., et al. 2017, [A&A](http://dx.doi.org/10.1051/0004-6361/201628704), [602, A1](https://ui.adsabs.harvard.edu/abs/2017A&A...602A...1S)

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, [ApJS](http://dx.doi.org/10.1088/0067-0049/214/2/15), [214, 15](https://ui.adsabs.harvard.edu/abs/2014ApJS..214...15S)

(ref: Spilker2014) Spilker, J. S., Marrone, D. P., Aguirre, J. E., et al. 2014, [ApJ](http://dx.doi.org/10.1088/0004-637X/785/2/149), [785, 149](https://ui.adsabs.harvard.edu/abs/2014ApJ...785..149S)

(ref: Springel2005) Springel, V., White, S. D. M., Jenkins, A., et al. 2005, [Nature](http://dx.doi.org/10.1038/nature03597), [435, 629](https://ui.adsabs.harvard.edu/abs/2005Natur.435..629S)

(ref: Tacconi2018) Tacconi, L. J., Genzel, R., Saintonge, A., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aaa4b4), [853, 179](https://ui.adsabs.harvard.edu/abs/2018ApJ...853..179T)

(ref: Tacconi2008) Tacconi, L. J., Genzel, R., Smail, I., et al. 2008, [The Astrophysical Journal](http://dx.doi.org/10.1086/587168), 680, 246

(ref: Tacconi2020) Tacconi, L. J., Genzel, R., & Sternberg, A. 2020, [Annual Review of Astronomy and Astrophysics](http://dx.doi.org/https://doi.org/10.1146/annurev-astro-082812-141034), 58, 157

(ref: Talia2021) Talia, M., Cimatti, A., Giulietti, M., et al. 2021, [ApJ](http://dx.doi.org/10.3847/1538-4357/abd6e3), [909, 23](https://ui.adsabs.harvard.edu/abs/2021ApJ...909...23T)

(ref: Tan2014) Tan, Q., Daddi, E., Magdis, G., et al. 2014, [A&A](http://dx.doi.org/10.1051/0004-6361/201423905), [569, A98](https://ui.adsabs.harvard.edu/abs/2014A&A...569A..98T)

(ref: Valentino2018) Valentino, F., Magdis, G. E., Daddi, E., et al. 2018, [ApJ](http://dx.doi.org/10.3847/1538-4357/aaeb88), [869, 27](https://ui.adsabs.harvard.edu/abs/2018ApJ...869...27V)

(ref: Valentino2020) Valentino, F., Magdis, G. E., Daddi, E., et al. 2020, [ApJ](http://dx.doi.org/10.3847/1538-4357/ab6603), [890, 24](https://ui.adsabs.harvard.edu/abs/2020ApJ...890...24V)

(ref: van_der_Burg2014) van der Burg, R. F. J., Muzzin, A., Hoekstra, H., et al. 2014, [A&A](http://dx.doi.org/10.1051/0004-6361/201322771), [561, A79](https://ui.adsabs.harvard.edu/abs/2014A&A...561A..79V)

(ref: Vlugt2023) van der Vlugt, D., Hodge, J. A., Jin, S., et al. 2023, [ApJ](http://dx.doi.org/10.3847/1538-4357/acd549), [951, 131](https://ui.adsabs.harvard.edu/abs/2023ApJ...951..131V)

(ref: Virtanen2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, [Nature Methods](http://dx.doi.org/10.1038/s41592-019-0686-2), [17, 261](https://ui.adsabs.harvard.edu/abs/2020NatMe..17..261V)

(ref: Walter2012) Walter, F., Decarli, R., Carilli, C., et al. 2012, [Nature](http://dx.doi.org/10.1038/nature11073), [486, 233](https://ui.adsabs.harvard.edu/abs/2012Natur.486..233W)

(ref: Wang2016) Wang, T., Elbaz, D., Daddi, E., et al. 2016, [ApJ](http://dx.doi.org/10.3847/0004-637X/828/1/56), [828, 56](https://ui.adsabs.harvard.edu/abs/2016ApJ...828...56W)

(ref: Wang2019) Wang, T., Schreiber, C., Elbaz, D., et al. 2019, [Nature](http://dx.doi.org/10.1038/s41586-019-1452-4), [572, 211](https://ui.adsabs.harvard.edu/abs/2019Natur.572..211W)

(ref: Wardlow2017) Wardlow, J. L., Cooray, A., Osage, W., et al. 2017, [ApJ](http://dx.doi.org/10.3847/1538-4357/837/1/12), [837, 12](https://ui.adsabs.harvard.edu/abs/2017ApJ...837...12W)

(ref: Weaver2022) Weaver, J. R., Kauffmann, O. B., Ilbert, O., et al. 2022, [ApJS](http://dx.doi.org/10.3847/1538-4365/ac3078), [258, 11](https://ui.adsabs.harvard.edu/abs/2022ApJS..258...11W)

(ref: Xiao2023) Xiao, M. Y., Elbaz, D., Gómez-Guijarro, C., et al. 2023, [A&A](http://dx.doi.org/10.1051/0004-6361/202245100), [672, A18](https://ui.adsabs.harvard.edu/abs/2023A&A...672A..18X)

(ref: Yang2017) Yang, C., Omont, A., Beelen, A., et al. 2017, [A&A](http://dx.doi.org/10.1051/0004-6361/201731391), [608, A144](https://ui.adsabs.harvard.edu/abs/2017A&A...608A.144Y)

(ref: Zhou2023) Zhou, L., Wang, T., Daddi, E., et al. 2024, [A&A](http://dx.doi.org/10.1051/0004-6361/202348351), [684, A196](https://ui.adsabs.harvard.edu/abs/2024A&A...684A.196Z)

# Photometry used for combined SED fitting of CGG-z4.a+b

|  |  |  |  |  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
| ID | S$_{24\rm \mu m}$ | S$_{100\rm \mu m}$ | S$_{160\rm \mu m}$ | S$_{250\rm \mu m}$ | S$_{350\rm \mu m}$ | S$_{500\rm \mu m}$ | S$_{850\rm \mu m}$ | S$_{872\rm \mu m}$ | S$_{3\rm mm}$ | S$_{10\rm cm}$ |
|  | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] | \[mJy\] |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |
| CGG-z4.a+b | 0.022$\pm$0.010 | \<3.44 | 8.02$\pm$2.52 | 19.22$\pm$3.01 | 46.71$\pm$9.60 | 34.68$\pm$5.14 | 12.86$\pm$1.77 | 15.01$\pm$0.35 | 0.257$\pm$0.009 | 0.025$\pm$0.003 |

: Data used for SED fitting of CGG-$z4$.a,b.

Table notes: CGG-z4.a,b were fitted using the SED fitting code of (cite: Liu2020; Liu2021). Columns: (1) Name; (2) Mips 24 $\rm\mu m$; (3) PACS 100 $\rm\mu m$; (4) PACS 160 $\rm\mu m$; (5) SPIRE 250 $\rm\mu m$; (6) SPIRE 350 $\rm\mu m$; (7) SPIRE 500 $\rm\mu m$; (8) SCUBA2 850 $\rm\mu m$; (9) ALMA 872 $\rm\mu m$; (10) ALMA 3 mm; (11) VLA 10 cm.

# Bagpipes SED fits

Figures/353556_fit.pdf (47.5,32)**353556**

Figures/354768_fit.pdf (47.5,32)**354768**

Figures/355293_fit.pdf (47.5,32)**355293**

Figures/358735_fit.pdf (47.5,32)**358735**

Figures/358920_fit.pdf (47.5,32)**358920**

Figures/361346_fit.pdf (47.5,32)**361346**

Figures/362449_fit.pdf (47.5,32)**362449**

Figures/353918_fit.pdf (47.5,32)**353918**

Figures/357448_fit.pdf (47.5,32)**357448**

Figures/355779_fit.pdf (47.5,32)**355779**

Figures/361388_fit.pdf (47.5,32)**361388**

# Galaxy properties from SED fitting

|  |  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|:---|
| ID(COSMOS) | $z$ | $\log {\rm M_{\rm \star}/M_{\rm \odot}}$ | SFR | $\rm A_{\rm V}$ | Z | Age |
|  |  | \[dex\] | \[M$_{\rm \odot}$ yr$^{-1}$\] |  | \[Z$_{\rm \odot}$\] | \[Gyr\] |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) |
| Spec-z |  |  |  |  |  |  |
| CGG-z4.a | 4.331 | 10.77$^{+0.51}_{-0.49}$ | 1408$\pm86$ |  |  |  |
| CGG-z4.b | 4.324 | 10.56$^{+0.42}_{-0.26}$ | 703$\pm65$ |  |  |  |
| Photo-z |  |  |  |  |  |  |
| 353556 | 4.44$^{+0.23}_{-0.15}$ | 10.33$^{+0.15}_{-0.27}$ | 241$^{+117}_{-114}$ | 1.29$^{+0.27}_{-0.31}$ | 0.07$^{+0.32}_{-0.05}$ | 0.02$^{+0.01}_{-0.01}$ |
| 354768 | 4.37$^{+0.06}_{-0.03}$ | 9.81$^{+0.15}_{-0.20}$ | 71$^{+31}_{-27}$ | 1.31$^{+0.74}_{-0.44}$ | 0.05$^{+0.08}_{-0.04}$ | 0.01$^{+0.01}_{-0.01}$ |
| 355293 | 3.87$^{+0.20}_{-0.24}$ | 8.51$^{+0.65}_{-0.71}$ | 2$^{+4}_{-1}$ | 0.57$^{+1.22}_{-0.40}$ | 0.04$^{+0.07}_{-0.02}$ | 0.05$^{+0.22}_{-0.04}$ |
| 358735 | 4.54$^{+0.11}_{-0.16}$ | 9.28$^{+0.53}_{-0.37}$ | 12$^{+27}_{-7}$ | 1.37$^{+1.35}_{-0.90}$ | 0.53$^{+0.74}_{-0.41}$ | 0.10$^{+0.17}_{-0.07}$ |
| 358920 | 4.35$^{+0.13}_{-0.20}$ | 9.75$^{+0.12}_{-0.16}$ | 64$^{+20}_{-20}$ | 1.11$^{+0.38}_{-0.29}$ | 0.03$^{+0.06}_{-0.02}$ | 0.01$^{+0.01}_{-0.01}$ |
| 361346 | 3.90$^{+0.18}_{-0.17}$ | 9.43$^{+0.63}_{-0.17}$ | 6$^{+21}_{-2}$ | 0.46$^{+1.71}_{-0.32}$ | 0.02$^{+0.02}_{-0.01}$ | 0.38$^{+0.08}_{-0.13}$ |
| 362449 | 4.33$^{+0.18}_{-0.27}$ | $10.18^{+0.27}_{-0.25}$ | $148^{+159}_{-56}$ | $1.52^{+0.52}_{-0.41}$ | $0.20^{+0.79}_{-0.16}$ | $0.02^{+0.04}_{-0.01}$ |
| 353918 | 4.51$^{+0.16}_{-0.12}$ | $9.20^{+0.08}_{-0.11}$ | $17^{+4}_{-4}$ | $0.36^{+0.18}_{-0.10}$ | $0.02^{+0.01}_{-0.01}$ | $0.01^{+0.01}_{-0.01}$ |
| 357448 | 4.62$^{+0.10}_{-0.08}$ | $8.88^{+0.13}_{-0.21}$ | $9^{+3}_{-4}$ | $0.19^{+0.16}_{-0.09}$ | $0.05^{+0.28}_{-0.04}$ | $0.03^{+0.02}_{-0.01}$ |
| 355779 | 4.02$^{+0.15}_{-0.26}$ | $10.19^{+0.42}_{-0.59}$ | $41^{+73}_{-31}$ | $2.53^{+0.99}_{-1.33}$ | $0.03^{+0.05}_{-0.01}$ | $0.31^{+0.14}_{-0.18}$ |
| 361388 | 4.23$^{+0.09}_{-0.09}$ | 10.44$^{+0.23}_{-0.23}$ | $115^{+121}_{-55}$ | $3.01^{+0.58}_{-0.71}$ | $0.03^{+0.06}_{-0.02}$ | $0.19^{+0.20}_{-0.12}$ |
| Total |  |  |  |  |  |  |
| CGG-z4 | 4.30$^{+0.12}_{-0.14}$ | 11.29$^{+0.38}_{-0.33}$ | 2837$^{+731}_{-472}$ |  |  |  |

: SED fitting result for CGG-$z4$ group galaxies.

Table notes: CGG-z4.a,b were fitted using the MICHI2 SED fitting code of (cite: Liu2020; Liu2021) to determine the SFR. For galaxies with photometric redshift, results are the median photometric redshift from EAZY SED fitting with Classic COSMOS2020 photometry, and the remaining parameters were computed by Bagpipes at the spectroscopic redshift of CGG-z4.a, assuming a constant SFH and a (cite: Salim2018) attenuation curve. Columns: (1) Name/COSMOS2020 catalog ID; (2) Redshift; (3) The stellar mass; (4) The star formation rate; (5) Reddening using a (cite: Salim2018) dust law; (6) Metallicity; (7) Mass-weighted age.

# Gas mass estimates and their products

|  |  |  |  |  |  |
|:---|:---|:---|:---|:---|:---|
| ID | M$_{\rm gas,thin}$ | M$_{\rm gas,thick}$ | M$_{\rm gas,\alpha_{CO}=0.8}$ | M$_{\rm gas,\alpha_{CO}=3.8}$ | M$_{\rm gas,CI}$ |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) |
| Gas mass | log(\[M$_{\rm \odot}$\]) | log(\[M$_{\rm \odot}$\]) | log(\[M$_{\rm \odot}$\]) | log(\[M$_{\rm \odot}$\]) | log(\[M$_{\rm \odot}$\]) |
| CGG-z4.a | $11.29^{+0.12}_{-0.16}$ | $11.07^{+0.15}_{-0.24}$ | $10.51^{+0.04}_{-0.04}$ | $11.05^{+0.04}_{-0.04}$ | $11.14^{+0.09}_{-0.11}$ |
| CGG-z4.b | $10.99^{+0.12}_{-0.17}$ | $10.77^{+0.15}_{-0.24}$ | $10.28^{+0.05}_{-0.06}$ | $10.82^{+0.05}_{-0.06}$ | $<10.66$ |
| Gas mass ratio ($\rm M_{\rm gas}/M_{\rm \star}$) |  |  |  |  |  |
| CGG-z4.a | $1.7^{+3.6}_{-0.9}$ | $1.0^{+2.2}_{-0.6}$ | $0.3^{+0.6}_{-0.1}$ | $1.0^{+2.1}_{-0.5}$ | $1.2^{+2.5}_{-0.6}$ |
| CGG-z4.b | $1.7^{+3.4}_{-0.9}$ | $1.0^{+2.1}_{-0.6}$ | $0.3^{+0.6}_{-0.2}$ | $1.2^{+2.3}_{-0.6}$ | $<2.3$ |
| Gas depletion time ($\rm M_{\rm gas}/SFR$) | \[Myr\] | \[Myr\] | \[Myr\] | \[Myr\] | \[Myr\] |
| CGG-z4.a | $140^{+44}_{-44}$ | $84^{+36}_{-36}$ | $23^{+2}_{-2}$ | $80^{+9}_{-9}$ | $99^{+23}_{-23}$ |
| CGG-z4.b | $140^{+46}_{-46}$ | $84^{+37}_{-37}$ | $27^{+4}_{-4}$ | $94^{+15}_{-15}$ | $<69$ |

: Gas mass estimates for CGG-z4.a,b, and the products calculated from them.

Table notes: Columns: (1) shows the name of the source and (2) gas mass using thin dust model; (3) gas mass using thick dust model; (4) gas mass using an $\alpha_{\rm CO}$ numerical value of 0.8; (5) gas mass using an $\alpha_{\rm CO}$ numerical value of $3.8\pm0.1$; (6) gas mass using an $\alpha_{\rm CI}$ numerical value of $16.2\pm0.4$. Due to the large uncertainty on the stellar masses, the gas mass ratios are estimated through Monte Carlo sampling, generating $10^{6}$ samples and taking their median and $68\%$ confidence interval.

</paper>

Write the methods card for this paper.