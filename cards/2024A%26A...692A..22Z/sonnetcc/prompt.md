# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2024A%26A...692A..22Z\sonnetcc\reply.txt

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
 "bibcode": "2024A&A...692A..22Z",
 "title": "ASW<SUP>2</SUP>DF: Census of the obscured star formation in a galaxy cluster in formation at z = 2.2",
 "year": 2024,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Zhang, Y. H.",
 "n_authors": 16,
 "arxiv_id": "2410.10169",
 "doi": "10.1051/0004-6361/202451379",
 "alma_projects_linked_by_archive": [
  "2021.1.00435.S"
 ]
}
```

Paper text:
<paper>
# ASW$^2$DF: Census of the obscured star formation in a galaxy cluster in formation at $z=2.2$

We report the results of the deep and wide Atacama Large Millimeter/submillimeter Array (ALMA) 1.2 mm mapping of the Spiderweb protocluster at $z=2.16$. The observations were divided into six contiguous fields covering a survey area of 19.3 arcmin$^2$. With $\sim$13h on-source time, the final maps in the six fields reach the 1$\sigma$ rms noise in a range of $40.3-57.1\,\mu$Jy at a spatial resolution of $0.5\ensuremath{''}-0.9\ensuremath{''}$. By using different source extraction codes and careful visual inspection, we detect 47 ALMA sources at a significance higher than 4$\sigma$. We construct the differential and cumulative number counts down to $\sim0.2$ mJy after the correction for purity and completeness obtained from Monte Carlo simulations. The ALMA 1.2 mm number counts of dusty star-forming galaxies (DSFGs) in the Spiderweb protocluster are overall two times that of general fields, some fields/regions showing even higher overdensities (more than a factor of 3). This is consistent with the results from previous studies over a larger scale using single-dish instruments. Comparison of the spatial distributions between different populations indicates that our ALMA sources are likely drawn from the same distribution as CO(1-0) emitters from the COALAS large program, but distinct from that of H$\alpha$ emitters. The cosmic SFR density of the ALMA sources is consistent with previous results (e.g. LABOCA 870 $\mu$m observations) after accounting for the difference in volume. We show that molecular gas masses estimates from dust measurements are not consistent with the ones derived from CO(1-0) and thus have to be taken with caution. The multiplicity fraction of single-dish DSFGs is higher than that of the field. Moreover, two extreme concentrations of ALMA sources are found on the outskirts of the Spiderweb protocluster, with an excess of more than 12 times that of general fields. These results indicate that the ALMA-detected DSFGs are supplied through gas accretion along filaments and are triggered by intense star formation by accretion shocks before falling into the cluster center. The identified two galaxy groups are likely falling into the protocluster center and will trigger new merger events eventually, as indicated in simulations.

# Introduction

As a result of the inhomogeneous mass assembly in the Universe, the “cosmic web” is composed of filaments, sheets, and voids (cite: Bond1996). Galaxy protoclusters were formed at the densest nodes of the cosmic web at high redshift and evolved into mature galaxy clusters in the local Universe (cite: Overzier2016). Star formation in protoclusters reached its peak at $z\sim2-3$, with a contribution of $\sim$20 percent to the cosmic star formation rate (SFR) density at the same epoch (cite: Chiang2017). Therefore, protoclusters at high redshift provide a unique opportunity to investigate the formation and evolution of different galaxy populations in connection with the large-scale structure assembly.

Submillimeter galaxies (SMGs), first discovered in coarse single-dish (sub)mm surveys, are the brightest population of dusty star-forming galaxies (cite: Casey2014) with at least a few mJy at submillimeter (submm) wavelength (cite: Blain2002), whose star formation is heavily dust-obscured and hardly detected in the optical/near-infrared (NIR) bands. This rare population has been studied for more than two decades since its discovery (cite: Smail1997; Hughes1998), and their number densities are well constrained at different (sub)mm wavelengths (cite: Weiss2009; Oliver2010; Scott2012; Casey2013; Chen2013; Geach2017; Magnelli2019; Simpson2019; Shim2020; Bing2023). Detailed studies on source properties suggest that DSFGs dominate the cosmic SFR density at cosmic noon (cite: Bourne2017; Koprowski2017; Madau2014), the peak epoch of cosmic star formation and active galactic nucleus (AGN) activities (cite: Hopkins2006; Zheng2009), and will eventually evolve into elliptical galaxies in the local Universe (cite: Lutz2001; Smail2002; Swinbank2006; Gullberg2019).

However, most previous studies of DSFGs are based on observations with single-dish facilities such as JCMT/SCUBA2 (cite: Holland1999; Holland2013), APEX/LABOCA (cite: Siringo2009) and ASTE/AzTEC (cite: Wilson2008) with a coarse resolution (15$^{\prime\prime}-$30$^{\prime\prime}$), thus hampered by source blending and counterpart identification (cite: Chen2016; An2018). The high confusion noise allows only the detection of bright SMGs (cite: Blain2002). Thanks to the Atacama Large Millimeter/submillimeter Array (cite: Wootten2009) with its unprecedented resolution and sensitivity, we have the opportunity to probe DSFGs down to tens of $\mu$Jy at a sub-arcsec resolution, extending to the ‘normal’ star-forming galaxy population with an SFR of tens of solar masses per year (cite: Aravena2016; Aravena2020). Extensive efforts have been made to investigate the DSFGs with deep ALMA contiguous mapping surveys in general fields (cite: Hatsukade2016; Hatsukade2018; Dunlop2017; Gonzalez2017; Gonzalez2019; Gonzalez2020; Franco2018; Decarli2019; Gomez2022), which helped in our understanding of the dust and gas properties of this population in the distant Universe (cite: Hodge2020).

Moreover, SMGs are located preferentially in massive dark-matter halos (cite: Blain2004; Hickox2012; Wilkinson2017) similar to those around radio galaxies (cite: Stevens2003; Humphrey2011; Rigby2014; Zeballos2018) and quasars (cite: Priddey2008; Stevens2010; Carrera2011; Jones2017; Wethers2020), thus can serve as a tracer for protoclusters (cite: Calvi2023). These halos reside in overdense environments and hold intense star formation, making them an ideal laboratory to study where and how extreme starbursts take place. Overdensities of SMGs have been confirmed in protoclusters within a wide redshift range z$\sim2-7$ ((cite: DeBreuck2004; Greve2007; Tamura2009; Dannerbauer2014; Casey2016; AB2018; Wang2021; Zhang2022; Zeng2024; Zhoudz2024); (cite: Alberts2022)). These studies are based on observations with single-dish telescopes and thus can only reveal the overall properties of the brightest SMGs. Therefore, ALMA (contiguous) mapping of these SMG overdensities is indispensable to study DSFGs individually and their connection with the surrounding large-scale structure. Due to a limited number of deep ALMA mapping surveys on such extreme structures (cite: Umehata2015; Umehata2017; Umehata2018; Zhou2020; Pensabene2024; Wang2024), it is strongly demanded to create a census of DSFGs in protoclusters to enlarge the sample and investigate the roles that environment plays in forming the DSFG population.

One of the most overdense structures is the prominent Spiderweb protocluster at $z=2.16$, which has been studied for more than twenty years since its discovery (cite: Kurk2000; Pentericci2000). The high redshift radio galaxy MRC1138-262 (cite: Roettgering1994; Pentericci1997) at the center of the protocluster, has a clumpy morphology with a large number of companion galaxies (cite: Miley2006; Hatch2009) and surrounded by an extended molecular gas reservoir (cite: Emonts2016; Emonts2018). The overdense environment of the Spiderweb protocluster has been confirmed via various populations, including X-ray detections (cite: Pentericci2002; Croft2005; Tozzi2022a; Tozzi2022b), Ly$\alpha$ emitters (cite: Pentericci2000; Kurk2000), H$\alpha$ emitters (cite: Kuiper2011; Koyama2013; Shimakawa2014; Shimakawa2018b; Daikuhara2024), extremely red objects (cite: Kurk2004a), (sub)millimeter galaxies (cite: Rigby2014; Dannerbauer2014; Zeballos2018), and CO(1-0) emitters (cite: Jin2021). The overdensity signature motivates the study of the environmental effects on the member galaxies in terms of UV morphologies (cite: Naufal2023), gas-phase metallicity (cite: Perez2023), AGN activity (cite: Tozzi2022a; Shimakawa2024) and the cold molecular gas content (cite: Dannerbauer2017; Emonts2016; Emonts2018; Chen2024). Observations of hundreds of hours towards this protocluster have been accumulated at a very wide wavelength range from X-ray to radio, making it an ideal target to study DSFGs in such complex environments. Moreover, (cite: Tozzi2022b) reported a diffuse X-ray emission centered on the Spiderweb galaxy over a scale of $\sim100\,$kpc, powered by the inverse-Compton scattering associated with the radio jets. The hot, nascent intracluster medium (ICM) has been detected through the Sunyaev–Zeldovich effect (cite: Mascolo2023). Especially, the later result shows that this structure will evolve into a mature galaxy cluster in the local Universe.

In this paper, we report the first results of the ALMA Spiderweb Wide and Deep Field (ASW$^2$DF) survey, mapping dusty star-forming galaxies through ALMA band 6 observations on the Spiderweb protocluster at $z=2.16$. In Section [2](#sec: obs), we introduce the observations and data reduction, along with a summary of the data products. We describe the source extraction and the constructed source catalog in Section [3](#sec: catalog). We present the Monte Carlo simulation and the number count results in Section [4](#sec: number counts). In Section [5](#sec: discussion), we compare our results with the literature and estimate the overdensity of DSFGs in the Spiderweb protocluster. We summarize our results in Section [6](#sec: summary). For simplicity, we refer to sources detected by submm/mm single-dish telescopes to as SMGs, and sources detected by ALMA as DSFGs throughout this paper. We adopt a flat $\Lambda$CDM cosmology with $H_0=71$ kms $^{-1}$ Mpc$^{-1}$, $\Omega _{\rm \Lambda}$=0.7 (cite: Spergel2003; Spergel2007) throughout the paper, giving a scale of 0.490 physical Mpc (pMpc) or 1.549 comoving Mpc (cMpc) per arcmin at $z=2.16$.

![](plots/01_detections_rms.png)

# Observations and data reduction

ASW$^2$DF is a 1.2 mm galaxy survey aiming to reveal dusty star-forming galaxies in the Spiderweb protocluster. This survey covers the central part of the filamentary structure traced by HAEs (cite: Koyama2013; Shimakawa2018b), and is complemented by the existing COALAS CO(1-0) large program (cite: Jin2021). In this section, we describe the details of this survey, as well as the data reduction and the products.

## Observations

The ASW$^2$DF mapping observations include six contiguous fields around on the Spiderweb galaxy, each field is made up by a 87-pointing mosaic covering an area of $1^\prime\times3^\prime$. The observations were carried out in Cycle 8 (Project ID: 2021.1.00435.S; PI: Y. Koyama) between 31 December 2021 and 17 April 2022 in ALMA band 6. Three execution blocks (EBs) have been conducted in each of Field 1, 2, 3, 4, and four EBs in each of Field 5 and Field 6. We note that one EB failed due to antenna issues. The total number of available antennas ranges from 42 to 46. All the EBs in Field 1$-$3 and two in Field 4 were observed in C4 configuration, with a baseline range of 14.9$-$976.6 m and a theoretical resolution of 0.4$''$. The remaining eight EBs in Field 4$-$6 were observed in C2 configuration, with a baseline range of 15.0 m to 500.2 m and a theoretical resolution of 0.7$''$. The maximum recoverable scales are 4.5$''$ and 8.2$''$ in C4 and C2 configurations, respectively. The correlator was set up at a single tuning, with four spectral windows centered at 239.0, 241.0, 255.0 and 257.0 GHz respectively. Each spectral window contains 128 channels of 15.625 MHz each in dual polarization with a bandwidth of 1.875 GHz. The tuning setup also covers the redshifted CO(7-6) and CI(2-1) lines ($\nu_{\rm rest}=806.65$ and 809.34 GHz) at z$\sim$2.16, providing the possibility of detecting molecular gas in the Spiderweb protocluster. We will report results on these lines in a later publication.

One quasar J1256$-$0547 was used for flux and bandpass calibrations in 11 EBs (Field 1$-$3 and two in Field 4), and another quasar J1037$-$2934 was used in seven EBs (Field 5-6 and one in Field 4). The remaining one EB of Field 4 used quasar J1107$-$4449 as a flux and bandpass calibrator while quasar J1146$-$2859 was observed as the phase calibrator for all EBs. Meanwhile, all the calibrators were used for calibrating the precipitable water vapor (PWV). The average PWV is 0.3-2.4 mm with a median of 0.9 mm. The on source time was 2.03 h for each field (except 2.70 h for Field 4), resulting in a total on source time of 12.84 h.

![image](plots/02_flux_distribution.png) ![image](plots/02_noise_ratio.png)

## Data reduction

The Common Astronomy Software Applications (cite: CASA2022) with the ALMA pipeline version 2021.2.0.128 (cite: Hunter2023) were used to perform the data reduction. The visibilities were calibrated and flagged using the scripts provided by the ALMA archive. The imaging of the visibility data sets were done by using the task `TCLEAN` in CASA, within the “mosaic” gridder mode and the “hogbom” deconvolver. The “Briggs” data weighting with the robust parameter of 0.5 was employed to optimize between angular resolution, noise, and sidelobe levels (cite: Briggs1995). The multi-frequency synthesis algorithm was used to combine the four spectral windows into the single dirty continuum image. We note that the channels at the edge of the spectral window and the bad baselines, as well as the potential emission lines mentioned above were flagged for the continuum imaging. The final available bandwidth is 6.375 GHz. After measuring the 1$\sigma$ rms within the entire dirty maps, the cleaning process was repeated until reaching the 3$\sigma$ levels in order to obtain the final clean maps.

Due to the variation of available antennas and the observing conditions, the Execution Fraction (EF) was evaluated to quantify the performance of each EB. The EF is the effective quality of the data from each EB normalized to the expected theoretical value assumed by the ALMA scheduling system. Higher EF means that the EB was observed under good weather conditions and has a better sensitivity. The final images in six fields have different EF (3.62$-$5.05) and a sensitivity range from 40.3 $\mu$Jy to 57.1 $\mu$Jy. The sensitivity was measured from the standard deviation of the science image before correcting the flux values at the edge of the mosaic for the primary beam response which will be used for the source extraction and discussed in the next section. Importantly, Field 4 has the best sensitivity due to an additional EB. The resolution of Field 1$-$3 and Field 4$-$6 are different due to the change of configurations. The average resolution is 0.49$''$ $\times$ 0.34$''$ with a pixel scale of 0.07$''$ for Field 1$-$3, while the average resolution is 0.87$''$ $\times$ 0.60$''$ with a pixel scale of 0.14$''$ for Field 4$-$6. In Figure [1](#fig: detections), the different noise levels and resolutions across the six fields in the mosaic map are clearly seen. We summarize the observing date, number of available antennas, baseline lengths, theoretical resolution, on source time, PWV, EF, synthesized beam, position angle and the 1$\sigma$ noise of each field in Table [\[tab: obs\]](#tab: obs).

# Source catalog

One of the main aims of the sub-mm/mm continuum imaging is to create a source catalog. Source extraction is thus an important part of the catalog construction and is performed in different ways in the literature. We extract ALMA sources with the Python package SEP (cite: Barbary2016), which uses the core algorithms of SExtractor (cite: Bertin1996). SExtractor is the most commonly used program for detecting the sources in ALMA images at different ALMA bands (cite: Simpson2014; Simpson2015; Aravena2016; Fujimoto2016; Oteo2016; Stach2018; Stach2019; Simpson2020; Klitsch2020; Chen2023a; Fujimoto2023), as it is able to detect sources with complex structures. We also use AEGEAN (cite: Hancock2012; Hancock2018) which is specifically designed and often used in the radio domain, including ALMA maps (cite: Umehata2015; Hatsukade2016; Stach2017; Umehata2017; Umehata2018; Ueda2018; Hatsukade2018). Additionally, we use the Source Finding Application (SoFiA) (cite: Serra2015; Westmeier2021) to extract the ALMA sources as a further check, as it is suitable for searching emission lines from data cubes, but it can also be used for continuum source detection in ALMA maps (cite: Klitsch2018; Hamanowicz2023). In this section, we describe and compare the results of the rms noise estimation and source extraction from different codes. We note that this is the first time that a (detailed) comparison of different source extraction algorithms applied on ALMA data is done.

## Noise estimation

It is essential to make a fair sensitivity estimation (i.e., rms noise) before source extraction. We use science images without the primary beam (PB) correction for rms noise estimation and source extraction, because the pixel values in these images are quite uniform and perfectly follow a Gaussian profile as shown in the left panel of Figure [2](#fig: noise_ratio). The PB-corrected images will be used for the flux measurement of detected objects.

In general, two methodologies are commonly employed to estimate the noise of ALMA maps. One method is to calculate the standard deviation within an rms box, as the noise of the central pixel. The box is moving in a step of one pixel across the image, and each pixel will get an individual rms noise which we call here the “individual” method. The step size may consist of several pixels, resulting in the estimation of rms noise for pixels located in a grid pattern. Interpolation is subsequently employed to derive the complete noise map. In principle, this method captures the noise fluctuation across the entire image. It is worth noting that the sizes of both the rms box and the moving step vary significantly in the literature. For example, the box with $100\times100$ pixels was used for noise estimation in a step of one pixel (cite: Hatsukade2016; Umehata2017; Umehata2018). (cite: Franco2018) utilized a box size of 100 pixels but two pixels in each step. (cite: Gomez2022) adopted a step size of two pixels, accompanied by a larger box with $200\times200$ pixels. Moreover, the box size can be scaled by the synthesized beam in order to calculate the noise of the central pixel (cite: Dunlop2017; Stach2017). The differences in those parameters are also seen in the default values suggested by the source extraction codes previously mentioned.

|  Code  |  Key Parameters  |     Values      |
|:------:|:----------------:|:---------------:|
|        |      thresh      |        4        |
|        |       err        | 1$\sigma$ noise |
|  SEP   |     minarea      |        5        |
|        |       mask       |     PB\>0.5     |
|        |  filter_kernel   |      None       |
|        |    –seedclip     |        4        |
|        |    –forcerms     | 1$\sigma$ noise |
| AEGEAN |    –forcebkg     |        0        |
|        |     –island      |                 |
|        |    –negative     |                 |
|        | scfind.threshold |        4        |
|        | linker.minPixels |        5        |
| SoFiA  | linker.minSizeXY |        1        |
|        | linker.minSizeZ  |        1        |
|        | scfind.kernelsZ  |        0        |

: Key parameters used in SEP, AEGEAN, SoFiA.

The other method, i.e. the “fixed” method, is to calculate the standard deviation of the whole image without the PB correction as the typical 1$\sigma$ rms noise, and the value is fixed across the entire image. This method is used for ALMA maps in both single pointing and contiguous mapping modes (cite: Gonzalez2017; Zavala2018; Gonzalez2020; Zavala2021; Chen2023a; Fujimoto2023). Note that in both methods, the sigma-clipping iterations are normally applied before the standard deviation calculation to remove the contribution from the bright sources.

We estimate and compare the rms noise of our science images using the “individual” and “fixed” methods respectively. All the pixels used for noise estimation are within the coverage where the primary beam response is larger than 50 percent. The following source extraction will also be restricted within this region. The “individual” method is performed using SEP, AEGEAN and SoFiA respectively, as these tools can directly create the two-dimensional noise map. For consistency, we use the rms box of $100\times100$ pixels with a step size of one pixel to calculate the standard deviation for the central pixel of the box, instead of using the default values in the three codes. The “fixed” method is straightforward by calculating the standard deviation of the entire image in each field as the 1$\sigma$ noise, after five iterations of the 5-sigma-clipping process. We find that SoFiA can also produce the 1$\sigma$ noise by disabling the parameter `scaleNoise` and the results are identical to our calculation.

We divide the noise map from the “individual” method by the 1$\sigma$ noise from the “fixed” method in each field to obtain the noise ratios for a comparison. The right panel of Fig. [2](#fig: noise_ratio) shows the distributions of the noise ratios of three different codes. The median ratio of the results of SEP and AEGEAN is both $\sim$ 0.984, indicating that the “individual” noise map is relatively lower than the “fixed” 1$\sigma$ noise. This is consistent with our tests that the noise of the central pixel increases with the box size, and the “fixed” method is equivalent to treating the entire image as a single box. Similar results were also reported in the literature (cite: Franco2018; Zavala2021). The distribution of ratios for the result of SoFiA has a higher median value around one together with a larger scatter. We attribute this to the lack of the sigma-clipping process during the noise estimation in SoFiA. Although the median noise obtained using the “individual” method in all three codes is very close to the 1$\sigma$ noise from the “fixed” method, differences between individual pixels may lead an obvious discrepancy between the source catalogs.

## Source extraction

Both the two-dimensional noise maps created by SEP, AEGEAN and SoFiA in the “individual” method, and the 1$\sigma$ noise value in the “fixed” method are used for the source extraction. The sources are detected at \>4$\sigma$ in the PB-uncorrected image in each field with these three codes. An important parameter is how many pixels linked to each other above the detection threshold should be considered as a source. This parameter is characterized by `minarea` with a default value of five in SEP, meaning that a source can only be identified when it has at least five contiguous pixels above 4$\sigma$. The five pixels, much smaller than the synthesized beam size, that meet the 4$\sigma$ threshold must be interconnected with no limitations on their arrangement along the x-axis or y-axis. We adopt this value as it is used by default in SEP and SExtractor in most previous studies. Lower values will introduce more spurious sources at the same detection threshold. A similar parameter `linker.minPixels` in SoFiA is set to five for consistency. There is no identical parameter in AEGEAN. We cut the original catalog and only include sources with more than five adjacent pixels above 4$\sigma$ into the AEGEAN’s catalog. The key parameters with the customized values used in three codes are listed in Table [1](#tab: se_params).

Based on the noise maps from the “individual” method, we detect 54, 48 and 49 sources at \>4$\sigma$ through SEP, AEGEAN and SoFiA respectively. The differences in source numbers come from the discrepancies of the noise maps created by SEP, AEGEAN and SoFiA following this method. Understanding the reason why these codes result in different noise maps even with the same rms box size ($100\times100$ pixels) is beyond the scope of this paper; here we only focus on the catalogs they produced and make a conclusion on the final catalog construction. Interestingly, all three codes produced the same catalog containing 47 detections when we use the 1$\sigma$ noise values from the “fixed” method. This result confirms the reliability of the codes as they can detect identical sources with the same noise characterization. This explains why obtaining different catalogs with “individual” method is mainly due to the use of different noise maps. The higher number of detections from the “individual” method is probably due to a lower noise estimation or large dispersion in the noise distribution.

We demonstrate that the results of the source extraction are heavily affected by different noise estimates. Though the “individual” method with a defined rms box could reflect the fluctuation of the background noise, it is difficult to find a coherent criterion to calculate the scale of the local noise fluctuation as the resolution and pixel scale vary a lot in different surveys. The 1$\sigma$ noise with the “fixed” method is more representative as it is directly derived from the standard deviation of the Gaussian profile drawn in the flux distribution. Additionally, the “fixed” method produces $\sim2$ percent higher noise than the median noise from SEP and AEGEAN with “individual” method (see Fig. [2](#fig: noise_ratio) right panel), thus could be considered as a conservative way.

![](plots/03_purity.png)

In this work, we refer to the rms noise value derived from the “fixed” method as the typical noise representing the observing depth, which is also the minimum noise of the map after PB correction in each field (Table [\[tab: obs\]](#tab: obs)). Accordingly, there are 47 sources detected by all three codes through the “fixed” method. We consider these sources to be primary detections and include them in the main catalog. We note that the number of detections by each code depends on the chosen rms methods. There must be some faint sources that cannot be detected by the “fixed” method at 4$\sigma$ significance, but will be detected by the “individual” method. We match our main catalog with the results from the “individual” method, and find that there are 13 sources detected by at least one of the three codes with the “individual” method but cannot be detected by the “fixed” method. We mark these 13 sources as tentative sources.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | R.A. | Dec. | S/N$_{\rm p}$ | S/N$_{\rm d}$ | $S_{\rm peak}$ | $S_{\rm fit}$ | $S_{\rm aper}$ | Counterpart | eyes ID | Cat |
|  | (J2000) | (J2000) |  |  | (mJy) | (mJy) | (mJy) |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |
| ASW2DF.01 | 11:40:57.80 | -26:29:35.5 | 25.27 | 23.56 | 1.17 ± 0.05 | 1.51 ± 0.05 | 1.81 ± 0.13 | SMG,CO | robust | A |
| ASW2DF.02 | 11:41:00.32 | -26:30:31.9 | 20.31 | 19.02 | 1.04 ± 0.05 | 2.02 ± 0.09 | 2.20 ± 0.11 | SMG,CO | robust | A |
| ASW2DF.03 | 11:40:59.60 | -26:30:39.2 | 20.28 | 19.19 | 0.97 ± 0.05 | 1.78 ± 0.07 | 1.82 ± 0.14 | SMG,CO$_{\rm ext}$ | robust | A |
| ASW2DF.04 | 11:40:53.21 | -26:29:11.1 | 19.69 | 17.93 | 0.92 ± 0.05 | 1.18 ± 0.06 | 1.36 ± 0.12 | SMG | robust | A |
| ASW2DF.05 | 11:40:46.06 | -26:29:11.3 | 18.87 | 17.60 | 0.76 ± 0.04 | 1.27 ± 0.08 | 1.40 ± 0.11 | HAE,CO$_{\rm ext}$ | robust | A |
| ASW2DF.06 | 11:40:35.36 | -26:28:35.1 | 15.28 | 14.27 | 0.68 ± 0.04 | 0.88 ± 0.07 | 0.93 ± 0.11 | — | robust | A |
| ASW2DF.07 | 11:40:44.06 | -26:28:21.1 | 13.61 | 12.21 | 0.56 ± 0.04 | 0.84 ± 0.07 | 0.79 ± 0.10 | — | robust | A |
| ASW2DF.08 | 11:40:57.42 | -26:30:48.0 | 11.78 | 10.93 | 0.66 ± 0.06 | 0.72 ± 0.08 | 1.16 ± 0.14 | — | possible | B |
| ASW2DF.09 | 11:40:58.48 | -26:30:36.7 | 11.31 | 9.93 | 0.53 ± 0.05 | 0.56 ± 0.05 | 0.71 ± 0.10 | — | possible | B |
| ASW2DF.10 | 11:40:53.64 | -26:27:57.0 | 10.32 | 9.52 | 0.54 ± 0.05 | 0.67 ± 0.06 | 0.82 ± 0.14 | SMG | robust | A |
| ASW2DF.11 | 11:40:39.02 | -26:30:35.4 | 10.20 | 9.03 | 0.50 ± 0.05 | 0.59 ± 0.07 | 0.57 ± 0.12 | — | robust | A |
| ASW2DF.12 | 11:40:46.66 | -26:29:10.2 | 10.03 | 8.96 | 0.42 ± 0.04 | 0.57 ± 0.06 | 0.63 ± 0.11 | HAE,CO$_{\rm ext}$ | robust | A |
| ASW2DF.13 | 11:40:59.38 | -26:30:43.5 | 9.99 | 9.51 | 0.51 ± 0.05 | 0.67 ± 0.07 | 0.81 ± 0.15 | — | possible | B |
| ASW2DF.14 | 11:40:40.86 | -26:29:46.8 | 9.93 | 9.31 | 0.48 ± 0.05 | 0.81 ± 0.07 | 0.67 ± 0.10 | CO$_{\rm ext}$ | robust | A |
| ASW2DF.15 | 11:40:43.94 | -26:28:34.2 | 9.39 | 8.63 | 0.38 ± 0.04 | 0.57 ± 0.06 | 0.66 ± 0.11 | — | robust | A |
| ASW2DF.16 | 11:40:37.32 | -26:30:17.3 | 8.36 | 7.76 | 0.38 ± 0.05 | 0.75 ± 0.08 | 0.76 ± 0.12 | HAE,CO | robust | A |
| ASW2DF.17 | 11:40:48.34 | -26:29:08.5 | 8.22 | 7.84 | 0.47 ± 0.06 | 1.00 ± 0.10 | 1.46 ± 0.19 | SMG,CO$_{\rm ext}$ | robust | A |
| ASW2DF.18 | 11:40:35.14 | -26:29:35.2 | 7.07 | 6.67 | 0.32 ± 0.04 | 0.34 ± 0.06 | 0.36 ± 0.12 | — | possible | B |
| ASW2DF.19 | 11:40:53.70 | -26:29:11.8 | 6.90 | 6.56 | 0.32 ± 0.05 | 0.60 ± 0.07 | 0.79 ± 0.11 | — | possible | B |
| ASW2DF.20 | 11:40:51.27 | -26:29:38.6 | 6.57 | 6.05 | 0.40 ± 0.06 | 0.75 ± 0.11 | 0.91 ± 0.18 | HAE,CO | robust | A |
| ASW2DF.21 | 11:40:56.52 | -26:29:44.8 | 6.56 | 5.92 | 0.33 ± 0.05 | 0.29 ± 0.06 | 0.38 ± 0.13 | — | possible | B |
| ASW2DF.22 | 11:40:43.54 | -26:29:02.5 | 6.17 | 5.59 | 0.26 ± 0.04 | 0.29 ± 0.05 | 0.49 ± 0.11 | — | possible | B |
| ASW2DF.23 | 11:40:54.56 | -26:28:23.8 | 5.67 | 5.03 | 0.26 ± 0.05 | 0.47 ± 0.09 | 0.52 ± 0.11 | HAE, CO | possible | B |
| ASW2DF.24 | 11:40:53.10 | -26:28:47.2 | 5.59 | 5.28 | 0.26 ± 0.05 | 0.36 ± 0.06 | 0.28 ± 0.14 | — | possible | B |
| ASW2DF.25 | 11:40:52.45 | -26:29:39.8 | 5.35 | 4.78 | 0.25 ± 0.05 | 0.19 ± 0.05 | 0.18 ± 0.12 | — | possible | B |
| ASW2DF.26 | 11:40:39.73 | -26:30:27.8 | 5.25 | 4.57 | 0.25 ± 0.05 | 0.32 ± 0.07 | 0.32 ± 0.14 | — | possible | B |
| ASW2DF.27 | 11:40:46.31 | -26:29:32.8 | 5.19 | 4.22 | 0.21 ± 0.04 | 0.15 ± 0.04 | 0.17 ± 0.11 | — | possible | B |
| ASW2DF.28 | 11:40:54.74 | -26:28:03.1 | 5.06 | 4.82 | 0.24 ± 0.05 | 0.40 ± 0.08 | 0.56 ± 0.12 | HAE | possible | B |
| ASW2DF.29 | 11:40:38.58 | -26:30:25.5 | 5.05 | 4.55 | 0.38 ± 0.08 | 0.30 ± 0.08 | 0.43 ± 0.19 | CO | marginal | B |
| ASW2DF.30 | 11:40:49.14 | -26:30:37.8 | 4.91 | 4.47 | 0.29 ± 0.06 | 0.23 ± 0.06 | 0.16 ± 0.17 | — | possible | B |
| ASW2DF.31 | 11:40:48.76 | -26:27:52.8 | 4.90 | 4.44 | 0.36 ± 0.07 | 0.65 ± 0.15 | 0.60 ± 0.19 | SMG | possible | B |
| ASW2DF.32 | 11:40:57.52 | -26:27:59.1 | 4.88 | 4.32 | 0.24 ± 0.05 | 0.18 ± 0.05 | 0.13 ± 0.14 | — | — | B |
| ASW2DF.33 | 11:40:57.81 | -26:30:47.8 | 4.83 | 4.66 | 0.28 ± 0.06 | 0.67 ± 0.11 | 1.14 ± 0.15 | SMG, CO$_{\rm ext}$ | cloud-like | B |
| ASW2DF.34 | 11:40:50.82 | -26:30:07.2 | 4.82 | 4.08 | 0.28 ± 0.06 | 0.23 ± 0.05 | 0.26 ± 0.17 | — | — | B |
| ASW2DF.35 | 11:40:42.43 | -26:28:04.3 | 4.81 | 4.14 | 0.26 ± 0.05 | 0.32 ± 0.08 | 0.50 ± 0.13 | — | cloud-like | B |
| ASW2DF.36 | 11:40:57.57 | -26:30:24.3 | 4.74 | 4.21 | 0.22 ± 0.05 | 0.15 ± 0.04 | 0.05 ± 0.09 | — | — | B |
| ASW2DF.37 | 11:40:52.84 | -26:29:11.0 | 4.72 | 4.36 | 0.22 ± 0.05 | 0.35 ± 0.08 | 0.46 ± 0.11 | — | possible | B |
| ASW2DF.38 | 11:40:58.88 | -26:29:58.7 | 4.72 | 4.33 | 0.22 ± 0.05 | 0.16 ± 0.05 | 0.25 ± 0.09 | — | — | B |
| ASW2DF.39 | 11:40:56.21 | -26:29:32.9 | 4.67 | 4.01 | 0.26 ± 0.06 | 0.24 ± 0.06 | 0.12 ± 0.16 | — | possible | B |
| ASW2DF.40 | 11:41:00.77 | -26:30:42.9 | 4.60 | 4.21 | 0.31 ± 0.07 | 0.35 ± 0.08 | 0.56 ± 0.15 | — | possible | B |
| ASW2DF.41 | 11:40:35.98 | -26:29:02.3 | 4.58 | 4.18 | 0.21 ± 0.04 | 0.53 ± 0.10 | 0.65 ± 0.12 | — | cloud-like | B |
| ASW2DF.42 | 11:40:40.18 | -26:28:39.5 | 4.57 | 4.24 | 0.22 ± 0.05 | 0.21 ± 0.06 | 0.06 ± 0.14 | — | robust | A |
| ASW2DF.43 | 11:40:55.81 | -26:30:24.7 | 4.54 | 4.12 | 0.34 ± 0.07 | 0.26 ± 0.08 | 0.17 ± 0.18 | — | marginal | B |
| ASW2DF.44 | 11:40:48.99 | -26:30:17.1 | 4.51 | 4.14 | 0.26 ± 0.06 | 0.56 ± 0.12 | 0.90 ± 0.15 | — | cloud-like | B |
| ASW2DF.45 | 11:40:53.96 | -26:29:00.9 | 4.43 | 4.15 | 0.21 ± 0.05 | 0.27 ± 0.06 | 0.35 ± 0.13 | — | — | B |
| ASW2DF.46 | 11:40:50.71 | -26:28:31.4 | 4.35 | 4.08 | 0.25 ± 0.06 | 0.26 ± 0.08 | 0.32 ± 0.20 | — | — | B |
| ASW2DF.47 | 11:40:51.11 | -26:29:05.1 | 4.24 | 4.05 | 0.25 ± 0.06 | 0.48 ± 0.10 | 0.61 ± 0.15 | CO$_{\rm ext}$ | possible | B |

Table notes: (1) ALMA sources with IDs sorted by the peak S/N; (2) Right Ascension (J2000); (3) Declination (J2000); (4) S/N at the peak pixel; (5) S/N at the fifth brightest pixel of a source, which can be detected by the “fixed” method at 4$\sigma$; (6) Peak flux at 1.2 mm; (7) Gaussian fitting flux; (8) 2$\times$synthesized beam aperture flux; (9) Counterparts of ALMA sources matched from different galaxy populations including SMGs (cite: Dannerbauer2014), HAEs (cite: Koyama2013; Shimakawa2018b), and CO emitters (cite: Jin2021; Chen2024); CO emitters identified as extended gas reservoirs by (cite: Chen2024) are marked with a subscript ‘ext’; (10) The classifications of the sources identified by visual inspection, including ‘robust’, ‘possible’, ‘could-like’ and ‘edge’; (11) source category.

|  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| ID | R.A. | Dec. | S/N$_{\rm p}$ | S/N$_{\rm d}$ | $S_{\rm peak}$ | $S_{\rm fit}$ | $S_{\rm aper}$ | Counterpart | eyes ID | Cat |
|  | (J2000) | (J2000) |  |  | (mJy) | (mJy) | (mJy) |  |  |  |
| \(1\) | \(2\) | \(3\) | \(4\) | \(5\) | \(6\) | \(7\) | \(8\) | \(9\) | \(10\) | \(11\) |
| ASW2DF.48 | 11:40:34.69 | -26:28:49.4 | 4.86 | 3.96 | 0.22 ± 0.04 | 0.15 ± 0.04 | 0.34 ± 0.10 | — | possible | C |
| ASW2DF.49 | 11:40:44.57 | -26:30:05.7 | 4.84 | 3.90 | 0.20 ± 0.04 | 0.12 ± 0.04 | 0.10 ± 0.11 | — | — | C |
| ASW2DF.50 | 11:40:54.51 | -26:27:47.6 | 4.52 | 3.80 | 0.35 ± 0.08 | 0.24 ± 0.07 | 0.30 ± 0.19 | — | marginal | C |
| ASW2DF.51 | 11:40:57.76 | -26:29:24.3 | 4.47 | 3.96 | 0.21 ± 0.05 | 0.16 ± 0.05 | 0.15 ± 0.13 | — | — | C |
| ASW2DF.52 | 11:40:45.22 | -26:29:20.4 | 4.46 | 3.79 | 0.18 ± 0.04 | 0.14 ± 0.04 | 0.07 ± 0.12 | — | — | C |
| ASW2DF.53 | 11:40:38.03 | -26:30:04.0 | 4.45 | 3.93 | 0.23 ± 0.05 | 0.19 ± 0.07 | 0.07 ± 0.14 | — | possible | C |
| ASW2DF.54 | 11:40:53.70 | -26:30:41.2 | 4.45 | 3.93 | 0.22 ± 0.05 | 0.20 ± 0.05 | 0.21 ± 0.12 | — | — | C |
| ASW2DF.55 | 11:40:35.01 | -26:29:07.5 | 4.45 | 3.88 | 0.20 ± 0.04 | 0.14 ± 0.05 | 0.07 ± 0.11 | — | — | C |
| ASW2DF.56 | 11:40:42.25 | -26:30:48.7 | 4.44 | 3.60 | 0.28 ± 0.06 | 0.17 ± 0.05 | 0.12 ± 0.17 | — | possible | C |
| ASW2DF.57 | 11:40:58.45 | -26:30:42.5 | 4.42 | 3.94 | 0.22 ± 0.05 | 0.22 ± 0.06 | 0.24 ± 0.12 | — | — | C |
| ASW2DF.58 | 11:40:59.10 | -26:29:07.6 | 4.40 | 3.86 | 0.20 ± 0.05 | 0.18 ± 0.04 | 0.25 ± 0.12 | — | — | C |
| ASW2DF.59 | 11:40:58.98 | -26:29:23.8 | 4.39 | 3.83 | 0.20 ± 0.05 | 0.19 ± 0.06 | 0.09 ± 0.10 | — | — | C |
| ASW2DF.60 | 11:40:36.22 | -26:27:45.9 | 4.29 | 3.97 | 0.37 ± 0.09 | 0.40 ± 0.10 | 0.28 ± 0.22 | — | marginal | C |
| ASW2DF.61 | 11:40:35.80 | -26:30:30.1 | 4.28 | 3.94 | 0.19 ± 0.05 | 0.18 ± 0.05 | 0.07 ± 0.11 | — | possible | C |
| ASW2DF.62 | 11:40:41.80 | -26:30:47.0 | 4.28 | 3.71 | 0.25 ± 0.06 | 0.32 ± 0.08 | 0.39 ± 0.17 | — | cloud-like | C |
| ASW2DF.63 | 11:40:36.70 | -26:30:37.6 | 4.21 | 3.84 | 0.19 ± 0.05 | 0.13 ± 0.04 | 0.16 ± 0.13 | — | — | C |
| ASW2DF.64 | 11:40:46.87 | -26:29:36.9 | 4.09 | 3.77 | 0.38 ± 0.09 | 0.50 ± 0.12 | 0.58 ± 0.25 | — | marginal | C |
| ASW2DF.65 | 11:40:38.38 | -26:28:53.8 | 4.02 | 3.75 | 0.25 ± 0.06 | 0.18 ± 0.05 | 0.29 ± 0.17 | — | marginal | C |
| ASW2DF.66 | 11:40:46.91 | -26:30:52.1 | 4.00 | 3.60 | 0.24 ± 0.06 | 0.22 ± 0.07 | 0.17 ± 0.19 | — | possible | C |
| ASW2DF.67 | 11:40:41.69 | -26:29:40.0 | 3.93 | 3.60 | 0.19 ± 0.05 | 0.28 ± 0.07 | -0.00 ± 0.10 | — | possible | C |
| ASW2DF.68 | 11:40:40.05 | -26:29:03.7 | 3.83 | 3.28 | 0.19 ± 0.05 | 0.45 ± 0.12 | 0.58 ± 0.10 | — | cloud-like | C |

Table notes: The columns are the same as those in Table [\[table: main catalog\]](#table: main catalog).

Furthermore, an independent visual inspection was conducted on the ALMA maps to verify the source catalogs extracted by the different codes and identify faint, extended sources below the detection limit (cite: Gonzalez2020). We visually identified 53 sources on the six ALMA maps, bypassing the use of any source extraction code. We further classified the 53 sources into four categories including “robust” — bright and prominent sources in the entire map; “possible” — obviously yet less bright sources with a high possibility of being genuine; “cloud-like” — sources exhibiting extended features; “edge” — sources resembling those in the “possible” category but located at the mosaic edges in each field. Among the 53 sources identified by our visual inspection, we find that 41 are included in the main catalog, leaving 12 eye-selected sources undetected by the “fixed” method. These 12 sources are also marked as tentative. Additionally, there is a small overlap: 13 tentative sources identified by the “individual” method include some of the 12 visually inspected tentative sources. By merging these two catalogs we obtain a supplementary catalog including 21 tentative sources in total. Notably, there are 16 sources identified as “robust” by visual inspection, all of which are included in the main catalog. Additionally, we note that all sources above 5$\sigma$ in the main catalog are recovered by visual inspection, suggesting the reliability of the visual inspection.

![image](plots/04_completeness.png) ![image](plots/04_boost_factor.png)

To summarize, we classify the 16 bright sources identified by visual inspection as “best” in category A, and the remaining 31 sources of the main catalog are included in category B. We note that all 47 ALMA sources in the main catalog were securely detected by the codes through the “fixed” method and will be used for the number counts calculations. The supplementary catalog comprises category C, encompassing 21 tentative sources identified through visual inspection and/or detected by codes using the “individual” method. The tentative sources in the supplementary catalog must be taken with caution and will not be used in the following number counts analysis. Figure [1](#fig: detections) shows the detections from category A, B, and C overlaid on the 1.2 mm continuum maps. In addition, we present our main catalog that includes 47 ALMA sources and a supplementary catalog comprising 21 tentative sources in Tables [\[table: main catalog\]](#table: main catalog) and [\[table: supp catalog\]](#table: supp catalog) respectively, sorted by their peak signal-to-noise ratios.

In order to examine the probability of the spurious sources in the science catalog, we calculate the purity of our images. The purity is defined as following: $$\begin{equation}
    p = \frac{N_{\rm pos}-N_{\rm neg}}{N_{\rm pos}}\,,
\label{eq: purity}
\end{equation}$$ where $p$ is the purity in each S/N bin, $N_{\rm pos}$ and $N_{\rm neg}$ are the positive and negative detections in a specific S/N bin. We obtain the negative detections by inverting the science map (multiplying the map by $-1$) and applying the same source extraction process used to detect positive peaks in the original map. Figure [3](#fig: purity) demonstrates the number of positive and negative detections, as well as the purity within the S/N range of $3.5-5.5$ from the “fixed” method. The purity reaches $\sim0.9$ at a threshold of S/N=4, indicating that around five sources are fake in our main catalog in a statistic sense. Sources above 5$\sigma$ are all considered to be real, which is in line with the results of (cite: Chen2023a). The purity estimations of the “individual” method with three codes are also plotted in Fig. [3](#fig: purity) for a comparison. We find that detections above 4$\sigma$ significance from the “fixed” method have the highest purity compared to any of the three codes using the “individual” method. This further confirms the reliability of the “fixed” method for estimating the rms noise. The adopted purity of 0.9 suggests that sources with peak S/N between 4.0 and 5.0 in our main catalog are a mixture of real and spurious detections, which might influence the subsequent analysis. To address this, we do not only conduct the analysis based on the main catalog but also perform an additional analysis using only \>5$\sigma$ sources in the following sections. The results from this subset are then compared with those from the entire main catalog to assess the robustness of our analysis.

## Flux measurement

We use several methods to measure the fluxes of our ALMA sources. The typical size of ALMA detections at $\sim$1 mm are rather compact with a median size of 0.1$''$$-$0.3$''$ (cite: Gonzalez2017; Umehata2018; Gomez2022). As the resolution of our images is $\sim$0.5$''$ or even larger, most of the detections are not spatially resolved in principle. The peak flux can serve as a good measurement of the total flux of a source in this case, since all emission from the source is convolved in the synthesized beam, and integrated into the brightest pixel. We firstly extract the peak fluxes of the ALMA sources from the images after the primary beam correction.

We also use the elliptical Gaussian model to fit our ALMA sources and estimate their integrated fluxes. Following (cite: Chen2023a), we fit the sources using the Levenberg-Marquardt algorithm in the Python package astropy.modeling. A cutout image with a size of 5$\times$major axis is extracted, centered on each source, and used for the fitting process. The amplitude, axial ratio, and positional angle are free to change for obtaining the best-fitting values. The integrated flux of the each source are calculated by summing up the flux density within the fitted Gaussian aperture before the correction of the synthesized beam. The uncertainty in the integrated flux for each source is estimated through the standard deviation obtained from 1000 iterations of the flux measurements using the same best-fitting Gaussian aperture at random positions.

Additionally, we measure the source fluxes using the aperture photometry, which is performed by the Python package photutils. The aperture size and shape are not identical in the literature. For example, the circular aperture with a diameter of 1.6$^{\prime\prime}$ and 2.0$^{\prime\prime}$ were used by (cite: Gomez2022) and (cite: Fujimoto2023) respectively. While (cite: Chen2023a) reported the scaled elliptical aperture (i.e. $2\times$ synthesized beam), which results in reliable flux measurement. Since the images in our six fields have different resolutions, we adopted the elliptical aperture of $2\times$ synthesized beam to measure the aperture fluxes for the sources in each field. We list the source fluxes measured from peak pixel, Gaussian fitting and aperture photometry, as well as the classification (eyes ID) from visual inspection in Table [\[table: main catalog\]](#table: main catalog) and [\[table: supp catalog\]](#table: supp catalog). We note that the detectable S/N, obtained from the ratio of the flux in the fifth brightest pixel of each source and the 1$\sigma$ noise, is also listed in the source table. The detectable S/N defines the threshold at which our method can detect each source, given the parameter $minarea=5$.

# Number counts

One of the main goals of the ASW$^2$DF survey is to obtain the number counts of the DSFGs in the Spiderewb protocluster field. The number counts derived from the initial source catalog suffer from biases such as incompleteness, purity, and flux boosting. In this section, we investigate the biases and calculate the effective area before calculating the number counts.

## Completeness and flux boosting

In general, the source detection rate increases with the intrinsic fluxes of ALMA sources, up to 100 percent above the flux density $\sim0.5$ mJy (cite: Gomez2022). Completeness is defined as the ratio between the detected sources and the real source number within a specific intrinsic flux bin. We used a Monte Carlo simulation to characterize the completeness of our science catalog. The main idea of the simulation is to build a mock catalog containing plenty of artificial sources and then assess the performance of the source extraction on the science images.

![](plots/05_eff_area.png)

Firstly, the 47 sources from our main science catalog (category A and B) were masked with the scaled elliptical aperture on the science images. Secondly, we divided the flux range from 0.1 to 3.1 mJy into 30 flux bins with a step of 0.1 mJy. In each flux bin, we generate an artificial catalog with 20 sources with assigned fluxes from the normal random distribution. The sources are positioned at random positions on the images where the primary beam response is greater than 0.5. We checked the source positions and removed the ones which are too close (i.e., less than 1 arcsec) to avoid additional bias from source blending. Thirdly, the point-like artificial sources were convolved with the synthesized beam and then injected into the image with primary beam correction, as this image reflects the intrinsic flux of the sources. We introduced point-like sources instead of sources with specific sizes (cite: Gomez2022), given the inherent complexity in estimating the intrinsic sizes of our ALMA sources, which may vary from those typically observed in general fields. Employing this conservative approach with point-like sources leads to a slight increase in completeness (cite: Gomez2022; Chen2023a) and ensures the robustness of subsequent overdensity analysis. We multiplied the newly created image by the primary beam response to obtain the PB uncorrected image. The source extraction and flux measurement were performed on this artificial image in the same manner as we did in Sec. [3.2](#sec: source extraction). The artificial sources were considered recovered when they were extracted less than 1 arcsec from their original injected positions. The procedure was repeated for 1000 iterations in each flux bin and each field. Finally, we obtained the mock catalog with tens of thousands of recovered artificial sources, which will be used for the completeness assessment.

Figure [4](#fig: comp_boost) demonstrates the completeness result from our mock catalog. The completeness over all six fields increases rapidly within the input flux range of 0.1$-$0.5 mJy, reaching 80% and 100% completeness at around 0.3 mJy and 0.6 mJy, respectively. As the 1$\sigma$ sensitivities vary between different fields (see Table [\[tab: obs\]](#tab: obs)), we also show the completeness estimation for Field 3 and 4 as they have the highest and lowest typical noise. It is clear that the completeness from these two fields follows a trend similar to the overall one, but is slightly different. We note that for the rest of the four fields, the completeness behaves the same as the one for all six fields and the discrepancies from Field 3 and 4 do not affect our results. We used the overall one for all six fields to correct for our science catalog.

The flux boosting effect can also be quantified through the MC simulation (cite: Hogg1998; Murdoch1973). This has been discussed in previous ALMA studies (cite: Hatsukade2016; Umehata2017; Umehata2018; Hatsukade2018; Franco2018; Gomez2022; Chen2023a). There are two independent reasons responsible for boosting fluxes (cite: Casey2014). One is the so-called Eddington bias (cite: Eddington1913). As the source number increases exponentially from the bright to the faint end, the sources scattering towards higher flux densities are much more than the number of sources scattered to lower flux densities. The other reason is that, the unresolved faint sources below the detection limit could also contribute to fluxes of the bright sources within the same beam, which are more often seen in single-dish submm/mm surveys (cite: Coppin2006).

We used the matched catalog from the MC simulation to measure the flux boosting and assess the performance of the flux measurements for our science catalog. We obtained the flux boosting factor by dividing the recovered flux ($S_{\rm out}$) by the input flux ($S_{\rm in}$) of each source in the matched catalog. Both two-dimensional Gaussian fitting and aperture photometry are used for the flux measurement on the recovered sources. We show the flux boosting estimation from these two methods as a function of the peak S/N in Figure [4](#fig: comp_boost). We notice that both two-dimensional Gaussian fitting and aperture photometry can recover the source flux accurately at \>5$\sigma$, within a 3 percent difference than intrinsic flux. At a peak S/N lower than five, both methods overestimate the source flux, in which a slightly higher boosting factor is shown in the Gaussian fitting method. This result is consistent with previous studies on similar comparison (cite: Gomez2022; Chen2023a).

We note from Fig. [4](#fig: comp_boost) that the aperture photometry suffers more from the scatters of the boosting factors in all S/N bins. This implies that the measured flux may deviate further from the intrinsic flux of the individual source. Furthermore, the flux is not significantly boosted (up to 10%) in both methods even in the lowest S/N region (4$\sigma$), rather lower than the flux uncertainty which is at a level of $\sim20$ percent. The Gaussian fitting fluxes are adopted in the following analysis, including the number counts calculation. We also tested the analysis with aperture photometry and obtained consistent results.

## Effective area

The science images produced by the interferometric observations are heavily influenced by the primary beam response. Our contiguous mapping observations have a better homogeneous sensitivity than the single pointing ones, but the noise still changes rapidly at the edge of each field. We calculate the effective area as a function of the local noise that increases from the center to the edges of the images. The local noise is calculated by dividing the “fixed” noise values by the primary beam response over the whole image where PB\>0.5. Thus, the local noise ranges from one to two times the “fixed” rms noise value in each field, as the primary beam correction decreases from 1 to 0.5.

![image](plots/06_counts_diff.png) ![image](plots/06_counts_inte.png)

Figure [5](#fig: area) shows the effective area versus the local rms noise in the combination of all six fields. The total effective area increases with the local rms noise and reach the maximum of 19.3 arcmin$^2$ at the noise of 120 $\mu$Jy, indicating the total area of the ASW$^2$DF survey. We note that the effective area curves are not as smooth as seen in the literature (cite: Gomez2022), showing several discontinuities due to the different depths in the six fields. We also show the 1$\sigma$ noise for six fields with vertical dashed lines, clearly demonstrating where the discontinuities start. For a comparison, we also list the survey area from the literature targeting both fields and protoclusters (cite: Oteo2016; Aravena2016; Hatsukade2016; Hatsukade2018; Umehata2017; Umehata2018; Gonzalez2020; Gomez2022; Chen2023a; Fujimoto2023; Pensabene2024; Adscheid2024; Wang2024) in Fig. [5](#fig: area). We choose these surveys because they were conducted at 1.1/1.2 mm, which are very close to our observations, minimizing the uncertainty due to the flux conversion (see Sec. [4.3](#sec: nc)). These surveys will be used for the following discussion on number counts and galaxy overdensity. We note that our survey reaches a good balance between survey area and sensitivity compared to the archival ALMA maps. Notably, the ADF22 survey observed the protocluster SSA22 at a comparable sensitivity and survey area as ours, offering a good chance for a comparison on the ALMA-detected DSFGs in protoclusters. We calculate the effective area for each source in our catalog before constructing the number counts. For each source, we divide the peak flux by the detection threshold of four to obtain the detectable noise, the effective area of this source is derived from the detectable noise and the curve in Fig. [5](#fig: area). The brightest sources can be detected anywhere within the survey area, thus having the maximum effective area. The faint sources can only be detected at 4$\sigma$ where the local noise is very low (i.e., the central region of each field), thus having a relatively smaller effective area.

## Number counts

We derive the number counts from the main science catalog (category A and B), including 47 sources in total. Each source has a contribution to the number counts as:

$$\begin{equation}
\label{eq: contribution}
\xi(S) = \frac{p(S)}{A_{\rm{eff}}(S)~C(S)}\,,
\end{equation}$$

where $S$ is the source flux, $p(S)$ is the purity which is defined in Eq. [\[eq: purity\]](#eq: purity). $C(S)$ is the completeness associated with the source flux. $A_{\rm{eff}}$ is the effective area for the source flux as described in the previous subsection. The sum of the contribution of the sources within a specific flux bin is the differential number counts:

$$\begin{equation}
\label{eq: diff_nc}
\frac{dN}{dS} = \frac{\sum \xi(S)}{\Delta S}\,.
\end{equation}$$

By summing up the contribution of sources that are brighter than the flux $S_0$, we can obtain the cumulative number counts:

$$\begin{equation}
\label{eq:cum_nc}
N(>S_0) = \sum \xi(S)\,.
\end{equation}$$

We construct the differential and cumulative number counts over the whole flux range from our main catalog. We calculate the uncertainties of the number counts by constructing 1000 rounds of the number counts. In each iteration, the flux of each source is randomly sampled based on its measured flux and the 1$\sigma$ noise. The new set of source fluxes are split into different flux bins for calculating the number counts. The median values of the 1000 rounds are adopted as the final number counts, and the 1$\sigma$ dispersion are taken as the number counts errors. We use the same approach to calculate the differential and cumulative number counts as well as their scatters, respectively.

|  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Survey | Type | $\lambda$ | Resolution | Depth | S/N | N$_{\rm source}$ | Area | Ref. |
|  |  | \(mm\) | ($^{\prime\prime}$) | ($\mu$Jy) |  |  | (arcmin$^2$) |  |
| ASW$^2$DF | M | 1.2 | $0.33-0.94$ | $40.3-57.1$ | 4.0 | 47 | 19.3 | This work |
| A$^3$COSMOS | S | $0.45-3$ | $-$ | $-$ | 5.4 | 2204 | 896.3 | (cite: Adscheid2024)$^a$ |
| A$^3$GOODS-S | S | $0.45-3$ | $-$ | $-$ | 5.4 | 491 | 149.6 | (cite: Adscheid2024)$^b$ |
| MQN01 (PCL) | M | 1.26 | $1.23\times1.05$ | 42 | 4.0 | 11 | 4.4 | (cite: Pensabene2024) |
| ALCS | M | 1.2 | $1.26\times0.98$ | 63.0 | 5.0 | 180 | 131.2 | (cite: Fujimoto2023)$^c$ |
| ALMACAL IX | S | $0.87-3$ | $-$ | $-$ | 5.0 | 132 | 149.0 | (cite: Chen2023a)$^d$ |
| GOODS-ALMA 2.0 | M | 1.1 | $0.45\times0.42$ | 68.4 | 5.0 (3.5) | 44 (88) | 72.4 | (cite: Gomez2022) |
| ASPECS-LP | M | 1.2 | $1.53\times1.08$ | 9.3 | 4.2 | 4.3 | 35 | (cite: Gonzalez2020)$^e$ |
| ASAGAO | M | 1.2 | $0.59\times0.53$ | 30 | 5.0 (4.0) | 25 (45) | 26 | (cite: Hatsukade2018) |
| ADF22 (PCL) | M | 1.1 | $0.53\times0.52$ | 73 | 5.0 (4.5) | 35 (58) | 20 | (cite: Umehata2018)$^g$ |
| ADF22 (PCL) | M | 1.1 | $1.16\times1.02$ | 60 | 5.0 | 18 | 6 | (cite: Umehata2017)$^h$ |
| ALMACAL I | S | 1.2 (0.87) | \<1 | $\sim$250 | 5.0 | 8 (11) | 16 (6) | (cite: Oteo2016) |
| ASPECS | M | 1.2 (3.0) | $1.70\times0.90$ | 12.7 | 3.5 | 9 | 1 | (cite: Aravena2016)$^i$ |
| ALMA Archive | S | 1.2 | $-$ | $-$ | 3.0 | 122 | 8.9 | (cite: Fujimoto2016) |
| SXDF–ALMA | M | 1.1 | $0.53\times0.41$ | 55 | 4.0 | 23 | 2 | (cite: Hatsukade2016) |
| Ex-MORA | M | 2.0 | $1.68\times1.44$ | 51 | 5.0 | 37 | 577 | (cite: Long2024) |
| MORA | M | 2.0 | $1.80\times1.40$ | 90 | 5.0 | 13 | 184 | (cite: Zavala2021) |
| AS2COSMOS | S | 0.87 | $0.80\times0.79$ | 190 | 4.8 | 260 | 5760$^f$ | (cite: Simpson2020) |
| ALMACAL VII | S | 0.65 | $0.34-0.98$ | $47-1022$ | 4.5 | 21 | 5.5 | (cite: Klitsch2020) |
| AS2UDS | S | 0.87 | $0.15-0.30$ | 250 | 4.3 | 695 | 50 | (cite: Stach2018) |
| ALMA Archive | S | 3.0 | \>1.0 | \<200 | 5.0 | 16 | 200 | (cite: Zavala2018) |
| GOODS-ALMA | M | 1.1 | $0.61\times0.59$ | 182 | 4.8 | 20 | 69 | (cite: Franco2018) |
| ALMA Frontier Fields | S | 1.1 | $0.50-1.50$ | 55-71 | 4.5 | 19 | 14 | (cite: Munoz2018) |
| ALMA HUDF | M | 1.3 | $0.71\times0.67$ | 34 | 3.5 | 16 | 4.5 | (cite: Dunlop2017) |
| ALMA UKIDSS UDS | S | 0.87 | $0.80\times0.65$ | 260 | 4.0 | 52 | 2808 | (cite: Simpson2015)$^j$ |
| ALMA Archive | S | 1.1 (1.3) | $-$ | $7.8-52.1$ | 3.5 | 50 | 3.4 (2.4) | (cite: Carniani2015) |
| ALMA Archive | S | 1.2 | $0.6-1.5$ | $17-88$ | 4.0 | 11 | 2.9 | (cite: Ono2014) |
| ALMA Archive | S | 1.3 | $0.6-1.3$ | $40-100$ | 3.8 | 15 | 2.7 | (cite: Hatsukade2013) |
| ALESS | S | 0.87 | $1.60\times1.15$ | 400 | 3.5 | 32 | $-$ | (cite: Hodge2013)$^k$ |
| ALESS | S | 0.87 | $1.80\times1.20$ | \<600 | 3.5 | 99 | 880 | (cite: Karim2013) |

Table notes: The top panel shows the references we used for the discussion of number counts and galaxy overdensity. Surveys targeting protoclusters are marked with “PCL” in brackets. Depending on the observing mode, contiguous mapping surveys are marked as “M” and single pointings or the collections of archival surveys are marked as “S”. (a&b): The S/N threshold and source number are adopted from the blind search category, the survey area is the combined area from band 3 to band 9; (c): The resolution and depth are adopted from the average of 33 fields; (d): The resolution and depth are various between observations, the source number and survey area is adopted from band 6 at 1.2 mm; (e): The resolution and depth are from the natural weighted data; (f): The area is from the S2COSMOS survey (cite: Simpson2019) and used for constructing their number counts; (g): The resolution and depth are the mean values from the 0.60$''$ tapered images; (h): The resolution is from the FULL/LORES data, which was primarily used in their analysis; (i): The resolution, depth and source number are adopted from 1.2 mm data; (j): The resolution and depth are adopted from the low resolution “detection” maps, the survey area is from the parent single-dish survey; (k): The resolution and depth are adopted from the median value from the ALESS pointings.

Figure [6](#fig: nc) shows the number counts for each field, as well as all six fields together. The flux bins for each field are the same with that from the total fields but shifted for 0.02 mJy to avoid the overlap. We note that in the main catalog, there are only six sources brighter than 1 mJy and one brighter than 2 mJy. This aligns with the source density in GOODS-ALMA (cite: Gomez2022), where 18 (7) sources brighter than 1 (2) mJy are found in a survey area four times larger than that of our ALMA maps. However, there are 16 sources brighter than 1 mJy found in the ADF22 survey after accounting for the flux conversion (cite: Umehata2018). The number of bright sources is around three times higher than compared to the 6 bright sources (\>1 mJy) in the Spiderweb field, within a similar survey area of $\sim20$ arcmin$^2$. We argue that this is because the DSFGs are located near the gas rich filaments in SSA22, which has a relative earlier evolutionary stage at higher redshift (cite: Umehata2019). Huge amount of gas is accreted into these galaxies and tremendous star formation is triggered subsequently.

![](plots/07_density_map.png)

Our ASW$^2$DF survey targets the prominent Spiderweb protocluster at $z=2.16$, therefore, it is important to compare our results to the number counts in general fields and other protoclusters at similar wavelengths from the literature. In Fig. [6](#fig: nc), we plot the results of ALMA observations at 1.1/1.2 mm from the literature (cite: Oteo2016; Aravena2016; Fujimoto2016; Hatsukade2016; Hatsukade2018; Umehata2017; Umehata2018; Gonzalez2020; Gomez2022; Chen2023a; Pensabene2024; Adscheid2024) as we mentioned in previous section. The central wavelength of our observations is 1.2 mm, and for the number counts at 1.1 mm wavelength we re-scale the flux density to make the number counts comparable with our results. We adopt an average spectral energy distribution from a sample of ALESS SMGs (cite: da_Cunha2015), and assume a redshift of 2.2 which is close to that of the Spiderweb protocluster. We then obtain the flux conversion factor of $S_{\rm 1.1\,mm}/S_{\rm 1.2\,mm}$ to be 1.29, identical to that in (cite: Umehata2018) by using a modified black body model. We note that even at the same wavelength, the number counts from different surveys show a scatter due to the variation of the survey designs, observing depth and data analysis.

By comparing our results with the field number counts in the literature as shown in Fig. [6](#fig: nc), we find that both differential and cumulative number counts in the entire Spiderweb field are higher than those in general fields, especially at the faint end. Qualitatively, it is clearly seen that the cumulative number counts in Field 1 to 3 are overdense than that of general fields, while Field 4 to 6 show comparable or less dense signatures. We notice that the cumulative number counts in Field 1 are extraordinarily higher than in the other fields at the bright end, as three out of six bright sources (\>1 mJy) are in Field 1. Among the previous ALMA contiguous mapping surveys — only a few targeted on protocluster regions (cite: Umehata2015; Umehata2017; Umehata2018; Pensabene2024) —, we also plot the number counts in the field of the protocluster SSA22 at $z=3.1$, which shows an excess by a factor of three to five at 1.1 mm (cite: Umehata2017; Umehata2018). For the protocluster around the quasar MQN01, we adopt their source catalog and construct the number counts after accounting for the purity (cite: Pensabene2024), as shown in Fig. [6](#fig: nc). We can see that our results are comparable with the number counts in SSA22 (cite: Umehata2018) and MQN01 (cite: Pensabene2024). We will calculate and discuss the overdensity of ALMA sources quantitatively in the next section.

# Discussion

## Overdensity of DSFGs detected by ALMA

Based on the 47 ALMA sources in our main science catalog, we examine if there is an excess of DSFGs in the Spiderweb protocluster. In Table [\[tab: surveys\]](#tab: surveys), we summarize the surveys conducted in the last decade, constructing ALMA number counts mostly in bands 6 and 7. We collected the source catalogs from field surveys (cite: Oteo2016; Aravena2016; Fujimoto2016; Hatsukade2016; Hatsukade2018; Umehata2017; Umehata2018; Gonzalez2020; Gomez2022; Chen2023a; Pensabene2024; Adscheid2024) as listed in the upper panel of Table [\[tab: surveys\]](#tab: surveys), which are also plotted in Fig. [6](#fig: nc). For the sake of fairness, we only count the sources brighter than 0.23 mJy at 1.2 mm, to ensure a reliable detection of each source at \>4$\sigma$ significance, given the sensitivity of $\sim$50 $\mu$Jy in our observations as well as most archival surveys at 1.2 mm. Similarly, a flux lower limit of 0.3 mJy is adopted for reliable detections (\>$4\sigma$) in the surveys at 1.1 mm, which mostly have $\sim$70 $\mu$Jy sensitivity (cite: Umehata2018; Gomez2022). We calculate the number density of the ALMA sources in our main catalog and public surveys by simply dividing the source numbers by the survey area respectively. We obtain a number density of $\rho\sim2.1\pm0.3\,\rm arcmin^{-2}$ in the field of the Spiderweb protocluster, surpassing the average number density of $\rho\sim1.0\pm0.4\,\rm arcmin^{-2}$ in general fields. The number density of ALMA sources detected in the SSA22 field is $\rho\sim2.8\pm0.4\,\rm arcmin^{-2}$, slighly higher than that in the Spiderweb field. The overdensity of three times than fields is consistent with that reported in (cite: Umehata2017; Umehata2018). In the protocluster around the quasar MQN01 (cite: Pensabene2024), the surface density is estimated to be $\rho\sim2.0\pm0.4,\rm arcmin^{-2}$, revealing an overdensity of twice and comparable to that in the Spiderweb protocluster. The similarity of number counts between the MQN01 and Spiderweb fields can also be seen in Fig. [6](#fig: nc).

+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
|             | Field 1          | Field 2         | Field 3         | Field 4        | Field 5        | Field 6        | Total           |
+:===========:+:================:+:===============:+:===============:+:==============:+:==============:+:==============:+:===============:+
| $S$ \[mJy\] | dN/d$S$ \[10$^3$ mJy$^{-1}$deg$^{-2}$\]                                                                                   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $0.20-0.31$ | $108.27\pm88.26$ | $41.34\pm30.67$ | $32.81\pm18.10$ | $11.33\pm4.31$ | $20.11\pm8.39$ | $10.52\pm3.79$ | $66.73\pm66.73$ |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $0.31-0.50$ | $13.24\pm7.22$   | $43.96\pm20.69$ | $37.14\pm20.03$ | $6.72\pm2.36$  | $10.58\pm4.18$ | $10.20\pm4.72$ | $14.00\pm14.00$ |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $0.50-0.80$ | $11.58\pm2.36$   | $9.76\pm6.14$   | $21.90\pm14.25$ | $6.43\pm2.04$  | $4.61\pm1.74$  | $6.79\pm2.69$  | $9.10\pm9.10$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $0.80-1.27$ | $2.31\pm0.67$    | $2.08\pm0.36$   | $3.20\pm1.43$   | $2.86\pm1.00$  | $2.02\pm0.00$  | $2.53\pm0.89$  | $2.33\pm2.33$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $1.27-2.02$ | $3.19\pm0.64$    | $1.27\pm0.00$   | $1.27\pm0.00$   | $1.27\pm0.00$  | $-$            | $-$            | $0.77\pm0.77$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $S$ \[mJy\] | N(\>$S$) \[10$^3$ deg$^{-2}$\]                                                                                            |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 0.25        | $11.93\pm3.73$   | $14.95\pm2.42$  | $15.20\pm1.66$  | $4.69\pm0.49$  | $4.54\pm0.99$  | $5.21\pm0.50$  | $9.38\pm2.21$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 0.40        | $7.25\pm0.72$    | $7.13\pm3.60$   | $11.23\pm3.29$  | $3.82\pm0.20$  | $2.33\pm0.70$  | $3.66\pm0.69$  | $5.44\pm0.40$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 0.65        | $4.91\pm0.81$    | $1.85\pm0.68$   | $2.96\pm1.85$   | $2.06\pm0.39$  | $1.09\pm0.34$  | $1.98\pm0.59$  | $2.82\pm0.31$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 1.05        | $2.86\pm0.00$    | $0.95\pm0.00$   | $0.96\pm0.01$   | $0.95\pm0.04$  | $-$            | $0.95\pm0.00$  | $0.99\pm0.09$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 1.69        | $1.81\pm0.29$    | $-$             | $-$             | $-$            | $-$            | $-$            | $0.35\pm0.06$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| $S$ \[mJy\] | ALMA overdensity                                                                                                          |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 0.25        | $2.25\pm0.74$    | $2.82\pm0.54$   | $2.87\pm0.42$   | $0.88\pm0.13$  | $0.86\pm0.21$  | $0.98\pm0.14$  | $1.77\pm0.45$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 0.40        | $2.13\pm0.30$    | $2.09\pm1.08$   | $3.29\pm1.02$   | $1.12\pm0.13$  | $0.68\pm0.22$  | $1.07\pm0.23$  | $1.59\pm0.20$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 0.65        | $2.76\pm0.56$    | $1.04\pm0.40$   | $1.66\pm1.06$   | $1.16\pm0.26$  | $0.61\pm0.20$  | $1.11\pm0.36$  | $1.58\pm0.26$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 1.05        | $3.21\pm0.47$    | $1.07\pm0.16$   | $1.07\pm0.16$   | $1.07\pm0.16$  | $-$            | $1.07\pm0.16$  | $1.11\pm0.19$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| 1.69        | $4.63\pm1.20$    | $-$             | $-$             | $-$            | $-$            | $-$            | $0.90\pm0.24$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| U18 field   | $2.64\pm0.83$    | $3.31\pm0.53$   | $3.36\pm0.37$   | $1.04\pm0.11$  | $1.00\pm0.22$  | $1.15\pm0.11$  | $2.08\pm0.49$   |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
|             | ALMA overdensity around the SW galaxy                                                                                     |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| Radii (kpc) | \<150            | $150-300$       | $300-450$       | $450-600$      | $600-750$      | $750-900$      | $900-1050$      |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+
| Factor      | 3.5              | 2.4             | 2.8             | 4.0            | 1.6            | 1.3            | 1.4             |
+-------------+------------------+-----------------+-----------------+----------------+----------------+----------------+-----------------+

Table notes: The overdensity in each field at each flux bin is calculated based on the field results from (cite: Chen2023a) and (cite: Gomez2022). The overdensity results with a name “U18 field” are calculated based on the field results from (cite: Umehata2018).

We use the derived number counts to compare with the results from general fields and quantify the overdensity of DSFGs in the Spiderweb protocluster. We adopt the recent results from the ALMACAL (cite: Chen2023a) and GOODS-ALMA (cite: Franco2018; Gomez2022) surveys because they have the largest survey area in individual pointings and contiguous mosaic modes respectively, minimizing the effect of the selection bias and cosmic variance. (cite: Chen2023a) constructed the number counts at exactly the same wavelength as in our observations, thus avoiding the uncertainty from the flux conversion. We convert the number counts at 1.1 mm in GOODS-ALMA survey to that at 1.2 mm by using the factor of 1.29 mentioned above. The discrepancies in differential number counts between bright and faint ends will also affect the overdensity estimation. Thus we use the cumulative number counts to evaluate the overdensity for the entire population of the ALMA sources. Based on the sensitivity of our science maps and the flux range of the main catalog, we adopt the five flux bins in logarithmic space within a flux range of 0.25$-$1.69 mJy and calculate the cumulative number counts. We only compare our results with the data points in the literature instead of their best-fitting curves in order to avoid fitting errors. The overdensity is characterized by the ratio between the number counts in the Spiderweb protocluster and the results from general fields. We note that the cumulative number counts in the A3COSMOS survey (cite: Adscheid2024) are not provided and cannot be directly compared. Nevertheless, their differential number counts are in a good agreement with that in the literature, thus the overdensity calculation would be the same if their cumulative number counts were available.

The number counts and overdensity of our ALMA sources are shown in Table [\[tab: nc\]](#tab: nc). At the lowest flux limit of 0.25 mJy, we estimate the number counts in the Spiderweb protocluster around two times that of general fields. This is consistent with the previous estimation mentioned above by only counting the source numbers. The overdensity is prominent in the eastern part of the Spiderweb protocluster (from Field 1 to Field 3), while the number counts in the western part (from Field 4 to Field 6) are close to that of general fields. In contrast, the HAEs are mostly concentrated around the Spiderweb galaxy (i.e., the protocluster center), with filament-like structures extending to the east and west (cite: Koyama2013; Shimakawa2018b). Notably, Field 1 shows the highest overdensity of ALMA sources at the bright end, the number density excess increases with the flux bins reaching up to 3.2 (4.6) at \>1.05 (1.69) mJy. This trend can also be seen in the cumulative number counts as shown in Fig. [6](#fig: nc). In addition, we measured the overdensity factor around the Spiderweb galaxy of 3.5, 2.4, 2.8, 4.0, 1.6, 1.3 and 1.4 in radii of $<150 , 150-300, 300-450, 450-600, 600-750, 750-900, 900-1050$ kpc, respectively.

(cite: Umehata2018) reported that the number counts of 1.1 mm ALMA sources in SSA22 have an overdensity by a factor of three to five. We note that the number counts in general fields used for the comparison in (cite: Umehata2018) are derived from the best-fitting of combined data from various surveys (cite: Karim2013; Simpson2015; Aravena2016; Hatsukade2016; Oteo2016), which is also shown in the right panel of Fig. [6](#fig: nc). We notice that the best-fitting curve used in (cite: Umehata2018) is lower than the cumulative number counts in (cite: Gomez2022) and (cite: Chen2023a) which were used for our comparison. We compare our number counts with the fitting curve of general fields given in (cite: Umehata2018) and obtain an overdensity of 2.08 in the entire Spiderweb field, which is slightly higher to the result of $\sim$1.8 obtained from the comparison with (cite: Chen2023a) and (cite: Gomez2022). We also list these results for each field compared to the field presented in (cite: Umehata2018), in the last row of ALMA overdensity in Table [\[tab: nc\]](#tab: nc). As previously mentioned, we also restrict our analysis to sources (\>5$\sigma$) with purity close to one to calculate their cumulative number counts. This results in an overdensity of 1.7 at the lowest flux bin compared to field, consistent with those from the entire main catalog within 10% uncertainties.

We note that the Spiderweb field was also covered by previous surveys observed with single-dish telescopes. The analysis of `Herschel` 500 $\mu$m sources confirmed an overdensity by a factor of two within 6 cMpc around the central radio galaxy (cite: Rigby2014), which is exactly the same as our results. (cite: Dannerbauer2014) reported 16 SMGs detected by APEX LABOCA over an area of $\sim$140 arcmin$^2$ around the Spiderweb galaxy. The number density of LABOCA SMGs is up to four times that of general fields at 870 $\mu$m down to $S_{870\,\mu \rm m}=7$ mJy. Similarly, 47 sources are detected by ASTE/AzTEC at 1.1 mm in the Spiderweb field, over an area of $\sim$210 arcmin$^2$ (cite: Zeballos2018). The 1.1 mm AzTEC sources also show an overdensity by a factor of $\sim2$ compared to general fields. These results show a good agreement with our calculations, further confirming the overdensity nature of dust-obscured galaxies in the Spiderweb protocluster.

## Spatial correlation between different populations

The spatial distributions of different member galaxies such as HAEs and DSFGs, cannot only reveal the local overdensities in protoclusters, but also help to depict the large scale structure over up to hundreds of comoving Mpc. Distinct sub-components (i.e., density peaks) and filamentary structures associated with protoclusters have been reported in several studies through different populations (cite: Matsuda2005; Casey2015; Cucciati2018; Shimakawa2018a; Zheng2021; Shi2021; Sun2024). Based on narrow-band imaging, the filamentary structures were identified over $\sim$10 cMpc scale traced by HAEs, running across from the east to the south-west of the Spiderweb protocluster (cite: Koyama2013; Shimakawa2018b). (cite: Jin2021) reported that CO emitters seems to trace the large scale structure extending to more than one hundred cMpc, suggestive of a super-protocluster or a filamentary structure linking to the Spiderweb field.

The surveys of the HAEs and CO emitters cover overall the footprint of our ALMA observation. In Figure [7](#fig: density map), we show the positions of HAEs, CO emitters, and ALMA-detected DSFGs. We build the density maps of HAEs (in blue), DSFGs (in orange), and CO emitters (in green) based on the 5th neighbor analysis. The adopted method and the constructed HAE density map are identical to those of (cite: Shimakawa2018b). It is clearly seen that the HAEs are highly concentrated around the Spiderweb galaxy. In contrast, the concentration of ALMA sources does not overlap with the HAE density peak centered on the radio galaxy, as reported by (cite: Dannerbauer2014). The offset between these two populations was also found in two massive protoclusters at similar redshift (cite: Zhang2022) with a single-dish instrument. We can see that the CO emitters are roughly associated with the density peaks of the ALMA sources and are located near the filaments identified by the HAEs.

We quantitatively evaluated the overdensity factors of HAEs and CO emitters in each field and compared them with that of DSFGs, as the ALMA observations were equally divided into six fields from east to west.

We note that the overall overdensity factors of DSFGs, HAEs and CO emitters vary a lot, and range from a factor of two to more than one order of magnitude. We count the number of each population covered by our ALMA observations, and divide the number by the ALMA survey area of $\sim20\,{\rm arcmin}^2$ to obtain the average number density of each population over the entire ALMA footprint. We then calculate the surface density in each field with the same method and derive the excess of number density by normalizing them with the overall average number density. We show the results in the upper panel of Figure [8](#fig: pop_comparison). It is clearly seen that the HAEs are highly concentrated in Fields 3 and 4, corresponding to the region surrounding the central Spiderweb galaxy. Both HAEs and DSFGs show significant excess in Field 1, exceeding their respective overall overdensities within the ALMA footprint. All three populations suggest lower overdensities in the western part, i.e., Fields 5 and 6, compared to the entire region of the protocluster.

![](plots/08_pop_comparison.png)

In the lower panel of Fig. [8](#fig: pop_comparison), we show the cumulative distribution function (CDF) of HAE, DSFGs and CO emitters as a function of distance to the central Spiderweb galaxy. Again, the HAEs are more concentrated towards the protocluster center than the other two populations. Approximately half of the HAEs are detected within the R$_{200}$, which is defined by (cite: Shimakawa2014) using both spectroscopically confirmed LAEs and HAEs. Only $\sim30$ percent of DSFGs and CO emitters are found within the R$_{200}$, and these two populations show very similar spatial distributions. This may indicate that cold gas has accumulated along filaments on the outskirts of the protocluster, where galaxies were fed abundant gas and triggered with intense star formation before falling into the cluster center.

| Populations | K-S statistic | Probability | Significance |
|:-----------:|:-------------:|:-----------:|:------------:|
| HAE & DSFG  |     0.264     |    0.084    | 1.8$\sigma$  |
|  HAE & CO   |     0.261     |    0.094    | 1.7$\sigma$  |
|  DSFG & CO  |     0.170     |    0.623    | 0.5$\sigma$  |

: Results of 2D K-S test on the different source populations in the Spiderweb protocluster field.

Furthermore, we adopted a 2D Kolmogorov-Smirnov test (cite: Peacock1983; Fasano1987) to assess the correlation between HAEs, DSFGs, and CO emitters. In Table [2](#tab: ks_test), we show the results of the K-S test on these three populations. By comparing HAEs with DSFGs, the probability of them being drawn from the same distribution is 0.084, similar to that between HAEs and CO emitters. However, given the low significance (\<2$\sigma$) of K-S test between HAEs and the other two populations, we cannot determine that they are totally distinct populations. This is probably due to the fact that some HAEs are extremely massive star-forming galaxies, they are easily detected in dust and CO emissions and therefore overlap with the populations of DSFGs and CO emitters (cite: Gullberg2016; Emonts2016; Emonts2018; Dannerbauer2017).

(cite: Zhang2022) reported that SMGs and HAEs are drawn from different spatial distributions in two protoclusters with higher significance from the K-S test. This may indicate that DSFGs and HAEs have stronger anticorrelation over a larger scale of $\sim$30 cMpc and that their density peaks are representative of different local environments within protoclusters. This trend is also suggested by the fraction of DSFGs/SMGs containing HAE counterparts. There are ten SMGs found to host HAE counterparts among a sample of 97 SMGs in the two MAMMOTH protoclusters (cite: Zhang2022), resulting in a detection rate of around 10 percent. When focusing on the spiderweb protocluster on a smaller scale, 10 of 47 DSFGs in our main catalog are HAEs within a matching radius of 1 arcsec, making the detection rate of HAE counterparts to be 20 percent (see Table [\[table: main catalog\]](#table: main catalog)). We note that there is a significant difference between the spatial resolutions of the single-dish telescope used in (cite: Zhang2022) and ALMA in our work, while the consistency between our ALMA results and previous LABOCA results (cite: Dannerbauer2014) has already shown the authenticity of single-dish observations. More ALMA observations towards the Spiderweb field covering larger scale are required to confirm the relations between HAE and DSFG populations.

![](plots/09_gas_mass.png)

Interestingly, we find that ALMA-detected DSFGs and CO emitters have a rather high probability (62.3%, see Table [2](#tab: ks_test)) coming from the same spatial distribution, consistent with the results of the CDF analysis shown in Fig. [8](#fig: pop_comparison). This is reasonable as the molecular gas reservoirs are an indispensable fuel for star formation and DSFGs are dust obscured galaxies with intense star formation. The COALAS survey covers an area similar to that of our observations, and there are 43 ALMA sources in the main catalog located in the COALAS footprint. We note that the depth of the COALAS survey is not completely homogeneous over the whole map, see for details (cite: Jin2021) and (cite: Chen2024). We find that 13 ALMA sources are confirmed as CO emitters by cross-matching these two populations with a varied radius of $2-6$ arcsec scaled by the ATCA synthesized beams (cite: Jin2021). The matching results are the same as those using a fixed radius of 3 arcsec adopted in (cite: Jin2021). Interestingly, seven (6 robust, 1 tentative) out of the 13 CO emitters with ALMA counterparts are extended molecular gas reservoirs, indicating a fraction of extended gas reservoirs around 50%, higher than that reported in (cite: Chen2024). This further suggests that cluster galaxies with extended gas reservoirs are the results of efficient accretion of cold gas inflows along filaments, and starbursts fueled by sufficient gas are responsible for the growth of the stellar population in these galaxies (cite: Chen2024).

This may raise these questions: If the ALMA sources and CO emitters are indeed correlated and indicative of intense star formation activities associated with significant gas inflows, why have we only detected 30 percent (13/43) of ALMA sources with CO emissions? We compare the depths of the ALMA and ATCA observations and estimate how sensitive they are in terms of molecular gas mass. (cite: Scoville2023) proposed (cite: Scoville2014; Scoville2016) that the gas mass can be determined from the dust luminosity at the Rayleigh–Jeans (RJ) tail due to its optically thin nature. By assuming a dust temperature of 25 K, spectral index $\beta=2$, and a constant gas-to-dust-mass ratio of 105 (cite: Draine2011), we derive the gas masses of our ALMA sources to be $2.0-27.3\times10^{10}\,{\rm M}_{\odot}$ based on the Gaussian fitting flux measurements. We note that the gas masses obtained above from dust luminosity are based on the assumption of normal star-forming galaxies (cite: Scoville2023). (cite: Jin2021) divided their CO emitters into two regimes, and used a $\alpha_{\rm CO, SB}=0.8$ and $\alpha_{\rm CO,SFG}= 3.6$ (${\rm M}_{\odot}\,[{\rm K\,km\,s}^{-1}\,{\rm pc^2}]^{-1}$) to obtain the gas masses of starbursts and star-forming galaxies, respectively.

In Figure [9](#fig: gas_mass), we compare the molecular gas masses obtained from 1.2 mm fluxes and CO luminosities of the 13 ALMA sources with CO emitter counterparts. Following (cite: Jin2021), we assign different $\alpha_{\rm CO}$ values for each source individually, and mark them with blue dashed circles. It is clearly seen that the gas masses obtained from dust and CO emissions do not agree with each other. Moreover, we use a single $\alpha_{\rm CO}$ value of $0.8\,{\rm M}_{\odot}\,({\rm K\,km\,s}^{-1}\,{\rm pc^2})^{-1}$ for all the 13 ALMA sources and repeat this process with a higher $\alpha_{\rm CO}$ value of $3.6\,{\rm M}_{\odot}\,({\rm K\,km\,s}^{-1}\,{\rm pc^2})^{-1}$. We can see from Figure [9](#fig: gas_mass) that the gas measurements from dust emission are significantly different with the lower $\alpha_{\rm CO}$ conversions, while comparable with the gas masses derived from higher $\alpha_{\rm CO}$ with large scatters. Thus, we conclude that the reliability of molecuar gas masses derived through dust measurements have to be seen with caution. By adopting an $\alpha_{\rm CO}$ of $3.6\,{\rm M}_{\odot}\,({\rm K\,km\,s}^{-1}\,{\rm pc^2})^{-1}$, we estimate the CO emitters with a lower limit of gas mass to be $5.0\times10^{10}\,{\rm M}_{\odot}$ in the COALAS survey, corresponding to an observing flux of 0.4 mJy at 1.2 mm. This means that about half of ALMA sources have gas reservoirs below the ATCA detection limit.

![](plots/09_cosmic_sfrd.png)

In addition, we note that the CO emitters are detected within a quite large velocity range, corresponding to $\sim$120 cMpc along the line of sight (cite: Jin2021), much larger than the spatial coverage of both the ALMA and ATCA observations which have a scale of $\sim6\times9$ cMpc$^2$. The 2D K-S test are solely based on the sky positions and thus cannot determine the correlation between DSFGs and CO emitters in redshift space. The upcoming analysis on the JWST data (cite: Dannerbauer2021) and more spectroscopic observations will help to confirm the membership of these ALMA sources, and unveil the nature of these dusty sources in relation to the CO emitters and surrounding large scale structures.

In Fig. [7](#fig: density map), we also show the seven LABOCA sources (cite: Dannerbauer2014) and five AzTEC sources (cite: Zeballos2018) within the coverage of our ALMA observations. All of them are revolved by our ALMA observations and located at the eastern part of the Spiderweb protocluster. In particular, there are three LABOCA sources and two AzTEC sources in Field 1, making this region an extreme concentration of DSFGs over the entire Spiderweb field. This also matches well with previous results based on the field-to-field number counts and the CDF analysis. The similar distributions of LABOCA/AzTEC sources and ALMA sources verify that DSFGs revealed by ALMA are indeed concentrated in the eastern part of the Spiderweb field, without affected by the observing differences between six fields (see Table [\[tab: obs\]](#tab: obs)).

(cite: Dannerbauer2014) reported, based on the coarse spatial resolution of LABOCA, that the spatial distribution of SMG overdensity seems to be similar to the eastern filaments. Overall, we can see from Fig. [7](#fig: density map), that both the DSFGs and CO emitters are concentrated close to the filaments traced by HAEs, even though they are likely drawn from different spatial distributions compared to that of HAEs. This is consistent with the basic concept that galaxy clusters assemble their mass by accreting gas and galaxies from the cosmic web through filaments as highways (cite: Zel’dovich1970; Rost2021). The abundant gas supplies were cooling down and sustained around the filaments by accretion shocks (cite: Rost2021; Rost2024), and galaxies close to the filaments on the outskirts of the protocluster were fueled by cold gas accretion (cite: Dekel2009; Daddi2021). On the other hand, the accumulation of gas materials and shocks could trigger starbursts in these DSFGs through more frequent galaxy mergers and interactions, which are closely related to the local environments (cite: Liu2023; Naufal2023). To this end, a panoramic mapping of three-dimensional Ly$\alpha$ emission is crucial to reveal the underlying gas reservoirs and cold streams not only in the center of the protocluster, but also on the outskirts extending to several Mpc (cite: Umehata2019; Martin2023).

We calculate the cosmic SFR density of the ALMA sources over a survey area of $\sim$20 arcmin$^2$, corresponding to 48 cMpc$^2$. We firstly convert the fluxes of these ALMA sources into fluxes at 850 $\mu$m according to the ALESS SED (cite: da_Cunha2015), then derive the SFR for each source based on the linear relation from (cite: Cowie2017). The derived SFR density depends significantly on the assumed volume. If conservatively, we adopt a ligh-of-sight distance of 120 cMpc from (cite: Jin2021), in which the CO emitters are assumed to trace a super structure, we obtain an SFR density to be $1.78\pm0.35\,{\rm M}_\odot\,\rm{yr}^{-1}\rm{cMpc}^{-3}$, being around 14 times that of the average cosmic SFR density (cite: Madau2014) and well above the predictions of simulations (cite: Bassini2020). However, if considering a 2 Mpc sphere as adopted in (cite: Dannerbauer2014), which is representative of a core-like volume, we obtain a SFR density to be $58.21\pm11.41\,{\rm M}_\odot\,\rm{yr}^{-1}\rm{cMpc}^{-3}$. Moreover, within a smaller group size of $\sim$400 kpc sphere (see Sec. [5.3](#sec: discuss3)), we would obtain a much higher SFR density of $1171.25\pm233.20\,{\rm M}_\odot\,\rm{yr}^{-1}\rm{cMpc}^{-3}$. We show our results in Figure [10](#fig: sfrd), together with those from protoclusters at different scales and fields from the literature. The SFR density of our ALMA sources in a core-like 2 Mpc sphere agrees very well with that of (cite: Dannerbauer2014), and are comparable to the cores of other protoclusters at similar redshift. When focusing on the group size, the estimated SFR density will be even much higher than coeval protoclusters, while comparable to the starburst group LH-SBC3 at $z=3.95$ (cite: Zhou2024), DRC (cite: Oteo2018) and STP2349$-$56 (cite: Hill2020). We emphasize that due to the uncertainty of the calculations of the cosmic volume, one should take the cosmic SFR density with caution.

## DSFGs related to the evolution of the Spiderweb protocluster

The high concentration of DSFGs in a small region might indicate the existence of a protocluster core or galaxy groups with intense starburst activities. There are 14 (23) sources over a physical scale of 130 (300) kpc confirmed by ALMA in the core of the protocluster SPT2349$-$56 at $z=4.3$ (cite: Miller2018; Hill2020). An extreme protocluster core, DRC, was also discovered with at least 10 ALMA sources over $\sim$300 kpc at $z=4.0$ (cite: Oteo2018; Long2020). (cite: gomez2019) reported two `Herschel` protoclusters, HELAISS02 at $z=2.17$ and HXMM20 at $z=2.6$, confirmed by ALMA with four and five detections over a similar scale. Most recently, the first results of the NICE large program showed that a starburst galaxy group at $z=3.95$ with four members was discovered within a diameter of 180 kpc (cite: Zhou2024).

These results motivate us to estimate the excess of the DSFGs over a smaller scale and examine their local environment. In Fig. [7](#fig: density map), we can see that there are two distinct concentrations of ALMA-detected DSFGs around DKB01/DKB03 and DKB02 respectively. There are eight (six) DSFGs around DKB01/DKB03 (DKB02) over a scale of 400 kpc, suggesting an excess by a factor of \>12 compared to that in general fields. We tentatively regard these concentrations as two galaxy groups, SW-GE1 and SW-GE2, with intense star formation activities. We calculate the total SFR of these two groups to be $2688\pm385$ and $806\pm121\,{\rm M}_\odot\,\rm{yr}^{-1}$. The estimated SFRs of these groups are comparable with that of the central Spiderweb complex (cite: Shimakawa2018b). However, when focusing on the traditional HAE overdensity peaks centered on the Spiderweb galaxy (ASW2DF.17), we find only two ALMA sources within a comparable physical scale. Similarly, the SMG DKB12 has been confirmed as a galaxy group containing at least four HAE members within 60 kpc (cite: Dannerbauer2014; Shimakawa2018b), which is even smaller than the scale of 400 kpc adopted here. Only one ALMA source (ASW2DF.01) is related to these HAEs. This is consistent with previous findings, which show that the clustering of ALMA-detected DSFGs is clearly deviated from HAE density peaks.

We note that three out of eight ALMA-detected DSFGs (ID: 02, 03, 33) in group SW-GE1 have been spectroscopically confirmed by either CO(1-0) and/or H$\alpha$ emission (cite: Jin2021; Perez2023). Moreover, two previously reported HAEs but undetected by ALMA are located in this region (cite: Perez2023), and one of them is also a CO emitter (cite: Jin2021). These five confirmed members have already proven that SW-GE1 contains an extreme overdensity of DSFGs of at least 10, and even more when considering their volume density. Three additional ALMA sources (ID: 08, 09, 13) at \>5$\sigma$ are identified in this group, with two exhibiting clear $K_{\rm s}$ counterparts (cite: Shimakawa2018b), suggesting they are likely group members.

Interestingly, the sources ASW2DF.03 and ASW2DF.33, which have been previously confirmed by (cite: Dannerbauer2014) and dubbed as DKB01b and DKB03, are recently reported to host extended gas reservoirs up to $\sim70$ kpc (cite: Chen2024). It is clearly seen that the robust candidates for extended gas reservoirs are mostly located in CO density peaks along the filaments (see Fig. [7](#fig: density map)). These results support the idea that the gas fuels are preferentially located in denser local environments and suspected to be the results of effective accretion of cold streams along filaments, then various mechanisms like gas truncation, galaxy mergers/interactions are attributed to the causes of the extended gas reservoirs and the growth of proto-ICM (cite: Chen2024).

As for the other group SW-GE2 with six ALMA sources (ID: 04, 19, 24, 37, 45, 47), none of them are identified as HAEs nor CO emitters. Only ASW2DF.04, the brightest one with a secure counterpart detected with the Karl G. Jansky Very Large Array (VLA) (cite: Dannerbauer2014), has recently been confirmed as a member galaxy at $z=2.15$ (Naufal et al., in prep.). We exclude the source ASW2DF.37 which overlaps with an AGN at $z=1.512$ (cite: Pentericci2002; Croft2005). Furthermore, only half of the six ALMA sources have a S/N higher than five, making the authenticity of this galaxy group less certain. This situation is similar to the one that has been reported in (cite: Chen2023b), in which the authors found that an assumed overdensity of dusty galaxies is actually composed by seven galaxies distributed at a wide redshift range rather than being a real association.

Nevertheless, the membership of the other four ALMA sources and their potential physical relation to the large scale structure should be investigated with further spectroscopic observations.

It is evident that DSFGs are grouped and host intense star formation activities on the outskirts of the Spiderweb protocluster up to $\sim3\times{\rm R}_{200}$. Contrarily, the protocluster center shows a relative lack of DSFGs and is believed to be nearly virialized (cite: Dannerbauer2014; Shimakawa2014; Jin2021). The member HAEs located in the protocluster center are at the high-mass end, likely in a post-starburst phase and with higher AGN fraction (cite: Shimakawa2018b; Shimakawa2024; Perez2023). This is consistent with the scenario proposed by (cite: Shimakawa2018b), in which the Spiderweb protocluster is experiencing a “maturing phase”. In this scenario, the red, passive galaxies have emerged in the protocluster center (cite: Kurk2004b; Kodama2007; Zirm2008; Doherty2010; Tanaka2010; Tanaka2013), while massive HAEs are maturing galaxies undergoing a rapid transition to quenched populations, with active AGN feedback responsible for suppressing the star formation activities in these HAEs (cite: Saro2009; Shimakawa2024; Perez2024). Some of them host post-starburst features and thus are suspected to be starbursts previously in their evolution (cite: Shimakawa2018b). For the ALMA-detected DSFGs located on the outskirts, they are still forming stars intensely because of efficient gas accretion and frequent interaction/merger events. Furthermore, these DSFGs may have assembled most of their masses before accreting into the potential well in the protocluster center (cite: Smail2014; Dannerbauer2014). A similar distribution has been reported by (cite: Shi2024), who found a strong anti-correlation between star formation activities and the density profile in a massive protocluster at the same epoch. This is consistent with the inside-out growth scenario proposed in simulations, that protoclusters at $z\sim1.5-5$ were experiencing rapid star formation over an extended scale of $10-20$ Mpc (cite: Chiang2017), and most of the galaxies are rapidly evolving inside the collapsing ﬁlaments instead of the protocluster core (cite: Remus2023).

![](plots/10_flux_ratio.png)

On the other hand, the Spiderweb protocluster is considered to be the result of the merger of two massive halos based on the double-peaked velocity distribution of the spectroscopically confirmed members (cite: Pentericci2000; Kuiper2011). Simulations have indicated that a significant fraction of the cluster mass was assembled through the accretion of galaxy groups (cite: McGee2009) and several merger events could occur in a protocluster during its virialization (cite: Kimmig2023). We might be witnessing a late phase of a major merger between two galaxy groups within the protocluster center, where the HAEs show an enhanced AGN fraction, and some of them are hosting post-starburst features (cite: Shimakawa2018b; Tozzi2022a). The anisotropic nature of the merged subhalos could be responsible for the asymmetric proto-ICM discovered recently (cite: Mascolo2023; Lepore2024). We thus speculate that the galaxy groups SW-GE1 and SW-GE2 will eventually fall into the potential well of the protocluster center and another merger will be triggered. Using the previously estimated SFRs and gas masses, we could have a rough idea of the depletion time of these ALMA sources, despite the inherent degeneracy between the two quantities based only on dust measurements. Without newly replenished gas inflows, the depletion time is estimated to be $340\pm48$ Myr, i.e., these ALMA-detected DSFGs will consume up their gas reservoirs and become passive at $z\sim1.9$.

## Comparison between ALMA and single-dish observations 

The preceding single-dish observations conducted on the Spiderweb protocluster provide an opportunity to match and compare the ALMA and LABOCA/AzTEC detections. All the seven LABOCA sources are detected by ALMA with at least one ALMA counterpart. Four of them are recovered with multiple (two or more) ALMA detections, indicating a multiplicity fraction of $\sim$57%. The multiplicity fraction is higher than that in general fields (cite: Stach2018; Simpson2020). All the brightest LABOCA sources DKB01, DKB02 and DKB03 show multiplicity, consistent with the trend that the bright single-dish sources are more likely to consist of multiple ALMA sources (cite: Hodge2013; Stach2018; Simpson2020). Furthermore, all five AzTEC sources within the ASW$^2$DF survey coverage are detected by ALMA, and four of them are recovered with more than one ALMA source. The 80% multiplicity of AzTEC sources is even higher than that in the protocluster SSA22 (cite: Umehata2018), under the same instrument beam size of FWHM=30 arcsec. The higher multiplicity of single-dish detections revealed by ALMA supports the overdensity nature of DSFG population in the Spiderweb protocluster.

We compare the flux measurements between ALMA and LABOCA/AzTEC sources to check how much of the single-dish flux are recovered by the ALMA observations. We sum up the fluxes of ALMA sources located within each LABOCA/AzTEC beam. The fluxes of the single-dish sources are scaled to 1.2 mm by using the same method described in Sec. [4.3](#sec: nc), with $S_{\rm 1.2\,mm}/S_{\rm 870\,\mu m}$ of 0.40 and $S_{\rm 1.2\,mm}/S_{\rm 1.1\,mm}$ of 0.77. Fig. [11](#fig: flux_ratio) shows the ratio of the summed ALMA flux compared to the single-dish flux. In most cases, the single-dish flux is not fully reproduced by the ALMA observations. The median ratios for the LABOCA sources and AzTEC sources are $0.62\pm0.12$ and $0.60\pm0.04$, which agree well with the results of (cite: Umehata2018) within uncertainties. Similarly, (cite: Hill2020) found that the integrated flux of the ALMA sources at 850 $\mu$m only account for $55\pm5$ percent of the integrated LABOCA flux at 870 $\mu$m in the core region of the protocluster SPT2349$-$56, meaning that there are still many galaxies under the detection limit due to the low SFR or spatial resolution.

There are several causes which could explain the missed flux by the ALMA sources. First of all, the flux of LABOCA sources adopted in (cite: Dannerbauer2014) is the observed flux, which could be boosted by the Eddington bias and confusion noise. Secondly, the fluxes of ALMA sources are recovered better with increasing beam sizes, and more flux may be lost with Briggs weighting compared to natural weighting (cite: Oteo2017). Our observations could recover most of the source fluxes in principle, but may still miss some fluxes due to the weighing scheme and the high resolution. Especially considering that there are a number of DSFGs showing clear extended features (i.e., cloud-like), whose emission cannot be fully covered by the aperture we used for flux measurement. This is also indicated by the big differences (\>50%) between the flux measurements from aperture and Gaussian fitting, such as sources with ASW2DF IDs of 08, 33, 35, 41 and 44 (see Figure [12](#fig: gallery_main) and [13](#fig: gallery_supp)). Furthermore, there could be fainter dusty galaxies undetected by ALMA that contribute to the single-dish flux, as described in (cite: Umehata2018). Finally, the observing frequency of the ALMA observations is not exactly the same as that of single-dish surveys (cite: Simpson2015; Simpson2020), the flux conversion factor could overestimate the single-dish flux and then lower the flux ratios. For example, (cite: Gomez2022) adopted a flux conversion factor of 0.44 for $S_{\rm 1.1\,mm}/S_{\rm 870\,\mu m}$ and 1.36 for $S_{\rm 1.1\,mm}/S_{\rm 1.2\,mm}$, which will decrease the single-dish flux by up to 30 percent.

# Summary

We present the first results of the ASW$^2$DF survey targeting the prominent Spiderweb protocluster at $z=2.16$. The observations were carried out in ALMA band 6. The data were reduced and cleaned into contiguous mosaic maps in six fields, with a total survey area of around 20 arcmin$^2$. We tested the “individual” and “fixed” methods on the rms noise estimation (see Sec. [3.1](#sec: noise)). The “fixed” method is more conservative and adopted to estimate the typical 1$\sigma$ noise in each field, being in a range of $40.3-57.1\,\mu$Jy. Below we summarize our main results in this paper:

1.  We used three publicly available codes (SEP, AEGEAN and SoFiA) to extract sources in the ALMA maps at S/N\>4. With the conservative “fixed” method, the three codes give consistent results and a sample of 47 detections was obtained as the main catalog, with a high purity of \>90 percent. Additionally, we performed a careful visual inspection on the mosaic maps to identify the ALMA sources independently. A supplementary catalog is provided to contain 21 sources identified by visual inspection or detected by any of the three codes with the “individual” method, which cannot be detected by the “fixed” method at \>4$\sigma$.

2.  Based on the main catalog, we constructed the differential and cumulative number counts down to 0.25 mJy at 1.2 mm. By comparing our results with those of general fields and public protoclusters, we find that the number counts of our ALMA sources are around two times that in general fields, and consistent with previous results with single-dish instruments. In addition, the number counts in Fields 1 to 3 are higher than the overall estimation, while Fields 4 to 6 show slightly lower number counts.

3.  The comparison between the spatial distributions of our ALMA sources with HAEs and CO emitters in the same field, reveals that the DSFGs detected by ALMA are preferentially located at the outskirts of the Spiderweb protocluster, and likely drawn from the same distribution as that of CO emitters. This is consistent with simulations that the galaxies and gas were falling into the cluster through filaments, where the starbursts are triggered by abundant gas accretion and frequent interactions/mergers due to the accretion shocks (cite: Zel’dovich1970; Rost2021). We find that 30 percent of ALMA sources located in the COALAS footprint are detected through CO(1-0) observations of our COALAS large program. The main reason for the non-detections could be the shallow (and not completely uniform) depth of the CO(1-0) observations. The SFR density of our ALMA sources is consistent with previous results (cite: Dannerbauer2014) after accounting the difference in volume. Using dust measurements in order to derive molecular gas masses should be considered with caution.

4.  Two extreme concentrations of ALMA sources around DKB01/DKB02 and DKB03 are located in the eastern part of the protocluster, with an excess of 12 times that of general fields, denoted as SW-GE1 and SW-GE2. This supports the scenario proposed by (cite: Shimakawa2018b) that the Spiderweb protocluster is in a maturing phase. Here, some massive HAEs, exhibiting post-starburst features, are located in the nearly virialized protocluster center. In contrast, the DSFGs on the outskirts are undergoing starbursts due to efficient gas accretion before their accretion into the protocluster center. These two newly identified groups are likely to eventually fall into the protocluster center and trigger another merger event.

5.  Comparing our ALMA maps with previous single-dish observations, we found that the multiplicity fraction is higher for the single-dish SMGs in the Spiderweb protocluster than that in general fields. This could also explain the overdense nature of DSFGs in the protocluster. The flux comparison indicates that the ALMA recovered around 60 percent of the single-dish fluxes. The potential reasons for the flux loss could be: flux boosting in single-dish observations, missing flux issue due to high resolution of ALMA, extended and/or faint DSFGs which are larger than the apertures used for flux measurement, and uncertainty of flux conversion between observed wavelengths.

# Acknowledgements

This paper makes use of the following ALMA data: ADS/JAO.ALMA#2021.1.00435.S ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc. The Australia Telescope Compact Array is part of the Australia Telescope National Facility (grid.421683.a) which is funded by the Australian Government for operation as a National Facility managed by CSIRO. We acknowledge the Gomeroi people as the traditional owners of the Observatory site. HD, YZ, JMPM and ZC acknowledges ﬁnancial supports from the Agencia Estatal de Investigación del Ministerio de Ciencia e Innovación (AEIMCINN) under grant (La evolución de los cúmulos de galaxias desde el amanecer hasta el mediodía cósmico) with reference (PID2019105776GB-I00/DOI:10.13039/501100011033). In addition, HD, YZ and JMPM acknowledge support from the Agencia Estatal de Investigación del Ministerio de Ciencia, Innovación y Universidades (MCIU/AEI) under grant (Construcción de cúmulos de galaxias en formación a través de la formación estelar oscurecida por el polvo) and the European Regional Development Fund (ERDF) with reference (PID2022-143243NB-I00/10.13039/501100011033). YZ acknowledges the support from the China Scholarship Council (202206340048), and the National Science Foundation of Jiangsu Province (BK20231106). JMPM acknowledges funding from the European Union’s Horizon research and innovation programme under the Marie Skłodowska-Curie grant agreement No 101106626. XZZ acknowledges the support from the National Science Foundation of China (12233005 and 12073078). CDE acknowledges funding from the MCIN/AEI (Spain) and the “NextGenerationEU”/PRTR (European Union) through the Juan de la Cierva-Formación program (FJC2021-047307-I). YK, RS, and TK acknowledge support from JSPS KAKENHI Grant Number JP23H01219.

189 natexlab

(ref: Adscheid2024) Adscheid, S., Magnelli, B., Liu, D., et al. 2024, A&A, 685, A1

(ref: Alberts2022) Alberts, S. & Noble, A. 2022, Universe, 8, 554

(ref: An2018) An, F. X., Stach, S. M., Smail, I., et al. 2018, ApJ, 862, 101

(ref: Aravena2020) Aravena, M., Boogaard, L., Gónzalez-López, J., et al. 2020, ApJ, 901, 79

(ref: Aravena2016) Aravena, M., Decarli, R., Walter, F., et al. 2016, ApJ, 833, 68

(ref: AB2018) Arrigoni Battaia, F., Chen, C.-C., Fumagalli, M., et al. 2018, A&A, 620, A202

(ref: Barbary2016) Barbary, K. 2016, The Journal of Open Source Software, 1, 58

(ref: Bassini2020) Bassini, L., Rasia, E., Borgani, S., et al. 2020, A&A, 642, A37

(ref: Bertin1996) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bing2023) Bing, L., Béthermin, M., Lagache, G., et al. 2023, A&A, 677, A66

(ref: Blain2004) Blain, A. W., Chapman, S. C., Smail, I., & Ivison, R. 2004, ApJ, 611, 725

(ref: Blain2002) Blain, A. W., Smail, I., Ivison, R. J., Kneib, J. P., & Frayer, D. T. 2002, Phys. Rep., 369, 111

(ref: Bond1996) Bond, J. R., Kofman, L., & Pogosyan, D. 1996, Nature, 380, 603

(ref: Bourne2017) Bourne, N., Dunlop, J. S., Merlin, E., et al. 2017, MNRAS, 467, 1360

(ref: Briggs1995) Briggs, D. S. 1995, PhD thesis, New Mexico Institute of Mining and Technology

(ref: Calvi2023) Calvi, R., Castignani, G., & Dannerbauer, H. 2023, A&A, 678, A15

(ref: Carniani2015) Carniani, S., Maiolino, R., De Zotti, G., et al. 2015, A&A, 584, A78

(ref: Carrera2011) Carrera, F. J., Page, M. J., Stevens, J. A., et al. 2011, MNRAS, 413, 2791

(ref: CASA2022) CASA Team, Bean, B., Bhatnagar, S., et al. 2022, PASP, 134, 114501

(ref: Casey2016) Casey, C. M. 2016, ApJ, 824, 36

(ref: Casey2013) Casey, C. M., Chen, C.-C., Cowie, L. L., et al. 2013, MNRAS, 436, 1919

(ref: Casey2015) Casey, C. M., Cooray, A., Capak, P., et al. 2015, ApJL, 808, L33

(ref: Casey2014) Casey, C. M., Narayanan, D., & Cooray, A. 2014, Phys. Rep., 541, 45

(ref: Champagne2021) Champagne, J. B., Casey, C. M., Zavala, J. A., et al. 2021, ApJ, 913, 110

(ref: Chen2013) Chen, C.-C., Cowie, L. L., Barger, A. J., et al. 2013, ApJ, 776, 131

(ref: Chen2016) Chen, C.-C., Smail, I., Ivison, R. J., et al. 2016, ApJ, 820, 82

(ref: Chen2023b) Chen, J., Ivison, R. J., Zwaan, M. A., et al. 2023a, A&A, 675, L10

(ref: Chen2023a) Chen, J., Ivison, R. J., Zwaan, M. A., et al. 2023b, MNRAS, 518, 1378

(ref: Chen2024) Chen, Z., Dannerbauer, H., Lehnert, M. D., et al. 2024, MNRAS, 527, 8950

(ref: Chiang2017) Chiang, Y.-K., Overzier, R. A., Gebhardt, K., & Henriques, B. 2017, ApJL, 844, L23

(ref: Coppin2006) Coppin, K., Chapin, E. L., Mortier, A. M. J., et al. 2006, MNRAS, 372, 1621

(ref: Cowie2017) Cowie, L. L., Barger, A. J., Hsu, L. Y., et al. 2017, ApJ, 837, 139

(ref: Croft2005) Croft, S., Kurk, J., van Breugel, W., et al. 2005, AJ, 130, 867

(ref: Cucciati2018) Cucciati, O., Lemaux, B. C., Zamorani, G., et al. 2018, A&A, 619, A49

(ref: da_Cunha2015) da Cunha, E., Walter, F., Smail, I. R., et al. 2015, ApJ, 806, 110

(ref: Daddi2021) Daddi, E., Valentino, F., Rich, R. M., et al. 2021, A&A, 649, A78

(ref: Daikuhara2024) Daikuhara, K., Kodama, T., Pérez-Martı́nez, J. M., et al. 2024, MNRAS, 531, 2335

(ref: Dannerbauer2021) Dannerbauer, H., Koyama, Y., Jin, S., et al. 2021, Mapping, resolving and penetrating into the dusty Spiderweb protocluster with unqiue Pa-beta imaging, JWST Proposal. Cycle 1, ID. #1572

(ref: Dannerbauer2014) Dannerbauer, H., Kurk, J. D., De Breuck, C., et al. 2014, A&A, 570, A55

(ref: Dannerbauer2017) Dannerbauer, H., Lehnert, M. D., Emonts, B., et al. 2017, A&A, 608, A48

(ref: DeBreuck2004) De Breuck, C., Bertoldi, F., Carilli, C., et al. 2004, A&A, 424, 1

(ref: Decarli2019) Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138

(ref: Dekel2009) Dekel, A., Birnboim, Y., Engel, G., et al. 2009, Nature, 457, 451

(ref: Mascolo2023) Di Mascolo, L., Saro, A., Mroczkowski, T., et al. 2023, Nature, 615, 809

(ref: Doherty2010) Doherty, M., Tanaka, M., De Breuck, C., et al. 2010, A&A, 509, A83

(ref: Draine2011) Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium

(ref: Dunlop2017) Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861

(ref: Eddington1913) Eddington, A. S. 1913, MNRAS, 73, 359

(ref: Emonts2018) Emonts, B. H. C., Lehnert, M. D., Dannerbauer, H., et al. 2018, MNRAS, 477, L60

(ref: Emonts2016) Emonts, B. H. C., Lehnert, M. D., Villar-Martı́n, M., et al. 2016, Science, 354, 1128

(ref: Fasano1987) Fasano, G. & Franceschini, A. 1987, MNRAS, 225, 155

(ref: Franco2018) Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152

(ref: Fujimoto2023) Fujimoto, S., Kohno, K., Ouchi, M., et al. 2023, arXiv e-prints, ApJS in press, arXiv:2303.01658

(ref: Fujimoto2016) Fujimoto, S., Ouchi, M., Ono, Y., et al. 2016, ApJS, 222, 1

(ref: Geach2017) Geach, J. E., Dunlop, J. S., Halpern, M., et al. 2017, MNRAS, 465, 1789

(ref: Gomez2022) Gómez-Guijarro, C., Elbaz, D., Xiao, M., et al. 2022, A&A, 658, A43

(ref: gomez2019) Gómez-Guijarro, C., Riechers, D. A., Pavesi, R., et al. 2019, ApJ, 872, 117

(ref: Gonzalez2017) González-López, J., Bauer, F. E., Romero-Cañizales, C., et al. 2017, A&A, 597, A41

(ref: Gonzalez2019) González-López, J., Decarli, R., Pavesi, R., et al. 2019, ApJ, 882, 139

(ref: Gonzalez2020) González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91

(ref: Greve2007) Greve, T. R., Stern, D., Ivison, R. J., et al. 2007, MNRAS, 382, 48

(ref: Gullberg2016) Gullberg, B., Lehnert, M. D., De Breuck, C., et al. 2016, A&A, 591, A73

(ref: Gullberg2019) Gullberg, B., Smail, I., Swinbank, A. M., et al. 2019, MNRAS, 490, 4956

(ref: Hamanowicz2023) Hamanowicz, A., Zwaan, M. A., Péroux, C., et al. 2023, MNRAS, 519, 34

(ref: Hancock2012) Hancock, P. J., Murphy, T., Gaensler, B. M., Hopkins, A., & Curran, J. R. 2012, MNRAS, 422, 1812

(ref: Hancock2018) Hancock, P. J., Trott, C. M., & Hurley-Walker, N. 2018, PASA, 35, e011

(ref: Hatch2009) Hatch, N. A., Overzier, R. A., Kurk, J. D., et al. 2009, MNRAS, 395, 114

(ref: Hatsukade2016) Hatsukade, B., Kohno, K., Umehata, H., et al. 2016, PASJ, 68, 36

(ref: Hatsukade2018) Hatsukade, B., Kohno, K., Yamaguchi, Y., et al. 2018, PASJ, 70, 105

(ref: Hatsukade2013) Hatsukade, B., Ohta, K., Seko, A., Yabe, K., & Akiyama, M. 2013, ApJL, 769, L27

(ref: Hickox2012) Hickox, R. C., Wardlow, J. L., Smail, I., et al. 2012, MNRAS, 421, 284

(ref: Hill2020) Hill, R., Chapman, S., Scott, D., et al. 2020, MNRAS, 495, 3124

(ref: Hodge2020) Hodge, J. A. & da Cunha, E. 2020, Royal Society Open Science, 7, 200556

(ref: Hodge2013) Hodge, J. A., Karim, A., Smail, I., et al. 2013, ApJ, 768, 91

(ref: Hogg1998) Hogg, D. W. & Turner, E. L. 1998, PASP, 110, 727

(ref: Holland2013) Holland, W. S., Bintley, D., Chapin, E. L., et al. 2013, MNRAS, 430, 2513

(ref: Holland1999) Holland, W. S., Robson, E. I., Gear, W. K., et al. 1999, MNRAS, 303, 659

(ref: Hopkins2006) Hopkins, A. M. & Beacom, J. F. 2006, ApJ, 651, 142

(ref: Hughes1998) Hughes, D. H., Serjeant, S., Dunlop, J., et al. 1998, Nature, 394, 241

(ref: Humphrey2011) Humphrey, A., Zeballos, M., Aretxaga, I., et al. 2011, MNRAS, 418, 74

(ref: Hunter2023) Hunter, T. R., Indebetouw, R., Brogan, C. L., et al. 2023, PASP, 135, 074501

(ref: Jin2021) Jin, S., Dannerbauer, H., Emonts, B., et al. 2021, A&A, 652, A11

(ref: Jones2017) Jones, S. F., Blain, A. W., Assef, R. J., et al. 2017, MNRAS, 469, 4565

(ref: Karim2013) Karim, A., Swinbank, A. M., Hodge, J. A., et al. 2013, MNRAS, 432, 2

(ref: Kimmig2023) Kimmig, L. C., Remus, R.-S., Dolag, K., & Biffi, V. 2023, ApJ, 949, 92

(ref: Klitsch2018) Klitsch, A., Péroux, C., Zwaan, M. A., et al. 2018, MNRAS, 475, 492

(ref: Klitsch2020) Klitsch, A., Zwaan, M. A., Smail, I., et al. 2020, MNRAS, 495, 2332

(ref: Kodama2007) Kodama, T., Tanaka, I., Kajisawa, M., et al. 2007, MNRAS, 377, 1717

(ref: Koprowski2017) Koprowski, M. P., Dunlop, J. S., Michałowski, M. J., et al. 2017, MNRAS, 471, 4155

(ref: Koyama2013) Koyama, Y., Kodama, T., Tadaki, K.-i., et al. 2013, MNRAS, 428, 1551

(ref: Kuiper2011) Kuiper, E., Hatch, N. A., Miley, G. K., et al. 2011, MNRAS, 415, 2245

(ref: Kurk2004b) Kurk, J. D., Pentericci, L., Overzier, R. A., Röttgering, H. J. A., & Miley, G. K. 2004a, A&A, 428, 817

(ref: Kurk2004a) Kurk, J. D., Pentericci, L., Röttgering, H. J. A., & Miley, G. K. 2004b, A&A, 428, 793

(ref: Kurk2000) Kurk, J. D., Röttgering, H. J. A., Pentericci, L., et al. 2000, A&A, 358, L1

(ref: Lacaille2019) Lacaille, K. M., Chapman, S. C., Smail, I., et al. 2019, MNRAS, 488, 1790

(ref: Lepore2024) Lepore, M., Di Mascolo, L., Tozzi, P., et al. 2024, A&A, 682, A186

(ref: Liu2023) Liu, S., Zheng, X. Z., Shi, D. D., et al. 2023, MNRAS, 523, 2422

(ref: Long2024) Long, A. S., Casey, C. M., McKinney, J., et al. 2024, arXiv e-prints, submitted to ApJ, arXiv:2408.14546

(ref: Long2020) Long, A. S., Cooray, A., Ma, J., et al. 2020, ApJ, 898, 133

(ref: Lutz2001) Lutz, D., Dunlop, J. S., Almaini, O., et al. 2001, A&A, 378, 70

(ref: Madau2014) Madau, P. & Dickinson, M. 2014, ARA&A, 52, 415

(ref: Magnelli2019) Magnelli, B., Karim, A., Staguhn, J., et al. 2019, ApJ, 877, 45

(ref: Martin2023) Martin, D. C., Darvish, B., Lin, Z., et al. 2023, Nature Astronomy, 7, 1390

(ref: Matsuda2005) Matsuda, Y., Yamada, T., Hayashino, T., et al. 2005, ApJL, 634, L125

(ref: McGee2009) McGee, S. L., Balogh, M. L., Bower, R. G., Font, A. S., & McCarthy, I. G. 2009, MNRAS, 400, 937

(ref: Miley2006) Miley, G. K., Overzier, R. A., Zirm, A. W., et al. 2006, ApJL, 650, L29

(ref: Miller2018) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469

(ref: Munoz2018) Muñoz Arancibia, A. M., González-López, J., Ibar, E., et al. 2018, A&A, 620, A125

(ref: Murdoch1973) Murdoch, H. S., Crawford, D. F., & Jauncey, D. L. 1973, ApJ, 183, 1

(ref: Naufal2023) Naufal, A., Koyama, Y., Shimakawa, R., & Kodama, T. 2023, ApJ, 958, 170

(ref: Oliver2010) Oliver, S. J., Wang, L., Smith, A. J., et al. 2010, A&A, 518, L21

(ref: Ono2014) Ono, Y., Ouchi, M., Kurono, Y., & Momose, R. 2014, ApJ, 795, 5

(ref: Oteo2018) Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, ApJ, 856, 72

(ref: Oteo2017) Oteo, I., Ivison, R. J., Negrello, M., et al. 2017, arXiv e-prints, Submitted to ApJ, arXiv:1709.04191

(ref: Oteo2016) Oteo, I., Zwaan, M. A., Ivison, R. J., Smail, I., & Biggs, A. D. 2016, ApJ, 822, 36

(ref: Overzier2016) Overzier, R. A. 2016, A&ARv, 24, 14

(ref: Peacock1983) Peacock, J. A. 1983, MNRAS, 202, 615

(ref: Pensabene2024) Pensabene, A., Cantalupo, S., Cicone, C., et al. 2024, A&A, 684, A119

(ref: Pentericci2002) Pentericci, L., Kurk, J. D., Carilli, C. L., et al. 2002, A&A, 396, 109

(ref: Pentericci2000) Pentericci, L., Kurk, J. D., Röttgering, H. J. A., et al. 2000, A&A, 361, L25

(ref: Pentericci1997) Pentericci, L., Roettgering, H. J. A., Miley, G. K., Carilli, C. L., & McCarthy, P. 1997, A&A, 326, 580

(ref: Perez2024) Pérez-Martı́nez, J. M., Dannerbauer, H., & Emonts, B. H. C. 2024, A&A, Submitted

(ref: Perez2023) Pérez-Martı́nez, J. M., Dannerbauer, H., Kodama, T., et al. 2023, MNRAS, 518, 1707

(ref: Priddey2008) Priddey, R. S., Ivison, R. J., & Isaak, K. G. 2008, MNRAS, 383, 289

(ref: Remus2023) Remus, R.-S., Dolag, K., & Dannerbauer, H. 2023, ApJ, 950, 191

(ref: Rigby2014) Rigby, E. E., Hatch, N. A., Röttgering, H. J. A., et al. 2014, MNRAS, 437, 1882

(ref: Roettgering1994) Roettgering, H. J. A., Lacy, M., Miley, G. K., Chambers, K. C., & Saunders, R. 1994, A&AS, 108, 79

(ref: Rost2021) Rost, A., Kuchner, U., Welker, C., et al. 2021, MNRAS, 502, 714

(ref: Rost2024) Rost, A. M., Nuza, S. E., Stasyszyn, F., et al. 2024, MNRAS, 527, 1301

(ref: Saro2009) Saro, A., Borgani, S., Tornatore, L., et al. 2009, MNRAS, 392, 795

(ref: Scott2012) Scott, K. S., Wilson, G. W., Aretxaga, I., et al. 2012, MNRAS, 423, 575

(ref: Scoville2014) Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84

(ref: Scoville2023) Scoville, N., Faisst, A., Weaver, J., et al. 2023, ApJ, 943, 82

(ref: Scoville2016) Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83

(ref: Serra2015) Serra, P., Westmeier, T., Giese, N., et al. 2015, MNRAS, 448, 1922

(ref: Shi2021) Shi, D. D., Cai, Z., Fan, X., et al. 2021, ApJ, 915, 32

(ref: Shi2024) Shi, D. D., Wang, X., Zheng, X. Z., et al. 2024, ApJ, 963, 21

(ref: Shim2020) Shim, H., Kim, Y., Lee, D., et al. 2020, MNRAS, 498, 5065

(ref: Shimakawa2018a) Shimakawa, R., Kodama, T., Hayashi, M., et al. 2018a, MNRAS, 473, 1977

(ref: Shimakawa2014) Shimakawa, R., Kodama, T., Tadaki, K. I., et al. 2014, MNRAS, 441, L1

(ref: Shimakawa2018b) Shimakawa, R., Koyama, Y., Röttgering, H. J. A., et al. 2018b, MNRAS, 481, 5630

(ref: Shimakawa2024) Shimakawa, R., Pérez-Martı́nez, J. M., Koyama, Y., et al. 2024, MNRAS, 528, 3679

(ref: Simpson2020) Simpson, J. M., Smail, I., Dudzevičiūtė, U., et al. 2020, MNRAS, 495, 3409

(ref: Simpson2015) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2015, ApJ, 799, 81

(ref: Simpson2019) Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2019, ApJ, 880, 43

(ref: Simpson2014) Simpson, J. M., Swinbank, A. M., Smail, I., et al. 2014, ApJ, 788, 125

(ref: Siringo2009) Siringo, G., Kreysa, E., Kovács, A., et al. 2009, A&A, 497, 945

(ref: Smail2014) Smail, I., Geach, J. E., Swinbank, A. M., et al. 2014, ApJ, 782, 19

(ref: Smail1997) Smail, I., Ivison, R. J., & Blain, A. W. 1997, ApJL, 490, L5

(ref: Smail2002) Smail, I., Ivison, R. J., Blain, A. W., & Kneib, J. P. 2002, MNRAS, 331, 495

(ref: Spergel2007) Spergel, D. N., Bean, R., Doré, O., et al. 2007, ApJS, 170, 377

(ref: Spergel2003) Spergel, D. N., Verde, L., Peiris, H. V., et al. 2003, ApJS, 148, 175

(ref: Stach2019) Stach, S. M., Dudzevičiūtė, U., Smail, I., et al. 2019, MNRAS, 487, 4648

(ref: Stach2018) Stach, S. M., Smail, I., Swinbank, A. M., et al. 2018, ApJ, 860, 161

(ref: Stach2017) Stach, S. M., Swinbank, A. M., Smail, I., et al. 2017, ApJ, 849, 154

(ref: Stevens2003) Stevens, J. A., Ivison, R. J., Dunlop, J. S., et al. 2003, Nature, 425, 264

(ref: Stevens2010) Stevens, J. A., Jarvis, M. J., Coppin, K. E. K., et al. 2010, MNRAS, 405, 2623

(ref: Sun2024) Sun, F., Helton, J. M., Egami, E., et al. 2024, ApJ, 961, 69

(ref: Swinbank2006) Swinbank, A. M., Chapman, S. C., Smail, I., et al. 2006, MNRAS, 371, 465

(ref: Tamura2009) Tamura, Y., Kohno, K., Nakanishi, K., et al. 2009, Nature, 459, 61

(ref: Tanaka2010) Tanaka, M., De Breuck, C., Venemans, B., & Kurk, J. 2010, A&A, 518, A18

(ref: Tanaka2013) Tanaka, M., Toft, S., Marchesini, D., et al. 2013, ApJ, 772, 113

(ref: Tozzi2022b) Tozzi, P., Gilli, R., Liu, A., et al. 2022a, A&A, 667, A134

(ref: Tozzi2022a) Tozzi, P., Pentericci, L., Gilli, R., et al. 2022b, A&A, 662, A54

(ref: Ueda2018) Ueda, Y., Hatsukade, B., Kohno, K., et al. 2018, ApJ, 853, 24

(ref: Umehata2019) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97

(ref: Umehata2018) Umehata, H., Hatsukade, B., Smail, I., et al. 2018, PASJ, 70, 65

(ref: Umehata2015) Umehata, H., Tamura, Y., Kohno, K., et al. 2015, ApJL, 815, L8

(ref: Umehata2017) Umehata, H., Tamura, Y., Kohno, K., et al. 2017, ApJ, 835, 98

(ref: Wang2024) Wang, G. C. P., Chapman, S. C., Sulzenauer, N., et al. 2024, arXiv e-prints, arXiv:2406.16637

(ref: Wang2021) Wang, G. C. P., Hill, R., Chapman, S. C., et al. 2021, MNRAS, 508, 3754

(ref: Weiss2009) Weiß, A., Kovács, A., Coppin, K., et al. 2009, ApJ, 707, 1201

(ref: Westmeier2021) Westmeier, T., Kitaeff, S., Pallot, D., et al. 2021, MNRAS, 506, 3962

(ref: Wethers2020) Wethers, C. F., Banerji, M., Hewett, P. C., & Jones, G. C. 2020, MNRAS, 492, 5280

(ref: Wilkinson2017) Wilkinson, A., Almaini, O., Chen, C.-C., et al. 2017, MNRAS, 464, 1380

(ref: Wilson2008) Wilson, G. W., Austermann, J. E., Perera, T. A., et al. 2008, MNRAS, 386, 807

(ref: Wootten2009) Wootten, A. & Thompson, A. R. 2009, IEEE Proceedings, 97, 1463

(ref: Zavala2018) Zavala, J. A., Casey, C. M., da Cunha, E., et al. 2018, ApJ, 869, 71

(ref: Zavala2021) Zavala, J. A., Casey, C. M., Manning, S. M., et al. 2021, ApJ, 909, 165

(ref: Zeballos2018) Zeballos, M., Aretxaga, I., Hughes, D. H., et al. 2018, MNRAS, 479, 4577

(ref: Zel’dovich1970) Zel’dovich, Y. B. 1970, A&A, 5, 84

(ref: Zeng2024) Zeng, X., Ao, Y., & Zhang, Y. 2024, MNRAS, 528, 2964

(ref: Zhang2022) Zhang, Y., Zheng, X. Z., Shi, D. D., et al. 2022, MNRAS, 512, 4893

(ref: Zheng2009) Zheng, X. Z., Bell, E. F., Somerville, R. S., et al. 2009, ApJ, 707, 1566

(ref: Zheng2021) Zheng, X. Z., Cai, Z., An, F. X., Fan, X., & Shi, D. D. 2021, MNRAS, 500, 4354

(ref: Zhoudz2024) Zhou, D., Greve, T. R., Gullberg, B., et al. 2024a, arXiv e-prints, accepted to A&A, arXiv:2408.02177

(ref: Zhou2020) Zhou, L., Elbaz, D., Franco, M., et al. 2020, A&A, 642, A155

(ref: Zhou2024) Zhou, L., Wang, T., Daddi, E., et al. 2024b, A&A, 684, A196

(ref: Zirm2008) Zirm, A. W., Stanford, S. A., Postman, M., et al. 2008, ApJ, 680, 224

# Additional material

![](plots/a0_gallery_main.png)

![](plots/a0_gallery_supp.png)

|  |  |  |  |  |  |  |  |  |  |  |  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Field | EB | Date | Ant. | Baseline | Resolution | $\tau_{\rm target}$ | PWV | EF | Synthesized beam | PA | $\sigma$ |
|  |  |  |  | \(m\) | (arcsec) | (min) | \(mm\) |  |  | (deg) | ($\mu$Jy) |
|  | 1 | 31 Dec 2021 | 42 | 14.9$-$976.6 | 0.4$-$5.0 | 40.57 | 1.49 | 1.10 |  |  |  |
| 1 | 2 | 02 Jan 2022 | 43 | 14.9$-$976.6 | 0.4$-$5.2 | 40.55 | 0.96 | 1.50 | 0.51$''$ $\times$ 0.33$''$ | $-$78.6 | 46.2 |
|  | 3 | 02 Jan 2022 | 44 | 14.9$-$976.6 | 0.4$-$5.1 | 40.57 | 0.79 | 1.50 |  |  |  |
|  | 1 | 03 Jan 2022 | 42 | 14.9$-$783.1 | 0.4$-$5.3 | 40.53 | 1.33 | 1.31 |  |  |  |
| 2 | 2 | 03 Jan 2022 | 44 | 14.9$-$976.6 | 0.4$-$5.3 | 40.57 | 1.11 | 1.49 | 0.48$''$ $\times$ 0.34$''$ | $-$83.9 | 45.9 |
|  | 3 | 06 Jan 2022 | 45 | 14.9$-$976.6 | 0.4$-$5.1 | 40.57 | 0.71 | 1.50 |  |  |  |
|  | 1 | 03 Jan 2022 | 42 | 14.9$-$783.1 | 0.4$-$5.3 | 40.55 | 1.27 | 1.37 |  |  |  |
| 3 | 2 | 07 Jan 2022 | 46 | 14.9$-$976.6 | 0.4$-$5.5 | 40.57 | 2.29 | 0.99 | 0.48$''$ $\times$ 0.34$''$ | $-$83.2 | 57.1 |
|  | 3 | 07 Jan 2022 | 45 | 14.9$-$976.6 | 0.4$-$5.4 | 40.58 | 1.79 | 1.27 |  |  |  |
|  | 1 | 07 Jan 2022 | 45 | 14.9$-$976.6 | 0.4$-$5.4 | 40.58 | 1.55 | 1.29 |  |  |  |
| 4 | 2 | 08 Jan 2022 | 44 | 14.9$-$976.6 | 0.4$-$5.4 | 40.57 | 2.39 | 0.76 | 0.83$''$ $\times$ 0.53$''$ | $-$77.4 | 40.3 |
|  | 3 | 13 Apr 2022 | 45 | 15.0$-$500.2 | 0.8$-$8.5 | 40.57 | 0.38 | 1.50 |  |  |  |
|  | 4 | 13 Apr 2022 | 46 | 15.0$-$500.2 | 0.8$-$8.5 | 40.55 | 0.43 | 1.50 |  |  |  |
|  | 1 | 14 Apr 2022 | 44 | 15.0$-$500.2 | 0.7$-$8.2 | 40.55 | 0.43 | 1.50 |  |  |  |
| 5 | 2 | 15 Apr 2022 | 44 | 15.0$-$500.2 | 0.7$-$7.5 | 40.55 | 0.88 | 1.50 | 0.85$''$ $\times$ 0.63$''$ | 88.3 | 48.2 |
|  | 3 | 17 Apr 2022 | 46 | 15.0$-$500.2 | 0.7$-$7.2 | 40.57 | 0.50 | 1.50 |  |  |  |
|  | 1 | 14 Apr 2022 | 44 | 15.0$-$500.2 | 0.7$-$8.2 | 40.55 | 0.57 | 1.50 |  |  |  |
| 6 | 2 | 14 Apr 2022 | 44 | 15.0$-$500.2 | 0.7$-$8.2 | 40.57 | 0.34 | 1.50 | 0.94$''$ $\times$ 0.64$''$ | $-$84.7 | 44.7 |
|  | 3 | 15 Apr 2022 | 42 | 15.0$-$500.2 | 0.7$-$7.7 | 40.55 | 0.52 | 1.50 |  |  |  |

</paper>

Write the methods card for this paper.