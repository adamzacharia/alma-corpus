# Task for a Claude Code subagent

Below are the full instructions (system rules + JSON Schema) and one paper. Follow them exactly and write the methods card as ONE JSON object, nothing else, to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...696A..95G\sonnetcc\reply.txt

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
 "bibcode": "2025A&A...696A..95G",
 "title": "Connecting the growth of galaxies to the large-scale environment in a massive node of the Cosmic Web at z ∼ 3",
 "year": 2025,
 "journal": "Astronomy and Astrophysics",
 "first_author": "Galbiati, M.",
 "n_authors": 13,
 "arxiv_id": "2410.03822",
 "doi": "10.1051/0004-6361/202452493",
 "alma_projects_linked_by_archive": [
  "2021.1.00793.S"
 ]
}
```

Paper text:
<paper>
# Connecting the growth of galaxies to the large-scale environment in a massive node of the Cosmic Web at z$\sim$3

# Introduction

According to the current cosmological model, the majority of the inter-galactic gas is distributed in a network of filaments and sheets, called the Cosmic Web, formed through gravitational collapse of the initial density fluctuations (cite: Bond1996). Structures form in the densest part of the Cosmic Web and grow hierarchically, merging into the massive virialized groups and clusters we observe in today’s universe at the intersection of filaments (cite: deLapparent1986; Geller1989; Alpaslan2014; Libeskind2018). This large-scale environment is thought to play a key role in regulating how the embedded galaxies form and evolve across the cosmic time. Indeed, galaxies found in virialized clusters at $z\lesssim1$ are more massive and form stars at a lower rate compared to the galaxies living in the field (cite: Baldry2006; Bamford2009; Peng2010; Calvi2013; Tomczak2017; Lemaux2019; Tomczak2019; Old2020; Chartab2020; vdBurg2020; McNab2021). It is thus implied that the galaxies inhabiting extremely overdense regions assemble their mass rapidly and undergo intense episodes of star formation (cite: Thomas2005; Raichoor2011; Gu2018_int). Therefore, the $z\gtrsim2$ progenitors of present-day clusters, often referred to as protoclusters (cite: Sunyaev1972; Cen2000; Overzier2016; Alberts2022), are an ideal laboratory within which we can study the fundamental link between galaxies and their large-scale environment.

Overdensities of Ly$\alpha$ and H$\alpha$ emitters, Lyman Break Galaxies (LBGs) or dusty star-forming galaxies are commonly used as a tracer for candidate clusters’ progenitors (cite: Steidel1998; Steidel2000; Kurk2000; Kurk2004; Hayashino2004; Chapman2009; Tanaka2011; Lee2014; Casey2015; Oteo2018; Shi2019a; Shi2019b), although their spatial distribution does not necessarily follow fully virialized structures (cite: Lovell2018; Toshikawa2020), unlike $z\approx0$ clusters. Indeed, at $z\gtrsim2$, (cite: Chiang2013) predicted protoclusters to extend over $\approx10-20\rm\,cMpc$, while some well studied structures show multiple peaks in their galaxies’ overdensity and extend on even much larger scales (cite: Steidel1998; Pentericci2000; Cucciati2018). In similar $z\gtrsim2$ overdense environments, galaxies are found to be sites of higher star formation activity and their stellar mass function shows an excess at the high-mass-end compared to the field (cite: Kodama2007; Koyama2013a; Koyama2013b; Shimakawa2017; Shimakawa2018; Greenslade2018; Miller2018; Ito2020; Lemaux2022; Taamoli2023; Toshikawa2024) as well as enhanced active galactic nuclei (AGN) activity (cite: Lehmer2009; Tozzi2022; Gatica2024). A high rate of mergers (cite: Alonso2012; Mei2023), efficient gas accretion (cite: dAmato2020) and interactions with a *proto-*intracluster medium (cite: DiMascolo2023) are expected to play a key role in regulating galaxies growth and activity in these high-redshift overdensities. Though star forming galaxies are observed to be the dominant population in clusters’ progenitors (cite: Kuiper2010; Spitler2012; Contini2016), the detections of quiescent galaxies has been reported in some structures (cite: Kodama2007; Kubo2013; Shi2019b). These observations suggest that protoclusters could be ideal environments to study the onset of environmental quenching and the processes driving the suppression of the star formation activity observed in $z\approx0$ clusters’ galaxies. Theoretical works (cite: Muldrew2015; Chiang2017; Lovell2018) are consistent with these observational results, and both support a picture in which galaxies in protoclusters have assembled their masses and rapidly grown at earlier times than those in the field.

Complementary to blind searches, overdense structures of the Inter-Galactic Medium (IGM) itself (cite: Lee2018; Newman2020; Newman2022), as well as the surroundings of highly biased objects, such as High-Redshift Radio Galaxies (HzRGs; (cite: Roettgering1994; Pentericci2000; Hayashi2012; Hatch2014; Rigby2014; Orsi2016; PerezMartinez2023)), Hot Dust-Obscured Galaxies (cite: Jones2014; Assef2015; Penney2019; Luo2022; Ginolfi2022; Zewdie2023) and luminous quasars (QSOs; (cite: Kashikawa2007; Venemans2007; Overzier2008; Priddey2008; Kim2009; Utsumi2010; Banados2013; Husband2013; Adams2015; Mignoli2020; Kashino2023)) have been typically explored as signposts of galaxy overdensities. In particular, high-redshift quasars are among the brightest objects in the $z\gtrsim2$ universe and are thus expected to trace overdense structures. Indeed, a hyperluminous quasar at $z\approx2.84$ was found at the center of a large overdensity of LBGs (cite: Steidel2011), Ly$\alpha$ emitters (cite: Kikuta2019) and sub-millimeter galaxies (cite: Lacaille2019; Wang2024), tracing a large-scale structure extending across $\approx100\rm\,cMpc$. (cite: GarciaVergara2021) explored the galaxy clustering around $z\approx4$ quasars and found a large overdensity of different galaxy populations, that is CO(4–3) line emitters and Ly$\alpha$ emitting galaxies. On the other hand, (cite: Falder2011; Trainor2012; Adams2015; Hennawi2015) reported the detection of galaxy overdensities in the environment of luminous quasars in only $\approx10\%$ of the cases.

Despite the increasing number of $z\gtrsim2$ galaxy overdensities and candidate protoclusters discovered in the literature, the heterogeneity of the tracers and the methods adopted to identify the galaxies in their surroundings makes it challenging to draw a unified picture and to consistently trace the assembly and the evolution of the overdense structures down to present-day clusters. Comparing the galaxy environment around radio-loud AGNs from the Clusters Around Radio-Loud AGNs (CARLA; (cite: Wylezalek2013)) program and radio-quiet quasars with similar masses and redshifts, (cite: Hatch2014) found that the choice of the biased tracer itself has an effect on the large-scale galaxy environment identified in its surroundings. Indeed, on average, radio-loud AGN are observed to be surrounded by larger overdensities and to trace larger structures than radio-quiet quasars. Additionally, differences among overdensities of galaxies selected with a similar criterion around the same biased tracer may arise as a consequence of these structure being in a different evolutionary stage, as shown by, e.g., (cite: Shimakawa2018).

We present in this work a multiwavelength survey of the large-scale galaxy environment around the $z\approx3.25$ quasar CTS G18.01, which has been pre-selected for being surrounded by extended and filamentary-shaped Ly$\alpha$ emission from the cosmic gas (named MQN01), as discovered by (cite: Borisova2016) and as confirmed later by deeper observations covering a wider area (Cantalupo et al., in prep.). In particular, we targeted the field with a mosaic of observations taken with the Multi Unit Spectroscopic Explorer (cite: Bacon2010) at the Very Large Telescope (VLT), the FOcal Reducer and low dispersion Spectrograph 2 (cite: Appenzeller1998) and the High Acuity Wide field K-band Imager (cite: Pirard2004; Casali2006; Kissler-Patig2008; Siebenmorgen2011) at the VLT. The combination of these datasets aims at selecting star forming galaxies at the redshift of the quasar across $24\times24\rm\,cMpc^2$ and provides spectroscopic confirmation within an area of $4\times4\rm\,cMpc^2$ that is covered by MUSE. Additional HST/ACS, JWST/NIRCam and *Chandra* observation are used to derive star formation rates and stellar masses by modeling the galaxies’ spectral energy distribution (SED) and to explore this peculiar environment in the context of galaxies’ formation and evolution. The goal of this work is thus to exploit this rich multiwavelength dataset to explore an overdense region at $z\approx3$ (cite: Pensabene2024) and unveil the roles of both the local and large-scale environment on the stellar mass assembly and star formation activity of the galaxies populating this unique field.

We describe the data in Section [2](#sec:data) and present in Section [3](#sec:selection) the samples of galaxies identified around the target quasar. In Sections [4.1](#sec:result_zDist)-[4.3](#sec:radial_overdensity) we investigate the overdensity of star-forming galaxies within $4\times4\rm\,cMpc^2$ around the quasar and explore their properties, compared to galaxies in the field, in Sections [4.4](#sec:result_MainSeq)-[4.6](#sec:over_profiles). We then explore the overdensity of LBGs across $24\times24\rm\,cMpc^2$ in Section [4.7](#sec:result_Voronoi). Finally, we discuss this structure in the context of galaxies formation and evolution in Section [5](#sec:discussion). Throughout, unless otherwise noted, we quote magnitudes in the AB system, distances in physical units, and adopt the Planck 2015 cosmology ($\Omega_{\mathrm{m}} = 0.307$, $H_0 = 67.7$ km s$^{-1}$ Mpc$^{-1}$; (cite: Planck2016)).

# Observations and data reduction

## MUSE observations

The main dataset consists of a mosaic of four VLT/MUSE pointings around the quasar CTS G18.01. The observations are part of a MUSE Guaranteed Time of Observations (GTO) programme ID 0102.A-0448(A), PI S. Cantalupo. They were all conducted in October 2018 in visitor mode with an integration time of, on average[^2], $\approx10$ hours per pointing using MUSE with AO in Wide-Field mode. The data were taken on clear nights, at airmass $\leq$2.8, angular distance from the moon $\geq30\rm\,deg$, lunar illumination $\leq20\%$ and requiring an image quality better than $\rm FWHM\leq0.8\,arcsec$. The different frames of each pointing were observed with relative inclination of 90 degrees and small dithers ($\lesssim1\rm\,arcsec$) to mitigate the differences in the performance of the 24 IFUs (cite: Borisova2016; Marino2018). Each of the pointing covers $1\times1\rm\,arcmin^2$, resulting in a final mosaic with a Field-of-View (FoV) of $\approx2\times2\rm\,arcmin^2$ which corresponds to $4\times4\rm\,cMpc^2$ at the redshift of the central quasar, $z\approx3.25$.

The raw data were initially reduced with the ESO Muse pipeline (cite: Weilbacher2014). The scibasic routine of the ESO Muse pipeline was used to subtract bias, apply flat fielding, perform twilight and illumination corrections, calibrate the wavelengths and the line spread function using arcs and reduce the sky flats. The same calibrations are applied to the field targeting the standard star that is then used to calibrate the flux. The known astrometric offsets (cite: Bacon2015) are corrected by registering the datacubes using the point sources identified in each collapsed individual frame. Once aligned, all the individual frames are combined in a final datacube by using a 3D drizzling interpolation process. The final stacked datacube produced by the ESO pipeline are known (cite: Borisova2016; Bacon2017; Marino2018; Cantalupo2019) to be affected by imperfections in the flat-fielding process and instabilities of the detector. To correct for these effects and improve the quality of the datacubes, we post-process the final products using the CubExtractor (CubEx hereafter, (cite: DeBeer2023) and Cantalupo et al., in prep.) package, version 1.8, and its subroutines (see figure 1 in (cite: Lofthouse2020) for an example of the post-processing results compared to the science products reduced by the ESO pipeline). In details, CubeFix applies the flat-fielding correction by using the observed sky to self-calibrate the exposures. This process is applied iteratively after masking the continuum-detected sources to avoid contamination. The result is an optimal re-alignment of the relative illumination between the stacks and slices of each IFU, which are not completely corrected by the daily flats. CubeSharp performs flux-conserving sky subtraction by including empirical corrections of the line spread function. By means of the CubeCombine tool, we then combined the individual exposures into a single datacube. Such cube is then employed to mask continuum sources detected in the collapsed white-light image to optimize a second iteration of CubeFix and CubeSharp. Finally, CubeCombine is used to produce the final and fully-reduced datacube.

## FORS2 and HAWK-I mosaics

![](Completeness.pdf)

We followed-up the MUSE observations with a joint VLT/FORS2 and VLT/HAWK-I programme (ID 110.23ZX, PI S.Cantalupo). The FORS2 mosaic is designed to cover an area of $\approx24\times24\rm\,cMpc^2$, which corresponds to a FoV that is $\approx6\times6$ larger than the one of MUSE and to overlap in the same area covered by MUSE. The observations were executed during ESO Cycle 110-111 in both visitor and service mode, as detailed below and consists of imaging in three different filters: U$_{\rm High}$ (7h on source, $\lambda_{\rm eff}=361\,$nm), B$_{\rm High}$ (5h on source, $\lambda_{\rm eff}=437\,$nm) and R$_{\rm Special}$ (45 minutes on source, $\lambda_{\rm eff}=655\,$nm). The U-band data were taken in visitor mode during two half-nights in October 2022 (Run ID 110.23ZX.001) with the blue-sensitive E2V FORS2 CCD. The B-band and R-band observations were taken in service mode with the MIT CCD. The imaging observations in all the three filters were executed with the default CCD read-out mode for imaging, 2$\times2$ binning and low gain. Our observational constraints include clear nights, airmass $\leq1.5$, $\leq20\%$ of lunar illumination and a seeing better than $\rm 0.8\rm\,arcsec$ FWHM. We observed each mosaic position twice and applied small dithers between the individual frames in each invidual OB to improve contamination removal, background subtraction and to cover the gap between the two chips. To reduce the data, we used the ESO pipeline recipes for FORS2 (cite: Izzo2010) to apply standard bias, flat and flux calibrations [^3]. The 2D background was locally modelled and subtracted using the python package photutils (cite: Bradley2023). Finally, we aligned the astrometry of each individual frame with stars from Gaia DR3 catalog (cite: Gaia2016; Gaia2023) by using the scamp package (cite: Bertin2006). The reduced and registered frames are sigma-clipped and combined into the large-scale mosaic using swarp (cite: Bertin2010).

To characterize the depth of the final mosaics, we measured the $3\sigma$ limiting magnitude of each image (see Table [4](#tab:fors)) within apertures of radius $r=4\rm\,pixels\approx1\rm\,arcsec$, corresponding to twice the maximum value of the PSF, and placed in 5000 random positions in blank regions, with all the sources masked to avoid contamination. To estimate the image quality of the science products we used the software PSFEx (cite: Bertin2011) which extracts a sample of unsaturated stars to measure the Point Spread Function (PSF) across the entire FoV accounting for spatial variations. We report the mean value across the FoV in Table [4](#tab:fors), which will also be used to perform accurate photometry later in the analysis: the variation between the minimum and maximum PSF across the FoV is $\lesssim10\%$ for all the images.

As a final step, we performed injection/recovery experiments to estimate the completeness of the science mosaics. We first created background-only versions of the images by replacing each pixel belonging to known sources, as identified by SExtractor ((cite: Bertin1996), version 2.24.2) using the same parameters listed in Section [3.1](#sec:sel_UBR), with a value randomly extracted from a normal distribution centered on the median value of the background. To create the artificial sources, we convolved point sources with the PSF and randomly injected 1500 mocks for each $\Delta m=0.025\rm\,mag$ bin of magnitude, from $m=24\rm\,mag$ to $m=31\rm\,mag$, in the background-only mosaics. The number of mocks is carefully chosen to avoid overlap and deblending issues. We then run SExtractor and measured the fraction of sources we can recover as a function of the magnitude. We compute the results (see Figure [1](#fig:data_FORS) and Table [4](#tab:fors)) for the full mosaic, distinguishing three different regions (the deepest one is designed to overlap with the MUSE FoV at the center of the mosaic) depending on the number of exposures.

+--------+--------------------------------------------------------+--------------------------------------------------------+--------------------------------------------------------+---+
| Filter | |                          |                           | |                        |                             | |               |                                      |   |
|        | |:------------------------:|                           | |:----------------------:|                             | |:-------------:|                                      |   |
|        | | $m_{\rm3\sigma}^{\rm a}$ |                           | | $m_{\rm 50\%}^{\rm b}$ |                             | | PSF$^{\rm c}$ |                                      |   |
|        | |       $(\rm mag)$        |                           | |      $(\rm mag)$       |                             | |   (arcsec)    |                                      |   |
|        |                                                        |                                                        |                                                        |   |
|        | : Depth and PSF of the VLT/FORS2 imaging observations. | : Depth and PSF of the VLT/FORS2 imaging observations. | : Depth and PSF of the VLT/FORS2 imaging observations. |   |
+:======:+:======================================================:+:======================================================:+:======================================================:+:=:+
| U      | 27.90                                                  | 28.25 28.23 28.20                                      | 0.78                                                   |   |
+--------+--------------------------------------------------------+--------------------------------------------------------+--------------------------------------------------------+---+
| B      | 27.45                                                  | 28.40 28.38 28.33                                      | 0.65                                                   |   |
+--------+--------------------------------------------------------+--------------------------------------------------------+--------------------------------------------------------+---+
| R      | 26.08                                                  | 26.99 26.96 26.91                                      | 0.60                                                   |   |
+--------+--------------------------------------------------------+--------------------------------------------------------+--------------------------------------------------------+---+

: Depth and PSF of the VLT/FORS2 imaging observations.

Table notes:

The survey strategy described above for the FORS2 observations was employed to image the same area of $\approx24\times24\rm\,cMpc^2$ around the target quasar with VLT/HAWK-I. We observed the field with a set of three filters: CH4 (1h on source, $\lambda_{\rm eff}=1.575\rm\,\mu m$), H (2h on source, $\lambda_{\rm eff}=1.620\rm\,\mu m$) and K$_{\rm s}$ (2h on source, $\lambda_{\rm eff}=2.146\rm\,\mu m$). The observations were executed in October-December 2022 requiring the same constraints listed for FORS2. The raw data were bias subtracted, flat fielded and flux calibrated by using the ESO Pipeline recipes for HAWK-I imaging (version 2.4.13) implemented in EsoRex ((cite: EsoRex2015), version 3.13.6). The 2MASS (cite: Skrutskie2006) catalogue is used to measure the flux zero-point. After subtracting the background, we used the hawki$\_$science$\_$postprocess recipe in the ESO Pipeline to combine the exposures into the final science mosaic. As a final step, we registered the astrometry of the final mosaic to Gaia by using the DrizzlePac package[^4] (cite: Gonzaga2012; Hoffmann2021).

## Multiwavelength photometry and ancillary data

![](Footprint.pdf)

This field has also been targeted by a multiwavelength campaign spanning from the X-Ray to the millimeter wavelengths (see the left panel in Figure [2](#fig:Summary_FoV)), which enables us to perform a complete census of the different population of sources in the environment of the central quasar, including AGN and dusty star-forming galaxies, that may be elusive in optical observations. Travascio et al., (submitted) collected 600ks of broadband (0.5$\-$7.0 KeV) observations with the Advanced CCD Imaging Spectrometer (ACIS) mounted onboard the *Chandra* spacecraft (cite: Weisskopf2000) during Cycle 23 (PI: S.Cantalupo). The final FoV extends above the $24\times24\rm\,cMpc^2$ observed by FORS2 and HAWK-I and provides $\approx1\rm\,arcsec$ resolution imaging and moderate resolution spectroscopy. We also observed the field with the Hubble Space Telescope (HST) for a total of 22 orbits in Cycle 30 (PID: 17065, PI: S. Cantalupo) and used the HST/ACS (Advanced Camera for Survey, (cite: Ford1998)) instrument to image a $\approx3.4\times3.4\rm\,arcmin^2$ FoV around the central quasar with the filters ACS F625W (25397 sec) and ACS F814W (30238 sec). We complemented our multiwavelength dataset with the *James Webb* Space Telescope (JWST, (cite: Rigby2023)) pre-imaging observations associated to the GO Cycle 1 programme ID 1835 ((cite: Cantalupo2021_JWST), PI S.Cantalupo). With an on-source exposure time of $\approx2\times27\rm\,minutes$, we pointed JWST/NIRCam to image a $2\times5\rm\,arcmin^2$ FoV with the extra-wide filters F150W2 (in the short wavelength channel, $0.6-2.3\rm\,\mu m$) and F322W2 (in the long wavelength channel, $2.4-5.0\rm\,\mu m$). Details on the data reduction are reported in (cite: Wang2024_bigwheel). Finally, (cite: Pensabene2024) targeted the field with a Cycle 8 ALMA programme (ID 2021.1.00793.S, PI S. Cantalupo) surveying the $4\times4\rm\,cMpc^2$ MUSE FoV with Band 3 and Band 6 mosaics to detect dusty star forming galaxies via their 1.2 mm continuum emission or CO(4–3) emission lines. The data and the reduction steps are detailed in (cite: Pensabene2024).

# Data analysis

We describe in this section the methods we adopted to search for galaxies around the target quasar. The rest-frame UV color selections used to identify the Lyman break galaxies in the FORS2 images are detailed in Section [3.1](#sec:sel_UBR) and Appendix [7](#sec:sel_UGR). The sample of continuum-selected galaxies identified in the MUSE mosaic, as well as their spectroscopic redshift measurements, is described in Section [3.2](#sec:sample_MUSE).

## Photometric selection of Lyman break galaxies

![](UBR_selection.pdf)

To identify the Lyman break galaxies at $z\approx3-3.5$ across the FORS2 FoV, we calibrated a selection based on $U-B$ and $B-R$ colors (cite: Bielby2011). We carefully choose those photometric bands to avoid any possible contamination due to the presence of bright Ly$\alpha$ emission which may be arising from the recombination of the ionizing radiation emitted by the central quasar, rather than from the galaxies’ activity. To calibrate the selection region, we used BPASS SPS models ((cite: BPASS2018), v2.2-100bin-t8.0-Z001) with a Salpeter IMF (cite: Salpeter1955) up to a stellar mass limit of $M_\star=100M_\odot$, binary evolution and stellar metallicity $Z_\star=0.001$ (corresponding to $Z_\star\approx0.07\,Z_\ensuremath{\odot}$ with solar abundances from (cite: Asplund2009)). We assumed a constant star formation history and stellar age of $t=10^8{\rm\,Yr}=100\rm\,Myr$, chosen to be consistent with the median age of the stellar population of the galaxies identified in MUSE (see Section [3.4](#sec:SED_fitting) and also (cite: Steidel2018) for a similar approach). We also considered discrete values of reddening: $E(B-V)=0,0.05,0.10,0.15,0.20$, which are typical values for LBGs at $z\approx3$ (cite: Shapley2003). The models are then post-processed to account for the attenuation due to the absorption from the inter-galactic medium. We thus generated 500 IGM realizations randomly extracted from 1000 sightlines from (cite: Steidel2018) and produced by inserting along each line-of-sight intervening H i absorption-line-systems, based on their column density distribution function reported in (cite: Rudie2013), to reproduce the stochastic nature of the IGM absorption. Finally, the color criterion requires:

(i) $U>U_{\rm BKG}^{3\sigma}$

(ii) $U-B>1.89$

(iii) $B-R<1.74\times(U-B)-1.24$

(iv) $0.31<B-R<2.20$

The first condition corresponds to requiring that the source is not detected in U-band above $3\sigma_{\rm BKG}$, where $\sigma_{\rm BKG}$ is the RMS of the background measured within the same aperture used for colors, and is added to avoid contamination from sources at lower redshift and stars (see an application of this same criterion to select U-dropouts galaxies at $z\approx3$ in (cite: vdBurg2010)).

We choose the R-band as the detection image and run SExtractor with the following parameters: i) threshold=1.5 weighted on the mosaic exposure map to assure a uniform threshold across the FoV; ii) minarea=5 pixels, corresponding to $\approx1.3\rm\,arcsec^2$; iii) default deblending parameters. The image is also filtered with a $3\times3$ Gaussian kernel to optimize the detection of faint objects. Colors are measured within a fixed circular aperture of $d=5\rm\,pixels\approx1.26\rm\,arcsec$, although we found that the results do not dependent on the radius of the aperture by varying this within the range $0.5-2.0\rm\,arcsec$. The radius is then re-scaled for the variations of the PSF between the different images, as listed in Table [4](#tab:fors). The results are reported in Figure [3](#fig:sample_LBG). All the candidates have been visually inspected to remove the objects that lie partially outside the edge of the FoV, the photometry of which cannot be performed on the full-size of the source. As a result, we identified 535 $z\approx3.0-3.5$ LBGs across $24\times24\rm\,cMpc^2$. The quality of the color selections is tested by cross-matching the catalogue of LBG candidates to the spectroscopic sample of galaxies identified in MUSE (Section [3.2](#sec:sample_MUSE)), as reported in Table [5](#tab:color_plus_MUSE).

## MUSE spectroscopic sample of galaxies

By leveraging the deep MUSE observations, we searched i) for a spectroscopic confirmation of the color-selected Lyman break galaxies; ii) additional continuum-selected sources in close proximity to the central quasar that are not detected in the shallower FORS2/R-band nor color-selected as LBGs. To this end, we run SExtractor in the MUSE white-light image, obtained by collapsing the datacube along the wavelength direction, with the parameters: i) threshold=2.5 rescaled by the RMS of the background to guarantee a uniform threshold across the FoV; ii) minarea=6 pixels, corresponding to $\approx 1.2\rm\,arcsec^2$; iii) minimum deblending parameter deblend$\_$mincont=0.0001. The spectra are extracted within an aperture $r=2.5\times R_{\rm Kron}$ to collect the total flux of the sources. We assign a spectroscopic redshift to the continuum-detected sources by using M. Fossati fork[^5] of Marz tool (cite: Hinton2016), which includes additional high-resolution templates suitable for high-redshift galaxies. We attribute confidence scores to the redshift measurements following the method illustrated in (cite: Bielby2019).

We are able to assign a high-confidence spectroscopic redshift to $\approx38\%$ of the sources. We attribute low confidence to all the sources that exhibit bright Ly$\alpha$ emission at $z\approx z_{\rm QSO}$ on top of a low signal-to-noise continuum and in absence of other spectral features. This choice is motivated by the presence of the bright target quasar, which prevents us from ruling out whether the Ly$\alpha$ emission is powered by a $z\approx z_{\rm QSO}$ galaxy or it arises from recombination emission of the quasar radiation on top of a featureless continuum emitted by a foreground or background object. We thus require at least two of the following stellar and interstellar absorption or nebular emission lines to be clearly recognizable in the rest-frame UV spectra: Ly$\alpha\,1216\,$Å, N v$\,\lambda1240\,$Å, Si ii$\,\lambda1260\,$Å, O i+Si II$\,\lambda1303\,$Å, C ii$\,\lambda1334\,$Å, Si ii$\,\lambda1526\,$Å, C iv$\,\lambda\lambda1548,1550\,$Å, Fe ii$\,\lambda1608\,$Å, He ii$\,\lambda1640\,$Å, Al ii$\,\lambda\lambda\lambda1670,1854,1862\,$Å, C iii$\,\lambda\lambda1906,1908\,$Å.

With this method, we identify 21 galaxies with high-confidence spectroscopic redshifts lying within a line-of-sight separation $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ from the central quasar (right panel in Figure [2](#fig:Summary_FoV)). To prove that our selection of galaxies associated with the QSO is robust against the choice of velocity window, we searched for galaxies within a larger range $\lvert\Delta\varv\rvert\leq2500\rm\,km\,s^{-1}$ in the MUSE cube and found that the number of sources increases only marginally, by $\lesssim10\%$. In order to complete the characterization the galaxy population around the central quasar, we cross-match the catalogue of MUSE galaxies to the sample of X-Ray emitting AGN observed with *Chandra* (Travascio et al., submitted) and to that of dusty star-forming galaxies detected with ALMA by (cite: Pensabene2024). We identified a total of five AGN detected in X-Ray, three of which are also CO(4–3) line emitters (see Figure [2](#fig:Summary_FoV)).

As a final step, we cross-match the catalogue of color-selected Lyman break galaxies with the spectroscopic sample assembled in MUSE and report the results in Table [5](#tab:color_plus_MUSE). The majority of the LBG candidates ($\gtrsim45\%$) is found within $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ from the quasar. Only $\approx15\%$ has a redshift outside this narrow window, but within the range $2.8<z<3.5$ the color selection is calibrated on. The remaining sources have insufficient spectroscopic information to confidently constrain their redshifts. Compared with the spectroscopic sample, the galaxies that are not color-selected are on average $\times1.2$ more massive (stellar masse $\log(M_\star/M_\odot)\gtrsim10$), and $\times2.4$ more dust extincted (visual extinction $A_{\rm v}\gtrsim0.5$) than those classified as LBGs.

| LBGs selection$^{(a)}$ | Area$^{(b)}$ $[\rm cMpc^2]$ |  MUSE$^{(c)}$  |
|:----------------------:|:---------------------------:|:--------------:|
|          UBR           |        $24\times24$         | $53\%$ (10/19) |
|          UGR           |         $4\times4$          | $79\%$ (15/19) |

: Report of $UBR$ and $UGR$ color selections calibrated to identify $3.0<z<3.5$ Lyman break galaxies around the central quasar.

Table notes:

## Control-field samples

We describe in this section the two independent control samples we built to properly compare the properties of the galaxies identified near the quasar to the expectations for random regions of the universe. To guarantee a consistent comparison, we make sure that these control samples have a similar selection function to the spectroscopic sample of galaxies identified in MUSE.

We first explored publicly available MUSE datacubes. We selected fields observed with $10$ hours of exposure time and without any bright quasar at $z\approx3.0-3.5$, which are known to be biased tracers of galaxies overdensities (cite: Garcia_Vergara2017). In the final sample we included the most recent data release (cite: Bacon2023) of the MUSE-Hubble Ultra Deep Field (cite: Bacon2017), Q0055$-$269 and Q1317$-$0507 from the MUSEQuBES survey (cite: Muzahid2020), which were all observed as part of the MUSE-GTO programme, and the archived J162116$+$004823 and J200324$-$325144 (cite: Muzahid2020) from the MAGG survey (cite: Lofthouse2020; Fossati2021; Galbiati2023; Galbiati2024). To be fully consistent with the selection function of this work, we searched these datacubes for continuum-detected galaxies and required high-confidence spectroscopic redshifts to be measured with the same criterion adopted in Section [3.2](#sec:sample_MUSE). As a result, we identify 43 galaxies (hereafter called “MUSE-FIELD” sample) with spectroscopic redshift in the range $2.5<z<4.5$ spread across an area over three times larger than the MQN01 MUSE FoV. As a complementary analysis, we also identified a control sample from our own MUSE datacube of the MQN01 including 11 continuum-detected galaxies within the range $2.5\lesssim z\lesssim4.5$, excluding those with velocity separation $\lvert\Delta\varv\rvert\leq1500\rm\,km\,s^{-1}$ from the quasar’s redshift to avoid contamination due to the proximity to the central QSO.

## Galaxies’ physical properties and SED fitting

We aggregated all the photometric measurements from the multiwavelength data described in Section [2](#sec:data) to derive the properties of all the galaxies confidently identified within the redshift range $2.5\lesssim z\lesssim4.5$ in the MQN01 MUSE mosaic, that is, those around the central quasar as well as those in the control-field sample. Specifically, we aim at constraining the stellar mass ($M_\star$), star formation rate ($\rm SFR$) and dust extinction ($A_{\rm v}$) of each source.

As five of the 21 sources included in the MUSE spectroscopic sample are X-Ray detected AGN, we use the publicly available code CIGALE ((cite: Burgarella2005; Noll2009; Boquien2019), version 2022.1, which includes X-Ray implementation by (cite: Yang2020; Yang2022_cigale)) to separate the contribution of the AGN from that of the host and derive a reliable estimate of the galaxies’ SFR and stellar mass. We chose high-resolution (cite: BC03) stellar population models, (cite: Chabrier2003) initial mass function and (cite: Calzetti2000) dust law. We fixed both the stellar and the gas-phase metallicity to 0.20 (solar), 0.08 and 0.04 in separate runs. Similarly, we also performed different runs with an exponentially declining, a delayed exponentially declining or an effectively constant ($\tau=10\rm\,Gyr$) star formation history. We notice that such different assumptions on the metallicity and star formation histories lead to results that are consistent within $1\sigma$ with each other, and thus consider the output obtained assuming solar metallicity and exponentially declining star formation history across the paper. The AGN and the X-Ray emissions are modelled following (cite: Fritz2006) and (cite: Yang2022_cigale), respectively. The full input grid of parameters is adapted from (cite: Barrufet2020) and (cite: Riccio2023), and listed in Table [\[tab:CIGALE_AGN\]](#tab:CIGALE_AGN). To estimate realistic uncertainties on the best-fit stellar mass and SFR, we follow (cite: Pacifici2023) and combine the observed uncertainties inherited from photometry, with those related to the choice of the models (e.g., star formation history and stellar physics). We adopted an uncertainty value of $0.2\rm\,dex$ for the stellar mass (cite: Conroy2013) and of $0.3\rm\,dex$ for the SFR. Compared to the typical errors returned by the fitting code ($\approx 0.09\rm\,dex$ for the stellar masses and $\approx 0.04\rm\,dex$ for the SFR), the dispersion due to systematics is the dominant source of uncertainty. The properties estimated for each galaxy are listed in Table [\[tab:SED_table\]](#tab:SED_table). We also prove that these results are independent on the code used to fit the galaxies’ SED in the Appendix [11](#app:SED_table).

# Results

## A large overdensity of star-forming galaxies clustered around the quasar

![](zHist.pdf)

To characterize the large-scale environment around the central QSO, we first investigate the clustering of the galaxies relative to the quasar along the line-of-sight. We reproduce in Figure [4](#fig:res_zhist) the redshift distribution of the MQN01 high-confidence spectroscopic sample of galaxies identified in the MSUE FoV (black) and of the Lyman break galaxies selected via $UBR$ colors (Section [3.1](#sec:sel_UBR)) for which a secure measurement of the spectroscopic redshift is available from MUSE (hatched gray histogram). The histogram is normalized by the different areas we surveyed to assemble the samples. An excess of galaxies peaked within the redshift interval $3.15\lesssim z\lesssim3.35$ clearly emerges. To roughly estimate the amplitude of the local clustering, we compare these results to expectations for the “MUSE-FIELD” sample and report that the surface density of galaxies identified in the redshift bin closest to the quasar is a factor of $\approx8$ larger than the field. Similarly, the surface density of $UBR$-selected galaxies is higher by a factor of $\approx5.5$ compared to the field. Zooming in around the quasar in terms of the line-of-sight velocity, we observe that the majority of the sources are clustered within an even narrower velocity range (see the inset in Figure [4](#fig:res_zhist)), corresponding to $\pm1000\rm\,km\,s^{-1}$. We thus select it as a linking window to identify the galaxies connected to the central quasar throughout the following analysis.

## Luminosity Function and amplitude of the overdensity

![](Cumulative_LF_wUBR_Panel1.pdf)

Once established that an excess of star-forming galaxies is found in proximity to the quasar, we now provide a more statistical argument to investigate the amplitude of the overdensity relative to blank fields. We thus compute the cumulative luminosity function (LF), $\phi_{\rm c}(\rm<M_{R})$, defined as the number density of galaxies as a function of their luminosity. In order to account for the difference in redshift compared to the surveys available in the literature, we convert the flux measured in the R-band into absolute magnitude, $M_{\rm R}$. To obtain the cumulative luminosity function, we first compute the differential number of galaxies at a given magnitude and per unit volume within nine intervals of $\Delta M_{\rm R}=0.175\rm\,mag$ and associate uncertainties from Poisson statistics. The differential measure is then integrated along the magnitude axis. We apply this procedure for the sample of 21 galaxies spectroscopically identified to lie within $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ around the redshift of the quasar. The results are shown in Figure [5](#fig:res_LF_R). We produce the cumulative luminosity function also for the “MUSE-FIELD” sample of galaxies in the range $3.0\leq z\leq3.5$ following the same steps described above. For these galaxies, the $M_{\rm R}$ magnitude is estimated by convolving their spectra with the transmission curve of the FORS2/$R_{\rm special}$ filter. Similarly, we also produce the cumulative luminosity function for all the galaxies identified in the MUSE mosaic within $2.5<z<4.5$, masking the peak of the overdensity in velocity space around the quasar. The luminosity functions of these two independent field samples are consistent with each other, both in shape and normalization. The consistency of the comparison is achieved by having searched for the galaxies in the same MUSE datacube or in those with similar exposure time, $\approx10\rm h$, and applied the same method and constraints to select only the sources with a precise measure of their spectroscopic redshift. On these bases, we assume the selection function to be the same across the samples and do not apply any completeness corrections to the above luminosity functions. In addition, we prove the normalization of the luminosity function of the field sample to be consistent with results derived in $\mathcal{R}$-band by (cite: Reddy2009) for a sample of color-selected LBGs with a spectroscopic redshift in the range $2.7\leq z<3.4$.

To statistically measure the amplitude of the overdensity around the quasar, we take the ratio[^6] between the cumulative luminosity function and the one from (cite: Reddy2009). As shown in Figure [5](#fig:res_LF_R) (lower panel), we measure an overdensity $\rho/\bar{\rho}=53\pm17$ at $M_{\rm R}\leq-19.25\rm\,mag$. We also note that the overdensity is flat as a function of the magnitude threshold up to $M_{\rm R}=-19.5\rm\,mag$ and declines at fainter magnitudes due to the incompleteness of the sample. This suggests that, on average, we only find a shift in the normalization of the luminosity function and do not observe any excess of bright or faint galaxies in the environment around the quasar compared to the field. We also perform the same analysis for the sample of color-selected LBGs and show the derived rest-frame UV luminosity functions in Appendix [8](#app:LF_LBGs).

## Clustering analysis

![](Correlation_Functions.pdf)

Comparing the correlation length of the galaxies clustered around different quasars at similar redshifts encodes key information about the structures in which they are hosted. We follow the formalism from (cite: Trainor2012), TS12 hereafter, and derive the galaxy-galaxy auto-correlation function, $w_{\rm GG}$, and the quasar-galaxies cross-correlation function, $w_{\rm QG}$. In three dimensions, the correlation functions are typically modelled by a power law, $\xi=(r/r_0)^{-\gamma}$, where $\gamma$ is the slope and $r_0$ the correlation length. Once integrated in the redshift direction, the projected correlation functions take a functional form that still depends on the parameters $\gamma$ and $r_0$ (see, eq. 10 in TS12). In each radial bin, we compute $w_{\rm GG,QG}(R)=(N_{\rm obs}/N_{\rm exp})-1$, where $N_{\rm obs}$ is the observed number of galaxies identified within a radial bin and $N_{\rm exp}$ is the expected one, derived from the luminosity functions of the field sample from Section [4.2](#sec:result_LF). To compute the galaxy-galaxy auto-correlation function without being affecting by the presence of the quasar in our field, we took the $2.5<z<4.5$ galaxies with spectroscopic redshift measured from rest-frame UV absorption lines, that is, similar to our selection in Section [3.2](#sec:sample_MUSE), from the UDF catalog (cite: Bacon2023). In addition, we proved this result to be consistent with upper limits for the auto-correlation of the galaxies identified in our field at $2.5<z<4.5$, masking $\lvert\Delta\varv\rvert\leq1500\rm\,km\,s^{-1}$ around the redshift of the quasar. The results are shown in Figure [6](#fig:clustering), with the horizontal errorbars marking the width of each radial bin and the vertical ones derived from the 16th and 84th percentile of the distributions obtained by bootstrapping over the sample of galaxies. We derive the correlation length by fitting the equation 10 from TS12 to the data. The slope, $\gamma$, is degenerate with the correlation length and therefore fixed to different values to facilitate consistent comparisons with the literature. The best-fit results are shown in Figure [6](#fig:clustering) and listed in Table [6](#tab:clustering). The uncertainties are obtained from the 16th and 84th percentiles of the bootstrap distributions. The cross-correlation length estimated for spectroscopically-selected star forming galaxies in MQN01 is substantially higher than the galaxy-galaxy correlation lengths obtained using the same selection, and higher than the values found around other quasars in the literature at similar times, e.g. compared to TS12. In Section [5.1](#sec:disc_overdensity), we discuss the implications of these results.

|  |  |  |  |
|:--:|:--:|:--:|:--:|
|  |  |  |  |
| function |  |  |  |
| $\lvert\Delta\varv\rvert\le1000\rm\,km\,s^{-1}$ |  |  |  |
| $\lvert\Delta\varv\rvert\le1500\rm\,km\,s^{-1}$ | $\gamma$ |  |  |
|  |  |  |  |
| $w_{\rm QG}^{\rm MQN01}$ | $23.06^{+3.49}_{-3.43}$ | $22.39^{+3.72}_{-3.36}$ | 1.5 |
|  | $15.71^{+1.79}_{-1.83}$ | $14.08^{+1.76}_{-2.01}$ | 1.8 |
|  |  |  |  |
| $w_{\rm GG}^{\rm UDF}$ | $4.25^{+1.56}_{-1.44}$ | $2.65^{+1.28}_{-1.10}$ | 1.5 |
|  | $3.54^{+1.05}_{-1.08}$ | $2.36^{+0.92}_{-0.83}$ | 1.8 |

: Quasar-galaxies cross-correlation and galaxy-galaxy auto-correlation lengths measured for the MUSE spectroscopic sample and for the field galaxies identified in the UDF-MOSAIC (cite: Bacon2023), respectively.

## Galaxies’ star formation activity compared to the field

![image](FLD_SED_Main_Sequence_SFR.pdf) ![image](FLD_SED_Main_Sequence_sSFR.pdf)

How the large-scale environment affects galaxies growth is a key question within the framework of galaxy evolution in a hierarchical universe, especially in overdense regions throughout cosmic time. A useful approach to gauge galaxies’ ability to accrete cold gas and sustain star formation is by looking at their positioning in the stellar mass versus star formation rate (or specific star formation rate, sSFR) plane relative to the "main sequence" (cite: Brinchmann2004; Daddi2007; Elbaz2007; Noeske2007; Salim2007).

In Figure [7](#fig:SED_mainseq) we directly compare the star formation rate (left panel) and the specific star formation rate (right panel) as a function of galaxies’ stellar mass derived for the galaxies clustered around the quasar with the star forming main sequence at $z\approx3.25$. We parametrized the main sequence with the functional forms from (cite: Speagle2014) (blue), (cite: Popesso2022) (green) and (cite: Koprowski2024) (purple) at the quasar redshift, allowing for a $0.3\rm\,dex$ dispersion. The method we used to identify the galaxies (Section [3.2](#sec:sample_MUSE)) selects rest-frame UV bright sources, that is, actively star forming and not too heavily obscured by dust. In other words, our selection tends to exclude passive or extremely red galaxies. As a result, at a given stellar mass, we do not observe any significant offset from the main sequence calibrated on blank fields at $z\approx3$ for the clustered galaxies, nor for the AGNs detected by *Chandra* (yellow squares in Figure [7](#fig:SED_mainseq)). The evidence that galaxies form stars at main sequence rates seems to be a recurrent feature in some of the known $z\approx2-3$ protoclusters (cite: Koyama2013a; Koyama2013b; Cooke2014; Shimakawa2017; Shimakawa2018; Shi2019a; Shi2019b; Shi2020; Toshikawa2024).

Due to the differences in the selection function and in the SFR estimates between the sample of MQN01 galaxies and the ones used to calibrate the parametrizations of the main sequence, it is more informative to directly compare the properties of the galaxies in the overdensity to those included in a field sample with a similar selection function. To this end, we consider the control-field sample of 11 galaxies identified in the MUSE FoV (see, Section [3.3](#sec:field_samples)). All these galaxies are scattered along the expected main sequence. In addition, we compare the distributions of stellar mass (top panels), SFR and sSFR (right panels) shown in Figure [7](#fig:SED_mainseq) by performing a KS test (significant at $2\sigma$ level for $p$-values$\leq0.05$). While the distributions of sSFR are unlikely drawn from the same parent one, $p-$value$\approx0.01$, there is no statistical difference in those of stellar mass and SFR ($p$-value$\approx0.35$ and $p-$value$\approx0.45$, respectively). Nonetheless, we notice that we find only one galaxy in the field sample located in the $\log(\rm M_\star/M_\odot)\gtrsim10.5$ region of the main sequence, and it is possibly the excess of galaxies in the high-mass tail of the distribution that is driving the difference in the sSFR. The direct comparison between the distributions of the two samples does not take into account the different encompassing co-moving volume ($\approx2\times10^4\rm\,cMpc^3$ for the field sample, which is more than 50 times larger compared to that of the sample of galaxies clustered around the quasar). Normalizing the number of sources by the co-moving volume, we find that the number density of massive ($M_\star\gtrsim10^{10.5}M_\odot$) star forming galaxies is $217^{+200}_{-183}$ times higher around the quasar than in a blank field. Even accounting for the overdensity of $\approx53$ measured around the quasar in Section [4.2](#sec:result_LF), the presence of massive galaxies exceeds by a factor of $4^{+2}_{-3}$ the expectations for the field (see, Section [8](#fig:SED_stellarMF) for details). On the other hand, the incidence of $M_\star\lesssim10^{10.5}M_\odot$ galaxies around the quasar is $92^{+80}_{-43}$ times larger than in the field sample, which corresponds to a factor of $1.7^{+1.6}_{-0.8}$ once accounting for the overdensity. This results also corresponds to a factor of $4^{+2}_{-3}$ more galaxies forming stars at a rate $\log[\rm SFR/(M_\odot Yr^{-1})]\geq1.7$ around the quasar compared to blank fields. In terms of sSFR, the massive star-forming galaxies discussed above reside at $\log(\rm sSFR/Yr^{-1})<-8.5$, leading to a large overdensity ($11^{+7}_{-9}$) in this sSFR range as well. This scenario is thus consistent with a picture where a consistent fraction of galaxies in this overdense environment is experiencing a phase of accelerated mass assembly and is rapidly consuming its gas content.

## Galaxies’ stellar mass function

![image](FLD_Stellar_Mass_FunctionBC03_Cumulative.pdf) ![image](FLD_Stellar_Mass_FunctionBC03_Cumulative_v1.pdf)

Motivated by the results obtained in Section [4.4](#sec:result_MainSeq), we now compute the galaxies’ number density as a function of their stellar mass by integrating the differential stellar mass function and propagating the Poisson errors arising in each interval of masses. To also take into account the errors on the measure of the stellar mass itself, we bootstrap varying the fiducial values within the uncertainties derived from the galaxies’ SED fitting for 1000 times. The standard deviation from the 16th and 84th percentiles of the resulting bootstrap distribution is then squared and summed with errors propagated from the integral above. In the right-panel in Figure [8](#fig:SED_stellarMF) we show the resulting cumulative stellar mass function, while in the left-panel we normalize it at the stellar mass completeness limit[^7] to better capture any difference in shape. The estimate for the galaxies around the quasar (black stars) is compared to the expectations for different field samples. We thus take as a reference the stellar mass function computed by (cite: Weaver2023) in the COSMOS2020 field within the redshift range $3.0<z<3.5$ and rescale it by the MQN01 overdensity $\rho/\bar{\rho}\approx53$. This is also consistent with what we obtain for the galaxies included in the control-field sample and identified within the redshift range $2.5<z<4.5$, masking the peak of the overdensity in velocity space (orange diamonds). While both the stellar mass functions flatten and deviate from (cite: Weaver2023) field expectations at $\log(M_\star/M_\odot)\lesssim9.5$, likely due to the incompleteness of the samples, that of star-forming galaxies clustered with the quasar is also flatter at masses $\log(M_\star/M_\odot)\gtrsim10.5$. In other words, this change in the shape of the stellar mass function provides evidence that the surroundings of the quasar are richer in massive galaxies compared to the field, with $4\pm2$ and $24\pm11$ times more sources in the two bins at $\log(M_\star/M_\odot)\gtrsim10.5$, respectively, once accounted for the overdensity.

## Connecting the local overdense environment to the galaxy properties

![](vs_Overdensity_withFLD_NOBINNING.pdf)

We now turn to investigate how the properties of the galaxies depends on the local overdensity. We thus employ a scale-independent Voronoi Tessellation (one element per cell) to parametrize the local density of galaxies clustered around the quasar. According to this criterion, the size of each cell is, by construction, inversely proportional to the local galaxy surface density (i.e., small cells corresponds to crowded environments). Open cells at the edge of the FoV (7/21) are excluded from the analysis due to the loss of information about the objects located outside the MUSE mosaic. The overdensity is then defined as $\Delta=\rho/\bar{\rho}-1$ (so that $\log(1+\Delta)=0$ corresponds to the case in which the galaxy density is the same as the field, i.e., $\rho=\bar{\rho}$). We show in Figure [9](#fig:OverdensityProfiles) how the SFR, stellar mass and sSFR correlate with the local galaxy density. To address this analysis on a more statistical basis, we also performed a Spearman-rank correlation test and report in Table [7](#tab:corr_overdensity) the strength of the correlation, $\rho_{\rm spearman}$, and the probability that no monotonic relation exists between the two variables, $p$-value. We require $p$-value$\leq0.05$ for a correlation to be significant at least at 2$\sigma$ confidence level. As a result, we observe that the galaxies’ stellar mass and specific star formation rate are positively and negatively, respectively, correlated ($|\rho_{\rm spearman}|\gtrsim0.45$ and $p$-value$\approx0.05$) with the local density at $2\sigma$ significance. On the other hand, we do not observe any significant environmental effect on the star formation rate itself ($p-$value$\approx0.29$).

|             Variable              | $\rho_{\rm Spearman}$ | $p$-value |
|:---------------------------------:|:---------------------:|:---------:|
| $\log\rm[SFR/(M_{\odot}Yr^{-1})]$ |         +0.27         |   0.29    |
|    $\log\rm(M_\star/M_\odot)$     |         +0.46         |   0.05    |
|      $\log\rm(sSFR/Yr^{-1})$      |         -0.50         |   0.04    |

: Results of the Spearman-rank test on the correlations between the properties of the MQN01 galaxies and the local overdensity.

## Probing the structure on larger scales

![image](Overdensity_Map_size_7_arcsec.pdf) ![image](Overdensity_MUSE_Map_size_5_arcsec.pdf)

The large-scale structures in which galaxies are embedded are expected to extend well beyond the $\approx4\times4\rm\,cMpc^2$ we are able to trace with the star-forming galaxies identified within the FoV of the MUSE mosaic. We thus model the 2D spatial distribution of the $UBR$-selected LBGs across the $\approx24\times24\rm\,cMpc^2$ FoV of FORS2 and compare it to that of the spectroscopically selected sources lying within $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ from the quasar in the $4\times4\rm\,cMpc^2$ FoV of the MUSE mosaic. This is done by creating an evenly spaced grid of $7"\times7"$ and $5"\times5"$ cells covering the entire FORS2 and MUSE FoV, respectively. The number of galaxies identified within each cell is then normalized by the volume of the cell and compared to the co-moving density expected for the field sample (see Section [4.2](#sec:result_LF)). The grid is then oversampled (by a factor of 3 and 2, respectively) and smoothed with a Gaussian Kernel ($\sigma=6,5$, respectively, corresponding to $\approx0.5"$). Results are shown in Figure [10](#fig:voronoi_LBG).

The LBGs appear to be overdense ($\rho/\bar{\rho}\gtrsim1$) across the entire $\approx24\times24\,\rm cMpc^2$ FoV, even at large distances from the central quasar. The overdense regions $\rho/\bar{\rho}\gtrsim1.5$ are concentrated closer to the center of the field and show a preferential vertical orientation, which corresponds to the North-South direction on the sky, and is also aligned with both the overdensity of spectroscopically-selected galaxies that we observe in MUSE (right panel) and the extended Ly$\alpha$ emitting gas observed by (cite: Borisova2016) and Cantalupo, et al. (in prep.). This evidence supports a picture in which the large-scale structure traced by the galaxies clustered with the quasar extends well beyond the FoV of the MUSE mosaic, for tens of cMpc. We reserve a more statistical treatment of the LBGs alignment as a function of the local overdensity to Appendix [9](#sec:alignement). On the other hand, when looking at this structure on scales of $24\times24\rm\,cMpc^2$, we observe that the most overdense regions, $\rho/\bar{\rho}\gtrsim2$, are not found within the FoV of the MUSE mosaic, but are mostly concentrated in the southern part of the field. A number of possible scenarios, or a combination of them, should be tested to explain this evidence: i) they are part of a foreground or background structure; ii) the structure surrounding the quasar itself extends in the southern direction; iii) despite being close to the peak of the overdensity in the MUSE FoV, the quasar is not the center of the structure, which is instead in the South; iv) they are tracing two merging or interacting structures. Spectroscopic confirmation of the LBGs would be essential to discriminate between these scenarios.

# Discussion

In this section, we put the results presented above into a broader context by comparing them to previous results available in the literature. In particular, in Section [5.1](#sec:disc_overdensity) we discuss the overdensity and clustering measurements in MQN01 in light of other studies targeting quasars and overdense regions at $z>2$. In Section [5.2](#sec:disc_galaxy_evolution), we focus on the galaxies’ sSFR and stellar mass function in MQN01 comparing them to other works from the literature, both in the field and in overdense regions, in order to reveal the possible role of the local environment on galaxy formation and evolution.

## MQN01 overdensity and clustering compared to other fields

The number of galaxies spectroscopically confirmed to be within $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ and in an area of $\approx4\times4\rm\,cMpc^2$ ($\approx2\times2\rm\,arcmin^2$) around the MQN01 quasar results in an overdensity of $\rho/\bar{\rho}=53\pm17$ which corresponds to a surface density of $\approx1.3\rm\,cMpc^{-2}$. At a redshift similar to that of MQN01, several galaxy overdensities and protoclusters have been studied in the literature, such as SSA22 at $z\approx3.08$ (cite: Steidel1998; Steidel2003), Hyperion at $z\approx2.47$ (cite: Cucciati2018) and Spiderweb at $z\approx2.15$ (cite: Roettgering1994; Pentericci1997). In particular, (cite: Topping2016) found 40 LBGs in SSA22 with spectroscopic redshift in the range $z=3.05-3.12$ across $17.25\times17.25\rm\,cMpc^2$, which result in a surface density of $\approx0.13\rm\,cMpc^{-2}$. (cite: Huang2022) discovered 53 Ly$\alpha$ emitters in a region extended over $\approx30\times20\rm\,cMpc^2$ in Hyperion, with a surface density of $\approx0.08\rm\,cMpc^{-1}$. In Spiderweb, (cite: PerezMartinez2023) found 39 spectroscopically confirmed H$\alpha$ emitters across $13.7\times19.3\rm\,cMpc^2$, corresponding to a surface density of $\approx0.15\rm\,cMpc^{-1}$. Notably, the surface density measured in the MQN01 field is $\approx10-20$ times higher with respect to these structures. A direct comparison, however, is not straightforward given the different galaxy populations selected in these works, the different levels of completeness reached and the surveyed volumes. A detail comparison would require, for instance, a MUSE (or KCWI) survey in these proto-cluster fields, similar to the one performed around MQN01.

Besides the large overdensity of star-forming galaxies in the field, a significant excess of galaxies in MQN01 obtained with different tracers has been reported. In particular, (cite: Pensabene2024) found $\approx18$ times more CO(4–3) line emitters and higher 1.2mm source number counts compared to blank fields, with the latter result that is similar to the findings in SSA22. Exploring *Chandra* X-Ray data, an overdensity of $\rho/{\bar\rho}\approx1000$ of AGNs has recently been unveiled by Travascio et al., (submitted) and found to exceed that observed in SSA22 and Spiderweb protoclusters. These studies support the peculiarity of the MQN01 field in terms of galaxy overdensity as suggested by our spectroscopic study in the rest-frame UV.

Stronger evidences about the rarity of the MQN01 structure are obtained by the cross-correlation function presented in Section [4.3](#sec:radial_overdensity). In particular, we obtained a quasar-galaxy cross-correlation length of $r_0=15.71^{+1.79}_{-1.83}~h^{-1}{\rm cMpc}$, which is signifcantly higher than the galaxy-galaxy correlation length of $r_0=3.54^{+1.05}_{-1.08}~h^{-1}{\rm cMpc}$ for fixed $\gamma=1.8$. Despite the limited statistics, the cross-correlation lengths obtained using CO(4–3) line emitters around the MQN01 by (cite: Pensabene2024), $r_0=10.8^{+8.8}_{-4.7}\,h^{-1}\rm cMpc$, are also consistent with these values. These values clearly indicate that galaxies in the MQN01 structure are more clustered around the quasar compared to both the average fields and other quasars at similar redshifts (cite: Trainor2012; GarciaVergara2021). For consistency and to control for the effects of different selection functions, we compare our results with works that studied the clustering of similar samples of galaxies, within similar volumes and at similar redshifts. TS12 measured an auto-correlation length $r_0=(5.8\pm1.3)\,h^{-1}\rm cMpc$ and a cross-correlation length $r_0=(7.1\pm1.3)\,h^{-1}\rm cMpc$ (once rescaled to the cosmology adopted in this paper, which corresponds to a correction factor of 1.03), assuming $\gamma=1.5$, for a spectroscopic sample of galaxies identified within $\pm1500\rm\,km\,s^{-1}$ from 15 quasars at $z\approx2.7$. The auto-correlation functions of galaxies selected as those found in MQN01, are consistent with that of TS12 (see, Table [6](#tab:clustering)). On the other hand, the cross-correlation lengths of the galaxies identified within $\lvert\Delta\varv\rvert\leq1500\rm\,km\,s^{-1}$ around the quasar is $\approx3.2$ times larger compared to TS12. We also measured the quasar-galaxy cross-correlation function in the MAGG survey (cite: Lofthouse2020), which 28 fields centered on quasars and observed with MUSE (see Appendix [10](#app:clustering_magg) for more details). For consistency with the sample of galaxies used in this work, we considered only those that have been continuum-selected, as described in (cite: Lofthouse2020), brighter than $m_{\rm R}\le26.5\rm\,mag$, with a secure measure of their spectroscopic redshifts and found within $\lvert\Delta\varv\rvert\le1500\rm\,km\,s^{-1}$ from the redshift of each MAGG quasar (median $z\approx3.7$). We derived a cross-correlation length of $r_0=(3.8\pm0.8)~h^{-1}\rm cMpc$ for fixed $\gamma=1.5$. Interestingly, The one measured in the MQN01 field is $\approx6$ times larger. Altogether, these pieces of evidence suggest that the MQN01 quasar could possibly be associated with a much larger halo than the typical quasar host at these redshifts, which is estimated to be around $\log(M_{\rm h}/M_\odot)\approx12-12.5$ (cite: Fossati2021; ArrigoniBattaia2022; DeBeer2023).

## The role of the local environment on galaxy formation and evolution

One of the key results presented in Section [4.5](#sec:SMfunction) is the fact that the galaxy overdensity in the MQN01 galaxies depends on the galaxy stellar mass. In particular, Figure [8](#fig:SED_stellarMF) shows that there is an elevated fraction of massive galaxies compared to the expectations from average regions of the universe, suggesting a possible link between the environment and galaxy growth. Indeed, despite the limited statistics, we find a hint that the local galaxy overdensity is positively correlated with the galaxies’ stellar mass (and negatively correlated with their sSFR) as shown in Figure [9](#fig:OverdensityProfiles). Our results reinforce previous findings in the literature (cite: Darvish2016; Chartab2020; Lemaux2022; Taamoli2023), which did not have the large dynamic range in overdensity as provided by our sample.

For instance, by using a large sample of protocluster candidates, (cite: Toshikawa2024) found that U-dropout galaxies living in overdense regions at $z\approx3$ show a cumulative stellar mass function that is flatter at the massive end compared to the field. Similarly, (cite: Shimakawa2017; Shimakawa2018) found a statistically significant excess of massive galaxies in two $z\approx2$ protoclusters, broadly consistent with other studies of continuum-selected galaxies and H$\alpha$ emitters in overdense regions at similar redshifts (cite: Steidel2005; Koyama2013a; Koyama2013b; Cooke2014). However, they also observe that such massive galaxies are mostly located in the densest regions of the protocluster, while sources in less dense areas have a stellar mass function distribution that is more similar to that of the field (cite: Forrest2024).

The presence of an excess of massive galaxies in overdense regions, such as protoclusters, can be supported by different scenarios: i) the high density environment is able to trigger mergers as well as boost the rate of interactions between galaxies (cite: Alonso2012; Cooke2014; dAmato2020); ii) the access to a large gas reservoir that is efficiently accreted from the cosmic web onto the galaxies (cite: Shimakawa2017). Indeed, (cite: Umehata2019) found that AGNs and sub-millimeter galaxies in the SSA22 protocluster are located within filaments of gas, which can potentially be accreted by these sources fuelling their star formation and driving their growth. On the other hand, there is also evidence that overdensities play a minor role in shaping the scaling relations of galaxies at $z>2$ (cite: McGee2009; Fossati2017), which requires further investigation to be conducted in similar regions of the universe. Altogether, these possible scenarios suggest that these galaxies grew rapidly, either assembling their masses earlier or more efficiently than those in the field.

## Caveats and future prospects

The most important step for a more complete view of the galaxy population in MQN01 is the inclusion of the passive galaxies. One possibility to select them would require, for instance, properly sampling the Balmer break, expected to be in the H-band at the MQN01 redshift. Photometric data obtained with VLT/HAWK-I are currently available and will be used in a future study to complement the dataset presented here. In addition, JWST spectra covering the Balmer lines at rest-frame wavelengths from 400 to 700 nm are available for some galaxies in the field (cite: Cantalupo2021_JWST; Wang2024_bigwheel). However, for a more complete view of the passive galaxy population grism JWST spectroscopy would be necessary. Only a small area of the MQN01 structure, as probed through our LBG survey, currently has MUSE coverage and thus spectroscopic confirmation. An ongoing MUSE survey (Program ID 112.25N3, PI S. Cantalupo) is covering $\approx14\rm\,cMpc$ in the North-South direction and will be used to extend the study of the clustering and the galaxies’ properties up to the outskirt of the structure. Finally, our findings are limited to one individual and rare structure, which prevent us from generalizing them to the broader population of protoclusters. To identify a larger number of systems similar to MQN01 and study their galaxy populations, it would be necessary to conduct systematic deep and wide surveys, for instance with MUSE or KCWI, targeting extended quasar nebulae as signposts for these structures.

# Summary and conclusions

We detected and studied a population of star-forming galaxies clustered within $\approx4\times4\rm\,cMpc^2$ around the $z\approx3.25$ quasar CTS G18.01, known as MQN01 field. The quasar is surrounded by a giant Ly$\alpha$ emitting nebula discovered by (cite: Borisova2016) and Cantalupo, et al. (in prep.), and the field hosts a large overdensity of dusty star-forming galaxies (cite: Pensabene2024) and AGNs (Travascio, et al. submitted). By leveraging a rich set of multiwavelength data, including MUSE, HST, FORS2, HAWK-I, JWST and *Chandra*, we derived the star formation rates and the stellar masses of these galaxies and explored their connection to the local and large-scale overdense environment. The key results are summarized below:

- We discovered an overdensity of star forming galaxies of $\rho/\bar{\rho}=53\pm17$ clustered within $4\times4\rm\,cMpc^2$ and $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ around the central quasar. Measuring the amplitude of the clustering as a function of the projected distance from the quasar, we derived a cross-correlation length that is $\approx3.2$ times larger than the average value found by (cite: Trainor2012) for $z\approx2.7$ quasars. Galaxies in this structure are thus either more clustered or living in a more massive structure than those observed around average quasars at similar times.

- We found that the galaxies in the overdensity are forming stars at a rate consistent with the expected main sequence at $z\approx3.25$. In addition, the ability of these galaxies to form stars appears to be more sensitive to the gas and baryon content of the galaxies, probed by their stellar masses, rather than to the local overdensities and the large-scale environment in which they reside.

- At the high mass end, the cumulative stellar mass function is flatter compared to the field. This suggests the presence of an excess of massive galaxies in the structure, with $\approx4$ times higher number density than in the field at $\log(M_\star/M_\odot)\geq10.5$. In addition, all the massive galaxies are also X-Ray AGNs. Such an excess of massive star forming galaxies may be due to a higher merger rate or efficient accretion that allow the galaxies to assemble their mass at earlier times or more efficiently than in the field and provide them of enough fuel to continue forming stars at main sequence rates.

- The distribution of color-selected Lyman break galaxies on scales $\times36$ larger than the original FoV of the MUSE mosaic suggests that the overdensity extends along the North-South direction and is thus align with the Ly$\alpha$ emitting gas detected by (cite: Borisova2016) around the quasar and to the $\approx4\rm\,cMpc$ filamentary structure observed in emission by Cantalupo et al., (in prep.) This may be a hint that the gaseous structure in which galaxies are embedded extends for tens of cMpc.

Overdense structures, such as MQN01, are ideal places to explore the possible connection between the environment and the properties of galaxies at high redshift. The advancement in the study of overdensities at $z>2$ is finally making it possible to explore a wide range of environments, even at the cosmic noon. However, given their rarity, it is still challenging to build a large sample of such structures, and thus to increase the statistical significance of any possible connection between galaxies and environment. As such, even if based on a single field, our study provides important clues for future investigations to piece together the coevolution of galaxies and their large-scale environments from the very early epochs to the late times.

# Acknowledgements

This project was supported by the European Research Council (ERC) Consolidator Grant 864361 (CosmicWeb) and by Fondazione Cariplo grant no. 2020-0902. MiF gratefully acknowledges support from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (grant agreement no. 757535) and by Fondazione Cariplo, grant no. 2018-2329. This work is based on observations collected at the European Southern Observatory under ESO programmes IDs 102.A-0448(A), and 110.23ZX. This work made use of Astropy (<http://www.astropy.org>) a community-developed core Python package and an ecosystem of tools and resources for astronomy (cite: Astropy2013; Astropy2018; Astropy2022), Numpy (cite: Numpy2020), SciPy (cite: SciPy2020), and Matplotlib (cite: Matpltolib2007).

202 natexlab

(ref: Adams2015) Adams, S. M., Martini, P., Croxall, K. V., Overzier, R. A., & Silverman, J. D. 2015, MNRAS, 448, 1335

(ref: Alberts2022) Alberts, S. & Noble, A. 2022, Universe, 8, 554

(ref: Alonso2012) Alonso, S., Mesa, V., Padilla, N., & Lambas, D. G. 2012, A&A, 539, A46

(ref: Alpaslan2014) Alpaslan, M., Robotham, A. S. G., Driver, S., et al. 2014, MNRAS, 438, 177

(ref: Appenzeller1998) Appenzeller, I., Fricke, K., Fürtig, W., et al. 1998, The Messenger, 94, 1

(ref: ArrigoniBattaia2022) Arrigoni Battaia, F., Chen, C.-C., Liu, H.-Y. B., et al. 2022, ApJ, 930, 72

(ref: Asplund2009) Asplund, M., Grevesse, N., Sauval, A. J., & Scott, P. 2009, ARA&A, 47, 481

(ref: Assef2015) Assef, R. J., Eisenhardt, P. R. M., Stern, D., et al. 2015, ApJ, 804, 27

(ref: Astropy2022) Astropy Collaboration, Price-Whelan, A. M., Lim, P. L., et al. 2022, ApJ, 935, 167

(ref: Astropy2018) Astropy Collaboration, Price-Whelan, A. M., Sipőcz, B. M., et al. 2018, AJ, 156, 123

(ref: Astropy2013) Astropy Collaboration, Robitaille, T. P., Tollerud, E. J., et al. 2013, A&A, 558, A33

(ref: Banados2013) Bañados, E., Venemans, B., Walter, F., et al. 2013, ApJ, 773, 178

(ref: Bacon2010) Bacon, R., Accardo, M., Adjali, L., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7735, Ground-based and Airborne Instrumentation for Astronomy III, ed. I. S. McLean, S. K. Ramsay, & H. Takami, 773508

(ref: Bacon2023) Bacon, R., Brinchmann, J., Conseil, S., et al. 2023, A&A, 670, A4

(ref: Bacon2015) Bacon, R., Brinchmann, J., Richard, J., et al. 2015, A&A, 575, A75

(ref: Bacon2017) Bacon, R., Conseil, S., Mary, D., et al. 2017, A&A, 608, A1

(ref: Baldry2006) Baldry, I. K., Balogh, M. L., Bower, R. G., et al. 2006, MNRAS, 373, 469

(ref: Bamford2009) Bamford, S. P., Nichol, R. C., Baldry, I. K., et al. 2009, MNRAS, 393, 1324

(ref: Barrufet2020) Barrufet, L., Pearson, C., Serjeant, S., et al. 2020, A&A, 641, A129

(ref: Bertin2006) Bertin, E. 2006, in Astronomical Data Analysis Software and Systems XV, Vol. 351, 112

(ref: Bertin2010) Bertin, E. 2010, SWarp: Resampling and Co-adding FITS Images Together, Astrophysics Source Code Library, record ascl:1010.068

(ref: Bertin2011) Bertin, E. 2011, in Astronomical Society of the Pacific Conference Series, Vol. 442, Astronomical Data Analysis Software and Systems XX, ed. I. N. Evans, A. Accomazzi, D. J. Mink, & A. H. Rots, 435

(ref: Bertin1996) Bertin, E. & Arnouts, S. 1996, A&AS, 117, 393

(ref: Bielby2011) Bielby, R. M., Shanks, T., Weilbacher, P. M., et al. 2011, MNRAS, 414, 2

(ref: Bielby2019) Bielby, R. M., Stott, J. P., Cullen, F., et al. 2019, MNRAS, 486, 21

(ref: Bond1996) Bond, J. R., Kofman, L., & Pogosyan, D. 1996, Nature, 380, 603

(ref: Boquien2019) Boquien, M., Burgarella, D., Roehlly, Y., et al. 2019, A&A, 622, A103

(ref: Borisova2016) Borisova, E., Cantalupo, S., Lilly, S. J., et al. 2016, ApJ, 831, 39

(ref: Bradley2023) Bradley, L., Sipőcz, B., Robitaille, T., et al. 2023, astropy/photutils: 1.10.0

(ref: Brinchmann2004) Brinchmann, J., Charlot, S., White, S. D. M., et al. 2004, MNRAS, 351, 1151

(ref: BC03) Bruzual, G. & Charlot, S. 2003, MNRAS, 344, 1000

(ref: Burgarella2005) Burgarella, D., Buat, V., & Iglesias-Páramo, J. 2005, MNRAS, 360, 1413

(ref: Byler2018) Byler, N., Dalcanton, J. J., Conroy, C., et al. 2018, ApJ, 863, 14

(ref: Calvi2013) Calvi, R., Poggianti, B. M., Vulcani, B., & Fasano, G. 2013, MNRAS, 432, 3141

(ref: Calzetti2000) Calzetti, D., Armus, L., Bohlin, R. C., et al. 2000, ApJ, 533, 682

(ref: Cantalupo2021_JWST) Cantalupo, S., Fossati, M., Fumagalli, M., et al. 2021, Unraveling the knots of gaseous Cosmic Web filaments at z 3 through H-alpha emission observations, JWST Proposal. Cycle 1, ID. #1835

(ref: Cantalupo2019) Cantalupo, S., Pezzulli, G., Lilly, S. J., et al. 2019, MNRAS, 483, 5188

(ref: Casali2006) Casali, M., Pirard, J.-F., Kissler-Patig, M., et al. 2006, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 6269, Ground-based and Airborne Instrumentation for Astronomy, ed. I. S. McLean & M. Iye, 62690W

(ref: Casey2015) Casey, C. M., Cooray, A., Capak, P., et al. 2015, ApJL, 808, L33

(ref: Cen2000) Cen, R. & Ostriker, J. P. 2000, ApJ, 538, 83

(ref: Chabrier2003) Chabrier, G. 2003, PASP, 115, 763

(ref: Chapman2009) Chapman, S. C., Blain, A., Ibata, R., et al. 2009, ApJ, 691, 560

(ref: Chartab2020) Chartab, N., Mobasher, B., Darvish, B., et al. 2020, ApJ, 890, 7

(ref: Chiang2013) Chiang, Y.-K., Overzier, R., & Gebhardt, K. 2013, ApJ, 779, 127

(ref: Chiang2017) Chiang, Y.-K., Overzier, R. A., Gebhardt, K., & Henriques, B. 2017, ApJL, 844, L23

(ref: Conroy2013) Conroy, C. 2013, ARA&A, 51, 393

(ref: Contini2016) Contini, E., De Lucia, G., Hatch, N., Borgani, S., & Kang, X. 2016, MNRAS, 456, 1924

(ref: Cooke2014) Cooke, E. A., Hatch, N. A., Muldrew, S. I., Rigby, E. E., & Kurk, J. D. 2014, MNRAS, 440, 3262

(ref: Cucciati2018) Cucciati, O., Lemaux, B. C., Zamorani, G., et al. 2018, A&A, 619, A49

(ref: Daddi2007) Daddi, E., Dickinson, M., Morrison, G., et al. 2007, ApJ, 670, 156

(ref: dAmato2020) D’Amato, Q., Gilli, R., Prandoni, I., et al. 2020, A&A, 641, L6

(ref: Darvish2016) Darvish, B., Mobasher, B., Sobral, D., et al. 2016, ApJ, 825, 113

(ref: Davidzon2013) Davidzon, I., Bolzonella, M., Coupon, J., et al. 2013, A&A, 558, A23

(ref: DeBeer2023) de Beer, S., Cantalupo, S., Travascio, A., et al. 2023, MNRAS, 526, 1850

(ref: deLapparent1986) de Lapparent, V., Geller, M. J., & Huchra, J. P. 1986, ApJL, 302, L1

(ref: DiMascolo2023) Di Mascolo, L., Saro, A., Mroczkowski, T., et al. 2023, Nature, 615, 809

(ref: Elbaz2007) Elbaz, D., Daddi, E., Le Borgne, D., et al. 2007, A&A, 468, 33

(ref: EsoRex2015) ESO CPL Development Team. 2015, EsoRex: ESO Recipe Execution Tool, Astrophysics Source Code Library, record ascl:1504.003

(ref: Falder2011) Falder, J. T., Stevens, J. A., Jarvis, M. J., et al. 2011, ApJ, 735, 123

(ref: Ford1998) Ford, H. C., Bartko, F., Bely, P. Y., et al. 1998, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 3356, Space Telescopes and Instruments V, ed. P. Y. Bely & J. B. Breckinridge, 234–248

(ref: Forrest2024) Forrest, B., Lemaux, B. C., Shah, E. A., et al. 2024, arXiv e-prints, arXiv:2405.18491

(ref: Fossati2019SED) Fossati, M., Fumagalli, M., Lofthouse, E. K., et al. 2019, MNRAS, 490, 1451

(ref: Fossati2021) Fossati, M., Fumagalli, M., Lofthouse, E. K., et al. 2021, MNRAS, 503, 3044

(ref: Fossati2018SED) Fossati, M., Mendel, J. T., Boselli, A., et al. 2018, A&A, 614, A57

(ref: Fossati2017) Fossati, M., Wilman, D. J., Mendel, J. T., et al. 2017, ApJ, 835, 153

(ref: Fritz2006) Fritz, J., Franceschini, A., & Hatziminaoglou, E. 2006, MNRAS, 366, 767

(ref: Gaia2016) Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al. 2016, A&A, 595, A1

(ref: Gaia2023) Gaia Collaboration, Vallenari, A., Brown, A. G. A., et al. 2023, A&A, 674, A1

(ref: Galbiati2024) Galbiati, M., Dutta, R., Fumagalli, M., Fossati, M., & Cantalupo, S. 2024, A&A, 690, A7

(ref: Galbiati2023) Galbiati, M., Fumagalli, M., Fossati, M., et al. 2023, MNRAS, 524, 3474

(ref: GarciaVergara2021) Garcia-Vergara, C. 2021, in Galaxy Cluster Formation II, 49

(ref: Garcia_Vergara2017) Garcı́a-Vergara, C., Hennawi, J. F., Barrientos, L. F., & Rix, H.-W. 2017, ApJ, 848, 7

(ref: Gatica2024) Gatica, C., Demarco, R., Dole, H., et al. 2024, MNRAS, 527, 3006

(ref: Geller1989) Geller, M. J. & Huchra, J. P. 1989, Science, 246, 897

(ref: Ginolfi2022) Ginolfi, M., Piconcelli, E., Zappacosta, L., et al. 2022, Nature Communications, 13, 4574

(ref: Gonzaga2012) Gonzaga, S., Hack, W., Fruchter, A., & Mack, J. 2012, The DrizzlePac Handbook

(ref: Greenslade2018) Greenslade, J., Clements, D. L., Cheng, T., et al. 2018, MNRAS, 476, 3336

(ref: Gu2018_int) Gu, M., Conroy, C., & Brammer, G. 2018, ApJL, 862, L18

(ref: Numpy2020) Harris, C. R., Millman, K. J., van der Walt, S. J., et al. 2020, Nature, 585, 357

(ref: Hatch2014) Hatch, N. A., Wylezalek, D., Kurk, J. D., et al. 2014, MNRAS, 445, 280

(ref: Hayashi2012) Hayashi, M., Kodama, T., Tadaki, K.-i., Koyama, Y., & Tanaka, I. 2012, ApJ, 757, 15

(ref: Hayashino2004) Hayashino, T., Matsuda, Y., Tamura, H., et al. 2004, AJ, 128, 2073

(ref: Hennawi2015) Hennawi, J. F., Prochaska, J. X., Cantalupo, S., & Arrigoni-Battaia, F. 2015, Science, 348, 779

(ref: Hinton2016) Hinton, S. R., Davis, T. M., Lidman, C., Glazebrook, K., & Lewis, G. F. 2016, Astronomy and Computing, 15, 61

(ref: Hoffmann2021) Hoffmann, S. L., Mack, J., Avila, R., et al. 2021, in American Astronomical Society Meeting Abstracts, Vol. 238, American Astronomical Society Meeting Abstracts, 216.02

(ref: Huang2022) Huang, Y., Lee, K.-S., Cucciati, O., et al. 2022, ApJ, 941, 134

(ref: Matpltolib2007) Hunter, J. D. 2007, Computing in Science and Engineering, 9, 90

(ref: Husband2013) Husband, K., Bremer, M. N., Stanway, E. R., et al. 2013, MNRAS, 432, 2869

(ref: Ilbert2013) Ilbert, O., McCracken, H. J., Le Fèvre, O., et al. 2013, A&A, 556, A55

(ref: Inoue2011) Inoue, A. K. 2011, MNRAS, 415, 2920

(ref: Ito2020) Ito, K., Kashikawa, N., Toshikawa, J., et al. 2020, ApJ, 899, 5

(ref: Izzo2010) Izzo, C., de Bilbao, L., Larsen, J., et al. 2010, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 7737, Observatory Operations: Strategies, Processes, and Systems III, ed. D. R. Silva, A. B. Peck, & B. T. Soifer, 773729

(ref: Jones2014) Jones, S. F., Blain, A. W., Stern, D., et al. 2014, MNRAS, 443, 146

(ref: Kashikawa2007) Kashikawa, N., Kitayama, T., Doi, M., et al. 2007, ApJ, 663, 765

(ref: Kashino2023) Kashino, D., Lilly, S. J., Matthee, J., et al. 2023, ApJ, 950, 66

(ref: Kikuta2019) Kikuta, S., Matsuda, Y., Cen, R., et al. 2019, PASJ, 71, L2

(ref: Kim2009) Kim, S., Stiavelli, M., Trenti, M., et al. 2009, ApJ, 695, 809

(ref: Kissler-Patig2008) Kissler-Patig, M., Pirard, J. F., Casali, M., et al. 2008, A&A, 491, 941

(ref: Kodama2007) Kodama, T., Tanaka, I., Kajisawa, M., et al. 2007, MNRAS, 377, 1717

(ref: Koprowski2024) Koprowski, M. P., Wijesekera, J. V., Dunlop, J. S., et al. 2024, arXiv e-prints, arXiv:2403.06575

(ref: Koyama2013a) Koyama, Y., Kodama, T., Tadaki, K.-i., et al. 2013a, MNRAS, 428, 1551

(ref: Koyama2013b) Koyama, Y., Smail, I., Kurk, J., et al. 2013b, MNRAS, 434, 423

(ref: Kubo2013) Kubo, M., Uchimoto, Y. K., Yamada, T., et al. 2013, ApJ, 778, 170

(ref: Kuiper2010) Kuiper, E., Hatch, N. A., Röttgering, H. J. A., et al. 2010, MNRAS, 405, 969

(ref: Kurk2004) Kurk, J. D., Pentericci, L., Röttgering, H. J. A., & Miley, G. K. 2004, A&A, 428, 793

(ref: Kurk2000) Kurk, J. D., Röttgering, H. J. A., Pentericci, L., et al. 2000, A&A, 358, L1

(ref: Lacaille2019) Lacaille, K. M., Chapman, S. C., Smail, I., et al. 2019, MNRAS, 488, 1790

(ref: Laigle2016) Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24

(ref: Lee2018) Lee, K.-G., Krolewski, A., White, M., et al. 2018, ApJS, 237, 31

(ref: Lee2014) Lee, K.-S., Dey, A., Hong, S., et al. 2014, ApJ, 796, 126

(ref: Lehmer2009) Lehmer, B. D., Alexander, D. M., Geach, J. E., et al. 2009, ApJ, 691, 687

(ref: Lemaux2022) Lemaux, B. C., Cucciati, O., Le Fèvre, O., et al. 2022, A&A, 662, A33

(ref: Lemaux2019) Lemaux, B. C., Tomczak, A. R., Lubin, L. M., et al. 2019, MNRAS, 490, 1231

(ref: Libeskind2018) Libeskind, N. I., van de Weygaert, R., Cautun, M., et al. 2018, MNRAS, 473, 1195

(ref: Lofthouse2020) Lofthouse, E. K., Fumagalli, M., Fossati, M., et al. 2020, MNRAS, 491, 2057

(ref: Lovell2018) Lovell, C. C., Thomas, P. A., & Wilkins, S. M. 2018, MNRAS, 474, 4612

(ref: Luo2022) Luo, Y., Fan, L., Zou, H., et al. 2022, ApJ, 935, 80

(ref: Marino2018) Marino, R. A., Cantalupo, S., Lilly, S. J., et al. 2018, ApJ, 859, 53

(ref: McGee2009) McGee, S. L., Balogh, M. L., Bower, R. G., Font, A. S., & McCarthy, I. G. 2009, MNRAS, 400, 937

(ref: McNab2021) McNab, K., Balogh, M. L., van der Burg, R. F. J., et al. 2021, MNRAS, 508, 157

(ref: Mei2023) Mei, S., Hatch, N. A., Amodeo, S., et al. 2023, A&A, 670, A58

(ref: Mignoli2020) Mignoli, M., Gilli, R., Decarli, R., et al. 2020, A&A, 642, L1

(ref: Miller2018) Miller, T. B., Chapman, S. C., Aravena, M., et al. 2018, Nature, 556, 469

(ref: Moustakas2013) Moustakas, J., Coil, A. L., Aird, J., et al. 2013, ApJ, 767, 50

(ref: Muldrew2015) Muldrew, S. I., Hatch, N. A., & Cooke, E. A. 2015, MNRAS, 452, 2528

(ref: Muzahid2020) Muzahid, S., Schaye, J., Marino, R. A., et al. 2020, MNRAS, 496, 1013

(ref: Newman2020) Newman, A. B., Rudie, G. C., Blanc, G. A., et al. 2020, ApJ, 891, 147

(ref: Newman2022) Newman, A. B., Rudie, G. C., Blanc, G. A., et al. 2022, Nature, 606, 475

(ref: Noeske2007) Noeske, K. G., Faber, S. M., Weiner, B. J., et al. 2007, ApJL, 660, L47

(ref: Noll2009) Noll, S., Burgarella, D., Giovannoli, E., et al. 2009, A&A, 507, 1793

(ref: Old2020) Old, L. J., Balogh, M. L., van der Burg, R. F. J., et al. 2020, MNRAS, 493, 5987

(ref: Orsi2016) Orsi, Á. A., Fanidakis, N., Lacey, C. G., & Baugh, C. M. 2016, MNRAS, 456, 3827

(ref: Oteo2018) Oteo, I., Ivison, R. J., Dunne, L., et al. 2018, ApJ, 856, 72

(ref: Overzier2016) Overzier, R. A. 2016, A&ARv, 24, 14

(ref: Overzier2008) Overzier, R. A., Bouwens, R. J., Cross, N. J. G., et al. 2008, ApJ, 673, 143

(ref: Pacifici2023) Pacifici, C., Iyer, K. G., Mobasher, B., et al. 2023, ApJ, 944, 141

(ref: Peng2010) Peng, Y.-j., Lilly, S. J., Kovač, K., et al. 2010, ApJ, 721, 193

(ref: Penney2019) Penney, J. I., Blain, A. W., Wylezalek, D., et al. 2019, MNRAS, 483, 514

(ref: Pensabene2024) Pensabene, A., Cantalupo, S., Cicone, C., et al. 2024, A&A, 684, A119

(ref: Pentericci2000) Pentericci, L., Kurk, J. D., Röttgering, H. J. A., et al. 2000, A&A, 361, L25

(ref: Pentericci1997) Pentericci, L., Roettgering, H. J. A., Miley, G. K., Carilli, C. L., & McCarthy, P. 1997, A&A, 326, 580

(ref: PerezMartinez2023) Pérez-Martı́nez, J. M., Dannerbauer, H., Kodama, T., et al. 2023, MNRAS, 518, 1707

(ref: Pirard2004) Pirard, J.-F., Kissler-Patig, M., Moorwood, A., et al. 2004, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 5492, Ground-based Instrumentation for Astronomy, ed. A. F. M. Moorwood & M. Iye, 1763–1772

(ref: Planck2016) Planck Collaboration, Adam, R., Ade, P. A. R., et al. 2016, A&A, 594, A1

(ref: Popesso2022) Popesso, P., Concas, A., Cresci, G., et al. 2023, MNRAS, 519, 1526

(ref: Pozzetti2010) Pozzetti, L., Bolzonella, M., Zucca, E., et al. 2010, A&A, 523, A13

(ref: Priddey2008) Priddey, R. S., Ivison, R. J., & Isaak, K. G. 2008, MNRAS, 383, 289

(ref: Raichoor2011) Raichoor, A., Mei, S., Nakata, F., et al. 2011, ApJ, 732, 12

(ref: Reddy2009) Reddy, N. A. & Steidel, C. C. 2009, ApJ, 692, 778

(ref: Reddy2008) Reddy, N. A., Steidel, C. C., Pettini, M., et al. 2008, ApJS, 175, 48

(ref: Riccio2023) Riccio, G., Yang, G., Małek, K., et al. 2023, A&A, 678, A164

(ref: Rigby2014) Rigby, E. E., Hatch, N. A., Röttgering, H. J. A., et al. 2014, MNRAS, 437, 1882

(ref: Rigby2023) Rigby, J., Perrin, M., McElwain, M., et al. 2023, PASP, 135, 048001

(ref: Roettgering1994) Roettgering, H. J. A., Lacy, M., Miley, G. K., Chambers, K. C., & Saunders, R. 1994, A&AS, 108, 79

(ref: Rudie2013) Rudie, G. C., Steidel, C. C., Shapley, A. E., & Pettini, M. 2013, ApJ, 769, 146

(ref: Salim2007) Salim, S., Rich, R. M., Charlot, S., et al. 2007, ApJS, 173, 267

(ref: Salpeter1955) Salpeter, E. E. 1955, ApJ, 121, 161

(ref: Sanchez2022) Sánchez, S. F., Barrera-Ballesteros, J. K., Lacerda, E., et al. 2022, ApJS, 262, 36

(ref: Shapley2003) Shapley, A. E., Steidel, C. C., Pettini, M., & Adelberger, K. L. 2003, ApJ, 588, 65

(ref: Shi2019b) Shi, K., Huang, Y., Lee, K.-S., et al. 2019a, ApJ, 879, 9

(ref: Shi2019a) Shi, K., Lee, K.-S., Dey, A., et al. 2019b, ApJ, 871, 83

(ref: Shi2020) Shi, K., Toshikawa, J., Cai, Z., Lee, K.-S., & Fang, T. 2020, ApJ, 899, 79

(ref: Shimakawa2017) Shimakawa, R., Kodama, T., Hayashi, M., et al. 2018a, MNRAS, 473, 1977

(ref: Shimakawa2018) Shimakawa, R., Koyama, Y., Röttgering, H. J. A., et al. 2018b, MNRAS, 481, 5630

(ref: Siebenmorgen2011) Siebenmorgen, R., Carraro, G., Valenti, E., et al. 2011, The Messenger, 144, 9

(ref: Skrutskie2006) Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ, 131, 1163

(ref: Speagle2014) Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS, 214, 15

(ref: Spitler2012) Spitler, L. R., Labbé, I., Glazebrook, K., et al. 2012, ApJL, 748, L21

(ref: BPASS2018) Stanway, E. R. & Eldridge, J. J. 2018, MNRAS, 479, 75

(ref: Steidel1998) Steidel, C. C., Adelberger, K. L., Dickinson, M., et al. 1998, ApJ, 492, 428

(ref: Steidel2005) Steidel, C. C., Adelberger, K. L., Shapley, A. E., et al. 2005, ApJ, 626, 44

(ref: Steidel2000) Steidel, C. C., Adelberger, K. L., Shapley, A. E., et al. 2000, ApJ, 532, 170

(ref: Steidel2003) Steidel, C. C., Adelberger, K. L., Shapley, A. E., et al. 2003, ApJ, 592, 728

(ref: Steidel2011) Steidel, C. C., Bogosavljević, M., Shapley, A. E., et al. 2011, ApJ, 736, 160

(ref: Steidel2018) Steidel, C. C., Bogosavljević, M., Shapley, A. E., et al. 2018, ApJ, 869, 123

(ref: Steidel1996) Steidel, C. C., Giavalisco, M., Pettini, M., Dickinson, M., & Adelberger, K. L. 1996, ApJL, 462, L17

(ref: Sunyaev1972) Sunyaev, R. A. & Zeldovich, Y. B. 1972, A&A, 20, 189

(ref: Taamoli2023) Taamoli, S., Mobasher, B., Chartab, N., et al. 2024, ApJ, 966, 18

(ref: Tanaka2011) Tanaka, I., De Breuck, C., Kurk, J. D., et al. 2011, PASJ, 63, 415

(ref: Thomas2005) Thomas, D., Maraston, C., Bender, R., & Mendes de Oliveira, C. 2005, ApJ, 621, 673

(ref: Tomczak2017) Tomczak, A. R., Lemaux, B. C., Lubin, L. M., et al. 2017, MNRAS, 472, 3512

(ref: Tomczak2019) Tomczak, A. R., Lemaux, B. C., Lubin, L. M., et al. 2019, MNRAS, 484, 4695

(ref: Topping2016) Topping, M. W., Shapley, A. E., & Steidel, C. C. 2016, ApJL, 824, L11

(ref: Toshikawa2020) Toshikawa, J., Malkan, M. A., Kashikawa, N., et al. 2020, ApJ, 888, 89

(ref: Toshikawa2024) Toshikawa, J., Wuyts, S., Kashikawa, N., et al. 2024, MNRAS, 527, 6276

(ref: Tozzi2022) Tozzi, P., Pentericci, L., Gilli, R., et al. 2022, A&A, 662, A54

(ref: Trainor2012) Trainor, R. F. & Steidel, C. C. 2012, ApJ, 752, 39

(ref: Umehata2019) Umehata, H., Fumagalli, M., Smail, I., et al. 2019, Science, 366, 97

(ref: Utsumi2010) Utsumi, Y., Goto, T., Kashikawa, N., et al. 2010, ApJ, 721, 1680

(ref: vdBurg2010) van der Burg, R. F. J., Hildebrandt, H., & Erben, T. 2010, A&A, 523, A74

(ref: vdBurg2020) van der Burg, R. F. J., Rudnick, G., Balogh, M. L., et al. 2020, A&A, 638, A112

(ref: Venemans2007) Venemans, B. P., Röttgering, H. J. A., Miley, G. K., et al. 2007, A&A, 461, 823

(ref: SciPy2020) Virtanen, P., Gommers, R., Oliphant, T. E., et al. 2020, Nature Methods, 17, 261

(ref: Wang2024) Wang, G. C. P., Chapman, S. C., Sulzenauer, N., et al. 2024a, arXiv e-prints, arXiv:2406.16637

(ref: Wang2024_bigwheel) Wang, W., Cantalupo, S., Pensabene, A., et al. 2024b, arXiv e-prints, arXiv:2409.17956

(ref: Weaver2023) Weaver, J. R., Davidzon, I., Toft, S., et al. 2023, A&A, 677, A184

(ref: Weilbacher2014) Weilbacher, P. M., Streicher, O., Urrutia, T., et al. 2014, in Astronomical Society of the Pacific Conference Series, Vol. 485, Astronomical Data Analysis Software and Systems XXIII, ed. N. Manset & P. Forshay, 451

(ref: Weisskopf2000) Weisskopf, M. C., Tananbaum, H. D., Van Speybroeck, L. P., & O’Dell, S. L. 2000, in Society of Photo-Optical Instrumentation Engineers (SPIE) Conference Series, Vol. 4012, X-Ray Optics, Instruments, and Missions III, ed. J. E. Truemper & B. Aschenbach, 2–16

(ref: Wylezalek2013) Wylezalek, D., Galametz, A., Stern, D., et al. 2013, ApJ, 769, 79

(ref: Yang2022_cigale) Yang, G., Boquien, M., Brandt, W. N., et al. 2022, ApJ, 927, 192

(ref: Yang2020) Yang, G., Boquien, M., Buat, V., et al. 2020, MNRAS, 491, 740

(ref: Zewdie2023) Zewdie, D., Assef, R. J., Mazzucchelli, C., et al. 2023, A&A, 677, A54

# Custom G-band and UGR selection

![](UGR_selection.pdf)

As described in Section [3.1](#sec:sel_UBR), we measured $U-B$ and $B-R$ colors to select Lyman break galaxies within the redshift range $z\approx3-3.5$ across a much larger FoV compared to that of the MUSE mosaic. In order to be able to compare our results with other sample in the literature, it is essential to keep the selection function between different studies as similar as possible. Taking advantage of the MUSE data, we restrict to the $4\times4\rm\,cMpc^2$ FoV of the MUSE mosaic and identify the LBG candidates using a $UGR$ (that is, based on $U-G$ and $G-R$ colors) color selection (cite: Steidel1996; Steidel2003). To this end, we construct a custom-made G-band image covering the FoV of the MUSE mosaic. We therefore combine the B-band image taken with FORS2 with a top-hat medium-band image built out of the MUSE data, producing a custom G-band image with effective wavelength $\lambda_{\rm eff}=4727.3\,$Å. The MUSE top-hat filter spans a wavelength range from $4920\,$Å, corresponding to a transmission of $5\%$ for the FORS2 B$_{\rm High}$ filter, to $5510\,$Å, which corresponds to the maximum wavelength of the FORS2 $\rm G_{\rm High}$ filter.

To calibrate the color selection, we used the same SPS models described in Section [3.1](#sec:sel_UBR) convolved for the transmission functions of the FORS2 filters and of the custom G-band. As a result, the selection criterion reads as following:

(i) $U>U_{\rm BKG}^{3\sigma}$

(ii) $U-G>1.22$

(iii) $G-R<0.88\times(U-G)-0.81$

(iv) $0.21<G-R<1.75$

Finally, the results of this alternative color selection are shown in Figure [3](#fig:sample_LBG), while the success rate for the sample of spectroscopically-selected galaxies clustered around the quasar is reported in Table [5](#tab:color_plus_MUSE). In details, within the $\approx4\times4\rm\,cMpc^2$ FoV of the MUSE mosaic, we are able to select 33 candidate Lyman break galaxies at $z\approx3.0-3.5$, 23 of them also selected by the $UBR$ criterion.

# The UV luminosity function of LBGs

![](Cumulative_LF_wUBR_Panel2.pdf)

We here estimate the overdensity of $UBR$ color-selected LBGs by applying the same method described in Section [4.2](#sec:result_LF) and thus deriving the rest-frame UV cumulative luminosity functions in the FoV of MUSE and FORS2 (see Figure [12](#fig:LF_LBGs)). These are corrected for the completeness of the R-band, that is used for the detection of the galaxies (see Figure [1](#fig:data_FORS)). The highest normalization is observed for the LBGs with spectroscopic redshift within $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ around the quasar in the FoV of the MUSE mosaic. This sample mimics a selection based on photometry and a spectroscopic follow-up, but fails to select massive and dusty galaxies with $\log(M_\star/M_\odot)\gtrsim10$ and $A_{\rm v}\gtrsim0.5$ (as reported in Section [3.1](#sec:sel_UBR)). In this case, the overdensity estimated relative to the completeness corrected luminosity function from (cite: Reddy2009), is $\rho/\bar{\rho}=24\pm14$ at $M_{\rm R}\leq-19.25\rm\,mag$ and thus consistent within the uncertainties with the results we obtained for the main spectroscopic sample. An overdensity $\rho/\bar{\rho}=3\pm1$ is observed even when considering a $\times6$ larger volume in redshift. However, the luminosity function becomes fully consistent with (cite: Reddy2009) once computed for all the LBGs detected across the $\times36$ larger area sampled by FORS2, suggesting that the overdensity is diluted in such a large volume. This provides the evidence that the 3D distribution of the star-forming galaxies is significantly peaked not only along the line of sight but also spatially around the quasar.

# Alignment of the LBGs with the large-scale overdensity

![](Alignment_only_FullSample.pdf)

Assuming the LBGs span the entire redshift range $3.0<z<3.5$ (see Section [3.1](#sec:sel_UBR)), we measured the local co-moving galaxy density by using the $N_{th}$ neighbor estimator with the same formalism presented by (cite: Shimakawa2017). We choose N=5. Although we expect this method not to be efficient at the edges of the FoV, these galaxies should not affect significantly the statistics and are mostly limited to $R\gtrsim11\rm\,cMpc$. Furthermore, we validate the choice of the estimator by comparing the $N_{th}$ neighbor results to the co-moving density obtained by the scale independent the Voronoi Tessellation, described in Section [4.6](#sec:over_profiles). We observe that the 3rd neighbor systematically over-estimate the density by a factor of $\approx1.5$ compared to the Voronoi Tessellation, but the two methods turn out to be consistent for $N\geq5$. The local density is finally converted into a co-moving overdensity $\rho/\bar{\rho}$ against the expected density of galaxies in a blank field (see Section [4.2](#sec:result_LF)).

We then measured the orientation of each galaxy with respect to the North-South direction and the central quasar. In bins of co-moving overdensity defined to contain roughly the same number of galaxies, we measured the fraction of LBGs oriented along the North-South direction around the quasar as a function of the environment (see Figure [13](#fig:alignement)). We require a galaxy for being aligned to the North-South direction to be offset by an angle within $\pm\ang{25}$ (black, corresponding to $\ang{0}-\ang{25}$ or $\ang{155}-\ang{180}$) or $\pm\ang{45}$ (magenta, corresponding to $\ang{0}-\ang{45}$ or $\ang{135}-\ang{180}$), chosen so that $\gtrsim40\%$ and $100\%$, respectively, of the MUSE spectroscopic sample is found to be aligned.

Figure [13](#fig:alignement) shows that the fraction of LBGs oriented along the North-South direction steeply increases with the local co-moving density. In other words, the regions that overdense in LBGs are not sparsely distributed across the large area we surveyed, but instead do preferentially follow the same orientation as the spectroscopically selected galaxies within $4\times4\rm\,cMpc^2$ and $\Delta\varv=\pm1000\rm\,km\,s^{-1}$ from the central quasar. To further support this result, we reproduce the expectations for a sample of randomly-distributed galaxies by injecting the same number of LBGs of the real data in random positions across the FoV. We repeat the injection $1,000$ times and show, despite the large uncertainties derived from the 16th and 84th percentile of the bootstrap distribution, that the fraction of aligned galaxies is flat as a function of the co-moving galaxy overdensity. To support this argument on a more statistical ground, we performed a Spearman’s rank correlation test on both the data and the bootstrap results. For the data we found a positive correlation that is significant well above $2\sigma$, as given by $\rho_{\rm spearman}=0.93$, $p-$value$=0.003$ for the threshold $\pm\ang{45}$, and $\rho_{\rm spearman}=0.97$, $p-$value$=0.0005$ for $\pm\ang{25}$. On the other hand, for the random-like samples we find $\rho_{\rm spearman}=0.01$, $p-$value$=0.78$ for the threshold $\pm\ang{45}$, and $\rho_{\rm spearman}=0.02$, $p-$value$=0.86$ for $\pm\ang{25}$. Altogether, this analysis provides a strong evidence for the distribution of massive LBGs to be preferentially aligned along the direction of the overdensity of star-forming galaxies observed in a much smaller volume around the central quasar and thus further supports a picture in which the gaseous structure embedding these galaxies extends for several tens of cMpc.

# MQN01 clustering compared to the MAGG survey

The clustering analysis presented in Section [4.3](#sec:radial_overdensity) and discussed in Section [5.1](#sec:disc_overdensity) provides hints that the MQN01 quasar can possibly be associated to a halo that is much larger compared to those of average quasars at similar redshifts. To further support this conclusion, we here give the details of the quasar-galaxy cross-correlation function we derived for continuum-selected galaxies clustered around the 28 quasars included in the MAGG survey. Such galaxies have been identified by (cite: Lofthouse2020) running sextractor (cite: Bertin1996) on the MUSE white-light images obtained for each of the 28 cubes centered on a $3.2\lesssim z\lesssim4.5$ quasar (median $z\approx3.7$). This software outputs a segmentation map that is used to extract the spectra of all the sources, which are finally inspected using Marz (cite: Hinton2016) to assign a reliable spectroscopic redshift. As a final step, to produce a sample with a selection function that is as similar as possible to that of the MQN01 galaxies, we selected 20 galaxies with R-band magnitude $m_{\rm R}\lesssim26.5\rm\,mag$, high-quality spectroscopic redshift, and found within a line-of-sight separation $\lvert\Delta\varv\rvert\le1500\rm\,km\,s^{-1}$ from the central quasar of the respective field. We finally derived the projected quasar-galaxy cross-correlation function by using the same procedure described in Section [4.3](#sec:radial_overdensity). The results are shown in Figure [14](#fig:clustering_magg). We measured a cross-correlation length $r_0=(3.8\pm0.8)\,h^{-1}{\rm cMpc}$ for fixed $\gamma=1.5$. Although the different sizes of the FoV, as well as the different selection and average redshift of the samples, make it difficult to compare this result with TS12, the fact that the cross-correlation in MAGG is $\approx6$ times smaller than that of MQN01 remains an important indicator of the rare and massive nature of the quasar host halo, as discussed in Section [5.1](#sec:disc_overdensity).

![](MAGG_xCorr.pdf)

# Results from SED fitting

We provide in this section further details and results on the galaxies’ SED fitting process. The parameters we set in the initial file of CIGALE are listed below in Table [\[tab:CIGALE_AGN\]](#tab:CIGALE_AGN), while Table [\[tab:SED_table\]](#tab:SED_table) shows the properties estimated for each of the 21 galaxies included in the main spectroscopic sample, as well as their redshift and results of the color-selections employed to identify the LBGs. For the sources detected in X-Ray, the derived SFR and stellar mass may be significantly affected by the contribution of the AGN emission to the total SED. We have thus investigated the morphology of these sources in the JWST/NIRCam data and verified that none of them shows compact bright emission in the center, suggesting that the contribution of the AGN emission does not outshine that of the stellar continuum. Furthermore, according to the best-fit model obtained by running CIGALE, the contribution of the AGN emission to the total galaxies’ SED is, in terms of flux density, $\gtrsim1\rm\,dex$ smaller compared to the stellar continuum. Based on these considerations, we conclude that the properties we derived for these sources are reliable and are not dominated by presence of an AGN.

We also tested the results of the SED modeling to be independent of the code we used. To this end, we fit the observed galaxies’ photometry using the Monte Carlo Spectro-Photometric Fitter (`MC-SPF`, (cite: Fossati2018SED; Fossati2019SED)). The grid of stellar spectra is built upon the updated version[^8] of the (cite: BC03) high-resolution models at solar metallicity assuming an exponentially declining star formation history and the (cite: Chabrier2003) initial mass function. A grid of nebular emission lines models from (cite: Byler2018) is scaled to the number of Lyman continuum photons from the stellar models, converted into flux at the redshift of the galaxies and then added to templates. To model the dust attenuation, we assume the double attenuation law from (cite: Calzetti2000), which includes extra extinction of the young stars compared to those older than 10 Myr. Comparing the two SED fitting codes, the median difference we observe in the galaxies’ properties is $0.048\pm0.050\rm\,dex$ for the stellar mass and $0.054\pm0.055\rm\,dex$ for the star formation rate, which is in both the cases substantially smaller than other uncertainties associated to these parameters.

+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Parameter                                                                                           | Value                                       |   |
+:====================================================================================================+:===========================================:+:=:+
| Exponential or Delayed star formation History                                                                                                     |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| e-folding time of the main stellar population model (Myr)                                           | 50-15000 in step $\Delta\tau=50\rm\,Myr$    |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Age of the main stellar population (Myr)                                                            | 25-2000 in step $\Delta{\rm age}=5\rm\,Myr$ |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Stellar population models: (cite: BC03)                                                                                                           |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Initial mass function                                                                               | (cite: Chabrier2003)                        |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Metallicities (in separate runs)                                                                    | 0.008, 0.004, 0.020                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Age of the separation between the young and the old star population (Myr)                           | 10                                          |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Dust attenuation law: (cite: Calzetti2000)                                                                                                        |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| E(B-V)l: color excess of the nebular lines                                                          | 0.0-0.75 in step $\rm\Delta E(B-V)l=0.015$  |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| E(B-V)f: reduction factor to compute the E(B-V)                                                     |                                             |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| for the stellar continuum attenuation                                                               | 0.44                                        |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Nebular Emission: (cite: Inoue2011)                                                                                                               |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Ionization parameter                                                                                | -2.0                                        |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Gas metallicity (set to be same as the stellar metallicity)                                         | 0.008, 0.004, 0.020                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Fraction of Lyman continuum photons escaping the galaxy                                             | 0.0                                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| AGN emission$^{(a)}$: (cite: Fritz2006)                                                                                                           |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| AGN fraction: contribution of the AGN to the total $L_{\rm IR}$                                     | 0.0, 0.01, 0.1, 0.2, 0.3,                   |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
|                                                                                                     | 0.4, 0.5, 0.6, 0.7, 0.8, 0.9                |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Opening angle of the dust torus                                                                     | 10, 30, 60                                  |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Angle between AGN axis and line of sight                                                            | 0.001, 89.9                                 |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Optical depth at 9.7                                                                                | 1.0, 6.0                                    |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| X-ray emission$^{(a)}$: (cite: Yang2022_cigale)                                                                                                   |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Photon index of the AGN intrinsic X-ray spectrum                                                    | 1.8                                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Power-law slope connecting $L_{\nu}$ at rest-frame 2500Å and 2keV ($\alpha_{\rm ox}$)               | -1.9, -1.7, -1.5, -1.3, -1.1, -0.9          |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Maximum allowed deviation of $\alpha_{\rm ox}$ from the empirical $\alpha_{\rm ox}-L_{\nu}$ (2500Å) | 0.2                                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Deviation from the expected LMXB scaling relation ($\delta_{\rm LMXB}$)                             | 0.0                                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+
| Deviation from the expected HMXB scaling relation ($\delta_{\rm HMXB}$)                             | 0.0                                         |   |
+-----------------------------------------------------------------------------------------------------+---------------------------------------------+---+

Table notes:

| Coordinates | spec-z | $\log{[\rm SFR/\rm (M_\odot Yr^{-1})]}$ | $\log{[\rm sSFR/\rm Yr^{-1}]}$ | $\log{[M_\star/M_\odot]}$ | $A_{\rm V}$ | AGN | UBR | UGR |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 00:41:35.39 -49:37:19.41 | 3.254 | 1.84$\pm$0.30 | -8.62$\pm$0.36 | 10.46$\pm$0.20 | 0.64$\pm$0.03 |  |  |  |
| 00:41:35.21 -49:37:11.76 | 3.246 | 0.92$\pm$0.30 | -8.61$\pm$0.36 | 9.53 $\pm$0.20 | 0.70$\pm$0.09 |  |  |  |
| 00:41:31.95 -49:37:07.89 | 3.253 | 1.02$\pm$0.30 | -8.33$\pm$0.36 | 9.35 $\pm$0.20 | 0.41$\pm$0.03 |  |  |  |
| 00:41:31.60 -49:36:58.25 | 3.245 | 2.26$\pm$0.32 | -8.92$\pm$0.39 | 11.19$\pm$0.22 | 1.15$\pm$0.05 |  |  |  |
| 00:41:26.93 -49:36:50.15 | 3.254 | 1.13$\pm$0.30 | -8.60$\pm$0.36 | 9.74 $\pm$0.20 | 0.30$\pm$0.04 |  |  |  |
| 00:41:34.99 -49:36:41.87 | 3.241 | 1.24$\pm$0.38 | -8.75$\pm$0.44 | 9.99 $\pm$0.23 | 0.90$\pm$0.06 |  |  |  |
| 00:41:32.22 -49:36:39.41 | 3.246 | 1.29$\pm$0.30 | -8.47$\pm$0.36 | 9.76 $\pm$0.20 | 0.53$\pm$0.06 |  |  |  |
| 00:41:35.04 -49:36:34.90 | 3.236 | 0.32$\pm$0.30 | -8.26$\pm$0.36 | 8.58 $\pm$0.20 | 0.08$\pm$0.02 |  |  |  |
| 00:41:34.50 -49:36:32.13 | 3.243 | 1.11$\pm$0.30 | -8.46$\pm$0.36 | 9.57 $\pm$0.20 | 0.57$\pm$0.06 |  |  |  |
| 00:41:32.18 -49:36:20.74 | 3.243 | 1.70$\pm$0.38 | -8.92$\pm$0.43 | 10.62$\pm$0.22 | 1.70$\pm$0.13 |  |  |  |
| 00:41:31.19 -49:36:20.33 | 3.254 | 0.85$\pm$0.30 | -8.30$\pm$0.36 | 9.15 $\pm$0.20 | 0.25$\pm$0.02 |  |  |  |
| 00:41:31.79 -49:36:18.97 | 3.248 | 0.66$\pm$0.30 | -8.67$\pm$0.36 | 9.33 $\pm$0.20 | 0.46$\pm$0.04 |  |  |  |
| 00:41:32.02 -49:36:18.98 | 3.243 | 2.19$\pm$0.33 | -8.89$\pm$0.40 | 11.08$\pm$0.22 | 0.88$\pm$0.06 |  |  |  |
| 00:41:31.92 -49:36:17.84 | 3.250 | 0.27$\pm$0.30 | -9.73$\pm$0.36 | 10.0 $\pm$0.20 | 0.31$\pm$0.25 |  |  |  |
| 00:41:34.89 -49:36:15.77 | 3.247 | 0.66$\pm$0.30 | -8.32$\pm$0.36 | 8.97 $\pm$0.20 | 0.30$\pm$0.02 |  |  |  |
| 00:41:34.12 -49:36:02.81 | 3.247 | 1.30$\pm$0.30 | -8.26$\pm$0.36 | 9.56 $\pm$0.20 | 0.38$\pm$0.02 |  |  |  |
| 00:41:30.93 -49:35:39.02 | 3.239 | 0.96$\pm$0.30 | -8.24$\pm$0.36 | 9.20 $\pm$0.20 | 0.25$\pm$0.02 |  |  |  |
| 00:41:30.94 -49:35:34.61 | 3.248 | 1.61$\pm$0.30 | -8.30$\pm$0.36 | 9.91 $\pm$0.20 | 0.54$\pm$0.03 |  |  |  |
| 00:41:29.98 -49:35:34.32 | 3.258 | 0.71$\pm$0.30 | -8.22$\pm$0.36 | 8.93 $\pm$0.20 | 0.20$\pm$0.03 |  |  |  |
| 00:41:32.25 -49:35:29.16 | 3.244 | 0.01$\pm$0.30 | -8.96$\pm$0.36 | 9.00 $\pm$0.20 | 0.45$\pm$0.15 |  |  |  |
| 00:41:35.13 -49:37:12.81 | 3.245 | 2.09$\pm$0.30 | -9.28$\pm$0.36 | 11.37$\pm$0.20 | 0.58$\pm$0.03 |  |  |  |

Table notes: The properties listed in the table refer to the sample of spectroscopically selected galaxies that have been identified in the FoV of the MUSE mosaic within a line-of-sight separation $\lvert\Delta\varv\rvert\leq1000\rm\,km\,s^{-1}$ from the central quasar. Uncertainties on the SFR, sSFR and $M_\star$ are computed as described in Section [3.4](#sec:SED_fitting).

[^1]:

[^2]: The final, combined cube consists on a $2\times2$ mosaic of 4 pointings. All of these overlaps in a small region $\approx60\rm\,kpc$ away from the quasar, where the integrated exposure time is of 20h. In all the other regions it ranges from 8h, at the edges, to 12h.

[^3]: The photometric calibration of the B-band and R-band observations is done with the extinction-corrected instrumental zero-point available on the ESO data quality-control database (<http://archive.eso.org/qc1/qc1_cgi>). These measurements are processed using the ESO pipeline by combining standard star observations taken for at least 7 stable nights around the nights of the observations. For the U-band images, instead, we run the ESO pipeline on the daily standard frames to measure the zero-point.

[^4]: <https://www.stsci.edu/scientific-community/software/drizzlepac.html>

[^5]: <https://matteofox.github.io/Marz/>

[^6]: We employed the luminosity functions to measure the expected number density of galaxies for blank fields. For the sample of LBGs, we integrated R-band luminosity function of (cite: Reddy2008) and multiplied it by the completeness curve of the FORS2/R-band (see Figure [1](#fig:data_FORS)) in order to resemble for the selection function of our sample. For the sample of spectroscopically-selected galaxies, instead, such value was directly taken from the luminosity function of the “MUSE-FIELD” sample (which is also consistent, within $1\sigma$ uncertainty, to the estimates from the luminosity function of (cite: Reddy2009) and that of the control-field sample we built masking the overdensity around the quasar). As a result, we measured a co-moving density in blank fields to be $\bar{\rho}_{\rm LBGs}=(2.4\pm0.2)\times10^{-3}\rm\,cMpc^{-3}$ and $\bar{\rho}_{\rm spec-z}=(2.5\pm0.8)\times10^{-3}\rm\,cMpc^{-3}$ for the color-selected LBGs and the MUSE spectroscopic sample, respectively.

[^7]: To estimate an order-of-magnitude completeness for the MUSE spectroscopic samples, we adopt the empirical method from (cite: Pozzetti2010; Davidzon2013; Ilbert2013; Moustakas2013; Laigle2016), which has already been applied by (cite: Toshikawa2024) on U-dropout galaxies at $z\approx3$. With a K-band magnitude limit of $25.5\rm\,mag$ (see Section [2.3](#sec:data_ancillary)), we estimate that our sample is 90$\%$ complete at $\log(M_\star/M_\odot)\approx9.8$.

[^8]: The set of models is publicly available at <http://www.bruzual.org/CB19/>. A detailed description is provided in Appendix A of (cite: Sanchez2022).

</paper>

Write the methods card for this paper.